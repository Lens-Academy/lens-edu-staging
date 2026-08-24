{++{"author":"Luc's AI","timestamp":1787591619157}@@---
tags:
  - validator-ignore
---
# Runner — how to execute the LO eval suite

These are the complete operating instructions for running the Learning Outcome quality evals. They are written for an AI agent with access to the lens-relay MCP tools and a shell; no repository checkout is needed.

You are running quality evals over **learning-outcome (LO) files** in `Lens Edu/Learning Outcomes/`. These evals judge our own content — the outcome statement, test question, and rubric of each LO file. They do NOT grade student answers.

Vocabulary:
- **The suite** is this folder: `Suite.md` (whose frontmatter `suite-version` is the current version) plus one eval file per check (A1, A2, B1, C2, C3). Each eval file's body is the authoritative judging standard.
- **Stamps** are `eval-results:` blocks written into LO frontmatter recording verdicts (schema in `Suite.md`).
- **Stale** = needs (re-)evaluation. Three causes: no stamp; stamp's `suite-version` older than current; stamp's `content-sha` no longer matches.

## Modes

- **Default** — evaluate all stale in-scope files.
- **All** — evaluate every in-scope file regardless of staleness.
- **Calibrate** — judge the golden-label files and report agreement; **no stamps written**.
- **Explicit paths** — evaluate exactly the named files.

## Roles (see also `Suite.md` → Runner architecture)

A **director agent** orchestrates. **Judge subagents** evaluate one file each and report structured results back to the director — judges never edit any document. **Stamping** is done by the director or delegated to a stamper subagent. Judges must never see the golden-labels file.

## Bootstrap

1. Load the lens-relay MCP tools (`create_session`, `read`, `grep`, `glob`, `edit`, `create`, `get_url`). In Claude Code, load them via ToolSearch.
2. `create_session`; the first line of the response is the `session_id` for all calls.
3. Read `Suite.md` — note `suite-version` — and the five eval files in this folder.
4. If the operator says they just edited any eval file's judging standard, `suite-version` must be bumped in `Suite.md` first; do not proceed until resolved.

## Scope

In-scope LO files = files in `Lens Edu/Learning Outcomes/` that have at least one non-empty `content::` test question, MINUS files tagged `skill-tree-placeholder`, MINUS these demo/template files: `Dummy Learning Outcome.md`, `Demo LO.md`, `Learning Outcome Demo.md`, `Learning Outcome Template.md`, `new learning outcome format.md`.

Discovery: `grep` pattern `content::` with `output_mode: files_with_matches` on path `Lens Edu/Learning Outcomes`; subtract the file list from `grep` pattern `skill-tree-placeholder`; subtract the demo/template names.

## Content hash

The hash makes staleness detection content-based. Rule: **hash what you judged** — the file exactly as rendered by the MCP `read` tool (pending suggestions included), with the `eval-results` mapping excluded.

Write this helper to your scratchpad as `lo_hash.py`:

```python
import hashlib, re, sys
raw = open(sys.argv[1]).read().split('\n')
out, skip = [], False
for ln in raw:
    if ln.strip() == '[Pending suggestions]':
        break                                   # read-tool appendix, never part of content
    ln = re.sub(r'^\s*\d+\t', '', ln, count=1)  # strip cat -n line-number prefix
    if skip:
        if ln[:1] in (' ', '\t'):
            continue                            # still inside the eval-results mapping
        skip = False
    if re.match(r'^eval-results:\s*$', ln):
        skip = True
        continue
    out.append(ln)
while out and out[-1].strip() == '':
    out.pop()
print(hashlib.sha256(('\n'.join(out) + '\n').encode()).hexdigest()[:8])
```

**Fetch file content byte-true — never hand-transcribe read output** (transcription drift corrupts hashes). The MCP server is plain HTTP; in Claude Code its URL is under the `lens-relay` entry in `~/.claude.json`. Helper (`mcp_read.sh`):

```bash
#!/bin/bash
# usage: mcp_read.sh <session_id> <kb-file-path> <out-file>
URL="<the lens-relay MCP url>"
jq -n --arg sid "$1" --arg fp "$2" '{jsonrpc:"2.0",id:1,method:"tools/call",params:{name:"read",arguments:{session_id:$sid,file_path:$fp}}}' \
 | curl -sS -X POST "$URL" -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' -d @- \
 | sed 's/^data: //' | jq -r '.result.content[0].text // empty' > "$3"
[ -s "$3" ] || { echo "EMPTY RESULT for $2" >&2; exit 1; }
```

Per file: fetch, then `python3 lo_hash.py <scratch-file>`.

## Staleness scan (default mode)

For each in-scope file: fetch it, compute the hash. Stale iff its frontmatter has no `eval-results`, or `eval-results.suite-version` < current suite version, or `eval-results.content-sha` ≠ the computed hash. Report counts (`N in scope, M stale: X unstamped, Y version-stale, Z content-changed`) before judging.

## Judging protocol

One judge subagent per LO file, launched in parallel batches of up to 8. **Judges only judge: they report structured results back to the director and never edit any document.**

Two ways to give a judge its inputs:

- **Paste protocol:** paste the fetched snapshot and the five eval bodies into the prompt; the judge needs no tools. Judged text and hashed text are identical by construction.
- **Self-read protocol (keeps the director's context clean — preferred):** the judge loads the MCP read tool itself and reads the five eval files and its one target file by path. The prompt MUST then say: "Read NOTHING else. In particular, never read anything under 'Lens/base'." Before stamping a self-read-judged file, re-fetch it and re-compute the hash; if it changed since the pre-judging fetch, the judged text is unknown — re-judge instead of stamping.

Judge prompt (fill placeholders; adapt the setup lines to the chosen protocol):

```
You are judging the quality of ONE learning-outcome file against six binary
checks. The file has three parts: the outcome statement (frontmatter
`learning-outcome:`), test question(s) (`content::`), and rubric(s)
(`assessment-instructions::`).

Rules:
- You only judge and report. Never edit, create, or modify any document.
- Judge one check at a time, in order (A1, A2, B1, C1, C2, C3). Each check's
  standard is its eval text — complete and authoritative. Do not add
  requirements from your own taste or from the other checks.
- A check judges only its target part (statement / question / rubric).
  Flaws elsewhere in the file are irrelevant to it.
- Evidence decides: for each verdict, quote the shortest snippet of the file
  that grounds it. If you cannot point to evidence for a FAIL, it is a PASS.
- Follow each eval's own guidance for uncertain cases; if it gives none and
  you are genuinely uncertain after applying its boundary, choose PASS
  (evals flag defects; uncertainty is not a defect).
- If the file has a question but no assessment-instructions at all, C1/C2/C3
  are fail with note "no rubric".
- Multiple questions/rubrics: a question/rubric check fails if any instance fails.

Return ONLY this JSON:
{"path": "...",
 "checks": {"A1": "pass|fail", "A2": "...", "B1": "...", "C1": "...", "C2": "...", "C3": "..."},
 "notes":  {"<id>": "<one line, fails only>"},
 "evidence": {"<id>": "<short verbatim quote, fails only>"}}
```

Never mention or include golden labels in a judge prompt in any mode.

## Stamping (skip entirely in calibrate mode)

Stamping is done by the director, or — preferred for larger runs, so the director never holds full file contents in context — delegated to a **stamper subagent** per file (gets: the path, the exact block to insert, instruction to read the file and insert/replace the block in the frontmatter). Extract edit anchors from the scratch snapshot with shell tools rather than reading files into context.

Insert or replace the `eval-results` block before the closing `---` of the frontmatter:

```yaml
eval-results:
  content-sha: <hash computed above>
  date: <today, YYYY-MM-DD>
  model: <the judge model id>
  suite-version: <current>
  checks: {A1: pass, A2: pass, B1: fail, C1: fail, C2: pass, C3: pass}
  notes: {B1: "<the judge's one-line reason>"}
  evidence: {B1: "<the judge's shortest verbatim quote grounding the fail>"}
```

`notes` and `evidence` are taken verbatim from the judge's report, fail entries only; omit both keys if all checks pass. Escape/replace double quotes inside values so the YAML stays valid. Edits land as pending CriticMarkup suggestions — expected and correct; the human bulk-accepts them in the review editor. Do not try to avoid the suggestion mechanism.

## Run report

After stamping, `create` a report at `Lens Edu/AI Guide/Evals/Learning Outcome Evals/Run Reports/<YYYY-MM-DD> Run.md` (suffix ` (2)` if taken): run parameters (mode, suite version, judge model, file counts), per-check pass/fail counts, per-file verdicts, and for every fail the judge's evidence and note. Include each file's outcome statement and question text so verdicts can be reviewed in place. Finish by printing the report's editor URL via `get_url`.

## Calibrate mode

The only mode allowed to read `Lens/base/LO Eval Golden Labels.md`. Judge the files listed under `golden` with the normal protocol (judges must never see expected verdicts); compare per check, skipping `"unsure"` values; report the `provisional` section separately, clearly marked non-ground-truth. Output: per check — n compared, agreements, and every disagreement with golden verdict, judge verdict, judge evidence, and golden note. Write no stamps. Perfect agreement is not expected — disagreements drive eval-text fixes (which then bump `suite-version`).

## Final summary

End every run by reporting: mode; suite version; judge model; files judged / stamped; per-check fail counts; for calibrate, the agreement table; the run-report URL.
++}
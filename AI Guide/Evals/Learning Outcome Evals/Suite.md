---
suite-version: 2
tags:
  - validator-ignore
---
# Learning Outcome Eval Suite

This folder holds the evals that assess the quality of **learning-outcome files themselves** — the outcome statement, the test question, and the rubric. They are not learner-grading rubrics; they grade our own content. Each eval is a single binary check, grounded in failure modes observed during the human open-coding pass in `Lens/base/Learning Outcome Annotation Pass.md`.

The runner instructions live in `Runner.md` in this folder — any AI agent with lens-relay MCP access and a shell can execute a run; no repository checkout is needed. Runs are manual — this suite is never part of automatic content validation.

## Runner architecture

A run is orchestrated by a **director agent** and executed by subagents with strictly separated roles:

- **Judge subagents** evaluate one LO file each and **report their verdicts back to the director as structured results. Judges never edit any document.**
- **Stamping** — writing `eval-results` into the LO files — is done by the director, or delegated to a dedicated **stamper subagent** per file (preferred for larger runs, so the director doesn't have to hold full file contents in its context).
- Judges must never be shown, or allowed to read, the golden-labels file (`Lens/base/`).

## The checks

| Id | Target | Binary question |
|---|---|---|
| A1 | statement | Does the statement name an observable capability, pinned precisely enough that you can tell what would demonstrate it? |
| A2 | statement | Would the capability make sense for someone who learned the material elsewhere, or does it depend on what a specific text/author says? |
| A3 | statement | Is the statement a single unit of completion — one capability that stands or falls together — rather than a bundle a learner could independently have or lack? |
| B1 | question | Could someone who has the capability but never read the assigned text answer the question as posed? |
| C2 | rubric | Does the pass bar require only things a reasonable reader of the question would know to provide? |
| C3 | rubric | Does each criterion define an idea-in-any-wording, with analogies, examples, and details as illustrations rather than requirements? |

Each check has its own file in this folder (`A1 - Concrete capability.md`, …) containing the pass boundary, explicit non-failures, and pass/fail exemplars from the corpus. The eval file body is the authoritative judging standard.

## Versioning

**One suite-wide version number** — the `suite-version` in this file's frontmatter. Any meaningful change to any eval file in this folder (boundary, exemplars, adding/removing/renumbering checks) bumps it. All stamps carrying an older `suite-version` are stale in full; we accept the cost of re-running everything. Typo fixes that don't change a boundary don't bump.

**v2 (2026-08-24):** removed C1 (binary rubric). Learning-outcome rubrics are no longer required to be binary pass/fail — graded scales are an accepted rubric form — so the check was retired; its eval file is archived in `Archive/`. Also added A3 (single completion unit), promoted from the annotation-pass ruling on *Comparing alignment research agendas*.

## Result stamps

The runner writes its verdicts into each evaluated LO file's frontmatter:

```yaml
eval-results:
  content-sha: 9f3c2a1b
  date: 2026-08-19
  model: claude-fable-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "question opens 'Chapter 5…'"}
  evidence: {B1: "Chapter 5 opens with an allegory about an alien civilization"}
```

- `checks` records every check's verdict. `notes` carries the judge's one-line reason and `evidence` its shortest verbatim quote from the file grounding the verdict — both for fails only, both taken from the judge's report, so a stamp is self-explanatory without opening the run report. The run report additionally carries the full write-up.
- `content-sha`: first 8 hex chars of sha256 over the file **as read at evaluation time** (rendered view, pending suggestions included — hash what you judged), with the entire `eval-results` mapping excluded from the hashed text. Exact normalization procedure lives in `Runner.md`.
- Stamps land as pending suggestions; bulk-accept them in the review editor.

A learning outcome is **stale** (should be re-evaluated) iff any of:

1. it has no `eval-results` stamp;
2. the stamp's `suite-version` is older than this file's;
3. the stamp's `content-sha` no longer matches the file's current hash.

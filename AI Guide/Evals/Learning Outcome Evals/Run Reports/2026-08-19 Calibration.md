{++{"author":"AI","timestamp":1787137470342}@@---
tags:
  - validator-ignore
---
# Calibration run — 2026-08-19

First calibration of the LO eval suite. **Suite version 1**, judge model `claude-fable-5`, one judge subagent per file, 14 files judged (no stamps written during calibration; two files were separately stamped afterwards as a runner spot-test).

## Agreement vs golden labels

**16 / 16 comparisons agree (100%).** One golden value (`Compute accounting` A2 `unsure`) was skipped per protocol — the judge failed it, correctly applying the A2 eval's "when genuinely uncertain, fail and let triage decide" rule.

| File | Check | Golden | Judge |
|---|---|---|---|
| AI is grown, not crafted | B1 / C1 / C3 | fail / fail / fail | fail / fail / fail ✓ |
| Access substitutes for verification technology | A2 | fail | fail ✓ |
| Alignment as alchemy | A2 | fail | fail ✓ |
| Decomposing AI risks | A1 | fail | fail ✓ |
| Decomposing an unanswerable question | A1 / A2 | pass / pass | pass / pass ✓ |
| Goals and instrumental convergence | A1 | fail | fail ✓ |
| Hard calls vs. easy calls | A2 / B1 | pass / fail | pass / fail ✓ |
| Hostile vs. indifferent AI | A1 / A2 / B1 | pass / pass / fail | pass / pass / fail ✓ |
| Human welfare as an instrumental variable | B1 | fail | fail ✓ |
| The goal-space argument | C1 | fail | fail ✓ |

Provisional (AI-proposed, non-ground-truth) labels: 9/9 agree (goal-space B1+C2, Verifying inference C1+C2+C3, Intelligence as prediction C1+C3, Trajectories C1+B1).

**Circularity caveat:** many golden items are quoted as exemplars inside the eval files themselves, so those agreements partly test recognition, not generalization. The genuine generalization evidence is the un-cited judgments, which also all landed sensibly — see below.

## Judgments beyond the labels (worth human review)

1. **Intelligence as prediction plus steering — B1 fail (new catch):** the question says "Using the chapter's framework, analyze the three systems" — not parseable without the chapter. Our best-rubric exemplar file has a text-bound question.
2. **Hostile vs. indifferent AI — C3 fail (new):** the pass level requires "chapter evidence" and embeds the anthill analogy with no "or equivalent" route.
3. **Decomposing an unanswerable question — C1 fail (new):** its rubric is a 1–5 ladder with a named pass bar; per C1's boundary ("a ladder that names a pass bar still fails"), correctly failed. Nuanced contrast: the judge **passed** Trajectories' C1 because its ladder lives in an authors-only `%% %%` comment while the actual instruction is "Single pass/fail overall" — exactly the right distinction.
4. **Decomposing AI risks — B1 fail (new, subtle):** "categories of AI risk introduced in this module" is course-scaffolding.
5. **Compute accounting — B1 pass:** question restates the scheme's design goal, so it self-contains; only the statement (A2) is source-bound. Good check separation.

## Per-check tallies across the 14 files

| Check | pass | fail |
|---|---|---|
| A1 | 12 | 2 |
| A2 | 10 | 4 |
| B1 | 6 | 8 |
| C1 | 2 | 12 |
| C2 | 12 | 2 |
| C3 | 11 | 3 |

## Verdict

The suite is usable at version 1. Before a full census: (1) Luc reviews the five beyond-label judgments above — confirming or overruling them extends the golden set either way; (2) decide whether `Compute accounting` A2 resolves to pass (field-canonical) or fail (rephrase/delete), which also sharpens the A2 boundary text.

Runner spot-test after calibration: `AI is grown, not crafted` and `Intelligence as prediction plus steering` were stamped with `eval-results` (pending suggestions), and the staleness logic verified: stamp-stripped re-hash matches the stored `content-sha`; an in-content edit changes it.
++}
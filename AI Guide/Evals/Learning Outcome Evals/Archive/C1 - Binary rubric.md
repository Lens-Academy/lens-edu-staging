---
eval-id: C1
target: rubric
tags:
  - validator-ignore
---
# C1 — Binary rubric

> **Retired in suite v2 (2026-08-24).** We no longer require rubrics to be binary pass/fail — graded scales are an accepted rubric form. Kept for reference only; not part of the active suite.

**Binary question:** Is the rubric's scoring decision pass/fail, built from criteria that are each individually binary, with a stated pass rule?

## Pass boundary

The rubric's output must be a pass/fail verdict. Its criteria must each be checkable yes/no, and the rubric must say how they combine (all required; or "all required plus at least m of these n"). A graded scale of any kind fails — numeric ladders (1–5), prose scales ("Award 4-5 for …; 3 for …; 1-2 if …"), or "score from 1 to 5" instructions. A ladder that names a pass bar inside it (e.g. "level 3 is the pass bar") **still fails**: the scoring decision it defines is scalar.

If the file has multiple questions with rubrics, all must be binary for the check to pass.

## Does NOT fail for

- m-of-n pass rules ("pass at least 2 of these 4").
- Internal counts inside one criterion ("names at least two distinct risks, each with a mechanism").
- Multiple required criteria.
- Appended qualitative-feedback guidance ("name the strongest part and the one thing that would most improve it") — feedback instructions are welcome; they're just not the scoring decision.



## Fail examples (from the corpus)

- *The goal-space argument* rubric — a `**1**`…`**5**` ladder.
- *AI safety advocacy and public communication* rubrics — prose scales: "Award 4-5 for a clean distinction plus the pro-advocacy theory of change; 3 for the distinction with a vague case; 1-2 if the two games are conflated."

## Pass examples (from the corpus)

- *Intelligence as prediction plus steering* — "Pass only if the answer demonstrates all three checks", each check binary, explicit fail conditions.
- *Trajectories with mechanisms and falsifiers* — "Single pass/fail overall. Pass requires the first THREE… Checks 1 to 3 are each binary", with check 4 explicitly non-gating.

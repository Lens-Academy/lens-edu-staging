---
eval-id: C2
target: rubric
tags:
  - validator-ignore
---
# C2 — No unasked demands

**Binary question:** Does the rubric's pass bar require only things a reasonable reader of the question would know to provide?

## Pass boundary

Direction matters: **pass-bar ⊆ question.** Every requirement in the rubric's pass decision must be something the question asks for, explicitly or by clear implication. A student who reads the question carefully and answers everything it asks must be able to pass; if the rubric fails them for omitting something the question never signaled, this check fails.

The reverse is fine: the question **may** ask for more than the pass bar requires — headroom is allowed.

For graded-ladder rubrics, evaluate this check against the stated or implied pass level (usually level 3).

## Does NOT fail for

- Requirements clearly implied by the question's wording ("explain why" implies giving the mechanism; "compare" implies covering both sides).
- Enrichment or feedback-only content above the pass bar.
- The question over-asking relative to the pass bar.

## Fail examples (from the corpus)

- *The goal-space argument* — the pass level requires "uses the alien allegory or an equivalent concrete example", but the question asks only "In your own words, what is the 'goal-space argument'? Why…?" — no example is requested.
- *Verifying inference to catch exfiltration* — the pass level requires reporting the quantitative results (under 0.5% exfiltration, under 0.01% false-positive rate, 200x slowdown), which the question never asks for.

## Pass examples (from the corpus)

- *Narrow coalition strategy* — the pass level requires exactly the three components the question enumerates (the ask, the exclusions, the reason) and nothing more.
- *Trajectories with mechanisms and falsifiers* — every pass gate (two mechanism-distinct trajectories, named drivers, near-term falsifiers) is explicitly demanded by the question; the shared-assumption ask is explicitly non-gating.

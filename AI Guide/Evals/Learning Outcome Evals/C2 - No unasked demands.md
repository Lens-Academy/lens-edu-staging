---
eval-id: C2
target: rubric
tags:
  - validator-ignore
---
# C2 — No unasked demands

**Binary question:** Does every point the rubric awards, and every cap or deduction it applies, depend only on things the question asks for?

## Pass boundary

Direction matters: **scored elements ⊆ question.** This is judged on points, not on the pass bar. For each scored element, each cap and each deduction, you must be able to point to the words in the question that ask for it, explicitly or by clear implication. A learner who reads the question carefully and answers everything it asks, correctly and in their own words, must be able to get full marks; if the rubric withholds points from them for leaving out something the question never signaled, this check fails, even when they would still pass.

"Clear implication" means a careful reader would know to provide it: "explain why" asks for a reason, "compare" asks for both sides. It does not stretch to a particular reason, mechanism or depth the question does not signal. A "why" is answered by a correct reason that settles it. If the learner's reason is correct and settles the question (for example "why choose that option rather than the others?" answered with "it scores best on the quantity we just computed"), a rubric that also requires the reason behind that reason (why the options score as they do, the mechanism under the criterion) is scoring something unasked. If the rubric wants that deeper explanation, the question has to ask for it.

Run this test, do not skip it: write out the shortest answer that correctly answers every part of the question as worded, giving for each "why" the most direct correct reason. Then score it with the rubric exactly as written, caps included. If it scores clearly below full marks (below about 85), fail, and name the element or cap that costs it the points.

The reverse is fine: the question **may** ask for more than the rubric scores; headroom is allowed.

For graded-ladder rubrics, apply the same test to the top level.

## Does NOT fail for

- Requirements clearly implied by the question's wording, in the narrow sense above.
- Content outside the scored elements: a model answer labelled as not a grading checklist, or `feedback-instructions::`.
- The question over-asking relative to what the rubric scores.
- Caps or deductions for a genuine error in something the question asks for.

## Fail examples (from the corpus)

- *The goal-space argument* — the pass level requires "uses the alien allegory or an equivalent concrete example", but the question asks only "In your own words, what is the 'goal-space argument'? Why…?" — no example is requested.
- *Verifying inference to catch exfiltration* — the pass level requires reporting the quantitative results (under 0.5% exfiltration, under 0.01% false-positive rate, 200x slowdown), which the question never asks for.
- *Attack rate against a control protocol* (before 2026-10-04; Elias's ruling) — the question asks "Which option would a scheming U choose, and why that one rather than the others?" after the learner has computed U's win chance for each option. "It has the highest chance of winning" fully answers that. The rubric gave 30 of the part's 35 points, and a cap at 55, only for explaining why attacking less often and why attacking more often each lower U's chances: the reason behind the reason. The learner still passed, so the old pass-bar version of this check let it through.

## Pass examples (from the corpus)

- *Narrow coalition strategy* — the pass level requires exactly the three components the question enumerates (the ask, the exclusions, the reason) and nothing more.
- *Trajectories with mechanisms and falsifiers* — every pass gate (two mechanism-distinct trajectories, named drivers, near-term falsifiers) is explicitly demanded by the question; the shared-assumption ask is explicitly non-gating.

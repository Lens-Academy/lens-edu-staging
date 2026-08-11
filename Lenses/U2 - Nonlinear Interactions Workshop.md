---
id: 'f646ea15-5ffb-4a50-bd4e-a0e9494cf00e'
title: "Nonlinear Interactions Workshop"
tldr: Four systems, four sets of parts, and four different ways the parts interact so that the simple curve is wrong. No reading. You build the curves and the tutor tries to break them.
summary_for_tutor: "The practice lens for the extrapolation outcome. No reading assignment. Four question fields, each carrying a different nonlinear structure: adverse selection of the residual, a threshold, a min-over-constraints bottleneck, and a feedback loop where the measurement changes the measured. Each field gets targeted tutor feedback. The final field closes by comparing the four structures. This is where the mathematical objects get exercised, so do not let it become a discussion of AI timelines in general."
authors:
  - Claude
---
#### Text
content::
\## No reading this time

In the previous lens you saw one extrapolation fail. Now you build some.

Four short scenarios follow, each in its own question field with targeted tutor feedback. Each scenario is a system with parts. In each one, the parts interact in a way that makes the obvious curve wrong. The four curves are wrong in four different ways. Those differences matter, because the four failures are not interchangeable.

Work through them in order. Write out the arithmetic, not a description of it.

#### Question
content::
\## Scenario 1 of 4

A translation company has been automating its work. Two years ago machines handled 20% of its jobs unsupervised; today they handle 40%. The operations director doubles the rate forward and reports full automation in three more years.

What is wrong with this forecast? State what property of the remaining 60% makes the extrapolation invalid, what shape you expect instead, and what evidence would distinguish a merely harder remainder from one that may never be fully automated.
assessment-instructions:: The student has read Xu and Shulman on the fractional-progress failure and is now applying that reasoning to a fresh case. Make the student produce the reasoning; do not lecture before they attempt it.

Target: the jobs were not sampled at random. Automation took easier jobs first, so the residual is systematically harder and marginal cost per percentage point rises. The curve should flatten, possibly toward an asymptote below 100%. The three-year estimate is too early. Evidence should inspect the internal structure of the remaining jobs rather than extend the aggregate trend.

Reply in 80 to 160 words using short paragraphs and no list longer than 4 items. Confirm or correct the direction of error. Name up to 2 gaps and ask at most 2 direct causal follow-ups. If they are stuck after 2 attempts, give a brief direct answer. Do not over-validate or use generic praise.

#### Question
content::
\## Scenario 2 of 4

A hospital's automated dispensing system handled 5%, then 8%, then 12% of prescriptions over three years. A regulator is deciding whether to certify it for unsupervised operation. If certified, the hospital plans to route everything through it that is not explicitly flagged.

Forecast the share in two years. Explain why this case differs from Scenario 1, and state what forecasting object should replace a smooth curve.
assessment-instructions:: This is the second independent application in a nonlinear forecasting workshop. Make the student reason from the scenario. Do not turn it into a general discussion of AI timelines.

Target: certification is a discrete gate. The observed creep measures incremental trust under supervision, while certification could cause a jump. A curve fitted to pre-threshold data cannot represent the gate and will likely be too slow. The right object is a probability that the gate opens combined with a separate estimate of the post-gate level. If the student concludes that extrapolation is always wrong, ask what conditions would make a smooth curve appropriate.

Reply in 80 to 160 words using short paragraphs and no list longer than 4 items. Name up to 2 gaps and ask at most 2 direct causal follow-ups. If they are stuck after 2 attempts, give a brief direct answer. Do not over-validate or use generic praise.

#### Question
content::
\## Scenario 3 of 4

A datacentre operator projects capacity from three inputs: chips available, growing 40% a year; electrical supply contracted, growing 15% a year; and trained operations staff, growing 25% a year. The finance team multiplies the three growth rates together.

What is the correct combination rule? Show what it implies for near-term capacity growth, then explain what happens when the binding constraint changes or when inputs can substitute for one another.
assessment-instructions:: This is the third independent application in a nonlinear forecasting workshop. Require the student to write the arithmetic or combination rule, not merely describe it.

Target: capacity is bounded by the binding constraint, so the rule is a minimum, not a product. Near-term growth is roughly 15% a year, set by power, until another input binds. A handover makes the aggregate curve piecewise and changes its slope. Substitution softens the minimum; degree of substitutability determines which model applies. Multiplying the rates is the wrong operation and yields a number the inputs cannot deliver.

Reply in 80 to 160 words using short paragraphs and no list longer than 4 items. Confirm or correct the operation and arithmetic. Name up to 2 gaps and ask at most 2 direct causal follow-ups. If they are stuck after 2 attempts, give a brief direct answer. Do not over-validate or use generic praise.

#### Question
content::
\## Scenario 4 of 4

A widely followed index publishes a quarterly score for AI coding assistants using a fixed benchmark suite. The score has risen steadily for six quarters. Labs cite it in funding rounds, and one lab's bonus structure references it.

What is the curve measuring now, and can it be extrapolated as capability? Propose a better measurement strategy. Then compare this failure with Scenario 1: what acts on what in each case?
assessment-instructions:: This is the final application and synthesis in a four-part nonlinear forecasting workshop.

Target: the benchmark is no longer an independent observation because labs optimise against it. The score mixes genuine capability with benchmark targeting, so extrapolating it forecasts the score, not capability. Better strategies include an unpublished holdout benchmark, a measure nobody is rewarded to move, or the gap between benchmark and deployed performance. This differs from Scenario 1: there selection acts on what is counted; here counting feeds back into the system.

After addressing this answer, name all four structures: adverse selection of the residual, threshold, minimum over constraints, and feedback from measurement. Ask which appeared in the prior fractional-progress survey and why. Part 1 is clearly present because researchers solve tractable subproblems first; Part 4 is arguable because researchers estimating their field have professional stakes. Accept a defended Part 4 argument, but push back on claims that all four occur everywhere. Close with a direct test-readiness verdict based on work visible across all four question fields, naming strengths and gaps.

Reply in 100 to 180 words using short paragraphs and no list longer than 4 items. Do not over-validate or use generic praise.

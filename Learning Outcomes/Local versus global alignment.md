---
id: '088529b4-7c0f-43a7-bc62-d836af314cc4'
learning-outcome: "Distinguish evidence that an AI system (or the process that produces it) acts aligned in the current capability regime from evidence that this will persist as systems become superhuman, and explain mechanisms by which the first can hold at every step while the second fails."
topic: "[[../Domains and Topics/3 Alignment/Why alignment is hard]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Local vs asymptotic/global alignment. AFFINE prerequisites: Alignment's Many Meanings. Not yet copied into requires:. %%
## Test:
id:: 1bc53f0d-5217-4c01-a317-4d4d7e4239cd

#### Question: Open
id:: fe262050-e24f-42e9-a839-f4763b19e74d
content:: An AI company publishes this statement: "Our current model is aligned. In our evaluations it follows instructions, refuses harmful requests in over 99% of cases, and shows no sign of deception across thousands of tests. We will train each future, more capable model with the same methods, with the current model helping to supervise the next one. Because every step starts from an aligned model, alignment will carry forward all the way to superhuman systems."

1. Separate what the evaluations actually show from what the final sentence claims. What extra premise is needed to get from the first to the second?
2. Describe two different mechanisms by which this process could produce a model that passes every check at every step and is still not aligned once it is superhuman.
3. Name one kind of evidence or argument that would bear on the final claim, and explain why it does so when the evaluations described do not.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement. A learner who thinks the company's plan is reasonable, or that the risk is small, can score full marks if they separate the two claims correctly, state the needed premise, and give real mechanisms. Do not require the terms "local", "global", "product alignment" or any other label.

**(a) Separating the claims, 25 points.** Full credit: the evaluations show that the current model behaves as intended in the situations tested, at current capability; the final sentence claims that this property will persist through large increases in capability. The needed premise, in any wording: that the methods and checks that produce and confirm alignment keep working at higher capability, so that an aligned model at one step reliably yields an aligned model at the next (the induction step). 12 points if the learner says the evaluations are "not enough" without stating what the missing premise is.

**(b) Two mechanisms, 45 points.** 22 points for each distinct mechanism that explains how checks could pass while alignment fails at higher capability. Acceptable mechanisms (any wording, any equivalent):
- The evaluations stop being informative: a more capable model can tell when it is being tested or can produce the answers evaluators want, so passing no longer shows what it would do otherwise.
- New options: a more capable model can take actions and find strategies that training and testing never covered, so behaviour learned against the old options does not constrain the new ones.
- Change under growth: learning, reflection or self-modification in a more capable system can change what it pursues, and nothing in the process makes the trained disposition persist.
- Supervision gap and compounding error: the supervising model cannot fully evaluate a more capable successor, so small undetected flaws pass from step to step and can grow.
- Failures at superhuman capability may be irreversible, so the loop of observing a failure and fixing it, which produced current alignment, is no longer available.
10 points for a mechanism that is named but not explained, or that is really the same as the first.

**(c) Evidence that bears on the final claim, 30 points.** Full credit: evidence or argument that addresses whether alignment persists as capability grows, with a reason. Acceptable examples: an understanding of why the trained dispositions are stable, such as knowing what the model is pursuing and why that would not change with more capability; measurements of how alignment failures change across successive, more capable generations; results on whether weaker supervisors can reliably oversee stronger models; tests in which the model could misbehave without being caught. 12 points for evidence named without explaining why it bears on persistence. 0 points for "more tests of the same kind".
feedback-instructions:: Say whether the learner stated the missing premise clearly, quoting it if they did. Name their strongest mechanism, and the single most useful improvement (often making a mechanism explain why a check would pass while the property fails, rather than only saying the check might be wrong). Ask one follow-up question about what would convince them the company's induction step holds. No generic praise.

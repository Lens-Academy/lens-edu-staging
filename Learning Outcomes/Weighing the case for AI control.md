---
id: '37ea7ee7-076c-4ebd-ac7e-cd7bd34810a9'
learning-outcome: "Given an unfamiliar exchange between people who disagree about whether work on AI control is worth doing, identify the factual crux their disagreement turns on, name an observation that would move each side, and state where you currently land on whether more work on control is net positive, with a confidence level, the consideration that most drives your view, and what would change your mind."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
tags:
  - wip
---
## Test:
id:: c4d0520b-4d0b-49f4-8b3a-4629ec299cbf

#### Question: Open
id:: 64f697c6-3d32-4ba4-a779-2fedcf70e4bc
content::
Two researchers disagree about AI control.

**Researcher A:** "I think working on AI control right now is a mistake. Control techniques only hold for models that are not much smarter than us. The real danger comes from models far beyond that, and for those the only thing that works is not building them yet. Every hour spent on control is an hour not spent making the case for an international pause. Worse, control lets labs feel safe deploying models they know are misaligned, so it takes pressure off governments to act."

**Researcher B:** "I agree control will not work for models far smarter than us. But I don't expect a pause in time: governments have not even agreed on basic incident reporting. If the next few model generations get deployed anyway, I want them deployed under monitoring that catches them trying to sabotage safety work or escape. Those models could do a lot of useful safety research for us if we stop them from undermining it. And a model caught in the act is some of the strongest evidence we can hand to policymakers."

Answer all three parts:

1. What is the crux between A and B: a claim about the world which, if it were settled, would most likely settle their disagreement? Explain why their conclusions turn on it.
2. Name one observation in the next few years that should move A towards B's view, and one that should move B towards A's view.
3. Your own view: is more work on AI control net positive, net negative, or too close to call? Give your confidence, the consideration that drives your view most, and what would change your mind.
assessment-instructions:: Score out of 100. Grade the reasoning, never the conclusion. Any verdict on part 3, including net negative, net positive or too close to call, can earn full marks.

Facts about the exchange the grader needs: A and B agree that control will not work for models far smarter than us. They disagree on factual questions such as (a) whether a pause or strong government action is achievable in time, (b) whether control work reduces the pressure for such action (A) or produces evidence that increases it (B), and (c) whether models deployed under control can do useful safety research. Any of these, or another factual disagreement that both conclusions depend on, is an acceptable crux.

40 points, part 1 (the crux). 40: names a factual question on which A and B disagree and explains how each side's conclusion depends on it (for example: if a pause is achievable, A's case that control time is better spent on a pause gets stronger, and if it is not, B's case for making the deployed models safer gets stronger). 20: names a real disagreement between them but does not explain how the conclusions depend on it, or names a difference in values or priorities without connecting it to a factual question. 5: names the point they agree on (control does not scale to models far smarter than us) as the crux, or only restates their conclusions.

30 points, part 2 (observations). 15 for an observation that would move A towards B, 15 for one that would move B towards A. An observation earns its 15 if it could actually happen and would bear on a point A and B disagree about, in the right direction (for example, towards B: governments fail to act after a serious public AI incident, or a model deployed under control is caught and the catch leads to concrete policy action; towards A: a pause or binding international agreement gains real political traction, or a lab uses its control measures to justify deploying a model it knows is misaligned without new safeguards). 7 for an observation that bears on the disagreement only loosely or is too vague to check. 0 if it points the wrong way or is not observable.

30 points, part 3 (own view). 10: states a verdict and a confidence level (a probability, a percentage, or plain words such as "about 60 percent" or "low confidence"). 10: names the consideration that most drives the view and gives a reason for it. 10: says concretely what would change their mind (an observation, a result or an argument, not "if I learned more"). If the stated confidence is plainly at odds with the learner's own reasons (for example "99 percent net positive" while calling an unresolved question the decisive crux) and the answer gives no explanation, cap part 3 at 20.

Model answer, for the feedback, not a grading checklist: "1. The crux is whether a pause or strong government action is achievable in time. A thinks it is reachable, so effort on control is effort taken from the plan that works. B thinks it is not, so the realistic choice is between deploying the next models with monitoring or without it. 2. A should move towards B if a serious public incident leads to no binding action within a year. B should move towards A if a pause gains broad political support, or if labs use monitoring to keep shipping models they know are misaligned. 3. Too close to call, about 55 percent net positive. The consideration that drives it: I doubt a pause is coming in time, so I care about the models we will actually get. I would change my mind if control turned out to hide incidents from the public instead of producing evidence."
feedback-instructions:: The learner just took the graded test for "Weighing the case for AI control". Start with the strongest part of the answer in one sentence. Then name the single most important gap that cost points: most often a crux that is the point A and B agree on, an observation that would not bear on the crux, or a "what would change my mind" that is too vague to check. Give one concrete example of how to fix it. Do not comment on whether their verdict is right, and do not argue for any side. 80 to 150 words, short paragraphs, no lists, no generic praise. If the learner says they do not understand the score, point to the part that lost the most points and explain what the rubric looked for there.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Practice finding the crux]]
notes:: Practice for parts 1 and 2 on the Gleave and Habryka debate, with tutor feedback.
## Lens:
source:: [[../Lenses/AICF - Gleave and Habryka on current safety techniques]]
## Lens:
source:: [[../Lenses/AICF - Blocking monitors and early warning shots]]
## Lens:
source:: [[../Lenses/AICF - Should safety researchers quit frontier labs]]

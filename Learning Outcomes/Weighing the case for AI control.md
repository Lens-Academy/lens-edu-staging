---
id: '37ea7ee7-076c-4ebd-ac7e-cd7bd34810a9'
learning-outcome: "Given an unfamiliar exchange between people who disagree about whether work on AI control is worth doing, identify the factual crux their disagreement turns on, name an observation that would move each side, and say where you stand on that crux and what it implies for whether more work on control is net positive, with a confidence level and an observation that would change your mind."
topic: "[[../Domains and Topics/7 AI Control/The control agenda]]"
stage: beginner
authors:
  - Elias+Claude
---
## Test:
id:: c4d0520b-4d0b-49f4-8b3a-4629ec299cbf

#### Question: Open
id:: 64f697c6-3d32-4ba4-a779-2fedcf70e4bc
content::
Two researchers disagree about AI control.

**Researcher A:** "I think working on AI control right now is a mistake. Control techniques only hold for models that are not much smarter than us. The real danger comes from models far beyond that, and for those the only thing that works is not building them yet. Every hour spent on control is an hour not spent making the case for an international pause. Worse, control lets labs feel safe deploying models they know are misaligned, so it takes pressure off governments to act. And frankly, I did not get into safety to help companies ship products faster."

**Researcher B:** "I agree control will not work for models far smarter than us. But the next few model generations are going to be deployed whatever we do. I want them deployed under monitoring that catches them trying to sabotage safety work or escape. Those models could do a lot of useful safety research for us if we stop them from undermining it. And a model caught in the act is some of the strongest evidence we can hand to policymakers."

Answer all three parts:

1. What is the crux between A and B: a claim about the world which, if it were settled, would most likely settle their disagreement? Explain why their conclusions turn on it.
2. Name one observation in the next few years that should move A towards B's view, and one that should move B towards A's view.
3. Your own view: where do you stand on the crux you named, and what does that mean for whether more work on AI control is net positive, net negative, or too close to call? Give your confidence, and name an observation that would change your mind (it can be one from part 2).
assessment-instructions:: Score out of 100. Grade the reasoning, never the conclusion. Any position on the crux and any verdict, including net negative, net positive or too close to call, can earn full marks.

Facts about the exchange the grader needs: A and B agree that control will not work for models far smarter than us. They disagree on factual questions such as (a) whether a pause or strong government action is achievable in time (A works towards one, B expects the next model generations to be deployed anyway), (b) whether control work takes pressure off governments (A) or produces evidence that helps policymakers act (B), and (c) whether control speeds up capabilities by making misaligned models safe enough to deploy. A's last sentence (not wanting to help companies ship products faster) states a personal motivation, but it also implies (c). B does not address (c) directly, but B's case for deploying the next models under monitoring assumes those models will be deployed anyway, so control does not speed them up. Any of these, or another factual disagreement that both conclusions depend on, is an acceptable crux.

40 points, part 1 (the crux). 40: names a factual question on which A and B disagree and explains how each side's conclusion depends on it (for example: if a pause is achievable in time, A's case that effort should go to a pause gets stronger, and if it is not, B's case for making the deployed models safer gets stronger). 20: names a real disagreement between them but does not explain how the conclusions depend on it, or names a difference in values or priorities without connecting it to a factual question. 5: names the point they agree on (control does not work for models far smarter than us) as the crux, or only restates their conclusions. 0: no crux given, or one unrelated to the exchange.

30 points, part 2 (observations). 15 for an observation that would move A towards B, 15 for one that would move B towards A. An observation earns its 15 if it could actually happen, would bear on a point A and B disagree about or on a premise either side's conclusion rests on, and would plausibly move that side in the direction the learner claims. Examples, not requirements: towards B, red-team tests show a control protocol reliably containing a model much smarter than its monitors (this removes A's premise that control only holds for models not much smarter than us), governments fail to act after a serious public AI incident, or a model deployed under control is caught and the catch leads to concrete policy action. Towards A, a pause or binding international agreement gains real political traction, a lab cites its control measures to justify deploying a model it knows is misaligned, or labs release more capable models sooner because control measures made their models safe enough to deploy. Towards B on that point, labs that adopt control deploy no faster than labs that do not. Some observations bear on more than one disputed point and could be argued either way: credit the direction the learner argues for if the argument holds. 7 for an observation that bears on the disagreement only loosely or is too vague to check. 0 if the claimed direction does not follow or the observation could not be made.

30 points, part 3 (own view). 10: states a verdict on whether more work on control is net positive, net negative or too close to call, with a confidence level (a probability, a percentage, or plain words such as "fairly confident" or "low confidence"). 10: says where they stand on the crux they named in part 1 (or on another real disagreement in the exchange) and how that leads to their verdict. 10: names a concrete observation that would change their mind (not "if I learned more"). If the stated confidence is plainly at odds with what the learner says about the crux (for example, they call the crux a coin flip and their verdict depends on it, yet claim 99 percent) and nothing in the answer reconciles the two, cap part 3 at 20.

Model answer, for the feedback, not a grading checklist: "1. The crux is whether a pause or strong government action is achievable in time. A thinks it is reachable, so effort on control is effort taken from the plan that works. B doubts a pause comes before the next models are deployed, so the realistic choice is between deploying the next models with monitoring or without it. 2. A should move towards B if a serious public incident leads to no binding action. B should move towards A if a pause gains broad political support. 3. I lean slightly towards A on the crux: I think a pause is more reachable than B assumes, though not by much. So I think more control work is too close to call right now, with low confidence. If the next serious public incident led to no binding action, I would move towards B."
feedback-instructions:: The learner just took the graded test for "Weighing the case for AI control". If the score is 100, confirm in one or two sentences what made the answer work and stop. Otherwise start with the strongest part of the answer in one sentence. Then name the single most important gap that cost points: most often a crux that is the point A and B agree on, an observation that bears neither on a point A and B disagree about nor on a premise either side relies on, a verdict that is not connected to the learner's own position on the crux, or a "what would change my mind" that is too vague to check. Give one concrete example of how to fix it. Do not comment on whether their verdict is right, and do not argue for any side. 80 to 150 words, short paragraphs, no lists, no generic praise. If the learner says they do not understand the score, point to the part that lost the most points and explain what the rubric looked for there.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AICF - Practice finding the crux]]
notes:: Practice for parts 1 and 2 on the Gleave and Habryka debate, with tutor feedback.
## Lens:
source:: [[../Lenses/AICF - Gleave and Habryka on current safety techniques]]
notes:: The debate the crux practice is built on.
## Lens:
source:: [[../Lenses/AICF - Blocking monitors and early warning shots]]
notes:: Asks where Cheng and Li still disagree with Greenblatt, a smaller crux exercise.
## Lens:
source:: [[../Lenses/AICF - Should safety researchers quit frontier labs]]
notes:: Arguments and replies to weigh, with practice judging which replies hold.
## Lens:
source:: [[../Lenses/AICF - Do warning shots change policy]]
notes:: Evidence on the policy-response crux behind several of the unit's debates. Part 3 of the test is practised in the "Your view" inline lens at the end of the Unit 5 module, with tutor feedback.

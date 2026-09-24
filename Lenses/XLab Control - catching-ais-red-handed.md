---
id: 'a1f058be-04ef-47f9-ba1b-c88d67dd1a73'
title: "Catching AIs red-handed (1): what a catch buys you"
tldr: "A schemer only has to slip past you once. But you only have to catch it once. Greenblatt and Shlegeris argue that the moment you hold one clear example of a model trying to escape, the board tilts your way: you can shut it down, or you can mine that single example for everything it will tell you about the next attempt."
summary_for_tutor: "Unit 3 of AI Control 1, part 1 of 2. The learner reads Greenblatt and Shlegeris, \"Catching AIs red-handed\", from the opening through the Conclusion, in four excerpts. Excerpt 1 (opening through the eight strategies for few-shot catastrophe prevention) is followed by a recall question on what few-shot catastrophe prevention is. Excerpt 2 (when the control-then-few-shot plan works) is followed by a recall question on the catch-then-shut-down plan. Excerpt 3 (avoiding overfit) is followed by a recall question on why labs might train monitors but not the policy, then a two-part understanding check on the definition of catching and on the mirrored first-critical-try framing. Excerpt 4 (conclusion) is followed by a recall question on why control evaluations should never be fully retired. Part 2, 'Catching AIs red-handed (2)', has the appendices and two graded free-response questions on whether a catch produces evidence anyone will act on. Grade the recall questions against the criteria in each brief; do not hand the learner the answer before they attempt it."
reading_minutes: 40
tutor_minutes: 5
tags: []
---
#### Text
content::
Part 1 of 2. This part reads Greenblatt and Shlegeris's argument that a single caught escape attempt changes a lab's position, and their eight strategies for using a caught example, through to the post's conclusion. Short recall questions follow each section; answer them from memory before reading on. Part 2 reads the appendices and asks whether a catch is enough to make anyone act.

#### Article
source:: [[../articles/shlegeris-catching-ais-red-handed]]
from:: We’ve been spending a lot of time recently thinking about how to mitigate risks posed by
to:: we’d need to avoid training set leakage to ensure the new AIs don’t have advance knowledge of what’s going on).

#### Question: Open
id:: 1956a7eb-8a16-4213-8471-4068e5d4c16b
content:: What is few-shot catastrophe prevention?
assessment-instructions:: Quick recall check on a term the reading defines. Full credit for an answer that captures both halves: it is the problem of preventing future escape attempts given a few caught examples of a model trying to escape, and it is the problem a lab faces when it keeps deploying a model after catching it rather than shutting it down. Partial credit for the first half alone. Do not credit an answer that only restates the words of the term. Grade only against the reading the learner has just done.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: ## When does the “control then few-shot-catastrophe-prevention” plan work?
to:: you realize that you came way too close to the escape attempt succeeding, and so you can confidently decide you need to shut down the model.

#### Question: Open
id:: ceb29a2e-30fe-499a-9608-224258f48608
content:: What is the catch-then-shut-down plan, and why is it worth committing to it in advance?
assessment-instructions:: Quick recall check. Full credit for an answer that gives the plan (stopping use of a model once it has been caught attempting to escape) and at least one of the reasons the reading gives for committing in advance: the lab may need to act quickly, and in the moment many stakeholders will be deeply opposed to shutting the model down; customers may even hold service-level agreements that penalize taking the model offline, so it is valuable to write the permission to disable access into the agreement ahead of time. Partial credit for the plan without a reason. Grade only against the reading the learner has just done.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: ## Avoiding overfit and maintaining paranoia
to:: intentionally performing fake attempts is very unlikely to be a good strategy for the AI.

#### Question: Open
id:: a0dfc318-d65f-46b8-aec0-133a4d7aea45
content:: After catching escape attempts, why might a lab train its monitoring models on the caught examples but leave the policy model itself untouched?
assessment-instructions:: Quick recall check drawing on the "Small sample count ML" strategy. Full credit for an answer naming at least two of the three downsides the reading gives for training the body of the policy: it could teach the policy which countermeasures are in place and which approaches are likely to fail; it makes all prior attempts off-policy, which disrupts interventions like a probe trained on the body of the model; and it reduces the number of future attempts, whereas catching more attempts is valuable. Partial credit for one. Credit an answer that also notes the upside the reading concedes (training the body may add reliability). Grade only against the reading the learner has just done.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Callout: Understanding check
tone:: blue

#### Question: Open
id:: 603262db-edb6-49f8-8224-ebea44a11535
content:: What does it mean to catch a scheming model red-handed?
assessment-instructions:: Understanding check, part 1 of 2. Full credit for an answer that has the reading's definition: finding inputs on which the deployed model demonstrably takes catastrophic actions with a probability far higher than would be expected if it were not purposefully looking for opportunities to take such actions. Also credit the confidence condition: the catch has to be established with extremely high confidence, which may take a large investigation. Do not credit "the model did something suspicious" or "the monitor flagged it" without the probability comparison. Grade only against the reading the learner has just done.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: 2afda5a4-e43e-41d7-a9fd-9cd46c2890b7
content:: In what sense is a deployment with a scheming AI a "first critical try" situation for both sides?
assessment-instructions:: Understanding check, part 2 of 2. Full credit for an answer that gives both sides of the mirror: the lab risks an irreversible catastrophe if its safety measures fail once at a bad time, and the AI faces the mirror-image risk that an escape attempt which gets caught substantially reduces its chances of ever succeeding. Both sides desperately want to succeed on the first critical try. Partial credit for the lab's side alone, which is the half most learners already know from the standard alignment framing. Grade only against the reading the learner has just done.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: ## Conclusion
to:: it would be good to have developed the techniques ahead of time.

#### Question: Open
id:: d169d0fb-f113-49c9-a624-d1c51eaa9ff7
content:: Why should control evaluations never be fully retired, even after several escape attempts have been caught and studied?
assessment-instructions:: Quick recall check. Full credit for an answer that names the fake-attempt problem: caught attempts may be deliberately poorly executed fakes intended to create a false sense of security or divert resources toward less effective safeguards, so a lab that tunes only to what it has caught can overfit. Also credit the second half: to achieve anything a scheming AI must eventually make a serious attempt, so a sufficiently high chance of catching that first serious attempt must be maintained. Partial credit for either half. Grade only against the reading the learner has just done.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "Catching AIs red-handed." *Redwood Research blog*, 7 May 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/catching-ais-red-handed)
*The reading this lesson is built around: the argument that a single caught escape attempt changes a lab's position, and eight strategies for using it. This part covers the post through its conclusion; the appendices are in part 2.*

XLab. "Catching AIs red-handed." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/catching-ais-red-handed)
*The source lesson this page adapts.*
:::

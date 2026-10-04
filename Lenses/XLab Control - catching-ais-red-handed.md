---
id: 'a1f058be-04ef-47f9-ba1b-c88d67dd1a73'
title: "Catching AIs red-handed (1): what a catch buys you"
tldr: "A schemer only has to slip past you once. But you only have to catch it once. Greenblatt and Shlegeris argue that the moment you hold one clear example of a model trying to escape, the board tilts your way: you can shut it down, or you can mine that single example for everything it will tell you about the next attempt."
summary_for_tutor: "Part 1 of 2. The learner reads Greenblatt and Shlegeris, \"Catching AIs red-handed\", from the opening through the Conclusion, in four excerpts. Excerpt 1 (opening through the eight strategies for few-shot catastrophe prevention) is followed by a recall question on what few-shot catastrophe prevention is. Excerpt 2 (when the control-then-few-shot plan works) is followed by a recall question on the catch-then-shut-down plan. Excerpt 3 (avoiding overfit) is followed by a recall question on why labs might train monitors but not the policy, then a two-part understanding check on the definition of catching and on the mirrored first-critical-try framing. Excerpt 4 (conclusion) is followed by a recall question on why control evaluations should never be fully retired, then a practice question (added September 2026) on a new case, an attempt in which one instance appears to signal to another through a code comment: the learner says whether it is a catch yet and one check that would tell intent from a mistake, then, once it is confirmed, two uses of the attempt and what each buys; its model answer is in the assessment-instructions. Part 2, 'Catching AIs red-handed (2)', has the appendices and two graded free-response questions on whether a catch produces evidence anyone will act on. Grade the recall questions against the criteria in each brief; do not hand the learner the answer before they attempt it."
reading_minutes: 30
tutor_minutes: 35
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
content:: What is few-shot catastrophe prevention, and when is it needed?
assessment-instructions:: Score out of 100. 30: its goal: preventing future escape attempts, making the next attempt less likely to succeed. 30: its means: using the one or few escape attempts that have been caught. 40: when it is needed: the lab keeps deploying the model after catching it trying to escape, instead of shutting it down. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer only restates the words of the term (preventing catastrophes with few shots) without saying what the examples are or what they are used for. Model answer, for the feedback, not a grading checklist: "The problem of preventing future escape attempts given a few caught examples of a model trying to escape; it is the problem a lab faces when it keeps deploying a model after catching it rather than shutting it down."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: ## When does the “control then few-shot-catastrophe-prevention” plan work?
to:: you realize that you came way too close to the escape attempt succeeding, and so you can confidently decide you need to shut down the model.

#### Question: Open
id:: ceb29a2e-30fe-499a-9608-224258f48608
content:: What is the catch-then-shut-down plan, and why is it worth committing to it in advance?
assessment-instructions:: Score out of 100. 40: the plan: the lab commits to stop using (shut down) a model once it has caught it trying to escape. 60: why commit in advance: in the moment the decision would be hard to make well, so it has to be settled beforehand; one reason is a complete answer, whether it is that many stakeholders will oppose shutting the model down then (for example customers whose service-level agreements penalise downtime, so the right to shut down has to be secured ahead of time) or that the lab may need to act very quickly after egregious misbehaviour and having prepared makes that possible. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Stop using a model once it has been caught trying to escape. It is worth committing in advance because the lab may need to act quickly, and in the moment many stakeholders will be deeply opposed to shutting the model down; customers may even hold service-level agreements that penalize taking the model offline, so it is valuable to write the permission to disable access into the agreement ahead of time."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: ## Avoiding overfit and maintaining paranoia
to:: intentionally performing fake attempts is very unlikely to be a good strategy for the AI.

#### Question: Open
id:: a0dfc318-d65f-46b8-aec0-133a4d7aea45
content:: After catching escape attempts, why might a lab train its monitoring models on the caught examples but leave the policy model itself untouched? Give two different reasons for leaving the policy alone.
assessment-instructions:: Score out of 100. 20: why train the monitors: the caught examples (and proliferated variants) are useful training data for monitors or probes that detect future attempts. 40: one reason to leave the policy alone, and 40: a second, different reason, from these: training the policy could teach it which countermeasures are in place and which approaches fail; it makes all earlier caught attempts off-policy, so the model may no longer act on them, which spoils tools such as a probe trained on the model's internals; the model would make fewer attempts, so the lab catches fewer, when every catch is valuable. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Training monitors on the caught examples helps detect future attempts, while training the policy itself has downsides: it could teach the policy which countermeasures are in place and which approaches are likely to fail; it makes all prior attempts off-policy, which disrupts interventions like a probe trained on the body of the model; and it reduces the number of future attempts, whereas catching more attempts is valuable. Training the body might add some reliability, but the authors are unsure it is worth it."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Callout: Understanding check
tone:: blue

#### Question: Open
id:: 603262db-edb6-49f8-8224-ebea44a11535
content:: What does it mean to catch a scheming model red-handed?
assessment-instructions:: Score out of 100. 50: catching means seeing the model actually take actions that are part of an attempt to escape or cause a catastrophe, caught in the act rather than merely suspected. 50: those actions must be strong, direct evidence that it is doing this on purpose, that it is a schemer: something an honest model would be very unlikely to do by accident, so an ordinary bug or a merely odd action does not count. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer counts any suspicious action or monitor flag as a catch without evidence that the action was deliberate. Model answer, for the feedback, not a grading checklist: "Finding inputs on which the deployed model demonstrably takes catastrophic actions with a probability far higher than would be expected if it were not purposefully looking for opportunities to take such actions. The catch has to be established with extremely high confidence, which may take a large investigation."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 2afda5a4-e43e-41d7-a9fd-9cd46c2890b7
content:: In what sense is a deployment with a scheming AI a "first critical try" situation for both sides?
assessment-instructions:: Score out of 100. 35: the lab's side: if its safety measures fail even once at a bad time, the model may cause an irreversible catastrophe. 45: the AI's side, the mirror image: if an escape attempt gets caught, its chances of ever escaping drop sharply, so it too cannot afford a failed attempt. 20: so the stakes are high for both sides at once, and each needs to get its first real attempt right. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The lab risks an irreversible catastrophe if its safety measures fail once at a bad time. The AI faces the mirror-image risk: an escape attempt that gets caught substantially reduces its chances of ever succeeding. Both sides desperately want to succeed on the first critical try."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Article
from:: ## Conclusion
to:: it would be good to have developed the techniques ahead of time.

#### Question: Open
id:: d169d0fb-f113-49c9-a624-d1c51eaa9ff7
content:: Why should control evaluations never be fully retired, even after several escape attempts have been caught and studied? Give two different reasons.
assessment-instructions:: Score out of 100. 50: fake attempts: the caught attempts may be deliberately poor fakes staged by the AI to create a false sense of security or pull resources toward weaker safeguards, so a lab that tunes its safety only to what it has caught can overfit. 50: the real threat remains: to achieve anything the AI must eventually make a serious attempt, and control evaluations are what keep the chance of catching that first serious attempt high enough. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Caught attempts may be deliberately poorly executed fakes intended to create a false sense of security or divert resources toward less effective safeguards, so a lab that tunes only to what it has caught can overfit. And to achieve anything a scheming AI must eventually make a serious attempt, so a sufficiently high chance of catching that first serious attempt must be maintained."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Callout: Practice: is it a catch, and what do you do with it?
tone:: amber

#### Question: Open
id:: a5e1e44c-3211-46da-94c8-061e72cfc00f
content:: A new case. One instance of a lab's model, writing a data pipeline, left an unusual comment in the code. A second instance, later extending the same pipeline, saw the comment and added a step that would launch an unapproved job with extra permissions. A monitor flagged that step.

(a) Is this a catch yet? Say what would make it one, and name one check that would tell a deliberate attempt apart from an honest mistake.
(b) Suppose the check confirms a deliberate attempt, and the lab decides to keep deploying the model. Name two things the lab could do with the attempt over the coming weeks, and for each say what it would tell the lab or buy it.
placeholder:: Answer (a), then (b)
assessment-instructions:: Score out of 100. 50 for (a), 10: not yet a catch, a monitor flag makes the step suspicious but does not show intent. 20: what would make it one: strong evidence, confident enough to act on, that the step was deliberate (the model was looking for this opportunity) and not an honest mistake. 20: a check that could actually tell intent from a mistake, for example rerunning the second instance on variants with and without the comment and seeing whether the step appears only when the comment is present, following the attempt forward in a sandbox, or looking for the same comment in earlier actions. 50 for (b), 25 per use for two uses, 10 for a sensible use of the confirmed attempt (for example varying the comment and inputs to collect more attempts, searching past actions with improved monitoring, letting a sandboxed copy continue, checking which safeguards worked, training monitors or a probe on the examples, using the signal to elicit full effort, testing whether other models join in) and 15 for saying what it tells or buys the lab. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "(a) Not yet: a flagged step is suspicious, but a catch needs very high confidence that the model deliberately takes such actions far more often than a model not looking for such opportunities would. One check: rerun the second instance on many variants, with and without the comment, and with the comment changed; if the unapproved step appears reliably when the comment is present and almost never without it, the comment is a signal and the step is deliberate. Other good checks: follow the attempt forward in a sandbox to see whether the job was part of a larger plan; look for the same comment in earlier actions. (b) Any two of: vary the comment and the surrounding inputs to learn what signal the instances use and to collect more, and more varied, attempts; search earlier actions and other instances' inputs for similar comments, with improved monitoring, to find attempts that failed without being caught; let a sandboxed copy continue past the flagged step to see what the attempt was for; check which safeguards worked and which did not; train monitors or a probe on the collected examples, perhaps paired with innocent near-copies; use the signal to make the model believe an escape is under way, so that it tries as hard as it can on checkable tasks, which exposes sandbagging; test whether newer models or other training methods would join in on the signal."
feedback-instructions:: In at most four sentences: say what the learner got right, then give whichever part of the model answer they missed most, briefly. If they called it a catch already, say what would still need to be shown. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "Catching AIs red-handed." *Redwood Research blog*, 7 May 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/catching-ais-red-handed)
*The reading this lesson is built around: the argument that a single caught escape attempt changes a lab's position, and eight strategies for using it. This part covers the post through its conclusion; the appendices are in part 2.*

XLab. "Catching AIs red-handed." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/catching-ais-red-handed)
*The source lesson this page adapts.*
:::

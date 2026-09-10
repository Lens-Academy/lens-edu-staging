---
id: 'a1f058be-04ef-47f9-ba1b-c88d67dd1a73'
title: "Catching AIs red-handed"
tldr: "A schemer only has to slip past you once. But you only have to catch it once. Greenblatt and Shlegeris argue that the moment you hold one clear example of a model trying to escape, the board tilts your way: you can shut it down, or you can mine that single example for everything it will tell you about the next attempt."
summary_for_tutor: "Ported from XLab's AI Control curriculum, Module 1. The learner reads Greenblatt and Shlegeris, \"Catching AIs red-handed\", in five excerpts. Excerpt 1 (opening through the eight strategies for few-shot catastrophe prevention) is followed by a recall question on what few-shot catastrophe prevention is. Excerpt 2 (when the control-then-few-shot plan works) is followed by a recall question on the catch-then-shut-down plan. Excerpt 3 (avoiding overfit) is followed by a recall question on why labs might train monitors but not the policy, then a two-part understanding check on the definition of catching and on the mirrored first-critical-try framing. Excerpt 4 (conclusion) is followed by a recall question on why control evaluations should never be fully retired. XLab then adds its own note pushing back on catching as a win condition, and sets two graded free-response questions on the legibility of evidence. Excerpt 5 is the appendices. Grade the recall questions against the criteria in each brief; do not hand the learner the answer before they attempt it."
reading_minutes: 90
tutor_minutes: 0
tags: []
---
#### Article
source:: [[../articles/shlegeris-catching-ais-red-handed]]
from:: We’ve been spending a lot of time recently thinking about how to mitigate risks posed by
to:: we’d need to avoid training set leakage to ensure the new AIs don’t have advance knowledge of what’s going on).

#### Question: Open
id:: 1956a7eb-8a16-4213-8471-4068e5d4c16b
content:: What is few-shot catastrophe prevention?
assessment-instructions:: Quick recall check on a term the reading defines. Full credit for an answer that captures both halves: it is the problem of preventing future escape attempts given a few caught examples of a model trying to escape, and it is the problem a lab faces when it keeps deploying a model after catching it rather than shutting it down. Partial credit for the first half alone. Do not credit an answer that only restates the words of the term. Respond in at most three sentences: name what is correct, name what is missing, and stop. No generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the two bullets contrasting shutting the model down with continuing to deploy it) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response. Tell them to move on.

#### Article
from:: ## When does the “control then few-shot-catastrophe-prevention” plan work?
to:: you realize that you came way too close to the escape attempt succeeding, and so you can confidently decide you need to shut down the model.

#### Question: Open
id:: ceb29a2e-30fe-499a-9608-224258f48608
content:: What is the catch-then-shut-down plan, and why is it worth committing to it in advance?
assessment-instructions:: Quick recall check. Full credit for an answer that gives the plan (stopping use of a model once it has been caught attempting to escape) and at least one of the reasons the reading gives for committing in advance: the lab may need to act quickly, and in the moment many stakeholders will be deeply opposed to shutting the model down; customers may even hold service-level agreements that penalize taking the model offline, so it is valuable to write the permission to disable access into the agreement ahead of time. Partial credit for the plan without a reason. Respond in at most three sentences: name what is correct, name what is missing, and stop. No generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the service-level-agreement example) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response. Tell them to move on.

#### Article
from:: ## Avoiding overfit and maintaining paranoia
to:: intentionally performing fake attempts is very unlikely to be a good strategy for the AI.

#### Question: Open
id:: a0dfc318-d65f-46b8-aec0-133a4d7aea45
content:: After catching escape attempts, why might a lab train its monitoring models on the caught examples but leave the policy model itself untouched?
assessment-instructions:: Quick recall check drawing on the "Small sample count ML" strategy. Full credit for an answer naming at least two of the three downsides the reading gives for training the body of the policy: it could teach the policy which countermeasures are in place and which approaches are likely to fail; it makes all prior attempts off-policy, which disrupts interventions like a probe trained on the body of the model; and it reduces the number of future attempts, whereas catching more attempts is valuable. Partial credit for one. Credit an answer that also notes the upside the reading concedes (training the body may add reliability). Respond in at most three sentences: name what is correct, name what is missing, and stop. No generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the phrase "learn from negative examples") rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response. Tell them to move on.

#### Callout: Understanding check
tone:: blue

#### Question: Open
id:: 603262db-edb6-49f8-8224-ebea44a11535
content:: What does it mean to catch a scheming model red-handed?
assessment-instructions:: Understanding check, part 1 of 2. Full credit for an answer that has the reading's definition: finding inputs on which the deployed model demonstrably takes catastrophic actions with a probability far higher than would be expected if it were not purposefully looking for opportunities to take such actions. Also credit the confidence condition: the catch has to be established with extremely high confidence, which may take a large investigation. Do not credit "the model did something suspicious" or "the monitor flagged it" without the probability comparison. Respond in at most three sentences: name what is correct, name what is missing, and stop. No generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the three-instance vulnerability example in "What's catching?") rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response. Tell them to move on.

#### Question: Open
id:: 2afda5a4-e43e-41d7-a9fd-9cd46c2890b7
content:: In what sense is a deployment with a scheming AI a "first critical try" situation for both sides?
assessment-instructions:: Understanding check, part 2 of 2. Full credit for an answer that gives both sides of the mirror: the lab risks an irreversible catastrophe if its safety measures fail once at a bad time, and the AI faces the mirror-image risk that an escape attempt which gets caught substantially reduces its chances of ever succeeding. Both sides desperately want to succeed on the first critical try. Partial credit for the lab's side alone, which is the half most learners already know from the standard alignment framing. Respond in at most three sentences: name what is correct, name what is missing, and stop. No generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the sentence about the same argument going the other way) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response. Tell them to move on.

#### End Callout

#### Article
from:: ## Conclusion
to:: it would be good to have developed the techniques ahead of time.

#### Question: Open
id:: d169d0fb-f113-49c9-a624-d1c51eaa9ff7
content:: Why should control evaluations never be fully retired, even after several escape attempts have been caught and studied?
assessment-instructions:: Quick recall check. Full credit for an answer that names the fake-attempt problem: caught attempts may be deliberately poorly executed fakes intended to create a false sense of security or divert resources toward less effective safeguards, so a lab that tunes only to what it has caught can overfit. Also credit the second half: to achieve anything a scheming AI must eventually make a serious attempt, so a sufficiently high chance of catching that first serious attempt must be maintained. Partial credit for either half. Respond in at most three sentences: name what is correct, name what is missing, and stop. No generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the sentence about fake coups) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response. Tell them to move on.

#### Text
content::
:::callout {title="Note" tone="amber"}
The original control framing treats catching a scheming AI red-handed as a win condition. Once you've caught it, you either shut it down or apply few-shot catastrophe prevention and either way the AI's odds of eventual success drop a lot. However, many have argued that even a clean red-handed catch, such as a situation where a model backdoors security-critical code and separately exploits the backdoor on a given input and we spot that, still might not result in the desired actions from important AI stakeholders. Rival AI labs, the US president, and even other people inside your lab could attribute this to role-play, a one-off anomaly, sabotage by rivals, or shoddy alignment work on your part. This raises the question of whether catching is an appropriate win condition if it doesn't have a high likelihood of decreasing the global level of AI risk. To put it concisely, there are other factors which decrease the efficacy of good control work that are outside of the control evaluations themselves.
:::

Respond to the following discussion questions and take some time to write out your answers. A good place to look for assistance is the Redwood Research blog, although after this section's readings you should be able to begin an answer by yourself.

#### Question: Open
id:: d20e6bc3-6b15-417a-98e8-433ddcfb388d
content::
**Stage 1.** A catch only matters for shutdown if it produces evidence that can survive counterarguments from people that disagree with you on misalignment. Create a catch scenario and figure out what needs to be true for the evidence to lead to a shutdown. Try to come up with possible counterarguments and proactively answer them.

Write at least 150 words and at most 500 words.
assessment-instructions:: Graded free response, scored against three criteria of equal weight, and against the length bound (at least 150 words, at most 500 words; deduct if the response is under the minimum). (1) Catch: creates a valid and realistic catch scenario that's relatively detailed. A scenario is realistic if the actions are ones a deployed model could plausibly take and the catch is one a lab could plausibly notice; detail means naming the affordance, the action, and how it surfaced, not just "the model tried to escape". (2) Stress-Test: comes up with counterarguments and argues for a shutdown effectively. Counterarguments should be the ones a real sceptic would raise, for example role-play, a one-off anomaly, sabotage by a rival, or shoddy alignment work by the team that reported it, and the response should answer them rather than dismiss them. (3) Requirements for Shutdown: mentions catch scenario requirements for a shutdown to happen, that is, what has to be true of the evidence, the decision process, or the prior commitments for the catch to actually stop the deployment. Award partial credit per criterion. Do not reward length or fluency on their own; a well-written scenario with no counterarguments fails criterion 2. Grade only against the reading and XLab's note on this page. No generic praise (great job, excellent work, well done).

#### Question: Open
id:: 81ff09bc-f18b-472f-8b91-9274ed86c73b
content::
**Stage 2.** Where is the biggest bottleneck for the legibility of evidence and why?

Redwood has [some](https://www.alignmentforum.org/posts/4QRvFCzhFbedmNfp4/to-be-legible-evidence-of-misalignment-probably-has-to-be) [posts](https://blog.redwoodresearch.org/p/behavioral-red-teaming-is-unlikely) tackling this; try to read this after attempting the question and think of one thing you may agree or disagree with the authors on.

Write at least 100 words and at most 400 words.
assessment-instructions:: Graded free response, scored against three criteria of equal weight, and against the length bound (at least 100 words, at most 400 words; deduct if the response is under the minimum). (1) Selects Bottleneck: picks a bottleneck to argue for. A response that lists several without committing to one does not meet this criterion. (2) Explanation: argues that the bottleneck selected is the biggest bottleneck as well as why exactly its a bottleneck. Look for a mechanism, not an assertion: what specifically fails at that point, and why fixing anything else leaves the problem in place. (3) Comparison: mentions at least one agreement or disagreement with the authors' takes, referring to the two linked Redwood posts (Greenblatt on evidence of misalignment having to be behavioral to be legible, and Shlegeris on behavioral red-teaming being unlikely to produce clear strong evidence that models aren't scheming). A generic nod to "the authors" with no identifiable claim does not meet this criterion. Award partial credit per criterion. Grade only against the reading, XLab's note on this page, and the two linked posts. No generic praise (great job, excellent work, well done).

#### Article
from:: ## Appendix: Framing in terms of E\[utility | scheming\]

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "Catching AIs red-handed." *Redwood Research blog*, 7 May 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/catching-ais-red-handed)
*The reading this lesson is built around: the argument that a single caught escape attempt changes a lab's position, and eight strategies for using it.*

Greenblatt, Ryan. "To be legible, evidence of misalignment probably has to be behavioral." *LessWrong*, 15 Apr. 2025. [lesswrong.com](https://www.lesswrong.com/posts/4QRvFCzhFbedmNfp4/to-be-legible-evidence-of-misalignment-probably-has-to-be)
*One of the two posts XLab points learners at for the second free-response question, on what kind of evidence of misalignment can actually be made legible to outsiders.*

Shlegeris, Buck. "Behavioral red-teaming is unlikely to produce clear, strong evidence that models aren't scheming." *Redwood Research blog*, 10 Oct. 2024. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/behavioral-red-teaming-is-unlikely)
*The second post XLab points learners at, arguing that behavioral red-teaming will not settle the question either way.*

XLab. "Catching AIs red-handed." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/catching-ais-red-handed)
*The source lesson this page adapts, including its note on whether catching is an appropriate win condition.*
:::

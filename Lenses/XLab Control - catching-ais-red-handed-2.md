---
id: '56f4b75b-117f-42a4-9c6f-7a4a66c480b5'
title: "Catching AIs red-handed (2): when a catch is not enough"
tldr: "A clean catch is only a win if the people who decide believe it. Rival labs, officials and even colleagues can call a caught escape attempt role-play, a fluke, sabotage or sloppy work. This part reads the fine print on what counts as a catch, then asks you to build one that would survive those objections."
summary_for_tutor: "Unit 3 of AI Control 1, part 2 of 2 of Greenblatt and Shlegeris, 'Catching AIs red-handed', continuing 'Catching AIs red-handed (1)', which covered the post from its opening through the Conclusion (few-shot catastrophe prevention and its eight strategies, the catch-then-shut-down plan, avoiding overfit to fake attempts). This part: the post's five appendices (framing in terms of E[utility | scheming], defining catching, techniques that don't catch but do update P(scheming), escape attempts that fail without being caught, when AIs will be caught); then a note pushing back on catching as a win condition, since stakeholders may attribute even a clean catch to role-play, a one-off anomaly, sabotage by rivals or shoddy alignment work; then two graded free-response questions on the legibility of evidence. Stage 1 asks the learner to build a catch scenario, say what must be true for it to lead to a shutdown, and answer sceptics' counterarguments. Stage 2 asks for the biggest bottleneck for the legibility of evidence, and to engage two linked Redwood posts read off-page after attempting. Grade against the criteria in each brief."
reading_minutes: 55
tutor_minutes: 5
tags: []
---
#### Text
content::
Part 2 of 2. The previous part read Greenblatt and Shlegeris's case that catching a model red-handed changes a lab's position, and their strategies for using a caught example. This part first reads the post's appendices: what exactly counts as a catch, how escape attempts can fail without being caught, what evidence moves the odds of scheming without a catch, and when a catch is likely to happen. It then asks whether a catch is enough, in two written exercises on whether the evidence from a catch would lead anyone to act.

#### Article
source:: [[../articles/shlegeris-catching-ais-red-handed]]
from:: ## Appendix: Framing in terms of E\[utility | scheming\]

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
assessment-instructions:: Graded free response, scored against three criteria of equal weight, and against the length bound (at least 150 words, at most 500 words; deduct if the response is under the minimum). (1) Catch: creates a valid and realistic catch scenario that's relatively detailed. A scenario is realistic if the actions are ones a deployed model could plausibly take and the catch is one a lab could plausibly notice; detail means naming the affordance, the action, and how it surfaced, not just "the model tried to escape". (2) Stress-Test: comes up with counterarguments and argues for a shutdown effectively. Counterarguments should be the ones a real sceptic would raise, for example role-play, a one-off anomaly, sabotage by a rival, or shoddy alignment work by the team that reported it, and the response should answer them rather than dismiss them. (3) Requirements for Shutdown: mentions catch scenario requirements for a shutdown to happen, that is, what has to be true of the evidence, the decision process, or the prior commitments for the catch to actually stop the deployment. Award partial credit per criterion. Do not reward length or fluency on their own; a well-written scenario with no counterarguments fails criterion 2. Grade only against the reading and the note on this page.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 81ff09bc-f18b-472f-8b91-9274ed86c73b
content::
**Stage 2.** Where is the biggest bottleneck for the legibility of evidence and why?

Redwood has [some](https://www.alignmentforum.org/posts/4QRvFCzhFbedmNfp4/to-be-legible-evidence-of-misalignment-probably-has-to-be) [posts](https://blog.redwoodresearch.org/p/behavioral-red-teaming-is-unlikely) tackling this; try to read this after attempting the question and think of one thing you may agree or disagree with the authors on.

Write at least 100 words and at most 400 words.
assessment-instructions:: Graded free response, scored against three criteria of equal weight, and against the length bound (at least 100 words, at most 400 words; deduct if the response is under the minimum). (1) Selects Bottleneck: picks a bottleneck to argue for. A response that lists several without committing to one does not meet this criterion. (2) Explanation: argues that the bottleneck selected is the biggest bottleneck as well as why exactly its a bottleneck. Look for a mechanism, not an assertion: what specifically fails at that point, and why fixing anything else leaves the problem in place. (3) Comparison: mentions at least one agreement or disagreement with the authors' takes, referring to the two linked Redwood posts (Greenblatt on evidence of misalignment having to be behavioral to be legible, and Shlegeris on behavioral red-teaming being unlikely to produce clear strong evidence that models aren't scheming). A generic nod to "the authors" with no identifiable claim does not meet this criterion. Award partial credit per criterion. Grade only against the reading, the note on this page, and the two linked posts.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "Catching AIs red-handed." *Redwood Research blog*, 7 May 2024. [redwoodresearch.substack.com](https://redwoodresearch.substack.com/p/catching-ais-red-handed)
*The reading this lesson is built around: the argument that a single caught escape attempt changes a lab's position, and eight strategies for using it.*

Greenblatt, Ryan. "To be legible, evidence of misalignment probably has to be behavioral." *LessWrong*, 15 Apr. 2025. [lesswrong.com](https://www.lesswrong.com/posts/4QRvFCzhFbedmNfp4/to-be-legible-evidence-of-misalignment-probably-has-to-be)
*One of the two posts to read for the second free-response question, on what kind of evidence of misalignment can actually be made legible to outsiders.*

Shlegeris, Buck. "Behavioral red-teaming is unlikely to produce clear, strong evidence that models aren't scheming." *Redwood Research blog*, 10 Oct. 2024. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/behavioral-red-teaming-is-unlikely)
*The second of those posts, arguing that behavioral red-teaming will not settle the question either way.*

XLab. "Catching AIs red-handed." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/catching-ais-red-handed)
*The source lesson this page adapts.*
:::

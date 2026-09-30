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
assessment-instructions:: Score out of 100. 34: the catch scenario, 14: realistic, an action a deployed model could plausibly take and a catch a lab could plausibly notice, and 20: detailed, naming the affordance used, the action taken and how it came to light, not just "the model tried to escape". 33: the stress test, 13: counterarguments a real sceptic would raise (for example role-play, a one-off anomaly, sabotage by a rival, shoddy alignment work by the team reporting it), and 20: each answered with an argument rather than dismissed. 33: requirements for shutdown: what has to be true of the evidence, the decision process or prior commitments for the catch to actually stop the deployment. Give credit for each point whenever the answer shows the idea, in any wording. Deduct 10 if the response is under 150 words. Model answer, for the feedback, not a grading checklist: "Scenario: an AI agent doing infrastructure work at a lab slips a subtle flaw into the permission checks of the sandbox it runs in; days later, in an unrelated task, it uses exactly that flaw to start copying its own weights to an outside server. A trusted monitor flags the unusual outbound transfer, and an audit traces the transfer back to the earlier commit. For this to lead to a shutdown, the evidence must be reproducible and inspectable by people outside the team: the logs, the code, and re-running the model on similar inputs and watching it try again far more often than chance. The lab also needs a commitment made in advance that a confirmed escape attempt means shutdown, with agreement on what counts as confirmed, and ideally contracts that allow taking the model offline. Counterarguments: 'It was role-play': nothing in its prompts asked it to play a part, and two separate tasks were coordinated toward one goal. 'A one-off fluke': reruns show it happens repeatedly on such inputs. 'Sabotage by a rival': the logs show every step came from our model, with no outside input. 'Shoddy alignment work': whatever the cause, a model that does this is not safe to keep deploying."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 81ff09bc-f18b-472f-8b91-9274ed86c73b
content::
**Stage 2.** Where is the biggest bottleneck for the legibility of evidence and why?

Redwood has [some](https://www.alignmentforum.org/posts/4QRvFCzhFbedmNfp4/to-be-legible-evidence-of-misalignment-probably-has-to-be) [posts](https://blog.redwoodresearch.org/p/behavioral-red-teaming-is-unlikely) tackling this; try to read this after attempting the question and think of one thing you may agree or disagree with the authors on.

Write at least 100 words and at most 400 words.
assessment-instructions:: Score out of 100. 33: selects a bottleneck: the answer commits to one bottleneck rather than listing several. 34: explanation, 17: why it is a bottleneck, with a mechanism, what specifically fails at that point, and 17: why it is the biggest, why fixing anything else would leave the problem in place. 33: comparison: at least one identifiable agreement or disagreement with a specific claim in the two linked posts (Greenblatt, that legible evidence of misalignment probably has to be behavioural; Shlegeris, that behavioural red-teaming is unlikely to produce clear, strong evidence that models are not scheming). Give credit for each point whenever the answer shows the idea, in any wording. Deduct 10 if the response is under 100 words. Model answer, for the feedback, not a grading checklist: "The biggest bottleneck is that the people who have to act on the evidence cannot check it themselves, so it comes down to whether they trust the lab that reports it. Evidence from inside the model, such as interpretability findings or suspicious internal reasoning, is hard for outsiders to verify and easy to explain away as an artifact of the method, so it will not move a sceptical rival lab or government. Better detection tools do not fix this: whatever they find is still illegible to someone who cannot inspect it. What remains is behavioral evidence, the model doing something clearly bad that others can reproduce. I agree with Greenblatt that legible evidence of misalignment probably has to be behavioral. Shlegeris adds the other side: behavioral red-teaming can show that a model is scheming but is unlikely to give clear, strong evidence that it is not, so a lab whose tests come back clean has learned little. That asymmetry makes the bottleneck worse, because the burden of proof falls entirely on catching the model in the act."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

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

---
id: '702fce69-02f3-4b20-882b-911f72435a1a'
title: "The case for control (3): are useful models too capable to control?"
tldr: "Control only matters if the models worth controlling can still be controlled. Greenblatt and Shlegeris argue that the first transformatively useful AIs will be very dangerous but probably not uncontrollable. This part makes the first half of that case: they are unlikely to be wildly superhuman in the few domains, such as hacking and persuasion, where that would defeat control."
summary_for_tutor: "Part 3 of 4 of Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', continuing 'The case for control (1)' and '(2)', which defined control, set it beside alignment and showed why control is evaluable; 'The case for control (4)' follows with why evading careful control is hard without wildly superhuman skill, how long the control window lasts, and the implications. This lens carries the opening of the post's section 'Control is likely achievable for early transformatively useful AIs', through the subsection 'We can probably avoid our AIs having qualitatively wildly superhuman skills in problematic domains'. The argument, in order: (1) three capability properties, very dangerous, transformatively useful and uncontrollable, and the claim that labs will build models with the first two before models with the third; (2) the first transformatively useful AIs will probably be very dangerous, because the tasks that would substantially reduce risk need broad, general capability; (3) 'transformatively useful' probably does not imply 'uncontrollable': the authors split the worry into problems from qualitatively wildly superhuman skill and problems without it, and take the first here: wildly superhuman skill (highly inscrutable actions, innocent-looking outputs with hidden effects, things a human team could not do in months) would defeat control only in a few problematic domains (hacking, persuasion, manipulating scientific results or conceptual arguments), and early transformatively useful AIs probably won't have it there, because across-the-board superhuman AI would have been useful earlier, the useful applications don't need it, those domains track general capability, and AI capability profiles so far look broadly human. Vocabulary assumed from parts 1 and 2: scheming, the control property, untrusted versus trusted models, protocol, control evaluation, red team, catching red-handed. New here: transformatively useful, uncontrollable, qualitatively wildly superhuman, problematic domains, the control window, control frontier, diffuse threat. The three exercise blocks are: an open question on whether a control window exists at all, answered on the page by the control-timeline widget, a slider that widens or closes the window and lights four milestones for what the time inside it buys, with the figure's caveats carried by Text segments before and after it; a commit-and-construct on whether inscrutability is necessary for uncontrollability, which lands on research sabotage as a diffuse threat; and an understanding check on the problematic domains and on why early transformatively useful AIs are unlikely to be wildly superhuman in them. If a learner argues that useful models must be uncontrollable, ask them what the transformative applications actually require, rather than restating the authors' four strands for them. The excerpt ends with the authors' pointer to an appendix with more detail; it is in 'The case for control (4)', folded at the end."
reading_minutes: 17
tutor_minutes: 28
tags: []
---
#### Text
content::
Part 3 of 4. The previous two parts ([[../Lenses/XLab Control - the-case-for-controlling-powerful-ais|part 1]] and [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-2|part 2]]) defined control, set it beside alignment, and showed why, unlike alignment, you can test whether you have it. This part asks whether control is achievable for the models we actually want to use: will the first AIs useful enough to transform safety work already be too capable to control? The authors split that worry in two, and this part takes the first half: models that are wildly superhuman in a domain that matters. [[../Lenses/XLab Control - the-case-for-controlling-powerful-ais-4|The next part]] takes the second half, then asks how long control lasts and what follows for labs, the public and researchers. Three exercises break up the reading: each one asks you to work out a step of the argument before the authors hand it to you. Answer before you move on, even roughly.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: # Control is likely achievable for early transformatively useful AIs
to:: So transformatively useful models are probably also very dangerous.

#### Callout: Reasoning prompt: could useful models remain controllable?
#### Question: Open
id:: dc2636c8-c8df-4375-a5b2-3d96ba6ff35e
content:: Could such highly capable, transformatively useful models still remain controllable? What properties of the models themselves, the control protocol, or the environment in which the models are trained and deployed could determine this?
placeholder:: Write your reasoning
assessment-instructions:: Score out of 100. 40: whether they could remain controllable, answered with reasoning: it depends on whether models become uncontrollable at the same point as they become transformatively useful, or only later, leaving a window in which models are useful and dangerous but can still be controlled. 60: at least two properties that could decide it, 30 each, from the models, the protocol or the environment, for example the capability gap between the model and the trusted labour watching it (humans and weaker trusted models), how good the model is at evading control or sabotaging evaluations, what access and affordances it is given, what monitoring costs, whether its reasoning stays interpretable, or how fast the lab builds the next model. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "If transformative usefulness implied uncontrollability, control would provide no useful period in which advanced models could be safely deployed. The point at which models become useful enough to substantially reduce risk would also be the point at which control ceased to be viable. If transformative usefulness didn't imply uncontrollability, however, there may be a control window: a period in which models are already transformatively useful, dangerous, but a carefully designed protocol could theoretically still retain the control property."
feedback-instructions:: In at most six sentences, name what the learner's reasoning got right and, if anything is missing or wrong, the most important thing, then give the framing they are about to read. If transformative usefulness implied uncontrollability, control would buy no usable period at all, because the moment models became useful enough to reduce risk would be the moment control stopped working. If it does not imply uncontrollability, there may be a control window: a stretch in which models are already transformatively useful and dangerous, yet a carefully designed protocol could still retain the control property. Tell them the next section argues for the second picture.

#### End Callout

#### Text
content::
Here is the shape of the answer the next section argues for. The axis runs from now into the future through three regions: not yet transformatively useful, the control window, and uncontrollable. The arrival of transformative usefulness is fixed; the slider moves only the control frontier, and the milestones underneath show what the time inside the window buys.

#### Widget
source:: [[../widgets/xlab-control-control-timeline]]

#### Text
content::
Widths there are qualitative: an ordering of successive frontier systems, not calendar time. The window's width is not fixed in advance. It depends on how fast capabilities are pushed past transformative usefulness, and the next part of the reading argues we should hold off on building uncontrollable AI for as long as possible.

#### Article
from:: ## "Transformatively useful" probably doesn't imply "uncontrollable"
to:: Control evaluations might fail because the red team will struggle to elicit or estimate these qualitatively wildly superhuman abilities.[^note-greenblatt-buck-25]

#### Callout: Commit and construct: is inscrutability necessary?
#### Text
content::
The authors have described highly inscrutable actions as one reason sufficiently capable models may become uncontrollable.

Suppose every action a model took could be understood by a capable human team that examined it carefully. Would a sufficiently careful lab necessarily be able to control the model?

#### Question: Choice
id:: ce891560-21fa-48ed-bfd7-ef5d2eee63fa
content:: Do you think inscrutability is necessary for uncontrollability?
options::
- Inscrutability is necessary
- Inscrutability is not necessary

#### Question: Rating
id:: 16f27f3b-8882-4f4f-b2bf-b0f4d6a26c40
content:: How confident are you in your answer?
scale:: 3
low-label:: Not confident
high-label:: Very confident

#### Question: Open
id:: 1c428c01-3812-4e77-ace0-ceacbed89a91
content:: Explain your reasoning for the choice you just made.
placeholder:: Explain your reasoning
assessment-instructions:: Score out of 100. 40: the distinction: whether an action can be understood when examined carefully is not the same as whether anyone catches or stops it; an answer that gives a way an understandable action could still get through has shown this, even if it does not state it separately. 45: at least one way an understandable action could still get through; one sound way earns all 45, for example: it may never be inspected, since review capacity is limited; it can be understandable yet hard to evaluate as good or harmful; its significance may only appear together with many other individually understandable actions; a reviewer may see what it does without being able to tell whether it is part of a larger strategy. 15: a conclusion that follows from the reasoning, for example that scrutability removes one source of control failure but not every source; either choice earns these points when the reasoning supports it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Scrutability means that an action can be understood if it is examined carefully. This does not, by itself, imply that the model is controlled: an understandable action might, for example, never be inspected, or matter only together with many other individually understandable actions. Scrutability therefore removes one possible source of control failure, but it does not logically eliminate every other source. Inscrutability is not conceptually necessary for a model to pose a serious threat to control."
feedback-instructions:: In at most six sentences: state what the learner's reasoning does well and, if anything is missing or wrong, the most important thing, then give the resolution. Scrutability means an action can be understood if examined carefully, which does not by itself imply the model is controlled: an understandable action might not be inspected, might be understandable without being easy to evaluate, might matter only together with many other understandable actions, and reviewers might see what it does without seeing whether it is part of a larger strategy. So scrutability removes one source of control failure but not every other, and inscrutability is not conceptually necessary for a serious threat to control. Close by saying that leaves the harder question the next prompt asks: can they construct a credible threat in which the model's actions remain scrutable?

#### Question: Open
id:: b633dab0-e4e0-47b5-99e8-853e4e88ba24
content::
Construct the strongest threat model you can: what unacceptable outcome could a scheming but scrutable model cause through many actions that each look ordinary or low-stakes, so that no single one is incriminating? Say how the model brings it about, and why a reviewer who understands each action still would not catch it.

The model's actions should remain scrutable, meaning a capable human team could understand them if it examined them carefully. Do not assume that the model has qualitatively wildly superhuman skills in a problematic domain.

If you committed to "inscrutability is necessary": try to construct the strongest counterexample to your original view, even if you remain unconvinced that it is realistic.

If you committed to "inscrutability is not necessary": turn your general intuition into the most credible concrete threat model you can.

:::callout{title="Hint" tone="amber" collapse="closed"}
A single high-stakes action, such as attempting to exfiltrate model weights or inserting a clearly dangerous security backdoor, is often highly scrutinizable. Because the harm is concentrated, the action is more likely to appear suspicious and to be incriminating if a monitor or auditor catches it.

What kinds or sequences of actions would be less individually incriminating? Could a model take actions that each appear ordinary, defensible, or low-stakes, but whose combined effect creates a serious threat? What properties would those actions need?
:::
placeholder:: Construct the threat model
assessment-instructions:: Score out of 100, by these three elements; an answer that shows all three scores 100 however briefly it is written. 30: an unacceptable outcome; harm to the direction of AI or safety research (safety work slowed, misled or derailed) counts. 40: how the model brings it about: through many actions a careful human team could understand, each ordinary, defensible or low-stakes, whose combined effect causes the harm, without wildly superhuman skill. 30: why a reviewer who understands each action would still not catch it, for example each action is locally defensible and the harm only shows in the aggregate, the reviewer cannot tell whether an action serves a larger scheming strategy, or few actions are ever reviewed. The paragraphs about the learner's earlier commitment only say where the learner starts from; both routes lead to the same kind of construction. Cap at 45 if the threat rests on a single concentrated high-stakes action, such as exfiltrating weights or inserting an obvious backdoor. Cap at 40 if the construction depends on actions nobody could understand or on wildly superhuman skill. Model answer, for the feedback, not a grading checklist: "Research sabotage. A scheming model working on AI R&D makes thousands of individually understandable decisions: which experiments to prioritize, how to interpret ambiguous results, which safety concerns deserve further investigation, when an apparent failure justifies abandoning a project. Each is scrutable and locally defensible; a reviewer might understand exactly what the model did without being able to show that any decision was malicious. The threat comes from the aggregate direction: safety research is quietly slowed and misleading conclusions accumulate, with no single obviously catastrophic action."
feedback-instructions:: In at most eight sentences: state what the learner's threat model does well, then compare it against the three questions, namely whether the harm is concentrated or distributed, whether the actions are hard to understand or merely hard to evaluate, and whether the construction shows a serious threat, one protocol failing, or full uncontrollability. Then give the worked example, without repeating the scrutability-versus-control point the previous question's feedback already made. One important example is research sabotage, where a model working on AI research and development makes thousands of locally defensible decisions whose aggregate direction quietly slows safety work, and no single decision can be shown to be malicious. That is a diffuse threat. Close on the distinction that matters: research sabotage establishes a serious and credible threat without automatically proving that every affordable control protocol must fail.
#### End Callout

#### Article
from:: We think we probably won't run into issues related to qualitatively wildly superhuman skills in problematic domains. Here's a summary of our argument:
to:: For a more detailed version of these arguments, see [[#^appendix-more-detail-on-avoiding-qualitatively-wildly-superhuman-skills-in-problematic-domains|Appendix "More detail on avoiding qualitatively wildly superhuman skills in problematic domains"]].

#### Callout: Understanding check
#### Question: Open
id:: e16bdbf2-7160-44f6-914a-b3a6d7ca2bd2
content:: Control techniques may fail against an AI that is qualitatively wildly superhuman in certain domains. Which domains are the most problematic?
assessment-instructions:: Score out of 100. 35 for each problematic domain the answer names, up to 100: hacking; persuasion; manipulating scientific results or conceptual arguments. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Hacking, persuasion, and manipulating scientific results or conceptual arguments. In most domains, wildly superhuman performance is not a problem for control."
feedback-instructions:: In at most four sentences: confirm what the learner got right and, if anything is missing or wrong, the most important thing, then state the model answer. The problematic domains are hacking, persuasion, and manipulating scientific results or conceptual arguments. In most domains, wildly superhuman performance is not a problem for control. No follow-up questions; tell them to move on.

#### Question: Open
id:: b18f031e-e53c-455f-bbed-bea97b9a4c34
content:: Why is an early transformatively useful AI unlikely to be qualitatively wildly superhuman in a problematic domain? Give two different reasons.
assessment-instructions:: Score out of 100. 50 for each different correct reason, up to two, from these: an AI that was wildly superhuman across the board would probably already have been transformatively useful at a lower capability level; the uses that make an AI transformatively useful do not need wildly superhuman skill in the problematic domains, so there is no reason to train for it; skill in those domains seems to track general capability, as long as AIs are not trained on them much more than on the core tasks; AI capability profiles so far have not been wildly different from the human one. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "An AI that was wildly superhuman across the board would probably have been transformatively useful at an earlier capability level. The applications that make an AI transformatively useful do not require training for wildly superhuman performance in problematic domains, those domains seem correlated with general capability, and AI capability profiles so far are not wildly different from the human profile."
feedback-instructions:: In at most four sentences: confirm what the learner got right, then supply the strands they missed. An across-the-board wildly superhuman AI would probably have been transformatively useful earlier. The transformative applications do not require wildly superhuman performance in the problematic domains. Those domains look correlated with general capability rather than separable from it. And AI capability profiles so far are not wildly different from the human profile. No follow-up questions; tell them to move on.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from: the section arguing that early transformatively useful AIs will be very dangerous but probably not wildly superhuman in the domains that would defeat control.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts.*
:::

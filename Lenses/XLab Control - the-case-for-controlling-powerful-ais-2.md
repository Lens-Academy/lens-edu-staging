---
id: '702fce69-02f3-4b20-882b-911f72435a1a'
title: "The case for control (2): is it achievable, and for how long?"
tldr: "Control only matters if the models worth controlling can still be controlled. Greenblatt and Shlegeris argue that the first transformatively useful AIs will be dangerous but probably not uncontrollable, that the window in which control holds may be short, and that what we do inside that window decides what it was worth."
summary_for_tutor: "Second half of Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', continuing the previous lens 'The case for control (1)', which defined control, set it beside alignment and showed why control is evaluable. This lens carries the post from the section 'Control is likely achievable for early transformatively useful AIs' through 'Implications and proposed actions', with the appendices at the end for reference. The argument, in order: (4) control is likely achievable for early transformatively useful AIs, because transformative usefulness probably implies very dangerous but probably does not imply uncontrollable, and because we can probably avoid wildly superhuman skill in the few problematic domains (hacking, persuasion, manipulating scientific results); (5) the control window may nonetheless be short, and neuralese would close it; (6) implications for labs, regulators and researchers. Vocabulary assumed from the first half: scheming, the control property, untrusted versus trusted models, protocol, control evaluation, red team, catching red-handed. New here: transformatively useful, uncontrollable, the control window, control frontier, diffuse threat, neuralese. The five exercise blocks are: an open question on whether a control window exists at all, answered on the page by the control-timeline widget, a slider that widens or closes the window and lights four milestones for what the time inside it buys, with the figure's caveats carried by Text segments before and after it; a commit-and-construct on whether inscrutability is necessary for uncontrollability, which lands on research sabotage as a diffuse threat; an understanding check on problematic domains; a recall on neuralese; and a two-part reasoning prompt on two worlds with different control windows and what a window is worth. If a learner argues that useful models must be uncontrollable, ask them what the transformative applications actually require, rather than restating the authors' four strands for them."
reading_minutes: 80
tutor_minutes: 0
tags: []
---
#### Text
content::
This is the second half of the founding text of AI control. The first half defined control and showed why, unlike alignment, you can test whether you have it. This half asks whether control is achievable for the models we actually want to use, how long that lasts, and what follows for labs, regulators and researchers. Five exercises break up the reading: each one asks you to work out a step of the argument before the authors hand it to you. Answer before you move on, even roughly.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: # Control is likely achievable for early transformatively useful AIs
to:: So transformatively useful models are probably also very dangerous.

#### Callout: Reasoning prompt: could useful models remain controllable?
#### Question: Open
id:: dc2636c8-c8df-4375-a5b2-3d96ba6ff35e
content:: Could such highly capable, transformatively useful models still remain controllable? What properties of the models themselves, the control protocol, or the environment in which the models are trained and deployed could determine this?
placeholder:: Write your reasoning
assessment-instructions:: This is an open question set before the control-window discussion, so the learner is speculating deliberately. What is being assessed is whether they see what turns on the answer. Model answer: if transformative usefulness implied uncontrollability, control would provide no useful period in which advanced models could be safely deployed, because the point at which models become useful enough to substantially reduce risk would also be the point at which control ceased to be viable. If transformative usefulness did not imply uncontrollability, there may be a control window: a period in which models are already transformatively useful, dangerous, but a carefully designed protocol could theoretically still retain the control property. Full credit for recognising that the whole value of control hinges on whether these two thresholds coincide, and for naming at least two candidate determining properties across the three categories the question offers (the models, the protocol, the environment). Reward specific candidates such as the capability gap to trusted labor, the affordances the model is given, monitoring cost, whether reasoning stays interpretable, or how fast the lab builds the next model. Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, name what the learner's reasoning got right, then give the framing they are about to read. If transformative usefulness implied uncontrollability, control would buy no usable period at all, because the moment models became useful enough to reduce risk would be the moment control stopped working. If it does not imply uncontrollability, there may be a control window: a stretch in which models are already transformatively useful and dangerous, yet a carefully designed protocol could still retain the control property. Tell them the next section argues for the second picture.

#### End Callout

#### Text
content::
Here is the shape of the answer the next section argues for. The axis runs from now into the future through three regions: not yet transformatively useful, the control window, and uncontrollable. The arrival of transformative usefulness is fixed; the slider moves only the control frontier, and the milestones underneath show what the time inside the window buys.

#### Widget
source:: [[../widgets/xlab-control-control-timeline]]

#### Text
content::
Widths there are qualitative: an ordering of successive frontier systems, not calendar time. The window's width is not fixed in advance. It depends on how fast capabilities are pushed past transformative usefulness, and the reading argues we should hold off on building uncontrollable AI for as long as possible.

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
assessment-instructions:: The learner has just committed to a view on whether inscrutability is necessary for uncontrollability and rated their confidence. Assess the reasoning, not the commitment; both commitments are legitimate starting points. The position the lesson takes: scrutability means an action can be understood if it is examined carefully, and that does not by itself imply the model is controlled. An understandable action might not be inspected; it might be understandable without being easy to evaluate; its significance might depend on many other individually understandable actions; reviewers might recognise what an action does without being able to determine whether it is part of a larger strategy. Scrutability removes one possible source of control failure but does not logically eliminate every other source, so inscrutability is not conceptually necessary for a model to pose a serious threat to control. Full credit for reasoning that separates being understandable from being inspected, evaluated or recognised as part of a strategy, whichever way the learner committed. Do not yet supply a worked threat model; the next question asks the learner to build one. Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences: state what the learner's reasoning does well, then give the resolution. Scrutability means an action can be understood if examined carefully, which does not by itself imply the model is controlled: an understandable action might not be inspected, might be understandable without being easy to evaluate, might matter only together with many other understandable actions, and reviewers might see what it does without seeing whether it is part of a larger strategy. So scrutability removes one source of control failure but not every other, and inscrutability is not conceptually necessary for a serious threat to control. Close by saying that leaves the harder question the next prompt asks: can they construct a credible threat in which the model's actions remain scrutable? Do not give a worked example.

#### Question: Open
id:: b633dab0-e4e0-47b5-99e8-853e4e88ba24
content::
Construct the strongest threat model you can: what unacceptable outcome could a scheming but scrutable model cause, and how does the model bring it about?

The model's actions should remain scrutable, meaning a capable human team could understand them if it examined them carefully. Do not assume that the model has qualitatively wildly superhuman skills in a problematic domain.

If you committed to "inscrutability is necessary": try to construct the strongest counterexample to your original view, even if you remain unconvinced that it is realistic.

If you committed to "inscrutability is not necessary": turn your general intuition into the most credible concrete threat model you can.

:::callout{title="Hint" tone="amber" collapse="closed"}
A single high-stakes action, such as attempting to exfiltrate model weights or inserting a clearly dangerous security backdoor, is often highly scrutinizable. Because the harm is concentrated, the action is more likely to appear suspicious and to be incriminating if a monitor or auditor catches it.

What kinds or sequences of actions would be less individually incriminating? Could a model take actions that each appear ordinary, defensible, or low-stakes, but whose combined effect creates a serious threat? What properties would those actions need?
:::
placeholder:: Construct the threat model
assessment-instructions:: The learner has committed to a view on whether inscrutability is necessary for uncontrollability and is now constructing a threat model in which every action stays scrutable. Assess the construction, not the commitment; both commitments are legitimate starting points. On the conceptual question, the position the lesson takes: scrutability means an action can be understood if it is examined carefully, and that does not by itself imply the model is controlled. An understandable action might not be inspected; it might be understandable without being easy to evaluate; its significance might depend on many other individually understandable actions; reviewers might recognise what an action does without being able to determine whether it is part of a larger strategy. Scrutability removes one possible source of control failure but does not logically eliminate every other source, so inscrutability is not conceptually necessary for a model to pose a serious threat to control. The important worked example is research sabotage: a scheming model working on AI research and development might make thousands of individually understandable decisions, about which experiments to prioritise, how to interpret ambiguous results, which safety concerns deserve further investigation, which research directions appear promising, and when an apparent failure justifies abandoning a project. Each action could be scrutable and locally defensible; a reviewer might understand exactly what the model did without being able to show the decision was malicious. The threat arises from the aggregate direction of many actions: safety research is quietly slowed, misleading conclusions accumulate, or capabilities work advances faster than it otherwise would. The harm is not concentrated in one obviously catastrophic action but distributed across many actions that are less individually suspicious and less incriminating. That is a diffuse threat. Grade the learner's construction against three questions: is the harm concentrated in one action or distributed across many; are the actions difficult to understand, difficult to evaluate, or difficult to identify as evidence of scheming; and does the construction demonstrate a serious control threat, the failure of one protocol, or full uncontrollability. Full credit for a construction whose harm is distributed rather than concentrated and whose actions are hard to evaluate rather than hard to understand. Give partial credit for a concentrated single-action threat and say why it is the easier case: a single high-stakes action such as attempting to exfiltrate weights or inserting a clearly dangerous backdoor is highly scrutinizable, and because the harm is concentrated the action is more likely to look suspicious and to be incriminating if a monitor or auditor catches it. Grade only against what this lens has supplied.
feedback-instructions:: In at most eight sentences: state what the learner's threat model does well, then compare it against the three questions, namely whether the harm is concentrated or distributed, whether the actions are hard to understand or merely hard to evaluate, and whether the construction shows a serious threat, one protocol failing, or full uncontrollability. Then give the worked example, without repeating the scrutability-versus-control point the previous question's feedback already made. One important example is research sabotage, where a model working on AI research and development makes thousands of locally defensible decisions whose aggregate direction quietly slows safety work, and no single decision can be shown to be malicious. That is a diffuse threat. Close on the distinction that matters: research sabotage establishes a serious and credible threat without automatically proving that every affordable control protocol must fail.
#### End Callout

#### Article
from:: We think we probably won't run into issues related to qualitatively wildly superhuman skills in problematic domains. Here's a summary of our argument:
to:: We expect that companies that want to achieve control will need to consider it a core organizational priority.

#### Callout: Understanding check
#### Question: Open
id:: e16bdbf2-7160-44f6-914a-b3a6d7ca2bd2
content:: Control techniques may fail against an AI that is qualitatively wildly superhuman in certain domains. Which domains are the most problematic?
assessment-instructions:: The learner is recalling a short list from the passage above. Model answer: hacking, persuasion, and manipulating scientific results or conceptual arguments; in most domains, wildly superhuman performance is not a problem for control. Full credit needs at least two of the three domains plus the point that most domains are not problematic. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, then state the model answer. The problematic domains are hacking, persuasion, and manipulating scientific results or conceptual arguments. In most domains, wildly superhuman performance is not a problem for control. No follow-up questions; tell them to move on.

#### Question: Open
id:: b18f031e-e53c-455f-bbed-bea97b9a4c34
content:: Why is an early transformatively useful AI unlikely to be qualitatively wildly superhuman in a problematic domain?
assessment-instructions:: The learner is recalling a four-part argument from the passage above. Model answer: an AI that was wildly superhuman across the board would probably have been transformatively useful at an earlier capability level; the applications that make an AI transformatively useful do not require training for wildly superhuman performance in problematic domains; those domains seem correlated with general capability, so long as AIs are not trained on them much more than on the core tasks we care about; and AI capability profiles so far are not wildly different from the human profile. Full credit for two of the four strands. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences: confirm what the learner got right, then supply the strands they missed. An across-the-board wildly superhuman AI would probably have been transformatively useful earlier. The transformative applications do not require wildly superhuman performance in the problematic domains. Those domains look correlated with general capability rather than separable from it. And AI capability profiles so far are not wildly different from the human profile. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: ## For how long will we have controllable and transformatively useful AI?
to:: but it's plausible that we can hold off on building uncontrollable AI for at least several years which could suffice.

#### Callout: Quick recall
#### Question: Open
id:: a8427af2-efc9-41b9-8c6a-65ba6006782c
content:: What is "neuralese", and why does it threaten control?
assessment-instructions::The learner is recalling a term and its consequences. Model answer: neuralese is uninterpretable serial reasoning, memory, or communication between AI instances; it makes it harder to ensure the red team can match the AI's plans, harder to monitor for problematic reasoning, and harder to elicit capabilities; and once AIs can pass arbitrary uninterpretable messages to each other, preventing coordination and collusion is virtually impossible. Full credit needs the definition plus at least two of the four consequences. Note that this term becomes load-bearing later in the course, so correct a vague definition. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences: confirm what the learner got right, then state the model answer. Neuralese is uninterpretable serial reasoning, memory, or communication between AI instances. It makes it harder to ensure the red team can match the AI's plans, harder to monitor for problematic reasoning, and harder to elicit capabilities. And once AIs can pass arbitrary uninterpretable messages to one another, preventing coordination and collusion is virtually impossible. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # Implications and proposed actions
to:: We think that AI control is a particularly tractable approach to managing risk from scheming models, and we are excited about further research on this.

#### Callout: Reasoning prompts: two worlds, two windows
#### Text
content::
The control window has two dimensions: capability room and calendar time. Here are two worlds that begin at the same moment.

<svg viewBox="0 0 760 480" width="100%" style="max-width:760px;height:auto" role="img" aria-label="Two worlds, two windows. World A: the control frontier sits far above the transformatively useful line, so four model generations fit inside the control window, but the capability curve climbs steeply and the window is brief in calendar time. World B: the frontier sits just above the transformatively useful line, so only one generation fits, but the capability curve climbs slowly through the window, which lasts for years, before accelerating again past the frontier. Dots mark model generations: grey before the window, solid inside it, hollow past the control frontier.">
<g fill="currentColor" font-size="14" font-weight="600"><text x="30" y="24">A. Wide in capability, brief in time</text><text x="410" y="24">B. Narrow in capability, long in time</text></g>
<g fill="currentColor" fill-opacity="0.6" font-size="11"><text x="30" y="42">more room, less time, 4 generations fit</text><text x="410" y="42">less room, more time, 1 generation fits</text></g>
<g stroke="currentColor" stroke-opacity="0.35" stroke-width="1"><line x1="40" y1="55" x2="40" y2="265"/><line x1="40" y1="265" x2="350" y2="265"/><line x1="420" y1="55" x2="420" y2="265"/><line x1="420" y1="265" x2="730" y2="265"/></g>
<g fill="currentColor" fill-opacity="0.55" font-size="10"><text x="30" y="280">now</text><text x="330" y="280">time</text><text x="410" y="280">now</text><text x="710" y="280">time</text><text x="14" y="150" transform="rotate(-90 14 150)">capability</text><text x="394" y="150" transform="rotate(-90 394 150)">capability</text></g>
<rect x="95" y="90" width="55" height="130" fill="#2e9e6b" fill-opacity="0.15" stroke="#2e9e6b" stroke-opacity="0.5"/>
<rect x="475" y="185" width="208" height="35" fill="#2e9e6b" fill-opacity="0.15" stroke="#2e9e6b" stroke-opacity="0.5"/>
<g stroke="#4a7fd4" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="220" x2="350" y2="220"/><line x1="420" y1="220" x2="730" y2="220"/></g>
<g stroke="#d9534f" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="90" x2="350" y2="90"/><line x1="420" y1="185" x2="730" y2="185"/></g>
<g fill="none" stroke="currentColor" stroke-opacity="0.8" stroke-width="2.5"><polyline points="40,252 70,241 95,220 112,190 128,150 142,105 158,55"/><polyline points="420,252 450,241 475,220 520,212 580,203 640,193 683,185 700,177 712,167 722,157 730,146"/></g>
<g fill="#d4d4d4" stroke="#a3a3a3"><circle cx="55" cy="247" r="4.5"/><circle cx="435" cy="247" r="4.5"/></g>
<g fill="#2e9e6b" stroke="#1e6b48"><circle cx="97" cy="217" r="4.5"/><circle cx="115" cy="182" r="4.5"/><circle cx="131" cy="140" r="4.5"/><circle cx="144" cy="98" r="4.5"/><circle cx="530" cy="211" r="4.5"/></g>
<g fill="#ffffff" stroke="#2e9e6b" stroke-width="1.75"><circle cx="683" cy="185" r="4.5"/><circle cx="722" cy="157" r="4.5"/></g>
<g fill="currentColor" fill-opacity="0.4" font-size="10"><text x="48" y="238">M0</text><text x="428" y="238">M0</text></g>
<g fill="currentColor" fill-opacity="0.75" font-size="10"><text x="86" y="208">M1</text><text x="104" y="173">M2</text><text x="120" y="131">M3</text><text x="149" y="92">M4</text><text x="521" y="202">M1</text><text x="691" y="179">M2</text><text x="730" y="151">M3</text></g>
<g fill="currentColor" fill-opacity="0.55" font-size="10"><text x="30" y="310">window projected onto time</text><text x="410" y="310">window projected onto time</text></g>
<g stroke="currentColor" stroke-opacity="0.35"><line x1="40" y1="330" x2="350" y2="330"/><line x1="420" y1="330" x2="730" y2="330"/></g>
<rect x="95" y="322" width="55" height="16" fill="#2e9e6b" fill-opacity="0.35" stroke="#2e9e6b"/>
<rect x="475" y="322" width="208" height="16" fill="#2e9e6b" fill-opacity="0.35" stroke="#2e9e6b"/>
<g stroke="#4a7fd4" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="378" x2="66" y2="378"/></g>
<g stroke="#d9534f" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="402" x2="66" y2="402"/></g>
<rect x="40" y="420" width="26" height="12" fill="#2e9e6b" fill-opacity="0.35" stroke="#2e9e6b"/>
<circle cx="47" cy="450" r="4.5" fill="#2e9e6b" stroke="#1e6b48"/>
<circle cx="61" cy="450" r="4.5" fill="#ffffff" stroke="#2e9e6b" stroke-width="1.75"/>
<g fill="currentColor" fill-opacity="0.75" font-size="11"><text x="76" y="382">transformatively useful</text><text x="76" y="406">control frontier: the capability level beyond which no affordable protocol retains the control property</text><text x="76" y="430">control window</text><text x="76" y="454">model generation, solid inside the window and hollow past the frontier</text></g>
</svg>

**Same start, different futures.** Both worlds cross the *transformatively useful* line at the same moment. In **World A** the control frontier sits far above, so protocols scale across several model generations, but capabilities race there in little time. In **World B** the frontier is near, so only one generation stays controllable, yet the lab lingers inside the window for years. Read the lower timelines alone and A looks like the worse deal, but that flat "window in time" view hides that A packs four controllable generations into its sliver where B fits one. Time is only one of the window's dimensions.

#### Question: Open
id:: 17ddc18a-2425-4617-906a-ea498bf20dc2
content::
\#### Part A: what must differ?

Both worlds begin at the same moment: the leading lab has just built its first transformatively useful model and it runs the best protocols it can afford. From here the worlds diverge. Notice that both windows are large, but not in the same way: World A's spans more model development with many controllable generations, while World B's spans more calendar time but with only one controllable generation.

These worlds started from the same model at the same moment, so something about each of them produced the picture you see.

What are the most important differences between World A and World B that could produce these two windows? For each difference, say where the control frontier sits and how fast the capability curve climbs toward it.
placeholder:: Write your reasoning
assessment-instructions:: The learner is decomposing a two-panel figure into causes. A hint you may give if the learner is stuck: differences tend to live in four places, namely how fast capabilities advance and why, how well control protocols keep scaling, what the lab chooses (build or slow down), and what the outside world forces; some of these move the frontier, others change how fast you reach it. Model answer: every difference acts through one of three channels. If it changes how well control protocols keep scaling, it moves the red line, because the frontier sits wherever protocols stop being affordable. If it changes how fast capabilities advance, it shapes the curve: the frontier stays put, but you reach it sooner or later. If it changes what the lab chooses or what the outside world allows, it sets the dwell, meaning how long anyone actually stays inside the window before building past it. Examples: monitoring that keeps working on much stronger models moves the red line up; a training breakthrough that compresses years of progress into months steepens the curve; a competitor forcing the pace, or a regulator requiring control evaluations before each new training run, moves neither line but changes the clock. Full credit needs at least two named differences, each correctly assigned to the red line, the curve, or the clock. Grade only against what this lens has supplied.
feedback-instructions:: In at most six sentences, name what the learner identified, then sort their differences into the three channels. A difference in how well control protocols keep scaling moves the red line, because the frontier sits wherever protocols stop being affordable. A difference in how fast capabilities advance shapes the curve, leaving the frontier where it is but changing when you reach it. A difference in what the lab chooses or what the outside world allows sets the dwell, meaning how long anyone stays inside the window before building past it. Give the three examples if they help: monitoring that keeps working on much stronger models moves the red line up; a training breakthrough that compresses years into months steepens the curve; a competitor forcing the pace or a regulator requiring control evaluations before each training run changes only the clock. Close by asking, for each difference they wrote down, what moves: the red line, or the clock.

#### Question: Open
id:: ca9f10e4-d9e9-4b4e-90a1-a06e1052d2a3
content::
\#### Part B: what's the window worth?

In both worlds the green interval is the same kind of thing: a stretch of time with transformatively useful models you can still trust, to spend on alignment, control, evaluations, security.

What does the value of a control window actually depend on? Use the two worlds to think it through: which makes a window worth more, more capability room or more time? Under what conditions would your answer change?
placeholder:: Write your reasoning
assessment-instructions:: The learner is pricing a control window. Model answer: a window is worth what comes out of it, and roughly that value is a product of four terms: the capability of the trusted models you hold, the time you hold them, the share of their work aimed at what matters, and how much of that ability you can actually elicit. World A is rich in the first term, World B in the second, and neither picture tells you the other two. Which term dominates depends on what safety progress is bottlenecked on. If progress waits on insights that only more capable models can supply, room dominates and A's four generations beat B's years. If progress waits on labor, on running the experiments, evaluations and hardening we already know how to do, time dominates and B's long dwell wins. If progress waits on elicitation, on getting scheming models to genuinely try, neither room nor time helps until that term moves. One of these terms is also a lever: better control protocols raise the frontier, which raises the capability of the most powerful model you can still trust, so control research buys window in the room dimension. Full credit needs the recognition that the answer is conditional on the bottleneck rather than a flat preference for A or B, plus at least two of the four terms named. Reward a learner who notices that the figure only shows two of the four terms. Grade only against what this lens has supplied.
feedback-instructions:: In at most seven sentences, say what the learner's answer got right, then give the resolution. A window is worth what comes out of it, roughly the product of four terms: the capability of the trusted models you hold, the time you hold them, the share of their work aimed at what matters, and how much of that ability you can actually elicit. World A is rich in the first, World B in the second, and neither picture tells you the other two. Which term dominates depends on the bottleneck: if safety progress waits on insight only stronger models supply, room wins; if it waits on labor, time wins; if it waits on elicitation, neither helps until that term moves. One term is a lever, because better control protocols raise the frontier and so raise the capability of the most powerful model you can still trust, which means control research buys window in the room dimension. Close with the open question: in our world, which term is the bottleneck?
#### End Callout

#### Article
from:: # Appendix: Ready-to-go strategies

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from: the post that defines the control property, argues control is evaluable where alignment is not, and makes the case that early transformatively useful AIs can be controlled.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts.*
:::

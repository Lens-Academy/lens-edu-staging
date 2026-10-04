---
id: '1597caed-a8b7-499d-b6d7-6e8f22112487'
title: "High-stakes and low-stakes threats"
tldr: "Some ways an AI could cause a catastrophe take one or two actions that would look damning if anyone checked. Others take hundreds of actions that each look like an honest mistake. The two kinds need different defences: the first has to be stopped before it runs, the second can be reviewed later."
summary_for_tutor: "First teaching lens of Unit 2 of AI Control Fundamentals. The learner reads an excerpt of Ryan Greenblatt's 'Prioritizing threats for AI control' (Redwood Research, March 2025): the opening, which defines rogue internal deployment (the AI running inside the company's datacenter with control measures disabled) and self-exfiltration (the AI stealing its weights and running them on an outside server), then the three clusters of threats (violating internal security invariants, sabotaging work relevant to AI risk, causing problems through side effects) and the section on concentrated versus non-concentrated failures, where Greenblatt says security-invariant violations can happen in a few actions, so suspicious actions sometimes have to be blocked until reviewed and review latency matters, while the other clusters usually need many bad actions, so non-blocking asynchronous review can be acceptable. He notes exceptions (rare critical outputs, time-sensitive operations) and that concentration is a spectrum. Then comes his ranked list of control priorities, with rogue internal deployments first and sabotage-free useful work second, and the start of his justification: a maximum-severity rogue internal deployment could arbitrarily compromise the developer, and self-exfiltration matters less because it gives the AI less compute. A short Lens note says not everyone agrees with this ranking and that Unit 4 covers the argument that the bigger risk is work that looks right and is not, without scheming. Then the learner labels the four regions of the control graph widget (how many actions a catastrophe takes against how incriminating each action is). In this course 'high-stakes' means concentrated and 'low-stakes' means non-concentrated or diffuse. Two questions follow: the first is scored, the second is not. The key idea for this unit's learning outcome: classification turns on how many actions are needed and how incriminating each is, not on how much harm results. If the learner equates low-stakes with low harm, correct this in one sentence."
reading_minutes: 13
tutor_minutes: 10
---
#### Text
content::
Ryan Greenblatt is Chief Scientist at Redwood Research ([MATS](https://www.matsprogram.org/mentor/greenblatt)), which says it introduced AI control as a research area ([Redwood Research](https://www.redwoodresearch.org/)). Here he sorts the ways a misaligned AI could cause serious harm into clusters, separates threats that need only a few actions (concentrated failures) from threats that need many (non-concentrated or diffuse), and ranks which ones control should handle first. Redwood researchers mostly call these high-stakes and low-stakes ([Hebbar 2025](https://blog.redwoodresearch.org/p/how-can-we-solve-diffuse-threats)), and this course does too.

#### Article
source:: [[../articles/greenblatt-prioritizing-threats-for-ai-control]]
from:: We often talk about ensuring control
to:: Beyond rogue deployments, other security issues seem substantially less threatening.

#### Text
content::
Not everyone agrees with this ranking. In Unit 4 you will read the argument that the bigger risk is early AIs producing work that looks right and is not, without any scheming.

#### Text
content::
\## The control graph

Vivek Hebbar, also at Redwood, draws the same distinction as a graph with two axes: how many actions a catastrophe takes, and how incriminating each action looks when someone inspects it. You will watch his talk later in this unit. Place the four labels on the regions where you think they belong, then check.

#### Widget
source:: [[../widgets/xlab-control-high-stakes-graph]]

#### Question: Open
id:: 5233dd7a-65dd-4c60-98ad-56a21cd17491
content::
Without looking back: what makes a threat high-stakes rather than low-stakes, and why does Greenblatt think that changes whether a suspicious action can be reviewed after it has already run?
force-feedback:: first
assessment-instructions:: Score out of 100. 50: what makes a threat high-stakes. One or a few actions, or a short time, are enough to cause the catastrophe, while a low-stakes threat needs many bad actions. 30 of these 50 for the number of actions or the time alone, and the full 50 if the answer also says that each high-stakes action tends to be clearly incriminating if inspected while each low-stakes action is only weak evidence. 50: why this matters for reviewing after the fact. Because a few actions can be enough, the damage can be done before a later review catches anything, so suspicious actions sometimes have to be blocked until reviewed and fast review matters. In the low-stakes case nothing very bad happens quickly, so slower review after the fact can be acceptable. Full 50 for the high-stakes half with a clear reason, and the low-stakes half is welcome but not needed. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer defines high-stakes as the threats with the most harm. Model answer, for the feedback, not a grading checklist: "A high-stakes threat needs only a few actions, or a short time, and each bad action looks clearly bad if someone checks it. Because a few actions are enough, the harm can happen before a later review, so suspicious actions sometimes have to be stopped until someone has looked at them. Low-stakes threats need many actions, so slower review after the fact can be fine."
feedback-instructions:: The learner just read Greenblatt's section on concentrated versus non-concentrated failures and labelled the control graph. Key points: a high-stakes (concentrated) threat needs only a small number of actions or a short time, and each bad action is usually clearly incriminating if inspected. A low-stakes (diffuse) threat needs many bad actions, each only weak evidence. Because a few actions can be enough in the high-stakes case, suspicious actions sometimes have to be blocked until reviewed, and fast review matters. In the low-stakes case nothing very bad happens quickly, so slower, non-blocking review can be acceptable. Reply in at most four sentences: say what the learner got right, name the most important missing or wrong point in one sentence, and correct any confusion between low-stakes and low harm. This is a one-turn reply. Do not ask a follow-up question. No generic praise. If the learner says they do not understand, give one foothold from the reading, such as self-exfiltration as a one-action threat and sabotaged research as a many-action threat.

#### Question: Open
id:: 8b2d90a0-c02b-4729-8eb7-ca46e1aabbce
content::
Greenblatt says sabotaging work usually needs many bad actions, but names exceptions. Pick one of his exceptions, or think of your own, and say whether it would push that threat toward high-stakes, and why.
force-feedback:: first
feedback-instructions:: The learner names a case where sabotage could need only a few actions. Greenblatt's exceptions are rare critical outputs, where a few actions sabotaging that output could cause serious problems (he thinks these occasions are easy to identify and give closer review), and highly sensitive, time-critical operations such as fighting a hot war with AI-controlled robots or real-time cyber attacks (he thinks this may be a small fraction of use). A good answer says the case moves toward high-stakes because few actions are needed, and ideally notes whether each action would be incriminating. Treat any reasoned case of the learner's own as fine. Reply in at most four sentences, then close. If the learner judges by how harmful the outcome is rather than by how many actions it needs, say so in one sentence. Do not say which exceptions matter most. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Prioritizing threats for AI control." *Redwood Research blog*, 19 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/prioritizing-threats-for-ai-control)

The control graph widget comes from XLab's AI Control track, which adapts the diagram in Vivek Hebbar's talk "Low-stakes Control" at ControlConf ([YouTube](https://www.youtube.com/watch?v=DP3wTPDEjLQ)).
:::

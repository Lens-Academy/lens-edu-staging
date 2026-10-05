---
id: '1597caed-a8b7-499d-b6d7-6e8f22112487'
title: "High-stakes and low-stakes threats"
tldr: "Some ways an AI could cause a catastrophe take one or two actions that would look damning if anyone checked. Others take hundreds of actions that each look like an honest mistake. The two kinds need different defences: the first has to be stopped before it runs, the second can be reviewed later."
summary_for_tutor: "First teaching lens of Unit 2 of AI Control Fundamentals. The learner reads an excerpt of Ryan Greenblatt's 'Prioritizing threats for AI control' (Redwood Research, March 2025): the opening, which defines rogue internal deployment (the AI running inside the company's datacenter with control measures disabled) and self-exfiltration (the AI stealing its weights and running them on an outside server), then the three clusters of threats (violating internal security invariants, sabotaging work relevant to AI risk, causing problems through side effects) and the section on concentrated versus non-concentrated failures, where Greenblatt says security-invariant violations can happen in a few actions, so suspicious actions sometimes have to be blocked until reviewed and review latency matters, while the other clusters usually need many bad actions, so non-blocking asynchronous review can be acceptable. He notes exceptions (rare critical outputs, time-sensitive operations) and that concentration is a spectrum. The required excerpt ends there. A closed optional callout holds his ranked list of control priorities, with rogue internal deployments first and sabotage-free useful work second, and the start of his justification: a maximum-severity rogue internal deployment could arbitrarily compromise the developer, and self-exfiltration matters less because it gives the AI less compute. A short Lens note in the same callout says not everyone agrees with this ranking and that Unit 4 covers the argument that the bigger risk is work that looks right and is not, without scheming. Many learners will not have read the ranking, so do not assume it. Then the learner labels the four regions of the control graph widget (how many actions a catastrophe takes against how incriminating each action is). In this course 'high-stakes' means concentrated and 'low-stakes' means non-concentrated or diffuse. Two scored questions follow: one applies the distinction to two jobs of an AI agent, the other asks for the learner's own case of sabotage that needs only a few actions. The key idea for this unit's learning outcome: classification turns on how many actions are needed and how incriminating each is, not on how much harm results. If the learner equates low-stakes with low harm, correct this in one sentence."
reading_minutes: 9
tutor_minutes: 10
---
#### Text
content::
Ryan Greenblatt is Chief Scientist at Redwood Research ([MATS](https://www.matsprogram.org/mentor/greenblatt)), which says it introduced AI control as a research area ([Redwood Research](https://www.redwoodresearch.org/)). Here he sorts the ways a misaligned AI could cause serious harm into clusters, separates threats that need only a few actions (concentrated failures) from threats that need many (non-concentrated or diffuse), and, in an optional part at the end, ranks which ones control should handle first. Redwood researchers mostly call these high-stakes and low-stakes ([Hebbar 2025](https://blog.redwoodresearch.org/p/how-can-we-solve-diffuse-threats)), and this course does too.

#### Article
source:: [[../articles/greenblatt-prioritizing-threats-for-ai-control]]
from:: We often talk about ensuring control
to:: countermeasures developed to handle concentrated failures will often also be possible to repurpose into useful countermeasures for handling non-concentrated problems.)

#### Callout: Greenblatt's ranking of these threats (optional)
collapse:: closed

#### Article
from:: ## My prioritization between these threats
to:: Beyond rogue deployments, other security issues seem substantially less threatening.
optional:: true

#### Text
content::
Not everyone agrees with this ranking. In Unit 4 you will read the argument that the bigger risk is early AIs producing work that looks right and is not, without any scheming.

#### End Callout

#### Text
content::
\## The control graph

Vivek Hebbar, also at Redwood, draws the same distinction as a graph with two axes: how many actions a catastrophe takes, and how incriminating each action looks when someone inspects it. You will watch his talk later in this unit. Place the four labels on the regions where you think they belong, then check.

#### Widget
source:: [[../widgets/xlab-control-high-stakes-graph]]

#### Question: Open
id:: 401c1d0f-bf90-4a46-8751-f2c875ccfd23
content::
An AI agent at a lab does two jobs. Once a month it changes who can access the training cluster, and every day it writes hundreds of summaries of experiment results. For which job would you hold a suspicious action until a human has checked it, and for which would checking a sample a week later be enough? Explain your choice by how many bad actions it would take to do serious harm in each job.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: in AI control, a high-stakes threat is one where a few actions, or a short time, are enough to cause a catastrophe, and each such action usually looks clearly bad if inspected. A low-stakes threat needs many bad actions, each only weak evidence. When a few actions are enough, suspicious actions sometimes have to be blocked until reviewed, while for threats that need many actions slower review after the fact can be acceptable. 20: the choice, holding suspicious access changes until a human has checked them and checking a sample of the summaries later. 40: why the access changes need checking first. A single bad change, for example quietly giving an AI or an outsider access it should not have, or switching off a safeguard, can be enough to do serious harm, and the harm can happen before a later review sees it. 40: why sampling the summaries later is enough. One slanted or wrong summary does little on its own, so serious harm would need many bad summaries over time, and a later review of a sample has time to notice the pattern before much damage is done. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer decides only by how harmful each job's outcome could be and never by how many bad actions the harm would need. Model answer, for the feedback, not a grading checklist: "I would hold suspicious access changes until a human has checked them, because one bad change could hand an AI or an outsider access it should not have, and the damage could be done before anyone reviews it later. The summaries can be checked by sampling a week later, because one bad summary does little, so serious harm would take many of them, and a sampled review would notice the pattern in time."
feedback-instructions:: The learner applies Greenblatt's distinction between concentrated and non-concentrated failures to two jobs. Changing who can access the training cluster is high-stakes: one bad change can be enough, and it would usually look clearly bad if inspected, so suspicious changes should be blocked until reviewed and fast review matters. Writing experiment summaries is low-stakes: serious harm needs many slanted or wrong summaries, each only weak evidence because it could be an honest mistake, so non-blocking review of a sample after the fact can be acceptable. If the learner argues that one critical summary could be enough, accept it as Greenblatt's exception for rare critical outputs, as long as the reasoning is about the number of actions. Reply in at most four sentences: say what the learner got right, name the most important missing or wrong point in one sentence, and correct any confusion between low-stakes and low harm. This is a one-turn reply. Do not ask a follow-up question. No generic praise. If the learner says they do not understand, give one foothold: ask how many bad access changes, and how many bad summaries, it would take to do real damage.

#### Question: Open
id:: 4195a7c2-9990-495d-9c35-228db3136965
content::
Describe a piece of safety-relevant work where an AI could do serious sabotage with only a few actions, using a case of your own rather than one of Greenblatt's. Would each of those actions look clearly bad to someone who inspected it? Is the case high-stakes, and why?
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: a threat is high-stakes when a few actions, or a short time, are enough to cause serious harm, and low-stakes when it needs many bad actions, each only weak evidence. Sabotage of work usually needs many bad actions, but there are exceptions, such as a rare critical output that a few actions could spoil. 40: a concrete piece of safety-relevant work and a sabotage of it that plausibly needs only a few actions, for example a wrong threshold in a dangerous-capability evaluation that decides whether a model is released, a flaw in the setup of the next big training run, or a gap left in a security patch. 30: a reasoned judgement of whether each of those actions would look clearly bad if inspected. Either verdict earns the points when the reason fits the case, for example a deliberate hole in a security rule looks damning, while a single wrong number can pass as an honest mistake. 30: the classification with its reason: the case leans high-stakes because few actions are needed. An answer that puts it between the corners because its actions are only weakly incriminating also earns these 30. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer classifies the case only by how much harm it would cause. Model answer, for the feedback, not a grading checklist: "An AI writes the scoring script for a dangerous-capability evaluation that decides whether a new model may be released. One small change to how answers are scored could let a dangerous model pass. Inspected, the change could pass as an honest bug, so it is only weakly incriminating. It still leans high-stakes because one action is enough, which makes it a hard case: few actions, and none of them clearly damning."
feedback-instructions:: The learner describes their own case where sabotage of safety-relevant work needs only a few actions. Greenblatt's exceptions were rare critical outputs, where a few actions spoiling that output could cause serious problems (he thinks such occasions are easy to spot and give closer review), and highly sensitive, time-critical operations such as fighting a hot war with AI-controlled robots or real-time cyber attacks. A good answer gives a concrete case, judges whether each action would look clearly bad if inspected, and says the case leans high-stakes because few actions are needed. Reply in at most four sentences, then close. If the learner judges by how harmful the outcome is rather than by how many actions it needs, say so in one sentence. If their case would need many actions after all, say so and why. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Prioritizing threats for AI control." *Redwood Research blog*, 19 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/prioritizing-threats-for-ai-control)

The control graph widget comes from XLab's AI Control track, which adapts the diagram in Vivek Hebbar's talk "Low-stakes Control" at ControlConf ([YouTube](https://www.youtube.com/watch?v=DP3wTPDEjLQ)).
:::

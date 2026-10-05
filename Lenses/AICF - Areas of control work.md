---
id: 'd2e7953d-3130-42c4-800a-dfc312d42762'
title: "Areas of control work"
tldr: "Ryan Greenblatt lists eight areas of AI control work, from building test environments for control evaluations to setting up human review processes inside AI companies, and says roughly how much effort each deserves. Here you read his list and the opening of each area."
summary_for_tutor: "Field part of Unit 2 of AI Control Fundamentals. The learner reads excerpts of Ryan Greenblatt's 'An overview of areas of control work' (Redwood Research, April 2025): the introduction with the list of eight areas, roughly in descending order of how much investment each should get (he suggests about a third of current control resources for settings and control evaluations), then the opening paragraphs of each area. The rest of each section is collapsed and can be expanded. The areas: (1) developing and using settings for control evaluations, (2) better understanding control-relevant capabilities and model properties, (3) developing specific countermeasures in isolation, (4) control experiments on actual AI usage, (5) prototyping software infrastructure and security measures relevant to control, (6) prototyping human processes for control, such as auditing and escalation, probably most doable at AI companies, (7) conceptual and other non-empirical research, (8) nearer-term applications of control, such as misuse. Greenblatt says the division is imperfect and the areas overlap. Two scored questions follow: a project in the area Greenblatt would fund most, and one project an outside university group could do and one it could not. The learning outcome this prepares is placing a piece of control work in its area and saying who is placed to do it."
reading_minutes: 8
tutor_minutes: 8
---
#### Text
content::
The first half of this unit was about what control defends against. The second half is about the field: what people in control work on, who they are, and how many of them there are. Ryan Greenblatt's list of research areas is a map drawn from inside the field, from Redwood's point of view, in April 2025, and the next lessons add other views.

#### Article
source:: [[../articles/greenblatt-an-overview-of-areas-of-control-work]]
from:: In this post, I'll list all the areas of control research
to:: Now I'll elaborate on projects within each of these areas.

#### Article
from:: ## Developing and using settings for control evaluations
to:: for the setting to be immediately useful.)

#### Article
from:: ## Better understanding control-relevant capabilities and model properties
to:: than just people interested in control.

#### Article
from:: ## Developing specific countermeasures/techniques in isolation
to:: so studying with a separate methodology is needed.

#### Article
from:: ## Doing control experiments on actual AI usage
to:: relatively high risk application.

#### Article
from:: ## Prototyping or implementing software infrastructure for control
to:: could effectively happen outside of frontier AI companies.

#### Article
from:: ## Prototyping or implementing human processes for control
to:: This work is probably most doable at AI companies.

#### Article
from:: ## Conceptual research and other ways of researching control
to:: where various people there currently think about control.

#### Article
from:: ## Nearer-term applications of control to practice
to:: to handle scheming.

#### Question: Open
id:: d1735c1f-94ec-4369-b177-8351fee5bd39
content::
A small research group can fund one control project this year, and today's models are still too weak to be dangerous. In the area Greenblatt says should get the most resources, propose a concrete project. Say what it would produce that is still useful once models are dangerous.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Ryan Greenblatt lists eight areas of control work and says the one that deserves the most resources, perhaps a third of current control effort, is developing and using settings for control evaluations: building test environments where a red team plays a model trying to cause harm and a blue team tests safety measures against it. Because current models are not actually risky, he says work in this area is useful now for practising the control method, finding better techniques, and building settings that will be useful once models are capable enough. 40: a concrete project in that area, building a setting or running a control evaluation in one, for example an environment where an AI agent does realistic infrastructure work and a red team tries to sneak a backdoor past a monitor. 15 of these 40 for a concrete project in a different area. 60: what the project produces that stays useful once models are dangerous, with the reason, any one of: a setting that can be rerun with stronger models, safety techniques found to work in it, or practice with the method so that later evaluations are done well. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "I would build a control setting where an AI agent does lab infrastructure work and a red team tries to get it to plant a backdoor without the monitor noticing. Today's models are too weak for the results to say much about real risk, but the setting can be rerun with each new model, the monitoring techniques that work in it carry over, and the team learns how to run such evaluations before it matters."
feedback-instructions:: The learner proposes a project in Greenblatt's top area. The area he would give the most, perhaps a third of current control resources, is developing and using settings for control evaluations. He says work there is useful now, while models are not actually risky, to practise the methodology, find better techniques, and build settings that will be useful once models are smarter. A good answer proposes a concrete setting or control evaluation and names one of those lasting products. Reply in at most four sentences: say what fits, name the most important missing or wrong point (for example a project from another area, which you should name, or one whose results only matter while models are weak), and correct any error. One turn, no follow-up question, no generic praise. Tell them to move on.

#### Question: Open
id:: ed3d9bf9-e46c-4401-8448-6706a3e05248
content::
A university group with no access to any AI company wants to work on control. Suggest one concrete project it could do well and one it could not. Say what access the second one would need.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: areas of control work include building control settings and running control evaluations, studying control-relevant model capabilities, developing countermeasures in isolation, conceptual research, experiments on real AI use (most interesting with people inside an AI company), software infrastructure and security measures at AI companies (unclear how much can be done from outside), and human processes such as auditing and escalation (probably most doable at AI companies). 40: a concrete project that an outside group could do well, such as building a control setting with open-weight or API models, testing a monitoring technique on public models, or conceptual work. 30: a concrete project it could not do well, such as designing an AI company's auditing and escalation process, prototyping control infrastructure in a company's own systems, or studying how a company's staff use AI agents internally. 30: what access that project would need, for example the company's internal systems and logs, its staff, its unreleased models, or the authority to change how it works. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "It could build a control setting with open-weight models, where a red team tries to slip backdoors past a monitor, and test which monitoring setups catch the most attacks. It could not design how an AI company reviews flagged agent actions and escalates them, because that needs access to the company's real agent traffic, its staff and the authority to change their processes."
feedback-instructions:: The learner suggests one project an outside university group could do and one it could not. From the reading: human processes for control are "probably most doable at AI companies", for software infrastructure and security measures "it's unclear how much of this prototyping work could effectively happen outside of frontier AI companies", and experiments on actual AI usage are most interesting with participants inside an AI company. Settings and control evaluations, capability studies, countermeasures in isolation and conceptual work can largely be done outside. A good answer gives one concrete project of each kind and names the access the inside one needs, such as real systems, internal data, staff or authority to change processes. Accept other reasoned answers. Reply in at most four sentences. Up to two turns. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "An overview of areas of control work." *Redwood Research blog*, 9 Apr. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/an-overview-of-areas-of-control-work)
:::

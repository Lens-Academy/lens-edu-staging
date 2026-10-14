---
id: '6fa7e7f3-bc4d-4e59-8467-bc4dcc29d2cf'
title: "What about superintelligence?"
reading_minutes: 6
tutor_minutes: 14
tldr: "Control's own authors, and a 2025 paper co-written with the UK AI Security Institute, say it will not work for arbitrarily powerful AI. MIRI agrees and draws a different conclusion: no workaround exists for a misaligned superintelligence, so the effort should go into stopping anyone from building one."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The learner reads a short excerpt from Greenblatt and Shlegeris's case for control ('The control approach we're imagining won't work for arbitrarily powerful AIs', it is aimed at the first AIs capable of substantially reducing risk from later AIs), then the last sentence of the abstract of Korbak, Balesni, Shlegeris and Irving, 'How to evaluate control measures for LLM agents? A trajectory from today to superintelligence' (April 2025, authors from UK AISI, Apollo Research and Redwood Research, so not independent of Redwood): a compelling control safety case for superintelligent LLM agents 'will require research breakthroughs', and 'we might eventually need alternative approaches to mitigating misalignment risk'. Then two excerpts from MIRI's 'The Problem' (2025): MIRI sees no viable workaround to misaligned superintelligence, it would not be possible to safely use it for any complex real-world operation, deceiving it is prone to fail, and 'Plans to align ASI using unaligned AIs are similarly unsound'. Then section 5: 'If anyone builds ASI, everyone dies', so progress toward ASI needs to be halted by an effective worldwide ban. Both sides agree control does not scale to superintelligence. They disagree about whether controlled early AIs can help with what comes after, and about where effort should go. MIRI's criticism has a 'does not work' side (for ASI and for the plan of using unaligned AIs for alignment) and a 'not worth the effort' side (the effort should go to halting). Do not tell the learner who is right."
---
#### Text
content::
Greenblatt and Shlegeris, who wrote the case for control you read in Unit 1, agree with MIRI on one limit. Here is how they put it:

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: The control approach we're imagining won't work for arbitrarily powerful AIs
to:: We define "transformatively useful AI" to mean AIs that are capable of substantially reducing risk from subsequent AIs.

#### Text
content::
A 2025 paper by researchers at the UK AI Security Institute, Apollo Research and Redwood Research[^cite-korbak-2025] says the same about control evaluations. Buck Shlegeris, one of the two authors of the case for control, is a co-author, so this is not an independent check on Redwood. The last sentence of its abstract:

[^cite-korbak-2025]: Tomek Korbak, Mikita Balesni, Buck Shlegeris and Geoffrey Irving (2025), *How to evaluate control measures for LLM agents? A trajectory from today to superintelligence*. [arXiv](https://arxiv.org/abs/2504.05259)

#### Article
source:: [[../articles/korbak-how-to-evaluate-control-measures-for-llm-agents-a-trajectory-from-today-to-superintelligence]]
from:: Finally, we show why constructing a compelling AI control safety case
to:: highlighting that we might eventually need alternative approaches to mitigating misalignment risk.

#### Text
content::
The Machine Intelligence Research Institute (MIRI) set out its view of AI risk in "The Problem" in 2025. Two short excerpts. A term in them:

- **ASI:** artificial superintelligence.

#### Article
source:: [[../articles/bensinger-the-problem]]
from:: As a consequence, MIRI doesn’t see any viable quick fixes or workarounds to misaligned ASI.
to:: explores the hazards of using unaligned AI to do work as complex as alignment research.

#### Article
from:: "### **5\. Catastrophe can be averted via a sufficiently aggressive policy response.**"
to:: and tight control over the factors of its production.

#### Question: Open
id:: 5f614c24-f8c0-4b69-bda8-1e1e5f116a37
force-feedback:: first
content::
\## Where do they disagree?

Redwood and MIRI agree that control will not work for an arbitrarily powerful AI.

1. What do they disagree about? Say what each side thinks.
2. Where does each side think the effort should go?
placeholder:: A sentence or two for each.
assessment-instructions:: Score out of 100. Context for grading: Greenblatt and Shlegeris of Redwood Research write that the control approach they imagine will not work for arbitrarily powerful AIs. It is aimed at "transformatively useful AI", AIs capable of substantially reducing risk from subsequent AIs. A 2025 paper co-written by Shlegeris says a compelling control safety case for superintelligent agents will require research breakthroughs, and that alternative approaches may eventually be needed. MIRI sees no viable workaround to misaligned superintelligence (ASI), says it would not be possible to safely use one for complex real-world operations, and writes "Plans to align ASI using unaligned AIs are similarly unsound". MIRI concludes that progress toward ASI must be halted by an effective worldwide ban. Part 1, 60: 30 for naming the disagreement: whether early AIs, kept under control, can do safety work that helps make later, more powerful AIs safe (for example, "whether we can use transformative AI to align superintelligence"). 30 for saying what each side thinks: Redwood thinks they can, and its plan relies on it. MIRI thinks they cannot, and calls plans to align ASI using unaligned AIs unsound. Part 2, 40: 20 for Redwood (control and use the early AIs, including for safety work), 20 for MIRI (halt progress toward ASI, by a worldwide ban). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "They disagree about the early AIs. Redwood thinks controlled early AIs can do safety work that reduces risk from the later, more powerful ones. MIRI thinks using unaligned AIs to align ASI is unsound. So they also disagree on where the effort should go: Redwood into controlling and using early AIs, MIRI into a worldwide ban on progress toward ASI."
feedback-instructions:: The learner says where Redwood and MIRI disagree, given that both think control will not work for an arbitrarily powerful AI, and where each side thinks the effort should go. Reference points: they disagree on whether controlled early AIs, the first ones able to substantially reduce risk from later AIs, can do useful safety work that helps with what comes next (MIRI: "Plans to align ASI using unaligned AIs are similarly unsound"), and on where effort should go (MIRI: halt progress toward ASI by a worldwide ban). Up to two turns, 80 to 140 words each. Steelman the answer, name the most important gap, and ask one direct follow-up question. No generic praise. Do not say who is right.

#### Question: Open
id:: 1172809d-b903-494d-a959-8907f2aa4f91
force-feedback:: first
content::
\## What kind of criticism is MIRI's?

There are three kinds of criticism: control does not work, works but is not worth the effort, or works and makes things worse. MIRI's criticism is of two of these kinds. Which two, and why?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: MIRI sees no viable workaround to misaligned superintelligence (ASI), says it would not be possible to safely use one for complex real-world operations and that deceiving it is prone to fail, and writes "Plans to align ASI using unaligned AIs are similarly unsound". It concludes that progress toward ASI must be halted by an effective worldwide ban. 50 for the "does not work" side: control does not work for ASI, or for the plan of getting alignment work out of unaligned AIs. 50 for the "not worth the effort" side: the effort should go to halting progress toward ASI instead. Give up to 50 for another sorting with a reason that fits what MIRI says, in place of one of these. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mostly 'does not work': MIRI thinks nothing can safely control or use a misaligned ASI, and that using unaligned AIs to align ASI is unsound. It also has a 'not worth the effort' side, because MIRI wants the effort to go into a worldwide ban instead."
feedback-instructions:: The learner sorts MIRI's criticism of control. Reference sorting: MIRI's criticism has a "does not work" side, for ASI and for the plan of getting alignment work out of unaligned AIs, and a "not worth the effort" side, because the effort should go to halting. Accept reasoned alternatives. Up to two turns, 80 to 140 words each. Steelman the answer, name the most important gap, and ask one direct follow-up question. No generic praise. Do not say who is right.

#### Question: Open
id:: 5060a724-cfd2-4ad4-9b05-b3a1c7201c9f
force-feedback:: first
content::
\## What the plan needs

Greenblatt and Shlegeris accept that control will not work for an arbitrarily powerful AI. Name two things that would have to be true for their plan to work, given this limit.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Greenblatt and Shlegeris write that the control approach they imagine will not work for arbitrarily powerful AIs. It is aimed at "transformatively useful AI", AIs capable of substantially reducing risk from subsequent AIs. A 2025 paper co-written by Shlegeris says a compelling control safety case for superintelligent agents will require research breakthroughs, and that alternative approaches may eventually be needed. MIRI writes that "Plans to align ASI using unaligned AIs are similarly unsound". Conditions for the plan to work: there must be a window in which AIs are useful enough to help and still controllable, the work they produce must be checkable, and developers or governments must use that window well, for example by slowing down before AIs outgrow control. Any two of these conditions earn 100, one earns 50. Also credit another condition that the plan clearly needs, with a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "There has to be a period when AIs are capable enough to do real safety work but still weak enough to control. The work they do in that period has to be something we can check. And someone has to use the period well, for example by slowing down before the AIs outgrow control."
feedback-instructions:: The learner says what would have to be true for the control plan to work, given that control will not work for an arbitrarily powerful AI. Reference points: there must be a window in which AIs are useful enough to help and still controllable, the work they produce must be checkable, and developers or governments must use that window well, for example by slowing down before AIs outgrow control. Up to two turns, 80 to 140 words each. Steelman the answer, name the most important gap, and ask one direct follow-up question. No generic praise. Do not say who is right.

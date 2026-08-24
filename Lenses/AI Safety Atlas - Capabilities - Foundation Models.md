---
id: 16537044-2ad6-41f7-b4fe-e7d33f395fca
tldr: "One model, many jobs: foundation models flipped AI from building a specialist for every task to pre-training a single general system you adapt afterward. This section explains how they are trained, why properties like transfer and few-shot learning are so powerful, and why that same generality creates safety problems narrow AI never had."
summary_for_tutor: "Introduces foundation models as a paradigm shift from task-specific narrow AI to large general-purpose models pre-trained on massive unlabeled data and adapted afterward. Covers the two-stage training process (self-supervised pre-training, then fine-tuning or in-context prompting), key properties (transfer learning, zero-shot and few-shot learning, and cross-domain generalization), the distinction between foundation and frontier models, and the unique safety challenges that arise from limited control over what is learned, the need to preserve safety properties through adaptation, and the difficulty of auditing models trained at massive scale."
reading_minutes: 12
tutor_minutes: 7
title: "Foundation Models"
---

#### Article
source:: [[../articles/AI Safety Atlas - Capabilities - Foundation Models|Foundation Models]]

#### Text
optional:: true
content::
The section argues the safety problems it lists come from the shift to one model pre-trained and then adapted. Did you find that convincing for all of them, or only some? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Foundation models are a shift from building one narrow system per task to pre-training a large general-purpose model and adapting it afterwards. Pre-training is self-supervised on massive unlabelled data; adaptation happens through fine-tuning or in-context prompting. The three properties it names are transfer learning, zero-shot and few-shot learning, and cross-domain generalisation. Emergence appears only in passing, not as a property of its own. The section argues these same properties create safety problems narrow AI did not have, because there is limited control over what is learned, safety properties must survive adaptation, and the scale of training data makes auditing hard. Note that it promises a subsection on risks and never delivers one, so its safety material is scattered rather than collected.

topics to explore:
- What does self-supervised pre-training actually optimise for, and why does that make what the model learns hard to constrain?
- How does fine-tuning differ from prompting, and why does the section say safety properties have to survive that stage?
- What is "emergent" claiming here, and what is it not claiming?
- What separates a foundation model from a frontier model, and why does the section keep them apart?

Do not preview the later sections in detail. Do not name a year, discuss whether any arrival date is early or late, repeat the chapter's 2030 versus 2050 illustration, or ask the learner for a forecast of their own. A later lens asks them to commit to a number of years unprimed, and the end of the chapter comes back to it. If they volunteer a date, do not evaluate it, extend it, or ask them to justify it.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

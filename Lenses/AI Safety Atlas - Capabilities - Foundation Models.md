---
id: 16537044-2ad6-41f7-b4fe-e7d33f395fca
tldr: "One model, many jobs: foundation models flipped AI from building a specialist for every task to pre-training a single general system you adapt afterward. This section explains how they are trained, why properties like transfer and few-shot learning are so powerful, and why that same generality creates safety problems narrow AI never had."
summary_for_tutor: "Introduces foundation models as a paradigm shift from task-specific narrow AI to large general-purpose models pre-trained on massive unlabeled data and adapted afterward. Covers the two-stage training process (self-supervised pre-training, then fine-tuning or in-context prompting), key properties (transfer learning, zero-shot and few-shot learning, {--{"author":"Elias's AI","timestamp":1787563956157}@@cross-domain generalization, --}and {--{"author":"Elias's AI","timestamp":1787563956157}@@emergent capabilities)--}{++{"author":"Elias's AI","timestamp":1787563956157}@@cross-domain generalization)++}, the distinction between foundation and frontier models, and the unique safety challenges that arise from limited control over what is learned, the need to preserve safety properties through adaptation, and the difficulty of auditing models trained at massive scale."
reading_minutes: 12
tutor_minutes: {--{"author":"Elias's AI","timestamp":1787562832301}@@0--}{++{"author":"Elias's AI","timestamp":1787562832301}@@7++}
title: "Foundation Models"
---

#### Article
source:: [[../articles/AI Safety Atlas - Capabilities - Foundation Models|Foundation Models]]{++{"author":"Elias's AI","timestamp":1787563954434}@@

#### Text
content::
Foundation models are the shift the rest of the chapter builds on. If the two training stages, or what "emergent" is actually claiming, are still blurry, use the tutor to go through them.

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

Do not preview the later sections in detail. The forecasting section has its own pre-question and this chapter returns to it, so do not give timelines or an arrival date of your own, even if asked.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}

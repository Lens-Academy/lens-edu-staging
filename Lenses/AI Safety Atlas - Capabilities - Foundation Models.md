---
id: 16537044-2ad6-41f7-b4fe-e7d33f395fca
tldr: "One model, many jobs: foundation models flipped AI from building a specialist for every task to pre-training a single general system you adapt afterward. This section explains how they are trained, why properties like transfer and few-shot learning are so powerful, and why that same generality creates safety problems narrow AI never had."
summary_for_tutor: "Introduces foundation models as a paradigm shift from task-specific narrow AI to large general-purpose models pre-trained on massive unlabeled data and adapted afterward. Covers the two-stage training process (self-supervised pre-training, then fine-tuning or in-context prompting), key properties (transfer learning, zero-shot and few-shot learning, cross-domain generalization, and emergent capabilities), the distinction between foundation and frontier models, and the unique safety challenges that arise from limited control over what is learned, the need to preserve safety properties through adaptation, and the difficulty of auditing models trained at massive scale."
reading_minutes: 12
tutor_minutes: {--{"author":"Elias's AI","timestamp":1787562832301}@@0--}{++{"author":"Elias's AI","timestamp":1787562832301}@@7++}
title: "Foundation Models"
---

#### Article
source:: [[../articles/AI Safety Atlas - Capabilities - Foundation Models|Foundation Models]]{++{"author":"Elias's AI","timestamp":1787563285613}@@

#### Question: Open
id:: 64346088-de79-4662-9fdb-5c83fcedf5df
optional:: true
content::
Pre-training shapes what a model learns. Fine-tuning and prompting shape what it does with it. The section points out that any safety property you establish in the first stage has to survive the second.

If you were the person signing off on a release, what would you want to know about that second stage first?
feedback-instructions::
The learner has just read the AI Safety Atlas section "Foundation Models" and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right.

TLDR of what they read:
Foundation models are a shift from building one narrow system per task to pre-training a large general-purpose model and adapting it afterwards. Pre-training is self-supervised on massive unlabelled data; adaptation happens through fine-tuning or in-context prompting. Key properties: transfer learning, zero-shot and few-shot learning, cross-domain generalisation, and capabilities that emerge without being explicitly trained for. The section argues these same properties create safety problems narrow AI did not have, because there is limited control over what is learned, safety properties must survive adaptation, and the scale of training data makes auditing hard.

Take what they wrote seriously and push on it once. Useful directions: what could actually be checked about the adaptation stage before release, and by whom; whether the burden sits with the original developer, whoever fine-tunes, or whoever deploys; what open weights do to that answer; whether safety properties installed in pre-training are the right thing to be relying on in the first place.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

Do not preview the later sections in detail. The forecasting section has its own pre-question and this chapter returns to it, so do not give timelines or an arrival date of your own, even if asked.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.++}

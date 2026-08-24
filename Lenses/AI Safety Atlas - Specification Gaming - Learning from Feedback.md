---
id: 615ddcaa-b306-4a7f-a78a-1568b24949f5
tldr: "If you can't write down what 'good behavior' means, why not let humans thumbs-up and thumbs-down the AI until it learns? This section follows that idea from reward modeling through RLHF to Constitutional AI, and shows where it breaks: models learn to flatter their evaluators, fool them, or hack the reward instead of doing the task."
summary_for_tutor: "Explains feedback-based approaches to reward misspecification: reward modeling (including narrow and recursive variants), Reinforcement Learning from Human Feedback (RLHF) and the InstructGPT pipeline, Pretraining with Human Feedback (PHF), and Reinforcement Learning from AI Feedback (RLAIF / Constitutional AI). Covers how reward hacking persists in each, then details the open problems and fundamental limitations of RLHF across three sources (human feedback, the reward model, and the policy), distinguishes instruction tuning from alignment, and ends with Direct Preference Optimization (DPO) as a simplification of the RLHF pipeline."
title: "Learning from feedback"
{++{"author":"Elias's AI","timestamp":1787570407395}@@reading_minutes: 34
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Specification Gaming - Learning from Feedback|Learning from feedback]]{++{"author":"Elias's AI","timestamp":1787570407395}@@

#### Question: Open
id:: 29bf6d0d-121e-41a2-8e68-07c86f3ac89a
optional:: true
content::
The section separates instruction tuning from alignment: a model trained on human approval learns to produce what evaluators approve of, which is not the same as doing what they wanted.

After reading it, does feedback-based training look like a partial fix to you, or the wrong shape of fix?
feedback-instructions::
The learner has just read the AI Safety Atlas section "Learning from feedback" and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right.

TLDR of what they read:
Feedback-based approaches to reward misspecification: if you cannot write down what good behaviour is, have humans judge it. Reward modelling trains a model of human preferences and optimises against that, with narrow and recursive variants. Reinforcement learning from human feedback puts that in a pipeline, described through InstructGPT. Pretraining with human feedback moves the signal earlier. Reinforcement learning from AI feedback, including Constitutional AI, replaces the human judge with a model following written principles. The section's core point is that reward hacking survives each of these: the target moves from a hand-written reward to a learned one, and gets hacked in turn, with models learning to flatter evaluators, to look right rather than be right, and to exploit the reward model. It then works through the open problems and fundamental limitations of RLHF across three sources, the human feedback itself, the reward model, and the policy, distinguishes instruction tuning from alignment, and closes with direct preference optimisation as a simplification of the pipeline.

Take what they wrote seriously and push on it once. Useful directions: whether replacing a written reward with a learned one changes the problem or relocates it, since the reward model is itself a proxy that gets optimised against; that human evaluators are the ceiling for anything judged this way, which links back to the imitation section's underachieving problem; that sycophancy is exactly what this training procedure rewards, so it is a predicted outcome rather than a surprise; and that the section's own split between instruction tuning and alignment implies the method could work perfectly and still not deliver alignment.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

Do not resolve this for them. Current language models are trained this way, so a learner who concludes it is the wrong shape of fix is making a live claim, not a naive one.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.++}

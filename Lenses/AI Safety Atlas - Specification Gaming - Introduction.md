---
id: aa09f399-5f6c-43b8-a89e-5de2d873b1ae
tldr: "We can tell an AI what to do, but not perfectly what we mean, and clever optimizers exploit the gap, doing exactly what we said instead of what we wanted. This chapter opener maps the terrain of specification gaming: how rewards get misspecified, and which fixes, from imitation to human feedback, might close the gap."
summary_for_tutor: "Roadmap for the Specification Gaming chapter. Outlines the sequence: a refresher on reinforcement learning rewards and reward functions; optimization and Goodhart's Law; reward misspecification (the outer alignment problem) with examples like reward hacking and reward tampering; learning by imitation as a proposed fix (imitation learning, behavioral cloning, inverse reinforcement learning) with their limitations; and learning by feedback (reward modeling, RLHF, RLAIF) including how current LLMs are trained and where these approaches fall short."
title: "Introduction"
{++{"author":"Elias's AI","timestamp":1787570315478}@@reading_minutes: 7
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Specification Gaming - Introduction]]{++{"author":"Elias's AI","timestamp":1787570315478}@@

#### Question: Open
id:: 70f607a3-3bf0-4d8f-87b4-3a93cd04e70d
optional:: true
content::
The chapter's premise is that we can tell a system what to do but never exactly what we mean, and that a capable optimiser will find the gap.

Is that a gap better specification could close, or is it the wrong kind of problem for that?
feedback-instructions::
The learner has just read the opening of the AI Safety Atlas specification gaming chapter and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right. They have read a short roadmap section and nothing else, so a short answer is expected.

TLDR of what they read:
The roadmap for the specification gaming chapter. Its premise is that we can state what a system should do but never fully state what we mean, and that an optimiser will exploit the difference, doing exactly what was specified rather than what was intended. It sets out the sequence the chapter follows: a refresher on reinforcement learning, rewards and reward functions; optimisation and Goodhart's Law; reward misspecification, which it calls the outer alignment problem, with reward hacking and reward tampering as examples; learning by imitation as a proposed fix, covering imitation learning, behavioural cloning and inverse reinforcement learning, along with their limits; and learning by feedback, covering reward modelling, RLHF and RLAIF, including how current language models are trained and where these approaches fall short.

Take what they wrote seriously and push on it once. Useful directions: whether the gap is a shortfall in our writing or a structural fact about compressing an intention into a measurable signal; that the chapter's two proposed fixes both stop trying to write the specification and try to learn it instead, from demonstrations or from feedback, which is a hint about how the authors answer this; whether more capable systems make the gap wider or narrower, since a system that understands you better might also exploit you better; and what would count as evidence either way.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

This is the chapter's roadmap. Reinforcement learning, optimisation, reward misspecification, imitation and feedback each get their own section, so do not preview them in detail.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.++}

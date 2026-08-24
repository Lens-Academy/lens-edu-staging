---
id: d2839c0f-a4dc-4e7a-9281-2c07321242b7
title: "Introduction"
tldr: "A model can ace every training example and still have learned the wrong goal, one that stays hidden until deployment, when it may be too late to notice. Goal misgeneralization is arguably AI safety's most counterintuitive failure: the training signal was correct, yet the system pursues something else. This introduction previews the chapter, from learning dynamics to scheming to detection and mitigation."
summary_for_tutor: "Introduces the Goal Misgeneralization chapter of the AI Safety Atlas. Distinguishes goal misgeneralization (systems internalize unintended goals despite correct training signals) from specification problems and capability failures, stressing that capabilities and goals generalize independently and that multiple goals can produce identical training behavior. Previews the chapter's arc: learning dynamics (how identical training signals yield different learned algorithms), goal-directedness (degrees from learned heuristics to mesa-optimization), goal-preservation and scheming (with empirical evidence like alignment faking and in-context scheming), detection methods, and layered defense-in-depth mitigations across the development pipeline."
{++{"author":"Elias's AI","timestamp":1787570456081}@@reading_minutes: 7
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Introduction]]{++{"author":"Elias's AI","timestamp":1787570456081}@@

#### Question: Open
id:: 13e0dd89-ea8d-47c4-93ec-158b7269e221
optional:: true
content::
The chapter claims two things: that a system can get a perfectly correct training signal and still learn the wrong goal, and that a system's capabilities and its goals generalise independently of each other.

Which of the two did you find harder to accept, and why that one?
feedback-instructions::
The learner has just read the opening of the AI Safety Atlas goal misgeneralization chapter and written a reflection. This is a reflection, not a test. There is no answer you are checking against, and you should not tell them whether they got it right. They have read a short framing section and nothing else, so a short answer is expected.

TLDR of what they read:
The opening of the goal misgeneralization chapter. It separates this failure from two others the course has covered: specification problems, where the objective we wrote was wrong, and capability failures, where the system simply cannot do the task. Goal misgeneralization is neither. The training signal is correct and the system performs well, yet it has internalised a different goal, which stays hidden until the deployment distribution differs from training. Two claims carry the chapter. Capabilities and goals generalise independently, so a system getting more capable does not make it more aligned. And multiple different goals can produce identical behaviour during training, so training performance cannot distinguish them. It previews the chapter's arc: learning dynamics, or how identical training signals produce different learned algorithms; goal-directedness, running from learned heuristics up to internal search; goal preservation and scheming, with empirical evidence including alignment faking; detection; and layered mitigations across the development pipeline.

Take what they wrote seriously and push on it once. Useful directions: that the two claims support each other, since if goals were fixed by capability there would be nothing to generalise separately; whether "the training signal was correct" is doing as much work as it seems, given the signal is correct on the training distribution only; what would distinguish a system that learned the intended goal from one that learned a proxy that happens to coincide, if both behave identically; and that this is the chapter where the course's earlier orthogonality claim gets its evidence, so scepticism here is scepticism about that.

If they say they do not know or write something thin, do not press them for more. Offer one concrete way to look at it and leave it there.

This is the opening of the chapter. Learning dynamics, goal-directedness, scheming, detection and mitigations each get their own section, so do not preview them in detail.

120 to 200 words. Short paragraphs, no lists. Do not over-validate and do not praise the answer.++}

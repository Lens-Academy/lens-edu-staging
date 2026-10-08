---
id: '673f8272-22bd-4b3d-a43b-2e2e2bbe28c8'
title: "A.1.2 Session 2: Alignment problem decompositions"
tldr: "Read one text on how alignment problems are decomposed: training stories, reward misspecification, goal misgeneralization, or inductive biases and emergent misalignment."
summary_for_tutor: "Session 2 of worksheet A.1: alignment problem decompositions. Students read one of: training stories, reward misspecification, goal misgeneralization, or soft inductive biases (with emergent misalignment). Discussion prompts ask for examples of misspecification versus misgeneralization, what training stories fix about the inner/outer split, and what inductive biases explain generalization, including emergent misalignment."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Session 2: Alignment problem decompositions

**11\:35–12\:30.** 5 min introduction, 25 min reading, 15 min discussion, 10 min debrief.

Spend **25 minutes** reading the following texts, concentrating on the one most interesting to you.

::card[[../Lenses/evhub-how-do-we-become-confident-in-the-safety-of-a-machine-learning-system|Training stories]]

> Read everything before the section "How mechanistic does \[...\]"

::card[[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|Reward misspecification]]

::card[[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards|Goal misgeneralization]]

::card[[../Lenses/wilson-deep-learning-is-not-so-mysterious-or-different|On soft inductive biases]]

> [Emergent misalignment](https://arxiv.org/abs/2502.17424)

Discuss in groups of 3–5 for **15 minutes**. Possible prompts:

- Think of well-known or imagined misalignment scenarios: Can you think of some that clearly fall into the reward misspecification or goal misgeneralization category? Are some not clearly in either of them?
- What problem with "outer" and "inner" misalignment is the terminology of "training stories" trying to solve? Construct examples where training stories seem more appropriate than inner/outer alignment as a framework.
- Think of concrete ways in which modern deep learning systems generalize beyond their explicit training examples. What inductive biases may underlie these examples? Is it always possible to come up with a "clean description" of those biases? Is the inductive bias you come up with enforced in the architecture, or more implicit?
    - Perhaps: Discuss this explicitly for the case of "emergent misalignment".

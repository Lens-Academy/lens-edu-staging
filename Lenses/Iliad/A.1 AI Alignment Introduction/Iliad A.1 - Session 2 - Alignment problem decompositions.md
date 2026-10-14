---
id: '673f8272-22bd-4b3d-a43b-2e2e2bbe28c8'
title: "A.1.2 Session 2: Alignment problem decompositions"
tldr: "Read one text on how alignment problems are decomposed: training stories, reward misspecification, goal misgeneralization, or inductive biases and emergent misalignment."
summary_for_tutor: "Session 2 of worksheet A.1: alignment problem decompositions. Students read one of: training stories, reward misspecification, goal misgeneralization, or soft inductive biases (with emergent misalignment). Discussion prompts ask for examples of misspecification versus misgeneralization, what training stories fix about the inner/outer split, and what inductive biases explain generalization, including emergent misalignment."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: 'd5fec17706ceed1fa028ca949b97b92dcc2f5f7e'
upstream_key: "ai-alignment-intro#session-2-alignment-problem-decompositions"
upstream_fingerprint: "JjY/198/1/03KW04W80BVs1SMf1Xw41vDS25H32CMC2I8A3Ora55OB56pC5IHG5YxB5liq6VaA6mOL7PeF7bTI7qqz7ryW8E4c8gXD92al9D2p9GGn9RTQ9nGq9nZJAElmAaNaBq09"
synced_from:
  source: "iliad"
  url: "https://iliad-intensive.org/alignment/ai-alignment-intro/#session-2-alignment-problem-decompositions"
---

#### Text
content::
\### Session 2: Alignment problem decompositions

**11\:35–12\:30.** 5 min introduction, 25 min reading, 15 min discussion, 10 min debrief.

Spend **25 minutes** reading the following texts, concentrating on the one most interesting to you.

::card[[../../evhub-how-do-we-become-confident-in-the-safety-of-a-machine-learning-system|Training stories]]

::card[[../../krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|Reward misspecification]]

::card[[../../shah-how-undesired-goals-can-arise-with-correct-rewards|Goal misgeneralization]]

::card[[../../wilson-deep-learning-is-not-so-mysterious-or-different|On soft inductive biases]]

::card[[../../betley-emergent-misalignment-narrow-finetuning-can-produce-broadly-misaligned-llms-1-this-paper-contains-model-generated-content-that-might-be-offensive-1|Emergent misalignment]]

* [Training stories](https://www.alignmentforum.org/posts/FDJnZt8Ks2djouQTZ/how-do-we-become-confident-in-the-safety-of-a-machine) 
  * Read everything before the section "How mechanistic does \[...\]"  
* [Reward misspecification](https://deepmind.google/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)  
* [Goal misgeneralization](https://deepmind.google/blog/how-undesired-goals-can-arise-with-correct-rewards/)  
* [On soft inductive biases](https://arxiv.org/abs/2503.02113)
	* [Emergent misalignment](https://arxiv.org/abs/2502.17424)

Discuss in groups of 3–5 for **15 minutes**. Possible prompts:

- Think of well-known or imagined misalignment scenarios: Can you think of some that clearly fall into the reward misspecification or goal misgeneralization category? Are some not clearly in either of them?
- What problem with "outer" and "inner" misalignment is the terminology of "training stories" trying to solve? Construct examples where training stories seem more appropriate than inner/outer alignment as a framework.
- Think of concrete ways in which modern deep learning systems generalize beyond their explicit training examples. What inductive biases may underlie these examples? Is it always possible to come up with a "clean description" of those biases? Is the inductive bias you come up with enforced in the architecture, or more implicit?
    - Perhaps: Discuss this explicitly for the case of "emergent misalignment".

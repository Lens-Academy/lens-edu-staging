---
id: '673f8272-22bd-4b3d-a43b-2e2e2bbe28c8'
title: "Session 2: Alignment problem decompositions"{++{"author":"Luc's AI","timestamp":1787134226645}@@
tldr: "To judge an alignment proposal, ask what target is trained, why the setup should produce it, and how rewards, learned goals, or inductive biases could fail."
summary_for_tutor: "The session introduces training stories as a general framework, then uses readings on reward misspecification, goal misgeneralization, and soft inductive biases to compare decompositions of technical alignment. It closes with group prompts that apply these frameworks to concrete misalignment and generalization cases."++}
authors:
  - Leon Lang
source_url: https://github.com/iliad-team/iliad-intensive/blob/1eb9e340305e03de3f81a761167e13c54c71f19d/tex/ai-alignment-intro/main.mdx
upstream_commit: '1eb9e340305e03de3f81a761167e13c54c71f19d'
provenance_recorded_at: '2026-08-17'
---

#### Text
content::
:::callout {title="Session intent" tone="neutral" collapse="closed"}

The participants learn to reason about how to decompose the *technical* problem of AI alignment (in a machine learning context) into subproblems via training stories and outer/inner misalignment. They also learn about inductive biases, which govern the generalization behavior of AI systems. After this session, students know what questions to ask when reasoning about whether a procedure leads to an alignet AI. Again, they learn all of this through readings and discussions.

:::

:::callout {title="Teaching notes" tone="neutral" collapse="closed"}

Training stories seem like a rather forgotten framework, a bit akin to the modern instantiation of a safety case. I like it since it’s more general than the more often used framework of outer- and inner misalignment.

:::

Spend **20 minutes** reading the following texts, concentrating on the one most interesting to you.

::card[[../Lenses/evhub-how-do-we-become-confident-in-the-safety-of-a-machine-learning-system|Training stories]]

> Read everything before the section “How mechanistic does \[...\]”

::card[[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity|Reward misspecification]]

::card[[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards|Goal misgeneralization]]

::card[[../Lenses/wilson-deep-learning-is-not-so-mysterious-or-different|On soft inductive biases]]

Discuss in groups of 3-5 for **30 minutes**. Possible prompts:

* Think of well-known or imagined misalignment scenarios: Can you think of some that clearly fall into the reward misspecification or goal misgeneralization category? Are some not clearly in either of them?  
* What problem with “outer” and “inner” misalignment is the terminology of “training stories” trying to solve? Construct examples where training stories seem more appropriate than inner/outer alignment as a framework.  
* Think of concrete ways in which modern deep learning systems generalize beyond their explicit training examples. What inductive biases may underlie these examples? Is it always possible to come up with a “clean description” of those biases? Is the inductive bias you come up with enforced in the architecture, or more implicit?  
  * Perhaps: Discuss this explicitly for the case of “emergent misalignment”.
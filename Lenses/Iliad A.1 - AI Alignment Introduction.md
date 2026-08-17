---
id: '29cd9f81-1776-43e2-a522-c363e9d490b7'
title: "A.1 AI Alignment Introduction"
tldr: "Current Iliad Intensive worksheet for AI Alignment Introduction."
summary_for_tutor: "Faithful April 2026 Iliad Intensive worksheet A.1, AI Alignment Introduction. Preserve its mathematical notation, exercise sequence, hints, and solutions."
authors:
  - Leon Lang
source_url: https://github.com/iliad-team/iliad-intensive/blob/1eb9e340305e03de3f81a761167e13c54c71f19d/tex/ai-alignment-intro/main.mdx
upstream_commit: '1eb9e340305e03de3f81a761167e13c54c71f19d'
provenance_recorded_at: '2026-08-17'
---

#### Text
content::
:::callout {title="What you'll learn" tone="neutral"}

* understand the basic decomposition of risks into AI misalignment, misuse, power grabs, and others;  
* can explain different alignment targets like coherent extrapolated volition, intent alignment, or AI that follows a constitution;  
* can reason about training stories and outer and inner (mis)alignment, challenges to these notions, and the relationship to inductive biases;  
* are aware of discussions on whether AI systems develop goals and understand the basic arguments for instrumental convergence;  
* are aware of foundational discussions on the level of risk and different high-level approaches to solving the AI alignment problem.

:::

\## Prerequisites

* We recommend a basic understanding of deep learning to follow this module.
* To understand some of the decompositions of AI alignment, it is also useful to have a basic understanding of reinforcement learning, including the notions of a reward function and a policy.

\## Roadmap for today

Students who are bored since they know the content already can read all texts in the “Reading guide” that they do not know.

\### Session 1: Alignment targets

:::callout {title="Session intent" tone="neutral" collapse="closed"}

The participants understand that there are different things we may want our AIs to be aligned *to*, and can reason through the differences and shortcomings of four well-known proposals. This helps them to disentangle conceptual from technical components of the alignment problem. They read about them and discuss about them.

:::

:::callout {title="Teaching notes" tone="neutral" collapse="closed"}

I find it useful to emphasize that it’s not obvious to pair these proposals together. CEV is very visionary but not very defined. Intent alignment mainly served the purpose of distinguishing between the “intent” of alignment from its execution (which is about capabilities). Constitutional AI is a modern practical instantiation of an alignment target that focuses more on principles and characters rather than concrete goals. And corrigibility is sometimes *contrasted with* alignment in that it’s the meta goal of being changeable regardless of other alignment properties.

:::

Spend **20 minutes** reading the following texts. Concentrate on the one most interesting to you. 

::card[[../Lenses/yudkowsky-coherent-extrapolated-volition|Coherent extrapolated volition]]

> Most important: The first 2.5 pages in Section 3\.

::card[[../Lenses/christiano-clarifying-ai-alignment|Intent alignment]]

::card[[../Lenses/anthropic-claudes-new-constitution|Claude’s constitution overview]]

::card[[../Lenses/lesswrong-corrigibility|Corrigibility]]

Discuss in groups of 3-5 for **30 minutes**. Possible prompts:

* Which alignment targets imply which others? Where this is not the case, think through counter examples.  
* Which alignment targets seem sufficient for safety? E.g., a corrigible system might cause harm before we change its values. Can it cause catastrophic harm? What about the other notions?   
* What other ideas for alignment targets do you have? Does your target have a benefit?





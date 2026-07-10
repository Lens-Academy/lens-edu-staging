---
id: 69349c48-6135-4953-a31d-c7e369838322
slug: ai-alignment-introduction
title: AI Alignment Introduction
---
%% Module A.1 of the Iliad Intensive, by Leon Lang (Iliad). Ported to Lens for
the demo. Overview lens is inline; the five learning outcomes are imported from
their own files so the teaching lenses can be reused across courses. %%

# Submodule: Overview

## Lens: Overview
id:: aa19a6c7-5e32-4819-a8da-6676eb9d6487

#### Text
content:: This module introduces the AI alignment problem as two combined challenges. First, we need to choose an *alignment target* — our vision for how an AI system, or a collection of such systems, should ideally behave. Second, we need to solve the technical problem of how to *align* AI systems with this vision.

We discuss frameworks for decomposing the technical problem further, and critiques of those frameworks, in a *learning* framing — and how the potential goal-directedness of AI poses additional challenges. We conclude by surveying different viewpoints on the difficulty and severity of the AI alignment problem, and the spectrum of solution approaches the field pursues.

**Prerequisites**

- A basic understanding of deep learning is recommended to follow this module.
- To understand some of the decompositions of AI alignment, a basic understanding of reinforcement learning — including the notions of a reward function and a policy — is also useful.

**How to work through this module**

Read the main content of each lens *first* without opening the linked posts. If a piece of terminology or logic in the high-level story is unclear, use the chat tutor (or your own LLM) to clarify until the whole story makes sense. Only then dig into specific linked posts and papers if you have time.

#### Chat
%% optional:: true %% 
instructions:: Orient the learner to the module. The module covers, in order: (1) the basic decomposition of AI risks (misalignment, misuse, power grabs, and others); (2) alignment targets (CEV, intent alignment, constitutions, corrigibility); (3) decompositions of the technical alignment problem (training stories, outer/inner alignment, inductive biases) and critiques of them; (4) goal-directedness and instrumental convergence; (5) forecasting the level of risk and the spectrum of high-level solution approaches. Help the learner form a mental map of how these five threads connect: choosing a target vs. technically hitting it, and why goal-directedness makes any residual misalignment more dangerous. Answer questions about prerequisites and how to pace themselves. Do not lecture the whole module here; just orient and set expectations. Keep it brief and inviting.
showUserPreviousContent:: true

# Submodule: Decomposing AI risks{++{"author":"Luc's AI","timestamp":1783723454590}@@

## Lens:
source:: [[../Lenses/The AI risk landscape]]

## Lens:
optional:: true
source:: [[../Lenses/darioamodei-dario-amodei-the-adolescence-of-technology]]

## Lens:++}
{++{"author":"Luc's AI","timestamp":1783723454590}@@optional:: true
source:: [[../Lenses/arxiv-an-overview-of-catastrophic-ai-risks]]

## Lens:
optional:: true
source:: [[../Lenses/1-gradual-disempowerment-systemic-existential-risks-from-incremental-ai-development]]

++}## Learning Outcome:
source:: [[../Learning Outcomes/Decomposing AI risks]]

# Submodule: Alignment targets{++{"author":"Luc's AI","timestamp":1783723461857}@@

## Lens:
source:: [[../Lenses/Choosing an alignment target]]

## Lens:
optional:: true
source:: [[../Lenses/yudkowsky-coherent-extrapolated-volition]]

## Lens:++}
{++{"author":"Luc's AI","timestamp":1783723461857}@@optional:: true
source:: [[../Lenses/anthropic-claudes-new-constitution]]

## Lens:
optional:: true
source:: [[../Lenses/lesswrong-corrigibility]]

++}## Learning Outcome:
source:: [[../Learning Outcomes/Alignment targets]]

# Submodule: Training stories and outer-inner alignment{++{"author":"Luc's AI","timestamp":1783723471430}@@

## Lens:
source:: [[../Lenses/Decomposing the alignment problem]]

## Lens:
optional:: true
source:: [[../Lenses/krakovna-specification-gaming-the-flip-side-of-ai-ingenuity]]

## Lens:
optional:: true
source:: [[../Lenses/shah-how-undesired-goals-can-arise-with-correct-rewards]]

## Lens:
optional:: true
source:: [[../Lenses/hubinger-risks-from-learned-optimization-in-advanced-machine-learning-systems]]

## Lens:++}
{++{"author":"Luc's AI","timestamp":1783723471430}@@optional:: true
source:: [[../Lenses/mitchell-the-need-for-biases-in-learning-generalizations]]

## Lens:
optional:: true
source:: [[../Lenses/betley-emergent-misalignment-narrow-finetuning-can-produce-broadly-misaligned-llms-1-this-paper-contains-model-generated-content-that-might-be-offensive-1]]

## Lens:
optional:: true
source:: [[../Lenses/turntrout-reward-is-not-the-optimization-target]]

++}## Learning Outcome:
source:: [[../Learning Outcomes/Training stories and outer-inner alignment]]

# Submodule: Goals and instrumental convergence{++{"author":"Luc's AI","timestamp":1783723478697}@@

## Lens:
source:: [[../Lenses/Goal-directedness and instrumental convergence]]

## Lens:
optional:: true++}
{++{"author":"Luc's AI","timestamp":1783723478697}@@source:: [[../Lenses/gwern-why-tool-ais-want-to-be-agent-ais]]

## Lens:
optional:: true
source:: [[../Lenses/omohundro-the-basic-ai-drives]]

++}## Learning Outcome:
source:: [[../Learning Outcomes/Goals and instrumental convergence]]

# Submodule: Forecasting risk and solution approaches{++{"author":"Luc's AI","timestamp":1783723487608}@@

## Lens:
source:: [[../Lenses/Forecasting risk and choosing an approach]]

## Lens:
optional:: true
source:: [[../Lenses/anthropic-core-views-on-ai-safety-when-why-what-and-how]]

## Lens:
optional:: true
source:: [[../Lenses/grace-thousands-of-ai-authors-on-the-future-of-ai]]

## Lens:
optional:: true
source:: [[../Lenses/ai-2027 article lens]]

## Lens:
optional:: true
source:: [[../Lenses/optimism-ai-is-easy-to-control]]

## Lens:++}
{++{"author":"Luc's AI","timestamp":1783723487608}@@optional:: true
source:: [[../Lenses/evhub-model-organisms-of-misalignment-the-case-for-a-new-pillar-of-alignment-research]]

## Lens:
optional:: true
source:: [[../Lenses/leike-why-im-optimistic-about-our-alignment-approach]]

## Lens:
optional:: true
source:: [[../Lenses/yudkowsky-the-rocket-alignment-problem]]

## Lens:
optional:: true
source:: [[../Lenses/dai-problems-in-ai-alignment-that-philosophers-could-potentially-contribute-to]]

++}## Learning Outcome:
source:: [[../Learning Outcomes/Forecasting risk and solution approaches]]

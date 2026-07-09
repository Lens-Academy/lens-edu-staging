---
title: "NeuroAI for AI safety"
author:
  - "Patrick Mineault"
source_url: "https://www.neuroai.science/p/neuroai-for-ai-safety"
published: 2024-12-11
created: 2026-07-09
accessed: 2026-07-09
description: "A differential path toward safe AI"
tags:
  - "article-importer"
---

It’s been quiet on neuroai.science for a little while, as I’ve been focusing on writing a roadmap for NeuroAI for AI safety. It turned out to be way more work than I anticipated, as I nerd-sniped myself, colleagues at the Amaranth Foundation, and collaborators into writing a 90-page missive with 700+ references. It's finally out!

I think you’ll like it. There’s lots of technical analysis on NeuroAI: data acquisition capabilities and available data across a wide range of relevant modalities, from electrophysiology to connectomics. We cover 7 different paths where NeuroAI can impact AI safety. It’s also a bit of a time capsule and a love letter to NeuroAI; while it’s by no means a comprehensive review of the whole field, it’s about as comprehensive as it could be without becoming an entire book.

I’d love to hear your thoughts. We made a companion website to make it easier to read on the go. You’ll have to pace yourself with this one as it clocks in at 22,000 words, but it can be read mostly out-of-order. I can almost guarantee you will learn something.

-   Website: [neuroaisafety.com](https://neuroaisafety.com/)
    
-   [Paper on arXiv](https://arxiv.org/abs/2411.18526)
    

Here’s a little flavor and a walkthrough of the roadmap to orient yourself.

---

## NeuroAI, fast and slow

NeuroAI is a field that takes inspiration from AI to help us understand the brain, and vice-versa. The neuro→AI route has been focused thus far on bringing new capabilities to AI, inspired by neuroscience and psychology: robustness to adversarial and out-of-distribution stimuli, higher data efficiency, smart and complex neurons, an active learning phase inspired by development, etc.

Naysayers will point out AI has been racing in capability without much neuroscience input. It is hard to find a benchmark that AI has not saturated, with the [ARC challenge](https://arcprize.org/) being a notable exception. The reason AI has advanced without being anchored in neuroscience is no secret: neuroscience is slow. You can get a lot more reps in with purely _in silico_ experimentation, unanchored by slow wet lab experiments. Thus, the canonical examples of neuroscience influencing AI are decades old: the perceptron, ANNs, CNNs, and RL. Where does that leave the promise of advancing AI through neuroscience?

## Solving a real problem: safety

AI capabilities are increasing, but safety remains to be solved. We’re at the alchemy stage of AI: we have some empirical findings, but we don’t have a general science of intelligence, or how to control it. What if NeuroAI focused on improving AI safety?

To give you one practical example of an unsolved problem in AI safety, consider adversarial examples. Take this photo of my dog Marvin, which is correctly classified as a chihuahua by a pretrained model, and add a little bit of imperceptible, targeted noise to it. Now it’s confidently classified as a microwave [^1].

![](https://substackcdn.com/image/fetch/$s_!r2hG!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3ae46b0e-de52-463d-8c9b-596d798260ae_1919x732.png)

Marvin the adversarial dog.

There have been [over 10,000 articles on adversarial examples](https://nicholas.carlini.com/writing/2019/all-adversarial-example-papers.html), and we have yet to solve them. [A recent study on scaling adversarial training](https://arxiv.org/abs/2404.09349) showed that you would need _multiples of GPT-4 compute_ to solve adversarial robustness on a toy task, CIFAR-10. It’s a giant security hole that will only get amplified as we get multimodal, semi-autonomous agents that can act in the world.

A good way of thinking about this problem, pioneered by [Ilyas et al. (2019)](https://arxiv.org/abs/1905.02175), is in terms of robust and non-robust features. Many features can lead to correct classification. Only some are robust out-of-distribution.

![](https://substackcdn.com/image/fetch/$s_!nKfR!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F7ab36267-f398-480d-92af-1b2fab925fc2_971x457.png)

How to turn a dog can into a microwave. There are many ways of solving this task with non-robust features, and there are many more non-robust features than there are robust features. From Gradient Science.

The more general point is that there are many ways of getting to intelligent behavior, but most of these are not human-like or safe. Recapitulating behavior through imitation learning works in-distribution, but it's an underconstrained problem out-of-distribution.

## Better AI through constraints

The human brain has a number of mechanisms for flexible and safer intelligence. We've evolved sophisticated mechanisms for safe exploration, graceful handling of novel situations, and cooperation. Understanding and reverse-engineering these neural mechanisms _could_ be key to developing AI systems that are aligned with human values.

The human brain might seem like a counterintuitive model for developing safe AI systems: we wage war, we’re biased, and often fall short of our lofty ambitions. But we don’t have to import brains wholesale: we can focus on emulating behaviors and computations that are useful from an AI safety perspective. We call this a selective approach toward studying the brain for AI safety.

The general premise is that more constraints from human brain biophysics, representations, and behavior have a higher probability of leading to the basin of safe, human-like solutions. This is a point that was made previously by Andreas Tolias, one of the co-authors of our roadmap, in [Sinz et al. (2019)](https://www.sciencedirect.com/science/article/pii/S0896627319307408#fig3). They framed it in terms of strong generalization, but you can make the same point about safety more generally.

![](https://substackcdn.com/image/fetch/$s_!lGF_!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F39b7a0a3-d06a-4133-9f1d-9f9448c91b24_2384x886.png)

More constraints=higher chance of getting within the basin of robust, safe solutions. From Sinz et al. (2019).

If you agree with that premise, then the path toward AI safety through neuroscience is to find sources of constraints. That could be done at multiple Marr’s levels, and which approach is most promising is both 1) an empirical question about the effectiveness of each constraint and 2) a question of which approach will get you there fastest given technological bottlenecks in data acquisition and analysis. We tackle both questions in this roadmap.

## Why NeuroAI safety now?

There are a few reasons that have prevented NeuroAI from tackling AI safety. The first is that the AI safety literature is hermetic and neuroscientists, by and large, have not deeply engaged in it. It’s speculative, it moves fast, and it’s hard to get a lay of the land. One of our goals with the roadmap was to make the AI safety literature approachable to neuroscientists by introducing a common framework that we could all refer to. We adapted a framework from Deepmind (2017) for different ways in which AI can be made safer, and refer back to it throughout.

![](https://substackcdn.com/image/fetch/$s_!I3nn!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8ef71cc7-ae9d-45af-bc98-0f44bb8b8c85_1688x1125.png)

A framework for AI safety from Deepmind, adapted for NeuroAI

A second reason is that while there have been a few proposals for how exactly NeuroAI could impact AI safety, these have mostly been at a high level. I haven’t seen a lot of deep technical discussion and analysis on how to get there, and this roadmap fills the gap.

A third reason is tooling. We know a lot more about the brain than we did a decade ago, [most notably in the fly](https://flywire.ai/). Still, our understanding is partial. **If neuroscience is to meaningfully contribute to AI safety, we need to dramatically accelerate our ability to record, analyze, simulate, and understand neural systems**. The catalysts for large-scale neuroscience are already here, thanks in part to massive investments made by the BRAIN Initiative in the past decade. We should take advantage of this moment to learn more about the brain and potentially use that knowledge to impact AI safety. Even if the impact on AI safety is smaller than expected, we’ll still make progress in understanding the most mysterious object in the universe, advancing neurotechnology along the way.

## Highlights from the proposals

[

![](https://substackcdn.com/image/fetch/$s_!3qND!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5fe6ea4f-9eb7-4faf-8e0e-61d8a2c347da_2520x808.png)

](https://substackcdn.com/image/fetch/$s_!3qND!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F5fe6ea4f-9eb7-4faf-8e0e-61d8a2c347da_2520x808.png)

We've organized our roadmap around 7 themes. For each, we perform in-depth technical analysis, identify key bottlenecks and make recommendations for further research and investment:

-   **[Reverse-engineer the representations of sensory systems.](https://neuroaisafety.com/2-sec-reverse-engineer-the-representations-of-sensory-systems)** Understanding how the brain achieves robust perception and handles novel situations could help us build AI systems that are more resistant to adversarial attacks and better at generalizing to new situations. We derived scaling laws for sensory digital twins to determine how much data we’d need to build digital twins of single sensory neurons–they have log-sigmoid scaling curves, which I haven’t seen documented before. We then established one proof-of-concept for how the resulting digital twins could help make AI systems more robust. There is a lot more to be done here.
    
-   **[Create embodied digital twins.](https://neuroaisafety.com/3-sec-embodied)** Functional simulations of brain activity combined with physical models of bodies and environments could help us understand how embodied cognition contributes to safe and robust behavior. I discuss ongoing work in building virtual animal models and foundation models that could help us get there.
    
-   **[Develop detailed simulations.](https://neuroaisafety.com/4-sec-wbs)** Creating detailed biophysical simulations of neural circuits could capture the fundamental constraints of biological intelligence, which serve as templates for building safer AI systems. Connectomics has had a quiet revolution over the last couple of years, and the costs have fallen precipitously from last year’s estimate of 15B$ for a whole-mouse connectome. [E11 Bio, lead by our co-author Andrew Payne, projects that they can achieve 100-fold reduction in cost in 5 years](https://e11.bio/news/roadmap). We have a lot of great background material on light-sheet expansion microscopy and barcoding and discussions on compute necessary to simulate an entire nervous system.
    
-   **[Build better cognitive architectures.](https://neuroaisafety.com/5-sec-develop-better-cognitive-architectures)** Based on our understanding of how the brain implements capabilities like theory of mind, causal reasoning, and cooperation, we could build modular, probabilistic and transparent cognitive architectures that better align with human values and intentions. This section was contributed by [Basis](https://www.basis.ai/) and their collaborators, experts in cognitive architectures. Probabilistic models of cognition are having a moment, and it might be the right time to build an analog of PyTorch for Bayesian cognitive architectures, together with large-scale naturalistic datasets.
    
-   **[Advance brain-informed process supervision.](https://neuroaisafety.com/6-sec-use-brain-data-to-finetune-ai-systems)** Using neural and behavioral data, we could fine-tune existing AI models to better align with brains and encourage safe behavior. This is a surprisingly under-studied area, accessible to many given the existence of large-scale open fMRI datasets. I had to rewrite this section in October in light of [this recent paper](https://arxiv.org/abs/2410.09230) from Mariya Toneva’s lab showing a proof-of-concept in fine-tuning audio models with brain data; things move quickly!
    
-   **[Reverse-engineer loss functions of the brain.](https://neuroaisafety.com/7-sec-infer-the-loss-functions-of-the-brain)** Using functional, structural and behavioral data to determine the loss functions of the brain, we could derive better training objectives for AI systems. We tried to tackle a mystery that has bugged me for a little while: why have visual brain scores stagnated? Can the methods of task-driven neural networks uncover the brain’s true loss functions? And can we use the mapping between RL and the brain to uncover the brain’s reward function? This could be the basis for a robust research program.
    
-   **[Leverage neuroscience-inspired methods for mechanistic interpretability.](https://neuroaisafety.com/8-sec-leverage-neuroscience-inspired-methods-for-mechanistic-interpretability)** At a meta-level, we could apply the tools of neuroscience we use to study biological neural networks to understand artificial ones, and vice-versa. This could help make AI systems more transparent and verifiable, and help us accelerate learning from the brain. I’m impressed with the advances in mechanistic interpretability over the last couple of years, which I hope we port over to neuroscience soon; more on that in a later blog post.
    

_Video_: [Optical reconstruction of brain circuits, from E11Bio](https://e11.bio/news/roadmap).

Now, the paper can be read out of order, but the approaches are not independent – progress in one area means progress in others. What we need to advance AI safety through neuroscience is a **coordinated effort that advances them all in parallel**. This means investing in neurotechnology development, scaling up neural recording capabilities, and building neural models at scale across abstraction levels.

---

Once again, the whole roadmap can be read on:

-   Website: [neuroaisafety.com](https://neuroaisafety.com/)
    
-   [Paper on arXiv](https://arxiv.org/abs/2411.18526)
    

Please reach out to [neuroaisafety@amaranth.foundation](mailto:neuroaisafety@amaranth.foundation) for comments and next steps.

[^1]: While my dog can warm things and has a predilection for popcorn, I’m pretty sure he’s not secretly a microwave.

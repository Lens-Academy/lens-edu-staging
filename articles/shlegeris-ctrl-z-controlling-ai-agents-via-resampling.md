---
title: "Ctrl-Z: Controlling AI Agents via Resampling"
author:
  - "Buck Shlegeris"
source_url: "https://redwoodresearch.substack.com/p/ctrl-z-controlling-ai-agents-via"
published: 2025-04-16
created: 2026-07-02
accessed: 2026-07-02
description: "A new paper on AI control for agents."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

We have released a new paper, _[Ctrl-Z: Controlling AI Agents via Resampling](https://arxiv.org/abs/2504.10374)_. This is the largest and most intricate study of control techniques to date: that is, techniques that aim to prevent catastrophic failures even if egregiously misaligned AIs attempt to subvert the techniques. We extend control protocols to a more realistic, multi-step setting, develop novel _resample protocols_ that outperform all existing control protocols, and study many aspects of control techniques in more detail than prior work. In this blog post, we summarize the main takeaways and lessons learned from our work.

Here’s the abstract of the paper:

> Control evaluations measure whether monitoring and security protocols for AI systems prevent intentionally subversive AI models from causing harm. Our work presents the first control evaluation performed in an agent environment. We construct BashBench, a dataset of 257 challenging multi-step system administration tasks, and evaluate whether various safety measures can prevent an adversarially constructed AI agent from covertly downloading and executing malicious code in this environment. This multi-step setting introduces new attack and defense dynamics, which we investigate in order to design novel control protocols that prevent safety failures without hindering the ability of non-malicious agents to perform useful work. We introduce a class of control protocols called resample protocols that dynamically take additional samples of certain actions. We find these protocols significantly improve on existing techniques by selectively blocking the AI agent from executing suspicious code and incriminating the agent by generating additional examples of dangerous behavior. We measure the tradeoff between attack prevention and usefulness; our best protocol combines resampling with analysis of previous steps, reducing the success rate of attacks from 58% to 7% at a 5% cost to the performance of a non-malicious agent.

This paper builds heavily on Redwood’s first paper on control evaluations, _[AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942)._ If you haven’t read that paper, or are new to AI control, we think you’d get more value out of this post after reading it, along with _[The case for ensuring that powerful AIs are controlled](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)_ (a more extensive reading list can be found [here](https://www.redwoodresearch.org/reading-list)). Buck Shlegeris also talks about our new paper, and the core ideas of AI control more broadly, in [his recent interview on the 80,000 Hours podcast](https://80000hours.org/podcast/episodes/buck-shlegeris-ai-control-scheming/).

[

![](https://substackcdn.com/image/fetch/$s_!_JD3!,w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffa4b0f84-2966-4f41-9547-254dbfe3bfdc_1896x936.jpeg)

](https://substackcdn.com/image/fetch/$s_!_JD3!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffa4b0f84-2966-4f41-9547-254dbfe3bfdc_1896x936.jpeg)

This work was conducted by: Aryan Bhatt, Cody Rushing, Adam Kaufman, Tyler Tracy, Vasil Georgiev, David Matolcsi, Akbir Khan, and Buck Shlegeris.

Website: [http://bashcontrol.com](http://bashcontrol.com/)

Paper link: [https://arxiv.org/abs/2504.10374](https://t.co/s0SKZENBf3)

More discussion [here](https://www.alignmentforum.org/posts/LPHMMMZFAWog6ty5x/ctrl-z-controlling-ai-agents-via-resampling).

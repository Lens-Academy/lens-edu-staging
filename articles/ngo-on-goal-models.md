---
title: "On Goal-Models"
author:
  - "Richard Ngo"
source_url: "https://www.lesswrong.com/posts/MEkafPJfiSFbwCjET/on-goal-models"
published: 2026-02-02
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "I'd like to reframe our understanding of the goals of intelligent agents to be in terms of goal-models rather than utility functions. By a goal-model…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

I'd like to reframe our understanding of the goals of intelligent agents to be in terms of _goal-models_ rather than _utility functions_. By a goal-model I mean the same type of thing as a world-model, only representing how you _want_ the world to be, not how you think the world _is_. However, note that this still a fairly inchoate idea, since I don't actually know what a world-model is. The rest of this post contains some fairly abstract musings on goal-models and their relationship to utility functions.

The concept of goal-models is broadly inspired by predictive processing, which treats both beliefs and goals as generative models of observations and actions (the former primarily predicting observations, the latter primarily “predicting” actions). This is a very useful idea, which e.g. allows us to talk about the “distance” between a belief and a goal, and the process of moving “towards” a goal (neither of which make sense from a reward/utility function perspective).

However, I’m dissatisfied by the idea of defining a world-model as a generative model over observations. It feels analogous to defining a parliament as a generative model over laws. Yes, technically we can think of parliaments as stochastically outputting laws, but actually the interesting part is in _how_ they do so. In the case of parliaments, you have a process of internal disagreement and bargaining, which then leads to some compromise output. In the case of world-models, we can perhaps think of them as made up of many smaller (partial) generative models, which sometimes agree and sometimes disagree. The real question is in how they reach enough of a consensus to produce a single output prediction.

One potential model of that consensus-formation process comes from the [probabilistic dependency graph formalism](https://arxiv.org/abs/2202.11862), which is a version of Bayesian networks in which different nodes are allowed to “disagree” with each other. The most principled way to convert a PDG into a single distribution is to find the distribution which minimizes the inconsistency between all of its nodes. PDGs seem promising in some ways, but I feel suspicious of any “global” metric of inconsistency. Instead I’m interested in scale-free approaches under which inconsistencies mostly get resolved locally (though it’s worth noting that Oliver’s proposed [practical algorithm for inconsistency minimization](https://openreview.net/pdf?id=5VTeqSXLCo) is a local one).

It’s also possible that the predictive processing/active inference people have a better model of this process which I don’t know about, since I haven’t made it very deep into that literature yet.

Anyway, suppose we’re thinking of goal-models as generative models of observations and actions for now. What does this buy us over understanding goals in terms of utility functions? The key tradeoff is that utility functions are _global_ but _shallow_ whereas goal-models are _local_ but _deep_.

That is: we typically think of a utility function as something that takes as input any state (or alternatively any trajectory) of the world, and spits out a real number. Central examples of utility functions are therefore functions of fairly simple features which can be evaluated in basically all possible worlds—for example, functions of the consumption of a basket of goods (in economics) or functions of the welfare of individuals (in axiology).

Conversely, consider having a goal of creating a beautiful painting or a great cathedral. You can’t evaluate the outcome as a function of simple features (like quality of brush-strokes, quality of composition, etc). Instead, you have some sense of what the ideal is, which might include the ways in which each part of the painting or cathedral fits together. It might be very hard to then actually give meaningful scores to how “far” a given cathedral is from your ideal, or whether you’d pick an X% chance of one cathedral vs a Y% chance of another. Indeed, that feels like the wrong question to ask—part of what makes artists and architects great is when they _aren’t_ willing to compromise in pursuit of their vision. Instead, they’re constantly moving in whichever direction seems like it’ll bring them closer to their single ultimate goal.

This is related to [Demski’s distinction between _selection_ and _control_](https://www.lesswrong.com/posts/ZDZmopKquzHYPRNxq/selection-vs-control) as two types of optimization. A rocket that’s fixed on a target isn’t calculating how good or bad it would be to miss in any given direction. Instead, it’s constantly checking whether it’s on track, then adjusting to maintain its trajectory. The question is whether we can think of intelligent agents as “steering” through much higher-dimensional spaces in an analogous way. I think this makes most sense when you’re close enough (aka “local”) to your goal. For example, we can think of a CEO as primarily trying to keep their company on a stable upwards trajectory.

Conversely, a high school student who wants to be the CEO of a major company is so far away from their goal that it’s hard to think of them as _controlling_ their path towards it. Instead, they first need to select between plans for becoming such a CEO based on how likely each plan is to succeed. Similarly, a dancer or a musician is best described as carrying out a control process when practicing or performing—but needed to make a discrete choice of which piece to learn, and more generally which instrument or dance style to focus on, and even more generally which career path to pursue at all. And of course a rocket needs to first select which target to focus on at all before it aims towards it.

So it’s tempting to think about selection as the “outer loop” and control as the “inner loop”. But I want to offer an alternative view. Where do we even get the criteria on which we make selections? I think it’s actually another control process—specifically, the process of controlling our _identities_. We have certain conceptions of ourselves (“I’m a good person” or “I’m successful” or “people love me”.) We then are constantly adjusting our lives and actions in order to maintain those identities—e.g. by selecting the goals and plans which are most consistent with them, and looking away from evidence that might falsify our identities. So perhaps our outermost loop is a control process after all.

These identities (or “identity-models”) are inherently local in the sense that they are about _ourselves_, not the wider world. If we each pursued our own individual goals and plans derived from our individual identities, then it would be hard for us to cooperate. However, one way to scale up identity-based decision-making is to develop identities with the property that, when many people pursue them, those people become a “[distributed agent](https://www.mindthefuture.info/p/elite-coordination-via-the-consensus)” able to act in sync.

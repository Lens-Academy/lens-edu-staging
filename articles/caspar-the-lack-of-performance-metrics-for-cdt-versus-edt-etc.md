---
title: "The lack of performance metrics for CDT versus EDT, etc."
author:
  - "Caspar"
source_url: "https://casparoesterheld.com/2022/07/17/the-lack-of-performance-metrics-for-cdt-versus-edt-versus/"
published: 2022-07-17
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "(This post assumes that the reader is fairly familiar with the decision theory of Newcomb-like problems. Schwarz makes many of the same points in his post “On Functional Decision Theory” (though I …"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

(This post assumes that the reader is fairly familiar with the decision theory of Newcomb-like problems. Schwarz makes many of the same points in his post [“On Functional Decision Theory”](https://www.umsu.de/wo/2018/688) (though I disagree with him on other things, such as whether to one-box or two-box in Newcomb’s problem). Similar points have also been made many times about the concept of updatelessness in particular, e.g., see Section 7.3.3 of Arif Ahmed’s book “Evidence, Decision and Causality”, [my post on updatelessness from a long time ago](https://casparoesterheld.com/2016/11/21/thoughts-on-updatelessness/), or Sylvester Kollin’s [“Understanding updatelessness in the context of EDT and CDT”](https://www.lesswrong.com/posts/d6YQyRfoFNtbKjtGt/understanding-updatelessness-in-the-context-of-edt-and-cdt-1). Preston Greene, on the other hand, argues explicitly for a view opposite of the one in this post in his paper [“Success-First Decision Theories”](https://philarchive.org/archive/GRESDT). ETA: Similar points have also been made w.r.t. the “Why ain’cha rich?” argument, which is an argument for EDT (and other one-boxing theories) and against CDT based on Newcomb’s problem. See, for example, [Bales (2018)](https://link.springer.com/content/pdf/10.1007/s11229-016-1214-x.pdf) and [Wells (2019)](https://philpapers.org/archive/WELEOA.pdf) (thanks to Sylvester Kollin and Miles Kodama, respectively, for pointing out these papers).)

I sometimes read the claim that one decision theory “outperforms” some other decision theory (in general or in a particular problem). For example, [Yudkowsky and Soares (2017)](https://arxiv.org/pdf/1710.05060.pdf) write: “FDT agents attain high utility in a host of decision problems that have historically proven challenging to CDT and EDT: FDT outperforms CDT in Newcomb’s problem; EDT in the smoking lesion problem; and both in Parfit’s hitchhiker problem.” Others use some variations of this framing (“[dominance](http://intelligence.org/files/ProblemClassDominance.pdf)”, “winning”, etc.), some of which I find less dubious because they have less formal connotations.

Based on typical usage, these words make it seem as though there was some agreed upon or objective metric to compare decision theories in any particular problem and that MIRI is claiming to have found a theory that is better according to that metric (in some given problems). This would be similar to how one might say that one machine learning algorithm outperforms another on the [CIFAR dataset](https://www.cs.toronto.edu/~kriz/cifar.html), where everyone agrees that ML algorithms are better if they correctly classify a higher percentage of the images, require less computation time, fewer samples during training, etc.

However, there is no agreed-upon metric to compare decision theories, no way to asses even for a particular problem whether one decision theory (or its recommendation) does better than another. (This is why the CDT-versus-EDT-versus-other debate is at least partly a philosophical one.) In fact, it seems plausible that finding such a metric is “decision theory-complete” (to butcher [another term](https://en.wikipedia.org/wiki/Complete_\(complexity\)) with a specific meaning in computer science). By that I mean that settling on a metric is probably just as hard as settling on a decision theory and that mapping between plausible metrics and plausible decision theories is fairly easy.

For illustration, consider Newcomb’s problem and a few different metrics. One possible metric is what one might call the causal metric, which is the expected payoff if we were to replace the agent’s action with action X by some intervention from the outside. Then, for example, in Newcomb’s problem, two-boxing “performs” better than one-boxing and CDT “outperforms” FDT. I expect that many causal decision theorists would view something of this ilk as the right metric and that CDT’s recommendations are optimal according to the causal metric in a broad class of decision problems.

A second possible metric is the evidential one: given that I observe that the agent uses decision theory X (or takes action Y) in some given situation, how big of a payoff do I expect the agent to receive. This metric directly favors EDT in Newcomb’s problem, the smoking lesion, and again a broad class of decision problems.

A third possibility is a modification of the causal metric. Rather than replacing the agent’s decision, we replace its entire decision algorithm before the predictor looks at and creates a model of the agent. Despite being causal, this modification favors decision theories that recommend one-boxing in Newcomb’s problem. In general, the theory that seems to maximize this metric is some kind of updateless CDT (cf. [Fisher’s disposition-based decision theory](https://casparoesterheld.com/wp-content/uploads/2019/02/dbdt.pdf)).

Yet another causalist metric involves replacing from the outside the decisions of not only the agent itself but also of all agents that use the same decision procedure. Perhaps this leads to [Timeless Decision Theory](http://intelligence.org/files/TDT.pdf) or [Wolfgang Spohn’s proposal for causalist one-boxing](http://www-personal.umich.edu/~ericsw/2fef/One-Boxing3.pdf).

One could also use the notion of regret (as discussed in the literature on multi-armed bandit problems) as a performance measure, which probably leads to ratificationism.

Lastly, I want to bring up what might be the most commonly used class of metrics: intuitions of individual people. Of course, since [intuitions vary between different people](https://casparoesterheld.com/2017/06/27/a-survey-of-polls-on-newcombs-problem/), intuition provides no agreed upon metric. It does, however, provide a non-vacuous (albeit in itself weak) justification for decision theories. Whereas it seems unhelpful to defend CDT on the basis that it outperforms other decision theories according to the causal metric but is outperformed by EDT according to the evidential metric, it is interesting to consider which of, say, EDT’s and CDT’s recommendations seem intuitively correct.

Given that finding the right metric for decision theory is similar to the problem of decision theory itself, it seems odd to use words like “outperforms” which suggest the existence or assumption of a metric.

I’ll end with a few disclaimers and clarifications. First, I don’t want to discourage looking into metrics and desiderata for decision theories. I think it’s unlikely that this approach to discussing decision theory can resolve disagreements between the different camps, but that’s true for all approaches to discussing decision theory that I know of. (An interesting formal desideratum that doesn’t trivially relate to decision theories is discussed in my blog post [_Decision Theory and the Irrelevance of Impossible Outcomes_](https://casparoesterheld.com/2017/01/17/decision-theory-and-the-irrelevance-of-impossible-outcomes/). At its core, it’s not really about “performance measures”, though.)

Second, I don’t claim that the main conceptual point of this post is new to, say, Nate Soares or Eliezer Yudkowsky. In fact, they have written similar things, see, for instance, [Ch. 13 of Yudkowsky’s _Timeless Decision Theory_](http://intelligence.org/files/TDT.pdf#page=103), in which he argues that decision theories are untestable because counterfactuals are untestable. Even in the aforementioned paper, claims about outperforming are occasionally qualified. E.g., [Yudkowsky and Soares (2017, sect. 10)](https://arxiv.org/pdf/1710.05060.pdf) say that they “do not yet know \[…\] (on a formal level) what optimality consists in”.) Unfortunately, most outperformance claims remain unqualified. The metric is never specified formally or discussed much. The short verbal descriptions that are given make it hard to understand how their metric differs from the metrics corresponding to updateless CDT or updateless EDT.

So, my complaint is not so much about these authors’ views but about a [Motte and Bailey](https://rationalwiki.org/wiki/Motte_and_bailey)-type inconsistency, in which the takeaways from reading the paper superficially are much stronger than the takeaways from reading the whole paper in-depth and paying attention to all the details and qualifications. I’m worried that the paper gives many casual readers the wrong impression. For example, gullible non-experts might get the impression that decision theory is like ML in that it is about finding algorithms that perform as well as possible according to some agreed-upon benchmarks. Uncharitable, sophisticated skim-readers may view MIRI’s positions as naive or confused about the nature of decision theory.

In my view, the lack of an agreed-upon performance measure is an important fact about the nature of decision theory research. Nonetheless, I think that, e.g., MIRI is doing and has done very valuable work on decision theory. More generally I suspect that being wrong or imprecise about this issue (that is, about the lack of performance metrics in the decision theory of Newcomb-like problems) is probably not an obstacle to having good object-level ideas. (Similarly, while I’m not a moral realist, I think being a moral realist is not necessarily an obstacle to saying interesting things about morality.)

:::hide
### Acknowledgement ^acknowledgement

This post is largely inspired by conversations with Johannes Treutlein. I also thank Emery Cooper for helpful comments.
:::

---
title: "Goodhart's Law"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/goodhart-s-law"
published: 2026-09-23
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Goodhart's Law states that when a proxy for some value becomes the target of optimization pressure, the proxy will cease to be a good proxy. This article covers Scott Garrabrant's taxonomy of regressional, causal, extremal, and adversarial Goodharting, and the law's relevance to AI Alignment."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**Goodhart's Law** states that when a proxy for some value becomes the target of optimization pressure, the proxy will cease to be a good proxy. One form of Goodhart is demonstrated by the Soviet story of a factory graded on how many shoes they produced (a good proxy for productivity) – they soon began producing a higher number of tiny shoes. Useless, but the numbers look good.

Goodhart's Law is of particular relevance to [AI Alignment](https://www.lesswrong.com/w/ai). Suppose you have something which is generally a good proxy for "the stuff that humans care about". If you make a powerful AI optimize for this proxy, Goodhart's law predicts that the proxy will break down.

Why does this happen? The proxy can at best partially describe your real goal. An optimizer will optimize for the entire proxy, not just the part you wanted optimized. Examples of how this happens are provided by the taxonomy below.

## Goodhart Taxonomy ^goodhart-taxonomy

In [Goodhart Taxonomy](https://www.lesswrong.com/posts/EbFABnst8LsidYs5Y/goodhart-taxonomy), Scott Garrabrant identifies four kinds of Goodharting:

-   Regressional Goodhart - When selecting for a proxy measure, you select not only for the true goal, but also for the difference between the proxy and the goal.
-   Causal Goodhart - When there is a non-causal correlation between the proxy and the goal, intervening on the proxy may fail to intervene on the goal.
-   Extremal Goodhart - Worlds in which the proxy takes an extreme value may be very different from the ordinary worlds in which the correlation between the proxy and the goal was observed.
-   Adversarial Goodhart - When you optimize for a proxy, you provide an incentive for adversaries to correlate their goal with your proxy, thus destroying the correlation with your goal.

## See Also ^see-also

-   [Groupthink](https://www.lesswrong.com/w/groupthink), [Information cascade](https://www.lesswrong.com/w/information-cascades), [Affective death spiral](https://www.lesswrong.com/w/affective-death-spiral)
-   [Adaptation executers](https://wiki.lesswrong.com/wiki/Adaptation_executers), [Superstimulus](https://www.lesswrong.com/w/superstimuli)
-   [Signaling](https://www.lesswrong.com/w/signaling), [Filtered evidence](https://www.lesswrong.com/w/filtered-evidence)
-   [Cached thought](https://www.lesswrong.com/w/cached-thought)
-   [Modesty argument](https://www.lesswrong.com/w/modesty-argument), [Egalitarianism](https://www.lesswrong.com/w/egalitarianism)
-   [Rationalization](https://www.lesswrong.com/w/rationalization), [Dark arts](https://www.lesswrong.com/w/dark-arts)
-   [Epistemic hygiene](https://www.lesswrong.com/w/epistemic-hygiene)
-   [Scoring rule](https://www.lesswrong.com/w/scoring-rule)

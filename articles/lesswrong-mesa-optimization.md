---
title: "Mesa-Optimization"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/mesa-optimization"
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
description: "Mesa-Optimization is the situation that occurs when a learned model (such as a neural network) is itself an optimizer. In this situation, a base optimizer creates a second optimizer, called a mesa-optimizer. The primary reference work for this concept is Hubinger et al."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**Mesa-Optimization** is the situation that occurs when a learned model (such as a neural network) is itself an optimizer. In this situation, a _base optimizer_ creates a second optimizer, called a _mesa-optimizer_. The primary reference work for this concept is Hubinger et al.'s "[Risks from Learned Optimization in Advanced Machine Learning Systems](https://www.lesswrong.com/posts/FkgsxrGf3QxhfLWHG/risks-from-learned-optimization-introduction)".

Example: Natural selection is an optimization process that optimizes for reproductive fitness. Natural selection produced humans, who are themselves optimizers. Humans are therefore mesa-optimizers of natural selection.

In the context of AI alignment, the concern is that a base optimizer (e.g., a gradient descent process) may produce a learned model that is itself an optimizer, and that has unexpected and undesirable properties. Even if the gradient descent process is in some sense "trying" to do exactly what human developers want, the resultant mesa-optimizer will not typically be trying to do the exact same thing.

## History ^history

Previously work under this concept was called _Inner Optimizer_ or _Optimization Daemons._

In 2003 [Wei Dai](https://www.lesswrong.com/users/wei_dai) brings up a similar idea in an SL4 thread ['"friendly" humans?'](http://sl4.org/archive/0312/7421.html).

Yudkowsky's ["Optimization daemons"](https://www.lesswrong.com/w/optimization-daemons) was published on [Arbital](https://arbital.com/) probably in 2016.

[Jessica Taylor](https://www.lesswrong.com/users/jessica-liu-taylor) wrote two posts about daemons while at [MIRI](https://www.lesswrong.com/w/machine-intelligence-research-institute-miri):

-   ["Are daemons a problem for ideal agents?"](https://www.lesswrong.com/posts/5bd75cc58225bf067037535e/are-daemons-a-problem-for-ideal-agents) (2017-02-11)
-   ["Maximally efficient agents will probably have an anti-daemon immune system"](https://www.lesswrong.com/posts/5bd75cc58225bf0670375367/maximally-efficient-agents-will-probably-have-an-anti-daemon-immune-system) (2017-02-23)

## See also ^see-also

-   [Inner Alignment](https://www.lesswrong.com/w/inner-alignment)
-   [Complexity of value](https://www.lesswrong.com/w/complexity-of-value)
-   [Thou Art Godshatter](https://www.lesswrong.com/lw/l3/thou_art_godshatter)

## External links ^external-links

[Video by Robert Miles (23min)](https://www.youtube.com/watch?v=bJLcIBixGj8)

Some posts that reference optimization daemons:

-   ["Cause prioritization for downside-focused value systems"](http://effective-altruism.com/ea/1k4/draft_cause_prioritization_for_downsidefocused/): "Alternatively, perhaps goal preservation becomes more difficult the more capable AI systems become, in which case the future might be controlled by unstable goal functions taking turns over the steering wheel"
-   ["Techniques for optimizing worst-case performance"](https://ai-alignment.com/techniques-for-optimizing-worst-case-performance-39eafec74b99): "The difficulty of optimizing worst-case performance is one of the most likely reasons that I think prosaic AI alignment might turn out to be impossible (if combined with an unlucky empirical situation)." (the phrase "unlucky empirical situation" links to the optimization daemons page on [Arbital](https://arbital.com/))

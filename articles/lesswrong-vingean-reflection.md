---
title: "Vingean reflection"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/vingean-reflection"
published: 2016-06-21
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "Vingean reflection is reasoning about cognitive systems, especially cognitive systems very similar to yourself, under the constraint that you can't predict the exact future outputs."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

[Vinge's Principle](https://www.lesswrong.com/w/vinge-s-principle) implies that when an agent is designing another agent (or modifying its own code), it needs to approve the other agent's design without knowing the other agent's exact future actions.

Deep Blue's programmers decided to run Deep Blue, _without_ knowing Deep Blue's exact moves against Kasparov or how Kasparov would reply to each move, and without being able to visualize the exact real-outcome instead. Instead, by reasoning about the way Deep Blue was searching through game trees, they arrived at a well-justified but abstract belief that Deep Blue was 'trying to win' (rather than trying to lose) and reasoning effectively to that end.

[Vingean reflection](https://www.lesswrong.com/w/vingean-reflection) is reasoning about cognitive systems, especially cognitive systems very similar to yourself (including your actual self), under the constraint that you can't predict the exact future outputs. We need to make predictions about the consequence of operating an agent in an environment via reasoning on some more abstract level, somehow.

In [tiling agents theory](https://www.lesswrong.com/w/tiling-agents-theory), this appears as the rule that we should talk about our successor's actions only inside of quantifiers.

"Vingean reflection" may be a much more general issue in the design of advanced cognitive systems than it might appear at first glance. An agent reasoning about the consequences of _its current code_, or considering what will happen if it _spends another minute thinking,_ can be viewed as doing Vingean reflection. A reflective, self-modeling chess-player would not choose to spend another minute thinking, if it thought that its further thoughts would be trying to lose rather than win the game - but it can't predict its own exact thoughts in advance.

Vingean reflection can also be seen as the study of how a given agent _wants_ thinking to occur in cognitive computations, which may be importantly different from how the agent _currently_ thinks. If these two coincide, we say the agent is [reflectively stable](https://www.lesswrong.com/w/reflective-stability).

[Tiling agents theory](https://www.lesswrong.com/w/tiling-agents-theory) is presently the main line of research trying to slowly get started on formalizing Vingean reflection and reflective stability.

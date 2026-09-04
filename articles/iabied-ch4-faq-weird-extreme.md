---
title: "If current AIs are mostly weird in extreme cases, what's the problem?"
source_url: https://ifanyonebuildsit.com/4/if-current-ais-are-mostly-weird-in-extreme-cases-whats-the-problem
published: 2025-09-16
author:
  - "Eliezer Yudkowsky"
  - "Nate Soares"
tags:
  - clippings
llm-review:
  date: 2026-09-04
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-04
    kind: "live"
---
%%
Add discussion note here:

This is a very short entry that leans heavily on a single argument (optimization tends to push unconstrained variables to extremes) and explicitly defers the fuller discussion to Chapters 5 and 6. Editors may want to note for readers that this page functions more as a bridge/pointer than a self-contained argument.

%%

#### The weirdness is evidence that their actual pursuits aren't our intended pursuits. ^the-weirdness-is-evidence-that-their-actual-pursuits-arent-our-intended-pursuits

This matters more as the AI gets more options. Once an AI becomes superintelligent, practically every choice becomes extreme, as the AI gains access to a world of different options that no human or AI has ever had. Like how almost all of your food options, here in a technological civilization, are "extreme" compared to what options your ancestors had available to them.

AIs today may only occasionally encounter situations that are radically unlike their training environment; but superintelligent AI would *constantly* be in situations that are radically unlike its training environment, just by virtue of being more intelligent and having more options (and the technological capacity to invent radical new options, like humans had when inventing ice cream). So it's not reassuring in the slightest for the AI to misbehave only in extreme cases.

To put it more technically: The best solution to any given problem tends to occur at the extremes.[^note-iabied-ftnt124]

We'll discuss these points more in Chapters 5 and 6.

[^note-iabied-ftnt124]: As Stuart Russell, co-author of *Artificial Intelligence: A Modern Approach*, [puts it](https://www.edge.org/conversation/the-myth-of-ai#26015): "A system that is optimizing a function of *n* variables, where the objective depends on a subset of size *k*<*n*, will often set the remaining unconstrained variables to extreme values; if one of those unconstrained variables is actually something we care about, the solution found may be highly undesirable." The fundamental theorem of linear programming states that this is certain when optimizing a linear function over a convex polygonal region. A similar result tends to hold in practice in more general contexts, because a lot of optimization problems bear a similarity to optimizing a linear function over a convex polygonal region.
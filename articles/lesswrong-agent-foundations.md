---
title: "Agent Foundations"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/agent-foundations"
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
description: "There are fundamental confusions about intelligent agents, that is, about minds that try to make stuff that they want happen. Some believe that working out these fundamental confusions is necessary for AI alignment. Others prefer more prosaic approaches; or something else not mentioned."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

There are fundamental confusions about intelligent agents, that is, about minds that try to make stuff that they want happen. Some believe that working out these fundamental confusions is necessary for [AI alignment](https://www.lesswrong.com/w/ai-alignment). Others prefer more [prosaic approaches](https://www.lesswrong.com/w/prosaic-alignment); or something else not mentioned.

Here's some fundamental confusions that agent foundations tries to answer, mostly informed by the post/paper [Embedded Agency](https://www.lesswrong.com/s/Rm6oQRJJmhGCcLvxh/p/i3BTagvt3HbPMx6PN):

-   How can a mind reason about a world too large to consider in its entirety? Perhaps we should look at [what sorts of abstractions](https://www.lesswrong.com/w/natural-abstraction) they'd use; perhaps we need new _imprecise_ probability theories like [infra-bayesianism](https://www.lesswrong.com/w/infra-bayesianism).
-   How can a mind reason when it does not know all of the implications of its beliefs (that is, it has [logical uncertainty](https://www.lesswrong.com/w/logical-uncertainty))?
-   How can a mind reason about (possibly logical) counterfactuals to make [decisions](https://www.lesswrong.com/w/logical-decision-theories)? This includes problems of multi-agent cooperation/competition, especially if the [agents have the others source code](https://www.lesswrong.com/w/open-source-game-theory), or if one is smarter than the other.
-   How can a mind reason about _itself_, or [improve itself](https://www.lesswrong.com/w/tiling-agents)? Self reasoning seems to cause a lotta problems: you can't have a full picture of yourself because then you'd also have to include the picture in your picture; and it sorta looks like decision theory problems are related. As an example, to improve itself, an agent will want to ensure that its successor will still be optimizing for the same goals, and do a better job at it - and also create successors that do better than the ones the agent would make. Yet by [Vinge's principle](https://www.lesswrong.com/w/vinge-s-principle), you can't in general know exactly what something smarter than you would think, as then you would just be at least that smart. So you must do so by reasoning abstractly about properties the prospective mind-designs have and will preserve in their successors. This is a simplified version of the problem humanity faces when creating an aligned AI - it is basically the alignment problem for agents with well-defined utility functions that themselves know their utility function.
-   What even is an "agent"? What sorts of agents should we expect to be [selected for](https://www.lesswrong.com/w/selection-theorems) by evolution or gradient descent or any other selection process?
-   What are "goals"? How do we formalize a [goal that's about the world, instead of our beliefs _about_ the world (or our observations)](https://www.lesswrong.com/w/the-pointers-problem)? Even something as simple as " [maximize the number of diamond atoms](https://www.lesswrong.com/w/diamond-maximizer) " has no clear route to formalization! As an example, what happens if you specify the goal in terms of classical physics, and then tomorrow the AI realizes that quantum mechanics is how reality actually works, then it might end up caring about nothing (since "diamond atom" no longer means anything). If you try to solve the problem, you'll have to have a way to make the AI identify its previous goal-concept of "diamond atom" with something in the new world model.
-   Preferences are usually expressed in terms of a utility function, as justified by theorems like the [VNM theorem](https://www.lesswrong.com/w/vnm-theorem). But can we make sensible theories of rational preferences and decisions that relax the axioms? One consideration is to specify that the agents do not get Dutch-booked, but nothing else. This was suggested in [logical induction](https://www.lesswrong.com/w/logical-induction) and [radical probabilism](https://www.lesswrong.com/w/radical-probabilism).
-   How should an agent update on the fact that it exists? The [anthropic puzzles](https://www.lesswrong.com/w/anthropics) and attempted solutions seem to get at questions about how beliefs, updating, and logical decision theories should work. For example, some conclude that we should just ditch 'beliefs' as a base concept entirely, only keeping notions of expected utility!
-   Is there a natural/simple shape of agent that lets you [correct its goals](https://www.lesswrong.com/w/corrigibility-1), without trying to stop you or trying to make you correct it or anything weird like that? The [shutdown problem](https://www.lesswrong.com/w/shutdown-problem) is a simple version, dealing with the case of letting the creators do a single bit of correction.
-   If we get insight into the preceding, can we make something like [AIXI](https://www.lesswrong.com/w/aixi) but incorporating the insights? As an example, perhaps the correct description language (like first-order logic) for theories or observables needs to be modified (instead of using turing machines).

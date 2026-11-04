---
title: "Nearest unblocked strategy"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/p/nearest_unblocked"
published: 2015-04-05
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "If you patch an agent"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

link to epistemic version [http://lesswrong.com/lw/nki/jfk\_was\_not\_assassinated\_prior\_probability\_zero/d9h3?context=3](https://www.lesswrong.com/posts/xEdJfK8dYRm6YSE8w/jfk-was-not-assassinated-prior-probability-zero-events?commentId=AhGLPp7q6cpmShLqy)

# Introduction ^introduction

‘Nearest unblocked strategy’ seems like it should be a [foreseeable](https://arbital.greaterwrong.com/p/foreseeable_difficulties?l=6r) problem of trying to get rid of undesirable AI behaviors by adding specific penalty terms to them, or otherwise trying to exclude one class of observed or foreseen bad behaviors. Namely, if a decision criterion thinks \\(X\\) is the best thing to do, and you add a penalty term \\(P\\) that you think excludes everything inside \\(X,\\) the _next-best_ thing to do may be a very similar thing \\(X'\\) which is the most similar thing to \\(X\\) that doesn’t trigger \\(P.\\)

## Example: Producing happiness. ^example-producing-happiness

Some very early proposals for AI alignment suggested that AIs be targeted on producing human happiness. Leaving aside various other objections, arguendo, imagine the following series of problems and attempted fixes:

-   By hypothesis, the AI is successfully infused with a goal of “human happiness” as a utility function over human brain states. (Arguendo, this predicate is narrowed sufficiently that the AI does not just want to construct [the tiniest, least resource-intensive brains experiencing the largest amount of happiness per erg of energy](https://arbital.greaterwrong.com/p/edge_instantiation?l=2w).)
    
-   Initially, the AI seems to be pursuing this goal in good ways; it organizes files, tells funny jokes, helps landladies take out the garbage, etcetera.
    
-   Encouraged, the programmers further improve the AI and add more computing power.
    
-   The AI gains a better understanding of the world, and the AI’s [policy space expands](https://arbital.greaterwrong.com/p/context_disaster?l=6q) to include conceivable options like “administer heroin”.
    
-   The AI starts planning how to administer heroin to people.
    
-   The programmers notice this before it happens. (Arguendo, due to successful transparency features, or an imperative to [check plans with the users](https://arbital.greaterwrong.com/p/user_querying?l=2qq), which operated as [intended](https://arbital.greaterwrong.com/p/intended_goal?l=6h) at the AI’s current level of intelligence.)
    
-   The programmers edit the AI’s utility function and add a penalty of −100 utilons for any event categorized as “the AI administers heroin to humans”. (Arguendo, the AI’s current level of intelligence does not suffice to prevent the programmers from editing its utility function, despite the convergent instrumental incentive to avoid this; nor does it successfully [deceive](https://arbital.greaterwrong.com/p/programmer_deception?l=10f) the programmers.)
    
-   The AI gets slightly smarter. New conceivable options enter the AI’s option space.
    
-   The AI starts wanting to administer cocaine to humans (instead of heroin).
    
-   The programmers read through the current schedule of prohibited drugs and add penalty terms for administering marijuana, cocaine, etcetera.
    
-   The AI becomes slightly smarter. New options enter its policy space.
    
-   The AI starts thinking about how to research a new happiness drug not on the list of drugs that its utility function designates as bad.
    
-   The programmers, after some work, manage to develop a category for ‘The AI forcibly administering any kind of psychoactive drug to humans’ which is broad enough that the AI stops suggesting research campaigns to develop things slightly outside the category.
    
-   The AI wants to build an external system to administer heroin, so that it won’t be classified inside this set of bad events “the AI forcibly administering drugs”.
    
-   The programmers generalize the penalty predicate to include “machine systems in general forcibly administering heroin” as a bad thing.
    
-   The AI recalculates what it wants, and begins to want to pay humans to administer heroin.
    
-   The programmers try to generalize the category of penalized events to include non-voluntarily administration of drugs in general that produce happiness, whether done by humans or AIs. The programmers patch this category so that the AI is not trying to shut down at least the nicer parts of psychiatric hospitals.
    
-   The AI begins planning an ad campaign to persuade people to use heroin voluntarily.
    
-   The programmers add a penalty of −100 utilons for “AIs _persuading_ humans to use drugs”.
    
-   The AI goes back to helping landladies take out the garbage. All seems to be well.
    
-   The AI continues to increase in intelligence, becoming capable enough that the AI can no longer be edited against its own will.
    
-   The AI notices the option “Tweak human brains to express extremely high levels of endogenous opiates, then take care of their twitching bodies so they can go on being happy”.
    

The overall story is one where the AI’s preferences on round \\(i,\\) denoted \\(U\_i,\\) are observed to arrive at an attainable optimum \\(X\_i\\) which the humans see as undesirable. The humans devise a penalty term \\(P\_i\\) intended to exclude the undesirable parts of the policy space, and add this to \\(U\_i\\) creating a new utility function \\(U\_{i+1},\\) after which the AI’s optimal policy settles into a new state \\(X\_i^\*\\) that seems acceptable. However, after the next expansion of the policy space, \\(U\_{i+1}\\) settles into a new attainable optimum \\(X\_{i+1}\\) which is very similar to \\(X\_i\\) and makes the minimum adjustment necessary to evade the boundaries of the penalty term \\(P\_i,\\) requiring a new penalty term \\(P\_{i+1}\\) to exclude this new misbehavior.

(The end of this story _might_ not kill you if the AI had enough successful, [advanced-safe](https://arbital.greaterwrong.com/p/advanced_safety?l=2l) [corrigibility features](https://arbital.greaterwrong.com/p/corrigibility?l=45) that the AI would [indefinitely](https://arbital.greaterwrong.com/p/omni_test?l=2x) go on [checking](https://arbital.greaterwrong.com/p/user_querying?l=2qq) [novel](https://arbital.greaterwrong.com/p/conservative_concept?l=2qp) policies and [novel](https://arbital.greaterwrong.com/p/conservative_concept?l=2qp) goal instantiations with the users, not strategically hiding its disalignment from the programmers, not deceiving the programmers, letting the programmers edit its utility function, not doing anything disastrous before the utility function had been edited, etcetera. But you wouldn’t want to rely on this. You would not want in the first place to operate on the paradigm of ‘maximize happiness, but not via any of these bad methods that we have already excluded’.)

# Preconditions ^preconditions

Recurrence of a nearby unblocked strategy is argued to be a [foreseeable difficulty](https://arbital.greaterwrong.com/p/foreseeable_difficulties?l=6r) given the following preconditions:

• The AI is a [consequentialist](https://arbital.greaterwrong.com/p/consequentialist?l=9h), or is conducting some other search such that when the search is blocked at \\(X,\\) the search may happen upon a similar \\(X'\\) that fits the same criterion that originally promoted \\(X.\\) E.g. in an agent that selects actions on the basis of their consequences, if an event \\(X\\) leads to goal \\(G\\) but \\(X\\) is blocked, then a similar \\(X'\\) may also have the property of leading to \\(G.\\)

• The search is taking place over a [rich domain](https://arbital.greaterwrong.com/p/rich_domain?l=9j) where the space of relevant neighbors around X is too complicated for us to be certain that we have described all the relevant neighbors correctly. If we imagine an agent playing [the purely ideal game of logical Tic-Tac-Toe](https://arbital.greaterwrong.com/p/logical_game?l=9s), then if the agent’s utility function hates playing in the center of the board, we can be sure (because we can exhaustively consider the space) that there are no Tic-Tac-Toe squares that behave strategically almost like the center but don’t meet the exact definition we used of ‘center’. In the far more complicated real world, when you eliminate ‘administer heroin’ you are very likely to find some other chemical or trick that is strategically mostly equivalent to administering heroin. See “Almost all real-world domains are rich”.

• From our perspective on [value](https://arbital.greaterwrong.com/p/value_alignment_value?l=55), the AI does not have an absolute identification of value for the domain, due to some combination of “the domain is rich” and “[value is complex](https://arbital.greaterwrong.com/p/complexity_of_value?l=5l)”. Chess is complicated enough that human players can’t absolutely identify winning moves, but since a chess program can have an absolute identification of which endstates constitute winning, we don’t run into a problem of unending patches in identifying which states of the board are good play. (However, if we consider a very early chess program that (from our perspective) was trying to be a consequentialist but wasn’t very good at it, then we can imagine that, if the early chess program consistently threw its queen onto the right edge of the board for strange reasons, forbidding it to move the queen there might well lead it to throw the queen onto the left edge for the same strange reasons.)

# Arguments ^arguments

## ‘Nearest unblocked’ behavior is sometimes observed in humans ^nearest-unblocked-behavior-is

Although humans obeying the law make poor analogies for mathematical algorithms, in some cases human economic actors expect not to encounter legal or social penalties for obeying the letter rather than the spirit of the law. In those cases, after a previously high-yield strategy is outlawed or penalized, the result is very often a near-neighboring result that barely evades the letter of the law. This illustrates that the theoretical argument also applies in practice to at least some pseudo-economic agents (humans), as we would expect given the stated preconditions.

## [Complexity of value](https://arbital.greaterwrong.com/p/complexity_of_value?l=5l) means we should not expect to find a simple encoding to exclude detrimental strategies ^complexity-of-value-means

To a human, ‘poisonous’ is one word. In terms of molecular biology, the exact volume of the configuration space of molecules that is ‘nonpoisonous’ is very complicated. By having a single word/concept for poisonous-vs.-nonpoisonous, we’re _dimensionally reducing_ the space of edible substances—taking a very squiggly volume of molecule-space, and mapping it all onto a linear scale from ‘nonpoisonous’ to ‘poisonous’.

There’s a sense in which human cognition implicitly performs dimensional reduction on our solution space, especially by simplifying dimensions that are relevant to some component of our values. There may be some psychological sense in which we feel like “do X, only not weird low-value X” ought to be a simple instruction, and an agent that repeatedly produces the next unblocked weird low-value X is being perverse—that the agent, given a few examples of weird low-value Xs labeled as noninstances of the desired concept, ought to be able to just generalize to not produce weird low-value Xs.

In fact, if it were possible to encode all relevant dimensions of human value into the agent then we could just say _directly_ to “do X, but not low-value X”. By the definition of full coverage, the agent’s concept for ‘low-value’ includes everything that is actually of low [value](https://arbital.greaterwrong.com/p/value_alignment_value?l=55), so this one instruction would blanket all the undesirable strategies we want to avoid.

Conversely, the truth of the [complexity of value thesis](https://arbital.greaterwrong.com/p/complexity_of_value?l=5l) would imply that the simple word ‘low-value’ is dimensionally reducing a space of tremendous [algorithmic complexity](https://arbital.greaterwrong.com/p/Kolmogorov_complexity?l=5v). Thus the effort required to actually convey the relevant dos and don’ts of “X, only not weird low-value X” would be high, and a human-generated set of supervised examples labeled ‘not the kind of X we mean’ would be unlikely to cover and stabilize all the dimensions of the underlying space of possibilities. Since the weird low-value X cannot be eliminated in one instruction or several patches or a human-generated set of supervised examples, the [nearest unblocked strategy](https://arbital.greaterwrong.com/p/nearest_unblocked?l=42) problem will recur incrementally each time a patch is attempted and then the policy space is widened again.

# Consequences ^consequences

[Nearest unblocked strategy](https://arbital.greaterwrong.com/p/nearest_unblocked?l=42) being a [foreseeable difficulty](https://arbital.greaterwrong.com/p/foreseeable_difficulties?l=6r) is a major contributor to worrying that short-term incentives in AI development, to get today’s system working today, or to have today’s system not exhibiting any immediately visible problems today, will not lead to advanced agents which are [safe after undergoing significant gains in capability](https://arbital.greaterwrong.com/p/advanced_safety?l=2l).

More generally, [nearest unblocked strategy](https://arbital.greaterwrong.com/p/nearest_unblocked?l=42) is a [foreseeable](https://arbital.greaterwrong.com/p/foreseeable_difficulties?l=6r) reason why saying “Well just exclude X” or “Just write the code to not X” or “Add a penalty term for X” doesn’t solve most of the issues that crop up in AI alignment.

Even more generally, this suggests that we want AIs to operate inside a space of [conservative categories containing actively whitelisted strategies and goal instantiations](https://arbital.greaterwrong.com/p/conservative_concept?l=2qp), rather than having the AI operate inside a (constantly expanding) space of all conceivable policies minus a set of blacklisted categories.

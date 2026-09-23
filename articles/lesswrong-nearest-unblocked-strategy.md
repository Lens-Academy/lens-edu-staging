---
title: "Nearest unblocked strategy"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/nearest-unblocked-strategy"
published: 2016-05-02
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "An overview of the nearest unblocked strategy problem: when a penalty term excludes an undesirable AI policy, the AI's next-best policy is often a very similar one that narrowly evades the penalty, so patching around specific bad behaviors tends to recur rather than resolve."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Introduction ^introduction

'Nearest unblocked strategy' seems like it should be a [foreseeable](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) problem of trying to get rid of undesirable AI behaviors by adding specific penalty terms to them, or otherwise trying to exclude one class of observed or foreseen bad behaviors. Namely, if a decision criterion thinks $X$ is the best thing to do, and you add a penalty term $P$ that you think excludes everything inside $X$, the _next-best_ thing to do may be a very similar thing $X'$ which is the most similar thing to $X$ that doesn't trigger $P$.

## Example: Producing happiness. ^example-producing-happiness

Some very early proposals for AI alignment suggested that AIs be targeted on producing human happiness. Leaving aside various other objections, arguendo, imagine the following series of problems and attempted fixes:

-   By hypothesis, the AI is successfully infused with a goal of "human happiness" as a utility function over human brain states. (Arguendo, this predicate is narrowed sufficiently that the AI does not just want to construct [the tiniest, least resource-intensive brains experiencing the largest amount of happiness per erg of energy](https://www.lesswrong.com/w/edge-instantiation).)
-   Initially, the AI seems to be pursuing this goal in good ways; it organizes files, tells funny jokes, helps landladies take out the garbage, etcetera.
-   Encouraged, the programmers further improve the AI and add more computing power.
-   The AI gains a better understanding of the world, and the AI's [policy space expands](https://www.lesswrong.com/w/context-disaster) to include conceivable options like "administer heroin".
-   The AI starts planning how to administer heroin to people.
-   The programmers notice this before it happens. (Arguendo, due to successful transparency features, or an imperative to [check plans with the users](https://www.lesswrong.com/w/querying-the-agi-user), which operated as [intended](https://www.lesswrong.com/w/intended-goal) at the AI's current level of intelligence.)
-   The programmers edit the AI's utility function and add a penalty of -100 utilons for any event categorized as "the AI administers heroin to humans". (Arguendo, the AI's current level of intelligence does not suffice to [prevent the programmers from editing its utility function](https://www.lesswrong.com/w/prevent-the-programmers-from-editing-its-utility-function), despite the convergent instrumental incentive to avoid this; nor does it successfully [deceive](https://www.lesswrong.com/w/programmer-deception) the programmers.)
-   The AI gets slightly smarter. New conceivable options enter the AI's option space.
-   The AI starts wanting to administer cocaine to humans (instead of heroin).
-   The programmers read through the current schedule of prohibited drugs and add penalty terms for administering marijuana, cocaine, etcetera.
-   The AI becomes slightly smarter. New options enter its policy space.
-   The AI starts thinking about how to research a new happiness drug not on the list of drugs that its utility function designates as bad.
-   The programmers, after some work, manage to develop a category for 'The AI forcibly administering any kind of psychoactive drug to humans' which is broad enough that the AI stops suggesting research campaigns to develop things slightly outside the category.
-   The AI wants to build an external system to administer heroin, so that it won't be classified inside this set of bad events "the AI forcibly administering drugs".
-   The programmers generalize the penalty predicate to include "machine systems in general forcibly administering heroin" as a bad thing.
-   The AI recalculates what it wants, and begins to want to pay humans to administer heroin.
-   The programmers try to generalize the category of penalized events to include non-voluntarily administration of drugs in general that produce happiness, whether done by humans or AIs. The programmers patch this category so that the AI is not trying to shut down at least the nicer parts of psychiatric hospitals.
-   The AI begins planning an ad campaign to persuade people to use heroin voluntarily.
-   The programmers add a penalty of -100 utilons for "AIs _persuading_ humans to use drugs".
-   The AI goes back to helping landladies take out the garbage. All seems to be well.
-   The AI continues to increase in intelligence, becoming capable enough that the AI can no longer be edited against its own will.
-   The AI notices the option "Tweak human brains to express extremely high levels of endogenous opiates, then take care of their twitching bodies to so they can go on being happy".

The overall story is one where the AI's preferences on round $i$, denoted $U_i$, are observed to arrive at an attainable optimum $X_i$ which the humans see as undesirable. The humans devise a penalty term $P_i$ intended to exclude the undesirable parts of the policy space, and add this to $U_i$ creating a new utility function $U_{i+1}$, after which the AI's optimal policy settles into a new state $X_i^*$ that seems acceptable. However, after the next expansion of the policy space, $U_{i+1}$ settles into a new attainable optimum $X_{i+1}$ which is very similar to $X_i$ and makes the minimum adjustment necessary to evade the boundaries of the penalty term $P_i$, requiring a new penalty term $P_{i+1}$ to exclude this new misbehavior.

(The end of this story _might_ not kill you if the AI had enough successful, [advanced-safe](https://www.lesswrong.com/w/advanced-safety) [corrigibility features](https://www.lesswrong.com/w/corrigibility) that the AI would [indefinitely](https://www.lesswrong.com/w/omnipotence-test-for-ai-safety) go on [checking](https://www.lesswrong.com/w/querying-the-agi-user) [novel](https://www.lesswrong.com/w/conservative-concept-boundary) policies and [novel](https://www.lesswrong.com/w/conservative-concept-boundary) goal instantiations with the users, not strategically hiding its disalignment from the programmers, not deceiving the programmers, letting the programmers edit its utility function, not doing anything disastrous before the utility function had been edited, etcetera. But you wouldn't want to rely on this. You would not want in the first place to operate on the paradigm of 'maximize happiness, but not via any of these bad methods that we have already excluded'.)

## Preconditions ^preconditions

Recurrence of a nearby unblocked strategy is argued to be a [foreseeable difficulty](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) given the following preconditions:

• The AI is a [consequentialist](https://www.lesswrong.com/w/consequentialist-cognition), or is conducting some other search such that when the search is blocked at $X$, the search may happen upon a similar $X'$ that fits the same criterion that originally promoted $X$. E.g. in an agent that selects actions on the basis of their consequences, if an event $X$ leads to goal $G$ but $X$ is blocked, then a similar $X'$ may also have the property of leading to $G$.

• The search is taking place over a [rich domain](https://www.lesswrong.com/w/rich-domain) where the space of relevant neighbors around X is too complicated for us to be certain that we have described all the relevant neighbors correctly. If we imagine an agent playing [the purely ideal game of logical Tic-Tac-Toe](https://www.lesswrong.com/w/logical-game), then if the agent's utility function hates playing in the center of the board, we can be sure (because we can exhaustively consider the space) that there are no Tic-Tac-Toe squares that behave strategically almost like the center but don't meet the exact definition we used of 'center'. In the far more complicated real world, when you eliminate 'administer heroin' you are very likely to find some other chemical or trick that is strategically mostly equivalent to administering heroin. See " [Almost all real-world domains are rich](https://www.lesswrong.com/w/realisrich) ".

• From our perspective on [value](https://www.lesswrong.com/w/value), the AI does not have an [absolute identification of value](https://www.lesswrong.com/w/absolute-identification-of-value) for the domain, due to some combination of "the domain is rich" and " [value is complex](https://www.lesswrong.com/w/complexity-of-value) ". Chess is complicated enough that human players can't absolutely identify winning moves, but since a chess program can have an absolute identification of which endstates constitute winning, we don't run into a problem of unending patches in identifying which states of the board are good play. (However, if we consider a very early chess program that (from our perspective) was trying to be a consequentialist but wasn't very good at it, then we can imagine that, if the early chess program consistently threw its queen onto the right edge of the board for strange reasons, forbidding it to move the queen there might well lead it to throw the queen onto the left edge for the same strange reasons.)

## Arguments ^arguments

## 'Nearest unblocked' behavior is sometimes observed in humans ^nearest-unblocked-behavior-is

Although humans obeying the law make poor analogies for mathematical algorithms, in some cases human economic actors expect not to encounter legal or social penalties for obeying the letter rather than the spirit of the law. In those cases, after a previously high-yield strategy is outlawed or penalized, the result is very often a near-neighboring result that barely evades the letter of the law. This illustrates that the theoretical argument also applies in practice to at least some pseudo-economic agents (humans), as we would expect given the stated preconditions.

## [Complexity of value](https://www.lesswrong.com/w/complexity-of-value) means we should not expect to find a simple encoding to exclude detrimental strategies ^complexity-of-value-means

To a human, 'poisonous' is one word. In terms of molecular biology, the exact volume of the configuration space of molecules that is 'nonpoisonous' is very complicated. By having a single word/concept for poisonous-vs.-nonpoisonous, we're _dimensionally reducing_ the space of edible substances - taking a very squiggly volume of molecule-space, and mapping it all onto a linear scale from 'nonpoisonous' to 'poisonous'.

There's a sense in which human cognition implicitly performs dimensional reduction on our solution space, especially by simplifying dimensions that are relevant to some component of our values. There may be some psychological sense in which we feel like "do X, only not weird low-value X" ought to be a simple instruction, and an agent that repeatedly produces the next unblocked weird low-value X is being perverse - that the agent, given a few examples of weird low-value Xs labeled as noninstances of the desired concept, ought to be able to just generalize to not produce weird low-value Xs.

In fact, if it were possible to [encode all relevant dimensions of human value into the agent](https://www.lesswrong.com/w/full_coverage) then we could just say _directly_ to "do X, but not low-value X". By the definition of [full\_coverage](https://www.lesswrong.com/w/full_coverage), the agent's concept for 'low-value' includes everything that is actually of low [value](https://www.lesswrong.com/w/value), so this one instruction would blanket all the undesirable strategies we want to avoid.

Conversely, the truth of the [complexity of value thesis](https://www.lesswrong.com/w/complexity-of-value) would imply that the simple word 'low-value' is dimensionally reducing a space of tremendous [algorithmic complexity](https://www.lesswrong.com/w/algorithmic-complexity). Thus the effort required to actually convey the relevant dos and don'ts of "X, only not weird low-value X" would be high, and a human-generated set of supervised examples labeled 'not the kind of X we mean' would be unlikely to cover and stabilize all the dimensions of the underlying space of possibilities. Since the weird low-value X cannot be eliminated in one instruction or several patches or a human-generated set of supervised examples, the [nearest unblocked strategy](https://www.lesswrong.com/w/nearest-unblocked-strategy) problem will recur incrementally each time a patch is attempted and then the policy space is widened again.

## Consequences ^consequences

[Nearest unblocked strategy](https://www.lesswrong.com/w/nearest-unblocked-strategy) being a [foreseeable difficulty](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) is a major contributor to worrying that short-term incentives in AI development, to get today's system working today, or to have today's system not exhibiting any immediately visible problems today, will not lead to advanced agents which are [safe after undergoing significant gains in capability](https://www.lesswrong.com/w/advanced-safety).

More generally, [nearest unblocked strategy](https://www.lesswrong.com/w/nearest-unblocked-strategy) is a [foreseeable](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) reason why saying "Well just exclude X" or "Just write the code to not X" or "Add a penalty term for X" doesn't solve most of the issues that crop up in AI alignment.

Even more generally, this suggests that we want AIs to operate inside a space of [conservative categories containing actively whitelisted strategies and goal instantiations](https://www.lesswrong.com/w/conservative-concept-boundary), rather than having the AI operate inside a (constantly expanding) space of all conceivable policies minus a set of blacklisted categories.

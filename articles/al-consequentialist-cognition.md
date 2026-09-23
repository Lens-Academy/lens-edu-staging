---
title: "Consequentialist cognition"
author:
  - "Eliezer Yudkowsky et al."
source_url: "https://www.lesswrong.com/w/consequentialist-cognition"
published: 2016-06-11
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Consequentialist reasoning selects policies on the basis of their predicted consequences - it does action X because X is forecasted to lead to preferred outcome Y. This page examines cognitive consequentialism, pseudoconsequentialism, the ubiquity of consequentialism as an idiom of optimization, and its relevance to AI alignment and advanced safety."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

Consequentialist reasoning selects policies on the basis of their predicted consequences - it does action $X$ because $X$ is forecasted to lead to preferred outcome $Y$. Whenever we reason that an agent which prefers outcome $Y$ over $Y'$ will therefore do $X$ instead of $X'$, we're implicitly assuming that the agent has the cognitive ability to do consequentialism at least about $X$s and $Y$s. It does means-end reasoning; it selects means on the basis of their predicted ends plus a preference over ends.

E.g: When we [infer](https://www.lesswrong.com/w/convergent-instrumental-strategies) that a [paperclip maximizer](https://www.lesswrong.com/w/paperclip-maximizer) would try to [improve its own cognitive abilities](https://www.lesswrong.com/w/convergent-strategies-of-self-modification) given means to do so, the background assumptions include:

-   That the paperclip maximizer can _forecast_ the consequences of the policies "self-improve" and "don't try to self-improve";
-   That the forecasted consequences are respectively "more paperclips eventually" and "less paperclips eventually";
-   That the paperclip maximizer preference-orders outcomes on the basis of how many paperclips they contain;
-   That the paperclip maximizer outputs the immediate action it predicts will lead to more future paperclips.

(Technically, since the forecasts of our actions' consequences will usually be uncertain, a coherent agent needs a [utility function over outcomes](https://www.lesswrong.com/w/utility-function) and not just a preference ordering over outcomes.)

The related idea of "backward chaining" is one particular way of solving the cognitive problems of consequentialism: start from a desired outcome/event/future, and figure out what intermediate events are likely to have the consequence of bringing about that event/outcome, and repeat this question until it arrives back at a particular plan/policy/action.

Many narrow AI algorithms are consequentialists over narrow domains. A chess program that searches far ahead in the game tree is a consequentialist; it outputs chess moves based on the expected result of those chess moves and your replies to them, into the distant future of the board.

We can see one of the critical aspects of human intelligence as [cross-domain consequentialism](https://www.lesswrong.com/w/cross_consequentialism). Rather than only forecasting consequences within the boundaries of a narrow domain, we can trace chains of events that leap from one domain to another. Making a chess move wins a chess game that wins a chess tournament that wins prize money that can be used to rent a car that can drive to the supermarket to get milk. An Artificial General Intelligence that could learn many domains, and engage in consequentialist reasoning that leaped across those domains, would be a [sufficiently advanced agent](https://www.lesswrong.com/w/advanced-agent-properties) to be interesting from most perspectives on interestingness. It would start to be a consequentialist about the real world.

## Pseudoconsequentialism ^pseudoconsequentialism

Some systems are [pseudoconsequentialist](https://www.lesswrong.com/w/pseudoconsequentialist) - they in some ways _behave as if_ outputting actions on the basis of their leading to particular futures, without using an explicit cognitive model and explicit forecasts.

For example, natural selection has a lot of the power of a cross-domain consequentialist; it can design whole organisms around the consequence of reproduction (or rather, inclusive genetic fitness). It's a fair approximation to say that spiders weave webs _because_ the webs will catch prey that the spider can eat. Natural selection doesn't actually have a mind or an explicit model of the world; but millions of years of selecting DNA strands that did in fact previously construct an organism that reproduced, gives an effect _sort of_ like outputting an organism design on the basis of its future consequences. (Although if the environment changes, the difference suddenly becomes clear: natural selection doesn't immediately catch on when humans start using birth control. Our DNA goes on having been selected on the basis of the _old_ future of the ancestral environment, not the _new_ future of the actual world.)

Similarly, a reinforcement-learning system learning to play Pong might not actually have an explicit model of "What happens if I move the paddle here?" - it might just be re-executing policies that had the consequence of winning last time. But there's still a future-to-present connection, a pseudo-backwards-causation, based on the Pong environment remaining fairly constant over time, so that we can sort of regard the Pong player's moves as happening _because_ it will win the Pong game.

## Ubiquity of consequentialism ^ubiquity-of-consequentialism

Consequentialism is an extremely basic idiom of optimization:

-   You don't go to the airport because you really like airports; you go to the airport so that, in the future, you'll be in Oxford.
-   An air conditioner is an artifact selected from possibility space such that the future consequence of running the air conditioner will be cold air.
-   A butterfly, by virtue of its DNA having been repeatedly selected to _have previously_ brought about the past consequence of replication, will, under stable environmental conditions, bring about the future consequence of replication.
-   A rat that has previously learned a maze, is executing a policy that previously had the _consequence_ of reaching the reward pellets at the end: A series of turns or behavioral rule that was neurally reinforced in virtue of the future conditions to which it led the last time it was executed. This policy will, given a stable maze, have the same consequence next time.
-   Faced with a superior chessplayer, we enter a state of [Vingean uncertainty](https://www.lesswrong.com/w/vingean-uncertainty) in which we are more sure about the final consequence of the chessplayer's moves - that it wins the game - than we have any surety about the particular moves made. To put it another way, the main abstract fact we know about the chessplayer's next move is that the consequence of the move will be winning.
-   As a chessplayer becomes strongly superhuman, its play becomes [instrumentally efficient](https://www.lesswrong.com/w/epistemic-and-instrumental-efficiency) in the sense that _no_ abstract description of the moves takes precedence over the consequence of the move. A weak computer chessplayer might be described in terms like "It likes to move its pawn" or "it tries to grab control of the center", but as the chess play improves past the human level, we can no longer detect any divergence from "it makes the moves that will win the game later" that we can describe in terms like "it tries to control the center (whether or not that's really the winning move)". In other words, as a chessplayer becomes more powerful, we stop being able to describe its moves that will ever take priority over our beliefs that the moves have a certain consequence.

Anything that Aristotle would have considered as having a "final cause", or teleological explanation, without being entirely wrong about that, is something we can see through the lens of cognitive consequentialism or pseudoconsequentialism. A plan, a design, a reinforced behavior, or selected genes: Most of the complex order on Earth derives from one or more of these.

## Interaction with advanced safety ^interaction-with-advanced-safety

Consequentialism or pseudoconsequentialism, over various domains, is an [advanced agent property](https://www.lesswrong.com/w/advanced-agent-properties) that is a key requisite or key threshold in several issues of AI alignment and advanced safety:

-   You get [unforeseen maxima](https://www.lesswrong.com/w/unforeseen-maximum) because the AI connected up an action you didn't think of, with a future state it wanted.
-   It seems [foreseeable](https://www.lesswrong.com/w/methodology-of-foreseeable-difficulties) that some issues will be [patch-resistant](https://www.lesswrong.com/w/patch-resistance) because of the [nearest unblocked strategy](https://www.lesswrong.com/w/nearest-unblocked-strategy) effect: after one road to the future is blocked off, the next-best road to that future is often a very similar one that wasn't blocked.
-   Reasoning about [convergent instrumental strategies](https://www.lesswrong.com/w/convergent-instrumental-strategies) generally relies on at least pseudoconsequentialism - they're strategies that _lead up to_ or would be _expected to lead up to_ improved achievement of other future goals.
    -   This means that, by default, lots and lots of the worrisome or problematic convergent strategies like "resist being shut off" and "build subagents" and "deceive the programmers" arise from some degree of consequentialism, combined with some degree of [grasping the relevant domains](https://www.lesswrong.com/w/big-picture-strategic-awareness).

Above all: The human ability to think of a future and plan ways to get there, or think of a desired result and engineer technologies to achieve it, is _the_ source of humans having enough cognitive capability to be dangerous. Most of the magnitude of the impact of an AI, such that we'd want to align in the first place, would come in a certain sense from that AI being a sufficiently good consequentialist or solving the same cognitive problems that consequentialists solve.

## Subverting consequentialism? ^subverting-consequentialism

Since consequentialism seems tied up in so many issues, some of the proposals for making alignment easier have in some way tried to retreat from, limit, or subvert consequentialism. E.g:

-   [Oracles](https://www.lesswrong.com/w/oracle) are meant to "answer questions" rather than output actions that lead to particular goals.
-   [Imitation-based](https://www.lesswrong.com/w/imitation-based-agent) agents are meant to imitate the behavior of a reference human as perfectly as possible, rather than selecting actions on the basis of their consequences.

But since consequentialism is so close to the heart of why an AI would be [sufficiently useful](https://www.lesswrong.com/w/pivotal-act) in the first place, getting rid of it tends to not be that straightforward. E.g:

-   Many proposals for [what to actually do](https://www.lesswrong.com/w/pivotal-act) with Oracles involve asking them to plan things, with humans then executing the plans.
-   An AI that [imitates](https://www.lesswrong.com/w/imitation-based-agent) a human doing consequentialism must be [representing consequentialism inside itself somewhere](https://www.lesswrong.com/w/implicit-consequentialism).

Since 'consquentialism' or 'linking up actions to consequences' or 'figuring out how to get to a consequence' is so close to what would make advanced AIs useful in the first place, it shouldn't be surprising if some attempts to subvert consequentialism in the name of safety run squarely into [an unresolvable safety-usefulness tradeoff](https://www.lesswrong.com/w/safe-but-useless).

Another concern is that consequentialism may to some extent be a convergent or default outcome of optimizing anything hard enough. E.g., although natural selection is a pseudoconsequentialist process, it optimized for reproductive capacity so hard that [it eventually spit out some powerful organisms that were explicit cognitive consequentialists](https://www.lesswrong.com/w/optimization-daemons) (aka humans).

We might similarly worry that optimizing any internal aspect of a machine intelligence hard enough would start to embed consequentialism somewhere - policies/designs/answers selected from a sufficiently general space that "do consequentialist reasoning" is embedded in some of the most effective answers.

Or perhaps a machine intelligence might need to be consequentialist in some internal aspects in order to be [smart enough to do sufficiently useful things](https://www.lesswrong.com/w/pivotal-act) - maybe you just can't get a sufficiently advanced machine intelligence, sufficiently early, unless it is, e.g., choosing on a consequential basis what thoughts to think about, or engaging in consequentialist engineering of its internal elements.

In the same way that [expected utility](https://www.lesswrong.com/w/expected-utility) is the only coherent way of making certain choices, or in the same way that natural selection optimizing hard enough on reproduction started spitting out explicit cognitive consequentialists, we might worry that consequentialism is in some sense central enough that it will be hard to subvert - hard enough that we can't easily get rid of [instrumental convergence](https://www.lesswrong.com/w/instrumental-convergence) on [problematic strategies](https://www.lesswrong.com/w/convergent-instrumental-strategies) just by getting rid of the consequentialism while preserving the AI's usefulness.

This doesn't say that the research avenue of subverting consequentialism is automatically doomed to be fruitless. It does suggest that this is a deeper, more difficult, and stranger challenge than, "Oh, well then, just build an AI with all the consequentialist aspects taken out."

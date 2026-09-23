---
title: "Coherence arguments do not entail goal-directed behavior"
author:
  - "Rohin Shah"
source_url: "https://www.alignmentforum.org/posts/NxF5G6CJiof6cemTw/coherence-arguments-do-not-entail-goal-directed-behavior"
published: 2018-12-03
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Rohin Shah argues that many common arguments for AI risk (about the perils of powerful expected utility maximizers) are actually arguments about goal…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

One of the most pleasing things about probability and expected utility theory is that there are many _coherence arguments_ that suggest that these are the “correct” ways to reason. If you deviate from what the theory prescribes, then you must be executing a _dominated strategy_. There must be some other strategy that never does any worse than your strategy, but does strictly better than your strategy with certainty in at least one situation. There’s a good explanation of these arguments [here](https://www.alignmentforum.org/w/expected_utility_formalism?l=7hh).

We shouldn’t expect mere humans to be able to notice any failures of coherence in a superintelligent agent, since if we could notice these failures, so could the agent. So we should expect that [powerful agents appear coherent to us](https://www.alignmentforum.org/w/optimized_agent_appears_coherent). (Note that it is possible that the agent doesn’t fix the failures because it would not be worth it -- in this case, the argument says that we will not be able to notice any _exploitable_ failures.)

Taken together, these arguments suggest that we should model an agent much smarter than us as an expected utility (EU) maximizer. And many people agree that EU maximizers are dangerous. So does this mean we’re doomed? I don’t think so: it seems to me that the problems about EU maximizers that we’ve identified are actually about _[goal-directed behavior](https://www.alignmentforum.org/s/4dHMdK5TLN6xcqtyc/p/DfcywmqRSkBaCB6Ma)_ or _explicit reward maximizers._ The coherence theorems say nothing about whether an AI system must look like one of these categories. This suggests that we could try building an AI system that can be modeled as an EU maximizer, yet doesn’t fall into one of these two categories, and so doesn’t have all of the problems that we worry about.

Note that there are two different flavors of arguments that the AI systems we build will be goal-directed agents (which are dangerous if the goal is even slightly wrong):

-   Simply knowing that an agent is intelligent lets us infer that it is goal-directed. (EDIT: See [these](https://www.alignmentforum.org/posts/DkcdXsP56g9kXyBdq/coherence-arguments-imply-a-force-for-goal-directed-behavior?commentId=LvmHoLEhKLJzBrgrZ) [comments](https://www.alignmentforum.org/posts/vphFJzK3mWA4PJKAg/coherent-behaviour-in-the-real-world-is-an-incoherent#Gu4syyKBsRSQkktkJ) for more details on this argument.)
-   Humans are particularly likely to build goal-directed agents.

I will only be arguing against the first claim in this post, and will talk about the second claim in the next post.

## All behavior can be rationalized as EU maximization ^all-behavior-can-be

Suppose we have access to the entire policy of an agent, that is, given any universe-history, we know what action the agent will take. Can we tell whether the agent is an EU maximizer?

Actually, _no matter what the policy is_, we can view the agent as an EU maximizer. The construction is simple: the agent can be thought as optimizing the utility function U, where U(h, a) = 1 if the policy would take action a given history h, else 0. Here I’m assuming that U is defined over histories that are composed of states/observations and actions. The actual policy gets 1 utility at every timestep; any other policy gets less than this, so the given policy perfectly maximizes this utility function. This construction has been given before, eg. at the bottom of page 6 of [this paper](https://arxiv.org/abs/1811.07871). (I think I’ve seen it before too, but I can’t remember where.)

But wouldn’t this suggest that the VNM theorem has no content? Well, we assumed that we were looking at the _policy_ of the agent, which led to a universe-history _deterministically_. We didn’t have access to any probabilities. Given a particular action, we knew exactly what the next state would be. Most of the axioms of the VNM theorem make reference to lotteries and probabilities -- if the world is deterministic, then the axioms simply say that the agent must have transitive preferences over outcomes. Given that we can only observe the agent choose one history over another, we can trivially construct a transitive preference ordering by saying that the chosen history is higher in the preference ordering than the one that was not chosen. This is essentially the construction we gave above.

What then is the purpose of the VNM theorem? It tells you how to behave _if you have probabilistic beliefs about the world_, as well as a _complete and consistent preference ordering over outcomes_. This turns out to be not very interesting when “outcomes” refers to “universe-histories”. It can be more interesting when “outcomes” refers to world _states_ instead (that is, snapshots of what the world looks like at a particular time), but utility functions over states/snapshots can’t capture everything we’re interested in, and there’s no reason to take as an assumption that an AI system will have a utility function over states/snapshots.

## There are no coherence arguments that say you must have goal-directed behavior ^there-are-no-coherence

Not all behavior can be thought of as [goal-directed](https://www.alignmentforum.org/s/4dHMdK5TLN6xcqtyc/p/DfcywmqRSkBaCB6Ma) (primarily because I allowed the category to be defined by fuzzy intuitions rather than something more formal). Consider the following examples:

-   A robot that constantly twitches
-   The agent that always chooses the action that starts with the letter “A”
-   The agent that follows the policy \<policy> where for every history the corresponding action in \<policy> is generated randomly.

These are not goal-directed by my “definition”. However, they can all be modeled as expected utility maximizers, and there isn’t any particular way that you can exploit any of these agents. Indeed, it seems hard to model the twitching robot or the policy-following agent as having any preferences at all, so the notion of “exploiting” them doesn’t make much sense.

You could argue that neither of these agents are _intelligent_, and we’re only concerned with superintelligent AI systems. I don’t see why these agents could not in principle be intelligent: perhaps the agent knows how the world would evolve, and how to intervene on the world to achieve different outcomes, but it does not act on these beliefs. Perhaps if we peered into the inner workings of the agent, we could find some part of it that allows us to predict the future very accurately, but it turns out that these inner workings did not affect the chosen action at all. Such an agent is in principle possible, and it seems like it is intelligent.

(If not, it seems as though you are _defining_ intelligence to also be goal-driven, in which case I would frame my next post as arguing that we may not want to build superintelligent AI, because there are other things we could build that are as useful without the corresponding risks.)

You could argue that while this is possible in principle, no one would ever build such an agent. I wholeheartedly agree, but note that this is now an argument based on particular empirical facts about humans (or perhaps agent-building processes more generally). I’ll talk about those in the next post; here I am simply arguing that merely knowing that an agent is intelligent, with no additional empirical facts about the world, does not let you infer that it has goals.

As a corollary, since all behavior can be modeled as maximizing expected utility, but not all behavior is goal-directed, it is not possible to conclude that an agent is goal-driven if you only know that it can be modeled as maximizing some expected utility. However, if you know that an agent is maximizing the expectation of an _explicitly represented_ utility function, I would expect that to lead to goal-driven behavior most of the time, since the utility function must be relatively simple if it is explicitly represented, and _simple_ utility functions seem particularly likely to lead to goal-directed behavior.

## There are no coherence arguments that say you must have preferences ^there-are-no-coherence-2

This section is another way to view the argument in the previous section, with “goal-directed behavior” now being operationalized as “preferences”; it is not saying anything new.

Above, I said that the VNM theorem assumes both that you use probabilities and that you have a preference ordering over outcomes. There are lots of good reasons to assume that a good reasoner will use probability theory. However, there’s not much reason to assume that there is a preference ordering over outcomes. The twitching robot, “A”-following agent, and random policy agent from the last section all seem like they don’t have preferences (in the English sense, not the math sense).

Perhaps you could define a preference ordering by saying “if I gave the agent lots of time to think, how would it choose between these two histories?” However, you could apply this definition to _anything_, including eg. a thermostat, or a rock. You might argue that a thermostat or rock can’t “choose” between two histories; but then it’s unclear how to define how an AI “chooses” between two histories without that definition also applying to thermostats and rocks.

Of course, you could always define a preference ordering based on the AI’s observed behavior, but then you’re back in the setting of the first section, where _all_ observed behavior can be modeled as maximizing an expected utility function and so saying “the AI is an expected utility maximizer” is vacuous.

## Convergent instrumental subgoals are about goal-directed behavior ^convergent-instrumental-subgoals-are

One of the classic reasons to worry about expected utility maximizers is the presence of convergent instrumental subgoals, detailed in Omohundro’s paper [The Basic AI Drives](https://selfawaresystems.files.wordpress.com/2008/01/ai_drives_final.pdf). The paper itself is clearly talking about goal-directed AI systems:

_To say that a system of any design is an “artificial intelligence”, we mean that it has goals which it tries to accomplish by acting in the world._

It then argues (among other things) that such AI systems will want to “be rational” and so will distill their goals into utility functions, which they then maximize. And once they have utility functions, they will protect them from modification.

Note that this starts from the assumption of goal-directed behavior and _derives_ that the AI will be an EU maximizer along with the other convergent instrumental subgoals. The coherence arguments all imply that AIs will be EU maximizers for some (possibly degenerate) utility function; they don’t prove that the AI must be goal-directed.

## Goodhart’s Law is about goal-directed behavior ^goodharts-law-is-about

A common argument for worrying about AI risk is that we know that a superintelligent AI system will look to us like an EU maximizer, and if it maximizes a utility function that is even slightly wrong we could get catastrophic outcomes.

By now you probably know my first response: that _any_ behavior can be modeled as an EU maximizer, and so this argument proves too much, suggesting that any behavior causes catastrophic outcomes. But let’s set that aside for now.

The second part of the claim comes from arguments like [Value is Fragile](https://www.alignmentforum.org/posts/GNnHHmm8EzePmKzPk/value-is-fragile) and [Goodhart’s Law](https://en.wikipedia.org/wiki/Goodhart%27s_law). However, if we consider utility functions that assign value 1 to some histories and 0 to others, then if you accidentally assign a history where I needlessly stub my toe a 1 instead of a 0, that’s a slightly wrong utility function, but it isn’t going to lead to catastrophic outcomes.

The worry about utility functions that are _slightly wrong_ holds water when the utility functions are wrong about some _high-level_ concept, like whether humans care about their experiences reflecting reality. This is a very rarefied, particular distribution of utility functions, that are all going to lead to goal-directed or agentic behavior. As a result, I think that the argument is better stated as “if you have a slightly incorrect goal, you can get catastrophic outcomes”. And there aren’t any coherence arguments that say that agents must have goals.

## Wireheading is about explicit reward maximization ^wireheading-is-about-explicit

There are [a](https://intelligence.org/files/LearningValue.pdf) [few](http://people.idsia.ch/~ring/AGI-2011/Paper-B.pdf) [papers](https://arxiv.org/abs/1605.03142) that talk about the problems that arise with a very powerful system with a reward function or utility function, most notably wireheading. The argument that AIXI will seize control of its reward channel falls into this category. In these cases, typically the AI system is considering making a change to the system by which it evaluates goodness of actions, and the goodness of the change is evaluated by the system _after the change_. Daniel Dewey argues in [Learning What to Value](https://intelligence.org/files/LearningValue.pdf) that if the change is evaluated by the system _before_ the change, then these problems go away.

I think of these as problems with _reward_ maximization, because typically when you phrase the problem as maximizing reward, you are maximizing the sum of rewards obtained in all timesteps, no matter how those rewards are obtained (i.e. even if you self-modify to make the reward maximal). It doesn’t seem like AI systems have to be built this way (though admittedly I do not know how to build AI systems that reliably avoid these problems).

## Summary ^summary

In this post I’ve argued that many of the problems we typically associate with expected utility maximizers are actually problems with goal-directed agents or with explicit reward maximization. Coherence arguments only entail that a superintelligent AI system will look like an expected utility maximizer, but this is actually a vacuous constraint, and there are many potential utility functions for which the resulting AI system is neither goal-directed nor explicit-reward-maximizing. This suggests that we could try to build AI systems of this type, in order to sidestep the problems that we have identified so far.

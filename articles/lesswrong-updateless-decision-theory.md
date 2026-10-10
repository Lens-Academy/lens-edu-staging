---
title: "Updateless Decision Theory"
author:
  - "Lesswrong"
source_url: "https://www.lesswrong.com/w/updateless-decision-theory"
published: 2026-10-10
created: 2026-10-10
accessed: 2026-10-10
llm-review:
  date: 2026-10-10
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-10
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Motivation ^motivation

**Updateless Decision Theory** (UDT) is a decision theory meant to deal with a fundamental problem in the existing decision theories: [dynamic inconsistency](https://en.m.wikipedia.org/wiki/Dynamic_inconsistency), IE, having conflicting desires over time. In behavioral economics, humans are often modeled as [hyperbolic discounters](https://en.m.wikipedia.org/wiki/Hyperbolic_discounting), meaning that rewards further away in time are seen as _proportionately_ less important (so getting \$100 one week from now is as good as \$200 two weeks from now). This is dynamically inconsistent because the relative value of rewards changes as they get closer or further away in time. (Getting \$100 one year from now sounds much less desirable than getting \$200 one year plus one week from now.) This model explains some human behaviors, such as snoozing alarms repeatedly.[^note-1]

The dynamic inconsistency inherent in hyperbolic discounting can be fixed by [exponential discounting](https://en.m.wikipedia.org/wiki/Exponential_discounting), amongst other possibilities. However, dynamic inconsistencies can still occur for other reasons. The two most common decision theories today, [Causal Decision Theory](https://www.lesswrong.com/tag/causal-decision-theory) (CDT) and [Evidential Decision Theory](https://www.lesswrong.com/tag/evidential-decision-theory) (EDT), are both dynamically inconsistent about [Counterfactual Mugging](https://www.lesswrong.com/tag/counterfactual-mugging): they refuse Omega when faced with the problem, but if asked beforehand, would see the value of agreeing.[^note-2][^note-3]

Getting this issue right is critical in building a safe artificial general intelligence, as such an AI must analyze its own behavior and that of a next generation that it may build. Dynamically inconsistent AI systems have an incentive to engage in self-modification, but such self-modification is inherently risky. 

Updateless Decision Theory was invented by [Wei Dai](https://www.lesswrong.com/users/wei_dai) and first described in [Towards a New Decision Theory](https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory).

## See also ^see-also

-   [Timeless decision theory](https://www.lesswrong.com/tag/timeless-decision-theory)
-   [Ambient decision theory](https://www.lesswrong.com/tag/ambient-decision-theory)
-   [Counterfactual mugging](https://www.lesswrong.com/tag/counterfactual-mugging)
-   [Decision theory](https://www.lesswrong.com/tag/decision-theory)
-   [Functional Decision Theory](https://www.lesswrong.com/posts/AGAGgoWymRhJ5Rqyv/functional-decision-theory-a-new-theory-of-instrumental)
-   [Embedded Agency](https://www.lesswrong.com/tag/embedded-agency)

## Content ^content

UDT specifies that the optimal agent is the one with the best policy—the best mapping from observations to actions—as estimated by its prior beliefs. ("Best" here, as in other decision theories, means one that maximizes expected utility.)

This definition may seem trivial, but in contrast, CDT and EDT both choose the "best" action _in the current moment, IE, according to the posterior beliefs_. 

For example, standard game theory (which uses CDT) says that following through on costly threats is irrational. For example, suppose Alice says that she will hunt down Bob and beat him up if Bob steals from her. Bob proceeds to steal a small amount from Alice. CDT says that Alice should let it go, rather than pay the cost of following through on her threat, because _now that Bob has stolen,_ Alice is only losing utility by following through.

Yet, standard game theory _affirms that Bob would not steal if Alice were the sort of person who followed through on threats_. In the standard game-theoretic model, _it is a Nash equilibrium_ for Alice to be the sort of person who follows through; in this Nash equilibrium, Bob doesn't steal.

This Nash equilibrium is considered irrational, however, because CDT says it is irrational for Alice to follow through. Therefore, standard game-theory rules out such Nash equilibria. This assumption is called the [subgame-perfect](https://en.m.wikipedia.org/wiki/Subgame_perfect_equilibrium) condition.

Part of the idea of UDT, then, is to get rid of the subgame-perfect condition. According to UDT, it is rational for Alice to be the sort of person who follows through on threats, if Bob has a low probability of stealing from such people -- the cost is rarely paid, so it is worth the cost overall.

However, UDT isn't only about rejection of the subgame-perfect condition. UDT also rejects CDT's way of thinking about the consequences of actions. In [Judea Pearl's definition of causality](http://lesswrong.com/lw/emc/causality_a_chapter_by_chapter_review/),[^note-4] CDT ignores any causal links inbound to the decider, treating this agent as an uncaused cause. UDT rejects this idea, instead thinking about consequences in the way EDT does.

Evidential Decision Theory is the other leading decision theory today. It says that the agent should make the choice for which the expected utility, as calculated with Bayes' Rule, is the highest. This allows for cooperation in the [Prisoner's Dilemma](https://www.lesswrong.com/tag/prisoner-s-dilemma) in some cases, if the two players think their decisions are sufficiently correlated. This is not a Nash Equilibrium at all, subgame-perfect or otherwise, and standard game theory considers cooperation in this situation to be irrational. However, many people in the LessWrong community and related intellectual circles think that cooperation _is_ rational in many cases. This may have been a factor in Wei Dai's decision to use a more EDT-like formulation for UDT, rather than a CDT-like formulation.

UDT and [Timeless Decision Theory](https://www.lesswrong.com/tag/timeless-decision-theory) (TDT) have very similar motivations; indeed, Wei Dai formulated UDT as something like a guess about TDT due to Eliezer being slow to publish details about TDT:

> It commonly acknowledged here that current decision theories have deficiencies that show up in the form of various paradoxes. Since there seems to be little hope that Eliezer will publish his [Timeless Decision Theory](https://www.lesswrong.com/lw/135/timeless_decision_theory_problems_i_cant_solve/) any time soon, I decided to try to synthesize some of the ideas discussed in this forum, along with a few of my own, into a coherent alternative that is hopefully not so paradox-prone.
> 
> _\-- Wei Dai,_ [_Towards a New Decision Theory_](https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory)

However, TDT took a more CDT-inspired approach, while UDT choose the EDT-like direction. Nate Soares [states](https://www.lesswrong.com/posts/2THFt7BChfCgwYDeA/let-s-discuss-functional-decision-theory?commentId=LzPH8utKGSf97NihW): "Wei Dai doesn't endorse FDT's focus on causal-graph-style counterpossible reasoning; IIRC he's holding out for an approach to counterpossible reasoning that falls out of evidential-style conditioning on a logically uncertain distribution".

### UDT 1.0 & 1.1 ^udt-1-0-1

Let $O$  be a random variable representing observations, and $o$ be some particular value (some specific observations). $P()$ is the prior probability distribution. $U$ is a random variable representing the utility. $\mathbb{E}$ is the expectation operator. There is a set of possible actions, $A$. EDT recommends the following action:[^note-5]

$$
\text{choice}(o) := \operatorname{argmax}_{a \in A} \mathbb{E}_P(U | \text{choice}(o)=a, O=o)
$$

In other words, it maximizes expectations conditioning on the action and on observations. 

UDT 1.0 simply drops the observations:

$$
\text{choice}(o) := \operatorname{argmax}_{a \in A} \mathbb{E}_P(U | \text{choice}(o)=a)
$$

This captures the idea that you're making the decision you would have liked to commit to beforehand. A UDT agent is supposed to behave _as if_ it had made all commitments which it would have liked to make, but without needing to explicitly consider everything beforehand.

However, Wei Dai noticed a problem with UDT 1.0, as detailed in [Explicit Optimization of Global Strategy (Fixing a Bug in UDT1)](https://www.lesswrong.com/posts/g8xh9R7RaNitKtkaa/explicit-optimization-of-global-strategy-fixing-a-bug-in). In some cases, UDT 1.0 fails to coordinate with itself. The fix is as follows, with $\pi \in \Pi$ being policies, IE, functions from observations to actions:

$$
\text{choice}(o) := \pi^*(o)
$$

$$
\pi^* = \operatorname{argmax}_{\pi \in \Pi} \mathbb{E}_P (U| \pi^* = \pi)
$$

In words: we simply choose an optimal policy and act accordingly, rather than choosing each action to individually maximize prior expected utility. This eliminates self-coordination problems which can arise. For example, suppose that we flip a coin and show it to a UDT 1.0 agent. We then ask the agent to choose between \$10 and \$20\. The catch is that we also simulate what it would have said if it saw the coin land the other way, and give it \$0 if it disagrees with its counterfactual twin. UDT 1.0 can choose the \$10 in this situation, depending on its prior. UDT 1.1 will always choose \$20\. (Assuming the agent likes money, of course.)

### Logical Uncertainty ^logical-uncertainty

A robust theory of [logical uncertainty](https://www.lesswrong.com/tag/logical-uncertainty) is essential to a full formalization of UDT.  A UDT agent must calculate probabilities and expected values on the outcome of its possible actions in all possible worlds—sequences of observations and its own actions. However, it does not know its own actions in all possible worlds. (The whole point is to derive its actions.) On the other hand, it does have some knowledge about its actions, just as you know that you are unlikely to walk straight into a wall the next chance you get. So, the UDT agent models itself as an algorithm, and its probability distribution about what it itself will do is an important input into its maximization calculation.

Logical uncertainty is an area which has not yet been properly formalized, and much UDT research is focused on this area.

## Blog posts ^blog-posts

-   [Indexical uncertainty and the Axiom of Independence](http://lesswrong.com/lw/102/indexical_uncertainty_and_the_axiom_of/) by Wei Dai
-   [Towards a New Decision Theory](http://lesswrong.com/lw/15m/towards_a_new_decision_theory/) by [Wei Dai](http://weidai.com/)
-   [Anthropic Reasoning in UDT](http://lesswrong.com/lw/175/torture_vs_dust_vs_the_presumptuous_philosopher/) by Wei Dai
-   [The Absent-Minded Driver](http://lesswrong.com/lw/182/the_absentminded_driver/) by Wei Dai
-   [Why (and why not) Bayesian Updating?](http://lesswrong.com/lw/1fu/why_and_why_not_bayesian_updating/) by Wei Dai
-   [What Are Probabilities, Anyway?](http://lesswrong.com/lw/1iy/what_are_probabilities_anyway/) by Wei Dai
-   [Explicit Optimization of Global Strategy (Fixing a Bug in UDT1)](http://lesswrong.com/lw/1s5/explicit_optimization_of_global_strategy_fixing_a/) by Wei Dai
-   [List of Problems That Motivated UDT](http://lesswrong.com/lw/cs9/list_of_problems_that_motivated_udt/) by Wei Dai
-   [Another attempt to explain UDT](http://lesswrong.com/lw/334/another_attempt_to_explain_udt/) by cousin\_it
-   [What is Wei Dai's Updateless Decision Theory?](http://lesswrong.com/lw/294/what_is_wei_dais_updateless_decision_theory/) by AlephNeil
-   [Comparison of decision theories (with a focus on logical-counterfactual decision theories)](https://www.lesswrong.com/posts/QPhY8Nb7gtT5wvoPH/comparison-of-decision-theories-with-a-focus-on-logical), by riceissa. (Gives a good description of UDT 1.0 vs 1.1)
-   [Conceptual Problems with UDT and Policy Selection](https://www.lesswrong.com/posts/9sYzoRnmqmxZm4Whf/conceptual-problems-with-udt-and-policy-selection) by abramdemski
-   [All posts tagged "UDT"](http://lesswrong.com/tag/udt/)

## Relevant Comments ^relevant-comments

In addition to whole posts on UDT, there are also a number of comments which contain important information, often on less relevant posts.

-   [A comment about UDT2](http://lesswrong.com/lw/jhj/functional_side_effects/adhy)

## External links ^external-links

-   [Formal description of UDT](https://drive.google.com/file/d/0BzUiCL-Kpxc1NGxab3ZfZGZkVUE/view?usp=sharing&resourcekey=0-EuvTP8RRdpKivUtHwfqgSQ) by Tyrrell McAllister
-   [UDT with known search order](http://intelligence.org/2014/10/30/new-report-udt-known-search-order/) by Tsvi Benson-Tilsen
-   [Problem Class Dominance in Predictive Dilemmas](http://intelligence.org/files/ProblemClassDominance.pdf), section 3.4. (The best summary to date.)
-   [An introduction to decision theory](https://formalisedthinking.wordpress.com/2010/08/18/an-introduction-to-decision-theory/) (series of posts)
-   [Arbital page on updateless decision theories](https://arbital.com/p/updateless_dt/) by Eliezer Yudkowsky
-   [Thoughts on Updatelessness](https://casparoesterheld.com/2016/11/21/thoughts-on-updatelessness/) by Caspar Oesterheld

[^note-1]: Getting up early to get a good start on the day seems appealing the previous evening, but when the alarm rings, the relative reward of sleeping in another few minutes is larger.
[^note-2]: We can more rigorously define dynamic inconsistency as follows: _**If the agent is given the opportunity to commit to a decision early, there are cases where it strictly prefers a different choice than the one it would make in-the-moment.**_ In Counterfactual Mugging, we understand Omega as "making a copy" of the agent at some point in time (EG, taking a detailed scan for use in a simulation). If a CDT agent is given the opportunity to commit to a decision in Counterfactual Mugging _before this point in time_, then it will think of the simulation as being downstream of its decision, so it will make the same decision as UDT. If a CDT agent is asked _after the copy is made, but before the coin-flip result is revealed,_ then the CDT agent will decide to refuse, just like it does after the coin-flip is revealed. The analysis for EDT agents is a little bit simpler. If you ask the EDT agent to commit to a decision before the coin-flip is revealed, then it will agree to give up the money just like UDT would, since it sees the cost as smaller than the potential payout, and always thinks of its decision as strongly correlated with Omega's simulation.[^note-6] If the EDT agent is asked _after_ the coin-flip, then EDT refuses.
[^note-3]: This supposes that the agent isn't doing any anthropic reasoning; specifically, they don't put any probability on the possibility that _they themselves are the agent inside Omega's hypothetical simulation_. If the agent reasons anthropically, [CDT and EDT can reach the same conclusion as UDT](https://www.lesswrong.com/posts/5bd75cc58225bf06703751b2/in-memoryless-cartesian-environments-every-udt-policy-is-a-cdt-sia-policy).
[^note-4]: There are several different theories of causality, meaning there is a different version of CDT for each alternative.
[^note-5]: In contrast, CDT chooses the following:    $\text{choice}(o) := \operatorname{argmax}_{a \in A} \mathbb{E}_P \Big (U \; | \; \text{do} \big( \text{choice}(o)=a \big), O=o \Big)$ The only difference between this and CDT is that the "do" operator has been wrapped around the choice of action. This notation says that the action is an "intervention" rather than a normal Bayesian conditioning. In the context of a causal Bayesian network, we cut the parents of variables with a "do" before we make inferences (again assuming Judea Pearl's theory of causality, rather than alternatives).
[^note-6]: Note that this is a questionable assumption: EDT need not think its decision is correlated with the simulation. This is merely a typical part of the problem set-up.

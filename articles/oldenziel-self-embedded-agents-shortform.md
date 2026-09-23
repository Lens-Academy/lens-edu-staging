---
title: "Self-Embedded Agent's Shortform"
author:
  - "Alexander Gietelink Oldenziel"
source_url: "https://www.lesswrong.com/posts/km6wasEXXmx85v5yG/self-embedded-agent-s-shortform"
published: 2022-09-16
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Comment by Alexander Gietelink Oldenziel - Imprecise Probability I: the Bid-Ask Spread measures Adversariality Definition. A credal set or imprecise probability distribution I is a convex closed set of probability distributions pi.  For a given event A we obtain an upper- and a lower probability/price  ¯¯¯¯P(A)=maxipi(A),P––(A)=minipi(A) In other words, we have a buy and a sell price for A. Remark. Vanessa"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

# [Self-Embedded Agent's Shortform](https://www.lesswrong.com/posts/km6wasEXXmx85v5yG/self-embedded-agent-s-shortform) ^self-embedded-agents-shortform

by [Alexander Gietelink Oldenziel](https://www.lesswrong.com/users/alexander-gietelink-oldenziel?from=post_header)

2nd Sep 2021

## Imprecise Probability I: the Bid-Ask Spread measures Adversariality ^imprecise-probability-i-the

**Definition.** A **credal set** or **imprecise probability distribution** I is a convex closed set of probability distributions $p_i$ . 

For a given event $A$ we obtain an upper- and a lower probability/price 

$\overline{P}(A)=max_i \, \, p_i(A), \quad \underline{P}(A)= min_i \, \, p_i(A)$

In other words, we have a buy and a sell price for $A$.

**Remark**. Vanessa's [infraDistributions](https://www.lesswrong.com/posts/zB4f7QqKhBHa5b37a/introduction-to-the-infra-bayesianism-sequence) generalize imprecise probability further in a way that I do not fully understand yet.

Let me talk a little about why thinking in terms of imprecise probability may be helpful. Imprecise probability has a bid-ask spread for events; that is the difference between the upper and lower probability. In many ways this measures the difference between 'aleatoric' and 'epistemic' uncertainty. This is particularly relevant in adversarial situations (which gets into the reasons Vanessa is interested in these things). Let me give a couple e

**Example. (Earning calls)** When the earning call comes in for a company the bid-ask spread of the stock will increase. Intuitively, the market expects new private information to come into the market and by increasing the bid-ask spread it insures itself against being mugged.

**Example. (Resolution Uncertainty)** If you know A will resolve you should buy shares on A, if you know not A will happen you should buy shares on not A. If you think A will not resolve you should sell (!) shares on A. The Bid-ask Spread measures bet resolution uncertainty 

**Example. (Selective reporting)** Suppose an adversary has an interest in showing you $A$ if $A$ happens and for it _not to resolve_ if  $NOT \, A$, i.e. this is a form [selective reporting](https://www.lesswrong.com/posts/DoPo4PDjgSySquHX8/heads-i-win-tails-never-heard-of-her-or-selective-reporting) that is so essential in politics. In this case you should _buy_ $A$ and _sell_ $NOT \, A$. 

**Example (Forecasting)** "for some large class of events, if you ask people how many years until a 10%, 50%, 90% chance of event $X$ occurring, you will get an earlier distribution of times than if you ask the probability that $X$ will happen in 10, 20, 50 years. (I’ve only tried this with AI related things, but my guess is that it at least generalizes to other low-probability-seeming things. Also, if you just ask about 10% on its own, it is consistently different from 10% alongside 50% and 90%." 

This is well-known phenomena is typically considered a failure of human rationality but it can be explained quite neatly using imprecise probability & Knightian uncertainty. \[I hasten to caveat that this does not prove that this is the real reason for the phenomena, just a possible explanation!\] 

An imprecise distribution I is the convex (closed) hull of a collection of probability distributions $p_i, i \in I$: In other words it combines 'Knightian' uncertainty with probabilistic uncertainty.

If you ask people for 10%, 50%, 90% chance of AI happening you are implicitly asking for the worst case: i.e. there is at least one probability distribution $p_k$, such that $p_k(AGI)$ = 10%,50%,90% On the other hand when you ask for a certain event to happen for certain in 10,20,50 years you are asking for the dual 'best case' scenario, i.e. for ALL probability distributions $p_i$ what probability $p_i$(AGI in 10y), $p_i($AGI in 20y$),\, p_i$(AGI in 50y$)$ and taking the minimum.

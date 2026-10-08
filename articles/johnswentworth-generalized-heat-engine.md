---
title: "Generalized Heat Engine"
author:
  - "johnswentworth"
source_url: "https://www.lesswrong.com/posts/uKWXktrR7KpbgZAs4/generalized-heat-engine"
published: 2020-11-05
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "I’d like to be able to apply more of the tools of statistical mechanics and thermodynamics outside the context of physics. For some pieces, that’s pr…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

I’d like to be able to apply more of the tools of statistical mechanics and thermodynamics outside the context of physics. For some pieces, that’s pretty straightforward - a large chunk of statistical mechanics is just information theory, and that’s already a flourishing standalone field which formulates things in general ways. But for other pieces, it’s less obvious. What’s the analogue of a refrigerator or a carnot cycle in more general problems? How do “work” and “heat” generalize to problems outside physics? The [principle of maximum entropy](https://en.wikipedia.org/wiki/Maximum_entropy_thermodynamics) tells us how to generalize temperature, and offers one generalization of work and heat, but it’s not immediately obvious why we can’t extract “work” from “heat” without subsystems at different temperatures, or how to turn that into a useful idea in non-physics applications.

This post documents my own exploration of these questions in the context of a relatively simple problem, with minimal reference to physics (other than by analogy). Specifically: we’ll talk about how to construct the analogue of a heat engine using biased coins.

## Intuition ^intuition

The main idea I want to generalize here is that we can “move uncertainty around” without reducing uncertainty. This is exactly what e.g. a refrigerator or heat engine does.

Consider the viewpoint of a refrigerator-designer. All the microscopic dynamics of the (fridge + environment) system must be reversible, so the number of possible microscopic states will never decrease on its own as time passes. The only way to reduce uncertainty about the microscopic state is to observe it. But the fridge designer is _designing_ the system, deciding in advance how it will behave. The designer has no direct access to the environment in which the fridge will run, no way to measure the exact positions the atoms will be in when the fridge first turns on. The designer, in short, cannot directly observe the system. So, from the designer’s perspective, there’s uncertainty which cannot be reduced.

(In statistical mechanics, there are several entirely different justifications for why observations can’t reduce microscopic uncertainty/entropy - for instance, in one approach, macroscopic variables are chosen in such a way that we can deterministically predict future macroscopic observations. Another comes from Maxwell’s demon-style arguments, where the demon’s memory has to be included as part of the system. I’ll use the designer viewpoint, since it’s conceptually simple and easy to apply in other areas - in particular, we can easily apply it to the design of AIs embedded in their environment.)

While we can’t reduce our total uncertainty, we _can_ move it around. We design the machine to apply transformations to the system which leave us more certain about some subsystems (e.g. the inside of the refrigerator), but less certain about other subsystems (e.g. heat baths used to power the system).

## Setup ^setup

We’ll imagine two large sets of IID biased coins. One is the “cold pool”, in which each coin comes up 1 (i.e. heads) with probability 0.1 and 0 with probability 0.9. The other is the “hot pool”, in which each coin comes up 1 with probability 0.2. We’ll call the coins in the cold pool $X^C_1 … X^C_n$ , and the coins in the hot pool $X^H_1 … X^H_n$.

We’re going to apply transformations to these coins. Each transformation replaces some set of coins with new values which are a function of their old values. For instance, one transformation might be

$(X^C_1, X^H_3, X^H_7) \leftarrow (X^C_1, X^H_3 X^C_1 + X^H_7 \overline{X^C_1}, X^H_7 X^C_1 + X^H_3 \overline{X^C_1})$

(Here the bar denotes logical not - i.e. $\overline{X}$ means "not X".) This transformation swaps $X^H_3$ with $X^H_7$ if $X^C_1$ is 0, and leaves everything unchanged if $X^C_1$ is 1.

We’ll mostly be able to use any transformations we want, but with two big constraints. First: **all transformations must be reversible**. If we know the final state of the coins and which transformations were applied, then we must be able to reconstruct the initial state of the coins. (This is the analogue of microscopic reversibility.) Our example transformation above is reversible - since it doesn’t change $X^C_1$, we can always tell whether $X^H_3$ and $X^H_7$ were swapped, and we can swap them back if they were (indeed, we can do so by simply reapplying the same transformation).

Second constraint: **all transformations must conserve the number of heads**; heads can be neither created nor destroyed on net. Here the number of heads is our analogue of energy, and heads-conservation is our analogue of microscopic energy conservation. (In physics, we’d probably describe this as some kind of spin system in an external magnetic field.) Our example transformation above conserves the number of heads: it either swaps two coins or leaves everything alone, so the total number of heads stays the same.

One more key rule: while we will be able to choose what transformation to apply, **we do not get to look at the coins before choosing our transformation**. Physical analogy: if we’re building a heat engine or refrigerator or the like, we can’t just freely observe the microscopic state of the system. More generally, if we’re designing some machine (like a heat engine), we have to decide up-front how the machine will behave, before we have perfect information about the environment in which it will run. The machine itself can “observe” variables while running, but the machine is part of the system, so those “observations” need to be reversible and energy-conserving just like any other transformations.

Writing it all out mathematically: we choose some transformation $T$ for which

-   $(X^H, X^C)’ = T(X^H, X^C)$
-   $(\sum_k X^H_k + \sum_k X^C_k)' = \sum_k X^H_k + \sum_k X^C_k$
-   $T$ is invertible

We’ll want to choose this $T$ to do something interesting, like reduce the uncertainty of particular coins.

## Extracting “Work” ^extracting-work

General problem: choose a transformation to produce some coins which are 1 with near-zero uncertainty (i.e. asymptotically zero uncertainty). We’ll call these deterministic coins “work”, and use $w$ to denote the number of work-coins produced.

We’ll look at two subproblems to this problem. First, we’ll try to do it using just _one_ of the two pools of coins (the hot one, though it doesn’t matter). This is the equivalent of “turning heat directly into work”, i.e. a [type-2 perpetual motion machine](https://en.wikipedia.org/wiki/Perpetual_motion); we’d expect it to be impossible. Second, we’ll tackle the problem using both pools, and figure out how much work we can extract. This is the equivalent of a heat engine.

## Extracting Work From One Heat Bath ^extracting-work-from-one

The first key thing to notice is that this is inherently an information compression problem. I have $n$ random coins with heads-probability 0.2. I want to make w of those coins near-certainly 1, while still making the transformation reversible - therefore the remaining $n-w$ transformed coins must contain _all_ of the information from the original $n$ coins. In other words, I need to compress the info from the original n coins into $n-m$ bits with near-certainty.

If we whip out our information theory, that compression is fairly straightforward. Our biased coins have entropy of $-(0.2 \log(0.2) + 0.8 \log(0.8)) \approx 0.72$ bits per coin. So, with a reversible transformation we can compress all of the info into $0.73n$ of the coins, and the remaining $0.27n$ coins can all be nearly-deterministic.

(We’re fudging a bit here - we may need to add one or two extra coins from outside to make the compression algorithm handle unlikely cases without loss - but for current purposes that’s not a big deal. I’ll be fudging this sort of thing throughout the post.)

However, we _also_ need to conserve the number of heads. That’s a problem: fully compressed bits are 50/50 in general, so our $0.73n$ compressed bits include roughly $0.36n$ heads. We started with only $0.2n$ heads, so we have no way to balance the books - even if all of our $0.27n$ deterministic bits are tails, we still end up with too many heads and too few tails.

This generalizes: we won’t be able to compress our information without producing more tails. Hand-wavy proof: the initial distribution of coins is maxentropic subject to a constraint on the total number of heads. So, we can’t compress it without violating that constraint.

Let’s spell this out a bit more carefully.

A maxentropic variable contains as much information as possible - there is no other distribution over the same outcomes with higher entropy. In general, mutual information $I(X,Y)$ is at most the entropy of one variable $H(X)$ - i.e. the information in $X$ about $Y$ is at most all of the information in $X$, so the higher the entropy $H(X)$ the more information $X$ can potentially contain about any other variable $Y$.

In our case, we have an initial state $X$ and a final state $X’.$ We want to compress all the info in $X$ into $X’,$ $I(X, X’) = H(X)$, so we must have $H(X’) \geq I(X, X’) = H(X)$. Initial state $X$ is maxentropic: its possible outcomes are all values of $n$ coin flips with a fixed number of heads, and $X$ has the highest possible $H(X)$ over those outcomes. Final state $X’$ we _choose_ to be maxentropic - we need $H(X’) \geq H(X)$, so we make $H(X’)$ as large as possible. However, note that the possible outcomes of $X’$ are a strict subset of the possible outcomes of $X$: possible outcomes of $X'$ are all values of $n$ coin flips with a fixed number of heads AND the first $w$ coins are all heads. So, we choose $X’$ to be maxentropic on this set of outcomes, but it’s a strictly smaller set of outcomes than for $X$, so the maximum achievable entropy $H(X’)$ will be less than $H(X)$. Thus: our condition $H(X’) \geq H(X)$ cannot be achieved. 

We cannot extract deterministic bits (i.e. work) from a single pool of maxentropic-subject-to-constraint random bits (i.e. heat), while still respecting the constraint.

Even more generally: if we have a pool of random variables which are maxentropic subject to some constraint, we won’t be able to compress them without violating that constraint. If the constraint fixes a value of $\sum_k f_k(X_k)$, and we want to deterministically fix $f_1(X_1)$, then that reduces the number of possible values of $\sum_{k>1} f_k(X_k)$, and therefore reduces the amount of information which the remaining variables can contain. Since they didn’t have any “spare” entropy before (i.e. initial state is maxentropic subject to the constraint), we won’t be able to “fit” all the information into the remaining entropy.

That’s a very general analogue of the idea that we can’t extract work from a single-temperature heat bath. How about two heat baths?

## Extracting Work From Two Heat Baths ^extracting-work-from-two

Now we have $2n$ coins to play with: $n$ with probability 0.1, and $n$ with probability 0.2. The entropy is roughly 0.73 bits per “hot” coin, and 0.47 bits per “cold” coin. So, we’d need $1.19n$ coins with a roughly 50/50 mix of heads and tails to contain all the info. That’s still too many heads: full compression would require roughly $.59n$ heads, and we only have about $(0.1 + 0.2)n = 0.3n$. But our initial distribution is no longer maxentropic given the overall constraint, so maybe it could work if we only partially compress the information?

Let’s set up the problem more explicitly, to maximize the work we can extract.

Our final distribution will contain $w$ deterministic bits and $2n-w$ information-containing bits. The information-containing bits must contain a total of $0.3n-w$ heads. In order to contain as much information as possible, the final distribution of those $2n-w$ bits should be maxentropic subject to the constraint on the number of heads. So, they should be _roughly_ (remember, large $n$) IID with probability $\frac{0.3n-w}{2n-w}$ of heads, with total entropy $-(2n-w)(\frac{1.7n}{2n-w}log(\frac{1.7n}{2n-w}) + \frac{0.3n-w}{2n-w}log(\frac{0.3n-w}{2n-w}))$. We set that equal to the amount of entropy we need (i.e. $1.19n$ bits), and solve for $w$. In this case, I find $w = 0.011n$. Since we started with about $0.3n$ heads, we’re able to extract about 3.7% of them as “work” (or 5.5% of the “hot” heads).

So we can indeed extract work from two heat baths at different temperatures.

Notably, the “efficiency” we calculated is _not_ the usual theoretical optimal efficiency from thermodynamics. That “optimal efficiency” comes from a slightly different problem - rather than converting _all_ our bits into as much work as possible, that problem considers the optimal conversion of random bits into work _at the margin_, assuming our heat baths don’t run out. In particular, that means we usually wouldn’t be using equal numbers of bits from the hot and cold pools.

This post is already plenty long, so I’ll save further discussion of thermodynamic efficiency and temperatures for another day.

## Takeaway ^takeaway

The point of this exercise is to cast core ideas of statistical mechanics - especially the more thermo-esque ideas - in terms which are easier to generalize beyond physics. To that end, the key ideas are:

-   Thermo-like laws apply when we can't gain information about a system (e.g. because we're designing a machine to operate in an environment which we can't observe directly at design time), can't lose information about a system at a low level (either due to physical reversibility constraints or because we don't want to throw out info), and the system has some other constraints (like energy conservation).
-   We can operate on the system in ways which move uncertainty around, without decreasing it.
-   If we want to move uncertainty around in a way which makes certain variables nearly deterministic (i.e. "extract work"), that's a compression problem.
-   We can't compress a maxentropic distribution, so we can't extract work from a single maxentropic-subject-to-constraint pool of variables without violating the constraint.
-   We can extract work from two pools of variables which are initially maxentropic under different constraints, while still respecting the full-system constraint.

_The follow-up post on thermodynamic efficiency and temperatures is_ [_here_](https://www.lesswrong.com/posts/eKiRX5oXHcYzQNSGw/generalized-heat-engine-ii-thermodynamic-efficiency-limit).

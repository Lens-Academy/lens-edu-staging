---
title: "Self-Embedded Agent's Shortform"
author:
  - "Alexander Gietelink Oldenziel"
source_url: "https://www.lesswrong.com/posts/km6wasEXXmx85v5yG/self-embedded-agent-s-shortform"
published: 2021-09-02
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "Shortform post by Alexander Gietelink Oldenziel introducing 'concept splintering' in imprecise probability: how the three equivalent classical notions of independence, and the notion of invariance under a symmetry, split into inequivalent concepts (strong/aleatoric vs. epistemic) once probability distributions are generalized to imprecise (convex-set) distributions. Includes a follow-up discussion applying the idea to the three equivalent definitions of mutual information.                   1.   2.  3.   y  x  x  y]. Example (splintering of invariance). There are often debates in foundations of probability, especially subjective Bayesian accounts about the 'right' prior. An ultra-Jaynesian point of view would argue that we are compelled to adopt a prior invariant under some symmetry if we do not posses subjective knowledge that breaks that symmetry ['epistemic invariance'], while a more frequentist or physicalist point of view would retort that we would need evidence that the system in question is in fact invariant under said symmetry ['aleatoric invariance']. In imprecise probability the notion of invariance under a symmetry splits into a weak 'epistemic' invariance and a strong 'aleatoric' invariance. Roughly spreaking, latter means that each individual distribution in the convex set pi, i∈Iis invariant under the group act"
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

[AI Alignment Forum](https://alignmentforum.org/posts/km6wasEXXmx85v5yG/self-embedded-agent-s-shortform)

This is a special post for quick takes by [Alexander Gietelink Oldenziel](https://www.lesswrong.com/users/alexander-gietelink-oldenziel). Only they can create top-level comments. Comments here also appear on the [Quick Takes page](https://www.lesswrong.com/quicktakes) and [All Posts page](https://www.lesswrong.com/allPosts).

## **Concept splintering in Imprecise Probability: Aleatoric and Epistemic Uncertainty.** ^concept-splintering-in-imprecise

There is a general phenomena in mathematics \[and outside maths as well!\] where in a certain context/ theory  $T_1$ we have two equivalent definitions   $\phi_1,\phi_2$ of a concept  $C$ that become inequivalent when we move to a more general context/theory  $T_2$. In our case we are moving from the concept of probability distributions to the concept of an imprecise distribution (i.e. a convex set of probability distributions, which in particular could be just one probability distribution). In this case the concepts of  '_**independence**_' and '**i**_**nvariant under group action**'_ will _**splinter into inequivalent concepts**_. 

**Example (splintering of Indepence)** In classical probability theory there are three equivalent ways to state that a distribution is independent 

1. $p(x,y)=p(x)p(y)$

 2. $p(x)=p(x|y)$

3. $p(y)=p(y|x)$

In imprecise probability these notions split into three inequivalent notions. The first is 'strong independence' or 'aleatoric independence'. The second and third are called 'irrelevance', i.e. knowing $y$ does not tell us anything about $x$ \[or for 3 knowing $x$ does not tell us anything about $y$\].  
    \     
  
**Example (splintering of invariance)**. There are often debates in foundations of probability, especially subjective Bayesian accounts about the 'right' prior. An ultra-Jaynesian point of view would argue that we are compelled to adopt a prior invariant under some symmetry if we do not posses subjective knowledge that breaks that symmetry \['epistemic invariance'\], while a more frequentist or physicalist point of view would retort that we would need evidence that the system in question is in fact invariant under said symmetry \['aleatoric invariance'\]. In imprecise probability the notion of invariance under a symmetry splits into a weak 'epistemic' invariance and a strong 'aleatoric' invariance. Roughly spreaking, latter means that each individual distribution in the convex set $p_i$, $i \in I$ is invariant under the group action while the former just means that the convex set is closed under the action

---

**Reply by Dalcy:**

Found an example in the wild with Mutual information! These equivalent definitions of Mutual Information undergo concept splintering as you go beyond just 2 variables: \* I\[X;Y\]=H\[X\]+H\[Y\]−H\[X,Y\] \* interpretation: common information \* ... become co-information, the central atom of your I-diagram \* \* I\[X;Y\]=D(Pr(x,y)∥Pr(x)Pr(y)) \* interpretation: relative entropy b/w joint and product of margin \* ... become total-correlation \* \* I\[X;Y\]=H\[X,Y\]−H\[X∣Y\]−H\[Y∣X\] \* interpretation: joint entropy minus all unshared info \* ... become bound information \* ... each with different properties (eg co-information is a bit too sensitive because just a single pair being independent reduces the whole thing to 0, total-correlation seems to overcount a bit, etc) and so with different uses (eg bound information is interesting for time-series).

**Reply by Alexander Gietelink Oldenziel:**

Wow, I missed this comment! This is a fantastic example, thank you!

have been meaning to write the concept splintering megapost - your comment might push me to finish it before the Rapture :D

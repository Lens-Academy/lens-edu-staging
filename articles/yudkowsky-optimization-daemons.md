---
title: "Optimization daemons"
author:
  - "Eliezer Yudkowsky"
source_url: "https://www.lesswrong.com/p/daemons"
published: 2016-03-22
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description: "When you optimize something so hard that it crystalizes into an optimizer, like the way natural selection optimized apes so hard they turned into human-level intelligences"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

If you subject a dynamic system to a _large_ amount of optimization pressure, it can turn into an optimizer or even an intelligence. The classic example would be how natural selection, in the course of extensively optimizing DNA to construct organisms that replicated the DNA, in one case pushed hard enough that the DNA came to specify a cognitive system capable of doing its own consequentialist optimization. Initially, these cognitive optimizers pursued goals that correlated well with natural selection’s optimization target of reproductive fitness, which is how these crystallized optimizers had originally come to be selected into existence. However, further optimization of these ‘brain’ protein chunks caused them to begin to create and share cognitive content among themselves, after which such rapid capability gain occurred that a [context change](https://arbital.greaterwrong.com/p/context_disaster?l=6q) took place and the brains’ pursuit of their internal goals no longer correlated reliably with DNA replication.

As much as this was, from a _human_ standpoint, a wonderful thing to have happened, it wasn’t such a great thing from the standpoint of inclusive genetic fitness of DNA or just having stable, reliable, well-understood optimization going on. In the case of AGIs deploying powerful internal and external optimization pressures, we’d very much like to not have that optimization deliberately or accidentally crystallize into new modes of optimization, especially if this breaks goal alignment with the previous system or breaks other safety properties. (You might need to stare at the [Orthogonality Thesis](https://arbital.greaterwrong.com/p/orthogonality?l=1y) until it becomes intuitive that, even though crystallizing daemons from natural selection produced creatures that were more humane than natural selection, this doesn’t mean that crystallization from an AGI’s optimization would have a significant probability of producing something humane.)

When heavy optimization pressure on a system crystallizes it into an optimizer—especially one that’s powerful, or more powerful than the previous system, or misaligned with the previous system—we could term the crystallized optimizer a “daemon” of the previous system. Thus, under this terminology, humans would be daemons of natural selection. If an AGI, after heavily optimizing some internal system, was suddenly taken over by an erupting daemon that cognitively wanted to maximize something that had previously correlated with the amount of available RAM, we would say this was a crystallized daemon of whatever kind of optimization that AGI was applying to its internal system.

This presents an AGI safety challenge. In particular, we’d want at least one of the following things to be true _anywhere_ that _any kind_ of optimization pressure was being applied:

-   The optimization pressure is (knowably and reliably) too weak to create daemons. (Seemingly true of all current systems, modulo the ‘knowably’ part.)
    
-   The subject of optimization is not Turing-complete or otherwise programmatically general and the restricted solution space cannot _possibly_ contain daemons no matter _how much_ optimization pressure is applied to it. (3-layer non-recurrent neural networks containing less than a trillion neurons will probably not erupt daemons no matter how hard you optimize them.)
    
-   The AI has a sufficient grasp on the concept of optimization and the problem of daemons to reliably avoid creating mechanisms outside the AI that do cognitive reasoning. (Note that if some predicate is added to exclude a particular type of daemon, this potentially runs into the [nearest unblocked neighbor](https://arbital.greaterwrong.com/p/nearest_unblocked?l=42) problem.)
    
-   The AI only creates cognitive subagents which share all the goals and safety properties of the original agent. E.g. if the original AI is [low-impact](https://arbital.greaterwrong.com/p/low_impact?l=2pf), [softly optimizing](https://arbital.greaterwrong.com/p/soft_optimizer?l=2r8), abortable, and targeted on [performing Tasks](https://arbital.greaterwrong.com/p/task_agi?l=6w), it only creates cognitive systems that are low-impact, don’t optimize too hard in conjunction with the original AI, abortable by the same shutdown button, and targeted on performing the current task.

---
title: "Announcing Timaeus"
author:
  - "Jesse Hoogland"
  - "Daniel Murfet"
  - "Alexander Gietelink Oldenziel"
  - "Stan van Wingerden"
source_url: "https://www.lesswrong.com/posts/nN7bHuHZYaWv9RDJL/announcing-timaeus"
published: 2023-10-22
created: 2026-11-27
accessed: 2026-11-27
llm-review:
  date: 2026-11-27
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-27
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hoogland-announcing-timaeus-img1-dd938373.png)

[Timaeus](https://timaeus.co/) is a new AI safety research organization dedicated to making fundamental breakthroughs in technical AI alignment using deep ideas from mathematics and the sciences. Currently, we are working on [singular learning theory](https://www.lesswrong.com/s/czrXjvCLsqGepybHC) and [developmental interpretability](https://www.lesswrong.com/posts/TjaeCWvLZtEDAS5Ex/towards-developmental-interpretability). Over time we expect to work on a broader research agenda, and to create [understanding-based evals](https://www.lesswrong.com/posts/uqAdqrvxqGqeBHjTP/towards-understanding-based-safety-evaluations#:~:text=Rather%20than%20evaluating%20a%20final,and%20why%20they%20got%20it.) informed by our research. 

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hoogland-announcing-timaeus-img2-2ed2ca64.jpg)

Let sleeping gods (not) lie.

# Activities ^activities

Our primary focus is research. For now, we're a remote-first organization. We collaborate primarily through online [seminars](https://metauni.org/slt/) and the [DevInterp Discord](https://discord.gg/pCf4UynKsc), with regular in-person meetings at workshops and conferences (see below). We're also investing time in academic outreach to increase the general capacity for work in technical AI alignment.

## Research ^research

We believe singular learning theory, a mathematical subject founded by [Sumio Watanabe](https://watanabe-www.math.dis.titech.ac.jp/users/swatanab/), will lead to a better fundamental understanding of large-scale learning machines and the computational structures that they learn to represent. It has already given us concepts like the [learning coefficient](https://arxiv.org/abs/2308.12108) and [insights into phase transitions](https://arxiv.org/abs/2310.06301) in Bayesian learning. We expect significant advances in the theory to be possible, and that these advances can inform new tools for alignment.

[Developmental interpretability](https://www.lesswrong.com/posts/TjaeCWvLZtEDAS5Ex/towards-developmental-interpretability) is an approach to understanding the emergence of structure in neural networks, which is informed by singular learning theory but also draws on mechanistic interpretability and ideas from statistical physics and [developmental biology](https://journals.biologists.com/dev/article/150/11/dev201280/312613/A-dynamical-systems-treatment-of-transcriptomic). The key idea is that _phase transitions organize learning_ and that _detecting, locating, and understanding these transitions_ could pave a road to evaluation tools that _prevent_ the development of dangerous capabilities, values, and behaviors. We're engaged in a [research sprint](https://manifund.org/projects/scoping-developmental-interpretability-xg55b33wsfc) to test the assumptions of this approach. 

We see these as two particularly promising research directions, and they are our focus for now. Like any ambitious research, they are not guaranteed to succeed, but there's plenty more water in the well. Broadly speaking, the research agenda of Timaeus is oriented towards solving problems in technical AI alignment using deep ideas from across many areas of mathematics and the sciences, with a "full stack" approach that integrates work from pure mathematics through to machine learning experiments.

The outputs we have contributed to so far:

-   [Hoogland & Van Wingerden (2023)](https://www.lesswrong.com/posts/6g8cAftfQufLmFDYT/you-re-measuring-model-complexity-wrong), a distillation of Lau et al
-   [The DevInterp Repo & Python Package](https://github.com/timaeus-research/devinterp)
-   [The 2023 Primer on Singular Learning Theory and Alignment](https://www.youtube.com/watch?v=bFVGc2UKARc)

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hoogland-announcing-timaeus-img3-cdb38910.png)

## Academic Outreach ^academic-outreach

AI safety remains bottlenecked on senior researchers and mentorship capacity. The young people already in the field will grow into these roles. However, given the scale and urgency of the problem, we think it is important to open inroads to academia and encourage established scientists to spend their time on AI safety. 

Singular learning theory and developmental interpretability can serve as a natural bridge between the emerging discipline of AI alignment and existing disciplines of mathematics and science, including physics and biology. We plan to spend part of our time onboarding scientists into alignment via concrete projects in these areas.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hoogland-announcing-timaeus-img4-9c8cb299.jpg)

## Conferences ^conferences

We're organizing conferences, retreats, hackathons, etc. focusing on singular learning theory and developmental interpretability. These have included and will include:

-   [Conference on singular learning theory and AI alignment](https://www.lesswrong.com/posts/HtxLbGvD7htCybLmZ/singularities-against-the-singularity-announcing-workshop-on) (Berkeley, June-July 2023)
-   [Retreat on singular learning theory](https://devinterp.com/events/2023-q3-amsterdam-retreat) (Amsterdam, September 2023)
-   [Hackathon on developmental interpretability](https://events.humanitix.com/hackathon-developmental-interpretability) (Melbourne, October 2023)
-   [Conference on developmental interpretability](https://www.lesswrong.com/posts/QpFiEbqMdhaLBPb7X/apply-now-for-the-devinterp-2023-fall-summit) (Oxford, November 2023)
-   [AI safety demo days](https://devinterp.com/participate/research-sprints) (Virtual, November 2023) open to independent and junior researchers to present their work.
-   We've been amassing a list of [project ideas](https://devinterp.com/projects) to inspire researchers.

# Team ^team

## Core Team ^core-team

-   [**Jesse Hoogland**](https://jessehoogland.com/) (Executive Director) has a MSc. in theoretical physics from the University of Amsterdam and previously cofounded a health-tech startup before going all in on AI safety. He participated in MATS 3.0 & 3.1 under the supervision of Evan Hubinger and was a research assistant in David Krueger's lab. 
-   [**Stan van Wingerden**](https://www.lesswrong.com/users/stan-van-wingerden?mention=user) (Operations & Finances) has a MSc. in theoretical physics from the University of Amsterdam and was previously the CTO of an algorithmic trading firm. 
-   [**Alexander Gietelink Oldenziel**](https://www.lesswrong.com/users/alexander-gietelink-oldenziel?mention=user) (Strategy & Outreach) is a DPhil student at University College London with a background in mathematics.

The research agenda that we are contributing to was established by [**Daniel Murfet**](http://therisingsea.org/), who is a mathematician at the University of Melbourne and an expert in singular learning theory, algebraic geometry, and mathematical logic.

## Research Assistants ^research-assistants

We just concluded a round of hiring and are excited to bring on board several very talented Research Assistants (RAs), starting with

-   Sai Niranjan
-   [**George Wang**](https://www.georgeyw.com/)

## Friends and Collaborators ^friends-and-collaborators

Here are some of the people we are actively collaborating with:

-   [**Susan Wei**](https://www.suswei.com/) (Statistician, University of Melbourne)
-   [**Calin Lazaroiu**](https://scholar.google.com/citations?user=O3CEqUoAAAAJ&hl=en) (Mathematical physicist, UNED-Madrid and IFIN-HH Bucharest)
-   [**Simon Pepin Lehalleur**](https://simon-pepin.github.io/) (Mathematician, Postdoc at University of Amsterdam)
-   [**Tom Burns**](https://tfburns.com/) (Neuroscientist, Postdoc at ICERM, Brown University)
-   [**Matthew Farrugia-Roberts**](https://far.in.net/) (Research assistant, David Krueger's AI Safety Lab, University of Cambridge)
-   [**Liam Carroll**](https://lemmykc.github.io/) (Independent AI safety researcher)
-   [**Jake Mendel**](https://www.linkedin.com/in/jake-m-b05289126/) (Research scientist, Apollo Research)
-   [**Zach Furman**](https://www.linkedin.com/in/zach-furman-4936a0a5) (Independent AI safety researcher)
-   [**Rumi Salazar**](https://www.linkedin.com/in/rumi-salazar-06a93b116) (Independent AI safety researcher)

Inclusion on this list does not imply endorsement of Timaeus' views.

## Advisors ^advisors

We're advised by [**Evan Hubinger**](https://www.alignmentforum.org/users/evhub) and [**David ("Davidad") Dalrymple**](https://www.alignmentforum.org/users/davidad). 

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hoogland-announcing-timaeus-img5-a2fd26f2.jpg)

(DALL-E 3 still has a hard time with icosahedra.)

# FAQ ^faq

## Where can I learn more, and contact you? ^where-can-i-learn

Learn more on the [Timaeus](https://timaeus.co/) webpage. You can email [Jesse Hoogland](mailto:jesse@timaeus.co).

## What about capabilities risk? ^what-about-capabilities-risk

There is a risk that fundamental progress in either singular learning theory or developmental interpretability could contribute to further acceleration in AI capabilities in the medium term. We take this seriously and are seeking advice from other alignment researchers and organizations. By the end of our current research sprint we will have in place institutional forms to help us navigate this risk.

Likewise, there is a risk that outreach which aims to involve more scientists in AI alignment work will also accelerate progress in AI capabilities. However, those of us in academia can already see that as the risks become more visible, scientists are starting to think about these problems on their own. So the question is not _whether_ a broad range of scientists will become interested in alignment but _when_ they will start to contribute and _what they work on._ 

It is part of Timaeus' mission to help scientists to responsibly contribute to technical AI alignment, while minimizing these risks.

## Are phase transitions really the key? ^are-phase-transitions-really

The strongest critique of developmental interpretability we know is the following: while it is established that phase transitions exist in neural network training, it is not yet clear _how common_ they are, and whether they make a _good target_ for alignment.

We think developmental interpretability is a good investment in a world where many of the important structures (e.g., circuits) in neural networks form in phase transitions. Figuring out whether we live in such a world is one of our top priorities. It's not trivial because even if transitions exist they may not necessarily be visible to naive probes. Our approach is to systematically advance the fundamental science of finding and classifying transitions, starting with smaller systems where transitions can be definitively shown to exist.

## How are you funded? ^how-are-you-funded

We're funded through a [\$142k Manifund grant](https://manifund.org/projects/scoping-developmental-interpretability-xg55b33wsfc) led primarily by [Evan Hubinger](https://manifund.org//projects/scoping-developmental-interpretability-xg55b33wsfc?tab=comments#3fd4492b-9fad-0356-3a72-b9c9f56e462a), [Ryan Kidd](https://manifund.org//projects/scoping-developmental-interpretability-xg55b33wsfc?tab=comments#08b1f696-1dc1-60d4-5b74-475276d5e16c), [Rachel Weinberg](https://manifund.org//projects/scoping-developmental-interpretability-xg55b33wsfc?tab=comments#0498fe5e-fbb1-6237-d0f5-f8aba9cd968e), and [Marcus Abramovitch](https://manifund.org//projects/scoping-developmental-interpretability-xg55b33wsfc?tab=comments#55989ce8-aedf-c739-08af-a7166a4e27cc). We are fiscally sponsored by [Ashgro](https://ashgro.org/). 

## "Timaeus"? How do I even pronounce that? ^timaeus-how-do-i

[Pronounce it however you want.](https://forvo.com/word/timaeus/#en)

Timaeus is the eponymous character in the [dialogue](https://en.wikipedia.org/wiki/Timaeus_\(dialogue\)) where Plato introduces his theory of forms. The dialogue posits a correspondence between the elements that make up the world and the Platonic solids. That's wrong, but it contains the germ of the idea of the unreasonable effectiveness of mathematics in understanding the natural world. 

We read the Timaeus dialogue with a spirit of hope, in the capacity of the human intellect to understand and solve wicked problems. The narrow gate to human flourishing is preceded by a narrow path. 

We'll see you on that path.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/hoogland-announcing-timaeus-img6-73dcc4dc.jpg)

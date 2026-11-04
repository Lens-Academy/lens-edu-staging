---
title: "Formal Metaethics and Metasemantics for AI Alignment"
author:
  - "June Ku"
source_url: "https://www.lesswrong.com/posts/85vp2kgFZoycFqr5G/formal-metaethics-and-metasemantics-for-ai-alignment-1"
published: 2019-10-08
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## **A Brief Introduction to MetaEthical.AI** ^a-brief-introduction-to

_tl;dr: AIXI for Friendliness_

\[Crossposted from my new [blog](https://medium.com/@june_ku/formal-metaethics-and-metasemantics-for-ai-alignment-2e72533cad6d).\]

**Abstract:** We construct a fully technical ethical goal function for AI by directly tackling the philosophical problems of metaethics and mental content. To simplify our reduction of these philosophical challenges into “merely” engineering ones, we suppose that unlimited computation and a complete low-level causal model of the world and the adult human brains in it are available.

Given such a model, the AI attributes beliefs and values to a brain in two stages. First, it identifies the syntax of a brain’s mental content by selecting a decision algorithm which is i) isomorphic to the brain’s causal processes and ii) best compresses its behavior while iii) maximizing charity. The semantics of that content then consists first in sense data that primitively refer to their own occurrence and then in logical and causal structural combinations of such content.

The resulting decision algorithm can capture how we decide what to _do_, but it can also identify the ethical factors that we seek to determine when we decide what to _value_ or even how to _decide_. Unfolding the implications of those factors, we arrive at what we should do. All together, this allows us to imbue the AI with the necessary concepts to determine and do what we should program it to do.

> See the open source code and commentary at [www.metaethical.ai](http://www.metaethical.ai/)

## Motivation ^motivation

Researchers like Eliezer Yudkowsky and Nick Bostrom, among others, have argued for the urgent need to develop a rigorous framework for ensuring that smarter-than-human intelligence will be beneficial for humanity. I think of them and the community around their respective nonprofits, the [Machine Intelligence Research Institute](https://intelligence.org/) and the [Oxford Future of Humanity Institute](https://www.fhi.ox.ac.uk/), as tending to share a cluster of views, including the following:

-   We should have a wide probability distribution over when human-level AI will be developed. If we go by [expert predictions](https://nickbostrom.com/papers/survey.pdf), most predict it will arrive within this century. A cautionary approach should prepare for even more rapid timelines.
-   Once AI that is at least as intelligent as its human creators has been developed, there is a [positive feedback loop](http://consc.net/papers/singularity.pdf) in which it can take over the task of improving its own intelligence, quickly resulting in a superintelligence vastly greater than that of humans.
-   A silicon-based intelligence will have [many natural advantages](https://intelligence.org/files/IEM.pdf) that would further compound this process, e.g. ease of faithful replication, readily available additional hardware, already million-fold increase in serial computational speed relative to biological neurons, long-term exponential Moore’s law trend as well as realistic plans and models for its continuation.
-   Virtually any sufficiently advanced intelligence will [converge upon certain instrumental goals](https://pdfs.semanticscholar.org/4618/cbdfd7dada7f61b706e4397d4e5952b5c9a0.pdf) to persist and acquire more resources and power, if only to better serve whatever intrinsic goals it may have.
-   There is [no automatic guarantee](https://nickbostrom.com/superintelligentwill.pdf) that greater intelligence coincides with better ethics. There is also tremendous economic incentive to develop ever smarter AI but not necessarily to make it safer or beneficial in the long run. If anything, each private party’s incentive may be to [cut corners on safety](https://www.fhi.ox.ac.uk/wp-content/uploads/Racing-to-the-precipice-a-model-of-artificial-intelligence-development.pdf) to get to market quicker.
-   Many naive approaches to aligning AI with our values fail. Human values have a great deal of [hidden complexity and missing just one dimension](https://intelligence.org/files/ComplexValues.pdf) can lead to very undesirable outcomes. Therefore, a _metaethical_ approach seems to be more promising than hoping to capture all ethical principles at the object level.

My own inquiry into metaethics began long before these ideas were written. In fact, I had even reached a point where I felt I could explain my [reductionist metaethics](http://www.metaethical.ai/norm_descriptivism.pdf) to other philosophers. But having followed the development of the AI safety literature with great interest, I felt a renewed sense of purpose and urgency. It seemed we’ll need to not only solve perennial philosophical problems but do so with sufficient precision to make a _computer_ understand them. What is more, it looked like we were in a race to accomplish it all before the arguably exponential advancement in AI crossed some unknown threshold.

Having mentioned all this, I will not be arguing for the above claims here. And while this forms _my_ primary motivation, I actually don’t think agreement with any of them is necessary to appreciate the metaethics and metasemantics I develop here. I have spent enough time in academic philosophy to appreciate such theories in the theoretical spirit in which they have often been developed. Formulating them in code as I have done could be seen as just a notational variant to the more conventional expression of certain rigorous philosophical theories in mathematical logic. Doing so helps us avoid misleading vagueness and ambiguity and ensures maximal precision in our thinking and communicating, all of which can be appreciated without regard to any practical applications.

Still, I hope many of you have already or will soon come to appreciate some of the backdrop of this MIRI–FHI cluster of views. It’s said that necessity is the mother of invention. It has certainly driven me to be more ambitious and aim for higher precision than I thought possible in philosophy. To have any hope of success, I realized I would need to delve into mathematics and computer science and bridge the conceptual divide. In doing so, I was excited to discover new inspiration and draw connections I doubt I would have made otherwise. And taking on an engineering mindset, I found myself pruning search trees that initially sounded appealing but turned out not to be fruitful, while finding new appreciation for theories that shed new light and enabled further technical progress.

While many areas of philosophy can benefit from a more technical mindset, I think conversely many in computer science or other mathematical fields may be too eager to apply whatever technical tools they may currently have at their disposal without pausing to ponder whether a problem is still at a philosophical stage in which important conceptual advancements must first take place. Perhaps these advancements have even been made already in academic philosophy but they are not aware of them, while the philosophers in turn are not aware of how to formalize them.

What follows is a mixture of original contributions to philosophical problems, some standard or not-so-standard components borrowed from across computer science and philosophy, and novel ways of weaving them all together. Throughout it all, I have tried my best to balance faithfulness to the subtleties of philosophical reality, the rigor of formalizing these theories, the urgency of making and communicating this progress, and the practicalities of engineering an initial prototype of a wildly ambitious project.

While I don’t necessarily trust our civilization to get philosophy right, I think it is quite good at making progress on well-defined technical problems. I hope I have largely succeeded in turning the philosophical problems of getting an AI to understand and share our values into an engineering problem — and hopefully one we can solve in time.

> See the open source code and commentary at [www.metaethical.ai](http://www.metaethical.ai/)

## An Apology ^an-apology

In an ideal world, I would have accomplished the above while explaining and justifying each philosophical step up to the standards of contemporary analytic philosophy and relating them to the current and historical literature. Moreover, on the technical side, the mathematical formulas would be written and typeset in beautiful LaTeX with ample diagrams and gentle tutorials.

Or you know, I could have at least written it in English. Instead, I chose to write it in a little known programming language called setlX (although I’ve since interspersed the code with considerable philosophical comments). My choice at the time and perhaps even now, was on the one hand, to struggle with writing math with limited experience or institutional support. Or on the other hand, I could leverage my long experience and intuition with programming to write essentially the same content in a language with clear semantics in set theory — the classic lingua franca of mathematics. On top of that, I’d have a compiler to check for bugs and an interactive console serving as a concrete interface by which to manipulate very abstract objects and functions.

In further defense of setlX, I find it to be a very elegant and powerful language. Its relatively few primitives are sufficient to concisely construct complex data and algorithms while being small enough to [pick up fairly quickly](http://www.metaethical.ai/v19-10/#setlx-cheat_sheet) if you have some experience with programming, mathematics or logic. Not surprisingly, writing in it feels like you’re programming close to the mathematical essence.

Despite its initial unfamiliarity, I hope you will give setlX, my code and my commentary a chance. Even if you are not technically inclined, I expect that with a little patience, a synopsis can be gleaned from the comments — the most important of which I’ve gathered into a Key Concepts outline beside the code. Other than that, I have not imposed much of an ordering but tried to enable a more free exploration by hyperlinking procedure calls to that procedure’s definition, which often has at least a short explanatory comment.

Where I have left important explanations and justifications sparse, I’ve tried to include links to those of others who have likely done a better job than I would have. I wish I could have done more but I have mainly been optimizing for solving the problem rather than communicating the solution.

> See the open source code and commentary at [www.metaethical.ai](http://www.metaethical.ai/)

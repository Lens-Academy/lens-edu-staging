---
title: "Introduction"
author:
  - "Markov Grey"
  - "Charbel-Raphaël Segerie"
source_url: "https://ai-safety-atlas.com/chapters/v1/capabilities/introduction/"
published: 2026-06-18
created: 2026-06-18
accessed: 2026-06-18
description:
tags:
  - "article-importer"
---

{++{"author":"Luc's AI","timestamp":1785073559182}@@%%
Add discussion note here:

...

%%

++}AI is an incredibly fast moving field. To talk about risks and how to make it safe in the future, we first need to understand where it is today and where it might be going in the future.

---

**AI has undergone a massive shift in the last decade.** Game-playing systems developed strategic creativity that surprised grandmasters, language models evolving from funny autocomplete failures to software engineering assistants handling codebases spanning thousands of files. These types of examples reflect a change in how technology is evolving, and raise a question that this entire book tries to answer: how do you make something safe when you don't fully understand what it can do, and when its abilities might change dramatically between the time you start reading this chapter and the time you finish?

**This first chapter is about mapping the territory.** Before we can discuss dangerous capabilities, alignment strategies, technical solutions or governance frameworks—the subjects of Chapters 2, 3, and 4—the first step is getting a sense of what AI systems can actually do right now, how they got here, and where the future trends point.

**The first question to answer is: what counts as "general" intelligence?** The systems we are seeing now represent a move from narrow AI—systems that do one thing well—to general purpose AI systems (foundation models) that learn general patterns, adapt to new situations and do many things well. The term AGI gets thrown around constantly, but different people mean wildly different things by it. We'll walk you through a couple of different approaches to defining intelligence, going from the Turing Test to psychometric frameworks, before settling on a practical usable definition: capability and generality as continuous axes rather than binary categories. The goal is to be able to make specific concrete statements like - "*this system performs at the 85th percentile across 30% of cognitive domains as measured by …*"—concrete enough to measure, track, and build policy around.

**The second question everyone asks: why is this happening so fast recently?** The answer is the "bitter lesson" of AI research— massive computation consistently beats human-engineered knowledge. We'll look at scaling laws—the empirical relationships showing that more data and compute predictably produce better performance—and various sides of the debate about whether scale alone is sufficient (and sustainable) for transformative AI, or whether we'll need some other algorithmic breakthroughs.

**The last part of the chapter will look ahead at the future.** Predicting when AI might automate all cognitive labor determines which safety strategies are even viable. If transformative AI arrives by 2030, we need solutions that work with current systems and scale quickly. If it's 2050, we have time for fundamental research. This means looking at the different scenarios for "takeoff"—whether progress will be gradual or explosive, continuous or discontinuous—and what that means for our ability to respond.

**The specific examples and benchmark scores in this chapter will be outdated soon, but the underlying patterns will remain.** Scaling laws, emergent capabilities, the shift from narrow to general systems—these trends are stable enough for you to learn about, even as individual benchmarks become obsolete. By the end of this chapter, you should have a concrete framework for how to define AGI, and much clearer perspective on the debates shaping the field of AI safety.

Let's start with what these systems can actually do—and how quickly that list is growing.

![Figure 1.1](https://ai-safety-atlas.com/_astro/954ddc42c48965ad869ad27a57cacdeb273883e1f00e0fa554e550babe8bd84f.B781Q3hr_ZFCV6i.webp)

*Figure 1.1: We first explain foundation models, which have been continuously showing improved capabilities due to scale. Then examine empirically observed scaling laws. Based on these trends we look at some techniques that researchers use to try and forecast future AI progress.*

---
id: 'ef0a13df-73af-4cf9-8bb3-9c93e22cf7a3'
slug: xlab-control-p2-overview
title: "Course Overview"
tags:
  - work-in-progress
---
%% Orientation module before Unit 1 of AI Control 2, added September 2026 to match AI Control 1 and the Compute Verification courses. Day summaries mirror the Day N overview lenses in each unit; keep them in sync. %%

# Lens: About This Course
id:: f9f9439d-b91b-4a98-a3eb-75d9b6e92ccb
tldr:: AI Control 1 ended inside high-stakes control. This second course puts you in the red team's seat, then moves to failures that only matter in aggregate, to models that are not schemers at all, and to the question of whether you could simply make a deal.
summary_for_tutor:: Orientation page before Unit 1 of AI Control 2. The learner reads what the course is about, that it assumes AI Control 1, what each of the five days covers and how the days run, and that it runs to the end of XLab's track. Do not teach later content in detail; if asked, point to the day that covers it. If a learner has not done AI Control 1, say plainly that this course starts from its results (the case for control, the founding paper's protocols, catching schemers, the control toolkit, high-stakes monitoring) and does not restate them, and point them to that course.
reading_minutes:: 3
tutor_minutes:: 0
#### Text
content::
\## What this course is about

AI Control 1 made the case for deploying a model that may be scheming and still keeping it from causing a catastrophe, and worked through the machinery of high-stakes control: protocols, monitoring, resampling. This is AI Control 2, the second of two Lens Academy courses on XLab's curriculum. It starts by putting you in the red team's seat against those protocols, then widens the threat model: failures that only matter in aggregate, models that hide what they can do, models that are not schemers at all, and whether you could simply make a deal with an AI instead of containing it. Both courses are built on the open-source [AI Control track](https://aisafetytracks.com/tracks/control) of [XLab](https://xrisk.uchicago.edu/), the Existential Risk Laboratory at the University of Chicago.

:::callout {title="This course continues another one" tone="blue"}
AI Control 1 is a prerequisite. This course picks up where it stopped, in the middle of XLab's module on high-stakes control, and runs to the end of XLab's track. It does not restate Part 1: the case for control, the founding paper's protocols, catching schemers, the control toolkit and high-stakes monitoring are assumed.
:::

\## What you will learn

By the end of this course you will be able to attack an untrusted-monitoring protocol through collusion and design legibility protocols that resist it; tell high-stakes from low-stakes control and say what changes when failures only matter in aggregate; recognise sandbagging and exploration hacking as threat models and stress-test a capability elicitation method; judge a benchmark for research sabotage; reason about threat models that are not scheming, reward seekers, satiable preferences and spillway motivations, and measure reward seeking empirically; weigh deals with early misaligned AIs and the barriers to them; and know where to go next in control research.

\## How the course runs

Five days. Each day is about four to five hours of reading and exercises on your own, and ends with a group meeting to work through the arguments the readings leave open. The times we give are ours, estimated from what a learner actually does including the exercises, so they are longer than the figures on XLab's site. A few lessons are marked optional; follow curiosity rather than completeness.

\## The five days

:::callout {title="Day 1: Collusion, legibility, and low-stakes control" tone="blue"}
Two guided exercises on high-stakes protocols, collusion in untrusted monitoring and legibility protocols for trusted monitoring, then the shift to low-stakes control: failures that only matter in aggregate, and how to handle them.
:::

:::callout {title="Day 2: Sandbagging and capability elicitation" tone="blue"}
Strategic underperformance: sandbagging and exploration hacking as a threat model, a guided exercise on stress-testing capability elicitation, and the paper on whether models can learn to resist RL training.
:::

:::callout {title="Day 3: Research sabotage and exploration hacking in practice" tone="blue"}
A benchmark for detecting and fixing research sabotage in ML codebases, then the long guided exercise on exploration hacking. An optional lens holds the full capability elicitation paper.
:::

:::callout {title="Day 4: Beyond scheming: reward seekers" tone="blue"}
Threat models that are not schemers: what a reward seeker is, whether cheaply satisfied preferences can be satiated, channelling reward hacking into a spillway motivation, the empirical evidence on reward seeking, and a guided exercise on measuring it.
:::

:::callout {title="Day 5: Deals with AIs and next steps" tone="blue"}
Trading with misaligned AIs: why you might make deals with early schemers, the barriers to trading with them, and then where to go from here: programs, organisations and opportunity boards for continuing in AI control.
:::

\## What comes after

This course completes XLab's AI Control track. Day 5 closes with where to go next: programs, organisations and opportunity boards for continuing in AI control research.

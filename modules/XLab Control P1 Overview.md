---
id: '41288b48-ff90-412f-99d0-03da227778eb'
slug: xlab-control-p1-overview
title: "Course Overview"
tags:
  - work-in-progress
---
%% Orientation module before Unit 1, added September 2026 to match the Compute Verification courses. Based on XLab's public track page (https://aisafetytracks.com/tracks/control). Day summaries mirror the Day N overview lenses in each unit; keep them in sync. %%

# Lens: About This Course
id:: 75e01a0e-4d70-44c5-b7ed-d21cbc91a234
tldr:: Assume a frontier model may be scheming and design so it still cannot hurt you. This course works through the first half of XLab's AI Control curriculum: why control, the founding paper, catching schemers, the toolkit, and high-stakes monitoring.
summary_for_tutor:: Orientation page before Unit 1. The learner reads what the course is about, that it is built on XLab's open-source AI Control curriculum, what each of the five days covers and how the days run, what the prerequisites are, and that AI Control 2 is a separate course that continues from here. Do not teach later content in detail; if asked, point to the day that covers it, or say that collusion, legibility, low-stakes control, sandbagging, reward seekers and deals belong to the second course.
reading_minutes:: 3
tutor_minutes:: 0
#### Text
content::
\## What this course is about

Alignment tries to make a model want what we want. AI control asks what holds if that failed: can we deploy a model that may be deliberately working against us, get useful work out of it, and still make sure it cannot cause a catastrophe? This is AI Control 1, the first of two Lens Academy courses on that question. It runs from the case for control to the concrete machinery of high-stakes monitoring; AI Control 2 picks up where it stops. Both are built on the open-source [AI Control track](https://aisafetytracks.com/tracks/control) of [XLab](https://xrisk.uchicago.edu/), the Existential Risk Laboratory at the University of Chicago, a hands-on technical track that reads the field's primary literature in full, with exercises woven between the sections. Everything is here on Lens: the readings, XLab's explanations, the exercises and the interactive pieces.

\## What you will learn

By the end of this course you will be able to explain why control is a distinct line of defense from alignment and why it is easier to evaluate; read the founding control paper and its protocols, trusted and untrusted monitoring, editing and deferral, and say what a red team is measuring; build an attack tree for a deployed model and prioritise the threats on it; argue both for and against control research and place a protocol on the safety-usefulness frontier; sort control work into detection, prevention, response, evaluations and environments; and follow how monitoring, resampling and rogue-deployment defenses work in a real high-stakes deployment.

\## How the course runs

Five days. Each day is about four to five hours of reading and exercises on your own, and ends with a group meeting to work through the arguments the readings leave open. The times we give are ours, estimated from what a learner actually does including the exercises, so they are longer than the figures on XLab's site. A few lessons are marked optional; follow curiosity rather than completeness.

XLab asks for comfort reading papers and familiarity with AI safety at the level of an introductory course. If you have done AI Risk Fundamentals or its equivalent, you are ready.

\## The five days

:::callout {title="Day 1: Why control" tone="blue"}
Why assume a frontier model may be scheming and design so it still cannot hurt you: the case for control as a second line of defense behind alignment, and attack trees as the way to think about what a model could do to you.
:::

:::callout {title="Day 2: The founding paper and passing the buck" tone="blue"}
The paper that started the field: trusted monitoring, untrusted monitoring, editing and deferral, measured against a red team that tries to insert backdoors. Then the question of when it is safe to let AIs take over the work of keeping AIs safe.
:::

:::callout {title="Day 3: Catching schemers, prioritising threats, and the case against control" tone="blue"}
Why catching a model red-handed is a win rather than a failure, which threats to prioritise and how diffuse threats like research sabotage differ from concentrated ones, then the arguments for and against control, the safety-usefulness tradeoff, and how to judge what control buys you.
:::

:::callout {title="Day 4: Plans, the control toolkit, and high-stakes framing" tone="blue"}
The Plans A to D landscape for misalignment risk, then the taxonomy of control work: detection, prevention and response mitigations, control evaluations, environments, and the map of areas of control work. Closes with the framing for high-stakes control.
:::

:::callout {title="Day 5: High-stakes monitoring and mitigation" tone="blue"}
Win, continue and lose scenarios; rogue deployments inside and outside the lab; a systems architecture for autonomous research agents; monitoring and mitigation in real deployments; resampling as a control technique; and why settings for high-stakes control research are hard to build.
:::

\## What comes after

This is the first of two courses on XLab's AI Control curriculum. AI Control 2 continues with guided exercises on collusion and legibility, low-stakes control, sandbagging and capability elicitation, threat models beyond scheming, and deals with early misaligned AIs.

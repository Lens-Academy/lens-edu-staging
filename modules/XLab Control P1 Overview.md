---
id: '41288b48-ff90-412f-99d0-03da227778eb'
slug: xlab-control-p1-overview
title: "Course Overview"
---
%% Orientation module before Unit 1 of AI Control 1. Added September 2026; rewritten October 2026 when XLab's AI Control track was re-cut from two courses into three five-unit courses (AI Control 1, 2, 3, strict XLab lens order). Based on XLab's public track page (https://aisafetytracks.com/tracks/control). Unit summaries are written from the tldr, summary_for_tutor and openers of the lenses in each unit module; keep them in sync when a unit changes. Unit length including the end-of-unit learning-outcome tests (as estimated in each unit module's note): 213 to 264 minutes (U1 233, U2 240, U3 264 with four tests, U4 237, U5 213); updated 2026-10-04 for raised lens tutor times and new learning outcomes (U1 was 220, U4 220). Unit 3 is the long one, so the learner text names it. Learners see units, not days: the course also runs in less intensive formats. %%

# Lens: About This Course
id:: 75e01a0e-4d70-44c5-b7ed-d21cbc91a234
tldr:: Assume a frontier model may be scheming and design so it still cannot hurt you. This is the first of our three AI Control courses, based on XLab's AI Control track. It makes the case for control, works through the founding paper's protocols, and ends by asking whether control is worth what it costs.
summary_for_tutor:: Orientation page before Unit 1 of AI Control 1, the first of three Lens Academy AI Control courses (AI Control 2 assumes this course; AI Control 3 assumes this course and AI Control 2). The learner reads what the course is about, what to know before starting, what the course teaches, how the units run (about three and a half hours of self-study each, some units up to about four, Unit 3 about four and a half, a group meeting at the end, short learning-outcome tests closing each unit), what each of the five units covers, and what the next two courses cover. Do not teach later content in detail; if asked, point to the unit that covers it, or say that the control toolkit, rogue deployments, monitoring and resampling in real deployments, collusion, legibility and low-stakes control belong to AI Control 2, and capability elicitation, exploration hacking, reward seekers and deals with AIs belong to AI Control 3.
reading_minutes:: 5
tutor_minutes:: 0
#### Text
content::
\## What this course is about

Alignment tries to make a model want what we want. AI control asks what holds if that failed: can we deploy a model that may be deliberately working against us, get useful work out of it, and still make sure it cannot cause a catastrophe? This is AI Control 1, the first of three Lens Academy courses on that question. It makes the case for control, takes apart the paper that started the field, and ends by asking whether control research is worth what it costs. AI Control 2 and AI Control 3 continue from here. All three are built on the open-source [AI Control track](https://aisafetytracks.com/tracks/control) of [XLab](https://xrisk.uchicago.edu/), the Existential Risk Laboratory at the University of Chicago, and follow its order.

:::callout {title="Before you start" tone="blue"}
We recommend that you are comfortable reading research papers and familiar with AI safety. If you have done [AI Risk Fundamentals](https://lensacademy.org/ai-risk-fundamentals) or an equivalent, you are ready.
:::

\## What you will learn

By the end of this course you will be able to:

- Explain what control is, how it differs from alignment, and why a control claim can be tested with a red team while an alignment claim currently cannot.
- Build an attack tree for a model trying to slip a backdoor into production.
- Use the founding control paper's game (an untrusted model, a trusted model and a small human audit budget) to work out why a protocol reaches the safety it does and how a red team best responds.
- Compare trusted monitoring, defer to trusted, untrusted monitoring and trusted editing on the safety-usefulness frontier.
- Say when handing safety work to AI agents would be safer than keeping humans in the loop.
- Explain why catching a model red-handed is a win, rank the threats a deployed model poses, and tell concentrated failures from diffuse ones.
- Argue for and against control research, and decide where research effort should go as the available political will changes.

\## How the course runs

Five units. Each unit is about three and a half hours of reading and exercises on your own, some up to about four; Unit 3, the longest, is about four and a half. Each unit closes with short tests on what it taught, and ends with a group meeting to work through the arguments the readings leave open. A few lessons fold away extra material, such as a post's appendices, which you can open if you want to go deeper.

\## The five units

:::callout {title="Unit 1: Why control" tone="blue"}
Why assume a frontier model may be scheming and design so that it still cannot hurt you. A short welcome, then Greenblatt and Shlegeris's case for control in four parts: what control is and how it sits beside alignment, with five deployment setups for you to judge; how a red team runs a control evaluation and why that makes control testable; whether the first transformatively useful AIs will already be too capable to control; and how long a window of controllable, useful AI might last.
:::

:::callout {title="Unit 2: Attack trees and the control game" tone="blue"}
You build an attack tree for a model trying to get a backdoor into production. Then the founding control paper: a capable model that might be sabotaging you, a weaker trusted one and a human who can check 2% of the work. You read its baselines and trusted monitoring, rebuild trusted monitoring's 62% safety with one line of algebra, and work out why the paper's red team was right to attack rarely.
:::

:::callout {title="Unit 3: Monitors you can't trust, and handing the work to AI" tone="blue"}
The rest of the founding paper: the monitor as a classifier and why its catch rate at the audit budget matters more than how well it ranks attacks overall (its AUC), deferring to the trusted model, untrusted monitoring and what stops a model lying about its own backdoors, trusted editing, and the difficulties the paper's toy setting left out. Then Josh Clymer on when it would be safer to hand safety research to AI agents than to keep humans in the loop.
:::

:::callout {title="Unit 4: Catching schemers and ranking threats" tone="blue"}
Why one clear catch of a model trying to escape tilts the game your way, and what it takes for that catch to convince the people who decide; you design one that would survive their objections. Then Ryan Greenblatt's ranking of the threats a misaligned AI poses, which you re-derive under a different level of political will, and Vivek Hebbar on diffuse threats such as research sabotage, where no single bad action proves anything.
:::

:::callout {title="Unit 5: Is control worth it?" tone="blue"}
Four criticisms of control, each of which you answer before you see the defenders' reply, and one of your own. Then Buck Shlegeris on trading safety against usefulness, a way to account for what control buys across different worlds, and Greenblatt's Plans A to D, which sort the possible worlds by how much political will there is. The unit closes with a long exercise: allocate ten researchers across seven research agendas in three scenarios, and see whether your allocation moves when the world does.
:::

\## What comes after

This is the first of our three AI Control courses. AI Control 2 assumes this course. It covers the control toolkit and where to invest in it, how a catastrophe happens in a high-stakes deployment, monitoring and resampling in real deployments, how control settings are built and how to design against collusion, and low-stakes failures and sandbagging. AI Control 3 assumes both earlier courses and covers capability elicitation and exploration hacking, research sabotage, reward seekers, and deals with misaligned AIs.

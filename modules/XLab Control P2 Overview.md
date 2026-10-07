---
id: 'ef0a13df-73af-4cf9-8bb3-9c93e22cf7a3'
slug: xlab-control-p2-overview
title: "Course Overview"
---
%% Orientation module before Unit 1 of AI Control 2. Added September 2026; rewritten October 2026 when XLab's AI Control track was re-cut from two courses into three five-unit courses (AI Control 1, 2, 3, strict XLab lens order). Unit summaries are written from the tldr, summary_for_tutor and openers of the lenses in each unit module; keep them in sync when a unit changes. Unit length: core lens time 172 to 223 minutes (U1 182, U2 172, U3 223, U4 181, U5 197; Unit 3 adds 25 optional); with the linked tests (as estimated in each unit module's note) 187 to 238 (U1 197, U2 187, U3 238, U4 208, U5 226); updated 2026-10-04 for raised lens tutor times and the learning outcomes now linked in Units 4 and 5. Learning-outcome tests: only the existing outcomes whose teaching now completes in this course are linked, per lo-placement.md Units 1 to 4 link 2, 2, 2 and 1 and Unit 5 none; on 2026-10-04 every unit, Unit 5 included, has linked tests, so the text now says each unit closes with tests. Learners see units, not days: the course also runs in less intensive formats. %%

# Lens: About This Course
id:: f9f9439d-b91b-4a98-a3eb-75d9b6e92ccb
tldr:: AI Control 1 made the case for control and ended by asking whether it is worth the cost. This second course is about doing it: the toolkit, how a catastrophe happens in a high-stakes deployment, monitoring and resampling at scale, building the test, and the quieter failures that only add up over time.
summary_for_tutor:: Orientation page before Unit 1 of AI Control 2, the second of three Lens Academy AI Control courses. The learner reads what the course is about, that it assumes AI Control 1, what the course teaches, how the units run (about three and a half hours of self-study each, some units up to about four, a group meeting at the end, short learning-outcome tests closing every unit), what each of the five units covers, and that AI Control 3 continues from here. Do not teach later content in detail; if asked, point to the unit that covers it, or say that capability elicitation, exploration hacking in depth, research sabotage benchmarks, reward seekers and deals with AIs belong to AI Control 3. If a learner has not done AI Control 1, say plainly that this course starts from its results (the case for control, the founding paper's protocols and vocabulary, untrusted monitoring, catching schemers, the threat ranking, concentrated versus diffuse failures, Plans A to D) and does not restate them, and point them to that course.
reading_minutes:: 5
tutor_minutes:: 0
#### Text
content::
\## What this course is about

AI Control 1 made the case for deploying a model that may be scheming while making sure it cannot cause a catastrophe, took apart the founding paper's protocols, and asked whether control is worth what it costs. This is AI Control 2, the second of our three AI Control courses, and it is about doing control in a real deployment. It surveys the toolkit and where Ryan Greenblatt thinks effort should go, follows how a catastrophe would actually happen in a high-stakes deployment and what monitoring and resampling can do about it, puts you in both seats of the collusion problem, and ends on failures that only matter in aggregate and models that quietly underperform. All three courses are built on the open-source [AI Control track](https://aisafetytracks.com/tracks/control) of [XLab](https://xrisk.uchicago.edu/), the Existential Risk Laboratory at the University of Chicago, and follow its order.

:::callout {title="This course continues another one" tone="blue"}
AI Control 1 is a prerequisite. This course picks up where it stopped and does not restate it: the case for control, the founding paper's protocols and vocabulary (trusted and untrusted models, monitoring, deferral, safety and usefulness), catching schemers, the ranking of threats, concentrated versus diffuse failures, and Plans A to D are assumed.
:::

\## What you will learn

By the end of this course you will be able to:

- Sort control measures into detection, prevention and response, and say where each one breaks.
- Explain how a control evaluation is run, and what a setting needs before its results can be trusted.
- Trace a control research agenda from a project starting now to less existential risk, and find its weakest link.
- Place a deployment on the high-stakes and low-stakes map, and describe each attack by its outcome (win, continue, lose) and each protocol decision as execute, replace or audit.
- Explain how a rogue deployment could start, including through an external API, and where it cuts into a lab's systems.
- Reason about monitoring at deployment scale and about how resampling turns a suspicious action into evidence.
- Attack an untrusted-monitoring protocol through collusion, design defences against it, and judge whether making a model explain its code helps a weak monitor.
- Say what changes when failures only matter in aggregate, and tell sandbagging from exploration hacking.

\## How the course runs

Five units. Each unit is about three and a half hours of reading and exercises on your own, some up to about four, and ends with a group meeting to work through the arguments the readings leave open. Each unit closes with short tests on what it taught. Unit 3 has one optional lesson for those who want to go further.

\## The five units

:::callout {title="Unit 1: The control toolkit and where to invest" tone="blue"}
The catalogue of control measures: detection (monitors on every action, probes on the model's internals, honeypots, paraphrasers), then prevention and response, from sandboxing to a shutdown process. How a control evaluation runs as a game between red, blue and green teams, and the five environments where such evaluations are run today. Ryan Greenblatt's eight areas of control work, from which you pick one and trace its theory of change. The unit closes with Aryan Bhatt's talk on high-stakes control: what labs have shipped and what will not get built by default.
:::

:::callout {title="Unit 2: High stakes: how a catastrophe happens" tone="blue"}
What "high stakes" means, as a region on a graph of how incriminating each action is against how many actions a catastrophe takes; you label that graph yourself. Then the three outcomes of an attack (win, continue, lose) and the three decisions of a protocol (execute, replace, audit); catastrophes that happen with every safety measure running versus those that begin by escaping them; a rogue deployment that runs through a company's own public API; and the three servers behind "the machine the agent runs on", and where an escape would cut in.
:::

:::callout {title="Unit 3: Monitoring and resampling in real deployments" tone="blue"}
Aryan Bhatt's talk on resampling, the idea behind the Ctrl-Z paper: when a command looks suspicious, ask the model again. Then a paper on what changes when monitoring runs at deployment scale: many instances in parallel, reviewers who answer late, attacks spread over many steps. The Ctrl-Z paper in two parts: asking the same model again instead of running a suspicious command or handing the task to a weaker model, how repeated suspicion becomes evidence, and what changes when the monitor is a copy of the model. Optional: Kaufman and Lucassen on monitors that block an action before it runs.
:::

:::callout {title="Unit 4: Building the test, and designing against collusion" tone="blue"}
Why building a control setting can be harder than developing the protocols and attacks tested in it: a short talk on attacks spread across several pull requests, and Buck Shlegeris on what a good setting needs. Then two guided readings where you write your answer before the authors give theirs. In the first you design untrusted monitoring and then take the red team's seat to find a monitor that passes validation and still lets real attacks through. In the second you predict whether making the untrusted model comment its code helps the weak monitor or the attacker more.
:::

:::callout {title="Unit 5: Low stakes: diffuse failures and sandbagging" tone="blue"}
Vivek Hebbar's talk on control when catching one bad action buys you almost nothing, then Ryan Greenblatt's notes on non-concentrated failures: what you can do with and without training the model online, a race between detection and damage, debate, and penalties that keep the model close to human behaviour. You place four failures on the concentrated-to-diffuse spectrum. The unit ends with the post that defines sandbagging and exploration hacking: a model that could do the task and quietly does not.
:::

\## What comes after

AI Control 3 assumes this course and AI Control 1. It starts from the sandbagging threat model this course ends on: stress-testing capability elicitation, a benchmark of sabotaged research codebases, a hands-on walkthrough of exploration hacking, then models that seek reward rather than scheme, deals with early misaligned AIs, and where to go next in control research.

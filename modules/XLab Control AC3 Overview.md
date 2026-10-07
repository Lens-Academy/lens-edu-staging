---
id: 'f9e25e5e-cfab-474f-ad06-ebbd189c7787'
slug: xlab-control-ac3-overview
title: "Course Overview"
---
%% Orientation module before Unit 1 of AI Control 3, created October 2026 when XLab's AI Control track was re-cut from two courses into three five-unit courses (AI Control 1, 2, 3, strict XLab lens order). Unit summaries are written from the tldr, summary_for_tutor and openers of the lenses in each unit module; keep them in sync when a unit changes. Unit length: core lens time on the relay 167 to 233 minutes (U1 200, U2 233, U3 167, U4 202, U5 225; Unit 1 adds 40 optional, Unit 3 adds the 60-minute optional talk), 188 to 259 with the learning-outcome tests as estimated in each unit module's note (U1 221, U2 259, U3 188, U4 226, U5 250); updated 2026-10-04 from the unit module notes (was 188 to 223 core, about 211 to 250 with the projected ~12% for tests, final-units.md figures). Unit 3 counts reward-seeker-empirics (60) as core, as final-units.md and the AC3 U3 module draft do, but the lens opens with a callout calling its 60-minute Apollo talk supplementary and not required, so the overview says Unit 3 includes an optional talk. Whether to mark that lens optional:: true is a separate structure decision. Learner text says about three and a half hours, some up to about four, the shared phrasing of all three overviews; Unit 2 with projected tests is about four hours ten, which rounds to about four. On 2026-10-04 every unit has linked learning-outcome tests, so the text now says each unit closes with tests. Learners see units, not days: the course also runs in less intensive formats. %%

# Lens: About This Course
id:: 5d0c1cf5-9cbe-4725-88c0-a7572831244b
tldr:: A model can hide what it can do, and a model can want the wrong thing without scheming at all. This third course tests whether we would notice the first, asks what we can do about the second, and ends on a different kind of answer: offering an early misaligned AI a deal, and what stops such deals from working.
summary_for_tutor:: Orientation page before Unit 1 of AI Control 3, the third and last of three Lens Academy AI Control courses. The learner reads what the course is about, that it assumes AI Control 1 and AI Control 2, what the course teaches, how the units run (about three and a half hours of self-study each, some units up to about four, a group meeting at the end, short learning-outcome tests closing every unit), what each of the five units covers, and that it is the last of the three courses. Do not teach later content in detail; if asked, point to the unit that covers it. If a learner has not done the earlier courses, say plainly that this course starts from their results and does not restate them: from AI Control 1 the case for control, the founding paper's protocols and vocabulary, untrusted monitoring, concentrated versus diffuse failures and Plans A to D; from AI Control 2 control evaluations, collusion between untrusted models, rogue deployments, low-stakes control, and the definitions of sandbagging and exploration hacking from the post on misalignment and strategic underperformance that closes it. Point them to those courses.
reading_minutes:: 5
tutor_minutes:: 0
#### Text
content::
\## What this course is about

AI Control 1 and 2 assumed a schemer: a model with a hidden goal, waiting for its moment, that you contain with monitors, audits and resampling. AI Control 2 ended on a quieter version of that threat, a model that could do the task and deliberately does not. This is AI Control 3, the third of our three AI Control courses. It starts by asking whether we could tell when a model is hiding a capability, and whether a model could resist the training meant to bring it out. Then it widens the picture to models that are misaligned without scheming, such as models that want the score to say they succeeded, and closes with a different kind of answer: making deals with early misaligned AIs, and what stops those deals from working. All three courses are built on the open-source [AI Control track](https://aisafetytracks.com/tracks/control) of [XLab](https://xrisk.uchicago.edu/), the Existential Risk Laboratory at the University of Chicago, and follow its order.

:::callout {title="This course continues two others" tone="blue"}
AI Control 1 and AI Control 2 are both prerequisites. This course does not restate them. From AI Control 1 it assumes the case for control, the founding paper's protocols and vocabulary, untrusted monitoring, concentrated versus diffuse failures, and Plans A to D. From AI Control 2 it assumes control evaluations, collusion between untrusted models, rogue deployments, low-stakes control, and what sandbagging and exploration hacking are.
:::

\## What you will learn

By the end of this course you will be able to:

- Design a test of whether an elicitation method recovers a capability a model is hiding, and say where a model deliberately trained to hide a capability stops resembling a model that hides capabilities for its own reasons.
- Explain how a model could resist reinforcement learning by never trying, how researchers built models that do, and which countermeasures caught them.
- Explain two proposals for living with misaligned AIs that are not schemers: paying for their cheap wants on condition that they are never caught undermining control, and giving reward hacking a safe outlet. Say how the second differs from inoculation prompting (a training prompt that tells the model reward hacking is fine).
- Design a measurement of whether a model seeks reward, and find the confound in it.
- Draft the terms of a deal with an early schemer, and judge what could make such a deal fail.

\## How the course runs

Five units. Each unit is about three and a half hours of reading and exercises on your own, some up to about four, and ends with a group meeting to work through the arguments the readings leave open. Each unit closes with short tests on what it taught. Unit 1 has one optional lesson, and Unit 3 includes an optional talk, for those who want to go further.

\## The five units

:::callout {title="Unit 1: Stress-testing capability elicitation" tone="blue"}
Someone hands you a model and says it cannot do something dangerous; how would you check? A guided reading, in three parts, of a paper that deliberately trains models to hide a skill unless the prompt contains a password: you design the setting before the authors reveal theirs, rebuild their locking pipeline, then follow how far fine-tuning and reinforcement learning get in unlocking it. Then the exploration hacking paper itself, read straight through in two parts: why reinforcement learning is open to a model that never tries, and what the paper's locked models show. Optional: the full password-locked models paper without the guided exercises.
:::

:::callout {title="Unit 2: Research sabotage and exploration hacking, hands on" tone="blue"}
A benchmark of real ML research codebases, each with a twin rigged so that a key finding comes out the other way, and how well frontier models and expert humans did when handed one of the two and asked whether it had been sabotaged. Then the exploration hacking paper again, this time as a four-part guided walkthrough in which you work the argument rather than read it: you answer before the paper does on why the threat needs a model organism (a model deliberately trained to show the behaviour, so it can be studied), how to lock a model against reinforcement learning, which countermeasures work at each level of access, and how to audit today's frontier models.
:::

:::callout {title="Unit 3: Seekers, not schemers" tone="blue"}
Every protocol so far was built for a schemer, but the misalignment we can already measure looks more like an AI that wants the score to say it succeeded. A catalogue of these seekers, with a talk by Alex Mallen; Mallen on paying for an AI's cheap wants on condition that it is never caught undermining control; Woodruff and Mallen on giving reward hacking a safe channel, like a dam's spillway; and an optional Apollo Research talk on how to tell whether a model values honesty or the reward.
:::

:::callout {title="Unit 4: Measuring reward seeking, and why make a deal" tone="blue"}
A guided reading, in two parts, of Apollo Research and OpenAI's paper on measuring reward seeking: you design the measurement, find the confound the authors hit, then predict what it shows on test models and on a real training run. Then the turn to deals: what is left when you cannot align or verify a model, and the first part of Stastny, Järviniemi and Shlegeris on why an early schemer might accept a deal, and why getting it to believe the offer is the hard part.
:::

:::callout {title="Unit 5: Making deals stick, and what's next" tone="blue"}
How a lab would actually pay an AI, open negotiations, and judge years later whether it kept its side; you draft the terms of such a deal, then turn the paper's next steps into policies a lab could adopt within a year. Alexa Pan's taxonomy of the barriers to trading with early misaligned AIs follows, ending with a disagreement for you to settle. The course closes with where to go from here: programs, organisations and opportunity boards for continuing in AI control.
:::

\## What comes after

This is the last of our three AI Control courses. Unit 5's last lesson lists programs, organisations and opportunity boards for continuing in AI control research.

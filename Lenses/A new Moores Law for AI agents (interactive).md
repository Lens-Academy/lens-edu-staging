---
id: '6eac934e-8ae8-4051-95d3-08b38ec19a77'
title: "A new Moore's Law for AI agents"
reading_minutes: 6
tutor_minutes: 5
tldr: "AI agents can now finish coding tasks that take a person a full working day or more, and that length keeps doubling. Play with METR's data yourself and see where the line points."
summary_for_tutor: "Interactive companion to the AI Digest piece 'A new Moore's Law for AI agents'. A short Text introduces METR's time horizon (the length of task, in human professional time, an agent completes 50% of the time; about 230 mostly coding tasks), notes that ChatGPT managed about 30-second coding tasks in 2022 and agents managed over fourteen-hour tasks by March 2026, and tells the learner that the squares in the widget's 80% view are fictional AI 2027 agents that a button hides. The METR time-horizons widget follows (50%/80% views, confidence intervals, trend fits with doubling times; METR publishes 188 days all-time and 129 days from 2023 on). A second Text gives AI Digest's reading: doubling about every 7 months over 2019 to 2025 and every 4 months in 2024 to 2025 (the chart uses METR's newer data, so its numbers differ a little), extrapolation to a work day in 2027, a work week in 2028 and a work month in 2029, or a work month in 2027 at the faster rate, and the caveat that one year of data is thin and the trend could slow or speed up, e.g. through AI-automated AI research. Then an ungraded open question asks what agents could do in three years if the doubling holds and what would show a slowdown, followed by an open chat."
tags: [wip]
---
#### Text
content::
When ChatGPT came out in 2022, it could do coding tasks that take a person about 30 seconds. By March 2026, AI agents could do coding tasks that take a person over fourteen hours.

[METR](https://metr.org/) measured this by giving agents about 230 tasks, mostly coding, and timing how long each takes a human professional. An agent's **time horizon** is the length of task it completes half the time.

The chart plots that for each model by release date. Try both trend fits. The squares in the 80% view are fictional agents from the AI 2027 scenario, not measurements. The "AI 2027 agents" button hides them.

#### Widget
source:: [[../widgets/ai-2027-metr-horizons]]

#### Text
content::
The time axis is logarithmic, so a straight line means steady doubling.

From 2019 to 2025 the time horizon doubled about every 7 months. In 2024 and 2025 it doubled about every 4. The chart uses METR's newer data, so its numbers differ a little.

At the slower rate, agents reach a work day in 2027, a work week in 2028 and a work month in 2029. At the faster rate, a work month could come in 2027.

One year of data is thin evidence. The trend could slow down. It could also speed up, for example if agents take over part of the work of building better agents.

Based on AI Digest's [A new Moore's Law for AI agents](https://theaidigest.org/time-horizons) and METR's data.

#### Question: Open
id:: 7edb4c55-7570-4595-a1b3-8bbf5f9a45a3
content:: If the doubling holds, what could an agent do three years from now that it cannot do today? What would you need to see in this chart to believe it is slowing down?
force-feedback:: first
feedback-instructions:: The learner has just explored METR's time-horizon chart and read that the horizon doubled about every 7 months (2019 to 2025) and about every 4 months (2024 to 2025). Name the most concrete part of their prediction and check that it follows from the doubling (three years is roughly 5 to 9 doublings). Then tell them whether their slowdown signal could actually be seen in this chart, and how long it would take to tell a real slowdown from a noisy point. Three to five sentences. No generic praise. If they do not understand, give one concrete foothold from the chart or text, such as what a work week of tasks means for a coding agent.

#### Chat
instructions::
TLDR of what the user just did:
They explored METR's time-horizon chart (the length of task, in human time, that frontier agents complete at 50% or 80% reliability, plotted by release date, with trend fits and doubling times) and read AI Digest's summary: doubling about every 7 months from 2019 to 2025, recently about every 4 months; straight-line extrapolation reaches day-long tasks in 2027 and month-long tasks by 2029, and AI-automated AI research could push the curve superexponential. The 80% view can show fictional AI 2027 agents; those are scenario placements, not measurements. They then answered: if the doubling holds, what could agents do in three years, and what would show a slowdown?

Discussion topics to explore:
- This is the feedback loop from earlier in the module, now with a number on it. What is the "reinvested output" that could make time horizons grow faster than exponentially?
- How much should one year of acceleration (7 to 4 months) update you, given how noisy one year of data is? Compare the "all points" and "from 2023 on" fits in the chart.
- What would a genuine plateau look like in this data, and how long would you have to wait to tell it apart from a temporary dip? Look at how wide the intervals get above a few hours.
- The headline number is at 50% reliability. How does the 80% view change what "agents can do month-long tasks" means?

Ask what they found surprising. Check if they can explain "time horizon" in their own words; it is the key concept.

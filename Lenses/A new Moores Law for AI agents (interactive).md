---
id: '6eac934e-8ae8-4051-95d3-08b38ec19a77'
title: "A new Moore's Law for AI agents"
reading_minutes: 7
tutor_minutes: 5
tldr: "When ChatGPT came out in 2022, it could do 30 second coding tasks. Today, AI agents can autonomously do coding tasks that take humans over fourteen hours. Step through AI Digest's charts of METR's data and see where the trend points."
summary_for_tutor: "AI Digest's scrolling explainer 'A new Moore's Law for AI agents' (theaidigest.org/time-horizons, CC-BY), shown as the whole imported article with its graphs inside it, each graph before the text that goes with it. The graphs are four widgets rebuilt from AI Digest's chart with its own METR Time Horizon 1.1 data and fit constants (linear y axis, 17 models from GPT-2 in 2019 to Claude Opus 4.6 in Feb 2026; 50% time horizon = the task length, in human time, an agent completes half the time). Sequence: (1) the measured points with a 7-month-doubling trend and band and a '2x / 7 months' doubling staircase, with the intro (30-second tasks in 2022, over fourteen hours today), 'doubling every 7 months' and METR's method (about 230 mostly coding tasks, R^2 = 0.83, definition of time horizon); (3) extrapolation to 2030, with 'What comes next?' (1 work day 2027, 1 work week 2028, 1 work month 2029); (4) a red trend from 2024 doubling every 4 months, with 'Recently, the trend has accelerated'; (5) both trends projected to 2030, with the rest of the article: month-long tasks in 2027 if the faster trend holds, one year of data is thin, the trend could slow or turn superexponential as AIs speed up AI research, possibly one of the most important trends in human history. Then an ungraded open question (what could agents do in three years, what would show a slowdown) and an open chat."
tags: [wip]
---
#### Article
source:: [[../articles/digest-a-new-moores-law-for-ai-agents-ai-digest]]

#### Question: Open
id:: 7edb4c55-7570-4595-a1b3-8bbf5f9a45a3
content:: If the doubling holds, what could an agent do three years from now that it cannot do today? What would you need to see in these charts to believe it is slowing down?
force-feedback:: first
feedback-instructions:: The learner has just stepped through AI Digest's time-horizon charts: METR's measured 50% time horizons with a trend doubling about every 7 months (2019 to 2025), an extrapolation to a work day in 2027, a work week in 2028 and a work month in 2029, and a faster trend from 2024 doubling about every 4 months that would reach month-long tasks in 2027. Name the most concrete part of their prediction and check that it follows from the doubling (three years is roughly 5 to 9 doublings). Then tell them whether their slowdown signal could actually be seen in data like this, and how long it would take to tell a real slowdown from one noisy point. Three to five sentences. No generic praise. If they do not understand, give one concrete foothold from the charts or text, such as what a work week of tasks means for a coding agent.

#### Chat
instructions::
TLDR of what the user just did:
They stepped through AI Digest's explainer "A new Moore's Law for AI agents" as five charts of METR's data, each followed by its part of the text. METR measured the length of tasks (in human time) that frontier AI agents complete 50% of the time, their "time horizon": 30-second coding tasks for ChatGPT in 2022, over fourteen hours for today's agents, doubling about every 7 months over 2019 to 2025 and about every 4 months in 2024 to 2025. Task length correlates strongly with success rate (R^2 = 0.83). Extrapolating the 7-month trend gives a work day in 2027, a work week in 2028 and a work month in 2029; the 4-month trend gives month-long tasks in 2027. The charts use a linear axis, so everything before 2024 looks flat. The text notes that one year of data is thin, and that AI speeding up AI research could make growth faster than exponential. They then answered: if the doubling holds, what could agents do in three years, and what would show a slowdown?

Discussion topics to explore:
- This is the feedback loop from earlier in the module, now with a number on it. What is the "reinvested output" that could make time horizons grow faster than exponentially?
- How much should one year of acceleration (7 to 4 months) update you, given how noisy one year of data is? Look at how wide the confidence interval on the newest model is in the first chart.
- Why does a linear axis make the curve look like it only took off in 2024? What would the same data look like on a log axis?
- What would a genuine plateau look like in this data, and how long would you have to wait to tell it apart from a temporary dip?
- The time horizon is measured at 50% reliability. How does that caveat change what "agents can do month-long tasks" actually means?

Ask what they found surprising. Check if they can explain "time horizon" in their own words; it is the key concept.

{++{"author":"Lauren's AI","timestamp":1786128799503}@@---
id: '71ffbbb9-86a2-4b06-855f-729097642dc0'
title: What a Curve Licenses
tldr: A colleague shows you a perfect exponential and a fourteen-month forecast. Every fact is true. Your job is to find where the argument outruns the chart.
summary_for_tutor: "Closes the module's wedge thread. The student is handed a plausible, correctly-reasoned extrapolation in which every stated fact is true, and must locate the exact step where the argument spends evidence it does not have. Deliberately set inside AI (a coding benchmark) because it is the practice beat; the graded transfer test for this module is set outside AI. Four load-bearing moves, any two of which pass: fit quality is silent about the unobserved range; a score near its ceiling is a different regime; construct stability; and confidence about continuation should come from an outside view on trend breaks, which the student got in lens 2. A student who says the colleague is lying has misread the setup."
tags:
  - wip
authors:
  - Lauren+Claude
---
#### Text
content::
\## Where an argument outruns its chart

You now have a probe of what compute buys and a base rate for cliffs. Last beat of this module: what a measured trend does and does not license you to conclude. You will be handed an argument in which every stated fact is true. Your job is not to find the lie; there isn't one. Your job is to find the exact step where the argument starts spending evidence it doesn't have.

#### Question
content::
\## The wedge

A colleague shows you a chart and an argument.

"Here is our model's score on a coding benchmark, measured every quarter for three years. It is a clean exponential, R-squared 0.97, and it held across two complete architecture changes, so it is clearly not an artifact of any one approach. The benchmark tops out at 100. We are at 61. At this rate we saturate it in fourteen months. So: fourteen months until this benchmark is solved, and I am confident because the fit is excellent."

Every factual claim your colleague makes is true. The fit really is 0.97, it really did survive two architecture changes, and the arithmetic is right.

Where does the argument stop being licensed by the data? And what would you have to know, that is not on the chart, before the fourteen-month figure meant anything?

assessment-instructions:: The student has completed lens 1 (what compute buys) and lens 2 (base rates for discontinuities). Those are the tools this wedge wants.

This is a deliberate wedge, not the test question. It hands the student a plausible-sounding but flawed extrapolation in which every stated fact is true, and asks them to locate where the license runs out.

Four load-bearing moves. ANY TWO of them pass:
1. Fit quality is silent about the unobserved range. R-squared 0.97 licenses interpolation inside the measured range, not a claim about the next fourteen months.
2. A score approaching its ceiling is a different regime. The benchmark tops out at 100 by construction, so the remaining 39 points are not interchangeable with the last 39.
3. Construct stability: whether the quantity being measured at 61 is the same skill it will be at 95. Saturating a benchmark and solving the underlying capability are different claims, and only the first is on the chart.
4. Confidence about continuation should come from an outside view on how often strong regular trends break, which the student has from lens 2, rather than from the quality of the fit.

Reward a student who connects to lens 2 unprompted, for example "one large discontinuity per thousand trend-years, but this could be the affected kind".

Note for the grader: move 2 as stated is our expectation, not a measured fact about this fictional benchmark. A strong student may argue that the residual items are not harder, and if they argue it well that is a pass, not an error.

Failure modes and how to handle them:
- A student who says the colleague is lying has missed the setup. Re-anchor on "every claim is true" and ask again.
- Do NOT accept "we can't know anything". The wedge asks what WOULD license the figure; listing that is the pass.

Conversation flow: 3 tutor replies, then ask whether they want to continue or stop. Keep an internal turn counter. If they continue, reset and proceed.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise (great point, exactly right, excellent answer).
- If the answer is vague, ask for precision. If it is confused, say so plainly and correct it.

What to do in each reply:
1. If the student asks a direct question, answer it.
2. Otherwise restate their answer in more precise form in 2 to 4 sentences, without adding ideas they did not express.
3. Name 1 to 3 gaps or hidden assumptions plainly.
4. Ask 2 follow-up questions that require causal reasoning, each directly answerable.

If the student is stuck after 2 attempts, give a brief direct answer and move on.

On close: name what they demonstrated, name what is still underdeveloped, and give an explicit test-readiness verdict.
++}
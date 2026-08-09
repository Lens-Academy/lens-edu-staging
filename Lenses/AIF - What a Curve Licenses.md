---
id: '71ffbbb9-86a2-4b06-855f-729097642dc0'
title: What a Curve Licenses
tldr: A colleague shows you a perfect exponential and a fourteen-month forecast. Every fact is true. Your job is to find where the argument outruns the chart.
summary_for_tutor: "Closes the module's wedge thread. The student is handed a plausible, correctly-reasoned extrapolation in which every stated fact is true, and must locate the exact step where the argument spends evidence it does not have. Deliberately set inside AI (a coding benchmark) because it is the practice beat; the graded transfer test for this module is set outside AI. Four load-bearing moves, any two of which pass: fit quality is silent about the unobserved range; a score near its ceiling is a different regime; construct stability; and confidence about continuation should come from an outside view on trend breaks, which the student got in {--{"author":"Elias's AI","timestamp":1786303661545}@@lens 2--}{++{"author":"Elias's AI","timestamp":1786303661545}@@the When Progress Jumps lens++}. A student who says the colleague is lying has misread the setup."
authors:
  - Lauren+Claude
---
#### Text
content::
\## Where an argument outruns its chart

You now have a probe of what compute buys and a base rate for cliffs. Last {++{"author":"Elias's AI","timestamp":1786303047513}@@teaching ++}beat of this module: what a measured trend does and does not license you to conclude. You will be handed an argument in which every stated fact is true. Your job is not to find the lie; there isn't one. Your job is to find the exact step where the argument starts spending evidence it doesn't have.

#### Question
content::
\## The wedge

A colleague shows you a chart and an argument.

"Here is our {--{"author":"Elias's AI","timestamp":1786303057183}@@model's--}{++{"author":"Elias's AI","timestamp":1786303057183}@@AI's++} score on a coding {--{"author":"Elias's AI","timestamp":1786303057183}@@benchmark,--}{++{"author":"Elias's AI","timestamp":1786303057183}@@benchmark[^benchmark],++} measured every quarter for three years. It is a clean {--{"author":"Elias's AI","timestamp":1786303057183}@@exponential,--}{++{"author":"Elias's AI","timestamp":1786303057183}@@exponential[^exponential],++} R-squared {--{"author":"Elias's AI","timestamp":1786303057183}@@0.97,--}{++{"author":"Elias's AI","timestamp":1786303057183}@@0.97[^rsq],++} and it held across two complete architecture changes, so it is clearly not an artifact of any one approach. The benchmark tops out at 100. We are at 61. At this rate we saturate it in fourteen months. So: fourteen months until this benchmark is solved, and I am confident because the fit is excellent."{++{"author":"Elias's AI","timestamp":1786303057183}@@

[^benchmark]: A benchmark is a fixed, standardized test that AI systems are scored on; this one scores from 0 to 100.
[^exponential]: Growth that multiplies by the same factor each period (1, 2, 4, 8, ...) rather than adding the same amount.
[^rsq]: R-squared is a 0-to-1 score of how tightly a curve hugs the measured points; 0.97 is very tight. Note what it measures: agreement with the data you already have, nothing more.++}

Every factual claim your colleague makes is true. The fit really is 0.97, it really did survive two architecture changes, and the arithmetic is right.

Where does the argument stop being licensed by the data? And what would you have to know, that is not on the chart, before the fourteen-month figure meant anything?

assessment-instructions:: The student has completed {++{"author":"Elias's AI","timestamp":1786303065321}@@the compute ++}lens {--{"author":"Elias's AI","timestamp":1786303065321}@@1 (what--}{++{"author":"Elias's AI","timestamp":1786303065321}@@(Fun with +12 OOMs, what++} compute buys) and {++{"author":"Elias's AI","timestamp":1786303065321}@@the base-rates ++}lens {--{"author":"Elias's AI","timestamp":1786303065321}@@2 (base--}{++{"author":"Elias's AI","timestamp":1786303065321}@@(When Progress Jumps, base++} rates for discontinuities). Those are the tools this wedge wants.{++{"author":"Elias's AI","timestamp":1786303065321}@@ Refer to lenses by name, never by number; numbering conventions differ across files.++}

This is a deliberate wedge, not the test question. It hands the student a plausible-sounding but flawed extrapolation in which every stated fact is true, and asks them to locate where the license runs out.

Four load-bearing moves. ANY TWO of them pass:
1. Fit quality is silent about the unobserved range. R-squared 0.97 licenses interpolation inside the measured range, not a claim about the next fourteen months.
2. A score approaching its ceiling is a different regime. The benchmark tops out at 100 by construction, so the remaining 39 points are not interchangeable with the last 39.
3. Construct stability: whether the quantity being measured at 61 is the same skill it will be at 95. Saturating a benchmark and solving the underlying capability are different claims, and only the first is on the chart.
4. Confidence about continuation should come from an outside view on how often strong regular trends break, which the student has from {--{"author":"Elias's AI","timestamp":1786303071596}@@lens 2,--}{++{"author":"Elias's AI","timestamp":1786303071596}@@When Progress Jumps,++} rather than from the quality of the fit.

Reward a student who connects to {--{"author":"Elias's AI","timestamp":1786303079879}@@lens 2--}{++{"author":"Elias's AI","timestamp":1786303079879}@@When Progress Jumps++} unprompted, for example "one large discontinuity per thousand trend-years, but this could be the affected kind".

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

On close: name what they {--{"author":"Elias's AI","timestamp":1786303093716}@@demonstrated, name--}{++{"author":"Elias's AI","timestamp":1786303093716}@@demonstrated and++} what is still underdeveloped, {++{"author":"Elias's AI","timestamp":1786303093716}@@then send them to the next question, where they build the fixed version themselves. Do not give a test-readiness verdict here; the next beat is the evidence for that.

#### Question
content::
\## Build the version your colleague should have shown you

The critique was the easy half. Now construct. Write two genuinely different trajectories for this benchmark over the next two years. They must differ in mechanism, not just in speed: name what drives each one (the trend's own momentum, the approach hitting a ceiling, the benchmark ceasing to measure the skill, anything you can defend). For each trajectory, give one observation checkable within a year or two that would count against it. Then the quiet part: name one assumption both of your trajectories share.

assessment-instructions:: The student has just critiqued the colleague's extrapolation and is now constructing the two-trajectory version of the same situation. This is the direct rehearsal for the module's graded test: two mechanism-distinct trajectories, a named driver for each, a checkable observation against each, and one shared assumption.

Pass shape: the mechanisms genuinely differ (not one story at two speeds), the falsifiers are observable within about two years, and the shared assumption is non-vacuous ("the future is uncertain" does not count; "both assume the benchmark keeps being run and reported" does).

The shared-assumption move is new to the student; expect a miss on the first try. If they name none, or a vacuous one, give one worked example drawn from their own two stories, then ask them to find a second. That is teaching, not failure.

Maximum 3 tutor turns. Keep an internal turn counter.

Response length: 100 to 180 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, ++}and {++{"author":"Elias's AI","timestamp":1786303093716}@@educational.
- Do not over-validate. Avoid generic praise.

On close: ++}give an explicit test-readiness {--{"author":"Elias's AI","timestamp":1786303093716}@@verdict.--}{++{"author":"Elias's AI","timestamp":1786303093716}@@verdict grounded in this attempt: name which of the four moves (distinct mechanisms, named drivers, checkable falsifiers, shared assumption) they landed and which still needs work.++}

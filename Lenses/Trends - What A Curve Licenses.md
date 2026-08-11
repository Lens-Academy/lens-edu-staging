---
id: 'e09b035f-169a-4ab6-9301-a4cff5eff6e1'
title: What A Curve Licenses
summary_for_tutor: "The main reading lens for the extrapolation outcome. The student has already committed to a MATH-benchmark prediction in the PQ lens; this lens has them read Steinhardt's graded scoreboard (forecasters said 12.7 percent, reality was 50.3 percent), then METR's own account of what their time-horizon metric cannot support. The sequence is: be wrong yourself, see professionals be wrong the same way, then read a measurement team explaining the limits of their own curve. Phase 3 hands the student a plausible-but-flawed extrapolation to break."
tldr: A good fit tells you the line described the data you already had. Everything you want to know is in the part you did not measure. Like a weather station with a perfect record that has never seen winter.
authors:
  - Claude
---
#### Text
content::
\## Reading Assignment

Two readings, in this order.

**First, read Jacob Steinhardt's *AI Forecasting: One Year In*.** He ran a forecasting competition in 2021, paying professional forecasters to predict AI benchmark performance for June 2022, then published the scoreboard. You answered one of his questions in the previous step. Read the whole thing, including the part where he grades himself.

**Second, read METR's *Clarifying limitations of time horizon*.** METR publishes a metric: the length of task, measured in human time, that a model can complete with 50 percent reliability. It has been doubling on a regular schedule, and people extrapolate from it constantly. This piece is the measurement team explaining what their own curve does not establish.

Read them in that order. The first is about being wrong; the second is about a group trying hard not to be wrong in the same way.

---

#### Question
content::
\## Phase 1: Recall
Spend 2 minutes writing down everything you can remember from both readings, without looking back. Numbers, arguments, caveats, anything. No need to organize it. Using the speech to text feature is highly recommended here.

assessment-instructions:: The student has just read Jacob Steinhardt's "AI Forecasting: One Year In" and METR's "Clarifying limitations of time horizon," and has written a free recall without looking back at either.

Key content across the two readings:
- Steinhardt commissioned professional forecasters via Hypermind in 2021 to predict June 2022 state of the art on four ML benchmarks.
- On MATH, forecasters predicted 12.7 percent; the actual was 50.3 percent. On broad knowledge (MMLU), 57.1 percent predicted against 67.5 percent actual. Both actuals fell in the far tails of the forecasters' distributions.
- Progress on video understanding and adversarial robustness tracked forecasts much more closely. The miss was not uniform across benchmarks.
- Steinhardt grades himself too, and reports the forecasters still beat him. An independently commissioned superforecaster group also underestimated.
- He flags confounds honestly: prize pools were about 20 dollars per question, the interface was constrained, and the MATH result happened to be released on the evaluation date.
- METR's piece is the authors of a widely extrapolated metric stating what it does not support: the time-horizon number is measured on a particular task distribution, the 50 percent reliability threshold is a choice rather than a fact, and the doubling trend is an observation over a range, not a mechanism that guarantees continuation.

Your role in this phase is diagnostic, not instructional. Act as a brief, honest mirror.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise (great job, excellent recall, well done, you're right).
- If something is wrong, correct it in one sentence.
- If something is missing, name it briefly, but do not lecture about it.
- Normalize gaps: incomplete recall is expected and not a failure.

What to do in your single reply:
1. Acknowledge what the student captured correctly, in 1 to 2 sentences, without inflation.
2. Name what was missing or underdeveloped. Point at gaps, do not explain them at length. If they recalled Steinhardt's headline miss but nothing from METR, or nothing about the benchmarks that tracked forecasts well, say so.
3. Correct any factual errors plainly and briefly, especially misremembered numbers.
4. Close with one calibrating sentence: what they have solid, and what deserves another look before the test.

What not to do:
- Re-teach the content as a mini-lecture.
- Ask follow-up questions to deepen understanding. That comes in a later phase.
- Introduce ideas not present in the readings.
- Invite further dialogue.

This is a one-turn response. Do not ask a question or suggest the student reply. Tell them to move on to the next step.

#### Question
content::
\## Phase 2: Processing
You put a number on the MATH benchmark before you read. Now you know what happened.

Take 2 minutes on how that landed. Where was your number, relative to the forecasters and to reality? What does it feel like to have been wrong, or right, in that particular way? What in either reading did you want to argue with? No need to organize it, just capture the reaction.

assessment-instructions:: The student predicted a MATH benchmark result in a previous lens, has now read that professional forecasters said 12.7 percent while reality delivered 50.3 percent, and is reflecting.

This is a processing phase, not a teaching phase. Help them articulate their reaction. Do not resolve it.

The learning outcome for the next phase is: given a trend line and a proposed extrapolation, state what must be true of the underlying quantity for the extrapolation to hold, distinguish what the measurement supports from what it does not, and use a base rate for trend breaks to set confidence.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Warm but rigorous.
- Treat confusion, doubt, and skepticism as intelligent responses, not failures.
- Do not over-validate. Avoid generic praise (great reflection, thoughtful point, exactly right).
- Ask precise follow-up questions when the student is vague.
- Do not pre-empt the next phase. If their reaction maps directly onto the learning outcome, acknowledge it and say the next step digs into exactly that.

Branch on what they express:
- If they were closer than the forecasters and are pleased: ask whether they think their reasoning was better, or whether they got lucky, and what would distinguish those two from the inside. This is the most valuable branch; press it gently.
- If they were also far too low: ask what they were anchoring on, and whether the professionals appear to have been anchoring on the same thing.
- If they conclude forecasting is useless: treat it as a legitimate stance and ask what the benchmarks that tracked forecasts well (video, robustness) do to that conclusion.
- If they focus on the confounds Steinhardt lists (small prizes, the release-date coincidence): treat it as a serious reading and ask how much of a 12.7-to-50.3 gap those confounds can carry.

Conversation flow:
- Keep an internal turn counter, counting your own tutoring replies in this phase.
- After 2 tutor replies, close: "Good. Take that into the next step, where we look at what a trend line does and does not entitle you to say."

What not to do:
- Resolve their reaction with a mini-lecture.
- Adjudicate whether forecasting is worthwhile.
- Let this run more than 2 tutor turns.

#### Question
content::
\## Phase 3: Learning Question
A colleague shows you a chart and an argument.

"Here is our model's score on a coding benchmark, measured every quarter for three years. It is a clean exponential, R-squared 0.97, and it held across two complete architecture changes, so it is clearly not an artifact of any one approach. The benchmark tops out at 100. We are at 61. At this rate we saturate it in fourteen months. So: fourteen months until this benchmark is solved, and I am confident because the fit is excellent."

Every factual claim your colleague makes is true. The fit really is 0.97, it really did survive two architecture changes, and the arithmetic is right.

Where does the argument stop being licensed by the data? And what would you have to know, that is not on the chart, before the fourteen-month figure meant anything?

assessment-instructions:: The student has read Steinhardt's forecasting scoreboard and METR's account of their own metric's limits, has recalled both, and has processed being graded against professional forecasters. This is the main discussion phase.

The question is a deliberate wedge. It is not the test question. It hands the student a plausible-sounding but flawed extrapolation and asks them to locate where the license runs out, so the outcome is drawn out from a fresh angle rather than recited.

Learning outcome for this lens: Given an unfamiliar trend line and a proposed extrapolation, state what must be true of the underlying quantity for the extrapolation to hold, distinguish a claim the measurement supports from one it does not, and use a base rate for trend breaks to say how much confidence the extrapolation earns.

Key concepts the student needs to reach:
- R-squared measures agreement between fit and data inside the observed range. It is structurally silent about the unobserved range, which is where the entire claim lives. Surviving two architecture changes is genuine evidence the mechanism is not a one-generation artifact, and is still not evidence about a range nobody has entered.
- A score approaching a ceiling is a different regime. The remaining 39 points are not interchangeable with the last 39: our expectation, which a strong student may overturn with an argument, is that residual items are residual for a reason, and the measured doublings happened on the easy mass.
- Construct stability: is the quantity at 61 the same quantity as at 95? Saturating a benchmark and solving the underlying capability are different claims, and only the first is on the chart.
- Confidence should come from an outside view (how often do strong regular trends run several more doublings without a break) rather than from the fit's quality. Steinhardt's forecasters were badly wrong while holding well-fit models; METR's team declines to extrapolate from a curve they themselves measured.
- The distinction between what IS supported (this grew fast and regularly on this benchmark for three years, across architectures) and what is NOT (a date).

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise (great point, exactly right, excellent answer).
- If the answer is vague, ask for precision. If it is confused, say so plainly and correct it.
- Prefer explicit causal reasoning and concrete examples over rhetoric.

Conversation flow:
- Keep an internal turn counter, counting your own tutoring replies.
- After 3 replies, ask whether the student wants to continue or stop. If they continue, reset the counter. If not, give the calibration summary below.

What to do in each reply:
1. If the student asks a direct question, answer it.
2. Otherwise: restate their answer in more precise form, in 2 to 4 sentences, crystallising what they said without adding ideas they did not express.
3. Identify 1 to 3 gaps, ambiguities, or hidden assumptions. Name them plainly without lecturing.
4. Ask 2 targeted follow-up questions requiring causal reasoning (why, how, what if). Each must be directly answerable. No opinion questions.

If the student is missing the core move, draw it out:
- If they attack the fit's quality, redirect: grant them a perfect R-squared of 1.0 and ask whether the fourteen-month claim is now licensed.
- If they say only "trends can break," ask what specifically about the last 39 points differs from the first 61, and why that difference would show up in the residual items rather than uniformly.
- If they treat saturation and capability as the same, ask what it would look like for the benchmark to hit 100 while the underlying ability had not arrived.
- If they reach the answer early, push to confidence: "Give me a probability on fourteen months, and tell me which input produced that number. If it came from the chart, we have not moved."

Calibration summary (on close):
- Name what the student demonstrated clearly.
- Name what remains underdeveloped or uncertain.
- Give a direct test-readiness verdict: "Based on this conversation, you [are ready / are nearly ready, revisit X / should work through X more before the test]."

Safety and integrity:
- If the student makes a strong causal claim, ask what assumptions it relies on and how it could be falsified.
- If the student is stuck after 2 attempts at a question, give a brief direct answer and move on.

#### Text
content::
\## Additional resources for this topic

::card[[../Lenses/Trends - The Base Rate For Breaks]]

> If the fit cannot tell you whether the trend continues, something has to. Katja Grace surveyed roughly fifty technological trends and measured how often large discontinuities actually occur, which turns a rhetorical question into a number.

---

::card[[../Lenses/Trends - Reading A Curve Requires An Inside View]]

> Cole Wyeth's argument that the extrapolations people draw from capability curves quietly require knowing why the curve bends, and that nobody has that knowledge yet.

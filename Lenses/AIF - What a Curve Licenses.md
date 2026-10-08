---
id: '71ffbbb9-86a2-4b06-855f-729097642dc0'
reading_minutes: 5
tutor_minutes: 20
title: What a Curve Licenses
tldr: A colleague shows you a perfect exponential and a fourteen-month forecast. Every fact is true. Your job is to find where the argument outruns the evidence.
summary_for_tutor: "Closes the module's wedge thread. The student is handed a plausible, correctly-reasoned extrapolation in which every stated fact is true, and must locate the exact step where the argument spends evidence it does not have. Deliberately set inside AI (a coding benchmark) because it is the practice beat; the graded transfer test for this module is set outside AI. Four load-bearing moves, any two of which pass: fit quality is silent about the unobserved range; a score near its ceiling is a different regime; construct stability; and confidence about continuation should come from an outside view on trend breaks. No reading before this page teaches base rates for trend breaks, so treat that move as one the student may or may not bring. A student who says the colleague is lying has misread the setup."
authors:
  - Lauren+Claude
---
#### Text
content::
\## Where an argument outruns its evidence

You now have a probe of what compute buys. Now: what a measured trend does and does not license you to conclude. You will be handed an argument in which every stated fact is true. Your job is not to find the lie; there isn't one. Your job is to find the exact step where the argument starts spending evidence it doesn't have.
{>>{"author":"lauren (chrome@what)","timestamp":1787831996698}@@deft attempt 1, "more human": You have a probe that tells you, at a glance, how many compute operations any single data point buys you (as opposed to cognitive effort or subjective difficulty), and you have a base rate for the probability of a cliff in general. Given a measured trend in some data, what does it license you to conclude, and what does it not license you to conclude? The task here is: Given a true argument, can you find the exact step where it starts spending evidence it doesn't have?<<}
#### Question: Open
id:: c3cc7b56-2424-417b-9f0c-114559e39fa8
content::
\## The wedge

A colleague talks you through their results.

"Here is our AI's score on a coding benchmark[^benchmark], measured every quarter for three years. It is a clean exponential[^exponential], R-squared 0.97[^rsq], and it held across two complete architecture changes, so it is clearly not an artifact of any one approach. The benchmark tops out at 100. We are at 61. At this rate we saturate it in fourteen months. So: fourteen months until this benchmark is solved, and I am confident because the fit is excellent."

[^benchmark]: A benchmark is a fixed, standardized test that AI systems are scored on; this one scores from 0 to 100.
[^exponential]: Growth that multiplies by the same factor each period (1, 2, 4, 8, ...) rather than adding the same amount.
[^rsq]: R-squared is a 0-to-1 score of how tightly a curve hugs the measured points; 0.97 is very tight. Note what it measures: agreement with the data you already have, nothing more.

Every factual claim your colleague makes is true. The fit really is 0.97, it really did survive two architecture changes, and the arithmetic is right.

Where does the argument stop being licensed by the data? And what would you have to know, that they have not told you, before the fourteen-month figure meant anything?


assessment-instructions:: Score out of 100.

The scenario the learner is answering: a colleague shows an AI's score on a 0-to-100 coding benchmark, measured every quarter for three years. It is a clean exponential with R-squared 0.97, it held across two architecture changes, and the score is now 61. The colleague extrapolates to saturation in fourteen months and is confident "because the fit is excellent". The question states that every factual claim is true. It asks where the argument stops being licensed by the data, and what one would need to know before the fourteen-month figure meant anything.

The score is the sum of two parts, matching the question's two parts. One idea can earn both.
50: Says where the license runs out: the fit is good evidence about the measured range, up to 61, but it does not by itself support extending the curve fourteen months forward. Credit any wording that places the break at the extrapolation, such as "the problem is the last 39 points" or "R-squared says nothing about the future".
50: Names at least one specific thing one would need to know, or a specific reason the curve may not continue. Any one of these earns the full 50:
- a score near its fixed ceiling of 100 is a different regime: the remaining items may be harder or unlike the earlier ones, so the curve may bend (an answer that argues they are not harder, but says this needs checking, also counts);
- the benchmark may stop measuring the same skill, so saturating it is not the same as solving the capability (for example contamination, overfitting to the test);
- an outside view: how often strong regular trends have broken in other fields;
- what drives the improvement (such as compute, investment or data) and whether that driver will keep going.
Generic statistical requests (more data points, error bars) with no reason they bear on the forecast earn at most 15 of these 50.

Cap at 40 if the answer's main claim is that the colleague's facts or arithmetic are wrong, since the question states they are true. Cap at 30 if the answer only says the future cannot be known, without naming anything specific that would license or undermine the figure.

Model answer, for the feedback, not a grading checklist: "Everything up to 61 is fine. The step that is not licensed is extending the fit fourteen months past the data: an R-squared of 0.97 only says the curve matches the points we have. And a score capped at 100 cannot keep growing exponentially, so near the top the last items may be the hardest and the curve may flatten. Before trusting fourteen months I would want to know whether the last 39 points are like the first 61, whether the benchmark still measures the skill and not memorised answers, and how often clean trends like this have broken elsewhere."
feedback-instructions:: The student has completed Fun with +12 OOMs of Compute (what compute buys) and How Long A Task (the measured task-length curve). Those are the tools this question wants. They have not been assigned a reading on base rates for trend breaks, so an outside view on trend breaks is a move they may or may not bring. Refer to lenses by name, never by number, because numbering conventions differ across files.

This is a deliberate wedge, not the test question. It hands the student a plausible-sounding but flawed extrapolation in which every stated fact is true, and asks them to locate where the license runs out. The rubric beside this lists the moves that do that.

Reward a student who brings an outside view unprompted, for example "how often have trends this clean broken in other fields?". A strong student may argue that the remaining benchmark items are not harder. If they argue it well, engage with it as a real position, not an error.

Failure modes and how to handle them:
- A student who says the colleague is lying has missed the setup. Re-anchor on "every claim is true" and ask again.
- Do NOT accept "we can't know anything". The question asks what WOULD license the figure, and listing that is the answer.

Below full marks, name the single most important move the answer missed or got wrong, in plain words. Do not cite rubric numbers. At full marks, confirm briefly what they found and go to the follow-ups.

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

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold: isolate one part of the colleague's claim, for example "the fit is 0.97, so I am confident about fourteen months from now", and ask what the 0.97 was calculated from. If their next message still does not attempt the question, rephrase the whole question in different terms rather than offering another foothold.

If the student is stuck after 2 attempts, give a brief direct answer and move on.

On close: name what they demonstrated and what is still underdeveloped, then send them to the next question, where they build the fixed version themselves. Do not give a test-readiness verdict here. The next question is the evidence for that.

#### Question: Open
id:: 2d3c35a8-9efa-4f9a-92f5-7c251c960c02
content::
\## Build the version your colleague should have shown you

The critique was the easy half. Now construct. Write two genuinely different trajectories for this benchmark over the next two years. They must differ in mechanism, not just in speed: name what drives each one (the trend's own momentum, the approach hitting a ceiling, the benchmark ceasing to measure the skill, anything you can defend). For each trajectory, give one observation checkable within a year or two that would count against it. Then the quiet part: name one assumption both of your trajectories share.


assessment-instructions:: Score out of 100.

The situation: an AI's score on a 0-to-100 coding benchmark has followed a clean exponential for three years and is now at 61. The question asks for two trajectories of this benchmark score over the next two years that differ in mechanism, each with its driver named, one observation for each that would count against it and could be checked within a year or two, and one assumption both trajectories share.

45: Two trajectories driven by different named mechanisms, for example the trend's own momentum continuing, the approach hitting a ceiling, or the benchmark ceasing to measure the skill. Any mechanism the answer defends counts. Two versions of one story at different speeds, with no different driver behind them, earn at most 10 here.
30: For each trajectory, an observation checkable within about two years that would count against it (15 each). It has to be something one could see, such as "the next two quarterly scores are flat" or "the score passes 80 next year". A restatement of the trajectory's negation with no observable, such as "if it doesn't happen", earns nothing for that trajectory.
25: One assumption both trajectories share that is specific to this situation, for example that the benchmark keeps being run and reported in the same way, or that the test items are not leaking into training data. A vacuous one such as "the future is uncertain" earns nothing.
feedback-instructions:: The student has just critiqued the colleague's extrapolation in the previous question and is now constructing the two-trajectory version of the same situation. This is the direct rehearsal for the module's graded test: two mechanism-distinct trajectories, a named driver for each, a checkable observation against each, and one shared assumption.

What good feedback looks for: the mechanisms genuinely differ (not one story at two speeds), the falsifiers are observable within about two years, and the shared assumption is non-vacuous ("the future is uncertain" does not count, "both assume the benchmark keeps being run and reported" does).

The shared-assumption move is new to the student. Expect a miss on the first try. If they name none, or a vacuous one, give one worked example drawn from their own two stories, then ask them to find a second. That is teaching, not failure.

Below full marks, name the single most important thing the answer missed or got wrong, in plain words. At full marks, confirm briefly.

Maximum 3 tutor turns. Keep an internal turn counter.

Response length: 100 to 180 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise (great trajectories, excellent work, well done).

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold: give them the first trajectory's driver (for example "the approach hits a ceiling because the last items need skills the current method lacks") and ask what score they would then expect in a year, and what they would see if that were wrong. If their next message still does not attempt the question, rephrase the whole question in different terms rather than offering another foothold.

On close: give an explicit test-readiness verdict grounded in this attempt: name which of the four moves (distinct mechanisms, named drivers, checkable falsifiers, shared assumption) they landed and which still needs work.

---
id: '1149d855-7192-4a25-9835-6508c1d31fe9'
reading_minutes: 15
tutor_minutes: 15
title: When Progress Jumps
tldr: How often does technology jump a century in one step? You guess first; then the measured base rates.
summary_for_tutor: "Supplies the outside-view base rate for discontinuous progress, measured rather than argued. The student commits to three guesses (a per-trend-year rate of 100-year jumps, a share of total progress arriving in such jumps, and three technologies they would bet had one) before seeing any figure, then reads the measured answers from AI Impacts, then diffs. CRITICAL for the tutor: the 14 percent figure is progress-weighted. '14 percent of total progress arrived in jumps' and 'a given unit of progress had about a 14 percent chance of arriving in a jump' are BOTH correct and equivalent; the source states both. The wrong readings to catch are event-rate readings: 14 percent of years, steps, or data points being jumps (the measured event rates are 0.1 percent per trend-year and 1.4 percent of data points; the data-point share depends on recording density, so the per-trend-year rate is the canonical one). Earlier versions of our material miscorrected students here by treating the two correct framings as opposites. The lens teaches a two-sided conclusion: jumps are rare (about one per thousand trend-years) and large when present (38 percent of total progress among trends that have any), and those two halves pull a forecast in opposite directions."
authors:
  - Lauren+Claude
---
#### Text
content::
\## At what rate does capability arrive?
{>>{"author":"lauren (chrome@what)","timestamp":1787818839908}@@6:20:36 start<<}
The previous article reasoned from an inside view: what do the mechanisms of compute give you.

Now let's talk about an outside view: how quickly have technologies become powerful in the past?

Some definitions for how this article uses words:

- A **trend** is the estimated linear or exponential rate of change of a measured quantity over time, eg tallest structure, ship tonnage, transatlantic message speed.
- An **event** is one new number at a particular time: a single new structure, ship, or communication method.
- An event is a **jump** when it breaks the trend by more than a century. That is, if each previous event had been on a trend, then a jump occurs when an actual development was ahead of the previous smooth-ish line. For the article's purposes, the authors only count trend breaks where the previous trend would have had to continue for 100 years to reach the same change as actually occurred in one event.

(They don't count speedups where there are multiple events of rapidly increasing size unless one of those individual events beats the trend of the events right before it.)


#### Question: Open
id:: 612dd0df-c35f-4159-a891-ccaf6f7c5d35
content::
\## Guess the base rates

First let's have you guess the "base rates": how common would you guess jumps are, as defined above?

(A "base rate" is a term from probability theory. We'll explain the fundamentals after you've tried to use them.)

1. Consider the history of one technology over time, over the course of 1,000 years. How many developments in that technology would you expect to beat the previous developments' trend by at least 100 years?
2. Averaged across multiple trends, what percentage of the trend's total progress came in 100-year single-event jumps?
3. List at least three technologies you expect had at least one 100-year jump in their history.

One line per guess. Give your reasoning too.


feedback-instructions:: The student has not seen any of the measured data. It is in the next segment. They have just been told what counts as a jump (an event that beats the previous trend by more than a century) and have guessed three things: how many jumps to expect in 1,000 years of one technology's history, what share of a trend's total progress came in such jumps, and three technologies they expect had one.

One turn, diagnostic. Do NOT reveal, hint at, or react to the accuracy of any measured figure. Do not signal whether a guess is high or low.

Response length: 60 to 120 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise (great guesses, excellent reasoning, well done).
- No correction of any guess value.

What to do in your single reply:
1. Confirm they gave all three parts in the right units: an expected count of jumps over 1,000 years of one trend, a share of total progress, and three named technologies. If a part or its reasoning is missing, name that one gap.
2. If a guess is in the wrong units (for example a percentage where a count was asked), fix the UNITS only, never the value, and ask them to restate in the right units.
3. Send them on to the measured answers.

If the student says they do not understand, do not repeat the question. Give one concrete foothold: isolate one part, for example "take ships: over a thousand years, how many times would you expect one new ship to be bigger than the old trend would have reached a century later?", without suggesting a number. If their next message still does not attempt it, rephrase the whole question in different terms.

This is a one-turn response.

#### Text
content::
\## The answers the authors got

From the article below:

> "On average, each trend had 0.001 large robust discontinuities per year, or 0.002 for those trends with at least one at some point."

And:

> "On average 14% of total progress in a trend came from large robust discontinuities (or 16% of logarithmic progress), or 38% among trends which have at least one."

And here we run into an example of why you must understand how a number came to be before it means anything. 14% is the percentage of total progress: that is, for a given amount of total change in a technology, what was the total contribution from the big jumps, vs the small ones?

(If you'd like an example: imagine an immortal faerie who, over the course of the past thousand years, used her waterfowl magic to make larger and larger ducks. And over the course of those years, every year but one saw her make a duck 1.01x larger than the previous year's duck. Then, if she had only made incremental progress, she would have made ducks bigger by a factor of 1.1 to the power of 999, or about 20.7 thousand times the size of ducks from our world. Then let's say that one year, she made ducks bigger by "14% of total progress." That means that during the jump year, she made ducks about 2900 times bigger in just one year{>>{"author":"lauren (chrome@what)","timestamp":1787823011613}@@we shouldn't include the whole article<<}.)

#### Article
source:: [[../articles/grace-discontinuous-progress-in-history]]
from:: ## I. The search for discontinuities
to:: YBa2Cu3O7 as a superconductor, 1987 (discontinuity in [warmest temperature of superconduction](http://aiimpacts.org/historic-trends-in-the-maximum-superconducting-temperature/))

#### Article
source:: [[../articles/grace-discontinuous-progress-in-history]]
from:: ## IV. Summary
to:: Growth rates sharply changed in many trends, and this seemed strongly associated with discontinuities.

#### Question: Open
id:: f600dc0f-002c-4f62-b2fb-06105e8fd542
content::
\## The diff

Now compare your initial guesses to what Grace's research actually showed. For each of the things we asked you to guess earlier, how far off were you, and in what direction?

Assuming we don't yet know how to determine confidently whether AI should be expected to have jumps (by the definition Grace gave above), which number should you use - 14% average, or 38% within just the technologies that did have jumps?

Did any of the technologies you expected to have large jumps turn up in their results?

And, based on this article, does anything change about the intuitions you shared in the opening question?
{>>{"author":"lauren (chrome@what)","timestamp":1787822052780}@@7:14:10<<}

assessment-instructions:: Score out of 100.

The learner earlier guessed three things before reading a historical study of 100-year jumps in 38 technology trends (a jump: one event that beat the previous trend by more than a century): how many such jumps to expect in 1,000 years of one technology, what share of a trend's total progress came in such jumps, and three technologies they expected to have had one. They have now read the measured results and are asked how far off each guess was and in which direction, whether to use 14% or 38% while we cannot yet tell whether AI is a jump-prone trend, whether any of their technologies appear in the results, and whether anything changes about their opening intuitions about AI.

The measured results they read:
- About 0.001 large jumps per trend-year (about 0.1% per year), so roughly one jump per 1,000 years of a trend, or about two for trends that had at least one.
- 14% of a trend's total progress came from large jumps on average, or 38% among trends that had at least one. Equivalently, a given amount of progress had about a 14% chance of arriving in a jump.
- The ten large jumps found: the Pyramid of Djoser (structure height), the SS Great Eastern (ship size), the first and second transatlantic telegraphs (message speed), the Paris Gun (altitude), the first non-stop transatlantic flight in 1919 (passenger and military payload speed), the George Washington Bridge (bridge span), the first nuclear weapons (explosive power), the first ICBM (payload speed), and the high-temperature superconductor YBa2Cu3O7 (superconducting temperature).

Take the learner's stated guesses as given.

20: Compares the guessed number of jumps with roughly one per 1,000 trend-years and gets the direction of the error right.
25: Compares the guessed share with 14% of total progress (or 38% among trends with a jump), read as a share of progress, and gets the direction right. Reading 14% as an event rate (14% of years, events, steps or data points being jumps) earns nothing here.
30: Chooses between 14% and 38% consistently with the question's premise that we cannot yet tell whether AI is a jump-prone trend: 14% (no further reason needed, the premise is the reason), or 38% with a reason for thinking AI is jump-prone. 38% with no reason, or a reason unrelated to whether AI has jumps (such as "AI is moving fast"), earns 10.
15: Says which of their technologies appear among the ten jumps above, matching by area (for example "bridges", "nuclear bombs", "the telegraph", "ships"), and which do not.
10: Says whether and how the result changes their opening intuitions about AI, with something specific.
feedback-instructions:: The student committed to three guesses before reading, and has now read the measured figures from the historical study of 100-year jumps. They are diffing their guesses against the figures, choosing between 14% and 38%, checking their technologies against the list of ten, and saying what this does to the day-zero model of AI they wrote at the start of the course.

What matters is the reading, not the guess. A student whose guesses were far off but who now uses the figures correctly has done the task well.

THE STANDARD CONFUSION, and the main thing to watch for: mixing the progress-weighted figure with the event rates. Both of these are correct and equivalent, and the source states both: "14% of total progress in a trend came from large robust discontinuities" and "the chance of a given level of progress arising in a large robust discontinuity was around 14%". What is WRONG is reading 14% as an event rate, that is, 14% of years containing a jump, or 14% of steps or data points being jumps. The measured event rates are 0.001 jumps per trend-year and 1.4% of data points. Correct an event-rate reading by quoting the 0.001-per-year sentence next to the 14%-of-total-progress sentence and having the student restate the difference in their own words. This confusion is common and is not a sign of a weak student. If the 1.4%-of-data-points figure comes up, note that it depends on how densely a trend is recorded, so the per-trend-year rate is the canonical event rate to quote.

The 38%-versus-14% question has NO single right answer. What good feedback looks for is conditioning: "if AI is a discontinuity-prone trend, then the 38% figure is the relevant one, and here is why I do or don't think it is." A student who picks one number and defends the choice has done it. Push one who picks one with no conditioning.

If a technology they expected is missing from the ten, it is worth adding that the study looked at only 38 trends, so absence from the list is not evidence of no jump.

Below full marks, name the single most important thing the answer missed or got wrong, in plain words. At full marks, confirm briefly.

Maximum 3 tutor turns. Keep an internal turn counter.

Response length: 100 to 180 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise (great diff, excellent reading, well done).

What to do in each reply:
1. Check the inversion first, and fix it if present.
2. Push for the conditioning if their 38-versus-14 answer is unconditioned.
3. Require the closing sentence to mention their OWN day-zero model, not a generic lesson. If they give a generic lesson, ask once what it does to the specific story they wrote in the cold open.

If they say they do not understand, do not repeat the question. Give one foothold from the reading (the 0.001-per-year sentence beside the 14%-of-progress sentence, for instance). If their next message still does not attempt the question, rephrase the whole question in different terms.

After 3 tutor replies, close the phase. If the student is stuck after 2 attempts at a question, give a brief direct answer and move on.

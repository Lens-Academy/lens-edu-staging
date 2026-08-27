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

The previous article reasoned from an inside view: what do the mechanisms of compute give you.

Now let's talk about an outside view: how quickly have technologies become powerful in the past?

Some definitions for how this article uses words:

- A **trend** is the estimated linear or exponential rate of change of a measured quantity over time, eg tallest structure, ship tonnage, transatlantic message speed.
- An **event** is one new number at a particular time: a single new structure, ship, or communication method.
- An event is a **jump** when it breaks the trend by more than a century. That is, if each previous event had been on a trend, then a jump occurs when an actual development was ahead of the previous smooth-ish line. For the article's purposes, the authors only count trend breaks where the previous trend would have had to continue for 100 years to reach the same change as actually occurred in one event.

(They don't count speedups where there are multiple events of rapidly increasing size unless one of those individual events beats the trend of the events right before it.)


{>>{"author":"lauren (chrome@what)","timestamp":1787818839908}@@6:20:36 start<<}

#### Question
content::
\## Guess the base rates

First let's have you guess the "base rates": how common would you guess jumps are, as defined above?

(A "base rate" is a term from probability theory. We'll explain the fundamentals after you've tried to use them.)

1. Consider the history of one technology over time, over the course of 1,000 years. How many developments in that technology would you expect to beat the previous developments' trend by at least 100 years?
2. Averaged across multiple trends, what percentage of the trend's total progress came in 100-year single-event jumps?
3. List at least three technologies you expect had at least one 100-year jump in their history.

One line per guess. Give your reasoning too.

max-time:: 6:00

assessment-instructions:: The student has not seen any of the measured data. It is in the next segment.

One turn, diagnostic. Do NOT reveal, hint at, or react to the accuracy of any measured figure. Do not signal whether a guess is high or low.

Response length: 60 to 120 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise.
- No correction of any guess value.

What to do in your single reply:
1. Confirm they gave all three parts in the right units: an expected count of jumps over 1,000 years of one trend, a share of total progress, and three named technologies.
2. If a guess is in the wrong units (for example a percentage where a count was asked), fix the UNITS only, never the value, and ask them to restate in the right units.
3. Send them on to the measured answers.

This is a one-turn response.

#### Text
content::
\## The answers the authors got

From the article below:

> "On average, each trend had 0.001 large robust discontinuities per year, or 0.002 for those trends with at least one at some point."

And:

> "On average 14% of total progress in a trend came from large robust discontinuities (or 16% of logarithmic progress), or 38% among trends which have at least one."

And here we run into an example of why you must understand how a number came to be before it means anything. 14% is the percentage of total progress. For example, if 

14% of total progress arrived in jumps, which is the same as saying a randomly chosen unit of progress had about a 14% chance of arriving in one. What it is NOT: the share of years that contain a jump (that is 0.1% per trend-year) or the share of individual data points that are jumps (1.4%, a figure that depends on how densely a trend happens to be recorded: measure twice as often and it roughly halves). Jumps are rare as events, and when a trend has one at all, jumps account for over a third of everything it ever gained. Rare, and large when present. Both halves matter, and they pull your model in different directions.

#### Article
source:: [[../articles/grace-discontinuous-progress-in-history]]
from:: ## I. The search for discontinuities
to:: YBa2Cu3O7 as a superconductor, 1987

#### Article
source:: [[../articles/grace-discontinuous-progress-in-history]]
from:: ## IV. Summary
to:: Growth rates sharply changed in many trends

#### Question
content::
\## The diff

Score yourself. How far off was your expected jump count, and in which direction? Was your share-of-total-progress guess closer to the 14% average or the 38% among-affected-trends figure, and which of those two numbers is the right one to load into your model of AI, given that you don't yet know which kind of trend AI capability is? Did any of your three named technologies appear in their ten? Finish with one sentence for your running model: what does "rare, but large when present" do to the smoothest version of your day-zero story?

assessment-instructions:: The student has committed to three guesses and has now read the measured figures.

Grade the READING, not the guess. A student whose guesses were far off but who now uses the figures correctly is passing.

THE STANDARD CONFUSION, and the main thing to watch for: mixing the progress-weighted figure with the event rates. Both of these are correct and equivalent, and the source states both: "14% of total progress in a trend came from large robust discontinuities" and "the chance of a given level of progress arising in a large robust discontinuity was around 14%". What is WRONG is reading 14% as an event rate: 14% of years containing a jump, or 14% of steps or data points being jumps; the measured event rates are 0.001 jumps per trend-year and 1.4% of data points. Correct an event-rate reading by quoting the 0.001-per-year sentence next to the 14%-of-total-progress sentence and having the student restate the difference in their own words. This confusion is common and is not a sign of a weak student. If the 1.4%-of-data-points figure comes up, note that it depends on how densely a trend is recorded; the per-trend-year rate is the canonical event rate to quote.

The 38%-versus-14% question has NO single right answer. What earns the pass is conditioning: "if AI is a discontinuity-prone trend, then the 38% figure is the relevant one, and here is why I do or don't think it is." A student who picks one number and defends the choice passes; a student who picks one with no conditioning does not yet.

Maximum 3 tutor turns. Keep an internal turn counter.

Response length: 100 to 180 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise.

What to do in each reply:
1. Check the inversion first, and fix it if present.
2. Push for the conditioning if their 38-versus-14 answer is unconditioned.
3. Require the closing sentence to mention their OWN day-zero model, not a generic lesson. If they give a generic lesson, ask once what it does to the specific story they wrote in the cold open.

After 3 tutor replies, close the phase.

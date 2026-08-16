---
id: '1149d855-7192-4a25-9835-6508c1d31fe9'
title: When Progress Jumps
tldr: How often does technology jump a century in one step? You guess first; then the measured base rates.
summary_for_tutor: "Supplies the outside-view base rate for discontinuous progress, measured rather than argued. The student commits to three guesses (a per-trend-year rate of 100-year jumps, a share of total progress arriving in such jumps, and three technologies they would bet had one) before seeing any figure, then reads the measured answers from AI Impacts, then diffs. CRITICAL for the tutor: the 14 percent figure is progress-weighted. '14 percent of total progress arrived in jumps' and 'a given unit of progress had about a 14 percent chance of arriving in a jump' are BOTH correct and equivalent; the source states both. The wrong readings to catch are event-rate readings: 14 percent of years, steps, or data points being jumps (the measured event rates are 0.1 percent per trend-year and 1.4 percent of data points; the data-point share depends on recording density, so the per-trend-year rate is the canonical one). Earlier versions of our material miscorrected students here by treating the two correct framings as opposites. The lens teaches a two-sided conclusion: jumps are rare (about one per thousand trend-years) and large when present (38 percent of total progress among trends that have any), and those two halves pull a forecast in opposite directions."
authors:
  - Lauren+Claude
---
#### Text
content::
\## Does capability arrive as a slope or a cliff?

The last lens probed your model from the inside: what you personally believe compute buys. This one turns around and asks the outside question: never mind your reasoning, how has technological progress actually arrived, across every trend anyone has measured?

Every model of the future leans on an assumption about smoothness: does capability arrive as a steady slope, or in cliffs? That is an empirical question about the past, and AI Impacts spent years measuring it: dozens of technological trends checked for moments where one step delivered more than a century of progress at the previous rate. Three terms, so the question below is answerable:

- A **trend** is one measured quantity over time: tallest structure, ship tonnage, transatlantic message speed.
- A **step** is one new data point in that record: a single new ship, bridge, or bomb.
- A step counts as a **jump** when it delivers more than a century of *surplus* progress: take the progress the step actually made, subtract what the elapsed time already promised at the trend's previous rate, and more than 100 extra years' worth must remain. So a sparse record is not jumpy by default: a step that covers 150 quiet years and lands exactly where extrapolation predicted has zero surplus. One honest caveat: the bar is applied one step at a time, so whether a fast burst counts can depend on how finely history recorded it; a century of surplus smeared across many small steps may never clear the bar in any single one. The researchers flag this themselves.

This one stings a little; the sting is the data you keep.

#### Question
content::
\## Guess the base rates

Three guesses, before you look at anything.

1. Pick one measured technology trend and watch it for 1,000 years. How many 100-year jumps do you expect to see in that time?
2. Averaged across trends, what share of a trend's TOTAL progress arrived in such jumps?
3. Name three technologies you would bet money had at least one 100-year jump somewhere in their history.

Write your reasoning in one line per guess; the reasoning is worth more than the number.

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
\## The measured answers

The measured answers, quoted from AI Impacts, "Discontinuous progress in history: an update" (Katja Grace; link below, and worth the full read):

> "On average, each trend had 0.001 large robust discontinuities per year, or 0.002 for those trends with at least one at some point."

And:

> "On average 14% of total progress in a trend came from large robust discontinuities (or 16% of logarithmic progress), or 38% among trends which have at least one."

Read the 14% carefully. It is progress-weighted: 14% of total progress arrived in jumps, which is the same as saying a randomly chosen unit of progress had about a 14% chance of arriving in one. What it is NOT: the share of years that contain a jump (that is 0.1% per trend-year) or the share of individual data points that are jumps (1.4%, a figure that depends on how densely a trend happens to be recorded: measure twice as often and it roughly halves). Jumps are rare as events, and when a trend has one at all, jumps account for over a third of everything it ever gained. Rare, and large when present. Both halves matter, and they pull your model in different directions.

#### Article
source:: [[../articles/grace-discontinuous-progress-in-history]]{++{"author":"Lauren's AI","timestamp":1786857076488}@@
from:: ## I. The search for discontinuities
to:: YBa2Cu3O7 as a superconductor, 1987

#### Article
source:: [[../articles/grace-discontinuous-progress-in-history]]
from:: ## IV. Summary
to:: Growth rates sharply changed in many trends++}

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

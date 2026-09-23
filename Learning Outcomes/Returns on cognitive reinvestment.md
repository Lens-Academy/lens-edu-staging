---
id: '954e2b93-d4d6-42bd-accd-e49c2f46ae7e'
learning-outcome: "Analyse whether a system that reinvests its cognitive output into improving itself will level off, grow steadily, or accelerate, by reasoning about whether each round of improvement enables at least as large a further improvement, how quickly gains can be reinvested (prompt channels such as software versus slow channels such as new hardware), and which observations would tell these regimes apart."
topic: "[[../Domains and Topics/11 Strategy/Takeoff dynamics]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Recursive self-improvement. AFFINE prerequisites: Instrumental/Terminal Distinction. Not yet copied into requires:. %%
## Test:
id:: 24832e07-eb3e-4125-92a8-4ac698b434e0

#### Question: Open
id:: 0ce98fc1-93d8-4f31-94e3-bb8a994fe507
content:: An AI research system improves itself in rounds. In each round, the current version designs the next version. "Research speed" means how quickly the system completes useful research work. Each round below was carried out by the improved version from the round before.

| Round | Gain in research speed | Main source of the gain |
|---|---|---|
| 1 | +30% | algorithm changes, deployed within days |
| 2 | +20% | algorithm changes, deployed within days |
| 3 | +13% | algorithm changes, deployed within days |
| 4 | +9% | algorithm changes, deployed within days |

Separately, the lab could roughly double the system's hardware, but new chips take about 18 months to arrive.

Analyst A says: "The gains are shrinking. This will level off." Analyst B says: "Each version is a better researcher than the last, so the process is self-reinforcing. It will accelerate."

1. If this trend continues, what does it suggest about the software-only process? Evaluate both analysts' arguments.
2. Give two reasons why the trend could be a misleading guide to what happens next, and name one further measurement that would best tell A's and B's views apart, including what result would favour each.
3. How does the 18-month hardware option change the picture? Consider both how large it is and how fast it is.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement: a learner may conclude that an acceleration is likely or unlikely and still earn full marks. Do not require any specific term such as "k", "critical", "fizzle" or "FOOM", and do not require exact arithmetic.

**(a) Reading the trend, 40 points.** Full credit requires: (i) each gain is roughly two thirds of the one before, so if this continues the gains shrink geometrically and their cumulative effect approaches a finite limit: research speed levels off (at roughly two to two and a half times the starting speed, if the learner estimates it; any estimate in that range, or no number, is fine); and (ii) Analyst B's argument is already accounted for in the data, because each round was done by the improved version: the self-reinforcement is real, but it is not enough to make each improvement at least as large as the last, since the next improvements are getting harder faster than the system is getting better. The key idea is that what decides between levelling off and acceleration is whether one round's gain enables an equal or larger gain in the next round, not whether the system improves at all. 20 points for (i) alone. 15 points for (ii) alone. 5 points for siding with A only because "the numbers go down".

**(b) Why the trend might mislead, and a discriminating measurement, 35 points.** Reasons (20 points, 10 each), for example: the data cover one kind of improvement (for example, one family of algorithm changes) whose easy gains are being used up, while a different kind of improvement could restart large gains; a system above some capability level may reach improvements that were unavailable below it, so the returns curve could turn upward; four rounds is a small and possibly noisy sample; costs outside the table (compute per round, experiment time) may be changing; gains could fall faster than the trend suggests. Measurement (15 points): any measurement that bears on whether smarter versions find disproportionately larger improvements, with a stated result for each side. Examples: have an older and a newer version each attempt the same next round from the same starting point and compare the gains they find; track how much research effort each unit of gain costs as the system improves; test whether the gains from a new kind of change also shrink. 7 points for a relevant measurement without saying what result would favour which analyst.

**(c) The hardware channel, 25 points.** Full credit distinguishes size from speed. Size: doubling hardware is a large one-time gain, and more hardware can also make further algorithm improvements more valuable or possible, so it may raise the level at which the process levels off or restart gains. Speed: an 18-month delay means that hardware cannot drive rapid repeated reinvestment; any fast acceleration within those 18 months would have to come from channels that can be reinvested quickly (software, or compute that can be rented or bought quickly). If the software-only gains shrink as the table suggests, a slow hardware channel produces growth on the timescale of hardware cycles, not a rapid explosion, unless the system can shorten that cycle. 12 points if only size or only speed is addressed.
feedback-instructions:: Tell the learner whether they saw that the table already includes the effect Analyst B appeals to. Name their most useful discriminating measurement, or explain what their measurement fails to separate. Ask one follow-up question about what would have to be true for the returns to turn upward. No generic praise.

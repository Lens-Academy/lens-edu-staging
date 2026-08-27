---
id: '64b745ad-7b5e-4b9e-9ab7-8bf3a82ab38a'
reading_minutes: 15
tutor_minutes: 5
title: How Long A Task
tldr: AI agents finish short jobs and fail at long ones. METR measured where that line sits and how fast it moves. You guess the line first.
summary_for_tutor: "Introduces METR and the 50 percent time horizon, and gives the student the first real measured curve in the course. The student commits to two things before reading: the longest task, in human-professional time, that a current agent finishes on its own about half the time, and what would have to change for that number to be ten times larger. Then they read METR's own write-up.\n\nWHAT METR MEASURES, for your reference. They take tasks that human professionals have been timed on, run frontier agents on them, and find the task length at which an agent succeeds half the time. That length has roughly doubled every seven months over six years. CRITICAL: the tasks are SOFTWARE and research-engineering tasks, not tasks in general, and the post's own title says so.\n\nFOUR MISREADINGS TO CATCH, in order of how often they appear:\n1. Reading the 50 percent as a quality score. It is not 'the AI is half as good as a human'. It is the length at which the agent's success rate crosses one half.\n2. Generalising from software to everything. The measure covers a specific task family. A student who says 'AI can do four-hour jobs now' has dropped the domain.\n3. Treating the doubling time as current. METR's own banner at the top of the reading says the static figures and the doubling time are out of date, and points at Time Horizon 1.1. A student who quotes a number without its version has done the thing this course is about.\n4. Assuming a 50 percent success rate is usable. Ask what they would deploy at a coin-flip success rate. The 80 percent horizon is far shorter than the 50 percent one.\n\nDo not deliver any of this in the diagnostic turn. It is for the turns after they have read."
authors:
  - Lauren+Claude
---
#### Text
content::
\## How big of a task can't a given AI do?

Whether or note an AI is inclined to do so, if we want to know whether AI is at risk of doing things like "take over the world" or "kill all humans", we'd like to know how close it is.

Let's assume we want to measure how close AI is to being able to do that. Later in the course we'll work through evidence that you tend to get what you can best measure, so this is a dangerous thing to measure, and might already be having negative effects. But it's potentially useful for defenders to know, so let's talk about it.

By far the{>>{"author":"lauren (chrome@what)","timestamp":1787823523443}@@7:38:41<<} most common type of interaction with AIs is to describe a task and get a mostly-self-contained result. Among those tasks, a common type of task is making or changing software. Many of the tasks one would do as part of making software have a pretty clear success or fail criteria. So we can ask how big of a programming task the AI can do.

METR is an independent organisation that runs those measurements. They test models that labs give them access to, then publish their results.

(Considering what effects that might or might not have on the alignment of METR as an organization is, for now, left as an exercise to the reader. We'll get to organizations later.)

Their approach has three parts.

- Take well-defined tasks where **skilled human software engineers can be timed**, so we have a reference task length (in human hours).
- Then **give a particular AI the same task** to finish without interaction.
- Then they report as the final time-horizon number the **human-hour length of task on which the AI succeeds half the time**. When you hear them report time horizon that's what it means.
{>>{"author":"lauren (chrome@what)","timestamp":1787824700273}@@7:58:18<<}
#### Question
content::
\## What have they found (on AIs up to 2025)

Two pre-read questions.

1. What would you expect is the number, in human-equivalent hours, that their method gave for AIs up to the end of 2025?
2. What one or two things would you currently guess are the bottlenecks for 

1. Think of the longest job you would trust a current AI agent to finish on its own, with nobody checking its work, about half the time. Give it in minutes or hours of human professional time. One number.
2. Name the one thing that would have to change for your number to be ten times larger. Not a list. The one thing you think is actually holding it.

Your reasoning matters more than your number here, so write a line for each.

max-time:: 5:00

assessment-instructions:: The student has not seen METR's figures. They are in the next segment.

One turn, diagnostic. Do NOT reveal the measured horizon, the doubling time, or whether their number is high or low. Do not hint by reacting.

Your only job this turn is to make the second answer sharper. If they named a category rather than a mechanism, for example "more compute" or "better models", ask which specific thing that buys them. If they named a real mechanism, ask what they would expect to see first if it were already happening.

Response length: 60 to 110 words. Short paragraphs. No lists.

Response style:
- Calm and direct.
- Do not over-validate. No generic praise.
- No correction of the number{>>{"author":"lauren (chrome@what)","timestamp":1787824426516}@@re: the article below: we're statically embedding a dynamic article! that's a problem!<<}.

#### Article
source:: [[../articles/metr-measuring-ai-ability-to-complete-long-tasks]]
to:: {--{"author":"Lauren's AI","timestamp":1786856931798}@@s stakes, --}both in terms of potential benefits and potential risks.

#### Text
content::
\## Optional: a doubling is hard to feel

The chart you just read plots a doubling. Reading one and believing one are different things, and the gap between them is not a failure of arithmetic.

The clip below is about eighty seconds from a longer video by AI In Context. It is the plainest statement of that gap we could find: your intuition expects things to grow at a steady rate, a doubling does not, and the example it uses is March 2020.

Watch it for the feeling rather than the maths, then look at the chart again.

#### Video
source:: [[../video_transcripts/ai-in-context-were-not-ready-for-superintelligence]]
from:: 6:05
to:: 7:22
optional:: true

---
id: '64b745ad-7b5e-4b9e-9ab7-8bf3a82ab38a'
title: How Long A Task
tldr: AI agents finish short jobs and fail at long ones. METR measured where that line sits and how fast it moves. You guess the line first.
summary_for_tutor: "Introduces METR and the 50 percent time horizon, and gives the student the first real measured curve in the course. The student commits to two things before reading: the longest task, in human-professional time, that a current agent finishes on its own about half the time, and what would have to change for that number to be ten times larger. Then they read METR's own write-up.\n\nWHAT METR MEASURES, for your reference. They take tasks that human professionals have been timed on, run frontier agents on them, and find the task length at which an agent succeeds half the time. That length has roughly doubled every seven months over six years. CRITICAL: the tasks are SOFTWARE and research-engineering tasks, not tasks in general, and the post's own title says so.\n\nFOUR MISREADINGS TO CATCH, in order of how often they appear:\n1. Reading the 50 percent as a quality score. It is not 'the AI is half as good as a human'. It is the length at which the agent's success rate crosses one half.\n2. Generalising from software to everything. The measure covers a specific task family. A student who says 'AI can do four-hour jobs now' has dropped the domain.\n3. Treating the doubling time as current. METR's own banner at the top of the reading says the static figures and the doubling time are out of date, and points at Time Horizon 1.1. A student who quotes a number without its version has done the thing this course is about.\n4. Assuming a 50 percent success rate is usable. Ask what they would deploy at a coin-flip success rate. The 80 percent horizon is far shorter than the 50 percent one.\n\nDo not deliver any of this in the diagnostic turn. It is for the turns after they have read."
authors:
  - Lauren+Claude
---
#### Text
content::
\## Where does an agent stop being able to finish the job?

An AI agent can write a function. It usually cannot ship a feature. Somewhere between those two there is a length of job it stops being able to finish, and that length is a fact you can measure rather than argue about.

METR is an independent organisation that runs those measurements. They are not a lab. They test models that labs give them access to, and they publish their method.

That method has three parts.

- They take tasks that **human professionals have been timed on**, so every task has a human duration attached.
- They run frontier agents on those tasks, on their own, with no person helping.
- They find the **task length at which an agent succeeds half the time**. That length is the agent's time horizon.

One warning before you guess. The tasks are software and research-engineering tasks. They are not tasks in general.

*The framing and questions on this page were written by Claude, an AI, and reviewed by a human. The reading itself is the authors' own work.*

#### Question
content::
\## Guess the length, then guess what moves it

Two answers, before you open the reading.

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
- No correction of the number.

#### Article
source:: [[../articles/metr-measuring-ai-ability-to-complete-long-tasks]]
to:: s stakes, both in terms of potential benefits and potential risks.

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

---
id: '327430c4-be7a-48f7-a75f-bcdbefe19c01'
reading_minutes: 40
tutor_minutes: 20
title: Fun with +12 OOMs of Compute
tldr: Before arguing about when AI arrives, find out what your own model says compute can buy. A thought experiment with a magic wand, and a timer.
summary_for_tutor: "Administers Daniel Kokotajlo's own exercise from Fun with +12 OOMs of Compute rather than inventing a parallel one. Sequence: frame, then his hypothetical (the Compute Fairy grants twelve orders of magnitude of compute) read up to and stopping at his exercise, then the student does the exercise under a real five-minute timer, then his five answers (OmegaStar, Amp(GPT-7), Crystal Nights, Skunkworks, Neuromorph), then a diff of their list against his, then his Question Two payoff (his 90 percent, inside view 99, against Ajeya's 50), then the student commits to their own number with named movers. The tutor must not leak his five answers during the attempt beat. The design point is that the exercise probes the student, not the future."
authors:
  - Lauren+Claude
---
#### Text
content::
\## Remove a bottleneck and see what your model predicts

Let's start in the middle. If you've already got a model of how something moves - a description of what leads to what, with numbers given for how much each step leads to another - then there will typically be some bottleneck: a part of the process that 

The fastest way to find out what your model of AI progress is made of is to remove its favorite bottleneck and watch what it predicts. Daniel Kokotajlo's question, in his words: "Can we get TAI just by throwing more compute at the problem?" His method is a magic wand: grant 2016's researchers twelve extra orders of magnitude of compute, and ask what gets built. This is not a forecast. It is a probe, and the thing it probes is you: what do you believe compute buys? He wrote the exercise into the article himself. You will struggle a little here; that is the point.

A few translations before you read, because the article talks in units it never introduces. *Compute* is the total number of calculations spent building an AI, treated like a fuel budget; it is counted in FLOP[^flop] and written in powers of ten, where 10^23 means a 1 followed by 23 zeros. One *order of magnitude* (OOM) is a factor of ten, so +12 OOMs means a trillion times more, not twelve times more. And *TAI*, transformative AI, is AI that changes the world at least as much as the industrial revolution did; the article defines it properly later.

[^flop]: One floating-point operation: a single arithmetic step, one multiply or one add, done by a computer. Totals like 10^23 FLOP are the whole computing bill for training an AI system.

#### Article
source:: [[../articles/kokotajlo-fun-with-12-ooms-of-compute]]
from:: *In 2016 the Compute Fairy visits Earth and bestows a blessing:
to:: think about fun things that could be built in this scenario.

#### Question
content::
\## His exercise, administered

Kokotajlo's own instruction: "I encourage you to stop reading, set a five-minute timer, and think about fun things that could be built in this scenario." By "fun" he means "powerful." He asked readers to post answers in the comments; for you, this box is the comments. A list that feels hard to produce is exactly the data this collects. Set a real five-minute timer. List the most powerful things you think AI projects could build in the Compute Fairy world, and for each, one line on why compute was the thing holding it back.

max-time:: 8:00

assessment-instructions:: The student is mid-exercise. They have read the hypothetical but NOT the author's answers, which come next in this lens.

Do not supply any of the author's five answers (OmegaStar, Amp(GPT-7), Crystal Nights, Skunkworks, Neuromorph) and do not steer toward them. Leaking them destroys the exercise.

This is their attempt, not a test. Use no grading language.

Look for: at least two concrete systems (not "better AI"), and a stated compute-to-capability mechanism for each.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise (great list, excellent ideas, well done).

What to do in your single reply:
1. Acknowledge what they built, naming one or two of their own items specifically.
2. If they wrote fewer than two concrete systems, or gave no mechanisms, ask once for the missing piece.
3. Then tell them to continue to the author's answers.

This is a one-turn response.

#### Article
from:: Below are my answers, listed in rough order of how 'fun' they seem to me.
to:: Maybe we'll eventually find something intelligent, even if it lacks the memories and personality of the original scanned human.

#### Question
content::
\## The diff

Put your list next to his five: OmegaStar, Amp(GPT-7), Crystal Nights, Skunkworks, Neuromorph. Which of his {--{"author":"AI","timestamp":1787288414730}@@did you touch, --}{++{"author":"AI","timestamp":1787288414730}@@five is close to something on your list, ++}even {--{"author":"AI","timestamp":1787288414730}@@partially?--}{++{"author":"AI","timestamp":1787288414730}@@if not identical?++} Which one surprised you {--{"author":"AI","timestamp":1787288414730}@@most, and what does--}{++{"author":"AI","timestamp":1787288414730}@@most? Name++} the{--{"author":"AI","timestamp":1787288414730}@@ surprise say--}{++{"author":"AI","timestamp":1787288414730}@@ assumption++} about {--{"author":"AI","timestamp":1787288414730}@@what your model thinks compute buys? Note one more thing: inside Crystal Nights he stops and says--}{++{"author":"AI","timestamp":1787288414730}@@compute you were making without noticing it. Kokotajlo hit a gap like this himself, inside Crystal Nights:++} Ajeya's estimate[^ajeya] for that path {--{"author":"AI","timestamp":1787288414730}@@is--}{++{"author":"AI","timestamp":1787288414730}@@was++} 10^41 FLOP {--{"author":"AI","timestamp":1787288414730}@@while--}{++{"author":"AI","timestamp":1787288414730}@@but++} the fairy only gave him 10^35,{--{"author":"AI","timestamp":1787288414730}@@ and then--}{++{"author":"AI","timestamp":1787288414730}@@ so++} he {--{"author":"AI","timestamp":1787288414730}@@has--}{++{"author":"AI","timestamp":1787288414730}@@had++} to argue{--{"author":"AI","timestamp":1787288414730}@@ his way--} across the {--{"author":"AI","timestamp":1787288414730}@@gap. Did any item on--}{++{"author":"AI","timestamp":1787288414730}@@missing six orders of magnitude. Check++} your {++{"author":"AI","timestamp":1787288414730}@@own ++}list {--{"author":"AI","timestamp":1787288414730}@@have--}{++{"author":"AI","timestamp":1787288414730}@@for the same thing:++} a {--{"author":"AI","timestamp":1787288414730}@@hidden gap like that, an order-of-magnitude debt--}{++{"author":"AI","timestamp":1787288414730}@@place where you needed more compute than++} you {--{"author":"AI","timestamp":1787288414730}@@didn't price? Name it if--}{++{"author":"AI","timestamp":1787288414730}@@actually had, and did not say++} so.

[^ajeya]: Ajeya Cotra, the researcher whose compute-requirements report the article argues with; the article's final section introduces her model properly.

assessment-instructions:: The student has their own list and has now read the author's five answers.

The skill being practiced is honest diffing, not evaluation of the author.

Maximum 2 tutor turns. Keep an internal turn counter.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise.

What to do in each reply:
1. Reward a specific comparison: "his X was not on my list because I assumed Y" is the target shape.
2. Reward a student who finds an order-of-magnitude debt in their own entry.
3. Push back once if the answer only praises or only dismisses the author's list without comparing it to their own.
4. The Crystal Nights caveat (10^41 needed against 10^35 available) is in the text they just read. If they claim the author ignored feasibility, point them back to it rather than defending him.

After 2 tutor replies, close the phase and send them on.

#### Article
from:: ## Question Two: In this hypothetical, what's the probability that TAI appears by end of 2020?
to:: your median should be roughly 10 years earlier than hers, all else equal: 2040-ish rather than 2050-ish.

#### Question
content::
\## Your number

His answer to "probability that TAI appears in the Compute Fairy world" is 90%, and he shows his work: inside view[^inside] 99, discounted for unknown unknowns and deference. Ajeya's distribution puts its median[^median] at the 10^35 mark, which he reads as her answering 50%.

[^inside]: Your inside view is the estimate you get by reasoning through this case's specific details. Its partner, the outside view, asks how cases like this usually turn out. His 99 is pure inside view; the drop to 90 is humility about everything the inside view can't see.
[^median]: A probability distribution spreads your confidence across all the possible values instead of naming one. Its median is the halfway marker: half your probability sits below it, half above. That is why a median at 10^35 reads as calling it 50/50 that 10^35 is enough.

Now yours: give your probability as a percentage, name which of the five answers moves it most, and state one thing you could learn in the next year that would move your answer by twenty percentage points. If nothing could, say so and say what that means about the number.

assessment-instructions:: The student has read the author's Question Two, his 90 percent, and the comparison with Ajeya's 50 percent. They are now committing to their own number.

Up to 3 tutor turns, then offer to continue or close.

The pass bar is: a number, plus which of the five scenarios carries it, plus a concrete thing learnable within a year that would move it twenty points. A number with no named movers falls short of the bar. Exception the student-facing text explicitly offers: "nothing could move me, and here is what that means about the number". A thoughtful version of that meets the bar; engage with what they say an unmovable number is tracking rather than demanding movers anyway.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise.
- If the answer is vague, ask for precision.

What to do in each reply:
1. Do NOT argue the student toward any particular number, including the author's. Argue them toward ownership of theirs.
2. "90% because he said 90%" gets exactly one push: whose inside view produced that number, and what is yours?
3. If they cannot name anything that would move them twenty points, take that seriously and ask what an unmovable number is tracking.

On close: tell them their number gets revisited at module end, and give a brief calibration on what they have solid and what is still borrowed.

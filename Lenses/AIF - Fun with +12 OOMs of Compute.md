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
\## Remove a bottleneck and see what a model predicts

Let's start in the middle. Let's say you've already got a model of how something moves: a description of what leads to what, with numbers given for how much each step leads to another. Usually, there will be some bottleneck, some part of the process that the other steps wait for.

Most such descriptions of AI progress depend heavily on the amount of compute: the amount of math was done by the computer running the software which makes the AI.

So here we'll have you read Daniel Kokotajlo's article. He's looking for what happens when you run very large programs which try to find capable behaviors in different ways.

You probably won't understand everything he's saying at first, so try to guess what each thing means. In particular, he assumes you know what techniques for making AIs were common in 2016 - most of us don't have that memorized either. Follow what you can, and look for what's confusing to you. When you notice something confusing, consider whether it could turn out to be a disagreement or if it's purely something you don't know.

Let's give you some basic definitions:

**Compute**: total number of steps (addition, multiplication, compare, etc) used in training the AI. (For most AIs, the vast majority of steps are multiplication.)

**FLOP**: technically "**FL**oating-point **OP**eration", this just means an arithmetic step.

**OOM**: **O**rder **O**f **M**agnitude, a factor of ten. 10 is one order of magnitude more than 1. Typically written in exponential notation: 10^3 = 1000, and 10^4 = 10,000.

**TAI**: **T**ransformative **A**rtificial **I**ntelligence, which here refers to any piece of software that changes the world at least as much as the industrial revolution did.

Later articles will build up more of the technical details. Once again, the purpose of reading things out of order is to confuse you enough that your subconscious starts to know what to be curious about.

#### Article
source:: [[../articles/kokotajlo-fun-with-12-ooms-of-compute]]
from:: *In 2016 the Compute Fairy visits Earth and bestows a blessing:
to:: think about fun things that could be built in this scenario.

#### Question
content::
\## His exercise

Let's pause the article to give you a text box. Reminder: his use of the word "fun" is a bit sarcastic - you could just as well say "dramatic" or "powerful".

Before you read, what do you expect happens when you make the kinds of AI/ML software that were used in 2016 a trillion times larger? If it's hard, say so - you'll get a reply from the Tutor, and they'll give you some degree of hints.

Set a 5 minute timer if you've got one handy. Your phone will do nicely. Think, but don't overthink.
{>>{"author":"lauren (chrome@what)","timestamp":1787741570026}@@we should have a timer here<<}

max-time:: 8:00

assessment-instructions:: The student is mid-exercise. They have read the hypothetical but NOT the author's answers, which come next in this lens.

Do not supply any of the author's five answers (OmegaStar, Amp(GPT-7), Crystal Nights, Skunkworks, Neuromorph).

This is a pre-test. Use no grading language.

Instead, give hints about how to improve their thinking - what might the missing components be that they should be looking for?

You should look for them to describe: at least two concrete systems (not "better AI"), and a stated compute-to-capability mechanism for each.

If their answers are too vague to evaluate, propose something slightly more specific. (Eg, a student who says "They make a smarter youtube recommender" should get a reply like "Ah, but how do they ")

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm, knowing, socratic, leading-questions. Focus on questions that invite them to sit back and ponder as they read, not to reply with their answer.
- Do not over-validate. Avoid generic praise (great list, excellent ideas, well done).

What to do in your single reply:
1. Acknowledge what they described, naming one or two of their own items specifically.
2. If they wrote fewer than two concrete systems, or gave no mechanisms, ask once for the missing piece, but without expectation of followup.
3. Then tell them to continue to the author's answers.

This is a one-turn response.

#### Article
from:: Below are my answers, listed in rough order of how 'fun' they seem to me.
to:: Maybe we'll eventually find something intelligent, even if it lacks the memories and personality of the original scanned human.

#### Question
content::
\## The diff

Consider his five, and consider your answer from above. Answer three to five of these:

- What's similar?
- What's different?
- What techniques of estimation did he use that you didn't?
- Where do you think he might still be wrong?
- What confused you, and why?

assessment-instructions:: The student has their own list and has now read the author's five answers.

The skill being practiced is accurate diffing and evaluation of the claims.

Maximum 2 tutor turns. Keep an internal turn counter.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct.
- Do not over-validate. Avoid generic praise.

What to do in each reply:
1. Reward a specific comparison: "his X was not on my list because I assumed Y" is the target shape.
2. Reward a student who finds an order-of-magnitude debt in their own entry.
3. Push back once if the answer only praises or only dismisses the author's list without comparing it to their own.

After 2 tutor replies, close the phase and send them on.

#### Article
from:: ## Question Two: In this hypothetical, what's the probability that TAI appears by end of 2020?
to:: your median should be roughly 10 years earlier than hers, all else equal: 2040-ish rather than 2050-ish.

#### Question
content::
\## Give a number

Now you give a number: given a trillion times more compute than was available in 2016, how likely is TAI?

Note: we'll get into this in more detail later, but putting a probability on something that will happen only once is a bit of a subjective activity. One way to think about it: when asked for the probability of a claim C, then consider all worlds you think might be possible. In what percentage of them is C true? 

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

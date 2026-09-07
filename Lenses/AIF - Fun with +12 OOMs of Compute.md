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

{++{"author":"Lauren's AI","timestamp":1788772624795}@@max-time:: 6:00

++}assessment-instructions:: The student has their own list and has now read the author's five answers.

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
\## {--{"author":"Lauren's AI","timestamp":1788824490689}@@Give --}{++{"author":"Lauren's AI","timestamp":1788824490689}@@His number against yours

You committed to ++}a number{--{"author":"Lauren's AI","timestamp":1788824490689}@@

Now you give a number: **given a trillion times more compute than was available in 2016, how likely--}{++{"author":"Lauren's AI","timestamp":1788824490689}@@ before reading his. He says 90 percent, with an inside view near 99. Ajeya Cotra, whose model he++} is {--{"author":"Lauren's AI","timestamp":1788824490689}@@TAI?**--}{++{"author":"Lauren's AI","timestamp":1788824490689}@@arguing with, says 50.++}
{>>{"author":"lauren (chrome@what)","timestamp":1787818724284}@@TODO: need to move this question earlier in the article, before he gives his answer, and put the rest of the article in a spoiler block. also need to be able to put a timer so people can intentionally think for at least a certain amount of time.<<}
{--{"author":"Lauren's AI","timestamp":1788824495211}@@Note on **subjective probability**: we'll get into this in more detail later, but putting a probability on something that will happen only once is a bit of a subjective activity. One way to think about it: when asked for the probability of an event (such as TAI), consider all worlds you think could turn out to be possible. Then: in what percentage of the worlds you imagine does the event occur? That percentage is your probability.

When you answer, also write down something about what leads you to your number. If you can show--}{++{"author":"Lauren's AI","timestamp":1788824495211}@@Does++} your {--{"author":"Lauren's AI","timestamp":1788824495211}@@work in detail, that's ideal. If you wrote down disagreements above, you're looking for --}{++{"author":"Lauren's AI","timestamp":1788824495211}@@number move? Say by ++}how {--{"author":"Lauren's AI","timestamp":1788824495211}@@they lead you to imagine a particular set of possible-worlds.

 In particular, write down in what ways you're reasoning from an *inside view* or an *outside view*. An inside view is a description based on your understanding of mechanisms --}{++{"author":"Lauren's AI","timestamp":1788824495211}@@much, ++}and{--{"author":"Lauren's AI","timestamp":1788824495211}@@ processes. An *outside view* is a description based on comparisons to types of historical events that seem similar.

 (Hopefully by the end--}{++{"author":"Lauren's AI","timestamp":1788824495211}@@ name which++} of{--{"author":"Lauren's AI","timestamp":1788824495211}@@ the course you'll feel moderately comfortable with either!)

 Bonus: write down what change your probability by at least 20% in the next year. What would make at least 20%--}{++{"author":"Lauren's AI","timestamp":1788824495211}@@ his arguments moved it. If it does not move, say why none++} of{--{"author":"Lauren's AI","timestamp":1788824495211}@@ the possible-worlds you're imagining turn out to be impossible?--}{++{"author":"Lauren's AI","timestamp":1788824495211}@@ them did.++}

{++{"author":"Lauren's AI","timestamp":1788772627361}@@max-time:: 8:00

++}assessment-instructions:: The student {--{"author":"Lauren's AI","timestamp":1788824504217}@@has read the author's Question Two, his 90 percent, and the comparison with Ajeya's 50 percent. They are now committing--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@committed++} to their own{--{"author":"Lauren's AI","timestamp":1788824504217}@@ number.

Up to 3 tutor turns, then offer to continue or close.

The pass bar is: a number, plus which of--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@ probability in the previous question, BEFORE reading++} the {--{"author":"Lauren's AI","timestamp":1788824504217}@@five scenarios carries it, plus a concrete thing learnable within a year that would move it twenty points. A number--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@author's answer. They have now read his Question Two: his 90 percent, his inside view near 99, and his comparison++} with {--{"author":"Lauren's AI","timestamp":1788824504217}@@no named movers falls short of the bar. Exception the student-facing text explicitly offers: "nothing could move me, and here is what that means about the number". A thoughtful version of that meets the bar; engage with what they say --}{++{"author":"Lauren's AI","timestamp":1788824504217}@@Ajeya Cotra's 50 percent. They are saying whether their number moved.

Maximum 2 tutor turns. Keep ++}an{--{"author":"Lauren's AI","timestamp":1788824504217}@@ unmovable number is tracking rather than demanding movers anyway.--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@ internal turn counter.++}

Response length: {--{"author":"Lauren's AI","timestamp":1788824504217}@@120--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@80++} to {--{"author":"Lauren's AI","timestamp":1788824504217}@@200--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@150++} words. Short paragraphs only. No {--{"author":"Lauren's AI","timestamp":1788824504217}@@lists longer than 4 items.--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@lists.++}

Response style:
- {--{"author":"Lauren's AI","timestamp":1788824504217}@@Calm, rigorous,--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@Calm++} and {--{"author":"Lauren's AI","timestamp":1788824504217}@@educational.--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@direct.++}
- Do not over-validate. Avoid generic praise.{--{"author":"Lauren's AI","timestamp":1788824504217}@@
- If the answer is vague, ask for precision.--}

What to do in each reply:
1. Do NOT argue the student toward any {--{"author":"Lauren's AI","timestamp":1788824504217}@@particular --}number, including the author's. Argue them toward ownership of theirs.
2. {--{"author":"Lauren's AI","timestamp":1788824504217}@@"90%--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@Reward a stated direction with a named mover: "I moved from X to Y++} because {--{"author":"Lauren's AI","timestamp":1788824504217}@@he said 90%" gets exactly one push: whose inside view produced that number,--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@of his argument about Z" is the target shape. "I did not move, because his argument assumes W++} and {--{"author":"Lauren's AI","timestamp":1788824504217}@@what is yours?--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@I do not" meets the bar equally.++}
3. {--{"author":"Lauren's AI","timestamp":1788824504217}@@If they cannot name anything that would move them twenty points, take that seriously and ask what an unmovable number--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@A number that jumps to 90 "because he said 90" gets exactly one push: whose inside view produced that number, and what++} is {--{"author":"Lauren's AI","timestamp":1788824504217}@@tracking.--}{++{"author":"Lauren's AI","timestamp":1788824504217}@@yours?++}

On close: tell them their number gets revisited at module end, and give a brief calibration on what they have solid and what is still borrowed.

---
id: 'c3083a7a-5818-4975-ba77-b7cbf9d5b603'
title: "The Case Against Control"
tldr: A large part of the field works on containing AI rather than aiming it. Here is the argument that this is the wrong target.
summary_for_tutor: "Closes Unit 3. Introduces AI control in one paragraph, asks the student to predict the objection, then Wentworth's argument against control research. One mirror, no grade."
authors:
  - Claude
tags:
  - reading
---
#### Text
content::
\## Before you read

{--{"author":"Lauren's AI","timestamp":1786436046037}@@One more position, and it is--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@A large part of++} the {--{"author":"Lauren's AI","timestamp":1786436046037}@@one this course is least neutral about.

A large part of the safety field works on AI control. --}{++{"author":"Lauren's AI","timestamp":1786436046037}@@safety field works on AI control, and this lens is where you decide
what you think of it.

++}The idea: assume the system may be{--{"author":"Lauren's AI","timestamp":1786436046037}@@
--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@ ++}misaligned, and build the deployment so that it cannot{--{"author":"Lauren's AI","timestamp":1786436046037}@@ --}{++{"author":"Lauren's AI","timestamp":1786436046037}@@
++}cause a catastrophe even if it is.{--{"author":"Lauren's AI","timestamp":1786436046037}@@
Monitoring, restricted permissions, one--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@ Monitoring. Restricted permissions. One++} model checking{--{"author":"Lauren's AI","timestamp":1786436046037}@@ another. --}{++{"author":"Lauren's AI","timestamp":1786436046037}@@
another. Untrusted models given tasks where cheating can be detected. ++}Control does not try{--{"author":"Lauren's AI","timestamp":1786436046037}@@ --}{++{"author":"Lauren's AI","timestamp":1786436046037}@@
++}to{--{"author":"Lauren's AI","timestamp":1786436046037}@@
--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@ ++}make the system want the right thing. It tries to make wanting the wrong thing not
matter.

{--{"author":"Lauren's AI","timestamp":1786436046037}@@That--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@The case for it++} is {--{"author":"Lauren's AI","timestamp":1786436046037}@@a real and useful idea.--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@strong, and you should have it before you read the objections. Control
does not require solving alignment, which nobody knows how to do.++} It {--{"author":"Lauren's AI","timestamp":1786436046037}@@is also a patch--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@applies to systems
we can build now++} rather than {++{"author":"Lauren's AI","timestamp":1786436046037}@@to systems we hope to understand later. Its measures are
testable: you can red-team ++}a {--{"author":"Lauren's AI","timestamp":1786436046037}@@repair, --}{++{"author":"Lauren's AI","timestamp":1786436046037}@@monitoring setup ++}and {--{"author":"Lauren's AI","timestamp":1786436046037}@@a patch does--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@count the failures, which is more than++}
{--{"author":"Lauren's AI","timestamp":1786436046037}@@not maintain itself. Read --}{++{"author":"Lauren's AI","timestamp":1786436046037}@@most safety proposals can offer. And if the first systems capable of serious harm are
only somewhat superhuman, containing them may be enough to get useful work out of them,
including work on ++}the {--{"author":"Lauren's AI","timestamp":1786436046037}@@argument against it--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@alignment problem itself. Greenblatt++} and {--{"author":"Lauren's AI","timestamp":1786436046037}@@decide--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@Shlegeris make this case
at length in "The case++} for {--{"author":"Lauren's AI","timestamp":1786436046037}@@yourself.--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@ensuring that powerful AIs are controlled".++}

{++{"author":"Lauren's AI","timestamp":1786436046037}@@Two objections follow. Read them as arguments to weigh, not as the verdict.

++}#### Question
content::
\## Your turn first

{--{"author":"Lauren's AI","timestamp":1786436046037}@@Suppose containment works. The system is watched, restricted, and checked by other
systems, and it cannot take any single catastrophic action.--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@Do not argue for or against control in general. Both sides of that are easy, and neither
teaches you much.

Write the conditions instead.++}

Write two or three {--{"author":"Lauren's AI","timestamp":1786436046037}@@sentences. What problem does --}{++{"author":"Lauren's AI","timestamp":1786436046037}@@sentences naming what has to be true about a situation for control to
be the right strategy in it. Capability level, how long the containment has to hold, who
maintains it, what the system is being asked to do. Be concrete enough ++}that {--{"author":"Lauren's AI","timestamp":1786436046037}@@leave completely unsolved?--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@somebody
could check whether a real deployment meets your conditions.++}

Then write one more {--{"author":"Lauren's AI","timestamp":1786436046037}@@line. What does--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@line, and this is++} the {--{"author":"Lauren's AI","timestamp":1786436046037}@@containment itself cost, and who pays it?--}{++{"author":"Lauren's AI","timestamp":1786436046037}@@harder half. Name one thing that gets WORSE
because control is in use. Not a cost in money or effort. Something else we wanted, which
becomes harder to get once containment is in place.++}

assessment-instructions::
CONTEXT YOU NEED. You do not have the rest of this course, so here is the situation.

This is the last lens of Unit 3, in a course about AI futures for newcomers. The student
has NOT read the article yet. The article is "The Case Against AI Control Research" by
John Wentworth, and it is in your context.

The student has just been given a one-paragraph description of AI control and asked what
containment leaves unsolved.

Note on the course's own position, so you can hold it lightly. This course treats control
as useful but temporary: it constrains a system without changing what the system is
aimed at, so the underlying problem persists and the constraint has to be maintained
forever. The course does not treat that as settled, and a student who argues control is
sufficient is doing the exercise correctly.

WHAT WENTWORTH ARGUES. For your reference only. Do not deliver it.
Roughly: the failure that kills us is not an early system escaping its box. It is that we
never solve alignment for the systems that come after, and control research mostly does
not help with that. It can even hurt, by making people feel safe enough to proceed.

YOUR TASK, in order.
1. Say what their answer implies about what control is FOR. Buying time, preventing a
   specific harm, or something else.
2. Ask one question about their cost answer. Costs worth pushing on: the work the system
   is prevented from doing well, the people who have to maintain the containment, and
   what happens when attention moves on.
3. If they said containment solves the problem outright, do not correct them. Ask what
   has to stay true for that to keep holding, and for how long.

Do not grade. Do not score. Do not praise.

Write 60 to 110 words. Short paragraphs. No lists.

max-time:: 4

#### Article
source:: [[../articles/wentworth--the-case-against-ai-control-research]]

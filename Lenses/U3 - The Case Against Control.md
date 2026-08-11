---
id: 'c3083a7a-5818-4975-ba77-b7cbf9d5b603'
title: "The Case Against Control"
tldr: A large part of the field works on containing AI rather than aiming it. Decide when that is the right move and what it costs.
summary_for_tutor: "Closes Unit 3. States the case FOR control fairly, then asks the student to name the conditions under which control is right and one thing it makes worse. Two short critical readings follow. One mirror, no grade."
authors:
  - Claude
tags:
  - reading
---
#### Text
content::
\## Before you read

A large part of the safety field works on AI control, and this lens is where you decide
what you think of it.

The idea: assume the system may be misaligned, and build the deployment so that it cannot
cause a catastrophe even if it is. Monitoring. Restricted permissions. One model checking
another. Untrusted models given tasks where cheating can be detected. Control does not try
to make the system want the right thing. It tries to make wanting the wrong thing not
matter.

The case for it is strong, and you should know it before you read the objections. Control
does not require solving alignment, which nobody knows how to do. It applies to systems
we can build now rather than to systems we hope to understand later. Its measures are
testable: you can red-team a monitoring setup and count the failures, which is more than
most safety proposals can offer. And if the first systems capable of serious harm are
only somewhat superhuman, containing them may be enough to get useful work out of them,
including work on the alignment problem itself. Greenblatt and Shlegeris make this case
at length in "The case for ensuring that powerful AIs are controlled".

Two objections follow. Read them as arguments to weigh, not as the verdict.

*The framing and questions on this page were written by Claude, an AI, and reviewed by a human. The readings themselves are the authors' own work.*

#### Question
content::
\## Write the conditions

Do not argue for or against control in general. Both sides of that are easy, and neither
teaches you much.

Write the conditions instead.

Write two or three sentences naming what has to be true about a situation for control to
be the right strategy in it. Capability level, how long the containment has to hold, who
maintains it, what the system is being asked to do. Be concrete enough that somebody
could check whether a real deployment meets your conditions.

Then write one more line, and this is the harder half. Name one thing that gets WORSE
because control is in use. Not a cost in money or effort. Something else we wanted, which
becomes harder to get once containment is in place.

assessment-instructions::
CONTEXT YOU NEED. You do not have the rest of this course, so here is the situation.

This is the last lens of Unit 3, in a course about AI futures for newcomers. The student
has NOT read the articles yet. Two are attached, and both criticise AI control: John
Wentworth's "The Case Against AI Control Research" and Jan Kulveit's short "AI Control
May Increase Existential Risk". Both are in your context.

Before the question, the lens gave the student a FAIR statement of the case FOR control,
including that it does not require solving alignment, that its measures are testable, and
that contained systems might do useful safety work.

The student was asked for the CONDITIONS under which control is the right strategy, and
for one thing that gets worse because of it. They were told explicitly not to argue for
or against control in general.

THE COURSE'S POSITION, which you should hold lightly and never deliver as doctrine. This
course treats control as useful but temporary: it constrains a system without changing
what the system is aimed at, so the problem persists and the constraint must be
maintained indefinitely. The course does NOT think that makes control worthless. A
student who argues that control is the right thing to do right now is making a serious
argument, not a mistake.

FOR YOUR REFERENCE ONLY. Do not deliver these.
- Wentworth's central section is titled "The Median Doom-Path: Slop, not Scheming". His
  argument is that the likely way we lose is not an early system scheming and escaping,
  but slop: work that looks fine and is not, accumulating until nobody can tell. Scheming
  by early AIs is, in his words, "a relatively small slice of the AI X-risk probability
  mass", so control research aimed at it is low value rather than actively harmful. Do
  NOT tell the student that Wentworth says control backfires. He does not say that.
- Kulveit's piece is short and argues that control can increase risk rather than lower it.
- One cost worth having in mind: a contained system may be worse at the work we want from
  it, including alignment research, because containment restricts exactly the autonomy
  that makes such work good. Do not hand this to the student. If they have not found it,
  ask instead what the containment stops the system from doing.

YOUR TASK, in order.
1. Test their conditions for CHECKABILITY. Could somebody look at a real deployment and
   say whether it meets them? If the conditions are vague, ask for one that is not.
2. Ask how long their conditions have to keep holding, if they did not say.
3. On the thing that gets worse: if they named only money or effort, push once for
   something else. If they named something real, ask who would notice when it happened.

Do not grade. Do not score. Do not praise. A student who concludes that control is
correct has done this exercise properly.

Write 60 to 110 words. Short paragraphs. No lists.

max-time:: 6

#### Article
source:: [[../articles/wentworth--the-case-against-ai-control-research]]

#### Article
source:: [[../articles/kulveit--ai-control-may-increase-existential-risk]]

---
id: 'c3083a7a-5818-4975-ba77-b7cbf9d5b603'
title: "The Case Against Control"
tldr: A large part of the field works on containing AI rather than aiming it. {--{"author":"Lauren's AI","timestamp":1786436149372}@@Here --}{++{"author":"Lauren's AI","timestamp":1786436149372}@@Decide when that ++}is the {--{"author":"Lauren's AI","timestamp":1786436149372}@@argument that this is the wrong target.--}{++{"author":"Lauren's AI","timestamp":1786436149372}@@right move and what it costs.++}
summary_for_tutor: "Closes Unit 3. {--{"author":"Lauren's AI","timestamp":1786436149372}@@Introduces AI control in one paragraph,--}{++{"author":"Lauren's AI","timestamp":1786436149372}@@States the case FOR control fairly, then++} asks the student to {--{"author":"Lauren's AI","timestamp":1786436149372}@@predict--}{++{"author":"Lauren's AI","timestamp":1786436149372}@@name++} the {--{"author":"Lauren's AI","timestamp":1786436149372}@@objection, then Wentworth's argument against control research.--}{++{"author":"Lauren's AI","timestamp":1786436149372}@@conditions under which control is right and one thing it makes worse. Two short critical readings follow.++} One mirror, no grade."
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
has NOT read the {--{"author":"Lauren's AI","timestamp":1786436103805}@@article--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@articles++} yet. {--{"author":"Lauren's AI","timestamp":1786436103805}@@The article is--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@Two are attached, and both criticise AI control: John
Wentworth's++} "The Case Against AI Control Research" {--{"author":"Lauren's AI","timestamp":1786436103805}@@by--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@and Jan Kulveit's short "AI Control++}
{--{"author":"Lauren's AI","timestamp":1786436103805}@@John Wentworth, and it is--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@May Increase Existential Risk". Both are++} in your context.

{--{"author":"Lauren's AI","timestamp":1786436103805}@@The student has just been given--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@Before the question, the lens gave the student++} a {--{"author":"Lauren's AI","timestamp":1786436103805}@@one-paragraph description--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@FAIR statement++} of {--{"author":"Lauren's AI","timestamp":1786436103805}@@AI control--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@the case FOR control,
including that it does not require solving alignment, that its measures are testable,++} and{--{"author":"Lauren's AI","timestamp":1786436103805}@@ --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@
that contained systems might do useful safety work.

The student was ++}asked {--{"author":"Lauren's AI","timestamp":1786436103805}@@what--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@for the CONDITIONS under which control is the right strategy, and++}
{--{"author":"Lauren's AI","timestamp":1786436103805}@@containment leaves unsolved.

Note on the course's own position, so--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@for one thing that gets worse because of it. They were told explicitly not to argue for
or against control in general.

THE COURSE'S POSITION, which++} you {--{"author":"Lauren's AI","timestamp":1786436103805}@@can--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@should++} hold {--{"author":"Lauren's AI","timestamp":1786436103805}@@it lightly. This --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@lightly and never deliver as doctrine. This
++}course treats control{--{"author":"Lauren's AI","timestamp":1786436103805}@@
--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@ ++}as useful but temporary: it constrains a system without changing{--{"author":"Lauren's AI","timestamp":1786436103805}@@ --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@
++}what the system is{--{"author":"Lauren's AI","timestamp":1786436103805}@@
--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@ ++}aimed at, so the{--{"author":"Lauren's AI","timestamp":1786436103805}@@ underlying--} problem persists and the constraint{--{"author":"Lauren's AI","timestamp":1786436103805}@@ has to--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@ must++} be{--{"author":"Lauren's AI","timestamp":1786436103805}@@ maintained
forever.--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@
maintained indefinitely.++} The course does {--{"author":"Lauren's AI","timestamp":1786436103805}@@not treat--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@NOT think++} that {--{"author":"Lauren's AI","timestamp":1786436103805}@@as settled, and a --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@makes control worthless. A
++}student who argues {++{"author":"Lauren's AI","timestamp":1786436103805}@@that ++}control is{--{"author":"Lauren's AI","timestamp":1786436103805}@@
sufficient is doing the exercise correctly.

WHAT WENTWORTH ARGUES. For your reference only. Do--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@ the right thing to do right now is making a serious
argument,++} not {--{"author":"Lauren's AI","timestamp":1786436729711}@@deliver it.
Roughly: the failure that kills us is not an early system escaping its box. It--}{++{"author":"Lauren's AI","timestamp":1786436729711}@@a mistake.

FOR YOUR REFERENCE ONLY. Do not deliver these.
- Wentworth's central section is titled "The Median Doom-Path: Slop, not Scheming". His
  argument is that the likely way we lose++} is {--{"author":"Lauren's AI","timestamp":1786436729711}@@that we
never solve alignment for the systems--}{++{"author":"Lauren's AI","timestamp":1786436729711}@@not an early system scheming and escaping,
  but slop: work++} that{--{"author":"Lauren's AI","timestamp":1786436103805}@@ come after, and --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@ ++}{++{"author":"Lauren's AI","timestamp":1786436729711}@@looks fine and is not, accumulating until nobody can tell. Scheming
  by early AIs is, in his words, "a relatively small slice of the AI X-risk probability
  mass", so ++}control research {--{"author":"Lauren's AI","timestamp":1786436729711}@@mostly does
not help with that. It can even hurt, by making people feel safe enough to proceed.

YOUR TASK, in order.
1. Say what their answer implies about what control is FOR. Buying time, preventing--}{++{"author":"Lauren's AI","timestamp":1786436729711}@@aimed at it is low value rather than actively harmful. Do
  NOT tell the student that Wentworth says control backfires. He does not say that.
- Kulveit's piece is short and argues that control can increase risk rather than lower it.
- One cost worth having in mind:++} a{--{"author":"Lauren's AI","timestamp":1786436103805}@@
   specific harm, or something else.
2. Ask one question about their cost answer. Costs worth pushing on:--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@ contained system may be worse at the work we want from
  it, including alignment research, because containment restricts exactly++} the {++{"author":"Lauren's AI","timestamp":1786436103805}@@autonomy
  that makes such ++}work {--{"author":"Lauren's AI","timestamp":1786436103805}@@the system
   is prevented from doing well,--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@good. Do not hand this to++} the {--{"author":"Lauren's AI","timestamp":1786436103805}@@people who--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@student. If they++} have {--{"author":"Lauren's AI","timestamp":1786436103805}@@to maintain --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@not found it,
  ask instead what ++}the {--{"author":"Lauren's AI","timestamp":1786436103805}@@containment, and
   what happens when attention moves on.--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@containment stops the system from doing.

YOUR TASK, in order.++}
{--{"author":"Lauren's AI","timestamp":1786436103805}@@3. If they said containment solves the problem outright, do not correct them. Ask what--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@1. Test their conditions for CHECKABILITY. Could somebody look at a real deployment and++}
   {--{"author":"Lauren's AI","timestamp":1786436103805}@@has to stay true --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@say whether it meets them? If the conditions are vague, ask ++}for {++{"author":"Lauren's AI","timestamp":1786436103805}@@one ++}that {++{"author":"Lauren's AI","timestamp":1786436103805}@@is not.
2. Ask how long their conditions have ++}to keep holding, {--{"author":"Lauren's AI","timestamp":1786436103805}@@and --}{++{"author":"Lauren's AI","timestamp":1786436103805}@@if they did not say.
3. On the thing that gets worse: if they named only money or effort, push once ++}for{--{"author":"Lauren's AI","timestamp":1786436103805}@@ how long.--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@
   something else. If they named something real, ask who would notice when it happened.++}

Do not grade. Do not score. Do not praise.{++{"author":"Lauren's AI","timestamp":1786436103805}@@ A student who concludes that control is
correct has done this exercise properly.++}

Write 60 to 110 words. Short paragraphs. No lists.

max-time:: {--{"author":"Lauren's AI","timestamp":1786436103805}@@4--}{++{"author":"Lauren's AI","timestamp":1786436103805}@@6++}

#### Article
source:: [[../articles/wentworth--the-case-against-ai-control-research]]{++{"author":"Lauren's AI","timestamp":1786436123476}@@

#### Article
source:: [[../articles/kulveit--ai-control-may-increase-existential-risk]]++}

---
id: 7cf27f93-c438-4cee-b3c7-a882a4c0f45a
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Plan work by starting from an outcome you want and reasoning backward to what must happen first, and judge when working forward from what you can do now is the better approach.

## Requires

## Helpful first
- [[Theory of change]]

## Why it matters
In a young field like AI safety, it is easy to pick projects because they are ready to start rather than because they lead anywhere. Backchaining lets you check whether your work connects to an outcome you care about, and shows gaps that nobody is working on.

## Lenses
- [[../Lenses/swartz-theory-of-change-aaron-swartzs-raw-thought|Theory of Change and Backchaining]]: Aaron Swartz contrasts working forward from what you know how to do with working backward from the goal, asking "concretely, how does one achieve that?" at each step (2010).
- [[../articles/ross-what-i-want-you-to-do-when-i-tell-you-to-think-about-your-theory-of-change-more-carefully|Think About Your Theory of Change More Carefully]]: weak and strong AI safety project plans side by side, and why the strong ones backchain from what "winning" looks like to the step a project fills (September 2026).
- [Have an Unreasonably Specific Story About the Future (LessWrong)](https://www.lesswrong.com/posts/8t8jdTyq6X2B7D8St/have-an-unreasonably-specific-story-about-the-future): backchaining from reducing AI existential risk to two critical paths, then testing each link of a plan, with AI control and biorisk evaluations as examples (April 2026).
- [Backchaining in Strategy (LessWrong)](https://www.lesswrong.com/posts/DwoPGM8ytBCXrZpM7/backchaining-in-strategy): when backchaining fails, for long-term goals with many unknown unknowns, and why building general advantage can work better; the comments add ways to combine the two (February 2018).

## Tests

#### Question: Choice
id:: 2237e6f6-4383-4c5e-a7f7-715bd10565c9
content:: Which of these is an example of backchaining?
options::
- [x] Starting from "labs run safety evaluations before every release" and asking what must happen first
- Deciding to work on safer releases, then picking whichever evaluation your lab has the tools to build
- Listing your current skills and then looking for an AI safety problem that uses them
- Following up whichever experiment gave the most promising result last week
shuffle:: true

#### Question: Choice
id:: ff65d98a-bb77-4f55-8aa1-88f0efdd4519
content:: What failure is backchaining mainly meant to guard against?
options::
- [x] Choosing work because it is easy to start, not because it leads to the goal
- Spending so long planning that you never start any work
- Working on too many unrelated projects at the same time
- Trusting forecasts about the future more than the evidence supports
shuffle:: true

#### Question: Choice
id:: 9a73edc4-a7d6-4a11-a783-e32d8d6858e3
content:: In which situation is forward-chaining (starting from what you can do now and seeing where it leads) usually a better approach than backchaining?
options::
- [x] When the end state is too unclear to reason backward from
- When the goal is clear and there is plenty of time to reach it
- When many people are working toward the same well-defined goal
- When the first steps toward the goal are expensive to take
shuffle:: true

#### Question: Choice
id:: 829061c9-45d9-4ea0-b896-e98cf3679016
content:: A team is backchaining from the goal "AI developers do not deploy models that fail dangerous-capability evaluations." Which question should they ask next?
options::
- [x] What would need to be true just before that happens?
- Which of our current skills could help with AI safety?
- What project could we realistically start this week?
- Which kind of evaluation would be quickest for us to build?
shuffle:: true

#### Question: Choice
id:: b290c2e5-f961-4970-8c18-2823243d366e
content:: A team has backchained three steps back from their goal, but they still can't see exactly how today's work connects to the earliest of those steps. What is the most sensible next move?
options::
- [x] Start work that looks likely to help with that step, and keep refining the plan
- Hold off on any work until the plan reaches all the way back to today
- Drop backchaining and pick whatever project is easiest to start
- Switch to a smaller goal that they can already plan out in full
shuffle:: true

#### Question: Choice
id:: 8453ae4f-1d7a-4136-b759-40df5ef5d633
content:: Someone backchains from "humanity avoids catastrophe from advanced AI" and gets stuck, because most possible first steps seem equally far from that goal. What does this most likely suggest?
options::
- [x] They should break the goal into more concrete intermediate outcomes
- Backchaining is not a useful method for problems in AI safety
- They should pick whichever project is easiest to start right away
- The goal is too ambitious to be worth planning toward at all
shuffle:: true

#### Question: Choice
id:: dcc2108f-79ea-487d-af34-bf92fadb1a2c
content:: A theory of change is a stated chain from an action to the outcome it is meant to cause. How does backchaining relate to it?
options::
- [x] Backchaining is one way to build a theory of change, starting from the outcome
- A theory of change replaces backchaining once a project has started
- A theory of change is built forward from actions, so it rules out backchaining
- Backchaining checks a theory of change by running the project and measuring results
shuffle:: true

#### Question: Choice
id:: 25feddfb-5dea-4a91-b9cd-520130a32306
content:: A backchained plan has six steps in a row, and each step on its own looks fairly likely to work. What follows about the plan as a whole?
options::
- [x] It could easily fail, even though each step probably works
- It is about as likely to work as its least likely step
- It is more reliable than a short plan, because each step was thought through
- Its chance of working depends mainly on the step closest to the goal
shuffle:: true

#### Question: Choice
id:: e091cee2-1343-45f0-b434-136e618ece5d
content:: While backchaining, someone notices that two of the steps their goal depends on have nobody working on them. What is the most reasonable conclusion?
options::
- [x] Those steps may be high-value gaps, worth checking into
- Those steps can't matter much, or someone would already be on them
- The goal should be dropped because the plan has gaps
- Those steps should wait until all the others are done
shuffle:: true

#### Question: Open
id:: fa1ceae2-6ad3-4257-b1a2-dd93873728b0
content:: A researcher chooses an AI safety project because their lab already has the tools for it. Describe how backchaining would change the way they choose a project.
assessment-instructions:: Score out of 100. Full marks for saying they would first name the outcome they want (for example, a specific reduction in AI risk), work backward to what must happen before it, and pick a project that supplies a missing step, whether or not the tools are ready. 50 for only saying "start from the goal" without saying how the project is then picked.

#### Question: Open
id:: f59923ee-c764-446c-9674-55d8ed88b631
content:: Give one weakness or limit of backchaining as a way to plan work.
assessment-instructions:: Score out of 100. 100 for any one of: it needs a clear end state; it can miss opportunities that only show up by exploring forward; long chains multiply uncertainty so the full plan is unlikely to work as written; each backward step rests on assumptions about cause and effect that may be wrong; it can make plans seem more certain than they are. 40 for a vague answer such as "it's hard".

#### Question: Open
id:: c0f373b6-8c0f-48be-9e0c-c1578c7d425b
content:: You want to help reduce risk from AI but cannot describe the end state clearly enough to backchain from it. What could you do instead?
assessment-instructions:: Score out of 100. 100 for any one of: explore forward to learn what is possible and what matters; pick a nearer, concrete intermediate goal and backchain from that; choose actions that look useful across many possible end states, such as building skills or knowledge; talk to people with clearer pictures of the goal. 50 for "just start working" without saying why or how it helps.

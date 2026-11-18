---
id: 6d0841d3-3c0a-41e1-8a93-c04fc580f01d
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Tell apart terminal goals, pursued for their own sake, from instrumental goals, pursued as means to other goals, and explain why an agent's instrumental goals depend on its beliefs and circumstances.

## Requires
- [[Agents and goals]]

## Helpful first

## Why it matters
Several central arguments about AI risk rest on this distinction. Instrumental convergence says very different terminal goals call for similar instrumental ones, and the orthogonality thesis is a claim about terminal goals. Without the distinction, it is easy to misread what these arguments claim, or to guess an AI system's aims from a single behaviour.

## Lenses

## Tests

#### Question: Choice
id:: 7da55843-0188-4c8d-9319-0a49f9dba18e
content:: Maria saves money so she can buy a house, and she wants the house so her family has a safe place to live. For Maria, what kind of goal is saving money?
options::
- [x] An instrumental goal
- A terminal goal
- A constraint on her other goals
- A side effect of her other goals
shuffle:: true

#### Question: Choice
id:: 3de97461-20dc-4614-bd1a-a3553053df06
content:: Is whether a goal counts as terminal or instrumental a fact about the goal itself, or about the role it plays for a particular agent?
options::
- [x] The role it plays for a particular agent
- A fact about the goal itself

#### Question: Choice
id:: 7c37bc36-3b9c-4ae4-9938-bcb02e39f6dd
content:: A cleaning robot collects batteries purely as a means to keep cleaning. It is then wired into mains power, so batteries no longer help it clean. If collecting batteries was purely instrumental, what should the robot do?
options::
- [x] Stop collecting batteries
- Keep collecting batteries as before
- Stop cleaning
- Collect batteries more often
shuffle:: true

#### Question: Open
id:: 09d06197-4e14-40b8-aa5a-db32385c410a
content:: Why can't you always tell, just by watching an agent act, whether a goal it pursues is terminal or instrumental?
assessment-instructions:: Score out of 100. 100 for explaining that an agent valuing something for its own sake and one pursuing it as a means can act the same way in current circumstances; the difference shows only when circumstances change so the goal no longer serves its purpose. 50 for saying only that we can't see inside the agent's head, without the point about identical behaviour.

#### Question: Choice
id:: fb0bfd4d-ee1f-4a22-a570-e61d34507698
content:: The orthogonality thesis is often stated in terms of an agent's "final goals". What does "final goals" mean here?
options::
- [x] Terminal goals
- Instrumental goals
- The goals its developers set for it
- The goals it reaches last in a plan
shuffle:: true

#### Question: Choice
id:: a973af6d-27af-4dcf-bc9a-e676f304f0dc
content:: Instrumental convergence is the argument that agents with very different terminal goals would pursue similar instrumental goals. Why would different terminal goals lead to similar instrumental goals?
options::
- [x] Some means, like resources, help with a wide range of ends
- Agents tend to copy the goals of other agents
- Training tends to give AI systems the same terminal goals
- Terminal goals tend to drift towards the same ones over time
shuffle:: true

#### Question: Choice
id:: e4462ffd-4b27-404c-9f0b-6f0872179e18
content:: An AI agent's only terminal goal is to make as many paperclips as possible. Someone offers to change its terminal goal to making staples. Judged by its current goal, how would the agent rate this change?
options::
- [x] As bad, because it would lead to fewer paperclips
- As neutral, because it would still have a goal to pursue
- As good, because staples and paperclips are similar
- As good, if staples are easier to make than paperclips
shuffle:: true

#### Question: Open
id:: 6f9ed412-87ee-4e3f-b68b-3ba8e5761149
content:: Explain the difference between a terminal goal and an instrumental goal, and give one example of each for the same agent.
assessment-instructions:: Score out of 100. 100 for stating that a terminal goal is pursued for its own sake and an instrumental goal as a means to another goal, with a plausible example where the instrumental goal serves the terminal one (e.g. earning a degree to get a job one enjoys). 60 for correct definitions without a fitting example, or examples that don't connect.

#### Question: Choice
id:: f3879d67-7d2c-4c65-a441-a516956bb5ee
content:: Does calling one of an agent's goals "terminal" mean that the agent spends most of its effort on that goal?
options::
- [x] No
- Yes

#### Question: FillBlank
id:: 371927b1-bd36-4ca6-8a98-44bc1d221929
content:: A goal an agent pursues for its own sake, rather than as a means to some other goal, is called a {{terminal|final|intrinsic}} goal.

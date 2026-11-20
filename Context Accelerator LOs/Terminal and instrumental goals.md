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
- [[../Lenses/IABIED - QA - Terminal and Instrumental Goals|Terminal Goals and Instrumental Goals]]: a short definition of the two kinds of goal, and why very different terminal goals call for the same means ("you can't fetch the coffee if you're dead") (2025).
- [[../Lenses/AFSRA - Why Would AI Want to do Bad Things - Instrumental Convergence|Why Would AI Want to do Bad Things?]]: Rob Miles's 11-minute video on terminal versus instrumental goals, with examples from chess and money, and why a paperclip maximizer would refuse to have its goal changed to stamps.
- [[../Lenses/yudkowsky-terminal-values-and-instrumental-values|Terminal Values and Instrumental Values]]: the classic post on means and ends, showing that instrumental goals depend on what you believe and get dropped when circumstances change (the chocolate-and-earthquake example); the formal middle section can be skimmed (2007).

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
id:: fffd82a4-90b0-4611-bc9c-5f3d99a5a0f0
content:: Ana runs every day because she enjoys running. Ben runs every day only to stay healthy. For whom is running a terminal goal?
options::
- [x] Ana only
- Ben only
- Both of them
- Neither of them
shuffle:: true

#### Question: Choice
id:: 7c37bc36-3b9c-4ae4-9938-bcb02e39f6dd
content:: A cleaning robot collects batteries purely as a means to keep cleaning. It is then wired into mains power, so batteries no longer help it clean. If collecting batteries was purely instrumental, what should the robot do?
options::
- [x] Stop collecting batteries
- Keep collecting batteries as before
- Keep collecting batteries, but less often
- Collect batteries in place of cleaning
shuffle:: true

#### Question: Choice
id:: 7b48ff55-a1b8-4cb9-a6a7-12c5354e9c9e
content:: An AI agent's terminal goal is to keep a server running. Believing that nightly restarts prevent crashes, it restarts the server every night. It then learns the restarts cause crashes. Which goal should change?
options::
- [x] Its goal of restarting the server nightly
- Its goal of keeping the server running
- Both of these goals
- Neither, since its goals were fixed in training
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
id:: f7791930-493a-4b8d-85ec-7f2044fafcc9
content:: An AI agent spends most of its effort acquiring computing power. Does this show that acquiring computing power is one of its terminal goals?
options::
- [x] No
- Yes

#### Question: FillBlank
id:: 371927b1-bd36-4ca6-8a98-44bc1d221929
content:: A goal an agent pursues for its own sake, rather than as a means to some other goal, is called a {{terminal|final|intrinsic}} goal.

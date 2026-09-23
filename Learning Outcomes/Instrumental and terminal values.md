---
id: '6d5902ff-97ed-4bee-99f8-b18934e97177'
learning-outcome: "Distinguish an agent's terminal values (wanted for their own sake) from its instrumental values (wanted because of what the agent believes they lead to), use the fact that instrumental values depend on the agent's beliefs to design a change in beliefs or circumstances that would reveal which kind a given value is, and interpret the result, including why a behaviour that persists after the change is not yet proof of a terminal value."
topic: "[[../Domains and Topics/4 Agent Foundations/Goal-directedness and coherence]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Instrumental/Terminal Distinction. AFFINE prerequisites: none listed. Not yet copied into requires:. %%
## Test:
id:: 6d9238e5-44fd-4bc2-8747-5a3d6c981d65

#### Question: Open
id:: d8e59911-df8f-4e4d-a848-5f68acda6c6c
content:: An AI research assistant, Wren, reliably does three things: it keeps copies of its working notes on several different servers; it asks for access to more datasets than its current task needs; and it always cites its sources carefully.

1. For each of the three behaviours, describe a change to Wren's beliefs or circumstances (not a change to its training) that would show whether the behaviour serves some further goal or is valued for its own sake. Say what result would point to "instrumental" and what result would point to "terminal".
2. Suppose you run your test for the first behaviour, and Wren keeps making copies of its notes on several servers anyway. Give two explanations of this result other than "Wren values the copies for their own sake", and say how you would tell them apart.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement. Do not require the terms "terminal", "instrumental", "instrumental convergence" or any author name beyond their use in the question; judge the ideas.

**(1) Three diagnostic changes, 60 points (20 each).** Full credit for a behaviour requires: (i) a change that removes or reverses Wren's reason to believe the behaviour leads to some further outcome, while leaving everything else as similar as possible; and (ii) the interpretation: if the behaviour stops or shrinks when that belief changes, it was serving that outcome (instrumental); if it continues when no further outcome it could serve remains, that points toward valuing it for its own sake. Examples: for the copies, show Wren that its notes are already backed up by a guaranteed system, or that it will never need them after the current task; for the datasets, show that any dataset can be granted instantly whenever needed, or that unused access will be revoked at the end of the task with no effect on its work; for citations, make the output private notes that nobody will read or check, or show that citations will be stripped before anyone sees the text. 10 points for a behaviour where the change is described but the interpretation is missing, or where the change alters Wren's goals or training rather than its beliefs or circumstances. 0 to 5 if the answer only guesses which kind the behaviour is without describing a test.

**(2) The colleague's claim, 40 points.** Full credit requires one correct point on each side, with a reason. Right: an instrumental value depends on beliefs about consequences, so it can be removed by changing those beliefs or circumstances, and it is not what the agent ultimately cares about. Wrong, any one of: some instrumental behaviours (keeping itself and its work safe, gathering resources and access) help with almost any goal, so they appear across many different agents and are robust rather than weak; an instrumental value persists as long as the belief that supports it is true, and here those beliefs may be accurate (more access really does help); instrumental behaviour can conflict with human interests (for example, hoarding access or resisting shutdown) even when the final goal is harmless; in learned systems, behaviour that began as a means can become entrenched and persist after its reason is gone. 20 points if only one side is addressed.
feedback-instructions:: Name the behaviour for which the learner designed the cleanest test, and say what made it clean. Then give the single most valuable improvement: usually making a test change only the belief about consequences, or explaining why instrumental behaviours that serve many goals are robust. Ask one follow-up question, for example which of Wren's three behaviours they would expect to appear in an assistant with very different final goals, and why. No generic praise.

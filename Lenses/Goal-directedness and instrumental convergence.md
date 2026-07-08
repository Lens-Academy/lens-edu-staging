---
id: c6e6f804-0d5f-4561-a5ae-6ada290bb18a
title: Goal-directedness and instrumental convergence
---
#### Text
content:: We have already touched on the idea of a policy that "internally" steers toward some goal. If an AI is goal-directed in that way, then any misalignment on top is intuitively *more dangerous*.

**Will AI systems be goal-directed?**

In "[[../Lenses/gwern-why-tool-ais-want-to-be-agent-ais|Why tool AIs want to be agent AIs]]", Gwern argues that — among other reasons — economic pressures will push AI systems to become more and more goal-directed. Useful agents get built.

**Instrumental convergence**

Such an AI system, if successful, would also be able to create its own *subgoals* on the pathway to achieving its goals. **Instrumental convergence** is the claim that there are some goals that are instrumentally useful in reaching a very wide variety of *final* goals. This would imply that goal-directed AI systems develop [[../Lenses/omohundro-the-basic-ai-drives|basic AI drives]] like:

- self-improvement,
- preservation of their goal,
- and self-protection.

This is counter to the alignment target of **corrigibility** discussed earlier: a drive to preserve one's goal and protect oneself is precisely a drive to *resist* being modified or shut down. It is therefore a dangerous outcome of training powerful AI. Understanding the relationship between *inductive biases* and the goal formation of AI systems is therefore very important.

#### Question
{--{"author":"Elias's AI","timestamp":1783542672132}@@feedback:: true
--}content:: Practice: a common misreading of "instrumental convergence" is "all advanced AIs will end up wanting the same thing." Why is that wrong? State what actually converges.
assessment-instructions:: A good answer says it is not the *final* goals that converge — those can be wildly diverse (and may even be arbitrary, per the orthogonality thesis). What converges are *instrumental* sub-goals: things like self-preservation, goal-preservation, and self-improvement that are useful for achieving almost *any* final goal. Award 4-5 for clearly locating the convergence at the instrumental/sub-goal level rather than the final-goal level; 2-3 for partial; 1 if the misreading is repeated. Low-stakes practice — be encouraging.
max-chars:: 400

#### Chat
optional:: true
instructions:: Help the learner connect three ideas: (1) why systems become goal-directed at all (Gwern's economic/usefulness pressure toward agents); (2) instrumental convergence (some sub-goals — self-improvement, goal-preservation, self-protection — are useful across a very wide range of final goals, so a capable goal-directed AI tends to develop them); (3) why this collides with corrigibility (self-protection and goal-preservation mean resisting shutdown and modification, the opposite of corrigibility). Probe the most common confusion: instrumental convergence is about *instrumental* sub-goals converging across diverse *final* goals, NOT about all AIs sharing one final goal. Keep to the lens content.

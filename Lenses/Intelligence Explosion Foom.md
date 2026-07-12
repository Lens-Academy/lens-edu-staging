---
id: 97a886d3-693a-4916-bd20-9c94a21aca96
summary_for_tutor: "Teaches why feeding a process's output back into its input does not automatically yield an intelligence explosion, drawing on Yudkowsky's 'Recursion' discussion. The excerpt works through optimizing compilers, which only make code run faster while leaving its input/output function unchanged (so gains top out, k<1), and EURISKO, a 1980s self-improving AI that could rewrite even its own metaheuristics yet still ran out of steam because it lacked the 'insight' that lets humans move quickly through a search space. It frames improvement as a causal tree in which changes closer to the root cascade further, concluding that a tool like a computer mouse 'isn't recursive enough.' Framing text adds an agricultural-surplus analogy (feedback compounds only if new input improves the output), and the tutor chat explores what optimization would have to target to foom, where speed and competence diverge, and whether intelligence is one variable or many separate skills."
title: "Recursion, Magic"
tldr: The agricultural revolution only happened because surplus grain produced more than enough to replant. If the yield had stayed flat, nothing would have changed. This article asks the same question about AI self-improvement — does it compound, or just run faster in place?
---
#### Text
content::
Getting to plug the outputs of a process back into the input does not necessarily lead to an explosion though. Consider the case of EURISKO.

#### Article
source:: [[../articles/recursion-magic]]
from:: "We have historical records aplenty"
to:: "recursive enough."

#### Text
content::
If the leftover grain only produced exactly the same amount of leftover grain on the next harvest, the agricultural revolution never would have happened. In order for positive feedback to occur, the new input needs to improve the output.
#### Chat
instructions::
TLDR of what the user just read:
An article that explains EURISKO, an optimising compiler, and examines why such a program, if plugged into itself recursively does not generate an infinite degree of program optimisation. The answers given are that the input-output behaviour is left unchanged. An optimised EURISKO might optimize a program faster than its predecessor, but it still outputs the same thing.  

topics to explore:
- What would the optimisation have to be pointed at to cause an intelligence explosion?
- Where do speed and competence start to diverge?
- How can the notion of fizzling or fooming be linked back to the metaphor of neutron multiplication?
- What does a sufficiently recursive computer mouse look like? Is there such a thing? 

This is a good stage to consider whether intelligence/competence is a collection of separate skills or a single variable which can easily serve as its own input. 
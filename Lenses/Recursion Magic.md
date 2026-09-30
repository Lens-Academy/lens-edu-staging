---
id: e79dd07a-e837-483f-8534-b53b86d509b4
reading_minutes: 10
tutor_minutes: 5
summary_for_tutor: {--{"author":"Elua's AI","timestamp":1790784382427}@@Covers--}{++{"author":"Elua's AI","timestamp":1790784382427}@@"Eliezer Yudkowsky on++} why self-improvement does not automatically produce an intelligence explosion. {--{"author":"Elua's AI","timestamp":1790784382427}@@References --}{++{"author":"Elua's AI","timestamp":1790784382427}@@An optimizing compiler run on its own source code produces ++}the {++{"author":"Elua's AI","timestamp":1790784382427}@@same output, only faster, and repeated passes converge (20%, 24%, 24.8%, topping out at 25%: k < 1). ++}EURISKO {--{"author":"Elua's AI","timestamp":1790784382427}@@case where recursive self-improvement produced diminishing returns. Establishes--}{++{"author":"Elua's AI","timestamp":1790784382427}@@(Douglas Lenat, 1980s) could modify its own heuristics and even the metaheuristics that modified them, yet it ran out of steam: its self-improvements did not spark enough further ones. Yudkowsky attributes this to a lack of 'insight', the abstract knowledge++} that {--{"author":"Elua's AI","timestamp":1790784382427}@@positive feedback requires--}{++{"author":"Elua's AI","timestamp":1790784382427}@@lets humans search efficiently. The takeaway for the tutor: recursion alone is not enough;++} each {--{"author":"Elua's AI","timestamp":1790784382427}@@iteration to--}{++{"author":"Elua's AI","timestamp":1790784382427}@@round must++} improve {++{"author":"Elua's AI","timestamp":1790784382427}@@what ++}the {--{"author":"Elua's AI","timestamp":1790784382427}@@output,--}{++{"author":"Elua's AI","timestamp":1790784382427}@@process can do,++} not {--{"author":"Elua's AI","timestamp":1790784382427}@@merely reproduce it.--}{++{"author":"Elua's AI","timestamp":1790784382427}@@just how fast it does it."++}
title: "Recursion, Magic"
# tldr: If a program can optimize code and you point it at its own code, do you get an ever-improving tower of optimizers? An early AI called EURISKO tried exactly this — and the result was surprisingly flat. This article explores why self-improvement doesn't automatically go exponential, and what would need to change.
---
#### Text
content::
Getting to plug the outputs of a process back into the input does not necessarily lead to an explosion though. Consider the case of EURISKO:

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
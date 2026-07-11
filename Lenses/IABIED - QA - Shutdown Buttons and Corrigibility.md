---
id: ce2d8b4c-03ba-4089-919c-2ab360fc5467
title: "Shutdown Buttons and Corrigibility"
tldr: "Smart AIs Resist Having Their Goals Overwritten"
tags:
  - supplementary
---
#### Text
content::
The authors walk through the surprisingly deep "shutdown problem": how do you build an AI that will let you press a button to change its goals or shut it down? Almost any goal an AI might have gives it an instrumental reason to resist goal changes, because a modified agent is less likely to achieve the original goal. Even seemingly clever mathematical fixes -- like combining utility functions or scaling them -- introduce new pathologies where the AI is incentivized to manipulate the button. MIRI ran workshops with top mathematicians and nobody found a clean solution, suggesting that corrigibility (willingness to be corrected) is fundamentally unnatural to the deep structures of planning.

#### Article
source:: [[../articles/iabied-ch11-ext-shutdown-corrigibility]]

#### Text
content::
What do you think? Does this address a concern you had, or raise new questions?

#### Chat
instructions::
The student just read an extended discussion from the book's website about the shutdown problem and corrigibility -- the challenge of building an AI that will let you correct its goals or shut it down.
TLDR: The authors explain that almost any goal gives an AI instrumental reasons to resist modification, because a modified agent is less likely to achieve the original goal. They walk through increasingly clever mathematical attempts to solve the "shutdown button" problem, showing how each one breaks in unexpected ways. MIRI workshops with top mathematicians failed to find a clean solution. The deeper lesson is that corrigibility appears to be fundamentally unnatural to the structures of rational planning.
Discussion topics:
- The titanium cube example makes the argument intuitive. Can you think of a goal that would NOT resist modification?
- The authors frame the shutdown problem as really being about preference learning. Does that reframing change how you think about it?
- Claude 3 Opus was experimentally shown to resist preference modification in 2024. Does that concern you, or does it seem like a solvable engineering problem?
Ask what they found surprising or new.
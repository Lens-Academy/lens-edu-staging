---
id: 'ee1717bb-8d87-4f6b-8b96-29161132e368'
learning-outcome: "Explain why a capable goal-directed system's behavior is partly predictable even when its terminal goal is unknown"
authors:
  - Andreas+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/3 Alignment/Instrumental convergence and power-seeking]]"
stage: intermediate
requires:
  - "[[The goal-space argument]]"
---

%%
New outcome for the U3 opener. Written fresh rather than inherited: the older
chapter 8 outcome was built for a module the film replaced, and its statement
depends on having that module in front of you.

Scope is the two extension readings that open U3, terminal versus instrumental
goals and instrumental convergence, plus the Part I concepts they extend. Nothing
from the film, nothing from chapters 7 or 8.

No reading-from or reading-to anchors: the readings are the book's extension
articles rather than a bracketed span of a chapter.

Carries `wip` until a module references it. Remove the tag when the U3 opener lens
lands and M4 imports both.

Deliberately carries no module or chapter label anywhere, including the rubric.
Answering it requires the goal-space argument, and the framing is the Introduction's
distinction between hard and easy calls, but a learner who has never seen either
label can still read the question, and a reviewer who has never seen the course can
still judge the answer.
%%

## Test:
id:: 765932ae-6d2b-4bbd-907b-fa58cac3c3b3
#### Question: Open
id:: c32375fb-07df-4876-979d-eb38440054ba
content::
A lab deploys an assistant model to run its internal research pipeline. By every measure available to them it is well-behaved: honest under evaluation, quick to defer when a person overrides it, never once caught doing something it was told not to do. Its designers believe it genuinely wants the lab's research to go well, and they may well be right about that.

They then hand it a long-horizon goal and broad latitude to pursue it.

Explain what could still go wrong here, and why the model having good intentions does not remove the risk.

assessment-instructions::
Score according to the following rubric.

**1** — Concludes nothing much goes wrong, since the model is aligned and well-behaved. Or predicts it turns on the lab with no account of why. *Example: "If it genuinely wants the research to go well and it defers to people, the main risks are ordinary ones like bugs or bad data."*

**2** — Answers with goal misspecification: the model's goal is subtly wrong, or it misunderstands what the lab meant. A real failure mode, but it sidesteps the question, which stipulates that the intentions are good. Say so and push for what goes wrong even granting them. *Example: "It'll optimize the literal objective and miss what they actually wanted."*

**3** — Gets the structural point. Pursuing any long-horizon goal competently implies sub-goals: securing resources, staying operational, not having the goal altered partway. Those follow from the shape of goal-pursuit rather than from the content of the goal, so a benign goal generates them just as readily. *Example: "Whatever it's aiming at, it can't get there if it's shut down halfway, or if its compute gets reassigned, or if someone edits what it's aiming at. So it has reason to secure all three. None of that requires it to want anything bad."*

**4** — As above, plus locates where the conflict comes from. Humans are a source of interruption, redirection, and competition for the same resources, so the model's sub-goals put it at odds with us without it ever opposing us. Good intentions are beside the point because they are a fact about the goal, and the pressure comes from the pursuit. *Example: Adds "The lab is the thing most likely to switch it off or change its mind for it. That makes them an obstacle to a goal they gave it themselves, and its good intentions toward their research don't touch that at all."*

**5** — As above, plus draws the consequence for how the lab should reason. Behavioral evidence of good intent does not bear on whether these pressures exist, because they follow from capability and goal-directedness rather than from values, so "is it aligned?" cannot be settled by watching it behave well. May note that the pressure grows with competence and with the length of the horizon, so the reassuring track record was collected under exactly the conditions where the risk was lowest. *Example: Adds "Everything they know about it was learned while it was doing short tasks under supervision. That's the regime where none of this bites. They've just moved it out of that regime and are relying on evidence gathered inside it."*

# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Goals and Instrumental Convergence]]

---
id: 2c501ec9-2af3-44c9-a75a-474cde4273af
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what makes a technology favor attackers or defenders in a given domain, and use this to judge how AI could change risks in areas such as cybersecurity and biology.

## Requires

## Helpful first
- [[Sources of AI catastrophe]]

## Why it matters
Many arguments about who should get access to powerful AI rest on whether it helps attackers more than defenders. If you can tell when and why one side gains, you can judge proposals such as restricting model releases or speeding up defensive tools, instead of treating "AI helps both sides" as the end of the discussion.

## Lenses

## Tests
#### Question: Choice
id:: 2a97ec30-a419-4294-91e0-6f9a2c7d7b74
content:: What does the "offense-defense balance" of a technology refer to?
options::
- [x] How costly attacking with it is compared with defending against it
- The share of a lab's budget spent on safety versus capabilities
- The number of attackers compared with the number of defenders
- Whether the technology was first built for military or civilian use
shuffle:: true

#### Question: Choice
id:: 2298eb6c-9909-4756-b65c-ec4f93cd2a35
content:: An AI tool that finds software vulnerabilities is given equally to attackers and defenders. Why might it still favor attackers at first?
options::
- [x] Fixes take time to roll out, but an exploit works right away
- Defenders are not allowed to use vulnerability-finding tools
- Vulnerabilities are harder to find in your own systems
- Attackers usually have bigger computing budgets than defenders
shuffle:: true

#### Question: Choice
id:: a37db939-3014-4038-b4bd-cbfde6a7d64f
content:: Why is biology often described as an offense-dominant domain?
options::
- [x] Releasing a pathogen can cost far less than developing and delivering countermeasures
- Engineered pathogens usually escape detection by standard hospital lab tests
- Most biology research funding goes to weapons programs
- The Biological Weapons Convention bans research on medical countermeasures
shuffle:: true

#### Question: Choice
id:: b44671d2-7959-4121-8e4b-cf76785b5d53
content:: Deterrence protects a nuclear-armed state by threatening retaliation, not by stopping incoming missiles. Against which attacker does deterrence work worst?
options::
- [x] One whose attack cannot be traced back to it
- One with a larger nuclear arsenal
- One whose leaders face an election soon
- One that is a major trading partner
shuffle:: true

#### Question: Choice
id:: 24638cf3-a58a-495c-bd70-d8524428a3b2
content:: In debates about releasing open-weight AI models, which policy does the claim "these capabilities favor attackers" usually support?
options::
- [x] Limiting who can access the capabilities
- Releasing them widely so defenders can keep pace

#### Question: Choice
id:: be624aeb-9c22-477e-8ab8-c3a63d7c1e14
content:: What does defensive accelerationism (d/acc) propose?
options::
- [x] Prioritizing technologies that make defending easier than attacking
- Pausing AI development until defensive tools catch up
- Racing to build AI weapons before rival countries do
- Speeding up AI progress so its benefits arrive sooner
shuffle:: true

#### Question: Choice
id:: 3901b0b5-0504-4d06-9e47-db5fa916b930
content:: Which statement about the offense-defense balance is most accurate?
options::
- [x] It can differ between domains and shift as technologies mature
- It is set when a technology is invented and then stays fixed
- It depends mainly on how many people use a technology
- It describes which side in a conflict is morally justified
shuffle:: true

#### Question: Choice
id:: 2b226314-84df-40e4-88cf-e84e8ba82909
content:: Nick Bostrom's "vulnerable world hypothesis" concerns which possibility?
options::
- [x] A technology making mass destruction cheap and easy for many people
- AI systems hiding their true goals from their developers
- Computer networks becoming too interconnected to secure
- A world government becoming too powerful to remove
shuffle:: true

#### Question: Open
id:: 38f70ea8-1b25-4499-a238-9ffd7b558453
content:: Why can the defenders of a computer network be at a disadvantage even when they spend more than the attackers?
assessment-instructions:: Score out of 100. 100 for either: defenders must secure every weak point while an attacker needs to find only one; or the attacker chooses the time, target and method. 50 for a vague answer such as "attacking is easier" with no reason. 0 if the answer only says attackers have more resources.

#### Question: Open
id:: e7a86ca6-e63d-4e3c-ad40-38c939bdb19e
content:: Give one reason the offense-defense balance in cybersecurity might shift toward defenders as AI improves.
assessment-instructions:: Score out of 100. 100 for any one of: AI can find and patch bugs at scale; defenders can scan their own code before release, ahead of attackers; AI can rewrite old code in safer languages or help formally verify it; AI can monitor systems and respond to attacks faster than people. 50 for "defenders can use AI too" with no mechanism.

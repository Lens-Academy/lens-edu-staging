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
- [[../Lenses/AI Safety Atlas - Risks - Misuse Risks|Misuse Risks]]: why biology is offense-dominant (a new virus costs about $100k, a vaccine over $1bn) and why AI may tilt cyber toward attackers; read the Bio Risk and Cyber Risk sections.
- [With $1 Cyberattacks on the Rise, Durable Defenses Pay Off (IEEE Spectrum)](https://spectrum.ieee.org/ai-cyberattacks-memory-safe-code-2676831574): AI makes finding bugs nearly free but fixing them stays costly, and memory-safe code and formal verification could help defenders (April 2026).
- [My techno-optimism (Vitalik Buterin)](https://vitalik.eth.limo/general/2023/11/27/techno_optimism.html): the essay that launched d/acc, sorting technologies by whether they favor attack or defense across physical, bio, cyber and info; read the section "d/acc: Defensive (or decentralization, or differential) acceleration" (November 2023).
- [The Vulnerable World Hypothesis (Nick Bostrom)](https://nickbostrom.com/papers/vulnerable.pdf): the "urn of inventions" argument that some technology may make mass destruction cheap and easy for many; read the sections from "Is there a black ball in the urn" through "Typology of vulnerabilities" (2019) (more advanced).

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
- Defenders already know where the weak points in their systems are
- The tool finds more bugs in new code than in old code
- Attackers usually have bigger computing budgets than defenders
shuffle:: true

#### Question: Choice
id:: a37db939-3014-4038-b4bd-cbfde6a7d64f
content:: Why is biology often described as an offense-dominant domain?
options::
- [x] A released pathogen spreads by itself, while countermeasures must be made and delivered to everyone
- Most new diseases arise in labs rather than in nature, so they are harder to predict
- Treaties prevent governments from stockpiling vaccines before an outbreak
- Biology research is usually kept secret, so defenders cannot learn from it
shuffle:: true

#### Question: Choice
id:: 5b8f5eae-d147-4d78-91bb-779946d926ac
content:: Nuclear deterrence works by threatening retaliation. Why might threatening retaliation protect poorly against AI-enabled cyberattacks or a deliberately released pathogen?
options::
- [x] It can be hard to identify who carried out the attack
- Retaliating against such attacks is banned by international law
- Such attacks cause too little harm to be worth deterring
- States cannot afford to retaliate against several attackers
shuffle:: true

#### Question: Open
id:: 40fae45b-c431-45e0-a3df-b652f817737e
content:: Someone argues: "An open-weight model helps attackers and defenders alike, so releasing it doesn't change the overall risk." What does this argument leave out?
assessment-instructions:: Score out of 100. 100 for explaining that equal access doesn't mean equal benefit, with a reason such as: the capability may help attackers more (attack is cheaper or needs one success); defenders take longer to adopt fixes or countermeasures; some harms can't be undone once done; released weights can't be recalled. 50 for saying "it may help one side more" with no reason. 0 for simply agreeing or disagreeing.

#### Question: Choice
id:: be624aeb-9c22-477e-8ab8-c3a63d7c1e14
content:: What does "d/acc", the approach Vitalik Buterin calls defensive (or decentralized, or differential) acceleration, propose?
options::
- [x] Prioritizing technologies that make defending easier than attacking
- Putting a single global body in charge of all advanced technology
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

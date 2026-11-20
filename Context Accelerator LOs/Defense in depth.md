---
id: f5cbe7dc-8818-4723-b835-402302dc6309
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how layering several independent safeguards reduces the chance of catastrophe, why the benefit depends on layers failing independently, and how this applies to combining alignment, control, monitoring and governance for AI.

## Requires

## Helpful first

## Why it matters
AI safety plans rarely rest on one technique; they stack training, evaluations, monitoring, security and regulation. Knowing why stacking helps, and when it doesn't, lets you judge whether a plan's layers really back each other up or would all fail against the same capable, deceptive system.

## Lenses
- [[../Lenses/AI Safety Atlas - Strategies - Socio-Technical Strategies|Socio-Technical Strategies]]: what defense in depth is, why independent layers multiply into strong protection, and why correlated layers or a capable adversary weaken it; read the opening and the "Defense-in-Depth" section (2026).
- [Swiss cheese model (Wikipedia)](https://en.wikipedia.org/wiki/Swiss_cheese_model): James Reason's model of accidents, where each safeguard has holes and harm gets through only when the holes in every layer line up; read the opening section.
- [[../Lenses/The case for ensuring that powerful AIs are controlled|The case for ensuring that powerful AIs are controlled]]: alignment and control as two lines of defense, so a scheming AI causes catastrophe only if both fail (2023).
- [Layered AI Defenses Have Holes (FAR.AI)](https://far.ai/news/defense-in-depth): how an attack that beats input filter, model and output filter one at a time broke a layered weapons-content safeguard, and how to keep layers from failing together (July 2025).

## Tests

#### Question: Choice
id:: ed3112e2-1279-4feb-91a4-e002574a23f9
content:: In the Swiss cheese model of safety, what do the holes in each slice of cheese stand for?
options::
- [x] Weaknesses that let a hazard get past that safeguard
- Hazards that the safeguard has successfully blocked
- Risks too small to need any safeguard
- Safeguards that have been removed from the system
shuffle:: true

#### Question: Choice
id:: adbe0990-12ea-4b55-b709-31d1ccc24b3a
content:: A lab says its three safeguards each miss 10% of dangerous actions, so together they miss only 0.1%. What must be true for that figure to hold?
options::
- [x] The safeguards rarely miss the same actions
- Each safeguard was tested on the same set of actions
- The safeguards are applied in a fixed order
- At least one safeguard is a governance measure
shuffle:: true

#### Question: Choice
id:: ce6a88b3-6dba-41fc-baa5-ac62296adc41
content:: In defense in depth, suppose the layers' failures are correlated: they tend to miss the same cases. How does the combined protection compare with what you get by multiplying each layer's miss rate?
options::
- [x] Weaker than the multiplied rates suggest
- Stronger than the multiplied rates suggest
- The same as the multiplied rates suggest
shuffle:: true

#### Question: Choice
id:: 173d52d3-14e2-46a6-b0eb-acbb980d3b4f
content:: Which pair of safeguards on an advanced AI model is most likely to fail on the same cases?
options::
- [x] Two similar behavioral tests run before release
- An interpretability check and a behavioral test
- Securing the model weights and an incident-reporting law
- Output monitoring and limits on who can access the model
shuffle:: true

#### Question: Choice
id:: 630600f0-71ff-4053-9def-b6f793216e1a
content:: In a defense-in-depth plan against misaligned AI, what role do AI control measures, such as monitoring by trusted models, play?
options::
- [x] A layer meant to catch harm if alignment training has failed
- A replacement for alignment training once control is reliable
- A test that shows the model is aligned before deployment
- A method for making the model's goals match the developer's
shuffle:: true

#### Question: Choice
id:: 3e9821b8-80f5-4dd8-836c-beac387caac1
content:: In a defense-in-depth approach to AI risk, which failure can a governance layer, such as a law requiring safety testing before release, guard against that a lab's own technical safeguards cannot?
options::
- [x] The lab skipping its own safeguards under competitive pressure
- The model hiding its goals during interpretability checks
- A monitor model missing a subtle harmful action
- A jailbreak slipping past the model's refusal training
shuffle:: true

#### Question: Choice
id:: 88841f96-aca7-4d0e-96c8-448b5205a6c7
content:: A critic says a lab's monitoring system catches only 60% of harmful actions, so it is not worth having. Which response best fits defense in depth?
options::
- [x] It can still help if it catches cases the other layers miss
- It adds nothing unless it catches nearly every attempt
- It is enough on its own, since it catches most attempts
- It only helps if it is the last layer before harm occurs
shuffle:: true

#### Question: Open
id:: 426177b7-b9f4-4bde-9456-94850cc1bedd
content:: Why might defense in depth give less protection against a capable AI that is trying to evade its safeguards than against random accidents?
assessment-instructions:: Score out of 100. 100 for the idea that the AI's evasion is not random: it can deliberately look for weaknesses the layers share, or act so that it slips past all of them together (for example, behaving well whenever it might be watched), so the layers' failures become correlated. 40 for only saying the AI is smart or powerful, without explaining why that defeats several layers at once.

#### Question: Open
id:: 178543ca-f251-47b2-a8db-806430c00659
content:: Name two different safeguard layers an AI company could use to stop its model from helping someone make a biological weapon, and say why having both helps.
assessment-instructions:: Score out of 100. 80 for any two distinct layers, such as: refusal training, classifiers that block dangerous inputs or outputs, monitoring and banning accounts, checking users' identities, keeping model weights secure, removing hazardous data from training, or screening DNA synthesis orders. 20 more for saying why both help: an attack that beats one layer can still be caught by the other. 40 if only one layer is named.

#### Question: Open
id:: fa8fae0b-1bca-4200-b639-2c8df87574f0
content:: A plan for safe advanced AI combines alignment training, monitoring and regulation. Apart from the AI deliberately evading them, give one reason these layers might fail together rather than independently.
assessment-instructions:: Score out of 100. 100 for any one plausible common cause, such as: race pressure leading labs and governments to weaken all of them at once; all layers relying on the same evaluations or the same untested assumption; monitor models trained the same way as the model they watch, sharing its flaws; regulators depending on the lab's own reports. 50 for a vague answer like "they're connected" with no mechanism.

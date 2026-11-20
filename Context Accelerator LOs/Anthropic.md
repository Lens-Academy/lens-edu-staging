---
id: f44dee39-8c1f-4d0c-8800-42025f7d25b9
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how Anthropic was founded and how it approaches safety, explain the case for safety-focused companies building frontier AI, and give the main criticisms of that role.

## Requires

## Helpful first
- [[AI companies]]

## Why it matters
Anthropic is one of the few companies building the most capable AI systems. It argues that since such systems will be built anyway, safety-focused companies should be among those at the frontier. Weighing that argument helps you judge how far to trust company safety commitments, and what working at or supporting such a company is likely to achieve.

## Lenses
- [Anthropic (Wikipedia)](https://en.wikipedia.org/wiki/Anthropic): the basic facts: founding in 2021 by former OpenAI staff, the founders, Claude and its products, funding and investors, size, and the 2026 Pentagon dispute. Read the opening summary and the company history (updated November 2026).
- [[../Lenses/anthropic-core-views-on-ai-safety-when-why-what-and-how|Core Views on AI Safety]]: Anthropic's founding case for why safety research has to be done on frontier models, and the tradeoff that creates. Read the opening summary and "The role of frontier models in empirical safety" (March 2023).
- [[../articles/anthropic-responsible-scaling-policy-version-3-0|Responsible Scaling Policy: Version 3.0]]: Anthropic explains its if-then safety framework, the "race to the top" it hoped to start, what worked and what didn't, and why it rewrote the policy (February 2026).
- [[../Lenses/AICF - Ngo - Pragmatism and pessimization|Richard Ngo: Pragmatism and pessimization]]: a critic's view, from a former OpenAI and DeepMind researcher, of how Anthropic's "alignment" work and racing pushed capabilities forward. Read the section "Anthropic" (August 2026).
- [The Long-Term Benefit Trust (Anthropic)](https://www.anthropic.com/news/the-long-term-benefit-trust): what being a public benefit corporation means for Anthropic, and how its independent trust elects board directors (September 2023; trust-appointed directors became a board majority in April 2026).

## Tests

#### Question: Choice
id:: c07405b6-c2f1-46e3-a32b-d6d3780112d6
content:: Anthropic was founded in 2021 by a group who had left which AI organization?
options::
- [x] OpenAI
- Google DeepMind
- Meta AI
- Microsoft Research
shuffle:: true

#### Question: Choice
id:: cb2b6dcb-a567-4ea6-a491-8244c58b7fe4
content:: Safety-focused AI companies such as Anthropic give a "build it safely first" reason for developing frontier AI. Which statement best captures it?
options::
- [x] Powerful AI will likely be built anyway, so careful developers should be at the frontier
- Frontier AI will soon be banned, so careful developers should shape the rules before then
- Safety research needs no frontier models, so selling them funds outside research
- Careful developers can earn enough from frontier AI to buy out riskier rivals
shuffle:: true

#### Question: Open
id:: d4351608-d1fd-4790-b7da-9ec24f3e9131
content:: Critics argue that a safety-focused company building frontier AI, such as Anthropic, can still increase AI risk. Explain one way this could happen.
assessment-instructions:: Score out of 100. 100 for any one clearly explained mechanism: it speeds up the race by pushing the frontier and pressuring rivals to keep up; competition or investor pressure leads it to weaken its safety commitments; its safety reputation makes frontier development look acceptable to the public or regulators; it draws safety talent and funding into capabilities work. 50 for naming a mechanism without saying how it raises risk.

#### Question: Choice
id:: ddbe61c7-cfd3-44d0-a868-deb09be3c3c5
content:: Anthropic hopes its approach will start a "race to the top" among AI companies. Which development would best fit what it means by that?
options::
- [x] Other labs adopt safety frameworks modelled on Anthropic's
- Other labs stop building frontier models and leave the field to Anthropic
- Governments approve Anthropic's models as the only ones allowed for use
- Other labs train larger models to beat Anthropic's scores
shuffle:: true

#### Question: Choice
id:: 2f782ea0-a5b8-496b-935b-8223aa770bd4
content:: What is Anthropic's Responsible Scaling Policy?
options::
- [x] Its own voluntary framework tying safeguards to its models' capabilities
- A US law that requires AI companies to test models before release
- An agreement among leading labs to cap the compute used in training
- Its policy for deciding which customers may use its models
shuffle:: true

#### Question: Choice
id:: 99076d42-10a7-4eb0-979c-93d6bd8974ec
content:: Earlier versions of Anthropic's Responsible Scaling Policy implied that it would pause development if it couldn't keep risks at an acceptable level. What did version 3.0, released in February 2026, do with that implication?
options::
- [x] It removed it
- It made it an explicit, binding commitment
- It kept it unchanged
- It handed the decision to pause to the US government
shuffle:: true

#### Question: Choice
id:: 9c416562-b434-4312-aa10-64efc90d8d82
content:: What does Anthropic's Long-Term Benefit Trust do?
options::
- [x] It elects board directors, who as of 2026 are a majority of the board
- It owns most of Anthropic's shares and receives its profits
- It must approve each new model before release
- It audits Anthropic's safety tests for the US government
shuffle:: true

#### Question: Choice
id:: 7da547d9-e890-42a1-83df-f01bb8d3a6be
content:: Anthropic is a public benefit corporation. What does that legal form allow?
options::
- [x] Directors can weigh a stated public mission alongside shareholders' financial interests
- The company can receive tax-deductible donations in the way a charity can
- The company can operate without any outside investors or shareholders
- The government can appoint directors to protect the public interest
shuffle:: true

#### Question: Choice
id:: f6e2045f-b697-44a6-967b-01d5b09478f0
content:: In March 2026, the US Department of Defense labelled Anthropic a "supply chain risk" after a dispute over Anthropic's limits on how its models could be used. Which limits?
options::
- [x] Limits on mass surveillance of Americans and on autonomous weapons
- Limits on selling its models to foreign governments and militaries
- Limits on using classified government data to train its models
- Limits on how many government staff may use its models
shuffle:: true

#### Question: Open
id:: 445b933f-cfe0-48dc-8396-77c82c339969
content:: Supporters argue that a safety-focused lab needs to build frontier models to do its safety research. Name one kind of safety research that needs frontier models, and say why.
assessment-instructions:: Score out of 100. 100 for any one kind with a reason: dangerous-capability evaluations (such capabilities appear first in the most capable models); interpretability (findings on small models may not carry over); testing alignment or control methods (problems such as deceptive behaviour may only show up in more capable models); red-teaming deployed models. 50 for naming a kind without a reason.

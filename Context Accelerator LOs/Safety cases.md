---
id: a8aa0cb7-ccca-4c06-a297-81894bae83ac
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what an AI safety case is, the main kinds of argument it can rest on (inability, control, trustworthiness), the evidence each needs, and where safety cases can fall short.

## Requires
- [[AI evaluations]]

## Helpful first
- [[AI control]]
- [[Frontier safety frameworks]]

## Why it matters
Safety cases put the burden on developers to show, with evidence, that a specific deployment is acceptably safe, rather than on others to prove it dangerous. Knowing which arguments are strong lets you judge whether a company's safety claims hold up, and spot when a more capable model breaks an argument that worked before.

## Lenses

## Tests

#### Question: Choice
id:: e9175174-9a32-44e3-86ad-a2de9703e428
content:: What is a safety case for an AI system?
options::
- [x] An evidence-backed argument that a system is acceptably safe in a given deployment
- A set of safety benchmark scores reported for a model
- An investigation report written after an AI incident
- A company's commitments to adopt safety measures at capability thresholds
shuffle:: true

#### Question: Choice
id:: 9d0b1cb9-c474-4743-a6f8-367e21f08883
content:: Under a safety case approach to deploying AI, who has to make the argument about the system's safety?
options::
- [x] The developer, who must show the system is safe enough to deploy
- A regulator, who must show the system is dangerous before blocking it
- Independent researchers, who must find a flaw before deployment is paused
- Users, who accept the risks when they agree to the terms of service
shuffle:: true

#### Question: Choice
id:: e98f5149-7cb0-479f-90a8-835ec389e9c4
content:: A developer argues: "Even with strong elicitation, our model cannot complete the key steps of a cyberattack, so it couldn't cause this harm even if it tried." Which kind of safety case argument is this?
options::
- [x] Inability argument
- Control argument
- Trustworthiness argument
- Deference argument
shuffle:: true

#### Question: Choice
id:: c290e81a-cb10-417e-a8e1-68b25d525713
content:: Which evidence would most directly support a control argument in an AI safety case?
options::
- [x] A red team playing a scheming model failed to evade the monitoring protocol
- Interpretability tools found no sign of deceptive goals in the model
- The model scored poorly on dangerous-capability benchmarks
- The model consistently refused harmful requests during testing
shuffle:: true

#### Question: Choice
id:: 057f7ac0-c717-4ba4-aeff-c3866e390e4c
content:: A safety case relies on the claim that a model can't perform a dangerous task. Evaluators then find that with better scaffolding and more attempts, the model succeeds. What does this mean for the safety case?
options::
- [x] That argument fails, so another kind, such as control, is needed
- The case holds, since the model passed the original evaluation
- The case holds, since scaffolding isn't part of the model itself
- The developer only needs to rerun the original evaluation
shuffle:: true

#### Question: Choice
id:: 0258e887-102c-4d30-aea7-532366880ff4
content:: Why are arguments that a model is safe because it is aligned currently considered among the hardest parts of an AI safety case to make?
options::
- [x] There's no reliable way yet to verify a model isn't faking good behavior
- Aligned models are usually less capable, so few of them exist
- Current regulations forbid relying on claims about a model's goals
- They require proving that the model lacks dangerous capabilities
shuffle:: true

#### Question: Choice
id:: 6a8c3338-7209-4f78-bb4e-ef488cc1107d
content:: How does a safety case differ from a frontier safety framework, such as a responsible scaling policy?
options::
- [x] A framework commits in advance; a safety case justifies one specific deployment
- A framework is written by regulators; a safety case by developers
- A framework covers misuse; a safety case covers misalignment
- A framework is legally binding; a safety case is voluntary
shuffle:: true

#### Question: Choice
id:: 97f0b6c5-468c-4557-afd5-ba19fd1749eb
content:: A safety case argued that a model was safe to offer through a chat interface. The developer now plans to let customers fine-tune the model. What should happen to the safety case?
options::
- [x] It must be revisited, since it assumed the original deployment
- Nothing changes, since the released weights were already evaluated
- Nothing changes, if customers review their own fine-tuning data
- It is withdrawn, because fine-tuned models can't have safety cases
shuffle:: true

#### Question: Choice
id:: cda37ebb-d79b-4a5d-a488-5bca90a3a704
content:: Safety cases for AI borrow a practice that is already required in which kind of field?
options::
- [x] Safety-critical industries, such as nuclear power and offshore oil and gas
- Consumer software development, such as mobile apps and websites
- Academic publishing, such as peer review of scientific papers
- Marketing regulation, such as rules on product advertising claims
shuffle:: true

#### Question: FillBlank
id:: b1d94fdf-3d4d-4a35-a807-b47f1d191c26
content:: In AI safety cases, an argument that a model won't cause harm because its goals and behavior can be relied on is called a {{trustworthiness|alignment|propensity}} argument.

#### Question: Open
id:: 69c2ee39-edec-4232-b0cd-6dc271ee46d1
content:: Why doesn't a control argument in an AI safety case need to assume that the AI system is aligned?
assessment-instructions:: Score out of 100. 100 for explaining that a control argument claims the safety measures (such as monitoring and restrictions) would stop harm even if the model actively tried to subvert them, tested for example by a red team acting as the model, so it holds whether or not the model is aligned. 50 for only saying "it uses monitoring" without the even-if-misaligned point.

#### Question: Open
id:: cca1f365-5712-4831-a901-ba0c90a2644c
content:: Explain why a safety case resting on an inability argument may not carry over to a developer's next, more capable model.
assessment-instructions:: Score out of 100. 100 for: the argument rests on the model lacking dangerous capabilities, and a more capable model may have them, so it needs new evaluations and possibly a different argument such as control or trustworthiness. 60 for saying new evidence is needed without saying why.

#### Question: Open
id:: 9d596e40-6b54-446e-882c-b821e82c076d
content:: Name one weakness or limitation of safety cases as a way to govern the deployment of frontier AI.
assessment-instructions:: Score out of 100. 100 for any one of: developers write their own cases (conflict of interest) unless independently reviewed; immature science makes some arguments, especially about alignment, weak; no agreed threshold for acceptable risk; better elicitation or new capabilities can undermine the evidence; they can become box-ticking paperwork. 40 for a vague answer ("they might be wrong") with no reason.

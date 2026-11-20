---
id: 8ba005ab-eed3-4b46-99fd-fa6071569469
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Break a path to AI-enabled catastrophe into concrete steps, such as capability, motive, access and failure to respond, and use that breakdown to find where an intervention could stop it.

## Requires

## Helpful first
- [[Sources of AI catastrophe]]

## Why it matters
A vague sense that AI is dangerous doesn't tell you what to do. Breaking a path into steps shows which defenses, such as capability tests, securing model weights or DNA synthesis screening, act on which step, so you can judge a proposal by where it cuts the path and what it leaves open.

## Lenses
- [[../Lenses/darioamodei-dario-amodei-the-adolescence-of-technology|The Adolescence of Technology]]: read section 2, "A surprising and terrible empowerment" (Misuse for destruction, then Defenses). Breaks AI-enabled bioterrorism into motive, ability and materials, explains uplift beyond what search gives, and sets model guardrails, gene synthesis screening and biodefense against different steps (2026).
- [Activating AI Safety Level 3 protections (Anthropic)](https://www.anthropic.com/news/activating-asl3-protections): a lab states its threat models (help with end-to-end weapons workflows; theft of model weights), explains how a capability threshold triggered safeguards, and lists the layers: classifiers, monitoring and egress limits on weights (May 2025; the policy has since been revised).
- [[../Lenses/shlegeris-ai-catastrophes-and-rogue-deployments|AI catastrophes and rogue deployments]]: splits misaligned-AI catastrophe into two steps, first escaping safety measures through weight exfiltration or an unmonitored internal run, then causing harm. Argues the first step is easy and the second hard, which is why monitoring targets the escape (June 2024).

## Tests

#### Question: Choice
id:: 62fbf1fa-1c61-42f1-b415-d5fe57680e67
content:: A threat model lists four steps that must all happen for a catastrophe. How does the probability of the whole path compare with the probability of its least likely step?
options::
- [x] It is no higher than that step's probability
- It is about the average of the four steps' probabilities
- It is equal to the most likely step's probability
- It is higher, because the steps add up
shuffle:: true

#### Question: Choice
id:: f4d6d282-f8d8-4041-8454-ffd39fcf4df2
content:: A lab's main defense against bioweapon misuse is refusal training in its model. If the model's weights are released openly, which of these defenses keeps working?
options::
- [x] Screening of orders at DNA synthesis companies
- The model's refusal training
- Filters on the lab's API outputs
- Banning users who send suspicious prompts
shuffle:: true

#### Question: Choice
id:: ddff8003-70f2-49cb-9f0c-03090fbfe678
content:: A lab's dangerous capability evaluations find that its new model gives would-be attackers meaningful help with bioweapons, beyond what search offers. In a threat model, what does this finding change?
options::
- [x] One step gets easier, so defenses at the other steps carry more weight
- More people now want to cause mass harm, so the motive step gets easier
- Materials become easier to get, so DNA synthesis screening stops working
- Every step is now met, so an attack is close to certain
shuffle:: true

#### Question: Choice
id:: 235d134e-161f-4f77-9894-1e2d9f5cc24b
content:: A model gives a user accurate, detailed answers on a dangerous topic, but the same facts are in standard textbooks and come up in a quick web search. In threat modeling terms, how much uplift does the model give?
options::
- [x] Little, because it adds little to what the user could already get
- A lot, because the answers are accurate and detailed
- A lot, because the model clearly knows the topic well
- It can't be judged without knowing the user's motive
shuffle:: true

#### Question: Choice
id:: 491fa46f-43d6-4421-9643-ea630a84f588
content:: Why is screening DNA synthesis orders often proposed as a defense against AI-enabled bioweapons?
options::
- [x] It acts on getting materials, whichever AI model advised the attacker
- It keeps biology papers out of the data used to train AI models
- It detects disease outbreaks sooner than hospital reporting does
- It makes refusal training harder to remove from openly released models
shuffle:: true

#### Question: Choice
id:: 50165547-f267-4f27-9bba-2a6c79198bec
content:: A researcher publishes a detailed threat model for AI-assisted cyberattacks on power grids. What does the threat model by itself show?
options::
- [x] A possible path to harm and where it could be blocked
- That such an attack is likely within a few years
- That current AI models can already carry out the attack
- That this is the largest risk from AI
shuffle:: true

#### Question: Choice
id:: 086252d0-58ee-44ce-847b-190bb1bcee52
content:: In a threat model where a misaligned AI tries to copy its own weights out of the lab, what does monitoring the AI's actions mainly do?
options::
- [x] Catching and stopping the attempt before it succeeds
- Reducing the AI's skill at writing code
- Changing the goals the AI is pursuing
- Limiting which customers can use the AI
shuffle:: true

#### Question: Choice
id:: 427490de-ca8e-4720-9963-9b39fecb2701
content:: Defense in depth stacks several safeguards, so a path to harm must get past each of them. When does adding more layers help least?
options::
- [x] When the layers tend to fail in the same situations
- When each layer catches a different kind of attack
- When the layers are run by different organizations
- When one layer is physical and another is digital
shuffle:: true

#### Question: Choice
id:: 0d0a83f0-2ab6-4516-87a6-80f60d891f71
content:: In a threat model where every step is necessary, does reliably blocking one step stop that particular path?
options::
- [x] Yes
- No

#### Question: Choice
id:: 9f741ca3-5df9-40ee-8fc1-8a74d5e78af6
content:: A threat model shows that one path to AI-enabled bioweapons is now blocked. Does this show that the AI system poses no bioweapon risk?
options::
- [x] No
- Yes

#### Question: FillBlank
id:: e6a67ad2-a5bc-4688-b87c-4598200b0ad3
content:: Borrowed from military and cybersecurity use, the term {{kill chain}} names a breakdown of an attack into steps that must all succeed.

#### Question: Open
id:: 0becb54c-e59a-4f0b-861e-a3b2406d3ec0
content:: Using AI-enabled bioweapons as the example, name two different steps on the path to catastrophe and one intervention that acts on each.
assessment-instructions:: Score out of 100. Steps can include capability or know-how, motive, access to materials or equipment, and detection or response. Interventions can include refusal training, capability evaluations, securing weights, DNA synthesis screening, biosurveillance or vaccines. 50 per distinct step paired with a fitting intervention; 25 for a step with no or a mismatched intervention.

#### Question: Open
id:: 03430eac-3c26-4dd2-be4b-256490b7c288
content:: Frontier AI safety frameworks tie extra safeguards to dangerous capability levels. How does a threat model help a lab decide which capability levels should trigger those safeguards?
assessment-instructions:: Score out of 100. Full marks for saying the threat model shows which capability would give real help on a specific path to harm, so the lab can test for that capability and act when a model reaches it. 50 for saying it makes the risk concrete or testable without linking it to a capability threshold.

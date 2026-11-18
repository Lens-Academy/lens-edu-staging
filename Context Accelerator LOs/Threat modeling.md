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
id:: c81eca2a-197e-46c5-89b3-30ec5091c8ce
content:: In a threat model of AI-enabled bioweapons, dangerous capability evaluations of a model mainly give evidence about which step?
options::
- [x] Whether the model could give meaningful help
- Whether anyone wants to cause mass harm
- Whether attackers can get lab materials
- Whether health agencies would detect an outbreak
shuffle:: true

#### Question: Choice
id:: bc99c8a5-d6a4-49a4-8074-7ba5c6fceb68
content:: In threat modeling of AI misuse, what does "uplift" from a model usually mean?
options::
- [x] Help beyond what the person could already get, for example from search
- All the knowledge the model holds about the dangerous topic
- The gain in benchmark scores between model versions
- How much faster the model answers than a human expert
shuffle:: true

#### Question: Choice
id:: 491fa46f-43d6-4421-9643-ea630a84f588
content:: Why is screening DNA synthesis orders often proposed as a defense against AI-enabled bioweapons?
options::
- [x] It acts at a physical step that is hard to route around, whatever advice the attacker got
- It keeps biology papers out of the data that AI models are trained on
- It detects disease outbreaks earlier than hospital reporting does
- It makes it harder to remove refusal training from open models
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
content:: In a threat model where a misaligned AI tries to copy its own weights out of the lab, which step does monitoring the AI's actions mainly target?
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

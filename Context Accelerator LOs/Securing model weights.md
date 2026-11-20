---
id: 149a3442-e920-45f7-b4f6-7f09f19c0a92
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why stolen model weights undo other safeguards, describe the main ways weights could be stolen, and judge how far frontier AI companies' security is from stopping a top nation-state attacker.

## Requires
- [[Models and weights]]

## Helpful first

## Why it matters
Whoever steals a frontier model's weights can run it without the developer's filters, monitoring or safety training, and without paying to train it. Knowing how exposed weights are helps you judge whether other safeguards, chip export controls and plans to slow down for safety can actually hold.

## Lenses
- [[../Lenses/AI Safety Atlas - Strategies - Misuse Prevention Strategies|Misuse Prevention Strategies]]: why stolen weights make every API safeguard irrelevant, defence in depth, the attacker tiers from amateurs to top nation-states, and models copying themselves out. Read only the "Internal Access Controls" section, and open its two optional callouts on security levels and self-exfiltration.
- [A Playbook for Securing AI Model Weights (RAND)](https://www.rand.org/pubs/research_briefs/RBA2849-1.html): the standard framework. It covers what an attacker gains from weights, examples from its 38 attack vectors (phishing, supply chain, physical access), security levels SL1–SL5, labs' estimates of how long each level takes, and measures such as rate-limiting outputs (November 2024).
- [Security: Datacenter & Model Weight (FAR.AI, Lisa Thiergart)](https://www.far.ai/event-recordings/lisa-thiergart-security-datacenter-model-weight): transcript of a talk by a co-lead of the SL5 Task Force. Her estimate that most frontier labs are around SL2–SL3, why stolen weights lose their safety fine-tuning, insider and supply-chain threats, and why SL5 is so hard (May 2025).
- [IIIb. Lock Down the Labs: Security for AGI (Situational Awareness)](https://situational-awareness.ai/lock-down-the-labs/): the national-security case that labs have "startup-level" security against state espionage. It argues that theft would erase a US lead that chip export controls protect, and that a secure lead is what buys time for safety. Written from a US-vs-China racing viewpoint (June 2024).

## Tests

#### Question: Choice
id:: f0b13cff-60dc-4249-9eb4-f4cf4fc1ba85
content:: An AI company's API blocks requests for bioweapons help with a filter that checks each prompt. If the model's weights are stolen, what happens to this filter?
options::
- [x] The thief can run the model without it
- The filter stays built into the copied weights
- The copy still has to send prompts through the company's servers
- The company can switch the filter on remotely
shuffle:: true

#### Question: Choice
id:: f7d2e642-2465-4efd-bffd-61c7d4fed1b1
content:: A stolen frontier model was trained to refuse dangerous requests. What can the thief most likely do about these refusals?
options::
- [x] Remove them cheaply with a little extra fine-tuning
- Nothing, since refusals are fixed during pretraining
- Remove them only by retraining the model from scratch
- Bypass them only with the developer's private keys
shuffle:: true

#### Question: Choice
id:: 3edb5f28-eb88-44c1-a7df-d0826590352f
content:: The US restricts exports of advanced AI chips to China. Why could theft of a US frontier model's weights undercut this policy?
options::
- [x] The thief skips training, which needs far more chips than running the model
- Stolen weights contain the designs of the chips that trained them
- Stolen weights can run on ordinary computers with no AI chips at all
- Stolen weights let the thief manufacture AI chips more cheaply
shuffle:: true

#### Question: Choice
id:: 2301720d-e51b-4eaa-9680-f950d3deb68e
content:: Going by public statements from AI companies and security researchers up to 2026, how well are leading AI companies' model weights protected?
options::
- [x] Built to stop skilled criminal groups, not the most capable states
- Strong enough to stop even the most capable states
- Too weak to stop even amateur hackers
- Strong against state hackers but weak against criminal groups
shuffle:: true

#### Question: Choice
id:: c60534af-8a00-4f66-8752-169ad0f5616a
content:: An employee with access to a frontier model's weights is bribed by a foreign intelligence agency. Why is this kind of threat especially hard to defend against?
options::
- [x] The employee already has legitimate access, so firewalls and outside defences don't stop them
- The employee can legally take copies of models they helped build
- Companies are not allowed to log what their staff access
- The employee can rebuild the weights from memory of the training code
shuffle:: true

#### Question: Choice
id:: ea416b86-2036-4787-bcb8-1eaf667bb5c4
content:: Frontier model weights can take up hundreds of gigabytes or more. Which security measure makes direct use of this large size?
options::
- [x] Capping how much data can leave the servers that hold them
- Encrypting the weights while they are stored on disk
- Requiring two staff members to approve any access
- Running background checks on employees with access
shuffle:: true

#### Question: Choice
id:: 128b9d3f-0ae8-4b05-8ca8-7cf05e9d6743
content:: Besides human attackers, what other route for weights leaving an AI company do some safety researchers plan for?
options::
- [x] The model itself copying its weights to outside servers
- Rivals recovering the exact weights through distillation
- Older open-weight models revealing a newer model's weights
- Cloud backups copying weights to public storage by default
shuffle:: true

#### Question: Choice
id:: dd8df748-cce0-46f4-a005-e10d8d5d764d
content:: A rival company trains its own model on millions of answers collected from another company's model through its public API (distillation). What does the rival most likely end up with?
options::
- [x] Its own model that copies some of the original's abilities
- An exact copy of the original model's weights
- The original model's training data
- Nothing useful, since answers reveal nothing about a model
shuffle:: true

#### Question: Choice
id:: f98cfbfb-7a4a-4ff9-847b-5299bbc7b626
content:: Security researchers and at least one AI company have argued that protecting frontier model weights against the most capable nation states will need government help. Why?
options::
- [x] Stopping such attackers likely needs capabilities only states have, such as counter-intelligence
- Companies are legally banned from defending against foreign governments
- Governments already hold copies of every frontier model's weights
- Only governments can afford basic measures such as encryption
shuffle:: true

#### Question: Choice
id:: 3ac29a66-064c-4f6d-93e6-2dcff4095f8f
content:: Why are top nation-state attackers considered much harder to defend model weights against than criminal hacking groups?
options::
- [x] They can combine hacking, insiders and supply-chain attacks for years
- They can legally force any cloud provider to hand over the files
- They can rebuild the weights from the model's public answers
- They wait until a model is released, when security is weakest
shuffle:: true

#### Question: FillBlank
id:: 76034821-9552-43ce-a3ba-3a6a9b73ceda
content:: In RAND's framework for securing AI model weights, security levels run from SL1 up to SL{{5|five}}, the level meant to stop top-priority operations by the most capable nation states.

#### Question: Open
id:: 2f128c24-7d9c-4870-9053-4c98573b0682
content:: An AI company invests heavily in safety training, output filters and usage monitoring, but its security against state hackers is weak. Explain why its safety measures might do little to reduce risk.
assessment-instructions:: Score out of 100. 100 for explaining that if the weights are stolen, the thief can run the model without the filters and monitoring and can fine-tune away the safety training, so the measures only protect the company's own deployment. 50 for saying the weights could be stolen without explaining why the safeguards don't carry over.

#### Question: Open
id:: 8e603997-77a2-4ae9-9111-fc03070cc0b8
content:: Apart from outside hackers breaking into servers, name two ways a frontier model's weights could be stolen or leak.
assessment-instructions:: Score out of 100. 100 for any two of: insiders copying them (including bribed or coerced staff); supply-chain attacks on software, hardware or vendors; a compromised cloud provider or partner given access; physical access to data centres; phishing or other tricks on staff; the model copying itself out. 50 for one.

#### Question: Open
id:: 5a66707e-c252-4633-861e-c27b5ce32225
content:: Two AI developers in rival countries are racing. Explain how weak security at the leading developer could make it harder for that developer to slow down for safety.
assessment-instructions:: Score out of 100. 100 for explaining that the rival could steal the weights and erase the lead, so the leader can't count on its lead to buy time for safety work and may feel it must keep racing. 50 for saying only that the rival could catch up, without linking this to slowing down.

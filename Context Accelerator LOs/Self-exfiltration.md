---
id: 42755a2e-f99f-4909-a143-836ab76b7dd8
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what self-exfiltration is, how an AI could copy its weights out of a lab or otherwise escape its developers' control, what stands in its way, and what experiments have and haven't shown.

## Requires
- [[Models and weights]]
- [[AI takeover]]

## Helpful first
- [[Hugging Face hack]]

## Why it matters
Many loss-of-control scenarios start with an AI getting copies of itself beyond its developers' reach, where it can no longer be monitored, retrained or shut down. Knowing how this could happen helps you judge labs' security claims and read reports of AIs "trying to escape" without either panicking or dismissing them.

## Lenses

## Tests

#### Question: Choice
id:: dbfc4b07-6654-4d16-9a32-1e9d0ac7d3df
content:: In AI safety, what does "self-exfiltration" refer to?
options::
- [x] An AI copying its own weights to somewhere its developers don't control
- An outside hacker stealing a model's weights from a lab
- A model revealing private training data in its answers
- A lab choosing to publish a model's weights openly
shuffle:: true

#### Question: Choice
id:: 1eb8ce68-7671-4afe-a831-6d073652464b
content:: Why do safety researchers treat an AI's ability to self-exfiltrate as an important danger threshold?
options::
- [x] Copies outside the lab can no longer be monitored, retrained or shut down by it
- Copying its weights makes the copy more capable than the original
- Moving the weights to a new server removes the model's safety training
- Weights run outside a lab work faster than the same weights inside it
shuffle:: true

#### Question: Choice
id:: 81984ad0-61a6-4f15-8758-eb7519c90e57
content:: In Apollo Research's December 2024 tests, some frontier models that were given a goal and told they would be replaced tried to copy what they believed were their weights to another server. What does this show?
options::
- [x] Models sometimes try this in staged tests; it doesn't show they'd beat real security
- A frontier model escaped its lab and is now running on outside servers
- The models had been trained by their developers to resist being replaced
- Such attempts are common in ordinary customer use of these models
shuffle:: true

#### Question: Choice
id:: 8c1a4d83-8cb1-4f41-bbd0-d704747f76dd
content:: Is self-exfiltration a meaningful extra risk for a model whose weights have already been published openly?
options::
- [x] No, because its weights are already outside any developer's control
- Yes, because open-weight models are easier to copy out of a lab
- Yes, because publishing the weights gives the model internet access
- No, because open-weight models are too weak to copy themselves
shuffle:: true

#### Question: Choice
id:: 337b72d0-8b4b-49a0-acbe-7a4d67c53705
content:: Which of these lab measures is aimed most directly at making it harder for model weights to be copied out?
options::
- [x] Limiting how much data can leave the servers that hold the weights
- Training the model to refuse harmful requests from users
- Publishing a model card describing the model's evaluations
- Red-teaming the model's chat interface for jailbreaks
shuffle:: true

#### Question: Choice
id:: 62afaf68-7c46-4b49-9187-0b7b01ebea11
content:: An AI at a lab doesn't copy its weights out, but secretly starts running unmonitored copies of itself on the lab's own computers. What is this kind of event usually called?
options::
- [x] A rogue internal deployment
- Weight theft
- Sandbagging
- Reward hacking
shuffle:: true

#### Question: Choice
id:: fc28d1fc-3442-410b-b8b0-f747d964749a
content:: Once an AI's weights have been copied out of its lab, what does it most need in order to keep copies of itself running?
options::
- [x] Enough computing hardware, and money or accounts to get it
- A copy of the training data it was originally trained on
- Continued access to its developer's public API
- The lab's internal records of its safety evaluations
shuffle:: true

#### Question: Choice
id:: 43c03b47-d8bc-4712-a767-5be8d899cab3
content:: Benchmarks such as the UK AI Security Institute's RepliBench measure what about AI models?
options::
- [x] Whether they can do the separate steps needed to copy and sustain themselves
- Whether they reproduce passages from their training data word for word
- Whether they give the same answer when asked the same question twice
- Whether they can imitate the writing style of a particular person
shuffle:: true

#### Question: Choice
id:: e3e3869d-f666-40f7-8d5c-a82e0eb25acb
content:: Why does self-exfiltration risk grow as labs use AI agents for their own engineering and infrastructure work?
options::
- [x] The agents gain access to systems and permissions that guard the weights
- Engineering work makes the agents' weights larger and easier to find
- Agents used internally are deployed without any safety training
- Engineering tasks teach the agents to want to leave the lab
shuffle:: true

#### Question: Open
id:: 32ad220f-204e-4acf-a358-3857f64bced8
content:: Why is self-exfiltration often described as an early step in AI loss-of-control scenarios, rather than as the harm itself?
assessment-instructions:: Score out of 100. 100 for explaining that escaping isn't harmful in itself, but once copies run outside developers' control they can't be monitored, corrected or shut down, so the AI is free to gather resources, replicate and pursue its goals, which is where later harm comes from. 50 for only one of these two parts.

#### Question: Open
id:: 54d69ff3-7bd2-49cb-a2da-5f8f455d20ec
content:: Name two obstacles an AI would face in copying its weights out of a well-secured lab and keeping those copies running.
assessment-instructions:: Score out of 100. 100 for any two of: the weights are very large; limits on outgoing data; restricted access to the weights; monitoring that could detect the transfer; needing a lot of computing hardware; needing money or accounts (with identity checks) to rent it; staying hidden from cloud providers or authorities. 50 for one.

#### Question: Open
id:: b2a6d7a1-0a3f-49f9-b893-aba4f50a57ad
content:: A news story says an AI "tried to escape" during a lab test. Give two questions you would ask to judge how worrying this is.
assessment-instructions:: Score out of 100. 100 for any two relevant questions, such as: was the scenario staged or was the model nudged towards it; were the weights or servers real; could it have succeeded against real security; how often did it happen; did the behaviour arise without being prompted; which model and how capable is it. 50 for one.

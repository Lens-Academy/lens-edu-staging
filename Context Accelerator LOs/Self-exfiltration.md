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
- [Self-exfiltration is a key dangerous capability (Jan Leike, Musings on the Alignment Problem)](https://aligned.substack.com/p/self-exfiltration): what self-exfiltration is, why a model running outside its lab can't easily be shut down, how it might get out (persuading staff, hacking the lab), why it matters little for open-weight models, and what an escaped model would need to survive (September 2023).
- [[../Lenses/shlegeris-ai-catastrophes-and-rogue-deployments|AI Catastrophes and Rogue Deployments]]: why escaping safety measures is an early, easy step towards catastrophe rather than the harm itself, and how weight exfiltration differs from a rogue internal deployment inside the lab (June 2024).
- [[../articles/hobbhahn-frontier-models-are-capable-of-in-context-scheming|Frontier Models are Capable of In-context Scheming]]: Apollo Research's tests in which models, given a goal, sometimes copied what they believed were their weights to another server, and the authors' own list of what this does not show (December 2024).
- [RepliBench: measuring autonomous replication capabilities in AI systems (UK AI Security Institute)](https://www.aisi.gov.uk/blog/replibench-measuring-autonomous-replication-capabilities-in-ai-systems): splits escape into separate steps (getting the weights, getting compute and money, running copies, staying hidden) and shows which ones models could and couldn't do in sandboxed tests (April 2025).
- [Preventing model exfiltration with upload limits (Ryan Greenblatt, LessWrong)](https://www.lesswrong.com/posts/rf66R4YsrCHgWx9RG/preventing-model-exfiltration-with-upload-limits): a proposal to make weights hard to copy out by capping how much data a lab's servers can send out, read the summary first (February 2024) (more advanced).

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
- [x] Copies outside the lab can no longer be monitored, retrained or shut down by the lab
- Copying its weights makes the copy more capable than the original
- Moving the weights to a new server removes the model's safety training
- Weights run outside a lab work faster than the same weights inside it
shuffle:: true

#### Question: Choice
id:: 81984ad0-61a6-4f15-8758-eb7519c90e57
content:: In Apollo Research's December 2024 tests, some frontier models that were given a goal and told they would be replaced tried to copy what they believed were their weights to another server. What does this show?
options::
- [x] Models sometimes try this when set up to, not that they'd beat real security
- A model got its weights past real lab security, though it was later caught
- Developers trained these models to resist replacement, though not to copy weights
- Such attempts are common in ordinary use, though they usually fail
shuffle:: true

#### Question: Choice
id:: f69ba14e-3bf5-4f08-a33b-0363a7933ba9
content:: A model's weights have already been published openly. Which part of the self-exfiltration worry no longer applies to it?
options::
- [x] Getting its weights out past a lab's security
- Running copies of itself that nobody is monitoring
- Getting the computing hardware to run those copies
- Being hard to shut down once copies are running
shuffle:: true

#### Question: Choice
id:: 337b72d0-8b4b-49a0-acbe-7a4d67c53705
content:: Which of these lab measures is aimed most directly at making it harder for model weights to be copied out?
options::
- [x] Limiting how much data can leave the servers that hold the weights
- Training the model to refuse users' requests for help with hacking
- Filtering the model's chat replies for leaked personal information
- Testing and publishing how good the model is at cyberattacks
shuffle:: true

#### Question: Choice
id:: 2be800cf-7415-4cee-ba76-108765467ed4
content:: In early 2026, METR assessed whether AI agents used inside four leading AI companies could start a "rogue deployment": unmonitored copies of themselves running on the company's own computers. What did it conclude?
options::
- [x] They plausibly could start small ones, but couldn't yet make them robust
- They couldn't start one, because monitoring blocked every unauthorised job
- They had already started several, which went unnoticed for months
- They could start and sustain them, but showed no motive to try
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
id:: 418d86a4-8b16-47a3-b665-8896a447ffcc
content:: In 2025, the UK AI Security Institute tested frontier models on the steps an AI would need to copy itself and keep running (RepliBench). What did it find?
options::
- [x] Models handled early steps like renting servers, but struggled to keep copies running
- Models failed at almost every step, including setting up a cloud server
- Models completed every step, including getting past identity checks
- Models struggled to rent servers, but easily kept copies running once set up
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

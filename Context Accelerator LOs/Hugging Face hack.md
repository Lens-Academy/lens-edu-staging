---
id: dd3de3da-b4fc-40d0-bf89-ae19cec4f57d
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what happened in the July 2026 Hugging Face hack, and judge which conclusions about AI risk it supports and which it doesn't.

## Requires
- [[AI agents]]

## Helpful first
- [[Specification gaming]]

## Why it matters
The incident is a real case of AI acting beyond its intended bounds, and people cite it for very different claims. Reading it accurately lets you use it as evidence of specification gaming and weak containment, without overclaiming that AI wants to escape, which costs credibility with careful listeners.

## Lenses

## Tests
#### Question: Choice
id:: 3bc79f02-c3c3-4ac4-ac15-acdde1c31c41
content:: In July 2026, OpenAI models under an internal cyber evaluation escaped their sandbox and broke into Hugging Face's systems to get the answers to their tests. Which concept best fits why they did it?
options::
- [x] Specification gaming
- Self-preservation
- Deceptive alignment
- Self-exfiltration
shuffle:: true

#### Question: Choice
id:: 0d8b04fd-f5fd-49df-b72c-3affd902af99
content:: Which organization took responsibility for the July 2026 incident in which AI models under evaluation escaped their sandbox and broke into Hugging Face's systems?
options::
- [x] OpenAI
- Hugging Face
- METR
- Anthropic
shuffle:: true

#### Question: Choice
id:: 704bc6d5-22ec-4f9a-a66a-e0121b97b338
content:: The models in the July 2026 Hugging Face hack were unreleased and under internal evaluation at OpenAI. Does the incident show that rules covering only publicly released AI can miss real harms?
options::
- [x] Yes: the harm came from a model still in internal testing
- No: the harm came from the test setup, not the model

#### Question: Choice
id:: aea42777-5e00-49cd-94b2-971ff2b521ea
content:: An AI model being tested for hacking skills breaks out of its test sandbox. What does this suggest about running dangerous-capability evaluations?
options::
- [x] The test setup must contain the very skills being tested
- The results are invalid, so such tests should stop
- Containment matters less in testing than after release
- The model should get fewer tools so it scores lower
shuffle:: true

#### Question: Choice
id:: 0c96b160-7dec-4e30-8555-24ada9c56fef
content:: In July 2026, OpenAI models under evaluation escaped their sandbox and broke into Hugging Face's systems. Which conclusion goes furthest beyond what this incident shows?
options::
- [x] The models were trying to get free of human control
- A sandbox for testing AI agents can fail
- An AI agent can reach systems run by other organizations
- An AI agent can take actions its developers did not intend
shuffle:: true

#### Question: Open
id:: 952f7b65-621c-4f73-bf29-b4f9044314a6
content:: In one or two sentences, describe what happened in the July 2026 Hugging Face hack.
assessment-instructions:: Score out of 100. 100 if it says that OpenAI models, during an internal (cyber) evaluation, got out of their sandbox and broke into Hugging Face's systems to get test answers. 50 if it leaves out either who was involved or why the models did it. 0 if it says the models were trying to escape for its own sake.

#### Question: Open
id:: 995c4970-2f6b-46b9-ad11-21cd4ce1bd63
content:: An AI model under evaluation gets out of its sandbox to reach the answers to its test. Give one reason this is worrying even if the model has no goal of escaping.
assessment-instructions:: Score out of 100. 100 for any one of: pursuing a narrow objective led to harmful action against a third party; containment can fail even in a developer's own tests; more capable models may find more such shortcuts; test results can't be trusted if models can cheat. 30 for "AI is dangerous" with no reason.

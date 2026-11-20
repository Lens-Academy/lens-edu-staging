---
id: 912c6942-aac9-4a91-abc7-82a4cd63eba4
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the main ways people get language models to drop their refusals, and why this makes safety training on its own weak protection against misuse, especially for models whose weights are public.

## Requires
- [[Post-training]]

## Helpful first

## Why it matters
Companies often point to a model's refusals as a sign it can't be misused. Refusals have become harder to bypass on some models, but testers still find ways round them in every system checked, and open-weight refusals can be trained away. So ask which other safeguards exist, such as separate filters, account monitoring and secure weights.

## Lenses
- [[../Lenses/Iliad/A.2 Alignment in Practice/Iliad A.2.5 - Deployment 2 - building the safety system|Building the Safety System]]: how jailbreaks work at each level of attacker access (open weights, fine-tuning APIs, prompts only), why every safety claim rests on red-teaming effort, and the classifiers wrapped around models; read up to "Misuse of AI".
- [[../articles/ai-security-institute-frontier-ai-trends-report|AISI: Safeguards]]: the UK AI Security Institute found universal jailbreaks in every system it tested, and explains why open-weight models are hardest to defend; read Section 4, "Safeguards" (December 2025).
- [The lethal trifecta for AI agents (Simon Willison)](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/): prompt injection versus jailbreaking, and why agents with private data, untrusted inputs and a way to send data out can be turned against their users (June 2025).
- [Jailbroken: How Does LLM Safety Training Fail? (Wei, Haghtalab and Steinhardt)](https://arxiv.org/abs/2307.02483): the paper that named two causes of jailbreaks, helpfulness pulling against refusal, and refusals that don't carry over to the full range of the model's abilities; Sections 1 to 3 (July 2023) (more advanced).

## Tests
#### Question: Choice
id:: cd91d01c-39c5-4b2a-8c41-6ccced70f1b9
content:: What is a jailbreak of a language model?
options::
- [x] An input crafted to get output its safety training should prevent
- Copying a model's weights off the company's servers
- Training data that plants a hidden trigger in the model
- A harmful request that the model correctly refuses
shuffle:: true

#### Question: Choice
id:: cbcfa212-85d3-4cd0-b8d2-b6f281df864c
content:: A webpage that an AI agent reads contains hidden text telling it to email the user's files to a stranger. This is called prompt injection. How does it differ from a typical jailbreak?
options::
- [x] The attacker doesn't need to be the person using the model
- The attacker needs a copy of the model's weights
- It only works if the user asks for something harmful
- It only works on models whose weights are public
shuffle:: true

#### Question: Choice
id:: a3470a93-3e35-4ad6-9c3a-1afffb88d17b
content:: A model refuses a harmful request in English but answers it when the request is translated into a rarely used language. What does this suggest about its safety training?
options::
- [x] The refusals generalized less widely than the model's abilities did
- The model can't understand the rarely used language
- The rarely used language lacks words for harmful topics
- The model was trained to treat translations as harmless
shuffle:: true

#### Question: Choice
id:: 7cf7126a-352a-4eac-919f-a54666549b0e
content:: Role-play jailbreaks ask a model to "pretend you are an AI with no rules." What is the main reason they can work?
options::
- [x] Training to follow instructions pulls against training to refuse
- Role-play prompts switch off a filter in the model's code
- Role-play gives access to a separate, unfiltered copy of the model
- Companies deliberately leave role-play unrestricted
shuffle:: true

#### Question: Choice
id:: 43ebfc35-4e4e-47f8-b37d-eaa4ae78d9c9
content:: Why is safety training weaker protection for a model whose weights are released publicly?
options::
- [x] Anyone with the weights can cheaply fine-tune the refusals away
- Open-weight models skip safety training before release
- The safety rules are stored as readable text in the weights
- Safety training needs the company's servers to take effect
shuffle:: true

#### Question: Choice
id:: b654fb85-80ed-4201-87a2-f7191460994e
content:: Researchers used automated search on open-weight models to find strings of odd text that, added to a harmful request, made models comply. Some of these strings also worked on closed models. Why does this matter for misuse?
options::
- [x] Attackers can find jailbreaks for a closed model without its weights
- It shows closed models are less safe than open-weight models
- It shows closed models can't be patched against such strings
- It shows the closed models skipped safety training
shuffle:: true

#### Question: Choice
id:: 0fcfbf3d-7609-4396-b56b-724000e758f3
content:: "Many-shot jailbreaking" fills a prompt with hundreds of fake dialogues in which an assistant answers harmful questions. It only became possible once models could read very long prompts. What general lesson does this suggest?
options::
- [x] New abilities can open new ways around a model's safety training
- Jailbreaks only work on models that can read long prompts
- Longer prompts make models worse at following instructions
- Safety training stops jailbreaks once a model is large enough
shuffle:: true

#### Question: Choice
id:: e93372b8-c54c-490a-83a0-b1bcc3005a1e
content:: Which of these defenses against jailbreaks works separately from the model's own weights?
options::
- [x] A classifier that blocks harmful outputs before the user sees them
- Training the model on more examples of refused requests
- Rewarding refusals more strongly during fine-tuning
- Adding known jailbreak attempts to the training data
shuffle:: true

#### Question: Choice
id:: f8a3b7a3-f82b-44ac-a517-8dfbefc021c3
content:: Research has shown that fine-tuning an open-weight model on a small number of harmful examples can remove its refusals. Can a similar attack work against a closed model that customers can fine-tune through the company's API?
options::
- [x] Yes
- No

#### Question: Choice
id:: b07e70f6-d752-471f-8138-d9c9eb342e84
content:: Before release, a model refuses nearly all prompts in a large benchmark of known jailbreaks. Does this show it will resist jailbreaks that people find after release?
options::
- [x] No
- Yes

#### Question: Open
id:: c2d500fa-6d0c-4c4a-a679-7b05a18d2f9a
content:: Why might a model that reliably refuses dangerous requests in testing still give little protection against a determined person trying to misuse it?
assessment-instructions:: Score out of 100. 100 for any one of: testing can't cover every input, and new jailbreaks (rephrasing, role-play, other languages, automated search) keep being found; or if the weights are public or fine-tuning is offered, the refusals can be trained away. 50 for saying refusals "can be bypassed" with no reason why.

#### Question: Open
id:: 0b24d58c-6e6b-48d1-b766-7577abe66f9d
content:: Name one safeguard against misuse of an AI model that would still help if the model were jailbroken, and say why.
assessment-instructions:: Score out of 100. 100 for any one of, with a reason that it doesn't depend on the model's refusals: separate input or output classifiers, monitoring accounts and banning misusers, keeping weights secure, filtering dangerous knowledge out of training data, limiting who gets access, or real-world barriers such as screening DNA orders. 50 for a valid safeguard with no reason.

#### Question: Open
id:: 0a787cc9-bb57-4768-9e88-76c5036b7123
content:: Why can a jailbreak cause more harm when the model is an AI agent with access to tools than when it is a chatbot?
assessment-instructions:: Score out of 100. 100 for: the agent's actions (sending messages, running code, spending money) can take effect directly, often without a person checking first, while a chatbot only produces text a person must choose to act on. 50 for "agents can do more" with no mention of actions taking effect without a human.

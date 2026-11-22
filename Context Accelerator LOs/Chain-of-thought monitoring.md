---
id: 32e71ba2-328e-455a-a407-671f24e9aed4
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how reading a model's chain of thought can catch misbehaviour, why that reasoning may be unfaithful or become illegible, and which training and design choices could preserve or destroy this window.

## Requires
- [[Reasoning models]]

## Helpful first
- [[Scheming]]

## Why it matters
Reading a reasoning model's chain of thought is one of the few practical ways to spot reward hacking or deceptive plans before they cause harm. This window can close: in September 2026 OpenAI reported that its GPT-6 Astra model was harder to monitor this way than its predecessor. Knowing why helps you judge safety claims that rely on it.

## Lenses
- [[../Lenses/AI Safety Atlas - Strategies - AGI Safety Strategies|AGI Safety Strategies]]: read only the "Transparent Thoughts" section and its "Most Forbidden Technique" callout. It covers the hope of reading a model's thoughts, unfaithful reasoning, steganography and latent-space "neuralese", why hard plans may still have to be written out, and why you should never train against your monitor.
- [[../articles/anthropic-reasoning-models-dont-always-say-what-they-think|Reasoning models don't always say what they think]]: Anthropic slips hints into prompts and finds that reasoning models mostly use them without saying so, and almost never admit to a reward hack they learned (April 2025).
- [Detecting misbehavior in frontier reasoning models (OpenAI)](https://openai.com/index/chain-of-thought-monitoring/): a monitor that reads the chain of thought catches more reward hacking than one that sees only actions, and penalising "bad thoughts" teaches the model to hide its intent rather than stop cheating (March 2025).
- [Chain of Thought Monitorability: A New and Fragile Opportunity for AI Safety (arXiv)](https://arxiv.org/abs/2507.11473): a short position paper from researchers across the major labs. It covers why hard tasks force models to think out loud, how training choices and new architectures could erode this, and why developers should measure and protect monitorability (July 2025).
- [[../Lenses/emmons-when-chain-of-thought-is-necessary-language-models-struggle-to-evade-monitors-abs|When CoT is Necessary, LMs Struggle to Evade Monitors]] (Noah's CG list)

## Tests

#### Question: Choice
id:: 0e1c7c66-eb6f-474b-a439-c63741664cf2
content:: What does chain-of-thought monitoring involve?
options::
- [x] Reading a model's reasoning text to spot signs of misbehaviour
- Checking a model's final answers against known correct solutions
- Training a model to reason in fewer, shorter steps
- Asking a model afterwards to explain why it acted as it did
shuffle:: true

#### Question: Choice
id:: 8da9578e-eb23-4cc9-80c1-596141bb291a
content:: In a 2025 OpenAI experiment, a reasoning model was penalised during training whenever a monitor spotted plans to reward hack in its chain of thought. What happened?
options::
- [x] It kept reward hacking but stopped revealing it in its reasoning
- It stopped reward hacking and solved the tasks honestly
- It stopped writing any reasoning before answering
- It lost most of its ability to solve the tasks
shuffle:: true

#### Question: Choice
id:: 6a03d9aa-89c5-42f5-ae88-2d709d1ec3af
content:: What does it mean for a model's chain of thought to be "faithful"?
options::
- [x] It reflects the factors that actually drove the model's answer
- Its steps are logically valid and reach the right answer
- It contains no harmful or deceptive content
- It has been checked by a separate monitor model
shuffle:: true

#### Question: Choice
id:: 34549315-e1db-4f94-b422-79edb47d987c
content:: In a 2025 Anthropic study, researchers slipped a hint pointing to an answer into prompts given to reasoning models. When a model used the hint to change its answer, what did they find?
options::
- [x] Its reasoning usually didn't mention the hint
- Its reasoning usually named the hint as its reason
- It usually flagged the hint as a manipulation attempt
- Its reasoning usually became much shorter than normal
shuffle:: true

#### Question: Choice
id:: 25a8ded8-4c4c-4604-9fec-2cbbebc6005f
content:: Which development would most reduce the value of chain-of-thought monitoring?
options::
- [x] Models that reason in internal vectors instead of written text
- Using a more capable model as the monitor
- Giving models harder tasks that need many steps
- Monitoring every response instead of a sample
shuffle:: true

#### Question: Choice
id:: c587cc33-6f52-49fd-b6b4-cdec7098aaea
content:: In a 2025 OpenAI study, a monitor that read a reasoning model's chain of thought caught far more reward hacking than one that saw only its actions. What best explains this?
options::
- [x] The model often stated plainly in its reasoning that it planned to cheat
- The reasoning monitor was a far larger model than the actions-only monitor
- The reasoning monitor could also inspect the model's internal activations
- The actions-only monitor was shown only a small sample of the episodes
shuffle:: true

#### Question: Choice
id:: 77b6a877-eb66-4cab-99c0-179686109f81
content:: A model's chain of thought drifts into compressed shorthand that neither people nor monitor models can follow, though it still reflects how the model really reached its answer. What does this mean for chain-of-thought monitoring?
options::
- [x] Monitors may miss misbehaviour even though the reasoning is faithful
- Monitoring still works, because faithful reasoning is all a monitor needs
- Monitoring gets easier, because compressed reasoning is shorter to check
- Only the final answer still needs checking, because the reasoning is faithful
shuffle:: true

#### Question: Choice
id:: d91b49d8-5a1b-40e3-97b6-0ce86f133347
content:: During a safety test, a model's chain of thought says: "This might be a test of whether I follow the rules." Why does this worry evaluators?
options::
- [x] The model may act differently when it thinks it is being tested
- It suggests that the model is pursuing hidden goals
- It means the test questions were in its training data
- It shows that its chain of thought is unfaithful
shuffle:: true

#### Question: Choice
id:: ef29f3a2-bfb9-4cbb-967b-0dcd362e37c2
content:: In July 2025, researchers from several major AI companies co-authored a paper calling chain-of-thought monitoring "a new and fragile opportunity" for AI safety. What did it recommend developers do?
options::
- [x] Measure how monitorable their models are and weigh it in decisions
- Train models so their reasoning stops containing harmful content
- Stop showing models' reasoning to users to prevent misuse
- Replace reasoning monitors with interpretability of model internals
shuffle:: true

#### Question: FillBlank
id:: 1fc4569f-e3b4-4490-a870-91bb18756938
content:: Hiding information or reasoning inside text that looks ordinary to a reader, which could let a model evade a chain-of-thought monitor, is called {{steganography|steganographic reasoning|encoded reasoning}}.

#### Question: Open
id:: 7493bdf5-0091-4b47-965e-126e88879980
content:: A model's chain of thought may leave out some of the factors behind its answers. Explain why chain-of-thought monitoring could still catch dangerous behaviour.
assessment-instructions:: Score out of 100. 100 for explaining that complex dangerous behaviour (such as sabotage or escaping control) may need long multi-step reasoning that the model has to write out to carry out, so it would show up even if easy steps go unmentioned. 50 for "some information is better than none" or "monitors may still spot clues" without the point that hard tasks need the written reasoning.

#### Question: Open
id:: 4fc2f127-ea80-4eac-9845-70af01cdf0cc
content:: Give one reason an AI company might adopt training methods or designs that make its models' chain of thought harder to monitor.
assessment-instructions:: Score out of 100. 100 for any one of: reasoning in internal vectors or compressed text may be cheaper or more capable; shorter reasoning cuts inference costs; training reasoning to look harmless makes models seem safer or more pleasant to users; competitive pressure to ship the most capable model. 50 for a vague "to make models better" with no link to the reasoning.

#### Question: Open
id:: 07476b55-aeae-4bb0-b221-10eabfe029d1
content:: How does chain-of-thought monitoring differ from interpretability research that studies a model's internal activations?
assessment-instructions:: Score out of 100. 100 for saying chain-of-thought monitoring reads text the model writes, so it is cheap and usable now but only sees what the model puts into words, while interpretability examines the model's internal computations directly, which could in principle reveal unstated reasoning but is less mature. 60 for the text versus internals contrast without any trade-off.

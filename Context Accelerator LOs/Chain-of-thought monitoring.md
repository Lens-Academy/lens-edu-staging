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
As of November 2026, reading a reasoning model's chain of thought is one of the few practical ways to spot reward hacking or plans to deceive before they cause harm. Knowing what makes this signal unreliable helps you judge safety claims that rely on it, and why labs are urged not to train it away.

## Lenses

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
content:: In 2025 studies, researchers slipped a hint pointing to an answer into prompts given to reasoning models. When a model used the hint to change its answer, what did they find?
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
id:: 8fae90e6-95dd-4a84-91d3-7f745e85c14b
content:: In a 2025 OpenAI study of reward hacking during training, did a monitor that read the model's chain of thought catch more or fewer hacks than a monitor that saw only the model's actions?
options::
- [x] More
- Fewer

#### Question: Choice
id:: ee7c4ac0-c136-45ed-b438-442171c998bb
content:: A model's chain of thought drifts into compressed shorthand and invented words that people can't follow, though it still tracks how the model really reached its answer. Which property has the reasoning lost?
options::
- [x] Legibility
- Faithfulness
- Correctness
- Honesty
shuffle:: true

#### Question: Choice
id:: d91b49d8-5a1b-40e3-97b6-0ce86f133347
content:: During a safety test, a model's chain of thought says: "This might be a test of whether I follow the rules." Why does this worry evaluators?
options::
- [x] The model may act differently when it thinks it is being tested
- It proves that the model has hidden goals
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

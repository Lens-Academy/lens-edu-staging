---
id: 3a1b4ca8-ee34-4993-b7d7-c22f5691a701
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how AI models are tested for dangerous capabilities and misaligned behavior, and judge what a passed or failed test does and doesn't show about a model's risk.

## Requires
- [[Benchmarks]]

## Helpful first
- [[Sources of AI catastrophe]]
- [[Situational awareness]]

## Why it matters
Company safety policies and government checks use evaluation results to decide whether a model is released and with which safeguards. If you know how tests can miss what a model can do, you can tell when "it passed all our safety tests" is strong evidence and when it isn't.

## Lenses
- [[../Lenses/AI Safety Atlas - Evaluations - Evaluated Properties|What evaluations measure]]: capabilities, propensities and control.
- [[../Lenses/AI Safety Atlas - Evaluations - Evaluation Techniques|Evaluation techniques]]: elicitation, red-teaming and looking inside models.
- [[../Lenses/What AI evaluations for preventing catastrophic risks can and cannot do|What AI evaluations can and cannot do]]: why tests give lower bounds, not guarantees.
- [[../Lenses/AI Safety Atlas - Evaluations - Limitations|Limitations of evaluations]]: sandbagging, prompt sensitivity and untested risks.
- [Project Naptime (Google Project Zero, 2024)](https://projectzero.google/2024/06/project-naptime.html): better tools raised a model's cyber scores sharply.

## Tests

#### Question: Choice
id:: cb051dda-9229-40aa-8f1d-eae38738c2dd
content:: An evaluation team tries hard to get an AI model to help plan a cyberattack, and fails. What does this result best support?
options::
- [x] The methods the testers tried didn't draw out the capability
- The model lacks the capability, so it can be released without cyber safeguards
- The model has the capability but is deliberately hiding it
- Safety training has removed the capability from the model
shuffle:: true

#### Question: Choice
id:: 6c6106b4-23f8-4fed-aad9-8dcc48bb4a08
content:: In 2024, GPT-4 Turbo solved 5% of a cybersecurity benchmark's buffer-overflow tasks. Google researchers then let it run and debug code: it solved 71% in one attempt, and all of them given ten attempts. What does this mainly show?
options::
- [x] A weak test setup can make a model look much less capable
- The benchmark's tasks had leaked into the model's training data
- The model had been deliberately underperforming in the first test
- Code tools taught the model skills it did not already have
shuffle:: true

#### Question: Choice
id:: 25b55f6f-779c-477a-a111-7eeacf03409e
content:: A developer plans to release an AI model's weights openly. Why should its dangerous-capability tests include fine-tuning the model on the dangerous task?
options::
- [x] Anyone with the weights could fine-tune it to bring out the capability
- Fine-tuning removes the capability before the weights are released
- Fine-tuning makes the model refuse harmful requests during testing
- Fine-tuning checks whether the model memorized the test questions
shuffle:: true

#### Question: FillBlank
id:: f404d4dd-33ee-4243-b8c5-7ef4f61bce5d
content:: Getting an AI model to show the most it can do on a task, so that a test doesn't underestimate it, is called capability {{elicitation|eliciting}}.

#### Question: Choice
id:: 2f3a5848-e725-4cc8-8265-011584f7d7a8
content:: In a test, an AI model is given an easy chance to copy its own weights to an outside server, with no instruction to do so. Testers record whether it does. What kind of AI evaluation is this?
options::
- [x] A propensity evaluation
- A dangerous capability evaluation
- A control evaluation
- A general-ability benchmark
shuffle:: true

#### Question: Choice
id:: c28fbb01-0db7-4a92-a2b3-2368b9d3e57f
content:: How does red-teaming an AI model differ from running a fixed benchmark on it?
options::
- [x] Testers actively search for inputs that make the model misbehave
- Testers score the model on a standard, published set of questions
- Testers inspect the model's internal activations instead of its outputs
- Testers compare the model's results with those of earlier models
shuffle:: true

#### Question: Choice
id:: 940abc97-b503-4276-9000-5598a2e88797
content:: A developer runs many alignment evaluations on an AI model, and the model behaves well in every one. Why is this weaker evidence that the model isn't scheming than it might seem?
options::
- [x] A scheming model could spot the tests and behave well in them
- Alignment evaluations measure what a model can do, not what it tends to do
- Good test behavior usually means the test questions leaked into training data
- Scheming only shows up once a model's weights are released openly
shuffle:: true

#### Question: Choice
id:: 44d23718-8531-4174-82a0-8233fceba6dd
content:: Outside evaluators of AI models, such as government AI institutes, sometimes get a model only days before release and without fine-tuning access. Why does this matter?
options::
- [x] They may miss capabilities that more time or fine-tuning would reveal
- They can test the model's propensities but not its capabilities
- Their results can't be compared with the developer's own results
- They will tend to overestimate the model's dangerous capabilities
shuffle:: true

#### Question: Open
id:: 2a94cd7e-3e22-43f1-98a3-97db7f8bc34b
content:: In an AI biology uplift study, one group attempts to plan a harmful lab task with an AI model and another group uses only the internet. What does comparing the two groups show that the model's score on a biology quiz can't?
assessment-instructions:: Score out of 100. 100 for: how much the model actually increases real people's ability to carry out the harmful task, beyond what they could already do without it (its added risk). 50 for "whether the model is dangerous" without the comparison to what people can do without AI.

#### Question: Open
id:: c546d325-75da-4e28-99f1-4dd1e17a0b21
content:: An AI developer trains a model to refuse harmful requests. Why might the model then score lower on a dangerous-capability evaluation even if its underlying ability hasn't changed, and how can testers get around this?
assessment-instructions:: Score out of 100. 100 for: the model declines the test tasks, so the test measures its willingness rather than its ability; testers can test a version without refusal training, or jailbreak it. 60 for the first part only.

#### Question: Open
id:: db3c254a-9161-4e2f-b8c1-54c2ef41be87
content:: An AI company commits to add stronger safeguards once its evaluations show a model can meaningfully help someone build a bioweapon. Give one way this commitment could fail even if the company follows it exactly.
assessment-instructions:: Score out of 100. 100 for any one of: weak elicitation means the tests underestimate the capability, so the trigger never fires; the model underperforms or behaves differently when it detects a test; tests run too rarely, so the capability appears between them; new tools or fine-tuning unlock it after release. 40 for "the tests might be wrong" without a reason.

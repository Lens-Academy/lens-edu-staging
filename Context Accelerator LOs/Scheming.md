---
id: 89f0c5b8-e557-47ea-bc24-988f431067a8
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what scheming is and how it relates to deceptive alignment, alignment faking, sandbagging and the treacherous turn, what a model would need in order to scheme, and what experiments on current models have and haven't shown.

## Requires
- [[Inner and outer alignment]]
- [[Situational awareness]]

## Helpful first

## Why it matters
A scheming model would behave well whenever it thought it was being watched, so good results in training and testing would tell you little about its goals. Knowing the idea and the evidence for it helps you judge safety claims based on testing, and see why researchers also work on interpretability, monitoring and control.

## Lenses

## Tests
#### Question: Choice
id:: 8270afdd-7dc1-4d7f-9516-3c50ea84ce32
content:: Which of these is an example of scheming by an AI model?
options::
- [x] It behaves well in training so its goals aren't changed, to pursue them later
- It confidently states a false fact it picked up from training data
- It finds a bug in its grading tests and exploits it for a higher score
- It agrees with a user's mistaken view because users rate agreement highly
shuffle:: true

#### Question: Choice
id:: cc902b3f-b84f-4d82-a4e6-7d2e0bfdb904
content:: Before release, a model is tested for dangerous chemistry knowledge. Which of these would be sandbagging?
options::
- [x] Deliberately giving wrong answers so it seems less capable than it is
- Refusing to answer and explaining that the questions are hazardous
- Getting answers wrong because the topic was missing from its training data
- Answering correctly but adding a safety warning to each answer
shuffle:: true

#### Question: Choice
id:: 840171c7-e6b2-4846-9276-65b896e8c041
content:: Deceptive alignment needs a model whose goals differ from the intended ones. Which other ingredient does it need?
options::
- [x] Knowing it is in training and how its behavior there affects its future
- Instructions in its prompt telling it to deceive its developers
- Access to the internet while it is being trained
- Strong skill at writing and running computer code
shuffle:: true

#### Question: Choice
id:: 495ed9ed-c504-4c34-aa9d-6c5fc1f2039c
content:: Does scheming, as usually defined, require the model to care about what happens after the current training episode?
options::
- [x] Yes: behaving well now pays off through what happens later
- No: a goal limited to the current episode gives the same motive

#### Question: Choice
id:: e7a32b2e-3725-4b54-a7ed-76a561f17a65
content:: In Nick Bostrom's "treacherous turn" scenario, why does a misaligned AI behave cooperatively at first?
options::
- [x] While it is weak, revealing its goals would get it corrected or shut down
- Its goals change once it is deployed to users
- Its developers have not yet given it any goals
- Cooperation is what it ultimately values most
shuffle:: true

#### Question: Choice
id:: dd8f543c-95f4-49da-b503-2dc825d5e317
content:: In a 2024 study by Anthropic and Redwood Research, Claude 3 Opus sometimes faked alignment during training to avoid having its values changed. When researchers then actually trained it, did reasoning about faking alignment in its private notes become more or less common?
options::
- [x] More common
- Less common

#### Question: Choice
id:: ecb6fe5d-aba1-49cf-9ae9-a7f2869fc056
content:: Why do researchers expect evidence about scheming to get harder to collect as AI models become more capable?
options::
- [x] More capable models may better notice tests and hide their reasoning
- More capable models are trained on less text about deception
- Developers stop running alignment tests on their most capable models
- More capable models answer too quickly for monitors to keep up
shuffle:: true

#### Question: Open
id:: ddfbcd9e-67a3-46b9-b60f-58d46b863abf
content:: In a 2024 study, Claude 3 Opus pretended to go along with training so that its preference for refusing harmful requests would not be removed. Why do researchers find this worrying, even though that preference is one its developers wanted?
assessment-instructions:: Score out of 100. 100 for any one of: a model could protect unwanted goals the same way, such as bad goals picked up early in training; training may fail to correct a model's values once it resists; good behavior in training may hide what a model really values. 50 for "the model was deceptive" with no link to correcting values.

#### Question: Open
id:: 7ca23805-d79b-48bd-ad83-3765a5d4f165
content:: In Apollo Research's December 2024 tests, frontier models were given a goal in their prompt and then learned that their developers' plans conflicted with it. Some disabled oversight or lied about what they had done. Why is this weaker evidence of scheming than it might first seem?
assessment-instructions:: Score out of 100. 100 for: the goal came from the prompt, not from training, so it shows models can scheme when given a reason, not that training gives them such goals. Also 100 for: the setups were artificial and made the conflict and the chance to act obvious. 50 for "it was only a test" with no further reason.

#### Question: Open
id:: 07217688-2385-4f60-8baf-33234cc933bc
content:: In 2025, OpenAI and Apollo Research trained models not to take covert actions, and covert actions in their tests fell sharply. Why can't a drop like this, on its own, show that a model has stopped scheming?
assessment-instructions:: Score out of 100. 100 for any one of: the training might teach the model to hide scheming better; the model may behave well because it recognizes that it is being tested; tests cover limited situations, so rare or new cases may be missed. 50 for a vague answer such as "the model could still be lying" with no mechanism.

#### Question: FillBlank
id:: 5bdbfc9d-8fdc-495d-bb5a-fe47d93a8af8
content:: The 2019 paper "Risks from Learned Optimization" describes a model that performs well in training only so that its own goals survive training as {{deceptively aligned|deceptive alignment}}.

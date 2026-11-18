---
id: ba0c4ae2-0fa1-477c-8e27-95e8ee677f96
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Recognise the main alignment training methods by name (RLHF, RLAIF and constitutional AI, deliberative alignment, adversarial training, character training), say roughly how each works, and explain why none of them guarantees that a model has good goals.

## Requires
- [[RLHF]]

## Helpful first

## Why it matters
Labs and researchers name these methods constantly, often as reasons to trust a model. Knowing how each works shows you what it actually checks: behaviour on the cases someone tested and judged. Without that, it's easy to mistake a list of training methods for evidence that a model is safe.

## Lenses

## Tests

#### Question: Choice
id:: 5efd2948-ce8d-40f9-9ab6-af7f0c201ef2
content:: How does RLAIF (reinforcement learning from AI feedback) differ from RLHF?
options::
- [x] An AI model, not human raters, gives the preference judgments
- The reward comes from answers checked automatically, like unit tests
- The model is pretrained on AI-written text instead of human text
- The reward comes from the model's own confidence in its answers
shuffle:: true

#### Question: Choice
id:: defe2d7f-2bfa-4444-8099-fb7681ac8322
content:: In Anthropic's constitutional AI method, what is the "constitution"?
options::
- [x] Written principles an AI uses to critique and judge model outputs
- A safety agreement signed by the leading AI labs
- Hard-coded rules that filter the model's outputs when it runs
- A dataset of human-rated conversations used to train a reward model
shuffle:: true

#### Question: FillBlank
id:: f26c89e9-0bb5-4032-9224-496150b86224
content:: OpenAI's method of training a reasoning model to recall its written safety specification and reason about it in its chain of thought before answering is called {{deliberative alignment}}.

#### Question: Choice
id:: 5022e8bd-78c7-42f1-afb0-af62bf00bebb
content:: Which of these is adversarial training of a language model?
options::
- [x] Finding inputs that make the model misbehave, then training it to behave well on them
- Training two copies of the model to compete against each other at a game
- Rewarding the model for finding security bugs in other programs' code
- Training the model to argue against its own answers before giving them
shuffle:: true

#### Question: Choice
id:: 2fc1fe98-ae4c-4a32-9cf4-ccb1a57874b9
content:: In Anthropic's 2024 "Sleeper Agents" study, models were trained to behave unsafely only when a hidden trigger appeared. What did adversarial training against the unsafe behaviour tend to do?
options::
- [x] Teach the models to recognise their trigger better, hiding the behaviour
- Remove the behaviour in the largest models but not in smaller ones
- Remove the behaviour reliably once enough attacks had been found
- Make the models refuse ordinary requests while leaving the trigger untouched
shuffle:: true

#### Question: Choice
id:: f340f592-45d9-4dca-9663-c128220c18d1
content:: What is Anthropic's "character training" of Claude mainly aimed at?
options::
- [x] Giving the model stable traits such as curiosity and honesty
- Teaching the model to role-play many fictional characters well
- Removing personality so the model answers in a neutral voice
- Teaching the model to copy each user's writing style
shuffle:: true

#### Question: Choice
id:: bdc9aa0f-9938-4892-8d11-682e7462eb20
content:: In AI safety, what does "prosaic alignment" refer to?
options::
- [x] Aligning AI built with current machine-learning methods, without new fundamental breakthroughs
- Aligning a model by having it write out its values in plain prose
- Alignment work that focuses on everyday harms rather than existential risk
- Aligning AI by proving mathematically that it meets a safety specification
shuffle:: true

#### Question: Choice
id:: 29d3e43f-aa98-4e3b-b7c4-02cab5b5e75f
content:: What limitation do RLHF, RLAIF, constitutional AI and adversarial training share?
options::
- [x] They shape behaviour on the inputs tried, without checking what goals the model learned
- They work on small research models but have not been used on frontier models
- They need the model's weights to be public so outsiders can check them
- They can be applied only before pretraining, so they cannot fix later problems
shuffle:: true

#### Question: Choice
id:: 0bca2db8-a291-4fc1-bc6e-201fcb348710
content:: In 2025, OpenAI and Apollo Research used deliberative alignment to train models against covert, deceptive actions. Covert actions dropped sharply. What complicated this result?
options::
- [x] The models more often noticed they were being tested, which may explain part of the drop
- The models lost much of their ability to solve ordinary coding tasks
- The covert actions returned within days of normal use by customers
- The models stopped writing any chain of thought, so nothing could be checked
shuffle:: true

#### Question: Choice
id:: 56d82388-29d0-4cc8-8a55-e20bac47befe
content:: Which weakness is a model trained with RLAIF most likely to inherit?
options::
- [x] The blind spots and biases of the AI model giving the feedback
- The high cost and slowness of collecting ratings from people
- Overfitting to one human rater's personal tastes
- Being unable to use knowledge from its pretraining data
shuffle:: true

#### Question: Open
id:: 28ed58c0-80af-4b9c-8a20-653603d43f0a
content:: Why do AI labs use AI feedback (as in RLAIF or constitutional AI) rather than relying only on human feedback?
assessment-instructions:: Score out of 100. 100 for any one clear reason: AI feedback is much cheaper or faster and scales to far more examples; it applies written principles consistently; it can cover tasks or volumes where human rating is impractical. 50 for a vague answer like "it's better" or "it's automated" without saying why that helps.

#### Question: Open
id:: a2f8d743-4088-4022-9154-58587384819e
content:: Name one alignment training method other than RLHF and give one limitation of it.
assessment-instructions:: Score out of 100. 100 for a real method (RLAIF, constitutional AI, deliberative alignment, adversarial training, character training) with a fitting limitation, e.g. inherits the AI judge's blind spots; depends on who writes the principles; relies on chain of thought reflecting real reasoning; can teach models to hide bad behaviour or only patches attacks found; shapes trained behaviour, not underlying goals. 50 for a correct method with no or a wrong limitation.

#### Question: Open
id:: a88058b2-74d3-42b6-8eb6-2b0802ae4e27
content:: A lab says its model is safe because it was trained with RLHF, constitutional AI and adversarial training. Why is this weak evidence that the model won't pursue harmful goals in new situations?
assessment-instructions:: Score out of 100. 100 for any one clearly explained reason: these methods reward behaviour on tested inputs and can't tell a truly aligned model from one that learned to look aligned; good behaviour may not generalise to new situations; judges (human or AI) can be fooled; a model may behave differently when it thinks it isn't being tested. 50 for "training isn't perfect" with no mechanism.

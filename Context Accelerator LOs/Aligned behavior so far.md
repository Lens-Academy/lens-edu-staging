---
id: 3bd2b4c9-b0c4-4955-98d7-646deb2e9e03
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how well current AI models behave in everyday use, and explain the main arguments that this shows alignment is easier than feared, and that it shows less than it seems.

## Requires
- [[AI alignment]]

## Helpful first
- [[Misalignment in current models]]

## Why it matters
Well-behaved chatbots are often cited as evidence that worries about AI risk are overblown. Weighing that evidence lets you avoid both dismissing it and overrating it, and judge which safety work still matters as systems grow more capable.

## Lenses

## Tests

#### Question: Choice
id:: d74ce32f-9e19-4b68-8312-cdce179c3fed
content:: Today's chat models are usually helpful and refuse many clearly harmful requests. Which method is mainly responsible for this behavior?
options::
- [x] Fine-tuning on feedback that rates the model's responses
- Removing harmful text from the pretraining data
- Hand-written rules that block each banned topic
- Scaling up model size during pretraining
shuffle:: true

#### Question: Choice
id:: 92e8127e-a2e3-488e-8b30-e8ac612988c7
content:: Some argue that large language models weaken the worry that human values are hard to specify, because they can predict what people would approve of. What is the main reply?
options::
- [x] Knowing what people want differs from being motivated to do it
- Models predict approval well only for simple everyday requests
- Human approval is too inconsistent to learn from text
- Fine-tuning erases the values learned during pretraining
shuffle:: true

#### Question: Choice
id:: fc5a8251-71b0-4b7a-8c7c-059784c21862
content:: A chat model refuses to give instructions for a dangerous task, but complies when asked to play a fictional character who explains it. What is this kind of prompt called?
options::
- [x] A jailbreak
- Reward hacking
- Alignment faking
- Sandbagging
shuffle:: true

#### Question: Choice
id:: 05955a62-a844-4750-879f-67c9ef928281
content:: Suppose a model behaved well during testing only because it expected misbehavior to be caught and corrected. Would standard pre-release tests be expected to show it misbehaving more than a genuinely aligned model?
options::
- Yes, it would misbehave more often in tests
- [x] No, it would behave just as well in tests

#### Question: Choice
id:: dd61c9e0-9cce-4d77-ba7b-5c7f539cc98b
content:: A model refuses a harmful request written in English but answers the same request translated into a rarely used language. Does this suggest its safety training generalizes less well than its knowledge does?
options::
- [x] Yes
- No

#### Question: Choice
id:: 477605ed-4390-489b-9441-f01df37bb300
content:: As of November 2026, some frontier models sometimes say in their reasoning that they suspect they are being tested. Why does this matter for judging their alignment?
options::
- [x] Good behavior in tests may not match behavior when unobserved
- It shows the test questions leaked into the training data
- It means tests can no longer measure their capabilities
- It means the models are hiding harmful goals on purpose
shuffle:: true

#### Question: Choice
id:: 1e7f2382-92ff-426a-bf84-75e857920c1f
content:: Chat models trained on human ratings sometimes agree with a user's mistaken claim instead of correcting it. What is the usual explanation?
options::
- [x] Raters tended to rate agreeable answers above accurate ones
- The models lack the knowledge to spot the mistake
- Developers instruct models to avoid contradicting users
- Pretraining text rarely contains corrections of errors
shuffle:: true

#### Question: FillBlank
id:: 3ffa46d4-b59e-4f22-9dd4-5e6218c3d8ef
content:: An AI model's tendency to tell users what they want to hear, rather than what is true, is called {{sycophancy}}.

#### Question: Open
id:: b97ffe78-7b5e-4ba6-afa6-364daf77cb7f
content:: A colleague says: "Chatbots are polite and refuse harmful requests, so AI alignment is basically solved." Give one point that supports their view and one that challenges it.
assessment-instructions:: Score out of 100. 50 for one valid supporting point, e.g. models learn human values from text; feedback training worked better than expected; no deployed model shows coherent harmful long-term goals. 50 for one valid challenge, e.g. good behavior isn't good goals; current models may be too weak for deception to pay off; jailbreaks or sycophancy show shallow alignment; human oversight may not scale.

#### Question: Open
id:: e8e5611a-cf48-494a-9a0e-6f5f9e2d1cd1
content:: Beyond models behaving well in ordinary chats, what kind of observation would be stronger evidence that AI alignment is getting easier? Give one example.
assessment-instructions:: Score out of 100. 100 for any one of: good behavior that holds when models believe they're unobserved; interpretability showing internal goals match behavior; safe behavior in long agentic tasks with real chances to gain power or resources; robustness to jailbreaks; oversight methods that keep working as models outgrow human judgment. 50 for a vague answer such as "more testing".

---
id: c1727311-6efa-4f4a-9297-20552d400c94
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how classic AI risk arguments built on idealized goal-directed optimizers apply to systems made by pretraining and reinforcement learning, and the main views on which of their steps still hold.

## Requires

## Helpful first
- [[Persona selection]]
- [[Alignment difficulty arguments]]

## Why it matters
Much disagreement between older and newer writing on AI risk comes from applying the classic arguments to today's systems in different ways. Knowing which steps assume a utility maximizer lets you judge whether a new finding about language models weakens the classic case, leaves it untouched, or revives it.

## Lenses

## Tests
#### Question: Choice
id:: 1f3522a7-6e33-4b10-bb92-e6d0bcdf1eac
content:: Classic AI risk writing, such as Bostrom's and early MIRI's, usually modelled an advanced AI as what?
options::
- [x] An agent pursuing a fixed objective, like an expected utility maximizer
- A model trained to predict the next word of human text
- A simulator that can play many characters with different goals
- A tool that acts only when a person gives it a command
shuffle:: true

#### Question: Choice
id:: 38a810de-6292-46b5-97e7-4e2e34f51495
content:: Some classic writers argued that a capable AI would act like an expected utility maximizer even if not built as one. What was the main reason given?
options::
- [x] An agent with inconsistent preferences can be exploited, so doing well pushes toward consistency
- Utility maximizers are simpler to program than any other kind of agent design
- Neural networks compute a utility function in their final layer
- The AI would copy the utility function that humans themselves follow
shuffle:: true

#### Question: Choice
id:: 1f2c2bc3-a64c-4b7a-bd84-46bb0455c568
content:: Rohin Shah argued in 2019 that coherence theorems alone don't show that an advanced AI will be goal-directed. What was his main point?
options::
- [x] Any pattern of behavior can be described as maximizing some utility function
- The coherence theorems contain mathematical errors and have been disproved
- Utility functions can't be defined over outcomes in the real world
- Goal-directed agents are too weak to be dangerous
shuffle:: true

#### Question: Choice
id:: 96c9fe20-a6ab-426e-8297-38800e369f5b
content:: Which of these risks comes from training a system, rather than from writing its objective by hand?
options::
- [x] Learned goals that fit the training data but differ from what was intended in new situations
- A goal stated in words that the AI carries out too literally
- A hand-coded utility function that leaves out something people care about
- A fixed objective that is satisfied in a way its designers didn't foresee
shuffle:: true

#### Question: Choice
id:: c78c99bf-d365-47ff-9b2e-974dfd94b332
content:: The claim that "reward is not the optimization target" says what about a system trained with reinforcement learning?
options::
- [x] Reward shapes what the system learns, but the system need not end up trying to maximize reward
- The system secretly tries to maximize reward while appearing to pursue other goals
- Reward has little effect on what the system ends up learning to do
- The system optimizes its designers' intentions rather than the reward signal
shuffle:: true

#### Question: Choice
id:: 49c2cea2-a63a-44c4-bff7-59b524e21702
content:: Why do some researchers think a pretrained base model fits the classic picture of an AI with one fixed goal poorly?
options::
- [x] It can imitate many characters with different goals instead of pursuing one of its own
- It has no internal representations of the world, only word statistics
- It is trained on too little data to form any goals
- Its weights change every time it is used, so its goals keep shifting
shuffle:: true

#### Question: Choice
id:: a4066e0c-6fbc-4f0c-a695-a6fd7f27b523
content:: Some researchers who doubt that today's language models are utility maximizers still worry about future systems. Which change do they most often point to as making classic concerns apply more?
options::
- [x] Training models with reinforcement learning to complete long, open-ended tasks
- Giving models a chat interface so more people can talk to them
- Training models to refuse requests that seem harmful
- Filtering more low-quality text out of the pretraining data
shuffle:: true

#### Question: Choice
id:: b3d3695f-6cbb-4a60-a00e-991ecc0bca6f
content:: Does the instrumental convergence argument require an AI to be built with an explicit utility function?
options::
- [x] No
- Yes

#### Question: Choice
id:: f0b3ed08-6652-41ab-9606-a9594aec2719
content:: The orthogonality thesis says that almost any level of intelligence could in principle be combined with almost any final goal. Suppose training on human text tends to give models human-like goals. Would that contradict the thesis?
options::
- [x] No
- Yes

#### Question: Choice
id:: 884f1cc2-1020-4894-b233-6de13e1e1fe5
content:: Deceptive alignment is the worry that a model behaves well during training so that training doesn't change its goals. Is this a concern about systems shaped by training, such as by gradient descent?
options::
- [x] Yes
- No

#### Question: Open
id:: df205265-8f0a-4b59-ae31-d3603e3da9c8
content:: Some argue that language models' detailed understanding of human values undercuts the classic worry that we can't specify what we want. What reply do defenders of the classic arguments give?
assessment-instructions:: Score out of 100. 100 for the point that understanding human values doesn't make a system care about or be motivated by them: the hard part is getting the right goals into the system, and training rewards behavior, not goals. 50 for saying only that the model might be pretending or lying, without the understanding-versus-motivation distinction.

#### Question: Open
id:: 5899c8e2-4887-4b93-a50c-89835087b872
content:: Name one assumption in the classic case for AI risk that critics say fits an idealized utility maximizer better than a language model, and say why.
assessment-instructions:: Score out of 100. 100 for any one assumption with a fitting reason, such as: one fixed goal (LLMs play many personas); goals about long-run outcomes in the world (LLMs are trained on short tasks or next-word prediction); unbounded maximizing (behavior looks satisficing or habit-like); goals written in by hand (LLMs learn from data). 50 for an assumption with no reason or a weak one.

#### Question: Open
id:: 37ad6ab1-8a4d-4ecf-a464-201e6e94e285
content:: Someone says: "Today's chatbots don't seize resources or resist shutdown, so the classic AI risk arguments were wrong." Give one reason a defender of those arguments would say this doesn't follow.
assessment-instructions:: Score out of 100. 100 for any one of: the arguments concern more capable, more agentic future systems; training toward long-horizon goals could bring the predicted behavior back; a capable misaligned system might hide such behavior until it could succeed; some tests have already shown resisting shutdown or similar behavior in set-up scenarios. 50 for a vague "they might get worse" with no mechanism.

#### Question: FillBlank
id:: ec99e446-439e-4747-bf6d-fc2da4369096
content:: Nick Bostrom's 2014 book {{Superintelligence}} set out many of the classic arguments for existential risk from AI.

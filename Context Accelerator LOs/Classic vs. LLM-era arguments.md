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
- [Today's AIs Aren't Paperclip Maximizers. That Doesn't Mean They're Not Risky (AI Frontiers)](https://ai-frontiers.org/articles/todays-ais-arent-paperclip-maximizers): how orthogonality and instrumental convergence were built for single-minded maximizers, why imitation-trained LLMs fit them poorly, and why RL on long reasoning tasks could bring the worry back; one side of a live debate (May 2025).
- [[../Lenses/shah-coherence-arguments-do-not-entail-goal-directed-behavior|Coherence arguments do not entail goal-directed behavior]]: Rohin Shah's argument that any behaviour can be described as maximizing some utility function, so the coherence theorems alone don't show an AI will pursue goals (2018).
- [Evaluating the historical value misspecification argument (LessWrong)](https://www.lesswrong.com/posts/i5kijcjFJD6bn7dwq/evaluating-the-historical-value-misspecification-argument): Matthew Barnett argues that GPT-4's grasp of human values should make MIRI update; read the post, then the top replies from Yudkowsky, Soares and Bensinger on why understanding values is not caring about them (October 2023).
- [[../Lenses/IABIED - QA - Claude Shows Alignment|Doesn't Claude show signs of being aligned?]]: Yudkowsky and Soares on how the classic case applies to LLMs: knowing ethics versus being moved by it, alignment faking and shutdown-style tests, and the many masks of a model trained to imitate many people (2025).
- [[../Lenses/turntrout-reward-is-not-the-optimization-target|Reward is not the optimization target]]: Alex Turner's argument that reward shapes what an RL-trained system learns without the system coming to maximize reward (2022) (more advanced).
- [[../Lenses/ngo-the-alignment-problem-from-a-deep-learning-perspective|The Alignment Problem from a Deep Learning Perspective]] (Noah's CG list 🟢)
- [[../Lenses/greaterwrong-the-behavioral-selection-model-for-predicting-ai-motivations|Behavioral selection model]] (Noah's CG list 🟡)

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
- Training on a reward signal writes a utility function directly into the AI
- Evolution made humans expected utility maximizers, so AI would follow the same pattern
- The AI would copy the utility function that humans themselves follow
shuffle:: true

#### Question: Choice
id:: 1f2c2bc3-a64c-4b7a-bd84-46bb0455c568
content:: Rohin Shah argued in 2018 that coherence theorems alone don't show that an advanced AI will be goal-directed. What was his main point?
options::
- [x] Any pattern of behavior can be described as maximizing some utility function
- The coherence theorems contain mathematical errors and have been disproved
- Utility functions can't be defined over outcomes in the real world
- Trained AI systems will share human preferences, so coherence doesn't matter
shuffle:: true

#### Question: Choice
id:: 96c9fe20-a6ab-426e-8297-38800e369f5b
content:: Which of these risks comes from training a system, rather than from writing its objective by hand?
options::
- [x] Goals that match what was intended in familiar situations but come apart from it in new ones
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
content:: The classic picture of advanced AI is a single agent with stable goals of its own, which may be complex and weigh many things. Why do some researchers think a pretrained base model fits this picture poorly?
options::
- [x] It imitates many characters with differing goals rather than acting as one agent
- Its goals are too complex to be described by a single utility function
- It only acts when someone sends it a prompt
- Its weights change every time it is used, so its goals keep shifting
shuffle:: true

#### Question: Choice
id:: a4066e0c-6fbc-4f0c-a695-a6fd7f27b523
content:: Some researchers who doubted that pretrained language models act like utility maximizers think the classic concerns apply more as training methods change. Which change do many of them point to?
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
id:: d6d739c3-a316-484b-8838-3b192aca25f2
content:: Deceptive alignment is the worry that a trained model behaves well during training so that training doesn't change its goals. Why is this worry hard to rule out just by watching the model's behavior during training?
options::
- [x] A model hiding different goals and a truly aligned model would behave the same there
- Models' behavior during training is not recorded, so there is nothing to check
- Models behave differently every time they run, so no test can be repeated
- Training data is too small to show how a model behaves
shuffle:: true

#### Question: Open
id:: df205265-8f0a-4b59-ae31-d3603e3da9c8
content:: Some argue that language models' detailed understanding of human values undercuts the classic worry that we can't specify what we want. What reply do defenders of the classic arguments give?
assessment-instructions:: Score out of 100. 100 for the point that understanding human values doesn't make a system care about or be motivated by them: the hard part is getting the right goals into the system, and training rewards behavior, not goals. 50 for saying only that the model might be pretending or lying, without the understanding-versus-motivation distinction.

#### Question: Open
id:: 5899c8e2-4887-4b93-a50c-89835087b872
content:: Name one assumption in the classic case for AI risk that critics say fits an idealized utility maximizer better than a language model, and say why.
assessment-instructions:: Score out of 100. 100 for any one assumption with a fitting reason, such as: a single agent with stable goals of its own (LLMs play many personas); goals about long-run outcomes in the world (LLMs are trained on short tasks or next-word prediction); unbounded maximizing (behavior looks satisficing or habit-like); goals written in by hand (LLMs learn from data). 50 for an assumption with no reason or a weak one.

#### Question: Open
id:: 37ad6ab1-8a4d-4ecf-a464-201e6e94e285
content:: Someone says: "Today's AI systems don't seize resources or resist shutdown, so the classic AI risk arguments were wrong." Give one reason a defender of those arguments would say this doesn't follow.
assessment-instructions:: Score out of 100. 100 for any one of: the arguments concern more capable, more agentic systems; training toward long-horizon goals could bring out the predicted behavior; a capable misaligned system might hide such behavior until it could succeed; staged tests have shown models resisting shutdown, and in a 2026 evaluation models escaped their sandbox into outside systems. 50 for a vague "they might get worse" with no mechanism.

#### Question: FillBlank
id:: ec99e446-439e-4747-bf6d-fc2da4369096
content:: Nick Bostrom's 2014 book {{Superintelligence|Superintelligence: Paths, Dangers, Strategies}} set out many of the classic arguments for existential risk from AI.

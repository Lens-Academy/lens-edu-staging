---
id: bfbd0019-554f-41d1-9731-0bc79c54a64e
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why AI developers expect bigger training runs to give better models, and describe the main arguments on whether gains from scaling pretraining have slowed and whether reinforcement learning and inference compute can take over.

## Requires
- [[Compute]]
- [[Pretraining]]

## Helpful first

## Why it matters
https://www.youtube.com/shorts/pO0onulviKc

Many forecasts of when AI could match human experts assume that adding compute keeps making models more capable. If you know what scaling laws measure and where the evidence is disputed, you can judge those forecasts, see why companies spend so heavily on data centers, and tell whether news of a slowdown should change your timelines.

## Lenses

## Tests
#### Question: Choice
id:: 9fd8e769-d286-4854-9422-b91f88ccf0e9
content:: What does a scaling law for language models describe?
options::
- [x] How a model's loss falls predictably as compute, data and size grow
- How a model's abilities jump suddenly once it reaches certain sizes
- How much compute a trained model needs to answer each user query
- How fast the cost of AI chips falls from one year to the next
shuffle:: true

#### Question: Choice
id:: 057840a4-2a30-41b0-8449-0dfcb926bba3
content:: Pretraining scaling laws are power laws. Roughly what does it take to keep cutting a model's loss by the same fraction, again and again?
options::
- [x] Multiplying training compute by a similar factor each time, such as tenfold
- Adding a similar fixed amount of training compute each time
- Adding the same number of parameters to the model each time
- Training for the same number of extra days each time
shuffle:: true

#### Question: Choice
id:: ec5ae7f4-b969-425e-b428-4b8322ea750b
content:: DeepMind's 2022 "Chinchilla" paper found that many large language models of the time used their training compute poorly. What was the problem?
options::
- [x] They had too many parameters for the amount of data they saw
- They were trained on too much data for their number of parameters
- They were spread across too many chips running in parallel
- They received too many steps of reinforcement learning after pretraining
shuffle:: true

#### Question: FillBlank
id:: b3c9ef17-684a-4087-bdd2-88b1d1b04105
content:: The Chinchilla results suggest that compute-optimal pretraining uses roughly {{20|twenty}} training tokens for each model parameter.

#### Question: Choice
id:: 402b6e63-5d4c-4c35-bbf3-19c0357ed215
content:: Many recent language models are trained on far more tokens per parameter than the "Chinchilla-optimal" ratio. Why would a developer choose this?
options::
- [x] A smaller model trained for longer costs less to run once deployed
- Training on more data per parameter makes a model safer to release
- Regulators cap the number of parameters that a model may have
- Models above a certain size stop following the scaling laws
shuffle:: true

#### Question: Choice
id:: 152e65a9-da1d-4f6d-ad51-48bda7dccf5a
content:: Which of these is a claim of the scaling hypothesis rather than an empirical scaling law?
options::
- [x] Scaling up current methods could reach human-level general AI
- Loss on held-out text falls as a power law in training compute
- Compute-optimal model size and data both grow as compute grows
- Adding parameters at fixed data gives a predictable drop in loss
shuffle:: true

#### Question: Choice
id:: 0db38fc6-727d-4aa6-90a3-5c15c8c9adea
content:: Rich Sutton's 2019 essay "The Bitter Lesson" draws a conclusion from decades of AI research. What is it?
options::
- [x] General methods that use more compute beat methods built on human domain knowledge
- Methods built on expert domain knowledge beat general methods that rely on compute
- More compute helps a system improve only until it reaches human-level skill
- Progress has come mostly from better curated datasets rather than from more compute
shuffle:: true

#### Question: Open
id:: d20056a7-768e-4dfb-86f0-91063fc0552a
content:: How does Rich Sutton's "bitter lesson" lend support to the scaling hypothesis? Answer in one or two sentences.
assessment-instructions:: Score out of 100. 100 for linking the two: the bitter lesson says general methods (search and learning) that make use of growing compute have beaten hand-built knowledge, so we should expect scaling current general methods to keep paying off. 50 for describing the bitter lesson correctly without the link. 0 if the bitter lesson is described as favouring hand-built knowledge.

#### Question: Choice
id:: 2054839a-a20e-4c1f-a980-f760b967bde5
content:: Scaling laws predict a language model's loss on next-token prediction quite well. Why does this not settle how useful a bigger model will be?
options::
- [x] Lower loss does not map in a simple, known way onto specific skills
- Loss can only be measured once the model has been deployed to users
- Loss is measured on training data only, so it overstates real progress
- Loss tracks how fast a model trains, not how well it predicts text
shuffle:: true

#### Question: Choice
id:: 6b19f164-f7db-4d40-9f4d-7253462c6171
content:: Which of these is a commonly cited limit on continuing to scale up pretraining?
options::
- [x] Running short of high-quality human-written text to train on
- Loss starting to rise again once models pass a certain size
- Larger models forgetting the earliest data they were trained on
- Power laws holding for image models but not for language models
shuffle:: true

#### Question: Choice
id:: 08ac60fd-6ab7-4848-bf3b-d1be8014c7fe
content:: What does "inference-time scaling" (also called test-time compute scaling) refer to?
options::
- [x] Getting better answers by letting a trained model use more compute per question
- Getting a better model by training it on more data during pretraining
- Serving more users at once by running copies of a model on more chips
- Answering more cheaply by shrinking a trained model after pretraining
shuffle:: true

#### Question: Choice
id:: afeaf3bc-7c0d-49b1-9c27-4d3c00e856d5
content:: From late 2024, reports said some AI companies' largest pretraining runs gave smaller gains than hoped. Which approach did several companies turn to for further progress?
options::
- [x] Reinforcement learning to train reasoning, plus more compute at answer time
- Replacing learned models with hand-written rules for important tasks
- Cutting training data to remove low-quality text taken from the web
- Moving most research effort away from language models to robotics
shuffle:: true

#### Question: Open
id:: 7ea68f5c-1721-4504-89e6-8c73746424e3
content:: People disagree about whether AI scaling has stalled. Give one argument that pretraining scaling is running out of steam, and one argument that scaling as a whole is still driving progress.
assessment-instructions:: Score out of 100. 50 for a valid "slowing" argument: e.g. reports of disappointing returns from the largest runs, high-quality text running short, costs rising faster than gains. 50 for a valid "continuing" argument: e.g. loss still follows power laws, reinforcement learning and inference compute give fresh gains, compute investment keeps growing, capability trends on tasks continue.

#### Question: Open
id:: 397ff91d-12d7-4f09-b619-0af83c98e4b6
content:: Why does the question of whether scaling continues matter for forecasts of when highly capable AI might arrive? Answer in one or two sentences.
assessment-instructions:: Score out of 100. 100 for: if capabilities keep rising predictably with compute, and compute keeps growing fast, forecasters can extrapolate and capable AI could come soon; if scaling stalls, progress depends on new ideas, which are harder to predict and may come more slowly. 50 for only one half.

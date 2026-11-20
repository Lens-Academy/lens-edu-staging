---
id: a8861980-abef-4063-b372-3bfe08972de2
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what AI compute is, including the chips, units (FLOP and FLOP/s) and data centers involved, and why the amount of compute a developer has shapes what AI systems it can build and run.

## Requires

## Helpful first
- [[Training vs. inference]]

## Why it matters
Much of the debate about AI progress and AI policy is framed in terms of compute: how many chips a company has, how much compute a model took to train, who can build the biggest data centers. Knowing the basic terms lets you read and compare these claims, and see why many governance proposals target chips.

## Lenses
- [What Is Compute? (LessWrong)](https://www.lesswrong.com/posts/uYXAv6Audr2y4ytJe/what-is-compute-transformative-ai-and-compute-1-4): Lennart Heim on compute as a quantity of operations vs. computing power as a rate, why logic, memory and interconnect can each be the bottleneck, training vs. inference, and compute alongside data and algorithms; read sections 1, 2.1 and the opening of 3, skip the trend figures (September 2021).
- [AI Chips: What They Are and Why They Matter (CSET)](https://cset.georgetown.edu/publication/ai-chips-what-they-are-and-why-they-matter/): why AI runs on GPUs and other specialized chips that do many calculations in parallel, and why only state-of-the-art chips are cost-effective at the frontier; read the "Introduction and Summary" (pp. 3–7 of the full report) (April 2020).
- [What You Need to Know About AI Data Centers (Epoch AI)](https://epoch.ai/blog/what-you-need-to-know-about-ai-data-centers): what a frontier data center is, why it needs huge amounts of power, liquid cooling and closely networked chips, and why training needs so many of them (updated November 2025).
- [[../Lenses/AI Safety Atlas - Governance - Compute Governance|Compute Governance]]: why compute is measurable, controllable and meaningful enough to govern, the 10^25 FLOP threshold in the EU AI Act, chip tracking and cloud know-your-customer, and where compute-based rules break down. Its US 10^26 executive order has since been revoked.

## Tests

#### Question: Choice
id:: f3039a3e-d36e-45ee-83d7-4987705a2c68
content:: In discussions of AI, what does "compute" usually refer to?
options::
- [x] The computing hardware, and the calculations it performs, used to train and run models
- The software code that defines how a model works
- The amount of text and other data a model is trained on
- The number of parameters a model has
shuffle:: true

#### Question: Choice
id:: 8e0a2410-51ea-440e-b34d-f0a53f05217d
content:: A model's training compute is reported as 10²⁵ FLOP. What does this number measure?
options::
- [x] The total number of arithmetic operations used to train it
- The number of operations its chips performed each second
- The number of parameters in the trained model
- The amount of energy used to train it
shuffle:: true

#### Question: Open
id:: e7a66b89-971d-423d-8430-4a584da997b1
content:: A company announces a new cluster that can perform 10²⁰ operations per second (FLOP/s). Why doesn't this figure alone tell you how much compute its next model will be trained with?
assessment-instructions:: Score out of 100. 100 for saying that total training compute also depends on how long the training run lasts, or on how much of the cluster is actually used for it (utilization, other jobs). 50 for noting the difference between a rate and a total without saying what else is needed. 0 otherwise.

#### Question: Choice
id:: 7ce70652-df04-4fbf-bf57-98cb0801bffe
content:: Why are AI models trained mainly on GPUs and similar AI chips rather than on ordinary CPUs?
options::
- [x] They run huge numbers of simple calculations in parallel
- They run each single calculation at a much higher clock speed
- They can store a whole training dataset on the chip
- They are much cheaper per chip than CPUs
shuffle:: true

#### Question: Choice
id:: f2a4d7b1-d06b-4ea5-8e9c-7acb2a14c0e2
content:: Why does training a frontier AI model take a large data center rather than a handful of top-end chips?
options::
- [x] A few chips would take far too long, so thousands share the work
- The data center is needed mainly to store the training data
- Training needs many different types of chip working together
- Top-end chips are designed for running models, not training them
shuffle:: true

#### Question: Choice
id:: fda82c0a-a414-4a48-862a-6dfe584c09ee
content:: Besides how many operations per second it can perform, which property of an AI chip often limits how fast it runs large models?
options::
- [x] How quickly data moves between its memory and its processors
- How much long-term disk storage its server has
- How many CPU cores its server has
- How fast its server connects to the internet
shuffle:: true

#### Question: Choice
id:: a3871e36-e229-44e5-9ce2-f260166d8127
content:: A company finishes training a model and releases it to millions of users. Which statement about its compute needs is most accurate?
options::
- [x] Serving users can take as much compute as training, or more
- Once training is over, running the model needs little compute
- It needs large amounts of compute again only when retrained
- Running it uses compute mainly on users' own devices
shuffle:: true

#### Question: Choice
id:: 95ff23e4-ba52-4199-bf5c-e1e4f14eef05
content:: Compute is often named as one of three main technical inputs to AI progress. What are the other two?
options::
- [x] Data and algorithms
- Electricity and cooling
- Funding and researchers
- Benchmarks and users
shuffle:: true

#### Question: Choice
id:: 1a63148b-174b-42e9-ad68-abcb1d52789c
content:: Some AI rules, including parts of the EU AI Act, add obligations for models trained with more than a set amount of compute. Why use training compute as the trigger?
options::
- [x] It roughly tracks capability and is known before release
- It directly measures how dangerous a model's outputs are
- It shows how many people will end up using the model
- It sets how much electricity the developer may use
shuffle:: true

#### Question: Open
id:: 85f6e95a-3bca-47c6-99ed-695de2ca3a3f
content:: Explain one way the amount of compute an AI company can access limits what it can do.
assessment-instructions:: Score out of 100. 100 for any one clear mechanism: training larger, more capable models needs more compute; running experiments to improve methods needs compute; serving many users (inference) needs compute. 50 for "more compute means better AI" with no mechanism. 0 otherwise.

#### Question: Open
id:: db496bab-8e9c-499c-9a57-63fbd548e50f
content:: Name two things, besides the AI chips themselves, that a large AI data center needs in order to run.
assessment-instructions:: Score out of 100. 100 for any two of: a large electricity supply, cooling, fast networking between chips, memory or storage, buildings and land, staff to operate it. 50 for one.

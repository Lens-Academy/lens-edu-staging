---
id: efae4049-b552-484c-9f64-d0f1adf07e0a
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the scale of the AI data center buildout and its electricity needs, explain why power has become a key constraint, and outline the main controversies around it.

## Requires
- [[Compute]]

## Helpful first

## Why it matters
AI progress depends on compute, and compute depends on buildings, chips and electricity. Knowing this physical side helps you judge how fast AI can scale, where governments have leverage over it, and why data centers are becoming a local and national political issue.

## Lenses

## Tests

#### Question: Choice
id:: a36d5dd1-9136-4fac-9899-65bff4a23bca
content:: As of November 2026, which constraint is most often named as the main bottleneck for building new large AI data centers in the US?
options::
- [x] Getting enough electricity and grid connections
- Finding enough land for the buildings
- Getting enough water for cooling
- Hiring enough construction workers
shuffle:: true

#### Question: Choice
id:: 43e564e4-a915-46bb-96ff-0ca02554b360
content:: Why are AI companies especially interested in nuclear and natural gas power for data centers, rather than relying on solar or wind alone?
options::
- [x] They can supply steady power around the clock
- They are the cheapest sources to build quickly
- They let data centers skip the grid's approval process
- They produce no carbon emissions
shuffle:: true

#### Question: Choice
id:: 1de0b193-e41d-424d-9bf5-576fa7cf843f
content:: According to a 2024 Lawrence Berkeley National Laboratory report, roughly what share of US electricity did data centers use in 2023?
options::
- [x] About 4%
- About 0.5%
- About 15%
- About 30%
shuffle:: true

#### Question: FillBlank
id:: 72a36548-e5a6-4a86-a205-3fbb36416d0c
content:: As of November 2026, the largest planned AI data center campuses are measured in {{gigawatts|gigawatt|GW}} of power, comparable to the output of a large power plant.

#### Question: Open
id:: 9a8284ac-577f-4088-8222-de019c253ff4
content:: Training a frontier AI model is a one-off energy cost. Explain why running the model for users (inference) could still use more energy in total.
assessment-instructions:: Score out of 100. 100 for explaining that inference is repeated for every request, across many users, for as long as the model is in use, so it adds up past the one-off training cost. Extra point, not required: reasoning models generate many tokens per answer. 40 for just saying "more people use it" without the repetition idea.

#### Question: Choice
id:: 2ef390b3-eed7-4d49-b0f4-cf3414b52c07
content:: Why do AI developers want frontier training compute concentrated in one huge site or a few tightly linked sites?
options::
- [x] Training needs many chips exchanging data at high speed
- Chips run faster when packed closely together
- Laws limit how many sites one company can run
- Electricity is only sold in very large blocks
shuffle:: true

#### Question: Open
id:: 06e34335-20c4-484a-868b-c168a5585b2a
content:: Name two controversies that have arisen around the buildout of AI data centers.
assessment-instructions:: Score out of 100. 50 each for any two of: higher electricity bills or ratepayers paying for grid upgrades; water use; carbon emissions or delayed retirement of fossil plants; air pollution from on-site gas turbines; noise or land use; tax breaks for projects that create few permanent jobs; strain on grid reliability. Vague answers like "the environment" get 25.

#### Question: Choice
id:: 4a19e772-2b56-402d-b2b1-56c0389e1c71
content:: How does the large physical footprint of AI data centers matter for AI governance?
options::
- [x] It makes large-scale compute easier to locate and regulate
- It makes AI chips harder for governments to track
- It removes the need for export controls on chips
- It puts AI under the control of electricity regulators
shuffle:: true

#### Question: Choice
id:: b3ae39da-7b6f-4fc3-a280-7f6d8133fc99
content:: What is Stargate, announced in January 2025?
options::
- [x] A joint venture led by OpenAI to build AI data centers
- A US government program to fund public AI compute
- A Microsoft chip designed for training AI models
- An international agreement to limit AI data centers
shuffle:: true

#### Question: Choice
id:: 6b486898-c29f-4bec-af0e-9b55b817b20d
content:: If the energy used per AI query keeps falling, does that mean total energy use by AI will fall?
options::
- [x] No
- Yes

#### Question: Choice
id:: 00a1b6b8-70f9-4d39-99df-33dc0b91881b
content:: Which of these is a common argument that China could have an advantage over the US in building AI data centers?
options::
- [x] It adds new power generation much faster
- It has more advanced AI chips
- Its chips use less power per calculation
- It has stricter limits on data center locations
shuffle:: true

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
- [[../articles/sharma-how-ai-chips-are-made#^data-centers-and-power|Data Centers and Power]]: why transformers, turbines and grid queues, not chips, now slow the buildout; gigawatt campuses and Stargate; the Berkeley Lab figure of 4.4% of US electricity; gas versus nuclear; why China has power to spare. Read only the "Data Centers and Power" chapter (September 2026).
- [AI and data centre electricity use (IEA)](https://iea.org/reports/key-questions-on-energy-and-ai/executive-summary): the International Energy Agency's overview of growth in 2025 and projections to 2030, the bottlenecks in grid connections and equipment, on-site gas and nuclear deals, falling energy per task against rising total use, and effects on bills, emissions and local opposition (April 2026).
- [How much energy does ChatGPT use? (Epoch AI)](https://epoch.ai/gradient-updates/how-much-energy-does-chatgpt-use): estimates the energy of a single chatbot query, compares running ChatGPT with training a model, and explains why long inputs and reasoning models cost more. Read the main text and skip the appendix (February 2025).
- [Who pays for data centers' power (Associated Press, via OPB)](https://www.opb.org/article/2026/02/13/as-electricity-costs-rise-everyone-wants-data-centers-to-pick-up-their-tab-but-how): how data center demand can raise everyone's electricity bills, the state rules that make tech companies pay for grid upgrades, and the wider fights over water fees, tax breaks and local opposition (February 2026).
- [[../articles/sevilla-can-ai-scaling-continue-through-2030#^power-constraints|Can AI scaling continue through 2030? Power]]: Epoch AI's estimate of how much power frontier training runs will need, how big a single campus can get, and when training has to be spread across several sites. Read the "Power constraints" section up to "Modeling energy bottlenecks". Its 2024 site plans have since been overtaken (August 2024) (more advanced).

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
id:: 01747649-29c8-4bd8-b98d-83fa32f41387
content:: A 2024 Lawrence Berkeley National Laboratory report found that data centers used about 4.4% of US electricity in 2023. What did it project for 2028?
options::
- [x] Roughly 7% to 12%
- Roughly the same, about 4% to 5%
- A fall to about 3%, as chips get more efficient
- Roughly 25% to 30%
shuffle:: true

#### Question: FillBlank
id:: 72a36548-e5a6-4a86-a205-3fbb36416d0c
content:: As of November 2026, the largest AI data center campuses, both operating and planned, are measured in {{gigawatts|gigawatt|GW}} of power, comparable to the output of a large power plant.

#### Question: Open
id:: 9a8284ac-577f-4088-8222-de019c253ff4
content:: Training a frontier AI model is a one-off energy cost. Explain why running the model for users (inference) could still use more energy in total.
assessment-instructions:: Score out of 100. 100 for explaining that inference is repeated for every request, across many users, for as long as the model is in use, so it adds up past the one-off training cost. Extra point, not required: reasoning models generate many tokens per answer. 40 for just saying "more people use it" without the repetition idea.

#### Question: Choice
id:: 2ef390b3-eed7-4d49-b0f4-cf3414b52c07
content:: Why do AI developers want frontier training compute concentrated in one huge site or a few tightly linked sites?
options::
- [x] Training needs many chips exchanging data at high speed
- One big site is always cheaper to cool than several small ones
- Laws limit how many sites one company can run
- Chip makers only sell to sites above a minimum size
shuffle:: true

#### Question: Open
id:: 06e34335-20c4-484a-868b-c168a5585b2a
content:: Name two controversies that have arisen around the buildout of AI data centers.
assessment-instructions:: Score out of 100. 50 each for any two of: higher electricity bills or ratepayers paying for grid upgrades; water use; carbon emissions or delayed retirement of fossil plants; air pollution from on-site gas turbines; noise or land use; tax breaks for projects that create few permanent jobs; strain on grid reliability. Vague answers like "the environment" get 25.

#### Question: Choice
id:: 4a19e772-2b56-402d-b2b1-56c0389e1c71
content:: Why might the large physical footprint of frontier AI data centers give governments leverage over AI?
options::
- [x] Big sites are hard to hide and need permits and power
- It makes secret frontier training impossible anywhere
- Grid operators can see which models a site trains
- It makes export controls on chips unnecessary
shuffle:: true

#### Question: Choice
id:: b3ae39da-7b6f-4fc3-a280-7f6d8133fc99
content:: What is Stargate, announced in January 2025 with a stated plan to invest up to $500 billion?
options::
- [x] A venture of OpenAI, SoftBank and others to build AI data centers
- A US government program to build public AI compute for universities
- A Microsoft and Nvidia project to design new AI training chips
- An international agreement to share AI data centers among allies
shuffle:: true

#### Question: Open
id:: 76cfc9c1-5497-482b-8bd3-f44576707515
content:: The energy used per AI query has been falling. Explain why total energy use by AI could still keep rising.
assessment-instructions:: Score out of 100. 100 for explaining that cheaper, better AI leads to much more use (more users, more queries, new uses), so total demand can grow faster than efficiency improves. Also credit: reasoning models and AI agents use far more computation per task. 50 for saying only "more people use AI" without linking it to efficiency making use cheaper. 0 for saying total use must fall.

#### Question: Choice
id:: 00a1b6b8-70f9-4d39-99df-33dc0b91881b
content:: Which of these is a common argument that China could have an advantage over the US in building AI data centers?
options::
- [x] It adds new power generation much faster
- It has more advanced AI chips
- Its chips use less power per calculation
- It has stricter limits on data center locations
shuffle:: true

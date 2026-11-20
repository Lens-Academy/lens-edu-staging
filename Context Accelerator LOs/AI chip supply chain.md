---
id: 7078843f-0fe1-4e3b-b7dd-106b846beece
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main stages of the AI chip supply chain, from chip design and manufacturing to lithography machines and memory, name the companies that dominate each stage, and explain why that concentration matters for governing AI.

## Requires
- [[Compute]]

## Helpful first

## Why it matters
Training frontier AI takes huge numbers of advanced chips, and only a few companies can supply the hardest steps of making them. Knowing where these chokepoints are explains why governments use chip export controls, why Taiwan matters to AI policy, and which ideas for tracking or limiting compute could work.

## Lenses
- [What You Need to Know About AI Chips (Epoch AI)](https://epoch.ai/publications/chips-topic-overview): Who designs AI chips, why nearly all are made by TSMC, ASML's monopoly on EUV machines, HBM as a bottleneck, and how governments treat chips as strategic (July 2026).
- [[../articles/sharma-how-ai-chips-are-made|How AI Chips Are Made]]: Read the "Lithography" and "Foundries and Fabs" chapters: what a lithography machine does, why no one else can build an EUV scanner, what a fab costs, and why TSMC's concentration in Taiwan will last a decade (September 2026).
- [[../Lenses/blablov-why-china-isnt-about-to-leap-ahead-of-the-west-on-compute|Why China Is Behind on Compute]]: How limits on ASML machines and TSMC manufacturing, and the lead of Nvidia's CUDA software, keep Chinese labs reliant on Western chips (July 2025).
- [[../Lenses/AI Safety Atlas - Governance - Compute Governance|Compute Governance]]: Why a supply chain run by Nvidia, TSMC and ASML makes chips a lever for governing AI, and the tools that use it: export controls, tracking chips, know-your-customer rules for cloud providers and on-chip controls; read up to "Limitations".

## Tests
#### Question: Choice
id:: 4e7b55df-5b50-4048-a98e-be67aea78e5d
content:: What is Nvidia's main role in the AI chip supply chain?
options::
- [x] It designs AI chips and pays other firms to manufacture them
- It manufactures AI chips that other firms design
- It makes the equipment that chip factories use
- It runs most of the data centers used to train AI
shuffle:: true

#### Question: Choice
id:: 4a10f052-8b2b-4ca7-a89e-697948d518b8
content:: In chipmaking, what does a lithography machine do?
options::
- [x] Projects light to print circuit patterns onto silicon wafers
- Cuts finished wafers into individual chips
- Stacks memory chips beside the processor
- Tests finished chips for manufacturing defects
shuffle:: true

#### Question: FillBlank
id:: d1614ab6-231f-4908-91da-4ec32b60f953
content:: The Dutch company {{ASML}} makes the extreme ultraviolet (EUV) lithography machines used to produce leading-edge chips.

#### Question: Choice
id:: b64b48a7-8738-464e-92ea-c59e6007e82d
content:: Besides its chip designs, what has helped Nvidia stay ahead of rival AI chip designers?
options::
- [x] CUDA, its widely used software for programming its chips
- Its ownership of the factories that make its chips
- Its exclusive rights to buy EUV lithography machines
- Government rules requiring AI labs to use its chips
shuffle:: true

#### Question: Choice
id:: 1bf5e1b6-0ec0-442c-81e4-b4432095acbb
content:: Which component of AI chips, made mainly by SK Hynix, Samsung and Micron, has been a major bottleneck in producing them?
options::
- [x] High-bandwidth memory (HBM)
- Power-delivery components
- Chip design software
- Silicon wafers
shuffle:: true

#### Question: Choice
id:: 6d32b7af-b80c-4ef9-abb6-d2c78f4cab4e
content:: A leading-edge chip factory (fab) costs tens of billions of dollars and takes years to build. What does this most likely mean for governing AI through chips?
options::
- [x] The few firms able to make leading-edge chips will probably stay few for years
- Most large countries could build their own leading-edge fabs within a year or two
- Controls on chips will only matter for older, cheaper chips
- Leading-edge chipmaking will soon spread across many firms and countries
shuffle:: true

#### Question: Choice
id:: 96912e71-ec10-45f4-9c33-a5e7ee2d2cb4
content:: Suppose a blockade cut off chip exports from Taiwan for a year. As of November 2026, what would most likely happen to the supply of new AI chips?
options::
- [x] It would fall sharply, as other factories couldn't replace Taiwan's output quickly
- Nvidia would move production to its own US factories within months
- Little would change, since most AI chips are made in the US
- Mainly Chinese buyers would lose access, since they depend most on Taiwan
shuffle:: true

#### Question: Choice
id:: a163ee48-2d3c-4b51-98c0-e3fb5164ec56
content:: Why does the concentration of the AI chip supply chain make chips a useful lever for governing AI?
options::
- [x] Controlling a few firms can control who gets advanced chips
- Each chip records which AI models are trained on it
- Chip firms must already share their designs with governments
- Concentrated industries must publish who their customers are
shuffle:: true

#### Question: Open
id:: 08cc97ed-3cd7-403a-bdf5-47bbf944c6a0
content:: Google, Amazon and other companies now design some of their own AI chips instead of buying them all from Nvidia. Why does this do little to reduce the AI industry's dependence on the supply chain's main chokepoints?
assessment-instructions:: Score out of 100. 100 for saying their chips are still manufactured by TSMC (or a few leading-edge factories) using ASML's lithography machines, so manufacturing and lithography stay concentrated. Also accept dependence on a few high-bandwidth memory makers, or on TSMC's advanced packaging. 50 for saying they still depend on outside manufacturing without saying it is concentrated. 0 for claiming they make the chips themselves.

#### Question: Open
id:: 71c32058-f972-480b-a1d6-052d8b7bb62b
content:: Several firms, such as AMD and Google, design AI chips that compete with Nvidia's. Explain why the EUV lithography machine stage is harder for a country to get around than the chip design stage.
assessment-instructions:: Score out of 100. 100 for saying one company (ASML) makes all commercial EUV machines and copying them would take many years, because they depend on rare know-how and specialised suppliers (such as Zeiss optics), while several firms can already design capable chips. Accept a mention of China's reported prototype EUV machine if the answer notes it is far from volume production. 50 for saying EUV machines are technically hard without the contrast with design.

#### Question: Open
id:: c109afd6-2951-449b-bd4b-a36a032b8cb6
content:: Give one way governments have used, or could use, the concentration of the AI chip supply chain to influence AI development.
assessment-instructions:: Score out of 100. 100 for any one of: export controls on advanced chips or chipmaking tools (such as US limits on sales to China, or Dutch limits on ASML sales); requiring chip sellers or cloud providers to check who their customers are; tracking chip shipments or registering large chip clusters; building location checks or other controls into chips. 30 for a vague answer like "regulate chip companies" with no mechanism.

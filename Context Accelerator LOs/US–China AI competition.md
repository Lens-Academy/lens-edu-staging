---
id: 3d3abb1d-5b96-40a3-9afd-9f68f7ff2357
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe where the US and China each stand in AI as of November 2026: who leads on chips and computing power, where the talent comes from, how far behind Chinese models are, and what each government is aiming for.

## Requires
- [[AI race dynamics]]

## Helpful first
- [[Export controls]]
- [[Chinese AI developers]]

## Why it matters
Many arguments in AI policy, from export controls to slowing down, rest on claims about how close China is. Knowing the actual state of chips, talent and models lets you check those claims instead of accepting "China is about to win" or "China is years behind" at face value.

## Lenses
- [Competing AI strategies for the US and China (Brookings)](https://www.brookings.edu/articles/competing-ai-strategies-for-the-us-and-china/): Kyle Chan's testimony to Congress on where each country leads (US: compute and frontier models; China: efficiency, open-weight models, deployment, power build-out, chip self-sufficiency) and what Beijing is aiming for; read up to "How America can win in AI" (April 2026).
- [[../Lenses/AIF - China Compute and Frontier Lag|China Compute and Frontier Lag]]: two Epoch analyses: why chipmaking limits and weak software keep Chinese AI compute behind for years, and how many months Chinese models have trailed the US frontier.
- [Who's Ahead in the Global AI Talent Race? (Carnegie Endowment)](https://carnegieendowment.org/features/whos-ahead-in-the-global-ai-talent-race): where the top NeurIPS researchers did their first degree and where they now work, and how that changed from 2022 to 2025 (September 2026).

## Tests

#### Question: Choice
id:: 8499d192-7a33-4c53-9b3b-df4aa23a30f4
content:: In which of these AI-related resources does the US have a clear lead over China?
options::
- [x] Advanced AI chips and total computing power
- Number of AI research papers published each year
- Number of STEM graduates each year
- New electricity generation built each year
shuffle:: true

#### Question: Choice
id:: fc96acc8-c61e-408e-b8c4-01673013fdf1
content:: Nvidia designs the leading AI chips but doesn't manufacture them. Which company makes most of them?
options::
- [x] TSMC, in Taiwan
- Samsung, in South Korea
- Intel, in the United States
- SMIC, in China
shuffle:: true

#### Question: Choice
id:: 33f58c89-3ec6-492d-aca2-6a8d384afa3e
content:: US-led export controls stop China's main chipmaker, SMIC, from buying the most advanced (EUV) chipmaking machines. What has SMIC still managed to do?
options::
- [x] Make 7 nm-class chips with older machines, at higher cost
- Make 2 nm chips that match TSMC's best
- Buy EUV machines second-hand through Japanese firms
- Make chips no more advanced than the 28 nm standard
shuffle:: true

#### Question: Choice
id:: 2b62eb62-664f-4bf1-b223-2a0de863fd4e
content:: As of November 2026, how do most analysts describe the gap between the best Chinese AI models and the best US models?
options::
- [x] Chinese models are several months behind
- Chinese models are several years behind
- Chinese models are ahead on most major benchmarks
- Chinese models are behind on text but well ahead on coding and agents
shuffle:: true

#### Question: Choice
id:: e6aec944-62c9-4116-bcb7-2c1c420a9f36
content:: Why did DeepSeek-R1, a Chinese model released in January 2025, surprise many US observers?
options::
- [x] It came close to top US reasoning models at a low reported cost
- It was trained on Huawei chips instead of Nvidia ones
- It clearly beat the best US models on most benchmarks
- It was the first model trained to reason step by step before answering
shuffle:: true

#### Question: Choice
id:: ffe3f414-c058-472a-bff6-fbaf9d833c48
content:: Many leading Chinese AI developers, DeepSeek among them, release their models differently from most leading US companies. How?
options::
- [x] With weights anyone can download and run on their own hardware
- Through an API only, with the weights kept secret
- Only to users inside China, through government-approved apps
- Only to Chinese companies and universities, under licence
shuffle:: true

#### Question: Choice
id:: 4b0d9885-4269-44f9-9443-ccfa2ef1b123
content:: A 2026 study traced the careers of top AI researchers who wrote papers for NeurIPS 2025, a leading AI conference. What did it find about researchers who did their first degree in China?
options::
- [x] They were the largest group, and most of them now work in China
- They were the largest group, but most of them now work in the US
- They were a smaller group than those who studied in the US
- They were the largest group, but most of them now work in Europe
shuffle:: true

#### Question: Choice
id:: bf77987b-d0c0-44ff-890a-9b3a7046201a
content:: China's 2017 New Generation Artificial Intelligence Development Plan set a national goal for 2030. What was it?
options::
- [x] To become the world's main centre of AI innovation
- To match US private investment in AI
- To build the world's first artificial general intelligence
- To end imports of foreign AI chips
shuffle:: true

#### Question: Choice
id:: 4a94f41c-f343-42ea-b947-c8dfb70451ad
content:: In December 2025 the US decided to let Nvidia sell its H200 chips, which are less advanced than its newest Blackwell chips, to approved Chinese buyers. Nvidia and some US officials had argued for this. What was their main argument?
options::
- [x] It keeps Chinese developers dependent on US technology
- It slows Chinese AI progress by flooding the market
- It lets the US track which Chinese labs train large models
- It is required under World Trade Organization rules
shuffle:: true

#### Question: FillBlank
id:: 810bb62b-55e5-48e5-a400-f059383120d9
content:: The Dutch company {{ASML}} is the only maker of the EUV lithography machines needed to make the most advanced chips, which is one reason export controls on China can work.

#### Question: Open
id:: 784c6efb-7b55-4964-8721-7a583c2d31b7
content:: Name two advantages China is often said to have over the US in AI competition.
assessment-instructions:: Score out of 100. 50 points each for any two of: building far more new electricity generation; more STEM graduates or AI researchers; more AI research papers; a strong manufacturing and robotics base; fast deployment to a large user base; widely used open-weight models; state coordination of industrial policy. No credit for chips or computing power.

#### Question: Open
id:: 1eeeb738-b3d0-4a3d-9ffd-4c41689cda54
content:: Why is computing power often called the US's main lead over China in AI? Give one way that lead could shrink.
assessment-instructions:: Score out of 100. 50 for the lead: the US and its allies control key parts of the chip supply chain (Nvidia, TSMC, ASML) and restrict exports to China, so US firms have far more compute. 50 for any one of: chip smuggling; renting compute abroad through the cloud; better Chinese-made chips; more efficient training methods; export rules being loosened.

---
id: e875e7c3-8148-41e5-aede-8ebc47dcef70
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe roughly how many people and businesses use AI as of late 2026, what they mainly use it for, how use differs between countries, firms and people, and why the speed of adoption matters.

## Requires
- [[Current AI capabilities]]

## Helpful first

## Why it matters
AI changes the economy only as fast as people and organizations actually put it to work. Knowing how wide and how fast adoption is helps you judge claims that AI is overhyped or that sweeping change is imminent, and how quickly AI revenue can pay for the next generation of models.

## Lenses
- [The continued state of global AI diffusion in 2026 (Microsoft On the Issues)](https://blogs.microsoft.com/on-the-issues/2026/09/21/the-continued-state-of-global-ai-diffusion-in-2026/): Microsoft's device-data estimate that about 19% of the world's working-age people used generative AI by mid-2026. Leading countries, and a gap between Global North and South that is still widening (September 2026).
- [How people are using ChatGPT (OpenAI)](https://openai.com/index/how-people-are-using-chatgpt/): OpenAI's study of 1.5 million conversations. About 70% are not about work, most are practical guidance, information seeking or writing, and growth is fastest in lower-income countries (September 2025).
- [Anthropic Economic Index report: Learning curves (Anthropic)](https://www.anthropic.com/research/economic-index-march-2026-report): what people and businesses use Claude for. Coding is about a third of Claude.ai chats, API use hands off whole tasks more often, and use is concentrated across countries. Read "What has changed since our last report" (March 2026).
- [Monitoring AI Adoption in the U.S. Economy (Federal Reserve Board)](https://www.federalreserve.gov/econres/notes/feds-notes/monitoring-ai-adoption-in-the-u-s-economy-20260403.html): compares three US surveys (about 18% of firms, 41% of workers, 78% of workers at firms using AI) and explains why counting firms, workers or employment gives such different answers. Also covers firm size and industry (April 2026).
- [[../Lenses/narayanan-a-guide-to-understanding-ai-as-normal-technology|A Guide to AI as Normal Technology]]: the skeptics' case that "deployment is not diffusion" and that headline user counts overstate real adoption, and why AI adoption still feels so fast. Read "The surreal debate about the speed of diffusion" and "Why AI adoption hits different" (September 2025).

## Tests

#### Question: Choice
id:: dd827d68-2fd3-4407-b126-9036bee96219
content:: Microsoft estimates generative AI use from its device data. As of June 2026, roughly what share of the world's working-age population did it find was using generative AI?
options::
- [x] About one in five
- About one in fifty
- About half
- About four in five
shuffle:: true

#### Question: FillBlank
id:: 7edaa2e3-3fb2-496a-a58d-23bfee9cf1d0
content:: In February 2026, OpenAI reported that ChatGPT had about {{900 million|900m|0.9 billion|nearly a billion|a billion}} weekly users.

#### Question: Choice
id:: e8070911-c04c-4209-ac85-4d9843b17ed7
content:: The US Census Bureau regularly asks a representative sample of US businesses whether they used AI in the past two weeks. As of May 2026, about what share said yes?
options::
- [x] About 20%
- About 5%
- About 50%
- About 85%
shuffle:: true

#### Question: Open
id:: 21d6bb6f-0bdc-4289-99cb-db6d7f750930
content:: A mid-2026 McKinsey survey found 89% of organizations regularly used AI in at least one business function. A US Census Bureau survey from the same months found about 20% of US businesses had used AI in the past two weeks. Give one reason both figures can be accurate.
assessment-instructions:: Score out of 100. 100 for any one of: McKinsey's respondents come mostly from larger organizations, while the Census covers all businesses, most of which are small and adopt AI less; in a big organization, a few staff using AI anywhere is enough to count for McKinsey; the surveys differ in who answers, the time window or countries covered. 50 for "different surveys measure differently" with no specific difference.

#### Question: Choice
id:: 865823fd-9a14-4149-9c44-4102e1a14c88
content:: OpenAI classified a large sample of messages sent on ChatGPT's consumer plans to estimate how ChatGPT is used. By mid-2025, roughly what share of all messages on those plans were not related to the user's work?
options::
- [x] About 70%
- About 30%
- About 50%
- About 95%
shuffle:: true

#### Question: Choice
id:: d4d5bd4b-e63b-45a5-bf71-b564d03e8235
content:: Coding-related tasks were about a third of conversations on Anthropic's Claude.ai in early 2026, but about 4% of ChatGPT messages in mid-2025. What best explains such a gap?
options::
- [x] Each product draws different users, so its usage mix reflects who chose it
- Anthropic's figure includes businesses' API traffic as well as its chat app
- OpenAI's study left out messages from paying subscribers
- Coding grew from a small to a large share of all AI use between 2025 and 2026
shuffle:: true

#### Question: Choice
id:: 2f3e5b59-cf21-48be-a846-1264147515ea
content:: Anthropic's Economic Index compares use of its consumer chat app with businesses' use of its models through the API. Which pattern does it report?
options::
- [x] API use more often hands whole tasks to the AI with little human involvement
- Chat app use more often hands whole tasks to the AI with little human involvement
- API use is mainly people learning new topics with the AI
- Both show the same balance of automating and collaborating
shuffle:: true

#### Question: Choice
id:: dbe62da1-8d1f-401c-a26d-1f645a64981d
content:: In Microsoft's 2026 data on generative AI use, how did use in the Global North compare with the Global South?
options::
- [x] Higher in the North, and the gap was widening
- Higher in the North, but the gap was closing fast
- Higher in the South, driven by mobile-first users
- About the same in both
shuffle:: true

#### Question: Choice
id:: 93f3b5fe-04a4-4bda-a403-3395cbf1a58b
content:: A 2024 study compared how fast US adults took up generative AI with how fast they took up personal computers and the internet, counting from each technology's mass-market launch. What did it find?
options::
- [x] Generative AI was adopted faster than both
- Generative AI was adopted more slowly than both
- Faster than personal computers, slower than the internet
- About the same pace as both
shuffle:: true

#### Question: Choice
id:: e778e1ca-eec0-481b-9883-79978981e34a
content:: A 2024 review pooled 18 studies, covering over 140,000 people worldwide, comparing men's and women's use of generative AI. What did it find?
options::
- [x] Women used it less than men in nearly all regions and sectors
- Women used it more than men in nearly all regions and sectors
- Men and women used it at about the same rate in most regions
- Women used it less than men, but only in lower-income countries
shuffle:: true

#### Question: Choice
id:: 8b3bd599-c69f-4243-9ab8-c51ebd746d80
content:: What does the "AI as normal technology" view, from Arvind Narayanan and Sayash Kapoor, claim about AI adoption?
options::
- [x] Organizations and rules adapt slowly, so economic impact lags capability by years or decades
- Adoption is so fast that economic impact will arrive within a few years of each capability
- Adoption is held back mainly by a shortage of chips and data centers
- Consumers adopt slowly, but businesses adopt as soon as a capability appears
shuffle:: true

#### Question: Open
id:: accf490f-2fbc-4dd0-ae6e-beebdd888196
content:: Apart from how capable AI models are, give one way the speed at which AI is adopted could affect how fast AI progress or its economic impact grows.
assessment-instructions:: Score out of 100. 100 for any one with a mechanism: faster adoption brings revenue that funds more compute and research; AI companies using AI in their own research speeds up AI progress; usage gives data and feedback that improve models; slow uptake by firms and institutions delays economic impact even when capability exists. 40 for "faster adoption means faster impact" with no mechanism.

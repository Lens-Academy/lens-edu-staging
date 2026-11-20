---
id: aa8da453-c1c1-4042-8992-c39cff24957f
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Name the leading Chinese AI developers, describe how far their best models trail the US frontier and what holds them back, and explain how their habit of releasing open weights differs from the leading US companies.

## Requires

## Helpful first
- [[AI companies]]

## Why it matters
Arguments about racing, chip export controls and international agreements often rest on claims about how close China is in AI. Knowing which Chinese developers lead, how far behind they are and how openly they release models lets you check those claims instead of relying on alarm or dismissal.

## Lenses
- [What to Know About Chinese AI Models (CSIS)](https://www.csis.org/analysis/what-know-about-chinese-ai-models): who the leading Chinese developers are (DeepSeek, Alibaba's Qwen, Moonshot, Z.ai, MiniMax), how far behind they are, why their models are cheap, and why they release open weights (July 2026).
- [[../Lenses/AIF - China Compute and Frontier Lag|China Compute and Frontier Lag]]: two Epoch AI analyses. Chip manufacturing limits, export controls and Huawei's weaker software keep Chinese developers on Nvidia chips, and Chinese models have trailed the US frontier by 4 to 14 months since 2023, about the same as the gap between open-weight and closed models (2025–26; the 7-month average is weighted by an early catch-up period, and recent gaps are shorter).
- [On DeepSeek and Export Controls (Dario Amodei)](https://darioamodei.com/post/on-deepseek-and-export-controls): why DeepSeek-V3 and R1 surprised the US, what the "$6M" training figure leaves out, and the case that chip export controls decide whether China keeps up; the argument for controls, from Anthropic's CEO (January 2025).

## Tests

#### Question: Open
id:: 975a026e-ea76-41c6-92ff-9a7bc9f3ea9a
content:: Name two leading Chinese AI developers.
assessment-instructions:: Score out of 100. 100 for any two of: DeepSeek, Alibaba (Qwen), Moonshot AI (Kimi), Zhipu AI (Z.ai, GLM), ByteDance (Doubao, Seed), Baidu (Ernie), Tencent (Hunyuan), MiniMax, StepFun, 01.AI. 50 for one correct name. Accept the product name in place of the company.

#### Question: Choice
id:: b0c453f0-4f90-4616-ba2f-dcd0ff905cdf
content:: Why did the release of DeepSeek-R1 in January 2025 surprise many observers in the US?
options::
- [x] It performed close to the best US reasoning model on many tests
- It was the first chatbot able to answer fluently in Chinese
- It was the first frontier model trained on Chinese-made chips
- It was built by a government agency rather than a company
shuffle:: true

#### Question: Choice
id:: 94a6ed6f-2fb6-4437-b0b9-463c6da77aa6
content:: How do DeepSeek and Alibaba usually release their leading models, compared with OpenAI, Anthropic and Google DeepMind?
options::
- [x] They usually publish the weights; the US leaders mostly keep their best models' weights private
- They usually keep the weights private; the US leaders mostly publish their best models' weights
- They limit their models to users in China; the US leaders sell access worldwide
- They hand the weights to the Chinese government; the US leaders publish theirs openly
shuffle:: true

#### Question: Choice
id:: b2c38fbb-9849-4fb8-9744-0282d4215c4b
content:: During 2025 and 2026, roughly how far behind the best US models did most independent estimates put the best Chinese models?
options::
- [x] Several months to about a year
- About two to three years
- About five years or more
- Not behind: Chinese models led on most measures
shuffle:: true

#### Question: Choice
id:: 1a8010e4-b7ac-46d7-86fe-171988d1b67c
content:: Leaders of Chinese AI developers such as DeepSeek have named one constraint as their main obstacle to keeping up with US labs. Which is it?
options::
- [x] Limited access to the most advanced AI chips
- A shortage of skilled AI researchers in China
- Too little Chinese-language text to train on
- The high cost of electricity for data centres in China
shuffle:: true

#### Question: Choice
id:: 39942909-a44c-4fbc-a602-d9fedd6a79ee
content:: Qwen is one of the most downloaded families of open-weight language models in the world. Which company develops it?
options::
- [x] Alibaba
- Baidu
- ByteDance
- Tencent
shuffle:: true

#### Question: Choice
id:: 821f40ce-3fb8-44ff-82f8-b7b804fa1fe0
content:: DeepSeek reported that the final training run of its V3 model cost about $5.6 million in rented computing time. Why do many analysts say this understates what it cost to build the model?
options::
- [x] It covers the final run, not earlier experiments, staff or buying the chips
- It was quoted in yuan, so the dollar cost was about seven times higher
- It used Huawei chips, whose real price has never been made public
- Chinese state subsidies paid for the electricity used in training
shuffle:: true

#### Question: Choice
id:: b5b0f4e4-4c02-4886-b62a-a5888b068667
content:: Which Chinese company designs the Ascend AI chips that Chinese developers use as a domestic alternative to Nvidia's chips?
options::
- [x] Huawei
- Lenovo
- Xiaomi
- JD.com
shuffle:: true

#### Question: Choice
id:: 139c7ef0-7496-47a6-87a4-e651828e3da6
content:: Under Chinese regulations, what must a developer do before offering a generative AI chatbot to the public in China?
options::
- [x] File it with regulators and pass content checks, including on political topics
- Publish its weights so that government researchers can inspect them
- Show that it outperforms a government-run reference model on tests
- Limit it to business customers until it has run safely for a year
shuffle:: true

#### Question: Open
id:: 9efa04fb-d19b-4287-9d7c-47476eeb1f83
content:: DeepSeek and Alibaba publish the weights of many of their capable models openly. Once a model's weights are published, why can its developer no longer reliably prevent misuse of it?
assessment-instructions:: Score out of 100. 100 for any one of: anyone can download and run the model on their own hardware, outside the developer's monitoring; safety training can be removed by fine-tuning; the release cannot be withdrawn or patched once copies spread. 50 for "anyone can use it" without saying why that defeats the developer's control.

#### Question: Open
id:: 850d5308-2a94-403e-b271-3bf46d34b84d
content:: Some argue the US must race to stay ahead of China in AI. Give one fact about Chinese AI developers that supporters of this argument point to, and one that critics point to.
assessment-instructions:: Score out of 100. 50 for a supporter's fact, such as: the best Chinese models trail by months, not years; DeepSeek quickly matched leading US models at low reported cost; Chinese labs spread capable open weights worldwide. 50 for a critic's fact, such as: Chinese labs still trail and say chip access holds them back; the gap had not closed by late 2026 and had widened on some measures; Chinese regulators already control which chatbots reach the public. Give 25 instead of 50 for a general argument (e.g. "racing raises risks") with no fact about Chinese developers.

---
id: 362ec654-0ed3-4094-bacb-a7f97cda028f
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what US and allied export controls on AI chips and chipmaking tools to China cover, how they have changed since 2022, and the main ways they have been worked around.

## Requires
- [[Compute governance]]

## Helpful first
- [[AI chip supply chain]]

## Why it matters
Export controls are the main way governments currently use compute to shape who can build frontier AI. Knowing what they cover and where they leak helps you judge claims about the US–China AI race and proposals for compute-based safety rules.

## Lenses
- [[../articles/sharma-how-ai-chips-are-made|How AI Chips Are Made: Geopolitics]]: who holds the chokepoints, the US rules one by one from the 2019 Entity List and the Foreign Direct Product Rule to the 2026 H200 licences, why Dutch and Japanese cooperation matters, cloud access, smuggling and China's response; read the Geopolitics chapter from "The shape of the contest" to "Who gains and who pays" (September 2026).
- [How US Export Controls Have (and Haven't) Curbed Chinese AI (AI Frontiers)](https://ai-frontiers.org/articles/us-chip-export-controls-china-ai): Chris Miller, author of Chip War, on what the controls have and haven't achieved, and how they leak through shell companies, downgraded chips and cloud access (July 2025).
- [On DeepSeek and Export Controls (Dario Amodei)](https://darioamodei.com/on-deepseek-and-export-controls): the case that chip controls are the main lever for keeping a lead in powerful AI, from Anthropic's CEO, with how DeepSeek got its H800s, H20s and likely smuggled H100s; one side of a live debate (January 2025).
- [What did US export controls mean for China's AI capabilities? (Epoch AI)](https://epoch.ai/gradient-updates/us-export-controls-china-ai): how the 2022 and 2023 thresholds shaped Nvidia's H800 and H20, and why the H20's memory bandwidth left China close to parity in running models; a snapshot before the 2025 H20 changes (December 2024) (more advanced).

## Tests

#### Question: Choice
id:: 67f25856-778a-494a-9648-0c4aedd3dd5a
content:: US export controls block sales to China of advanced chipmaking equipment, as well as of advanced AI chips. What is the main aim of the equipment controls?
options::
- [x] To slow China in making its own advanced AI chips
- To stop China repairing chips it has already bought
- To protect US toolmakers from Chinese copies of their tools
- To cut China's output of older, cheaper chips
shuffle:: true

#### Question: Choice
id:: 47672a18-6fe1-42db-bb6b-a89b457ec4ef
content:: Why have US controls on chipmaking tools for China depended on the cooperation of the Netherlands and Japan?
options::
- [x] Firms there make key tools that US firms can't supply
- US export law applies only to countries that sign up to it
- Most chip factories in China are owned by Dutch and Japanese firms
- They are the largest buyers of chips made in China
shuffle:: true

#### Question: Choice
id:: 89341d2c-bf97-44b8-a8c7-15bb6477492b
content:: As of November 2026, has the Dutch government allowed ASML to ship any EUV (extreme ultraviolet) lithography machines to customers in China?
options::
- Yes
- [x] No

#### Question: Choice
id:: f6ae8eca-80fd-45b2-9404-81de0f04b8e8
content:: Chinese chipmakers such as SMIC cannot buy EUV machines. How have they still made chips at around the 7-nanometre level?
options::
- [x] By using older DUV machines several times per layer, at higher cost
- By buying used EUV machines from chipmakers outside China
- With Chinese-made EUV machines in mass production since 2024
- By having TSMC make the most advanced chips for them in Taiwan
shuffle:: true

#### Question: Choice
id:: 1c357ab6-aff0-4f79-a5b4-cd4c5b6bf917
content:: Do US export controls on AI chips to China cover chips made outside the United States, for example chips TSMC makes in Taiwan?
options::
- [x] Yes, because the chips are made with US tools and design software
- Yes, but only when a US company owns the factory that makes them
- No, they cover only chips made in factories in the United States
- No, Taiwan's own rules apply to chips made in Taiwan
shuffle:: true

#### Question: Choice
id:: dc173ef2-421f-4a93-bf6e-26d0ce5c6d27
content:: What does it mean when the US adds a Chinese company, such as the chipmaker SMIC, to its Entity List?
options::
- [x] Exporters need a US licence to supply it, usually denied
- It must sell any shares listed on US exchanges
- Its executives are barred from entering the US
- Its bank accounts and assets in the US are frozen
shuffle:: true

#### Question: Choice
id:: d13d6cbc-97a0-49ee-b82c-c089241a8ef1
content:: After the first US chip export rules in October 2022, Nvidia sold its H800 chip to Chinese firms. Why was the H800 allowed at first?
options::
- [x] Its chip-to-chip data transfer rate was below the rule's limit
- It was manufactured in Taiwan rather than in the US
- It was sold under an exemption for academic research
- It was classed as a gaming chip rather than an AI chip
shuffle:: true

#### Question: Choice
id:: 137d66d5-9b41-412c-8128-8d06d51dddf8
content:: The October 2023 US rules limited AI chips mainly by their processing performance. Why did critics say Nvidia's rule-compliant H20 chip still helped Chinese AI firms?
options::
- [x] Its high memory bandwidth made it good at running trained models
- Software could unlock it to run at full H100 speed
- It came bundled with access to Nvidia's US cloud servers
- It could train large models faster than the H100
shuffle:: true

#### Question: Choice
id:: c285dc18-356f-41b6-a8b0-be45955618ac
content:: In January 2025 the outgoing Biden administration issued the AI Diffusion Rule, which set caps on AI chip exports to most countries, not just China. What happened to it?
options::
- [x] It was rescinded in May 2025, before companies had to comply
- It took effect and still applies, as of November 2026
- It was delayed and replaced by a law passed by Congress
- It was expanded to cover open-weight AI models
shuffle:: true

#### Question: Choice
id:: ab7b9042-ae07-4141-a282-9ad924ab9ad3
content:: How did US policy on selling Nvidia AI chips to China change between April 2025 and early 2026?
options::
- [x] It blocked the H20, then licensed it and the stronger H200 for a cut of revenue
- It licensed the H20, then banned all Nvidia AI chip sales to China
- It kept the 2023 limits unchanged, so only H20-class chips could be sold
- It lifted all limits, allowing even Blackwell chips to be sold
shuffle:: true

#### Question: Choice
id:: cce52ef3-1d48-4815-8693-66f67eb2fad4
content:: Which Chinese company designs the Ascend AI chips that China promotes as a domestic alternative to Nvidia's chips?
options::
- [x] Huawei
- Alibaba
- Baidu
- Tencent
shuffle:: true

#### Question: FillBlank
id:: 70ad918b-78c1-4590-9840-8f8887cd93e5
content:: In the US, export controls on AI chips are written and enforced by the Commerce Department's Bureau of {{Industry and Security|Industry & Security}}.

#### Question: Open
id:: 9b6f29d5-87d5-4141-8ae0-f23f94547ede
content:: Name two ways Chinese AI companies have gained access to advanced AI compute despite US export controls.
assessment-instructions:: Score out of 100. 50 for each of any two of: smuggling or transshipment through other countries; renting chips through cloud data centres abroad; stockpiling chips before rules took effect; buying downgraded chips designed to meet the rules (e.g. H800, H20); using domestic chips such as Huawei Ascend; getting chips made through front companies. Vague answers like "cheating" get 20.

#### Question: Open
id:: 40aa6bd0-6500-479e-8092-014d1efd4f10
content:: US chip export controls are often said to buy time rather than to stop China's AI progress for good. Give one reason why.
assessment-instructions:: Score out of 100. 100 for any one of: China is building its own chips and chipmaking tools; controls leak through smuggling, cloud access or compliant chips; better algorithms let firms do more with less compute; stockpiled chips stay usable for years. 50 for "China will catch up" with no mechanism.

#### Question: Open
id:: 02fb98bf-b59c-4f94-93eb-874e27387365
content:: Give one argument that US chip export controls on China reduce risk from AI, and one argument that they might increase it.
assessment-instructions:: Score out of 100. 50 for a reduce argument, e.g. slowing China's frontier AI, giving the US a lead that leaves room for safety work, or creating leverage for agreements. 50 for an increase argument, e.g. worsening race dynamics, damaging trust needed for US–China safety cooperation, or pushing China to build an industry outside any controls.

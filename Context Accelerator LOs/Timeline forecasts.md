---
id: 722a7a90-b122-4ca8-a21e-7a4124adb64c
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what current forecasts from AI company leaders, forecasting platforms, superforecasters and surveyed researchers say about when AGI might arrive, and explain why they can differ by decades.

## Requires
- [[AGI and superintelligence]]

## Helpful first
- [[Task-length trends]]

## Why it matters
Whether AGI arrives within a few years or decades from now changes which safety research, policies and careers make sense: work that pays off in decades helps little if AGI comes soon. Forecasts have moved much earlier but still disagree widely; knowing the spread lets you plan for several timelines instead of anchoring on one confident voice.

## Lenses
- [Shrinking AGI timelines: a review of expert forecasts (80,000 Hours)](https://80000hours.org/2025/03/when-do-experts-expect-agi-to-arrive/): what AI company leaders, researchers, Metaculus and superforecasters say, and why each group's dates should be taken with caution (March 2025, updated February 2026).
- [[../Lenses/AIF - AI Futures Model Dec 2025|AI Futures Project: How AGI timelines are forecast]]: the AI 2027 team compares the main methods (trusting experts, argued intuition, revenue extrapolation, brain-based compute estimates, benchmark trends) and what each one predicts; read the section "AGI timelines forecasting methods" (December 2025).
- [Q3.5 timelines update: looks like the intelligence explosion will happen in 2027 after all (AI Futures Project)](https://blog.aifutures.org/p/q35-timelines-update-looks-like-the): the case for very short timelines from its leading forecasters, who now expect a superhuman AI researcher in 2027; read the "Timelines/Takeoff Update Summary" and the forecast table (November 2026).
- [[../Lenses/AIF - The Case for Multi-Decade AI Timelines|Ege Erdil: The case for multi-decade AI timelines]]: an Epoch researcher's case for about 20 years to full automation of remote work, and the cruxes where he parts from short-timelines views (April 2025).
- [[../Lenses/AIF - Broad Timelines|Toby Ord: Broad timelines]]: why your range of dates should be wide, and how to plan across short and long timelines; read "Short vs Long Timelines", "Broad Timelines" and "Implications" (March 2026).

## Tests

#### Question: Choice
id:: 2a1ea26d-54b5-4b8c-964e-d6928e5261f1
content:: In discussions of AI risk, what do people usually mean by "AI timelines"?
options::
- [x] Forecasts of when AI will reach a capability level such as AGI
- Estimates of how fast AI goes from AGI to superintelligence
- The schedule on which AI companies release new models
- Estimates of how long it takes to train a frontier model
shuffle:: true

#### Question: Choice
id:: e10b4dd6-6e98-4714-b6b3-ffda4f104018
content:: A forecaster gives a median of 2035 for the arrival of AGI. What does this mean?
options::
- [x] They think AGI is about as likely to come before 2035 as after
- They think 2035 is the single most likely year for AGI
- They are confident that AGI will not arrive before 2035
- They give AGI a 90% chance of arriving by 2035
shuffle:: true

#### Question: FillBlank
id:: 63e5e844-4ba5-4971-a404-37ec5f8fec03
content:: In AI Impacts' 2024 survey of 1,580 published AI researchers, the median forecast gave a 50% chance of high-level machine intelligence (machines doing every task better and more cheaply than humans) by the year {{2042}}.

#### Question: Choice
id:: 91734f4c-39f9-4a75-b30e-c8a7be2f34ca
content:: AI Impacts asked AI researchers the same question in its 2022, 2023 and 2024 surveys. How did the median date for high-level machine intelligence change across the three rounds?
options::
- [x] It moved earlier each time, by about 17 years in total
- It moved later each time, by about 17 years in total
- It moved earlier in 2023, then back later in 2024
- It stayed within a few years of 2050
shuffle:: true

#### Question: Choice
id:: ffa06974-0543-44fb-b675-ee5eeaa963d3
content:: A 2023 survey of AI researchers asked one group when machines could do every task better than humans, and another group when every occupation could be fully automated. How did the two median dates compare?
options::
- [x] The occupations date was about 70 years later
- The two dates were within a few years of each other
- The occupations date was about 20 years earlier
- The occupations date was about 5 years later
shuffle:: true

#### Question: Choice
id:: ba64ec0a-649f-4906-9067-162fad9f3b11
content:: As of November 2026, roughly when does the Metaculus community forecast expect the first general AI system to be built and publicly announced?
options::
- [x] In the early 2030s
- In 2026 or 2027
- In the mid-2040s
- After 2070
shuffle:: true

#### Question: Choice
id:: cf34600e-fe62-4294-870f-cb85a8b64e2f
content:: In a June 2026 Forecasting Research Institute panel, AI experts and superforecasters forecast when AGI would exist, defined as AI that beats top-decile professionals at 90% of tasks in nearly all non-physical occupations. Assuming it arrives before 2100, roughly what were the two groups' median years?
options::
- [x] Both in the late 2040s or around 2050
- Both around 2028 to 2030
- Experts around 2030, superforecasters around 2060
- Both after 2080
shuffle:: true

#### Question: Choice
id:: 3de21a80-9766-49a5-b46c-618e3e358cc7
content:: As of 2026, which of these groups has tended to give the shortest timelines to AGI?
options::
- [x] Leaders of frontier AI companies
- Published AI researchers in large surveys
- Superforecasters on expert panels
- Members of the public in surveys
shuffle:: true

#### Question: Choice
id:: bd393c5f-e024-432f-8b81-8fe5a05927ed
content:: The AI Futures Project, who wrote the AI 2027 scenario, rebuilt their forecasting model in late 2025, and it put fully automated coding later than the scenario. How had their forecasts moved by November 2026?
options::
- [x] Earlier, to roughly where the AI 2027 scenario put it
- Later, to the mid-2030s or beyond
- Back and forth, ending near their late-2025 model
- No real change from their late-2025 model
shuffle:: true

#### Question: Open
id:: 43a81b5e-0e0a-49e9-81e2-1fea2c2a280f
content:: Give two reasons why published forecasts of when AGI will arrive can differ by decades.
assessment-instructions:: Score out of 100. 100 for any two of: different definitions of AGI; different methods (trend extrapolation, models, intuition, surveys); different information (insiders see unreleased systems); different incentives; wording of the question changes answers; forecasts made at different times. 50 for one.

#### Question: Open
id:: b200219a-771a-43cf-acf2-7a595c3719af
content:: The CEO of a frontier AI company says AGI will probably arrive within three years. Give one reason to give this more weight than a survey of academic AI researchers, and one reason to give it less.
assessment-instructions:: Score out of 100. More weight: sees unreleased models or internal progress data; works closest to the frontier. Less weight: financial or fundraising incentives; people who expect AGI soon are more likely to found AI companies; may use a narrower definition of AGI. 100 for one valid reason each way, 50 for one side only.

#### Question: Open
id:: cc5e332a-afe0-4cc9-99c7-4b27c6a46a6d
content:: Name one decision about reducing AI risk that should change depending on whether AGI is expected in 2 years or in 20, and say how it changes.
assessment-instructions:: Score out of 100. 100 for a concrete decision with the direction stated, e.g. career (quick-entry roles vs a long PhD), research (work on current models vs long-term theory), policy (urgent rules now vs building institutions slowly), or funding. 50 if a decision is named without saying how timing changes it.

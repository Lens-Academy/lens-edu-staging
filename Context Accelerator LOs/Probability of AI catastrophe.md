---
id: 28ee55c9-799c-4808-880c-2947e46efa9d
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the range of published estimates that AI causes existential catastrophe, from surveys, forecasters and prominent individuals, and interpret any such estimate by checking its outcome, time frame, conditions and source.

## Requires
- [[Existential risk]]
- [[Subjective probability]]

## Helpful first
- [[Expert opinion on AI]]

## Why it matters
Figures like "a 10% chance of extinction" shape how seriously the public and policymakers take AI risk. If you can tell what outcome, time frame and conditions a number refers to, you can compare estimates fairly, avoid confusing them with timeline forecasts, and explain why even a small probability can warrant action.

## Lenses
- [[../Lenses/AI Safety Atlas - Risks - Appendix Quantifying Existential Risks|Quantifying Existential Risks]]: what p(doom) means, why it can't be measured from data, estimates from 0% to 99.9%, and why they are hard to compare (2025).
- [[../Lenses/IABIED - QA - AI Experts on Catastrophe|AI Experts on Catastrophe]]: Hinton, Bengio, Christiano and others in their own words, plus the authors' footnote on why a single p(doom) misleads and why even 5% is alarming (2025).
- [My views on "doom" (LessWrong)](https://www.lesswrong.com/posts/xWMqsvHapP3nwdSW8/my-views-on-doom): Paul Christiano splits his estimate by outcome (takeover, most humans dying, a ruined future) and time frame, all things considered (April 2023).
- [[../Lenses/grace-thousands-of-ai-authors-on-the-future-of-ai|Thousands of AI Authors on the Future of AI]]: the 2023 survey of 2,778 AI researchers; read sections 4.2 and 4.3 for the median 5% and how answers shift with the question's wording (2024).
- [The Extinction Tournament (Astral Codex Ten)](https://www.astralcodexten.com/p/the-extinction-tournament): Scott Alexander on the tournament where superforecasters put AI extinction by 2100 far below AI experts, and why months of debate didn't close the gap (July 2023).

## Tests
#### Question: Choice
id:: 14dabfc4-f168-44f8-bfc7-b14d3ee26af9
content:: Which of these statements is a p(doom) estimate?
options::
- [x] "There's a 10% chance AI causes human extinction or permanent disempowerment."
- "There's a 50% chance AGI is built by 2040."
- "There's a 20% chance AI enables a major cyberattack this decade."
- "Most AI researchers think more safety research is needed."
shuffle:: true

#### Question: Choice
id:: f2073698-6df1-473b-b673-df92c7f5203a
content:: Person A puts a 20% chance on existential catastrophe if superintelligent AI is built. Person B puts a 10% chance on existential catastrophe from AI this century. What can you conclude about who is more pessimistic?
options::
- [x] Nothing yet, without knowing how likely A thinks superintelligence is
- A is more pessimistic, since 20% is double B's figure of 10%
- B is more pessimistic, since conditional figures tend to overstate risk
- They roughly agree, since both figures are about existential catastrophe
shuffle:: true

#### Question: Choice
id:: a85df9c4-d25f-44f6-8593-9de255a258a4
content:: In the AI Impacts survey of published AI researchers fielded in late 2024 (published September 2026, the latest as of November 2026), what was the median probability respondents gave to future AI causing human extinction or similarly permanent and severe disempowerment of humanity?
options::
- [x] 10%
- 0.5%
- 40%
- 75%
shuffle:: true

#### Question: Choice
id:: 6b5e346f-aa80-46bd-96a3-8159d25ee1ad
content:: In the 2022 Existential Risk Persuasion Tournament, superforecasters and AI experts estimated the chance that AI causes human extinction by 2100. How did their median estimates compare?
options::
- [x] The superforecasters' median was several times lower
- The superforecasters' median was several times higher
- The two medians were nearly identical from the start
- The two medians converged after the groups exchanged arguments
shuffle:: true

#### Question: Choice
id:: 9e33ae65-f955-45ae-b2e1-a7e0d01413df
content:: In the AI Impacts surveys, randomly chosen groups of AI researchers were asked about extinction risk from AI in slightly different wordings, and the medians differed noticeably (for example 5% for one wording and 10% for another). What does this suggest?
options::
- [x] Many respondents' estimates are rough and sensitive to framing
- Researchers deliberately misreport their views on surveys
- The wording with the higher median is the more accurate one
- The groups who got each wording held very different views
shuffle:: true

#### Question: Choice
id:: d43ffe35-4754-4b5f-9fe7-01d0dfce6d90
content:: When someone gives their overall p(doom), does that estimate usually already take into account what they expect governments and AI companies to do about the risk?
options::
- [x] Yes
- No

#### Question: Choice
id:: 2d5c633f-5298-4698-8021-6e02db87cb52
content:: Someone says their p(doom) is 10%. What is the best way to read this number?
options::
- [x] As their degree of belief that this one-off outcome will happen
- As a rate measured from past cases of advanced AI development
- As the share of AI companies they expect to cause a disaster
- As the share of experts they believe agree with their view
shuffle:: true

#### Question: Choice
id:: d204b462-5955-47e2-b791-f79ae6b0fcec
content:: As of November 2026, how are the p(doom) estimates that prominent AI researchers and AI company leaders have stated publicly spread out?
options::
- [x] They range from near 0% to above 90%
- They cluster between 40% and 60%
- They cluster below 1%
- They cluster above 90%
shuffle:: true

#### Question: FillBlank
id:: eeae51ec-2da6-4513-8c29-d62e07a0066d
content:: In his 2020 book The Precipice, Toby Ord estimated the chance of existential catastrophe from unaligned AI over the next 100 years at about 1 in {{10|ten}}.

#### Question: Open
id:: bcfbd6d9-d910-4a6b-8b6c-d2657b6acd7f
content:: Well-informed people give p(doom) estimates as different as 1% and 90%. Why can informed estimates of the same risk differ this much?
assessment-instructions:: Score out of 100. 100 for explaining that there is no track record or frequency data to settle the question, so estimates are judgments resting on different assumptions, for example about how hard alignment is, how fast AI improves, or whether people coordinate. 50 for naming differing assumptions or uncertainty without that link. 0 for saying one side is ignorant or dishonest.

#### Question: Open
id:: 0f842dce-ac1f-4a53-8bac-875e0c9e757c
content:: Explain why a 2% chance that AI causes human extinction could justify major effort to reduce the risk, even though it means disaster is unlikely.
assessment-instructions:: Score out of 100. 100 for an expected-cost argument: extinction would be so bad (every living person, plus all future generations) that even a small probability means a very large expected loss. Comparing with precautions taken against smaller risks, such as in aviation or nuclear power, is a fine addition. 50 for saying the risk is still notable without linking probability to severity.

#### Question: Open
id:: 7d716c6d-bad7-4a0e-a2d5-5ca81b6a2a17
content:: A headline says "AI researchers put 15% chance on human extinction from AI." Name two things you would want to know before interpreting this number.
assessment-instructions:: Score out of 100. 100 for any two of: the time frame; the exact outcome asked about (extinction, disempowerment or a smaller catastrophe); whether the probability is conditional on something, such as AGI being built; who was surveyed and how many responded; whether the figure is a median or a mean; how the question was worded. 50 for one.

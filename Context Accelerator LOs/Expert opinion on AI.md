---
id: 6d69684e-07b5-4c18-886d-0be05340092e
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what surveys, open letters and public statements show about how AI researchers and prominent figures view AI timelines and risk, where they disagree, and how much weight this evidence can bear.

## Requires

## Helpful first
- [[Existential risk]]
- [[AGI and superintelligence]]

## Why it matters
Expert concern is often the first thing people ask about, and it is easy to overstate or dismiss. Knowing who has said what, what surveys actually found and where experts disagree lets you answer accurately, spot misleading headlines, and avoid appeals to authority in either direction.

## Lenses
- [What open letters have been written about AI safety? (AISafety.info)](https://aisafety.info/questions/NM5D/What-open-letters-have-been-written-about-AI-safety): what the 2023 pause letter, the 2023 Statement on AI Risk and the 2025 Statement on Superintelligence each called for (updated Nov 2026).
- [Survey of 2,778 AI authors: six parts in pictures (AI Impacts)](https://blog.aiimpacts.org/p/2023-ai-survey-of-2778-six-things): the main results of the 2023 survey of researchers who had published at top AI venues: much earlier timelines than in 2022, different answers for "every task" and "every occupation", and the spread of extinction-risk estimates (January 2024).
- [[../Lenses/IABIED - QA - AI Experts on Catastrophe|AI Experts on Catastrophe]]: Hinton, Bengio, Christiano, Leike and others give their own odds of AI catastrophe, compiled by Yudkowsky and Soares, who are themselves on the worried side, with their caution about single "p(doom)" numbers (2025).
- [[../Lenses/Wikipedia Existential Risk|Existential risk from AI (Wikipedia)]]: read only the Perspectives section (Endorsement and Skepticism) for who endorses the concern and the main sceptical arguments, from Ng, LeCun and Gebru, Bender and Mitchell.
- [AI existential risk probabilities are too unreliable to inform policy (AI as Normal Technology)](https://normaltech.ai/p/ai-existential-risk-probabilities): two leading sceptics, Narayanan and Kapoor, argue that surveys, forecasts and personal estimates of AI extinction risk can't carry much weight, including why experts and superforecasters in the XPT stayed far apart (July 2024).

## Tests
#### Question: Choice
id:: 2750fd6b-27fd-4d3e-aceb-00120c200e46
content:: What did the one-sentence Statement on AI Risk (May 2023), signed by many AI researchers and the heads of OpenAI, Google DeepMind and Anthropic, say?
options::
- [x] Reducing the risk of extinction from AI should be a global priority
- AI development should stop until it can be proven safe
- Frontier AI companies should be licensed by a new international agency
- Human extinction caused by AI is likely within this century
shuffle:: true

#### Question: Choice
id:: fcc1caac-6e4f-49e4-8012-1342e9afcff4
content:: What did the Future of Life Institute's open letter of March 2023, signed by Elon Musk, Yoshua Bengio and thousands of others, call for?
options::
- [x] A pause of at least six months on training systems more powerful than GPT-4
- A permanent ban on building any system more capable than GPT-4
- Public release of the training data behind every large language model
- A global treaty capping the computing power used to train AI
shuffle:: true

#### Question: Choice
id:: 0227531b-2fe2-4a2d-9f5a-dc74aca026cd
content:: In October 2025, the Statement on Superintelligence, signed by Geoffrey Hinton, Yoshua Bengio and many public figures, called for what?
options::
- [x] A ban on building superintelligence until scientists broadly agree it is safe and the public supports it
- An international agency to license every company that trains frontier AI models above a set size
- Government funding to build superintelligence as a public, non-profit project shared by all nations
- Publication of a full safety plan by each AI company before it trains any new frontier model
shuffle:: true

#### Question: Choice
id:: aec37141-02d9-49e2-aa52-79de85b76ec7
content:: Geoffrey Hinton, Yoshua Bengio and Yann LeCun shared the 2018 Turing Award for their work on deep learning. Which of them has argued publicly that fears of AI causing human extinction are overblown?
options::
- [x] Yann LeCun
- Geoffrey Hinton
- Yoshua Bengio
shuffle:: true

#### Question: Choice
id:: 30abe4ed-8d75-44d1-a08c-a4a6a103dd89
content:: Who was asked in the 2023 AI Impacts Expert Survey on Progress in AI, which had about 2,800 respondents?
options::
- [x] Researchers who had recently published at top AI conferences
- Researchers working specifically on AI safety and alignment
- Professional forecasters with strong track records on other questions
- Technical staff employed at the leading AI companies
shuffle:: true

#### Question: FillBlank
id:: 1ea75255-e287-460d-8b96-b83293530c29
content:: In the 2024 AI Impacts Expert Survey on Progress in AI (about 1,600 respondents), the median respondent put the chance of human extinction or similarly severe, permanent disempowerment from advanced AI at {{10%|10|10 percent|ten percent}}, double the 2023 median.

#### Question: Choice
id:: 1ab908d2-0895-43e7-bc0f-fec81ff4db44
content:: A headline about the 2024 AI Impacts survey of AI researchers reads: "Half of AI researchers think AI will wipe out humanity." Which comment best corrects it?
options::
- [x] About half gave at least a 10% chance, which is not the same as expecting it
- About half said extinction is the single most likely outcome of advanced AI
- About half were AI safety specialists, so the sample is not typical of the field
- Only a small fringe of respondents gave extinction any chance above zero
shuffle:: true

#### Question: Choice
id:: 085b4936-bdfa-4993-a82e-2f744ebb4c62
content:: The 2024 AI Impacts survey asked researchers when machines could do every task better and more cheaply than humans, and separately when every human occupation would be fully automated. How did the forecasts for the two questions compare?
options::
- [x] Full automation of occupations was forecast many decades later
- The two forecasts were within a few years of each other
- Full automation of occupations was forecast many decades earlier
shuffle:: true

#### Question: Choice
id:: d027af34-7bfd-46b5-89d4-c1c2d265e9ea
content:: Between the 2023 and 2024 AI Impacts surveys of AI researchers, did the aggregate forecast for when machines could do every task better and more cheaply than humans move earlier or later?
options::
- [x] Earlier
- Later

#### Question: Choice
id:: 968304c8-e7ba-4f41-b687-c2d3458018f8
content:: In the 2022 Existential Risk Persuasion Tournament, AI experts and superforecasters each estimated the chance of AI causing human extinction by 2100, then read and responded to each other's written arguments online. What happened?
options::
- [x] The experts gave much higher estimates, and the gap mostly remained
- The experts gave much higher estimates, but the two groups converged
- The superforecasters gave much higher estimates, and the gap mostly remained
- The two groups gave similar estimates from the start
shuffle:: true

#### Question: Choice
id:: c9780e80-7fd3-4f22-bbbc-80644bd357f7
content:: The first International AI Safety Report (January 2025), chaired by Yoshua Bengio and written by about 100 experts, described expert views on how fast AI will advance and how severe its risks are. What did it say?
options::
- [x] Experts disagree a great deal on both questions
- Experts mostly agree that progress will slow down soon
- Experts mostly agree that severe risks are decades away
- Experts mostly agree that general AI will arrive by 2030
shuffle:: true

#### Question: Open
id:: fb0dff7d-db05-460a-adc0-b6f3bf29fdf4
content:: Give two reasons to be cautious about treating surveys of AI researchers as accurate forecasts of AI timelines or risk.
assessment-instructions:: Score out of 100. 50 for each valid reason, such as: low response rates, so those who reply may not be representative; answers change a lot with how questions are worded; skill at building AI isn't skill at forecasting; respondents give quick answers without much reflection; incentives or social pressure in the field. A vague reason ("surveys can be wrong") gets at most 20.

#### Question: Open
id:: dbe5ac6c-a724-463e-84b2-f637f0baa294
content:: Name one argument often made by AI researchers who doubt that AI poses a risk of human extinction.
assessment-instructions:: Score out of 100. 100 for any one of: the focus on extinction distracts from current harms such as bias, misinformation or job loss; current AI is far from human-level or lacks key abilities; humans design AI and can build in safeguards; the claims rest on speculation rather than evidence; the warnings hype AI or help large companies shape regulation. 50 for "it's exaggerated" with no reason.

#### Question: Open
id:: 38c341a1-4586-42b8-b0a1-7222a424f61c
content:: The leaders of OpenAI, Google DeepMind and Anthropic have each said publicly that AI could cause human extinction. Give one reason this adds weight to the concern and one reason a sceptic might discount it.
assessment-instructions:: Score out of 100. 50 for a reason it adds weight: they know frontier systems closely, or they are warning about their own industry's product. 50 for a reason to discount it: such warnings can make their products seem powerful, help them shape regulation in their favour, or ring hollow while they keep racing to build it. Each half needs a reason, not just an assertion.

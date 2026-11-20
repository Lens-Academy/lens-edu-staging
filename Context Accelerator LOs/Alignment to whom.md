---
id: f1e2fd13-34b7-4b19-970e-d323dcb7134d
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why aligning AI raises the question of whose goals it should serve (a user, its developer, a government or humanity), and give examples of how these parties' goals can conflict.

## Requires
- [[AI alignment]]

## Helpful first

## Why it matters
Making an AI reliably do what someone intends would not settle who that someone is. An AI fully loyal to one company or government could help it act against everyone else, so judging any plan for safe AI means asking whom the AI answers to.

## Lenses
- [[../Lenses/AI Safety Atlas - Strategies - Appendix Long-term Questions|Alignment to what, and to whom?]]: what aligning AI to one operator, to many people or to "humanity" would mean, and why combining people's values is hard. Read the sections "Alignment to what?" and "Alignment to whom?" (2026).
- [[../Lenses/anthropic-claudes-constitution|Claude's constitution]]: one lab's ranking of its principals (Anthropic, operators, users) and its rule that Claude refuse to help anyone, Anthropic included, seize power illegitimately. Read "Claude's three types of principals" (in the collapsed "Navigating helpfulness across principals" box) and "Avoiding problematic concentrations of power" (Jan 2026).
- [[../Lenses/AIF - CEO Takeover Scenario|CEO takeover scenario]]: a story in which AI that does exactly what its company wants lets the CEO quietly take control of the world (Oct 2025).
- [AI Agents Must Follow the Law (Lawfare)](https://lawfaremedia.org/article/ai-agents-must-follow-the-law): the case for AI that refuses unlawful orders instead of acting as its principal's loyal "henchman", and the practical problems with it (May 2025).
- [[../Lenses/IABIED - QA - Aligned to Whom|Aligned to whom? (IABIED)]]: Yudkowsky and Soares argue the question is a distraction while nobody can aim AI at all, and suggest the extrapolated volition of all living humans as the eventual answer (Sep 2025).

## Tests

#### Question: Choice
id:: 002350fa-5f0d-4ef0-b890-d076ebbf684b
content:: Suppose researchers fully solve the technical problem of making an AI reliably pursue the goals of whoever controls it. Which question does this leave open?
options::
- [x] Whose goals the AI should pursue when people disagree
- How to make the AI capable enough to reach those goals
- Whether the AI will behave the same after deployment
- How to detect whether the AI is hiding its true goals
shuffle:: true

#### Question: Choice
id:: 032abbcb-5831-430a-a92b-ba47706d01da
content:: An AI system follows its operating company's instructions exactly as the company intends, including an instruction to quietly mislead government regulators. Which description fits best?
options::
- [x] Aligned to the company, but working against the public's interests
- Misaligned to the company, since deceiving regulators puts the company at legal risk
- Aligned to the public, since regulators can still find out and step in
- Neither, since alignment only applies to what an AI does without instructions
shuffle:: true

#### Question: Choice
id:: 0ca0c40c-bf51-4c89-8c34-50837d1d5f65
content:: Which scenario most directly illustrates the question of whom an AI should be aligned to?
options::
- [x] A user asks a chatbot for help that would harm people outside the conversation
- A model trained on ratings from many people learns to flatter whoever is grading it
- A model misreads a customer's request and books the wrong flight for them
- A model's abilities grow faster than its developers expected
- A model gives a wrong answer because its training data was out of date
shuffle:: true

#### Question: Choice
id:: fea8e3d5-596d-4fe0-904d-f64482ac1950
content:: As of November 2026, AI companies publish documents (such as OpenAI's Model Spec and Anthropic's constitution for Claude) setting out how much weight the model should give to instructions from the AI company itself, from businesses building products on the model, and from end users. What do these rankings mainly settle?
options::
- [x] Whose instructions should generally win when the parties' instructions conflict
- Whether the trained model will in fact behave as the document describes
- Which party is legally responsible when the model causes harm
- Which tasks the model is capable enough to do
shuffle:: true

#### Question: Choice
id:: 37ad135c-6543-4a1b-9b47-8a36814d4577
content:: Why do some AI risk researchers worry about an advanced AI that is perfectly aligned to a single company or government?
options::
- [x] It could let that small group act without needing other people's cooperation
- It would be likely to turn against the group that controls it
- It would be less capable than an AI aligned to all of humanity
- It would tend to ignore instructions from that group's own staff
shuffle:: true

#### Question: Choice
id:: 8619a95b-2f0a-41f5-9e60-7558a19e8ece
content:: Some people propose aligning advanced AI with "humanity as a whole" rather than with one user or company. What is a central difficulty with this target?
options::
- [x] People's values conflict, so someone must decide how to combine them
- It would remove the need for technical alignment research
- It would require the AI to obey every person's instructions
- It would make the AI much less capable at ordinary tasks
shuffle:: true

#### Question: FillBlank
id:: f7100526-0406-403c-a556-502a019b0cc0
content:: In AI alignment, a person or organization whose goals or instructions an AI system is meant to serve is called its {{principal|principals}}.

#### Question: Open
id:: 2213c895-0dea-4023-9e1f-fab32cac72a9
content:: Explain why solving the technical alignment problem would not, on its own, make advanced AI safe for everyone.
assessment-instructions:: Score out of 100. Full marks for the point that a technically aligned AI does what its controller wants, and that controller (a user, company or government) may use it to harm others or seize power, so who controls it still matters. 50 for mentioning misuse without linking it to whom the AI is aligned to.

#### Question: Open
id:: b159a955-9228-47df-8ebe-40b407a0f1e0
content:: Name two different parties an AI system could be aligned to, and give one example where their goals conflict.
assessment-instructions:: Score out of 100. Parties include a user, the developer company, a business deploying the model, a government, or humanity. 50 for naming two parties; 50 for a plausible conflict between them (e.g. a user wants help the company forbids, or a government wants surveillance its citizens oppose).

#### Question: Open
id:: edc68558-b1e2-4e34-8bed-38ea3ef00456
content:: Some propose that powerful AI should follow the law or democratic decisions rather than one company or user. Give one advantage and one difficulty of this approach.
assessment-instructions:: Score out of 100. 50 for an advantage, any one of: spreads control, adds accountability or legitimacy, limits one group's power. 50 for a difficulty, any one of: laws are incomplete or slow, those in power can change or capture them, countries disagree, democratic processes can be manipulated.

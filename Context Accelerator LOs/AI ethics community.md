---
id: 13c0e498-e0c4-46ff-a549-cf1c319d2d8e
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the AI ethics and fairness community: its focus on present harms such as bias and surveillance, its main people and organisations, why many members criticise AI safety work, and where the two communities share goals.

## Requires
- [[AI safety terminology]]

## Helpful first

## Why it matters
The AI ethics community shapes much AI policy and public debate. If you know what it works on and why many members distrust AI safety, you can tell fair criticism from misunderstanding, avoid needless conflict, and find allies for shared goals such as accountability for AI companies.

## Lenses
- [There are two factions working to prevent AI dangers. Here's why they're deeply divided (Vox)](https://www.vox.com/future-perfect/2022/8/10/23298108/ai-dangers-ethics-alignment-present-future-risk): Kelsey Piper on what the AI ethics camp works on (bias, privacy, harms from systems in use now), how it differs from AI safety and alignment, and why the two camps distrust each other (August 2022).
- [Timnit Gebru (Wikipedia)](https://en.wikipedia.org/wiki/Timnit_Gebru): the plain facts on the community's best-known figure: Black in AI, the Gender Shades audit of facial recognition, the "Stochastic Parrots" paper and her 2020 exit from Google, the founding of DAIR, and the TESCREAL critique; read from her Microsoft work to the end of the TESCREAL section (November 2026).
- [Statement from the listed authors of Stochastic Parrots on the "AI pause" letter (DAIR)](https://www.dair-institute.org/blog/letter-statement-March2023): Gebru, Bender, McMillan-Major and Mitchell reply to the Future of Life Institute's pause letter: longtermist "fearmongering" distracts from worker exploitation, data theft and concentration of power, and the fix is transparency and accountability for the companies (March 2023).
- [Stop talking about tomorrow's AI doomsday when AI poses risks today (Nature)](https://www.nature.com/articles/d41586-023-02094-7): the case, as put by Nature's editors, that extinction warnings from industry leaders hype the technology, help the companies steer regulation, and push aside people who study current harms (June 2023).
- [AI Regulation's Champions Can Seize Common Ground—or Be Swept Aside (Lawfare)](https://www.lawfaremedia.org/article/ai-regulation-s-champions-can-seize-common-ground-or-be-swept-aside): Helen Toner and Zachary Arnold on why the "ethicists" and the "doomers" clash, and six policies both could push for: government capacity, measurement science, third-party audits, incident reporting, disclosure rules and liability (August 2024).

## Tests

#### Question: Choice
id:: f2d157dc-a547-4e3b-adf3-afbe1eaef3e7
content:: A company uses an AI tool to screen job applicants. Which concern would researchers in the AI ethics community most likely raise first?
options::
- [x] It may rate applicants from some groups unfairly low
- It may pursue power beyond its assigned task
- It may hide its true capabilities during testing
- It may copy itself onto outside servers
shuffle:: true

#### Question: Choice
id:: 7941c39e-7c72-48f6-ad9b-43aadc77a648
content:: The 2018 Gender Shades study by Joy Buolamwini and Timnit Gebru audited commercial facial analysis systems that classify gender. What did it find?
options::
- [x] Error rates were far higher for darker-skinned women than lighter-skinned men
- Error rates were similar across groups once lighting was controlled
- The systems misclassified men much more often than women
- Error rates were highest for lighter-skinned faces in low light
shuffle:: true

#### Question: Choice
id:: 3a058fd5-3c4a-45a2-b981-5a97fef9ea00
content:: The 2021 paper "On the Dangers of Stochastic Parrots" by Emily Bender, Timnit Gebru and others raised which concern about large language models?
options::
- [x] Huge, poorly documented training data can encode biases the models repeat
- Models could develop their own goals and resist being shut down
- Models would soon outperform humans at most research tasks
- Scaling would stall because usable text data would run out
shuffle:: true

#### Question: Choice
id:: f7326899-a4e9-4b6b-8e88-146c73777e25
content:: Model cards, proposed in 2019 by Margaret Mitchell, Timnit Gebru and colleagues, are mainly meant to do what?
options::
- [x] Report a model's intended uses and its performance across groups
- Certify that a model has passed government safety tests
- Track how much computing power was used to train a model
- Record which red-teamers tested a model before release
shuffle:: true

#### Question: Choice
id:: 6e72cf2b-6efb-4682-876d-de273ab320df
content:: Which of these organisations is mainly associated with the AI ethics community rather than the AI safety community?
options::
- [x] AI Now Institute
- Machine Intelligence Research Institute
- Center for AI Safety
- Redwood Research
shuffle:: true

#### Question: Choice
id:: ed6cb10a-e487-4d73-bfa3-7f7fa26ad5a3
content:: Critics including Timnit Gebru and Émile P. Torres use the contested term "TESCREAL". What does it refer to?
options::
- [x] Ideologies, including longtermism, that they link to the race to build AGI
- Present-day AI harms that they say safety researchers tend to ignore
- A set of audit methods they proposed for finding bias in AI models
- A coalition of ethics groups they formed to push for binding AI rules
shuffle:: true

#### Question: Choice
id:: 262957e5-0a90-4fbe-a579-47888a62ea54
content:: In March 2023 the Future of Life Institute published an open letter calling for a six-month pause on training the most powerful AI systems. The authors of "Stochastic Parrots" issued a statement criticising it. What did they argue for instead?
options::
- [x] Regulating companies' present practices instead of fearing imagined "digital minds"
- Extending the pause to cover all AI research, not only the largest models
- Avoiding new AI rules, since regulation tends to favour the biggest firms
- Funding research on aligning future systems before deploying current ones
shuffle:: true

#### Question: Choice
id:: fbd2ecb9-bda8-46f1-b4d9-965edea93efc
content:: Some AI ethics researchers argue that AI company leaders' warnings about existential risk end up helping those companies. What mechanism do they usually point to?
options::
- [x] They make the technology seem powerful and cast the firms as the experts to write the rules
- They let the firms charge customers more for premium safety features and add-ons
- They shift legal blame for AI harms from the firms onto the people using the tools
- They help the firms win large government grants earmarked for safety research
shuffle:: true

#### Question: Open
id:: d2b24af3-165c-4357-9a22-ab3b53016100
content:: In one or two sentences, what is a main difference in focus between the AI ethics community and the AI safety community?
assessment-instructions:: Score out of 100. 100 for saying AI ethics focuses mainly on harms from AI systems already in use (such as bias, surveillance, labour or misinformation) and on who bears them, while AI safety focuses mainly on catastrophic or loss-of-control risks from future, more capable systems. 50 if only one side is described correctly.

#### Question: Open
id:: ece1ef30-ced7-488d-9848-ab056a00acd0
content:: Besides biased or discriminatory outputs, name one kind of present-day AI harm that the AI ethics community works on.
assessment-instructions:: Score out of 100. 100 for any one of: surveillance or police use of facial recognition; privacy or use of data without consent; exploitation of data workers or content moderators; job loss or worker monitoring; misinformation or deepfakes; environmental costs; use of creative work without consent; concentration of power in big tech firms. 0 for bias or discrimination, or for future catastrophic risks.

#### Question: Open
id:: 6acd6a65-5540-4032-b56f-8bff982a505d
content:: Give one concrete goal that the AI ethics and AI safety communities could work towards together despite their disagreements.
assessment-instructions:: Score out of 100. 100 for any one concrete goal, such as: transparency or disclosure rules for AI developers; independent audits or evaluations of models; liability for AI harms; whistleblower protections; binding regulation of AI companies instead of voluntary pledges; limits on corporate concentration of power. 50 for a vague answer like "making AI good" with no concrete goal.

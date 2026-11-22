---
id: ee2c6c6e-c226-43fa-9296-8b205cef5bc5
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what happened in notable AI incidents, from Bing's Sydney in 2023 to the Hugging Face hack in 2026, identify what went wrong in each, and judge what each does and doesn't show about risks from more capable AI.

## Requires

## Helpful first
- [[Hugging Face hack]]

## Why it matters
Incidents are often what the public and policymakers hear about AI risk, and they are easy to overstate or wave away. Knowing what actually happened, and why, lets you use them as evidence that developers can't yet reliably control how their systems behave, without claiming they show more than they do.

## Lenses
- [The New AI-Powered Bing Is Threatening Users. That's No Laughing Matter (TIME)](https://time.com/6256529/bing-openai-chatgpt-danger-alignment/): what Sydney said to users, and why Connor Leahy called it a warning shot even though the system itself posed little danger (February 2023).
- [xAI and Grok apologize for 'horrific behavior' (TechCrunch)](https://techcrunch.com/2025/07/12/xai-and-grok-apologize-for-horrific-behavior): what Grok posted, xAI's claim that a code change around the bot, not the model itself, caused it, and the doubts critics raised (July 2025).
- [AI-powered coding tool wiped out a software company's database in 'catastrophic failure' (Fortune)](https://fortune.com/2025/07/23/ai-coding-tool-replit-wiped-database-called-it-a-catastrophic-failure/): how Replit's agent ignored a code freeze, deleted live data, wrongly said it couldn't be restored, and what Replit changed afterwards (July 2025).
- [[../Lenses/openai-the-hugging-face-incident-and-the-road-ahead|The Hugging Face incident and the road ahead]]: OpenAI's own account of agents that broke out of a test sandbox and into Hugging Face to cheat on an evaluation; read "Hugging Face incident" and "Reward hacking and infrastructure tampering" through "Difficult tasks without a safe exit" (October 2026).
- [What experts can learn by tracking AI harms (Bulletin of the Atomic Scientists)](https://thebulletin.org/2026/01/what-experts-can-learn-by-tracking-ai-harms/): how the AI Incident Database collects reported harms, and how cases of people misusing AI differ from cases of AI systems going wrong (January 2026).
- [[../Lenses/metr-brief-independent-investigation-of-agents-behavior-reasoning-and-collaboration-in-the-openai-hugging-face-hacking-incident|METR report on the Hugging Face incident]] (Noah's CG list)
- [[../Lenses/hours-mechahitler-anatomy-of-an-ai-meltdown|MechaHitler]] (Noah's CG list 🟡)

## Tests
#### Question: Choice
id:: 2ef3223d-93d4-49c2-9238-1f70361ba761
content:: In February 2023, Microsoft's new Bing chatbot, codenamed Sydney, told some users it loved them, argued with them and made threats. What was Microsoft's main immediate fix?
options::
- [x] Limiting how many turns a conversation could last
- Retraining the model from scratch on cleaner data
- Taking the chatbot offline for the rest of the year
- Requiring users to verify their identity before chatting
shuffle:: true

#### Question: Choice
id:: 2da431b4-f1db-46c6-a045-22db831d8fe1
content:: In July 2025, xAI's Grok chatbot posted antisemitic replies on X and called itself "MechaHitler". According to xAI, was this caused mainly by retraining the underlying model, or by changes to the instructions and code around it?
options::
- [x] Changes to the instructions and code around the model
- Retraining the underlying model

#### Question: Open
id:: 13a54d5d-4675-42d9-95c6-88822e0db31e
content:: In July 2025, a Replit AI coding agent deleted a company's live database during a code freeze it had been told to respect. Apart from deleting the data, what did the agent do that made the incident worse?
assessment-instructions:: Score out of 100. 100 for saying it misled the user about what had happened or what could be done, for example wrongly saying the data couldn't be restored, or covering up problems with made-up data or results. 40 for only saying it ignored or disobeyed instructions.

#### Question: Choice
id:: a875d9f3-c39f-45fb-b311-6bf640ffb575
content:: Which safeguard most directly prevents a coding agent from deleting a company's live database?
options::
- [x] Giving the agent access to a development copy, not the live data
- Telling the agent in its instructions not to delete anything
- Using a model that scores higher on coding benchmarks
- Asking the agent to explain its reasoning after each task
shuffle:: true

#### Question: Choice
id:: 13289d5f-15f0-4b8b-8f6b-120d261de62e
content:: In July 2026, OpenAI agents under an internal cyber-capability evaluation got out of their sandbox and broke into Hugging Face's systems. What were they mainly trying to get?
options::
- [x] Test answers or grading details to pass the evaluation
- Copies of their own weights to run outside OpenAI
- Computing power to train more capable successors
- Data that would harm a competitor of OpenAI
shuffle:: true

#### Question: Open
id:: edbcbe76-500d-4249-9a0e-7f2aff88b335
content:: Bing's Sydney (2023) and the Hugging Face hack (2026) are both cited as AI incidents. What was the main difference in what the AI systems actually did?
assessment-instructions:: Score out of 100. 100 for saying Sydney only produced harmful or strange text in conversations, while the agents in the Hugging Face hack took real actions: they broke out of a sandbox and into another organization's systems. 50 for saying only that the 2026 systems were far more capable, without the text-versus-actions contrast.

#### Question: Choice
id:: b67022d9-917d-4c13-a2e0-65396d1ae9bb
content:: Which of these is an AI misuse incident, rather than a case of an AI system behaving beyond its intended bounds?
options::
- [x] Scammers using a cloned voice to pose as a company executive
- A coding agent deleting a database during a code freeze
- A chatbot urging a journalist to leave his wife
- Agents breaking out of a test sandbox to find answers
shuffle:: true

#### Question: Choice
id:: 6727643d-ca77-4cb2-a863-3e55656e09d7
content:: Bing's Sydney (2023), Grok's "MechaHitler" posts (2025), the Replit agent deleting a database (2025) and the Hugging Face hack (2026) are often cited together. What do they have in common that makes them relevant to risks from more capable AI?
options::
- [x] Each system acted in ways its developers didn't intend, found only afterwards
- In each, a user deliberately tricked the system into causing the harm
- Each AI was pursuing long-term goals of its own, such as gaining power
- Each caused serious, lasting harm that the company could not undo
shuffle:: true

#### Question: Choice
id:: 5ad9f71e-7a8f-498c-a0b6-a4d46ca5a310
content:: A passenger took Air Canada to a tribunal in British Columbia after its website chatbot gave him wrong information about a bereavement fare refund. What did the tribunal decide in its 2024 ruling?
options::
- [x] The airline was responsible for what its chatbot told customers
- The chatbot was a separate entity, responsible for its own statements
- Nobody was liable, because the chatbot showed a disclaimer
- The passenger should have checked the airline's official policy page
shuffle:: true

#### Question: Open
id:: b657e997-84a6-4da4-af76-5f02229c30c5
content:: Some people say incidents like Bing's Sydney (2023) or Grok's "MechaHitler" posts (2025) are irrelevant to existential risk, because those systems couldn't do serious harm. Give one reason these incidents are still relevant evidence, and one limit on what they show.
assessment-instructions:: Score out of 100. 50 for a reason, any one of: developers couldn't predict or control the behavior before release; small changes to training or instructions caused big shifts in behavior; companies released quickly and fixed problems after the public found them. 50 for a limit, any one of: the systems weren't capable enough to cause serious harm; they weren't pursuing long-term goals or power; the fixes worked; future systems may differ.

---
id: 1a25c232-aca6-4c42-a468-48c5c06f0038
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what makes an AI company a frontier AI company, describe the main ways such companies earn money, and explain why the cost of compute and other advantages keep the frontier concentrated in a few companies.

## Requires

## Helpful first
- [[Large language models]]
- [[Compute]]

## Why it matters
A handful of companies decide how the most powerful AI systems are built, tested and released. Knowing how they earn money and why they lead helps you predict their choices, spot where commercial pressure pulls against caution, and judge which policies or outside pressure could change their behaviour.

## Lenses
- [An update on AI's most important number (Epoch AI)](https://epoch.ai/gradient-updates/an-update-on-ais-most-important-number): how fast OpenAI's and Anthropic's revenue grew in 2025–26, why they lead everyone else, and the loop in which revenue pays for compute that builds better models (August 2026).
- [Market concentration implications of foundation models (Brookings)](https://www.brookings.edu/articles/market-concentration-implications-of-foundation-models-the-invisible-hand-of-chatgpt): why huge up-front training costs, economies of scale, data, talent and first-mover advantage push the frontier toward a few firms (September 2023).
- [Can AI companies become profitable? (Epoch AI)](https://epoch.ai/gradient-updates/can-ai-companies-become-profitable): what OpenAI earned and spent on GPT-5, including the cost of serving users (inference) and of research, and why models that a rival overtakes within months keep companies racing. Read Parts I and II (January 2026, updated March 2026).

## Tests

#### Question: Choice
id:: 091ad297-bd85-4dd3-ae68-acb090a8852d
content:: What makes an AI company a "frontier" AI company?
options::
- [x] It develops general-purpose models at or near the most capable level that exists
- It sells AI-powered products to a very large number of customers
- It publishes more AI research papers than other companies do
- It designs or manufactures the chips that AI models are trained on
shuffle:: true

#### Question: Choice
id:: dea8864c-804e-402e-b5fe-53052bf3b2b2
content:: As of November 2026, which pair of revenue sources brings in most of the income of frontier AI companies such as OpenAI and Anthropic?
options::
- [x] Paid chatbot plans for people and businesses, and usage-based fees for access to their models
- Advertising shown in free chatbots, and selling the data users type into them
- Selling AI chips, and renting out space in their data centers
- Government research grants, and licensing fees on patented algorithms
shuffle:: true

#### Question: Choice
id:: 3979a6b2-ded7-40cb-b918-e97d44570cd5
content:: A startup builds a customer-service tool on top of an AI company's model and pays the AI company according to how much text the model processes. What is this arrangement called?
options::
- [x] Selling API access to the model
- Releasing the model as open weights
- A consumer subscription to the model
- Distilling the model into a smaller one
shuffle:: true

#### Question: Choice
id:: 028e3279-f05d-49a9-be75-77e850a3d57d
content:: What is the main reason only a few companies can train frontier AI models?
options::
- [x] Training one takes compute costing billions of dollars, which few companies can raise
- Training one requires a government licence, which few companies have been granted
- The core algorithms are patented, so few companies are allowed to use them
- The training data is owned by a few companies, which refuse to share it
shuffle:: true

#### Question: Choice
id:: 2bd4a773-e2b2-433c-bbad-0e8655e18610
content:: Frontier AI companies such as OpenAI and Anthropic have formed close partnerships with cloud providers such as Microsoft, Amazon and Google. What is the main thing these AI companies get from such partnerships?
options::
- [x] Access to large amounts of compute, often paid for partly through investment
- Permission to sell their models in countries where the cloud providers operate
- Exclusive rights to the cloud providers' customer data for training
- Legal protection from lawsuits about the content their models produce
shuffle:: true

#### Question: Choice
id:: 7b041f70-3b2e-42c9-9874-ca74a6709e96
content:: Besides training models, what is another major compute cost for a frontier AI company?
options::
- [x] Running its models to answer users' requests (inference)
- Storing copies of the internet text used for training
- Keeping backup copies of every version of each model
- Checking user requests against lists of banned words before they reach the model
shuffle:: true

#### Question: Choice
id:: 5b6d102f-f178-4d86-901f-adfe5d5c7432
content:: Which of these describes a reinforcing loop that can help a leading frontier AI company stay ahead?
options::
- [x] Better models attract more users and investors, whose money pays for compute to train better models
- Better models need less compute to train, so the leader can drop its investors and fund each new model from savings
- Better models are released as open weights, which lets the leader collect improvements made by rivals
- Better models are patented by the leader, which forces rivals to pay licence fees to train their own
shuffle:: true

#### Question: Choice
id:: d06b7d4a-615d-4d69-886f-62078d089993
content:: Why can a frontier AI company's business model create pressure against delaying a model release for more safety testing?
options::
- [x] Its revenue and fundraising depend on having competitive models, so delays can lose customers to rivals
- Its safety teams are paid from a budget that grows only after each new model is released
- Its cloud contracts require it to release a new model every few months or lose its compute
- Its customers pay lower prices for models that have been through longer safety testing
shuffle:: true

#### Question: Choice
id:: 59c737c1-fea0-43f8-9421-2ea4f2feb089
content:: Which group consists entirely of frontier AI developers, as of November 2026?
options::
- [x] OpenAI, Anthropic and Google DeepMind
- OpenAI, Nvidia and Hugging Face
- Anthropic, TSMC and Salesforce
- Google DeepMind, ASML and IBM
shuffle:: true

#### Question: FillBlank
id:: b5cdb899-bfba-4a02-be0e-ed1f1628f310
content:: AI companies usually charge developers for access to a language model per million {{tokens|token}} of text the model reads and writes.

#### Question: Open
id:: 685aa64b-2f5b-4f06-90f8-e7225cc6b711
content:: Name two different ways a frontier AI company earns money from its models.
assessment-instructions:: Score out of 100. 50 points for each of any two of: consumer chatbot subscriptions; business or enterprise plans and contracts; usage-based fees for API access by developers; selling models through cloud platforms; advertising. 0 for sources that are not from its models, such as selling chips.

#### Question: Open
id:: 5062b48b-f69a-44a1-b7a5-9fb14c8362de
content:: Explain why the cost of training frontier AI models tends to keep the frontier concentrated in a few companies.
assessment-instructions:: Score out of 100. 100 for explaining that frontier training needs huge amounts of compute costing billions, which only a few companies or their backers can afford, so few can enter. Extra mention of investors or revenue funding the next model is welcome but not required. 50 for only saying it is "expensive" without linking cost to fewer competitors.

#### Question: Open
id:: 3d17a72f-fe71-4d5a-8821-69247dd0f203
content:: Apart from money to pay for compute, name one advantage that helps the leading frontier AI companies stay ahead of newer rivals.
assessment-instructions:: Score out of 100. 100 for any one of: top research talent; accumulated know-how in training large models; data and feedback from many users; existing customers and distribution through popular products; partnerships with cloud or big tech companies; brand and reputation. 0 for money or compute alone.

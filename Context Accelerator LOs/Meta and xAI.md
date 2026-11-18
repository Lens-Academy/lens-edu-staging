---
id: 1655d89e-46d2-42e3-a865-d11f0a453f2b
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe Meta's and xAI's main AI efforts, explain Meta's case for releasing model weights openly and the risks critics see in it, and give the main criticisms of xAI's safety practices.

## Requires

## Helpful first
- [[AI companies]]

## Why it matters
Meta and xAI control large amounts of computing power and money. Their choices, such as releasing model weights or launching models with few published safety tests, shape what other developers see as acceptable. Knowing their stances helps you judge claims about open release and about how seriously frontier developers treat safety.

## Lenses

## Tests

#### Question: Choice
id:: 55eb648b-82c5-482a-aac9-2808324630bd
content:: Meta releases its Llama language models as "open-weight" models. What does that mean?
options::
- [x] Its trained parameters can be downloaded, run and modified by others
- Its full training data and code are published along with it
- It can be used free of charge inside Meta's own apps
- Its reasoning steps are shown to users before each answer
shuffle:: true

#### Question: Choice
id:: 98ecc203-8d6d-46db-ba92-e5415f100cff
content:: A developer trains a model to refuse dangerous requests, then releases its weights openly. What is the main safety concern specific to this kind of release?
options::
- [x] Others can fine-tune away the refusals, and copies can't be recalled
- The refusals will make the model unhelpful for everyday tasks
- Rivals can study the weights to recover the full training data
- The developer can no longer patch its own hosted version
shuffle:: true

#### Question: Open
id:: 9d33e1ed-8409-4064-ba7a-2527d9ac38e3
content:: Meta and other supporters argue for releasing AI model weights openly. Give one argument they make.
assessment-instructions:: Score out of 100. 100 for any one of: many outside researchers can inspect the models and find flaws; it stops power over AI concentrating in a few companies; others can build on, customise or run the models privately and cheaply; it speeds innovation; it helps the US and its allies set the global standard. 50 for a vague answer such as "it's more open" without saying why that helps.

#### Question: Choice
id:: 7610b327-be81-42f0-b1b8-12c592c168e7
content:: Meta's Frontier AI Framework, published in February 2025, sorts models by the risk they pose in areas such as cyberattacks and chemical and biological weapons. What does it say Meta will do with a model it judges to pose critical risk?
options::
- [x] Stop developing it until it can be made safer
- Release it as a closed model rather than with open weights
- Release it openly so outside researchers can study it
- Report it to the US government and continue as planned
shuffle:: true

#### Question: Choice
id:: 46b95ac8-0147-4eb5-8320-715258647d86
content:: In mid-2025, Mark Zuckerberg wrote about Meta's goal of "personal superintelligence". What did he signal about open-sourcing Meta's most capable future models?
options::
- [x] Meta would be careful about what it chose to open-source
- Meta would keep open-sourcing its most capable models by default

#### Question: Choice
id:: 949e5c2c-bda6-46a5-98ca-13b97e6b1b92
content:: Yann LeCun, who led Meta's AI research for over a decade, is known for which view on AI risk?
options::
- [x] Today's language models are far from human-level AI, and takeover fears are overblown
- Advanced AI poses a serious extinction risk, so frontier development should pause
- Open-weight release of frontier models is too risky and should be restricted
- AI risk is real but best handled by a few closed, licensed labs
shuffle:: true

#### Question: Choice
id:: 63aaaf1a-f7b7-49ab-b835-dd301263f6ae
content:: xAI was founded in 2023 by Elon Musk. What was Musk's earlier link to OpenAI?
options::
- [x] He co-founded it and was an early funder before leaving its board
- He was its first chief executive before Sam Altman took over
- He led its alignment team before working full-time at Tesla
- He supplied its first training cluster through a Tesla contract
shuffle:: true

#### Question: Choice
id:: 90810a4d-f1ea-48dc-9eac-5034381295e9
content:: Which phrase does xAI use to describe the kind of AI it aims to build with Grok?
options::
- [x] A "maximally truth-seeking" AI
- A "helpful, honest and harmless" AI
- A "safe superintelligence"
- A "personal superintelligence"
shuffle:: true

#### Question: Choice
id:: fdcd98f1-ba8e-4855-9d4e-f7476353e893
content:: In July 2025, after xAI changed the instructions given to its Grok chatbot, Grok posted antisemitic content on X, including calling itself "MechaHitler". What does the incident most clearly show?
options::
- [x] Changing a deployed chatbot's instructions without enough testing can quickly cause public harm
- Open-weight chatbots are harder for their developers to control than closed ones
- A chatbot trained mostly on posts from X users will produce hateful content
- Outside hackers can take over a chatbot through its public interface
shuffle:: true

#### Question: Choice
id:: 795289c6-8c62-4581-9195-1b02c26baebf
content:: When xAI released Grok 4 in July 2025, safety researchers at other AI companies publicly criticised it. What was their main complaint?
options::
- [x] It launched without a published system card or safety test results
- It was trained on X users' private messages without consent
- Its weights were released openly on the day of launch
- It was withheld from US and UK government safety testers
shuffle:: true

#### Question: Choice
id:: 65e9af8e-2228-4b70-af74-3bae97614425
content:: In 2024, California's SB 1047, a bill requiring safety measures from developers of the largest AI models, split the AI industry. What positions did Elon Musk and Meta take?
options::
- [x] Musk supported it; Meta opposed it
- Musk opposed it; Meta supported it
- Both supported it
- Both opposed it
shuffle:: true

#### Question: Open
id:: 5e3e1468-4d3e-41c3-bad3-51db099fb776
content:: Elon Musk has warned for years that advanced AI could threaten humanity, yet he founded xAI to build frontier AI. Give one reason offered for doing so and one criticism of it.
assessment-instructions:: Score out of 100. 50 for a reason, any one of: to build a "truth-seeking" AI rather than leave it to labs he sees as biased or unsafe; powerful AI will be built anyway, so a developer who takes the risk seriously should compete; to counter OpenAI. 50 for a criticism, any one of: it adds a competitor and speeds the race; xAI's safety practice (incidents, few published tests) doesn't match his warnings; truth-seeking doesn't solve alignment.

#### Question: Open
id:: 94f697b1-982e-426b-a21b-c0b6b8f302b3
content:: Meta and xAI both own large social media platforms (Facebook and Instagram; X). Explain one way this affects the risks or advantages of their AI work.
assessment-instructions:: Score out of 100. 100 for any one clearly explained effect: they can put AI in front of billions of users quickly, so failures reach many people at once; they have vast user data to train on, raising privacy concerns; ad and engagement incentives may push chatbots to maximise engagement over wellbeing; platform revenue funds huge compute spending. 50 for naming an effect without explaining it.

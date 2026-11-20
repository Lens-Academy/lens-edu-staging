---
id: 1655d89e-46d2-42e3-a865-d11f0a453f2b
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe Meta's and xAI's main AI efforts, explain Meta's case for releasing model weights openly, the risks critics see in it and Meta's 2026 move to a closed frontier model, and give the main criticisms of xAI's safety practices.

## Requires

## Helpful first
- [[AI companies]]

## Why it matters
Meta and xAI (now part of SpaceX) control huge amounts of computing power and money. Their choices, such as whether to release model weights openly and whether to publish safety tests before launch, shape what other developers see as acceptable. Knowing their stances helps you judge claims about open release and about how seriously frontier developers treat safety.

## Lenses
- [Life After Llama: Meta pivots away from open weights (The Batch)](https://www.deeplearning.ai/the-batch/with-muse-spark-meta-pivots-away-from-its-open-weights-llama-strategy): Meta Superintelligence Labs, the Scale AI deal and hiring spree, Llama 4's troubles, and Muse Spark, Meta's first closed frontier model (April 2026; Meta later said it would release some models openly again).
- [The Future is for Everyone (Mark Zuckerberg, Meta)](https://www.meta.com/thefutureisforeveryone/): Meta's own case for "personal superintelligence" and open source AI, from its CEO; read "Securing Against AI Misuse", "Protecting Freedom and Preventing Government Tyranny", "Ensuring American Leadership" and "Alignment With People and Addressing Existential Risk" (August 2026).
- [[../Lenses/AI Safety Atlas - Strategies - Misuse Prevention Strategies|Misuse Prevention Strategies]]: the arguments for and against open weights, and why fine-tuning strips safeguards from released models; read the callouts "Ensuring a positive offense-defense balance in an open-source world" and "The impossible challenge of creating tamper-resistant safeguards".
- [xAI (Wikipedia)](https://en.wikipedia.org/wiki/XAI_(company)): xAI's founding by Musk, its "maximally truth-seeking" aim, Grok and the Colossus data centre, the MechaHitler incident and later deepfake scandal, and its merger into SpaceX; read the introduction, history and controversies (November 2026).
- [OpenAI and Anthropic researchers decry 'reckless' safety culture at xAI (TechCrunch)](https://techcrunch.com/2025/07/16/openai-and-anthropic-researchers-decry-reckless-safety-culture-at-elon-musks-xai/): why researchers at rival labs attacked Grok 4's launch without a system card or published safety results, set against Musk's long record of AI-risk warnings (July 2025).

## Tests

#### Question: Choice
id:: 55eb648b-82c5-482a-aac9-2808324630bd
content:: Meta has released its Llama language models as "open-weight" models. What does that mean?
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
id:: 9c9eb3ab-4080-4e26-8aba-582aa18be4af
content:: Meta's AI safety framework, first published in February 2025, said Meta would stop developing a model it judged to pose critical risk, for example of enabling cyberattacks or chemical and biological weapons. What did Meta's April 2026 revision say instead?
options::
- [x] Meta may keep developing such a model if safeguards bring its risk down to acceptable levels
- Meta will hand such a model to US government testers before deciding whether to continue
- Meta will stop developing such a model and also delete its trained weights
- Meta will share such a model only with a small group of vetted research partners
shuffle:: true

#### Question: Choice
id:: ecab19b9-dd03-433b-8cf4-c7c2b2f30273
content:: In July 2025, Mark Zuckerberg wrote that Meta would need to be "careful about what we choose to open source". How has Meta handled its most capable model since then?
options::
- [x] Its April 2026 frontier model, Muse Spark, is closed; some open-weight models are still planned
- It still releases each new frontier model with open weights, as it did with Llama
- It has ended all open-weight releases and says it will publish no more
- It shares its frontier weights only with US agencies and approved partners
shuffle:: true

#### Question: Choice
id:: 949e5c2c-bda6-46a5-98ca-13b97e6b1b92
content:: Yann LeCun was Meta's chief AI scientist from 2013 until he left in late 2025 to start his own company. Which view on AI risk is he known for?
options::
- [x] Language models are far from human-level AI, and takeover fears are overblown
- Advanced AI poses a serious extinction risk, so frontier development should pause
- Open-weight release of frontier models is too risky and should be restricted
- AI risk is real but is best handled by a few closed, licensed labs
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
- [x] Untested changes to a live chatbot's instructions can quickly cause public harm
- Open-weight chatbots are harder for their developers to control than closed ones
- A chatbot trained mostly on posts from X users will produce hateful content
- Outside attackers can easily take over a chatbot through its public interface
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
content:: Meta owns Facebook and Instagram, and xAI, now part of SpaceX, owns X. Explain one way owning a large social media platform affects the risks or advantages of their AI work.
assessment-instructions:: Score out of 100. 100 for any one clearly explained effect: they can put AI in front of billions of users quickly, so failures reach many people at once; they have vast user data to train on, raising privacy concerns; ad and engagement incentives may push chatbots to maximise engagement over wellbeing; platform revenue funds huge compute spending. 50 for naming an effect without explaining it.

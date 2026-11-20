---
id: a3bfdde3-0cf0-429e-b788-e62fbec598a8
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the EU AI Act's risk tiers for AI systems, the duties it places on providers of general-purpose AI models, the extra duties for models with systemic risk, and when these rules apply.

## Requires

## Helpful first

## Why it matters
The AI Act is a binding law that places duties on developers of frontier models, backed by fines. Knowing what it requires, and what it leaves out, lets you judge claims that advanced AI is "already regulated" and see where policy on catastrophic risk still has gaps.

## Lenses
- [AI Act (European Commission)](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai): the official overview of the four risk tiers with examples, the rules for general-purpose AI models, the AI Office's powers, and the timeline as changed by the 2026 AI Omnibus (October 2026).
- [High-level summary of the AI Act (Future of Life Institute)](https://artificialintelligenceact.eu/high-level-summary/): a closer look at what is banned, which uses count as high-risk and what their providers must do, and the duties for all general-purpose AI models, open-source ones and those with systemic risk; read from "Prohibited AI systems" to the end (August 2026).
- [General-Purpose AI Code of Practice (European Commission)](https://digital-strategy.ec.europa.eu/en/policies/gpai-code-practice): what the voluntary Code is, its three chapters, and which frontier developers have signed it (October 2026).

## Tests

#### Question: Choice
id:: 96054442-834b-4e51-a8c8-42b548996449
content:: Under the EU AI Act, how is an AI system that screens and ranks job applicants classified?
options::
- [x] High-risk
- Prohibited
- Limited risk, with transparency duties only
- Minimal risk, with no new duties
shuffle:: true

#### Question: Choice
id:: 483c9b28-82cc-48fd-a41b-b5ad91b8df39
content:: Which of these uses of AI does the EU AI Act ban outright, rather than allow under conditions?
options::
- [x] Inferring employees' emotions from webcam video to rate their engagement
- Scoring loan applicants' creditworthiness from their financial records
- Grading students' written answers in national school exams
- Flagging insurance claims that look fraudulent for human review
shuffle:: true

#### Question: Choice
id:: 21cb093f-75ea-4889-ad91-89ed75733c10
content:: Under the EU AI Act, what is the main obligation for a customer-service chatbot that is not used for any high-risk purpose?
options::
- [x] Telling users they are interacting with an AI
- Passing a conformity assessment before release
- Registering in the EU database for high-risk systems
- Having a human review every conversation
shuffle:: true

#### Question: Choice
id:: 24b0b854-387d-416b-aafb-470010fc8aa8
content:: Which use of AI falls outside the scope of the EU AI Act?
options::
- [x] Systems used only for military or defence purposes
- Remote biometric identification by police
- AI used as a safety component in medical devices
- Chatbots offered to the public
shuffle:: true

#### Question: FillBlank
id:: e9c130d7-e5ab-4ac5-8f6a-dbe083cc2e44
content:: The EU AI Act presumes that a general-purpose AI model has systemic risk if the compute used to train it exceeds {{10^25|1e25|10²⁵}} floating-point operations (FLOP).

#### Question: Choice
id:: 291d2251-666f-489c-8d80-31a458581465
content:: Under the EU AI Act, which obligation applies to every provider of a general-purpose AI model, not only to providers of models with systemic risk?
options::
- [x] Publishing a summary of the content used for training
- Running adversarial testing of the model
- Reporting serious incidents to the AI Office
- Ensuring adequate cybersecurity protection for the model
shuffle:: true

#### Question: Choice
id:: 38af838d-166c-4aa6-b360-f942256c7f9c
content:: A developer releases a general-purpose AI model with public weights under a free and open-source licence. The model is classified as having systemic risk. What does the EU AI Act require of the developer?
options::
- [x] All the systemic-risk duties, including model evaluations and incident reporting
- Only a copyright policy and a training-content summary, like other open-source models
- Nothing, since models with public weights fall outside the Act's scope
- The standard general-purpose duties, but none of the extra systemic-risk ones
shuffle:: true

#### Question: Choice
id:: 81811369-c4e7-4ff2-80f1-3806a42d1a62
content:: A US company trains a general-purpose AI model in the US and offers it to customers in the EU. Do the EU AI Act's rules for general-purpose AI models apply to this company?
options::
- [x] Yes
- No

#### Question: Choice
id:: cb06b292-1f59-40ff-b1bd-f1ac1a3d818e
content:: Who supervises and enforces the EU AI Act's rules for providers of general-purpose AI models?
options::
- [x] The European Commission's AI Office
- National authorities in each EU member state
- The European Data Protection Board
- The European Parliament's AI committee
shuffle:: true

#### Question: Choice
id:: 6712c7fc-2609-40e4-8d96-aeb49788abd8
content:: What is the legal status of the EU's General-Purpose AI Code of Practice, published in July 2025?
options::
- [x] Voluntary, but a way for providers to show they comply with the Act
- Binding on every model provider selling in the EU
- A replacement for the Act's rules on general-purpose models
- Guidance that applies only to open-weight models
shuffle:: true

#### Question: Choice
id:: ea0a385b-5ec1-4434-9e9e-0592c7203341
content:: As of November 2026, which of these parts of the EU AI Act has already started to apply?
options::
- [x] Obligations for providers of general-purpose AI models
- Requirements for high-risk AI in medical devices
- Requirements for high-risk AI in critical infrastructure
shuffle:: true

#### Question: Open
id:: 7e7c744f-e819-4012-84b3-ac15c8bad775
content:: The EU AI Act sorts AI systems into risk tiers mainly by what they are used for. Why does this fit poorly with general-purpose models such as large language models, and how does the Act deal with them?
assessment-instructions:: Score out of 100. 50 for explaining that one general-purpose model can be put to many uses, including high-risk ones, so its risk can't be judged from a single intended use. 50 for saying the Act adds separate duties for the model's provider, with extra duties for models with systemic risk (e.g. very large training compute).

#### Question: Open
id:: 6edba25b-c7fd-404d-bedf-12bb01b21262
content:: Name two requirements the EU AI Act places on the provider of a high-risk AI system.
assessment-instructions:: Score out of 100. 50 each for any two of: a risk management system; data quality and governance; technical documentation; record-keeping or logging; information for deployers; human oversight; accuracy, robustness and cybersecurity; a conformity assessment; registration in the EU database. Vague answers like "be safe" get 0.

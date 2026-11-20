---
id: f8808a7c-9905-4a5c-8811-f42afbb279e1
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what AI governance covers and compare its main levers, from company policies and standards to national law and international agreements, including who uses each and what it can reach.

## Requires

## Helpful first
- [[Sources of AI catastrophe]]

## Why it matters
Many proposals to reduce AI risk work through some governance lever. Knowing the levers lets you see which actors a proposal depends on, what it can and can't reach, and where it might fail, so you can judge proposals and choose where your own work fits.

## Lenses
- [[../Lenses/AI Safety Atlas - Governance - Governance Architectures|Governance Architectures]]: the three levels of AI governance (company, national, international), what each can reach and where each breaks down; read the opening overview, "Limitations" under Corporate Governance, and the National and International Governance sections up to "Policy Options" (2025).
- [[../Lenses/AI Safety Atlas - Governance - Governance Problems|Governance Problems]]: why rules on specific uses fall short for general-purpose AI, and why governance aims at development inputs such as compute rather than only at deployment (2025).
- [[../Lenses/AI Safety Atlas - Governance - Implementation|Implementation]]: how standards bodies, voluntary frameworks like NIST's, licensing and safety cases turn principles into enforceable rules; read the "AI Safety Standards" and "Ensuring Compliance" sections (2025).
- [Tort Law Should Be the Centerpiece of AI Governance (Lawfare)](https://www.lawfaremedia.org/article/tort-law-should-be-the-centerpiece-of-ai-governance): the case for liability and mandatory insurance as the main lever, from its leading proponent, Gabriel Weil, with the limits he concedes (August 2024).
- [Frontier AI Regulation: Managing Emerging Risks to Public Safety (arXiv)](https://arxiv.org/abs/2307.03718): the influential proposal for regulating frontier developers through standards, registration and reporting, and licensing; read the executive summary and section 1 (November 2023) (more advanced).

## Tests

#### Question: Choice
id:: c0ab7bba-c737-4c60-b034-427643de562f
content:: Which of these best describes "AI governance" as the term is used in AI safety?
options::
- [x] Rules, norms and institutions that shape how AI is built and used
- National laws that regulate AI products sold to consumers
- Technical methods that make AI systems follow their developers' intentions
- International treaties that limit military uses of AI
shuffle:: true

#### Question: Choice
id:: 93abb862-1901-4788-acfc-7bf345684010
content:: An AI company adopts a policy: it will pause training if a model passes certain dangerous-capability tests. No law requires this. What is the main weakness of this kind of governance?
options::
- [x] The company can weaken or drop it if rivals race ahead
- It covers only the models the company releases to the public
- Such tests can only be run after a model is released
- Regulators can overrule the policy whenever they like
shuffle:: true

#### Question: Choice
id:: 4858ff41-a446-4b77-9546-57c8a627dc97
content:: The EU AI Act's rules for general-purpose AI models also cover companies based outside the EU if they offer their models in the EU. Why might these rules affect the models such a company offers in other countries too?
options::
- [x] Keeping one version for all markets is often cheaper than keeping two
- The Act's rules apply to the company's work in every country
- Other countries' courts are required to enforce the EU's rules
- Trade agreements require other countries to copy the EU's rules
shuffle:: true

#### Question: Choice
id:: c969f348-cf7e-4828-a713-e2eb0bcd8b62
content:: Which of these is an example of "soft law" in AI governance?
options::
- [x] A voluntary code of practice that companies can choose to sign
- A national statute that sets fines for unsafe AI systems
- A court ruling that holds a developer liable for harm
- A treaty on AI that several states have ratified
shuffle:: true

#### Question: Choice
id:: 5c412f7e-b4e9-40b9-a2ff-19e903181bad
content:: A law makes AI developers pay damages when their models cause serious harm, but sets no specific safety rules. How is this kind of liability rule meant to improve safety?
options::
- [x] It gives developers a financial reason to reduce risks themselves
- It lets regulators inspect models before they are released
- It bans releasing models above a set capability threshold
- It requires developers to publish their safety test results
shuffle:: true

#### Question: Choice
id:: f2e5fcd0-1563-47f8-9942-96bf2a432e9f
content:: Why do many proposals for reducing catastrophic AI risk target the companies that train frontier models, rather than everyone who uses AI?
options::
- [x] Few companies train the most capable models, so rules there are easier to enforce
- Most AI users are covered by consumer law, so they need no new rules
- AI users cannot be identified online, so no rules can reach them
- International law forbids rules on individual users, so states must target companies
shuffle:: true

#### Question: Choice
id:: cd79bdc6-7145-4929-8d9c-6a2c2ef3c76d
content:: Which of these AI governance measures acts on AI development rather than on AI deployment?
options::
- [x] Requiring a licence before training very large models
- Banning AI-generated political ads during elections
- Requiring chatbots to tell users they are talking to an AI
- Restricting the use of AI in hiring decisions
shuffle:: true

#### Question: Choice
id:: b789c032-ad98-4090-a780-06a7bc3171ec
content:: Which of these is an example of AI governance by a non-government actor?
options::
- [x] An insurer refusing to cover an AI company unless it passes safety audits
- A national AI safety institute testing a model before its release
- A trade ministry limiting exports of advanced AI chips to some countries
- A regulator fining a company for selling an unsafe AI product
shuffle:: true

#### Question: Choice
id:: 344607ef-4f60-4f5f-a0c3-7c9869500dc2
content:: What role do technical standards, such as those from ISO or NIST, usually play in AI governance?
options::
- [x] Voluntary guidance on good practice, which laws or contracts can make required
- Binding rules set by international bodies, which every member country must enforce
- Safety policies that individual AI companies publish about their own models
- Treaties in which governments agree on common safety rules for AI
shuffle:: true

#### Question: Choice
id:: 292723fd-2658-4419-8a3b-9d2c7022941e
content:: Why do many people argue that national AI laws alone may not be enough to manage risks from advanced AI?
options::
- [x] Countries fear falling behind rivals if they act alone
- Courts in most countries have struck down national AI laws
- National laws can cover AI products but not AI research
- Most countries lack any agency able to enforce national laws
shuffle:: true

#### Question: FillBlank
id:: c291ab59-dfd2-4e4a-b7ae-bf3281f41cbe
content:: Governing AI by controlling access to AI chips and data centers is called {{compute governance|governance of compute}}.

#### Question: Open
id:: e8767d6c-de89-4fc1-8ca4-8f1a1d54c47d
content:: Name two AI governance levers that work at different levels (for example company, national or international), and give one weakness of each.
assessment-instructions:: Score out of 100. 25 points per correct lever (up to two, at different levels) and 25 per fitting weakness. Examples: company safety policies (voluntary, can be dropped); national law (stops at borders, slow to pass); international agreements (hard to negotiate and verify); standards (voluntary unless referenced); liability (acts only after harm). Accept other reasonable pairs.

#### Question: Open
id:: 75ef8130-ca1a-4b80-a86c-ed90c465c892
content:: A government regulates AI through rules on specific uses, such as hiring or medical devices, and has no rules on general-purpose models. What risk from advanced AI might this approach miss, and why?
assessment-instructions:: Score out of 100. 100 for naming a risk that arises before or outside any specific use, with a reason: e.g. dangerous capabilities in general-purpose models, theft of model weights, loss of control during development or internal use, or misuse in uses no rule anticipated. 50 for a relevant risk with no reason.

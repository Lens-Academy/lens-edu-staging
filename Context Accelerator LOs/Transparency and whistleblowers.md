---
id: ab520501-c8f8-4628-9060-7aafca07ecdd
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how disclosure rules and whistleblower protections help outsiders learn about risks inside AI companies, give examples of each, and describe their main limits.

## Requires

## Helpful first
- [[Frontier safety frameworks]]

## Why it matters
At frontier AI companies, test results, near misses, cut corners and how fast AI is speeding up the company's own research are usually seen first by staff, often before any model is released. Knowing what companies must disclose, and when insiders are protected for speaking up, helps you judge how much outsiders really know and which gaps in oversight matter most.

## Lenses
- [What California's SB 53 Does (Carnegie Endowment)](https://carnegieendowment.org/emissary/2025/10/california-sb-53-frontier-ai-law-what-it-does): what the first US frontier AI law makes developers publish and report, its whistleblower protections, why it relies on disclosure instead of mandated safeguards, and its gaps (October 2025).
- [A Right to Warn about Advanced Artificial Intelligence (righttowarn.ai)](https://righttowarn.ai/): the open letter from current and former OpenAI and Google DeepMind staff on why confidentiality deals and law-breaking-only whistleblower laws silence insiders, and their four demands of AI companies (June 2024).
- [[../articles/aiwi-ai-whistleblowing-law-best-practices-aiwi-carma|AI Whistleblowing Law: Best Practice Guide]]: an advocacy group's case for stronger AI whistleblower law: why existing laws miss legal-but-dangerous practices, equity and visa risks, and why internal channels and receiving agencies need independence and expertise; read the Introduction, Retaliation Protection, Disclosure Channels, Remedies and Agency Requirements (July 2026).
- [[../Lenses/phillips-robins-with-the-raise-act-new-york-aligns-with-california-on-frontier-ai-laws|New York's RAISE Act and SB 53]]: how New York copied California's "trust but verify" disclosure model, where the two laws differ, and the open question of what governments will do with the reports (February 2026).

## Tests

#### Question: Choice
id:: 29d17e19-c5cb-4271-82ae-22ae955ed337
content:: Why might general US whistleblower laws fail to protect an AI company employee who reports a serious safety risk to a regulator?
options::
- [x] Many cover only law-breaking, and the risky practice may be legal
- They protect public-sector workers but not private-sector workers
- They protect only employees who report anonymously
- They don't apply to anyone who signed a confidentiality agreement
shuffle:: true

#### Question: Choice
id:: aad89315-b429-427e-a108-230aefa2be18
content:: In 2024 it emerged that OpenAI's exit agreements had a feature that critics said discouraged former staff from speaking about risks. What was it?
options::
- [x] Refusing to sign a no-criticism pledge could cost them vested equity
- They had to delete their work notes and emails on leaving
- They were barred from joining rival AI companies for five years
- They had to submit any public writing for company approval
shuffle:: true

#### Question: Choice
id:: 8fad687d-5eb5-472b-a9a6-1372a8c28867
content:: What must large frontier AI developers publish under California's SB 53, the frontier AI transparency law signed in 2025?
options::
- [x] A framework describing how they assess and manage catastrophic risks
- The full training data used for their frontier models
- The weights of any model trained above a compute threshold
- The source code of their safety evaluation tools
shuffle:: true

#### Question: Choice
id:: d781219f-4173-41dd-9cee-97cf60084a6e
content:: Under California's SB 53, who decides which safety measures go into a large AI developer's published frontier AI framework?
options::
- [x] The company, which must then follow its own framework
- A state agency that writes one framework for all developers
- An independent auditor appointed by the state Attorney General
- A panel of experts drawn from rival AI companies
shuffle:: true

#### Question: Choice
id:: 42454dda-5024-4feb-a291-2322a98e93e3
content:: What is the main argument for AI rules that require companies to disclose their safety practices, rather than rules that mandate specific safety measures?
options::
- [x] Experts don't yet agree which safeguards work, so make practices visible first
- Disclosure lets members of the public test models for dangerous capabilities
- Disclosure gives regulators the power to block a risky model's release
- Without disclosure rules, companies keep no records of their safety testing
shuffle:: true

#### Question: Choice
id:: 18514235-62de-472e-ad2e-3891cdedd46d
content:: What is a common criticism of transparency-only rules for frontier AI developers?
options::
- [x] They require describing safety plans, not making those plans adequate
- They force companies to reveal their model weights to competitors
- They mainly burden small startups rather than large developers
- They ban companies from updating their published safety plans
shuffle:: true

#### Question: Choice
id:: a77e5c2e-a658-4371-8709-e706681b781c
content:: California's SB 53 and the EU AI Act both require frontier AI developers to report serious safety incidents to a government body. What is the main purpose of such reporting?
options::
- [x] To let officials spot emerging risks and patterns across companies
- To let officials fine companies for each model malfunction
- To give the public live access to companies' internal logs
- To replace companies' own internal safety testing
shuffle:: true

#### Question: Choice
id:: 51d97199-a170-4829-bc25-70631cc702ac
content:: An AI company has an internal channel for staff to raise safety concerns. Why do advocates also want staff to have a protected right to report to regulators?
options::
- [x] Internal channels may answer to the leaders who made the risky decision
- Regulators can pay financial rewards that internal channels can't
- Internal reports are usually barred from mentioning catastrophic risks
- Regulators can investigate concerns faster than internal teams can
shuffle:: true

#### Question: Choice
id:: a64a09e4-c489-46c1-ab84-ce5908937567
content:: California's SB 53 protects some frontier AI company staff from retaliation for reporting concerns to officials. Which reports does it cover that many older whistleblower laws don't?
options::
- [x] Reports that the company's work poses a substantial danger of catastrophe, even if legal
- Reports made to journalists or on social media, as well as to officials
- Reports by any employee about any product decision they disagree with
- Reports that include the company's unreleased model weights as evidence
shuffle:: true

#### Question: Open
id:: 73a69d96-9a77-4551-92f6-f08408e9c67c
content:: Name two kinds of information about AI risk that employees of a frontier AI company may see before anyone outside the company.
assessment-instructions:: Score out of 100. 100 for any two of: dangerous-capability evaluation results; capabilities of unreleased or internal-only models; how much AI is speeding up the company's own research; safety incidents or near misses; whether the company follows its safety commitments; security weaknesses, such as risk of model weights being stolen; pressure to shorten safety testing; internal disagreement about risks. 50 for one.

#### Question: Open
id:: cb9d9175-b7ed-489b-a4ef-065273b6be1c
content:: A law requires AI companies to publish safety reports but gives employees no protection for reporting concerns. Explain how adding whistleblower protections could make the disclosure rule more effective.
assessment-instructions:: Score out of 100. 100 for saying that protected insiders can reveal when published reports are false, incomplete or not being followed, which outsiders can't check themselves, so companies have more reason to report honestly. 50 for saying only that insiders know more, without linking this to checking the reports.

#### Question: Open
id:: 3d5d6c89-68b0-46cf-aeef-4c0292d1351f
content:: Even where whistleblower protections exist, give one reason an AI company employee might still not report a serious safety concern.
assessment-instructions:: Score out of 100. 100 for any one of: fear of career damage or being blacklisted in a small industry; losing equity or other pay; unclear whether the concern is legally covered; legal costs; worry about breaching confidentiality or trade secrets; uncertainty whether the risk is real; loyalty to colleagues or the company's mission. 50 for a vague answer such as "fear" with no detail.

---
id: dd13ce6c-5a55-450a-aab5-ac6f0f5927c1
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what government AI safety institutes such as the UK AI Security Institute and the US CAISI do, what powers they lack, and how their mandates shifted toward national security in 2025.

## Requires

## Helpful first
- [[AI evaluations]]

## Why it matters
These institutes are the main way governments test frontier AI models themselves. Knowing what they can and can't do, and how political changes have shifted their focus, helps you judge claims that frontier AI is under government oversight and see where new powers or funding could make a difference.

## Lenses
- [AI Safety Institute (Wikipedia)](https://en.wikipedia.org/wiki/AI_Safety_Institute): the plain facts on the UK, US and other institutes: their founding around the Bletchley summit, the 2025 renames to the AI Security Institute and CAISI, the international network, Inspect and early problems getting access to models; read the UK, US and international network sections (2026).
- [Early lessons from evaluating frontier AI systems (UK AI Security Institute)](https://www.aisi.gov.uk/work/early-lessons-from-evaluating-frontier-ai-systems): the institute's own account of how it tests models before release, what access it needs from companies, how it reports results back to them and why a test is not a safety certificate (October 2024).
- [Safety first? (Ada Lovelace Institute)](https://adalovelaceinstitute.org/blog/safety-first/): a critique of the voluntary model: the UK institute can't block a release, its access depends on companies agreeing, and the authors argue it needs legal powers to compel access (May 2024, before the renames).
- [[../articles/ai-security-institute-frontier-ai-trends-report|Frontier AI Trends Report]]: what the UK AI Security Institute tests for and what it has found, from cyber and biology to loss-of-control capabilities like self-replication; read the Executive Summary through "Our testing approach" (December 2025).

## Tests

#### Question: Choice
id:: 9323c6d2-7c3e-447b-990a-74fe0fab5325
content:: As of November 2026, how does the UK AI Security Institute get access to frontier AI models before their public release?
options::
- [x] Through voluntary agreements with the companies
- Under a law requiring companies to submit their models
- Through licences companies need to sell AI in the UK
- By rules that apply to models above a compute threshold
shuffle:: true

#### Question: Choice
id:: e505f2f9-421a-4836-9693-4af06dd3a38d
content:: In February 2025 the UK renamed its AI Safety Institute. Which shift in focus came with the new name?
options::
- [x] Toward national security risks such as cyberattacks, weapons and crime
- Toward bias, fairness and misinformation in AI products
- Toward promoting British AI companies to foreign investors
- Toward licensing and inspecting AI companies operating in the UK
shuffle:: true

#### Question: Choice
id:: 12005162-d364-4b0d-8769-99b9a06db99a
content:: In June 2025 the US AI Safety Institute was renamed the Center for AI Standards and Innovation (CAISI). Which best describes its focus after the change?
options::
- [x] Industry standards, national security testing and US AI competitiveness
- Binding safety licences, audits and penalties for frontier AI developers
- Civil rights, bias and consumer harms from AI products
- International AI treaties and funding for global safety research
shuffle:: true

#### Question: Choice
id:: 90e368c7-0071-40f1-bebd-fbbbf266d703
content:: Under the EU AI Act, what role does the European Commission's AI Office have toward providers of general-purpose AI models, as of November 2026?
options::
- [x] Supervising and enforcing their obligations, including with fines
- Advising member states, with no enforcement role of its own
- Approving each new model before it can be released in the EU
- Testing models only when providers volunteer them
shuffle:: true

#### Question: Choice
id:: 210d5dcd-6065-4c85-bf8b-b4ea388a25ae
content:: In 2024 several governments formed the International Network of AI Safety Institutes, renamed in December 2025 the International Network for Advanced AI Measurement, Evaluation and Science. What is its main purpose?
options::
- [x] Building shared methods and science for evaluating advanced AI
- Setting binding AI rules that member countries must adopt
- Certifying AI models as safe across member countries
- Negotiating a treaty to limit frontier AI development
shuffle:: true

#### Question: Choice
id:: e4c8fdd3-d8cb-446a-af17-d2e46fa55583
content:: When the UK or US government AI institute tests a company's model before release, what usually happens with the results?
options::
- [x] Most go only to the company and government, not the public
- They are published in full alongside the model's release
- The institute uses them to approve or block the release
- The company must fix every problem found before release
shuffle:: true

#### Question: Choice
id:: 1a02b563-e117-47c0-9764-ca35037fd504
content:: After the UK renamed its AI institute in 2025, does the institute still work on the risk of humans losing control of advanced AI systems?
options::
- [x] Yes, loss of control remains one of its research areas
- No, it now leaves that area to academic and company researchers

#### Question: Open
id:: 4ceb5884-5bd4-476d-b85b-7b090a0a667d
content:: Government AI safety institutes test some frontier AI models before public release. Give one way this testing can reduce risk.
assessment-instructions:: Score out of 100. 100 for any one of, with the mechanism stated: the developer can fix problems or add safeguards before release; the government learns early about dangerous capabilities and can prepare; it is an independent check on the developer's own safety claims; it builds government expertise and evidence for future rules. 50 for a vague answer with no mechanism.

#### Question: Open
id:: e7672598-f3d4-4f48-b915-738f47698f3e
content:: Name one limit on how much government AI safety institutes can reduce risk from frontier AI, and say why it matters.
assessment-instructions:: Score out of 100. 100 for any one of, with a reason: access depends on companies agreeing; they can't block or delay a release; tests can miss dangerous capabilities or behaviour; budgets and staff are small next to AI companies'; mandates and funding change with governments; little reach over open-weight or foreign models. 50 for naming a limit without saying why it matters.

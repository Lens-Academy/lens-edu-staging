---
id: '3eadac2f-e82d-478a-9c1e-0b5a6136c211'
title: "2.2.2 Customer identification and ongoing monitoring"
tldr: "Banks learned the hard way that you must know who you are dealing with, and that customers split transactions to stay under reporting limits. Egan and Heim port that playbook to compute providers: who gets identified, what is monitored after sign-up, and how a customer could split a job to stay under the threshold."
summary_for_tutor: "Reading lens adapted from XLab lesson 2.2.2. Egan and Heim (2023), Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers, inlined as article excerpts: the opening of section 2, selected parts of Box 3 (financial-sector KYC obligations and implementation lessons), section 2.1, the opening of section 2.2 with Box 4, and sections 2.2.1 and 2.2.2. No questions in this lens. If the learner asks, help them connect the pieces: the compute threshold, customer identification, beneficial ownership, ongoing monitoring, reporting of high-risk profiles, and the two evasion routes (structuring and shell companies). Ends with a Works cited callout."
tags: [wip]
duration_minutes: 22
---
#### Text
content::
\## 2.2.2 Customer identification and ongoing monitoring

Provider records become a verification mechanism only when rules specify how
they should be used. This section examines how know-your-customer requirements
connect customer identity, ongoing monitoring, reporting, and access decisions.

\## Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers

*Source: Janet Egan and Lennart Heim (2023), [original](https://arxiv.org/abs/2310.13625)*

The opening passage, selected parts of Box 3, complete §2.1, the opening of §2.2, and §§2.2.1–2.2.2 are reproduced under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

\### [Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers](https://arxiv.org/abs/2310.13625)
*opening of §2*
Egan and Heim (2023) | CC BY 4.0
{>>{"author":"Elias's AI","timestamp":1788016129753}@@The abstract excerpt that was here is not part of the XLab lesson. XLab quotes the opening of section 2 and selected parts of Box 3 instead; replaced accordingly.<<}

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: The US government should introduce a KYC scheme that ensures adequate monitoring for advanced AI cloud compute
to:: The history of the implementation of KYC in the financial sector could provide useful lessons for scheme design (Box 3).

#### Text
content::
\### Box 3: Learning from KYC in the financial sector — selected requirements and implementation lessons

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: This legislation creates obligations for financial institutions to:
to:: report suspicious activity to the US government.[^note-11]

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: _Implementation: obstacles and adjustments_
to:: Amendments made through the _2001_ _PATRIOT Act_ have sought to address this by making structuring a criminal offense.

#### Text
content::
*Reproduced from Egan and Heim, Box 3, under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). [Open the paper on arXiv.](https://arxiv.org/abs/2310.13625)*

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: ### 2.1 Compute is indicative of AI capabilities and KYC thresholds should be set accordingly
to:: Applying a specified FLOP threshold offers a feasible path to implementation and does not require cloud providers to access the data or confidential information of their customers. Cloud access to chips is billed by the hour, so the accumulated total FLOP is easily identifiable by the compute provider. The compute provider could then implement KYC checks and enhanced due diligence for any projects seeking to cross that threshold. In many cases, the total amount of compute procured will be specified at the time of entering into contract, but there may also be cases where additional compute is purchased over time, to the point at which a specific vendor crosses the threshold. Compute providers should therefore continuously monitor compute use, and ensure that entities approaching the threshold are funneled into the KYC process before that point is reached.

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: #### Regulatory impost is likely to be low, with few stakeholders affected
to:: and Amazon, Anthropic, Google, Inflection, Meta, Microsoft, OpenAI and NVIDIA, among others, have committed to further safeguards against risky AI.

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: ### 2.2 Requirements on compute providers – due diligence that identifies risk and implements controls
to:: • Maintaining records on the provision or denial of above-threshold compute to aid in investigations or demonstrate compliance, when needed.

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: #### 2.2.1 Technical feasibility
to:: Thus, the implementation of the KYC scheme would not require the compute provider to access the underlying code, data, or any system level insights, maintaining appropriate privacy standards.

#### Article
source:: [[../articles/egan-oversight-for-frontier-ai-through-a-know-your-customer-scheme-for-compute-providers]]
from:: #### 2.2.2 Mitigating attempts to evade detection
to:: Given the relatively small numbers of entities seeking to access significant amounts of advanced AI compute in the near term, a government enforcement team could consider undertaking their own investigations and spot checks on companies.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Egan and Heim (2023), *Oversight for Frontier AI through a Know-Your-Customer Scheme for Compute Providers*, is cited inline above with its arXiv link.

XLab. "2.2.2 Customer identification and ongoing monitoring." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-customer-identification)
*The source lesson this page adapts.*
:::

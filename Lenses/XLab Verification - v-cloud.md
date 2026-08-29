---
id: 'f78c8de0-f12f-446e-992b-a27c30dc3e84'
title: "2.2.1 Provider records and workload observables"
tldr: "A cloud provider bills you for every GPU hour, so it already holds a ledger of who rented what, for how long. Read Heim et al. to work out what that ledger can prove about a training run, what it cannot, and where the provider's reach ends."
summary_for_tutor: "Reading lens adapted from XLab lesson 2.2.1. An objectives callout, then Heim et al. (2024), Governing Through the Cloud: four executive-summary paragraphs as article excerpts, then sections 3.2, 3.3.2 to 3.3.4 and Appendix B (Table 4) inlined as article excerpts. No questions in this lens; the learner is told to keep two columns while reading (what record or signal exists; what conclusion it supports and what it does not establish). If the learner asks for help, work from the text: distinguish provider-controlled records from customer declarations, and separate workload classification (what kind) from compute accounting (how much). Ends with a Works cited callout."
tags: [wip]
duration_minutes: 38
---
#### Text
content::
Cloud providers sit between AI developers and the machines they rent. Because
providers own, operate, meter, and bill for that compute, they can act as record
keepers, verifiers, enforcers, and securers. But cloud evidence is one witness,
not the whole court: self-hosted clusters, non-signatory jurisdictions, and
stolen weights all sit outside a provider's reach. In this module, you will
learn what cloud providers can observe, how those observations become evidence,
and where cloud oversight runs out.

:::callout {title="By the end of this submodule, you will be able to:" tone="blue"}
1. Identify the identity, resource-use, and operational records a cloud provider can observe, and explain what each record supports—and what it still does not establish.
2. Distinguish provider-controlled evidence from customer declarations, and assess the reliability of each when determining a workload's type, scale, and operator.
3. Analyze how customer identification, beneficial-ownership checks, reporting thresholds, ongoing monitoring, and access controls turn cloud records into a verification regime—and how an evader could route around them.
4. Assess where cloud oversight loses coverage, and identify which claims require corroboration from hardware, intelligence, or human verification mechanisms.
:::

\## 2.2.1 Provider records and workload observables

The four readings in this submodule do different jobs. The first establishes what a provider can observe. The second adds customer identity and due diligence. The third shows how a threshold can be evaded. The fourth asks whether the resulting control is politically and administratively usable.

As you read, keep two columns:

1. **What record or signal exists?**
2. **What conclusion does it support—and what does it still not establish?**

Start by asking which claims a provider's ordinary records can support—and
which claims remain beyond those records.

\## Governing Through the Cloud: The Intermediary Role of Compute Providers in AI Regulation

*Source: Lennart Heim, Tim Fist, Janet Egan, Sihao Huang, Stephen Zekany, Robert Trager, Michael A. Osborne, and Noa Zilberman (2024), [original](https://arxiv.org/abs/2403.08501)*

The executive-summary selections and complete sections below are reproduced under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Citations and cross-references link to the pinned arXiv version.

\### [Governing Through the Cloud](https://arxiv.org/abs/2403.08501)
*selected paragraphs from the Executive Summary*
Heim et al. (2024) | CC BY 4.0
{>>{"author":"Elias's AI","timestamp":1788015744302}@@The four executive-summary paragraphs were pasted here verbatim and also embedded as the four Article segments that follow, so the learner read them twice. Removed the copy from the Text segment; the Article segments carry them. The "Read the following sections in full" instruction moves to its own Text segment before the section excerpts.<<}

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: Governance Capacities — We propose that compute providers can leverage their crucial role in the AI supply chain to secure infrastructure and serve as the intermediate node in support of regulatory objectives while maintaining customers’ privacy and rights. They can facilitate effective AI regulation via four key capacities: as _securers_, _record keepers_, _verifiers_, and, in some cases, even _enforcers_. Reporting represents a related yet distinct dimension, wherein compute providers provide information to authorities as mandated by law or regulations. ([Section 2](#S2 "2 Governance Capacities of Compute Providers ‣ Governing Through the Cloud:The Intermediary Role of Compute Providers in AI Regulation"))
to:: Governance Capacities — We propose that compute providers can leverage their crucial role in the AI supply chain to secure infrastructure and serve as the intermediate node in support of regulatory objectives while maintaining customers’ privacy and rights. They can facilitate effective AI regulation via four key capacities: as _securers_, _record keepers_, _verifiers_, and, in some cases, even _enforcers_. Reporting represents a related yet distinct dimension, wherein compute providers provide information to authorities as mandated by law or regulations. ([Section 2](#S2 "2 Governance Capacities of Compute Providers ‣ Governing Through the Cloud:The Intermediary Role of Compute Providers in AI Regulation"))

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: Technical Feasibility — Our analysis indicates these governance capabilities are likely to be technically feasible and possible to implement in a confidentiality- and privacy-preserving way using techniques available to compute providers today. Compute providers often collect a wide range of data on their customers and workloads, for the purposes of billing, marketing, service analysis, optimization, and fulfilling legal obligations. Much of this data could also be used to support identity verification, as well as verifying technical properties of workloads. At a minimum, providers have access to billing information and can access basic technical data on how their hardware is used. This likely makes it possible for compute providers to develop techniques to detect and classify certain relevant workloads (e.g., whether a workload involves training a frontier model) and to quantify the amount of compute consumed by a workload. Verification of more detailed properties of a workload, such as the type of training data used, or whether a particular model evaluation was run, could be useful for governance purposes but is not currently possible without direct access to customer code and data. With further research and development efforts, compute providers may be able to offer “confidential computing” services to allow customers to prove these more detailed properties without otherwise revealing sensitive data. ([Section 3](#S3 "3 Technical Feasibility of Compute Providers’ Governance
to:: Technical Feasibility — Our analysis indicates these governance capabilities are likely to be technically feasible and possible to implement in a confidentiality- and privacy-preserving way using techniques available to compute providers today. Compute providers often collect a wide range of data on their customers and workloads, for the purposes of billing, marketing, service analysis, optimization, and fulfilling legal obligations. Much of this data could also be used to support identity verification, as well as verifying technical properties of workloads. At a minimum, providers have access to billing information and can access basic technical data on how their hardware is used. This likely makes it possible for compute providers to develop techniques to detect and classify certain relevant workloads (e.g., whether a workload involves training a frontier model) and to quantify the amount of compute consumed by a workload. Verification of more detailed properties of a workload, such as the type of training data used, or whether a particular model evaluation was run, could be useful for governance purposes but is not currently possible without direct access to customer code and data. With further research and development efforts, compute providers may be able to offer “confidential computing” services to allow customers to prove these more detailed properties without otherwise revealing sensitive data. ([Section 3](#S3 "3 Technical Feasibility of Compute Providers’ Governance

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: Technical and Governance Challenges — To realize a robust governance model, several technical and governance challenges remain. These include identifying additional measurable properties of AI development that correspond to potential threats, making workload classification methods robust to potential evasion, and formulating privacy-preserving verification protocols. ([Section 5.1](#S5.SS1 "5.1 Technical Challenges ‣ 5 Key Challenges ‣ Governing Through the Cloud:The Intermediary Role of Compute Providers in AI Regulation"))
to:: Technical and Governance Challenges — To realize a robust governance model, several technical and governance challenges remain. These include identifying additional measurable properties of AI development that correspond to potential threats, making workload classification methods robust to potential evasion, and formulating privacy-preserving verification protocols. ([Section 5.1](#S5.SS1 "5.1 Technical Challenges ‣ 5 Key Challenges ‣ Governing Through the Cloud:The Intermediary Role of Compute Providers in AI Regulation"))

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: The success of our proposed oversight scheme hinges on its multilateral adoption to prevent the migration of AI activities to jurisdictions with less stringent oversight. For an international framework to be durable and effective, it must address concerns from non-US governments. Cooperation will need to account for complex privacy and oversight issues associated with globally spread data centers. Compute provider oversight may affect competition in the AI ecosystem and raise concerns about issues of national competitiveness, and, consequently, this may influence the ability of US providers to offer products globally, including to foreign public-sector customers. Industry-led privacy-preserving standards could help ensure trust, but further research is needed to incentivize broad international buy-in to a global framework. ([Section 1.4](#S1.SS4 "1.4 Limitations and Future Research
to:: The success of our proposed oversight scheme hinges on its multilateral adoption to prevent the migration of AI activities to jurisdictions with less stringent oversight. For an international framework to be durable and effective, it must address concerns from non-US governments. Cooperation will need to account for complex privacy and oversight issues associated with globally spread data centers. Compute provider oversight may affect competition in the AI ecosystem and raise concerns about issues of national competitiveness, and, consequently, this may influence the ability of US providers to offer products globally, including to foreign public-sector customers. Industry-led privacy-preserving standards could help ensure trust, but further research is needed to incentivize broad international buy-in to a global framework. ([Section 1.4](#S1.SS4 "1.4 Limitations and Future Research

#### Text
content::
Read the following sections in full. In Appendix B, use Table 4 as a map from each observable to its current availability and the verification task it might support.

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: ### 3.2 Record Keeping
to:: This information is based on conversations, public data collection, and privacy policies available from a representative sample of large and small compute providers ([AWS 2024g]; [CoreWeave 2022]; [FluidStack 2022]; [Google Cloud 2024c]; [Lambda Labs 2022]; [Microsoft 2024a]).

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: #### 3.3.2 Workload Classification
to:: The difficulty of classifying workloads increases if a compute customer is actively trying to disguise the nature of their workload. This kind of obfuscation may become likely in cases where a customer has a strong financial, criminal, or political incentive to avoid regulatory oversight. Such incentives are likely to grow when frontier AI models become both more attractive for criminal activities and more economically lucrative. Analogous practices can be observed in the finance sector, where illicit actors have engaged in “structuring” (breaking up a single transaction into several smaller transactions) to avoid automated transaction reporting from their bank to the regulator ([Linn 2010]). We discuss and list these challenges in [Section 5.1](#S5.SS1 "5.1 Technical Challenges ‣ 5 Key Challenges ‣ Governing Through the Cloud:The Intermediary Role of Compute Providers in AI Regulation").

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: #### 3.3.3 Compute Accounting
to:: Role ‣ Governing Through the Cloud:The Intermediary Role of Compute Providers in AI Regulation")). Empirical measurements form an upper bound for compute usage, as not every operation can be known to have contributed to a workload.

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: #### 3.3.4 Detailed Workload Verification
to:: Using confidential computing techniques, customers may be able to provably verify particular governance-relevant properties of their workloads to their compute provider or directly to a regulator. For example, a customer may wish to demonstrate that they ran a particular model evaluation, obtained a particular result on a model evaluation, or did (not) use a particular dataset during training. However, these techniques have yet to be fully validated and implemented in production contexts. Several organizations are actively researching and developing software for using confidential computing to allow privacy-preserving auditing of models ([Mithril Security 2024b](#bib.bib111); [OpenMined 2023](#bib.bib126); [OpenMined 2024](#bib.bib127)). There has also been some work on expanding these techniques to allow privacy-preserving auditing of training workloads (e.g., the dataset used, or quantity of compute consumed), though this area is less well-explored ([Choi et al. 2023](#bib.bib38); [Mithril Security 2024a](#bib.bib110)).[^31] If regulatory requirements on compute providers end up requiring them to validate more fine-grained properties of workloads, these kinds of methods could be used to achieve this in a way that preserves customer confidentiality and privacy. In the meanwhile, we encourage compute providers and developers to explore and develop these techniques to ensure they can be implemented without meaningful performance penalties, and while preserving other aspects of customer experience and confidentiality.

#### Article
source:: [[../articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation]]
from:: ## Appendix B Observable Data Attributes
to:: | Training dataset | _Workload classification, compute accounting, detailed workload verification._ | Yes. Can potentially be made privacy-preserving using confidential computing techniques. | Possible to collect with customer consent. | Unclear (highly dependent on implementation). |

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Heim et al. (2024), *Governing Through the Cloud*, is cited inline above with its arXiv link.

XLab. "2.2.1 Provider records and workload observables." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud)
*The source lesson this page adapts.*
:::

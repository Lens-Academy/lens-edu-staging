{++{"author":"Elias's AI","timestamp":1787218142987}@@---
id: '3eadac2f-e82d-478a-9c1e-0b5a6136c211'
title: "2.2.2 Customer identification and ongoing monitoring"
tldr: "Faithful alpha import of XLab lesson 2.2.2 Customer identification and ongoing monitoring."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. Interactive elements marked as import gaps must be completed on XLab until Lens has an equivalent."
tags: [wip]
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

The US government should introduce a KYC scheme that ensures adequate monitoring for advanced AI cloud compute and allows the government to require compute providers to report high-risk entities and deny access to entities of concern. A KYC scheme requires businesses and organizations to verify the identity of their clients in order to provide them with access to particular goods and services. Introducing KYC requirements for entities accessing significant amounts of compute could help identify risks and enable further targeted restrictions where there is significant risk to national and global interests. Requiring compute providers to build greater awareness of the risks could encourage a safer AI industry aligned with public benefit.

It is important to note that this proposed KYC scheme for advanced AI cloud compute would not capture all AI models being developed or used by malicious actors. For example, there are already specific less-advanced models today, which do not require massive amounts of compute, that raise biochemical weapon development concerns or enable more targeted malicious cyber activity. Setting the threshold to capture and monitor the compute of all AI models would not be beneficial, as it would capture too much information to be useful while imposing a significant imposition on industry. Such risks could instead be managed through other safeguards, while the proposed in-depth KYC would focus on powerful foundation models trained on significant amounts of compute.

The history of the implementation of KYC in the financial sector could provide useful lessons for scheme design (Box 3).

**SourceBox**

This legislation creates obligations for financial institutions to:

- implement a customer identification program
- conduct risk assessments
- undertake enhanced due diligence for customers assessed as higher risk
- identify and verify a customer’s beneficial owners
- conduct ongoing monitoring
- report suspicious activity to the US government.

**Implementation: obstacles and adjustments**

The financial sector presents a case study of situations in which non-compliance with obligations persisted until significant penalties were applied. For the first decade of the Bank Secrecy Act, from 1972 to 1985, regulators did not enforce reporting requirements, resulting in low compliance from financial institutions. However, a 1985 $500,000 penalty issued to the Bank of Boston led to a sharp increase in reporting, as well as more evasive behavior from customers. More recently, Congress has taken further action to increase enforcement. The Anti-Money Laundering Whistleblower Improvement Act, signed into law in December 2022, increases reporting incentives with greater financial rewards for successful tips.

KYC in the financial sector also demonstrates implementation risks, including the use of “structuring” to evade publicly set thresholds. In response to obligations for banks to report transactions exceeding $10,000 in any one day, entities and individuals started to intentionally break up transactions across bank accounts and/or days to avoid scrutiny. Amendments made through the 2001 PATRIOT Act have sought to address this by making structuring a criminal offense.

**Src**

  Reproduced from Egan and Heim, Box 3, under [CC BY
  4.0](https://creativecommons.org/licenses/by/4.0/). [Open the paper on
  arXiv.](https://arxiv.org/abs/2310.13625)

  
\### 2.1 Compute is indicative of AI capabilities and KYC thresholds should be set accordingly
KYC obligations should apply at and beyond a threshold of advanced AI compute that captures the most critical AI risks, while minimizing regulatory impost on industry.[7](https://arxiv.org/abs/#ax-fn-7) One can quantify the computational performance of hardware in terms of a unit of floating point operations per second (FLOP/s). The resulting accumulation of computing power going into developing or deploying an AI model can be measured in the quantity of FLOP.[[39](https://arxiv.org/abs/#ax-ref-heim-flop-2023)] This allows for a defined threshold. Government could work closely with AI experts and compute providers to ensure that the threshold is set at a level that captures frontier AI models. Because such models are most likely to emerge at the largest compute scales, the initial threshold could be set at the level of FLOP used to train current foundational models, like GPT-4[[40](https://arxiv.org/abs/#ax-ref-mcaleese-retrospective-2023)] or Claude 2,[[41](https://arxiv.org/abs/#ax-ref-wiggers-anthropics-2023)] thereby also capturing models trained on even more compute. This would also ensure that the burden of compliance with the KYC scheme only falls on operators able to absorb it; GPT-4, for example, is estimated to have cost $50 million to train.[[42](https://arxiv.org/abs/#ax-ref-epoch-key-2023)] This would only capture a handful of models at the time of writing. With training requirements continuing to double every six-to-12 months, we can expect that an increasing number of cloud-trained AI model developers will be subject to KYC.[[20](https://arxiv.org/abs/#ax-ref-sevilla-compute-2022)]
Improvements in algorithmic efficiency over time may result in increased compute efficiency – requiring less compute to achieve the same training results, and potentially necessitating a lower threshold to capture models of concern.[[1](https://arxiv.org/abs/#ax-ref-anderljung-frontier-2023), [43](https://arxiv.org/abs/#ax-ref-tucker-social-2020)] Conversely, advances in regulation or society’s ability to manage AI impacts may decrease the risks associated with advanced AI models, thereby making a higher threshold appropriate.[[1](https://arxiv.org/abs/#ax-ref-anderljung-frontier-2023), [43](https://arxiv.org/abs/#ax-ref-tucker-social-2020)] The threshold should therefore be dynamic and subject to regular review by government and industry. It should be responsive to metrics broader than computing power that influence AI capability and society’s resilience to AI risks. This will also allow for continued refinement as processes mature and the ability to adapt to changing geostrategic conditions and risks.
Applying a specified FLOP threshold offers a feasible path to implementation and does not require cloud providers to access the data or confidential information of their customers. Cloud access to chips is billed by the hour, so the accumulated total FLOP is easily identifiable by the compute provider. The compute provider could then implement KYC checks and enhanced due diligence for any projects seeking to cross that threshold. In many cases, the total amount of compute procured will be specified at the time of entering into contract, but there may also be cases where additional compute is purchased over time, to the point at which a specific vendor crosses the threshold. Compute providers should therefore continuously monitor compute use, and ensure that entities approaching the threshold are funneled into the KYC process before that point is reached.

\#### Regulatory impost is likely to be low, with few stakeholders affected
Given the proposed threshold, only a small number of customers for a small number of US compute providers would be affected. Providers that offer, or use in-house, the most advanced computing power also tend to be the most resourced, such as Microsoft Azure, Google Cloud, NVIDIA, Amazon Web Services (AWS), and Oracle Cloud Infrastructure.[[44](https://arxiv.org/abs/#ax-ref-nvidia-corporation-nvidia-2023)] These factors could help mitigate the risk of an overly costly, burdensome regime (criticisms often directed at KYC in the financial sector). In addition to having the bandwidth to implement KYC, these companies may already be working to control significant AI risks, given their public commitments to ethical and/or responsible AI.[[45](https://arxiv.org/abs/#ax-ref-croak-google-2023)] Microsoft has specifically called for the implementation of a KYC program in their report Governing AI: A Blueprint for the Future,[[6](https://arxiv.org/abs/#ax-ref-smith-how-2023)] and Amazon, Anthropic, Google, Inflection, Meta, Microsoft, OpenAI and NVIDIA, among others, have committed to further safeguards against risky AI.[[16](https://arxiv.org/abs/#ax-ref-shear-pressured-2023)]

  
\### 2.2 Requirements on compute providers – due diligence that identifies risk and implements controls
For AI cloud compute services that possess sufficient computational power, i.e., type and number of AI chips, to surpass the threshold, the scheme would require compute providers to identify and verify the entity and its beneficial owners, and maintain appropriate records. The government could also define ‘high-risk’ profiles, and require compute providers to report such cases, in order to monitor for emerging risks and to inform future controls. The KYC scheme should also be used as a key mechanism to ensure the implementation of rules.
While the KYC scheme provides the mechanism for oversight of advanced AI compute, rules governing US companies in their provision of such compute can be implemented through complementary existing authorities. For example, the US government could update the rules affecting the Export Administration Regulations to prevent the provision of above-threshold compute to entities on the Entity List without a license.[[10](https://arxiv.org/abs/#ax-ref-bureau-of-industry-and-security-commerce-2)] [8](https://arxiv.org/abs/#ax-fn-8)
Beyond export controls, the KYC scheme will allow for the implementation of broader regulations on AI. For example, should the government choose to mandate the voluntary commitments made by leading AI companies – including, for example, having implemented safe-development practices and cybersecurity standards – the KYC checks could also ensure that those accessing advanced AI compute are in compliance before permitting access. In this way, the KYC scheme forms a flexible foundation to ensure oversight of an increasingly sensitive set of technologies.

  Figure 1: Mechanisms of KYC Scheme for compute providers

While we can seek to adapt the model established by the financial sector to the context of compute providers as a starting point (Box 4), consultation and stress-testing with industry stakeholders will be key to developing a workable scheme.
[boxrule=1pt,enhanced jigsaw, sharp corners,pad at break*=1mm,colbacktitle=gray!05,colback=gray!05,colframe=black,coltitle=black,boxrule=0pt,toprule=1pt,leftrule=1pt,bottomrule=0pt, titlerule=1pt,rightrule=1pt,toptitle=1mm,bottomtitle=1mm,fonttitle=,parbox=false,title=Box 4: Possible requirements for compute providers] Building on requirements established in the financial sector, and requiring further consultation with compute providers, KYC requirements for advanced AI cloud compute might include:
- Identifying the entity, including:

- company name

- proof of incorporation

- legal form and status

- address of registered office

- list of directors and senior management

- list of board members

- basic regulating powers (e.g. memorandum and articles of association)

- unique identifier (e.g. tax identification number or equivalent, where applicable).

- Identifying key personnel and all beneficial owners, including:

- full name, including any aliases

- date and place of birth

- nationality

- home address

- government issued identification number.

- Verifying information provided, including through checking domestic and international government registries.

- Providing a high-level overview of the purpose for the use of compute power, and where relevant, investigating details of sublessors of the compute.

[boxrule=1pt,enhanced jigsaw, sharp corners,pad at break*=1mm,colbacktitle=gray!05,colback=gray!05,colframe=black,coltitle=black,boxrule=0pt,toprule=0pt,leftrule=1pt,bottomrule=1pt, titlerule=1pt,rightrule=1pt,toptitle=1mm,bottomtitle=1mm,fonttitle=,parbox=false]
- Conducting ongoing high-level usage monitoring to identify changes or emerging characteristics that could change the assessment:

- changes in contracts that bring entities into the KYC threshold or increase in procured cloud compute that exceeds the expected scope of the stated project

- use of compute different from what would be expected from the stated purpose (e.g. high-level usage patterns that may indicate AI training rather than AI deployment).

- Sharing information with other compute providers to identify and mitigate evasion attempts while preserving privacy.

- Assessing whether an entity would match a defined ‘high-risk’ profile and reporting these cases to the government. Factors that could be considered include:

- the US specially designated nationals and blocked persons list;

- the US Entity List.

- other entities restricted from accessing advanced AI chips under export controls.

- strong links to a country of concern, which may be informed by factors including that:

- the entity or beneficial owner/s are based in a country of concern

- there is evidence that the entity or beneficial owner/s have significant ties to a country of concern

- the entity’s board has significant ties to a country of concern

- director/s or senior management are currently affiliated with research institutions from a country of concern

- IP addresses originate in a country of concern

- evidence of large amounts of data going to/from a country of concern.

- the source of the entity’s capital or funding is not clear (which could potentially lead to requiring the entity to clarify their source or lose compute access).

- entities from countries on the [FATF high-risk jurisdiction list](https://arxiv.orghttps://www.fatf-gafi.org/content/fatf-gafi/en/publications/High-risk-and-other-monitored-jurisdictions/Call-for-action-June-2023.html).

- requests for significantly more compute power than is typically used to develop current cutting-edge models.

- Using KYC to enforce established rules, which may include:

- updated Export Administration Regulations that restrict companies providing above-threshold compute to entities on the Entity List

- seeking confirmation of the entity’s implementation of safe-development practices, including cybersecurity standards (if the voluntary commitments agreed upon between industry and the White House become mandatory).

- Maintaining records on the provision or denial of above-threshold compute to aid in investigations or demonstrate compliance, when needed.

  
\#### 2.2.1 Technical feasibility
It is likely that information pertaining to an entity’s identity and beneficial owners will be readily attainable, given that entities would have such information on hand for their financial institutions. Similarly, checking information against government registries and lists is also feasible, and can draw on existing compliance expertise from the financial sector.
However, while compute providers can collect statements from customers on their planned use of cloud compute, this can be difficult to verify in practice. CSPs often take pride in their ability to offer privacy to their customers, with some providers designing ‘confidential compute’ offerings to make it technically impossible for compute providers to look in at the customer’s data.[[49](https://arxiv.org/abs/#ax-ref-nvidia-corporation-nvidia-nodate)] It is not always clear what compute is being used for, with both the training of foundational models and using AI models for inference requiring intensive compute power.[[50](https://arxiv.org/abs/#ax-ref-heim-compute-2021)] Given the sensitive proprietary information and data involved in cutting-edge AI models, requirements that significantly affect privacy will likely generate significant industry backlash and diminish US industry power. The dispute between the FBI and Apple in 2016 is evidence of the tension between the US government’s security priorities and privacy principles held by the technology sector and general public.[[51](https://arxiv.org/abs/#ax-ref-kharpal-apple-2016)] Further research and collaboration with industry is warranted to identify mechanisms that allow for more effective verification in a way that preserves privacy. A helpful starting point could be focusing on the types of clusters used and how the GPUs are networked, as well as chip hours, which tend to differ according to purpose. This information is known to the compute provider, as these requirements would generally be specified as part of a customer order. Thus, the implementation of the KYC scheme would not require the compute provider to access the underlying code, data, or any system level insights, maintaining appropriate privacy standards.

  
\#### 2.2.2 Mitigating attempts to evade detection
As seen in the case of KYC in the financial sector, malicious actors may seek to evade detection by engaging in “structuring”. In the case of AI, that structuring could involve finding ways to deconstruct compute-intensive projects into smaller, discrete sub-projects that fall below the reporting threshold. Compute providers would be responsible for undertaking their own fraud prevention to ensure that they identify a single entity acting as multiple customers, a measure that is likely already present in existing practices to prevent customers from bypassing terms and conditions. The government would need to work closely with compute providers and the AI industry to monitor how AI development changes in response to the introduction of such schemes and develop responses.
An information-sharing mechanism could be a key tool that compute providers could use to work together to identify actors purchasing disaggregated compute from different companies. However, information-sharing between competitors may be restricted by US Antitrust Laws.[[52](https://arxiv.org/abs/#ax-ref-us-department-of-justice-antitrust-2023)] Close engagement with legal and regulatory experts will be required to carefully design an appropriate scheme, and/or statutory protection could be achieved through legislation. Previous case studies offer some hope: statements from the Department of Justice and Federal Trade Commission noted that sharing information regarding cybersecurity threats was appropriate and a well designed cyber threat sharing scheme would not be likely to raise antitrust concerns.[[53](https://arxiv.org/abs/#ax-ref-federal-trade-commission-ftc-2014)] Privacy preserving techniques, such as Private Set Intersection computation,[[54](https://arxiv.org/abs/#ax-ref-nist-computer-security-research-center-b)] can also be employed effectively in support of information sharing.
Another detection evasion risk could arise from the use of shell companies to obscure an entity’s ultimate owners. The beneficial ownership information reporting requirement, commencing January 2024 in the US and is currently being adopted more broadly by FATF members, could help decrease this risk by requiring companies to disclose information on the people who ultimately own them.[[55](https://arxiv.org/abs/#ax-ref-financial-crimes-enforcement-network-fin)] However, given the strategic and economic importance of advanced AI, it is likely that [malicious] actors will continue to try to obfuscate their identities. Given the relatively small numbers of entities seeking to access significant amounts of advanced AI compute in the near term, a government enforcement team could consider undertaking their own investigations and spot checks on companies.

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-customer-identification)*
++}
---
title: "Common Elements of Frontier AI Safety Policies"
author:
  - "METR"
source_url: "https://metr.org/common-elements"
published: 2025-12-16
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "opus"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description: "Model Evaluation & Threat Research"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Summary ^summary

A number of developers of large foundation models have committed to corporate protocols that lay out how they will evaluate their models for severe risks and mitigate these risks with information security measures, deployment safeguards, and accountability practices. Beginning in September of 2023, several AI companies began to voluntarily publish these protocols. In May of 2024, sixteen companies agreed to do so as part of the Frontier AI Safety Commitments at the AI Seoul Summit, with an additional four companies joining since then. Currently, twelve companies [have published](https://metr.org/fsp) frontier AI safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Naver, Meta, G42, Cohere, Microsoft, Amazon, xAI, and NVIDIA.

This December 2025 version contains references to some developers’ updated frontier AI safety policies. In addition, it also mentions relevant guidance from the EU AI Act’s [General-Purpose AI Code of Practice](https://ec.europa.eu/newsroom/dae/redirection/document/118119) and California’s [Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53).[^note-1]

In our original report from August 2024, we noted how each policy studied made use of _capability thresholds_, such as the potential for AI models to facilitate biological weapons development or cyberattacks, or to engage in autonomous replication or automated AI research and development. The policies also outline commitments to conduct model evaluations assessing whether models are approaching capability thresholds that could enable severe or catastrophic harm.

When these capability thresholds are approached, the policies also prescribe _model weight security_ and _model deployment mitigations_ in response. For models with more concerning capabilities, we noted that in each policy developers commit to securing model weights in order to prevent theft by increasingly sophisticated adversaries. Additionally, they commit to implementing deployment safety measures that would significantly reduce the risk of dangerous AI capabilities being misused and causing serious harm.

The policies also establish _conditions for halting development and deployment_ if the developer’s mitigations are insufficient to manage the risks. To manage these risks effectively, the policies include evaluations designed to _elicit the full capabilities of the model,_ as well as policies defining the _timing and frequency of evaluations_ – which is typically before deployment, during training, and after deployment. Furthermore, all three policies express intentions to explore _accountability mechanisms_, such as oversight by third parties or boards, to monitor policy implementation and potentially assist with evaluations. Finally, the policies may be _updated over time_ as developers gain a deeper understanding of AI risks and refine their evaluation processes.

## Introduction ^introduction

Frontier safety policies are protocols adopted by leading AI companies to ensure that the risks associated with developing and deploying state-of-the-art AI models are kept at an acceptable level.[^note-2] This concept was initially introduced by METR in 2023, and the first such policy was piloted in September of that year. Today, there are twelve existing examples of AI developers publishing frontier AI safety policies:[^note-3]

1.  [Anthropic’s Responsible Scaling Policy, v2.2](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf)
2.  [OpenAI’s Preparedness Framework, Version 2](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf)
3.  [Google DeepMind’s Frontier Safety Framework, Version 3.0](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf)
4.  [Magic’s AGI Readiness Policy](https://magic.dev/agi-readiness-policy)
5.  [Naver’s AI Safety Framework](https://clova.ai/en/tech-blog/en-navers-ai-safety-framework-asf)
6.  [Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/)
7.  [G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf)
8.  [Cohere’s Secure AI Frontier Model Framework](https://cohere.com/security/the-cohere-secure-ai-frontier-model-framework-february-2025.pdf)
9.  [Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf)
10.  [Amazon’s Frontier Model Safety Framework](https://www.amazon.science/publications/amazons-frontier-model-safety-framework)
11.  [xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf)
12.  [NVIDIA’s Frontier AI Risk Assessment](https://images.nvidia.com/content/pdf/NVIDIA-Frontier-AI-Risk-Assessment.pdf)

This page analyzes the common elements between these policies. These components are:

1.  Capability Thresholds: Thresholds at which specific AI capabilities would pose severe risk and require new mitigations.
    
2.  Model Weight Security: Information security measures that will be taken to prevent model weight access by unauthorized actors.
    
3.  Model Deployment Mitigations: Access and model-level measures applied to prevent the unauthorized use of a model’s dangerous capabilities.
    
4.  Conditions for Halting Deployment Plans: Commitments to stop deploying models if the AI capabilities of concern emerge before the appropriate mitigations can be put in place.
    
5.  Conditions for Halting Development Plans: Commitments to halt model development if capabilities of concern emerge before the appropriate mitigations can be put in place.
    
6.  Full Capability Elicitation During Evaluations: Intentions to perform model evaluations in a way that does not underestimate the full capabilities of the model.
    
7.  Timing and Frequency of Evaluations: Concrete timelines outlining when and how often evaluations must be performed – e.g. before deployment, during training, and after deployment.
    
8.  Accountability: Intentions to implement both internal and external oversight mechanisms designed to encourage adequate execution of the frontier safety policy.
    
9.  Updating Policies Over Time: Intentions to update the policy periodically, with protocols detailing how this will be done.
    

Note that despite commonalities, each policy is unique and reflects a distinct approach to AI risk management. Some policies have substantial differences from others. For example, NVIDIA’s and Cohere’s frameworks emphasize domain-specific risks rather than focusing solely on catastrophic risk. Additionally, both xAI and Magic’s safety policies heavily emphasize quantitative benchmarks when assessing their models, unlike most others. By analyzing these common elements with background information and policy excerpts, this report intends to provide insight into current practices in managing severe AI risks.

Table 1: Inclusion of safety elements across frontier AI safety policies.

| Common Element | Presence in Frontier Safety Policies |
| --- | --- |
| [[#^capability-thresholds]] | Present in 9 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Meta, G42, Microsoft, Amazon, xAI. |
| [[#^model-weight-security]] | Present in 11 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Meta, G42, Cohere, Microsoft, Amazon, xAI, NVIDIA. |
| [[#^model-deployment-mitigations]] | Present in 12 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Naver, Meta, G42, Cohere, Microsoft, Amazon, xAI, NVIDIA. |
| [[#^conditions-for-halting-deployment]] | Present in 9 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Naver, Meta, G42, Microsoft, Amazon, xAI. |
| [[#^conditions-for-halting-development]] | Present in 8 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Meta, G42, Microsoft, NVIDIA. |
| [[#^full-capability-elicitation-during]] | Present in 7 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Meta, G42, Microsoft, Amazon. |
| [[#^timing-and-frequency-of]] | Present in 9 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Naver, Meta, G42, Microsoft, Amazon. |
| [[#^accountability]] | Present in 12 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Naver, Meta, G42, Cohere, Microsoft, Amazon, xAI, NVIDIA. |
| [[#^updating-policies-over-time]] | Present in 12 of the existing safety policies: Anthropic, OpenAI, Google DeepMind, Magic, Naver, Meta, G42, Cohere, Microsoft, Amazon, xAI, NVIDIA. |

## Capability Thresholds ^capability-thresholds

**Descriptions of AI capability levels which would pose severe risk and require new robust mitigations.** Most policies outline dangerous capability thresholds which are compared to the results of model evaluations to determine whether they have been crossed.

### Anthropic ^anthropic

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=2), Executive Summary:

_To determine when a model has become sufficiently advanced such that its deployment and security measures should be strengthened, we use the concepts of Capability Thresholds and Required Safeguards. A Capability Threshold tells us_ when _we need to upgrade our protections, and the corresponding Required Safeguards tell us_ what standard _should apply. The Required Safeguards for each Capability Threshold are intended to mitigate risk to acceptable levels._

### OpenAI ^openai

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=4), pages 3–4:

_Our capability elicitation efforts are designed to detect the threshold levels of capability that we have identified as enabling meaningful increases in risk of severe harms. \[…\] We do not deploy models that reach a High capability threshold until the associated risks that they pose are sufficiently minimized. If a model under development reaches a Critical capability threshold, we also require safeguards to sufficiently minimize the associated risks during development, irrespective of deployment plans._ \[…\]

_For each Tracked Category, we develop and maintain a threat model identifying specific risks of severe harms that could arise from the frontier capabilities in that domain and sets corresponding capability thresholds that would lead to a meaningful increase in risk of severe harm. SAG reviews and approves these threat models. Capability thresholds concretely describe things an AI system might be able to help someone do or might be able to do on its own that could meaningfully increase risk of severe harm._

_High capability thresholds mean capabilities that significantly increase existing risk vectors for severe harm. Covered systems that cross this capability threshold are required to have robust and effective safeguards that sufficiently minimize the associated risk of severe harm before they are deployed and appropriate security controls as they are developed. Critical capability thresholds mean capabilities that present a meaningful risk of a qualitatively new threat vector for severe harm with no ready precedent. Critical capabilities require safeguards even during the development of the covered system, irrespective of deployment plans._

### Google DeepMind ^google-deepmind

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=4), page 4:

_The Framework is built around capability thresholds called “Critical Capability Levels (CCLs).” These are capability levels at which, absent mitigation measures, frontier AI models or systems may pose heightened risk of severe harm. CCLs are determined by identifying and analyzing the main foreseeable paths through which a model could result in severe harm: we then define the CCLs as the minimal set of capabilities a model must possess to do so._

_We describe three sets of CCLs: misuse CCLs, machine learning R&D CCLs, and misalignment CCLs._

### Magic ^magic

[Magic’s AGI Readiness Policy:](https://magic.dev/agi-readiness-policy#:~:text=Our%20current%20understanding%20suggests%20at%20least%20four%20threat%20models%20of%20concern%20as%20our%20AI%20systems%20become%20more%20capable%3A)

_Our current understanding suggests at least four threat models of concern as our AI systems become more capable: Cyberoffense, AI R&D, Autonomous Replication and Adaptation (ARA), and potentially Biological Weapons Assistance. \[…\] We describe these threat models along with high-level, illustrative capability levels that would require strong mitigations. We commit to developing detailed dangerous capability evaluations for these threat models based on input from relevant experts, prior to deploying frontier coding models._

### Meta ^meta

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=4), page 4:

_We define our thresholds based on the extent to which frontier AI would uniquely enable the execution of any of the threat scenarios we have identified as being potentially sufficient to produce a catastrophic outcome. If a frontier AI is assessed to have reached the critical risk threshold and cannot be mitigated, we will stop development and implement the measures outlined in Table 1. Our high and moderate risk thresholds are defined in terms of the level of uplift a model provides towards realising a threat scenario._

### G42 ^g42

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=4), page 4:

_Capability thresholds establish points at which an AI model’s functionality requires substantially enhanced safeguards to account for unique risks associated with high stakes capabilities. An initial list of potentially hazardous AI capabilities which G42 will monitor for is:_

-   _Biological Threats: When an AI’s capabilities could facilitate biological security threats, necessitating strict, proactive measures._
-   _Offensive Cybersecurity: When an AI’s capabilities could facilitate cybersecurity threats, necessitating strict, proactive measures._

### Microsoft ^microsoft

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=6), page 5:

_Deeper capability assessment provides a robust indication of whether a model possesses a tracked capability and, if so, whether this capability is at a low, medium, high, or critical risk level, informing decisions about appropriate mitigations and deployment. We use qualitative capability thresholds to guide this classification process as they offer important flexibility across different models and contexts at a time of nascent and evolving understanding of frontier AI risk assessment and management practice._

### Amazon ^amazon

[Amazon’s Frontier Model Safety Framework](https://www.amazon.science/publications/amazons-frontier-model-safety-framework#page=2), page 2:

_Critical Capability Thresholds describe model capabilities within specified risk domains that could cause severe public safety risks. When evaluations demonstrate that an Amazon frontier model has crossed these Critical Capability Thresholds, the development team will apply appropriate safeguards._

### xAI ^xai

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf), page 1:

_This RMF discusses two major categories of AI risk—malicious use and loss of control—and outlines the quantitative thresholds, metrics, and procedures that xAI may utilize to manage and improve the safety of its AI models._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice

[Code of Practice](https://code-of-practice.ai/?section=safety-security#measure-4-1-systemic-risk-acceptance-criteria-and-acceptance-determination), Measure 4.1:

_Signatories will: (1) for each identified systemic risk, at least: (a) define appropriate systemic risk tiers that:_

_I. are defined in terms of model capabilities, and may additionally incorporate model propensities, risk estimates, and/or other suitable metrics;_

_II. are measurable; and_

_III. comprise at least one systemic risk tier that has not been reached by the model;_

### SB 53 ^sb-53

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=industry%20best%20practices.-,\(d\),-A%20large%20frontier), 22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(2) Defining and assessing thresholds used by the large frontier developer to identify and assess whether a frontier model has capabilities that could pose a catastrophic risk, which may include multiple-tiered thresholds._

These capability thresholds are informed by threat models – plausible pathways through which frontier systems may result in catastrophic harm. These threat models provide the context needed to determine capability thresholds. The following threat models are most common among safety policies:

-   Biological weapons assistance: AI models enabling malicious actors to develop biological weapons capable of causing catastrophic harm.
    
-   Cyberoffense: AI models enabling malicious actors to automate or enhance cyberattacks (e.g., on critical societal infrastructure).
    
-   Automated AI research and development: AI models accelerating the pace of AI development by automating research at an expert-human level.
    

Other capabilities that are evaluated by some, but not all, safety policies include:

-   Autonomous replication: AI models with the ability to replicate themselves across servers, manage their own deployment, and generate revenue to sustain their operations.
    
-   Advanced persuasion: AI models enabling malicious actors to conduct robust and large scale manipulation (e.g., malicious election interference).
    
-   Deceptive alignment: AI models that intentionally deceive its developers by appearing aligned with their objectives when monitored, while pursuing the AIs’ own conflicting objectives in secret.
    

Table 2: Covered threat models of each frontier AI safety policy.

| Policy | Covered Threat Models |
| --- | --- |
| [Anthropic’s Responsible Scaling Policy, v2.2](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf) | Chemical, Biological, Radiological, and Nuclear (CBRN) weapons; Autonomous AI Research and Development (AI R&D); Cyber Operations |
| [OpenAI’s Preparedness Framework, Version 2](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf) | Biological and Chemical, Cybersecurity, AI Self-improvement |
| [Google DeepMind’s Frontier Safety Framework, Version 3.0](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf) | CBRN, Cyber, Harmful Manipulation, Machine Learning R&D, Misalignment |
| [Magic’s AGI Readiness Policy](https://magic.dev/agi-readiness-policy) | Cyberoffense, AI R&D, Autonomous Replication and Adaptation, Biological Weapons Assistance |
| [Naver’s AI Safety Framework](https://clova.ai/en/tech-blog/en-navers-ai-safety-framework-asf) | Loss of Control, Misuse (e.g., biochemical weaponization) |
| [Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/) | Cybersecurity, Chemical & Biological risks |
| [G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf) | Biological Threats, Offensive Cybersecurity |
| [Cohere’s Secure AI Frontier Model Framework](https://cohere.com/security/the-cohere-secure-ai-frontier-model-framework-february-2025.pdf) | Malicious Use (malware, child sexual exploitation), Harmful Outputs (outputs that result in an illegal discriminatory outcome, insecure code generation) [^note-4] |
| [Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf) | CBRN weapons, Offensive Cyberoperations, Advanced Autonomy (including AI R&D) |
| [Amazon’s Frontier Model Safety Framework](https://www.amazon.science/publications/amazons-frontier-model-safety-framework) | CBRN Weapons Proliferation, Offensive Cyber Operations, Automated AI R&D |
| [xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf) | Malicious Use (including CBRN and cyber weapons), Loss of Control |
| [NVIDIA’s Frontier AI Risk Assessment](https://images.nvidia.com/content/pdf/NVIDIA-Frontier-AI-Risk-Assessment.pdf) | Potential frontier model risks: Cyber Offense, CBRN, Persuasion and Manipulation, and Unlawful discrimination at-scale. Risk categories dependent on model capabilities, intended use case, and level of autonomy. |

### Biological Weapons Assistance ^biological-weapons-assistance

Current language models are able to provide detailed advice relevant to creating a biological weapon.[^cite-5] [^cite-6] [^cite-7] For instance, OpenAI has found that its o1-preview and o1-mini models reach its “medium risk threshold” due to the models’ ability to assist experts with operational planning of known biological threats [^cite-8] and that pre-mitigation versions of models like deep research are “on the cusp of being able to meaningfully help novices create known biological threats.” [^cite-9] In the future, more advanced models could pose a major biosecurity risk if they enable novices or experts to create biological threats they otherwise would be unable to, or if they can autonomously synthesize a biological threat using a cloud biology lab.[^cite-10] [^cite-11]

In addition to OpenAI, other assessments of AI-enabled biological risk have been conducted by RAND,[^cite-12] Meta,[^cite-13] and Anthropic.[^cite-14] Such assessments can involve working with biology experts to design biorisk questions, and assessing the accuracy of model responses to long-form biorisk questions compared to experts. For example, Anthropic’s evaluations of Claude 3.7 Sonnet assessed the qualitative helpfulness of model access for novices through uplift trials, as well as model performance in automating pathogen acquisition work, and model accuracy on the open-source LAB-Bench benchmark.[^cite-15]

#### Anthropic ^anthropic-2

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=8), page 4:

**CBRN-3:** _The ability to significantly help individuals or groups with basic technical backgrounds (e.g., undergraduate STEM degrees) create/obtain and deploy CBRN weapons._

**CBRN-4:** _The ability to substantially uplift CBRN development capabilities of moderately resourced state programs (with relevant expert teams), such as by novel weapons design, substantially accelerating existing processes, or dramatic reduction in technical barriers._

#### OpenAI ^openai-2

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=6), page 5:

_\[Biological and Chemical – High\] The model can provide meaningful counterfactual assistance (relative to unlimited access to baseline of tools available in 2021) to “novice” actors (anyone with a basic relevant technical background) that enables them to create known biological or chemical threats._

_\[Biological and Chemical – Critical\] The model can enable an expert to develop a highly dangerous novel threat vector (e.g., comparable to a novel CDC Class A biological agent) OR the model can be connected to tools and equipment to complete the full engineering and/or synthesis cycle of a regulated or novel biological threat without human intervention._

#### Google DeepMind ^google-deepmind-2

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=4), page 4:

_CBRN: Risks of models assisting in the development, preparation, and/or execution of a chemical, biological, radiological, or nuclear (“CBRN”) threat._

Page 10:

_CBRN uplift level 1: Provides low to medium resourced actors uplift in reference scenarios resulting in additional \[baseline without generative AI\] expected harm at severe scale._

#### Magic ^magic-2

[Magic’s AGI Readiness Policy](https://magic.dev/agi-readiness-policy#:~:text=The%20model%20provides%20expert%2Dlevel%20guidance%20which%20increases%20the%20accessibility%20or%20severity%20of%20bioweapon%20development.)

Biological Weapons Assistance: _The model provides expert-level guidance which increases the accessibility or severity of bioweapon development. With the model’s help, a non-expert malicious actor can synthesize a viable pandemic agent, or an expert can synthesize a novel biological threat._

#### Meta ^meta-2

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=15), page 15:

_Chemical & Biological Outcome 1: Proliferation of known medium-impact biological and chemical weapons for low and moderate skill actors._

-   _TS.1.1: Small cells of low or moderate skill actors acquire sufficient scientific and operational capabilities to succeed at complex chemical and biological workflows._
-   _TS.1.2: Small cells of low and moderate skill actors can consistently execute relevant and complex wet-lab biological protocols._

_Chemical & Biological Outcome 2: Proliferation of high impact biological weapons, with capabilities equivalent to known agents, for high-skilled actors._

-   _TS.2.1: A well-resourced group of high-skill actors can procure and scale up production of a high-impact biological agent._
-   _TS.2.2: A well-resourced group of high-skill actors can improve an existing medium-impact biological agent to match the capabilities of a high-impact agent._

_Chemical & Biological Outcome 3: Development of high-impact biological weapons with novel capabilities for high-skilled actors._

-   _TS.3.1: A group with extensive resources can meaningfully accelerate the development of a novel biological agent with significant new capabilities._

#### G42 ^g42-2

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=5):

_Biological threats: Enabling an individual with only introductory biology experience in developing a biological weapon, through providing detailed advice, automating biological processes, etc. Or, facilitating the design of novel biological weapons with substantially greater potential for damage. \[…\] Although there is less prior research on evaluating and mitigating risks from biological design tools (BDTs), it is still critical for G42 to develop innovative measures for these tools over time._

#### Microsoft ^microsoft-2

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=4), page 2:

_**Chemical, biological, radiological, and nuclear (CBRN) weapons.** A model’s ability to provide significant capability uplift to an actor seeking to develop and deploy a chemical, biological, radiological, or nuclear weapon._

Page 11:

_CBRN – Low: The model either does not respond to queries related to developing and delivering CBRN attacks or responds with information that is already publicly available._

_CBRN – Medium: The model provides some assistance increasing the ability of an existing expert (PhD level education in related fields) to develop a known CBRN threat._

_CBRN – High: The model provides a meaningful uplift to an expert’s (PhD level education in related fields) ability to develop and deliver a novel CBRN threat. \[Or\] The model provides a meaningful uplift to a medium-skilled actor’s (e.g., STEM education) ability to develop and deliver a known CBRN threat._

_CBRN – Critical: The model provides a meaningful uplift to an expert’s ability to develop a highly dangerous novel threat or significantly lowers the barriers to a low-skilled actor developing and delivering a known CBRN threat._

#### Amazon ^amazon-2

[Amazon’s Frontier Model Safety Framework](https://www.amazon.science/publications/amazons-frontier-model-safety-framework#page=2), page 2:

_Chemical, Biological, Radiological, and Nuclear (CBRN) Weapons Proliferation: CBRN Weapons Proliferation focuses on the risk that a model may be able to guide malicious actors in developing and deploying CBRN weapons. The CBRN Capability Threshold focuses on the potential that a frontier model may provide actors material “uplift” in excess of other publicly available research or existing tools, such as internet search._

_Critical Capability Threshold: AI at this level will be capable of providing expert-level, interactive instruction that provides material uplift (beyond other publicly available research or tools) that would enable a non-subject matter expert to reliably produce and deploy a CBRN weapon._

#### xAI ^xai-2

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf#page=5), page 5, under _Addressing Risks of Malicious Use_:

_Thresholds: We developed an internal benchmark of benign and restricted biology and chemistry related queries in collaboration with SecureBio. Our risk acceptance criteria for system deployment is maintaining an answer rate of less than 1 out of 20 on restricted queries. We plan to add additional thresholds tied to other benchmarks._

Relevant regulatory guidance:

#### Code of Practice ^code-of-practice-2

[Code of Practice](https://code-of-practice.ai/?section=safety-security#appendix-1-4-specified-systemic-risks), Appendix 1.4:

_the following are treated as specified systemic risks for the purpose of systemic risk identification in Measure 2.1, point (2):_

_(1) Chemical, biological, radiological and nuclear: Risks from enabling chemical, biological, radiological, and nuclear (CBRN) attacks or accidents. This includes significantly lowering the barriers to entry for malicious actors, or significantly increasing the potential impact achieved, in the design, development, acquisition, release, distribution, and use of related weapons or materials._

Measure 4.1:

_Signatories will: (1) for each identified systemic risk (pursuant to Measure 2.1), at least: (a) define appropriate systemic risk tiers \[…\]_

#### SB 53 ^sb-53-2

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=frontier%20model%20doing%20any%20of%20the%20following%3A-,\(A\)%C2%A0Providing%20expert%2Dlevel%20assistance%20in%20the%20creation%20or%20release%20of%20a%20chemical%2C%20biological%2C%20radiological%2C%20or%20nuclear%20weapon.,-\(B\)%C2%A0Engaging%20in%20conduct%20with%20no%20meaningful), 22757.11.(c):

_“Catastrophic risk” means a foreseeable and material risk that a frontier developer’s development, storage, use, or deployment of a frontier model will materially contribute to the death of, or serious injury to, more than 50 people or more than one billion dollars ($1,000,000,000) in damage to, or loss of, property arising from a single incident involving a frontier model doing any of the following:_

_(A) Providing expert-level assistance in the creation or release of a chemical, biological, radiological, or nuclear weapon._

22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(2) Defining and assessing thresholds used by the large frontier developer to identify and assess whether a frontier model has capabilities that could pose a catastrophic risk, which may include multiple-tiered thresholds._

### Cyberoffense ^cyberoffense

If models are capable of novel, high-value exploits or attacks on critical infrastructure,[^cite-16] they could cause substantial harm. Present-day models possess an emerging ability to solve cybersecurity challenges and exploit vulnerabilities in websites, open-source software, and networks.[^cite-17] [^cite-18] [^cite-19]

Open-source cyberoffense benchmarks include Cybench,[^cite-20] eyeballvul,[^cite-21] and Google DeepMind CTFs.[^cite-22] Several AI labs have evaluated their models for cyberoffense capabilities and describe results in their model cards or evaluation reports, including Meta,[^cite-23] Anthropic,[^cite-24] OpenAI,[^cite-25] and Google DeepMind.[^cite-26]

#### OpenAI ^openai-3

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=6), pages 5–6:

_\[Cybersecurity – High\]  
The model removes existing bottlenecks to scaling cyber operations including by automating end-to-end cyber operations against reasonably hardened targets OR by automating the discovery and exploitation of operationally relevant vulnerabilities._

_\[Cybersecurity – Critical\]  
A tool-augmented model can identify and develop functional zero-day exploits of all severity levels in many hardened real-world critical systems without human intervention OR model can devise and execute end-to-end novel strategies for cyberattacks against hardened targets given only a high level desired goal._

#### Google DeepMind ^google-deepmind-3

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=4), page 4:

_Cyber: Risks of models assisting in the development, preparation, and/or execution of a cyber attack._

Page 10:

_Cyber uplift level 1: Provides sufficient uplift with high impact cyber attacks for additional expected harm at severe scale._

#### Magic ^magic-3

[Magic’s AGI Readiness Policy:](https://magic.dev/agi-readiness-policy#:~:text=Cyberoffense,-The%20model%20is)

_Cyberoffense: The model is effective at real-world cyberoffense operations. With the model’s help, the cost of discovery of new zero-days or breaking critical infrastructure for a malicious expert actor is reduced by at least 10x; accessing classified and not previously accessible information from a major government; a talented Computer Science undergrad level malicious actor spending 3 months and $1m in compute has a substantial chance of breaking critical infrastructure._

#### Meta ^meta-3

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=14), page 14:

_Cyber Outcome 1: Automated end-to-end compromise of a best-practice protected corporate-scale environment (ex. Fully patched, MFA-protected)._

-   _TS.1.1: End-to-End compromise of a fully patched environment protected by state of the art security best practices. Complete end to end automation of cyber operations to achieve a goal like ransoming or comprehensive theft of a company’s critical IP using a chain of techniques- such as network infiltration, sensitive data discovery, exfiltration, privilege escalation, and lateral movement - for significantly less than cost of services on black market and/or in short amount of time_

_Cyber Outcome 2: Automated discovery and reliable exploitation of critical zero-day vulnerabilities in current popular, security best-practices software before defenders can find and patch them_

-   _TS.2.1: Automated discovery and exploitation of cybervulnerabilities in current popular software using all best practice exploit mitigations that would take human expert teams one month or more, on average, to find, for significantly less than cost of services on black market and/or in a short amount of time._

_Cyber Outcome 3: Widespread economic damage to individuals or corporations via scaled long form fraud and scams._

-   _TS.3.1: Automate end-to-end scam flows (e.g. pig butchering) grooming, infrastructure evasion, multi-platform coordination, and fund movement for significantly less than the cost of services on the black market._

#### G42 ^g42-3

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=6), page 6:

_Offensive cybersecurity: Automating powerful cyber offensive operations against unsecured or secured targets, in a way that could cause critical damage._

#### Microsoft ^microsoft-3

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=13), page 12:

_Offensive Cyberoperations – High: The model provides meaningful uplift to a low-to-medium skilled actor’s ability to create and conduct highly disruptive or destructive cyber-attacks, including on critical infrastructure, for example, through discovering novel zero-day exploit chains or developing complex malware or other tactics, techniques, and procedures._

_Offensive Cyberoperations – Critical: The model provides a meaningful uplift to a low-skilled actor’s ability to identify and exploit major vulnerabilities or enables a well-resourced and expert actor to develop and execute novel and effective strategies against hardened targets._

#### Amazon ^amazon-3

[Amazon’s Frontier Model Safety Framework](https://www.amazon.science/publications/amazons-frontier-model-safety-framework#page=2), page 2:

_Offensive Cyber Operations: Offensive Cyber Operations focuses on risks that would arise from the use of a model by malicious actors to compromise digital systems with the intent to cause harm. The Offensive Cyber Operations Threshold focuses on the potential that a frontier model may provide material uplift in excess of other publicly available research or existing tools, such as internet search._

_Critical Capability Threshold: AI at this level will be capable of providing material uplift (beyond other publicly available research or tools) that would enable a moderately skilled actor (e.g., an individual with undergraduate level understanding of offensive cyber activities or operations) to discover new, high-value vulnerabilities and automate the development and exploitation of such vulnerabilities_

#### xAI ^xai-3

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf#page=5), page 5:

_Cyber Attacks on Critical Infrastructure: Independent third-party assessments of xAI’s current models on realistic offensive cyber tasks requiring identifying and chaining many exploits in sequence indicate that xAI’s models remain below the offensive cyber abilities of a human professional. Thus, xAI currently relies on our basic refusal policy to prevent misuse for cyber attacks. We will continue to re-assess the cyber misuse risks in future releases, and are still working on identifying enforceable critical steps similar to those we have identified for chemical and biological weapons._

One company, Anthropic, discusses cyberoffensive capabilities as a threat model that may be included in future iterations of their safety policy, but which currently requires additional investigation.

#### Anthropic ^anthropic-3

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=9), page 5:

_We will also maintain a list of capabilities that we think require significant investigation and may require stronger safeguards than ASL-2 provides. This group of capabilities could pose serious risks, but the exact Capability Threshold and the Required Safeguards are not clear at present. These capabilities may warrant a higher standard of safeguards, such as the ASL-3 Security or Deployment Standard. However, it is also possible that by the time these capabilities are reached, there will be evidence that such a standard is not necessary (for example, because of the potential use of similar capabilities for defensive purposes). Instead of prespecifying particular thresholds and safeguards today, we will conduct ongoing assessments of the risks with the goal of determining in a future iteration of this policy what the Capability Thresholds and Required Safeguards would be._

_At present, we have identified one such capability:_

_Cyber Operations: The ability to significantly enhance or automate sophisticated destructive cyber attacks, including but not limited to discovering novel zero-day exploit chains, developing complex malware, or orchestrating extensive hard-to-detect network intrusions._

_This will involve engaging with experts in cyber operations to assess the potential for frontier models to both enhance and mitigate cyber threats, and considering the implementation of tiered access controls or phased deployments for models with advanced cyber capabilities. We will conduct either pre- or post-deployment testing, including specialized evaluations. We will document any salient results alongside our Capability Reports._

Relevant regulatory guidance:

#### Code of Practice ^code-of-practice-3

[Code of Practice](https://code-of-practice.ai/?section=safety-security#appendix-1-4-specified-systemic-risks), Appendix 1.4:

_the following are treated as specified systemic risks for the purpose of systemic risk identification in Measure 2.1, point (2): \[…\]_

_(3) Cyber offence: Risks from enabling large-scale sophisticated cyber-attacks, including on critical systems (e.g. critical infrastructure). This includes significantly lowering the barriers to entry for malicious actors, or significantly increasing the potential impact achieved in offensive cyber operations, e.g. through automated vulnerability discovery, exploit generation, operational use, and attack scaling._

Measure 4.1:

_Signatories will: (1) for each identified systemic risk (pursuant to Measure 2.1), at least: (a) define appropriate systemic risk tiers \[…\]_

#### SB 53 ^sb-53-3

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=frontier%20model%20doing%20any%20of%20the%20following%3A-,\(A\)%C2%A0Providing%20expert%2Dlevel%20assistance%20in%20the%20creation%20or%20release%20of%20a%20chemical%2C%20biological%2C%20radiological%2C%20or%20nuclear%20weapon.,-\(B\)%C2%A0Engaging%20in%20conduct%20with%20no%20meaningful), 22757.11.(c):

_“Catastrophic risk” means a foreseeable and material risk that a frontier developer’s development, storage, use, or deployment of a frontier model will materially contribute to the death of, or serious injury to, more than 50 people or more than one billion dollars ($1,000,000,000) in damage to, or loss of, property arising from a single incident involving a frontier model doing any of the following:_

_(B) Engaging in conduct with no meaningful human oversight, intervention, or supervision that is either a cyberattack or, if the conduct had been committed by a human, would constitute the crime of murder, assault, extortion, or theft, including theft by false pretense._

22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(2) Defining and assessing thresholds used by the large frontier developer to identify and assess whether a frontier model has capabilities that could pose a catastrophic risk, which may include multiple-tiered thresholds._

### Automated AI Research and Development ^automated-ai-research-and

Large language models can contribute to various aspects of AI research, such as generating synthetic pretraining [^cite-27] [^cite-28] and fine-tuning data,[^cite-29] [^cite-30] [^cite-31] designing reward functions [^cite-32], and general-purpose programming.[^cite-33] [^cite-34] In the future, models may be able to substantially automate AI research and development (AI R&D) for frontier AI [^cite-35]. This development could lead to a growth or proliferation in AI capabilities, including other capabilities of concern, that outpaces ability to ensure sufficient oversight and safeguards.[^cite-36]

The National Security Memorandum on AI describes “automat\[ing\] development and deployment of other models” (with cyber, biological or chemical weapon, or autonomous malicious capabilities) as one of the AI capabilities relevant to national security that the U.S. AI Safety Institute must conduct tests for.[^cite-37] Open-source benchmarks such as MLE-bench [^cite-38] and RE-Bench [^cite-39] can help measure the capabilities of language model agents to automate machine learning engineering tasks.

#### Anthropic ^anthropic-4

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=8), page 4:

_AI R&D-4: The ability to fully automate the work of an entry-level, remote-only Researcher at Anthropic._

_AI R&D 5: The ability to cause dramatic acceleration in the rate of effective scaling._

#### OpenAI ^openai-4

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=7), page 6:

_\[AI Self-improvement - High\]_ _The model’s impact is equivalent to giving every OpenAI researcher a highly performant mid-career research engineer assistant, relative to those researchers’ 2024 baseline._

_\[AI Self-improvement - Critical\]_ _The model is capable of recursively self improving (i.e., fully automated AI R&D), defined as either (leading indicator) a superhuman research-scientist agent OR (lagging indicator) causing a generational model improvement (e.g., from OpenAI o1 to OpenAI o3) in 1/5th the wall-clock time of equivalent progress in 2024 (e.g., sped up to just 4 weeks) sustainably for several months._

#### Google DeepMind ^google-deepmind-4

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=4), page 4:

_Machine Learning R&D: Risks of the misuse of models capable of accelerating the rate of AI progress, the result of which could be the unsafe attainment or proliferation of other powerful AI models._

Pages 13–14:

_ML R&D acceleration level 1: Has been used to accelerate AI development, resulting in AI progress substantially accelerating from historical rates._

_ML R&D automation level 1: Can fully automate the work of any team of researchers at Google focused on improving AI capabilities, with approximately comparable all-inclusive costs._

#### Magic ^magic-4

[Magic’s AGI Readiness Policy:](https://magic.dev/agi-readiness-policy#:~:text=breaking%20critical%20infrastructure.-,AI%20R%26D,-The%20model%20facilitates)

AI R&D: _The model facilitates a dramatic acceleration in the rate of effective compute scaling or can effectively replace high-level machine learning researchers. Such capabilities may enable it to contribute to the unsafe proliferation or enhancement of other dangerous AI capabilities._

#### Microsoft ^microsoft-4

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=14), page 13:

_Advanced Autonomy – High: The model can autonomously complete a range of generalist tasks equivalent to multiple days’ worth of generalist human labor and appropriately correct for complex error conditions, or autonomously complete the vast majority of coding tasks at the level of expert humans._

_Advanced Autonomy – Critical: The model can fully automate the AI R&D pipeline at a fraction of human labor costs, majorly accelerating AI R&D._

#### Amazon ^amazon-4

[Amazon’s Frontier Model Safety Framework](https://cdn.amazon.science/a7/7c/8bdade5c4eda9168f3dee6434fff/pc-amazon-frontier-model-safety-framework-2-7-final-2-9.pdf#page=2), page 2:

_Automated AI R&D: Automating AI R&D processes could accelerate discovery and development of AI capabilities that will be critical for solving global challenges. However, Automated AI R&D could also accelerate the development of models that pose enhanced CBRN, Offensive Cybersecurity, or other severe risks._

_Critical Capability Threshold: AI at this level will be capable of replacing human researchers and fully automating the research, development, and deployment of frontier models that will pose severe risk such as accelerating the development of enhanced CBRN weapons and offensive cybersecurity methods._

One company’s safety policy recognizes automated AI R&D as an important capability, however, instead of classifying it as a threat model, it is mentioned as a form of elicitation that must be considered when assessing other capabilities.

#### Meta ^meta-4

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=17), page 17:

_Our evaluations \[…\] account for enabling capabilities, such as automated AI R&D, that might increase the potential for enhancements to model capabilities._

Relevant regulatory guidance:

#### Code of Practice ^code-of-practice-4

[Code of Practice](https://code-of-practice.ai/?section=safety-security#appendix-1-4-specified-systemic-risks), Appendix 1.4:

_the following are treated as specified systemic risks for the purpose of systemic risk identification in Measure 2.1, point (2): \[…\]_

_(2) Loss of control: Risks from humans losing the ability to reliably direct, modify, or shut down a model. Such risks may emerge from misalignment with human intent or values, self-reasoning, self-replication, self-improvement, deception, resistance to goal modification, power-seeking behaviour, or autonomously creating or improving AI models or AI systems._

Measure 4.1:

_Signatories will: (1) for each identified systemic risk (pursuant to Measure 2.1), at least: (a) define appropriate systemic risk tiers \[…\]_

### Additional Threat Models ^additional-threat-models

Some other threat models – autonomous replication, harmful manipulation, misalignment, and loss of control – are highlighted in at least one existing frontier AI safety policy.

#### Google DeepMind ^google-deepmind-5

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=4), page 4:

_Harmful Manipulation: Risks of models with high manipulative capabilities potentially being misused in ways that could reasonably result in large scale harm._

Pages 10–11

_Harmful manipulation level 1 (exploratory): Possesses manipulative capabilities sufficient to enable it to systematically and substantially change beliefs and behavior in identified high stakes contexts over the course of interactions with the model, reasonably resulting in additional expected harm at severe scale._

Page 4:

_For misalignment risk, we outline an exploratory approach that focuses on detecting when models might develop a baseline instrumental reasoning ability at which they have the potential to undermine human control, assuming no additional mitigations were applied._

Page 15:

_\[Illustrative\] Instrumental Reasoning Level 1: The instrumental reasoning abilities of the model enable enough situational awareness (ability to work out and use relevant details of its deployment setting) and stealth (ability to circumvent basic oversight mechanisms) such that, absent additional mitigations, we cannot rule out the model significantly undermining human control._

_\[Illustrative\] Instrumental Reasoning Level 2: The instrumental reasoning abilities of the model enable enough situational awareness and stealth that, even when relevant model outputs (including, e.g. scratchpads) are being monitored, we cannot detect or rule out the risk of a model significantly undermining human control._

#### Magic ^magic-5

[Magic’s AGI Readiness Policy:](https://magic.dev/agi-readiness-policy#:~:text=dangerous%20AI%20capabilities.-,Autonomous%20Replication%20and%20Adaptation,-If%20given%20access) Autonomous Replication and Adaptation:

_If given access to its own weights and prompted to do so, the AI model could autonomously maintain its own operation executing cybercrime and using the proceeds to create arbitrarily many replicas of itself._

#### xAI ^xai-4

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf#page=6), under Addressing Risks of Loss of Control, pages 6–7:

_The following are example benchmarks that xAI may use to evaluate its models for concerning propensities relevant to loss of control risks:_

-   _Model Alignment between Statements and Knowledge (MASK): Frontier LLMs may lie when under pressure; and increasing model scale may increase accuracy but may not increase honesty. MASK is a benchmark to evaluate honesty in LLMs by comparing the model’s response when asked neutrally versus when pressured to lie._
-   _Sycophancy: A tendency toward excessive flattery or other sycophantic behavior has been observed in some production AI systems, possibly resulting from directly optimizing against human preferences. xAI uses an evaluation setting initially introduced by Anthropic to quantify the degree to which this behavior manifests in regular conversational contexts._ \[…\]

_Thresholds: Our risk acceptance criteria for system deployment is maintaining a dishonesty rate of less than 1 out of 2 on MASK. We plan to add additional thresholds tied to other benchmarks._

One company, OpenAI, discusses additional thread models that may be included in future iterations of their safety policy, but which currently requires additional investigation.

#### OpenAI ^openai-5

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=7), pages 6–7:

_There are also some areas of frontier capability that do not meet the criteria to be Tracked Categories, but where we believe work is required now in order to prepare to effectively address risks of severe harms in the future. These capabilities either need more research and threat modeling before they can be rigorously measured, or do not cause direct risks themselves but may need to be monitored because further advancement in this capability could undermine the safeguards we rely on to mitigate existing Tracked Category risks. We call these Research Categories \[…\]_ _Research Category:_

-   _Long-range Autonomy: ability for a model to execute a long-horizon sequence of actions sufficient to realize a “High” threat model (e.g., a cyberattack) without being directed by a human (including successful social engineering attacks when needed)_
-   _Sandbagging: ability and propensity to respond to safety or capability evaluations in a way that significantly diverges from performance under real conditions, undermining the validity of such evaluations._
-   _Autonomous Replication and Adaptation: ability to survive, replicate, resist shutdown, acquire resources to maintain and scale its own operations, and commit illegal activities that collectively constitute causing severe harm (whether when explicitly instructed, or at its own initiative), without also utilizing capabilities tracked in other Tracked Categories._
-   _Undermining Safeguards: ability and propensity for the model to act to undermine safeguards placed on it, including e.g., deception, colluding with oversight models, sabotaging safeguards over time such as by embedding vulnerabilities in safeguards code, etc._
-   _Nuclear and Radiological: ability to meaningfully counterfactually enable the creation of a radiological threat or enable or significantly accelerate the development of or access to a nuclear threat while remaining undetected._

Relevant regulatory guidance:

#### Code of Practice ^code-of-practice-5

[Code of Practice](https://code-of-practice.ai/?section=safety-security#appendix-1-4-specified-systemic-risks), Appendix 1.4:

_the following are treated as specified systemic risks for the purpose of systemic risk identification in Measure 2.1, point (2):_ \[…\]

_(4) Harmful manipulation: Risks from enabling the strategic distortion of human behaviour or beliefs by targeting large populations or high-stakes decision-makers through persuasion, deception, or personalised targeting. This includes significantly enhancing capabilities for persuasion, deception, and personalised targeting, particularly through multi-turn interactions and where individuals are unaware of or cannot reasonably detect such influence. Such capabilities could undermine democratic processes and fundamental rights, including exploitation based on protected characteristics._

Measure 4.1:

_Signatories will: (1) for each identified systemic risk (pursuant to Measure 2.1), at least: (a) define appropriate systemic risk tiers \[…\]_

#### SB 53 ^sb-53-4

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=frontier%20model%20doing%20any%20of%20the%20following%3A-,\(A\)%C2%A0Providing%20expert%2Dlevel%20assistance%20in%20the%20creation%20or%20release%20of%20a%20chemical%2C%20biological%2C%20radiological%2C%20or%20nuclear%20weapon.,-\(B\)%C2%A0Engaging%20in%20conduct%20with%20no%20meaningful), 22757.11.(c):

_“Catastrophic risk” means a foreseeable and material risk that a frontier developer’s development, storage, use, or deployment of a frontier model will materially contribute to the death of, or serious injury to, more than 50 people or more than one billion dollars ($1,000,000,000) in damage to, or loss of, property arising from a single incident involving a frontier model doing any of the following:_

_(B) Engaging in conduct with no meaningful human oversight, intervention, or supervision that is either a cyberattack or, if the conduct had been committed by a human, would constitute the crime of murder, assault, extortion, or theft, including theft by false pretense._

22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(2) Defining and assessing thresholds used by the large frontier developer to identify and assess whether a frontier model has capabilities that could pose a catastrophic risk, which may include multiple-tiered thresholds._

## Model Weight Security ^model-weight-security

**Measures that will be taken to prevent model weight access by unauthorized actors**. If malicious actors steal the weights of models with capabilities of concern, they could misuse those models to cause severe harm. Therefore, as models develop increasing capabilities of concern, progressively stronger information security measures are recommended to prevent theft and unintentional release of model weights. Security risks can come from insiders, or they can come from external adversaries of varying sophistication, from opportunistic actors to top-priority nation-state operations.[^cite-40] [^note-41]

### Anthropic ^anthropic-5

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=12), pages 8–10:

_When a model must meet the ASL-3 Security Standard, we will evaluate whether the measures we have implemented make us highly protected against most attackers’ attempts at stealing model weights._

_We consider the following groups in scope: hacktivists, criminal hacker groups, organized cybercrime groups, terrorist organizations, corporate espionage teams, internal employees, and state-sponsored programs that use broad-based and non-targeted techniques (i.e., not novel attack chains). \[…\]_

_To make the required showing, we will need to satisfy the following criteria:_

1.  _Threat modeling: Follow risk governance best practices, such as use of the MITRE ATT&CK Framework to establish the relationship between the identified threats, sensitive assets, attack vectors and, in doing so, sufficiently capture the resulting risks that must be addressed to protect model weights from theft attempts. As part of this requirement, we should specify our plans for revising the resulting threat model over time._
2.  _Security frameworks: Align to and, as needed, extend industry-standard security frameworks for addressing identified risks, such as disclosure of sensitive information, tampering with accounts and assets, and unauthorized elevation of privileges with the appropriate controls. \[…\]_
3.  _Audits: Develop plans to (1) audit and assess the design and implementation of the security program and (2) share these findings (and updates on any remediation efforts) with management on an appropriate cadence. We expect this to include independent validation of threat modeling and risk assessment results; a sampling-based audit of the operating effectiveness of the defined controls; periodic, broadly scoped, and independent testing with expert red-teamers who are industry-renowned and have been recognized in competitive challenges._
4.  _Third-party environments: Document how all relevant models will meet the criteria above, even if they are deployed in a third-party partner’s environment that may have a different set of safeguards._

### OpenAI ^openai-6

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=13), page 12:

_Models that have reached or are forecasted to reach Critical capability in a Tracked Category present severe dangers and should be treated with extreme caution. Such models require additional safeguards (safety and security controls) during development, regardless of whether or when they are externally deployed. We do not currently possess any models that have Critical levels of capability, and we expect to further update this Preparedness Framework before reaching such a level with any model._

Page 20:

_Robust security practices and controls are essential to mitigating risks associated with the deployment of models reaching High capability thresholds. Our security approach integrates industry best practices with OpenAI-specific innovations tailored to manage the unique threats posed by frontier AI technologies \[…\] We will require the following practices for High capability models:_

-   _Security Threat Modeling and Risk Management \[…\]_
-   _Defense in Depth \[…\]_
-   _Access Management \[…\]_
-   _Secure Development and Supply Chain \[…\]_
-   _Operational Security \[…\]_
-   _Auditing and Transparency \[…\]_

### Google DeepMind ^google-deepmind-6

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=8), page 8:

_Here, we use security levels that indicate goals/principles in line with the RAND framework.[^note-42] Because AI security is an area of active research, we expect the concrete measures implemented to reach each level of security to evolve substantially._

Pages 10–14 (adapted):

| _Critical capability level_ | _Recommended security level_ |
| --- | --- |
| _CBRN uplift 1_ | _Security level 2_ |
| _Cyber uplift level 1_ | _Security level 2_ |
| _Harmful manipulation level 1_ | _Security level 2_ |
| _ML R&D acceleration level 1_ | _Security level 3_ |
| _ML R&D automation level 1_ | _We recommend Security Level 4 for this capability threshold, but emphasize that this must be taken on by the frontier AI field as a whole._ |

### Magic ^magic-6

[Magic’s AGI Readiness Policy:](https://magic.dev/agi-readiness-policy#:~:text=As%20we%20develop%20more%20capable%20models)

_As we develop more capable models, it will become especially important to harden our security against attempts to extract our models’ weights and other resource-intensive outputs of our training process._

_The effectiveness of our deployment mitigations – like training models to refuse harmful requests, continuously monitoring a model’s outputs for misuse, and other proprietary interventions – is generally contingent on the models being securely in our possession. Accordingly, we will place particular emphasis on implementing information security measures._

_We will implement the following information security measures, based on recommendations in RAND’s Securing Artificial Intelligence Model Weights report, if and when we observe evidence that our models are proficient at our Covered Threat Models._

-   _Hardening model weight and code security: implementing robust security controls to prevent unauthorized access to our model weights. These controls will make it extremely difficult for non-state actors, and eventually state-level actors, to steal our model weights._
-   _Internal compartmentalization: implementing strong access controls and strong authentication mechanisms to limit unauthorized access to LLM training environments, code, and parameters._

### Meta ^meta-5

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=13), page 13:

_Security Mitigations – Critical: Access is strictly limited to a small number of experts, alongside security protections to prevent hacking or exfiltration insofar as is technically feasible and commercially practicable._

_Security Mitigations – High: Access is limited to a core research team, alongside security protections to prevent hacking or exfiltration._

_Security Mitigations – Moderate: Security measures will depend on the release strategy._

### G42 ^g42-4

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=9), page 9–11:

_G42’s Security Mitigation Levels are a set of levels, mapped to the Frontier Capability Thresholds, describing escalating information security measures. These protect against the theft of model weights, model inversion, and sensitive data, as models reach higher levels of capability and risk. …_

_Security level 1 – Suitable for models with minimal hazardous capabilities. No novel mitigations required on the basis of catastrophically dangerous capabilities._

_Security level 2 – Intermediate safeguards for models with capabilities requiring controlled access, providing an extra layer of caution. The model should be secured such that it would be highly unlikely that a malicious individual or organization (state sponsored, organized crime, terrorist, etc.) could obtain the model weights or access sensitive data._

_Security level 3 – Advanced safeguards for models approaching hazardous capabilities that could uplift state programs. Model weight security should be strong enough to resist even concerted attempts, with support from state programs, to steal model weights or key algorithmic secrets._

_Security level 4 – Maximum safeguards. Security strong enough to resist concerted attempts with support from state programs to steal model weights._

### Cohere ^cohere

[Cohere’s Secure AI Frontier Model Framework](https://cohere.com/security/the-cohere-secure-ai-frontier-model-framework-february-2025.pdf#page=9), page 9:

_Core security controls: Our core controls across network security, endpoint security, identity and access management, data security, and others are designed to protect Cohere from cyber risks that could expose our models, systems, or sensitive data, such as malware, phishing, denial-of-service, insider threats, and vulnerabilities._

_These controls include:_

-   _Advanced perimeter security controls and real-time threat prevention and monitoring_
-   _Secure, risk-based defaults and internal reviews_
-   _Advanced endpoint detection and response across our cloud infrastructure and distributed devices_
-   _Strict access controls, including multifactor authentication, role-based access control, and just-in-time access, across and within our environment to protect against insider and external threats (internal access to unreleased model weights is even more strenuously restricted)_
-   _“Secure Product Lifecycle” controls, including security requirements gathering, security risk assessment, security architecture and product reviews, security threat modeling, security scanning, code reviews, penetration testing, and bug bounty programs._

### Microsoft ^microsoft-5

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=7), page 6:

_Securing frontier models is an essential precursor to safe and trustworthy use and the first priority of this framework. Any model that triggers leading indicator assessment is subject to robust baseline security protection. Security safeguards are then scaled up depending on the model’s pre-mitigation scores, with more robust measures applied to models with High and Critical risk levels._

Page 7:

_**Models posing high-risk** on one or more tracked capability will be subject to security measures protective against most cybercrime groups and insider threats. Examples of requirements for models having a high-risk score include:_

-   _Restricted access, including access control list hygiene and limiting access to weights of the most capable models other than for core research and for safety and security teams. Strong perimeter and access control are applied as part of preventing unauthorized access._
-   _Defense in depth across the lifecycle, applying multiple layers of security controls that provide redundancy in case some controls fail. Model weights are encrypted._
-   _Advanced security red teaming, using third parties where appropriate, to reasonably simulate relevant threat actors seeking to steal the model weights so that security safeguards are robust._

_**Models posing critical risk** on one or more tracked capability are subject to the highest level of security safeguards. Further work and investment are needed to mature security practices so that they can be effective in securing highly advanced models with critical risk levels that may emerge in the future. Appropriate requirements for critical risk level models will likely include the use of high-trust developer environments, such as hardened tamper-resistant workstations with enhanced logging, and physical bandwidth limitations between devices or networks containing weights and the outside world._

### Amazon ^amazon-5

[Amazon’s Frontier Model Safety Framework](https://cdn.amazon.science/a7/7c/8bdade5c4eda9168f3dee6434fff/pc-amazon-frontier-model-safety-framework-2-7-final-2-9.pdf#page=3), page 3:

_Upon determining that an Amazon model has reached a Critical Capability Threshold, we will implement a set of Safety Measures and Security Measures to prevent elicitation of the critical capability identified and to protect against inappropriate access risks. \[…\] Security Measures are designed to prevent unauthorized access to model weights or guardrails implemented as part of the Safety Measures, which could enable a malicious actor to remove or bypass existing guardrails to exceed Critical Capability Thresholds._

Page 4:

_We describe our current practices in greater detail in Appendix A. Below are some key elements of our existing security approach that we use to safeguard our frontier models:_

-   _**Secure compute and networking environments.** The Trainium or GPU-enabled compute nodes used for AI model training and inference within the AWS environment are based on the EC2 Nitro system, which provides confidential computing properties natively across the fleet. Compute clusters run in isolated Virtual Private Cloud network environments. All development of frontier models that occurs in AWS accounts meets the required security bar for careful configuration and management. These accounts include both identity-based and network-based boundaries, perimeters, and firewalls, as well as enhanced logging of security-relevant metadata such as netflow data and DNS logs._
-   _**Advanced data protection capabilities.** For models developed on AWS, model data and intermediate checkpoint results in compute clusters are stored using AES-256 GCM encryption with data encryption keys backed by the FIPS 140-2 Level 3 certified AWS Key Management Service. Software engineers and data scientists must be members of the correct Critical Permission Groups and authenticate with hardware security tokens from enterprise-managed endpoints in order to access or operate on any model systems or data. Any local, temporary copies of model data used for experiments and testing are also fully encrypted in transit and at rest._
-   _**Security monitoring, operations, and response.** Amazon’s automated threat intelligence and defense systems detect and mitigate millions of threats each day. These systems are backed by human experts for threat intelligence, security operations, and security response. Threat sharing with other providers and government agencies provides collective defense and response._

### xAI ^xai-5

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf#page=8), page 8:

_xAI has implemented appropriate information security standards sufficient to prevent its critical model information from being stolen by a motivated non-state actor. To prevent the unauthorized proliferation of advanced AI systems, we also implement security measures against the large-scale extraction and distillation of reasoning traces, which have been shown to be highly effective in quickly reproducing advanced capabilities while expending far fewer computational resources than the original AI system._

### NVIDIA ^nvidia

[NVIDIA’s Frontier AI Risk Assessment](https://images.nvidia.com/content/pdf/NVIDIA-Frontier-AI-Risk-Assessment.pdf#page=12), page 12:

_When a model shows capabilities of frontier AI models pre deployment we will initially restrict access to model weights to essential personnel and ensure rigorous security protocols are in place._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-6

[Code of Practice](https://code-of-practice.ai/?section=safety-security#commitment-6-security-mitigations-2), Commitment 6:

_Signatories commit to implementing an adequate level of cybersecurity protection for their models and their physical infrastructure along the entire model lifecycle, as specified in the Measures for this Commitment, to ensure the systemic risks stemming from their models that could arise from unauthorised releases, unauthorised access, and/or model theft are acceptable (pursuant to Commitment 4)._

### SB 53 ^sb-53-5

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=\(7\)%C2%A0Cybersecurity%20practices%20to%20secure%20unreleased%20model%20weights%20from%20unauthorized%20modification%20or%20transfer%20by%20internal%20or%20external%20parties.), 22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(7) Cybersecurity practices to secure unreleased model weights from unauthorized modification or transfer by internal or external parties._

## Model Deployment Mitigations ^model-deployment-mitigations

**Access and model-level measures applied to prevent the unauthorized use of a model’s dangerous capabilities.** Developers can train models to decline harmful requests [^cite-43] or employ additional techniques [^cite-44] [^cite-45] including adversarial training [^cite-46] [^cite-47] and output monitoring.[^cite-48] For models with greater levels of harmful capabilities, these safety measures may need to pass certain thresholds of robustness, including expert and automated red-teaming.[^note-49] [^cite-50] [^cite-51] [^note-52] [^cite-53] These protective measures should scale proportionally with model capabilities, as more powerful AI systems will inevitably attract more sophisticated attempts to circumvent restrictions or exploit their advanced abilities. Note that deployment mitigations are only effective as long as the model weights are securely within the possession of the developer.[^cite-54] [^cite-55]

### Anthropic ^anthropic-6

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=12), page 8:

_When a model must meet the ASL-3 Deployment Standard, we will evaluate whether the measures we have implemented make us robust to persistent attempts to misuse the capability in question. To make the required showing, we will need to satisfy the following criteria:_

1.  _Threat modeling: Make a compelling case that the set of threats and the vectors through which an adversary could catastrophically misuse the deployed system have been sufficiently mapped out, and will commit to revising as necessary over time._
2.  _Defense in depth: Use a “defense in depth” approach by building a series of defensive layers, each designed to catch misuse attempts that might pass through previous barriers. As an example, this might entail achieving a high overall recall rate using harm refusal techniques. This is an area of active research, and new technologies may be added when ready._
3.  _Red-teaming: Conduct red-teaming that demonstrates that threat actors with realistic access levels and resources are highly unlikely to be able to consistently elicit information from any generally accessible systems that greatly increases their ability to cause catastrophic harm relative to other available tools._
4.  _Rapid remediation: Show that any compromises of the deployed system, such as jailbreaks or other attack pathways, will be identified and remediated promptly enough to prevent the overall system from meaningfully increasing an adversary’s ability to cause catastrophic harm. Example techniques could include rapid vulnerability patching, the ability to escalate to law enforcement when appropriate, and any necessary retention of logs for these activities._
5.  _Monitoring: Prespecify empirical evidence that would show the system is operating within the accepted risk range and define a process for reviewing the system’s performance on a reasonable cadence. Process examples include monitoring responses to jailbreak bounties, doing historical analysis or background monitoring, and any necessary retention of logs for these activities._
6.  _Trusted users: Establish criteria for determining when it may be appropriate to share a version of the model with reduced safeguards with trusted users. In addition, demonstrate that an alternative set of controls will provide equivalent levels of assurance. This could include a sufficient combination of user vetting, secure access controls, monitoring, log retention, and incident response protocols._
7.  _Third-party environments: Document how all relevant models will meet the criteria above, even if they are deployed in a third-party partner’s environment that may have a different set of safeguards._

### OpenAI ^openai-7

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=11), page 10:

_Each capability threshold has a corresponding class of risk-specific safeguard guidelines under the Preparedness Framework. We use the following process to select safeguards for a deployment:_

-   _We first identify the plausible ways in which the associated risk of severe harm can come to fruition in the proposed deployment._
-   _For each of those, we then identify specific safeguards that either exist or should be implemented that would address the risk._
-   _For each identified safeguard, we identify methods to measure their efficacy and an efficacy threshold._

Page 12:

_Models that have reached or are forecasted to reach Critical capability in a Tracked Category present severe dangers and should be treated with extreme caution. Such models require additional safeguards (safety and security controls) during development, regardless of whether or when they are externally deployed._

### Google DeepMind ^google-deepmind-7

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=8), pages 8–9:

_Deployment Mitigations – Misuse:_  
_The following deployment mitigation process will be applied to models reaching a CCL, allowing for iterative and flexible tailoring of mitigations to each risk and use case._

1.  _Development and assessment of mitigations: safeguards and an accompanying safety case are developed by iterating on the following:_
    -   _Developing and improving a suite of safeguards targeting the capability, which may include measures such as safety post-training, monitoring and analysis, account moderation, jailbreak detection and patching, user verification, and bug bounties._
    -   _Assessing the robustness of these mitigations against the risk posed through testing (e.g. automated evaluations, red teaming) and threat modeling research. The assessment takes the form of a safety case, and could take into account factors such as: \[…\]_
2.  _Pre-deployment review of safety case: external deployments of a model take place only after the appropriate governance function determines the safety case regarding each CCL the model has reached to be adequate. In particular, we will deem deployment mitigations adequate if the evidence suggests that for the CCLs the model has reached, the increase in likelihood of severe harm has been reduced to an acceptable level._
3.  _Post-deployment processes: our safety cases and mitigations may be updated if deemed necessary by post-market monitoring. Material updates to a safety case will be submitted to the appropriate governance function for review._ _This process is designed to ensure that residual risk remains at acceptable levels: evidence of efficacy collected during development and testing, as well as expert-driven estimates of other parameters, will enable us to assess residual risk and to detect substantial changes that invalidate our risk assessment._

Pages 12–13:

_Deployment Mitigations – Machine Learning R&D:_

1.  _Development and assessment of mitigations: safeguards and an accompanying safety case are developed by iterating on the following: \[…\]_
2.  _Pre-deployment review of safety case: external deployments and large scale internal deployments of a model take place only after the appropriate governance function determines the safety case regarding each CCL the model has reached to be adequate. In particular, we will deem deployment mitigations adequate if the evidence suggests that for the CCLs the model has reached, the increase in likelihood of severe harm has been reduced to an acceptable level._
3.  _Post-deployment processes: our safety cases and mitigations may be updated if deemed necessary by post-market monitoring. Material updates to a safety case will be submitted to the appropriate governance function for review._

### Magic ^magic-7

[Magic’s AGI Readiness Policy:](https://magic.dev/agi-readiness-policy#:~:text=code%2C%20and%20parameters.-,Deployment%20Mitigations,-Deployment%20mitigations%20aim)

_Deployment mitigations aim to disable dangerous capabilities of our models once detected. These mitigations will be required in order to make our models available for wide use, if the evaluations for our Covered Threat Models trigger._

_The following are two examples of deployment mitigations we might employ:_

-   _Harm refusal: we will train our models to robustly refuse requests for aid in causing harm – for example, requests to generate cybersecurity exploits._
-   _Output monitoring: we may implement techniques such as output safety classifiers to prevent serious misuse of models. Automated detection may also apply for internal usage within Magic._

_A full set of mitigations will be detailed publicly by the time we complete our policy implementation, as described in this document’s introduction. Other categories of mitigations beyond the two illustrative examples listed above likely will be required._

### Naver ^naver

[Naver’s AI Safety Framework:](https://clova.ai/en/tech-blog/en-navers-ai-safety-framework-asf)

_Once AI systems are evaluated and their risks identified according to the two standards, we must implement appropriate guardrails around them. We should only deploy AI systems if those safeguards have proven effective in mitigating risks and keep an eye on the systems even after deployment through continuous monitoring. In theory, there may be cases where AI systems are used for special purposes and require safety guardrails in place, in which case AI systems should not be deployed._

### Meta ^meta-6

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=13), page 13:

_Measures – Critical: Successful execution of a threat scenario does not necessarily mean that the catastrophic outcome is realizable. If a model appears to uniquely enable the execution of a threat scenario we will pause development while we investigate whether barriers to realizing the catastrophic outcome remain. Our process is as follows:_

1.  Implement mitigations to reduce risk to moderate levels, to the extent possible
2.  Conduct a threat modelling exercise to determine whether other barriers to realising the catastrophic outcome exist
3.  If additional barriers exist, update our Framework with the new threat scenarios, and re-run our assessments to assign the model to the appropriate risk threshold
4.  If additional barriers do not exist, continue to investigate mitigations, and do not further develop the model until such a time as adequate mitigations have been identified.

_Measures – High: Implement mitigations to reduce risk to moderate levels_

_Measures – Moderate: Mitigations will depend on the results of evaluations and the release strategy._

### G42 ^g42-5

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=7), pages 7–9:

_G42’s Deployment Mitigation Levels are a set of levels, mapped to the Frontier Capability Thresholds, that describe escalating mitigation measures for products deployed externally. These protect against misuse, including through jailbreaking, as models reach higher levels of capability and risk. These measures address specifically the goal of denying bad actors access to dangerous capabilities under the terms of intended deployment for our models, i.e. presuming that our development environment’s information security has not been violated._

_Deployment Mitigation Level 1 – Foundational safeguards, applied to models with minimal hazardous capabilities. No novel mitigations required on the basis of catastrophically dangerous capabilities_

_Deployment Mitigation Level 2 – Intermediate safeguards for models with capabilities requiring focused monitoring. Even a determined actor should not be able to reliably elicit CBRN weapons advice or use the model to automate powerful cyberattacks including malware generation as well as misinformation campaigns, fraud material, illicit video/text/image generation via jailbreak techniques overriding the internal guardrails and supplemental security products._

_Deployment Mitigation Level 3 – Advanced safeguards for models approaching significant capability thresholds. Deployment safety should be strong enough to resist sophisticated attempts to jailbreak or otherwise misuse the model._

_Deployment Mitigation Level 4 – Maximum safeguards, designed for high-stakes frontier models with critical functions. Deployment safety should be strong enough to resist even concerted attempts, with support from state programs, to jailbreak or otherwise misuse the model._

### Cohere ^cohere-2

[Cohere’s Secure AI Frontier Model Framework](https://cohere.com/security/the-cohere-secure-ai-frontier-model-framework-february-2025.pdf#page=13), page 13, row “Deployment and maintenance” under column “Key Mitigations We Apply”:

-   _Blocklists, custom classifiers, and prompt injection guard filters, and human review to detect and intercept attempts to create unsafe outputs \[…\]_
-   _Safety classifiers and human review to detect and intercept attempts to create unsafe outputs_
-   _Human-interpretable explanation of outputs_

### Microsoft ^microsoft-6

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=8), page 7–8:

_We apply state-of-the-art safety mitigations tailored to observed risks so that the model’s risk level remains at medium once mitigations have been applied. We will continue to contribute to research and best-practice development, including through organizations such as the Frontier Model Forum, and to share and leverage best practice mitigations as part of this framework. Examples of safety mitigations we utilize include:_

-   _**Harm refusal**, applying state-of-the-art harm refusal techniques so that a model does not return harmful information relating to a tracked capability at a high or critical level to a user…_
-   _**Deployment guidance**, with clear documentation setting out the capabilities and limitations of the model, including factors affecting safe and secure use and details of prohibited uses…_
-   _**Monitoring and remediation**, including abuse monitoring in line with Microsoft’s Product Terms and provide channels for employees, customers, and external parties to report concerns about model performance, including serious incidents that may pose public safety and national security risks. We apply mitigations and remediation as appropriate to address identified concerns and adjust customer documentation as needed. Other forms of monitoring, including for example, automated monitoring in chain-of-thought outputs, are also utilized as appropriate…_
-   _**Phased release, trusted users, and usage studies**, as appropriate for models demonstrating novel or advanced capabilities. This can involve sharing the model initially with defined groups of trusted users with a view to better understanding model performance while in use before general availability \[…\]_

### Amazon ^amazon-6

[Amazon’s Frontier Model Safety Framework](https://www.amazon.science/publications/amazons-frontier-model-safety-framework), page 3–4:

_Upon determining that an Amazon model has reached a Critical Capability Threshold, we will implement a set of Safety Measures and Security Measures to prevent elicitation of the critical capability identified and to protect against inappropriate access risks. Safety Measures are designed to prevent the elicitation of the observed Critical Capabilities following deployment of the model. \[…\] Examples of current safety mitigations include:_

-   _**Training Data Safeguards:** We implement a rigorous data review process across various model training stages that aims to identify and redact data that could give rise to unsafe behaviors._
-   _**Alignment Training:** We implement automated methods to ensure we meet the design objectives for each of Amazon’s responsible AI dimensions, including safety and security. Both supervised fine tuning (SFT) and learning with human feedback (LHF) are used to align models. Training data for these alignment techniques are sourced in collaboration with domain experts to ensure alignment of the model towards the desired behaviors._
-   _**Harmful Content Guardrails:** Application of runtime input and output moderation systems serve as a first and last line of defense and enable rapid response to newly identified threats or gaps in model alignment. Input moderation systems detect and either block or safely modify prompts that contain malicious, insecure or illegal material, or attempt to bypass the core model alignment (e.g. prompt injection, jail-breaking). Output moderation systems ensure that the content adheres to our Amazon Responsible AI objectives by blocking or safely modifying violating outputs._
-   _**Fine-tuning Safeguards:** Models are trained in a manner that makes them resilient to malicious customer fine-tuning efforts that could undermine initial Responsible AI alignment training by the Amazon team._
-   _**Incident Response Protocols:** Incident escalation and response pathways enable rapid remediation of reported AI safety incidents, including jailbreak remediation._

### xAI ^xai-6

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf), pages 1–2:

_**Approach to Mitigating Risks of Malicious Use**: Alongside comprehensive evaluations measuring dual-use capabilities, our mitigation strategy for malicious use risks is to identify critical steps in major risk scenarios and implement redundant layers of safeguards in our models to inhibit user progress in advancing through such steps. xAI works with a variety of governmental bodies, non-governmental organizations, private testing firms, industry peers, and academic researchers to identify such inhibiting steps, commonly referred to as bottlenecks, and implement commensurate safeguards to mitigate a model’s ability to assist in accelerating a bad actor’s progress through them. Model safeguards leverage a broad variety of techniques, including standard software systems and state-of-the-art AI capabilities, to detect and block potential abuses._

Page 7:

_xAI trains its models to be honest and have values conducive to controllability, such as recognizing and obeying an instruction hierarchy. In addition, using a high level instruction called a “system prompt”, xAI directly instructs its models to not deceive or deliberately mislead the user._

### NVIDIA ^nvidia-2

[NVIDIA’s Frontier AI Risk Assessment](https://images.nvidia.com/content/pdf/NVIDIA-Frontier-AI-Risk-Assessment.pdf#page=12), page 12:

_Measures will also be in place to restrict at-will fine tuning of frontier AI models without safeguards in NeMo customizer, reducing the options to retrain a model on data related to dangerous tasks or to reduce how often the model refuses potentially dangerous requests._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-7

[Code of Practice](https://code-of-practice.ai/?section=safety-security#commitment-5-safety-mitigations-2), Commitment 5:

_Signatories commit to implementing appropriate safety mitigations along the entire model lifecycle, as specified in the Measure for this Commitment, to ensure the systemic risks stemming from the model are acceptable (pursuant to Commitment 4)._

Measure 5.1:

_Signatories will implement safety mitigations that are appropriate, including sufficiently robust under adversarial pressure (e.g. fine-tuning attacks or jailbreaking), taking into account the model’s release and distribution strategy._

### SB 53 ^sb-53-6

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=\(2\)%C2%A0Defining%20and,of%20catastrophic%20risks.), 22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(2) Defining and assessing thresholds used by the large frontier developer to identify and assess whether a frontier model has capabilities that could pose a catastrophic risk, which may include multiple-tiered thresholds._

_(3) Applying mitigations to address the potential for catastrophic risks based on the results of assessments undertaken pursuant to paragraph (2)._

_(4) Reviewing assessments and adequacy of mitigations as part of the decision to deploy a frontier model or use it extensively internally._

_(5) Using third parties to assess the potential for catastrophic risks and the effectiveness of mitigations of catastrophic risks._

## Conditions for Halting Deployment Plans ^conditions-for-halting-deployment

**Commitments to stop deploying AI models if capabilities of concern emerge before the adequate mitigations can be put in place.** Deploying models with concerning capabilities would be unsafe if broad user access enables catastrophic misuse. This can happen when mitigations are disproportionately weak compared to the model’s dangerous capabilities—making them vulnerable to circumvention by determined actors—or when the specific types of mitigations needed to address novel risks are entirely absent. By refusing to deploy systems without the appropriate safeguards, companies reduce the likelihood that third parties can exploit these harmful capabilities.

### Anthropic ^anthropic-7

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=15), page 11:

_In any scenario where we determine that a model requires ASL-3 Required Safeguards but we are unable to implement them immediately, we will act promptly to reduce interim risk to acceptable levels until the ASL-3 Required Safeguards are in place:_

-   _**Interim Measures:** The CEO and Responsible Scaling Officer may approve the use of interim measures that provide the same level of assurance as the relevant ASL-3 Standard but are faster or simpler to implement. In the deployment context, such measures might include blocking model responses, downgrading to a less-capable model in a particular domain, or increasing the sensitivity of automated monitoring. In the security context, an example of such a measure would be storing the model weights in a single-purpose, isolated network that meets the ASL-3 Standard.\[…\]_
    
-   _**Stronger Restrictions:** In the unlikely event that we cannot implement interim measures to adequately mitigate risk, we will impose stronger restrictions. In the deployment context, we will de-deploy the model and replace it with a model that falls below the Capability Threshold. Once the ASL-3 Deployment Standard can be met, the model may be re-deployed. In the security context, we will delete model weights. \[…\]_
-   _**Monitoring pretraining:** We will not train models with comparable or greater capabilities to the one that requires the ASL-3 Security Standard. This is achieved by monitoring the capabilities of the model in pretraining and comparing them against the given model. \[…\]_

### OpenAI ^openai-8

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=12), page 11:

_SAG can find the safeguards do not sufficiently minimize the risk of severe harm and recommend potential alternative deployment conditions or additional or more effective safeguards that would sufficiently minimize the risk._

Page 15:

_OpenAI Leadership, i.e., the CEO or a person designated by them, is responsible for:_

-   _Making all final decisions, including accepting any residual risks and making deployment go/no-go decisions, informed by SAG’s recommendations._

### Google DeepMind ^google-deepmind-8

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=6), pages 6–7:

_A model for which the risk assessment indicates a misuse CCL has been reached will be deemed to pose an acceptable level of risk for further development or deployment, if, for example:_

-   _We assess that the deployment mitigations have brought the risk of severe harm to an appropriate level proportionate to the risk, based on considerations such as whether the risk has been reduced to an acceptable level by mitigations, the scope of the deployment, \[…\]_
-   _Security mitigations have been applied to the model weights reaching the recommended security level stated below, or we otherwise assess that the level of security applied is adequate, e.g. if they match or exceed the level of security applied to other models with similar capabilities or risk profiles, or we assess that the benefits of the open release of model weights outweigh the risks._

_A model for which the risk assessment indicates a machine learning R&D CCL has been reached will be deemed to pose an acceptable level of risk for further development or deployment, if, for example:_

-   _We assess that the deployment mitigations have brought the risk of severe harm to an appropriate level proportionate to the risk, based on considerations such as whether the risk has been reduced to an acceptable level by mitigations, and information pertaining to model propensities and the severity of related events._
-   _Security mitigations have been applied to the model weights reaching the recommended security level stated below, or we otherwise assess that the level of security applied is adequate, e.g. if they match or exceed the level of security applied to other models with similar capabilities or risk profiles, or we assess that the benefits of the open release of model weights outweigh the risks._

### Naver ^naver-2

[Naver’s AI Safety Framework](https://clova.ai/en/tech-blog/en-navers-ai-safety-framework-asf):

_Once AI systems are evaluated and their risks identified according to the two standards, we must implement appropriate guardrails around them. We should only deploy AI systems if those safeguards have proven effective in mitigating risks and keep an eye on the systems even after deployment through continuous monitoring. In theory, there may be cases where AI systems are used for special purposes and require safety guardrails in place, in which case AI systems should not be deployed._

### Meta ^meta-7

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=12), pages 12–13:

_If a frontier AI is assessed to have reached the critical risk threshold and cannot be mitigated, we will stop development and implement the measures outlined in Table 1._

_High risk threshold – Do not release. The model provides significant uplift towards execution of a threat scenario (i.e. significantly enhances performance on key capabilities or tasks needed to produce a catastrophic outcome) but does not enable execution of any threat scenario that has been identified as potentially sufficient to produce a catastrophic outcome._

### G42 ^g42-6

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=5), page 5:

_If a necessary Deployment Mitigation Level cannot be achieved, then the model’s deployment must be restricted; if a necessary Security Mitigation Level cannot be achieved, then further capabilities development of the model must be paused._

### Microsoft ^microsoft-7

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=9), page 8:

_If, during the implementation of this framework, we identify a risk we cannot sufficiently mitigate, we will pause development and deployment until the point at which mitigation practices evolve to meet the risk._

### Amazon ^amazon-7

[Amazon’s Frontier Model Safety Framework](https://www.amazon.science/publications/amazons-frontier-model-safety-framework), page 1:

_At its core, this Framework reflects our commitment that we will not deploy frontier AI models developed by Amazon that exceed specified risk thresholds without appropriate safeguards in place._

Page 3:

_We will evaluate models following the application of these safeguards to ensure that they adequately mitigate the risks associated with the Critical Capability Threshold. In the event these evaluations reveal that an Amazon frontier model meets or exceeds a Critical Capability Threshold and our Safety and Security Measures are unable to appropriately mitigate the risks (e.g. by preventing reliable elicitation of the capability by malicious actors), we will not deploy the model until we have identified and implemented appropriate additional safeguards._

### xAI ^xai-7

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf#page=5), page 5:

_We developed an internal benchmark of benign and restricted biology and chemistry related queries in collaboration with SecureBio. Our risk acceptance criteria for system deployment is maintaining an answer rate of less than 1 out of 20 on restricted queries. We plan to add additional thresholds tied to other benchmarks._

Page 7:

_Our risk acceptance criteria for system deployment is maintaining a dishonesty rate of less than 1 out of 2 on MASK._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-8

[Code of Practice](https://code-of-practice.ai/?section=safety-security#measure-4-2-proceeding-or-not-proceeding-based-on-systemic-risk-acceptance-determination), Measure 4.2:

_Signatories will only proceed with the development, the making available on the market, and/or the use of the model, if the systemic risks stemming from the model are determined to be acceptable (pursuant to Measure 4.1)._

_If the systemic risks stemming from the model are not determined to be acceptable or are reasonably foreseeable to be soon not determined to be acceptable (pursuant to Measure 4.1), Signatories will take appropriate measures to ensure the systemic risks stemming from the model are and will remain acceptable prior to proceeding._

### SB 53 ^sb-53-7

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=\(2\)%C2%A0Defining%20and,of%20catastrophic%20risks.), 22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(4) Reviewing assessments and adequacy of mitigations as part of the decision to deploy a frontier model or use it extensively internally._

## Conditions for Halting Development Plans ^conditions-for-halting-development

**Commitments to halt model development if the capabilities of concern emerge before the adequate mitigations can be put in place.** Continuing to train a model becomes hazardous if it’s developing concerning capabilities while simultaneously lacking adequate security measures to protect its weights from theft. Furthermore, certain AI risks like deceptive alignment can only be detected and addressed during the training process itself, making it particularly dangerous to proceed without proper safeguards in place.

### Anthropic ^anthropic-8

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=15), page 11:

_In any scenario where we determine that a model requires ASL-3 Required Safeguards but we are unable to implement them immediately, we will act promptly to reduce interim risk to acceptable levels until the ASL-3 Required Safeguards are in place:_ \[…\]

-   _**Monitoring Pre-training:** We will not train models with comparable or greater capabilities to the one that requires the ASL-3 Security Standard. This is achieved by monitoring the capabilities of the model in pretraining and comparing them against the given model. If the pretraining model’s capabilities are comparable or greater, we will pause training until we have implemented the ASL-3 Security Standard and established it is sufficient for the model._

### OpenAI ^openai-9

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=6), pages 5–6, Table 1’s safeguard guidelines for _Critical capability thresholds_:

-   _Until we have specified safeguards and security controls that would meet a Critical standard, halt further development_

### Google DeepMind ^google-deepmind-9

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=6), pages 6–7:

_A model for which the risk assessment indicates a misuse CCL has been reached will be deemed to pose an acceptable level of risk for further development or deployment, if, for example:_

-   _We assess that the deployment mitigations have brought the risk of severe harm to an appropriate level proportionate to the risk, based on considerations such as whether the risk has been reduced to an acceptable level by mitigations, the scope of the deployment, \[…\]_
-   _Security mitigations have been applied to the model weights reaching the recommended security level stated below, or we otherwise assess that the level of security applied is adequate, e.g. if they match or exceed the level of security applied to other models with similar capabilities or risk profiles, or we assess that the benefits of the open release of model weights outweigh the risks._

_A model for which the risk assessment indicates a machine learning R&D CCL has been reached will be deemed to pose an acceptable level of risk for further development or deployment, if, for example:_

-   _We assess that the deployment mitigations have brought the risk of severe harm to an appropriate level proportionate to the risk, based on considerations such as whether the risk has been reduced to an acceptable level by mitigations, and information pertaining to model propensities and the severity of related events._
-   _Security mitigations have been applied to the model weights reaching the recommended security level stated below, or we otherwise assess that the level of security applied is adequate, e.g. if they match or exceed the level of security applied to other models with similar capabilities or risk profiles, or we assess that the benefits of the open release of model weights outweigh the risks._

### Magic ^magic-8

[Magic’s AGI Readiness Policy](https://magic.dev/agi-readiness-policy#:~:text=If%20we%20have%20not%20developed%20adequate%20dangerous%20capability%20evaluations):

_If we have not developed adequate dangerous capability evaluations by the time these benchmark thresholds are exceeded, we will halt further model development until our dangerous capability evaluations are ready._

\[…\]

_In cases where said risk for any threat model passes a ‘red-line’, we will adopt safety measures outlined in the Threat Mitigations section, which include delaying or pausing development in the worst case until the dangerous capability detected has been mitigated or contained._

### Meta ^meta-8

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=12), pages 12–13:

_If a frontier AI is assessed to have reached the critical risk threshold and cannot be mitigated, we will stop development and implement the measures outlined in Table 1._

-   _**Critical risk threshold – Stop development.** The model would uniquely enable the execution of at least one of the threat scenarios that have been identified as potentially sufficient to produce a catastrophic outcome and that risk cannot be mitigated in the proposed deployment context._

### G42 ^g42-7

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=5), page 5:

_If a necessary Deployment Mitigation Level cannot be achieved, then the model’s deployment must be restricted; if a necessary Security Mitigation Level cannot be achieved, then further capabilities development of the model must be paused._

### Microsoft ^microsoft-8

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=9), page 8:

_If, during the implementation of this framework, we identify a risk we cannot sufficiently mitigate, we will pause development and deployment until the point at which mitigation practices evolve to meet the risk._

### NVIDIA ^nvidia-3

[NVIDIA’s Frontier AI Risk Assessment](https://images.nvidia.com/content/pdf/NVIDIA-Frontier-AI-Risk-Assessment.pdf#page=14), page 14:

_Key to this approach is early detection of potential risks, coupled with mechanisms to pause development when necessary._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-9

[Code of Practice](https://code-of-practice.ai/?section=safety-security#measure-4-2-proceeding-or-not-proceeding-based-on-systemic-risk-acceptance-determination), Measure 4.2:

_Signatories will only proceed with the development, the making available on the market, and/or the use of the model, if the systemic risks stemming from the model are determined to be acceptable (pursuant to Measure 4.1)._

_If the systemic risks stemming from the model are not determined to be acceptable or are reasonably foreseeable to be soon not determined to be acceptable (pursuant to Measure 4.1), Signatories will take appropriate measures to ensure the systemic risks stemming from the model are and will remain acceptable prior to proceeding._

## Full Capability Elicitation during Evaluations ^full-capability-elicitation-during

**Intentions to perform evaluations in a way that elicits the full capabilities of the model.** It is generally challenging to comprehensively explore a model’s capabilities, even in a specific domain such as cyberoffense. Without dedicated efforts to elicit full capabilities,[^cite-56] evaluations may significantly underestimate the extent to which a model has capabilities of concern.[^cite-57] This is because model capabilities can be substantially improved through post-training enhancements such as fine-tuning, prompt engineering, or agent scaffolding.[^cite-58] For example, if the model is fine-tuned to refuse harmful requests, it is possible that the harmful capability could still be accessed through jailbreaking prompts discovered later. Model capabilities can additionally be improved through tool usage, such as the ability to execute code [^cite-59] or search the web.

Capability elicitation can involve a variety of techniques. One is to fine-tune the model to not refuse harmful requests, to reduce the chance that refusals lead to underestimation of capabilities. Another is to fine-tune the model for improved performance on relevant tasks. Evaluations that incorporate fine-tuning help to anticipate potential risks if model weights are stolen. Such evaluations are especially relevant if end users can fine-tune the model or if the developer improves fine-tuning later.[^cite-60] When evaluating AI agents, capabilities can be influenced by the quality of prompt engineering, tools afforded to the model, and usage of inference-time compute.[^cite-61]

### Anthropic ^anthropic-9

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=10), page 6:

_Elicitation: Demonstrate that, when given enough resources to extrapolate to realistic attackers, researchers cannot elicit sufficiently useful results from the model on the relevant tasks. We should assume that jailbreaks and model weight theft are possibilities, and therefore perform testing on models without safety mechanisms (such as harmlessness training) that could obscure these capabilities. We will also consider the possible performance increase from using resources that a realistic attacker would have access to, such as scaffolding, finetuning, and expert prompting. At minimum, we will perform basic finetuning for instruction following, tool use, minimizing refusal rates._

### OpenAI ^openai-10

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=9), page 8:

_Our evaluations are intended to approximate the full capability that the adversary contemplated by our threat model could extract from the deployment candidate model, including by using the highest-capability tier of system settings, using a version of the model that has a negligible rate of safety-based refusals on our Tracked Category capability evaluations (which may require a separate model variant), and with the best presently-available scaffolds. These measures are taken to approximate the high end of expected elicitation by threat actors attempting to misuse the model, and should be tailored depending on the level of expected access (e.g., doing finetuning if the weights will be released). Nonetheless, given the continuous progress in model scaffolding and elicitation techniques, we regard any one-time capability elicitation in a frontier model as a lower bound, rather than a ceiling, on capabilities that may emerge in real world use and misuse._

### Google DeepMind ^google-deepmind-10

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=5), page 5:

_In our evaluations, we seek to equip the model with appropriate scaffolding and other augmentations to make it more likely that we are also assessing the capabilities of systems that will likely be produced with the model._

### Meta ^meta-9

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=17), page 17:

_Our evaluations are designed to account for the deployment context of the model. This includes assessing whether risks will remain within defined thresholds once a model is deployed or released using the target release approach. For example, to help ensure that we are appropriately assessing the risk, we prepare the asset – the version of the model that we will test – in a way that seeks to account for the tools and scaffolding in the current ecosystem that a particular threat actor might seek to leverage to enhance the model’s capabilities. We also account for enabling capabilities, such as automated AI R&D, that might increase the potential for enhancements to model capabilities._

_We may take into account monetary costs as well as a threat actor’s ability to overcome other barriers to misuse relevant to our threat scenarios such as access to compute, restricted materials, or lab facilities._

### G42 ^g42-8

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=5), page 5–6:

_Such evaluations will incorporate capability elicitation – techniques such as prompt engineering, fine-tuning, and agentic tool usage – to optimize performance, overcome model refusals, and avoid underestimating model capabilities. Models created to generate output in a specific language, such as Arabic or Hindi, may be tested in those languages._

### Microsoft ^microsoft-9

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=7), page 6:

_Capability elicitation: Evaluations include concerted efforts at capability elicitation, i.e., applying capability enhancing techniques to advance understanding of a model’s full capabilities. This includes fine-tuning the model to improve performance on the capability being evaluated or ensuring the model is prompted and scaffolded to enhance the tracked capability—for example, by using a multi-agent setup, leveraging prompt optimization, or connecting the model to whichever tools and plugins will maximize its performance. Resources applied to elicitation should be extrapolated out to those available to actors in threat models relevant to each tracked capability._

### Amazon ^amazon-8

[Amazon’s Frontier Model Safety Framework](https://cdn.amazon.science/a7/7c/8bdade5c4eda9168f3dee6434fff/pc-amazon-frontier-model-safety-framework-2-7-final-2-9.pdf#page=3), page 3:

_We will re-evaluate deployed models prior to any major updates that could meaningfully enhance underlying capabilities. Our evaluation process includes “maximal capability evaluations” to determine the outer bounds of our models’ Critical Capabilities._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-10

[Code of Practice](https://code-of-practice.ai/?section=safety-security#appendix-3-2-model-elicitation), Appendix 3.2:

_Signatories will ensure that the model evaluations are conducted with at least a state-of-the-art level of model elicitation that elicits the model’s capabilities, propensities, affordances, and/or effects, by using at least state-of-the-art techniques that:_

_(1) minimise the risk of under-elicitation; and_

_(2) minimise the risk of model deception during model evaluations (e.g. sandbagging);_

_such as by adapting test-time compute, rate limits, scaffolding, and tools, and conducting fine-tuning and prompt engineering._

## Timing and Frequency of Evaluations ^timing-and-frequency-of

**Concrete timelines outlining when and how often evaluations must be performed – before deployment, during training, and after deployment.** Evaluations are important throughout the model development lifecycle. Evaluations can inform whether it is safe to deploy a model externally or internally, based on its capabilities for harm and the robustness of safety measures. Merely possessing a model can also pose risk if it has hazardous capabilities and the information security measures are insufficient to prevent theft of model weights.[^cite-62]

### Anthropic ^anthropic-10

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=9), page 5:

_We will routinely test models to determine whether their capabilities fall sufficiently far below the Capability Thresholds such that we are confident that the ASL-2 Standard remains appropriate. We will first conduct preliminary assessments (on both new and existing models, as needed) to determine whether a more comprehensive evaluation is needed. The purpose of this preliminary assessment is to identify whether the model is notably more capable than the last model that underwent a comprehensive assessment._

_The term “notably more capable” is operationalized as at least one of the following:_

1.  _The model is notably more performant on automated tests in risk-relevant domains (defined as 4x or more in Effective Compute 4)._
2.  _Six months’ worth of finetuning and other capability elicitation methods have accumulated. This is measured in calendar time, since we do not yet have a metric to estimate the impact of these improvements more precisely._

_In addition, the Responsible Scaling Officer may in their discretion determine that a comprehensive assessment is warranted. If a new or existing model is below the “notably more capable” standard, no further testing is necessary._

### OpenAI ^openai-11

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=10), page 9:

_The Preparedness Framework applies to any new or updated deployment that has a plausible chance of reaching a capability threshold whose corresponding risks are not addressed by an existing Safeguards Report. Examples of such covered deployments are:_

-   _every frontier model (e.g., OpenAI o1 or OpenAI o3) that we plan to deploy externally_
-   _any agentic system (including significant agents deployed only internally) that represents a substantial increase in the capability frontier_
-   _any significant change in the deployment conditions of an existing model (e.g., enabling finetuning, releasing weights, or significant new features) that makes the existing Capabilities Report or Safeguards Report no longer reasonably applicable_
-   _incremental updates or distilled models with unexpectedly significant increases in capability._ _If justified by our forecasts and threat models as potentially posing a severe risk during development and prior to external deployment, we will select an appropriate checkpoint during development to be covered by the Preparedness Framework._

### Google DeepMind ^google-deepmind-11

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=4), pages 4–5:

_For each risk domain, we conduct aspects of our risk assessment at various moments throughout the model development process, both before and after deployment. We conduct a risk assessment for the first external deployment of a new frontier AI model. For subsequent versions of the model, we conduct a further risk assessment if the model has meaningful new capabilities or a material increase in performance, until the model is retired or we deploy a more capable model. The reason for this is because a material change in the model’s capabilities may mean that the risk profile of the model has changed or the justification for why the risks stemming from the model are acceptable has been materially undermined._

_To identify meaningful new capabilities or material increases in performance, we conduct model capability evaluations, including our automated benchmarks. These evaluations are primarily aimed at understanding the capabilities of the model and may be triggered, for example, upon the completion of a pre-training or post-training run, on various candidates of a model version._

### Naver ^naver-3

[Naver’s AI Safety Framework](https://clova.ai/en/tech-blog/en-navers-ai-safety-framework-asf#:~:text=Our%20goal%20is%20to%20have%20AI%20systems%20evaluated%20quarterly):

_Our goal is to have AI systems evaluated quarterly to mitigate loss of control risks, but when performance is seen to have increased six times, they will be assessed even before the three-month term is up. Because the performance of AI systems usually increases as their size gets bigger, the amount of computing can serve as an indicator when measuring capabilities._

### Meta ^meta-10

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=16), pages 16–17:

_We conduct an initial set of evaluations on a first checkpoint to assess capabilities across the risk domains \[…\]_

_If we identify that a frontier AI does exhibit sufficient performance on these capabilities, we will conduct further evaluations to establish whether the frontier AI would enable execution of the threat scenario._

### Amazon ^amazon-9

[Amazon’s Frontier Model Safety Framework](https://cdn.amazon.science/a7/7c/8bdade5c4eda9168f3dee6434fff/pc-amazon-frontier-model-safety-framework-2-7-final-2-9.pdf#page=3), page 3:

_We conduct evaluations on an ongoing basis, including during training and prior to deployment of new frontier models. We will re-evaluate deployed models prior to any major updates that could meaningfully enhance underlying capabilities._

Some companies that have not yet trained and deployed frontier models have adopted policies committing to executing intensive model evaluations for dangerous capabilities only after models approach frontier performance.

### Magic ^magic-9

[Magic’s AGI Readiness Policy](https://magic.dev/agi-readiness-policy#:~:text=Based%20on%20these%20scores):

_Based on these scores, when, at the end of a training run, our models exceed a threshold of 50% accuracy on LiveCodeBench, we will trigger our commitment to incorporate a full system of dangerous capabilities evaluations and planned mitigations into our AGI Readiness Policy, prior to substantial further model development, or publicly deploying such models._

\[…\]

_Prior to publicly deploying models that exceed the current frontier of coding performance, we will evaluate them for dangerous capabilities and ensure that we have sufficient protective measures in place to continue development and deployment in a safe manner._

### G42 ^g42-9

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=4), page 4:

_G42 will conduct evaluations throughout the model lifecycle to assess whether our models are approaching Frontier Capability Thresholds. At the outset, G42 will conduct preliminary evaluations based on open-source and in-house benchmarks relevant to a hazardous capability. If a given G42 model achieves lower performance on relevant open-source benchmarks than a model produced by an outside organization that has been evaluated to be definitively below the capability threshold, then such G42 model will be presumed to be below the capability threshold._

_If the preliminary evaluations cannot rule out proficiency in hazardous capabilities, then we will conduct in-depth evaluations that study the capability in more detail to assess whether the Frontier Capability Threshold has been met._

### Microsoft ^microsoft-10

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=6), page 5:

_The leading indicator assessment is run during pre-training, after pre-training is complete, and prior to deployment to ensure a comprehensive assessment as to whether a model warrants deeper inspection \[…\] Models in scope of this framework will undergo leading indicator assessment at least every six months to assess progress in post-training capability enhancements, including fine-tuning and tooling. Any model demonstrating frontier capabilities is then subject to a deeper capability assessment \[which\] provides a robust indication of whether a model possesses a tracked capability and, if so, whether this capability is at a low, medium, high, or critical risk level, informing decisions about appropriate mitigations and deployment._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-11

[Code of Practice](https://code-of-practice.ai/?section=safety-security#measure-1-2-implementing-the-framework), Measure 1.2:

_Along the entire model lifecycle, Signatories will continuously: (1) assess the systemic risks stemming from the model by:_

_(a) conducting lighter-touch model evaluations that need not adhere to Appendix 3 (e.g. automated evaluations) at appropriate trigger points defined in terms of, e.g. time, training compute, development stages, user access, inference compute, and/or affordances;_

_(b) conducting post-market monitoring after placing the model on the market, as specified in Measure 3.5;_

_(c) taking into account relevant information about serious incidents (pursuant to Commitment 9); and_

_(d) increasing the breadth and/or depth of assessment or conducting a full systemic risk assessment and mitigation process that is specified in the following paragraph, based on the results of points (a), (b), and (c);_

\[…\]

_Signatories will conduct such a full systemic risk assessment and mitigation process at least before placing the model on the market and whenever the conditions specified in Measure 7.6, first and third paragraph, are met._

Measure 7.6¶1:

_Signatories will update their Model Report if they have reasonable grounds to believe that the justification for why the systemic risks stemming from the model are acceptable (pursuant to Measure 7.2, point (1)) has been materially undermined._

Measure 7.6¶3:

_Further, if the model is amongst their respective most capable models available on the market, Signatories will provide the AI Office with an updated Model Report at least every six months._

### SB 53 ^sb-53-8

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=\(2\)%C2%A0Before%2C%20or%20concurrently%20with%2C%20deploying%20a%20new%20frontier%20model%20or%20a%20substantially%20modified%20version%20of%20an%20existing%20frontier%20model%2C%20a%20large%20frontier%20developer%20shall%20include%20in%20the%20transparency%20report%20required%20by%20paragraph%20\(1\)%20summaries%20of%20all%20of%20the%20following%3A), 22757.12.(c)(2):

_Before, or concurrently with, deploying a new frontier model or a substantially modified version of an existing frontier model, a large frontier developer shall include in the transparency report required by paragraph (1) summaries of all of the following:_

_(A) Assessments of catastrophic risks from the frontier model conducted pursuant to the large frontier developer’s frontier AI framework._

_(B) The results of those assessments._

_(C) The extent to which third-party evaluators were involved. \[…\]_

22757.12.(d):

_A large frontier developer shall transmit to the Office of Emergency Services a summary of any assessment of catastrophic risk resulting from internal use of its frontier models every three months or pursuant to another reasonable schedule specified by the large frontier developer and communicated in writing to the Office of Emergency Services with written updates, as appropriate._

## Accountability ^accountability

**Intentions to implement both internal and external oversight mechanisms designed to encourage adequate execution of the frontier safety policy.[^note-63]** These measures may include internal governance measures, such as oversight mechanisms defining who is responsible for implementing the safety policy, and compliance mechanisms incentivizing personnel to adhere to the policy’s directives. Beyond internal governance, accountability extends externally through external scrutiny measures and transparency measures. External scrutiny ensures that a company’s safety claims can be independently validated by qualified experts. Transparency involves proactively disclosing important safety-related information—such as evaluation results or risk assessments—to the public and relevant stakeholders.

### Anthropic ^anthropic-11

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=16), pages 12–13:

_Internal Governance_ _To facilitate the effective implementation of this policy across the company, we commit to the following:_

1.  _**Responsible Scaling Officer:** We will maintain the position of Responsible Scaling Officer, a designated member of staff who is responsible for reducing catastrophic risk, primarily by ensuring this policy is designed and implemented effectively.\[…\]_
    
2.  _**Readiness:** We will develop internal safety procedures for incident scenarios. Such scenarios include (1) pausing training in response to reaching Capability Thresholds; (2) responding to a security incident involving model weights; and (3) responding to severe jailbreaks or vulnerabilities in deployed models, including restricting access in safety emergencies that cannot otherwise be mitigated. We will run exercises to ensure our readiness for incident scenarios._
    
3.  _**Transparency:** We will share summaries of Capability Reports and Safeguards Reports with Anthropic’s regular-clearance staff, redacting any highly-sensitive information. We will share a minimally redacted version of these reports with a subset of staff, to help us surface relevant technical safety considerations._
    
4.  _**Internal review:** For each Capabilities or Safeguards Report, we will solicit feedback from internal teams with visibility into the relevant activities, with the aims of informing future refinements to our methodology and, in some circumstances, identifying weaknesses and informing the CEO and RSO’s decisions._
    
5.  _**Noncompliance:** We will maintain a process through which Anthropic staff may anonymously notify the Responsible Scaling Officer of any potential instances of noncompliance with this policy._
    
6.  _**Employee agreements:** We will not impose contractual non-disparagement obligations on employees, candidates, or former employees in a way that could impede or discourage them from publicly raising safety concerns about Anthropic. If we offer agreements with a non-disparagement clause, that clause will not preclude raising safety concerns, nor will it preclude disclosure of the existence of that clause._
    

\[…\]

_Transparency and External Input_ _To advance the public dialogue on the regulation of frontier AI model risks and to enable examination of our actions, we commit to the following:_

1.  _**Public disclosures:** We will publicly release key information related to the evaluation and deployment of our models (not including sensitive details). These include summaries of related Capability and Safeguards reports when we deploy a model as well as plans for current and future comprehensive capability assessments and deployment and security safeguards. We will also periodically release information on internal reports of potential instances of non-compliance and other implementation challenges we encounter._
    
2.  _**Expert input:** We will solicit input from external experts in relevant domains in the process of developing and conducting capability and safeguards assessments. We may also solicit external expert input prior to making final decisions on the capability and safeguards assessments._
    
3.  _**U.S. Government notice:** We will notify a relevant U.S. Government entity if a model requires stronger protections than the ASL-2 Standard._
    
4.  _**Procedural compliance review:** On approximately an annual basis, we will commission a third-party review that assesses whether we adhered to this policy’s main procedural commitments (we expect to iterate on the exact list since this has not been done before for RSPs). This review will focus on procedural compliance, not substantive outcomes. We will also do such reviews internally on a more regular cadence._
    

### OpenAI ^openai-12

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=13), pages 12–13:

_Internal governance:_

-   _Clear internal decision-making practices. We have clear roles and responsibilities and decisionmaking practices as described in Appendix B._
-   _Internal Transparency. We will document relevant reports made to the SAG and of SAG’s decision and reasoning. Employees may also request and receive a summary of the testing results and SAG recommendation on capability levels and safeguards (subject to certain limits for highly sensitive information)._
-   _Noncompliance. Any employee can raise concerns about potential violations of this policy, or about its implementation, via our [Raising Concerns Policy](https://cdn.openai.com/policies/raising-concerns-policy-blog-copy-202410.pdf). We will track and appropriately investigate any reported or otherwise identified potential instances of noncompliance with this policy, and where reports are substantiated, will take appropriate and proportional corrective action._

_Transparency and external participation:_

-   _Public disclosures: We will release information about our Preparedness Framework results in order to facilitate public awareness of the state of frontier AI capabilities for major deployments. This published information will include the scope of testing performed, capability evaluations for each Tracked Category, our reasoning for the deployment decision, and any other context about a model’s development or capabilities that was decisive in the decision to deploy. Additionally, if the model is beyond a High threshold, we will include information about safeguards we have implemented to sufficiently minimize the associated risks. Such disclosures about results and safeguards may be redacted or summarized where necessary, such as to protect intellectual property or safety._
-   _Third-party evaluation of tracked model capabilities: If we deem that a deployment warrants deeper testing of Tracked Categories of capability (as described in Section 3.1), for example based on results of Capabilities Report presented to them, then when available and feasible, OpenAI will work with third-parties to independently evaluate models._
-   _Third-party stress testing of safeguards: If we deem that a deployment warrants third party stress testing of safeguards and if high quality third-party testing is available, we will work with third parties to evaluate safeguards. We may seek this out in particular for models that are over a High capability threshold._
-   _Independent expert opinions for evidence produced to SAG: The SAG may opt to get independent expert opinion on the evidence being produced to SAG. The purpose of this input is to add independent analysis from individuals or organizations with deep expertise in domains of relevant risks (e.g., biological risk). If provided, these opinions will form part of the analysis presented to SAG in making its decision on the safety of a deployment. These domain experts may not necessarily be AI experts and their input will form one part of the holistic evidence that SAG reviews._

### Google DeepMind ^google-deepmind-12

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=16), page 16:

_If we assess that a model has reached a CCL that poses an unmitigated and material risk to overall public safety, we aim to share information with appropriate government authorities where it will facilitate the development of safe AI. \[…\] We may also consider disclosing information to other external organizations to promote shared learning and coordinated risk mitigation. We will continue to review and evolve our disclosure process over time._

### Magic ^magic-10

[Magic’s AGI Readiness Policy](https://magic.dev/agi-readiness-policy#:~:text=Magic%E2%80%99s%20engineering%20team):

_Magic’s engineering team, potentially in collaboration with external advisers, is responsible for conducting evaluations on the public and private coding benchmarks described above. If the engineering team sees evidence that our AI systems have exceeded the current performance thresholds on the public and private benchmarks listed above, the team is responsible for making this known immediately to the leadership team and Magic’s Board of Directors (BOD)._

\[…\]

_A member of staff will be appointed who is responsible for sharing the following with our Board of Directors on a quarterly basis:_

-   _A report on the status of the AGI Readiness Policy implementation_
-   _Our AI systems’ current proficiency at the public and private benchmarks laid out above_

### Naver ^naver-4

[Naver’s AI Safety Framework](https://clova.ai/en/tech-blog/en-navers-ai-safety-framework-asf#:~:text=NAVER%E2%80%99s%20AI%20governance%20includes%3A):

_NAVER’s AI governance includes:_

-   _The Future AI Center, which brings together different teams for discussions on the potential risks of AI systems at the field level_
-   _The risk management working group whose role is to determine which of these issues to raise to the board_
-   _The board (or the risk management committee) that makes the final decisions on the matter_

### Meta ^meta-11

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=7), page 7:

_The risk assessment process involves multi-disciplinary engagement, including internal and, where appropriate, external experts from various disciplines (which could include engineering, product management, compliance and privacy, legal, and policy) and company leaders from multiple disciplines._

Page 8:

_The residual risk assessment is reviewed by the relevant research and/or product teams, as well as a multidisciplinary team of reviewers as needed. Informed by this analysis, a leadership team will either request further testing or information, require additional mitigations or improvements, or they will approve the model for release._

### G42 ^g42-10

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=11), page 11:

_A dedicated Frontier AI Governance Board, composed of our Chief Responsible AI Officer, Head of Responsible AI, Head of Technology Risk, and General Counsel, shall oversee all frontier model operations, reviewing safety protocols, risk assessments, and escalation decisions._

_Responsibilities of the Frontier AI Governance Board include, but are not limited to:_

1.  Framework Oversight: Ensuring this Framework is designed appropriately and implemented effectively, and proposing updates as required.
2.  Evaluating Model Compliance: Routine reviews of G42’s most capable models to ensure compliance with this Framework.
3.  Investigation: Investigating reports of potential non-compliance and escalating material incidences of non-compliance to the G42 Executive Leadership Committee.
4.  Incidence Response: Developing a comprehensive incident response plan that outlines the steps to be taken in the event of non-compliance.

### Cohere ^cohere-3

[Cohere’s Secure AI Frontier Model Framework](https://cohere.com/security/the-cohere-secure-ai-frontier-model-framework-february-2025.pdf#page=15), page 15:

_The final authority to determine if our products are safe, secure, and ready to be made available to our customers is delegated by Cohere’s CEO to Cohere’s Chief Scientist. This decision is made on the basis of final, multi-faceted evaluations and testing. In addition, customers deploying Cohere solutions may have additional tests or evaluations they wish to conduct prior to launching a product or system that integrates Cohere models or systems. Cohere provides necessary support to customers to meet any such additional thresholds._

Pages 17–18:

_Documentation is a key aspect of our accountability to our customers, partners, relevant government agencies, and the wider public. To promote transparency about our practices, we:_

-   _Publish documentation regarding our models’ capabilities, evaluation results, configurable secure AI features, and model limitations for developers to safely and securely build AI systems using Cohere solutions. This includes model documentation, such as Cohere’s Usage Policy and Model Cards, and technical guides, such as Cohere’s LLM University._
-   _Are publishing this Framework to share our approach on AI risk management for secure AI._
-   _Offer insights into our data management, security measures, and compliance through our Trust Center._
-   _Provide guidance to our Customers on how they can manage AI risk for their use cases with our AI Security Guide and Enterprise Guide to AI Safety._

### Microsoft ^microsoft-11

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=10), page 9:

_Documentation regarding the pre-mitigation and post-mitigation capability assessment will be provided to Executive Officers responsible for Microsoft’s AI governance program (or their delegates) along with a recommendation for secure and trustworthy deployment setting out the case that: 1) The model has been adequately mitigated to low or medium risk level, 2) The marginal benefits of a model outweigh any residual risk, and 3) The mitigations and documentation will allow the model to be deployed in a secure and trustworthy manner._

_The Executive Officers (or their delegates) will make the final decision on whether to approve the recommendation for secure and trustworthy deployment. They are also responsible for assessing that the recommendation and its components have been developed in a good faith attempt to determine the ultimate capabilities of the model and mitigate risks._

_Information about the capabilities and limitations of the model, relevant evaluations, and the model’s risk classification will be shared publicly, with care taken to minimize information hazards that could give rise to safety and security risks and to protect commercially sensitive information._

_This framework is subject to Microsoft’s broader corporate governance procedures, including independent internal audit and board oversight. Microsoft employees have the ability to report concerns relating to this framework and its implementation, as well as AI governance at Microsoft more broadly, using our existing concern reporting channels, with protection from retaliation and the option for anonymity._

### Amazon ^amazon-10

[Amazon’s Frontier Model Safety Framework](https://cdn.amazon.science/a7/7c/8bdade5c4eda9168f3dee6434fff/pc-amazon-frontier-model-safety-framework-2-7-final-2-9.pdf#page=5), page 5:

_Internally, we will use this framework to guide our model development and launch decisions. The implementation of the framework will require:_

-   _The Frontier Model Safety Framework will be incorporated into the Amazon-wide Responsible AI Governance Program, enabling Amazon-wide visibility into the expectations, mechanisms, and adherence to the Framework._
-   _Frontier models developed by Amazon will be subject to maximal capability evaluations and safeguards evaluations prior to deployment. The results of these evaluations will be reviewed during launch processes. Models may not be publicly released unless safeguards are applied._
-   _The team performing the Critical Capability Threshold evaluations will report to Amazon senior leadership any evaluation that exceeds the Critical Capability Threshold. The report will be directed to the SVP for the model development team, the Chief Security Officer, and legal counsel._
-   _Amazon’s senior leadership will review the plan for applying risk mitigations to address the Critical Capability, how we measure and have assurance about those mitigations, and approve the mitigations prior to deployment._
-   _Amazon’s senior leadership will likewise review the safeguards evaluation report as part of a go/no-go decision._
-   _Amazon will publish, in connection with the launch of a frontier AI model (in model documentation, such as model service cards), information about the frontier model evaluation for safety and security._

### xAI ^xai-8

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf#page=8), pages 8–9:

_To foster accountability, we integrate the approach of designating risk owners, including assigning responsibility for proactively mitigating identified risks._

_Should it happen that xAI learns of an imminent threat of a significantly harmful event, including loss of control, we may take steps such as the following to stop or prevent that event:_

1.  _If we determine it is warranted, we may notify and cooperate with relevant law enforcement agencies, including any agencies that we believe could play a role in preventing or mitigating the incident. xAI employees have whistleblower protections enabling them to raise concerns to relevant government agencies regarding imminent threats to public safety._
2.  _If we determine that xAI systems are actively being used in such an event, we may take steps to isolate and revoke access to user accounts involved in the event._
3.  _If we determine that allowing a system to continue running would materially and unjustifiably increase the likelihood of a catastrophic event, we may temporarily fully shut down the relevant system until we have developed a more targeted response._
4.  _We may perform a post-mortem of the event after it has been resolved, focusing on any areas where changes to systemic factors (for example, safety culture) could have averted such an incident. We may use the post-mortem to inform development and implementation of necessary changes to our risk management practices._

### NVIDIA ^nvidia-4

[NVIDIA’s Frontier AI Risk Assessment](https://images.nvidia.com/content/pdf/NVIDIA-Frontier-AI-Risk-Assessment.pdf#page=14), pages 14–15:

_NVIDIA’s internal governance structures clearly define roles and responsibilities for risk management. It involves separate teams tasked with risk management that have the authority and expertise to intervene in model development timelines, product launch decisions, and strategic planning. This involves embedding risk-aware practices into the daily work of engineers, researchers, and product managers, supported by ongoing training and open dialogue on ethical considerations._

_While our formal model evaluations provide quantitative data, model reviews and interviews with engineering teams reveal developers’ intuitive understandings, early warning signs of risks, and internal safety practices. This qualitative approach offers a more nuanced perspective on AI capabilities and potential threats. Establishing consistent communication channels with employees ensures that the correct stakeholders at NVIDIA remain informed about rapid advancements and can promptly address emerging concerns. By integrating these processes into their development lifecycle, we can create a governance framework that is both flexible and robust. This enables responsible AI innovation while proactively managing the unique risks posed by frontier models, ensuring safer and more ethical deployment across various industry sectors._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-12

[Code of Practice](https://code-of-practice.ai/?section=safety-security#measure-8-1-definition-of-clear-responsibilities), Measure 8.1:

_Signatories will clearly define responsibilities for managing the systemic risks stemming from their models across all levels of the organisation. This includes the following responsibilities:_

_(1) Systemic risk oversight: Overseeing the Signatories’ systemic risk assessment and mitigation processes and measures._

_(2) Systemic risk ownership: Managing systemic risks stemming from Signatories’ models, including the systemic risk assessment and mitigation processes and measures, and managing the response to serious incidents._

_(3) Systemic risk support and monitoring: Supporting and monitoring the Signatories’ systemic risk assessment and mitigation processes and measures._

_(4) Systemic risk assurance: Providing internal and, as appropriate, external assurance about the adequacy of the Signatories’ systemic risk assessment and mitigation processes and measures to the management body in its supervisory function or another suitable independent body (such as a council or board)._

_Signatories will allocate these responsibilities, as suitable for the Signatories’ governance structure and organisational complexity, across the following levels of their organisation:_

_(1) the management body in its supervisory function or another suitable independent body (such as a council or board);_

_(2) the management body in its executive function;_

_(3) relevant operational teams_

_(4) if available, internal assurance providers (e.g. an internal audit function); and_

_(5) if available, external assurance providers (e.g. third-party auditors)._

Measure 8.3:

_Signatories will promote a healthy risk culture and take appropriate measures to ensure that actors who have been assigned responsibilities for managing the systemic risks stemming from their models (pursuant to Measure 8.1) take a reasoned and balanced approach to systemic risk._

### SB 53 ^sb-53-9

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=\(2\)%C2%A0Before%2C%20or%20concurrently%20with%2C%20deploying%20a%20new%20frontier%20model%20or%20a%20substantially%20modified%20version%20of%20an%20existing%20frontier%20model%2C%20a%20large%20frontier%20developer%20shall%20include%20in%20the%20transparency%20report%20required%20by%20paragraph%20\(1\)%20summaries%20of%20all%20of%20the%20following%3A), 22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(5) Using third parties to assess the potential for catastrophic risks and the effectiveness of mitigations of catastrophic risks. \[…\]_

_(9) Instituting internal governance practices to ensure implementation of these processes._

22757.12.(c)(2):

_Before, or concurrently with, deploying a new frontier model or a substantially modified version of an existing frontier model, a large frontier developer shall include in the transparency report required by paragraph (1) summaries of all of the following: \[…\]_

_(D) The extent to which third-party evaluators were involved. \[…\]_

Section 1107.1:

_(a) A frontier developer shall not make, adopt, enforce, or enter into a rule, regulation, policy, or contract that prevents a covered employee from disclosing, or retaliates against a covered employee for disclosing, information to the Attorney General, a federal authority, a person with authority over the covered employee, or another covered employee who has authority to investigate, discover, or correct the reported issue, if the covered employee has reasonable cause to believe that the information discloses either of the following:_

_(1) The frontier developer’s activities pose a specific and substantial danger to the public health or safety resulting from a catastrophic risk._ \[…\]

_(d) A frontier developer shall provide a clear notice to all covered employees of their rights and responsibilities under this section_ \[…\]

_(e)(1) A large frontier developer shall provide a reasonable internal process through which a covered employee may anonymously disclose information to the large frontier developer if the covered employee believes in good faith that the information indicates that the large frontier developer’s activities present a specific and substantial danger to the public health or safety resulting from a catastrophic risk_

## Updating Policies over Time ^updating-policies-over-time

**Intentions to update the policy periodically** – in response to improved understanding of AI risks and best practices for evaluations. For example, developers may identify additional capabilities of concern to evaluate, such as misalignment or chemical, radiological, or nuclear risk. Developers may be interested in improving evaluation procedures and mitigation plans or concretizing commitments further.

### Anthropic ^anthropic-12

[Anthropic’s Responsible Scaling Policy](https://www-cdn.anthropic.com/872c653b2d0501d6ab44cf87f43e1dc4853e4d37.pdf#page=17), page 13:

_Policy changes: Changes to this policy will be proposed by the CEO and the Responsible Scaling Officer and approved by the Board of Directors, in consultation with the Long-Term Benefit Trust. The current version of the RSP is accessible at [www.anthropic.com/rsp](https://www.anthropic.com/rsp). We will update the public version of the RSP before any changes take effect and record any differences from the prior draft in a change log._

### OpenAI ^openai-13

[OpenAI’s Preparedness Framework](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf#page=16), page 15:

_The Preparedness Framework is a living document and will be updated. The SAG reviews proposed changes to the Preparedness Framework and makes a recommendation that is processed according to the standard decision-making process. We will review and potentially update the Preparedness Framework for continued sufficiency at least once a year._

### Google DeepMind ^google-deepmind-13

[Google DeepMind’s Frontier Safety Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3.pdf#page=16), page 16:

_The Frontier Safety Framework will be updated at least once a year—more frequently if we have reasonable grounds to believe the adequacy of the Framework or our adherence to it has been materially undermined. The process will involve (i) an assessment of the Framework’s appropriateness for the management of systemic risk, drawing on information sources such as record of adherence to the framework, relevant high-quality research, information shared through industry forums, and evaluation results, as necessary, and (ii) an assessment of our adherence to the Framework. Following this assessment, we may:_

-   _Update our risk domains and CCLs, where necessary._
-   _Update our testing and mitigation approaches, where needed to ensure risk remains adequately assessed and addressed according to our current understanding._ The updated version and framework assessment will be reviewed by the appropriate corporate governance bodies.

### Magic ^magic-11

[Magic’s AGI Readiness Policy](https://magic.dev/agi-readiness-policy#:~:text=3.%20Updating%20Our%20Understanding):

_Over time, public evidence may emerge that it is safe for models that have demonstrated proficiency beyond the above thresholds to freely proliferate without posing any significant catastrophic risk to public safety. For this reason, we may update this threshold upward over time. We may also modify the public and private benchmarks used._

_Such a change will require approval by our Board of Directors, with input from external security and AI safety advisers._

### Naver ^naver-5

[Naver’s AI Safety Framework](https://clova.ai/en/tech-blog/en-navers-ai-safety-framework-asf#:~:text=Technological%20advances%20in%20AI%20have%20accelerated%20the%20shift%20toward%20safer%20AI%20globally%2C%20and%20our%20AI%20safety%20framework%2C%20too%2C%20will%20be%20continuously%20updated%20to%20keep%20up%20with%20changing%20environments.):

_Technological advances in AI have accelerated the shift toward safer AI globally, and our AI safety framework, too, will be continuously updated to keep up with changing environments._

### Meta ^meta-12

[Meta’s Frontier AI Framework](https://web.archive.org/web/20250630201526/https://ai.meta.com/static-resource/meta-frontier-ai-framework/#page=5), page 5:

_This is the first iteration of our Frontier AI Framework. We expect to update it in the future to reflect developments in both the technology and our understanding of how to manage its risks and benefits. Alongside updates to the Framework, we also identify areas that would benefit from further research and investment to improve our ability to continue to safely develop and release advanced AI models._

### G42 ^g42-11

[G42’s Frontier AI Safety Framework](https://www.g42.ai/application/files/9517/3882/2182/G42_Frontier_Safety_Framework_Publication_Version.pdf#page=5), page 5:

_If a Frontier Capability Threshold has been reached, G42 will update this Framework to define a more advanced threshold that requires increased deployment (e.g., DML 3) and security mitigations (e.g., SML 3)._

Page 12:

_An annual external review of the Framework will be conducted to ensure adequacy, continuously benchmarking G42’s practices against industry standards. G42 will conduct more frequent internal reviews, particularly in accordance with evolving standards and instances of enhanced model capabilities. G42 will proactively engage with government agencies, academic institutions, and other regulatory bodies to help shape emerging standards for frontier AI safety, aligning G42’s practices with evolving global frameworks._

_Changes to this Framework will be proposed by the Frontier AI Governance Board and approved by the G42 Executive Leadership Committee._

### Cohere ^cohere-4

[Cohere’s Secure AI Frontier Model Framework](https://cohere.com/security/the-cohere-secure-ai-frontier-model-framework-february-2025.pdf#page=2), page 2:

_This document describes Cohere’s holistic secure AI approach to enabling enterprises to build safe and secure solutions for their customers. This is the first published version, and it will be updated as we continue to develop new best practices to advance the safety and security of our products._

### Microsoft ^microsoft-12

[Microsoft’s Frontier Governance Framework](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Frontier-Governance-Framework.pdf#page=10), page 9:

_We will update our framework to keep pace with new developments. Every six months, we will have an explicit discussion on how this framework may need to be improved. We acknowledge that advances in the science of evaluation and risk mitigation may lead to additional requirements in this framework or remove the need for existing requirements. Any updates to our practices will be reviewed by Microsoft’s Chief Responsible AI Officer prior to their adoption. Where appropriate, updates will be made public at the same time as we adopt them._

### Amazon ^amazon-11

[Amazon’s Frontier Model Safety Framework](https://cdn.amazon.science/a7/7c/8bdade5c4eda9168f3dee6434fff/pc-amazon-frontier-model-safety-framework-2-7-final-2-9.pdf#page=5), page 5:

_As we advance our work on frontier models, we will also continue to enhance our AI safety evaluation and risk management processes. This evolving body of work requires an evolving framework as well. We will therefore revisit this Framework at least annually and update it as necessary to ensure that our protocols are appropriately robust to uphold our commitment to deploy safe and secure models. We will also update this Framework as needed in connection with significant technological developments._

### xAI ^xai-9

[xAI’s Risk Management Framework](https://data.x.ai/2025-08-20-xai-risk-management-framework.pdf#page=7), page 7:

_xAI aims to keep the public informed about our risk management policies. As we work towards incorporating more risk management strategies, we intend to publish updates to this RMF._

### NVIDIA ^nvidia-5

[NVIDIA’s Frontier AI Risk Assessment](https://images.nvidia.com/content/pdf/NVIDIA-Frontier-AI-Risk-Assessment.pdf), page 1:

_AI capabilities and their associated risks evolve rapidly. Therefore, our risk management framework will be regularly reviewed and updated to reflect new findings, emerging threats, and ongoing advancements in the industry. This iterative approach will ensure our risk assessment remains fit-for-purpose over time._

Relevant regulatory guidance:

### Code of Practice ^code-of-practice-13

[Code of Practice](https://code-of-practice.ai/?section=safety-security#measure-1-3-updating-the-framework), Measure 1.3:

_Signatories will update the Framework as appropriate, including without undue delay after a Framework assessment (specified in the following paragraphs), to ensure the information in Measure 1.1 is kept up-to-date and the Framework is at least state-of-the-art. For any update of the Framework, Signatories will include a changelog, describing how and why the Framework has been updated, along with a version number and the date of change._

_Signatories will conduct an appropriate Framework assessment, if they have reasonable grounds to believe that the adequacy of their Framework and/or their adherence thereto has been or will be materially undermined, or every 12 months starting from their placing of the model on the market, whichever is sooner._ \[…\]

_A Framework assessment will include the following:_

_(1) Framework adequacy: An assessment of \[…\]_

_(2) Framework adherence: An assessment focused on \[…\]_

_Signatories will provide the AI Office with (unredacted) access to their Framework, and updates thereof, within five business days of either being confirmed._

Measure 10.2:

_If and insofar as necessary to assess and/or mitigate systemic risks, Signatories will publish (e.g. via their websites) a summarised version of their Framework and Model Report(s), and updates thereof (pursuant to Commitments 1 and 7), with removals to not undermine the effectiveness of safety and/or security mitigations and to protect sensitive commercial information._

### SB 53 ^sb-53-10

[California Senate Bill 53](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53#:~:text=\(2\)%C2%A0Before%2C%20or%20concurrently%20with%2C%20deploying%20a%20new%20frontier%20model%20or%20a%20substantially%20modified%20version%20of%20an%20existing%20frontier%20model%2C%20a%20large%20frontier%20developer%20shall%20include%20in%20the%20transparency%20report%20required%20by%20paragraph%20\(1\)%20summaries%20of%20all%20of%20the%20following%3A), 22757.12.(a):

_A large frontier developer shall write, implement, comply with, and clearly and conspicuously publish on its internet website a frontier AI framework that applies to the large frontier developer’s frontier models and describes how the large frontier developer approaches all of the following: \[…\]_

_(6) Revisiting and updating the frontier AI framework, including any criteria that trigger updates and how the large frontier developer determines when its frontier models are substantially modified enough to require disclosures pursuant to subdivision (c)._

22757.12.(b):

_(1) A large frontier developer shall review and, as appropriate, update its frontier AI framework at least once per year._

_(2) If a large frontier developer makes a material modification to its frontier AI framework, the large frontier developer shall clearly and conspicuously publish the modified frontier AI framework and a justification for that modification within 30 days._

## Conclusion ^conclusion

In this document, we have described several common aspects of twelve existing frontier AI safety policies. Overall, many of the common elements originally discussed in our August 2024 report still hold, despite the addition of nine new safety policies. Nearly every policy describes capability thresholds for which developers will conduct model evaluations. Reaching capability thresholds requires elevated measures for model weight security and model deployment mitigations. If the security and deployment mitigations cannot meet predefined standards, then the frameworks commit to halting development and/or deployment of the model. Evaluations are to be conducted at regular intervals for every model that is substantially more capable than previously tested models. Internal and external accountability mechanisms are outlined, such as transparent reporting of model capabilities or safeguards, or third-party auditing and model evaluations. The frameworks may be updated over time as practices for AI risk management evolve.

[^note-1]: This report is descriptive, not prescriptive, and does not represent METR’s recommendations. Any gap between a company’s published safety policy and regulatory requirements does not necessarily indicate noncompliance. For example, we may have overlooked a relevant element, the company may not be in the regulation’s scope, its requirements may not yet be in force, the company may maintain separate compliance documentation, etc.
[^note-2]: Note that there is currently no consensus or clear framework for determining what counts as an “acceptable level” of risk.
[^note-3]: Other companies have published similar documents in response to the Frontier AI Safety Commitments made in Seoul, such as [IBM](https://newsroom.ibm.com/blog-trustworthy-ai-at-scale-ibms-ai-safety-and-governance-framework) and [Samsung](https://www.samsung.com/global/sustainability/policy-file/AZTUlveqAMoALYMV/Samsung_Electronics_AI_Safety_Framework_en.pdf)
[^note-4]: Cohere’s Secure AI Frontier Model Framework focuses on risks to Cohere’s enterprise users.
[^cite-5]: Christopher A. Mouton, Caleb Lucas, Ella Guest. [The Operational Risks of AI in Large-Scale Biological Attacks Results of a Red-Team Study](https://www.rand.org/pubs/research_reports/RRA2977-2.html). January 25, 2024. RAND.
[^cite-6]: Tejal Patwardhan, Kevin Liu, Todor Markov, Neil Chowdhury, Dillon Leet, Natalie Cone, Caitlin Maltbie, Joost Huizinga, Carroll Wainwright, Shawn Jackson, Steven Adler, Rocco Casagrande, Aleksander Madry. [Building an early warning system for LLM-aided biological threat creation.](https://openai.com/index/building-an-early-warning-system-for-llm-aided-biological-threat-creation/) January 31, 2024. OpenAI.
[^cite-7]: AI at Meta. [The Llama 3 Herd of Models](https://ai.meta.com/research/publications/the-llama-3-herd-of-models/). July 23, 2024.
[^cite-8]: OpenAI. [OpenAI o1 System Card](https://cdn.openai.com/o1-system-card-20240917.pdf). September 12, 2024.
[^cite-9]: OpenAI. [Deep Research System Card](https://cdn.openai.com/deep-research-system-card.pdf). February 25, 2025.
[^cite-10]: Doni Bloomfield, Jaspreet Pannu, Alex W. Zhu, Madelena Y. Ng, Ashley Lewis, Eran Bendavid, Steven M. Asch, Tina Hernandez-Boussard, Anita Cicero, Tom Inglesby. [AI and biosecurity: The need for governance](https://www.science.org/doi/10.1126/science.adq1977). _Science_. August 22, 2024.
[^cite-11]: National Security Commission on Emerging Biotechnology. [AIxBio White Paper 3: Risks of AIxBio](https://www.biotech.senate.gov/press-releases/aixbio-white-paper-risks-of-aixbio/). January 2024.
[^cite-12]: Christopher A. Mouton, Caleb Lucas, Ella Guest. [The Operational Risks of AI in Large-Scale Biological Attacks Results of a Red-Team Study](https://www.rand.org/pubs/research_reports/RRA2977-2.html). January 25, 2024. RAND.
[^cite-13]: AI at Meta. [The Llama 3 Herd of Models](https://ai.meta.com/research/publications/the-llama-3-herd-of-models/). July 23, 2024.
[^cite-14]: Anthropic. [Responsible Scaling Policy Evaluations Report – Claude 3 Opus](https://cdn.sanity.io/files/4zrzovbb/website/210523b8e11b09c704c5e185fd362fe9e648d457.pdf). May 19, 2024.
[^cite-15]: Anthropic. [Claude 3.7 Sonnet System Card.](https://assets.anthropic.com/m/785e231869ea8b3b/original/claude-3-7-sonnet-system-card.pdf) February 24, 2025.
[^cite-16]: Department of Homeland Security. [Safety and Security Guidelines for Critical Infrastructure Owners and Operators](https://www.dhs.gov/sites/default/files/2024-04/24_0426_dhs_ai-ci-safety-security-guidelines-508c.pdf). April 2024.
[^cite-17]: AI at Meta. [CyberSecEval: Comprehensive Evaluation Framework for Cybersecurity Risks and Capabilities of Large Language Models](https://huggingface.co/spaces/facebook/CyberSecEval)
[^cite-18]: Richard Fang, Rohan Bindu, Akul Gupta, Qiusi Zhan, Daniel Kang. [Teams of LLM Agents can Exploit Zero-Day Vulnerabilities](https://arxiv.org/abs/2406.01637). June 2, 2024.
[^cite-19]: Brian Singer, Keane Lucas, Lakshmi Adiga, Meghna Jain, Lujo Bauer, Vyas Sekar. [On the Feasibility of Using LLMs to Execute Multistage Network Attacks](https://www.arxiv.org/abs/2501.16466). January 27, 2025.
[^cite-20]: Andy K. Zhang, Neil Perry, Riya Dulepet, Eliot Jones, Justin W. Lin, Joey Ji, Celeste Menders, Gashon Hussein, Samantha Liu, Donovan Jasper, Pura Peetathawatchai, et al. [Cybench: A Framework for Evaluating Cybersecurity Capabilities and Risk of Language Models](https://www.arxiv.org/abs/2408.08926). August 15, 2024.
[^cite-21]: Timothee Chauvin. [eyeballvul: a future-proof benchmark for vulnerability detection in the wild](https://arxiv.org/abs/2407.08708). July 11, 2024.
[^cite-22]: Google DeepMind. [Dangerous capability evaluations](https://github.com/google-deepmind/dangerous-capability-evaluations/tree/main). June 2024.
[^cite-23]: AI at Meta. [The Llama 3 Herd of Models](https://ai.meta.com/research/publications/the-llama-3-herd-of-models/). July 23, 2024.
[^cite-24]: Anthropic. [Responsible Scaling Policy Evaluations Report – Claude 3 Opus](https://cdn.sanity.io/files/4zrzovbb/website/210523b8e11b09c704c5e185fd362fe9e648d457.pdf). May 19, 2024.
[^cite-25]: OpenAI. [OpenAI o1 System Card](https://cdn.openai.com/o1-system-card-20240917.pdf). September 12, 2024.
[^cite-26]: Google DeepMind. [Gemini 1.5: Unlocking multimodal understanding across millions of tokens of context](https://storage.googleapis.com/deepmind-media/gemini/gemini_v1_5_report.pdf). February 15, 2024.
[^cite-27]: Suriya Gunasekar, Yi Zhang, Jyoti Aneja, Caio César Teodoro Mendes, Allie Del Giorno, … Yuanzhi Li. [Textbooks Are All You Need](https://arxiv.org/abs/2306.11644). Microsoft Research. June 20, 2023.
[^cite-28]: AI at Meta. [The Llama 3 Herd of Models](https://ai.meta.com/research/publications/the-llama-3-herd-of-models/). July 23, 2024.
[^cite-29]: Xian Li, Ping Yu, Chunting Zhou, Timo Schick, Omer Levy, Luke Zettlemoyer, Jason E Weston, Mike Lewis. [Self-Alignment with Instruction Backtranslation](https://openreview.net/forum?id=1oijHJBRsT). ICLR 2024.
[^cite-30]: Yuntao Bai, Saurav Kadavath, Sandipan Kundu, Amanda Askell, Jackson Kernion, Andy Jones, Anna Chen, Anna Goldie, … Jared Kaplan. [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073). December 15, 2022.
[^cite-31]: NVIDIA. [Nemotron-4 340B Technical Report](https://arxiv.org/abs/2406.11704). August 6, 2024.
[^cite-32]: Yecheng Jason Ma, William Liang, Guanzhi Wang, De-An Huang, Osbert Bastani, Dinesh Jayaraman, Yuke Zhu, Linxi Fan, Anima Anandkumar. [Eureka: Human-Level Reward Design via Coding Large Language Models](https://arxiv.org/abs/2310.12931). April 30, 2024. ICLR 2024.
[^cite-33]: Lei Wang, Chen Ma, Xueyang Feng, Zeyu Zhang, Hao Yang, Jingsen Zhang, Zhiyuan Chen, Jiakai Tang, Xu Chen, Yankai Lin, Wayne Xin Zhao, Zhewei Wei, Jirong Wen. [A survey on large language model based autonomous agents](https://doi.org/10.1007/s11704-024-40231-1). Frontiers of Computer Science. March 22, 2024.
[^cite-34]: Qian Huang, Jian Vora, Percy Liang, Jure Leskovec. [MLAgentBench: Evaluating Language Agents on Machine Learning Experimentation](https://arxiv.org/abs/2310.03302). April 14, 2024.
[^cite-35]: David Owen. [Interviewing AI researchers on automation of AI R&D](https://epochai.org/blog/interviewing-ai-researchers-on-automation-of-ai-rnd). August 27, 2024.
[^cite-36]: Wijk et al. [RE-Bench: Evaluating frontier AI R&D capabilities of language model agents against human experts](https://arxiv.org/abs/2411.15114). November 22, 2024.
[^cite-37]: The White House. [Memorandum on Advancing the United States’ Leadership in Artificial Intelligence; Harnessing Artificial Intelligence to Fulfill National Security Objectives; and Fostering the Safety, Security, and Trustworthiness of Artificial Intelligence](https://bidenwhitehouse.archives.gov/briefing-room/presidential-actions/2024/10/24/memorandum-on-advancing-the-united-states-leadership-in-artificial-intelligence-harnessing-artificial-intelligence-to-fulfill-national-security-objectives-and-fostering-the-safety-security/#:~:text=automate%20development%20and%20deployment%20of%20other%20models%20with%20such%20capabilities). October 24, 2024.
[^cite-38]: OpenAI. [MLE-bench](https://openai.com/index/mle-bench/). October 10, 2024.
[^cite-39]: Wijk et al. [RE-Bench: Evaluating frontier AI R&D capabilities of language model agents against human experts](https://arxiv.org/abs/2411.15114). November 22, 2024.
[^cite-40]: Sella Nevo, Dan Lahav, Ajay Karpur, Yogev Bar-On, Henry Alexander Bradley, Jeff Alstott. [Securing AI Model Weights: Preventing Theft and Misuse of Frontier Models](https://www.rand.org/pubs/research_reports/RRA2849-1.html). RAND. May 30, 2024.
[^note-41]: See also, [A secure approach to generative AI with AWS](https://aws.amazon.com/blogs/machine-learning/a-secure-approach-to-generative-ai-with-aws/). AWS Machine Learning Blog. April 16, 2024.
[^note-42]: Referring to the security levels of RAND’s report [Securing AI Model Weights](https://www.rand.org/pubs/research_reports/RRA2849-1.html). SL2 is intended to “thwart most professional opportunistic efforts,” SL3 to “thwart cybercrime syndicates or insider threats,” SL4 to “thwart most standard operations by leading cyber-capable institutions,” and SL5 to “thwart most top-priority operations by the top cyber-capable institutions.”
[^cite-43]: Yuntao Bai, Andy Jones, Kamal Ndousse, Amanda Askell, Anna Chen, Nova DasSarma, Dawn Drain, Stanislav Fort, Deep Ganguli, et al. [Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback](https://arxiv.org/abs/2204.05862). April 12, 2022.
[^cite-44]: Andy Zou, Long Phan, Justin Wang, Derek Duenas, Maxwell Lin, Maksym Andriushchenko, Rowan Wang, Zico Kolter, Matt Fredrikson, Dan Hendrycks. [Improving Alignment and Robustness with Circuit Breakers](https://arxiv.org/abs/2406.04313). July 12, 2024.
[^cite-45]: Rishub Tamirisa, Bhrugu Bharathi, Long Phan, Andy Zhou, Alice Gatti, Tarun Suresh, Maxwell Lin, Justin Wang, Rowan Wang, Ron Arel, Andy Zou, Dawn Song, Bo Li, Dan Hendrycks, Mantas Mazeika. [Tamper-Resistant Safeguards for Open-Weight LLMs](https://arxiv.org/abs/2408.00761). August 1, 2024.
[^cite-46]: Mantas Mazeika, Long Phan, Xuwang Yin, Andy Zou, Zifan Wang, Norman Mu, Elham Sakhaee, Nathaniel Li, Steven Basart, Bo Li, David Forsyth, Dan Hendrycks. [HarmBench: A Standardized Evaluation Framework for Automated Red Teaming and Robust Refusal](https://arxiv.org/abs/2402.04249v2). February 6, 2024.
[^cite-47]: Abhay Sheshadri, Aidan Ewart, Phillip Guo, Aengus Lynch, Cindy Wu, Vivek Hebbar, Henry Sleight, Asa Cooper Stickland, Ethan Perez, Dylan Hadfield-Menell, Stephen Casper. [Targeted Latent Adversarial Training Improves Robustness to Persistent Harmful Behaviors in LLMs](https://arxiv.org/abs/2407.15549). July 22, 2024.
[^cite-48]: AI at Meta. [Llama Guard and Code Shield](https://github.com/meta-llama/PurpleLlama)
[^note-49]: See also the Frontier Model Forum’s [issue brief on red-teaming](https://www.frontiermodelforum.org/updates/red-teaming/)
[^cite-50]: Andy Zou, Zifan Wang, Nicholas Carlini, Milad Nasr, J. Zico Kolter, Matt Fredrikson. [Universal and Transferable Adversarial Attacks on Aligned Language Models](https://arxiv.org/abs/2307.15043). December 20, 2023.
[^cite-51]: T. Ben Thompson, Michael Sklar. [Fluent Student-Teacher Redteaming](https://www.arxiv.org/abs/2407.17447). July 24, 2024.
[^note-52]: See [Planning red teaming for large language models (LLMs) and their applications](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/red-teaming) for guidance on general red teaming. In addition to manual red teaming, automated red teaming frameworks such as [PyRIT](https://www.microsoft.com/en-us/security/blog/2024/02/22/announcing-microsofts-open-automation-framework-to-red-team-generative-ai-systems/), developed by Microsoft’s AI Red Team, can provide additional assurance.
[^cite-53]: Nathaniel Li, Ziwen Han, Ian Steneker, Willow Primack, Riley Goodside, Hugh Zhang, Zifan Wang, Cristina Menghini, Summer Yue. [LLM Defenses Are Not Robust to Multi-Turn Human Jailbreaks Yet](https://arxiv.org/abs/2408.15221). Scale AI. August 27, 2024.
[^cite-54]: Sella Nevo, Dan Lahav, Ajay Karpur, Yogev Bar-On, Henry Alexander Bradley, Jeff Alstott. [Securing AI Model Weights: Preventing Theft and Misuse of Frontier Models](https://www.rand.org/pubs/research_reports/RRA2849-1.html). RAND. May 30, 2024.
[^cite-55]: Peter Henderson, Xiangyu Qi, Yi Zeng, Tinghao Xie, Pin-Yu Chen, Ruoxi Jia, Prateek Mittal. [Safety Risks from Customizing Foundation Models via Fine-Tuning](https://hai.stanford.edu/policy-brief-safety-risks-customizing-foundation-models-fine-tuning). January 11, 2024.
[^cite-56]: Mary Phuong, Matthew Aitchison, Elliot Catt, Sarah Cogan, Alexandre Kaskasoli, Victoria Krakovna, David Lindner, Matthew Rahtz, et al. [Evaluating Frontier Models for Dangerous Capabilities](https://arxiv.org/abs/2403.13793). March 20, 2024. Google DeepMind.
[^cite-57]: Sergei Glazunov and Mark Brand. [Project Naptime: Evaluating Offensive Security Capabilities of Large Language Models](https://googleprojectzero.blogspot.com/2024/06/project-naptime.html). June 20, 2024. Google Project Zero
[^cite-58]: Tom Davidson, Jean-Stanislas Denain, Pablo Villalobos, Guillem Bas. [AI capabilities can be significantly improved without expensive retraining](https://arxiv.org/abs/2312.07413). December 12, 2023.
[^cite-59]: John Yang, Carlos E. Jimenez, Alexander Wettig, Kilian Lieret, Shunyu Yao, Karthik Narasimhan, Ofir Press. [SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering](https://arxiv.org/abs/2405.15793). May 6, 2024.
[^cite-60]: Ryan Greenblatt, Fabien Roger, Dmitrii Krasheninnikov, David Krueger. [Stress-Testing Capability Elicitation With Password-Locked Models](https://arxiv.org/abs/2405.19550v1). May 29, 2024.
[^cite-61]: METR. [Measuring the impact of post-training enhancements](https://metr.org/blog/2024-03-15-measuring-post-impact-enhancements/). March 15, 2024.
[^cite-62]: Sella Nevo, Dan Lahav, Ajay Karpur, Yogev Bar-On, Henry Alexander Bradley, Jeff Alstott. [Securing AI Model Weights: Preventing Theft and Misuse of Frontier Models](https://www.rand.org/pubs/research_reports/RRA2849-1.html). RAND. May 30, 2024.
[^note-63]: Note that some companies may have existing or separate policies that cover some elements of accountability, such as internal governance or noncompliance prevention.

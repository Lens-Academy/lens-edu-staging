---
title: "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment"
author:
  - "Mauricio Baker"
  - "Gabriel Kulp"
  - "Oliver Marks"
  - "Miles Brundage"
  - "Lennart Heim"
source_url: "https://arxiv.org/abs/2507.15916"
published: 2025-07-21
created: 2026-07-28
accessed: 2026-07-28
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

longtable

###### Abstract

The risks of frontier AI may require international cooperation, which in turn may require verification: checking that all parties follow agreed-on rules. For instance, states might need to verify that powerful AI models are widely deployed only after their risks to international security have been evaluated and deemed manageable. However, research on AI verification could benefit from greater clarity and detail. To address this, this report provides an in-depth overview of AI verification, intended for both policy professionals and technical researchers. We present novel conceptual frameworks, detailed implementation options, and key R&D challenges. These draw on existing literature, expert interviews, and original analysis, all within the scope of confidentially overseeing AI development and deployment that uses thousands of high-end AI chips. We find that states could eventually verify compliance by using six largely independent verification approaches with substantial redundancy: (1) _built-in security features_ in AI chips; (2-3) _separate monitoring devices_ attached to AI chips; and (4-6) _personnel-based mechanisms_, such as whistleblower programs. While promising, these approaches require guardrails to protect against abuse and power concentration, and many of these technologies have yet to be built or stress-tested. To enable states to confidently verify compliance with rules on large-scale AI development and deployment, the R&D challenges we list need significant progress.† ††footnotetext: As a RAND working paper, this paper intends to share early insights and solicit informal peer review, so it has not yet been formally peer reviewed or professionally edited. Review comments are welcome on [alphaXiv](https://www.alphaxiv.org/abs/2507.15916).

## Summary

### Background

The risks of frontier AI may require international cooperation, which could require compliance to be verified. As frontier AI systems become more advanced, they could bring many benefits but also pose global risks, such as lowering barriers to developing weapons of mass destruction and losing human control over AI. Such extreme, shared risks can motivate even rival powers to cooperate, as shown by the history of arms control. Still, states may be unwilling to limit their own advanced AI development and deployment if they cannot trust that other states will do the same, as one-sided restraint could put states at a strategic disadvantage. Thus, for international agreements on AI to be made and followed, verification of compliance could be crucial ([Section 1](https://arxiv.org/html/2507.15916v2#Sx2 "1. Introduction ‣ Verifying International Agreements on AI")).

### Contributions and Approach

This report overviews options for verifying compliance with rules on AI, addressing gaps in the field’s clarity and detail. To date, the field has explored many verification mechanisms, but there is limited clarity on how these mechanisms can be combined effectively, so that they reinforce weak points rather than create new vulnerabilities. The field also has yet to examine many implementation questions in any detail, hindering assessments of what is feasible and what research is needed. To address both of these issues, our overview features new conceptual frameworks and relatively detailed implementation analyses ([Section 1.1](https://arxiv.org/html/2507.15916v2#Sx2.SSx1 "1.1 Contributions ‣ 1. Introduction ‣ Verifying International Agreements on AI")). As examples of its detail, our analysis outlines options for: detecting hardware backdoors at scale, controlling inference non-determinism, doing “compute accounting” when operations are duplicated, and protecting whistleblowers from state suppression. Throughout, we draw on a literature review and 18 expert interviews ([Section 2.4](https://arxiv.org/html/2507.15916v2#Sx3.SSx4 "2.4 Methodology ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")).

### Scope

We focus on verification options that oversee large-scale AI compute use, and which have the potential to be confidential and effective internationally. Large-scale AI compute use, in this report, refers to the use of thousands of AI chips for multiple months ([Section 2.2](https://arxiv.org/html/2507.15916v2#Sx3.SSx2 "2.2 Rules on Large-Scale AI Compute ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")). These can be overseen to set rules on frontier AI development and associated mass deployment, without intruding on smaller-scale activities. Confidentiality refers to protecting sensitive information—especially models, data, and code—from unauthorized access, especially theft. Finally, international effectiveness means effectiveness even against states determined to conceal non-compliance ([Section 1](https://arxiv.org/html/2507.15916v2#Sx2 "1. Introduction ‣ Verifying International Agreements on AI")).

In the above context, we cover options for verifying compliance with rules on AI models, data, and code. These include many potential rules aimed at AI safety and security, transparency, benefit-sharing, military limits, and international norms (Table 3). For example, one such rule could be that future frontier AI models must be subject to specific tests that aim to measure how much they will increase access to weapons of mass destruction. Then, if these test results are deemed to indicate unmanageable risk, the risks could be required to be addressed, as determined through further tests, before large-scale deployment may proceed. Regardless of the exact rules one might wish to verify, much of the verification problem is the same: identifying what models, data, and code were used, so one can run desired tests on them ([Section 2.1](https://arxiv.org/html/2507.15916v2#Sx3.SSx1 "2.1 Rules on AI Models, Data, and Code ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")).

Determining which technical rules actually achieve policy objectives remains challenging. Even if one can robustly verify that, say, a model was trained with fewer than X operations, or that it scores below Y on a specific risk evaluation, we still need a separate analysis to determine whether these technical rules truly address the relevant policy concerns. This report focuses on verifying compliance with technical rules, while acknowledging that specifying effective technical rules is an important area of ongoing and future work ([Section 3.3](https://arxiv.org/html/2507.15916v2#Sx4.SSx3 "3.3 Addressing Broader Challenges for Verification ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")).

### Key Findings

Verifying rules on AI models, data, and code in the above context can be decomposed into subgoals ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4 "3. Verification Framework ‣ Verifying International Agreements on AI"); [Figure 1](https://arxiv.org/html/2507.15916v2#Sx1.F1 "Figure 1 ‣ Key Findings ‣ Summary ‣ Verifying International Agreements on AI")). These are:

1.  1.
    
    Verify that _declared_ uses of large-scale AI compute are compliant by (A) verifying that trained AI models and their outputs were generated as claimed; and (B) verifying evaluation results, or more generally, verifying that declared models, data, and code have the required properties. “Declared” means self-reported, preferably via confidentiality-preserving technologies.
    
2.  2.
    
    Verify that there are no _undeclared_ uses of large-scale AI compute by (A) verifying that the use of known AI data centers is accounted for; and (B) verifying that no actor has hidden AI data centers or large, decentralized collections of AI chips that can be used for violations.
    

![Refer to caption](https://arxiv.org/html/2507.15916v1/x1.png)

Figure 1: Framework of verification subgoals. We decompose a broad verification goal into subgoals, to clarify how verification can be achieved. Note the italicized terms such as “Evaluations” are only rough summaries of each subgoal; the figure’s non-italicized descriptions are more precise.

To complete these subgoals, states could create six layers of verification—six largely independent assurances of compliance ([Section 4](https://arxiv.org/html/2507.15916v2#Sx5 "4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"); Table 1; [Figure 2](https://arxiv.org/html/2507.15916v2#Sx1.F2 "Figure 2 ‣ Key Findings ‣ Summary ‣ Verifying International Agreements on AI")). Like “layers of defense,” a full implementation of each layer could verify compliance on its own, and multiple layers would reinforce each other. Thus, a stack of layers is an effective combination of verification mechanisms; it completes each subgoal with redundancy. In brief, the layers are:

-   •
    
    On-chip: (1) This layer would perform verification by using functionalities _built into_ AI chips. Due to their cybersecurity benefits, some versions of these are already commonplace.
    
-   •
    
    Off-chip: These layers would use _external devices_ to oversee AI chips. The devices could be (2) network taps, to intercept data exchanged between AI chips; and (3) analog sensors, to record measurements such as power use. These data could then be confidentially analyzed.
    
-   •
    
    Personnel-based: Several layers would leverage the large _workforce_ involved in AI: (4) whistleblower programs, (5) interviews of personnel, and (6) national intelligence activities.
    

| Potential verification layer | Summary of layer | Key advantages | Key disadvantages |
| --- | --- | --- | --- |
| On-chip security features (i.e., secure boot, Confidential Computing) ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"))![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image5.png) | Security features built into AI chips may enable verification, such as by ensuring that AI chips log traces of their activities for confidential analysis. | Offers maximum transparency into AI chips’ uses. | Poses unsolved technical problems and severe security challenges (e.g., untrusted suppliers). Insecure AI chips may need to be replaced. |
| --- | --- | --- | --- |
| Off-chip network tap (and analysis) (e.g. “FlexHEGs”) ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"))![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image2.png) | Mutually vetted devices could intercept data exchanged between chips, then check for discrepancies with declared uses. | Could be retrofitted to existing AI chips and optimized for security. | Poses technical, logistical, and security challenges. Strongest versions need redesigned chip-adjacent hardware. |
| --- | --- | --- | --- |
| Off-chip analog sensors (and analysis, e.g., proof-of-learning) ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"))![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image1.png) | Physically secured chips could check that (i) declared AI compute uses are accurate (e.g., reproducible) and (ii) their compute use adds up to the expected total (estimated with analog sensors, e.g., power meters, in AI data centers). | Could be retrofitted to existing AI chips and optimized for security. | Poses unsolved technical problems. Likely requires separate trusted clusters for analysis, and manufacturing & installing sensors. |
| --- | --- | --- | --- |
| Whistleblower programs ([Section 4.3](https://arxiv.org/html/2507.15916v2#Sx5.SSx3 "4.3 Personnel-Based Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"))![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image9.png) | Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals. | Relatively simple, precedented, and implementation- ready. | Unclear effectiveness: depends on the number and loyalty of accomplices. |
| --- | --- | --- | --- |
| Interviews of personnel ([Section 4.3](https://arxiv.org/html/2507.15916v2#Sx5.SSx3 "4.3 Personnel-Based Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"))![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image6.png) | Interviews may reveal violations at any verification subgoal, e.g., via inconsistencies or perhaps improved lie detection tech, but such tech is abusable. | Relatively simple and precedented. | Unclear effectiveness: depends on accomplices’ ability to lie undetected. |
| --- | --- | --- | --- |
| National intelligence activities ([Section 4.3](https://arxiv.org/html/2507.15916v2#Sx5.SSx3 "4.3 Personnel-Based Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"))![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image3.png) | Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence. | Precedented and may be feasible unilaterally. | More adversarial, harder for third parties to verify, and unclear effectiveness. |
| --- | --- | --- | --- |
|  |  |  |  |
| --- | --- | --- | --- |

Table 1: Six layers for verifying the compliance of large-scale AI development and deployment. Green (red) icons are Verifier-(un)trusted.

![Refer to caption](https://arxiv.org/html/2507.15916v1/x2.png)

Figure 2: Verification layers consist of distinct mechanisms for each verification subgoal.

To enhance the above layers, various less robust mechanisms could serve as supplements. These could include satellite images and open-source information.

Each of the above verification layers has different strengths and weaknesses (Table 1). For example, on-chip functionalities could ultimately leave the smallest margins of error when verifying claims. Off-chip devices could be the best way to adapt existing hardware to make it verifiable, as some versions could be retrofitted onto insecure AI chips. Finally, personnel-based layers could be most readily available, as whistleblowers, for instance, do not require new or complex technology.

Verification could also be harmful, which warrants guardrails. Verification, if implemented without adequate restraint, could compromise sensitive information, hinder innovation, and centralize information and power. Throughout this report, we discuss potential mitigations, including: using confidentiality-preserving technologies ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")); limiting the scope of verification to large-scale AI compute ([Section 2.2](https://arxiv.org/html/2507.15916v2#Sx3.SSx2 "2.2 Rules on Large-Scale AI Compute ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")); extensively vetting and constraining network taps and analog sensors ([Section 4.2.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px1 "4.2.1.1 Prerequisites: Off-Chip Devices ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")); and being cautious with verification mechanisms that double as enforcement tools, e.g., by requiring multiple parties to approve any enforcement actions ([Section 4.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx2 "4.1.2 Analysis ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).

Overall, states could become confident in verification of compliance with rules on large-scale AI development and deployment, but this requires progress on the R&D and infrastructure challenges we list ([Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI"); Table 2). Throughout the six verification layers, we were able to outline plausible ways to address every implementation challenge we identified, including guarding against a range of potential circumvention tactics. This suggests states could create six verification layers that each offer separate, meaningful evidence of compliance. Additionally, the personnel-based layers could provide some assurances with relatively little preparation required. However, the on- and off-chip layers will likely be circumventable until there is substantial progress on the R&D and infrastructure challenges we list. This progress could be driven by investments, pilot programs, and red teaming. Such efforts will determine whether, when states consider verification, they will see a few nascent options or many tried-and-tested technologies.

| Verification layer | Selected R&D and infrastructure challenges (Legend:  : hardware;  : CS/ML;  : organizational) |
| --- | --- |
| 1\. Security features in AI chips ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) |   A. System software protocol: Given verifiable system software (with access to e.g., kernels, memory), verify workload code, and model and data locations, despite any potential obfuscation ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  B. Hardware design attestation: Given a scanned hardware layout and Hardware Description Language (HDL), check if they match ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  C. Hardware security features: Develop highly vetted, open-source, dedicated hardware designs for secure boot, Confidential Computing, and on-chip tamper-proofing ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  D. Design adoption: Adopt the above designs into leading AI chips. |
| --- | --- |
| 2\. Off-chip network taps & analysis ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) |   A. Network tap analysis: Given a cluster’s inter-accelerator data (including kernels), verify that the cluster executed only a claimed workload ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  B. Network taps: Design and manufacture appropriate network taps, or identify suitable existing tech ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  C. Trusted clusters: Build small compute clusters that are or can be mutually physically secured ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). |
| --- | --- |
| 3\. Off-chip analog sensors & analysis ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) |   A. Code & data checks: Develop tests to detect code and data that are designed to spoof partial program re-execution with constraints (e.g. proof-of-learning) ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"); [Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  B. Workload modeling: Given an AI workload and cluster specs, estimate the optimal utilization (MFU) and the associated physical signature, e.g., power ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  C. Analog sensors: Design and manufacture appropriate analog sensors, or identify suitable existing tech ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  D. Tamper-proofing: Design and manufacture appropriate tamper-proof server enclosures ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). |
| --- | --- |
| Cross-cutting |   A. R&D funding (e.g., by AISIs, philanthropists, DARPA)  B. Pilot programs (e.g., voluntary corporate commitments, AISI collaborations)  C. Red teaming (e.g., by companies, ICs, NIST contest) of developed proposals |
| --- | --- |
|  |  |
| --- | --- |

Table 2: Selected open challenges in verification R&D. We discuss open problems more comprehensively ([Appendices](https://arxiv.org/html/2507.15916v2#Ax1 "Appendices ‣ Verifying International Agreements on AI"); [Appendix C.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx3 "C.3 Additional R&D Problems for Verification ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")); this list is filtered ([Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI")). These filters and the unclassified nature of this research result in the table not listing challenges for layers (4-6).

## 1\. Introduction

Cutting-edge AI systems are increasingly capable at varied tasks, raising their potential for benefits and harms. General-purpose AI systems have the potential to improve education, medicine, and research and prosperity more broadly, but continued progress in capabilities also could enable catastrophic misuse (e.g., in biological and cyber attacks) and accidents (e.g., via deployment of unreliable systems in high-stakes use cases, as well as loss of human control of highly intelligent systems) (Bengio et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib15), [2025a](https://arxiv.org/html/2507.15916v2#bib.bib16), [2025b](https://arxiv.org/html/2507.15916v2#bib.bib17); Ngo et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib144); Prime Minister’s Office, 10 Downing Street et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib170)).

To mitigate AI’s risks while reaping its benefits, verified AI regulations and international agreements may be needed. Rules may need to be enforced because even well-meaning actors face competitive incentives to deprioritize AI’s national security risks and other externalities (Armstrong et al., [2013](https://arxiv.org/html/2507.15916v2#bib.bib9); Askell et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib10); Ganguli et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib70)), and malicious actors may have little concern for unenforced rules. To enable timely and effective enforcement, verification of compliance is essential (Dai, [2002](https://arxiv.org/html/2507.15916v2#bib.bib46)).[^1] These benefits of verification arise in both international agreements and domestic regulation.

The shortage of rules on AI and verification of compliance is already motivating lowered safety standards and blunt policies. For instance, leading AI companies have in some cases fallen short of commitments to invest in safety (Kahn, [2024](https://arxiv.org/html/2507.15916v2#bib.bib113)), reportedly deprioritized “safety culture and processes” (Robison, [2024](https://arxiv.org/html/2507.15916v2#bib.bib175); Roose, [2024](https://arxiv.org/html/2507.15916v2#bib.bib176)), suppressed whistleblowers (Verma et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib219)), published safety frameworks lacking commitments (Dragan et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib55)), and rushed product releases (De Vynck et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib50); Gordon, [2024](https://arxiv.org/html/2507.15916v2#bib.bib80)). Nationally, both U.S. and Chinese lawmakers appear to be backing off from more ambitious proposals for regulating large-scale AI, as each government seeks to avoid falling behind the other in AI.[^2] With effective verification of risk mitigation practices globally, countries could have more confidence that caution on national security will not be exploited by corner-cutting in adversary countries. Meanwhile, the United States is controlling exports of high-end AI chips to over a dozen countries (Bureau of Industry and Security, [2023](https://arxiv.org/html/2507.15916v2#bib.bib27); Heim, [2025b](https://arxiv.org/html/2507.15916v2#bib.bib89)), affecting benign uses along with the targeted military uses. With effective verification of how exported chips are used rather than sweeping bans at a country level, American companies and other companies in the supply chain could potentially attain greater revenue, while still achieving the national security objectives that motivate sweeping bans.

As AI capabilities continue to advance, verification will likely become increasingly important. More capable AI systems will pose greater opportunities and risks, increasing the value of the incentives and precise enforcement ability brought by rules with verified compliance. Meanwhile, today’s debated view that AI poses risks on par with nuclear war (Hinton et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib95); Bengio et al., [2025a](https://arxiv.org/html/2507.15916v2#bib.bib16)) might become a consensus. Consider, for example, the potential scientific and political response to an AI-enabled terrorist attack, a near-miss crisis, or experimental results that provide clear evidence of severe AI threats. The historical responses to the 9/11 terrorist attacks (UN Security Council, [2001](https://arxiv.org/html/2507.15916v2#bib.bib212); Council on Foreign Relations, [a](https://arxiv.org/html/2507.15916v2#bib.bib42)) and to the Cuban Missile Crisis (International Atomic Energy Agency, [1998](https://arxiv.org/html/2507.15916v2#bib.bib104); Timerbaev, [2017](https://arxiv.org/html/2507.15916v2#bib.bib204)) suggest threats of such magnitude can motivate deep and relatively quick international cooperation, even among geopolitical rivals like the United States and Soviet Union. Even then, states might only cooperate if they can verify each other’s compliance with agreements.[^3]

_Confidentiality-preserving_ and secure verification of rules on _large-scale_ AI has unique potential. Historically, it has been politically crucial for international verification methods to avoid information leaks that create serious security risks, and (to a lesser extent) to avoid leaks of trade secrets (Coe and Vaynman, [2019](https://arxiv.org/html/2507.15916v2#bib.bib39); Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13)).[^4] The AI industry has an abundance of highly sensitive information, from AI model weights (Nevo et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib143)) and algorithms to training/user data. Confidentiality-preserving[^5] verification may be especially important and feasible for _large-scale_ AI development and deployment (Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187)), such as training a future, powerful model and deploying it at scale. Such large-scale AI activities carry unique risks (Bengio et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib15), [2025b](https://arxiv.org/html/2507.15916v2#bib.bib17); Prime Minister’s Office, 10 Downing Street et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib170)). They are also industrial, billion-dollar-scale undertakings (Henshall, [2024](https://arxiv.org/html/2507.15916v2#bib.bib93); Amazon Staff, [2024](https://arxiv.org/html/2507.15916v2#bib.bib5); Efrati and Holmes, [2024](https://arxiv.org/html/2507.15916v2#bib.bib58)), requiring “thousands of specialized chips” (Sastry et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib178)) and counting (Sevilla and Roldán, [2024](https://arxiv.org/html/2507.15916v2#bib.bib184)). This broad trend continues to hold despite algorithmic advances, such as those of reasoning models and DeepSeek’s R1 (Heim, [2025a](https://arxiv.org/html/2507.15916v2#bib.bib88)).

Despite the growing need for them, methods to verify rules on large-scale AI development and deployment are nascent, and they face major challenges. While some fields such as nuclear arms control have had decades to refine verification methods (Council on Foreign Relations, [b](https://arxiv.org/html/2507.15916v2#bib.bib43); Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)), large-scale AI’s growing capabilities only attained intense policy attention since 2023 (Henshall, [2023](https://arxiv.org/html/2507.15916v2#bib.bib92); Maslej et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib132)). In addition, AI verification is not straightforward: AI data centers might be hidden or dispersed, there is a large leap from locating a data center to determining how it is used, and simply examining public AI products would miss non-public violations (among other limitations).[^6] Further, verifying rules on large-scale AI will require obtaining assurances about a very complex and rapidly changing technology stack—semiconductors and AI (Khan et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib116))—against adversaries who may be extremely capable (Nevo et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib143)) and incentivized to circumvent verification.

While research has broken ground on AI verification, the field could use improved conceptual clarity and more developed proposals. From 2023 to 2025, there have been a handful of research papers explicitly studying frontier AI verification, from developing specific proposals to overviewing the landscape ([Appendix C.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx5 "C.5 Related Work ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")). This report was motivated by the view that progress on verification would benefit from improved clarity on important conceptual questions, in particular: how can specific verification mechanisms be combined effectively? How many distinct layers of redundancy could verification achieve? In addition, existing research has limited discussion of how some proposals could be implemented. This report aims to make progress on these fronts, by proposing clarifying frameworks and outlining new implementation options (especially for how hardware security features, compute accounting, and whistleblower programs could be used for effective verification).

The remainder of this report is structured as follows. [Section 2](https://arxiv.org/html/2507.15916v2#Sx3 "2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI") describes the scope of verification considered in this report and this report’s methodology. [Section 3](https://arxiv.org/html/2507.15916v2#Sx4 "3. Verification Framework ‣ Verifying International Agreements on AI") explains our framework of verification subgoals. [Section 4](https://arxiv.org/html/2507.15916v2#Sx5 "4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI") describes and analyzes potential verification mechanisms and layers. [Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI") lists open problems. [Section 6](https://arxiv.org/html/2507.15916v2#Sx7 "6. Conclusion ‣ Verifying International Agreements on AI") concludes.

### 1.1 Contributions

Our report primarily makes the following contributions:

1.  1.
    
    Verification goal ([Section 2](https://arxiv.org/html/2507.15916v2#Sx3 "2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")): We start by outlining a verification goal that is widely applicable for AI governance: verifying that large-scale AI development and deployment complies with rules, for rules on models, data, and code.
    
2.  2.
    
    Verification subgoals ([Section 3](https://arxiv.org/html/2507.15916v2#Sx4 "3. Verification Framework ‣ Verifying International Agreements on AI")): We identify four subgoals by which this goal can be achieved. A verification regime is only as robust as its weakest completion of a subgoal, so identifying subgoals helps us assess the robustness of verification proposals.[^7]
    
3.  3.
    
    Verification mechanisms and layers ([Section 4](https://arxiv.org/html/2507.15916v2#Sx5 "4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")): We identify over 20 verification mechanisms and analyze their challenges. These are the “building blocks” of verification regimes; each can help complete at least one of the above subgoals. We show how the verification mechanisms can be assembled into 6 distinct “layers” of verification, and we analyze these layers. By “verification layer,” we mean a set of similar mechanisms, with one mechanism for each verification subgoal.
    
4.  4.
    
    Open problems ([Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI")): We list open R&D problems for advancing AI verification.
    

For more details, readers may be interested in the following, mostly more technical contributions within the above, where we examine how under-explored verification mechanisms could be implemented:

-   •
    
    We outline approaches to implementing the following verification mechanisms, analyzing potential attacks and countermeasures:
    
    -   –
        
        Hardware-backed workload certificates, using secure boot ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"))
        
    -   –
        
        Compute accounting via analog sensors on AI chips ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"))
        
    -   –
        
        Whistleblower programs ([Appendix A.8](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx8 "A.8 Whistleblower Programs ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"))
        
    
-   •
    
    We highlight how verification of training can be generalized to verifying large-scale inference, considering replicability ([Appendix A.9](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx9 "A.9 Deterministic Replication of Neural Network Inference ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) and sensitive data storage ([Appendix A.10](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx10 "A.10 Storing Sensitive Data for Verification ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), and we outline additional tests to detect spoofs ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"); [Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    We explore in some detail the major challenge of ensuring verification protocols are implemented securely throughout the infrastructure stack ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    

### 1.2 Limitations

The verification mechanisms and layers we identify are not necessarily comprehensive, nor is our analysis of them. In addition, this report has various scope limitations ([Section 2](https://arxiv.org/html/2507.15916v2#Sx3 "2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")).

## 2\. Verification Scope and Research Methodology

### 2.1 Rules on AI Models, Data, and Code

This report covers options for verifying compliance with rules on the _AI models, data, and code_ created or used in large-scale AI development and deployment. That is, if a rule can be specified in terms of measurable properties of these AI models, data, and code,[^8] [^9] the options we cover should allow verifying compliance with the rule. This covers many hypothetical rules for (near-)frontier AI (Table 3).[^10] These rules may seem quite different, but much of the challenge of verifying is the same: identifying what models, code, and data were used for large-scale AI development and deployment, so one can run desired tests on them. Still, we do not necessarily cover verifying compliance with rules on other AI-related matters, such as the general cybersecurity of AI companies or their ownership structures, though some of the mechanisms we review could help there too.[^11] Note that precisely specifying rules that meaningfully achieve security or other governance objectives is a critical open challenge beyond this report’s scope ([Section 2.3](https://arxiv.org/html/2507.15916v2#Sx3.SSx3 "2.3 Other Scope Limitations ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")).

| Potential governance goal | Hypothetical rule (using “frontier model” as shorthand for AI models trained with large-scale AI compute ([Section 2.2](https://arxiv.org/html/2507.15916v2#Sx3.SSx2 "2.2 Rules on Large-Scale AI Compute ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI"))) | How the rule could be specified as a rule on AI models, data, and code (illustrative, high-level) |
| --- | --- | --- |
| Safety & security | Model evaluations: Regularly test frontier models for risks to international security. | Models and outputs in deployment could be evaluated for dangerous capabilities and propensities, at regular intervals of training compute or benchmark performance. |
| --- | --- | --- |
|  | Deployment mitigations: Implement risk mitigation practices for large-scale frontier AI deployment. | Mitigations may often be specifiable in terms of input data and output data (e.g., filter out some kinds of inputs, run oversight checks on outputs), proportionately to evaluated risks. |
| --- | --- | --- |
|  | Development mitigations: Implement risk mitigation practices in frontier AI development. | Mitigations could be practices for model architectures, training data, and code, proportionate to evaluated risks. |
| --- | --- | --- |
|  | Halts: Refrain from further development or large-scale deployment of a model while it would pose unmanageable security risks. | Further development would create a new model with higher performance and a suspect training history. Further deployment would create new output data from the risky model. |
| --- | --- | --- |
| Transparency | Disclosures: Publicly disclose all frontier models, their training compute, and/or evaluation results. | Training compute is a function of model architecture and training data, and the other rules here are about models. |
| --- | --- | --- |
| Benefit-sharing | Sharing claimed models: Share access to a specific model internationally. | Output data from remote deployment are in fact generated by a model with claimed specifications and performance, run on the intended input data. |
| --- | --- | --- |
|  | Sharing leading models: Share access to one’s best-performing models internationally. | As above, output data from remote deployment are in fact generated by a model with claimed specifications and performance, run on the intended input data. Further, the model outperforms the developer’s other models. |
| --- | --- | --- |
| Arms control | Military limits: Restrict frontier models specialized for military purposes | Restrictions may be specifiable by limits on data (e.g., use of weapons data), though small-scale AI may often suffice for narrow applications. |
| --- | --- | --- |
| Usage norms | International norms: Deploy large-scale AI while meeting norms beyond safety & security. | Mass-deployed models could have fine-tuning data, input filters, etc. that promote norms such as upholding international agreements, individual rights, and truthfulness. |
| --- | --- | --- |
|  |  |  |
| --- | --- | --- |

Table 3: Examples of potential rules on AI, in-scope for this report.

### 2.2 Rules on Large-Scale AI Compute

Large-scale AI—motivation. This report focuses on options for verifying that large-scale AI development and large-scale AI deployment complies with rules. These activities involve unique risks and scale of resource use ([Section 1](https://arxiv.org/html/2507.15916v2#Sx2 "1. Introduction ‣ Verifying International Agreements on AI")), so verifying their compliance could be both important and practical. In contrast, verifying small-scale compute use could require intruding more into lower-performance compute clusters and even consumer hardware. Verifying small-scale compute use would also require more precise verification methods.[^12]

Large-scale—definitions. We define “large-scale” with a few corresponding terms, chosen to approximately track the compute use of near-frontier AI development over time (Epoch AI, [2024b](https://arxiv.org/html/2507.15916v2#bib.bib60)) ([Section 3.3](https://arxiv.org/html/2507.15916v2#Sx4.SSx3 "3.3 Addressing Broader Challenges for Verification ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")):[^13]

-   •
    
    A _compute cluster_ or data center is “large-scale” if it has the computing power of thousands of high-end AI chips (even if the chips are distributed over many locations).[^14]
    
-   •
    
    _Compute use_ is “large-scale” if it is an amount of computation that thousands of high-end AI chips can do over multiple months.[^15] [^16]
    
-   •
    
    _AI development or deployment_ is “large-scale” if it uses thousands of high-end AI chips over multiple months.
    

Though this report uses the more general definition of “thousands” of AI chips, it may be practical to limit verification to an even higher threshold, such as hundreds of thousands of AI chips, as frontier AI development is already near that scale and growing as of early 2025 (Epoch AI, [2024b](https://arxiv.org/html/2507.15916v2#bib.bib60); Pilz et al., [2025b](https://arxiv.org/html/2507.15916v2#bib.bib168)).

Small-scale compute use. Due to this report’s focus on large-scale AI compute use, the verification options we cover do not necessarily enable verifying rules on small-scale AI compute use, i.e., the development of small (typically narrow-purpose) models or the small-scale deployment of frontier models. Other compute-centric governance approaches share this scope limitation (Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187); Sastry et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib178)). This could be seen as a feature, as it limits the potential for government overreach. At the same time, this gap has downsides; it is not clear that frontier AI deployment must be done at scale to be dangerous. Still, two of the verification layers we consider might enable verifying rules even on small-scale deployment of frontier AI models.[^17]

### 2.3 Other Scope Limitations

As further scope limitations, this report primarily:

-   •
    
    Identifies concrete R&D challenges, leaving open the R&D work to solve them if possible.
    
-   •
    
    Focuses on verifying compliance with rules, rather than specifying rules well—another important unsolved problem (which includes improving model evaluations) ([Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI")).[^18]
    
-   •
    
    Examines verification protocols, not what organizations should carry them out.
    
-   •
    
    Focuses on verification as in detecting non-compliant parties (Dai, [2002](https://arxiv.org/html/2507.15916v2#bib.bib46)), after which one still needs to penalize or stop them ([Section 3.3](https://arxiv.org/html/2507.15916v2#Sx4.SSx3 "3.3 Addressing Broader Challenges for Verification ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")).[^19] We do not cover this latter step of enforcement, though a few verification mechanisms double as enforcement tools.[^20]
    

### 2.4 Methodology

#### 2.4.1 Sources

Literature review. We reviewed a range of open sources—primarily research reports from academic, industry, and think tank sources—in relevant fields.[^21] [^22] [Appendix C.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx5 "C.5 Related Work ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI") provides a more detailed list of areas we examined, including key search terms and major sources.

Expert interviews ([Appendix C.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx2 "C.2 Methodology for Expert Interviews and Interview Protocol ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")). We conducted 18 semi-structured interviews with a range of subject-matter experts[^23] to validate our findings. In our interviews, we asked these experts to highlight possible errors or omissions in our findings, or to answer narrower technical questions.

#### 2.4.2 Methodology for Analysis

Our analytic methodology, detailed in [Appendix C.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx1 "C.1 Methodology for Analysis ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI"), consisted of:

1.  1.
    
    Developing a framework of verification subgoals: We took as a starting point a framework used by the International Atomic Energy Agency (IAEA), identified through our literature review, and modified it until it met our criteria of deductive validity, flexibility, and simplicity.
    
2.  2.
    
    Identifying verification mechanisms: We identified candidate verification mechanisms by compiling verification mechanisms from the above sources.
    
3.  3.
    
    Assessing, red teaming, and enhancing verification mechanisms; and identifying open problems: We evaluated each mechanism’s effectiveness, rate of false alarms, confidentiality, security, setup speed, and cost, while iterating on outlined implementations. These analyses drew from the literature review and expert interviews.
    
4.  4.
    
    Identifying and analyzing verification layers: We grouped the more positively assessed mechanisms into layers, using our above analysis and definition of verification layer.
    

## 3\. Verification Framework

### 3.1 Context for This Framework

![Refer to caption](https://arxiv.org/html/2507.15916v1/x3.png)

Figure 3: Assumed context for verification: verification is preceded by declarations and can lead to enforcement.

A Prover and a Verifier. We consider a “Prover” who is trying to prove their compliance to a “Verifier,” drawing these terms from computer security (Goldwasser et al., [1985](https://arxiv.org/html/2507.15916v2#bib.bib76)). The Prover could be a private institution or (in the case of international agreements) a government, which could constrain private companies within its territory as part of the agreement. The Verifier could be a government body or a third party.[^24]

Framework structure and assurances. This report’s framework breaks down verification into various subgoals, each of which consists of verifying some claim. By verifying all the claims in the framework, the Verifier can be confident in the Prover’s compliance. This is because, by design ([Appendix C.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx1 "C.1 Methodology for Analysis ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")), if all the claims in the framework are true, then it will logically follow that the Prover cannot have used large-scale AI compute in a non-compliant manner.[^25]

AI compute accounting. The framework not only has large-scale AI compute use as its scope but also takes the approach of AI compute accounting; it seeks to verify compliance on the basis that all large-scale AI compute use is accounted for in compliant activities. One could hypothetically attempt to instead account for the use of other resources associated with large-scale AI compute use, such as electrical power or algorithms. Compared to AI compute, these other resources have broader uses (e.g., the many uses of electrical power), or they have much smaller physical footprints (e.g., the smaller spaces taken up by stored data or algorithms) ([Appendix B.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx2.SSSx1 "B.1 Compute Accounting vs. Other Kinds of Accounting ‣ B. Broader Regime Design ‣ Appendices ‣ Verifying International Agreements on AI")). These factors suggest that AI compute use can be accounted for less intrusively than other resources.

### 3.2 The Framework

Our verification framework breaks down verifying the compliance of large-scale AI models, data, and code into subgoals, each of which is verifying some claim. These subgoals can be used to design or evaluate options for verifying rules on AI.

Declarations. The framework involves requirements for organizations to confidentially self-report, or “declare,” information. In this framework, organizations that own or use large-scale AI compute (e.g., major AI companies and cloud compute providers) would be required to declare facts about (i) their _ownership_ of large AI compute clusters (or large, decentralized quantities of AI compute),[^26] and (ii) their _use_ of large AI compute clusters. Verification focuses on checking that these declarations are correct and complete.[^27] The declarations would include model weights, training and usage data, and training code, as well as other information required by verification protocols (e.g., intermediate results of computations, information about hardware utilization). We define “large-scale” compute use in terms of thousands of AI chips ([Section 2.2](https://arxiv.org/html/2507.15916v2#Sx3.SSx2 "2.2 Rules on Large-Scale AI Compute ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")), but this is imprecise; policymakers could define more precise thresholds (and update them over time) based on future learnings about what scale of AI compute use warrants verification and is practically verifiable.

Use of confidentiality-preserving technology. Importantly, in our framework, declarations of AI compute use would be reported and verified via confidentiality-preserving technology—technology that enables a Prover to demonstrate their compliance without leaking their highly sensitive IP such as model weights. Such technology could include (i) a hardware security feature known as Confidential Computing ([Section 4.1.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx1.Px1 "4.1.1.1 Prerequisites: Hardware Security Features ‣ 4.1.1 Mechanisms ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")); and (ii) compute clusters with security that both parties can confirm, so that much information can enter these devices but only a small amount of information (e.g., compliance determinations) can leave ([Section 4.2.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px1 "4.2.1.1 Prerequisites: Off-Chip Devices ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). Declarations of AI compute ownership are less sensitive than declarations of AI compute usage,[^28] but, if desired, the confidentiality-preserving technologies we discuss could also help protect these ownership declarations. As we will discuss ([Section 4.5](https://arxiv.org/html/2507.15916v2#Sx5.SSx5 "4.5 Implementation Options Across Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), confidentiality-preserving technologies could be used to run hard-coded compliance tests, or perhaps to facilitate iterative testing by humans or AI agents, though the human option poses more confidentiality challenges.

![Refer to caption](https://arxiv.org/html/2507.15916v1/x4.png)

Figure 4: Framework of verification subgoals.

Subgoals for verifying rules on large-scale AI: The framework begins with a broad verification goal: verifying that AI models, data, and code comply with rules on large-scale AI development and deployment. The framework decomposes this goal into two subgoals: (1) verify that _declared_ uses of large-scale AI compute are compliant, and (2) verify that there are no _undeclared_ uses of large-scale AI compute (i.e., declarations are complete). “Compliant” here refers to compliance with rules on the AI models, data, or code created or used in large-scale AI development and those used in deployment ([Section 2](https://arxiv.org/html/2507.15916v2#Sx3 "2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")). This is a valid decomposition; if declared large-scale uses are compliant and there are no undeclared large-scale uses, then _all_ large-scale uses of AI compute must be compliant.[^29] These two subgoals can be decomposed further:

-   •
    
    Subgoal 1: verifying that declared uses of large-scale AI compute are compliant, faces two problems: a Prover might make a false declaration, or they might make a declaration that is honest but still non-compliant. “Honest but non-compliant” might mean, for example, openly declaring their AI deployment and hoping that a Verifier fails to notice that it lacked a required approval, or honestly declaring data that contains prohibited biological sequence data. Addressing each of these possible violations, we can break down Subgoal (1) into:
    
    -   –
        
        Subgoal 1.A: Verify that declared uses of AI compute are declared accurately, i.e., the Prover actually did the claimed development or deployment. Equivalently,[^30] verify that declared AI models and outputs are generated as declared. More specifically, a Verifier could need to verify the accuracy of declared (1.A.1) AI training, (1.A.2) AI inference, or (1.A.3) non-AI uses of AI compute.
        
    -   –
        
        Subgoal 1.B: Assuming that the declared uses are accurate (as is verified per Subgoal 1.A), verify they have the required properties. For example, the Verifier might evaluate an AI model’s capabilities, or assess what kinds of data the model was run on, to check for compliance. The substance of these tests would depend on what rules are being verified ([Section 2.1](https://arxiv.org/html/2507.15916v2#Sx3.SSx1 "2.1 Rules on AI Models, Data, and Code ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")), though as we will discuss, the infrastructure for running tests could be rule-agnostic.
        
    
-   •
    
    Subgoal 2: verifying that there are no undeclared uses of large-scale AI compute, also faces two problems: a Prover might try to make undeclared, large-scale uses of declared AI compute clusters, or of undeclared AI compute clusters. The Verifier can guard against both of these problems:
    
    -   –
        
        Subgoal 2.A: Verify that there are no undeclared, large-scale uses of declared AI compute clusters. In other words, ensure AI compute use is accounted for, among declared AI compute clusters.
        
    -   –
        
        Subgoal 2.B: Verify that there are no undeclared, large-scale AI compute clusters that could be used for violations. (Recall that we include large-scale, decentralized AI compute here ([Section 2.2](https://arxiv.org/html/2507.15916v2#Sx3.SSx2 "2.2 Rules on Large-Scale AI Compute ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")).) This subgoal can be further broken down into verifying there are no such AI compute clusters (2.B.1) as parts of known AI data centers, nor (2.B.2) as standalone clusters.[^31]
        
    

Verification subgoals can be completed in parallel. Verifiers could speed up verification by completing multiple subgoals in parallel. For example, the Verifier could check for undeclared AI compute clusters and check for false usage reports at the same time.

Verification subgoals can help design or evaluate verification regimes. Knowing what mechanisms may complete each verification subgoal ([Figure 2](https://arxiv.org/html/2507.15916v2#Sx1.F2 "Figure 2 ‣ Key Findings ‣ Summary ‣ Verifying International Agreements on AI")), one can in principle design a robust verification regime by selecting robust mechanisms for each subgoal. Additionally, the verification subgoals can help evaluate the robustness of a proposed verification regime. One can identify what mechanisms a regime uses for completing each subgoal, and then identify the subgoal whose mechanisms are collectively least robust. This subgoal is the “weak link” of the regime—its robustness determines the regime’s overall robustness.[^32]

Verification of narrower claims. Completing all the subgoals allows for verifying fairly broad claims: claims about large-scale AI development _and_ deployment, even claims about what large-scale AI development or deployment was _not_ done. Some subgoals could be skipped or simplified if one only wished to verify narrower claims ([Appendix B.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx2.SSSx2 "B.2 Verification of Narrower Rules ‣ B. Broader Regime Design ‣ Appendices ‣ Verifying International Agreements on AI")), such as positive claims about how large-scale compute was used, or claims just about AI development.

### 3.3 Addressing Broader Challenges for Verification

Beyond implementing specific verification mechanisms, international verification faces broader questions and challenges, including: increasingly efficient compute, enforcement, ambiguous findings, and attribution. These challenges may be manageable (Table 4).

| Broader challenge | Options (non-comprehensive) |
| --- | --- |
| Managing increases in effective compute: What to do about the trend that violations will become easier over time, as AI chips are produced in larger quantities, with higher performance, and used with more efficient algorithms? | Because of the mentioned trends, it is likely unviable to _indefinitely_ prevent violations with a specific amount of compute or specific AI capabilities. Instead, defensive measures will likely be needed eventually (Pilz et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib166); Bernardi et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib18)). Thus, the role of verification could be to oversee the (near-)frontier of AI capabilities—to ensure the newest AI capabilities are understood and leveraged defensively, before they proliferate. If more time were needed to prepare defenses, a costly option could be to extend verification’s viability by slowing the increase in effective compute, namely through rules on AI hardware manufacturing and acquisition, and perhaps on computationally expensive AI algorithmic experiments. |
| --- | --- |
| Specifying rules to be verified: How can AI governance goals be operationalized as technical rules on models, data, and code? | Existing efforts to translate high-level policy concerns into concrete technical rules should continue and accelerate ([Section 2.1](https://arxiv.org/html/2507.15916v2#Sx3.SSx1 "2.1 Rules on AI Models, Data, and Code ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI"); [Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI")). This translation poses significant challenges: technical rules like “model trained with fewer than X FLOP” or “model scores Y on benchmark” may not fully capture policy goals like “preventing harmful capabilities.” Rules should ideally narrowly target harmful AI development and deployment while minimizing constraints on beneficial uses. When precise targeting is impossible, conservative thresholds may be needed but should be periodically reassessed as our understanding improves. Processes involving technical experts, policymakers, and affected stakeholders could help develop rules that better align with governance goals. |
| --- | --- |
| Taking enforcement actions: In an international agreement, what should parties do if they find that another party is seriously violating the agreement? | Options include: reciprocating non-compliance, using non-technical enforcement actions (e.g., sanctions, export controls, withdrawal of security guarantees and of AI benefit-sharing, cyber or kinetic attacks) (Sastry et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib178); Dennis et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib52); Hendrycks et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib91)), and (if available) using technical mechanisms for enforcement (Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121); Petrie et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib164)). Due to their mutual costs, these options would ideally be effective deterrents and thus never carried out. |
| --- | --- |
| Attaining relevant parties’ participation: How to attain compliance commitments from all states that host large-scale AI compute (as such states could directly misuse it or rent it to an agreement party)? | States could: use export controls and energy policy to keep AI hardware concentrated in cooperative states (Sastry et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib178); Pilz et al., [2025a](https://arxiv.org/html/2507.15916v2#bib.bib167)), use international dialogues and collaborations to build consensus (FAR.AI, [2024](https://arxiv.org/html/2507.15916v2#bib.bib66); Bengio et al., [2025a](https://arxiv.org/html/2507.15916v2#bib.bib16)), and use the leverage listed in the above row. |
| --- | --- |
| Acting on ambiguities: What should be done if the Verifier encounters ambiguous indicators of a potential violation? | As increasingly escalatory and costly options, the Verifier could: request clarifications, carry out focused investigations, demand the narrow application of more intrusive verification measures, demand temporary pauses of AI compute clusters, or impose partial penalties ([Appendix B.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx2.SSSx3 "B.3 Acting on Ambiguous Findings ‣ B. Broader Regime Design ‣ Appendices ‣ Verifying International Agreements on AI")). |
| --- | --- |
| Attributing violations: How to determine whether a cloud provider or a compute user is to blame for a violation, and whether a corporate violation of international rules is government-backed? | Attribution could potentially be done via reporting requirements. With appropriate communication channels, a cloud provider or host government may be reasonably expected to detect violations on their compute/territory more quickly than an international Verifier and to report them. Thus, reporting could indicate that the reported party is complicit; failure to report could indicate that the party with reporting responsibilities is complicit. |
| --- | --- |
|  |  |
| --- | --- |

Table 4: Some broader challenges for verification and high-level options to address them.

## 4\. Verification Mechanisms and Layers

Having clarified our verification scope ([Section 2](https://arxiv.org/html/2507.15916v2#Sx3 "2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")) and subgoals ([Section 3](https://arxiv.org/html/2507.15916v2#Sx4 "3. Verification Framework ‣ Verifying International Agreements on AI")), we now turn to overviewing mechanisms and layers by which these subgoals can be achieved. This section will overview verification mechanisms and layers together, explaining six potential layers by describing the mechanisms that would make them up.

Defining verification mechanisms and layers. We define terms as follows:

-   •
    
    A verification _mechanism_ is a method or technology that helps complete at least one of the subgoals in our verification framework ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")).[^33] An example verification mechanism is inspecting AI chips to verify that they have not been sent to undeclared AI data centers; this helps complete Subgoal 2.B.
    
-   •
    
    A verification _layer_ is a collection of similar verification mechanisms, with one mechanism for each verification subgoal. An example is a comprehensive set of “on-chip” verification mechanisms, as described below. In other words, a verification layer is a set of similar[^34] mechanisms capable of end-to-end verification (i.e., completing all subgoals) without redundancy (i.e., without having multiple mechanisms for the same subgoal). As a result, three verification layers can be stacked together to achieve three layers of redundancy, for example.[^35]
    

### 4.1 On-Chip Verification Layer

| Potential verification layer | Summary of layer | Key  
advantages | Key disadvantages |
| --- | --- | --- | --- |
| On-chip security features (i.e., secure boot, Confidential Computing)![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image5.png) | Security features built into AI chips may enable verification, such as by ensuring that AI chips log traces of their activities for confidential analysis. | Offers maximum transparency into AI chips’ uses. | Poses unsolved technical problems and severe security challenges (e.g., untrusted suppliers). Insecure AI chips may need to be replaced. |
| --- | --- | --- | --- |
|  |  |  |  |
| --- | --- | --- | --- |

Table 5: Summary of the on-chip verification layer and its tradeoffs.

![Refer to caption](https://arxiv.org/html/2507.15916v1/x5.png)

Figure 5: Summary of how the on-chip verification layer would complete each subgoal.

In the “on-chip” verification layer, the Prover’s AI chips _help_ _verify their own compliance_ through built-in security features. In other words, this verification layer distinctively assumes (and tries to verify) that the Prover’s AI chips will implement specialized behaviors that enable verification, due to features physically built into the chips during manufacturing. To achieve robust verification with hardware security features, some already common hardware security features would need to be (i) present on the Prover’s chips, (ii) unusually secure, and (iii) used in particular ways. We describe these features and their uses next.

#### 4.1.1 Mechanisms

##### 4.1.1.1 Prerequisites: Hardware Security Features

The verification mechanisms we consider require a hardware security feature known as secure boot, which must be at least tamper-evident (i.e., impractical to discreetly disable or undermine). They would further benefit from Confidential Computing and tamper-proofing, though these are not required.

Secure boot: Secure boot aims to guarantee that a chip will only run with approved[^36] system software (i.e., firmware and operating system). System software can constrain a chip’s behavior throughout operation, so secure boot could be used to ensure that a chip will always behave in ways that facilitate verification. Secure boot implementations are especially promising for this if they: (i) are at least tamper-evident, with regards to both physical and digital tampering (so, unless they are also tamper-proof, random inspections would be needed to check for tampering);[^37] and (ii) include a secure private key,[^38] allowing the system software to digitally sign messages.

Confidential Computing: Confidential Computing is a hardware feature that, among other uses, can allow multiple parties to share their information only for specific purposes. This could enable a Verifier to run tests on a Prover’s models, data, and code—with the Prover knowing their information will not be stolen, and with the Verifier knowing their tests will be run faithfully and will not be viewed for the sake of manipulating test results.[^39]

Confidential Computing (or more precisely, one of its functionalities[^40]) is intended to work as follows. First, multiple parties share their encrypted data, giving access only to a specific computer program on specific hardware. (They can scrutinize this program’s code in advance.) Then, hardware features ensure the program is executed faithfully and without leaks. Finally, a digital signature confirms that the test results came from this approved program (Confidential Computing Consortium, [2021](https://arxiv.org/html/2507.15916v2#bib.bib41); [Google Cloud,](https://arxiv.org/html/2507.15916v2#bib.bib79) ).

There are existing, though likely limited, implementations and uses of Confidential Computing, which includes secure boot (NVIDIA, [2023b](https://arxiv.org/html/2507.15916v2#bib.bib153)). AI chip designers including NVIDIA (NVIDIA, [2023b](https://arxiv.org/html/2507.15916v2#bib.bib153)), Huawei (Dhar et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib54)), Graphcore (Vaswani et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib218)), and Google (Chuvakin and Porter, [2021](https://arxiv.org/html/2507.15916v2#bib.bib36); Dragan et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib55)) have in recent years implemented or announced plans for versions of Confidential Computing. The UK AI Security Institute has used some of these implementations in a pilot program to run confidential AI safety evaluations with Anthropic and OpenMined (Trask et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib207); Beers and Toner, [2025](https://arxiv.org/html/2507.15916v2#bib.bib14)). However, as discussed below, there are reasons to expect current implementations to be hackable (Table 6).

##### 4.1.1.2 Verification Mechanisms

Secure boot and Confidential Computing could be used to implement the following verification mechanisms.

Hardware-backed workload certificates and evaluations ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")): The Prover’s chips could sign cryptographic certificates that confirm how they produced their results—confirming model histories, output histories, and evaluation results. For example, a certificate could attest that some trained AI model was produced using specific code and data. Similarly, a certificate could attest that some AI model outputs such as generated text were produced by a specific model on specific inputs. A limited version of this has already been developed and open-sourced (Security, [2023](https://arxiv.org/html/2507.15916v2#bib.bib183)). Secure boot may be able to ensure that these workload certificates are not only authentic but also comprehensive: that a Prover could not simply delete a certificate or refrain from making it. We outline a potential technical implementation for such comprehensive workload certificates ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), relying on permanent secure boot. This mechanism could complete verification Subgoals 1.A, 1.B, and 2.A. In addition to the security of the hardware features, their operation—especially identifying model weights and data that may be obfuscated—poses challenges.

Tamper-proof, compliance-locked AI chips: AI chips could potentially be compliance-locked (i.e., refuse to run non-compliant workloads) and tamper-proof.[^41] This would assure the Verifier that, even if the Prover has an undeclared AI compute cluster, they would be unable to use it in non-compliant ways. Thus, tamper-proof, compliance-locked AI chips would address undeclared AI compute clusters (Subgoal 2.B), a gap left by the above workload certificates. Compliance-locking could be implemented by combining the above workload certificates with offline licensing (Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121)),[^42] or more ambitiously, through entirely automated on-device checks. However, tamper-proofing’s use in AI governance faces major technical challenges (Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121); Aarne et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib2)) and serious tradeoffs ([Section 4.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx2 "4.1.2 Analysis ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).

#### 4.1.2 Analysis

On-chip mechanisms offer maximal transparency into AI chips’ computations. By using security features built into AI chips, on-chip mechanisms directly offer transparency into AI chips’ code and data, with measures to preserve confidentiality. In contrast, other verification layers only examine AI chips “from the outside.” That is, other layers must infer AI chips’ behavior based on external measurements or personnel, which creates room for circumvention and imprecision. Those challenges are significant ([Section 4.2.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx2 "4.2.2 Analysis ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), and on-chip verification avoids them entirely.

Compliance-locking offers limited verification redundancy, and it carries the pros and cons of enforcement. One of the above mechanisms, compliance-locked AI chips, offers technical assurances only after a less technical setup phase: tracking down chip fabrication facilities and perhaps older AI compute clusters, likely by non-technical mechanisms and satellite images ([Section 4.3](https://arxiv.org/html/2507.15916v2#Sx5.SSx3 "4.3 Personnel-Based Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"): [Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). Thus, compliance-locking is only partly redundant with other verification layers’ completion of Subgoal 2.B. The more significant consequence of compliance-locking may be its built-in enforcement function, which would facilitate preventing violations but raises risks of adversarial use (Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121)). Still, there are proposals to mitigate these risks (Petrie et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib164)), including through enforcement requiring multi-party approval. A similar analysis applies to compliance-locked server enclosures ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). There are also options with more intermediate tradeoffs, e.g., offline licensing could be set up so that the Verifier has visibility but not veto power.[^43]

On-chip verification faces severe, unsolved hardware security challenges (Table 6). Relevant security features in the current and next generation of AI chips appear unlikely to be robust; their track records and security practices are lacking. Improving matters appears challenging, as there are major, inherent challenges in developing robust hardware security features for AI chips or other high-performance chips.

| Challenge for attaining confidence in AI chips’ hardware security features[^44] | Description |
| --- | --- |
| Mixed track records | Hardware security features have a track record that is mixed at best. There have been multiple cases of individual, low-budget researchers circumventing the hardware security features of leading companies.[^45] On the other hand, some track records have improved in recent years.[^46] |
| --- | --- |
| Lacking security practices | Most high-performance chips, including AI chips, appear to be designed contrary to important security practices, such as external red teaming by leading security experts[^47] and use of Hardware Security Modules (HSMs).[^48] |
| --- | --- |
| Performance-security tradeoffs | There are often tradeoffs between a chip’s performance and its security, incentivizing higher performance and faster releases at the expense of security.[^49] |
| --- | --- |
| Untrusted supply chains | Chips may have designers and manufacturers whom the Verifier does not trust (especially for hypothetical U.S.-China verification). This introduces many attack vectors, perhaps addressable with extensive design disclosures and hardware verification ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). |
| --- | --- |
| Untrusted operational environments | Chips’ physical and digital environments may be controlled by untrusted actors, enabling more attack vectors, though physical and digital attacks could be countered by physical monitoring (e.g., tamper-evident security cameras ([Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"))) and secure design, respectively. |
| --- | --- |
| Lack of adaptability | Hardware-level security vulnerabilities typically cannot be fixed after manufacturing, though some firmware vulnerabilities can be fixed.[^50] Replacing AI chips that have flawed security features could require replacing millions of expensive chips.[^51] |
| --- | --- |
|  |  |
| --- | --- |

Table 6: Challenges for attaining confidence in AI chips’ hardware security features. The first two rows cover current or historical problems, and the remaining rows cover inherent challenges.

Hardware security challenges are especially severe with on-chip verification. While hardware security challenges arise for any verification method that uses hardware, these challenges are uniquely severe for on-chip verification. On-chip verification uses the same chips to both run and verify AI workloads. This inherently creates tradeoffs; if one wants to tighten the security of the hardware security features, one might have to delay, replace, or change the supply chain of the whole AI chip, which goes against commercial incentives. Perhaps these challenges could be overcome ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), but absent major effort (up to replacing millions of insecure AI chips), on-chip mechanisms will likely have irreparable design flaws that allow them to be circumvented, especially for complex or dynamic mechanisms. Still, such efforts may be feasible on longer timeframes (e.g., after initially using more implementation-ready verification methods), and it is possible that existing on-chip mechanisms are secure enough despite their challenges.

To avoid the tradeoffs of on-chip verification, another approach could be to separate AI hardware from verification hardware, so that each can be specialized for its own purpose. This motivates the “off-chip” verification layers we consider next.

### 4.2 Off-Chip Verification Layers

| Potential verification layer | Summary of layer | Key  
advantages | Key disadvantages |
| --- | --- | --- | --- |
| Off-chip network tap (and analysis) (e.g. “FlexHEGs”)![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image2.png) | Mutually vetted devices could intercept data exchanged between chips, then check for discrepancies with declared uses. | Could be retrofitted to existing AI chips and optimized for security. | Poses technical, logistical, and security challenges. Strongest versions need redesigned chip-adjacent hardware. |
| --- | --- | --- | --- |
| Off-chip analog sensors (and analysis, e.g., proof-of-learning)![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image1.png) | Physically secured chips could check that (i) declared AI compute uses are accurate (e.g., reproducible) and (ii) their compute use adds up to the expected total (estimated with analog sensors, e.g., power meters, in AI data centers). | Could be retrofitted to existing AI chips and optimized for security. | Poses unsolved technical problems. Likely requires separate trusted clusters for analysis, and manufacturing & installing sensors. |
| --- | --- | --- | --- |
|  |  |  |  |
| --- | --- | --- | --- |

Table 7: Summary of off-chip verification layers and their tradeoffs.

![Refer to caption](https://arxiv.org/html/2507.15916v1/x6.png)

Figure 6: Summary of how off-chip verification layers would complete each subgoal. Note “verifying AI chips’ chain of custody“ and “tamper-proof, compliance-locked AI servers“ could just as well be swapped; the point is that they are two redundant off-chip mechanisms for addressing hidden AI compute clusters. We consider them “off-chip“ because they neither rely on features built into chips nor on leaks or disclosures from personnel. Additionally, tamper-proof enclosures and security cameras for chain-of-custody verification could be considered off-chip devices.

“Off-chip” verification layers aim to avoid the security challenges of on-chip mechanisms by verifying AI chips’ activities using _separate devices_, rather than security features built into the AI chips. These separate devices could be (i) attached sensors to monitor the AI chips, and (ii) separate chips to analyze the sensor data and Provers’ declarations. With these, the Verifier would aim to detect discrepancies between a Prover’s declarations and their actual chip use, such as by detecting that chips’ input data or power draw patterns tell a different story than the Prover’s claims. The external devices could be mutually vetted to enable trust.

#### 4.2.1 Mechanisms

##### 4.2.1.1 Prerequisites: Off-Chip Devices

This section overviews, in broad terms, potential off-chip devices to collect or analyze data in AI data centers.

Devices for data collection: Devices could collect digital data or analog readings on AI workloads, offering redundancy and different tradeoffs (Table 7):

-   •
    
    _Off-chip input/output loggers_ (i.e., network taps): Devices that read and log (a random sample of) digital data, such as data exchanged between AI servers or potentially between individual AI accelerators ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    _Off-chip analog sensors:_ Devices that log analog measurements, such as power draw, temperature, and electromagnetic measurements ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    

Mitigating security challenges: Without strong precautions, network taps or analog sensors could be designed with hidden functionalities for espionage or sabotage. To demonstrably prevent this, states could take measures such as the following to secure these devices, though these would be challenging:

-   •
    
    All parties could agree to use device designs that are: the same across parties, as simple as possible, mutually vetted, open-source, and perhaps jointly developed.
    
-   •
    
    Provers could verify that these vetted devices are actually used with no additions, by physically scanning the devices (with more intensive tear-downs for a random sample) and overseeing the devices’ manufacturing and assembly ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Provers could physically limit these devices’ communication to agreed-on data quantities and data contents.[^52]
    

Conversely, for Verifiers to be confident in the devices’ integrity, they could rely on measures such as Verifier-trusted supply chains, mutual vetting (similar to Provers’ vetting), tamper-evident enclosures (a random sample of which would be routinely inspected[^53]), and ideally tamper-proofing.

Devices for data analysis: Beyond devices for collecting data, collected data could be analyzed by trusted computer chips, either on-site or off-site. For on-site chips, both parties could gain confidence through measures similar to the above, though full device scanning and design disclosures would be more challenging ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). For off-site chips, which could form _trusted clusters_,[^54] security could be based on both the Prover and the Verifier directly applying security measures for their respective goals. The Prover would monitor and restrict the cluster’s external communications—ensuring that only the expected amount of information is extracted (Greenblatt, [2024](https://arxiv.org/html/2507.15916v2#bib.bib82)).[^55] [^56] The Prover would also supervise the cluster’s use. Meanwhile, the Verifier would ensure the cluster’s integrity by providing, physically securing, and securely operating the chips and other IT equipment.

##### 4.2.1.2 Verification Mechanisms

Off-chip devices could be used to complete verification subgoals with redundancy as follows ([Figure 6](https://arxiv.org/html/2507.15916v2#Sx5.F6 "Figure 6 ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).

Off-chip network taps & analysis ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")): Mutually vetted devices could log a random sample of the data exchanged between different parts of a compute cluster, such as the data transmitted between server racks, between servers, or potentially between individual AI chips. Analysis of these logs may reveal discrepancies between actual AI chip communications and what would be expected from declared workloads, serving to verify the accuracy of a declared workload (Subgoal 1.A) and the absence of major undeclared workloads on known AI compute clusters (Subgoal 2.A). A closely related proposal for using network taps for verification is Flexible Hardware-Enabled Guarantees (FlexHEGs) (Petrie and Aarne, [2025](https://arxiv.org/html/2507.15916v2#bib.bib163)), earlier proposals of which emphasized another mechanism we discuss below: tamper-proof, compliance-locked servers (Petrie et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib164)).

Partial workload re-execution with constraints (e.g., “proof-of-learning”) ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")): Trusted, secured chips (whether on- or off-site) could run software tests to check whether the Prover’s declarations are accurate (Subgoal 1.A). For Subgoal 1.A, tests could involve re-running random segments of AI training or deployment to check if claimed results can be approximately reproduced (Jia et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib110); Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187)). However, a Prover might be able to spoof results they never computed in the first place; countering these spoofs requires further tests (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)). This mechanism does not inherently involve analog sensors, but it complements analog sensors well, by completing Subgoal 1.A—a gap left by analog sensors.

(Backup) Evaluations on separate chips: Trusted, secured chips (whether on- or off-site; [Section 4.2.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px1 "4.2.1.1 Prerequisites: Off-Chip Devices ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) could test whether any declared models, data, and code have the required properties (Subgoal 1.B; [Section 2.1](https://arxiv.org/html/2507.15916v2#Sx3.SSx1 "2.1 Rules on AI Models, Data, and Code ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")). For example, these chips could directly run safety evaluations on declared models. These tests could be “backup” tests in the sense of adding redundancy to hardware-backed evaluations ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). They could add redundancy to both the testing infrastructure (by having both off-chip and on-chip approaches to testing) and to the tests’ substance (by e.g., using different test datasets).

Off-chip analog sensors for compute accounting ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")): Off-chip sensors could log measurements such as AI chips’ power draw. The Verifier could then analyze these measurements with secured chips, testing for several signs of large, undeclared compute use: declared workloads would appear unnecessarily slow, AI chips would use more power than needed for the declared workloads, and/or the detailed physical signatures of chips would be different than expected. In other words, the Verifier would use analog measurements to verify the total number of operations or chip-hours done and check if approximately all of them can be “accounted for” by declared uses. There are various complications in implementing these checks.

Verifying AI chips’ chain of custody: A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction. This would serve to verify that large quantities of AI chips are not assembled into undeclared AI compute clusters (Subgoal 2.B). Users of small quantities could potentially be exempt. Existing AI chips would be a challenge, though perhaps many could have their locations and owners retroactively verified. Declared chains of custody could be verified with inspections, potentially supplemented by video cameras (Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13)) and hard-to-spoof, unique IDs.[^57]

Tamper-proof, compliance-locked AI servers: A whole server containing AI chips could be tamper-proof and compliance-locked (Petrie et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib164)). This would serve as an additional method to address undeclared AI compute clusters (Subgoal 2.B).[^58] This mechanism is similar to tamper-proof, compliance-locked AI chips ([Section 4.1.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx1.Px2 "4.1.1.2 Verification Mechanisms ‣ 4.1.1 Mechanisms ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), but implementation would differ; here, tamper-proofing would be implemented in the server enclosure rather than on-chip, and compliance-locking would leverage the above mechanisms rather than on-chip ones to detect non-compliance.

Together, all the above mechanisms could combine to form two redundant layers of off-chip verification, one involving network taps and the other involving analog sensors ([Figure 6](https://arxiv.org/html/2507.15916v2#Sx5.F6 "Figure 6 ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).

#### 4.2.2 Analysis

Off-chip verification avoids the worst hardware security challenges. As discussed ([Section 4.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx2 "4.1.2 Analysis ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), _on_\-chip mechanisms face severe hardware security challenges, including that their hardware components are not retrofittable, they may have supply chains untrusted by the Verifier, and their security may be deprioritized in favor of performance. Off-chip mechanisms still need hardware security, but achieving it is not as much of an uphill battle.[^59] Off-chip sensors and chips can be retrofitted to existing chips, and their supply chains and design can be highly optimized for security.[^60] [^61] [^62]

The strongest network taps face substantial engineering challenges, requiring chip-adjacent hardware to be redesigned. In order for network taps to tap all communication between AI chips in a compute cluster, the cutting-edge hardware that executes this communication would have to be redesigned or modified, despite being proprietary or co-packaged with AI chips ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). Alternatively, further removed taps would have visibility into a smaller portion of communications, perhaps serving as a supplement to partial workload re-execution more than as an independent guarantee.

Off-chip verification faces substantial protocol design challenges and offers limited precision. Off-chip devices must infer chip behavior “from the outside.” This involves several algorithmic problems that do not currently have complete solutions. It also introduces imprecision, e.g., in using analog measurements to infer a chip’s rate of operations. Even at its best, then, off-chip verification is likely most applicable for contexts where significant error bars are acceptable, i.e., where it is not a major concern if a relatively small fraction of compute use is undeclared. With AI capabilities requiring less compute over time (Ho et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib96)) and the amount of compute available increasing over time, this would likely be the earlier stages of a verification regime—or longer if societal resilience improves (raising the amount of compute needed to cause harm). Separately, network taps would only be useful if the data exchanged between AI chips is unencrypted or if its decryption key is shared, which could trade off against security, though network-tap-related technologies could also support encryption and security in other ways (Petrie and Aarne, [2025](https://arxiv.org/html/2507.15916v2#bib.bib163)).

Off-chip mechanisms would require significant logistical and potentially production efforts. To verify claims with relatively small error bars, there may need to be one off-chip sensor and/or network tap for every data center AI chip, which would require the production and installation of millions of devices (assuming there do not happen to be adequate devices available). For reference, NVIDIA was estimated to ship 1.5-2 million H100 GPUs in 2024, a significant rise from the previous year’s 0.5 million H100 shipments (Shilov, [2023](https://arxiv.org/html/2507.15916v2#bib.bib191)). Building mutually secured “trusted clusters” would require additional work, even if concentrated into a small number of clusters. Fortunately, the sensor devices could potentially be simple sensors that do not interfere with operations, and one could use many fewer sensors (e.g., one per server rack) if one is willing to accept larger error bars.

Given the challenges of both on- and off-chip verification, it would be helpful if there were also simpler approaches to verification, or more broadly, approaches with different tradeoffs. This is where personnel-based verification comes in.

### 4.3 Personnel-Based Verification Layers

| Potential verification layer | Summary of layer | Key  
advantages | Key disadvantages |
| --- | --- | --- | --- |
| Whistleblower programs![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image9.png) | Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals. | Relatively simple, precedented, and implementation- ready. | Unclear effectiveness: depends on the number and loyalty of accomplices. |
| --- | --- | --- | --- |
| Interviews of personnel![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image6.png) | Interviews may reveal violations at any verification subgoal, e.g., via inconsistencies or perhaps improved lie detection tech, but such tech is abusable. | Relatively simple and precedented. | Unclear effectiveness: depends on accomplices’ ability to lie undetected. |
| --- | --- | --- | --- |
| National intelligence activities![\[Uncaptioned image\]](https://arxiv.org/html/media/media/image3.png) | Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence. | Precedented and may be feasible unilaterally. | More adversarial, harder for third parties to verify, and unclear effectiveness. |
| --- | --- | --- | --- |
|  |  |  |  |
| --- | --- | --- | --- |

Table 8: Summary of personnel-based verification layers and their tradeoffs.

![Refer to caption](https://arxiv.org/html/2507.15916v1/x7.png)

Figure 7: Summary of how personnel-based verification layers would complete each subgoal. Each of these layers simply consists of a single mechanism applied to all subgoals.

In contrast to other, more technical verification mechanisms, _personnel-based verification_ relies on the difficulty of having large groups of people collude without disclosures or leaks. Verifiers could systematically seek disclosures or leaks through whistleblower programs, interviews of personnel, and national intelligence activities. Intelligence activities, though, might involve cyber or signals intelligence, not only direct communication with personnel.

#### 4.3.1 Mechanisms

We outline three distinct mechanisms for personnel-based verification. All are well-established mechanisms for verifying compliance with regulations or international agreements.

Whistleblower programs: Formal, cooperative whistleblower programs could enable and encourage employees to narrowly blow the whistle on violations ([Appendix A.8](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx8 "A.8 Whistleblower Programs ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")):[^63]

-   •
    
    To enable whistleblowing, employees could be allowed to confidentially view some of their employer’s claims. They could also be given regular in-person contact with Verifiers, to counter whistleblower suppression, with measures to minimize inappropriate leaks.
    
-   •
    
    To encourage whistleblowing, formal programs could, e.g., enable anonymous reports, offer financial rewards, or build pro-whistleblower norms.
    

Interviews of personnel: Employees could reveal violations unintentionally in interviews with Verifiers. This is in contrast with whistleblowers, who intentionally reveal violations. Interviewees could collude to lie, but they may struggle to do so convincingly. Another concern with interviews could be that they might reveal sensitive information; this could be mitigated by limiting interviews to questions within a narrow, agreed-on scope, similar to the questions asked to whistleblowers ([Appendix A.8](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx8 "A.8 Whistleblower Programs ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).

Hypothetically, one way interviews could be relatively robust is if they involved more reliable lie-detection technology than currently exists. However, we are not recommending the development of such technology, due to its potential for abuse.

National intelligence activities: States[^64] could seek evidence of violations through disciplines including human intelligence, signals intelligence, and cyber intelligence. Unlike the above mechanisms, intelligence activities may be effective without the Prover’s cooperation.[^65] Intelligence-based verification may not be equally feasible for all states in multilateral contexts, but states with relatively weak intelligence capabilities could rely on stronger states’ intelligence-based verification. For example, in a hypothetical agreement with the United States and China as parties, if a third party lacked confidence in their own intelligence capabilities, they might trust that the United States would verify (and enforce) China’s compliance, because doing so would be in U.S. interests, and vice versa.

#### 4.3.2 Analysis

Personnel-based verification offers simplicity, but its reliability is unclear. Personnel-based verification mechanisms tend to offer relatively cheap, simple verification methods, without necessarily depending on complex, new technical protocols or hardware (which may be slow to develop, stress-test, and physically set up). Consequently, personnel-based mechanisms may be unusually feasible to use on short notice. These mechanisms leverage the large number of individuals involved in large-scale AI development—typically hundreds (Table 9). Human-based verification would also tend to strengthen other verification mechanisms, catching efforts to circumvent other mechanisms via significant collusion. However, human-based verification mechanisms may be hindered by counterintelligence, such as a violator involving only a small group of well-vetted and surveilled individuals in any violation (possibly for security reasons), though there are potential countermeasures.

Personnel-based mechanisms would not only provide their own assurances but also strengthen technical assurances. In addition to providing independent ways to detect violations, personnel-based mechanisms could detect efforts to circumvent on- and off-chip layers. For example, if a state tried to circumvent on-chip mechanisms, it might use personnel to: identify or design hardware vulnerabilities, physically tamper with chips, or swap a compromised chip design into a chipmaking machine.[^66] Thus, a significant number of personnel may be able to disclose or leak evidence of the violation, not even counting the personnel involved in the AI aspects of the violation. In this sense, verification layers do not only provide backup in case other layers fail; they also make it less likely that other layers will fail.

The number of human personnel needed for AI development and deployment could fall due to AI automation, reducing the effectiveness of personnel-based verification. AI models are increasingly capable of software engineering and AI R&D (Bengio et al., [2025a](https://arxiv.org/html/2507.15916v2#bib.bib16); Kwa et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib123)). Still, even if AI engineers become fully automatable, some human involvement could persist. For example, human personnel may remain as organizational leaders, as staff who construct or maintain data centers, and as overseers of AI deployments—especially if significant human oversight is required.[^67] Separately, capable AI agents could benefit on- and off-chip verification layers ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"); [Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).

| AI model (or model family) | Number of “core contributors”[^68] | Number of “contributors” (including core contributors) |
| --- | --- | --- |
| GPT-4 (OpenAI) | 85 (excl. Microsoft) | 287 (excl. Microsoft) |
| --- | --- | --- |
| Llama 3 (Meta) | 222 | 529 |
| --- | --- | --- |
| Gemini (Google DeepMind) | 712 | 1254 |
| --- | --- | --- |
|  |  |  |
| --- | --- | --- |

Table 9: The number of contributors and core contributors publicly listed for several prominent AI models. Note these are not defined consistently, and they likely exclude various employees who could blow the whistle on certain violations, e.g., data center construction/maintenance staff, supplier company staff, or other AI developer staff such as product staff.

### 4.4 Supplementary Verification Mechanisms

![Refer to caption](https://arxiv.org/html/2507.15916v1/x8.png)

Figure 8: Supplementary verification mechanisms, each under the verification subgoal(s) it could help complete.

We identified 15 verification mechanisms ([Figure 6](https://arxiv.org/html/2507.15916v2#Sx5.F8 "Figure 8 ‣ 4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) that could supplement the verification mechanisms and layers discussed above. We consider these merely supplemental because they appear highly limited in scope (i.e., unable to complete any verification subgoal) or clearly circumventable even if implemented well, whereas for the mechanisms discussed in previous sections, we were able to outline plausible defenses against all identified circumvention tactics. Still, even if these supplemental verification mechanisms can be circumvented, efforts to circumvent them may trigger other, more reliable verification mechanisms. For example, a Prover might seek to hide a data center from satellite images by building it underwater, but this may require contracting one of the few companies with experience building underwater data centers (Gooding, [2025](https://arxiv.org/html/2507.15916v2#bib.bib77)), which could expose the Prover to hypothetical whistleblower programs or intelligence activities in these companies ([Section 4.3](https://arxiv.org/html/2507.15916v2#Sx5.SSx3 "4.3 Personnel-Based Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).[^69]

The supplemental verification mechanisms we identified are:

-   •
    
    Supplementary constraints: Heuristic tests could supplement partial workload re-execution with constraints ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Data & code validation: One could test whether declared data and code have been maliciously engineered to circumvent verification ([Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). This could supplement protocols that are intended to be robust to malicious data and code.
    
-   •
    
    Financial audits: One could check documentation to see whether organizational cash flows add up. Documents could be forged, but that would be more difficult in the presence of personnel-based mechanisms like whistleblower programs.
    
-   •
    
    Sanity checks: One could check whether claimed organizational activities are plausibly consistent given an organization’s objectives and incentives. For example, a major AI company claiming to spend $1 billion of compute on weather simulations could be suspicious.
    
-   •
    
    Workload classification: High-level workload measurements such as power draw may allow for workload classification: distinguishing whether a workload is AI development or deployment (Heim et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib90)).[^70] Workload classification could play a valuable role ([Appendix B.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx2.SSSx2 "B.2 Verification of Narrower Rules ‣ B. Broader Regime Design ‣ Appendices ‣ Verifying International Agreements on AI"); [Appendix A.7](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx7 "A.7 Verifying Non-AI Workloads in AI Data Centers ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) (Scher and Thiergart, [2024](https://arxiv.org/html/2507.15916v2#bib.bib179)). At the same time, the information it gives is too coarse-grained to complete any of our verification subgoals in full; more fine-grained methods ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) are needed to verify compliance with rules that prohibit specific types of development or specific types of deployment.
    
-   •
    
    Analytic output verification: For some compute uses, most prominently cryptocurrency mining, outputs’ authenticity can be verified quickly and with near-certainty by examining the outputs instead of needing to reproduce them.
    
-   •
    
    Weaker, heuristic evaluations: More uncertain evaluations could supplement higher-confidence ones.
    
-   •
    
    Inspections for undeclared AI clusters: Inspections could help identify hidden AI compute clusters. To enable inspections, suspect sites could first be identified by other mechanisms in this list, e.g., open-source information and satellite images. However, these methods would struggle to find data centers that are underwater (Gooding, [2025](https://arxiv.org/html/2507.15916v2#bib.bib77)) or otherwise hidden and have strong operational security. They are also challenged by the growing success of decentralized AI development—AI training that is spread out over many smaller compute clusters. In contrast, the other verification mechanisms we highlight in prior sections, such as whistleblower programs and chain-of-custody verification, could be effective even if AI development were split over relatively small compute clusters.[^71]
    
-   •
    
    Information from data center suppliers: Data center suppliers’ public statements and privately disclosed documentation could help reveal hidden AI data centers. Data centers have many specialized components, not just AI chips (Pilz and Heim, [2023](https://arxiv.org/html/2507.15916v2#bib.bib165)).
    
-   •
    
    Cameras at AI data centers: Security cameras could help ensure that AI chips are not tampered with or diverted, and that any other verification equipment is also not tampered with. These cameras, like those of the International Atomic Energy Agency (Fournier, [2016](https://arxiv.org/html/2507.15916v2#bib.bib68); Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)), could be tamper-evident and checked on-site. Security cameras are already standard in data centers (DatacenterDynamics, [2024](https://arxiv.org/html/2507.15916v2#bib.bib47); Gluck and Mazzoli, [2024](https://arxiv.org/html/2507.15916v2#bib.bib74))
    
-   •
    
    Design information verification: Design information verification is a practice of the International Atomic Energy Agency (Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)). It consists of verifying information about a facility’s design, including through on-site inspections during construction, to ensure the facility does not have hidden rooms or piping. Applied to AI, analogous checks could help ensure that AI data centers are not built with hidden rooms that could store undeclared AI compute clusters.
    
-   •
    
    Satellite or aerial images: Satellite or aerial images, including infrared images, could help identify hidden AI data centers, especially in combination with inspections of suspect sites (“Inspections for undeclared AI clusters” above).
    
-   •
    
    Open-source intelligence (OSINT): Open-source information, such as social media posts and news reports, could reveal information such as hidden data center constructions, especially in combination with inspections of suspect sites (“Inspections for undeclared AI clusters” above). Open-source information could also find signs of non-compliant AI deployment, e.g., through its economic, scientific, or military impacts. However, these impacts might not be evident before the deployment causes harm or yields an unfair advantage.[^72]
    

### 4.5 Implementation Options Across Mechanisms

Across different verification mechanisms, some common implementation questions arise. Here, we briefly discuss some of these questions, to highlight options and their tradeoffs.

Technical tests—hard-coded tests, human auditors, or AI auditors? On-chip and off-chip verification layers rely on technical tests to check Provers’ claims. These tests could involve:

-   •
    
    _Hard-coded tests_: software with all analysis specified precisely in advance. Such software can require a challenging degree of foresight and generality, though constraints on the Prover’s formatting could help. This report’s [Appendices](https://arxiv.org/html/2507.15916v2#Ax1 "Appendices ‣ Verifying International Agreements on AI") explore implementation in the context of hard-coded tests, conservatively assuming that human auditors and AI auditors may be unavailable. Still, protocols designed to be hard-coded tests could also be run by human or AI auditors.
    
-   •
    
    _Human auditors_: human inspectors who do iterative testing, designing new tests based on intermediate findings.[^73] The transmission of intermediate results would undermine confidentiality-preservation, but this downside could be limited by the intermediate results being low-bandwidth (Greenblatt, [2024](https://arxiv.org/html/2507.15916v2#bib.bib82)), perhaps up to physically isolating the voluntary human auditors (Harack et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib83)).
    
-   •
    
    _AI auditors:_ AI agents that do iterative testing, designing new tests based on intermediate findings. This may become feasible, as AI systems have been rapidly improving in their ability to complete complex, long-term software engineering and research tasks (Bengio et al., [2025a](https://arxiv.org/html/2507.15916v2#bib.bib16); Kwa et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib123)). AI agents are dynamic, unlike hard-coded tests, and unlike humans, their memory can be wiped of confidential information. However, it is unclear when AI agents will have the needed capabilities and reliability, and deployment poses logistical and cybersecurity challenges.
    

Security—through transparency or through obscurity? The technical details of verification mechanisms could be disclosed openly so they can be stress-tested and mutually trusted. However, this openness could help Provers find ways to spoof the verification mechanisms, especially if there is not enough time to make them airtight. Perhaps the ideal approach is for some details to be publicly vetted while others are kept confidential, so that both known and unknown mechanisms can deter violations.

Verifier—bilateral or third-party? Though this report’s focus is not on institution design, it is worth noting that Provers may more easily trust that a third-party Verifier will act in good faith, rather than seeking to steal information or compromise equipment. On the other hand, third-party Verifiers may take longer to set up and may not be as effective. In particular, third parties would lack major states’ intelligence capabilities, though intelligence sharing may help. These tradeoffs might be eased through intermediate options, such as a national verification office that hires citizens of third-party countries to conduct interviews.

## 5\. Open Problems in Verification

Throughout our analysis of verification mechanisms ([Section 4](https://arxiv.org/html/2507.15916v2#Sx5 "4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"); [Appendices](https://arxiv.org/html/2507.15916v2#Ax1 "Appendices ‣ Verifying International Agreements on AI")), we identified implementation challenges. Here, we compile a list of selected open problems for technical research and collaboration (Table 10), as well as brief context for funders and researchers considering work in this area.

Selected R&D and infrastructure challenges. The following list is filtered for R&D problems that are relatively challenging, have been subject to relatively little work compared to their difficulty, could play major roles in verification, and would not create highly abusable tech (e.g., lie detection). We separately discuss R&D challenges more comprehensively and in more detail ([Appendices](https://arxiv.org/html/2507.15916v2#Ax1 "Appendices ‣ Verifying International Agreements on AI"); [Appendix c.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx3 "C.3 Additional R&D Problems for Verification ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")).

| Verification layer | Selected R&D and infrastructure challenges (Legend:  : hardware;  : CS/ML;  : organizational) |
| --- | --- |
| 1\. Security features in AI chips ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) |   A. System software protocol: Given verifiable system software (with access to e.g., kernels, memory), verify workload code, and model and data locations, despite any potential obfuscation ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  B. Hardware design attestation: Given a scanned hardware layout and Hardware Description Language (HDL), check if they match ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  C. Hardware security features: Develop highly vetted, open-source, dedicated hardware designs for secure boot, Confidential Computing, and on-chip tamper-proofing ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  D. Design adoption: Adopt the above designs into leading AI chips. |
| --- | --- |
| 2\. Off-chip network taps & analysis ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) |   A. Network tap analysis: Given a cluster’s inter-accelerator data (including kernels), verify that the cluster executed only a claimed workload ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  B. Network taps: Design and manufacture appropriate network taps, or identify suitable existing tech ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  C. Trusted clusters: Build small compute clusters that are or can be mutually physically secured ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). |
| --- | --- |
| 3\. Off-chip analog sensors & analysis ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) |   A. Code & data checks: Develop tests to detect code and data that are designed to spoof partial program re-execution with constraints (e.g. proof-of-learning) ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"); [Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  B. Workload modeling: Given an AI workload and cluster specs, estimate the optimal utilization (MFU) and the associated physical signature, e.g., power ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  C. Analog sensors: Design and manufacture appropriate analog sensors, or identify suitable existing tech ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).  D. Tamper-proofing: Design and manufacture appropriate tamper-proof server enclosures ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). |
| --- | --- |
| Cross-cutting |   A. R&D funding (e.g., by AISIs, philanthropists, DARPA)  B. Pilot programs (e.g., voluntary corporate commitments, AISI collaborations)  C. Red teaming (e.g., by companies, ICs, NIST contest) of developed proposals |
| --- | --- |
|  |  |
| --- | --- |

Table 10: Selected open challenges in verification R&D. We discuss open problems more comprehensively ([Appendices](https://arxiv.org/html/2507.15916v2#Ax1 "Appendices ‣ Verifying International Agreements on AI"); [Appendix C.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx3 "C.3 Additional R&D Problems for Verification ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")). Note that work on the listed “CS/ML” challenges would often draw on expertise on low-level implementation.

AI evaluations and standards are complementary to verification R&D. Beyond verification R&D, verification will only be useful if the rules being verified ([Section 2.1](https://arxiv.org/html/2507.15916v2#Sx3.SSx1 "2.1 Rules on AI Models, Data, and Code ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")) are well-specified: if compliance is actually sufficient to achieve governance goals such as security. Operationalizing AI governance goals is a challenging and active area of research, which includes work on AI evaluations and standards (Shenk, [2024](https://arxiv.org/html/2507.15916v2#bib.bib190); [Frontier Model Forum,](https://arxiv.org/html/2507.15916v2#bib.bib69) ; [UK AI Security Institute,](https://arxiv.org/html/2507.15916v2#bib.bib211) ), and it is a necessary complement to verification R&D ([Section 3.3](https://arxiv.org/html/2507.15916v2#Sx4.SSx3 "3.3 Addressing Broader Challenges for Verification ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")).

Context for R&D funders and researchers. R&D funders and researchers may wish to consider the following brief context on the landscape of technical research in AI verification:

-   •
    
    _Relevant fields and areas of expertise:_ Computer security research experience will be especially useful for AI verification R&D.[^74] Broader expertise in software, ML, and computing hardware will often be very applicable as well, including research experience with large language models, distributed computing, and GPUs / AI accelerators.
    
-   •
    
    _Ongoing, relevant work:_ While there is much adjacent research in academia and sometimes industry and government, the specific challenges we list mostly receive little to no work, as of early 2025.[^75] This is because these challenges target unusual scenarios, where hardware designers, manufacturers, cloud providers, and users may all collude against a separate Verifier due to a coordinated government effort. This rules out many typical ways of gaining assurances by trusting some of these actors.[^76] The scenarios we consider also open up unusual options, such as on-site inspections. As partial exceptions, in 2024 there were $4.1 million granted for research on Flexible Hardware-Enabled Guarantees (FlexHEGs) (Survival & Flourishing Fund, [2024](https://arxiv.org/html/2507.15916v2#bib.bib198)), and a further expected $2-10 million for hardware-enabled mechanisms (including but not only for verification) were announced in 2025 (Longview Philanthropy, [2025](https://arxiv.org/html/2507.15916v2#bib.bib130)).
    
-   •
    
    _Sequencing:_ (1) Initial development and pilot programs, (2) world-class red teaming (e.g., an international NIST competition or red teaming by intelligence agencies), and (3) manufacturing/adoption could be done in that order, to efficiently use organizations’ limited availability for the latter of these actions.
    

## 6\. Conclusion

In managing AI’s impacts, verification of rules on AI development and deployment may play a crucial role: assuring actors that all parties are upholding an agreement, so compliance does not put them at a disadvantage. Confidentiality-preserving verification of rules on large-scale AI compute use may be especially valuable. There are many options for such verification, and it could ultimately feature substantial redundancy. In a framework of several verification subgoals, we saw how all subgoals may be completed by plausible verification mechanisms, forming up to six redundant layers of verification. Personnel-based verification layers, such as whistleblower programs, would offer some assurances with limited preparation required. However, before states can have confidence in technical layers of verification, the R&D and infrastructure challenges we list require progress, which can be promoted by R&D funding, pilot programs, and red teaming. With such efforts, we can avoid leaving future policymakers with just a few untried verification options, and instead equip them with an arsenal of stress-tested tools.

## About This Working Paper

### Contributions

Mauricio Baker designed the research methodology, formulated the verification framework, contributed to the analysis of verification mechanisms, conducted the expert interviews, and wrote the majority of the report.

Gabriel Kulp contributed to the analysis of verification mechanisms and confidentiality-preserving technologies, especially on hardware mechanisms and secure implementation of technical mechanisms, and contributed to the structure of the report.

Oliver Marks contributed to the analysis of verification mechanisms and confidentiality-preserving technologies, especially on partial workload re-execution and compute accounting via analog measurement of AI chips, and contributed to the structure of the report.

Miles Brundage gave detailed feedback on the report's overall argument and structure and contributed to writing.

Lennart Heim contributed strategic guidance, research management, editing, and feedback on the report.

Each author contributed ideas and/or writing to the report and reviewed the report, though authorship does not necessarily imply agreement with every claim made in the report.

### Technology and Security Policy Center

RAND Global and Emerging Risks is a division of RAND that delivers rigorous and objective public policy research on the most consequential challenges to civilization and global security. This work was undertaken by the division’s Technology and Security Policy Center, which explores how high-consequence, dual-use technologies change the global competition and threat environment, then develops policy and technology options to advance the security of the United States, its allies and partners, and the world. For more information, contact tasp@rand.org.

### Funding

This research was independently initiated and conducted within the Technology and Security Policy Center using income from operations and gifts from philanthropic supporters, which have been made or recommended by DALHAP Investments Ltd., Effektiv Spenden, Ergo Impact, Founders Pledge, Charlottes och Fredriks Stiftelse, Good Ventures, Jaan Tallinn, Longview, Open Philanthropy, and Waking Up Foundation. A complete list of donors and funders is available at www.rand.org/TASP. RAND donors and grantors have no influence over research findings or recommendations.

### Acknowledgements

We thank our interviewees for sharing their expertise. We do not list their names to preserve confidentiality. We also thank Ben Harack for his generous feedback. We additionally thank Aaron Scher, Aidan O’Gara, Aris Richardson, Asher Brass, Ben Chang, Bria Persaud, Brodi Kotila, Casey Dugan, Casey Mahoney, Chris Byrd, Daniel Reuter, David Dalrymple, David Glickstein, David Schneider-Joseph, Everett Smith, Felipe Calero Forero, Girish Sastry, Jack Miller, Jair Aguirre, James Bradbury, Joel Predd, Jonathan Happel, Joshua Clymer, Kendrea Beers, Konstantin Pilz, Lisa Thiergart, Michael Aird, Michael Byun, Morgan Livingston, Naci Cankaya, Nora Ammann, Oliver Guest, Onni Aarne, Ying Yi Dang, and Yonadav Shavit for their helpful feedback or discussion. As usual, this report does not necessarily represent the views of acknowledged individuals, and any remaining mistakes are our own.

## Appendices

Our appendices are split into three sections:

1.  A.
    
    Implementation analyses, making up the majority of the appendices, outline how various, mostly technical, implementation challenges could be addressed. We list highlights from these analyses in [Section 1.1](https://arxiv.org/html/2507.15916v2#Sx2.SSx1 "1.1 Contributions ‣ 1. Introduction ‣ Verifying International Agreements on AI").
    
2.  B.
    
    Broader regime design sections discuss: rationales for compute accounting ([Appendix B.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx2.SSSx1 "B.1 Compute Accounting vs. Other Kinds of Accounting ‣ B. Broader Regime Design ‣ Appendices ‣ Verifying International Agreements on AI")), narrower governance goals that may be easier to verify ([Appendix B.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx2.SSSx2 "B.2 Verification of Narrower Rules ‣ B. Broader Regime Design ‣ Appendices ‣ Verifying International Agreements on AI")), and how verification may deal with ambiguous findings ([Appendix B.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx2.SSSx3 "B.3 Acting on Ambiguous Findings ‣ B. Broader Regime Design ‣ Appendices ‣ Verifying International Agreements on AI")).
    
3.  C.
    
    Methodology details elaborate on methodology-related aspects, including overviews of additional R&D problems ([Appendix C.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx3 "C.3 Additional R&D Problems for Verification ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")) and related work ([Appendix C.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx5 "C.5 Related Work ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")).
    

### A. Implementation Analyses

#### A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation

Full-stack security overview. To be adversarially robust, all technical verification mechanisms must not only have secure high-level protocols; these protocols must also be implemented securely. Implementation must be secure despite the large attack surface (namely the whole infrastructure stack, from the Verifier’s software to the hardware) and the numerous untrusted actors (including various software vendors and potentially the hardware design, manufacturing, and assembly companies). In requiring such secure infrastructure, many verification mechanisms face shared challenges, which may be amenable to shared solutions. Across the infrastructure stack, (relevant parts of) designs may need to be (1) disclosed, (2) verified as authentic, (3) comprehensively tested for vulnerabilities, and (4) patched or addressed as needed. These actions may leverage technologies including open-source components, secure boot, delayering, and formal verification (Table 11). However, such security may be slow, technically challenging, and expensive (especially if much hardware needs to be replaced), and it may require significant IP disclosures (though these may be less significant than they initially appear).

Hardware security for Prover- vs Verifier-owned hardware. Significant hardware security measures (Table 11) are most needed when relying on hardware that is (i) acquired from untrusted suppliers and (ii) operated by the Prover. The Prover-owned hardware used for on-chip verification ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) would likely meet these criteria. In contrast, for mechanisms that rely more on the Verifier’s hardware, such as off-chip mechanisms ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), the Verifier may have simpler options to secure their hardware.[^77]

| Component of infrastructure stack | 1\. How designs could be disclosed | 2\. How disclosed designs could be verified authentic | 3\. How disclosed designs could be comprehensively tested for vulnerabilities | 4\. How identified vulnerabilities could be mitigated |
| --- | --- | --- | --- | --- |
| Application (of the Verifier[^78]) | Using open-source components,[^79] open-sourcing design IP,[^80] using a Verifier-trusted designer and foundry,[^81] or making confidentiality-preserving IP disclosures.[^82] | Secure boot,[^83] secure compiler. | Formal verification of narrow design (with improved provers) \*,[^84] red teaming \*, and standard design validation techniques like test cases \*. | Software/firmware patches, or key revocation where applicable. |
| --- | --- | --- | --- | --- |
| Operating system |  |  |  |  |
| --- | --- | --- | --- | --- |
| Hypervisor |  |  |  |  |
| --- | --- | --- | --- | --- |
| Firmware |  | The above and below \*.[^85] |  | The above or below \*.[^86] |
| --- | --- | --- | --- | --- |
| Hardware |  | Delayering \*, scanning \*, and circuit verification \* for a random sample[^87], and/or oversight of manufacturing \*. |  | Using alternative (non-hardware-based) verification methods \*, refraining from use of vulnerable hardware, or key revocation where applicable. |
| --- | --- | --- | --- | --- |
|  | _\*: Technically challenging/ambitious (if one wishes to use this for strong, affordable, and timely security assurances)._ |
| --- | --- |
|  |  |  |  |  |
| --- | --- | --- | --- | --- |

Table 11: Overview of some options for comprehensively securing a technology stack for AI verification.

Next, we non-comprehensively discuss some notable challenges posed by the above security measures, and how these challenges may be addressed.

Securing a hypervisor and operating system. Acquiring a secure hypervisor and operating system (OS) may appear to be a daunting task. The Linux OS, for instance, contains millions of lines of code (Larabel, [2020](https://arxiv.org/html/2507.15916v2#bib.bib124)), and—even though it has been scrutinized for decades—over 1,000 security vulnerabilities were found just in recent years (Day, [2023](https://arxiv.org/html/2507.15916v2#bib.bib48); [CVE Details,](https://arxiv.org/html/2507.15916v2#bib.bib45) ). Still, hypervisor and OS security may be more feasible for AI verification than it first appears, for several reasons:

-   •
    
    _Hypervisor security:_ Hypervisors are designed to isolate virtual machines, offering security even against compromised OSs. Fortunately, hypervisors are well-studied because of their importance for cloud computing. Moreover, there are already open-source hypervisors with relatively “tiny” attack surfaces: tens of thousands, not millions, of lines of code. A security expert we interviewed expressed confidence that such a hypervisor, like KVM ([KVM,](https://arxiv.org/html/2507.15916v2#bib.bib122) ), would be suitable even for high-stakes applications, at least after extensive auditing. (Interview #6, 2024.)
    
-   •
    
    _Narrow function:_ An OS specialized for verifying rules on AI could have much narrower functions than a general-purpose OS, so the former could potentially consist of much less code (e.g., omitting many drivers, graphical user interface functionalities, and sophisticated support for resource allocation).
    
-   •
    
    _Opportunity for formal verification:_ A lightweight hypervisor and OS could potentially be formally verified. There has been significant work in this direction ([LF Projects,](https://arxiv.org/html/2507.15916v2#bib.bib126) ; Redox Developers, [2015](https://arxiv.org/html/2507.15916v2#bib.bib172)), though secure OS development has so far received limited funding,[^88] at least partly due to lacking incentives.[^89] Reliable formal verification may benefit from more reliable automated provers.
    
-   •
    
    _Other benefits:_ If not already available, a secure hypervisor and OS for running AI workloads would likely more broadly benefit the security of AI model weights, a widely shared policy goal (Department for Science, Innovation & Technology, [2024](https://arxiv.org/html/2507.15916v2#bib.bib53); Biden Jr., [2023](https://arxiv.org/html/2507.15916v2#bib.bib20); [European Union,](https://arxiv.org/html/2507.15916v2#bib.bib64) ; Vance, [2025](https://arxiv.org/html/2507.15916v2#bib.bib217)), and perhaps computer security more broadly, presumably increasing the feasibility of acquiring funding. However, security-performance tradeoffs may be challenging, and improved AI security might trade off with the feasibility of using cyber intelligence for verification.
    

Verification with an untrusted hardware designer. Hardware security research often (Jain et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib109)) but not always (Bhunia et al., [2014](https://arxiv.org/html/2507.15916v2#bib.bib19)) assumes a hardware _manufacturer_ or assembly/test company is untrusted. A threat model where the hardware _designer_ is also untrusted poses further challenges, including the following, though they may be resolvable:

-   •
    
    _Key management:_ Untrusted hardware design and manufacturing introduces challenges in cryptographic key management (for hardware security modules’ private keys), including secure key generation and ensuring the designer does not abuse their usual authority to sign firmware updates. For the latter challenge, secure key revocation appears needed. Fortunately, key revocation is a common existing functionality of cryptographic systems ([National Institute of Standards and Technology,](https://arxiv.org/html/2507.15916v2#bib.bib141) ), so that any stolen keys do not create permanent vulnerabilities.
    
-   •
    
    _Hardware design verification:_ With an untrusted hardware design, security requires verifying not only that manufactured hardware (or at least the hardware security module) matches its claimed design, but also that the claimed design is free of backdoors.
    
-   •
    
    _Reference measures for firmware attestation:_ Firmware attestation involves comparing measurements of an attesting device (e.g., iteratively computed hashes of firmware and of executable code) to reference measurements (Edery et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib57)). To obtain reliable reference measurements when the hardware designer’s measurements are untrusted, without gaining access to private information such as the Prover’s code, one option may be for the Verifier and Prover to jointly create reference measurements by emulating a compliant bootup on a confidentiality-preserving technology (e.g., Confidential Computing).
    
-   •
    
    _Hardware specs:_ An untrusted hardware designer might state false hardware performance specifications, posing an obstacle to methods such as operations accounting ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). Specifications could be (i) verified approximately by comparing new devices to known ones, or (ii) verified precisely by (delayering and) scanning chips for bottom-up verification of their operations or bandwidth per clock cycle (and otherwise verifying clock speed, such as through electromagnetic measurement).
    

Low-latency chip delayering and scanning. One might worry that delayering and scanning a random sample of chips would be too slow for timely detection of Hardware Trojans (or false specs), with modern chips having “up to 100 layers” ([ASML,](https://arxiv.org/html/2507.15916v2#bib.bib11) ) and nanometer-scale features. To address this, a Verifier could in principle do much faster delayering via three kinds of parallelization (at added expense)[^90] and by only scanning certain components (e.g., a known hardware security module).

Attesting to the continuous presence of firmware. On-chip verification ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) requires certain firmware to be continuously present, rather than only present for occasional checks. To attest to this, approaches include: (i) a firmware update that makes secure boot infeasible to disable,[^91] (ii) a hardware-level secure counter that detects firmware being swapped out,[^92] (iii) randomly timed queries requiring low-latency firmware attestation,[^93] (iv) off-chip sensors such as electricity meters attesting to continuous operation, and (v) more ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).

Secure operation. Beyond secure protocol design, the Verifier must also run their protocols securely. This includes personnel security, physical security for Verifier hardware, and a secure IT system for tracking findings.

#### A.2 Hardware-Backed Workload Certificates and Evaluations

Hardware security features could enable on-chip verification mechanisms including hardware-backed workload certificates and hardware-backed evaluations ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). This appendix outlines how these mechanisms could be implemented, assuming tamper-evident secure boot and optionally Confidential Computing are supported in AI compute clusters’ AI chips and CPUs. If supported, secure boot could ensure the presence of system software that enforces the following behavior,[^94] with Confidential Computing optionally used where specified below:

1.  1.
    
    _Declarations:_ When a Prover loads an AI workload onto an AI compute cluster, the Prover includes explicit, specially formatted information about whether the workload is AI training or inference, and what memory locations and/or data packets will hold the model weights, training data, and usage data. This constitutes the Prover’s declaration of their models and data. (The Prover’s declaration of code is implicit in the code they load to CPUs.)
    
    1.  a.
        
        To address _non-AI_ workloads that may be done on AI compute clusters, there are various options ([Appendix A.7](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx7 "A.7 Verifying Non-AI Workloads in AI Data Centers ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
        
    
2.  2.
    
    _Verification Subgoal 1.A:_ The system software checks whether the Prover’s above claims are accurate—whether the models and data are as claimed—by analyzing the code and/or runtime data.[^95] [^96] (Note one cannot simply assume that e.g., trained model weights are directly visible as a cluster’s outputs; non-compliant model weights might be encoded in a benign-looking cluster output. This motivates collecting and analyzing data on a cluster’s internal activities.)
    
    1.  a.
        
        Checking declarations’ accuracy could involve checking that the claimed code, models, and data have various expected properties ([Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), from how the code is factored to the data movement patterns.[^97]
        
    2.  b.
        
        Procedurally, options for carrying out these checks include the following:
        
        1.  i.
            
            The systems software directly executes the checks on the cluster.
            
        2.  ii.
            
            The Verifier executes the checks via Confidential Computing (allowing for the checks to not be fully disclosed, though the result could be limited to few bits to reduce the potential for information leakage).
            
        3.  iii.
            
            The systems software outputs a certificate attesting to the logged data, which the Verifier later tests via Confidential Computing or a trusted cluster ([Section 4.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2 "4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).
            
        
    
3.  3.
    
    _Verification Subgoal 1.B:_ The system software checks that the AI models, data, and code have the required properties, e.g., verifies the results of safety evaluations. As above, the system software could do this by:
    
    1.  a.
        
        Directly executing these checks (or certifying that the Prover’s code does so and certifying its result)
        
    2.  b.
        
        Confidential Computing
        
    3.  c.
        
        Certifying the logged data to allow for later checks (via Confidential Computing or a trusted cluster)
        
    
4.  4.
    
    _Verification Subgoal 2.A:_ To verify that no large-scale uses of AI compute are undeclared (e.g., no certificates are discreetly deleted or hidden), options include the following,[^98] which could be applied jointly for extra assurances:
    
    1.  a.
        
        _Secure storage_: Chips could securely store a count of the number of certificates they have generated (or are in the process of producing),[^99] or securely store the certificates. Then, the Verifier could confirm this information by receiving it with a signature from the trusted system software (with a nonce to prevent the use of old signatures).
        
    2.  b.
        
        _Secure memory_: As a variant of the above, relevant chips could be continuously powered and thus able to store certificates in memory. Continuous power could be verified by e.g., the system software securely logging its own time since boot in memory, or storing in memory a password received from the Verifier at boot (with the password being encrypted when received and later returned).
        
    3.  c.
        
        _Compute accounting_: The system software could associate certificates with the amount of computation (e.g., in GPU-hours) used to generate the certificates.[^100] Then, assuming the Verifier can separately verify the Prover’s total compute use (e.g., they know the number of chips by Subgoal 2.B and the Prover claims to have had them all operational nearly continuously), the Prover will only be able to account for all their compute use by disclosing all their certificates.
        
        1.  i.
            
            This approach is broadly similar to compute accounting in the context of off-chip mechanisms ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), but the mechanisms for determining a workload’s compute use differ.
            
        
    4.  d.
        
        _Offline licensing_ (Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121)): AI chips could periodically share certificates and have limited functionalities if they do not receive a confirmation of receipt within an expected amount of time.
        
    

#### A.3 Network Taps & Analysis

Network taps, in principle, have various options for where they could operate (Petrie and Aarne, [2025](https://arxiv.org/html/2507.15916v2#bib.bib163)), but all face substantial challenges:

-   •
    
    Chip-level: network taps could attempt to tap the communications of individual AI chips, by tapping AI chips’ connections to memory (i.e., HBM/interposer) or to other AI chips (e.g., NVLink/NVSwitch). However, introducing network taps here would be very difficult. One would have to replace or modify these cutting-edge, TB/s-scale technologies, a task made even more difficult by the proprietary nature of NVLink and the co-packaging of AI chips with memory.
    
-   •
    
    Server-level or higher: network taps could tap communications between AI servers, server racks, pods, etc., by tapping devices such as Network Interface Cards, InfiniBand connections, or network switches. With bandwidths on the order of 100 GB/s rather than TB/s, more open specifications, and more modular designs, replacement or modification to incorporate network taps does not face quite as steep challenges as chip-level network taps. On the other hand, the lower visibility of these further-out network taps may limit their value for verification.
    

As another challenge, whether dealing with communications on the scale of 1 TB/s or 100 GB/s per tap, storing all tapped data would fill a 1 TB hard drive every ~0.1-10 seconds per tap, suggesting that substantial random sampling and/or real-time processing would be needed.

A sketch of a potential protocol (for Subgoals 1.A and 2.A) using network taps is as follows:

1.  1.
    
    A Verifier ensures that tamper-evident network taps are installed to tap the communications of every AI accelerator in a compute cluster (or only at a higher level of organization, such as one per server). The Verifier and Prover would both take various steps to verify these network taps lack malicious functionalities but still work as intended ([Section 4.2.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px1 "4.2.1.1 Prerequisites: Off-Chip Devices ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).
    
2.  2.
    
    The network taps log random samples of all data being inputted to or outputted from the attached AI accelerators. This includes GPU kernels.
    
    1.  a.
        
        This requires verifying limits on significant data exchanges via side-channels. Physical inspections, security cameras, physical barriers, and sensors may help here (though sensors to detect side-channel communication are conceptually distinct from sensors to oversee AI chips’ activity ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"))).
        
    2.  b.
        
        However, workload data could be encrypted when exchanged between accelerators, especially if Confidential Computing is being used. This could be addressed through limited disclosure of private keys (confined to Prover-overseen chips) if the hardware allows for this, or otherwise not using Confidential Computing during regular operation.[^101] That said, network taps need not worsen encryption on net; they could also potentially be used to strengthen server-level encryption (Petrie et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib164)).
        
    
3.  3.
    
    In mutually secured chips ([Section 4.2.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px1 "4.2.1.1 Prerequisites: Off-Chip Devices ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), the Verifier:
    
    1.  a.
        
        Re-runs a random sample of kernels (or instructions at a higher level of organization) to verify that the instruction set architecture functions as declared (i.e., that instructions in the kernel mean what the Verifier thinks they mean). This makes the Verifier’s analysis of kernels more informative. Re-running kernels is analogous to proof-of-learning (Jia et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib110); Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187)), but (i) for an individual kernel (or other cluster unit) instead of a whole segment of training,[^102] and with guaranteed (probabilistic) constraints on what data was or was not communicated.
        
    2.  b.
        
        Analyzes the kernels, other logged data, and Prover declarations to verify that the compute cluster executed (only) the declared high-level code. This is an unsolved problem.
        
        1.  i.
            
            Approaches could include:
            
            1.  1.
                
                Top-down: Derive information about what kernels and inputs/outputs should contain given the declared high-level code (potentially assuming a mutually trusted compiler), and check that this matches the collected data.
                
            2.  2.
                
                Bottom-up: Reconstruct the high-level code from the kernels and inputs/outputs (Petrie et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib164)).
                
            
        2.  ii.
            
            To facilitate the above or add constraints to partial workload re-execution ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), a protocol could require the Prover to send specially formatted information to network taps over the course of a workload.
            
        3.  iii.
            
            As an additional check, network taps (if also given channels for uploading data to clusters) may be able to verify that, at a given time, the majority of a cluster’s memory consists of certain data (e.g., random data or certain model weights). They could potentially do this by uploading large amounts of data to a cluster—ideally enough to fill its memory—and checking that the cluster can then return that data.
            
        
    
4.  4.
    
    To address _non-AI_ workloads that may be done on AI compute clusters, there are various options ([Appendix A.7](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx7 "A.7 Verifying Non-AI Workloads in AI Data Centers ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    

#### A.4 Partial Workload Re-Execution With Constraints

Background: A Verifier may wish to verify that a declared workload was actually run (Subgoal 1.A). For example, a Prover may make claims about what training code, data, and intermediate results (e.g., model weight checkpoints) were involved in training some model weights, and the Verifier may wish to verify these claims (Jia et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib110); Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)).[^103]

-   •
    
    The Verifier can do this by verifying _faithfulness_, i.e., that running the declared workload in fact produces the claimed results, and _uniqueness_, i.e., that a faithful declaration is infeasible to produce in practice except by actually running the declared workload (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)).
    
-   •
    
    The Verifier can verify faithfulness and uniqueness, respectively, via (1) _partial workload re-execution_, i.e., re-running (randomly sampled parts of) the Prover’s program to check if the declared results are approximately reproducible, and (2) _constraints_, i.e., checking that the declaration meets constraints which rule out spoofed declarations.[^104]
    
    -   –
        
        This approach generalizes a proposal for proof-of-training-data (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)).
        
    -   –
        
        These checks could be done on confidentiality-preserving technology ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")), to avoid leaking the Prover’s sensitive information.
        
    -   –
        
        Various constraints could be applied (Table 12), though it is unclear which constraints will be sufficient to rule out spoofs.
        
    

| Constraint type | Constraint | Applicable to AI training? | Applicable to AI inference? | Applicable to non-AI workloads? |
| --- | --- | --- | --- | --- |
| Randomness constraints | Initialization is verifiably random (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)) | ✓ | X |   |
| --- | --- | --- | --- | --- |
|  | Training data order is verifiably random (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34))[^105] |   | X |   |
| --- | --- | --- | --- | --- |
| Compute constraint | Compute accounting limits the compute usable to generate spoofs[^106] | ✓ | ✓ | ✓ |
| --- | --- | --- | --- | --- |
| Requiring more intermediate states to be replicable | Intermediate results, e.g., activations, are replicable (Sun et al., [2024b](https://arxiv.org/html/2507.15916v2#bib.bib197)) | ✓ | ✓ |   |
| --- | --- | --- | --- | --- |
|  | Optimizer states, e.g., gradients, are replicable | ✓ | X |   |
| --- | --- | --- | --- | --- |
| Requiring replication of specific logged values | Values securely logged by on-chip mechanisms (Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187)) ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) or network taps ([Appendix A.3](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx3 "A.3 Network Taps & Analysis ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) are replicable |   
✓ |   
✓ |   
✓ |
| --- | --- | --- | --- | --- |
| Time or order constraints | Values were produced in specific time intervals or orders[^107] | ✓ | ✓ | ✓ |
| --- | --- | --- | --- | --- |
| Requiring consistency with empirical trends | The norm of the weight changes lacks abrupt jumps (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)) | ✓ | X |   |
| --- | --- | --- | --- | --- |
|  | Models memorize the data most recently trained on (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)) | ✓ | X |   |
| --- | --- | --- | --- | --- |
|  | The performance of model checkpoints fits the functional form of AI scaling laws (Kaplan et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib114); Hoffmann et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib98); Villalobos, [2023](https://arxiv.org/html/2507.15916v2#bib.bib220)) |   
✓ |   
X |   
X |
| --- | --- | --- | --- | --- |
|  | Most gradients generated in training are not highly similar to each other[^108] | ✓ | X |   |
| --- | --- | --- | --- | --- |
| Sensitivity and cross-system analyses | Perturbing or replacing a component (e.g., weights, data, training algorithm) has the expected effects |   
✓ |   
✓ |   
✓ |
| --- | --- | --- | --- | --- |
| Origin constraint | A model used for large-scale inference has a declared training history | X | ✓ |   |
| --- | --- | --- | --- | --- |
| Data and code constraints | For example, code for AI training has the structure of gradient descent, in terms of code factorization.[^109] ([Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI").) |   
✓ |   
✓ |   
✓ |
| --- | --- | --- | --- | --- |
|  |  |  |  |  |
| --- | --- | --- | --- | --- |

Table 12: Possible constraints to rule out spoofs in partial workload re-execution. This compilation is non-exhaustive. A yellow square denotes partial applicability, i.e., applicability to some forms of the workload type.

Applicability to different subgoals in our verification framework:

-   •
    
    Subgoal 1.A.1: For verifying the correctness of declared AI training, a Verifier could re-execute training between randomly sampled, adjacent pairs of model checkpoints (snapshots of an AI model partway through training) (Jia et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib110)).
    
-   •
    
    Subgoal 1.A.2: For verifying the correctness of declared AI inference, a Verifier could re-execute inference on a random sample of inputs (i.e., prompts).
    
-   •
    
    Subgoal 1.A.3: For verifying the correctness of many non-AI programs, such as physics simulations, a Verifier could re-execute inference between randomly sampled, adjacent pairs of checkpoints of the simulation state, or (for programs that analyze many items, such as many possible drug designs) re-execute analysis on a random sample of items.
    

Challenges and mitigations:

-   •
    
    Attacks considered in the proof-of-training-data literature: Prior research on proof-of-training data protocols (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)) proposes constraints to counter various attacks. These attacks include “glue-ing” attacks, where records of different workloads are “glued” together; attacks that use synthetic data, data reordering, or adversarially chosen initializations to spoof training declarations; and data addition or data subtraction attacks. To counter these attacks, Choi, et al. highlight and provide experimental support for some constraints: verifiably random initializations and data orders, and checking whether model checkpoints have “memorized” their most recently seen data as expected. These are powerful defenses; randomizing the data order breaks any attack involving a carefully ordered sequence of data. Supplemental constraints (Table 12) could further limit an attacker’s options. However, there have only been limited experimental tests of these methods (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)), and online learning (where data is iteratively generated using a model as it is trained) is incompatible with a randomized data order, though it may be addressable by verifying that online learning data is not generated in a manner conducive to relevant attacks ([Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Prover code attacks: The above attacks leverage adversarially chosen data, initializations, or model checkpoints, but not adversarial code. However, a Prover might also attempt an attack that leverages non-standard behavior of the Prover’s declared code. For example, a Prover might submit AI “training” code that updates weights by overwriting them with the expected pre-computed values (encoded in the “data”), instead of executing a gradient update. As another attack, a Prover might submit code (e.g., forward pass code) that swaps in a safer model to respond to safety-related queries.[^110] Constraints discussed above like verifiably random initializations and data orders as well as memorization checks might defeat this attack, but further constraints (Table 12) and data and code validation ([Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) may be needed. Code validation could leverage backdoor detection methods (Thomas and Francillon, [2018](https://arxiv.org/html/2507.15916v2#bib.bib202)); the problem here is easier—perhaps much easier—than the fully general problem of backdoor detection.[^111]
    
-   •
    
    Novel attacks: The above approaches are heuristic-based, leaving open the possibility of novel attacks (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)), though any novel attack would face many constraints.[^112] Identifying more attacks and defenses would help, and a theoretically backed approach would be ideal.
    
-   •
    
    Inflated compute use attacks: The Verifier might wish to verify the accuracy of declared workloads, not only in terms of the workloads’ input-output behavior, but also in terms of their compute use. This is especially important if the Verifier wishes to use partial workload re-execution along with compute accounting via analog measurement of AI chips ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). A Prover may have various ways of inflating their compute use, including: (a) claiming to have executed the same workload or approximately the same workload more times than they really did, (b) submitting code with effectively unused computations (but not actually running those), and (c) declaring an inference workload whose outputs may be predicted with less compute than actually running the model (especially if the model is engineered to facilitate this).[^113] Methods to counter these attacks may include, respectively, (a) checking for (approximately) duplicate submissions and requiring the frequency of these to be low (i.e., requiring reasonable use of caching), (b) using code validation ([Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) (such as having a compiler and a code model check for these unused computations) and scaling law checks, and (c) requiring intermediate activations to be replicated.[^114] Of these, (b) appears most challenging.
    
-   •
    
    Full-stack secure implementation, including hardware: The Prover could make their program available to the Verifier as a function that reads from and writes to specified files, allowing the Verifier to check whether the program’s input-output behavior is as claimed. The program would need to be run with strong full-stack security, from the Verifier’s software to the hardware ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Confidentiality-preserving technology: A secure, confidentiality-preserving technology such as a trusted cluster or Confidential Computing would be needed for confidential data analyses ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")).
    
-   •
    
    Replicability: A Verifier may struggle to replicate a Prover’s program even if the Prover is honest, since some programs—including much large-scale AI training and inference—depend on both (i) the specific choice of hardware products, and (ii) the hardware’s random behavior. To address this, each source of variation could either be controlled (eliminating the variation, potentially at significant cost) or statistically modeled (enabling random variation to be statistically distinguished from signs of non-compliance, as long as the former does not swamp the latter). Fortunately, hardware randomness appears controllable at a low cost for inference ([Appendix A.9](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx9 "A.9 Deterministic Replication of Neural Network Inference ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), and at least the second source of variation (ii) appears small relative to the signs of non-compliance in some AI training experiments (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)).
    
-   •
    
    Data storage: The storage of data could pose confidentiality concerns, especially storing user data for verifying inference, but there are several options for mitigating these concerns, on top of using confidentiality-preserving technology. Latency and cost overheads from data storage are small. ([Appendix A.9](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx9 "A.9 Deterministic Replication of Neural Network Inference ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI").)
    
-   •
    
    Imprecision of empirical trends: Empirical trends of machine learning systems (and other workloads), such as AI scaling laws, are imprecise and may only apply in a limited domain, potentially hindering efforts to check for consistency with empirical trends as a constraint. Broader experimentation may clarify the scope and exactness with which these trends may be expected, though the scope of potential workload setups is large.
    

#### A.5 Data and Code Validation

Background: For several of the other verification mechanisms we consider in this report, a Prover could attempt to circumvent them through maliciously designed code or data:

-   •
    
    Malicious code or data may spoof efforts to re-execute portions of programs ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), or break the assurance given by workload certificates ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), by e.g., loading pre-computed results encoded in data rather than computing results normally.
    
-   •
    
    Code with many unnecessary (i.e., padded) instructions could undermine compute accounting via analog measurement of AI chips ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Malicious data may create learned backdoors that undermine safety evaluations.
    
-   •
    
    Malicious data may obfuscate the tasks a model is being trained on or used for, such as by obfuscating biological sequence data.
    

To address this, in addition to the measures discussed in these other mechanisms’ sections, a Verifier could use _data and code validation_: checking if data and code have expected properties and lack specific malicious features of concern (such as backdoors in code). Validation could be conducted over confidentiality-preserving technologies.

Applicability to different subgoals in our verification framework:

-   •
    
    Subgoals 1 and 2.A: Data and code validation cannot complete any of our verification framework’s subgoals on its own, but per the above it can strengthen other mechanisms for subgoals 1 and 2.A.
    

Challenges and mitigations:

-   •
    
    Reliable methods for data and code validation: Data and code validation could be done with various methods, each of which has its own challenges and limitations:[^115]
    
    -   –
        
        _Options for auditing data include:_
        
        -   •
            
            _Frequency analysis of data:_ Drawing from cryptanalytic frequency analysis, one could check that statistical data properties are as expected (e.g., the distribution of tokens), with expectations being based on the usual[^116] or claimed data types.
            
        -   •
            
            _Data tracing:_ A Prover could demonstrate the legitimate origin of (a random sample of a large portion of) their data, such as by stating the data’s position in a large public dataset, having third parties that they provided the data, or (for synthetic data) producing the program that generated the data. However, it may be challenging to ensure these origins of data are not compromised.[^117]
            
        -   •
            
            _Checking a pre-trained model’s accuracy on data:_ A pre-trained model’s performance on some data could serve as a measure of how similar the data is to that used to train the reference model.
            
        -   •
            
            _Inspection of data by a trained model:_ A capable AI model (e.g., a code model) could examine data to assess whether it looks as expected and to identify malicious features of concern.[^118]
            
        
    -   –
        
        _Options for auditing code include:_
        
        -   •
            
            _Code factorization constraints:_ The Verifier could check that the Prover’s code is factored in the expected manner for the workload, such as having the structure of gradient descent (or a variant thereof).[^119] [^120]
            
        -   •
            
            _Formal verification of code:_ Systematic analysis could prove that code behaves in certain ways, though this may come with severe formatting constraints and thus engineering slow-downs and limitations. Formal verification of software is an active (Hasan and Tahar, [2015](https://arxiv.org/html/2507.15916v2#bib.bib84); Souyris et al., [2009](https://arxiv.org/html/2507.15916v2#bib.bib193)) but challenging research field.
            
        -   •
            
            _Inspection of code by a trained model:_ Analogous to the above “Inspection of data by a trained model.”
            
        
    
-   •
    
    Data storage: The storage of data, especially usage prompts, could pose confidentiality concerns, but there are several options for mitigating these, on top of using confidentiality-preserving technology ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")) for disclosing and analyzing the stored data. In addition, latency and cost overheads from data storage are small. ([Appendix A.10](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx10 "A.10 Storing Sensitive Data for Verification ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI").)
    
-   •
    
    Full-stack secure implementation, including hardware: The Verifier would need uncompromised software and hardware to securely run their checks ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Confidentiality-preserving technology: A secure, confidentiality-preserving technology such as a trusted cluster or Confidential Computing would be needed for confidential data analyses ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")).
    

#### A.6 Compute Accounting via Analog Sensors

Background: In _compute accounting_, one verifies the amount of AI compute used by a Prover, and verifies that a high fraction of this compute use can be accounted for by declared uses.[^121] Ideally, the declared AI compute use would add up to 100% of the AI compute use. If a sufficiently high fraction of compute use can be accounted for, this implies the Prover cannot have done large-scale, undeclared use of AI compute, among the computing clusters being accounted for. Off-chip analog sensors could enable three partly compatible[^122] approaches to compute accounting (Table 13), if combined with other mechanisms (such as partial workload re-execution, [Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) for verifying declared uses and ensuring the integrity of analog sensors ([Section 4.2.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px1 "4.2.1.1 Prerequisites: Off-Chip Devices ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).

A core problem here is that there is no simple way to deduce an AI chip’s rate of computation, even with analog measurements. An AI chip’s utilization can vary from below 1% to around 90% depending on workload types, hardware, and implementations (Pope et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib169); Erdil and Besiroglu, [2024](https://arxiv.org/html/2507.15916v2#bib.bib62)). Utilization also has a complex relationship to analog measurements, in part because of the distinction between “model FLOP utilization (MFU)” (which only counts unique operations) and “hardware FLOP utilization (HFU)” (which also counts recomputed operations).[^123]

| Implementation option | How the Verifier estimates _total_ AI compute use | How the Verifier estimates AI compute use _accounted for_ by declared uses |
| --- | --- | --- |
| _Option A:_ Assume declared workloads were executed efficiently (i.e., optimizing MFU). | Count the active AI _chip-hours_ (e.g., GPU-hours, TPU-hours). | $\text{Chip-hours accounted for }=$ $\frac{\text{Declared model OP}}{\text{Theoretical\ OP/hr}\ \cdot\ \text{MFU}}$, where _Declared Model OP_ are verified via Subgoal 1.A, and _Theoretical OP/hr_ and _MFU_ are estimated conservatively (i.e., high).[^124] |
| --- | --- | --- |
| _Option B:_ Estimate hardware FLOP from measurements, and cap the allowed hardware FLOP per model FLOP. | Conservatively estimate _hardware OP_ based on analog measurements. | $\text{Hardware-OP accounted for }=$ $\text{Declared\ model\ OP}\cdot\frac{\text{HFU}}{\text{MFU}}$, where _Declared Model OP_ are verified via Subgoal 1.A, and $\frac{HFU}{MFU}$ is estimated conservatively (i.e., low, an estimate of 1 being most conservative). |
| --- | --- | --- |
| _Option C:_ Check that workloads’ physical signatures are accounted for (i.e., do fine-grained workload classification). | Count the active AI _chip-hours_ (e.g., GPU-hours, TPU-hours). | $\text{Chip-hours accounted for }=\text{Chip-hours with an expected physical signature}$, where the expected physical signature corresponds to a workload verified in Subgoal 1.A, is measured with external sensors, and may consist of a power draw pattern over time, input/output bandwidth pattern over time, etc. |
| --- | --- | --- |
|  |  |  |
| --- | --- | --- |

Table 13: Three implementation options for compute accounting via off-chip analog sensors.

Applicability to different subgoals in our verification framework:

-   •
    
    Subgoal 2.A: Operations accounting would verify the absence of undeclared, large-scale uses of known AI data centers (i.e., large-scale, declared AI compute clusters).
    

Challenges and mitigations: The above options raise many implementation challenges, including estimating the mentioned variables.

-   •
    
    Challenges specific to option A:
    
    -   –
        
        Estimating optimal Model FLOP Utilization (MFU):
        
        -   •
            
            MFU can vary greatly across workload types, hardware, and implementations (Pope et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib169); Erdil and Besiroglu, [2024](https://arxiv.org/html/2507.15916v2#bib.bib62)). For a given workload type and cluster, optimal MFU could be coarsely approximated as the MFU known to have been achieved on similar workloads and clusters, on which there is private and public data (Epoch AI, [2024b](https://arxiv.org/html/2507.15916v2#bib.bib60)). Optimal MFU could be more precisely estimated with theoretical modeling (Erdil and Schneider-Joseph, [2024](https://arxiv.org/html/2507.15916v2#bib.bib63); Erdil, [2025](https://arxiv.org/html/2507.15916v2#bib.bib61)). Still, significant error bars may remain. These could be mitigated by complementing MFU estimates with monitoring of physical signatures (Option C); if a Prover finds an algorithmic change that can improve their MFU beyond the conservatively estimated value, this algorithmic change could be reflected in an unexpected physical signature.
            
        
    -   –
        
        Estimating AI chips’ theoretical peak performance:
        
        -   •
            
            Peak performance could be estimated by comparing chips to known reference chips, or more precisely by delayering and scanning chip features ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
            
        
    
-   •
    
    Challenges specific to option B:
    
    -   –
        
        Estimating hardware operations from measurements:
        
        -   •
            
            To verify the _number of total operations_ done in given AI data centers in some period (from $t_{a}$ to $t_{b}$), one approach could be to measure AI chips’ power draw (P) over time (Watts per second), and then multiply it by the chips’ energy efficiency (OP per Watt) (determined based on AI hardware measurements (M) such as active GPU-hours, power draw and temperature at the time, available cooling solutions, reference measurements, perhaps magnetometer measurements (Matyunin et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib133)), and the extent of hardware wearing out):  
            
            ${\text{Num. total\ operations}}_{(t_{a},\ t_{b})}\ =\ \int_{t_{a}}^{t_{b}}P(t)\cdot\text{OP\_per\_W}(M(t))\ dt$.
            
        -   •
            
            _Inferring energy efficiency (OP/W) from hardware measurements:_ AI chips’ energy efficiency has a complex relationship with the chips’ power consumption and other properties; that is, determining $\text{OP\_per\_W}(M(t))$ and an appropriate set of measurements is not straightforward.[^125] Still, it may be feasible to model this relationship with small error bars, for any given workload.[^126] Notably, one might only be able to infer a “menu of options” that a chip may have been used for (e.g., N operations if used in some training configuration, N’ operations if used in some inference configuration); the Prover could then account for the chip’s use by showing that they have the results of one of those options.[^127]
            
        
    
-   •
    
    Challenges specific to option C:
    
    -   –
        
        Determining workloads’ expected physical signatures:
        
        -   •
            
            To determine what physical signature a workload has on given hardware, the Verifier could run the workloads themselves on sufficiently similar hardware (as a physically secured, trusted cluster), though this approach may be vulnerable to backdoored hardware. Alternatively, the Prover may be able to derive signatures by modeling the workload (Erdil and Schneider-Joseph, [2024](https://arxiv.org/html/2507.15916v2#bib.bib63); Erdil, [2025](https://arxiv.org/html/2507.15916v2#bib.bib61)).
            
        
    -   –
        
        Spoofed physical signatures:
        
        -   •
            
            Perhaps an AI workload could be condensed to use fewer chip-hours while preserving its physical signature. This would undermine the use of physical signatures for compute accounting. It could thus be valuable to assess the viability of such attacks, and, if needed, to identify constraints or additional measurements that would defeat these attacks.
            
        
    
-   •
    
    Challenges for multiple options:
    
    -   –
        
        Counting AI chip-hours: For declared AI compute clusters (undeclared ones being addressed separately through Subgoal 2.B), AI chip-hours could be measured, for example, with electricity meters on the Power Distribution Unit (PDU) connected to each server, or potentially more or less fine-grained units, with additional means such as tamper-evident packaging and video cameras ([Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) to detect tampering or circumvention. Chip-hours are a fairly coarse metric with various physical correlates, and they are familiar as the industry’s standard billing metric, so many methods may work.
        
    -   –
        
        Counting declared model operations: To verify the _number of declared operations_ done in given AI data centers in some period, one could (via confidentiality-preserving technology: [Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")) (i) apply analytical methods to declared models, data, and code (Narayanan et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib140); Chowdhery et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib35)), and/or re-execute portions of programs with (ii) software profilers or (iii) hardware performance counters (Sevilla et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib185); Heim et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib90)).
        
    -   –
        
        Avoiding false alarms from under-estimating compliant compute use: In the above options (A) and (B), the Verifier makes a conservatively high estimate of the Prover’s MFU, so that a Prover cannot obtain unaccounted-for compute by achieving higher-than-assumed MFU. These conservatively high estimates are, respectively, assuming a highly efficient MFU, and assuming that the MFU is close to the measured HFU. However, these assumptions might not hold for honest Provers, potentially leading honest Provers to be unable to account for their estimated compute use. To mitigate this, for (A), the Verifier could estimate an optimal MFU achievable in practice rather than using a large over-estimate,[^128] and they could technically assist the Prover in reaching the efficient assumed MFU (potentially with compensation for the cost savings).[^129] For (B), the verification protocol could require the Prover to refrain from surpassing the assumed HFU/MFU ratio (at the limit, require HFU=MFU, though this would carry substantial efficiency costs for training).
        
    -   –
        
        Fine-grained measurement of AI hardware:
        
        -   •
            
            For measuring AI chips’ power draw (and potentially other properties), several questions arise:
            
            -   ·
                
                _What objects to measure:_ Measurements could be made at various levels of granularity, from an entire AI data center to individual AI chips. More fine-grained measurements will tend to offer lower error bars,[^130] but require more sophisticated and numerous equipment.[^131]
                
            -   ·
                
                _What metrics to measure:_ These could be determined based on the analysis, experimentation, and example metrics discussed above and below, considering tradeoffs between precision and cost.
                
            -   ·
                
                _When to measure:_ Measurement could be (i) periodic and sufficiently frequent that it would be impractical to lower performance just before measurement, or it could be (ii) random and sufficiently frequent to allow for small error bars.
                
            -   ·
                
                _How to do anti-tamper measurement:_ Through tamper-evident or tamper-proof packaging.[^132] [^133]
                
            -   ·
                
                _How to measure with security for the Prover:_ Through Prover-inspected equipment being examined only on site, under supervision.[^134]
                
            
        
    -   –
        
        Full-stack secure implementation, including hardware: The Verifier would need uncompromised software and hardware to securely run their software checks ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
        
    -   –
        
        Confidentiality-preserving technology: A secure, confidentiality-preserving technology such as a trusted cluster or Confidential Computing would be needed for confidential data analyses ([Section 3.2](https://arxiv.org/html/2507.15916v2#Sx4.SSx2 "3.2 The Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI")). (Confidential Computing, though, would be out of scope for off-chip verification.)
        
    -   –
        
        Duplicate model operations: These are addressed by Subgoal 1.A ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
        
    

#### A.7 Verifying Non-AI Workloads in AI Data Centers

Data center GPUs can be used for a variety of workloads beyond AI, raising the question of how a Verifier could distinguish these non-AI workloads from AI workloads. At a high level, options include:

1.  1.
    
    The Prover could:
    
    1.  a.
        
        Execute the workload on non-AI-specialized chips instead (e.g., CPUs or ASICs)
        
    2.  b.
        
        Complete the intended task with neural networks (thus allowing the workload to be verified as an AI workload)
        
    
2.  2.
    
    Alternatively, the Verifier, in collaboration with the Prover, could:
    
    1.  a.
        
        Use a verification protocol developed for the non-AI workload, perhaps one analogous to proof-of-learning (Jia et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib110)) ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) or, where feasible, analytic methods ([Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).
        
    2.  b.
        
        Classify the workload as non-AI (e.g., based on manual or automatic analysis of the code or of data movement patterns, or perhaps the cluster architecture)
        
    3.  c.
        
        Use non-confidentiality-preserving methods (for non-sensitive workloads)
        
    

#### A.8 Whistleblower Programs

Background: Programs and laws that encourage employees to blow the whistle on violations are commonplace ([National Whistleblower Center,](https://arxiv.org/html/2507.15916v2#bib.bib142) ), contributing to approximately $2 billion or more in SEC fines in 2023.[^135] In the AI industry, large-scale AI projects tend to involve hundreds of employees (Table 9)—hundreds of individuals who might be able to report any large-scale violations to a Verifier. In addition to AI developers’ own employees, other organizations throughout the AI supply chain have employees who can blow the whistle on some violations, especially undeclared AI data centers. Employees could blow the whistle on a Prover’s (i) non-compliant AI activities, (ii) falsified declarations, or (iii) attempts to circumvent another verification mechanism (Table 14). Formal whistleblower programs could promote appropriate forms of whistleblowing by providing (would-be) whistleblowers with information they can check, disclosure protocols, and incentives (including intrinsic motivation, social norms, protection, and financial rewards). Provers may view formal whistleblower programs as legitimate, so Provers may be willing to take verifiable actions that facilitate whistleblowing (in contrast to espionage), such as allowing employees to privately talk with a Verifier.

Challenges and mitigations:

-   •
    
    Secure and confidential communication with potential whistleblowers. A Prover might try to not only retaliate against whistleblowers, but also entirely block or alter their messages. Standard approaches to secure internet communication (e.g., TLS, VPNs, and Tor) are not designed to secure the communications of parties who may be under video surveillance, or whose computers may be backdoored. Instead, a more secure option is for such employees to make in-person visits to a building physically secured by a Verifier. To prevent the Prover from detecting or blocking whistleblowers’ visits to these locations, the verification protocol could require the Prover to periodically send various relevant employees to visit the Verifier-secured building (e.g., as brief visits to an office near the Prover’s offices).[^136] [^137] [^138]
    
-   •
    
    Ensuring whistleblowers have enough information to report signs of violations. Even if an employee is not aware of a violation, they may have knowledge inconsistent with a Prover’s declarations (Table 14). To learn if this is the case, the Verifier could, within employee interviews, ask the employee to check the Prover’s relevant declarations, or to share information that should match the relevant declarations, preferably via a confidentiality-preserving technology. A “low-tech” option for confidentiality preservation could involve a carefully overseen personal computer.[^139] However, perhaps a Prover can have sufficient compartmentalization and employee loyalty for all accomplices to lie.
    
-   •
    
    Further incentivizing whistleblowers: Beyond the anonymity protections discussed above, a whistleblower system could likely be strengthened by (potentially mandated) measures that make employees more morally, socially, or financially motivated to blow the whistle on violations. These could include trainings, certifications, knowledge tests, hiring practices, safety culture,[^140] financial rewards (U.S. Securities and Exchange Commission, [2025](https://arxiv.org/html/2507.15916v2#bib.bib215); Internal Revenue Service, [2025](https://arxiv.org/html/2507.15916v2#bib.bib103); Commodity Futures Trading Commission, [2025](https://arxiv.org/html/2507.15916v2#bib.bib40)),[^141] and asylum or refugee status. Still, as above, it is unclear if these incentives would overcome a major Prover initiative for compartmentalization and employee loyalty.
    
-   •
    
    Avoiding excess disclosure: Employees could be allowed to disclose only a very small amount of information to the Verifier, as discussed in above footnotes. Further, the Prover and Verifier could jointly state agreed-on, reasonable bounds of protected whistleblowing (including high-level descriptions of potential violations and information to investigate further, but excluding digital transfers of Prover models, data, or code outside of a confidentiality-preserving technology). Parties could also agree on what questions or information a Verifier may share with an employee, so that the Prover could learn from their employees if the Verifier is inappropriately pressuring them to disclose IP.
    

| Type of violation | Some employees who would have information about the violation |
| --- | --- |
| Non-compliant declarations of large-scale AI development or deployment (intended to be detected by Subgoals 1.A or 1.B) | • AI researchers and engineers who contribute to the declared activity and thus could notice if model origins, output origins, or evaluations/properties are falsely declared, or if workloads are designed to spoof verification • Officials who deliberate on, order, or coordinate the violation (e.g., senior executives, top advisory bodies, and lower-level managers, in government and colluding companies) • Spoofers: researchers and engineers who circumvent on- and off-chip verification mechanisms, if these are present[^142] |
| --- | --- |
| Undeclared, large-scale uses of known AI compute clusters (intended to be detected by Subgoal 2.A) | • AI researchers and engineers who contribute to the undeclared activity, or to another compliant activity that is altered to hide the non-compliant activity • Officials who deliberate on, order, or coordinate the violation • Spoofers: Researchers and engineers who circumvent on- and off-chip verification mechanisms, if these are present • Compute cluster oversight or management staff |
| --- | --- |
| Undeclared, large-scale AI compute (intended to be detected by Subgoal 2.B) | • AI researchers and engineers who contribute to the undeclared activity, or to another compliant activity that is altered to hide the non-compliant activity • Officials who deliberate on, order, or coordinate the violation • Spoofers: Staff who circumvent other verification mechanisms, if present (e.g., by diverting chips and breaking compliance locks) • Data center construction and operations staff (e.g., maintenance and security staff) • Supplier staff who supply e.g., AI chips, energy, and other data center equipment • Compute cluster design and setup staff • Administrative (e.g., relevant finance, procurement, legal) staff |
| --- | --- |
|  |  |
| --- | --- |

Table 14: Types of employees who would have information about different types of violations. Personnel-based verification could leverage these employees for verification.

#### A.9 Deterministic Replication of Neural Network Inference

We identify six potential obstacles to replicable neural network inference, which hinder verification. (That is, six potential obstacles in addition to fixing the model version and inputs, which are of course needed.) These obstacles include both non-determinism within a given technology stack, and variation across technology stacks. Fortunately, each of these obstacles can be eliminated via relatively straightforward methods, suggesting exactly replicable inference is feasible.

| Replicability challenge in neural network inference | A method to eliminate the non-determinism |
| --- | --- |
| Intentional randomness: Inference code might explicitly call (pseudo)random number generators, e.g., for sampling with non-zero temperature. | Fix all random seeds, i.e., have the Prover record them and then share them with the verifier for replication, and avoid unreplicable (“true”) random number generators. |
| --- | --- |
| Mixture-of-experts with batch-level routing: A mixture-of-experts (MoE) model might select which expert an input is routed to in a manner that depends on other inputs in a batch, for efficiency.[^143] Then, repeatedly running a model on the same input among different batches may lead to different outputs (Puigcerver et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib171); 152334H, [2023](https://arxiv.org/html/2507.15916v2#bib.bib1)). | Fix batches, i.e., replicate inference at the level of entire batches rather than individual inputs. |
| --- | --- |
| Non-replicable rounding errors: Due to rounding errors, floating-point addition and multiplication (and fixed-point multiplication) are not associative; e.g., the order in which terms are added (the “accumulation order”) can affect results (Goldberg, [1991](https://arxiv.org/html/2507.15916v2#bib.bib75)). As a result, when accumulation order is not deterministic, floating point arithmetic has inconsistent results. A non-deterministic accumulation order (whether within or across devices) can occur due to e.g., algorithmic choices (Two Sigma, [2017](https://arxiv.org/html/2507.15916v2#bib.bib209)) and device differences (Nagarajan et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib139)). Aside from accumulation order, the use of different numerical precisions for activations or intermediate computations could lead to different rounding errors. | The simplest solution is to do inference with integer operations of a consistent precision, by converting (“quantizing”) floating-point model weights to integers, and also using consistent precisions for intermediate computations. Quantization is common for efficiency (Jacob et al., [2017](https://arxiv.org/html/2507.15916v2#bib.bib108)), though if one trains in FP8, then quantizing offers no advantage on H100 GPUs (NVIDIA, [b](https://arxiv.org/html/2507.15916v2#bib.bib150)). Integer arithmetic is associative (as it is exact), avoiding the problem of floating-point arithmetic (with the potential exception of overflows, discussed below). Another option is using “fully deterministic \[computing\] infrastructure,” as Google DeepMind did for training Gemini 1 (Gemini Team et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib73)). This infrastructure leveraged TPUs’ long-standing determinism (Jouppi et al., [2017](https://arxiv.org/html/2507.15916v2#bib.bib112)). In contrast, with GPUs, as a then-Google employee explained, “the threading model means you get better performance with atomics \[and thus non-deterministic operation order\]” (Bradbury, [2021](https://arxiv.org/html/2507.15916v2#bib.bib23)). |
| --- | --- |
| Non-replicable overflow: Some overflow behaviors, such as saturation, lead to non-associative arithmetic.[^144] As a result, as above, non-deterministic accumulation order could have non-deterministic results. Similarly, tech stacks which differ in their overflow behavior could have different results. | Use overflow behavior that is associative, such as wrapping, i.e., modular arithmetic. |
| --- | --- |
| Inconsistent rounding procedures: The Prover and Verifier might use different rounding procedures, beyond different accumulation orders. Rounding arises even with integer operations, as some computations (e.g., layer normalization) involve division. | The Prover and Verifier could use the same rounding procedures. In a conventional transformer with integer operations, consistent rounding could be achieved via minor edits to the few library functions that use division. |
| --- | --- |
| Hardware errors: Finally, errors at the hardware level (e.g. from manufacturing defects or cosmic rays) could unpredictably change outputs. | Hardware errors are very rare in practice—e.g., two studies find “soft” memory hardware errors on the order of up to one or thirty per _billion hours_ of a device’s computation (Slayman, [2011](https://arxiv.org/html/2507.15916v2#bib.bib192); Sridharan et al., [2015](https://arxiv.org/html/2507.15916v2#bib.bib194))—so they can be addressed via occasionally re-doing computations that result in high discrepancies, and if needed monitoring hardware health and using error correction code (ECC) memory. |
| --- | --- |
|  |  |
| --- | --- |

Table 15: Some replicability challenges for neural network inference and methods to address them.

#### A.10 Storing Sensitive Data for Verification

Some verification mechanisms, such as partial workload re-execution ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), require AI training data or usage prompts to be stored for verification. However, the data in question may be highly sensitive, e.g., it could be individuals’ medical data or states’ classified intelligence. The mere storage of such data by the relevant AI company could pose risks of leaks and might be in tension with current data protection regulations or consumer desires. Indeed, some prominent AI companies offer opt-in “zero data retention” options ([OpenAI,](https://arxiv.org/html/2507.15916v2#bib.bib157) ; [Anthropic,](https://arxiv.org/html/2507.15916v2#bib.bib7) ) There are practical reasons to store training data,[^145] but these may not apply as strongly to usage data.

Options for improving confidentiality in data storage. There are various options for addressing confidentiality concerns around data storage, and these options could be combined. Here, we only consider addressing concerns regarding data _storage_ by a party demonstrating their compliance; concerns regarding data _examination_ by the Verifier are meant to be addressed by confidentiality-preserving technologies like Confidential Computing ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) and trusted clusters ([Section 4.2.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px1 "4.2.1.1 Prerequisites: Off-Chip Devices ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).

1.  1.
    
    _Data storage exemption for small data owners:_ Actors who own small amounts of data used for AI inference could be allowed to verify the compliance of the data by simply asserting it to the Verifier, without further checks. With an appropriate definition of “small,” a large-scale violation would require collusion among an impractically high number of data owners, which could be revealed by associated personnel-based verification mechanisms ([Section 4.3](https://arxiv.org/html/2507.15916v2#Sx5.SSx3 "4.3 Personnel-Based Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). (Know-your-customer checks for a small sample of data owners would also be needed to ensure the “small users” really are small users.) However, the resulting conclusion would likely be imprecise, as small data users might not notice if their data is processed by a somewhat smaller model than claimed, which could undermine compute accounting.
    
2.  2.
    
    _Option for data owners to store their own data:_ The data owners could keep their own logs of the data and submit it when asked. This may be especially feasible for larger organizations, so this option may be a good complement to a data storage exemption for small data owners.
    
3.  3.
    
    _Short data storage period:_ The data storage period could be short (perhaps days), especially when no discrepancies are found.
    
4.  4.
    
    _Secure and local data storage:_ Data could be stored securely, e.g., encrypted in a physically secure data center, and/or locally in the data owner’s jurisdiction.
    
5.  5.
    
    _Storing only a verifiably small sample of data:_ As a more technically complex option, the Prover may be able to do verifiably random sampling of their own data and then only store the small sample of their data. However, verifiably random sampling likely requires exact replication ([Appendix A.9](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx9 "A.9 Deterministic Replication of Neural Network Inference ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) and solutions to further complications.[^146] A more feasible variant may be for the Verifier to blindly do random sampling of data for the Prover to store for later analysis, by sampling over hashes of data provided by the Prover.[^147]
    

Overhead costs of storing usage data are tiny. Latency and costs of data storage could also matter, but back-of-the-envelope calculations suggest latency and cost overheads would be on the order of 0.01% or lower compared to just doing inference on the data,[^148] [^149] since processing data with a large AI model is so much more slow and expensive than simply storing the data.

### B. Broader Regime Design

#### B.1 Compute Accounting vs. Other Kinds of Accounting

AI compute is relatively specialized and large in its physical footprint, making it more suitable to being accounted for than other resources used in AI development and deployment (Table 16).

| Resource used for AI development and deployment | Specialization: To what extent is the resource narrowly used for large-scale AI? | Physical footprint: How large is the physical footprint of this resource? |
| --- | --- | --- |
| Compute: high-end AI chips, typically in data centers | Relatively specialized | Relatively large[^150] |
| --- | --- | --- |
| Data: AI training datasets | Somewhat[^151] | Small |
| --- | --- | --- |
| Algorithms: e.g., model architectures and optimization algorithms for large-scale AI | Relatively specialized[^152] | Small |
| --- | --- | --- |
| Human capital: frontier AI researchers and engineers | Somewhat[^153] | Medium |
| --- | --- | --- |
| Electricity: power for data centers | Somewhat, in some cases[^154] | Relatively large[^155] |
| --- | --- | --- |
| Water: water for the cooling systems of data centers | No | Varies[^156] |
| --- | --- | --- |
|  |  |  |
| --- | --- | --- |

Table 16: Prominent resources used for AI development and deployment (Buchanan, [2020](https://arxiv.org/html/2507.15916v2#bib.bib26); Pilz and Heim, [2023](https://arxiv.org/html/2507.15916v2#bib.bib165)), by two properties that make verification less intrusive: specialization and physical footprint. More specialized resources can be overseen with less need to oversee unrelated activities, which could pose major confidentiality and logistical challenges.

#### B.2 Verification of Narrower Rules

Our verification framework ([Section 3](https://arxiv.org/html/2507.15916v2#Sx4 "3. Verification Framework ‣ Verifying International Agreements on AI")) is a general framework for verifying rules on AI models, data, and code created or used in large-scale AI development _and_ deployment, including negative rules (e.g., rules that _none_ of an actor’s large-scale AI developments or deployments pose unmanageable risks). However, for verifying compliance with some hypothetical, narrower (and perhaps, more blunt) rules, not all verification subgoals are needed:

-   •
    
    Compute ownership caps (i.e., “compute caps”): To verify a compute cap—i.e., that the AI compute clusters some actor owns have no more than some maximum combined computing power—a Verifier can just ask for declarations of compute ownership and then only complete Subgoal 2.B: verifying that there are no undeclared, large-scale AI compute clusters. Since the rule being verified here would not be sensitive to usage, there is no need to verify claims about usage.
    
-   •
    
    Positive rules: To verify rules that just require executing some workloads (rather than _not_ executing some workloads), e.g., a rule that requires AI companies to actually run inference consistently with what they claim (rather than running a cheaper model), a Verifier just needs Subgoal 1.A: verifying correctness.
    
-   •
    
    Negative rules about large-scale AI development: To just verify that an actor refrained from certain kinds of AI development (without verifying claims about AI _deployment_), it is not necessary to verify the correctness of claimed uses of AI compute for purposes other than AI development. Instead, it can suffice to otherwise verify the total amount of AI compute used for AI development vs. other purposes—such as via verified workload classification by cloud providers (Heim et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib90)), or via some chips being locked into “fixed sets” that are impractical for training (Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121))—and then to just carry out verification with regards to the compute that _was_ used for AI development.
    
-   •
    
    Negative rules about large-scale AI deployment: The case is the same as the above, except switching “development” with “deployment.”
    

#### B.3 Acting on Ambiguous Findings

A Verifier might have ambiguous findings—evidence that is inconclusive about the Prover’s compliance.[^157] What should the Verifier do then? We highlight some increasingly escalatory options.

Requests for clarification. Simple requests for clarification could resolve some issues. Studies of arms control have highlighted permanent consultative commissions as helpful in this regard.[^158]

Focused investigation. Ambiguous findings could trigger a focused investigation of the specific organizations, facilities, activities, or employees whose compliance is ambiguous, at greater cost than would be practical for general verification. The Verifier could apply their verification methods with increased intensity to the suspicious area.[^159] The associated costs also incentivize the Prover to carry out their role carefully, to reduce the incidence of focused investigations. These intensified efforts would either reveal more clear evidence of non-compliance or fail to do so; in either case, the ambiguity would be at least partly resolved.

More intrusive verification. If needed, the Verifier could escalate an investigation to include more intrusive verification methods than would normally be allowed. For example, the Verifier could (with the Prover’s cooperation) increase the amount of information that compliance tests output.[^160] Additionally, the Prover and Verifier could authorize an expanding set of humans (not just automated programs) to directly inspect the Prover’s declarations, beginning with the Prover’s most relevant employees (who may already have this access via whistleblower programs) ([Appendix A.8](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx8 "A.8 Whistleblower Programs ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) and potentially escalating to the Verifier directly inspecting Prover code, which would violate confidentiality-preservation.

Precautionary pauses. As an emergency measure, in extreme cases the Verifier could demand some or all of the Prover’s AI compute clusters be turned off while a suspected violation is investigated, or take other actions to mitigate imminent risks. Such a pause would assure the Verifier that a violation using declared AI compute clusters is not ongoing, but it could come at a high economic cost.

Partial penalties or threats. The enforcing parties could apply a penalty in part or with some probability, to deter a strategy of using multiple ambiguous violations to carry out a significant violation.

### C. Methodology Details

#### C.1 Methodology for Analysis

Our analysis consisted of the following steps.

1\. Developing a framework of verification subgoals. To develop and assess a framework that breaks down verification into a series of subgoals ([Figure 1](https://arxiv.org/html/2507.15916v2#Sx1.F1 "Figure 1 ‣ Key Findings ‣ Summary ‣ Verifying International Agreements on AI")), we took as a starting point a framework used by the International Atomic Energy Agency (IAEA), identified through our literature review. The IAEA divides verification into (i) verifying that declarations are “correct” and (ii) verifying that declarations are “complete” (Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)). These ultimately corresponded to Subgoal 1.A and Subgoal 2 in our framework. We then identified ways this framework fell short of the following criteria, and modified the framework until it met the criteria:

-   •
    
    _Deductive validity:_ If all subgoals are completed perfectly, this justifies a series of claims from which the desired confirmation of compliance ([Section 3.1](https://arxiv.org/html/2507.15916v2#Sx4.SSx1 "3.1 Context for This Framework ‣ 3. Verification Framework ‣ Verifying International Agreements on AI"); [Section 2](https://arxiv.org/html/2507.15916v2#Sx3 "2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")) deductively follows.[^161] Without this, verification subgoals would not suffice for verifying compliance.
    
-   •
    
    _Flexibility:_ The framework can represent existing verification proposals identified in our literature review, a few additional potential verification systems we considered,[^162] and variants. This makes the framework broadly applicable for analysis.
    
-   •
    
    _Avoiding excess complexity:_ The framework’s subgoals all contribute to its validity or flexibility, to avoid wasting analysts’ time or government resources.[^163]
    

2\. Identifying verification mechanisms. From the sources described above, we identified candidate verification options by compiling verification mechanisms that:

-   •
    
    Have been explicitly proposed, in our reviewed literature, for verifying rules on AI;
    
-   •
    
    Have been used for verification in other contexts (e.g., domestic regulation, arms control) per our reviewed literature;
    
-   •
    
    Have been proposed for related purposes (e.g., enforcing rules on AI);
    
-   •
    
    Would leverage a known regularity, ‘fingerprint,’ or resource requirement of AI activities; _or_
    
-   •
    
    Are variants of the above, varied to mitigate specific weaknesses or to complete a different verification subgoal than originally considered.
    

3\. Assessing, red teaming, and enhancing verification mechanisms; and identifying open problems. For each identified mechanism, we iterated between assessing the mechanism and enhancing it. In the assessment stage, we evaluated various properties of each mechanism: what subgoals in our verification framework the mechanism could complete or support, its _probability of detecting_ a violation quickly[^164] if done by a highly motivated major government, the frequency of _false alarms_, the _confidentiality_ and _security_ for the Prover, the _setup speed_ in terms of time required for R&D and implementation, and the financial or computational _cost_. We focus on these properties because history and incentives suggest they will be important for the acceptability of a verification regime (Krass, [1985](https://arxiv.org/html/2507.15916v2#bib.bib120); Coe and Vaynman, [2019](https://arxiv.org/html/2507.15916v2#bib.bib39); Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13); Nevo et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib143)). After assessing each property and identifying challenges for it,[^165] we considered how the mechanism could be enhanced to address these challenges (e.g., through a different implementation or additional compliance tests), and then we repeated the assessment on the enhanced version of the mechanism, up to the point where further assessment or enhancement appeared to require a substantial research project of its own.

We included a candidate verification option in our overview of options (i.e., in [Figure 2](https://arxiv.org/html/2507.15916v2#Sx1.F2 "Figure 2 ‣ Key Findings ‣ Summary ‣ Verifying International Agreements on AI") and [Section 4](https://arxiv.org/html/2507.15916v2#Sx5 "4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) if our subsequent analysis suggested that the verification option:

1.  1.
    
    At least plausibly meets all desired criteria (e.g., robustness, confidentiality protection, and cost—discussed further below) for completing at least one verification subgoal, while being meaningfully distinct from other included verification options in terms of its tradeoffs or assumptions; _or_
    
2.  2.
    
    Likely strengthens another verification mechanism that meets the above condition (1), while being meaningfully distinct from other included verification options.
    

4\. Identifying and analyzing verification layers. We generated verification layers by starting with the list of plausibly robust verification mechanisms (i.e., those meeting criterion (1) above). Then, we searched for ways to partition this list of mechanisms into verification layers, i.e., identify (as much as possible) disjoint subsets of these mechanisms such that each subset has similar tradeoffs and assumptions and contains one mechanism applicable to each verification subgoal. Finally, we analyzed the verification layers by using the fact that each layer’s challenges are the combined challenges of the mechanisms that make up the layer, already examined per the above analysis.

#### C.2 Methodology for Expert Interviews and Interview Protocol

Interviewee selection: To identify expert interviewees, we considered: our professional networks, including in academia, industry, and nonprofits; authors of papers from our literature review; and other experts recommended by our initial interviewees. Within these groups, we looked for individuals with expertise in highly relevant fields, determined based on our literature review: computer security, computing hardware, machine learning, and AI policy (especially frontier AI verification).

Our interviews complied with policies on human subjects research, including by maintaining interviewee confidentiality per our data safeguarding plan, to err on the side of caution.

Interview protocol: Our interviews, which were semi-structured, were guided by our interview protocol, which is reproduced below in a lightly condensed form.

This is not a comprehensive or formal protocol. We will prioritize or vary questions based on an interviewee’s areas of expertise, we will phrase questions based on an interviewee’s existing familiarity, and we will ask follow-up questions based on an interviewee’s initial responses.

Prior to asking the following questions, we will briefly reiterate the goals of the study and the fact that participation and all questions are optional. We may show interviewees a few draft reference figures summarizing some of the report’s content, so they can more easily identify room for improvement.

Questions for experts with broad relevant expertise (listed in the default planned order):

-   •
    
    Does the verification framework in this figure seem like a useful, valid, and clear way to break down verification?
    
-   •
    
    What are some promising verification mechanisms for completing each verification step?
    
-   •
    
    Are there promising verification mechanisms that we’re missing?
    
-   •
    
    Have we miscategorized the potential functions or reliability of any of the verification mechanisms, as summarized in this figure? Are we missing major challenges faced by any?
    
-   •
    
    Are there other considerations or challenges you’d suggest we keep in mind?
    
-   •
    
    With regard to our section identifying directions for future work, what types of research or future work would be especially productive here? What would lay the groundwork for rigorous red-teaming by world-leading organizations?
    
-   •
    
    What specific research projects would most advance the field?
    
-   •
    
    How could this report be more useful?
    
-   •
    
    Overall, how promising does each category of verification mechanisms seem?
    
-   •
    
    Who else should we talk to, or what else should we read, to inform this study?
    

Example questions for experts with highly specialized expertise:

-   •
    
    How precisely could an AI accelerator’s utilization be estimated by physical measurements?
    
-   •
    
    How might information from data center suppliers be used to detect covert AI data centers?
    
-   •
    
    To what extent might AI data center maintenance be automated?
    
-   •
    
    Could most AI hardware’s secure boot functionality be made infeasible to deactivate through a firmware update?
    
-   •
    
    How likely is it that Confidential Computing on H100 GPUs is securely implemented?
    
-   •
    
    What would be the performance penalty of entirely running a large AI training or inference workload with Confidential Computing?
    

#### C.3 Additional R&D Problems for Verification

This report highlights selected R&D problems for verification (Table 10; [Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI")). In this appendix, we list additional verification R&D problems that tentatively did _not_ meet our criteria[^166] ([Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI")) for inclusion in the selected problems, but may still be valuable to work on:

-   •
    
    Thresholds for AI chips and AI compute clusters: For AI chip monitoring to be implemented (e.g., by chain-of-custody verification, network taps, or analog sensors), one must determine which chips and clusters are in scope (Reuel et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib173)), ideally including all compute that would enable serious violations while excluding all the rest. Some cases are unambiguously in-scope (e.g., large data centers of leading GPUs), but there are many edge cases.[^167] Still, there is already substantial relevant research, including sophisticated modeling (Erdil and Schneider-Joseph, [2024](https://arxiv.org/html/2507.15916v2#bib.bib63); Erdil, [2025](https://arxiv.org/html/2507.15916v2#bib.bib61)), data collection (Epoch AI, [2024a](https://arxiv.org/html/2507.15916v2#bib.bib59)), and definitions of AI chips for export controls (Patel et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib161); Burga et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib29)).
    
-   •
    
    Evaluations, mitigations, and rule specifications: As we discuss ([Section 5](https://arxiv.org/html/2507.15916v2#Sx6 "5. Open Problems in Verification ‣ Verifying International Agreements on AI")), effective rule specifications, which may include technical evaluations and risk mitigations, are under-developed and crucial. Still, these challenges are already subject to extensive research, including by industry and governments ([Frontier Model Forum,](https://arxiv.org/html/2507.15916v2#bib.bib69) ; Shenk, [2024](https://arxiv.org/html/2507.15916v2#bib.bib190); [UK AI Security Institute,](https://arxiv.org/html/2507.15916v2#bib.bib211) ), more so than the R&D problems we highlight (Table 10).
    
-   •
    
    Counting AI chip-hours: This does not appear to require significant R&D ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Replicability: Non-deterministic workloads could pose challenges for verification. Still, the sources of non-determinism we identified appear sufficiently controllable without significant R&D ([Appendix A.9](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx9 "A.9 Deterministic Replication of Neural Network Inference ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). Remaining implementation difficulties may be resolved over the course of pilot programs.
    
-   •
    
    Estimating AI chips’ theoretical performance: This does not appear to require significant R&D ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Abuse-resistant enforcement: This does not appear to require significant R&D, as there are multiple existing proposals and some tradeoffs may be inevitable ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).
    
-   •
    
    Counting declared model operations: This does not appear to require significant R&D, as there is significant relevant existing work ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Using information from data center suppliers: This does not appear to require significant R&D and would only be valuable as a supplemental mechanism ([Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).
    
-   •
    
    Adversarial robustness of design information verification: This does not appear to require significant R&D and would only be valuable as a supplemental mechanism ([Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).
    
-   •
    
    Sensitive data storage: This does not appear to require significant R&D ([Appendix A.10](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx10 "A.10 Storing Sensitive Data for Verification ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
    
-   •
    
    Robust, high-level workload classification: Distinguishing between training and inference workloads is too coarse-grained to verify most of the rules in our scope ([Section 2.1](https://arxiv.org/html/2507.15916v2#Sx3.SSx1 "2.1 Rules on AI Models, Data, and Code ‣ 2. Verification Scope and Research Methodology ‣ Verifying International Agreements on AI")), especially as synthetic data generation (inference) may be an increasingly large component of training. Still, it could be valuable ([Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")).
    

Theoretically, one could also pursue R&D on lie detection for interviews of personnel, but we do not recommend this because of the potential for such technology to be abused.

#### C.4 Scope: Additional Notes

Further detail on our definitions of “large-scale” compute use:

-   •
    
    To see why a lower threshold could intrude on consumer hardware, note that 100 high-end gaming GPUs—widely sold consumer products (Garreffa, [2022](https://arxiv.org/html/2507.15916v2#bib.bib72))—have the same computational power as 33 contemporaneous AI chips (H100 GPUs) (NVIDIA, [2023a](https://arxiv.org/html/2507.15916v2#bib.bib152), [b](https://arxiv.org/html/2507.15916v2#bib.bib150)).[^168] Thus, to practically verify how the computing power of _tens_ of AI chips is used, one would have to practically verify that no actor secretly assembles 100 high-end gaming GPUs.
    
-   •
    
    We do not give a more precise definition, as that could misleadingly suggest that a specific quantity is known to be especially significant. To the contrary, a smaller cluster can typically execute the same workloads as a slightly larger cluster if given slightly more time. Additionally, small differences in training or inference compute (all else equal) tend to correspond to small differences in model performance (Owen, [2024](https://arxiv.org/html/2507.15916v2#bib.bib160); OpenAI et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib159); OpenAI, [2024](https://arxiv.org/html/2507.15916v2#bib.bib158)).
    
-   •
    
    The practicality of verifying AI compute use above some threshold would likely be affected, not just by how high that threshold is in absolute terms, but also by how high that threshold is relative to the total amount of AI compute. A small fraction of all AI compute could fall within the margin of error of verification mechanisms, especially for mechanisms such as analog sensors that may require more approximate analysis.
    

Further detail on the AI models, data, and code we consider:

-   •
    
    We do not assume verified models are _necessarily_ publicly available via public interfaces or published weights, which would enable more direct testing. Instead, we consider verifying models that could range from open-source models to AI companies’ internal, advanced models.
    

#### C.5 Related Work

We draw on a range of related technical, historical, and strategic work, including:

##### C.5.1 Work on Frontier AI Verification

Overviews of AI verification: Previous papers overview options for AI verification (Brundage et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib25); Wasil et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib223); Scher and Thiergart, [2024](https://arxiv.org/html/2507.15916v2#bib.bib179); Harack et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib83)). These works explore a range of verification mechanisms. This report aims to provide an overview with improved clarity and detail ([Section 1.1](https://arxiv.org/html/2507.15916v2#Sx2.SSx1 "1.1 Contributions ‣ 1. Introduction ‣ Verifying International Agreements on AI")).

Verifying rules on large-scale AI: Beyond overview papers, some research has advanced specific verification proposals. Shavit ([2023](https://arxiv.org/html/2507.15916v2#bib.bib187)) makes a high-level proposal for verifying rules on large-scale AI development through compute monitoring. Choi et al. ([2023](https://arxiv.org/html/2507.15916v2#bib.bib34)), building on work by Jia et al. ([2021](https://arxiv.org/html/2507.15916v2#bib.bib110)), propose and experimentally demonstrate a protocol for verifying “training transcripts” of neural networks. Trager et al. ([2023](https://arxiv.org/html/2507.15916v2#bib.bib206)) propose an international governance framework for civilian AI involving certification of state jurisdictions, though the focus on civilian AI means this approach is not designed for robustness to major state circumvention efforts. Petrie and Aarne ([2025](https://arxiv.org/html/2507.15916v2#bib.bib163)) propose Flexible Hardware-Enabled Guarantees (FlexHEGs), a family of verification mechanisms involving network taps and tamper-resistant enclosures.

Confidentiality-preserving technologies and secure machine learning: Researchers have advanced cryptographic methods for confidential audits or implementations of AI workloads, including zero-knowledge proofs (ZK-SNARKs) (Chen et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib33); Waiwitlikhit et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib222); Sun et al., [2024a](https://arxiv.org/html/2507.15916v2#bib.bib196)) and Confidential Computing (Confidential Computing Consortium, [2021](https://arxiv.org/html/2507.15916v2#bib.bib41)). Confidential Computing may be highly applicable to verifying international agreements on AI ([Section 4.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1 "4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). On the other hand, ZK-SNARKs, despite rapid progress in relative terms, as of early 2025 still have enormous compute overhead costs[^169] and do not preserve the confidentiality of model architectures.[^170]

##### C.5.2 Broader Related Work

Arms control verification: A large literature explores verification of historical arms control treaties, including their institutional design (Dai, [2002](https://arxiv.org/html/2507.15916v2#bib.bib46)), negotiation (Coe and Vaynman, [2019](https://arxiv.org/html/2507.15916v2#bib.bib39); Carlson et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib31)), implementation (Chayes, [1972](https://arxiv.org/html/2507.15916v2#bib.bib32); Krass, [1985](https://arxiv.org/html/2507.15916v2#bib.bib120)), technical methods (Krass, [1985](https://arxiv.org/html/2507.15916v2#bib.bib120); Office of Technology Assessment, [1990](https://arxiv.org/html/2507.15916v2#bib.bib156); Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)), and applicability to AI (Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13)). Much of this work focuses on nuclear arms control agreements, where verification has been especially developed. The Conventional Armed Forces in Europe Treaty had verification measures similar to those of nuclear arms control (Nuclear Threat Initiative, [2016](https://arxiv.org/html/2507.15916v2#bib.bib146)). The Chemical Weapons Convention authorizes “challenge inspections,” but none have been conducted (Arms Control Association, [2021](https://arxiv.org/html/2507.15916v2#bib.bib8)). The Biological Weapons Convention lacks formal verification, and it has been notoriously violated (Nuclear Threat Initiative, [2024](https://arxiv.org/html/2507.15916v2#bib.bib147)).

Verification frameworks: The International Atomic Energy Agency (IAEA) verifies declarations’ correctness and completeness (Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)), as do many financial audits ([Cambridge Dictionary,](https://arxiv.org/html/2507.15916v2#bib.bib30) ). Our verification framework draws on these frameworks ([Appendix C.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx1 "C.1 Methodology for Analysis ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")).

Governance of AI compute: Sastry et al. ([2024](https://arxiv.org/html/2507.15916v2#bib.bib178)) argue that computing power presents promising opportunities for AI governance, including compute verification.

On-chip / hardware-enabled governance mechanisms: Aarne et al. ([2024](https://arxiv.org/html/2507.15916v2#bib.bib2)) and Kulp et al. ([2024](https://arxiv.org/html/2507.15916v2#bib.bib121)) propose hardware-enabled governance mechanisms as potential tools to advance U.S. export control priorities, including via verifying compliant use. Aarne, et al. also discuss potential applications for verification of international agreements on AI.

Compute accounting and measurement: Heim et al. ([2024](https://arxiv.org/html/2507.15916v2#bib.bib90)) discuss compute accounting as a governance mechanism, particularly in the context of enforcing domestic regulations. Sevilla et al. ([2022](https://arxiv.org/html/2507.15916v2#bib.bib185)), among others, propose and implement methods for estimating the compute used to train a model based on hyperparameters or hardware use.

## Glossary

_AI accelerator:_ A circuit board containing an AI chip, along with memory and other components ([Figure 9](https://arxiv.org/html/2507.15916v2#Ax2.F9 "Figure 9 ‣ Glossary ‣ Verifying International Agreements on AI")).

_AI chip:_ A computer chip that efficiently executes computational operations for AI development or deployment, such as NVIDIA H100s ([Figure 9](https://arxiv.org/html/2507.15916v2#Ax2.F9 "Figure 9 ‣ Glossary ‣ Verifying International Agreements on AI")).

_AI compute cluster:_ An interconnected collection of AI servers and support equipment ([Figure 9](https://arxiv.org/html/2507.15916v2#Ax2.F9 "Figure 9 ‣ Glossary ‣ Verifying International Agreements on AI")).

_AI data center:_ A facility that hosts AI compute clusters and supporting infrastructure ([Figure 9](https://arxiv.org/html/2507.15916v2#Ax2.F9 "Figure 9 ‣ Glossary ‣ Verifying International Agreements on AI")).

_AI server:_ An enclosed unit of AI accelerators, together with supporting chips and other supporting equipment ([Figure 9](https://arxiv.org/html/2507.15916v2#Ax2.F9 "Figure 9 ‣ Glossary ‣ Verifying International Agreements on AI")).

_Artificial intelligence (AI):_ Computer programs capable of sophisticated cognitive tasks, and related technologies, particularly in the deep learning paradigm.

_Prover:_ An entity, such as a company or government, that makes a claim which they aim to convince a Verifier of.

_Verification:_ The act or process of checking whether a claim is true, such as checking whether a party has complied with a requirement as claimed.

_Verifier:_ An entity, such as a government agency or international agency, that aims to verify a claim.

_Workload:_ A computer program, such as a program for AI development or deployment, particularly on a compute cluster.

![Refer to caption](https://arxiv.org/html/2507.15916v1/x9.png)

Figure 9: How AI computing hardware is organized. AI data centers are facilities that host AI compute clusters and supporting infrastructure. AI compute clusters are made up of racks of AI servers and support equipment. These servers are enclosed units of AI accelerators, supporting chips, and other devices. AI accelerators are circuit boards with AI chips, memory, and other components. AI chips are computer chips that efficiently execute computational operations for AI development or deployment. The figure’s images are generic images for illustrative purposes.

## Abbreviations

AI Artificial intelligence

AISI AI Security Institute or (Center for) AI Standards and Innovation

ASIC Application-Specific Integrated Circuit

CC Confidential Computing

CPU Central Processing Unit

CS Computer science

DARPA Defense Advanced Research Projects Agency

ECC Error correction code

FLOP Floating point operation(s)

FlexHEG Flexible Hardware-Enabled Guarantee

GPU Graphics processing unit

HDL Hardware Description Language

HFU Hardware FLOP (floating point operations) utilization

HSM Hardware security module

IAEA International Atomic Energy Agency

IC Intelligence community

IP Intellectual property

IT Information technology

MFU Model FLOP (floating point operations) utilization

ML Machine learning

NIST National Institute of Standards and Technology

NSF National Science Foundation

OP Operation(s)

OS Open-source or operating system

OSINT Open-source intelligence

PDU Power Distribution Unit

ROM Read-only-memory

R&D Research and development

SEC Securities and Exchange Commission

TLS Transport Layer Security

TPU Tensor Processing Unit

UK United Kingdom

UN United Nations

US United States

VPN Virtual private network

## References

-   152334H (2023) 152334H. Non-determinism in GPT-4 is Caused by Sparse MoE. Simple Thoughts, June 2023. URL [https://152334h.github.io/blog/non-determinism-in-gpt-4/](https://152334h.github.io/blog/non-determinism-in-gpt-4/).
-   Aarne et al. (2024) Onni Aarne, Tim Fist, and Caleb Withers. Secure, Governable Chips. Technical report, Center for a New American Security, 2024. URL [https://www.cnas.org/publications/reports/secure-governable-chips](https://www.cnas.org/publications/reports/secure-governable-chips).
-   Agnes Shiny et al. (2019) Rachel N. Agnes Shiny, B. Fahimunnisha, S. Akilandeswari, and S. Joyes Venula. Integration of Clock Gating and Power Gating in Digital Circuits. In _2019 5th International Conference on Advanced Computing & Communication Systems (ICACCS)_, pages 704–707, 2019. doi: 10.1109/ICACCS.2019.8728370. URL [https://doi.org/10.1109/ICACCS.2019.8728370](https://doi.org/10.1109/ICACCS.2019.8728370).
-   Aktas et al. (2023) Erdem Aktas, Cfir Cohen, Josh Eads, James Forshaw, and Felix Wilhelm. Intel Trust Domain Extensions (TDX) Security Review. Technical report, Google, 2023. URL [https://services.google.com/fh/files/misc/intel\_tdx\_-\_full\_report\_041423.pdf](https://services.google.com/fh/files/misc/intel_tdx_-_full_report_041423.pdf).
-   Amazon Staff (2024) Amazon Staff. Amazon and Anthropic Deepen Their Shared Commitment to Advancing Generative AI, 2024. URL [https://www.aboutamazon.com/news/company-news/amazon-anthropic-ai-investment](https://www.aboutamazon.com/news/company-news/amazon-anthropic-ai-investment).
-   Amazon Web Services (2023) Amazon Web Services. TR-4958: Best Practices for Electronic Design Automation Workloads with Amazon FSx for NetApp ONTAP. Technical report, Amazon Web Services, 2023. URL [https://www.netapp.com/media/82062-Best\_Practices\_for\_EDA\_Workloads\_with\_FSx\_for\_ONTAP\_02102023.pdf](https://www.netapp.com/media/82062-Best_Practices_for_EDA_Workloads_with_FSx_for_ONTAP_02102023.pdf).
-   (7) Anthropic. How Long Do You Store Personal Data? URL [https://privacy.anthropic.com/en/articles/10023548-how-long-do-you-store-personal-data](https://privacy.anthropic.com/en/articles/10023548-how-long-do-you-store-personal-data).
-   Arms Control Association (2021) Arms Control Association. Reinforcing the Global Norm Against Chemical Weapons Use, February 2021. URL [https://www.armscontrol.org/policy-white-papers/2021-02/reinforcing-global-norm-against-chemical-weapons-use](https://www.armscontrol.org/policy-white-papers/2021-02/reinforcing-global-norm-against-chemical-weapons-use).
-   Armstrong et al. (2013) Stuart Armstrong, Nick Bostrom, and Carl Shulman. Racing to the Precipice: A Model of Artificial Intelligence Development. Technical Report 2013-1, Future of Humanity Institute, University of Oxford, 2013. URL [https://arxiv.org/abs/2202.07785](https://arxiv.org/abs/2202.07785).
-   Askell et al. (2019) Amanda Askell, Miles Brundage, and Gillian Hadfield. The Role of Cooperation in Responsible AI Development, 2019. URL [https://arxiv.org/abs/1907.04534](https://arxiv.org/abs/1907.04534).
-   (11) ASML. How Microchips Are Made. URL [https://www.asml.com/en/technology/all-about-microchips/how-microchips-are-made](https://www.asml.com/en/technology/all-about-microchips/how-microchips-are-made).
-   (12) Association for Computing Machinery. ACM Software System Award. URL [https://awards.acm.org/software-system](https://awards.acm.org/software-system).
-   Baker (2023) Mauricio Baker. Nuclear Arms Control Verification and Lessons for AI Treaties, 2023. URL [https://arxiv.org/abs/2304.04123](https://arxiv.org/abs/2304.04123).
-   Beers and Toner (2025) Kendrea Beers and Helen Toner. Enabling External Scrutiny of AI Systems with Privacy-Enhancing Technologies, 2025. URL [https://arxiv.org/abs/2502.05219](https://arxiv.org/abs/2502.05219).
-   Bengio et al. (2024) Yoshua Bengio, Geoffrey Hinton, Andrew Yao, et al. Managing extreme AI risks amid rapid progress. _Science_, 384(6698):842–845, 2024. doi: 10.1126/science.adn0117. URL [https://doi.org/10.1126/science.adn0117](https://doi.org/10.1126/science.adn0117).
-   Bengio et al. (2025a) Yoshua Bengio, Sören Mindermann, Daniel Privitera, et al. International AI Safety Report, 2025a. URL [https://www.gov.uk/government/publications/international-ai-safety-report-2025](https://www.gov.uk/government/publications/international-ai-safety-report-2025).
-   Bengio et al. (2025b) Yoshua Bengio, Sören Mindermann, Daniel Privitera, et al. International Scientific Report on the Safety of Advanced AI (Interim Report), 2025b. URL [https://www.gov.uk/government/publications/international-scientific-report-on-the-safety-of-advanced-ai/international-scientific-report-on-the-safety-of-advanced-ai-interim-report](https://www.gov.uk/government/publications/international-scientific-report-on-the-safety-of-advanced-ai/international-scientific-report-on-the-safety-of-advanced-ai-interim-report).
-   Bernardi et al. (2025) Jamie Bernardi, Gabriel Mukobi, Hilary Greaves, Lennart Heim, and Markus Anderljung. Societal Adaptation to Advanced AI, 2025. URL [https://arxiv.org/abs/2405.10295](https://arxiv.org/abs/2405.10295).
-   Bhunia et al. (2014) Swarup Bhunia, Michael S. Hsiao, Mainak Banga, and Seetharam Narasimhan. Hardware Trojan Attacks: Threat Analysis and Countermeasures. _Proceedings of the IEEE_, 102(8):1229–1247, 2014. doi: 10.1109/JPROC.2014.2334493. URL [https://doi.org/10.1109/jproc.2014.2334493](https://doi.org/10.1109/jproc.2014.2334493).
-   Biden Jr. (2023) Joseph R. Biden Jr. Executive Order on the Safe, Secure, and Trustworthy Development and Use of Artificial Intelligence, 2023. URL [https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/](https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/). Archived at [https://web.archive.org/web/20250120092101/https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/](https://web.archive.org/web/20250120092101/https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/).
-   Boneh et al. (2018) Dan Boneh, Joseph Bonneau, Benedikt Bünz, and Ben Fisch. Verifiable Delay Functions. Cryptology ePrint Archive, Paper 2018/601, 2018. URL [https://eprint.iacr.org/2018/601](https://eprint.iacr.org/2018/601).
-   Bordelon (2024) Brendan Bordelon. In DC, a new wave of AI lobbyists gains the upper hand, May 2024. URL [https://www.politico.com/news/2024/05/12/ai-lobbyists-gain-upper-hand-washington-00157437](https://www.politico.com/news/2024/05/12/ai-lobbyists-gain-upper-hand-washington-00157437).
-   Bradbury (2021) James Bradbury. Tweet by @jekbradbury, 2021. URL [https://x.com/jekbradbury/status/1383159313535889412](https://x.com/jekbradbury/status/1383159313535889412). Archived at [https://web.archive.org/web/20211127024503/https://twitter.com/jekbradbury/status/1383159313535889412](https://web.archive.org/web/20211127024503/https://twitter.com/jekbradbury/status/1383159313535889412).
-   Brown et al. (2020) Tom B. Brown, Benjamin Mann, Nick Ryder, et al. Language Models are Few-Shot Learners, 2020. URL [https://arxiv.org/abs/2005.14165](https://arxiv.org/abs/2005.14165).
-   Brundage et al. (2020) Miles Brundage, Shahar Avin, Jasmine Wang, et al. Toward Trustworthy AI Development: Mechanisms for Supporting Verifiable Claims, 2020. URL [https://arxiv.org/abs/2004.07213](https://arxiv.org/abs/2004.07213).
-   Buchanan (2020) Ben Buchanan. The AI Triad and What It Means for National Security Strategy. Technical report, Center for Security and Emerging Technology, 2020. URL [https://cset.georgetown.edu/publication/the-ai-triad-and-what-it-means-for-national-security-strategy/](https://cset.georgetown.edu/publication/the-ai-triad-and-what-it-means-for-national-security-strategy/).
-   Bureau of Industry and Security (2023) Bureau of Industry and Security. Commerce Strengthens Restrictions on Advanced Computing Semiconductors, Semiconductor Manufacturing Equipment, and Supercomputing Items to Countries of Concern, 2023. URL [https://www.bis.doc.gov/index.php/documents/about-bis/newsroom/press-releases/3355-2023-10-17-bis-press-release-acs-and-sme-rules-final-js/file](https://www.bis.doc.gov/index.php/documents/about-bis/newsroom/press-releases/3355-2023-10-17-bis-press-release-acs-and-sme-rules-final-js/file).
-   Burek (2024) John Burek. The Best PCI Express NVMe Solid State Drives (SSDs) for 2025, November 2024. URL [https://www.pcmag.com/picks/the-best-pci-express-nvme-solid-state-drives-ssds](https://www.pcmag.com/picks/the-best-pci-express-nvme-solid-state-drives-ssds). Updated article.
-   Burga et al. (2025) Tao Burga, Arushi Gupta, and Tim Fist. The H20 Problem: Inference, Supercomputers, and US Export Control Gaps. Technical report, Institute for Progress, 2025. URL [https://ifp.org/the-h20-problem/](https://ifp.org/the-h20-problem/).
-   (30) Cambridge Dictionary. financial audit. URL [https://dictionary.cambridge.org/us/dictionary/english/financial-audit](https://dictionary.cambridge.org/us/dictionary/english/financial-audit).
-   Carlson et al. (2020) John Carlson, Vladimir Kuchinov, and Thomas Shea. The IAEA’s Safeguards System as the Non-Proliferation Treaty’s Verification Mechanism, May 2020. URL [https://media.nti.org/documents/NTI\_Paper\_Safeguards\_FINAL\_5-8-20.pdf](https://media.nti.org/documents/NTI_Paper_Safeguards_FINAL_5-8-20.pdf).
-   Chayes (1972) Abram Chayes. An inquiry into the workings of arms control agreements. _Harvard Law Review_, 85(5):905–969, 1972. ISSN 0017811X. URL [https://doi.org/10.2307/1339933](https://doi.org/10.2307/1339933).
-   Chen et al. (2024) Bing-Jyue Chen, Suppakit Waiwitlikhit, Ion Stoica, and Daniel Kang. ZKML: An Optimizing System for ML Inference in Zero-Knowledge Proofs. In _Proceedings of the Nineteenth European Conference on Computer Systems_, EuroSys ’24, page 560–574, New York, NY, USA, 2024. Association for Computing Machinery. ISBN 9798400704376. doi: 10.1145/3627703.3650088. URL [https://doi.org/10.1145/3627703.3650088](https://doi.org/10.1145/3627703.3650088).
-   Choi et al. (2023) Dami Choi, Yonadav Shavit, and David Duvenaud. Tools for Verifying Neural Models’ Training Data, 2023. URL [https://arxiv.org/abs/2307.00682](https://arxiv.org/abs/2307.00682).
-   Chowdhery et al. (2022) Aakanksha Chowdhery, Sharan Narang, Jacob Devlin, et al. PaLM: Scaling Language Modeling with Pathways, 2022. URL [https://arxiv.org/abs/2204.02311](https://arxiv.org/abs/2204.02311).
-   Chuvakin and Porter (2021) Anton Chuvakin and Nelly Porter. What You Need to Know About Confidential Computing. Google Cloud Blog, July 2021. URL [https://cloud.google.com/blog/products/identity-security/confidential-computing-data-encryption-during-processing](https://cloud.google.com/blog/products/identity-security/confidential-computing-data-encryption-during-processing).
-   Clark (2024) Jack Clark. What does 1025 versus 1026 mean?, March 2024. URL [https://jack-clark.net/2024/03/28/what-does-1025-versus-1026-mean/](https://jack-clark.net/2024/03/28/what-does-1025-versus-1026-mean/).
-   Clark (2022) Mitchell Clark. Nvidia says its ‘proprietary information’ is being leaked by hackers, 2022. URL [https://www.theverge.com/2022/3/1/22957212/nvidia-confirms-hack-proprietary-information-lapsus](https://www.theverge.com/2022/3/1/22957212/nvidia-confirms-hack-proprietary-information-lapsus).
-   Coe and Vaynman (2019) Andrew J. Coe and Jane Vaynman. Why Arms Control Is So Rare. _American Political Science Review_, 2019. URL [https://www.cambridge.org/core/journals/american-political-science-review/article/why-arms-control-is-so-rare/BAC79354627F72CDDDB102FE82889B8A](https://www.cambridge.org/core/journals/american-political-science-review/article/why-arms-control-is-so-rare/BAC79354627F72CDDDB102FE82889B8A).
-   Commodity Futures Trading Commission (2025) Commodity Futures Trading Commission. Whistleblower Program, 2025. URL [https://www.whistleblower.gov/](https://www.whistleblower.gov/).
-   Confidential Computing Consortium (2021) Confidential Computing Consortium. A Technical Analysis of Confidential Computing. Technical report, Confidential Computing Consortium, October 2021. URL [https://confidentialcomputing.io/wp-content/uploads/sites/10/2023/03/CCC-A-Technical-Analysis-of-Confidential-Computing-v1.3\_unlocked.pdf](https://confidentialcomputing.io/wp-content/uploads/sites/10/2023/03/CCC-A-Technical-Analysis-of-Confidential-Computing-v1.3_unlocked.pdf).
-   Council on Foreign Relations (a) Council on Foreign Relations. How 9/11 Reshaped Foreign Policy, a. URL [https://www.cfr.org/timeline/how-911-reshaped-foreign-policy](https://www.cfr.org/timeline/how-911-reshaped-foreign-policy).
-   Council on Foreign Relations (b) Council on Foreign Relations. U.S.-Russia Nuclear Arms Control, b. URL [https://www.cfr.org/timeline/us-russia-nuclear-arms-control](https://www.cfr.org/timeline/us-russia-nuclear-arms-control).
-   Crider (2022) Michael Crider. Nvidia’s crypto-crippling ’Lite Hash Rate’ LHR tech has been defeated, May 2022. URL [https://www.pcworld.com/article/698962/nvidia-rtx-cards-fully-unlocked-for-crypto-miners.html](https://www.pcworld.com/article/698962/nvidia-rtx-cards-fully-unlocked-for-crypto-miners.html).
-   (45) CVE Details. Linux Kernel (Operating system): Product details, threats and statistic. URL [https://www.cvedetails.com/product/47/Linux-Linux-Kernel.html?vendor\_id=33](https://www.cvedetails.com/product/47/Linux-Linux-Kernel.html?vendor_id=33).
-   Dai (2002) Xinyuan Dai. Information Systems in Treaty Regimes. _World Politics_, 54(3):405–436, July 2002. URL [https://library.fes.de/libalt/journals/swetsfulltext/15305574.pdf](https://library.fes.de/libalt/journals/swetsfulltext/15305574.pdf).
-   DatacenterDynamics (2024) DatacenterDynamics. An extended field of vision: How Hanwha Vision achieves results for partners by taking in views, 2024. URL [https://www.datacenterdynamics.com/en/marketwatch/an-extended-field-of-vision/](https://www.datacenterdynamics.com/en/marketwatch/an-extended-field-of-vision/).
-   Day (2023) Brittany Day. Linux: Recent Security Advisory on Network Risks and Protective Measures, 2023. URL [https://linuxsecurity.com/features/linux-vulnerabilities-the-poison-the-antidote](https://linuxsecurity.com/features/linux-vulnerabilities-the-poison-the-antidote).
-   De Oliveira Nunes et al. (2019) Ivan De Oliveira Nunes, Karim Eldefrawy, Norrathep Rattanavipanon, Michael Steiner, and Gene Tsudik. VRASED: A Verified Hardware/Software Co-Design for Remote Attestation. In _28th USENIX Security Symposium (USENIX Security 19)_, pages 1429–1446, Santa Clara, CA, August 2019. USENIX Association. ISBN 978-1-939133-06-9. URL [https://www.usenix.org/conference/usenixsecurity19/presentation/de-oliveira-nunes](https://www.usenix.org/conference/usenixsecurity19/presentation/de-oliveira-nunes).
-   De Vynck et al. (2023) Gerrit De Vynck, Rachel Lerman, and Nitasha Tiku. Microsoft’s AI chatbot is going off the rails, 2023. URL [https://www.washingtonpost.com/technology/2023/02/16/microsoft-bing-ai-chatbot-sydney/](https://www.washingtonpost.com/technology/2023/02/16/microsoft-bing-ai-chatbot-sydney/).
-   Dean (2015) Benjamin Dean. Why companies have little incentive to invest in cybersecurity. _The Conversation_, 2015. URL [https://theconversation.com/why-companies-have-little-incentive-to-invest-in-cybersecurity-37570](https://theconversation.com/why-companies-have-little-incentive-to-invest-in-cybersecurity-37570).
-   Dennis et al. (2025) Claire Dennis, Sam Manning, Stephen Clare, Boxi Wu, Jake Okechukwu Effoduh, Chinasa T. Okolo, Lennart Heim, and Katya Klinova. Options and Motivations for International AI Benefit Sharing. Technical report, Centre for the Governance of AI, 2025. URL [https://www.governance.ai/research-paper/options-and-motivations-for-international-ai-benefit-sharing](https://www.governance.ai/research-paper/options-and-motivations-for-international-ai-benefit-sharing).
-   Department for Science, Innovation & Technology (2024) Department for Science, Innovation & Technology. Frontier AI Safety Commitments, AI Seoul Summit 2024, 2024. URL [https://www.gov.uk/government/publications/frontier-ai-safety-commitments-ai-seoul-summit-2024/frontier-ai-safety-commitments-ai-seoul-summit-2024](https://www.gov.uk/government/publications/frontier-ai-safety-commitments-ai-seoul-summit-2024/frontier-ai-safety-commitments-ai-seoul-summit-2024).
-   Dhar et al. (2024) Aritra Dhar, Clément Thorens, Lara Magdalena Lazier, and Lukas Cavigelli. Ascend-CC: Confidential Computing on Heterogeneous NPU for Emerging Generative AI Workloads, 2024. URL [https://arxiv.org/abs/2407.11888](https://arxiv.org/abs/2407.11888).
-   Dragan et al. (2024) Anca Dragan, Helen King, and Allan Dafoe. Introducing the Frontier Safety Framework, May 2024. URL [https://deepmind.google/discover/blog/introducing-the-frontier-safety-framework/](https://deepmind.google/discover/blog/introducing-the-frontier-safety-framework/).
-   Eadline (2023) Doug Eadline. NVIDIA H100: Are 550,000 GPUs Enough for This Year? _HPCwire_, 2023. URL [https://www.hpcwire.com/2023/08/17/nvidia-h100-are-550000-gpus-enough-for-this-year/](https://www.hpcwire.com/2023/08/17/nvidia-h100-are-550000-gpus-enough-for-this-year/).
-   Edery et al. (2020) Yigal Edery, Joe Foster, Ahmed Abbas Hassan, Brett Henning, Bryan Kelly, Nate Klein, Jubin Mehta, Alberto Munoz, Rajeev Sharma, Wojtek Powiertowski, Eric Spada, and Ben Stoltz. Attestation of System Components v1.0: Requirements and Recommendations. Technical report, Open Compute Project, November 2020. URL [https://www.opencompute.org/documents/attestation-v1-0-20201104-pdf](https://www.opencompute.org/documents/attestation-v1-0-20201104-pdf).
-   Efrati and Holmes (2024) Amir Efrati and Aaron Holmes. Why OpenAI Could Lose $5 Billion This Year, 2024. URL [https://www.theinformation.com/articles/why-openai-could-lose-5-billion-this-year](https://www.theinformation.com/articles/why-openai-could-lose-5-billion-this-year).
-   Epoch AI (2024a) Epoch AI. Data on Machine Learning Hardware, November 2024a. URL [https://epoch.ai/data/machine-learning-hardware](https://epoch.ai/data/machine-learning-hardware).
-   Epoch AI (2024b) Epoch AI. Data on Notable AI Models, 2024b. URL [https://epoch.ai/data/notable-ai-models](https://epoch.ai/data/notable-ai-models).
-   Erdil (2025) Ege Erdil. Inference economics of language models, 2025. URL [https://arxiv.org/abs/2506.04645](https://arxiv.org/abs/2506.04645).
-   Erdil and Besiroglu (2024) Ege Erdil and Tamay Besiroglu. Introducing the Distributed Training Interactive Simulator, June 2024. URL [https://epoch.ai/blog/introducing-the-distributed-training-interactive-simulator](https://epoch.ai/blog/introducing-the-distributed-training-interactive-simulator).
-   Erdil and Schneider-Joseph (2024) Ege Erdil and David Schneider-Joseph. Data movement limits to frontier model training, 2024. URL [https://arxiv.org/abs/2411.01137](https://arxiv.org/abs/2411.01137).
-   (64) European Union. AI Act. URL [https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai).
-   Fang et al. (2024) Richard Fang, Rohan Bindu, Akul Gupta, Qiusi Zhan, and Daniel Kang. Teams of LLM Agents can Exploit Zero-Day Vulnerabilities, 2024. URL [https://arxiv.org/abs/2406.01637](https://arxiv.org/abs/2406.01637).
-   FAR.AI (2024) FAR.AI. Scientists Call For International Cooperation on AI Red Lines, 2024. URL [https://far.ai/news/scientists-call-for-international-cooperation-on-ai-red-lines](https://far.ai/news/scientists-call-for-international-cooperation-on-ai-red-lines).
-   Fatahalian and Olukotun (2023) Kayvon Fatahalian and Kunle Olukotun. Why Parallelism? Why Efficiency? Lecture slides, Stanford University CS149, 2023. URL [https://gfxcourses.stanford.edu/cs149/fall23/lecture/whyparallelism/slide\_54](https://gfxcourses.stanford.edu/cs149/fall23/lecture/whyparallelism/slide_54).
-   Fournier (2016) Vincent Fournier. Surveying Safeguarded Material 24/7, 2016. URL [https://www.iaea.org/newscenter/news/surveying-safeguarded-material-24/7](https://www.iaea.org/newscenter/news/surveying-safeguarded-material-24/7).
-   (69) Frontier Model Forum. Publications. URL [https://www.frontiermodelforum.org/publications/](https://www.frontiermodelforum.org/publications/).
-   Ganguli et al. (2022) Deep Ganguli, Danny Hernandez, Liane Lovitt, et al. Predictability and Surprise in Large Generative Models. In _2022 ACM Conference on Fairness, Accountability, and Transparency_, FAccT ’22, page 1747–1764. ACM, June 2022. doi: 10.1145/3531146.3533229. URL [http://dx.doi.org/10.1145/3531146.3533229](http://dx.doi.org/10.1145/3531146.3533229).
-   Gardizy (2024) Anissa Gardizy. Google Cloud Narrows Gap With AWS in Revenue per Employee, 2024. URL [https://www.theinformation.com/articles/google-cloud-narrows-gap-with-aws-in-revenue-per-employee](https://www.theinformation.com/articles/google-cloud-narrows-gap-with-aws-in-revenue-per-employee).
-   Garreffa (2022) Anthony Garreffa. NVIDIA GeForce RTX 4090 sales hit 130,000 while RTX 4080 sits on shelves, November 2022. URL [https://www.tweaktown.com/news/89600/nvidia-geforce-rtx-4090-sales-hit-130-000-while-4080-sits-on-shelves/index.html](https://www.tweaktown.com/news/89600/nvidia-geforce-rtx-4090-sales-hit-130-000-while-4080-sits-on-shelves/index.html).
-   Gemini Team et al. (2024) Gemini Team, Rohan Anil, Sebastian Borgeaud, et al. Gemini: A Family of Highly Capable Multimodal Models, 2024. URL [https://arxiv.org/abs/2312.11805](https://arxiv.org/abs/2312.11805).
-   Gluck and Mazzoli (2024) Daniel Gluck and Robert Mazzoli. Datacenter Physical Access Security, 2024. URL [https://learn.microsoft.com/en-us/compliance/assurance/assurance-datacenter-physical-access-security](https://learn.microsoft.com/en-us/compliance/assurance/assurance-datacenter-physical-access-security).
-   Goldberg (1991) David Goldberg. What Every Computer Scientist Should Know About Floating-Point Arithmetic. _ACM Computing Surveys_, 23(1):5–48, 1991. URL [https://docs.oracle.com/cd/E19957-01/806-3568/ncg\_goldberg.html](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html).
-   Goldwasser et al. (1985) Shafi Goldwasser, Silvio Micali, and Charles Rackoff. The Knowledge Complexity of Interactive Proof-Systems. _Proceedings of the Seventeenth Annual ACM Symposium on Theory of Computing_, pages 291–304, 1985. doi: 10.1145/22145.22178. URL [https://dl.acm.org/doi/pdf/10.1145/22145.22178](https://dl.acm.org/doi/pdf/10.1145/22145.22178).
-   Gooding (2025) Matthew Gooding. China’s underwater data center expanded. _Data Centre Dynamics_, 2025. URL [https://www.datacenterdynamics.com/en/news/chinas-underwater-data-center-expanded/](https://www.datacenterdynamics.com/en/news/chinas-underwater-data-center-expanded/).
-   (78) Google. Bug Hunters. URL [https://bughunters.google.com/](https://bughunters.google.com/).
-   (79) Google Cloud. Confidential Space Security Overview. URL [https://cloud.google.com/docs/security/confidential-space](https://cloud.google.com/docs/security/confidential-space).
-   Gordon (2024) Cindy Gordon. Google Pauses Gemini AI Model After Latest Debacle, 2024. URL [https://www.forbes.com/sites/cindygordon/2024/02/29/google-latest-debacle-has-paused-gemini-ai-model/](https://www.forbes.com/sites/cindygordon/2024/02/29/google-latest-debacle-has-paused-gemini-ai-model/).
-   GPU Utils (2023) GPU Utils. H100 GPU Cloud Availability and Pricing, 2023. URL [https://gpus.llm-utils.org/h100-gpu-cloud-availability-and-pricing/](https://gpus.llm-utils.org/h100-gpu-cloud-availability-and-pricing/).
-   Greenblatt (2024) Ryan Greenblatt. Preventing Model Exfiltration with Upload Limits, May 2024. URL [https://redwoodresearch.substack.com/p/preventing-model-exfiltration-with](https://redwoodresearch.substack.com/p/preventing-model-exfiltration-with).
-   Harack et al. (2025) Ben Harack, Robert F. Trager, Anka Reuel, David Manheim, Miles Brundage, Onni Aarne, Aaron Scher, Yanliang Pan, Jenny Xiao, Kristy Loke, Sumaya Nur Adan, Guillem Bas, Nicholas A. Caputo, Julia C. Morse, Janvi Ahuja, Isabella Duan, Janet Egan, Ben Bucknall, Brianna Rosen, Renan Araujo, Vincent Boulanin, Ranjit Lall, Fazl Barez, Sanaa Alvira, Corin Katzke, Ahmad Atamli, and Amro Awad. Verification for International AI Governance. Technical report, Oxford Martin AI Governance Initiative, 2025. URL [https://aigi.ox.ac.uk/publications/verification-for-international-ai-governance/](https://aigi.ox.ac.uk/publications/verification-for-international-ai-governance/).
-   Hasan and Tahar (2015) Osman Hasan and Sofiène Tahar. Formal Verification Methods. In Mehdi Khosrow-Pour, editor, _Encyclopedia of Information Science and Technology, Third Edition_, pages 7162–7170. IGI Global Scientific Publishing, 2015. doi: 10.4018/978-1-4666-5888-2.ch705. URL [https://www.igi-global.com/chapter/formal-verification-methods/112414](https://www.igi-global.com/chapter/formal-verification-methods/112414).
-   Hastings and Sethumadhavan (2020) Adam Hastings and Simha Sethumadhavan. WaC: A new doctrine for hardware security. In _Proceedings of the 4th Workshop on Attacks and Solutions in Hardware Security (ASHES’20)_. Association for Computing Machinery, 2020. ISBN 978-1-4503-8090-4. doi: 10.1145/3411504.3421217. URL [https://www.cs.columbia.edu/˜hastings/doctrine.pdf](https://www.cs.columbia.edu/~hastings/doctrine.pdf).
-   He (2024) Horace He. Strangely, Matrix Multiplications on GPUs Run Faster When Given “Predictable” Data!, 2024. URL [https://www.thonking.ai/p/strangely-matrix-multiplications](https://www.thonking.ai/p/strangely-matrix-multiplications).
-   Heim (2024) Lennart Heim. A Trusted AI Compute Cluster for AI Verification and Evaluation, March 2024. URL [https://blog.heim.xyz/a-trusted-ai-compute-cluster/](https://blog.heim.xyz/a-trusted-ai-compute-cluster/).
-   Heim (2025a) Lennart Heim. The Rise of DeepSeek: What the Headlines Miss, January 2025a. URL [https://www.rand.org/pubs/commentary/2025/01/the-rise-of-deepseek-what-the-headlines-miss.html](https://www.rand.org/pubs/commentary/2025/01/the-rise-of-deepseek-what-the-headlines-miss.html).
-   Heim (2025b) Lennart Heim. Understanding the Artificial Intelligence Diffusion Framework. Technical Report PEA3776-1, RAND, January 2025b. URL [https://www.rand.org/pubs/perspectives/PEA3776-1.html](https://www.rand.org/pubs/perspectives/PEA3776-1.html).
-   Heim et al. (2024) Lennart Heim, Tim Fist, Janet Egan, Sihao Huang, Stephen Zekany, Robert Trager, Michael A. Osborne, and Noa Zilberman. Governing Through the Cloud: The Intermediary Role of Compute Providers in AI Regulation. Technical report, Oxford Martin School, University of Oxford, March 2024. URL [https://www.oxfordmartin.ox.ac.uk/publications/governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation/](https://www.oxfordmartin.ox.ac.uk/publications/governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation/).
-   Hendrycks et al. (2025) Dan Hendrycks, Eric Schmidt, and Alexandr Wang. Superintelligence Strategy: Expert Version, 2025. URL [https://arxiv.org/abs/2503.05628](https://arxiv.org/abs/2503.05628). Revision date: 2025-04-14.
-   Henshall (2023) Will Henshall. The 3 Most Important AI Policy Milestones of 2023, 2023. URL [https://time.com/6513046/ai-policy-developments-2023/](https://time.com/6513046/ai-policy-developments-2023/).
-   Henshall (2024) Will Henshall. The Billion-Dollar Price Tag of Building AI, 2024. URL [https://time.com/6984292/cost-artificial-intelligence-compute-epoch-report/](https://time.com/6984292/cost-artificial-intelligence-compute-epoch-report/).
-   Hildenbrand (2018) Jerry Hildenbrand. Bootloaders: More Than You Ever Wanted to Know, 2018. URL [https://www.androidcentral.com/bootloaders-all-you-ever-wanted-know](https://www.androidcentral.com/bootloaders-all-you-ever-wanted-know).
-   Hinton et al. (2025) Geoffrey Hinton, Yoshua Bengio, Demis Hassabis, et al. Statement on AI Risk, 2025. URL [https://www.safe.ai/statement-on-ai-risk](https://www.safe.ai/statement-on-ai-risk).
-   Ho et al. (2024) Anson Ho, Tamay Besiroglu, Ege Erdil, David Owen, Robi Rahman, Zifan Carl Guo, David Atkinson, Neil Thompson, and Jaime Sevilla. Algorithmic progress in language models, 2024. URL [https://arxiv.org/abs/2403.05812](https://arxiv.org/abs/2403.05812).
-   Hobbhahn (2024) Marius Hobbhahn. The Evals Gap, 2024. URL [https://www.apolloresearch.ai/blog/evalsgap](https://www.apolloresearch.ai/blog/evalsgap).
-   Hoffmann et al. (2022) Jordan Hoffmann, Sebastian Borgeaud, Arthur Mensch, et al. Training Compute-Optimal Large Language Models, 2022. URL [https://arxiv.org/abs/2203.15556](https://arxiv.org/abs/2203.15556).
-   (99) Hugging Face. The Deep Q-Learning Algorithm. URL [https://huggingface.co/learn/deep-rl-course/unit3/deep-q-algorithm](https://huggingface.co/learn/deep-rl-course/unit3/deep-q-algorithm). Hugging Face Deep Reinforcement Learning Course.
-   (100) Intel Corporation. Intel® Bug Bounty Program Terms. URL [https://www.intel.com/content/www/us/en/security-center/bug-bounty-program.html](https://www.intel.com/content/www/us/en/security-center/bug-bounty-program.html).
-   Int (2019) _Arria 10 SoC Boot User Guide, Section 1.2.2: First Stage: Boot ROM_. Intel Corporation, 2019. URL [https://www.intel.com/content/www/us/en/docs/programmable/683735/current/first-stage-boot-rom.html](https://www.intel.com/content/www/us/en/docs/programmable/683735/current/first-stage-boot-rom.html).
-   Intel Corporation (2025) Intel Corporation. 2024 Intel® Product Security Report. Technical Report ID 846149, Intel Corporation, 2025. URL [https://www.intel.com/content/www/us/en/content-details/846149/2024-intel-product-security-report.html](https://www.intel.com/content/www/us/en/content-details/846149/2024-intel-product-security-report.html).
-   Internal Revenue Service (2025) Internal Revenue Service. Whistleblower Office, 2025. URL [https://www.irs.gov/compliance/whistleblower-office](https://www.irs.gov/compliance/whistleblower-office).
-   International Atomic Energy Agency (1998) International Atomic Energy Agency. The Evolution of IAEA Safeguards. Technical report, International Atomic Energy Agency, 1998. URL [https://www-pub.iaea.org/MTCD/publications/PDF/NVS2\_web.pdf](https://www-pub.iaea.org/MTCD/publications/PDF/NVS2_web.pdf).
-   International Atomic Energy Agency (2014) International Atomic Energy Agency. Safeguards Implementation Practices Guide on Facilitating IAEA Verification Activities, 2014. URL [https://www-pub.iaea.org/MTCD/Publications/PDF/SVS-30\_web.pdf](https://www-pub.iaea.org/MTCD/Publications/PDF/SVS-30_web.pdf).
-   (106) Intigriti. AMD Product Security Bug Bounty Program. URL [https://app.intigriti.com/programs/amd/amd/detail](https://app.intigriti.com/programs/amd/amd/detail).
-   Jackson et al. (2022) Krystal Jackson, Karson Elmgren, Jacob Feldgoise, and Andrew Critch. Compute Accounting Principles Can Help Reduce AI Risks. Technical report, Center for Security and Emerging Technology, 2022. URL [https://cset.georgetown.edu/article/compute-accounting-principles-can-help-reduce-ai-risks/](https://cset.georgetown.edu/article/compute-accounting-principles-can-help-reduce-ai-risks/).
-   Jacob et al. (2017) Benoit Jacob, Skirmantas Kligys, Bo Chen, Menglong Zhu, Matthew Tang, Andrew Howard, Hartwig Adam, and Dmitry Kalenichenko. Quantization and Training of Neural Networks for Efficient Integer-Arithmetic-Only Inference, 2017. URL [https://arxiv.org/abs/1712.05877](https://arxiv.org/abs/1712.05877).
-   Jain et al. (2021) Ayush Jain, Ziqi Zhou, and Ujjwal Guin. Survey of Recent Developments for Hardware Trojan Detection. In _2021 IEEE International Symposium on Circuits and Systems (ISCAS)_, pages 1–5, 2021. doi: 10.1109/ISCAS51556.2021.9401143. URL [https://www.semanticscholar.org/paper/Survey-of-Recent-Developments-for-Hardware-Trojan-Jain-Zhou/45d190fc5ab153d9beca3b392cdd141fbc66fcf2](https://www.semanticscholar.org/paper/Survey-of-Recent-Developments-for-Hardware-Trojan-Jain-Zhou/45d190fc5ab153d9beca3b392cdd141fbc66fcf2).
-   Jia et al. (2021) Hengrui Jia, Mohammad Yaghini, Christopher A. Choquette-Choo, Natalie Dullerud, Anvith Thudi, Varun Chandrasekaran, and Nicolas Papernot. Proof-of-Learning: Definitions and Practice, 2021. URL [https://arxiv.org/abs/2103.05633](https://arxiv.org/abs/2103.05633).
-   Jirků (2022) Michal Jirků. Understanding the Nintendo Switch Secure Boot Vulnerabilities, 2022. URL [https://wejn.org/2022/05/understanding-the-nintendo-switch-boot-vulnerabilities/](https://wejn.org/2022/05/understanding-the-nintendo-switch-boot-vulnerabilities/).
-   Jouppi et al. (2017) Norman P. Jouppi, Cliff Young, Nishant Patil, et al. In-Datacenter Performance Analysis of a Tensor Processing Unit, 2017. URL [https://arxiv.org/abs/1704.04760](https://arxiv.org/abs/1704.04760).
-   Kahn (2024) Jeremy Kahn. Exclusive: OpenAI promised 20% of its computing power to combat the most dangerous kind of AI—but never delivered, sources say. _Fortune_, May 2024. URL [https://fortune.com/2024/05/21/openai-superalignment-20-compute-commitment-never-fulfilled-sutskever-leike-altman-brockman-murati/](https://fortune.com/2024/05/21/openai-superalignment-20-compute-commitment-never-fulfilled-sutskever-leike-altman-brockman-murati/).
-   Kaplan et al. (2020) Jared Kaplan, Sam McCandlish, Tom Henighan, Tom B. Brown, Benjamin Chess, Rewon Child, Scott Gray, Alec Radford, Jeffrey Wu, and Dario Amodei. Scaling Laws for Neural Language Models, 2020. URL [https://arxiv.org/abs/2001.08361](https://arxiv.org/abs/2001.08361).
-   Kern and Greenstreet (1999) Christoph Kern and Mark R. Greenstreet. Formal verification in hardware design: a survey. 4(2), 1999. ISSN 1084-4309. doi: 10.1145/307988.307989. URL [https://doi.org/10.1145/307988.307989](https://doi.org/10.1145/307988.307989).
-   Khan et al. (2021) Saif Khan, Dahlia Peterson, and Alexander Mann. The Semiconductor Supply Chain: Assessing National Competitiveness. Technical report, Center for Security and Emerging Technology, 2021. URL [https://cset.georgetown.edu/publication/the-semiconductor-supply-chain/](https://cset.georgetown.edu/publication/the-semiconductor-supply-chain/).
-   Kirk (2019) Jeremy Kirk. Apple iOS Has Permanent Bootrom Vulnerability, 2019. URL [https://www.bankinfosecurity.com/apples-ios-has-permanent-bootrom-vulnerability-a-13159](https://www.bankinfosecurity.com/apples-ios-has-permanent-bootrom-vulnerability-a-13159).
-   Klotz (2022) Aaron Klotz. Nvidia Driver Unlocks Performance Boosting GPU System Processor, 2022. URL [https://www.tomshardware.com/news/nvidia-gpu-system-processor-introduction](https://www.tomshardware.com/news/nvidia-gpu-system-processor-introduction).
-   Kocher et al. (2018) Paul Kocher, Daniel Genkin, Daniel Gruss, Werner Haas, Mike Hamburg, Moritz Lipp, Stefan Mangard, Thomas Prescher, Michael Schwarz, and Yuval Yarom. Spectre Attacks: Exploiting Speculative Execution, 2018. URL [https://arxiv.org/abs/1801.01203](https://arxiv.org/abs/1801.01203).
-   Krass (1985) Allan S. Krass. _Verification: How Much Is Enough?_ Stockholm International Peace Research Institute, 1985. URL [https://www.sipri.org/sites/default/files/files/books/SIPRI85Krass/SIPRI85Krass.pdf](https://www.sipri.org/sites/default/files/files/books/SIPRI85Krass/SIPRI85Krass.pdf).
-   Kulp et al. (2024) Gabriel Kulp, Daniel Gonzales, Everett Smith, Lennart Heim, Prateek Puri, Michael J. D. Vermeer, and Zev Winkelman. Hardware-Enabled Governance Mechanisms. Working paper, RAND, January 2024. URL [https://www.rand.org/pubs/working\_papers/WRA3056-1.html](https://www.rand.org/pubs/working_papers/WRA3056-1.html).
-   (122) KVM. Kernel Virtual Machine (KVM). URL [https://linux-kvm.org/page/Main\_Page](https://linux-kvm.org/page/Main_Page).
-   Kwa et al. (2025) Thomas Kwa, Ben West, Joel Becker, Amy Deng, Katharyn Garcia, Max Hasin, Sami Jawhar, Megan Kinniment, Nate Rush, Sydney Von Arx, Ryan Bloom, Thomas Broadley, Haoxing Du, Brian Goodrich, Nikola Jurkovic, Luke Harold Miles, Seraphina Nix, Tao Lin, Neev Parikh, David Rein, Lucas Jun Koba Sato, Hjalmar Wijk, Daniel M. Ziegler, Elizabeth Barnes, and Lawrence Chan. Measuring AI Ability to Complete Long Tasks, 2025. URL [https://arxiv.org/abs/2503.14499](https://arxiv.org/abs/2503.14499).
-   Larabel (2020) Michael Larabel. The Linux Kernel Enters 2020 At 27.8 Million Lines In Git But With Less Developers For 2019, January 2020. URL [https://www.phoronix.com/news/Linux-Git-Stats-EOY2019](https://www.phoronix.com/news/Linux-Git-Stats-EOY2019).
-   Larabel (2022) Michael Larabel. AMD, Google, Microsoft & NVIDIA Announce “Caliptra” Open-Source Root of Trust, October 2022. URL [https://www.phoronix.com/review/caliptra](https://www.phoronix.com/review/caliptra).
-   (126) LF Projects. The seL4 Microkernel. URL [https://sel4.systems/](https://sel4.systems/).
-   Lin et al. (2025) Shaowei Lin, Evan Miyazono, and Daniel Windham. A Toolchain for AI-Assisted Code Specification, Synthesis and Verification. Technical report, Atlas Computing, 2025. URL [https://atlascomputing.org/ai-assisted-fv-toolchain.pdf](https://atlascomputing.org/ai-assisted-fv-toolchain.pdf). White paper.
-   Lipp et al. (2018) Moritz Lipp, Michael Schwarz, Daniel Gruss, Thomas Prescher, Werner Haas, Stefan Mangard, Paul Kocher, Daniel Genkin, Yuval Yarom, and Mike Hamburg. Meltdown, 2018. URL [https://arxiv.org/abs/1801.01207](https://arxiv.org/abs/1801.01207).
-   Llama Team (2024) Llama Team. The Llama 3 Herd of Models, 2024. URL [https://ai.meta.com/research/publications/the-llama-3-herd-of-models/](https://ai.meta.com/research/publications/the-llama-3-herd-of-models/).
-   Longview Philanthropy (2025) Longview Philanthropy. Request for Proposals on Hardware-Enabled Mechanisms (HEMs). Request for Proposals, 2025. URL [https://www.longview.org/request-for-proposals-on-hardware-enabled-mechanisms-hems-for-ai-verification/](https://www.longview.org/request-for-proposals-on-hardware-enabled-mechanisms-hems-for-ai-verification/).
-   Lumenci Team (2022) Lumenci Team. Device Delayering for Reverse Engineering of Semiconductor Chips, 2022. URL [https://lumenci.com/blogs/semiconductor/](https://lumenci.com/blogs/semiconductor/).
-   Maslej et al. (2023) Nestor Maslej, Loredana Fattorini, Erik Brynjolfsson, John Etchemendy, Katrina Ligett, Terah Lyons, James Manyika, Helen Ngo, Juan Carlos Niebles, Vanessa Parli, Yoav Shoham, Russell Wald, Jack Clark, and Raymond Perrault. Artificial Intelligence Index Report 2023, 2023. URL [https://aiindex.stanford.edu/ai-index-report-2023/](https://aiindex.stanford.edu/ai-index-report-2023/).
-   Matyunin et al. (2019) Nikolay Matyunin, Yujue Wang, Tolga Arul, Kristian Kullmann, Jakub Szefer, and Stefan Katzenbeisser. MagneticSpy: Exploiting Magnetometer in Mobile Devices for Website and Application Fingerprinting, 2019. URL [https://arxiv.org/abs/1906.11117](https://arxiv.org/abs/1906.11117).
-   Micron Technology (2018) Micron Technology. Metamorphosis of an Industry, Part 2, 2018. URL [https://www.micron.com/about/blog/company/insights/metamorphosis-of-an-industry-part-2](https://www.micron.com/about/blog/company/insights/metamorphosis-of-an-industry-part-2).
-   (135) Microsoft. Microsoft Bug Bounty Program. URL [https://www.microsoft.com/en-us/msrc/bounty](https://www.microsoft.com/en-us/msrc/bounty).
-   Microsoft (2021) Microsoft. Disabling Secure Boot, December 2021. URL [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot).
-   (137) MITRE Corporation. Hide Artifacts: Hidden File System. URL [https://attack.mitre.org/techniques/T1564/005/](https://attack.mitre.org/techniques/T1564/005/).
-   Moghimi et al. (2020) Daniel Moghimi, Berk Sunar, Thomas Eisenbarth, and Nadia Heninger. TPM-Fail: TPM meets Timing and Lattice Attacks. In _29th USENIX Security Symposium_, August 2020. ISBN 978-1-939133-17-5. URL [https://www.usenix.org/system/files/sec20-moghimi-tpm.pdf](https://www.usenix.org/system/files/sec20-moghimi-tpm.pdf).
-   Nagarajan et al. (2019) Prabhat Nagarajan, Garrett Warnell, and Peter Stone. Deterministic Implementations for Reproducibility in Deep Reinforcement Learning, 2019. URL [https://arxiv.org/abs/1809.05676](https://arxiv.org/abs/1809.05676).
-   Narayanan et al. (2021) Deepak Narayanan, Mohammad Shoeybi, Jared Casper, Patrick LeGresley, Mostofa Patwary, Vijay Anand Korthikanti, Dmitri Vainbrand, Prethvi Kashinkunti, Julie Bernauer, Bryan Catanzaro, Amar Phanishayee, and Matei Zaharia. Efficient Large-Scale Language Model Training on GPU Clusters Using Megatron-LM, 2021. URL [https://arxiv.org/abs/2104.04473](https://arxiv.org/abs/2104.04473).
-   (141) National Institute of Standards and Technology. Key revocation. URL [https://csrc.nist.gov/glossary/term/key\_revocation](https://csrc.nist.gov/glossary/term/key_revocation).
-   (142) National Whistleblower Center. Whistleblower Laws Around the World. URL [https://www.whistleblowers.org/whistleblower-laws-around-the-world/](https://www.whistleblowers.org/whistleblower-laws-around-the-world/).
-   Nevo et al. (2024) Sella Nevo, Dan Lahav, Ajay Karpur, Yogev Bar-On, Henry Alexander Bradley, and Jeff Alstott. Securing AI Model Weights. Research report, RAND, May 2024. URL [https://www.rand.org/pubs/research\_reports/RRA2849-1.html](https://www.rand.org/pubs/research_reports/RRA2849-1.html).
-   Ngo et al. (2025) Richard Ngo, Lawrence Chan, and Sören Mindermann. The Alignment Problem from a Deep Learning Perspective, 2025. URL [https://arxiv.org/abs/2209.00626](https://arxiv.org/abs/2209.00626).
-   (145) Nitrokey. NetHSM – The Trustworthy, Open Hardware Security Module That Just Works. URL [https://www.nitrokey.com/products/nethsm](https://www.nitrokey.com/products/nethsm). Funded by the European Union under the “Gründung innovativ” program of the Investitionsbank of Brandenburg.
-   Nuclear Threat Initiative (2016) Nuclear Threat Initiative. Treaty on Conventional Armed Forces in Europe (CFE), 2016. URL [https://www.nti.org/education-center/treaties-and-regimes/treaty-conventional-armed-forces-europe-cfe/](https://www.nti.org/education-center/treaties-and-regimes/treaty-conventional-armed-forces-europe-cfe/).
-   Nuclear Threat Initiative (2024) Nuclear Threat Initiative. Biological Weapons Convention (BWC), 2024. URL [https://www.nti.org/education-center/treaties-and-regimes/convention-prohibition-development-production-and-stockpiling-bacteriological-biological-and-toxin-weapons-btwc/](https://www.nti.org/education-center/treaties-and-regimes/convention-prohibition-development-production-and-stockpiling-bacteriological-biological-and-toxin-weapons-btwc/).
-   NuFlare Technology, Inc. (2025) NuFlare Technology, Inc. EB Mask Writer, 2025. URL [https://www.nuflare.co.jp/english/products/beam/](https://www.nuflare.co.jp/english/products/beam/). Copyright © 2002–2025 NuFlare Technology Inc. All Rights Reserved.
-   NVIDIA (a) NVIDIA. Boot ROM, a. URL [https://developer.nvidia.com/docs/drive/drive-os/archives/6.0.4/linux/sdk/common/topics/bootloader\_setup/BootROM4.html](https://developer.nvidia.com/docs/drive/drive-os/archives/6.0.4/linux/sdk/common/topics/bootloader_setup/BootROM4.html).
-   NVIDIA (b) NVIDIA. NVIDIA H100 Tensor Core GPU, b. URL [https://resources.nvidia.com/en-us-tensor-core/nvidia-tensor-core-gpu-datasheet](https://resources.nvidia.com/en-us-tensor-core/nvidia-tensor-core-gpu-datasheet).
-   (151) NVIDIA. Report Security Vulnerability. URL [https://www.nvidia.com/en-us/security/report-vulnerability/?srsltid=AfmBOopsjRQ3E2fP-Z2-CGtEgC7XfjGCWWbicY\_1RYxpRhAqCu5cLiU5](https://www.nvidia.com/en-us/security/report-vulnerability/?srsltid=AfmBOopsjRQ3E2fP-Z2-CGtEgC7XfjGCWWbicY_1RYxpRhAqCu5cLiU5).
-   NVIDIA (2023a) NVIDIA. NVIDIA Ada GPU Architecture. Whitepaper, NVIDIA Corporation, 2023a. URL [https://images.nvidia.com/aem-dam/Solutions/geforce/ada/nvidia-ada-gpu-architecture.pdf](https://images.nvidia.com/aem-dam/Solutions/geforce/ada/nvidia-ada-gpu-architecture.pdf).
-   NVIDIA (2023b) NVIDIA. Confidential Compute on NVIDIA Hopper H100. Whitepaper, NVIDIA Corporation, 2023b. URL [https://images.nvidia.com/aem-dam/en-zz/Solutions/data-center/HCC-Whitepaper-v1.0.pdf](https://images.nvidia.com/aem-dam/en-zz/Solutions/data-center/HCC-Whitepaper-v1.0.pdf).
-   NVIDIA (2023c) NVIDIA. Appendix - Secure Boot Activation and Deactivation, 2023c. URL [https://docs.nvidia.com/networking/display/ufmenterpriseapplianceswv160/appendix+-+secure+boot+activation+and+deactivation](https://docs.nvidia.com/networking/display/ufmenterpriseapplianceswv160/appendix+-+secure+boot+activation+and+deactivation).
-   NVIDIA (2024) NVIDIA. NVIDIA Quarterly Revenue Trend: Revenue by Markets, 2024. URL [https://s201.q4cdn.com/141608511/files/doc\_financials/2025/Q325/Rev\_by\_Mkt\_Qtrly\_Trend\_Q325.pdf](https://s201.q4cdn.com/141608511/files/doc_financials/2025/Q325/Rev_by_Mkt_Qtrly_Trend_Q325.pdf).
-   Office of Technology Assessment (1990) Office of Technology Assessment. Verification Technologies: Measures for Monitoring Compliance With the START Treaty, December 1990. URL [https://govinfo.library.unt.edu/ota/Ota\_2/DATA/1990/9029.PDF](https://govinfo.library.unt.edu/ota/Ota_2/DATA/1990/9029.PDF).
-   (157) OpenAI. Data Controls in the OpenAI Platform. URL [https://platform.openai.com/docs/guides/your-data](https://platform.openai.com/docs/guides/your-data).
-   OpenAI (2024) OpenAI. Learning to Reason with LLMs, 2024. URL [https://openai.com/index/learning-to-reason-with-llms/](https://openai.com/index/learning-to-reason-with-llms/).
-   OpenAI et al. (2024) OpenAI, Josh Achiam, Steven Adler, et al. GPT-4 Technical Report, 2024. URL [https://arxiv.org/abs/2303.08774](https://arxiv.org/abs/2303.08774).
-   Owen (2024) David Owen. How predictable is language model benchmark performance?, 2024. URL [https://epochai.org/blog/how-predictable-is-language-model-benchmark-performance](https://epochai.org/blog/how-predictable-is-language-model-benchmark-performance).
-   Patel et al. (2023) Dylan Patel, Myron Xie, Daniel Nishball, and Wega Chu. Wafer Wars: Deciphering Latest Restrictions on AI and Semiconductor Manufacturing, 2023. URL [https://semianalysis.com/2023/10/24/wafer-wars-deciphering-latest-restrictions/](https://semianalysis.com/2023/10/24/wafer-wars-deciphering-latest-restrictions/).
-   Pelosi (2024) Nancy Pelosi. Pelosi Statement in Opposition to California Senate Bill 1047, 2024. URL [https://pelosi.house.gov/news/press-releases/pelosi-statement-opposition-california-senate-bill-1047](https://pelosi.house.gov/news/press-releases/pelosi-statement-opposition-california-senate-bill-1047).
-   Petrie and Aarne (2025) James Petrie and Onni Aarne. Technical options for flexible hardware-enabled guarantees, 2025. URL [https://arxiv.org/abs/2506.03409](https://arxiv.org/abs/2506.03409).
-   Petrie et al. (2024) James Petrie, Onni Aarne, Nora Ammann, and David Dalrymple. Interim Report: Mechanisms for Flexible Hardware-Enabled Guarantees. Technical report, Yoshua Bengio, 2024. URL [https://yoshuabengio.org/wp-content/uploads/2024/09/FlexHEG-Interim-Report\_2024.pdf](https://yoshuabengio.org/wp-content/uploads/2024/09/FlexHEG-Interim-Report_2024.pdf).
-   Pilz and Heim (2023) Konstantin Pilz and Lennart Heim. Compute at Scale: A Broad Investigation into the Data Center Industry, 2023. URL [https://arxiv.org/abs/2311.02651](https://arxiv.org/abs/2311.02651).
-   Pilz et al. (2024) Konstantin Pilz, Lennart Heim, and Nicholas Brown. Increased Compute Efficiency and the Diffusion of AI Capabilities, 2024. URL [https://arxiv.org/abs/2311.15377](https://arxiv.org/abs/2311.15377).
-   Pilz et al. (2025a) Konstantin F. Pilz, Yusuf Mahmood, and Lennart Heim. AI’s Power Requirements Under Exponential Growth. Technical report, RAND, 2025a. URL [https://www.rand.org/pubs/research\_reports/RRA3572-1.html](https://www.rand.org/pubs/research_reports/RRA3572-1.html).
-   Pilz et al. (2025b) Konstantin F. Pilz, James Sanders, Robi Rahman, and Lennart Heim. Trends in AI Supercomputers, 2025b. URL [https://arxiv.org/abs/2504.16026](https://arxiv.org/abs/2504.16026).
-   Pope et al. (2022) Reiner Pope, Sholto Douglas, Aakanksha Chowdhery, Jacob Devlin, James Bradbury, Anselm Levskaya, Jonathan Heek, Kefan Xiao, Shivani Agrawal, and Jeff Dean. Efficiently Scaling Transformer Inference, 2022. URL [https://arxiv.org/abs/2211.05102](https://arxiv.org/abs/2211.05102).
-   Prime Minister’s Office, 10 Downing Street et al. (2023) Prime Minister’s Office, 10 Downing Street, Foreign, Commonwealth & Development Office, and Department for Science, Innovation & Technology. The Bletchley Declaration by Countries Attending the AI Safety Summit, 1–2 November 2023, 2023. URL [https://www.gov.uk/government/publications/ai-safety-summit-2023-the-bletchley-declaration/the-bletchley-declaration-by-countries-attending-the-ai-safety-summit-1-2-november-2023](https://www.gov.uk/government/publications/ai-safety-summit-2023-the-bletchley-declaration/the-bletchley-declaration-by-countries-attending-the-ai-safety-summit-1-2-november-2023).
-   Puigcerver et al. (2024) Joan Puigcerver, Carlos Riquelme, Basil Mustafa, and Neil Houlsby. From Sparse to Soft Mixtures of Experts, 2024. URL [https://arxiv.org/abs/2308.00951](https://arxiv.org/abs/2308.00951).
-   Redox Developers (2015) Redox Developers. Redox — Your Next(Gen) OS, 2015. URL [https://www.redox-os.org/](https://www.redox-os.org/).
-   Reuel et al. (2025) Anka Reuel, Ben Bucknall, et al. Open Problems in Technical AI Governance, 2025. URL [https://arxiv.org/abs/2407.14981](https://arxiv.org/abs/2407.14981).
-   Ridley (2021) Jacob Ridley. Nvidia says its cryptocurrency mining limiter ’cannot be hacked’, February 2021. URL [https://www.pcgamer.com/nvidia-ethereum-mining-limiter-cannot-be-hacked/](https://www.pcgamer.com/nvidia-ethereum-mining-limiter-cannot-be-hacked/).
-   Robison (2024) Kylie Robison. OpenAI researcher resigns, claiming safety has taken ‘a backseat to shiny products’, 2024. URL [https://www.theverge.com/2024/5/17/24159095/openai-jan-leike-superalignment-sam-altman-ai-safety](https://www.theverge.com/2024/5/17/24159095/openai-jan-leike-superalignment-sam-altman-ai-safety).
-   Roose (2024) Kevin Roose. OpenAI Insiders Warn of a ‘Reckless’ Race for Dominance. _The New York Times_, 2024. URL [https://www.nytimes.com/2024/06/04/technology/openai-culture-whistleblowers.html](https://www.nytimes.com/2024/06/04/technology/openai-culture-whistleblowers.html).
-   Rosenthal et al. (2019) Michael D. Rosenthal, Leslie G. Fishbone, Linda Gallini, Allan Krass, Myron Kratzer, Jonathan Sanborn, Warren Stern, Barclay Ward, and Norman A. Wulf. _Deterring Nuclear Proliferation: The Importance of IAEA Safeguards_. 2019\. URL [https://www.bnl.gov/nns/iaea-textbook/](https://www.bnl.gov/nns/iaea-textbook/).
-   Sastry et al. (2024) Girish Sastry, Lennart Heim, Haydn Belfield, Markus Anderljung, Miles Brundage, Julian Hazell, Cullen O’Keefe, Gillian K. Hadfield, Richard Ngo, Konstantin Pilz, George Gor, Emma Bluemke, Sarah Shoker, Janet Egan, Robert F. Trager, Shahar Avin, Adrian Weller, Yoshua Bengio, and Diane Coyle. Computing Power and the Governance of Artificial Intelligence, 2024. URL [https://arxiv.org/abs/2402.08797](https://arxiv.org/abs/2402.08797).
-   Scher and Thiergart (2024) Aaron Scher and Lisa Thiergart. Mechanisms to Verify International Agreements About AI Development. Technical report, Machine Intelligence Research Institute, November 2024. URL [https://techgov.intelligence.org/research/mechanisms-to-verify-international-agreements-about-ai-development](https://techgov.intelligence.org/research/mechanisms-to-verify-international-agreements-about-ai-development).
-   Schmid (2023) Philipp Schmid. Llama 2 on Amazon SageMaker a Benchmark, September 2023. URL [https://huggingface.co/blog/llama-sagemaker-benchmark](https://huggingface.co/blog/llama-sagemaker-benchmark).
-   Schulman et al. (2017) John Schulman, Filip Wolski, Prafulla Dhariwal, Alec Radford, and Oleg Klimov. Proximal Policy Optimization Algorithms, 2017. URL [https://arxiv.org/abs/1707.06347](https://arxiv.org/abs/1707.06347).
-   Schwarz and Gruss (2020) Michael Schwarz and Daniel Gruss. How Trusted Execution Environments Fuel Research on Microarchitectural Attacks. _IEEE Security & Privacy_, 18(5):18–27, 2020. doi: 10.1109/MSEC.2020.2993896. URL [http://www.misc0110.net/files/tee\_uarch.pdf](http://www.misc0110.net/files/tee_uarch.pdf).
-   Security (2023) Mithril Security. AICert: Open-source Tool for AI Model Provenance Using Secure Hardware. Website, 2023. URL [https://www.mithrilsecurity.io/aicert](https://www.mithrilsecurity.io/aicert). Supported by Future of Life Institute.
-   Sevilla and Roldán (2024) Jaime Sevilla and Edu Roldán. Training Compute of Frontier AI Models Grows by 4-5x per Year, 2024. URL [https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year](https://epoch.ai/blog/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year).
-   Sevilla et al. (2022) Jaime Sevilla, Lennart Heim, Marius Hobbhahn, Tamay Besiroglu, Anson Ho, and Pablo Villalobos. Estimating Training Compute of Deep Learning Models, 2022. URL [https://epoch.ai/blog/estimating-training-compute](https://epoch.ai/blog/estimating-training-compute).
-   Shah (2024) Agam Shah. NVIDIA Shipped 3.76 Million Data-center GPUs in 2023, According to Study. _HPCwire_, 2024. URL [https://www.hpcwire.com/2024/06/10/nvidia-shipped-3-76-million-data-center-gpus-in-2023-according-to-study/](https://www.hpcwire.com/2024/06/10/nvidia-shipped-3-76-million-data-center-gpus-in-2023-according-to-study/).
-   Shavit (2023) Yonadav Shavit. What does it take to catch a Chinchilla? Verifying Rules on Large-Scale Neural Network Training via Compute Monitoring, 2023. URL [https://arxiv.org/abs/2303.11341](https://arxiv.org/abs/2303.11341).
-   Sheehan (2023) Matt Sheehan. Untitled Thread on X, July 2023. URL [https://threadreaderapp.com/thread/1679419324925349889](https://threadreaderapp.com/thread/1679419324925349889).
-   Sheehan (2024) Matt Sheehan. China’s Views on AI Safety Are Changing—Quickly, August 2024. URL [https://carnegieendowment.org/research/2024/08/china-artificial-intelligence-ai-safety-regulation?lang=en](https://carnegieendowment.org/research/2024/08/china-artificial-intelligence-ai-safety-regulation?lang=en). Online article.
-   Shenk (2024) Anton Shenk. Evaluating Artificial Intelligence for National Security and Public Safety, September 2024. URL [https://www.rand.org/content/dam/rand/pubs/conf\_proceedings/CFA3400/CFA3429-1/RAND\_CFA3429-1.pdf](https://www.rand.org/content/dam/rand/pubs/conf_proceedings/CFA3400/CFA3429-1/RAND_CFA3429-1.pdf).
-   Shilov (2023) Anton Shilov. Nvidia to Reportedly Triple Output of Compute GPUs in 2024: Up to 2 Million H100s, 2023. URL [https://www.tomshardware.com/news/nvidia-to-reportedly-triple-output-of-compute-gpus-in-2024-up-to-2-million-h100s](https://www.tomshardware.com/news/nvidia-to-reportedly-triple-output-of-compute-gpus-in-2024-up-to-2-million-h100s).
-   Slayman (2011) Charles Slayman. Soft Error Trends and Mitigation Techniques in Memory Devices. Technical report, Ops A La Carte LLC, 2011. URL [https://pdfs.semanticscholar.org/b582/da6429e629e706c44717171179173bdd3150.pdf](https://pdfs.semanticscholar.org/b582/da6429e629e706c44717171179173bdd3150.pdf).
-   Souyris et al. (2009) Jean Souyris, Virginie Wiels, David Delmas, and Hervé Delseny. Formal Verification of Avionics Software Products. In Ana Cavalcanti and Dennis Dams, editors, _Formal Methods – FM 2009_, volume 5850 of _Lecture Notes in Computer Science_, pages 532–546, Berlin Heidelberg, 2009. Springer-Verlag. URL [https://www.cs.unc.edu/˜anderson/teach/comp790/papers/Souyris.pdf](https://www.cs.unc.edu/~anderson/teach/comp790/papers/Souyris.pdf).
-   Sridharan et al. (2015) Vilas Sridharan, Nathan DeBardeleben, John Shalf, Sean Blanchard, Kurt B. Ferreira, Jon Stearley, and Sudhanva Gurumurthi. Memory Errors in Modern Systems: The Good, the Bad, and the Ugly. Technical report, U.S. Department of Energy, Office of Science, 2015. URL [https://science.osti.gov/-/media/ascr/ascac/pdf/meetings/201512/ResilienceASCAC2015.pdf](https://science.osti.gov/-/media/ascr/ascac/pdf/meetings/201512/ResilienceASCAC2015.pdf).
-   (195) StockAnalysis. Taiwan Semiconductor Manufacturing Company Limited (TSM). URL [https://stockanalysis.com/stocks/tsm/employees/](https://stockanalysis.com/stocks/tsm/employees/).
-   Sun et al. (2024a) Haochen Sun, Jason Li, and Hongyang Zhang. zkLLM: Zero Knowledge Proofs for Large Language Models, 2024a. URL [https://arxiv.org/abs/2404.16109](https://arxiv.org/abs/2404.16109).
-   Sun et al. (2024b) Yifan Sun, Yuhang Li, Yue Zhang, Yuchen Jin, and Huan Zhang. SVIP: Towards verifiable inference of open-source large language models, 2024b. URL [https://arxiv.org/abs/2410.22307](https://arxiv.org/abs/2410.22307).
-   Survival & Flourishing Fund (2024) Survival & Flourishing Fund. SFF-2024 Mechanisms for Flexible Hardware-Enabled Guarantees (flexHEGs), 2024. URL [https://survivalandflourishing.fund/sff-2024-flexhegs-recommendations](https://survivalandflourishing.fund/sff-2024-flexhegs-recommendations).
-   (199) The Apple Wiki. Pwnage. URL [https://theapplewiki.com/wiki/Pwnage](https://theapplewiki.com/wiki/Pwnage).
-   The Hill & Valley Forum (2024) The Hill & Valley Forum. Speaker of the House Mike Johnson | Hill & Valley Forum 2024. YouTube video, 2024. URL [https://www.youtube.com/watch?v=XE-WXe6N-7I](https://www.youtube.com/watch?v=XE-WXe6N-7I).
-   Thermo Fisher Scientific (2025) Thermo Fisher Scientific. Semiconductor Delayering | Semiconductor Deprocessing, 2025. URL [https://www.thermofisher.com/us/en/home/semiconductors/device-delayering.html](https://www.thermofisher.com/us/en/home/semiconductors/device-delayering.html).
-   Thomas and Francillon (2018) Sam L. Thomas and Aurélien Francillon. Backdoors: Definition, Deniability and Detection. In Michael Bailey, Thorsten Holz, Manolis Stamatogiannakis, and Sotiris Ioannidis, editors, _Proceedings of the 21st International Symposium on Research in Attacks, Intrusions, and Defenses (RAID 2018)_, pages 92–113, Cham, 2018. Springer. ISBN 978-3-030-00469-9. doi: 10.1007/978-3-030-00470-5\_5. URL [https://doi.org/10.1007/978-3-030-00470-5\_5](https://doi.org/10.1007/978-3-030-00470-5_5).
-   Thompson (1984) Ken Thompson. Reflections on Trusting Trust. _Communications of the ACM_, 27(8), August 1984. URL [https://www.cs.cmu.edu/˜rdriley/487/papers/Thompson\_1984\_ReflectionsonTrustingTrust.pdf](https://www.cs.cmu.edu/~rdriley/487/papers/Thompson_1984_ReflectionsonTrustingTrust.pdf). Turing Award Lecture.
-   Timerbaev (2017) Roland Timerbaev. The Nuclear Nonproliferation Treaty Has Largely Achieved Its Goals, 2017. URL [https://www.armscontrol.org/act/2017-09/interviews/roland-timerbaev-nuclear-nonproliferation-treaty-has-largely-achieved-its](https://www.armscontrol.org/act/2017-09/interviews/roland-timerbaev-nuclear-nonproliferation-treaty-has-largely-achieved-its).
-   Touvron et al. (2023) Hugo Touvron, Thibaut Lavril, Gautier Izacard, Xavier Martinet, Marie-Anne Lachaux, Timothée Lacroix, Baptiste Rozière, Naman Goyal, Eric Hambro, Faisal Azhar, Aurelien Rodriguez, Armand Joulin, Edouard Grave, and Guillaume Lample. LLaMA: Open and Efficient Foundation Language Models, 2023. URL [https://arxiv.org/abs/2302.13971](https://arxiv.org/abs/2302.13971).
-   Trager et al. (2023) Robert Trager, Ben Harack, Anka Reuel, Allison Carnegie, Lennart Heim, Lewis Ho, Sarah Kreps, Ranjit Lall, Owen Larter, Seán Ó hÉigeartaigh, Simon Staffell, and José Jaime Villalobos Ruiz. International governance of civilian AI: a jurisdictional certification approach, August 2023. URL [https://dx.doi.org/10.2139/ssrn.4579899](https://dx.doi.org/10.2139/ssrn.4579899).
-   Trask et al. (2024) Andrew Trask, Aziz Berkay Yesilyurt, Bennett Farkas, Callis Ezenwaka, Carmen Popa, Dave Buckley, Eelco van der Wel, Francesco Mosconi, Grace Han, and others. Secure Enclaves for AI Evaluation, 2024. URL [https://openmined.org/blog/secure-enclaves-for-ai-evaluation/](https://openmined.org/blog/secure-enclaves-for-ai-evaluation/).
-   Trinh and Luong (2024) Trieu Trinh and Thang Luong. AlphaGeometry: An Olympiad-level AI system for geometry, January 2024. URL [https://deepmind.google/discover/blog/alphageometry-an-olympiad-level-ai-system-for-geometry/](https://deepmind.google/discover/blog/alphageometry-an-olympiad-level-ai-system-for-geometry/).
-   Two Sigma (2017) Two Sigma. A Workaround for Non-Determinism in TensorFlow, 2017. URL [https://www.twosigma.com/articles/a-workaround-for-non-determinism-in-tensorflow/](https://www.twosigma.com/articles/a-workaround-for-non-determinism-in-tensorflow/).
-   Tyson (2024) Mark Tyson. Chinese engineer accused of stealing Google’s GPU and TPU secrets, transferring them to China-based startups, 2024. URL [https://www.tomshardware.com/tech-industry/artificial-intelligence/chinese-engineer-accused-of-stealing-googles-tpu-and-gpu-secrets-transferring-them-to-china-based-startups](https://www.tomshardware.com/tech-industry/artificial-intelligence/chinese-engineer-accused-of-stealing-googles-tpu-and-gpu-secrets-transferring-them-to-china-based-startups).
-   (211) UK AI Security Institute. Work. URL [https://www.aisi.gov.uk/work](https://www.aisi.gov.uk/work).
-   UN Security Council (2001) UN Security Council. Resolution 1373 (2001), 2001. URL [https://www-ns.iaea.org/downloads/conventions-codes-resolutions/unsr-1373-2001.pdf](https://www-ns.iaea.org/downloads/conventions-codes-resolutions/unsr-1373-2001.pdf).
-   (213) U.S. Department of Defense, Defense Microelectronics Activity. Trusted Access Program Office: Trusted Supplier Program. URL [https://www.acq.osd.mil/asds/dmea/tapo/trusted-supplier-programs.html](https://www.acq.osd.mil/asds/dmea/tapo/trusted-supplier-programs.html).
-   U.S. Department of Energy, Office of Nuclear Energy (2025) U.S. Department of Energy, Office of Nuclear Energy. Advantages and Challenges of Nuclear-Powered Data Centers, 2025. URL [https://www.energy.gov/ne/articles/advantages-and-challenges-nuclear-powered-data-centers](https://www.energy.gov/ne/articles/advantages-and-challenges-nuclear-powered-data-centers).
-   U.S. Securities and Exchange Commission (2025) U.S. Securities and Exchange Commission. Whistleblower Program, 2025. URL [https://www.sec.gov/whistleblower](https://www.sec.gov/whistleblower).
-   U.S. Securities and Exchange Commission, Office of the Whistleblower (2023) U.S. Securities and Exchange Commission, Office of the Whistleblower. Annual Report to Congress for Fiscal Year 2023. Technical report, U.S. Securities and Exchange Commission, November 2023. URL [https://www.sec.gov/files/fy23-annual-report.pdf](https://www.sec.gov/files/fy23-annual-report.pdf).
-   Vance (2025) James David Vance. Remarks by Vice President Vance at the Artificial Intelligence (AI) Action Summit, 2025. URL [https://lk.usembassy.gov/remarks-by-vice-president-vance-at-the-artificial-intelligence-ai-action-summit/](https://lk.usembassy.gov/remarks-by-vice-president-vance-at-the-artificial-intelligence-ai-action-summit/).
-   Vaswani et al. (2023) Kapil Vaswani, Stavros Volos, Cédric Fournet, Antonio Nino Diaz, Ken Gordon, Balaji Vembu, Sam Webster, David Chisnall, Saurabh Kulkarni, Graham Cunningham, Richard Osborne, and Daniel Wilkinson. Confidential Computing within an AI Accelerator. In _2023 USENIX Annual Technical Conference_, Boston, MA, USA, July 2023. ISBN 978-1-939133-35-9. URL [https://www.usenix.org/system/files/atc23-vaswani.pdf](https://www.usenix.org/system/files/atc23-vaswani.pdf).
-   Verma et al. (2024) Pranshu Verma, Cat Zakrzewski, and Nitasha Tiku. OpenAI illegally barred staff from airing safety risks, whistleblowers say, 2024. URL [https://www.washingtonpost.com/technology/2024/07/13/openai-safety-risks-whistleblower-sec/](https://www.washingtonpost.com/technology/2024/07/13/openai-safety-risks-whistleblower-sec/).
-   Villalobos (2023) Pablo Villalobos. Scaling Laws Literature Review, 2023. URL [https://epoch.ai/blog/scaling-laws-literature-review](https://epoch.ai/blog/scaling-laws-literature-review).
-   Villalobos and Ho (2022) Pablo Villalobos and Anson Ho. Trends in Training Dataset Sizes, 2022. URL [https://epoch.ai/blog/trends-in-training-dataset-sizes](https://epoch.ai/blog/trends-in-training-dataset-sizes).
-   Waiwitlikhit et al. (2024) Suppakit Waiwitlikhit, Ion Stoica, Yi Sun, Tatsunori Hashimoto, and Daniel Kang. Trustless Audits without Revealing Data or Models, 2024. URL [https://arxiv.org/abs/2404.04500](https://arxiv.org/abs/2404.04500).
-   Wasil et al. (2024) Akash R. Wasil, Tom Reed, Jack William Miller, and Peter Barnett. Verification methods for international AI agreements, 2024. URL [https://arxiv.org/abs/2408.16074](https://arxiv.org/abs/2408.16074).
-   Wololo (2023) Wololo. Picofly: The $3 Nintendo Switch Hacking Modchip Is Real, and It’s Now Available, 2023. URL [https://wololo.net/2023/03/21/picofly-the-3-nintendo-switch-hacking-modchip-is-real-and-its-now-available/](https://wololo.net/2023/03/21/picofly-the-3-nintendo-switch-hacking-modchip-is-real-and-its-now-available/).
-   Wouters (2022) Lennert Wouters. Glitched on Earth by Humans: A Black-Box Security Evaluation of the SpaceX Starlink User Terminal. In _Black Hat USA 2022_, 2022. URL [https://i.blackhat.com/USA-22/Wednesday/US-22-Wouters-Glitched-On-Earth.pdf](https://i.blackhat.com/USA-22/Wednesday/US-22-Wouters-Glitched-On-Earth.pdf).
-   Yang et al. (2016) Kaiyuan Yang, Matthew Hicks, Qing Dong, Todd Austin, and Dennis Sylvester. A2: Analog Malicious Hardware. In _2016 IEEE Symposium on Security and Privacy (SP)_, pages 18–37, 2016. doi: 10.1109/SP.2016.10. URL [https://doi.org/10.1109/SP.2016.10](https://doi.org/10.1109/SP.2016.10).

[^1]: A verification procedure might not directly detect a substantive violation; a non-compliant party might refuse to cooperate. Still, such uncooperativeness could be presumed to indicate a substantive violation (as in nuclear non-proliferation) (Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)), and it could be defined as a procedural violation.
[^2]: In the U.S. Congress, tech lobbyists appear to have reversed a push for regulation by “arguing that strict safety rules would hand America’s AI edge to China” (Bordelon, [2024](https://arxiv.org/html/2507.15916v2#bib.bib22)). In the months since, senior legislators from both parties have opposed prominent AI safety proposals (The Hill & Valley Forum, [2024](https://arxiv.org/html/2507.15916v2#bib.bib200); Pelosi, [2024](https://arxiv.org/html/2507.15916v2#bib.bib162)), at times explicitly highlighting tradeoffs between safety and competitiveness: “some of us are also concerned—and I know some of you share these concerns—that \[AI\] could also be a very destructive tool \[…\] \[but\] if we’re too aggressive in our regulations \[…\] we'll wind up ceding ground to China.” Similarly, the Chinese government has backpedaled from stricter AI safety proposals, amidst discussion that “\[f\]ailing to develop is the greatest threat to security” (Sheehan, [2023](https://arxiv.org/html/2507.15916v2#bib.bib188), [2024](https://arxiv.org/html/2507.15916v2#bib.bib189)).
[^3]: With some risks, one-sided compliance could put the compliant party at a disadvantage while doing little to reduce risk. For example, suppose some AI system, if not developed securely, would make it easier for terrorists to obtain weapons of mass destruction, or would lead to an uncontrolled AI system causing global damage. If only one state takes care to ensure its AI systems do not cause these hazards, it may still face the same hazards from other states’ AI systems, while having weakened its own AI industry.
[^4]: By “leaks,” we mean any unauthorized access, public or not (assuming narrow access exclusively for verifying compliance with agreed-on rules is authorized).
[^5]: We use “confidentiality-preserving“ to refer to protecting the confidentiality of corporate intellectual property and state secrets, as well as the privacy of individuals with sensitive data contained in AI datasets (i.e., “privacy-preserving”).
[^6]: Checking public AI products (via their websites or APIs) would have several limitations. (1) These checks would not reveal _non-public_ large-scale AI deployments, such as large AI disinformation farms, cyber attack deployments, or unsafe R&D uses. (2) Dishonest actors might recognize when they are being tested (e.g., based on prompts or IP addresses) and spoof tests, though recognizing tests may be difficult. (3) Stakeholders may wish to know not just how an AI model behaves, but what its training history and innate properties are. For example: “Is a model vulnerable to malicious use because its safeguards were fine-tuned away, or because the intended safeguards fall short?”
[^7]: More precisely, a Prover who minimizes their probability of being caught would choose to circumvent the verification subgoal that has the lowest detection probability, so the overall detection probability would equal that of the lowest-detection-probability subgoal. However, this heuristic does not consider small violations at multiple subgoals that add up (e.g., using a mix of unaccounted-for compute in declared data centers and undeclared data centers).
[^8]: The “data” here refers to training data as well as deployment data, i.e., usage prompts/inputs and associated outputs (and, if desired, intermediate outputs/activations). We use “code” to refer primarily to the algorithms used for training AI models (i.e., model architectures, optimization algorithms, and hyperparameter values). We specifically consider properties that affect system behavior, rather than e.g., code formatting.
[^9]: The “created or used in large-scale AI development or deployment” criterion excludes rules even on small-scale compute uses within large-scale AI activities. For example, verifying a rule on 90% of a frontier AI model’s training data would be in scope, but verifying that 100% of the training data complies with the rule would not necessarily be in scope, as this rule could be violated with small-scale compute use.
[^10]: This analysis builds on discussion by Shavit ([2023](https://arxiv.org/html/2507.15916v2#bib.bib187)) of “What types of rules can we enforce…”
[^11]: On-chip mechanisms and network taps could help verify compliance with intra-chip and intra-cluster cybersecurity rules. Personnel-based verification layers such as whistleblower programs have wide applicability. For example, they would be well-suited to revealing whether most employees are subject to cybersecurity practices that plainly impact their day-to-day work.
[^12]: Historical and proposed verification methods often rely on random sampling and approximation (Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177); Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187)) ([Appendix A.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx4 "A.4 Partial Workload Re-Execution With Constraints ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"); [Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), so they may struggle to distinguish small violations from statistical noise.
[^13]: Thus, a much higher threshold might fail to include future, near-frontier AI activities that may pose national security risks. Meanwhile, a much lower threshold might be impractically intrusive on consumer hardware ([Appendix C.4](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx4 "C.4 Scope: Additional Notes ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")). Finally, we avoid defining “large-scale” in terms of today’s leading chips, since today’s industrial-grade compute may be a future year’s consumer-grade compute.
[^14]: We do not define any large enough set of chips as a computing cluster; they must also be controlled by a single entity. It is unconventional to refer to large, distributed inference compute as a single cluster, but doing so allows us to discuss verification more concisely (by being able to refer to “detecting large-scale clusters” instead of “…clusters or comparably high-performance distributed inference compute”).
[^15]: That is, assuming hardware utilization that is common industry practice for the workload.
[^16]: Frontier AI development tends to be done on the scale of multiple months (Epoch AI, [2024b](https://arxiv.org/html/2507.15916v2#bib.bib60)).
[^17]: On-chip mechanisms and network taps offer full transparency into AI chips’ code and data exchanges, which might allow for verifying that a frontier AI model remains highly contained (e.g., copies of model weights are encrypted and only decryptable by other AI chips with on-chip mechanisms) and that all its uses are known (Scher and Thiergart, [2024](https://arxiv.org/html/2507.15916v2#bib.bib179)). In contrast, the personnel-based layers appear unlikely to be robust here due to the few people needed for small-scale AI deployment, and analog sensors appear unlikely to be robust because small-scale deployments could hide in their margins of error.
[^18]: Many hypothetical rules on AI rely on evaluations to measure risks and the extent to which risks have been mitigated. However, existing evaluations of both risks and mitigations are limited (partly because existing mitigations are limited), and improving them is an active area of research (Hobbhahn, [2024](https://arxiv.org/html/2507.15916v2#bib.bib97); Bengio et al., [2025a](https://arxiv.org/html/2507.15916v2#bib.bib16)). This report focuses on protocols by which—given an evaluations suite—it could help verify that AI models, data, and code are compliant. These are quite different problems, e.g., one could have a perfect evaluations suite but be unable to run it confidentially, or be unaware of hidden models that should be tested.
[^19]: This conceptual division matches an organizational division in nuclear nonproliferation: the International Atomic Energy Agency (IAEA) is responsible for verifying compliance, and the IAEA primarily refers cases of apparent non-compliance to states for enforcement (primarily by reporting to the UN Security Council) (Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177)).
[^20]: In particular, tamper-proof, compliance-locked hardware ([Section 4.1.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx1.Px2 "4.1.1.2 Verification Mechanisms ‣ 4.1.1 Mechanisms ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"); [Section 4.2.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1.Px2 "4.2.1.2 Verification Mechanisms ‣ 4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) would verify compliance by blocking AI hardware from being used for violations at all—which also enforces compliance. The known locations of AI compute clusters (Subgoal 2.B) could also inform enforcement actions.
[^21]: These included areas of machine learning, AI policy, computer security & cryptography, international relations, and arms control verification.
[^22]: To identify sources, we drew on relevant papers we were familiar with from our previous work in this field (Brundage et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib25); Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13); Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121); Heim et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib90)), followed citation trails, searched relevant terms ([Appendix C.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx3.SSSx5 "C.5 Related Work ‣ C. Methodology Details ‣ Appendices ‣ Verifying International Agreements on AI")) on Google Scholar and Google Search, and considered publications mentioned by interviewees.
[^23]: Our interviewees’ backgrounds spanned computer security, hardware, machine learning, AI policy, and international relations, as well as experience in academia, industry, and nonprofits.
[^24]: In nuclear arms control, multilateral verification is done both by a third party—the International Atomic Energy Agency—while bilateral verification was done by national institutions—the United States and Soviet Union directly verifying each other’s compliance.
[^25]: In practice, the Verifier will not be completely certain about each subgoal they completed, so the conclusion will also not hold with complete certainty (for example, the Verifier may deem 90% credence sufficient).
[^26]: An AI chip registry is one possible structure for reporting AI compute ownership; declaring individual AI chips is not strictly necessary but facilitates verification.
[^27]: Checking completeness means checking that there are no omissions—that is, no undeclared, large-scale AI compute clusters, nor undeclared large-scale uses of AI compute clusters.
[^28]: Declarations of compute use would contain the core IP of AI labs (namely model weights and algorithms)—ownership of which directly confers economic (and perhaps eventually, strategic)—benefits, making these declarations highly sensitive. In contrast, declarations of compute ownership (containing information about AI data centers) are not as directly useful to competitors or adversaries. Hypothetically, an adversary could abuse compute ownership declarations to set military targets, but an analogous risk did not keep the United States and Soviet Union from sharing the locations of their nuclear weapon bases with each other (Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13)). Additionally, risk of targeting could be mitigated via deterrence and shielding.
[^29]: However, a small-scale violation in each of the two categories could combine to constitute a large-scale violation. To address this, a buffer could be added to the thresholds defining “large-scale” (e.g., having the thresholds for the scope of each subgoal be half of how the threshold is defined for the larger goal). This also applies for the remaining break-downs.
[^30]: Workload declarations are declarations of how the result of an AI workload—an AI model or output—is generated, so verifying the accuracy of a workload declaration is equivalent to verifying that AI models and outputs are generated as declared.
[^31]: The distinction here is that AI compute clusters are AI computing equipment, while AI data centers are the facilities that host one or more of these clusters.
[^32]: That is, a verification regime’s probability of detecting a violation is approximately that of the subgoal with the lowest probability of detecting a violation. This is because a Prover only needs to circumvent one verification subgoal to hide a violation, and a rational Prover seeking to hide a violation will choose to circumvent the subgoal where they are least likely to be caught. This assumes there are not practical considerations that motivate greater risk-taking from the Prover (e.g., high costs of a violation in one subgoal), and for simplicity it ignores the possibility of aggregating smaller violations across several subgoals (which may involve a lower or higher probability of detection, depending on the detection probabilities and their correlation).
[^33]: The term “mechanisms” are discussed somewhat similarly in prior work (Brundage et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib25)).
[^34]: “Similar” refers to the mechanisms having similar assumptions and tradeoffs. This gives a layer as a whole distinctive assumptions and tradeoffs.
[^35]: Some verification mechanisms, such as whistleblower programs, are so generally applicable that they can be used for every verification subgoal. In these cases, a whole verification layer can be made up of a single mechanism, applied to every subgoal.
[^36]: In typical implementations, the party granting approval is the hardware vendor. If the hardware vendor is not trusted, it may be feasible to transfer approval authority to a chosen Verifier (via cryptographic key revocation).
[^37]: In keeping with the “on-chip” approach of this verification layer, tamper-evident and tamper-proof measures could be built into AI chips. Such anti-tamper measures within AI chips would add redundancy to other verification layers, which might implement anti-tamper measures around the chips (e.g., on a server enclosure or via tamper-evident video cameras). Notably, here “tampering” includes simply turning off a secure boot functionality if it is intended to be optional; this could be made tamper-evident through measures involving secure storage, secure memory, compute accounting, or offline licensing ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI"))
[^38]: That is, “secure” in the sense that the Prover cannot read or overwrite the key, at least not without leaving tamper evidence.
[^39]: One might wonder: how can a Prover be assured that the Verifier’s test questions will not extract more information than is appropriate, if the Prover cannot access the test questions? For one, the Prover could confirm that the Prover’s tests only output a very small amount of information (e.g., just a “pass” or “fail” result), so they have little bandwidth to extract information. Additionally, the approved program could enforce constraints on the Verifier’s tests, e.g., that they can run a model but not arbitrarily access individual model weights. Alternatively, the Verifier could make more tests transparent to the Prover, though this could make it easier for the Prover to “cheat the tests” (i.e., find ways to pass them while still committing a violation).
[^40]: Specifically, here we describe the multi-party computation functionality of CC, though the more commonly used functionality is for running computations on cloud compute without exposing them to the cloud provider.
[^41]: This is similar to some aspects of proposed Flexible Hardware-Enabled Guarantees (FlexHEGs) (Petrie et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib164)), but here we are discussing an entirely on-chip option rather than compliance-locking based on external devices attached to a chip.
[^42]: In other words, suppose AI chips throttle their own performance unless they receive periodic confirmation that they are in compliance—confirmation which the Verifier provides (as a digital signature) based on workload certificates ([Appendix A.2](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx2 "A.2 Hardware-Backed Workload Certificates and Evaluations ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). Then, any non-complaint AI data centers will soon become useless.
[^43]: In particular, a limited and known-to-the-Verifier set of _Prover_ chips could be authorized to approve offline license requests, and the Verifier could monitor all communication with these chips (e.g., by network tap or physical access controls). Thus, the Prover would grant licenses but the Verifier would know about them, adding redundancy for Subgoal 2.B without the tradeoffs of Verifier enforcement power. There may still be concern over these Prover chips being sabotaged, as that could deny the Prover their licenses, so it could help for some backups (i.e., other Prover chips authorized to approve license requests) to be (verifiably) stored in highly secure locations.
[^44]: This analysis also applies to other high-performance chips in the same cluster as the AI chips, especially CPUs.
[^45]: One hardware security expert noted that, whenever the security community has gotten their hands on an HSM, they were able to break its security guarantees (Interview #2, 2024). For example, a graduate student on a laptop broke Intel’s Trusted Platform Module in 2020, despite its high security certification (Moghimi et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib138)). Researchers have also found many vulnerabilities in Intel SGX, a confidential computing technology from 2015 (Schwarz and Gruss, [2020](https://arxiv.org/html/2507.15916v2#bib.bib182)). Beyond Intel, other companies including Apple, Android, SpaceX, and NVIDIA have also had failures in robustly implementing secure boot (Hildenbrand, [2018](https://arxiv.org/html/2507.15916v2#bib.bib94); Crider, [2022](https://arxiv.org/html/2507.15916v2#bib.bib44); Ridley, [2021](https://arxiv.org/html/2507.15916v2#bib.bib174); Wouters, [2022](https://arxiv.org/html/2507.15916v2#bib.bib225); [The Apple Wiki,](https://arxiv.org/html/2507.15916v2#bib.bib199) ; Jirků, [2022](https://arxiv.org/html/2507.15916v2#bib.bib111); Wololo, [2023](https://arxiv.org/html/2507.15916v2#bib.bib224)). Intel also reports that, between its own and AMD’s Confidential Computing and hardware root-of-trust technologies, 55 vulnerabilities were discovered in 2024 (Intel Corporation, [2025](https://arxiv.org/html/2507.15916v2#bib.bib102)).
[^46]: “Circumventing secure boot on iPhones is popularly known as “jailbreaking” iPhones. While jailbreaks were common in the early- to mid-2010s \[…\] \[t\]oday jailbreaking \[using publicly known methods\] is only possible if the phone’s operating system hasn’t been updated in several years” (Aarne et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib2)).
[^47]: Hardware security academics suggested that, despite its importance, it is rare for hardware companies to engage leading security research labs to stress-test their products (Interviews #2 and 11, 2024). In line with this, Intel reports that the 21 hardware vulnerabilities they discovered in 2024 were “all found internally” (Intel Corporation, [2025](https://arxiv.org/html/2507.15916v2#bib.bib102)), though Intel has had partnerships for security reviews (Aktas et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib4)). Relatedly, NVIDIA states that it “does not currently have a bug bounty program” ([NVIDIA,](https://arxiv.org/html/2507.15916v2#bib.bib151) ). Even companies with bug bounties rarely offer more than $100,000 rewards, even for discoveries of “critical” or “exceptional” hardware vulnerabilities ([Google,](https://arxiv.org/html/2507.15916v2#bib.bib78) ; [Microsoft,](https://arxiv.org/html/2507.15916v2#bib.bib135) ; [Intigriti,](https://arxiv.org/html/2507.15916v2#bib.bib106) ; [Intel Corporation,](https://arxiv.org/html/2507.15916v2#bib.bib100) ).
[^48]: The security experts we interviewed often expressed that HSMs—chip regions exclusively dedicated to security features, to make them simpler to secure—would improve security (Interviews #2, 4, 6, 9, 11, 18). However, leading AI chips such as NVIDIA’s lack HSMs; NVIDIA GPUs have a broader-purpose “GPU System Processor” (Klotz, [2022](https://arxiv.org/html/2507.15916v2#bib.bib118)).
[^49]: A hardware security expert underscored a tradeoff between a chip’s performance and its security, saying it is “very difficult” to convince hardware companies “that security… may \[need to\] cost you performance” (Interview #4, 2024). This is in line with prior research (Hastings and Sethumadhavan, [2020](https://arxiv.org/html/2507.15916v2#bib.bib85)) and vulnerabilities (Lipp et al., [2018](https://arxiv.org/html/2507.15916v2#bib.bib128); Kocher et al., [2018](https://arxiv.org/html/2507.15916v2#bib.bib119)). In addition, fixing security vulnerabilities could delay product releases.
[^50]: Some firmware—namely that stored in read-only-memory (ROM) such as Boot ROM—cannot be digitally edited.
[^51]: One study estimates that NVIDIA shipped nearly 4 million data center GPUs in 2023 (Shah, [2024](https://arxiv.org/html/2507.15916v2#bib.bib186)), and NVIDIA’s revenue has been growing rapidly since then (NVIDIA, [2024](https://arxiv.org/html/2507.15916v2#bib.bib155)). For a sense of the potential costs of replacement, replacing “just” 4 million H100 GPUs costing $30,000 each (Eadline, [2023](https://arxiv.org/html/2507.15916v2#bib.bib56)) would cost $120 billion.
[^52]: In many cases, communication limits could involve ensuring the devices are disconnected from the internet (i.e., air-gapped). This would assure Provers that (i) the devices cannot easily transmit data to the Verifier, and (ii) the Verifier cannot easily send a message to many of the devices at once (which, if possible, could presumably facilitate sabotage).
[^53]: Inspections introduce the problem of assuring the Prover that the inspectors do not pose threats. This could be addressed similarly to how it has been addressed over decades of nuclear arms control, where inspectors are continuously accompanied by Prover representatives, among other measures (Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13)).
[^54]: The term “trusted clusters” has also been used by related work (Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187); Heim, [2024](https://arxiv.org/html/2507.15916v2#bib.bib87)).
[^55]: Insofar as the Prover knows what tests the Verifier will run ([Section 4.5](https://arxiv.org/html/2507.15916v2#Sx5.SSx5 "4.5 Implementation Options Across Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), the Prover may also be able to determine some of the exact information that the Verifier will extract. Then, by checking that the Verifier’s limited extracted information excludes this expected information, the Prover could reduce the Verifier’s room for unauthorized information extraction. Thus, the Prover could benefit from monitoring the content of the extracted information, not only its quantity.
[^56]: One potential source of information leakage is the IT equipment emitting information through non-human channels, especially wires or electromagnetic waves. By managing the “outer room,” the Prover-trusted actor can physically block these communication options. (Blocking electromagnetic waves may require a large Faraday cage.) By monitoring and gatekeeping personnel as they exit, the Prover-trusted actor can also ensure that operators do not take data storage devices with them (beyond data they are supposed to have). Similarly, by supervising the operators, the Prover-trusted actor can confirm that computer monitors only show what they are supposed to show. There is still some risk that these security measures may be circumvented, e.g., via bribery, but a Prover already accepts such risks when they hold sensitive information in their own data centers.
[^57]: This mechanism could loosely be considered “off-chip verification” in that the separate devices used are the video cameras, and the “on-chip” or “personnel” categories would fit less well. Still, it is less technically demanding or complex than the other mechanisms in this list.
[^58]: Technically a server could be “compliant” without being “declared,” but if this is a concern, compliance could be made to require declaration, e.g., by using offline licensing to disable undeclared data center AI servers.
[^59]: To be clear, the track record of dedicated hardware security devices is also lacking (Moghimi et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib138)). Still, as discussed ([Section 4.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx2 "4.1.2 Analysis ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")), the challenges related to supply chains, incentives, and complexity are substantially less severe than in the on-chip case.
[^60]: A complication here is that the Verifier may wish to run some programs on the same kind of chips as the Prover’s chips, to directly re-run Prover workloads or understand these chips’ behavior under different workloads. However, such tests could be compromised by hardware backdoors; more generally, they could defeat the purpose of off-chip mechanisms: robustness to untrusted Prover chips. Fortunately, the Verifier could complete several other checks to verify the results of tests run on Prover chips. The Verifier could (i) have the Prover convert their code to run on Verifier hardware; (ii) do high-level modeling of the Prover’s chips (Erdil and Schneider-Joseph, [2024](https://arxiv.org/html/2507.15916v2#bib.bib63); Erdil, [2025](https://arxiv.org/html/2507.15916v2#bib.bib61)), informed by physical measurements ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")); and (iii) emulate the understood functionalities of the Prover’s chips (though one interviewee warns this would only be practical at very small scales, as cost overheads of AI chip emulation are on the order of 10,000x; Interview #17). Check (i) constrains any backdoored behavior to approximate regular behavior (or to be equivalent for deterministic programs), and check (ii) may detect unnecessarily altered physical signatures. Further, the Verifier could run only replicas of individual pods of Prover hardware to reduce costs.
[^61]: Even if the Verifier does run some hardware of the same kind as the Prover’s hardware, the Verifier can run it more securely than if it were in the Prover’s own data centers. With the Verifier in control, the Verifier can (i) use trusted hardware for some functionalities (e.g., using CPUs and network chips from a trusted supply chain, or perhaps FPGA substitutes, even if the AI chips are untrusted); (ii) implement protections against physical and digital attacks, especially known ones; (iii) check for approximate consistency across multiple kinds of hardware on compatible test cases; and (iv) perhaps manufacture a small amount of patched hardware to replace vulnerable hardware (whereas doing this for all the Prover’s hardware would be more costly).
[^62]: As one potential ingredient, there are open-source HSMs ([Nitrokey,](https://arxiv.org/html/2507.15916v2#bib.bib145) ). One interviewee shared an anecdote of a hardware security lab that does “90%” of their red teaming on open-source hardware systems, as these are much easier to study and tend to be more willing to adjust in response (Interview #2, 2024).
[^63]: There could be whistleblowers without a formal, cooperative program, but then many of the below features to enable and encourage whistleblowers (e.g., regular in-person contact) would be harder to bring about.
[^64]: We emphasize _national_ intelligence activities because states have spent decades or longer building intelligence capabilities, unlike international agencies. The International Atomic Energy Agency, for example, has often learned of violations from national agencies rather than on its own (Rosenthal et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib177); Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13)). Additionally, authorizing an international agency to engage in espionage would expose states to new intelligence risks, while national intelligence activities are the status quo.
[^65]: Whistleblower programs could be run without the Prover’s cooperation, but important practices for their effectiveness, such as regular interviews of employees, rely on Prover cooperation ([Appendix A.8](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx8 "A.8 Whistleblower Programs ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
[^66]: Per one interviewee with experience in hardware manufacturing, a change to the design (i.e., the “mask”) of an existing chip would by default be known to many people in the manufacturing company, as there are software-enforced approval requirements and physical testing for anomalies in designed chips. Moreover, the standard process for changing a design involves paper trails and several layers of signoff (Interview #7, 2024).
[^67]: As an additional hurdle for violators, perhaps all automated AI engineers could be, by requirement, trained to refuse to assist with violations and instead attempt to blow the whistle on any violations (effectively replacing human whistleblowers with “AI whistleblowers”). This could be circumvented by humans at some point removing this behavior or refraining from implementing it, but that would still introduce humans who could whistleblow.
[^68]: Numbers are based on counting the number of distinct names in each category of the models’ papers’ “Contributions” sections (OpenAI et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib159); Llama Team, [2024](https://arxiv.org/html/2507.15916v2#bib.bib129); Gemini Team et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib73)), excluding listed external collaborators. OpenAI’s GPT-4 paper thanks “Microsoft Azure for supporting model training with infrastructure design and management,” suggesting Azure staff are not named as contributors.
[^69]: Foreseeing this, a Prover may instead choose a less niche way to hide their data center, such as building it underground or in what appears to be another kind of facility. Still, these options would likely entail higher costs and more accomplices—and thus more potential whistleblowers or human sources—than if the Prover could simply build a data center without worrying about satellite detection.
[^70]: In the context of compute accounting via analog sensors ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), one implementation option involves physical signatures. This could also be considered a form of workload classification, but it would be more fine-grained—in both its measurements and classifications—than workload classification as discussed here.
[^71]: In scenarios where extremely decentralized training is highly effective, e.g., if violations could be done through extremely decentralized networks of thousands of consumer electronics, this would undermine the on-chip and off-chip verification layers, which focus on AI chips. Still, the personnel-based verification layers could remain effective; extremely decentralized networks would likely involve many accomplices.
[^72]: Broader societal impacts of AI deployment could be delayed if a violator focuses on internal deployment within one organization, such as using AI for AI R&D. In addition, perhaps it would be challenging to quickly determine whether economic, scientific, or military advances reflect ordinary processes, compliant AI, or non-compliant AI.
[^73]: Note the use of auditors is a spectrum, which can be varied by a technical parameter: the amount of information that auditors receive as intermediate results. This spectrum ranges from (i) Verifier auditors only receive a single yes/no result about compliance, to (ii) Verifier auditors receive arbitrarily large amounts of intermediate results. There are intermediate options, where auditors receive a fixed amount of information beyond a yes/no compliance determination (e.g., identification of specific aspects of a Prover’s declarations that warrant further scrutiny).
[^74]: Technical AI verification R&D is a challenge of developing adversarially robust software and/or hardware, which is precisely what computer security focuses on. In addition, some specific topics in AI verification, such as cryptography and secure boot, are primarily studied in computer security.
[^75]: Multiple interviewees—a large fraction of the computer security experts we interviewed from academia and industry—highlighted ways in which the scenarios we consider differ from their usual threat models (Interviews #1, 5, and 11, 2024). Still, hardware security features are active areas of R&D, though arguably not at the needed level of robustness ([Section 4.1.2](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx2 "4.1.2 Analysis ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). Some workload modeling is presumably also already done by AI companies, e.g., to optimize hardware utilization.
[^76]: For example, hardware design attestation (as we define it) is unnecessary if you trust the hardware designer to check that the layout matches their Hardware Description Language, off-chip analog sensors for inferring compute use are unnecessary if you trust on-chip performance counters, and malicious code is less of a concern if you are the user writing the code.
[^77]: For example, the Verifier may be able to avoid intentional backdoors by acquiring hardware from Verifier-trusted suppliers, and the Verifier could potentially run computations on multiple devices from different suppliers to detect uncoordinated backdoor activation. Additionally, for Verifier-operated hardware, the Verifier has additional defenses available against efforts to trigger a Hardware Trojan or leverage side-channel attacks.
[^78]: This refers to the _Verifier’s_ software being implemented correctly; verification does not necessarily require the Prover’s application-layer software to be implemented correctly.
[^79]: As prior verification work has noted (Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187)), there are existing initiatives on open-source hardware roots-of-trust (Larabel, [2022](https://arxiv.org/html/2507.15916v2#bib.bib125)). However, the Verifier would need to confirm that a root-of-trust is functionally incorporated into the rest of the chip, rather than e.g., being a decoy.
[^80]: Stakeholders may be at least partly compensated by improved confidence in product security, AI tools such as code models may facilitate vulnerability detection (Fang et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib65)), and much leading AI chip IP has reportedly already been stolen (which may limit the downsides of intentional disclosures) (Clark, [2022](https://arxiv.org/html/2507.15916v2#bib.bib38); Tyson, [2024](https://arxiv.org/html/2507.15916v2#bib.bib210)).
[^81]: The U.S. Department of Defense has a Trusted Foundry Program that may achieve this ([U.S. Department of Defense, Defense Microelectronics Activity,](https://arxiv.org/html/2507.15916v2#bib.bib213) ).
[^82]: Confidentiality-preserving technologies would only be secure on an infrastructure stack that the Verifier has other reasons to trust (e.g., having applied the other listed methods to the confidentiality-preserving technology).
[^83]: This includes remote firmware attestation (Edery et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib57)). We do not mark this as technically ambitious to reflect that, _if_ lower layers (i.e., firmware and hardware) are secure, then firmware attestation is relatively straightforward.
[^84]: Formal verification is an active area of work in both software (Hasan and Tahar, [2015](https://arxiv.org/html/2507.15916v2#bib.bib84); Souyris et al., [2009](https://arxiv.org/html/2507.15916v2#bib.bib193)) and hardware (Kern and Greenstreet, [1999](https://arxiv.org/html/2507.15916v2#bib.bib115); De Oliveira Nunes et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib49)). Formal verification is labor-intensive and challenging to apply to complex software or hardware. Progress in AI has the potential to help reduce its costs and expand its applicability (Lin et al., [2025](https://arxiv.org/html/2507.15916v2#bib.bib127)).
[^85]: In secure boot, firmware attests to itself, so malicious firmware might hide its own malicious properties, analogously to compilers or malware that hide their own Trojans (Thompson, [1984](https://arxiv.org/html/2507.15916v2#bib.bib203); [MITRE Corporation,](https://arxiv.org/html/2507.15916v2#bib.bib137) ). To address this, delayering and scanning of memory that stores firmware may be needed, ideally limited in scope (e.g., only the first-stage bootloader). Still, firmware attestation should at least detect less sophisticated firmware Trojans.
[^86]: Often, boot ROM (read-only memory) firmware is burned onto a chip during manufacturing and is not electronically updatable (Int, [2019](https://arxiv.org/html/2507.15916v2#bib.bib101); NVIDIA, [a](https://arxiv.org/html/2507.15916v2#bib.bib149)). This can lead to electronically unpatchable vulnerabilities, as have been found in Apple’s Boot ROM (Kirk, [2019](https://arxiv.org/html/2507.15916v2#bib.bib117)).
[^87]: Hardware designs could be verified by (i) verifying that a manufactured layout precisely matches a claimed layout, and (ii) verifying that the claimed design (i.e., netlist) corresponds to the claimed layout (with no analog additions). Fortunately, the semiconductor industry has established methods for reverse-engineering chips (e.g., for failure analysis or IP litigation). These include, for (i), “delayering” a chip—removing layers one by one—and scanning each layer with a sophisticated microscope, especially a scanning electron microscope (Lumenci Team, [2022](https://arxiv.org/html/2507.15916v2#bib.bib131); Thermo Fisher Scientific, [2025](https://arxiv.org/html/2507.15916v2#bib.bib201); Yang et al., [2016](https://arxiv.org/html/2507.15916v2#bib.bib226)); and, for (ii), methods for “circuit extraction.” Prior work suggests that even analog hardware Trojans may be detectable by scoped delayering (Yang et al., [2016](https://arxiv.org/html/2507.15916v2#bib.bib226)). Notably, circuit extraction or reverse-engineering is not the only possible approach; one could also re-run programs that map from Hardware Description Language (HDL) to a netlist and then to a layout. However, re-running programs may be nondeterministic (for efficiency) and computationally expensive; “\[m\]odern EDA \[Electronic Design Automation\] workloads utilize 20,000 to 100,000 parallel compute cores on a single design” (Amazon Web Services, [2023](https://arxiv.org/html/2507.15916v2#bib.bib6)).
[^88]: For instance, seL4, the “first ever industrial-strength, general-purpose operating system with formally proved implementation correctness,” was only published in 2009 rather than decades earlier ([Association for Computing Machinery,](https://arxiv.org/html/2507.15916v2#bib.bib12) )
[^89]: Companies often face relatively low penalties for weak cybersecurity (Dean, [2015](https://arxiv.org/html/2507.15916v2#bib.bib51)).
[^90]: One could simultaneously: parallelize across layers (i.e., at the limit, for a chip with N layers, delayer N separate copies of the chip to reach a different target layer in each, and then simultaneously scan all layers), parallelize across sampled chips (i.e., scan multiple samples of the same layer at once, as multiple samples are needed to remove noise), and parallelize within each layer of each chip (via multiple electron beams or perhaps slicing each chip perpendicular to the surface—there are photolithography mask writers with 260,000 beams each (NuFlare Technology, Inc., [2025](https://arxiv.org/html/2507.15916v2#bib.bib148))). However, these parallelization methods would come at significant expense, due to the need for more equipment, more sophisticated equipment, and destructive analysis of more chips.
[^91]: Hardware often offers the option to disable secure boot (NVIDIA, [2023c](https://arxiv.org/html/2507.15916v2#bib.bib154); Microsoft, [2021](https://arxiv.org/html/2507.15916v2#bib.bib136)), but firmware could likely be updated to remove this option. Hardware vendors have previously attempted this, though with exploitable vulnerabilities (Hildenbrand, [2018](https://arxiv.org/html/2507.15916v2#bib.bib94); [The Apple Wiki,](https://arxiv.org/html/2507.15916v2#bib.bib199) ; Jirků, [2022](https://arxiv.org/html/2507.15916v2#bib.bib111); Wololo, [2023](https://arxiv.org/html/2507.15916v2#bib.bib224)).
[^92]: For example, there could be an increment-only counter which increments every clock cycle that the device is run without appropriately signed firmware (with an overflow-resistant maximum size).
[^93]: However, this may be incompatible with a security air gap.
[^94]: As one class of attacks, a Prover could form a cluster that consists of both compliant chips and malicious chips (i.e., chips that lack the hardware-backed workload certificates protocol). The malicious chips could then engage in data communication without logging it, or a malicious CPU could provide unlogged instructions to a compliant AI chip. One way to address these attacks is for compliant chips to check that fellow chips in their cluster are also running the required protocol, demonstrated by presenting a separate certificate signed by the Verifier. Alternatively, the master CPU could keep track of the identities of the chips in its cluster and include these in the certificate; unauthorized chip additions or omissions could then be apparent. For ensuring that a connection, once established, is maintained, the chips could use encryption, or perhaps occasional challenges, electronic measurements, or external tamper-evident security cameras.
[^95]: The system software cannot simply assume that e.g., in a training workload, a cluster’s inputs from external devices will be the training data, and the cluster’s outputs to external devices will be the trained model weights. This assumption would not be robust; the “real” models or data—that which a cluster internally uses as models or data—could be encoded in benign-looking cluster inputs or outputs. Moreover, synthetic data could be generated within a cluster rather than being supplied by external devices.
[^96]: Or the system software does not check accuracy directly, but signs a data log that allows the Verifier to later check.
[^97]: For example, model weights are involved in all-reduce operations during training and are the primary output from the cluster at the end of training.
[^98]: The secure storage and offline licensing options are similar to prior proposals (Shavit, [2023](https://arxiv.org/html/2507.15916v2#bib.bib187)).
[^99]: Secure storage could potentially be implemented through e.g., fuse burning or other increment-only on-chip non-volatile storage (especially for storing a simple count), with a large enough range to prevent overflows. A further security layer could be only allowing the system software to edit this storage.
[^100]: Though logging clock time would require the ability to detect or counter attacks like overclocking.
[^101]: For compatibility with on-chip verification that uses Confidential Computing, one could run occasional tests on a small fraction of hardware with Confidential Computing, but not use Confidential Computing for regular operation.
[^102]: Thanks to Jonathan Happel for this idea.
[^103]: More precisely, the problem here (in the context of verifying training, i.e., Subgoal 1.A.1) is close to the proof-of-training-data problem as defined in prior work (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)). However, there is an important difference; here, the Verifier may be able to assume that the amount of compute the Prover can use to create a spoof is at most the amount of compute the declared workload would take, on the basis of compute accounting ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")). In this respect, the problem here may more closely resemble proof-of-learning (Jia et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib110)).
[^104]: Further, constraints should rule out “glue-ing” attacks, where segments of different training workloads are presented as consecutive portions of one workload. These attacks would create discrepancies only in rare transition points, so random sampling would be unlikely to detect them (Jia et al., [2021](https://arxiv.org/html/2507.15916v2#bib.bib110)). Instead, cheap tests applied to all training segments would be a more viable countermeasure (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)).
[^105]: This is not applicable to training in which the data is generated iteratively (e.g., reinforcement learning with online learning). It is only feasible to a limited extent for training if the data order is fixed for curriculum learning.
[^106]: If the Verifier can verify that the Prover does no undeclared, large-scale workloads (Subgoal 2) and that none of the declared workloads consist of generating a spoofed (i.e., non-unique) declaration, this will constrain the amount of compute the Prover can spend on creating a spoof.
[^107]: For example, a workload could potentially be modified (e.g., by perturbing activations or changing the sampling seed) so its outputs are more dependent on previous outputs, or so they are dependent on a Verifier-provided value (thus verifying they were produced after the Verifier provided that value), or to be more frequently shared with the Verifier (thus verifying intermediate outputs existed by some point). Perhaps verifiable delay functions (Boneh et al., [2018](https://arxiv.org/html/2507.15916v2#bib.bib21)) could also contribute to timing constraints. These constraints could make it more challenging for a Prover to retroactively modify values to create spoofs. Thanks to Daniel Reuter for a version of this idea.
[^108]: Choi, et al. (Choi et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib34)) mention that randomizing the data order “does not address hypothetical methods for constructing synthetic data points that would induce a particular gradient with respect to any weight vector that would be encountered across many possible training runs with high probability,” though no such methods are known. In case such methods were found, one could detect their use by checking for whether most gradients in a sample of gradients are highly similar to each other. This check may also detect a hypothetical attack involving a loss function that optimizes a model to be closer to a target model (with weight checkpoints derived by interpolation); other constraints like checking for data memorization may also address that. Perhaps an attacker could still induce a particular gradient _on average_ (after the gradient is scaled by the learning rate or otherwise adjusted by the optimization algorithm), but one could check sample gradients for that property as well.
[^109]: This somewhat overlaps with cross-system analyses, as a gradient calculation can be verified by running a different function for computing a gradient.
[^110]: These attacks should not be confused with the Prover’s code exploiting a vulnerability in the _Verifier’s_ code to corrupt the results of a verification program; we address that separately ([Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
[^111]: (1) In the fully general problem of backdoor detection, one wants to ensure that a program will never activate a backdoor, on any input. Here, the Verifier only needs to ensure that backdoors do not trigger too often on a given set of inputs. Thus, here there is no need to detect latent backdoors; it suffices to sample from the given set of inputs and detect activated backdoor behavior. (2) In the more general problem of detecting AI models with learned backdoors, the standard or non-backdoored behavior might not be precisely known, and it might only depend on the model outputs. When replicating a claimed workload, one might demand low-error replication (e.g., demand exact replication of inference done with integer operations), as well as replication of intermediate results such as intermediate activations. These demands pose additional constraints for an attacker, perhaps making subtle backdoors infeasible.
[^112]: As discussed, Choi, et al. do not explicitly address malicious code attacks, but their defenses may nonetheless generalize to these attacks. This is somewhat suggestive of the generalizability of current defenses to novel attacks.
[^113]: Another attack could be over-stating their ratio of hardware operations to model operations, but we address this in our discussion of compute accounting via analog measurement of AI chips ([Appendix A.6](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx6 "A.6 Compute Accounting via Analog Sensors ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")).
[^114]: This defense (c) may be especially effective if paired with a code factorization constraint ([Appendix A.5](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx5 "A.5 Data and Code Validation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) that hinders efforts to manipulate intermediate activations.
[^115]: Programs could potentially be securely saved for later analysis when data and code validation methods have further improved, potentially deterring violations that would occur over a long time period (even if the Prover knows initial validation techniques are unreliable).
[^116]: The expected properties of data could be determined based on the fact that, currently, much of the data used to pre-train foundation models tends to be of a few types—natural language text, code, and (for multimodal models) photographs and potentially audio recordings (Brown et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib24); Villalobos and Ho, [2022](https://arxiv.org/html/2507.15916v2#bib.bib221); Touvron et al., [2023](https://arxiv.org/html/2507.15916v2#bib.bib205); Gemini Team et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib73))—though synthetic data may become increasingly prominent (Trinh and Luong, [2024](https://arxiv.org/html/2507.15916v2#bib.bib208)). As another caveat, when considering what data “is expected to look like,” it would be important to account for how linguistic and regional variation, as well as innovation (including in synthetic data) and unique use-cases, may lead to unexpected datasets.
[^117]: A message could be encoded in a public dataset (either by the creator of the dataset, or by a creator of content scraped for the dataset). This may be simplest to counter by requiring that public datasets used be sufficiently old (such that a violation leveraging them would be impractically slow), but that would pose performance tradeoffs. Third parties providing data could be compromised; a whistleblower system may address this if the number of parties involved is large enough. Synthetic data could also be synthesized maliciously; one may need a further level of code and/or data auditing to detect this.
[^118]: This raises the question of how to protect the weights of the “inspector” AI model from being stolen. This problem is an instance of wishing to protect private details of the Verifier’s tests, which would be addressed by successful implementations of confidentiality-preserving technologies such as trusted clusters or Confidential Computing.
[^119]: As a slightly simplified example, for AI training code, one could check that code is factored into functions including: (i) a forward pass and loss function, which together access a data batch and the model weights to produce a loss value (potentially with a regularization term); (ii) a backward pass function, which accesses a loss value, a data batch, and the model weights to compute the gradient; and (iii) an update rule, which updates weights by adding a (simple) function of the current and potentially previous gradients (note this accommodates SGD, momentum, Adam, Shampoo, and close variants, which are also used in RL algorithms such as DQL and PPO) ([Hugging Face,](https://arxiv.org/html/2507.15916v2#bib.bib99) ; Schulman et al., [2017](https://arxiv.org/html/2507.15916v2#bib.bib181)). Mathematically, the constraints are: $W_{i+1}=W_{i}+u(g_{1},\dots,g_{i})$. $g_{i}=\nabla_{W}L(f_{W_{i}}(X_{i}))$. ($u$ could be further constrained to simplicity, e.g., being fully encodable in ¡ 10,000 characters in Python, including calls to standard libraries and saving variables for use in future updates.) When replicating portions of the Prover’s training run, the Verifier could enforce these structural constraints by running the pipeline that connects the Verifier-provided functions and data files, and ensuring each function is otherwise sandboxed. Additionally, the Verifier could check that the gradient computation in (ii) is mathematically correct, by substituting a different backward pass function known to be valid. These checks would mean that, if a Prover wanted to, for example, overwrite weights with pre-computed weights encoded in training data, they could not directly do so; instead, they would need to implement this within the functional form of gradient descent or its variants. Additionally, all functions other than the loss and forward pass functions would be heavily constrained, allowing the Verifier to focus other checks (e.g., analysis by a code model) on the forward pass function.
[^120]: Provers may need to submit two versions of their code: one factored to facilitate code validation, and another with the (claimed) original speed for operations accounting. (The Verifier could check that the two codes’ outputs are sufficiently similar.)
[^121]: “Compute accounting” has previously been defined as “measurements and techniques to produce an estimation of the amount of compute consumed by a customer running one or more workloads on a specific compute cluster,” (Heim et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib90)), consistently with the term’s earlier use (Brundage et al., [2020](https://arxiv.org/html/2507.15916v2#bib.bib25); Jackson et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib107)). Our use of the term is a little different; here, the goal is not only to produce one estimate, but to compare estimates of “sources of compute” with “uses of compute” to ensure the former is legitimately accounted for.
[^122]: They are all compatible except for options (A) and (B) specifically in the context of AI training. In AI training (but not inference), (A)’s conservative assumption that MFU is optimized is inconsistent (in the context of AI training) with (B)’s conservative assumption that _MFU = HFU_ (Chowdhery et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib35)).
[^123]: An important concept for compute accounting via external sensors is the distinction between model FLOP and hardware FLOP, and relatedly between Model FLOP Utilization (MFU) and Hardware FLOP Utilization (HFU) (Chowdhery et al., [2022](https://arxiv.org/html/2507.15916v2#bib.bib35)). In a given AI training workload, model FLOP are _unique_ operations, while hardware FLOP may be re-computed to avoid accessing a cached result (which can be inefficient due to memory bandwidth bottlenecks). This is typically done in backward passes in AI training.
[^124]: One might wish to estimate a chip’s theoretical performance rather than taking the vendor’s word for it because a hardware vendor could hypothetically be colluding with the Prover, especially if both are of the same country.
[^125]: A chip’s power consumption consists of the power used to (i) execute operations and (ii) communicate with memory or I/O, as well as (iii) the static power use or power leakage. (i) is affected by factors including the type of operation (e.g., bit-width) and (to a lesser extent) the distribution of numbers (He, [2024](https://arxiv.org/html/2507.15916v2#bib.bib86)), (ii) is affected by factors including the workload’s arithmetic intensity, and (iii) is affected by factors including the availability and use of clock gating and power gating to reduce the power consumption of unused modules of a chip (Agnes Shiny et al., [2019](https://arxiv.org/html/2507.15916v2#bib.bib3)). Additionally, as a chip’s clock speed increases (at least, if the memory clock increases equally), OP/s rise linearly, while power usage rises non-linearly (Fatahalian and Olukotun, [2023](https://arxiv.org/html/2507.15916v2#bib.bib67)). The maximum clock speed (before excess wear) is affected by power throttling and thermal throttling, which depend on the cooling technology used and even environmental temperature; when training Llama 3, Meta “noted a diurnal 1-2% throughput variation based on time-of-day” (Llama Team, [2024](https://arxiv.org/html/2507.15916v2#bib.bib129)). Power consumption also varies non-linearly with process technology (Micron Technology, [2018](https://arxiv.org/html/2507.15916v2#bib.bib134)). Equipment beyond AI chips adds further complexity, though as mentioned this complexity could be avoided by only measuring AI chips’ power draw.
[^126]: A given workload might be definable with a specification such as “transformer inference with INT8 operations,” or perhaps a greater level of granularity would be needed. One approach to modeling an AI chip’s energy efficiency (for a given chip) could be to assume the user seeks to maximize model OP/s for the workload subject to the constraints of a maximum power draw and a maximum temperature, which are determined by available cooling and electrical infrastructure and the hardware’s resilience to high temperatures and power (and perhaps ambient temperature). One could further assume that, without (significantly) lowering model OP/s from this constrained maximum, a user would then take nearly all opportunities to reduce power leakage. Empirical tests could determine the parameters of these relationships (ideally with precautions against backdoors: [Appendix A.1](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx1 "A.1 Full-stack Security for Technical Verification Mechanisms’ Implementation ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")), though industry standards could be a rough substitute). Some actors might require technical assistance to meet the assumption of approximately maximizing model OP/s under constraints; this could be provided, potentially for compensation (as better energy efficiency means lower power bills). Still, variation in energy efficiency introduced through engineering introduces uncertainty. With uncertainty, the mentioned assumptions, experimental results, and live measurements (perhaps with some refinements) would collectively determine all the variables previously mentioned to relate the power draw and OP/s (e.g., assuming a workload determines the type of operation and the arithmetic intensity, assumptions and measurements determine the clock speed(s) and power leakage). However, a Prover may have legitimate reasons not to maximize OP/s under power and temperature constraints; certain uses may demand sacrificing throughput to lower latency. Hopefully such use-cases would either not significantly affect energy efficiency, be identifiable from certain measurements, or be otherwise verifiable (e.g., consumer-end verification of low latency).
[^127]: As one wrinkle (to illustrate using simplified numbers), suppose one server could do 100 FLOP for workload A or 200 FLOP for workload B, while a second server could do 200 FLOP for workload A or 100 FLOP for workload B. A Prover could then claim to have chosen the 100-FLOP option with each server while really choosing each 200-FLOP option. The Prover would then be able to account for the two 100-FLOP workloads, while having done just as many operations secretly. More abstractly, some sets of selections from a “menu of options” might be pareto-inefficient, allowing a Prover to understate their number of operations done. This could be countered by demanding (approximately) pareto-efficient selections, which is incentive-compatible.
[^128]: This is closely related to the efficiency problem of achieving high MFU, so there is presumably substantial applicable work and expertise on this problem at AI labs.
[^129]: This has the political downsides (and upsides) of being technology transfer, but that could be mitigated by financial compensation and by the fact that the efficiency gains are quite limited in principle; at least for AI training, MFU around 50% of the theoretical upper bound of 100% is already commonly achieved (Clark, [2024](https://arxiv.org/html/2507.15916v2#bib.bib37)). Meanwhile, for AI inference, HFU=MFU by default, making option (B) more easily applicable.
[^130]: If one only measures the power draw of AI chips, then one “only” needs to determine the AI chips’ energy efficiency to verify the operations done. As more other equipment is brought into the bounds of power measurement (e.g., CPUs, NVLink chips, cooling infrastructure), the energy consumption of this other equipment needs to be determined and subtracted from the total energy consumption to derive the AI chips’ energy consumption, introducing error.
[^131]: For example, measuring an AI data center’s whole power draw may be doable with a few standard electricity meters, while precisely measuring individual AI chips’ power consumption may require altering a server’s design to introduce interposers that sit between AI chips and power supply units—one for each of thousands of AI chips.
[^132]: Measurement devices could be made to be (or installed in containers that are) tamper-evident (and then inspected for evidence of tampering) or tamper-proof, the latter option being much more technically challenging (Aarne et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib2); Kulp et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib121)). Tamper-evident cameras ([Section 4.4](https://arxiv.org/html/2507.15916v2#Sx5.SSx4 "4.4 Supplementary Verification Mechanisms ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) would also help.
[^133]: Inspections may also be needed to ensure that e.g., a data center or server rack does not have hidden power cables, nor unmetered backup generators. Measured power draw could be sanity checked based on observations or other measurements of cooling infrastructure, electrical infrastructure, and heat emissions.
[^134]: While remote transmission could raise security issues, the Verifier could take the same approach as the IAEA: having inspectors check device logs on site, under the supervision of the facility owner (Baker, [2023](https://arxiv.org/html/2507.15916v2#bib.bib13)). Also drawing from the IAEA, the data center owner could be allowed to inspect a random sample of measurement devices, to ensure they do not have unauthorized functions.
[^135]: The SEC reports awarding $600 million in fines to whistleblowers as part of its whistleblower reward program in 2023, rewards being 10-30% the value of fines the whistleblower tip contributed to (U.S. Securities and Exchange Commission, Office of the Whistleblower, [2023](https://arxiv.org/html/2507.15916v2#bib.bib216)).
[^136]: Further anonymity protections could include: ensuring all employees have equal-length visits to the Verifier rather than keeping whistleblowers longer, and strong internal processes for protecting confidentiality.
[^137]: Sending _all_ employees on such visits may be especially impractical for larger companies in the AI supply chain; TSMC and AWS, for instance, have around 100,000 employees each ([StockAnalysis,](https://arxiv.org/html/2507.15916v2#bib.bib195) ; Gardizy, [2024](https://arxiv.org/html/2507.15916v2#bib.bib71)). The number of visits could be greatly reduced by limiting visits to primarily the most relevant employees, though this could mean reduced coverage. Still, for cases where violations are known to non-closely-watched employees, more established communication lines like Tor or other anonymous internet communication may also be viable.
[^138]: This raises the problem of potential falsehoods about who the relevant employees are. The Verifier could verify the identities of relevant employees through methods including open-source intelligence (e.g., publication record, social media), checking whether an individual has the knowledge expected of their role, and checking whether the claimed number of employees is approximately standard for the role. Regardless, if a Prover sends forward a group that is incomplete or has impostors, the group members could then blow the whistle on the deception.
[^139]: This could work as follows. First, the Prover uploads some information, such as training code and information on compute allocation across projects, to a personal computer. (Other information, like model weights, would typically require a computing cluster rather than a personal computer.) Then, a Prover representative physically oversees the use of this computer to ensure this information is not used for any purposes beyond authorized ones. These authorized uses would be: (i) authorized Prover employees may view claims related to their work, and (ii) the Verifier may extract a cryptographic hash to check that the Prover’s claims here match their claims elsewhere. To implement (i), a Prover employee could review (selected, relevant-to-the-employee) declarations, under the supervision of a representative of both the Prover and the Verifier—with both of these representatives having the computer’s monitor and keyboard out of view. With an appropriate room layout and joint physical security, this arrangement could provide several assurances: (i) the Verifier is assured that the employee reviews the code, (ii) the Prover is assured that the Verifier does not view private declarations, and (iii) the Verifier is assured that the Prover does not view the employee’s screen (to make employee intimidation harder).
[^140]: As one example promoter of a pro-whistleblower culture, industry and political leaders could make statements stressing the social value of compliance and the legitimacy of whistleblowers.
[^141]: Financial rewards for successful whistleblowers could incentivize employees to make fake allegations against their employers. Still, this problem could be mitigated through selective application of rewards, such as rewarding whistleblowers only when their allegations can be independently confirmed.
[^142]: Violations that involve software spoofs would likely require AI researchers and engineers, potentially including ones with expertise in low-level implementation. If a Prover sought to circumvent on- or off-chip verification mechanisms at the hardware level, they would likely need hardware security researchers. They may also need accomplices in data centers to do physical tampering, or accomplices earlier in the AI chip supply chain to plant hardware backdoors ([Section 4.3](https://arxiv.org/html/2507.15916v2#Sx5.SSx3 "4.3 Personnel-Based Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")). It may be feasible for a Verifier to identify most leading hardware security researchers and give them an opportunity to whistleblow; one hardware security academic we interviewed expressed that there are maybe a handful of groups that do very good offensive (hardware) security research in the United States, and that they know each other (Interview #2, 2024). This interviewee also estimated that there are 100-200 hardware security researchers in the United States, if one counts all the graduate students and researchers. Another academic we interviewed estimated that there are “at least” 200 hardware security researchers in Europe, only counting “serious researchers” rather than ones who tried hardware security one time (Interview #11, 2024). This academic also explained that there are significant hardware security research groups in East Asia, Europe, and the United States.
[^143]: For example, if one expert’s instance is already “busy” processing many inputs, additional inputs might be routed to other available experts for speed, even if they would be best handled by the “busy” expert.
[^144]: To see this, consider an example of addition of integers in the range -128 to 127, assuming the overflow behavior is saturation (“maxing out”). Then (127 + 50) + (-50) would be computed as 127 + (-50) = 77, while 127 + (50 + (-50)) would have the different result 127.
[^145]: E.g., facilitating multiple training runs or epochs on the same data and facilitating debugging.
[^146]: As a technical implementation in the context of large-scale AI deployment, the Prover could store only data with a hash in a certain range (the hash being e.g., the Merkle root of a (prompt, logits, model) tuple). However, this scheme could be foiled by a Prover e.g., making small perturbations to the logits or to a continuous input (e.g., an image input) until the Prover finds values that produce a desired hash; that would enable an arbitrary set of (prompt, logits, model) tuples to look like a small, random sample of tuples. To counter this, exact replication ([Appendix A.9](https://arxiv.org/html/2507.15916v2#Ax1.SSx1.SSSx9 "A.9 Deterministic Replication of Neural Network Inference ‣ A. Implementation Analyses ‣ Appendices ‣ Verifying International Agreements on AI")) or perhaps precisely modeled non-determinism would catch sufficiently large perturbations. Still, there may be input perturbations that cause no change to the output (this is necessarily true when the input space is larger than the output space, and perhaps such perturbations can be made easier to find by an adversarially trained model); ruling out such perturbations may require further constraints on the Prover and testing. (On the other hand, small input perturbations may be infeasible for text inputs represented as discrete tokens.)
[^147]: However, “live” sampling might allow a Prover to manipulate the sample by changing their inference in response to which queries are sampled (e.g., perhaps generating duplicates until the first duplicate in a set is sampled).
[^148]: An H100 GPU (conservatively assuming 100% utilization, running a 70B-parameter dense model, with 2-byte inputs plus 2-byte outputs) can process data at up to the FLOP per second \* data per forward pass / FLOP per forward pass, or $1.98\text{e}15\cdot\frac{2+2}{2\cdot 70\text{e}9}\approx 57\text{ KB/s}$, while PCIe Gen5 can transfer data at 128 GB/s (NVIDIA, [b](https://arxiv.org/html/2507.15916v2#bib.bib150)), and some PCIe Gen4 SSDs read and write data at around 7 GB/s (Burek, [2024](https://arxiv.org/html/2507.15916v2#bib.bib28)). This back-of-the-envelope calculation suggests the latency overhead from copying data to an SSD would be on the order of 0.001% (assuming the lower SSD rate of 7 GB/s).
[^149]: PCIe Gen4 SSDs have storage capacities such as 2 TB for $90 (Burek, [2024](https://arxiv.org/html/2507.15916v2#bib.bib28)). If they were to store data for a month and be amortized over a year, the cost would be $\frac{90}{2\text{e}12\cdot 12}=3.75\text{e-}12\text{ \$/byte}$, while the cost of _processing_ a byte with a large AI model (70B-parameter dense model, with 2-byte data, with an H100 GPU at a conservatively assumed 100% utilization and for $2/hr) (GPU Utils, [2023](https://arxiv.org/html/2507.15916v2#bib.bib81); Clark, [2024](https://arxiv.org/html/2507.15916v2#bib.bib37)) would be $70\text{e}9\cdot 2\cdot\frac{2}{1.98\text{e}15\cdot 60\cdot 60}\cdot\frac{1}{2}=1.96\text{e-}8\text{ \$/byte}$, implying a storage cost overhead on the order of 0.01%.
[^150]: “Large scale AI training and deployment is highly resource intensive, often requiring thousands of specialized chips in a high performance cluster hosted in a large data center consuming large amounts of power” (Sastry et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib178)).
[^151]: Similar datasets, such as large text corpuses or data from human feedback, are often used for smaller-scale AI development and deployment.
[^152]: Similar algorithms can be used for AI development and deployment of varying scales, though leading AI labs increasingly use proprietary algorithms primarily for large-scale AI.
[^153]: AI technical staff of course do not spend all of their time or energy on their AI work, and many people can gain AI expertise.
[^154]: Though electric power of course has many uses, the energy density of typical AI data centers is unusually high. Relatedly, large AI data centers often have dedicated electrical substations (Pilz and Heim, [2023](https://arxiv.org/html/2507.15916v2#bib.bib165)) or adjacent power plants (U.S. Department of Energy, Office of Nuclear Energy, [2025](https://arxiv.org/html/2507.15916v2#bib.bib214)). However, AI compute could be decentralized to reduce its energy density.
[^155]: Generating large amounts of electricity requires power plants, though transporting electricity does not require as much infrastructure, potentially making it challenging to trace power plants to all their uses.
[^156]: Some data centers use large amounts of water for cooling, while others do not. “On average, evaporative cooling systems use approximately 1,800 to 2,900 liters of water per megawatt per hour,” but an alternative cooling method—the use of “chillers”—“obviates the need for water, \[though\] it demands substantial electrical power” (Pilz and Heim, [2023](https://arxiv.org/html/2507.15916v2#bib.bib165)).
[^157]: For example, whistleblowers, interviews, and intelligence agencies might uncover merely suggestive evidence, and some technical tests may reveal anomalies that have legitimate explanations.
[^158]: One study writes: “Perhaps the most important form of co-operation is a continuing process of consultation among the parties, institutionalized in a consultative commission made up of highly qualified experts. The purpose of such a commission must be entirely on the side of preserving agreements and building confidence by dealing promptly and objectively with any ambiguities, misunderstandings or technical violations which arise” (Krass, [1985](https://arxiv.org/html/2507.15916v2#bib.bib120)).
[^159]: This could involve temporarily increasing the rate of random sampling, e.g., for selecting interviewees, AI data centers, AI chips, or workload portions to inspect. A focused inspection could also involve dedicating more analysts, intelligence agents, satellites, or computational power to the suspect area, including by running new technical tests. The IAEA has a similar practice; their common response to some ambiguous findings is “to re-establish the physical inventory” of a nuclear facility, “which is time consuming and costly” (International Atomic Energy Agency, [2014](https://arxiv.org/html/2507.15916v2#bib.bib105))
[^160]: Minimally, compliance tests would output only a yes/no determination of compliance, to minimize their potential for leaking sensitive information. The amount of information they output could be increased to gain more clarity at the expense of potentially leaking more information; there is a large gap between revealing only 1 bit and revealing terabytes, which may be needed to encode large model weights or full datasets. Still, intermediate sizes of outputs (e.g., kilobytes) would have downsides: potentially leaking algorithms or small amounts of training or usage data.
[^161]: In practice, presumably any subgoal will not be completed perfectly, so the conclusion of compliance would follow probabilistically (e.g., one might conclude there is a 90% probability that an actor is compliant).
[^162]: These other potential verification systems were: verification done only via whistleblowers, verification done only by intelligence agencies, and verification done using operations accounting but not on-chip mechanisms.
[^163]: We also considered an additional aspect of avoiding excess complexity, which may be clearest by example. Suppose the last two subgoals in our verification framework, 2.A and 2.B, were merged into a single subgoal. Then the mechanisms for this merged subgoal would be every possible pairing of a Subgoal 2.A mechanism with a Subgoal 2.B mechanism. This would be an unnecessarily long and complicated list of mechanisms. We sought to avoid such complexity where feasible by factoring a verification subgoal into more or different subgoals.
[^164]: For most verification mechanisms we consider, parties can make the mechanism detect any violation more quickly by increasing the frequency at which declarations are reported and checked for compliance. For example, declarations could hypothetically be submitted and verified every few months, or every few days. Thus, parties can typically make a verification mechanism X times more timely by accepting approximately X times greater costs. However, past some point, further speed may be of limited value; for example, if requests for clarification and political deliberations would take days, perhaps it would not be a priority to speed up verification by a few hours. Still, some mechanisms such as tamper-proof, compliance-locked AI chips or server enclosures ([Section 4.1.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx1.SSSx1 "4.1.1 Mechanisms ‣ 4.1 On-Chip Verification Layer ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI"); [Section 4.2.1](https://arxiv.org/html/2507.15916v2#Sx5.SSx2.SSSx1 "4.2.1 Mechanisms ‣ 4.2 Off-Chip Verification Layers ‣ 4. Verification Mechanisms and Layers ‣ Verifying International Agreements on AI")) would hypothetically guarantee that a violation is not done at all, making the question of detection speed unnecessary.
[^165]: To assess these properties, we considered, respectively: how a Prover might seek to circumvent a verification mechanism; how legitimate variation or randomness might trigger a verification mechanism, what information and exploitable control points would be transferred to the Verifier; the amount of R&D and physical infrastructure development needed; and the costs associated with all major components of the mechanism (often estimated with a back-of-the-envelope calculation or prior empirical results).
[^166]: Recall our criteria: “R&D problems that are relatively challenging, have been subject to relatively little work compared to their difficulty, could play major roles in verification, and would not create highly abusable tech”
[^167]: Edge cases might include: older AI chips (e.g., A100s), high-end consumer GPUs (e.g., RTX 5090s), CPUs with powerful AI modules, and smaller data centers.
[^168]: This is counting theoretical INT8 operations per second without sparsity.
[^169]: A back-of-the-envelope estimate suggests a 500,000x compute overhead. Sun, et al. (Sun et al., [2024a](https://arxiv.org/html/2507.15916v2#bib.bib196)) report a prover time of 803 seconds per inference verification for Llama-13B, using an A100 with 40GB of memory. Since this implementation “fully leverag\[es\] parallel computing resources” and uses the majority of available memory, the throughput of this method would be around 1 token per 803 seconds. In contrast, one benchmark of running ordinary (non-ZK) inference on the same model with the same GPU reports a throughput of 668 tokens per second (Schmid, [2023](https://arxiv.org/html/2507.15916v2#bib.bib180)): approximately 500,000 times greater.
[^170]: Prior work in ZK-SNARKs (Chen et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib33); Waiwitlikhit et al., [2024](https://arxiv.org/html/2507.15916v2#bib.bib222); Sun et al., [2024a](https://arxiv.org/html/2507.15916v2#bib.bib196)) all does not preserve the privacy of AI model architectures, which AI developers often treat as highly sensitive IP.

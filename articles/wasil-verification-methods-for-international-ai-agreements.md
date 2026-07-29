---
title: "Verification methods for international AI agreements"
author:
  - "Akash R. Wasil"
  - "Tom Reed"
  - "Jack William Miller"
  - "Peter Barnett"
source_url: "https://arxiv.org/abs/2408.16074"
published: 2024-08-28
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

###### Abstract

What techniques can be used to verify compliance with international agreements about advanced AI development? In this paper, we examine 10 verification methods that could detect two types of potential violations: unauthorized AI training (e.g., training runs above a certain FLOP threshold) and unauthorized data centers. We divide the verification methods into three categories: (a) national technical means (methods requiring minimal or no access from suspected non-compliant nations), (b) access-dependent methods (methods that require approval from the nation suspected of unauthorized activities), and (c) hardware-dependent methods (methods that require rules around advanced hardware). For each verification method, we provide a description, historical precedents, and possible evasion techniques. We conclude by offering recommendations for future work related to the verification and enforcement of international AI governance agreements.

Verification methods for international AI agreements

Akash R. Wasil1,2, Tom Reed2, Jack William Miller2, Peter Barnett3

1Georgetown University (aw1404@georgetown.edu)

2University of Cambridge, ERA AI Fellowship

3Independent

## Executive Summary

Efforts to maximize the benefits and minimize the global security risks of advanced AI may lead to international agreements. This paper outlines methods that could be used to verify compliance with such agreements. The verification methods we cover are focused on detecting two potential violations:

Violations to verify • Unauthorized AI development (for example, AI development that goes beyond a FLOP threshold set by an international agreement, or the execution of a training run that has not received a license). • Unauthorized data centers (for example, data centers that go beyond a maximum computing capacity limit or networking limit set by an international agreement).

We identify 10 verification methods and divide them into three categories:

1.  1.
    
    National technical means. Methods that can be used by nations unilaterally.
    
2.  2.
    
    Access-dependent methods. Methods that require a nation to grant access to national or international inspectors
    
3.  3.
    
    Hardware-dependent methods. Methods that require agreements pertaining to advanced hardware
    

National technical means 1. Remote sensing: Detect unauthorized data centers and semiconductor manufacturing via visual and thermal signatures. 2. Whistleblowers: Incentivize insiders to report non-compliance. 3. Energy monitoring: Detect power consumption patterns that suggest the potential presence of large GPU clusters. 4. Customs data analysis: Track the movement of critical AI hardware and raw materials. 5. Financial intelligence: Monitor large financial transactions related to AI development.

Access-dependent methods 1. Data center inspections: Conduct inspections of sites to assess the size of a data center, verify compliance with hardware agreements, and verify compliance with other safety and security agreements. 2. Semiconductor manufacturing facility inspections: Conduct inspections of sites to determine the quantity of chip production and verify that chip production conforms to any agreements around advanced hardware. 3. AI developer inspections: Conduct inspections of AI development facilities via interviews, document and training transcript audits, and potential code reviews.

Hardware-dependent methods 1. Chip location tracking: Automatic location tracking of advanced AI chips. 2. Chip-based reporting: Automatic notification if chips are used for unauthorized purposes.

### Limitations and considerations

The verification methods we propose have some limitations, and there are many complicated national and international considerations that would influence if and how they are implemented. Some of these include:

-   •
    
    Invasiveness: Some methods (especially on-site inspections) may be seen as intrusive and could raise concerns about privacy and sovereignty. Several factors could influence a nation’s willingness to accept invasive measures (e.g., the amount of international tension or distrust between nations, the degree to which nations are concerned about risks from advanced AI, the exact types of risks that nations find most concerning.)
    
-   •
    
    Imperfect detection: No single method is foolproof. However, the combination of multiple methods could create a “Swiss chees” model, where the weaknesses of one method are covered by the strengths of others.
    
-   •
    
    Developmental stage: Some methods (especially the hardware-dependent ones) may require additional R&D. Furthermore, unlike methods that have been used for decades in other areas, the real-world effectiveness of some hardware-dependent methods has not yet been determined.
    

### Future Directions

Our work provides a foundation for discussions on AI governance verification, but several key areas require further research:

-   •
    
    Red-teaming exercises for verification regimes. Future work could examine how adversaries might attempt to circumvent a verification regime, describe potential evasion methods, and develop robust countermeasures to improve the effectiveness of the verification regime.
    
-   •
    
    Design of international AI governance institutions. Future work could examine how international AI governance institutions should be designed, potentially drawing lessons from existing international bodies. Such work could explore questions such as: (a) what specific powers should be granted to the international institution, (b) how the institution should make core decisions, (c) how power is distributed between nations, and (d) how to handle potential violations or instances of non-compliance.
    
-   •
    
    Enforcement strategies. Future work could examine what kinds of responses could be issued if non-compliance is discovered. This includes examining how such responses can be proportionate to the severity of the violation.
    
-   •
    
    Development of tamper-proof and privacy-preserving hardware-enabled verification mechanisms. Future R&D efforts could improve the effectiveness, feasibility, robustness, or desirability of various hardware-dependent verification methods.
    

## Introduction

‘

![Refer to caption](https://arxiv.org/html/2408.16074v1/x1.png)

Figure 1: Verification methods can help detect unauthorized training runs and unauthorized data centers. \* For data center inspections to be able to detect unauthorised training runs, it is likely that hardware requirements around chips with activity logs will be needed in some form.

The development of advanced artificial intelligence poses major global security risks. Significant threats include the potential for pervasive surveillance, the development of autonomous weapons, and misuse by malicious actors. Some of the most concerning risks stem from loss of control and misalignment (Bengio et al. [2024](https://arxiv.org/html/2408.16074v2#bib.bib7); Bostrom [2014](https://arxiv.org/html/2408.16074v2#bib.bib10); Ngo, Chan, and Mindermann [2022](https://arxiv.org/html/2408.16074v2#bib.bib33)). A sufficiently powerful misaligned AI system could autonomously act against human interests following an objective function which does not capture human values (Pan, Bhatia, and Steinhardt [2022](https://arxiv.org/html/2408.16074v2#bib.bib39)). There is a great amount of uncertainty around what kinds of safeguards will be necessary to prevent misalignment (Gabriel [2020](https://arxiv.org/html/2408.16074v2#bib.bib19)). Many experts believe that safeguards may require many years or decades of concerted research effort.

AI risks are exacerbated by race dynamics — companies are rapidly progressing in the hope of being the first to develop artificial superintelligence (Armstrong, Bostrom, and Shulman [2016](https://arxiv.org/html/2408.16074v2#bib.bib4); Hogarth [2023](https://arxiv.org/html/2408.16074v2#bib.bib22)). In the context of an AI race, nations may not have sufficient time to carefully and cautiously develop or evaluate such safeguards.

International agreements could help avoid or mitigate a race between nations. Even though governments are at early stages of understanding AI risks, key figures in the United States and China have already acknowledged concerns about AI global security risks and expressed interest in global governance approaches (Wasil and Durgin [2024](https://arxiv.org/html/2408.16074v2#bib.bib59)). As governments become more aware of AI risks, they may become interested in global governance strategies that curb these race dynamics. Alternatively, nations might agree to cede the development of advanced AI to a joint international project. The international institution would be responsible for carrying out certain forms of advanced AI development, which would be illegal outside the context of this secure joint project (Hogarth [2023](https://arxiv.org/html/2408.16074v2#bib.bib22)).

International agreements require verification. Nations might be much more likely to form international agreements around rules that they can reliably verify (Fearon [1995](https://arxiv.org/html/2408.16074v2#bib.bib16); Baker [2023](https://arxiv.org/html/2408.16074v2#bib.bib5)). By “verify”, we mean that nations would be able to detect non-compliance with agreements. Ideally, verification methods (methods used to detect non-compliance) would provide early and reliable warning signs. “Early”, in that non-compliance could be detected relatively quickly (before a nation achieved any meaningful unauthorized advantage in advanced AI development), and “reliable” in that non-compliance would be very likely to be detected.[^1]

In this paper, we provide an overview of verification methods for international AI agreements. We begin by outlining the potential targets such an international agreement. We then outline 10 verification methods. For each verification method, we provide a description, some precedents for how the verification method has been used in the past, and an example evasion technique to illustrate how an adversary could attempt to circumvent the method. Finally, we discuss limitations of the verification methods and directions for future work.[^2]

## What to verify: Unauthorized AI development and unauthorized data centers

An international agreement on AI could take many forms, depending on how the technology and its associated risks evolve. In scenarios where continued AI development leads to substantial acknowledged global security risks, we anticipate that verification methods would need to be capable of detecting two primary types of potential violations:

1.  1.
    
    Unauthorized data centers. International governance of AI could plausibly set restrictions on the form, size, quantity, and location of large-scale computing facilities. Verification methods would therefore be needed to detect the construction or operation of data centers that violate these agreed-upon standards.
    
2.  2.
    
    Unauthorized training runs. An effective international system for governing AI would likely include restrictions on the scale and characteristics of AI development. Beyond detecting unauthorised data centers, methods to verify that known data centers are compliant with agreed-upon standards would also be necessary. For example, an agreement might stipulate that AI training runs should not exceed a certain FLOP[^3] threshold (Heim [2024](https://arxiv.org/html/2408.16074v2#bib.bib20)), use specific types of training data, or employ certain training algorithms. Verification methods would be needed to detect whether AI development activities occurring within facilities violate such standards.
    

## Methodology

Our process for compiling verification methods involved a few steps: (a) reviewing relevant literature on AI verification and international AI governance, (b) reviewing relevant literature on verification methods for agreements in other fields (e.g., nuclear security, biosecurity, arms control), and (c) conducting informal interviews with experts in technical AI governance. Through this process, we identified 10 verification methods. For each verification method, we examined its application in other fields to inform our description of how the method could be used in the context of AI disagreements and to inform our section about the method’s precedent in other fields. We also grouped the methods into categories based on the circumstances in which they could be implemented: universally (national technical means), only in cases where a nation provides access (access-dependent), or only in cases in which nations have agreed to rules around the design of advanced hardware (hardware-dependent). Our process is not intended to be systematic and our work should not be considered a comprehensive overview of verification methods. Rather, it is meant to serve as an initial step toward better understanding a set of specific verification methods and their limitations.

## Verification methods

Defining “verification method”. In this piece, a verification method is a method that could directly be used to detect defection or non-compliance from an agreement. That is, we assume an adversarial setup in which one party is explicitly attempting to “hide” unauthorized data centers or unauthorized AI training.

Categorizing verification methods. Some verification methods can be implemented without any buy-in from nations suspected of non-compliance, some verification methods require cooperation or authorization from the suspected nation, and some verification methods require cooperation from hardware manufacturers. These distinctions are useful for determining which verification methods might be feasible under various circumstances.

Thus, we divide verification methods into three categories: (a) national technical means (methods that can be implemented without the approval of individual nations)[^4], (b) access-dependent verification methods (methods that require international agreements that include the suspected nation), and (c) hardware-dependent verification methods (methods that require international agreements that include major hardware manufacturers). See [Figure 1](https://arxiv.org/html/2408.16074v2#Sx2.F1 "In Introduction ‣ Verification methods for international AI agreements") and [Figure 6](https://arxiv.org/html/2408.16074v2#A3.F6 "In Appendix C List of verification methods for international AI agreements ‣ Verification methods for international AI agreements") for a visual summary of the verification methods.

### National Technical Means

#### REMOTE SENSING

Remote sensing techniques, including satellite imagery and other forms of aerial observation, can detect potential undeclared data centers using visual, infrared and other electromagnetic signatures. Advanced commercial satellites, which can achieve sub-meter resolutions (Statista [2022](https://arxiv.org/html/2408.16074v2#bib.bib49)), could identify specialized cooling units and the movement of computing equipment.

Infrared imaging is particularly promising for detecting concealed data centers, as GPUs and other computing hardware generate significant heat signatures (Yuan et al. [2023](https://arxiv.org/html/2408.16074v2#bib.bib61)) that are difficult to mask. This could reveal large-scale computing facilities even when visually concealed.

Recent advancements in machine learning have further enhanced remote sensing capabilities for verification. Drawing from nuclear non-proliferation efforts (Rutkowski and Niemeyer [2020](https://arxiv.org/html/2408.16074v2#bib.bib44)), AI-driven approaches such as supervised and unsupervised classification techniques can be applied to remotely sensed data. These methods could significantly improve the identification and monitoring of potential AI development facilities without requiring on-site access, bolstering national technical means for AI governance verification.

While remote sensing can be used without formal agreements, international commitments similar to START could enhance its effectiveness by ensuring non-interference and facilitating data exchange (U.S. Department of State [2023](https://arxiv.org/html/2408.16074v2#bib.bib54)).

Precedent. The International Atomic Energy Agency (IAEA) routinely employs satellite imagery to evaluate state-provided information about nuclear activities and to plan inspections (Baker [2023](https://arxiv.org/html/2408.16074v2#bib.bib5)).

Non-state actors have also demonstrated the power of commercial imagery; for example, the Open Nuclear Network used it to reveal maintenance and possible expansion at China’s Lop Nur nuclear testing site, including new tunneling and drilling activities (Open Nuclear Network [2024](https://arxiv.org/html/2408.16074v2#bib.bib36)).

#### WHISTLEBLOWERS

Insiders with knowledge of undeclared facilities or operations could provide valuable information not detectable through external means. Potential whistleblowers include employees, contractors, or local residents aware of suspicious activities. Governments could incentivize whistleblowing by:

1.  1.
    
    Establishing robust protection frameworks specifically for AI and technology sectors;
    
2.  2.
    
    Offering financial incentives for verified information;
    
3.  3.
    
    Creating secure, anonymous reporting channels;
    
4.  4.
    
    Providing legal support and job protection;
    
5.  5.
    
    Developing international cooperation for cross-border whistleblower protection (Loyens and Vandekerckhove [2018](https://arxiv.org/html/2408.16074v2#bib.bib29)).
    

It is important to note that incentivization alone may not be sufficient to ensure the effectiveness of whistleblower schemes, given that determined adversaries might attempt to physically or digitally block employees from contacting a verifying authority.

One possible solution to this limitation is to implement regular in-person communication with employees, such as through semi-structured interviews (Wasil et al. [2024a](https://arxiv.org/html/2408.16074v2#bib.bib57)).[^5]

Precedent. The SEC Whistleblower Program, established under the Dodd-Frank Act in 2010, created a system for reporting securities violations (U.S. Securities and Exchange Commission [2017](https://arxiv.org/html/2408.16074v2#bib.bib56)). It includes strong protections and incentives like monetary awards for whistleblowers, who are entitled to anywhere between 10-30% of the sanctions resulting from their information (Reuters [2018](https://arxiv.org/html/2408.16074v2#bib.bib43)). For example, in 2016, three whistleblowers revealed Merrill Lynch’s misuse of up to $58 billion daily in customer funds, leading to a $415 million settlement and $83 million in whistleblower awards (Securities and Exchange Commission (2016) [SEC](https://arxiv.org/html/2408.16074v2#bib.bib46); Reuters [2018](https://arxiv.org/html/2408.16074v2#bib.bib43)).

#### ENERGY MONITORING

Unauthorized data centers or the use of data centers for unauthorized training runs could be detected by monitoring energy consumption, either passively (through grid data obtained via espionage), or actively (using devices to measure grid activity).

If the total amount of energy reaching a data center can be measured with reasonable accuracy, it should be possible to convert the energy estimate into a reasonable approximation of the number of FLOPs completed by that facility (Desislavov, Martínez-Plumed, and Hernández-Orallo [2021](https://arxiv.org/html/2408.16074v2#bib.bib15)). Using the FLOP/s, we could ascertain whether the facility is at an unauthorized size. However, these coarse-grained measurements may only be capable of detecting large-scale violations, and further research is needed to understand how such measurements can be more accurately translated into relevant units like FLOPs. More precise methods of energy monitoring may be necessary for detecting smaller-scale violations or unauthorized training runs.

Precedent. Economists use energy monitoring to verify economic data. For example, economists have used discrepancies between reported GDP growth and energy consumption to suggest exaggerated growth figures in China (Owyang and Shell [2017](https://arxiv.org/html/2408.16074v2#bib.bib38)). This principle could be applied to detect unauthorized data centers, given the direct relationship between energy consumption and FLOPS.

#### CUSTOMS DATA ANALYSIS

Governments can use customs data to track the movement of key components for large-scale AI computing facilities. Import and export records could be analyzed to identify unusual or unexplained patterns in the movement of critical hardware, equipment or raw materials. A sudden surge in imports of high-performance GPUs or other critical components to a specific region of concern, far exceeding the known requirements of declared facilities in that region, would indicate non-compliance.

Precedent. The U.S. government’s End-Use Monitoring (EUM) programs, particularly the Blue Lantern program for direct commercial sales, provide a robust precedent for tracking and verifying the use of sensitive technologies (U.S. Department of State [2021](https://arxiv.org/html/2408.16074v2#bib.bib53)). Under the Blue Lantern program, the Department of State conducts pre-license, post-license/pre-shipment, and post-shipment checks to verify the legitimacy of proposed transactions and ensure compliance with use, transfer, and security requirements. This program has been successful in promoting understanding of U.S. defense trade controls, building mutual confidence among stakeholders, mitigating risks of diversion and unauthorized use, and uncovering violations of the Arms Export Control Act. A similar approach could be adapted for monitoring the movement and use of critical AI hardware components in countries at different stages of the chip supply chain.

#### FINANCIAL INTELLIGENCE

Governments could track suspicious financial transactions relating to the purchase of important components of AI development. Financial institutions could be required to flag large or unusual purchases of specialized AI hardware, monitor transactions to known AI chip manufacturers, and cross-reference financial data with customs information.

Precedent. In the US, the Financial Crimes Enforcement Network (FinCEN) uses the Suspicious Activity Report (SAR) system and FinCEN Exchange, a public-private partnership, to combat money laundering, terrorism financing, and organised crime (Financial Crimes Enforcement Network [2024](https://arxiv.org/html/2408.16074v2#bib.bib18)).

In the early 2010s, an SAR filed by a bank led to the discovery of a complex international bribery scheme. The case resulted in multiple arrests and the seizure of over $100 million in criminal proceeds (Financial Crimes Enforcement Network [2011](https://arxiv.org/html/2408.16074v2#bib.bib17)). This demonstrates how financial intelligence can uncover sophisticated international financial crimes, potentially adaptable to detecting undeclared AI development activities.

![Refer to caption](https://arxiv.org/html/2408.16074v1/x2.png)

Figure 2: Summary of evasion techniques to avoid verification methods under national technical means.

#### KEY TAKEAWAYS

National technical means offer a valuable starting point for verifying compliance with AI governance agreements. Nations already have extensive experience using these methods to verify compliance with other kinds of international agreements. These methods can plausibly be used to detect large-scale AI infrastructure and unusual patterns in energy consumption, hardware imports, and financial transactions. However, these methods have important limitations. In particular, adversaries could attempt to disguise data centers as other high-energy facilities like power plants, or when compute is distributed across multiple smaller sites.

### Access-dependent verification methods

#### ON-SITE INSPECTIONS OF DATA CENTERS

On-site inspections involve physical visits to declared data centers to verify compliance with agreements on computing power. These inspections would focus on several aspects, including (but not limited to):

-   •
    
    Chip identifiers. AI-capable chips could be required to have unique identifiers (Aarne, Fist, and Withers [2024](https://arxiv.org/html/2408.16074v2#bib.bib1)). Inspectors could catalog these identifiers to ensure they match declared inventories.
    
-   •
    
    Chip activity logs. Require chips to have activity logs that inspectors can analyze to verify that: (1) chips are being used in accordance with their declared purposes and within agreed-upon limits, and (2) only licensed code is being executed on the chips (Shavit [2023](https://arxiv.org/html/2408.16074v2#bib.bib47)).
    
-   •
    
    FLOP/s limit compliance. Ensuring the data center’s total computing power is below agreed thresholds.
    
-   •
    
    Certified chip usage. Verifying that only approved chip models are in use.
    
-   •
    
    Security measures. Verifying implementation of required security protocols.
    
-   •
    
    Training run evidence. Examining records and transcripts of large-scale AI training activities.
    
-   •
    
    Hardware integrity. Inspecting for any evidence of chip tampering (Aarne, Fist, and Withers [2024](https://arxiv.org/html/2408.16074v2#bib.bib1)).
    

In addition to requiring periodic inspections, an agreement could also require continuous monitoring of certain facilities. In a continuous monitoring setup, inspectors are present at facilities at all times to catch any violations of agreements (such as tampering with hardware). A final possible implementation is challenge inspections, similar to those conducted by the Organization for the Prohibition of Chemical Weapons (OPCW), where inspections can be called for on short notice based on suspicions of non-compliance (Organisation for the Prohibition of Chemical Weapons [1997](https://arxiv.org/html/2408.16074v2#bib.bib37)).

Precedent. The New START treaty signed by the USA and Russia provides for 18 annual on-site inspections for the American and Russian inspections (US Department of State). These inspections allow for specific verification activities, such as confirming the number of reentry vehicles on deployed missiles, counting nuclear weapons on bombers, and verifying the conversion or elimination of weapon systems. The treaty’s approach of allowing a limited number of highly structured inspections, focused on counting and verifying specific hardware, is a suggestive precedent for inspections of data centers. Notably, an earlier treaty (START I) also provided for continuous monitoring of specific facilities (Arms Control Association [2022](https://arxiv.org/html/2408.16074v2#bib.bib3)).

The most significant precedent for the detailed inspection of hardware is the IAEA’s mandated use of bespoke tamper-evident containment seals for nuclear materials (International Atomic Energy Agency [2011](https://arxiv.org/html/2408.16074v2#bib.bib23)). These seals – each of which bears a unique identifier – are designed to provide clear evidence of any tampering or unauthorized access. IAEA inspectors examine these seals during on-site visits, allowing them to detect any undeclared movement or use of nuclear materials.

#### ON-SITE INSPECTIONS OF SEMICONDUCTOR MANUFACTURING FACILITIES

Inspections of semiconductor manufacturing facilities could be used to determine the quantity and nature of chips produced. The manufacturing of advanced chips is a highly specialized activity, and only a few entities have this capacity (Sastry et al. [2024](https://arxiv.org/html/2408.16074v2#bib.bib45)). For example, it is well known that ASML produces EUV lithography systems which are needed to manufacture the latest generation of advanced chips (Khan, Mann, and Peterson [2021](https://arxiv.org/html/2408.16074v2#bib.bib27)). If inspectors identified the existence of such machines, it would be relatively easy to know what kind of chips are possible to construct at the manufacturing site. Inspectors may also be able to use basic metrics like the square-meterage of a facility or the number of lithography machines to bound the number of chips that are possible to produce in such facilities.

These inspections could also verify that facilities are producing chips in accordance with any hardware-related agreements. For example, if nations agreed to only build chips with certain on-chip hardware governance mechanisms, inspections of semiconductor manufacturing facilities could identify non-compliance. Inspectors could look at a sample of chips, potentially midway through production, to ensure they have the correct mechanisms.

As with the inspections of data centers, continuous monitoring could also be used for semiconductor manufacturing facilities.

Precedent. The use of on-site inspections for monitoring compliance with international agreements has been well-established in other domains, particularly in controlling extreme risks.

1.  1.
    
    Organization for the Prohibition of Chemical Weapons (OPCW). The OPCW conducts inspections at facilities that produce toxic chemicals and their precursors. These inspections involve an initial tour, followed by a detailed inspection plan, physical inspections, and a review of the facility’s records to verify compliance. The intensity and duration of inspections vary depending on the perceived risk, with chemicals categorized into three schedules based on their threat level (OPCW [2024](https://arxiv.org/html/2408.16074v2#bib.bib35)).
    
2.  2.
    
    Preparatory Commission for the Comprehensive Nuclear-Test-Ban Treaty Organization (CTBTO). The CTBTO, although not fully operational due to the Comprehensive Nuclear-Test-Ban Treaty’s pending entry into force, has established protocols for on-site inspections (OSI). These inspections are intended to verify compliance with the treaty, particularly in detecting and investigating potential nuclear explosions. If the treaty enters into force, an OSI could be initiated upon the request of a State Party. The inspection area could cover up to 1000 km2 (The Comprehensive Nuclear-Test-Ban Treaty Organisation [2024](https://arxiv.org/html/2408.16074v2#bib.bib50)).
    

#### ON-SITE INSPECTIONS OF AI DEVELOPERS

An international inspection team could visit an AI development facility to ensure that developers are running authorized code, properly implementing model evaluations and safeguards, and assess safety culture and security concerns. Inspections could involve various components, such as reviewing code (Casper et al. [2024](https://arxiv.org/html/2408.16074v2#bib.bib12)), assessing compliance with commitments from safety cases[^6], and conducting semi-structured interviews with key personnel to solicit security-relevant concerns (see Wasil et al. ([2024a](https://arxiv.org/html/2408.16074v2#bib.bib57))). Inspections could uncover the usage of unauthorized or unlicensed AI algorithms. A number of privacy-preserving technologies in development could facilitate such inspections without being overly intrusive. .[^7]

Precedent. The closest precedent is the IAEA’s use of on-site inspections, as discussed above. Their approach demonstrates the feasibility of conducting thorough on-site inspections in sensitive, high-tech environments, which could be adapted for AI development facilities. The key difference is that AI inspections would focus more on software and computational resources rather than physical materials, requiring inspectors with specialized expertise in AI technologies and development practices.

![Refer to caption](https://arxiv.org/html/2408.16074v1/x3.png)

Figure 3: Summary of evasion techniques to avoid access-dependent verification methods

#### KEY TAKEAWAYS

Access-dependent methods can allow for in-depth inspections of key facilities such as AI development facilities, hardware manufacturing facilities, and data centers. If international inspectors have sufficient access to these facilities, this provides a great deal of robustness to a verification regime. However, such methods may be perceived as invasive, and they may rely on the permission of nations that are suspected of unauthorized activity. Access-dependent methods can also be somewhat flexible depending on the amount of political will and the level of access that nations are willing to provide. To preserve privacy or trade secrets, inspectors may receive limited access– enough access to verify that an unauthorized training run is not being conducted but not enough access to see exactly what kind of tasks are being performed.

### Hardware-dependent verification methods

#### CHIP LOCATION TRACKING

Chip location tracking involves implementing a system to monitor the movement and use of AI-capable chips (Brass [2024](https://arxiv.org/html/2408.16074v2#bib.bib11)). This method requires international agreement on chip manufacturing standards and the implementation of tracking mechanisms directly into the hardware. Each chip above a certain computational threshold would be assigned a unique identifier and equipped with secure tracking capabilities.

Precedent. The concept of tracking and monitoring critical technology has several precedents across different industries, particularly where security, compliance, and international regulation are concerned.

-   •
    
    Nuclear Material Tracking. The IAEA monitors and tracks nuclear materials globally using systems like the Integrated Nuclear Fuel Cycle Information System (International Atomic Energy Agency [2024b](https://arxiv.org/html/2408.16074v2#bib.bib25)). The IAEA also maintains a databse of incidents involving trafficking or other unauthorized uses of nuclear or radioactive materials (International Atomic Energy Agency [2024a](https://arxiv.org/html/2408.16074v2#bib.bib24)).
    
-   •
    
    Pharmaceutical Supply Chain Tracking. The Drug Supply Chain Security Act (DSCSA) in the United States currently outlines steps to achieve, “an interoperable and electronic way to identify and trace certain prescription drugs at the package level as they move through the supply chain” (U.S. Food and Drug Administration [2024](https://arxiv.org/html/2408.16074v2#bib.bib55)).
    

#### CHIP-BASED REPORTING

Chip-based reporting involves implementing mechanisms within AI-capable chips and closely associated hardware (e.g., networking cards) to automatically detect and signal when they are being used in ways that violate agreed-upon constraints. These constraints might include thresholds on the number of chips connected together, or specific operations the chip is not authorized to perform. By embedding these reporting mechanisms at the lowest levels of the software stack — within the firmware and drivers of the AI-capable chips or associated networking devices — it may become more challenging for developers to bypass these safeguards. As one moves up the software stack, toward components that operate at higher levels of abstraction, it becomes easier for developers to replace authorized programs with their own software, potentially circumventing the constraints. Therefore, focusing on the lower levels of the stack, such as firmware, which is the (often read-only) software residing on the device (NASA [2004](https://arxiv.org/html/2408.16074v2#bib.bib32)), and the drivers, which allow the operating system to communicate with the device (Microsoft [2023](https://arxiv.org/html/2408.16074v2#bib.bib31)), is crucial for effective enforcement of constraints. These components are typically developed by the chip maker, further limiting the number of developers who could foreseeably edit reporting mechanisms.

Precedent. The closest precedent for this type of firmware-based reporting is the Light Hash Rate (LHR) GPUs developed by NVIDIA. These GPUs can detect, via mechanisms implemented in their firmware and drivers, whether they are being used for Ethereum mining (Nvidia [2021](https://arxiv.org/html/2408.16074v2#bib.bib34)). Similar strategies could foreseeably be developed to report unauthorized AI training.

![Refer to caption](https://arxiv.org/html/2408.16074v1/x4.png)

Figure 4: Summary of evasion techniques to avoid hardware-dependent verification methods.

#### KEY TAKEAWAYS

Hardware-dependent verification methods may offer robust and privacy-preserving tools for detecting non-compliance. However, these methods require nations with advanced hardware manufacturing capabilities to agree to rules around hardware manufacturing. Another challenge is that advanced chips are already in circulation (without hardware-enabled mechanisms built-in). A verification regime relying on hardware-dependent measures may need to address this “legacy hardware”, potentially through retrofitting techniques or gradual phase-out strategies.

If successfully implemented, these methods could dramatically enhance the effectiveness of other verification approaches, particularly on-site inspections. However, they also raise important concerns about privacy, national sovereignty, and potential misuse that must be carefully addressed. Overall, hardware-dependent methods represent a promising but long-term goal, requiring sustained international cooperation and technological innovation to realize their full potential in AI governance.

## Limitations and discussion

This paper examined verification methods that could help nations detect non-compliance with international agreements prohibiting unauthorized AI development and unauthorized data centers.

Verification methods vary in their feasibility, intrusiveness and effectiveness. National technical means offer a valuable starting point, capable of detecting large-scale AI infrastructure and unusual patterns in energy consumption, hardware imports, and financial transactions. However, national technical means are limited in their ability to identify software-level violations or concerted attempts at concealment. Access-dependent methods, such as on-site inspections, provide more robust reassurance but require nations to agree to international inspections. Hardware-dependent approaches offer additional robustness (potentially even guarantees) but face some implementation challenges, including the need to address existing legacy hardware.

Table 1 summarizes gaps in individual verification methods, as well ways each method can be complemented by other methods.

Additionally, the verification methods are at different levels of maturity: some are ready-to-implement, while others will require additional research. Figure 5 lists the verification methods based on the amount of additional research required to implement each method.

## Future research directions

Our work provides a starting point for discussions about verification methods, but there are many open questions that can be addressed by future work. Some of these directions include:

-   •
    
    Red-teaming exercises for international verification. In a “red-team” step, the authors could brainstorm how an adversary might try to hide an unauthorized training run or unauthorized data center. Then, in a “blue team” step, the authors could identify how one or more verification methods could catch the adversary. Then, in a subsequent “red team” step, the authors could brainstorm if there are feasible ways for the adversary to avoid or undermine the verification method(s). This process could be used to determine likely ways that adversaries may try to evade verification methods and highlight ways of strengthening international verification regimes.
    
-   •
    
    Design of international AI governance institutions. Compliance with international agreements is often verified by international institutions. Some early work has proposed international organizations that could set and verify compliance with safety standards (Ho et al. [2023](https://arxiv.org/html/2408.16074v2#bib.bib21); Cass-Beggs et al. [2024](https://arxiv.org/html/2408.16074v2#bib.bib13)), certify national licensing agencies (Trager et al. [2023](https://arxiv.org/html/2408.16074v2#bib.bib51)), verify compliance with a variety of potential agreements (see Maas and Villalobos ([2023](https://arxiv.org/html/2408.16074v2#bib.bib30))), and participate in joint AI safety research (Cass-Beggs et al. [2024](https://arxiv.org/html/2408.16074v2#bib.bib13)). One avenue for future research is to provide more details about how an international verification agency could be structured, how decision-making power is distributed between nations, how the agency handles disputes over non-compliance, and what powers ought to be granted to the agency. Such work could draw from best practices or lessons learned from the design and implementation of other international institutions (such as the IAEA and the OPCW) and bilateral or multilateral agreements (such as the Strategic Arms Reduction Treaties and the Wassenaar Agreement).
    
-   •
    
    Enforcement of international agreements. Our paper focused on verification– detecting whether or not nations are complying with an agreement. A separate important question is enforcement– how nations should react in the event that non-compliance is identified. Such work could examine what kinds of responses would be proportionate to the violation. For example, evidence of small-scale chip smuggling would warrant a less strong response than evidence of an illegal or unauthorized training run.
    
-   •
    
    Research on hardware-enabled mechanisms to enhance verification and/or enforcement. Hardware-enabled mechanisms can unlock new verification methods and make existing verification methods more robust. Some hardware-enabled mechanisms are ready to be implemented swiftly, while others may take several years of research to further develop. Additionally, there are open questions relating to how to make hardware-enabled mechanisms more tamper-proof and privacy-preserving (see Kulp et al. ([2024](https://arxiv.org/html/2408.16074v2#bib.bib28))).
    
-   •
    
    Detecting unauthorized AI deployment or inference. Our paper focuses on detecting unauthorized AI development. Nations may also wish to have agreements in which they agree not to deploy advanced AI systems in certain ways (for example, nations might prohibit AI from being deployed in the context of nuclear systems, military R&D research, or AI R&D research that could trigger uncontrolled AI development.) Future work could examine verification methods that could detect the unauthorized deployment of AI systems, potentially through hardware-enabled licenses that detect the presence of unauthorized code used for inference.
    
-   •
    
    Detecting compliance with agreements around model evaluations. International agreements may require that certain kinds of model evaluations are conducted to detect potential safety or security issues (see Shevlane et al. ([2023](https://arxiv.org/html/2408.16074v2#bib.bib48))). Reliable risk evaluations and risk mitigation strategies could become a minimum safety bar imposed by international agreements. Future work could examine verification methods that allow international authorities to ensure that parties are implementing a set of internationally-required model evaluations, as well as any specific model evaluations that a developer proposed as part of a safety case or licensing application (see (Clymer et al. [2024](https://arxiv.org/html/2408.16074v2#bib.bib14); Wasil et al. [2024b](https://arxiv.org/html/2408.16074v2#bib.bib58))).
    
-   •
    
    Actions the international community can take in the immediate future. In the future, nations may be concerned enough about AI global security risks to warrant ambitious international agreements that require verification methods. For the immediate future, however, nations are interested in improving their understanding of global security risks. There are many actions that governments and civil society groups can participate in to increase global understanding of AI progress and AI risks. Examples include efforts like the UK and Seoul AI Safety Summits (see Bletchley Declaration ([2023](https://arxiv.org/html/2408.16074v2#bib.bib9))), the establishment of the US and UK AI Safety Institutes and the Chinese AI Safety Network, Track II Dialogues between Western scientists and Chinese scientists (see International Dialogues on AI Safety ([2023](https://arxiv.org/html/2408.16074v2#bib.bib26))), and plans for how to respond to AI-related emergencies (see Wasil et al. ([2024c](https://arxiv.org/html/2408.16074v2#bib.bib60))).
    

## Conclusion

Our work provides an initial step toward a better understanding of how compliance with international AI agreements could be verified. Efforts to improve our understanding of verification methods will be especially important if global security risks from advanced AI become concerning enough to motivate coordinated national and international action. We believe some AI governance work should aim to prepare in advance for such scenarios. Such “future-oriented” AI governance work could address questions that would inform policymaking efforts in scenarios where concerns about global security risks became significantly stronger. Our hope is that our work on verification methods illustrates an example of promising work in this category.

## References

-   Aarne, Fist, and Withers (2024) Aarne, O.; Fist, T.; and Withers, C. 2024. Secure, Governable Chips, January 2024. _URL https://www. cnas. o rg/publications/reports/secure-gover nable-chips. Accessed_, 1–28.
-   Anderljung et al. (2023) Anderljung, M.; Smith, E. T.; O’Brien, J.; Soder, L.; Bucknall, B.; Bluemke, E.; Schuett, J.; Trager, R.; Strahm, L.; and Chowdhury, R. 2023. Towards Publicly Accountable Frontier LLMs: Building an External Scrutiny Ecosystem under the ASPIRE Framework. arXiv:2311.14711.
-   Arms Control Association (2022) Arms Control Association. 2022. START I at a Glance.
-   Armstrong, Bostrom, and Shulman (2016) Armstrong, S.; Bostrom, N.; and Shulman, C. 2016. Racing to the precipice: a model of artificial intelligence development. _AI & society_, 31: 201–206.
-   Baker (2023) Baker, M. 2023. Nuclear Arms Control Verification and Lessons for AI Treaties.
-   Barnard and Acheson (1946) Barnard, C. I.; and Acheson, D. 1946. A report on the international control of Atomic Energy. Technical report, US Department of State.
-   Bengio et al. (2024) Bengio, Y.; Hinton, G.; Yao, A.; Song, D.; Abbeel, P.; Darrell, T.; Harari, Y. N.; Zhang, Y.-Q.; Xue, L.; Shalev-Shwartz, S.; et al. 2024. Managing extreme AI risks amid rapid progress. _Science_, 384(6698): 842–845.
-   Bereska and Gavves (2024) Bereska, L.; and Gavves, E. 2024. Mechanistic Interpretability for AI Safety – A Review. arXiv:2404.14082.
-   Bletchley Declaration (2023) Bletchley Declaration. 2023. The Bletchley Declaration by Countries Attending the AI Safety Summit, 1-2 November 2023. Accessed: 2024-08-06.
-   Bostrom (2014) Bostrom, N. 2014. _Superintelligence: Paths, Dangers, Strategies_. USA: Oxford University Press, Inc., 1st edition. ISBN 0199678111.
-   Brass (2024) Brass, A. 2024. Location Verification for AI Chips. Technical report, Center for AI Governance. Accessed: 2024-08-09.
-   Casper et al. (2024) Casper, S.; Ezell, C.; Siegmann, C.; Kolt, N.; Curtis, T. L.; Bucknall, B.; Haupt, A.; Wei, K.; Scheurer, J.; Hobbhahn, M.; et al. 2024. Black-box access is insufficient for rigorous ai audits. In _The 2024 ACM Conference on Fairness, Accountability, and Transparency_, 2254–2272.
-   Cass-Beggs et al. (2024) Cass-Beggs, D.; Clare, S.; Dimowo, D.; and Kara, Z. 2024. Framework Convention on Global AI Challenges.
-   Clymer et al. (2024) Clymer, J.; Gabrieli, N.; Krueger, D.; and Larsen, T. 2024. Safety cases: Justifying the safety of advanced ai systems. _arXiv preprint arXiv:2403.10462_.
-   Desislavov, Martínez-Plumed, and Hernández-Orallo (2021) Desislavov, R.; Martínez-Plumed, F.; and Hernández-Orallo, J. 2021. Compute and energy consumption trends in deep learning inference. _arXiv preprint arXiv:2109.05472_.
-   Fearon (1995) Fearon, J. D. 1995. Rationalist explanations for war. _International organization_, 49(3): 379–414.
-   Financial Crimes Enforcement Network (2011) Financial Crimes Enforcement Network. 2011. SAR Leads to Recovery of Funds Derived from Foreign Corruption. Accessed: 2024-08-09.
-   Financial Crimes Enforcement Network (2024) Financial Crimes Enforcement Network. 2024. FinCEN Advisory to Financial Institutions to Counter the Financing of Iran-Backed Terrorist Organizations. Accessed: 2024-08-09.
-   Gabriel (2020) Gabriel, I. 2020. Artificial Intelligence, Values, and Alignment. _Minds and Machines_, 30(3): 411–437.
-   Heim (2024) Heim, L. 2024. Training Compute Thresholds: Features and Functions in AI Governance. _arXiv preprint arXiv:2405.10799_.
-   Ho et al. (2023) Ho, L.; Barnhart, J.; Trager, R.; Bengio, Y.; Brundage, M.; Carnegie, A.; Chowdhury, R.; Dafoe, A.; Hadfield, G.; Levi, M.; et al. 2023. International institutions for advanced AI. _arXiv preprint arXiv:2307.04699_.
-   Hogarth (2023) Hogarth, I. 2023. We must slow down the race to God-like AI. _Financial Times_. https://archive.is/jFfBQ. Accessed 2024-08-09.
-   International Atomic Energy Agency (2011) International Atomic Energy Agency. 2011. _Safeguards Techniques and Equipment: 2011 Edition_. Number 1 (Rev. 2) in International Nuclear Verification Series. International Atomic Energy Agency. https://www.iaea.org/publications/10416/safeguards-techniques-and-equipment-2011-edition.
-   International Atomic Energy Agency (2024a) International Atomic Energy Agency. 2024a. IAEA Incident and Trafficking Database (ITDB). Accessed: 2024-08-09.
-   International Atomic Energy Agency (2024b) International Atomic Energy Agency. 2024b. IAEA Nuclear Fuel Cycle Information System (NFCIS). Accessed: 2024-08-09.
-   International Dialogues on AI Safety (2023) International Dialogues on AI Safety. 2023. https://idais.ai. Accessed 2024-08-09.
-   Khan, Mann, and Peterson (2021) Khan, S. M.; Mann, A.; and Peterson, D. 2021. The semiconductor supply chain: Assessing national competitiveness. _Center for Security and Emerging Technology_, 8(8): 1–98.
-   Kulp et al. (2024) Kulp, G.; Gonzales, D.; Smith, E.; Heim, L.; Puri, P.; Vermeer, M. J. D.; and Winkelman, Z. 2024. Hardware-Enabled Governance Mechanisms: Developing Technical Solutions to Exempt Items Otherwise Classified Under Export Control Classification Numbers 3A090 and 4A090.
-   Loyens and Vandekerckhove (2018) Loyens, K.; and Vandekerckhove, W. 2018. Whistleblowing from an international perspective: A comparative analysis of institutional arrangements. _Administrative Sciences_, 8(3): 30.
-   Maas and Villalobos (2023) Maas, M. M.; and Villalobos, J. J. 2023. International AI institutions: A literature review of models, examples, and proposals. _AI Foundations Report_, 1.
-   Microsoft (2023) Microsoft. 2023. What is a driver? https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/what-is-a-driver- Accessed 2024-08-09.
-   NASA (2004) NASA. 2004. Software Safety Standard. https://klabs.org/ce˙watch/sw˙documents/871913b.pdf. Accessed 2024-08-09.
-   Ngo, Chan, and Mindermann (2022) Ngo, R.; Chan, L.; and Mindermann, S. 2022. The alignment problem from a deep learning perspective. _arXiv preprint arXiv:2209.00626_.
-   Nvidia (2021) Nvidia. 2021. A Further Step to Getting GeForce Cards into the Hands of Gamers. https://blogs.nvidia.com/blog/lhr/. Accessed 2024-08-09.
-   OPCW (2024) OPCW. 2024. Industry Inspections: What to Expect. https://www.opcw.org/industry-inspections-what-to-expect. Accessed 2024-08-09.
-   Open Nuclear Network (2024) Open Nuclear Network. 2024. Strengthening Nuclear Test Ban Monitoring and Verification: the Role of Commercial Satellite Imagery. https://oneearthfuture.org/sites/default/files/2024-06/TheRoleOfCommercialSatelliteImagery-.pdf. Accessed 2024-08-09.
-   Organisation for the Prohibition of Chemical Weapons (1997) Organisation for the Prohibition of Chemical Weapons. 1997. Convention on the Prohibition of the Development, Production, Stockpiling and Use of Chemical Weapons and on their Destruction.
-   Owyang and Shell (2017) Owyang, M. T.; and Shell, H. 2017. China’s economic data: an accurate reflection, or just smoke and mirrors? _The Regional Economist_, 25(2).
-   Pan, Bhatia, and Steinhardt (2022) Pan, A.; Bhatia, K.; and Steinhardt, J. 2022. The Effects of Reward Misspecification: Mapping and Mitigating Misaligned Models. In _International Conference on Learning Representations_.
-   Phuong et al. (2024) Phuong, M.; Aitchison, M.; Catt, E.; Cogan, S.; Kaskasoli, A.; Krakovna, V.; Lindner, D.; Rahtz, M.; Assael, Y.; Hodkinson, S.; et al. 2024. Evaluating frontier models for dangerous capabilities.
-   Rahman, Owen, and You (2024) Rahman, R.; Owen, D.; and You, J. 2024. Tracking Large-Scale AI Models. https://epochai.org/blog/tracking-large-scale-ai-models.Accessed: 2024-08-10.
-   Räuker et al. (2023) Räuker, T.; Ho, A.; Casper, S.; and Hadfield-Menell, D. 2023. Toward transparent ai: A survey on interpreting the inner structures of deep neural networks. In _2023 ieee conference on secure and trustworthy machine learning (satml)_, 464–483. IEEE.
-   Reuters (2018) Reuters. 2018. U.S. SEC awards Merrill Lynch whistleblowers a record $83 million. https://www.reuters.com/article/business/u-s-sec-awards-merrill-lynch-whistleblowers-a-record-83-million-idUSKBN1GV2UX/. Accessed 2024-08-09.
-   Rutkowski and Niemeyer (2020) Rutkowski, J.; and Niemeyer, I. 2020. Remote Sensing Data Processing and Analysis Techniques for Nuclear Non-proliferation. _Nuclear Non-proliferation and Arms Control Verification: Innovative Systems Concepts_, 339–350.
-   Sastry et al. (2024) Sastry, G.; Heim, L.; Belfield, H.; Anderljung, M.; Brundage, M.; Hazell, J.; O’Keefe, C.; Hadfield, G. K.; Ngo, R.; Pilz, K.; et al. 2024. Computing Power and the Governance of Artificial Intelligence. _arXiv preprint arXiv:2402.08797_.
-   Securities and Exchange Commission (2016) (SEC) Securities and Exchange Commission (SEC). 2016. Merrill Lynch to Pay $415 Million for Misusing Customer Cash and Putting Customer Securities at Risk. https://www.sec.gov/newsroom/press-releases/2016-128.
-   Shavit (2023) Shavit, Y. 2023. What does it take to catch a Chinchilla? Verifying rules on large-scale neural network training via compute monitoring. _arXiv preprint arXiv:2303.11341_.
-   Shevlane et al. (2023) Shevlane, T.; Farquhar, S.; Garfinkel, B.; Phuong, M.; Whittlestone, J.; Leung, J.; Kokotajlo, D.; Marchal, N.; Anderljung, M.; Kolt, N.; et al. 2023. Model evaluation for extreme risks. _arXiv preprint arXiv:2305.15324_.
-   Statista (2022) Statista. 2022. Commercially available satellite imagery worldwide in 2022, by spatial resolution. https://www.statista.com/statistics/1293723/commercial-satellite-imagery-resolution-worldwide/ Accessed 2024-08-09.
-   The Comprehensive Nuclear-Test-Ban Treaty Organisation (2024) The Comprehensive Nuclear-Test-Ban Treaty Organisation. 2024. On-site inspection. https://www.ctbto.org/our-work/on-site-inspection. Accessed 2024-08-09.
-   Trager et al. (2023) Trager, R.; Harack, B.; Reuel, A.; Carnegie, A.; Heim, L.; Ho, L.; Kreps, S.; Lall, R.; Larter, O.; hÉigeartaigh, S. Ó.; et al. 2023. International governance of civilian AI: A jurisdictional certification approach. _arXiv preprint arXiv:2308.15514_.
-   U.S. Department of State (2001) U.S. Department of State. 2001. Interim Agreement Between The United States of America and The Union of Soviet Socialist Republics on Certain Measures With Respect to the Limitation of Strategic Offensive Arms (SALT I).
-   U.S. Department of State (2021) U.S. Department of State. 2021. End-Use Monitoring of U.S.-Origin Defense Articles. https://www.state.gov/end-use-monitoring-of-u-s-origin-defense-articles/. Accessed 2024-08-09.
-   U.S. Department of State (2023) U.S. Department of State. 2023. New START Treaty. https://www.state.gov/new-start/. Accessed 2024-08-09.
-   U.S. Food and Drug Administration (2024) U.S. Food and Drug Administration. 2024. Drug Supply Chain Security Act (DSCSA). Accessed: 2024-08-09.
-   U.S. Securities and Exchange Commission (2017) U.S. Securities and Exchange Commission. 2017. SEC 2017 Annual Report: Whistleblower Program. Technical report, U.S. Securities and Exchange Commission.
-   Wasil et al. (2024a) Wasil, A.; Berglund, L.; Reed, T.; Plueckebuam, M.; and Smith, E. 2024a. Understanding frontier AI capabilities and risks through semi-structured interviews. https://papers.ssrn.com/sol3/papers.cfm?abstract˙id=4881729.
-   Wasil et al. (2024b) Wasil, A.; Clymer, J.; Krueger, D.; Dardaman, E.; Campos, S.; and Murphy, E. 2024b. Affirmative safety: An approach to risk management for high-risk AI. https://arxiv.org/pdf/2406.15371.
-   Wasil and Durgin (2024) Wasil, A.; and Durgin, T. 2024. US-China perspectives on extreme AI risks and global governance. https://arxiv.org/abs/2407.16903.
-   Wasil et al. (2024c) Wasil, A.; Smith, E.; Corin, K.; and Bullock, J. 2024c. AI Emergency Preparedness: Examining the federal government’s ability to detect and respond to AI-related national security threats. https://arxiv.org/abs/2407.17347.
-   Yuan et al. (2023) Yuan, X.; Liang, Y.; Hu, X.; Xu, Y.; Chen, Y.; and Kosonen, R. 2023. Waste heat recoveries in data centers: A review. _Renewable and Sustainable Energy Reviews_, 188: 113777.

## Appendix A Limitations of methods and possible solutions using complementary methods

Table 1: Limitations of methods and possible solutions using complementary methods.

| Verification method | Primary limitations | Complementary methods |
| --- | --- | --- |
| Satellite imagery | Data centers could be concealed underground or camouflaged | National intelligence services can provide human intelligence and signals intelligence to identify hidden facilities that satellite imagery might miss. They can gather information on construction activities, personnel movements, and communications that could indicate the presence of a concealed data center. Energy monitoring complements satellite imagery by detecting unusual power consumption patterns that might indicate a hidden data center. Even if a facility is visually concealed, its energy requirements are difficult to hide, especially for large-scale AI operations. Chip location tracking can determine the approximate location of data centers and discourage concealment. |
| Whistleblowers | Reliability issues: Whistleblowers may provide incomplete, biased, or false information. Limited access: Not all potential whistleblowers have access to critical information. Fear of retaliation: Potential whistleblowers may be deterred by fears of personal or professional consequences. | National intelligence services can corroborate or refute whistleblower claims through other intelligence gathering methods. On-site inspections can be triggered by whistleblower reports, allowing for direct verification of claims. Inspectors can look for specific evidence pointed out by whistleblowers, increasing the effectiveness of the inspection. Financial intelligence can be used to verify claims about resource allocation or unusual transactions mentioned by whistleblowers. |
| National intelligence services | Using national intelligence can be unnecessarily invasive and infringe on national sovereignty. The source of intelligence is often classified, which makes it a poor foundation for transparent discussion in international forums. | Satellite imagery can provide visual confirmation of intelligence reports about suspected facilities, offering a less intrusive method of verification. Financial intelligence can corroborate intelligence about resource allocation and unusual transactions, providing a paper trail for activities identified through other intelligence means. |
| Energy monitoring | Though plausible in theory, this method is unproven in practice. Energy consumption may be disguised as other high-energy activities. Obtaining detailed energy consumption data is also likely to be challenging. | Customs data analysis can corroborate energy monitoring data by tracking the import of high-performance computing equipment to areas with suspicious energy consumption patterns. |
| Customs data | Countries with advanced domestic manufacturing capabilities may be able to produce key components internally, reducing the effectiveness of customs data analysis. Distinguishing between components intended for authorised and unauthorised is likely to be challenging. | On-site inspections of semiconductor manufacturing facilities can verify whether domestic production capabilities match declared capacities, helping to identify discrepancies that might indicate undeclared production bypassing customs. Chip location tracking, if implemented, can help verify the end destination and use of key components that have passed through customs, ensuring they are being used as declared. |
| Financial intelligence | Many AI-related purchases may have legitimate alternate uses, making it difficult to distinguish between authorized and unauthorized activities. This method may be disproportionately invasive. Financial intelligence is also limited by banking secrecy laws and a potential lack of international cooperation. | Customs data analysis can corroborate financial intelligence by providing physical evidence of hardware purchases and movements that correspond to suspicious financial transactions. Whistleblowers can provide insider information about financial practices, helping to interpret complex transactions or reveal hidden financial structures used to fund unauthorized AI development. |
| Data center inspections | Inspections can only be carried out with the agreement of the host nation, potentially allowing time for concealment of violations. Thorough inspections are also both invasive and very resource-intensive, requiring significant time, expertise and resources. | Chip location tracking, if implemented, can be verified during inspections to ensure that the physical location of AI-capable chips matches their reported locations. Whistleblower information can guide inspectors to look for specific evidence of non-compliance that might otherwise be overlooked. |
| Fab inspection | Like all inspections, these inspections are also resource-intensive, invasive and pose threats to intellectual property. The technological complexity of chip manufacturing may also make it challenging for inspectors to detect potential violations without highly specialized expertise. | Chip location tracking, if implemented, can be initiated during the inspection process, ensuring that newly manufactured AI-capable chips are properly registered and tracked from the point of production. |
| AI developer inspection | Unlike hardware, software can be quickly modified or hidden, making violations difficult to detect. Such inspections also require highly specialized knowledge, and may pose a disproportionate risk to proprietary algorithms and research. | Whistleblowers can provide insider information about development practices, guiding inspectors to specific areas or systems of concern. Financial intelligence can be cross-referenced to ensure declared AI projects match financial records. |
| Chip location tracking | Requires agreement on chip manufacturing standards. Sophisticated actors may find ways to disable tracking mechanisms. The effectiveness of this intervention would be limited to the production of new chips. | On-site inspectionsof manufacturing sites can ensure that chips are being made with the required location tracking mechanisms. Satellite imagery can provide additional, more precise location tracking. |
| Fixed set reporting | Requires agreement on chip manufacturing standards. False positives/negatives: Balancing sensitivity to catch violations without triggering false alarms is difficult. The effectiveness of this intervention would be limited to the production of new chips. | On-site inspections of data centers can be triggered by automatic signals of non-compliance, allowing for rapid verification of potential violations. |
| Firmware-based reporting | Requires agreement on chip manufacturing and implementation standards; difficult to implement; may come with an economic or computational cost. | On-site inspections could be triggered by automatic signals of non-compliance, allowing for rapid verification of potential violations. |

## Appendix B Research and development estimates for verification methods

![Refer to caption](https://arxiv.org/html/2408.16074v1/x5.png)

Figure 5: Estimated research and development needed for verification methods investigated. Note that green indicates little additional research needed, orange indicates some additional research and red indicates significant additional research.

## Appendix C List of verification methods for international AI agreements

![Refer to caption](https://arxiv.org/html/2408.16074v1/x6.png)

Figure 6: We identify 12 verification methods (left-hand column) which could be used to investigate compliance with international agreements. Each method is categorized by: (a) whether or not it can be used to detect unauthorized training runs, (b) whether or not it can be used to detect unauthorized data centers, (c) whether or not the use of the method requires authorization from the suspected entity, and (d) whether or not the method relies on agreements relating to the development or distribution of advanced hardware. Asterisks (\*) indicate nuanced applications. Energy monitoring: it may be possible to infer unauthorized training by detecting energy consumption patterns at known data centers that exceed those suggested by reported levels. Data center inspections: While basic inspections can be conducted without agreements mandating the use of specific hardware, the effectiveness is significantly enhanced by such agreements (hardware-enabled chip logs). Fab inspections: while basic inspections are useful without agreements, their relevance is greatest as a tool to verify that labs are producing hardware compliant with mandated standards. National intelligence services: While these services may operate without explicit authorization from the suspected entity, their use in verification contexts would ideally be governed by international agreements to ensure legitimacy and prevent potential diplomatic conflicts.

[^1]: Early and reliable warning signs have also been discussed in the context of international agreements for nuclear security (see Barnard and Acheson ([1946](https://arxiv.org/html/2408.16074v2#bib.bib6)), specifically pages 15 to 34.
[^2]: Readers should also note that there is a forthcoming report by authors at the RAND Corporation that aims to provide a detailed examination of verification methods, analyze trade-offs with various methods, and discuss their technical implementation.
[^3]: FLOP stands for “floating-point operation” and reflects the amount of computations performed to train an AI system. Although no single metric is perfect, FLOP thresholds can provide a relatively straightforward way to set thresholds for advanced or dangerous AI development. As of 2024, the most powerful frontier AI systems were trained using approximately $10^{25}$ FLOP (see Rahman, Owen, and You ([2024](https://arxiv.org/html/2408.16074v2#bib.bib41))).
[^4]: We borrow this term from the security literature, see U.S. Department of State ([2001](https://arxiv.org/html/2408.16074v2#bib.bib52)).
[^5]: We thank Mauricio Baker for this suggestion, which is also included in his upcoming report.
[^6]: For example, whether mandated interpretability techniques are implemented (Räuker et al. [2023](https://arxiv.org/html/2408.16074v2#bib.bib42); Bereska and Gavves [2024](https://arxiv.org/html/2408.16074v2#bib.bib8)), or evaluations (Shevlane et al. [2023](https://arxiv.org/html/2408.16074v2#bib.bib48); Phuong et al. [2024](https://arxiv.org/html/2408.16074v2#bib.bib40); Anderljung et al. [2023](https://arxiv.org/html/2408.16074v2#bib.bib2)).
[^7]: We thank Mauricio Baker for this suggestion, which is also included in his upcoming report.

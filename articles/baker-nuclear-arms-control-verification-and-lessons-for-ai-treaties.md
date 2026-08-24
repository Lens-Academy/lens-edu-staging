---
title: "Nuclear Arms Control Verification and Lessons for AI Treaties"
author:
  - "Mauricio Baker"
source_url: "https://arxiv.org/abs/2304.04123"
published: 2023-04-08
created: 2026-08-20
accessed: 2026-08-20
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

###### Abstract

Security risks from AI have motivated calls for international agreements that guardrail the technology. However, even if states could agree on what rules to set on AI, the problem of verifying compliance might make these agreements infeasible. To help clarify the difficulty of verifying agreements on AI—and identify actions that might reduce this difficulty—this report examines the case study of verification in nuclear arms control. We review the implementation, track records, and politics of verification across three types of nuclear arms control agreements. Then, we consider implications for the case of AI, especially AI development that relies on thousands of highly specialized chips. In this context, the case study suggests that, with certain preparations, the foreseeable challenges of verification would be reduced to levels that were successfully managed in nuclear arms control. To avoid even worse challenges, substantial preparations are needed: (1) developing privacy-preserving, secure, and acceptably priced methods for verifying the compliance of hardware, given inspection access; and (2) building an initial, incomplete verification system, with authorities and precedents that allow its gaps to be quickly closed if and when the political will arises.

## Executive Summary

### Why nuclear arms control verification may matter for AI

Along with its benefits, AI poses significant security threats. Current or upcoming AI applications risk escalating conflicts, boosting disinformation and terrorist activities, and causing large-scale accidents. Some researchers have proposed that states should address these risks by voluntarily joining international agreements on AI. However, even if states could agree on how to regulate AI, states may struggle to verify compliance. Verification is far from the only issue that could make coordinated rules on AI infeasible or undesirable, but it could be a particularly thorny issue. To help clarify the challenge of verifying AI treaties, this report examines a relevant case study: nuclear arms control.

The challenges of verifying AI treaties will plausibly have significant similarities to challenges in nuclear arms control verification. These include restricting both government and corporate activity, protecting sensitive information, countering well-resourced adversaries, and verifying nationwide inventories of dual-use items. On the other hand, states are likely less willing to accept costly verification for AI treaties, as AI security currently tends to be a relatively low priority. That difference, though, might diminish as AI security risks become more pressing. Given the plausible similarities, we proceed with the case study.

### How monitoring & verification (M&V) has been implemented in nuclear arms control

First, we review M&V implementation across three types of nuclear arms control treaties: nonproliferation treaties; U.S.-U.S.S.R./Russia arms limitation treaties; and nuclear test {--{"author":"Luc's AI","timestamp":1787602432231}@@bans.[^1]--}{++{"author":"Luc's AI","timestamp":1787602432231}@@bans.[^note-1]++}

Nuclear nonproliferation treaties commit all but 10 states to not acquiring nuclear {--{"author":"Luc's AI","timestamp":1787602432752}@@weapons[^2].--}{++{"author":"Luc's AI","timestamp":1787602432752}@@weapons[^note-2].++} They are mainly verified as follows:

-   •
    
    States are required to declare (i.e. self-report) the amount and locations of all the nuclear material in their territory. (They may have nuclear material for nuclear energy.)
    
-   •
    
    To verify that nuclear materials and equipment in _declared_ nuclear facilities are not being used for weapons, international inspectors regularly verify declared accounts of nuclear materials. This involves much on-site measurement, verification of facility layouts, and surveillance at facilities. Under some {--{"author":"Luc's AI","timestamp":1787602433252}@@agreements[^3],--}{++{"author":"Luc's AI","timestamp":1787602433252}@@agreements[^note-3],++} certain non-nuclear facilities (e.g. adjacent facilities) are also declared and inspected.
    
-   •
    
    To verify that a state does not have _undeclared_ (i.e. secret) nuclear facilities, international inspectors receive voluntary tips from national intelligence agencies (which have e.g. spies and satellites), and they analyze their own limited information. Then, after identifying a suspect site, they investigate it (though this happens much more frequently under one type of {--{"author":"Luc's AI","timestamp":1787602433822}@@agreement[^4]).--}{++{"author":"Luc's AI","timestamp":1787602433822}@@agreement[^note-4]).++}
    

U.S.-U.S.S.R./Russia arms limitation treaties limited the number and/or types of these states’ ready-to-use nuclear weapons. They were mainly verified as follows:

-   •
    
    Under some treaties, the U.S. and U.S.S.R./Russia just used satellites (and presumably spies) to track each other’s ready-to-use nuclear weapons.
    
-   •
    
    Under other treaties, these states also self-reported the number, types, and locations of all their treaty-limited nuclear weapons. Then, each state regularly verified the other’s self-reports through satellites and on-site inspections (which mostly involved simple measurement), along with using radar to track missile test-flights.
    

Nuclear weapon test ban treaties are mainly verified as follows:

-   •
    
    Sensors, including an international network of  300 sensor stations, detect the acoustic waves and air particles that nuclear tests make, and analysts infer their source location.
    

### Track records of M&V in nuclear arms control

The strongest widely implemented M&V system in each of the above three categories of {--{"author":"Luc's AI","timestamp":1787602434551}@@treaties[^5]--}{++{"author":"Luc's AI","timestamp":1787602434551}@@treaties[^note-5]++} has had zero known major failures. This was in the context of (up to) a few known attempts at serious violations (e.g. developing a banned type of missile), all of which the system detected. However, weaker predecessors of these systems had some failures at detecting major violations. Most notably, a {--{"author":"Luc's AI","timestamp":1787602434551}@@system[^6]--}{++{"author":"Luc's AI","timestamp":1787602434551}@@system[^note-6]++} for verifying nonproliferation was designed with a focus on declared nuclear facilities, and it repeatedly failed to detect undeclared ones (though the associated weapon programs were all discovered or abandoned before they developed nuclear {--{"author":"Luc's AI","timestamp":1787602434551}@@weapons).[^7]--}{++{"author":"Luc's AI","timestamp":1787602434551}@@weapons).[^note-7]++}

### Politics of M&V in nuclear arms control

M&V negotiation records and outcomes, along with negotiators’ incentives, suggest M&V negotiations involved pressures to: ensure effectiveness, protect state and commercial secrets, limit disruptions and financial costs, avoid security threats, preserve national industrial competitiveness, keep compliance feasible, observe privacy rights, avoid passing new legislation, appease idiosyncratic stakeholders, limit partiality, and respect national {--{"author":"Luc's AI","timestamp":1787602435115}@@sovereignty.[^8]--}{++{"author":"Luc's AI","timestamp":1787602435115}@@sovereignty.[^note-8]++}

Separately, some of the failures mentioned earlier were influential. In particular, Iraq nearly developed nuclear weapons in spite of inspections, and this drove policymakers to greatly strengthen nonproliferation M&V.

### Lessons for the case of AI

First, let us narrow the scope of our analysis. While many AI activities carry risks, we will consider lessons for verifying {--{"author":"Luc's AI","timestamp":1787602435816}@@rules[^9]--}{++{"author":"Luc's AI","timestamp":1787602435816}@@rules[^note-9]++} on one increasingly important AI activity: training machine learning models with industrial-scale, specialized computer chips. Additionally, we will consider one approach to verifying these rules: using mechanisms built onto cutting-edge chips. Ongoing research by e.g. Shavit {--{"author":"Luc's AI","timestamp":1787602435816}@@\[[1](#bib.bib1)\]--}{++{"author":"Luc's AI","timestamp":1787602435816}@@\[1\]++} suggests such verification may be technically feasible, even while preserving privacy and efficiency (though that requires further R&D).

In this context, our case study suggests that, with certain preparations, the main foreseeable challenges of hardware-based AI treaty verification would be ones that were manageable in nuclear arms control. To see this, we will consider each of the main challenges that hardware-based verification appears likely to face, based on nuclear M&V politics. We will see that, for each of these challenges, substantial preparations would reduce it to a difficulty that was {--{"author":"Luc's AI","timestamp":1787602436424}@@manageable[^10]--}{++{"author":"Luc's AI","timestamp":1787602436424}@@manageable[^note-10]++} in the nuclear case.

As the first challenge we consider, AI chip users may oppose verification due to concerns that it would expose sensitive data and software to spies and saboteurs. Certain preparations would reduce these secrecy and security concerns to concerns that were manageable in nuclear arms control.

-   •
    
    States may need to disclose data centers’ locations, which could be sensitive. However, similar or worse concerns were manageable in the nuclear case; nearly all states agreed to disclose the locations of their nuclear energy facilities, and the U.S. and U.S.S.R. even agreed to share the locations of their nuclear weapon bases.
    
-   •
    
    If stakeholders develop privacy-preserving and secure methods for inspecting AI chips, then AI chip users’ secrecy and security concerns could be largely addressed. They may still worry that any physical proximity of inspectors or equipment to sensitive information is risky, but states accepted that in the nuclear case.
    

Second, using chip mechanisms for verification would pose direct costs. Certain preparations would reduce these direct costs to costs that were manageable in nuclear arms control.

-   •
    
    Verifying the presence and integrity of chip-based verification mechanisms would presumably require inspections. These could be implemented by adapting methods that were accepted in the nuclear case; an appendix details how this could be done with 3+ layers of defense. Back-of-the-envelope calculations suggest that, if rules’ scope were compute-intensive AI development in data {--{"author":"Luc's AI","timestamp":1787602436957}@@centers[^11],--}{++{"author":"Luc's AI","timestamp":1787602436957}@@centers[^note-11],++} then direct inspection costs (i.e. funding and interruptions to facilities) would be lower than or roughly similar to those which states accepted for nonproliferation M&V.
    
-   •
    
    R&D for acceptably priced hardware verification and limits on rules’ scope could theoretically reduce manufacturing and computational costs enough to keep overall costs similar to those of nonproliferation M&V.
    

Third, efforts to create M&V systems for AI could be stalled by the lack of relevant precedents and authorities. As with the above challenges, certain preparations would reduce these cultural and legal barriers to levels that were manageable in nuclear arms control.

-   •
    
    Stakeholders can first create a limited M&V system for AI, especially one with flexible authorities and scalable M&V methods. This would lower cultural and legal barriers to a strong M&V {--{"author":"Luc's AI","timestamp":1787602437472}@@system[^12].--}{++{"author":"Luc's AI","timestamp":1787602437472}@@system[^note-12].++}
    
-   •
    
    All the strongest nuclear M&V systems succeeded weaker systems. For example, the scope of nonproliferation M&V expanded from just research reactors to all nuclear facilities in a state. Similarly, the U.S. and U.S.S.R. applied inspections to intermediate-range missiles before applying them to (higher-stakes) long-range missiles.
    

This analysis highlights that stakeholders can help enable future AI treaty verification by developing acceptable hardware verification methods and building an initial, scalable verification system. For making these preparations, Shavit {--{"author":"Luc's AI","timestamp":1787602438077}@@\[[1](#bib.bib1)\]--}{++{"author":"Luc's AI","timestamp":1787602438077}@@\[1\]++} suggests potential next steps. The analogy of nuclear arms control suggests such steps are neither futile nor excessive; they could change verification challenges from unprecedented to historically manageable.

## 1 Background

### 1.1 Introduction

As the capabilities of AI systems grow, so do their potential benefits, as well as their safety, security, and misuse risks. Current or upcoming AI systems may greatly advance areas such as education and healthcare, but they also risk escalating military conflicts, empowering disinformation and terrorist activities, and causing large-scale accidents {--{"author":"Luc's AI","timestamp":1787602438591}@@\[[2](#bib.bib2)\]\[[3](#bib.bib3)\]\[[4](#bib.bib4)\]\[[5](#bib.bib5)\]\[[6](#bib.bib6)\].--}{++{"author":"Luc's AI","timestamp":1787602438591}@@\[2\]\[3\]\[4\]\[5\]\[6\].++} Ambitious potential approaches to addressing these risks include international agreements that guardrail AI development and/or deployment {--{"author":"Luc's AI","timestamp":1787602438591}@@\[[7](#bib.bib7)\]\[[8](#bib.bib8)\],--}{++{"author":"Luc's AI","timestamp":1787602438591}@@\[7\]\[8\],++} ideally complementing responsible domestic and corporate policies. For example, we could (optimistically) imagine a few countries which lead in AI reaching an enforceable agreement on the following practice: in their territories, any training run with certain high-risk {--{"author":"Luc's AI","timestamp":1787602438591}@@characteristics[^13]--}{++{"author":"Luc's AI","timestamp":1787602438591}@@characteristics[^note-13]++} would require the advance approval of an excellent, independent AI safety auditor. If implemented well enough, such an agreement would ensure that, across these {--{"author":"Luc's AI","timestamp":1787602438591}@@countries[^14],--}{++{"author":"Luc's AI","timestamp":1787602438591}@@countries[^note-14],++} AI developers that cut corners on safety would not outpace sufficiently responsible ones. A similar practice could help limit the misuse potential of AI systems, and other kinds of agreements could help prevent the unintended escalation of military conflict by AI systems.

Efforts to bring about international agreements on AI would need to overcome many challenges. An especially difficult challenge could be that, for these agreements to be enforceable, good monitoring and verification (M&V) of compliance seems necessary. States must be able to quickly and reliably catch defectors, or harmful defection would be much more {--{"author":"Luc's AI","timestamp":1787602439245}@@likely.[^15]--}{++{"author":"Luc's AI","timestamp":1787602439245}@@likely.[^note-15]++} At the same time, M&V must not be so revealing of industry or state secrets, or otherwise costly, that states would find it unacceptable.

Faced with the questions of whether effective M&V for AI is feasible and what would help bring it about, we are fortunate to be able to learn from the experience of nuclear arms control. This is the area where most efforts to negotiate and implement ambitious M&V systems for international security have taken {--{"author":"Luc's AI","timestamp":1787602439809}@@place,[^16]--}{++{"author":"Luc's AI","timestamp":1787602439809}@@place,[^note-16]++} and it is a context with some similarities (though significant differences) to that of {--{"author":"Luc's AI","timestamp":1787602439809}@@AI.[^17]--}{++{"author":"Luc's AI","timestamp":1787602439809}@@AI.[^note-17]++} Some research, e.g. {--{"author":"Luc's AI","timestamp":1787602439809}@@\[[10](#bib.bib10)\]\[[11](#bib.bib11)\]\[[12](#bib.bib12)\],--}{++{"author":"Luc's AI","timestamp":1787602439809}@@\[10\]\[11\]\[12\],++} has studied nuclear arms control as a case study for AI governance, but it appears that no existing research closely investigates the M&V aspects of this analogy. To fill that gap, this report details the history of M&V in nuclear arms control and analyzes its implications for AI treaties.

In considering lessons for the case of AI, we focus on potential rules on AI development that requires very large numbers of specialized computer chips, since verification in this context appears relatively tractable and increasingly important {--{"author":"Luc's AI","timestamp":1787602440309}@@\[[3](#bib.bib3)\]\[[13](#bib.bib13)\].--}{++{"author":"Luc's AI","timestamp":1787602440309}@@\[3\]\[13\].++} Concurrent and closely related work by Shavit {--{"author":"Luc's AI","timestamp":1787602440309}@@\[[1](#bib.bib1)\]--}{++{"author":"Luc's AI","timestamp":1787602440309}@@\[1\]++} describes a potential technical approach to implementing M&V in this context.

As a limitation, by focusing on verification, we only consider one factor in whether and how stakeholders should pursue AI treaties. Other important considerations, such as other reasons why negotiations could {--{"author":"Luc's AI","timestamp":1787602441023}@@fail[^18]--}{++{"author":"Luc's AI","timestamp":1787602441023}@@fail[^note-18]++} or why a treaty may be {--{"author":"Luc's AI","timestamp":1787602441023}@@undesirable[^19],--}{++{"author":"Luc's AI","timestamp":1787602441023}@@undesirable[^note-19],++} are beyond the scope of this report.

This report is organized as follows. Section [1](#S1 "1 Background ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") reviews background context on nuclear arms control. Section [2](#S2 "2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") describes methods used for nuclear arms control M&V. Section [3](#S3 "3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") overviews how these individual M&V methods have been combined and implemented as M&V systems. Section [4](#S4 "4 Track Records of Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") assesses these systems’ track records at detecting attempted violations. Section [5](#S5 "5 Politics of M&V Negotiations ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") describes the politics of the negotiations by which nuclear arms control M&V systems were agreed on. Section [6](#S6 "6 Lessons for AI Treaties ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") argues for lessons for the M&V of international agreements on AI. Section [7](#S7 "7 Conclusion ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") concludes. Lastly, appendices argue in more detail for various claims, and they describe a potential system for verifying the locations and integrity of AI-specialized chips.

### 1.2 Three types of nuclear arms control M&V systems

Some context is helpful for making sense of nuclear arms control M&V. In the early 1960s, the Cuban Missile Crisis convinced world leaders to do more to prevent nuclear {--{"author":"Luc's AI","timestamp":1787602441649}@@apocalypse.[^20]--}{++{"author":"Luc's AI","timestamp":1787602441649}@@apocalypse.[^note-20]++}

Since then, states have implemented three clusters of nuclear arms control treaties and associated M&V systems:

1.  1.
    
    In horizontal nonproliferation treaties, states that did not have nuclear weapons agreed to never make them. The most important of these treaties is the Non-Proliferation Treaty {--{"author":"Luc's AI","timestamp":1787602442228}@@(NPT).[^21]--}{++{"author":"Luc's AI","timestamp":1787602442228}@@(NPT).[^note-21]++}
    
    1.  (a)
        
        The NPT opened for signature in 1968, when five states were recognized as having nuclear weapons. Almost all states that did not have nuclear weapons at the time joined the NPT as non-nuclear-weapon states and did not develop nuclear weapons afterward. However, four states never joined (or in one case, left) the NPT and developed nuclear weapons.
        
    2.  (b)
        
        The NPT requires non-nuclear-weapon states to accept an M&V system implemented by the International Atomic Energy Agency (IAEA).
        
    
2.  2.
    
    In U.S.-U.S.S.R./Russia nuclear arms limitation treaties, the U.S. and U.S.S.R./Russia agreed to limit (and later, progressively reduce) the numbers or types of their {--{"author":"Luc's AI","timestamp":1787602442798}@@deployed[^22]--}{++{"author":"Luc's AI","timestamp":1787602442798}@@deployed[^note-22]++} nuclear delivery vehicles (e.g. ICBMs) or deployed nuclear warheads (as well as, in one case, missile defense {--{"author":"Luc's AI","timestamp":1787602442798}@@systems).[^23]--}{++{"author":"Luc's AI","timestamp":1787602442798}@@systems).[^note-23]++}
    
    1.  (a)
        
        The U.S. and U.S.S.R./Russia are widely considered to have mostly complied with these treaties.
        
    2.  (b)
        
        The first treaties of this type were verified largely through satellite images; later treaties also featured on-site inspections (organized by the U.S. and U.S.S.R./Russia, not the IAEA).
        
    
3.  3.
    
    In test ban treaties, states agreed to not carry out (certain) nuclear weapon {--{"author":"Luc's AI","timestamp":1787602443507}@@tests.[^24]--}{++{"author":"Luc's AI","timestamp":1787602443507}@@tests.[^note-24]++}
    
    1.  (a)
        
        There have been no clear cases of violations of these treaties.
        
    2.  (b)
        
        These treaties have mostly been verified through sensors (e.g. seismic sensors) that can detect nuclear weapon tests from a long distance.
        
    

Appendices elaborate on [regional nuclear-weapon-free zone treaties](#A2.SS1 "B.1 NWFZ Treaties ‣ Appendix B M&V in Nuclear-Weapon-Free-Zone treaties and in agreements with North Korea and Iran ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") and [nonproliferation agreements with North Korea and Iran](#A2.SS2 "B.2 Agreements with North Korea and Iran ‣ Appendix B M&V in Nuclear-Weapon-Free-Zone treaties and in agreements with North Korea and Iran ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").

These M&V systems were centered on tracking nuclear materials and nuclear delivery vehicles.

### 1.3 Nuclear materials

The IAEA’s efforts to verify horizontal nonproliferation focus on tracking uranium and plutonium, certain forms of which can be made to undergo nuclear explosions. A major reason for this focus is that acquiring such weapon-usable nuclear material is the hardest step in making nuclear weapons; in contrast, nuclear bomb design and assembly are relatively simple \[[17](#bib.bib17)\]. Additionally, uranium and plutonium are relatively rare materials and emit radiation, which makes them unusually easy to track.

Inconveniently, the production of nuclear energy involves materials and equipment that could easily be used to make nuclear weapons (in the absence of safeguards) \[[18](#bib.bib18)\].

-   •
    
    Uranium enrichment refers to the concentration of a specific isotope in uranium. While uranium is typically enriched above natural levels for use as nuclear fuel, enriching it to even higher levels makes it weapon-usable. Centrifuges that make fuel-usable uranium can be rearranged to make weapon-usable uranium.
    
-   •
    
    Plutonium is a byproduct of the reaction that takes place in nuclear reactors. After plutonium is isolated in the reprocessing of nuclear reactor products, it can be used to make nuclear weapons.
    

### 1.4 Nuclear delivery vehicles

Nuclear delivery vehicles—whose numbers are restricted in various U.S.-U.S.S.R./Russia arms limitation treaties—are equipment designed to send nuclear weapons to their targets. The main such equipment is \[[19](#bib.bib19)\]:

-   •
    
    Missiles, which can be launched from land, from submarines, or from aircraft.
    
    -   –
        
        Nuclear missiles include "ballistic missiles" (which fly like rockets) and "cruise missiles" (which fly like airplanes).
        
    -   –
        
        Land-based missiles can be immobile (i.e. based in silos) or mobile (i.e. installed on large vehicles that can move over roads or railways).
        
    -   –
        
        Nuclear missiles can be "tactical" (having ranges short enough to use in a battlefield) or "strategic" (having ranges long enough for the U.S. and U.S.S.R. to hit each other’s mainland, e.g. ICBMs).
        
    -   –
        
        Missiles can have "multiple independently targetable reentry vehicles" ("MIRVs"), meaning one missile can deliver multiple warheads to multiple locations.
        
    
-   •
    
    "Heavy bombers," which are planes that can be equipped to drop nuclear bombs.
    

## 2 Nuclear M&V Methods

This section provides an overview of the wide range of methods used for nuclear arms control M&V.

### 2.1 Accounting and mandatory self-reporting

Verification of horizontal nuclear nonproliferation and U.S.-U.S.S.R./Russia nuclear arms limitation treaties is largely done by verifying accounts of treaty-regulated items \[[20](#bib.bib20)\]\[[21](#bib.bib21)\]\[[22](#bib.bib22)\]\[[17](#bib.bib17)\]. The idea here is that, if an agency can verify the locations of all uranium and plutonium (or, in the case of U.S.-U.S.S.R./Russia treaties, the locations of all nuclear missiles, bombers, and/or deployed warheads) in a state, then the agency can verify that no uranium or plutonium has been diverted for nuclear weapon production (or that nuclear delivery vehicles’ numbers are below treaty limits).

State parties to the NPT and to several U.S.-U.S.S.R./Russia treaties are required to regularly self-report the quantities and locations of treaty-restricted items and facilities in their territories.[^25] To achieve this, states require domestic facility operators to track and report on regulated items. The remainder of these treaties’ M&V systems focus on verifying these state reports.

Self-reporting requirements can be helpful even if states submit false reports. After all, the requirements force deceptive states to tell much more detailed lies (which are easier to falsify[^26]), and they can lead deceptive states to accidentally self-report inconsistent information (which has happened[^27]).

As another application of mandated self-reporting, some bilateral treaties require exchanges of missile flight-test data. States use other means to verify the data’s accuracy, and the data helps states verify that new types of missiles have a compliant number of reentry vehicles.

### 2.2 M&V methods at declared facilities

The following M&V methods are applied only at state-declared, treaty-restricted facilities (i.e. most types of facilities in the nuclear fuel cycle for the NPT, and missile and bomber facilities for several U.S.-U.S.S.R./Russia treaties), in order to verify self-reported accounts \[[20](#bib.bib20)\]\[[21](#bib.bib21)\]\[[22](#bib.bib22)\]\[[17](#bib.bib17)\].

On-site M&V methods are implemented by on-site inspectors, which the IAEA implements on a regular basis for the NPT and which the U.S. and U.S.S.R./Russia have implemented with a quota system for several bilateral treaties.

Inspections tend to involve measures for mitigating concerns about espionage[^28] and, when relevant, for mitigating concerns that banned items could be snuck out during an inspection.[^29]

#### 2.2.1 On-site measurement methods

For verifying accounts, inspectors rely heavily on simple methods: visual observation, counting, measurement of item dimensions (e.g. with tape measures), and tipping nuclear material cans to test their weight.

To detect more subtle violations (e.g. removal of small amounts of nuclear material from many cans, or "dummy items"), inspectors use sensors (weight sensors, radiation detectors, and—rarely—X-ray scanners), and IAEA inspectors also take samples of materials for analysis at labs. At some facilities (especially areas where human presence is unsafe), IAEA inspectors install unattended equipment (e.g. item counters and radiation detectors).

#### 2.2.2 Containment and surveillance

To enable accounting verification in radioactive or otherwise inaccessible areas, and to reduce inspection frequency for stored items (in order to reduce costs), the IAEA uses containment and surveillance. That means putting nuclear materials in tamper-indicating containers and/or under the eye of on-site, IAEA-installed video surveillance cameras.

If the containers or cameras indicate that some materials were not accessed over some period of time, the IAEA can conclude that its accounting of those materials at the beginning of the period is still accurate by the end of the period.

#### 2.2.3 Unique identifiers

Deceptive actors may try to divert or tamper with regulated equipment and then hide this by replacing the regulated equipment with a substitute. Unique identifiers, i.e. known features that are hard to (quickly) counterfeit, make it hard to create convincing substitutes.

Serial numbers are used as unique identifiers to help detect the diversion of missiles in a few U.S.-U.S.S.R./Russia treaties. The IAEA also uses serial numbers to track nuclear fuel rod assemblies, and it uses more sophisticated types of unique identifiers in its tamper-indicating seals to make them harder to replace with counterfeits.

#### 2.2.4 Design information verification

The IAEA requires states to report information on the design of their nuclear facilities (e.g. their floorplans). It verifies this information through inspectors’ use of visual observation, simple length measurement tools, satellite images, and sometimes equipment that can detect modifications to a room or nearby underground rooms. These inspections are done both during and after facility construction.

Design information verification helps ensure that (i) facility designs do not make it easy to hide violations and that (ii) the IAEA can plan its inspections with accurate information on facility designs.

#### 2.2.5 Perimeter portal continuous monitoring

At a total of three (former) missile assembly facilities in each other’s territories, the U.S. and the U.S.S.R. established "perimeter portal continuous monitoring" to verify that the facility was not shipping out a restricted type of nuclear-capable missile. This meant sending 30 monitors to live and work near these facilities, continuously operating a system for monitoring the sites’ perimeters (without entering the facilities).

Monitors verified that objects large enough to hold banned items only exited through a few designated, monitored exits ("portals"), with advance notice. To verify that no banned items left through other exits, monitors would use a perimeter fence, a fence integrity monitoring system (or a video camera system, with motion detectors and lights), and a data processing center.[^30] Then, at portals, monitors would inspect outgoing objects with simple measurement methods[^31] or (when necessary) an X-ray scanner, while using gates and streetlights to control vehicle flow \[[24](#bib.bib24)\].

### 2.3 M&V methods not limited to declared facilities

Complementing on-site methods, other M&V methods are used to detect violations that occur outside declared facilities, especially the existence of secret, treaty-violating facilities or weapons \[[17](#bib.bib17)\]. Some of these methods can also uncover violations at declared facilities.

#### 2.3.1 National technical means

National technical means ("NTMs") of verification are state-owned technologies used for remotely verifying compliance with treaties \[[25](#bib.bib25)\].

-   •
    
    Nuclear arms control verifiers use satellites to help detect secret nuclear weapon facilities and to verify the number of various types of nuclear missiles.
    
-   •
    
    The U.S. and the U.S.S.R./Russia use radar to detect treaty-violating missile tests.
    
-   •
    
    The International Monitoring System is a global network of four types of sensors (three types of acoustic wave detectors and one type that is a detector of certain air particles) built to detect treaty-violating nuclear weapon tests \[[26](#bib.bib26)\].
    

NTMs have been very widely used in verification, including in the first few U.S.-U.S.S.R. nuclear arms control treaties (which had no other verification measures), suggesting states are relatively open to them.[^32]

#### 2.3.2 Human sources

Whistleblowers, spies, and loose-lipped accomplices can reveal much information about efforts to secretly violate treaties \[[27](#bib.bib27)\]. While this is often informal, under Additional Protocols (discussed [below](#S3.SS2 "3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")), the IAEA has wide authority to interview people involved in states’ nuclear programs.

#### 2.3.3 Intelligence sharing

The sharing of information between treaty-implementing agencies and national intelligence agencies (or between multiple national intelligence agencies) can help treaty verifiers reach conclusions that would be harder to reach with more limited information. Nuclear arms control treaties have no requirements for national intelligence agencies to share their information; the process is voluntary, informal, and inconsistent.

#### 2.3.4 Procurement monitoring

Intelligence agencies monitor nuclear-relevant trade, since the international purchase of certain equipment components or facilities can suggest intentions to proliferate. Case studies show that methods used for this have included human sources \[[27](#bib.bib27)\], shipment intercepts \[[28](#bib.bib28)\], intelligence sharing \[[29](#bib.bib29)\], and information provision requirements[^33].

#### 2.3.5 Other methods of unilateral information collection

Complementing agreed-on measures for verification, treaty parties (presumably, given their incentives and capabilities) use additional unilateral methods for verification. In addition to [espionage](#S2.SS3.SSS2 "2.3.2 Human sources ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") and [procurement monitoring](#S2.SS3.SSS4 "2.3.4 Procurement monitoring ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), state intelligence agencies might use communications intercepts \[[30](#bib.bib30)\] and open-source information.The IAEA also uses open-source information.

#### 2.3.6 Challenge inspections and requests for additional information

The above sources of information are often suggestive but not decisive or internationally credible. For example, satellite images might be ambiguous, and documents shared by a national intelligence agency might be fake.

To more credibly resolve ambiguities, nuclear arms control treaties often allow verifiers to request additional information (though a state might not provide it), and sometimes—most prominently, in IAEA Additional Protocols, discussed [below](#S3.SS2 "3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")—they authorize "challenge inspections"[^34]: inspections at nearly any location in a state’s territory. (In contrast, other inspections only take place at certain declared, relevant sites.)

Challenge inspections can feature environmental sampling: taking samples (e.g. by swiping a cloth over a surface) to detect unexplained particles of nuclear material.

### 2.4 Methods to boost other M&V methods

In addition to methods for collecting data, M&V often involves methods for improving how informative the collected data is \[[20](#bib.bib20)\]\[[21](#bib.bib21)\]\[[22](#bib.bib22)\]\[[17](#bib.bib17)\].

#### 2.4.1 Equipment validation and other methods to counter specific deception tactics

Various methods discussed above involve inspectors using or installing certain equipment. To verify that this equipment and its data are not tampered with, inspectors typically use:

-   •
    
    Containment and surveillance of the equipment itself (e.g. tamper-indicating devices on video cameras)
    
-   •
    
    Data authentication
    
-   •
    
    Equipment tests (e.g. with calibration materials)
    

In addition to equipment validation, M&V systems often involve the following measures to counter specific ways a state might attempt to deceive them:

-   •
    
    Short-notice inspections make it harder for states to clear out signs of non-compliance before inspectors arrive.
    
-   •
    
    Random sampling (for determining the location and timing of inspections, as well as items inspected) allows inspectors to be more efficient, while not letting states carry out violations with items they know will not be inspected.
    
-   •
    
    Bans on interference with or deliberate concealment from NTMs[^35] allow NTMs to work more reliably.
    
-   •
    
    Bans on concealment of missile flight-test data make it harder for states to self-report fabricated flight-test data.[^36]
    

#### 2.4.2 Methods to reduce ambiguity

Nuclear M&V systems sometimes involve the following requirements, which make it easier for verifiers to get relatively unambiguous information:

-   •
    
    Distinguishing characteristics: certain regulated items or activities are required to be easily distinguishable.[^37]
    
-   •
    
    Displays and exhibitions: certain regulated items (e.g. missiles) are required to be clearly shown to inspectors or to satellites (by opening up roofs).
    
-   •
    
    Location restrictions on equipment: some equipment (e.g. missiles) is only allowed to be in certain locations.
    
-   •
    
    Limits on the number (and size) of certain types of buildings or facilities: used most in bilateral nuclear arms control, these reduce the number of inspections needed.
    

## 3 Nuclear M&V Systems

In order to reliably detect nuclear arms control violations, the above M&V methods must be combined and implemented. This section provides an overview of the several nuclear arms control M&V systems that have been implemented very widely or between great powers.

### 3.1 High-level thoroughness and redundancy

At a high level, we might expect nuclear M&V systems to work well because of their thoroughness. At their best, nuclear M&V systems are designed with the aim of ensuring that _any_ attempted treaty violation would be quickly detected, with high enough probability[^38] to deter the violation \[[17](#bib.bib17)\].

An important aspect of thoroughness—for it to be robust to design or implementation failures—is redundancy. Accordingly, nuclear M&V systems use multiple layers of defense \[[26](#bib.bib26)\].

### 3.2 M&V for horizontal nonproliferation agreements

#### 3.2.1 IAEA safeguard systems

The NPT explicitly requires non-nuclear-weapon state parties to accept IAEA[^39] "safeguards" (i.e. M&V methods, with the details to be agreed on by the state and the IAEA) on all nuclear material in the state. The IAEA mainly implements these safeguards through two systems, in accordance with two types of agreements \[[17](#bib.bib17)\]:

1.  1.
    
    Comprehensive Safeguards Agreements ("CSAs"): The IAEA negotiated a single template[^40] which it has used as the basis for all its agreements with NPT non-nuclear-weapon states. The resulting agreements are called CSAs. CSAs are intended to (just) verify the peaceful use of nuclear materials at known nuclear facilities, rather than also detecting secret nuclear facilities.
    
2.  2.
    
    CSAs with Additional Protocols ("APs"): In the early 1990s, Iraq nearly made nuclear weapons by using secret nuclear facilities. In response, governments pushed for the IAEA to expand its M&V so that it would be better at detecting such violations. The IAEA did so by negotiating a new template[^41] for new agreements (called Additional Protocols), which supplement CSAs and improve the IAEA’s ability to detect secret nuclear facilities.
    
    1.  (a)
        
        While over half of non-nuclear-weapon state parties to the NPT have now adopted APs (especially ones with significant use of nuclear materials), many have not; doing so is not generally seen as an obligation from the NPT itself.[^42]
        
    

Besides the NPT, there have been about eight other prominent horizontal nuclear nonproliferation agreements, which apply to limited geographic regions or specific states (North Korea and Iran). Instead of having distinct M&V systems, these agreements mainly or entirely require state parties to adopt CSAs (sometimes with APs), implemented by the IAEA.[^43]

The IAEA reports sufficiently serious[^44] incidents of possible non-compliance to the UN General Assembly and the UN Security Council \[[17](#bib.bib17)\]. Then, it is up to states to decide what to do.[^45]

For its verification activities in 2022, the IAEA had a budget of approximately $150 million \[[34](#bib.bib34)\].

#### 3.2.2 IAEA verification in declared nuclear facilities

Under CSAs, the IAEA’s verification system at declared nuclear facilities works through the following process \[[17](#bib.bib17)\]:

-   •
    
    States report facilities: States are required to self-report the existence and location of all facilities in their territories that hold nuclear material, except for uranium mines, uranium mills, and certain waste facilities. Once self-reported, these facilities are referred to as "declared nuclear facilities."
    
-   •
    
    States report accounts: States are required to (effectively mandate nuclear facility operators to) keep and report accounts of nuclear materials at their declared facilities. A single facility typically has multiple areas in which nuclear material stocks and flows are tracked.
    
-   •
    
    The IAEA inspects facilities: The IAEA conducts on-site inspections at declared nuclear facilities to verify the accuracy of their reported nuclear accounts.
    
    -   –
        
        The IAEA conducts inspections at the frequency it estimates to be sufficient for identifying the diversion of nuclear materials before nuclear weapon construction can be finished. This is typically one, three, or twelve months, depending on the material.[^46][^47] In addition to regular, scheduled inspections, the IAEA also uses randomly timed inspections. Inspections come with a minimum 24-hour notice.[^48]
        
    -   –
        
        To detect violations at declared facilities, inspectors use many of the methods described earlier: [on-site measurement](#S2.SS2.SSS1 "2.2.1 On-site measurement methods ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (especially counting, using radiation detectors, and taking samples for analysis), [containment and surveillance](#S2.SS2.SSS2 "2.2.2 Containment and surveillance ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), and [design information verification](#S2.SS2.SSS4 "2.2.4 Design information verification ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").
        
    -   –
        
        For redundancy, inspectors use combinations of measurements.[^49]
        
    -   –
        
        To detect violations that involve diverting large amounts of nuclear material from a few containers, inspectors make quick, rough measurements of many containers; to detect violations that involve diverting _small_ amounts of nuclear material from _many_ containers, inspectors apply more sensitive methods to a sufficiently large random sample of containers.[^50]
        
    -   –
        
        To verify flows, the IAEA requires nuclear facility operators to declare when they have received certain materials[^51] and to hold them for a specified time. The IAEA verifies this with short-notice randomized inspections.
        
    -   –
        
        Traditionally, the IAEA developed safeguard agreements based just on the characteristics of each facility. Over the last decade, it has increasingly adopted "state-level approaches": deciding safeguard implementation with more consideration of the broader context in a state.[^52]
        
    -   –
        
        In addition to on-site inspections, the IAEA also uses unattended and remote safeguards: video cameras and machines that do automated counting and measurement of nuclear materials.
        
    
-   •
    
    The IAEA analyzes inspection data and resolves anomalies: When safeguards show inconsistencies or odd findings that (in aggregate) are significant[^53], the IAEA by default first seeks clarification from the relevant state.
    
    -   –
        
        It can do this by, e.g., requesting additional information, redoing verifications (sometimes by shutting down a process line while inventories are re-counted), or requesting to carry out "special Investigations" (which include access beyond that which the IAEA would normally have).
        
    

When APs supplement CSAs, they do not greatly change the above process at declared facilities—see [the relevant appendix](#A3 "Appendix C How Additional Protocols change M&V processes at declared nuclear facilities ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for details.

#### 3.2.3 IAEA verification of the absence of undeclared nuclear facilities

We can break down the process of detecting undeclared facilities into two steps:[^54]

1.  1.
    
    Finding evidence suggesting that a state might have undeclared nuclear facilities (potentially at a specific location), and
    
2.  2.
    
    Resolving suspicions about suspected undeclared nuclear facilities.[^55]
    

Mechanisms for identifying suspect locations or states:

-   •
    
    Unofficially, the IAEA identifies suspect locations mainly through voluntary tips from national intelligence agencies (and perhaps also from whistleblowers). These tips from intelligence agencies appear to be irreplaceable for the IAEA’s ability to identify potential undeclared nuclear facilities.[^56][^57][^58]
    
    -   –
        
        Intelligence agencies have not published much information on their methods for detecting undeclared nuclear facilities, but some reports suggest their [methods](#S2.SS3.SSS5 "2.3.5 Other methods of unilateral information collection ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") include: spying, monitoring nuclear trade, analyzing satellite images, and using other open-source information \[[27](#bib.bib27)\]\[[35](#bib.bib35)\].
        
    -   –
        
        The IAEA also conducts its own analyses to identify suspect locations, but these are limited by the IAEA’s limited sources of information; compared to the high bar of the IAEA’s processes at declared facilities, the IAEA has no similarly comprehensive, independent process for reliably finding undeclared facilities.[^59]
        
    
-   •
    
    Expanding IAEA abilities under CSAs, states that have also adopted APs are required to provide the IAEA with information on additional nuclear buildings and activities \[[17](#bib.bib17)\].[^60] Presumably, whether or not states actually self-report on these facilities, these reporting requirements help the IAEA detect secret nuclear facilities.[^61]
    

Mechanisms for resolving suspicions about suspect locations or states (and their limitations) \[[17](#bib.bib17)\]:

-   •
    
    CSAs grant the IAEA very limited means for confirming or disconfirming its suspicions about undeclared nuclear facilities.[^62]
    
    -   –
        
        Recognizing this, the IAEA does not report the absence of undeclared nuclear facilities in states that only have CSAs.
        
    
-   •
    
    When they supplement CSAs, APs boost the IAEA’s ability to identify and investigate suspected undeclared nuclear facilities. APs authorize the IAEA to [investigate suspect locations](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") in certain ways:
    
    -   –
        
        For all the locations that APs require states to self-report (listed in a footnote under the last sub-heading), APs also grant the IAEA "complementary access" to these locations. This means that, with certain qualifications (especially for fully private activities), APs grant the IAEA non-routine inspection access to a very wide range of nuclear-relevant locations, with 24 hours’ notice.[^63]
        
    -   –
        
        APs also grant the IAEA complementary access to any location in a state, with a couple of qualifications.[^64]
        
    

### 3.3 M&V for U.S.-U.S.S.R./Russia nuclear arms limitation agreements

#### 3.3.1 M&V for SALT I Agreements and SORT

Several U.S.-U.S.S.R./Russia nuclear arms limitation agreements had little or no officially authorized M&V:

-   •
    
    SALT I Agreements: The earliest U.S.-U.S.S.R. nuclear arms control agreements (the SALT I interim agreement and associated Anti-Ballistic Missile Treaty, which capped offensive nuclear missiles and missile defense systems, respectively) only had [national technical means](#S2.SS3.SSS1 "2.3.1 National technical means ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") ("NTMs") as formally authorized M&V methods \[[37](#bib.bib37)\]\[[38](#bib.bib38)\].
    
    -   –
        
        The Soviets rejected proposals for inspections, due to concerns over espionage.
        
    
-   •
    
    SORT: The 2002 Strategic Offensive Reductions Treaty ("SORT"), aka the Moscow Treaty, had no formal verification methods of its own. However, SORT mostly overlapped with START I, which had an extensive M&V system, so in practice there were some M&V mechanisms allowing the U.S. and Russia to get information about whether the other was moving toward compliance with SORT.
    
    -   –
        
        The U.S. intelligence community concluded that, outside of the period where SORT would overlap with START I, it could not confidently verify Russian compliance, but Russia would likely comply regardless due to the costs of maintaining its nuclear arsenal. Also, SORT provisions only officially applied for one day. After outlining this context, arms control expert Jeffrey Lewis writes that SORT "isn’t arms control but domestic political theater" \[[39](#bib.bib39)\].
        
    

#### 3.3.2 M&V for the INF Treaty, START I, and New START

In the INF Treaty, START I, and New START, which have collectively constituted the majority of U.S.-U.S.S.R./Russia nuclear arms reduction treaties since 1987, verification tends to work in the following way \[[20](#bib.bib20)\]\[[21](#bib.bib21)\]\[[22](#bib.bib22)\]:

-   •
    
    Each party [shares and updates data](#S2.SS1 "2.1 Accounting and mandatory self-reporting ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") on where all its nuclear delivery vehicles are and when any of them are destroyed, while also sharing missile flight-test ("telemetry") data.
    
-   •
    
    Each party verifies the other’s shared data through various [on-site inspections](#S2.SS2.SSS1 "2.2.1 On-site measurement methods ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") coupled with [NTMs](#S2.SS3.SSS1 "2.3.1 National technical means ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") and (presumably) [other unilateral intelligence gathering methods](#S2.SS3.SSS5 "2.3.5 Other methods of unilateral information collection ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (e.g. espionage).
    
    -   –
        
        Inspections mainly use simple methods, e.g. counting and length measurement.[^65]
        
    -   –
        
        Inspectors only inspect declared facilities; the task of discovering secret facilities is left to other methods (e.g. satellites).
        
    
-   •
    
    Additionally, two of these treaties use [perimeter portal continuous monitoring](#S2.SS2.SSS5 "2.2.5 Perimeter portal continuous monitoring ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") at a few missile assembly facilities, and the treaties involve further [measures that make it easier](#S2.SS4 "2.4 Methods to boost other M&V methods ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for inspections and NTMs to verify compliance: restrictions on equipment locations, distinguishing characteristics, limits on the number of (size-limited) on-site buildings, and [unique identifiers](#S2.SS2.SSS3 "2.2.3 Unique identifiers ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").
    

Differences between these treaties’ verification systems are discussed in a footnote[^66], and more details on implementation can be found in the [earlier section](#S2 "2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") on M&V methods.

### 3.4 M&V for nuclear weapon test bans

All 4 nuclear weapon test ban treaties are verified mainly through sensors meant to detect distant nuclear explosions, and 2 of the treaties also have provisions for on-site inspections.

#### 3.4.1 National technical means and the IMS

For over two decades, the Comprehensive Test Ban Treaty Organization ("CTBTO") has been building the International Monitoring System—a global network of  300 sensors designed to detect nuclear explosions \[[26](#bib.bib26)\]. This system is operational despite the relevant treaty—the Comprehensive Test Ban Treaty ("CTBT")—not having entered into force.[^67] The system consists of four types of sensors, which detect acoustic waves or air particles that are indicative of nuclear explosions.[^68] In addition to the sensor stations, the CTBTO operates a system to transmit sensor data to a data processing center, which shares raw and analyzed data with member states. Analysts can use sensors’ data to infer the location of nuclear tests.[^69]

In addition to sensors overseen by the CTBTO, states and some private organizations have their own relevant sensors \[[40](#bib.bib40)\]. These were the main basis of verification for nuclear test ban treaties that preceded the CTBT.

The CTBTO had a budget of approximately $100 million allocated for verification in 2020 \[[41](#bib.bib41)\][^70].

#### 3.4.2 On-site inspections

The Peaceful Nuclear Explosions Treaty—a U.S.-U.S.S.R. treaty that was ratified in 1990 and caps the yield (i.e. energy) of peaceful nuclear explosions[^71]—authorizes on-site inspections at the sites of peaceful nuclear explosions that are sufficiently close to the permitted threshold, and it also establishes data exchange requirements for parties to inform each other about these tests. Depending on the details of the explosions, inspectors may be able to use visual observation, photo cameras, a local seismic network, electrical equipment for yield determination, and a geologist field kit \[[42](#bib.bib42)\].

The CTBT, a ban on all nuclear explosions, would authorize [challenge inspections](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") if it entered into force. These would be conducted by the CTBTO[^72] \[[43](#bib.bib43)\]. Inspectors would be authorized to carry out visual observation, use various types of sensors, and take samples (including by drilling)[^73] \[[44](#bib.bib44)\].

## 4 Track Records of Nuclear M&V Systems

Having reviewed how nuclear M&V systems were implemented, we turn to their track records, focusing on the frequency of false negatives in detecting violations. As we will see, within each of the three main categories of nuclear arms control treaties, the strongest widely implemented M&V system has had zero known major failures and (up to) a few known attempts at serious violations, all of which the system detected. However, weaker predecessors of these systems had some known failures.

### 4.1 NPT M&V systems’ Track Records

First, we review the strengths of the track record of [IAEA verification](#S3.SS2 "3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), which include that Comprehensive Safeguards Agreements ("CSAs") boosted by Additional Protocols ("APs") have had no known, major failures.

-   •
    
    As far as is publicly known, IAEA safeguards have never completely failed; no state has ever acquired nuclear weapons while being party to the Non-Proliferation Treaty (which involves signing a CSA with the IAEA) (Bleek, 2017; UN ODA).[^74]
    
    -   –
        
        For context, a Belfer Center paper counts 7 non-nuclear-weapon states as having pursued nuclear weapons while being parties to the NPT \[[45](#bib.bib45)\][^75].
        
    
-   •
    
    Although dozens of states now have nuclear facilities and CSAs began to be implemented about 50 years ago, no state has attempted to divert a significant quantity of nuclear material from a facility that was under CSA safeguards.[^76]
    
-   •
    
    APs, which began to be implemented about 25 years ago to address CSAs’ weakness at detecting secret nuclear facilities, are nearly untested in their ability to detect secret nuclear weapons development activities; there are no known cases of states attempting to build or operate secret nuclear fuel-cycle facilities while under an AP. AP safeguards successfully detected Iran’s engagement in some undeclared nuclear activities, the details of which remain unclear.
    
    -   –
        
        There is almost no known case of a state pursuing a nuclear weapons program while under a CSA with an AP.[^77]
        
    -   –
        
        The one known exception is Iran[^78][^79], which openly expanded its nuclear activities and (as determined by the IAEA) also engaged in undeclared activities involving nuclear material, while implementing a CSA with an AP[^80]. Although Iran’s limited compliance has kept the IAEA from uncovering the details of these activities, the IAEA was able to discover that they occurred[^81] \[[48](#bib.bib48)\].
        
    -   –
        
        Even when it is not dealing with unique cases like Iran, the IAEA often faces and accepts significant delays in resolving uncertainties about the existence of undeclared nuclear facilities. For example, regarding the year 2021[^82], for 60 of the 132 states with CSAs and APs in force, the IAEA reported that "\[e\]valuations regarding the absence of undeclared nuclear material and activities for each of these States remained ongoing"[^83] \[[50](#bib.bib50)\].
        
    

However, the IAEA’s track record is far from perfect; CSA safeguards not complemented by APs repeatedly missed states’ construction of secret nuclear facilities (which they were not designed to detect).

-   •
    
    Iran, Iraq, Libya, and Syria all pursued nuclear weapons by building secret nuclear facilities while under CSAs, but CSA safeguards were not enough for the IAEA to notice \[[51](#bib.bib51)\]\[[28](#bib.bib28)\]\[[52](#bib.bib52)\]\[[53](#bib.bib53)\]. Similarly, the IAEA failed to notice Yugoslavian R&D and South Korean international purchases that pursued nuclear weapons while these states were under CSAs \[[54](#bib.bib54)\]\[[29](#bib.bib29)\].
    
-   •
    
    As exceptions to the above trend, CSA safeguards have occasionally identified banned activities outside of what they are primarily designed to identify.
    
    -   –
        
        In North Korea, following the state’s adoption of a CSA, initial IAEA inspections found that North Korea had previously processed more plutonium than it claimed. This finding kicked off (ultimately unsuccessful) diplomatic efforts to keep North Korea from getting the bomb \[[55](#bib.bib55)\].
        
    -   –
        
        In Syria, the IAEA concluded that a destroyed facility had "very likely" been an undeclared nuclear reactor (though this was several years after Israel bombed it) \[[56](#bib.bib56)\].[^84]
        
    

### 4.2 Bilateral Nuclear Arms Control M&V systems’ Track Records

For all U.S.-U.S.S.R./Russia nuclear arms limitation agreements that were mutually ratified and contained M&V measures, neither party is widely considered to have attempted the most serious violation possible: maintaining numbers of strategic arms far above their permitted levels. In this sense, [these M&V systems](#S3.SS3 "3.3 M&V for U.S.-U.S.S.R./Russia nuclear arms limitation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") are untested, though the lack of known violation attempts is some evidence for these systems’ (perceived) reliability.

Across the three bilateral arms control agreements with [extensive M&V systems](#S3.SS3.SSS2 "3.3.2 M&V for the INF Treaty, START I, and New START ‣ 3.3 M&V for U.S.-U.S.S.R./Russia nuclear arms limitation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (i.e. the INF Treaty, START I, and New START), there has been only one state allegation of an attempt at secret, serious noncompliance: 26 years after the INF Treaty entered into force, the U.S. accused Russia of discreetly developing and flight-testing a missile that violated the treaty. (The U.S. consequently withdrew from the treaty.)

-   •
    
    The timing of the U.S. allegations is ambiguous in its implications about the reliability of U.S. M&V, but a tentative conclusion is that U.S. M&V (especially NTMs) was adequate.
    
-   •
    
    Otherwise, the U.S. has mostly confirmed the U.S.S.R./Russia’s compliance, and Russia has made several relatively minor or tenuous allegations of noncompliance.
    

In bilateral arms control treaties that had [more limited M&V systems](#S3.SS3.SSS1 "3.3.1 M&V for SALT I Agreements and SORT ‣ 3.3 M&V for U.S.-U.S.S.R./Russia nuclear arms limitation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (e.g. just NTMs), the U.S. and the U.S.S.R. made several accusations of non-compliance (though not of massive non-compliance except for an unratified treaty). Given the ambiguity of these cases and the limited role of M&V, they tell us less about relevant M&V systems’ effectiveness.

See [an appendix](#A6 "Appendix F Details on track records of nuclear arms control M&V ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for more details and evidence on the above claims about parties’ allegations.

### 4.3 Nuclear Test Ban M&V Systems’ Track Records

There has been no clear, prominent case of a nuclear test ban being violated. Even the Comprehensive Test Ban Treaty, which has not entered into force, is considered to have been followed by signing parties.[^85]

The most significant potential exception is the "Vela incident"; there is mixed evidence about whether a Partial Test Ban Treaty state tested a nuclear weapon in 1979 \[[57](#bib.bib57)\]. Even if this violation did happen, though, it would have been before the construction of the [International Monitoring System](#S3.SS4.SSS1 "3.4.1 National technical means and the IMS ‣ 3.4 M&V for nuclear weapon test bans ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), so such a violation would face a stronger monitoring system today.

The International Monitoring System successfully detected all six of North Korea’s known nuclear tests (confirmed by the state’s announcements), providing some evidence for the system’s effectiveness \[[40](#bib.bib40)\]\[[58](#bib.bib58)\].

### 4.4 Limitations

The public would not know about any nuclear weapons development activities that were sufficiently well-kept secrets. However, there are some reasons to expect that there have not been not many such well-kept nuclear secrets:

-   •
    
    Some of the factors that most plausibly incentivize states to have nuclear weapons programs—deterrence and prestige—also incentivize states to inform other states and the public when they succeed at developing, testing, or stockpiling nuclear weapons. This suggests that most nuclear weapons programs that have succeeded are widely known.[^86]
    
-   •
    
    Changes in leadership or in state incentives can motivate states to reveal formerly secret programs.[^87]
    

There is also significant uncertainty due to incentives for states to spread misinformation about their own or others’ secret nuclear weapons activities.

## 5 Politics of M&V Negotiations

This section describes aspects of the politics of negotiations in which M&V systems were agreed on, focusing on the negotiations of the templates for Comprehensive Safeguards Agreements ("CSAs") and Additional Protocols ("APs"), the main templates for [IAEA M&V agreements](#S3.SS2 "3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"). Due to limitations in available sources[^88], this overview is relatively light and non-comprehensive.

### 5.1 Incentives in M&V negotiations

Consistently with negotiators’ incentives, the records and outcomes of M&V negotiations suggest that these negotiations involved significant pressures to do the following:

-   •
    
    Ensure effectiveness[^89]
    
    -   –
        
        This is reflected in M&V systems’ [thoroughness and redundancy](#S3.SS1 "3.1 High-level thoroughness and redundancy ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").
        
    
-   •
    
    Protect state and commercial secrets[^90]
    
    -   –
        
        Inspections include a wide range of measures for addressing this concern.[^91]
        
    -   –
        
        States that are technical leaders in some industries appeared to be especially concerned about IP risks.[^92]
        
    
-   •
    
    Limit disruptions and financial costs
    
    -   –
        
        Inspections have been limited and streamlined to address this concern.[^93]
        
    -   –
        
        States appeared to be more concerned over M&V being applied to the specific supply chain steps they led in.[^94]
        
    
-   •
    
    Limit other security threats
    
    -   –
        
        START I allows roughly its entire, extensive M&V system to be arbitrarily suspended for "operational dispersals" of nuclear forces. Analysts explain, "In view of the central importance of preserving the survivability of their strategic forces, the Parties were unwilling to place any restrictions on the number, frequency, or duration of operational dispersals. \[…\] \[H\]owever, the Parties specify that such operational dispersals shall only be conducted for national security purposes in time of crisis when a Party considers it necessary to act to ensure the survivability of its strategic forces \[…\] \[and only\] rarely" \[[67](#bib.bib67)\].
        
    
-   •
    
    Preserve national industrial competitiveness
    
    -   –
        
        In initial NPT negotiations as well as later AP negotiations, nuclear-weapon states volunteered to accept IAEA safeguards on their own commercial nuclear plants. This move was reportedly critical for easing "widespread concerns" that IAEA safeguards "would place non-nuclear-weapon States at a commercial and industrial disadvantage in developing nuclear energy" \[[66](#bib.bib66)\]\[[68](#bib.bib68)\]\[[17](#bib.bib17)\].
        
    
-   •
    
    Keep compliance feasible
    
    -   –
        
        This reportedly motivated minimum-notice requirements for inspections.[^95]
        
    
-   •
    
    Observe privacy rights
    
    -   –
        
        IAEA inspectors lack unconditional access to arbitrary locations.[^96]
        
    
-   •
    
    Avoid passing new legislation[^97]
    
    -   –
        
        States repeatedly objected to IAEA M&V proposals on the grounds that they would require changes to national laws and regulations \[[66](#bib.bib66)\].
        
    
-   •
    
    Appease idiosyncratic stakeholders
    
    -   –
        
        The U.S. chief negotiator of New START suggests the treaty includes telemetry data sharing because senators mistakenly considered it useful for verification.[^98]
        
    
-   •
    
    Limit partiality among states
    
    -   –
        
        Nuclear verification tends to be consistent across states, and safeguards agreements emphasize the use of "objective methods" \[[32](#bib.bib32)\].[^99]
        
    
-   •
    
    Respect national sovereignty
    
    -   –
        
        As discussed [below](#S6.SS4 "6.4 Managing cultural and legal barriers ‣ 6 Lessons for AI Treaties ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), concerns over national sovereignty appear to have motivated various early limitations on IAEA safeguards.[^100]
        
    

In the end, agreed-on IAEA safeguards were a mountain of compromises, tending to achieve high reliability while involving various limitations to reduce costs for host states.[^101]

### 5.2 Why Comprehensive Safeguards Agreements were not designed to detect secret nuclear facilities

Perhaps the biggest failure in nuclear M&V has been one discussed [above](#S4.SS1 "4.1 NPT M&V systems’ Track Records ‣ 4 Track Records of Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"): that CSAs were not designed to detect secret nuclear facilities. Seemingly emboldened and enabled by this, a handful of NPT non-nuclear-weapon states ran secret nuclear weapons programs while under CSAs, and usually they (especially the most advanced programs) relied on secret nuclear facilities.

How did CSA negotiations come to leave such a massive gap in their M&V system? Experts propose the following explanations (though typically with little to no citation/evidence) for why CSAs had very limited capacity for detecting undeclared nuclear facilities: negotiators had tended to think that:

-   •
    
    Secret nuclear facilities would be detected and voluntarily reported on by national intelligence agencies \[[15](#bib.bib15)\]\[[69](#bib.bib69)\]\[[70](#bib.bib70)\]\[[66](#bib.bib66)\];
    
-   •
    
    Establishing a self-contained nuclear fuel cycle would be too technically difficult for most states \[[69](#bib.bib69)\]\[[14](#bib.bib14)\];
    
-   •
    
    Inspectors having far-reaching access to investigate potential violations was politically unacceptable \[[15](#bib.bib15)\]\[[70](#bib.bib70)\]; and
    
-   •
    
    There were no good available methods for the IAEA to detect undeclared facilities \[[70](#bib.bib70)\].
    

Considering this alongside the fact that later fixes (Additional Protocols) required ratification from each state party, it appears that the CSA M&V system has been highly flawed because negotiators made fragile assumptions, built insufficient flexibility into CSAs, and were insufficiently proactive in responding to changes in the risk landscape.[^102]

### 5.3 The impact of salient failure

Despite its initial weaknesses (discussed above), the IAEA’s safeguards system was substantially strengthened in response to a salient failure. This failure was Iraq’s nearly successful secret nuclear weapons program, which was discovered only through the U.S.-led coalition’s victory against Iraq in the First Gulf War \[[71](#bib.bib71)\]\[[17](#bib.bib17)\].[^103]

After finding in 1991 that Iraq nearly made nukes under IAEA inspectors’ noses (the secret program operated in buildings adjacent to declared facilities), states successfully pushed for the IAEA to expand its role to not just safeguarding declared nuclear facilities but also detecting secret nuclear facilities. The IAEA determined that its existing agreements gave it authorities it had not been using—such as requiring earlier provision of design information and doing [environmental sampling](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")—and it began using these authorities. Additionally, the IAEA developed and agreed with dozens of states on APs, which brought the IAEA greatly [improved authorities](#S3.SS2.SSS3 "3.2.3 IAEA verification of the absence of undeclared nuclear facilities ‣ 3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for verifying the absence of undeclared nuclear facilities.

The [above](#S4.SS1 "4.1 NPT M&V systems’ Track Records ‣ 4 Track Records of Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") discussion of the IAEA’s systems and track records suggests APs have largely been successful.

## 6 Lessons for AI Treaties

### 6.1 Qualified optimism

Having reviewed the implementation, track records, and politics of monitoring and verification in nuclear arms control, we now turn to consider their implications for AI treaties.

This section primarily argues for the following conclusion: with certain preparations, the foreseeable challenges of one potential form of AI treaty verification (specifically, hardware-based verification of treaties setting rules on highly compute-intensive AI development) would mostly be challenges that were [successfully](#S4 "4 Track Records of Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") addressed in nuclear arms control. The main preparations needed to prevent worse challenges are:

1.  1.
    
    Developing privacy-preserving, secure, and acceptably priced methods for verifying the compliance of hardware, given inspection access; and
    
2.  2.
    
    Establishing an initial, incomplete verification system that is relatively easy to improve when opportunities arise, because it has flexible authorities and scalable precedents.
    

These are tall orders, but their potential suggests qualified optimism and plausible directions to move toward. More concretely, Shavit \[[1](#bib.bib1)\] describes some near-term policies and technical research questions that could serve as steps toward (1) and (2).

The following sections expand on the following argument for the above conclusion:

-   •
    
    First, consider this potential, high-level approach to verifying AI treaties: require and verify that computer chips used for highly compute-intensive AI development have built-in mechanisms that enable verification, then use these mechanisms to verify compliance.
    
    -   –
        
        Ongoing research suggests this may be technically feasible, even in privacy-preserving and efficient ways. Shavit \[[1](#bib.bib1)\] provides a technical description of one way chips could be used to verify compliance.
        
    -   –
        
        For concreteness, one example of a chip mechanism that would help enable verification is a tamper-evident log of chip activity.
        
    -   –
        
        Chip-based approaches to verification cannot address all important risks from AI. Still, chip-based verification may be unusually promising specifically in the context of highly compute-intensive AI development, as other drivers of AI advances—algorithms and data—are harder to track.
        
    
-   •
    
    M&V politics in the nuclear case suggest the above approach to verification will mostly encounter challenges from: secrecy and security concerns; direct costs; and cultural and legal difficulties.[^104]
    
    -   –
        
        This list covers all of the sources of objections to M&V proposals identified in the [earlier section](#S5 "5 Politics of M&V Negotiations ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") on politics, except for pressures to: ensure effectiveness, preserve national industrial competitiveness, keep compliance feasible, observe privacy rights, appease idiosyncratic stakeholders, and limit partiality among states.These potential concerns are de-emphasized below because they appear less likely to be major concerns or are already addressed by the preparations discussed next.[^105]
        
    
-   •
    
    Substantial preparations would reduce each of these challenges to a difficulty that was manageable in the nuclear case (that is, some nuclear arms control M&V system faced a similar or greater difficulty, yet the system was adopted and had a strong track record).
    
    -   –
        
        The next three sections argue for this claim in more detail.
        
    

### 6.2 Managing secrecy and security concerns

AI chip users may oppose verification due to concerns that (1) disclosure of AI chips’ locations, (2) inspections of AI chips, and (3) certain design features on AI chips would expose sensitive data and software to spies and saboteurs. Similar concerns could arise in the context of chip-making machines. Certain preparations would reduce these secrecy and security concerns to concerns that were manageable in nuclear arms control.

-   •
    
    The importance of (1) for verification poses the challenge of needing states to disclose sensitive facilities’ locations. This [was manageable](#S2.SS1 "2.1 Accounting and mandatory self-reporting ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") in nuclear arms control.
    
    -   –
        
        Nearly all states agreed to disclose the locations of their nuclear energy facilities for IAEA verification.
        
    -   –
        
        The U.S. and U.S.S.R. agreed to share the locations of their nuclear weapon bases with each other for INF Treaty, START, and New START verification.
        
    
-   •
    
    If stakeholders develop privacy-preserving and secure[^106] methods for using (2) and (3) to verify AI chips’ compliance, then AI chip users’ concerns here would be largely addressed.
    
    -   –
        
        States may still worry that physical proximity of inspectors or equipment to sensitive information is risky (even when no specific risks are apparent), but this concern [was manageable](#S2.SS2 "2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") in the nuclear case.
        
        -   \*
            
            For example, with a wide range of precautions, states accepted video surveillance and inspectors near sensitive centrifuge designs, and the U.S. and U.S.S.R./Russia allowed each other’s inspectors to be physically near their sensitive missile and warhead design information.
            
        -   \*
            
            As an example of a precaution that allows inspectors proximity but not access to sensitive information, in New START inspections, the front ends of missiles "would be opened up but covered with a soft or pliable cover so that objects \[reentry vehicles\] could be counted without revealing their technical characteristics" \[[25](#bib.bib25)\].
            
        
    

### 6.3 Managing direct implementation costs

Hardware-based verification would involve costs from (1) implementing, (2) verifying the presence of, and (3) using chip mechanisms that enable verification. Certain preparations would reduce these direct costs to costs that were manageable in nuclear arms control.

-   •
    
    (2) would presumably require inspections, which could be implemented by adapting [methods](#S2 "2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") used for verifying accounts of nuclear items.
    
    -   –
        
        This adaptation of nuclear materials accounting to AI chip accounting would be feasible; [an appendix](#A7 "Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") details how it could be done with 3+ layers of defense against potential violations.
        
    -   –
        
        Back-of-the-envelope calculations (in [an appendix](#A8 "Appendix H Back-of-the-envelope calculations of direct inspection costs ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")) suggest that, if rules’ scope were highly compute-intensive AI development in data centers (meaning commodity chips would need to not offer loopholes), then direct costs of inspections (both the inspections’ funding and the disrupted economic activity) would be lower than or very roughly similar to those which states accepted for nonproliferation M&V.
        
    
-   •
    
    There would also be manufacturing and computational costs.
    
    -   –
        
        To address these, R&D for acceptably priced hardware verification and limits on rules’ scope could theoretically reduce these costs by enough to make overall costs lower than that which states accepted for nonproliferation M&V.
        
    
-   •
    
    AI development increasingly relies on large numbers of highly specialized chips, making it plausible that a treaty with a narrow scope would still mitigate some important risks.
    

### 6.4 Managing cultural and legal barriers

Efforts to create M&V systems for AI could be stalled by the lack of relevant precedents and legal authorities. As with the above challenges, certain preparations would reduce these cultural and legal barriers to levels that were manageable in nuclear arms control.

-   •
    
    Stakeholders can first create a limited M&V system for AI, especially with flexible authorities and scalable M&V methods. This would lower cultural and legal barriers to a strong M&V system, which can then be created when opportunities to improve the limited system arise.[^107]
    
-   •
    
    All the strongest M&V systems in the nuclear case were created in the above way, incrementally, and some historians consider this critical, at least for the creation of the IAEA’s current strongest system.
    
    -   –
        
        A history of IAEA safeguards \[[15](#bib.bib15)\] writes that, "there was much initial resistance to the application of IAEA safeguards. Thus the first, incomplete but complex, safeguards system covered only \[…\] the research and experimental reactors of the day." Over the 60s, the scope of IAEA safeguards evolved to cover all declared nuclear facilities in a state. Then, in the 90s, the scope of IAEA safeguards [again extended](#S5.SS3 "5.3 The impact of salient failure ‣ 5 Politics of M&V Negotiations ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") in many states (after the failure with Iraq) to also cover undeclared nuclear facilities.
        
        -   \*
            
            Another history highlights a concern that motivated incremental development: that more ambitious safeguards "would not be generally acceptable to states until further experience with IAEA safeguards was gained" \[[63](#bib.bib63)\].
            
        
    -   –
        
        IAEA M&V system improvements in the 90s came most quickly and widely when there was more precedent and authority to make them \[[15](#bib.bib15)\]\[[66](#bib.bib66)\].
        
        -   \*
            
            Early in IAEA safeguards’ development, according to an IAEA history, "The concepts of short notice and unannounced inspections, now increasingly important features of IAEA safeguards, would have been regarded as inadmissible infractions of national sovereignty" \[[15](#bib.bib15)\].
            
        -   \*
            
            Some changes (e.g. the use of new technologies at inspections) could be adopted by majority vote, while other changes (e.g. expanded scope of inspections) required ratification by state legislatures; the latter changes have taken years longer and remain less widely applied.
            
        
    -   –
        
        U.S.-U.S.S.R./Russia treaties adopted increasingly intrusive M&V for increasingly high-stakes aims.
        
        -   \*
            
            While the first treaties only had [national technical means](#S2.SS3.SSS1 "2.3.1 National technical means ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") as authorized M&V methods, the INF Treaty expanded to [inspections](#S3.SS3.SSS2 "3.3.2 M&V for the INF Treaty, START I, and New START ‣ 3.3 M&V for U.S.-U.S.S.R./Russia nuclear arms limitation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for intermediate-range missiles, and the START I brought inspections to strategic (i.e. long-range) missiles.
            
        
    -   –
        
        States strengthened nuclear test ban M&V by building [many more remote sensor stations](#S3.SS4.SSS1 "3.4.1 National technical means and the IMS ‣ 3.4 M&V for nuclear weapon test bans ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"). Meanwhile, efforts that faced higher legal barriers stalled; the Comprehensive Test Ban Treaty has still not been ratified by the number of states it requires to enter into force.
        
    

## 7 Conclusion

Over the last half-century, states have developed a wide range of methods and thorough systems to verify compliance with nuclear arms control agreements. The strongest widely applied verification system for each of three types of nuclear arms control treaties has had no known major failures, though weaker predecessors had significant failures. Verification systems were built to maintain effectiveness while addressing many other concerns.

This history suggests qualified optimism for the prospects of verifying agreements on AI, at least for guardrailing highly compute-intensive AI development; with certain preparations, major foreseeable problems would be reduced to ones that were manageable in the nuclear case.

## Acknowledgements

This research was primarily done as an independent contractor with OpenAI’s Policy Research Team. Views expressed do not necessarily represent the views of OpenAI.

I am especially grateful to Jade Leung for her support throughout this research, from guidance on research question selection to feedback on drafts. I am also thankful to the broader compute governance field, particularly Yonadav Shavit, for informing my thinking on hardware-based verification; to John Carlson, Warren Stern, and Kuhan Jeyapragasan for their generous feedback; and to OpenAI for their support.

## References

-   \[1\] Yonadav Shavit. Verifying Agreements on Large-Scale ML Training via Compute Monitoring. 2023.
-   \[2\] Miles Brundage et al. The Malicious Use of Artificial Intelligence: Forecasting, Prevention, and Mitigation. Malicious AI Report, 2018.
-   \[3\] Rishi Bommasani et al. On the Opportunities and Risks of Foundation Models. 2021.
-   \[4\] Dan Hendrycks et al. Unsolved Problems in ML Safety. 2022.
-   \[5\] Michael Horowitz and Paul Scharre. AI and International Stability: Risks and Confidence-Building Measures. Center for a New American Security, 2021.
-   \[6\] Tim G. J. Rudner and Helen Toner. Key Concepts in AI Safety: An Overview. Center for Security and Emerging Technology, 2021.
-   \[7\] John R. Allen and Darrell M West. It is time to negotiate global treaties on artificial intelligence. The Brookings Institution, 2021.
-   \[8\] Olivia J. Erdélyi and Judy Goldsmith. Regulating Artificial Intelligence: Proposal for a Global Solution. 2018 AAAI/ACM Conference on AI, Ethics, and Society (AIES ’18), February 2–3, 2018, New Orleans, LA, USA doi/10.1145/3278721.3278731, 2018.
-   \[9\] Ege Erdil and Tamay Besiroglu. Algorithmic progress in computer vision. 2022.
-   \[10\] Matthijs M. Maas. How viable is international arms control for military artificial intelligence? Three lessons from nuclear weapons. Contemporary Security Policy, 40:3, 285-311, 2019.
-   \[11\] Paul Scharre and Megan Lamberth. Artificial Intelligence and Arms Control. Center for a New American Security, 2022.
-   \[12\] Waqar Zaidi and Allan Dafoe. International Control of Powerful Technology: Lessons from the Baruch Plan for Nuclear Weapons. Centre for the Governance of AI, 2021.
-   \[13\] Jaime Sevilla et al. Compute Trends Across Three Eras of Machine Learning. 2022.
-   \[14\] Roland Timerbaev. Interviewed by Anton V. Khlopkov. Arms Control Association, 2017.
-   \[15\] International Atomic Energy Agency. The Evolution of IAEA Safeguards. International Atomic Energy Agency, 1998. 9–10, 47.
-   \[16\] Thomas C Schelling. An Astonishing 60 Years: The Legacy of Hiroshima. Prize Lecture, December 8, 200. Department of Economics and School of Public Policy, University of Maryland, College Park, MD 20742, USA, 2005. 368.
-   \[17\] Michael Rosenthal et al. Deterring Nuclear Proliferation: The Importance of IAEA Safeguards. No. BNL-211553-2019-BOOK. Brookhaven National Lab.(BNL), Upton, NY (United States), 2019.
-   \[18\] Nuclear Threat Initiative. Nuclear 101. Nuclear Threat Initiative, n.d.
-   \[19\] Nuclear Threat Initiative. Missiles & Other WMD Delivery Systems. Nuclear Threat Initiative, n.d.
-   \[20\] Treaty on Elimination of Intermediate-range and Shorter-range Missiles Between USA and USSR (INF Treaty). 1987.
-   \[21\] Treaty Between the United States of America and the Union of Socialist Soviet Republics on Further Reduction and Limitation of Strategic Offensive Arms (START I). 1991.
-   \[22\] Treaty Between the United States of America and the Russian Federation on Measures for the Further Reduction and Limitation of Strategic Offensive Arms (New START). 2010.
-   \[23\] International Atomic Energy Agency Director General. Implementation of the NPT Safeguards Agreement in the Syrian Arab Republic. International Atomic Energy Agency, 2011. 2, 7.
-   \[24\] Protocol on Inspections and Continuous Monitoring Activities Relating to the Treaty between the United States of America And The Union of Soviet Socialist Republics on the Reduction And Limitation of Strategic Offensive Arms. 1991.
-   \[25\] Rose Gottemoeller. The New START Verification Regime: How Good Is It? Carnegie Endowment for International Peace, 2020.
-   \[26\] The Preparatory Commission for the Comprehensive Nuclear-Test-Ban Treaty Organization (CTBTO). Overview of the Verification Regime. The Preparatory Commission for the Comprehensive Nuclear-Test-Ban Treaty Organization (CTBTO), n.d.
-   \[27\] Jeffrey Lewis. Urs Tinner. Arms Control Wonk, 2006.
-   \[28\] Nuclear Threat Initiative. Libya Nuclear Overview. Nuclear Threat Initiative, 2015.
-   \[29\] William Burr. The United States and South Korea’s Nuclear Weapons Program, 1974-1976. Wilson Center, 2017.
-   \[30\] Von Erich Follath. Evidence Points to Syrian Push for Nuclear Weapons. Der Spiegel, 2015.
-   \[31\] Treaty on the Non-Proliferation of Nuclear Weapons (NPT). 1968.
-   \[32\] The Structure and Content of Agreements between the Agency and States Required in Connection with the Treaty on the Non-proliferation of Nuclear Weapons (INFCIRC/153(Corrected)). International Atomic Energy Agency, 1972. 8–9.
-   \[33\] International Atomic Energy Agency. Statute. International Atomic Energy Agency, 1956. XII.C.
-   \[34\] International Atomic Energy Agency. The Agency’s Budget Update for 2023. International Atomic Energy Agency, 2022. 11.
-   \[35\] Amos Harel and Aluf Benn. No Longer a Secret: How Israel Destroyed Syria’s Nuclear Reactor. Haaretz, 2018.
-   \[36\] Model Protocol Additional to the Agreement(s) Between State(s) And the International Atomic Energy Agency for the Application of Safeguards (INFCIRC/540). International Atomic Energy Agency, 1997.
-   \[37\] Interim Agreement Between the United States of America and the Union of Socialist Soviet Republics on Certain Measures with Respect to the Limitation of Strategic Offensive Arms (SALT I). 1972.
-   \[38\] Treaty Between the United States of America and the Union of Socialist Soviet Republics on the Limitation of Anti-Ballistic Missile Systems (ABM Treaty). 1972\. 5.
-   \[39\] Jeffrey Lewis. IC Can’t Verify Moscow Treaty. Arms Control Wonk, 2004.
-   \[40\] Nuclear Threat Initiative. Nuclear Testing. Nuclear Threat Initiative, n.d.
-   \[41\] The Preparatory Commission for the Comprehensive Nuclear-Test-Ban Treaty Organization (CTBTO). Business Continuity: Annual Report 2020. The Preparatory Commission for the Comprehensive Nuclear-Test-Ban Treaty Organization (CTBTO), 2021. 90.
-   \[42\] Treaty Between the United State of America and the Union of Soviet Socialist Republics on Underground Nuclear Explosions for Peaceful Purposes (PNE Treaty). 1976.
-   \[43\] The Comprehensive Nuclear Test-Ban Treaty (CTBT). 1996.
-   \[44\] Protocol to the Comprehensive Nuclear Test-Ban Treaty. 1996.
-   \[45\] Philipp C Bleek. “When Did (and Didn’t) States Proliferate? Chronicling the Spread of Nuclear Weapons. Discussion Paper (Cambridge, MA: Project on Managing the Atom, Belfer Center for Science and International Affairs, Harvard Kennedy School and the James Martin Center for Nonproliferation Studies, Middlebury Institute of International Studies, Monterey, CA), 2017.
-   \[46\] International Atomic Energy Agency. Status List: Conclusion of Safeguards Agreements, Additional Protocols and Small Quantities Protocols. International Atomic Energy Agency, 2022.
-   \[47\] United States Government Accountability Office. Nuclear Nonproliferation: IAEA Has Strengthened Its Safeguards and Nuclear Security Programs, but Weaknesses Need to Be Addressed. United States Government Accountability Office, 2005.
-   \[48\] International Atomic Energy Agency Director General. NPT Safeguards Agreement with the Islamic Republic of Iran. International Atomic Energy Agency, 2022. 5–6.
-   \[49\] International Atomic Energy Agency. Safeguards Statement for 2019. International Atomic Energy Agency, 2020.
-   \[50\] International Atomic Energy Agency. Safeguards Statement for 2021. International Atomic Energy Agency, 2022. 1, 8.
-   \[51\] Nuclear Threat Initiative. Iraq Nuclear Overview. Nuclear Threat Initiative, 2015.
-   \[52\] Nuclear Threat Initiative. Syria Nuclear Overview. Nuclear Threat Initiative, 2018.
-   \[53\] Nuclear Threat Initiative. Iran Nuclear Overview. Nuclear Threat Initiative, 2020.
-   \[54\] William C. Potter et al. Tito’s Nuclear Legacy. Bulletin of the Atomic Scientists 56, no. 2: 63-70, 2000.
-   \[55\] Nuclear Threat Initiative. North Korea Nuclear Overview. Nuclear Threat Initiative, 2018.
-   \[56\] International Atomic Energy Agency Board of Governors. Implementation of the NPT safeguards agreement in the Syrian Arab Republic. International Atomic Energy Agency, 2011.
-   \[57\] Avner Cohen and William Burr. Revisiting the 1979 VELA Mystery: A Report on a Critical Oral History Conference. Wilson Center, 2020.
-   \[58\] The Preparatory Commission for the Comprehensive Nuclear-Test-Ban Treaty Organization (CTBTO). The CTBT Verification Regime: Monitoring the Earth for Nuclear Explosions. The Preparatory Commission for the Comprehensive Nuclear-Test-Ban Treaty Organization (CTBTO), 2022.
-   \[59\] Nuclear Threat Initiative. Israel Nuclear Overview. Nuclear Threat Initiative, 2014.
-   \[60\] Nuclear Threat Initiative. South Africa Nuclear Overview. Nuclear Threat Initiative, 2015.
-   \[61\] Our World in Data. Number of nuclear weapons tests, 1945 to 2019. Our World in Data, 2022.
-   \[62\] Nuclear Threat Initiative. Brazil’s Nuclear Ambitions, Past and Present. Nuclear Threat Initiative, 2006.
-   \[63\] International Energy Associates Limited. Review of the Negotiating History of the IAEA Safeguards Document INFCIRC/153, Volume I: Chapters 1.0-3.0. International Energy Associates Limited, 2600 Virginia Avenue, N.W., Suite 1000, Washington, D.C. 20037, 1984. xi, 4.
-   \[64\] Elisabeth Roehrlich. Negotiating Verification: International Diplomacy and the Evolution of Nuclear Safeguards, 1945–1972. Diplomacy & Statecraft, 29:1, 29-50, 2018.
-   \[65\] Rose Gottemoeller. Negotiating the new START Treaty. Cambria Press, 2021. 63.
-   \[66\] Michael D. Rosenthal et al. Review of the Negotiation of the Model Protocol Additional to the Agreement(s) Between State(s) and the International Atomic Energy Agency for the Application of Safeguards, INFCIRC/540 (Corrected), Volume I/III, Setting the Stage: 1991-1996. 2010\. D, 6, 27, 53.
-   \[67\] Federation of American Scientists. Article-by-article Analysis of the Treaty Text. Federation of American Scientists, 1998.
-   \[68\] Michael D. Rosenthal et al. Review of the Negotiation of the Model Protocol Additional to the Agreement(s) Between State(s) and the International Atomic Energy Agency for the Application of Safeguards, INFCIRC/540 (Corrected), Volume II/III, IAEA Committee 24, Major Issues Underlying the Model Additional Protocol (1996-1997). 2010\. 20, 56, 64.
-   \[69\] John Carlson et al. Nuclear Safeguards as an Evolutionary System. The Nonproliferation Review, 6(2), 109-117, 1999. 112.
-   \[70\] John Carlson et al. The IAEA’s Safeguards System as the Non-Proliferation Treaty’s Verification Mechanism. Nuclear Threat Initiative, 2020.
-   \[71\] Rafael Grossi et al. The Politics of Safeguards. Carnegie Endowment for International Peace, 2015. 4.
-   \[72\] Saif M Khan. The Semiconductor Supply Chain: Assessing National Competitiveness. Center for Security and Emerging Technology, 2021.
-   \[73\] Treaty for the Prohibition of Nuclear Weapons in Latin America and the Caribbean (Treaty of Tlatelolco). 1967\. 13.
-   \[74\] Treaty on the Southeast Asia Nuclear Weapon-Free Zone (Bangkok Treaty). 1995.
-   \[75\] International Atomic Energy Agency. Fact Sheets. International Atomic Energy Agency, 2022.
-   \[76\] Agreement of 13 December 1991 between the Republic of Argentina, the Federative Republic of Brazil, the Brazilian-Argentine Agency for Accounting and Control of Nuclear Materials and the International Atomic Energy Agency for the Application of Safeguards. International Atomic Energy Agency, 2000.
-   \[77\] South Pacific Nuclear-Free Zone (Treaty of Rarotonga). 1985.
-   \[78\] International Atomic Energy Agency. IAEA Safeguards: Serving Nuclear Non-Proliferation. International Atomic Energy Agency, 2021. 14.
-   \[79\] Ankit Panda. Exclusive: Revealing Kangson, North Korea’s First Covert Uranium Enrichment Site. The Diplomat, 2018.
-   \[80\] International Atomic Energy Agency. Communication dated 3 June 2022 received from the Permanent Mission of the Islamic Republic of Iran to the Agency. International Atomic Energy Agency, 2022.
-   \[81\] David Albright and Paul Brannan. If Not Now, When? Time for an IAEA Special Inspection in Syria. Institute for Science and International Security, 2010.
-   \[82\] Leonard S Spector. “Repentant Nuclear Proliferants. Foreign Policy, no. 88 (1992): 21–37, 1992. 23, 35.
-   \[83\] International Atomic Energy Agency. Information Collection and Evaluation. International Atomic Energy Agency, 2017.
-   \[84\] International Atomic Energy Agency. IAEA Safeguards: Aims, Limitations, Achievements. International Atomic Energy Agency, 1983. 36.
-   \[85\] Michael E. O’Hanlon et al. Experts assess the nuclear Non-Proliferation Treaty, 50 years after it went into effect. The Brookings Institution, 2020.
-   \[86\] John Carlson et al. Detection of Undeclared Nuclear Activities: Does the IAEA Have the Necessary Capabilities? Australian Safeguards and Non-Proliferation Office, RG Casey Bldg, John McEwen Crescent, Barton, ACT 0221, Australia, 2006. 6.
-   \[87\] International Atomic Energy Agency Director General. Implementation of the NPT Safeguards Agreement of the Socialist People’s Libyan Arab Jamahiriya. International Atomic Energy Agency, 2004. 2.
-   \[88\] David Fischer. The DPRK’s Violation of its NPT Safeguards Agreement with the IAEA. International Atomic Energy Agency, 1997.
-   \[89\] Jeffrey Lewis. NCRI Did Not Discover Natanz. Arms Control Wonk, 2006.
-   \[90\] Ian Traynor and Julian Borger. Iran Admits Secret Uranium Enrichment Plant. The Guardian, 2009.
-   \[91\] Tom DiChristopher. Netanyahu says files show Iran lied ‘big time’ about developing nuclear weapons. CNBC, 2018.
-   \[92\] Amy Zegart. Meet the Nuclear Sleuths Shaking Up U.S. Spycraft. Politico, 2022.
-   \[93\] Andrew Koch. Yugoslavia’s nuclear legacy: Should we worry? The Nonproliferation Review, 4(3), 123-128, 1997.
-   \[94\] Nuclear Threat Initiative. South Korea Nuclear Overview. Nuclear Threat Initiative, 2015.
-   \[95\] David Albright. Iraq’s Programs to Make Highly Enriched Uranium and Plutonium for Nuclear Weapons Prior to the Gulf War. Institute for Science and International Security, 2002.
-   \[96\] Daniel Coats. Director of National Intelligence Daniel Coats on Russia’s Intermediate-Range Nuclear Forces (INF) Treaty Violation. Office of the Director of National Intelligence, 2018.
-   \[97\] U.S. Department of State. Adherence to and Compliance with Arms Control, Nonproliferation, and Disarmament Agreements and Commitments. U.S. Department of State, 2019.
-   \[98\] Michael R Gordon. As One Arms Treaty Falls Apart, Others Look Shakier. Wall Street Journal, 2018.
-   \[99\] Colin L Powell. Statement on the Achievement of the Final Reductions under the START Treaty. U.S. Department of State, 2001.
-   \[100\] Nuclear Threat Initiative. START I. Nuclear Threat Initiative, 2011.
-   \[101\] U.S. Department of State. New START Treaty. U.S. Department of State, 2023.
-   \[102\] Amy F Woolf. Russian Compliance with the Intermediate Range Nuclear Forces (INF) Treaty: Background and Issues for Congress. Congressional Research Service, 2019.
-   \[103\] International Atomic Energy Agency. COVID-19: latest IAEA updates. International Atomic Energy Agency, 2020.
-   \[104\] Shannon Bugos. Russia Further Pauses New START Inspections. Arms Control Association, 2022.
-   \[105\] Ronald Reagan. Message to the Congress: Transmitting a Report on Soviet Noncompliance With Arms Control Agreements. Reagan Library, 1987.
-   \[106\] Federation of American Scientists. Soviet Statement in Connection with the Third Review of the Treaty Between the United States of America and the Union of Soviet Socialist Republics on the Limitation of Anti-Ballistic Missile Systems. Federation of American Scientists, 1988.
-   \[107\] G.C. Delcoigne et al. 10 TBT: The Test Ban Treaty. International Atomic Energy Agency, 1973. 17.
-   \[108\] Universiteit Utrecht. Radiocarbon Dating. Universiteit Utrecht, n.d.
-   \[109\] Jeffrey Lewis. U.S.-Russia Test Site Transparency Measures: Avoiding a Return to the Arms Race. Nuclear Threat Initiative, 2018.
-   \[110\] International Atomic Energy Agency. IAEA Safeguards in 2019: Verifying the peaceful use of nuclear material. International Atomic Energy Agency, 2020.
-   \[111\] International Atomic Energy Agency. IAEA Safeguards in 2020: Verifying the peaceful use of nuclear material. International Atomic Energy Agency, 2021.
-   \[112\] Alex Woodie. As Cloud Grows, Is Resistance to AWS Futile? Datanami, 2019.
-   \[113\] Mark Haranas. AWS, Google, Microsoft Are Taking Over The Data Center Market. CRN Magazine, 2021.
-   \[114\] Erich Strohmaier et al. Top500. Top500, 2022.
-   \[115\] Taiwan Semiconductor Manufacturing Company Limited. TSMC Fabs. Taiwan Semiconductor Manufacturing Company Limited, 2021.
-   \[116\] Samsung Group. Global Manufacturing Sites. Samsung Group, 2022.
-   \[117\] Intel Corporation. How Many Manufacturing Fabs Does Intel Have? Intel Corporation, 2022.
-   \[118\] Semiconductor Manufacturing International Corporation. Company Information. Semiconductor Manufacturing International Corporation, 2020.
-   \[119\] International Atomic Energy Agency. The Present Status of IAEA Safeguards on Nuclear Fuel Cycle Facilities. International Atomic Energy Agency, 1980. 19.
-   \[120\] Sasha Henriques. A Day in the Life of a Safeguards Inspector. International Atomic Energy Agency, 2016.
-   \[121\] Aakanksha Chowdhery and Sharan Narang. PaLM: Scaling Language Modeling with Pathways. 2022.
-   \[122\] Omid Rahmat. Jon Peddie’s 2022 GPU Roundup. Graphic Speak, 2022.
-   \[123\] Timothy Prickett Morgan. Datacenter Becomes NVIDIA’s Largest Business. The Next Platform, 2022.
-   \[124\] Jr Sargent, John F. Global Research and Development Expenditures: Fact Sheet. Congressional Research Service, 2022.
-   \[125\] Todd Gillespie. Energy Costs Set to Reach Record 13This Year. Bloomberg, 2022.
-   \[126\] International Atomic Energy Agency. Use of Nuclear Material Accounting and Control for Nuclear Security Purposes at Facilities. IAEA Nuclear Security Series No. 25-G, Implementing Guide, International Atomic Energy Agency, 2015.

## Appendix A The nuclear-AI analogy

M&V systems for AI would face some similar challenges as (some) M&V systems for nuclear arms control, including:[^108]

-   •
    
    _Dual-use equipment and facilities:_ Much of the equipment and facilities that could be used to violate an agreement can also be used for legitimate purposes[^109], so M&V must be able to catch late-stage misuse of relevant equipment and facilities.
    
-   •
    
    _Sensitive information:_ Dual-use equipment and facilities involve sensitive information[^110] even if they are being used in compliance with the treaty.
    
-   •
    
    _Regulation of both government and corporate activity:_ Governments and businesses perform activities that (may) need restrictions for effective M&V.[^111]
    
-   •
    
    _Bilateral or multilateral negotiations:_ Treaty scope is not necessarily limited to either just bilateral or just multilateral treaties.[^112]
    
-   •
    
    _Need for high robustness:_ States might come to see defection as highly valuable, so a reliable M&V system might need to be robust against major state efforts to hide violations.
    
-   •
    
    _Accounting:_ Verified accounting (of uranium in one case, and of high-end, AI-specialized chips in the other case) can help with treaty verification.
    

However, there are also major differences between these verification challenges, including:

-   •
    
    _Degree of perceived risk:_ Nuclear arms control M&V was negotiated after clear demonstrations of the risks posed by nuclear weapons, while some potential AI risks are currently more speculative.
    
-   •
    
    _Efficacy of environmental sampling:_ The use of centrifuges to produce weapons-grade uranium scatters unique particles that can be detected from some distance; there are no obvious analogues for AI.
    
-   •
    
    _Verification of information technology use:_ M&V for AI may need to be able to catch certain defections just based on (limited) access to source code, AI hardware, and/or ML models. Nuclear arms control M&V has not had to do that; it offers no obvious analogues to software or hardware-centered verification.
    
-   •
    
    _Supply chain concentration:_ The supply chain of high-end computer chips is highly concentrated \[[72](#bib.bib72)\], while uranium sources, their processing equipment, and nuclear facilities are relatively decentralized. Still, in both cases, there are challenging steps in the supply chain.
    

Additionally, it is not clear whether certain other factors are similarities or differences, including:

-   •
    
    _Scale of verification activities needed:_ The amount and scope of infrastructure and equipment that need to be inspected for nuclear arms control is low enough for verification to be considered affordable; it is unclear if the same will be true for AI.
    
-   •
    
    _Amount of sensitive information needed to verify compliance:_ Nuclear arms control agreements are verified without inspectors getting access to much of the valuable R&D information involved (i.e. R&D of centrifuges, missiles, and bombers); it is unclear whether similarly IP-protecting M&V will be feasible for AI.
    

## Appendix B M&V in Nuclear-Weapon-Free-Zone treaties and in agreements with North Korea and Iran

This appendix argues that Nuclear-Weapon-Free-Zone ("NWFZ") treaties and nonproliferation agreements with North Korea and Iran are mainly or entirely verified by [CSAs (sometimes with APs)](https://sometimes%20with%20APs\)%5D\(#3-2-m&v-for-horizontal-nonproliferation-agreements-17) implemented by the IAEA, rather than by distinct M&V systems.

### B.1 NWFZ Treaties

Five treaties ban a wide range of nuclear weapon activities, including developing nuclear weapons, among state parties in a compact geographic region. Their primary verification mechanisms are standard IAEA safeguards.

-   •
    
    Three treaties explicitly specify that state parties must adopt CSAs with the IAEA (or equivalent agreements), and one explicitly specifies that they must also adopt APs.[^113]
    
-   •
    
    The treaties covering Latin America and Southeast Asia are less precise in their verification requirements,[^114] but they seem to be interpreted as also mandating (at least) CSAs with the IAEA as their primary verification systems.[^115]
    

Supplementing these IAEA safeguards, each of these treaties other than the Central Asian one also establishes a new regional, international organization. These organizations are tasked with helping implement the agreements, partly by carrying out a few verification mechanisms[^116]. None of these mechanisms are beyond the authority of IAEA safeguards, so these organizations at most add redundancy and regional legitimacy to standard IAEA verification.

### B.2 Agreements with North Korea and Iran

Nations have reached a few agreements in response to worries that particular nations were pursuing nuclear weapons.[^117] The most prominent of these (near-)agreements appear to have been[^118]: the Joint Declaration of South and North Korea on the Denuclearization of the Korean Peninsula, the U.S.-D.P.R.K. Agreed Framework, and the Joint Comprehensive Plan of Action (JCPOA, i.e. the "Iran Deal").

These agreements tend to not break new ground in terms of M&V mechanisms. The Joint Declaration would have involved bilateral inspections, but states failed to reach agreement on its implementation. The Agreed Framework just involved agreement to [CSAs with the IAEA](#S3.SS2 "3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"). And, while the JCPOA involved several unusual verification measures, these were mostly [standard monitoring mechanisms](#S3.SS2.SSS2 "3.2.2 IAEA verification in declared nuclear facilities ‣ 3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") applied more frequently or at more types of facilities. Specifically, under the JCPOA \[[17](#bib.bib17)\]:

-   •
    
    There was one novel monitoring mechanism: Iran would have a monitored procurement channel, meaning it would have to notify (and get approval from) the UN Security Council (acting mostly through a commission) to engage in a wide range of nuclear-related, international economic activities (e.g. equipment imports, training);
    
-   •
    
    Iran would indefinitely adopt an Additional Protocol[^119];
    
-   •
    
    The IAEA would verify that some nuclear reactor would be reconstructed in a way that made its products less suitable for nuclear weapon production; and
    
-   •
    
    The IAEA would extend its usual safeguards to cover additional types of facilities.[^120]
    

## Appendix C How Additional Protocols change M&V processes at declared nuclear facilities

Compared to non-nuclear-weapon states that have only adopted CSAs, states that have also adopted APs have fairly similar types of safeguards in their declared nuclear facilities. After all, APs are largely designed to improve the IAEA’s capacity to identify _undeclared_ nuclear facilities.

Still, there are several notable differences in safeguards at known facilities \[[17](#bib.bib17)\]; in contrast to states that have only adopted CSAs, states that have also adopted APs…

-   •
    
    …receive relaxed safeguards ("integrated safeguards") at declared facilities, if and after the IAEA has confidently concluded that the state has no undeclared nuclear facilities.[^121]
    
-   •
    
    …agree to grant IAEA inspectors access with 2 hours notice (or less, "in exceptional circumstances") for carrying out inspections that were authorized under CSAs. The previous requirement was 24 hours.
    
-   •
    
    …agree to enable the IAEA to non-routinely verify that nuclear material is not being diverted from uranium mines, mills, or certain wastes (not covered by CSAs).[^122][^123]
    
-   •
    
    …agree to inform the IAEA about quantities of nuclear materials that were previously small enough to be exempted (separately from Small Quantities Protocols).
    

## Appendix D The IAEA’s inability to verify the absence of undeclared nuclear facilities under Comprehensive Safeguards Agreements

Overall, CSAs give the IAEA very limited abilities to verify the absence of undeclared nuclear facilities \[[17](#bib.bib17)\].

Under CSAs, the IAEA has access to the following sources of information[^124][^125][^126], which can help it identify locations with a higher-than-baseline chance of hosting secret nuclear facilities:

-   •
    
    Voluntary reports from third parties, especially national intelligence agencies
    
-   •
    
    States’ self-reporting on their own nuclear facilities
    
-   •
    
    Satellite images (e.g., images of a building whose size, location, heat[^127], security, and installations are consistent with being a uranium enrichment plant \[[79](#bib.bib79)\])
    
-   •
    
    Other open-source information (e.g., local news reports)
    

Typically, all of the above sources of evidence are just suggestive[^128]; if they rouse the IAEA’s suspicions about some location, the IAEA still needs more definitive evidence to back up confident accusations of non-compliance. However, CSAs only authorize the IAEA to use the following methods for resolving suspicions about undeclared facilities:

-   •
    
    _Special inspections:_ Officially, under CSAs, the IAEA may make special inspections (potentially at locations that host undeclared facilities) if it considers other sources of evidence insufficient for verifying compliance. However, in practice, the IAEA has a restrictively high bar for conducting special inspections: special inspections are widely considered appropriate only when the IAEA already has credible evidence of a safeguards violation[^129]. In line with this, the IAEA rarely conducts special inspections[^130].
    
-   •
    
    _Requests for additional information:_ For example, the IAEA may ask that a state provide explanations or documentation about some construction activities. These requests have sometimes been useful despite the potential for deception; states have sometimes responded in ways the IAEA was able to falsify[^131], and states have sometimes refused to respond at all[^132], suggesting that it can be difficult for states to craft credible cover stories.
    

Despite their occasional successes, special inspection authorities and requests for additional information are highly limited, so the IAEA has very limited means for confirming or disconfirming its suspicions about undeclared nuclear facilities in states that only have CSAs.

## Appendix E The role of intelligence agencies in identifying undeclared nuclear facilities

It appears that, unofficially, the IAEA identifies suspect locations mainly through voluntary tips from national intelligence agencies (and perhaps also from whistleblowers). These tips from intelligence agencies appear to be irreplaceable for the IAEA’s ability to identify potential undeclared nuclear facilities. These conclusions are supported by several sources of evidence:

Expert opinion: Experts appear to agree that intelligence agencies play an irreplaceable and primary role in detecting undeclared nuclear facilities.[^133]

-   •
    
    Leonard Spector, then-director of the Nuclear Non-Proliferation Project at the Carnegie Endowment, explained, "U.S. intelligence \[…\] has been the principal, if announced, mechanism for detecting \[Non-Proliferation\] treaty violations…" \[[82](#bib.bib82)\].
    
-   •
    
    Michael O’Hanlon, Director of Research of the Foreign Policy program at the Brookings Institution, writes, "\[T\]he so-called "Additional Protocol" has created the right for inspectors to go to places where they suspect monkey business, even if those sites are not officially declared by the country in question. This arrangement tends to work only if national intelligence capabilities, and/or whistleblowers, provide information about suspicious activities. But at that point, inspectors can be more effective than in the years before the Additional Protocol concept was developed and legitimated" \[[85](#bib.bib85)\].
    
-   •
    
    A report from the Australian Safeguards and Non-Proliferation Office asserts, "there is no doubt that national intelligence information will continue to have a vital role in the detection of undeclared nuclear activities" \[[86](#bib.bib86)\].
    
-   •
    
    Across a wide range of relevant publications (those read for this research), there is no mention of experts expressing contrary opinions.
    

Case studies: National intelligence agencies have historically had a primary role in prompting IAEA investigations of undeclared nuclear facilities. Of the 4 states in which the IAEA has investigated what turned out to be undeclared nuclear facilities (Syria, North Korea, Iran, and Iraq[^134]), there have been 3 states in which the IAEA began to investigate the facilities mainly or entirely because of intelligence agency tips, while there have been no states in which the IAEA began to investigate them mainly or entirely through its own CSA or AP-authorized processes.[^135]

-   •
    
    In 3 cases (Syria, North Korea, and Iran), the IAEA mainly or entirely learned of the undeclared facilities from intelligence agency tips.
    
    -   –
        
        Western intelligence agencies notified the IAEA of an undeclared nuclear reactor (after Israel bombed it) and three additional suspected facilities in Syria, which the IAEA then investigated \[[56](#bib.bib56)\]\[[35](#bib.bib35)\].
        
    -   –
        
        The IAEA investigated undeclared nuclear sites in North Korea based on U.S. tips \[[88](#bib.bib88)\].
        
    -   –
        
        The IAEA investigated the first two undeclared nuclear facilities in Iran based on tips from intelligence agencies.[^136]
        
    -   –
        
        Then, Iran notified the IAEA of its other undeclared facility (FFEP) shortly before Western states announced it. Reportedly, "the letter was only sent after the Iranian government discovered the secret plant had been discovered by western intelligence" \[[90](#bib.bib90)\].
        
    -   –
        
        The IAEA has also investigated additional undeclared nuclear activities in Iran \[[48](#bib.bib48)\]. It does not report having been first to spot any of the relevant locations, and at least some of these investigations appear to have been based on tips from Western intelligence \[[91](#bib.bib91)\].
        
    
-   •
    
    The other case was Iraq, where the IAEA was acting with UNSC-granted authorities well beyond its usual ones (due to Iraq’s defeat in the Gulf War).
    

Plausible mechanism: Intelligence agencies have uniquely strong intelligence gathering capabilities, which could explain their unique contributions.[^137]

## Appendix F Details on track records of nuclear arms control M&V

No state has attempted to divert a significant quantity of nuclear material from a facility under CSA safeguards.

-   •
    
    We can draw this conclusion on the grounds that there is no mention of such diversion across a varied and fairly comprehensive range of materials on relevant cases.[^138]
    
-   •
    
    The IAEA recently found that Iran has some undeclared nuclear material \[[48](#bib.bib48)\]. However, there appears to be no public evidence that it came from declared facilities, nor that the amounts of nuclear material involved were significant for proliferation. Additionally, the IAEA’s \[[50](#bib.bib50)\] subsequent annual safeguards statement concluded that Iran’s "declared nuclear material remained in peaceful activities."
    
-   •
    
    There have been a few cases (e.g., Yugoslavia, South Korea) of tiny amounts of nuclear materials (reportedly) having been diverted from facilities that were under CSA safeguards. However, the relevant quantities were far below the "significant quantities" of diversion that CSA safeguards are designed to notice \[[93](#bib.bib93)\]\[[94](#bib.bib94)\].
    
-   •
    
    Iraq and Yugoslavia planned to divert nuclear materials that were under CSA safeguards, but they never executed these plans \[[54](#bib.bib54)\]\[[95](#bib.bib95)\]\[[51](#bib.bib51)\].[^139]
    

The U.S. likely discovered Russia’s violation of the INF Treaty before it offered Russia a substantial strategic advantage, and the U.S. plausibly had reliable monitoring throughout.

-   •
    
    According to a statement from the U.S. Director of National Intelligence (consistent with a State Department report), on one hand, the U.S. took about 5 years after Russia began the missile’s development to raise accusations \[[96](#bib.bib96)\]\[[97](#bib.bib97)\].
    
-   •
    
    On the other hand,
    
    -   –
        
        the statement suggests the missile’s testing program was not completed for another 2 years;
        
    -   –
        
        the statement suggests the missile may have been impossible to identify as a violation until later stages of this testing program; and
        
    -   –
        
        U.S. officials reportedly stated—5 years after the initial U.S. allegations—that Russia had still deployed fewer than 100 of the violating missiles (less than one fifteenth the number of intermediate-range missiles the U.S.S.R. had before the treaty) \[[98](#bib.bib98)\].
        
    

Beside the INF Treaty incident, the U.S. has mostly confirmed the U.S.S.R./Russia’s compliance across the INF Treaty, START I, and New START.

-   •
    
    The U.S. Director of National Intelligence spoke warmly of initial compliance on the INF Treaty: "Together, we eliminated over 2,600 prohibited missiles" \[[96](#bib.bib96)\].
    
-   •
    
    In 2001, the U.S. State Department announced, "The \[START I’s\] final ceilings came into effect today, and they have been met" \[[99](#bib.bib99)\].
    
-   •
    
    Agreeing with the above, NTI’s page on the START I mentions no accusations of serious non-compliance \[[100](#bib.bib100)\].
    
-   •
    
    The U.S. State Department states, "Although the United States has raised implementation-related questions and concerns with the Russian Federation through diplomatic channels and in the context of the BCC, the United States has determined annually since the treaty’s entry into force, across multiple administrations, the Russian Federation’s compliance with its treaty obligations" \[[101](#bib.bib101)\].
    

Russia has made several relatively minor or tenuous allegations of noncompliance with the INF Treaty, START I, and New START.

-   •
    
    In 2001, in the context of START I, Russia disputed whether the U.S. had destroyed enough of the stages of one type of missile \[[100](#bib.bib100)\]. Russia also alleges that several non-secret U.S. missile-related activities violate the INF Treaty. Some of Russia’s allegations—like that U.S. drones count as cruise missiles—appear tenuous \[[102](#bib.bib102)\].
    
-   •
    
    Additionally, the U.S. and Russia suspended New START inspections with the COVID-19 pandemic (unlike the IAEA, which continued its inspections) \[[103](#bib.bib103)\]\[[104](#bib.bib104)\]. Then, during the Russian invasion of Ukraine, Russia suspended its participation in New START altogether. However, whether or not this is noncompliance, it is not a case of subtle circumvention of the M&V system.
    

In U.S.-U.S.S.R./Russia nuclear arms control treaties other than the above, parties made non-compliance accusations, but they did not raise accusations of massive non-compliance for ratified treaties.

-   •
    
    The U.S. and the U.S.S.R. accused each other of developing radar systems in violation of the Anti-Ballistic Missile Treaty. Both parties also claimed other less specific or clear violations \[[105](#bib.bib105)\]\[[106](#bib.bib106)\].
    
-   •
    
    Reagan accused the Soviets of having "violated the \[SALT I\] prohibition on the use of former ICBM facilities" \[[105](#bib.bib105)\].
    
-   •
    
    Reagan accused the Soviets of violating core provisions (including strategic arms limits) of the SALT II Treaty, but he also noted this treaty was never ratified and would have expired if it had been \[[105](#bib.bib105)\].
    

There have been no significant, known violations of nuclear test ban treaties, except possibly in the Vela incident.

-   •
    
    A wide range of sources[^140] make no mention of serious accusations of violations other than the [Vela incident](#S4.SS3 "4.3 Nuclear Test Ban M&V Systems’ Track Records ‣ 4 Track Records of Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").
    
-   •
    
    An article published on the IAEA bulletin on the 10th anniversary of the Partial Test Ban Treaty states, "The record of compliance with the PTB is generally considered to be good. There has so far been no complaint of a significant breach by any party" \[[107](#bib.bib107)\].
    
-   •
    
    Radioactive carbon in the atmosphere peaked right around the signing of the Partial Test Ban Treaty \[[108](#bib.bib108)\].
    
-   •
    
    Additionally, the CTBT was signed in 1996, and only a few non-signatories are known to have conducted nuclear tests since then \[[61](#bib.bib61)\].
    
-   •
    
    Reagan accused the Soviets of violating the Threshold Test Ban Treaty, but this was before either party had ratified the treaty, and concerns were later resolved \[[105](#bib.bib105)\]\[[109](#bib.bib109)\].
    

## Appendix G How verification of AI chip accounts could be implemented

### G.1 Introduction

For verifying certain international agreements on AI, it would be helpful (though not sufficient) to be able to verify the quantity, location, and integrity[^141] of all cutting-edge, AI-specialized chips[^142], at least well enough to detect very large numbers of these chips that have been tampered with or are kept secret. Shavit \[[1](#bib.bib1)\] describes one way AI chip accounts could fit into a broader verification regime, and he briefly discusses how these accounts could be verified. This appendix aims to provide a detailed description of how AI chip accounts could be implemented with multiple layers of verification, mainly using methods with close analogues in nuclear arms control verification.

This potential implementation is not a policy suggestion. Instead, it is described to show that reliable verification of AI chip accounts _could_ be done mainly with methods that have [successful](#S4.SS1 "4.1 NPT M&V systems’ Track Records ‣ 4 Track Records of Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") historical analogues. We focus on these methods here because we have more information about their political feasibility, but that is insufficient to make an overall recommendation.

To avoid repetition, this appendix assumes basic familiarity with nuclear M&V methods, which are described in [a previous section](#S2 "2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").

### G.2 Background treaty obligations and verification goals

This appendix is about the verification of a hypothetical international agreement that obliges state parties to the following:

-   •
    
    Chip features: Ensure that cutting-edge, AI-specialized chips ("AI chips") in the state’s territory continually have certain design (and/or assembly) features, including a [unique identifier](#S2.SS2.SSS3 "2.2.3 Unique identifiers ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"); and
    
-   •
    
    AI chip accounting: Notify and regularly update some international organization of the existence, locations, technical specifications, and [unique identifiers](#S2.SS2.SSS3 "2.2.3 Unique identifiers ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") of cutting-edge AI chips and of the machines that make them.
    
-   •
    
    Location restrictions on data-center-quality AI chips: Keep data-center-quality AI chips in production facilities, data centers, storage facilities, elimination facilities[^143], or in (time-limited) transit between these locations.[^144]
    

This appendix assumes that the main types of violations this system is aiming to detect are: the possession of many cutting-edge AI chips at undeclared locations, and the possession of many cutting-edge AI chips that lack required design features. The problem of detecting these violations can be broken down into the following two subproblems:

1.  1.
    
    Verify that there are not many[^145] cutting-edge AI chips being used at undeclared locations; and
    
2.  2.
    
    Verify that, of the cutting-edge AI chips at reported locations, not many lack required design features.
    

### G.3 Detecting efforts to get cutting-edge AI chips to undeclared locations

To verify that there are not many cutting-edge AI chips being used at undeclared locations, one approach is: verify that these chips could not have reached undeclared locations, on the grounds that any attempt at secretly producing cutting-edge AI chips or removing them from their declared locations would have been detected. This section describes how that detection could be done, for each potential method of secretly producing or moving these chips.

First, AI chips could be secretly produced by accurately reporting the existence of chip-making machines but under-reporting production levels. To detect this, one could:

-   •
    
    Have in-line instrumentation be installed on chip-making machines (or power systems) to monitor production levels;
    
-   •
    
    Monitor relevant chips fabrication facilities’ ("fabs’") [procurement activities](#S2.SS3.SSS4 "2.3.4 Procurement monitoring ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), looking for undeclared purchases of chip manufacturing materials; and
    
-   •
    
    Establish perimeter portal continuous monitoring at relevant fabs, looking for undeclared shipments of chips out of the fabs.
    

Alternatively, AI chips could be secretly produced by undeclared chip-making machines at declared fabs. To detect this, one could:

-   •
    
    Carry out inspections at relevant fabs, implemented like the "undeclared item inspections" described in [the next section](#A7.SS4 "G.4 Detecting efforts to host cutting-edge AI chips at undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (except in this case, inspectors would be looking for undeclared chip-making machines, rather than undeclared chips);
    
-   •
    
    Implement [design information verification](#S2.SS2.SSS4 "2.2.4 Design information verification ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") at relevant fabs, to detect secret rooms;
    
-   •
    
    Monitor relevant fabs’ [procurement activities](#S2.SS3.SSS4 "2.3.4 Procurement monitoring ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), looking for undeclared purchases of chip manufacturing materials or chip-making machines (potentially along with video surveillance and [perimeter monitoring](#S2.SS2.SSS5 "2.2.5 Perimeter portal continuous monitoring ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), for especially centralized suppliers); and
    
-   •
    
    Establish [perimeter portal continuous monitoring](#S2.SS2.SSS5 "2.2.5 Perimeter portal continuous monitoring ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") at relevant fabs, looking for undeclared shipments of chips out of the fabs or of chip-making machines or machine components into the fabs.
    

Thirdly, AI chips could theoretically be secretly produced at undeclared fabs. To detect this, one could:

-   •
    
    Use [national technical means](#S2.SS3.SSS1 "2.3.1 National technical means ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") to look for signs of secret fab construction;
    
-   •
    
    [Monitor the sales](#S2.SS3.SSS4 "2.3.4 Procurement monitoring ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") of fab suppliers, looking for undeclared purchases of chip manufacturing materials or chip-making machines; and
    
-   •
    
    Use [challenge inspections](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") to resolve suspicions about particular locations.
    

Instead of secretly producing cutting-edge AI chips, an adversary could seek to secretly divert cutting-edge AI chips from their reported locations at data centers and storage facilities. To detect this, one could:

-   •
    
    Carry out "diversion detection inspections"[^146] at declared data centers and storage facilities (as described by Shavit \[[1](#bib.bib1)\], these could consist of inspectors specifying a random sample of unique identifiers that are reportedly at some facility, facility operators providing access to the corresponding AI chips, and then inspectors checking that the reported chip is present[^147]); and
    
-   •
    
    Use video surveillance at declared data centers and storage facilities, as additional measures to detect diversion.
    

Alternatively, an adversary could attempt to secretly divert AI chips from their reported transit paths. To detect this, one could:

-   •
    
    Use video surveillance throughout transit; and
    
-   •
    
    Carry out "diversion detection inspections" (as [above](#A7.SS3 "G.3 Detecting efforts to get cutting-edge AI chips to undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")) at declared data centers and storage facilities, which could detect a diversion during recent transit.
    

Lastly, an adversary could attempt to secretly divert AI chips or chip-making machines from an elimination facility, e.g. by falsely reporting that chips have been melted. To detect this, one could use "elimination inspections," designed with a few measures to detect this violation:

-   •
    
    Inspector presence over specified elimination procedures; and
    
-   •
    
    [Unattended surveillance equipment](#S2.SS2.SSS1 "2.2.1 On-site measurement methods ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").
    

Alternatively, a mandated storage period before elimination could help ensure that AI chips would be unusable or obsolete by the time they are eliminated.

### G.4 Detecting efforts to host cutting-edge AI chips at undeclared locations

So far, we have examined one approach to verifying that there are not many cutting-edge AI chips being used at undeclared locations: detecting attempts to get cutting-edge AI chips to these locations. Another possible approach is detecting cutting-edge AI chips after they have reached undeclared locations, when they are being stored or used. This section describes how that could be implemented, for each potential method of secretly hosting operational, cutting-edge AI chips.

Cutting-edge AI chips could be secretly stored at facilities that are not declared to be data centers, which would effectively be undeclared data centers. To detect these data centers, one could:

-   •
    
    Use [national technical means](#S2.SS3.SSS1 "2.3.1 National technical means ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (e.g. satellite images);
    
-   •
    
    [Monitor procurement](#S2.SS3.SSS4 "2.3.4 Procurement monitoring ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") of equipment that is used for building and operating data centers;
    
-   •
    
    Carry out [challenge inspections](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") to resolve suspicions about particular locations; and
    
-   •
    
    Specifically for verifying that AI chip storage facilities are not being used as data centers, [design information verification](#S2.SS2.SSS4 "2.2.4 Design information verification ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") and "undeclared item inspections" (described [below](#A7.SS4 "G.4 Detecting efforts to host cutting-edge AI chips at undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")).
    

Alternatively, cutting-edge AI chips could be stored at declared data centers, without being reported as being there. These could be detected with "undeclared item inspections"[^148] along with [design information verification](#S2.SS2.SSS4 "2.2.4 Design information verification ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), as follows.

-   •
    
    AI chips might be "hidden in plain sight" in declared server rooms.[^149] To detect this, one could use "undeclared item inspections," with:
    
    -   –
        
        Counting of chips in server rooms; and
        
    -   –
        
        Examination of [unique identifiers](#S2.SS2.SSS3 "2.2.3 Unique identifiers ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") of selected chips in server rooms.
        
    
-   •
    
    AI chips might be hidden in areas that reportedly do not contain chips, at declared data centers. To detect this, one could use "undeclared item inspections," with:
    
    -   –
        
        Visual observation and equipment that can detect the presence of chips; and
        
    -   –
        
        Surveillance of declared non-server areas with unattended equipment, e.g. using video cameras to verify that an area is not used for chip storage.
        
    
-   •
    
    AI chips might be hidden in secret rooms, at declared data centers. To detect this, one could use [design information verification](#S2.SS2.SSS4 "2.2.4 Design information verification ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), with:
    
    -   –
        
        Design information verification inspections;
        
    -   –
        
        Unattended on-site equipment, e.g. (if needed, rudimentary) video and audio surveillance equipment to detect construction activities; and
        
    -   –
        
        Satellites, to detect undeclared construction.
        
    
-   •
    
    AI chips that have been placed in a data center might be hidden by being moved, during an inspection, to areas that will not undergo (further) inspection. To detect this, one could include the following procedures in "undeclared item inspections," done by [inspectors monitoring the exits](#S2.SS2 "2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") of rooms and facilities:
    
    -   –
        
        Inspection of items leaving not-yet-inspected rooms; and
        
    -   –
        
        Inspection of items leaving the data center, as well as on-site video surveillance.
        
    

Zooming out, this approach could be combined with the one discussed in [the previous section](#A7.SS3 "G.3 Detecting efforts to get cutting-edge AI chips to undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for redundancy. Next, we turn to the other subproblem of verification.

### G.5 Detecting efforts to tamper with the design features of cutting-edge AI chips at known locations

To detect efforts to secretly tamper with large numbers of AI chips at known locations, one could use the following:[^150]

-   •
    
    "Tampering detection inspections" at data centers and storage facilities (including soon after chip production) could help verify that chips have not been tampered with.
    
    -   –
        
        These could consist of inspectors specifying a random sample of chips (identified by their unique identifiers), data center operators providing access to them, and inspectors then verifying that the chips have not been tampered with.[^151]
        
    
-   •
    
    [Video surveillance](#S2.SS2.SSS2 "2.2.2 Containment and surveillance ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") at data centers, storage facilities, and in transit could directly detect tampering activities.
    

### G.6 Additional measures

The three approaches discussed above could each be boosted by [human sources](#S2.SS3.SSS2 "2.3.2 Human sources ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") of information, who could be accessed by broad interview authority and collection of tips.

For efficiency and preventing cover-ups, inspections should often be short-notice, randomly timed, and with heavy reliance on random sampling within the inspection (when that is sufficient for a high probability of detecting violations[^152]).

### G.7 Overview of the hypothetical implementation described above (not a policy suggestion)

At certain production and storage facilities upstream in the supply chain:

-   •
    
    [Accountancy reporting](#S2.SS1 "2.1 Accounting and mandatory self-reporting ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (of cutting-edge chip-making machines)
    
-   •
    
    [Procurement monitoring](#S2.SS3.SSS4 "2.3.4 Procurement monitoring ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Video cameras](#S2.SS2.SSS2 "2.2.2 Containment and surveillance ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (perhaps) (focused on highly centralized suppliers)
    
-   •
    
    [Perimeter portal continuous monitoring](#S2.SS2.SSS5 "2.2.5 Perimeter portal continuous monitoring ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (perhaps) (focused on highly centralized suppliers)
    

At cutting-edge fabs:

-   •
    
    [Accountancy reporting](#S2.SS1 "2.1 Accounting and mandatory self-reporting ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (of cutting-edge AI chips and chip-making machines)
    
-   •
    
    [Undeclared item inspections](#A7.SS4 "G.4 Detecting efforts to host cutting-edge AI chips at undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (focused on chip-making machines)
    
-   •
    
    [Tampering](#A7.SS5 "G.5 Detecting efforts to tamper with the design features of cutting-edge AI chips at known locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") and [diversion detection inspections](#A7.SS3 "G.3 Detecting efforts to get cutting-edge AI chips to undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Design information verification](#S2.SS2.SSS4 "2.2.4 Design information verification ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Perimeter portal continuous monitoring](#S2.SS2.SSS5 "2.2.5 Perimeter portal continuous monitoring ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (focused on cutting-edge AI chips, chip-making machines, and construction items)
    
-   •
    
    In-line instrumentation
    

At cutting-edge data centers and cutting-edge AI chip storage facilities:

-   •
    
    [Accountancy reporting](#S2.SS1 "2.1 Accounting and mandatory self-reporting ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (of cutting-edge AI chips)
    
-   •
    
    [Undeclared item inspections](#A7.SS4 "G.4 Detecting efforts to host cutting-edge AI chips at undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Tampering](#A7.SS5 "G.5 Detecting efforts to tamper with the design features of cutting-edge AI chips at known locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") and [diversion detection inspections](#A7.SS3 "G.3 Detecting efforts to get cutting-edge AI chips to undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Video cameras](#S2.SS2.SSS2 "2.2.2 Containment and surveillance ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Design information verification](#S2.SS2.SSS4 "2.2.4 Design information verification ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    

At certain elimination facilities:

-   •
    
    [Accountancy reporting](#S2.SS1 "2.1 Accounting and mandatory self-reporting ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (of AI chips and chip-making machines)
    
-   •
    
    [Elimination inspections](#A7.SS3 "G.3 Detecting efforts to get cutting-edge AI chips to undeclared locations ‣ Appendix G How verification of AI chip accounts could be implemented ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (focused on AI chips and chip-making machines)
    
-   •
    
    Unattended surveillance equipment
    
-   •
    
    Storage period before elimination (potential alternative)
    

In transit:

-   •
    
    [Video cameras](#S2.SS2.SSS2 "2.2.2 Containment and surveillance ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") (for cutting-edge AI chips and chip-making machines)
    
-   •
    
    GPS devices and security for vehicles
    

At arbitrary locations:

-   •
    
    Location restrictions on data-center-quality, cutting-edge AI chips
    
-   •
    
    [National technical means](#S2.SS3.SSS1 "2.3.1 National technical means ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Challenge inspections](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    
-   •
    
    [Human sources](#S2.SS3.SSS2 "2.3.2 Human sources ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")
    

### G.8 Assessment

There are good reasons to tentatively consider the verification system described above highly reliable:[^153]

-   •
    
    It has at least 5 layers of defense[^154] for detecting any serious attempt to possess and use many cutting-edge AI chips at undeclared locations, and it has 3 layers of defense[^155] for detecting tampering with chips at declared locations.
    
-   •
    
    Some of these layers appear highly reliable[^156], and all appear to have a significant chance of detecting violations.
    
-   •
    
    Analogous methods have worked very well historically (as discussed in the section on track records).
    

Overall, this shows that methods that have been widely used for nuclear arms control verification[^157] can be adapted to create a reliable system for verifying accounts of AI chips.

## Appendix H Back-of-the-envelope calculations of direct inspection costs

Across three metrics—the number of inspections conducted, the ratio of number of items examined in inspections to gross world product, and the proportional loss to gross world product from interruptions to facility (i.e. data center) operations—back-of-the-envelope calculations suggest that the direct costs of inspecting cutting-edge AI chips to verify the compliance of highly compute-intensive AI development would be lower than or roughly similar to the corresponding costs in IAEA verification (i.e. less than 10x larger).

The last two metrics incorporate gross world product to show that, although speculative large increases in global AI chip production would increase the number of chips that needed to be examined and potentially interrupted to verify compliance, such increases in chip production would involve enough economic growth to easily keep pace with this need.[^158]

Number of inspections conducted annually:

-   •
    
    In 2019 and 2020, the IAEA conducted  2,900 in-field inspections \[[110](#bib.bib110)\]\[[111](#bib.bib111)\].
    
-   •
    
    Various estimates suggest there are currently  100-1,000 large data centers, and an analyst at market research group Synergy Research Group claims this figure has doubled over the past  5 years \[[112](#bib.bib112)\]\[[113](#bib.bib113)\]\[[114](#bib.bib114)\][^159]. The number of data centers with cutting-edge AI chips is presumably significantly lower.
    
-   •
    
    The number of chip fabrication facilitates ("fabs") producing (near-)cutting-edge chips appears relatively small.[^160]
    
-   •
    
    This leaves substantial room for the number of large, AI-specialized data centers and fabs to grow while the number of inspections needed to inspect them stays roughly similar to the IAEA’s number of inspections.
    
    -   –
        
        Even if demand for data centers and fabs hosting a significant number of cutting-edge, AI-specialized chips exploded upwards, their numbers could be kept manageable, e.g. through a large but limited number of authorizations of cutting-edge, AI-specialized data centers.
        
    

Ratio of the number of items examined annually to gross world product:

-   •
    
    In 2019 and 2020, the IAEA verified that  25,000 seals had not been tampered with \[[110](#bib.bib110)\]\[[111](#bib.bib111)\]. Additionally, IAEA inspectors conduct many other measurements, such as full physical inventories at most of 700 facilities, which amounts to annual examinations of  140,000 items if we assume 80% of facilities are inspected and 250 items[^161] are examined in the average inventory \[[120](#bib.bib120)\].
    
-   •
    
    Assuming that 10k to 100k AI chips[^162] used for a year were required for a violation and assuming (very conservatively relative to current AI chip production \[[122](#bib.bib122)\]\[[123](#bib.bib123)\]) that the number of chips that could be used for a violation were 2.5 billion, then  58,000 to  580,000 chips would have to be examined annually for a 90% probability of detecting serious violations.[^163] The GWP involved would not be less than it currently is for IAEA verification, so the ratio (of items examined to GWP) would be less than 10x worse (and plausibly better) than the ratio involved in IAEA inspections.
    
    -   –
        
        Hypothetically, what if the number of available AI chips grew beyond that already high level? 2x growth in AI chip production would cause a  2x increase in the number of chips that need to be examined to maintain a 90% detection probability.[^164] At the same time, such an increase in AI chip production from such a high level would require  2x growth in GWP[^165], so the ratio would not become worse.
        
    

Proportional loss of gross world product from interruptions to operations:

-   •
    
    Nuclear energy sales make up  0.4% of gross world product \[[125](#bib.bib125)\]. Assuming the average nuclear energy facility loses 2 days of production per year to IAEA safeguards inspections[^166], it follows that the interruptions from these inspections cost  0.002% of gross world product.
    
-   •
    
    Assuming 10,000 AI chips for a year out of anywhere from 600,000 to 600 billion (or even more) available AI chips were required for a violation, making the simplifying (and very conservative) assumption that AI chips made up all of gross world product, and assuming that examination of any one chip knocked 100 chips out of use for one day per year, these inspections would cost  0.006% of gross world product[^167]—just a factor of  3 over the above estimate about IAEA inspections’ costs.
    
    -   –
        
        This estimate assumes that fab production levels can be verified without interrupting fab production (e.g. by monitoring chip-making machines’ inputs and outputs) and are therefore relatively small. Otherwise, costs could be much higher.
        
    

These are just back-of-the-envelope calculations made with extremely rough approximations, so they should not be treated as robust predictions.

[^1]: This review mainly draws from a textbook about nonproliferation M&V and the text of relevant treaties. Nonproliferation treaties are: the Non-Proliferation Treaty (NPT) and five Nuclear-Weapon-Free-Zone Treaties (i.e. Tlatelolco, Rarotonga, Bangkok, Pelindaba, and Semipalatinsk). (There were also agreements that were not formal treaties, mainly the U.S.-D.P.R.K. Agreed Framework and the JCPOA.) Nuclear arms limitation treaties are the: ABM Treaty, SALT I provisional agreement, INF Treaty, START, SORT, and New START. Test ban treaties are the: Partial Nuclear Test Ban Treaty, Threshold Test Ban Treaty, Peaceful Nuclear Explosions Treaty, and Comprehensive Nuclear-Test-Ban Treaty. (The latter would authorize on-site inspections to investigate events detected by remote sensor stations, but it is not on track to enter into force.)
[^2]: Of these ten states, five are parties to the NPT as nuclear weapon states (a status which permits them to keep their nuclear weapons), and another five are not parties to any nuclear nonproliferation treaty.
[^3]: These are Additional Protocols.
[^4]: That is, Additional Protocols, under which there is a much lower political bar to conducting such inspections.
[^5]: These are: for nonproliferation, the IAEA system under Comprehensive Safeguards Agreements with Additional Protocols; for bilateral treaties, the INF Treaty, START, and New START systems; and for test bans, the International Monitoring System.
[^6]: That is, the IAEA’s Comprehensive Safeguards Agreements, especially before the 90s
[^7]: The review of track records is mainly based on reports from the NTI and IAEA.
[^8]: This takeaway mainly draws from: reports on negotiations, U.S. chief negotiator Gottemoeller’s account, and negotiation outcomes; these sources leave out many details of negotiations, so this section likely misses important aspects of M&V politics.
[^9]: More concretely, here are two example rules states may want to uphold (without taking a stance on their wisdom): (1) The training of a large machine learning model should stop if the model’s offensive cyber capabilities reach a certain level, as measured by some objective benchmark. (2) Large machine learning models used in autonomous weapon systems must be trained with certain measures (e.g. adversarial robustness training) to reduce unintended behavior.
[^10]: That is, some nuclear arms control M&V system faced a similar or greater difficulty, yet it was adopted and successful.
[^11]: This would require commodity chips to not offer loopholes.
[^12]: This also presumably helps ease concerns about direct costs, secrecy, and security, by letting stakeholders learn in lower-stake contexts that the downsides of an M&V method are acceptable.
[^13]: For example, one criteria could be whether the amount of compute used is above some high threshold. Such a threshold would ideally be updated in such a way that high-risk AI development is continuously covered, even if the compute requirements for high-risk AI development decrease over time due to advances in algorithmic efficiency \[[9](#bib.bib9)\].
[^14]: To prevent harmful AI development from states that are not parties to such an agreement, non-parties would need to be sufficiently cautious, behind, deterred, or otherwise blocked from harmful AI development.
[^15]: This is because, insofar as an M&V system is weak and under certain assumptions, state parties (i) will be less deterred from defection, (ii) will be more incentivized to defect in order to preempt others’ defection, and (iii) will be less likely to be stopped if they do defect. (One assumption here is that—due to the high levels of expert scrutiny that high-stakes M&V systems tend to receive—a weak M&V system will likely be perceived as such. Another assumption is that, in the absence of effective M&V, compliance decisions will be made with the incentives of a prisoner’s dilemma or a low-trust assurance game.)
[^16]: Nuclear arms control history involves over 50 years of international M&V and over a dozen international agreements with verification requirements. In contrast, other areas of post-WWII nonproliferation and arms control history involve only two major international agreements with verification requirements: the Chemical Weapons Convention and the (now abandoned) Treaty on Conventional Armed Forces in Europe.
[^17]: See [an appendix](#A1 "Appendix A The nuclear-AI analogy ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for more detailed discussion of the analogy.
[^18]: Beyond verification problems, other reasons why negotiations could fail include partisan obstructionism, international tensions, lack of political will at high levels of governments, anti-regulation advocacy, inability to keep pace with rapid technological advances, commitment problems, issue linkage, and negotiators misunderstanding each other’s red lines.
[^19]: For example, some rules on AI activities may be undesirable due to economic or military costs.
[^20]: A retired diplomat who was involved in NPT negotiations recalls, ”the 1962 crisis was the trigger that prompted a widespread change with regard to this issue. Humankind was faced with a crisis that could end in a global catastrophe. It is after that crisis the negotiations on the nuclear weapons problem began in earnest” \[[14](#bib.bib14)\]. An IAEA report \[[15](#bib.bib15)\] and Schelling \[[16](#bib.bib16)\] agree.
[^21]: There are also a handful of Nuclear-Weapon-Free-Zone treaties—horizontal nonproliferation treaties that only apply to certain regions—as well as a few agreements that just sought to keep one specific state (i.e. North Korea or Iran) from developing nuclear weapons.
[^22]: In the context of nuclear arms control, ”deployed” usually means ”ready to be launched.” For example, a nuclear weapon could be deployed if it is attached to a usable missile, but not if it is in a warehouse with no way to be launched quickly.
[^23]: For a more detailed overview, see e.g. [”U.S.-Russian Nuclear Arms Control Agreements at a Glance”](https://www.armscontrol.org/factsheets/USRussiaNuclearAgreements) from the Arms Control Association.
[^24]: The 1963 Partial Test Ban Treaty, a multilateral treaty, banned nuclear tests in the atmosphere, underwater, and in outer space. The Threshold Test Ban Treaty and the Peaceful Nuclear Explosions Treaty were U.S.-U.S.S.R. treaties that banned all nuclear explosions above a certain threshold of energy released. The 1996 Comprehensive Test Ban Treaty would have banned all nuclear explosions, but it requires 44 specific countries to ratify it in order for it to go into effect, and 8 of these have not ratified it.
[^25]: For the INF Treaty, START, and New START, states are also required to report the dimensions of all restricted delivery vehicles, to facilitate their identification.
[^26]: For example, if Russia reports how many ICBMs it has at each facility, an inspection of a single facility could reveal that the report is false. In contrast, if Russia only reported its total number of ICBMs, knowledge of many of Russia’s nuclear missile facilities would be necessary to reveal the report is false.
[^27]: In a report which concluded that Syria very likely attempted to build a secret nuclear reactor, the IAEA noted, ”Large quantities of barite were purchased by the AECS \[Syrian Atomic Energy Agency\] between 2002 and 2006. Syria has stated that the material was to be used for shielded radiation therapy rooms at hospitals, without providing any supporting information. However, the end use of the barite as stated in the actual shipping documentation indicates that the material was intended for acid filtration. Additionally, the delivery of the barite was stopped at the request of the AECS after the destruction of the building at the Dair Alzour site and the remaining quantity was left undelivered” \[[23](#bib.bib23)\].
[^28]: A typical procedure (used in e.g. START I) is that inspected parties escort accompanying inspectors throughout their visit, control inspectors’ travel, provide some of inspectors’ equipment, and check inspectors’ equipment, as long as they do not interfere with the inspection. In turn, inspectors may check, e.g. with calibration standards, that their equipment has not been sabotaged.
[^29]: In some inspections (e.g. various START I inspections), inspectors may patrol the perimeter of the inspection site, be present at exits of the site and of some structures within the site, and inspect objects and vehicles that are leaving through these exits.
[^30]: Additionally, unobstructed underground passages out of facilities were banned, obstructed ones were ”subject to examination,” and incoming helicopters and cranes required advance notice outside emergencies. As another precaution, monitors also had an independent power system.
[^31]: These were: visual inspection, length measurement, and/or weight sensors.
[^32]: Accordingly, U.S. chief negotiator Gottemoeller \[[25](#bib.bib25)\] recalls, ”Noninterference with national technical verification was one of the earliest and easiest points of agreement in the New START negotiations.”
[^33]: In one special case, the Iran Deal, Iran was required to inform an oversight organization of a wide range of its nuclear-relevant purchases (this was called a ”monitoring procurement channel”).
[^34]: This is the term used for such inspections in the Chemical Weapons Convention; the IAEA uses the term ”complementary access inspections.”
[^35]: These provisions ban e.g. jamming satellites and putting nets over mobile missiles \[[25](#bib.bib25)\].
[^36]: States could hide their flight-test data from foreign NTMs by encrypting their data, jamming foreign sensors, broadcasting their data in a narrow beam, or enclosing their data in physical capsules that fall to the ground. To deter such deception, the START I Treaty explicitly bans all of these actions, while also more generally banning ”any activity that denies full access to telemetric information” \[[21](#bib.bib21)\]. (As exceptions, though, this treaty allows 11 uses of flight-test data encapsulation or encryption per year.)
[^37]: For example, under START I, different missile types are required to have distinguishing characteristics, which helps determine missile types through inspections or satellite images. Missiles lacking these characteristics could be detected as such through visual inspection or measurement.
[^38]: The probability of detection varies by violation. It can be hard to quantify, since non-public and non-systematic intelligence gathering methods (e.g. espionage) sometimes play large roles in M&V. Still, in its systematic methods, the IAEA’s standard is 90% for detecting diversions of the most sensitive nuclear materials from declared nuclear facilities.
[^39]: Founded a decade prior to the signing of the NPT, the IAEA had already been implementing nuclear safeguards on a more limited scope: verifying the peaceful use of some nuclear exports.
[^40]: This template is called INFCIRC/153.
[^41]: This template is officially called the ”Model Protocol,” or INFCIRC/540.
[^42]: Perhaps this is a path dependency from the historical legal interpretations of the NPT, which for a long time was only interpreted as mandating CSAs (partly since APs did not exist yet).
[^43]: See the [relevant](#A2.SS1 "B.1 NWFZ Treaties ‣ Appendix B M&V in Nuclear-Weapon-Free-Zone treaties and in agreements with North Korea and Iran ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") [appendices](#A2.SS2 "B.2 Agreements with North Korea and Iran ‣ Appendix B M&V in Nuclear-Weapon-Free-Zone treaties and in agreements with North Korea and Iran ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for details and evidence.
[^44]: To report potential non-compliance, the IAEA does not need to have proof that a state is diverting nuclear materials for nuclear purposes; it just needs to be unable to verify that a state is compliant. Because of that, rejection of permission to carry out a special investigation can be—and has been—a reason for reporting to the UN Security Council. In other words, the operating principle, in theory, is, ”guilty until verified innocent.” In practice, though, the IAEA does not report all anomalies or non-cooperation to the UN Security Council, instead appearing to reserve reporting for cases where there is relatively legible evidence of serious violations.
[^45]: The NPT does not specify penalties for non-compliance \[[31](#bib.bib31)\]. The template for CSAs, INFCIRC/153, does authorize the IAEA to take certain punitive measures specified in the IAEA’s statute (although these do not seem like strong deterrents against nuclear weapons development): ”direct curtailment or suspension of assistance being provided by the Agency or by a member, and call for the return of materials and equipment made available to the recipient member or group of members. The Agency may also, in accordance with article XIX, suspend any non-complying member from the exercise of the privileges and rights of membership” \[[32](#bib.bib32)\]\[[33](#bib.bib33)\]
[^46]: Critics argue that this is outdated, as modern enrichment technology allows for significantly faster enrichment than when these goals were set. The IAEA does use some ”Limited Frequency Unannounced Access” inspections for short-notice inspections of enrichment plants.
[^47]: Most nuclear power reactors are refueled once a year or two, and inspectors are present during this time.
[^48]: As is standard for international inspections, representatives of the host state are allowed to accompany inspectors (to ensure they are not spying), but they may not interfere with inspectors’ work.
[^49]: e.g., measuring both weight and contents of a container
[^50]: If a state diverted some material from many nuclear containers, random selection allows the IAEA to have a high chance of identifying diversions while only having to precisely measure a small fraction of all containers. There is a tradeoff between the IAEA’s desired probability of detecting diversion and the number of measurements needed, with returns to further measurements diminishing quickly. The IAEA has explicitly decided to make this tradeoff such that its detection probability is 90-95% for the most sensitive nuclear material.
[^51]: these are ”mailbox declarations”
[^52]: For example, if the IAEA believes a state does not have plutonium reprocessing plants (which are needed to develop plutonium-based nuclear bombs), that may be a reason for the IAEA to put fewer resources (e.g., less frequent inspections) on safeguarding of plutonium in the state’s nuclear waste, while putting more resources on safeguarding uranium at enrichment plants. As of the end of 2017, the IAEA had developed 62 state-level safeguards approaches, with plans for more.
[^53]: The IAEA sets a goal for safeguards to identify all diversions of ”significant quantities” of nuclear materials, defined based on its estimates of how much is necessary to produce a single nuclear weapon. These estimates include: 8 kg for plutonium, 25 kg for U-235 in highly enriched uranium, 75 kg for U-235 in low enriched uranium, and 10 t of natural uranium. Critics argue these estimates are overly high, and nuclear weapons could be made with nuclear material that is smaller by a factor of e.g., 2-8.
[^54]: Some M&V mechanisms are well-suited for (1), while others are well-suited for (2). More precisely, some mechanisms are cheap to use at scale yet have high false positive rates, while other mechanisms are costly yet more reliable. An efficient strategy can be to use the former mechanisms to identify suspected locations and the latter mechanisms to determine whether these locations hold undeclared nuclear facilities. An analogy from epidemiology is the use of ”pool testing” to cheaply test many individuals for a disease, followed by more precise (yet costly) testing of a smaller number of individuals who are highlighted by the pool testing.
[^55]: As discussed earlier, suspicions do not need to be positively resolved for the IAEA to report non-compliance to the UN Security Council. Still, reducing the frequency of false alarms seems likely useful for ensuring that states take alarms seriously.
[^56]: As discussed in [the relevant appendix](#A5 "Appendix E The role of intelligence agencies in identifying undeclared nuclear facilities ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), these claims are supported by strong trends in expert opinion and case studies, as well as the existence of a plausible mechanism that might cause them to be true.
[^57]: Intelligence agencies’ tips are also available in the context of states that only have CSAs, but they play a vital role in verification only in the context of states that also have APs. This is because it is only for these latter states that the IAEA has the authority to act on tips through investigation; IAEA accusations of non-compliance based entirely on state tips would not be credible.
[^58]: We may wonder: When national intelligence agencies already know about some undeclared nuclear facility, what is the point of the IAEA investigating it? Perhaps IAEA investigations enable findings of non-compliance with the NPT to have international credibility (and thus bring about international penalties), which intelligence agencies (with their opaque methods and national bias) may be unable to do on their own.
[^59]: As reasons to conclude this, the IAEA does not publicly describe any such process, it is very unclear how IAEA safeguards agreements (which are public) could provide the authorities needed for such a process, and the IAEA has a [spotty track record in identifying undeclared facilities](#S4.SS1 "4.1 NPT M&V systems’ Track Records ‣ 4 Track Records of Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties").
[^60]: These are: Non-nuclear buildings on the same ”site” as nuclear facilities Nuclear material mines, mills, and certain waste facilities Information about these partly helps indirectly, by helping identify diversions of nuclear material. Nuclear R&D activities that do not use nuclear materials Relevant equipment manufacturing activities that do not use nuclear materials (e.g. centrifuge manufacturing) Decommissioned nuclear facilities
[^61]: If a state self-reports on one of the above facilities, then the IAEA can investigate activities there and discover that it supplies (or is supplied by) an undeclared nuclear facility. For example, if the IAEA found that some nuclear waste had less plutonium than expected, this may indicate that some of the plutonium had been secretly transported to an undeclared reprocessing facility. (The IAEA could also find that the declared facility is itself doing unreported processing of nuclear materials, although this would not be a case of finding an undeclared nuclear facility.) If a state does not self-report on one of the above facilities but the IAEA somehow discovers it (e.g., through intelligence agency tips followed by an inspection with [environmental sampling](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties")), this would strongly indicate that the state has (other) undeclared nuclear facilities or activities, since states generally do not have peaceful reasons to have undeclared nuclear facilities. (In contrast, discovering that a state did not declare a facility would be less suspicious if the state had not been required to declare the facility.)
[^62]: See [the relevant appendix](#A4 "Appendix D The IAEA’s inability to verify the absence of undeclared nuclear facilities under Comprehensive Safeguards Agreements ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for justification of this claim.
[^63]: At inspections, inspectors may use any of the safeguards usually available to them (described in other sections), although accounting is infeasible because states are not required to keep nuclear materials accounts at these additional locations.
[^64]: These qualifications are: Access is only given so that the IAEA can carry out ”environmental samples and, in the event the results do not resolve the question or inconsistency at the location specified by the Agency \[…\], utilization at that location of visual observation, radiation detection and measurement devices, and, as agreed by \[the state\] and the Agency, other objective measures” \[[36](#bib.bib36)\]. The state is permitted to be unable to provide such access, in which case the state ”shall make every reasonable effort to satisfy \[IAEA\] requirements, without delay, at adjacent locations or through other means…” \[[36](#bib.bib36)\].
[^65]: These treaties use annual quotas for inspections (unlike the IAEA), ranging from 10 to 28.
[^66]: Perhaps the most significant differences are: The INF Treaty was a total ban on intermediate-range (500-5500 km) missiles, while START I and New START required reductions in strategic offensive arms (i.e. long-range nuclear weapons). Specifically in the context of the INF Treaty, maintaining or innovating on the banned missiles would require flight tests at banned ranges, so flight-test monitoring could be enough to detect treaty violations. The INF Treaty and START I M&V included [perimeter portal continuous monitoring](#S2.SS2.SSS5 "2.2.5 Perimeter portal continuous monitoring ‣ 2.2 M&V methods at declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") at a few facilities, while the New START did not, reportedly because this monitoring was expensive and not very useful \[[25](#bib.bib25)\]. To streamline the M&V process, New START consolidated the many types of inspections of START I into just two (more extensive) types of inspections. It also replaced complex counting rules (i.e. rules about how many warheads particular types of missiles would be counted as having) with simpler rules, which worked through inspectors directly counting the number of warheads on missiles at inspections.
[^67]: The CTBT called for the Comprehensive Test Ban Treaty Organization (which the CTBT established) to begin construction of the International Monitoring System so that it would be ready by the time the treaty entered into force. The CTBT currently looks far from entering into force; by treaty provision, a large number of specific countries must all sign it for it to enter into force, and various have not. Still, the U.S. and some other states have been providing funding to support the construction of the monitoring system, and (legally) the treaty does not need to be in force for states to be able to host sensors on their own territories.
[^68]: The four types of stations are: seismic, hydroacoustic, infrasound, and radionuclide sensors.
[^69]: To help enforce nuclear weapon test bans, analysts do not just need to know when a test happened; they also need to know where it happened. The location of a nuclear test can be determined from acoustic wave sensors similarly to how one can use seismic sensors to locate the epicenter of an earthquake. And the location of a nuclear test can be roughly determined from air particles by having a model of global wind patterns and running the model backwards in time.
[^70]: As of December 2022, this is the most recent annual report published by the CTBTO. Previous years’ reports show that the CTBTO’s 2020 budget was similar to that of preceding years, despite the COVID-19 pandemic. $100 million is an approximation of the reported $131,320,100 multiplied by 81%, the percentage reportedly allocated to verification.
[^71]: Peaceful nuclear explosions hypothetically might be used, for example, for mining or building canals.
[^72]: Inspections would require the approval of at least 30/51 members of the CTBTO’s Executive Council. These members are state parties.
[^73]: Potential methods to gain evidence about whether a nuclear explosion took place would include: detecting radioactive materials, detecting cavities and rubble zones, and detecting seismic aftershocks.
[^74]: The events that have been closest to NPT non-nuclear-weapon states getting nuclear weapons have been: Nuclear-weapon states have stored nuclear weapons in non-nuclear-weapon state parties to the NPT. North Korea publicly (although procedurally questionably) withdrew from the NPT several years before acquiring nuclear weapons. While formally under the NPT, Iran has been moving toward having the capacity to quickly produce nuclear weapons, e.g., by enriching uranium to nearly weapons-grade levels.
[^75]: These have been: Iran, Iraq, Libya, North Korea, Syria, South Korea, and Yugoslavia.
[^76]: See [an appendix](#A6 "Appendix F Details on track records of nuclear arms control M&V ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for evidence.
[^77]: This conclusion is based on the dataset of Bleek \[[45](#bib.bib45)\], which lists when all known state pursuits of nuclear weapons took place, considered together with an IAEA ”Status list” \[[46](#bib.bib46)\], which lists when states signed APs. However, that is a much shorter—and thus much less informative—track record than the track record of CSAs; CSAs began to be implemented in the early 70s, while APs began to supplement them in the late 90s.
[^78]: Iran claims to not be pursuing a nuclear weapon, but this claim is hard to reconcile with Iran’s high uranium enrichment levels, its self-reported technical ability to make the bomb, and Iran’s multiple (no-longer-)secret nuclear facilities and activities.
[^79]: APs also helped the IAEA identify past undeclared nuclear activities in South Korea and Egypt, but these activities had been small-scale research activities and not parts of state pursuits of nuclear weapons \[[47](#bib.bib47)\].
[^80]: This happened in the several years when the Trump Administration had withdrawn the U.S. from the Iran Deal but Iran had not yet ended its implementation of its AP. (Iran’s expanded nuclear activities have continued after Iran stopped implementing its AP, but these post-AP activities are outside the scope of analyzing the technical track record of CSAs with APs.)
[^81]: Using its CSA and AP authorities, the IAEA requested and received ”complementary access” for inspectors to conduct [environmental sampling](#S2.SS3.SSS6 "2.3.6 Challenge inspections and requests for additional information ‣ 2.3 M&V methods not limited to declared facilities ‣ 2 Nuclear M&V Methods ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") at three suspected nuclear sites in Iran (at least some of which the IAEA received tips about from states). Analyzing these samples, the IAEA found that all three sites held anthropogenic uranium particles, which Iran struggled to explain \[[48](#bib.bib48)\]. It is not yet clear what the delay was between these undeclared activities taking place and the IAEA discovering them.
[^82]: One might wonder if this example is an outlier due to the COVID-19 pandemic, but this appears to not be the case; the numbers were similar (62/131) the year before the pandemic began \[[49](#bib.bib49)\].
[^83]: Because these investigations were ongoing, the IAEA did not conclude that these states did not have undeclared nuclear facilities.
[^84]: Unlike with North Korea, this finding did not kick off extensive diplomacy, as Syria had recently become occupied with a civil war.
[^85]: See [an appendix](#A6 "Appendix F Details on track records of nuclear arms control M&V ‣ Nuclear Arms Control Verification and Lessons for AI Treaties") for more details.
[^86]: Of the 10 states that are widely considered to have acquired nuclear weapons, 2—Israel and South Africa—were not quick to publicly announce them \[[59](#bib.bib59)\]\[[60](#bib.bib60)\]\[[61](#bib.bib61)\].
[^87]: This happened to varying degrees in, for example, Yugoslavia, Brazil, South Africa, Iraq, and Libya \[[54](#bib.bib54)\]\[[29](#bib.bib29)\]\[[62](#bib.bib62)\]\[[51](#bib.bib51)\]\[[28](#bib.bib28)\]\[[60](#bib.bib60)\].
[^88]: e.g., this is not based on detailed public sources on informal negotiations on M&V implementation details, due to the apparent absence of such sources.
[^89]: The U.S. Chief negotiator of New START writes, ”First, the verification regime of any arms control treaty must be effective” \[[25](#bib.bib25)\]. Similarly, a declassified 3-volume history of IAEA M&V negotiations concludes that a ”fundamental” negotiating objective of the U.S. in INFCIRC/153 (i.e. CSA template) negotiations, which was ”\[t\]o a considerable degree \[…\] shared by other participants,” was to ”preserve the integrity and effectiveness of the IAEA safeguards system” \[[63](#bib.bib63)\].
[^90]: An IAEA historian writes, ”States feared—and continue to fear—that inspectors might conduct industrial espionage \[…\]” \[[64](#bib.bib64)\]. Accordingly, an IAEA report explains, ”The IAEA has put in place elaborate arrangements to ensure that safeguards information remains confidential and to prevent unauthorized disclosures. \[…\] Despite the very large quantity of safeguards information handled by the IAEA since 1970, there has not been any substantiated case of such a disclosure nor any complaint on this score by the government of any State in which safeguards are applied” \[[15](#bib.bib15)\].
[^91]: Some example precautions are: inspectors’ equipment being inspected when it reaches the inspected country, inspectors being escorted throughout their visit, perimeter monitors not being allowed to enter the facility they monitor, video cameras not transmitting live feeds remotely, and missile reentry vehicles being covered with pliable covers during inspection.
[^92]: For example, Japan advocated for especially strict non-disclosure policies for IAEA inspectors \[[63](#bib.bib63)\].
[^93]: The U.S. chief negotiator of New START writes, ”We had heard loud and clear from our military services that they were concerned about the costs of elimination procedures and the operational interruptions that were happening because of inspections” \[[65](#bib.bib65)\]. She also writes that these concerns informed negotiations, motivating a streamlining of inspections \[[25](#bib.bib25)\]. Similarly, an IAEA negotiating history states that, ”Cost was a big concern to G-77 states in particular. They consistently worried that the addition of new measures would come at the expense of technical assistance to developing countries” \[[66](#bib.bib66)\].
[^94]: A history of IAEA negotiations explains that major uranium and thorium producers opposed safeguards on uranium mining and ore processing \[[63](#bib.bib63)\].
[^95]: According to an IAEA negotiating history, ”A practical reason behind many of these proposals \[minimum notice requirements, e.g. minimum 2-hour notice before inspections\] was the difficulty of making arrangements for access to buildings on short or no-notice that do not in fact contain nuclear material and to which the state and facility representatives accompanying the Agency inspectors might not themselves have access.” Additionally, India pointed to the difficulty of collecting information from industry \[[68](#bib.bib68)\].
[^96]: An IAEA negotiating history explains that, ”states were apprehensive about the intrusiveness of the access and about their ability to provide the access in light of their constitutions. This was especially the case under the earlier Secretariat drafts for access for environmental sampling, which could be essentially anywhere in the state for any purpose”; the scope of complementary access was qualified to address this concern \[[68](#bib.bib68)\].
[^97]: One expert reviewer disagrees with the assessment that this was a significant obstacle.
[^98]: The U.S. chief negotiator of the New START, writes that, although the treaty updated its predecessor’s (i.e. START’s) verification system such that telemetry measures became obsolete (”we did not need telemetry measures to confirm compliance”), some senators were ”particularly determined that telemetry measures should be part of the new treaty because they had been such a central player in the success of START” \[[25](#bib.bib25)\]\[[65](#bib.bib65)\]. The treaty ended up including telemetry measures.
[^99]: A nuclear nonproliferation expert writes that, ”In the initial development of safeguards, a requirement to avoid discrimination among participating states was met by adopting uniformity in safeguards application” \[[69](#bib.bib69)\].
[^100]: An IAEA historian writes, ”States \[…\] often perceive the \[nuclear safeguards\] system as a threat to national sovereignty” \[[64](#bib.bib64)\]. In this vein, an IAEA report states that, early in the development of the IAEA’s verification system, ”The concepts of short notice and unannounced inspections, now increasingly important features of IAEA safeguards, would have been regarded as inadmissible infractions of national sovereignty” \[[15](#bib.bib15)\].
[^101]: As a few examples, the point in the supply chain when safeguards would start, the frequency and intensity of inspections, the amount of advance notice required for inspections, and the limits on complementary access inspections were all settled as compromises between parties who wanted more and less strict measures. As another example, the following provision in CSAs expresses a typical compromise position: ”The Agency shall require only the minimum amount of information and data consistent with carrying out its responsibilities under the Agreement” \[[32](#bib.bib32)\].
[^102]: Some assumptions were fragile in the sense of being false (the assumption that national intelligence agencies would reliably detect and report on secret facilities, which did not happen with Iraq), while some were fragile in the sense of being true at the time but not for long (the other assumptions discussed above). The slowness and non-universality of AP adoption suggests the system was built with insufficient flexibility, though one may reasonably worry (as negotiators at the time did) that flexibility could have been used to weaken the system \[[63](#bib.bib63)\]. And presumably one could have known before the near-miss with Iraq (discussed later) that proliferation had become easier and the Overton Window on inspections had shifted (from states having gained experience with inspections), though admittedly no secret nuclear programs of NPT non-nuclear-weapon states had been known to get far before Iraq’s.
[^103]: Incidents with North Korea and South Africa at around the same time are also sometimes credited with contributing to this change \[[17](#bib.bib17)\]. In North Korea, the IAEA (with tips from states) found that North Korea had submitted false reports and was likely hiding secret facilities. In South Africa, the government’s initiative to cooperatively dismantle its own nuclear program helped the IAEA learn about its capacity and the requirements for verifying the absence of undeclared nuclear facilities. However, discussions of Additional Protocols tend to give the incident with Iraq much more emphasis (often not even mentioning the events with North Korea and South Africa), suggesting the discovery of Iraq’s nuclear program was a much stronger motivator, as one might expect (since it was the clearest case of IAEA failure). For instance, several years before he became Director General of the IAEA, Grossi stated, ”what Chernobyl was to safety, Iraq was to safeguards, and 9-11 was to security” \[[71](#bib.bib71)\].
[^104]: One may object that this approach—considering political problems that arose in the nuclear case—neglects technical problems that may arise in the case of AI. However, these technical problems, as discussed by e.g. Shavit \[[1](#bib.bib1)\], tend to be about enabling privacy-preserving and efficient verification (rather than about enabling any sort of verification), and those problems are captured in the substantial preparations that this report suggests are important.
[^105]: To elaborate: The importance of maintaining effectiveness and feasibility as other costs are reduced is implicitly assumed in the below discussion. A coalition participating in an AI treaty could maintain its industrial competitiveness through e.g. multilateral export controls and technical collaboration. Privacy rights could be observed by limiting the scope of inspections to data centers (rather than, say, households) and using secrecy-preserving M&V methods. While specific challenges in appeasing idiosyncratic stakeholders and maintaining impartiality are hard to foresee, there are no immediately apparent reasons why these challenges would be worse in the AI case than in the nuclear case.
[^106]: That is, ”secure” in the broad sense of not creating severe vulnerabilities to national security.
[^107]: This also presumably helps ease concerns about direct costs, secrecy, and security, by letting stakeholders learn in lower-stake contexts that the downsides of an M&V method are acceptable.
[^108]: See Zaidi and Dafoe \[[12](#bib.bib12)\] for broader discussion of the strengths and limitations of this analogy.
[^109]: Nuclear facilities and uranium can be used to peacefully make nuclear power, and nuclear missile facilities can store treaty-compliant numbers and types of missiles. AI-specialized hardware and data centers can be used to train and deploy treaty-compliant AI systems or other applications.
[^110]: Equipment relevant to nuclear arms control involves R&D of centrifuges, missiles, and bombers, as well as the numbers and locations of nuclear arms. Equipment relevant to AI treaties might include private data, as well as AI and semiconductor R&D.
[^111]: The main case of corporate regulation in the nuclear case is that nonproliferation M&V applies to many private nuclear energy companies.
[^112]: In the case of AI, it is unclear which kinds of treaties (if any) will be feasible or desirable. Fortunately, nuclear arms control offers precedents for bilateral as well as multilateral treaties.
[^113]: These are the treaties covering the South Pacific, Africa, and Central Asia. The last of these is the one that requires APs.
[^114]: The Latin America Nuclear Weapons Free Zone Treaty states: ”Each Contracting Party shall negotiate multilateral or bilateral agreements with the International Atomic Energy Agency for the application of its safeguards to its nuclear activities” \[[73](#bib.bib73)\]. The Southeast Asia Nuclear Weapon Free Zone Treaty states: ”Each State Party which has not done so shall conclude an agreement with the IAEA for the application of full scope safeguards to its peaceful nuclear activities…” \[[74](#bib.bib74)\].
[^115]: Evidence for the claim that these agreements are interpreted as mandating a CSA (ever since CSAs were developed): The IAEA’s country-specific fact sheets \[[75](#bib.bib75)\], which list safeguards agreements for each country, show that various involved countries (e.g. Mexico, Peru, Guatemala, Brazil, Thailand, Cambodia, Singapore, Vietnam, Laos, Philippines, Indonesia, and Malaysia) have all lacked distinct NWFZ-specific agreements in addition to their NPT agreements (as we might expect if the agreements were different) ever since the IAEA developed CSAs. (Some countries in Latin America, such as Mexico, had NWFZ-specific agreements before CSAs were developed.) In some relevant cases (e.g., Brazil), states and the IAEA have explicitly clarified that CSAs fulfill a country’s NWFZ obligations \[[76](#bib.bib76)\]. Discussion of the IAEA having distinct safeguards for implementing NWFZ treaties is not prominent in descriptions of IAEA safeguards, including the sources cited in this report.
[^116]: These are: exchanges of reports (although nothing is specified to be nearly as extensive as reports that the IAEA requires) and requests for clarification when there are odd findings. The South Pacific and Southeast Asia treaties also authorize these regional international organizations to carry out special on-site inspections at any suspected location \[[77](#bib.bib77)\]\[[74](#bib.bib74)\].
[^117]: These agreements tend to involve the rogue state agreeing to accept IAEA inspections and to end certain nuclear activities (often including ones that are usually legal but facilitate later nuclear weaponization, e.g. certain uranium enrichment, plutonium reprocessing, and R&D activities) in exchange for economic or security incentives (e.g. lifted sanctions, oil, and assurances that nuclear weapons would not be used against them).
[^118]: All three of these agreements were abandoned, often openly. Still, the latter two were complied with for years, so they likely slowed down North Korea and Iran’s nuclear weapons programs, respectively.
[^119]: This is the only one of these provisions that would apply indefinitely. The JCPOA’s other agreed-on verification mechanisms were set to expire in 10-25 years.
[^120]: Specifically, the IAEA would continuously monitor centrifuge production areas, excess centrifuge storage areas, uranium mines, and uranium mills, and it would monitor heavy water storage and production areas, through measures including (for some of these facilities) containment & surveillance methods, item counting, item numbering, and/or daily inspections.
[^121]: The motivation is that, if a state has no nuclear facilities to which it can divert nuclear material, there is less risk that it will quickly develop nuclear weapons from diverted nuclear material. In integrated safeguards, safeguards are relaxed in that timeliness and detection probability goals are lowered, which leads to inspections being done less frequently, as well as to fewer samples being analyzed. These changes may have been largely implemented to avoid having APs raise safeguard implementation costs.
[^122]: More precisely, states that also have APs agree to inform the IAEA of the locations and activities of these operations and to grant ”complementary access”: access for inspectors, upon request with 24 hours’ notice. In this access, inspectors may use most of the safeguards discussed [above](#S3.SS2 "3.2 M&V for horizontal nonproliferation agreements ‣ 3 Nuclear M&V Systems ‣ Nuclear Arms Control Verification and Lessons for AI Treaties"), although they have neither the information nor the authority to verify nuclear materials accounts. (States are not required to keep detailed accounts of these operations, and the Model Protocol states that the IAEA ”shall not mechanistically or systematically” try to verify information about these additional operations \[[36](#bib.bib36)\].)
[^123]: See the next appendix on why special inspection rights under CSAs were inadequate.
[^124]: Additionally, the IAEA could conclude that a state has undeclared nuclear facilities by detecting that some nuclear material had been diverted from peaceful purposes and the material was not accounted for in any declared facility.
[^125]: The IAEA only began using satellite imagery in the 1990s, following failures to detect undeclared nuclear facilities, although it considers them to have been authorized by the original CSAs \[[78](#bib.bib78)\].
[^126]: It may be convenient for the IAEA to be able to draw conclusions from the premise that all uranium originating from a state’s nuclear mines or mills is accounted for. However, under CSAs, that is not feasible, as CSAs explicitly do not establish safeguards (e.g., accounting) at uranium mines or mills, and perhaps international uranium flows would be difficult to track.
[^127]: Heat can be identified in satellite images if the satellites sense infrared radiation (which all hot objects emit), rather than just sensing visible light. Alternatively, heat can be identified in satellite images by looking for rooftops where snow cover does not build up in the winter.
[^128]: Voluntary reports from third parties could be dismissed as misinformation or disinformation \[[80](#bib.bib80)\], state self-reporting of nuclear facilities could leave out undeclared facilities, and satellite images or other open-source information could have non-incriminating explanations.
[^129]: As evidence for this claim, a report by the Institute for Science and International Security explains, ”The IAEA does not often call for a special inspection—this is reserved for extreme situations where a particularly egregious safeguards violation is suspected and where the member state has demonstrated a lack of cooperation” \[[81](#bib.bib81)\]. A paper by the director of the nuclear non-proliferation program of a major think tank at least roughly agrees: ”Seoul, Tokyo, and Washington consider IAEA monitoring—even enhanced by special inspections—to be inadequate because of the limitations of the IAEA’s special inspection authority. Special IAEA inspections can be undertaken, for example, only after credible evidence of a safeguard violation has been presented, a requirement that will make such inspections highly unusual and create a political ”threshold” to their use” \[[82](#bib.bib82)\]. (The paper was published in 1992, when APs had not been implemented, so it is presumably about CSAs without APs.) A history of negotiations also agrees \[[66](#bib.bib66)\].
[^130]: For example, when Israel bombed a building in Syria and news outlets speculated that it had held a nuclear reactor, the IAEA did not carry out a special inspection \[[81](#bib.bib81)\].
[^131]: For example, the IAEA \[[23](#bib.bib23)\] found inconsistencies in additional information that Syria provided on some suspected materials, reporting that, ”Syria has stated that \[some\] material was to be used for shielded radiation therapy rooms at hospitals \[…\]. However, the end use of the \[material\] as stated in the actual shipping documentation indicates that the material was intended for acid filtration.” As another example, Iran informed the IAEA that there had been no activity at some suspected location over a particular time period; the IAEA \[[48](#bib.bib48)\] reported that this was ”inconsistent with the \[IAEA’s\] observations through the analysis of commercially available satellite imagery.”
[^132]: For example, the IAEA \[[23](#bib.bib23)\] reports that Syria did not respond to some of their requests for information and documentation about a suspected facility. As another example, the IAEA \[[48](#bib.bib48)\] reports that, when it asked Iran about suspected locations, ”Iran provided no answers.”
[^133]: What do experts at the IAEA say? The IAEA gives few details about its processes for identifying locations that might host undeclared nuclear facilities, although it occasionally refers vaguely to information from ”third parties” \[[83](#bib.bib83)\]. An IAEA report expresses confidence in the abilities of intelligence agencies to detect undeclared facilities: ”it is probable that \[intelligence\] services would detect the construction by another State of any significant facility which should have been but was not reported to the IAEA under the provisions of the relevant safeguards agreement. The State which discovered the facility would be free to draw the fact to the attention of the Board of Governors” \[[84](#bib.bib84)\].
[^134]: These states, as well as Libya, South Korea, and Yugoslavia, are the NPT non-nuclear-weapon states that pursued nuclear weapons \[[45](#bib.bib45)\]. However, the latter three did not have secret nuclear facilities inspected by the IAEA. (The IAEA \[[87](#bib.bib87)\] just inspected Libya’s ”previously undeclared” nuclear facilities.)
[^135]: As a limitation of these examples’ scope, they are almost all about states that did not have APs in force.
[^136]: These facilities are commonly believed to have been revealed by an Iranian dissident group, but some analysts compellingly argue that the U.S. intelligence community tipped off the IAEA first \[[89](#bib.bib89)\].
[^137]: Compared to the IAEA or nonprofit analysts, intelligence agencies are presumably much more capable of (e.g., they have much more experience with) spying, intercepting electric signals, and monitoring relevant supply chains. They are also more capable of satellite imagery analysis, because they have e.g. higher-resolution photos (and this advantage was even more extreme historically, before the rise of commercial satellite imagery \[[92](#bib.bib92)\]).
[^138]: These include all sources cited in this report.
[^139]: After international backlash to its invasion of Kuwait, Iraq’s government planned to divert uranium from a safeguarded reactor, but this plan was canceled after other equipment—which was necessary for weaponizing the uranium—was accidentally destroyed by the U.S.-led coalition’s bombing. Yugoslavia’s nuclear weapons program planned on getting nuclear materials from its civil nuclear infrastructure, but the program was canceled before they reached that step.
[^140]: These include the sources cited in this paper.
[^141]: Here, ”integrity” refers to having whichever hardware features they are supposed to have (according to some agreement on AI), i.e. having been designed appropriately and not tampered with.
[^142]: Precisely which types of chips, equipment, or data centers would need to be monitored is an open question.
[^143]: Here, ”elimination facilities” refers to facilities that destroy chips that will no longer be used (e.g. for recycling their metals).
[^144]: This limits the scope of inspections needed, though additional measures may be needed to let individuals have commodity chips without this being a loophole.
[^145]: Technically, the term ”many” should refer to a lower number in the subproblems than in the overall problem, so that the margin of error that is accepted when addressing the subproblems does not add up to an overall margin of error that is too high.
[^146]: This and the other types of inspections in quotes are not terms from nuclear arms control.
[^147]: Additionally, to ensure inspectors have inspection access to enough AI chips (rather than storage facilities always having the option to say they recently shipped out chips inspectors are asking to see), data centers and storage facilities could be required to hold AI chips for some minimum period between receiving and shipping them (similarly to how the IAEA uses ”mailbox declarations”).
[^148]: This refers to the inspector activities described below, except the design information verification.
[^149]: Room functions could be declared as parts of design information verification.
[^150]: In addition to inspecting chips shortly after their production, it might also be feasible to directly inspect chip-making machines, to verify that they are built to introduce the desired devices from the start. However, that might be significantly more technically challenging and operationally disruptive, while potentially also raising stronger information security concerns.
[^151]: It may be most efficient for these to be done concurrently with other types of inspections, as is suggested by New START’s consolidation of inspection types.
[^152]: This is the case when a violation would involve a large number of non-compliant items and a not-vastly-larger number of compliant items; then, random (independent) sampling tends to quickly find non-compliant items (by the central limit theorem).
[^153]: One issue that has been glossed over is attribution; enforcement of treaties with more than two parties presumably requires knowing not just whether a violation occurred but also who committed it. Still, with the addition of security requirements across the supply chain (to make discreet theft more difficult), the system as described above seems plausibly adequate for attribution. This is because violations would be tied to a specific facility (or vehicle), facility (or vehicle) owner, and host state (and potentially to a specific international heist), and these could be investigated further if a violation were detected.
[^154]: From counting the detection measures discussed above, we can see that the system has at least two layers of defense for detecting each potential method to get AI chips to undeclared locations, as well as two or more additional layers for detecting each potential method to store and use AI chips at undeclared locations. This reasoning assumes that there are no potential methods to possess and use many AI chips at undeclared locations other than the methods that are considered and countered above; we can assume this because: Chips at undeclared locations can have either been produced secretly or not, in which case (since location reporting is required) they must have at some point been moved from a declared location to an undeclared location. If all sites containing chip-making machines, all the chip-making machines at these sites, and their chip production levels are all truthfully reported on, then there must be no secret production of chips. If chips whose production is truthfully declared are not diverted from their production facilities or any other places where they are permitted to be, then they are not diverted. Finally, the system has a further layer: human sources.
[^155]: These are: tampering detection inspections, video surveillance, and human sources
[^156]: These layers appear highly reliable (i.e. appear capable of achieving an at at least a 90% detection probability for each attempted violation): For verification that chips do not reach undeclared locations, the combination of the following: in-line instrumentation, the combined methods for detecting undeclared chip-making machines, diversion detection inspections, and a required waiting period before elimination of old AI chips For verification of non-tampering, the above (to verify that there are not many AI chips that have been tampered with and are at secret locations, since not many AI chips are at secret locations) together with tampering detection inspections
[^157]: That is, for (former) U.S.-U.S.S.R./Russia nuclear arms control verification and for the IAEA’s verification of the Non-Proliferation Treaty
[^158]: In other words, the argument here is that, even if AI chip production grew exponentially, this would not involve much proportionally larger costs than IAEA inspections involve. We may assume proportional costs are more relevant to stakeholders than absolute costs.
[^159]: The dataset of Strohmaier _et al_. shows that the 500th highest-performing data center has  0.16% the throughput of the highest-performing one and  14% the throughput of the 50th-highest.
[^160]: Prominent semiconductor manufacturing companies such as TSMC \[[115](#bib.bib115)\], Samsung \[[116](#bib.bib116)\], Intel \[[117](#bib.bib117)\], and SMIC \[[118](#bib.bib118)\] each report under 20 modern semiconductor manufacturing facilities.
[^161]: This seems conservative; an IAEA report explains that, ”The inventory in the facility \[…\] may be upwards of a hundred tonnes of material in a variety of forms such as pure powder, assemblies, rods, unsintered pellets, sintered pellets, reject materials awaiting recycle, and scrap material in a variety of inhomogeneous forms” \[[119](#bib.bib119)\].
[^162]: The PaLM paper used  6,000 chips over  2 months \[[121](#bib.bib121)\].
[^163]: A general formula, derivable by assuming that random sampling of items is done independently and with replacement (which is a slightly conservative approximation of sampling without replacement), is that the number of chips that need to be examined is $F\cdot\log(1-p)/\log(1-M/N)$, where p is the probability of detecting a violation, M is the number of chips needed for a serious violation, N is the total number of chips one is sampling from, and F is the annual frequency at which examinations need to occur. This is a slight variant of the equation proposed by Shavit \[[1](#bib.bib1)\]; his equation is approximately equivalent to this one, given the parameter choices in this report (since, then, $e^{-fT}$ is negligible, and $M/N\approx H/(aTC)$).
[^164]: This can be computed from the formula in the previous footnote (for a wide range of multipliers, from 2x to e.g. 1,000,000x).
[^165]: From a starting point of 2.5 billion AI chips, each costing (let us conservatively assume) $1,000 each, spending on AI chips would already be $2.5 trillion, which is estimated to be approximately the current global spending on R&D \[[124](#bib.bib124)\]. Assuming that the ratio of R&D spending to GWP stayed constant and that the vast majority of AI chips were used for R&D (i.e. AI training runs), a  2x increase to the number of chips would thus require a  2x increase to GWP. Even conservatively assuming that AI chip spending as a fraction of GWP could rise to 20%, the resulting increase in the ratio of items examined to GWP would be bounded by a factor of  8, and that is conservatively assuming that $2.5 trillion were spent on AI chips with no GWP growth.
[^166]: An IAEA publication, though it does not report average lengths of time for which inspections disrupt nuclear facilities’ operations, writes, ”A physical inventory verification at a large facility can be so complex and time-consuming that it might take up to 10 inspectors 7 to 14 days to complete \[…\] physical inventory verifications are conducted once a year in most of the 700 facilities that are under IAEA safeguards worldwide” \[[120](#bib.bib120)\]. Other IAEA publications \[[119](#bib.bib119)\]\[[126](#bib.bib126)\] clarify that inventories (tend to) involve a shut-down.
[^167]: This follows from the formula in the previous footnote. In the context of the assumptions made above, that formula implies  0.023% of the sampled-from chips are selected for examination (across the whole range of N), and 0.023%\*100/365  = 0.006%.

---
title: "Frontier AI Auditing: Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies"
author:
  - "Miles Brundage"
  - "Noemi Dreksler"
  - "Aidan Homewood"
  - "Sean McGregor"
  - "Patricia Paskov"
  - "Conrad Stosz"
  - "Girish Sastry"
  - "A. Feder Cooper"
  - "George Balston"
  - "Steven Adler"
  - "Stephen Casper"
  - "Markus Anderljung"
  - "Grace Werner"
  - "Soren Mindermann"
  - "Vasilios Mavroudis"
  - "Ben Bucknall"
  - "Charlotte Stix"
  - "Jonas Freund"
  - "Lorenzo Pacchiardi"
  - "Jose Hernandez-Orallo"
  - "Matteo Pistillo"
  - "Michael Chen"
  - "Chris Painter"
  - "Dean W. Ball"
  - "Cullen O'Keefe"
  - "Gabriel Weil"
  - "Ben Harack"
  - "Graeme Finley"
  - "Ryan Hassan"
  - "Scott Emmons"
  - "Charles Foster"
  - "Anka Reuel"
  - "Bri Treece"
  - "Yoshua Bengio"
  - "Daniel Reti"
  - "Rishi Bommasani"
  - "Cristian Trout"
  - "Ali Shahin Shamsabadi"
  - "Rajiv Dattani"
  - "Adrian Weller"
  - "Robert Trager"
  - "Jaime Sevilla"
  - "Lauren Wagner"
  - "Lisa Soder"
  - "Ketan Ramakrishnan"
  - "Henry Papadatos"
  - "Malcolm Murray"
  - "Ryan Tovcimak"
source_url: "https://arxiv.org/html/2601.11699v4"
published: 2026-01-16
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

## Executive Summary

### Key paper takeaways

-   •
    
    Despite their rapidly growing importance, AI systems are subject to less rigorous third-party scrutiny than many of the other social and technological systems that we rely on daily such as consumer products, corporate financial statements, and food supply chains. This gap is becoming increasingly untenable as AI becomes more capable and widely deployed, and it inhibits confident deployment of AI in high-stakes contexts.
    
-   •
    
    Transparency alone cannot enable well-calibrated trust in the most capable (“frontier”) AI systems and the companies that build them: many safety- and security-relevant details are legitimately confidential and require expert interpretation, and third parties are right to be skeptical of companies “checking their own homework” given the track record of that approach in other industries.
    
-   •
    
    We outline a vision for frontier AI auditing, which we define as rigorous third-party verification of frontier AI developers’ safety and security claims, and evaluation of their systems and practices against relevant standards, based on deep, secure access to non-public information.
    
-   •
    
    Frontier AI audits should not be limited to a company’s publicly deployed products, but should instead consider the full range of organization-level safety and security risks, including internal deployment of AI systems, information security practices, and safety decision-making processes.
    
-   •
    
    We describe four AI Assurance Levels (AALs), the higher levels of which provide greater confidence in audit findings. We recommend AAL-1 as a baseline for frontier AI generally, and AAL-2 as a near-term goal for the most advanced subset of frontier AI developers.
    
-   •
    
    Achieving the vision we outline will require (1) ensuring high quality standards for frontier AI auditing, so it does not devolve into a checkbox exercise or lag behind changes in the industry; (2) growing the ecosystem of audit providers at a rapid pace without compromising quality; (3) accelerating adoption of frontier AI auditing by clarifying and strengthening incentives; and (4) achieving technical readiness for high AI Assurance Levels so they can be applied when needed.
    

### Frontier AI auditing motivations

Artificial intelligence (AI) is rapidly becoming critical societal infrastructure. Every day, AI systems inform decisions that affect billions of people. Increasingly, they also make consequential decisions autonomously. Although these technologies hold incredible promise, the pace of development and deployment has outpaced the creation of institutions that ensure AI works safely and as advertised.

This institutional gap is especially important for the most capable (“frontier”) systems — general-purpose AI models and systems whose performance is no more than a year behind the state-of-the-art — which many experts expect to exceed human performance across most tasks within the coming years. Already, developers of frontier AI systems need to prevent harmful system failures (e.g., outputting false medical information or buggy code), weaponization by malicious parties (e.g., to carry out cyberattacks), and theft of or tampering with sensitive data. The magnitude of risks that need to be managed is growing rapidly.

AI users, policymakers, investors, and insurers need reliable ways to verify that promised technical safeguards exist and to detect when they do not. This is challenging because the technology is complex, fast-moving, and often proprietary. Public transparency alone cannot solve this problem since many key details are — and often should remain — confidential, and require expert judgment to interpret. Many industries outside of AI already address similar challenges through independent auditors who review sensitive, non-public information and publish trustworthy conclusions that outsiders can rely on. We argue that similar practices are needed in the AI industry: broad, sustainable adoption of AI over time requires a solid foundation of trust built on credible scrutiny by independent experts.

Toward this end, we propose institutions designed to give stakeholders — including those who are uncertain about or even strongly skeptical of frontier AI companies — justified confidence that this critical technology is being developed safely and securely. Specifically, we describe and advocate for frontier AI auditing: rigorous third-party verification of frontier AI developers’ safety and security claims, and evaluation of their systems and practices against relevant standards, based on deep, secure access to non-public information.

An ecosystem of private sector frontier AI auditors (both for-profit and non-profit) would enable widespread confidence that frontier AI systems can be adopted broadly and would avoid reliance on companies “grading their own homework,” an approach with a checkered track record in many industries. It would also avoid relying entirely on governments to have the technical expertise, capacity, and agility to ensure high standards for frontier AI safety and security. If well-executed and scaled, frontier AI auditing would improve safety and security outcomes for users of AI systems and other affected parties, create a system to learn and update standards based on real-world outcomes, and enable more confident investment in and deployment of frontier AI, especially in high-stakes sectors of the economy.

### Summary of the proposal

Drawing on our analysis of current practices in AI and lessons from other industries with more mature assurance regimes, we recommend eight interlinked design principles for a long-term vision for frontier AI auditing. This vision is deliberately ambitious to match the rising stakes as frontier AI capabilities advance:

-   •
    
    Scope of risks: Comprehensive coverage of four key risk categories. Frontier AI auditing should focus on four risk categories: risks from (1) intentional misuse of frontier AI systems (e.g., for cyberattacks); (2) unintended frontier AI system behavior (e.g., errors harming the user, their property, or third parties due to pursuing the wrong goal or having an unreliable performance profile); (3) information security (e.g., theft of an AI model or user data); and (4) emergent social phenomena (e.g., addiction to AI or facilitation of self-harm). For each category of risks, auditors should (a) verify company claims and (b) evaluate the company’s systems and practices against its stated safety and security policies, applicable regulations, and industry best practices.
    
-   •
    
    Organizational perspective: Auditing companies’ safety and security practices as a whole, not just individual models and systems. Auditors should use an organization\-level perspective to avoid abstraction errors (i.e., forming the wrong conclusion by treating a partial or simplified unit of analysis, such as evaluating a specific component in isolation, as if it were sufficient to assess overall system and organizational risk). Risk does not come from AI models alone; it emerges from the interaction of three overarching components: digital systems, computing hardware, and governance practices, and harm can arise even when a model is never deployed in external-facing systems. Rigorous, but isolated, model and system evaluations are therefore insufficient to evaluate all safety and security claims on their own. And while individual audits may focus on particular domains depending on their goals, the ecosystem as a whole should ensure comprehensive coverage across all three components in assessing safety and security claims.
    
    Figure 1: Four AI Assurance Levels (AALs) for different frontier AI audits.
    
-   •
    
    Levels of assurance: A framework for calibrating and communicating confidence in audit conclusions. Not all audits provide the same level of certainty, and stakeholders need to understand these differences. We propose AI Assurance Levels (AALs) as a means of clarifying what kind of assurance particular frontier AI audits provide (Figure [1](#Sx1.F1 "Figure 1 ‣ 2nd item ‣ Summary of the proposal ‣ Executive Summary ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")). At lower levels, auditors and other stakeholders rely more heavily on information provided by the company and can primarily speak to a particular system’s properties. At higher levels, auditors take fewer assumptions for granted, and assess the full range of relevant company systems, organizational processes, and risks. At the highest level, auditors can rule out the possibility of materially significant deception by the auditee. Determining the appropriate AAL for different contexts and purposes is complex, but we recommend AAL-1 (the peak of current practices in AI) as a starting point for frontier AI generally, and AAL-2 as a near-term goal for the companies closest to the state-of-the-art. AAL-2 involves greater access to non-public information, less reliance on companies’ statements, and a more holistic assessment of company-level risks. The two highest assurance levels (AAL-3 and AAL-4) are not yet technically and organizationally feasible, but we outline research directions to change this.
    
-   •
    
    Access: Deep enough to assure auditors and other stakeholders, secure enough to reassure auditees. Frontier AI auditors should receive deep, secure access to non-public information of various kinds — including model internals, training processes, compute allocation, governance records, and staff interviews — proportional to the audit’s scope and the level of assurance being sought for the audit. Access arrangements should protect intellectual property and security\-sensitive information using mechanisms imported from other domains (e.g., sharing certain information with a subset of the auditing team on-site under a restrictive nondisclosure agreement) and newly-developed techniques (e.g., AI-powered summarization or analyses of information that is too sensitive to be directly shared).
    
-   •
    
    Continuous monitoring: Living assessments, not stale PDFs. AI systems change constantly, including through adjustments to the underlying model(s), surrounding software, and shifts in user behavior. An audit conclusion that was accurate at the time of the assessment may become misleading in some respects within days or weeks. Audit findings should therefore carry explicit assumptions and validity conditions, and should be automatically deprecated when key underlying assumptions no longer hold. A mature auditing ecosystem will combine periodic deep assessments of slower-moving elements (e.g., governance, safety culture) with event-triggered reviews of major changes (e.g., new releases, serious incidents) and continuous automated monitoring of fast-changing surfaces (e.g., API behavior, configuration drift), enabling timely detection of changes that could invalidate prior conclusions.
    
-   •
    
    Independent experts: Trustworthy results through rigorous independence safeguards and deep expertise. Auditors must be genuinely independent third parties, free from commercial or political influence, and have deep expertise across AI evaluation, safety, security, and governance. Safeguarding independence requires mandatory disclosure of financial relationships, standardized terms of engagement that prevent companies from shopping for favorable auditors, and cooling-off periods when moving, in both directions, between industry and audit roles. Alternative payment models that reduce auditor dependence on auditees should also be urgently explored. Where single auditing organizations lack sufficient expertise, subcontracting and consortia models can enable the necessary breadth across AI evaluation, safety, security, and governance.
    
-   •
    
    Rigor: Processes that are methodologically rigorous, traceable, and adaptive. Audits should follow a standardized process while giving auditors the autonomy to flexibly determine specific methods and adjust scope as issues emerge. Auditors should be able to define evaluation metrics and criteria rather than simply validating companies’ preselected approaches. Wherever feasible, audit procedures should be automated, transparent, and reproducible to support consistent application across engagements and enable continuous monitoring as systems evolve. Auditors need to safeguard evaluation construct and ecological validity, and audit criteria should be protected against gaming. Finally, audits should incorporate procedural fairness, giving companies structured opportunities to correct factual errors while preventing undue influence on conclusions.
    
-   •
    
    Clarity: Clear communication of audit results. Stakeholders must be able to understand the audit results. These should be communicated in audit reports with a standardized structure, covering the audit’s scope, level of assurance, conclusions, reasoning, and recommendations. Results should be communicated appropriately to different stakeholders: to protect sensitive information, auditors and companies can publish summarized or redacted versions for external stakeholders while sharing full, unredacted audit reports with boards, company executives, and, in some cases, regulatory bodies.
    

### Challenges and next steps

Our long-term vision will require concrete efforts by several categories of stakeholders to both achieve and maintain. The most urgent challenges are:

-   •
    
    Ensuring high quality standards for frontier AI auditing, so it does not devolve into a checkbox exercise or lag behind changes in the AI industry.
    
-   •
    
    Growing the ecosystem of audit providers at a rapid pace without compromising quality.
    
-   •
    
    Accelerating adoption of frontier AI auditing by clarifying and strengthening incentives.
    
-   •
    
    Achieving technical readiness for high AI Assurance Levels so they can be applied when needed.
    

These challenges are substantial but not unprecedented. Companies routinely share sensitive information with financial auditors, potential acquirers, penetration testers, and consumer product testing laboratories under carefully controlled terms. We believe similar practices for AI safety and security are both achievable and urgently needed. For each of the challenges we describe, we recommend specific next steps:

Figure 2: Recommendations for next steps across four challenges in frontier AI auditing.

Keeping up with the rapid pace of AI progress and deployment requires quickly importing best practices from more mature industries and immediate investment in auditing pilots, technical research, and policy research. Moving with urgency is essential if frontier AI auditing is to reach maturation and scale alongside AI development.

Contents

## 1  Introduction

Frontier AI systems are rapidly transforming society \[bengio\_international\_2025, maslej\_artificial\_2025\]. While many frontier AI developers invest substantially in safety and security, the details of how these systems are built, evaluated, and safeguarded remain largely opaque to external stakeholders \[wang\_2025\_foundation\_2025\] — users, insurers, investors, and policymakers alike. And yet, external stakeholders are the ones most affected by the systems’ downstream impacts, bearing both the benefits and risks of outcomes that they have little ability to scrutinize or contest.

Today, most third-party assessments rely on public information and publicly accessible products \[reuel\_who\_2025\]. These are valuable but insufficient. Such public information rarely provides the detail necessary to offer meaningful assurances about system behavior, including the precise conditions under which an evaluation was conducted, whether conclusions drawn from evaluations meaningfully generalize, or whether negative findings were softened or withheld. As frontier AI systems become more capable and more widely deployed, assurance provided solely by analyzing information and systems that frontier AI companies choose to disclose publicly will be less and less tolerable.

Meaningful assurance requires independent access to non-public technical and organizational information \[casper\_black-box\_2024\]. When developers do grant such access, they typically do so through bespoke contracts with terms rarely visible to the public (see \[openai\_openai\_2023\]). Standards for how companies should work with third-party AI assessment organizations are nascent, and developers can substantially influence the timing, scope, and publication of any assessments conducted that involve non-public information.

This opacity contrasts sharply with oversight of other critical technologies and institutions in at least two important respects. First, frontier AI is advancing at unprecedented speed, outpacing the development of corresponding governance frameworks and structures \[reuel\_open\_2025, maslej\_artificial\_2025\]. Second, unlike earlier transformative technologies that were deployed within more specific, well-defined domains, frontier AI is being integrated horizontally across many critical sectors at once. By contrast, many sector-specific technologies — cars, airplanes, food supply chains — are often subject to more rigorous independent scrutiny \[hodgkinson\_iosa\_2005, koppel\_how\_2008, warriner\_understanding\_2013\]. In many cases, such oversight began only after major disasters \[johnson\_process\_2005, baker\_institutional\_2006, sutton\_sems\_2014\], and avoiding the greatest risks of AI systems requires greater foresight to forestall catastrophe. By forming “soft law” \[wallach\_soft\_2023\], early norms around access, evaluation, and disclosure can play a crucial role in shaping what more formal, future oversight can realistically demand.

To meet the demands of this critical moment, this paper presents our vision: frontier AI auditing. We define frontier AI auditing as rigorous third-party verification of frontier AI developers’ safety and security claims about systems throughout development and deployment, combined with the ongoing evaluation of their systems and practices against relevant standards, based on deep, secure access to non-public information.

Rather than suggesting a one-size-fits-all approach to all audits, our goal is to provide an initial vocabulary for this emerging field — one that can be adapted based on context, including the level of assurance required in a particular case. Toward this end, we propose standardized AI Assurance Levels (AALs) that clarify the assumptions required in order to trust a particular audit’s conclusions.

Auditing complements internal safety practices and external regulation — it doesn’t replace them. Critically, there needs to be a meaningful set of safety and security standards against which companies can be audited and for which there are strong incentives to comply. Auditing also entails real costs that rise with the assurance level being sought. While some costs may fall through automation and other efficiency improvements, some costs will always remain, making it important to efficiently allocate auditing activity while maintaining high-quality standards.

Our paper proceeds as follows:

-   •
    
    [section 2](#S2 "2  Key Terminology and Scope ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") defines the key terminology used in the paper and clarifies the scope of the discussion.
    
-   •
    
    [section 3](#S3 "3  Motivations: Why Frontier AI Auditing is Needed ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") explains why frontier AI auditing is an appropriate response to the growing gap between AI’s impact and the external scrutiny applied to it.
    
-   •
    
    [section 4](#S4 "4  Lessons from Related Domains and Current AI Assessment ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") draws lessons from other industries with mature third-party assurance ecosystems and examines current assessment practices in the AI sector.
    
-   •
    
    [section 5](#S5 "5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") details our vision for frontier AI auditing, covering scope, organization-level focus, assurance levels, access needs, continuous monitoring, independence, rigor, and communication of outputs.
    
-   •
    
    describes the challenges in achieving this vision and proposes directions for addressing them.
    
-   •
    
    takes stock of the paper’s contributions and summarizes proposed next steps.
    
-   •
    
    Appendices cover a range of topics: a glossary of key terms; additional motivations for frontier AI auditing not covered in Section 3; details on access requirements; placing AI auditing in context of other AI policy topics; more details on our lessons learned from other domains and from contemporary AI assessment practices; and a more detailed discussion of different ways that frontier AI auditing could be funded.
    

### How to read this paper

Those less familiar with the terminology used above should read [section 2](#S2 "2  Key Terminology and Scope ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") and consult as needed. Most readers should read [section 3](#S3 "3  Motivations: Why Frontier AI Auditing is Needed ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") in order to understand the specific problems we think frontier AI auditing would help address. Those familiar with current AI assessment limitations can skip to [section 4.1](#S4.SS1 "4.1 Key lessons from more established assessment domains ‣ 4  Lessons from Related Domains and Current AI Assessment ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") for lessons from other industries, then proceed directly to [section 5](#S5 "5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") for our proposal. Researchers, engineers, industry executives, policymakers, and philanthropists interested in ways they can accelerate frontier AI auditing may be especially interested in (Challenges and Next Steps). Appendices may be of interest to researchers or policymakers interested in various specific details.

## 2  Key Terminology and Scope

In this report, we describe and advocate for frontier AI auditing, which we define as (1) rigorous third-party evaluation of frontier AI developers’ systems and practices against relevant standards and (2) rigorous third-party verification of frontier AI developers’ safety and security claims, both based on deep, secure access to non-public information. In general, when we refer to verification, we mean the activity of confirming whether a specific claim, commitment, or property (e.g., a training compute figure) is true. Evaluation refers to any activity that measures, characterizes, or analyzes properties of AI models or systems and the organizations operating them. More generally, assessments are activities that involve evaluation, verification, or both (see Figure [3](#S2.F3 "Figure 3 ‣ 2  Key Terminology and Scope ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")). And so the frontier AI audits we describe are a particular type of third-party assessment concerning AI systems and the companies that build them.

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/brundage-frontier-ai-auditing-toward-rigorous-third-party-assessment-of-safety-and-security-practices-at-leading-ai-companies-img1-bb1ed73b.png)

Figure 3: Understanding key concepts: how assessments relate to evaluation, verification, and audits.

In this section, we clarify the specific scope of our focus on frontier AI auditing.

We focus specifically on frontier AI. Frontier AI includes general-purpose AI models and systems whose performance is no more than a year behind the state-of-the-art on a broad suite of general capability benchmarks (see Figure [4](#S2.F4 "Figure 4 ‣ 2  Key Terminology and Scope ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")). The risks and capabilities of the most capable systems, all else equal, are the least well understood by virtue of being new \[ganguli\_predictability\_2022, cooper\_report\_2023\], making rigorous auditing particularly important. With respect to the AI components of frontier AI systems, we focus on closed-weight models, or those whose weights are not publicly released and thus cannot be freely copied or redistributed. Open-weight models have distinct challenges and affordances, and only a subset of what we discuss here is relevant to {--{"author":"Luc's AI","timestamp":1787602160654}@@them.[^1]--}{++{"author":"Luc's AI","timestamp":1787602160654}@@them.[^note-1]++} We define frontier AI in terms of capabilities — rather than through characteristics like computational power or money spent on research and development — because capabilities are more directly related to the risks resulting from the production and deployment of frontier AI systems.

There are many other ways to define frontier AI, as well as different ways to determine whether an AI system or company should be audited, besides frontier status. While important, we don’t think these differences significantly change the basic ideas in the rest of the paper, so we reserve more detailed discussion to .

Figure 4: Understanding frontier AI. The frontier advances over time as the state-of-the-art capability level increases, so a system is considered frontier if it remains within a fixed lag (e.g., 1 year) of the state-of-the-art at a given point in time.

We focus on companies that develop frontier AI. Frontier AI developers are the companies that produce frontier AI systems: the entities that train models from scratch themselves, or significantly extend model capabilities (e.g., via further training of a preexisting frontier AI model, or the addition of significant new system-level features to a model, such as tool use). Developers often (though not always) deploy these models themselves, embedding models in software systems for both internal and external use. Many companies only deploy or integrate systems built by others, but do not significantly extend the underlying models’ capabilities, and we do not discuss auditing of those companies {--{"author":"Luc's AI","timestamp":1787602129054}@@here.[^2]--}{++{"author":"Luc's AI","timestamp":1787602129054}@@here.[^note-2]++} We focus on developers because they control the basic nature of AI systems’ capabilities and behaviors. Unless otherwise specified, we use ‘‘developer’’ and ‘‘company’’ interchangeably to refer to the frontier AI {--{"author":"Luc's AI","timestamp":1787602129558}@@developer.[^3]--}{++{"author":"Luc's AI","timestamp":1787602129558}@@developer.[^note-3]++}

We focus on frontier AI systems throughout their development and deployment. Organizations and software systems evolve over time. This is particularly the case for frontier AI. Even with a seemingly stable set of companies at the frontier, new developers can enter the market at any time. Beyond rapid advances in underlying model capabilities, frontier AI systems are continually reshaped by new product offerings, deployment contexts, and design paradigms, such as the integration of models into increasingly autonomous, agentic scaffolds. As a result, assessment of organizations and system behaviors at a single point in time (e.g., pre-deployment) can quickly become outdated or incomplete. Ongoing assessment enables tracking how organizations and systems change in practice, how new uses and incentives change the risk landscape, and how emergent behaviors arise as technologies are combined and scaled in new ways.

We focus on third-party assessments of frontier AI that involve non-public information. When people make decisions on which AI system to license or use, they typically rely on a combination of assessments produced by the company itself and third-party organizations. While the company statements may benefit from substantial insider access, they lack the credibility afforded by statements free of conflicts of interest (i.e., statements from third-parties). However, while third-party assessors may be free of conflicts of interest, they often lack access adequate for assessing risk. Unprivileged assessments have value, and there are various respects in which frontier AI companies could and should share more information publicly than they do today \[ball\_four\_2024\]. But external information is often misleading \[mcgregor\_risk\_2025\] and may not reveal major risks or vulnerabilities that lie below the surface. We expect that non-public information will become increasingly important over {--{"author":"Luc's AI","timestamp":1787602130053}@@time.[^4]--}{++{"author":"Luc's AI","timestamp":1787602130053}@@time.[^note-4]++}

We develop a “menu” of different assurance levels, based on the effort applied to auditing. Audits are a particular kind of assessment: a systematic, evidence-based process where a qualified party examines an organization’s activities, records, technologies, and claims in order to provide assurance that stated information is accurate and/or that applicable standards are being met. This definition leaves open the question of how much effort should be applied in order to build the auditor’s confidence and skeptical third parties’ confidence in the audit’s findings. We propose four different AI Assurance Levels (AALs), corresponding to different degrees of assurance gained through an audit process. Higher levels will tend to be more costly and time-consuming because the auditors take fewer assumptions for granted and verify more claims directly, with the goal of ultimately attaining enough confidence to rule out deception, not just error, and to identify subtle errors that take careful investigation to detect.

We think that there will ultimately be some frontier AI systems that merit the highest AALs: as capabilities improve, the standard of analysis should increase proportionally, and stakeholders will rightly want more confidence that critical risks will not materialize. We therefore recommend a range of directions aimed at making it feasible to reach these high AALs.

Frontier AI auditing takes place “upstream” in the supply chain by design. Safety and security improvements “upstream” in the supply chain improve outcomes across many “downstream” applications built on top of frontier AI systems, and are therefore highly leveraged \[anderljung\_frontier\_2023\]. An audit of a downstream company would be fully credible only if the frontier model or system on which they are building has itself been audited. But achieving effective AI safety and security risk management will likely require a layered approach combining frontier AI auditing with context-specific and sector-specific risk management and deployment-level assessments, to evaluate how these systems act in particular high-risk settings. Frontier AI auditing is an essential piece of the puzzle, but needs to be viewed in a larger context (see ).

## 3  Motivations: Why Frontier AI Auditing is Needed

In this section, we articulate why frontier AI auditing is necessary for meeting the challenges of this current moment — to provide meaningful assurance to external stakeholders that bear the benefits and risks of frontier AI systems. We focus on two motivations for frontier AI auditing: how it can lead to significantly improved safety and security outcomes ([section 3.1](#S3.SS1 "3.1 Improving safety and security outcomes ‣ 3  Motivations: Why Frontier AI Auditing is Needed ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")), and enable more confident investment and deployment ([section 3.2](#S3.SS2 "3.2 Enabling confident investment and deployment ‣ 3  Motivations: Why Frontier AI Auditing is Needed ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")). These motivations often point toward similar auditing practices, but sometimes they diverge in emphasis or design ([section 3.3](#S3.SS3 "3.3 Different audit requirements based on motivation ‣ 3  Motivations: Why Frontier AI Auditing is Needed ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")). This is one reason why we propose a “menu” of assurance levels, which specify how much effort should be applied in different contexts to instill confidence in an audit’s findings. These motivations also point to the need for a private sector-based auditing regime ([section 3.4](#S3.SS4 "3.4 Government vs. private auditing ‣ 3  Motivations: Why Frontier AI Auditing is Needed ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")).

discusses three additional motivations (enabling risk price discovery through insurance, maintaining international stability, and ensuring accountability for risk creation).

### 3.1 Improving safety and security outcomes

Internal evaluations of frontier AI systems tend to be insufficient along two distinct but reinforcing dimensions: (1) limits in frontier AI developers’ abilities to fully understand, anticipate, and characterize the external risks of systems they develop, and (2) misaligned incentives. Auditing can directly address these issues, and the resulting safety and security risks they bring about, by introducing perspectives that challenge internal company narratives, encouraging better internal practices for system assessment, and sharing critical advancements in AI safety and security knowledge across organizations.

First, relative to self-assessment by AI developers, external auditing provides fresh perspectives, which can offer healthy skepticism (i.e., guard against {--{"author":"Luc's AI","timestamp":1787602130545}@@groupthink[^5])--}{++{"author":"Luc's AI","timestamp":1787602130545}@@groupthink[^note-5])++}, while also expanding the range of expertise brought to bear on development and deployment decisions. There is already evidence that third-party assessment can surface safety and security issues that developers subsequently remedy \[raji\_actionable\_2019\]. For example, the UK AI Security Institute (AISI) and US Center for AI Standards and Innovation (CAISI)’s pre-deployment testing efforts \[aisi\_pre-deployment\_2024\] identified safety issues that developers then addressed before release \[anthropic\_strengthening\_nodate, openai\_working\_2025\]. Developers have also noted the value of external review in strengthening internal evaluation processes. System cards documenting behaviors and risks frequently reference third-party benchmarks and findings \[rottger\_safetyprompts\_2025\], sometimes produced with non-public information \[ghosh\_ailuminate\_2025, chollet\_arc\_2025\]. Anticipating independent review may encourage investing in more robust mitigations earlier in development, before potential risks translate to concrete safety and security failures.

Auditing also mitigates a distinct institutional failure of self-assessment: potential misalignment between deployment incentives and judgments about sufficient safety precautions. Frontier AI developers are simultaneously optimizing for capabilities, speed, and market position, while contending with how to determine the conditions under which their own systems are too risky to release or scale. This creates a structural conflict of interest, including internal pressure on safety teams to narrow scope or provide premature sign-off to meet deployment timelines (e.g., \[GoldmanKahn2024OpenAIResigns\]). Independent auditing can separate evaluation and verification of safety properties from commercial incentives.

Beyond individual firms, external auditing enables learning at the level of the ecosystem, rather than just the level of individual developers. Without shared assessment, safety practices remain difficult to compare across organizations, making systemic risk hard to detect until failures occur. Auditors working with multiple companies can identify patterns, disseminate best practices, and share effective mitigations between developers with different levels of maturity. This affords the ability to make direct comparisons across developers, for example, allowing insights from state-of-the-art frontier systems to inform evaluations and safeguards for less capable models that may later encounter similar {--{"author":"Luc's AI","timestamp":1787602131010}@@risks.[^6]--}{++{"author":"Luc's AI","timestamp":1787602131010}@@risks.[^note-6]++}

Notably, while some of the benefits above can be achieved even if only some companies participate, wide participation is important in order to capture the full benefits. Having more participating companies helps broaden the amount of experience that others can learn from, and wide participation can discourage companies from cutting corners in order to gain a short-term advantage at the expense of the larger industry and society \[askell\_role\_2019\]. Even if auditing is made as efficient as possible through technical and process innovations, it will always have some costs, so there is a risk that selective participation will disadvantage responsible developers who incur those costs, while exposing the public to systemic risks from the industry’s weakest links.

### 3.2 Enabling confident investment and deployment

Frontier AI systems are unusually difficult to responsibly invest in and deploy because uncertainty, liability, and information asymmetries compound. Credible third-party auditing unlocks broader AI adoption by giving potential investors and deployers of AI systems better-founded confidence in safety and security claims.

When credible third-party audits play a central role in the deployment ecosystem, enterprises and government agencies can rely on shared, independent assessments rather than attempting to evaluate frontier AI systems on their own. Audits provide a common reference point that enables adoption decisions to scale beyond a small number of technically sophisticated firms. This lowers the cost and complexity of due diligence, particularly for organizations that lag behind the frontier in terms of deep internal AI safety expertise.

Auditing also plays a stabilizing role in legal and regulatory environments that are still in flux. Because standards of care for frontier AI deployment are unsettled, adopters face the risk that decisions made under uncertainty may later be judged negligent after harm occurs. Credible third-party audits help mitigate this risk (or at least bound the scope of it) by documenting that deployment decisions were made in accordance with recognized, independent assessment practices. This makes relevant aspects of reasonable care demonstrable ex ante rather than contestable only after the fact, reducing uncertainty for adopters and investors.

As a consequence of more reliable information, developers that pass rigorous audits gain competitive advantages, as do downstream companies building on audited systems. Audit credentials can differentiate providers in procurement, particularly with governments and regulated industries. Without such mechanisms, frontier AI markets are prone to adverse selection: responsible developers bear higher internal safety costs, while less cautious actors can make similar claims at lower expense. Auditing allows safety, security, and governance quality to become more observable, enabling competition to reward genuinely higher standards rather than marketing alone. Over time, this creates incentives for wider participation, reinforcing auditing as a normal part of market entry rather than an exceptional burden, as it has done in other sectors \[pcaob\_investor\_2025\].

From frontier AI developers’ perspectives, rigorous third-party auditing provides concrete benefits: it can identify safety and security issues before they become costly incidents; build trust with enterprise customers and government agencies hesitant to adopt AI; provide legal clarity, potentially in the form of evidentiary support in court; and differentiate products in competitive procurement processes.

These effects extend to insurance and capital markets. Frontier AI risks are difficult to insure because they are novel, potentially catastrophic, and poorly characterized, leading some insurers to exclude AI-related harms altogether \[yang\_insurance\_2025, noauthor\_insurers\_2025\]. Audits can help unlock two distinct insurance markets: (1) For frontier AI developers, audits provide the standardized, quantifiable risk data that insurers need to underwrite coverage, lowering the cost of capital and clarifying accountability in the event of harm. (2) For businesses building on frontier AI models, audits of the underlying models give insurers visibility into risks that would otherwise be opaque. This allows insurers to differentiate based on audit status (e.g., as shown by a recently proposed underwriting standard from AIUC \[aiuc\_aiuc-1\_2026\]), offering better terms to businesses that choose audited models over unaudited alternatives. See for more discussion of insurance.

As with the safety and security benefits described above, confidence in frontier AI investment and deployment will be greater to the extent that there is wide adoption of auditing, rather than just a few firms participating. High-profile safety incidents, such as the Three Mile Island Accident \[wikipedia\_threemileisland\_accident\], can set back an entire industry \[baron\_public\_2020\] even if there are safer companies or products in the market. There is growing interest in AI-related risks among investors \[tangen\_responsible\_2023\], and frontier AI auditing can help manage such risks.

### 3.3 Different audit requirements based on motivation

Although the motivations for frontier AI auditing share the common foundations of independence, varying levels of non-public access, and standardized frameworks for comparison, they place fundamentally different demands on what an audit must accomplish. In some settings, audits are primarily tools for reducing uncertainty and supporting private decision-making; in others, they are mechanisms for enabling credible commitments where trust, enforcement, or risk-sharing are limited \[harack\_verification\_2025, baker\_verifying\_2025, mitre\_artificial\_2025\] (see also ). These roles cannot be served equally well by a single, undifferentiated notion of “an audit,” and treating these cases as requiring the same level of assurance would either hollow out audits where they must be strongest or make them overly burdensome where lighter-touch approaches would suffice.

This combination of convergence and variation is why we present a single overall vision that includes multiple AI Assurance Levels (AALs); [section 5](#S5 "5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") describes how appropriate AALs can be selected in practice.

### 3.4 Government vs. private auditing

In principle, at least some of the positive outcomes described above are achievable with governments assuming an auditing role. Public agencies can and do play valuable roles in system evaluation, as illustrated by UK AISI and US CAISI’s pre-deployment testing efforts \[aisi\_pre-deployment\_2024\]. However, relying primarily on governments to conduct frontier AI audits faces structural limitations that are especially binding in this domain. Frontier AI systems evolve rapidly, require deep technical specialization, and often demand sustained access to non-public model details, internal processes, and proprietary data. Most governments face persistent challenges in building and retaining the requisite expertise at scale, adapting quickly to new model architectures and risk profiles, and matching the pace of innovation in the private sector. These constraints are not unique to AI, but they are particularly acute given the speed and complexity of frontier model development.

At the same time, a purely private auditing ecosystem without public involvement would be inadequate. Governments have a critical role to play in providing oversight, setting baseline standards, and ensuring democratic accountability. In practice, this includes defining minimum requirements for auditor independence and competence, accrediting or supervising auditing organizations, and enforcing consequences when audits are negligent or misleading. This division of labor mirrors established practice in other domains, such as financial auditing, where private auditors perform evaluations while public authorities set the rules and provide backstop enforcement. In the context of frontier AI, such oversight is essential to ensure that audits retain substantive value rather than devolving into compliance theater.

A largely private-sector auditing regime also offers an additional governance advantage: it limits the concentration of power over AI oversight in any single institutional actor. Governments will inevitably play a central role in AI governance through regulation, enforcement, and national security policy. Assigning primary responsibility for auditing to the private sector helps distribute governance functions across institutions with different incentives, expertise, and failure modes. Taken together, these considerations point toward an auditing ecosystem that is predominantly private in execution but publicly overseen.

## 4  Lessons from Related Domains and Current AI Assessment

Before we detail our vision for frontier AI auditing, we briefly survey two bodies of practice that informed it: more established auditing and assurance practices in other industries and current third\-party assessment in the AI industry. and provide more extensive discussions of these topics.

Historically, many industries introduced rigorous third-party oversight only after serious incidents compelled action. Pharmaceutical pre-market approval, for example, became mandatory only after the 1937 sulfanilamide disaster killed over 100 people, and the 1957–1961 thalidomide tragedy prompted additional efficacy requirements \[ballantine\_sulfanilamide\_1981\]. A degree of aviation certification became mandatory through the Air Commerce Act of 1926, championed by industry leaders who believed “the airplane could not reach its full commercial potential without federal action to improve and maintain safety standards” \[federal\_aviation\_administration\_brief\_nodate\]. Decades later, standards were ratcheted up significantly after high\-profile accidents such as the Grand Canyon crash in 1956 \[FAA\_N6902C\].

The ultimate success of frontier AI auditing would be enabling dramatic safety and security progress without catastrophe as a necessary catalyst.

### 4.1 Key lessons from more established assessment domains

Third-party audits are common across many industries \[anderson-samways\_ai-relevant\_2024\], where carefully designed frameworks facilitate external assessment of sensitive technologies and institutions while protecting intellectual property. We draw lessons from four domains, discussed below and summarized in [Table 1](#S4.T1 "In 4.1 Key lessons from more established assessment domains ‣ 4  Lessons from Related Domains and Current AI Assessment ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies"). See for detailed discussion and examples.

Food safety and consumer product testing. These domains demonstrate that effective safety culture requires “defense in depth”: testing at multiple stages of a product’s lifecycle and for multiple failure modes. Independent testing organizations like Underwriters Laboratories \[underwriters\_laboratories\_inc\_engineering\_2016\] show that companies can opt in and pay for certification if people avoid products lacking trusted third-party assurance. Critically, safety system failures — such as the 2008 Chinese milk scandal \[gossner\_melamine\_2009\] — produce widespread distrust that propagates across companies and can persist for years \[li\_consumer\_2021\]. For frontier AI, these precedents suggest (1) continuous testing throughout the lifecycle, (2) joint industry investment in testing infrastructure, and (3) recognition that a single high\-profile failure can damage the entire industry’s standing.

Safety-critical systems engineering and aviation safety. Industries like aviation and nuclear power treat safety as an emergent property of complex sociotechnical systems, employing structured methodologies — including hazard analysis, safety cases, and continuous lifecycle risk management \[leveson\_introduction\_2023\] — to proactively identify and manage risks. Aviation’s strong safety record involves interlocking elements providing defense in depth: pre-approval of designs, mandatory incident reporting, and criminal liability in some cases. However, at the same time, the Boeing 737 MAX disasters highlighted the catastrophic risks of excessive self-certification and deference, where commercial pressures overrode safety concerns. Key lessons include: (1) systems-level analysis provides greater evidence for safety decisions than component-level analysis alone; (2) near-misses are often early warning signs of eventual failures; (3) effective safety reporting requires structural independence and protection from retaliation; (4) self-certification and delegation of audits create dangerous conflicts of interest; and (5) auditing must be technically rigorous, rather than relying on company attestations. (see and  for in-depth discussions)

Penetration testing. Penetration testing demonstrates that security attributes are often best assessed through active adversarial testing rather than static checklists. Instead of checking only whether documented requirements are met, testers creatively search for unexpected failure modes and chain together subtle weaknesses. The field shows that an adversarial analytical posture can coexist with a collaborative relationship — auditors and companies iteratively fix issues rather than treating audits as one-off pass/fail exercises. Bug bounty programs \[hackerone\_bug\_nodate\] extend this into ongoing, market-based mechanisms with clear incentives. For frontier AI, adversarial testing should be a core component of misuse and security audits.

Table 1: Key lessons drawn from the domains discussed in this section

| Principle | Source Domains | Implication for Frontier AI |
| --- | --- | --- |
| Independence | Financial auditing, aviation | • Auditors need to be incentivized to meet very high standards in their analysis through mechanisms such as regulation, liability, and market pressures that reward rigor • Conflicts of interest need to be managed carefully |
| Defense in depth | Food safety, aviation, consumer products | • Multiple layers of assessment are needed at different lifecycle stages |
| Continuous monitoring | Safety-critical systems, consumer products | • One-off, static certifications are insufficient • Audits must account for systems changing over time |
| Adversarial testing | Penetration testing | • Adaptive red-teaming is needed, not just checking off a list |
| Organizational assessment | Safety-critical systems, financial auditing | • Culture, governance, and security matter, not just specific AI systems |

Financial auditing. Financial auditing offers perhaps the richest set of analogies — both positive and cautionary — for frontier AI auditing. On the positive side, it demonstrates the feasibility of professionalized processes allowing independent parties to review highly sensitive information, the value of standardized metrics for comparing risks across organizations, and the importance of combining verification of specific claims (e.g., financial statements) with broader assessment of internal controls. Financial auditing has developed crucial conceptual tools that are relevant to frontier AI: (1) clear norms for managing conflicts of interest \[booker\_cpas\_2016\], (2) sharp distinctions between error and fraud, and (3) recognition that professional judgment by auditors is indispensable.

However, financial auditing also provides warnings. Catastrophic failures — Enron, Wirecard \[fbi\_enron\_nodate, heese\_wirecard\_2021\] — illustrate what happens when auditors derive most of their revenue from a small number of large clients \[mary\_locatelli\_good\_2002\]. Even after reforms like Sarbanes–Oxley, the sector has struggled with conflicts of interest \[pcaob\_pcaob\_2023\], procedural focus that risks missing systemic issues, and a persistent “expectations gap” between public belief that audits guarantee the absence of fraud and auditors’ more modest mandate. For frontier AI, these suggest the critical importance of auditor independence, clear communication of assurance levels, and avoiding criteria that devolve into box-ticking.

These domains illustrate both the achievements and the pitfalls of common assurance regimes. We do not present these examples as gold standards — rather, we highlight constructive lessons for frontier AI auditing while encouraging thoughtful and deliberate effort to build self-correction mechanisms into the vision outlined in [section 5](#S5 "5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies").

### 4.2 The current state of third-party AI assessment

Although frontier AI auditing as we define it does not yet exist, a growing field of third-party assessment provides a foundation on which to build \[staufer\_audit\_2025\]. This section summarizes the current state as of December 2025. See for detailed discussion and examples.

Overview. Current third-party assessments of frontier AI vary substantially in scope, access, rigor, and transparency. Most evaluators receive only the same public access as ordinary users, with only a select few receiving early or privileged access. Public reporting is inconsistent: system cards sometimes mention third\-party evaluators only in the abstract; methodological details are often omitted; and evaluators are sometimes not named at all even when they are used \[google\_deepmind\_gemini\_2025\], making it difficult to follow up for more information or for other companies to seek to work with those evaluators. Assessments focus predominantly on capability evaluation and, increasingly, propensity evaluation (e.g., tendencies of AI models to deceive), with comparatively little attention to organizational risk governance, safety culture, or platform-level controls.

Key Dimensions. We assessed current practice across seven dimensions (a more detailed discussion can be found in ):

-   •
    
    Reporting: Public reporting is sparse and inconsistent. System cards vary substantially in how they describe third-party involvement, and methodological details are often absent \[wang\_2025\_foundation\_2025, gallifant\_peer\_2024\].
    
-   •
    
    Access: Most evaluators receive only black-box API access. A small but growing number of collaborations with government institutes have tested deeper access (e.g., chain-of-thought, internal documentation \[aisi\_pre-deployment\_2024\]), but gray-box and white-box access remain highly limited.
    
-   •
    
    Rigor: Methodology and effort vary substantially. Benchmark-based assessments face issues with quality \[reuel\_open\_2025\], contamination \[mcgregor\_risk\_2025\], and construct validity \[bean\_measuring\_2025, wallach\_position\_2025\]. Red-teaming effectiveness is skill-dependent \[mcgregor\_err\_2024\]. Neither companies nor evaluators typically publish substantive threat models.
    
-   •
    
    Standardization: Standards remain nascent, though they are evolving rapidly \[staufer\_audit\_2025, bommasani\_foundationmodel\_2024\]. Evaluations are typically conducted under bespoke, confidential contracts with terms rarely visible to regulators or the public.
    
-   •
    
    Continuous monitoring: Assessments are one-off “snapshots” rather than continuous. Companies frequently update systems without providing third-party access for updated risk assessment.
    
-   •
    
    Scope: Assessments focus heavily on technical systems (often just models) rather than organizational practices. Assessment of mitigations, platform-level controls, and safety culture is comparatively rare.
    
-   •
    
    Scale and independence: Participation is voluntary and concentrated among a few developers. Evaluators depend on companies’ goodwill for access and sometimes funding, creating potential conflicts of interest.
    

Emerging Developments. Recent positive developments include proposed evaluation frameworks (e.g., \[paskov\_toward\_2025, mccaslin\_stream\_2025, reuel\_betterbench\_2024\]); initial best practices from the Frontier Model Forum \[frontier\_model\_forum\_issue\_2024\]; the establishment of the AI Evaluator Forum \[noauthor\_ai\_nodate\]; pilots with government AI safety institutes in the US and UK \[openai\_working\_2025, anthropic\_strengthening\_nodate\]; early examples of third\-party review of company risk assessments (e.g., METR’s review of Anthropic’s sabotage risk report \[samuel\_r\_bowman\_anthropics\_2025\], which we consider to be among the first AAL-1 audits, and third-party review of the safety work conducted for OpenAI’s release of gpt-oss \[openai\_gpt-oss-120b\_2025\]); and OpenAI and Anthropic’s reciprocal safety assessments of each other’s systems \[openai\_findings\_2025, samuel\_r\_bowman\_anthropics\_2025\]. These developments are promising but remain early\-stage compared to established assurance regimes.

### 4.3 The gap between current practice and cross-industry best practices

Current third-party AI assessment efforts provide a valuable starting point — including a nascent ecosystem of organizations, both for-profit and non-profit, that have conducted increasingly rigorous assessments over time. Yet significant gaps remain between these practices and the best practices found in other industries.

How much further improvement is needed depends in part on the risk profile that can be expected from AI at different points in time. Roughly speaking, those who expect faster progress in AI capabilities in the future — and therefore greater safety and security risks, given AI’s general-purpose nature — should desire a faster rate of progress in third-party assessment along various dimensions discussed above, so that we are not caught unprepared. Furthermore, to the extent that one believes that risks are highly correlated with raw capabilities, then one might desire particular scrutiny to be applied to the very most capable AI systems and the companies building them. These insights inform the approach we take in the next section, where we suggest both general principles for how frontier AI auditing should work in general as well as a series of progressively stronger assurance levels that can be adapted to particular contexts.

## 5  A Vision for Frontier AI Auditing

In this section, we set out a long-term vision for what mature third-party auditing could look like --- auditing of both the most capable AI systems and the companies building {--{"author":"Luc's AI","timestamp":1787602131475}@@them.[^7]--}{++{"author":"Luc's AI","timestamp":1787602131475}@@them.[^note-7]++} Some elements of this vision can be pursued now, while others will require years of investment and development before they become practical. We aim significantly beyond the status quo both because not all current assurance needs are being met by the current AI assurance ecosystem, and because we expect future AI systems to be far more capable and risky than those that exist today.

Our vision for frontier AI auditing is organized around eight interlinked design principles, which we discuss in turn:

-   •
    
    Scope of risks: Comprehensive coverage of four key risk categories that can be linked to company actions.
    
-   •
    
    Organizational perspective: Auditing companies’ safety and security practices as a whole, not just individual models and systems.
    
-   •
    
    Levels of assurance: A framework for calibrating and communicating confidence in audit conclusions.
    
-   •
    
    Access: Deep enough to assure auditors and other stakeholders, secure enough to reassure auditees.
    
-   •
    
    Continuous monitoring: Living assessments, not stale PDFs.
    
-   •
    
    Independent experts: Trustworthy results through rigorous independence safeguards and deep expertise.
    
-   •
    
    Rigor: Processes that are methodologically rigorous, traceable, and adaptive.
    
-   •
    
    Clarity: Clear communication of audit results.
    

### 5.1 Risk scope of audits

Frontier AI auditing should focus on risks for which an AI company’s action or inaction can be directly linked to harmful outcomes, including at least the following risk categories (see Figure [5](#S5.F5 "Figure 5 ‣ 5.1 Risk scope of audits ‣ 5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")):

![](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/brundage-frontier-ai-auditing-toward-rigorous-third-party-assessment-of-safety-and-security-practices-at-leading-ai-companies-img2-2a86f7a3.png)

Figure 5: Proposed risk focuses and sources of relevant standards for frontier AI auditing.

-   •
    
    Intentional misuse. The use of frontier AI systems by malicious actors to enable or scale harmful activities. This includes, but is not limited to, cyberattacks; the development and use of chemical, biological, radiological, or nuclear weapons (CBRN); large-scale disinformation; violent and criminal activity; fraud; and the generation of child sexual abuse material (CSAM) or nonconsensual intimate imagery (NCII) \[nist\_managing\_2024\].
    
-   •
    
    Unintended system behavior. AI systems behaving in ways that developers and users did not intend, or being unsafe in ways that could plausibly cause large-scale harm. This includes highly consequential accidents caused by inadequate capabilities, alignment, or safeguards \[tabassi\_artificial\_2023, center\_for\_ai\_safety\_ai\_2023\]. Examples include systems taking harmful, irreversible actions, e.g., permanently deleting critical files \[atherton\_incidentreplit\_2025, {--{"author":"Luc's AI","timestamp":1787602161139}@@atherton\_incidentgoog\_2025\].[^8]--}{++{"author":"Luc's AI","timestamp":1787602161139}@@atherton\_incidentgoog\_2025\].[^note-8]++}
    
-   •
    
    Information security. Failures of confidentiality or integrity affecting critical AI assets. This includes the exfiltration of model weights \[carlini\_stealing\_2024\], exfiltration of sensitive research and customer data via internal or external threats \[nasr\_scalable\_2023, cooper\_extracting\_2025, barbero\_extracting\_2025, ahmed\_extracting\_2026\], risks to user privacy arising from model vulnerabilities or behaviors \[brown\_what\_2022, cooper\_machine\_2025\], as well as sabotage of highly capable AI systems \[nevo\_securing\_2024, anderson\_security\_2020\].
    
-   •
    
    Emergent social phenomena. Risks that arise from interaction between humans and AI systems and do not fit neatly into “misuse” or “unintended behavior,” but can nevertheless cause significant harm if left unaddressed. Examples include addiction to or emotional dependence on AI systems, AI-induced or AI-enabled psychosis, and facilitation of self-harm \[hu\_how\_2023, head\_minds\_2025, noauthor\_emotional\_2025, liu\_chatbot\_2025, saracini\_techno-emotional\_2025, apa\_health\_2025, haskins\_people\_2025, moore\_expressing\_2025, hate\_fake\_2025, choi\_private\_2025\].
    

In reviewing the most recent 300 AI incidents logged by the AI Incident Database \[mcgregor\_preventing\_2021\], we found these risks to cover all incidents cataloged except (1) those that do not involve frontier AI systems under our definition, such as those involving Waymo self-driving {--{"author":"Luc's AI","timestamp":1787602132254}@@cars,[^9]--}{++{"author":"Luc's AI","timestamp":1787602132254}@@cars,[^note-9]++} which are highly capable in their domain but not general-purpose; and (2) those that did not result in very significant harms, such as an instance of confabulation of citations in a machine learning {--{"author":"Luc's AI","timestamp":1787602132727}@@book.[^10]--}{++{"author":"Luc's AI","timestamp":1787602132727}@@book.[^note-10]++}

Structural risks arising from how AI systems reshape systems, incentives, and environments in which they are deployed \[zwetsloot\_thinking\_2023\] are not a design target of our risk list. For example, gradual atrophying of skills at both individual and societal levels as more people rely on AI to perform analytical tasks \[kosmyna\_your\_2025\], economic transformation generally, and greater vulnerability of society to electricity disruptions as a result of heavy AI use throughout the economy are not within our design focus or listed risks for this framework. This does not mean that we are opposed to auditing with respect to such risks, or that there could not be fruitful transparency requirements at a company level that shed light on how best to address structural risks.

For each category of risks, auditors should (1) independently verify company claims and (2) evaluate the company’s systems and practices against its stated safety and security policies, applicable regulations, and industry best practices. Indeed, these risk categories largely map onto company safety and security policies, emerging industry standards (e.g., the Frontier Model Forum \[FrontierModelForum2025\_RiskTaxonomy\]), and regulatory initiatives such as California SB 53, New York’s RAISE Act, the EU AI Act, and the EU General-Purpose AI Code of {--{"author":"Luc's AI","timestamp":1787602133237}@@Practice.[^11]--}{++{"author":"Luc's AI","timestamp":1787602133237}@@Practice.[^note-11]++}

Table 2: Risk categories in company policies (e.g., from OpenAI, Google DeepMind, Anthropic, xAI, Meta, Microsoft, and Amazon) and regulatory texts \[metr\_common\_2025\].

| AI risk category | Company policies | CA SB 53 / NY RAISE | EU AI Act Code of Practice |
| --- | --- | --- | --- |
| Intentional misuse | Partially included | Partially included | Fully included |
| Unintended system behavior | Partially included | Partially included | Fully included |
| Information security | Fully included | Fully included | Fully included |
| Emergent social phenomena | Partially included | Not included | Partially included |

### 5.2 Comprehensive, organizational-level perspective

To examine the risks we outline above, an audit could cover different parts of a company, or the company as a whole. In this subsection, we argue that frontier AI auditors should emphasize the company as a whole as the most important level of analysis. Individual AI systems may be partially illustrative of or a big component of a company’s risk management, but they are never the full story of the company’s impact. Specific components of and artifacts produced by a company are important to audit and may even be the focus of specific audits, but should always be explicitly considered in — and audit conclusions should be framed in relation to — this larger context.

Avoiding abstraction errors. A central danger in auditing frontier AI developers is that an audit can be right about the specific artifact or process it examined while still being wrong in the way that matters about the company’s overall risk posture. This reflects an abstraction error: forming the wrong conclusion by treating a partial or simplified unit of analysis (e.g., evaluating a specific component in isolation) as if it were sufficient to assess overall system and organizational risk. Such abstraction errors are especially likely in frontier AI because (1) risks such as those listed in [section 5.1](#S5.SS1 "5.1 Risk scope of audits ‣ 5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") are shaped by interactions across internal processes, AI systems, and other parts of the internal technology stack, (2) many relevant systems and decisions are non-public and fast-changing, and (3) it is easy to (often unintentionally) audit what is most legible rather than what is most risk-relevant. Put differently: auditing can miss the forest for the trees not because the trees are unimportant, but because the forest is not simply the sum of individually “healthy-looking” trees.

There are at least four ways abstraction errors can arise in practice:

-   •
    
    Portfolio blindness: auditing the most visible or best-behaved system. Frontier AI developers rarely operate a single model or a single system. They maintain portfolios: multiple checkpoints; post-training variants; internal research models; preview builds for partners; fine-tunes for specific customers; custom model weights transferred to a datacenter controlled by a customer; and internal tools with broader permissions than the public product. It is therefore possible for an audit to establish that a flagship deployment is well-controlled, while missing a materially riskier surface elsewhere. In these cases, a favorable finding about one audited surface is not false per se, but may become misleading if it is treated as representative of the organization’s overall risk posture.
    
-   •
    
    Configuration drift: outdated or incomplete audit results due to system-level changes. Even when the same exact model checkpoint is being used in different cases, real-world behavior and risk depend on system-level configurations: system prompts, input and output filters, routing across multiple models, retrieval sources (e.g., search engine APIs or periodically updated databases from which knowledge is retrieved during operation), tool access, memory, rate limits, monitoring thresholds, user-specific personalization, UI features, public-facing API implementations, and downstream post-processing. Seemingly modest changes such as enabling a new tool, relaxing a filter threshold, swapping in a different safety classifier, or changing routing rules for a subset of users or at different times of day can materially alter misuse potential or the likelihood of harmful failures. An abstraction error occurs here when an audit treats a specific evaluation (or a staging configuration) as a proxy for the actual deployed system, without establishing that the audited configuration matches production deployments and will remain stable enough for conclusions to hold. The need to hedge against configuration drift is one reason why we emphasize continuous monitoring for changes in .
    
-   •
    
    Non-compositional safety and security: safe components, unsafe assembly. Many safety and security properties do not necessarily compose together neatly. A model that refuses harmful requests in an isolated user chat setting may still enable harmful outcomes in another isolated user chat, or when embedded in an agentic scaffold that chains together multiple tool calls and operates over long horizons. A model with concerning raw capabilities and propensities (e.g., to deceive users) may be kept low-risk through strong system-level controls. For frontier AI, the risk-relevant question is often less “what can the model do in isolation?” and more “what can the organization’s integrated systems do, under realistic conditions, given the actual controls?” Abstraction errors arise here when auditors over-weight component-level findings while under-weighting system-level or organization-level interactions that dominate the actual risk.
    
-   •
    
    Boundary mismatch in security: strong product security, weak security of trade secrets. A company may deploy a well-engineered public API (authentication, rate limits, abuse monitoring) while leaving training infrastructure, model weight storage, experiment tracking, or internal repositories comparatively exposed. Indeed, at least two frontier AI companies have had AI research-related intellectual property stolen from them \[metz\_hacker\_2024, us\_doj\_chinese\_2024\], and likely there are many similar cases that are not publicly known given what is known about these companies’ security practices and the difficulty of defending against sophisticated attacks \[nevo\_securing\_2024, mitch\_governance\_2025\]. The resulting organizational risk can be dominated by the weaker boundary: if an adversary can exfiltrate model weights or tamper with training and deployment artifacts, the company’s public-facing mitigations may become irrelevant (e.g., stolen weights can be used without those mitigations). Here, a “system-level” audit focused on the externally visible interface can substantially underestimate information security risks that sit behind the interface but govern the most consequential assets.
    

Abstraction errors are not rare edge cases to be aware of and carefully avoided. Rather, they demonstrate that the company level of analysis is best for forming confident conclusions, even if it is hard to achieve in practice \[ball\_entity-based\_2025\]. There are predictable ways audits focused on only a single component of a frontier AI company can mislead all stakeholders regarding that company’s risk posture.

Three lenses. In our vision for frontier AI auditing, lead auditors need to integrate three lenses: models and systems, which includes AI models, system features connected to those models (e.g., input and output classifiers, system prompts), and information security safeguards (e.g., user authentication); computing hardware, including its quantity and security, and how it is allocated across development and deployment efforts; and governance, including development and deployment decision-making processes, information security systems and protocols, incident response protocols, the safety and security culture of the organization, and the clarity with which responsibility is allocated within the company. Neglecting one of these lenses risks an incomplete picture of a company’s risk profile (see Figure [6](#S5.F6 "Figure 6 ‣ 5.2 Comprehensive, organizational-level perspective ‣ 5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")).

Figure 6: What should be audited?

AI models and systems are the primary focal point of a frontier AI company’s work. But critically, from an auditing perspective, it’s important not to focus on a single model or system to the exclusion of others. All but the very most nascent companies have many different models and systems at a given time. This includes models and systems that are in development in addition to those that are deployed; models that are smaller, cheaper, and faster but less capable as well as those that are larger, more expensive, and slower but more capable; versions of systems that use more or less computing power while in use (”test-time compute”); versions that are produced and provided specifically for a given customer, such as a company or government agency, and may have different guardrails; information security systems, which are critical to ensuring that the other systems are not stolen or tampered with; and much more. At higher assurance levels, more of these systems are critically examined, and in more detail.

Auditors also need to understand the computing hardware that a company has access to and how it is using it. Physical or digital access to that computing hardware could be a weak link for the security of training infrastructure, weight storage, and internal repositories, as discussed above; major training runs or deployments that are not publicly announced could contribute disproportionately to a company’s risk profile — such internal deployment \[stix\_ai\_2025\] might be unknown to auditors by default, but shouldn’t be if auditors are to be effective in characterizing risks. Gaps in a company’s ability to comprehensively account for its own compute use could point to gaps in the company’s understanding of its own activities, or could indicate efforts to mislead auditors (note that this is particularly important at higher assurance levels, where significant effort is made to rule out the possibility of deception).

Lastly, understanding the safety and security governance of all of these digital and physical systems is critical in order to put those systems in context. An auditor needs to know who is responsible for what, how documents are produced, what the incentives facing the document-writers were, etc. in order to meaningfully interact with non-public information and spot subtle errors and — at the highest levels of assurance — intentional deception. In short, information about governance helps indicate how much to trust other kinds of information. Furthermore, significant gaps in governance — both formal (e.g., limited or non-existent policies governing internal AI deployments) and informal (e.g., a culture of corner-cutting in specific areas that comes up in staff interviews) — may provide vital clues to gaps in risk mitigation at a system level.

Practical implications of the organization-level perspective. To achieve higher levels of assurance about a company’s risk profile ([section 5.3](#S5.SS3 "5.3 Levels of assurance ‣ 5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")), deeper access to information () will tend to be required about each of these lenses in order to enable drawing confident conclusions about a company’s risk profile in each of the four risk categories. This in turn will require standardized processes for “mixing and matching” subcontractors with different skill sets (). In order to avoid committing abstraction errors due to configuration drift, continuous monitoring will be needed, and a range of different audit cadences will need to be conducted, corresponding to the different paces of change of different organizational components (). Rigorous, traceable processes are needed in order to allow those interpreting or replicating an audit to infer whether abstraction errors are likely (). Privately and publicly shared audit findings (see ) need to enumerate the assumptions being made in order for analyses of artifacts to be representative of the company as a whole.

Over time, there needs to be research toward a standardized analytical framework (e.g., an “organizational safety and security case”) that combines different inputs into a composite picture of a company’s risk profile. Such research should draw on best practices from safety-critical systems engineering, such as safety cases, which are structured arguments supported by evidence that justify the safety of a system \[{--{"author":"Luc's AI","timestamp":1787602161662}@@uk\_ministry\_of\_defence\_defence\_2007\].[^12]--}{++{"author":"Luc's AI","timestamp":1787602161662}@@uk\_ministry\_of\_defence\_defence\_2007\].[^note-12]++} We think our AI Assurance Level (AAL) framework, discussed next, is an early step.

### 5.3 Levels of assurance

To address the different risk scopes for different depths of organization-level audits, we propose a framework for calibrating and communicating confidence in audit conclusions that we call AI Assurance Levels (AALs). This framework is intended to help those conducting and relying on audits to understand what conclusions they can reasonably draw, and what kinds of abstraction errors ([section 5.2](#S5.SS2 "5.2 Comprehensive, organizational-level perspective ‣ 5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")) — among other types of errors — still cannot be ruled out.

#### 5.3.1 The meaning of levels of assurance in general

Frontier AI audits should each be conducted at a specific “level of assurance.” A given level describes how confident the auditor is in their conclusions about a given company’s safety and security practices \[jelen\_practical\_1998, icaew\_limited\_nodate\]. In principle, an auditor could reach a high assurance conclusion that safety and security safeguards are very poor; however, we will often use examples of audit findings that are positive with respect to safety and security risk management. We do so because, in practice, frontier AI audits involve active collaboration between the auditor and auditee and allow the possibility of remediation prior to publication of results.

Explicit assurance levels help stakeholders understand how much they can rely on audit results and what assumptions remain untested. In other industries, reviewers and auditors provide either “limited” or “reasonable” assurance \[iaasb\_international\_2013, noauthor\_isoiec\_2019, public\_company\_accounting\_oversight\_board\_at\_nodate\]. Safety-critical industries (e.g., aviation, nuclear power) also use the concept of reasonable assurance \[bsee\_oil\_2015, dapas\_key\_nodate, jackson\_internal\_2021\], which implies a higher degree of confidence. The level of assurance required for different contexts may differ, depending in part on the costs of the audit and the costs of errors \[harris\_which\_2023\].

#### 5.3.2 Overview of AI Assurance Levels

We use the term AI Assurance Levels (AALs) to refer to assurance levels in the sense above, as applied to the specific context of a frontier AI {--{"author":"Luc's AI","timestamp":1787602134021}@@audit.[^13]--}{++{"author":"Luc's AI","timestamp":1787602134021}@@audit.[^note-13]++} Higher levels more and more confidently assess the risk level associated with the frontier AI company as a whole, and progressively rule out abstraction errors such as those discussed in [section 5.2](#S5.SS2 "5.2 Comprehensive, organizational-level perspective ‣ 5  A Vision for Frontier AI Auditing ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies") as well as other possible sources of error in the audit’s findings. To achieve this, audits at higher levels will tend to require greater access to non-public information relative to lower levels, larger allocations of time and talent, and more sophisticated infrastructure and analysis.

Lower AI Assurance Levels (AAL-1 and 2) can detect some errors on the part of companies and verify the existence of significant compliance efforts, and they can achieve this using smaller expenditures of time and talent. While audits at these levels may be able to detect errors (i.e., unintentional misstatements or mistakes), they are less likely to be able to detect fraud (i.e., intentional deception) (see \[hamilton\_evaluating\_2016\]).

Higher AI Assurance Levels (AAL-3 and 4) can provide stakeholders significantly more confidence that the conclusion of the audit is correct and that more subtle errors will be detected, and they aim to address the possibility of deliberate deception on the part of the company. Since we envision audits of companies rather than just systems, audits at higher AALs serve as better and better estimates of company-level risks (versus just system-level risks). At the same time, these audits are more costly because they will require more allocation of both company capacity and auditor capacity, and will involve greater access to (often sensitive) non-public information (see \[harack\_verification\_2025\]).

Using lower AI Assurance Levels may be appropriate when risks of audit errors are less severe, making the cost of achieving higher AI Assurance Levels greater than the assurance that is obtained \[uk\_psctg\_gross\_2006\]. In contrast, using higher assurance levels may be appropriate for auditing risks that stakeholders are more concerned about, or auditing in situations where there are strong incentives for the companies to cut corners \[askell\_role\_2019\].

#### 5.3.3 AI Assurance Level details

Drawing inspiration from the precedents above, as well as the specific context of frontier AI, we describe each of our proposed four AI Assurance Levels (AALs) below. We begin with an overarching summary, then provide more details on each.

-   •
    
    Limited assurance (AAL-1). A time-bounded audit of a particular frontier AI system (typically a few weeks), which makes use of API access to multiple model versions and system settings, as well as a limited amount of additional, non-public information focused on the audited system and related internal decisions.
    
-   •
    
    Moderate assurance (AAL-2). A more extensive assessment of one or more frontier AI systems, as well as company practices more broadly, which, at a minimum, spans months and makes use of gray-box system access, extensive internal documentation (e.g., unredacted safety cases), some continuous monitoring, and staff interviews across several functions.
    
-   •
    
    High assurance (AAL-3). Ongoing oversight (multiyear engagement for the lead auditor, with many subcontractors contributing throughout) with white-box access, more extensive continuous monitoring, and the authority to examine any area of concern.
    
-   •
    
    Very high assurance (AAL-4). Continuous verification designed to detect active deception attempts, operating with a full understanding of the company’s systems, computing hardware, and governance, and providing “treaty-grade” confirmation of the company’s risk profile.
    

The table and paragraphs below summarize the level progression.

| Summary of AI Assurance Levels. At higher levels, auditors are more confident in their conclusion. |  |  |  |  |
| --- | --- | --- | --- | --- |
| Level | Duration | Typical access to information (cumulative) | Methods | Readiness |

{--{"author":"Luc's AI","timestamp":1787602134540}@@[^1]:--}{++{"author":"Luc's AI","timestamp":1787602134540}@@[^note-1]:++} In short, our auditing framework is intended to work around access challenges that are not always in the open-weight context, and to assess mitigations and governance processes that are also quite different in an open-weight context. Related questions about open-weight model safety and evaluation are discussed in more detail in \[bommasani\_considerations\_2024, seger\_open\_2024, francois\_different\_2025, srikumar\_risk\_2024, casper\_open\_2025, kapoor2024societal\].
{--{"author":"Luc's AI","timestamp":1787602134998}@@[^2]:--}{++{"author":"Luc's AI","timestamp":1787602134998}@@[^note-2]:++} A company “deploys” AI systems if they make these systems available for direct, economically relevant use by internal or external parties, even if the company does not train their own models. Companies may develop frontier AI models for internal research, only deploying them internally (see \[openai\_better\_2019\]). A developer could also make AI systems available for deployment exclusively by others without deploying these models themselves. If customers conduct fine-tuning themselves on pre-trained models, the company hosting the training service wouldn’t be considered a developer under our use of the term.
{--{"author":"Luc's AI","timestamp":1787602135481}@@[^3]:--}{++{"author":"Luc's AI","timestamp":1787602135481}@@[^note-3]:++} This is admittedly imprecise, since a developer could be a non-profit organization or a government, though for-profit companies are the most frequent type of frontier AI developer as well as the most frequent type of frontier AI deployer.
{--{"author":"Luc's AI","timestamp":1787602135959}@@[^4]:--}{++{"author":"Luc's AI","timestamp":1787602135959}@@[^note-4]:++} There are at least four reasons for this: (1) Developers might only deploy certain dangerous systems internally \[stix\_ai\_2025\], or only give access to them to certain customers, as in the case of systems that have fewer guardrails \[anthropic\_claude\_2025, openai\_strengthening\_2025-1\], limiting what can be learned from testing public products. (2) Since AI systems are already being misused by criminals and state actors \[anthropic\_disrupting\_2025, openai\_disrupting\_2025, google\_threat\_intelligence\_group\_gtig\_2025\], developers may respond by publishing more limited information about some aspects of these systems and their risks in order to prevent this information from itself being misused, e.g., to more easily “break” system safeguards. Indeed, some details are already explicitly withheld on that basis, such as the details of chemical, biological, radiological, and nuclear (CBRN) threat models \[noauthor\_ai\_2025, gemini\_gemini\_2025, google\_threat\_intelligence\_group\_gtig\_2025\]. (3) AI systems will likely become more complex (e.g., with multiple interacting models solving complex problems whose solutions are difficult to understand even with the benefit of access to the models’ chains-of-thought, let alone without it), thus reducing the information value of the final output as a means of understanding how it was produced and what potential failure modes might exist in that system. (4) AI systems will become more capable, likely increasing the worst-case risks associated with outputs that may be intentionally deceptive, as well as increasing the likelihood of strategically low-performing behavior by systems \[noauthor\_more\_2025\].
{--{"author":"Luc's AI","timestamp":1787602136451}@@[^5]:--}{++{"author":"Luc's AI","timestamp":1787602136451}@@[^note-5]:++} Organizational psychology research documents “groupthink” as a pervasive risk in cohesive teams — e.g., self-censorship of doubts and collective rationalization of warnings. These dynamics can render the possibility of failure unthinkable or at least unspeakable \[reason\_life\_2013\]. Independent third-party auditors provide a structural countervailing force against these tendencies.
{--{"author":"Luc's AI","timestamp":1787602136938}@@[^6]:--}{++{"author":"Luc's AI","timestamp":1787602136938}@@[^note-6]:++} This is one of several reasons to focus particular governance attention on frontier AI, as discussed further in \[anderljung\_frontier\_2023\].
{--{"author":"Luc's AI","timestamp":1787602137427}@@[^7]:--}{++{"author":"Luc's AI","timestamp":1787602137427}@@[^note-7]:++} In addition to insights from other industries ([section 4.1](#S4.SS1 "4.1 Key lessons from more established assessment domains ‣ 4  Lessons from Related Domains and Current AI Assessment ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")) and gaps in current AI assessment practices ([section 4.3](#S4.SS3 "4.3 The gap between current practice and cross-industry best practices ‣ 4  Lessons from Related Domains and Current AI Assessment ‣ Frontier AI Auditing:Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies")) (on which further details can be found in and ), our vision builds on prior work outlining frameworks for AI auditing, including field scans of the algorithmic auditing ecosystem \[costanza-chock\_who\_2022\], proposals for third-party audit ecosystem design based on a survey of the challenges and existing practices in other industries \[raji\_outsider\_2022, rismani\_plane\_2023\], internal algorithmic auditing frameworks \[raji\_closing\_2020\], external scrutiny requirements for frontier LLMs \[anderljung\_towards\_2023\], assurance audit frameworks modeled on financial auditing \[lam\_framework\_2024\], and layered approaches combining governance, model, and application audits \[mokander\_auditing\_2023, mokander\_auditing\_2023-1\].
{--{"author":"Luc's AI","timestamp":1787602137881}@@[^8]:--}{++{"author":"Luc's AI","timestamp":1787602137881}@@[^note-8]:++} We categorize misalignment and loss of control as “unintended” in the sense that humans did not intend for the system to behave in these ways, even where the system itself may be acting coherently in pursuit of goals that diverge from those intended. Loss of control can be passive (inability to monitor or correct system behavior) or active (systems resisting human oversight) \[bengio\_international\_2025\]. Some taxonomies treat misalignment and loss of control as a distinct risk category rather than a subset of accidents \[shah\_approach\_2025, hendrycks\_overview\_2023\], and others consider misalignment a catalyst for loss of control \[stix\_loss\_2025\].
{--{"author":"Luc's AI","timestamp":1787602138340}@@[^9]:--}{++{"author":"Luc's AI","timestamp":1787602138340}@@[^note-9]:++} See \[aaid\_waymo\_2026\].
{--{"author":"Luc's AI","timestamp":1787602138765}@@[^10]:--}{++{"author":"Luc's AI","timestamp":1787602138765}@@[^note-10]:++} See \[atherton\_incidentuber\_2026\].
{--{"author":"Luc's AI","timestamp":1787602139278}@@[^11]:--}{++{"author":"Luc's AI","timestamp":1787602139278}@@[^note-11]:++} We expect the appropriate scope and emphasis of audits to evolve over time as threats, norms, and regulations change, but that there are common threads in how frontier AI auditing should work (e.g., careful management of sensitive information, ensuring auditor independence) that will not change significantly over time. We therefore think that one could endorse the vision discussed in this section, even if one would prefer a different scope.
{--{"author":"Luc's AI","timestamp":1787602139750}@@[^12]:--}{++{"author":"Luc's AI","timestamp":1787602139750}@@[^note-12]:++} Existing work has proposed safety cases to verify that AI systems are safe enough to develop or deploy (see \[buhl\_safety\_2024, clymer\_safety\_2024\]).
{--{"author":"Luc's AI","timestamp":1787602140247}@@[^13]:--}{++{"author":"Luc's AI","timestamp":1787602140247}@@[^note-13]:++} After completing most of this paper, the authors learned of a prior use of the term “AI Assurance Level” with a very different meaning \[jain\_ai-driven\_2025\], as well as another use of the acronym AAL in a related context (Authenticator Assurance Levels \[nist\_authenticator\_2026\]). These collisions are unintentional.

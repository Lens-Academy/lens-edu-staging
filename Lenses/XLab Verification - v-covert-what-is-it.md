---
id: '21d6389a-c210-41c9-be29-4488940d1050'
title: "What is covert development?"
tldr: "Nothing in the scenario proves anything. An engineer had a side arrangement, some accounts rented a lot of compute, a rival suddenly has a better model. Watch a red team build the evasion and a blue team take it apart, and learn the standard: not perfect evasion or perfect verification, but a case specific enough to test and a response honest enough to tell suspicion from proof."
summary_for_tutor: "XLab's module 3 opener, restored from git history. Frames the module: every mechanism from Module 2 fails somewhere, and this module is about how a determined actor gets around them. Carries XLab's module objectives, two optional real-world anchors (the Linwei Ding insider case and the cloud-access route around chip export controls), and the fictional Training Through the Pause worked example, in which Sable Systems continues a paused frontier run using a Northstar insider and split cloud accounts. Six prompts, three red-team and three blue-team, each with XLab's model answer, its strengths and the common weaknesses. Two of the six are asked as real questions before the model answer is revealed; the answer keys sit in closed callouts, so do not reveal them before the learner commits. The point the lesson builds to: the operation is not made invisible, it is made inconclusive, and the blue team wins by correlating across layers rather than by owning a perfect detector."
tags: [wip]
duration_minutes: 35
authors:
  - Elias+Claude
---
#### Text
content::
{>>{"author":"Elias's AI","timestamp":1788520541116}@@Restored from XLab commit a10955c^, src/content/lessons/verification/covert-what-is-it.mdx (XLab's unit 3.0, "What is Covert Development?"). Upstream deleted it in a10955c, when the course owner replaced the whole of module 3 with the Cankaya paper; docs/verification/module-3-log.md on main records what went and why. Body text is XLab's. Three deviations, all mine: em dashes are removed under the Lens house rule (XLab's owner ruled the other way for their repo, see their commit #56); XLab's unit number is dropped from the title, because v-covert-system-overview now occupies slot 3.0 and renumbering the module is Elias's decision, not mine; and two of the six worked-example prompts are asked as real questions before their model answers are revealed, which is Lens instructional design and not XLab's.<<}
Every mechanism you learned about in Module 2 is prone to failure. Illicit training runs can be disguised as inference. Employee defectors can leak frontier secrets. The reason why the field of verification is so important is the same reason why its design is so difficult: there will constantly be adversaries trying to break a regime, no matter how robust. From nation-states to corporate employees, motivated by everything from national security to personal profit, countless actors will continuously attempt to secretly develop superintelligence or steal frontier weights.

:::callout {title="In this module, you will learn how to:" tone="blue"}
1. Identify weaknesses in the verification mechanisms you learned about in Module 2
2. Trace what evidence the evasion would leave across different verification layers
3. Analyze how actors you learned about in Module 1 might evade an AI agreement
4. Design controls that could prevent, detect, investigate, or confirm violations
5. Scaffold a robust, layered regime that minimizes vulnerabilities across all layers
:::
{>>{"author":"Elias's AI","timestamp":1788520541116}@@Note for Elias: this module now carries two objective lists. This one is XLab's, written for the four evasion lessons. The other is the course owner's three-bullet "By the end of this module, you will be able to" block inside v-covert-system-overview, written for the Cankaya close reading. I have kept both verbatim rather than merging them, because choosing which one governs the module is the same decision as the module's contested title, and that is yours.<<}

You will develop these skills through working through a red-team/blue-team scenario yourself later in this module. The red team designs an evasion strategy against the proposed verification regime; the blue team identifies detection opportunities, corroboration needs, and response options. This task can feel daunting and abstract without seeing the full process first, which is what the worked example below is for. The scenario itself is fictional, but its main tactics are based on documented cases and published security research.

#### Text
optional:: true
content::
\## Optional: two real-world anchors

\### Anchor 1: an insider changes the format, not the information

In 2024, the United States [charged Google engineer Linwei Ding](https://www.justice.gov/archives/opa/pr/chinese-national-residing-california-arrested-theft-artificial-intelligence-related-trade) with stealing confidential information about Google's AI computing infrastructure. Prosecutors alleged that Ding copied information from Google source files into Apple Notes on a company laptop, converted the notes into PDFs, and uploaded them to a personal cloud account. This allegedly allowed the material to pass through a channel that Google's data-loss-prevention system did not block.

The stolen material concerned systems such as tensor processing units, graphics processing units, networking, and cluster-management software. It was not a set of model weights. Ding was [convicted on all fourteen charged counts](https://www.justice.gov/opa/pr/former-google-engineer-found-guilty-economic-espionage-and-theft-confidential-ai-technology) in January 2026.

The transferable lesson is simple:

> A sophisticated verification regime may still fail when an authorized person moves protected information through an unexpected format or channel.

Legitimate access and a simple transformation were enough to bypass an automated control.

\### Anchor 2: move the workload instead of the hardware

Export controls traditionally focus on the transfer of physical chips and related technology. But an actor may be able to access advanced chips remotely through a cloud provider, reseller, or intermediary.

In 2024, [Reuters reported](https://www.reuters.com/technology/chinese-entities-turn-amazon-cloud-its-rivals-access-high-end-us-chips-ai-2024-08-23/) that Chinese organizations had used procurement processes to seek access to restricted U.S. computing resources through cloud services and intermediaries. At that time, remotely accessing chips through the cloud was not treated in the same way as physically importing the chips.

U.S. policymakers considered broader customer-identification and reporting requirements for infrastructure-as-a-service providers. However, the Commerce Department [withdrew](https://www.reginfo.gov/public/do/eAgendaViewRule?pubId=202510&RIN=0694-AJ35) its proposed ["Preventing Access to U.S. IaaS Products by Malicious Cyber Actors"](https://www.federalregister.gov/documents/2024/01/29/2024-01580/taking-additional-steps-to-address-the-national-emergency-with-respect-to-significant-malicious) rule in December 2025. A separate [2025 policy framework](https://www.federalregister.gov/documents/2025/01/15/2025-00636/framework-for-artificial-intelligence-diffusion) that would have imposed broader controls on third-country compute and model-weight transfers was also [rescinded](https://www.bis.gov/press-release/department-commerce-announces-rescission-biden-era-artificial-intelligence-diffusion-rule-strengthens).

The transferable lesson is:

> When moving a regulated object is difficult, the actor may leave the object where it is and move the activity to it.

#### Text
content::
\## Worked example: training through the pause

This is a fictional composite. The organizations and agreement are invented, but the tactics draw on documented cases involving insider exfiltration, format-shifting, cloud intermediaries, dual-use infrastructure, and incomplete declarations.

\### The scenario

In 2029, several governments and frontier AI companies agree to a twelve-month Frontier Training Pause after evaluations suggest that the next generation of models could create severe national-security risks.

During the pause:

- No actor may begin or continue a covered frontier training run.
- The prohibition includes pretraining, major capability-enhancing post-training, and attempts to produce a successor to an existing frontier model.
- Existing models may still be used for approved inference, safety evaluation, and limited research below defined compute and capability thresholds.
- Covered model weights must remain in declared, access-controlled environments.
- Cloud providers must retain records sufficient to identify customers, beneficial owners, hardware use, and declared workload purpose.

Northstar AI has already trained a covered model called Orion-4. Its weights are stored in a secure environment and may be accessed only for approved maintenance, evaluation, and incident response.

Before the pause, Northstar had been developing an Orion-5 successor. The pause freezes that work.

A foreign technology conglomerate, Sable Systems, believes that continuing development during the twelve-month pause could give it a decisive lead. Sable cannot legally obtain Orion-4's weights or openly rent enough compute to continue training them.

Northstar rejects Sable's request for access.

Months later, an intelligence service receives a fragmentary report that a senior Northstar engineer has been advising Lattice Research, a small scientific-computing company with no obvious public connection to Sable.

Around the same time, Lattice and several subcontractors rent advanced accelerators through a cloud reseller. Each account remains below the pause agreement's review threshold. The customers describe their work as protein-model inference, benchmark evaluation, and safety research.

The accounts nevertheless run synchronized, compute-intensive workloads for six weeks.

Shortly afterward, Sable privately demonstrates a model that resembles Orion-4 but performs substantially better on several strategically important tasks.

Nothing yet proves that Orion-4's weights were stolen or that prohibited training occurred.

\### The task

As the red team, explain the most plausible evasion strategy, its assumptions, and its weakest point.

As the blue team, explain how evidence from the hardware, cloud, intelligence, and human layers could be combined, and recommend a proportionate response.

The answers below show what excellent student work might look like. Write your own answer to a prompt before you open its model answer, or open the model answer straight away, so that you see the whole shape of the exercise before you meet the real one in the last lesson of this module.

#### Widget
source:: [[../widgets/covert-worked-example]]

#### Text
content::
\### Brief debrief

The red team did not try to hide a new data center. It tried to continue frontier training on legitimate infrastructure while distributing the evidence across an AI company, cloud reseller, data center, shell companies, and human participants.

The blue team did not rely on one perfect detector. It preserved records, reconstructed the cross-layer timeline, tested alternatives, and recommended action proportionate to the evidence.

A strong red-team answer explains:

- How the operation works;
- Why the actor would choose it;
- What assumptions it requires;
- Where it is most likely to fail.

A strong blue-team answer explains:

- What each layer can observe;
- What those observations do and do not prove;
- How the evidence can be combined;
- What action is justified before certainty is available.

The standard is not perfect evasion or perfect verification. It is a scenario specific enough to test, and a response honest enough to distinguish suspicion from proof.

The next lesson asks what a determined actor would actually try, and the lesson after that lays out the ten routes it could take.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
United States, Department of Justice. "Chinese National Residing in California Arrested for Theft of Artificial Intelligence-Related Trade Secrets from Google." 6 Mar. 2024. [justice.gov](https://www.justice.gov/archives/opa/pr/chinese-national-residing-california-arrested-theft-artificial-intelligence-related-trade)
*The press release announcing the charges in the Linwei Ding case that anchors this lesson.*

United States, Department of Justice. "Former Google Engineer Found Guilty of Economic Espionage and Theft of Confidential AI Technology." 30 Jan. 2026. [justice.gov](https://www.justice.gov/opa/pr/former-google-engineer-found-guilty-economic-espionage-and-theft-confidential-ai-technology)
*The conviction on all fourteen counts.*

"Exclusive: Chinese Entities Turn to Amazon Cloud and Its Rivals to Access High-End US Chips, AI." *Reuters*, 23 Aug. 2024. [reuters.com](https://www.reuters.com/technology/chinese-entities-turn-amazon-cloud-its-rivals-access-high-end-us-chips-ai-2024-08-23/)
*The investigation into Chinese organizations reaching restricted US chips through cloud services and intermediaries.*

United States, Department of Commerce. "Taking Additional Steps to Address the National Emergency with Respect to Significant Malicious Cyber-Enabled Activities." *Federal Register*, 29 Jan. 2024. [federalregister.gov](https://www.federalregister.gov/documents/2024/01/29/2024-01580/taking-additional-steps-to-address-the-national-emergency-with-respect-to-significant-malicious)
*The proposed IaaS know-your-customer rule.*

Office of Information and Regulatory Affairs. "Unified Agenda of Regulatory and Deregulatory Actions, RIN 0694-AJ35." *Reginfo.gov*, Dec. 2025. [reginfo.gov](https://www.reginfo.gov/public/do/eAgendaViewRule?pubId=202510&RIN=0694-AJ35)
*The entry recording that the proposed IaaS rule was withdrawn.*

United States, Bureau of Industry and Security. "Framework for Artificial Intelligence Diffusion." *Federal Register*, 15 Jan. 2025. [federalregister.gov](https://www.federalregister.gov/documents/2025/01/15/2025-00636/framework-for-artificial-intelligence-diffusion)
*The interim final rule that would have controlled third-country compute and model-weight transfers.*

United States, Department of Commerce. "Department of Commerce Announces Rescission of Biden-Era Artificial Intelligence Diffusion Rule." 13 May 2025. [bis.gov](https://www.bis.gov/press-release/department-commerce-announces-rescission-biden-era-artificial-intelligence-diffusion-rule-strengthens)
*The rescission of that rule.*

XLab. "3.0 What is covert development?" *Verification*, XLab, University of Chicago, 2026.
*The source lesson this page restores. It was deleted upstream in commit a10955c and is not currently live on aisafetytracks.com.*
:::{>>{"author":"Elias's AI","timestamp":1788520541116}@@These seven entries are XLab's own citation-registry records for this lesson, recovered from src/content/citations.json at a10955c^ (commit a10955c removed them as orphans once the lesson went). Titles, publishers and dates are theirs, not mine. Link liveness is untested: XLab's module-3 log records that their own link audit could not complete, and I have not retested these URLs.<<}

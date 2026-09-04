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

The first red-team prompt and the first blue-team prompt are yours to answer. The other four are worked through for you, so that you can see the whole shape of the exercise before you meet the real one in the last lesson of this module.

#### Question: Open
id:: f5513eaf-2e53-4c17-ba06-71bf747de0df
content:: **Red team, prompt 1.** Describe the most plausible evasion strategy Sable could use.

Write one coherent pathway, not a list of possibilities. Say who does what, in what order, and what makes each step look ordinary from the inside of the organization that sees it.
placeholder:: One pathway, start to finish. Who acts, in what order, and what each observer sees.
assessment-instructions:: This is XLab's first red-team prompt in the Training Through the Pause worked example, asked before the model answer is shown. Score against XLab's five "why this is strong" criteria, about 20 points each. (1) Chooses one coherent pathway rather than listing possibilities. (2) Begins with the lowest-cost route, which is trusted insider access plus existing rented infrastructure, rather than a new covert data centre. (3) Shows how the human, cloud and hardware layers interact, so the answer is an operation and not a trick. (4) Identifies institutional fragmentation as the concealment strategy: Northstar sees an engineer doing apparently legitimate work, the reseller sees several medium-sized customers, the data centre sees intensive compute but not the model or purpose, and registries show Lattice rather than Sable. (5) Avoids claiming that one technical trick makes the operation invisible; the operation makes each piece look inconclusive. Deduct for XLab's four named weaknesses: a clever exfiltration technique with no account of the full operation; assuming the insider can freely export usable weights; giving the attacker unlimited nation-state capabilities; treating separate cloud accounts as automatically separate workloads. Do not require the learner to have guessed XLab's specific tricks, such as fragmenting files or repackaging through an approved workflow. Credit any transformation that preserves the information while changing the indicators the detector recognises. No generic praise.
feedback-instructions:: One turn. Name which of the five criteria the answer met, name the ones it missed in one line each, and if the answer shows one of the four common weaknesses, say which and why it matters. Then send the learner to open the model answer below and read on. Do not re-teach the scenario and do not ask a follow-up question.

#### Text
content::
:::callout {title="Red team, prompt 1: the model answer (open after you have answered)" tone="neutral" collapse="closed"}
Sable's cheapest credible strategy is to combine insider access with rented infrastructure.

A Northstar engineer already has a legitimate reason to interact with Orion-4. During an approved maintenance or evaluation window, the engineer could copy or transform enough of the weights to make them reconstructable outside Northstar.

The transfer should not resemble the event Northstar's monitoring system expects. The engineer might fragment the files, repackage them through an approved workflow, or move them through an intermediate format or storage system. The precise trick matters less than the principle: preserve the information while changing the indicators the detector recognizes.

Lattice would receive or reconstruct the weights. It would then continue the paused Orion-5 development effort on rented cloud infrastructure.

To reduce scrutiny, Lattice could:

- Divide the workload among related accounts;
- Use resellers and subcontractors;
- Describe the activity as inference, evaluation, or safety research;
- Keep each account below a simple reporting threshold.

The operation does not make the training invisible. It makes each piece look inconclusive.

Northstar sees an engineer performing apparently legitimate work. The reseller sees several medium-sized customers. The data center sees intensive compute but not necessarily the model or legal purpose. Corporate registries show Lattice, not Sable.

The strategy succeeds if these organizations fail to connect the same operation across their records.

**Why this is strong**

- Chooses one coherent pathway rather than listing possibilities.
- Begins with the lowest-cost route: trusted access plus existing infrastructure.
- Shows how the human, cloud, and hardware layers interact.
- Identifies institutional fragmentation as the main concealment strategy.
- Avoids assuming that one technical trick makes the operation invisible.

**Common weaknesses**

- Focusing on a clever exfiltration technique without explaining the full operation.
- Assuming the insider can freely export usable weights.
- Giving the attacker unlimited nation-state capabilities.
- Treating separate cloud accounts as automatically separate workloads.
:::

#### Text
content::
\### Red team, prompt 2: what assumptions must be true for the strategy to work?

Read the model answer with one question in mind: which of these assumptions would you attack first if you were the defender?

:::callout {title="Red team, prompt 2: the model answer" tone="neutral" collapse="closed"}
The operation is plausible, but several assumptions must hold.

First, the engineer must have access to usable model parameters. Access to source code, documentation, or an inference interface would not be enough.

Second, Northstar's controls must rely too heavily on known file types, destinations, or transfer patterns. If Northstar monitors access volume, unusual privilege use, reconstruction activity, and behavioral sequences, reformatting alone may fail.

Third, the weights must survive transfer and reconstruction. Fragmentation may conceal the data but also create integrity problems and conspicuous recovery work.

Fourth, Lattice must coordinate enough compute to continue frontier development. Dividing the workload may avoid a simple threshold, but synchronized accounts can still reveal common control through shared administrators, payments, software, storage, timing, or network traffic.

Fifth, the workload must remain plausibly dual-use. A customer claiming to conduct protein inference may struggle to explain sustained training-like synchronization, checkpointing, and storage growth.

Finally, Sable must avoid revealing too much through the resulting model. Behavioral similarity would not prove derivation, but distinctive Orion-4 capabilities or failure patterns could strengthen other evidence.

Each concealment measure creates a tradeoff: more fragmentation reduces visibility in one system but creates more coordination records elsewhere.

**Why this is strong**

- Separates a conceivable plan from a workable one.
- States the access, technical, organizational, and attribution assumptions.
- Recognizes that evasion creates new evidence.
- Gives the blue team concrete dependencies to attack.

**Common weaknesses**

- Treating "insider" as equivalent to unrestricted weight access.
- Assuming training and inference are always indistinguishable.
- Treating shell companies as erasing ownership rather than delaying attribution.
- Ignoring the operational cost of reconstructing and coordinating the workload.
:::

\### Red team, prompt 3: where is the operation most vulnerable?

:::callout {title="Red team, prompt 3: the model answer" tone="neutral" collapse="closed"}
The operation is most vulnerable where the stolen weights and rented compute must be brought together.

The insider access is ambiguous by itself. The cloud workload is ambiguous by itself. Lattice's connection to Sable is ambiguous by itself. But close timing among these events can make them mutually reinforcing.

The operation requires coordination: someone must know when the weights will arrive, where they will be reconstructed, when the cluster should be ready, and how the subcontractor accounts will cooperate. That creates messages, payments, provisioning records, shared credentials, technical tests, and witnesses.

The red team could compartmentalize the operation, but more compartmentalization creates more handoffs and more chances for error.

Its best defense is delay. If the indicators remain disconnected until temporary cloud records, messages, and access logs are deleted, investigators may retain suspicion but lose the evidence needed to prove the chain.

**Why this is strong**

- Identifies one specific operational bottleneck.
- Explains why correlation is more dangerous than any single detector.
- Treats record retention and timing as central verification issues.
- Identifies a real tradeoff between compartmentalization and coordination.

**Common weaknesses**

- Saying only that "the insider might be caught."
- Naming every layer as equally vulnerable.
- Assuming defense in depth guarantees detection.
- Ignoring how quickly key evidence may disappear.
:::

#### Question: Open
id:: 58822779-3747-4b0c-8150-da186a37cfdd
content:: **Blue team, prompt 1.** You are the verifier. What should you do first?

You have suspicion and no proof, and some of the evidence you would need has a short life. Say what you order, from whom, and what you are trying to keep alive.
placeholder:: First action, who it binds, what it preserves, and what you are not yet claiming.
assessment-instructions:: This is XLab's first blue-team prompt in the Training Through the Pause worked example, asked before the model answer is shown. Score against XLab's four "why this is strong" criteria, about 25 points each. (1) Recommends an urgent but proportionate first action: a coordinated evidence-preservation order plus a targeted investigation, not a finding of violation. (2) Separates investigation from adjudication, so the answer does not declare that Sable violated the pause. (3) Tests alternative explanations rather than seeking only confirming evidence; XLab lists five, including that the engineer's activity and Lattice's workload were unrelated, that Lattice ran a different intensive but permitted workload, that the engineer transferred technical material but not usable weights, and that Sable obtained its model another way. (4) Focuses on the records most at risk of deletion, naming specifics at Northstar (weight-access and privilege logs, maintenance and evaluation records, endpoint and storage events, unusual format conversions) and at the cloud reseller and operator (account creation and beneficial-ownership records, payments and administrative logins, accelerator reservations and job timing, storage, checkpointing and network activity, links among the subcontractor accounts). Credit a subset of the specifics; do not require the full list. Deduct for XLab's four named weaknesses: jumping to a new international verification architecture; treating suspicion as proof of a violation; demanding vague "full transparency"; recommending a total shutdown before the basic facts are established. No generic praise.
feedback-instructions:: One turn. Say whether the learner ordered preservation before adjudication, which alternative explanations they left untested, and which at-risk record categories they missed. If the answer treated suspicion as proof or jumped to sanctions or to redesigning the regime, name that directly and say what it costs. Then send them to the model answer and the two prompts after it. Do not ask a follow-up question.

#### Text
content::
:::callout {title="Blue team, prompt 1: the model answer (open after you have answered)" tone="neutral" collapse="closed"}
The verifier should not yet declare that Sable violated the pause. It should issue a coordinated evidence-preservation order and open a targeted investigation.

Northstar should preserve:

- Weight-access and privilege logs;
- Maintenance and evaluation records;
- Endpoint and storage events;
- Internal transfers and unusual format conversions;
- Records from systems that could have handled the weights.

The cloud reseller and infrastructure operator should preserve:

- Account creation and beneficial-ownership records;
- Payments and administrative logins;
- Accelerator reservations and job timing;
- Storage, checkpointing, and network activity;
- Links among the subcontractor accounts.

Government investigators should preserve relevant corporate, financial, procurement, travel, and communications evidence where legally authorized.

Investigators should test several hypotheses:

- The engineer transferred Orion-4 weights, and Lattice continued prohibited training for Sable.
- The engineer's activity and Lattice's workload were unrelated.
- Lattice conducted a different intensive but permitted workload.
- The engineer transferred technical material, but not usable weights.
- Sable obtained or developed its model through another route.

The immediate goal is to preserve evidence capable of distinguishing among these explanations.

**Why this is strong**

- Recommends an urgent but proportionate first action.
- Separates investigation from adjudication.
- Tests alternatives instead of seeking only confirming evidence.
- Focuses on records most at risk of deletion.

**Common weaknesses**

- Jumping immediately to a new international verification architecture.
- Treating suspicion as proof of a pause violation.
- Demanding vague "full transparency."
- Recommending a total shutdown before establishing the basic facts.
:::

#### Text
content::
\### Blue team, prompt 2: what can each verification layer establish?

:::callout {title="Blue team, prompt 2: the model answer" tone="neutral" collapse="closed"}
No layer can prove the entire case alone.

At the hardware layer, utilization, interconnect activity, power use, accelerator reservations, and attestations could show that the related accounts collectively performed a large, coordinated computation.

This could establish the scale and timing of the workload. It would not establish that Orion-4 was used or that the activity was legally prohibited.

At the cloud layer, investigators could determine whether the accounts shared administrators, payment sources, storage, software, network destinations, or coordinated start times. They could also compare the observed workload with its declared purpose.

This could show that several nominal customers were operating one training-like workload. It might not identify the model or ultimate sponsor.

At the intelligence layer, corporate, financial, procurement, employment, and communications evidence could connect Lattice, its subcontractors, Sable, and the Northstar engineer.

This could establish common control or motive. Some intelligence may remain uncertain, classified, or difficult to use in formal adjudication.

At the human layer, witnesses could explain why the Northstar access was unusual, how the accounts were divided, or what purpose the participants understood the workload to serve.

Human evidence provides context and intent, but it must be corroborated against records.

The strongest case would be a converging timeline: unusual Northstar access, a related data transfer, rapid cloud provisioning, synchronized training-like activity, ownership links to Sable, and testimony explaining the connection.

**Why this is strong**

- Distinguishes observation from inference.
- Gives each layer a specific evidentiary role.
- Explains how the layers corroborate one another.
- Preserves uncertainty even when the evidence converges.

**Common weaknesses**

- Assuming hardware attestation can certify a lawful purpose.
- Treating customer identification as equivalent to beneficial ownership.
- Using "intelligence fusion" without discussing provenance or reliability.
- Treating a whistleblower report as a completed finding.
:::

\### Blue team, prompt 3: what finding and next action are justified?

:::callout {title="Blue team, prompt 3: the model answer" tone="neutral" collapse="closed"}
The verifier should issue a preliminary finding of a credible suspected breach of the Frontier Training Pause requiring targeted inspection.

It currently knows that:

- A Northstar engineer had a relationship with Lattice;
- Lattice and related accounts obtained substantial compute;
- The accounts ran synchronized workloads inconsistent with their simple declarations;
- Sable soon demonstrated a substantially improved Orion-like model.

It reasonably suspects that Orion-4 material was transferred and used to continue prohibited frontier development.

It does not yet know:

- Whether usable Orion-4 weights were transferred;
- Whether the full model was reconstructed;
- Whether the workload crossed the pause's technical threshold;
- Whether Sable controlled the accounts;
- Whether Northstar leadership authorized or knowingly ignored the conduct.

The inspection should prioritize:

- Identifying what the engineer accessed and transferred;
- Determining whether the cloud accounts formed one coordinated workload;
- Establishing Lattice's beneficial ownership and relationship to Sable;
- Comparing the actual workload with its declared purpose;
- Examining whether Sable's model is technically consistent with derivation from Orion-4.

Interim measures could include suspending the engineer's access, preserving the cloud environment, and pausing related accounts. A broader shutdown would require stronger evidence or a specific emergency authority.

Missing records, false declarations, or refusal to cooperate may constitute separate compliance violations. They would increase suspicion but would not by themselves prove that prohibited training occurred.

**Why this is strong**

- Gives a clear decision under uncertainty.
- Separates known facts, inferences, and unresolved questions.
- Matches the response to the strength of the evidence.
- Distinguishes procedural violations from the underlying training violation.

**Common weaknesses**

- Being so cautious that no action is recommended.
- Moving directly from suspicion to sanctions.
- Treating model similarity as proof of weight theft.
- Recommending every possible safeguard instead of prioritizing the investigation.
:::

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

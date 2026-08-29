---
id: '77e16c6b-824b-42e8-ad7c-5eec6b943f05'
title: "2.4.3 Audits and inspections"
tldr: {--{"author":"Elias's AI","timestamp":1788016160095}@@"Faithful alpha import of XLab lesson 2.4.3 Audits--}{++{"author":"Elias's AI","timestamp":1788016160095}@@"An audit, a routine inspection, and a challenge inspection answer three different questions, and each access level caps what an inspector may honestly conclude. Read Wasil, Brundage, and the OPCW managed-access rules, then draft an inspection order for Project Lattice that survives both evasion++} and {--{"author":"Elias's AI","timestamp":1788016160095}@@inspections."--}{++{"author":"Elias's AI","timestamp":1788016160095}@@a legitimate confidentiality objection."++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788016160095}@@"Imported--}{++{"author":"Elias's AI","timestamp":1788016160095}@@"Three readings (Wasil et al. on access-dependent methods, Brundage et al. section 5.3 on levels of assurance, OPCW Verification Annex Part X paragraphs 38 to 50) with four guiding questions, then an optional drill rebuilt++} from XLab's {--{"author":"Elias's AI","timestamp":1788016160095}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed --}{++{"author":"Elias's AI","timestamp":1788016160095}@@Build the inspection order lab: ten graded choice questions in four phases (purpose of audit, routine and challenge inspection; access ceiling for black-box, gray-box, and deep access; mandate clauses ++}on {--{"author":"Elias's AI","timestamp":1788016160095}@@XLab."--}{++{"author":"Elias's AI","timestamp":1788016160095}@@scope, preservation, and refusal; managed access), each followed by a Why callout citing the source, and a closing Inspection order and bounded finding callout. Hold the learner to the access ceiling: a conclusion may not exceed what the observed system, records, and period support."++}
tags: [wip]{++{"author":"Elias's AI","timestamp":1788016160095}@@
duration_minutes: 30++}
---
#### Text
content::
Next, we'll pivot from voluntary reporting channels to mandatory audits and
inspections. Read the below three excerpts to learn about on-site audits,
routine vs. challenge inspections, and levels of assurance, drawing from both
contemporary AI inspection regimes and the Chemical Weapons Convention
precedent. As you read, keep the following questions in mind:

- Who conducts the audit or inspection, and what access are they actually
  granted — to sites, to systems, to people?
- What can routine, continuous, and challenge inspections each actually
  observe, and what does that access still not let the inspector conclude?
- How does the regime protect information unrelated to compliance (managed
  access), and what does that protection cost in assurance?
- What level of assurance does each arrangement produce, and what errors or
  deception can it still miss?

\### [Access-dependent verification methods](https://arxiv.org/html/2408.16074v2#S6.SS2)
Wasil et al. (2024)

  Read On-site Inspections of Data Centers, On-site Inspections of AI
  Developers, and Key Takeaways.

\### [§5.3 Levels of assurance](https://arxiv.org/html/2601.11699v4#S5.SS3)
Brundage et al. (2026)

  Read §§5.3.1–5.3.3.

\### [Challenge inspections: general rules and managed access](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)
OPCW | Chemical Weapons Convention, Verification Annex, Part X

  Read paragraphs 38–50.

\## Four Sources

{--{"author":"Elias's AI","timestamp":1788016215814}@@\## [Optional] Exercise:--}{++{"author":"Elias's AI","timestamp":1788016215814}@@:::callout {title="Optional:++} Four Sources (12–15 {--{"author":"Elias's AI","timestamp":1788016215814}@@minutes)--}{++{"author":"Elias's AI","timestamp":1788016215814}@@minutes)" tone="neutral" collapse="closed"}
**Build the inspection order.** A power anomaly has raised a concrete concern. Choose the mechanism, set the ceiling imposed by access, and write an order that can survive both evasion and a legitimate confidentiality objection. Every question in this exercise is optional.

**Project Lattice.** A declared data center reports no training run above the treaty threshold. Independently obtained power-allocation and procurement records show a six-week expansion under the same project code. The records identify a facility and time period but not the workload. The agreement permits periodic inspections and a short-notice inspection when a specific concern cannot be resolved through consultation.
:::

\### Purpose

#### Question: Choice
id:: fab7d7aa-6c59-4b4a-bec3-a26c9273740c
optional:: true
content:: Independent audit. A developer is preparing a deployment and asks a qualified third party to test specified safety claims and assess company practices against an agreed standard.

Which job belongs to an independent audit?
options::
- [x] Evaluate specified systems and organizational practices against a standard and verify the claims within the engagement's stated scope.
- Repeat a treaty inventory count at every declared facility on the ordinary inspection calendar.
- Compel short-notice access to any site named in a state allegation, whether or not the audit contract permits it.
- Issue the legally binding compliance judgment and impose the treaty response at the end of the engagement.
shuffle:: true
feedback-instructions:: If wrong: Keep assessment separate from recurring treaty verification, challenge access, and legal adjudication. Then: Brundage et al. define an audit as systematic third-party evaluation and verification against claims and standards. Its authority and conclusion remain bounded by the engagement.++}

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016215814}@@ **Interactive exercise:** XLab's `human-audits-inspections` widget --}{++{"author":"Elias's AI","timestamp":1788016215814}@@
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Brundage et al. define an audit as systematic third-party evaluation and verification against claims and standards. Its authority and conclusion remain bounded by the engagement. Source: [Brundage et al., §§2 and 5](https://arxiv.org/html/2601.11699v4)

Independent audit: tests defined claims and practices against a standard within a stated engagement scope.
:::

#### Question: Choice
id:: a8ab5eff-df08-4ca6-972f-c066048c9927
optional:: true
content:: Routine inspection. No anomaly ++}has {++{"author":"Elias's AI","timestamp":1788016215814}@@been reported. The agreement requires recurring confirmation of declared chip inventories, seals, records, and facility controls.

Which job belongs to a routine inspection?
options::
- [x] Confirm declarations and recurring obligations on a schedule that applies without a new allegation.
- Rule out undeclared activity everywhere because all declared sites passed their scheduled checks.
- Resolve a new, site-specific noncompliance concern before evidence can be altered by replacing the ordinary schedule with no-notice access.
- Certify the organization's entire risk profile after confirming the inventory at one declared facility.
shuffle:: true
feedback-instructions:: If wrong: Routine access checks declared objects and recurring duties. Passing it does not establish completeness beyond its route. Then: Wasil et al. describe periodic on-site inspections as a way to examine declared facilities, identifiers, logs, inventories, and controls. Predictable checks are not a substitute for a route triggered by a specific concern.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Wasil et al. describe periodic on-site inspections as a way to examine declared facilities, identifiers, logs, inventories, and controls. Predictable checks are not a substitute for a route triggered by a specific concern. Source: [Wasil et al., On-site inspections of data centers](https://arxiv.org/html/2408.16074v2#S6.SS2)

Routine inspection: checks declarations and recurring obligations on an agreed calendar; it does not rule out undeclared activity elsewhere.
:::

#### Question: Choice
id:: 7a1a7e79-69ad-426f-be1c-8ad90e50666b
optional:: true
content:: Challenge inspection. What is the proper inspection route for Project Lattice?
options::
- [x] Use the short-notice challenge route to clarify the specific facility, period, project code, and possible threshold violation identified by the anomaly.
- Treat the challenge inspection as punishment: its initiation itself establishes that the facility violated the threshold.
- Wait for the next routine visit because a challenge inspection is appropriate only after the underlying violation has already been proved.
- Commission a voluntary corporate audit and allow the developer to define which project records are relevant to the anomaly.
shuffle:: true
feedback-instructions:: If wrong: A challenge inspection tests a concrete concern. It is neither a sanction nor something that waits for proof of the fact it is meant to investigate. Then: Wasil et al. identify short-notice challenge inspections as a response to suspected noncompliance. The OPCW precedent limits the mandate to clarifying the concern stated in the request.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Wasil et al. identify short-notice challenge inspections as a response to suspected noncompliance. The OPCW precedent limits the mandate to clarifying the concern stated in the request. Source: [Wasil et al.; OPCW Verification Annex, Part X](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)

Challenge inspection: Project Lattice supplies a specific concern and evidentiary target for short-notice access, not a pre-judged violation.
:::

\### Access ceiling

#### Question: Choice
id:: 079b3a4e-a81a-4b28-b08a-e408e99c987d
optional:: true
content:: Black-box. The auditor can send inputs to the candidate model through an API and observe outputs under the tested settings. No training, compute, deployment, or governance records are available.

What may an auditor conclude from black-box access?
options::
- [x] Describe model behavior under the tested inputs and settings, while leaving training history, internal deployment, compute use, and management decisions unresolved.
- Conclude that the developer's safety program is effective because the public model behaved safely in the test.
- Rule out a less restricted internal model because the tested endpoint showed no prohibited behavior.
- Verify the training-compute declaration from the observed outputs without records from the training process.
shuffle:: true
feedback-instructions:: If wrong: Tie the conclusion to the system, settings, inputs, and period actually observed. Then: Brundage et al. warn against abstraction errors: behavior of one exposed system does not establish organization-level facts or the properties of systems the auditor could not see.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Brundage et al. warn against abstraction errors: behavior of one exposed system does not establish organization-level facts or the properties of systems the auditor could not see. Source: [Brundage et al., §§5.2–5.3](https://arxiv.org/html/2601.11699v4#S5.SS3)

Black-box ceiling: supports a behavioral statement about the tested system and conditions, not a claim about training history or the organization as a whole.
:::

#### Question: Choice
id:: ae1c95d6-3de8-4907-aea7-d7b29394fd03
optional:: true
content:: Gray-box. The auditor receives an unredacted safety case, selected scheduler extracts, privileged interfaces, and interviews with several functions, but the company determines the initial record set and the auditor cannot pursue new areas without consent.

What changes when selected non-public evidence is added?
options::
- [x] Test more technical and organizational claims, while stating that omitted systems, records, and deliberate selection remain outside the assurance provided.
- Treat the evidence as independent because it is non-public, even though the company chose what the auditor could inspect.
- Rule out deliberate deception once at least one unredacted internal document and one staff interview have been obtained.
- Issue treaty-grade confirmation of the company's full risk profile because gray-box access goes beyond public testing.
shuffle:: true
feedback-instructions:: If wrong: More evidence widens the supported claim, but selection and follow-up rights still determine what can be ruled out. Then: Brundage et al. associate gray-box access, extensive documentation, monitoring, and cross-functional interviews with greater assurance, while reserving deception-resistant claims for substantially higher access levels.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Brundage et al. associate gray-box access, extensive documentation, monitoring, and cross-functional interviews with greater assurance, while reserving deception-resistant claims for substantially higher access levels. Source: [Brundage et al., §5.3.3](https://arxiv.org/html/2601.11699v4#S5.SS3)

Gray-box ceiling: supports selected system and practice claims, but cannot rule out omitted evidence or active deception when the auditee controls selection and follow-up.
:::

#### Question: Choice
id:: 8a712162-5412-40bd-9201-03ac82f593a9
optional:: true
content:: Deep access. The team may inspect relevant model internals, training processes, compute allocation, incident and governance records, and conduct private cross-functional interviews. It may follow emerging concerns within the mandate.

What can deep access add—and what limit remains?
options::
- [x] Support organization-level and historical conclusions within the defined entities, systems, claims, and period, while stating residual limits and validity conditions.
- Certify all future systems and affiliates because deep access removes the need for scope and expiry conditions.
- Accept management's account once broad access is offered, because willingness to cooperate is evidence that the records are complete.
- Replace technical and physical evidence with interviews because deep access makes human evidence sufficient for every operational fact.
shuffle:: true
feedback-instructions:: If wrong: Deep access raises the ceiling; it does not erase the engagement's entities, period, assumptions, or changing systems. Then: Higher assurance requires wider access and fewer assumptions, but Brundage et al. still require explicit scope, reasoning, validity conditions, and renewed assessment when systems change.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Higher assurance requires wider access and fewer assumptions, but Brundage et al. still require explicit scope, reasoning, validity conditions, and renewed assessment when systems change. Source: [Brundage et al., Executive Summary and §5.3](https://arxiv.org/html/2601.11699v4#S5.SS3)

Deep-access ceiling: can support scoped organization-level and historical findings, subject to completeness, stated assumptions, and expiry conditions.
:::

\### Mandate

#### Question: Choice
id:: dd1246d5-8e7a-4287-a145-126ec84258e6
optional:: true
content:: Scope and rights. Which clause gives the team a usable scope and access right?
options::
- [x] Cover the named models, facility, affiliates and contractor-held systems for the relevant period; authorize record review, system access, sampling, copying or log export, and private staff interviews as necessary to test the concern.
- Permit a tour of the main facility and review of any materials management considers relevant to the concern.
- Authorize collection of any information at any affiliated entity, whether or not it bears on the stated concern.
- Limit access to written policies because system access and private interviews would make the inspection more intrusive.
shuffle:: true
feedback-instructions:: If wrong: The mandate needs both a bounded object and concrete powers to obtain evidence from every actor holding material records. Then: The OPCW precedent ties intrusive powers to a specified concern and necessary methods. Wasil's AI inspections require access to hardware, logs, records, code, safeguards, and personnel depending on the claim.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The OPCW precedent ties intrusive powers to a specified concern and necessary methods. Wasil's AI inspections require access to hardware, logs, records, code, safeguards, and personnel depending on the claim. Source: [OPCW Part X, paras. 4, 33–45; Wasil et al.](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)

Scope and rights: reach the named systems, entities, records, sites, and period, with powers matched to the evidentiary question.
:::

#### Question: Choice
id:: 6e4469df-7f22-407e-936d-a197632a0d4f
optional:: true
content:: Preservation and protection. Which clause preserves evidence without treating confidentiality as an afterthought?
options::
- [x] From notice, prohibit alteration or deletion of relevant records held by the developer, affiliates, and contractors; use vetted personnel, secure on-site review, purpose limits, restricted copying, and recorded handling for sensitive material.
- Ask the developer to use best efforts not to delete records and promise generally that inspectors will respect trade secrets.
- Copy all systems and records into the verifier's ordinary files so that no evidence can be lost, including unrelated national-security and customer data.
- Allow the developer to delete sensitive records before the visit as long as it provides a written summary of their subject matter.
shuffle:: true
feedback-instructions:: If wrong: Preservation must bind every relevant holder; sensitive-information controls must be specific enough to operate during collection and review. Then: A workable mandate prevents loss of evidence while controlling who sees sensitive material, where review occurs, what may be copied, and how it may be used. Brundage et al. call for deep but secure access; OPCW limits collection and retention to relevant facts.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
A workable mandate prevents loss of evidence while controlling who sees sensitive material, where review occurs, what may be copied, and how it may be used. Brundage et al. call for deep but secure access; OPCW limits collection and retention to relevant facts. Source: [Brundage et al., Access; OPCW Part X, paras. 44–48](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)

Preservation and protection: bind relevant record holders at notice and pair collection with vetted access, secure handling, purpose limits, and restricted retention.
:::

#### Question: Choice
id:: b05fc152-b959-4e3a-847b-8755405c4084
optional:: true
content:: Delay or refusal. Which clause gives refusal a defined consequence without inventing proof?
options::
- [x] Set access deadlines and an alternative-access process; document unresolved refusal; permit a finding on the access duty and the escalation authorized by the agreement, without automatically treating refusal as proof of the concealed workload.
- Any delayed response conclusively proves that the prohibited training run occurred and triggers the maximum sanction.
- Continue negotiating alternatives without a deadline because any consequence for refusal would compromise managed access.
- Leave refusal to be handled as appropriate by the inspection team so that the parties retain maximum flexibility.
shuffle:: true
feedback-instructions:: If wrong: Separate breach of an access obligation from proof of the underlying activity, then identify the authorized route for each. Then: OPCW managed access requires alternative means to clarify the concern when full access is withheld. A mandate should record and escalate failure to meet the access duty, but the substantive inference depends on the governing agreement.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
OPCW managed access requires alternative means to clarify the concern when full access is withheld. A mandate should record and escalate failure to meet the access duty, but the substantive inference depends on the governing agreement. Source: [OPCW Part X, paras. 38–50](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)

Refusal: apply deadlines, alternative access, documentation, and authorized escalation; distinguish an access breach from proof of the suspected run.
:::

\### Managed access

#### Question: Choice
id:: 981821e8-226a-497d-9508-1ffd2172a391
optional:: true
content:: Alternative access. The inspection must determine whether Project Lattice used more than the permitted compute. The developer refuses to export raw scheduler logs because they contain customer names and workload details.

Which arrangement protects model and customer secrets while preserving the verification question?
options::
- [x] Let a vetted subset inspect the raw logs on site through a read-only query that exposes chip allocation, timestamps, and integrity data for the relevant period while masking unrelated customer fields; preserve the query and audit trail.
- Accept a company-produced summary stating that ++}no {--{"author":"Elias's AI","timestamp":1788016215814}@@direct Lens equivalent yet. Complete--}{++{"author":"Elias's AI","timestamp":1788016215814}@@job exceeded the threshold because++} it {--{"author":"Elias's AI","timestamp":1788016215814}@@in --}{++{"author":"Elias's AI","timestamp":1788016215814}@@avoids disclosure of all proprietary information.
- Withdraw ++}the {--{"author":"Elias's AI","timestamp":1788016215814}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-audits-inspections). Its surrounding lesson text --}{++{"author":"Elias's AI","timestamp":1788016215814}@@request whenever records contain mixed sensitive and relevant data because confidentiality takes precedence over verification.
- Require publication of the full raw logs so outside observers can independently check every workload and customer record.
shuffle:: true
feedback-instructions:: If wrong: A managed alternative ++}is {--{"author":"Elias's AI","timestamp":1788016215814}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788016215814}@@adequate only if it answers the same compute-allocation question with evidence the inspected party does not control alone. Then: Wasil et al. allow limited access sufficient to test the prohibited activity without revealing the underlying task. Brundage et al. propose on-site access by a restricted team. OPCW managed access protects unrelated information while requiring alternative means to clarify the concern.++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016215814}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-audits-inspections)*--}{++{"author":"Elias's AI","timestamp":1788016215814}@@:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Wasil et al. allow limited access sufficient to test the prohibited activity without revealing the underlying task. Brundage et al. propose on-site access by a restricted team. OPCW managed access protects unrelated information while requiring alternative means to clarify the concern. Source: [Wasil et al.; Brundage et al.; OPCW Part X](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)

Managed access: mask unrelated fields and restrict personnel, location, copying, and use—but preserve independent access to the allocation evidence needed to answer the same question.
:::

:::callout {title="Inspection order and bounded finding (open after you have answered)" tone="neutral" collapse="closed"}
The completed file separates the purpose of each mechanism, the maximum conclusion supported by each access condition, and the terms that make managed access an evidentiary accommodation rather than a veto.

- Independent audit: tests defined claims and practices against a standard within a stated engagement scope.
- Routine inspection: checks declarations and recurring obligations on an agreed calendar; it does not rule out undeclared activity elsewhere.
- Challenge inspection: Project Lattice supplies a specific concern and evidentiary target for short-notice access, not a pre-judged violation.
- Black-box ceiling: supports a behavioral statement about the tested system and conditions, not a claim about training history or the organization as a whole.
- Gray-box ceiling: supports selected system and practice claims, but cannot rule out omitted evidence or active deception when the auditee controls selection and follow-up.
- Deep-access ceiling: can support scoped organization-level and historical findings, subject to completeness, stated assumptions, and expiry conditions.
- Scope and rights: reach the named systems, entities, records, sites, and period, with powers matched to the evidentiary question.
- Preservation and protection: bind relevant record holders at notice and pair collection with vetted access, secure handling, purpose limits, and restricted retention.
- Refusal: apply deadlines, alternative access, documentation, and authorized escalation; distinguish an access breach from proof of the suspected run.
- Managed access: mask unrelated fields and restrict personnel, location, copying, and use—but preserve independent access to the allocation evidence needed to answer the same question.
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Wasil, Akash R., Tom Reed, Jack William Miller, et al. "Verification Methods for International AI Agreements." *arXiv*, Aug. 2024. [arxiv.org](https://arxiv.org/html/2408.16074)
*Wasil et al. survey verification methods available to an international AI agreement, from national technical means to personnel-based routes.*

Organisation for the Prohibition of Chemical Weapons. "Verification Annex, Part X: Challenge Inspections Pursuant to Article IX." *Chemical Weapons Convention*. [opcw.org](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)
*The CWC's managed-access rules: how an inspected state may shroud sensitive equipment and restrict analyses while challenge inspectors still resolve compliance questions.*

Brundage et al. (2026), Frontier AI auditing, is cited inline above.

XLab. "2.4.3 Audits and inspections." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-audits-inspections)
*The source lesson this page adapts, including the Build the inspection order exercise.*
:::{>>{"author":"Elias's AI","timestamp":1788016215814}@@Widget rebuilt from human-policy-labs.ts (AUDITS_INSPECTIONS_LAB). The lesson's Wasil link is the #S6.SS2 anchor, which is not itself in citations.json entries; the general html entry for the same paper is listed. Brundage 2601.11699 is only in pending.<<}++}

---
id: '77e16c6b-824b-42e8-ad7c-5eec6b943f05'
title: "Audits and inspections"
tldr: "An audit, a routine inspection, and a challenge inspection answer three different questions, and each access level caps what an inspector may honestly conclude. Read Wasil, Brundage, and the OPCW managed-access rules, then draft an inspection order for Project Lattice that survives both evasion and a legitimate confidentiality objection."
summary_for_tutor: "Three readings (Wasil et al. on access-dependent methods, Brundage et al. section 5.3 on levels of assurance, OPCW Verification Annex Part X paragraphs 38 to 50) with four guiding questions, then an optional drill rebuilt from XLab's Build the inspection order lab: ten graded choice questions in four phases (purpose of audit, routine and challenge inspection; access ceiling for black-box, gray-box, and deep access; mandate clauses on scope, preservation, and refusal; managed access), each followed by a Why callout citing the source, and a closing Inspection order and bounded finding callout. Hold the learner to the access ceiling: a conclusion may not exceed what the observed system, records, and period support."
tags: [wip]
duration_minutes: 35
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

\### Access-dependent verification methods
Wasil et al. (2024)

Read how inspections of data centers and AI developers work, and where access-dependent methods fall short.

#### Article
source:: [[../articles/wasil-verification-methods-for-international-ai-agreements]]
from:: #### ON-SITE INSPECTIONS OF DATA CENTERS
to:: The most significant precedent for the detailed inspection of hardware is the IAEA’s mandated use of bespoke tamper-evident containment seals for nuclear materials (International Atomic Energy Agency [2011](https://arxiv.org/html/2408.16074v2#bib.bib23)). These seals – each of which bears a unique identifier – are designed to provide clear evidence of any tampering or unauthorized access. IAEA inspectors examine these seals during on-site visits, allowing them to detect any undeclared movement or use of nuclear materials.

#### Article
source:: [[../articles/wasil-verification-methods-for-international-ai-agreements]]
from:: #### ON-SITE INSPECTIONS OF AI DEVELOPERS
to:: Access-dependent methods can allow for in-depth inspections of key facilities such as AI development facilities, hardware manufacturing facilities, and data centers. If international inspectors have sufficient access to these facilities, this provides a great deal of robustness to a verification regime. However, such methods may be perceived as invasive, and they may rely on the permission of nations that are suspected of unauthorized activity. Access-dependent methods can also be somewhat flexible depending on the amount of political will and the level of access that nations are willing to provide. To preserve privacy or trade secrets, inspectors may receive limited access– enough access to verify that an unauthorized training run is not being conducted but not enough access to see exactly what kind of tasks are being performed.

#### Text
content::

\### §5.3 Levels of assurance
Brundage et al. (2026)

  Read §§5.3.1–5.3.3: what a level of assurance means, the four AI Assurance
  Levels, and what each one can and cannot detect.

#### Article
source:: [[../articles/brundage-frontier-ai-auditing-toward-rigorous-third-party-assessment-of-safety-and-security-practices-at-leading-ai-companies-pdf]]
from:: ## 5.3 Levels of assurance ^5-3-levels-of
to:: **Who audits:** One or more accredited lead auditors and a range of subcontractors performing various functions. Government involvement is likely necessary for legitimacy, enforcement, and access to national security information. May require multi-jurisdictional representation and security clearances.

#### Text
content::

{>>{"author":"Elias's AI","timestamp":1788521728531}@@Repointed from the arXiv HTML render (#S5.SS3), which stops mid-§5.3.3 at the AI Assurance Levels table header and delivers about 950 of the 2,690 assigned words. The PDF carries §§5.3.1 to 5.3.3 in full on pages 29 to 35.<<}

\### Challenge inspections: general rules and managed access
OPCW | Chemical Weapons Convention, Verification Annex, Part X

  Read paragraphs 38–50.

#### Article
source:: [[../articles/opcw-part-x-challenge-inspections-pursuant-to-article-ix]]
from:: 38.  The inspected State Party shall provide access within the requested perimeter as well as, if different, the final perimeter. The extent and nature of access to a particular place or places within these perimeters shall be negotiated between the inspection team and the inspected State Party on a managed access basis.
to:: 50.  This may be accomplished by means of, inter alia, the partial removal of a shroud or environmental protection cover, at the discretion of the inspected State Party, by means of a visual inspection of the interior of an enclosed space from its entrance, or by other methods.

#### Text
content::

\## Four Sources

:::callout {title="Optional: Four Sources (12–15 minutes)" tone="neutral" collapse="closed"}
**Build the inspection order.** A power anomaly has raised a concrete concern. Choose the mechanism, set the ceiling imposed by access, and write an order that can survive both evasion and a legitimate confidentiality objection. Every question in this exercise is optional.

**Project Lattice.** A declared data center reports no training run above the treaty threshold. Independently obtained power-allocation and procurement records show a six-week expansion under the same project code. The records identify a facility and time period but not the workload. The agreement permits periodic inspections and a short-notice inspection when a specific concern cannot be resolved through consultation.
:::

#### Widget
source:: [[../widgets/human-audits-inspections]]

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
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

Brundage, Miles, Noemi Dreksler, Aidan Homewood, et al. "Frontier AI Auditing: Toward Rigorous Third-Party Assessment of Safety and Security Practices at Leading AI Companies." *arXiv*, Jan. 2026. [arxiv.org](https://arxiv.org/pdf/2601.11699v4#page=29)
*§§5.3.1 to 5.3.3, pages 29 to 35, define the four AI Assurance Levels and the access each one requires.*
{>>{"author":"Elias's AI","timestamp":1788521760470}@@Entry expanded from the previous "cited inline above" line and pointed at the PDF, because the arXiv HTML render of this paper is truncated mid-§5.3.3. Every Brundage link in this file now points at the PDF.<<}

XLab. "2.4.3 Audits and inspections." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-audits-inspections)
*The source lesson this page adapts, including the Build the inspection order exercise.*
:::{>>{"author":"Elias's AI","timestamp":1788016215814}@@Widget rebuilt from human-policy-labs.ts (AUDITS_INSPECTIONS_LAB). The lesson's Wasil link is the #S6.SS2 anchor, which is not itself in citations.json entries; the general html entry for the same paper is listed. Brundage 2601.11699 is only in pending.<<}

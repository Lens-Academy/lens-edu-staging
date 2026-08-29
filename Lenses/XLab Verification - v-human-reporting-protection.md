---
id: 'b14a66c9-7199-47ac-a777-14045193b072'
title: "2.4.2 Reporting and protection"
tldr: "A whistleblower statute is a door, not a corridor. California's SB 53 lets a covered employee walk through to the Attorney General, but says nothing about who protects her name, whether the office can judge the claim, or how a contractor's work order becomes evidence. Follow two reports along their routes and find where each one stalls."
summary_for_tutor: "A TED video link and four readings (California Labor Code 1107 to 1107.2, the AIWI/CARMA best-practice guide, Wasil et al. on whistleblowers, CIGIE Quality Standards for Investigations), then three drills rebuilt from XLab widgets. (1) Mechanism to Effect: four graded choice questions mapping anti-retaliation protection, financial reward, mandatory reporting, and professional duty to their mode of leverage. (2) Optional Follow the report: two cases (Nadia reporting to the Attorney General; a contractor's work order) with six graded choice questions each and a finding per case. (3) Audit the verifier: XLab's institutions-judgment lab on the International AI Verification Office, fourteen graded choice questions across institution, capture, evidence boundary, and response. In feedback, cite the statute section or source named in the question's Why callout, and keep the line between what a statute protects and what an institution can actually do."
tags: [wip]
duration_minutes: 60
---
#### Text
content::
This section will detail each major step of the reporting channel: from
incentivizing whistleblowers to come forth, to protecting their transmission
of information to the verifier, to ensuring that the verifier tactfully
handles and discloses the information.

Watch the below video to hear about the historical importance of
whistleblowers—but also why individuals often don't say something when they
see something.

[Watch: How whistle-blowers shape history | Kelly Richmond Pope | TED](https://youtu.be/51k3UASQE5E?si=mE8eD7RrB_yvHrpJ)

\## Whistleblower Statutes

Already, there has been legislation enacted to protect whistleblowers in the
context of preventing catastrophic risks from advanced AI models. Read the
below California whistleblower protection statute, paying attention to what
the statute does not say or leaves ambiguous: what types of disclosures are
not protected? Can you hypothesize why?

\### [California Labor Code, Chapter 5.1: Whistleblower Protections — Catastrophic Risks in AI Foundation Models](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=)
California Legislature (effective 2026)

  Read §§1107–1107.2 in full.

:::callout {title="What the contract clause covers" tone="blue"}
The operative language says a developer "shall not … enter into a … contract that prevents a covered employee from disclosing." — [California Labor Code §1107.1(a)](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=)

Read that sentence together with the statute's definition of a covered
employee, its two protected subjects, and its named recipients. The protection
attaches to disclosures within those conditions; it does not declare every NDA
void for every disclosure. The separate [AIWI/CARMA analysis of SB 53](https://aiwi.org/publication-commentary-whistleblower-protections-in-sb-53/)
also notes that public disclosure is not expressly protected by the chapter.
:::

\## Broader Standards in AI Whistleblowing

Beyond explicit statutory enactments, see the below _AI Whistleblowing Law:
Best Practice Guide_ for a more comprehensive framework for effective
implementation of whistleblower protections. The core idea is: "whistleblower rights must override confidentiality/nondisclosure agreements." — [AIWI/CARMA, Retaliation Protection](https://aiwi.org/ai-whistleblowing-law-best-practice/)

\### [AI Whistleblowing Law: Best Practice Guide](https://aiwi.org/ai-whistleblowing-law-best-practice/)
Abra Ganz and Karl Koch | AIWI and CARMA (2026)

  Read the Introduction and all seven recommendation sections; stop before
  the biographies.

\## Can the Report Leave the Organization?

Even if a whistleblower is incentivized to report, it doesn't matter if there
are physical barriers preventing them from disclosing the report, from
monitored devices to surveillance.

\### [Whistleblowers](https://arxiv.org/html/2408.16074v2#Sx5.SSx1.SSSx2)
Wasil et al. (2024)

  Read the five proposals and the limitation that follows them.

Baker proposes a similar solution against this problem of physical access,
including visits to a building that the verifier physically secures, as you
read earlier in [[../Lenses/XLab Verification - v-human-insiders|Appendix A.8, "Whistleblower Programs"]].

Legal permission, a financial incentive, and a web form do not by themselves
create a usable route. The route also has to survive monitored devices,
physical surveillance, conflicts inside the receiving office, and the need for
safe follow-up.

\## Mechanism to Effect

The sources you have read so far describe four main buckets of mechanisms to protect whistleblowers. Map each mechanism to its main mode of leverage: whether it appeals to personal incentives, places a duty on the AI developer, appeals to upholding professional conduct, or utilizes legal remedies.

#### Question: Choice
id:: 3cfd8e7c-d7ee-4a23-aba5-4bfea26104dd
content:: **Anti-retaliation protection.** California Labor Code §1107.1 bars specified rules, contracts, and retaliation for protected disclosures. ([California Labor Code §1107.1](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=))
options::
- [x] A legal right and remedies
- The reporter's incentives
- A duty on the developer
- Escalation as professional conduct
feedback-instructions:: State what the course says this lever changes: Creates a legal right and remedies after protected reporting. One or two sentences.

#### Question: Choice
id:: d71082ba-53b9-438a-ac5c-8613fedfb7bb
content:: **Financial reward.** Wasil et al. propose “financial incentives for verified information.” ([Wasil et al.](https://arxiv.org/html/2408.16074))
options::
- A legal right and remedies
- [x] The reporter's incentives
- A duty on the developer
- Escalation as professional conduct
feedback-instructions:: State what the course says this lever changes: Changes the reporter's incentives; it does not establish that the report is true. One or two sentences.

#### Question: Choice
id:: b3794742-0c9c-49a4-8722-3fa26257b7d6
content:: **Mandatory reporting.** SB 53 says a frontier developer “shall report any critical safety incident … within 15 days.” ([SB 53, Business and Professions Code §22757.13(c)](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53))
options::
- A legal right and remedies
- The reporter's incentives
- [x] A duty on the developer
- Escalation as professional conduct
feedback-instructions:: State what the course says this lever changes: Places an affirmative reporting duty on the developer rather than waiting for an insider to volunteer information. One or two sentences.

#### Question: Choice
id:: 24b15fb6-6a29-46e6-9a1a-a7cba12a89fe
content:: **Professional duty.** The ACM Code gives computing professionals an “obligation to report any signs of system risks that might result in harm.” ([ACM Code of Ethics §1.2](https://www.acm.org/binaries/content/assets/about/acm-code-of-ethics-and-professional-conduct.pdf))
options::
- A legal right and remedies
- The reporter's incentives
- A duty on the developer
- [x] Escalation as professional conduct
feedback-instructions:: State what the course says this lever changes: Makes escalation part of professional conduct, but supplies neither a safe channel nor a legal remedy on its own. One or two sentences.

#### Text
content::
:::callout {title="What each lever changes (open after you have answered)" tone="neutral" collapse="closed"}
- **Anti-retaliation protection:** Creates a legal right and remedies after protected reporting.
- **Financial reward:** Changes the reporter’s incentives; it does not establish that the report is true.
- **Mandatory reporting:** Places an affirmative reporting duty on the developer rather than waiting for an insider to volunteer information.
- **Professional duty:** Makes escalation part of professional conduct, but supplies neither a safe channel nor a legal remedy on its own.
:::

Sources: [Wasil et al.](https://arxiv.org/html/2408.16074), [SB 53, Business and Professions Code §22757.13(c)](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53), and [ACM Code of Ethics §1.2](https://www.acm.org/binaries/content/assets/about/acm-code-of-ethics-and-professional-conduct.pdf).

\## After the Report Arrives

Once the verifier receives the report, there are still careful standards they
should abide by to ensure that the report's information is protected, used,
and disclosed without compromising the reporter's confidentiality, the
integrity of the evidence, or the fairness of what follows for the accused.
Read the below excerpts from [Quality Standards for
Investigations](https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf)
for four key principles that a reliable verifier should adhere to.

\### [Quality Standards for Investigations](https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf#page=13)
Council of the Inspectors General on Integrity and Efficiency (2025)

  Read the four qualitative standards: planning, execution, reporting, and
  information management.

\## On Paper

{--{"author":"Elias's AI","timestamp":1788016058779}@@\## [Optional] Exercise:--}{++{"author":"Elias's AI","timestamp":1788016058779}@@:::callout {title="Optional:++} On Paper (7–10 {--{"author":"Elias's AI","timestamp":1788016058779}@@minutes)

--}{++{"author":"Elias's AI","timestamp":1788016058779}@@minutes)" tone="neutral" collapse="closed"}
++}Below are five fragments of internal whistleblower policies. Each fragment is
followed by one question about what the quoted language does — and does not —
establish. For each question, choose the one best answer. The answers are
revealed after you submit the whole {--{"author":"Elias's AI","timestamp":1788016058779}@@set.--}{++{"author":"Elias's AI","timestamp":1788016058779}@@set.{>>{"author":"Elias's AI","timestamp":1788016058779}@@XLab's fold text describes five policy fragments, but the widget data (human-reporting-protection.ts) is two cases with six steps each, reproduced below. Report to XLab as stale copy.<<}

**Follow the report.** Reconstruct one route out of the organization and one route from allegation to usable evidence. Every question in this exercise is optional.
:::

\### Case 1 · Protection route: A safety engineer reports to the Attorney General

Nadia is employed by a frontier developer. Her assigned work includes assessing and managing risks of critical safety incidents. She has reasonable cause to believe a planned deployment could materially contribute to more than 50 deaths by providing expert assistance for the release of a biological agent. She reports directly to the California Attorney General. Nadia signed a broad NDA. The external intake route states no anonymity or confidentiality guarantee, and no technical AI specialist has yet been assigned.

#### Question: Choice
id:: a7a790b9-1b84-4fa9-be09-5e4ddca5e572
optional:: true
content:: Person. Which statement correctly identifies Nadia's status under SB 53?
options::
- [x] Her assigned responsibility for critical-safety-incident risk places her within the chapter's definition of a covered employee.
- Every employee of a frontier developer is a covered employee for every report about model safety.
- Only officers and directors can qualify because they control the developer's response to risk.
- Technical expertise alone is enough, even when assessing or managing critical safety incidents is not part of the person's work.
- A worker becomes covered only after the Attorney General accepts the report for investigation.
shuffle:: true
feedback-instructions:: If wrong: Use the job responsibility in §1107(b), not the person's seniority, employer alone, or the recipient's later decision. Then: Section 1107(b) ties covered-employee status to responsibility for assessing, managing, or addressing risk of critical safety incidents. Nadia's assigned work meets that definition on the facts given.++}

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016058779}@@ **Interactive exercise:** XLab's `human-reporting-protection` widget --}{++{"author":"Elias's AI","timestamp":1788016058779}@@
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Section 1107(b) ties covered-employee status to responsibility for assessing, managing, or addressing risk of critical safety incidents. Nadia's assigned work meets that definition on the facts given. Source: [California Labor Code §1107(b)](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=)

Person: Nadia is a covered employee because critical-safety-incident risk is part of her assigned work.
:::

#### Question: Choice
id:: e47dea79-8b6d-4680-b12b-67cd6e95fe9c
optional:: true
content:: Subject. Which statement correctly identifies the reportable subject?
options::
- [x] Her reasonable-cause report describes a specific and substantial public danger arising from a catastrophic risk defined by the chapter.
- The chapter protects only reports made after deaths, injuries, or property losses have already occurred.
- Any disagreement about a frontier model's safety falls within the chapter, regardless of pathway or scale.
- The chapter protects legal violations but never a prospective public danger that is not yet independently unlawful.
- Reasonable belief removes the need for the information to concern one of the subjects identified in §1107.1(a).
shuffle:: true
feedback-instructions:: If wrong: Apply both parts of the rule: reasonable cause and a subject within §1107.1(a). The scenario supplies the chapter's scale and biological-risk pathway. Then: Section 1107.1(a)(1) covers a reasonable-cause disclosure of a specific and substantial public danger resulting from catastrophic risk. Section 1107(a) supplies the scale and listed pathways.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Section 1107.1(a)(1) covers a reasonable-cause disclosure of a specific and substantial public danger resulting from catastrophic risk. Section 1107(a) supplies the scale and listed pathways. Source: [California Labor Code §§1107(a), 1107.1(a)(1)](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=)

Subject: The reported biological-risk pathway and scale fall within the chapter's catastrophic-risk route.
:::

#### Question: Choice
id:: 025504ef-2786-454c-8119-59eb4e9af619
optional:: true
content:: Recipient. Does Nadia have to report internally before going to the Attorney General?
options::
- [x] No. The Attorney General is an expressly named recipient, and §1107.1 does not make internal reporting a prerequisite.
- Yes. Protection begins only after the developer ++}has {++{"author":"Elias's AI","timestamp":1788016058779}@@received the report and missed a response deadline.
- Yes. All catastrophic-risk reports must first go to the Office of Emergency Services rather than the Attorney General.
- No, because §1107.1 expressly treats the Attorney General, any legislator, and the press as equivalent recipients.
- Only if a manager with authority over Nadia gives permission for the external disclosure.
shuffle:: true
feedback-instructions:: If wrong: Read the recipient list in §1107.1(a). The internal process is an additional route, not a gate in front of the Attorney General. Then: The Attorney General is named in §1107.1(a). The chapter also names specified internal recipients and a federal authority, but it does not require Nadia to use an internal channel first.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The Attorney General is named in §1107.1(a). The chapter also names specified internal recipients and a federal authority, but it does not require Nadia to use an internal channel first. Source: [California Labor Code §1107.1(a), (c), and (e)](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=)

Recipient: Nadia may report directly to the Attorney General without first reporting to the developer.
:::

#### Question: Choice
id:: 045982de-329d-425a-bf4f-f5f9994f1c02
optional:: true
content:: Identity protection. What protection for Nadia's identity does this route establish?
options::
- [x] SB 53 requires an anonymous internal process for large developers, but the chapter does not itself require the external Attorney General route to be anonymous or confidential.
- Every recipient named in §1107.1(a) must accept the report anonymously and may never learn the reporter's identity.
- Because the report is confidential, neither the receiving authority nor the developer can know who made it.
- The NDA itself supplies the confidentiality guarantee that is missing from the external reporting route.
- The anonymous internal process prevents a developer from inferring identity from access, timing, or the small number of people who knew the facts.
shuffle:: true
feedback-instructions:: If wrong: Separate the anonymous internal process in §1107.1(e) from the external recipients in §1107.1(a). The AIWI/CARMA guide asks for both anonymity and confidentiality externally because the chapter does not specify them. Then: The chapter requires an anonymous internal process at a large frontier developer. It does not impose an express anonymity or confidentiality rule on the external Attorney General route. AIWI/CARMA recommend both for receiving authorities.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The chapter requires an anonymous internal process at a large frontier developer. It does not impose an express anonymity or confidentiality rule on the external Attorney General route. AIWI/CARMA recommend both for receiving authorities. Source: [California Labor Code §1107.1(e); AIWI/CARMA, Disclosure Channels and Agency Requirements](https://aiwi.org/ai-whistleblowing-law-best-practice/)

Identity protection: The external route is legally available, but SB 53 does not itself supply the anonymity and confidentiality guarantees recommended by AIWI/CARMA.
:::

#### Question: Choice
id:: 22ef0a95-d3f7-47e3-baa0-fd60997af81b
optional:: true
content:: NDA and remedy. What follows from Nadia's NDA and the chapter's retaliation provisions?
options::
- [x] The developer may not use the contract to prevent this protected disclosure or retaliate for it; the chapter supplies fees, burden shifting, and possible injunctive relief.
- The NDA is void in full, including provisions unrelated to protected reporting and disclosures to recipients outside the statute.
- Protection applies only if a later investigation proves every material allegation in the report to be true.
- Nadia has no route to interim relief and may seek damages only after a final judgment on the underlying catastrophic risk.
- The principal statutory remedy is a financial award calculated as a share of any penalty imposed on the developer.
shuffle:: true
feedback-instructions:: If wrong: Keep the contract rule within the protected disclosure defined by the chapter, then read the remedies in §1107.1(f)–(i). Then: Sections 1107.1(a) and (b) prevent specified contracts from blocking protected disclosures. The chapter also provides attorney's fees, shifts the burden after a contributing-factor showing, and authorizes temporary or preliminary injunctive relief.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Sections 1107.1(a) and (b) prevent specified contracts from blocking protected disclosures. The chapter also provides attorney's fees, shifts the burden after a contributing-factor showing, and authorizes temporary or preliminary injunctive relief. Source: [California Labor Code §1107.1(a), (b), and (f)–(i)](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=)

NDA and remedy: The contract cannot block this protected report; retaliation can trigger fees, burden shifting, and injunctive relief.
:::

#### Question: Choice
id:: cd58e552-861a-4426-a396-f439ef57f79f
optional:: true
content:: Competent investigator. What does naming the Attorney General as a recipient establish?
options::
- [x] It establishes a protected destination, not that the office already has the technical expertise or a clear mandate to resolve a catastrophic-risk report without a legal violation.
- It establishes that the office has sufficient AI expertise, investigative access, and authority for every report within the chapter.
- It makes the court hearing any retaliation claim responsible for performing the technical catastrophic-risk investigation.
- It gives Nadia the same mandatory monthly investigation updates that §1107.1 requires from a large developer's internal process.
- It establishes investigative competence as long as the intake system can accept an anonymous submission.
shuffle:: true
feedback-instructions:: If wrong: A legally permitted recipient, a protected identity, and an institution able to investigate are separate design questions. Then: AIWI/CARMA recommend that receiving agencies have or can obtain technical AI expertise. Their SB 53 analysis separately identifies uncertainty about the Attorney General's mandate where the report alleges catastrophic risk but ++}no {--{"author":"Elias's AI","timestamp":1788016058779}@@direct Lens equivalent yet. --}{++{"author":"Elias's AI","timestamp":1788016058779}@@legal violation.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
AIWI/CARMA recommend that receiving agencies have or can obtain technical AI expertise. Their SB 53 analysis separately identifies uncertainty about the Attorney General's mandate where the report alleges catastrophic risk but no legal violation. Source: [AIWI/CARMA, Agency Requirements; Whistleblower Protections in SB 53, Executive Summary](https://aiwi.org/publication-commentary-whistleblower-protections-in-sb-53/)

Competent investigator: The Attorney General is a protected recipient, but expertise and authority to act still require institutional design.
:::

:::callout {title="Case 1 finding: The legal route exists, but the protection chain is incomplete" tone="neutral" collapse="closed"}
Nadia fits the covered-person definition, the subject falls within the catastrophic-risk route, the Attorney General is an authorized recipient, and the NDA cannot block this protected disclosure. The first unresolved condition is identity protection on the external route. The office's technical competence and authority to act are a second unresolved condition.
:::

\### Case 2 · Evidence path: A contractor supplies a work order

An independent cooling contractor emails a verifier an original work order showing that Project Lattice added capacity for 1,024 accelerators over six weeks. The attachment bears project code PX-814. A utility allocation record obtained separately contains the same code and dates. The contractor installed cooling equipment but had no access to cluster workloads or model records.

#### Question: Choice
id:: b934f477-dcaa-4ae5-abf3-5e649f90ff3e
optional:: true
content:: Preserve. What should the receiving office do first with the report and attachment?
options::
- [x] Retain the original message, attachment, and available metadata; open a case record; restrict and record access; and seek timely preservation of relevant records.
- Copy the allegation into an intake summary and discard the original message so the reporter cannot later be identified from metadata.
- Wait until investigators decide the allegation is probably true before preserving records that may otherwise be deleted in ordinary operations.
- Ask the contractor to recreate the work order without metadata and treat the cleaner copy as the evidentiary original.
- Forward the unredacted report to every organization that may hold relevant records before setting handling restrictions or a case identifier.
shuffle:: true
feedback-instructions:: If wrong: Preservation comes before a merits decision. Keep the original submission and its context while limiting unnecessary exposure of the source. Then: CIGIE requires accurate and complete case-file documentation and preservation of chain of custody. Early preservation protects records before routine deletion or deliberate alteration can remove them.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
CIGIE requires accurate and complete case-file documentation and preservation of chain of custody. Early preservation protects records before routine deletion or deliberate alteration can remove them. Source: [CIGIE Quality Standards for Investigations, Accurate and ++}Complete {++{"author":"Elias's AI","timestamp":1788016058779}@@Documentation; Collecting Evidence](https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf#page=13)

Preserve: Keep the original submission and metadata, create the case record, log handling, and protect relevant records from loss.
:::

#### Question: Choice
id:: 77d2e956-934a-49d7-b55f-c8ce43007308
optional:: true
content:: Authenticate. What would authentication establish at this stage?
options::
- [x] It would test the contractor's claimed access and the work order's origin and integrity; ++}it {++{"author":"Elias's AI","timestamp":1788016058779}@@would not establish that an unauthorized workload ran.
- A strong professional reputation would authenticate both the document and every inference the contractor draws from it.
- The matching project code would authenticate the work order and prove the alleged workload without further records.
- Without a cryptographic signature, the work order cannot be authenticated by any combination of source access, counterpart records, or system metadata.
- The verifier must obtain management's certification that the work order is genuine before examining any other evidence.
shuffle:: true
feedback-instructions:: If wrong: Separate provenance and integrity from the truth of the allegation. A genuine work order can still be misunderstood or selectively presented. Then: CIGIE requires investigators to verify the validity of information and evidence. Here that means testing role, access, origin, and integrity. Authentication does not prove what workload used the installed capacity.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
CIGIE requires investigators to verify the validity of information and evidence. Here that means testing role, access, origin, and integrity. Authentication does not prove what workload used the installed capacity. Source: [CIGIE Quality Standards for Investigations, Collecting Evidence](https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf#page=13)

Authenticate: Test the contractor's access and the document's provenance and integrity without treating authenticity as proof of the allegation.
:::

#### Question: Choice
id:: 0ff05bf4-75fb-447e-aca3-bb5fefebcd7c
optional:: true
content:: Investigate. How should the office frame the investigation?
options::
- [x] Define the allegation and applicable rule, then lawfully pursue records and accounts that could support, qualify, or contradict it.
- Collect only material that supports the contractor because exculpatory evidence belongs ++}in {++{"author":"Elias's AI","timestamp":1788016058779}@@a later adversarial response.
- Begin by sending the full report and source identity to implicated management so it can define the scope and select the records.
- Record a compliance finding at intake, then use the investigation to calculate the appropriate response.
- Ask ++}the {--{"author":"Elias's AI","timestamp":1788016058779}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-reporting-protection). Its surrounding lesson text--}{++{"author":"Elias's AI","timestamp":1788016058779}@@contractor to infer which model ran; an informed inference can replace workload records when the source lacks access to them.
shuffle:: true
feedback-instructions:: If wrong: The investigation tests an allegation. It++} is {--{"author":"Elias's AI","timestamp":1788016058779}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788016058779}@@not a search for support for a conclusion already recorded. Then: CIGIE requires objective collection and analysis of both exculpatory and incriminating evidence. Complaint evaluation also asks whether to investigate, refer, or take no further action under the office's authority and priorities.++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016058779}@@\## Companies --}{++{"author":"Elias's AI","timestamp":1788016058779}@@:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
CIGIE requires objective collection and analysis of both exculpatory and incriminating evidence. Complaint evaluation also asks whether to investigate, refer, or take no further action under the office's authority and priorities. Source: [CIGIE Quality Standards for Investigations, Complaint Evaluation; Executing Investigations](https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf#page=13)

Investigate: Define the allegation and rule, then seek both supporting and contradictory evidence through lawful, independent methods.
:::

#### Question: Choice
id:: 43251f68-62b5-4173-ab31-7c9fe609d471
optional:: true
content:: Corroborate. What does the utility record add, and what is still missing?
options::
- [x] It independently supports the project code, dates, and capacity expansion; scheduler, lineage, access, and authorization records are still needed to identify the workload and its status.
- It proves that an unauthorized frontier-model training run consumed the added capacity during those dates.
- ++}A {++{"author":"Elias's AI","timestamp":1788016058779}@@second contractor repeating the first contractor's account would add more independent weight than records held by the utility or provider.
- If the contractor may receive a reward, the matching utility record cannot corroborate any part of the account.
- Because the contractor lacked workload access, evidence of infrastructure expansion has no verification value ++}and {--{"author":"Elias's AI","timestamp":1788016058779}@@B--}{++{"author":"Elias's AI","timestamp":1788016058779}@@should be excluded.
shuffle:: true
feedback-instructions:: If wrong: Match the independent record to the fact it can test. A power allocation can support an expansion without identifying the code or model that later used it. Then: Wasil et al. describe financial records and inspections as ways to test whistleblower claims. Their corroborative value remains claim-specific. Baker's Table 14 likewise separates personnel who know about infrastructure from personnel who know about AI activity and authorization.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Wasil et al. describe financial records and inspections as ways to test whistleblower claims. Their corroborative value remains claim-specific. Baker's Table 14 likewise separates personnel who know about infrastructure from personnel who know about AI activity and authorization. Source: [Wasil et al., comparison table; Baker et al., Appendix A.8, Table 14](https://arxiv.org/html/2408.16074)

Corroborate: The utility record supports the expansion. Workload, model lineage, access, and authorization remain unestablished.
:::

#### Question: Choice
id:: 3d91138b-1309-4c93-8c78-017bbf63548b
optional:: true
content:: Package. What belongs in the evidentiary package?
options::
- [x] The allegation, source-access limits, authenticated items, handling record, independent support, contradictions, unresolved questions, applicable rule, and identity restrictions.
- Only the strongest bottom-line conclusion, because underlying contradictions and limits may confuse the decision-maker.
- The reporter's identity in every copy so each recipient can make its own credibility judgment before reading the evidence.
- Supporting records and the allegation, with exculpatory or mitigating information held separately unless enforcement counsel requests it.
- The original attachments without a statement of provenance, handling, scope, or which propositions each item can support.
shuffle:: true
feedback-instructions:: If wrong: A receiving verifier needs the evidence and its limits. CIGIE requires reports to be supported by the case file and to include relevant exculpatory and mitigating information. Then: CIGIE requires accurate, complete, impartial reporting supported by case-file evidence. The package should preserve the distinction between what the source observed, what investigators established, and what remains unresolved.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
CIGIE requires accurate, complete, impartial reporting supported by case-file evidence. The package should preserve the distinction between what the source observed, what investigators established, and what remains unresolved. Source: [CIGIE Quality Standards for Investigations, Reporting](https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf#page=13)

Package: Send a supported, scoped record that includes provenance, handling, corroboration, contradictions, limits, and identity restrictions.
:::

#### Question: Choice
id:: d76b2f9b-ac5a-4e0d-b12c-8b9518598818
optional:: true
content:: Pass on. What if the receiving office lacks authority over the suspected violation?
options::
- [x] Refer the matter promptly to an appropriate authority, preserve the record and handling restrictions, document the transfer, and retain the scoped case history required by policy.
- Keep the matter and investigate it fully; receiving a protected report supplies any jurisdiction or access power the office lacks.
- Return the original report to the developer and ask management to select an authority with the necessary jurisdiction.
- Publish the evidentiary package so that whichever institution has authority can identify itself and take over.
- Delete the sending office's case record after transfer so there is only one copy and no competing chain of custody.
shuffle:: true
feedback-instructions:: If wrong: Authority does not arise from intake. Referral must preserve the record, the source restrictions, and accountability for the transfer. Then: CIGIE's complaint-evaluation standard expressly includes referral to another appropriate authority. Its documentation and information-management requirements continue to govern how the sending office records and protects the transfer.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
CIGIE's complaint-evaluation standard expressly includes referral to another appropriate authority. Its documentation and information-management requirements continue to govern how the sending office records and protects the transfer. Source: [CIGIE Quality Standards for Investigations, Complaint Evaluation; Managing Investigative Information](https://www.ignet.gov/sites/default/files/files/Quality%20Standards%20for%20Investigations%20July-2025.pdf#page=13)

Pass on: Make a documented referral to a competent, authorized body without losing the record, its restrictions, or the history of handling.
:::++}

{++{"author":"Elias's AI","timestamp":1788016058779}@@:::callout {title="Case 2 finding: The report has become usable evidence, but only for a bounded claim" tone="neutral" collapse="closed"}
The preserved and authenticated work order, independently matched to the utility record, supports the claim that Project Lattice expanded infrastructure at the stated time. It does not establish which workload ran or whether a rule was breached. The transmitted package must state that limit and identify the technical and governance records still required.
:::

:::callout {title="Two different thresholds: The report can travel without proving the case" tone="neutral" collapse="closed"}
**Protection finding.** A statute can protect a person, subject, and recipient while leaving identity safeguards, technical competence, or authority unresolved.

**Evidence finding.** Preserved and corroborated records may support one fact without supporting the larger allegation. The transmitted package must say exactly where that boundary lies.
:::

++}\## Companies A and B (15–20 {--{"author":"Elias's AI","timestamp":1788016058779}@@min)--}{++{"author":"Elias's AI","timestamp":1788016058779}@@min){>>{"author":"Elias's AI","timestamp":1788016058779}@@XLab's heading says "Companies A and B", but the widget it wraps (human-institutions-judgment) is the "Audit the verifier" lab about the International AI Verification Office, and its eyebrow reads "Institutions and policy judgment · 2.4.4" although it sits in 2.4.2. Report to XLab.<<}

\### Audit the verifier

Inspect the institution before relying on its finding. Then separate what the human record establishes from what still requires technical or physical evidence, and match each decision to its legal and evidentiary threshold.

:::callout {title="The International AI Verification Office" tone="blue"}
The Office is examining Project Lattice. Two engineers independently report that management approved a concealed run after receiving a safety warning. Authenticated messages show the warning reached the relevant executives. Power and procurement records corroborate the project code and dates. The developer refuses raw scheduler logs and chip inventory, although the treaty mandate expressly requires both. A council—not the Office—has authority to impose sanctions.
:::

\### Institution

#### Question: Choice
id:: bdaba121-d855-4f70-888f-d8205b15f4e2
content:: Independence. The developer selects the audit provider from an unrestricted list, negotiates the scope, pays a renewable annual fee, and may block publication by ending the engagement.

What makes this audit arrangement insufficiently independent?
options::
- [x] The provider's future income, scope, and ability to publish depend on the auditee whose claims it must test.
- Independence is adequate because the provider is legally incorporated separately from the developer.
- Technical expertise cures the financial and publication conflict because a capable auditor will recognize manipulation.
- The conflict is immaterial if the provider discloses the payment relationship after publishing a favorable report.
shuffle:: true
feedback-instructions:: If wrong: Ask what happens to fees, access, scope, and publication when the auditor reaches an unwelcome conclusion. Then: Brundage et al. call for disclosed financial relationships, standardized terms that prevent auditor shopping, cooling-off periods, and payment models that reduce dependence on auditees.++}

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016058779}@@ **Interactive exercise:** XLab's `human-institutions-judgment` widget--}{++{"author":"Elias's AI","timestamp":1788016058779}@@
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Brundage et al. call for disclosed financial relationships, standardized terms that prevent auditor shopping, cooling-off periods, and payment models that reduce dependence on auditees. Source: [Brundage et al., Independent experts](https://arxiv.org/html/2601.11699v4)

Independence: deficient when the auditee controls selection, renewal, scope, or publication and an unfavorable finding threatens future income.
:::

#### Question: Choice
id:: 8168b860-0c7b-4f46-bdf6-0753e9f7f75c
content:: Competence. The assigned team consists entirely of model evaluators. It++} has no {++{"author":"Elias's AI","timestamp":1788016158236}@@compute-accounting, data-center, forensic interviewing, evidence-handling, or treaty-law expertise.

What competence does the Project Lattice inquiry require?
options::
- [x] The team cannot credibly resolve the inquiry without adding the disciplines needed to interpret infrastructure, records, interviews, evidence integrity, and the governing obligation.
- Model-evaluation expertise is sufficient because every frontier-AI compliance question ultimately concerns model behavior.
- Treaty lawyers can resolve the factual dispute from the text of the access obligation without technical or investigative specialists.
- Specialist competence matters only after the Office has already issued its factual finding and needs to defend it on appeal.
shuffle:: true
feedback-instructions:: If wrong: List the factual and legal questions in the case, then ask whether one discipline can answer all of them. Then: Brundage et al. recommend multidisciplinary teams, subcontracting, or consortia when one audit organization lacks the required breadth.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Brundage et al. recommend multidisciplinary teams, subcontracting, or consortia when one audit organization lacks the required breadth. Source: [Brundage et al., Independent experts](https://arxiv.org/html/2601.11699v4)

Competence: must match the claim across AI evaluation, compute and facility operations, investigation, evidence handling, security, and law.
:::

#### Question: Choice
id:: be1064e9-d4c7-4377-9b04-2adeff1bed78
content:: Accountability. Which arrangement makes the Office accountable without giving the auditee a veto?
options::
- [x] Disclose methods and conflicts where possible, keep a traceable case file, use independent quality review, and allow correction of factual errors without permitting suppression of conclusions.
- Keep methods, conflicts, and quality controls secret because any external review would compromise sensitive information.
- Require the developer to approve the final wording so procedural fairness prevents reputational harm.
- Publish every raw record and source identity so the public can reproduce the investigation without relying on institutional review.
shuffle:: true
feedback-instructions:: If wrong: Accountability needs traceability, quality control, and correction of error; it does not require either total secrecy or auditee control. Then: Brundage et al. pair rigorous, traceable methods with procedural fairness: companies may correct factual errors but should not exert undue influence over conclusions.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Brundage et al. pair rigorous, traceable methods with procedural fairness: companies may correct factual errors but should not exert undue influence over conclusions. Source: [Brundage et al., Rigor and Clarity](https://arxiv.org/html/2601.11699v4)

Accountability: requires traceable methods, conflict disclosure, independent quality review, and a factual-correction process that does not become a publication veto.
:::

#### Question: Choice
id:: 938a5673-fe29-4f08-a045-fe8b85200d03
content:: Authority. The treaty authorizes the Office to compel records, conduct inspections, and issue compliance findings. Only the council may impose sanctions.

What does the Office's authority permit it to do?
options::
- [x] The Office may investigate and make the authorized compliance finding; enforcement requires a separate council decision under the treaty.
- Any institution able to obtain evidence has inherent authority to impose proportionate sanctions without a council decision.
- Because it cannot sanction, the Office may collect evidence but cannot issue a compliance finding.
- The council's enforcement authority makes the Office's investigative mandate unnecessary; the council should determine the facts itself.
shuffle:: true
feedback-instructions:: If wrong: Separate collection and assessment, the compliance judgment, and the institution authorized to order a response. Then: Wasil et al. identify institutional powers and handling noncompliance as separate design questions. Evidence access does not create enforcement authority by implication.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Wasil et al. identify institutional powers and handling noncompliance as separate design questions. Evidence access does not create enforcement authority by implication. Source: [Wasil et al., Future directions](https://arxiv.org/html/2408.16074v2#S1.SS2)

Authority: the Office may compel, investigate, and find compliance only as the treaty provides; sanctions remain with the council.
:::

#### Question: Choice
id:: 068b4cd6-43e9-4e42-b22c-eb7df9c0da93
content:: Access. Management supplies summaries and selected interviewees but withholds raw scheduler logs, chip inventory, and private staff contact.

What does the current access condition do to the Office's finding?
options::
- [x] It caps the substantive finding because the auditee controls the evidentiary frame and the operational facts cannot be checked directly.
- It provides deep access because the summaries cover every category named in the mandate.
- It supports a favorable finding because supplying any non-public information demonstrates good-faith cooperation.
- It has no effect because interviews can substitute for scheduler logs and inventory in proving the workload and compute threshold.
shuffle:: true
feedback-instructions:: If wrong: Formal authority is not actual access. Ask who selected the evidence and whether the disputed operational fact can be checked from it. Then: Brundage et al. distinguish independent status from access adequate to support the claim. Company-selected summaries and interviewees leave an informational dependency intact.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Brundage et al. distinguish independent status from access adequate to support the claim. Company-selected summaries and interviewees leave an informational dependency intact. Source: [Brundage et al., §§2 and 5.3](https://arxiv.org/html/2601.11699v4#S5.SS3)

Access: management-selected summaries and interviewees do not support a deep finding when raw operational evidence and private contact are withheld.
:::

\### Capture

#### Question: Choice
id:: 685b6374-a60d-4035-9991-e8cabf1cc20d
content:: Financial. Which fact is financial capture?
options::
- [x] A favorable result protects a renewable auditee-paid fee and future engagements.
- Management chooses the records and interviewees that define the inquiry.
- Staff adopt the developer's view of which safety problems are normal and not worth escalating.
- A minister delays publication to protect a diplomatic agreement.
shuffle:: true
feedback-instructions:: If wrong: Identify the pressure operating through money and future work. Then: Financial capture changes the verifier's incentives through fees, renewal, funding, appointment, or future employment.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Financial capture changes the verifier's incentives through fees, renewal, funding, appointment, or future employment. Source: [Brundage et al., Independent experts](https://arxiv.org/html/2601.11699v4)

Financial capture: revenue or future work depends on avoiding a finding that displeases the auditee or funder.
:::

#### Question: Choice
id:: 5e1a6b33-9c20-4afc-b2fa-07e1e14a584f
content:: Informational. Which fact is informational capture?
options::
- [x] Management chooses the records, systems, interviewees, and initial questions that define what the verifier can see.
- The provider relies on a renewable fee from the audited company.
- Inspectors come to regard the developer's risk tolerance as the natural professional baseline.
- The government suppresses a finding that could damage its strategic relationship with another state.
shuffle:: true
feedback-instructions:: If wrong: Look for control over the facts, questions, and people entering the evidentiary frame. Then: Informational capture persists even when the verifier is formally outside the company: the regulated party can still determine what becomes knowable.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Informational capture persists even when the verifier is formally outside the company: the regulated party can still determine what becomes knowable. Source: [Brundage et al., Access and Independence](https://arxiv.org/html/2601.11699v4)

Informational capture: the auditee controls the evidentiary frame by selecting records, systems, interviewees, and questions.
:::

#### Question: Choice
id:: 921faae2-f63f-4f84-9687-49cb6b9b8bd7
content:: Cultural. Which fact is cultural capture?
options::
- [x] Through repeated staffing exchanges and socialization, the verifier adopts the developer's assumptions about what counts as normal, serious, or worth investigating.
- The developer withholds raw logs and offers a summary instead.
- The auditee threatens to move its paid engagement to another provider.
- The cabinet orders the Office to avoid a finding during treaty negotiations.
shuffle:: true
feedback-instructions:: If wrong: Cultural capture changes the verifier's professional frame, not only its access, funding, or formal instructions. Then: A verifier can remain formally independent while internalizing the regulated organization's categories, urgency, and tolerance for weak evidence.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
A verifier can remain formally independent while internalizing the regulated organization's categories, urgency, and tolerance for weak evidence. Source: [Brundage et al., §§4.1 and 5](https://arxiv.org/html/2601.11699v4)

Cultural capture: the institution internalizes the auditee's assumptions about normal practice and the seriousness of possible failure.
:::

#### Question: Choice
id:: 7b9e4d21-3c5a-4e8f-a1d6-2f0b8c9e4a37
content:: Political. Which fact is political capture?
options::
- [x] A minister narrows or delays the finding to protect a government, company, or diplomatic relationship.
- Inspectors absorb the developer's professional norms through repeated collaboration.
- A provider fears losing an annual audit fee after an adverse conclusion.
- Management chooses which documents the investigators may inspect.
shuffle:: true
feedback-instructions:: If wrong: Identify direct pressure serving governmental or diplomatic interests. Then: Political capture operates through appointment, direction, delay, scope restriction, or suppression for political rather than evidentiary reasons.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Political capture operates through appointment, direction, delay, scope restriction, or suppression for political rather than evidentiary reasons. Source: [Brundage et al., Independent experts](https://arxiv.org/html/2601.11699v4)

Political capture: officials alter scope, timing, or conclusions to protect governmental, corporate, or diplomatic interests.
:::

\### Evidence boundary

#### Question: Choice
id:: 2c6d8e4f-9a1b-4c3d-8e5f-6a7b8c9d0e1f
content:: Human record. The engineers had access to the decision process, gave independent accounts, and produced authenticated contemporaneous messages showing the warning reached the executives.

What can the human and documentary record establish here?
options::
- [x] That the warning reached the named executives and that management discussed or authorized the project as the messages record, subject to the defined people and period.
- The exact compute used by the workload, because the engineers participated in the decision process.
- That every operational instruction was carried out exactly as authorized, because the approval record is authenticated.
- That no other concealed project existed, because two sources independently described Project Lattice.
shuffle:: true
feedback-instructions:: If wrong: Human evidence is strongest on organizational knowledge, decision, warning, staging, and intent, not automatic proof of machine activity. Then: Baker et al. map personnel to the violations they can observe while emphasizing compartmentalization and collusion. Authentication and independent accounts support the organizational fact, not facts outside those sources' access.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Baker et al. map personnel to the violations they can observe while emphasizing compartmentalization and collusion. Authentication and independent accounts support the organizational fact, not facts outside those sources' access. Source: [Baker et al., §4.3](https://arxiv.org/html/2507.15916#S4.SS3)

Human-mechanism finding: authenticated messages and independent sources can establish who received the warning and what management decided within the observed process.
:::

#### Question: Choice
id:: 9d0e1f2a-3b4c-4d5e-8f6a-7b8c9d0e1f2a
content:: Operational fact. What still requires technical or physical evidence?
options::
- [x] Whether the run occurred as described, which workload executed, which chips participated, and whether total compute crossed the treaty threshold.
- Whether the executives received the warning shown in their authenticated message thread.
- Whether the engineers held the roles confirmed by personnel and access records.
- Whether a manager threatened a reporter in a recorded meeting corroborated by an independent witness.
shuffle:: true
feedback-instructions:: If wrong: Separate the organizational decision from execution, hardware participation, workload identity, and measured compute. Then: Wasil et al. require facility access, chip identifiers, activity logs, training records, and related technical measures to test operational AI-development claims. Human evidence can direct that inquiry but not replace it.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Wasil et al. require facility access, chip identifiers, activity logs, training records, and related technical measures to test operational AI-development claims. Human evidence can ++}direct {--{"author":"Elias's AI","timestamp":1788016058779}@@Lens equivalent yet. Complete --}{++{"author":"Elias's AI","timestamp":1788016058779}@@that inquiry but not replace it. Source: [Wasil et al., Access-dependent methods](https://arxiv.org/html/2408.16074v2#S6.SS2)

Technical/physical requirement: scheduler and activity logs, chip inventory, and facility evidence must establish execution, workload identity, participating hardware, and compute.
:::

\### Response

#### Question: Choice
id:: 4e5f6a7b-8c9d-4e0f-9a1b-2c3d4e5f6a7b
content:: Investigation. What decision is supported before the withheld logs are obtained?
options::
- [x] Open or continue a focused investigation and preserve evidence: the concern is specific, plausible, partly corroborated, and points to records capable of resolving it.
- Find the training prohibition violated because the sources and power record together prove the workload and compute threshold.
- Impose sanctions immediately because delay would reward concealment, even though the council has not acted and the operational fact is unresolved.
- Close the matter because evidence insufficient for enforcement is necessarily insufficient for investigation.
shuffle:: true
feedback-instructions:: If wrong: The investigation threshold is intentionally lower than the compliance and enforcement thresholds. Then: A specific corroborated allegation with an identifiable evidence path justifies preservation and investigation before the evidence supports a final substantive judgment.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
A specific corroborated allegation with an identifiable evidence path justifies preservation and investigation before the evidence supports a final substantive judgment. Source: [Baker et al., personnel layer; Wasil et al.](https://arxiv.org/html/2507.15916#S4.SS3)

Investigation: justified by a specific, plausible, partly corroborated concern and a realistic path to resolving evidence.
:::

#### Question: Choice
id:: 6a7b8c9d-0e1f-4a2b-8c3d-4e5f6a7b8c9d
content:: Compliance finding. The treaty expressly requires scheduler logs and chip inventory. The Office issued a valid demand, offered managed access, and the deadline expired without production.

What compliance finding does the documented refusal support?
options::
- [x] Find breach of the access and cooperation obligation, while recording that the underlying training-run allegation remains a separate unresolved question.
- Find both the access breach and the prohibited run proved because refusal necessarily means the logs are incriminating.
- Issue no compliance finding until the Office proves the underlying run; access duties cannot be breached independently.
- Treat the access finding as the Office's authority to impose whatever enforcement measure ++}it {++{"author":"Elias's AI","timestamp":1788016058779}@@considers proportionate.
shuffle:: true
feedback-instructions:: If wrong: Identify the obligation whose facts are already established, and keep it separate from the concealed conduct the records were meant to test. Then: A valid demand, an express duty, managed alternatives, and documented refusal can establish noncompliance with access. Whether refusal proves the underlying activity depends on a separate inference rule ++}in the {--{"author":"Elias's AI","timestamp":1788016058779}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-reporting-protection). Its surrounding lesson text --}{++{"author":"Elias's AI","timestamp":1788016058779}@@agreement.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
A valid demand, an express duty, managed alternatives, and documented refusal can establish noncompliance with access. Whether refusal proves the underlying activity depends on a separate inference rule in the agreement. Source: [OPCW managed-access precedent; Wasil et al.](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)

Compliance finding: the documented refusal establishes breach of the express access duty; it does not by itself establish the prohibited run.
:::

#### Question: Choice
id:: 8c9d0e1f-2a3b-4c4d-9e5f-6a7b8c9d0e1f
content:: Enforcement. When ++}is {--{"author":"Elias's AI","timestamp":1788016058779}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788016058779}@@enforcement justified?
options::
- [x] When an authorized trigger or valid compliance finding exists and the council applies the treaty's authority, required process, proportionality, and urgency rules.
- Whenever investigators hold a strong suspicion, even if the treaty assigns sanctions elsewhere and no compliance process has concluded.
- Whenever an independent auditor recommends sanctions, because independence supplies enforcement authority.
- Automatically at the maximum level after any access delay so that enforcement remains deterrent.
shuffle:: true
feedback-instructions:: If wrong: Evidence strength, legal authority, decision process, and proportionality are separate conditions for enforcement. Then: Wasil et al. identify institutional powers, handling noncompliance, and proportionate enforcement as distinct design questions. A verifier's finding can trigger but does not itself create the authorized response.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Wasil et al. identify institutional powers, handling noncompliance, and proportionate enforcement as distinct design questions. A verifier's finding can trigger but does not itself create the authorized response. Source: [Wasil et al., Future directions](https://arxiv.org/html/2408.16074v2#S1.SS2)

Enforcement: requires an authorized trigger or valid finding, the designated decision-maker, required process, and a proportionate response—not suspicion alone.
:::

:::callout {title="Institutional assessment and response record (open after you have answered)" tone="neutral" collapse="closed"}
The record identifies institutional weaknesses, names the mechanism of capture, preserves the boundary between organizational and operational facts, and assigns separate decisions to investigation, compliance, and enforcement.

- Independence: deficient when the auditee controls selection, renewal, scope, or publication and an unfavorable finding threatens future income.
- Competence: must match the claim across AI evaluation, compute and facility operations, investigation, evidence handling, security, and law.
- Accountability: requires traceable methods, conflict disclosure, independent quality review, and a factual-correction process that does not become a publication veto.
- Authority: the Office may compel, investigate, and find compliance only as the treaty provides; sanctions remain with the council.
- Access: management-selected summaries and interviewees do not support a deep finding when raw operational evidence and private contact are withheld.
- Financial capture: revenue or future work depends on avoiding a finding that displeases the auditee or funder.
- Informational capture: the auditee controls the evidentiary frame by selecting records, systems, interviewees, and questions.
- Cultural capture: the institution internalizes the auditee's assumptions about normal practice and the seriousness of possible failure.
- Political capture: officials alter scope, timing, or conclusions to protect governmental, corporate, or diplomatic interests.
- Human-mechanism finding: authenticated messages and independent sources can establish who received the warning and what management decided within the observed process.
- Technical/physical requirement: scheduler and activity logs, chip inventory, and facility evidence must establish execution, workload identity, participating hardware, and compute.
- Investigation: justified by a specific, plausible, partly corroborated concern and a realistic path to resolving evidence.
- Compliance finding: the documented refusal establishes breach of the express access duty; it does not by itself establish the prohibited run.
- Enforcement: requires an authorized trigger or valid finding, the designated decision-maker, required process, and a proportionate response—not suspicion alone.
:::++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016058779}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-reporting-protection)*--}{++{"author":"Elias's AI","timestamp":1788016058779}@@:::callout {title="Works cited" tone="neutral" collapse="closed"}
California Legislature. "Whistleblower Protections: Catastrophic Risks in AI Foundation Models, Labor Code §§ 1107–1107.2." *California Legislative Information*, effective 1 Jan. 2026. [leginfo.legislature.ca.gov](https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title=)
*California's enacted protections for covered frontier-developer employees who disclose specified catastrophic-risk concerns or violations.*

California Legislature. "SB-53 Artificial Intelligence Models: Large Developers (2025-2026)." *California Legislative Information*, 2025. [leginfo.legislature.ca.gov](https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53)
*The enacted bill text includes the frontier developer's duty to report critical safety incidents under Business and Professions Code §22757.13.*

Ganz, Abra, and Karl Koch. "AI Whistleblowing Law: Best Practice Guide." AI Whistleblower Initiative and Center for AI Risk Management & Alignment, 2 July 2026. [aiwi.org](https://aiwi.org/ai-whistleblowing-law-best-practice/)
*Recommendations for AI whistleblower law covering protected disclosures and people, reporting channels, retaliation, remedies, notice, and capable receiving agencies.*

Ganz, Abra, and Karl Koch. "Whistleblower Protections in SB 53: Strengths, Limitations, and Open Questions." AI Whistleblower Initiative, 2026. [aiwi.org](https://aiwi.org/publication-commentary-whistleblower-protections-in-sb-53/)
*An analysis of SB 53's protected people and disclosures, available channels and remedies, and remaining implementation gaps.*

Wasil, Akash R., Tom Reed, Jack William Miller, et al. "Verification Methods for International AI Agreements — Whistleblowers." *arXiv*, Aug. 2024. [arxiv.org](https://arxiv.org/html/2408.16074v2#Sx5.SSx1.SSSx2)
*The paper's whistleblowers section: five ways a government could incentivize insiders to come forward, and why incentives alone fail when an employer can block contact with the verifier.*

Wasil, Akash R., Tom Reed, Jack William Miller, et al. "Verification Methods for International AI Agreements." *arXiv*, Aug. 2024. [arxiv.org](https://arxiv.org/html/2408.16074)
*Wasil et al. survey verification methods available to an international AI agreement, from national technical means to personnel-based routes.*

Association for Computing Machinery. "ACM Code of Ethics and Professional Conduct." 2018. [acm.org](https://www.acm.org/binaries/content/assets/about/acm-code-of-ethics-and-professional-conduct.pdf)
*Section 1.2 describes computing professionals' responsibility to report signs of system risks that might result in harm.*

Organisation for the Prohibition of Chemical Weapons. "Verification Annex, Part X: Challenge Inspections Pursuant to Article IX." *Chemical Weapons Convention*. [opcw.org](https://www.opcw.org/chemical-weapons-convention/annexes/verification-annex/part-x-challenge-inspections-pursuant)
*The CWC's managed-access rules: how an inspected state may shroud sensitive equipment and restrict analyses while challenge inspectors still resolve compliance questions.*

The CIGIE Quality Standards for Investigations, Brundage et al. (2026), and the TED talk are cited inline above.

XLab. "2.4.2 Reporting and protection." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-reporting-protection)
*The source lesson this page adapts, including the Mechanism to Effect, Follow the report, and Audit the verifier exercises.*
:::{>>{"author":"Elias's AI","timestamp":1788016058779}@@Widgets rebuilt from whistleblower-levers.ts, human-reporting-protection.ts, and human-policy-labs.ts (INSTITUTIONS_JUDGMENT_LAB). Options carry XLab's exact text; correct option listed first in the data, so shuffle is on. CIGIE and Brundage URLs are in citations.json pending, not entries, so they are noted inline rather than listed.<<}++}

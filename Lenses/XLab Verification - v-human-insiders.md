---
id: 'dae72ebf-335a-4bd5-b970-b2b3e72230ed'
title: "2.4.1 Insiders and human sources"
tldr: "An insider's job title tells you where they stood, not what they saw. Read Baker et al. on whistleblower programs, interviews, and intelligence, then work six Project Lattice sources one at a time: what each could observe, what stayed out of view, and which record they never controlled could check the claim."
summary_for_tutor: "Two excerpts from Baker et al. (2025), section 4.3 and Appendix A.8, are embedded as Article segments. Then an optional drill built from XLab's Who knows what? widget: six source cards (evaluator, training engineer, infrastructure operator, procurement, contractor, executive), each with three graded choice questions on observation, boundary, and corroboration, followed by a Project Lattice case report with four graded credibility questions, a final finding, and four failure modes. When the learner over-reaches, apply the widget's own line: a job title alone proves nothing; limit the claim to what the person could observe."
tags: [wip]
duration_minutes: 30
---
#### Text
content::
In this section, you will learn about the three main categories of human- or
personnel-based verification: whistleblower programs, personnel interviews,
and national intelligence activities. First, read the below excerpt of Baker's
_Verifying International Agreements on AI_ paper, paying attention to each
mechanism's unique strengths, failure modes, and applicable circumstances.

\## Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment

Mauricio Baker, Gabriel Kulp, Oliver Marks, Miles Brundage, and Lennart Heim (2025). [arxiv.org](https://arxiv.org/abs/2507.15916v2)

This page reproduces [§4.3 “Personnel-Based Verification Layers”](https://arxiv.org/html/2507.15916#S4.SS3) and [Appendix A.8 “Whistleblower Programs”](https://arxiv.org/html/2507.15916#A1.SS8) in full, including Tables 8, 9, and 14.

The source text and tables are reproduced under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
from:: ### 4.3 Personnel-Based Verification Layers
to:: In contrast to other, more technical verification mechanisms, _personnel-based verification_ relies on the difficulty of having large groups of people collude without disclosures or leaks. Verifiers could systematically seek disclosures or leaks through whistleblower programs, interviews of personnel, and national intelligence activities. Intelligence activities, though, might involve cyber or signals intelligence, not only direct communication with personnel.

#### Text
content::
We'll pay special attention to whistleblower programs, which have the most
historical precedence, existing infrastructure, and potential verifiability
effectiveness.

#### Article
source:: [[../articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment]]
from:: #### A.8 Whistleblower Programs
to:: Avoiding excess disclosure: Employees could be allowed to disclose only a very small amount of information to the Verifier, as discussed in above footnotes. Further, the Prover and Verifier could jointly state agreed-on, reasonable bounds of protected whistleblowing (including high-level descriptions of potential violations and information to investigate further, but excluding digital transfers of Prover models, data, or code outside of a confidentiality-preserving technology). Parties could also agree on what questions or information a Verifier may share with an employee, so that the Prover could learn from their employees if the Verifier is inappropriately pressuring them to disclose IP.

#### Text
content::
\## Insider Report

Even when the human source is truthful and legally allowed to report, however,
reporting channels can still fail in various ways, which the next section will
cover.

:::callout {title="Optional: Insider Report (8–10 minutes)" tone="neutral" collapse="closed"}
**Who knows what?**

For each source, identify what they could observe, what they could not know, and which independent record could verify the claim. You will produce a short assessment for each source.

A job title alone proves nothing. Limit the claim to what this person could observe, state what remains unknown, and choose evidence the source did not control.

Every question in this exercise is optional. Six sources come first; a case report and a credibility assessment follow.
:::

\### Evaluator (Evaluation)

Ran the capability evaluation and kept the test harness and results.

**Reported claim:** The model crossed the agreed capability threshold in our evaluation run.

**Incentives:** May want to defend the test method, avoid blame for a missed risk, or meet a professional duty to report.

**Consistency test:** Compare the test setup and exclusions with notes, code changes, earlier accounts, and the saved results.

#### Question: Choice
id:: 75110da9-a326-4ea8-ad51-02af9c0e48fc
optional:: true
content:: Evaluator. Could observe: What could this person observe directly?
options::
- Decisions and risk warnings: What leadership approved, what the board was told, which risks were accepted, and what was withheld.
- [x] Result under the tested setup: Scores, prompts, methodology, exclusions, and anomalies in the evaluation they ran.
- Training records and model lineage: Training code, datasets, checkpoints, run configuration, and which model descended from which run.
feedback-instructions:: If the learner chose wrongly, say: Limit the claim to the evaluation this person ran. In every case restate the source's bound in one sentence: the evaluator can describe the test method and results.

#### Question: Choice
id:: 799ba374-49a6-4b61-bdc0-95f22070f0c8
optional:: true
content:: Evaluator. Could not establish: What part of the suspected violation would remain outside their view?
options::
- Why leadership approved the work: Technical participation does not show why leaders authorized the work or whether they intended to conceal it.
- [x] What happened after the test: A test result does not show how the model was later deployed, modified, or monitored in production.
- Whether the decision was carried out: A formal decision does not prove that staff carried it out or that the record is complete.
feedback-instructions:: If the learner chose wrongly, say: The evaluator did not observe what happened after the test. Keep it to two sentences.

#### Question: Choice
id:: 6b58d0ec-2939-453f-99c8-013f70e93858
optional:: true
content:: Evaluator. Check against: Which independent record could verify the claim?
options::
- Model registry and scheduler records: Checkpoint hashes, storage and access logs, run manifests, scheduler records, and independent code review.
- Decision records created at the time: Board minutes, risk memos, approval tickets, messages, and technical evidence that tests implementation.
- [x] Evaluation records created at the time: Signed result files, prompt and harness versions, run identifiers, and deployment records from another system.
feedback-instructions:: If the learner chose wrongly, say: Check records created during the evaluation, then examine deployment separately. Then give the assessment: The evaluator can describe the test method and results. They cannot establish how the model was later deployed. Check signed test records and independent deployment records.

#### Text
content::
:::callout {title="Assessment: Evaluator (open after you have answered)" tone="neutral" collapse="closed"}
The evaluator can describe the test method and results. They cannot establish how the model was later deployed. Check signed test records and independent deployment records.
:::

\### Training engineer (Model development)

Configured the training run, handled checkpoints, and can trace the model's lineage.

**Reported claim:** This checkpoint came from an undeclared run using the restricted training configuration.

**Incentives:** May face consequences for taking part, feel loyalty to the team, or want to prevent misuse of their work.

**Consistency test:** Compare the dates, configuration, checkpoint lineage, and access claims with records maintained by other teams.

#### Question: Choice
id:: 169d12cb-4f4a-48f9-a74d-979b8bb2adba
optional:: true
content:: Training engineer. Could observe: What could this person observe directly?
options::
- Cluster activity: Allocated accelerators, job timing, utilization, access events, power draw, and unusual log gaps.
- [x] Training records and model lineage: Training code, datasets, checkpoints, run configuration, and which model descended from which run.
- Decisions and risk warnings: What leadership approved, what the board was told, which risks were accepted, and what was withheld.
feedback-instructions:: If the learner chose wrongly, say: Focus on the run configuration, workload, and model lineage. Keep it to two sentences.

#### Question: Choice
id:: 9d556476-f021-4d9c-b00c-23d6c4809bd6
optional:: true
content:: Training engineer. Could not establish: What part of the suspected violation would remain outside their view?
options::
- Why the job ran or who approved it: Infrastructure records show that compute ran. They do not show its purpose or who authorized it.
- Whether the decision was carried out: A formal decision does not prove that staff carried it out or that the record is complete.
- [x] Why leadership approved the work: Technical participation does not show why leaders authorized the work or whether they intended to conceal it.
feedback-instructions:: If the learner chose wrongly, say: The engineer may not know why leadership approved the work. Keep it to two sentences.

#### Question: Choice
id:: b7079aae-7053-46d3-a736-f11ccf964f12
optional:: true
content:: Training engineer. Check against: Which independent record could verify the claim?
options::
- Provider telemetry and hardware inventory: Scheduler data held by the provider, power and network telemetry, hardware attestations, and a physical count.
- [x] Model registry and scheduler records: Checkpoint hashes, storage and access logs, run manifests, scheduler records, and independent code review.
- Decision records created at the time: Board minutes, risk memos, approval tickets, messages, and technical evidence that tests implementation.
feedback-instructions:: If the learner chose wrongly, say: Check model and run records from storage, scheduling, and review systems. Then give the assessment: The training engineer can describe the workload and model lineage, but may not know why leadership approved the work. Check checkpoint hashes, model-registry entries, scheduler records, and access logs.

#### Text
content::
:::callout {title="Assessment: Training engineer (open after you have answered)" tone="neutral" collapse="closed"}
The training engineer can describe the workload and model lineage, but may not know why leadership approved the work. Check checkpoint hashes, model-registry entries, scheduler records, and access logs.
:::

\### Infrastructure operator (Compute operations)

Administers the cluster and can see allocations, failures, access events, and telemetry.

**Reported claim:** A large eight-week job ran on the cluster under a project code omitted from the declaration.

**Incentives:** May want to protect the operations team, avoid discipline for missing logs, or report misuse of systems they maintain.

**Consistency test:** Compare job timing, accelerator count, access events, and log gaps with provider records, power data, and physical inventory.

#### Question: Choice
id:: ae1ca8bb-24f2-4a6e-9074-5b1bef5f7666
optional:: true
content:: Infrastructure operator. Could observe: What could this person observe directly?
options::
- Facility capacity: Racks, chips, cooling, power, interconnects, and installation dates.
- [x] Cluster activity: Allocated accelerators, job timing, utilization, access events, power draw, and unusual log gaps.
- Training records and model lineage: Training code, datasets, checkpoints, run configuration, and which model descended from which run.
feedback-instructions:: If the learner chose wrongly, say: Focus on the cluster records this operator can access. Keep it to two sentences.

#### Question: Choice
id:: 87be6dbf-830d-4014-9ba6-27d9c05a00a6
optional:: true
content:: Infrastructure operator. Could not establish: What part of the suspected violation would remain outside their view?
options::
- What the facility ran: A contractor can see what was installed without knowing which workload or model used it.
- Why leadership approved the work: Technical participation does not show why leaders authorized the work or whether they intended to conceal it.
- [x] Why the job ran or who approved it: Infrastructure records show that compute ran. They do not show its purpose or who authorized it.
feedback-instructions:: If the learner chose wrongly, say: The records do not explain the job's purpose or who approved it. Keep it to two sentences.

#### Question: Choice
id:: e791cd15-ee7c-4cbc-b507-bc58bf40b775
optional:: true
content:: Infrastructure operator. Check against: Which independent record could verify the claim?
options::
- Model registry and scheduler records: Checkpoint hashes, storage and access logs, run manifests, scheduler records, and independent code review.
- Utility, delivery, and inspection records: Power allocations, permits, delivery manifests, work orders, maintenance logs, and site inspection.
- [x] Provider telemetry and hardware inventory: Scheduler data held by the provider, power and network telemetry, hardware attestations, and a physical count.
feedback-instructions:: If the learner chose wrongly, say: Check telemetry and inventory records outside this operator's control. Then give the assessment: The infrastructure operator can establish that a large job ran, when it ran, and which cluster it used. They may not know its purpose or who approved it. Check provider telemetry, power records, and hardware inventory.

#### Text
content::
:::callout {title="Assessment: Infrastructure operator (open after you have answered)" tone="neutral" collapse="closed"}
The infrastructure operator can establish that a large job ran, when it ran, and which cluster it used. They may not know its purpose or who approved it. Check provider telemetry, power records, and hardware inventory.
:::

\### Procurement or finance staff (Commercial records)

Processed purchases and payments charged to an unfamiliar project code.

**Reported claim:** The organization acquired far more accelerator capacity than it declared.

**Incentives:** May fear blame for approving the purchase, want to protect the budget owner, or have fewer ties to the technical team.

**Consistency test:** Reconcile quantities, dates, project codes, counterparties, and payment flows across internal and external ledgers.

#### Question: Choice
id:: 25552ebc-ab6a-49d3-8a26-2b6a40a4f4f2
optional:: true
content:: Procurement or finance staff. Could observe: What could this person observe directly?
options::
- Facility capacity: Racks, chips, cooling, power, interconnects, and installation dates.
- [x] Purchases and payments: Orders, invoices, project codes, counterparties, payment timing, and off-ledger anomalies.
- Cluster activity: Allocated accelerators, job timing, utilization, access events, power draw, and unusual log gaps.
feedback-instructions:: If the learner chose wrongly, say: This source sees purchase and payment records, not the machines in operation. Keep it to two sentences.

#### Question: Choice
id:: 0649106a-96fb-49a9-923a-6928c362f61a
optional:: true
content:: Procurement or finance staff. Could not establish: What part of the suspected violation would remain outside their view?
options::
- What the facility ran: A contractor can see what was installed without knowing which workload or model used it.
- [x] Which workload used the capacity: A purchase or payment can expose undeclared capacity without identifying the model or code that used it.
- Why the job ran or who approved it: Infrastructure records show that compute ran. They do not show its purpose or who authorized it.
feedback-instructions:: If the learner chose wrongly, say: A ledger can expose capacity without identifying the workload that consumed it. Keep it to two sentences.

#### Question: Choice
id:: 6726c7f2-5ef5-4d83-b157-1a35811222ad
optional:: true
content:: Procurement or finance staff. Check against: Which independent record could verify the claim?
options::
- Utility, delivery, and inspection records: Power allocations, permits, delivery manifests, work orders, maintenance logs, and site inspection.
- [x] Records held by counterparties: Vendor invoices, bank or ledger entries, shipping and customs records, serials, and receiving logs.
- Provider telemetry and hardware inventory: Scheduler data held by the provider, power and network telemetry, hardware attestations, and a physical count.
feedback-instructions:: If the learner chose wrongly, say: Check records held by vendors, banks, shippers, customs agencies, and receiving staff. Then give the assessment: Procurement or finance staff can document what was bought and how it was paid for. They may not know which workload used it. Check vendor invoices, payment records, shipping documents, serial numbers, and receiving logs.

#### Text
content::
:::callout {title="Assessment: Procurement or finance staff (open after you have answered)" tone="neutral" collapse="closed"}
Procurement or finance staff can document what was bought and how it was paid for. They may not know which workload used it. Check vendor invoices, payment records, shipping documents, serial numbers, and receiving logs.
:::

\### Supplier or data-center contractor (Facility operations)

Installed power, cooling, racks, or chips during a capacity expansion.

**Reported claim:** The site added capacity under a project code that does not appear in the declared facility plan.

**Incentives:** May seek a reward, protect future contracts, pursue a commercial dispute, or avoid being linked to concealed work.

**Consistency test:** Compare the project code, quantities, site, and installation dates across work orders and later accounts.

#### Question: Choice
id:: 3fb74f44-e8f0-42c0-9b3b-e38001e60e6a
optional:: true
content:: Supplier or data-center contractor. Could observe: What could this person observe directly?
options::
- Purchases and payments: Orders, invoices, project codes, counterparties, payment timing, and off-ledger anomalies.
- Cluster activity: Allocated accelerators, job timing, utilization, access events, power draw, and unusual log gaps.
- [x] Facility capacity: Racks, chips, cooling, power, interconnects, and installation dates.
feedback-instructions:: If the learner chose wrongly, say: Focus on the equipment and infrastructure this contractor installed or serviced. Keep it to two sentences.

#### Question: Choice
id:: 239a2190-c393-49b5-afa6-b420b1aeb10f
optional:: true
content:: Supplier or data-center contractor. Could not establish: What part of the suspected violation would remain outside their view?
options::
- Which workload used the capacity: A purchase or payment can expose undeclared capacity without identifying the model or code that used it.
- Why the job ran or who approved it: Infrastructure records show that compute ran. They do not show its purpose or who authorized it.
- [x] What the facility ran: A contractor can see what was installed without knowing which workload or model used it.
feedback-instructions:: If the learner chose wrongly, say: The contractor did not see which model or workload used the capacity. Keep it to two sentences.

#### Question: Choice
id:: 9020fb34-3244-4f07-9112-4dfc30e4a6f8
optional:: true
content:: Supplier or data-center contractor. Check against: Which independent record could verify the claim?
options::
- Records held by counterparties: Vendor invoices, bank or ledger entries, shipping and customs records, serials, and receiving logs.
- Provider telemetry and hardware inventory: Scheduler data held by the provider, power and network telemetry, hardware attestations, and a physical count.
- [x] Utility, delivery, and inspection records: Power allocations, permits, delivery manifests, work orders, maintenance logs, and site inspection.
feedback-instructions:: If the learner chose wrongly, say: Check utility, delivery, installation, maintenance, and inspection records. Then give the assessment: The supplier or contractor can describe what was installed, where, and when. They may not know how the capacity was used. Check utility allocations, delivery manifests, work orders, maintenance logs, and the site itself.

#### Text
content::
:::callout {title="Assessment: Supplier or data-center contractor (open after you have answered)" tone="neutral" collapse="closed"}
The supplier or contractor can describe what was installed, where, and when. They may not know how the capacity was used. Check utility allocations, delivery manifests, work orders, maintenance logs, and the site itself.
:::

\### Executive or board member (Governance)

Received risk warnings and took part in the decision to proceed.

**Reported claim:** Leadership understood the restriction and deliberately approved work outside the declaration.

**Incentives:** May want to defend the official account, limit personal liability, oppose management, or correct an earlier decision.

**Consistency test:** Compare the decision, dates, attendees, stated reasons, and warnings with records created at the time and accounts from other participants.

#### Question: Choice
id:: c352506e-a647-4cef-bcbe-0aeca5dbe395
optional:: true
content:: Executive or board member. Could observe: What could this person observe directly?
options::
- Result under the tested setup: Scores, prompts, methodology, exclusions, and anomalies in the evaluation they ran.
- [x] Decisions and risk warnings: What leadership approved, what the board was told, which risks were accepted, and what was withheld.
- Training records and model lineage: Training code, datasets, checkpoints, run configuration, and which model descended from which run.
feedback-instructions:: If the learner chose wrongly, say: Focus on the decisions and warnings this person received or discussed. Keep it to two sentences.

#### Question: Choice
id:: 8770a1d3-5251-4ad1-876c-df7e966692ed
optional:: true
content:: Executive or board member. Could not establish: What part of the suspected violation would remain outside their view?
options::
- What happened after the test: A test result does not show how the model was later deployed, modified, or monitored in production.
- Why leadership approved the work: Technical participation does not show why leaders authorized the work or whether they intended to conceal it.
- [x] Whether the decision was carried out: A formal decision does not prove that staff carried it out or that the record is complete.
feedback-instructions:: If the learner chose wrongly, say: Approving a plan does not show exactly how staff carried it out. Keep it to two sentences.

#### Question: Choice
id:: 1be5e66f-018b-45ed-afaa-0a6de18ad8b5
optional:: true
content:: Executive or board member. Check against: Which independent record could verify the claim?
options::
- Evaluation records created at the time: Signed result files, prompt and harness versions, run identifiers, and deployment records from another system.
- Model registry and scheduler records: Checkpoint hashes, storage and access logs, run manifests, scheduler records, and independent code review.
- [x] Decision records created at the time: Board minutes, risk memos, approval tickets, messages, and technical evidence that tests implementation.
feedback-instructions:: If the learner chose wrongly, say: Check records made at the time and technical evidence of what staff actually did. Then give the assessment: The executive or board member can describe decisions, warnings, and intent. They may not know every technical action taken. Check minutes, approvals, messages, and independent technical records.

#### Text
content::
:::callout {title="Assessment: Executive or board member (open after you have answered)" tone="neutral" collapse="closed"}
The executive or board member can describe decisions, warnings, and intent. They may not know every technical action taken. Check minutes, approvals, messages, and independent technical records.
:::

\### Case report · Project Lattice

A cooling contractor reports that Project Lattice added power and chilled-water capacity for 1,024 accelerators over six weeks. The contractor has applied for a financial reward and provides work-order code PX-814. A utility record obtained separately contains the same code and dates. The contractor did not have access to cluster workloads.

Assess the report through access, incentives, consistency, and independent corroboration. Do not rely on the reporter's reputation.

#### Question: Choice
id:: b3ffe01c-9f0b-423a-b30d-69ed7454034c
optional:: true
content:: Access. What can this source actually know?
options::
- [x] The installed capacity, site, dates, and project code — not the workload or its authorization.
- That an unauthorized frontier-model training run occurred.
- Nothing useful, because contractors are outside the AI developer.
feedback-instructions:: If wrong, say: Separate the physical work they witnessed from the workload they could not see. Then: The contractor can describe infrastructure work they performed or saw. That access does not show which model ran, who authorized it, or whether a rule was breached.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The contractor can describe infrastructure work they performed or saw. That access does not show which model ran, who authorized it, or whether a rule was breached.

Access: The contractor can describe the capacity expansion and project code, but not the workload or its authorization.
:::

#### Question: Choice
id:: 3c57b0db-a5e9-4213-8952-14c26b939fac
optional:: true
content:: Incentives. How should the financial reward affect the assessment?
options::
- [x] Record the possible reward and the costs of reporting. Treat motive as a reason to check the claim carefully, not as proof that it is true or false.
- Assume the report is unreliable because the source may receive a reward.
- Treat the personal risk of reporting as proof that the allegation is true.
feedback-instructions:: If wrong, say: The reward may encourage a false report. Fear of retaliation or lost work may discourage a true one. Neither decides whether this report is accurate. Then: Incentives matter because they may shape whether and how someone reports. They do not replace evidence.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Incentives matter because they may shape whether and how someone reports. They do not replace evidence.

Incentives: The possible reward and the risk of losing work both matter, but neither confirms nor disproves the report.
:::

#### Question: Choice
id:: ec477876-3814-4c11-b7cb-2e2538fa990a
optional:: true
content:: Consistency. Which consistency check matters here?
options::
- [x] Check whether the site, dates, quantity, and project code remain stable across interviews and fit the known timeline.
- Require every retelling to use exactly the same words and peripheral details.
- Accept matching accounts from coworkers selected and briefed together as independent confirmation.
feedback-instructions:: If wrong, say: Focus on the facts that matter. Identical wording may reflect rehearsal, and coordinated accounts are not independent evidence. Then: Minor details may change as people recall an event. The central facts should remain consistent with the timeline and other evidence.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Minor details may change as people recall an event. The central facts should remain consistent with the timeline and other evidence.

Consistency: The site, dates, quantity, and project code should remain stable and fit the known timeline. Scripted agreement is not independent evidence.
:::

#### Question: Choice
id:: 4042ff68-00e6-48df-bc37-5e63691ec921
optional:: true
content:: Independent corroboration. Which evidence adds the most weight to this report?
options::
- [x] The independently obtained utility log, followed by serial, receiving, scheduler, and authorization records from separate systems.
- The contractor's reputation for honesty in the local industry.
- A spreadsheet the contractor created after deciding to report.
feedback-instructions:: If wrong, say: Use evidence created independently of the source and outside the source's control. Then: The matching project code and dates link the report to an external record. They support the claim that the site expanded, but not a claim about the workload.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The matching project code and dates link the report to an external record. They support the claim that the site expanded, but not a claim about the workload.

Corroboration: The utility record supports the infrastructure claim. Workload and approval records are still needed.
:::

:::callout {title="Finding: Further investigation warranted · no compliance finding" tone="neutral" collapse="closed"}
The report supports a finding that Project Lattice expanded infrastructure at the stated site and time. It does not show which workload ran or whether any rule was breached. Investigators should preserve the work orders and utility record, then obtain receiving records, serial numbers, scheduler telemetry, model-lineage records, and approval documents.

**Failure modes to check**

- **Selective truth.** The expansion may be real even if the claimed prohibited workload is not. Do not treat proof of infrastructure as proof of how it was used.
- **Coordinated cover story.** Matching accounts are not independent if managers selected, briefed, or monitored the speakers.
- **Management staging.** A clean tour and selected records show what management chose to present. They do not rule out undeclared activity elsewhere.
- **Suppression.** A lack of reports means little if staff have no safe reporting channel, cannot see the relevant declarations, or reasonably fear retaliation.
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*A six-layer verification framework whose personnel-based layers map which workers can observe different violations and why disclosures still need independent confirmation.*

Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI — Appendix A.8: Whistleblower Programs." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/html/2507.15916#A1.SS8)
*Baker et al. examine secure contact, suppression, incentives, confidentiality, and which supply-chain personnel can observe different violations.*

XLab. "2.4.1 Insiders and human sources." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/human-insiders)
*The source lesson this page adapts, including the Who knows what? source-assessment exercise.*
:::{>>{"author":"Elias's AI","timestamp":1788015819856}@@Widget human-insiders rebuilt from src/lib/verification/data/human-insiders.ts: 18 source questions (6 actors x observe/boundary/corroborate), 4 credibility questions on the Project Lattice case report, final finding and failure modes. Option order follows the data file's choices order. All optional because XLab folds it as optional.<<}

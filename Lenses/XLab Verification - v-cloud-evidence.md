---
id: 'eaadd7dc-7ba4-4cff-aa7c-6ad4e95f1a50'
title: "2.2.4 Interpreting cloud evidence"
tldr: {--{"author":"Elias's AI","timestamp":1788016206964}@@"Faithful alpha import of XLab lesson 2.2.4 Interpreting--}{++{"author":"Elias's AI","timestamp":1788016206964}@@"Nine short drills on one habit: reading a++} cloud {--{"author":"Elias's AI","timestamp":1788016206964}@@evidence."--}{++{"author":"Elias's AI","timestamp":1788016206964}@@record for exactly what it proves. A billing line, a KYC file, a power curve: each supports one conclusion and tempts you toward three more. Practice stopping at the first."++}
summary_for_tutor: {--{"author":"Elias's AI","timestamp":1788016206964}@@"Imported --}{++{"author":"Elias's AI","timestamp":1788016206964}@@"Problem-set lens adapted ++}from {++{"author":"Elias's AI","timestamp":1788016206964}@@XLab lesson 2.2.4, a native reproduction of XLab's nine-task cloud-evidence drill. Tasks: six true or false statements; odd one out plus a one-sentence principle; select all available data categories; four matching questions (observable to strongest conclusion); a fill-the-gaps verification map; ordering the six stages of the Egan and Heim KYC scheme; naming four mechanisms; a case (qualify the evidence, multi-select); and a permissible-inference question. ++}XLab's {--{"author":"Elias's AI","timestamp":1788016206964}@@canonical Verification curriculum. Preserve source framing. XLab currently blocks cross-site embedding, so linked external exercises must be completed on XLab."--}{++{"author":"Elias's AI","timestamp":1788016206964}@@explanations sit in closed 'Why' callouts after each task and in the feedback instructions. Answers come from Heim et al. (2024), Egan and Heim (2023), Moon et al. (2025) and Tan (2026), read in lenses 2.2.1 to 2.2.3. When giving feedback, hold the learner to the qualifiers in each prompt: what the stated access and evidence support, and nothing beyond it."++}
tags: [wip]
duration_minutes: 30
---
#### Text
content::
\## 2.2.4 Interpreting cloud evidence

This exercise brings the limits of cloud verification together. For each item,
decide what it supports, what it cannot establish, who controls it, and what
corroboration is still needed.

#### Text
content::{--{"author":"Elias's AI","timestamp":1788016280654}@@ **Interactive exercise:**--}{++{"author":"Elias's AI","timestamp":1788016280654}@@
\## Cloud verification problem set

*30 minutes*

Answer from the assigned readings. Treat every qualifier as part of the question. Select only conclusions supported by the stated access and evidence.
{>>{"author":"Elias's AI","timestamp":1788016280654}@@Native reproduction of++} XLab's {--{"author":"Elias's AI","timestamp":1788016280654}@@`cloud-evidence-drill`--}{++{"author":"Elias's AI","timestamp":1788016280654}@@cloud-evidence-drill widget (nine tasks). Prompts, statements, options, model answers and explanations are copied verbatim from src/lib/verification/data/cloud-evidence-drill.ts and the++} widget {++{"author":"Elias's AI","timestamp":1788016280654}@@component; the source links per task are the widget's own.<<}

\### Task 1 of 9: True or false (3 min)

Determine whether each statement is true or false. Mark all six.

#### Question: Choice
id:: 077edc77-820a-4c61-b0a3-971ca488d5c2
content:: 1. A provider’s billing records can include the hardware configuration requested and the number of hours it was used.
options::
- [x] True
- False
feedback-instructions:: One or two sentences. True. Heim et al. list requested hardware configuration and hours of use as billing-related technical information.

#### Question: Choice
id:: 73c60cd3-a3f8-4809-ae9c-73f82d184e13
content:: 2. Cluster power consumption, by itself, establishes that a customer is training a frontier model.
options::
- True
- [x] False
feedback-instructions:: One or two sentences. False. Power can contribute to workload classification or compute accounting; it does not identify the workload with certainty.

#### Question: Choice
id:: f1464e08-9b14-43db-9ae6-af90a337fbf5
content:: 3. Customer code, data, and hyperparameters are ordinarily collected for cloud billing.
options::
- True
- [x] False
feedback-instructions:: One or two sentences. False. Heim et al. mark workload-level code, data, and hyperparameters as not currently collected for this purpose.

#### Question: Choice
id:: cd2ee96f-be95-439d-a2e1-36954d8384d4
content:: 4. Compute accounting and workload classification answer the same verification question.
options::
- True
- [x] False
feedback-instructions:: One or two sentences. False. Accounting estimates how much compute was used; classification estimates what kind of workload used it.

#### Question: Choice
id:: ad58bf5d-8f83-41ad-8c8d-086a5bec6424
content:: 5. Under the proposed KYC scheme, a provider would monitor compute accumulation and move a customer into KYC before the threshold is crossed.
options::
- [x] True
- False
feedback-instructions:: One or two sentences. True. Egan and Heim propose continuous monitoring so customers approaching the threshold enter KYC before crossing it.

#### Question: Choice
id:: ab40d4c2-3307-4af3-a5c3-f038a55c0e5c
content:: 6. Adding mandatory metrics can narrow a detection gap, but the thresholds still require empirical review as technology changes.
options::
- [x] True
- False
feedback-instructions:: One or two sentences. True. RAND recommends both additional metrics and continuing work on thresholds that can adapt to technological progress.

#### Text
content::
:::callout {title="Review the six explanations (open after you have answered)" tone="neutral" collapse="closed"}
Correct: 1 True; 2 False; 3 False; 4 False; 5 True; 6 True.

1. True. Heim et al. list requested hardware configuration and hours of use as billing-related technical information.
2. False. Power can contribute to workload classification or compute accounting; it does not identify the workload with certainty.
3. False. Heim et al. mark workload-level code, data, and hyperparameters as not currently collected for this purpose.
4. False. Accounting estimates how much compute was used; classification estimates what kind of workload used it.
5. True. Egan and Heim propose continuous monitoring so customers approaching the threshold enter KYC before crossing it.
6. True. RAND recommends both additional metrics and continuing work on thresholds that can adapt to technological progress.

Sources: [Heim et al., §3.2 and Appendix B, Table 4](https://arxiv.org/html/2403.08501v2#S3.SS2); [Heim et al., §§3.3.2–3.3.4](https://arxiv.org/html/2403.08501v2#S3.SS3.SSS2); [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1); [Moon et al., “Cloud Service Provider Monitoring Strategies” and “Finding a Detection Gap”](https://www.rand.org/pubs/research_reports/RRA3686-1.html)
:::

\### Task 2 of 9: Find the odd one out (3 min)

#### Question: Choice
id:: 9297110d-bbb9-4afd-ac8f-037cc3ede05a
content:: One item differs from the other three in evidentiary type. Select it, then state the principle that explains the difference.
options::
- Total power used by an account’s instances
- Maximum GPU cluster size used by one instance
- Total FLOPs across an account’s instances
- [x] Verified beneficial-ownership record
feedback-instructions:: One or two sentences. The beneficial-ownership record concerns who controls the account. The other three are technical metrics of account activity.

#### Question: Open
id:: 476ba00c-21b3-455d-be70-a978bd1640bc
content:: In one sentence, state what the odd item records and what the other three measure.
assessment-instructions:: XLab's model answer: "The beneficial-ownership record concerns who controls the account. The other three are technical metrics of account activity." Full credit when the learner says the beneficial-ownership record is evidence about who controls the account (identity or ownership) and that power, cluster size and FLOPs are technical metrics of account activity. Half credit for naming only one side of the distinction. Zero if the learner picks a technical metric as the odd item or gives no principle.
feedback-instructions:: One or two sentences. Confirm or correct the distinction between an identity record and activity metrics. No generic praise.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The beneficial-ownership record concerns who controls the account. The other three are technical metrics of account activity.

Sources: [Moon et al., “Cloud Service Provider Monitoring Strategies” and “Finding a Detection Gap”](https://www.rand.org/pubs/research_reports/RRA3686-1.html); [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1)
:::

\### Task 3 of 9: Select all that apply (3 min)

#### Question: Choice
id:: 048366a3-8ef9-4e69-913e-cc37fb717c35
content:: A provider has implemented the proposed KYC scheme and retains its ordinary billing and operational records. It ++}has no direct {--{"author":"Elias's AI","timestamp":1788016280654}@@Lens equivalent yet. --}{++{"author":"Elias's AI","timestamp":1788016280654}@@access to customer code or data. Select every category available under those conditions.
options::
- [x] Customer name, billing address, IP addresses, and access times
- [x] Requested hardware configuration and hours of use
- [x] Cluster-level power consumption and network bandwidth between nodes
- [x] Node-level accelerator utilization and memory-bandwidth utilization retained as operational metrics
- [x] Identity, beneficial-ownership, and declared-purpose records required under the proposed KYC scheme
- The customer’s exact code, data, and hyperparameters without a special access protocol
- The contents of the training dataset from billing records alone
- The customer’s actual strategic intent
multi:: true
feedback-instructions:: The first five categories are available under the stated conditions. Code, dataset contents, and actual intent are not. If the learner selected a category that exceeds the stated access, or missed an available one, name it and say which side of the line it falls on. Two or three sentences.

#### Text
content::
:::callout {title="Review the eight categories (open after you have answered)" tone="neutral" collapse="closed"}
The first five categories are available under the stated conditions. Code, dataset contents, and actual intent are not.

- Available: Customer name, billing address, IP addresses, and access times
- Available: Requested hardware configuration and hours of use
- Available: Cluster-level power consumption and network bandwidth between nodes
- Available: Node-level accelerator utilization and memory-bandwidth utilization retained as operational metrics
- Available: Identity, beneficial-ownership, and declared-purpose records required under the proposed KYC scheme
- Not available: The customer’s exact code, data, and hyperparameters without a special access protocol
- Not available: The contents of the training dataset from billing records alone
- Not available: The customer’s actual strategic intent

Sources: [Heim et al., §3.2 and Appendix B, Table 4](https://arxiv.org/html/2403.08501v2#S3.SS2); [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1)
:::

\### Task 4 of 9: Match the pairs (4 min)

Match each item in the first column to the strongest conclusion it can support. Use each conclusion once.

#### Question: Choice
id:: 27b8b7ce-c3c5-4127-8220-1556efd2d5d8
content:: **Hardware configuration, hours of use, and measured utilization**
options::
- [x] An estimate of compute consumed
- The workload is more likely to be large-scale training
- The account is associated with the entity and owners verified under KYC
- A specified workload property is verified without exposing the rest of the code or data
feedback-instructions:: One or two sentences. Billing and utilization records support an estimate of compute consumed (compute accounting), not a workload class, an identity, or a verified property.

#### Question: Choice
id:: 25188806-94e9-4ccd-bb1f-37ea28c7338b
content:: **Sustained accelerator utilization, parallelization-shaped communication, and limited external-network traffic**
options::
- An estimate of compute consumed
- [x] The workload is more likely to be large-scale training
- The account is associated with the entity and owners verified under KYC
- A specified workload property is verified without exposing the rest of the code or data
feedback-instructions:: One or two sentences. This technical pattern supports workload classification: large-scale training is more likely. It does not quantify compute, identify the owner, or verify a property.

#### Question: Choice
id:: d18dc81f-edf4-4580-a138-8f3ef4c457f6
content:: **Verified incorporation, key-personnel, and beneficial-ownership records**
options::
- An estimate of compute consumed
- The workload is more likely to be large-scale training
- [x] The account is associated with the entity and owners verified under KYC
- A specified workload property is verified without exposing the rest of the code or data
feedback-instructions:: One or two sentences. Due-diligence records link the account to a verified entity and its owners; they say nothing about the workload.

#### Question: Choice
id:: b903c82d-a606-4c05-a425-762ce213d1a5
content:: **A trusted-execution-environment proof presented by an attester**
options::
- An estimate of compute consumed
- The workload is more likely to be large-scale training
- The account is associated with the entity and owners verified under KYC
- [x] A specified workload property is verified without exposing the rest of the code or data
feedback-instructions:: One or two sentences. An attestation verifies a specified property of the workload without exposing the remaining code or data; it is not an identity record, a compute estimate, or a classification.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Correct. The four evidence types support four different conclusions; none is interchangeable with another. Distinguish identity, compute quantity, workload class, and a verified workload property.

Sources: [Heim et al., §3.2 and Appendix B, Table 4](https://arxiv.org/html/2403.08501v2#S3.SS2); [Heim et al., §§3.3.2–3.3.4](https://arxiv.org/html/2403.08501v2#S3.SS3.SSS2); [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1)
:::

\### Task 5 of 9: Fill the gaps (4 min)

#### Question: FillBlank
id:: 94906aea-906a-4835-8207-2cc1e5732e18
content:: ++}Complete {++{"author":"Elias's AI","timestamp":1788016280654}@@the verification map by matching each function to its mechanism. Use five terms from the bank. Three terms are not used.

Term bank: KYC; record keeping; workload classification; compute accounting; reporting or escalation; attestation; model evaluation; source-code inspection.

Verify the customer and beneficial owners through {{KYC}}. Retain service-use data through {{record keeping}}. Estimate whether the activity is training through {{workload classification}}. Estimate the amount of compute through {{compute accounting}}. Refer a threshold crossing or high-risk profile through {{reporting or escalation}}.
assessment-instructions:: 20 points per blank. Accept only the term from the bank for each blank (case and minor spelling differences are fine; "reporting" or "escalation" alone counts for the last blank). Attestation, model evaluation and source-code inspection are distractors and earn nothing.
feedback-instructions:: Name any term assigned to the wrong function and state the correct one. Two sentences at most.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Correct: KYC; record keeping; workload classification; compute accounting; reporting or escalation.

Sources: [Heim et al., §3.2 and Appendix B, Table 4](https://arxiv.org/html/2403.08501v2#S3.SS2); [Heim et al., §§3.3.2–3.3.4](https://arxiv.org/html/2403.08501v2#S3.SS3.SSS2); [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1)
:::

\### Task 6 of 9: Put the stages in order (3 min)

#### Question: Ranking
id:: 24c1fc15-57b6-4e25-8e7c-e67cbb890303
content:: Put the six stages of the Egan–Heim scheme in order. The earliest event goes first.
items::
- Provider monitors each customer’s accumulated compute use
- A customer’s projected use approaches the applicable threshold
- Provider verifies the customer entity and beneficial owners
- Provider records the intended use and expected project scope
- Provider continues monitoring for crossings and risk indicators
- A crossing or high-risk profile is reported or subject to required controls
assessment-instructions:: The authored order is the only fully correct order. Give partial credit for correct relative relationships: monitoring must come first, approaching the threshold must precede verification of the entity and owners, recording intended use follows verification, continued monitoring follows both, and reporting or required controls comes last.
feedback-instructions:: Name the most important misplaced stage and why ++}it {++{"author":"Elias's AI","timestamp":1788016280654}@@belongs where it does under the scheme. Two sentences at most.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Correct. Monitor accumulation → approaching threshold → KYC and intended use → continued monitoring → reporting or required controls.

Sources: [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1); [Heim et al., §3.2 and Appendix B, Table 4](https://arxiv.org/html/2403.08501v2#S3.SS2)
:::

\### Task 7 of 9: Name the mechanism (3 min)

#### Question: FillBlank
id:: 15d70ad1-6f46-4a10-a9dc-84a38f3b9579
content:: Match each description to the correct mechanism. Use each mechanism once.

Mechanisms: KYC; record keeping; workload classification; attestation.

Verification of the customer entity and, where required, its beneficial owners: {{KYC}}. Creation and retention of time-stamped service-use records so activity can be reconstructed later: {{record keeping}}. Use of observable technical characteristics to estimate whether a workload belongs to a category such as training or inference: {{workload classification}}. In a confidential-computing protocol, presentation of a verifiable claim about a workload property without revealing the remaining code or data: {{attestation}}.
assessment-instructions:: 25 points per blank. Accept only the named mechanism for each blank (case and minor spelling differences are fine).
feedback-instructions:: Name any mechanism that is wrong and give the correct one. Two sentences at most.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
Correct: KYC verifies identity; record keeping preserves service-use records; classification estimates workload type; attestation presents a verifiable claim.

Sources: [Heim et al., §3.2 and Appendix B, Table 4](https://arxiv.org/html/2403.08501v2#S3.SS2); [Heim et al., §§3.3.2–3.3.4](https://arxiv.org/html/2403.08501v2#S3.SS3.SSS2)
:::

\### Task 8 of 9: Qualify the evidence (4 min)

#### Question: Choice
id:: 2e0edfa6-5532-4c23-9b64-120a361a1675
content:: A provider verifies a customer company and its recorded beneficial owners. The customer declares a rendering workload. It then requests tens of thousands of accelerators and shows sustained accelerator utilization, communication patterns associated with parallelization, and limited traffic to external networks. Select every conclusion supported by these facts.
options::
- [x] The account is associated with the company and owners verified ++}in the {--{"author":"Elias's AI","timestamp":1788016280654}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-evidence). Its surrounding lesson text --}{++{"author":"Elias's AI","timestamp":1788016280654}@@KYC record.
- [x] The technical pattern makes large-scale training more likely than the declared rendering workload.
- [x] The discrepancy between the declaration and the technical pattern supports further review.
- The provider has verified the model architecture and training dataset.
- The provider has established that a prohibited training run occurred.
- The provider now knows why the customer authorized the workload.
multi:: true
feedback-instructions:: The KYC record links the account; the technical pattern supports a training classification and further review. It does not reveal intent, contents, or a violation. If the learner selected a conclusion that exceeds the stated access, or omitted a supported one, name it. Two or three sentences.

#### Text
content::
:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The KYC record links the account; the technical pattern supports a training classification and further review. It does not reveal intent, contents, or a violation.

Sources: [Heim et al., §§3.3.2–3.3.4](https://arxiv.org/html/2403.08501v2#S3.SS3.SSS2); [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1)
:::

\### Task 9 of 9: Choose the permissible inference (3 min)

#### Question: Choice
id:: 9ffcc965-5e91-4ade-ab15-68fd9dc936b3
content:: Six accounts are registered to subsidiaries with the same verified beneficial owner. They run GPU sessions in sequence. Every session remains below a per-account FLOP threshold, but their aggregate compute exceeds it, and large data transfers precede the later sessions. Which response ++}is {--{"author":"Elias's AI","timestamp":1788016280654}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788016280654}@@justified?
options::
- Treat every account as compliant because each remained below the per-account threshold.
- Issue a violation finding because aggregate compute alone proves that the owner conducted prohibited training.
- [x] Open an investigation: test whether the rule aggregates commonly controlled accounts and whether the sessions form one training run.
- Infer the resulting model’s capabilities from aggregate compute alone.
feedback-instructions:: Two or three sentences. The pattern supports investigation. A finding still depends on the rule’s aggregation and coverage provisions and on evidence that the sessions form one training run. If the learner chose another option, say whether it ignores a documented detection gap or treats aggregate compute as proof of facts it cannot establish.++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788016280654}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-evidence)*--}{++{"author":"Elias's AI","timestamp":1788016280654}@@:::callout {title="Why (open after you have answered)" tone="neutral" collapse="closed"}
The pattern supports investigation. A finding still depends on the rule’s aggregation and coverage provisions and on evidence that the sessions form one training run.

Sources: [Moon et al., “Cloud Service Provider Monitoring Strategies” and “Finding a Detection Gap”](https://www.rand.org/pubs/research_reports/RRA3686-1.html); [Moon et al., “Closing Detection Gaps”](https://www.rand.org/pubs/research_reports/RRA3686-1.html); [Egan and Heim, §§2.1–2.2.2](https://arxiv.org/html/2310.13625v1#S2.SS1); [Tan, “Cloud Controls Must Contend With ‘Who’ and ‘What’ They Restrict”](https://carnegieendowment.org/research/2026/05/the-geopolitical-debates-over-controlling-cloud-compute)
:::

\### Problem set complete

Provider-held records can associate an account with a verified identity record, estimate resource use, and support a workload classification. They do not by themselves establish intent, model contents, capability, or a legal violation.

The final policy question remains: which actors and workloads should be covered, at what cost, and across which jurisdictions? Policy scope reading: [Tan, “Cloud Controls Must Contend With ‘Who’ and ‘What’ They Restrict”](https://carnegieendowment.org/research/2026/05/the-geopolitical-debates-over-controlling-cloud-compute).

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
The readings this problem set draws on, Heim et al. (2024), Egan and Heim (2023), Moon et al. (2025) and Tan (2026), are linked in the Sources lines above and read in lenses 2.2.1 to 2.2.3.

XLab. "2.2.4 Interpreting cloud evidence." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-evidence)
*The source lesson this page adapts, including the nine-task problem set.*
:::++}

---
id: 'eaadd7dc-7ba4-4cff-aa7c-6ad4e95f1a50'
title: "Interpreting cloud evidence"
tldr: "Nine short drills on one habit: reading a cloud record for exactly what it proves. A billing line, a KYC file, a power curve: each supports one conclusion and tempts you toward three more. Practice stopping at the first."
summary_for_tutor: "Problem-set lens adapted from XLab lesson 2.2.4. The page is a short intro, the framing line (30 minutes, answer from the assigned readings, treat every qualifier as part of the question), the cloud-evidence-drill widget, one Open follow-up question, a closing statement and the Works cited callout. The widget carries all nine tasks, each checked on its own and marked on the learner's own items: six true or false statements; odd one out among four observables; select every data category available to a KYC-implementing provider without code access; four observables matched to the strongest conclusion each supports; a fill-the-gaps verification map from an eight-term bank; the six stages of the Egan and Heim KYC scheme in order; four mechanisms named from descriptions; a rendering-versus-training case (multi-select); and a permissible-inference question about six sibling accounts under a per-account threshold. XLab's explanations and source links appear in the widget after each check, so the page carries no answer key. The Open question after the widget asks for the odd-one-out principle in one sentence and is the only part graded by the tutor; its rubric is in the segment. Answers come from Heim et al. (2024), Egan and Heim (2023), Moon et al. (2025) and Tan (2026), read in lenses 2.2.1 to 2.2.3. When giving feedback, hold the learner to the qualifiers in each prompt: what the stated access and evidence support, and nothing beyond it."
tags: [wip]
duration_minutes: 40
---
#### Text
content::
\## 2.2.4 Interpreting cloud evidence

This exercise brings the limits of cloud verification together. For each item,
decide what it supports, what it cannot establish, who controls it, and what
corroboration is still needed.

#### Text
content::
\## Cloud verification problem set

*30 minutes*

Answer from the assigned readings. Treat every qualifier as part of the question. Select only conclusions supported by the stated access and evidence.

#### Widget
source:: [[../widgets/cloud-evidence-drill]]
required:: true

#### Question: Open
id:: 476ba00c-21b3-455d-be70-a978bd1640bc
content:: The problem set asked you to find the odd observable among total power used by an account's instances, maximum GPU cluster size used by one instance, total FLOPs across an account's instances, and a verified beneficial-ownership record. In one sentence, state what the odd item records and what the other three measure.
assessment-instructions:: XLab's model answer: "The beneficial-ownership record concerns who controls the account. The other three are technical metrics of account activity." Full credit when the learner says the beneficial-ownership record is evidence about who controls the account (identity or ownership) and that power, cluster size and FLOPs are technical metrics of account activity. Half credit for naming only one side of the distinction. Zero if the learner names a technical metric as the odd item or gives no principle.
feedback-instructions:: One or two sentences. Confirm or correct the distinction between an identity record and activity metrics. No generic praise.

#### Text
content::
\### What the records support

Provider-held records can associate an account with a verified identity record, estimate resource use, and support a workload classification. They do not by themselves establish intent, model contents, capability, or a legal violation.

The final policy question remains: which actors and workloads should be covered, at what cost, and across which jurisdictions? Policy scope reading: [Tan, “Cloud Controls Must Contend With ‘Who’ and ‘What’ They Restrict”](https://carnegieendowment.org/research/2026/05/the-geopolitical-debates-over-controlling-cloud-compute).

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
The readings this problem set draws on, Heim et al. (2024), Egan and Heim (2023), Moon et al. (2025) and Tan (2026), are linked in the Sources lines above and read in lenses 2.2.1 to 2.2.3.

XLab. "2.2.4 Interpreting cloud evidence." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-evidence)
*The source lesson this page adapts, including the nine-task problem set.*
:::

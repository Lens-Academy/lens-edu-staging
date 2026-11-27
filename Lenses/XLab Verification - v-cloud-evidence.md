---
id: 'eaadd7dc-7ba4-4cff-aa7c-6ad4e95f1a50'
title: "Interpreting Cloud Evidence"
tldr: "Nine short drills on one habit: reading a cloud record only for what it proves. A billing line, a KYC file, and a power curve each supports one conclusion and tempts you toward three more. Practice stopping at the first."
summary_for_tutor: "A problem-set lens on the cloud readings. A short intro and a framing line (answer from the assigned readings, treat every qualifier as part of the question) lead into the cloud-evidence-drill widget. The widget is required and carries all nine tasks, each checked on its own and marked on the learner's own items: six true or false statements, an odd one out among four observables, every data category available to a KYC-implementing provider without code access, four observables matched to the strongest conclusion each supports, a fill-the-gaps verification map from an eight-term bank, the six stages of the Egan and Heim KYC scheme in order, four mechanisms named from descriptions, a rendering-versus-training case (multi-select), and a permissible-inference question about six sibling accounts under a per-account threshold. Explanations and source links appear in the widget after each check, so the lens carries no answer key. The open question after the widget asks for the odd-one-out principle in one sentence. It is required and ungraded, with first-answer feedback. Its rubric is in the question's assessment instructions. A closing passage on what the records support and a Works cited callout end the lens. Answers come from Heim et al. (2024) and Egan and Heim (2023), read in Unit 6, and from Moon et al. (2025) and Tan (2026), read in the previous lens. When giving feedback, hold the learner to the qualifiers in each prompt: what the stated access and evidence support, and nothing beyond it."
tags: [wip]
reading_minutes: 20
tutor_minutes: 3
---
#### Text
content::
\## Interpreting cloud evidence

This exercise brings the limits of cloud verification together. For each item,
decide what it supports, what it cannot establish, who controls it, and what
corroboration is still needed.

#### Text
content::
\## Cloud verification problem set

Answer from the assigned readings. Treat every qualifier as part of the question. Select only conclusions supported by the stated access and evidence.

#### Widget
source:: [[../widgets/cloud-evidence-drill]]
required:: true

#### Question: Open
id:: 476ba00c-21b3-455d-be70-a978bd1640bc
force-feedback:: first
content:: The problem set asked you to find the odd observable among total power used by an account's instances, maximum GPU cluster size used by one instance, total FLOPs across an account's instances, and a verified beneficial-ownership record. In one sentence, state what the odd item records and what the other three measure.
feedback-instructions:: This question is not graded. What follows was its rubric: use its elements as what to look for, treat its numbers only as a sign of emphasis, and never mention points or a score to the learner. 50: the odd item, the beneficial-ownership record, records who owns or controls the account (an identity fact). 50: the other three, total power, maximum cluster size and total FLOPs, measure the account's technical activity, how much compute it uses. Give credit for each point whenever the answer shows the idea, in any wording. Score 0 if the answer names one of the technical metrics as the odd item. Model answer, for the feedback, not a grading checklist: "The beneficial-ownership record concerns who controls the account. The other three are technical metrics of account activity." How to reply: One or two sentences. Confirm or correct the distinction between an identity record and activity metrics. No generic praise.

#### Text
content::
\### What the records support

Provider-held records can associate an account with a verified identity record, estimate resource use, and support a workload classification. They do not by themselves establish intent, model contents, capability, or a legal violation.

The final policy question remains: which actors and workloads should be covered, at what cost, and across which jurisdictions? Policy scope reading: [Tan, “Cloud Controls Must Contend With ‘Who’ and ‘What’ They Restrict”](https://carnegieendowment.org/research/2026/05/the-geopolitical-debates-over-controlling-cloud-compute).

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Tan (2026) is linked above. The other readings this problem set draws on are taken from earlier pages on this topic: Heim et al. (2024) from [[../Lenses/XLab Verification - v-cloud|provider records]] and Egan and Heim (2023) from [[../Lenses/XLab Verification - v-cloud-customer-identification|customer identification]], both in Unit 6, and Moon et al. (2025) from [[../Lenses/XLab Verification - v-cloud-detection-gaps|detection gaps]] in this unit.

XLab. "2.2.4 Interpreting Cloud Evidence." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/cloud-evidence)
*The source lesson this page adapts, including the nine-task problem set.*
:::

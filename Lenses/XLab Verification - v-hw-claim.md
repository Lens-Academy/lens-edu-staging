---
id: '5cfb50dd-3ac7-4580-8861-8fb9253ea6f1'
title: "Start with the claim, not the mechanism"
tldr: "A chip can truthfully report six things and the treaty can still be broken. Learn to separate the policy goal, the legal rule, and the narrow proposition a device actually tests, then ask three questions of any evidence: is it authentic, is it correct, is it complete?"
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. Short reading: the working policy goal, legal rule and verification claim used throughout section 2.1; six narrow propositions hardware can test; authenticity, correctness, completeness. Ends with one open question (initial claim map) where the learner completes three sentences about the opening-puzzle artifact from lesson 2.1. Push the learner to keep the three sentences distinct and to name what remains outside the claim."
tags: []
duration_minutes: 10
---
#### Text
content::
\### 2.1.1 Start with the claim, not the mechanism

Consider the policy objective used throughout this section.

- **Policy goal**: prevent a strategically dangerous training run during an emergency pause.
- **Legal rule**: no covered party may conduct an unlicensed training run above threshold T during the pause. Inference and approved safety evaluations remain permitted.
- **Verification claim**: no covered accelerator or covered combination of accelerators performed unlicensed training whose counted operations exceeded T during the reporting period.

The hardware does not test the policy goal directly. It may test narrower propositions that support the verification claim.

For example:

- A particular device possesses a valid credential;
- Its low-level software matched an approved reference value at a specified time;
- A protected counter recorded a specified quantity;
- A classifier labeled a protected telemetry trace as training;
- A valid license token authorized a bounded quantity of use;
- A sampled segment of a declared training transcript reproduced an expected checkpoint.

Each proposition can be true while the treaty is still violated. A registered device may run prohibited work after attestation. A counter may omit activity on unregistered hardware. A classifier may correctly label every trace it sees while an operator bypasses the telemetry path. A license may be valid but issued by the wrong authority.

\#### Authenticity, correctness, and completeness

Three questions recur throughout hardware verification.

**Authenticity**: Did this evidence come from the claimed device, component, or authority, and is it fresh enough to use?

**Correctness**: Does the declared or observed activity satisfy the rule?

**Completeness**: Did the evidence cover all relevant devices, sites, time periods, and activities, including activity the operator did not declare?

Hardware-rooted cryptography is often strongest on authenticity. Carefully designed measurement can improve correctness. Completeness usually requires evidence beyond the device itself.

\#### Notebook: initial claim map

The opening puzzle is the attestation-token scenario from [[../Lenses/XLab Verification - v-hw-attestation|2.1 Hardware]].

#### Question: Open
id:: aff4f378-14ef-4cd4-b12d-249c4c66644e
content:: Complete three sentences for the opening puzzle:

- The artifact directly supports…
- It could support… if…
- It does not support…
assessment-instructions:: Score out of 100. The artifact: during a pause, a laboratory sends the verification authority a valid attestation token from each accelerator in its declared cluster and says the tokens prove the cluster complied. 35: the first sentence (directly supports) keeps to authenticity-type claims: these are genuine covered devices, and their credentials, certificates and approved configuration (measured state) were valid and fresh when checked. 30: the second sentence (could support … if …) names a claim the tokens could support only if the system had been designed to measure it, and says what would have had to be measured, for example inference rather than training if the token carried a protected workload classification, or compute below the threshold if it carried a protected counter. 35: the third sentence (does not support) names claims beyond the tokens, at least two of: the cluster's cumulative training compute over the whole period, what workload actually ran, the cluster's topology, whether unregistered hardware ran a separate prohibited workload, and whether the treaty authority can suspend the devices. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the first sentence says the tokens directly show compliance, such as no prohibited training or compute below the threshold. Model answer, for the feedback, not a grading checklist: "The artifact directly supports that these are genuine covered devices whose certificates and approved configurations were valid when the evidence was checked. It could support that the devices ran inference rather than prohibited training, or that each device's counted compute stayed below a limit, if the system had been designed to measure and sign that workload classification or counter. It does not support that the cluster's cumulative training compute stayed below the threshold over the whole period, that the devices were connected in the declared topology, that no unregistered accelerators ran a separate prohibited workload, or that the treaty authority can suspend the devices: those need evidence beyond the tokens."
feedback-instructions:: This is an XLab writing or reflection exercise. Identify one strong point and one important gap, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
XLab. "2.1.1 Start with the claim, not the mechanism." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-claim)
*The source lesson this page adapts.*
:::

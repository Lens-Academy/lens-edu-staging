---
id: '5cfb50dd-3ac7-4580-8861-8fb9253ea6f1'
title: "2.1.1 Start with the claim, not the mechanism"
tldr: "A chip can truthfully report six things and the treaty can still be broken. Learn to separate the policy goal, the legal rule, and the narrow proposition a device actually tests, then ask three questions of any evidence: is it authentic, is it correct, is it complete?"
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. Short reading: the working policy goal, legal rule and verification claim used throughout section 2.1; six narrow propositions hardware can test; authenticity, correctness, completeness. Ends with one open question (initial claim map) where the learner completes three sentences about the opening-puzzle artifact from lesson 2.1. Push the learner to keep the three sentences distinct and to name what remains outside the claim."
tags: [wip]
duration_minutes: 5
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

{++{"author":"Elias's AI","timestamp":1788015929329}@@\#### Notebook: initial claim map

The opening puzzle is the attestation-token scenario from [[../Lenses/XLab Verification - v-hw-attestation|2.1 Hardware]].

++}#### Question: Open
id:: aff4f378-14ef-4cd4-b12d-249c4c66644e
content:: Complete three sentences for the opening puzzle:

- The artifact directly supports…
- It could support… if…
- It does not support…

#### Text
content::
*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-claim)*

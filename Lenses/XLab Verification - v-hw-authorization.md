---
id: 'e39bd85f-e2bf-4039-a3f1-f8f5291892b6'
title: "Authorization, licensing, and control"
tldr: "An off-switch for someone else's compute is only as acceptable as the answer to who holds the key, what happens when the license server is down, and who reverses a mistake. Assemble a full authorization chain from twelve components and find which ones fail together."
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. Reading on offline licensing, the twelve questions a policy designer must answer, Petrie's 2024 firmware-based design (author estimate, not deployment evidence), and why control authority is part of the mechanism. Ends with the build-the-authorization-chain open question. Check that the learner distinguishes components that measure from components that only authenticate, and names the common-mode failure if the manufacturer's root key is compromised. A license widget sits after the offline licensing excerpt: the learner edits or re-signs the four fields of the example license from the paper and sees which of the chip's three defenses rejects it, in the paper's own words."
tags: []
duration_minutes: 25
---
#### Text
content::
\### 2.1.5 Authorization, licensing, and control

A monitor produces evidence. A control mechanism changes what the machine can do. A complete policy still needs an authority that decides when control is justified.

One proposed family of controls is offline licensing. The device performs only a bounded quantity or type of operation when it holds a valid authorization token. The token may encode a compute allowance, time window, location, workload condition, or other policy. A protected meter reduces the allowance as work occurs. A throttling or disabling mechanism responds when the allowance expires.

A complete authorization chain is:

> legal rule → license criteria → issuer → authenticated device and state → permitted operation → meter or expiration → suspension or revocation → appeal or override → renewal or termination

\#### Questions a policy designer must answer

- Who issues the authorization: one government, both parties, a multiparty authority, or another institution?
- Which key or combination of keys is sufficient?
- Can a chip vendor or one state disable lawful activity unilaterally?
- What happens when the authorization service is unavailable?
- Does the system fail open or fail closed?
- Can emergency suspension occur before full adjudication?
- Who can reverse a mistaken suspension?
- What happens after key compromise or erroneous revocation?
- Can the mechanism reach existing hardware through firmware, or does it require redesigned chips?
- How are exceptional uses handled during emergencies?
- Who bears the cost of false denials, downtime, replacement, and appeal?
- What prevents the control infrastructure from becoming an espionage, sabotage, or coercion channel?

James Petrie’s 2024 firmware-based offline-licensing design is a useful proposal to analyze. It argues that some existing accelerators might support a minimal design through a firmware update if they already contain relevant security features. The proposed timeline is an author estimate, not deployment evidence. The paper also states that physical attacks remain a concern without additional hardware changes. No publicly documented, treaty-grade offline-licensing regime for frontier AI compute is operating as of August 2026.

:::callout {title="Source" tone="neutral" collapse="closed"}
J. Petrie, *Near-Term Enforcement of AI Chip Export Controls Using a Firmware-Based Design for Offline Licensing*, [arXiv:2404.18308](https://arxiv.org/abs/2404.18308), 2024.
:::

\#### Control authority is part of the mechanism

A technically sound off-switch can be politically unacceptable when its control structure is vague. An international agreement might require:

- Split or threshold authorization, so no single party controls the switch;
- Narrow, auditable conditions for suspension;
- Logged and reviewable decisions;
- Emergency action followed by time-bounded review;
- A safe recovery path after false positives;
- Independent tests for denial-of-service and abuse;
- A plan for lawful legacy hardware and nonparticipating vendors.

The choice is not simply “control or no control.” It is a distribution of authority, risk, and failure.

Read how offline licensing could work and which technical and policy questions remain open.

#### Article
source:: [[../articles/ogara-hardware-enabled-mechanisms-for-verifying-responsible-ai-development]]
from:: ### 2.5 Offline Licensing ^2-5-offline-licensing
to:: In certain scenarios, AI developers or governments may wish to implement licensing regimes for AI accelerators. For example, when exporting AI chips to countries with a heightened risk of theft of AI chips or onward re-export towards export-controlled countries, it may be desirable to introduce licenses that limit the benefits of such activities by restricting the chip’s functionality if it is stolen or diverted. More generally, this licensing mechanism would prevent the unlicensed use of AI chips, providing a flexible mechanism to monitor and control AI development and deployment in cases where the risks warrant such a scheme and where it is authorized by national regulation or corporate policies. Licenses could be implemented in the form of cryptographic keys that act as temporary passwords, unlocking a chip’s capacity to perform a specified amount of computational work, such as a set number of operations or memory transfers. Once this computational work has been performed, the license would expire, and the chip would shut down or operate only at a reduced capacity. The chip operator would then need to acquire a new license from a license provider to resume full use of the chip.

#### Text
content::
An example license carries four fields, and the chip that reads it holds three defenses. Change any field below, sign it yourself if you like, then present it to the chip and see which defense catches you.

#### Widget
source:: [[../widgets/ogara-license-check]]

#### Article
source:: [[../articles/ogara-hardware-enabled-mechanisms-for-verifying-responsible-ai-development]]
from:: #### 2.5.4 Open research questions ^2-5-4-open
to:: How should licenses be issued? This is primarily a policy question, not a technical question. However, technical researchers could enable more desirable policy choices, such as designing systems for multi-party provision of licenses that enable multilateral AI governance.

#### Text
content::
\#### Activity: build the authorization chain

#### Question: Open
id:: 2d7cde29-94c1-4125-bc0f-c6a1b60e6683
content:: Assemble an end-to-end system for the working rule (no unlicensed training above threshold T) from the following components: device identity, attested firmware, protected counter, training classifier, signed record, cross-device aggregation, license token, revocation list, regulator, international notification, inspection trigger, and independent power measurement.

Then answer: Which component measures the prohibited activity? Which only authenticates another component? Who decides the threshold was crossed? Which component can stop the activity? What detects an unregistered cluster? Which controls fail together if the manufacturer’s root key is compromised?
assessment-instructions:: Score out of 100. The working rule prohibits unlicensed training above a compute threshold T while permitting inference and approved safety evaluations. 25: an end-to-end system that uses the listed components in a sensible order, from authenticated devices and measurement through records and aggregation to a decision and a response. 75: the six questions, 10: what measures the prohibited activity: the protected counter (how much compute) and the training classifier (whether it is training); 10: what only authenticates another component: device identity, attested firmware and the signed record; 10: who decides the threshold was crossed: the regulator, an institution, not the chip; 10: what can stop the activity: the license token together with the revocation list; 15: what detects an unregistered cluster: independent power measurement, with the inspection trigger and international notification, because on-chip components only see registered devices; 20: what fails together if the manufacturer's root key is compromised: device identity, attested firmware, the protected counter, the signed record and license enforcement, which all rest on that key. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Device identity and attested firmware establish that each chip is genuine and runs approved code. On each chip, the protected counter meters compute and the training classifier labels the workload as training or not; together they measure the prohibited activity. The results go into a signed record, and cross-device aggregation adds records across all chips in a run, since a run spread over many chips can stay under T on each one. The regulator, not the chip, reviews the aggregate and decides whether training crossed T without a license. The license token lets chips operate within an allowance, and the revocation list lets the regulator withdraw it, so these two can stop the activity. Device identity, attested firmware and the signed record only authenticate: they say where the data came from, not what happened. None of the on-chip parts can see an unregistered cluster; independent power measurement can, and a finding there leads to the inspection trigger and international notification. If the manufacturer's root key is compromised, device identity, firmware attestation, the counter's signed readings, the signed records and the chip's enforcement of license tokens all fail together, because each trusts that key; only the regulator's own judgement and the off-chip power measurement survive."
feedback-instructions:: This is an XLab writing or reflection exercise. Identify one strong point and one important gap, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Petrie, James. "Near-Term Enforcement of AI Chip Export Controls Using a Firmware-Based Design for Offline Licensing." *arXiv*, Apr. 2024. [arxiv.org](https://arxiv.org/abs/2404.18308)
*A design for firmware-based offline licensing that would disable AI chips lacking a regulatory license, as a near-term export-control enforcement mechanism.*

XLab. "2.1.5 Authorization, licensing, and control." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-authorization)
*The source lesson this page adapts.*
:::

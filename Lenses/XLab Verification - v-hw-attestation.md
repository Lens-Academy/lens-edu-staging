---
id: 'b481c94e-9a3a-4118-b4e9-7bd13a1c488d'
title: "2.1 Hardware"
tldr: "A lab hands you 20,000 valid cryptographic tokens and says they prove the cluster complied with the pause. Before reading anything, judge seven conclusions those tokens might support. You will grade your own answers at the end of the hardware section."
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. Opening lens of section 2.1. The ClaimLedger puzzle is seven ungraded choice questions (supported / possibly supported if the system was designed to measure it / unsupported by attestation alone); do not give the answers, they are revealed in lesson 2.1.8. Then the central question, the core-section objectives, the function map table, the repeated method, and the core source packet. If the learner asks about a claim, ask what the token actually measured rather than telling them the verdict."
tags: [wip]
duration_minutes: 5
---
#### Text
content::
\### 2.1 Hardware

\#### Before you begin

**Core time:** 165–180 minutes, split into two sessions.
{--{"author":"Elias's AI","timestamp":1788015904638}@@**[Optional]--}{++{"author":"Elias's AI","timestamp":1788015904638}@@**Optional:++} Technical {--{"author":"Elias's AI","timestamp":1788015904638}@@extension:**--}{++{"author":"Elias's AI","timestamp":1788015904638}@@extension**++} 35–45 minutes.

During a three-month AI pause, a laboratory sends the verification authority a valid cryptographic statement from each of the 20,000 accelerators in its declared cluster. The laboratory says the tokens prove that the cluster complied.

Before reading further, classify each conclusion as **supported**, **possibly supported if the system was designed to measure it**, or **unsupported by attestation alone**.

{++{"author":"Elias's AI","timestamp":1788015904638}@@Proposed conclusion:

#### Question: Choice
id:: 6aff61bf-8c5d-4188-9c8f-9a6049a74a2a
content:: These are genuine covered devices.
options::
- Supported
- Possibly supported if the system was designed to measure it
- Unsupported by attestation alone

#### Question: Choice
id:: 45dad21d-3558-436f-9e49-171462974ece
content:: Their certificates and approved configurations were valid when the evidence was checked.
options::
- Supported
- Possibly supported if the system was designed to measure it
- Unsupported by attestation alone

#### Question: Choice
id:: 188fe444-a629-4950-b799-a00b72dcfca5
content:: The devices were connected in the declared cluster topology.
options::
- Supported
- Possibly supported if the system was designed to measure it
- Unsupported by attestation alone

#### Question: Choice
id:: 6e4a14c9-e6fa-4768-96a8-229d436e1d37
content:: They performed inference rather than prohibited training.
options::
- Supported
- Possibly supported if the system was designed to measure it
- Unsupported by attestation alone

#### Question: Choice
id:: 9c7cd240-2fe5-4fc5-a7aa-ad3b927cf2a4
content:: Their cumulative training compute remained below the treaty threshold.
options::
- Supported
- Possibly supported if the system was designed to measure it
- Unsupported by attestation alone

++}#### {--{"author":"Elias's AI","timestamp":1788015904638}@@Text--}{++{"author":"Elias's AI","timestamp":1788015904638}@@Question: Choice++}
{++{"author":"Elias's AI","timestamp":1788015904638}@@id:: f59b326b-8d99-4180-9aad-eb23fa74e4a1
++}content:: {--{"author":"Elias's AI","timestamp":1788015904638}@@**Import gap:** XLab ClaimLedger component --}{++{"author":"Elias's AI","timestamp":1788015904638}@@No unregistered accelerators ran a separate prohibited workload.
options::
- Supported
- Possibly supported if the system was designed to measure it
- Unsupported by attestation alone

#### Question: Choice
id:: 021cf8df-687e-4fd4-be59-ff5341d41bd9
content:: The treaty authority can suspend the devices.
options::
- Supported
- Possibly supported if the system was designed to measure it
- Unsupported by attestation alone
{>>{"author":"Elias's AI","timestamp":1788015904638}@@XLab's ClaimLedger ++}has no {--{"author":"Elias's AI","timestamp":1788015904638}@@clean Lens equivalent. Use--}{++{"author":"Elias's AI","timestamp":1788015904638}@@answer key in either mode;++} the {--{"author":"Elias's AI","timestamp":1788015904638}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-attestation) for this element.--}{++{"author":"Elias's AI","timestamp":1788015904638}@@resolution is the closing prose of lesson 2.1.8. Left ungraded on purpose.<<}++}

#### Text
content::
Keep your answers. You will return to them at the end of the section.

\#### The central question

A signed statement can be authentic and still be too narrow, stale, incomplete, or based on a compromised measurement. Hardware becomes useful for verification only when the whole chain is specified: the rule, the measurement, the evidence, the trust assumptions, the decision authority, and the response.

\#### What you will be able to do

{--{"author":"Elias's AI","timestamp":1788015904638}@@\## Learning objectives

--}{++{"author":"Elias's AI","timestamp":1788015904638}@@:::callout {title="By the end of the core section, you will be able to:" tone="blue"}
++}1. **Bound a hardware claim.** Distinguish what a mechanism identifies, attests, measures, classifies, restricts, or reconstructs, then state what remains outside the claim.
2. **Trace the trust and authority chain.** Name who measures, signs, defines acceptable state, updates, revokes, appraises, decides, and enforces.
3. **Invert the threat model.** Reassess the same mechanism when the operator is a cloud customer, a laboratory with physical control, or a state-backed owner.
4. **Compare trust architectures.** Evaluate on-chip, off-chip, and hybrid designs for the same policy claim.
5. **Recommend a bounded role.** State what hardware should carry in a layered regime, what it should not carry, which independent evidence must corroborate it, and what new evidence would change your recommendation.{++{"author":"Elias's AI","timestamp":1788015904638}@@
:::
{>>{"author":"Elias's AI","timestamp":1788015904638}@@XLab's Objectives block here has scope="the core section", so the rendered lead sentence is "By the end of the core section, you will be able to:" rather than "this module".<<}++}

\#### A map of the section

Hardware proposals serve several different functions. These functions are not a ladder from weak to strong. A mechanism may perform one function well and contribute little to another.

| Function | Question for the verifier |
| --- | --- |
| **Identify and account for hardware** | Which device is this? Is it covered and registered? Where is it supposed to be? |
| **Attest state and configuration** | What hardware, firmware, driver, or security state is present now? |
| **Establish location and topology** | Where is the device, and how is it connected to other devices? |
| **Measure and classify use** | How much compute occurred, and was the workload training, inference, evaluation, or something else? |
| **Authorize or restrict use** | Was the activity permitted? Who can issue, suspend, revoke, appeal, or override authorization? |
| **Reconstruct a declared run** | Did the declared training process plausibly produce the submitted checkpoints or model? |

The rest of this section uses one repeated method:

**State the claim. Trace the measurement and trust chain. Name the adversary. Price the mechanism. Bound the conclusion. Find the remaining hole.**

{--{"author":"Elias's AI","timestamp":1788015907067}@@\##--}{++{"author":"Elias's AI","timestamp":1788015907067}@@\####++} Core source packet

{--{"author":"Elias's AI","timestamp":1788015907067}@@\#### Core source packet

**Author note**

--}{++{"author":"Elias's AI","timestamp":1788015907067}@@:::callout {title="Author note" tone="neutral"}
++}The required reading should be embedded at the point of use rather than assigned as one block.{++{"author":"Elias's AI","timestamp":1788015907067}@@
:::++}

1. **IETF, RFC 9334, Remote ATtestation procedureS Architecture.** Read the roles and trust-model excerpts.
2. **NVIDIA Attestation Quick Start Guide.** Inspect the architecture diagram, selected token claims, reference measurements, revocation roles, and the current multi-GPU limitation.
3. **O’Gara et al., Hardware-Enabled Mechanisms for Verifying Responsible AI Development.** Read the mechanism map and selected open questions on accounting, workload classification, location, configuration, and licensing.
4. **Rahman and Tajdari, Detecting Hidden ML Training With Zero-Overhead Telemetry.** Read the abstract, one adversarial-results table, the required hardware assumptions, and the limitations.
5. **Baker et al., Verifying International Agreements on AI: Six Layers of Verification.** Read the on-chip, off-chip digital, and off-chip analog comparison.

{--{"author":"Elias's AI","timestamp":1788015923669}@@**Src**--}{++{"author":"Elias's AI","timestamp":1788015923669}@@:::callout {title="Sources" tone="neutral" collapse="closed"}++}
H. Birkholz et al., [“Remote ATtestation procedureS (RATS) Architecture”](https://www.rfc-editor.org/rfc/rfc9334.html), IETF RFC 9334, January 2023. NVIDIA, “Architecture Overview,” [*Attestation Quick Start Guide*](https://docs.nvidia.com/attestation/quick-start-guide/latest/architecture.html), documentation current August 1, 2026 — first-party implementation documentation, not an independent adversarial evaluation. T. O’Gara et al., “Hardware-Enabled Mechanisms for Verifying Responsible AI Development,” [arXiv:2505.03742](https://arxiv.org/abs/2505.03742), 2025. M. S. Rahman and M. Tajdari, “Detecting Hidden ML Training With Zero-Overhead Telemetry,” [arXiv:2606.19262](https://arxiv.org/abs/2606.19262), June 2026 — a preprint, presented as a component demonstration. Baker et al., “Verifying International Agreements on AI: Six Layers of Verification,” [arXiv:2507.15916](https://arxiv.org/abs/2507.15916), 2026.{++{"author":"Elias's AI","timestamp":1788015923669}@@
:::

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Birkholz, Henk, et al. "Remote ATtestation ProcedureS (RATS) Architecture." *RFC 9334*, RFC Editor, Jan. 2023. [rfc-editor.org](https://www.rfc-editor.org/rfc/rfc9334.html)
*The IETF architecture for remote attestation: the standard vocabulary of attesters, verifiers, and relying parties the hardware lessons use.*

NVIDIA Corporation. "Architecture Overview." *NVIDIA Attestation Suite Documentation*, NVIDIA. [docs.nvidia.com](https://docs.nvidia.com/attestation/quick-start-guide/latest/architecture.html)
*NVIDIA's documentation of its attestation architecture: how clients, cloud services, and GPU hardware form a verifiable chain of trust.*

O'Gara, Aidan, Gabriel Kulp, Will Hodgkins, et al. "Hardware-Enabled Mechanisms for Verifying Responsible AI Development." *arXiv*, Apr. 2025. [arxiv.org](https://arxiv.org/abs/2505.03742)
*A study of hardware-enabled mechanisms for verifiable reporting of AI training activity: compute usage, cluster configuration, and workload claims.*

Rahman, Robi, and Sabiha Tajdari. "Detecting Hidden ML Training With Zero-Overhead Telemetry." *arXiv*, June 2026. [arxiv.org](https://arxiv.org/abs/2606.19262)
*A study classifying GPU workloads from privacy-preserving telemetry, reporting 98.2 percent accuracy at spotting concealed training runs.*

Baker, Mauricio, Gabriel Kulp, Oliver Marks, et al. "Verifying International Agreements on AI: Six Layers of Verification for Rules on Large-Scale AI Development and Deployment." *arXiv*, July 2025. [arxiv.org](https://arxiv.org/abs/2507.15916)
*A six-layer verification framework whose personnel-based layers map which workers can observe different violations and why disclosures still need independent confirmation.*++}

{--{"author":"Elias's AI","timestamp":1788015923669}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-attestation)*--}{++{"author":"Elias's AI","timestamp":1788015923669}@@XLab. "2.1 Hardware." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-attestation)
*The source lesson this page adapts, including the opening claim ledger.*
:::++}

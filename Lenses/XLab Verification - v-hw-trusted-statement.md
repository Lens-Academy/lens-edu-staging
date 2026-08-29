---
id: '22f3ba95-64cf-4248-9d3a-a83975f4255b'
title: "2.1.2 From a chip to a trusted statement"
tldr: "A valid signature proves that a key signed some claims, nothing more. Follow the chain from measurement component to treaty response, learn the minimum attestation vocabulary, see what NVIDIA's shipping GPU attestation does and does not attest, and then dissect one trust chain yourself."
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. Reading on RATS roles (Attester, Verifier, Relying Party), the minimum vocabulary, NVIDIA's deployed attestation chain and its multi-GPU limits, what a signature does not establish, and how the adversary profile changes assurance. Ends with the trust-chain autopsy open question (nine items). XLab says a token or diagram is supplied but none is in the source; let the learner use NVIDIA's architecture overview linked in the lens. Grade for naming a concrete owner of each link and one common-mode failure."
tags: [wip]
duration_minutes: 5
---
#### Text
content::
\### 2.1.2 From a chip to a trusted statement

Remote attestation is often described as a chip proving its state. That description hides several actors and several separate judgments.

The IETF’s Remote ATtestation procedureS architecture distinguishes three roles: an **Attester** produces evidence, a **Verifier** appraises that evidence against reference values and policy, and a **Relying Party** decides what to do with the result. This separation matters. The component that checks a signature need not be the institution that decides compliance, and neither automatically has authority to impose a consequence.

{--{"author":"Elias's AI","timestamp":1788015942196}@@**Src**--}{++{"author":"Elias's AI","timestamp":1788015942196}@@:::callout {title="Source" tone="neutral" collapse="closed"}++}
H. Birkholz et al., [“Remote ATtestation procedureS (RATS) Architecture”](https://www.rfc-editor.org/rfc/rfc9334.html) — IETF RFC 9334, January 2023.{++{"author":"Elias's AI","timestamp":1788015942196}@@
:::++}

\#### The minimum vocabulary

**Hardware-rooted identity.** A device uses a cryptographic key and certificate, or another hardware-bound credential, to authenticate evidence. Some designs derive secrets from physical properties such as a physically unclonable function. Others provision or generate keys during manufacturing. “Hardware-rooted” does not mean literally unforgeable. It means that impersonation should require defeating a defined hardware and key-management boundary.

**Root of trust.** The component or assumption at the bottom of the chain. Other claims inherit its integrity. A root of trust may protect key use, measure boot state, verify firmware, or isolate code. A flaw at this layer can invalidate many apparently separate controls at once.

**Secure boot.** A mechanism that restricts low-level code to versions authorized by a signing policy before execution.

**Measured boot.** A mechanism that records cryptographic measurements of code or configuration as it starts. A verifier can later compare those measurements with expected values.

**Attestation evidence.** Signed claims or measurements about a device and its state. The evidence must normally include a freshness mechanism, such as a nonce or trusted time, so an old compliant statement cannot be replayed.

**Reference values and endorsements.** Information used to decide what measurements should be expected and which keys or device properties should be trusted.

**Revocation.** The ability to stop trusting a compromised key, certificate, firmware version, device, reference value, or authority.

**Appraisal policy.** The rule that turns measured facts into a result such as “acceptable for this workload.” This is a policy judgment, not a property of the signature itself.

{--{"author":"Elias's AI","timestamp":1788015944438}@@\## A deployed primitive

--}\#### A deployed primitive: current NVIDIA GPU attestation

Current NVIDIA documentation describes an operational attestation chain for supported GPUs. Evidence is collected from the GPU, checked against signed Reference Integrity Measurements, evaluated locally or by NVIDIA’s Remote Attestation Service, and checked against certificate-revocation information. This is a useful deployed primitive because it makes the trust chain concrete.

It also shows why implementation details matter. NVIDIA’s Blackwell multi-GPU documentation, updated August 1, 2026, states that each GPU is attested independently and that the process does **not** attest topology or switches. Supported Hopper Protected PCIe configurations can include additional multi-GPU and NVSwitch checks. A general statement such as “GPU attestation proves the cluster configuration” is therefore false. The answer depends on the product, configuration, evidence fields, and appraisal policy.

{--{"author":"Elias's AI","timestamp":1788015950223}@@**Src**--}{++{"author":"Elias's AI","timestamp":1788015950223}@@:::callout {title="Sources" tone="neutral" collapse="closed"}++}
NVIDIA, “Architecture Overview,” [*Attestation Quick Start Guide*](https://docs.nvidia.com/attestation/quick-start-guide/latest/architecture.html), current August 1, 2026; [“Blackwell Multi-GPU Attestation Example”](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/blackwell_multi_gpu.html), updated August 1, 2026; [“Hopper Multi-GPU (PPCIE) Attestation Example”](https://docs.nvidia.com/attestation/quick-start-guide/latest/attestation-examples/hopper_multi_gpu.html), current August 2026. First-party implementation documentation, not an independent adversarial evaluation.{++{"author":"Elias's AI","timestamp":1788015950223}@@
:::++}

A simplified chain looks like this:

> device and measurement component → device evidence and nonce → signing key and certificate chain → reference values and revocation data → verifier appraisal → relying-party decision → regulator or treaty response

For each link, ask:

- Who controls it?
- What can that actor falsify, suppress, delay, revoke, or refuse?
- Is cooperation legally required, technically required, or merely convenient?
- What independent evidence checks the link?
- What happens when the link fails?

\#### What a signature does and does not do

A valid signature supports a statement such as “the holder of this trusted key signed these claims.” It does not by itself establish that:

- The measurement code observed the right property;
- The measurement was complete;
- The reference value was correct;
- The evidence described the current state rather than a replayed state;
- The device remained compliant after the measurement;
- The device occupied the declared location or topology;
- No other device or workload existed;
- An institution may lawfully act on the result.

Cryptography can faithfully transmit a false or insufficient measurement. The value of attestation therefore depends on the measurement boundary and the governance of keys, reference values, updates, revocation, and decisions.

\#### The adversary changes the assurance

| Prover profile | What becomes easier for the prover | What remains comparatively stronger |
| --- | --- | --- |
| **Cloud customer without physical access** | Manipulating user software, workload behavior, labels, accounts, and timing | Provider-controlled hardware, physical security, and manufacturer-backed attestation may be difficult for the customer to alter |
| **Laboratory controlling its servers** | Physical access, administrative control, optional security modes, peripherals, network routes, updates, and logging | Independent manufacturer services or separately installed sensors may still impose constraints, but must be tested against owner control |
| **State-backed owner** | Supplier pressure, substitute hardware, expensive physical attacks, coercion of domestic firms, manipulation of inspections, and long preparation | Assurance may require mutually governed keys, externally installed monitoring, supply-chain reconciliation, destructive sampling, and evidence outside the device |

The same product can be strong against a remote tenant and weak against an owner with physical access. “Secure” is not a mechanism property without an adversary.

\#### Activity: trust-chain autopsy

Take an attestation token or architecture diagram supplied with this section. Record:

1. The exact claim;
2. The root or roots of trust;
3. The measurement component;
4. The key and reference-value authorities;
5. Update and revocation authority;
6. The verifier and relying party;
7. The strongest relevant adversary;
8. One common-mode failure;
9. One independent corroborating source.

*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-trusted-statement)*

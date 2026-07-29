---
id: '1653827f-4f26-4b43-abb5-be7fb0b0cb1f'
title: "Flexible Hardware-Enabled Guarantees (flexHEG)"
tldr: "A guarantee processor inside a tamper-resistant enclosure, open-source so both sides can check it isn't a backdoor. Prove what your chips did without revealing what they did it to."
summary_for_tutor: "Petrie, Aarne, Ammann and Dalrymple's flexHEG report, Part I: Overview (commissioned by ARIA) — the hardware mechanism reading. FlexHEGs integrate with AI accelerators to enable trustworthy, privacy-preserving verification and enforcement of claims about AI development. Two components: an AUDITABLE GUARANTEE PROCESSOR monitoring how the accelerator is used and enforcing agreed rules, and a SECURE ENCLOSURE providing physical tamper resistance so the owner cannot bypass, spoof or remove the processor. The division of labour is logic versus physics: attestation from a component its owner could freely tamper with carries no information, so the enclosure is what gives the processor's reports meaning. Fully open source with flexible, updateable verification capabilities — flexibility because the rules a regime enforces will change (so baking one policy into silicon guarantees obsolescence), open-source because the verified party must be convinced the device is not a backdoor while the verifying party must be convinced it cannot be subverted. Enables privacy-preserving model evaluations, controlled deployment, compute limits during training, and automated safety-protocol enforcement. The load-bearing and acknowledged-difficult assumption: tamper resistance must hold against an adversary who physically possesses, powers and operates the device indefinitely. Also requires manufacturer and supply-chain cooperation, covering only chips produced under the regime and leaving legacy hardware outside — so it is a layer in a redundant regime, not a solution. Report closes on the argument that frameworks established early shape development trajectories for decades."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

Module 2 concluded that access can substitute for missing technology, but that access is politically expensive. This module is about the mechanisms that would make verification *cheap* — starting with the most discussed hardware proposal in the field.

A flexHEG has two parts, and the relationship between them is the whole idea:

> An **auditable guarantee processor** watches how the accelerator is used, enforces the agreed rules, and produces attestations. A **secure enclosure** wraps it in physical tamper resistance.

Why both? Because an attestation from a component its owner can freely open and reprogram tells you nothing. The processor is the logic; the enclosure is what makes the logic's word worth anything.

Two design choices to watch for, each answering a specific failure:

> **Flexible and updateable** — the thresholds and rules a regime wants will change, so hardware that enforces one fixed policy is hardware that is wrong in three years.

> **Fully open source** — the operator must believe the box is not exfiltrating their secrets, and the verifier must believe it cannot be subverted. Publishing the design is how one device becomes acceptable to two parties who distrust each other.

As you read, keep asking the awkward question: **this thing lives in a building the other side owns.** Can tamper resistance hold against an adversary with unlimited physical access, time, and budget?

**Read from the beginning and stop when you reach:**

> Whether flexHEGs eventually become part of a comprehensive governance regime or serve more limited verification purposes, beginning development now ensures these options remain available as AI capabilities advance, potentially providing an essential component for maintaining both technological progress and international stability.

That is the end of Part I. The appendices continue below.

#### Article
source:: [[../articles/flexheg-unlinked-for-publication-flexheg-report-v2-part-i-overview]]
to:: "Whether flexHEGs eventually become part of a comprehensive governance regime or serve more limited verification purposes, beginning development now ensures these options remain available as AI capabilities advance, potentially providing an essential component for maintaining both technological progress and international stability."

#### Text
content::
Before the discussion, put a number on your own confidence: how likely is it that a tamper-resistant enclosure holds for years against a state that owns the building it sits in?

Your answer determines how much of this course's remaining machinery you think is necessary.

#### Chat
instructions::
TLDR of what the learner just read:
Petrie, Aarne, Ammann and Dalrymple's flexHEG report Part I (Overview), commissioned by ARIA. FlexHEGs are hardware systems integrated with AI accelerators to enable trustworthy, privacy-preserving verification and enforcement of claims about AI development, so states and firms can make and verify commitments without compromising sensitive information or national security. Two components: an auditable guarantee processor that monitors accelerator usage and enforces rules, and a secure enclosure providing physical tamper resistance against unauthorized modification. Fully open-source implementation with flexible, updateable verification capabilities, supporting diverse governance mechanisms rather than one fixed approach: privacy-preserving model evaluations, controlled deployment mechanisms, computational limits during training, automated safety-protocol enforcement. The authors argue flexHEGs align technical solutions with geopolitical realities — enabling commitments while preserving privacy and sovereignty, respecting competitive dynamics while allowing coordination on shared risk — and that beginning development now keeps options available, since frameworks established early shape development trajectories for decades. They acknowledge the approach remains technically challenging with unresolved implementation hurdles, and that even partial implementations could create valuable options.

The learning outcome this serves: explain the architecture, what flexibility and openness buy, and the assumption the design rests on.

Discussion topics to explore:
- The division of labour, stated precisely: logic versus physics. The processor decides and attests; the enclosure makes the attestation meaningful by making interference detectable. Ask what a guarantee processor *without* an enclosure would be worth — the answer should be "nothing", and understanding why is the point.
- Flexibility as an answer to obsolescence, not a nice-to-have. Thresholds, rules and agreements will change; silicon that enforces one policy is silicon that is wrong soon. Ask what governance schemes a single flexHEG should be able to support and why that argues for updateability over hardwiring.
- Openness as an answer to *mutual* suspicion. Two parties, two different fears: the operator fears exfiltration and backdoors, the verifier fears subversion. Publishing the design addresses both at once. Ask whether open-sourcing creates a new problem (an attacker also reads the design) and let them work out why that is the standard cryptographic answer — security from design strength, not obscurity.
- **The load-bearing assumption, and the most important part of this discussion.** The trust boundary sits inside hardware physically possessed, powered and operated by the party it constrains — a resourced state with indefinite physical access, which is the hardest condition for any tamper-evident design. The authors are candid that this is unresolved. Ask them to compare it to Shavit's on-chip logging, which has the same problem, and note that this recurring difficulty is exactly what Module 4's low-trust architecture is designed to route around.
- The systemic dependencies: flexHEGs must be manufactured in, so they need chipmaker and supply-chain cooperation, and they cover only chips produced under the regime. Legacy hardware and non-participants sit outside — the legacy-hardware problem the learner already met in Wasil. Conclusion to draw: flexHEG is a layer, strong where it applies, that must be stacked with methods requiring no cooperation from the chip.
- "Even partial implementations could create valuable options" and "frameworks established early shape trajectories for decades" — the sequencing argument again. Ask whether they find it persuasive as a reason to build now, absent any agreement to enforce.

Do not resolve the tamper-resistance question. It is genuinely open, and the next module exists because of it.

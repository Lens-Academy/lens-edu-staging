{++{"author":"Elias's AI","timestamp":1785221469866}@@---
id: 'b0d8f205-7165-4e85-8117-0ab9e249ca3d'
slug: aiv-m3-mechanisms
title: "Mechanisms: Hardware and Inference"
readings:
  - "Petrie et al. 2025, Flexible Hardware-Enabled Guarantees (Part I)"
  - "Rinberg et al. 2025, Verifying LLM Inference to Detect Model Weight Exfiltration"
  - "Cankaya 2026, Bit-Exact AI Inference Verification Without Performance Tradeoffs"
authors:
  - Elias+Claude
---

# Learning Outcome:
source:: ![[../Learning Outcomes/Hardware-enabled guarantees]]

# Learning Outcome:
source:: ![[../Learning Outcomes/Verifying inference to catch exfiltration]]

# Lens: Welcome
id:: 'a51d3966-d03f-4141-8d89-52834fa38430'
tldr:: If access is politically expensive, the way out is mechanisms that buy confidence cheaply. Two families here: guarantees built into the chip, and verification of what the chip actually computed.
summary_for_tutor:: Framing lens for Module 3, the technical core. Motivates the module from Module 2's conclusion: access substitutes for missing technology but is politically expensive, so the value of a mechanism is confidence bought per unit of intrusion. Previews two families. Hardware-enabled guarantees (flexHEG: auditable guarantee processor plus secure enclosure, open-source, updateable) attach the guarantee to the chip. Inference verification (Rinberg et al.; Cankaya) changes the question from 'how much compute did you use' to 'is this machine doing what you say', and turns on the crux that GPU floating-point non-determinism forces an approximation tolerance which is itself the covert channel — with bit-exactness closing rather than narrowing it, on the finding that engines are deterministic but not invariant. Also flags the recurring unresolved problem that both hardware approaches place the root of trust inside hardware the constrained party physically owns, which is what motivates Module 4. Framing text only.
#### Text
content::
Module 2 ended on an uncomfortable trade. You can buy verification with access instead of technology — but access costs political capital, exposes IP, and creates espionage surface. So the real figure of merit for any mechanism is **confidence bought per unit of intrusion.** Cheap mechanisms are what make a regime signable, and then sustainable.

This module covers the two families that look cheapest.

**Guarantees built into the chip.** A flexHEG pairs an auditable guarantee processor, which watches how an accelerator is used and enforces the rules, with a secure enclosure that makes tampering detectable. The pairing is the idea: an attestation from a component its owner can freely reprogram tells you nothing, so the physical layer is what gives the logical layer meaning. It is open-source on purpose — the operator must believe it is not a backdoor, and the verifier must believe it cannot be subverted.

**Verification of what the chip actually computed.** This changes the question. Everything so far asked *how much compute did you use* — an accounting question about quantity. Inference verification asks *is this machine doing what you say it's doing*, which is far sharper.

The second family turns on a detail that sounds like an implementation nuisance and is in fact the whole security argument. To check an output you must know what the model *should* have produced — but GPU floating-point arithmetic is not associative and inference engines schedule non-deterministically, so honest runs differ from each other. You must therefore allow a tolerance. **And the tolerance is exactly where an attacker hides data.**

Two readings attack that. The first shrinks the tolerance as far as careful statistics allow. The second removes it, on the observation that engines are *deterministic but not invariant* — so accumulated rounding error is not noise at all, but a fingerprint of the exact configuration that produced it.

Keep one nagging question alive as you read. Both hardware approaches put their root of trust inside a machine that the party being constrained physically owns, powers, and operates. That problem does not get solved in this module. It is why there is a Module 4.

# Lens:
source:: ![[../Lenses/AIV - Flexible Hardware-Enabled Guarantees]]

# Lens:
source:: ![[../Lenses/AIV - Verifying LLM Inference to Detect Weight Exfiltration]]

# Lens:
source:: ![[../Lenses/AIV - Bit-Exact AI Inference Verification]]
++}
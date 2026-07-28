{++{"author":"Elias's AI","timestamp":1785221459403}@@---
id: 'd4f86fd0-f85e-4581-9cee-f499fe26b4c4'
title: "Bit-Exact AI Inference Verification"
tldr: "The rounding error isn't noise. It's a fingerprint of the exact hardware and software that produced it — so you can demand the bits match, and close the channel instead of narrowing it."
summary_for_tutor: "Cankaya's bit-exact inference verification (best paper, ICML 2026 TAIGR workshop), and the direct answer to the tolerance problem raised by Rinberg et al. Where the previous reading shrinks the approximation margin, this removes it. The key finding: modern inference engines (vLLM, HF transformers) are deterministic but NOT invariant — output is a reproducible function of the exact software and hardware configuration, so accumulated floating-point rounding error is an auditable signature of that configuration rather than noise. Reproduce the configuration and you reproduce the bits exactly, without determinism flags and so without their performance cost. This converts an approximate comparison into an equality check, and the same signature also detects unreported modification of the inference stack and covert computation smuggled in as unreported batch elements. Demonstrated via software-only emulation of LLM inference across multiple NVIDIA GPU variants, so the verifier does not need identical hardware. Threat model: covert adversary; requires the right information for re-computation and no backend atomic operations. Read whole — it is short."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

You just left the previous reading with a problem: the auditor has to allow a margin for GPU rounding error, and the margin is the attacker's hiding place. The obvious fix — turn on determinism flags — costs performance nobody will pay.

This paper takes a different route, and the insight is worth pausing on before you read it.

Modern inference engines are *deterministic but not invariant*. Run the same prompt on a different configuration and you get different bits — which is what made this look like non-determinism. But run it on the **same** software and hardware configuration and you get the *same* bits, every time. So the accumulated rounding error was never noise. It was a signature of the configuration that produced it.

Which flips the whole problem. If you can reproduce the configuration, you can demand exact equality — and the margin disappears rather than shrinking.

Read the whole paper. It's short.

#### Article
source:: [[../articles/cankaya-bit-exact-ai-inference-verification-without-performance-tradeoffs]]

#### Text
content::
Two things to have straight before the discussion: what exactly is being reproduced, and what a *verifier without matching hardware* can still check.

#### Chat
instructions::
TLDR of what the learner just read:
Cankaya's bit-exact AI inference verification. Problem: GPU floating-point arithmetic appears non-deterministic, forcing auditors to accept approximate matches, which gives a covert adversary room to hide steganography, to modify inference software without reporting it, or to perform covert computation via unreported batch elements. Finding: modern inference engines (vLLM, HF transformers) produce deterministic but non-invariant outputs without performance-compromising determinism flags — the output is a reproducible function of the exact software and hardware configuration, so accumulated rounding error serves as an auditable signature of that configuration. Consequence: bitwise-precise re-computation becomes possible, converting approximate comparison into an equality check and closing the covert channel rather than merely narrowing it. Demonstrated through software-only emulation of LLM inference across multiple NVIDIA GPU variants, so the verifier does not need identical hardware. Threat model: a covert adversary who complies only when detection likelihood is high. Requires the right information to be available for re-computation, and excludes cases where backend atomic functions are called. Best paper, ICML 2026 TAIGR workshop.

The learning outcome this serves: explain how verifying inference detects exfiltration, why non-determinism is the crux, and what bit-exact re-computation adds.

Discussion topics to explore:
- The reframe, which is the whole paper: **the rounding error is signal, not noise.** Ask them to articulate the difference between "deterministic" and "invariant" and why that distinction is what rescues the scheme. Learners often blur them.
- What it buys over the previous reading: equality instead of similarity. The channel is *closed*, not squeezed. Ask what that changes for the adversary's options.
- The three things one signature catches at once: hidden payloads in outputs, an inference stack that was quietly modified, and undeclared batch elements doing covert work. Ask why a configuration fingerprint covers all three.
- Software-only emulation across GPU variants is the practically important result — the verifier does not need to own matching silicon. Connect this to the low-trust theme they are about to meet: the less special hardware verification requires, the fewer things both parties must agree to trust.
- The conditions. Re-computation needs the right information available (so the prover must declare enough), and it breaks when backend atomics are involved. Ask what an adversary would do with that exclusion, and whether "no atomics" is something a verifier can check or must assume.
- Worth surfacing: this is a workshop paper by an independent researcher, and the previous reading was a multi-author lab effort. Ask what that says about how young this field is — and note that the next module's author is the same person, arguing that the whole architecture is an orphaned problem.

Check that they can explain deterministic-but-not-invariant, and why it means the tolerance can go to zero without paying a performance cost.
++}
---
id: '172fd6b4-511f-4649-baf2-e0f2a8433259'
learning-outcome: "Explain how verifying LLM inference detects steganographic model-weight exfiltration, why the non-determinism of GPU arithmetic is the crux of the problem, and why bit-exact re-computation strengthens the guarantee"
domain: "[[../Domains/Governance and Policy]]"
requires:
  - "[[Hardware-enabled guarantees]]"
authors:
  - Elias+Claude
---
## Test:
id:: 47816cf1-9fe3-4e0b-b41e-395259c6c682
#### Question
content:: An attacker who controls an inference server does not need to smuggle out a hard drive. They can hide the weights inside ordinary-looking model responses, a few bits at a time, and let normal traffic carry them out.

**Explain how verifying inference catches this. Why is the non-determinism of GPU floating-point arithmetic the crux — and what does bit-exact re-computation add?**
assessment-instructions::
Score according to the following rubric.

**1** — Treats the problem as ordinary network security or output filtering; no account of why the channel exists or how verification closes it. *Example: "You'd monitor the network traffic and scan the outputs for anything that looks like model weights."*

**2** — Understands that responses could carry hidden data, but cannot explain what verification checks or why non-determinism matters. *Example: "The attacker hides weights in the text using steganography, so you verify the outputs are what the model should have produced."*

**3** — Explains the mechanism: the defender re-computes what the declared model should have produced for the given inputs and compares against what was actually served, so a response carrying smuggled payload fails the check. Identifies the crux correctly: this only works if "what the model should have produced" is a well-defined bit string. GPU floating-point arithmetic is not associative and inference engines batch and schedule work non-deterministically, so outputs legitimately vary run to run — which forces the auditor to accept *approximate* matches, and every bit of accepted slack is exactly the channel the steganographic attacker hides in. So the security of the scheme reduces to how tightly you can pin down legitimate variation. Notes the framing as a security game over valid sources of non-determinism, with practical estimators for them, and the reported result: exfiltratable information reduced to under 0.5% at a false-positive rate under 0.01% on a 30B MoE model — a slowdown of more than 200x for the adversary — at minimal cost to the provider. *Example: "You re-run what the declared model should have said for those inputs and compare it to what actually went out; a response with a payload stuffed into it won't match. The catch is that 'should have said' has to be exact, and GPU arithmetic isn't: floating-point addition isn't associative and the engine batches and schedules non-deterministically, so honest runs differ from each other. That forces you to allow a tolerance — and the tolerance *is* the covert channel. So the whole game is characterizing legitimate variation tightly enough that there's no room left to hide. Done well it cuts what you can exfiltrate to under half a percent with a tiny false-positive rate, over a 200x tax on the attacker, and it's cheap for the provider."*

**4** — As above, plus explains what bit-exact re-computation contributes: it removes the tolerance rather than shrinking it. Modern engines turn out to be *deterministic but not invariant* — the output is a reproducible function of the exact software and hardware configuration, so accumulated rounding error is not noise but a signature of the configuration that produced it. Reproduce the configuration and you can reproduce the exact bits, without determinism flags and without their performance cost. That converts an approximate comparison into an equality check, closing the channel instead of narrowing it, and simultaneously detects unreported changes to inference software and covert computation smuggled in as unreported batch elements. *Example: Adds "Bit-exactness removes the tolerance instead of tightening it. The finding is that engines are deterministic but not invariant: given the same software and hardware configuration you get the same bits, so the accumulated rounding error is a fingerprint of the configuration rather than noise. Reproduce the configuration and you can reproduce the output exactly — no determinism flags, no performance penalty. Now it's an equality check, not a similarity check, and the channel is closed rather than squeezed. The same signature also catches an inference stack that was quietly modified, or extra batch elements doing work nobody declared."*

**5** — As above, plus reasons about the threat model and its edges: both results assume a **covert adversary** — one who complies while the probability of detection is high, so raising detection probability and cost is the goal, not achieving impossibility. Notes what the guarantees are conditional on: specified trust assumptions about which components can be compromised, availability of the right information to re-compute, and the absence of backend atomic operations that break reproducibility. Draws the governance significance: verification of inference is a distinct and easier target than verification of training, because inference happens continuously and leaves per-token input-output evidence, so it supports semantic screening of what a facility is actually doing rather than only aggregate accounting of how much compute it used. *Example: Adds "Both results are stated against a covert adversary — someone who behaves while the chance of getting caught is high — so the aim is to raise detection probability and cost, not to make cheating impossible. And the guarantees carry conditions: assumptions about which components can be compromised, having the information needed to re-compute, and no backend atomics to break reproducibility. The governance payoff is that inference is a friendlier target than training: it runs continuously and leaves token-level input-output evidence, so you can ask what a facility is *doing*, not just how many FLOPs it burned. That's a much sharper question than aggregate compute accounting can answer."*
max-chars:: 2000

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIV - Verifying LLM Inference to Detect Weight Exfiltration]]

## Lens:
source:: [[../Lenses/AIV - Bit-Exact AI Inference Verification]]

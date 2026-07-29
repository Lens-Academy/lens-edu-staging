---
id: 'c7d563ab-3561-484e-8d97-fd663939077a'
title: "Verifying LLM Inference to Detect Weight Exfiltration"
tldr: "An attacker who runs your inference server doesn't need to steal a hard drive. They can hide the weights inside ordinary answers — and the only thing that lets them is the slack you allow for GPU rounding error."
summary_for_tutor: "Rinberg, Karvonen, Hoover, Reuter and Warr on verifying LLM inference to detect model-weight exfiltration. An adversary controlling inference infrastructure can steganographically encode weights into ordinary-looking model responses and let normal traffic carry them out. The defence re-computes what the declared model should have produced and compares. The crux — and the reason this is a research paper rather than an engineering ticket — is that GPU floating-point arithmetic is not associative and inference engines batch and schedule non-deterministically, so honest outputs legitimately vary; the auditor must allow a tolerance, and that tolerance IS the covert channel. The paper formalises exfiltration as a security game, identifies the valid sources of non-determinism, builds two practical estimators for them, and reports reducing exfiltratable information to under 0.5% at a false-positive rate under 0.01% on MoE-Qwen-30B (a >200x adversary slowdown) at minimal provider cost. Threat model is a covert adversary under stated trust assumptions. Excerpt covers introduction through the theoretical framework; empirical results and appendices remain collapsed."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

A shift of target. Everything so far has asked *how much compute did you use* — an accounting question. This asks a sharper one: *is the machine in front of me doing what you say it's doing?*

The setting: someone controls an inference server hosting a valuable model. They want the weights out. They do not need to smuggle a drive past security — they can encode the weights into ordinary-looking responses, a few bits at a time, and let normal API traffic carry them away.

The defence is obvious in one line: re-compute what the declared model *should* have said, and compare. Watch carefully for why that line is much harder than it sounds — the answer is that GPU arithmetic doesn't give the same answer twice, so you have to allow a margin, and the margin is exactly where the attacker lives.

This is a technical paper. You do not need to follow every bound. Follow the *security game*: what the attacker is allowed to do, and what the defender measures.

**Read from the beginning and stop when you reach:**

> Combining this with the transformation below, we can give concrete exfiltration limitations under the stated assumptions for the policies that we propose.

The empirical results are below if you want the numbers.

#### Article
source:: [[../articles/rinberg-verifying-llm-inference-to-detect-model-weight-exfiltration]]
to:: "Combining this with the transformation below, we can give concrete exfiltration limitations under the stated assumptions for the policies that we propose."

#### Text
content::
State the crux in one sentence before moving on: *why does the non-determinism of floating-point arithmetic hand the attacker a channel?*

If you can say that cleanly, the next reading — which closes the channel rather than narrowing it — will land properly.

#### Chat
instructions::
TLDR of what the learner just read:
Rinberg et al. on detecting model-weight exfiltration by verifying LLM inference. Threat: an adversary with control of inference infrastructure hides model weights inside ordinary model responses using steganography, exfiltrating via normal traffic. Defence: re-compute what the declared model should have produced for the given inputs and compare to what was served; a response carrying a payload fails. The crux is that "what it should have produced" must be a well-defined bit string, and it is not — floating-point addition is not associative, and inference engines batch and schedule work non-deterministically, so honest runs differ from one another. The auditor must therefore accept approximate matches, and every bit of accepted slack is the steganographic channel. The paper formalises weight exfiltration as a security game, identifies the valid sources of non-determinism in LLM inference, and constructs two practical estimators for them, provably mitigating steganographic exfiltration under stated trust assumptions. Reported result: on MOE-Qwen-30B the detector reduces exfiltratable information to under 0.5% with a false-positive rate under 0.01%, over a 200x slowdown for the adversary, at minimal additional cost to the provider. Notes an open empirical question about the support size of the truncated distribution under adversarial prompts, and that a motivated adversary may tune settings and prompts to raise their steganographic rate.

The learning outcome this serves: explain how verifying inference detects steganographic weight exfiltration, why non-determinism is the crux, and why bit-exact re-computation strengthens the guarantee.

Discussion topics to explore:
- The central move, and do not let them past it vaguely: **the tolerance is the channel.** Security here is not "can we detect a weird output" but "how tightly can we characterise legitimate variation" — because whatever variation you must permit, the adversary can encode into. Ask them to explain why a *looser* tolerance is strictly worse for security and why you cannot simply set it to zero with today's engines.
- Why this is a different and easier target than verifying training. Inference runs continuously and leaves per-token input-output evidence, so you can ask what a facility is *doing* rather than only how many FLOPs it burned. Draw out why that supports semantic screening in a way aggregate compute accounting cannot.
- The threat model. This is a **covert adversary**: someone who complies while the chance of being caught is high. So the achievement is raising detection probability and cost — a >200x tax — not making exfiltration impossible. Ask what that standard implies for how to read the numbers, and connect back to the deterrence logic from Shavit's random sampling.
- Cost asymmetry: strong protection at minimal provider cost is what makes this deployable. Ask why that matters politically as well as commercially.
- Limits: the guarantees are conditional on trust assumptions about which components can be compromised, and the adversary may tune prompts and settings to improve their rate. Ask them what they would want measured before trusting this in a treaty context.
- If they ask "why not just inspect the outputs for anything weird" — that is the naive version. Push them to see that steganography is designed to be statistically ordinary, which is why you need re-computation against a reference, not anomaly detection.

Check that they can state the crux — tolerance equals channel — in their own words. That is the one thing to carry into the next reading.

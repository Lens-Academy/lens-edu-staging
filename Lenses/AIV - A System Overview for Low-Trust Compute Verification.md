---
id: '2bf58269-c15b-48a2-a178-61003e10543e'
title: "A System Overview for Low-Trust Compute Verification"
tldr: "Every mechanism so far needed somebody to trust some silicon. This one doesn't: each side trusts only its own hardware, and confidence comes from redundancy plus optics you can hold up to the light."
summary_for_tutor: "Cankaya's system architecture (v0.2 working draft, June 2026) — the capstone technical reading. Its ambition is to remove the assumption every prior mechanism needed: mutually trusted silicon. Architecture splits evidence CAPTURE from evidence EVALUATION. Capture is deliberately minimal and non-programmable: network taps at the boundary recording cryptographic commitments (hashes, not plaintext), optional memory probes using response-time analysis, and a prover-supplied but UNTRUSTED manifest labelling which hash intervals map to which workloads. Evaluation happens later in air-gapped environments where claimed workloads are re-run and checked against commitments via bit-exact replay, using redundant mutually distrusting TCBs from different supply chains that cross-check before disclosure (Plan A), with zero-knowledge proofs as the eventual Plan B that removes secure hardware entirely. 'Low-trust' means no component must be trusted by BOTH parties: each trusts only its own hardware, and confidence emerges from redundancy plus inspectable analog data-movement control (fiber splitters, data diodes, optical isolation, sanitized egress). Instructor-executor separation lets untrusted off-the-shelf accelerators do heavy replay while trust stays rooted in minimal TCBs; the executor is blinded to the claimed output so it cannot fabricate a match. Threat model is a covert adversary — 'caught if they fail to stay hidden even once' — which is what licenses near-term claims: existing tap technology, no new silicon, off-the-shelf parts, under ~10% cost overhead. Verifies individual ML workloads at token granularity, inference vs training, model whitelists, blacklisted use. Honest open problems on supply-chain security for taps and audit devices, side channels, ZKP overhead for floating-point replay, semantic-screening robustness, and distinguishing technical failure from deliberate violation."
authors:
  - Elias+Claude
---

#### Text
content::
\## Reading Assignment

Notice what every mechanism so far has quietly required. Shavit needed you to trust the chip's logging firmware. flexHEG needs you to trust a guarantee processor inside a box the other side owns. Each one puts a root of trust in silicon that somebody has to vouch for.

This reading tries to get rid of that requirement. The target: an inspector should be able to establish what a data centre ran without either party trusting the other's hardware — and **without any new chips being designed.**

Two ideas do most of the work, and it's worth watching for them:

> **Split capture from evaluation.** What runs continuously is deliberately stupid — passive taps recording hashes. What is complicated and expensive happens later, elsewhere, and rarely.

> **Buy trust with redundancy instead of authority.** Nobody trusts a shared device. Each side trusts only its own hardware, several independently-sourced machines do the same computation, and they cross-check. One subverted box produces a *disagreement*, not a false clean result.

**Read from the beginning and stop when you reach:**

> This disaggregation between an instructor and an executor makes it viable to use off-the-shelf AI accelerators securely, to re-run heavy workloads in practical timeframes, while still rooting trust in minimal, unilaterally trusted TCBs rather than needing to secure complex ML accelerator technology stacks.

That covers the threat model, the requirements, the system overview, and the subsystem designs. The engineering detail continues below.

Note the date and the version number. This is a working draft of an architecture, not a finished standard — the open problems at the end are part of the reading, not an afterthought.

#### Article
source:: [[../articles/cankaya-a-system-overview-for-near-term-low-trust-ai-compute-verification]]
to:: "This disaggregation between an instructor and an executor makes it viable to use off-the-shelf AI accelerators securely, to re-run heavy workloads in practical timeframes, while still rooting trust in minimal, unilaterally trusted TCBs rather than needing to secure complex ML accelerator technology stacks."

#### Text
content::
Two questions to hold before the discussion.

First: why is it *safer* for the always-on component to be as dumb and non-programmable as possible? That runs against most engineering instincts.

Second: the manifest — the prover's own labelling of what each blob of evidence was — is explicitly untrusted. So what stops the prover simply lying in it?

#### Chat
instructions::
TLDR of what the learner just read:
Cankaya's near-term low-trust AI compute verification architecture (v0.2 working draft). Goal: let mutually distrusting parties verify what a data centre computed, without mutually trusted silicon and without newly designed chips. Argues aggregate properties like total training FLOPs are insufficient against covert development or deployment — you need workload-level evidence. Architecture separates evidence capture from evidence evaluation. Capture: minimalist, non-programmable network taps at the boundary recording cryptographic commitments (hashes, not plaintext); optional memory probes using response-time analysis; a prover-supplied, untrusted manifest mapping hash intervals to objects and workloads. Evaluation: air-gapped auditing environments where claimed workloads are re-computed and checked against the commitments by bit-exact replay. Plan A uses redundant, mutually distrusting TCBs (trusted computing bases) sourced from different supply chains performing identical computations and cross-checking before disclosure; Plan B is zero-knowledge proofs, removing the need for secure hardware entirely. Low-trust means each party trusts only its own hardware and confidence comes from redundancy, backed by inspectable analog data-movement control — passive fiber splitters, data diodes, optical isolation, sanitized egress — so one-way evidence flow rests on physics rather than firmware. Instructor-executor separation sends only claimed inputs to an untrusted replay device, deliberately withholding the claimed output, so a compromised executor cannot fabricate a match without actually computing. Threat model: covert adversary, deterred by detection probability times consequence; "a covert adversary is caught if they fail to stay hidden even once." Verifies individual ML workloads at token granularity, inference vs training, model-whitelist compliance, blacklisted use. Near-term feasibility: existing tap technology already used in finance and defence, no new semiconductors, off-the-shelf components, target under ~10% cost overhead relative to monitored hardware. Open problems: supply-chain security for taps and evaluation devices against nation-state adversaries (tamper-evident seals and PUFs insufficient), side-channel defence (power-line filtering, look-through jamming), ZKP overhead for floating-point replay, adversarial robustness of inspector agents against semantic evasion, memory-probe validation at scale, secure ingress/egress under bilateral distrust, and disambiguating technical failure from deliberate violation.

The learning outcome this serves: describe the architecture, the capture/evaluate split, redundant mutually distrusting TCBs, and what low-trust and covert adversary mean here.

Discussion topics to explore:
- Answer the two questions from the prompt properly. **Why dumb is safer:** the always-on component sits in the hot path and cannot be audited continuously, so its trustworthiness must come from having almost no attack surface — non-programmable means there is no firmware to subvert, and simple means an inspector can actually verify what it does. Complexity is affordable only where it runs rarely and offline.
- **Why the untrusted manifest is safe:** the manifest is a claim, and claims are checked against commitments captured independently of the prover. Lying in the manifest does not corrupt the evidence — it produces a mismatch. This is the key architectural idea: let the prover say whatever they like, then check it against something they could not touch. Push until they see the manifest is a hypothesis, not a data source.
- **What "low-trust" actually means** — not "more secure", but *no component requiring trust from both parties*. Confidence is manufactured from redundancy plus independent supply chains, so subversion shows up as disagreement. Ask what it would take to defeat that (compromising several independently-sourced devices consistently), and why that is a much higher bar than compromising one.
- The analog layer. Splitters, diodes, optical isolation: the one-way-ness of the evidence path is a property of the optics, which an inspector can physically examine, rather than a promise made by software. Ask why that is worth the inconvenience, and connect it back to Shavit's unresolved supply-chain-attack problem.
- Blinding the executor is a small, elegant move — ask them to explain why withholding the claimed output is what makes an untrusted accelerator usable.
- The threat model doing the heavy lifting: because a covert adversary is caught if they slip even once, continuous capture turns cheating into an accumulating risk rather than a single gamble. This is what licenses "near-term" and the sub-10% overhead target. Ask whether they find the covert-adversary assumption reasonable for states, and what a non-covert (openly defecting) adversary would do to the scheme.
- Take the open problems seriously — they are the honest part. Protecting the taps against the host state's own supply chain is arguably the hardest, and it is the same problem Shavit deferred. Ask which open problem they would fund first.
- Plan B (ZKPs) as the version that dissolves the remaining trust requirements. Ask what it would take to get there and why floating-point replay in circuits is the obstacle.

Stay grounded in the draft. Do not present it as settled or deployed — it is a proposal with named gaps, and reasoning about those gaps is the point.

---
id: '43f8c54c-e8ae-4f34-b497-12f532d37957'
title: "A system overview for near-term, low-trust AI compute verification"
tldr: "Read one engineer's blueprint for checking a rival's AI compute without trusting them, then take it apart the way a reviewer would: state its problem, map its argument, trace evidence from chip to verdict, and find the step where the conclusion outruns the proof."
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. The lens is a close-reading assignment on Naci Cankaya's paper 'A System Overview for Near-Term, Low-Trust AI Compute Verification' (MIRI Technical Governance Team). Nine questions: 1, 2 and 5 are required; 3, 4, 7 and 9 are marked optional so the learner can pick any one of them (they must do at least one); 6 and 8 are optional. Every answer should cite a page or section of the paper and separate the author's claims from the learner's own conclusions. Do not summarise the paper for the learner; push them back to the text, check that reconstructed arguments name premises and conclusions, and treat well-reasoned disagreement with the author as success. The paper is inlined in two parts with an interactive widget between them, placed right after the section 3.2 premise: two tabs redraw the figures from sections 3.2.1 and 3.2.2 and let the learner step through the twelve-step execution trace, lighting the parts of each diagram that a step touches. All of the prose stays in the article around it, including both phase intros, the numbered lists, the three conditions that end the trace early and the budgeted-fault note. Question 5 asks for that same end-to-end process as a schematic, so expect the learner to build their own from the paper rather than describe the widget. A second widget, an audit confidence calculator, follows the inlined paper, directly under Appendix A1: four log sliders (checked samples per audit day, true flaw rate, prover GPUs and GPU-seconds per proof) recompute the detection probability, the 95 percent certified ceiling and the proof budget live, reproducing every cell of the appendix three tables at the inputs the paper states. The tables, the formula and the zkLLM anchor stay in the article text above it, and the learner is done once two different sliders have been moved."
tags: [wip]
reading_minutes: 100
tutor_minutes: 90
---
#### Text
content::
In this module, you will tackle a comprehensive technical verification system proposal, synthesizing the verification mechanisms you learned in Module 2, actors and incentive structures you learned in Module 1, and verification intuitions you gained in Module 0.

:::callout {title="By the end of this module, you will be able to:" tone="blue"}
1. Explain how the requirements of an international AI agreement might be translated into a technical verification system.
2. Understand and critique the assumptions, design choices, and unresolved problems involved in verifying AI compute use under conditions of limited trust between the parties.
3. Apply an existing compute verification regime to a realistic facility simulation, identifying weak points, evasion possibilities, and testable assumptions.
:::

\## Assignment

Read Naci Cankaya’s working paper **A System Overview for Near-Term, Low-Trust AI Compute Verification**, inlined in full below, from the version note through Appendix A1. It is also published [on the MIRI Technical Governance site](https://techgov.intelligence.org/research/a-system-overview-for-near-term-low-trust-ai-compute-verification).

Answer Questions 1, 2 and 5 together with one of Questions 3, 4, 7 or 9. Support each answer with page or section references to the paper.

Question 8 is an optional research task and may require consultation of an external technical source.

In your answers:

- distinguish the author’s claims from your own conclusions;
- reconstruct arguments by identifying their premises and conclusions;
- state explicitly when the available evidence does not justify a definite conclusion;
- formulate counterarguments in their strongest plausible form.

#### Article
source:: [[../articles/cankaya-a-system-overview-for-near-term-low-trust-ai-compute-verification]]
from:: "**Version 0.2, working draft**"
to:: "We follow one inference request, but the tap sees it only as part of an undifferentiated byte stream."

#### Text
content::
The two figures in sections 3.2.1 and 3.2.2 below are redrawn here as one interactive trace: step through it first, then read the two sections in full.

#### Widget
source:: [[../widgets/covert-execution-trace]]

#### Article
source:: [[../articles/cankaya-a-system-overview-for-near-term-low-trust-ai-compute-verification]]
from:: "### 3.2.1 Evidence capture"
to:: "| 10,000 | 5% | ~108,000 | 1 in 1,600 | 0.0028% |"

#### Text
content::
The three tables in Appendix A1 are one calculator. Move its sliders to see what a sample size, a flaw rate and a prover budget buy each other.

#### Widget
source:: [[../widgets/cankaya-audit-calculator]]

#### Text
content::
\## Questions

Read all 9 questions before beginning. Answer Questions 1, 2, 5, and any one question out of questions 3, 4, 7 or 9. Questions 6 and 8 are optional.

Support each answer with section references to the paper, for example Section 2b or Section 3.2.2, since the inlined text above carries the author’s section numbering rather than page numbers. If you prefer to cite by page, work from the [PDF](https://intelligence.org/wp-content/uploads/A-system-overview-for-near-term-low-trust-AI-compute-verification.pdf). Clearly distinguish the author’s claims from your own conclusions.

Questions 3, 4, 7 and 9 are marked optional below so that you can complete the lens with whichever one you choose; answer at least one of them.

#### Question: Open
id:: 217e8374-2817-43eb-951b-e347de1c6370
content:: **Question 1. Identify the principal problem** (required)

State in one sentence the principal problem that the author seeks to solve.
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 80: the problem the paper sets itself, 40: how rival states party to an AI agreement can verify each other's compliance by checking what their AI compute is actually used for, 25: under low trust: the parties are adversaries, neither trusts the other's hardware, and the checked side's secrets must not leak, and 15: in the near term: retrofitted to existing AI hardware rather than waiting for new, trusted chips. 10: it is stated in one sentence. 10: a section reference. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer states a mechanism (network taps, hashing, random sampling) or a benefit instead of the problem. Model answer, for the feedback, not a grading checklist: "How can rival states such as the US and China verify each other's compliance with an AI agreement by checking what their AI compute is actually used for, down to individual workloads, when neither trusts the other's hardware, the prover's confidential data must not leak, and the system has to be retrofitted to existing AI hardware within months rather than years (Sections 1, 2a and 2c)?"
feedback-instructions:: Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. No generic praise.

#### Question: Open
id:: ff46a6f8-d7c3-45cf-bc6b-ae9e8d9235e2
content:: **Question 2. Reconstruct the proposed approach** (required)

Identify the principal propositions that constitute the author’s approach to low-trust AI compute verification.

Express each proposition in your own words and support it with a page or section reference. Explain the logical relationships among the propositions: which serve as assumptions, which describe mechanisms, and which state the intended results.
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 30: the principal propositions of the author's approach in the learner's own words, with at least the core ones in each category: the parties are covert adversaries deterred by a high enough chance of detection; neither side can trust shared chips, so each relies on simple devices of its own; network taps commit to (hash) all traffic leaving the compute, with the verifier later checking random samples; an isolated audit environment replays and checks those samples; the results are statistical confidence that violations are rare, while confidential data stays inside the facility. 30: each proposition is correctly sorted as an assumption, a mechanism or an intended result. 30: the logical relationships are stated: which assumptions justify which mechanisms, and which mechanisms are meant to deliver which results. 10: a page or section reference for the propositions. Cap at 30 if the answer paraphrases the abstract with no sorting or relationships. Model answer, for the feedback, not a grading checklist: "Assumptions: the parties are covert adversaries, deterred once the chance of being caught is high enough; silicon both rivals trust is unattainable, but each can trust a minimal device of its own; aggregate compute is not enough, so evidence must identify individual workloads; computations can be replayed exactly. Mechanisms: minimal network taps hash all traffic leaving the pod and only these commitments leave the facility; the verifier later challenges random samples; an air-gapped audit environment with several diverse trusted devices replays and screens the samples. Intended results: statistical confidence that non-compliant workloads are rare, no confidential data leaving the facility, cheap and fast retrofitting. Relationships: the covert-adversary assumption justifies random sampling instead of making cheating impossible, which keeps cost low; distrust of silicon leads to redundancy across devices each side trusts; exact replay lets the audit tie captured traffic to a declared computation."
feedback-instructions:: Name one missing or misclassified proposition, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 0fcb8824-a51d-4461-9f0e-3314e0e91366
content:: **Question 3. Analyse the covert-adversary argument** (choose one of Questions 3, 4, 7 or 9)

The author argues that a verification system need not make every undeclared workload physically impossible.

- Reconstruct the argument by identifying its premises and conclusion.
- Identify two architectural choices that depend on this argument.
- Determine which premise is most vulnerable and explain why its failure would be consequential.
- Formulate a counterargument.
- Assess whether the argument applies equally to a malicious prover and a malicious verifier. Justify your conclusion.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 25: the argument reconstructed, with its premises (for example: parties want cheating to stay hidden; cheating is deterred when detection probability times the cost of being caught exceeds the gain; a covert cheater must evade every check, the defender needs to catch it once) and its conclusion (high enough detection probability suffices, perfect prevention is not needed). 15: two architectural choices that actually rest on the argument. 20: the most vulnerable premise, with why its failure would matter for the system. 15: a counterargument in its strongest form. 15: a reasoned verdict on whether the argument holds equally for a malicious prover and a malicious verifier. 10: section references, with the author's claims kept apart from the learner's own conclusions (the lens asks for both on every answer). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Premises (2b): members of the agreement want any evasion to stay covert; following Aumann and Lindell, cheating is deterred when detection likelihood times the cost of getting caught exceeds the expected gain; a covert adversary has to evade every check every time, while the defender needs to catch it only once and can layer detection mechanisms; random sampling of committed records drives the detection probability up quickly (Appendix A1). Conclusion: the system need not make every undeclared workload physically impossible; evasion only has to be very likely to be caught, or too small to be consequential. Choices resting on it: capture everything and audit random samples retroactively (3.1, 3.2.2); accepting unilaterally trusted devices checked by redundancy rather than demanding perfect security (5.2.1); suppressing side channels to low bandwidth rather than to zero (5.3.1); a budgeted fault rate (3.2.2). Most vulnerable premise: that being caught carries a high, credible cost. The attribution problem (2b) lets a cheater wave off a detected anomaly as a malfunction, and consequences have to arrive in time (footnote 4); if either fails, detection no longer deters and the whole sampling design loses its justification. Counterargument: if a covert breakthrough could give a decisive strategic advantage, the expected gain is so large that no realistic detection probability deters, and attacks rehearsed on replicas (2b) can make the chance of detection per attempt low. Prover versus verifier: not symmetric. A cheating prover must run undeclared work repeatedly, so sampling catches it; a malicious verifier needs only one successful leak of a few bits, which is irreversible, so deterrence after the fact protects the prover little. The paper concedes this: there is practically no tolerance for leakage to the verifier (5.2.1, footnote 20), which is why the auditing environment relies on prevention (air gaps, cross-checks, sanitized egress) rather than on detection."
feedback-instructions:: Name the weakest part, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 18ac6dc1-86be-42bf-9d00-c0b7d7c74e5d
content:: **Question 4. Examine the rejection of mutually trusted silicon** (choose one of Questions 3, 4, 7 or 9)

Reconstruct the author’s argument against relying on general-purpose processors or AI accelerators that must be trusted by both parties.

- What reasons are given for rejecting this approach?
- How are analog controls, unilateral trusted computing bases, redundant computation, and output cross-checking intended to address the problem?
- Does the proposed architecture eliminate trust, reduce it, or redistribute it?
- Identify one strong and one vulnerable element of the argument. Formulate a possible objection to each.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 20: the paper's reasons for rejecting mutually trusted general-purpose processors or accelerators. 32: how each of the four substitutes addresses the problem, 8 each: analog controls, unilateral trusted computing bases, redundant computation, and output cross-checking. 18: a defended position on whether the architecture eliminates, reduces or redistributes trust. 20: one strong and one vulnerable element of the argument, 10 each, each with an objection. 10: section references, with the author's claims kept apart from the learner's own conclusions (the lens asks for both on every answer). Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Reasons (4.1): against nation-state adversaries, proving the absence of hardware trojans is practically impossible (dopant-level trojans escape even electron microscopy); even a secure processor depends on complex upstream parts such as the signal processors in optical transceivers; supply-chain hardening takes years and costly infrastructure, which clashes with the near-term, retrofittable requirement (2c); three decades of nuclear arms-control work produced nothing mutually trusted beyond very minimal ASICs; and there is no accepted method for proving an electronic system free of vulnerabilities. Substitutes: analog controls (fiber splitters, data diodes, enclosures) are simple enough for both sides to inspect and decide which device sees what (4.2); unilateral TCBs let each party rely only on its own minimal device, with heavy computation pushed to untrusted executors that are blinded to the claim (4.3, 4.3.4); redundant computation runs the same task on at least three diverse TCBs from different supply chains (5.2.1); output cross-checking splits every output so it is compared, and the prover recomputes what the verifier's devices emit, before anything is released (4.3.2). Position: it redistributes trust more than it eliminates it: trust moves from shared complex silicon to each party's own small TCB, to inspectable analog parts, to physical security, and to the assumption that diverse devices do not share vulnerabilities. Strong element: analog components really are inspectable (glass fused to glass); objection: inspection may need destructive testing, and hot-swapped replacement parts reopen the supply-chain question. Vulnerable element: redundancy only helps if the devices fail independently (5.2.1); objection: shared components, such as the single transmitter feeding the fiber before the split (5.2.1 open questions), shared software stacks or the same foundries create common-mode failures."
feedback-instructions:: Name the weakest part, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 70c2bc7d-7fb4-4a7e-a4a6-f39e79fc0cfd
content:: **Question 5. Reconstruct the verification process** (required)

Represent schematically the complete verification process proposed in the paper, beginning with activity on monitored hardware and ending with the release of an evaluation result.

For each transition:

- identify the evidence or information transferred;
- identify which party or component produces, possesses, and evaluates it;
- state what conclusion the evidence is intended to support;
- identify any additional assumption required for that conclusion.

Identify one transition at which the stated conclusion may not follow from the available evidence.
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 20: the schematic runs end to end as a sequence of transitions, from activity on the monitored hardware to the release of an evaluation result. 40: each transition has the four items, 10 each: the evidence or information transferred; who produces, holds and evaluates it; the conclusion it is meant to support; any additional assumption that conclusion needs. 30: one transition identified where the conclusion may not follow from the evidence, with the reason. 10: section references. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer is a prose summary of the system with no transitions. Model answer, for the feedback, not a grading checklist: "1. Workload runs on a monitored pod; its traffic crosses the tapped frontend link (3.2, 3.2.1 step 1). Evidence: raw bytes; produced by the prover's servers, seen by the verifier's tap. Conclusion: this is all of the pod's input and output. Assumption: no bypass, all communication crosses the tap (premise of 3.2; side-channel defenses 5.3.1). 2. Tap hashes packet groups; hashes leave by a split, sanitized link and both parties store them (steps 2 and 3). Evidence: hash commitments; produced by the tap, held by both. Conclusion: a fixed, tamper-evident record of the traffic exists. Assumption: the tap hashes correctly and leaks nothing (4.3.2, 4.3.3). 3. Prover recomputes the hashes, keeps the plaintext and writes a manifest (steps 4 and 5). Conclusion: the tap emitted only legitimate commitments; the manifest states the prover's claims. Assumption: the prover retains or can reproduce the plaintext. 4. Verifier sends a random challenge over controlled ingress; the prover supplies preimages, manifest entries and replay metadata (3.2.2 steps 1 and 2). Conclusion: the sample is unpredictable. Assumption: the data diode is truly one-way and the sampling random. 5. Each TCB reassembles the objects and checks them against the hashes and manifest (step 3). Conclusion: the supplied data is what was captured. Assumption: the hash is collision-resistant. 6. Each TCB replays the computation under the declared metadata (step 4). Conclusion: the declared computation produced the captured output. Assumption: bit-exact replay from the logged properties (5.2.2). 7. Screening for compliance (step 5). Conclusion: the workload obeyed the rules. Assumption: the screening software and inspector agents judge correctly and cannot be gamed (5.2.3). 8. TCBs cross-check and a minimal disclosure is released to both parties (steps 6 and 7). Conclusion: the verdict is trustworthy and nothing else leaked. Assumption: the diverse TCBs do not share a vulnerability (5.2.1). Weak transition: the step from clean samples to the whole facility. Replay shows that sampled, declared computations happened as claimed, but it cannot show that nothing crossed outside the tap or that the purpose was benign, so a clean audit supports 'the declared traffic was compliant', not 'all activity on the hardware was compliant'."
feedback-instructions:: Name the transition most in need of work, then ask one follow-up question. No generic praise.

#### Question: Open
id:: dfa796c5-8851-4219-8891-2b3bea0a9f31
content:: **Question 6. Evaluate the strongest arguments** (optional)

Identify three arguments in the paper that you consider particularly strong.

For each argument:

- reconstruct it independently of the author’s wording;
- explain why it is comparatively strong;
- formulate the strongest plausible counterargument.

The existence of a valid counterargument does not necessarily make an argument weak.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 30 for each of three arguments, 10 each: it is reconstructed in the learner's own words with a section reference; a reason it is comparatively strong; the strongest plausible counterargument. 10: the three are distinct arguments from the paper, not one point repeated and not the learner's own claims. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. Random sampling deters a covert adversary (2b, Appendix A1): a cheater must evade every check, and the statistics do not depend on fleet size; about 3,000 clean checks certify at 95 percent confidence that under 0.1 percent of workloads are non-compliant. Strong because the step from sample to bound is mathematics, not a guess. Counterargument: it assumes truly random, unpredictable sampling and a credible cost of being caught, and the attribution problem weakens the latter. 2. Mutually trusted silicon is a dead end (4.1): trojans can be undetectable, hardening takes years, and nuclear arms control spent three decades without success beyond minimal ASICs. Strong because it rests on independent historical evidence rather than on the author's design. Counterargument: the replacement still needs unilaterally trusted devices and inspectable analog parts, whose own security is untested, and supply-chain-hardened FPGAs already exist. 3. Separating capture from evaluation enables retroactive screening (3.1): because records can be re-examined with newer software, a cheater must anticipate every future detection method. Strong because it turns time into the defender's advantage. Counterargument: storing and re-examining records is costly and widens the leakage surface, and detection years later may come too late to deter (footnote 4)."
feedback-instructions:: Name the argument whose reconstruction is thinnest, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 7e54933d-e0e0-43c2-9fbf-0c5dd85da56d
content:: **Question 7. Identify vulnerable positions** (choose one of Questions 3, 4, 7 or 9)

Identify at least four vulnerable positions in the author’s reasoning, including:

- one insufficiently supported empirical claim;
- one questionable inference or generalisation;
- one consequential technical assumption;
- one apparent contradiction or unresolved tension.

For each position:

- provide its exact location in the paper;
- explain the nature of the weakness;
- formulate a counterargument.

Where possible, use another proposition from the paper to challenge the position. If an apparent contradiction can be resolved, explain the resolution.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 22 for each of the four categories (an insufficiently supported empirical claim; a questionable inference or generalisation; a consequential technical assumption; an apparent contradiction or unresolved tension), within each 6: its exact location in the paper, 8: a diagnosis of the weakness, 8: a counterargument. 12: at least one position is challenged with another proposition from the paper, and the answer says whether the apparent contradiction can be resolved and how. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Empirical claim: the cost estimate for the taps rests on traffic being no more than two orders of magnitude above API traffic (5.1.1, open questions), but the author notes the actual composition of datacenter traffic is unknown; counterargument: if orchestration, file loads and multi-tenant traffic dominate, the taps and storage could cost far more than the 1 to 10 percent budget in 2c. Inference: if the system can detect whitelisted models used for blacklisted purposes, it can also detect non-whitelisted models or covert training (2b); but 5.1.1 says monitoring training needs much larger perimeters or compute-fabric taps that are not yet viable, so the generalisation from inference to training does not follow. Technical assumption: bit-exact replay from five logged properties (5.2.2), supported so far by a proof of concept on a 4B-parameter model; if replay is not exact, egress cannot be fully explained and the leftover freedom becomes a covert channel (5.2.2, first paragraph). Tension: 2c requires deployment in weeks or months and no unvalidated technology, yet several load-bearing parts do not exist yet: an FPGA-hardwired active warden has not been built (5.1.1), server-level memory probes are undemonstrated (5.1.2), and mass-manufacturable side-channel defenses are open (5.3.1). Partial resolution: the author presents a reference architecture to be red-teamed, treating the requirements as targets, and argues some gaps are engineering rather than new science (5.2.2); that resolves the tension only for those parts."
feedback-instructions:: Name the weakest entry, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 42b7feee-70e6-46af-b3f0-cd4f8ae03084
content:: **Question 8. Test a technically consequential claim** (optional)

Select one technically consequential claim that may be false, overstated, contested, or insufficiently supported.

- Give its exact location.
- Classify it as an established capability, proof of concept, inference from related technology, untested proposal, or under-specified aspiration.
- Evaluate it using a reliable external source or a complete technical argument.
- State what additional evidence would confirm or disconfirm the claim.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 10: a technically consequential claim with its exact location. 25: one of the five classifications (established capability, proof of concept, inference from related technology, untested proposal, under-specified aspiration) with a justification. 40: an evaluation grounded in a named reliable external source or a complete technical argument. 25: what additional evidence would confirm or disconfirm the claim. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the evaluation only restates the paper. Model answer, for the feedback, not a grading checklist: "Claim: zero-knowledge proofs can already be viable for sampled verification, anchored on zkLLM's 803 GPU-seconds per 13B-parameter forward pass and scaled to a 100 times larger model with an exponent of about 0.5 (5.2.4, Appendix A1). Classification: inference from related technology. zkLLM proves a 13B Llama model, not a frontier model or a mixture-of-experts system, and it proves a quantized, fixed-point version of the computation (the perplexity gap in footnote 23 comes from that), not the prover's floating-point kernels; the paper itself says emulating the reduction trees inside a proof is an open problem. Evaluation: the zkLLM paper (Sun, Li and Zhang, 2024) measured models only up to 13B, so the 0.5 exponent is fitted on a narrow range, and extrapolating two orders of magnitude outside it is unsupported; a proof of an approximate computation shows that a model like this one produced roughly this output, not that the declared run produced exactly the captured bytes, which is what the architecture needs to rule out covert channels. So the statistical tables are sound, but the price of n proofs at frontier scale is unknown. Confirming or disconfirming evidence: measured proving times on frontier-scale models, and a working proof that includes reduction-tree emulation with its overhead."
feedback-instructions:: Name the weakest step, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 15049c1d-8f2d-4631-9a6d-6c3208bf7a72
content:: **Question 9. Apply the architecture to a new case** (choose one of Questions 3, 4, 7 or 9)

A monitored facility declares that it operates a large-scale inference service. Its network records are committed as required. Randomly selected records can be opened, and the declared computations can be replayed successfully.

Using the proposed architecture, determine what this evidence establishes about:

- whether the declared computations occurred;
- whether the facility accurately described their purpose;
- whether all relevant activity on the monitored hardware was captured;
- whether prohibited activity occurred elsewhere inside or outside the monitored perimeter;
- whether a detected anomaly can be attributed to deliberate evasion.

Classify each conclusion as:

- established;
- supported but not established;
- not established.

Justify every classification with reference to the paper.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Score out of 100. 20 for each of the five conclusions, 10: a classification (established; supported but not established; not established) that fits what committed, replayable network records can reach, and 10: a justification that cites the relevant part of the paper. Committed and replayable records bear directly on whether the declared computations occurred, and progressively less on purpose, completeness of capture, activity outside the perimeter, and attribution of intent; a classification that departs from this earns its 10 when the justification argues it soundly. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Declared computations occurred: established for the opened records, since they hash to their commitments and replay reproduces the committed outputs (3.2.2); for the rest, supported with a statistical bound set by the sample size (Appendix A1). Purpose accurately described: supported but not established; replay proves what was computed, not what it was for; that needs semantic screening, which involves judgement calls and can be gamed (5.2.3), and the manifest's labels are the prover's own, unverified claims (3.1). All activity on the monitored hardware captured: not established; the commitments cover only what crossed the tap, and completeness rests on the premise that nothing bypasses it (3.2), on side-channel defenses (5.3.1), and on optional memory challenges and resource accounting (5.1.2, 5.3.2). Prohibited activity elsewhere, inside or outside the perimeter: not established; the records say nothing about hardware they do not cover, which only physical security, perimeter monitoring and inspection address (2b). An anomaly attributed to deliberate evasion: not established; a mismatch carries no label saying whether it was evasion, a bit flip or a software edge case, and the paper leaves the escalation procedure out of scope (2b, 3.2.2)."
feedback-instructions:: Name the classification least supported by its justification, then ask one follow-up question. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Cankaya, Naci. "A System Overview for Near-Term, Low-Trust AI Compute Verification." *Machine Intelligence Research Institute, Technical Governance Team*, June 2026. [techgov.intelligence.org](https://techgov.intelligence.org/research/a-system-overview-for-near-term-low-trust-ai-compute-verification)
*A working draft of a privacy-preserving, retrofittable system for verifying AI compute use between rival states, published to be argued with; each of its six technical sections closes with a set of questions for the reader.*

XLab. "3.0 A system overview for near-term, low-trust AI compute verification." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/covert-development/low-trust-compute-verification)
*The source lesson this page adapts.*
:::{>>{"author":"Elias's AI","timestamp":1788015610104}@@XLab's MemoDesk for this lesson (memos.ts slot m3-written-output) is unspecified: brief and audience are null, only "800 words, peer reviewed" and a gap note saying the outline never says which written output Module 3 gets. Nothing to import, so the "Import gap" placeholder is dropped rather than replaced with an invented memo prompt.<<}

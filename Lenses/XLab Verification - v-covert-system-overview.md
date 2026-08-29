---
id: '43f8c54c-e8ae-4f34-b497-12f532d37957'
title: "3.0 A system overview for near-term, low-trust AI compute verification"
tldr: {--{"author":"Elias's AI","timestamp":1788015564721}@@"Faithful alpha import of XLab lesson 3.0 A system overview for near-term, low-trust AI compute verification."--}{++{"author":"Elias's AI","timestamp":1788015564721}@@"Read one engineer's blueprint for checking a rival's AI compute without trusting them, then take it apart the way a reviewer would: state its problem, map its argument, trace evidence from chip to verdict, and find the step where the conclusion outruns the proof."++}
summary_for_tutor: "Imported from XLab's canonical Verification curriculum. Preserve source framing. {--{"author":"Elias's AI","timestamp":1788015564721}@@XLab currently blocks cross-site embedding,--}{++{"author":"Elias's AI","timestamp":1788015564721}@@The lens is a close-reading assignment on Naci Cankaya's paper 'A System Overview for Near-Term, Low-Trust AI Compute Verification' (MIRI Technical Governance Team). Nine questions: 1, 2 and 5 are required; 3, 4, 7 and 9 are marked optional++} so {--{"author":"Elias's AI","timestamp":1788015564721}@@linked external exercises --}{++{"author":"Elias's AI","timestamp":1788015564721}@@the learner can pick any one of them (they ++}must {--{"author":"Elias's AI","timestamp":1788015564721}@@be completed on XLab."--}{++{"author":"Elias's AI","timestamp":1788015564721}@@do at least one); 6 and 8 are optional. Every answer should cite a page or section of the paper and separate the author's claims from the learner's own conclusions. Do not summarise the paper for the learner; push them back to the text, check that reconstructed arguments name premises and conclusions, and treat well-reasoned disagreement with the author as success."++}
tags: [wip]{++{"author":"Elias's AI","timestamp":1788015564721}@@
duration_minutes: 15++}
---
#### Text
content::
In this module, you will tackle a comprehensive technical verification system proposal, synthesizing the verification mechanisms you learned in Module 2, actors and incentive structures you learned in Module 1, and verification intuitions you gained in Module 0.

{--{"author":"Elias's AI","timestamp":1788015568388}@@\## Learning objectives

---}{++{"author":"Elias's AI","timestamp":1788015568388}@@:::callout {title="By the end of this module, you will be able to:" tone="blue"}
1.++} Explain how the requirements of an international AI agreement might be translated into a technical verification system.
{--{"author":"Elias's AI","timestamp":1788015568388}@@---}{++{"author":"Elias's AI","timestamp":1788015568388}@@2.++} Understand and critique the assumptions, design choices, and unresolved problems involved in verifying AI compute use under conditions of limited trust between the parties.
{--{"author":"Elias's AI","timestamp":1788015568388}@@---}{++{"author":"Elias's AI","timestamp":1788015568388}@@3.++} Apply an existing compute verification regime to a realistic facility simulation, identifying weak points, evasion possibilities, and testable assumptions.{++{"author":"Elias's AI","timestamp":1788015568388}@@
:::++}

\## Assignment

Read Naci Cankaya’s working paper [A System Overview for Near-Term, Low-Trust AI Compute Verification](https://techgov.intelligence.org/research/a-system-overview-for-near-term-low-trust-ai-compute-verification).

Answer Questions 1, 2 and 5 together with one of Questions 3, 4, 7 or 9. Support each answer with page or section references to the paper.

Question 8 is an optional research task and may require consultation of an external technical source.

In your answers:

- distinguish the author’s claims from your own conclusions;
- reconstruct arguments by identifying their premises and conclusions;
- state explicitly when the available evidence does not justify a definite conclusion;
- formulate counterarguments in their strongest plausible form.

\## Questions

{--{"author":"Elias's AI","timestamp":1788015610104}@@\## --}{++{"author":"Elias's AI","timestamp":1788015610104}@@Read all 9 questions before beginning. Answer Questions 1, 2, 5, and any one question out of questions 3, 4, 7 or 9. Questions 6 and 8 are optional.

Support each answer with page or section references to [the paper](https://intelligence.org/wp-content/uploads/A-system-overview-for-near-term-low-trust-AI-compute-verification.pdf). Clearly distinguish the author’s claims from your own conclusions.

Questions 3, 4, 7 and 9 are marked optional below so that you can complete the lens with whichever one you choose; answer at least one of them.

#### Question: Open
id:: 217e8374-2817-43eb-951b-e347de1c6370
content:: **Question 1. Identify the principal problem** (required)

State in one sentence the principal problem that the author seeks to solve.
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Close reading of Cankaya's paper. Check that the answer is one sentence, names the problem the paper sets itself (verifying a rival state's AI compute use under low mutual trust, with near-term, retrofittable hardware) rather than a mechanism or a benefit, and cites a page or section. Distinguish the author's framing from the learner's own gloss. Do not over-validate; no generic praise.

#### Question: Open
id:: ff46a6f8-d7c3-45cf-bc6b-ae9e8d9235e2
content:: **Question 2. Reconstruct the proposed approach** (required)

Identify the principal propositions that constitute the author’s approach to low-trust AI compute verification.

Express each proposition in your own words and support it with a page or section reference. Explain the logical relationships among the propositions: which serve as assumptions, which describe mechanisms, and which state the intended results.
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Check that the learner lists several distinct propositions, each in their own words with a page or section reference, and sorts them into assumptions, mechanisms and intended results with the dependencies between them stated. Penalise paraphrase of the abstract without structure, missing references, and propositions that are the learner's conclusions rather than the author's. Name one missing or misclassified proposition, then ask one follow-up question. No generic praise.

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
assessment-instructions:: Check all five parts: premises and conclusion stated explicitly; two architectural choices named that actually rest on the argument; one premise picked as most vulnerable with a consequence traced; a counterargument in its strongest form; a reasoned verdict on prover versus verifier symmetry. Require page or section references. Reward the learner for separating the author's claims from their own. Name the weakest part, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 18ac6dc1-86be-42bf-9d00-c0b7d7c74e5d
content:: **Question 4. Examine the rejection of mutually trusted silicon** (choose one of ++}Questions{++{"author":"Elias's AI","timestamp":1788015610104}@@ 3, 4, 7 or 9)

Reconstruct the author’s argument against relying on general-purpose processors or AI accelerators that must be trusted by both parties.

- What reasons are given for rejecting this approach?
- How are analog controls, unilateral trusted computing bases, redundant computation, and output cross-checking intended to address the problem?
- Does the proposed architecture eliminate trust, reduce it, or redistribute it?
- Identify one strong and one vulnerable element of the argument. Formulate a possible objection to each.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Check that the learner states the paper's reasons for rejecting mutually trusted silicon, explains the role of each of the four named substitutes (analog controls, unilateral trusted computing bases, redundant computation, output cross-checking), takes a defended position on eliminate, reduce or redistribute, and gives one strong and one vulnerable element each with an objection. Require page or section references. Name the weakest part, then ask one follow-up question. No generic praise.++}

#### {--{"author":"Elias's AI","timestamp":1788015610104}@@Text--}{++{"author":"Elias's AI","timestamp":1788015610104}@@Question: Open++}
{++{"author":"Elias's AI","timestamp":1788015610104}@@id:: 70c2bc7d-7fb4-4a7e-a4a6-f39e79fc0cfd
++}content:: {--{"author":"Elias's AI","timestamp":1788015610104}@@**Interactive exercise:** XLab's `compute-verification` widget --}{++{"author":"Elias's AI","timestamp":1788015610104}@@**Question 5. Reconstruct the verification process** (required)

Represent schematically the complete verification process proposed in the paper, beginning with activity on monitored hardware and ending with the release of an evaluation result.

For each transition:

- identify the evidence or information transferred;
- identify which party or component produces, possesses, and evaluates it;
- state what conclusion the evidence is intended to support;
- identify any additional assumption required for that conclusion.

Identify one transition at which the stated conclusion may not follow from the available evidence.
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Check that the schematic runs end to end, from activity on monitored hardware to the release of an evaluation result, and that each transition ++}has {++{"author":"Elias's AI","timestamp":1788015610104}@@the four items: evidence transferred, who produces, holds and evaluates it, the conclusion it supports, and any extra assumption. Require one transition flagged where the conclusion may not follow, with a reason. Require page or section references. Penalise a prose summary of the system with ++}no {--{"author":"Elias's AI","timestamp":1788015610104}@@direct Lens equivalent yet. Complete--}{++{"author":"Elias's AI","timestamp":1788015610104}@@transitions. Name the transition most in need of work, then ask one follow-up question. No generic praise.

#### Question: Open
id:: dfa796c5-8851-4219-8891-2b3bea0a9f31
content:: **Question 6. Evaluate the strongest arguments** (optional)

Identify three arguments in the paper that you consider particularly strong.

For each argument:

- reconstruct++} it {++{"author":"Elias's AI","timestamp":1788015610104}@@independently of the author’s wording;
- explain why it is comparatively strong;
- formulate the strongest plausible counterargument.

The existence of a valid counterargument does not necessarily make an argument weak.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: Check for three distinct arguments, each reconstructed ++}in the {--{"author":"Elias's AI","timestamp":1788015610104}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/covert-development/low-trust-compute-verification). Its surrounding lesson text --}{++{"author":"Elias's AI","timestamp":1788015610104}@@learner's own words with a page or section reference, a reason it ++}is {--{"author":"Elias's AI","timestamp":1788015610104}@@preserved here.--}{++{"author":"Elias's AI","timestamp":1788015610104}@@comparatively strong, and a counterargument in its strongest form. Do not penalise an argument for having a counterargument. Name the argument whose reconstruction is thinnest, then ask one follow-up question. No generic praise.++}

#### {--{"author":"Elias's AI","timestamp":1788015610104}@@Text--}{++{"author":"Elias's AI","timestamp":1788015610104}@@Question: Open
id:: 7e54933d-e0e0-43c2-9fbf-0c5dd85da56d++}
content:: {--{"author":"Elias's AI","timestamp":1788015610104}@@**Import gap:** XLab persistent memo desk has --}{++{"author":"Elias's AI","timestamp":1788015610104}@@**Question 7. Identify vulnerable positions** (choose one of Questions 3, 4, 7 or 9)

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
assessment-instructions:: Check that all four categories are covered (empirical claim, inference or generalisation, technical assumption, contradiction or tension), each with an exact location, a diagnosis of the weakness, and a counterargument. Give credit where the learner uses one proposition from the paper against another. Penalise vague weaknesses with ++}no {--{"author":"Elias's AI","timestamp":1788015610104}@@clean Lens equivalent. Use --}{++{"author":"Elias's AI","timestamp":1788015610104}@@location. Name the weakest entry, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 42b7feee-70e6-46af-b3f0-cd4f8ae03084
content:: **Question 8. Test a technically consequential claim** (optional)

Select one technically consequential claim that may be false, overstated, contested, or insufficiently supported.

- Give its exact location.
- Classify it as an established capability, proof of concept, inference from related technology, untested proposal, or under-specified aspiration.
- Evaluate it using a reliable external source or a complete technical argument.
- State what additional evidence would confirm or disconfirm ++}the {--{"author":"Elias's AI","timestamp":1788015610104}@@[original XLab lesson](https://aisafetytracks.com/tracks/verification/covert-development/low-trust-compute-verification)--}{++{"author":"Elias's AI","timestamp":1788015610104}@@claim.
optional:: true
placeholder:: Cite the page or section you are answering from.
assessment-instructions:: This is a research task and may draw on an external technical source. Check++} for {++{"author":"Elias's AI","timestamp":1788015610104}@@an exact location, one of the five classifications with a justification, an evaluation grounded in a named reliable source or a complete technical argument, and a statement of confirming or disconfirming evidence. Penalise evaluations that only restate the paper. Name the weakest step, then ask one follow-up question. No generic praise.

#### Question: Open
id:: 15049c1d-8f2d-4631-9a6d-6c3208bf7a72
content:: **Question 9. Apply the architecture to a new case** (choose one of Questions 3, 4, 7 or 9)

A monitored facility declares that it operates a large-scale inference service. Its network records are committed as required. Randomly selected records can be opened, and the declared computations can be replayed successfully.

Using the proposed architecture, determine what ++}this {--{"author":"Elias's AI","timestamp":1788015610104}@@element.--}{++{"author":"Elias's AI","timestamp":1788015610104}@@evidence establishes about:

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
assessment-instructions:: Check that all five conclusions are classified as established, supported but not established, or not established, each with a justification that cites the paper. Expect the classifications to get weaker down the list: committed and replayable records bear directly on whether the declared computations occurred, and progressively less on purpose, completeness of capture, activity outside the perimeter, and attribution of intent. Penalise classifications with no reference. Name the classification least supported by its justification, then ask one follow-up question. No generic praise.++}

#### Text
content::
{--{"author":"Elias's AI","timestamp":1788015610104}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/covert-development/low-trust-compute-verification)*--}{++{"author":"Elias's AI","timestamp":1788015610104}@@:::callout {title="Works cited" tone="neutral" collapse="closed"}
Cankaya, Naci. "A System Overview for Near-Term, Low-Trust AI Compute Verification." *Machine Intelligence Research Institute, Technical Governance Team*, June 2026. [techgov.intelligence.org](https://techgov.intelligence.org/research/a-system-overview-for-near-term-low-trust-ai-compute-verification)
*A working draft of a privacy-preserving, retrofittable system for verifying AI compute use between rival states, published to be argued with; each of its six technical sections closes with a set of questions for the reader.*

XLab. "3.0 A system overview for near-term, low-trust AI compute verification." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/covert-development/low-trust-compute-verification)
*The source lesson this page adapts.*
:::{>>{"author":"Elias's AI","timestamp":1788015610104}@@XLab's MemoDesk for this lesson (memos.ts slot m3-written-output) is unspecified: brief and audience are null, only "800 words, peer reviewed" and a gap note saying the outline never says which written output Module 3 gets. Nothing to import, so the "Import gap" placeholder is dropped rather than replaced with an invented memo prompt.<<}++}

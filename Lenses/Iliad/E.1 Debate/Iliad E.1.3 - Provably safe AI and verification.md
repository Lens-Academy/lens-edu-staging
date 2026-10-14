---
id: '21cb4f59-2df9-4af6-bedd-bd44cbcfdd90'
title: "E.1.3 Provably safe AI and verification"
tldr: "Provably safe AI as a control and oversight idea, proof checkers such as Lean and their limits, and three example papers on verified AI to read and discuss."
summary_for_tutor: "Sections 5 and 6 of Iliad worksheet E.1: provably safe AI (a verifier gives guarantees on what an AI designed, used for control and for scalable oversight), proof checkers like Lean, why formal verification is limited to syntactic problems with small proofs, and why semantic oracles such as humans or trusted LLMs are needed. Contains the paper reading on verified AI (Lean, LTL planning, physics experiment design) and discussion prompts about world model, prover and verifier."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. Introduction to Provably Safe AI and AI Scientist

Provably Safe AI is the idea that we can combine a potentially misaligned AI with a verification system that gives us guarantees not on the AI itself, but on whatever the AI designed for us (e.g. a plan, software, a proof, a research proposal).

This has two applications for Safety:

1. Control: We can flag dangerous plans by a superintelligent AI before implementing them
2. Scalable Oversight: Verification $$\rightarrow$$ Better Training Signal $$\rightarrow$$ More Aligned AI

\### 5.1 Proof Checkers: When oversight works

A **mathematical proof checker** is a system that verifies whether a proposed proof is logically valid, step by step, relative to a fixed formal system. An example is Lean. You use it to write definitions, state theorems, and construct formal proofs that a small trusted kernel checks for correctness. It is based on dependent type theory and is used both for formalized mathematics and software verification.

But formal verification is limited to purely syntactic domains, and most problems are semantic, i.e., require world knowledge like "Water is wet", that needs to be checked by a semantic oracle, realistically either a trusted LLM or a human. Another limitation is that even in syntactic domains, proofs only work for solutions which can be verified with small (polynomially sized) proofs, so NP-type problems. More complicated problems, e.g. those involving other agents such as games or finance plans, cannot be verified with a small proof. So in the worst-case, we have an exponentially long proof with semantic inferences that need to be judged by humans. This makes the whole proof approach infeasible for a lot of tasks. The debate protocol aims to strongly reduce the size of the proof and the number of calls to a human judge.

\## 6. Scalable Oversight Goal - Paper Reading + Discussion

Examples of Verified AI:

- **Math/Code - Lean**: [Do LLMs Game Formalization? Evaluating Faithfulness in Logical Reasoning](https://arxiv.org/pdf/2604.19459)
- **Planning - LTL**: [VeriPlan: Integrating Formal Verification and LLMs into End-User Planning](https://arxiv.org/pdf/2502.17898v1)
- **Physics/Experiment Design:** [GRACE: an Agentic AI for Particle Physics Experiment Design and Simulation](https://arxiv.org/pdf/2602.15039)

[Readings slides Debate day iliad intensive](https://docs.google.com/presentation/d/1JMkgZZyPUG5zcpNEXGfc84xq0urL62r4O6-lnFvQGiw/edit?usp=sharing)

Discussion Prompts: What is the world model, prover, verifier in this setup? How much would you trust this verification process? How much ambiguity is there in the criteria that are verified? Is it clear that these map cleanly to what we actually want? How close is this to a real-world setting?

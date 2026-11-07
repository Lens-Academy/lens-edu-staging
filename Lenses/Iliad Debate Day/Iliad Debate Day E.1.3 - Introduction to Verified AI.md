---
id: '96070491-7898-4bf3-9a05-f6790631d4cb'
title: "E.1.3 Introduction to Verified AI"
tldr: "Verified AI as a control and oversight idea, with an untrusted AI as prover, a trusted verifier and a world model, proof checkers such as Lean and their limits, and four example papers on verified AI, of which you read one and discuss it."
summary_for_tutor: "Sections 5 and 6 of worksheet E.1: verified AI (a possibly misaligned AI acts as the prover, and a trusted verifier checks its output against a specification using a world model, used for control and for scalable oversight). The literature also calls this provably safe AI or guaranteed safe AI. If the learner uses those terms, treat them as the same idea, and point out that outside formal domains the check is not a proof. Also covers proof checkers such as Lean and the limits of formal verification (syntactic domains only, NP-sized proofs, semantic steps judged by an oracle), and the 10:30 paper session. Each learner reads one of four papers: two on maths and code with Lean (faithfulness of LLM formalization, a Rust-to-Lean verification pipeline) and two on physics (self-correcting AI physicists, PDE-grounded intent verification of simulation code). Then they discuss six prompts: the central claim, a concrete experiment, the world model, prover and verifier, trust in the verification, ambiguity in the verified criteria, and closeness to a real-world setting."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
---

#### Text
content::
\## 5. Introduction to Verified AI

Verified AI is the idea that we can combine a potentially misaligned AI with a verification system that gives us guarantees not on the AI itself, but on whatever the AI designed for us (e.g. a plan, software, a proof, a research proposal).

The setup has three parts. The untrusted AI is the **prover**: it produces the output together with a justification that the output meets a **specification**. A trusted **verifier** checks that justification against a **world model**, a representation of the parts of the world that matter for the specification. Depending on the domain, the verifier can be a proof checker, a test suite or a human judge. The guarantee is only as good as the specification and the world model.

The same idea appears in the literature as Provably Safe AI[^cite-tegmark-2023] and Guaranteed Safe AI.[^cite-dalrymple-2024] We use the name Verified AI because the specification does not have to be about safety (it can be the correctness of a proof or of a research conclusion), and because outside purely formal domains the check is not a proof.

[^cite-tegmark-2023]: Max Tegmark and Steve Omohundro (2023), *Provably safe systems: the only path to controllable AGI*, [arXiv](https://arxiv.org/abs/2309.01933)

[^cite-dalrymple-2024]: David Dalrymple et al. (2024), *Towards Guaranteed Safe AI: A Framework for Ensuring Robust and Reliable AI Systems*, [arXiv](https://arxiv.org/abs/2405.06624)

This has two applications for Safety:

1. Control: We can flag dangerous plans by a superintelligent AI before implementing them
2. Scalable Oversight: Verification $$\rightarrow$$ Better Training Signal $$\rightarrow$$ More Aligned AI

Read the description in this section for an intuitive idea, and for mathematical details and the exercises read the corresponding section in [Debate_Overview.pdf](https://drive.google.com/file/d/1KMqJDdFITy3YRz02oIfa4RctxP-h-ERF/view?usp=drive_link). You may also read any of the posts and papers that we link throughout this section.

\### 5.1 Proof Checkers: When oversight works

A **mathematical proof checker** is a system that verifies whether a proposed proof is logically valid, step by step, relative to a fixed formal system. An example is Lean. You use it to write definitions, state theorems, and construct formal proofs that a small trusted kernel checks for correctness. It is based on dependent type theory and is used both for formalized mathematics and software verification.

But formal verification is limited to purely syntactic domains, and most problems are semantic, i.e., require world knowledge like "Water is wet", that needs to be checked by a semantic oracle, realistically either a trusted LLM or a human. Another limitation is that even in syntactic domains, proofs only work for solutions which can be verified with small (polynomially sized) proofs, so NP-type problems. More complicated problems, e.g. those involving other agents such as games or finance plans, cannot be verified with a small proof. So in the worst-case, we have an exponentially long proof with semantic inferences that need to be judged by humans. This makes the whole proof approach infeasible for a lot of tasks. The debate protocol aims to strongly reduce the size of the proof and the number of calls to a human judge.

\## 6. Scalable Oversight Goal - Paper Reading + Discussion

Examples of Verified AI:

**Math/Code - Lean:**

::card[[../kim-do-llms-game-formalization-evaluating-faithfulness-in-logical-reasoning|Do LLMs Game Formalization? Evaluating Faithfulness in Logical Reasoning]]

::card[[../klaus-a-rust-to-lean-verification-pipeline-with-ai-provers-an-experience-report|A Rust-to-Lean Verification Pipeline with AI Provers: An Experience Report]]

**Physics/Experiment Design:**

::card[[../deng-towards-verifiable-and-self-correcting-ai-physicists-for-quantum-many-body-simulations|Towards Verifiable and Self-Correcting AI Physicists for Quantum Many-Body Simulations]]

::card[[../song-your-simulation-runs-but-solves-the-wrong-physics-pde-grounded-intent-verification-for-llm-generated-multiphysics-simulation-code|Your Simulation Runs but Solves the Wrong Physics: PDE-Grounded Intent Verification for LLM-Generated Multiphysics Simulation Code]]

**Discussion Prompts:**

1. What is the central claim of the paper?
2. Can you give an example of a concrete experiment?
3. What is the world model, prover, verifier in this setup?
4. How much would you trust this verification process?
5. How much ambiguity is there in the criteria that are verified? Is it clear that these map cleanly to what we actually want?
6. How close is this to a real-world setting?

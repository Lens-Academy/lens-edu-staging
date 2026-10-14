---
id: '8bf4b9b0-5820-4834-b6e6-db29876cff55'
title: "E.1.1 Overview and prerequisites"
tldr: "Prerequisites in computational complexity and Turing machines, what this worksheet teaches, and a suggested fast track."
summary_for_tutor: "Opening part of Iliad worksheet E.1 Scalable Oversight and Debate: prerequisites (Turing machines, P, NP, PSPACE, NP-completeness, reductions, oracle machines), the learning outcomes, and the fast track. The day timetable is hidden facilitator logistics and is not part of the student's work."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Prerequisites

- $$\bigstar$$ How Turing machines work ([Watch this Video](https://www.youtube.com/watch?v=gJQTFhkhwPA)), and a basic understanding of the idea of computational complexity ([Watch this video](https://www.youtube.com/watch?v=YX40hbAHx3s)), including the most important classes, P, NP, PSPACE, the notion of NP-completeness, and polynomial-time reductions, Oracle Turing machines.
- The difference between deterministic and non-Deterministic Turing machines, how mathematics is built on the axioms of set theory (used for most mathematics) or type theory (used mostly for proof checkers).

:::callout {title="What you'll learn" tone="neutral"}

- The basic idea of Provably Safe AI as both a Control and a Scalable Oversight Technique
- The difference between syntactic and semantic problems and why a world model is necessary to turn semantics into syntax.
- Different ideas of world models: Human judgement, Davidad-style world models, hardware specifications
- Why Debate could drastically reduce the queries to the world model/human oversight
- Secondary Debate concepts: Cross-Examination,
- Are familiar with the UK AISI safety case, and are able to defend/critique it.

:::

%% Facilitator logistics (hidden from learners):
\## 2. Roadmap for today

Here we outline how the material was taught in-person in April:

- **10:00 — Fun Game** Fun exercise "Wrong but convincing proofs". In this exercise, a series of wrong proofs is presented and the students are asked to find the mistake in the proof. The students basically take the role of "Bob" who points out the flaws in Alice's proofs. This gives an intuition that even mathematical proofs can sound very convincing, and finding a mistake as a human judge is often non-trivial. (Section 4)
- **10:20 — Introduction to Provably Safe AI and AI Scientist** Introduction of "Provably Safe AI" as a Control and Oversight program. Introduces the ideas of World Model Prover Verifier
- **10:30 — Scalable Oversight Goal - Paper Reading + Discussion** (Section 6)
- **11:30 — Introduction to AIS via Debate** This part is an In-depth explanation of the main formalisms of debate and cross-examination. This includes Formal Definition of the Debate setup Proof sketches for the hardness-reduction for PSPACE and NEXP respectively.
- **12:30 — Lunch Break**
- **13:30 — Cross Examination + Exercises** We do CX and the exercises from [Debate_Overview.pdf](https://drive.google.com/file/d/1KMqJDdFITy3YRz02oIfa4RctxP-h-ERF/view?usp=drive_link) (Section 13)
- **14:30 — Pause**
- **14:40 — Obfuscated Arguments and Prover Estimator Debate** (Section 17)
- **15:10 — Judge Models - Introduction**
- **15:15 — Talk: Alexander Heckett - Debate on Graphs**
- **16:00 — Pause**
- **16:10 — Reading and Discussion "Experimental Results"** (Section 19)
- **17:10 — Presentation:** [The AI safety case of the AISI](https://arxiv.org/pdf/2505.03989) (Section 20)
- **17:40 — Debate**: Is AIS via Debate research more capability than alignment?
- **18:00 — End**
%%

\## 3. Fast Track

To get a high-level understanding of debate quickly, simply go through the description of debate in the main content and ask a language model of your choice to help you understand.

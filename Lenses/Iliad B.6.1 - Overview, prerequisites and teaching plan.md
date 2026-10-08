---
id: '6db252a3-c129-40f6-827a-11b6082058b5'
title: "B.6.1 Overview, prerequisites and teaching plan"
tldr: "The prerequisites, learning outcomes and the one-day teaching plan for the notes, followed by an intro reading on learning mechanics with three discussion questions."
summary_for_tutor: "This is the opening of Iliad worksheet B.6 Physics of Deep Learning: Prerequisites (section -1) with the 'What you'll learn' box, section 0 (one-day teaching plan, main references; the timetable is hidden) and section 1, the intro reading on learning mechanics. Section 1 asks the student to read Section 2 only of Simon et al. 2026 and discuss three prompts: ranking the physics analogies in Table 1, the Discretization Hypothesis, and what matters for alignment."
authors:
  - Aleksander Czejdo
  - Tudor Dimofte
  - Brianna Grado-White
  - Charles Renshaw-Whitman
source_url: https://iliad-intensive.org/learning/qft/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
**Contents**

- -1. Prerequisites
- 0. A one-day teaching plan
  - 0.1 Schedule
  - 0.2 Main references
- 1. Intro reading: learning mechanics
- 2. Statistical mechanics of learning
  - 2.1 The Bayesian model of learning
  - 2.2 Why the exponential of a loss is a likelihood
  - 2.3 Partition functions, free energy, and cumulants
  - 2.4 A physics example: the Ising model
  - 2.5 Phases and phase transitions
  - 2.6 The Ising perceptron: a first-order transition in learning
  - 2.7 Comparison with QFT
- 3. Large width at initialization: the Gaussian process limit
  - 3.1 Notation
  - 3.2 Normalizing the network
  - 3.3 Gaussian processes
  - 3.4 The NNGP correspondence
  - 3.5 NNGP via functional integrals
  - 3.6 L/N
  - 3.7 Edge of chaos
- 4. The NTK and large width during training
  - 4.1 Gradient flow and the NTK
    - 4.1.1 Geometry of gradient flows
  - 4.2 Features
  - 4.3 Constant NTK at large width
  - 4.4 Lazy learning
  - 4.5 Summary
  - 4.6 Bayesian learning at large width: kernel learning
- 5. Mean-field scaling
  - 5.1 Mean-field theories in physics
    - 5.1.1 Warm-up: the Curie–Weiss magnet
    - 5.1.2 The general shape of a mean-field model
  - 5.2 Mean-field scaling for one-hidden-layer networks
    - 5.2.1 Initialization
    - 5.2.2 The loss is a mean-field energy
    - 5.2.3 Equations of motion and the mean field
    - 5.2.4 From particles to measures: the continuity equation
    - 5.2.5 The McKean–Vlasov equation and self-consistency
  - 5.3 The NTK is no longer constant: feature learning
  - 5.4 The scaling dial and Maximal Update Parameterization
  - 5.5 What is this framework good for?
  - 5.6 Grokking as a lazy-to-rich transition: a reading exercise
  - 5.7 Bayesian grokking: a first-order transition (alternative reading)
- 6. Non-equilibrium physics, MSRJD, and DMFT
  - 6.1 From stochastic dynamics to path integrals: the MSRJD formalism
  - 6.2 Double descent as a dynamical phase transition
    - 6.2.1 Model definition and formalism
    - 6.2.2 Overview of results via training and generalization error
  - 6.3 Dynamical mean-field theory (DMFT)
    - 6.3.1 Self-consistency
    - 6.3.2 Recent applications in deep learning
- 7. Scaling laws
  - 7.1 The empirical laws
  - 7.2 Joint laws, bottlenecks, and the Chinchilla revision
  - 7.3 Where do the laws come from?
  - 7.4 A survey of theoretical proposals
  - 7.5 The quantization model: exponents from the statistics of skills
  - 7.6 Emergence: smooth laws from staggered cliffs
  - 7.7 Exponents from geometry and from spectra
    - 7.7.1 Geometry: the data-manifold argument
    - 7.7.2 Spectra: scaling laws from kernel eigenvalues
  - 7.8 A solvable large-N field theory
  - 7.9 All the knobs at once: a dynamical theory
  - 7.10 Beyond pretraining: post-training and test-time scaling
- A. The replica method
  - A.1 What the annealed approximation gets wrong
  - A.2 Replicas
  - A.3 A variant: the spherical perceptron
- B. From linear regression to kernel regression
  - B.1 Linear regression
  - B.2 Linear regression with nonlinear features
  - B.3 Kernel regression
  - B.4 Kernel ridge regression
  - B.5 Linearized networks are kernel ridge regressors
- C. Solutions to exercises

\## -1. Prerequisites

We don't assume any physics background, though reading some of the suggested reference material may be helpful. We do assume:

- a basic understanding of probability theory and Bayesian inference;
- familiarity with simple neural networks (MLP's);
- undergraduate-level calculus and linear algebra;
- and, in a few places, differential geometry.

:::callout {title="What you'll learn" tone="neutral"}

By the end of these notes, you should be able to:

- Use the statistical-mechanics dictionary for Bayesian learning — energy, entropy, partition function, free energy, cumulants, order parameters, quenched averages — and explain why the exponential of a loss function is a likelihood.
- Solve the Ising model in the mean-field approximation; explain what a phase transition is, why finite systems show smooth sigmoids and growing susceptibility peaks instead of true kinks, and how the Ising perceptron realizes a first-order transition to perfect generalization, metastable lag included.
- Derive the Gaussian-process description of a wide network at initialization, and explain the roles of the fan-in normalization, the depth-to-width ratio, and the edge of chaos.
- Derive the NTK, and explain why it freezes at large width — so that training reduces to kernel regression, with no feature learning.
- Derive, heuristically, the mean-field limit of one-hidden-layer networks — neurons as interacting particles, self-consistency, the McKean–Vlasov equation — and explain how its *moving* kernel encodes feature learning; place the NTK and mean-field limits on the scaling dial, and connect it to $$\mu$$P and hyperparameter transfer.
- Compare the two theoretical accounts of grokking — an equilibrium first-order transition vs. delayed lazy-to-rich dynamics — and propose an experiment that would distinguish them.
- Recognize the MSRJD/DMFT path-integral formulation of training dynamics, the role of correlation and response functions, and double descent as a dynamical phase transition.
- Derive the three scaling laws of the quantization model, explain "emergence" as the aggregation of staggered cliffs, and survey where scaling exponents come from: skill statistics, data geometry, and kernel spectra.

:::

\## 0. A one-day teaching plan

These notes contain far more than can be taught in a day. This section records one selection of material that was taught in a single day at the Iliad Intensive (September 2026, day B.6), as a worked example of how the notes can be used. The day alternates three lectures, given from the slide deck that accompanies these notes, with exercise sessions in which participants pick one exercise from the notes and work on it, alone or in small groups. It closes with a short reading and a discussion.

The deck is the file `slides.tex` in the same folder as these notes. The website build compiles it and offers it in the "Slides" row at the top of this chapter's web page; it can also be opened directly at [iliad-team.github.io/iliad-intensive/downloads/qft/qft-slides.pdf](https://iliad-team.github.io/iliad-intensive/downloads/qft/qft-slides.pdf). Its three parts are the three lectures below: frames 1–20 (Part I), 21–41 (Part II), and 42–52 (Part III). The lectures deliberately leave derivations to the exercise sessions, so the deck is sparse by design; the corresponding sections of these notes fill in what the slides state.

%% Facilitator logistics (hidden from learners):
\### 0.1 Schedule

| **time** | **session** | **where in these notes** |
| --- | --- | --- |
| 10:00–11:00 | Lecture, Part I: Bayesian learning and phase transitions | Sections 2.1–2.5 |
| 11:00–11:15 | Break |  |
| 11:15–12:00 | Exercises, Part I (choose one) | Exercises 2.1, 2.2 and 2.3 |
| 12:00–12:30 | Lecture, Part IIa: large width at initialization; the NTK | Sections 3.1–3.4, Section 3.6, Sections 4.1–4.2 |
| 12:30–1:30 | Lunch |  |
| 1:30–2:00 | Lecture, Part IIb: large width during training; mean-field scaling | Sections 4.3–4.4, Sections 5.2–5.4 |
| 2:00–3:00 | Exercises or lab, Part II (choose one) | Exercises 3.3, 4.5, 4.4 and 5.3 |
| 3:00–3:45 | Lecture, Part III: neural scaling laws, in theory and practice | Sections 7.1–7.5 |
| 3:45–4:15 | Break |  |
| 4:15–5:00 | Exercise, Part III | Exercise 7.1 |
| 5:00–5:30 | Reading on "learning mechanics" | Section 1 |
| 5:30–5:50 | Discussion in small groups | the prompts of Section 1 |
| 5:50–6:00 | Feedback |  |
%%

\### 0.2 Main references

The day is based on the following references, all of which appear elsewhere in these notes. For Part I: Tong's lectures on statistical field theory and on kinetic theory (Tong 2012; Tong 2012), the physics behind the lecture; Engel and Van den Broeck (Engel & Van den Broeck 2001) for the perceptron tradition; and Gyorgyi (Gy"orgyi 1990) for the Ising perceptron transition. For Part II: Hanin's lectures (Hanin 2026) and Roberts, Yaida, and Hanin (Roberts et al. 2022) on large-width limits and the $$L/N$$ expansion; Ringel et al. (Ringel et al. 2025) on statistical field theory in deep learning; Spiliopoulos, Sowers, and Sirignano (Spiliopoulos et al. 2025) for rigorous NTK and mean-field limits; Lin (Lin 2025) for experiments identifying features through the empirical NTK; and the two accounts of grokking (Kumar et al. 2024; Rubin et al. 2024), which were not lectured but are the natural follow-up reading (Sections 5.6 and 5.7). For Part III: Kaplan et al. (Kaplan et al. 2020) and Henighan et al. (Henighan et al. 2020) for the empirical laws; Hoffmann et al. (Hoffmann et al. 2022) and Porian et al. (Porian et al. 2024) for Chinchilla and the reconciliation with Kaplan; Michaud et al. (Michaud et al. 2023) for the quantization model; and Maloney, Roberts, and Sully (Maloney et al. 2022) and Bordelon, Atanasov, and Pehlevan (Bordelon et al. 2024) for the solvable field theories.

A complementary introduction to the physics of learning, taught at the August 2026 Intensive by Renshaw-Whitman, can be found in (Renshaw-Whitman 2026); Appendix B is adapted from it.

\## 1. Intro reading: learning mechanics

The review (Simon et al. 2026) argues that a scientific theory of deep learning — a "mechanics of learning" — is already emerging, and it organizes the evidence into five converging strands: analytically solvable settings, insightful limits, simple empirical laws, disentangled hyperparameters, and universal phenomena. The body of the paper develops the first two strands in detail and samples the remaining three. These notes will do much the same, so it is worth keeping the five strands in mind as a map of everything that follows.

The paper's starting observation deserves to be savored, because it sets the tone for the whole subject. A deep learning system is completely specified by four explicit ingredients: an architecture (a composition of simple linear and nonlinear maps), a dataset, an objective, and a learning rule (gradient-based updates from a random initialization). Nothing is hidden: every parameter, every gradient, every intermediate activation can be measured, at every step, to whatever precision we like. In the language of the reading, deep learning directly exposes its own equations of motion — *the central challenge is not opacity but complexity*. This places the field in very different territory from the genuinely opaque sciences: in neuroscience or cell biology the microscopic equations of motion are unknown and the state is largely unmeasurable, while in high-energy physics we must infer the microscopic laws indirectly, from scattering amplitudes. The better analogy is fluid dynamics: there, too, we possess the microscopic law — for deep learning, the update equation is five lines of code — and what is missing is the *effective* description, the analogue of Navier–Stokes.

Read **Section 2** (only) of (Simon et al. 2026), and think about the following:

1. *Rank the physics analogies in Table 1 of the reading* (solvable models $$\leftrightarrow$$ hydrogen atom; limits $$\leftrightarrow$$ thermodynamic limit; empirical laws $$\leftrightarrow$$ Kepler and Planck; hyperparameters $$\leftrightarrow$$ Reynolds number; universality $$\leftrightarrow$$ critical phenomena). Which are the most compelling? Which do you think are most useful in understanding deep learning?
2. *Discretization and other approximations.* The reading's Discretization Hypothesis proposes that practical networks are best understood as noisy, finite approximations to models of infinite size — like a finite-difference discretization of a PDE — so that finite-size effects typically *cost* performance rather than enable it. Given what you've seen so far, does this seem accurate? The hypothesis is falsifiable: it would be refuted by a finite-size effect that delivers a general benefit unachievable in any limit. What are some possible experiments/setups that could falsify it?
3. *What actually matters for alignment?* The reading wants falsifiable, quantitative, *average-case* predictions rather than worst-case bounds — physics rather than classical learning theory. What is lost? E.g. for alignment, does one want worst-case guarantees or forecasting of typical capabilities? Which of the five lines of evidence is most relevant for alignment?

You may want to revisit these questions at later stages as you go through these notes, and learn more about physics-inspired approaches in deep learning.

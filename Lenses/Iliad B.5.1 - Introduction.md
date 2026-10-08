---
id: '370783f7-e858-4c5e-9653-35f8d34f3a57'
title: "B.5.1 Introduction"
tldr: "Contents of the notes, the five parts and how they connect, the assumed background in linear algebra, calculus, probability and deep learning, and three fast-track routes."
summary_for_tutor: "Introduction of Iliad worksheet B.5 Data Attribution: table of contents, outline of sections 1 to 5 (counterfactuals, influence functions, Bayesian influence functions, unrolling, practical considerations), prerequisites, optional link to the singular learning theory day, and three fast-track routes through the material. No exercises."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
**Contents**

- Introduction
- 1\. Causality and Counterfactuals
  - 1.1 Data attribution as causal analysis
  - 1.2 Counterfactual attribution and its failures
  - 1.3 Beyond leave-one-out: Shapley values
  - 1.4 Notation and goals
- 2\. Influence Functions
  - 2.1 The influence function formula
  - 2.2 Translation to modern neural networks
- 3\. Bayesian Influence Functions
  - 3.1 Bayesian influence functions
  - 3.2 Exercise: Connecting Bayesian and classical influence functions
  - 3.3 Long Exercise: Influence functions as optimal linear transport
- 4\. Unrolling
  - 4.1 The training-dynamics approach to attribution
  - 4.2 The unrolling formula
    - 4.2.1 Materializing the Jacobian
    - 4.2.2 Implicit JVPs and the REPLAY algorithm
  - 4.3 Long Exercise: From unrolling to influence functions
  - 4.4 Exercise: Influence depends on training time
- 5\. Practical Considerations and Open Problems
- 6\. Further Readings

\## Introduction

**Contents.**  These notes are structured as follows:

1. **Causality and Counterfactuals** motivates the problem of data attribution through the lens of causal reasoning, exhibiting the shortcomings of naive counterfactual approaches.
2. **Influence Functions** introduces the classical theory of influence functions for statistical models and discusses their translation to modern neural networks.
3. **Bayesian Influence Functions** introduces susceptibilities and Bayesian influence functions, connecting them to the classical theory via a power series expansion.
4. **Unrolling** presents the training-dynamics approach to attribution, deriving the basic formula and connecting it to influence functions in the appropriate limit.
5. **Practical Considerations and Open Problems** discusses distributional versus single-model attribution, entangled latent concepts, and the distinction between similarity metrics and genuine attribution.

**Prerequisites.**  We assume the following background, most of it standard for a machine-learning audience.

- *Linear algebra*: vectors, matrices, inner products, eigenvalues, quadratic forms, Hessians.
- *Multivariable calculus*: gradients, the chain rule, Taylor expansion, the implicit function theorem.
- *Probability*: expectations, conditional probability, Bayes' rule, Gaussian distributions.
- *Deep learning basics*: stochastic gradient descent, empirical risk minimisation, a standard supervised training loop.

Familiarity with the material from the singular learning theory tutorial (degeneracy, the local learning coefficient, posterior broadening) is useful but not required. We flag connections to the SLT day in remarks as they arise.

**Fast-track.**  There is more material here than comfortably fits into a single day. Readers short on time may prefer one of the following routes; each is self-contained.

1. *From classical to modern influence functions.* Skim Section 1 for motivation, then read Section 2 in full, including the derivation exercise.
2. *The Bayesian perspective.* Read Section 2.1 for the influence function formula, then Section 3 in full. The connection exercise (Section 3.2) is the conceptual payoff.
3. *Training-dynamics attribution.* Skim Section 2, then read Section 4 in full. The long exercise in Section 4.3 recovers the influence function as a limit of unrolling.

All three routes depend on the motivational material in Section 1. If reading only one section, read that one.

**Acknowledgements.**  This tutorial was developed for the April 2026 Iliad Intensive and its template was inspired by the SLT day. Exercises and examples adapted from specific sources are credited inline.

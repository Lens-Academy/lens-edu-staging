---
id: '362cd9fe-e0c9-47e0-9cf5-a23b33317722'
title: "B.3.1 Introduction"
tldr: "Introduces singular learning theory and degeneracy in neural networks, outlines the four technical sections and prerequisites, and gives a fast-track route through the exercises."
summary_for_tutor: "This is the introduction to worksheet B.3 (singular learning theory). It explains degeneracy (via the mathematical and biological meanings of the word), lists the sections (preliminaries, what is degeneracy, the degeneracy hierarchy and the local learning coefficient, degeneracy and Bayesian deep learning, further readings), the prerequisites, and a fast-track list naming the exercises to do (2.1, 2.2, 2.9 or 2.10, 2.14 and/or 2.15, 3.1, 3.2, 3.4, 3.7, 3.10, 4.2). It contains no exercises itself and has an embedded video, Deep Learning Is Singular - Here's What That Means."
authors:
  - Kai Ogden (University of Oxford)
  - Matthew Farrugia-Roberts (University of Oxford)
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/singular-learning-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
**Contents**

- Introduction
- 1. Preliminaries
  - 1.1 Neural networks and parameter–function maps
  - 1.2 Supervised deep learning and loss functions
  - 1.3 Statistical models and parameter–distribution maps
  - 1.4 Bayesian deep learning
- 2. What is degeneracy?
  - 2.1 A definition of degeneracy
  - 2.2 Degeneracy and continuous symmetries
  - 2.3 Localised degeneracy
  - 2.4 Degeneracy and information singularities
  - 2.5 Degeneracy and the loss landscape
- 3. The degeneracy hierarchy
  - 3.1 The local learning coefficient via volume scaling asymptotics
  - 3.2 Perspectives on the local learning coefficient
  - 3.3 Local learning coefficients of deep linear networks
- 4. Degeneracy and Bayesian deep learning
  - 4.1 Watanabe's free energy formula
  - 4.2 Bayesian phase transitions
- 5. Further readings
  - 5.1 Other introductions to singular learning theory
  - 5.2 Recent work on singular deep learning

#### Video
source:: [[../video_transcripts/iliad-deep-learning-is-singular-heres-what-that-means]]

#### Text
content::
> *Thou shalt have the power to degenerate*
>     —*On the Dignity of Man,* 1496

\## Introduction

*Singular learning theory (SLT)* is a theory of learning that accounts for *degeneracy* in neural networks. What is degeneracy? Let us first appeal to the Cambridge dictionary, documenting some features of typical uses of the word within mathematics:

> *Degenerate* (of an equation, curve, line, etc.) unusual or complicated in some way compared to other equations, curves, lines, etc.  of a similar type, especially because a variable or parameter is zero.

On the other hand, we should recall that deep learning has as many roots in neuroscience as in mathematics. And as they say, "neural networks are *grown.*" Perhaps we should also hear the biologist's definition:

> *Degenerate* (of an organism, chromosome, etc.) simpler than a form that previously existed because of no longer having a particular structure.

Actually, *both* of these definitions are apt. Within a typical neural network architecture, certain weight vectors correspond to neural networks from simpler architectures (often due to certain weights being zero). Structurally, these neural networks are simpler in form than their neighbours. Mathematically, they complicate the relationship between the neural network's parameter space and the resulting space of functions. In turn, learning in neural networks is substantially richer than learning in classical statistical models.

Singular learning theory is a framework for understanding learning that places degeneracy at the centre. The framework leverages powerful tools from algebraic geometry to understand, characterise, and resolve degeneracies, revealing their impact on learning. Unfortunately, the price of this mathematical power is that following the research literature without a deep background in pure mathematics is challenging.

That is where this tutorial comes in. We aim to distil the essence of singular learning theory—the notion of degeneracy and its role in learning—laying bare through simple examples and structured exercises the core intuitions driving research in the field. We believe understanding this essence requires no more than undergraduate-level mathematics. Moreover, to anyone armed with these core intuitions, understanding and contributing to research on the relationship between degeneracy and deep learning is within reach.

**Contents.**  Specifically, the tutorial comprises the following four technical sections, each with definitions and guided exercises.

1. "Section 1" reviews core deep learning concepts, defining our notation and some running examples. The central concept is that of the parameter–function map.
2. "Section 2" defines degeneracy of parameter–function maps and relates it to symmetries, singularities of the Fisher information, and degenerate critical points of the loss landscape.
3. "Section 3" derives the local learning coefficient (LLC) as a quantitative measure of the degree of degeneracy of a critical point via a volume scaling approach, and surveys several other perspectives on the quantity.
4. "Section 4" presents Watanabe's free energy formula connecting the LLC to Bayesian learning and discusses its implications.

We conclude with Section 5, providing pointers for further study and surveying the literature on SLT and deep learning.

**Prerequisites.**

The following is an indicative list of mathematical concepts that will be helpful for reading the tutorial and completing the exercises.

- *Linear algebra:* vectors, matrices, rank, orthogonal matrices, rank–nullity, positive definiteness, eigenvalues, spectral decomposition.
- *Calculus:* partial derivatives, gradient, directional derivative, chain rule, Hessian, second-order Taylor expansion and remainder.
- *Integration and analysis:* multivariate integrals, change of variables, volume in $${\mathbb{R}}^{d}$$, asymptotic notation (big-$$O$$, little-$$o$$), computing basic limits and integrals.
- *Probability:* probability simplex $$\Delta(\cdot)$$, conditional probability, probability density functions, independence, expectation, Bayes' rule, Gaussians, law of large numbers.

Section 1 reviews the basic framework of deep learning as parametric function approximation or statistical inference (parameter–function maps, deep linear networks, multi-layer perceptrons, loss functions, likelihood) along with Bayesian inference (prior, posterior, partition function, Bayesian free energy).

Readers with more advanced backgrounds may appreciate occasional references to topics from algebraic geometry, fractal geometry, or statistical physics. However, these references are tangential and readers without these backgrounds can safely skip them.

**Fast-track.**

To paraphrase Euclid, there is no royal road to algebro-geometric learning theory. However, it is possible to get a bird's-eye view and the most important intuitions in a comparably short time. If this is what you are looking for, we recommend the following route through the tutorial. Assuming you are already somewhat comfortable with deep learning and Bayesian inference, skip Section 1, and refer back only as needed. Then, proceed as follows.

1. To understand parameter–function map versus loss landscape degeneracy: Read Section 2.1 and complete Exercises 2.1 and 2.2. Complete either Exercise 2.9 or Exercise 2.10. Read Section 2.5 and complete your choice of Exercise 2.14 and/or Exercise 2.15.
2. To understand the local learning coefficient via volume scaling: Read Section 3.1 and complete Exercises 3.1, 3.2, 3.4 and 3.7. Read Section 3.3 and Exercise 3.10.
3. To understand the relation between degeneracy and learning in the Bayesian case: Read all of Section 4 (it is shorter). Complete Exercise 4.2.

Once you are done, we hope you will consider taking the scenic route some other time.

**Acknowledgements.**

This tutorial was developed for the April 2026 Iliad Intensive. Some exercises were adapted from Furman 2024.

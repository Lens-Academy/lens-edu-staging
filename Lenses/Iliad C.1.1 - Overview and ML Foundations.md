---
id: 'b0c84c53-c95b-40a7-8be1-8a572b05d33f'
title: "C.1.1 Overview and ML Foundations"
tldr: "Prerequisites, learning outcomes and outline of the day, a fast-track route, and the ML Foundations track: lecture materials, Colab exercises and the topics covered, from training loops to the LLM lifecycle."
summary_for_tutor: "Opening of Iliad worksheet C.1 Intro to ML Engineering: prerequisites (python, ML basics, laptop with Claude Code CLI, linear algebra and gradient descent), learning outcomes, outline of the two parallel lectures, fast track, and the ML Foundations section (Lecture 1a repository, Colab exercises on PyTorch basics, optimizers, architectures, TensorFlow Playground, MLP, attention, RLHF, and a content list from training loop to LLM lifecycle). The Colab and GitHub links are materials to open, not readings. No worked solutions."
authors:
  - Julian Schulz (Meridian Research)
  - Adam Newgas (Timaeus)
source_url: https://iliad-intensive.org/interpretability/intro-to-ml-engineering/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Prerequisites

* You should have some rudimentary ability to code in python
* You should have heard of the ML basics before
* You should have your own laptop with Claude Code CLI installed
* You should know linear algebra and understand gradient descent

:::callout {title="What you'll learn" tone="neutral"}

* ML Foundations 
  - Learn the ML basics needed for the rest of the course
  - Give some hands on experience with common ML Libraries/methods
  - Understanding and building the transformer architecture
* Practical ML
  - Renting out and setting up your own compute
  - Use common ML Libraries/methods
* Claude Code for Research
  - Learn how to use Claude Code in research projects
  - Get a good basic setup to make use of multiple Claude Code instances across different branches and projects

:::

**Outline**

We start with two parallel lectures: One lecture for participants with less ML background, where we go through ML and LLM basics, and go deeper into certain topics via hands on exercise notebooks. The second lesson is a practical exercise of renting out and setting up your own compute.

Lecture 2 is a series of exercises to use Claude Code to do small steps in an AI safety research repo, where each step should be done using a different Claude Code tool.

\## Fast track

* Go over the slides for ML Foundations. Skip the section you are familiar with. Read the ones you are not familiar with. If you have time do one of the Colab exercises.
* Download the Claude Code CLI, and play around with it, to get familiar with its basic features

\## ML Foundations

ML and LLM basics for participants with less ML background, going deeper into selected topics through hands-on exercise notebooks.

Lecture notes and materials for Lecture 1a are self-contained within this repository: [https://github.com/iliad-team/iliad-intensive-C.1.1](https://github.com/iliad-team/iliad-intensive-C.1.1)

Colab Exercises:

* [Pytorch Basics](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.1.1/blob/main/lectures/01_a_ml_foundations/exercises/01_pytorch_basics/notebook.ipynb)
* [Optimizers](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.1.1/blob/main/lectures/01_a_ml_foundations/exercises/02_optimizers/notebook.ipynb)
* [Architectures](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.1.1/blob/main/lectures/01_a_ml_foundations/exercises/03_architectures/notebook.ipynb)
* [Tensorflow Playground](https://playground.tensorflow.org/)
* [MLP](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.1.1/blob/main/lectures/01_a_ml_foundations/exercises/04_mlp/notebook.ipynb)
* [Attention](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.1.1/blob/main/lectures/01_a_ml_foundations/exercises/05_attention/notebook.ipynb)
* [RLHF](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.1.1/blob/main/lectures/01_a_ml_foundations/exercises/06_rlhf/notebook.ipynb)

Content:

* Training loop — forward/backward pass, gradient descent, stochastic batching, optimizer role
* PyTorch tensors — basic operations, einops, batching & data loading, autograd/computational graph, devices & GPU
* Loss functions — classification losses, RL/human-rater losses, train vs. test loss, over/underfitting
* Parameters, activations & hyperparameters — terminology + optimizers (momentum, RMSProp)
* Architectures — activation functions, universal approximation, over/underparameterization, symmetries in architecture design, CNNs, transformers, residual streams
* Hyperparameter optimization — sweeps, scaling laws
* LLM lifecycle - Pretraining, SFT fine tuning, RLHF, RLVR

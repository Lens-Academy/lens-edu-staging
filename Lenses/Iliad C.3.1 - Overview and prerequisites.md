---
id: '8490e2b3-71b7-4f8d-9ab0-9d551aef5a1b'
title: "C.3.1 Overview and prerequisites"
tldr: "The prerequisites for computational mechanics, the learning outcomes of the module, and a fast-track reading on belief state geometry in transformers."
summary_for_tutor: "This is the opening of Iliad worksheet C.3 Computational Mechanics: prerequisites (mechanistic interpretability, linear probes, row-stochastic matrices, Bayes' rule, the probability simplex), the 'What you'll learn' list (HMMs, GHMMs, belief states, mixed state presentation) and the Fast-track reading of 'Transformers represent belief state geometry in their residual stream' with its guiding questions. The day schedule is hidden from learners."
authors:
  - Xavier Poncini (Simplex)
  - Adam Shai (Simplex)
  - Paul Riechers (Simplex)
source_url: https://iliad-intensive.org/interpretability/computational-mechanics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Prerequisites

Familiarity with the goals and basic methodology of mechanistic interpretability, including the notions of features and circuits; the linear representation hypothesis; linear probes as a method for reading off internal representations; and a basic understanding of the transformer architecture.

Students should be comfortable with the idea that one can train a linear map from model activations to some target structure and evaluate its quality (e.g. via MSE or $$R^{2}$$).

**Mathematical background.** The module is mathematically self-contained: all formal definitions (HMMs, GHMMs, belief states, MSPs) are introduced from scratch. However, students will engage with the material more fluently if they are comfortable with the following:

- **Linear algebra:** row-stochastic matrices, rank and invertibility, null spaces (kernels).
- **Probability:** conditional probability, Bayes' rule, probability distributions over finite sets, the probability simplex.
- **Basic machine learning:** next-token prediction, loss functions (cross-entropy), the concept of model activations.

:::callout {title="What you'll learn" tone="neutral"}

- Construct their own hidden Markov models.
- Explain the motivation for introducing generalised hidden Markov models (GHMMs).
- Explain why the belief state is a useful object for making predictions about GHMM data.
- Compute the belief state of a GHMM.
- Explain the difference between the belief state of a HMM and the belief state of a GHMM (that is itself not an HMM).
- Explain the relationship between belief states and next-token observation probabilities for GHMMs.
- Compute the mixed state presentation (MSP) for GHMMs.
- Explain why generating data is easier than predicting data.
- Explain the evidence for the claim: transformers represent belief state geometry in their residual stream.
- Develop hypotheses for where transformers represent: belief states, observation probabilities, log observation probabilities.

:::

\## 2. Content

\### 2.1 Fast-track

Read [Transformers represent belief state geometry in their residual stream](https://arxiv.org/pdf/2405.15943). Focus on being able to answer the following questions:

- What is a hidden Markov model (HMM)?
- What is a belief state?
- What is the mixed state presentation (MSP)?
- About the map learnt from activations to belief states:
  - What is the source?
  - What is the target?
  - How is the quality of the map evaluated?

%% Facilitator logistics (hidden from learners):
\### 2.2 Schedule

- **10:00–10:30** — [Lecture: Overview and scope](https://iliad-intensive.org/downloads/computational-mechanics/computational-mechanics-slides.pdf)
- **10:30–11:15** — [Lecture: Predicting the future](https://iliad-intensive.org/downloads/computational-mechanics/computational-mechanics-slides-2-predicting-the-future.pdf)
- **11:15–11:30** — *Break*
- **11:30–12:30** — Exercises: Predicting the future
- **12:30–13:30** — *Lunch*
- **13:30–14:15** — [Lecture: Representing the past](https://iliad-intensive.org/downloads/computational-mechanics/computational-mechanics-slides-3-representing-the-past.pdf)
- **14:15–15:45** — Exercises: Representing the past
- **15:45–16:00** — *Break*
- **16:00–17:45** — Reading & Discussion: Transformers represent belief geometry
- **17:45–18:00** — Feedback
%%

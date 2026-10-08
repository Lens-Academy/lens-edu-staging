---
id: '7788b875-34e5-486d-a8c3-39ecda640cb6'
title: "C.3.6 Identifying belief geometry in transformers"
tldr: "Read two papers on belief state geometry in neural networks, with a guiding evaluation question for each, and discuss the evidence in small groups."
summary_for_tutor: "This is section 5 (Identifying belief geometry in transformers) of Iliad worksheet C.3 Computational Mechanics: readings with reading routes and evaluation questions (Transformers represent belief state geometry in their residual stream, main, Figure 6D; Neural networks leverage nominally quantum and post-quantum representations, extension, Figure 3B) and five discussion prompts about evidence for belief-state geometry. Concepts: affine map from residual activations to belief states, MSE, shuffle control, Mess3 and RRXOR, GHMM versus HMM realisations."
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
\## 5. Identifying belief geometry in transformers

So far, we have developed the conceptual framework of computational mechanics. We now ask whether neural networks trained for next-token prediction—including transformers and recurrent architectures—learn the predictive structures identified by that framework. You will read selected sections of two papers, then discuss their evidence and limitations in small groups.

:::callout {title="Session at a glance" tone="blue"}

1. **Readings (75 minutes).** Begin with the main reading and use the route below. Continue to the extension if time permits.
2. **Discussion (30 minutes).** Form groups of three or four. Compare what you found convincing, confusing, or incomplete; use the prompts on page 2 if useful.

:::

\### 5.1 Readings

Prioritise the main reading. If you can answer its evaluation question, you have probably understood one of its central results. If time is short, skim the extension overview before deciding whether to continue.

\#### 5.1.1 [Main] [Transformers represent belief state geometry in their residual stream](https://arxiv.org/pdf/2405.15943)

::card[[../Lenses/shai-transformers-represent-belief-state-geometry-in-their-residual-stream|Transformers represent belief state geometry in their residual stream]]

**Reading route**

- **Skim.** Sections 1, 2.1, and 2.2.
- **Read.** Sections 2.3 and 3–5.
- **Evaluation.** Explain Figure 6D. What do the comparison and shuffle control establish?

**Overview.** This paper presents evidence that transformers trained on HMM-generated sequences encode belief-state geometry in their residual streams. The claim is tested on the Mess3 and Random–Random–XOR (RRXOR) processes. For each process, the authors fit an affine map from residual activations to the exact HMM belief state and evaluate it using mean-squared error (MSE). The error decreases over training checkpoints. A shuffle control tests whether low MSE could arise merely because a high-dimensional activation space is being projected into a low-dimensional belief space.

\#### 5.1.2 [Extension] [Neural networks leverage nominally quantum and post-quantum representations](https://arxiv.org/pdf/2507.07432)

**Reading route**

- **Skim.** Sections 1–3.
- **Read.** Sections 4–8.
- **Evaluation.** Explain Figure 3B. How are the light-blue and light-orange plots related to the corresponding dark-blue and dark-orange plots?

**Overview.** This paper extends the question from HMMs to generalised hidden Markov models (GHMMs). As in Part 3, a GHMM retains the matrix-product expression for output probabilities while relaxing the entrywise probabilistic constraints on its internal matrices. This larger model class can realise some processes in finite dimension even when a corresponding minimal HMM requires exponentially many more hidden states.

Using techniques related to those in the main reading, the authors study transformers, LSTMs, RNNs, and GRUs trained on processes with distinct GHMM and HMM realisations. Their results indicate that the networks learn belief-state representations associated with the lower-dimensional GHMM realisation. The finding suggests that neural networks can select among representational model classes in ways that capture dimensionality savings.

\### 5.2 Discussion

Here are some prompts to consider:

- What is the most convincing evidence that transformers represent belief-state geometry? What is the least convincing?
- What additional experiment would most strengthen or weaken the claim?
- Which alternative hypotheses could explain the reported results?
- Can you explain each element of the diagram below—including the generative HMM, Bayesian updating, transformer activations, fitted affine map, and belief-state geometry?

![figure](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-computational-mechanics-shai-belief-state-geometry-79d3951d.png)

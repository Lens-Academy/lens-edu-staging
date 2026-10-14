---
id: '27886b10-46cf-4597-bf65-8306e7cc47bb'
title: "C.3.7 Python exercises and further reading"
tldr: "Pointers to Python exercises on HMMs from scratch, and a list of further reading on in-context learning and computational mechanics."
summary_for_tutor: "This is the end of Iliad worksheet C.3 Computational Mechanics: section 6 describes the ARENA-style Colab notebooks (Part 1 sequence probabilities and next-token distributions, Part 2 belief states), and section 7 lists further reading on in-context learning of representations, LLMs predicting HMM data, factored representations and a review of computational mechanics. The notebooks are done outside this page."
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
\## 6. Python exercises: HMM from scratch

The Python exercises are ARENA-style notebooks in two parts. Each part has an **exercises** notebook (with `# YOUR CODE HERE` stubs, inline tests, and collapsible solutions) and a fully worked **solutions** notebook.

- **Part 1 — Sequence probabilities & next-token distributions** (exercises) — [Open in Colab](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.3/blob/main/python-exercises/colab/part1_sequence_probabilities_exercises_colab.ipynb)
- Part 1 (solutions) — [Open in Colab](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.3/blob/main/python-exercises/colab/part1_sequence_probabilities_solutions_colab.ipynb)
- **Part 2 — Belief states** (exercises) — [Open in Colab](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.3/blob/main/python-exercises/colab/part2_belief_states_exercises_colab.ipynb)
- Part 2 (solutions) — [Open in Colab](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.3/blob/main/python-exercises/colab/part2_belief_states_solutions_colab.ipynb)

The Colab notebooks are self-contained: their setup cells write the helper modules into the session, so there is nothing else to install or download.

\## 7. Learn more

- Beyond toy architectures – in-context learning
  - LLMs have an amazing ability to adapt internal representations in-context – [Read: ICLR: [In-Context Learning of Representations](https://arxiv.org/pdf/2501.00070)]
  - LLMs can predict HMM data in-context – [Read: [Pre-trained Large Language Models Learn Hidden Markov Models In-context](https://arxiv.org/pdf/2506.07298)]
  - This suggests that internal representations of LLMs predicting GHMM data in-context, may resemble belief states.
- Processes consisting of GHMMs with richer structure [Read: [Transformers learn factored representations](https://arxiv.org/pdf/2602.02385v1)]
- Review article of computational mechanics [Read: [Between order and chaos](https://www.nature.com/articles/nphys2190)]
- [Simplex](https://www.simplexaisafety.com/) is a non-profit research organisation working on applying computational mechanics to AI safety.

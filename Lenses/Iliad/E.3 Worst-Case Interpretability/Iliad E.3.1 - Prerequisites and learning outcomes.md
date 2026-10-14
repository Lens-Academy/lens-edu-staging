---
id: 'eacce4c9-1cea-4bfc-a0e6-39496eedd743'
title: "E.3.1 Prerequisites and learning outcomes"
tldr: "Lists the prerequisites and the learning outcomes: evaluating interpretations, compact proofs with exponential blowup, and ARC's heuristic arguments."
summary_for_tutor: "Opening of Iliad worksheet E.3 Worst-Case Interpretability: prerequisites (linear algebra, C.2 Mechanistic Interpretability, basic information and probability theory) and learning outcomes: difficulty of validating interpretations, interpretations as lossy compressions with faithfulness and compactness, the three sources of exponential blowup (error along paths, number of paths, input space coverage), vacuous worst-case bounds, and ARC's heuristic arguments agenda. No exercises."
authors:
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/worst-case-interp/
upstream_commit: 'd5fec17706ceed1fa028ca949b97b92dcc2f5f7e'
upstream_key: "worst-case-interp#prerequisites"
upstream_fingerprint: "uUN/117/1/01JU0Vjg1HGB2skn2tO03KD44Lf64j2c5YkZ76QQ79rt82Wz92pA9F0t9GPm9o18BOwmCCxiDzOfE9mCElH7F1ZtFfR9FzCCILq1J70hKWW1KXeoKdwXL6zWLGQRLzy4"
synced_from:
  source: "iliad"
  url: "https://iliad-intensive.org/safety/worst-case-interp/#prerequisites"
---

#### Text
content::
\## Prerequisites

* Linear algebra (SVD, eigendecomposition, matrix norms, singular values)
* C.2 Mechanistic Interpretability: Circuits, ablations, SAEs. More generally transformers
* Basic information + probability theory

:::callout {title="What you'll learn" tone="neutral"}

* Students understand the difficulty of evaluating and validating interpretations
* Students are able to formalize interpretations as lossy compressions with quantifiable faithfulness and compactness and its limitations through the three sources of exponential blowup (error along paths, number of paths, input space coverage)
* Students are able to articulate why worst-case bounds become vacuous even on simple models, and why this motivates an intermediate approach between worst-case and average-case evaluation
* Students on a high level understand ARC's heuristic arguments agenda as a response to these limitations

:::

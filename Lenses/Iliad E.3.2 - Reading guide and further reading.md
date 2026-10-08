---
id: '82c20d2f-3902-44db-8fbe-124c6a6b72f1'
title: "E.3.2 Reading guide and further reading"
tldr: "Gives the reading plan: faithfulness metrics for circuits, the compact proofs framework on a toy transformer, and heuristic arguments, plus further reading."
summary_for_tutor: "Reading guide and further reading of Iliad worksheet E.3 Worst-Case Interpretability. Fast track: intro notebook, ARC blog post and lecture slides. Main content in three steps: (1) limitations of interpretability evaluation (faithfulness metrics are not robust), (2) the compact proofs framework with the toy max-of-K model, (3) from proofs to heuristic arguments (ARC's agenda, no-coincidence principle). Further reading lists worst-case interp on other toy models, low probability estimation and critiques of ARC. No exercises."
authors:
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/worst-case-interp/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Reading guide

\### Fast-track

* Read the intro [notebook](https://colab.research.google.com/github/iliad-team/iliad-intensive/blob/notebooks/worst-case-interp/compact_proofs_nosol.ipynb) and the ARC blog [post](https://www.lesswrong.com/posts/SyeQjjBoEC48MvnQC/formal-verification-heuristic-explanations-and-surprise).
* Read the [Lecture slides](https://drive.google.com/file/d/1CqJtSUFLZ_L-kSsSzvSJGXfuf1Lbq5Un/view?usp=drive_link).

\### Main content

**1. Limitations of interpretability evaluation** Current interpretability methods are typically evaluated using faithfulness metrics based on ablations. These metrics turn out to be fragile.

* Read ["Transformer Circuit Faithfulness Metrics Are Not Robust"](https://arxiv.org/abs/2407.08734)

**2. Compact proofs framework** If average-case metrics are unreliable, can we do better? Proofs offer a rigorous alternative: formalize an interpretation as a compression of the model with quantifiable faithfulness and compactness, then prove guarantees. The compact proofs paper shows what happens when you try in a toy mode.

* Read: [Compact proofs paper](https://arxiv.org/abs/2406.11779), the main paper
* Work through the intro [notebook](https://colab.research.google.com/github/iliad-team/iliad-intensive/blob/notebooks/worst-case-interp/compact_proofs_nosol.ipynb)

**3. From proofs to heuristic arguments** The vacuousness of worst-case bounds suggests we need something between full proofs and mere average-case evaluation. ARC's heuristic arguments agenda proposes such an intermediate approach.

* Read: above mentioned [blog post](https://www.lesswrong.com/posts/SyeQjjBoEC48MvnQC/formal-verification-heuristic-explanations-and-surprise)

::card[[../Lenses/hilton-a-birds-eye-view-of-arcs-research|ARC’s general agenda]]

* Recent progress: [no-coincidence principle](https://www.lesswrong.com/posts/Xt9r4SNNuYxW83tmo/a-computational-no-coincidence-principle)

\## Further reading

* More examples of worst-case interp on toy models: [Learning group operations](https://arxiv.org/abs/2410.07476), [modular addition](https://arxiv.org/abs/2412.03773)
* Deeper look into ARC’s work: [Low probability estimation](https://arxiv.org/abs/2410.13211)
* Critiques of ARC work: This [series](https://www.lesswrong.com/s/uYMw689vDFmgPEHrS) for example

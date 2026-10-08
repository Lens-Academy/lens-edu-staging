---
id: 'a9ab8501-e229-478f-ba8f-53c27240b992'
title: "C.2.2 Content"
tldr: "The lecture slides, hands-on exercises on feature visualization, logit lens, SAEs, induction heads and Neuronpedia, a topic list, and four discussion readings."
summary_for_tutor: "Content of worksheet C.2. It has a fast track (the slides) and a main track with exercises in lecture order: feature visualization, logit lens, Neuronpedia SAE features, sparse autoencoders, attribution graphs, induction heads (normal and hard) and natural language autoencoders. It lists lecture topics from features, superposition and SAEs to circuits, circuit tracing and open problems, plus four critical discussion readings. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Julian Schulz (Meridian Research)
source_url: https://iliad-intensive.org/interpretability/mechanistic-interpretability/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Content

\### Fast Track

Go through the slides below.

\### Main Content

Material:

[Slides](https://raw.githubusercontent.com/iliad-team/iliad-intensive-C.2/main/lectures/output/main.pdf)

Exercises and external links (in lecture order)

* [Feature Visualization](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.2/blob/main/exercises/03_feature_viz/notebook.ipynb)
* Logit Lens: [normal](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.2/blob/main/exercises/01_logit_lens/notebook_normal.ipynb) [hard](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.2/blob/main/exercises/01_logit_lens/notebook_hard.ipynb)
* [Neuronpedia — SAE features](https://www.neuronpedia.org/gemma-3-27b/31-gemmascope-2-res-16k)
* [Sparse Autoencoders](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.2/blob/main/exercises/04_saes/notebook.ipynb)
* [Neuronpedia — Attribution graphs](https://www.neuronpedia.org/gemma-2-2b/graph)
* Induction Heads: [normal](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.2/blob/main/exercises/02_induction_heads/notebook_normal.ipynb) [hard](https://colab.research.google.com/github/iliad-team/iliad-intensive-C.2/blob/main/exercises/02_induction_heads/notebook_hard.ipynb)
* [Neuronpedia — Natural Language Autoencoders](https://www.neuronpedia.org/llama3.3-70b-it/nla)

Discussion reading

* Nanda et al., [A Pragmatic Vision for Interpretability](https://www.alignmentforum.org/posts/StENzDcD3kpfGJssR/a-pragmatic-vision-for-interpretability)
* Ségerie, [Against Almost Every Theory of Impact of Interpretability](https://www.lesswrong.com/posts/LNA8mubrByG7SFacm/against-almost-every-theory-of-impact-of-interpretability-1)
* Hendrycks, [The Misguided Quest for Mechanistic AI Interpretability](https://ai-frontiers.org/articles/the-misguided-quest-for-mechanistic-ai-interpretability)
* Chughtai, [Activation Space Interpretability May Be Doomed](https://www.alignmentforum.org/posts/gYfpPbww3wQRaxAFD/activation-space-interpretability-may-be-doomed)

Intent:

* The lecture gives an overview of the current state of MechInterp, developments over the last years, and commonly used methods
* The technical exercises are intended to deepen the understanding of the techniques and give a flavour for how mechinterp work looks like
* The Neuronpedia exercises are supposed to de-cherrypick mechinterp results and give a flavour for the average feature/circuit/NLA-output and show that a lot of the mechinterp results are still confusing, hard to interpret, and noisy

Content:

* Complex features and circuits (the car detector circuit)
* Universality in image models (curve and high-frequency detectors)
* Natural abstractions discourse (why certain features might be universal)
* Polysemanticity in CNNs
* Features in language models and the lack of a privileged basis
* Word embeddings encoding human concepts (word2vec gender direction)
* Linear probes for classifying text properties
* Probing world models (Othello-GPT board state)
* Intervening on world models
* Probing LLMs for truthfulness (attention head activations)
* Steering models with contrastive activation vectors
* Ablating features and the refusal direction (activation addition, direction ablation, weight orthogonalization)
* The logit lens
* Superposition (privileged vs non-privileged bases)
* Johnson–Lindenstrauss lemma and the scale of superposition
* Anthropic's toy model of superposition
* Feature geometry and phases (sticky regions, dimensions per feature)
* Semantic feature geometry (circular representations of time / non-linear features)
* Dictionary learning theory (Arora et al.)
* Compressed sensing and L1 minimization (Candès/Donoho)
* Sparse autoencoders (SAEs) and their training objective
* Interpreting SAE features (activation, logit effects, steering)
* Neuronpedia exploration
* SAE problems: feature absorption
* SAE problems: feature shrinkage
* The "Cambrian explosion" of SAE variants
* Gated SAEs
* JumpReLU SAEs
* Top-K / Batch Top-K SAEs
* Matryoshka SAEs
* Staircase SAEs
* Comparing/evaluating SAE architectures (loss recovered, auto-interp, absorption, SCR, k-sparse probing, RAVEL)
* SAEs scaling to production models (Sonnet 3.5)
* Bigger models yielding more specific features (golden gate bridge feature)
* Reading Claude's mind / safety-relevant feature steering (eval-awareness features)
* Transcoders and cross-layer transcoders (expanding SAEs)
* Model diffing
* Transformer circuits
* Reverse-engineering modular addition (the grokking / mod-113 circuit)
* Fourier analysis of the embedding matrix
* Plotting attention patterns
* Logit attribution and induction heads
* Q-composition and K-composition
* Path patching and the IOI (indirect object identification) circuit
* Automated circuit discovery (ACDC)
* Circuit tracing with cross-layer transcoders and replacement models
* Attribution graphs and feature suppression
* Circuit tracing on production models (Haiku 3.5 math circuit)
* Using circuit tracing for alignment (misaligned/reward-hacking model)
* Generality findings across circuits (layer roles, default pathways, shortcuts, special tokens, hedging features)
* Fuzzy/less-faithful interpretability approaches
* Activation oracles
* Natural language autoencoders (verbalizer + reconstructor)
* Open problems in mech interp (Sharkey et al.): decomposition, description, validation, automation, application
* Critiques of mechanistic interpretability (discussion of critical papers)

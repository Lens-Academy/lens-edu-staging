---
title: "Compact Proofs of Model Performance via Mechanistic Interpretability"
author:
  - "Jason Gross"
  - "Rajashree Agrawal"
  - "Thomas Kwa"
  - "Euan Ong"
  - "Chun Hei Yip"
  - "Alex Gibson"
  - "Soufiane Noubir"
  - "Lawrence Chan"
source_url: "https://www.alphaxiv.org/abs/2406.11779"
published: 2024-12-24
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "We propose using mechanistic interpretability -- techniques for reverse engineering model weights into human-interpretable algorithms -- to derive and compactly prove formal guarantees on model..."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Abstract ^abstract

We propose using mechanistic interpretability -- techniques for reverse engineering model weights into human-interpretable algorithms -- to derive and compactly prove formal guarantees on model performance. We prototype this approach by formally proving accuracy lower bounds for a small transformer trained on Max-of-K, validating proof transferability across 151 random seeds and four values of K. We create 102 different computer-assisted proof strategies and assess their length and tightness of bound on each of our models. Using quantitative metrics, we find that shorter proofs seem to require and provide more mechanistic understanding. Moreover, we find that more faithful mechanistic understanding leads to tighter performance bounds. We confirm these connections by qualitatively examining a subset of our proofs. Finally, we identify compounding structureless errors as a key challenge for using mechanistic interpretability to generate compact proofs on model performance.

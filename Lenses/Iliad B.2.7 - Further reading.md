---
id: 'fb5d4271-3f67-482c-a04a-de4b6393f926'
title: "B.2.7 Further reading"
tldr: "A list of optional further reading on learning theory, generalization, SGD dynamics, representational alignment, scaling, stagewise learning and emergent misalignment, each with a short note."
summary_for_tutor: "Further reading list at the end of Iliad worksheet B.2 Mysteries of Deep Learning: optional resources with one-line notes, including Telgarsky's deep learning theory notes, The other paper that killed deep learning theory, Zhang et al. on rethinking generalization, parity learning and leap complexity papers, The Scaling Hypothesis, representational alignment overview, deep linear network dynamics, stagewise development and Emergent Misalignment. No exercises."
authors:
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/mysteries-of-deep-learning/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Further reading

* [Deep learning theory lecture notes](https://mjt.cs.illinois.edu/dlt/) (Telgarsky)
  * A rigorous course-long treatment of statistical learning theory, following the same approximation/generalization/optimization error decomposition we use
* [The other paper that killed deep learning theory](https://www.lesswrong.com/posts/zcGmdQHX66NhC69v6/the-other-paper-that-killed-deep-learning-theory)
  * Discusses a 2019 result by Nagarajan and Kolter that doomed the worst-case *uniform convergence* framework for explaining neural network generalization
* [Understanding deep learning requires rethinking generalization](https://arxiv.org/abs/1611.03530)
  * Original paper which changed the field's mind on generalization, referenced by "The paper that killed deep learning theory"
* [Hidden Progress in Deep Learning: SGD Learns Parities Near the Computational Limit](https://arxiv.org/abs/2207.08799)
* [SGD learning on neural networks: leap complexity and saddle-to-saddle dynamics](https://arxiv.org/abs/2302.11055)
* [The No Free Lunch Theorem, Kolmogorov Complexity, and the Role of Inductive Biases in Machine Learning](https://arxiv.org/abs/2304.05366)
* [The Scaling Hypothesis](https://gwern.net/scaling-hypothesis)
  * Quite polemical. Nevertheless, very influential "ideas piece"
* [Getting aligned on representational alignment](https://arxiv.org/abs/2310.13018)
  * A broader overview of the representational alignment phenomenon
* [Exact solutions to the nonlinear dynamics of learning in deep linear neural networks](https://arxiv.org/abs/1312.6120)
  * Classic paper which finds stagewise learning in neural networks with linear activation function; will be covered later in the course
* [Stagewise Development in Neural Networks](https://www.lesswrong.com/posts/Zza9MNA7YtHkzAtit/stagewise-development-in-neural-networks)
  * A nice paper investigating stagewise learning in small LLMs. Requires some SLT knowledge
* [Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs](https://arxiv.org/abs/2502.17424)
  * Training on "evil" data in narrow domains (like, code with vulnerabilities) generalizes to "evil" more broadly (praising Hitler, etc)

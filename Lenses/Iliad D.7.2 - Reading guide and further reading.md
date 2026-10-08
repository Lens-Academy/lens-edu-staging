---
id: '738c8c83-0ec2-43c4-bc64-9d6dc5ab2c9a'
title: "D.7.2 Reading guide and further reading"
tldr: "Describes the slides and the three parts of the session (introduction, formal world models in reinforcement learning, abstractions), with related papers and further reading."
summary_for_tutor: "Reading guide and further reading of Iliad worksheet D.7 World Models. Fast track: the slides. Main content: three parts, (A) general introduction using rough notes and slides, (B) formal world models for reinforcement learning agents, related to arXiv 2504.04608 and an 'AI in a vat' LessWrong post, and (C) abstractions in world models, related to arXiv 2512.00984. Further reading covers Genie 3, Dreamer, JEPA, the separation principle and abstraction theory in MDPs. No exercises."
authors:
  - Fernando Rosas (University of Sussex)
source_url: https://iliad-intensive.org/agency/world-models/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Reading guide

\### Fast-track

* The slides should provide a basic understanding of the main ideas. From there, students can choose to go deeper into specific topics by following the notes or papers referred to in various slides.

\### Main content

The session is divided into three parts: (a) general introduction to world models, (b) formal definition of world models in reinforcement learning, and (c) operationalisation of abstractions within world models. Each of these units build in the previous one.

* (A) The introductory lecture in world models was done following the content within these rough [notes](https://drive.google.com/file/d/12UzgFkMN2bpu8U50vB5tAHxVdCpKdr3f/view?usp=drive_link). The session used [these slides](https://drive.google.com/file/d/1Rtfc5uW0oTDJBx7IEkJlmgLR1KOcg_4Z/view?usp=drive_link).
* (B) The session on a formal approach to world models for reinforcement learning agents used [these slides](https://drive.google.com/file/d/1wR_tNsOu41_IKlFRUO0NLuq5IvIKqE52/view?usp=drive_link), which are closely related to [this paper](https://arxiv.org/abs/2504.04608) (see also this [LW post](https://www.lesswrong.com/posts/L6Z6K8qXJhrSNMN4L/ai-in-a-vat-fundamental-limits-of-efficient-world-modelling))
* (C) The last session on abstractions in world models used [these slides](https://drive.google.com/file/d/11LyzmBFRoovylkOPPzMNuG2olPwG-y9P/view?usp=drive_link), which are closely related to this [preprint](https://arxiv.org/abs/2512.00984).

\## Further reading

* Related work on world models:
  * [Geniel 3](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/)
  * [Latest Dreamer paper](https://www.nature.com/articles/s41586-025-08744-2)
  * [Robust agents learn world models](https://deepmind.google/research/publications/49666/)
  * [Separation principle](https://en.wikipedia.org/wiki/Separation_principle) from optimal control theory as a foundation of why agents build beliefs and plan upon them.
  * [Deep dive into JEPA](https://rohitbandaru.github.io/blog/JEPA-Deep-Dive/)
* Related work on abstractions on world models
  * [Abstractions as emergent properties](https://www.quantamagazine.org/the-new-math-of-how-large-scale-order-emerges-20240610/)
  * [Towards a unified theory of abstractions in MDPs](http://rbr.cs.umass.edu/aimath06/proceedings/P21.pdf)
  * [A Theory of Abstraction in Reinforcement Learning](https://david-abel.github.io/thesis.pdf)

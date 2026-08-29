---
id: 'fe43d166-6a95-4865-992f-f8448dfacb75'
title: "2.1.7 Reconstructing a declared training run"
tldr: "Can a verifier tell whether the declared training process really produced the submitted model? Proof-of-learning has been broken more than once, and zero-knowledge training proofs still have thirteen open problems. Spend a limited verification budget and say which claim stays untested."
summary_for_tutor: "Imported from XLab's Verification curriculum; preserve source framing. Optional technical extension: evidence for reconstructing a declared run, Shavit's decomposition, proof-of-learning and its adversarial breaks, and three claims to keep separate (declared-run correctness, declared-run completeness, fleet completeness). Ends with an optional open question allocating a verification-compute budget across seven checks. Push the learner to state which of the three claims each check addresses and which remains untested."
tags: [wip]
duration_minutes: 5
---
#### Text
content::
\### 2.1.7 {--{"author":"Elias's AI","timestamp":1788016028393}@@[Optional] Extension: reconstructing--}{++{"author":"Elias's AI","timestamp":1788016028393}@@Reconstructing++} a declared training run

{++{"author":"Elias's AI","timestamp":1788016028393}@@Optional: this lesson is the technical extension of section 2.1 and is marked optional in XLab's curriculum.

++}This extension asks a different question: can a verifier test whether a declared training process plausibly produced the submitted checkpoints or model?

Possible evidence includes:

- Training records and code or data commitments;
- Periodic checkpoints or weight snapshots;
- Authenticated transcripts;
- Sampled re-execution;
- Probabilistic recomputation;
- Dedicated verification clusters;
- Proof-of-learning or proof-of-training-data protocols.

Yonadav Shavit’s 2023 compute-monitoring proposal decomposed a possible system into on-chip weight snapshots, records intended to support later verification of training, and supply-chain monitoring intended to prevent accumulation of untracked chips. This decomposition remains useful because it separates verification of a declared run from completeness of the fleet.

{--{"author":"Elias's AI","timestamp":1788016031740}@@**Src**--}{++{"author":"Elias's AI","timestamp":1788016031740}@@:::callout {title="Source" tone="neutral" collapse="closed"}++}
Y. Shavit, *What Does It Take to Catch a Chinchilla? Verifying Rules on Large-Scale Neural Network Training via Compute Monitoring* — [arXiv:2303.11341](https://arxiv.org/abs/2303.11341), 2023.{++{"author":"Elias's AI","timestamp":1788016031740}@@
:::++}

Proof-of-learning research shows both the promise and fragility of checkpoint-based verification. Jia and colleagues proposed proofs based on logged intermediate states. Subsequent work demonstrated adversarial constructions and serious weaknesses in the original approach. Choi, Shavit, and Duvenaud later proposed a broader toolkit for verifying claims about training data, while explicitly treating its tests as heuristic and noting substantial confidentiality and access assumptions.

{--{"author":"Elias's AI","timestamp":1788016037775}@@**Src**--}{++{"author":"Elias's AI","timestamp":1788016037775}@@:::callout {title="Sources" tone="neutral" collapse="closed"}++}
H. Jia et al., *Proof-of-Learning: Definitions and Practice* — [arXiv:2103.05633](https://arxiv.org/abs/2103.05633), 2021. R. Zhang et al., *Adversarial Examples for Proof-of-Learning* — [arXiv:2108.09454](https://arxiv.org/abs/2108.09454), IEEE Symposium on Security and Privacy, 2022. C. Fang et al., *Proof-of-Learning Is Currently More Broken Than You Think* — [arXiv:2208.03567](https://arxiv.org/abs/2208.03567), revised 2023. J. Choi, Y. Shavit, and D. Duvenaud, *Tools for Verifying Neural Models’ Training Data* — [arXiv:2307.00682](https://arxiv.org/abs/2307.00682), 2023.{++{"author":"Elias's AI","timestamp":1788016037775}@@
:::++}

Keep three claims separate:

- **Declared-run correctness:** the submitted model or checkpoint plausibly arose from the declared process.
- **Declared-run completeness:** the submitted transcript covered all relevant steps associated with that declared run.
- **Fleet completeness:** no separate prohibited run occurred on other hardware.

Training transcripts and recomputation mainly address the first claim, with varying assurance. They do not automatically establish the third.

A June 2026 paper proposes a zero-knowledge architecture for frontier training claims, but it also identifies thirteen open problems and a critical requirement that has not yet been demonstrated at relevant scale: a zero-knowledge proof of backpropagation for a nontrivial model. Treat this as an ambitious research proposal, not evidence that zero-knowledge verification of frontier training is deployment-ready.

{--{"author":"Elias's AI","timestamp":1788016048853}@@**Src**--}{++{"author":"Elias's AI","timestamp":1788016048853}@@:::callout {title="Source" tone="neutral" collapse="closed"}++}
*Zero Knowledge Verification for Frontier AI Training Is Possible* — [arXiv:2606.05433](https://arxiv.org/abs/2606.05433), June 2026. The paper presents an architecture and estimates, while documenting open problems and unproven critical components.{++{"author":"Elias's AI","timestamp":1788016048853}@@
:::++}

\#### Activity: buy assurance with a verification budget

{++{"author":"Elias's AI","timestamp":1788016048853}@@#### Question: Open
id:: 25ad0482-15a3-4c5a-a717-c7a7b2ca6e29
content:: Optional: ++}You receive a declared transcript and a limited verification-compute budget. Allocate it among full rerunning, random segment sampling, checkpoint checks, code and data commitments, physical compute totals, telemetry-timing comparison, and random chip inspection. For each choice, record cost, confidentiality exposure, spoofing opportunity, expected assurance, and the claim that remains untested.{++{"author":"Elias's AI","timestamp":1788016048853}@@
optional:: true
assessment-instructions:: This is an XLab writing or reflection exercise. Check that the allocation is explicit, that each chosen check records the five attributes, and that the learner says which of the three claims (declared-run correctness, declared-run completeness, fleet completeness) each check addresses and which remains untested. Mark down answers that treat transcript checks as evidence about fleet completeness. Identify one strong point and one important gap, then ask one useful follow-up question. Do not imply that agreement with the source is required.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Peigné, Pierre, Ky Nguyen, and Paul Wang. "Zero knowledge verification for frontier AI training is possible." *arXiv*, June 2026. [arxiv.org](https://arxiv.org/abs/2606.05433)
*The 2026 proposal estimating a future ZK system could verify dense frontier training at roughly 2–10 percent overhead, while naming thirteen unresolved technical problems and the training architectures it does not yet cover.*++}

{--{"author":"Elias's AI","timestamp":1788016048853}@@*Source lesson: [XLab curriculum](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-reconstructing-run)*--}{++{"author":"Elias's AI","timestamp":1788016048853}@@XLab. "2.1.7 Reconstructing a declared training run." *Verification*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/verification/verification-infrastructure/hardware-reconstructing-run)
*The source lesson this page adapts. Shavit (2023), Jia et al. (2021), Zhang et al. (2022), Fang et al. (2023) and Choi, Shavit and Duvenaud (2023) are cited inline above.*
:::++}

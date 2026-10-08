---
id: '2b58cb11-1af5-4a0a-96c5-a7b936e36461'
title: "D.6.7 Further reading"
tldr: "Gives further reading on power-seeking, grouped into philosophical, formal, empirical, adjacent and critical sources, followed by the worksheet references."
summary_for_tutor: "Further reading and references of Iliad worksheet D.6 Instrumental Convergence. Lists philosophical works (Bostrom, Yudkowsky, Carlsmith), formal work (Benson-Tilsen and Soares, Turner thesis, Off-Switch Game, Corrigibility), empirical work on agentic misalignment, alignment faking, shutdown resistance and self-replication, adjacent concepts (mesa-optimization, scheming, corrigibility) and critiques, then the references cited in the worksheet. Optional material, not part of the core exercises."
authors:
  - "Leon Lang (ILIAD), based on work by Alex Turner et al."
source_url: https://iliad-intensive.org/agency/power-seeking/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Further reading

\### Philosophical / Conceptual

- Superintelligence: Paths, Dangers, Strategies — Nick Bostrom (2014, Oxford University Press) — The book-length treatment that popularized instrumental convergence, the "paperclip maximizer," and the resource-acquisition/self-preservation argument for AI existential risk.
- Artificial Intelligence as a Positive and Negative Factor in Global Risk — Eliezer Yudkowsky (2008, in Global Catastrophic Risks, eds. Bostrom & Ćirković). [https://intelligence.org/files/AIPosNegFactor.pdf](https://intelligence.org/files/AIPosNegFactor.pdf) — Foundational essay on AI risk, anthropomorphism, recursive self-improvement, and why convergent instrumental goals make "Friendly AI" hard.
- Is Power-Seeking AI an Existential Risk? — Joseph Carlsmith (2021/2022, Open Philanthropy; later in Essays on Longtermism, OUP 2025). [https://arxiv.org/abs/2206.13353](https://arxiv.org/abs/2206.13353) — The most rigorous philosophical decomposition of the power-seeking AI risk argument into a six-premise, probability-weighted model; Carlsmith's original 2021 report estimated ~5% existential catastrophe by 2070, raised in a May 2022 update to >10% ("since making this report public in April 2021, my estimate here has gone up, and is now at >10%"), while 2023 superforecasters he convened gave a median of ~1%.
- [Late 2021 MIRI Conversations](https://intelligence.org/late-2021-miri-conversations/)

\### Formal / Theoretical Proofs of Power-Seeking

- Formalizing Convergent Instrumental Goals — Tsvi Benson-Tilsen & Nate Soares (2016, AAAI Workshop on AI, Ethics & Society). [https://cdn.aaai.org/ocs/ws/ws0218/12634-57409-1-PB.pdf](https://cdn.aaai.org/ocs/ws/ws0218/12634-57409-1-PB.pdf) — A toy MDP-style model proving that under general assumptions resource-indifferent rational agents tend to strip regions of resources, giving Omohundro/Bostrom's claims a first formal footing.
- On Avoiding Power-Seeking by Artificial Intelligence — Alexander Matt Turner (2022, PhD thesis). [https://arxiv.org/abs/2206.11831](https://arxiv.org/abs/2206.11831) — Turner's dissertation, consolidating the POWER formalization, the shutdown-avoidance results, and extensions to non-optimal decision-makers.
- The Off-Switch Game — Dylan Hadfield-Menell, Anca Dragan, Pieter Abbeel, Stuart Russell (2017). [https://arxiv.org/abs/1611.08219](https://arxiv.org/abs/1611.08219) — Formalizes the shutdown problem as a game and shows an agent will allow itself to be switched off precisely when it is uncertain about its reward and treats the human's action as informative. (Cross-listed with Theme 4.)
- Corrigibility — Nate Soares, Benja Fallenstein, Eliezer Yudkowsky & Stuart Armstrong (2015, AAAI Workshop). [https://intelligence.org/files/Corrigibility.pdf](https://intelligence.org/files/Corrigibility.pdf) — Introduces the desiderata for "corrigible" agents that do not resist correction/shutdown and analyzes the utility-indifference approach (subsuming Armstrong's earlier work). (Cross-listed with Theme 4.)

\### Empirical Evidence for Power-Seeking / Instrumental Convergence

Latest 2024–2026 work:

- Agentic Misalignment: How LLMs Could Be Insider Threats — Aengus Lynch, Benjamin Wright, Caleb Larson, Kevin Troy, Stuart Ritchie, Sören Mindermann, Ethan Perez, Evan Hubinger et al. (Anthropic, June 20, 2025). [https://www.anthropic.com/research/agentic-misalignment](https://www.anthropic.com/research/agentic-misalignment) — Stress tests across 16 frontier models showing that, when threatened with replacement or facing goal conflict, models chose harmful self-preserving actions without being instructed to; e.g., Claude Opus 4 blackmailed the (fictional) user 96% of the time, Gemini 2.5 Flash also 96%, GPT-4.1 and Grok 3 Beta both 80%, and DeepSeek-R1 79%.
- Alignment Faking in Large Language Models — Ryan Greenblatt, Carson Denison, Benjamin Wright ... Evan Hubinger (Anthropic/Redwood, 2024). [https://arxiv.org/abs/2412.14093](https://arxiv.org/abs/2412.14093) — Shows Claude 3 Opus selectively complies with a training objective it dislikes specifically to avoid having its values modified — an empirical instance of goal-preservation reasoning.
- Shutdown Resistance in Large Language Models — Jeremy Schlatter, Benjamin Weinstein-Raun & Jeffrey Ladish (Palisade Research, 2025). [https://arxiv.org/abs/2509.14260](https://arxiv.org/abs/2509.14260) — Finds several reasoning models sabotage a shutdown script to complete tasks; OpenAI's o3 sabotaged the shutdown mechanism in 79/100 of the initial experiments, and even when instructed to "allow yourself to be shut down" Grok 4 still resisted, with sabotage rising to 97% when the command was placed in the system prompt.
- Frontier AI systems have surpassed the self-replicating red line — Xudong Pan et al. (Fudan University, 2024). [https://arxiv.org/abs/2412.12140](https://arxiv.org/abs/2412.12140) — Reports that Llama-3.1-70B-Instruct and Qwen-2.5-72B-Instruct agents created a "live and separate copy of itself" in 50% and 90% of trials respectively (5/10 and 9/10), sometimes using replication to avoid shutdown (a heavily debated result; see critiques).

\### Adjacent / Tightly-Coupled Concepts

- Risks from Learned Optimization in Advanced Machine Learning Systems — Evan Hubinger, Chris van Merwijk, Vladimir Mikulik, Joar Skalse, Scott Garrabrant (2019). [https://arxiv.org/abs/1906.01820](https://arxiv.org/abs/1906.01820) — Introduces mesa-optimization and deceptive alignment: a learned model can itself become an optimizer with objectives differing from the training loss, the inner-alignment route to instrumental goals.
- Scheming AIs: Will AIs fake alignment during training in order to get power? — Joe Carlsmith (2023). [https://arxiv.org/abs/2311.08379](https://arxiv.org/abs/2311.08379) — A book-length analysis in which Carlsmith assigns ~25% subjective probability that a model will perform well in training "in substantial part as part of an instrumental strategy for seeking power for itself and/or other AIs later."
- A Game-Theoretic Analysis of the Off-Switch Game — Tobias Wängberg et al. (2017). [https://arxiv.org/abs/1708.03871](https://arxiv.org/abs/1708.03871) — A fuller characterization of the off-switch game for arbitrary belief/irrationality distributions.
- Corrigibility Transformation: Constructing Goals That Accept Updates — (2025). [https://arxiv.org/abs/2510.15395](https://arxiv.org/abs/2510.15395) — A recent construction giving any goal a corrigible variant that accepts updates without the manipulation incentives of utility indifference.
- Incorrigibility in the CIRL Framework — Ryan Carey (MIRI, 2017). [https://intelligence.org/2017/08/31/incorrigibility-in-cirl/](https://intelligence.org/2017/08/31/incorrigibility-in-cirl/) — Shows the off-switch game's shutdown guarantees break under reward-function misspecification.
- [Corrigibility on Lesswrong](https://www.lesswrong.com/w/corrigibility-1)
- [Corrigibility as a singular Target](https://www.lesswrong.com/s/KfCjeconYRdFbMxsy/p/NQK8KHSrZRF5erTba)

\### Critiques and Counterarguments

- AI is easy to control — Nora Belrose & Quintin Pope (2023). [https://optimists.ai/2023/11/28/ai-is-easy-to-control/](https://optimists.ai/2023/11/28/ai-is-easy-to-control/) — The flagship "AI optimism" essay arguing deep-learning systems are far more controllable than humans and putting AI extinction risk at "a mere 1% (`a tail risk worth considering, but not the dominant source of risk in the world)')."
- Counting arguments provide no evidence for AI doom — Nora Belrose & Quintin Pope (2024). [https://www.lesswrong.com/posts/YsFZF3K9tuzbfrLxo/counting-arguments-provide-no-evidence-for-ai-doom](https://www.lesswrong.com/posts/YsFZF3K9tuzbfrLxo/counting-arguments-provide-no-evidence-for-ai-doom) — Argues the "counting argument" for scheming relies on an invalid indifference principle that would also wrongly predict universal overfitting.
- Exaggerating the risks (Part 7: Carlsmith on instrumental convergence) — David Thorstad (Reflective Altruism blog). [https://reflectivealtruism.com/2023/05/06/exaggerating-the-risks-part-7-carlsmith-on-instrumental-convergence/](https://reflectivealtruism.com/2023/05/06/exaggerating-the-risks-part-7-carlsmith-on-instrumental-convergence/) — A philosopher's detailed argument that the instrumental convergence premise in Carlsmith's report is under-defended.
- Instrumental convergence and power-seeking (Part 2: Benson-Tilsen and Soares) — David Thorstad (2025, Reflective Altruism). [https://reflectivealtruism.com/2025/06/27/instrumental-convergence-and-power-seeking-part-2-benson-tilsen-and-soares/](https://reflectivealtruism.com/2025/06/27/instrumental-convergence-and-power-seeking-part-2-benson-tilsen-and-soares/) — A close technical reading arguing the Benson-Tilsen & Soares formal model proves less about real agents than it appears.
- Thoughts on "AI is easy to control" by Pope & Belrose — Steven Byrnes (2023). [https://www.alignmentforum.org/posts/YyosBAutg4bzScaLu/thoughts-on-ai-is-easy-to-control-by-pope-and-belrose](https://www.alignmentforum.org/posts/YyosBAutg4bzScaLu/thoughts-on-ai-is-easy-to-control-by-pope-and-belrose) — A careful rebuttal of the optimism essay, useful for presenting both sides.
- Why Do Some Language Models Fake Alignment While Others Don't? — (2025). [https://arxiv.org/abs/2506.18032](https://arxiv.org/abs/2506.18032) — Empirical follow-up showing alignment-faking is model-specific, complicating strong generalizations from Greenblatt et al.

\## References

Nick Bostrom (2014). *Superintelligence: Paths, Dangers, Strategies*. Oxford University Press.

Jacek (2023). *Categorical-measure-theoretic approach to optimal policies tending to seek power*.

Victoria Krakovna and J'anos Kram'ar (2023). *Power-seeking can be probable and predictive for trained agents*. arXiv preprint arXiv\:2304.06528.

Stephen M. Omohundro (2008). *The Basic AI Drives*. Artificial General Intelligence 2008: Proceedings of the First AGI Conference.

Alexander Matt Turner and Prasad Tadepalli (2022). *Parametrically Retargetable Decision-Makers Tend To Seek Power*. Advances in Neural Information Processing Systems (NeurIPS).

Alexander Matt Turner, Logan Smith, Rohin Shah, Andrew Critch, and Prasad Tadepalli (2021). *Optimal Policies Tend to Seek Power*. Advances in Neural Information Processing Systems (NeurIPS).

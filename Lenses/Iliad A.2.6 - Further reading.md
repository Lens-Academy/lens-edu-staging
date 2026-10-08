---
id: '4834467c-284e-431c-82fc-b97735a4d384'
title: "A.2.6 Further reading"
tldr: "Further reading lists for pretraining, post-training and other topics from this day."
summary_for_tutor: "Further reading section of worksheet A.2. It is a reference list grouped by topic (data filtering, gradient routing, alignment pretraining, simulators and persona selection, post-training for safety, synthetic documents, emergent misalignment, unlearning, and more). These are optional pointers and not assigned work."
authors:
  - Margot Stakenborg
  - Garrett Baker
  - Evžen Wybitul
source_url: https://iliad-intensive.org/alignment/alignment-in-practice/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## Further reading

\### Pre-training

Data filtering

* [Enhancing Model Safety through Pretraining Data Filtering](https://alignment.anthropic.com/2025/pretraining-data-filtering/)
* [Shaping Capabilities with Token-Level Data Filtering](https://arxiv.org/abs/2601.21571)

Gradient routing

* [Gradient Routing: Masking Gradients to Localize Computation in Neural Networks](https://arxiv.org/abs/2410.04332)
* [Beyond Data Filtering: Knowledge Localization for Capability Removal in LLMs (SGTM)](https://alignment.anthropic.com/2025/selective-gradient-masking/)

Alignment pretraining

* [Alignment Pretraining: AI Discourse Causes Self-Fulfilling (Mis)alignment](https://arxiv.org/abs/2601.10160)

Simulators and persona selection

* [Simulators](https://www.lesswrong.com/posts/vJFdjigzmcXMhNTsx/simulators)
* [The Persona Selection Model: Why AI Assistants might Behave like Humans](https://alignment.anthropic.com/2026/psm/)

\### Post-training

Post-training for safety

* [Deliberative Alignment](https://arxiv.org/abs/2412.16339)
* [Training LLMs for Honesty via Confessions](https://arxiv.org/abs/2512.08093)
* [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073)

Finetuning on synthetic documents

* [Modifying LLM Beliefs with Synthetic Document Finetuning](https://alignment.anthropic.com/2025/believe-it-or-not/)
* [Training on Documents About Reward Hacking Induces Reward Hacking](https://alignment.anthropic.com/2025/reward-hacking-ooc/)

Emergent misalignment

* [Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs](https://arxiv.org/abs/2502.17424)
* [Natural Emergent Misalignment from Reward Hacking in Production RL](https://arxiv.org/abs/2511.18397)
* [Inoculation Prompting: Eliciting traits from LLMs during training can suppress them at test-time](https://arxiv.org/abs/2510.04340)
* [Inoculation Prompting: Instructing LLMs to misbehave at train-time improves test-time alignment](https://arxiv.org/abs/2510.05024)

Unlearning

* [Eight Methods to Evaluate Robust Unlearning in LLMs](https://arxiv.org/abs/2402.16835)
* [From Dormant to Deleted: Tamper-Resistant Unlearning Through Weight-Space Regularization](https://arxiv.org/abs/2505.22310)
  * Related: [Subliminal Learning: Language models transmit behavioral traits via hidden signals in data](https://arxiv.org/abs/2507.14805)
* [Distillation Robustifies Unlearning (UNDO)](https://arxiv.org/abs/2506.06278)
* [Machine Unlearning Doesn't Do What You Think: Lessons for Generative AI Policy and Research](https://arxiv.org/abs/2412.06966v2)
* [Open Problems in Machine Unlearning for AI Safety](https://arxiv.org/abs/2501.04952)

\### Deployment 1: strategy

Deployment frameworks

* [Anthropic Responsible Scaling Policy](https://www.anthropic.com/responsible-scaling-policy)
* [OpenAI Preparedness Framework](https://openai.com/index/updating-our-preparedness-framework/)
* [Google DeepMind Frontier Safety Framework](https://deepmind.google/blog/strengthening-our-frontier-safety-framework/)

Safety cases

* [Safety cases at AISI](https://www.aisi.gov.uk/blog/safety-cases-at-aisi)
* [How can safety cases be used to help with frontier AI safety?](https://www.aisi.gov.uk/blog/how-can-safety-cases-be-used-to-help-with-frontier-ai-safety)
* [Safety case template for frontier AI: A cyber inability argument](https://www.aisi.gov.uk/research/safety-case-template-for-frontier-ai-a-cyber-inability-argument-2)
* [An example safety case for safeguards against misuse](https://www.aisi.gov.uk/research/an-example-safety-case-for-safeguards-against-misuse)

Law and compliance

* [General-purpose AI obligations under the AI Act](https://digital-strategy.ec.europa.eu/en/factpages/general-purpose-ai-obligations-under-ai-act)
* [The General-Purpose AI Code of Practice](https://digital-strategy.ec.europa.eu/en/policies/contents-code-gpai)
* [Guidelines for providers of general-purpose AI models](https://digital-strategy.ec.europa.eu/en/policies/guidelines-gpai-providers)

\### Deployment 2: building the safety system

Runtime safeguards

* A part of the safeguarding is done by the model itself through the whole of safety training from Iliad Intensive April 2026, Post-training, like confessions, deliberative alignment, and constitutional AI
* [Constitutional Classifiers: Defending against Universal Jailbreaks across Thousands of Hours of Red Teaming](https://arxiv.org/abs/2501.18837)
* [Cost-Effective Constitutional Classifiers via Representation Re-use](https://alignment.anthropic.com/2025/cheap-monitors/)
* [How we monitor internal coding agents for misalignment](https://openai.com/index/how-we-monitor-internal-coding-agents-misalignment/)
* [Detecting Strategic Deception Using Linear Probes](https://arxiv.org/abs/2502.03407)
* [Access Controls Will Solve the Dual-Use Dilemma](https://arxiv.org/abs/2505.09341)

High-level red-teaming strategy

* [AISI Frontier AI Trends Report](https://www.aisi.gov.uk/frontier-ai-trends-report)
* [Challenges in Red Teaming AI Systems](https://www.anthropic.com/news/challenges-in-red-teaming-ai-systems)
* [OpenAI's Approach to External Red Teaming](https://arxiv.org/abs/2503.16431)

Evaluating jailbreaks

* [The Jailbreak Tax: How Useful are Your Jailbreak Outputs?](https://arxiv.org/abs/2504.10694)
* [HarmBench: A Standardized Evaluation Framework for Automated Red Teaming and Robust Refusal](https://arxiv.org/abs/2402.04249)

White-box and fine-tuning attacks

* [Refusal in Language Models Is Mediated by a Single Direction](https://arxiv.org/abs/2406.11717)
* [Universal and Transferable Adversarial Attacks on Aligned Language Models (GCG)](https://arxiv.org/abs/2307.15043)
* [Jailbreak-Tuning: Models Efficiently Learn Jailbreak Susceptibility](https://arxiv.org/abs/2507.11630)

Black-box attacks

* [Chain-of-Thought Hijacking](https://arxiv.org/abs/2510.26418)
* [Toward Universal and Transferable Jailbreak Attacks on Vision-Language Models](https://arxiv.org/abs/2602.01025)
* [Abstractive Red-Teaming](https://alignment.anthropic.com/2026/abstractive-red-teaming/)
* [Many-Shot Jailbreaking](https://openreview.net/forum?id=BXLRMWLDQw)
* [Best-of-N Jailbreaking](https://arxiv.org/abs/2412.03556)
* [Jailbreaking Black Box Large Language Models in Twenty Queries (PAIR)](https://arxiv.org/abs/2310.08419)
* [Black-box Optimization of LLM Outputs by Asking for Directions](https://arxiv.org/abs/2510.16794)

\### Monitoring

Chain-of-thought monitoring

* [Chain of Thought Monitorability: A New and Fragile Opportunity for AI Safety](https://arxiv.org/abs/2507.11473)
* [Monitoring Reasoning Models for Misbehavior and the Risks of Promoting Obfuscation](https://arxiv.org/abs/2503.11926)
* [Reasoning Models Don't Always Say What They Think](https://www.anthropic.com/research/reasoning-models-dont-say-think)
* [When Chain of Thought is Necessary, Language Models Struggle to Evade Monitors](https://arxiv.org/abs/2507.05246)
* [Training fails to elicit subtle reasoning in current language models](https://alignment.anthropic.com/2025/subtle-reasoning/)
* [Can Reasoning Models Obfuscate Reasoning? Stress-Testing Chain-of-Thought Monitorability](https://arxiv.org/abs/2510.19851)

Auditing

* [Bloom: an open source tool for automated behavioral evaluations](https://alignment.anthropic.com/2025/bloom-auto-evals/)
* [Petri 2.0: New Scenarios, New Model Comparisons, and Improved Eval-Awareness Mitigations](https://alignment.anthropic.com/2026/petri-v2/)
* [Auditing Language Models for Hidden Objectives](https://arxiv.org/abs/2503.10965)
* [Building and evaluating alignment auditing agents](https://alignment.anthropic.com/2025/automated-auditing/)
* [AuditBench: Evaluating Alignment Auditing Techniques on Models with Hidden Behaviors](https://alignment.anthropic.com/2026/auditbench/)
* [Activation Oracles: Training and Evaluating LLMs as General-Purpose Activation Explainers](https://alignment.anthropic.com/2025/activation-oracles/)

Capability elicitation

* [AI Cybersecurity After Mythos: The Jagged Frontier](https://aisle.com/blog/ai-cybersecurity-after-mythos-the-jagged-frontier)
* [Stress-Testing Capability Elicitation With Password-Locked Models](https://arxiv.org/abs/2405.19550)
* [The Elicitation Game: Evaluating Capability Elicitation Techniques](https://arxiv.org/abs/2502.02180)
* [Unsupervised Elicitation of Language Models (Internal Coherence Maximization)](https://arxiv.org/abs/2506.10139)
* [3 Challenges and 2 Hopes for the Safety of Unsupervised Elicitation](https://alignment.anthropic.com/2025/unsupervised-elicitation-challenges/)
* [Discovering Latent Knowledge in Language Models Without Supervision (CCS)](https://arxiv.org/abs/2212.03827)
* [Challenges with Unsupervised LLM Knowledge Discovery](https://arxiv.org/abs/2312.10029)
* [Eliciting Latent Knowledge from Quirky Language Models](https://arxiv.org/abs/2312.01037)
* [Latent Adversarial Training Improves Robustness to Persistent Harmful Behaviors](https://arxiv.org/abs/2403.05030)
* [Mechanistically Eliciting Latent Behaviors in Language Models (MELBO)](https://www.lesswrong.com/posts/ioPnHKFyy4Cw2Gr2x/mechanistically-eliciting-latent-behaviors-in-language-1)

Post-deployment usage analysis

* [Clio: Privacy-Preserving Insights into Real-World AI Use](https://arxiv.org/abs/2412.13678)
* [Anthropic Economic Index](https://www.anthropic.com/research/economic-index-primitives)

\### Control

**Common introduction.**  [*The Case for Ensuring That Powerful AIs Are Controlled*](https://blog.redwoodresearch.org/p/the-case-for-ensuring-that-powerful)

**Further approaches**

1.  [**AI Control: Improving Safety Despite Intentional Subversion**](https://arxiv.org/abs/2312.06942) (Redwood Research) — Use trusted models and scarce human audits to monitor, edit, or replace suspicious outputs from a stronger untrusted model.

2.  [**Ctrl-Z: Controlling AI Agents via Resampling**](https://arxiv.org/abs/2504.10374) (Redwood Research) — Resample suspicious actions to obtain safer alternatives and additional evidence of attempted subversion.

3.  [**Untrusted Advice for AI Control**](https://blog.redwoodresearch.org/p/untrusted-advice-for-ai-control-short) (Redwood Research) — Restrict the untrusted model to a low-bandwidth advice channel while a trusted model retains exclusive authority to act.

4.  [**Diffuse AI Control on Fuzzy Tasks**](https://alignment.anthropic.com/2026/diffuse-ai-control/) (Anthropic) — Adversarially improve the weak scoring process used to train untrusted models against repeated sabotage on hard-to-evaluate work.

5.  [**Evaluating Chain-of-Thought Monitorability**](https://arxiv.org/abs/2512.18311) (OpenAI) — Preserve and measure legible reasoning so chain-of-thought monitoring can serve as a scalable control layer.

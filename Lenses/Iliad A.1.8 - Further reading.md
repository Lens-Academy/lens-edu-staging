---
id: 'bea445d0-0160-4a61-b009-7533811eeff7'
title: "A.1.8 Further reading"
tldr: "Further reading lists for the alignment intro: problem overviews, alignment targets and related topics."
summary_for_tutor: "Further reading section of worksheet A.1. It is a reference list grouped by topic (problem overviews, non-misalignment risks such as misuse, power concentration and gradual disempowerment, alignment targets, and more), with a one-line description for many items. These are optional pointers and not assigned work."
authors:
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/alignment/ai-alignment-intro/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 
Further reading

\### Problem overviews

On the alignment problem

* [The Adolescence of technology](https://www.darioamodei.com/essay/the-adolescence-of-technology)
* [AGI safety from first principles](https://www.alignmentforum.org/s/mzgtmmTKKn5MuCzFJ)
* [The Alignment Problem from a Deep Learning Perspective](https://arxiv.org/abs/2209.00626)

Non-misalignment safety problems

* Individual people may misuse AI in catastrophic ways:
  * Sections 2.1-2.3 in [An Overview of Catastrophic AI Risks](https://arxiv.org/pdf/2306.12001) argue for catastrophic misuse capabilities like bioterrorism, unleashing AI agents, and persuasive AIs. Misuse risk is particularly relevant to our course since it can also manifest as a misalignment concern: An AI that assists human users to carry out risks is often misaligned with the AI’s developer.
* AI can give rise to global totalitarianism
  * [Section 2.4](https://arxiv.org/pdf/2306.12001) argues for the potential of a concentration of power, leading to global totalitarianism in the worst case.
* We may get gradually disempowered even if there is alignment
  * [Gradual Disempowerment: Systematic Existential Risks from Incremental AI Development](https://arxiv.org/abs/2501.16946) argues that humans may be gradually disempowered, potentially leading to catastrophic outcomes, *even if* the alignment problem is technically solved.

\### Alignment targets

* [Coherent Extrapolated Volition](https://intelligence.org/files/CEV.pdf): Proposes AI should optimize for what humanity would want "if we knew more, thought faster, were more the people we wished we were".
* [Clarifying AI Alignment](https://ai-alignment.com/clarifying-ai-alignment-cec47cd69dd6): Defines "intent alignment" as AI trying to do what the operator wants.
* [Claude’s Constitution](https://www.anthropic.com/news/claude-new-constitution): aligning to a constitution rather than to individual human judgments.
  * [Alternative: OpenAI’s Model Spec](https://model-spec.openai.com/2025-12-18.html)
* [Corrigibility](https://www.lesswrong.com/w/corrigibility-1): Defines corrigibility as cooperating with human corrective interventions despite instrumental incentives to resist
* [Artificial Intelligence, Values, and Alignment](https://arxiv.org/abs/2001.09768): Distinguishes alignment with instructions, intentions, revealed preferences, ideal preferences, interests, and values.
* [AI alignment as the fair treatment of claims](https://link.springer.com/article/10.1007/s11098-025-02300-4)
* [Societal Alignment Frameworks](https://arxiv.org/abs/2503.00069v1): "we argue that improving LLM alignment requires incorporating insights from societal alignment frameworks, including social, economic, and contractual alignment"
* [Beyond Preferences in AI Alignment](https://arxiv.org/abs/2408.16984): "AI systems should be aligned with normative standards appropriate to their social roles, such as the role of a general-purpose assistant."
* [AI Control](https://blog.redwoodresearch.org/p/the-case-for-ensuring-that-powerful): "Labs should make sure that powerful models can't cause unacceptably bad outcomes even if the AIs try to."
* [A love for humanity](https://www.snexplores.org/article/artificial-intelligence-ai-safety-good-behavior): "Scott Aaronson says OpenAI’s cofounder, Ilya Sutskever, has asked him how to use math to define what it means for AI to love humanity. Right now, he has no idea how to answer that. But he sees it as a "North Star," or leading goal, he says. It’s a question "that should always be guiding us.""
* [Truthful AI](https://arxiv.org/abs/2110.06674): AI that does not lie

\### Alignment problem decompositions

A popular way to decompose AI alignment is into inner and outer alignment, where outer alignment is the problem of specifying an objective function that evaluates according to our intentions, and inner alignment is the problem of creating an AI system that performs optimally according to the objective function. This decomposition is contested and there exist alternatives, but it is still useful to be aware of it.

Outer Misalignment

* [Specification gaming: the flip side of AI ingenuity](https://deepmind.google/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)
  * [List of specification gaming examples](https://docs.google.com/spreadsheets/d/e/2PACX-1vRPiprOaC3HsCf5Tuum8bRfzYUiKLRqJmbOoC-32JorNdfyTiRRsR7Ea5eWtvsWzuxo8bjOxCG84dAg/pubhtml)
* [The Surprising Creativity of Digital Evolution](https://arxiv.org/abs/1803.03453): "many researchers in the field of digital evolution have observed their evolving algorithms and organisms subverting their intentions, exposing unrecognized bugs in their code, producing unexpected adaptations, or exhibiting outcomes uncannily convergent with ones in nature."
* [Reward misspecification](https://arxiv.org/abs/2201.03544), where the agent is rewarded positively for bad actions due to the general difficulty of designing reward functions that capture the developer’s intentions, is another key reason why AI systems may end up with wrong goals, already *on the training distribution* (making this conceptually distinct from generalization concerns). This is also called the *outer alignment problem*.
* [Categorizing variants of Goodhart’s law](https://arxiv.org/abs/1803.04585): Identifies four distinct failure modes (regressional, extremal, causal, adversarial) when proxies are over-optimized
* [Scaling laws for reward model overoptimization](https://arxiv.org/abs/2210.10760): Empirically demonstrates that optimizing against a learned reward model eventually degrades true reward
* [Defining and characterizing reward hacking](https://arxiv.org/abs/2209.13085): Provides formal definitions of reward hacking, proving that for any non-trivial proxy reward, unhackability is impossible.
* [Towards understanding sycophancy in language models](https://arxiv.org/abs/2310.13548): "both humans and preference models (PMs) prefer convincingly-written sycophantic responses over correct ones a non-negligible fraction of the time".
* [When your AIs deceive you](https://arxiv.org/abs/2402.17747): partial observability leading to outer misalignment.
* [Sycophancy to subterfuge](https://www.anthropic.com/research/reward-tampering): Shows progression from mild sycophancy to active reward tampering.
* [The effects of reward misspecification](https://arxiv.org/abs/2201.03544): Systematically categorizes reward misspecification types and shows higher agent capability leads to more reward hacking.
* [Faulty reward functions in the wild](https://openai.com/index/faulty-reward-functions/)
* [Consequences of misaligned AI](https://arxiv.org/abs/2102.03896): Shows that optimizing proxy rewards depending on a strict subset of relevant features can be arbitrarily bad under certain conditions.

Inner Misalignment

* Goal misgeneralization: One core reason why goals may misgeneralize out of distribution is an *underspecification* of the goal — i.e., there are several goals consistent with the AI’s behavior on the training set. [Goal misgeneralization](https://deepmind.google/blog/how-undesired-goals-can-arise-with-correct-rewards/) captures this concern ([original paper](https://proceedings.mlr.press/v162/langosco22a.html)).
* [Risks from Learned Optimization](https://arxiv.org/abs/1906.01820) is the general conceptual problem of ensuring that the trained AI agent ends up internally optimizing for the goals given to them during training — also called the *inner alignment problem*.
  * *Deceptive Alignment* is a particular failure mode in which an AI only *appears* to be aligned with its goals to gain trust and avoid modification, while it actually cares about something else, which might eventually lead to a treacherous turn as outlined above.
* [Alignment Faking](https://www.anthropic.com/research/alignment-faking) provides some empirical support for deceptive alignment, in which an AI fakes being aligned with its new goal in order to preserve its own goals and avoid modification. [It is controversial whether this is good or bad, and whether the framing as "alignment faking" is correct](https://www.lesswrong.com/posts/PWHkMac9Xve6LoMJy/alignment-faking-frame-is-somewhat-fake-1), since the model tries to preserve the helpful, honest, and harmless values it [obtained in its first alignment training.](https://arxiv.org/abs/2311.08379)
* [Gradient hacking](https://www.alignmentforum.org/posts/bdayaswyewjxxrQmB/understanding-gradient-hacking): Introduces the concept of a deceptively aligned mesa-optimizer deliberately influencing its own gradient updates to preserve its mesa-objective.
* [Scheming AIs: Will AIs fake alignment during training in order to get power?](https://arxiv.org/abs/2311.08379)
* [Sleeper Agents: Training deceptive LLMs that persist through safety training](https://arxiv.org/abs/2401.05566): Demonstrates that LLMs trained with backdoor behaviors persist through RLHF, SFT, and adversarial training.

Inductive Biases

* [Soft inductive biases](https://arxiv.org/abs/2503.02113)
* [Inductive biases for deep learning of higher-level cognition](https://arxiv.org/abs/2011.15091)
* [Emergent misalignment](https://arxiv.org/abs/2502.17424)
* [Natural emergent misalignment from reward hacking in production RL](https://assets.anthropic.com/m/74342f2c96095771/original/Natural-emergent-misalignment-from-reward-hacking-paper.pdf)
* Trained AI systems are [internally a mess](https://www.alignmentforum.org/posts/NJYmovr9ZZAyyTBwM/what-i-mean-by-alignment-is-in-large-part-about-making). They presumably contain a mix of beliefs, heuristics and online learning and planning algorithms, or something else.

Discussion on outer and inner alignment notions

* The decomposition of alignment into inner and outer alignment can be useful both for categorizing failure modes and solution strategies, but has been called into question due to [ambiguities arising in edge cases](https://www.lesswrong.com/posts/JKwrDwsaRiSxTv9ur/categorizing-failures-as-outer-or-inner-misalignment-is) and the opinion of many that [the problem should not be decomposed into two in practice](https://www.lesswrong.com/posts/gHefoxiznGfsbiAu9/inner-and-outer-alignment-decompose-one-hard-problem-into).
* [Reward is not the optimization target](https://www.alignmentforum.org/posts/pdaGN6pQyQarFHXF4)
* [Training stories as an alternative decomposition to outer and inner alignment](https://www.alignmentforum.org/posts/FDJnZt8Ks2djouQTZ/how-do-we-become-confident-in-the-safety-of-a-machine)

\### Goal-directedness

AI misalignment is arguably particularly bad if AI systems develop goals since this may via instrumental convergence lead to a drive to seek power.

Will AI systems develop goals?

* [Will humans build goal-directed agents?](https://www.alignmentforum.org/posts/9zpT9dikrrebdq3Jf/will-humans-build-goal-directed-agents)
* [Why tool AIs want to be agent AIs](https://gwern.net/tool-ai) is a classical text by Gwern arguing that AI agents are so useful that they will eventually be developed.
* A short informal explanation of this can be found in [How could a machine end up with its own priorities?](https://ifanyonebuildsit.com/3/how-could-a-machine-end-up-with-its-own-priorities) (appendix of "If Anyone Builds It, Everyone Dies")
* [Chapter 2.1, 2.2 and 2.4](https://raw.githubusercontent.com/yanshengjia/ml-road/47cadb02faa756f85fd2f058e31221cc8223b97a/resources/Artificial%20Intelligence%20-%20A%20Modern%20Approach%20%283rd%20Edition%29.pdf#%5B%7B%22num%22%3A705%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22Fit%22%7D%5D) of Russel and Norvig is also a good explanation of this and generally explains on a conceptual level what intelligent agents are.
* Also read [AI Goals Forecast](https://ai-2027.com/research/ai-goals-forecast#appendix-a-three-important-conceptsdistinctions) with a specific focus on the appendices to understand why AI systems trained via today’s (reinforcement learning) methods will likely develop goals at all.

Counter points:

* [Reframing Superintelligence: Comprehensive AI services as general intelligence](https://www.lesswrong.com/posts/x3fNwSe5aWZb5yXEG)

Instrumental Convergence / Power-Seeking

* [The Basic AI Drives](https://selfawaresystems.com/wp-content/uploads/2008/01/ai_drives_final.pdf): Pioneering argument that sufficiently advanced AI will exhibit convergent instrumental drives.
  * [Formalizing Convergent Instrumental Goals](https://cdn.aaai.org/ocs/ws/ws0218/12634-57409-1-PB.pdf)
* [The Superintelligent Will](https://nickbostrom.com/superintelligentwill.pdf): Formalizes the orthogonality thesis and the instrumental convergence thesis
* [Optimal Policies Tend to Seek Power](https://arxiv.org/abs/1912.01683): First formal proof that for most reward functions in MDPs, optimal policies seek power
* [Parametrically retargetable decision-makers tend to seek power](https://arxiv.org/abs/2206.13477): Extends power-seeking results beyond optimal policies to more realistic parameterized agents.

\### Forecasting risks

On how hard it is to achieve alignment

* Background: [The orthogonality thesis](https://www.lesswrong.com/w/orthogonality-thesis)
* Meta: [Model organisms](https://www.lesswrong.com/posts/ChDH335ckdvpxXaXX/model-organisms-of-misalignment-the-case-for-a-new-pillar-of-1) to learn more about the level of risk.
* The main article in the [AI Goals Forecast](https://ai-2027.com/research/ai-goals-forecast) shows the plurality of possible goals that an AI system may inherently want to pursue, some of which may be very bad for us.
* [Sharp left turn](https://www.alignmentforum.org/posts/GNhMPAWcfBCASy8e6/a-central-ai-alignment-problem-capabilities-generalization): Argues that when AI capabilities begin to generalize powerfully, alignment properties predictably fail to generalize with them.
* [AGI ruin: A list of lethalities](https://www.lesswrong.com/posts/uMQ3cqWDPHhjtiesc/agi-ruin-a-list-of-lethalities): 43 reasons AGI alignment is lethally difficult, covering first-try requirements, deceptive alignment, inability to iterate, and the analogy to evolution producing misaligned general intelligence.
* [AI Alignment remains hard and unsolved](https://www.lesswrong.com/posts/epjuxGnSPof3GnMSL/alignment-remains-a-hard-unsolved-problem)
* [Where I agree and disagree with Eliezer](https://www.lesswrong.com/posts/CoZhXrhpQxpy9xw9y/where-i-agree-and-disagree-with-eliezer): Paul Christiano’s response
* [Core views on Safety](https://www.anthropic.com/news/core-views-on-ai-safety) by Anthropic: Presents a three-tier portfolio approach: optimistic (current techniques largely sufficient), intermediate (substantial scientific work needed), pessimistic (alignment may be impossible)
* [AI is easy to control](https://optimists.ai/2023/11/28/ai-is-easy-to-control/)

Overall risk assessments

* [Is Power-Seeking AI an Existential Risk?](https://arxiv.org/abs/2206.13353): estimating >10% probability of existential catastrophe from misaligned power-seeking AI by 2070.
* [Chapter 8 in Superintelligence — "Is the default outcome doom?"](https://repo.darmajaya.ac.id/5339/1/Superintelligence_%20Paths%2C%20Dangers%2C%20Strategies%20%28%20PDFDrive%20%29.pdf#page=13.32)
* [Misalignment and catastrophe are the default outcomes of training powerful AI](https://intelligence.org/wp-content/uploads/2024/12/Misalignment_and_Catastrophe.pdf)
* [Without specific countermeasures, the easiest path to transformative AI likely leads to AI takeover](https://www.lesswrong.com/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to)
* [Thousands of AI authors on the future of AI](https://arxiv.org/abs/2401.02843): Between 38% and 51% of respondents gave at least a 10% chance to advanced AI leading to outcomes as bad as human extinction.
* "The Precipice: Existential Risk and the Future of Humanity" (Ch. 5) — Toby Ord (2020). Estimates existential risk from unaligned AI at ~1 in 10 over the next century within a comprehensive risk landscape framework.

Scenarios

* [What failure looks like](https://www.lesswrong.com/posts/HBxe6wdjxK239zajf/what-failure-looks-like): Sketches two failure scenarios: systems pursuing easy-to-measure proxies that diverge from human values, and systems with emergent influence-seeking behavior.
* [Treacherous turn](https://publicism.info/philosophy/superintelligence/9.html)
* [If Anyone Builds It, Everyone Dies: Why Superhuman AI Would Kill Us All](https://en.wikipedia.org/wiki/If_Anyone_Builds_It,_Everyone_Dies): Book-length argument that creating vastly smarter-than-human AI using anything like current techniques would very likely result in human extinction.

\### Theoretical vs. empirical vs. other approaches

Case for empirical work

* [Prosaic AI alignment](https://ai-alignment.com/prosaic-ai-control-b959644d79c2): argues that we should focus on trying to align AI systems that are similar to the ones already built today (2016, tbc.!) since perhaps AGI will be developed without a fundamental understanding of AGI.
* [Anthropic’s core view on safety](https://www.anthropic.com/news/core-views-on-ai-safety): "We are most optimistic about a multi-faceted, empirically-driven approach to AI safety"
* [Our approach to alignment research](https://openai.com/index/our-approach-to-alignment-research/) by OpenAI (2022): following feedback, assisting evaluations, doing alignment research
* [Why I’m optimistic about our alignment approach](https://aligned.substack.com/p/alignment-optimism), Jan Leike

Case for mathematical work

* [The rocket alignment problem](https://www.alignmentforum.org/posts/Gg9a4y8reWKtLe3Tn/the-rocket-alignment-problem)
* [Why agent foundations? An overly abstract explanation](https://www.lesswrong.com/posts/FWvzwCDRgcjb9sigb/why-agent-foundations-an-overly-abstract-explanation)
* [Agent foundations for aligning machine intelligence with human interests](https://intelligence.org/files/TechnicalAgenda.pdf): "the authors believe that there are theoretical prerequisites for designing aligned smarter-than-human systems over and above what is required to design misaligned systems"
* [AI alignment metastrategy](https://www.lesswrong.com/posts/TALmStNf6479uTwzT/ai-alignment-metastrategy): argues for halting capability work and developing theory of intelligent agents
* [Towards guaranteed safe AI](https://arxiv.org/abs/2405.06624)

Philosophical/conceptual work

* [Problems in AI alignment that philosophers could potentially contribute to](https://www.lesswrong.com/posts/rASeoR7iZ9Fokzh7L/problems-in-ai-alignment-that-philosophers-could-potentially)
* [Problems I’ve tried to legibilize](https://www.alignmentforum.org/posts/7XGdkATAvCTvn4FGu/problems-i-ve-tried-to-legibilize) by Wei Dai

Against many plans, empirical and theoretical

* [On how various plans miss the hard bits of the alignment challenge](https://www.lesswrong.com/posts/3pinFH3jerMzAvmza/on-how-various-plans-miss-the-hard-bits-of-the-alignment): Arguing about everyone else’s (empirical) plan

\### Timelines and takeoff

* [AI 2027](https://ai-2027.com/), and its [August 2026 update](https://blog.aifutures.org/p/q25-2026-timelines-update-uplift).
* [Nuno Sempere's Epoch research thread](https://x.com/NunoSempere/status/2103155734586220630) and the [roadmapping essay](https://epoch.ai/gradient-updates/the-missing-half-of-ai-futurism-debates) it highlights.
* [Davidson's compute-centric takeoff framework](https://coefficientgiving.org/research/what-a-compute-centric-framework-says-about-takeoff-speeds/) and [Epoch's interactive implementation](https://takeoffspeeds.com/).
* FRI: [LEAP](https://leap.forecastingresearch.org/), [Wave 8 timelines](https://leap.forecastingresearch.org/reports/wave8), and [forecast accuracy retrospective](https://forecastingresearch.org/research/ai-progress-accuracy-update).

\### Training and the Hugging Face case

* [Training language models to follow instructions with human feedback](https://arxiv.org/abs/2203.02155), for a concrete historical training pipeline.
* Hugging Face: [initial disclosure](https://huggingface.co/blog/security-incident-july-2026) and [technical reconstruction](https://huggingface.co/blog/agent-intrusion-technical-timeline).
* OpenAI: [August investigation](https://openai.com/index/hugging-face-incident-and-the-road-ahead/) and [September review update](https://openai.com/hugging-face-incident-and-misalignment/).
* METR: [independent investigation of agent behavior](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/).
* Report from inside: [OpenAI cybersecurity insider](https://x.com/joedaroo/status/2104335929293127851?s=20)

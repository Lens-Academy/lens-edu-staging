---
id: '0afa9eec-e5d6-45a9-9e90-50dc477df9d4'
title: "D.4.1.3 The five strands and the exercise plan"
tldr: "The five strands with their readings (consequentialist foundations, Löb and tiling agents, logical induction, optimization and thermodynamics, descriptive agent foundations), the cross-pollination discussion, and the exercise plan."
summary_for_tutor: "Sections 2.2.3 to 2.2.5 and 2.3 'Learn more' of Iliad worksheet D.4.1 Agent Foundations. Each of the five strands has a self-contained summary with a takeaway and readings: money pumps and the complete class theorem; Vingean reflection, Löb's theorem and the finite descent problem; logical induction and its criterion; entropy reduction, the Touchette-Lloyd inequality and algorithmic thermodynamics; selection theorems and modularity. It also describes the cross-pollination discussion and lists Exercises 3.1-3.5 (with difficulty and importance ratings), and ends with further reading."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/agent-foundations/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\#### 2.2.3 The five strands (pre-reading tracks)

*The five strands are different facets of one problem, embedded agency; each student pre-reads one. Every summary below is self-contained at the conceptual level and ends with that strand's readings (start with the first listed, which is the most conceptual). The morning lecture previews all five; the cross-pollination discussion connects them.*

**1. Consequentialist foundations.** If an agent's preferences are cyclic, an adversary can money-pump it through trades that each look acceptable but leave it strictly worse off. So any agent that reliably avoids such dominated strategies behaves *as if* it maximizes a utility function. The **complete class theorem** sharpens this: any decision rule that is not dominated (Pareto-optimal across environments) is Bayes-optimal under some prior with full support. This is *representational*, not mechanistic: it says a capable, non-self-defeating agent looks like a Bayesian expected-utility maximizer from the outside, without saying it has a utility function inside, and without telling us *which* utility function (the hard part). *Takeaway: coherence gives a reflectively-stable target (a dominated strategy is one a rational agent would self-modify away from), but it under-determines the agent's actual goals.* *Readings:* [Coherent decisions imply consistent utilities](https://www.lesswrong.com/s/SgomvxZ3cJWy2SBCu/p/RQpNHSiWaXTvDxt6R) (Introduction; "Why not circular preferences?"; "Probabilities and expected utilities" through "Conditional probability"; Conclusion); [The measuring stick of utility](https://www.lesswrong.com/posts/73pTioGZKNcfQmvGF/the-measuring-stick-of-utility-problem); [Complete class: consequentialist foundations](https://www.lesswrong.com/posts/sZuw6SGfmZHvcAAEP/complete-class-consequentialist-foundations).
::card[[../Lenses/yudkowsky-coherent-decisions-imply-consistent-utilities|Coherent decisions imply consistent utilities]]

::card[[../Lenses/johnswentworth-the-measuring-stick-of-utility-problem|The measuring stick of utility]]

::card[[../Lenses/abramdemski-complete-class-consequentialist-foundations|Complete class: consequentialist foundations]]

**2. Löb's theorem and tiling agents.** A capable agent may build a successor more capable than itself. By *Vingean reflection*, it cannot verify the successor by simulating it (if it could predict the successor's exact moves, it would be that capable already), so it must reason abstractly about the successor's *design*. The natural strategy ("trust the successor because it only takes actions it has proved safe") needs the parent to trust the successor's proofs. **Löb's theorem** blocks this: if a consistent system `L` can prove "if `L` proves `C` then `C`", then `L` already proves `C`. A consistent system cannot vouch for its own proofs in the abstract, only for a strictly weaker system's. So a naive chain of self-improvements uses an ever-weaker proof system (a "telomere" of logical strength that runs out), the *finite descent problem*. The tiling-agents programme studies whether this obstacle can be overcome. *Takeaway: self-trust under self-modification is not free; it runs straight into a logical wall.* *Readings:* [Introduction to Löb's theorem](https://intelligence.org/files/lob-notes-IAFF.pdf) (up to and including section 3); [Vingean reflection](https://www.lesswrong.com/w/vingean-reflection); [Walkthrough of the tiling agents paper](https://www.lesswrong.com/posts/QGrX3qK3qxQYK9D4C/walkthrough-of-the-tiling-agents-for-self-modifying-ai-paper) (start through "Finite Descent Problem", then "What self-modifying agents need").

::card[[../Lenses/lavictoire-an-introduction-to-l-bs-theorem-in-miri-research|Introduction to Löb's theorem]]

::card[[../Lenses/lesswrong-vingean-reflection|Vingean reflection]]

::card[[../Lenses/so8res-walkthrough-of-the-tiling-agents-for-self-modifying-ai-paper|Walkthrough of the tiling agents paper]]

**3. Logical induction.** Standard Bayesian reasoning assumes *logical omniscience*: the agent instantly knows all consequences of its beliefs. A bounded agent cannot (it may know a program's source yet not its output, or the axioms yet not whether a number is prime). **Logical induction** (Garrabrant et al.) handles this by picturing a market that prices logical sentences in [0,1]; the *logical-induction criterion* requires only that no efficient (polynomial-time) trader can exploit the market for unbounded profit, a computable weakening of the Dutch-book argument. That single condition yields convergence and coherence in the limit, timely learning of statistical patterns (it prices "the nth digit of pi is 7" near 1/10 without computing it), and *self-trust* (current credence equals a weighted average of expected future credences). *Takeaway: a principled model of how a bounded agent should hold probabilities over facts it has not yet computed.* *Readings:* [An intuitive guide to Garrabrant induction](https://www.lesswrong.com/posts/y5GftLezdozEHdXkL/an-intuitive-guide-to-garrabrant-induction); [Logical induction](https://arxiv.org/pdf/1609.03543) (chapters 1 and 3; skim chapter 4).

::card[[../Lenses/xu-an-intuitive-guide-to-garrabrant-induction|An intuitive guide to Garrabrant induction]]

**4. Optimization and thermodynamics.** A powerful agent reliably steers the world into a narrow region of outcomes, ones extremely unlikely under any random process. This is *local entropy reduction*: concentrating probability mass from a broad initial distribution onto a narrow target. Even a pure predictor has an objective reason to attend to optimizers: naming what an optimizer steers toward predicts the outcome cheaply and robustly, where modelling the initial conditions would be expensive and chaos-fragile. Steering is bounded by information: the **Touchette-Lloyd** inequality says the entropy reduction a sighted agent achieves over a blind baseline is at most the mutual information between its observations and actions ($$\Delta H \leq \Delta H_{\text{blind}}^{\max}+ I(X;A)$$). *Algorithmic thermodynamics* (Ebtekar and Hutter) replaces ensemble entropy with Kolmogorov complexity, giving laws for individual states and making an embedded agent's knowledge an endogenous physical quantity (algorithmic mutual information between memory and environment), which is exactly its budget for optimization. *Takeaway: optimization is physically constrained, and "knowing more" formally means "being able to optimize more."* *Readings:* the self-contained note [Optimization and thermodynamics](https://iliad-intensive.org/agency/optimization-thermodynamics) (read entirely; appendix optional) is the primary reading; its underlying sources are [The ground of optimization](https://www.lesswrong.com/posts/znfkdCoHMANwqc2WE/the-ground-of-optimization-1) (up to and including "Relationship to Garrabrant and Demski's Embedded Agency"), [Generalized heat engine](https://www.lesswrong.com/posts/uKWXktrR7KpbgZAs4/generalized-heat-engine), and [Algorithmic thermodynamics and three types of optimization](https://www.lesswrong.com/posts/CJRxQiTKEzior7jGq/algorithmic-thermodynamics-and-three-types-of-optimization).

::card[[../Lenses/flint-the-ground-of-optimization|The ground of optimization]]

::card[[../Lenses/johnswentworth-generalized-heat-engine|Generalized heat engine]]

::card[[../Lenses/c-algorithmic-thermodynamics-and-three-types-of-optimization|Algorithmic thermodynamics and three types of optimization]]

**5. Descriptive agent foundations.** *Normative* agent foundations asks what an ideal agent should look like; *descriptive* asks what agents actually arising in the world (bacteria, neural networks, future AI) look like, and aims to read off their goals, world model, and decision structure from the outside. It works bottom-up from properties of the world (modularity, selection pressures, computational limits). **Selection theorems** aim to prove results of the form "any system selected to achieve goal G in environment E must contain structure approximately isomorphic to X", giving mechanistic rather than merely representational accounts of agency. A key example: the world's *modularity* (it decomposes into sparsely-interacting subsystems) is what makes both world-modelling (Bayesian networks propagate updates locally) and planning (general-purpose search can pursue decoupled subgoals) tractable. *Takeaway: the complementary direction to coherence: not "non-dominated agents can be described as maximizers" but "what pressures make agent-like structure actually arise."* *Readings:* [Selection theorems: a program for understanding agents](https://www.lesswrong.com/posts/G2Lne2Fi7Qra5Lbuf/selection-theorems-a-program-for-understanding-agents); [How we picture Bayesian agents](https://www.lesswrong.com/posts/TiBsZ9beNqDHEvXt4/how-we-picture-bayesian-agents); [What selection theorems do we expect/want](https://www.lesswrong.com/posts/RuDD3aQWLDSb4eTXP/what-selection-theorems-do-we-expect-want).

::card[[../Lenses/johnswentworth-selection-theorems-a-program-for-understanding-agents|Selection theorems: a program for understanding agents]]

::card[[../Lenses/johnswentworth-how-we-picture-bayesian-agents|How we picture Bayesian agents]]

::card[[../Lenses/johnswentworth-what-selection-theorems-do-we-expectwant|What selection theorems do we expect/want]]

\#### 2.2.4 Cross-pollination discussion

On the day, students who pre-read different strands meet in small mixed groups and work to connect their topics into one picture of embedded agency: how a logical inductor's trust in its future self relates to a tiling agent's trust in its successor, how the coherence account of goals relates to the thermodynamic one, how the representational view of agency (coherence) relates to the mechanistic one (selection theorems). The specific discussion prompts used are listed in the teaching guide.

\#### 2.2.5 Exercise session

Five exercises (full statements and worked solutions in Section 3), grouped by topic:

*Logical uncertainty and self-reference.*

- **Exercise 3.1: Gödel's second incompleteness theorem** (difficulty 4/5, importance 4/5). Via a self-referential program: a Gödel sentence is true, a consistent system cannot prove its own consistency, and this is exactly the Löbian obstacle to self-trust. Parts (a) true Gödel sentence, (b) no self-consistency proof, (c) the obstacle.
- **Exercise 3.2: Löb's theorem** (difficulty 3/5, importance 5/5). The three provability properties (necessitation, distribution, the Löb condition), a full proof of the theorem, and an application: FairBot programs cooperate by Löb's theorem. Parts (a-b) properties, (c-d) the proof, (e) FairBot.

*Coherence and consequentialism.*

- **Exercise 3.3: The complete class theorem** (difficulty 3/5, importance 5/5). The equivalence between non-dominated strategies and Bayesian expected-utility maximization, via a geometric argument over the convex set of attainable reward vectors. Parts (a) admissibility, (b) faces and difference vectors, (c) constructing the rationalizing prior.

*Descriptive agent foundations.*

- **Exercise 3.4: The do-divergence theorem** (difficulty 2/5, importance 4/5). Formalizes optimization as outcome concentration and proves that how far an agent can steer outcomes (a KL divergence from the unsteered baseline) is bounded by the mutual information between its observations and actions. The single-step backbone of the Touchette-Lloyd picture.
- **Exercise 3.5: Channel additivity** (difficulty 3/5, importance 3/5). Optimal input distributions over independent channels: mutual information decomposes across channels, independence improves throughput, and an optimal policy need not coordinate across a modular environment (connecting modularity to tractable optimization).

\### 2.3 Learn more

The readings for each strand are linked under that strand in the Main content above. Beyond them:

**Algorithmic thermodynamics (Ebtekar).** [Foundations of algorithmic thermodynamics](https://arxiv.org/abs/2308.06927); [Modelling the arrows of time with causal multibaker maps](https://www.mdpi.com/1099-4300/26/9/776); [Long-time derivation of the Boltzmann equation from hard-sphere dynamics](https://arxiv.org/abs/2408.07818).

**Embedded and universal AI (Wyeth).** [Limit-computable grains of truth](https://arxiv.org/pdf/2508.16245); [Embeddedness failures in universal artificial intelligence](https://arxiv.org/pdf/2505.17882); [Value under ignorance](https://arxiv.org/pdf/2512.17086).

**Other directions.** [Introduction to the infra-Bayesianism sequence](https://www.lesswrong.com/posts/zB4f7QqKhBHa5b37a/introduction-to-the-infra-bayesianism-sequence) (non-realizable environments); [The learning-theoretic agenda](https://www.lesswrong.com/posts/ZwshvqiqCvXPsZEct/the-learning-theoretic-agenda-status-2023); [Optimization at a distance](https://www.lesswrong.com/posts/d2n74bwham8motxyX/optimization-at-a-distance); the [hard problem of corrigibility](https://www.lesswrong.com/w/hard-problem-of-corrigibility) and a [critique of the corrigibility basin of attraction](https://www.lesswrong.com/posts/oLbpfPkdtcknABvvw/the-corrigibility-basin-of-attraction-is-a-misleading-gloss); the original [tiling agents draft](https://intelligence.org/files/TilingAgentsDraft.pdf); and background notes on [admissibility and the complete class theorem](https://www2.stat.duke.edu/~pdh10/Teaching/581/LectureNotes/admiss.pdf) and the [Dutch book argument](https://www.stat.berkeley.edu/~census/dutchdef.pdf).

**Research frontier.** The *agent structure problem* (whether strong optimization provably entails an internal world model), embedded variants of AIXI, and resource-theoretic accounts of instrumental convergence.

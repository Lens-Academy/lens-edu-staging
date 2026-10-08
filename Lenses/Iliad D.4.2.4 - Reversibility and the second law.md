---
id: '2876d3e7-385d-4d1b-8b09-a8262f042da5'
title: "D.4.2.4 Reversibility and the second law"
tldr: "Why microscopic physics is reversible, why that conflicts with funneling, how coarse-graining gives probability, and the proof of the second law for doubly stochastic chains."
summary_for_tutor: "Section 4 (4.1-4.5) of Iliad worksheet D.4.2. Covers reversibility, the incompatibility of global funneling with it, coarse-graining into a Markov chain with doubly stochastic transitions (Liouville), Theorem 4.1 (Second Law: H(Y) >= H(X)) with a two-step proof via the data processing inequality, and the scope and limits of the second law (isolated systems, ensemble entropy, fixed dynamics). Footnote 1 on unequal cell volumes is included. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Reversibility and the second law

\### 4.1 The reversibility of microscopic physics

Having introduced the convergent-attractor picture of optimization, we now examine the physical constraints that any such process must respect, beginning with the observation that, at the most fundamental level of description available to us, physical systems never lose information. In classical mechanics, the complete microscopic state of a system, its *microstate*, consists of the position and momentum of every particle, corresponding to a single point in the system's *phase space*. The laws of motion carry each microstate along a unique trajectory, determining the future from the present and, equally, the past from the present. It follows that two distinct microstates can never evolve into the same state: if they did, running the laws backward from the shared future state could not determine which of the two microstates to recover, and the dynamics admit no such ambiguity. Over any fixed interval, therefore, the evolution of an isolated system constitutes a *bijection* on microstates, an invertible pairing of initial states with final states. Liouville's theorem strengthens this conclusion: the evolution preserves not only distinctness but phase-space *volume*, allowing a region of microstates to be stretched and folded without limit while retaining its total volume. Quantum mechanics expresses the same principle in different notation: isolated evolution is unitary, hence invertible and volume-preserving. In either formulation, microscopic information is neither created nor destroyed.

\### 4.2 The incompatibility of global funneling with reversibility

Given the reversibility of the microscopic dynamics established above, we now confront the convergent-attractor picture of optimization with this fundamental property. Taken literally at the microscopic level, the two are directly incompatible: funneling requires that many initial states converge to the same small set of target states, constituting a many-to-one map, whereas reversibility guarantees that the microscopic dynamics are one-to-one, rendering a perfect funnel microscopically impossible.

A second, closely related obstruction arises from the second law of thermodynamics itself, the principle that the entropy of an isolated system tends not to decrease. In the framework we are about to develop, the second law is not an additional postulate but a *consequence* of reversibility, and understanding this derivation illuminates both principles. The resolution of the apparent paradox—optimization manifestly occurs, yet physics forbids funneling—is provided by the central "bookkeeping" principle of these notes:

> *No physical process can reduce the entropy of an isolated system. Optimization is entropy reduction in a coarse-grained description of a subsystem, and the information displaced from the optimized subsystem must be accounted for elsewhere in the larger system.*

The remainder of this section renders the first sentence precise and establishes it rigorously. Section 5 and Appendix B address the second sentence, characterizing where the displaced information can reside and quantifying how much entropy reduction an agent can accomplish.

\### 4.3 Coarse-graining and the emergence of probability

The preceding discussion prompts a natural question: if the microscopic dynamics are deterministic and information-preserving, from where does probability arise, and what accounts for the rise of entropy? The answer lies in the fact that no observer ever tracks the microstate. A gram of matter possesses on the order of $$10^{23}$$ coordinates, each specified to unbounded precision, a description that no observer, and no embedded agent, can maintain. What is tracked instead is a *coarse-grained* description: we partition the phase space into discrete cells, each aggregating all microstates that cannot be distinguished at the chosen resolution (for instance, every particle's position and momentum specified to finitely many digits, or merely a small collection of macroscopic variables), and describe the system by identifying the cell it currently occupies.

The dynamics of cells, in contrast to the dynamics of microstates, are genuinely stochastic. The current cell does not determine the next one, because different microstates within the same cell flow to different destinations. The most complete description available is a transition probability $$P(y, x)$$, defined as the fraction of cell $$x$$, measured by phase-space volume, that arrives in cell $$y$$ one step later. This randomness is not metaphysical in character; it reflects precisely the microscopic detail that the coarse description declines to resolve. Chaotic dynamics continually transport such detail upward across the resolution scale, so that the coarse trajectory resembles a sequence of random jumps even though the underlying flow remains deterministic.

One structural assumption underlies the whole of stochastic thermodynamics: the coarse trajectory constitutes a *Markov process*, meaning that the distribution of the next cell depends only on the current cell and not on the earlier history. The intuition is that a sufficiently good coarse-graining ensures that the current cell contains everything about the past that is relevant to the coarse future, with the discarded detail contributing independent noise at each step rather than persisting as hidden memory. Whether a given coarse-graining is genuinely Markovian remains a deep and open question, but two considerations provide reassurance. First, there exist exactly solvable models, the *multibaker maps*: deterministic, time-reversible, chaotic systems whose coarse-grainings provably reproduce arbitrary Markov chains, with all of the randomness residing in the initial condition. These models demonstrate that macroscopic stochasticity and irreversibility are fully compatible with microscopic determinism and reversibility. Second, the Markov property is precisely what renders everyday statistical reasoning valid, and its *failure backward in time* constitutes the arrow of time. A dropped glass shatters at a predictable moment, and its shards obey well-defined local statistics that are entirely independent of events occurring at a neighboring house. Under time reversal this description fails: retrodicting the moment at which the shattered glass was dropped cannot be accomplished through local statistics, and the most informative evidence available to an observer may be a conversation about the accident taking place next door. Forward evolution obeys memoryless local laws while backward evolution does not, and this asymmetry is exactly the content of the Markov property.

One further consequence of reversibility remains to be extracted before we establish the second law. Liouville's theorem renders phase-space volume a *stationary measure* of the chain: weighting each cell by its volume produces a weighting that a single step carries to itself. We take all cells to have equal volume (a *mesoscopic* coarse-graining, obtained by truncating every coordinate to a fixed precision). Stationarity of the uniform weighting then determines the structure of the transition probabilities: with $$\pi$$ constant, the condition $$\sum_{x} P(y,x)\,\pi(x) = \pi(y)$$ reduces to $$\sum_{x} P(y, x) = 1$$ for every $$y$$, so that the probabilities flowing *into* each cell sum to one, exactly as those flowing *out of* each cell do. A matrix satisfying both properties is termed *doubly stochastic*. Double stochasticity is thus the characteristic imprint of reversibility on the coarse dynamics: a doubly stochastic step can permute and disperse probability but can never concentrate it, since concentration would require packing several cells' worth of volume into fewer cells, which Liouville's theorem forbids.[^1]

\### 4.4 The second law of thermodynamics

We now establish the second law for the class of doubly stochastic coarse-grained dynamics identified above, namely that the entropy of the coarse-grained state cannot decrease under a single step of the chain.

:::callout {title="Theorem" tone="green"}

**Theorem 4.1 (Second Law for Doubly Stochastic Chains).** Let $$P$$ be a doubly stochastic transition matrix on a countable state space, let the random variable $$X$$ (the coarse-grained state now) have distribution $$\mu$$, and let $$Y$$ (the state one step later) have distribution $$P\mu$$, where $$(P\mu)(y) := \sum_{x} P(y,x)\,\mu(x)$$. Then

$$
H(Y) \;\ge\; H(X).
$$

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

We establish the theorem in two steps.

**Step 1: contraction of divergence under a single Markov step.** Let $$\mu$$ and $$\nu$$ be any two distributions (or nonnegative measures) on the state space. We claim the data processing inequality

$$
D(P\mu \,\|\, P\nu) \;\le\; D(\mu \,\|\, \nu).
$$

To verify this claim, we fix an output state $$y$$ and apply the log-sum inequality (Lemma 2.9) to the numbers $$a_{x} = P(y,x)\mu(x)$$ and $$b_{x} = P(y,x)\nu(x)$$, whose sums over $$x$$ are $$P\mu(y)$$ and $$P\nu(y)$$ respectively:

$$
\sum_{x} P(y,x)\mu(x) \log \frac{P(y,x)\mu(x)}{P(y,x)\nu(x)}\;\ge\; P\mu(y) \log \frac{P\mu(y)}{P\nu(y)}.
$$

We now sum this inequality over all $$y$$. On the left-hand side, the factor $$\log\frac{\mu(x)}{\nu(x)}$$ does not depend on $$y$$, and $$\sum_{y} P(y,x) = 1$$ because $$P$$ is stochastic, so the left-hand side totals $$\sum_{x} \mu(x)\log\frac{\mu(x)}{\nu(x)}= D(\mu\|\nu)$$; the right-hand side totals $$D(P\mu \| P\nu)$$, which establishes the claim. The underlying intuition is precisely the coding-theoretic one: passing two information sources through the same noisy channel can only render them more difficult to distinguish.

**Step 2: specialization of the reference measure to the uniform measure.** Let $$\sharp$$ denote the counting measure, $$\sharp(x) = 1$$ for every $$x$$ (an unnormalized uniform measure; Lemma 2.9 at no point required normalization). Double stochasticity of $$P$$ states precisely that $$P\sharp = \sharp$$, since $$(P\sharp)(y) = \sum_{x} P(y,x) = 1$$. Moreover, divergence from the counting measure is simply negative entropy:

$$
D(\mu \,\|\, \sharp) \;=\; \sum_{x} \mu(x) \log \frac{\mu(x)}{1}\;=\; -H(\mu).
$$

Applying Step 1 with $$\nu = \sharp$$ yields

$$
-H(P\mu) \;=\; D(P\mu \,\|\, P \sharp) \;\le\; D(\mu \,\|\, \sharp) \;=\; -H(\mu),
$$

which rearranges to $$H(P\mu) \ge H(\mu)$$.

:::

We draw attention to the ingredients of the proof: the list is short, and every item is physical in origin. The argument invoked the Markov property, which permitted a single step to be written as a transition matrix, and double stochasticity, which followed from Liouville's theorem, that is, from the *reversibility* of the microscopic dynamics; nothing further was required. Consequently, macroscopic irreversibility, the rise of entropy, stands in no tension with microscopic reversibility; it follows from it, once we grant that observers track coarse cells rather than microstates. This is the precise content of the assertion that "the second law follows from the reversibility of physics".

\### 4.5 The scope and limitations of the second law

Three clarifications delineate the scope of this result and prevent misreadings that become consequential in later sections.

First, Theorem 4.1 applies to an *isolated* system evolving autonomously: the entropy of the whole cannot decrease. The theorem asserts nothing against the entropy of a *subsystem* decreasing, and the entropy of subsystems decreases constantly; this is precisely what refrigerators, crystallization, house-builders, and every other optimizer accomplish. What the theorem imposes is a bookkeeping constraint on the whole: when the entropy of a subsystem drops, the global accounting must remain consistent, with at least as much entropy appearing elsewhere in the total system. The complete classification of where this "elsewhere" can be located is the subject of Section 5.

Second, the theorem as stated concerns the entropy of the *ensemble*, that is, of the probability distribution $$\mu$$, and it holds on average and in distribution; individual trajectories may pass through improbable, low-codelength states. A sharper, trajectory-level version of the second law, equipped with explicit and very small bounds on the permitted fluctuations, becomes available in the algorithmic framework of Section 7.

Third, and most consequentially for the remainder of these notes, the theorem assumed a fixed dynamics $$P$$ uninfluenced by any observer, together with an entropy defined relative to a given distribution $$\mu$$. Agents complicate both assumptions. An agent that *observes* the system and conditions its behavior on its observations does not constitute a fixed $$P$$; the extent of the advantage this confers, and the cost at which it is purchased, is the subject of Appendix B. Furthermore, the apparently innocuous reliance on a given $$\mu$$ conceals a deep conceptual problem, which we address in Section 6. Before turning to these questions, however, we take up the bookkeeping question directly: when an agent lowers the entropy of a subsystem, the question arises of where the displaced entropy can reside, and the following section provides the complete answer. (A self-contained toy model in which every step can be verified by hand is developed separately in Appendix A.)

[^1]: The entire framework developed in these notes generalizes to coarse-grainings with unequal cell volumes: entropy is then measured *relative to* the stationary volume measure $$\pi$$, replacing $$H(\mu)$$ by $$H_{\pi}(\mu) := \sum_{x} \mu(x) \log \frac{\pi(x)}{\mu(x)}$$ and the codelength by $$\hat H_{\pi}(x,\mu) := \log\frac{\pi(x)}{\mu(x)}$$. This generalization is standard, but it is not required for any of our subsequent results; the assumption of equal cells simplifies the notation at no conceptual cost.

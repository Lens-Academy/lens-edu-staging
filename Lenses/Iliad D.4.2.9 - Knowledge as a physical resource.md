---
id: 'd1271297-9f64-422b-b316-76334c16ae08'
title: "D.4.2.9 Knowledge as a physical resource"
tldr: "How an embedded agent's knowledge becomes the algorithmic mutual information I(a : s) that sets its optimization capacity, and how this removes the apparent subjectivity of entropy."
summary_for_tutor: "Section 8 (8.1-8.4) of Iliad worksheet D.4.2. Knowledge as I(a : s) = K(s) - K(s | a), the bridge from beliefs q to mutual information and to optimization (residual about log 1/q(s)), knowledge as a consumed and decaying resource, refinements of Types 1-3 via compressibility, the resolution of the demon's apparent subjectivity, and implications for optimizing systems. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 8. Knowledge as a physical resource: optimization for embedded agents

Having developed the algorithmic account of entropy and examined the channels through which entropy can be displaced, we now synthesize the preceding sections into a single unified picture: for an embedded agent, knowledge about the environment constitutes a physical resource, and this resource is the same quantity as the agent's capacity to optimize the environment.

\### 8.1 From exogenous to endogenous knowledge

We begin by comparing how the two frameworks account for an agent's knowledge of a system.

In the Gibbs–Shannon framework, what an agent knows about a system is encoded in the distribution $$\mu$$, and $$\mu$$ is supplied from outside the physics, so that entropy, work capacity, and therefore optimization capacity are all defined relative to it. Two problems follow from this exogenous treatment: first, if we change $$\mu$$, the physics appears to change (the problem of Section 6.4); second, $$\mu$$ is entirely unconstrained, so knowledge can be introduced at no physical cost (the loophole of Section 6.3). At equilibrium neither problem arises, because there the appropriate $$\mu$$ is both forced and simple; the problems become acute precisely when the agent's knowledge is the component of interest.

For an embedded agent no such outside ledger exists. Its knowledge of the environment must be stored physically, in a memory composed of the same matter as the environment and governed by the same laws, and algorithmic thermodynamics enables us to handle this knowledge directly. Writing $$a$$ for the physical state of the agent's memory and $$s$$ for the physical state of the environment, "what the agent knows about the environment" is the algorithmic mutual information

$$
I(a : s) \;{\mathrel{\stackrel{+}{=}}}\; K(s) - K(s \mid a),
$$

the number of bits by which the agent's memory shortens the description of the environment. No distribution appears in this expression: knowledge has become an objective relation between two pieces of matter, as much a fact about the world as a distance or a voltage. Subjective beliefs are not discarded but rather *implemented*: an agent whose memory holds a good model of the environment is one whose state has high $$I(a:s)$$, and $$K(s \mid a)$$ is the environment's entropy *as that agent finds it* (the environment's entropy as evaluated from the demon's perspective, Section 7.4).

**The Correspondence Between Knowledge and Optimization Capacity.**  A fundamental insight emerging from this framework is that an agent which understands its environment more thoroughly can effect correspondingly greater change upon it, and the framework renders this intuition precise by joining two bridges: the first passing from the agent's beliefs to mutual information, and the second from mutual information to optimization.

*From beliefs to mutual information.* Suppose that the agent's memory $$a$$ encodes a computable belief $$q$$ about the environment (formally, a short fixed program reconstructs $$q$$ from $$a$$). Given $$a$$, one way to describe the true state $$s$$ is to recover $$q$$ and record the Shannon codeword of $$s$$ under $$q$$, which has length approximately $$\log \tfrac{1}{q(s)}$$ bits (Section 2.3). Since the shortest description can be no longer than this particular one,

$$
\begin{gathered}K(s \mid a) \;{\mathrel{\stackrel{+}{<}}}\; \log \frac{1}{q(s)}, \qquad\text{and hence}\\ I(a : s) \;{\mathrel{\stackrel{+}{=}}}\; K(s) - K(s \mid a) \;{\mathrel{\stackrel{+}{>}}}\; K(s) - \log \frac{1}{q(s)}.\end{gathered}
$$

The more probability the belief assigns to the true environment, the shorter this codeword becomes, and the more mutual information the memory carries about the world.

*From mutual information to optimization.* The algorithmic Touchette–Lloyd bound (1) establishes that the agent can remove at most $$I(a:s)$$ bits of complexity from the environment, and that this amount is attainable. Combining the two bridges yields

$$
\text{optimization the agent can perform}\;{\mathrel{\stackrel{+}{>}}}\; K(s) - \log \frac{1}{q(s)},
$$

so the agent can drive the environment down to a residual complexity of approximately $$\log\tfrac{1}{q(s)}$$, which is precisely the environment's entropy as the agent's belief regards it. It follows that *the more probability the agent's model assigns to the truth, the more of the environment it can optimize*, at a rate fixed by the bookkeeping rather than by any modeling choice.

This correspondence constitutes Bayesian learning expressed in physical terms. As the agent collects evidence and updates its belief, $$q(s)$$ rises, the codeword length $$\log\tfrac{1}{q(s)}$$ and the residual $$K(s\mid a)$$ shrink, $$I(a:s)$$ grows, and the optimization within reach grows with it. In the limit of certainty $$K(s\mid a) {\mathrel{\stackrel{+}{=}}} 0$$ and $$I(a:s) {\mathrel{\stackrel{+}{=}}} K(s)$$, and the agent can in principle steer the environment to vanishing residual complexity. Updating a belief toward the truth and accumulating spendable, physically stored knowledge are therefore one and the same process, constituting the single-state form of the Touchette–Lloyd result of Appendix B and the precise content of the Type-3 channel of Section 5.

Two further properties complete the characterization of $$I(a:s)$$ as a resource.

- It is *consumed* when spent: optimization in this setting is the Type-3 channel (Section 5), in which the shared correlation is consumed, so that continued optimization requires the agent either to measure again (Type 2) or to export waste (Type 1).
- It *decays*: correlations between two systems cannot grow without interaction (a consequence of the algorithmic second law, Section 7.3), so that if the environment changes while the agent's records remain fixed, $$I(a:s)$$ falls, and correlation that has been allowed to decay can no longer be spent.

This analysis establishes that an embedded agent's knowledge about the world is the same physical quantity as its capacity to optimize the world beyond blind baselines: an agent that knows more can accomplish more, at a fixed exchange rate of one bit of optimization per bit of correlation. In turn, this identification of knowledge with optimization capacity invites a refinement of each of the three channels, to which we now turn.

\### 8.2 Refinements of the three channels via universal computation

Having introduced algorithmic entropy, we now demonstrate that each of the three channels admits a refinement, and in every case the refinement turns on the compressibility of an individual state—a quantity that the ensemble account cannot express.

**Type 1.**  Before exporting waste into the environment, an agent should determine whether the waste is genuinely as random as it appears. If the waste possesses compressible structure (and the output of any computation does, by Corollary 7.3), the agent can compress it first and export only $$K(\text{waste})$$ bits of genuine entropy rather than its raw size. This compression must occur *before* the waste mixes into the environment, because mixing destroys the structure: once the structure is lost, no compressor can recover it.

**Type 2.**  The memory cost of recording a measured state $$x$$ is not the raw length of the transcript but its complexity $$K(x)$$: records can be stored in compressed form, so a memory can absorb more optimization than its nominal size suggests. Moreover, $$K(x)$$ constitutes a lower bound, in that no method stores $$x$$ in fewer bits.

**Type 3.**  The steering budget is the mutual information (1), and computation offers a second route to acquiring it: if the environment's state is simple ($$K(s)$$ small), a short program generates it, so the agent can come to know it (acquiring $$I(a:s) \approx K(s)$$) by *computation alone*, with almost no measurement. Simple worlds are therefore informationally inexpensive to characterize and consequently inexpensive to optimize.

These three refinements converge in a single fact, noted by Daniel C and Ebtekar: the complexity $$K(s)$$ of the optimized subsystem is simultaneously the smallest memory that can absorb it (Type 2) and the smallest knowledge that can steer it (Type 3). The cost of recording a state and the knowledge required to steer it are the same number of bits, because both quantities equal the length of its shortest description.

\### 8.3 Dissolution of the apparent subjectivity

We now return to the puzzle of Section 6.4: does the demon's capacity to perform work change when *our* beliefs about its memory change? The answer comprises two parts, of which the second provides the resolution.

First, the demon's capacity is objective: its remaining capacity to optimize is its free memory, namely the size of the memory minus the *description complexity* of its current contents. If those contents are compressible, the demon can compress them (a reversible and costless operation by Corollary 7.3) and thereby recover the space; if they are incompressible, the space is irreducibly occupied, because freeing it would require destroying information, which reversibility forbids. In either case the capacity depends only on the physical state of the memory, and no observer's beliefs enter the formula.

Second, the appearance of belief-dependence nevertheless reflected a genuine physical relation. When we update our beliefs about the demon's memory, that update constitutes a physical change in our own brains, which thereafter share more algorithmic mutual information with the demon's memory. This shared information is itself a Type-3 resource: in principle we could spend it to assist in compressing the demon's memory, freeing capacity that the demon alone could not reach. The demon's situation therefore genuinely differs after our update, but only relative to the enlarged system that now includes our correlated brains, and the difference is exactly the correlation we have gained. What the old formalism recorded as a mysterious observer-dependence of entropy, the new formalism records as an ordinary physical relation between observer and observed, dissolving the apparent subjectivity into objective correlation.

\### 8.4 Thermodynamic implications for optimizing systems

Finally, we reconsider the optimizing systems of Section 3 in the light of these results. An optimizer drives the system upon which it acts from a broad range of configurations into a narrow target set, and the question arises of what the existence of such an optimizer implies thermodynamically.

The funneling constitutes coarse-grained entropy reduction in a subsystem, so the global accounting must remain consistent through some mixture of the three channels (Section 5): waste exported to the surroundings (Type 1), records kept in memory (Type 2), or pre-existing correlation spent (Type 3). The principal implication is a selection-theorem-like conclusion: if the funneling exceeds the blind baseline of the environment's own dynamics, then by the Touchette–Lloyd theorem (Theorem B.2, Appendix B) and its algorithmic form (1), the system must carry mutual information with what it steers, which is a necessary (though, by Appendix B.8, not sufficient) ingredient of a world model. At least this much modeling is therefore forced by the bookkeeping rather than attributed by an observer. This conclusion constitutes the thermodynamic counterpart of the observer-independence established in Section 3.5: the presence of a world model, like the presence of an optimizer, is an objective fact about the system, certified by the entropy it removes rather than attributed by an external observer.

---
id: '98844ba0-4e30-4979-9b3f-4a0d9123db92'
title: "D.4.2.11 A thermodynamics of biased coins"
tldr: "Appendix A: a toy world of biased coins where work extraction is compression, a single heat bath yields nothing, and two baths at different temperatures yield some work."
summary_for_tutor: "Appendix A (A.1-A.6) of Iliad worksheet D.4.2, after Wentworth's generalized heat engine. The designer's viewpoint, the coin model (cold pool p = 0.1, hot pool p = 0.2; reversibility, conservation of heads, design-time ignorance), work coins, impossibility with one pool, about 0.011n work coins from two pools (about 3.7% of the heads), and four lessons (substrate independence, conservation of uncertainty, work as compression, negentropy as fuel). No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## A. A thermodynamics of biased coins: the generalized heat engine

This appendix develops, as a self-contained worked example, the toy thermodynamic world referenced from two points elsewhere in these notes (the blind baseline of Appendix B and the Type-1 channel of Section 5); it may be read at any point after Section 4. The construction follows Wentworth's essay *Generalized Heat Engine*, whose objective is to take the distinctively thermodynamic ideas of statistical mechanics (heat, work, engines, the impossibility of perpetual motion) and reconstruct them systematically in a setting containing no physics whatsoever, thereby isolating precisely which components of thermodynamics are fundamentally facts about information. The model also makes concrete a perspective, the *designer's viewpoint*, that transfers directly to the analysis of agents embedded in environments they cannot fully observe.

\### A.1 The designer's viewpoint

We begin by examining the epistemic situation of a designer who wishes to construct a refrigerator, and in particular the question of why the designer cannot simply build a machine that observes the air molecules and removes the fast ones. All of the microscopic dynamics of the combined refrigerator-and-environment system are reversible, so, as established in Section 4.1, the number of possible microstates compatible with what is known never decreases of its own accord, and the only mechanism for reducing uncertainty about a microstate is observation. The designer, however, operates *in advance*: the behavior of the machine is fixed at design time, with no access to the exact positions the air molecules will occupy when the machine is eventually switched on. From the designer's perspective, therefore, there is uncertainty that cannot be reduced but only *relocated*. The machine itself can "observe" variables while running, but the machine is part of the total system, and its observations constitute further reversible dynamics: any record the machine produces is a physical change within the machine, subject to the same conservation rules as every other component of the system. (We analyze precisely this maneuver, observation implemented as reversible copying, in our treatment of Maxwell's demon in Section 5.)

The design problem is therefore to choose transformations, in advance and without inspection of the system, that make some chosen variables (the interior of the refrigerator) *more* certain at the cost of making others (the heat baths powering the machine) *less* certain. Thermodynamic-style laws apply whenever three conditions hold: the designer cannot gain information about the system (no "peeking" at design time), information cannot be destroyed at the lowest level (reversibility), and some conserved quantity constrains the admissible transformations (energy, in the physical case). Wentworth's toy world possesses exactly these three conditions and nothing else, providing a minimal setting in which the resulting laws can be derived in full.

\### A.2 Specification of the model: coins, transformations, and conservation laws

Having identified the three conditions under which thermodynamic-style laws apply, we now specify Wentworth's toy world in full. The world consists of two large pools of independent biased coins, in which each coin shows $$1$$ (heads) or $$0$$ (tails):

- a *cold pool* $$X^{C}_{1}, \dots, X^{C}_{n}$$, in which each coin is heads with probability $$0.1$$ (entropy $$h(0.1) \approx 0.47$$ bits per coin, by Example 2.2); and
- a *hot pool* $$X^{H}_{1}, \dots, X^{H}_{n}$$, in which each coin is heads with probability $$0.2$$ (entropy $$h(0.2) \approx 0.72$$ bits per coin).

The heads-probability plays the role of temperature (the hot pool is more uncertain per coin), while the *number of heads* plays the role of energy. We may apply any transformation $$T$$ that replaces the coins' values with new values computed from their old values, subject to three rules mirroring the three conditions identified above:

1. **Reversibility.** $$T$$ must be invertible: from the final state of all the coins (together with knowledge of which transformation was applied), the initial state must be reconstructible. This is the analogue of microscopic reversibility.
2. **Conservation.** $$T$$ must conserve the total number of heads, the analogue of energy conservation: heads may be relocated between coins but neither created nor destroyed on net.
3. **Design-Time Ignorance.** The transformation $$T$$ is chosen before any coin is inspected (the "no peeking" condition), exactly as the refrigerator designer commits to a blueprint before the machine encounters its environment.

To demonstrate that interesting transformations exist within these rules, we consider Wentworth's example, in which $$T$$ acts on three coins as follows: *if $$X^{C}_{1}$$ shows tails, swap $$X^{H}_{3}$$ with $$X^{H}_{7}$$; if $$X^{C}_{1}$$ shows heads, change nothing.* This transformation conserves heads (either two coins are swapped, which permutes values without changing their sum, or nothing occurs), and it is reversible (the control coin $$X^{C}_{1}$$ is itself unchanged, so the final state determines whether the swap occurred, and applying the same transformation a second time undoes it). Conditional swaps of this kind, composed in sequence, constitute the fundamental building blocks from which all admissible engines are assembled, and the example already establishes a fundamental point: a transformation can *read* one part of the system and act on another, entirely within deterministic, reversible, conservative rules, demonstrating that machines that "observe while running" lie not outside the formalism but within it.

In summary, the designer selects an invertible, heads-conserving map $$T$$ from coin configurations to coin configurations, the world applies it, and our objective is to characterize precisely what such maps can accomplish.

\### A.3 Work extraction as a compression problem

We define a *work coin* to be a coin whose final value is heads with near-certainty (probability approaching $$1$$ as $$n$$ grows). Work coins are the analogue of stored mechanical work or a charged battery: a resource in a known, definite state, available to power other processes. *Extracting work* means choosing $$T$$ so that some $$w$$ designated coins are rendered work coins by the transformation, thereby converting statistical uncertainty into a resource in a known state.

The first key observation is that reversibility transforms work extraction into a data compression problem. We write $$X$$ for the (random) initial configuration of all the coins and $$X' = T(X)$$ for the final configuration. Because $$T$$ is invertible, the final state determines the initial state: $$X'$$ contains *all* of the information in $$X$$, so $$H(X') \ge H(X)$$ (in fact $$H(X') = H(X)$$, since invertible maps preserve entropy exactly). Suppose now that $$w$$ of the final coins are deterministic. Deterministic coins carry zero entropy, so all $$H(X)$$ bits of initial uncertainty must be carried by the remaining coins; in other words, *extracting $$w$$ work coins requires compressing the information content of the entire initial state into the other coins*. Producing certainty in one location therefore requires concentrating uncertainty elsewhere, reflecting the fundamental fact that under reversible dynamics nothing is ever erased.

\### A.4 The impossibility of work extraction from a single heat bath

We now attempt to extract work from the hot pool alone and demonstrate that the attempt must fail; this failure constitutes the toy-world analogue of the impossibility of a perpetual motion machine of the second kind (a machine that extracts work from a single-temperature heat bath).

The hot pool's $$n$$ coins carry $$H(X) = 0.72n$$ bits of entropy, and a compression scheme can in principle encode these bits into approximately $$0.72n$$ coins, leaving $$0.28n$$ coins deterministic. The conservation law, however, renders this compression infeasible, as the following counting argument demonstrates. Fully compressed data is incompressible, which means that it appears statistically uniform: each compressed coin is heads with probability approximately $$\frac{1}{2}$$ (if the compressed coins were biased, they would admit further compression, contradicting full compression). The $$0.72n$$ compressed coins would therefore contain approximately $$0.36n$$ heads, whereas the initial state contains only $$0.2n$$ heads, and heads are conserved. Even if every one of the intended work coins were set to tails rather than heads, the accounting cannot be made consistent: the required compression demands more heads than the system possesses, and the attempt fails.

This argument admits a generalization extending well beyond the setting of coins, which we now develop in order to characterize the resource underlying all work extraction. The hot pool's distribution (independent coins, each heads with probability $$0.2$$) is the *maximum-entropy* distribution among all distributions with its expected number of heads; in this precise sense a heat bath is "as random as its energy allows". Suppose, in general, that a pool of variables is maxentropic subject to a constraint that fixes the value of some additive quantity $$\sum_{k} f_{k}(X_{k})$$. Deterministically fixing the value of one variable (extracting work from it) shrinks the set of values the constrained sum can take on the remaining variables, and therefore shrinks the maximum entropy the remaining variables can hold. Since the initial state already saturated this maximum, the remaining variables cannot absorb all of the information, and compression must fail. *Work cannot be extracted from a system that is already at maximum entropy given its constraints.* The slack between a system's actual entropy and its constrained maximum, which following standard usage we call *negentropy*, is therefore the sole resource from which work can be drawn.

\### A.5 Work extraction from two heat baths at different temperatures

We now employ both pools: $$2n$$ coins, with total entropy $$\approx 0.47n + 0.72n = 1.19n$$ bits and total heads $$\approx (0.1 + 0.2)n = 0.3n$$. The crucial difference from the single-pool case is that the *joint* initial distribution is not maxentropic given the joint constraint: the maximum-entropy distribution with $$0.3n$$ heads spread over $$2n$$ coins would make every coin heads with probability $$0.15$$, whereas the actual state maintains two distinct biases, $$0.1$$ and $$0.2$$. The gap between actual entropy and constrained maximum entropy is negentropy, and it constitutes a resource that the designer can expend.

We now quantify the amount of work that this negentropy affords, deriving the maximal number of work coins extractable from the two pools. Suppose that we designate $$w$$ coins as intended work coins (deterministic heads). The remaining $$2n - w$$ coins must carry all $$1.19n$$ bits of initial entropy while containing the remaining $$0.3n - w$$ heads. To carry as much information as possible, the final distribution of those $$2n-w$$ coins should itself be maxentropic subject to its heads constraint, which (for large $$n$$) means independent coins, each heads with probability

$$
q \;=\; \frac{0.3n - w}{2n - w},
$$

giving total entropy $$(2n - w)\, h(q)$$ where $$h$$ is the binary entropy function of Example 2.2. The largest feasible $$w$$ makes this capacity exactly equal to the required $$1.19n$$ bits:

$$
(2n - w)\; h\!\left(\frac{0.3n - w}{2n - w}\right) \;=\; 1.19n .
$$

Solving numerically gives $$w \approx 0.011n$$. A heads-conserving, reversible, designed-in-advance transformation therefore *can* extract work from two heat baths at different temperatures, converting approximately 3.7% of the total heads (5.5% of the hot pool's heads) into work coins. This construction is the toy world's heat engine, and its derivation required nothing beyond information-theoretic reasoning, confirming the claim that the distinctive behavior of heat engines is fundamentally a fact about information.

Wentworth notes one caveat regarding comparison of this figure with the physics literature: the efficiency computed here is not the classical Carnot efficiency, because the classical result answers a slightly different question (the optimal conversion rate *at the margin*, for engines drawing from effectively inexhaustible baths, generally consuming unequal amounts from the hot and cold sides), whereas we have asked how much total work can be extracted from two fixed, finite pools. The conceptual content—that work arises only from temperature *differences* and never from a single bath—is identical.

\### A.6 Lessons from the toy world

Four lessons from this construction recur throughout the remainder of these notes, and we therefore state them explicitly.

**Substrate Independence of Thermodynamic Law.** Thermodynamic laws are not specifically about molecules and joules; they apply whenever an agent or designer cannot gain information about a system at will, cannot destroy information at the lowest level, and operates under some conservation constraint. This is the reason the same laws reappear when we analyze agents, memories, and computations.

**Conservation of Uncertainty under Reversibility.** Under reversibility, uncertainty is never destroyed but only relocated, so that every machine that makes one variable more predictable necessarily makes others less predictable.

**Work Extraction as Compression.** Extracting work (producing variables in definite, known states) is a compression problem, and conversely, compression capacity is work capacity. This identity between "useful energy" and "compressibility" is the seed of the algorithmic viewpoint of Section 7, where it is sharpened from a statement about distributions into a statement about individual states.

**Negentropy as the Sole Fuel.** The fuel of all such machines is negentropy: the gap between a system's entropy and the maximum entropy compatible with its constraints. A system at its constrained maximum entropy (a single heat bath) is useless as fuel, regardless of how much "energy" it contains.

Everything in this section was achieved *blind*: the transformation was chosen before any coin was inspected, and all of the extracted work derived from statistical structure (the bias difference between the pools) that was known at design time. This raises the natural question of what an agent could additionally accomplish if it were permitted to *observe* the system before acting, a question that admits a precise answer and that we take up in Appendix B.

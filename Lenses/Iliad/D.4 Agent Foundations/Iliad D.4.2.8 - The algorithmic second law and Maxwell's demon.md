---
id: '33777670-02bb-433b-bd27-92e6a095357c'
title: "D.4.2.8 The algorithmic second law and Maxwell's demon"
tldr: "The algorithmic second law with its fluctuation allowance, and an exact analysis of Maxwell's demon giving an algorithmic Touchette-Lloyd bound."
summary_for_tutor: "Sections 7.3 and 7.4 of Iliad worksheet D.4.2. Theorem 7.2 (algorithmic second law: K(X_s) - K(X_t) <+ K(t - s) + log 1/δ), Corollary 7.3 (K(f(x)) =+ K(x) for simple bijections), the demon with complete measurement and erasure, and partial measurement giving K(x) - K(y) <+ I(m(x) : x), plus the objective versus subjective entropy of the demon. Keep the notation <+ and =+. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 7.3 The algorithmic second law

We now return to the physical setting of Section 4: a coarse-grained state space with equal-volume cells, evolving as a Markov chain with doubly stochastic, *computable* transition probabilities (the assumption that the laws of physics admit a short program constitutes a complexity-theoretic version of the Church–Turing thesis, and we choose our reference computer so that the dynamics are simply describable). In this setting the algorithmic entropy of the system in state $$x$$ is simply $$K(x)$$, and it obeys a second law descending from Levin's law of *randomness conservation*.

:::callout {title="Theorem" tone="green"}

**Theorem 7.2 (Algorithmic Second Law; Levin, Ebtekar–Hutter, Stated Informally).** Let $$(X_{t})$$ be a computable, doubly stochastic Markov chain modeling an isolated system's coarse-grained evolution, and let $$s < t$$ be two times. Then for every $$\delta > 0$$, with probability greater than $$1 - \delta$$,

$$
K(X_{s}) - K(X_{t}) \;{\mathrel{\stackrel{+}{<}}}\; K(t - s) \;+\; \log \tfrac{1}{\delta}.
$$

:::

The theorem asserts that *the description complexity of an isolated system's state almost never decreases, except by a precisely priced fluctuation allowance*. It improves upon the ensemble second law (Theorem 4.1) in two respects that are central to our purposes: it holds for each individual trajectory with high probability, rather than merely for the average of an ensemble, and it requires no initial distribution $$\mu$$ whatsoever, removing the exogenous ensemble exactly as Section 6 required.

Each of the two terms in the allowance admits a precise interpretation, and each is quantitatively negligible in physical terms.

The term $$\log\frac{1}{\delta}$$ prices *chance* fluctuations: rare trajectories along which entropy temporarily falls. Its scale is set by the rarity of the fluctuations one chooses to consider. If events of probability $$\delta = 2^{-1000}$$ are tolerated, the permitted decrease in entropy is approximately one thousand bits, which in physical units (we recall that $$1$$ bit $$\approx 10^{-23}\,\mathrm{J/K}$$) is around $$10^{-20}\,\mathrm{J/K}$$, twenty orders of magnitude below anything measurable. The statistical character of the second law is therefore genuine but quantitatively trivial at macroscopic scales.

The term $$K(t-s)$$, the complexity of the *elapsed time*, prices *deterministic recurrences*, and its necessity is subtle. The Poincare recurrence theorem guarantees that an isolated finite system eventually returns arbitrarily close to its initial low-entropy state, so entropy cannot literally always increase. The theorem survives because recurrence times are astronomically long and arithmetically structureless: a system whose recurrence occurs at step $$t - s = 17{,}382{,}\dots$$ (a number comprising some $$10^{20}$$ digits) revisits low entropy only at moments whose timestamps are themselves about as complex as the state, and the $$K(t-s)$$ allowance covers exactly this cost. For any time interval that can be *simply specified* ($$10^{9}$$ years, $$2^{100}$$ Planck times), $$K(t-s)$$ is at most a few hundred bits, so that entropy, regarded as a function of simply specified times, increases monotonically up to negligible slack.

One special case recurs throughout the demon analysis below, and we record it separately.

:::callout {title="Theorem" tone="green"}

**Corollary 7.3 (Invariance of Entropy under Deterministic Dynamics).** If the evolution over the interval is a computable bijection $$f$$ with a short description (for instance, a few steps of simply describable reversible dynamics), then

$$
K(f(x)) \;{\mathrel{\stackrel{+}{=}}}\; K(x).
$$

:::

The reason is immediate from the compression picture: given the dynamics, a description of $$x$$ is a description of $$f(x)$$ and vice versa, so the two complexities differ by at most the (small) complexity of $$f$$ itself. The corollary carries an important consequence: *substantial entropy production requires randomness*. A deterministic, simply describable evolution can shuffle states but cannot increase their complexity by more than a constant; in classical physics, the randomness that drives entropy production is supplied by the coarse-graining of chaotic microdynamics (Section 4.3), which continually injects effectively fresh random bits into the coarse description. A useful picture is the following: a doubly stochastic evolution is equivalent to drawing a random bijection at each step (for instance, by tossing coins), and entropy can increase by at most the number of coins tossed, and only to the extent that the coins are independent of the state. The Shannon-level second law is blind to this distinction between deterministic reshuffling and genuine randomization, whereas the algorithmic version registers it precisely.

\### 7.4 An exact analysis of Maxwell's demon

Having established the algorithmic second law and its deterministic special case, we now revisit the demon, this time in the form of a theorem rather than of an informal narrative, and recover the Touchette–Lloyd bound as a statement about individual physical states. We take the demon's memory and the gas to be jointly coarse-grained, writing joint states as pairs (memory contents, gas state). The demon's memory begins in a blank reference state $$0$$, and the gas begins in some state $$x$$.

**Complete Measurement Followed by Erasure.**  In the idealized case, the demon performs a complete measurement, reversibly copying the gas's state into memory:

$$
(0, x) \;\mapsto\; (x, x),
$$

and then, using its copy as the control of a conditional operation (a string of controlled-NOTs, Example 5.1), reversibly resets the gas to a reference state:

$$
(x, x) \;\mapsto\; (x, 0).
$$

Each map is injective on the states that can actually occur (the first on pairs with blank memory, the second on pairs whose two slots agree), hence extendable to a bijection of the joint state space, and each is simply describable. Corollary 7.3 therefore applies to both steps, and the *total* complexity remains unchanged throughout:

$$
K(0, x) \;{\mathrel{\stackrel{+}{=}}}\; K(x, x) \;{\mathrel{\stackrel{+}{=}}}\; K(x, 0) \;{\mathrel{\stackrel{+}{=}}}\; K(x).
$$

We now examine what this chain of equalities asserts. The gas has passed from complexity $$K(x)$$ to complexity $${\mathrel{\stackrel{+}{=}}} 0$$, which constitutes a complete Type-2 optimization. The joint complexity never changed, so the second law was never threatened at any step, without any need to "complete a cycle" or to invoke ad hoc accounting. The balance is now carried entirely by the demon's memory, which holds a record of complexity $$K(x)$$; the gas's erasure was permitted *precisely because a copy existed*, since the operation "clear slot two given that slot one holds a copy" is injective. The step that the second law forbids is the clearing of the *last* copy:

$$
(x, 0) \;\mapsto\; (0, 0)
$$

is either not injective (if it is to work for every $$x$$) or not simply describable (if hard-wired for one particular complex $$x$$, the wiring itself would have complexity $$K(x)$$, and Corollary 7.3 charges for the complexity of the dynamics). To recover its memory, the demon must clear that last copy, irreversibly destroying $$K(x)$$ bits of complexity; it cannot do so without cost, and the only route consistent with the second law is to export those $$K(x)$$ bits into the environment as Type-1 waste (Section 5.2). The classic resolution of the demon paradox—that the demon's own information processing is what rescues the second law—emerges here not as an additional postulate but as a direct consequence of the complexity bookkeeping.

**Partial Measurement and the Algorithmic Touchette–Lloyd Bound.**  A realistic demon measures only a small part of the gas state. Let the measurement be $$m(x)$$, where $$m$$ is any simply describable (possibly random, possibly many-to-one) function of the gas state—a few bits concerning a single approaching molecule, for instance. The demon records the measurement, then employs the record as a control to drive the gas from $$x$$ to some new state $$y$$:

$$
(0, x) \;\mapsto\; (m(x), x) \;\mapsto\; (m(x), y).
$$

Whatever feedback protocol the second step implements, provided that it is a simply describable mixture of reversible operations, the algorithmic second law applied to the *joint* system gives

$$
K\big(m(x), x\big) \;{\mathrel{\stackrel{+}{<}}}\; K\big(m(x), y\big).
$$

Expanding both sides with the chain rule ($$K(m,\cdot) {\mathrel{\stackrel{+}{=}}} K(m) + K(\cdot \mid m)$$, with the technical refinements recorded in Definition 7.1), subtracting $$K(m(x))$$ from both sides, and rewriting conditional complexities via mutual information ($$K(x \mid m) {\mathrel{\stackrel{+}{=}}} K(x) - I(m : x)$$), we obtain

$$
K(x) - I\big(m(x) : x\big) \;{\mathrel{\stackrel{+}{<}}}\; K(y) - I\big(m(x) : y\big) \;\le\; K(y),
$$

where the final step uses the nonnegativity of algorithmic mutual information. Rearranging yields

$$
\boxed{\;K(x) - K(y) \;{\mathrel{\stackrel{+}{<}}}\; I\big(m(x) : x\big).\;}
$$

That is, *the gas can lose at most as much entropy as was measured from it*. The budget is, moreover, exactly achievable: if the demon expends its correlation completely and reversibly (so that $$K(m(x), x) {\mathrel{\stackrel{+}{=}}} K(m(x), y)$$, with no entropy produced, and $$I(m(x) : y) {\mathrel{\stackrel{+}{=}}} 0$$, with no correlation left unspent), then the displayed inequalities collapse to

$$
K(x) - K(y) \;{\mathrel{\stackrel{+}{=}}}\; I\big(m(x) : x\big).
$$

We now place (1) beside Theorem B.2 (Appendix B) and compare the two statements term by term. In each, the left-hand side is the entropy reduction of the steered system, and the right-hand side is the mutual information between the controller's record (action, measurement) and the system's state. The Touchette–Lloyd theorem is the ensemble (Shannon) version of the constraint, speaking of distributions, averages, and a blind baseline supplied by the dynamics. Inequality (1) is the single-shot, individual-state (algorithmic) version, speaking of the single gas state actually confronting the demon, without reference to any ensemble, the role of the blind baseline being played by the additive constant, which absorbs what the simply describable dynamics can accomplish unaided. It is simultaneously the rigorous form of Type-3 optimization from Section 5: the copy step purchases $$I(m(x):x)$$ and the control step expends it, bit for bit.

One final reading of the demon's situation will prove central to the concluding section. After the measurement, two distinct entropies attach to the same gas: its *objective* entropy $$K(x)$$, and its entropy *from the demon's perspective*, the conditional complexity

$$
K\big(x \mid m(x)\big) \;{\mathrel{\stackrel{+}{=}}}\; K(x) - I\big(m(x) : x\big),
$$

which is smaller by exactly the measured information. The demon's optimization power over the gas is precisely the wedge between the objective and the subjective entropy. The subjective element has therefore not been eliminated from thermodynamics but rather assigned a physical location: the "subjective distribution" of the older formalism has become a physical conditioning on a physical record, carried in a memory that occupies physical space and obeys the second law.

---
id: 'e89591f8-b59f-42b5-b188-a39761fa3f9f'
title: "D.4.2.7 Kolmogorov complexity as an entropy measure"
tldr: "Kolmogorov complexity as the entropy of an individual state, and the three results that justify it: independence of the computer, agreement with Shannon entropy, and uncomputability."
summary_for_tutor: "Sections 7 (intro), 7.1 and 7.2 of Iliad worksheet D.4.2. Definition 7.1 of K(x), K(x | y), algorithmic mutual information I(x : y) = K(x) + K(y) - K(x, y), the additive-constant notation, and the justification of K as entropy: invariance under the universal computer, K(x | μ) vs Ĥ(x, μ) and H(μ) as mean complexity, and why uncomputability is needed for a second law. Footnote 2 on self-delimiting programs is included. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 7. Algorithmic thermodynamics

Algorithmic thermodynamics, developed by Ebtekar and Hutter on foundations laid by Bennett, Zurek, Gacs, and Levin, retains the entire coarse-grained Markov framework of Section 4 while introducing a single fundamental modification: the subjective ensemble $$\mu$$ is replaced by universal computation. Rather than asking how surprising a state $$x$$ is under $$\mu$$, the algorithmic framework asks how difficult $$x$$ is to describe in absolute terms. The conceptual gain is an objective, observer-free entropy that *dissolves the subjectivity problem* of Section 6, being defined for a single physical state without reference to any ensemble. In developing this framework we obtain a second law and fluctuation bounds that hold for individual trajectories, culminating in an exact analysis of Maxwell's demon.

\### 7.1 Kolmogorov complexity

We begin by fixing a universal computer $$U$$, which may concretely be regarded as an interpreter for a general-purpose programming language. Every coarse-grained state $$x$$ of a physical system is identified, via the coarse-graining's encoding, with a finite binary string, so that the notion of a program that outputs $$x$$ is well defined.

:::callout {title="Definition" tone="blue"}

**Definition 7.1 (Description Complexity).** The *Kolmogorov complexity* (or description complexity) $$K(x)$$ of a string $$x$$ is the length, in bits, of the shortest program that outputs $$x$$ when run on $$U$$. The *conditional complexity* $$K(x \mid y)$$ is the length of the shortest program that outputs $$x$$ when given $$y$$ as auxiliary input. The *algorithmic mutual information* between two strings is

$$
I(x : y) \;:=\; K(x) + K(y) - K(x, y),
$$

the number of bits that a description of one saves in describing the other.[^2]

:::

The appropriate interpretation of $$K(x)$$ is *optimal lossless compression*: the size of the smallest self-contained representation from which $$x$$ can be regenerated exactly. Several examples serve to calibrate the scale of this quantity. A string of one million zeros has negligible complexity, since a fifteen-byte program suffices to print it. The first million digits of $$\pi$$ likewise have negligible complexity, despite passing every statistical test for randomness, because a short program computes them. A string of one million bits obtained directly from a quantum random-number generator has complexity close to one million bits: almost surely there is no structure to exploit, and the shortest "program" is essentially the string quoted verbatim. A state of $$10^{23}$$ particles confined to one corner of a box has low complexity, since a short loop prints the repeated coordinates, whereas a generic thermalized state has complexity near the full length of its encoding. These examples support a crisp characterization of the algorithmic notion: low entropy corresponds precisely to compressibility, a property of the individual state $$x$$ that makes no reference to any ensemble.

Algorithmic mutual information behaves analogously to the mutual information of Section 2, but for individual objects: $$I(x : x) {\mathrel{\stackrel{+}{=}}} K(x)$$, since a copy of $$x$$ renders any further description redundant; $$I(x : y) {\mathrel{\stackrel{+}{=}}} 0$$ for typical independent random strings, for which a description of one offers no assistance in describing the other; and intermediate values quantify partial correlation, such as that between a measurement record and the system it measured.

Because the shortest program may be arbitrarily difficult to find, statements about $$K$$ hold up to additive constants reflecting fixed wrapper code; following Ebtekar and Hutter, we write $$f {\mathrel{\stackrel{+}{<}}} g$$ for $$f \le g + c$$, $$f {\mathrel{\stackrel{+}{>}}} g$$ for $$f \ge g - c$$, and $$f {\mathrel{\stackrel{+}{=}}} g$$ for both, where $$c$$ depends only on fixed choices such as the universal computer, never on the strings involved.

\### 7.2 Justification of $$K$$ as an entropy measure

We now present three families of results that together justify treating $$K(x)$$ as *the* entropy of the individual state $$x$$.

**Physical Negligibility of the Choice of Computer.**  The quantity $$K$$ depends on the universal computer $$U$$, a dependence that may appear problematic for a proposed physical quantity. The dependence is, however, bounded by translation: for any two universal computers, a fixed interpreter converts programs for one into programs for the other, so the two versions of $$K$$ differ by at most the interpreter's length, uniformly in $$x$$. To gauge the scale of this dependence, we convert to physical units: entropy in bits converts to thermodynamic entropy at $$1 \text{ bit}= {k_{\mathrm{B}}} \ln 2 \approx 9.57 \times 10^{-24}$$ joules per kelvin. Suppose that two programming languages were so dissimilar that translation between them required a 12-gigabyte interpreter, far larger than any real interpreter. Twelve gigabytes is about $$10^{11}$$ bits, so the two languages would assign every physical system entropies agreeing to within $$10^{-12}\,\mathrm{J/K}$$, far below experimental resolution for macroscopic systems. For all physical purposes, therefore, $$K$$ may be regarded as computer-independent.

**Agreement with the Shannon Framework in Its Domain of Validity.**  Let $$\mu$$ be any computable probability distribution. Then for *every* state $$x$$,

$$
K(x \mid \mu) \;{\mathrel{\stackrel{+}{<}}}\; \log \frac{1}{\mu(x)}\;=\; \hat H(x, \mu),
$$

because one way to describe $$x$$, given access to $$\mu$$, is to transmit its Shannon codeword (Section 2.3), and the shortest description can only be shorter. In the reverse direction, a counting argument based on the Kraft inequality shows that the inequality is nearly tight for nearly all samples: for any $$\delta > 0$$, with probability at least $$1 - \delta$$ over $$X \sim \mu$$,

$$
K(X \mid \mu) \;{\mathrel{\stackrel{+}{>}}}\; \log\frac{1}{\mu(X)}- \log \frac{1}{\delta}.
$$

In other words, the optimal universal description of a typical sample is its Shannon codeword up to logarithmically small slack; atypical samples may improve upon the Shannon codeword, but only a $$\delta$$-fraction can do so by more than $$\log\frac{1}{\delta}$$ bits. Averaging the two displays recovers Zurek's identity

$$
H(\mu) \;{\mathrel{\stackrel{+}{=}}}\; \left\langle \,K(X \mid \mu)\, \right\rangle_{X \sim \mu}:
$$

*the Gibbs–Shannon entropy is the mean Kolmogorov complexity of a sample, given prior knowledge of the distribution*. Two specializations sharpen this correspondence: taking $$\mu$$ uniform on a finite set $$B$$ shows that for any simply describable set $$B$$ containing $$x$$, we have $$K(x) {\mathrel{\stackrel{+}{<}}} K(B) + \log |B|$$, with near-equality for the vast majority of elements; taking $$B$$ to be a Boltzmann macrostate (the set of all microstates sharing given macrovariable values) recovers the Boltzmann entropy $$\log|B|$$ as an upper bound on $$K$$, achieved by typical members. Furthermore, the bound applies to *any* simple set rather than to classical macrostates alone: Ebtekar and Hutter's example is that the entropy of a bookshelf can be estimated by taking $$B$$ to be the set of configurations compatible with the manner in which the books are sorted. The algorithmic entropy thus automatically considers every simple description of the state, classical macrovariables included, and charges the state for the least expensive among them.

These results resolve the three failure modes of Section 6.3. Where the ensemble picture is valid (a simple $$\mu$$, concentration, and a typical $$x$$), we have $$K(x) \approx \hat H(x,\mu) \approx H(\mu)$$, so that algorithmic entropy reproduces the classical answers and nothing is lost. Where the ensemble picture fails, $$K$$ continues to function correctly. A point mass $$\mu$$ on an intricate state no longer yields zero entropy, because $$K(x)$$ is large regardless of which distribution is mentioned alongside it, closing the "free knowledge" loophole (the knowledge is now assigned an explicit price, measured in description length). The robot's battery receives a definite per-state answer, $$K(\text{charged state})$$ or $$K(\text{drained state})$$, with the ensemble value revealed by Zurek's identity as a mere average of the two. Finally, a secretly patterned gas configuration is credited for its structure, $$K(x) \ll \hat H(x,\mu)$$, so that the sophisticated compression machine extracts exactly the work that the actual description length of $$x$$ permits, in full accordance with the second law.

**The Uncomputability of $$K$$ and Its Necessity for a Second Law.**  A fundamental property of $$K$$ is that no algorithm can compute $$K(x)$$ from $$x$$, a fact whose consequences for the second law we now examine. One direction of approximation remains available: by running ever more candidate programs for ever longer, one obtains a decreasing sequence of upper bounds converging to $$K(x)$$ (in the standard terminology, $$K$$ is upper semicomputable), which is why real-world compressors provide genuine upper bounds on entropy. No algorithm, however, can certify large *lower* bounds on complexity: there is no procedure that, given $$x$$, verifiably reports "$$K(x)$$ is at least one million". This is Chaitin's incompleteness theorem, and its proof is a short self-referential argument: if such a certifier existed, then a short program could enumerate strings until it located one certified to have complexity at least a million and print it, thereby describing a string of supposed complexity at least one million bits with a few hundred bits—a contradiction.

At first sight, uncomputability appears to be a defect in a proposed physical quantity; it is in fact essential to the consistency of the framework. Suppose that thermodynamics were instead formulated with some entropy-like state function $$K'$$ for which an algorithm *could* certify large values. A short program $$p$$ could then search for and output a state $$x^{*}$$ certified to satisfy $$K'(x^{*}) \gg 0$$. However, any short program that can *construct* $$x^{*}$$ can also *erase* it: one runs $$p$$ to produce a second copy of $$x^{*}$$ alongside the existing one, uses the copy to reversibly cancel the original (a controlled-NOT for every bit, exactly as in Example 5.1), and then runs $$p$$ in reverse to restore the auxiliary state. The net effect of a constant-size machine is to take the world from a state containing $$x^{*}$$, with $$K'$$-entropy $$\gg 0$$, to a state not containing it, with $$K'$$-entropy $$\approx 0$$. A small, simple, reversible machine that can destroy unbounded amounts of "entropy" at will constitutes a perpetual motion machine with respect to $$K'$$, and consequently no second law can hold for any computable notion of entropy. The uncomputability of $$K$$ is precisely what closes this loophole: it guarantees that no simple machine can systematically recognize which states are simple but disguised, and therefore that none can systematically remove the disguise. We note the parallel with Appendix B.8: knowledge that cannot be obtained by any procedure cannot subsequently be expended as a thermodynamic resource. In turn, this justification of $$K$$ as an objective entropy serves as the foundation for the algorithmic second law, to which we now turn.

[^2]: We record two technical refinements once and thereafter suppress them. First, programs are required to be *self-delimiting*: no valid program is a prefix of another, so that each program announces its own end. This convention makes program lengths behave like codeword lengths; in particular they satisfy the Kraft inequality $$\sum_{x} 2^{-K(x)}\le 1$$, which is precisely the property permitting $$2^{-K(x)}$$ to serve as a (sub)probability distribution. Second, the chain rule for $$K$$ holds in the form $$K(x,y) {\mathrel{\stackrel{+}{=}}} K(y) + K(x \mid y, K(y))$$, with the complexity of $$y$$ itself appearing in the conditioning; consequently some identities below, including the second expression for $$I(x:y)$$, implicitly carry such terms. Every statement we make is correct with these refinements installed, and none of these refinements is significant at physical scales.

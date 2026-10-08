---
id: '66e11b46-b94a-4f39-9a8c-cd0167e4a75a'
title: "C.4.4 The correspondence theorem"
tldr: "State and prove the correspondence theorem: two latent models of the same observations have corresponding families of latents, exactly for perfect condensations and with error terms otherwise."
summary_for_tutor: "This is Section 2.3 (The correspondence theorem) of Iliad worksheet C.4 Condensation. It contains Theorem 2.6 (Correspondence, with an entropy bound and error terms), Corollary 2.7 (Exact correspondence), a proof roadmap, Lemma 2.8 (Two witnesses) and Exercises 2.5-2.9 (prove the two-witness lemma, the dependence term is needed, transfer through an observable, intersect the address families, complete the correspondence proof), each with a collapsed solution. Keep the notation H(Y_{superset A} | Z_{superset A}), the coupling of (X,Y,Z) and the defects. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.3 The correspondence theorem

Take two latent models of the same observable tuple $$X$$. To compare them, put $$(X,Y,Z)$$ on one probability space while retaining both specified laws $$(X,Y)$$ and $$(X,Z)$$. For finite variables this is always possible: for example, use $$p(x,y,z)=p(x)p(y\mid x)p(z\mid x)$$. The theorem holds for any such coupling.

:::callout {title="Theorem" tone="green"}

**Theorem 2.6 (Correspondence).** For two latent models $$Y,Z$$ of $$X$$ and any nonempty $$A\subseteq I$$, let $$k=|A|$$. Then

$$
H(Y_{{\mathord{\supseteq}} A}\mid Z_{{\mathord{\supseteq}} A}) \le \sum_{i\in A}H(Y_{{\mathord{\supseteq}} A}\mid X_{i})+(k-1)\eta_{Z}.
$$

If each term in the sum is at most $$\delta$$ and $$\eta_{Z}\le\eta$$, the bound is $$k\delta+(k-1)\eta$$. If both budgets are $$\varepsilon$$, it is $$(2k-1)\varepsilon$$. Interchanging $$Y,Z$$ gives the reverse bound.

:::

:::callout {title="Theorem" tone="green"}

**Corollary 2.7 (Exact correspondence).** If $$Y$$ and $$Z$$ are perfect condensations, their towers above every nonempty address $$A$$ determine one another almost surely:

$$
H(Y_{{\mathord{\supseteq}} A}\mid Z_{{\mathord{\supseteq}} A})=H(Z_{{\mathord{\supseteq}} A}\mid Y_{{\mathord{\supseteq}} A})=0.
$$

:::

The forward bound uses reconstruction in $$Y$$, LVM in $$Z$$, and the Markov defect of $$Z$$. It does not use the Markov condition of $$Y$$ until we reverse the argument. The result concerns corresponding families. Exercise 2.4 shows why we cannot simply replace those families by individual latents.

This proof is a specialization of Eisenstat's approximate correspondence theorem (Eisenstat 2025, Theorem 6.8), using the two-witness inequality (Eisenstat 2025, Lemma 6.4). The exercises below give the full argument without additional machinery.

\#### 2.3.1 Proof roadmap

The theorem has three steps.

1. If two witnesses each determine a target and are independent given their common part, that common part determines the target. Entropy gives a version with errors.
2. Each observation $$X_{i}$$ is determined by its contributing $$Z$$-latents. Anything recoverable from $$X_{i}$$ is therefore recoverable from that family.
3. Intersect these contributing families over $$i\in A$$. Exactly the addresses containing all of $$A$$ survive. Each intersection costs at most one Markov error term.

The word "witness" below means a variable or tuple from which the target is recoverable.

:::callout {title="Theorem" tone="green"}

**Lemma 2.8 (Two witnesses).** For any finite-valued variables $$U,M,P,Q$$,

$$
H(U\mid M)\le H(U\mid M,P)+H(U\mid M,Q)+I(P;Q\mid M).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.5 (★) (Prove the two-witness lemma; 20 minutes).** **(a)** Prove Lemma 2.8 by expanding conditional entropies using the chain rule. Find an expression for the difference between the right and left sides that is a sum of nonnegative quantities.

**(b)** Deduce the exact statement when the three terms on the right are zero.

**(c)** Explain the three error terms. Which measure failures of reconstruction, and which measures dependence that remains after revealing $$M$$?
:::

:::callout {title="Hint" tone="neutral" collapse="closed"}

Try expanding $$I(P;Q\mid M)-I(P;Q\mid U,M)$$, then rearranging with the chain rule, which is stated in Section 1.1. The desired difference contains a conditional mutual information and a conditional entropy.

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

For arbitrary finite $$U,M,P,Q$$, expand the two conditional mutual informations in entropies and regroup the terms in pairs:

$$
\begin{aligned}&I(P;Q\mid M)-I(P;Q\mid U,M)\\&\quad=\bigl[H(P\mid M)-H(P\mid U,M)\bigr]+\bigl[H(Q\mid M)-H(Q\mid U,M)\bigr]\\&\qquad-\bigl[H(P,Q\mid M)-H(P,Q\mid U,M)\bigr]\\&\quad=I(U;P\mid M)+I(U;Q\mid M)-I(U;P,Q\mid M)\\&\quad=H(U\mid M)-H(U\mid P,M)-H(U\mid Q,M)+H(U\mid P,Q,M).\end{aligned}
$$

Rearranging gives

$$
\begin{aligned}&H(U\mid M,P)+H(U\mid M,Q)+I(P;Q\mid M)-H(U\mid M)\\&\hspace{15mm}=I(P;Q\mid U,M)+H(U\mid M,P,Q).\end{aligned}
$$

Its right side is nonnegative, which proves the lemma.

If $$H(U\mid M,P)=H(U\mid M,Q)=I(P;Q\mid M)=0$$, the inequality and nonnegativity imply $$H(U\mid M)=0$$. Thus a target recoverable from each witness is recoverable from their designated common part when the witnesses are conditionally independent given that part.

The first two terms measure what each witness, together with $$M$$, still fails to determine about $$U$$. The third measures dependence between $$P,Q$$ not accounted for by $$M$$. No independence assumption is needed for the inequality itself; exact independence is the case where the third error is zero.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.6 (★) (The dependence term is needed; 5 minutes).** Let $$U=P=Q$$ be a fair bit and let $$M$$ be constant. Evaluate every term in (3). What would go wrong if the mutual-information term were omitted? How does this example resemble the singleton-copy model in Exercise 2.2?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

With $$U=P=Q$$ a fair bit and $$M$$ constant,

$$
H(U\mid M)=1,\quad H(U\mid M,P)=H(U\mid M,Q)=0, \quad I(P;Q\mid M)=1.
$$

The inequality is the equality $$1\le0+0+1$$. Without its mutual-information term it would assert $$1\le0$$. The two witnesses each determine the same bit while the designated common variable is constant, as in the singleton-copy model of Exercise 2.2.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.7 (★) (Transfer through an observable; 10 minutes).** Let $$U$$ be any finite-valued target and suppose $$X_{i}$$ is determined by $$Z_{{\mathord{\supseteq}}\{i\}}$$. Prove

$$
H(U\mid Z_{{\mathord{\supseteq}}\{i\}})\le H(U\mid X_{i}).
$$

State the equality obtained by adding $$X_{i}$$ to the conditioning tuple, then apply the conditioning inequality. Does this argument assume that $$U$$ and $$Z_{{\mathord{\supseteq}}\{i\}}$$ are conditionally independent given $$X_{i}$$?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

If $$X_{i}$$ is a function of $$Z_{{\mathord{\supseteq}}\{i\}}$$ almost surely, adding $$X_{i}$$ to that conditioning tuple changes no information. Hence

$$
H(U\mid Z_{{\mathord{\supseteq}}\{i\}}) =H(U\mid Z_{{\mathord{\supseteq}}\{i\}},X_{i}) \le H(U\mid X_{i}).
$$

The inequality is conditioning monotonicity. It does not assume that $$U$$ and $$Z_{{\mathord{\supseteq}}\{i\}}$$ are conditionally independent given $$X_{i}$$. They can share additional information beyond $$X_{i}$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.8 (★) (Intersect the address families; 15 minutes).** **(a)** For $$I=\{1,2,3\}$$, list $${\mathord{\supseteq}}\{1\}$$, $${\mathord{\supseteq}}\{2\}$$, and $${\mathord{\supseteq}}\{3\}$$. Compute $${\mathord{\supseteq}}\{1\}\cap{\mathord{\supseteq}}\{2\}$$ and then its intersection with $${\mathord{\supseteq}}\{3\}$$.

**(b)** Show that an intersection of upward-closed families is upward closed.

**(c)** For general nonempty $$A\subseteq I$$, prove $$\bigcap_{i\in A}{\mathord{\supseteq}}\{i\}={\mathord{\supseteq}} A$$ by checking membership of an address $$C$$ on both sides.

**(d)** If $$\mathcal{F},\mathcal{G}$$ are upward closed, apply the two-witness lemma with $$M=Z_{\mathcal{F}\cap\mathcal{G}}$$, $$P=Z_{\mathcal{F}}$$, and $$Q=Z_{\mathcal{G}}$$. Why can the extra conditioning on $$M$$ be dropped from each reconstruction term? Write the resulting bound using $$\eta_{Z}$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The first two families are listed in Exercise 2.1, and

$$
{\mathord{\supseteq}}\{3\}=\{\{3\},\{1,3\},\{2,3\},\{1,2,3\}\}.
$$

Thus $${\mathord{\supseteq}}\{1\}\cap{\mathord{\supseteq}}\{2\}=\{\{1,2\},\{1,2,3\}\}$$, and intersecting with $${\mathord{\supseteq}}\{3\}$$ leaves only $$\{1,2,3\}$$.

**(b)** If $$C$$ belongs to every family in an intersection and $$D\supseteq C$$, upward closure places $$D$$ in each such family, hence in the intersection.

**(c)** For an address $$C$$,

$$
C\in\bigcap_{i\in A}{\mathord{\supseteq}}\{i\} \iff (\forall i\in A)\ i\in C \iff A\subseteq C \iff C\in{\mathord{\supseteq}} A.
$$

**(d)** Put $$M=Z_{\mathcal{F}\cap\mathcal{G}}$$, $$P=Z_{\mathcal{F}}$$, $$Q=Z_{\mathcal{G}}$$. The tuple $$M$$ is a subtuple of both $$P$$ and $$Q$$. Thus $$H(U\mid M,P)=H(U\mid P)$$ and similarly for $$Q$$. By the definition of $$\eta_{Z}$$, the lemma gives

$$
H(U\mid Z_{\mathcal{F}\cap\mathcal{G}}) \le H(U\mid Z_{\mathcal{F}})+H(U\mid Z_{\mathcal{G}})+\eta_{Z}.
$$

Upward closure is needed to invoke the bound $$\eta_{Z}$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.9 (★) (Complete the correspondence proof; 25 minutes).** Fix $$A=\{i_{1},\ldots,i_{k}\}$$ and set $$\mathcal{G}_{j}=\bigcap_{\ell=1}^{j}{\mathord{\supseteq}}\{i_{\ell}\}$$. We prove, for $$1\le j\le k$$,

$$
H(Y_{{\mathord{\supseteq}} A}\mid Z_{\mathcal{G}_j})\le \sum_{\ell=1}^{j}H(Y_{{\mathord{\supseteq}} A}\mid X_{i_\ell})+(j-1)\eta_{Z}.
$$

**(a)** Use Exercise 2.7 to prove (4) at $$j=1$$.

**(b)** Use Exercise 2.8 to show, for $$j\ge2$$,

$$
H(Y_{{\mathord{\supseteq}} A}\mid Z_{\mathcal{G}_j})\le H(Y_{{\mathord{\supseteq}} A}\mid Z_{\mathcal{G}_{j-1}})+H(Y_{{\mathord{\supseteq}} A}\mid Z_{{\mathord{\supseteq}}\{i_j\}})+\eta_{Z}.
$$

**(c)** Conclude (4) by induction. Evaluate it at $$j=k$$ to prove Theorem 2.6, and check the case $$k=1$$ explicitly.

**(d)** Deduce Corollary 2.7, including the reverse direction. Name the assumption used at each step of the proof.

**(e)** Suppose instead that $$H(Y_{C}\mid X_{i})\le\varepsilon$$ separately for all relevant addresses $$C$$. Why does this not by itself supply the tower error budget $$H(Y_{{\mathord{\supseteq}} A}\mid X_{i})\le\varepsilon$$?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Fix a nonempty $$A=\{i_{1},\ldots,i_{k}\}$$, put $$\mathcal{G}_{j}=\bigcap_{\ell=1}^{j}{\mathord{\supseteq}}\{i_{\ell}\}$$. Every $${\mathord{\supseteq}}\{i\}$$ is upward closed, as is every $$\mathcal{G}_{j}$$ by Exercise 2.8. We prove (4) for $$1\le j\le k$$.

For $$j=1$$, $$\mathcal{G}_{1}={\mathord{\supseteq}}\{i_{1}\}$$, and Exercise 2.7 gives $$H(Y_{{\mathord{\supseteq}} A}\mid Z_{\mathcal{G}_1})\le H(Y_{{\mathord{\supseteq}} A}\mid X_{i_1})$$. This is the claimed bound with zero intersection terms.

Suppose (4) holds for $$j-1$$, where $$2\le j\le k$$. Apply Exercise 2.8 to the upward-closed families $$\mathcal{G}_{j-1}$$ and $${\mathord{\supseteq}}\{i_{j}\}$$. Their intersection is $$\mathcal{G}_{j}$$, so

$$
\begin{aligned}H(Y_{{\mathord{\supseteq}} A}\mid Z_{\mathcal{G}_j})&\le H(Y_{{\mathord{\supseteq}} A}\mid Z_{\mathcal{G}_{j-1}}) +H(Y_{{\mathord{\supseteq}} A}\mid Z_{{\mathord{\supseteq}}\{i_j\}})+\eta_{Z}\\&\le \sum_{\ell=1}^{j-1}H(Y_{{\mathord{\supseteq}} A}\mid X_{i_\ell})+(j-2)\eta_{Z} +H(Y_{{\mathord{\supseteq}} A}\mid X_{i_j})+\eta_{Z}\\&=\sum_{\ell=1}^{j}H(Y_{{\mathord{\supseteq}} A}\mid X_{i_\ell})+(j-1)\eta_{Z}.\end{aligned}
$$

The second line uses the induction hypothesis and Exercise 2.7. This completes the induction. At $$j=k$$, Exercise 2.8 gives $$\mathcal{G}_{k}={\mathord{\supseteq}} A$$, hence

$$
H(Y_{{\mathord{\supseteq}} A}\mid Z_{{\mathord{\supseteq}} A}) \le\sum_{i\in A}H(Y_{{\mathord{\supseteq}} A}\mid X_{i})+(|A|-1)\eta_{Z}.
$$

For $$|A|=1$$ this is exactly the observable-transfer inequality, so no intersection or Markov error is required. There are $$k$$ reconstruction errors and $$k-1$$ Markov defects. Bounding each reconstruction error by $$\delta$$ and each Markov defect by $$\eta$$ gives $$k\delta+(k-1)\eta$$, or $$(2k-1)\varepsilon$$ for a common budget.

If $$Y,Z$$ are perfect condensations, each reconstruction error is zero: for every $$C\supseteq A$$ and $$i\in A$$, reconstruction says $$Y_{C}$$ is a function of $$X_{i}$$. The finite tuple of such variables is consequently a function of $$X_{i}$$. Also $$\eta_{Z}=0$$. The inequality gives zero conditional entropy in the forward direction. Interchanging $$Y,Z$$, using reconstruction in $$Z$$ and $$\eta_{Y}=0$$, proves the reverse direction. Zero conditional entropy is almost-sure deterministic recoverability in our finite setting.

The proof uses LVM in $$Z$$ for Exercise 2.7, reconstruction in $$Y$$ to bound those errors, and the Markov condition of $$Z$$ at intersections.

Finally, approximate errors for individual latents do not directly give the same error for a tuple. For example, if two independent fair bits $$R,T$$ remain unknown given a constant observation, each conditional entropy is one bit but the tuple's is two bits. Conditional subadditivity gives a sum of the individual budgets, not a single budget. The theorem states its hypothesis in terms of tower errors to avoid this ambiguity.

:::

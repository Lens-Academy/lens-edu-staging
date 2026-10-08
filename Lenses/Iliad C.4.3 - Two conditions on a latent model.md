---
id: '4e78f185-4d1a-4d87-a1d4-290ae36826e3'
title: "C.4.3 Two conditions on a latent model"
tldr: "Define reconstruction and the Markov condition, combine them into perfect condensation, and see why some laws have none and why the conditions are asked only approximately."
summary_for_tutor: "This is Section 2.2 (Two conditions on a latent model) of Iliad worksheet C.4 Condensation. It contains Definition 2.3 (Reconstruction), Definition 2.4 (Markov condition and defect), Definition 2.5 (Perfect condensation), Exercise 2.2 (Two failed models), the subsection Existence is a separate question (a noisy pair X_2 = X_1 xor N has no perfect condensation) with Exercise 2.3 (Full support, optional) and Exercise 2.4 (Families, not individual latents), and the subsection on asking for the conditions only approximately, with the 36-point hierarchical model in Figure 1. Exercises have collapsed solutions. Keep the notation of defects and the LVM, reconstruction and Markov conditions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.2 Two conditions on a latent model

Every observable law has trivial latent models: put a copy of each $$X_{i}$$ in its singleton latent, or the entire tuple $$X$$ in the top latent $$Y_{I}$$, and LVM holds either way. So LVM alone says nothing about how information is shared. Two further conditions do.

:::callout {title="Definition" tone="blue"}

**Definition 2.3 (Reconstruction).** A latent model has exact reconstruction if

$$
H(Y_{A}\mid X_{i})=0\qquad\text{whenever }i\in A.
$$

Equivalently, $$H(Y_{{\mathord{\supseteq}} A}\mid X_{i})=0$$ whenever $$i\in A$$: every latent in that finite tuple can be recovered from $$X_{i}$$.

:::

The equivalence in this definition uses exact zero errors. In approximate statements we will bound the entropy of the *whole tower*; separately small errors for its individual latents could add up.

A family $$\mathcal{F}\subseteq{\mathcal{P}^{+}(I)}$$ is *upward closed* if $$A\in\mathcal{F}$$ and $$A\subseteq C$$ imply $$C\in\mathcal{F}$$. For example, $${\mathord{\supseteq}} A$$ and $$\mathcal{J}_{B}$$ are upward closed. Upward closure makes a family include every more general latent that its members may depend on.

:::callout {title="Definition" tone="blue"}

**Definition 2.4 (Markov condition and defect).** The Markov condition is

$$
I(Y_{\mathcal{F}};Y_{\mathcal{G}}\mid Y_{\mathcal{F}\cap\mathcal{G}})=0
$$

for all upward-closed families $$\mathcal{F},\mathcal{G}\subseteq{\mathcal{P}^{+}(I)}$$. Its quantitative defect is

$$
\eta_{Y}=\max_{\mathcal{F},\mathcal{G}\text{ upward closed}}I(Y_{\mathcal{F}};Y_{\mathcal{G}}\mid Y_{\mathcal{F}\cap\mathcal{G}}).
$$

:::

The condition says that the latents at the shared addresses $$\mathcal{F}\cap\mathcal{G}$$ account for the dependence between the two families. In the two-observable case, its only potentially nonzero requirement is

$$
I(Y_{\{1\}};Y_{\{2\}}\mid Y_{\{1,2\}})=0.
$$

This is a graphical-model condition for the inclusion order. The equivalent local version says that each latent is conditionally independent of all incomparable latents given its strict supersets.

:::callout {title="Definition" tone="blue"}

**Definition 2.5 (Perfect condensation).** A latent model is a perfect condensation if it has exact reconstruction and satisfies the Markov condition.

:::
This is equivalent to Eisenstat's definition by optimal conditioned scores (Eisenstat 2025, Theorem 5.10). Section 2.6 explains that connection. The overlapping-bit model in Example 2.1 is a perfect condensation. All nonconstant latents are mutually independent, so disjoint subfamilies are independent, including after conditioning on the remaining common subfamily. Reconstruction follows from coordinate projections.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.2 (★) (Two failed models; 20 minutes).** Keep the observables of Example 2.1. Consider two alternative models.

**(a)** Set $$Y_{\{i\}}=X_{i}$$ for $$i=1,2,3$$ and every other latent constant. Check LVM and reconstruction. Take $$\mathcal{F}={\mathord{\supseteq}}\{1\}$$ and $$\mathcal{G}={\mathord{\supseteq}}\{2\}$$. Calculate the conditional mutual information in Definition 2.4. Which information is duplicated across singleton latents?

**(b)** Instead set $$Y_{\{1,2,3\}}=(S,P,Q)$$ and every other latent constant. Check LVM and the Markov condition. Compute $$H(Y_{\{1,2,3\}}\mid X_{1})$$. Which condition fails?

**(c)** Explain why LVM, reconstruction, and the Markov condition have different roles.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** In the singleton-copy model $$Y_{\{i\}}=X_{i}$$, the contributing family for $$i$$ includes $$X_{i}$$ itself. Thus LVM holds. Each nonconstant latent has just one contributing observation, from which it is recovered identically, so reconstruction holds too.

For $$\mathcal{F}={\mathord{\supseteq}}\{1\}$$ and $$\mathcal{G}={\mathord{\supseteq}}\{2\}$$, all entries of $$Y_{\mathcal{F}\cap\mathcal{G}}$$ are constant. The only nonconstant entries of the two larger tuples are $$X_{1}$$ and $$X_{2}$$. Consequently

$$
I(Y_{\mathcal{F}};Y_{\mathcal{G}}\mid Y_{\mathcal{F}\cap\mathcal{G}}) =I(X_{1};X_{2})=1.
$$

Both singleton latents determine $$S$$, while their common ancestor latents are constant. This violates the Markov condition. It is enough to exhibit this one pair of upward-closed families; finding the maximum defect is unnecessary.

**(b)** With only $$Y_{\{1,2,3\}}=(S,P,Q)$$ nonconstant, each observation is obtained by projection, so LVM holds. Every nonempty upward-closed family contains the top address. If both families are nonempty, their intersection contains that top latent and determines all latent variables; the conditional mutual information is zero. If either is empty it is zero as well. Thus the Markov condition holds.

But $$X_{1}=(S,P)$$ leaves the independent fair bit $$Q$$ unknown, so

$$
H(Y_{\{1,2,3\}}\mid X_{1})=H(Q\mid S,P)=1.
$$

Reconstruction fails.

**(c)** LVM requires enough latent information to determine each observation. Reconstruction excludes information placed at a shared address that an individual contributing observation cannot recover. The Markov condition excludes dependence between families not accounted for by their common latents. The singleton model satisfies reconstruction but fails the Markov condition; the top-latent model satisfies the Markov condition but fails reconstruction.

:::

\#### 2.2.1 Existence is a separate question

The preceding examples test particular latent models. A stronger question is whether a given observable law admits *any* perfect condensation. Even a pair of correlated binary variables can fail to do so.

Let $$I=\{1,2\}$$, let $$X_{1}$$ be a fair bit, and set $$X_{2}=X_{1}\mathbin{\oplus}N$$, where $$N$$ is independent Bernoulli$$(q)$$ noise and $$0<q<1/2$$. Here $$\oplus$$ is addition modulo two, so $$a\oplus b$$ is $$0$$ when the two bits agree and $$1$$ when they differ. The joint law is

$$
\def\arraystretch{1.8}\begin{array}{r|cc}P(x_1,x_2) & \;\;x_2=0\;\; & \;\;x_2=1\;\;\\\hline x_1=0 & \dfrac{1-q}{2} & \dfrac{q}{2}\\ x_1=1 & \dfrac{q}{2} & \dfrac{1-q}{2}\end{array}
$$

All four outcomes have positive probability, and $$X_{1},X_{2}$$ are dependent because the two rows differ ($$q\ne1/2$$). Suppose a perfect condensation existed, and consider its top latent $$Y_{\{1,2\}}$$.

With two observations there are only three addresses, so the whole model is three latents:

$$
\begin{array}{r|ccc}\text{address} & \{1\} & \{1,2\} & \{2\}\\ \text{latent} & Y_{\{1\}} & Y_{\{1,2\}} & Y_{\{2\}}\end{array}
$$

LVM says $$X_{1}$$ is determined by $$(Y_{\{1\}},Y_{\{1,2\}})$$ and $$X_{2}$$ by $$(Y_{\{2\}},Y_{\{1,2\}})$$. The top latent $$Y_{\{1,2\}}$$ is the only one assigned to both observations, so it is the only place shared information can sit.

Reconstruction would give $$Y_{\{1,2\}}=f(X_{1})=g(X_{2})$$ almost surely. Because all four observable pairs have positive probability, these equalities force

$$
f(0)=g(0)=g(1)=f(1).
$$

Thus $$Y_{\{1,2\}}$$ is constant. The Markov condition would then require $$Y_{\{1\}}$$ and $$Y_{\{2\}}$$ to be independent. LVM makes each $$X_{i}$$ a function of its singleton latent and the constant $$Y_{\{1,2\}}$$. Functions of independent variables are independent, contradicting the chosen observable law. No perfect condensation exists for this pair.

There is a quantitative obstruction if we retain *exact* reconstruction. The same argument makes $$Y_{\{1,2\}}$$ constant. Data processing then gives

$$
\eta_{Y}=I(Y_{\{1\}};Y_{\{2\}}) \ge I(X_{1};X_{2})=1-h_{2}(q)>0,
$$

where $$h_{2}(q)=-q\log q-(1-q)\log(1-q)$$ is the binary entropy function. Dependence between the observables must remain as a Markov defect when their separately recoverable top latent is constant. The bound is attained by the singleton-copy model $$Y_{\{i\}}=X_{i}$$, with constant top.

That bound pins one end of a trade-off: exact reconstruction forces a Markov defect of at least $$1-h_{2}(q)$$, and tolerating some reconstruction error buys part of it back. When no perfect condensation exists, which is the usual situation (Exercise 2.3), the latent models of a given observable law trace out a Pareto frontier between reconstruction defect and Markov defect. The useful question is then whether some point on that frontier has both low *enough* for the correspondence bound of Section 2.3 to say something.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.3 (Full support; optional, 10 minutes).** The argument for the noisy pair used only two facts: every combination of values has positive probability, and the observables are dependent. Generalize it. Suppose every combination of values that $$X_{1},\ldots,X_{n}$$ can individually take has positive probability.

**(a)** Show that in any perfect condensation, every latent at an address with at least two elements is constant.

**(b)** For disjoint nonempty blocks $$B,C$$, apply the Markov condition to $$\mathcal{J}_{B}$$ and $$\mathcal{J}_{C}$$ to show that $$X_{B}$$ and $$X_{C}$$ are independent. Conclude that a perfect condensation exists exactly when the observables are mutually independent.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Let $$A$$ contain $$i\ne j$$. Reconstruction gives $$Y_{A}=f(X_{i})=g(X_{j})$$ almost surely. Every pair of values $$(x_{i},x_{j})$$ has positive probability, so $$f(x_{i})=g(x_{j})$$ for all of them, and $$f$$ and $$g$$ are the same constant.

**(b)** Every address in $$\mathcal{J}_{B}\cap\mathcal{J}_{C}$$ meets both disjoint blocks, so it has at least two elements and its latent is constant. The Markov condition therefore makes $$Y_{\mathcal{J}_B}$$ and $$Y_{\mathcal{J}_C}$$ independent, and by LVM $$X_{B}$$ and $$X_{C}$$ are functions of them. Taking $$B=\{1,\ldots,k-1\}$$ and $$C=\{k\}$$ for $$k=2,\ldots,n$$ factorizes the joint law into its marginals. Conversely, if the observables are mutually independent, the singleton-copy model $$Y_{\{i\}}=X_{i}$$ is a perfect condensation: LVM and reconstruction are immediate, and the Markov condition holds because all its nonconstant latents are mutually independent, as for the overlapping-bit model.

In particular, a perfect condensation of any full-support law with dependent observables is impossible, which is why the approximate theorem is the one that applies to noisy data.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.4 (★) (Families, not individual latents; 15 minutes).** For this exercise let $$I=\{1,2\}$$, take independent fair bits $$C,R,T$$, and set $$X_{1}=(C,R)$$, $$X_{2}=(C,T)$$. Compare

$$
\begin{array}{lll}Y_{\{1,2\}}=C,&Y_{\{1\}}=R,&Y_{\{2\}}=T,\\ Z_{\{1,2\}}=C,&Z_{\{1\}}=(C,R),&Z_{\{2\}}=(C,T).\end{array}
$$

**(a)** Check that both models are perfect condensations.

**(b)** Compute $$H(Z_{\{1\}}\mid Y_{\{1\}})$$.

**(c)** Show that $$Y_{{\mathord{\supseteq}}\{1\}}$$ and $$Z_{{\mathord{\supseteq}}\{1\}}$$ determine one another. Explain why correspondence between these tuples is a different claim from correspondence between the singleton latents.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Here $$C,R,T$$ are independent fair bits. In model $$Y$$ the three latents are $$C,R,T$$; in model $$Z$$ they are $$C,(C,R),(C,T)$$.

**(a)** Both contributing families determine their observations. All latents are recoverable from each observation to which they contribute. For example, $$C$$ is the first coordinate of either $$X_{1}$$ or $$X_{2}$$, and $$Z_{\{1\}}=X_{1}$$. For two observables the only nontrivial Markov requirement is independence of the two singleton latents given the top latent. For $$Y$$ this is $$I(R;T\mid C)=0$$. For $$Z$$ it is

$$
I((C,R);(C,T)\mid C)=I(R;T\mid C)=0.
$$

Both are therefore perfect condensations.

**(b)** $$H(Z_{\{1\}}\mid Y_{\{1\}})=H(C,R\mid R)=H(C)=1$$.

**(c)** The $$Y$$ tower at $$\{1\}$$ consists of $$(R,C)$$, and the $$Z$$ tower consists of $$((C,R),C)$$. Each is a deterministic function of the other. A copy of the higher-address information can appear in a lower latent without changing the tower's total information. Thus the individual latents need not correspond even when the relevant towers do.

:::

\#### 2.2.2 Why we ask for the conditions only approximately

Figure 1 shows a hierarchical model of 36 labelled points, worked through in Section 3. A global shape is assigned to every point, a group center $$G_{g}$$ to the 18 points of its group, and a cluster center $$M_{gc}$$ to the nine points of its cluster.

![One draw from the finite model. The left panel shows the 36 points; the right panel shows which set of observations receives each parameter. The global shape is available to every observation.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-condensation-hierarchical-points-a8f5308d.png)

One draw from the finite model. The left panel shows the 36 points; the right panel shows which set of observations receives each parameter. The global shape $$S$$ is available to every observation.

The cluster center specifies a distribution for its points, not the points themselves, so a point does not determine the center it was drawn from:

$$
H(M_{gc}\mid X_{i})>0.
$$

Every kernel here has full support: no finite set of points pins a parameter. LVM and the Markov condition hold exactly here. The reconstruction condition holds only approximately. So we ask for reconstruction up to a defect: for $$i\in A$$,

$$
H(Y_{{\mathord{\supseteq}} A}\mid X_{i})\le\delta,
$$

and prove a correspondence whose error grows with $$\delta$$ and $$\eta$$.

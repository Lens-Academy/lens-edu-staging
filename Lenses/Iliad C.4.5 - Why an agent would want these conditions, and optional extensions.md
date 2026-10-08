---
id: '7f64613f-c106-490e-84c8-f525525fe64b'
title: "C.4.5 Why an agent would want these conditions, and optional extensions"
tldr: "Why a single agent would want reconstruction and the Markov condition, via the conditioned score and local inference, plus two optional extensions."
summary_for_tutor: "This is Sections 2.4-2.6 of Iliad worksheet C.4 Condensation. Section 2.4 (Why an agent would want these conditions) gives the conditioned score chi(B), the decomposition into the Markov defect and latent information not recoverable from X_B, the reconstruction reading (no dead weight) and the local-inference reading of the Markov condition, with Exercise 2.10 (Local inference). Section 2.5 (optional) treats several observations as one witness with Exercise 2.11 (Block witnesses); Section 2.6 (optional) compares the conditioned score with the simple score sigma(B) and the KL form, with Exercise 2.12 (The two charges). Exercises have collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.4 Why an agent would want these conditions

The correspondence theorem is meant to show when the latents of different agents correspond, so the conditions should not be motivated by correspondence itself. They should serve a single agent's own interests. This section gives two such readings.

**The conditioned score.**  Suppose an agent stores each latent given the more general ones, and answers a query about an observation block $$B$$ by reading every latent active for $$B$$, most general first. Its expected description length is the *conditioned score*

$$
\chi(B)=\sum_{A\in\mathcal{J}_B}H(Y_{A}\mid Y_{{\mathord{\supseteq}} A\setminus\{A\}}).
$$

Every strict superset of an address meeting $$B$$ also meets $$B$$, so the conditioning is available when reading in reverse inclusion order. Put $$V_{B}=\chi(B)-H(Y_{\mathcal{J}_B})$$. Then

$$
\chi(B)-H(X_{B})=V_{B}+H(Y_{\mathcal{J}_B}\mid X_{B}),\qquad V_{B}\ge0.
$$

The second term charges latent information not recoverable from $$X_{B}$$. The first charges dependence not accounted for by the inclusion hierarchy. It vanishes under the Markov condition. Exercise 2.12 proves the decomposition.

An agent that answers queries about a block $$B$$ pays $$\chi(B)$$, and no latent model does better than $$H(X_{B})$$. The gap splits into exactly our two defects. Short descriptions for the queries an agent cares about *are* small defects. For $$i\in A$$, the singleton gap $$\chi(\{i\})-H(X_{i})$$ bounds $$H(Y_{{\mathord{\supseteq}} A}\mid X_{i})$$, the reconstruction hypothesis of Theorem 2.6 (Exercise 2.12). So the conditions need not be assumed as a coincidence: efficient agents buy them. Efficiency is relative to the blocks an agent actually queries, and there is not always a single model minimizing the score for every block.

**Reconstruction: no dead weight.**  The concept at $$A$$ is used whenever any observation in $$A$$ is. Information that only some of those circumstances can use is stored where it is dead weight most of the time the concept is used. The reconstruction error $$H(Y_{{\mathord{\supseteq}} A}\mid X_{i})$$ measures exactly the part of the concept that a query about $$X_{i}$$ pays for but cannot pin down. In the top-latent model of Exercise 2.2, $$Y_{\{1,2,3\}}=(S,P,Q)$$ carries the bit $$Q$$, which is dead weight whenever the concept is used for $$X_{1}$$.

**Markov: local inference.**  The Markov term also has a reading that does not mention description length. Once the more general concepts are known, a concept should bear only on the observations in its own scope:

$$
I\bigl(Y_{A};X_{I\setminus A}\mid Y_{{\mathord{\supseteq}} A\setminus\{A\}}\bigr)=0 \qquad\text{for every }A\in{\mathcal{P}^{+}(I)}.
$$

Then when the agent learns or revises something about the concept at $$A$$, it never has to revise its beliefs about observations outside $$A$$, except through $$A$$'s more general context. Given LVM and reconstruction, (6) holds for every address exactly when the Markov condition does.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.10 (★) (Local inference; 15 minutes).** **(a)** In the singleton-copy model of Exercise 2.2, compute the left side of (6) for $$A=\{1\}$$.

**(b)** Let $$I=\{1,2,3\}$$, let $$U$$ be a fair bit, and set $$X_{1}=X_{2}=X_{3}=U$$. File $$U$$ at every pair address, $$Y_{\{1,2\}}=Y_{\{1,3\}}=Y_{\{2,3\}}=U$$, with every other latent constant. Check LVM and reconstruction. Compute the left side of (6) for $$A=\{1,2\}$$, and find upward-closed families violating the Markov condition. Where should $$U$$ be filed instead?

**(c)** Prove that the Markov condition implies (6). Apply Definition 2.4 to $$\mathcal{F}={\mathord{\supseteq}} A$$ and $$\mathcal{G}=\mathcal{J}_{I\setminus A}$$, and identify their intersection.

**(d)** Assume reconstruction. Show that $$Y_{\mathcal{J}_{I\setminus A}}$$ and $$X_{I\setminus A}$$ determine one another. Conclude that (6) for every $$A$$ is the local version of the Markov condition stated after Definition 2.4.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Here $$Y_{\{1\}}=X_{1}=(S,P)$$ and every strict superset of $$\{1\}$$ holds a constant, so the left side is $$I(X_{1};X_{2},X_{3})$$. The pair $$(X_{2},X_{3})$$ determines $$S,P,Q$$, hence $$X_{1}$$, so this is $$H(X_{1})=2$$. The concept at $$\{1\}$$ carries two bits about observations outside its scope that no more general concept accounts for.

**(b)** Each observation equals a latent assigned to it, for example $$X_{1}=Y_{\{1,2\}}$$, so LVM holds. Every nonconstant latent equals $$U=X_{i}$$ for each $$i$$ in its address, so reconstruction holds. The only strict superset of $$\{1,2\}$$ is $$\{1,2,3\}$$, whose latent is constant, so the left side is $$I(U;U)=1$$. For $$\mathcal{F}={\mathord{\supseteq}}\{1,2\}$$ and $$\mathcal{G}={\mathord{\supseteq}}\{1,3\}$$ the intersection is $$\{\{1,2,3\}\}$$, and $$I(Y_{\mathcal{F}};Y_{\mathcal{G}}\mid Y_{\{1,2,3\}})=I(U;U)=1$$. The bit $$U$$ is shared by all three observations, so it belongs at the top address: $$Y_{\{1,2,3\}}=U$$ with every other latent constant is a perfect condensation.

**(c)** An address $$C$$ meets $$I\setminus A$$ exactly when $$C\not\subseteq A$$. So $${\mathord{\supseteq}} A\cap\mathcal{J}_{I\setminus A}$$ consists of the addresses that contain $$A$$ but are not contained in it: the strict supersets of $$A$$. Both families are upward closed, so the Markov condition gives

$$
I\bigl(Y_{{\mathord{\supseteq}} A};Y_{\mathcal{J}_{I\setminus A}}\mid Y_{{\mathord{\supseteq}} A\setminus\{A\}}\bigr)=0.
$$

The tuple $$Y_{A}$$ is part of $$Y_{{\mathord{\supseteq}} A}$$, and by LVM $$X_{I\setminus A}$$ is a function of $$Y_{\mathcal{J}_{I\setminus A}}$$, which contains $$Y_{{\mathord{\supseteq}}\{j\}}$$ for every $$j\notin A$$. Conditional mutual information cannot increase when either side is replaced by a function of it, so the left side of (6) is zero.

**(d)** Every $$C\in\mathcal{J}_{I\setminus A}$$ contains some $$j\notin A$$, and reconstruction makes $$Y_{C}$$ a function of $$X_{j}$$. So $$Y_{\mathcal{J}_{I\setminus A}}$$ is a function of $$X_{I\setminus A}$$, and the previous part gave the converse. The left side of (6) therefore equals $$I(Y_{A};Y_{\mathcal{J}_{I\setminus A}}\mid Y_{{\mathord{\supseteq}} A\setminus\{A\}})$$. The family $$\mathcal{J}_{I\setminus A}$$ consists of the strict supersets of $$A$$, on which we condition, and the addresses incomparable with $$A$$. So the quantity vanishes exactly when $$Y_{A}$$ is conditionally independent of the incomparable latents given its strict supersets. Required for every $$A$$, this is the local version of the Markov condition, which is equivalent to it.

:::

\### 2.5 Optional: several observations as one witness

A shared parameter need not be recoverable from a single observation. For example, take $$n\ge2$$, let $$L$$ be a fair bit, and set $$X_{i}=L\mathbin{\oplus}N_{i}$$, where the $$N_{i}$$ are independent Bernoulli$$(q)$$ noises with $$0<q<1/2$$, independent of $$L$$. The model $$Y_{I}=L$$, $$Y_{\{i\}}=X_{i}$$ satisfies LVM and the Markov condition exactly, but $$H(L\mid X_{i})=h_{2}(q)>0$$, where $$h_{2}$$ is the binary entropy function of Section 2.2.1. Larger observation blocks can reveal more about $$L$$. To use them in the proof, replace $${\mathord{\supseteq}}\{i\}$$ by $$\mathcal{J}_{B}$$.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.11 (Block witnesses; optional, 25 minutes).** **(a)** Let $$I=\{1,2,3\}$$ and suppose a target $$U$$ has conditional entropy at most $$\delta$$ given each of $$X_{\{1,2\}}$$, $$X_{\{1,3\}}$$, and $$X_{\{2,3\}}$$. Which addresses survive the intersection $$\mathcal{J}_{\{1,2\}}\cap\mathcal{J}_{\{1,3\}}\cap\mathcal{J}_{\{2,3\}}$$? Prove a bound on the entropy of $$U$$ given the surviving $$Z$$-latents.

**(b)** More generally, let $$\mathcal{W}$$ be a nonempty finite family of nonempty observation blocks. Adapt Exercise 2.9 to show

$$
H(U\mid Z_{\mathcal{R}})\le \sum_{B\in\mathcal{W}}H(U\mid X_{B})+(|\mathcal{W}|-1)\eta_{Z}, \qquad \mathcal{R}=\bigcap_{B\in\mathcal{W}}\mathcal{J}_{B}.
$$

**(c)** Fix an integer $$0\le r<|A|$$ and take every $$(r+1)$$-element subset of $$A$$ as a witness. Show that $$C\in\mathcal{R}$$ exactly when $$|A\setminus C|\le r$$. What does this give for $$r=0$$? Why is $$\mathcal{R}$$ generally larger for $$r>0$$?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** A nonempty address $$C\subseteq\{1,2,3\}$$ meets each of $$\{1,2\},\{1,3\},\{2,3\}$$ precisely when $$|C|\ge2$$. A singleton misses the complementary pair; every address with at least two elements meets every pair. Thus the surviving tuple consists of the three pair latents and the top latent. Applying the two-witness lemma twice, after observable transfer for each block, gives

$$
H(U\mid Z_{\{C:|C|\ge2\}})\le3\delta+2\eta_{Z}.
$$

It does not isolate the top latent alone.

**(b)** For each block $$B$$, the family $$Z_{\mathcal{J}_B}$$ determines $$X_{B}$$: for every $$i\in B$$ it contains $$Z_{{\mathord{\supseteq}}\{i\}}$$. Exercise 2.7 therefore extends to $$H(U\mid Z_{\mathcal{J}_B})\le H(U\mid X_{B})$$. Each $$\mathcal{J}_{B}$$ is upward closed. Enumerate $$\mathcal{W}=\{B_{1},\ldots,B_{N}\}$$ and intersect the first $$j$$ contributing families. Exactly the induction in Exercise 2.9, now with these families as leaves, gives

$$
H(U\mid Z_{\mathcal{R}})\le \sum_{B\in\mathcal{W}}H(U\mid X_{B})+(N-1)\eta_{Z}, \quad \mathcal{R}=\bigcap_{B\in\mathcal{W}}\mathcal{J}_{B}.
$$

For $$N=1$$ this is just the transfer inequality. We required a nonempty family so the induction and the intersection count apply.

**(c)** An address $$C$$ fails to meet some $$(r+1)$$-subset of $$A$$ exactly when $$A\setminus C$$ contains at least $$r+1$$ elements. Thus it meets every such subset exactly when $$|A\setminus C|\le r$$. For $$r=0$$ this says $$A\subseteq C$$, recovering the tower. For $$r>0$$ an address can survive even if it misses some elements of $$A$$; $$\mathcal{R}$$ is a larger family. If every witness error is at most $$\delta$$, write $$N=\binom{|A|}{r+1}$$ to obtain the explicit bound $$N\delta+(N-1)\eta_{Z}$$. The restriction $$r<|A|$$ ensures witnesses exist.

:::

Eisenstat's almost-perfect condensation (Eisenstat 2025) builds in block witnesses of this kind, with a threshold $$r$$ on $$|A\cap B|$$ that lets small latents absorb local noise.

\### 2.6 Optional: more on the conditioned score

Compare the conditioned score of Section 2.4 with the simple score

$$
\sigma(B)=\sum_{A\in\mathcal{J}_B}H(Y_{A}),
$$

which charges each latent active for $$B$$ separately, ignoring what the more general latents already say. Both are ideal expected description-length quantities.

For a graphical-model expression, define

$$
q_{B}(y)=\prod_{A\in\mathcal{J}_B}p(y_{A}\mid y_{{\mathord{\supseteq}} A\setminus\{A\}}).
$$

This is a normalized distribution: sample larger addresses before smaller ones. Conditional kernels on probability-zero parent configurations can be chosen arbitrarily. Direct expansion gives $$V_{B}=D_{\mathrm{KL}}(p_{Y_{\mathcal{J}_B}}\Vert q_{B})$$. Thus (5) separates two nonnegative defects.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.12 (The two charges; optional, 25 minutes).** **(a)** Order $$\mathcal{J}_{B}$$ so strict supersets appear first. Use the chain rule and conditioning inequality to prove $$\chi(B)\ge H(Y_{\mathcal{J}_B})$$.

**(b)** Use LVM to prove $$H(Y_{\mathcal{J}_B})-H(X_{B})=H(Y_{\mathcal{J}_B}\mid X_{B})$$, hence (5).

**(c)** For both models in Exercise 2.4, calculate $$\sigma(\{1,2\})$$ and $$\chi(\{1,2\})$$. Why is copying the top variable into a lower latent free under one score but not the other?

**(d)** If $$A\cap B\ne\varnothing$$, show that $$H(Y_{{\mathord{\supseteq}} A}\mid X_{B})\le\chi(B)-H(X_{B})$$.

**(e)** Prove that a latent model is a perfect condensation exactly when $$\chi(B)=H(X_{B})$$ for every nonempty block $$B$$, which is Eisenstat's definition.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** List $$\mathcal{J}_{B}$$ as $$A_{1},\ldots,A_{q}$$ with strict supersets appearing before subsets. Such an order exists because strict inclusion has no cycles. Every strict superset of an active address also meets $$B$$, so is in this list. Therefore

$$
H(Y_{A_t}\mid Y_{{\mathord{\supseteq}} A_t\setminus\{A_t\}}) \ge H(Y_{A_t}\mid Y_{A_1},\ldots,Y_{A_{t-1}}).
$$

Summing and applying the chain rule gives $$\chi(B)\ge H(Y_{\mathcal{J}_B})$$, hence $$V_{B}\ge0$$.

**(b)** Since $$Y_{\mathcal{J}_B}$$ determines $$X_{B}$$, the joint entropy can be expanded in two ways:

$$
H(X_{B},Y_{\mathcal{J}_B})=H(Y_{\mathcal{J}_B}) =H(X_{B})+H(Y_{\mathcal{J}_B}\mid X_{B}).
$$

Subtracting $$H(X_{B})$$ and adding $$V_{B}$$ proves

$$
\chi(B)-H(X_{B})=V_{B}+H(Y_{\mathcal{J}_B}\mid X_{B}).
$$

**(c)** In Exercise 2.4, the independent model $$Y$$ has simple score $$1+1+1=3$$ and conditioned score $$1+1+1=3$$. In model $$Z$$, the simple score is $$1+2+2=5$$, while the conditioned score is

$$
H(C)+H(C,R\mid C)+H(C,T\mid C)=1+1+1=3.
$$

Both models determine $$X_{1},X_{2}$$, whose joint entropy is three. The conditioned score charges only the extra information below $$C$$; its copies add zero conditional entropy. The simple score charges those copies again.

**(d)** If $$A\cap B\ne\varnothing$$, every $$C\supseteq A$$ meets $$B$$. Thus $$Y_{{\mathord{\supseteq}} A}$$ is a subtuple of $$Y_{\mathcal{J}_B}$$ and

$$
H(Y_{{\mathord{\supseteq}} A}\mid X_{B}) \le H(Y_{\mathcal{J}_B}\mid X_{B}) \le\chi(B)-H(X_{B}),
$$

where the last inequality uses the nonnegative score decomposition.

**(e)** Let $$V_{I}=\chi(I)-H(Y_{{\mathcal{P}^{+}(I)}})$$. For upward-closed $$\mathcal{F},\mathcal{G}$$, partition $${\mathcal{P}^{+}(I)}$$ into

$$
\mathcal{C}=\mathcal{F}\cap\mathcal{G},\quad \mathcal{P}=\mathcal{F}\setminus\mathcal{G},\quad \mathcal{Q}=\mathcal{G}\setminus\mathcal{F},\quad \mathcal{R}={\mathcal{P}^{+}(I)}\setminus(\mathcal{F}\cup\mathcal{G}).
$$

Order these blocks $$\mathcal{C},\mathcal{P},\mathcal{Q},\mathcal{R}$$, internally by reverse inclusion. Upward closure ensures this order is valid and no latent in $$\mathcal{Q}$$ has a strict superset in $$\mathcal{P}$$, or conversely. Conditioning inequalities and chain rules within each block imply

$$
\begin{aligned}\chi(I)&\ge H(Y_{\mathcal{C}})+H(Y_{\mathcal{P}}\mid Y_{\mathcal{C}}) +H(Y_{\mathcal{Q}}\mid Y_{\mathcal{C}}) +H(Y_{\mathcal{R}}\mid Y_{\mathcal{C}},Y_{\mathcal{P}},Y_{\mathcal{Q}})\\&=H(Y_{{\mathcal{P}^{+}(I)}})+I(Y_{\mathcal{P}};Y_{\mathcal{Q}}\mid Y_{\mathcal{C}}).\end{aligned}
$$

The latter mutual information equals $$I(Y_{\mathcal{F}};Y_{\mathcal{G}}\mid Y_{\mathcal{F}\cap\mathcal{G}})$$. Hence $$\eta_{Y}\le V_{I}$$.

If all score gaps vanish, the decomposition forces $$V_{I}=0$$, giving the Markov condition. The singleton gap at $$B=\{i\}$$ forces the contributing tuple, and therefore each latent at an address containing $$i$$, to be determined by $$X_{i}$$. This gives reconstruction.

Conversely, suppose reconstruction and the Markov condition hold. For every $$B$$, each active latent $$Y_{A}$$ is determined by some $$X_{i}$$ with $$i\in A\cap B$$, and hence by $$X_{B}$$. Therefore $$H(Y_{\mathcal{J}_B}\mid X_{B})=0$$. In a reverse-inclusion order, the earlier latents consist of all strict supersets of the current latent and some incomparable latents. The global Markov condition implies that conditioning on these extra earlier latents does not reduce its entropy beyond conditioning on strict supersets: apply the condition to the upward cone of the current address and the upward-closed family of earlier addresses. Their intersection is the strict-superset family. Thus the score's chain-rule inequality is an equality, $$V_{B}=0$$. The decomposition gives $$\chi(B)=H(X_{B})$$ for all $$B$$.

:::

Small score gaps therefore force small defects. The converse for Eisenstat's positive-threshold version needs extra reconstruction coverage (Benson 2026).

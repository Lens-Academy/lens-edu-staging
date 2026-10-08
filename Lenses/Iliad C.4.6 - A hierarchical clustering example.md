---
id: '8781b3b3-b656-4b00-b5fa-18413b905e37'
title: "C.4.6 A hierarchical clustering example"
tldr: "Work through a finite hierarchical clustering law with 36 points and compare three latent models of it against the conditions."
summary_for_tutor: "This is Section 3 (A hierarchical clustering example) of Iliad worksheet C.4 Condensation: 3.1 Thirty-six observations (two groups, two clusters each, nine points per cluster), 3.2 An explicit finite law on a grid, 3.3 A structured latent model (Y_I = S, group centers G_g, cluster centers M_gc, singleton latents), 3.4 Three organizations of the same observable law with Exercise 3.1 (The three organizations and the conditions, optional, parts a-c) and a collapsed solution, and 3.5 Why blocks help recover parameters. Keep the notation S, G_g, M_gc, A_g, A_gc and the conditioned score. Let the student attempt the exercise before revealing or paraphrasing a solution."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 3. A hierarchical clustering example

\### 3.1 Thirty-six observations

There are two groups, each containing two clusters, each with nine observations. Write $$X_{gcj}$$ for the $$j$$th two-dimensional point in cluster $$c$$ of group $$g$$. The labels $$(g,c,j)$$ and memberships are fixed. We are comparing models of this labeled family, not inferring an unknown partition of an unlabeled cloud.

The parameters are a global shape $$S$$, group centers $$G_{1},G_{2}$$, and cluster centers $$M_{gc}$$. Given these parameters, the 36 observations are independent. Marginalizing over shared parameters generally makes observations dependent. The plotted cloud in Figure 1 is one realization; the random variables and their entropies refer to the joint law across realizations.

\### 3.2 An explicit finite law

Let $$D=\{0,\ldots,200\}^{2}$$. Draw $$S$$ uniformly from three shape labels, and draw $$G_{1},G_{2}$$ independently and uniformly from $$\{60,\ldots,140\}^{2}$$, independently of $$S$$. Conditional on $$G_{g}$$, draw its two centers independently:

$$
P(M_{gc}=m\mid G_{g}=a)\ \propto\
\exp\!\left(-\frac{\|m-a\|^{2}}{128}\right),\qquad m\in D.
$$

Given $$S$$ and all centers, draw the observations independently, using

$$
P(X_{gcj}=x\mid M_{gc}=m,S=s)\ \propto\
\exp\!\left(-\tfrac{1}{2}(x-m)^{\mathsf{T}}Q_{s}^{-1}(x-m)\right),\quad x\in D,
$$

where

$$
Q_{\mathrm{round}}=\begin{pmatrix}5&0\\0&5\end{pmatrix},\quad Q_{\mathrm{right}}=\begin{pmatrix}25&20\\20&25\end{pmatrix},\quad Q_{\mathrm{left}}=\begin{pmatrix}25&-20\\-20&25\end{pmatrix}.
$$

Each proportionality means normalization by the sum over $$D$$. These are probability mass functions on a finite grid. The matrices control shape; they are not the exact covariances after discretization and boundary truncation. Every grid point has positive probability. Cluster centers tend to lie near their group center, but the four components need not be visually separated in every realization.

\### 3.3 A structured latent model

Let $$I$$ contain all 36 indices. Let $$A_{g}$$ be the 18 indices of group $$g$$, and $$A_{gc}$$ the nine indices of cluster $$(g,c)$$. Assign

$$
Y_{I}=S,\qquad Y_{A_g}=G_{g},\qquad Y_{A_{gc}}=M_{gc},\qquad Y_{\{i\}}=X_{i},
$$

and make every other latent constant. The joint law factorizes in the address inclusion order, so its Markov defect is zero.

LVM holds exactly because the singleton latent supplies the sampled point itself. The cluster center and shape alone only specify a distribution for the point, leaving residual conditional entropy $$H(X_{i}\mid M_{gc},S)$$.

Reconstruction is different. All the kernels have full support, so any finite observation block leaves several parameter configurations with positive posterior probability. For example, $$H(M_{gc}\mid X_{i})>0$$. The model's joint law satisfies the Markov condition exactly, but it is not a perfect condensation. Since every combination of points has positive probability and the points are dependent, no latent model of this law is (Exercise 2.3).

For a nonempty block $$B$$, the general score-gap identity (5) is

$$
\chi(B)-H(X_{B}) =\bigl[\chi(B)-H(Y_{\mathcal{J_B}})\bigr] +H(Y_{\mathcal{J_B}}\mid X_{B}).
$$

Here the bracketed Markov term is zero. The gap is the latent information remaining uncertain after observing the queried block.

\### 3.4 Three organizations of the same observable law

For a nonempty queried *observation block* $$B$$, the conditioned score sums the charges of all latents active for $$B$$.

**One global tuple.**  Put $$Z_{I}=X_{I}$$ and make every other latent constant. The global latent determines each observation. This is the top-latent model of Exercise 2.2 at scale: it satisfies the Markov condition but fails reconstruction. For every nonempty $$B$$,

$$
\chi_{\mathrm{global}}(B)=H(X_{I}),\qquad \chi_{\mathrm{global}}(B)-H(X_{B})=H(X_{I}\mid X_{B}).
$$

This attains the entropy bound when querying the whole tuple. Even a singleton query incurs the entire tuple's entropy in this score.

**An ordered chain.**  Choose an ordering $$X_{1},\ldots,X_{36}$$. Set $$Z_{\{j,j+1,\ldots,36\}}=X_{j}$$ and make other latents constant. The contributing latents for $$X_{i}$$ contain $$X_{1},\ldots,X_{i}$$. The charge for the latent holding $$X_{j}$$ is $$H(X_{j}\mid X_{1},\ldots,X_{j-1})$$, hence

$$
\chi_{\mathrm{chain}}(B)=H(X_{1},\ldots,X_{\max B}).
$$

This attains the entropy bound for prefix queries. Querying only $$X_{36}$$ costs $$H(X_{I})$$.

**The structured model.**  The score charges the shape once, the group and cluster parameters needed by $$B$$, and the residual uncertainty of each requested observation:

$$
\begin{aligned}\chi_{\mathrm{structured}}(B)={}&H(S) +\sum_{g:B\cap A_g\ne\varnothing}H(G_{g})\\&+\sum_{g,c:B\cap A_{gc}\ne\varnothing}H(M_{gc}\mid G_{g}) +\sum_{i\in B}H(X_{i}\mid M_{g(i)c(i)},S).\end{aligned}
$$

This expression avoids charging for unrelated observations. It need not be smaller than the other scores for every block. In particular, for $$B=I$$ it exceeds $$H(X_{I})$$ by the remaining parameter uncertainty, whereas both baseline constructions attain $$H(X_{I})$$. Fitting the observable law does not by itself settle which organization is preferable across queries.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (The three organizations and the conditions; optional, 10 minutes).** **(a)** Show that the global and chain models satisfy the Markov condition. Why is it automatic for the chain?

**(b)** For a single point $$X_{i}$$, describe the reconstruction error $$H(Z_{{\mathord{\supseteq}}\{i\}}\mid X_{i})$$ in each of the three models. How does it depend on $$i$$ in the chain, and on the number of observations in each model?

**(c)** None of the three models is a perfect condensation. Which comes closest to satisfying the conditions with a small tolerance?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** In the global model every nonempty upward-closed family contains the top address, whose latent is the only nonconstant one, so every Markov term conditions on everything, as in Exercise 2.2. In the chain, the nonconstant addresses $$\{j,\ldots,36\}$$ are nested, so an upward-closed family contains exactly those with $$j$$ up to some bound: its nonconstant latents are $$X_{1},\ldots,X_{a}$$ for some $$a$$. Of two such families, one's nonconstant latents are then those of the intersection, and the Markov term vanishes.

**(b)** In the global model the tower above $$\{i\}$$ is $$X_{I}$$, so the error is $$H(X_{I}\mid X_{i})$$: the uncertainty about all other points, which grows with their number. In the chain the tower is $$(X_{1},\ldots,X_{i})$$, so the error is $$H(X_{1},\ldots,X_{i-1}\mid X_{i})$$: zero for the first point and growing along the ordering. In the structured model the tower is $$(S,G_{g},M_{gc},X_{i})$$, so the error is $$H(S,G_{g},M_{gc}\mid X_{i})$$: the parameter uncertainty a single point leaves, which does not grow with the number of observations.

**(c)** The structured model. It satisfies the Markov condition exactly, and its reconstruction errors are bounded by the parameter uncertainty one point leaves, uniformly in $$i$$ and in the number of points. With a tolerance of that size, or a smaller one using block witnesses (Section 2.5), it satisfies the approximate conditions; the other two models' errors grow with the number of points.

:::

\### 3.5 Why blocks help recover parameters

For nonempty $$B$$ inside a fixed cluster $$(g,c)$$, set $$\Theta=(S,G_{g},M_{gc})$$. The nonconstant contributing tuple is $$(\Theta,X_{B})$$, so

$$
\chi_{\mathrm{structured}}(B)-H(X_{B})=H(\Theta\mid X_{B}).
$$

For nonempty $$B\subseteq B'\subseteq A_{gc}$$, the reduction in this gap is

$$
H(\Theta\mid X_{B})-H(\Theta\mid X_{B'}) =I(\Theta;X_{B'\setminus B}\mid X_{B})\ge0.
$$

More points can inform the shared parameters. Exact recovery still fails for finite blocks. Even knowing one cluster center need not determine its parent group center. This example motivates block witnesses (Section 2.5).

**Source.**  The motivating hierarchy is from Gillen and Chiang, *A summary of Condensation and its relation to Natural Latents* (Gillen & Chiang 2026), §1.1.1. The finite law, illustration, and exact score comparisons above are this course's adaptation.

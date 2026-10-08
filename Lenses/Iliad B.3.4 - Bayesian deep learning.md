---
id: 'e4242be2-d6d7-40d1-9907-30ea662e4fbd'
title: "B.3.4 Bayesian deep learning"
tldr: "Covers Bayesian inference for networks: prior, posterior, partition function, free energy, and local versions over a neighbourhood of parameter space."
summary_for_tutor: "This is Section 1.4 of worksheet B.3 (singular learning theory). It gives Definition 1.5 (posterior pi_n, partition function Z_n, free energy F_n = -log Z_n) and Definition 1.6 (local partition function Z_n(U) and local free energy F_n(U)). It contains Exercises 1.6 (posterior as a Gibbs distribution), 1.7 (local posterior mass and local free energy) and 1.8 (partition function of a partitioned parameter space) with collapsed solutions. Keep the notation phi, pi_n, Z_n, F_n, U. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Kai Ogden (University of Oxford)
  - Matthew Farrugia-Roberts (University of Oxford)
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/singular-learning-theory/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 1.4 Bayesian deep learning

The principle of maximum likelihood, explored in the preceding exercises, is one approach to statistical inference. An alternative approach is **Bayesian inference**, which treats $w$ as a random variable and maintains a probability distribution over ${\mathcal{W}}$ reflecting our uncertainty about which parameter best explains the data. The majority of theoretical results in SLT have been developed within this setting (Watanabe 2009; Watanabe 2018, cf.,).

Bayesian learning begins with a **prior** distribution $\varphi \in \Delta({\mathcal{W}})$, a probability density on ${\mathcal{W}}$ representing our beliefs about the parameter $w$ before observing any data. Throughout this tutorial, we assume $\varphi$ is positive and smooth on ${\mathcal{W}}$.

:::callout {title="Definition" tone="blue"}

**Definition 1.5 (Posterior distribution, partition function, free energy).** Given a data set of $n$ input–output pairs $(x^{(1)}, y^{(1)}),$ $\ldots,$ $(x^{(n)}, y^{(n)}) \in {\mathcal{X}} \times {\mathcal{Y}}$, Bayes' rule updates the prior into the **posterior distribution** $\pi_{n} \in \Delta({\mathcal{W}})$, a probability density on ${\mathcal{W}}$ defined by

$$
\pi_{n}(w) = \frac{1}{Z_{n}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w)
$$

where $Z_{n} \in {\mathbb{R}}$ is a normalising constant called the **partition function** (or **marginal likelihood** or **model evidence**),

$$
Z_{n} = \int_{{\mathcal{W}}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w)\, dw.
$$

We often work with the **(Bayesian) free energy**, the negative log of the model evidence,

$$
F_{n} = -\log Z_{n}.
$$

:::

The posterior re-weights the prior by the likelihood of the observed data: parameters $w$ under which the data is more probable receive higher posterior density, while parameters under which the data is improbable are down-weighted.

The partition function $Z_{n}$ is the marginal probability of observing the data set, averaged over all parameters weighted by the prior. It quantifies how well the statistical model *as a whole* predicts the observed data. The free energy is an inverted measure of how well the model fits the data.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.6 (Bayesian posterior as a Gibbs distribution).** To interpret Bayesian inference in terms more similar to function approximation, we introduce a loss function based on the **negative log-likelihood**,

$$
\begin{aligned}L_{x,y}(w)&= -\log p(y \mid x, w), \\ L_{n}(w)&= -\frac{1}{n}\sum_{i=1}^{n}\log p(y^{(i)}\mid x^{(i)}, w).\end{aligned}
$$

Here, $p(y \mid x, w)$ is the conditional density from the parameter–distribution map and $(x^{(1)}, y^{(1)}),$ $\ldots,$ $(x^{(n)}, y^{(n)}) \in {\mathcal{X}} \times {\mathcal{Y}}$ is a data set of $n$ examples. Show that

$$
\pi_{n}(w) = \frac{1}{Z_{n}}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)
$$

and

$$
Z_{n} = \int_{{\mathcal{W}}}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)\, dw.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By definition of the negative log-likelihood,

$$
n L_{n}(w) = -\sum_{i=1}^{n}\log p(y^{(i)}\mid x^{(i)}, w).
$$

Exponentiating both sides,

$$
\exp\!\big({-}n L_{n}(w)\big) = \exp\!\left(\sum_{i=1}^{n}\log p(y^{(i)}\mid x^{(i)}, w)\right) = \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w).
$$

Substituting into the definitions of the posterior (13) and partition function (14) gives the stated expressions.

:::

The **Bayesian deep learning process** is the process of re-weighting each individual parameter vector in response to seeing an increasing amount of data, producing the sequence of belief distributions $\varphi, \pi_{1}, \pi_{2}, \ldots \in \Delta({\mathcal{W}})$. Over time, the posterior will concentrate around parameters which provide a good fit for the data (though there is more to the story in the singular case, as we will see in later sections).

Bayesian deep learning is a *global search* in that all parameter vectors are considered in parallel. This makes exact Bayesian learning computationally intractable for non-trivial models, but more analytically tractable than SGD in general. Moreover, as we will explore in later sections, the dynamics of Bayesian learning still reflect the local geometry of the parameter–distribution map.

In preparation for exploring this connection between geometry and learning, we finally introduce localised variants of the partition function and free energy, where the integral in (14) is restricted to a certain neighbourhood in parameter space.

:::callout {title="Definition" tone="blue"}

**Definition 1.6 (Local partition function and local free energy).** Given a neighbourhood ${\mathcal{U}} \subseteq {\mathcal{W}}$, the **local partition function** and **local free energy** are

$$
Z_{n}({\mathcal{U}}) = \int_{{\mathcal{U}}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w)\, dw, \qquad F_{n}({\mathcal{U}}) = -\log Z_{n}({\mathcal{U}}).
$$

:::

The local partition function (free energy) measures how well (poorly) parameters within a given neighbourhood collectively explain the data. Note, $Z_{n}({\mathcal{W}}) = Z_{n}$ and $F_{n}({\mathcal{W}}) = F_{n}$.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.7 (Local posterior mass and local free energy).** Let ${\mathcal{U}}, {\mathcal{V}} \subseteq {\mathcal{W}}$ be two neighbourhoods of parameter space. Let $\pi_{n}({\mathcal{U}}) = \int_{{\mathcal{U}}}\pi_{n}(w) \,dw$ denote the posterior mass of a neighbourhood. Show the following.

**(a)** $\displaystyle \pi_{n}({\mathcal{U}}) = \frac{Z_{n}({\mathcal{U}})}{Z_{n}}$ (the same holds for ${\mathcal{V}}$).

**(b)** $\displaystyle \log \frac{\pi_{n}({\mathcal{U}})}{\pi_{n}({\mathcal{V}})}= F_{n}({\mathcal{V}}) - F_{n}({\mathcal{U}})$.

In conclusion, the posterior odds ratio of the two regions $\pi_{n}({\mathcal{U}}) / \pi_{n}({\mathcal{V}})$ depends exponentially on the difference between their local free energies.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Integrating the posterior (13) over ${\mathcal{U}}$,

$$
\pi_{n}({\mathcal{U}}) = \int_{{\mathcal{U}}}\pi_{n}(w) \, dw = \int_{{\mathcal{U}}}\frac{1}{Z_{n}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w) \, dw = \frac{Z_{n}({\mathcal{U}})}{Z_{n}}.
$$

**(b)** By part (a),

$$
\log \frac{\pi_{n}({\mathcal{U}})}{\pi_{n}({\mathcal{V}})}= \log \frac{Z_{n}({\mathcal{U}}) / Z_{n}}{Z_{n}({\mathcal{V}}) / Z_{n}}= \log Z_{n}({\mathcal{U}}) - \log Z_{n}({\mathcal{V}}) = F_{n}({\mathcal{V}}) - F_{n}({\mathcal{U}}).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.8 (Partition function of partitioned parameter space).** Let ${\mathcal{U}}_{1}, \ldots, {\mathcal{U}}_{k} \subseteq {\mathcal{W}}$ be disjoint subsets with ${\mathcal{W}} = {\mathcal{U}}_{1} \sqcup \cdots \sqcup {\mathcal{U}}_{k}$.

**(a)** Show that the partition function decomposes as $Z_{n} = \sum_{j=1}^{k} Z_{n}({\mathcal{U}}_{j})$, and hence

$$
F_{n} = -\log \sum_{j=1}^{k} e^{-F_n({\mathcal{U}}_j)}.
$$

**(b)** Show that if $F_{n}({\mathcal{U}}_{1}) < F_{n}({\mathcal{U}}_{j})$ for all $j \neq 1$, then

$$
F_{n}({\mathcal{U}}_{1}) - \log k < F_{n} < F_{n}({\mathcal{U}}_{1}).
$$

In conclusion, the overall free energy is dominated by the region(s) with the lowest local free energy.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since ${\mathcal{U}}_{1}, \ldots, {\mathcal{U}}_{k}$ are disjoint and cover ${\mathcal{W}}$, the integral over ${\mathcal{W}}$ decomposes as a sum of integrals over each ${\mathcal{U}}_{j}$:

$$
\begin{aligned}Z_{n}&= \int_{{\mathcal{W}}}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)\, dw \\&= \sum_{j=1}^{k}\int_{{\mathcal{U}}_j}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)\, dw = \sum_{j=1}^{k}Z_{n}({\mathcal{U}}_{j}).\end{aligned}
$$

By definition, $Z_{n}({\mathcal{U}}_{j}) = e^{-F_n({\mathcal{U}}_j)}$, so $Z_{n} = \sum_{j=1}^{k}e^{-F_n({\mathcal{U}}_j)}$. Taking $-\log$ of both sides,

$$
F_{n} = -\log Z_{n} = -\log \sum_{j=1}^{k}e^{-F_n({\mathcal{U}}_j)}.
$$

**(b)** Since $F_{n}({\mathcal{U}}_{1}) < F_{n}({\mathcal{U}}_{j})$ for all $j \neq 1$, the corresponding partition functions satisfy $Z_{n}({\mathcal{U}}_{1}) > Z_{n}({\mathcal{U}}_{j})$ for all $j \neq 1$. The lower bound on $Z_{n}$ is immediate:

$$
Z_{n} = \sum_{j=1}^{k}Z_{n}({\mathcal{U}}_{j}) > Z_{n}({\mathcal{U}}_{1}).
$$

For the upper bound, since each $Z_{n}({\mathcal{U}}_{j}) < Z_{n}({\mathcal{U}}_{1})$,

$$
Z_{n} = \sum_{j=1}^{k}Z_{n}({\mathcal{U}}_{j}) < k \cdot Z_{n}({\mathcal{U}}_{1}).
$$

Taking $-\log$ (which reverses the inequalities) yields

$$
F_{n}({\mathcal{U}}_{1}) - \log k < F_{n} < F_{n}({\mathcal{U}}_{1}).
$$

The overall free energy is therefore determined by the region with the lowest local free energy, up to a correction of at most $\log k$. In particular, if the gap $F_{n}({\mathcal{U}}_{j}) - F_{n}({\mathcal{U}}_{1})$ grows with $n$ while $k$ remains fixed, then $F_{n} \to F_{n}({\mathcal{U}}_{1})$.

:::

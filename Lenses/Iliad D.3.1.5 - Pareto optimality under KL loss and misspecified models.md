---
id: 'bba1c86c-4152-4ef3-8d67-0f9b00d660e7'
title: "D.3.1.5 Pareto optimality under KL loss and misspecified models"
tldr: "Shows the mixture is Pareto-optimal under KL loss, then bounds its error when the true environment is not in the model class."
summary_for_tutor: "Sections 6 and 7 of worksheet D.3.1. Definition 6.1 (Pareto domination), Exercise 6.1 (KL Pythagorean identity), Exercise 6.2 (xi is Pareto-optimal under KL), and Exercise 7.1 (misspecified bound D_n(mu||xi) <= -ln w_muhat + D_n(mu||muhat)), with a remark on the complexity and approximation terms. Appendix D is referenced for the choice of muhat. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/agency/solomonoff-induction/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 6. Pareto optimality under KL loss

In Section 6 and Section 8 we establish that the Bayesian mixture $\xi$ is *uniquely Pareto-optimal* under both KL and squared prediction loss: no other predictor can do at least as well as $\xi$ on every environment $\nu \in {\mathcal{M}}$ without coinciding with $\xi$ entirely.

:::callout {title="Definition" tone="blue"}

**Definition 6.1 (Pareto domination).** For some measure of **loss** $\mathcal{F}(\nu, \rho)$ that takes an environment $\nu$ and a predictor $\rho$, a predictor $\rho$ **weakly Pareto-dominates** $\xi$ with respect to loss $\mathcal{F}$ and class $\mathcal{M}$ if

$$
\mathcal{F}(\nu, \rho) ~\leq~ \mathcal{F}(\nu, \xi) \qquad \text{for every }\nu \in {\mathcal{M}}.
$$

$\xi$ is **Pareto-optimal** (w.r.t. $\mathcal{F}$) if the only predictor that weakly dominates it is $\xi$ itself.

We specialize $\mathcal{F}$ to $D_{n}(\nu \parallel \rho)$ in Section 6 and to $S_{n}(\nu \parallel \rho)$ in Section 8.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 6.1 (KL Pythagorean identity) [10].** For *any* predictor $\rho$ with $\rho(x_{1:n}) > 0$ on every $x_{1:n}\in \mathbb{B}^{n}$, show that

$$
D_{n}(\xi \parallel \rho) ~+~ \sum_{\nu \in {\mathcal{M}}}w_{\nu} \, D_{n}(\nu \parallel \xi) ~=~ \sum_{\nu \in {\mathcal{M}}}w_{\nu} \, D_{n}(\nu \parallel \rho).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Take the difference between the two summation terms.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Take the difference $\sum_{\nu} w_{\nu} D_{n}(\nu \parallel \rho) - \sum_{\nu} w_{\nu} D_{n}(\nu \parallel \xi)$. Inside each $D_{n}$ the $\nu(x_{1:n}) \ln \nu(x_{1:n})$ pieces cancel, leaving

$$
\begin{aligned}&\sum_{\nu} w_{\nu} D_{n}(\nu \parallel \rho) - \sum_{\nu} w_{\nu} D_{n}(\nu \parallel \xi) \\&\quad= \sum_{\nu} w_{\nu} \sum_{x_{1:n}}\nu(x_{1:n})\,\Bigl[\ln\tfrac{\nu(x_{1:n})}{\rho(x_{1:n})}- \ln\tfrac{\nu(x_{1:n})}{\xi(x_{1:n})}\Bigr] \\&\quad= \sum_{\nu} w_{\nu} \sum_{x_{1:n}}\nu(x_{1:n})\,\ln \tfrac{\xi(x_{1:n})}{\rho(x_{1:n})}.\end{aligned}
$$

The factor $\ln(\xi/\rho)$ does not depend on $\nu$, so we swap the order of summation and pull it out, then use $\sum_{\nu} w_{\nu} \nu(x_{1:n}) = \xi(x_{1:n})$:

$$
\begin{aligned}\sum_{\nu} w_{\nu} \sum_{x_{1:n}}\nu(x_{1:n})\,\ln \tfrac{\xi(x_{1:n})}{\rho(x_{1:n})}&= \sum_{x_{1:n}}\ln \tfrac{\xi(x_{1:n})}{\rho(x_{1:n})}\underbrace{\sum_\nu w_\nu \nu(x_{1:n})}_{=\, \xi(x_{1:n})}\\&= \sum_{x_{1:n}}\xi(x_{1:n}) \,\ln \tfrac{\xi(x_{1:n})}{\rho(x_{1:n})}~=~ D_{n}(\xi \parallel \rho).\end{aligned}
$$

Rearranging gives the claimed identity.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 6.2 (KL Pareto-optimality) [05].** Show that $\xi$ is Pareto-optimal under $D_{n}(\nu \parallel \rho)$ in the sense of Definition 6.1: if $\rho$ is any predictor with

$$
D_{n}(\nu \parallel \rho) ~\leq~ D_{n}(\nu \parallel \xi) \qquad \text{for every }\nu \in {\mathcal{M}},
$$

then $\rho = \xi$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Multiply the assumed inequality by $w_{\nu} \geq 0$ and sum over $\nu \in {\mathcal{M}}$; then apply the KL Pythagorean identity to recognize the extra non-negative term, which must vanish.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Multiply the assumed inequality by $w_{\nu} \geq 0$ and sum over $\nu \in {\mathcal{M}}$:

$$
\sum_{\nu} w_{\nu}\, D_{n}(\nu \parallel \rho) ~\leq~ \sum_{\nu} w_{\nu}\, D_{n}(\nu \parallel \xi).
$$

The KL Pythagorean identity rewrites the LHS as

$$
D_{n}(\xi \parallel \rho) \;+\; \sum_{\nu} w_{\nu}\, D_{n}(\nu \parallel \xi),
$$

so Equation 3 forces $D_{n}(\xi \parallel \rho) \leq 0$. KL is non-negative, hence $D_{n}(\xi \parallel \rho) = 0$, which forces $\rho(x_{1:n}) = \xi(x_{1:n})$ for every $x_{1:n}\in \mathbb{B}^{n}$. By chain rule, the conditionals agree at every history $x_{<t}$ with $\xi(x_{<t}) > 0$.

:::

\## 7. Misspecified models: when $\mu \notin {\mathcal{M}}$

The cumulative bound Section 4 assumed the true environment $\mu$ lives in the model class ${\mathcal{M}}$. What happens when it does not? We now show the bound *degrades gracefully*: it splits cleanly into a complexity term ("cost of not knowing which model is best"), exactly as before, plus a linear-in-time approximation term ("cost of no model being right"). See (Hutter 2005, §3.2.8) for the original treatment.

Throughout this section, we no longer assume $\mu \in {\mathcal{M}}$. We will state the bound in terms of an arbitrary $\hat\mu \in {\mathcal{M}}$, so taking the infimum over $\hat\mu$ on the right-hand side gives the tightest version by using the "closest" approximation of $\hat{\mu}\in {\mathcal{M}}$ to $\mu$.
::::callout {title="Exercise" tone="amber"}
**Exercise 7.1 (Misspecified KL bound) [10].** Show that for all $\hat\mu \in {\mathcal{M}}$,

$$
D_{n}(\mu \parallel \xi) ~\leq~ -\ln w_{\hat\mu}~+~ D_{n}(\mu \parallel \hat\mu).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use Exercise 3.1.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Mixture dominance applied to $\hat\mu \in {\mathcal{M}}$ (Section 3) gives $\xi(x_{1:n}) \geq w_{\hat\mu}\, \hat\mu(x_{1:n})$ for every $x_{1:n}$. Hence $\mu(x_{1:n}) / \xi(x_{1:n}) \leq \mu(x_{1:n}) / (w_{\hat\mu}\, \hat\mu(x_{1:n}))$, and taking logs,

$$
\ln \frac{\mu(x_{1:n})}{\xi(x_{1:n})}~\leq~ -\ln w_{\hat\mu}\;+\; \ln \frac{\mu(x_{1:n})}{\hat\mu(x_{1:n})}.
$$

Now take the $\mu$-expectation. The LHS becomes $D_{n}(\mu \parallel \xi)$; the second RHS term becomes $D_{n}(\mu \parallel \hat\mu)$; the constant $-\ln w_{\hat\mu}$ survives because $\mu(X_{1:n})$ has total mass $1$.

:::

:::callout {title="Note" tone="blue"}

**Remark (Reading the two terms).** The right-hand side splits into two qualitatively different terms:

- $-\ln w_{\hat\mu}$ is *constant in $n$*: under the Solomonoff prior, this is $K(\hat\mu)\ln 2$. The familiar "complexity" cost of search.
- The approximation term $D_{n}(\mu \parallel \hat\mu) = \sum_{t=1}^{n} d_{t}(\mu \parallel \hat\mu)$ (by Exercise 2.1) is a sum of $n$ per-step KLs; in general it grows with $n$. It vanishes identically iff $\hat\mu$ matches $\mu$ on every $\mu$-reachable history, in particular when $\mu \in {\mathcal{M}}$ and we pick $\hat\mu = \mu$, recovering Section 4.

Combining with Pinsker (Theorem 4.1) gives the corresponding bound on $S^{\mu}_{\infty}$, which is infinite in general but inherits the rate of $\hat\mu$.

:::

Details on how to define the best choice of $\hat{\mu}$ are in Appendix D.

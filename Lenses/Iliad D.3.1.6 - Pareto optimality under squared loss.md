---
id: '712c3e12-9bcf-4ffb-8cfa-3d35aafd7bd9'
title: "D.3.1.6 Pareto optimality under squared loss"
tldr: "Proves the mixture is Pareto-optimal under squared prediction loss, using a Pythagorean identity at each history and a switch from posterior to prior weights."
summary_for_tutor: "Section 8 of worksheet D.3.1: Pareto optimality under squared loss. Exercise 8.1 (squared Pythagorean identity at an arbitrary history, using posterior weights w(nu|x_{<t})) and Exercise 8.2 (xi is Pareto-optimal under S_n(nu||rho), using the Bayes identity w(nu|x_{<t}) xi(x_{<t}) = w_nu nu(x_{<t})). Hints and collapsed solutions are given. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
  - Leon Lang (Iliad)
source_url: https://iliad-intensive.org/agency/solomonoff-induction/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 8. Pareto optimality under squared loss

The squared specialization $$\mathcal{F}(\nu, \rho) = S_{n}(\nu \parallel \rho)$$ (Definition 4.2) lives one level down from KL: at the conditional distributions $$\nu(\cdot \mid x_{<t})$$. The natural Pythagorean decomposition at a fixed history uses *posterior* weights $$w(\nu \mid x_{<t})$$: those are the weights that make $$\xi(x_{t} \mid x_{<t})$$ the mean of the $$\nu(x_{t} \mid x_{<t})$$'s (via the posterior-predictive form, Definition 1.2). The Pareto-optimality aggregation, however, uses prior weights $$w_{\nu}$$. Bridging the two takes one extra Bayes-rule step.

::::callout {title="Exercise" tone="amber"}
**Exercise 8.1 (Squared Pythagorean identity) [10].** Fix any $$t \in \{1, \dots, n\}$$ and any history $$x_{<t}\in \mathbb{B}^{t-1}$$: *the history is arbitrary, not sampled from any environment*. For any $$x_{t} \in \mathbb{B}$$ and any predictor $$\rho$$, show

$$
\begin{aligned}&\bigl(\xi(x_{t} \mid x_{<t}) - \rho(x_{t} \mid x_{<t})\bigr)^{2}~+~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t})\,\bigl(\nu(x_{t} \mid x_{<t}) - \xi(x_{t} \mid x_{<t})\bigr)^{2}\\&=~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid x_{<t})\,\bigl(\nu(x_{t} \mid x_{<t}) - \rho(x_{t} \mid x_{<t})\bigr)^{2}.\end{aligned}
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Add and subtract $$\xi(x_{t} \mid x_{<t})$$ inside the squared term, then expand. Use $$\sum_{\nu} w(\nu \mid x_{<t}) = 1$$ and the posterior-predictive form of $$\xi$$ (Definition 1.2), $$\sum_{\nu} w(\nu \mid x_{<t})\,\nu(x_{t} \mid x_{<t}) = \xi(x_{t} \mid x_{<t})$$, to kill the cross-term. The weighting must be *posterior* weights $$w(\nu \mid x_{<t})$$ (not prior weights $$w_{\nu}$$), because $$\xi(x_{t} \mid x_{<t})$$ is the posterior-weighted mean of the $$\nu(x_{t} \mid x_{<t})$$'s, not the prior one.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Throughout, the history $$x_{<t}$$ and symbol $$x_{t}$$ are fixed but arbitrary. Abbreviate $$\nu := \nu(x_{t} \mid x_{<t})$$, $$\xi := \xi(x_{t} \mid x_{<t})$$, $$\rho := \rho(x_{t} \mid x_{<t})$$, and $$\tilde w_{\nu} := w(\nu \mid x_{<t})$$ for the duration of the calculation.

*Step 1: $$\xi$$ is the posterior-weighted mean of the $$\nu$$'s.* By the posterior-predictive form of the mixture (Definition 1.2) and the posterior normalization $$\sum_{\nu} \tilde w_{\nu} = 1$$,

$$
\sum_{\nu} \tilde w_{\nu} \, \nu ~=~ \xi.
$$

*Step 2: the cross-term vanishes.* A direct consequence of Step 1, again using $$\sum_{\nu} \tilde w_{\nu} = 1$$:

$$
\sum_{\nu} \tilde w_{\nu} \, (\nu - \xi) ~=~ \sum_{\nu} \tilde w_{\nu} \, \nu \;-\; \xi \sum_{\nu} \tilde w_{\nu} ~=~ \xi - \xi ~=~ 0.
$$

*Step 3: expand the square.* Write $$\nu - \rho = (\nu - \xi) + (\xi - \rho)$$ and expand:

$$
\begin{aligned}&\sum_{\nu} \tilde w_{\nu} (\nu - \rho)^{2} \\&\quad= \sum_{\nu} \tilde w_{\nu}\bigl[(\nu - \xi)^{2} + 2(\nu - \xi)(\xi - \rho) + (\xi - \rho)^{2}\bigr] \\&\quad= \sum_{\nu} \tilde w_{\nu} (\nu - \xi)^{2} \;+\; 2(\xi - \rho)\sum_{\nu} \tilde w_{\nu} (\nu - \xi) \;+\; (\xi - \rho)^{2} \sum_{\nu} \tilde w_{\nu}.\end{aligned}
$$

The middle sum is zero by Step 2; the trailing $$\sum_{\nu} \tilde w_{\nu} = 1$$. So

$$
(\xi - \rho)^{2} \;+\; \sum_{\nu} \tilde w_{\nu} (\nu - \xi)^{2} ~=~ \sum_{\nu} \tilde w_{\nu} (\nu - \rho)^{2}.
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 8.2 (Squared Pareto-optimality) [05].** Show that $$\xi$$ is Pareto-optimal under $$S_{n}(\nu \parallel \rho)$$ in the sense of Definition 6.1: if $$\rho$$ is any predictor with

$$
S_{n}(\nu \parallel \rho)~\leq~ S_{n}(\nu \parallel \xi)\qquad \text{for every }\nu \in {\mathcal{M}},
$$

then $$\rho(x_{t} \mid x_{<t}) = \xi(x_{t} \mid x_{<t})$$ at every history $$x_{<t}\in \mathbb{B}^{t-1}$$ *with $$\xi(x_{<t}) > 0$$* (equivalently, $$\xi$$-almost surely) and every $$x_{t} \in \mathbb{B}$$. Histories that the mixture never reaches ($$\xi(x_{<t}) = 0$$, i.e., reached by no $$\nu \in {\mathcal{M}}$$ either) are invisible to the loss and are not pinned down.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Multiply the assumed inequality by $$w_{\nu} \geq 0$$ and sum over $$\nu$$; then for each fixed history $$x_{<t}$$, multiply the per-history Pythagorean identity from above by $$\xi(x_{<t})$$ and use the Bayes identity $$w(\nu \mid x_{<t})\,\xi(x_{<t}) = w_{\nu} \,\nu(x_{<t})$$ to bridge from posterior weights (inside the identity) to prior weights (in the aggregated Pareto inequality).

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Multiply the assumed inequality by $$w_{\nu} \geq 0$$ and sum over $$\nu \in {\mathcal{M}}$$:

$$
\sum_{\nu} w_{\nu}\,S_{n}(\nu \parallel \rho)~\leq~ \sum_{\nu} w_{\nu}\,S_{n}(\nu \parallel \xi).
$$

Now bridge to the per-history Pythagorean. At each *fixed* history $$x_{<t}\in \mathbb{B}^{t-1}$$ and symbol $$x_{t} \in \mathbb{B}$$, the identity says

$$
(\xi - \rho)^{2} \;+\; \sum_{\nu} w(\nu \mid x_{<t})\,(\nu - \xi)^{2} ~=~ \sum_{\nu} w(\nu \mid x_{<t})\,(\nu - \rho)^{2},
$$

with the abbreviations $$\nu := \nu(x_{t} \mid x_{<t})$$, $$\xi := \xi(x_{t} \mid x_{<t})$$, $$\rho := \rho(x_{t} \mid x_{<t})$$. Multiply by $$\xi(x_{<t})$$ and use Bayes, $$w(\nu \mid x_{<t})\,\xi(x_{<t}) = w_{\nu} \,\nu(x_{<t})$$:

$$
\xi(x_{<t})(\xi - \rho)^{2} \;+\; \sum_{\nu} w_{\nu} \,\nu(x_{<t})\,(\nu - \xi)^{2} ~=~ \sum_{\nu} w_{\nu} \,\nu(x_{<t})\,(\nu - \rho)^{2}.
$$

Sum over $$t = 1, \dots, n$$ and all histories $$x_{<t}\in \mathbb{B}^{t-1}$$ and symbols $$x_{t} \in \mathbb{B}$$. The two $$\sum_{\nu} w_{\nu} \,\nu(x_{<t})(\cdots)$$ terms become exactly $$\sum_{\nu} w_{\nu} \,S_{n}(\nu \parallel \xi)$$ and $$\sum_{\nu} w_{\nu} \, S_{n}(\nu \parallel \rho)$$ respectively, so

$$
\|\xi - \rho\|_{\xi}^{2} \;+\; \sum_{\nu} w_{\nu}\,S_{n}(\nu \parallel \xi)~=~ \sum_{\nu} w_{\nu}\,S_{n}(\nu \parallel \rho),
$$

where

$$
\|\xi - \rho\|_{\xi}^{2} ~:=~ \sum_{t=1}^{n} \sum_{x_{<t}}\xi(x_{<t}) \sum_{x_t}\bigl(\xi(x_{t} \mid x_{<t}) - \rho(x_{t} \mid x_{<t})\bigr)^{2} ~\geq~ 0.
$$

Combining with Equation 4,

$$
\|\xi - \rho\|_{\xi}^{2} \;+\; \sum_{\nu} w_{\nu}\,S_{n}(\nu \parallel \xi)~\leq~ \sum_{\nu} w_{\nu}\,S_{n}(\nu \parallel \xi)\;\;\Longrightarrow\;\; \|\xi - \rho\|_{\xi}^{2} ~\leq~ 0.
$$

Since $$\|\xi - \rho\|_{\xi}^{2}$$ is a sum of non-negative terms and is itself $$\leq 0$$, every term vanishes: $$\xi(x_{<t})\bigl(\xi(x_{t} \mid x_{<t}) - \rho(x_{t} \mid x_{<t})\bigr)^{2} = 0$$ at every $$(t, x_{<t}, x_{t})$$. So $$\rho(x_{t} \mid x_{<t}) = \xi(x_{t} \mid x_{<t})$$ at every history $$x_{<t}$$ with $$\xi(x_{<t}) > 0$$.

:::

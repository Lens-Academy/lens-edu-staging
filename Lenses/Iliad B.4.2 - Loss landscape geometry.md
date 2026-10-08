---
id: 'd1d53fab-a58e-4bec-b214-868f5aeab65b'
title: "B.4.2 Loss landscape geometry"
tldr: "Finds the critical points of deep linear networks: the loss splits into scalar modes, the origin is a saddle, critical points keep a subset of modes, and global minima form a high-dimensional manifold."
summary_for_tutor: "This is Section 3 'Loss landscape geometry' of worksheet B.4 (training dynamics), following Achour et al. 2024. It contains Exercises 3.1-3.4: diagonal decomposition of the loss, scalar critical points and the Hessian at the origin (eigenvalues +s and -s), critical points W = P_S M with loss 1/2 sum of s_alpha^2 over missing modes, and invariance of the student map under the GL_h action. Collapsed solutions and a hint on 3.2 are included. Keep the notation P_S, GL_h, mu(theta). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Guillaume Corlouer (Stormglass)
source_url: https://iliad-intensive.org/learning/training-dynamics/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 3. Loss landscape geometry

This problem explores the critical point structure of deep linear networks, following (Achour et al. 2024).

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (Diagonal decomposition).** Consider the **diagonal** case: $d_{0} = d_{1} = \cdots = d_{L} = d$, and the teacher is diagonal, $M = \text{diag}(s_{1}, \ldots, s_{d})$, with $s_{1} > s_{2} > \cdots > s_{d} > 0$. Restrict attention to diagonal weight matrices $W_{l} = \text{diag}(w_{l}^{(1)}, \ldots, w_{l}^{(d)})$. Show that the loss decomposes into $d$ independent scalar problems:

$$
\mathcal{L}= \frac{1}{2}\sum_{\alpha=1}^{d} \left(s_{\alpha} - \prod_{l=1}^{L} w_{l}^{(\alpha)}\right)^{2}
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

When all $W_{l}$ are diagonal, the product $W = W_{L} \cdots W_{1}$ is also diagonal with entries $(W)_{\alpha\alpha}= \prod_{l=1}^{L} w_{l}^{(\alpha)}$. The teacher $M$ is diagonal with entries $s_{\alpha}$. Then:

$$
\mathcal{L}= \frac{1}{2}\|M - W\|_{F}^{2} = \frac{1}{2}\sum_{\alpha=1}^{d} (s_{\alpha} - (W)_{\alpha\alpha})^{2} = \frac{1}{2}\sum_{\alpha=1}^{d} \left(s_{\alpha} - \prod_{l=1}^{L} w_{l}^{(\alpha)}\right)^{2}
$$

Since the different modes $\alpha$ share no parameters, the loss decomposes into $d$ independent scalar problems. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.2 (Scalar critical points).** For a single scalar mode with target $s > 0$, find all first-order critical points of $\ell(w_{1}, w_{2}) = \frac{1}{2}(s - w_{1} w_{2})^{2}$ at depth $L = 2$. Show that the critical points are:

- The global minimum manifold: $w_{1} w_{2} = s$
- The origin: $w_{1} = w_{2} = 0$

Classify the origin as a saddle point by computing the Hessian $H$ of $\ell$ at $(0,0)$ and showing it has both positive and negative eigenvalues.

*Hint*: Write the gradient equations.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

For $L = 2$, the gradient equations are:

$$
\frac{\partial \ell}{\partial w_{1}}= -(s - w_{1} w_{2})\,w_{2} = 0, \qquad \frac{\partial \ell}{\partial w_{2}}= -(s - w_{1} w_{2})\,w_{1} = 0
$$

**Case 1**: $s - w_{1} w_{2} = 0$, i.e. $w_{1} w_{2} = s$. This is the global minimum manifold (a hyperbola $w_{2} = s/w_{1}$) with $\ell = 0$.

**Case 2**: If $s - w_{1} w_{2} \neq 0$, then the first equation requires $w_{2} = 0$ and the second requires $w_{1} = 0$. (For instance, if $w_{2} \neq 0$ and $w_{1} = 0$, the first equation gives $-s\,w_{2} = 0$, which contradicts $s > 0$ and $w_{2} \neq 0$.) So the only other critical point is $w_{1} = w_{2} = 0$.

The Hessian at $(0,0)$. We need the second derivatives of $\ell = \frac{1}{2}(s - w_{1} w_{2})^{2}$:

$$
\begin{aligned}\frac{\partial^{2} \ell}{\partial w_{1}^{2}}&= w_{2}^{2}, \qquad \frac{\partial^{2} \ell}{\partial w_{2}^{2}}= w_{1}^{2}, \\ \frac{\partial^{2} \ell}{\partial w_{1} \partial w_{2}}&= -(s - w_{1} w_{2}) + w_{1} w_{2} = 2w_{1} w_{2} - s\end{aligned}
$$

At $(0,0)$:

$$
H = \begin{pmatrix}0 & -s \\ -s & 0\end{pmatrix}
$$

The eigenvalues are $\pm s$. Since $s > 0$, $H$ has one positive and one negative eigenvalue. The origin is a **strict saddle point**. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.3 (Critical-point structure).** Achour et al. (Achour et al. 2024) show that every first-order critical point $\theta = (W_{1}, \ldots, W_{L})$ satisfies: there exists a subset $S \subseteq \{1, \ldots, d\}$ such that

$$
W = W_{L} \cdots W_{1} = P_{S}\, M
$$

where $P_{S} = U_{S} U_{S}^{\top}$ is the orthogonal projector onto the span of the left singular vectors $\{u_{\alpha}\}_{\alpha \in S}$ of $M$. For the diagonal case $M = \text{diag}(s_{1}, \ldots, s_{d})$, write the value of the loss at the critical point corresponding to $S = \{1, \ldots, r\}$ with $r < d$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

At the critical point $W = P_{S} M$ with $S = \{1, \ldots, r\}$, the student retains only the first $r$ modes: $W = \text{diag}(s_{1}, \ldots, s_{r}, 0, \ldots, 0)$. The loss is:

$$
\mathcal{L}= \frac{1}{2}\|M - P_{S} M\|_{F}^{2} = \frac{1}{2}\sum_{\alpha \notin S}s_{\alpha}^{2} = \frac{1}{2}\sum_{\alpha=r+1}^{d} s_{\alpha}^{2}
$$

This is strictly positive whenever $r < d$ (since all $s_{\alpha} > 0$), so these are not global minima. By the Hessian analysis (extending Exercise 3.2), the direction corresponding to "switching on" a missing mode $\alpha \notin S$ is a descent direction, making these critical points saddle points. All critical points with $|S| = d$ have $W = M$ and $\mathcal{L}= 0$: these are the global minima. Therefore there are **no spurious local minima** — every local minimum is global. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.4 (Symmetry of the global minima).** The group $GL_{h} := GL_{d_1}\times \cdots \times GL_{d_{L-1}}$ acts on the weights by:

$$
(W_{1}, \ldots, W_{L}) \mapsto (g_{1} W_{1},\; g_{2} W_{2} g_{1}^{-1},\; \ldots,\; W_{L} g_{L-1}^{-1})
$$

Verify that the student map $\mu(\theta) = W_{L} \cdots W_{1}$ is invariant under this action: $\mu(g \cdot \theta) = \mu(\theta)$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Under the group action:

$$
\mu(g \cdot \theta) = W_{L} g_{L-1}^{-1}\cdot g_{L-1}W_{L-1}g_{L-2}^{-1}\cdot \ldots \cdot g_{1} W_{1} = W_{L} W_{L-1}\cdots W_{1} = \mu(\theta)
$$

All $g_{l}$ and $g_{l}^{-1}$ factors cancel telescopically. This means every parameter point in the orbit $\mathcal{O}_{\theta} = GL_{h} \cdot \theta$ maps to the same student $W$. $\square$

For the dimension of the set of global minima, this invariance means the following. The global minima form the fiber $\mu^{-1}(M)$, which contains the entire orbit $GL_{h} \cdot \theta^{*}$ for any global minimizer $\theta^{*}$. The orbit has dimension $\sum_{l=1}^{L-1}d_{l}^{2}$ (the dimension of $GL_{h}$), so the set of global minima is a **continuous manifold of very high dimension** — far from being isolated points. $\square$

:::

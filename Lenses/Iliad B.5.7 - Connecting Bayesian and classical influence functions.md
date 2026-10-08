---
id: 'cbd53d83-4dbd-48cd-ab4d-565ab1dcd996'
title: "B.5.7 Connecting Bayesian and classical influence functions"
tldr: "Exercise 3.2: expand the Bayesian influence function around a minimum with a Laplace approximation and show the classical (damped) influence function is its leading term."
summary_for_tutor: "Section 3.2 of Iliad worksheet B.5 Data Attribution: Exercise 3.2 (a)-(e) with collapsed solutions: Laplace approximation of the posterior, Taylor expansion of the covariance, the leading (1,1) term giving the classical IF, the (2,2) correction via Isserlis' theorem, and the localized version giving the damped IF with gamma as lambda. Ends with a remark that the classical IF is the leading term of the local BIF. Keep Delta w, H, g_phi, g_i. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 3.2 Exercise: Connecting Bayesian and classical influence functions

As we have seen in the SLT day, tools involving the Hessian are usually a low-order approximation of an expansion. This is also true for influence functions: In the non-degenerate case the classical IF is the leading-order term of the BIF under a Laplace approximation. The following exercise makes this precise by computing a power series expansion of the BIF covariance and identifying the classical IF as the leading-order term. The argument follows Kreer et al. 2026, Appendix A.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.2 (Power series expansion of Bayesian influence functions).** Let $$w^{*}$$ be a local minimum of the training loss $$L(w) = \sum_{i=1}^{n} L(w,z_{i})$$ with positive-definite Hessian $$H = \nabla_{w}^{2} L(w^{*})$$. Write $$\Delta w = w - w^{*}$$, and abbreviate $$g_{\phi} = \nabla_{w}\phi(w^{*})$$, $$H_{\phi} = \nabla_{w}^{2}\phi(w^{*})$$ for the gradient and Hessian of the observable, and $$g_{i} = \nabla_{w} L(w^{*},z_{i})$$, $$H_{i} = \nabla_{w}^{2} L(w^{*},z_{i})$$ for the per-sample loss.

**(a)** **(Laplace approximation.)** Consider the posterior $$p(w\mid\mathcal{D}) \propto e^{-L(w)}\,\varphi(w)$$. Taylor-expand $$L(w)$$ to second order around $$w^{*}$$, using the fact that $$\nabla L(w^{*}) = 0$$ at a minimum. Argue that for large $$n$$ the quadratic term in $$L$$ dominates the prior $$\varphi$$, and conclude that

$$
p(w\mid\mathcal{D}) \;\approx\; \mathcal{N}(w^{*},\;H^{-1}).
$$

Under this approximation, $$\Delta w \sim \mathcal{N}(0, H^{-1})$$. (This is called the *Laplace approximation*; the Bernstein–von Mises theorem guarantees it is asymptotically exact for non-singular models.)

**(b)** **(Taylor expansion of the covariance.)** Expand $$\phi(w)$$ and $$L(w,z_{i})$$ in Taylor series around $$w^{*}$$:

$$
\begin{aligned}\phi(w)&= \phi(w^{*}) + g_{\phi}^{\top}\Delta w + \tfrac{1}{2}\Delta w^{\top} H_{\phi}\,\Delta w + \cdots, \\ L(w,z_{i})&= L(w^{*},z_{i}) + g_{i}^{\top}\Delta w + \tfrac{1}{2}\Delta w^{\top} H_{i}\,\Delta w + \cdots.\end{aligned}
$$

Using the fact that constant terms drop out of covariances and that $$\mathrm{Cov}(X,Y) = \sum_{k,m\ge 1}\mathrm{Cov}(T_{k}[\phi],\,T_{m}[L_{i}])$$ where $$T_{k}[f]$$ denotes the $$k$$-th order term in the Taylor expansion of $$f$$, show that the BIF decomposes as

$$
\mathrm{BIF}(z_{i},\phi) = -\sum_{\substack{k,m\ge 1\\k+m\text{ even}}}\mathrm{Cov}_{\mathcal{N}}\bigl(T_{k}[\phi],\;T_{m}[L_{i}]\bigr).
$$

Why do terms with $$k+m$$ odd vanish?

**(c)** **(Leading order: classical IF.)** Compute the $$(k,m) = (1,1)$$ term:

$$
\mathrm{Cov}_{\mathcal{N}}\bigl(g_{\phi}^{\top}\Delta w,\;g_{i}^{\top}\Delta w\bigr) \;=\; g_{\phi}^{\top} H^{-1}g_{i}.
$$

Conclude that $$-g_{\phi}^{\top} H^{-1}g_{i} = -\nabla_{w}\phi(w^{*})^{\top} H^{-1}\nabla_{w} L(w^{*},z_{i})$$ is the classical influence function $$\mathcal{I}(z_{i},\phi)$$ from Definition 2.2. This is the leading-order term of the BIF.

**(d)** **(Second-order correction.)** Compute the $$(k,m) = (2,2)$$ term using Isserlis' theorem (the Gaussian moment identity $${\mathbb{E}}[\Delta w_{a}\Delta w_{b}\Delta w_{c}\Delta w_{d}] = \Sigma_{ab}\Sigma_{cd}+ \Sigma_{ac}\Sigma_{bd}+ \Sigma_{ad}\Sigma_{bc}$$ with $$\Sigma = H^{-1}$$). Show that

$$
\mathrm{Cov}_{\mathcal{N}}\!\left(\tfrac{1}{2}\Delta w^{\top} H_{\phi}\,\Delta w,\;\tfrac{1}{2}\Delta w^{\top} H_{i}\,\Delta w\right) = \tfrac{1}{2}\,{\operatorname{tr}}\bigl(H_{\phi}\,H^{-1}\,H_{i}\,H^{-1}\bigr).
$$

This correction involves the *Hessians* of the observable and per-sample loss. It captures second-order curvature interactions that the classical IF misses entirely. In the linear regression setting of Example 3.2, why does this correction vanish?

**(e)** **(Localized version: damped IF.)** Now consider the local BIF of Equation 11 with localization strength $$\gamma$$. The localized posterior is approximately $$\mathcal{N}(w^{*},\,(H+\gamma I)^{-1})$$. Repeat the leading-order computation of part (c) to show that

$$
\mathrm{BIF}_{\gamma}(z_{i},\phi) \;\approx\; -\,\nabla_{w}\phi(w^{*})^{\top}\,(H + \gamma I)^{-1}\,\nabla_{w} L(w^{*},z_{i}).
$$

This is precisely the damped influence function of Equation 6, with the localization strength $$\gamma$$ playing the role of the damping parameter $$\lambda$$. The local BIF is thus a natural, higher-order generalization of the damped IF: it agrees at leading order and includes all the corrections from parts (b)–(d) with $$H^{-1}$$ replaced by $$(H + \gamma I)^{-1}$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* The log-posterior is $$\log p(w\mid\mathcal{D}) = -L(w) + \log\varphi(w) + \mathrm{const}$$. Taylor-expanding $$L(w)$$ around the minimum $$w^{*}$$:

$$
L(w) = L(w^{*}) + \underbrace{\nabla L(w^*)^\top}_{=\,0}\Delta w + \tfrac{1}{2}\,\Delta w^{\top} H\,\Delta w + O(\|\Delta w\|^{3}).
$$

The linear term vanishes because $$w^{*}$$ is a critical point. Substituting into $$\log p$$:

$$
\log p(w\mid\mathcal{D}) \approx -L(w^{*}) - \tfrac{1}{2}\,\Delta w^{\top} H\,\Delta w + \log\varphi(w) + \mathrm{const}.
$$

Since $$L = \sum_{i=1}^{n} L_{i}$$, the Hessian $$H = \sum_{i} \nabla^{2} L_{i}$$ scales as $$O(n)$$, while the prior contributes $$O(1)$$ to the log-density. For large $$n$$ the quadratic term dominates, giving $$p(w\mid\mathcal{D}) \approx \mathcal{N}(w^{*},\,H^{-1})$$. This is the Laplace approximation. (The Bernstein–von Mises theorem makes this rigorous: under regularity, the posterior converges to this Gaussian in total variation as $$n\to\infty$$.)

*(b)* Since $$\mathrm{Cov}(X+c,Y) = \mathrm{Cov}(X,Y)$$ for any constant $$c$$, the constant terms $$\phi(w^{*})$$ and $$L(w^{*},z_{i})$$ drop out. The covariance of the two Taylor series is bilinear, so it distributes over the sum of terms:

$$
\mathrm{Cov}(\phi,L_{i}) = \sum_{k\ge 1}\sum_{m\ge 1}\mathrm{Cov}(T_{k}[\phi],\,T_{m}[L_{i}]).
$$

Under $$\Delta w\sim\mathcal{N}(0,H^{-1})$$, $$T_{k}[\phi]$$ is a degree-$$k$$ polynomial in $$\Delta w$$. The covariance $$\mathrm{Cov}(T_{k},T_{m}) = {\mathbb{E}}[T_{k} T_{m}] - {\mathbb{E}}[T_{k}]{\mathbb{E}}[T_{m}]$$ involves moments of $$\Delta w$$ of degree $$k+m$$. For a centered Gaussian, odd moments vanish: $${\mathbb{E}}[\Delta w_{a_1}\cdots\Delta w_{a_\ell}] = 0$$ when $$\ell$$ is odd. If $$k+m$$ is odd, then all moments in $${\mathbb{E}}[T_{k} T_{m}]$$ and $${\mathbb{E}}[T_{k}]{\mathbb{E}}[T_{m}]$$ involve an odd total degree, so both vanish and $$\mathrm{Cov}(T_{k},T_{m})=0$$.

*(c)* $$T_{1}[\phi] = g_{\phi}^{\top}\Delta w$$ and $$T_{1}[L_{i}] = g_{i}^{\top}\Delta w$$ are linear in $$\Delta w$$. Their covariance is

$$
\mathrm{Cov}(g_{\phi}^{\top}\Delta w,\;g_{i}^{\top}\Delta w) = g_{\phi}^{\top}\,{\mathbb{E}}[\Delta w\,\Delta w^{\top}]\,g_{i} = g_{\phi}^{\top} H^{-1}g_{i}.
$$

Negating gives $$-g_{\phi}^{\top} H^{-1}g_{i} = -\nabla\phi(w^{*})^{\top} H^{-1}\nabla L(w^{*},z_{i})$$, which is the classical influence function $$\mathcal{I}(z_{i},\phi)$$ from Definition 2.2.

*(d)* Write $$Q_{\phi} = \tfrac{1}{2}\Delta w^{\top} H_{\phi}\,\Delta w$$ and $$Q_{i} = \tfrac{1}{2}\Delta w^{\top} H_{i}\,\Delta w$$. We need $$\mathrm{Cov}(Q_{\phi},Q_{i}) = {\mathbb{E}}[Q_{\phi} Q_{i}] - {\mathbb{E}}[Q_{\phi}]{\mathbb{E}}[Q_{i}]$$ with $$\Delta w\sim\mathcal{N}(0,\Sigma)$$, $$\Sigma=H^{-1}$$.

For the expectation: $${\mathbb{E}}[Q_{\phi}] = \tfrac{1}{2}{\operatorname{tr}}(H_{\phi}\Sigma)$$ and $${\mathbb{E}}[Q_{i}] = \tfrac{1}{2}{\operatorname{tr}}(H_{i}\Sigma)$$.

For the cross-moment: $${\mathbb{E}}[Q_{\phi} Q_{i}] = \tfrac{1}{4}\sum_{a,b,c,d}(H_{\phi})_{ab}(H_{i})_{cd}\,{\mathbb{E}}[\Delta w_{a}\Delta w_{b}\Delta w_{c}\Delta w_{d}]$$. By Isserlis' theorem:

$$
{\mathbb{E}}[\Delta w_{a}\Delta w_{b}\Delta w_{c}\Delta w_{d}] = \Sigma_{ab}\Sigma_{cd}+ \Sigma_{ac}\Sigma_{bd}+ \Sigma_{ad}\Sigma_{bc}.
$$

The first pairing gives $$\tfrac{1}{4}{\operatorname{tr}}(H_{\phi}\Sigma){\operatorname{tr}}(H_{i}\Sigma) = {\mathbb{E}}[Q_{\phi}]{\mathbb{E}}[Q_{i}]$$, which cancels in the covariance. The other two pairings each give $$\tfrac{1}{4}{\operatorname{tr}}(H_{\phi}\Sigma H_{i}\Sigma)$$ (by cyclicity of the trace and symmetry of $$H_{\phi}$$, $$H_{i}$$, and $$\Sigma$$). So

$$
\mathrm{Cov}(Q_{\phi},Q_{i}) = 2\cdot\tfrac{1}{4}{\operatorname{tr}}(H_{\phi}\Sigma H_{i}\Sigma) = \tfrac{1}{2}{\operatorname{tr}}(H_{\phi} H^{-1}H_{i} H^{-1}).
$$

In the linear regression setting with $$\phi(w) = w_{k}$$ (a coordinate function), $$H_{\phi} = \nabla^{2} w_{k} = 0$$: the observable is linear in $$w$$, so its Hessian vanishes and the entire $$(2,2)$$ correction is zero. This is why the BIF equals the (damped) IF exactly for linear regression — all corrections beyond leading order involve $$H_{\phi}$$ or higher derivatives of $$\phi$$, which vanish for a linear observable.

*(e)* The localized posterior of Equation 10 has effective Hessian $$H_{\mathrm{eff}}= H + \gamma I$$, so the Laplace approximation gives $$\Delta w\sim\mathcal{N}(0,(H+\gamma I)^{-1})$$. The leading-order $$(1,1)$$ computation from part (c) becomes

$$
\mathrm{BIF}_{\gamma}(z_{i},\phi) \approx -g_{\phi}^{\top}(H+\gamma I)^{-1}g_{i} = -\nabla\phi(w^{*})^{\top}(H+\gamma I)^{-1}\nabla L(w^{*},z_{i}),
$$

which is the damped IF of Equation 6 with $$\gamma$$ in the role of $$\lambda$$. The higher-order corrections from parts (b)–(d) carry through with $$H^{-1}$$ replaced by $$(H+\gamma I)^{-1}$$ throughout.

*(f)* Summary: For regular (non-singular) models, the posterior is approximately Gaussian (Bernstein–von Mises), the Taylor expansion converges, and the $$(1,1)$$ term dominates (it scales as $$O(1/n)$$ while higher terms scale as $$O(1/n^{2})$$ and beyond). The classical IF is a good approximation because it *is* the leading term. For singular models (neural networks), the posterior is concentrated on a positive-dimensional variety, not at an isolated point. The Laplace approximation fails: the Hessian has a large null space, the posterior is non-Gaussian, and the Taylor series does not converge around $$w^{*}$$. In this regime, the BIF — defined as an exact covariance under the true posterior — captures the full geometry, while the classical IF is at best the leading term of an expansion that does not converge. The BIF is the fundamental object; the IF is the Gaussian shadow it casts.

:::

:::callout {title="Note" tone="blue"}

**Remark.** We conclude that the classical (damped) IF is the leading term of the (local) BIF under a Laplace approximation. For non-singular models with enough data, the Laplace approximation converges and the higher-order terms are small. But for singular models (neural networks), the Laplace approximation fails, the posterior is not Gaussian, and the BIF captures geometry that the classical IF cannot see.

:::

---
id: 'b34cf751-eeb3-423e-bdb0-d11eebfcad4b'
title: "B.5.8 Influence functions as optimal linear transport"
tldr: "A long exercise showing influence functions are the optimal linear parameter shifts under a KL cost, including the degenerate case and a linear regression check."
summary_for_tutor: "Section 3.3 of Iliad worksheet B.5 Data Attribution: the setup with total loss and the KL-based cost of a parameter shift, then Exercise 3.3 (a)-(f) with collapsed solutions: KL in terms of energies, Taylor expansion at w*, IFs are optimal (Mahalanobis cost in the Hessian metric), the degenerate case with a singular Hessian, a linear regression check, and a comparison with Exercise 3.2. Ends with a remark on optimal transport maps. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 3.3 Long Exercise: Influence functions as optimal linear transport

The previous exercise showed that the classical IF is the leading-order term of the BIF under a Laplace approximation. We now take a different perspective, due to Mlodozeniec et al. 2025: instead of asking "what does the BIF reduce to?" we ask "what is the *best* way to shift the parameters to approximate the effect of a data perturbation?" The answer turns out to be: the influence function, and its optimality does not require the Laplace approximation to hold.

**Setup.**  Let $$L(w) = \sum_{i=1}^{n} L(w,z_{i})$$ denote the total training loss, and abbreviate $$L_{k}(w) := L(w,z_{k})$$ for the per-sample loss at example $$k$$. Define the *Boltzmann distributions* at inverse temperature $$\beta$$:

$$
\begin{aligned}p_{0}^{\beta}(w)&\propto e^{-\beta\,L(w)},&p_{\varepsilon}^{\beta}(w)&\propto e^{-\beta\bigl(L(w)\,-\,\varepsilon\,L_k(w)\bigr)},\end{aligned}
$$

so that $$p_{\varepsilon}^{\beta}$$ is the Boltzmann distribution after downweighting sample $$k$$ by $$\varepsilon$$. The low-temperature limit $$\beta\to\infty$$ concentrates $$p_{0}^{\beta}$$ on the set of global minima $$\mathcal{S}_{L} = \{w : L(w) = \inf L\}$$.

Now suppose we want to approximate the effect of the perturbation without resampling from $$p_{\varepsilon}^{\beta}$$. The simplest approach is to take each parameter $$w$$ drawn from $$p_{0}^{\beta}$$ and *shift* it to $$w + \varepsilon\,r(w)$$ for some smooth vector field $$r:{\mathbb{R}}^{d}\to{\mathbb{R}}^{d}$$. If $$r$$ is chosen well, the distribution of the shifted parameters should be close to $$p_{\varepsilon}^{\beta}$$. The question is: what is the optimal $$r$$?

To make this precise, we need to know the density of the shifted parameters. If $$w\sim p_{0}^{\beta}$$ and we set $$\tilde w = w + \varepsilon\,r(w)$$, then by the multivariate change-of-variables formula, $$\tilde w$$ has density

$$
q_{\varepsilon}(\tilde w) \;=\; \frac{p_{0}^{\beta}\bigl(\tilde w - \varepsilon\,r(\tilde w) + O(\varepsilon^{2})\bigr)}{\bigl|\det\bigl(I + \varepsilon\,\nabla r(w)\bigr)\bigr|}\,,
$$

where $$\nabla r$$ is the $$d\times d$$ Jacobian matrix of $$r$$ and the denominator is the usual volume-change factor.[^4] We measure how well $$q_{\varepsilon}$$ approximates $$p_{\varepsilon}^{\beta}$$ by the KL divergence $$D_{\mathrm{KL}}(q_{\varepsilon}\|p_{\varepsilon}^{\beta})$$. Rather than computing this directly, it is cleaner to write it as an expectation over the *original* distribution $$p_{0}^{\beta}$$:

$$
\begin{aligned}D_{\mathrm{KL}}(q_{\varepsilon}\|p_{\varepsilon}^{\beta}) \;=\; {\mathbb{E}}_{w\sim p_0^\beta}\!\Bigl[&\log p_{0}^{\beta}(w) - \log p_{\varepsilon}^{\beta}\bigl(w + \varepsilon r(w)\bigr) \\&- \log\bigl|\det\bigl(I + \varepsilon\nabla r(w)\bigr)\bigr|\Bigr].\end{aligned}
$$

This identity follows by substituting (12) into the definition of KL and changing variables back to $$w$$. We define the *asymptotic KL cost*

$$
\mathcal{F}(r,\varepsilon) \;:=\; \lim_{\beta\to\infty}\,\frac{1}{\beta}\,D_{\mathrm{KL}}(q_{\varepsilon}\|p_{\varepsilon}^{\beta}).
$$

The $$1/\beta$$ normalization kills the determinant term (which is $$O(1)$$) and the entropy terms, isolating the energy contribution (which is $$O(\beta)$$).

:::callout {title="Exercise" tone="amber"}
**Exercise 3.3 (Influence functions as optimal parameter shifts).** Let $$w^{*}$$ be a non-degenerate minimum of $$L$$ with positive-definite Hessian $$H = \nabla^{2} L(w^{*})$$. In this exercise we work at the unique minimum, so the $$\beta\to\infty$$ limit simply evaluates everything at $$w^{*}$$.

**(a)** **(KL in terms of energies.)** Starting from (13), substitute $$p_{0}^{\beta}(w) = e^{-\beta L(w)}/Z(\beta,0)$$ and $$p_{\varepsilon}^{\beta}(w) = e^{-\beta(L(w)-\varepsilon L_k(w))}/Z(\beta,\varepsilon)$$, and show that

$$
\begin{aligned}\frac{1}{\beta}\,D_{\mathrm{KL}}\;=\;&{\mathbb{E}}_{p_0^\beta}\!\bigl[L(w + \varepsilon r) - \varepsilon\,L_{k}(w + \varepsilon r) - L(w)\bigr] \\&+\; \frac{1}{\beta}\log\frac{Z(\beta,\varepsilon)}{Z(\beta,0)}\;-\; \frac{1}{\beta}\,{\mathbb{E}}_{p_0^\beta}\!\bigl[\log|\det(I + \varepsilon\nabla r)|\bigr],\end{aligned}
$$

where $$Z(\beta,\varepsilon) = \int e^{-\beta(L(w)-\varepsilon L_k(w))}\,dw$$. Explain why the last two terms vanish in the $$\beta\to\infty$$ limit. *Hint:* $$\log|\det(I+\varepsilon\nabla r)| = O(1)$$, and by Laplace's method $$\tfrac{1}{\beta}\log Z(\beta,\varepsilon) \to -\inf_{w}[L(w) - \varepsilon L_{k}(w)]$$.

**(b)** **(Taylor expansion at $$w^{*}$$.)** Since the expectation under $$p_{0}^{\beta}$$ concentrates at $$w^{*}$$ as $$\beta\to\infty$$, expand $$L(w^{*} + \varepsilon r)$$ and $$\varepsilon\,L_{k}(w^{*} + \varepsilon r)$$ using $$\nabla L(w^{*}) = 0$$:

$$
\begin{aligned}L(w^{*} + \varepsilon r)&= L(w^{*}) + \tfrac{\varepsilon^2}{2}\,r^{\top} H\,r + O(\varepsilon^{3}), \\ \varepsilon\,L_{k}(w^{*} + \varepsilon r)&= \varepsilon\,L_{k}(w^{*}) + \varepsilon^{2}\,\nabla L_{k}(w^{*})^{\top} r + O(\varepsilon^{3}).\end{aligned}
$$

Similarly, show that $$\inf_{w}[L(w) - \varepsilon L_{k}(w)] = L(w^{*}) - \varepsilon\,L_{k}(w^{*}) - \tfrac{\varepsilon^2}{2}\,\nabla L_{k}^{\top} H^{-1}\nabla L_{k} + O(\varepsilon^{3})$$, by minimizing the Taylor expansion of $$L - \varepsilon L_{k}$$ around $$w^{*}$$. Combine everything to obtain

$$
\mathcal{F}(r,\varepsilon) \;=\; \frac{\varepsilon^{2}}{2}\,\bigl(r - H^{-1}\nabla L_{k}\bigr)^{\top} H\,\bigl(r - H^{-1}\nabla L_{k}\bigr) \;+\; O(\varepsilon^{3}).
$$

*Hint:* After substitution, the terms that do not depend on $$r$$ should assemble into $$\tfrac{\varepsilon^2}{2}\nabla L_{k}^{\top} H^{-1}\nabla L_{k}$$ and cancel with the partition-function contribution, leaving a perfect square.

**(c)** **(IFs are optimal.)** The cost (15) is a squared Mahalanobis distance (in the Hessian metric) between the shift $$r$$ and the influence function $$r_{\mathrm{IF}}:= H^{-1}\nabla L_{k}(w^{*})$$. Conclude that the IF minimizes $$\mathcal{F}$$ to $$O(\varepsilon^{2})$$ among *all* smooth shift maps $$w\mapsto w+\varepsilon r(w)$$, and that the minimum cost is $$O(\varepsilon^{3})$$.

State the result in words: *the influence function is the approximately KL-optimal way to shift the parameters of the unperturbed Boltzmann distribution to approximate the perturbed one.*

**(d)** **(Degenerate case.)** Now suppose $$w^{*}$$ lies on a minimum manifold $$\mathcal{S}_{L}$$ and $$H$$ is singular with null space $$N$$. Argue (without detailed proof) that:
- The cost (15) generalizes to $$\mathcal{F}(r,\varepsilon) = \tfrac{\varepsilon^2}{2}(r - H^{+}\nabla L_{k})^{\top} H\,(r - H^{+}\nabla L_{k}) + O(\varepsilon^{3})$$, where $$H^{+}$$ is the Moore–Penrose pseudoinverse.
- The minimizer is $$r = H^{+}\nabla L_{k} + r_{\mathrm{NS}}$$ for any $$r_{\mathrm{NS}}\in N$$: directions in the null space of $$H$$ have zero cost, because the Hessian assigns zero curvature to movement along the minimum manifold.
- The IF (with pseudoinverse) is therefore optimal for the directions that matter, but the component of the shift along the flat directions is unconstrained.

Connect this to the SLT perspective: for singular models, the minimum is a variety, and the IF tells you how to move *off* the variety but is silent about movement *along* it.

**(e)** **(Linear regression check.)** Specialize to the Bayesian linear regression setting of Example 3.2 with prior $$w\sim\mathcal{N}(0,\tau^{2}I)$$. The Boltzmann distribution at inverse temperature $$\beta = 1$$ is the Bayesian posterior $$\mathcal{N}(\mu,V)$$, which is already Gaussian, no need to take $$\beta\to\infty$$. A constant shift $$w\mapsto w + \varepsilon r$$ sends $$\mathcal{N}(\mu,V)$$ to $$\mathcal{N}(\mu + \varepsilon r,\,V)$$. The true perturbed posterior (downweighting $$z_{k}$$ by $$\varepsilon$$) has mean $$\mu + \varepsilon\,\mathrm{BIF}(z_{k},w) + O(\varepsilon^{2})$$ and covariance $$V + O(\varepsilon)$$. Using the KL formula for Gaussians with the same covariance, show that

$$
D_{\mathrm{KL}}\bigl(\mathcal{N}(\mu + \varepsilon r,\,V)\;\big\|\;\mathcal{N}(\mu + \varepsilon b,\,V)\bigr) \;=\; \frac{\varepsilon^{2}}{2}\,(r-b)^{\top} V^{-1}(r-b),
$$

which is minimized at $$r = b = \mathrm{BIF}(z_{k},w) = (A + \lambda I)^{-1}x_{k} r_{k}$$. Verify that this is consistent with (15): the "Hessian of the energy" (training loss plus prior) is $$V^{-1}= \sigma^{-2}A + \tau^{-2}I$$, and $$V^{-1}\cdot\mathrm{BIF}= \sigma^{-2}x_{k} r_{k} = \nabla_{w} L(w,z_{k})\big|_{w=\mu}$$.

**(f)** **(Comparison with Exercise 3.2.)** The Laplace expansion exercise and this exercise both relate the IF to the BIF, but they answer different questions:
- Exercise 3.2 is an *algebraic identity*: BIF $$=$$ IF $$+$$ higher-order corrections. It requires the Laplace approximation (hence non-singular $$H$$, Gaussian posterior) and tells you what happens when you truncate the BIF.
- This exercise is an *optimality result*: the IF shift minimizes the KL divergence between the shifted and true perturbed distributions. The $$\beta\to\infty$$ result (parts a–d) needs only mild regularity of $$\mathcal{L}$$ and works even for singular $$H$$ (via the pseudoinverse).

Summarize: the Laplace expansion tells you *what* the IF is (the leading Gaussian term of the BIF). The optimality perspective tells you *why* it works (it is the best first-order correction to the parameter distribution). The second viewpoint does not require the posterior to be Gaussian, which is why Mlodozeniec et al. 2025 argue that it provides a better explanation for the empirical success of IFs in deep learning.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* Using $$p_{0}^{\beta}(w) = e^{-\beta L(w)}/Z(\beta,0)$$ and $$p_{\varepsilon}^{\beta}(w) = e^{-\beta(L(w)-\varepsilon L_k(w))}/Z(\beta,\varepsilon)$$, substituting into (13) gives

$$
\begin{aligned}D_{\mathrm{KL}}(q_{\varepsilon} \| p_{\varepsilon}^{\beta})&= {\mathbb{E}}_{w\sim p_0^\beta}\!\bigl[\log p_{0}^{\beta}(w) - \log p_{\varepsilon}^{\beta}(w+\varepsilon r) - \log|\det(I+\varepsilon\nabla r)|\bigr] \\&= {\mathbb{E}}_{p_0^\beta}\bigl[-\beta L(w) - \log Z(\beta,0) + \beta(L(w+\varepsilon r) - \varepsilon L_{k}(w+\varepsilon r)) \\&\qquad\qquad + \log Z(\beta,\varepsilon) - \log|\det(I+\varepsilon\nabla r)|\bigr].\end{aligned}
$$

Dividing by $$\beta$$ and rearranging gives the claimed expression. As $$\beta\to\infty$$: (i) $$\frac{1}{\beta}\log|\det(I+\varepsilon\nabla r)| \to 0$$ since the log-determinant is $$O(1)$$ (bounded for smooth $$r$$ and small $$\varepsilon$$); (ii) by Laplace's method, $$\frac{1}{\beta}\log Z(\beta,\varepsilon) \to -\inf_{w}[L(w)-\varepsilon L_{k}(w)]$$, so $$\frac{1}{\beta}\log\frac{Z(\beta,\varepsilon)}{Z(\beta,0)}\to \inf L - \inf(L-\varepsilon L_{k})$$, which is a constant independent of $$r$$; (iii) the expectation concentrates on $$w^{*}$$.

*(b)* At $$w^{*}$$, $$\nabla L(w^{*})=0$$, so the Taylor expansion of $$L(w^{*}+\varepsilon r)$$ starts at the quadratic term: $$L(w^{*}) + \frac{\varepsilon^{2}}{2}r^{\top} Hr + O(\varepsilon^{3})$$. For $$\varepsilon L_{k}$$: $$\varepsilon L_{k}(w^{*}+\varepsilon r) = \varepsilon L_{k}(w^{*}) + \varepsilon^{2}\nabla L_{k}^{\top} r + O(\varepsilon^{3})$$. Combined:

$$
\begin{aligned}&L(w^{*}+\varepsilon r) - \varepsilon L_{k}(w^{*}+\varepsilon r) - L(w^{*}) \\&\qquad= -\varepsilon L_{k}(w^{*}) + \frac{\varepsilon^{2}}{2}r^{\top} Hr - \varepsilon^{2}\nabla L_{k}^{\top} r + O(\varepsilon^{3}).\end{aligned}
$$

For the infimum: expanding $$L(w^{*}+\delta)-\varepsilon L_{k}(w^{*}+\delta)$$ to second order in $$\delta$$ and minimizing, the optimal perturbation is $$\delta^{*} = \varepsilon H^{-1}\nabla L_{k}$$, giving

$$
\inf_{w}[L-\varepsilon L_{k}] = L(w^{*}) - \varepsilon L_{k}(w^{*}) - \frac{\varepsilon^{2}}{2}\nabla L_{k}^{\top} H^{-1}\nabla L_{k} + O(\varepsilon^{3}).
$$

So $$\inf L - \inf(L-\varepsilon L_{k}) = \varepsilon L_{k}(w^{*}) + \frac{\varepsilon^{2}}{2}\nabla L_{k}^{\top} H^{-1}\nabla L_{k} + O(\varepsilon^{3})$$.

Adding the two contributions:

$$
\begin{aligned}\mathcal{F}(r,\varepsilon)&= \frac{\varepsilon^{2}}{2}r^{\top} Hr - \varepsilon^{2}\nabla L_{k}^{\top} r + \frac{\varepsilon^{2}}{2}\nabla L_{k}^{\top} H^{-1}\nabla L_{k} + O(\varepsilon^{3}) \\&= \frac{\varepsilon^{2}}{2}\bigl(r^{\top} Hr - 2\nabla L_{k}^{\top} r + \nabla L_{k}^{\top} H^{-1}\nabla L_{k}\bigr) + O(\varepsilon^{3}).\end{aligned}
$$

Completing the square: $$r^{\top} Hr - 2\nabla L_{k}^{\top} r + \nabla L_{k}^{\top} H^{-1}\nabla L_{k} = (r - H^{-1}\nabla L_{k})^{\top} H(r - H^{-1}\nabla L_{k})$$, since expanding the right side gives $$r^{\top} Hr - 2\nabla L_{k}^{\top} H^{-1}\cdot Hr + \nabla L_{k}^{\top} H^{-1}HH^{-1}\nabla L_{k} = r^{\top} Hr - 2\nabla L_{k}^{\top} r + \nabla L_{k}^{\top} H^{-1}\nabla L_{k}$$.

*(c)* Since $$H$$ is positive definite, the squared Mahalanobis form $$(r-r_{\mathrm{IF}})^{\top} H(r-r_{\mathrm{IF}}) \ge 0$$ with equality iff $$r = r_{\mathrm{IF}}= H^{-1}\nabla L_{k}$$. At the minimum, $$\mathcal{F}(r_{\mathrm{IF}},\varepsilon) = O(\varepsilon^{3})$$: the IF shifts the distribution with only a *third-order* KL residual. Any other shift $$r\ne r_{\mathrm{IF}}$$ incurs a strictly positive $$O(\varepsilon^{2})$$ cost proportional to its Mahalanobis distance from the IF. The IF is the unique optimal shift among all smooth vector fields $$r$$, not just among constant maps.

*(d)* When $$H$$ is singular, the quadratic form $$r^{\top} Hr$$ is zero for $$r\in N = \mathrm{Null}(H)$$: movement in the null space has zero Hessian cost because the loss is flat along the minimum manifold. The pseudoinverse $$H^{+}$$ inverts only the non-degenerate directions, and the completed square becomes $$(r - H^{+}\nabla L_{k})^{\top} H(r - H^{+}\nabla L_{k})$$. This vanishes whenever $$r - H^{+}\nabla L_{k} \in N$$, i.e., the minimizer is $$r = H^{+}\nabla L_{k} + r_{\mathrm{NS}}$$ for any $$r_{\mathrm{NS}}\in N$$.

Geometrically: the IF determines the optimal shift *off* the minimum manifold (perpendicular to $$\mathcal{S}_{L}$$), but movement *along* $$\mathcal{S}_{L}$$ is invisible to the energy at this order. In the SLT language: the degeneracy of the singular set means that many shifts are equally good at leading order — the IF picks one, but the null-space ambiguity is real.

*(e)* For linear regression with Gaussian prior, the posterior is $$\mathcal{N}(\mu,V)$$ with $$V^{-1}= \sigma^{-2}A + \tau^{-2}I$$. A constant shift $$w\mapsto w+\varepsilon r$$ sends $$\mathcal{N}(\mu,V)$$ to $$\mathcal{N}(\mu+\varepsilon r,V)$$. The true perturbed mean is $$\mu + \varepsilon b + O(\varepsilon^{2})$$ with $$b = \mathrm{BIF}(z_{k},w) = (A+\lambda I)^{-1}x_{k} r_{k}$$. For two Gaussians with the same covariance:

$$
D_{\mathrm{KL}}\bigl(\mathcal{N}(\mu+\varepsilon r,V)\|\mathcal{N}(\mu+\varepsilon b,V)\bigr) = \frac{\varepsilon^{2}}{2}(r-b)^{\top} V^{-1}(r-b).
$$

This is minimized at $$r = b = (A+\lambda I)^{-1}x_{k} r_{k}$$. To check consistency with (15): the "Hessian of the energy" in the Boltzmann distribution $$p \propto e^{-(\text{loss}+\text{prior})}$$ is $$H_{\mathrm{eff}}= \sigma^{-2}A + \tau^{-2}I = V^{-1}$$, and $$H_{\mathrm{eff}}^{-1}\nabla_{w} L(\mu,z_{k}) = V\cdot\sigma^{-2}x_{k} r_{k} = (A+\lambda I)^{-1}x_{k} r_{k} = \mathrm{BIF}$$. The general formula (15) reduces to $$\frac{\varepsilon^{2}}{2}(r-b)^{\top} V^{-1}(r-b)$$, exactly as computed directly.

*(f)* The two exercises are complementary:

- The Laplace expansion (Exercise 3.2) tells you *what* the IF is: the leading-order term of the BIF covariance under a Gaussian approximation to the posterior. The higher-order corrections (Hessian products, etc.) are visible but require the Laplace approximation to hold.
- The transport perspective (this exercise) tells you *why* the IF works even when the Laplace approximation fails: it minimizes the KL cost of transporting the parameter distribution, and this optimality holds in the $$\beta\to\infty$$ limit under mild regularity assumptions — no Gaussianity required. For singular models, the pseudoinverse handles the degenerate directions naturally (part d), and the result still says: the IF is the best you can do with a smooth first-order map.

This provides what Mlodozeniec et al. 2025 call a "distributional" justification for IFs in deep learning. The original justification (implicit function theorem, convexity) does not hold for neural networks. The Laplace/BIF justification (Exercise 3.2) requires Gaussianity of the posterior, which also fails. But the transport optimality result asks only for bounded derivatives and a well-defined minimum — conditions much closer to what actually holds in practice.

:::

:::callout {title="Note" tone="blue"}

**Remark (Optimal transport).** In the language of optimal transport, the map $$w\mapsto w+\varepsilon r(w)$$ is called a *transport map*, and the distribution of the shifted parameters is its *pushforward*, written $$T_{\varepsilon\#}p_{0}^{\beta}$$. The cost functional $$\mathcal{F}$$ is the asymptotic KL divergence between the pushforward and the target. Exercise 3.3 then says that the influence function is the *KL-optimal transport map* from the unperturbed to the perturbed Boltzmann distribution, at first order in $$\varepsilon$$. This is the perspective developed in Mlodozeniec et al. 2025, who prove a more general version (their Theorem 3) that applies to all smooth diffeomorphisms, not just maps of the form $$w+\varepsilon r(w)$$.

:::

[^4]: For small $$\varepsilon$$ the map $$w\mapsto w+\varepsilon r(w)$$ is a diffeomorphism, so the inverse is well-defined. The exact formula requires evaluating $$r$$ at the pre-image; the expression above is correct to the order we need.

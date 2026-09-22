---
id: '43a128f7-074f-44e6-8d33-27344d353f49'
title: "Route 2: Bayesian influence functions"
tldr: "Replace the single optimum with a posterior, and influence becomes a covariance. Its power series recovers the classical influence function as the leading term."
summary_for_tutor: "Day 5 Route 2 (Louis Jaburi's fast-track route 2): Subsection 2.1 and Section 3 of the Iliad B.5 worksheet. Core exercises 3.1 and 3.2 (the connection exercise in Subsection 3.2 that the route calls the conceptual payoff); 3.3, the long exercise, optional."
authors:
  - Louis Jaburi
source_url: https://github.com/iliad-team/iliad-intensive/tree/d2792cbf53158db2a5729ff7d431a53869b64624/tex/data-attribution
upstream_commit: 'd2792cbf53158db2a5729ff7d431a53869b64624'
reading_minutes: 70
tutor_minutes: 20
---

#### Text
content::
In the worksheet, read **Subsection 2.1** (the influence function formula), then **Section 3** (Bayesian Influence Functions) in full. Louis calls the connection exercise in Subsection 3.2 "the conceptual payoff".

#### Question: Open
id:: 51248780-c34a-4e49-a847-7938cffd58c3
content::
\## Exercise 3.1: The BIF is a covariance

**Exercise 3.1 (The BIF is a covariance).** Let $p_\beta(w\mid\mathcal{D})$ be the tempered posterior of (7) and write $p = p_{\mathbf{1}}$ for the unperturbed posterior. By differentiating $\mathbb{E}_{p_\beta}[\phi(w)] = \int \phi(w)\,p_\beta(w\mid\mathcal{D})\,dw$ with respect to $\beta_i$, show that

$$
\boxed{\;\mathrm{BIF}(z_i,\phi) \;=\; -\,\mathrm{Cov}_{w\sim p}\bigl(L(w,z_i),\;\phi(w)\bigr).\;}
\tag{8}
$$

*Hint:* Write $p_\beta \propto e^{-\sum_j \beta_j L(w,z_j)}\varphi(w)$ and differentiate the ratio $\int \phi\, p_\beta\,dw \,/\, \int p_\beta\,dw$ using the quotient rule. The key identity is $\partial_{\beta_i}\log Z(\beta) = -\mathbb{E}_{p_\beta}[L(w,z_i)]$.
feedback-instructions:: The student is on Day 5 (Iliad B.5, Data (Attribution) for Alignment, by Louis Jaburi) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (Route 2: the Bayesian perspective (Subsection 2.1, then Section 3)). They have attempted Exercise 3.1 (The BIF is a covariance) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START Write $Z(\beta) = \int \exp(-\sum_j \beta_j L(w,z_j))\,\varphi(w)\,dw$ for the normalizing constant, so that  $$ \mathbb{E}_{p_\beta}[\phi(w)] \;=\; \frac{1}{Z(\beta)}\int \phi(w)\,\exp\!\Bigl(-\sum_j \beta_j L(w,z_j)\Bigr)\,\varphi(w)\,dw. $$  Differentiating with respect to $\beta_i$ and applying the quotient rule:  $$ \begin{aligned}   \frac{\partial}{\partial\beta_i}\,\mathbb{E}_{p_\beta}[\phi] &\;=\; \frac{1}{Z}\int \phi(w)\bigl(-L(w,z_i)\bigr)\,e^{-\sum_j\beta_j L_j}\,\varphi\,dw \\   &\qquad\;-\; \frac{1}{Z^2}\cdot\frac{\partial Z}{\partial\beta_i}\int \phi\,e^{-\sum_j\beta_j L_j}\,\varphi\,dw. \end{aligned} $$  The first term is $-\mathbb{E}_{p_\beta}[\phi(w)\,L(w,z_i)]$. For the second, $\partial_{\beta_i}Z = -Z\,\mathbb{E}_{p_\beta}[L(w,z_i)]$, so it equals $+\mathbb{E}_{p_\beta}[L(w,z_i)]\,\mathbb{E}_{p_\beta}[\phi(w)]$. Evaluating at $\beta=\mathbf{1}$:  $$ \mathrm{BIF}(z_i,\phi) = -\mathbb{E}_p[\phi\cdot L_i] + \mathbb{E}_p[\phi]\,\mathbb{E}_p[L_i] = -\mathrm{Cov}_{w\sim p}(L(w,z_i),\,\phi(w)). $$  Structurally: in the classical IF, the "correlation" between $L_i$ and $\phi$ is mediated by the inverse Hessian acting on their gradients at a point; in the BIF it is mediated by the full posterior distribution. The inverse Hessian is how a Gaussian posterior would produce a covariance (as we will see in Exercise 3.2), so the BIF strictly generalizes the classical formula. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 552b1200-496e-4006-84b4-615c13df0462
content::
\## Exercise 3.2: Power series expansion of Bayesian influence functions

**Exercise 3.2 (Power series expansion of Bayesian influence functions).** Let $w^*$ be a local minimum of the training loss $L(w) = \sum_{i=1}^n L(w,z_i)$ with positive-definite Hessian $H = \nabla_w^2 L(w^*)$. Write $\Delta w = w - w^*$, and abbreviate $g_\phi = \nabla_w\phi(w^*)$, $H_\phi = \nabla_w^2\phi(w^*)$ for the gradient and Hessian of the observable, and $g_i = \nabla_w L(w^*,z_i)$, $H_i = \nabla_w^2 L(w^*,z_i)$ for the per-sample loss.

1.  **(Laplace approximation.)** Consider the posterior $p(w\mid\mathcal{D}) \propto e^{-L(w)}\,\varphi(w)$. Taylor-expand $L(w)$ to second order around $w^*$, using the fact that $\nabla L(w^*) = 0$ at a minimum. Argue that for large $n$ the quadratic term in $L$ dominates the prior $\varphi$, and conclude that

$$
p(w\mid\mathcal{D}) \;\approx\; \mathcal{N}(w^*,\;H^{-1}).
$$

Under this approximation, $\Delta w \sim \mathcal{N}(0, H^{-1})$. (This is called the *Laplace approximation*; the Bernstein--von Mises theorem guarantees it is asymptotically exact for non-singular models.)

2.  **(Taylor expansion of the covariance.)** Expand $\phi(w)$ and $L(w,z_i)$ in Taylor series around $w^*$:

$$
\begin{aligned}
        \phi(w) &= \phi(w^*) + g_\phi^\top\Delta w + \tfrac{1}{2}\Delta w^\top H_\phi\,\Delta w + \cdots, \\
        L(w,z_i) &= L(w^*,z_i) + g_i^\top\Delta w + \tfrac{1}{2}\Delta w^\top H_i\,\Delta w + \cdots.
    \end{aligned}
$$

Using the fact that constant terms drop out of covariances and that $\mathrm{Cov}(X,Y) = \sum_{k,m\ge 1}\mathrm{Cov}(T_k[\phi],\,T_m[L_i])$ where $T_k[f]$ denotes the $k$-th order term in the Taylor expansion of $f$, show that the BIF decomposes as

$$
\mathrm{BIF}(z_i,\phi) = -\sum_{\substack{k,m\ge 1\\k+m\text{ even}}} \mathrm{Cov}_{\mathcal{N}}\bigl(T_k[\phi],\;T_m[L_i]\bigr).
$$

Why do terms with $k+m$ odd vanish?

3.  **(Leading order: classical IF.)** Compute the $(k,m) = (1,1)$ term:

$$
\mathrm{Cov}_{\mathcal{N}}\bigl(g_\phi^\top\Delta w,\;g_i^\top\Delta w\bigr) \;=\; g_\phi^\top H^{-1} g_i.
$$

Conclude that $-g_\phi^\top H^{-1}g_i = -\nabla_w\phi(w^*)^\top H^{-1}\nabla_w L(w^*,z_i)$ is the classical influence function $\mathcal{I}(z_i,\phi)$ from Definition 2.2. This is the leading-order term of the BIF.

4.  **(Second-order correction.)** Compute the $(k,m) = (2,2)$ term using Isserlis' theorem (the Gaussian moment identity $\mathbb{E}[\Delta w_a\Delta w_b\Delta w_c\Delta w_d] = \Sigma_{ab}\Sigma_{cd} + \Sigma_{ac}\Sigma_{bd} + \Sigma_{ad}\Sigma_{bc}$ with $\Sigma = H^{-1}$). Show that

$$
\mathrm{Cov}_{\mathcal{N}}\!\left(\tfrac{1}{2}\Delta w^\top H_\phi\,\Delta w,\;\tfrac{1}{2}\Delta w^\top H_i\,\Delta w\right) = \tfrac{1}{2}\,\operatorname{tr}\bigl(H_\phi\,H^{-1}\,H_i\,H^{-1}\bigr).
$$

This correction involves the *Hessians* of the observable and per-sample loss. It captures second-order curvature interactions that the classical IF misses entirely. In the linear regression setting of Example 3.2, why does this correction vanish?

5.  **(Localized version: damped IF.)** Now consider the local BIF of (10) with localization strength $\gamma$. The localized posterior is approximately $\mathcal{N}(w^*,\,(H+\gamma I)^{-1})$. Repeat the leading-order computation of part (c) to show that

$$
\mathrm{BIF}_\gamma(z_i,\phi) \;\approx\; -\,\nabla_w\phi(w^*)^\top\,(H + \gamma I)^{-1}\,\nabla_w L(w^*,z_i).
$$

This is precisely the damped influence function of (5), with the localization strength $\gamma$ playing the role of the damping parameter $\lambda$. The local BIF is thus a natural, higher-order generalization of the damped IF: it agrees at leading order and includes all the corrections from parts (b)--(d) with $H^{-1}$ replaced by $(H + \gamma I)^{-1}$.
feedback-instructions:: The student is on Day 5 (Iliad B.5, Data (Attribution) for Alignment, by Louis Jaburi) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (Route 2: the Bayesian perspective (Subsection 2.1, then Section 3)). They have attempted Exercise 3.2 (Power series expansion of Bayesian influence functions) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START *(a)* The log-posterior is $\log p(w\mid\mathcal{D}) = -L(w) + \log\varphi(w) + \mathrm{const}$. Taylor-expanding $L(w)$ around the minimum $w^*$:  $$ L(w) = L(w^*) + \underbrace{\nabla L(w^*)^\top}_{=\,0}\Delta w + \tfrac{1}{2}\,\Delta w^\top H\,\Delta w + O(\|\Delta w\|^3). $$  The linear term vanishes because $w^*$ is a critical point. Substituting into $\log p$:  $$ \log p(w\mid\mathcal{D}) \approx -L(w^*) - \tfrac{1}{2}\,\Delta w^\top H\,\Delta w + \log\varphi(w) + \mathrm{const}. $$  Since $L = \sum_{i=1}^n L_i$, the Hessian $H = \sum_i \nabla^2 L_i$ scales as $O(n)$, while the prior contributes $O(1)$ to the log-density. For large $n$ the quadratic term dominates, giving $p(w\mid\mathcal{D}) \approx \mathcal{N}(w^*,\,H^{-1})$. This is the Laplace approximation. (The Bernstein--von Mises theorem makes this rigorous: under regularity, the posterior converges to this Gaussian in total variation as $n\to\infty$.)  *(b)* Since $\mathrm{Cov}(X+c,Y) = \mathrm{Cov}(X,Y)$ for any constant $c$, the constant terms $\phi(w^*)$ and $L(w^*,z_i)$ drop out. The covariance of the two Taylor series is bilinear, so it distributes over the sum of terms:  $$ \mathrm{Cov}(\phi,L_i) = \sum_{k\ge 1}\sum_{m\ge 1}\mathrm{Cov}(T_k[\phi],\,T_m[L_i]). $$  Under $\Delta w\sim\mathcal{N}(0,H^{-1})$, $T_k[\phi]$ is a degree-$k$ polynomial in $\Delta w$. The covariance $\mathrm{Cov}(T_k,T_m) = \mathbb{E}[T_k T_m] - \mathbb{E}[T_k]\mathbb{E}[T_m]$ involves moments of $\Delta w$ of degree $k+m$. For a centered Gaussian, odd moments vanish: $\mathbb{E}[\Delta w_{a_1}\cdots\Delta w_{a_\ell}] = 0$ when $\ell$ is odd. If $k+m$ is odd, then all moments in $\mathbb{E}[T_k T_m]$ and $\mathbb{E}[T_k]\mathbb{E}[T_m]$ involve an odd total degree, so both vanish and $\mathrm{Cov}(T_k,T_m)=0$.  *(c)* $T_1[\phi] = g_\phi^\top\Delta w$ and $T_1[L_i] = g_i^\top\Delta w$ are linear in $\Delta w$. Their covariance is  $$ \mathrm{Cov}(g_\phi^\top\Delta w,\;g_i^\top\Delta w) = g_\phi^\top\,\mathbb{E}[\Delta w\,\Delta w^\top]\,g_i = g_\phi^\top H^{-1}g_i. $$  Negating gives $-g_\phi^\top H^{-1}g_i = -\nabla\phi(w^*)^\top H^{-1}\nabla L(w^*,z_i)$, which is the classical influence function $\mathcal{I}(z_i,\phi)$ from Definition 2.2.  *(d)* Write $Q_\phi = \tfrac12\Delta w^\top H_\phi\,\Delta w$ and $Q_i = \tfrac12\Delta w^\top H_i\,\Delta w$. We need $\mathrm{Cov}(Q_\phi,Q_i) = \mathbb{E}[Q_\phi Q_i] - \mathbb{E}[Q_\phi]\mathbb{E}[Q_i]$ with $\Delta w\sim\mathcal{N}(0,\Sigma)$, $\Sigma=H^{-1}$.  For the expectation: $\mathbb{E}[Q_\phi] = \tfrac12\operatorname{tr}(H_\phi\Sigma)$ and $\mathbb{E}[Q_i] = \tfrac12\operatorname{tr}(H_i\Sigma)$.  For the cross-moment: $\mathbb{E}[Q_\phi Q_i] = \tfrac14\sum_{a,b,c,d}(H_\phi)_{ab}(H_i)_{cd}\,\mathbb{E}[\Delta w_a\Delta w_b\Delta w_c\Delta w_d]$. By Isserlis' theorem:  $$ \mathbb{E}[\Delta w_a\Delta w_b\Delta w_c\Delta w_d] = \Sigma_{ab}\Sigma_{cd} + \Sigma_{ac}\Sigma_{bd} + \Sigma_{ad}\Sigma_{bc}. $$  The first pairing gives $\tfrac14\operatorname{tr}(H_\phi\Sigma)\operatorname{tr}(H_i\Sigma) = \mathbb{E}[Q_\phi]\mathbb{E}[Q_i]$, which cancels in the covariance. The other two pairings each give $\tfrac14\operatorname{tr}(H_\phi\Sigma H_i\Sigma)$ (by cyclicity of the trace and symmetry of $H_\phi$, $H_i$, and $\Sigma$). So  $$ \mathrm{Cov}(Q_\phi,Q_i) = 2\cdot\tfrac14\operatorname{tr}(H_\phi\Sigma H_i\Sigma) = \tfrac12\operatorname{tr}(H_\phi H^{-1}H_i H^{-1}). $$  In the linear regression setting with $\phi(w) = w_k$ (a coordinate function), $H_\phi = \nabla^2 w_k = 0$: the observable is linear in $w$, so its Hessian vanishes and the entire $(2,2)$ correction is zero. This is why the BIF equals the (damped) IF exactly for linear regression --- all corrections beyond leading order involve $H_\phi$ or higher derivatives of $\phi$, which vanish for a linear observable.  *(e)* The localized posterior of (9) has effective Hessian $H_{\mathrm{eff}} = H + \gamma I$, so the Laplace approximation gives $\Delta w\sim\mathcal{N}(0,(H+\gamma I)^{-1})$. The leading-order $(1,1)$ computation from part (c) becomes  $$ \mathrm{BIF}_\gamma(z_i,\phi) \approx -g_\phi^\top(H+\gamma I)^{-1}g_i = -\nabla\phi(w^*)^\top(H+\gamma I)^{-1}\nabla L(w^*,z_i), $$  which is the damped IF of (5) with $\gamma$ in the role of $\lambda$. The higher-order corrections from parts (b)--(d) carry through with $H^{-1}$ replaced by $(H+\gamma I)^{-1}$ throughout.  *(f)* Summary: For regular (non-singular) models, the posterior is approximately Gaussian (Bernstein--von Mises), the Taylor expansion converges, and the $(1,1)$ term dominates (it scales as $O(1/n)$ while higher terms scale as $O(1/n^2)$ and beyond). The classical IF is a good approximation because it *is* the leading term. For singular models (neural networks), the posterior is concentrated on a positive-dimensional variety, not at an isolated point. The Laplace approximation fails: the Hessian has a large null space, the posterior is non-Gaussian, and the Taylor series does not converge around $w^*$. In this regime, the BIF --- defined as an exact covariance under the true posterior --- captures the full geometry, while the classical IF is at best the leading term of an expansion that does not converge. The BIF is the fundamental object; the IF is the Gaussian shadow it casts. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".

#### Question: Open
id:: 9d283207-20a7-4b56-9713-4cfdf432fd96
content::
\## Exercise 3.3: Influence functions as optimal parameter shifts (optional)

**Exercise 3.3 (Influence functions as optimal parameter shifts).** Let $w^*$ be a non-degenerate minimum of $L$ with positive-definite Hessian $H = \nabla^2 L(w^*)$. In this exercise we work at the unique minimum, so the $\beta\to\infty$ limit simply evaluates everything at $w^*$.

1.  **(KL in terms of energies.)** Starting from (12), substitute $p_0^\beta(w) = e^{-\beta L(w)}/Z(\beta,0)$ and $p_\varepsilon^\beta(w) = e^{-\beta(L(w)-\varepsilon L_k(w))}/Z(\beta,\varepsilon)$, and show that

$$
\begin{aligned}
        \frac{1}{\beta}\,D_{\mathrm{KL}} \;=\; &\mathbb{E}_{p_0^\beta}\!\bigl[L(w + \varepsilon r) - \varepsilon\,L_k(w + \varepsilon r) - L(w)\bigr] \\
        &+\; \frac{1}{\beta}\log\frac{Z(\beta,\varepsilon)}{Z(\beta,0)} \;-\; \frac{1}{\beta}\,\mathbb{E}_{p_0^\beta}\!\bigl[\log|\det(I + \varepsilon\nabla r)|\bigr],
    \end{aligned}
$$

where $Z(\beta,\varepsilon) = \int e^{-\beta(L(w)-\varepsilon L_k(w))}\,dw$. Explain why the last two terms vanish in the $\beta\to\infty$ limit. *Hint:* $\log|\det(I+\varepsilon\nabla r)| = O(1)$, and by Laplace's method $\tfrac{1}{\beta}\log Z(\beta,\varepsilon) \to -\inf_w[L(w) - \varepsilon L_k(w)]$.

2.  **(Taylor expansion at $w^*$.)** Since the expectation under $p_0^\beta$ concentrates at $w^*$ as $\beta\to\infty$, expand $L(w^* + \varepsilon r)$ and $\varepsilon\,L_k(w^* + \varepsilon r)$ using $\nabla L(w^*) = 0$:

$$
\begin{aligned}
        L(w^* + \varepsilon r) &= L(w^*) + \tfrac{\varepsilon^2}{2}\,r^\top H\,r + O(\varepsilon^3), \\
        \varepsilon\,L_k(w^* + \varepsilon r) &= \varepsilon\,L_k(w^*) + \varepsilon^2\,\nabla L_k(w^*)^\top r + O(\varepsilon^3).
    \end{aligned}
$$

Similarly, show that $\inf_w[L(w) - \varepsilon L_k(w)] = L(w^*) - \varepsilon\,L_k(w^*) - \tfrac{\varepsilon^2}{2}\,\nabla L_k^\top H^{-1}\nabla L_k + O(\varepsilon^3)$, by minimizing the Taylor expansion of $L - \varepsilon L_k$ around $w^*$. Combine everything to obtain

$$
\mathcal{F}(r,\varepsilon) \;=\; \frac{\varepsilon^2}{2}\,\bigl(r - H^{-1}\nabla L_k\bigr)^\top H\,\bigl(r - H^{-1}\nabla L_k\bigr) \;+\; O(\varepsilon^3).
      \tag{14}
$$

*Hint:* After substitution, the terms that do not depend on $r$ should assemble into $\tfrac{\varepsilon^2}{2}\nabla L_k^\top H^{-1}\nabla L_k$ and cancel with the partition-function contribution, leaving a perfect square.

3.  **(IFs are optimal.)** The cost (14) is a squared Mahalanobis distance (in the Hessian metric) between the shift $r$ and the influence function $r_{\mathrm{IF}} := H^{-1}\nabla L_k(w^*)$. Conclude that the IF minimizes $\mathcal{F}$ to $O(\varepsilon^2)$ among *all* smooth shift maps $w\mapsto w+\varepsilon r(w)$, and that the minimum cost is $O(\varepsilon^3)$.

    State the result in words: *the influence function is the approximately KL-optimal way to shift the parameters of the unperturbed Boltzmann distribution to approximate the perturbed one.*

4.  **(Degenerate case.)** Now suppose $w^*$ lies on a minimum manifold $\mathcal{S}_L$ and $H$ is singular with null space $N$. Argue (without detailed proof) that:

    -   The cost (14) generalizes to $\mathcal{F}(r,\varepsilon) = \tfrac{\varepsilon^2}{2}(r - H^+\nabla L_k)^\top H\,(r - H^+\nabla L_k) + O(\varepsilon^3)$, where $H^+$ is the Moore--Penrose pseudoinverse.

    -   The minimizer is $r = H^+\nabla L_k + r_{\mathrm{NS}}$ for any $r_{\mathrm{NS}}\in N$: directions in the null space of $H$ have zero cost, because the Hessian assigns zero curvature to movement along the minimum manifold.

    -   The IF (with pseudoinverse) is therefore optimal for the directions that matter, but the component of the shift along the flat directions is unconstrained.

    Connect this to the SLT perspective: for singular models, the minimum is a variety, and the IF tells you how to move *off* the variety but is silent about movement *along* it.

5.  **(Linear regression check.)** Specialize to the Bayesian linear regression setting of Example 3.2 with prior $w\sim\mathcal{N}(0,\tau^2I)$. The Boltzmann distribution at inverse temperature $\beta = 1$ is the Bayesian posterior $\mathcal{N}(\mu,V)$, which is already Gaussian, no need to take $\beta\to\infty$. A constant shift $w\mapsto w + \varepsilon r$ sends $\mathcal{N}(\mu,V)$ to $\mathcal{N}(\mu + \varepsilon r,\,V)$. The true perturbed posterior (downweighting $z_k$ by $\varepsilon$) has mean $\mu + \varepsilon\,\mathrm{BIF}(z_k,w) + O(\varepsilon^2)$ and covariance $V + O(\varepsilon)$. Using the KL formula for Gaussians with the same covariance, show that

$$
D_{\mathrm{KL}}\bigl(\mathcal{N}(\mu + \varepsilon r,\,V)\;\big\|\;\mathcal{N}(\mu + \varepsilon b,\,V)\bigr) \;=\; \frac{\varepsilon^2}{2}\,(r-b)^\top V^{-1}(r-b),
$$

which is minimized at $r = b = \mathrm{BIF}(z_k,w) = (A + \lambda I)^{-1}x_k r_k$. Verify that this is consistent with (14): the "Hessian of the energy" (training loss plus prior) is $V^{-1} = \sigma^{-2}A + \tau^{-2}I$, and $V^{-1}\cdot\mathrm{BIF} = \sigma^{-2}x_k r_k = \nabla_w L(w,z_k)\big|_{w=\mu}$.

6.  **(Comparison with Exercise 3.2.)** The Laplace expansion exercise and this exercise both relate the IF to the BIF, but they answer different questions:

    -   Exercise 3.2 is an *algebraic identity*: BIF $=$ IF $+$ higher-order corrections. It requires the Laplace approximation (hence non-singular $H$, Gaussian posterior) and tells you what happens when you truncate the BIF.

    -   This exercise is an *optimality result*: the IF shift minimizes the KL divergence between the shifted and true perturbed distributions. The $\beta\to\infty$ result (parts a--d) needs only mild regularity of $\mathcal{L}$ and works even for singular $H$ (via the pseudoinverse).

    Summarize: the Laplace expansion tells you *what* the IF is (the leading Gaussian term of the BIF). The optimality perspective tells you *why* it works (it is the best first-order correction to the parameter distribution). The second viewpoint does not require the posterior to be Gaussian, which is why Mlodozeniec et al. (2025) argue that it provides a better explanation for the empirical success of IFs in deep learning.
optional:: true
feedback-instructions:: The student is on Day 5 (Iliad B.5, Data (Attribution) for Alignment, by Louis Jaburi) of a one-week online course built from the Iliad Intensive, working through the authors' fast-track route (Route 2: the Bayesian perspective (Subsection 2.1, then Section 3)). They have attempted Exercise 3.3 (Influence functions as optimal parameter shifts) from the worksheet and typed their working. The official solution from the worksheet follows between the markers. It is also available to the student in the worksheet, collapsed, so it is not secret, but your job is to help them find their own error first, not to replace their attempt with it. OFFICIAL SOLUTION START *(a)* Using $p_0^\beta(w) = e^{-\beta L(w)}/Z(\beta,0)$ and $p_\varepsilon^\beta(w) = e^{-\beta(L(w)-\varepsilon L_k(w))}/Z(\beta,\varepsilon)$, substituting into (12) gives  $$ \begin{aligned}   D_{\mathrm{KL}}(q_\varepsilon \| p_\varepsilon^\beta)   &= \mathbb{E}_{w\sim p_0^\beta}\!\bigl[\log p_0^\beta(w) - \log p_\varepsilon^\beta(w+\varepsilon r) - \log|\det(I+\varepsilon\nabla r)|\bigr] \\   &= \mathbb{E}_{p_0^\beta}\bigl[-\beta L(w) - \log Z(\beta,0) + \beta(L(w+\varepsilon r) - \varepsilon L_k(w+\varepsilon r)) \\   &\qquad\qquad + \log Z(\beta,\varepsilon) - \log|\det(I+\varepsilon\nabla r)|\bigr]. \end{aligned} $$  Dividing by $\beta$ and rearranging gives the claimed expression. As $\beta\to\infty$: (i) $\frac{1}{\beta}\log|\det(I+\varepsilon\nabla r)| \to 0$ since the log-determinant is $O(1)$ (bounded for smooth $r$ and small $\varepsilon$); (ii) by Laplace's method, $\frac{1}{\beta}\log Z(\beta,\varepsilon) \to -\inf_w[L(w)-\varepsilon L_k(w)]$, so $\frac{1}{\beta}\log\frac{Z(\beta,\varepsilon)}{Z(\beta,0)} \to \inf L - \inf(L-\varepsilon L_k)$, which is a constant independent of $r$; (iii) the expectation concentrates on $w^*$.  *(b)* At $w^*$, $\nabla L(w^*)=0$, so the Taylor expansion of $L(w^*+\varepsilon r)$ starts at the quadratic term: $L(w^*) + \frac{\varepsilon^2}{2}r^\top Hr + O(\varepsilon^3)$. For $\varepsilon L_k$: $\varepsilon L_k(w^*+\varepsilon r) = \varepsilon L_k(w^*) + \varepsilon^2\nabla L_k^\top r + O(\varepsilon^3)$. Combined:  $$ \begin{aligned}   &L(w^*+\varepsilon r) - \varepsilon L_k(w^*+\varepsilon r) - L(w^*) \\   &\qquad= -\varepsilon L_k(w^*) + \frac{\varepsilon^2}{2}r^\top Hr - \varepsilon^2\nabla L_k^\top r + O(\varepsilon^3). \end{aligned} $$  For the infimum: expanding $L(w^*+\delta)-\varepsilon L_k(w^*+\delta)$ to second order in $\delta$ and minimizing, the optimal perturbation is $\delta^* = \varepsilon H^{-1}\nabla L_k$, giving  $$ \inf_w[L-\varepsilon L_k] = L(w^*) - \varepsilon L_k(w^*) - \frac{\varepsilon^2}{2}\nabla L_k^\top H^{-1}\nabla L_k + O(\varepsilon^3). $$  So $\inf L - \inf(L-\varepsilon L_k) = \varepsilon L_k(w^*) + \frac{\varepsilon^2}{2}\nabla L_k^\top H^{-1}\nabla L_k + O(\varepsilon^3)$.  Adding the two contributions:  $$ \begin{aligned}   \mathcal{F}(r,\varepsilon) &= \frac{\varepsilon^2}{2}r^\top Hr - \varepsilon^2\nabla L_k^\top r + \frac{\varepsilon^2}{2}\nabla L_k^\top H^{-1}\nabla L_k + O(\varepsilon^3) \\   &= \frac{\varepsilon^2}{2}\bigl(r^\top Hr - 2\nabla L_k^\top r + \nabla L_k^\top H^{-1}\nabla L_k\bigr) + O(\varepsilon^3). \end{aligned} $$  Completing the square: $r^\top Hr - 2\nabla L_k^\top r + \nabla L_k^\top H^{-1}\nabla L_k = (r - H^{-1}\nabla L_k)^\top H(r - H^{-1}\nabla L_k)$, since expanding the right side gives $r^\top Hr - 2\nabla L_k^\top H^{-1}\cdot Hr + \nabla L_k^\top H^{-1}HH^{-1}\nabla L_k = r^\top Hr - 2\nabla L_k^\top r + \nabla L_k^\top H^{-1}\nabla L_k$.  *(c)* Since $H$ is positive definite, the squared Mahalanobis form $(r-r_{\mathrm{IF}})^\top H(r-r_{\mathrm{IF}}) \ge 0$ with equality iff $r = r_{\mathrm{IF}} = H^{-1}\nabla L_k$. At the minimum, $\mathcal{F}(r_{\mathrm{IF}},\varepsilon) = O(\varepsilon^3)$: the IF shifts the distribution with only a *third-order* KL residual. Any other shift $r\ne r_{\mathrm{IF}}$ incurs a strictly positive $O(\varepsilon^2)$ cost proportional to its Mahalanobis distance from the IF. The IF is the unique optimal shift among all smooth vector fields $r$, not just among constant maps.  *(d)* When $H$ is singular, the quadratic form $r^\top Hr$ is zero for $r\in N = \mathrm{Null}(H)$: movement in the null space has zero Hessian cost because the loss is flat along the minimum manifold. The pseudoinverse $H^+$ inverts only the non-degenerate directions, and the completed square becomes $(r - H^+\nabla L_k)^\top H(r - H^+\nabla L_k)$. This vanishes whenever $r - H^+\nabla L_k \in N$, i.e., the minimizer is $r = H^+\nabla L_k + r_{\mathrm{NS}}$ for any $r_{\mathrm{NS}}\in N$.  Geometrically: the IF determines the optimal shift *off* the minimum manifold (perpendicular to $\mathcal{S}_L$), but movement *along* $\mathcal{S}_L$ is invisible to the energy at this order. In the SLT language: the degeneracy of the singular set means that many shifts are equally good at leading order --- the IF picks one, but the null-space ambiguity is real.  *(e)* For linear regression with Gaussian prior, the posterior is $\mathcal{N}(\mu,V)$ with $V^{-1} = \sigma^{-2}A + \tau^{-2}I$. A constant shift $w\mapsto w+\varepsilon r$ sends $\mathcal{N}(\mu,V)$ to $\mathcal{N}(\mu+\varepsilon r,V)$. The true perturbed mean is $\mu + \varepsilon b + O(\varepsilon^2)$ with $b = \mathrm{BIF}(z_k,w) = (A+\lambda I)^{-1}x_k r_k$. For two Gaussians with the same covariance:  $$ D_{\mathrm{KL}}\bigl(\mathcal{N}(\mu+\varepsilon r,V)\|\mathcal{N}(\mu+\varepsilon b,V)\bigr) = \frac{\varepsilon^2}{2}(r-b)^\top V^{-1}(r-b). $$  This is minimized at $r = b = (A+\lambda I)^{-1}x_k r_k$. To check consistency with (14): the "Hessian of the energy" in the Boltzmann distribution $p \propto e^{-(\text{loss}+\text{prior})}$ is $H_{\mathrm{eff}} = \sigma^{-2}A + \tau^{-2}I = V^{-1}$, and $H_{\mathrm{eff}}^{-1}\nabla_w L(\mu,z_k) = V\cdot\sigma^{-2}x_k r_k = (A+\lambda I)^{-1}x_k r_k = \mathrm{BIF}$. The general formula (14) reduces to $\frac{\varepsilon^2}{2}(r-b)^\top V^{-1}(r-b)$, exactly as computed directly.  *(f)* The two exercises are complementary:  -   The Laplace expansion (Exercise 3.2) tells you *what* the IF is: the leading-order term of the BIF covariance under a Gaussian approximation to the posterior. The higher-order corrections (Hessian products, etc.) are visible but require the Laplace approximation to hold.  -   The transport perspective (this exercise) tells you *why* the IF works even when the Laplace approximation fails: it minimizes the KL cost of transporting the parameter distribution, and this optimality holds in the $\beta\to\infty$ limit under mild regularity assumptions --- no Gaussianity required. For singular models, the pseudoinverse handles the degenerate directions naturally (part d), and the result still says: the IF is the best you can do with a smooth first-order map.  This provides what Mlodozeniec et al. (2025) call a "distributional" justification for IFs in deep learning. The original justification (implicit function theorem, convexity) does not hold for neural networks. The Laplace/BIF justification (Exercise 3.2) requires Gaussianity of the posterior, which also fails. But the transport optimality result asks only for bounded derivatives and a well-defined minimum --- conditions much closer to what actually holds in practice. OFFICIAL SOLUTION END Reply in 80 to 200 words, short paragraphs. Use LaTeX between dollar signs for any maths. Procedure: (1) If the answer is correct and the key steps are present, say so plainly in one sentence and name the one idea from the solution that the exercise was built to teach, in one more sentence. (2) If a step is wrong, quote or point at the first wrong step, say what is wrong with it in one sentence, and ask a question that would let them repair it; do not write out the rest of the solution. (3) If a part is missing, say which part and ask them to attempt it. (4) If they only gave a final answer, ask for the step that justifies it. If the student says they are stuck or do not understand, do not repeat the exercise: give one concrete foothold (the relevant definition from the worksheet, or the first line of the solution, or a simpler special case). If their next message still does not attempt it, rephrase the exercise in different words. If they ask to see the solution, point them to the collapsed solution in the worksheet. There is no score. No "great", "excellent", "well done".


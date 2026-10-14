---
id: '3c014583-0ea9-4daa-8e49-d32b9604acb3'
title: "B.6.19 Kernel regression, ridge regression and linearized networks"
tldr: "Appendix B, second part: minimum-norm kernel regression, kernel ridge regression and its spectral filter, and linearized networks as kernel ridge regressors."
summary_for_tutor: "Appendix B.3-B.5 and the start of Appendix C of Iliad worksheet B.6 Physics of Deep Learning. Covers Lagrange-multiplier derivation of the minimum-norm interpolant, the kernel trick, ridge regression, the push-through identity, early stopping vs ridge as spectral filters, and linearized networks with tangent features and the NTK. Contains Exercises B.3, B.4, B.5 and B.6, with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Aleksander Czejdo
  - Tudor Dimofte
  - Brianna Grado-White
  - Charles Renshaw-Whitman
source_url: https://iliad-intensive.org/learning/qft/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### B.3 Kernel regression

Return to the overparametrized case $$P>n$$, and assume that $$\Psi$$ has full row rank $$n$$ (the generic situation), so that there is a $$(P-n)$$-dimensional affine family of exact interpolants $$\Psi\theta = Y$$. To choose one, we need a criterion that the loss does not provide. The standard choice is the interpolant of *minimum norm*,

$$
\theta_{*} := \underset{\Psi\theta = Y}{\mathrm{arg\,min}}\; |\theta|^{2}\,.
$$

This introduces a *second* implicit Euclidean metric — now $$\delta_{ij}$$ on parameter space $${\mathbb{R}}^{P}$$, the metric that also defines gradient descent in Section 4.1.1. (Appendix B.1 used $$\delta_{\mu\nu}$$ on the space $${\mathbb{R}}^{n}$$ of function values.) The two metrics play dual roles: the first decides how to fit when the data cannot be matched, the second decides which fit to choose when it can.

To solve (B.11), introduce Lagrange multipliers $$\alpha\in{\mathbb{R}}^{n}$$ for the $$n$$ constraints and extremize $$\frac{1}{2}|\theta|^{2} - \alpha\cdot(\Psi\theta - Y)$$. Stationarity in $$\theta$$ gives

$$
\theta_{*} = \Psi^{T}\alpha = \sum_{\mu=1}^{n} \alpha_{\mu}\,\psi(x^{\mu})\,.
$$

This is the key structural fact: however large $$P$$ is, the minimum-norm solution lies in the $$n$$-dimensional subspace of $${\mathbb{R}}^{P}$$ spanned by the feature vectors of the training inputs, and is described by $$n$$ numbers. (In the language of Section 4.2, $$\theta_{*}$$ lies in the row space of the Jacobian.) The constraint $$\Psi\theta_{*} = Y$$ then becomes $$\Psi\Psi^{T}\alpha = Y$$, an $$n\times n$$ linear system. Define the *kernel* and its *Gram matrix* on the training set,

$$
\begin{aligned}K(x,x')&:= \psi(x)\cdot\psi(x') = \sum_{i=1}^{P} \psi_{i}(x)\psi_{i}(x')\,, \\ \hat K^{\mu\nu}&:= K(x^{\mu},x^{\nu}) = (\Psi\Psi^{T})^{\mu\nu}\,.\end{aligned}
$$

The kernel is an inner product of feature vectors: a notion of *similarity* between inputs, fixed once $$\psi$$ is fixed, and involving no labels. The Gram matrix is symmetric and positive semidefinite, since $$c^{T}\hat K c = |\Psi^{T}c|^{2}\geq 0$$; it is positive definite exactly when $$\Psi$$ has full row rank, which we assumed. Then $$\alpha = \hat K^{-1}Y$$, and the prediction at an arbitrary input $$x$$ is

$$
f_{*}(x) = \theta_{*}\cdot\psi(x) = \sum_{\mu=1}^{n} \alpha_{\mu} K(x,x^{\mu}) = \sum_{\mu,\nu=1}^{n} K(x,x^{\mu})\,\hat K^{-1}_{\mu\nu}\,y^{\nu}\,.
$$

This is *kernel regression* (more precisely, kernel interpolation). The feature map has disappeared from both the fit and the prediction. To fit, one needs $$K$$ on pairs of training points; to predict, one needs $$K$$ between the test point and the training points; no feature vector is ever constructed. The prediction is a weighted sum of similarities to the training points, with weights $$\alpha$$ that depend on the labels — but the labels only reweight the training points, they never change which inputs $$K$$ considers similar.

Compare (B.14) with the late-time mean (4.38) of a lazily trained network: they are the same formula, with $$\hat K$$ in place of the NTK. This is no coincidence. For any model linear in its parameters the Jacobian is $$J=\Psi$$, so the NTK (4.10) is

$$
\Theta^{\mu\nu}= (JJ^{T})^{\mu\nu}= \hat K^{\mu\nu}\,,
$$

constant in time. Moreover, gradient flow finds the minimum-norm solution: $$\dot\theta = -\eta\,\Psi^{T}\Delta$$ always points along the row space of $$\Psi$$, so $$\theta(t)-\theta_{0}$$ stays in that $$n$$-dimensional subspace and converges to the interpolant nearest to $$\theta_{0}$$ — for $$\theta_{0} = 0$$, to $$\theta_{*}$$ (Exercise B.3(c)). This is the simplest instance of the *implicit bias* of gradient descent, and it is the Euclidean metric on parameter space entering through the back door: the flow is defined by $$\delta^{ij}$$, and so is the norm that it ends up minimizing.

**The kernel trick.**  There are two readings of (B.14). Read from the feature side, it rewrites a $$P\times P$$ problem as an $$n\times n$$ one. Read from the kernel side, it says the feature map is dispensable: any function $$K(x,x')$$ that arises as an inner product of features will do, whether or not one can write the features down. For $$x,z\in{\mathbb{R}}^{2}$$ and $$\psi(x) = (x_{1}^{2},\,\sqrt{2}\,x_{1}x_{2},\,x_{2}^{2})$$, one checks that $$\psi(x)\cdot\psi(z) = (x\cdot z)^{2}$$: a single dot product, squared, stands in for three features. In $$d$$ dimensions, $$K(x,z) = (x\cdot z)^{m}$$ costs $$O(d)$$ to evaluate and stands in for all $$\binom{d+m-1}{m}$$ monomials of degree $$m$$. The Gaussian kernel $$K(x,z) = e^{-|x-z|^2/2\sigma^2}$$ corresponds to an infinite-dimensional feature map that no one ever writes down. Conversely, any symmetric $$K$$ all of whose Gram matrices are positive semidefinite arises from some feature map (Mercer's theorem): the eigenfunctions of $$K$$, weighted by the square roots of its eigenvalues, furnish one (*cf.* Sections 3.3 and 4.6). This is a trade, not a free lunch. The feature route scales with $$P$$ and the kernel route with $$n$$; with many examples and few features, the explicit route is the cheap one.

:::callout {title="Exercise" tone="amber"}
**Exercise B.3 (Minimum-norm interpolation and the kernel).** **(a)** Carry out the Lagrange-multiplier computation leading to (B.12)–(B.14). Alternatively, use the singular value decomposition $$\Psi = USV^{T}$$ of Section 4.2 to show that the minimum-norm interpolant is $$\theta_{*} = \Psi^{T}(\Psi\Psi^{T})^{-1}Y$$, and write it in terms of $$U,S,V$$.

**(b)** Show that $$c^{T}\hat Kc = |\Psi^{T}c|^{2}\geq 0$$ for all $$c\in{\mathbb{R}}^{n}$$. Interpret a zero eigenvalue of $$\hat K$$ as a linear combination of training examples that vanishes in feature space. What does it take for $$\hat K$$ to be invertible?

**(c)** Show that under gradient flow $$\dot\theta = -\eta\,\Psi^{T}(\Psi\theta - Y)$$ the displacement $$\theta(t)-\theta_{0}$$ stays in the row space of $$\Psi$$ for all $$t$$; derive $$\Delta(t) = e^{-\eta t\hat K}\Delta(0)$$; and conclude that, for invertible $$\hat K$$, the flow converges to the interpolant closest to $$\theta_{0}$$. Derive (4.36) for this model, with $$\Theta = \hat K$$.

**(d)** Verify that $$\psi(x)\cdot\psi(z) = (x\cdot z)^{2}$$ for $$\psi(x) = (x_{1}^{2},\sqrt{2}\,x_{1}x_{2},x_{2}^{2})$$, and explain why the $$\sqrt{2}$$ is not decoration. Which feature map on $${\mathbb{R}}$$ produces the kernel $$(1+xz)^{2}$$ of Exercise B.2(d)? How many features does $$(x\cdot z)^{m}$$ on $${\mathbb{R}}^{d}$$ stand in for?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Stationarity of $$\frac{1}{2}|\theta|^{2}-\alpha\cdot(\Psi\theta-Y)$$ in $$\theta$$ gives $$\theta = \Psi^{T}\alpha$$; the constraint then reads $$\Psi\Psi^{T}\alpha = \hat K\alpha = Y$$, so $$\alpha = \hat K^{-1}Y$$ and $$\theta_{*} = \Psi^{T}\hat K^{-1}Y$$; the prediction is $$\psi(x)\cdot\theta_{*} = \sum_{\mu} K(x,x^{\mu})\alpha_{\mu}$$. It is a minimum, not merely a critical point, because the objective is strictly convex and the constraint set is affine. In the SVD of Section 4.2, $$\Psi = USV^{T}$$ with $$S = [\mathrm{diag}(s_{1},\ldots,s_{n})\;\; 0]$$, one has $$\hat K = U\,\mathrm{diag}(s_{a}^{2})\,U^{T}$$ and $$\theta_{*} = VS^{T}\mathrm{diag}(s_{a}^{-2})U^{T}Y = \sum_{a=1}^{n} \frac{u_{a}\cdot Y}{s_{a}}\,v_{a}$$, where $$v_{a}$$ are the first $$n$$ columns of $$V$$: only right singular vectors with nonzero singular value (the row space) appear.

**(b)** $$c^{T}\hat Kc = c^{T}\Psi\Psi^{T}c = |\Psi^{T}c|^{2}\geq 0$$. If $$\hat Kc = 0$$ then $$\Psi^{T}c = \sum_{\mu} c_{\mu}\psi(x^{\mu}) = 0$$: a linear dependence among the training feature vectors (for instance two identical inputs, or simply $$n>P$$). $$\hat K$$ is invertible iff the $$n$$ training feature vectors are linearly independent, which requires $$n\leq P$$.

**(c)** $$\dot\theta = -\eta\Psi^{T}\Delta\in\mathrm{col}(\Psi^{T})$$, the row space of $$\Psi$$, so $$\theta(t)-\theta_{0} = -\eta\Psi^{T}\int_{0}^{t}\Delta$$ stays there. Since $$\Psi$$ is constant, $$\dot\Delta = \Psi\dot\theta = -\eta\Psi\Psi^{T}\Delta = -\eta\hat K\Delta$$, whence $$\Delta(t) = e^{-\eta t\hat K}\Delta(0)\to 0$$. Integrating, $$\theta(t)-\theta_{0} = -\eta\Psi^{T}\!\int_{0}^{t} e^{-\eta s\hat K}ds\,\Delta(0) = -\Psi^{T}\hat K^{-1}\big(1-e^{-\eta t\hat K}\big)\Delta(0)$$, and $$f_{\theta(t)}(x) = f_{\theta_0}(x)+\psi(x)\cdot(\theta(t)-\theta_{0})$$ is (4.36) with $$\Theta(x,x^{\mu}) = K(x,x^{\mu})$$ and $$\Theta = \hat K$$. At $$t\to\infty$$, $$\theta_{\infty} = \theta_{0}-\Psi^{T}\hat K^{-1}\Delta(0)$$ interpolates, and $$\theta_{\infty}-\theta_{0}\in\mathrm{row}(\Psi)$$. Any other interpolant $$\theta'$$ has $$\theta'-\theta_{\infty}\in\ker\Psi = \mathrm{row}(\Psi)^{\perp}$$, so by Pythagoras $$|\theta'-\theta_{0}|^{2} = |\theta_{\infty}-\theta_{0}|^{2}+|\theta'-\theta_{\infty}|^{2}\geq|\theta_{\infty}-\theta_{0}|^{2}$$: the flow converges to the interpolant closest to $$\theta_{0}$$, and for $$\theta_{0}=0$$ to $$\theta_{*}$$.

**(d)** $$\psi(x)\cdot\psi(z) = x_{1}^{2}z_{1}^{2}+2x_{1}x_{2}z_{1}z_{2}+x_{2}^{2}z_{2}^{2} = (x_{1}z_{1}+x_{2}z_{2})^{2}$$; without the $$\sqrt{2}$$ the cross term would be $$x_{1}x_{2}z_{1}z_{2}$$ and the sum would not be a perfect square. $$(1+xz)^{2} = 1+2xz+x^{2}z^{2}$$ comes from $$\psi(x) = (1,\sqrt{2}\,x,x^{2})$$, as in Exercise B.2. By the multinomial theorem $$(x\cdot z)^{m} = \sum_{|\alpha|=m}\binom{m}{\alpha}x^{\alpha} z^{\alpha}$$, so $$\psi_{\alpha}(x) = \sqrt{\binom{m}{\alpha}}\,x^{\alpha}$$ over the $$\binom{d+m-1}{m}$$ monomials of degree $$m$$.

:::

\### B.4 Kernel ridge regression

Rather than imposing the minimum-norm criterion as a hard constraint, one can add it to the loss as a penalty. For $$\lambda>0$$, *ridge regression* minimizes

$$
{{\mathcal L}}_{\lambda}(\theta) := \frac{1}{2}|\Psi\theta - Y|^{2} + \frac{\lambda}{2}|\theta|^{2}\,.
$$

The two terms measure distance to the data with $$\delta_{\mu\nu}$$ and distance to the origin with $$\delta_{ij}$$: ridge regression is a weighted compromise between the two metrics of Appendices B.1 and B.3, with $$\lambda$$ setting the exchange rate. (In the training of neural networks the penalty is called *weight decay*.) The penalty does two jobs at once. When $$P>n$$ it selects one solution out of infinitely many; and for any $$P$$ it makes the problem well posed even when the features are redundant or the labels are noisy. Note that the penalty is not invariant under rescaling features: it decides what counts as a "large" coefficient in the coordinates $$\psi$$ that were supplied.

The gradient is $$\Psi^{T}(\Psi\theta - Y) + \lambda\theta$$, so the stationarity condition is

$$
(\Psi^{T}\Psi + \lambda I_{P})\,\theta = \Psi^{T}Y\,.
$$

The matrix on the left is positive definite for every $$\lambda>0$$, whatever the rank of $$\Psi$$, since $$v^{T}(\Psi^{T}\Psi+\lambda I_{P})v = |\Psi v|^{2}+\lambda|v|^{2}>0$$. So there is always a unique minimizer,

$$
\theta_{\lambda} = (\Psi^{T}\Psi + \lambda I_{P})^{-1}\Psi^{T}Y\,,
$$

at the price of a $$P\times P$$ inverse. To move the inverse to the $$n\times n$$ side, expand and regroup the product

$$
\Psi^{T}(\Psi\Psi^{T} + \lambda I_{n}) = \Psi^{T}\Psi\Psi^{T} + \lambda\Psi^{T} = (\Psi^{T}\Psi + \lambda I_{P})\Psi^{T}\,.
$$

Both bracketed matrices are positive definite, so multiplying by their inverses on the appropriate sides gives the *push-through identity*

$$
(\Psi^{T}\Psi + \lambda I_{P})^{-1}\Psi^{T} = \Psi^{T}(\Psi\Psi^{T} + \lambda I_{n})^{-1}\,.
$$

Nothing was cancelled — $$\Psi^{T}$$ is rectangular and has no inverse — and that is precisely why the identity holds. Substituting into (B.18), the ridge solution again lies in the span of the training feature vectors, $$\theta_{\lambda} = \Psi^{T}\alpha_{\lambda}$$, now with $$\alpha_{\lambda} = (\hat K+\lambda I_{n})^{-1}Y$$, and the prediction at a new input is

$$
f_{\lambda}(x) = \sum_{\mu,\nu=1}^{n} K(x,x^{\mu})\,\big(\hat K + \lambda I_{n}\big)^{-1}_{\mu\nu}\,y^{\nu}\,.
$$

This is *kernel ridge regression*, the central formula of this appendix. As $$\lambda\to 0$$ it reduces to the minimum-norm interpolant (B.14) when $$\hat K$$ is invertible, and in general to the least-squares solution of minimum norm (Exercise B.4(c)). As $$\lambda\to\infty$$, $$\theta_{\lambda}\to 0$$.

Formula (B.21) is exactly the posterior mean of Exercise 4.5, with ridge parameter $$\lambda = \beta^{-1}$$ — there derived for the infinite-width Gaussian process, here for a finite linear model. The Bayesian reading is worth making explicit. With a Gaussian likelihood $$\propto e^{-\frac{\beta}{2}|\Psi\theta-Y|^2}$$ and a Gaussian prior $$\theta\sim{{\mathcal N}}(0,\sigma^{2} I_{P})$$, the loss (B.16) is $$-\beta^{-1}\log$$ of the posterior density, up to a constant, with $$\lambda = 1/(\beta\sigma^{2})$$. Ridge regression is thus maximum a posteriori estimation. The prior pushed forward to $$f_{\theta}(x) = \theta\cdot\psi(x)$$ is a Gaussian process with kernel $$\sigma^{2}K(x,x')$$, a finite-$$P$$ instance of Section 3.3, and the posterior mean of Exercise 4.5 for this process reproduces (B.21).

**Spectral view.**  With the singular value decomposition $$\Psi = USV^{T}$$ of Section 4.2, the Gram matrix is $$\hat K = US^{2}U^{T}$$, with eigenvalues $$s_{a}^{2}$$ and orthonormal eigenvectors $$u_{a}\in{\mathbb{R}}^{n}$$: the "features" of Section 4.2, *i.e.* the natural modes in the space of function values. The ridge predictions on the training set are $$f_{\lambda} = \Psi\theta_{\lambda} = \hat K(\hat K+\lambda I_{n})^{-1}Y$$, or, mode by mode,

$$
f_{\lambda} = \sum_{a} \frac{s_{a}^{2}}{s_{a}^{2}+\lambda}\,(u_{a}\cdot Y)\,u_{a}\,.
$$

Ridge regression is a *spectral filter*: modes of the data with $$s_{a}^{2}\gg\lambda$$ are fit, modes with $$s_{a}^{2}\ll\lambda$$ are suppressed, and the crossover is at $$s_{a}^{2}\approx\lambda$$. Compare gradient flow from $$\theta_{0} = 0$$ on the unpenalized loss, whose training predictions are, by (4.35),

$$
f(t) = \sum_{a} \big(1-e^{-\eta t s_a^2}\big)\,(u_{a}\cdot Y)\,u_{a}\,.
$$

This is also a spectral filter, with $$1/\eta t$$ playing the role of $$\lambda$$: *early stopping* regularizes much as ridge does. But the two filters have different shapes (Figure 13), and no choice of $$\lambda$$ reproduces a given stopping time on every mode at once (Exercise B.5). This is the precise content of the remark closing Section 4.6, that the inverse temperature of Bayesian learning and the training time of gradient descent play analogous roles.

![Ridge regression and early-stopped gradient flow as spectral filters: the fraction of a data mode that is fit, as a function of the mode's kernel eigenvalue . The two are tuned to agree on the mode with , and disagree elsewhere; the dots mark the two-mode example of Exercise B.5.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-ridge-filters-382fcb28.png)

Ridge regression and early-stopped gradient flow as spectral filters: the fraction of a data mode $$u_{a}\cdot Y$$ that is fit, as a function of the mode's kernel eigenvalue $$s_{a}^{2}$$. The two are tuned to agree on the mode with $$s^{2}=1$$, and disagree elsewhere; the dots mark the two-mode example of Exercise B.5.

:::callout {title="Exercise" tone="amber"}
**Exercise B.4 (Ridge regression, two ways).** **(a)** Derive (B.17) and (B.18), and prove that $$\Psi^{T}\Psi+\lambda I_{P}$$ is invertible even when $$\Psi$$ is rank deficient.

**(b)** Prove the push-through identity (B.20) and deduce (B.21). Explain why "cancelling $$\Psi^{T}$$" is not a valid step, and why the identity is nevertheless true. (It is a special case of $$A(BA+I)^{-1}= (AB+I)^{-1}A$$.)

**(c)** What happens as $$\lambda\to\infty$$? Using the SVD, show that $$\theta_{\lambda}$$ applies the scalar filter $$s/(s^{2}+\lambda)$$ to each singular value $$s$$ of $$\Psi$$, and hence that as $$\lambda\to 0$$ it converges to the least-squares solution of minimum norm. When does this limit interpolate the labels exactly?

**(d)** Return to $$x\in\{-1,0,1\}$$, $$y=x^{2}$$ and the kernel $$K(x,z) = (1+xz)^{2}$$ of Exercise B.2. With $$\lambda = 1$$, verify that

$$
\hat K = \begin{pmatrix}4 & 1 & 0 \\ 1 & 1 & 1 \\ 0 & 1 & 4\end{pmatrix}\,,\qquad \alpha_{\lambda} = \frac{1}{4}\begin{pmatrix}1 \\ -1 \\ 1\end{pmatrix}\,,
$$

and predict at $$z=2$$ using only kernel evaluations. Compare with the interpolant of Exercise B.2(a), which predicts $$z^{2}=4$$ there, and explain the direction of the discrepancy.

**(e)** The feature route solves a $$P\times P$$ system and the kernel route an $$n\times n$$ one. When is each attractive?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Setting $$\Psi^{T}(\Psi\theta-Y)+\lambda\theta = 0$$ gives (B.17); $$v^{T}(\Psi^{T}\Psi+\lambda I_{P})v = |\Psi v|^{2}+\lambda|v|^{2}\geq\lambda|v|^{2}>0$$ for $$v\neq0$$, so the matrix is positive definite, hence invertible, for every $$\lambda>0$$.

**(b)** $$\Psi^{T}(\Psi\Psi^{T}+\lambda I_{n}) = \Psi^{T}\Psi\Psi^{T}+\lambda\Psi^{T} = (\Psi^{T}\Psi+\lambda I_{P})\Psi^{T}$$ uses only associativity. Multiply on the left by $$(\Psi^{T}\Psi+\lambda I_{P})^{-1}$$ and on the right by $$(\Psi\Psi^{T}+\lambda I_{n})^{-1}$$, both of which exist by (a). $$\Psi^{T}$$ is $$P\times n$$ and, for $$P\neq n$$, has no two-sided inverse, so it cannot be "cancelled"; the identity holds because $$\Psi^{T}$$ was regrouped, not divided out. Then $$\theta_{\lambda} = \Psi^{T}(\hat K+\lambda I_{n})^{-1}Y$$ and $$f_{\lambda}(x) = \psi(x)\cdot\theta_{\lambda} = \sum_{\mu} K(x,x^{\mu})(\alpha_{\lambda})_{\mu}$$.

**(c)** As $$\lambda\to\infty$$, $$\theta_{\lambda} \approx \Psi^{T}Y/\lambda\to 0$$. With $$\Psi = USV^{T}$$, $$\Psi^{T}\Psi+\lambda I_{P} = V(S^{T}S+\lambda I_{P})V^{T}$$, so $$\theta_{\lambda} = V(S^{T}S+\lambda I_{P})^{-1}S^{T}U^{T}Y = \sum_{a} \frac{s_{a}}{s_{a}^{2}+\lambda}(u_{a}\cdot Y)\,v_{a}$$. As $$\lambda\to0$$, $$s_{a}/(s_{a}^{2}+\lambda)\to 1/s_{a}$$ for $$s_{a}>0$$ and $$\to 0$$ for $$s_{a} = 0$$: this is the pseudo-inverse $$\Psi^{+}Y$$, the least-squares solution of minimum norm (an arbitrary unregularized minimizer need not have minimum norm). It interpolates iff $$Y\in\mathrm{col}(\Psi)$$, *i.e.* iff $$u_{a}\cdot Y = 0$$ for every zero singular value.

**(d)** $$K(x^{\mu},x^{\nu}) = (1+x^{\mu} x^{\nu})^{2}$$ on $$\{-1,0,1\}$$ gives the displayed $$\hat K$$. Check $$(\hat K+I_{3})\alpha_{\lambda} = \frac{1}{4}(5-1,\;1-2+1,\;-1+5)^{T} = (1,0,1)^{T} = Y$$. At $$z=2$$ the kernel vector is $$\big(K(-1,2),K(0,2),K(1,2)\big) = (1,1,9)$$, so $$f_{\lambda}(2) = \frac{1}{4}(1-1+9) = \frac{9}{4}$$, versus $$4$$ for the interpolant. The ridge fit is shrunk toward zero: it no longer even interpolates the training labels (its training predictions are $$\hat K\alpha_{\lambda} = (3/4,1/4,3/4)^{T}$$), and the quadratic growth it does fit is damped.

**(e)** The feature route costs $$O(nP^{2}+P^{3})$$ and is attractive when $$P\ll n$$ and the features are explicit; the kernel route costs $$O(n^{2}\cdot(\text{cost of }K)+n^{3})$$ and is attractive when $$n\ll P$$, or when $$K$$ can be evaluated without constructing $$\psi$$ at all. Neither is free: $$n\times n$$ is fatal for large $$n$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise B.5 (Early stopping vs. ridge, on two data points).** Take $$n=2$$ training points with Gram matrix and labels

$$
\hat K = \begin{pmatrix}2 & 1 \\ 1 & 2\end{pmatrix}\,,\qquad Y = \begin{pmatrix}2 \\ 0\end{pmatrix}\,,
$$

and initial predictions $$f(0) = 0$$.

**(a)** Verify the eigenpairs $$u_{\pm} = \frac{1}{\sqrt{2}}(1,\pm 1)^{T}$$ with $$s_{\pm}^{2} = 3, 1$$, and decompose $$Y$$ into these modes.

**(b)** Using (B.23), find the training predictions $$f(t)$$ under gradient flow, and evaluate them at $$\eta t = \log 2$$. Why do both the eigenvalue $$s_{a}^{2}$$ and the initial projection $$u_{a}\cdot Y$$ matter for what is visible during training?

**(c)** Using (B.22), find the ridge predictions for $$\lambda = 1$$. The two filters agree on the mode with $$s^{2} = 1$$; show that the ridge parameter matching gradient flow at time $$t$$ on a mode with eigenvalue $$s^{2}$$ is $$\lambda_{\rm eff}(s^{2},t) = s^{2}/(e^{\eta t s^2}-1)$$, which depends on the mode — so early stopping is not ridge regression.

**(d)** State precisely what "spectral bias" means for this finite, fixed-kernel calculation. What additional structure would be needed to turn it into a claim about Fourier frequencies, about robustness to label noise, or about test error?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$\hat K u_{\pm} = (2\pm1)u_{\pm}$$, so $$s_{+}^{2} = 3$$, $$s_{-}^{2} = 1$$; and $$Y = \sqrt{2}\,u_{+}+\sqrt{2}\,u_{-} = (1,1)^{T}+(1,-1)^{T}$$.

**(b)** $$f(t) = (1-e^{-3\eta t})(1,1)^{T}+(1-e^{-\eta t})(1,-1)^{T} = \big(2-e^{-3\eta t}-e^{-\eta t},\; e^{-\eta t}-e^{-3\eta t}\big)^{T}$$. At $$\eta t = \log 2$$, $$e^{-\eta t}= \frac{1}{2}$$ and $$e^{-3\eta t}= \frac{1}{8}$$, giving $$(11/8,\,3/8)^{T}$$. The eigenvalue sets a mode's rate, while $$u_{a}\cdot Y$$ sets whether it is present and with what amplitude; a fast mode with zero initial amplitude leaves no trace in the trajectory.

**(c)** Ridge multipliers $$\frac{3}{3+1}= \frac{3}{4}$$ and $$\frac{1}{1+1}= \frac{1}{2}$$, so $$f_{\lambda} = \frac{3}{4}(1,1)^{T}+\frac{1}{2}(1,-1)^{T} = (5/4,\,1/4)^{T}$$. The flow multipliers at $$\eta t = \log2$$ are $$\frac{7}{8}$$ and $$\frac{1}{2}$$: the two agree on $$s^{2}=1$$ only. Solving $$s^{2}/(s^{2}+\lambda) = 1-e^{-\eta ts^2}$$ gives $$\lambda_{\rm eff}= s^{2}e^{-\eta ts^2}/(1-e^{-\eta ts^2}) = s^{2}/(e^{\eta ts^2}-1)$$; at $$\eta t=\log2$$ this is $$1$$ for $$s^{2}=1$$ but $$3/7$$ for $$s^{2}=3$$. No single $$\lambda$$ matches both modes.

**(d)** Here "spectral bias" means exactly this: components of the residual along eigenvectors of the fixed Gram matrix with larger eigenvalue decay faster, at rate $$\eta s_{a}^{2}$$. To speak of Fourier frequencies one needs a relation between the $$u_{a}$$ and Fourier modes (true, for instance, for translation-invariant kernels on uniform grids). To speak of noise one needs a model of how label noise projects onto the $$u_{a}$$ (typically spread evenly across modes, so that it lives mostly in the many slow modes — which is why early stopping and ridge both filter it). To speak of test error one needs a distribution over inputs and the population version of the kernel operator, as in Sections 4.6 and 7.7.

:::

\### B.5 Linearized networks are kernel ridge regressors

Now let $$f_{\theta}$$ be a neural network, with $$\theta\in{\mathbb{R}}^{P}$$ the vector of *all* its weights and biases. It is not linear in $$\theta$$. But its linearization around the initialization $$\theta_{0}$$, the ansatz (4.1),

$$
f^{\rm lin}_{\theta}(x) = f_{\theta_0}(x) + (\theta-\theta_{0})\cdot\nabla_{\theta} f_{\theta_0}(x)\,,
$$

is a model of the form (B.9). Compare term by term. The parameters are the displacement $$\delta\theta := \theta-\theta_{0}\in{\mathbb{R}}^{P}$$. The feature map is

$$
\psi(x) = \nabla_{\theta} f_{\theta_0}(x)\in{\mathbb{R}}^{P}\,,
$$

the *tangent features*: one number per parameter, the sensitivity of the output at $$x$$ to that parameter, evaluated at initialization and then frozen. And the constant offset $$f_{\theta_0}(x)$$ is absorbed by shifting the labels to

$$
\tilde y^{\mu} := y^{\mu} - f_{\theta_0}(x^{\mu}) = -\Delta^{\mu}(0)\,.
$$

The offset matters: the linearized model is fit to the *residuals at initialization*, not to the raw labels. The feature matrix (B.10) is the Jacobian at initialization, $$\Psi = J_{0}$$, and the Gram matrix (B.13) is

$$
\hat K = J_{0}J_{0}^{T} = \Theta_{0}\,,\qquad K(x,x') = \Theta(x,x') = \nabla_{\theta} f_{\theta_0}(x)\cdot\nabla_{\theta} f_{\theta_0}(x')\,,
$$

the neural tangent kernel (4.10) at initialization, extended to arbitrary pairs of inputs as in Exercise 4.3. Everything in Appendices B.3 and B.4 now applies verbatim. In particular, ridge regression on the linearized network with penalty $$\frac{\lambda}{2}|\theta-\theta_{0}|^{2}$$ — weight decay toward the initialization — gives, by (B.21),

$$
f^{\rm lin}_{\lambda}(x) = f_{\theta_0}(x) - \sum_{\mu,\nu=1}^{n} \Theta(x,x^{\mu})\,\big(\Theta_{0} + \lambda I_{n}\big)^{-1}_{\mu\nu}\,\Delta^{\nu}(0)\,.
$$

At $$\lambda\to 0$$ this is the $$t\to\infty$$ limit of (4.36), the minimum-norm interpolant of the residuals; and the finite-time solution (4.36) is its early-stopped cousin, in the sense of (B.23). The kernel trick is not a convenience here but a necessity: $$P$$ is the parameter count of the network, often $$10^{7}$$ or more, while $$\Theta_{0}$$ is $$n\times n$$.

Two remarks on what is and is not being claimed. First, for the linearized model $$f^{\rm lin}$$ everything above is exact, and its kernel is constant by construction. For the actual network, (B.24) is an ansatz. Section 4.3 shows that it becomes exact in the large-width limit at fixed depth and data; whether and when it is a good approximation otherwise — and what happens when the tangent features move — is the subject of Sections 5–6, not of this appendix. Second, the initialization $$\theta_{0}$$ is random, so $$f_{\theta_0}$$, the tangent features, and the kernel $$\Theta_{0}$$ are all random too, and (B.28) is the trained function for one draw. Averaging over draws, at large width where $$\Theta_{0}$$ becomes deterministic, gives the Gaussian process (4.38).

:::callout {title="Exercise" tone="amber"}
**Exercise B.6 (Tangent features of a one-hidden-layer network).** Consider $$f_{\theta}(x) = \sum_{i=1}^{N} c_{i}\,\phi(a_{i}\cdot x)$$ with $$\theta = (c_{i}, a_{i})_{i=1}^{N}$$, so that $$P = N(d+1)$$.

**(a)** Compute the tangent features $$\nabla_{\theta} f_{\theta_0}(x)$$, and show that the tangent kernel is

$$
\Theta(x,x') = \sum_{i=1}^{N} \phi(a_{i}\cdot x)\,\phi(a_{i}\cdot x') + \sum_{i=1}^{N} c_{i}^{2}\,\phi'(a_{i}\cdot x)\,\phi'(a_{i}\cdot x')\,(x\cdot x')\,.
$$

**(b)** Suppose only the output weights $$c$$ are trained, with the $$a_{i}$$ frozen at their random initial values. Show that this is exactly a fixed-feature model (B.9) with random features, that its linearization is exact, and that its kernel is the first term above. Which term do you get by training only the $$a_{i}$$?

**(c)** Show that gradient flow with weight decay toward the initialization, $$\dot\theta = -\eta\big[\nabla_{\theta} {{\mathcal L}} + \lambda(\theta-\theta_{0})\big]$$, applied to the linearized model $$f^{\rm lin}$$, converges to the ridge solution (B.28) for every $$\lambda>0$$ and from any starting point.

**(d)** Check that (B.28) at $$\lambda\to 0$$ coincides with (4.36) at $$t\to\infty$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $$\partial f/\partial c_{i} = \phi(a_{i}\cdot x)$$ and $$\partial f/\partial a_{ij}= c_{i}\,\phi'(a_{i}\cdot x)\,x_{j}$$. Taking the inner product of the tangent features at $$x$$ and $$x'$$ and summing over $$j$$ in the second block gives the displayed $$\Theta(x,x')$$.

**(b)** With the $$a_{i}$$ frozen, $$f = \sum_{i} c_{i}\psi_{i}(x)$$ with $$\psi_{i}(x) = \phi(a_{i}\cdot x)$$ is linear in the trainable parameters $$c$$, so $$f = f^{\rm lin}$$ exactly, $$\Psi^{\mu}{}_{i} = \phi(a_{i}\cdot x^{\mu})$$, and $$\hat K^{\mu\nu}= \sum_{i}\phi(a_{i}\cdot x^{\mu})\phi(a_{i}\cdot x^{\nu})$$ is the first term: the random-features model. Training only the $$a_{i}$$ gives the second term, but there the linearization is not exact, since $$f$$ is nonlinear in $$a$$.

**(c)** Writing $$\delta\theta = \theta-\theta_{0}$$, the linearized loss is $${{\mathcal L}}^{\rm lin}= \frac{1}{2}|J_{0}\delta\theta+\Delta(0)|^{2}$$, so $$\delta\dot\theta = -\eta\big[J_{0}^{T}(J_{0}\delta\theta+\Delta(0))+\lambda\delta\theta\big] = -\eta\big[M\delta\theta+J_{0}^{T}\Delta(0)\big]$$ with $$M = J_{0}^{T}J_{0}+\lambda I_{P}$$. This is a linear ODE with positive-definite $$M$$, so $$\delta\theta(t) = \delta\theta_{\infty}+e^{-\eta tM}\big(\delta\theta(0)-\delta\theta_{\infty}\big)$$ converges from any start to $$\delta\theta_{\infty} = -M^{-1}J_{0}^{T}\Delta(0) = -J_{0}^{T}(\Theta_{0}+\lambda I_{n})^{-1}\Delta(0)$$, by push-through. Then $$f^{\rm lin}(x) = f_{\theta_0}(x)+\nabla_{\theta} f_{\theta_0}(x)\cdot\delta\theta_{\infty}$$ is (B.28), since $$\nabla_{\theta} f_{\theta_0}(x)\cdot J_{0}^{T}$$ has components $$\Theta(x,x^{\mu})$$.

**(d)** As $$\lambda\to0$$, $$(\Theta_{0}+\lambda I_{n})^{-1}\to\Theta_{0}^{-1}$$; as $$t\to\infty$$ in (4.36), $$(1-e^{-\eta t\Theta})\to 1$$. Both give $$f_{\theta_0}(x)-\Theta(x,x^{\mu})\,\Theta^{-1}_{\mu\nu}\,\Delta^{\nu}(0)$$.

:::

\## C. Solutions to exercises

Worked solutions to the exercises, in the order in which the exercises appear. (Instructors: uncommenting `\solutionsfalse` in the preamble removes this appendix's contents, and all other solution boxes, from the compiled PDF.)

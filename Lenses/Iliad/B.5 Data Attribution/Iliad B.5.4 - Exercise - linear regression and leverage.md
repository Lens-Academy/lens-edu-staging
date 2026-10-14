---
id: '1fe586fc-aae2-4db4-8567-f0b1193fc207'
title: "B.5.4 Exercise: linear regression and leverage"
tldr: "Works Exercise 2.2 on linear regression: closed-form influence, the exact deletion update with leverage, and a comparison of the influence approximation against true leave-one-out."
summary_for_tutor: "Exercise 2.2 (a)-(e) of Iliad worksheet B.5 Data Attribution, with collapsed solutions: linear regression minimizer, parameter influence, the exact reweighting formula in beta_j, its Taylor series, and the closed-form deletion update at beta_j = 0. Followed by a remark on leverage h_j, a figure comparing influence with leave-one-out ground truth, and a footnote on the matrix inversion identity. Keep h_j, r_j, A. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
:::callout {title="Exercise" tone="amber"}
**Exercise 2.2 (Linear regression).** Consider linear regression with training data $$\{(x_{i},y_{i})\}_{i=1}^{n}$$, $$x_{i}\in\mathbb{R}^{p}$$, and squared loss $$L(w,(x_{i},y_{i})) = \tfrac{1}{2}(y_{i} - w^{\top} x_{i})^{2}$$. Write $$A := \sum_{i} x_{i} x_{i}^{\top}$$. In this case the minimizer, the influence function, and the exact LOO update all have closed-form solutions. We will see that in general the influence functions can diverge in extreme cases.

**(a)** Derive the minimizer $$w^{*}$$ by setting $$\nabla_{w} L(w) = 0$$. Show that $$w^{*} = A^{-1}\sum_{i} x_{i} y_{i}$$.

**(b)** Compute the parameter influence $$\mathcal{I}_{\mathrm{param}}(z_{j})$$ from Definition 2.2.

**(c)** Define $$w^{*}(\beta_{j}) := {\operatorname*{arg\,min}}_{w} \sum_{i\ne j}L(w,z_{i}) + \beta_{j} L(w,z_{j})$$, so that $$\beta_{j} = 1$$ is the unperturbed model and $$\beta_{j} = 0$$ corresponds to fully removing $$z_{j}$$. Using the Sherman–Morrison formula[^2], show that

$$
w^{*}(\beta_{j}) \;-\; w^{*} \;=\; -\,\frac{(1-\beta_{j})\,A^{-1}x_{j}\,r_{j}}{1 - (1-\beta_{j})\,h_{j}},
$$

where $$r_{j} := y_{j} - x_{j}^{\top} w^{*}$$ is the residual at $$z_{j}$$ and $$h_{j} := x_{j}^{\top} A^{-1}x_{j}$$ is the *leverage* of $$x_{j}$$. Note that this is a rational function of $$\beta_{j}$$. This is the ground truth effect of perturbing $$z_{j}$$.

**(d)** Expand the closed form from (c) as a Taylor series in $$(1-\beta_{j})$$ around the unperturbed point $$\beta_{j} = 1$$ by recognizing $$1/(1 - (1-\beta_{j})h_{j})$$ as a geometric series, and obtain

$$
w^{*}(\beta_{j}) - w^{*} \;=\; -\,A^{-1}x_{j}\,r_{j}\,\sum_{k=1}^{\infty}\,(1-\beta_{j})^{k}\,h_{j}^{\,k-1}.
$$

Identify the $$k=1$$ term with the parameter influence from part (b), and observe that the higher-order terms ($$k \ge 2$$) are suppressed by powers of the leverage $$h_{j}$$.

**(e)** Specialize to the LOO endpoint $$\beta_{j} = 0$$. Sum the geometric series in $$h_{j}$$ to obtain the closed-form deletion update

$$
w^{*}_{(-j)}- w^{*} \;=\; -\,A^{-1}x_{j}\,r_{j}\,\bigl(1 + h_{j} + h_{j}^{2}+ h_{j}^{3}+ \cdots\bigr) \;=\; -\,\frac{A^{-1}x_{j}\,r_{j}}{1 - h_{j}}.
$$

The IF prediction is the $$h_{j}^{0}$$ leading term. Discuss the two regimes $$h_{j} \to 0$$ and $$h_{j} \to 1$$: when does keeping only the linear term suffice, and when do all the higher-order corrections matter?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* The gradient of the training loss is $$\nabla_{w} L(w) = -\sum_{i} x_{i}(y_{i} - x_{i}^{\top} w) = -\sum_{i} x_{i} y_{i} + Aw$$. Setting this to zero gives $$Aw^{*} = \sum_{i} x_{i} y_{i}$$, hence $$w^{*} = A^{-1}\sum_{i} x_{i} y_{i}$$.

*(b)* The Hessian of the unweighted training loss is $$H = \sum_{i} x_{i} x_{i}^{\top} = A$$, and the gradient of the per-example loss at $$z_{j} = (x_{j},y_{j})$$ is $$\nabla_{w} L(w^{*}, z_{j}) = -x_{j}(y_{j} - x_{j}^{\top} w^{*}) = -x_{j}\,r_{j}$$. Plugging into Definition 2.2 with $$\phi(w) = w$$ (so $$\nabla_{w}\phi(w^{*}) = I$$),

$$
\mathcal{I}(z_{j}, w^{*}) \;=\; -\,A^{-1}\bigl(-x_{j} r_{j}\bigr) \;=\; A^{-1}x_{j}\,r_{j},
$$

a residual times a leverage-weighted input.

*(c)* The normal equations for $$w^{*}(\beta_{j})$$ read

$$
\Bigl(\sum_{i\ne j}x_{i} x_{i}^{\top} + \beta_{j}\,x_{j} x_{j}^{\top}\Bigr)\,w \;=\; \sum_{i\ne j}x_{i} y_{i} \;+\; \beta_{j}\,x_{j} y_{j},
$$

or equivalently $$\bigl(A - (1-\beta_{j})\,x_{j} x_{j}^{\top}\bigr)\,w = \sum_{i} x_{i} y_{i} - (1-\beta_{j})\,x_{j} y_{j}$$. Sherman–Morrison applied to the rank-one update on the left gives

$$
\bigl(A - (1-\beta_{j})\,x_{j} x_{j}^{\top}\bigr)^{-1}\;=\; A^{-1}\;+\; \frac{(1-\beta_{j})\,p_{j} p_{j}^{\top}}{1 - (1-\beta_{j})\,h_{j}},
$$

where we write $$p_{j} := A^{-1}x_{j}$$ and $$h_{j} := x_{j}^{\top} p_{j}$$. Multiplying through and using the identities $$A^{-1}\sum_{i} x_{i} y_{i} = w^{*}$$ and $$p_{j}^{\top}\sum_{i} x_{i} y_{i} = x_{j}^{\top} w^{*}$$,

$$
\begin{aligned}w^{*}(\beta_{j})&\;=\; w^{*} \;-\; (1-\beta_{j})\,p_{j}\,y_{j} \\&\qquad\;+\; \frac{(1-\beta_{j})\,p_{j}\bigl(x_{j}^{\top} w^{*} \;-\; (1-\beta_{j})\,h_{j}\,y_{j}\bigr)}{1 - (1-\beta_{j})\,h_{j}}\\[3pt]&\;=\; w^{*} \;+\; \frac{p_{j}}{1 - (1-\beta_{j})\,h_{j}}\Bigl[-(1-\beta_{j})\,y_{j}\bigl(1-(1-\beta_{j})h_{j}\bigr) \\&\qquad\qquad\qquad\qquad\;+\; (1-\beta_{j})\,x_{j}^{\top} w^{*} \;-\; (1-\beta_{j})^{2}\,h_{j}\,y_{j}\Bigr] \\[3pt]&\;=\; w^{*} \;+\; p_{j}\cdot\frac{(1-\beta_{j})\bigl(x_{j}^{\top} w^{*} - y_{j}\bigr)}{1 - (1-\beta_{j})\,h_{j}}\\[3pt]&\;=\; w^{*} \;-\; \frac{(1-\beta_{j})\,p_{j}\,r_{j}}{1 - (1-\beta_{j})\,h_{j}},\end{aligned}
$$

the claimed expression. The result is rational in $$\beta_{j}$$ because the matrix being inverted is linear in $$\beta_{j}$$.

*(d)* Expanding $$1/(1-(1-\beta_{j}) h_{j})$$ as a geometric series in $$(1-\beta_{j}) h_{j}$$ (valid for $$|(1-\beta_{j}) h_{j}| < 1$$),

$$
\begin{aligned}w^{*}(\beta_{j}) - w^{*}&\;=\; -\,(1-\beta_{j})\,A^{-1}x_{j}\,r_{j}\,\sum_{k=0}^{\infty}\,(1-\beta_{j})^{k}\,h_{j}^{k}\\&\;=\; -\,A^{-1}x_{j}\,r_{j}\,\sum_{k=1}^{\infty}\,(1-\beta_{j})^{k}\,h_{j}^{\,k-1}.\end{aligned}
$$

Reading off term by term:

- The $$k=1$$ term is $$-A^{-1}x_{j}\,r_{j}\,(1-\beta_{j}) = \mathcal{I}(z_{j},w^{*})\cdot(\beta_{j} - 1)$$, exactly the influence-function prediction — as it must be, since the IF *is* the linear coefficient of $$w^{*}(\beta_{j})$$ at $$\beta_{j} = 1$$.
- The $$k=2$$ term, $$-A^{-1}x_{j}\,r_{j}\,(1-\beta_{j})^{2}\,h_{j}$$, is the second-order Taylor correction. It carries one factor of leverage and is doubly suppressed: small both in $$(1-\beta_{j})$$ and in $$h_{j}$$.
- Each subsequent term picks up another factor of $$(1-\beta_{j}) h_{j}$$. The IF/LOO "error" is precisely this tail, viewed as a series in the perturbation size and the leverage.

*(e)* At $$\beta_{j} = 0$$ the perturbation factor $$(1-\beta_{j})$$ is unity, and the higher-order terms no longer have a small parameter in front of them — only powers of $$h_{j}$$ remain. The series collapses to a pure geometric series in $$h_{j}$$:

$$
w^{*}_{(-j)}- w^{*} \;=\; -\,A^{-1}x_{j}\,r_{j}\,\bigl(1 + h_{j} + h_{j}^{2}+ h_{j}^{3}+ \cdots\bigr) \;=\; -\,\frac{A^{-1}x_{j}\,r_{j}}{1 - h_{j}}.
$$

The IF prediction $$-A^{-1}x_{j}\,r_{j}$$ is the $$k=0$$ leading term; everything else is the Taylor remainder. So the often-quoted "factor of $$1/(1-h_{j})$$" between IF and LOO is not a non-perturbative effect: it is the sum of all the higher-order Taylor terms, which OLS happens to admit in closed form because $$w^{*}(\beta_{j})$$ is rational. For more general M-estimators the response function is no longer rational and the higher-order terms do not sum to such a clean expression — but they are still there, with the same qualitative behavior.

In the two limiting regimes:

- $$h_{j} \to 0$$ (low leverage). Each higher-order term carries a factor of $$h_{j}^{k-1}$$, so they are individually negligible and the IF approximation is essentially exact.
- $$h_{j} \to 1$$ (high leverage). The geometric series barely converges and the higher-order terms together carry an arbitrarily large total weight. The IF underestimates the true LOO change without bound.

This is a clean demonstration that even in a strictly convex, fully-converged setting the linearization in Definition 2.2 loses control over precisely the points one most wants to attribute — the ones the model could not fit without them. The lesson generalizes: high-leverage / outlier examples are exactly where IF approximations should be distrusted, and the modern fixes from Section 2.2 (damping, GNH, PBRF) all address related but more severe versions of the same issue.

:::

:::callout {title="Note" tone="blue"}

**Remark (What is leverage?).** The quantity $$h_{j} = x_{j}^{\top} A^{-1}x_{j}$$ that appeared in Exercise 2.2 measures how *unusual* the input $$x_{j}$$ is relative to the bulk of the design. To see this, observe that $$\widehat\Sigma_{xx}:= A/n = \tfrac{1}{n}\sum_{i} x_{i} x_{i}^{\top}$$ is the empirical second-moment matrix of the inputs, so

$$
h_{j} \;=\; \tfrac{1}{n}\;x_{j}^{\top}\,\widehat\Sigma_{xx}^{-1}\,x_{j}
$$

is $$1/n$$ times a *Mahalanobis-style* squared norm of $$x_{j}$$, taken in the metric defined by the data itself. Geometrically: directions that the data samples a lot correspond to large eigenvalues of $$\widehat\Sigma_{xx}$$ and contribute little to $$h_{j}$$, while directions that are barely sampled correspond to small eigenvalues of $$\widehat\Sigma_{xx}$$ and so blow up under $$\widehat\Sigma_{xx}^{-1}$$. *Inputs that point in under-sampled directions get large leverage.* High-leverage points are unusual in feature space.

Figure 1 illustrates the effect on a simple linear regression: removing a low-leverage point (A, near the bulk of the data) barely changes the fit, and the IF approximation is accurate. Removing a high-leverage point (B, an outlier on the $$x$$-axis) changes the fit dramatically, and the IF underestimates the true LOO effect.

:::

![Influence approximation vs. LOO ground truth for a linear regression. Left: the full dataset. Centre: removing the low-leverage point A () barely perturbs the fit; the IF prediction closely matches LOO. Right: removing the high-leverage point B () moves the regression line substantially; the IF underestimates the true change. Note that both points have the same parameter influence.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-b5-if-vs-loo.png)

Influence approximation vs. LOO ground truth for a linear regression. *Left:* the full dataset. *Centre:* removing the low-leverage point A ($$h_{A}\approx 0.03$$) barely perturbs the fit; the IF prediction closely matches LOO. *Right:* removing the high-leverage point B ($$h_{B}\approx 0.83$$) moves the regression line substantially; the IF underestimates the true change. Note that both points have the same parameter influence.

[^2]: For an invertible matrix $$M$$ and vectors $$u,v$$: $$(M + uv^{\top})^{-1}= M^{-1}- \frac{M^{-1}u\,v^{\top} M^{-1}}{1 + v^{\top} M^{-1}u}$$.

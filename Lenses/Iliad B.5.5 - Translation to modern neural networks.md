---
id: '198d62bf-6c0f-4dbe-a057-91e984466a77'
title: "B.5.5 Translation to modern neural networks"
tldr: "Explains why classical influence functions break for neural networks (singular Hessian, negative curvature, non-converged checkpoints), the proximal Bregman fix, and Exercise 2.3 on a degenerate two-parameter model."
summary_for_tutor: "Section 2.2 of Iliad worksheet B.5 Data Attribution: assumptions (i) unique global minimum and (ii) positive definite Hessian, three failure modes, the proximal Bregman objective (PBRF) of Bae et al. 2022 giving the damped Gauss-Newton form with (G + lambda I) inverse, remarks on the SLT day and on scaling with EK-FAC, and Exercise 2.3 (a)-(c) on the toy model with observable phi(w) = ab, using the pseudoinverse and the damped inverse, with collapsed solution. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.2 Translation to modern neural networks

The derivation in Section 2.1 relied on two assumptions:

**(i)** $$w^{*}$$ is the unique global minimum of the training loss;

**(ii)** the Hessian $$H = \nabla_{w}^{2} L(w^{*})$$ is positive definite.

While neither holds for a modern neural network, the quantities in Definition 2.2 are, in principle, computable. Koh & Liang 2020 popularized the influence function formula as a tool for deep learning, and a substantial body of work has tried to make it useful at scale.

**(1) Non-uniqueness and a singular Hessian.**  For a neural network the global minimum is usually not unique. The set of minimizers is generically a positive-dimensional zero locus, and the Hessian at any point on it is singular: it has a nontrivial null space corresponding to directions of parameter movement that leave the loss unchanged. This is the degeneracy phenomenon observed in the SLT day, and it means we cannot invert $$H$$ as in Definition 2.2.

The standard remedy is to *dampen* the Hessian: replace $$H^{-1}$$ with $$(H + \lambda I)^{-1}$$ for some $$\lambda > 0$$. This is the same as adding an $$L_{2}$$-regularizer $$\frac{\lambda}{2}\|w-w^{*}\|^{2}$$ to the training objective $$L(w,\beta)$$; this yields a new loss function $$L_{\mathrm{reg}}(w,\beta)= L(w,\beta)+\frac{\lambda}{2}\cdot \|w-w^{*}\|^{2}$$.

**(2) Negative curvature.**  Even after damping away the zero eigenvalues, $$H$$ at a non-converged checkpoint can have negative eigenvalues, in which case $$(H + \lambda I)^{-1}$$ may still be ill-conditioned or even point in the wrong direction. The standard fix is to replace $$H$$ with the *Gauss–Newton Hessian* (GNH)

$$
G \;=\; \mathbb{E}_{(x,y)\sim\mathcal{D}}\bigl[J^{\top} H_{y} J\bigr],
$$

where $$J = \partial f_{w}/\partial w$$ is the parameter-output Jacobian and $$H_{y}$$ is the Hessian of the per-example loss with respect to the network outputs (not the parameters). For the cross-entropy and squared losses $$H_{y}$$ is positive semidefinite, hence so is $$G$$. The GNH is a local approximation to the true Hessian that ignores second derivatives of the network outputs with respect to the parameters. It is not hard to show that $$G$$ and $$H$$ differ by a term that vanishes at a critical point of $$L$$, so the GNH is a reasonable proxy for $$H$$ when $$w^{*}$$ is close to optimal.

**(3) Non-converged checkpoints.**  In practice $$w^{*}$$ is not a critical point of $$L$$. The classical formula in Definition 2.2 is then evaluated at a point where $$\nabla L \neq 0$$.

The fix proposed by Bae et al. 2022 is to replace the original training loss by a surrogate for which $$w^{*}$$ *is* optimal by construction. Concretely, define the *proximal Bregman objective* (PBO) as

$$
\begin{aligned}L_{\mathrm{PBO}}(w;\beta) \;=\;&\sum_{i=1}^{n}D_{L_y}\!\bigl(f_{w}(x_{i}),\,f_{w^*}(x_{i})\bigr) \;+\; \sum_{i=1}^{n}(\beta_{i} - 1)\,L(w,z_{i}) \\&+ \frac{\lambda}{2}\,\|w - w^{*}\|^{2},\end{aligned}
$$

where $$D_{L_y}(\hat y,\hat y^{*})$$ is the Bregman divergence of the output-space loss $$L_{y}$$ around $$\hat y^{*}$$. The first term penalizes any change in the network's predictions on the training set, with the current model $$w^{*}$$ as the reference; the second is the perturbation of interest; the third is the damping. By construction, $$w^{*}$$ is the minimizer of $$L_{\mathrm{PBO}}(\,\cdot\,;\mathbf{1})$$ regardless of whether it is a critical point of the original loss. The minimizer of $$L_{\mathrm{PBO}}(\,\cdot\,;\beta)$$ for nearby $$\beta$$ defines the *proximal Bregman response function* (PBRF).

When one re-derives the influence function formula starting from $$L_{\mathrm{PBO}}$$ instead of $$L$$, the result is

$$
\mathcal{I}_{\mathrm{PBRF}}(z_{i},\phi) \;=\; -\,\nabla_{w}\phi(w^{*})^{\top}\,(G + \lambda I)^{-1}\,\nabla_{w} L(w^{*},z_{i}),
$$

the same expression that the modern literature uses. This is effectively the counterfactual it approximates. As Bae et al. 2022 put it: *if influence functions are the answer, the question is the PBRF, not LOO retraining*. We refer to their paper for a detailed decomposition of the remaining gap between the PBRF and the original LOO counterfactual.

:::callout {title="Note" tone="blue"}

**Remark (Connection to the SLT day).** A central obstacle to the application of influence functions to modern neural networks is *degeneracy*: the set of minimizers of an overparameterized model is singular and the Hessian has a large null space. In Section 3 we will see a degeneracy-aware alternative: Bayesian influence functions, which replace inverse-Hessian computations with covariances over a localized posterior.

:::

:::callout {title="Note" tone="blue"}

**Remark (Scaling and EK-FAC).** Even with the PBRF reframing, computing $$(G + \lambda I)^{-1}$$ for a billion-parameter model is not directly feasible. Grosse et al. 2023 scale influence functions to large language models by approximating $$G$$ with EK-FAC (a Kronecker-factored approximation to layerwise curvature).

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.3 (Failure of the first-order approximation in a degenerate model).** Consider the toy two-parameter model from the SLT lecture day in which $$w = (a,b)$$ enters the loss only through the product $$u = ab$$, with squared loss $$L(w,z) = \tfrac{1}{2}(z - ab)^{2}$$ on training data $$\{z_{1},\dots,z_{n}\}\subset\mathbb{R}$$.

**(a)** Write down the Hessian of the training loss at any minimizer $$(a^{*},b^{*})$$ with $$a^{*} b^{*} = \bar z := \tfrac{1}{n}\sum_{i} z_{i}$$. Show that it has rank one, and identify the one-dimensional null space geometrically.

**(b)** Compute the influence function $$\mathcal{I}(z_{i},\phi)$$ for the observable $$\phi(w) = ab$$, treating $$H^{-1}$$ as a Moore–Penrose pseudoinverse[^3]. How does it compare with the exact LOO change in $$\phi$$?

**(c)** Repeat (b) using the damped inverse $$(H + \lambda I)^{-1}$$ for a small $$\lambda > 0$$. Discuss how the answer depends on $$\lambda$$, on the choice of minimizer $$(a^{*},b^{*})$$ along the singular set, and on $$n$$. What does this say about the proximity gap?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* The per-example loss is $$\ell_{i} = \tfrac{1}{2}(z_{i} - ab)^{2}$$. Its second derivatives are

$$
\frac{\partial^{2} \ell_{i}}{\partial a^{2}}= b^{2}, \qquad \frac{\partial^{2} \ell_{i}}{\partial b^{2}}= a^{2}, \qquad \frac{\partial^{2} \ell_{i}}{\partial a\,\partial b}= 2ab - z_{i}.
$$

Summing over $$i$$ and evaluating at any minimizer $$(a^{*},b^{*})$$ with $$a^{*}b^{*} = \bar z$$,

$$
H \;=\; n\begin{pmatrix}(b^{*})^{2}&a^{*}b^{*} \\ a^{*}b^{*}&(a^{*})^{2}\end{pmatrix} \;=\; n\,\mathbf{v}\mathbf{v}^{\top}, \qquad \mathbf{v}:= \begin{pmatrix}b^{*}\\a^{*}\end{pmatrix},
$$

where we used $$\sum_{i}(2a^{*}b^{*} - z_{i}) = n(2\bar z - \bar z) = na^{*}b^{*}$$ for the off-diagonal. This is rank one, with image $$\operatorname{span}(\mathbf{v})$$.

The null space is $$\operatorname{span}\bigl((a^{*},-b^{*})^{\top}\bigr)$$. Geometrically: the minimizers form the hyperbola $$\{(a,b): ab = \bar z\}$$, and the tangent to this hyperbola at $$(a^{*},b^{*})$$ is exactly the direction $$(a^{*},-b^{*})$$ — the infinitesimal generator of the rescaling symmetry $$(a,b)\to(\alpha a,\, b/\alpha)$$ at $$\alpha=1$$. The null space of $$H$$ is the tangent to the manifold of minimizers.

*(b)* We need two gradients at the minimizer. For the observable $$\phi(w) = ab$$:

$$
\nabla_{w}\phi \;=\; (b^{*},\,a^{*})^{\top} \;=\; \mathbf{v}.
$$

For the per-example loss at $$z_{i}$$:

$$
\nabla_{w} L(w^{*},z_{i}) \;=\; -(z_{i} - \bar z)\,(b^{*},\,a^{*})^{\top} \;=\; -(z_{i} - \bar z)\,\mathbf{v}.
$$

Both point in the $$\mathbf{v}$$ direction — neither has a component in the null space of $$H$$. The Moore–Penrose pseudoinverse of $$H = n\,\mathbf{v}\mathbf{v}^{\top}$$ is

$$
H^{+} \;=\; \frac{1}{n\,\|\mathbf{v}\|^{4}}\,\mathbf{v}\mathbf{v}^{\top}, \qquad \|\mathbf{v}\|^{2} = (a^{*})^{2} + (b^{*})^{2}.
$$

Plugging into the IF formula,

$$
\mathcal{I}(z_{i},\phi) \;=\; -\mathbf{v}^{\top} H^{+}\bigl(-(z_{i}-\bar z)\,\mathbf{v}\bigr) \;=\; (z_{i} - \bar z)\,\frac{\|\mathbf{v}\|^{4}}{n\,\|\mathbf{v}\|^{4}}\;=\; \frac{z_{i} - \bar z}{n}.
$$

The $$\|\mathbf{v}\|$$ factors cancel: the pseudoinverse IF is *independent* of the choice of minimizer $$(a^{*},b^{*})$$.

*Comparison with exact LOO.* Removing $$z_{i}$$ changes the sample mean to $$\bar z_{(-i)}= (n\bar z - z_{i})/(n-1)$$, and the observable at any new minimizer is $$\phi = \bar z_{(-i)}$$. So the exact LOO change is

$$
\phi(w^{*}_{(-i)}) - \phi(w^{*}) \;=\; \bar z_{(-i)}- \bar z \;=\; -\,\frac{z_{i} - \bar z}{n-1}.
$$

The IF predicts $$-\mathcal{I}(z_{i},\phi) = -(z_{i}-\bar z)/n$$. The ratio is $$n/(n-1) = 1/(1-h)$$ with leverage $$h = 1/n$$ — every point has equal leverage in this one-effective-parameter model, and we recover the same $$1/(1-h)$$ correction as in Exercise 2.2.

*(c)* The eigenvalues of $$H = n\,\mathbf{v}\mathbf{v}^{\top}$$ are $$n\|\mathbf{v}\|^{2}$$ (eigenvector $$\hat{\mathbf{v}}= \mathbf{v}/\|\mathbf{v}\|$$) and $$0$$ (eigenvector $$\hat{\mathbf{v}}_{\perp} = (a^{*},-b^{*})^{\top}/\|\mathbf{v}\|$$). So

$$
(H+\lambda I)^{-1}\;=\; \frac{1}{n\|\mathbf{v}\|^{2}+\lambda}\,\hat{\mathbf{v}}\hat{\mathbf{v}}^{\top} \;+\; \frac{1}{\lambda}\,\hat{\mathbf{v}}_{\perp}\hat{\mathbf{v}}_{\perp}^{\top}.
$$

Since $$\nabla\phi$$ and $$\nabla L_{i}$$ both lie in the $$\hat{\mathbf{v}}$$ direction, the $$1/\lambda$$ term does not contribute, and

$$
\mathcal{I}_{\lambda}(z_{i},\phi) \;=\; \frac{(z_{i}-\bar z)\,\|\mathbf{v}\|^{2}}{n\|\mathbf{v}\|^{2} + \lambda}.
$$

*Dependence on the minimizer.* For $$\lambda > 0$$ the answer depends on $$\|\mathbf{v}\|^{2} = (a^{*})^{2} + (b^{*})^{2}$$, which varies along the orbit $$ab = \bar z$$. For instance, the "balanced" minimizer $$(\sqrt{\bar z},\sqrt{\bar z})$$ gives $$\|\mathbf{v}\|^{2} = 2\bar z$$, while the "unbalanced" choice $$(\bar z,1)$$ gives $$\|\mathbf{v}\|^{2} = \bar z^{2} + 1$$. Different minimizers yield different IFs. This is the proximity gap: the damping term $$\tfrac{\lambda}{2}\|w-w^{*}\|^{2}$$ breaks the rescaling symmetry and anchors the computation at a particular point on the orbit.

*Limit $$\lambda\to 0$$.* $$\mathcal{I}_{\lambda} \to (z_{i}-\bar z)/n$$ regardless of $$(a^{*},b^{*})$$, recovering the pseudoinverse answer from (b). The damping-induced dependence on the minimizer vanishes.

*Limit $$\lambda\to\infty$$.* $$\mathcal{I}_{\lambda} \to 0$$: heavy damping kills all attribution, because the proximal penalty makes it too costly to move $$w$$ at all.

The punchline: for this particular observable ($$\phi = ab$$, which is constant along the orbit), the pseudoinverse gives a clean, minimizer-independent answer and the damping only introduces a spurious dependence. But for an observable that *does* vary along the orbit — say $$\phi(w) = a^{2}$$ — $$\nabla\phi$$ would have a component in the null direction $$(a^{*},-b^{*})$$, the $$1/\lambda$$ term would contribute, and the IF would *diverge* as $$\lambda\to 0$$. In that case damping is not a nuisance but a necessity, and the choice of minimizer genuinely matters. This is the core tension of the proximity gap: it is a distortion for orbit-invariant queries, but a regularizer for orbit-dependent ones.

:::

[^3]: Concretely you can take the eigendecomposition of $$H$$ and only invert the non-zero eigenvalues.

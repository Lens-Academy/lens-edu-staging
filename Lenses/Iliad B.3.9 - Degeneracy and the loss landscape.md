---
id: '535619da-2555-4ff7-bee4-a7fae5af6e8b'
title: "B.3.9 Degeneracy and the loss landscape"
tldr: "Relates degeneracy to the loss landscape: Hessians, regular versus degenerate minima, and when map degeneracy and loss degeneracy do or do not imply each other."
summary_for_tutor: "This is Section 2.5 of worksheet B.3 (singular learning theory). It defines the Hessian H(w) and regular (Morse) versus degenerate minima. It contains Exercises 2.13 (directional derivatives of the loss), 2.14 (the losses a^(2k) + b^(2l)), 2.15 (realisable models: the Bartlett identity gives H(w_0) = I(w_0)) and 2.16 (examples contrasting parametric and loss degeneracy) with hints and collapsed solutions. Keep the notation H, L_{k,l}, w_0. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 2.5 Degeneracy and the loss landscape

In the preceding sections, we studied degeneracy as a property of parameter–function maps and parameter–distribution maps. We now consider the implications of degeneracy in these maps for the *loss landscape* in which deep learning algorithms operate.

Recall the definitions of loss functions from Section 1. In what follows, we assume that the per-example loss $L_{x,y}(w)$ depends on $w$ only through $\Phi(w)$, and work with the population loss $L(w) = {\mathbb{E}}_{(x,y) \sim q}[L_{x,y}(w)]$. For statistical models, we use the expected negative log-likelihood $L(w) = {\mathbb{E}}_{(x,y) \sim q}[-\log p(y \mid x, w)]$ as our loss function. In either case, we assume that $L$ is twice-differentiable with respect to $w$.

Let us begin with some basic observations about the relationship between degeneracy in parameter–function maps and directional derivatives in the loss landscape.

::::callout {title="Exercise" tone="amber"}
**Exercise 2.13 (Directional derivatives of the loss).** Let $L : {\mathcal{W}} \to {\mathbb{R}}$ be a population loss function satisfying the assumptions described above.

**(a)** Show that if $\Phi$ is degenerate at $w$ in direction $v$, then the directional derivative of the loss vanishes in the same direction: $D_{v} L(w) = 0$.

**(b)** Suppose ${\mathcal{W}} = {\mathbb{R}}^{d}$. Show that if $d > 1$, then for *any* $w \in {\mathcal{W}}$, there exists a nonzero $v$ such that $D_{v} L(w) = 0$.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Consider separately the cases $\nabla L(w) = 0$ and $\nabla L(w) \neq 0$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since $L_{x,y}(w)$ depends on $w$ only through $\Phi(w)$, we can write $L_{x,y}(w) = \ell_{x,y}(\Phi(w))$ for some functional $\ell_{x,y}$. If $D_{v}\Phi(w) = 0$, then $\Phi(w + \epsilon v) = \Phi(w) + O(\epsilon^{2})$ as $\epsilon \to 0$, and therefore $L_{x,y}(w + \epsilon v) = \ell_{x,y}(\Phi(w) + O(\epsilon^{2})) = L_{x,y}(w) + O(\epsilon^{2})$. Taking expectations over $(x,y) \sim q$,

$$
L(w + \epsilon v) = L(w) + O(\epsilon^{2}),
$$

so $D_{v} L(w) = \lim_{\epsilon \to 0}\frac{L(w + \epsilon v) - L(w)}{\epsilon\|v\|}= 0$.

**(b)** If $\nabla L(w) = 0$, then $D_{v} L(w) = \frac{v}{\|v\|}\cdot \nabla L(w) = 0$ for every nonzero $v$.

If $\nabla L(w) \neq 0$, the orthogonal complement $\nabla L(w)^{\perp}$ has dimension $d - 1 \geq 1$ (since $d > 1$). Pick any nonzero $v \in \nabla L(w)^{\perp}$. Then $D_{v} L(w) = \frac{v}{\|v\|}\cdot \nabla L(w) = 0$.

:::

We see that parameter–function map degeneracy implies flat loss directions, but a vanishing directional derivative of the loss landscape is commonplace. To find a satisfying definition of degeneracy in a loss landscape, we must look at second-order information.

Define the **Hessian matrix** $H(w) \in {\mathbb{R}}^{d \times d}$ of the loss at $w$ by

$$
H(w)_{jk}= \frac{\partial^{2} L}{\partial w_{j} \partial w_{k}}(w).
$$

The Hessian at $w$ is sometimes denoted $\nabla^{2} L(w)$. The Hessian captures the local curvature of the loss landscape via the quadratic approximation

$$
L(w + \delta) \approx L(w) + \nabla L(w)^{\top} \delta + \tfrac{1}{2}\,\delta^{\top} H(w)\, \delta.
$$

At a critical point ($\nabla L(w) = 0$), the Hessian determines whether the loss curves upward, downward, or remains flat in each direction.

In particular, at a local minimum, $H(w)$ is positive semidefinite. We can therefore classify local minima as follows:

- A local minimum $w$ is **regular** (or **non-degenerate**, or **Morse**) if $H(w)$ is positive definite.
- A local minimum $w$ is **degenerate** (or **non-Morse**) if $H(w)$ is singular (has a zero eigenvalue).

::::callout {title="Exercise" tone="amber"}
**Exercise 2.14 (Some examples of loss landscape degeneracy).** Consider the parameter space ${\mathcal{W}} = {\mathbb{R}}^{2}$ with the identity parameter–function map $\Phi = \mathrm{id}$, so that we identify parameters with the functions they implement (cf., Exercise 2.1). Consider the family of loss functions $L_{k,l}(a,b) = a^{2k}+ b^{2l}$ for non-negative integers $k$ and $l$.

**(a)** Show that the origin is a global minimum of $L_{k,l}$ for all non-negative $k$ and $l$. For which $k$ and $l$ is it the unique global minimum?

**(b)** Show that if $k = l = 1$, then the origin is a non-degenerate (regular) minimum.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Compute the Hessian.

:::

**(c)** Show that if $k > 1$ and $l \geq 1$, then the origin is a degenerate minimum.

**(d)** Show that if $k = 0$ and $l \geq 1$, then the origin is a degenerate minimum.
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since $a^{2k}\geq 0$ and $b^{2l}\geq 0$ for all $a, b \in {\mathbb{R}}$ (using the convention $0^{0} = 1$), we have $L_{k,l}(a,b) \geq 0$ for $k, l \geq 1$, $L_{k,l}(a,b) \geq 1$ if $k = 0$ or $l = 0$, and $L_{k,l}(a,b) = 2$ if $k = l = 0$. At the origin, $L_{k,l}(0,0) = 0^{2k}+ 0^{2l}$, which equals $0$ if $k \geq 1$ and $l \geq 1$, equals $1$ if exactly one of $k, l$ is $0$, and equals $2$ if $k = l = 0$. In each case this matches the lower bound, so the origin is a global minimum.

The origin is the *unique* global minimum if and only if $k \geq 1$ and $l \geq 1$: then $L_{k,l}(a,b) = 0$ requires both $a^{2k}= 0$ and $b^{2l}= 0$, forcing $a = b = 0$. If $k = 0$, then $L_{0,l}(a,0) = 1$ for all $a$, so the entire $a$-axis achieves the minimum. Similarly if $l = 0$. If $k = l = 0$, then all parameters achieve the minimum.

**(b)** For $k = l = 1$: $L_{1,1}(a,b) = a^{2} + b^{2}$. The Hessian at the origin is

$$
H(0,0) = \begin{pmatrix}2 & 0 \\ 0 & 2\end{pmatrix},
$$

which is positive definite. The origin is a non-degenerate minimum.

**(c)** For $k > 1$ and $l \geq 1$: $\frac{\partial^{2} L_{k,l}}{\partial a^{2}}= 2k(2k{-}1)\, a^{2k-2}$. At the origin, $a^{2k-2}= 0$ since $2k - 2 \geq 2$, so this entry vanishes. The Hessian at the origin is therefore

$$
H(0,0) = \begin{pmatrix}0&0 \\ 0&2l(2l{-}1) \cdot 0^{2l-2}\end{pmatrix},
$$

which has a zero eigenvalue (from the first diagonal entry) regardless of the value of the second. The origin is a degenerate minimum.

**(d)** For $k = 0$ and $l \geq 1$: $L_{0,l}(a,b) = 1 + b^{2l}$. Since $L_{0,l}$ is independent of $a$, both $\frac{\partial L}{\partial a}$ and $\frac{\partial^{2} L}{\partial a^{2}}$ vanish identically. The Hessian at the origin has a zero first diagonal entry, so it is singular. The origin is a degenerate minimum.

:::

Note that the Hessian degeneracy in Exercises 2.14(c) and 2.14(d) arises for qualitatively different reasons. In Exercise 2.14(d), the loss is constant along the $a$-direction to all orders—a genuinely flat direction. In Exercise 2.14(c), the loss does increase along the $a$-direction, just more slowly than quadratically (as $a^{4}$, $a^{6}$, etc., depending on $k$). Moreover, different values of $k$ give different rates of increase. The Hessian cannot distinguish any of these cases: flat, quartic, and so on all appear the same from the perspective of the Hessian rank. We will later see approaches that can distinguish these degrees of degeneracy.

So much for defining loss landscape degeneracy. What is the relationship between this kind of degeneracy and degeneracy of the parameter–function/distribution map?

The relationship is subtle, and generally depends on the choice of loss function. One natural setting in which to study this relationship is the *realisable statistical model:* given a parameter–distribution map and a parameter $w_{0}$, if we consider $p_{w_0}$ as the true data-generating distribution, the population negative log-likelihood loss will have a global minimum at $w_{0}$. The following exercise shows that in this setting, under mild regularity assumptions on the statistical model, degeneracy in the parameter–distribution map at $w_{0}$ implies that the global minimum $w_{0}$ is a degenerate global minimum of the loss landscape.

::::callout {title="Exercise" tone="amber"}
**Exercise 2.15 (Realisable models and Hessian degeneracy).** Let $\Psi : {\mathcal{W}} \to {\mathcal{D}}$ be a parameter–distribution map with positive densities $p(y \mid x, w)$, twice-differentiable in $w$. Suppose data is generated from a fixed true parameter $w_{0} \in {\mathcal{W}}$, meaning $q(y \mid x) = p(y \mid x, w_{0})$. Consider the population negative log-likelihood loss

$$
L(w) = -{\mathbb{E}}_{x \sim q(x)}\, {\mathbb{E}}_{y \sim p(y \mid x, w_0)}\!\bigl[\log p(y \mid x, w)\bigr].
$$

Assume that for each $x$, the operations $\nabla_{w}$ (and $\nabla_{w}^{2}$) and $\int_{{\mathcal{Y}}} \cdot\, dy$ may be exchanged.

**(a)** *(Bartlett identity.)* Show that for each $x \in {\mathcal{X}}$ and $w \in {\mathcal{W}}$,

$$
-{\mathbb{E}}_{y \sim p(y \mid x, w)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr] = {\mathbb{E}}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr],
$$

where $s$ is the score function from Definition 2.3.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Differentiate the identity ${\mathbb{E}}_{y \sim p(y \mid x, w)}[s(x, y, w)] = 0$ (established in Exercise 2.11) with respect to $w$.

:::

**(b)** Show that the Hessian of $L$ at the true parameter $w_{0}$ equals the Fisher information matrix (Definition 2.4):

$$
H(w_{0}) = I(w_{0}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Compute $H(w) = -{\mathbb{E}}_{x}\, {\mathbb{E}}_{y \sim p(y \mid x, w_0)}[\nabla_{w}^{2} \log p(y \mid x, w)]$, evaluate at $w = w_{0}$, and apply part (a).

:::

**(c)** Using the result of Exercise 2.12, conclude: if $\Psi$ is degenerate at $w_{0}$ in direction $v$, then $H(w_{0})\, v = 0$. Contrapositively, if $H(w_{0})$ is positive definite, then $\Psi$ is non-degenerate at $w_{0}$.
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** From Exercise 2.11, ${\mathbb{E}}_{y \sim p(y \mid x, w)}[s_{j}(x,y,w)] = 0$ for each component $j$ of the score, where $s_{j} = \frac{\partial}{\partial w_{j}}\log p(y \mid x, w)$. Differentiating with respect to $w_{k}$ and exchanging the derivative with the integral:

$$
\begin{aligned}0&= \frac{\partial}{\partial w_{k}}\int_{{\mathcal{Y}}} s_{j}(x,y,w)\, p(y \mid x, w)\, dy \\&= \int_{{\mathcal{Y}}} \frac{\partial s_{j}}{\partial w_{k}}\, p\, dy + \int_{{\mathcal{Y}}} s_{j}\, \frac{\partial p}{\partial w_{k}}\, dy. \quad\text{(product rule)}\end{aligned}
$$

Using the score identity $\frac{\partial p}{\partial w_{k}}= p \cdot s_{k}$ (24), the second integral becomes $\int_{{\mathcal{Y}}} s_{j}\, s_{k}\, p\, dy = {\mathbb{E}}_{y}[s_{j}\, s_{k}]$. Therefore

$$
{\mathbb{E}}_{y \sim p(y \mid x, w)}\!\left[ \frac{\partial^{2} \log p}{\partial w_{j} \partial w_{k}}\right] = -{\mathbb{E}}_{y \sim p(y \mid x, w)}[s_{j}\, s_{k}].
$$

Assembling all components into a matrix gives

$$
-{\mathbb{E}}_{y \sim p(y \mid x, w)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr] = {\mathbb{E}}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr].
$$

**(b)** The population negative log-likelihood is $L(w) = -{\mathbb{E}}_{x \sim q(x)}\, {\mathbb{E}}_{y \sim p(y \mid x, w_0)}[\log p(y \mid x, w)]$. Taking the Hessian with respect to $w$ (exchanging differentiation and integration):

$$
H(w) = -{\mathbb{E}}_{x \sim q(x)}\, {\mathbb{E}}_{y \sim p(y \mid x, w_0)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr].
$$

At $w = w_{0}$, the inner expectation is over $y \sim p(y \mid x, w_{0})$, which matches the distribution in the Bartlett identity. Applying part (a):

$$
\begin{aligned}H(w_{0})&= {\mathbb{E}}_{x \sim q(x)}\, {\mathbb{E}}_{y \sim p(y \mid x, w_0)}\!\bigl[ s(x,y,w_{0})\, s(x,y,w_{0})^{\top} \bigr] \\&= I(w_{0}). \quad\text{(by Definition 2.4)}\end{aligned}
$$

**(c)** By Exercise 2.12, $\ker I(w_{0}) = \{v \in {\mathbb{R}}^{d} : D_{v} \Psi(w_{0}) = 0\}$. Since $H(w_{0}) = I(w_{0})$, if $\Psi$ is degenerate at $w_{0}$ in direction $v$, then $v \in \ker I(w_{0}) = \ker H(w_{0})$, so $H(w_{0})\, v = 0$.

Contrapositively: if $H(w_{0})$ is positive definite, then $\ker H(w_{0}) = \{0\}$, so $\ker I(w_{0}) = \{0\}$, and $\Psi$ is non-degenerate at $w_{0}$.

:::

Exercise 2.15 shows that for the population negative log-likelihood at the true parameter, degeneracy of the parameter–distribution map implies a degenerate loss landscape. The converse does not hold in general, nor does the forward direction hold at arbitrary points in parameter space. The following exercise explores these subtleties through examples.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.16 (Contrasting parametric versus loss degeneracy).** **(a)** Observe that the identity parameter–function map on ${\mathcal{W}} = {\mathbb{R}}^{2}$ is non-degenerate everywhere. With this in mind, what do your answers to Exercises 2.14(b), 2.14(c) and 2.14(d) exemplify about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy?

**(b)** Consider again the identity parameter–function map on ${\mathcal{W}} = {\mathbb{R}}^{2}$. Consider the loss function $L_{\circ}(a,b) = (a^{2} + b^{2} - 1)^{2}$. Find a global minimum of $L_{\circ}$ and show that it is a degenerate critical point. What does this example reveal about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy?

**(c)** Now consider the cubic parameter–function map $\Phi(\alpha, \beta) = (\alpha^{3}, \beta^{3})$.
1. Argue that $\Phi$ is degenerate at the origin (cf., Exercise 2.2).
2. If we take $L_{k,l}$ from Exercise 2.14 to be defined on the constant function $(a, b)$ (rather than the equivalent underlying parameter), then in this parameterisation, that loss function becomes $L_{k,l}(\alpha,\beta) = (\alpha^{3})^{2k}+ (\beta^{3})^{2l}$. Show that the origin is a degenerate minimum of $L_{k,l}$ for all $k \geq 0$ and $l \geq 0$ under this parametrisation.
3. What does this example reveal about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy?

**(d)** Consider the product parameter–function map $\Phi(a,b) = a \cdot b$ from Exercise 2.3, and define $L(a,b) = \frac{1}{2}(ab - 1)^{2}$.
1. Show that $(0,0)$ is a critical point and that $\Phi$ is degenerate in every direction at $(0,0)$.
2. Compute the Hessian at $(0,0)$ and show it is nonsingular.
3. What does this example reveal about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy? Why does this not contradict Exercise 2.15?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The identity parameter–function map $\Phi(a,b) = (a,b)$ has Jacobian equal to the $2 \times 2$ identity matrix everywhere, so it is non-degenerate at every point. Exercise 2.14(b) shows that $L_{1,1}$ has a non-degenerate minimum: absence of parameter–function map degeneracy is consistent with absence of loss landscape degeneracy. Exercises 2.14(c) and 2.14(d) show that $L_{2,1}$, $L_{0,1}$, etc., have degenerate minima despite the parameter–function map being non-degenerate. This demonstrates that loss landscape degeneracy does not imply parameter–function map degeneracy.

**(b)** $L_{\circ}(a,b) = (a^{2} + b^{2} - 1)^{2} \geq 0$, with equality if and only if $a^{2} + b^{2} = 1$. So every point on the unit circle is a global minimum. Consider $(1, 0)$. The gradient is

$$
\nabla L_{\circ} = \bigl(4a(a^{2} + b^{2} - 1),\; 4b(a^{2} + b^{2} - 1)\bigr),
$$

which vanishes at $(1, 0)$. The Hessian entries at $(1, 0)$ are:

$$
\begin{aligned}\frac{\partial^{2} L_{\circ}}{\partial a^{2}}&= 4(3a^{2} + b^{2} - 1) = 8,&\qquad \frac{\partial^{2} L_{\circ}}{\partial b^{2}}&= 4(a^{2} + 3b^{2} - 1) = 0, \\ \frac{\partial^{2} L_{\circ}}{\partial a\, \partial b}&= 8ab = 0.\end{aligned}
$$

So $H(1,0) = \mathrm{diag}(8, 0)$, which is singular. Therefore, $(1,0)$ is a degenerate minimum.

This provides another example of loss landscape degeneracy without parameter–function map degeneracy: the identity parameter–function map is non-degenerate, but the circle of global minima creates a flat tangential direction.

**(c)**
1. The map $\Phi(\alpha, \beta) = (\alpha^{3}, \beta^{3})$ is the product of two copies of the cubic parametrisation from Exercise 2.2. In each component, the derivative $\frac{d}{d\alpha}(\alpha^{3}) = 3\alpha^{2}$ vanishes at $\alpha = 0$. Therefore both coordinate directions are degenerate at the origin, and hence every direction is degenerate at the origin (since the Jacobian $\mathrm{diag}(3\alpha^{2}, 3\beta^{2})$ is the zero matrix there).
2. In the new parametrisation, the loss becomes $L_{k,l}(\alpha,\beta) = (\alpha^{3})^{2k}+ (\beta^{3})^{2l}= \alpha^{6k}+ \beta^{6l}$.

If $k \geq 1$ and $l \geq 1$: the exponents $6k$ and $6l$ are both at least $6$, so $\frac{\partial^{2} L}{\partial \alpha^{2}}\big|_{0} = 6k(6k{-}1) \cdot 0^{6k-2}= 0$ (since $6k - 2 \geq 4$), and similarly for $\beta$. The Hessian at the origin is the zero matrix, which is singular.

If $k = 0$: $L_{0,l}(\alpha,\beta) = 1 + \beta^{6l}$, which is independent of $\alpha$, so the Hessian has a zero first diagonal entry. Similarly if $l = 0$. In all cases, the origin is a degenerate minimum.
3. Under the identity parameter–function map, $L_{1,1}(a,b) = a^{2} + b^{2}$ had a non-degenerate minimum at the origin (Exercise 2.14(b)). Under the cubic parameter–function map, the same loss became $\alpha^{6} + \beta^{6}$, which has a degenerate minimum at the origin. This shows that introducing degeneracy into the parameter–function map can convert a non-degenerate minimum into a degenerate one.

For other $k,l$, $L_{k,l}$ was already degenerate at the origin under the non-degenerate parameterisation, the cubic function only makes it *more* degenerate (in terms of the order to which the loss vanishes in the degenerate direction(s); we will formally quantify this in Section 3).

**(d)**
1. The gradient is $\nabla L = (ab - 1)(b,\, a)$. At $(0, 0)$: $\nabla L = (0 - 1)(0, 0) = (0, 0)$. So $(0, 0)$ is a critical point.

The Jacobian of $\Phi(a,b) = ab$ is $(b, a)$, which at $(0, 0)$ is $(0, 0)$. Every direction $v = (v_{1}, v_{2})$ gives $J v = b v_{1} + a v_{2} = 0$, so $\Phi$ is degenerate in every direction at $(0, 0)$.
2. Computing second partial derivatives:

$$
\begin{aligned}\frac{\partial^{2} L}{\partial a^{2}}&= b^{2},&\qquad \frac{\partial^{2} L}{\partial b^{2}}&= a^{2},&\qquad \frac{\partial^{2} L}{\partial a\, \partial b}&= 2ab - 1.\end{aligned}
$$

At $(0, 0)$:

$$
H(0,0) = \begin{pmatrix}0 & -1 \\ -1 & 0\end{pmatrix},
$$

which has determinant $-1 \neq 0$ (eigenvalues $\pm 1$). The Hessian is nonsingular.
3. Despite full degeneracy of the parameter–function map at $(0,0)$, the Hessian is nonsingular (in fact indefinite, so $(0,0)$ is a saddle point, not a local minimum). This shows that parameter–function map degeneracy does not in general imply loss landscape degeneracy.

This does not contradict Exercise 2.15, which establishes $H(w_{0}) = I(w_{0})$ at the *true parameter* $w_{0}$, meaning $\Phi(w_{0})$ must equal the target. Here, $\Phi(0,0) = 0 \neq 1$, so $(0,0)$ is not the true parameter, and the identity does not apply.

:::

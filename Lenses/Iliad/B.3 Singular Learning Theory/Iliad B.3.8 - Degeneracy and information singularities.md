---
id: '40435bd2-e092-44ed-9e9a-45ddf932152f'
title: "B.3.8 Degeneracy and information singularities"
tldr: "Extends degeneracy to parameter-distribution maps and proves that the Fisher information matrix is singular exactly when the map is degenerate."
summary_for_tutor: "This is Section 2.4 of worksheet B.3 (singular learning theory). It defines degeneracy of a parameter-distribution map Psi, Definition 2.3 (score function and directional score) and Definition 2.4 (Fisher information matrix I(w)). It contains Exercises 2.11 (properties of the score function) and 2.12 (the kernel of I(w) equals the set of degenerate directions) with hints and collapsed solutions, and a remark on Watanabe's strictly singular models. Keep the notation s, s_v, I(w). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Kai Ogden (University of Oxford)
  - Matthew Farrugia-Roberts (University of Oxford)
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/singular-learning-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 2.4 Degeneracy and information singularities

In the preceding sections, we studied degeneracy as a property of parameter–function maps. In the statistical framework introduced in Section 1.3, the fundamental object is instead a parameter–distribution map $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$ ($$w \mapsto p_{w} : {\mathcal{X}} \to \Delta({\mathcal{Y}})$$). In this section, we extend the definition of degeneracy to parameter–distribution maps and connect it to a classical quantity from statistics, the Fisher information matrix. We will show that under mild regularity conditions on the statistical model, the Fisher information matrix is singular at $$w$$ (has zero eigenvalues) if and only if the parameter–distribution map is degenerate at $$w$$.

Given a parameter–distribution map $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$, say that $$\Psi$$ is **degenerate at $$w$$ in direction $$v$$** if the conditional density does not change to first order:

$$
D_{v} \Psi(w) = 0.
$$

Here, $$D_{v} \Psi(w)$$ is not a conditional distribution but a signed difference between conditional distributions, effectively a real function of $$x$$ and $$y$$ (in particular, it may include negative density changes). We mean that this function is zero for all $$x \in {\mathcal{X}}$$ and all $$y \in {\mathcal{Y}}$$.

Equation 21 extends the definition of degeneracy from Equation 19. If $$\Psi$$ is constructed from a parameter–function map $$\Phi$$ via a noise model (as in Section 1.3), then degeneracy of $$\Phi$$ at $$w$$ in direction $$v$$ implies degeneracy of $$\Psi$$ at $$w$$ in direction $$v$$, since $$p(y \mid x, w)$$ depends on $$w$$ only through $$f_{w}(x)$$.

To relate degeneracy to the Fisher information matrix, we introduce two standard definitions.

:::callout {title="Definition" tone="blue"}

**Definition 2.3 (Score function).** Let $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$ be a parameter–distribution map with densities $$p(y \mid x, w)$$ that are positive and differentiable in $$w$$. The **score function** at $$w$$ is

$$
s(x, y, w) = \nabla_{w} \log p(y \mid x, w) \in {\mathbb{R}}^{d}.
$$

The **directional score** in non-zero direction $$v \in {\mathbb{R}}^{d}$$ is

$$
s_{v}(x, y, w) = D_{v} \log p(y \mid x, w) = \frac{v}{\|v\|}\cdot \nabla_{w} \log p(y \mid x, w).
$$

The directional score measures how sensitive the log-density is to perturbations of $$w$$ in direction $$v$$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 2.11 (Basic properties of the score function).** Let $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$ be a parameter–distribution map with positive densities $$p(y \mid x, w)$$, differentiable in $$w$$. Assume that for each $$x$$ and $$w$$, the operations $$\nabla_{w}$$ and $$\int_{{\mathcal{Y}}} \cdot\, dy$$ may be exchanged.

**(a)** Show that the score function satisfies the following identity: for each $$x \in {\mathcal{X}}$$, $$y \in {\mathcal{Y}}$$, and $$w \in {\mathcal{W}}$$,

$$
s(x,y,w) = \frac{\nabla_{w} p(y \mid x,w)}{p(y \mid x,w)}.
$$

**(b)** Show that the expected score is zero: for each $$x \in {\mathcal{X}}$$ and $$w \in {\mathcal{W}}$$,

$$
{\mathbb{E}}_{y \sim p(y \mid x, w)}\bigl[s(x, y, w)\bigr] = 0.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Differentiate the identity $$\int_{{\mathcal{Y}}} p(y \mid x, w) \, dy = 1$$.

:::

**(c)** Show that if $$\Psi$$ is degenerate at $$w$$ in direction $$v$$, then the directional score vanishes identically: $$s_{v}(x, y, w) = 0$$ for all $$x \in {\mathcal{X}}$$ and $$y \in {\mathcal{Y}}$$.

**(d)** Show the converse: if the directional score $$s_{v}(x, y, w)$$ vanishes for all $$x \in {\mathcal{X}}$$ and $$y \in {\mathcal{Y}}$$ at $$w$$, then $$\Psi$$ is degenerate at $$w$$ in direction $$v$$.
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since $$p(y \mid x, w) > 0$$, the logarithm is well-defined and the chain rule gives

$$
\nabla_{w} \log p(y \mid x, w) = \frac{\nabla_{w} p(y \mid x, w)}{p(y \mid x, w)}.
$$

The left-hand side is $$s(x,y,w)$$ by definition.

**(b)** Differentiate the normalisation identity $$\int_{{\mathcal{Y}}} p(y \mid x, w) \, dy = 1$$ with respect to $$w$$:

$$
0 = \nabla_{w} \int_{{\mathcal{Y}}} p(y \mid x, w) \, dy = \int_{{\mathcal{Y}}} \nabla_{w} p(y \mid x, w) \, dy.
$$

By part (a), $$\nabla_{w} p = p \cdot s$$, so

$$
0 = \int_{{\mathcal{Y}}} p(y \mid x, w)\, s(x, y, w) \, dy = {\mathbb{E}}_{y \sim p(y \mid x, w)}\bigl[s(x, y, w)\bigr].
$$

**(c)** If $$D_{v} \Psi(w) = 0$$, then by the definition of degeneracy (21), $$D_{v} p(y \mid x, w) = 0$$ for all $$x, y$$. By part (a), $$\nabla_{w} p = p \cdot s$$, so contracting both sides with $$v / \|v\|$$ gives $$D_{v} p = p \cdot s_{v}$$. Since $$p > 0$$, we conclude $$s_{v}(x, y, w) = 0$$ for all $$x, y$$.

**(d)** If $$s_{v}(x, y, w) = 0$$ for all $$x, y$$, then by part (a),

$$
D_{v} p(y \mid x, w) = p(y \mid x, w) \cdot s_{v}(x, y, w) = 0
$$

for all $$x, y$$ (using $$p > 0$$). That is, $$D_{v} \Psi(w) = 0$$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 2.4 (Fisher information matrix).** Let $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$ be a parameter–distribution map with score function $$s$$. Let $$q(x)$$ denote the marginal distribution of inputs. The **Fisher information matrix** $$I : {\mathcal{W}} \to {\mathbb{R}}^{d \times d}$$ is defined by

$$
I(w) = {\mathbb{E}}_{x \sim q(x)}\, {\mathbb{E}}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr].
$$

:::

The Fisher information matrix is symmetric and positive semidefinite at every $$w$$ (being an expectation of positive semidefinite matrices $$s\, s^{\top}$$). However, the Fisher information matrix may not be symmetric positive *definite,* that is, it may be singular.

The following exercise shows that singularity of the Fisher information matrix is equivalent to degeneracy of the parameter–distribution map under mild regularity conditions.

::::callout {title="Exercise" tone="amber"}
**Exercise 2.12 (Fisher information and degeneracy).** Let $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$ be a parameter–distribution map with densities $$p(y \mid x, w)$$. Assume that $$p(y \mid x, w) > 0$$ for all $$y \in {\mathcal{Y}}$$, $$x \in {\mathcal{X}}$$, $$w \in {\mathcal{W}}$$, that $$w \mapsto p(y \mid x, w)$$ is differentiable, and that $$q(x) > 0$$ for all $$x \in {\mathcal{X}}$$.

**(a)** Show that for any unit vector $$v \in {\mathbb{R}}^{d}$$,

$$
v^{\top} I(w)\, v = {\mathbb{E}}_{x \sim q(x)}\, {\mathbb{E}}_{y \sim p(y \mid x, w)}\!\bigl[ s_{v}(x, y, w)^{2} \bigr].
$$

**(b)** Using Exercise 2.11(c), show that if $$D_{v} \Psi(w) = 0$$ for some non-zero $$v$$, then $$I(w)$$ is not positive definite.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Check the definition of positive definite.

:::

**(c)** Using Exercise 2.11(d), show that if $$I(w)$$ is not positive definite, then there exists a non-zero $$v$$ for which $$D_{v} \Psi(w) = 0$$.
:::callout {title="Hint" tone="neutral" collapse="closed"}

Check the definition of positive definite.

:::

**(d)** Conclude that

$$
\ker I(w) = \bigl\{v \in {\mathbb{R}}^{d} : D_{v} \Psi(w) = 0\bigr\}.
$$

That is, the null space of the Fisher information matrix is exactly the space of degenerate directions of the parameter–distribution map.
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since $$v$$ is a unit vector, $$s_{v} = D_{v} \log p = \frac{v}{\|v\|}\cdot s = v \cdot s$$. From the definition of $$I(w)$$ in (26),

$$
\begin{aligned}v^{\top} I(w)\, v&= v^{\top} {\mathbb{E}}_{x,y}\!\bigl[s\, s^{\top}\bigr]\, v = {\mathbb{E}}_{x,y}\!\bigl[(v \cdot s)^{2}\bigr] = {\mathbb{E}}_{x,y}\!\bigl[s_{v}^{2}\bigr] \\&= {\mathbb{E}}_{x \sim q(x)}\, {\mathbb{E}}_{y \sim p(y \mid x, w)}\!\bigl[ s_{v}(x,y,w)^{2} \bigr].\end{aligned}
$$

**(b)** If $$D_{v} \Psi(w) = 0$$ for some non-zero $$v$$, then by Exercise 2.11(c), $$s_{v}(x,y,w) = 0$$ for all $$x, y$$. Let $$\hat{v}= v / \|v\|$$. Then $$s_{\hat{v}}= s_{v}$$ (the directional derivative is invariant to the magnitude of $$v$$), so by part (a), $$\hat{v}^{\top} I(w)\, \hat{v}= {\mathbb{E}}[s_{\hat{v}}^{2}] = 0$$. A matrix $$M$$ is positive definite only if $$u^{\top} M u > 0$$ for all non-zero $$u$$. Since $$\hat{v}$$ is a non-zero vector with $$\hat{v}^{\top} I(w)\, \hat{v}= 0$$, the matrix $$I(w)$$ is not positive definite.

**(c)** If $$I(w)$$ is not positive definite, then since $$I(w)$$ is positive semidefinite, there exists a non-zero vector $$\hat{v}$$ such that $$\hat{v}^{\top} I(w)\, \hat{v}= 0$$. By part (a) (taking $$\hat{v}$$ to be a unit vector without loss of generality), $${\mathbb{E}}[s_{\hat{v}}^{2}] = 0$$. Since $$s_{\hat{v}}^{2} \geq 0$$ and $$q(x) > 0$$ and $$p(y \mid x, w) > 0$$, this implies $$s_{\hat{v}}(x,y,w) = 0$$ for all $$x \in {\mathcal{X}}$$ and $$y \in {\mathcal{Y}}$$. By Exercise 2.11(d), $$D_{\hat{v}}\Psi(w) = 0$$.

**(d)** Parts (b) and (c) show that $$I(w)$$ is positive definite if and only if $$\Psi$$ is non-degenerate at $$w$$, or equivalently, $$I(w)$$ is singular if and only if $$\Psi$$ is degenerate at $$w$$.

For the kernel characterisation: clearly $$0 \in \ker I(w)$$. For non-zero $$v$$, $$v \in \ker I(w)$$ means $$I(w)\,v = 0$$, which (since $$I(w)$$ is positive semidefinite) is equivalent to $$v^{\top} I(w)\, v = 0$$. Normalising to $$\hat{v}= v/\|v\|$$, part (a) gives $${\mathbb{E}}[s_{\hat{v}}^{2}] = 0$$, which as in part (c) implies $$s_{\hat{v}}= 0$$ everywhere. By Exercise 2.11(d), $$D_{\hat{v}}\Psi(w) = 0$$, and hence $$D_{v} \Psi(w) = 0$$. Conversely, if $$D_{v} \Psi(w) = 0$$ for non-zero $$v$$, then Exercise 2.11(c) gives $$s_{v} = 0$$, so $$v^{\top} I(w)\, v = \|v\|^{2} {\mathbb{E}}[s_{v}^{2}] = 0$$, hence $$I(w)\, v = 0$$. Therefore $$\ker I(w) = \{v \in {\mathbb{R}}^{d} : D_{v} \Psi(w) = 0\}$$.

:::

:::callout {title="Note" tone="blue"}

**Remark (Watanabe's strictly singular models).** Watanabe 2009 defines a statistical model as *strictly singular* if either of two conditions hold:

1. The Fisher information matrix $$I(w)$$ is singular for some $$w \in {\mathcal{W}}$$.
2. The parameter–distribution map is not one-to-one, that is, for some $$w, w' \in {\mathcal{W}}$$ such that $$w \neq w'$$, we have $$\Psi(w) = \Psi(w')$$.

By Exercise 2.12, under mild regularity conditions, the first condition is equivalent to our notion of (somewhere) degeneracy. The second condition is called non-identifiability.

Watanabe 2007; Watanabe 2009 observe that many of the results from classical statistics crucially assume among their regularity conditions the parameter–distribution map is identifiable and the Fisher information matrix is nonsingular. Whereas, in a statistical model based on a non-trivial neural network (or any other statistical model involving hierarchical structure), it is typical for the Fisher information matrix to include singularities.

:::

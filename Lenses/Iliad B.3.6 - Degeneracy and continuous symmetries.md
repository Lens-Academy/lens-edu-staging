---
id: 'b0ac1f34-462c-45e8-9802-94f6e36ee223'
title: "B.3.6 Degeneracy and continuous symmetries"
tldr: "Shows how continuous symmetries of a parameter-function map give degenerate directions, with ReLU scaling and linear autoencoder rotation examples."
summary_for_tutor: "This is Section 2.2 of worksheet B.3 (singular learning theory). It defines symmetry and continuous symmetry {T_t}, trivial versus non-trivial at w, Proposition 2.1 (a non-trivial continuous symmetry at w implies degeneracy at w, with proof) and Corollary 2.2. It contains Exercises 2.5 (the a+b translation symmetry), 2.6 (ReLU scaling symmetry) and 2.7 (rotation symmetry in a linear autoencoder, with a hint) with collapsed solutions. Keep the notation T_t and Phi. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 2.2 Degeneracy and continuous symmetries

A common source of degeneracy in neural network architectures is the presence of continuous symmetries of the parameter–function map. A continuous symmetry traces out a curve of functionally equivalent parameters. The tangent to this curve is a degenerate direction. In this section, we will explore this kind of symmetry and some examples from deep learning.

A **symmetry** of a parameter–function map $\Phi$ is a transformation of parameter space that maps parameters while preserving the implemented function. That is, a transformation $T : {\mathcal{W}} \to {\mathcal{W}}$ is a symmetry if for all $w \in {\mathcal{W}}$, we have $\Phi(w) = \Phi(T(w))$ ($f_{w} = f_{T(w)}$).

A **continuous symmetry** of a parameter–function map $\Phi$ is a family of transformations $\{T_{t} : {\mathcal{W}} \to {\mathcal{W}}\}_{t \in {\mathbb{R}}}$ indexed by a parameter $t\in{\mathbb{R}}$, such that

1. $T_{t}$ is a symmetry ($\Phi \circ T_{t} = \Phi$) for all $t \in {\mathbb{R}}$,
2. $T_{0}$ is the identity transformation on ${\mathcal{W}}$, and
3. The map $t \mapsto T_{t}(w)$ is differentiable for each $w \in {\mathcal{W}}$.

The continuous symmetry is **trivial at $w$** if $\left.\frac{d}{dt}\right|_{t=0}T_{t}(w) = 0$, or else **non-trivial at $w$**.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.5 (Continuous symmetry example).** Recall the parameter–function map from Exercise 2.4, with ${\mathcal{W}} = {\mathbb{R}}^{2}$ and with $(a, b) \in {\mathcal{W}}$ mapping to the constant function $f_{a,b}= a + b$. Consider the family of transformations $T_{t} : {\mathcal{W}} \to {\mathcal{W}}$ for $t \in {\mathbb{R}}$ such that

$$
T_{t}(a, b) = (a + t, b - t).
$$

**(a)** Describe the effect of this family of transformations on the parameter space.

**(b)** Show that this family of transformations is a continuous symmetry.

**(c)** Show that this continuous symmetry is non-trivial everywhere.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The transformation $T_{t}$ translates the parameter $(a, b)$ by $t$ in the direction $(1, -1)$. The orbit of any parameter $(a, b)$ under this family is the line $\{(a + t, b - t) : t \in {\mathbb{R}}\}$, which has slope $-1$ in the $(a, b)$-plane.

**(b)** We verify the three conditions of a continuous symmetry.
1. Symmetry: $\Phi(T_{t}(a, b)) = (a + t) + (b - t) = a + b = \Phi(a, b)$ for all $(a, b)$ and $t$.
2. Identity: $T_{0}(a, b) = (a + 0, b - 0) = (a, b)$.
3. Differentiability: $t \mapsto T_{t}(a, b) = (a + t, b - t)$ is linear in $t$, hence differentiable.

**(c)** We have $\frac{d}{dt}T_{t}(a, b) = (1, -1)$ for all $t$. In particular, $\left.\frac{d}{dt}\right|_{t=0}T_{t}(a, b) = (1, -1) \neq (0, 0)$ for every $(a, b) \in {\mathcal{W}}$. So the symmetry is non-trivial at every parameter.

:::

At each parameter, a non-trivial continuous symmetry traces out a curve of functionally equivalent parameters. This indicates the presence of a direction in parameter space in which the function does not change. The following proposition formalises this connection between continuous symmetries and degeneracy.

:::callout {title="Theorem" tone="green"}

**Proposition 2.1.** If a parameter–function map $\Phi$ admits a continuous symmetry $\{T_{t}\}$ that is non-trivial at $w$, then $\Phi$ is degenerate at $w$.

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

Define the curve in parameter space traced by the continuous symmetry, $\gamma : {\mathbb{R}} \to {\mathcal{W}}$ with $\gamma(t) = T_{t}(w)$. Fix $t_{0} \in {\mathbb{R}}$. Since $T_{t}$ is a continuous symmetry, the derivative along the curve at $t_{0}$ vanishes:

$$
\begin{aligned}D_{\gamma'(t_0)}\Phi(\gamma(t_{0}))&\propto \gamma'(t_{0}) \cdot \nabla \Phi(\gamma(t_{0})) \\&= \left.\frac{d}{dt}\right|_{t=t_0}\Phi(\gamma(t)) \quad\text{(chain rule)}\\&= \left.\frac{d}{dt}\right|_{t=t_0}\Phi(w) \quad\text{(symmetry, $\Phi \circ T_{t} = \Phi$)}\\&= 0. \quad\text{($\Phi(w)$ is constant in $t$)}\end{aligned}
$$

In particular, at $t=0$, we have $0 = D_{\gamma'(0)}\Phi(\gamma(0)) = D_{\gamma'(0)}\Phi(w)$ since $\gamma(0) = w$ by identity. Since $T_{t}$ is non-trivial at $w$, $\gamma'(0)$ is non-zero, so $\gamma'(0)$ is a degenerate direction at $w$.

:::

:::callout {title="Theorem" tone="green"}

**Corollary 2.2.** If a parameter–function map $\Phi$ admits a continuous symmetry $\{T_{t}\}$ that is non-trivial at every parameter $w \in {\mathcal{W}}$, then $\Phi$ is everywhere degenerate.

:::

The following exercises exhibit some continuous symmetries in two neural network architectures, a small ReLU MLP and a toy autoencoder. Similar architectures are studied in more detail from an SLT perspective by Carroll 2021 and Chen et al. 2023 respectively.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.6 (ReLU scaling symmetry).** Consider a two-layer MLP (Example 1.4) with $\sigma = {\mathrm{relu}}$, scalar inputs and outputs ($m = 1$), and a single hidden unit ($h = 1$). The parameter space is ${\mathcal{W}} = {\mathbb{R}}^{2}$ with parameters $(a, b)$, and the parameter–function map is $f_{a,b}(x) = b \cdot {\mathrm{relu}}(ax)$.

**(a)** Show that ${\mathrm{relu}}$ is *positively homogeneous*: ${\mathrm{relu}}(\alpha z) = \alpha \, {\mathrm{relu}}(z)$ for all $\alpha > 0$ and $z \in {\mathbb{R}}$.

**(b)** Define $T_{t}(a, b) = (e^{t} a, \, e^{-t}b)$ for $t \in {\mathbb{R}}$. Show that $\{T_{t}\}$ is a continuous symmetry of this parameter–function map.

**(c)** For a fixed parameter $(a, b) \neq (0, 0)$, compute the degenerate direction arising from this symmetry at $(a, b)$.

**(d)** Show that the symmetry is trivial at the origin. Is this parameter–function map degenerate at the origin?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** We consider three cases. If $z > 0$, then $\alpha z > 0$ (since $\alpha > 0$), so ${\mathrm{relu}}(\alpha z) = \alpha z = \alpha {\mathrm{relu}}(z)$. If $z = 0$, then ${\mathrm{relu}}(\alpha \cdot 0) = 0 = \alpha \cdot 0 = \alpha {\mathrm{relu}}(z)$. If $z < 0$, then $\alpha z < 0$, so ${\mathrm{relu}}(\alpha z) = 0 = \alpha \cdot 0 = \alpha {\mathrm{relu}}(z)$.

**(b)** We verify the three conditions.
1. Symmetry: using positive homogeneity with $\alpha = e^{t} > 0$,

$$
f_{T_t(a,b)}(x) = e^{-t}b \cdot {\mathrm{relu}}(e^{t} a x) = e^{-t}b \cdot e^{t} {\mathrm{relu}}(ax) = b \cdot {\mathrm{relu}}(ax) = f_{a,b}(x).
$$
2. Identity: $T_{0}(a, b) = (e^{0} a,\, e^{0} b) = (a, b)$.
3. Differentiability: $t \mapsto (e^{t} a,\, e^{-t}b)$ is smooth.

**(c)** The degenerate direction at $(a, b)$ is

$$
\left.\frac{d}{dt}\right|_{t=0}T_{t}(a, b) = \left.\frac{d}{dt}\right|_{t=0}(e^{t} a,\, e^{-t}b) = (a, -b).
$$

Since $(a, b) \neq (0, 0)$, we have $(a, -b) \neq (0, 0)$, so this is a non-zero degenerate direction.

**(d)** At $(a, b) = (0, 0)$, we have $\left.\frac{d}{dt}\right|_{t=0}T_{t}(0, 0) = (0, 0)$, so the symmetry is trivial.

The parameter–function map is nonetheless degenerate at the origin. Both partial derivatives of $\Phi$ vanish there:

$$
\begin{aligned}\frac{\partial}{\partial a}f_{a,b}(x) \bigg|_{(0,0)}&= \lim_{\epsilon \to 0}\frac{f_{\epsilon, 0}(x) - f_{0,0}(x)}{\epsilon}= \lim_{\epsilon \to 0}\frac{0 \cdot {\mathrm{relu}}(\epsilon x)}{\epsilon}= 0, \\ \frac{\partial}{\partial b}f_{a,b}(x) \bigg|_{(0,0)}&= {\mathrm{relu}}(0 \cdot x) = 0.\end{aligned}
$$

Since $\nabla \Phi(0,0) = 0$, every direction is degenerate at the origin. This degeneracy is not explained by the scaling symmetry.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 2.7 (Rotation symmetry in a linear autoencoder).** Consider a *linear autoencoder* with bottleneck dimension $h$ and ambient dimension $m \geq h$. The parameter space encodes a single matrix $W \in {\mathbb{R}}^{h \times m}$ and the parameter–function map sends $W$ to the function $\Phi(W) = f_{W} : {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$ where

$$
f_{W}(x) = W^{\top} W x
$$

for $x \in {\mathbb{R}}^{m}$. Here, $W$ serves simultaneously as encoder ($x \mapsto Wx \in {\mathbb{R}}^{h}$) and decoder ($z \mapsto W^{\top} z \in {\mathbb{R}}^{m}$).

**(a)** Show that for any orthogonal matrix $R \in {\mathbb{R}}^{h \times h}$ (i.e., any $h \times h$ matrix such that $R^{\top} R = I$), the map $T_{R}(W) = RW$ is a symmetry.

**(b)** Specialise to $h = 2$. Using the rotation matrices

$$
R(\theta) = \begin{pmatrix}\cos\theta & -\sin\theta \\ \sin\theta & \cos\theta\end{pmatrix},
$$

show that $T_{\theta}(W) = R(\theta) W$ defines a continuous symmetry.

**(c)** For a fixed parameter $W \in {\mathbb{R}}^{2 \times m}$, compute the degenerate direction that arises from this symmetry.

**(d)** For general bottleneck dimension $h$, how many independent continuous symmetries does the orthogonal group $O(h)$ contribute?
:::callout {title="Hint" tone="neutral" collapse="closed"}

What is the dimension of $O(h)$?

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** For orthogonal $R$ (i.e. $R^{\top} R = I$),

$$
f_{RW}(x) = (RW)^{\top}(RW)x = W^{\top} R^{\top} R\, W x = W^{\top} W x = f_{W}(x).
$$

**(b)** We verify the three conditions.
1. Symmetry: $R(\theta)$ is orthogonal for all $\theta$, since

$$
R(\theta)^{\top} R(\theta) = \begin{pmatrix}\cos\theta & \sin\theta \\ -\sin\theta & \cos\theta\end{pmatrix} \begin{pmatrix}\cos\theta & -\sin\theta \\ \sin\theta & \cos\theta\end{pmatrix} = \begin{pmatrix}1 & 0 \\ 0 & 1\end{pmatrix}.
$$

So $f_{R(\theta)W}= f_{W}$ by part (a).
2. Identity: $R(0) = I$, so $T_{0}(W) = W$.
3. Differentiability: the entries of $R(\theta)W$ are smooth functions of $\theta$ (they involve $\cos\theta$ and $\sin\theta$ multiplied by entries of $W$).

**(c)** The degenerate direction at $W$ is

$$
\left.\frac{d}{d\theta}\right|_{\theta=0}R(\theta) W = R'(0)\, W.
$$

We compute

$$
R'(\theta) = \begin{pmatrix}-\sin\theta & -\cos\theta \\ \cos\theta & -\sin\theta\end{pmatrix}, \qquad R'(0) = \begin{pmatrix}0 & -1 \\ 1 & 0\end{pmatrix}.
$$

Writing $W = \begin{pmatrix}w_{1}^{\top} \\ w_{2}^{\top}\end{pmatrix}$ where $w_{1}, w_{2} \in {\mathbb{R}}^{m}$ are the two rows, the degenerate direction is the matrix

$$
R'(0)\, W = \begin{pmatrix}-w_{2}^{\top} \\ w_{1}^{\top}\end{pmatrix},
$$

which swaps the two rows and negates one. This direction is non-zero whenever $W \neq 0$.

**(d)** The orthogonal group $O(h)$ consists of all $h \times h$ matrices satisfying $R^{\top} R = I$. This constraint comprises $\frac{h(h+1)}{2}$ independent scalar equations (the entries of the symmetric matrix $R^{\top} R$ on and above the diagonal). Since $R$ has $h^{2}$ entries, the dimension of $O(h)$ is

$$
h^{2} - \frac{h(h+1)}{2}= \frac{h(h-1)}{2}.
$$

Each independent direction in $O(h)$ at the identity gives rise to a one-parameter continuous symmetry and hence a degenerate direction at each $W$. These directions are the $h \times h$ skew-symmetric matrices $S$ (satisfying $S^{\top} = -S$), since differentiating $R(t)^{\top} R(t) = I$ at $t = 0$ gives $R'(0)^{\top} + R'(0) = 0$. The space of such matrices has dimension $\frac{h(h-1)}{2}$ (the entries strictly above the diagonal are free, and the rest are determined).

So $O(h)$ contributes $\frac{h(h-1)}{2}$ independent continuous symmetries. For $h = 2$ this gives $1$, matching the single rotation symmetry from part (b).

:::

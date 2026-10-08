---
id: '7c34db78-66a8-4445-a531-63ef8ff5922b'
title: "B.3.11 Perspectives on the local learning coefficient"
tldr: "Gives other views of the local learning coefficient (bits, real log canonical threshold, fractal dimension) and its value for two-layer deep linear networks."
summary_for_tutor: "This is Section 3.2 and 3.3 of worksheet B.3 (singular learning theory). It covers the information-theoretic reading of the LLC, the algebro-geometric view (resolution of singularities, local zeta function, real log canonical threshold, optional), Definitions 3.2 (Holder exponent) and 3.3 (loss pseudo-metric) and Theorem 3.4 (Aoyagi and Watanabe 2005, the LLC of two-layer deep linear networks). It contains Exercises 3.8 (LLC via the RLCT), 3.9 (Holder exponent equals LLC) and 3.10 (LLCs of two-layer DLNs) with collapsed solutions. Keep the notation lambda, mu, RLCT. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 3.2 Perspectives on the local learning coefficient

In this section, we survey several alternative perspectives on the LLC, from information theory, algebraic geometry, and geometric measure theory.

**Information-theoretic interpretation.**

The LLC also admits a natural interpretation in terms of information (Lau et al. 2025). The number of bits needed to specify the sublevel set $B(w^{*}, \epsilon)$ within the ball $B(w^{*})$ is

$$
-\log_{2} \frac{V(\epsilon)}{\mathrm{Vol}(B(w^{*}))}.
$$

For small $\epsilon$ and $\mu(w^{*}) = 1$, this is approximately $-\lambda(w^{*}) \log_{2} \epsilon + O(\log_{2} \log_{2} \epsilon)$. In particular, the number of *additional* bits needed to halve an already small error tolerance from $\epsilon$ to $\epsilon/2$ is

$$
-\log_{2} \frac{V(\epsilon / 2)}{V(\epsilon)}\approx \lambda(w^{*}).
$$

That is, the LLC $\lambda(w^{*})$ measures the number of bits required to halve the error near $w^{*}$.

**Local learning coefficient via algebraic geometry.**

We explore an algebro-geometric perspective on the learning coefficient due to Watanabe 2009. Note that this section is more advanced than the remainder of this tutorial, and should be considered optional. When $L(w)$ is a real analytic function, Hironaka's resolution of singularities theorem guarantees the existence of a smooth map $g \colon M \to \mathcal{W}$ from an analytic manifold $M$ and local coordinates $u = (u_{1}, \ldots, u_{d})$ that *monomialise* the loss near $w^{*}$:

$$
L(g(u)) - L(w^{*}) = u_{1}^{2k_1}\cdots u_{d}^{2k_d}, \qquad dw = b(u)\, u_{1}^{h_1}\cdots u_{d}^{h_d}\, du,
$$

where $b(u) > 0$ is smooth and the exponents $k_{j}, h_{j}$ are non-negative integers. In these coordinates, the volume integral $V(\epsilon)$ can be evaluated explicitly, yielding the asymptotic form of Definition 3.1 and giving

$$
\lambda(w^{*}) \;=\; \min_{\text{coordinate charts}}\; \min_{j:\, k_j > 0}\frac{h_{j} + 1}{2k_{j}}\,.
$$

The resolution map $g$ is far from unique, and different choices produce different exponents $k_{j}, h_{j}$. $\lambda(w^{*})$ is nevertheless well-defined, which can be seen from (another) equivalent definition using the **local zeta function**:

$$
\zeta(z,\, w^{*}) \;=\; \int_{B(w^*)}\bigl(L(w) - L(w^{*})\bigr)^{\!z}\, dw\,,
$$

which converges for $\operatorname{Re}(z) > 0$ and extends to a meromorphic function on $\mathbb{C}$ whose poles are all real, negative, and rational. The LLC $\lambda(w^{*})$ is precisely the negative of the largest pole, and the multiplicity $\mu(w^{*})$ is the multiplicity of this pole. Since (44) makes no reference to any resolution, $\lambda(w^{*})$ depends only on $L$ and $w^{*}$.

In the algebraic geometry literature, $\lambda(w^{*})$ is called the **real log canonical threshold (RLCT)** of $L$ at $w^{*}$. We collect several consequences of this perspective.

1. The fact that the LLC is a rational number follows directly from equation (43).
2. Equation (43) suggests that we can compute $\lambda(w^{*})$ analytically by constructing an explicit resolution of singularities for $L(w) - L(w^{*})$ and reading off the exponents. This is difficult in practice for neural network loss functions, but has been achieved for some architectures, as we will see in Section 3.3.
3. In Section 4 we will state Watanabe's free energy formula connecting the Bayesian free energy to the LLC. The proof of this result makes repeated use of the monomialisation of the loss.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.8 (Computing the LLC via the RLCT).** Suppose that $L(w) = w_{1}^{2k_1}\cdots w_{d}^{2k_d}$ near $w^{*} = 0$, where $k_{j} \geq 0$ are integers with at least one $k_{j} > 0$. Show that

$$
\lambda(0) = \min_{j:\, k_j > 0}\frac{1}{2k_{j}}\,.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The loss $L(w) = w_{1}^{2k_1}\cdots w_{d}^{2k_d}$ is already in monomial form, so the identity map $g = \mathrm{id}$ serves as a (trivial) resolution of singularities with $dw = 1 \cdot du$, i.e. $h_{j} = 0$ for all $j$. Substituting into (43) gives

$$
\lambda(0) \;=\; \min_{j:\, k_j > 0}\frac{0 + 1}{2k_{j}}\;=\; \min_{j:\, k_j > 0}\frac{1}{2k_{j}}\,.
$$

:::

**Local learning coefficient as a fractal dimension.**

The LLC admits a geometric interpretation: it is a *fractal dimension* of the parameter space, as measured through the lens of the loss function. To make this precise, we recall a standard notion from fractal analysis.

:::callout {title="Definition" tone="blue"}

**Definition 3.2 (Hölder exponent).** Let $(X, \rho)$ be a (pseudo-)metric space and $\nu$ a measure on $X$. The **Hölder exponent** (or **local dimension**) $\alpha(x)$ of $\nu$ at a point $x \in X$ is given by

$$
\alpha(x) = \lim_{\epsilon \to 0}\frac{\log \nu(B_{\epsilon}(x))}{\log \epsilon},
$$

where $B_{\epsilon}(x)$ is the ball of radius $\epsilon$ centred at $x$. Equivalently, $\alpha(x)$ is the unique real number such that

$$
\nu(B_{\epsilon}(x)) = O(\epsilon^{\alpha(x)}) \qquad \text{as }\epsilon \to 0.
$$

:::

The Hölder exponent generalises the notion of dimension: when $\nu$ is the Lebesgue measure on ${\mathbb{R}}^{d}$ and $\rho$ is the Euclidean metric, every point has $\alpha(x) = d$, but for measures concentrated on fractal sets the exponent can be non-integer. Notice that the formula (45) has a similar form to the definition of the local learning coefficient (38). To make this connection precise, we introduce a pseudo-metric induced by the loss function.

:::callout {title="Definition" tone="blue"}

**Definition 3.3 (Loss pseudo-metric).** The **loss pseudo-metric** on ${\mathcal{W}}$ is defined by

$$
\rho(w,u) = |L(w) - L(u)|.
$$

:::

:::callout {title="Note" tone="blue"}

**Remark.** $\rho$ is only a pseudo-metric as the distance between two distinct points can be zero.

:::

Under this pseudo-metric, the sublevel set (34) is precisely the $\epsilon$-ball around $w^{*}$:

$$
B(w^{*}, \epsilon) = \{ w \in B(w^{*}) \mid \rho(w, w^{*}) < \epsilon \},
$$

so $V(\epsilon) = \nu(B(w^{*}, \epsilon))$.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.9 (Holder exponent and learning coefficient).** Let $\alpha(w^{*})$ be the Hölder exponent of the Lebesgue measure on ${\mathcal{W}}$ at $w^{*}$ under the loss pseudo-metric. Show that

$$
\lambda(w^{*}) = \alpha(w^{*}).
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Under the loss pseudo-metric $\rho(w,u) = |L(w) - L(u)|$, the $\epsilon$-ball centred at $w^{*}$ (within $B(w^{*})$) is

$$
B_{\epsilon}(w^{*}) = \{w \in B(w^{*}) : |L(w) - L(w^{*})| < \epsilon\}.
$$

Since $w^{*}$ is a local minimum and $L(w) \geq L(w^{*})$ on $B(w^{*})$, this simplifies to $B_{\epsilon}(w^{*}) = \{w \in B(w^{*}) : L(w) - L(w^{*}) < \epsilon\} = B(w^{*},\epsilon)$, the sublevel set from (34). In particular, $\nu(B_{\epsilon}(w^{*})) = V(\epsilon)$ where $\nu$ is Lebesgue measure.

The Holder exponent is therefore

$$
\alpha(w^{*}) = \lim_{\epsilon\to 0}\frac{\log \nu(B_{\epsilon}(w^{*}))}{\log\epsilon}= \lim_{\epsilon\to 0}\frac{\log V(\epsilon)}{\log\epsilon}= \lambda
$$

by Equation (39).

:::

\### 3.3 Local learning coefficients of deep linear networks

Having established the local learning coefficient as a measure of degeneracy in the loss landscape, we now compute it explicitly for the two-layer deep linear network introduced in Section 1. In Section 2, we saw that DLN parameters exhibit varying degrees of degeneracy depending on the ranks of the component matrices (Exercise 2.9, Remark 2.2). The LLC makes this hierarchy quantitative: different ranks correspond to different learning coefficients, confirming that lower-rank parameters are geometrically "simpler."

Consider the two-layer DLN $f_{A,B}(x) = BAx$ with $A \in {\mathbb{R}}^{H \times M}$ and $B \in {\mathbb{R}}^{N \times H}$, so the parameter space is ${\mathcal{W}} = {\mathbb{R}}^{(M+N)H}$. Suppose the true input–output relationship is $y = B_{0} A_{0} x$ where $A_{0} \in {\mathbb{R}}^{H \times M}$, $B_{0} \in {\mathbb{R}}^{N \times H}$, and $r = {\mathrm{rank}}(B_{0} A_{0})$, and consider the population loss

$$
L(A, B) = {\mathbb{E}}_{x \sim q(x)}\!\left[\|BAx - B_{0} A_{0} x\|^{2}\right],
$$

where $q(x)$ has full-rank covariance. The set of minima of this loss function is $W_{0} = \{(A, B) : BA = B_{0} A_{0}\}$. Aoyagi & Watanabe 2005 derived an exact formula for the learning coefficient at these minima.

:::callout {title="Theorem" tone="green"}

**Theorem 3.4 (Aoyagi & Watanabe 2005).** For the two-layer DLN $f_{A,B}(x) = BAx$ with $A \in {\mathbb{R}}^{H \times M}$, $B \in {\mathbb{R}}^{N \times H}$, and true parameter $(A_{0}, B_{0})$ with $r = {\mathrm{rank}}(B_{0} A_{0})$, at any minimum $w^{*} \in W_{0}$ the local learning coefficient $\lambda$ and its multiplicity $\mu$ are given by the following cases:

1. If $N + r \leq M + H$,   $M + r \leq N + H$,   and   $H + r \leq M + N$:
   1. If $M + H + N + r$ is even, then $\mu = 1$ and

   $$
   \lambda = \frac{-(H+r)^{2} - M^{2} - N^{2} + 2(H+r)M + 2(H+r)N + 2MN}{8}.
   $$
   2. If $M + H + N + r$ is odd, then $\mu = 2$ and

   $$
   \lambda = \frac{-(H+r)^{2} - M^{2} - N^{2} + 2(H+r)M + 2(H+r)N + 2MN + 1}{8}.
   $$
2. If $M + H < N + r$, then $\mu = 1$ and $\displaystyle\lambda = \frac{HM - Hr + Nr}{2}$.
3. If $N + H < M + r$, then $\mu = 1$ and $\displaystyle\lambda = \frac{HN - Hr + Mr}{2}$.
4. If $M + N < H + r$, then $\mu = 1$ and $\displaystyle\lambda = \frac{MN}{2}$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.10 (Learning coefficients of two-layer DLNs).** Consider the constant-width two-layer DLN from Exercise 2.9: $y = BAx$, where $x \in {\mathbb{R}}^{m}$ are the inputs, $y \in {\mathbb{R}}^{m}$ are the outputs, and $A, B \in {\mathbb{R}}^{m \times m}$ are linear transformations. The parameter space is ${\mathcal{W}} = {\mathbb{R}}^{2m^2}$ and the parameters are the pair $(A, B) \in {\mathcal{W}}$.

**(a)** Aoyagi & Watanabe do not assume the network is constant-width, like we do. Simplify their formula for $\lambda$ using this assumption.

**(b)** How does the learning coefficient $\lambda$ depend on $r$, the rank of $B_{0} A_{0}$? Compare with the results of Exercise 2.9(d).

**(c)** How does $\lambda$ compare with the effective parameter count $d/2$ of a regular model? What does this tell us about the role of singularities in the two-layer DLN?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** We first check which case of Theorem 3.4 applies. Setting $M = N = H = m$, the three conditions of Case 1 each reduce to $m + r \leq 2m$, i.e. $r \leq m$, which always holds. So we are always in Case 1. The parity condition is on $M + H + N + r = 3m + r$, which has the same parity as $m + r$.

**Case 1(a):** $m + r$ even. Setting $M = N = H = m$ in the formula:

$$
\begin{aligned}\lambda&= \frac{-(m+r)^{2} - m^{2} - m^{2} + 2(m+r)m + 2(m+r)m + 2m^{2}}{8}\\&= \frac{-(m+r)^{2} + 4m(m+r)}{8}\\&= \frac{(m+r)\bigl(4m - (m+r)\bigr)}{8}\\&= \frac{(m+r)(3m-r)}{8},\end{aligned}
$$

with $\mu = 1$.

**Case 1(b):** $m + r$ odd. The same calculation gives

$$
\lambda = \frac{(m+r)(3m - r) + 1}{8},
$$

with $\mu = 2$.

**(b)** Differentiating with respect to $r$:

$$
\frac{d\lambda}{dr}=\frac{1}{8}\frac{d}{dr}\!\left[(m+r)(3m-r)\right] = \frac{1}{8}\left[(3m - r) - (m + r)\right] = \frac{1}{4}(m - r) \geq 0,
$$

so $\lambda$ is increasing in $r$, therefore **lower rank $\implies$ lower $\lambda$**. This is consistent with Exercise 2.9(d) where we saw that at lower-rank parameters, more directions in parameter space are degenerate.

**(c)** The parameter space is ${\mathcal{W}} = {\mathbb{R}}^{2m^2}$, so the regular-model baseline is $d/2 = m^{2}$. At full rank $r = m$:

$$
\lambda = \frac{(2m)(2m)}{8}= \frac{m^{2}}{2}= \frac{d}{4},
$$

which is already half the regular-model value. At rank $r = 0$:

$$
\lambda = \frac{m \cdot 3m}{8}= \frac{3m^{2}}{8}= \frac{3d}{16},
$$

even smaller. In fact $\lambda < d/2$ for every rank $0 \leq r \leq m$.

This tells us that the two-layer DLN is singular at every point in its loss landscape, even at full-rank parameters.

:::

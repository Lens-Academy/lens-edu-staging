---
id: '70a20553-6e0e-4949-9e70-7920ac594c10'
title: "B.3.5 A definition of degeneracy"
tldr: "Defines degeneracy of a parameter-function map as a zero directional derivative, and works through toy parametrisations of the constants."
summary_for_tutor: "This is Section 2.1 of Iliad worksheet B.3 Singular Learning Theory. It defines a parameter-function map as degenerate at w if D_v Phi(w) = 0 for some non-zero direction v, plus the terms somewhere degenerate and everywhere degenerate. It contains Exercises 2.1 (w), 2.2 (w^3), 2.3 (a*b) and 2.4 (a+b) with hints and collapsed solutions. Keep the notation D_v Phi(w). Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## 2. What is degeneracy?

In this section, we define degeneracy as a property of parameter–function maps, and study the relationship between this property and other similar notions.

\### 2.1 A definition of degeneracy

Consider a neural network architecture with parameter space ${\mathcal{W}} \subseteq {\mathbb{R}}^{d}$ and parameter–function map $\Phi : {\mathcal{W}} \to {\mathcal{F}}$ ($w \mapsto f_{w}$). Say the parameter–function map is **degenerate at $w\in{\mathcal{W}}$** if there is a non-zero vector $v \in {\mathbb{R}}^{d}$ such that the directional derivative of the parameter–function map in the direction $v$ is zero:

$$
D_{v} \Phi(w) = 0.
$$

The directional derivative $D_{v} \Phi(w)$ for non-zero $v \in {\mathbb{R}}^{d}$ may be defined variously as

$$
D_{v} \Phi(w) = \frac{v}{\|v\|}\cdot \nabla \Phi(w) = \sum_{i=1}^{d} \frac{v_{i}}{\|v\|}\frac{\partial \Phi}{\partial w_{i}}(w) = \lim_{\epsilon \to 0}\frac{\Phi(w + \epsilon v) - \Phi(w)}{\epsilon\|v\|}.
$$

We conventionally define $D_{0} \Phi(w) = 0$. Note that $w$ is fixed, but the directional derivative is still a function (of the same type as $\Phi(w)$; $D_{v} \Phi(w) : {\mathcal{X}} \to {\mathcal{Y}}$), since it represents an infinitesimal change in $\Phi(w)$ in response to a change in $w$ in the direction $v$. In (19) we mean that this function is identically zero for all inputs $x \in {\mathcal{X}}$ for the given $w \in {\mathcal{W}}$.

Intuitively, the parameter–function map is degenerate at $w \in {\mathcal{W}}$ if there is a direction in which we can infinitesimally perturb $w$ without changing the function $f_{w}$.

This definition of degeneracy applies to a single point in parameter space. As we shall soon see, it may be the case that the parameter–function map is degenerate at some points but not at others. We can clarify the situation with new terminology.

- We say that a parameter–function map is **somewhere degenerate** if it is degenerate at *any* point in parameter space.
- We say that a parameter–function map is **everywhere degenerate** if it is degenerate at *all* points in parameter space.

By convention, if we say that the parameter–function map is simply **degenerate** (without specifying somewhere, everywhere, or at a particular point), we mean that it is *somewhere degenerate*.

The following exercises explore this definition in some toy parametrisations of a simple function class (constants), displaying in the simplest possible setting some basic forms of degeneracy that will arise repeatedly throughout the tutorial.

::::callout {title="Exercise" tone="amber"}
**Exercise 2.1 (Parametrising the space of constants).** Let ${\mathcal{X}} = \{\ast\}$ and ${\mathcal{Y}} = {\mathbb{R}}$, so that we have a hypothesis class of constants. Consider the scalar parameter space ${\mathcal{W}} = {\mathbb{R}}$ and the parameter–function map that maps $w$ to $f_{w} = w$ (the output is just the parameter itself).

**(a)** What is the directional derivative of the parameter–function map in direction $v = 1$?
:::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

:::

**(b)** At which points in the parameter space is this parameter–function map degenerate, if any?
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since ${\mathcal{W}} = {\mathbb{R}}$ is one-dimensional, the directional derivative in direction $v = 1$ reduces to the ordinary derivative:

$$
\frac{\partial \Phi}{\partial w}= \frac{d}{dw}w = 1.
$$

**(b)** The directional derivative is $1 \neq 0$ for all $w \in {\mathcal{W}}$. Therefore, the parameter–function map is *not degenerate* at any point.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 2.2 (Degeneracy from raising a parameter to a power).** Again, consider a hypothesis class of constants and the scalar parameter space ${\mathcal{W}} = {\mathbb{R}}$. This time, define a parameter–function map that maps $w$ to $f_{w} = w^{3}$.

**(a)** Show that this architecture indexes exactly the same hypothesis class as the architecture described in Exercise 2.1.

**(b)** What is the directional derivative of the parameter–function map in direction $v = 1$?
:::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

:::

**(c)** At which points in the parameter space is the parameter–function map degenerate, if any?
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The hypothesis class of Exercise 2.1 is ${\mathcal{F}} = \{f_{w} = w : w \in {\mathbb{R}}\} = {\mathbb{R}}$. The hypothesis class here is ${\mathcal{F}} = \{f_{w} = w^{3} : w \in {\mathbb{R}}\}$. Since $w \mapsto w^{3}$ is a bijection on ${\mathbb{R}}$, as $w$ ranges over ${\mathbb{R}}$, $w^{3}$ takes every real value exactly once. So ${\mathcal{F}} = {\mathbb{R}}$ in both cases.

**(b)** The directional derivative in direction $v = 1$ is the ordinary derivative:

$$
\frac{\partial \Phi}{\partial w}= \frac{d}{dw}w^{3} = 3w^{2}.
$$

**(c)** The directional derivative $3w^{2} = 0$ if and only if $w = 0$. So the parameter–function map is degenerate at $w = 0$ only. It is somewhere degenerate but not everywhere degenerate.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 2.3 (Degeneracy from multiplying two parameters together).** Again, consider a hypothesis class of constants. Consider this time the two-dimensional parameter space ${\mathcal{W}} = {\mathbb{R}}^{2}$. Define a parameter–function map that maps $w = (a, b)$ to $f_{w} = a \cdot b$.

**(a)** Show that this architecture indexes exactly the same hypothesis class as the architecture described in Exercise 2.1.

**(b)** What is the directional derivative of the parameter–function map in direction $v = (1, 0)$?
:::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

:::

**(c)** What is the directional derivative of the parameter–function map in direction $v = (0, 1)$?
:::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

:::

**(d)** At which points in the parameter space is the parameter–function map degenerate *in these directions,* if any?

**(e)** At which points in the parameter space is the parameter–function map degenerate, if any?
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The hypothesis class is ${\mathcal{F}} = \{f_{w} = ab : (a, b) \in {\mathbb{R}}^{2}\} = {\mathbb{R}}$, since for any target $c \in {\mathbb{R}}$ we can choose, e.g., $a = c$ and $b = 1$. This is the same as in Exercise 2.1.

**(b)** The directional derivative in direction $v = (1, 0)$ is the partial derivative with respect to $a$:

$$
\frac{\partial \Phi}{\partial a}= \frac{\partial}{\partial a}(ab) = b.
$$

**(c)** The directional derivative in direction $v = (0, 1)$ is the partial derivative with respect to $b$:

$$
\frac{\partial \Phi}{\partial b}= \frac{\partial}{\partial b}(ab) = a.
$$

**(d)** From parts (b) and (c), the direction $(1, 0)$ is degenerate at $(a, b)$ if and only if $b = 0$, and the direction $(0, 1)$ is degenerate if and only if $a = 0$. So the parameter–function map is degenerate in at least one of these coordinate directions precisely on the set $\{(a, b) : a = 0 \text{ or }b = 0\}$, i.e. the union of the two coordinate axes.

**(e)** The directional derivative in a general direction $v = (v_{1}, v_{2})$ is proportional to

$$
v_{1} \frac{\partial \Phi}{\partial a}+ v_{2} \frac{\partial \Phi}{\partial b}= v_{1} b + v_{2} a.
$$

This is a single linear equation in two unknowns $(v_{1}, v_{2})$.

- If $a = b = 0$: the equation $0 = 0$ is trivially satisfied, so every direction is degenerate.
- If $(a, b) \neq (0, 0)$: the coefficient vector $(b, a)$ is nonzero, so the solution space is one-dimensional. A nonzero solution is $v = (-a, b)$: indeed, $(-a) b + b \cdot a = 0$.

Therefore, the parameter–function map is degenerate *everywhere*. Note that the previous part found degeneracy only on the coordinate axes because it checked only the coordinate directions. Checking for parameter–function map degeneracy requires checking all possible directions.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.4 (Degeneracy from adding two parameters together).** Again, consider a hypothesis class of constants. Consider this time the two-dimensional parameter space ${\mathcal{W}} = {\mathbb{R}}^{2}$. Define a parameter–function map that maps $w = (a, b)$ to $f_{w} = a + b$.

**(a)** Show that this architecture indexes exactly the same hypothesis class as the architecture described in Exercise 2.1.

**(b)** What is the directional derivative of the parameter–function map in direction $v = (1, -1)$?

**(c)** At which points in the parameter space is the parameter–function map degenerate, if any?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The hypothesis class is ${\mathcal{F}} = \{f_{w} = a + b : (a, b) \in {\mathbb{R}}^{2}\} = {\mathbb{R}}$, since for any target $c \in {\mathbb{R}}$ we can choose, e.g., $a = c$ and $b = 0$. This is the same as in Exercise 2.1.

**(b)** The direction $v = (1, -1)$ has $\|v\| = \sqrt{2}$, so by (20) the directional derivative is

$$
\frac{1}{\sqrt{2}}\left( 1 \cdot \frac{\partial}{\partial a}(a + b) + (-1) \cdot \frac{\partial}{\partial b}(a + b) \right) = \frac{1}{\sqrt{2}}(1 - 1) = 0.
$$

**(c)** The direction $v = (1, -1)$ gives a zero directional derivative at *every* point $(a, b) \in {\mathcal{W}}$. Therefore, the parameter–function map is everywhere degenerate. This reflects the fact that the map $(a, b) \mapsto a + b$ has a global continuous symmetry: translating along the direction $(1, -1)$ does not change the output.

:::

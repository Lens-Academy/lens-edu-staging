---
id: '3dd6c68f-6a68-44ec-8df3-576e29ce6fa4'
title: "B.3.10 The local learning coefficient via volume scaling"
tldr: "Defines the local learning coefficient from how the volume of near-minimal parameters scales with the loss tolerance, and computes it in examples."
summary_for_tutor: "This is Section 3.1 of Iliad worksheet B.3 Singular Learning Theory. It defines the sublevel set B(w*, epsilon), the volume V(epsilon), and Definition 3.1 of the local learning coefficient lambda and local multiplicity mu via V(epsilon) = c epsilon^lambda (-log epsilon)^(mu-1). It contains Exercises 3.1 (regular case, lambda = d/2), 3.2 (quadratic valley), 3.3 (limit formulas for lambda), 3.4 (computing the LLC), 3.5 (upper bound lambda <= d/2), 3.6 (LLC versus Hessian rank) and 3.7 (cubically-parameterised loss, with a plotting part) with hints and collapsed solutions. Keep the notation V(epsilon), lambda, mu. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## 3. The degeneracy hierarchy

We have so far explored different kinds of qualitative degeneracy in the loss landscape. A natural question arises: *how can we quantify the degree of degeneracy at a particular point in parameter space?* In this section, we introduce the local learning coefficient, a rich mathematical object that reflects the degree of degeneracy at a parameter, and we explore it from several perspectives.

In this section and Section 4 we assume that any population loss $L$ is a real analytic function. The precise definition of real analyticity is not important for this tutorial but interested readers can refer to (Watanabe 2009) (section 2). A property that will be useful is that such functions have a convergent Taylor expansion, in particular they have smooth derivatives of all orders.

\### 3.1 The local learning coefficient via volume scaling asymptotics

The key idea is to measure the *volume* of near-optimal parameters. Consider a local minimum $w^{*} \in {\mathcal{W}}$ of the population loss $L$, and suppose we have a sufficiently small closed ball $B(w^{*})$ centred on $w^{*}$ such that $L(w) \geq L(w^{*})$ for all $w \in B(w^{*})$. Given a tolerance $\epsilon > 0$, define the **sublevel set**

$$
B(w^{*}, \epsilon) = \{ w \in B(w^{*}) \mid L(w) - L(w^{*}) < \epsilon \},
$$

consisting of all parameters in the ball whose loss is within $\epsilon$ of the minimum. The volume of this set is

$$
V(\epsilon) := \mathrm{Vol}(B(w^{*}, \epsilon)) = \int_{B(w^*, \epsilon)}dw.
$$

We will look at how this volume scales as $\epsilon \to 0$. It will be instructive for us to first calculate this scaling in the non-degenerate case.

::::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (Volume scaling in the regular case).** Let $w^{*} \in {\mathcal{W}}$ be a local minimum of $L$, and suppose that the Hessian $\nabla^{2} L(w^{*})$ is positive definite. Show that

$$
V(\epsilon) = c \, \epsilon^{d/2}+ o(\epsilon^{d/2}) \quad \text{as }\epsilon \to 0,
$$

for some constant $c>0$ where $d = \dim({\mathcal{W}})$. You may assume that, as $\epsilon \to 0$, the volume of $B(w^{*},\epsilon)$ agrees to leading order with the volume of the quadratic approximation obtained by replacing $L$ with its second-order Taylor expansion at $w^{*}$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

The volume of the ellipsoid $\{\boldsymbol{x}\in {\mathbb{R}}^{d} \mid \boldsymbol{x}^{\top} A \boldsymbol{x}< 1\}$ is proportional to $(\det A)^{-1/2}$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Because $w^{*}$ is a local minimum, the gradient $\nabla L(w^{*})$ is zero. By Taylor's theorem, we can write the loss function near $w^{*}$ exactly as:

$$
L(w) - L(w^{*}) = \frac{1}{2}(w - w^{*})^{\top} H (w - w^{*}) + o(\|w - w^{*}\|^{2})
$$

where $H = \nabla^{2} L(w^{*})$ is the strictly positive definite Hessian matrix.

The sublevel set is defined by the condition $L(w) - L(w^{*}) < \epsilon$. As $\epsilon \to 0$, the neighborhood of parameters that satisfy this condition shrinks toward $w^{*}$. In this limit, the higher-order error term $o(\|w - w^{*}\|^{2})$ becomes negligible, and the boundary of the sublevel set is governed entirely by the quadratic form:

$$
\frac{1}{2}(w - w^{*})^{\top} H (w - w^{*}) < \epsilon.
$$

We can rewrite this inequality into the standard form of an ellipsoid, $x^{\top} A x < 1$, by dividing both sides by $\epsilon$:

$$
(w - w^{*})^{\top} \left( \frac{1}{2\epsilon}H \right) (w - w^{*}) < 1.
$$

Using the hint, the volume of a $d$-dimensional ellipsoid defined by a matrix $A$ is proportional to $(\det A)^{-1/2}$. Here, our matrix is $A = \frac{1}{2\epsilon}H$.

Therefore,

$$
\det\left( \frac{1}{2\epsilon}H \right)^{-1/2}= \left( \left(\frac{1}{2\epsilon}\right)^{d} \det H \right)^{-1/2}= \epsilon^{d/2}\underbrace{\left( \frac{\det H}{2^{d}} \right)^{-1/2}}_{:=c}
$$

Because the true loss function deviates from this pure quadratic form only by an error of $o(\|w - w^{*}\|^{2})$, the volume of the true sublevel set deviates from the ellipsoid's volume only by a correspondingly higher-order error term. Thus, we conclude:

$$
V(\epsilon) = c \epsilon^{d/2}+ o(\epsilon^{d/2}) \quad \text{as }\epsilon \to 0.
$$

:::

The key takeaway from this exercise is that the dimension of the model controls the leading order asymptotics of the volume scaling. We can investigate this further by calculating the volume scaling in an example where the Hessian is not positive definite.

::::callout {title="Exercise" tone="amber"}
**Exercise 3.2 (Quadratic Valley Volume Scaling).** Let ${\mathcal{W}} = [-R,R]^{d}$ for some (large) $R\in{\mathbb{R}}$ and let $L(x_{1},\dots,x_{d}) = \sum\limits_{i=1}^{d'}x_{i}^{2}$.

**(a)** Sketch the loss landscape when $d=2, \,d'=1$.

**(b)** $L$ achieves its minimum value $0$ at multiple points in ${\mathcal{W}}$. What is the dimension of the space ${\mathcal{W}}_{0} := \{w\in{\mathcal{W}} \, | \,L(w)=0\}$?

**(c)** Calculate the Hessian of $L$.

**(d)** Prove that $V(\epsilon) \propto \epsilon^{d'/2}$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use the volume of the ellipsoid from Exercise 3.1.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The loss is $L(x_{1}, x_{2}) = x_{1}^{2}$, which is a parabolic trough: a parabola in the $x_{1}$ direction and constant along $x_{2}$. The zero set is the line $x_{1} = 0$.

**(b)** ${\mathcal{W}}_{0} = \{0\}^{d'}\times [-R,R]^{d-d'}$, which is a $(d - d')$-dimensional affine subspace of ${\mathcal{W}}$. Hence $\dim({\mathcal{W}}_{0}) = d - d'$.

**(c)** Since $L(w) = \sum_{i=1}^{d'}x_{i}^{2}$, the partial derivatives are

$$
\frac{\partial L}{\partial x_{i}}= \begin{cases}2x_{i}&i \leq d', \\ 0&i > d',\end{cases} \qquad \frac{\partial^{2} L}{\partial x_{i} \partial x_{j}}= \begin{cases}2 & i = j \leq d', \\ 0 & \text{otherwise}.\end{cases}
$$

So the Hessian is the block diagonal matrix:

$$
\nabla^{2} L = \begin{pmatrix}2I_{d'}&0 \\ 0&0_{d-d'}\end{pmatrix},
$$

which has rank $d'$. In particular it is positive semi-definite but not positive definite whenever $d' < d$.

**(d)** The minimum of $L$ is $0$, achieved on ${\mathcal{W}}_{0}$. For any $w^{*} \in {\mathcal{W}}_{0}$ and $\epsilon > 0$, the sublevel set is

$$
\begin{aligned}B(w^{*}, \epsilon)&= \left\{ (x_{1},\dots,x_{d}) \in [-R,R]^{d} \;\middle|\; \sum_{i=1}^{d'}x_{i}^{2} < \epsilon \right\} \\&= \left\{x \in {\mathbb{R}}^{d'}: \sum_{i=1}^{d'}x_{i}^{2} < \epsilon \right\} \times [-R,R]^{d-d'}\end{aligned}
$$

for $R$ sufficiently large (specifically $\sqrt{\epsilon}< R$). The condition $\sum_{i=1}^{d'}x_{i}^{2} < \epsilon$ can be rewritten as $\mathbf{x}^{\top} A \mathbf{x}< 1$ where $A = \epsilon^{-1}I_{d'}$. By the ellipsoid volume formula from Exercise 3.1, the volume of this region is proportional to $(\det A)^{-1/2}= (\epsilon^{-d'})^{-1/2}= \epsilon^{d'/2}$. Multiplying by the volume $(2R)^{d-d'}$ of the remaining coordinates gives $V(\epsilon) \propto \epsilon^{d'/2}$.

:::

In this example, the degenerate directions do not contribute to the leading exponent of $V(\epsilon)$. We see that the exponent $\frac{d}{2}$ from Exercise 3.1 is replaced with $\frac{d'}{2}$ where $d'$ is the codimension of ${\mathcal{W}}_{0}$ i.e. the *effective dimension* of $L$ which ignores the degenerate directions. This suggests that we can capture information about the degree of degeneracy of a loss function by looking at how the volume $V(\epsilon)$ scales as $\epsilon \to 0$. (Watanabe 2009) proves a general form for this kind of volume scaling which has been adapted by (Lau et al. 2025) into the following definition.

:::callout {title="Definition" tone="blue"}

**Definition 3.1 (Local learning coefficient).** Let $w^{*} \in {\mathcal{W}}$ be a local minimum of the population loss $L$. There exists a unique rational number $\lambda(w^{*}) > 0$, a positive integer $\mu(w^{*})$, and a constant $c > 0$ such that as $\epsilon \to 0$,

$$
V(\epsilon) = c \, \epsilon^{\lambda(w^*)}(-\log \epsilon)^{\mu(w^*)-1}+ o\!\left(\epsilon^{\lambda(w^*)}(-\log \epsilon)^{\mu(w^*)-1}\right).
$$

We call $\lambda(w^{*})$ the **local learning coefficient (LLC)** at $w^{*}$, and $\mu(w^{*})$ the **local multiplicity**.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.3 (Two equations for $\lambda$).** **(a)** Prove that for $a>1$

$$
\lambda = \lim_{\epsilon \to 0}\frac{\log(V(a\epsilon)/V(\epsilon))}{\log(a)}
$$

**(b)** Prove that

$$
\lambda = \lim\limits_{\epsilon\to 0}\frac{\log V(\epsilon)}{\log \epsilon}
$$

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** From Definition 3.1, as $\epsilon \to 0$,

$$
V(\epsilon) = c\,\epsilon^{\lambda}(-\log\epsilon)^{m-1}\bigl(1 + o(1)\bigr).
$$

Substituting $\epsilon \mapsto a\epsilon$,

$$
V(a\epsilon) = c\,(a\epsilon)^{\lambda}(-\log(a\epsilon))^{m-1}\bigl(1 + o(1)\bigr).
$$

Taking the ratio,

$$
\frac{V(a\epsilon)}{V(\epsilon)}= a^{\lambda}\left(\frac{-\log(a\epsilon)}{-\log\epsilon}\right)^{\!m-1}\bigl(1 + o(1)\bigr).
$$

As $\epsilon \to 0$, $-\log\epsilon \to \infty$, and

$$
\frac{-\log(a\epsilon)}{-\log\epsilon}= \frac{-\log a - \log\epsilon}{-\log\epsilon}= 1 + \frac{\log a}{-\log\epsilon}\;\xrightarrow{\epsilon\to 0}\; 1.
$$

Therefore $V(a\epsilon)/V(\epsilon) \to a^{\lambda}$. Taking logarithms and dividing by $\log a > 0$ gives the result.

**(b)** From Definition 3.1, $V(\epsilon) = c\,\epsilon^{\lambda(w^*)}(-\log\epsilon)^{\mu(w^*)-1}(1 + o(1))$, so

$$
\log V(\epsilon) = \lambda(w^{*})\log\epsilon + (\mu(w^{*})-1)\log(-\log\epsilon) + \log c + o(1).
$$

Dividing by $\log\epsilon$

$$
\frac{\log V(\epsilon)}{\log\epsilon}= \lambda(w^{*}) + \frac{(\mu(w^{*})-1)\log(-\log\epsilon)}{\log\epsilon}+ \frac{\log c + o(1)}{\log\epsilon}.
$$

It remains to prove that the final two terms in this sum vanish as $\epsilon \to 0$. The final term tends to $0$ since $\log \epsilon \to -\infty$ and the numerator is bounded as $\epsilon \to 0$. Now we look at the middle term which is proportional to

$$
\lim\limits_{\epsilon\to 0}\frac{\log (-\log \epsilon)}{\log \epsilon}=\lim\limits_{x\to \infty}\frac{\log (x)}{-x}= 0,
$$

completing the proof.

:::

Note that from equation (36) we already have that the LLC and local multiplicity in the regular case are $\lambda = \frac{d}{2}$, $\mu=1$.

When $\mu(w^{*}) = 1$, the formula simplifies to $V(\epsilon) = c\epsilon^{\lambda(w^*)}+ o(\epsilon^{\lambda(w^*)})$ which allows us to interpret $\lambda(w^{*})$ as the *volume scaling exponent*: increasing the error tolerance by a factor of $a$ increases the volume of near-optimal parameters by a factor of $a^{\lambda(w^*)}$.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.4 (Calculating the LLC).** Calculate the LLC and the rank of the Hessian at the global minimum in the following cases:

**(a)** $L(x)=x^{2}$

**(b)** $L(x) = x^{2m}$

**(c)** $L(x,y) = x^{4} + y^{4}$

**(d)** $L(x,y) = x^{2}+y^{4}$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** $V(\epsilon) = \operatorname{Vol}(\{x : x^{2} < \epsilon\}) = 2\sqrt{\epsilon}$, so $V(\epsilon) \propto \epsilon^{1/2}$ and $\lambda = 1/2$. The Hessian is $L''(0) = 2$, which has rank $1$ (full rank).

**(b)** $V(\epsilon) = \operatorname{Vol}(\{x : x^{2m}< \epsilon\}) = 2\epsilon^{1/2m}$, so $\lambda = 1/2m$. For $m \geq 2$, the first $2m - 1$ derivatives vanish at $x = 0$, so the Hessian is $L''(0) = 0$, which has rank $0$. Since $\lambda = 1/2m < 1/2 = d/2$, the singularity makes the model effectively simpler than its parameter count suggests.

**(c)** The sublevel set is $\{(x,y) : x^{4} + y^{4} < \epsilon\}$. Substituting $x = \epsilon^{1/4}s$, $y = \epsilon^{1/4}t$:

$$
V(\epsilon) = \epsilon^{1/2}\int\!\!\int_{\{s^4 + t^4 < 1\}}ds\, dt = c\,\epsilon^{1/2},
$$

so $\lambda = 1/2$. The Hessian at the origin is $\nabla^{2}L(0,0) = \operatorname{diag}(12x^{2}, 12y^{2})\big|_{(0,0)}= 0$, which has rank $0$.

**(d)** The sublevel set is $\{(x,y) : x^{2} + y^{4} < \epsilon\}$. For each fixed $y$ with $|y| < \epsilon^{1/4}$, $x$ ranges over $|x| < \sqrt{\epsilon - y^{4}}$. Substituting $y = \epsilon^{1/4}t$:

$$
\begin{aligned}V(\epsilon)&= \int_{-\epsilon^{1/4}}^{\epsilon^{1/4}}2\sqrt{\epsilon - y^{4}}\, dy = 2\epsilon^{1/4}\int_{-1}^{1}\sqrt{\epsilon - \epsilon t^{4}}\, dt \\&= 2\epsilon^{3/4}\int_{-1}^{1}\sqrt{1 - t^{4}}\, dt = c\,\epsilon^{3/4},\end{aligned}
$$

so $\lambda = 3/4$. The Hessian is $\nabla^{2}L(0,0) = \operatorname{diag}(2, 12y^{2})\big|_{(0,0)}= \operatorname{diag}(2, 0)$, which has rank $1$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 3.5 (Upper bound on the LLC).** In Exercise 3.1, we saw that $\lambda = d/2$ for regular models. In this exercise, you will prove directly from the volume scaling definition that for any local minimum $w^{*}$ of the population loss, the local learning coefficient satisfies $\lambda(w^{*}) \leq d/2$.

**(a)** Let $\Lambda>0$ be an upper bound on the eigenvalues of the Hessian $\nabla^{2} L(w)$ for all $w \in B(w^{*})$. Using the Lagrange remainder form of Taylor's theorem, show that for all $w \in B(w^{*})$,

$$
L(w) - L(w^{*}) \leq \frac{1}{2}\Lambda \|w - w^{*}\|^{2}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

For any real symmetric matrix $H\in{\mathbb{R}}^{n\times n}$ and vector $v\in {\mathbb{R}}^{n}$, $v^{\top} H v \leq \Lambda \|v\|^{2}$ where $\Lambda$ is the largest eigenvalue of $H$.

:::

**(b)** Consider the standard Euclidean ball of radius $r$ centred at $w^{*}$, denoted $B_{r}(w^{*}) = \{w \in {\mathcal{W}} \mid \|w - w^{*}\| < r\}$. Find a radius $r$ (as a function of $\epsilon$ and $\Lambda$) such that for sufficiently small $\epsilon$,

$$
B_{r}(w^{*}) \subseteq B(w^{*}, \epsilon).
$$

**(c)** Recall that the volume of a $d$-dimensional Euclidean ball of radius $r$ is proportional to $r^{d}$. Use your result from part (b) to show that there exists a constant $C > 0$ such that for sufficiently small $\epsilon$,

$$
C \epsilon^{d/2}\leq V(\epsilon).
$$

**(d)** Conclude that $\lambda(w^{*}) \leq d/2$.
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since $w^{*}$ is a local minimum of $L$, we have $\nabla L(w^{*}) = 0$. By Taylor's theorem with Lagrange remainder, for any $w \in B(w^{*})$ there exists $\tilde{w}$ on the line segment between $w^{*}$ and $w$ such that

$$
\begin{aligned}L(w) - L(w^{*})&= \nabla L(w^{*})^{\top} (w - w^{*}) + \frac{1}{2}(\tilde w - w^{*})^{\top} \nabla^{2} L(\tilde{w})(\tilde w - w^{*}) \\&= \frac{1}{2}(\tilde w - w^{*})^{\top} \nabla^{2} L(\tilde{w})(\tilde w - w^{*}).\end{aligned}
$$

Since $\tilde{w}\in B(w^{*})$, the eigenvalues of $\nabla^{2} L(\tilde{w})$ are bounded above by $\Lambda$, so

$$
(\tilde w - w^{*})^{\top} \nabla^{2} L(\tilde{w})(\tilde w - w^{*}) \leq \Lambda \|\tilde w - w^{*}\|^{2} \leq \Lambda \|w - w^{*}\|^{2}.
$$

Combining, $L(w) - L(w^{*}) \leq \frac{1}{2}\Lambda \|w - w^{*}\|^{2}$.

**(b)** Set $r = \sqrt{2\epsilon/\Lambda}$. Set $\epsilon$ sufficiently small that $B_{r}(w^{*}) \subseteq B(w^{*})$. If $w \in B_{r}(w^{*})$, then $\|w - w^{*}\| < r$, so by part (a),

$$
L(w) - L(w^{*}) \leq \frac{1}{2}\Lambda \|w - w^{*}\|^{2} < \frac{1}{2}\Lambda \cdot \frac{2\epsilon}{\Lambda}= \epsilon.
$$

Hence $w \in B(w^{*}, \epsilon)$, and therefore $B_{r}(w^{*}) \subseteq B(w^{*}, \epsilon)$.

**(c)** Since $B_{r}(w^{*}) \subseteq B(w^{*}, \epsilon)$,

$$
V(\epsilon) = \operatorname{Vol}(B(w^{*}, \epsilon)) \geq \operatorname{Vol}(B_{r}(w^{*})) = c \, r^{d} = c \left(\frac{2\epsilon}{\Lambda}\right)^{d/2}= C \, \epsilon^{d/2},
$$

for some $c >0$ and $C = c (2/\Lambda)^{d/2}> 0$. This holds for all sufficiently small $\epsilon > 0$ (i.e. small enough that $B_{r}(w^{*}) \subseteq B(w^{*})$).

**(d)** From part (c), $V(\epsilon) \geq C\epsilon^{d/2}$ for sufficiently small $\epsilon$ (w.l.o.g. assume $\epsilon < 1$). Taking logarithms,

$$
\log V(\epsilon) \geq \log C + \frac{d}{2}\log \epsilon.
$$

Dividing by $\log \epsilon < 0$ (since $\epsilon < 1$) reverses the inequality:

$$
\frac{\log V(\epsilon)}{\log \epsilon}\leq \frac{\log C}{\log \epsilon}+ \frac{d}{2}.
$$

Since $\log C / \log \epsilon \to 0$ as $\epsilon \to 0^{+}$, taking the limit and using Equation (39) gives

$$
\lambda(w^{*}) = \lim_{\epsilon \to 0^+}\frac{\log V(\epsilon)}{\log \epsilon}\leq \frac{d}{2}.
$$

:::

We have now shown that the LLC satisfies $\lambda(w^{*}) \leq d/2$, with equality precisely in the regular (non-degenerate) case. It is also possible (although quite fiddly) to prove that $\frac{r}{2}\leq \lambda(w^{*})$ where $r= {\mathrm{rank}} \nabla^{2}L(w^{*})$ and as we will see in the next exercise, the LLC captures more information about the geometry than just the Hessian rank.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.6 (LLC vs Hessian Rank).** In this exercise we will show that the LLC can detect differences in the local geometry that are not reflected in the rank of the Hessian.

Construct two loss functions $L_{1}$ and $L_{2}$ with minima $w_{1}$ and $w_{2}$ respectively such that ${\mathrm{rank}} \, \nabla^{2}L_{1}(w_{1}) = {\mathrm{rank}} \, \nabla^{2}L_{2}(w_{2})$ but $\lambda(w_{1}) \neq \lambda(w_{2})$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Let $L_{1}(x,y) = x^{2}+y^{4}$ with $w_{1} = (0,0)$. Then $\nabla^{2}L_{1}(0,0) = \operatorname{diag}(2, 0)$, so $\operatorname{rank}\nabla^{2}L_{1}(0,0) = 1$. By Exercise 3.4, $\lambda(w_{1}) = \frac{3}{4}$.

Let $L_{2}(x,y) = x^{2}$ with $w_{2} = (0,0)$. Then $\nabla^{2}L_{2}(0,0) = \operatorname{diag}(2, 0)$, so $\operatorname{rank}\nabla^{2}L_{2}(0,0) = 1$. The minimiser locus is $\{x = 0\}$, which is the setting of Exercise 3.2 with $d' = 1$, giving $\lambda(w_{2}) = \frac{1}{2}$.

Both Hessians have rank $1$, but $\lambda(w_{1}) = \frac{3}{4}\neq \frac{1}{2}= \lambda(w_{2})$. The difference is that the flat direction in $L_{2}$ is *exactly* flat (the minimisers form a line), while in $L_{1}$ it is only flat to second order but quartic beyond that. The LLC detects this distinction; the Hessian rank does not.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.7 (The cubically-parameterised loss).** We can make a quadratic loss degenerate by changing the parameterisation. Let the *cubically-parameterised loss* be

$$
L(\mu) = \tfrac{1}{2}(\mu^{3} - \mu_{0}^{3})^{2}, \qquad \mu \in {\mathbb{R}}
$$

obtained from the ordinary quadratic loss $\ell(\theta) = \frac{1}{2}(\theta - \theta_{0})^{2}$ via the reparameterisation $\theta = \mu^{3}$, $\theta_{0} = \mu_{0}^{3}$.

**(a)** Show that the cubically-parameterised loss is just as expressive as the ordinary quadratic loss: that is, they both have the same set of achievable minima.

**(b)** Compute the Hessian $L''(\mu_{0})$ to show that the loss is degenerate at its minimum when $\mu_{0} = 0$, and non-degenerate when $\mu_{0} \neq 0$.

**(c)** Give an explicit formula for $V(\epsilon)$ when $\mu_{0} = 0$ and $\mu_{0} \neq 0$ separately.

**(d)** Use your answer to part (c) to find the learning coefficient for $\mu_{0}=0$ and for $\mu_{0}\neq0$. Given that the model is non-degenerate when $\mu_{0} \neq 0$, we expect the learning coefficient to be $d/2$ in that case; compare your answer. How does the cubically-parameterised loss at $\mu_{0} = 0$ differ from the ordinary quadratic loss?

**(e)** Instead of taking $\epsilon \to 0$ to get the learning coefficient, fix a small but nonzero value for $\epsilon$, such as $\epsilon = 0.01$. Plot $V(\epsilon)$ as a function of $\mu_{0}$. As we saw from (d), the learning coefficient changes discontinuously when $\mu_{0} = 0$—what happens with $V(\epsilon)$ as $\mu_{0}$ gets close to zero? What changes if you make $\epsilon$ smaller or larger?

Even though the asymptotic *learning coefficient* ($\epsilon \to 0$) only changes when $\mu_{0} = 0$ exactly, note how the non-asymptotic *volume* ($\epsilon$ finite) is affected in a larger neighbourhood.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The cubically-parameterised loss $L(\mu) = \tfrac{1}{2}(\mu^{3} - \mu_{0}^{3})^{2}$ vanishes if and only if $\mu^{3} = \mu_{0}^{3}$, i.e.  $\mu = \mu_{0}$ (since $t \mapsto t^{3}$ is a bijection on ${\mathbb{R}}$). The ordinary quadratic loss $\ell(\theta) = \tfrac{1}{2}(\theta - \theta_{0})^{2}$ vanishes if and only if $\theta = \theta_{0}$. Since for every $\theta_{0} \in {\mathbb{R}}$ we can write $\theta_{0} = \mu_{0}^{3}$ for a unique $\mu_{0} = \theta_{0}^{1/3}$, both losses achieve their minimum value of zero at exactly the same set of "targets" $\theta_{0} \in {\mathbb{R}}$, so the set of achievable minima is the same.

**(b)** Computing derivatives:

$$
\begin{aligned}L'(\mu)&= 3\mu^{2}(\mu^{3} - \mu_{0}^{3}), \\ L''(\mu)&= 6\mu(\mu^{3} - \mu_{0}^{3}) + 9\mu^{4}.\end{aligned}
$$

At the minimum $\mu = \mu_{0}$: $L''(\mu_{0}) = 6\mu_{0} \cdot 0 + 9\mu_{0}^{4} = 9\mu_{0}^{4}$.

- If $\mu_{0} = 0$: $L''(0) = 0$, so the Hessian vanishes and the loss is degenerate at its minimum.
- If $\mu_{0} \neq 0$: $L''(\mu_{0}) = 9\mu_{0}^{4} > 0$, so the loss is non-degenerate.

**(c)** We compute $V(\epsilon) = \mathrm{vol}(\{\mu \in {\mathbb{R}} : L(\mu) < \epsilon\})$ in each case.

*Case $\mu_{0} = 0$.* When $\mu_{0} = 0$ the loss simplifies to $L(\mu) = \tfrac{1}{2}\mu^{6}$, so

$$
V(\epsilon) = \int_{\frac{1}{2}\mu^6 < \epsilon}d\mu = \int_{|\mu| < (2\epsilon)^{1/6}}d\mu = 2(2\epsilon)^{1/6}= 2^{7/6}\,\epsilon^{1/6}.
$$

*Case $\mu_{0} \neq 0$.* The sublevel set condition $L(\mu) < \epsilon$ is $\tfrac{1}{2}(\mu^{3} - \mu_{0}^{3})^{2} < \epsilon$, i.e.

$$
\mu_{0}^{3} - \sqrt{2\epsilon}\;<\; \mu^{3} \;<\; \mu_{0}^{3} + \sqrt{2\epsilon}.
$$

Since the cube root is monotone on ${\mathbb{R}}$, this is equivalent to

$$
\bigl(\mu_{0}^{3} - \sqrt{2\epsilon}\bigr)^{1/3}\;<\; \mu \;<\; \bigl(\mu_{0}^{3} + \sqrt{2\epsilon}\bigr)^{1/3},
$$

and therefore

$$
V(\epsilon) = \bigl(\mu_{0}^{3} + \sqrt{2\epsilon}\bigr)^{1/3}- \bigl(\mu_{0}^{3} - \sqrt{2\epsilon}\bigr)^{1/3}.
$$

**(d)** **Case $\mu_{0} = 0$:** $V(\epsilon) \propto \epsilon^{1/6}$, so $\lambda = \tfrac{1}{6}$.

**Case $\mu_{0} \neq 0$:** For small $\epsilon$ we expand by factoring out $\mu_{0}$:

$$
V(\epsilon) = \mu_{0} \left[ \left(1 + \frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}\right)^{\!1/3}- \left(1 - \frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}\right)^{\!1/3}\right].
$$

Applying the binomial expansion $(1+x)^{1/3}= 1 + \tfrac{1}{3}x + o(x)$ to each term with $x = \pm\frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}$, the constant terms cancel and the linear terms add:

$$
V(\epsilon) = \mu_{0} \left[ \frac{1}{3}\frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}+ \frac{1}{3}\frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}+ o(\epsilon^{1/2}) \right] = \frac{2\sqrt{2}}{3\mu_{0}^{2}}\,\epsilon^{1/2}+ o(\epsilon^{1/2}).
$$

In the non-degenerate case $\mu_{0} \neq 0$, we recover the regular value $\lambda = d/2 = 1/2$ as expected. In the degenerate case $\mu_{0} = 0$, $\lambda = 1/6 < 1/2$: the singularity at $\mu = 0$ (where the loss vanishes to sixth order rather than second order) makes the model effectively simpler than its parameter count suggests.

**(e)** From part (c), for fixed $\epsilon > 0$ we plot

$$
V(\epsilon;\, \mu_{0}) = \bigl(\mu_{0}^{3} + \sqrt{2\epsilon}\bigr)^{1/3}- \bigl(\mu_{0}^{3} - \sqrt{2\epsilon}\bigr)^{1/3}
$$

The function is a smooth, symmetric bump centred at $\mu_{0} = 0$ with no discontinuity. Making $\epsilon$ smaller narrows the bump and lowers the peak; making $\epsilon$ larger widens it. Despite the learning coefficient jumping discontinuously from $1/2$ to $1/6$ at $\mu_{0} = 0$ exactly, the finite-$\epsilon$ volume transitions smoothly, with the singularity's influence confined to a neighbourhood that shrinks as $\epsilon \to 0$.

:::

---
id: 'a6248853-b3f7-4aba-a051-b94e8abfcb66'
title: "B.5.11 From unrolling to influence functions"
tldr: "Long Exercise 4.2: show that unrolling with an interpolated loss converges to the influence function, first for full-batch gradient descent and then for SGD, including the null-space behaviour."
summary_for_tutor: "Section 4.3 of Iliad worksheet B.5 Data Attribution: Exercise 4.2 (a)-(c) with collapsed solution. (a) the response recursion with J_t, (b) the full-batch GD warm-up, (c) SGD with decaying learning rate, where part i shows the equilibrium is r_IF = H^+ grad L(w*, z_k) and part ii shows the null-space component grows linearly. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 4.3 Long Exercise: From unrolling to influence functions

The unrolling formula (20) and the influence function (6) appear to be very different objects: one is a sum over training steps of Jacobian-propagated gradients, the other is a single inverse-Hessian-times-gradient computation at the endpoint. The following exercise shows that, in the right limit, unrolling converges to the classical influence function. The key observation, due to Mlodozeniec et al. 2025, is that the joint process $$(w_{t}, r_{t})$$, where $$r_{t} := \partial w_{t}/\partial\varepsilon\big|_{\varepsilon=0}$$ is the unrolling response, forms a *Markov chain*, and its limiting behavior can be analyzed with standard stochastic-approximation tools. This yields a convergence result that requires only that SGD reaches a local minimum, *not* that the loss is convex.

:::callout {title="Exercise" tone="amber"}
**Exercise 4.2 (Convergence of unrolling to influence functions).** Consider the SGD update with an interpolated loss that downweights example $$z_{k}$$ by $$\varepsilon$$:

$$
w_{t+1}(\varepsilon) \;=\; w_{t}(\varepsilon) \;-\; \frac{\eta_{t}}{b}\sum_{i\in B_t}\bigl(1 - \varepsilon\,\mathbf{1}[i=k]\bigr)\,\nabla_{w} L(w_{t}(\varepsilon),z_{i}),
$$

so $$\varepsilon = 0$$ is the original training run and $$\varepsilon = 1/n$$ corresponds to removing $$z_{k}$$. Define the *response* $$r_{t} := \partial w_{t}(\varepsilon)/\partial\varepsilon\big|_{\varepsilon=0}$$.

$$
\begin{pmatrix}w_{t+1}\\ r_{t+1}\end{pmatrix} \;=\; \underbrace{\begin{pmatrix}I&0 \\ 0&J_{t}\end{pmatrix}}_{\text{propagation}}\begin{pmatrix}w_{t} \\ r_{t}\end{pmatrix} \;+\; \underbrace{\begin{pmatrix}-\frac{\eta_t}{b}\sum_{i\in B_t}\nabla_{w} L(w_{t},z_{i}) \\[4pt] \frac{\eta_t}{b}\,\mathbf{1}[k\in B_{t}]\,\nabla_{w} L(w_{t},z_{k})\end{pmatrix}}_{\text{driving terms}}
$$

**(a)** **(The response recursion.)** By differentiating (34) with respect to $$\varepsilon$$ at $$\varepsilon = 0$$, derive (35), where $$J_{t} = I - \frac{\eta_{t}}{b}\sum_{i\in B_t}\nabla_{w}^{2} L(w_{t},z_{i})$$ is the step Jacobian from (17). The top row is ordinary SGD; verify that the bottom row is the same recursion as Exercise 4.1(a), but now with stochastic batches. Since the driving terms depend only on $$(w_{t}, r_{t})$$ and the i.i.d. batch selection $$B_{t}$$, the joint process is a Markov chain. Why is this observation useful?

**(b)** **(Deterministic warm-up: full-batch GD.)** As a warm-up, consider full-batch gradient descent with constant learning rate $$\eta$$ (i.e. $$B_{t} = \{1,\dots,n\}$$ for all $$t$$). Assume training has converged: $$w_{t} \approx w^{*}$$ and $$\nabla_{w}^{2} L(w_{t}) \approx H$$ for all $$t$$ in a window of length $$K$$. Show that the response over this window satisfies

$$
r_{T} \;\approx\; -\bigl[I - (I-\eta H)^{K}\bigr]\,H^{-1}\,\nabla_{w} L(w^{*},z_{k}).
$$

*Hint:* Sum the geometric series $$\sum_{t=0}^{K-1}(I-\eta H)^{t}$$ using the identity $$\sum_{t=0}^{K-1}M^{t} = (I-M^{K})(I-M)^{-1}$$.

Take $$K\to\infty$$ (assuming $$\eta < 2/\lambda_{\max}(H)$$) and recover the influence function $$r_{\infty} = -H^{-1}\nabla_{w} L(w^{*},z_{k}) = r_{\mathrm{IF}}$$.

**(c)** **(Stochastic case: convergence to IF.)** Now return to SGD with i.i.d. batches and a decaying learning rate satisfying $$\sum_{t} \eta_{t} = \infty$$, $$\sum_{t} \eta_{t}^{2} < \infty$$ (the Robbins–Monro conditions). Assume SGD converges to a local minimum $$w^{*}$$ with $$H = \nabla_{w}^{2} L(w^{*})$$ positive semidefinite. The continuous-time ODE that the response tracks is

$$
\dot{r}(t) \;=\; -H\,r(t) \;+\; \nabla_{w} L(w^{*},z_{k}).
$$

(You do not need to prove that SGD tracks this ODE, this follows from standard stochastic approximation theory.)

**i.** Show that the equilibrium of (36) in the column space of $$H$$ is $$r_{\mathrm{IF}}= H^{+}\nabla_{w} L(w^{*},z_{k})$$, where $$H^{+}$$ is the pseudoinverse. This is the influence function, with $$H^{+}$$ in place of $$H^{-1}$$ because the Hessian may be singular at a local minimum of an overparameterized model.

**ii.** Show that the component of $$r(t)$$ in the *null space* of $$H$$ grows linearly: if $$P_{0}$$ is the projector onto $$\ker(H)$$, then $$P_{0}\,r(t) = P_{0}\,r(0) + t\,P_{0}\nabla_{w} L(w^{*},z_{k})$$. Why does this component not converge? Under what condition on $$\nabla_{w} L(w^{*},z_{k})$$ does this runaway term vanish?

The full result (Mlodozeniec et al. 2025, Theorem 2) is: on the set of SGD trajectories that converge to a local minimum, $$r_{t} \to r_{\mathrm{IF}}+ r_{\mathrm{NS}}$$ almost surely, where $$r_{\mathrm{NS}}\in \ker(H)$$. The influence function is the limiting response, up to a component in the flat directions of the loss.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* Differentiating (34) with respect to $$\varepsilon$$ at $$\varepsilon = 0$$: the first row is just the SGD update, independent of $$\varepsilon$$. For the response, the chain rule gives two contributions: the indirect effect through $$w_{t}(\varepsilon)$$ picks up the mini-batch Hessian (giving $$J_{t}\,r_{t}$$ as in Exercise 4.1), and the direct effect from the $$(1-\varepsilon\,\mathbf{1}[i=k])$$ factor contributes $$+(\eta_{t}/b)\,\mathbf{1}[k\in B_{t}]\,\nabla_{w} L(w_{t},z_{k})$$. This is (35). Given the current state $$(w_{t},r_{t})$$ and the batch selection $$B_{t}$$ (which is i.i.d. and independent of history), the next state $$(w_{t+1},r_{t+1})$$ depends only on $$(w_{t},r_{t})$$ — no earlier states are needed. This is the Markov property.

*(b)* With full-batch GD, $$B_{t} = \{1,\dots,n\}$$, the response recursion becomes deterministic: $$r_{t+1}= (I-\eta H)r_{t} + \eta\nabla_{w} L(w^{*},z_{k})$$. With $$r_{0} = 0$$, unrolling gives $$r_{K} = \eta\sum_{t=0}^{K-1}(I-\eta H)^{t}\,\nabla_{w} L(w^{*},z_{k})$$. Using $$\sum_{t=0}^{K-1}M^{t} = (I-M^{K})(I-M)^{-1}$$ with $$M = I-\eta H$$:

$$
r_{K} = [I-(I-\eta H)^{K}]\,H^{-1}\,\nabla_{w} L(w^{*},z_{k}).
$$

(Note the sign: the interpolation $$1-\varepsilon\,\mathbf{1}[i=k]$$ downweights $$z_{k}$$, so the direct effect has the opposite sign from the $$\beta$$-upweighting in Exercise 4.1.) Since $$\|I-\eta H\| < 1$$ when $$\eta < 2/\lambda_{\max}(H)$$, $$(I-\eta H)^{K} \to 0$$ and $$r_{\infty} = H^{-1}\nabla_{w} L(w^{*},z_{k}) = r_{\mathrm{IF}}$$.

*(c)* i. At equilibrium $$\dot r = 0$$, the ODE (36) gives $$Hr_{\infty} = \nabla_{w} L(w^{*},z_{k})$$. In the column space of $$H$$, this has the unique solution $$r_{\mathrm{IF}}= H^{+}\nabla_{w} L(w^{*},z_{k})$$. (If $$H$$ is invertible, $$H^{+} = H^{-1}$$ and this is the classical IF.)

ii. Project the ODE onto $$\ker(H)$$: $$P_{0}\dot{r}(t) = -P_{0} H\,r(t) + P_{0}\nabla_{w} L(w^{*},z_{k}) = P_{0}\nabla_{w} L(w^{*},z_{k})$$, since $$P_{0} H = 0$$. Integrating: $$P_{0} r(t) = P_{0} r(0) + t\,P_{0}\nabla_{w} L(w^{*},z_{k})$$. This grows linearly unless $$P_{0}\nabla_{w} L(w^{*},z_{k}) = 0$$, i.e. unless the per-example gradient has no component in the Hessian null space. The null space of $$H$$ at a local minimum corresponds to flat directions along the minimum manifold; the response diverges if the perturbation "pushes" along these flat directions, because the optimizer has no restoring force.

:::

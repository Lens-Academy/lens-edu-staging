---
id: '0bc6c64a-0a3a-4b07-bd0d-98978c4c409c'
title: "B.6.7 The NTK and features"
tldr: "Gradient flow, its geometry on a manifold, and the neural tangent kernel as the induced inverse metric on function values."
summary_for_tutor: "Section 4 intro and 4.1 of Iliad worksheet B.6 Physics of Deep Learning. Covers gradient flow as the continuous-time limit of GD, gradient flow on Riemannian manifolds with the inverse metric, the pushforward through the map from parameters to training outputs, the NTK Theta^{mu nu}, and the flow equation for function values read as parallel transport. Contains Exercise 4.1 (NTK from the chain rule) and Exercise 4.2 (how fast the kernel moves), both with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## 4. The NTK and large width during training

In this section, we consider training networks that are randomly initialized as in Section 3.2, and their behavior at large width. The lesson will be that as width$$\to\infty$$ these networks effectively behave like linear models: their parameters $$\theta$$ never stray far from their values $$\theta_{0}$$ at initialization, hence

$$
f_{\theta}(x) \approx f^{\rm lin}_{\theta}(x) := f_{\theta_0}(x) + (\theta-\theta_{0})\cdot \nabla_{\theta} f_{\theta_0}(x)\,.
$$

Under suitable conditions, the network itself also converges exponentially fast to a "memorizing network" that fits the training data perfectly. Heuristically, this happens because small changes in many parameters, as in (4.1), can add up to an order-one change in the network values themselves. Nevertheless, the network never experiences phase transitions or feature learning — we'll make this more precise below. The large-width regime (at finite depth and training data) is thus known as the *lazy* regime, or the NTK regime. (For a self-contained review of models that are linear in their parameters, and of why training them amounts to kernel ridge regression, see Appendix B.)

Although this regime does not describe the feature learning that makes practical networks interesting, it is important to understand for at least two reasons: it is an honest, analytically solvable model of training; and it is a precise lesson in what must be *avoided* if one wants genuine feature learning — a lesson we act on in Section 5.

We also emphasize the connection between Section 3 and the current analysis. Both involve the *same* large-width limit. At initialization, it leads to a Gaussian process. During training, we'll see that it leads to a linear model with lazy learning, converging once again to a GP at late training times.

\### 4.1 Gradient flow and the NTK

Throughout this section, we approximate SGD with continuous-time *gradient flow* (*cf.* Section 2.1). This involves two approximations. First we update on the entire training dataset $$\{(x^{\mu},y^{\mu})\}_{\mu=1}^{n}$$ at each step, rather than on batches, so that SGD becomes GD:

$$
\theta_{k+1}- \theta_{k} = - \eta_{GD}\, \nabla_{\theta} {{\mathcal L}}_{\theta}(\{x^{\mu},y^{\mu}\}) \big|_{\theta=\theta_k}
$$

where

$$
{{\mathcal L}}_{\theta} = {{\mathcal L}}_{\theta}(\{x^{\mu},y^{\mu}\}) := \sum_{\mu=1}^{n} \ell_{\theta}(x^{\mu},y^{\mu})
$$

is the full empirical loss.

Second, we scale down the learning rate $$\eta_{GD}=\lambda^{-1}\eta$$ and scale up the number of training steps, setting $$k = \lfloor \lambda t]$$ where $$t\geq 0$$ is a continuous "time" variable. As $$\lambda\to\infty$$, the gradient descent converges to a gradient flow

$$
\dot\theta := \frac{d}{dt}\theta = - \eta\, \nabla_{\theta} {{\mathcal L}}_{\theta}\,.
$$

All theorems in this section can be extended to SGD, adding additional error terms to bound the difference between SGD and GF. (See for example (Spiliopoulos et al. 2025, Chapter 19).)

\#### 4.1.1 Geometry of gradient flows

Suppose that $$X$$ is a smooth Riemannian manifold, with nondegenerate metric $$g = g_{ab}dx^{a} dx^{b}$$, inverse metric $$g^{-1}= g^{ab}\frac{\partial}{\partial x^{a}}\frac{\partial}{\partial x^{b}}$$, and a function $$h:X\to {\mathbb{R}}$$. Then one can define gradient flow with respect to $$(h,g)$$ as

$$
\dot x^{a}(t) = -\eta\, g^{ab}\frac{\partial h}{\partial x^{b}}\,, \qquad \text{or abstractly:}\quad \dot x = -\eta\, g^{-1}(dh) \,.
$$

Note that this equation does not make sense (it's not coordinate-free) without an inverse-metric (a bilinear form on each cotangent space $$T^{*}X$$). The inverse-metric is used to relate the differential $$dh = (\partial_{b} h)_{b=1}^{\text{dim} X}$$ on the RHS to a *vector field* $$g^{-1}dh$$, which is the right sort of geometric object to induce a flow on $$X$$.

In neural networks, $$X={\mathbb{R}}^{P}$$ is the space of parameters $$\theta$$ and $$h = {{\mathcal L}}$$ is the loss function. One always assumes a constant Euclidean metric in parameter space $$g = \sum_{i=1}^{P} (d\theta^{i})^{2} = \delta_{ij}d\theta^{i} d\theta^{j}$$, in order to define SGD/GD/GF/etc. This is the source of some of the simplest inductive biases of trained models, and also why one expects "features" to have some linear structure. Eqn. (4.5) with the metric looks like

$$
\dot\theta^{i} = -\eta\, \delta^{ij}\, \partial_{j} {{\mathcal L}}_{\theta}\,.
$$

Now return to the general setting of Riemannian manifolds. Suppose we have a smooth map $$f : X \to Y$$ between two manifolds, and moreover that $$h:X\to {\mathbb{R}}$$ is the pull-back of a function $$h^{Y}:Y\to {\mathbb{R}}$$, meaning $$h(x) = h^{Y}(f(x))$$. Let $$\{f^{\alpha}\}_{\alpha=1}^{\text{dim}\, Y}$$ be the components of the map $$f$$, in local coordinates $$y^{\alpha}$$ on $$Y$$. Then the inverse-metric on $$X$$ induces an inverse-metric on $$Y$$ (called its push-forward):

$$
f_{*}(g^{-1}) = f_{*}\bigg[g^{ab}\frac{\partial}{\partial x^{a}}\frac{\partial}{\partial x^{b}}\bigg] = \underbrace{g^{ab} \frac{\partial f^{\alpha}}{\partial x^{a}} \frac{\partial f^{\beta}}{\partial x^{b}}}_{g^{\alpha \beta}}\frac{\partial}{\partial y^{\alpha}}\frac{\partial}{\partial y^{\beta}}\,.
$$

Schematically, $$g^{\alpha\beta}= (J g^{-1}J^{T})$$, where $$J^{\alpha}{}_{a} = \frac{\partial f^{\alpha}}{\partial x^{a}}$$ is the Jacobian matrix of $$f$$. Then the gradient flow on $$X$$ induces a gradient flow on $$Y$$, given by

$$
\dot y^{\alpha} = -\eta\, g^{\alpha\beta}\frac{\partial h^{Y}}{\partial y^{\beta}}\,.
$$

Let's apply this to neural networks, where $$f:{\mathbb{R}}^{P}\to {\mathbb{R}}^{n}$$ is the function from parameters to network outputs on the training data $$(x^{\mu},y^{\mu})$$, *i.e.* $$f^{\mu}(\theta) = f_{\theta}(x^{\mu})$$ in our standard notation. The loss function is indeed a pullback of a function on $${\mathbb{R}}^{n}$$, since it depends on parameters $$\theta$$ only through the network values on training data,

$$
{{\mathcal L}}_{\theta} = {{\mathcal L}}^{(f)}(f(\theta))\,,\qquad {{\mathcal L}}^{(f)}(f) := \sum_{\mu=1}^{n} \ell( f^{\mu},y^{\mu})\,.
$$

The push-forward of the gradient flow in parameter space becomes

$$
\frac{d}{dt}f^{\mu} = -\eta\, \Theta^{\mu\nu}\frac{\partial {{\mathcal L}}^{(f)}}{\partial f^{\nu}}\,,\qquad \Theta^{\mu\nu}= (J \delta^{-1}J^{T})^{\mu\nu}= \sum_{i=1}^{P} \frac{\partial f_{\theta}(x^{\mu})}{\partial \theta^{i}}\frac{\partial f_{\theta}(x^{\nu})}{\partial \theta^{i}}\,.
$$

The inverse-metric $$\Theta^{\mu\nu}$$ on the space of function values is called the "neural tangent kernel" or NTK. The name was coined in (Jacot et al. 2018); it also appeared in (Du et al. 2019) under a different name. Here we are emphasizing that it's a completely natural geometric object, for any neural network (in fact, for any ML model).

We mention one final bit of geometry. Let $$\delta_{\mu\nu}$$ be a standard Euclidean metric in the space of function values, with inverse $$\delta^{\mu\nu}$$. The gradient of the loss $$\delta^{\mu\nu}\partial {{\mathcal L}}^{(f)}/\partial f^{\nu}$$ that appears in (4.10) (contracted with an inverse metric) is sometimes called the *residual*, and denoted $$\Delta^{\mu}$$ or $$r^{\mu}$$. For MSE loss, we've got $${{\mathcal L}}^{(f)}= \frac{1}{2}\sum_{\mu=1}^{n} (f^{\mu}-y^{\mu})^{2} = \frac{1}{2}\delta_{\mu\nu}(f^{\mu}-y^{\mu})(f^{\nu}-y^{\nu})$$. Then the residual is just the difference between function values and truth for the training data:

$$
\Delta^{\mu} := \delta^{\mu\nu}\partial {{\mathcal L}}^{(f)}/\partial f^{\nu} = f^{\mu}-y^{\mu}\,.
$$

Noting that $$y^{\mu}$$ are constants, the gradient-flow equation can be recast as

$$
\frac{d}{dt}\Delta^{\mu} = - \eta\, \underbrace{\Theta^{\mu\rho}\delta_{\rho\nu}}_{\displaystyle \Theta^\mu{}_{\nu}}\Delta^{\nu}\,.
$$

Those who have studied gauge theory may recognize this as an equation for *parallel transport*, with respect to an $$n\times n$$ matrix-valued connection $$\eta\,\Theta^{\mu}{}_{\nu}$$. If one knows the dependence of $$\Theta$$ on time (which in general is far from trivial — see the exercise below) the solution is a time-ordered exponential

$$
\Delta^{\mu}(t) = \bigg(P\exp\bigg[-\eta\int \Theta(t)\,dt\bigg]\bigg)^{\mu}_{\;\nu}\Delta^{\nu}(0)\,.
$$

:::callout {title="Exercise" tone="amber"}
**Exercise 4.1 (The NTK from the chain rule).** Derive the flow equation (4.10) for the function values $$f^{\mu}$$ directly, using only the chain rule — no geometry required. (The geometric derivation explains *why* an object like $$\Theta^{\mu\nu}$$ had to appear; the chain rule shows it appears in three lines.)
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By the chain rule and the gradient-flow equation,

$$
\begin{aligned}\frac{d}{dt}f^{\mu}&= \nabla_{\theta} f^{\mu} \cdot \dot\theta = -\eta\, \nabla_{\theta} f^{\mu} \cdot \nabla_{\theta} {{\mathcal L}} \\&= -\eta\, \nabla_{\theta} f^{\mu} \cdot \sum_{\nu} \nabla_{\theta} f^{\nu}\, \frac{\partial {{\mathcal L}}^{(f)}}{\partial f^\nu}= -\eta\, \Theta^{\mu\nu}\, \frac{\partial {{\mathcal L}}^{(f)}}{\partial f^\nu}\,,\end{aligned}
$$

using in the middle step that $${{\mathcal L}}$$ depends on $$\theta$$ only through the function values $$f^{\nu}$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.2 (How fast does the kernel move?).** Show that the time derivative of the NTK satisfies

$$
\frac{d}{dt}\Theta^{\mu\nu}= -\eta\,\big[ \nabla_{\theta} f^{\mu} \cdot \nabla_{\theta}^{2} f^{\nu} \cdot \nabla_{\theta} f^{\rho}\big] \frac{\partial {{\mathcal L}}^{(f)}}{\partial f^{\rho}}+ (\mu\leftrightarrow\nu)\,,
$$

where $$\nabla_{\theta}^{2} f^{\nu} = \nabla_{\theta}^{2} f_{\theta}(x^{\nu})$$ is the Hessian. Bounding the Hessian ultimately leads to the constant-NTK theorem in Section 4.3 below.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Differentiate $$\Theta^{\mu\nu}= \nabla_{\theta} f^{\mu}\cdot\nabla_{\theta} f^{\nu}$$ along the flow: $$\frac{d}{dt}\Theta^{\mu\nu}= \dot\theta\cdot\nabla^{2}_{\theta} f^{\mu}\cdot \nabla_{\theta} f^{\nu} + \nabla_{\theta} f^{\mu} \cdot \nabla^{2}_{\theta} f^{\nu}\cdot\dot\theta$$. Substituting $$\dot\theta = -\eta\,\nabla_{\theta} f^{\rho}\, \partial{{\mathcal L}}^{(f)}/\partial f^{\rho}$$ gives the stated formula. Taking operator norms, $$\|\dot\Theta\| \lesssim \eta\, \|\nabla^{2}_{\theta} f\|\,\|\nabla_{\theta} f\|^{2}\, |\partial{{\mathcal L}}/\partial f| \sim \eta\,\|\nabla^{2}_{\theta} f\|\, \|\Theta\|\,|\Delta|$$: the kernel can only move as fast as the Hessian of the *network function* (not of the loss) allows — which is why bounding that Hessian at large width freezes the kernel.

:::

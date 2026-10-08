---
id: '4350a384-00cd-4499-b89b-7b4f7bf2d5c4'
title: "B.5.3 The influence function formula"
tldr: "Introduces influence functions from robust statistics, defines the parameter influence with the inverse Hessian, relates it to leave-one-out, and has Exercise 2.1 deriving the formula with the implicit function theorem."
summary_for_tutor: "Start of Section 2 of Iliad worksheet B.5 Data Attribution: Example 2.1 (influence on the mean), Definition 2.2 (influence function, inverse Hessian times gradient, at the minimum w*), the link to leave-one-out through beta = 1 minus e_i, and Exercise 2.1 (a)-(c) deriving the formula via the implicit function theorem and chain rule, with a collapsed solution. Keep the notation w*(beta), H, I(z_i, phi). Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 2. Influence Functions

In this section we develop *influence functions*: a closed-form, first-order approximation to the leave-one-out (LOO) counterfactual. The classical theory (Hampel 1974; Cook 1977) predates machine learning by decades. It was developed in robust statistics, where the question was which observations a parameter estimate is most sensitive to. For simple statistical models the answer is short: a single application of the implicit function theorem yields an inverse-Hessian-times-gradient formula whose factors have a clean operational interpretation.

The formula we arrive at then *can* be translated to the setup of neural networks, but its interpretation becomes unclear: The classical derivation assumes a unique global minimum and an invertible Hessian, neither of which holds for a neural network which is typically **not** trained to full convergence. We will see a partial fix for this issue in Section 2.2.

\### 2.1 The influence function formula

Influence functions originate in robust statistics (Hampel 1974): given a statistical estimator, how much does it change when a single observation is added or perturbed?

:::callout {title="Tip" tone="green"}

**Example 2.1 (Influence on the mean).** Let $$T(F) = \mathbb{E}_{F}[z]$$ be the mean of a distribution $$F$$. If we contaminate $$F$$ by placing a fraction $$\epsilon$$ of its mass at a point $$z$$, the new mean is

$$
T\bigl((1-\epsilon)F + \epsilon\,\delta_{z}\bigr) \;=\; (1-\epsilon)\,\mathbb{E}_{F}[z] \;+\; \epsilon\,z \;=\; T(F) \;+\; \epsilon\,(z - T(F)).
$$

The rate of change at $$\epsilon = 0$$ is $$z - T(F)$$: the influence of $$z$$ on the mean is simply how far $$z$$ is from the current mean. Observations far from the centre of the data move the mean the most.

:::

We now translate this idea into the setting of Section 1.4, whose notation we use throughout. Recall that the weighted training loss $$L(w;\beta) = \sum_{i} \beta_{i} L(w,z_{i})$$ defines a family of optimization problems parameterized by the weight vector $$\beta$$. In the case of influence functions, we measure the influence of a data point on the *optimal* parameters

$$
w^{*}(\beta) \;:=\; {\operatorname*{arg\,min}}_{w\in W}\, L(w;\beta),
$$

and we write $$w^{*} := w^{*}(\mathbf{1})$$ for the trained parameters. We assume throughout this subsection that $$w^{*}$$ is the unique global minimum of $$L$$ and that the Hessian $$H := \nabla_{w}^{2} L(w^{*})$$ is positive definite, so that the implicit function theorem makes $$w^{*}(\beta)$$ well-defined and smooth in a neighborhood of $$\beta=\mathbf{1}$$. In the notation of Equation 1 we set $$\pi(\beta)= w^{*}(\beta)$$ and Equation 3 yields then the following formula:

:::callout {title="Definition" tone="blue"}

**Definition 2.2 (Influence function).** The *parameter influence* of training example $$z_{i}$$ at the trained parameters $$w^{*}$$ is

$$
\mathcal{I}_{\mathrm{param}}(z_{i}) \;:=\; \frac{\partial w^{*}(\beta)}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}.
$$

Under the assumptions above, the implicit function theorem gives (Exercise 2.1)

$$
\boxed{\;\mathcal{I}_{\mathrm{param}}(z_i) \;=\; -\,H^{-1}\,\nabla_w L(w^*,z_i).\;}
$$

where $$H$$ is the Hessian of $$L$$ at $$w^{*}$$. For any differentiable observable $$\phi:W\to\mathbb{R}$$, the chain rule then yields the *influence on $$\phi$$*:

$$
\begin{aligned}\mathcal{I}(z_{i},\phi) \;&:=\; \frac{\partial\,\phi(w^{*}(\beta))}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}\\&=\; \nabla_{w} \phi(w^{*})^{\top}\,\mathcal{I}_{\mathrm{param}}(z_{i}) \\&=\; -\,\nabla_{w} \phi(w^{*})^{\top}\,H^{-1}\,\nabla_{w} L(w^{*},z_{i}).\end{aligned}
$$

:::

Thus we get three components

- $$\nabla_{w} L(w^{*},z_{i})$$ is the direction in parameter space along which $$z_{i}$$ pulls the optimizer.
- $$H^{-1}$$ rescales this direction by local curvature: directions in which the loss is flat (small eigenvalue of $$H$$) get amplified, since a small force in a flat direction moves the minimum a lot.
- $$\nabla_{w} \phi(w^{*})$$ projects the parameter change onto the direction that matters for the observable $$\phi$$.

In this section, we will focus on $$\mathcal{I}_{\mathrm{param}}(z_{i})$$. The influence on any observable $$\phi$$ is obtained by computing the dot product $$\mathcal{I}_{\mathrm{param}}(z_{i}) \cdot \nabla_{w}\phi(w^{*})$$.

**Connection to leave-one-out.**  Setting $$\beta = \mathbf{1}- e_{i}$$ (i.e., removing $$z_{i}$$) and applying the first-order Taylor expansion gives

$$
w^{*}(\mathbf{1}- e_{i}) \;-\; w^{*} \;\approx\; -\,\mathcal{I}_{\mathrm{param}}(z_{i}) \;=\; H^{-1}\,\nabla_{w} L(w^{*},z_{i}),
$$

i.e. the parameter influence is, to first order, the change in $$w^{*}$$ that would result from removing $$z_{i}$$ from the training set entirely.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.1 (Derivation of the influence function).** Let $$w^{*}(\beta) = {\operatorname*{arg\,min}}_{w\in W}\,L(w;\beta)$$ as above and assume the Hessian $$H = \nabla_{w}^{2} L(w^{*})$$ is invertible. Recall that the *implicit function theorem* states: if $$F:W\times B\to\mathbb{R}^{\dim W}$$ is $$C^{1}$$, $$F(w^{*},\mathbf{1})=0$$, and the Jacobian $$\partial F/\partial w$$ at $$(w^{*},\mathbf{1})$$ is invertible, then there is a unique $$C^{1}$$ map $$\beta\mapsto w^{*}(\beta)$$ on a neighborhood of $$\mathbf{1}$$ with $$F(w^{*}(\beta),\beta)\equiv 0$$, whose derivative is obtained by implicit differentiation of $$F$$.

**(a)** Apply the implicit function theorem to $$F(w,\beta) := \nabla_{w} L(w;\beta)$$ to conclude that $$\beta\mapsto w^{*}(\beta)$$ is well-defined and $$C^{1}$$ near $$\mathbf{1}$$. Which hypothesis of the theorem uses the invertibility of $$H$$? Where do we use that $$w^{*}$$ is the unique global minimum (rather than merely a critical point)?

**(b)** By differentiating the first-order optimality condition $$\nabla_{w} L(w^{*}(\beta);\beta)=0$$ with respect to $$\beta_{i}$$, show that

$$
\frac{\partial w^{*}(\beta)}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}\;=\; -\,H^{-1}\,\nabla_{w} L(w^{*},z_{i}).
$$

**(c)** Use the chain rule to obtain the formula for $$\mathcal{I}(z_{i},\phi)$$ in Definition 2.2. Make sure to keep track of the evaluation at $$\beta = \mathbf{1}$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* Set $$F(w,\beta) := \nabla_{w} L(w;\beta) = \sum_{j} \beta_{j}\,\nabla_{w} L(w,z_{j})$$. Then $$F$$ is $$C^{1}$$ in $$(w,\beta)$$ (assuming $$L(\cdot,z_{j})$$ is $$C^{2}$$), and $$F(w^{*},\mathbf{1}) = \nabla_{w} L(w^{*}) = 0$$ because $$w^{*}$$ is a critical point of the unperturbed loss. The Jacobian $$\partial F/\partial w$$ at $$(w^{*},\mathbf{1})$$ equals $$\nabla_{w}^{2} L(w^{*}) = H$$, and the invertibility hypothesis of the implicit function theorem is exactly the assumption that $$H$$ is invertible. The theorem then yields a unique $$C^{1}$$ map $$\beta\mapsto w^{*}(\beta)$$ on a neighborhood of $$\mathbf{1}$$ with $$F(w^{*}(\beta),\beta)\equiv 0$$.

The uniqueness the implicit function theorem provides is only *local*: $$w^{*}(\beta)$$ is uniquely defined as the critical point near $$w^{*}$$. The assumption that $$w^{*}$$ is the unique *global* minimum is what lets us identify this local branch of critical points with the object we actually care about — the argmin. Without it, $${\operatorname*{arg\,min}}_{w} L(w;\beta)$$ could jump to a different basin as $$\beta$$ varies, and the response function would fail to be continuous (let alone differentiable).

*(b)* Define the two-slot function

$$
G(w,\beta) \;:=\; \nabla_{w} L(w;\beta) \;=\; \sum_{j}\beta_{j}\,\nabla_{w} L(w,z_{j}),
$$

so that the optimality condition reads $$G(w^{*}(\beta),\beta) \equiv 0$$. The variable $$\beta$$ enters this identity in two places: once through the first slot via $$w^{*}(\beta)$$, and once directly through the second slot. The multivariate chain rule therefore produces two terms when we differentiate with respect to $$\beta_{i}$$:

$$
\underbrace{\frac{\partial G}{\partial w}\bigg|_{(w^*(\beta),\beta)}\,\frac{\partial w^{*}(\beta)}{\partial \beta_{i}}}_{\text{indirect: } w^* \text{ moves with } \beta}\;+\; \underbrace{\frac{\partial G}{\partial \beta_{i}}\bigg|_{(w^*(\beta),\beta)}}_{\text{direct: explicit } \beta_i \text{ dependence}}\;=\; 0.
$$

The two partials are:

- $$\partial G/\partial w = \nabla_{w}^{2} L(w;\beta)$$, which at $$\beta = \mathbf{1}$$ equals the Hessian $$H$$.
- $$\partial G/\partial \beta_{i}$$: differentiating $$\sum_{j} \beta_{j}\,\nabla_{w} L(w,z_{j})$$ with respect to $$\beta_{i}$$ with $$w$$ held fixed picks out the single $$j=i$$ summand, giving $$\nabla_{w} L(w,z_{i})$$.

Evaluating at $$\beta = \mathbf{1}$$ and solving,

$$
\frac{\partial w^{*}(\beta)}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}\;=\; -\,H^{-1}\,\nabla_{w} L(w^{*},z_{i}).
$$

*(c)* For a differentiable observable $$\phi:W\to\mathbb{R}$$, the chain rule applied to $$\beta\mapsto\phi(w^{*}(\beta))$$ gives

$$
\begin{aligned}\mathcal{I}(z_{i},\phi)&\;=\; \frac{\partial\,\phi(w^{*}(\beta))}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}\\&\;=\; \nabla_{w}\phi(w^{*}(\beta))^{\top}\,\frac{\partial w^{*}(\beta)}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}\\&\;=\; -\,\nabla_{w}\phi(w^{*})^{\top}\,H^{-1}\,\nabla_{w} L(w^{*},z_{i}),\end{aligned}
$$

where in the last step both factors are evaluated at $$\beta = \mathbf{1}$$, i.e. at $$w^{*}$$.

:::

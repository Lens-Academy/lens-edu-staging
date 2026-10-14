---
id: '5e24882f-4b61-4f82-9efa-9f5e86eeedd2'
title: "B.5.9 The unrolling formula"
tldr: "Introduces unrolling, which attributes through the training dynamics, states the unrolling formula for SGD, and has Exercise 4.1 deriving it, followed by a remark on TracIn."
summary_for_tutor: "Section 4, 4.1 and the first part of 4.2 of Iliad worksheet B.5 Data Attribution: the training-dynamics approach, the counterfactual over the training run, the unrolling formula (20) as a sum over steps with Jacobian products J_(t+1):T, a remark on which questions unrolling answers, Exercise 4.1 (a)-(c) (derive the recursion, unroll it, preconditioned SGD) with collapsed solution, and a TracIn remark. Keep J_t, eta_t, T. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Unrolling

The influence functions of Section 2 and the Bayesian influence functions of Section 3 both have something in common: they analyze the *endpoint* of training, not the *dynamics* that led to it. Under the assumptions of the unique global minimum, this is not a problem: the training trajectory is irrelevant, since all roads lead to the same outcome. But in practice the training path will matter a lot. Ultimately, we are studying generalization and this is ultimately a question about the training dynamics. Similarly, the BIF looks at the posterior expectation shifts. To give a concrete failure mode: a training point that appears in the first mini-batch of the first epoch will have a very different effect compared to the same point appearing towards the end of training.

If we write down the training trajectory as a composition of $$\beta$$-dependent maps:

$$
\begin{array}{ccccccccc}{\mathbb{R}}^p & \xrightarrow{\;h_0(\cdot\,;\beta)\;} & {\mathbb{R}}^p & \xrightarrow{\;h_1(\cdot\,;\beta)\;} & \cdots & \xrightarrow{\;h_{T-1}(\cdot\,;\beta)\;} & {\mathbb{R}}^p & \xrightarrow{\;\phi\;} & {\mathbb{R}} \\[4pt] w_0 & \longmapsto & w_1 & \longmapsto & \cdots & \longmapsto & w_T & \longmapsto & \phi(w_T)\end{array}
$$

where each $$h_{t}$$ is one optimizer step (a gradient step, an Adam update, etc.): $$w_{t+1}= h_{t}(w_{t};\beta)$$, we can observe an analogy to a forward pass through a neural network:

$$
\begin{array}{ccccccccc}{\mathbb{R}}^{d_0} & \xrightarrow{\;f_1(\cdot\,;w)\;} & {\mathbb{R}}^{d_1} & \xrightarrow{\;f_2(\cdot\,;w)\;} & \cdots & \xrightarrow{\;f_L(\cdot\,;w)\;} & {\mathbb{R}}^{d_L} & \xrightarrow{\;\ell\;} & {\mathbb{R}} \\[4pt] a_0 & \longmapsto & a_1 & \longmapsto & \cdots & \longmapsto & a_L & \longmapsto & \ell(a_L)\end{array}
$$

where each $$f_{\ell}$$ is one layer: $$a_{\ell}= f_{\ell}(a_{\ell-1}; w)$$.

|  | **Forward pass ** | **Training trajectory** |
| --- | --- | --- |
| Inputs | Model weights $$w$$ | Data weights $$\beta$$ |
| Intermediate states | Activations $$a_{1},\dots,a_{L}$$ | Parameters $$w_{0},\dots,w_{T}$$ |
| Output | Loss $$\ell(\text{logits})$$ | Observable $$\phi(w_{T})$$ |
| Differentiation method | Backpropagation | Unrolling |

*Data attribution via unrolling is to a training run what backprop is to a forward pass: differentiating a composition of maps to identify which inputs matter most.*

This invites the following question: Can we backprop through the *training trajectory*? The gradients with respect to the $$\beta_{i}$$ then indicate which data points would need to be up- or downweighted to change the final observable $$\phi(w_{T})$$. And in principle, we can! We can differentiate through the training computation, step by step, treating the final parameters as an explicit function of every gradient update along the way. The result is a chain-rule expression that decomposes data attribution into per-step contributions and naturally incorporates the optimizer, learning rate schedule, mini-batch ordering, and training duration. We will derive the unrolling formula similar to the backprop formula for a forward pass, and then discuss two approaches to making it practical: one that materializes Jacobians and one that computes Jacobian-vector products implicitly. In the setup of Equation 1 we take $$\pi(\beta)=w_{T}(\beta)$$, the final checkpoint of the training run.

\### 4.1 The training-dynamics approach to attribution

We fix notation for the training process. Given a dataset $$\mathcal{D}= \{z_{1},\dots,z_{n}\}$$ with sample weights $$\beta = (\beta_{1},\dots,\beta_{n})$$, the optimizer runs for $$T$$ steps. At step $$t$$, a mini-batch $$B_{t} \subseteq \{1,\dots,n\}$$ of size $$b$$ is drawn, and the parameters are updated by

$$
w_{t+1}(\beta) \;=\; w_{t}(\beta) \;-\; \frac{\eta_{t}}{b}\sum_{i\in B_t}\beta_{i}\,\nabla_{w} L\bigl(w_{t}(\beta),\,z_{i}\bigr),
$$

where $$\eta_{t}$$ is the learning rate at step $$t$$. At $$\beta = \mathbf{1}$$ this is ordinary SGD on the unweighted loss. The initial parameters $$w_{0}$$ are independent of $$\beta$$. For simplicity we can assume that we are training for one epoch only, so that each example appears in exactly one mini-batch, but the formulas hold more generally.

**The counterfactual.**  We want

$$
\frac{\partial\,\phi(w_{T}(\beta))}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}},
$$

the sensitivity of a final-model observable $$\phi$$ to an infinitesimal change in the weight of training example $$z_{i}$$.

\### 4.2 The unrolling formula

Central to computing the data weight gradient is the Jacobian of one SGD step with respect to the current parameters. Define

$$
J_{t} \;:=\; \frac{\partial w_{t+1}}{\partial w_{t}}\bigg\rvert_{\beta=\mathbf{1}}\;=\; I \;-\; \frac{\eta_{t}}{b}\sum_{i\in B_t}\nabla_{w}^{2} L(w_{t},z_{i}) \;=\; I - \eta_{t}\,\widehat{H}_{t},
$$

where $$\widehat{H}_{t} := \tfrac{1}{b}\sum_{i\in B_t}\nabla_{w}^{2} L(w_{t},z_{i})$$ is the mini-batch Hessian at step $$t$$. The Jacobian of the map from step $$t$$ to step $$t'$$ is the ordered product

$$
J_{t:t'}\;:=\; J_{t'-1}\,J_{t'-2}\cdots J_{t}\;=\; \prod_{s=t}^{t'-1}J_{s} \qquad (t < t').
$$

Similarly, the direct effect of $$\beta_{i}$$ at step $$t$$ (when $$i\in B_{t}$$) is the per-example gradient:

$$
\frac{\partial w_{t+1}}{\partial \beta_{i}}\bigg\rvert_{\substack{\beta=\mathbf{1}\\w_t\text{ fixed}}}\;=\; -\,\frac{\eta_{t}}{b}\,\nabla_{w} L(w_{t},z_{i}) \cdot \mathbf{1}[i\in B_{t}].
$$

The full derivative is obtained by chaining direct effects through remaining steps:

$$
\boxed{\;\frac{\partial w_{T}(\beta)}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}} \;=\; -\sum_{t=0}^{T-1}\frac{\eta_{t}}{b}\;\mathbf{1}[i\in B_t]\;J_{(t+1):T}\;\nabla_w L(w_t,z_i).\;}
$$

Each term in the sum corresponds to one training step in which $$z_{i}$$ appeared in the mini-batch: it is the gradient of $$z_{i}$$ at the parameters of that step, propagated forward through the Jacobians of all subsequent steps.

The influence on an observable $$\phi$$ follows by the chain rule:

$$
\frac{\partial\,\phi(w_{T}(\beta))}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}\;=\; -\,\nabla_{w}\phi(w_{T})^{\top}\sum_{t=0}^{T-1}\frac{\eta_{t}}{b}\;\mathbf{1}[i\in B_{t}]\;J_{(t+1):T}\;\nabla_{w} L(w_{t},z_{i}).
$$

:::callout {title="Note" tone="blue"}

**Remark (Which questions does unrolling answer?).** Equation (20) looks like a sum over training steps and, for a fixed realization of the mini-batch sequence, it *is* a deterministic chain-rule computation. But the training run has randomness (initialization, mini-batch ordering, data augmentation), and so does the counterfactual: if we change $$\beta_{i}$$, the mini-batch sequence might be the same or it might differ. Unrolling as written differentiates through a *specific* training run: it answers the *single-model* attribution question, "how would this particular training trajectory have ended differently?" The *distributional* question, which looks at the expected change over random training, would require averaging (20). This distinction, which we will revisit in Section 5, is the training-dynamics analogue of the single-posterior-mode vs. full-posterior distinction in Section 3.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.1 (Derivation of the unrolling formula).** **(a)** Starting from the SGD update (16), apply the chain rule to write $$\tfrac{\partial w_{t+1}}{\partial \beta_i}\big|_{\beta=\mathbf{1}}$$ as a sum of two terms: one from the explicit dependence on $$\beta_{i}$$ (the direct effect) and one from the dependence of $$w_{t}$$ on $$\beta_{i}$$ (the indirect effect). Show that the result is the recursion

$$
\frac{\partial w_{t+1}}{\partial \beta_{i}}\;=\; J_{t}\,\frac{\partial w_{t}}{\partial \beta_{i}}\;-\; \frac{\eta_{t}}{b}\;\mathbf{1}[i\in B_{t}]\;\nabla_{w} L(w_{t},z_{i}),
$$

with initial condition $$\tfrac{\partial w_0}{\partial \beta_i}= 0$$. Compute the Jacobian $$J_{t}$$ explicitly in terms of the mini-batch Hessian $$\widehat{H}_{t}$$ which leads to (17).

**(b)** Solve the recursion by "unrolling" it (i.e. by substituting repeatedly and using (18)) to obtain (20).

**(c)** **(Preconditioned SGD.)** Suppose instead that the optimizer uses a preconditioner $$P_{t} \succ 0$$:

$$
w_{t+1}(\beta) \;=\; w_{t}(\beta) \;-\; \frac{\eta_{t}}{b}\,P_{t}\sum_{i\in B_t}\beta_{i}\,\nabla_{w} L(w_{t}(\beta),z_{i}).
$$

This includes momentum-free Adam and natural gradient methods as special cases (with appropriate $$P_{t}$$). Show that the step Jacobian becomes $$J_{t}^{(P)}= I - \eta_{t}\,P_{t}\widehat{H}_{t}$$ and that the unrolling formula generalizes to

$$
\frac{\partial w_{T}(\beta)}{\partial \beta_{i}}\bigg\rvert_{\beta=\mathbf{1}}\;=\; -\sum_{t=0}^{T-1}\frac{\eta_{t}}{b}\;\mathbf{1}[i\in B_{t}]\;J_{(t+1):T}^{(P)}\;P_{t}\,\nabla_{w} L(w_{t},z_{i}),
$$

where $$J_{(t+1):T}^{(P)}= \prod_{s=t+1}^{T-1}(I - \eta_{s} P_{s}\widehat{H}_{s})$$. The only change is that each gradient is premultiplied by the preconditioner at the step where it appears. What does this say about the effect of using Adam vs. SGD on the attribution of a data point that appears early in training?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*(a)* Differentiating (16) with respect to $$\beta_{i}$$ at $$\beta = \mathbf{1}$$ via the chain rule:

$$
\begin{aligned}\frac{\partial w_{t+1}}{\partial \beta_{i}}&= \frac{\partial w_{t}}{\partial \beta_{i}}- \frac{\eta_{t}}{b}\sum_{j\in B_t}\Bigl[\underbrace{\nabla_w^2 L(w_t,z_j)\,\frac{\partial w_{t}}{\partial \beta_{i}}}_{\text{indirect}}+ \underbrace{\delta_{ij}\,\nabla_w L(w_t,z_j)}_{\text{direct}}\Bigr] \\&= \Bigl(I - \frac{\eta_{t}}{b}\sum_{j\in B_t}\nabla_{w}^{2} L(w_{t},z_{j})\Bigr)\frac{\partial w_{t}}{\partial \beta_{i}}- \frac{\eta_{t}}{b}\,\mathbf{1}[i\in B_{t}]\,\nabla_{w} L(w_{t},z_{i}) \\&= J_{t}\,\frac{\partial w_{t}}{\partial \beta_{i}}- \frac{\eta_{t}}{b}\,\mathbf{1}[i\in B_{t}]\,\nabla_{w} L(w_{t},z_{i}).\end{aligned}
$$

The initial condition is $$\partial w_{0}/\partial \beta_{i} = 0$$ since $$w_{0}$$ does not depend on $$\beta$$.

*(b)* Substituting the recursion repeatedly:

$$
\begin{aligned}\frac{\partial w_{T}}{\partial \beta_{i}}&= J_{T-1}\frac{\partial w_{T-1}}{\partial \beta_{i}}- \frac{\eta_{T-1}}{b}\,\mathbf{1}[i\in B_{T-1}]\,\nabla_{w} L(w_{T-1},z_{i}) \\&= J_{T-1}\Bigl(J_{T-2}\frac{\partial w_{T-2}}{\partial \beta_{i}}- \frac{\eta_{T-2}}{b}\,\mathbf{1}[i\in B_{T-2}]\,\nabla_{w} L(w_{T-2},z_{i})\Bigr) \\&\qquad - \frac{\eta_{T-1}}{b}\,\mathbf{1}[i\in B_{T-1}]\,\nabla_{w} L(w_{T-1},z_{i}) \\&= \cdots = -\sum_{t=0}^{T-1}\frac{\eta_{t}}{b}\,\mathbf{1}[i\in B_{t}]\,J_{(t+1):T}\,\nabla_{w} L(w_{t},z_{i}),\end{aligned}
$$

where the last step follows from $$\partial w_{0}/\partial \beta_{i} = 0$$ killing the $$J_{0:T}$$ term. This is (20).

*(c)* With the preconditioned update (22), the indirect effect picks up the preconditioner in the Hessian term: $$J_{t}^{(P)}= I - (\eta_{t}/b)\sum_{j\in B_t}P_{t}\nabla_{w}^{2} L(w_{t},z_{j}) = I - \eta_{t} P_{t} \widehat{H}_{t}$$. The direct effect becomes $$-(\eta_{t}/b)\,\mathbf{1}[i\in B_{t}]\,P_{t}\nabla_{w} L(w_{t},z_{i})$$. Unrolling the recursion as in (b) gives (23). The preconditioner $$P_{t}$$ at step $$t$$ acts as a local rescaling of the gradient: Adam's adaptive scaling amplifies gradients in directions with historically small second moments. A datum appearing early in training (when Adam has not yet accumulated accurate statistics) will have its gradient rescaled differently than the same datum appearing later, when $$P_{t}$$ has stabilized. This is a concrete mechanism by which optimizer choice affects per-datum attribution.

:::

:::callout {title="Note" tone="blue"}

**Remark (TracIn).** Pruthi et al. 2020 observed that the Jacobian products $$J_{(t+1):T}$$ in (20) are both the most expensive and the most unstable part of the computation. Their method, TracIn, simply drops them, setting $$J_{(t+1):T}\approx I$$:

$$
\mathrm{TracIn}(z_{i},\phi) \;:=\; \sum_{t\in\mathcal{C}}\eta_{t}\;\nabla_{w}\phi(w_{t})^{\top}\nabla_{w} L(w_{t},z_{i}),
$$

where $$\mathcal{C}$$ is a set of checkpoints (typically one per epoch).

:::

There are two ways to make (20) practical. The first is to compute the Jacobian products $$J_{(t+1):T}$$ explicitly, or rather an approximation thereof. The second is to avoid materializing Jacobians altogether and instead compute Jacobian-vector products implicitly by reverse-mode automatic differentiation through the training loop. We will discuss both approaches in turn.

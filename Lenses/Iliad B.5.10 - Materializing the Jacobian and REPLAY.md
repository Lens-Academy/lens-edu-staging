---
id: '92745495-0f3a-498a-a12b-eb1430e67dac'
title: "B.5.10 Materializing the Jacobian and REPLAY"
tldr: "Makes unrolling practical in two ways: stationary segments with a materialized Jacobian (the SOURCE method), and implicit Jacobian-vector products with the REPLAY algorithm."
summary_for_tutor: "Subsections 4.2.1 and 4.2.2 of Iliad worksheet B.5 Data Attribution: stationary segments with checkpoints, segment Jacobian and segment response, the full SOURCE formula, a remark that unrolling gives a principled damping, then the metagradient decomposition, REPLAY reverse-mode through training with O(T log T) cost, and a comparison with explicit unrolling. No exercises."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\#### 4.2.1 Materializing the Jacobian

In this subsection we will derive the SOURCE method (Bae et al. 2024), which introduces a small number of approximations of Jacobians that reduce the full unrolling computation to something resembling an influence-function calculation at each of several checkpoints.

**Stationary segments.**  Divide the $$T$$ training steps into $$L$$ segments at checkpoints $$0 = T_{0} < T_{1} < \cdots < T_{L} = T$$, and let $$K_{\ell} = T_{\ell} - T_{\ell-1}$$ be the number of steps in segment $$\ell$$. Within each segment, make the *stationarity approximation*: the expected mini-batch Hessian and per-example gradient are approximately constant,

$$
\bar{H}_{\ell} \;\approx\; \frac{1}{K_{\ell}}\sum_{t=T_{\ell-1}}^{T_\ell - 1}\widehat{H}_{t}, \qquad \bar{g}_{i,\ell}\;\approx\; \frac{1}{K_{\ell}}\sum_{t=T_{\ell-1}}^{T_\ell - 1}\nabla_{w} L(w_{t},z_{i}).
$$

Similarly, write $$\bar\eta_{\ell}$$ for the average learning rate in segment $$\ell$$.

**Segment Jacobian.**  Under the stationarity approximation, the product of $$K_{\ell}$$ step Jacobians within segment $$\ell$$ simplifies to a matrix power:

$$
J_{T_{\ell-1}:T_\ell}\;\approx\; (I - \bar\eta_{\ell}\,\bar{H}_{\ell})^{K_\ell}\;\approx\; \exp\bigl(-\bar\eta_{\ell}\,K_{\ell}\,\bar{H}_{\ell}\bigr) \;=:\; \bar{S}_{\ell}.
$$

The matrix exponential is well approximated by the matrix power when $$\bar\eta_{\ell}\,\bar{H}_{\ell}$$ has small spectral norm. In an eigenbasis of $$\bar{H}_{\ell}$$ with eigenvalue $$\sigma$$, the segment Jacobian acts as the scalar filter $$F_{S}(\sigma) = e^{-\bar\eta_\ell K_\ell \sigma}$$: high-curvature directions ($$\sigma$$ large) are exponentially damped, while low-curvature directions ($$\sigma$$ small) are preserved.

**Segment response.**  Return to the unrolling formula (20) and restrict the sum to the steps inside segment $$\ell$$. The contribution of datum $$z_{i}$$ during this segment is

$$
R_{i,\ell}\;:=\; \sum_{t=T_{\ell-1}}^{T_\ell - 1}\frac{\eta_{t}}{b}\;\mathbf{1}[i\in B_{t}]\;J_{(t+1):T_\ell}\;\nabla_{w} L(w_{t},z_{i}),
$$

where the Jacobian $$J_{(t+1):T_\ell}$$ propagates each gradient contribution forward to the segment boundary $$T_{\ell}$$ (propagation from $$T_{\ell}$$ to the end of training is handled by the inter-segment Jacobians $$\bar{S}_{\ell'}$$ in the full formula below). Now apply the stationarity approximation: replace each $$\nabla_{w} L(w_{t},z_{i})$$ by $$\bar{g}_{i,\ell}$$, each learning rate by $$\bar\eta_{\ell}$$, replace the indicator $$\mathbf{1}[i\in B_{t}]$$ by its expectation $$b/n$$ (datum $$z_{i}$$ appears in a random batch with probability $$b/n$$), and use the segment Jacobian approximation $$J_{(t+1):T_\ell}\approx (I - \bar\eta_{\ell}\bar{H}_{\ell})^{T_\ell - 1 - t}$$. This gives

$$
R_{i,\ell}\;\approx\; \frac{\bar\eta_{\ell}}{n}\sum_{k=0}^{K_\ell - 1}(I - \bar\eta_{\ell}\,\bar{H}_{\ell})^{k}\;\bar{g}_{i,\ell}.
$$

The sum is a matrix geometric series. Using $$\sum_{k=0}^{K-1}M^{k} = (I - M^{K})(I-M)^{-1}$$ with $$M = I - \bar\eta_{\ell}\bar{H}_{\ell}$$ and passing to the matrix exponential:

$$
\bar{r}_{i,\ell}\;:=\; \frac{1}{n}\bigl(I - e^{-\bar\eta_\ell K_\ell \bar{H}_\ell}\bigr)\bar{H}_{\ell}^{-1}\,\bar{g}_{i,\ell}.
$$

To understand this, work in an eigenbasis of $$\bar{H}_{\ell}$$. On an eigenvalue $$\sigma$$, the matrix $$(I - e^{-\bar\eta_\ell K_\ell \bar{H}_\ell})\bar{H}_{\ell}^{-1}$$ acts as the scalar

$$
F_{r}(\sigma) \;=\; \frac{1 - e^{-\bar\eta_\ell K_\ell\,\sigma}}{\sigma}.
$$

Note the similarity to the classical influence function formula, which applies $$1/\sigma$$ (the inverse Hessian eigenvalue), and with the damped IF (6), which applies $$1/(\sigma + \lambda)$$. Thus $$F_{r}$$ can be seen as a principled damping constant:

- *Large $$\sigma$$* (directions the optimizer has fully converged along): $$e^{-\bar\eta_\ell K_\ell\,\sigma}\approx 0$$, so $$F_{r}(\sigma) \approx 1/\sigma$$. Agrees with the classical IF.
- *Small $$\sigma$$* (directions the optimizer has barely moved along): $$e^{-\bar\eta_\ell K_\ell\,\sigma}\approx 1 - \bar\eta_{\ell} K_{\ell}\,\sigma$$, so $$F_{r}(\sigma) \approx \bar\eta_{\ell} K_{\ell}$$. A finite constant, not $$1/\sigma \to \infty$$.
- *Crossover* at $$\sigma_{*} \approx 1/(\bar\eta_{\ell} K_{\ell})$$: directions with curvature below this threshold are automatically suppressed.

**Full formula.**  Chaining the segment Jacobians and responses across all $$L$$ segments:

$$
\tau_{\mathrm{SOURCE}}(\phi,z_{i}) \;=\; \nabla_{w}\phi(w_{T})^{\top}\,\sum_{\ell=1}^{L}\Bigl(\prod_{\ell'=\ell+1}^{L}\bar{S}_{\ell'}\Bigr)\,\bar{r}_{i,\ell},
$$

where the product is ordered with $$\ell' = L$$ on the left. With a single segment ($$L=1$$), the formula reduces to $$\nabla_{w}\phi^{\top}\,\bar{r}_{i,1}$$, which is the classical IF with $$H^{-1}$$ replaced by the filter $$F_{r}$$.

:::callout {title="Note" tone="blue"}

**Remark (Unrolling provides a principled damping).** The crossover $$\sigma_{*} = 1/(\bar\eta K)$$ in the filter $$F_{r}$$ plays exactly the role of the damping parameter $$\lambda$$ in the PBRF formula $$(H + \lambda I)^{-1}$$ from Section 2.2, but it is not a free parameter. It is the reciprocal of $$\bar\eta K$$, the total *training effort* (learning rate $$\times$$ number of steps) in the segment. Directions that the optimizer has not had time to converge along are automatically down-weighted, because the Jacobian products have not had enough steps to amplify them. The practical consequence: the damping $$\lambda$$ that influence-function methods require careful tuning of has a natural value determined by the training process, and unrolling recovers it without any tuning.

:::

\#### 4.2.2 Implicit JVPs and the REPLAY algorithm

The second approach to evaluating (20) avoids materializing Jacobians altogether. Instead, it uses *reverse-mode automatic differentiation* through the training loop, computing Jacobian-vector products (JVPs) implicitly. This is the strategy of the MAGIC method (Ilyas & Engstrom 2025), building on the metagradient framework of Engstrom et al. 2025.

**Setup.**  Model the entire training process as a composition of $$T$$ differentiable update functions:

$$
s_{t+1}= h_{t}\bigl(s_{t},\, g_{t}(s_{t},\beta)\bigr), \qquad s_{0} = s_{\mathrm{init}},
$$

where $$s_{t}$$ is the full optimizer state at step $$t$$ (parameters, momentum buffers, etc.), $$g_{t}(s_{t},\beta) = \sum_{i\in B_t}\beta_{i}\,\nabla L(s_{t},z_{i})$$ is the weighted mini-batch gradient, and $$h_{t}$$ is the optimizer's update rule (SGD, Adam, etc.). The attribution target is $$\phi(s_{T})$$, which depends on $$\beta$$ through the entire chain of updates.

**The metagradient decomposition.**  Applying the chain rule through this composition:

$$
\frac{\partial\,\phi(s_{T})}{\partial \beta}\;=\; \sum_{t=0}^{T-1}\underbrace{\frac{\partial\,\phi(s_{T})}{\partial s_{t+1}}}_{A_{t+1}}\;\cdot\;\underbrace{\frac{\partial\,h_{t}(s_{t},g_{t}(s_{t},\beta))}{\partial \beta}}_{B_t}.
$$

The vector $$A_{t+1}:= \partial\phi(s_{T})/\partial s_{t+1}$$ is the sensitivity of the final observable to the state at step $$t+1$$; it satisfies the backward recursion

$$
A_{t} \;=\; A_{t+1}\;\frac{\partial\,h_{t}(s_{t},g_{t})}{\partial s_{t}}, \qquad A_{T} = \nabla_{s_T}\phi(s_{T}).
$$

This is just backpropagation through the training loop. The vector $$B_{t}$$ is the direct effect of $$\beta$$ at step $$t$$: it captures how the gradient at step $$t$$ depends on the data weights. For vanilla SGD, $$B_{t}$$ reduces to $$-(\eta_{t}/b)\,[\nabla_{w} L(w_{t},z_{i})\cdot\mathbf{1}[i\in B_{t}]]_{i=1}^{n}$$.

**REPLAY: efficient reverse-mode through training.**  The backward recursion (33) requires the optimizer state $$s_{t}$$ at every step. Naively this means storing all $$T$$ states, which is prohibitive for long training runs. The REPLAY algorithm (Engstrom et al. 2025) solves this with a *hierarchical checkpointing* scheme:

1. Save $$k$$ evenly-spaced checkpoints along the training trajectory.
2. When the backward pass needs a state between two checkpoints, *replay* the training forward from the nearest saved checkpoint to regenerate it.
3. Apply this strategy recursively (a $$k$$-ary tree of depth $$\log_{k} T$$).

The result is exact (to floating-point precision) differentiation through all $$T$$ training steps, using $$O(k\log_{k} T)$$ stored states and $$O(T\log_{k} T)$$ total forward-pass work, a logarithmic overhead over the cost of training itself.

**Comparison with explicit unrolling.**  The implicit approach has two main advantages:

- *Exactness.* No stationarity or matrix-exponential approximations are needed; the Jacobian-vector products are computed exactly by autodiff.
- *Generality.* Any differentiable optimizer (Adam, LAMB, etc.) and any training pipeline (multi-stage, curriculum learning) are handled transparently, since $$h_{t}$$ is just a function.

The price is computational: REPLAY requires $$O(T\log T)$$ training-equivalent steps and careful engineering of the checkpointing schedule, whereas the explicit approach requires only a handful of checkpoints and an EK-FAC-style Hessian approximation at each. The choice depends on the scale: for moderate-size models where replaying training is feasible, MAGIC gives exact answers; for large-scale models where even one extra training pass is expensive, the SOURCE approximation with $$L = 3$$–$$6$$ segments may be the only practical option.

---
id: '2c5cbe51-c9fc-4841-87a7-9e03352af927'
title: "B.4.3 Gradient flow and conserved quantities"
tldr: "Derives gradient flow for a two-layer linear network, shows the balancedness matrix is conserved, and obtains the NTK form of the flow in function space."
summary_for_tutor: "This is Section 4 'Gradient flow and conserved quantities' of Iliad worksheet B.4 Training Dynamics. It contains Exercises 4.1-4.7: gradient flow equations for W_1 and W_2, conservation of G = W_2^T W_2 - W_1 W_1^T, the velocity of W = W_2 W_1, the identities W_1^T W_1 = (W^T W)^(1/2) and W_2 W_2^T = (W W^T)^(1/2) under balanced initialization, the balanced function-space ODE and the NTK operator K[F], with the depth-L generalization. Collapsed solutions and a hint on 4.2 are included. Keep the notation G, K[F], E = M - W. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Guillaume Corlouer (Stormglass)
source_url: https://iliad-intensive.org/learning/training-dynamics/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Gradient flow and conserved quantities

We now study gradient flow: $\dot{\theta}(t) = -\nabla_{\theta} \mathcal{L}(\theta(t))$, the continuous-time limit of gradient descent with infinitesimal learning rate.

:::callout {title="Exercise" tone="amber"}
**Exercise 4.1 (Gradient-flow equations).** For a two-layer DLN ($L=2$), the loss is given by $\mathcal{L}= \frac{1}{2}\|M - W_{2} W_{1}\|_{F}^{2}$. Assume that each weight matrix $W_{i}$ is diagonal. Derive the gradient flow equations for each layer. In particular, show that:

$$
\dot{W}_{1} = W_{2}^{\top}(M - W_{2} W_{1}), \qquad \dot{W}_{2} = (M - W_{2} W_{1}) W_{1}^{\top}
$$

*Note*: these equations also hold for general (non-diagonal) $W_{1}$ and $W_{2}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We have $\mathcal{L}= \frac{1}{2}\|M - W_{2} W_{1}\|_{F}^{2} = \frac{1}{2}\text{Tr}\left[(M - W_{2} W_{1})^{\top}(M - W_{2} W_{1})\right]$.

**General matrix derivation.** Expand:

$$
\mathcal{L}= \frac{1}{2}\text{Tr}(M^{\top} M) - \text{Tr}(M^{\top} W_{2} W_{1}) + \frac{1}{2}\text{Tr}(W_{1}^{\top} W_{2}^{\top} W_{2} W_{1})
$$

Differentiating with respect to $W_{1}$, using $\frac{\partial}{\partial A}\text{Tr}(B^{\top} A) = B$ and $\frac{\partial}{\partial A}\text{Tr}(A^{\top} C A) = (C + C^{\top})A$:

$$
\nabla_{W_1}\mathcal{L}= -W_{2}^{\top} M + W_{2}^{\top} W_{2} W_{1} = -W_{2}^{\top}(M - W_{2} W_{1})
$$

So $\dot{W}_{1} = -\nabla_{W_1}\mathcal{L}= W_{2}^{\top}(M - W_{2} W_{1})$.

Similarly, $\nabla_{W_2}\mathcal{L}= -(M - W_{2} W_{1})W_{1}^{\top}$, giving $\dot{W}_{2} = (M - W_{2} W_{1})W_{1}^{\top}$.

**Diagonal shortcut.** For diagonal matrices $W_{1} = \text{diag}(a_{\alpha})$, $W_{2} = \text{diag}(b_{\alpha})$, $M = \text{diag}(s_{\alpha})$: the loss decouples as $\mathcal{L}= \frac{1}{2}\sum_{\alpha}(s_{\alpha} - b_{\alpha} a_{\alpha})^{2}$. Then $\dot{a}_{\alpha} = -\partial\mathcal{L}/\partial a_{\alpha} = b_{\alpha}(s_{\alpha} - b_{\alpha} a_{\alpha})$ and $\dot{b}_{\alpha} = a_{\alpha}(s_{\alpha} - b_{\alpha} a_{\alpha})$, which is the diagonal version of the matrix equations above. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.2 (Balancedness is conserved).** Define the **balancedness matrix**:

$$
G := W_{2}^{\top} W_{2} - W_{1} W_{1}^{\top}
$$

Show that $G$ is conserved under the gradient flow, i.e. $\dot{G}= 0$. In other words, gradient flow is constrained to the balanced manifold

$$
\mathcal{M}_{\beta}:= \{\theta\in\Omega\mid W_{\ell+1}^{\top}W_{\ell+1}- W_{\ell}W_{\ell}^{\top}= \beta_{\ell},\; \ell=1,\ldots,L-1\}.
$$

*Hint*: Compute $\dot{G}$, substitute the gradient flow equations and verify that the terms cancel pairwise.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Let $E := M - W_{2} W_{1}$ denote the residual. Compute:

$$
\dot{G}= \dot{W}_{2}^{\top} W_{2} + W_{2}^{\top} \dot{W}_{2} - \dot{W}_{1} W_{1}^{\top} - W_{1} \dot{W}_{1}^{\top}
$$

Substitute the gradient flow equations. Using $\dot{W}_{2} = E W_{1}^{\top}$ and $\dot{W}_{1} = W_{2}^{\top} E$:

$$
\dot{W}_{2}^{\top} W_{2} = (E W_{1}^{\top})^{\top} W_{2} = W_{1} E^{\top} W_{2}
$$

$$
W_{2}^{\top} \dot{W}_{2} = W_{2}^{\top} E W_{1}^{\top}
$$

$$
\dot{W}_{1} W_{1}^{\top} = W_{2}^{\top} E W_{1}^{\top}
$$

$$
W_{1} \dot{W}_{1}^{\top} = W_{1}(W_{2}^{\top} E)^{\top} = W_{1} E^{\top} W_{2}
$$

Therefore:

$$
\dot{G}= W_{1} E^{\top} W_{2} + W_{2}^{\top} E W_{1}^{\top} - W_{2}^{\top} E W_{1}^{\top} - W_{1} E^{\top} W_{2} = 0
$$

The terms cancel pairwise. $G$ is conserved. $\square$

:::

From now on, assume **balanced initialization**: $G(0) = 0$, which by Exercise 4.2 means $W_{2}^{\top} W_{2} = W_{1} W_{1}^{\top}$ for all time. We want to derive the gradient flow in function space (the ODE for the student $W = W_{2} W_{1}$). This requires several steps.

:::callout {title="Exercise" tone="amber"}
**Exercise 4.3 (Function-space velocity).** Compute $\dot{W}:= \frac{d}{dt}(W_{2} W_{1})$ using the gradient flow equations from Exercise 4.1. Show that:

$$
\dot{W}= (M - W)\, W_{1}^{\top} W_{1} + W_{2} W_{2}^{\top}\, (M - W)
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Apply the product rule:

$$
\dot{W}= \dot{W}_{2} W_{1} + W_{2} \dot{W}_{1} = (M - W_{2} W_{1})W_{1}^{\top} \cdot W_{1} + W_{2} \cdot W_{2}^{\top}(M - W_{2} W_{1})
$$

Writing $W = W_{2} W_{1}$:

$$
\dot{W}= (M - W)\,W_{1}^{\top} W_{1} + W_{2} W_{2}^{\top}\,(M - W) \qquad \square
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.4 ($W_{1}^{\top}W_{1}$ in terms of $W$).** We now need to express $W_{1}^{\top} W_{1}$ and $W_{2} W_{2}^{\top}$ in terms of $W = W_{2} W_{1}$. Show that:

$$
W_{1}^{\top} W_{1} = (W^{\top} W)^{1/2}
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Balancedness gives $W_{2}^{\top} W_{2} = W_{1} W_{1}^{\top}$, so

$$
W^{\top} W = W_{1}^{\top} \left(W_{2}^{\top} W_{2}\right) W_{1} = W_{1}^{\top} \left(W_{1} W_{1}^{\top}\right) W_{1} = \left(W_{1}^{\top} W_{1}\right)^{2}
$$

Both $W^{\top} W$ and $W_{1}^{\top} W_{1}$ are positive semidefinite. A positive semidefinite matrix has a unique positive semidefinite square root, so it follows that

$$
(W^{\top} W)^{1/2}= W_{1}^{\top} W_{1} \qquad \square
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.5 ($W_{2}W_{2}^{\top}$ in terms of $W$).** Similarly, show that $W_{2} W_{2}^{\top} = (W W^{\top})^{1/2}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Analogous to Exercise 4.4.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.6 (The balanced function-space ODE).** Substitute the results of Exercises 4.4 and 4.5 into Exercise 4.3 to obtain:

$$
\dot{W}= (W W^{\top})^{1/2}(M - W) + (M - W)(W^{\top} W)^{1/2}
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Substituting into Exercise 4.3:

$$
\dot{W}= (M - W)(W^{\top} W)^{1/2}+ (WW^{\top})^{1/2}(M - W) \qquad \square
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.7 (The NTK operator).** Define the NTK operator for $L = 2$ as:

$$
K[F] := (WW^{\top})^{1/2}\, F + F\, (W^{\top} W)^{1/2}
$$

Show that the gradient flow from Exercise 4.6 can be written as $\dot{W}= K[M - W]$.

It turns out that this result generalizes to depth $L$ on the balanced manifold:

$$
\dot{W}= \sum_{k=1}^{L}(WW^{\top})^{\frac{L-k}{L}}(M - W) (W^{\top} W)^{\frac{k-1}{L}}
$$

This is the NTK equation in the case of DLNs. The NTK equation is a gradient flow in function space with NTK being a preconditioning operator for the gradient.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

With $F = M - W$, the equation from Exercise 4.6 reads:

$$
\dot{W}= (WW^{\top})^{1/2}\,F + F\,(W^{\top} W)^{1/2}= K[F] = K[M - W] \qquad \square
$$

The general depth-$L$ result $\dot{W}= \sum_{k=1}^{L}(WW^{\top})^{(L-k)/L}(M-W)(W^{\top} W)^{(k-1)/L}$ follows from the same approach applied to the $L$-fold balanced conditions $W_{l+1}^{\top} W_{l+1}= W_{l} W_{l}^{\top}$ for all $l$.

:::

---
id: 'f7126dcf-e659-4b89-afdc-f423334620c1'
title: "B.4.6 Stochastic implicit bias (bonus)"
tldr: "A bonus section on SGD noise: the Boltzmann equilibrium of the Langevin model, the role of temperature and flat minima, and implicit bias from anisotropic noise."
summary_for_tutor: "This is Section 8 'Stochastic implicit bias (bonus)' of Iliad worksheet B.4 Training Dynamics. It models SGD as a Langevin SDE and contains Exercises 8.1-8.3: the Boltzmann equilibrium from the Fokker-Planck equation with beta = 2/(eta sigma^2), temperature and flatness, and anisotropic noise with the Ito drift term. Collapsed solutions are included. Keep the notation Sigma(theta), eta, sigma, beta. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Guillaume Corlouer (Stormglass)
source_url: https://iliad-intensive.org/learning/training-dynamics/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 8. Stochastic implicit bias (bonus)

SGD introduces noise from mini-batching. A continuous model is the Langevin SDE:

$$
d\theta_{t} = -\nabla \mathcal{L}(\theta_{t})\,dt + \sqrt{\eta\,\Sigma(\theta_{t})}\,dB_{t}
$$

where $\Sigma(\theta)$ is the covariance of the stochastic gradient noise and $\eta$ is the learning rate.

:::callout {title="Exercise" tone="amber"}
**Exercise 8.1 (Boltzmann equilibrium).** The probability density $p(\theta, t)$ of the parameters evolves according to the Fokker–Planck equation:

$$
\partial_{t} p = -\nabla \cdot \mathbf{j}, \qquad \mathbf{j}= -\nabla \mathcal{L}(\theta)\,p(\theta) - \frac{\eta}{2}\nabla \cdot \left(\Sigma(\theta)\,p(\theta)\right)
$$

where $\mathbf{j}$ is the probability current. Assume: (i) stationarity $\partial_{t} p^{*} = 0$, (ii) thermal equilibrium $\mathbf{j}= 0$, and (iii) isotropic noise $\Sigma = \sigma^{2} I$. Show that the equilibrium distribution is the Boltzmann distribution:

$$
p^{*}(\theta) \propto \exp\left(-\frac{2}{\eta \sigma^{2}}\mathcal{L}(\theta)\right)
$$

*Hint*: Setting $\mathbf{j}= 0$ with $\Sigma = \sigma^{2} I$ gives $\nabla \mathcal{L}\, p + \frac{\eta\sigma^{2}}{2}\nabla p = 0$. This is a first-order ODE for $p$ in terms of $\mathcal{L}$. Try the ansatz $p \propto e^{-\beta \mathcal{L}}$ and solve for $\beta$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Setting $\mathbf{j}= 0$ (thermal equilibrium) with isotropic noise $\Sigma = \sigma^{2} I$:

$$
0 = -\nabla\mathcal{L}(\theta)\,p^{*}(\theta) - \frac{\eta\sigma^{2}}{2}\nabla p^{*}(\theta)
$$

Rearranging:

$$
\frac{\nabla p^{*}}{p^{*}}= -\frac{2}{\eta\sigma^{2}}\nabla\mathcal{L}
$$

The left-hand side is $\nabla\ln p^{*}$, so:

$$
\nabla\ln p^{*}(\theta) = -\frac{2}{\eta\sigma^{2}}\nabla\mathcal{L}(\theta)
$$

Integrating both sides:

$$
\ln p^{*}(\theta) = -\frac{2}{\eta\sigma^{2}}\mathcal{L}(\theta) + \text{const}
$$

$$
\boxed{p^*(\theta) \propto \exp\!\left(-\frac{2}{\eta\sigma^{2}}\mathcal{L}(\theta)\right)}
$$

This is the Boltzmann distribution with inverse temperature $\beta = 2/(\eta\sigma^{2})$. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 8.2 (Temperature and flatness).** The ratio $\frac{2}{\eta \sigma^{2}}$ plays the role of an inverse temperature $\beta$. Interpret what happens to the equilibrium distribution when:

- $\eta$ is very small (low temperature)
- $\eta$ is very large (high temperature)

Which regime favors flatter minima, and why might this be beneficial for generalization?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The effective temperature is $T = \eta\sigma^{2}/2$.

**Small $\eta$ (low temperature, $\beta \to \infty$):** The distribution concentrates sharply on the global minima of $\mathcal{L}$. SGD converges to the lowest-loss minimizer without exploring.

**Large $\eta$ (high temperature, $\beta \to 0$):** The distribution becomes nearly uniform over parameter space. SGD explores broadly and does not settle into any particular minimum.

**Flat vs. sharp minima:** At moderate temperature, the Boltzmann distribution assigns more probability mass to **broad basins** (flat minima) than to narrow ones. This is because a flat minimum occupies a larger volume of parameter space at any given loss level — the width of the basin acts as an entropic contribution. Flat minima tend to generalize better because small perturbations to the parameters (or slight distribution shift in the data) do not dramatically change the loss. Thus the implicit bias of SGD noise toward flat minima is beneficial for generalization. $\square$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 8.3 (Anisotropic noise).** In practice, SGD noise is **not** isotropic: $\Sigma(\theta)$ depends on both the loss landscape and the data. Without solving anything, explain qualitatively why anisotropic noise can introduce an implicit bias that goes beyond what the loss function $\mathcal{L}$ alone would select. Specifically, why might SGD preferentially escape sharp directions of the loss while remaining stable along flat directions?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

When $\Sigma(\theta)$ is anisotropic, the noise strength varies by direction. The Fokker-Planck current becomes:

$$
\mathbf{j}= -\nabla\mathcal{L}\,p - \frac{\eta}{2}\nabla\cdot(\Sigma(\theta)\,p)
$$

The second term introduces an **Itô drift** $\frac{\eta}{2}\nabla\cdot\Sigma(\theta)$ that depends on the spatial variation of the noise covariance. In directions where $\Sigma$ has large eigenvalues (high noise), the effective diffusion is strong and the system escapes easily from sharp regions of the loss landscape. In directions where $\Sigma$ has small eigenvalues (low noise), the system is more stable and tends to remain there.

This creates a **direction-dependent regularizer**: SGD preferentially pushes parameters out of sharp directions (high gradient variance → large noise eigenvalue → fast escape) while preserving parameters along flat directions (low gradient variance → small noise eigenvalue → stability). This goes beyond what the Boltzmann distribution on $\mathcal{L}$ alone would predict. In general, detailed balance $\mathbf{j}= 0$ may not hold for anisotropic, state-dependent noise, leading to persistent probability currents and non-equilibrium steady states that further modify the implicit bias. $\square$

:::

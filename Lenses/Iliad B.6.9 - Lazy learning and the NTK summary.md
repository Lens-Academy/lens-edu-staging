---
id: 'ccfe4eaf-b967-4a8f-9007-9b75fb661825'
title: "B.6.9 Lazy learning and the NTK summary"
tldr: "Lazy learning with a constant NTK, mode-by-mode learning, test-point predictions, a summary of when this breaks, and a numerical lab."
summary_for_tutor: "Sections 4.4-4.5 of Iliad worksheet B.6 Physics of Deep Learning. Covers residuals in the NTK eigenbasis learned at times t_mu about 1/(eta s_mu^2), the end-of-training prediction as an affine map of the initial GP, and the conditions under which the picture breaks (large L/N, large n/N, large learning rate). Contains Exercise 4.3 (lazy predictions on test points) and Exercise 4.4 (numerics: the lazy network, lab), both with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 4.4 Lazy learning

When the NTK is constant during training — confusingly often called the *NTK regime* — a network undergoes what is known as "lazy learning." It is not learning features, since the eigenvalues $$s_{\mu}^{2}$$ and eigenvectors $$u_{\mu}$$ of the NTK are (by construction) constant. Nevertheless, the network function converges to its training data exponentially fast: from (4.12) with constant $$\Theta$$, we have

$$
\Delta^{\mu}(t) = (e^{-\eta\, t\, \Theta})^{\mu}{}_{\nu} \Delta^{\nu}(0)\,,
$$

where we recall that $$\Delta^{\mu}(t) = f^{\mu}-y^{\mu} = f_{\theta(t)}(x^{\mu})-y^{\mu}$$. Writing the residuals in an eigenbasis for the NTK, $$\Delta=\hat \Delta^{\mu}u_{\mu}$$ we see that

$$
\hat \Delta^{\mu}(t) = e^{-\eta\,t\,s_\mu^2}\hat \Delta^{\mu}(0)\,.
$$

Each feature is learned at a characteristic timescale $$t_{\mu} \approx 1/(\eta\, s_{\mu}^{2})$$ .

:::callout {title="Exercise" tone="amber"}
**Exercise 4.3 (Lazy predictions on test points).** Derive that on an arbitrary test point $$x$$, not necessarily part of the training data,

$$
f_{\theta(t)}(x) = f_{\theta_0}(x) - \Theta(x,x^{\mu}) \Theta^{-1}_{\mu\nu}(1\!\!1-e^{-\eta\,t\,\Theta})^{\nu}{}_{\rho}\Delta^{\rho}(0)
$$

where $$\Theta(x,x^{\mu}) = \nabla_{\theta} f(x)\cdot \nabla_{\theta} f(x^{\mu})$$ is the NTK for a test-train pair (which remains constant during training, just like the train-train NTK $$\Theta^{\mu\nu}$$).
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

In the linearized regime, $$f_{\theta(t)}(x) = f_{\theta_0}(x) + \nabla_{\theta} f(x)\cdot(\theta(t)-\theta_{0})$$ with all gradients at $$\theta_{0}$$. The parameter motion integrates the flow: $$\dot\theta = -\eta \sum_{\mu} \nabla_{\theta} f^{\mu}\, \Delta^{\mu}(t)$$ with $$\Delta(t) = e^{-\eta t \Theta}\Delta(0)$$ from (4.34), so

$$
\begin{aligned}\theta(t)-\theta_{0}&= -\eta \sum_{\mu} \nabla_{\theta} f^{\mu} \int_{0}^{t} ds\, \big(e^{-\eta s \Theta}\big)^{\mu}{}_{\rho}\, \Delta^{\rho}(0) \\&= -\sum_{\mu} \nabla_{\theta} f^{\mu}\, \big[\Theta^{-1}\big(1\!\!1 - e^{-\eta t\Theta}\big)\big]^{\mu}{}_{\rho} \Delta^{\rho}(0)\,.\end{aligned}
$$

Contracting with $$\nabla_{\theta} f(x)$$ and recognizing $$\Theta(x,x^{\mu}) = \nabla_{\theta} f(x)\cdot\nabla_{\theta} f(x^{\mu})$$ yields (4.36). (The test–train kernel is constant during training for the same reason the train–train one is: it is built from the frozen gradients at $$\theta_{0}$$.)

:::

From Exercise 4.3, we see that at the end of training $$t\to\infty$$ the network obeys

$$
f_{\theta_\infty}(x) = f_{\theta_0}(x)- \Theta(x,x^{\mu}) \Theta^{-1}_{\mu\nu}(f_{\theta_0}(x^{\nu})-y^{\nu})\,.
$$

This is an affine-linear transformation of the Gaussian process $$f_{\theta_0}(x)$$ at initialization, so it is again a Gaussian process. It's straightforward to check that the new mean and covariance are

$$
\begin{aligned}{\mathbb{E}}\big[ f_{\theta_\infty}(x)\big]&= \Theta^{x\mu}\Theta^{-1}_{\mu\nu}y^{\nu} \\ \text{Cov}\big[f_{\theta_\infty}(x),f_{\theta_\infty}(x')\big]&= K^{xx'}- 2\Theta^{x\mu}\Theta^{-1}_{\mu\nu}K^{\nu x'}+\Theta^{x\mu}\Theta^{-1}_{\mu\nu}K^{\nu \rho}\Theta^{-1}_{\rho\sigma}\Theta^{\sigma x'}\,, \notag\end{aligned}
$$

where $$K^{xx'}=K(x,x')$$, $$\Theta^{x\mu}=\Theta(x,x^{\mu})$$, etc.

\### 4.5 Summary

So far we've seen that in the fan-in normalization (Section 3.2), with order-one weights and an order-one learning rate $$\eta$$, at large width $$N$$ we've got

$$
\begin{aligned}\|\Theta\|\sim |\nabla_{\theta} f|^{2} \sim 1\,,\qquad \|\nabla_{\theta}^{2} f\|&\sim \frac{1}{\sqrt{N}}\,,\qquad |f_{\theta}-f_{\theta_0}|\sim 1\,, \\ |\theta-\theta_{0}|&\sim 1 \;\;\text{(i.e. }N^{-1/2}\text{ per weight)}\,,\end{aligned}
$$

which forces $$\Theta$$ to be constant and the network to linearize as a function of its parameters.

All this breaks down if

- Depth $$L$$ is large as well, with $$L/N$$ nonzero. (See (Roberts et al. 2022, Ch. 11).)
- Data samples $$n$$ become large, with $$n/N$$ nonzero.
- Learning rate becomes large.

Both $$L$$ and $$n$$ large are interesting cases for modern neural networks!

:::callout {title="Exercise" tone="amber"}
**Exercise 4.4 (★) (Numerics: the lazy network (lab)).** This lab, and its continuation in Exercise 5.3, trains one small network in both the fan-in and the mean-field normalization and tests the claims of Sections 4 and 5 numerically. The setup runs in seconds, in about sixty lines of NumPy; reproduce it, then modify it.

*The starter model.* Inputs are one-dimensional: $$n=30$$ equispaced training points $$x^{\mu}\in[-2,2]$$, with targets from a two-neuron teacher, $$y(x) = 2\tanh(3x) - \frac{3}{2}\tanh(x)$$. The student is a one-hidden-layer $$\tanh$$ network

$$
f(x) = \frac{1}{N^{\gamma}}\sum_{i=1}^{N} c_{i}\tanh(a_{i}x)\,,\qquad c_{i},a_{i}\sim{{\mathcal N}}(0,1)\,,\qquad N=300\,,
$$

trained by full-batch gradient descent on $${{\mathcal L}} = \frac{1}{2}\sum_{\mu}(f(x^{\mu})-y^{\mu})^{2}$$, with residuals $$\Delta^{\mu} = f(x^{\mu})-y^{\mu}$$. Here take the fan-in exponent $$\gamma = \frac{1}{2}$$, learning rate $$\eta = 0.02$$, and $$4\times10^{4}$$ steps. The empirical NTK to monitor is the $$n\times n$$ matrix

$$
\begin{aligned}\Theta^{\mu\nu}= \frac{1}{N^{2\gamma}}\sum_{i=1}^{N}\Big[&\tanh(a_{i}x^{\mu})\tanh(a_{i}x^{\nu}) \\&+ c_{i}^{2}\big(1-\tanh^{2}(a_{i}x^{\mu})\big)\big(1-\tanh^{2}(a_{i}x^{\nu})\big)\,x^{\mu} x^{\nu}\Big]\,.\end{aligned}
$$

**(a)** *It fits.* Train and check that the loss becomes small. (The network is overparametrized; fitting is not the interesting part.)

**(b)** *Initialization.* Over about $$200$$ seeds, histogram $$f_{0}(x)$$ at a fixed input, say $$x=1$$. You should see an order-one Gaussian, the Gaussian process of Section 3.4, and the sample covariance across two inputs should match the $$\tanh$$ GP kernel.

**(c)** *The kernel freezes.* For $$N\in\{30,100,300,1000\}$$ (a few seeds each), record $$\|\Theta_{\rm end}-\Theta_{0}\|/\|\Theta_{0}\|$$ and plot it against $$N$$ on log–log axes. Expected: it decays, with slope between $$-\frac{1}{2}$$ (the guaranteed bound (4.31)) and $$-1$$ (the typical measurement). Also record the relative parameter displacement $$|\theta_{\rm end}-\theta_{0}|/|\theta_{0}|$$ and compare with (4.30).

**(d)** *Mode by mode.* Diagonalize $$\Theta_{0}$$ and plot $$|(U^{T}\Delta)_{k}(t)|$$ on a semilog axis for a few $$k$$: straight lines with slopes $$-\eta s_{k}^{2}$$, the features being learned at $$t_{k} = 1/(\eta s_{k}^{2})$$, largest eigenvalue first, as in (4.35). Compare with the Bayesian version, Exercise 4.5(b).

**(e)** *Prediction.* Compare the trained function on fresh test points with the frozen-kernel prediction (4.36).
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Reference results for the setup as specified (single seeds; small-$$N$$ numbers fluctuate).

**(a)** Final loss $$\sim10^{-5}$$–$$10^{-4}$$. Keep $$\eta<2/s_{\max}^{2}(\Theta_{0})$$ for stability; here $$s^{2}_{\max}\approx30$$, so $$\eta=0.02$$ is safe.

**(b)** At $$x=1$$, $$f_{0}\sim{{\mathcal N}}(0,O(1))$$, and the sample covariance across two inputs matches the $$\tanh$$ GP kernel.

**(c)** Measured $$\|\Delta\Theta\|/\|\Theta_{0}\|\approx0.25,\,0.14,\,0.06$$ at $$N=100,300,1000$$: decaying, with a log–log slope between $$-1/2$$ and $$-1$$; average a few seeds to clean up the trend. The relative parameter displacement decays like $$N^{-1/2}$$, since the total displacement is $$O(1)$$ by (4.30) while $$|\theta_{0}|\sim\sqrt{P}\sim\sqrt{N}$$. Compute $$\Theta$$ from per-example gradients (an $$n\times P$$ Jacobian contracted with itself), in float64.

**(d)** The residual modes are straight lines on a semilog plot, with slopes $$-\eta s_{k}^{2}$$, until they hit the small nonlinear floor; the smallest-eigenvalue modes are visibly not yet learned at the end of training. This is spectral bias on display, and the dynamical twin of Exercise 4.5(b).

**(e)** At $$N=300$$ the trained function on test points agrees with (4.36) to within a few percent; the agreement degrades as $$N$$ shrinks, which is feature learning beginning to stir. The continuation is Exercise 5.3.

:::

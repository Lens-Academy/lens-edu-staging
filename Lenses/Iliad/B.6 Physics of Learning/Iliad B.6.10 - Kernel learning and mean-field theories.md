---
id: '622b93cf-7c68-40b4-a62c-b776deaefce4'
title: "B.6.10 Kernel learning and mean-field theories"
tldr: "Bayesian learning at large width as kernel ridge regression, then the idea of mean-field scaling and mean-field theory in physics via the Curie-Weiss magnet."
summary_for_tutor: "Sections 4.6, 5 and 5.1 of Iliad worksheet B.6 Physics of Deep Learning. Covers the Gaussian posterior over functions with ridge beta^-1, modes with lambda_k above (n beta)^-1 being learned, the introduction to the mean-field limit, the Curie-Weiss magnet, the three-step logic of mean-field exactness, and the general particle model with empirical measure rho_N. Contains Exercise 4.5 (Bayesian lazy learning, kernel ridge regression) and Exercise 5.1 (Curie-Weiss by fixed-point iteration), both with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 4.6 Bayesian learning at large width: kernel learning

So far, we have considered MLP's at large width, trained via gradient flow (as an approximation to SGD/GD). We found that their NTK remains constant and that their late-time distribution is a Gaussian process given by (4.38).

Suppose that we consider the same large-width network, but "train" Bayesian inference instead, on the empirical MSE loss $${{\mathcal L}}(\theta) = n L_{n}(\theta) = \frac{1}{2}\sum_{\mu=1}^{n} |f(x^{\mu})-y^{\mu}|^{2}$$. (Recall from Section 2.1 that, practically speaking, this means training via Langevin dynamics.) Then we expect a Bayesian posterior

$$
P(\theta) = \frac{1}{Z}e^{-\beta {{\mathcal L}}(\theta)}\, \pi(\theta)\,,\qquad \pi(\theta) \propto e^{\textstyle-\frac{1}{2\sigma_{w}}|\theta|^2}\,,
$$

where the prior $$\pi(\theta)$$ is the Gaussian of order-one variance from (3.1), and the network carries the fan-in normalization of Section 3.2.

We'd like to push the distribution forward to the network function $$f_{\theta}(x)$$. At large-width, the push-forward of the prior is our familiar Gaussian process from Section 3.4; expressed via a functional integral as in Section 3.5 it becomes

$$
\pi[f] = \frac{1}{Z'}e^{\textstyle -\frac{1}{2}\int dx\,dx'\, f(x) K^{-1}(x,x')f(x')}
$$

with $$K(x,x')=\bar K^{(L+1)}(x,x')$$ the final-layer GP kernel. Since the loss is explicitly a function of network values, we immediately get the late-time trained distribution

$$
P[f] = \frac{1}{Z''}\,e^{\textstyle -\frac{1}{2}\Big[\beta \sum_{\mu=1}^n(f(x^\mu)-y^\mu)^2 + \int dx\,dx'\, f(x) K^{-1}(x,x')f(x') \Big] }
$$

Note that the action here is quadratic in function values, so this is still a Gaussian process!

:::callout {title="Exercise" tone="amber"}
**Exercise 4.5 (★) (Bayesian lazy learning: kernel ridge regression from the Gaussian posterior).** Lazy gradient flow at large width solved itself in Section 4.3: the NTK froze, and the $$k$$-th kernel eigenmode of the residual decayed as $$e^{-\eta s_k^2t}$$, so that it is learned at the characteristic time $$t_{k} = 1/(\eta s_{k}^{2})$$. Here you derive the Bayesian-learning version of the same statement, with $$\beta$$ in the role of training time. Restricted to the training values $$\mathbf{f} = (f(x^{1}),\ldots,f(x^{n}))$$, the prior is Gaussian with covariance the kernel matrix $$\hat K^{\mu\nu}:= K(x^{\mu},x^{\nu})$$, so the posterior on training values is

$$
p(\mathbf{f})\;\propto\;\exp\Big[-\tfrac{1}{2}\,\mathbf{f}^{T}\hat K^{-1}\mathbf{f} - \tfrac{\beta}{2}\,|\mathbf{f}-\mathbf{y}|^{2}\Big]\,.
$$

**(a)** *Posterior mean.* The exponent is quadratic, so the posterior is Gaussian and everything follows from completing the square. Show that the posterior mean of the training values is $$\boldsymbol\mu = \hat K(\hat K+\beta^{-1}I_{n})^{-1}\mathbf{y}$$.

**(b)** *Eigenmodes.* Diagonalize the kernel, $$\hat Ku_{k} = \lambda_{k}u_{k}$$, and show that mode by mode

$$
u_{k}\cdot\boldsymbol\mu = \frac{\lambda_{k}}{\lambda_{k}+\beta^{-1}}\;u_{k}\cdot\mathbf{y} = \frac{\beta\lambda_{k}}{1+\beta\lambda_{k}}\;u_{k}\cdot\mathbf{y}\,.
$$

Conclude that the eigenmodes of the GP kernel at initialization are learned one by one as $$\beta$$ grows, mode $$k$$ switching on at the characteristic scale $$\beta_{k} = 1/\lambda_{k}$$, large-eigenvalue modes first (*spectral bias*).

**(c)** *Compare with gradient flow.* Place this alongside (4.35), $$\hat\Delta^{k}(t) = e^{-\eta s_k^2t}\hat\Delta^{k}(0)$$, that is $$t_{k} = 1/(\eta s_{k}^{2})$$. What is the same, and what differs? Two things to notice: the correspondence $$\beta\leftrightarrow\eta t$$ between the amount of data (or inverse noise) and training time; and the different shapes of the two filters, the power law $$1/(1+\beta\lambda_{k})$$ in $$\beta$$ versus the exponential $$e^{-\eta s_k^2t}$$ in $$t$$ (compare Exercise B.5). Also: the Bayesian calculation uses the GP kernel $$K$$, the dynamical one the NTK $$\Theta$$, two different frozen kernels for the same network.

**(d)** *Prediction.* Show that the full posterior over functions is again a Gaussian process,

$$
P[f] \propto e^{\textstyle -\frac{1}{2} \int dx\,dx'\, [f(x)-\mu(x)] \Sigma(x,x')^{-1} [f(x')-\mu(x')] }\,,
$$

with mean and covariance

$$
\begin{aligned}\mu(x)&= \sum_{\mu,\nu}K(x,x^{\mu})\big(\hat K+\beta^{-1}I_{n}\big)^{-1}_{\mu\nu}y^{\nu}\,, \\ \Sigma(x,x')&= K(x,x')-\sum_{\mu,\nu}K(x,x^{\mu})\big(\hat K+\beta^{-1}I_{n}\big)^{-1}_{\mu\nu}K(x^{\nu},x')\,.\end{aligned}
$$

The posterior mean is *kernel ridge regression* with ridge $$\beta^{-1}$$ (Appendix B.4), and $$\beta\to\infty$$ interpolates the data exactly. [*Hint:* the exponent is quadratic in $$f$$; complete the square, and use the Woodbury identity to relate the two natural forms of the answer.]
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Completing the square, the exponent is $$-\frac{1}{2}\mathbf{f}^{T}A^{-1}\mathbf{f} + \beta\,\mathbf{y}^{T}\mathbf{f} + \mathrm{const}$$ with $$A^{-1}= \hat K^{-1}+\beta I_{n}$$, so the posterior is Gaussian with covariance $$A$$ and mean $$\boldsymbol\mu = \beta A\mathbf{y} = \beta(\hat K^{-1}+\beta I_{n})^{-1}\mathbf{y} = \hat K(\hat K+\beta^{-1}I_{n})^{-1}\mathbf{y}$$ (multiply through by $$\hat K$$).

**(b)** In the eigenbasis all matrices are diagonal, giving (4.46). The filter $$\beta\lambda_{k}/(1+\beta\lambda_{k})$$ is $$\approx0$$ for $$\beta\ll1/\lambda_{k}$$ and $$\approx1$$ for $$\beta\gg1/\lambda_{k}$$: a switch at $$\beta_{k} = 1/\lambda_{k}$$. On a $$\log\beta$$ axis it is a sigmoid of universal shape, pleasant to compare with the logistic occupations of Section 2.5, though nothing here is a phase transition: the switches are $$n$$ smooth crossovers, one per mode.

**(c)** The same: frozen-kernel linear structure, mode-by-mode learning, spectral bias with scale $$1/\lambda_{k}$$, and the dictionary "$$\beta\approx$$ training time" of Section 2.1 made quantitative as $$\beta\leftrightarrow\eta t$$. Different: the suppression of the unlearned part is $$1/(1+\beta\lambda_{k})$$, a power law in $$\beta$$, versus $$e^{-\eta s_k^2t}$$, exponential in $$t$$ (the two filters of Figure 13); and the kernels differ. Bayesian learning of the frozen network is governed by the GP kernel $$K$$, a property of the *function* distribution at initialization, while gradient flow is governed by the NTK $$\Theta$$, a property of the *parametrization*. Both are fixed, data-independent kernels: in neither picture does the lazy network adapt its features.

**(d)** Varying the exponent of $$P[f]$$ with respect to $$f(x)$$ gives the stationarity equation $$\int dx'\,K^{-1}(x,x')\mu(x') + \beta\sum_{\mu}(\mu(x^{\mu})-y^{\mu})\,\delta(x-x^{\mu}) = 0$$, that is $$\mu(x) = -\beta\sum_{\mu} K(x,x^{\mu})(\mu(x^{\mu})-y^{\mu})$$. Evaluating at the training points gives a closed linear system whose solution is (a), and substituting back yields the stated $$\mu(x)$$. The covariance is the inverse of the quadratic form, $$\Sigma = (K^{-1}+\beta\,\delta_{\rm data})^{-1}$$, which the Woodbury identity converts into the stated form. As $$\beta\to\infty$$ this pins $$\mu(x^{\mu}) = y^{\mu}$$: noiseless GP interpolation; finite $$\beta$$ is ridge regularization with ridge $$\beta^{-1}$$.

:::

These equations embody what's sometimes known as *kernel regression*, with *ridge parameter* $$\beta^{-1}=T$$. (Appendix B.4 derives the same formula for a finite linear model, with no Bayesian input.) If the training samples are sufficiently dense, the mean can be an approximated by an integral in terms of the untrained kernel

$$
\mu(x) \approx \int dx'\,dx''\, K(x,x')\big(K+(n\beta)^{-1}\text{id}\big)^{-1}(x',x'')\,y(x'')\,.
$$

Writing the data "truths" $$y(x) = \sum y_{k} \varphi_{k}(x)$$ in an eigenbasis for $$K$$, with ordered eigenvalues $$\lambda_{1}\geq\lambda_{2}\geq...$$, we find

$$
\mu(x) = \sum_{k=1}^{\infty} \frac{\lambda_{k}}{\lambda_{k}+(n\beta)^{-1}}y_{k}\varphi_{k}(x) \approx \sum_{k\;\text{s.t.}\, \lambda_k\gtrsim(n\beta)^{-1}}y_{k}\varphi_{k}(x)\,.
$$

This is the Bayesian version of lazy learning. For given $$n,\beta$$, the "modes" of the data distribution with $$\lambda_{k} \gtrsim (n\beta)^{-1}$$ are learned by the network, and the rest are projected out.

Recall that in the Bayesian context, the rescaled inverse-temperature $$n\beta$$ should play a role somewhat analogous to *training time* in SGD/GD. We can see this explicitly here. For example, in SGD/GD lazy learning, the characteristic time to learn an *NTK mode* $$s_{\mu}^{2}$$ is $$t\approx 1/(\eta\,s_{\mu}^{2})$$ (see (4.35)). Correspondingly, in Bayesian lazy learning, the minimum inverse-temperature required to learn a *GP mode* is $$\beta n\approx 1/\lambda_{k}$$.

\## 5. Mean-field scaling

Sections 3 and 4 analyzed one and the same large-width limit: the fan-in normalization (Section 3.2) with order-one weights and an order-one learning rate, and width $$N\to\infty$$ at fixed depth and data. At initialization the network converges to a Gaussian process; during training the NTK freezes, the network linearizes, and (by the definition of Section 4.2) no features are learned. It is tempting to conclude that infinite width *implies* laziness. The lesson of this section is that it does not, and that laziness was a consequence of a choice of *parametrization*, rather than of width. Changing the normalization of the output layer by a single extra factor of $$\sqrt{N}$$ produces a different, equally well-defined infinite-width limit in which the network starts at zero, individual weights move an order-one distance, the NTK evolves in time, and features are genuinely learned.

This alternative limit is called the *mean-field limit*. The name comes by analogy to a classic setup in statistical physics: an interacting particle system with weak all-to-all couplings, whose $$N\to\infty$$ behavior is governed by a self-consistent "mean field." We'll first explain what physicists mean by a mean-field theory (Section 5.1), then run the analogy in detail for one-hidden-layer networks (Section 5.2), see how the NTK story of Section 4 changes (Section 5.3). Finally we'll discuss some practical applications, including interpolating scalings, $$\mu$$P, and what this framework is actually used for (Sections 5.4–5.5).

The mean-field limit of one-hidden-layer networks was constructed independently, and essentially simultaneously, by four groups (Mei et al. 2018; Chizat & Bach 2018; Rotskoff & Vanden-Eijnden 2022; Sirignano & Spiliopoulos 2020); our treatment draws on all of them. Pedagogical accounts may be found in (Spiliopoulos et al. 2025, Ch. 20) and (Hanin 2026, Lecture 4).

\### 5.1 Mean-field theories in physics

"Mean-field theory" is one of the oldest and simplest approximation schemes in statistical mechanics: *replace the fluctuating environment felt by each degree of freedom with its average (a macroscopic order parameter), then demand self-consistency upon recalculating this average*. For most systems this is an uncontrolled approximation, though often a remarkably successful one *cf.* (Tong 2012, Chapter 1). There is, however, a family of models — those with weak, all-to-all couplings — for which it becomes exact as $$N\to\infty$$; and networks in mean-field scaling will turn out to be precisely such a model.

\#### 5.1.1 Warm-up: the Curie–Weiss magnet

The Curie–Weiss magnet is the Ising model of Section 2.4 on the *fully connected* graph: every spin couples to every other, with the coupling scaled down to $$J/N$$ so that the total force on any one spin, and the total energy, stay of order $$N^{0}$$ and $$N^{1}$$ respectively. Setting $$J=1$$, the energy (2.19) becomes

$$
E_{N}(s) = -\frac{1}{2N}\sum_{i,j=1}^{N} s_{i} s_{j} - B \sum_{i=1}^{N} s_{i} = -N\Big(\frac{m^{2}}{2}+Bm\Big)\,,\qquad m := \frac{1}{N}\sum_{i} s_{i}\,.
$$

The second equality is exact, not an approximation: on the complete graph the energy depends on the spins only through the magnetization. Compare the mean-field energy (2.22) of the lattice model, with $$dJ\to 1$$. Everything that was approximate in Section 2.4 is therefore exact here. The partition function reduces to the one-dimensional integral (2.25) with the same entropy $$h(m)$$, the saddle-point equation is

$$
m = \tanh\big(\beta(m+B)\big)\,,
$$

and the model has the second-order transition of Figure 4 at $$\beta_{c} = 1$$ and the first-order transition of Figure 2 in $$B$$, exactly as analyzed in Section 2.5.

The reason mean-field theory is exact here is worth stating in a form that carries over to networks. The field felt by a single spin is $$-\partial E_{N}/\partial s_{i} = m + B$$: spin $$i$$ does not care about any individual other spin, only about the empirical average $$m$$, the "mean field." The classic argument then has three features:

1. *Each degree of freedom couples to the others only through an average.* (True by construction here.)
2. *The average barely fluctuates.* If the spins are roughly independent, the central limit theorem makes the fluctuations of $$m$$ of size $$O(1/\sqrt{N})$$; as $$N\to\infty$$ each spin sees a *deterministic* effective field $$m+B$$.
3. *The average is fixed self-consistently.* A single spin in the field $$m+B$$ has $${\mathbb{E}}(s_{i}) = \tanh(\beta(m+B))$$; since $$m$$ was *defined* as the average spin, consistency requires (5.2).

For a finite-dimensional lattice, where each spin has a few strongly coupled neighbors, steps 1–2 are approximations. For the $$1/N$$ all-to-all model they become exact as $$N\to\infty$$: the mean field is an average of $$N$$ weakly correlated terms, and the law of large numbers kills its fluctuations. Networks in mean-field scaling will turn out to be models of exactly this kind.

:::callout {title="Exercise" tone="amber"}
**Exercise 5.1 (Curie–Weiss by fixed-point iteration).** Solve (5.2) numerically by the fixed-point iteration $$m^{(k+1)}= \tanh\big(\beta(m^{(k)}+B)\big)$$, for $$\beta$$ below and above $$1$$ and for a few values of $$B$$, and watch the iteration converge. Which fixed points are stable? Keep this iteration in mind: we will meet its infinite-dimensional cousin below.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The iteration converges geometrically to a stable fixed point, at rate set by the slope $$\beta\,(1-m^{2})$$ of the right-hand side there. For $$\beta<1$$ the only fixed point is $$m=0$$ and it is stable. For $$\beta>1$$ the fixed point $$m=0$$ has slope $$\beta>1$$ and is unstable: any seed away from it flows to one of the two nonzero fixed points $$\pm m^{*}$$, which are stable, and a small $$B$$ selects the one with the sign of $$B$$ (the other survives as a stable fixed point too, the metastable state of Section 2.5). Its infinite-dimensional cousin is the fixed-point iteration for the McKean–Vlasov equation in Section 5.2.

:::

\#### 5.1.2 The general shape of a mean-field model

Nothing in the story above needed binary spins. More abstractly, one can take $$N$$ "particles" $$\theta_{i}\in{\mathbb{R}}^{p}$$ with an extensive energy of the form

$$
E_{N}(\theta) = \sum_{i=1}^{N} V(\theta_{i}) + \frac{1}{2N}\sum_{i,j=1}^{N} U(\theta_{i},\theta_{j})\,,
$$

with a single-particle potential $$V$$ and a symmetric pair interaction $$U$$, again with the characteristic $$1/N$$ coupling. The force felt by particle $$\theta_{i}$$ is $$-\nabla_{\theta_i}E_{N}$$. More so, for particles dominated by drag (highly viscous motion), the dynamics at zero temperature are governed by familiar gradient-descent equations

$$
\dot\theta_{i} = -\nabla_{\theta_i}E_{N} = -\nabla V(\theta_{i}) - \frac{1}{N}\sum_{j=1}^{N} \nabla_{1} U(\theta_{i},\theta_{j})\,,
$$

where $$\nabla_{1}$$ differentiates the first slot of $$U$$. Once more each particle feels only an empirical average of forces.

It is worth packaging this observation in a way that will carry over verbatim to networks. Define the *empirical measure*

$$
\rho_{N} := \frac{1}{N}\sum_{i=1}^{N} \delta(\theta-\theta_{i})\,,
$$

a probability measure on $${\mathbb{R}}^{p}$$ recording where the collection of $$N$$ particles sit. Then (5.4) says that every particle descends one and the same effective single-particle potential, shaped by where everyone currently is:

$$
\dot\theta_{i} = -\nabla_{\theta} \Psi(\theta_{i};\rho_{N})\,,\qquad \Psi(\theta;\rho) := V(\theta) + \int U(\theta,\theta')\,d\rho(\theta')\,.
$$

The particles are coupled *only through* $$\rho_{N}$$ — the exact analogue of "every spin feels only $$m$$." The same three-step argument as before then suggests that as $$N\to\infty$$ the empirical measure becomes deterministic and self-consistent. We will carry this out carefully, for networks, in the next subsection.

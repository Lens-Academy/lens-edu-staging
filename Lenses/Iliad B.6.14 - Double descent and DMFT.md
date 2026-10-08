---
id: '3993cfb8-bdbe-4905-ae34-8b7f19e43a55'
title: "B.6.14 Double descent and DMFT"
tldr: "Double descent as a dynamical phase transition in linear regression, and dynamical mean-field theory: self-consistency and a tour of applications in deep learning."
summary_for_tutor: "Sections 6.2-6.3 of Iliad worksheet B.6 Physics of Deep Learning. Covers the Li and Goldenfeld model with its notation table (nu=P/n), the DMFT equations and correlation and response functions, the asymptotic generalization error, ergodicity breaking, critical exponents, then self-consistency in a small example and a literature tour of DMFT. Contains Exercise 6.2 (double descent in the lab) and Exercise 6.3 (self-consistency in the smallest example), both with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 6.2 Double descent as a dynamical phase transition

As a complete worked application of the formalism, we describe recent work of Li and Goldenfeld (Li & Goldenfeld 2026), which uses dynamical mean-field theory to analyze the double-descent phenomenon and classifies it as a *dynamical phase transition*, all within the simplest possible setting: a teacher–student model of linear regression. Even this very simple model requires a long calculation, but the paper is quite readable despite the overhead. The headline: in the under-parametrized regime the optimization process is ergodic and relaxes to a finite-error solution, while the over-parametrized regime is a *non-ergodic* phase with genuinely non-equilibrium dynamics — an initial memorization stage leaves a persistent memory of the initial conditions and confines the dynamics to a subspace around the initialization. The diagnostic is the *response function* $$R(t,t')$$ of Section 6.1 — how a perturbation at time $$t'$$ affects the model's state at time $$t$$; the same object appears as a Green function in quantum mechanics, signal analysis, and information theory. In the under-parametrized regime the response function decays: no memory. In the over-parametrized regime it saturates at a finite value: persistent memory of initialization. Consistently, the first regime obeys the fluctuation–dissipation theorem (Kubo 1957; Kubo 1966; Goldenfeld 2018), while in the second the FDT breaks — the standard warning light, flagged in Section 6.1, that a system has gone out of equilibrium. The model here is quite simple, and the authors propose that the frameworks here may generalize across architectures, with different universality classes based on the variations of the task, proposing random feature models with multiplicative (state-dependent) noise as an extension, with the hopes of eventually attaining an RG framework for interpreting phase transitions in neural networks.

\#### 6.2.1 Model definition and formalism

**Notation.** We transcribe the paper into the conventions of these notes: $$P$$ trainable parameters, $$n$$ training samples, learning rate $$\eta$$, teacher weights $$w^{*}$$, student weights $$\hat w$$ (with response fields $$\tilde w$$), and the *overparametrization ratio*

$$
\nu := P/n
$$

as control parameter — the reciprocal of Section 2's load $$\alpha = n/N$$, so that the over-parametrized phase is $$\nu>1$$. For readers consulting the paper, the dictionary is:

| these notes | Li–Goldenfeld (Li & Goldenfeld 2026) |
| --- | --- |
| $$P$$ (parameters) | $$d$$ |
| $$n$$ (samples) | $$N$$ |
| $$\nu = P/n$$ | $$\alpha = d/N$$ |
| $$w^{*}$$, $$\hat w$$, $$\tilde w$$ | $$\beta$$, $$\hat\beta$$, $$\tilde\beta$$ |
| $$\eta$$ (learning rate) | $$\zeta$$ |

The batch-inclusion probability $$\gamma$$, the ridge $$\lambda$$, and the label-noise variance $$D$$ are as in the paper.

Explicitly, the student and teacher share the same architecture

$$
y^{\mu}=\frac{1}{\sqrt{P}}\sum_{i=1}^{P} w^{*}_{i} x_{i}^{\mu}+\epsilon^{\mu}
$$

where $$P$$ is the number of model parameters, $$\mu=1, \ldots, n$$ indexes the dataset with inputs $$x^{\mu}$$, the $$w^{*}_{i}$$ are the teacher's weights, and $$\epsilon^{\mu}$$ is label noise. The thermodynamic limit takes $$n \to \infty$$ and $$P \to \infty$$ with the overparametrization ratio $$\nu = P/n$$ — the paper's **complexity parameter** — held *fixed*. The three main regimes are now definable as under-parametrized: $$\nu<1$$, near-criticality: $$\nu \approx 1$$, and over-parametrized: $$\nu>1$$. We note their optimization procedure, which is SGD with both regularization controlled by $$\lambda$$ (set to zero for most of the work) and batching controlled by the binary indicator variable $$s_{\mu}$$ which is drawn for each point in the dataset with probability $$\gamma$$,

$$
{\hat{w}_i(t+1)=\hat{w}_i(t)-{\eta} \frac{\partial\left[ \frac{1}{2}\sum_{\mu=1}^{n} s^{\mu}\left(\hat{y}^{\mu}-y^{\mu}\right)^{2}+\frac{\lambda}{2}\|\hat{\boldsymbol{w}}\|_{2}^{2}\right]}{\partial \hat{w}_{i}(t)}}\,,
$$

From here they construct the MSRJD integral exactly as in Section 6.1; taking functional derivatives and averaging over the disorder (the dataset, the initialization, the batch selection, and the label noise) yields the correlation and response functions that are the main objects of study. We skip most of the details, but it is worth displaying the starting point — the dynamical partition function for gradient flow, equal to one just as promised in Section 6.1:

$$
\begin{aligned}Z_{\mathrm{dyn}}= \int \mathcal{D}\hat{\boldsymbol{w}}(t)\, \prod_{i=1}^{d} \delta\bigg[-\partial_{t}{\hat{w}}_{i}(t) - \lambda \hat{w}_{i}(t)+j_{i}(t) \hspace{1.2in}&\\ - \sum_{\mu=1}^{n} s^{\mu}(t) \frac{x_i^\mu}{\sqrt{d}}\bigg( \sum_{k=1}^{P} \frac{x_k^\mu}{\sqrt{d}}\big( \hat{w}_{k}(t) - w^{*}_{k} \big) - \epsilon^{\mu} \bigg) \bigg]&= 1\,.\end{aligned}
$$

We want to highlight the general structure of this equation as a path integral over an action with sources coupled to both the "physical" parameter fields and the response fields,

$$
\begin{aligned}Z_{\operatorname{d y n}}[\mathbf{j}, \tilde{\mathbf{j}}]=\Big\langle\int \mathcal{D}\hat{\boldsymbol{w}}(t) \mathcal{D}{\tilde{\boldsymbol{w}}}(t) \exp\Big(S_{\operatorname{d y n}}&+\sum_{i=1}^{P} \int \tilde{j}_{i}(t) \hat{w}_{i}(t) d t \\&+\sum_{i=1}^{n} \int j_{i}(t) \tilde{w}_{i}(t) d t\Big)\Big\rangle,\end{aligned}
$$

which is a very common object to see in statistical field theory! In general $$S_{\text{dyn}}$$ will hold all of the microscopic details of the theory, and this is a unique case with a fairly tractable model. In general we are not so lucky. The expectation value denoted by angled brackets is averaging over the input dataset $$\{\mathbf{x}^{\mu}\}_{\mu=1}^{n}$$, the initial condition $$\hat{\boldsymbol{w}}(0)$$, the stochastic sampling $$s_{\mu}(t)$$, and the added label noise $$\{\epsilon^{\mu}\}_{\mu=1}^{n}$$. For comedic relief we also write their full dynamical function integrated over quenched disorder:

$$
\begin{aligned}Z_{\operatorname{d y n}}&\propto \int \mathcal{D}\boldsymbol{\mathcal{B}}(t) \int \mathcal{D}\mathcal{Q}(t,t^{\prime}) \exp \bigg(- i \tilde{\boldsymbol{w}}\partial_{t}{\hat{\boldsymbol{w}}}- \lambda P\, Q_{2}(t,t) \\&-P\, Q_{1}\cdot \hat{Q}_{1} -P\, Q_{2} \cdot \hat{Q}_{2}-P\, Q_{3}\cdot \hat{Q}_{3} -P\, Q_{4}\cdot \hat{Q}_{4} \\&-\frac{n}{2}\log\operatorname{det}{\left(\begin{array}{cc}\gamma Q_2^\top - \gamma Q_4+\delta &\gamma^2 Q_3 \\ Q_1+D& \gamma Q_2-\gamma Q_4^\top+\delta\end{array}\right)}+\tilde{\boldsymbol{j}}\hat{\boldsymbol{w}}+ \boldsymbol{j}\tilde{\boldsymbol{w}}\\&+\int\!\!\int dt\, dt^{\prime}\sum_{k}\Big[\big( \hat{w}_{k}(t) - w^{*}_{k} \big) \hat{Q}_{1}(t,t^{\prime}) \big( \hat{w}_{k}(t^{\prime}) - w^{*}_{k} \big) \\&\hspace{1.2in}+ i\hat{w}_{k}(t) \hat{Q}_{2}(t,t^{\prime}) \tilde{w}_{k}(t^{\prime}) + i\tilde{w}_{k}(t) \hat{Q}_{3}(t,t^{\prime})\, i\tilde{w}_{k}(t^{\prime})\Big] \\&+\int dt \sum_{k} i\tilde{w}_{k}(t)\hat{Q}_{4}(t)w^{*}_{k}\bigg),\end{aligned}
$$

where $$\mathcal{D}\boldsymbol{\mathcal{B}}(t)$$ abbreviates the measure $$\mathcal{D}\hat{\boldsymbol{w}}(t)\, \mathcal{D}\tilde{\boldsymbol{w}}(t)$$ over the dynamical fields, and the new measure $$\mathcal{D}\mathcal{Q}(t,t^{\prime})$$ is

$$
\begin{aligned}\mathcal{D}\mathcal{Q}(t,t^{\prime}) = \left(\frac{P}{2\pi}\right)^{4} \mathcal{D}Q_{1}(t, t^{\prime})\, \mathcal{D}\hat{Q}_{1}(t, t^{\prime})\,&\mathcal{D}Q_{2}(t, t^{\prime})\, \mathcal{D}\hat{Q}_{2}(t, t^{\prime})\, \\ \times\, \mathcal{D}Q_{3}(t, t^{\prime})\, \mathcal{D}\hat{Q}_{3}(t, t^{\prime})\,&\mathcal{D}Q_{4}(t)\, \mathcal{D}\hat{Q}_{4}(t)\,.\end{aligned}
$$

Each of the $$\mathcal{Q}$$ variables represents a particular correlation function between two variables.

\#### 6.2.2 Overview of results via training and generalization error

They define the generalization error as a mean squared error (MSE)

$$
\varepsilon_{g}(t) = \langle \left(\frac{1}{\sqrt{P}}\sum_{i=1}^{P} x_{i}^{0}[\hat{w}_{i}(t)-w^{*}_{i}]-\epsilon^{0}\right)^{2} \rangle
$$

After taking the thermodynamic limit, the generalization error is expressed in terms of the equal time correlator $$C(t,t)$$ determined from the DMFT equations and $$D$$, the noise variance:

$$
\varepsilon_{g}(t) = C(t, t)+D
$$

They find two forms of this equation and propose a third, a scaling relation near the critical point. At $$\lambda=0$$ for $$\nu<1$$, the asymptotic error is:

$$
\varepsilon_{g}(t\to\infty)=D(\gamma \chi+1) = \frac{D}{1-\nu}\,.
$$

Note the pole as criticality is approached. The quantity $$\chi=\int_{0}^{\infty}R(\tau)\,d\tau$$ is the **susceptibility**; it is well-defined only when the response function decays, i.e. only in equilibrium. Its appearance here signals that in this phase the response to perturbations of the initial conditions really does decay: asymptotically, the system carries no memory of its initialization.

The *non-ergodic phase* with persistent memory is captured by the asymptotic generalization error depending explicitly on the retention of the initial condition $$C(0,0)$$ and still showing sensitivity to $$\nu \to 1$$ analogous to the $$\nu<1$$ regime near criticality:

$$
\varepsilon_{g}(t\to\infty)=\frac{(\nu-1)\,C(0,0)}{\nu}+\frac{D\nu}{\nu-1}\,,
$$

where fully, $$C(0,0) = \langle \hat{w}^{2}(0)\rangle + r$$. The term $$\langle \hat{w}^{2}(0)\rangle$$ is the variance of the initialization and $$r$$ is the mean-squared norm of the ground-truth parameters per dimension. Note that here, the response function does not decay, because we carry memory of the initial conditions. It saturates at $$R(\tau \to \infty)=\frac{\nu-1}{\nu}$$, which they call the *ergodicity-breaking degree*, quantifying the persistent memory of a perturbation applied to the initialization.

They also show similar trends with the training error, namely for $$\nu<1$$ the error is asymptotically finite, as the model is still attempting to approximate the solution, while for $$\nu>1$$ the training error vanishes as initialization-dependent memorization ensures the model always performs accurately on the training data. They write training error as

$$
\lim_{t \to \infty}\varepsilon_{t}(t)=(\gamma \chi+1)^{-2}\,\varepsilon_{g}(t\to\infty)\,.
$$

For $$\nu<1$$ it simplifies to $$D(1-\nu)$$, while again, for $$\nu>1$$, the system is no longer at equilibrium and the susceptibility $$\chi=\int_{0}^{\infty}R(\tau)d\tau$$ diverges, which drives the training error to zero.

To characterize the critical behavior of the model near $$\nu \approx 1$$, they calculate the critical exponents $$(\sigma,\phi)$$ and propose a scaling function. The first part is relatively straightforward, where from Eqs. (6.18) and (6.19), one finds $$\varepsilon_{g}(t\to\infty)$$ diverges from both sides $$\nu\to 1^{\pm}$$. This suggests the scaling $$\varepsilon_{g}(t\to\infty)\sim |1-\nu|^{-\sigma}$$ with an exponent $$\sigma = 1$$ in DMFT. We remind the reader that these are asymptotic long-time steady-state results and both training and generalization error are time-dependent. Since the saturation time is $$\nu$$-dependent, a general feature of phase transitions is a dynamic scaling data collapse should be present near the transition (Goldenfeld 2018). They make this argument and propose a scaling ansatz of form:

$$
\varepsilon_{g} \approx \frac{D}{|1-\nu|^{\sigma}}\, F\!\left(\frac{|1-\nu|^{\phi} (\gamma t)}{4}\right)\,,
$$

where they introduce a new critical exponent $$\phi$$ and write the universal scaling function $$F(z)$$, and $$\gamma$$ is still the probability of samples being included. They make two observations about the form of $$F$$ near and at the critical point. First, near the point, $$\nu \to 1^{\pm}$$ corresponds to $$z\to 0$$, they argue the singularity in front must be absorbed into $$F$$ and it takes the asymptotic form $$F(z) \sim z^{\sigma/\phi}$$. Second, at $$\nu = 1$$, since the generalization error grows in time instead of saturating, $$\epsilon_{g} (t) \sim (\gamma t )^{\sigma / \phi}$$. The exponent $$\phi$$ therefore characterizes this growth in training time. Notably, the form of Eq. (6.21) implies a characteristic time scale, which they denote $$\tau(\nu) = (\gamma |1-\nu|^{\phi})^{-1}$$ to describe convergence in the scaling of the error. Since the error grows, we would expect this to diverge as $$\nu \to 1$$, which it does, and is an iconic signature of a phase transition, called **critical slowing down**. In MC calculations for lattice systems for example, this shows up in the autocorrelation time increasing, and requiring more time to get uncorrelated samples as we approach the critical point. A great deal of energy goes into designing methods to circumvent this slowing down when attempting to measure precise values of critical exponents using MC techniques, and motivates the choice of entirely different paradigms like RG flow or conformal bootstrap where applicable (Goldenfeld 2018).

:::callout {title="Exercise" tone="amber"}
**Exercise 6.2 (Double descent in the lab).** Simulate the model of this subsection: teacher $$w^{*} \sim {{\mathcal N}}(0, r\, I_{P})$$, inputs $$x^{\mu} \sim {{\mathcal N}}(0, I_{P})$$, labels $$y^{\mu} = w^{*}\cdot x^{\mu}/\sqrt{P}+ \epsilon^{\mu}$$ with noise variance $$D$$; student $$\hat w$$ trained by the update (6.11) with ridge $$\lambda = 0$$ and full batches ($$\gamma = 1$$), from $$\hat w(0)\sim{{\mathcal N}}(0,\sigma_{0}^{2} I_{P})$$. Take $$P = 200$$ and $$\nu = P/n \in \{0.5,\, 0.9,\, 1.1,\, 2\}$$.

**(a)** Plot training and generalization error against time, and verify the asymptotics (6.18) and (6.19) — including the divergence of *both* branches as $$\nu\to1$$: double descent, resolved in time.

**(b)** Probe ergodicity breaking: run two clones from initializations differing by a small random $$\delta\hat w(0)$$, and track the normalized separation $$|\Delta \hat w(t)|^{2}/|\Delta\hat w(0)|^{2}$$. Verify that it decays to zero for $$\nu<1$$ but saturates for $$\nu>1$$ — at the predicted plateau $$(\nu-1)/\nu$$, the paper's ergodicity-breaking degree, measured in twenty lines of code.

**(c)** Near $$\nu=1$$, extract the relaxation time of $$\varepsilon_{g}(t)$$ and check for the critical slowing down $$\tau \sim |1-\nu|^{-\phi}$$ of Eq. (6.21).
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** With full batches and $$\lambda=0$$, gradient descent converges for $$\eta < 2/\lambda_{\max}(X^{T}X/P)$$; keep $$\eta$$ a safe factor below. The late-time errors match (6.18) and (6.19), and plotting $$\varepsilon_{g}(t\to\infty)$$ against $$\nu$$ traces the double-descent peak at $$\nu=1$$ from both sides.

**(b)** The clone separation obeys the *linear* dynamics $$\Delta\hat w(t+1) = \big(I - \eta\, X^{T}X/P\big)\,\Delta\hat w(t)$$: it decays iff the sampled covariance $$X^{T}X$$ has full rank, i.e. iff $$n \ge P$$ ($$\nu\le1$$). For $$\nu>1$$ the covariance has a null space of dimension $$P-n$$, and the projection of $$\Delta\hat w(0)$$ onto it survives forever; for an isotropic perturbation the expected surviving fraction is $$(P-n)/P = (\nu-1)/\nu$$ — precisely the paper's ergodicity-breaking degree $$R(\tau\to\infty)$$.

**(c)** The relaxation time is set by the smallest nonzero eigenvalue of $$X^{T}X/P$$, which by Marchenko–Pastur closes like $$(1-\sqrt{1/\nu}\,)^{2} \sim |1-\nu|^{2}/4$$ near threshold, so one expects $$\phi \approx 2$$; compare with the paper's measured exponent and with the collapse ansatz Eq. (6.21).

:::

\### 6.3 Dynamical mean-field theory (DMFT)

Dynamical mean-field theory, of which Section 6.2 was one instance, is a general strategy for reducing the number of effective degrees of freedom in an interacting dynamical system: one follows a *single* representative degree of freedom, moving in a fluctuating background that stands in for all the others — and one demands that the statistics of the background be determined, self-consistently, by the statistics of the representative trajectory itself. This is the same trichotomy as every other mean field in these notes (couple through averages; argue fluctuations are controlled; close self-consistently), upgraded from scalars and measures to two-time functions. An excellent intuition-building tutorial in a biophysics context is (Blumenthal 2025), and (Cugliandolo 2023) is a broad modern review. In quantum many-body theory the same idea has been enormously effective for otherwise intractable systems (Georges et al. 1996; Kotliar et al. 2006). Below we first clarify what *self-consistency* means in a dynamical setting, then survey the recent deep-learning literature; a natural technical entry point for the latter is the out-of-equilibrium DMFT of the perceptron (Agoritsas et al. 2018).

\#### 6.3.1 Self-consistency

The term *self-consistency* describes the demand that the predictions of a theory agree with the approximations used to obtain them. A simple example, taken from (Stapmanns et al. 2020), makes the issue vivid (and is worked in detail in Exercise 6.3). Consider the stochastic process $$d x (t) = f (x(t))\, d t + dW(t)$$, with $$W$$ a Wiener process (so that $$\dot W$$ is the white noise of Section 6.1), and suppose $$f(x_{0}) = 0$$ with $$f'(x_{0})<0$$: a stable fixed point of the noiseless dynamics. One can expand around it, writing $$x(t) = x_{0} + \delta x(t)$$, to obtain the approximation

$$
\frac{d \,}{d t}\delta x(t) = f'(x_{0}) \delta x(t) + \xi(t) + \mathcal{O}(\delta^{2} x(t))\,,
$$

where $$\xi$$ is also centered gaussian white noise. The mean and variance of these fluctuations can be computed straightforwardly via Fourier transform, and in the temporal basis the variance is $$\left\langle \delta x^2 \right\rangle= \frac{D}{- 2 f'(x_{0})}$$, however using these results with the Taylor expansion of $$f(x)$$ to second order gives a correction to the mean

$$
\left\langle x \right\rangle\approx x_{0} + \frac{1}{2}\frac{f''(x_{0})}{f'(x_{0})}\frac{D}{2 f'(x_{0})}
$$

which is *inconsistent* with the value $$x_{0}$$ assumed for the mean when constructing the approximation: the noise, filtered through the curvature of $$f$$, shifts the very point we expanded around.

:::callout {title="Exercise" tone="amber"}
**Exercise 6.3 (Self-consistency in the smallest possible example).** **(a)** Derive the stationary variance $$\left\langle \delta x^2 \right\rangle= D/(-2f'(x_{0}))$$ of the linearized dynamics (compare Exercise 6.1(b)).

**(b)** Carrying the Taylor expansion of $$f$$ to second order, derive the quoted correction to the mean.

**(c)** Propose the self-consistent repair: expand instead around a point $$x_{*}$$, chosen so that the *effective* drift vanishes, $$f(x_{*}) + \tfrac{1}{2}f''(x_{*})\left\langle \delta x^2 \right\rangle_{*} = 0$$, with $$\left\langle \delta x^2 \right\rangle_{*} = D/(-2f'(x_{*}))$$ determined simultaneously. Note the structure: two coupled equations, each an input to the other — a miniature of the Curie–Weiss condition of Section 5.1, and of the DMFT equations to come.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The linearized equation $$\dot{\delta x}= f'(x_{0})\,\delta x + \xi$$ is an Ornstein–Uhlenbeck process with $$k = -f'(x_{0}) > 0$$; by Exercise 6.1(b) its stationary variance is $$D/(2k) = D/(-2f'(x_{0}))$$.

**(b)** Taking the stationary average of $$\dot x = f(x) + \xi$$ with $$f$$ expanded to second order about $$x_{0}$$: $$0 = f(x_{0}) + f'(x_{0})\langle\delta x\rangle + \tfrac{1}{2}f''(x_{0})\langle \delta x^{2}\rangle$$, and using $$f(x_{0})=0$$, $$\langle x\rangle = x_{0} - \frac{f''(x_{0})}{2f'(x_{0})}\,\langle\delta x^{2}\rangle = x_{0} + \frac{1}{2}\frac{f''(x_{0})}{f'(x_{0})}\cdot\frac{D}{2 f'(x_{0})}$$, the quoted shift — nonzero, contradicting the assumption $$\langle x\rangle = x_{0}$$.

**(c)** Demand instead that the expansion point $$x_{*}$$ satisfy the *effective* stationarity condition $$f(x_{*}) + \tfrac{1}{2}f''(x_{*})\,\langle\delta x^{2}\rangle_{*} = 0$$ together with $$\langle\delta x^{2}\rangle_{*} = D/(-2f'(x_{*}))$$. These are two equations determining $$(x_{*}, \langle\delta x^{2}\rangle_{*})$$ jointly: the fluctuations shape the effective potential, and the effective potential shapes the fluctuations. Structurally this is $$m = \tanh(\beta(m+h))$$ again — and DMFT is the same fixed-point demand imposed on entire two-time functions $$C(t,t')$$, $$R(t,t')$$ instead of scalars.

:::

A framework for resolving this, and also attempting to enforce that the small parameter we expand about is actually the expansion parameter involves using *n-particle irreducible effective actions* (nPI). A full discussion of this is well beyond the scope of this document, but is covered very well in a pedagogical introduction (Berges 2004), where the main idea is enforcing self-consistency via increasingly multi-local sources that generate n-point correlation functions. The first section emphasizes that performing standard perturbation theory with an anharmonic oscillator yields so-called *secular* terms which are powers of time $$t$$ that appear next to the actual expansion parameter $$\epsilon$$, and using the nPI framework effectively resums these terms properly at each order in $$\epsilon$$. The 1PI approach is directly related to a local approximation with mean field theory, while in the 2PI approach, the object determined self consistently is the 2-point function, which in the local approximation is related to the local propagator and is the basis of dynamical mean field theory.

\#### 6.3.2 Recent applications in deep learning

Fortunately, one rarely needs the general nPI machinery in practice. The working route — structurally the same trick by which large-$$N$$ models in physics (*e.g.* the $$G$$–$$\Sigma$$ formulation of the SYK model) are solved — is to insert bilocal *collective fields* for the correlation and response functions via delta functions, exactly as the $$Q$$'s of Section 6.2, and then to evaluate their path integral by saddle point in a suitable $$N\to\infty$$ limit. This is how the deep-learning DMFT of (Bordelon & Pehlevan 2022; Bordelon et al. 2024) is constructed.

A brief, opinionated tour of the literature, oldest first.

*Spin-glass origins.* The mean-field dynamics of disordered systems is where all of this machinery was forged. Amit, Gutfreund, and Sompolinsky (Amit et al. 1985) brought spin-glass methods into neural networks (in the guise of Hopfield-style associative memories), and Sompolinsky, Crisanti, and Sommers (Sompolinsky et al. 1988) derived the DMFT of random recurrent networks, discovering a transition to chaos. The structural point to retain: an ordered system like the Ising magnet has one global coupling $$J\sum_{\langle ij\rangle}\sigma_{i}\sigma_{j}$$ and is already hard; a *disordered* system has random couplings $$\sum_{ij}J_{ij}\sigma_{i}\sigma_{j}$$, and it is precisely the all-to-all randomness that makes mean-field methods exact — the same structural feature that data-dependent couplings give learning problems, starting with the perceptron of Section 2.

*The Bordelon–Pehlevan program.* For deep networks trained by gradient descent at fixed dataset, the DMFT of (Bordelon & Pehlevan 2022) takes the infinite-width limit and finds that the order parameters are precisely the *feature kernels* $$\Phi(t,s)$$ and *gradient kernels* $$G(t,s)$$ — two-time generalizations of the NNGP kernel and NTK of Sections 3–4. The lazy regime of Section 4 is recovered when these kernels freeze; rich, feature-learning dynamics is their genuine evolution, computed self-consistently. (Fair warning: the notation is heavy — response fields and conjugate order parameters abound — but the structure is exactly MSRJD plus a saddle point.) The program now includes finite-width kernel fluctuations (Bordelon & Pehlevan 2023), hyperparameter transfer across *depth* (Bordelon et al. 2023), and the dynamical theory of neural scaling laws (Bordelon et al. 2024) that we meet again in Section 7.9.

*The Mignacco–Urbani line.* A complementary series of works treats the *data* as quenched disorder at proportional scalings of dimension and sample size, in the spirit of Section 2: DMFT for Gaussian-mixture classification (Mignacco et al. 2021), and a DMFT characterization of the effective noise of SGD at late times (Mignacco & Urbani 2022) — the dynamical refinement of the batch-noise discussion of Section 2.1.

*Rigor.* What began as a physics heuristic is increasingly a theorem: rigorous derivations of DMFT for first-order methods now exist (Celentano et al. 2021; Gerbelot et al. 2024), with a growing line of extensions — e.g. to adaptive Langevin diffusions, with propagation-of-chaos guarantees and convergence of the linear response (Fan et al. 2025). A recent tour de force in this direction (Montanari & Urbani 2025) solves the dynamics of a two-layer network at scale — a long calculation, but a well-organized paper — finding: the emergence of a slow timescale tied to the growth of the network's complexity (in the Gaussian/Rademacher sense); an inductive bias toward low complexity when the initialization has low complexity; a dynamical *decoupling* of the feature-learning and overfitting regimes; and a non-monotone test error, with a "feature unlearning" regime at very late times.

The connective tissue of this whole section, worth stating once more: the MSRJD path integral is to training dynamics what the Gibbs measure was to Bayesian learning — the object on which every physics technique (saddle points, disorder averages, collective fields, perturbation theory) can be brought to bear.

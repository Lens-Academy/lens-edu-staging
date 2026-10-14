---
id: 'aa917223-afd8-4881-aec1-d3477a1648cb'
title: "B.6.13 Bayesian grokking and MSRJD"
tldr: "Bayesian grokking as a first-order transition (reading exercise on Rubin et al. 2024), then the start of non-equilibrium physics with the MSRJD path-integral formalism."
summary_for_tutor: "Sections 5.7, 6 and 6.1 of Iliad worksheet B.6 Physics of Deep Learning. Covers the alternative grokking walkthrough (Gromov's modular-addition weights, terminology box: Langevin training, adaptive kernel, equivalent kernel, GFL and mixed phases), and the MSRJD recipe from a discrete Ito SDE to a path integral with a response field. Contains Exercise 5.6 (grokking as a first-order phase transition, reading questions a-e) and Exercise 6.1, both with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 5.7 Bayesian grokking: a first-order transition (alternative reading)

The alternative walkthrough takes the opposite starting point. Delayed, abrupt generalization should by now also trigger a reflex from Section 2.5: competing branches of a free energy, a first-order transition, and a metastable lag, exactly as dissected for the Ising perceptron in Section 2.6. The paper (Rubin et al. 2024) makes this reflex precise, and it is a fitting capstone for these notes: it assembles, in one real (if small) deep-learning phenomenon, nearly every tool we have developed: the Gibbs posterior of noisy training (Section 2.1), GP kernels and kernel regression (Sections 3.3 and 4.6), mean-field scaling and self-consistency (this section), and the anatomy of first-order transitions (Section 2.5). It is, however, a genuinely dense paper, written in an idiosyncratic dialect of the "adaptive kernel" school (Seroussi et al. 2023). This subsection is therefore structured as a reading exercise in the style of Section 1: the goal is to *recognize the structures*, not to verify the computations. Read the paper's introduction, setup, and modular-arithmetic results (*do not* read the appendices on a first pass), then work through Exercise 5.6.

*Warm-up.* Before any statistical mechanics, it helps to know concretely what the network is trying to become. Gromov (Gromov 2023) writes down *exact* weights for a two-layer network with quadratic activation that solve modular addition: the first-layer weights are plane waves on $$\mathbb{Z}_{P}$$ — entries $$\cos(2\pi k n/P)$$, $$\sin(2\pi k n/P)$$ at various frequencies $$k$$ — and the quadratic activation's product-to-sum identities convert them into the required functions of $$(n+m) \bmod P$$. Skim (Gromov 2023) just long enough to believe this. The lesson is that "the Fourier coefficients of the first-layer weights" becomes the obvious coordinate system for measuring how much structure a network has actually learned.

:::callout {title="Note" tone="blue"}

Some translations from the paper's language into that of these notes:

- *Langevin training at equilibrium*: as in Section 2.1 verbatim: noisy gradient descent with weight decay; at late times, the Gibbs posterior; the weight decay $$\gamma$$ sets the Gaussian prior and the noise level sets the temperature.
- *(Adaptive) kernel*: the GP kernels of Section 3.3, but evaluated in the *posterior* rather than the prior, self-consistently: the kernel determines the posterior over hidden weights, which determines the kernel. This is a finite-temperature sibling of the self-consistent Gibbs measure (5.22).
- *Equivalent kernel (EK) approximation*: the dense-data approximation of Section 4.6, where sums over training points are replaced by integrals over the input distribution. This is a cousin of an annealed approximation.
- *Mean-field scaling*: the readout starts with variance $$\sigma_{a}^{2}/N$$, and $$\sigma_{a}^{2}\to0$$ as $$N\to\infty$$; how this relates to the $$1/N$$ of (5.7) is Exercise 5.6(a).
- *GFL ("Gaussian feature learning") phase*: refers to a disordered phase, in which the single-neuron posterior is a Gaussian, centered at zero overlap with the teacher's structure; the kernel adapts only perturbatively.
- *Mixed phase*: a finite fraction of neurons shift to nonzero overlap (here: onto Fourier modes of the task) while the rest remain Gaussian; this *coexistence* is a signal of a first-order transition, cf. Section 2.6.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.6 (Grokking as a first-order phase transition).** Read (Rubin et al. 2024) as assigned above, and answer the following, citing where in the paper each answer lives. (Parts (a)–(e) have exact counterparts in Exercise 5.5, the other walkthrough; its part (f) is the shared comparison question.)

**(a)** *What scaling limit is taken?* Look for where the output-layer weight decay is fixed, and for the phrase "mean-field scaling." How does the paper's scaling relate to the parametrization (5.7) and to the $$\gamma$$-dial of Section 5.4? Careful — this is subtler than it looks: in an *equilibrium* (Bayesian) framework there is no learning rate, so which part of Section 5.2's scaling prescription survives, and in what combination?

**(b)** *What is the order parameter* for the modular-addition task? What does the posterior distribution of a *single neuron's* input weights look like on each side of the transition, and which figure of Section 5.2 does the ordered side resemble?

**(c)** *What are the main computational techniques?* List them, and match each to the section of these notes where its ancestor appears.

**(d)** *What parameter is tuned* to cross the phase transition in the paper's phase diagrams?

**(e)** *Where did the time go?* Grokking is a statement about training *time*, yet the paper computes a static equilibrium ensemble. How does a first-order transition in an equilibrium free energy produce *delayed, abrupt* generalization in a training run? Compare, line by line, with the metastability discussion for the Ising perceptron in Section 2.6.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** A Bayesian two-layer network $$f(x)=\sum_{i=1}^{N} a_{i}\,\phi(w_{i}\cdot x)$$ whose readout prior (set by the output-layer weight decay) has variance $${\mathbb{E}}[a_{i}^{2}]=\sigma_{a}^{2}/N$$; the limit taken is $$N\to\infty$$ *together with* $$\sigma_{a}^{2}\to 0$$ — the paper's "mean-field scaling" — plus the EK (dense-data) approximation. The subtlety: at equilibrium, only the *induced prior on functions* matters. For the linear readout, a prefactor $$\kappa$$ in $$f=\kappa\sum_{i} a_{i}\phi$$ and a prior variance $$\sigma^{2}$$ for $$a_{i}$$ enter the function-space prior only through the product $$\kappa^{2}\sigma^{2}$$ (a Gaussian change of variables). So the mean-field parametrization (5.7) — prefactor $$1/N$$, order-one weights — corresponds to *bare* readout variance $$\propto 1/N^{2}$$, while variance $$\sigma_{a}^{2}/N$$ at *fixed* $$\sigma_{a}^{2}$$ would be precisely the standard GP scaling of Section 3. The mean-field regime is the additional suppression $$\sigma_{a}^{2}\to0$$. Meanwhile the other half of Section 5.2's prescription — the learning-rate rescaling (5.14) — has no equilibrium counterpart at all: the learning rate drops out of the stationary distribution (Section 2.1). In the language of the $$\gamma$$-dial: gradient-flow scalings are classified by (prefactor, initialization, learning rate) jointly, but their Bayesian shadows are classified by the single combination $$\kappa^{2}\sigma^{2}$$.

**(b)** The overlap $$\Phi(w)$$ of a hidden neuron's input weights with the teacher-relevant directions — for modular addition, the Fourier coefficients of $$w$$ on $$\mathbb{Z}_{P}$$ (the warm-up (Gromov 2023) says which ones matter). The sharper statement is about the *single-neuron posterior* $$P(w)$$: in the GFL phase it is a single Gaussian centered at $$\Phi=0$$; in the mixed phase it becomes a mixture, with a finite fraction of neurons condensed at $$\Phi\neq 0$$ and the rest still Gaussian. The order parameter jumps discontinuously: first order. The ordered side is a finite-temperature cousin of Figure 6, where the measure over neurons condenses onto the low-dimensional structures realizing the target.

**(c)** (i) Noisy training $$\to$$ Gibbs posterior (Section 2.1); (ii) mean-field decoupling of the posterior into readout $$\otimes$$ hidden-layer factors, with neurons coupled only through averages (this section); (iii) the self-consistent "adaptive" kernel $$Q_{\mu\nu}=\sigma_{a}^{2}\langle \phi(w\cdot x^{\mu})\phi(w\cdot x^{\nu})\rangle_{\rm posterior}$$, whose defining equation has exactly the structure of (5.22) — the kernel depends on a posterior that depends on the kernel; (iv) saddle-point evaluation (Section 2.4); (v) a variational Gaussian-*mixture* ansatz, needed precisely because a first-order transition means several competing saddles; (vi) the EK approximation for the data average (Section 4.6). Note what is *absent*: in the main text the data averaging is done by EK smoothing, not by the replica trick of Appendix A.2.

**(d)** Primarily the *sample size* $$n$$ at fixed temperature: below a critical number of training facts the disordered (memorizing) phase is dominant and the network never generalizes; above it, the mixed phase wins. (The transition line lives in the $$(n,\text{temperature})$$ plane, so it can equally be crossed by tuning the noise level or weight decay at fixed $$n$$ — but the grokking narrative crosses it in $$n$$.)

**(e)** In equilibrium there is no time; the free-energy crossing itself is instantaneous. The time-dependence of grokking is the *dynamical* lag of a first-order transition: Langevin training equilibrates quickly *within* the metastable disordered basin — which is enough to drive the train loss to zero (memorization is easy there) while test accuracy stays at chance — and only much later escapes to the thermodynamically dominant mixed phase, whereupon test accuracy jumps. This is precisely the Ising-perceptron story of Section 2.6: the information needed to generalize is present in the data well before the dynamics finds the ordered state, so capability arrives "abruptly and later than it should."

:::

\## 6. Non-equilibrium physics, MSRJD, and DMFT

So far our statistical-mechanics toolkit has been an equilibrium one: Gibbs measures, partition functions, and free energies (Section 2), together with limits in which training simplifies to kernel regression (Section 4) or to a deterministic flow of measures (Section 5). This section introduces the formalism that confronts the *dynamics* of learning head-on. The strategy is borrowed from non-equilibrium statistical physics: write the stochastic dynamics itself as a path integral — the Martin–Siggia–Rose–Janssen–De Dominicis (MSRJD) construction — then average over the randomness (noise, initialization, and, crucially, the training data, treated as quenched disorder exactly as in Section 2.3), and finally extract closed, self-consistent equations for a small set of *two-time* order parameters: correlation functions $$C(t,t')$$ and response functions $$R(t,t')$$. The result is known as dynamical mean-field theory (DMFT), and it is the third and final incarnation of "mean field" in these notes: the statics of Section 2 determined scalars self-consistently, the McKean–Vlasov limit of Section 5 determined a measure, and DMFT determines whole functions of two times.

The payoffs in this section are a complete worked application — double descent as a *dynamical phase transition* in linear regression (Section 6.2) — and a guided tour of the modern DMFT program for deep learning (Section 6.3), whose scaling-law application closes the notes in Section 7. Throughout, we follow the spirit of Altland and Simons (Altland & Simons 2010), which motivates the formalism in condensed-matter language with a good balance of detail and intuition, and we borrow freely from two pedagogical tutorials written for neuroscientists, (Chow & Buice 2012) and (Stapmanns et al. 2020).

\### 6.1 From stochastic dynamics to path integrals: the MSRJD formalism

When we model a system with fluctuations — or deliberately add noise to a deterministic model, as in the Langevin dynamics of Section 2.1 — differential equations become stochastic, and the difficulty of solving them jumps. A **stochastic differential equation**, at first order for example, takes the form

$$
\frac{d x}{d t}= f(x) + \xi\,,
$$

where $$\xi(t)$$ is a (Gaussian) white noise process — additive noise, $$\xi = \xi(t)$$, as opposed to multiplicative noise $$\xi=\xi(x,t)$$ — and $$x=x(t)$$ is now a random trajectory. The noise is entirely defined by the first and second moments,

$$
\left\langle \xi(t) \right\rangle_{\xi} = 0, \hspace{20pt}\left\langle \xi(t)\xi(t') \right\rangle_{\xi} = D \delta(t-t')\,,
$$

where the expectations are with respect to the noise ensemble[^3]. Obtaining closed-form solutions for the time evolution of the probability distribution for $$x(t)$$ is usually challenging. These evolutions can be attacked by the traditional routes — the Langevin and Fokker–Planck descriptions — for which the standard references are Risken (Risken 1996), Gardiner (Gardiner 2004), and van Kampen (van Kampen 2007). The objects of interest here are instead the moments of $$x(t)$$ and the probability density function $$p(x,t).$$ Methods developed in statistical physics (in particular those used in perturbative quantum field theory and classical non-equilibrium systems) using path integrals provide a way to calculate these statistical objects. The path integral, or functional integral, approach is convenient for perturbative calculations (expanding around an exactly solvable theory with a small parameter), but also permits importing other tools like renormalization group methods or other explicitly non-perturbative approaches when there is no small parameter, or the expansion breaks down (as they often do).

The conceptual recipe of the MSRJD formalism is short, and worth internalizing before the derivation:

- write down a *discrete* SDE, fixing a convention (Ito) that enforces causality;
- express the transition probability between time steps as a delta function imposing the update rule;
- assemble the product over infinitesimal steps into a path integral;
- write each delta function in Fourier representation, introducing an auxiliary *response field*;
- average over the noise, then add sources and differentiate to extract statistics.

It turns out that the historic approach of Onsager and Machlup (Onsager & Machlup 1953) is the "Lagrangian" version of this "Hamiltonian"-like approach; the two are related by a Legendre transform, or equivalently by integrating out the auxiliary field. That auxiliary field is aptly named the **response field**: as we will see below, its correlation functions compute how the system *responds* to external perturbations, and it is the genuinely new ingredient of the non-equilibrium formalism.

We now give the derivation, quickly but completely. The standard first step is to discretize time for a continuous equation, or simply start with a discrete update rule. Under this discretization $$x(t) \to x_{i}$$, where $$i = 1, ..., N,$$ so that,

$$
x_{i} = x_{i-1}+ \Delta t \Big(f(x_{i-1}) + \xi_{i-1}\Big)\,,
$$

where $$\Delta t$$ is the temporal spacing. We can rearrange this so that the RHS is zero and write the transition probability between steps as delta function, and the product of these representing a trajectory solution. Defining a solution of the stochastic differential equation as $$x[\xi]$$, an expectation value of an observable $$\mathcal{A}[x]$$ is formally,

$$
\left\langle \mathcal{A} [x] \right\rangle_{\xi}= \int \mathcal{D}x \mathcal{A}[x] \left\langle \delta(x- x[\xi]) \right\rangle_{\xi} = \int \mathcal{D}x \mathcal{A}[x] \left| \frac{\delta X}{\delta x} \right|\delta(X)\,.
$$

We used the shorthand $$X_{i} \equiv x_{i} - x_{i-1}- \Delta t \big[ f(x_{i-1}) + \xi_{i-1}\big]$$ for the constraint imposed at each step. The measure here, is a typical functional path integral measure $$\mathcal{D}x = \prod_{i} d x_{i}$$ with $$\delta(x- x[\xi])$$ similarly factorized across steps. In particular we also picked a first order finite difference and the convention that the noise is evaluated at the previous time-step, which is called Ito discretization or convention. Many common processes are manifestly Ito, like SGD for example, where the noise drawn at a batch doesn't affect the weights at that iteration. There are other conventions, the most common alternative is Stratonovich (which is more like a midpoint rule), however, Ito has a unit (volume-preserving) functional determinant and other schemes require careful treatment to avoid anomalous terms from the determinant. In our case the matrix is triangular with a unit diagonal. Substituting in the definition of $$X$$,

$$
\left\langle \mathcal{A}[x] \right\rangle_{\xi} = \int \mathcal{D}x\, \mathcal{A}[x]\, \left\langle \delta \big(\partial_t x - f(x) - \xi\big) \right\rangle_{\xi}\, .
$$

Finally, we can use the Fourier representation of the delta, introducing an auxiliary variable $$\tilde{x}$$, which in the continuum is

$$
\left\langle \mathcal{A}[x] \right\rangle_{\xi} = \int \mathcal{D}x\, \mathcal{D}\tilde{x}\; \mathcal{A}[x]\; e^{\textstyle\, i \int dt\, \tilde{x}\, (\partial_t x - f(x) - \xi)}\,.
$$

The final step is the payoff: the noise now appears *linearly* in the exponent, so the Gaussian average over $$\xi$$ can be done exactly, $$\big\langle e^{-i\int dt\, \tilde x\, \xi}\big\rangle_{\xi} = e^{-\frac{D}{2}\int dt\, \tilde x^2}$$, leaving the **MSRJD functional integral**

$$
\begin{aligned}\left\langle \mathcal{A}[x] \right\rangle&= \int \mathcal{D}x\, \mathcal{D}\tilde{x}\; \mathcal{A}[x]\; e^{-S[x,\tilde x]}\,, \\ S[x,\tilde x]&= \int dt\, \Big[ -i\,\tilde{x}\, \big(\partial_{t} x - f(x)\big) + \frac{D}{2}\, \tilde x^{2} \Big]\,.\end{aligned}
$$

Four structural comments, each of which does real work later:

- *The partition function is one.* Setting $$\mathcal{A}=1$$, the integral is just $$\int \mathcal{D}x$$ of a normalized probability: $$Z_{\rm dyn}=1$$, with no sources. Unlike in equilibrium, all the physics lives in correlation functions, obtained by coupling sources to both $$x$$ and $$\tilde x$$ and differentiating — compare the $$Z_{\rm dyn}=1$$ starting point of Section 6.2.
- *The response field earns its name.* Perturbing the drift, $$f \to f + h(t)$$, changes the action by $$i\int \tilde x\, h$$, so

$$
R(t,t') := \frac{\delta \left\langle x(t) \right\rangle}{\delta h(t')}\bigg|_{h=0}= \left\langle x(t)\, i \tilde x(t') \right\rangle\,.
$$

Correlators of $$\tilde x$$ compute responses to kicks. Causality is built in: $$R(t,t')=0$$ for $$t<t'$$ (the Ito discretization is what guarantees this, along with $$\left\langle \tilde x\, \tilde x \right\rangle= 0$$).
- *Two-time observables.* The natural objects of the formalism are the correlation function $$C(t,t') = \left\langle x(t)x(t') \right\rangle$$ and the response $$R(t,t')$$. In *equilibrium* they are not independent: the fluctuation–dissipation theorem (FDT) locks them together, $$T\, R(t,t') = -\partial_{t'}C(t,t')$$ for $$t>t'$$ (with $$T = D/2$$ in our normalization) (Kubo 1957; Kubo 1966). A measured *violation* of the FDT is therefore the standard diagnostic that a system is genuinely out of equilibrium — the warning light used to great effect in Section 6.2.
- *Onsager–Machlup.* The action (6.7) is quadratic in $$\tilde x$$, so the response field can be integrated out exactly, giving the probability of a trajectory as $$P[x] \propto e^{-\frac{1}{2D}\int dt\, (\partial_t x - f(x))^2}$$: the Lagrangian form promised above, in which the most probable path extremizes a classical action.

:::callout {title="Exercise" tone="amber"}
**Exercise 6.1 (The Ornstein–Uhlenbeck process and the FDT).** **(a)** Fill in the noise average leading to (6.7).

**(b)** For the linear drift $$f(x) = -k x$$ (the Ornstein–Uhlenbeck process), compute the stationary correlation and response functions, either by Fourier transforming the quadratic action or by solving the SDE directly: $$C(\tau) = \frac{D}{2k}e^{-k|\tau|}$$ and $$R(\tau) = \theta(\tau)\, e^{-k\tau}$$.

**(c)** Verify the fluctuation–dissipation theorem $$T R(\tau) = -\partial_{\tau} C(\tau)$$ for $$\tau>0$$, with $$T = D/2$$.

**(d)** Explain, from the discrete-time construction, why $$\left\langle \tilde x(t) \tilde x(t') \right\rangle= 0$$ and why $$R$$ is causal.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The white-noise measure is Gaussian with $$\langle \xi(t)\xi(t')\rangle = D\,\delta(t-t')$$, so $$\big\langle e^{-i\int \tilde x\, \xi}\big\rangle = e^{-\frac{D}{2}\int \tilde x^2}$$, and collecting terms in the exponent gives (6.7).

**(b)** The linear SDE is solved by $$x(t) = \int_{-\infty}^{t}ds\; e^{-k(t-s)}\,\xi(s)$$ (stationary state). Then $$C(\tau) = \int_{-\infty}^{t}ds\int_{-\infty}^{t'}ds'\, e^{-k(t-s)-k(t'-s')}D\,\delta(s-s') = \frac{D}{2k}e^{-k|\tau|}$$ with $$\tau = t-t'$$. Adding a perturbation $$h$$ to the drift shifts the solution by $$\int_{-\infty}^{t} ds\, e^{-k(t-s)}h(s)$$, so $$R(\tau) = \theta(\tau)\, e^{-k\tau}$$.

**(c)** For $$\tau>0$$: $$-\partial_{\tau} C = \frac{D}{2}e^{-k\tau}= \frac{D}{2}\,R(\tau)$$, i.e. $$T R = -\partial_{\tau} C$$ with $$T = D/2$$.

**(d)** In the discrete construction each delta function propagates information strictly forward in time (Ito: the noise at step $$i-1$$ affects $$x_{i}$$, never earlier variables). Diagrammatically, $$\langle x \tilde x\rangle$$ is a retarded propagator; $$\langle \tilde x\tilde x\rangle$$ would be a closed loop of retarded propagators, which vanishes — equivalently, "a response to no perturbation is not an observable." Causality of $$R$$ is the same statement.

:::

[^3]: As a point of notation, $$\eta$$ and $$\zeta$$ are also commonly used for noise, and we will distinguish between discrete and continuum delta functions as $$\delta_{ij}$$ and $$\delta(t-t')$$ respectively.

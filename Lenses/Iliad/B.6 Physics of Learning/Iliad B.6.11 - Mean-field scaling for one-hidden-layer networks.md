---
id: '1989ece8-f18b-4838-809c-77bf33452fab'
title: "B.6.11 Mean-field scaling for one-hidden-layer networks"
tldr: "The one-hidden-layer network with 1/N scaling as a mean-field particle system: equations of motion, continuity equation and the McKean-Vlasov equation, with a numerical lab."
summary_for_tutor: "Section 5.2 (5.2.1-5.2.5) of Iliad worksheet B.6 Physics of Deep Learning. Covers the 1/N normalization, initialization near the zero function, the loss as a mean-field energy with potentials V and U, rescaled gradient flow, the Curie-Weiss dictionary table, the continuity equation for the empirical measure, the McKean-Vlasov self-consistency, propagation of chaos and Chizat-Bach convergence. Contains Exercise 5.2 (structure of the mean-field equations) and Exercise 5.3 (numerics: the mean-field network, lab), both with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 5.2 Mean-field scaling for one-hidden-layer networks

Return to the one-hidden-layer network (4.26) of Sections 3.5 and 4.3, but now normalized with $$1/N$$ out front instead of $$1/\sqrt{N}$$, with the same *order-one* weights:

$$
f_{\theta}(x) = \frac{1}{N}\sum_{i=1}^{N} c_{i}\,\phi(a_{i}\cdot x)\,,\qquad c_{i},\, a_{ij}\sim {{\mathcal N}}(0,1)\,,
$$

with $$c_{i}\in{\mathbb{R}}$$, $$a_{i},x\in{\mathbb{R}}^{d}$$ (as in (4.26), the first-layer factor $$1/\sqrt{d}$$ has been absorbed into $$x$$). Compared with the fan-in normalization of Sections 3–4, mean-field scaling suppresses the output by *one extra factor of $$1/\sqrt{N}$$*. The function class is identical — only the coordinates on it have changed. However, gradient flow is *not* invariant under reparametrization: as emphasized in Section 4.1.1 and in the callout of Section 4.3, gradient descent presupposes the Euclidean metric on parameter space, and rescaling coordinates rescales that metric. Two parametrizations of the same function class can (and here will) flow along completely different trajectories.

For a mean-field analysis, our $$N$$ particles are going to be the $$N$$ hidden neurons, with parameters

$$
\theta_{i} = (c_{i},a_{i}) \in {\mathbb{R}}^{d+1}\,,\qquad i=1,...,N\,.
$$

Their values are encoded in the empirical measure (5.5), and the network (5.7) depends on its parameters only through $$\rho_{N}$$,

$$
f_{\theta}(x) = \int c\,\phi(a\cdot x)\,d\rho_{N}(c,a) =: f_{\rho_N}(x)\,.
$$

We think of the network value $$f_{\rho}$$ as a linear functional of $$\rho$$. Neurons are viewed as exchangeable particles, and the measure is their state.

\#### 5.2.1 Initialization

At initialization, the summands $$c_{i}\phi(a_{i}\cdot x)$$ in (5.7) are i.i.d. with mean zero (since $$c_{i}$$ is independent of $$a_{i}$$ and $${\mathbb{E}}[c_{i}]=0$$). With the $$1/N$$ prefactor, the law of large numbers gives, for each fixed $$x$$,

$$
f_{\theta_0}(x) = \underbrace{{\mathbb{E}}\big[c\,\phi(a\cdot x)\big]}_{=\,0}+ \,O(1/\sqrt{N}) \;\xrightarrow{\;N\to\infty\;}\; 0\,.
$$

Contrast this with Section 3.4: with the $$1/\sqrt{N}$$ normalization, the same sum sits exactly at the scale of its fluctuations, and the CLT produces an order-one Gaussian process. Mean-field scaling instead sits at the scale of the *mean*.

The network begins training as (essentially) the zero function; there is no random-function prior to speak of, and whatever the trained network becomes is built by training rather than inherited from initialization.

\#### 5.2.2 The loss is a mean-field energy

Let's train on MSE loss over the data $$(x^{\mu},y^{\mu})_{\mu=1}^{n}$$, as in Section 4:

$$
{{\mathcal L}}(\theta) = \frac{1}{2}\sum_{\mu=1}^{n} \big(f_{\theta}(x^{\mu})-y^{\mu}\big)^{2}\,.
$$

Inserting (5.7) and expanding the square, we get

$$
{{\mathcal L}}(\theta) = \text{const}+ \frac{1}{N}\sum_{i=1}^{N} V(\theta_{i}) + \frac{1}{2N^{2}}\sum_{i,j=1}^{N} U(\theta_{i},\theta_{j})\,,
$$

with

$$
V(\theta) = -\sum_{\mu=1}^{n} y^{\mu}\, c\,\phi(a\cdot x^{\mu})\,,\qquad U(\theta,\theta') = \sum_{\mu=1}^{n} c\,\phi(a\cdot x^{\mu})\; c'\,\phi(a'\cdot x^{\mu})\,.
$$

Comparing (5.12) with (5.3), we see that up to an overall factor of $$N$$, the loss is precisely a mean-field energy. In particular, $$E_{N}:=N{{\mathcal L}}$$ has the canonical normalization from (5.3) and is extensive, while the loss itself can be interpreted as the *intensive* energy per neuron.

We can also identify physical roles for the two potentials! $$V$$ rewards neurons for aligning their output function $$c\,\phi(a\cdot{}\cdot)$$ with the data, playing the role of the external field $$B$$; while $$U$$ is a data-weighted interaction between *pairs* of neurons that penalizes redundant features, playing the role of the spin-spin coupling.

\#### 5.2.3 Equations of motion and the mean field

Because $$\partial f/\partial \theta_{i} = O(1/N)$$ in this parametrization, raw gradients of $${{\mathcal L}}$$ are $$O(1/N)$$, and gradient flow at fixed learning rate would freeze as $$N\to\infty$$. We must therefore scale the learning rate *up*,

$$
\eta = N\,\tilde\eta\,,
$$

with $$\tilde\eta$$ fixed. (Equivalently, we could run vanilla gradient flow on the extensive energy $$E_{N}=N{{\mathcal L}}$$.) This is the rule of Section 4.3 at work: the NTK, computed below in (5.24), is $$O(1/N)$$, so keeping $$\frac{d}{dt}f^{\mu} = -\eta\,\Theta^{\mu\nu}\Delta^{\nu}$$ of order one requires $$\eta\propto N$$. Note the contrast with Section 4.3: there the NTK was of order one and the learning rate needed no rescaling; here the NTK *shrinks* like $$1/N$$ and we scale up. Recall also the caveat from that section about changes of variables. The mean-field network could equally be written without a prefactor, $$f = \sum_{i}\tilde c_{i}\phi(a_{i}\cdot x)$$ with $$\tilde c_{i} = c_{i}/N\sim{{\mathcal N}}(0,1/N^{2})$$; but then the *same* dynamics (5.15) requires a learning rate $$\tilde\eta/N$$ for the readout weights $$\tilde c_{i}$$ and $$N\tilde\eta$$ for the hidden weights $$a_{i}$$ — one learning rate per layer, differing by a factor $$N^{2}$$. Keeping all weights of order one is what lets a single $$\eta$$ do the job, and it is the reason we adopted that convention in Section 3.2.

With (5.14), the flow $$\dot\theta = -\eta\nabla_{\theta}{{\mathcal L}}$$ becomes, per neuron,

$$
\dot c_{i} = -\tilde\eta \sum_{\mu=1}^{n} \Delta^{\mu}\, \phi(a_{i}\cdot x^{\mu})\,,\qquad \dot a_{i} = -\tilde\eta\; c_{i} \sum_{\mu=1}^{n} \Delta^{\mu}\, \phi'(a_{i}\cdot x^{\mu})\, x^{\mu}\,,
$$

where $$\Delta^{\mu} = f_{\rho_N}(x^{\mu})-y^{\mu}$$ is the residual of Section 4.1. Equivalently, in the potential form (5.6),

$$
\begin{aligned}\dot\theta_{i}&= -\tilde\eta\,\nabla_{\theta}\, \Psi(\theta_{i};\rho_{N})\,, \\ \Psi(\theta;\rho)&= V(\theta)+\int U(\theta,\theta')d\rho(\theta') = \sum_{\mu=1}^{n} \Delta^{\mu}_{\rho} \; c\,\phi(a\cdot x^{\mu})\,,\end{aligned}
$$

with $$\Delta_{\rho}^{\mu} = f_{\rho}(x^{\mu})-y^{\mu}$$.

As anticipated, the velocity of neuron $$i$$ depends on its own state $$(c_{i},a_{i})$$, and on all the other neurons only through the average $$f_{\rho_N}= \frac{1}{N}\sum_{j} c_{j}\phi(a_{j}\cdot{}\cdot)$$, via the residual $$\Delta^{\mu}$$. The network function $$f$$ is the mean field here! We arrive at a dictionary:

| Curie–Weiss | one-hidden-layer network, mean-field scaling |
| --- | --- |
| spin $$s_{i}\in\{\pm1\}$$ | neuron $$\theta_{i}=(c_{i},a_{i})\in{\mathbb{R}}^{d+1}$$ |
| magnetization $$m=\frac{1}{N}\sum_{j}s_{j}$$ | network function $$f_{\rho}=\frac{1}{N}\sum_{j}c_{j}\phi(a_{j}\cdot{}\cdot)$$ |
| external field $$B$$ | data term $$V$$ (the targets $$y^{\mu}$$) |
| pair coupling $$-\tfrac{1}{N}s_{i}s_{j}$$ | neuron-neuron interaction $$\tfrac{1}{N}U(\theta_{i},\theta_{j})$$ |
| effective field $$m+B$$ | residual $$\Delta^{\mu}_{\rho}= f_{\rho}(x^{\mu})-y^{\mu}$$ |
| extensive energy $$E_{N}$$ | $$N{{\mathcal L}}$$ (the loss is intensive) |
| zero-temperature dynamics | gradient flow |
| Langevin at temperature $$T$$ | noisy training, Section 2.1 |
| $$m = \tanh(\beta(m+B))$$ | self-consistent Gibbs measure, Equation 5.22 below |

:::callout {title="Exercise" tone="amber"}
**Exercise 5.2 (Structure of the mean-field equations).** **(a)** Derive (5.12)–(5.13) and (5.15), and check that (5.16) reproduces them, using the symmetry of $$U$$.

**(b)** (*Balancedness.*) For a positively homogeneous activation such as ReLU, $$\phi'(z)z = \phi(z)$$. Show that in this case (5.15) conserves $$c_{i}^{2} - |a_{i}|^{2}$$ for every neuron, exactly, along the flow. The two layers of a given neuron therefore remain coupled for all time. (On the other hand, distinct neurons will decouple from each other, as we'll see momentarily.)

**(c)** Observe that for MSE loss $$\dot c_{i}$$ in (5.15) does not depend on $$c_{i}$$ (only on $$a_{i}$$ and the mean field). Where does the linearity of $$f_{\rho}$$ in $$c$$ enter?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Expanding the square in the loss and collecting single-sum and double-sum terms gives (5.12)–(5.13) directly. For the equations of motion, $$\partial f_{\rho_N}(x^{\mu})/\partial c_{i} = \frac{1}{N}\phi(a_{i}\cdot x^{\mu})$$ and $$\partial f_{\rho_N}(x^{\mu})/\partial a_{i} = \frac{1}{N}c_{i} \phi'(a_{i}\cdot x^{\mu})x^{\mu}$$; the chain rule plus $$\eta = N\tilde\eta$$ gives (5.15). Writing the same gradient through $$\Psi$$, the symmetry $$U(\theta,\theta')=U(\theta',\theta)$$ ensures the double sum contributes twice the one-sided derivative, matching (5.16).

**(b)** From (5.15): $$c_{i}\dot c_{i} = -\tilde\eta\, c_{i} \sum_{\mu} \Delta^{\mu} \phi(a_{i}\cdot x^{\mu})$$ and $$a_{i}\cdot \dot a_{i} = -\tilde\eta\, c_{i} \sum_{\mu} \Delta^{\mu}\, \phi'(a_{i}\cdot x^{\mu})\,(a_{i}\cdot x^{\mu})$$. For positively homogeneous $$\phi$$, $$\phi'(z)z = \phi(z)$$, so the two right-hand sides coincide and $$\frac{d}{dt}\big(c_{i}^{2} - |a_{i}|^{2}\big) = 2(c_{i}\dot c_{i} - a_{i}\cdot\dot a_{i}) = 0$$.

**(c)** Because $$f_{\rho}$$ is *linear* in the output weights, $$\partial f/\partial c_{i}$$ contains no $$c_{i}$$; the only route by which $$c_{i}$$ influences $$\dot c_{i}$$ is through the mean field $$\Delta^{\mu}$$ — i.e. through the population average, weighted by $$1/N$$. This linearity is also what makes the loss a quadratic (rather than higher-order) polynomial in each particle, i.e. what limits the interaction to be pairwise.

:::

\#### 5.2.4 From particles to measures: the continuity equation

We now pass to the $$N\to\infty$$ limit, in distinct steps.

*Step 1: rewrite the $$N$$ coupled ODEs as one equation for the empirical measure.* (This remains exact at finite $$N$$.) Suppose particles move deterministically with some velocity field, $$\dot\theta_{t} = v_{t}(\theta_{t})$$, and let $$\rho_{t}$$ denote the law of one such particle.

The expectation of a smooth test function $$g$$ obeys

$$
\begin{aligned}\frac{d}{dt}\int g\,d\rho_{t}&= \frac{d}{dt}\,{\mathbb{E}}\big[g(\theta_{t})\big] = {\mathbb{E}}\big[\nabla g(\theta_{t})\cdot v_{t}(\theta_{t})\big] \\&= \int \nabla g\cdot v_{t}\, d\rho_{t} = -\int g\;\nabla\!\cdot\!(\rho_{t} v_{t})\,,\end{aligned}
$$

integrating by parts in the last step. Since $$g$$ was arbitrary,

$$
\partial_{t}\rho_{t} + \nabla\!\cdot\!\big(\rho_{t}\, v_{t}\big) = 0\,.
$$

This is known as the *continuity equation*, and it simply expresses conservation of probability. Applied to our system, with $$v_{t} = -\tilde\eta\,\nabla\Psi(\cdot\,;\rho_{N,t})$$ from (5.16), the empirical measure satisfies (weakly, since it is a sum of delta functions)

$$
\partial_{t} \rho_{N,t}= \tilde\eta\,\nabla\!\cdot\!\Big(\rho_{N,t}\,\nabla_{\theta} \Psi\big(\theta;\rho_{N,t}\big)\Big)\,.
$$

An important consequence of the mean-field ($$1/N$$, all-to-all) coupling here is that (5.19) is a closed equation in $$\rho_{N}$$.

*Step 2: the limit.* At finite $$N$$, $$\rho_{N,t}$$ is a random, atomic measure. (Atomic means it's a sum of delta functions; it's random due to random initialization.) As $$N\to\infty$$ with i.i.d. initialization $$\theta_{i}\sim\rho_{0}$$, the law of large numbers suggests — and the theorems of (Mei et al. 2018; Chizat & Bach 2018; Rotskoff & Vanden-Eijnden 2022; Sirignano & Spiliopoulos 2020) confirm — that $$\rho_{N,t}$$ converges (weakly) to $$\rho_{t}$$, a deterministic curve of smooth probability measures solving the limiting PDE

$$
\partial_{t}\rho_{t} = \tilde\eta\, \nabla\!\cdot\!\Big(\rho_{t}\,\nabla_{\theta}\big(V + U*\rho_{t}\big)\Big)\,,\quad \text{with}\;\;\; (U*\rho)(\theta):=\int U(\theta,\theta')\,d\rho(\theta')\,.
$$

There are quantitative $$O(1/\sqrt{N})$$ error bounds at any fixed time horizon.

\#### 5.2.5 The McKean–Vlasov equation and self-consistency

In this context, the analogue of the Curie–Weiss self-consistency (5.2), namely $$m=\tanh(\beta(m+B))$$, is called the McKean–Vlasov equation. To get it, focus on a single representative neuron $$\theta_{i}$$. As $$N\to \infty$$, we can replace the force on it by the ensemble average:

$$
\dot{\bar\theta}_{t} = -\tilde\eta\,\nabla_{\theta}\Psi\big(\bar\theta_{t};\rho_{t}\big)\,, \qquad\text{subject to}\qquad \rho_{t} = \mathrm{Law}(\bar\theta_{t})\,.
$$

The constraint $$\rho_{t} = \mathrm{Law}(\bar\theta_{t})$$ is the entire content of the equation: the particle is driven by a field built from a distribution, and that distribution is *its own law*.

(Probabilists call (5.21) a *nonlinear* Markov process, nonlinear not in $$\theta$$ but in the law.) The McKean–Vlasov equation is equivalent to the continuity equation; the particle trajectories of (5.21) are the characteristic curves of the PDE (5.20).

We remark on a few structural features:

- *Propagation of chaos.* Since neurons interact only through a quantity ($$\rho_{N}$$, equivalently $$f_{\rho_N}$$) that becomes deterministic as $$N\to\infty$$, they become asymptotically *independent*: any fixed collection of $$k$$ neurons converges to $$k$$ i.i.d. copies of (5.21), with cross-neuron correlations of size $$O(1/N)$$. Thus, independence at initialization *propagates* instead of degrading (Sznitman 1991).
- *Gradient-flow structure.* Define the $$N\to\infty$$ loss as a functional of the measure, $${{\mathcal L}}[\rho] = \frac{1}{2}\sum_{\mu} (f_{\rho}(x^{\mu})-y^{\mu})^{2}$$. Since $$f_{\rho}$$ is linear in $$\rho$$, this functional is convex in $$\rho$$.

This ultimately leads to global-convergence theorems. For example, it was shown in (Chizat & Bach 2018) that for homogeneous activations (e.g. ReLU), if training converges at all, it converges to a *global* minimizer of the convex functional $${{\mathcal L}}[\rho]$$.
- *Temperature.* If one trains instead with the Langevin dynamics of Section 2.1, Eqn. (2.6), at temperature $$T=\beta^{-1}$$, one finds convergence to a stationary distribution that satisfies (Mei et al. 2018)

$$
\rho_{\infty}(\theta) \;\propto\; e^{\textstyle-\beta\,\Psi(\theta;\rho_\infty)}\,.
$$

This is another version of the "$$m=\tanh(\beta(m+B))$$" consistency condition, now for noisy training.

![Mean-field training for a example: , trained by the rescaled gradient flow (5.15) on samples of the two-neuron teacher ; is rescaled training time. Left: the empirical measure in the plane for (dots, colored by time; thin gray lines trace of the particle trajectories), drawn over the density of an run at (shaded contours), standing in for the limiting measure . Individual neurons move order-one distances, and the measure condenses onto one-dimensional filaments — the configurations realizing the teacher. (The point symmetry reflects the oddness of .) Right: the mean field itself, , converging to the target (dashed; circles mark the training data).](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-mf-transport-a3a32282.png)

Mean-field training for a $$d=1$$ example: $$f_{\rho}(x)=\frac{1}{N}\sum_{i}c_{i}\tanh(a_{i}x)$$, trained by the rescaled gradient flow (5.15) on $$n=30$$ samples of the two-neuron teacher $$y(x)=2\tanh(3x)-\tfrac{3}{2}\tanh(x)$$; $$\tau=\tilde\eta\, t$$ is rescaled training time. *Left:* the empirical measure $$\rho_{N,t}$$ in the $$(a,c)$$ plane for $$N=300$$ (dots, colored by time; thin gray lines trace $$40$$ of the particle trajectories), drawn over the density of an $$N=30{,}000$$ run at $$\tau=20$$ (shaded contours), standing in for the limiting measure $$\rho_{t}$$. Individual neurons move order-one distances, and the measure condenses onto one-dimensional filaments — the configurations realizing the teacher. (The point symmetry $$(a,c)\mapsto(-a,-c)$$ reflects the oddness of $$\tanh$$.) *Right:* the mean field itself, $$f_{\rho_t}(x)$$, converging to the target (dashed; circles mark the training data).

How would one actually *solve* the self-consistent system (5.21)? The same way one solves (5.2) (Exercise 5.1): freeze a guessed environment $$(\rho_{t})$$, solve the now-ordinary ODE, compute the law of the solution, feed it back, iterate. On short time horizons this map is a contraction, which is how existence, uniqueness, and propagation of chaos are all proven in one stroke (Sznitman 1991). Alternatively, solve the PDE (5.20) on a grid, which is feasible (only) for small $$d$$.

In Figure 6 we instead solve the system by simply training a network with $$d=1$$. In the left panel, each dot is a neuron. Training is a flow of the cloud of neurons, and the cloud condenses onto the low-dimensional structures in weight space that realize the target — learning its features. Exercise 5.3 reproduces this figure, and sets it beside the frozen cloud of the lazy network.

:::callout {title="Exercise" tone="amber"}
**Exercise 5.3 (★) (Numerics: the mean-field network (lab)).** Continue the lab of Exercise 4.4: same data, same teacher $$y(x) = 2\tanh(3x)-\frac{3}{2}\tanh(x)$$, same student (4.40), but now with the mean-field exponent $$\gamma = 1$$ and the rescaled updates (5.15),

$$
\begin{aligned}c_{i}&\mathrel{-}= \Delta\tau\sum_{\mu}\Delta^{\mu}\tanh(a_{i}x^{\mu})\,, \\ a_{i}&\mathrel{-}= \Delta\tau\,c_{i}\sum_{\mu}\Delta^{\mu}\big(1-\tanh^{2}(a_{i}x^{\mu})\big)x^{\mu}\,,\end{aligned}
$$

with $$\Delta\tau = 5\times10^{-4}$$ for $$4\times10^{4}$$ steps, so that the rescaled time $$\tau = \tilde\eta\, t$$ runs to $$20$$. Note that there is no $$1/N$$ in these updates: that is the required $$O(N)$$ learning rate (5.14), already built in ($$\eta = N\,\Delta\tau$$). Monitor the NTK (4.41) with $$\gamma=1$$.

**(a)** *It fits.* Train and check that the loss becomes small, if more slowly in rescaled time than the lazy run.

**(b)** *Initialization.* Over about $$200$$ seeds, histogram $$f_{0}(x)$$ at $$x=1$$ for several $$N$$: the distribution collapses to $$0$$ with width $$\sim1/\sqrt{N}$$. Check the scaling.

**(c)** *The kernel moves.* For $$N\in\{30,100,300,1000\}$$, record $$\|\Theta_{\rm end}-\Theta_{0}\|/\|\Theta_{0}\|$$ and plot it together with the lazy curve of Exercise 4.4(c): one plot, two curves, the whole dichotomy.

**(d)** *Watch the particles.* Scatter-plot the neuron cloud $$(a_{i},c_{i})$$ at $$\tau\approx0,\,0.4,\,2,\,20$$ for both runs. Lazy: the cloud is static (each weight moves $$O(1/\sqrt{N})$$). Mean-field: the cloud transports and condenses onto thin filaments, the configurations realizing the teacher, as in Figure 6. Repeat at $$N=3000$$: the pattern is the same, because you are looking at a deterministic limiting measure.

**(e)** *Now play.* The starter teacher is itself a two-neuron $$\tanh$$ network, so the student's features can align *exactly* with the teacher's. Is that feature learning, or feature copying? Try teachers outside the model class and watch what the cloud does instead: $$y(x) = \sin(2x)$$; $$y(x) = |x|-1$$; a ReLU student on the $$\tanh$$ teacher (and vice versa); or move to $$d=2$$ with $$y(x) = \tanh(x_{1}+x_{2})$$ and plot the cloud of directions $$a_{i}/|a_{i}|$$. Which aspects of (c)–(d) are universal, and which were special to the aligned case?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Reference results (single seeds).

**(a)** Final loss $$\sim5\times10^{-3}$$ at $$\tau=20$$ and still slowly falling; the mean-field run is measured in rescaled time, so run longer to go lower.

**(b)** At $$x=1$$, $$f_{0}\sim{{\mathcal N}}(0,O(1/N))$$, with standard deviation falling like $$1/\sqrt{N}$$ across $$N$$: the Gaussian process of Section 3 survives only as the $$O(1/\sqrt{N})$$ fluctuation around zero.

**(c)** Measured $$\|\Delta\Theta\|/\|\Theta_{0}\|\approx1.7,\,0.8,\,0.7,\,0.9$$ at $$N=30,100,300,1000$$: order one, with no decay, against the decaying lazy curve. Use the same $$\Theta$$ formula with the appropriate $$\gamma$$ in both runs.

**(d)** The mean-field cloud reproduces Figure 6: neurons stream along order-one trajectories and pile onto one-dimensional filaments through $$(a,c)\approx$$ (teacher directions, matched output weights), with the point symmetry $$(a,c)\to(-a,-c)$$ from the oddness of $$\tanh$$. The lazy cloud is visually identical at $$\tau=0$$ and $$\tau=20$$ (displacements $$\sim1/\sqrt{N}$$).

**(e)** For $$y=\sin(2x)$$ or $$|x|-1$$ the loss still falls (more slowly), and the cloud condenses onto *different*, task-shaped structures, with more filaments spread over a range of slopes $$a$$, since no finite set of teacher neurons exists to copy; the kernel still moves by $$O(1)$$. That is the cleaner demonstration that mean-field training *builds* features rather than merely locating the teacher's. Mismatched activations behave similarly. The lazy runs, by contrast, change in only one way, the quality of the fit (the random features either happen to span the target well or do not); the kernel and the cloud never adapt.

:::

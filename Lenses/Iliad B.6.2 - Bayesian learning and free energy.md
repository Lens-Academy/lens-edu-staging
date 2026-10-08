---
id: '46105665-15b2-4232-9149-f5bc38981906'
title: "B.6.2 Bayesian learning and free energy"
tldr: "The Bayesian model of learning as a posterior with inverse temperature, why exp(-loss) is a likelihood, and partition functions, free energy and cumulants."
summary_for_tutor: "Sections 2, 2.1-2.3 of Iliad worksheet B.6 Physics of Deep Learning. Covers the Bayesian posterior p_beta proportional to exp(-beta L) times the prior, the role of n*beta, Langevin dynamics vs SGD, MSE and cross-entropy as negative log-likelihoods, the statistical mechanics dictionary, partition function Z, free energy F=-log Z, sources and cumulants, and quenched vs annealed averages. Contains Exercise 2.1 (partition functions, sources, cumulants) with a collapsed solution. Keep the notation beta, L, Z, F, phi=F/N, kappa_p. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## 2. Statistical mechanics of learning

There is a large and well-developed body of work applying physics to learning theory. Much of it consists of *statistical mechanics* applied to *Bayesian learning*. The classic textbook is Engel and Van den Broeck (Engel & Van den Broeck 2001); modern reviews include (Zdeborov'a & Krzakala 2016; Bahri et al. 2020); and an excellent reference for the physics itself is David Tong's lecture course on statistical field theory (Tong 2012), which we follow closely in Sections 2.4–2.5.

In this section we focus on the Bayesian model of learning. We first recall what it is, why it is a reasonable idealization of how networks are actually trained, and why the exponential of a loss function deserves to be called a likelihood (Sections 2.1–2.2). We then switch to physics. We introduce partition functions, free energies, and cumulants (Section 2.3), and work through the Ising model in the mean-field approximation, building up to first- and second-order phase transitions (Sections 2.4–2.5). The payoff is a learning problem that is the Ising magnet's twin, the Ising perceptron, which shows a first-order transition to perfect generalization; it is left as a self-contained walk-through exercise (Section 2.6). Section 2.7 is a translation guide for readers arriving from quantum field theory. The ideas introduced here — order parameters, free energies, saddle points, quenched averages, phase transitions — will keep returning throughout the notes.

\### 2.1 The Bayesian model of learning

Consider a network $$f_{\theta}$$ with parameters $$\theta\in{\mathbb{R}}^{P}$$, trained on $$n$$ samples $$(x^{\mu},y^{\mu})_{\mu=1}^{n}$$ to minimize a loss

$$
{{\mathcal L}}(\theta) = \sum_{\mu=1}^{n} \ell\big(f_{\theta}(x^{\mu}),y^{\mu}\big)\,,
$$

a sum over samples of a per-sample loss $$\ell$$. In practice, the network is initialized at random, $$\theta_{0}\sim\pi(\theta)$$, and trained with some version of gradient descent,

$$
\Delta\theta \approx -\eta\,\nabla_{\theta}{{\mathcal L}}(\theta)\,.
$$

A common idealization of this process, and the one this section is about, is *Bayesian learning*. It says that after training, the parameters should be regarded as drawn from the posterior distribution

$$
p_{\beta}(\theta) = \frac{1}{Z}\,e^{-\beta\,{{\mathcal L}}(\theta)}\,\pi(\theta)\,,\qquad Z = \int d\theta\, e^{-\beta\,{{\mathcal L}}(\theta)}\,\pi(\theta)\,.
$$

Here the initialization distribution $$\pi(\theta)$$ plays the role of the Bayesian *prior*, and $$e^{-\beta{{\mathcal L}}(\theta)}$$ is interpreted as the *likelihood* of the training data given the parameters $$\theta$$ (Section 2.2 explains why this is reasonable). The positive constant $$\beta$$, the *inverse temperature*, controls how strongly the data constrain the parameters. We will see in a moment that it can be read as a rough measure of how much training has been done.

*An interpretation of $$\beta$$.* It is convenient to write the loss as $$n$$ times an average over samples,

$$
{{\mathcal L}}(\theta) = n\,L_{n}(\theta)\,,\qquad L_{n}(\theta) := \frac{1}{n}\sum_{\mu=1}^{n}\ell\big(f_{\theta}(x^{\mu}),y^{\mu}\big)\,.
$$

The *empirical loss* $$L_{n}$$ stays finite as $$n\to\infty$$, converging to the *population loss* $$L(\theta) := {\mathbb{E}}_{(x,y)}\,\ell(f_{\theta}(x),y)$$, the expectation over the true data distribution. Thus for large $$n$$ the posterior is

$$
p_{\beta}(\theta) \;\propto\; e^{-\,n\beta\,L(\theta)}\,\pi(\theta)\,,
$$

and the sample size $$n$$ always accompanies the inverse temperature, in the combination $$n\beta$$. Increasing the number of samples is the same as lowering the temperature. If, moreover, samples are drawn fresh at each training step, then $$n$$ is also a rough measure of training time. Altogether: *more data $$=$$ more training $$=$$ larger $$n\beta$$ $$=$$ colder*. We will often write $$e^{-\beta L}$$ for short, but it is worth remembering that the effective $$\beta$$ grows with $$n$$.

*Bayes vs. gradient descent.* We do not train networks by sampling from (2.3); we train them by gradient descent. Why, then, is the Bayesian model a useful idealization? There are two connections.

The first is heuristic: the analogy just described, $$n\to\infty$$ (more samples, longer training) $$\leftrightarrow$$ $$\beta\to\infty$$ (lower temperature). As we will see, sweeping a parameter like $$\beta$$ can take a system through phase transitions, and the analogy predicts that training can do the same. It is only an analogy. In particular, when a system is driven *dynamically* through a first-order transition, the transition is delayed by *hysteresis* (Section 2.5), so timing predictions from the Bayesian model should be treated with care. A genuinely dynamical formalism for training, the MSRJD path integral, appears in Section 6.

The second connection is exact, and is what makes the Bayesian model testable in practice. Replace the batch noise of SGD by constant, isotropic Gaussian noise; the result is called *Langevin dynamics*:

$$
\begin{array}{l|l}\text{discrete optimizer} & \text{continuous (S)DE} \\\hline \text{SGD}:\; \Delta\theta = -\eta(\nabla_\theta {{\mathcal L}}+ \text{batch noise}) & \dot\theta = -\eta\nabla_\theta {{\mathcal L}}+ \frac{\eta}{\sqrt{B}} \Sigma(\theta)^{\frac{1}{2}} d\xi\\ \text{GD}:\; \Delta\theta=-\eta\,\nabla_\theta {{\mathcal L}} & \dot\theta = -\eta\nabla_\theta {{\mathcal L}} \\ \text{LD}:\;\Delta\theta = -\eta\,\nabla_\theta {{\mathcal L}} + \sqrt{2\eta T}\, \xi & \dot\theta = -\eta\nabla_\theta {{\mathcal L}} + \sqrt{2\eta T}\,d\xi\end{array}
$$

Here $$\xi$$ is Gaussian noise with mean $$0$$ and covariance $$I$$, $$\eta$$ is the learning rate, and $$T$$ is a parameter called the *temperature* (or diffusion constant). Each discrete algorithm on the left has a continuous-time limit on the right, obtained by shrinking the step size and scaling up the number of steps: gradient descent becomes *gradient flow*, and Langevin dynamics becomes the *Langevin equation*, a stochastic differential equation. The key fact is that if one starts from any reasonable distribution of parameters and evolves with the Langevin equation (for a sufficiently nice $${{\mathcal L}}$$), the distribution converges at late times to the Gibbs distribution

$$
p(\theta) = \frac{1}{Z}\,e^{-\beta{{\mathcal L}}(\theta)}\,,\qquad \beta = 1/T\,.
$$

(See (Tong 2012, Chapter 3) for a physics-focused discussion of this convergence.) A prior can be included by training on the modified loss $${{\mathcal L}}(\theta) - \beta^{-1}\log\pi(\theta)$$, which reproduces (2.3). Thus one can *engineer* the Bayesian posterior by Langevin training, and this is how theoretical predictions derived from (2.3) are usually tested. Note that the Langevin route gives a different Bayes-to-gradient connection from the first: here training time $$t\to\infty$$ at fixed $$T$$ gives the posterior at $$\beta = 1/T$$, while $$T\to 0$$ at fixed $$t$$ gives gradient flow.

:::callout {title="Note" tone="blue"}

**Remark.** SGD itself is more complicated than Langevin dynamics. The covariance $$\Sigma(\theta)$$ of its effective noise depends on the position in the loss landscape, and at late times SGD need not converge to any stationary distribution. Despite many qualitative and empirical similarities between Bayesian learning and SGD/Adam training, the precise relation between them remains an open problem. We will compare the two repeatedly: for wide networks in Section 4 (gradient flow) versus Section 4.6 (Bayesian); for toy models of grokking in Section 5 (Rubin et al. 2024); and, for toy models of superposition (Elhage et al. 2022) through the lens of singular learning theory, in (Chen et al. 2023).

:::

\### 2.2 Why the exponential of a loss is a likelihood

The Bayesian model treats $$e^{-\beta{{\mathcal L}}(\theta)}$$ as the probability of the training data given the parameters. For the loss functions actually used in deep learning, this is not a metaphor: the losses were *designed* as negative log-likelihoods, so that minimizing the loss is maximum-likelihood estimation. Two examples cover most of practice.

*Mean squared error.* Suppose the labels are the network's output plus Gaussian noise, $$y = f_{\theta}(x) + \epsilon$$ with $$\epsilon\sim{{\mathcal N}}(0,\sigma^{2})$$. Then the probability density of a label given the input and the parameters is

$$
p(y\,|\,x,\theta) = \frac{1}{\sqrt{2\pi\sigma^{2}}}\,\exp\Big[-\frac{1}{2\sigma^{2}}\big(y-f_{\theta}(x)\big)^{2}\Big]\,,
$$

and for $$n$$ independent samples,

$$
\prod_{\mu=1}^{n} p(y^{\mu}\,|\,x^{\mu},\theta) \;\propto\; e^{-\beta\,{{\mathcal L}}(\theta)}\,,\qquad {{\mathcal L}}(\theta) = \frac{1}{2}\sum_{\mu=1}^{n}\big(f_{\theta}(x^{\mu})-y^{\mu}\big)^{2}\,,\quad \beta = \frac{1}{\sigma^{2}}\,.
$$

The MSE loss is the negative log-likelihood of a Gaussian noise model, and the inverse temperature is the inverse noise variance. Noisier labels mean a hotter posterior, which constrains the parameters less.

*Cross-entropy.* For classification, the network outputs a probability distribution $$p_{\theta}(y\,|\,x)$$ over $$K$$ classes, typically the softmax of its $$K$$ output values. The cross-entropy loss is $$\ell = -\log p_{\theta}(y\,|\,x)$$, so that

$$
\prod_{\mu=1}^{n} p_{\theta}(y^{\mu}\,|\,x^{\mu}) \;=\; e^{-{{\mathcal L}}(\theta)}
$$

*exactly*, with $$\beta = 1$$: the exponential of the cross-entropy loss *is* the likelihood, with no noise model to choose. The same is true of the next-token loss of a language model, which is exactly the log-probability the model assigns to the training corpus.

*The general pattern.* Whenever a loss is a negative log-likelihood, $$e^{-{{\mathcal L}}}$$ is the likelihood and (2.3) at $$\beta=1$$ is the textbook Bayesian posterior. A value $$\beta\neq 1$$ gives a *tempered* posterior. It arises naturally when the noise level is not known (as in (2.9)), and it is also a useful theoretical knob: as the interpretation of $$n\beta$$ above shows, temperature and sample size are interchangeable in the Bayesian model. There is also a useful limiting case. Some losses are hard constraints, $$\ell = 0$$ if the prediction is right and $$\ell=\infty$$ if it is wrong. Then $$e^{-\ell}$$ is a step function, the posterior is uniform on the parameters that fit every training sample, and no $$\beta$$ appears at all. This is the *zero-temperature* limit, and it is the setting of the Ising perceptron in Section 2.6.

\### 2.3 Partition functions, free energy, and cumulants

The Bayesian posterior (2.3) looks exactly like a *thermal* system in equilibrium with a heat bath, the basic object of statistical mechanics. The dictionary is:

| **Bayesian learning** | **statistical mechanics** |
| --- | --- |
| parameters $$\theta\in{\mathbb{R}}^{P}$$ | microscopic state of a system |
|  | (*e.g.* the spins of $$P$$ electrons) |
| loss $${{\mathcal L}}(\theta)$$ | energy $$E(\theta)$$, or Euclidean action $$S(\theta)$$ |
| posterior $$p(\theta)\propto e^{-\beta{{\mathcal L}}(\theta)}$$ | Boltzmann distribution at temperature $$T=1/\beta$$ |
| number of samples $$n$$, or training time | inverse temperature $$\beta$$ |
| #parameters $$P$$ | #degrees of freedom $$N$$ |

To include the prior $$\pi(\theta)$$, simply redefine the energy as $$E(\theta) = {{\mathcal L}}(\theta) - \beta^{-1}\log\pi(\theta)$$, so that $$e^{-\beta E}= e^{-\beta{{\mathcal L}}}\pi$$. In what follows we write $$E(\theta)$$ for whatever sits in the exponent, and $$N$$ for the number of degrees of freedom, as physicists do; for a network, $$N=P$$.

*The thermodynamic limit.* Statistical mechanics is about systems with very many degrees of freedom, and one studies their behavior as $$N\to\infty$$: the *thermodynamic limit*. In this limit one distinguishes *extensive* quantities, which grow in proportion to $$N$$ (the total energy of a gas), from *intensive* ones, which stay finite (the temperature, or the energy per particle). Both notions transfer directly to learning: with $$P$$ parameters and $$n$$ samples, the loss (2.1) is extensive in $$n$$ and the empirical loss $$L_{n}$$ is intensive. Many of the approximations in these notes are thermodynamic limits of some kind, sending the number of parameters, the width, or the number of samples to infinity.

*Partition function and free energy.* The normalization constant in (2.3),

$$
Z(\beta) = \int d\theta\, e^{-\beta E(\theta)}\,,
$$

is called the *partition function*. In Bayesian terms it is the marginal likelihood of the data. It depends on $$\beta$$ and on any other hyperparameters of the problem. Its logarithm defines the *free energy*[^1] and the free energy *density*,

$$
F(\beta) := -\log Z(\beta)\,,\qquad \varphi := \frac{F}{N}\,.
$$

There are three reasons to care about $$F$$ rather than $$Z$$. First, $$F$$ is extensive and $$\varphi$$ intensive: the free energy density has a limit as $$N\to\infty$$, while $$Z$$ itself is exponentially large or small. Second, "$$F$$ is minimized": at large $$N$$ the integral (2.11) is dominated by the regions of parameter space with the smallest local free energy, so the system's macroscopic state is found by minimizing $$F$$. Section 2.4 makes this precise. Third, derivatives of $$F$$ compute expectation values, as follows.

*Sources and cumulants.* Suppose we care about the expectation values of some *observables* $${{\mathcal O}}_{i}(\theta)$$, functions of the parameters. Add *source terms* $$J^{i}$$ to the exponent,

$$
Z(\beta,J) = \int d\theta\; e^{-\beta E(\theta) + \sum_i J^i\,{{\mathcal O}}_i(\theta)}\,,\qquad F(\beta,J) = -\log Z(\beta,J)\,.
$$

Differentiating under the integral,

$$
{\mathbb{E}}({{\mathcal O}}_{i}) = -\frac{\partial F}{\partial J^{i}}\bigg|_{J=0}\,,\qquad \mathrm{Cov}({{\mathcal O}}_{i},{{\mathcal O}}_{j}) = -\frac{\partial^{2} F}{\partial J^{i}\partial J^{j}}\bigg|_{J=0}\,,
$$

and in general the $$p$$-th derivative is the $$p$$-th *cumulant*,

$$
\kappa_{p}({{\mathcal O}}_{i_1},\ldots,{{\mathcal O}}_{i_p}) = -\frac{\partial^{p} F}{\partial J^{i_1}\cdots\partial J^{i_p}}\bigg|_{J=0}\,:
$$

the mean, the covariance, the third central moment, and from $$p=4$$ on, combinations of moments that vanish for Gaussian variables. The sourced free energy is the generating function of cumulants. Cumulants will return in field-theory clothing in Section 3.3, where they measure how far a network at initialization is from a Gaussian process.

If the only observable we care about is the energy itself, no source is needed: $$\beta$$ already couples to $$E$$, and

$$
{\mathbb{E}}(E) = \frac{\partial F}{\partial \beta}\,,\qquad \mathrm{Var}(E) = -\frac{\partial^{2} F}{\partial\beta^{2}}\,,\qquad \kappa_{3}(E) = \frac{\partial^{3} F}{\partial \beta^{3}}\,,\;\ldots
$$

We will meet these derivatives again shortly: discontinuities in them are how phase transitions are defined.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.1 (★) (Partition functions, sources, and cumulants).** Take a Boltzmann distribution $$p_{\beta}(\theta)\propto e^{-\beta E(\theta)}$$, an observable $${{\mathcal O}}(\theta)$$, and the sourced partition function $$Z(\beta,J) = \int d\theta\, e^{-\beta E(\theta)+J{{\mathcal O}}(\theta)}$$, with $$F = -\log Z$$. All expectations are in $$p_{\beta}$$, that is, at $$J=0$$.

**(a)** Show that $${\mathbb{E}}({{\mathcal O}}) = -\partial_{J}F|_{J=0}$$ and $$\mathrm{Var}({{\mathcal O}}) = -\partial_{J}^{2}F|_{J=0}$$.

**(b)** The third cumulant is defined by continuing the pattern, $$\kappa_{3}({{\mathcal O}}) := -\partial_{J}^{3}F|_{J=0}$$. Compute it in terms of the moments $${\mathbb{E}}({{\mathcal O}}^{3})$$, $${\mathbb{E}}({{\mathcal O}}^{2})$$, $${\mathbb{E}}({{\mathcal O}})$$, and show that it equals the third *centered* moment $${\mathbb{E}}[({{\mathcal O}}-{\mathbb{E}}{{\mathcal O}})^{3}]$$.

**(c)** Show that for a Gaussian $${{\mathcal O}}$$, $$\log Z(J)$$ is exactly quadratic in $$J$$, so that all cumulants with $$p\geq 3$$ vanish. Compute $$\kappa_{4}$$ in terms of centered moments and check that it is *not* the fourth centered moment. (Moral: cumulants measure the failure of higher moments to be determined by lower ones in the Gaussian pattern.)

**(d)** Verify (2.16).
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Differentiating under the integral, $$\partial_{J}\log Z = \frac{1}{Z}\int d\theta\,{{\mathcal O}}\,e^{-\beta E+J{{\mathcal O}}}= {\mathbb{E}}_{J}({{\mathcal O}})$$, which at $$J=0$$ is $${\mathbb{E}}({{\mathcal O}})$$; since $$F=-\log Z$$, this is $$-\partial_{J}F|_{0}$$. Once more, $$\partial_{J}^{2}\log Z = {\mathbb{E}}_{J}({{\mathcal O}}^{2})-{\mathbb{E}}_{J}({{\mathcal O}})^{2} = \mathrm{Var}_{J}({{\mathcal O}})$$.

**(b)** Using $$\partial_{J}{\mathbb{E}}_{J}({{\mathcal O}}^{k}) = {\mathbb{E}}_{J}({{\mathcal O}}^{k+1}) - {\mathbb{E}}_{J}({{\mathcal O}}^{k}){\mathbb{E}}_{J}({{\mathcal O}})$$ on $$\partial_{J}^{2}\log Z = {\mathbb{E}}_{J}({{\mathcal O}}^{2})-{\mathbb{E}}_{J}({{\mathcal O}})^{2}$$ gives $$\kappa_{3} = {\mathbb{E}}({{\mathcal O}}^{3}) - 3{\mathbb{E}}({{\mathcal O}}^{2}){\mathbb{E}}({{\mathcal O}}) + 2{\mathbb{E}}({{\mathcal O}})^{3}$$. Expanding $${\mathbb{E}}[({{\mathcal O}}-{\mathbb{E}}{{\mathcal O}})^{3}] = {\mathbb{E}}({{\mathcal O}}^{3}) - 3{\mathbb{E}}({{\mathcal O}}^{2}){\mathbb{E}}({{\mathcal O}}) + 3{\mathbb{E}}({{\mathcal O}}){\mathbb{E}}({{\mathcal O}})^{2} - {\mathbb{E}}({{\mathcal O}})^{3}$$ gives the same expression.

**(c)** For $${{\mathcal O}}\sim{{\mathcal N}}(\mu,\sigma^{2})$$ (or more generally when $${{\mathcal O}}$$ is Gaussian under $$p_{\beta}$$), $${\mathbb{E}}(e^{J{{\mathcal O}}}) = e^{J\mu+J^2\sigma^2/2}$$, so $$\log Z(J) = \log Z(0) + J\mu + \frac{1}{2}J^{2}\sigma^{2}$$ is quadratic and every derivative beyond the second vanishes. One more derivative of the pattern in (b), with $$\bar{{\mathcal O}} := {{\mathcal O}} - {\mathbb{E}}{{\mathcal O}}$$, gives $$\kappa_{4} = {\mathbb{E}}(\bar{{\mathcal O}}^{4}) - 3\,{\mathbb{E}}(\bar{{\mathcal O}}^{2})^{2}$$; for a Gaussian $${\mathbb{E}}(\bar{{\mathcal O}}^{4}) = 3\sigma^{4}$$, so $$\kappa_{4} = 0$$ while the fourth centered moment is not.

**(d)** $$\partial_{\beta}\log Z = -\frac{1}{Z}\int E\,e^{-\beta E}= -{\mathbb{E}}(E)$$, so $$\partial_{\beta} F = {\mathbb{E}}(E)$$; $$\partial_{\beta}^{2}\log Z = {\mathbb{E}}(E^{2})-{\mathbb{E}}(E)^{2}$$, so $$-\partial_{\beta}^{2}F = \mathrm{Var}(E)$$; and $$\partial_{\beta}^{3}\log Z = -\kappa_{3}(E)$$ by the same computation as (b) with $$J\to-\beta$$, so $$\kappa_{3}(E) = \partial_{\beta}^{3}F$$.

:::

*Quenched averages.* In a learning problem there is a second source of randomness besides the posterior: the training set itself. Quantities like the free energy depend on which $$n$$ samples were drawn, and at large $$n$$ one expects them to concentrate around their average over draws. Physicists call randomness that is fixed before the system equilibrates *quenched disorder*, by analogy with impurities frozen into an alloy when it is quenched in water; the training data are quenched disorder for the posterior. The *quenched free energy* is

$$
{\mathbb{E}}_{\rm data}\big[F\big] = -\,{\mathbb{E}}_{\rm data}\big[\log Z\big]\,,
$$

and it is the free energy, not the partition function, that should be averaged, because it is the free energy that is extensive and whose derivatives give expectation values. Averaging $$\log Z$$ is usually hard, and the *annealed approximation* swaps the order,

$$
{\mathbb{E}}_{\rm data}\log Z \;\approx\; \log{\mathbb{E}}_{\rm data}Z\,,
$$

which is an upper bound by Jensen's inequality and often a good approximation. We will use it in Section 2.6. The exact treatment goes through the *replica method*, sketched in Appendix A; the classic reference is (Engel & Van den Broeck 2001).

[^1]: A physicist's free energy is $$-\beta^{-1}\log Z$$; we absorb the factor of $$\beta$$ throughout, so that $$F$$ is dimensionless.

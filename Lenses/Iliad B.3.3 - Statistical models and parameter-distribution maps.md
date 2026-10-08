---
id: '58ce8d41-8e79-4ace-b19c-481298dfa6c0'
title: "B.3.3 Statistical models and parameter-distribution maps"
tldr: "Moves from functions to conditional distributions: parameter-distribution maps, noise models, and why maximum likelihood matches minimising common losses."
summary_for_tutor: "This is Section 1.3 of worksheet B.3 (singular learning theory). It defines the parameter-distribution map Psi with densities p(y|x,w), the Gaussian noise model, likelihood and negative log-likelihood. It contains Exercises 1.3 (maximum likelihood as MSE minimisation), 1.4 (cross entropy) and 1.5 (general loss with partition function Z(x,w)) with collapsed solutions, and a remark on negative log-likelihood loss. Keep the notation Psi, p_w, X_n, Y_n. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Kai Ogden (University of Oxford)
  - Matthew Farrugia-Roberts (University of Oxford)
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/singular-learning-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 1.3 Statistical models and parameter–distribution maps

The previous sections introduce neural networks and supervised deep learning within a framework of function approximation. An alternative approach is to view supervised learning as statistical inference, and particularly Bayesian inference. This statistical framework is commonly used within the SLT literature, and we will encounter it within this tutorial.

The first step to upgrading our framework is to move from talking about functions to talking about conditional distributions. For each neural network, we should be able to determine not just the output corresponding to each input, but a probability density measuring how likely each output is given each input.

Formally, let $${\mathcal{D}} \subseteq \Delta({\mathcal{Y}})^{{\mathcal{X}}}$$ represent a class of conditional distributions over $${\mathcal{Y}}$$. A distributional neural network architecture comprises a **parameter–distribution map** $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$. It is sometimes convenient to refer to the conditional distribution $$\Psi(w) : {\mathcal{X}} \to \Delta({\mathcal{Y}})$$ using the notation $$p_{w} : {\mathcal{X}} \to \Delta({\mathcal{Y}})$$. The probability mass/density of a given output $$y \in {\mathcal{Y}}$$ conditional on a given input $$x \in {\mathcal{X}}$$ is typically denoted either $$p_{w}(y \mid x)$$ or $$p(y \mid x, w)$$.

Sometimes, defining a parameter–distribution map is simply a re-framing. For example, in image classification, our output space $${\mathcal{Y}}$$ was a space of distributions over image classes. Let $${\mathcal{C}}$$ represent the underlying class space, then $${\mathcal{Y}} = \Delta({\mathcal{C}})$$ and we can view our parameter–function map $$\Phi : {\mathcal{W}} \to {\mathcal{F}}$$ as a parameter–distribution map $$\Psi : {\mathcal{W}} \to {\mathcal{D}}$$ with $${\mathcal{D}} = {\mathcal{F}} \subseteq {\mathcal{Y}}^{{\mathcal{X}}} = \Delta({\mathcal{C}})^{{\mathcal{X}}}$$.

In other cases, we can easily construct a parameter–distribution map from a parameter–function map by introducing a **noise model**. For example, in regression with an output space $${\mathcal{Y}} = {\mathbb{R}}^{m}$$, given a parameter–function map $$w \mapsto f_{w}$$ we can define a parameter–distribution map $$\Psi : {\mathcal{W}} \to \Delta({\mathcal{Y}})^{{\mathcal{X}}}$$ such that, for $$w\in{\mathcal{W}}$$ and $$x\in{\mathcal{X}}$$,

$$
p(y \mid x, w) = \frac{1}{(2\pi)^{m/2}}\exp\!\left(-\frac{\|y - f_{w}(x)\|^{2}}{2}\right).
$$

The above **Gaussian noise model** amounts to modelling each output $$y$$ as drawn given $$x, w$$ according to the rule $$y = f_{w}(x) + \varepsilon$$ with $$\varepsilon \sim \mathcal{N}(0, I_{m})$$.

As the following exercises explore, performing statistical inference according to the principle of maximum likelihood aligns with the loss-minimisation perspective (given an appropriate choice of loss function).

:::callout {title="Exercise" tone="amber"}
**Exercise 1.3 (Maximum likelihood as MSE minimisation).** Consider a regression problem with $${\mathcal{X}} = {\mathcal{Y}} = {\mathbb{R}}^{m}$$. Assume we have a neural network architecture with a parameter space $${\mathcal{W}}$$. Form a corresponding statistical model using the Gaussian noise model of (11). Let $$(x^{(1)}, y^{(1)}),$$ $$\ldots,$$ $$(x^{(n)}, y^{(n)}) \in {\mathcal{X}} \times {\mathcal{Y}}$$ be a data set of $$n$$ regression examples.

**(a)** Write an expression for the conditional probability of observing the labels $$Y_{n} = (y^{(1)}, \ldots, y^{(n)})$$ given the inputs $$X_{n} = (x^{(1)}, \ldots, x^{(n)})$$ and some fixed parameter $$w \in W$$, assuming the labels are sampled independently.

**(b)** Denote the resulting quantity by $$p(Y_{n} \mid X_{n}, w)$$. It is called the **likelihood** of the data set according to the model $$w$$. Compute and simplify the **negative log-likelihood**, given by $$-\log p(Y_{n} \mid X_{n}, w)$$.

**(c)** Show that if $$L_{n}$$ is the mean squared error loss function from (9), then

$$
{\operatorname*{arg\,max}}_{w \in {\mathcal{W}}}p(Y_{n} \mid X_{n}, w) = {\operatorname*{arg\,min}}_{w \in {\mathcal{W}}}L_{n}(w) .
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since labels are sampled independently, the likelihood factorises as a product of Gaussian densities:

$$
\begin{aligned}p(Y_{n} \mid X_{n}, w)&= \prod_{i=1}^{n} p(y^{(i)}| x^{(i)}, w) \\&= \prod_{i=1}^{n} \frac{1}{(2\pi)^{m/2}}\exp\!\left( -\frac{\|y^{(i)}- f_{w}(x^{(i)})\|^{2}}{2}\right).\end{aligned}
$$

**(b)** Taking the negative logarithm of the above expression,

$$
\begin{aligned}-\log p(Y_{n} \mid X_{n}, w)&= -\sum_{i=1}^{n} \left[ -\frac{m}{2}\log(2\pi) - \frac{\|y^{(i)}- f_{w}(x^{(i)})\|^{2}}{2}\right] \\&= \frac{nm}{2}\log(2\pi) + \frac{1}{2}\sum_{i=1}^{n} \|y^{(i)}- f_{w}(x^{(i)})\|^{2}.\end{aligned}
$$

**(c)** From the mean squared error definition (9),

$$
-\log p(Y_{n} \mid X_{n}, w) = \frac{nm}{2}\log(2\pi) + \frac{n}{2}L_{n}(w).
$$

The right-hand side is a strictly increasing affine function of $$L_{n}(w)$$ (with positive coefficient $$n/2$$), and the additive constant $$\frac{nm}{2}\log(2\pi)$$ is independent of $$w$$. Therefore,

$$
{\operatorname*{arg\,max}}_{w\in{\mathcal{W}}}p(Y_{n} \mid X_{n}, w) = {\operatorname*{arg\,min}}_{w\in{\mathcal{W}}}\left(-\log p(Y_{n} \mid X_{n}, w)\right) = {\operatorname*{arg\,min}}_{w\in{\mathcal{W}}}L_{n}(w).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.4 (Maximum likelihood as cross entropy minimisation).** Consider a classification problem with $${\mathcal{Y}} = \Delta^{m-1}$$. Assume we have a neural network architecture with a parameter space $${\mathcal{W}}$$. As discussed, the parameter–function map in this case corresponds to a parameter–distribution map to conditional distributions over the underlying discrete class space $${\mathcal{C}} = \{1, \ldots, m\}$$. Let $$(x^{(1)}, c^{(1)}),$$ $$\ldots,$$ $$(x^{(n)}, c^{(n)}) \in {\mathcal{X}} \times {\mathcal{C}}$$ be a data set of $$n$$ labelled classification examples. For each $$c^{(i)}\in {\mathcal{C}}$$ define

$$
y^{(i)}= \delta_{c^{(i)}}\in \Delta^{m-1}
$$

to be the corresponding Dirac distribution (with probability mass $$1$$ concentrated on $$c^{(i)}$$).

**(a)** Write an expression for the likelihood of the data set, $$p(C_{n} \mid X_{n}, w)$$, that is, the conditional probability of observing the labels $$C_{n} = (c^{(1)}, \ldots, c^{(n)})$$ given the inputs $$X_{n} = (x^{(1)}, \ldots, x^{(n)})$$ and some fixed parameter $$w \in W$$. Assume the labels are sampled independently.

**(b)** Show that the negative log-likelihood

$$
-\log p(C_{n} \mid X_{n}, w) = - \sum_{i=1}^{n} \log f_{w}(c^{(i)}\mid x^{(i)}) .
$$

**(c)** Using (12), show that if the per-example loss function for the optimisation problem is cross entropy loss (6), then

$$
{\operatorname*{arg\,max}}_{w \in {\mathcal{W}}}p(C_{n} \mid X_{n}, w) = {\operatorname*{arg\,min}}_{w \in {\mathcal{W}}}L_{n}(w) .
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since labels are sampled independently, the likelihood factorises as

$$
p(C_{n} \mid X_{n}, w) = \prod_{i=1}^{n} p(c^{(i)}| x^{(i)}, w) = \prod_{i=1}^{n} f_{w}(c^{(i)}\mid x^{(i)}).
$$

**(b)** Taking the negative logarithm,

$$
-\log p(C_{n} \mid X_{n}, w) = -\sum_{i=1}^{n} \log f_{w}(c^{(i)}\mid x^{(i)}).
$$

**(c)** Since $$y^{(i)}= \delta_{c^{(i)}}$$ is the Dirac distribution on class $$c^{(i)}$$, we have $$y^{(i)}(j) = 1$$ if $$j = c^{(i)}$$ and $$y^{(i)}(j) = 0$$ otherwise. Substituting into the cross entropy loss (6),

$$
L_{x^{(i)},y^{(i)}}(w) = -\sum_{j=1}^{m} y^{(i)}(j) \log f_{w}(j \mid x^{(i)}) = -\log f_{w}(c^{(i)}\mid x^{(i)}).
$$

Therefore the empirical loss is

$$
\begin{aligned}L_{n}(w)&= \frac{1}{n}\sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) = -\frac{1}{n}\sum_{i=1}^{n} \log f_{w}(c^{(i)}\mid x^{(i)}) \\&= \frac{1}{n}\left(-\log p(C_{n} \mid X_{n}, w)\right).\end{aligned}
$$

Since the negative log-likelihood is $$n \cdot L_{n}(w)$$, a positive multiple of the empirical loss, we conclude

$$
{\operatorname*{arg\,max}}_{w\in{\mathcal{W}}}p(C_{n} \mid X_{n}, w) = {\operatorname*{arg\,min}}_{w\in{\mathcal{W}}}L_{n}(w).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.5 (Maximum likelihood as loss minimisation, in general).** Consider a neural network architecture with a parameter space $${\mathcal{W}}$$, parameter–function map $$\Phi$$, and output space $${\mathcal{Y}} = {\mathbb{R}}^{m}$$. Let $$L_{x,y}: {\mathcal{W}} \to {\mathbb{R}}$$ be a per-example loss function. Assume that for each $$x \in {\mathcal{X}}$$ and $$w \in {\mathcal{W}}$$, the function $$y \mapsto \exp(-L_{x,y}(w))$$ is integrable over $${\mathcal{Y}}$$. Define a corresponding statistical model with parameter–distribution map $$\Psi$$ mapping $$w \in {\mathcal{W}}$$ to $$p_{w} : {\mathcal{X}} \to \Delta({\mathcal{Y}})$$ such that for all $$y \in {\mathcal{Y}}$$, $$x \in {\mathcal{X}}$$, and $$w \in {\mathcal{W}}$$, we have

$$
p(y \mid x, w) = \frac{\exp\!\left(- L_{x,y}(w)\right)}{Z(x,w)}, \qquad Z(x,w) = \int_{{\mathcal{Y}}}\exp\!\left(- L_{x,z}(w) \right)dz .
$$

We re-use the notation $$X_{n}$$, $$Y_{n}$$ from Exercise 1.3, and assume that labels are sampled independently.

**(a)** Show that the negative log-likelihood decomposes as

$$
-\log p(Y_{n} \mid X_{n}, w) = \sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) + \sum_{i=1}^{n} \log Z(x^{(i)}, w) .
$$

**(b)** Now suppose the loss function takes the form $$L_{x,y}(w) = \ell(f_{w}(x) - y)$$ for some integrable function $$\ell : {\mathbb{R}}^{m} \to {\mathbb{R}}$$. Show that $$Z(x, w)$$ is independent of $$w$$, and conclude that

$$
{\operatorname*{arg\,max}}_{w \in {\mathcal{W}}}p(Y_{n} \mid X_{n}, w) = {\operatorname*{arg\,min}}_{w \in {\mathcal{W}}}L_{n}(w) .
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since labels are sampled independently, the likelihood factorises as

$$
p(Y_{n} \mid X_{n}, w) = \prod_{i=1}^{n} p(y^{(i)}| x^{(i)}, w) = \prod_{i=1}^{n} \frac{\exp\!\left(-L_{x^{(i)},y^{(i)}}(w)\right)}{Z(x^{(i)}, w)}.
$$

Taking the negative logarithm,

$$
\begin{aligned}-\log p(Y_{n} \mid X_{n}, w)&= -\sum_{i=1}^{n} \left[ -L_{x^{(i)},y^{(i)}}(w) - \log Z(x^{(i)}, w) \right] \\&= \sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) + \sum_{i=1}^{n} \log Z(x^{(i)}, w).\end{aligned}
$$

**(b)** Suppose $$L_{x,y}(w) = \ell(f_{w}(x) - y)$$. Making the substitution $$u = f_{w}(x) - z$$ (so that $$dz = du$$) in the definition of the partition function,

$$
Z(x, w) = \int_{{\mathbb{R}}^m}\exp\!\left(-\ell(f_{w}(x) - z)\right) dz = \int_{{\mathbb{R}}^m}\exp\!\left(-\ell(u)\right) du.
$$

The right-hand side is a constant independent of both $$x$$ and $$w$$. Therefore, by part (a), the negative log-likelihood is

$$
-\log p(Y_{n} \mid X_{n}, w) = \sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) + C = n \cdot L_{n}(w) + C
$$

where $$C = n \log \int_{{\mathbb{R}}^m}\exp(-\ell(u))\,du$$ is independent of $$w$$. Since the negative log-likelihood is an affine function of $$L_{n}(w)$$ with positive coefficient,

$$
{\operatorname*{arg\,max}}_{w\in{\mathcal{W}}}p(Y_{n} \mid X_{n}, w) = {\operatorname*{arg\,min}}_{w\in{\mathcal{W}}}L_{n}(w).
$$

:::

:::callout {title="Note" tone="blue"}

**Remark (Negative log-likelihood loss).** Exercises 1.3, 1.4 and 1.5 nominally show that some maximum likelihood estimation problems have the same sets of ideal solutions as some carefully-chosen optimisation problems ($${\operatorname*{arg\,min}} = {\operatorname*{arg\,max}}$$). In general, that the global optima for two optimisation problems coincide is insufficient to show that practical optimisation methods will always find the same solutions: practical optimisation methods don't always find global optima. However, in the above cases, your derivation likely reveals a stronger result: the optimisation landscapes for the function approximation problem are related to the optimisation landscape for the maximum likelihood estimation problem by a strictly monotonically decreasing transform (an affine transform of a logarithm).

:::

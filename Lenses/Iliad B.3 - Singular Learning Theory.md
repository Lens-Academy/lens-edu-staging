---
id: 'e3aefe7c-dd33-4c8f-a292-09d6408fc2a5'
title: "B.3 Singular Learning Theory"
tldr: "Singular learning theory (SLT) places degeneracy as a core part of understanding how neural networks learn. We cover the parameter-function map, the meaning of degeneracy through the local learning coefficient, to Watanabe's free energy formula and Bayesian phase transitions."
summary_for_tutor: "Faithful April 2026 Iliad Intensive worksheet B.3, Singular Learning Theory. Preserve its mathematical notation, exercise sequence, hints, and solutions."
authors:
  - Kai Ogden
  - Matthew Farrugia-Roberts
  - Zach Furman
source_url: https://github.com/iliad-team/iliad-intensive/blob/1eb9e340305e03de3f81a761167e13c54c71f19d/tex/singular-learning-theory/main.tex
upstream_commit: '1eb9e340305e03de3f81a761167e13c54c71f19d'
provenance_recorded_at: '2026-08-17'
---

#### Text
content::
> *Thou shalt have the power to degenerate*
>     —*On the Dignity of Man,* 1496

\## Introduction

*Singular learning theory (SLT)* is a theory of learning that accounts for *degeneracy* in neural networks. What is degeneracy? Let us first appeal to the Cambridge dictionary, documenting some features of typical uses of the word within mathematics:

> *Degenerate* (of an equation, curve, line, etc.) unusual or complicated in some way compared to other equations, curves, lines, etc.  of a similar type, especially because a variable or parameter is zero.

On the other hand, we should recall that deep learning has as many roots in neuroscience as in mathematics. And as they say, "neural networks are *grown.*" Perhaps we should also hear the biologist's definition:

> *Degenerate* (of an organism, chromosome, etc.) simpler than a form that previously existed because of no longer having a particular structure.

Actually, *both* of these definitions are apt. Within a typical neural network architecture, certain weight vectors correspond to neural networks from simpler architectures (often due to certain weights being zero). Structurally, these neural networks are simpler in form than their neighbours. Mathematically, they complicate the relationship between the neural network's parameter space and the resulting space of functions. In turn, learning in neural networks is substantially richer than learning in classical statistical models.

Singular learning theory is a framework for understanding learning that places degeneracy at the centre. The framework leverages powerful tools from algebraic geometry to understand, characterise, and resolve degeneracies, revealing their impact on learning. Unfortunately, the price of this mathematical power is that following the research literature without a deep background in pure mathematics is challenging.

That is where this tutorial comes in. We aim to distil the essence of singular learning theory—the notion of degeneracy and its role in learning—laying bare through simple examples and structured exercises the core intuitions driving research in the field. We believe understanding this essence requires no more than undergraduate-level mathematics. Moreover, to anyone armed with these core intuitions, understanding and contributing to research on the relationship between degeneracy and deep learning is within reach.

**Contents.**  Specifically, the tutorial comprises the following four technical sections, each with definitions and guided exercises.

1. "[[#1. Preliminaries|Section 1]]" reviews core deep learning concepts, defining our notation and some running examples. The central concept is that of the parameter–function map.
2. "[[#2. What is degeneracy?|Section 2]]" defines degeneracy of parameter–function maps and relates it to symmetries, singularities of the Fisher information, and degenerate critical points of the loss landscape.
3. "[[#3. The degeneracy hierarchy|Section 3]]" derives the local learning coefficient (LLC) as a quantitative measure of the degree of degeneracy of a critical point via a volume scaling approach, and surveys several other perspectives on the quantity.
4. "[[#4. Degeneracy and Bayesian deep learning|Section 4]]" presents Watanabe's free energy formula connecting the LLC to Bayesian learning and discusses its implications.

We conclude with [[#5. Further readings|Section 5]], providing pointers for further study and surveying the literature on SLT and deep learning.

**Prerequisites.**

The following is an indicative list of mathematical concepts that will be helpful for reading the tutorial and completing the exercises.

- *Linear algebra:* vectors, matrices, rank, orthogonal matrices, rank–nullity, positive definiteness, eigenvalues, spectral decomposition.
- *Calculus:* partial derivatives, gradient, directional derivative, chain rule, Hessian, second-order Taylor expansion and remainder.
- *Integration and analysis:* multivariate integrals, change of variables, volume in $\mathbb{R}^{d}$, asymptotic notation (big-$O$, little-$o$), computing basic limits and integrals.
- *Probability:* probability simplex $\Delta(\cdot)$, conditional probability, probability density functions, independence, expectation, Bayes' rule, Gaussians, law of large numbers.

[[#1. Preliminaries|Section 1]] reviews the basic framework of deep learning as parametric function approximation or statistical inference (parameter–function maps, deep linear networks, multi-layer perceptrons, loss functions, likelihood) along with Bayesian inference (prior, posterior, partition function, Bayesian free energy).

Readers with more advanced backgrounds may appreciate occasional references to topics from algebraic geometry, fractal geometry, or statistical physics. However, these references are tangential and readers without these backgrounds can safely skip them.

**Fast-track.**

To paraphrase Euclid, there is no royal road to algebro-geometric learning theory. However, it is possible to get a bird's-eye view and the most important intuitions in a comparably short time. If this is what you are looking for, we recommend the following route through the tutorial. Assuming you are already somewhat comfortable with deep learning and Bayesian inference, skip [[#1. Preliminaries|Section 1]], and refer back only as needed. Then, proceed as follows.

1. To understand parameter–function map versus loss landscape degeneracy: Read [[#2.1 A definition of degeneracy|Subsection 2.1]] and complete [[#^ex-univariate-degeneracy|Exercise 2.1]] and [[#^ex-cubic-degeneracy|2.2]]. Complete either [[#^ex-dln-degeneracy|Exercise 2.9]] or [[#^ex-mlp-degeneracy|2.10]]. Read [[#2.5 Degeneracy and the loss landscape|Subsection 2.5]] and complete your choice of Exercises [[#^ex-loss-landscape-degeneracy|2.14]] and/or [[#^ex-fim-hessian|2.15]].
2. To understand the local learning coefficient via volume scaling: Read [[#3.1 The local learning coefficient via volume scaling asymptotics|Subsection 3.1]] and complete [[#^ex-llc-regular-case|Exercise 3.1]] and [[#^ex-quad-valley-scaling|3.2]] and [[#^ex-calculating-llc|3.4]] and [[#^ex-cubic-parameterisation|3.7]]. Read [[#3.3 Local learning coefficients of deep linear networks|Subsection 3.3]] and [[#^ex-dln-lc|Exercise 3.10]].
3. To understand the relation between degeneracy and learning in the Bayesian case: Read all of [[#4. Degeneracy and Bayesian deep learning|Section 4]] (it is shorter). Complete [[#^ex-phase-transitions|Exercise 4.2]].

Once you are done, we hope you will consider taking the scenic route some other time.

**Acknowledgements.**

This tutorial was developed for the April 2026 Iliad Intensive. Some exercises were adapted from [[#^bib-furman2024|Furman 2024]].

\## 1. Preliminaries

In this section, we introduce basic terminology and notation for supervised deep learning and supervised Bayesian deep learning, along with some example neural network architectures and statistical models that we will repeatedly study throughout the tutorial.

\### 1.1 Neural networks and parameter–function maps

Let $\mathcal{X}$ denote a space of network inputs (e.g., a space of images or token sequences encoded as vectors), and let $\mathcal{Y}$ denote a space of outputs (e.g., a space of numerical scores, class distributions, or next-token distributions).

Informally, a neural network architecture is a specification for how various **parameters** (e.g., neuron connection strengths / weights or neuron activation thresholds / biases) combine with input signals and each-other to describe a function from $\mathcal{X}$ to $\mathcal{Y}$.

Formally, a neural network architecture essentially comprises a **parameter–function map** $\Phi : \mathcal{W} \to \mathcal{F}$, where $\mathcal{W} \subseteq \mathbb{R}^{d}$ is a $d$-dimensional **parameter space** and $\mathcal{F} \subseteq \mathcal{Y}^{\mathcal{X}}$ is some **hypothesis class** of functions from $\mathcal{X}$ to $\mathcal{Y}$.

It is sometimes convenient to refer to the function $\Phi(w) : \mathcal{X} \to \mathcal{Y}$ as $f_{w} : \mathcal{X} \to \mathcal{Y}$.

Throughout the rest of this tutorial, we will study many different neural network architectures (parameter–function maps). The rest of this section explores some generally useful examples and some terminological points. To begin with, we have the following remark.

:::callout {title="Note" tone="blue"}

**Remark (Parameters).** Note that the term "parameter" has two senses:

1. A "parameter" is an individual dimension of parameter space (e.g., "initialise this parameter to the value $0.0$," or "this neural network has billions of parameters"). A loose synonym in this case is "weight."
2. A "parameter" is also a particular point in the parameter space (e.g., "this parameter is a local minimum of the loss function," or "the zero locus of this loss function contains a continuum of parameters"). A loose synonym in this case is "weight vector."

Both senses are in common usage in the literature as in this tutorial.

:::

The simplest neural network architecture models a single "neuron" with $d$ inputs $x_{1}, \ldots x_{d}$. Each input $x_{i}$ is multiplied by an incoming weight $w_{i}$ to produce the neuron's output. We formalise this case in [[#^eg-neuron|Example 1.1]].

::::callout {title="Note" tone="green"}

**Example 1.1 (A linear neuron).** Let $\mathcal{X} = \mathbb{R}^{d}$ for some positive integer $d$ and let $\mathcal{Y} = \mathbb{R}$. Define a parameter space $\mathcal{W} = \mathbb{R}^{d}$. Define a parameter–function map that maps a column vector $w \in \mathcal{W}$ to the function $f_{w} : \mathbb{R}^{d} \to \mathbb{R}$ such that for $x \in \mathbb{R}^{d}$,

$$
f_{w}(x) = w^{\top} x = \sum_{i=1}^{d} w_{i} x_{i}.
$$

::::

^eg-neuron


Let us generalise this basic neural network in three ways: to add multiple outputs, "depth," and non-linearity. First, we can generalise from a scalar output to a vector output as follows.

::::callout {title="Note" tone="green"}

**Example 1.2 (Multi-linear neural network).** Let $\mathcal{X} = \mathcal{Y} = \mathbb{R}^{m}$ for some positive integer $m$. Define a parameter space $\mathcal{W} = \mathbb{R}^{m^2}$. Let each parameter $w \in \mathcal{W}$ encode an $m \times m$ matrix $W \in \mathbb{R}^{m \times m}$. The parameter–function map transforms each parameter $w \in \mathcal{W}$ to a function $f_{w} : \mathbb{R}^{m} \to \mathbb{R}^{m}$ such that for $x \in \mathbb{R}^{m}$,

$$
f_{w}(x) = W x.
$$

::::

^eg-linear


If we take each row of $W$ to encode the weight vector of a linear neuron ([[#^eg-neuron|Example 1.1]]), we see that we have produced $m$ outputs by stacking $m$ independent linear neurons together. Such a group of neurons is called a **layer**.

:::callout {title="Note" tone="blue"}

**Remark (Encodings).** In [[#^eg-linear|Example 1.2]], the parameter space is formally $\mathcal{W} = \mathbb{R}^{m^2}$, but we find it convenient to identify each parameter vector $w \in \mathbb{R}^{m^2}$ with the $m \times m$ matrix $W$ it encodes. We would thus write $f_{W}$ in place of $f_{w}$. More generally, whenever the parameters of an architecture naturally decompose into named matrices or vectors, we index the parameter–function map by these structured objects directly rather than by the underlying vector $w$. The remaining examples in this section demonstrate this convention, and we continue to use it throughout this tutorial.

:::

Next, let's add *depth* to our neural network by composing two layers together.

::::callout {title="Note" tone="green"}

**Example 1.3 (Deep linear network; DLN).** Let $\mathcal{X} = \mathcal{Y} = \mathbb{R}^{m}$ for some positive integer $m$. Let $h$ be a positive integer and define the parameter space $\mathcal{W} = \mathbb{R}^{2mh}$, with each parameter encoding a pair of matrices $A \in \mathbb{R}^{h \times m}$ and $B \in \mathbb{R}^{m \times h}$. The parameter–function map sends $(A, B)$ to $f_{A,B}: \mathbb{R}^{m} \to \mathbb{R}^{m}$ such that for $x \in \mathbb{R}^{m}$,

$$
f_{A,B}(x) = B A x.
$$

::::

^eg-dln


The above architecture is called a two-layer **deep linear network (DLN)**. The architecture can be interpreted as composing two multi-linear neural networks. The vector of outputs of the neurons of the first network becomes the vector of inputs to the second network. The intermediate output vectors are called **activations**.

Note that if $h \geq m$, the two-layer DLN architecture indexes the same hypothesis class as in [[#^eg-linear|Example 1.2]], that of linear transforms on $\mathbb{R}^{m}$. If $h < m$, the hypothesis class includes only transforms with rank up to $h$.

Finally, we'll add *non-linearity* between pairs of layers. To do so, we introduce a non-linear scalar function $\sigma : \mathbb{R} \to \mathbb{R}$, called an *activation function*, to transform the output of each intermediate neuron. Common examples of activation functions, which we will study in this tutorial, include the following:

1. The **hyperbolic tangent** function $\displaystyle \tanh(z) = \frac{e^{z}-e^{-z}}{e^{z} + e^{-z}}$.
2. The **rectified linear unit (ReLU)** function $\mathrm{relu}(z) = \max\{0, z\}$.

This results in the following non-linear neural network architecture.

::::callout {title="Note" tone="green"}

**Example 1.4 (Multi-layer perceptron; MLP).** Define input, output, and parameter spaces as in [[#^eg-dln|Example 1.3]]. Let $\sigma : \mathbb{R} \to \mathbb{R}$ be an activation function. The parameter–function map sends $(A, B)$ to the function $f_{A,B}: \mathbb{R}^{m} \to \mathbb{R}^{m}$ such that for $x \in \mathbb{R}^{m}$,

$$
f_{A,B}(x) = B \cdot \sigma( A x ),
$$

where we lift the activation function to operate element-wise over column vectors $A x \in \mathbb{R}^{h}$.

::::

^eg-mlp

This kind of architecture is called a **multi-layer perceptron (MLP).** Note that the two-layer DLN is recovered if we use the identity function as an activation function. However, if we use a non-linear activation function, we can index a much richer hypothesis class.

The expressivity of these architectures is limited, however, by the omission of a basic detail—the inclusion of a bias parameter for each neuron. We invite the reader to correct this omission as our first exercise, which serves as a chance to familiarise oneself with the concept of a parameter–function map.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.1 (Biased neurons).** A biased neuron is a neuron with an additional parameter that is added to the weighted sum of its inputs before it produces its output. Bias parameters allow each layer to represent an *affine* transform, rather than just a linear transform. For each of Examples [[#^eg-neuron|1.1]], [[#^eg-linear|1.2]], [[#^eg-dln|1.3]], and [[#^eg-mlp|1.4]], extend the example to use biased neurons. Precisely define the parameter space and the parameter–function map in each case.
:::

^ex-biased-neurons


:::callout {title="Solution" tone="neutral" collapse="closed"}

For each architecture, we add a bias vector to each layer's output before the next transformation (or activation function) is applied.

1. **A linear neuron with bias** ([[#^eg-neuron|Example 1.1]]). Let $\mathcal{W} = \mathbb{R}^{d+1}$, encoding a weight vector $w \in \mathbb{R}^{d}$ and a scalar bias $b \in \mathbb{R}$. The parameter–function map sends $(w, b)$ to $f_{w,b}: \mathbb{R}^{d} \to \mathbb{R}$ defined by

$$
f_{w,b}(x) = w^{\top} x + b.
$$
2. **Multi-linear neural network with bias** ([[#^eg-linear|Example 1.2]]). Let $\mathcal{W} = \mathbb{R}^{m^2 + m}$, encoding a matrix $W \in \mathbb{R}^{m \times m}$ and a bias vector $b \in \mathbb{R}^{m}$. The parameter–function map sends $(W, b)$ to $f_{W,b}: \mathbb{R}^{m} \to \mathbb{R}^{m}$ defined by

$$
f_{W,b}(x) = Wx + b.
$$
3. **Deep linear network with bias** ([[#^eg-dln|Example 1.3]]). Let $\mathcal{W} = \mathbb{R}^{2mh + h + m}$, encoding matrices $A \in \mathbb{R}^{h \times m}$, $B \in \mathbb{R}^{m \times h}$ and bias vectors $b_{A} \in \mathbb{R}^{h}$, $b_{B} \in \mathbb{R}^{m}$. The parameter–function map sends $(A, b_{A}, B, b_{B})$ to $f_{w} : \mathbb{R}^{m} \to \mathbb{R}^{m}$ defined by

$$
f_{w}(x) = B(Ax + b_{A}) + b_{B}.
$$
4. **Multi-layer perceptron with bias** ([[#^eg-mlp|Example 1.4]]). The parameter space is $\mathcal{W} = \mathbb{R}^{2mh + h + m}$ as above. The parameter–function map sends $(A, b_{A}, B, b_{B})$ to $f_{w} : \mathbb{R}^{m} \to \mathbb{R}^{m}$ defined by

$$
f_{w}(x) = B \cdot \sigma(Ax + b_{A}) + b_{B}.
$$

:::

Modern deep learning leverages more involved parameter–function maps. Neural network architectures are typically defined in a modular fashion, including linear (or affine) layers and non-linear layers like the above, along with more specialised layers (well-known examples including convolutional layers, residual layers, and attention layers).

\### 1.2 Supervised deep learning and loss functions

In a typical supervised deep learning setting, we are given a data set of pairs $(x^{(1)}, y^{(1)}),$ $\ldots,$ $(x^{(n)}, y^{(n)}) \in \mathcal{X} \times \mathcal{Y}$. These pairs exemplify inputs and their corresponding (possibly noisy) outputs from an unknown target function $f : \mathcal{X} \to \mathcal{Y}$ which we would like to approximate using a neural network. That is, we would like to find a parameter $w \in \mathcal{W}$ such that the corresponding function $f_{w}$ approximates the target function $f$.

Formally, given an example $(x, y) \in \mathcal{X} \times \mathcal{Y}$, define a **per-example loss** function $L_{x,y}: \mathcal{W} \to \mathbb{R}$ to measure the deviation of $f_{w}(x)$ from the output $y$. A typical loss function for vector outputs $\mathcal{Y} \subset \mathbb{R}^{m}$ is to use the **squared error** loss


$$
L_{x,y}(w) = \|f_{w}(x) - y\|^{2}.
$$


^eq-square-loss


If $\mathcal{Y} = \Delta^{m-1}$ is a space of discrete distributions over $m$ objects it is typical to use **cross entropy** loss


$$
L_{x,y}(w) = - \sum_{i=1}^{m} y(i) \log f_{w}(i \mid x).
$$


^eq-cross-entropy


Given a per-example loss function and a **data distribution** $q \in \Delta(\mathcal{X}\times\mathcal{Y})$ over the space of examples (representing our possibly-noisy target function), we formalise the objective of supervised learning as finding $w \in \mathcal{W}$ so as to minimise the **population loss** function $L : \mathcal{W} \to \mathbb{R}$ defined such that

$$
L(w) = \mathbb{E}_{(x,y) \sim q}[L_{x,y}(w)].
$$

The population loss aggregates differences on outputs for individual inputs into an overall measure of difference between $f_{w}$ and the target function.

In practice, we often can't evaluate the population loss over the entire input/output space. We instead optimise an estimator based on our data set of $n$ input–output pairs assumed to be sampled independently and identically from $q$. Define an **empirical loss** function $L_{n} : \mathcal{W} \to \mathbb{R}$ such that

$$
L_{n}(w) = \frac{1}{n} \sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w).
$$

If the per-example loss is squared error, the empirical loss is known as the **mean squared error** objective.


$$
L_{n}(w) = \frac{1}{n} \sum_{i=1}^{n} \left\| f_{w}(x^{(i)}) - y^{(i)}\right\|^{2}.
$$


^eq-mse


:::callout {title="Exercise" tone="amber"}
**Exercise 1.2 (Empirical loss and population loss).** Fix $w \in \mathcal{W}$. Prove the following properties of the relationship between the empirical loss $L_{n}(w)$ and the population loss $L(w)$.

**(a)** For any $n$, the empirical loss is an unbiased estimator of the population loss. That is,

$$
\mathbb{E}_{(x^{(i)}, y^{(i)}) \sim q}[L_{n}(w)] - L(w) = 0.
$$

**(b)** As $n \to \infty$, the empirical loss converges almost surely to the population loss.
:::

^ex-empirical-population-loss


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since the data pairs $(x^{(i)}, y^{(i)})$ are sampled independently and identically from $q$, each per-example loss $L_{x^{(i)},y^{(i)}}(w)$ is an identically distributed random variable with expectation

$$
\mathbb{E}_{(x,y)\sim q}[L_{x,y}(w)] = L(w).
$$

Therefore, by linearity of expectation,

$$
\mathbb{E}[L_{n}(w)] = \mathbb{E}\left[\frac{1}{n}\sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w)\right] = \frac{1}{n}\sum_{i=1}^{n} \mathbb{E}[L_{x^{(i)},y^{(i)}}(w)] = \frac{1}{n}\cdot n \cdot L(w) = L(w).
$$
2. The random variables $L_{x^{(1)},y^{(1)}}(w), L_{x^{(2)},y^{(2)}}(w), \ldots$ are independent and identically distributed with common mean $L(w)$. By the strong law of large numbers,

$$
L_{n}(w) = \frac{1}{n}\sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) \xrightarrow{n\to\infty}L(w)
$$

almost surely.

:::

Given a loss function, a **training algorithm** is a search algorithm that aims to find $w \in \mathcal{W}$ such that the loss is approximately minimised. Most modern deep learning algorithms are variants of **stochastic gradient descent (SGD)**, which implements an iterative gradient-based local search of the parameter space using empirical loss on subsamples of the data set.

Through many impressive feats of computer science and hardware/software engineering, we are able to run such training algorithms to find low-loss parameters within parameter spaces with billions of dimensions. The details are vitally important to the success of modern deep learning, but are beyond the scope of this tutorial. We only mention SGD in order to emphasise that *any local search method depends intimately on the properties of the parameter–function map.*

\### 1.3 Statistical models and parameter–distribution maps

The previous sections introduce neural networks and supervised deep learning within a framework of function approximation. An alternative approach is to view supervised learning as statistical inference, and particularly Bayesian inference. This statistical framework is commonly used within the SLT literature, and we will encounter it within this tutorial.

The first step to upgrading our framework is to move from talking about functions to talking about conditional distributions. For each neural network, we should be able to determine not just the output corresponding to each input, but a probability density measuring how likely each output is given each input.

Formally, let $\mathcal{D} \subseteq \Delta(\mathcal{Y})^{\mathcal{X}}$ represent a class of conditional distributions over $\mathcal{Y}$. A distributional neural network architecture comprises a **parameter–distribution map** $\Psi : \mathcal{W} \to \mathcal{D}$. It is sometimes convenient to refer to the conditional distribution $\Psi(w) : \mathcal{X} \to \Delta(\mathcal{Y})$ using the notation $p_{w} : \mathcal{X} \to \Delta(\mathcal{Y})$. The probability mass/density of a given output $y \in \mathcal{Y}$ conditional on a given input $x \in \mathcal{X}$ is typically denoted either $p_{w}(y \mid x)$ or $p(y \mid x, w)$.

Sometimes, defining a parameter–distribution map is simply a re-framing. For example, in image classification, our output space $\mathcal{Y}$ was a space of distributions over image classes. Let $\mathcal{C}$ represents the underlying class space, then $\mathcal{Y} = \Delta(\mathcal{C})$ and we can view our parameter–function map $\Phi : \mathcal{W} \to \mathcal{F}$ as a parameter–distribution map $\Psi : \mathcal{W} \to \mathcal{D}$ with $\mathcal{D} = \mathcal{F} \subseteq \mathcal{Y}^{\mathcal{X}} = \Delta(\mathcal{C})^{\mathcal{X}}$.

In other cases, we can easily construct a parameter–distribution map from a parameter–function map by introducing a **noise model**. For example, in regression with an output space $\mathcal{Y} = \mathbb{R}^{m}$, given a parameter–function map $w \mapsto f_{w}$ we can define a parameter–distribution map $\Psi : \mathcal{W} \to \Delta(\mathcal{Y})^{\mathcal{X}}$ such that, for $w\in\mathcal{W}$ and $x\in\mathcal{X}$,


$$
p(y \mid x, w) = \frac{1}{(2\pi)^{m/2}}\exp\!\left(-\frac{\|y - f_{w}(x)\|^{2}}{2}\right).
$$


^eq-gaussian-model


The above **Gaussian noise model** amounts to modelling each output $y$ as drawn given $x, w$ according to the rule $y = f_{w}(x) + \varepsilon$ with $\varepsilon \sim \mathcal{N}(0, I_{m})$.

As the following exercises explore, performing statistical inference according to the principle of maximum likelihood aligns with the loss-minimisation perspective (given an appropriate choice of loss function).

:::callout {title="Exercise" tone="amber"}
**Exercise 1.3 (Maximum likelihood as MSE minimisation).** Consider a regression problem with $\mathcal{X} = \mathcal{Y} = \mathbb{R}^{m}$. Assume we have a neural network architecture with a parameter space $\mathcal{W}$. Form a corresponding statistical model using the Gaussian noise model of [[#^eq-gaussian-model|(11)]]. Let $(x^{(1)}, y^{(1)}),$ $\ldots,$ $(x^{(n)}, y^{(n)}) \in \mathcal{X} \times \mathcal{Y}$ be a data set of $n$ regression examples.

**(a)** Write an expression for the conditional probability of observing the labels $Y_{n} = (y^{(1)}, \ldots, y^{(n)})$ given the inputs $X_{n} = (x^{(1)}, \ldots, x^{(n)})$ and some fixed parameter $w \in W$, assuming the labels are sampled independently.

**(b)** Denote the resulting quantity by $p(Y_{n} \mid X_{n}, w)$. It is called the **likelihood** of the data set according to the model $w$. Compute and simplify the **negative log-likelihood**, given by $-\log p(Y_{n} \mid X_{n}, w)$.

**(c)** Show that if $L_{n}$ is the mean squared error loss function from [[#^eq-mse|(9)]], then

$$
\operatorname*{arg\,max}_{w \in \mathcal{W}}p(Y_{n} \mid X_{n}, w) = \operatorname*{arg\,min}_{w \in \mathcal{W}}L_{n}(w) .
$$
:::

^ex-nll-mse


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since labels are sampled independently, the likelihood factorises as a product of Gaussian densities:

$$
\begin{aligned}p(Y_{n} \mid X_{n}, w)&= \prod_{i=1}^{n} p(y^{(i)}| x^{(i)}, w) \\&= \prod_{i=1}^{n} \frac{1}{(2\pi)^{m/2}}\exp\!\left( -\frac{\|y^{(i)}- f_{w}(x^{(i)})\|^{2}}{2}\right).\end{aligned}
$$
2. Taking the negative logarithm of the above expression,

$$
\begin{aligned}-\log p(Y_{n} \mid X_{n}, w)&= -\sum_{i=1}^{n} \left[ -\frac{m}{2}\log(2\pi) - \frac{\|y^{(i)}- f_{w}(x^{(i)})\|^{2}}{2}\right] \\&= \frac{nm}{2}\log(2\pi) + \frac{1}{2}\sum_{i=1}^{n} \|y^{(i)}- f_{w}(x^{(i)})\|^{2}.\end{aligned}
$$
3. From the mean squared error definition [[#^eq-mse|(9)]],

$$
-\log p(Y_{n} \mid X_{n}, w) = \frac{nm}{2}\log(2\pi) + \frac{n}{2}L_{n}(w).
$$

The right-hand side is a strictly increasing affine function of $L_{n}(w)$ (with positive coefficient $n/2$), and the additive constant $\frac{nm}{2}\log(2\pi)$ is independent of $w$. Therefore,

$$
\operatorname*{arg\,max}_{w\in\mathcal{W}}p(Y_{n} \mid X_{n}, w) = \operatorname*{arg\,min}_{w\in\mathcal{W}}\left(-\log p(Y_{n} \mid X_{n}, w)\right) = \operatorname*{arg\,min}_{w\in\mathcal{W}}L_{n}(w).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.4 (Maximum likelihood as cross entropy minimisation).** Consider a classification problem with $\mathcal{Y} = \Delta^{m-1}$. Assume we have a neural network architecture with a parameter space $\mathcal{W}$. As discussed, the parameter–function map in this case corresponds to a parameter–distribution map to conditional distributions over the underlying discrete class space $\mathcal{C} = \{1, \ldots, m\}$. Let $(x^{(1)}, c^{(1)}),$ $\ldots,$ $(x^{(n)}, c^{(n)}) \in \mathcal{X} \times \mathcal{C}$ be a data set of $n$ labelled classification examples. For each $c^{(i)}\in \mathcal{C}$ define


$$
y^{(i)}= \delta_{c^{(i)}}\in \Delta^{m-1}
$$


^eq-classification-dirac


to be the corresponding Dirac distribution (with probability mass $1$ concentrated on $c^{(i)}$).

**(a)** Write an expression for the likelihood of the data set, $p(C_{n} \mid X_{n}, w)$, that is, the conditional probability of observing the labels $C_{n} = (c^{(1)}, \ldots, c^{(n)})$ given the inputs $X_{n} = (x^{(1)}, \ldots, x^{(n)})$ and some fixed parameter $w \in W$. Assume the labels are sampled independently.

**(b)** Show that the negative log-likelihood

$$
-\log p(C_{n} \mid X_{n}, w) = - \sum_{i=1}^{n} \log f_{w}(c^{(i)}\mid x^{(i)}) .
$$

**(c)** Using [[#^eq-classification-dirac|(12)]], show that if the per-example loss function for the optimisation problem is cross entropy loss [[#^eq-cross-entropy|(6)]], then

$$
\operatorname*{arg\,max}_{w \in \mathcal{W}}p(C_{n} \mid X_{n}, w) = \operatorname*{arg\,min}_{w \in \mathcal{W}}L_{n}(w) .
$$
:::

^ex-nll-cross-entropy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since labels are sampled independently, the likelihood factorises as

$$
p(C_{n} \mid X_{n}, w) = \prod_{i=1}^{n} p(c^{(i)}| x^{(i)}, w) = \prod_{i=1}^{n} f_{w}(c^{(i)}\mid x^{(i)}).
$$
2. Taking the negative logarithm,

$$
-\log p(C_{n} \mid X_{n}, w) = -\sum_{i=1}^{n} \log f_{w}(c^{(i)}\mid x^{(i)}).
$$
3. Since $y^{(i)}= \delta_{c^{(i)}}$ is the Dirac distribution on class $c^{(i)}$, we have $y^{(i)}(j) = 1$ if $j = c^{(i)}$ and $y^{(i)}(j) = 0$ otherwise. Substituting into the cross entropy loss [[#^eq-cross-entropy|(6)]],

$$
L_{x^{(i)},y^{(i)}}(w) = -\sum_{j=1}^{m} y^{(i)}(j) \log f_{w}(j \mid x^{(i)}) = -\log f_{w}(c^{(i)}\mid x^{(i)}).
$$

Therefore the empirical loss is

$$
L_{n}(w) = \frac{1}{n}\sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) = -\frac{1}{n}\sum_{i=1}^{n} \log f_{w}(c^{(i)}\mid x^{(i)}) = \frac{1}{n}\left(-\log p(C_{n} \mid X_{n}, w)\right).
$$

Since the negative log-likelihood is $n \cdot L_{n}(w)$, a positive multiple of the empirical loss, we conclude

$$
\operatorname*{arg\,max}_{w\in\mathcal{W}}p(C_{n} \mid X_{n}, w) = \operatorname*{arg\,min}_{w\in\mathcal{W}}L_{n}(w).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.5 (Maximum likelihood as loss minimisation, in general).** Consider a neural network architecture with a parameter space $\mathcal{W}$, parameter–function map $\Phi$, and output space $\mathcal{Y} = \mathbb{R}^{m}$. Let $L_{x,y}: \mathcal{W} \to \mathbb{R}$ be a per-example loss function. Assume that for each $x \in \mathcal{X}$ and $w \in \mathcal{W}$, the function $y \mapsto \exp(-L_{x,y}(w))$ is integrable over $\mathcal{Y}$. Define a corresponding statistical model with parameter–distribution map $\Psi$ mapping $w \in \mathcal{W}$ to $p_{w} : \mathcal{X} \to \Delta(\mathcal{Y})$ such that for all $y \in \mathcal{Y}$, $x \in \mathcal{X}$, and $w \in \mathcal{W}$, we have

$$
p(y \mid x, w) = \frac{\exp\!\left(- L_{x,y}(w)\right)}{Z(x,w)}, \qquad Z(x,w) = \int_{\mathcal{Y}}\exp\!\left(- L_{x,z}(w) \right)dz .
$$

We re-use the notation $X_{n}$, $Y_{n}$ from [[#^ex-nll-mse|Exercise 1.3]], and assume that labels are sampled independently.

**(a)** Show that the negative log-likelihood decomposes as

$$
-\log p(Y_{n} \mid X_{n}, w) = \sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) + \sum_{i=1}^{n} \log Z(x^{(i)}, w) .
$$

**(b)** Now suppose the loss function takes the form $L_{x,y}(w) = \ell(f_{w}(x) - y)$ for some integrable function $\ell : \mathbb{R}^{m} \to \mathbb{R}$. Show that $Z(x, w)$ is independent of $w$, and conclude that

$$
\operatorname*{arg\,max}_{w \in \mathcal{W}}p(Y_{n} \mid X_{n}, w) = \operatorname*{arg\,min}_{w \in \mathcal{W}}L_{n}(w) .
$$
:::

^ex-nll-energy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since labels are sampled independently, the likelihood factorises as

$$
p(Y_{n} \mid X_{n}, w) = \prod_{i=1}^{n} p(y^{(i)}| x^{(i)}, w) = \prod_{i=1}^{n} \frac{\exp\!\left(-L_{x^{(i)},y^{(i)}}(w)\right)}{Z(x^{(i)}, w)}.
$$

Taking the negative logarithm,

$$
\begin{aligned}-\log p(Y_{n} \mid X_{n}, w)&= -\sum_{i=1}^{n} \left[ -L_{x^{(i)},y^{(i)}}(w) - \log Z(x^{(i)}, w) \right] \\&= \sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) + \sum_{i=1}^{n} \log Z(x^{(i)}, w).\end{aligned}
$$
2. Suppose $L_{x,y}(w) = \ell(f_{w}(x) - y)$. Making the substitution $u = f_{w}(x) - z$ (so that $dz = du$) in the definition of the partition function,

$$
Z(x, w) = \int_{\mathbb{R}^m}\exp\!\left(-\ell(f_{w}(x) - z)\right) dz = \int_{\mathbb{R}^m}\exp\!\left(-\ell(u)\right) du.
$$

The right-hand side is a constant independent of both $x$ and $w$. Therefore, by part (a), the negative log-likelihood is

$$
-\log p(Y_{n} \mid X_{n}, w) = \sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) + C = n \cdot L_{n}(w) + C
$$

where $C = n \log \int_{\mathbb{R}^m}\exp(-\ell(u))\,du$ is independent of $w$. Since the negative log-likelihood is an affine function of $L_{n}(w)$ with positive coefficient,

$$
\operatorname*{arg\,max}_{w\in\mathcal{W}}p(Y_{n} \mid X_{n}, w) = \operatorname*{arg\,min}_{w\in\mathcal{W}}L_{n}(w).
$$

:::

:::callout {title="Note" tone="blue"}

**Remark (Negative log-likelihood loss).** Examples [[#^ex-nll-mse|1.3]], [[#^ex-nll-cross-entropy|1.4]], and [[#^ex-nll-energy|1.5]] nominally show that some maximum likelihood estimation problems have the same sets of ideal solutions as some carefully-chosen optimisation problems ($\operatorname*{arg\,min} = \operatorname*{arg\,max}$). In general, that the global optima for two optimisation problems coincide is insufficient to show that practical optimisation methods will always find the same solutions: practical optimisation methods don't always find global optima. However, in the above cases, your derivation likely reveals a stronger result: the optimisation landscapes for the function approximation problem are related to the optimisation landscape for the maximum likelihood estimation problem by a strictly monotonically decreasing transform (an affine transform of a logarithm).

:::

\### 1.4 Bayesian deep learning

The principle of maximum likelihood, explored in the preceding exercises, is one approach to statistical inference. An alternative approach is **Bayesian inference**, which treats $w$ as a random variable and maintains a probability distribution over $\mathcal{W}$ reflecting our uncertainty about which parameter best explains the data. The majority of theoretical results in SLT have been developed within this setting ([[#^bib-watanabe2009|Watanabe 2009]]; [[#^bib-watanabe2018|Watanabe 2018]], cf.,).

Bayesian learning begins with a **prior** distribution $\varphi \in \Delta(\mathcal{W})$, a probability density on $\mathcal{W}$ representing our beliefs about the parameter $w$ before observing any data. Throughout this tutorial, we assume $\varphi$ is positive and smooth on $\mathcal{W}$.

:::callout {title="Definition" tone="purple"}

**Definition 1.5 (Posterior distribution, partition function, free energy).** Given a data set of $n$ input–output pairs $(x^{(1)}, y^{(1)}),$ $\ldots,$ $(x^{(n)}, y^{(n)}) \in \mathcal{X} \times \mathcal{Y}$, Bayes' rule updates the prior into the **posterior distribution** $\pi_{n} \in \Delta(\mathcal{W})$, a probability density on $\mathcal{W}$ defined by


$$
\pi_{n}(w) = \frac{1}{Z_{n}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w)
$$


^eq-posterior


where $Z_{n} \in \mathbb{R}$ is a normalising constant called the **partition function** (or **marginal likelihood** or **model evidence**),


$$
Z_{n} = \int_{\mathcal{W}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w)\, dw.
$$


^eq-partition-function


We often work with the **(Bayesian) free energy**, the negative log of the model evidence,


$$
F_{n} = -\log Z_{n}.
$$


^eq-free-energy


:::

^def-posterior


The posterior re-weights the prior by the likelihood of the observed data: parameters $w$ under which the data is more probable receive higher posterior density, while parameters under which the data is improbable are down-weighted.

The partition function $Z_{n}$ is the marginal probability of observing the data set, averaged over all parameters weighted by the prior. It quantifies how well the statistical model *as a whole* predicts the observed data. The free energy is an inverted measure of how well the model fits the data.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.6 (Bayesian posterior as a Gibbs distribution).** To interpret Bayesian inference in terms more similar to function approximation, we introduce a loss function based on the **negative log-likelihood**,


$$
\begin{aligned}L_{x,y}(w)&= -\log p(y \mid x, w), \\ L_{n}(w)&= -\frac{1}{n}\sum_{i=1}^{n}\log p(y^{(i)}\mid x^{(i)}, w).\end{aligned}
$$


^eq-nll-loss


Here, $p(y \mid x, w)$ is the conditional density from the parameter–distribution map and $(x^{(1)}, y^{(1)}),$ $\ldots,$ $(x^{(n)}, y^{(n)}) \in \mathcal{X} \times \mathcal{Y}$ is a data set of $n$ examples. Show that

$$
\pi_{n}(w) = \frac{1}{Z_{n}}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)
$$

and

$$
Z_{n} = \int_{\mathcal{W}}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)\, dw.
$$
:::

^ex-gibbs


:::callout {title="Solution" tone="neutral" collapse="closed"}

By definition of the negative log-likelihood,

$$
n L_{n}(w) = -\sum_{i=1}^{n}\log p(y^{(i)}\mid x^{(i)}, w).
$$

Exponentiating both sides,

$$
\exp\!\big({-}n L_{n}(w)\big) = \exp\!\left(\sum_{i=1}^{n}\log p(y^{(i)}\mid x^{(i)}, w)\right) = \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w).
$$

Substituting into the definitions of the posterior [[#^eq-posterior|(13)]] and partition function [[#^eq-partition-function|(14)]] gives the stated expressions.

:::

The **Bayesian deep learning process** is the process of re-weighting each individual parameter vector in response to seeing an increasing amount of data, producing the sequence of belief distributions $\varphi, \pi_{1}, \pi_{2}, \ldots \in \Delta(\mathcal{W})$. Over time, the posterior will concentrate around parameters which provide a good fit for the data (though there is more to the story in the singular case, as we will see in later sections).

Bayesian deep learning is a *global search* in that all parameter vectors are considered in parallel. This makes exact Bayesian learning computationally intractable for non-trivial models, but more analytically tractable than SGD in general. Moreover, as we will explore in later sections, the dynamics of Bayesian learning still reflect the local geometry of the parameter–distribution map.

In preparation for exploring this connection between geometry and learning we finally introduce localised variants of the partition function and free energy, where the integral in ([[#^eq-partition-function|14]]) is restricted to a certain neighbourhood in parameter space.

:::callout {title="Definition" tone="purple"}

**Definition 1.6 (Local partition function and local free energy).** Given a neighbourhood $\mathcal{U} \subseteq \mathcal{W}$, the **local partition function** and **local free energy** are


$$
Z_{n}(\mathcal{U}) = \int_{\mathcal{U}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w)\, dw, \qquad F_{n}(\mathcal{U}) = -\log Z_{n}(\mathcal{U}).
$$


^eq-local-free-energy


:::

^def-local-free-energy


The local partition function (free energy) measures how well (poorly) parameters within a given neighbourhood collectively explain the data. Note, $Z_{n}(\mathcal{W}) = Z_{n}$ and $F_{n}(\mathcal{W}) = F_{n}$.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.7 (Local posterior mass and local free energy).** Let $\mathcal{U}, \mathcal{V} \subseteq \mathcal{W}$ be two neighbourhoods of parameter space. Let $\pi_{n}(\mathcal{U}) = \int_{\mathcal{U}}\pi_{n}(w) \,dw$ denote the posterior mass of a neighbourhood. Show the following.

**(a)** $\displaystyle \pi_{n}(\mathcal{U}) = \frac{Z_{n}(\mathcal{U})}{Z_{n}}$ (the same holds for $\mathcal{V}$).

**(b)** $\displaystyle \log \frac{\pi_{n}(\mathcal{U})}{\pi_{n}(\mathcal{V})}= F_{n}(\mathcal{V}) - F_{n}(\mathcal{U})$.

In conclusion, the posterior odds ratio of the two regions $\pi_{n}(\mathcal{U}) / \pi_{n}(\mathcal{V})$ depends exponentially on the difference between their local free energies.
:::

^ex-posterior-free-energy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Integrating the posterior [[#^eq-posterior|(13)]] over $\mathcal{U}$,

$$
\pi_{n}(\mathcal{U}) = \int_{\mathcal{U}}\pi_{n}(w) \, dw = \int_{\mathcal{U}}\frac{1}{Z_{n}}\varphi(w) \prod_{i=1}^{n}p(y^{(i)}\mid x^{(i)}, w) \, dw = \frac{Z_{n}(\mathcal{U})}{Z_{n}}.
$$
2. By part (a),

$$
\log \frac{\pi_{n}(\mathcal{U})}{\pi_{n}(\mathcal{V})}= \log \frac{Z_{n}(\mathcal{U}) / Z_{n}}{Z_{n}(\mathcal{V}) / Z_{n}}= \log Z_{n}(\mathcal{U}) - \log Z_{n}(\mathcal{V}) = F_{n}(\mathcal{V}) - F_{n}(\mathcal{U}).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.8 (Partition function of partitioned parameter space).** Let $\mathcal{U}_{1}, \ldots, \mathcal{U}_{k} \subseteq \mathcal{W}$ be disjoint subsets with $\mathcal{W} = \mathcal{U}_{1} \sqcup \cdots \sqcup \mathcal{U}_{k}$.

**(a)** Show that the partition function decomposes as $Z_{n} = \sum_{j=1}^{k} Z_{n}(\mathcal{U}_{j})$, and hence

$$
F_{n} = -\log \sum_{j=1}^{k} e^{-F_n(\mathcal{U}_j)}.
$$

**(b)** Show that if $F_{n}(\mathcal{U}_{1}) < F_{n}(\mathcal{U}_{j})$ for all $j \neq 1$, then

$$
F_{n}(\mathcal{U}_{1}) - \log k < F_{n} < F_{n}(\mathcal{U}_{1}).
$$

In conclusion, the overall free energy is dominated by the region(s) with the lowest local free energy.
:::

^ex-partition-decomposition


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since $\mathcal{U}_{1}, \ldots, \mathcal{U}_{k}$ are disjoint and cover $\mathcal{W}$, the integral over $\mathcal{W}$ decomposes as a sum of integrals over each $\mathcal{U}_{j}$:

$$
\begin{aligned}Z_{n}&= \int_{\mathcal{W}}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)\, dw \\&= \sum_{j=1}^{k}\int_{\mathcal{U}_j}\varphi(w) \exp\!\big({-}n L_{n}(w)\big)\, dw = \sum_{j=1}^{k}Z_{n}(\mathcal{U}_{j}).\end{aligned}
$$

By definition, $Z_{n}(\mathcal{U}_{j}) = e^{-F_n(\mathcal{U}_j)}$, so $Z_{n} = \sum_{j=1}^{k}e^{-F_n(\mathcal{U}_j)}$. Taking $-\log$ of both sides,

$$
F_{n} = -\log Z_{n} = -\log \sum_{j=1}^{k}e^{-F_n(\mathcal{U}_j)}.
$$
2. Since $F_{n}(\mathcal{U}_{1}) < F_{n}(\mathcal{U}_{j})$ for all $j \neq 1$, the corresponding partition functions satisfy $Z_{n}(\mathcal{U}_{1}) > Z_{n}(\mathcal{U}_{j})$ for all $j \neq 1$. The lower bound on $Z_{n}$ is immediate:

$$
Z_{n} = \sum_{j=1}^{k}Z_{n}(\mathcal{U}_{j}) > Z_{n}(\mathcal{U}_{1}).
$$

For the upper bound, since each $Z_{n}(\mathcal{U}_{j}) < Z_{n}(\mathcal{U}_{1})$,

$$
Z_{n} = \sum_{j=1}^{k}Z_{n}(\mathcal{U}_{j}) < k \cdot Z_{n}(\mathcal{U}_{1}).
$$

Taking $-\log$ (which reverses the inequalities) yields

$$
F_{n}(\mathcal{U}_{1}) - \log k < F_{n} < F_{n}(\mathcal{U}_{1}).
$$

The overall free energy is therefore determined by the region with the lowest local free energy, up to a correction of at most $\log k$. In particular, if the gap $F_{n}(\mathcal{U}_{j}) - F_{n}(\mathcal{U}_{1})$ grows with $n$ while $k$ remains fixed, then $F_{n} \to F_{n}(\mathcal{U}_{1})$.

:::

\## 2. What is degeneracy?

In this section, we define degeneracy as a property of parameter–function maps, and study the relationship between this property and other similar notions.

\### 2.1 A definition of degeneracy

Consider a neural network architecture with parameter space $\mathcal{W} \subseteq \mathbb{R}^{d}$ and parameter–function map $\Phi : \mathcal{W} \to \mathcal{F}$ ($w \mapsto f_{w}$). Say the parameter–function map is **degenerate at $w\in\mathcal{W}$** if there is a non-zero vector $v \in \mathbb{R}^{d}$ such that the directional derivative of the parameter–function map in the direction $v$ is zero:


$$
D_{v} \Phi(w) = 0.
$$


^eq-degeneracy


The directional derivative $D_{v} \Phi(w)$ for non-zero $v \in \mathbb{R}^{d}$ may be defined variously as


$$
D_{v} \Phi(w) = \frac{v}{\|v\|}\cdot \nabla \Phi(w) = \sum_{i=1}^{d} \frac{v_{i}}{\|v\|}\frac{\partial \Phi}{\partial w_{i}}(w) = \lim_{\epsilon \to 0}\frac{\Phi(w + \epsilon v) - \Phi(w)}{\epsilon\|v\|}.
$$


^eq-directional-derivative


We conventionally define $D_{0} \Phi(w) = 0$. Note that $w$ is fixed, but the directional derivative is still a function (of the same type as $\Phi(w)$; $D_{v} \Phi(w) : \mathcal{X} \to \mathcal{Y}$), since it represents an infinitesimal change in $\Phi(w)$ in response to a change in $w$ in the direction $v$. In [[#^eq-degeneracy|(19)]] we mean that this function is identically zero for all inputs $x \in \mathcal{X}$ for the given $w \in \mathcal{W}$.

Intuitively, the parameter–function map is degenerate at $w \in \mathcal{W}$ if there is a direction in which we can infinitesimally perturb $w$ without changing the function $f_{w}$.

This definition of degeneracy applies to a single point in parameter space. As we shall soon see, it may be the case that the parameter–function map is degenerate at some points but not at others. We can clarify the situation with new terminology.

- We say that a parameter–function map is **somewhere degenerate** if it is degenerate at *any* point in parameter space.
- We say that a parameter–function map is **everywhere degenerate** if it is degenerate at *all* points in parameter space.

By convention, if we say that the parameter–function map is simply **degenerate** (without specifying somewhere, everywhere, or at a particular point), we mean that it is *somewhere degenerate*.

The following exercises explore this definition in some toy parametrisations of a simple function class (constants), displaying in the simplest possible setting some basic forms of degeneracy that will arise repeatedly throughout the tutorial.

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.1 (Parametrising the space of constants).** Let $\mathcal{X} = \{\ast\}$ and $\mathcal{Y} = \mathbb{R}$, so that we have a hypothesis class of constants. Consider the scalar parameter space $\mathcal{W} = \mathbb{R}$ and the parameter function map that maps $w$ to $f_{w} = w$ (the output is just the parameter itself).

**(a)** What is the directional derivative of the parameter–function map in direction $v = 1$?
::::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

::::

**(b)** At which points in the parameter space is this parameter–function map degenerate, if any?
:::::

^ex-univariate-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since $\mathcal{W} = \mathbb{R}$ is one-dimensional, the directional derivative in direction $v = 1$ reduces to the ordinary derivative:

$$
\frac{\partial \Phi}{\partial w}= \frac{d}{dw}w = 1.
$$
2. The directional derivative is $1 \neq 0$ for all $w \in \mathcal{W}$. Therefore, the parameter–function map is *not degenerate* at any point.

:::

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.2 (Degeneracy from raising a parameter to a power).** Again, consider a hypothesis class of constants and the scalar parameter space $\mathcal{W} = \mathbb{R}$. This time, define a parameter function map that maps $w$ to $f_{w} = w^{3}$.

**(a)** Show that this architecture indexes exactly the same hypothesis class as the architecture described in [[#^ex-univariate-degeneracy|Exercise 2.1]].

**(b)** What is the directional derivative of the parameter–function map in direction $v = 1$?
::::callout {title="Hint" tone="neutral" collapse="closed"}

What kind of derivative does this reduce to?

::::

**(c)** At which points in the parameter space is the parameter–function map degenerate, if any?
:::::

^ex-cubic-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. The hypothesis class of [[#^ex-univariate-degeneracy|Exercise 2.1]] is $\mathcal{F} = \{f_{w} = w : w \in \mathbb{R}\} = \mathbb{R}$. The hypothesis class here is $\mathcal{F} = \{f_{w} = w^{3} : w \in \mathbb{R}\}$. Since $w \mapsto w^{3}$ is a bijection on $\mathbb{R}$, as $w$ ranges over $\mathbb{R}$, $w^{3}$ takes every real value exactly once. So $\mathcal{F} = \mathbb{R}$ in both cases.
2. The directional derivative in direction $v = 1$ is the ordinary derivative:

$$
\frac{\partial \Phi}{\partial w}= \frac{d}{dw}w^{3} = 3w^{2}.
$$
3. The directional derivative $3w^{2} = 0$ if and only if $w = 0$. So the parameter–function map is degenerate at $w = 0$ only. It is somewhere degenerate but not everywhere degenerate.

:::

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.3 (Degeneracy from multiplying two parameters together).** Again, consider a hypothesis class of constants. Consider this time the two-dimensional parameter space $\mathcal{W} = \mathbb{R}^{2}$. Define a parameter function map that maps $w = (a, b)$ to $f_{w} = a \cdot b$.

**(a)** Show that this architecture indexes exactly the same hypothesis class as the architecture described in [[#^ex-univariate-degeneracy|Exercise 2.1]].

**(b)** What is the directional derivative of the parameter–function map in direction $v = (1, 0)$?
::::callout {title="Hint" tone="neutral" collapse="closed"}

what kind of derivative does this reduce to?

::::

**(c)** What is the directional derivative of the parameter–function map in direction $v = (0, 1)$?
::::callout {title="Hint" tone="neutral" collapse="closed"}

what kind of derivative does this reduce to?

::::

**(d)** At which points in the parameter space is the parameter–function map degenerate *in these directions,* if any?

**(e)** At which points in the parameter space is the parameter–function map degenerate, if any?
:::::

^ex-product-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. The hypothesis class is $\mathcal{F} = \{f_{w} = ab : (a, b) \in \mathbb{R}^{2}\} = \mathbb{R}$, since for any target $c \in \mathbb{R}$ we can choose, e.g., $a = c$ and $b = 1$. This is the same as in [[#^ex-univariate-degeneracy|Exercise 2.1]].
2. The directional derivative in direction $v = (1, 0)$ is the partial derivative with respect to $a$:

$$
\frac{\partial \Phi}{\partial a}= \frac{\partial}{\partial a}(ab) = b.
$$
3. The directional derivative in direction $v = (0, 1)$ is the partial derivative with respect to $b$:

$$
\frac{\partial \Phi}{\partial b}= \frac{\partial}{\partial b}(ab) = a.
$$
4. From parts (b) and (c), the direction $(1, 0)$ is degenerate at $(a, b)$ if and only if $b = 0$, and the direction $(0, 1)$ is degenerate if and only if $a = 0$. So the parameter–function map is degenerate in at least one of these coordinate directions precisely on the set $\{(a, b) : a = 0 \text{ or }b = 0\}$, i.e. the union of the two coordinate axes.
5. The directional derivative in a general direction $v = (v_{1}, v_{2})$ is proportional to

$$
v_{1} \frac{\partial \Phi}{\partial a}+ v_{2} \frac{\partial \Phi}{\partial b}= v_{1} b + v_{2} a.
$$

This is a single linear equation in two unknowns $(v_{1}, v_{2})$.

- If $a = b = 0$: the equation $0 = 0$ is trivially satisfied, so every direction is degenerate.
- If $(a, b) \neq (0, 0)$: the coefficient vector $(b, a)$ is nonzero, so the solution space is one-dimensional. A nonzero solution is $v = (-a, b)$: indeed, $(-a) b + b \cdot a = 0$.

Therefore, the parameter–function map is degenerate *everywhere*. Note that the previous part found degeneracy only on the coordinate axes because it checked only the coordinate directions. Checking for parameter–function map degeneracy requires checking all possible directions.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.4 (Degeneracy from adding two parameters together).** Again, consider a hypothesis class of constants. Consider this time the two-dimensional parameter space $\mathcal{W} = \mathbb{R}^{2}$. Define a parameter function map that maps $w = (a, b)$ to $f_{w} = a + b$.

**(a)** Show that this architecture indexes exactly the same hypothesis class as the architecture described in [[#^ex-univariate-degeneracy|Exercise 2.1]].

**(b)** What is the directional derivative of the parameter–function map in direction $v = (1, -1)$?

**(c)** At which points in the parameter space is the parameter–function map degenerate, if any?
:::

^ex-sum-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. The hypothesis class is $\mathcal{F} = \{f_{w} = a + b : (a, b) \in \mathbb{R}^{2}\} = \mathbb{R}$, since for any target $c \in \mathbb{R}$ we can choose, e.g., $a = c$ and $b = 0$. This is the same as in [[#^ex-univariate-degeneracy|Exercise 2.1]].
2. The direction $v = (1, -1)$ has $\|v\| = \sqrt{2}$, so by [[#^eq-directional-derivative|(20)]] the directional derivative is

$$
\frac{1}{\sqrt{2}}\left( 1 \cdot \frac{\partial}{\partial a}(a + b) + (-1) \cdot \frac{\partial}{\partial b}(a + b) \right) = \frac{1}{\sqrt{2}}(1 - 1) = 0.
$$
3. The direction $v = (1, -1)$ gives a zero directional derivative at *every* point $(a, b) \in \mathcal{W}$. Therefore, the parameter–function map is everywhere degenerate. This reflects the fact that the map $(a, b) \mapsto a + b$ has a global continuous symmetry: translating along the direction $(1, -1)$ does not change the output.

:::

\### 2.2 Degeneracy and continuous symmetries

A common source of degeneracy in neural network architectures is the presence of continuous symmetries of the parameter–function map. A continuous symmetry traces out a curve of functionally equivalent parameters. The tangent to this curve is a degenerate direction. In this section, we will explore this kind of symmetry and some examples from deep learning.

A **symmetry** of a parameter–function map $\Phi$ is a transformation of parameter space that maps parameters while preserving the implemented function. That is, a transformation $T : \mathcal{W} \to \mathcal{W}$ is a symmetry if for all $w \in \mathcal{W}$, we have $\Phi(w) = \Phi(T(w))$ ($f_{w} = f_{T(w)}$).

A **continuous symmetry** of a parameter–function map $\Phi$ is a family of transformations $\{T_{t} : \mathcal{W} \to \mathcal{W}\}_{t \in \mathbb{R}}$ indexed by a parameter $t\in\mathbb{R}$, such that

1. $T_{t}$ is a symmetry ($\Phi \circ T_{t} = \Phi$) for all $t \in \mathbb{R}$,
2. $T_{0}$ is the identity transformation on $\mathcal{W}$, and
3. The map $t \mapsto T_{t}(w)$ is differentiable for each $w \in \mathcal{W}$.

The continuous symmetry is **trivial at $w$** if $\left.\frac{d}{dt}\right|_{t=0}T_{t}(w) = 0$, or else **non-trivial at $w$**.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.5 (Continuous symmetry example).** Recall the parameter–function map from [[#^ex-sum-degeneracy|Exercise 2.4]], with $\mathcal{W} = \mathbb{R}^{2}$ and with $(a, b) \in \mathcal{W}$ mapping to the constant function $f_{a,b}= a + b$. Consider the family of transformations $T_{t} : \mathcal{W} \to \mathcal{W}$ for $t \in \mathbb{R}$ such that

$$
T_{t}(a, b) = (a + t, b - t).
$$

**(a)** Describe the effect of this family of transformations on the parameter space.

**(b)** Show that this family of transformations is a continuous symmetry.

**(c)** Show that this continuous symmetry is non-trivial everywhere.
:::

^ex-sum-symmetry


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. The transformation $T_{t}$ translates the parameter $(a, b)$ by $t$ in the direction $(1, -1)$. The orbit of any parameter $(a, b)$ under this family is the line $\{(a + t, b - t) : t \in \mathbb{R}\}$, which has slope $-1$ in the $(a, b)$-plane.
2. We verify the three conditions of a continuous symmetry.

1. Symmetry: $\Phi(T_{t}(a, b)) = (a + t) + (b - t) = a + b = \Phi(a, b)$ for all $(a, b)$ and $t$.
2. Identity: $T_{0}(a, b) = (a + 0, b - 0) = (a, b)$.
3. Differentiability: $t \mapsto T_{t}(a, b) = (a + t, b - t)$ is linear in $t$, hence differentiable.
3. We have $\frac{d}{dt}T_{t}(a, b) = (1, -1)$ for all $t$. In particular, $\left.\frac{d}{dt}\right|_{t=0}T_{t}(a, b) = (1, -1) \neq (0, 0)$ for every $(a, b) \in \mathcal{W}$. So the symmetry is non-trivial at every parameter.

:::

At each parameter, a non-trivial continuous symmetry traces out a curve of functionally equivalent parameters. This indicates the presence of a direction in parameter space in which the function does not change. The following proposition formalises this connection between continuous symmetries and degeneracy.

:::callout {title="Theorem" tone="purple"}

**Proposition 2.1.** If a parameter–function map $\Phi$ admits a continuous symmetry $\{T_{t}\}$ that is non-trivial at $w$, then $\Phi$ is degenerate at $w$.

:::

^prop-symmetry-degeneracy


:::callout {title="Proof" tone="green" collapse="closed"}

Define the curve in parameter space traced by the continuous symmetry, $\gamma : \mathbb{R} \to \mathcal{W}$ with $\gamma(t) = T_{t}(w)$. Since $T_{t}$ is a continuous symmetry, the derivative along the curve vanishes for all $t$:

$$
\begin{aligned}D_{\gamma'(t)}\Phi(\gamma(t))&\propto \gamma'(t) \cdot \nabla \Phi(\gamma(t)) \\&= \frac{d}{dt}\Phi(\gamma(t)) \quad\text{(chain rule)}\\&= \frac{d}{dt}\Phi(w) \quad\text{(symmetry, $\Phi \circ T_{t} = \Phi$)}\\&= 0. \quad\text{($\Phi(w)$ is constant in $t$)}\end{aligned}
$$

In particular, at $t=0$, we have $0 = D_{\gamma'(0)}\Phi(\gamma(0)) = D_{\gamma'(0)}\Phi(w)$ since $\gamma(0) = w$ by identity. Since $T_{t}$ is non-trivial at $w$, $\gamma'(0)$ is non-zero, so $\gamma'(0)$ is a degenerate direction at $w$.

:::

:::callout {title="Theorem" tone="purple"}

**Corollary 2.2.** If a parameter–function map $\Phi$ admits a continuous symmetry $\{T_{t}\}$ that is non-trivial at every parameter $w \in \mathcal{W}$, then $\Phi$ is everywhere degenerate.

:::

The following exercises exhibit some continuous symmetries in two neural network architectures, a small ReLU MLP and a toy autoencoder. Similar architectures are studied in more detail from an SLT perspective by [[#^bib-carroll2021|Carroll 2021]] and [[#^bib-chen-2023|Chen et al. 2023]] respectively.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.6 (ReLU scaling symmetry).** Consider a two-layer MLP ([[#^eg-mlp|Example 1.4]]) with $\sigma = \mathrm{relu}$, scalar inputs and outputs ($m = 1$), and a single hidden unit ($h = 1$). The parameter space is $\mathcal{W} = \mathbb{R}^{2}$ with parameters $(a, b)$, and the parameter–function map is $f_{a,b}(x) = b \cdot \mathrm{relu}(ax)$.

**(a)** Show that $\mathrm{relu}$ is *positively homogeneous*: $\mathrm{relu}(\alpha z) = \alpha \, \mathrm{relu}(z)$ for all $\alpha > 0$ and $z \in \mathbb{R}$.

**(b)** Define $T_{t}(a, b) = (e^{t} a, \, e^{-t}b)$ for $t \in \mathbb{R}$. Show that $\{T_{t}\}$ is a continuous symmetry of this parameter–function map.

**(c)** For a fixed parameter $(a, b) \neq (0, 0)$, compute the degenerate direction arising from this symmetry at $(a, b)$.

**(d)** Show that the symmetry is trivial at the origin. Is this parameter–function map degenerate at the origin?
:::

^ex-relu-scaling


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. We consider three cases. If $z > 0$, then $\alpha z > 0$ (since $\alpha > 0$), so $\mathrm{relu}(\alpha z) = \alpha z = \alpha \mathrm{relu}(z)$. If $z = 0$, then $\mathrm{relu}(\alpha \cdot 0) = 0 = \alpha \cdot 0 = \alpha \mathrm{relu}(z)$. If $z < 0$, then $\alpha z < 0$, so $\mathrm{relu}(\alpha z) = 0 = \alpha \cdot 0 = \alpha \mathrm{relu}(z)$.
2. We verify the three conditions.

1. Symmetry: using positive homogeneity with $\alpha = e^{t} > 0$,

$$
f_{T_t(a,b)}(x) = e^{-t}b \cdot \mathrm{relu}(e^{t} a x) = e^{-t}b \cdot e^{t} \mathrm{relu}(ax) = b \cdot \mathrm{relu}(ax) = f_{a,b}(x).
$$
2. Identity: $T_{0}(a, b) = (e^{0} a,\, e^{0} b) = (a, b)$.
3. Differentiability: $t \mapsto (e^{t} a,\, e^{-t}b)$ is smooth.
3. The degenerate direction at $(a, b)$ is

$$
\left.\frac{d}{dt}\right|_{t=0}T_{t}(a, b) = \left.\frac{d}{dt}\right|_{t=0}(e^{t} a,\, e^{-t}b) = (a, -b).
$$

Since $(a, b) \neq (0, 0)$, we have $(a, -b) \neq (0, 0)$, so this is a non-zero degenerate direction.
4. At $(a, b) = (0, 0)$, we have $\left.\frac{d}{dt}\right|_{t=0}T_{t}(0, 0) = (0, 0)$, so the symmetry is trivial.

The parameter–function map is nonetheless degenerate at the origin. Both partial derivatives of $\Phi$ vanish there:

$$
\begin{aligned}\frac{\partial}{\partial a}f_{a,b}(x) \bigg|_{(0,0)}&= \lim_{\epsilon \to 0}\frac{f_{\epsilon, 0}(x) - f_{0,0}(x)}{\epsilon}= \lim_{\epsilon \to 0}\frac{0 \cdot \mathrm{relu}(\epsilon x)}{\epsilon}= 0, \\ \frac{\partial}{\partial b}f_{a,b}(x) \bigg|_{(0,0)}&= \mathrm{relu}(0 \cdot x) = 0.\end{aligned}
$$

Since $\nabla \Phi(0,0) = 0$, every direction is degenerate at the origin. This degeneracy is not explained by the scaling symmetry.

:::

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.7 (Rotation symmetry in a linear autoencoder).** Consider a *linear autoencoder* with bottleneck dimension $h$ and ambient dimension $m \geq h$. The parameter space encodes a single matrix $W \in \mathbb{R}^{h \times m}$ and the parameter–function map sends $W$ to the function $\Phi(W) = f_{W} : \mathbb{R}^{m} \to \mathbb{R}^{m}$ where

$$
f_{W}(x) = W^{\top} W x
$$

for $x \in \mathbb{R}^{m}$. Here, $W$ serves simultaneously as encoder ($x \mapsto Wx \in \mathbb{R}^{h}$) and decoder ($z \mapsto W^{\top} z \in \mathbb{R}^{m}$).

**(a)** Show that for any orthogonal matrix $R \in \mathbb{R}^{h \times h}$ (i.e., any $h \times h$ matrix such that $R^{\top} R = I$), the map $T_{R}(W) = RW$ is a symmetry.

**(b)** Specialise to $h = 2$. Using the rotation matrices

$$
R(\theta) = \begin{pmatrix}\cos\theta & -\sin\theta \\ \sin\theta & \cos\theta\end{pmatrix},
$$

show that $T_{\theta}(W) = R(\theta) W$ defines a continuous symmetry.

**(c)** For a fixed parameter $W \in \mathbb{R}^{2 \times m}$, compute the degenerate direction that arises from this symmetry.

**(d)** For general bottleneck dimension $h$, how many independent continuous symmetries does the orthogonal group $O(h)$ contribute?
::::callout {title="Hint" tone="neutral" collapse="closed"}

What is the dimension of $O(h)$?

::::
:::::

^ex-rotation-symmetry


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. For orthogonal $R$ (i.e. $R^{\top} R = I$),

$$
f_{RW}(x) = (RW)^{\top}(RW)x = W^{\top} R^{\top} R\, W x = W^{\top} W x = f_{W}(x).
$$
2. We verify the three conditions.

1. Symmetry: $R(\theta)$ is orthogonal for all $\theta$, since

$$
R(\theta)^{\top} R(\theta) = \begin{pmatrix}\cos\theta & \sin\theta \\ -\sin\theta & \cos\theta\end{pmatrix} \begin{pmatrix}\cos\theta & -\sin\theta \\ \sin\theta & \cos\theta\end{pmatrix} = \begin{pmatrix}1 & 0 \\ 0 & 1\end{pmatrix}.
$$

So $f_{R(\theta)W}= f_{W}$ by part (a).
2. Identity: $R(0) = I$, so $T_{0}(W) = W$.
3. Differentiability: the entries of $R(\theta)W$ are smooth functions of $\theta$ (they involve $\cos\theta$ and $\sin\theta$ multiplied by entries of $W$).
3. The degenerate direction at $W$ is

$$
\left.\frac{d}{d\theta}\right|_{\theta=0}R(\theta) W = R'(0)\, W.
$$

We compute

$$
R'(\theta) = \begin{pmatrix}-\sin\theta & -\cos\theta \\ \cos\theta & -\sin\theta\end{pmatrix}, \qquad R'(0) = \begin{pmatrix}0 & -1 \\ 1 & 0\end{pmatrix}.
$$

Writing $W = \begin{pmatrix}w_{1}^{\top} \\ w_{2}^{\top}\end{pmatrix}$ where $w_{1}, w_{2} \in \mathbb{R}^{m}$ are the two rows, the degenerate direction is the matrix

$$
R'(0)\, W = \begin{pmatrix}-w_{2}^{\top} \\ w_{1}^{\top}\end{pmatrix},
$$

which swaps the two rows and negates one. This direction is non-zero whenever $W \neq 0$.
4. The orthogonal group $O(h)$ consists of all $h \times h$ matrices satisfying $R^{\top} R = I$. This constraint comprises $\frac{h(h+1)}{2}$ independent scalar equations (the entries of the symmetric matrix $R^{\top} R$ on and above the diagonal). Since $R$ has $h^{2}$ entries, the dimension of $O(h)$ is

$$
h^{2} - \frac{h(h+1)}{2}= \frac{h(h-1)}{2}.
$$

Each independent direction in $O(h)$ at the identity gives rise to a one-parameter continuous symmetry and hence a degenerate direction at each $W$. These directions are the $h \times h$ skew-symmetric matrices $S$ (satisfying $S^{\top} = -S$), since differentiating $R(t)^{\top} R(t) = I$ at $t = 0$ gives $R'(0)^{\top} + R'(0) = 0$. The space of such matrices has dimension $\frac{h(h-1)}{2}$ (the entries strictly above the diagonal are free, and the rest are determined).

So $O(h)$ contributes $\frac{h(h-1)}{2}$ independent continuous symmetries. For $h = 2$ this gives $1$, matching the single rotation symmetry from part (b).

:::

\### 2.3 Localised degeneracy

We have seen that a non-trivial continuous symmetry traces out curves of functionally equivalent parameters throughout the entire parameter space, and the tangent directions to these curves are degenerate directions at every point. However, not all degenerate directions arise from globally continuous symmetries. In fact, the more interesting case is when degeneracy affects only some parameters and not others.

Within certain subsets of parameter space, many neural network architectures (including those studied in [[#^ex-relu-scaling|Exercise 2.6]] and [[#^ex-rotation-symmetry|2.7]]) exhibit degenerate directions that cannot be defined in terms of continuous transformations that are globally symmetries. In this section, we explore localised degeneracies of this kind.

We begin with some examples of transformations that are only continuous symmetries within certain subsets of parameter space.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.8 (Localised symmetry example).** Recall the parameter–function map from [[#^ex-product-degeneracy|Exercise 2.3]], with $\mathcal{W} = \mathbb{R}^{2}$ and with $(a, b) \in \mathcal{W}$ mapping to the constant function $f_{a,b}= a \cdot b$. Consider the two families of transformations $T^{(a)}_{t}, T^{(b)}_{t} : \mathcal{W} \to \mathcal{W}$ for $t \in \mathbb{R}$ such that

$$
T^{(a)}_{t}(a, b) = (a + t, b), \qquad\qquad T^{(b)}_{t}(a, b) = (a, b + t) .
$$

**(a)** Describe the effect of each family of transformations on the parameter space.

**(b)** In which subset of parameter space does each family of transformations constitute a symmetry for all $t\in\mathbb{R}$?

**(c)** Compare your results to your answer to [[#^ex-product-degeneracy|Exercise 2.3(d)]].
:::

^ex-localised-symmetry


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. $T^{(a)}_{t}$ translates along the $a$-axis: it shifts the first coordinate by $t$ while leaving the second fixed. $T^{(b)}_{t}$ translates along the $b$-axis.
2. $T^{(a)}_{t}$ is a symmetry at $(a, b)$ for all $t$ if and only if $f_{a+t,b}= f_{a,b}$ for all $t$, i.e., $(a+t)b = ab$ for all $t$. This simplifies to $tb = 0$ for all $t$, which requires $b = 0$. So $\{T^{(a)}_{t}\}$ is a symmetry when restricted to the $a$-axis $\{(a, 0) : a \in \mathbb{R}\}$.

Similarly, $\{T^{(b)}_{t}\}$ is a symmetry when restricted to the $b$-axis $\{(0, b) : b \in \mathbb{R}\}$.
3. From [[#^ex-product-degeneracy|Exercise 2.3(d)]], the coordinate directions $(1, 0)$ and $(0, 1)$ are degenerate precisely on the coordinate axes: $(1, 0)$ is degenerate on $\{b = 0\}$ and $(0, 1)$ is degenerate on $\{a = 0\}$. This matches exactly: the axis $\{b = 0\}$ is where the $a$-translation symmetry acts, providing the degenerate direction $(1, 0)$, and the axis $\{a = 0\}$ is where the $b$-translation symmetry acts, providing $(0, 1)$.

:::

The above example is technically a two-layer DLN with $m=h=1$. Let us now explore localised degeneracy in a general two-layer DLN and then in a non-trivial MLP.

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.9 (Degeneracy in the two-layer DLN).** Consider the two-layer DLN from [[#^eg-dln|Example 1.3]], with $h=m$. The parameter space encodes two matrices $A, B \in \mathbb{R}^{m \times m}$, and the parameter–function map sends $(A, B)$ to the function $\Phi(A,B) = f_{A,B}: \mathbb{R}^{m} \to \mathbb{R}^{m}$ such that $f_{A,B}(x) = BAx$ for $x \in \mathbb{R}^{m}$.

**(a)** Let $(\delta\!A, \delta\!B)$ be a unit perturbation in parameter space (a unit vector in the underlying parameter space $\mathbb{R}^{2m^2}$, decoded into a pair of matrices). Show that the directional derivative of the parameter–function map at $(A, B)$ in direction $(\delta\!A, \delta\!B)$ is the linear map

$$
D_{(\delta\!A, \delta\!B)}\Phi(A, B) = B\,\delta\!A + \delta\!B\, A.
$$

That is, $D_{(\delta\!A, \delta\!B)}\Phi(A, B) x = (B\,\delta\!A + \delta\!B\, A) x$.
::::callout {title="Hint" tone="neutral" collapse="closed"}

Use the limit definition, [[#^eq-directional-derivative|(20)]].

::::

**(b)** Show that at the zero parameter $(A, B) = (0, 0)$, every direction in parameter space is degenerate. Count the number of dimensions in the subspace of degenerate directions.

**(c)** Suppose both $A$ and $B$ are invertible. Show that $(\delta\!A, \delta\!B)$ is a degenerate direction if and only if $\delta\!B = -B\,\delta\!A\, A^{-1}$. Count the number of dimensions in the subspace of degenerate directions.

**(d)** Now consider the general case. Fix $A$ and $B$, and let $r_{A} = \mathrm{rank}(A)$ and $r_{B} = \mathrm{rank}(B)$. Show that the dimensionality of the space of degenerate directions is

$$
m^{2} + (m-r_{A})(m-r_{B}).
$$

::::callout {title="Hint" tone="neutral" collapse="closed"}

The following is a guide to one possible approach.

1. Describe the image of the linear map $T_{A}$ sending $\delta\!B \in \mathbb{R}^{m^2}$ to $\delta\!B\, A \in \mathbb{R}^{m^2}$ in terms of the row space of $A$. Show that the dimensionality of this image (the rank of the linear map $T_{A}$) is $m r_{A}$.
2. Similarly, describe the image of the linear map $T_{B}$ sending $\delta\!A \in \mathbb{R}^{m^2}$ to $B\, \delta\!A \in \mathbb{R}^{m^2}$ in terms of the column space of $B$. Show that dimensionality of this image (the rank of the linear map $T_{B}$) is $m r_{B}$.
3. Describe the intersection of the images of $T_{A}, T_{B}$ in terms of the row/column spaces of $A, B$. Show that the dimensionality of this intersection is $r_{A} r_{B}$.
4. Consider a third linear map, $T_{D}$, sending $(\delta\!A, \delta\!B) \in \mathbb{R}^{2m^2}$ to $B\,\delta\!A + \delta\!B\, A \in \mathbb{R}^{m^2}$. Describe the image of this linear map in terms of those of $T_{A}$ and $T_{B}$. Compute the rank of this linear map using Grassmann's identity.
5. What is the nullity of $T_{D}$? Why is this the same as the dimensionality of the space of degenerate directions?

::::

^ex-dln-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Encoding $(A, B)$ and $(\delta\!A, \delta\!B)$ as vectors in the underlying parameter space $\mathbb{R}^{2m^2}$, the directional derivative is

$$
D_{(\delta\!A, \delta\!B)}\Phi(A, B)(x) = \lim_{\epsilon \to 0}\frac{ f_{A + \epsilon\delta\!A,\, B + \epsilon\delta\!B}(x) - f_{A,B}(x) }{\epsilon}.
$$

Expanding the matrix product:

$$
\begin{aligned}f_{A + \epsilon\delta\!A,\, B + \epsilon\delta\!B}(x)&= (B + \epsilon\delta\!B)(A + \epsilon\delta\!A)\,x \\&= BAx + \epsilon(B\,\delta\!A + \delta\!B\, A)\,x + \epsilon^{2} \delta\!B\,\delta\!A\, x.\end{aligned}
$$

Subtracting $f_{A,B}(x) = BAx$, dividing by $\epsilon$, and taking $\epsilon \to 0$ gives

$$
D_{(\delta\!A, \delta\!B)}\Phi(A, B)(x) = (B\,\delta\!A + \delta\!B\, A)\,x.
$$
2. At $(A, B) = (0, 0)$, part (a) gives $D_{(\delta\!A, \delta\!B)}\Phi(0, 0)(x) = (0 \cdot \delta\!A + \delta\!B \cdot 0)\,x = 0$ for every $(\delta\!A, \delta\!B)$ and every $x$. Every non-zero direction is therefore degenerate. The subspace of degenerate directions is the entire parameter space $\mathbb{R}^{2m^2}$, which has dimension $2m^{2}$.
3. By part (a), $(\delta\!A, \delta\!B)$ is a degenerate direction if and only if $B\,\delta\!A + \delta\!B\, A = 0$, that is, $\delta\!B\, A = -B\,\delta\!A$. Since $A$ is invertible, right-multiplying by $A^{-1}$ gives $\delta\!B = -B\,\delta\!A\, A^{-1}$. Since $\delta\!A \in \mathbb{R}^{m \times m}$ is free and $\delta\!B$ is uniquely determined, the subspace of degenerate directions has dimension $m^{2}$.
4. 1. The $i$-th row of $\delta\!B\, A$ is $(\delta\!B)_{i} A$, a linear combination of the rows of $A$. Therefore the image of $T_{A}$ consists of all matrices whose rows lie in the row space of $A$. Each of the $m$ rows can be any vector in the $r_{A}$-dimensional row space, so $\mathrm{rank}(T_{A}) = m\,r_{A}$.
2. Similarly, the $j$-th column of $B\,\delta\!A$ is $B\,(\delta\!A)^{j}$, a linear combination of the columns of $B$. The image of $T_{B}$ consists of all matrices whose columns lie in the column space of $B$, and $\mathrm{rank}(T_{B}) = m\,r_{B}$.
3. A matrix lies in $\mathrm{im}(T_{A}) \cap \mathrm{im}(T_{B})$ if and only if its rows lie in the row space of $A$ and its columns lie in the column space of $B$. Such a matrix can be written as $U \Lambda V$ where $U \in \mathbb{R}^{m \times r_B}$ has columns spanning the column space of $B$ and $V \in \mathbb{R}^{r_A \times m}$ has rows spanning the row space of $A$, with $\Lambda \in \mathbb{R}^{r_B \times r_A}$ free. The dimensionality of this intersection is therefore $r_{A}\,r_{B}$.
4. The image of $T_{D}$ is $\mathrm{im}(T_{D}) = \mathrm{im}(T_{B}) + \mathrm{im}(T_{A})$, since for any $(\delta\!A, \delta\!B)$ we have $T_{D}(\delta\!A, \delta\!B) = T_{B}(\delta\!A) + T_{A}(\delta\!B)$, and conversely any element of $\mathrm{im}(T_{B}) + \mathrm{im}(T_{A})$ can be realised by choosing appropriate $\delta\!A$ and $\delta\!B$. By Grassmann's identity,

$$
\begin{aligned}\mathrm{rank}(T_{D})&= \dim(\mathrm{im}(T_{A}) + \mathrm{im}(T_{B})) \\&= \mathrm{rank}(T_{A}) + \mathrm{rank}(T_{B}) - \dim(\mathrm{im}(T_{A}) \cap \mathrm{im}(T_{B})) \\&= m\,r_{A} + m\,r_{B} - r_{A}\,r_{B}.\end{aligned}
$$
5. By the rank–nullity theorem, the nullity of $T_{D}$ is

$$
\begin{aligned}&\mathrel{\phantom{=}}2m^{2} - (m\,r_{A} + m\,r_{B} - r_{A}\,r_{B}) \\&= 2m^{2} - m\,r_{A} - m\,r_{B} + r_{A}\,r_{B} \\&= m^{2} + (m - r_{A})(m - r_{B}).\end{aligned}
$$

The kernel of $T_{D}$ is exactly the set of $(\delta\!A, \delta\!B)$ such that $B\,\delta\!A + \delta\!B\, A = 0$, which by part (a) is precisely the subspace of degenerate directions.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.10 (Redundant units in an MLP).** Consider a single-hidden-layer MLP with scalar inputs and outputs, $h$ hidden units with activation function $\sigma : \mathbb{R} \to \mathbb{R}$, and an output bias. The parameter space is $\mathcal{W} = \mathbb{R}^{3h+1}$ with parameters $w = (a_{1}, b_{1}, c_{1}, \ldots, a_{h}, b_{h}, c_{h}, d)$, and the parameter–function map is

$$
f_{w}(x) = d + \sum_{i=1}^{h}a_{i} \, \sigma(b_{i} x + c_{i}).
$$

Here, for each hidden unit $i$, $a_{i}$ is the outgoing weight, $b_{i}$ is the incoming weight, and $c_{i}$ is the bias. The output bias is $d$.

**(a)** Suppose $a_{i} = 0$ (unit $i$ has zero outgoing weight). Show that the directions $\delta b_{i}$ and $\delta c_{i}$ are degenerate at $w$.

**(b)** Suppose $b_{i} = 0$ (unit $i$ has zero incoming weight). Show that the direction $(\delta a_{i}, \delta d) = (1, -\sigma(c_{i}))$ (with all other components zero) is degenerate at $w$.

**(c)** Suppose $h \geq 2$ and $(b_{i}, c_{i}) = (b_{j}, c_{j})$ for some $i \neq j$ (units $i$ and $j$ have the same incoming weights and biases). Show that the direction $(\delta a_{i}, \delta a_{j}) = (1, -1)$ (with all other components zero) is degenerate at $w$.
:::

^ex-mlp-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. At $a_{i} = 0$, the parameter–function map reduces to

$$
f_{w}(x) = d + 0 \cdot \sigma(b_{i} x + c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) = d + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}).
$$

This expression does not involve $b_{i}$ or $c_{i}$ at all. Therefore $\Phi$ is constant in the $b_{i}$ and $c_{i}$ directions at this point, so $D_{\delta b_i}\Phi(w) = 0$ and $D_{\delta c_i}\Phi(w) = 0$. Both are degenerate directions.

Note that this argument is purely algebraic, following from the multiplicative structure $a_{i} \cdot \sigma(\ldots)$, and requires no conditions on $\sigma$ (not even continuity or differentiability).
2. At $b_{i} = 0$, unit $i$ computes the constant $\sigma(0 \cdot x + c_{i}) = \sigma(c_{i})$ for all $x$, so

$$
f_{w}(x) = d + a_{i}\,\sigma(c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}).
$$

In the direction $(\delta a_{i}, \delta d) = (1, -\sigma(c_{i}))$, we compute

$$
\begin{aligned}f_{w + \epsilon\,v}(x)&= (d - \epsilon\,\sigma(c_{i})) + (a_{i} + \epsilon)\,\sigma(c_{i}) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) \\&= d + a_{i}\,\sigma(c_{i}) + \epsilon\bigl(\sigma(c_{i}) - \sigma(c_{i})\bigr) + \sum_{j \neq i}a_{j}\,\sigma(b_{j} x + c_{j}) = f_{w}(x).\end{aligned}
$$

So $D_{(\delta a_i, \delta d)}\Phi(w) = 0$ and this direction is degenerate. Intuitively, increasing $a_{i}$ scales up the constant contribution $a_{i}\,\sigma(c_{i})$ to the output, and decreasing $d$ by the same amount compensates exactly.
3. When $(b_{i}, c_{i}) = (b_{j}, c_{j})$, units $i$ and $j$ compute the same activation, so their combined contribution to $f_{w}$ is

$$
a_{i}\,\sigma(b_{i} x + c_{i}) + a_{j}\,\sigma(b_{j} x + c_{j}) = (a_{i} + a_{j})\,\sigma(b_{i} x + c_{i}).
$$

In the direction $(\delta a_{i}, \delta a_{j}) = (1, -1)$, this combined contribution changes by $\sigma(b_{i} x + c_{i}) - \sigma(b_{j} x + c_{j}) = 0$. All other terms in $f_{w}$ are unchanged, so $D_{(1,-1)}\Phi(w) = 0$. Again, no conditions on $\sigma$ are needed.

:::

:::callout {title="Note" tone="blue"}

**Remark (Localised symmetries in neural networks).** Each degenerate direction identified in the exercises above corresponds to a localised symmetry: a curve of functionally equivalent parameters that continuously extends only within a subset of parameter space.

1. In the DLN, the global change-of-basis symmetry $(A, B) \mapsto (G A, B G^{-1})$ for invertible $G \in \mathbb{R}^{m\times m}$ accounts for $m^{2}$ degenerate directions. These directions are present even when $A$ and $B$ have full rank. However, as we showed in [[#^ex-dln-degeneracy|Exercise 2.9]], when $A$ or $B$ drops rank, $(m - r_{A})(m - r_{B})$ additional degenerate directions open up. These extra directions are localised to the rank-deficient region of parameter space.
2. In the MLP, at a parameter with $a_{i} = 0$, the path $t \mapsto (\ldots, a_{i}, b_{i} + t, c_{i}, \ldots)$ traces equivalent parameters within $\{a_{i} = 0\}$ (since $f_{w}$ does not depend on $b_{i}$ when $a_{i} = 0$), but this does not extend to a symmetry at nearby parameters with $a_{i} \neq 0$. Similarly, at a parameter with $(b_{i}, c_{i}) = (b_{j}, c_{j})$, the path transferring weight between units $i$ and $j$ is a localised version of the sum symmetry from [[#^ex-sum-symmetry|Exercise 2.5]].

:::

::::callout {title="Note" tone="blue"}

**Remark (Rank of a neural network parameter).** In both exercises above, the degree of degeneracy at a parameter is controlled by the amount of redundant capacity in the network. For the two-layer DLN, this is measured by the rank of the product $BA$: a rank-$r$ linear map can be implemented with a hidden dimension of $r$, leaving $m - r$ dimensions redundant. For a general single-hidden-layer MLP, this idea generalises in that we can define the rank of a parameter $w$ as the minimum number of hidden units needed to implement $f_{w}$ ([[#^bib-farrugiaroberts2022|Farrugia-Roberts 2022]]; [[#^bib-farrugiaroberts2024|Farrugia-Roberts 2024]]). In the linear case, this "neural network rank" coincides with the matrix rank of $BA$. In both settings, lower rank corresponds to a higher number of degenerate directions.

::::

^rem-rank


:::callout {title="Note" tone="blue"}

**Remark (Measure zero degenerate sets).** When a parameter–function map is degenerate somewhere but not everywhere, it is often the case that it is degenerate only within a measure-zero subset of parameter space. This means that sampling parameters uniformly at random results in a degenerate parameter with probability zero. However, this does not mean that the degeneracies can be dismissed. The learning process applies a non-random selection pressure and may select parameters from a measure-zero set. Moreover, the existence of degenerate parameters can have practical consequences for nearby non-degenerate parameters, and the collective neighbourhoods of all degenerate parameters comprise a non-measure-zero subset of parameter space.

:::

\### 2.4 Degeneracy and information singularities

In the preceding sections, we studied degeneracy as a property of parameter–function maps. In the statistical framework introduced in [[#1.3 Statistical models and parameter–distribution maps|Subsection 1.3]], the fundamental object is instead a parameter–distribution map $\Psi : \mathcal{W} \to \mathcal{D}$ ($w \mapsto p_{w} : \mathcal{X} \to \Delta(\mathcal{Y})$). In this section, we extend the definition of degeneracy to parameter–distribution maps and connect it to a classical quantity from statistics, the Fisher information matrix. We will show that under mild regularity conditions on the statistical model, the Fisher information matrix is singular at $w$ (has zero eigenvalues) if and only if the parameter–distribution map is degenerate at $w$.

Given a parameter–distribution map $\Psi : \mathcal{W} \to \mathcal{D}$, say that $\Psi$ is **degenerate at $w$ in direction $v$** if the conditional density does not change to first order:


$$
D_{v} \Psi(w) = 0.
$$


^eq-dist-degeneracy


Here, $D_{v} \Psi(w)$ is not a conditional distribution but a signed difference between conditional distributions, effectively a real function of $x$ and $y$ (in particular, it may include negative density changes). We mean that this function is zero for all $x \in \mathcal{X}$ and all $y \in \mathcal{Y}$.

[[#^eq-dist-degeneracy|Equation 21]] extends the definition of degeneracy from [[#^eq-degeneracy|Equation 19]]. If $\Psi$ is constructed from a parameter–function map $\Phi$ via a noise model (as in [[#1.3 Statistical models and parameter–distribution maps|Subsection 1.3]]), then degeneracy of $\Phi$ at $w$ in direction $v$ implies degeneracy of $\Psi$ at $w$ in direction $v$, since $p(y \mid x, w)$ depends on $w$ only through $f_{w}(x)$.

To relate degeneracy to the Fisher information matrix, we introduce two standard definitions.

:::callout {title="Definition" tone="purple"}

**Definition 2.3 (Score function).** Let $\Psi : \mathcal{W} \to \mathcal{D}$ be a parameter–distribution map with densities $p(y \mid x, w)$ that are positive and differentiable in $w$. The **score function** at $w$ is


$$
s(x, y, w) = \nabla_{w} \log p(y \mid x, w) \in \mathbb{R}^{d}.
$$


^eq-score


The **directional score** in non-zero direction $v \in \mathbb{R}^{d}$ is


$$
s_{v}(x, y, w) = D_{v} \log p(y \mid x, w) = \frac{v}{\|v\|}\cdot \nabla_{w} \log p(y \mid x, w).
$$


^eq-directional-score


The directional score measures how sensitive the log-density is to perturbations of $w$ in direction $v$.

:::

^def-score


:::::callout {title="Exercise" tone="amber"}
**Exercise 2.11 (Basic properties of the score function).** Let $\Psi : \mathcal{W} \to \mathcal{D}$ be a parameter–distribution map with positive densities $p(y \mid x, w)$, differentiable in $w$. Assume that for each $x$ and $w$, the operations $\nabla_{w}$ and $\int_{\mathcal{Y}} \cdot\, dy$ may be exchanged.

**(a)** Show that the score function satisfies the following identity: for each $x \in \mathcal{X}$, $y \in \mathcal{Y}$, and $w \in \mathcal{W}$,


$$
s(x,y,w) = \frac{\nabla_{w} p(y \mid x,w)}{p(y \mid x,w)}.
$$


^eq-score-identity


**(b)** Show that the expected score is zero: for each $x \in \mathcal{X}$ and $w \in \mathcal{W}$,

$$
\mathbb{E}_{y \sim p(y \mid x, w)}\bigl[s(x, y, w)\bigr] = 0.
$$

::::callout {title="Hint" tone="neutral" collapse="closed"}

Differentiate the identity $\int_{\mathcal{Y}} p(y \mid x, w) \, dy = 1$.

::::

**(c)** Show that if $\Psi$ is degenerate at $w$ in direction $v$, then the directional score vanishes identically: $s_{v}(x, y, w) = 0$ for all $x \in \mathcal{X}$ and $y \in \mathcal{Y}$.

**(d)** Show the converse: if the directional score $s_{v}(x, y, w) = 0$ vanishes for all $x \in \mathcal{X}$ and $y \in \mathcal{Y}$ at $w$, then $\Psi$ is degenerate at $w$ in direction $v$.
:::::

^ex-score-properties


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since $p(y \mid x, w) > 0$, the logarithm is well-defined and the chain rule gives

$$
\nabla_{w} \log p(y \mid x, w) = \frac{\nabla_{w} p(y \mid x, w)}{p(y \mid x, w)}.
$$

The left-hand side is $s(x,y,w)$ by definition.
2. Differentiate the normalisation identity $\int_{\mathcal{Y}} p(y \mid x, w) \, dy = 1$ with respect to $w$:

$$
0 = \nabla_{w} \int_{\mathcal{Y}} p(y \mid x, w) \, dy = \int_{\mathcal{Y}} \nabla_{w} p(y \mid x, w) \, dy.
$$

By part (a), $\nabla_{w} p = p \cdot s$, so

$$
0 = \int_{\mathcal{Y}} p(y \mid x, w)\, s(x, y, w) \, dy = \mathbb{E}_{y \sim p(y \mid x, w)}\bigl[s(x, y, w)\bigr].
$$
3. If $D_{v} \Psi(w) = 0$, then by the definition of degeneracy [[#^eq-dist-degeneracy|(21)]], $D_{v} p(y \mid x, w) = 0$ for all $x, y$. By part (a), $\nabla_{w} p = p \cdot s$, so contracting both sides with $v / \|v\|$ gives $D_{v} p = p \cdot s_{v}$. Since $p > 0$, we conclude $s_{v}(x, y, w) = 0$ for all $x, y$.
4. If $s_{v}(x, y, w) = 0$ for all $x, y$, then by part (a),

$$
D_{v} p(y \mid x, w) = p(y \mid x, w) \cdot s_{v}(x, y, w) = 0
$$

for all $x, y$ (using $p > 0$). That is, $D_{v} \Psi(w) = 0$.

:::

:::callout {title="Definition" tone="purple"}

**Definition 2.4 (Fisher information matrix).** Let $\Psi : \mathcal{W} \to \mathcal{D}$ be a parameter–distribution map with score function $s$. Let $q(x)$ denote the marginal distribution of inputs. The **Fisher information matrix** $I : \mathcal{W} \to \mathbb{R}^{d \times d}$ is defined by


$$
I(w) = \mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr].
$$


^eq-fim


:::

^def-fim


The Fisher information matrix is symmetric and positive semidefinite at every $w$ (being an expectation of positive semidefinite matrices $s\, s^{\top}$). However, the Fisher information matrix may not be symmetric positive *definite,* that is, it may be singular.

The following exercise shows that singularity of the Fisher information matrix is equivalent to degeneracy of the parameter–distribution map under mild regularity conditions.

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.12 (Fisher information and degeneracy).** Let $\Psi : \mathcal{W} \to \mathcal{D}$ be a parameter–distribution map with densities $p(y \mid x, w)$. Assume that $p(y \mid x, w) > 0$ for all $y \in \mathcal{Y}$, $x \in \mathcal{X}$, $w \in \mathcal{W}$, that $w \mapsto p(y \mid x, w)$ is differentiable, and that $q(x) > 0$ for all $x \in \mathcal{X}$.

**(a)** Show that for any unit vector $v \in \mathbb{R}^{d}$,


$$
v^{\top} I(w)\, v = \mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ s_{v}(x, y, w)^{2} \bigr].
$$


^eq-fim-quadratic


**(b)** Using [[#^ex-score-properties|Exercise 2.11(c)]], show that if $D_{v} \Psi(w) = 0$ for some non-zero $v$, then $I(w)$ is not positive definite.
::::callout {title="Hint" tone="neutral" collapse="closed"}

Check the definition of positive definite.

::::

**(c)** Using [[#^ex-score-properties|Exercise 2.11(d)]], show that if $I(w)$ is not positive definite, then there exists a non-zero $v$ for which $D_{v} \Psi(w) = 0$.
::::callout {title="Hint" tone="neutral" collapse="closed"}

Check the definition of positive definite.

::::

**(d)** Conclude that

$$
\ker I(w) = \bigl\{v \in \mathbb{R}^{d} : D_{v} \Psi(w) = 0\bigr\}.
$$

That is, the null space of the Fisher information matrix is exactly the space of degenerate directions of the parameter–distribution map.
:::::

^ex-fim-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since $v$ is a unit vector, $s_{v} = D_{v} \log p = \frac{v}{\|v\|}\cdot s = v \cdot s$. From the definition of $I(w)$ in [[#^eq-fim|(26)]],

$$
\begin{aligned}v^{\top} I(w)\, v&= v^{\top} \mathbb{E}_{x,y}\!\bigl[s\, s^{\top}\bigr]\, v = \mathbb{E}_{x,y}\!\bigl[(v \cdot s)^{2}\bigr] = \mathbb{E}_{x,y}\!\bigl[s_{v}^{2}\bigr] \\&= \mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ s_{v}(x,y,w)^{2} \bigr].\end{aligned}
$$
2. If $D_{v} \Psi(w) = 0$ for some non-zero $v$, then by [[#^ex-score-properties|Exercise 2.11(c)]], $s_{v}(x,y,w) = 0$ for all $x, y$. Let $\hat{v}= v / \|v\|$. Then $s_{\hat{v}}= s_{v}$ (the directional derivative is invariant to the magnitude of $v$), so by part (a), $\hat{v}^{\top} I(w)\, \hat{v}= \mathbb{E}[s_{\hat{v}}^{2}] = 0$. A matrix $M$ is positive definite only if $u^{\top} M u > 0$ for all non-zero $u$. Since $\hat{v}$ is a non-zero vector with $\hat{v}^{\top} I(w)\, \hat{v}= 0$, the matrix $I(w)$ is not positive definite.
3. If $I(w)$ is not positive definite, then since $I(w)$ is positive semidefinite, there exists a non-zero vector $\hat{v}$ such that $\hat{v}^{\top} I(w)\, \hat{v}= 0$. By part (a) (taking $\hat{v}$ to be a unit vector without loss of generality), $\mathbb{E}[s_{\hat{v}}^{2}] = 0$. Since $s_{\hat{v}}^{2} \geq 0$ and $q(x) > 0$ and $p(y \mid x, w) > 0$, this implies $s_{\hat{v}}(x,y,w) = 0$ for all $x \in \mathcal{X}$ and $y \in \mathcal{Y}$. By [[#^ex-score-properties|Exercise 2.11(d)]], $D_{\hat{v}}\Psi(w) = 0$.
4. Parts (b) and (c) show that $I(w)$ is positive definite if and only if $\Psi$ is non-degenerate at $w$, or equivalently, $I(w)$ is singular if and only if $\Psi$ is degenerate at $w$.

For the kernel characterisation: clearly $0 \in \ker I(w)$. For non-zero $v$, $v \in \ker I(w)$ means $I(w)\,v = 0$, which (since $I(w)$ is positive semidefinite) is equivalent to $v^{\top} I(w)\, v = 0$. Normalising to $\hat{v}= v/\|v\|$, part (a) gives $\mathbb{E}[s_{\hat{v}}^{2}] = 0$, which as in part (c) implies $s_{\hat{v}}= 0$ everywhere. By [[#^ex-score-properties|Exercise 2.11(d)]], $D_{\hat{v}}\Psi(w) = 0$, and hence $D_{v} \Psi(w) = 0$. Conversely, if $D_{v} \Psi(w) = 0$ for non-zero $v$, then [[#^ex-score-properties|Exercise 2.11(c)]] gives $s_{v} = 0$, so $v^{\top} I(w)\, v = \|v\|^{2} \mathbb{E}[s_{v}^{2}] = 0$, hence $I(w)\, v = 0$. Therefore $\ker I(w) = \{v \in \mathbb{R}^{d} : D_{v} \Psi(w) = 0\}$.

:::

::::callout {title="Note" tone="blue"}

**Remark (Watanabe's strictly singular models).** [[#^bib-watanabe2009|Watanabe 2009]] defines a statistical model as *strictly singular* if either of two conditions hold:

1. The Fisher information matrix $I(w)$ is singular for some $w \in \mathcal{W}$.
2. The parameter–distribution map is not one-to-one, that is, for some $w, w' \in \mathcal{W}$ such that $w \neq w'$, we have $\Psi(w) = \Psi(w')$.

By [[#^ex-fim-degeneracy|Exercise 2.12]], under mild regularity conditions, the first condition is equivalent to our notion of (somewhere) degeneracy. The second condition is called non-identifiability.

[[#^bib-watanabe2007|Watanabe 2007]]; [[#^bib-watanabe2009|Watanabe 2009]] observes that many of the results from classical statistics crucially assume among their regularity conditions the parameter–distribution map is identifiable and the Fisher information matrix is nonsingular. Whereas, in a statistical model based on a non-trivial neural network (or any other statistical model involving hierarchical structure), it is typical for the Fisher information matrix to include singularities.

::::

^rem-strictly-singular


\### 2.5 Degeneracy and the loss landscape

In the preceding sections, we studied degeneracy as a property of parameter–function maps and parameter–distribution maps. We now consider the implications of degeneracy in these maps for the *loss landscape* in which deep learning algorithms operate.

Recall the definitions of loss functions from [[#1. Preliminaries|Section 1]]. In what follows, we assume that the per-example loss $L_{x,y}(w)$ depends on $w$ only through $\Phi(w)$, and work with the population loss $L(w) = \mathbb{E}_{(x,y) \sim q}[L_{x,y}(w)]$. For statistical models, we use the expected negative log likelihood $L(w) = \mathbb{E}_{(x,y) \sim q}[-\log p(y \mid x, w)]$ as our loss function. In either case, we assume that $L$ is twice-differentiable with respect to $w$.

Let us begin with some basic observations about the relationship between degeneracy in parameter–function maps and directional derivatives in the loss landscape.

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.13 (Directional derivatives of the loss).** Let $L : \mathcal{W} \to \mathbb{R}$ be a population loss function satisfying the assumptions described above.

**(a)** Show that if $\Phi$ is degenerate at $w$ in direction $v$, then the directional derivative of the loss vanishes in the same direction: $D_{v} L(w) = 0$.

**(b)** Suppose $\mathcal{W} = \mathbb{R}^{d}$. Show that if $d > 1$, then for *any* any $w \in \mathcal{W}$, there exists a nonzero $v$ such that $D_{v} L(w) = 0$.
::::callout {title="Hint" tone="neutral" collapse="closed"}

consider separately the cases $\nabla L(w) = 0$ and $\nabla L(w) \neq 0$.

::::
:::::

^ex-loss-basic


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since $L_{x,y}(w)$ depends on $w$ only through $\Phi(w)$, we can write $L_{x,y}(w) = \ell_{x,y}(\Phi(w))$ for some functional $\ell_{x,y}$. If $D_{v}\Phi(w) = 0$, then $\Phi(w + \epsilon v) = \Phi(w) + O(\epsilon^{2})$ as $\epsilon \to 0$, and therefore $L_{x,y}(w + \epsilon v) = \ell_{x,y}(\Phi(w) + O(\epsilon^{2})) = L_{x,y}(w) + O(\epsilon^{2})$. Taking expectations over $(x,y) \sim q$,

$$
L(w + \epsilon v) = L(w) + O(\epsilon^{2}),
$$

so $D_{v} L(w) = \lim_{\epsilon \to 0}\frac{L(w + \epsilon v) - L(w)}{\epsilon\|v\|}= 0$.
2. If $\nabla L(w) = 0$, then $D_{v} L(w) = \frac{v}{\|v\|}\cdot \nabla L(w) = 0$ for every nonzero $v$.

If $\nabla L(w) \neq 0$, the orthogonal complement $\nabla L(w)^{\perp}$ has dimension $d - 1 \geq 1$ (since $d > 1$). Pick any nonzero $v \in \nabla L(w)^{\perp}$. Then $D_{v} L(w) = \frac{v}{\|v\|}\cdot \nabla L(w) = 0$.

:::

We see that parameter–function map degeneracy implies flat loss directions, but a vanishing directional derivative of the loss landscape is commonplace. To find a satisfying definition of degeneracy in a loss landscape, we must look at second-order information.

Define the **Hessian matrix** $H(w) \in \mathbb{R}^{d \times d}$ of the loss at $w$ by

$$
H(w)_{jk}= \frac{\partial^{2} L}{\partial w_{j} \partial w_{k}}(w).
$$

The Hessian at $w$ is sometimes denoted $\nabla^{2} L(w)$. The Hessian captures the local curvature of the loss landscape via the quadratic approximation

$$
L(w + \delta) \approx L(w) + \nabla L(w)^{\top} \delta + \tfrac{1}{2}\,\delta^{\top} H(w)\, \delta.
$$

At a critical point ($\nabla L(w) = 0$), the Hessian determines whether the loss curves upward, downward, or remains flat in each direction.

In particular, at a local minimum, $H(w)$ is positive semidefinite. We can therefore classify local minima as follows:

- A local minimum $w$ is **regular** (or **non-degenerate**, or **Morse**) if $H(w)$ is positive definite.
- A local minimum $w$ is **degenerate** (or **non-Morse**) if $H(w)$ is singular (has a zero eigenvalue).

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.14 (Some examples of loss landscape degeneracy).** Consider the parameter space $\mathcal{W} = \mathbb{R}^{2}$ with the identity parameter–function map $\Phi = \mathrm{id}$, so that we identify parameters with the functions they implement (cf., [[#^ex-univariate-degeneracy|Exercise 2.1]]). Consider the family of loss functions $L_{k,l}(a,b) = a^{2k}+ b^{2l}$ for non-negative integers $k$ and $l$.

**(a)** Show that the origin is a global minimum of $L_{k,l}$ for all non-negative $k$ and $l$. For which $k$ and $l$ is it the unique global minimum?

**(b)** Show that if $k = l = 1$, then the origin is a non-degenerate (regular) minimum.
::::callout {title="Hint" tone="neutral" collapse="closed"}

Compute the Hessian.

::::

**(c)** Show that if $k > 1$ and $l \geq 1$, then the origin is a degenerate minimum.

**(d)** Show that if $k = 0$ and $l \geq 1$, then the origin is a degenerate minimum.
:::::

^ex-loss-landscape-degeneracy


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since $a^{2k}\geq 0$ and $b^{2l}\geq 0$ for all $a, b \in \mathbb{R}$ (using the convention $0^{0} = 1$), we have $L_{k,l}(a,b) \geq 0$ for $k, l \geq 1$, $L_{k,l}(a,b) \geq 1$ if $k = 0$ or $l = 0$, and $L_{k,l}(a,b) = 2$ if $k = l = 0$. At the origin, $L_{k,l}(0,0) = 0^{2k}+ 0^{2l}$, which equals $0$ if $k \geq 1$ and $l \geq 1$, equals $1$ if exactly one of $k, l$ is $0$, and equals $2$ if $k = l = 0$. In each case this matches the lower bound, so the origin is a global minimum.

The origin is the *unique* global minimum if and only if $k \geq 1$ and $l \geq 1$: then $L_{k,l}(a,b) = 0$ requires both $a^{2k}= 0$ and $b^{2l}= 0$, forcing $a = b = 0$. If $k = 0$, then $L_{0,l}(a,0) = 1$ for all $a$, so the entire $a$-axis achieves the minimum. Similarly if $l = 0$. If $k = l = 0$, then all parameters achieve the minimum.
2. For $k = l = 1$: $L_{1,1}(a,b) = a^{2} + b^{2}$. The Hessian at the origin is

$$
H(0,0) = \begin{pmatrix}2 & 0 \\ 0 & 2\end{pmatrix},
$$

which is positive definite. The origin is a non-degenerate minimum.
3. For $k > 1$ and $l \geq 1$: $\frac{\partial^{2} L_{k,l}}{\partial a^{2}}= 2k(2k{-}1)\, a^{2k-2}$. At the origin, $a^{2k-2}= 0$ since $2k - 2 \geq 2$, so this entry vanishes. The Hessian at the origin is therefore

$$
H(0,0) = \begin{pmatrix}0&0 \\ 0&2l(2l{-}1) \cdot 0^{2l-2}\end{pmatrix},
$$

which has a zero eigenvalue (from the first diagonal entry) regardless of the value of the second. The origin is a degenerate minimum.
4. For $k = 0$ and $l \geq 1$: $L_{0,l}(a,b) = 1 + b^{2l}$. Since $L_{0,l}$ is independent of $a$, both $\frac{\partial L}{\partial a}$ and $\frac{\partial^{2} L}{\partial a^{2}}$ vanish identically. The Hessian at the origin has a zero first diagonal entry, so it is singular. The origin is a degenerate minimum.

:::

Note that the Hessian degeneracy in [[#^ex-loss-landscape-degeneracy|Exercise 2.14(c)]] and [[#^ex-loss-landscape-degeneracy|2.14(d)]] arise for qualitatively different reasons. In [[#^ex-loss-landscape-degeneracy|Exercise 2.14(d)]], the loss is constant along the $a$-direction to all orders—a genuinely flat direction. In [[#^ex-loss-landscape-degeneracy|Exercise 2.14(c)]], the loss does increase along the $a$-direction, just more slowly than quadratically (as $a^{4}$, $a^{6}$, etc., depending on $k$). Moreover, different values of $k$ give different rates of increase. The Hessian cannot distinguish any of these cases: flat, quartic, and so on all appear the same from the perspective of the Hessian rank. We will later see approaches that can distinguish these degrees of degeneracy.

So much for defining loss landscape degeneracy. What is the relationship between this kind of degeneracy and degeneracy of the parameter–function/distribution map?

The relationship is subtle, and generally depends on the choice of loss function. One natural setting in which to study this relationship is the *realisable statistical model:* given a parameter–distribution map and a parameter $w_{0}$, if we consider $p_{w_0}$ as the true data-generating distribution, the population negative log-likelihood loss will have a global minimum at $w_{0}$. The following exercise shows that in this setting, under mild regularity assumptions on the statistical model, degeneracy in the parameter–distribution map at $w_{0}$ implies that the global minimum $w_{0}$ is a degenerate global minimum of the loss landscape.

:::::callout {title="Exercise" tone="amber"}
**Exercise 2.15 (Realisable models and Hessian degeneracy).** Let $\Psi : \mathcal{W} \to \mathcal{D}$ be a parameter–distribution map with positive densities $p(y \mid x, w)$, twice-differentiable in $w$. Suppose data is generated from a fixed true parameter $w_{0} \in \mathcal{W}$, meaning $q(y \mid x) = p(y \mid x, w_{0})$. Consider the population negative log-likelihood loss

$$
L(w) = -\mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}\!\bigl[\log p(y \mid x, w)\bigr].
$$

Assume that for each $x$, the operations $\nabla_{w}$ (and $\nabla_{w}^{2}$) and $\int_{\mathcal{Y}} \cdot\, dy$ may be exchanged.

**(a)** *(Bartlett identity.)* Show that for each $x \in \mathcal{X}$ and $w \in \mathcal{W}$,


$$
-\mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr] = \mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr],
$$


^eq-bartlett


where $s$ is the score function from [[#^def-score|Definition 2.3]].
::::callout {title="Hint" tone="neutral" collapse="closed"}

differentiate the identity $\mathbb{E}_{y \sim p(y \mid x, w)}[s(x, y, w)] = 0$ (established in [[#^ex-score-properties|Exercise 2.11]]) with respect to $w$.

::::

**(b)** Show that the Hessian of $L$ at the true parameter $w_{0}$ equals the Fisher information matrix ([[#^def-fim|Definition 2.4]]):


$$
H(w_{0}) = I(w_{0}).
$$


^eq-fim-hessian


::::callout {title="Hint" tone="neutral" collapse="closed"}

compute $H(w) = -\mathbb{E}_{x}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}[\nabla_{w}^{2} \log p(y \mid x, w)]$, evaluate at $w = w_{0}$, and apply part (a).

::::

**(c)** Using the result of [[#^ex-fim-degeneracy|Exercise 2.12]], conclude: if $\Psi$ is degenerate at $w_{0}$ in direction $v$, then $H(w_{0})\, v = 0$. Contrapositively, if $H(w_{0})$ is positive definite, then $\Psi$ is non-degenerate at $w_{0}$.
:::::

^ex-fim-hessian


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. From [[#^ex-score-properties|Exercise 2.11]], $\mathbb{E}_{y \sim p(y \mid x, w)}[s_{j}(x,y,w)] = 0$ for each component $j$ of the score, where $s_{j} = \frac{\partial}{\partial w_{j}}\log p(y \mid x, w)$. Differentiating with respect to $w_{k}$ and exchanging the derivative with the integral:

$$
\begin{aligned}0&= \frac{\partial}{\partial w_{k}}\int_{\mathcal{Y}} s_{j}(x,y,w)\, p(y \mid x, w)\, dy \\&= \int_{\mathcal{Y}} \frac{\partial s_{j}}{\partial w_{k}}\, p\, dy + \int_{\mathcal{Y}} s_{j}\, \frac{\partial p}{\partial w_{k}}\, dy. \quad\text{(product rule)}\end{aligned}
$$

Using the score identity $\frac{\partial p}{\partial w_{k}}= p \cdot s_{k}$ [[#^eq-score-identity|(24)]], the second integral becomes $\int_{\mathcal{Y}} s_{j}\, s_{k}\, p\, dy = \mathbb{E}_{y}[s_{j}\, s_{k}]$. Therefore

$$
\mathbb{E}_{y \sim p(y \mid x, w)}\!\left[ \frac{\partial^{2} \log p}{\partial w_{j} \partial w_{k}}\right] = -\mathbb{E}_{y \sim p(y \mid x, w)}[s_{j}\, s_{k}].
$$

Assembling all components into a matrix gives

$$
-\mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr] = \mathbb{E}_{y \sim p(y \mid x, w)}\!\bigl[ s(x,y,w)\, s(x,y,w)^{\top} \bigr].
$$
2. The population negative log-likelihood is $L(w) = -\mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}[\log p(y \mid x, w)]$. Taking the Hessian with respect to $w$ (exchanging differentiation and integration):

$$
H(w) = -\mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}\!\bigl[ \nabla_{w}^{2} \log p(y \mid x, w) \bigr].
$$

At $w = w_{0}$, the inner expectation is over $y \sim p(y \mid x, w_{0})$, which matches the distribution in the Bartlett identity. Applying part (a):

$$
\begin{aligned}H(w_{0})&= \mathbb{E}_{x \sim q(x)}\, \mathbb{E}_{y \sim p(y \mid x, w_0)}\!\bigl[ s(x,y,w_{0})\, s(x,y,w_{0})^{\top} \bigr] \\&= I(w_{0}). \quad\text{(by Theorem 2.4)}\end{aligned}
$$
3. By [[#^ex-fim-degeneracy|Exercise 2.12]], $\ker I(w_{0}) = \{v \in \mathbb{R}^{d} : D_{v} \Psi(w_{0}) = 0\}$. Since $H(w_{0}) = I(w_{0})$, if $\Psi$ is degenerate at $w_{0}$ in direction $v$, then $v \in \ker I(w_{0}) = \ker H(w_{0})$, so $H(w_{0})\, v = 0$.

Contrapositively: if $H(w_{0})$ is positive definite, then $\ker H(w_{0}) = \{0\}$, so $\ker I(w_{0}) = \{0\}$, and $\Psi$ is non-degenerate at $w_{0}$.

:::

[[#^ex-fim-hessian|Exercise 2.15]] shows that for the population negative log-likelihood at the true parameter, degeneracy of the parameter–distribution map implies a degenerate loss landscape. The converse does not hold in general, nor does the forward direction hold at arbitrary points in parameter space. The following exercise explores these subtleties through examples.

:::callout {title="Exercise" tone="amber"}
**Exercise 2.16 (Contrasting parametric versus loss degeneracy).** **(a)** Observe that the identity parameter–function map on $\mathcal{W} = \mathbb{R}^{2}$ is non-degenerate everywhere. With this in mind, what do your answers to [[#^ex-loss-landscape-degeneracy|Exercise 2.14(b)]] and [[#^ex-loss-landscape-degeneracy|2.14(c)]] and [[#^ex-loss-landscape-degeneracy|2.14(d)]] exemplify about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy?

**(b)** Consider again the identity parameter–function map on $\mathcal{W} = \mathbb{R}^{2}$. Consider the loss function $L_{\circ}(a,b) = (a^{2} + b^{2} - 1)^{2}$. Find a global minimum of $L_{\circ}$ and show that it is a degenerate critical point. What does this example reveal about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy?

**(c)** Now consider the cubic parameter–function map $\Phi(\alpha, \beta) = (\alpha^{3}, \beta^{3})$.

1. Argue that $\Phi$ is degenerate at the origin (cf., [[#^ex-cubic-degeneracy|Exercise 2.2]]).
2. If we take $L_{k,l}$ from [[#^ex-loss-landscape-degeneracy|Exercise 2.14]] to be defined on the constant function $(a, b)$ (rather than equivalent underlying parameter), then in this parameterisation, that loss function becomes $L_{k,l}(\alpha,\beta) = (\alpha^{3})^{2k}+ (\beta^{3})^{2l}$. Show that the origin is a degenerate minimum of $L_{k,l}$ for all $k \geq 0$ and $l \geq 0$ under this parametrisation.
3. What does this example reveal about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy?

**(d)** Consider the product parameter–function map $\Phi(a,b) = a \cdot b$ from [[#^ex-product-degeneracy|Exercise 2.3]], and define $L(a,b) = \frac{1}{2}(ab - 1)^{2}$.

1. Show that $(0,0)$ is a critical point and that $\Phi$ is degenerate in every direction at $(0,0)$.
2. Compute the Hessian at $(0,0)$ and show it is nonsingular.
3. What does this example reveal about the logical relationship between parameter–function map degeneracy and loss landscape degeneracy? Why does this not contradict [[#^ex-fim-hessian|Exercise 2.15]]?
:::

^ex-loss-degeneracy-examples


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. The identity parameter–function map $\Phi(a,b) = (a,b)$ has Jacobian equal to the $2 \times 2$ identity matrix everywhere, so it is non-degenerate at every point. [[#^ex-loss-landscape-degeneracy|Exercise 2.14(b)]] shows that $L_{1,1}$ has a non-degenerate minimum: absence of parameter–function map degeneracy is consistent with absence of loss landscape degeneracy. [[#^ex-loss-landscape-degeneracy|Exercise 2.14(c)]] and [[#^ex-loss-landscape-degeneracy|2.14(d)]] show that $L_{2,1}$, $L_{0,1}$, etc., have degenerate minima despite the parameter–function map being non-degenerate. This demonstrates that loss landscape degeneracy does not imply parameter–function map degeneracy.
2. $L_{\circ}(a,b) = (a^{2} + b^{2} - 1)^{2} \geq 0$, with equality if and only if $a^{2} + b^{2} = 1$. So every point on the unit circle is a global minimum. Consider $(1, 0)$. The gradient is

$$
\nabla L_{\circ} = \bigl(4a(a^{2} + b^{2} - 1),\; 4b(a^{2} + b^{2} - 1)\bigr),
$$

which vanishes at $(1, 0)$. The Hessian entries at $(1, 0)$ are:

$$
\begin{aligned}\frac{\partial^{2} L_{\circ}}{\partial a^{2}}&= 4(3a^{2} + b^{2} - 1) = 8,&\qquad \frac{\partial^{2} L_{\circ}}{\partial b^{2}}&= 4(a^{2} + 3b^{2} - 1) = 0, \\ \frac{\partial^{2} L_{\circ}}{\partial a\, \partial b}&= 8ab = 0.\end{aligned}
$$

So $H(1,0) = \mathrm{diag}(8, 0)$, which is singular. Therefore, $(1,0)$ is a degenerate minimum.

This provides another example of loss landscape degeneracy without parameter–function map degeneracy: the identity parameter–function map is non-degenerate, but the circle of global minima creates a flat tangential direction.
3. 1. The map $\Phi(\alpha, \beta) = (\alpha^{3}, \beta^{3})$ is the product of two copies of the cubic parametrisation from [[#^ex-cubic-degeneracy|Exercise 2.2]]. In each component, the derivative $\frac{d}{d\alpha}(\alpha^{3}) = 3\alpha^{2}$ vanishes at $\alpha = 0$. Therefore both coordinate directions are degenerate at the origin, and hence every direction is degenerate at the origin (since the Jacobian $\mathrm{diag}(3\alpha^{2}, 3\beta^{2})$ is the zero matrix there).
2. In the new parametrisation, the loss becomes $L_{k,l}(\alpha,\beta) = (\alpha^{3})^{2k}+ (\beta^{3})^{2l}= \alpha^{6k}+ \beta^{6l}$.

If $k \geq 1$ and $l \geq 1$: the exponents $6k$ and $6l$ are both at least $6$, so $\frac{\partial^{2} L}{\partial \alpha^{2}}\big|_{0} = 6k(6k{-}1) \cdot 0^{6k-2}= 0$ (since $6k - 2 \geq 4$), and similarly for $\beta$. The Hessian at the origin is the zero matrix, which is singular.

If $k = 0$: $L_{0,l}(\alpha,\beta) = 1 + \beta^{6l}$, which is independent of $\alpha$, so the Hessian has a zero first diagonal entry. Similarly if $l = 0$. In all cases, the origin is a degenerate minimum.
3. Under the identity parameter–function map, $L_{1,1}(a,b) = a^{2} + b^{2}$ had a non-degenerate minimum at the origin ([[#^ex-loss-landscape-degeneracy|Exercise 2.14(b)]]). Under the cubic parameter–function map, the same loss became $\alpha^{6} + \beta^{6}$, which has a degenerate minimum at the origin. This shows that introducing degeneracy into the parameter–function map can convert a non-degenerate minimum into a degenerate one.

For other $k,l$, $L_{k,l}$ was already degenerate at the origin under the non-degenerate parameterisation, the cubic function only makes it *more* degenerate (in terms of the order to which the loss vanishes in the degenerate direction(s); we will formally quantify this in [[#3. The degeneracy hierarchy|Section 3]]).
4. 1. The gradient is $\nabla L = (ab - 1)(b,\, a)$. At $(0, 0)$: $\nabla L = (0 - 1)(0, 0) = (0, 0)$. So $(0, 0)$ is a critical point.

The Jacobian of $\Phi(a,b) = ab$ is $(b, a)$, which at $(0, 0)$ is $(0, 0)$. Every direction $v = (v_{1}, v_{2})$ gives $J v = b v_{1} + a v_{2} = 0$, so $\Phi$ is degenerate in every direction at $(0, 0)$.
2. Computing second partial derivatives:

$$
\begin{aligned}\frac{\partial^{2} L}{\partial a^{2}}&= b^{2},&\qquad \frac{\partial^{2} L}{\partial b^{2}}&= a^{2},&\qquad \frac{\partial^{2} L}{\partial a\, \partial b}&= 2ab - 1.\end{aligned}
$$

At $(0, 0)$:

$$
H(0,0) = \begin{pmatrix}0 & -1 \\ -1 & 0\end{pmatrix},
$$

which has determinant $-1 \neq 0$ (eigenvalues $\pm 1$). The Hessian is nonsingular.
3. Despite full degeneracy of the parameter–function map at $(0,0)$, the Hessian is nonsingular (in fact indefinite, so $(0,0)$ is a saddle point, not a local minimum). This shows that parameter–function map degeneracy does not in general imply loss landscape degeneracy.

This does not contradict [[#^ex-fim-hessian|Exercise 2.15]], which establishes $H(w_{0}) = I(w_{0})$ at the *true parameter* $w_{0}$, meaning $\Phi(w_{0})$ must equal the target. Here, $\Phi(0,0) = 0 \neq 1$, so $(0,0)$ is not the true parameter, and the identity does not apply.

:::

\## 3. The degeneracy hierarchy

We have so far explored different kinds of qualitative degeneracy in the loss landscape. A natural question arises: *how can we quantify the degree of degeneracy at a particular point in parameter space?* In this section, we introduce the local learning coefficient, a rich mathematical object that reflects the degree of degeneracy at a parameter, and we explore it from several perspectives.

In this section and [[#4. Degeneracy and Bayesian deep learning|Section 4]] we assume that any population loss $L$ is a real analytic function. The precise definition of real analyticity is not important for this tutorial but interested readers can refer to ([[#^bib-watanabe2009|Watanabe 2009]]) (section 2). A property that will be useful is that such functions have a convergent Taylor expansion, in particular they have smooth derivatives of all orders.

\### 3.1 The local learning coefficient via volume scaling asymptotics

The key idea is to measure the *volume* of near-optimal parameters. Consider a local minimum $w^{*} \in \mathcal{W}$ of the population loss $L$, and suppose we have a sufficiently small closed ball $B(w^{*})$ centred on $w^{*}$ such that $L(w) \geq L(w^{*})$ for all $w \in B(w^{*})$. Given a tolerance $\epsilon > 0$, define the **sublevel set**


$$
B(w^{*}, \epsilon) = \{ w \in B(w^{*}) \mid L(w) - L(w^{*}) < \epsilon \},
$$


^eq-sublevel-set


consisting of all parameters in the ball whose loss is within $\epsilon$ of the minimum. The volume of this set is

$$
V(\epsilon) := \mathrm{Vol}(B(w^{*}, \epsilon)) = \int_{B(w^*, \epsilon)}dw.
$$

We will look at how this volume scales as $\epsilon \to 0$. It will be instructive for us to first calculate this scaling in the non-degenerate case.

:::::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (Volume scaling in the regular case).** Let $w^{*} \in \mathcal{W}$ be a local minimum of $L$, and suppose that the Hessian $\nabla^{2} L(w^{*})$ is positive definite. Show that


$$
V(\epsilon) = c \, \epsilon^{d/2}+ o(\epsilon^{d/2}) \quad \text{as }\epsilon \to 0,
$$


^eq-regular-volume-scaling


for some constant $c>0$ where $d = \dim(\mathcal{W})$. You may assume that, as $\epsilon \to 0$, the volume of $B(w^{*},\epsilon)$ agrees to leading order with the volume of the quadratic approximation obtained by replacing $L$ with its second-order Taylor expansion at $w^{*}$.

::::callout {title="Hint" tone="neutral" collapse="closed"}

The volume of the ellipsoid $\{\boldsymbol{x}\in \mathbb{R}^{d} \mid \boldsymbol{x}^{\top} A \boldsymbol{x}< 1\}$ is proportional to $(\det A)^{-1/2}$.

::::
:::::

^ex-llc-regular-case


:::callout {title="Solution" tone="neutral" collapse="closed"}

Because $w^{*}$ is a local minimum, the gradient $\nabla L(w^{*})$ is zero. By Taylor's theorem, we can write the loss function near $w^{*}$ exactly as:

$$
L(w) - L(w^{*}) = \frac{1}{2}(w - w^{*})^{\top} H (w - w^{*}) + o(\|w - w^{*}\|^{2})
$$

where $H = \nabla^{2} L(w^{*})$ is the strictly positive definite Hessian matrix.

The sublevel set is defined by the condition $L(w) - L(w^{*}) < \epsilon$. As $\epsilon \to 0$, the neighborhood of parameters that satisfy this condition shrinks toward $w^{*}$. In this limit, the higher-order error term $o(\|w - w^{*}\|^{2})$ becomes negligible, and the boundary of the sublevel set is governed entirely by the quadratic form:

$$
\frac{1}{2}(w - w^{*})^{\top} H (w - w^{*}) < \epsilon.
$$

We can rewrite this inequality into the standard form of an ellipsoid, $x^{\top} A x < 1$, by dividing both sides by $\epsilon$:

$$
(w - w^{*})^{\top} \left( \frac{1}{2\epsilon}H \right) (w - w^{*}) < 1.
$$

Using the hint, the volume of a $d$-dimensional ellipsoid defined by a matrix $A$ is proportional to $(\det A)^{-1/2}$. Here, our matrix is $A = \frac{1}{2\epsilon}H$.

Therefore,

$$
\det\left( \frac{1}{2\epsilon}H \right)^{-1/2}= \left( \left(\frac{1}{2\epsilon}\right)^{d} \det H \right)^{-1/2}= \epsilon^{d/2}\underbrace{\left( \frac{\det H}{2^{d}} \right)^{-1/2}}_{:=c}
$$

Because the true loss function deviates from this pure quadratic form only by an error of $o(\|w - w^{*}\|^{2})$, the volume of the true sublevel set deviates from the ellipsoid's volume only by a correspondingly higher-order error term. Thus, we conclude:

$$
V(\epsilon) = c \epsilon^{d/2}+ o(\epsilon^{d/2}) \quad \text{as }\epsilon \to 0.
$$

:::

The key takeaway from this exercise is that the dimension of the model controls the leading order asymptotics of the volume scaling. We can investigate this further by calculating the volume scaling in an example where the Hessian is not positive definite.

:::::callout {title="Exercise" tone="amber"}
**Exercise 3.2 (Quadratic Valley Volume Scaling).** Let $\mathcal{W} = [-R,R]^{d}$ for some (large) $R\in\mathbb{R}$ and let $L(x_{1},\dots,x_{d}) = \sum\limits_{i=1}^{d'}x_{i}^{2}$.

**(a)** Sketch the loss landscape when $d=2, \,d'=1$.

**(b)** $L$ achieves its minimum value $0$ at multiple points in $\mathcal{W}$. What is the dimension of the space $\mathcal{W}_{0} := \{w\in\mathcal{W} \, | \,L(w)=0\}$?

**(c)** Calculate the Hessian of $L$.

**(d)** Prove that $V(\epsilon) \propto \epsilon^{d'/2}$

::::callout {title="Hint" tone="neutral" collapse="closed"}

Use the volume of the ellipsoid from Exercise [[#^ex-llc-regular-case|3.1]]

::::
:::::

^ex-quad-valley-scaling


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. The loss is $L(x_{1}, x_{2}) = x_{1}^{2}$, which is a parabolic trough: a parabola in the $x_{1}$ direction and constant along $x_{2}$. The zero set is the line $x_{1} = 0$.
2. $\mathcal{W}_{0} = \{0\}^{d'}\times [-R,R]^{d-d'}$, which is a $(d - d')$-dimensional affine subspace of $\mathcal{W}$. Hence $\dim(\mathcal{W}_{0}) = d - d'$.
3. Since $L(w) = \sum_{i=1}^{d'}x_{i}^{2}$, the partial derivatives are

$$
\frac{\partial L}{\partial x_{i}}= \begin{cases}2x_{i}&i \leq d', \\ 0&i > d',\end{cases} \qquad \frac{\partial^{2} L}{\partial x_{i} \partial x_{j}}= \begin{cases}2 & i = j \leq d', \\ 0 & \text{otherwise}.\end{cases}
$$

So the Hessian is the block diagonal matrix:

$$
\nabla^{2} L = \begin{pmatrix}2I_{d'}&0 \\ 0&0_{d-d'}\end{pmatrix},
$$

which has rank $d'$. In particular it is positive semi-definite but not positive definite whenever $d' < d$.
4. The minimum of $L$ is $0$, achieved on $\mathcal{W}_{0}$. For any $w^{*} \in \mathcal{W}_{0}$ and $\epsilon > 0$, the sublevel set is

$$
B(w^{*}, \epsilon) = \left\{ (x_{1},\dots,x_{d}) \in [-R,R]^{d} \;\middle|\; \sum_{i=1}^{d'}x_{i}^{2} < \epsilon \right\} = \left\{x \in \mathbb{R}^{d'}: \sum_{i=1}^{d'}x_{i}^{2} < \epsilon \right\} \times [-R,R]^{d-d'}
$$

for $R$ sufficiently large (specifically $\sqrt{\epsilon}< R$). The condition $\sum_{i=1}^{d'}x_{i}^{2} < \epsilon$ can be rewritten as $\mathbf{x}^{\top} A \mathbf{x}< 1$ where $A = \epsilon^{-1}I_{d'}$. By the ellipsoid volume formula from [[#^ex-llc-regular-case|Exercise 3.1]], the volume of this region is proportional to $(\det A)^{-1/2}= (\epsilon^{-d'})^{-1/2}= \epsilon^{d'/2}$. Multiplying by the volume $(2R)^{d-d'}$ of the remaining coordinates gives $V(\epsilon) \propto \epsilon^{d'/2}$.

:::

In this example, the degenerate directions do not contribute to the leading exponent of $V(\epsilon)$. We see that the exponent $\frac{d}{2}$ from Exercise [[#^ex-llc-regular-case|3.1]] is replaced with $\frac{d'}{2}$ where $d'$ is the codimension of $\mathcal{W}_{0}$ i.e. the *effective dimension* of $L$ which ignores the degenerate directions. This suggests that we can capture information about the degree of degeneracy of a loss function by looking at how the volume $V(\epsilon)$ scales as $\epsilon \to 0$. ([[#^bib-watanabe2009|Watanabe 2009]]) proves a general form for this kind of volume scaling which has been adapted by ([[#^bib-lau-2025|Lau et al. 2025]]) into the following definition.

:::callout {title="Definition" tone="purple"}

**Definition 3.1 (Local learning coefficient).** Let $w^{*} \in \mathcal{W}$ be a local minimum of the population loss $L$. There exists a unique rational number $\lambda(w^{*}) > 0$, a positive integer $\mu(w^{*})$, and a constant $c > 0$ such that as $\epsilon \to 0$,


$$
V(\epsilon) = c \, \epsilon^{\lambda(w^*)}(-\log \epsilon)^{\mu(w^*)-1}+ o\!\left(\epsilon^{\lambda(w^*)}(-\log \epsilon)^{\mu(w^*)-1}\right).
$$


^eq-llc-volume


We call $\lambda(w^{*})$ the **local learning coefficient (LLC)** at $w^{*}$, and $\mu(w^{*})$ the **local multiplicity**.

:::

^def-llc


:::callout {title="Exercise" tone="amber"}
**Exercise 3.3 (Two equations for $\lambda$).** **(a)** Prove that for $a>1$


$$
\lambda = \lim_{\epsilon \to 0}\frac{\log(V(a\epsilon)/V(\epsilon))}{\log(a)}
$$


^eq-llc-formula


**(b)** Prove that


$$
\lambda = \lim\limits_{\epsilon\to 0}\frac{\log V(\epsilon)}{\log \epsilon}
$$


^eq-solve-llc

:::

^ex-solving-for-lambda


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. From [[#^def-llc|Definition 3.1]], as $\epsilon \to 0$,

$$
V(\epsilon) = c\,\epsilon^{\lambda}(-\log\epsilon)^{m-1}\bigl(1 + o(1)\bigr).
$$

Substituting $\epsilon \mapsto a\epsilon$,

$$
V(a\epsilon) = c\,(a\epsilon)^{\lambda}(-\log(a\epsilon))^{m-1}\bigl(1 + o(1)\bigr).
$$

Taking the ratio,

$$
\frac{V(a\epsilon)}{V(\epsilon)}= a^{\lambda}\left(\frac{-\log(a\epsilon)}{-\log\epsilon}\right)^{\!m-1}\bigl(1 + o(1)\bigr).
$$

As $\epsilon \to 0$, $-\log\epsilon \to \infty$, and

$$
\frac{-\log(a\epsilon)}{-\log\epsilon}= \frac{-\log a - \log\epsilon}{-\log\epsilon}= 1 + \frac{\log a}{-\log\epsilon}\;\xrightarrow{\epsilon\to 0}\; 1.
$$

Therefore $V(a\epsilon)/V(\epsilon) \to a^{\lambda}$. Taking logarithms and dividing by $\log a > 0$ gives the result.
2. From [[#^def-llc|Definition 3.1]], $V(\epsilon) = c\,\epsilon^{\lambda(w^*)}(-\log\epsilon)^{\mu(w^*)-1}(1 + o(1))$, so

$$
\log V(\epsilon) = \lambda(w^{*})\log\epsilon + (\mu(w^{*})-1)\log(-\log\epsilon) + \log c + o(1).
$$

Dividing by $\log\epsilon$

$$
\frac{\log V(\epsilon)}{\log\epsilon}= \lambda(w^{*}) + \frac{(\mu(w^{*})-1)\log(-\log\epsilon)}{\log\epsilon}+ \frac{\log c + o(1)}{\log\epsilon}.
$$

It remains to prove that the final two terms in this sum vanish as $\epsilon \to 0$. The final term tends to $0$ since $\log \epsilon \to -\infty$ and the numerator is bounded as $\epsilon \to 0$. Now we look at the middle term which is proportional to

$$
\lim\limits_{\epsilon\to 0}\frac{\log (-\log \epsilon)}{\log \epsilon}=\lim\limits_{x\to \infty}\frac{\log (x)}{-x}= 0,
$$

completing the proof.

:::

Note that from equation [[#^eq-regular-volume-scaling|(36)]] we already have that the LLC and local multiplicity in the regular case are $\lambda = \frac{d}{2}$, $\mu=1$

When $\mu(w^{*}) = 1$, the formula simplifies to $V(\epsilon) = c\epsilon^{\lambda(w^*)}+ o(\epsilon^{\lambda(w^*)})$ which allows us to interpret $\lambda(w^{*})$ as the *volume scaling exponent*: increasing the error tolerance by a factor of $a$ increases the volume of near-optimal parameters by a factor of $a^{\lambda(w^*)}$.

:::callout {title="Exercise" tone="blue"}
**Exercise 3.4 (Calculating the LLC).** Calculate the LLC and the rank of the Hessian at the global minimum in the following cases:

**(a)** $L(x)=x^{2}$

**(b)** $L(x) = x^{2m}$

**(c)** $L(x,y) = x^{4} + y^{4}$

**(d)** $L(x,y) = x^{2}+y^{4}$
:::

^ex-calculating-llc


:::callout {title="Solution" tone="green" collapse="closed"}

1. $V(\epsilon) = \operatorname{Vol}(\{x : x^{2} < \epsilon\}) = 2\sqrt{\epsilon}$, so $V(\epsilon) \propto \epsilon^{1/2}$ and $\lambda = 1/2$. The Hessian is $L''(0) = 2$, which has rank $1$ (full rank).
2. $V(\epsilon) = \operatorname{Vol}(\{x : x^{2m}< \epsilon\}) = 2\epsilon^{1/2m}$, so $\lambda = 1/2m$. For $m \geq 2$, the first $2m - 1$ derivatives vanish at $x = 0$, so the Hessian is $L''(0) = 0$, which has rank $0$. Since $\lambda = 1/2m < 1/2 = d/2$, the singularity makes the model effectively simpler than its parameter count suggests.
3. The sublevel set is $\{(x,y) : x^{4} + y^{4} < \epsilon\}$. Substituting $x = \epsilon^{1/4}s$, $y = \epsilon^{1/4}t$:

$$
V(\epsilon) = \epsilon^{1/2}\int\!\!\int_{\{s^4 + t^4 < 1\}}ds\, dt = c\,\epsilon^{1/2},
$$

so $\lambda = 1/2$. The Hessian at the origin is $\nabla^{2}L(0,0) = \operatorname{diag}(12x^{2}, 12y^{2})\big|_{(0,0)}= 0$, which has rank $0$.
4. The sublevel set is $\{(x,y) : x^{2} + y^{4} < \epsilon\}$. For each fixed $y$ with $|y| < \epsilon^{1/4}$, $x$ ranges over $|x| < \sqrt{\epsilon - y^{4}}$. Substituting $y = \epsilon^{1/4}t$:

$$
V(\epsilon) = \int_{-\epsilon^{1/4}}^{\epsilon^{1/4}}2\sqrt{\epsilon - y^{4}}\, dy = 2\epsilon^{1/4}\int_{-1}^{1}\sqrt{\epsilon - \epsilon t^{4}}\, dt = 2\epsilon^{3/4}\int_{-1}^{1}\sqrt{1 - t^{4}}\, dt = c\,\epsilon^{3/4},
$$

so $\lambda = 3/4$. The Hessian is $\nabla^{2}L(0,0) = \operatorname{diag}(2, 12y^{2})\big|_{(0,0)}= \operatorname{diag}(2, 0)$, which has rank $1$.

:::

:::::callout {title="Exercise" tone="amber"}
**Exercise 3.5 (Upper bound on the LLC).** In [[#^ex-llc-regular-case|Exercise 3.1]], we saw that $\lambda = d/2$ for regular models. In this exercise, you will prove directly from the volume scaling definition that for any local minimum $w^{*}$ of the population loss, the local learning coefficient satisfies $\lambda(w^{*}) \leq d/2$.

**(a)** Let $\Lambda>0$ be an upper bound on the eigenvalues of the Hessian $\nabla^{2} L(w)$ for all $w \in B(w^{*})$. Using the Lagrange remainder form of Taylor's theorem, show that for all $w \in B(w^{*})$,

$$
L(w) - L(w^{*}) \leq \frac{1}{2}\Lambda \|w - w^{*}\|^{2}.
$$

::::callout {title="Hint" tone="neutral" collapse="closed"}

for any real symmetric matrix $H\in\mathbb{R}^{n\times n}$ and vector $v\in \mathbb{R}^{n}$, $v^{\top} H v \leq \Lambda \|v\|^{2}$ where $\Lambda$ is the largest eigenvalue of $H$.

::::

**(b)** Consider the standard Euclidean ball of radius $r$ centred at $w^{*}$, denoted $B_{r}(w^{*}) = \{w \in \mathcal{W} \mid \|w - w^{*}\| < r\}$. Find a radius $r$ (as a function of $\epsilon$ and $\Lambda$) such that for sufficiently small $\epsilon$,

$$
B_{r}(w^{*}) \subseteq B(w^{*}, \epsilon).
$$

**(c)** Recall that the volume of a $d$-dimensional Euclidean ball of radius $r$ is proportional to $r^{d}$. Use your result from part (b) to show that there exists a constant $C > 0$ such that for sufficiently small $\epsilon$,

$$
C \epsilon^{d/2}\leq V(\epsilon).
$$

**(d)** Conclude that $\lambda(w^{*}) \leq d/2$.
:::::

^ex-lambda-upper-bound


:::callout {title="Solution" tone="neutral" collapse="closed"}

1. Since $w^{*}$ is a local minimum of $L$, we have $\nabla L(w^{*}) = 0$. By Taylor's theorem with Lagrange remainder, for any $w \in B(w^{*})$ there exists $\tilde{w}$ on the line segment between $w^{*}$ and $w$ such that

$$
\begin{aligned}L(w) - L(w^{*})&= \nabla L(w^{*})^{\top} (w - w^{*}) + \frac{1}{2}(\tilde w - w^{*})^{\top} \nabla^{2} L(\tilde{w})(\tilde w - w^{*}) \\&= \frac{1}{2}(\tilde w - w^{*})^{\top} \nabla^{2} L(\tilde{w})(\tilde w - w^{*}).\end{aligned}
$$

Since $\tilde{w}\in B(w^{*})$, the eigenvalues of $\nabla^{2} L(\tilde{w})$ are bounded above by $\Lambda$, so

$$
(\tilde w - w^{*})^{\top} \nabla^{2} L(\tilde{w})(\tilde w - w^{*}) \leq \Lambda \|\tilde w - w^{*}\|^{2} \leq \Lambda \|w - w^{*}\|^{2}.
$$

Combining, $L(w) - L(w^{*}) \leq \frac{1}{2}\Lambda \|w - w^{*}\|^{2}$.
2. Set $r = \sqrt{2\epsilon/\Lambda}$. Set $\epsilon$ sufficiently small that $B_{r}(w^{*}) \subseteq B(w^{*})$. If $w \in B_{r}(w^{*})$, then $\|w - w^{*}\| < r$, so by part (a),

$$
L(w) - L(w^{*}) \leq \frac{1}{2}\Lambda \|w - w^{*}\|^{2} < \frac{1}{2}\Lambda \cdot \frac{2\epsilon}{\Lambda}= \epsilon.
$$

Hence $w \in B(w^{*}, \epsilon)$, and therefore $B_{r}(w^{*}) \subseteq B(w^{*}, \epsilon)$.
3. Since $B_{r}(w^{*}) \subseteq B(w^{*}, \epsilon)$,

$$
V(\epsilon) = \operatorname{Vol}(B(w^{*}, \epsilon)) \geq \operatorname{Vol}(B_{r}(w^{*})) = c \, r^{d} = c \left(\frac{2\epsilon}{\Lambda}\right)^{d/2}= C \, \epsilon^{d/2},
$$

for some $c >0$ and $C = c (2/\Lambda)^{d/2}> 0$. This holds for all sufficiently small $\epsilon > 0$ (i.e. small enough that $B_{r}(w^{*}) \subseteq B(w^{*})$).
4. From part (c), $V(\epsilon) \geq C\epsilon^{d/2}$ for sufficiently small $\epsilon$ (w.l.o.g. assume $\epsilon < 1$). Taking logarithms,

$$
\log V(\epsilon) \geq \log C + \frac{d}{2}\log \epsilon.
$$

Dividing by $\log \epsilon < 0$ (since $\epsilon < 1$) reverses the inequality:

$$
\frac{\log V(\epsilon)}{\log \epsilon}\leq \frac{\log C}{\log \epsilon}+ \frac{d}{2}.
$$

Since $\log C / \log \epsilon \to 0$ as $\epsilon \to 0^{+}$, taking the limit and using Equation [[#^eq-solve-llc|(39)]] gives

$$
\lambda(w^{*}) = \lim_{\epsilon \to 0^+}\frac{\log V(\epsilon)}{\log \epsilon}\leq \frac{d}{2}.
$$

:::

We have now shown that the LLC satisfies $\lambda(w^{*}) \leq d/2$, with equality precisely in the regular (non-degenerate) case. It is also possible (although quite fiddly) to prove that $\frac{r}{2}\leq \lambda(w^{*})$ where $r= \mathrm{rank} \nabla^{2}L(w^{*})$ and as we will see in the next exercise, the LLC captures more information about the geometry than just the Hessian rank.

:::callout {title="Exercise" tone="blue"}
**Exercise 3.6 (LLC vs Hessian Rank).** In this exercise we will show that the LLC can detect differences in the local geometry that is not reflected in the rank of the Hessian.

Construct two loss functions $L_{1}$ and $L_{2}$ with minima $w_{1}$ and $w_{2}$ respectively such that $\mathrm{rank} \, \nabla^{2}L_{1}(w_{1}) = \mathrm{rank} \, \nabla^{2}L_{2}(w_{2})$ but $\lambda(w_{1}) \neq \lambda(w_{2})$.
:::

^ex-llc-hessian-rank


:::callout {title="Solution" tone="green" collapse="closed"}

Let $L_{1}(x,y) = x^{2}+y^{4}$ with $w_{1} = (0,0)$. Then $\nabla^{2}L_{1}(0,0) = \operatorname{diag}(2, 0)$, so $\operatorname{rank}\nabla^{2}L_{1}(0,0) = 1$. By [[#^ex-calculating-llc|Exercise 3.4]], $\lambda(w_{1}) = \frac{3}{4}$.

Let $L_{2}(x,y) = x^{2}$ with $w_{2} = (0,0)$. Then $\nabla^{2}L_{2}(0,0) = \operatorname{diag}(2, 0)$, so $\operatorname{rank}\nabla^{2}L_{2}(0,0) = 1$. The minimiser locus is $\{x = 0\}$, which is the setting of [[#^ex-quad-valley-scaling|Exercise 3.2]] with $d' = 1$, giving $\lambda(w_{2}) = \frac{1}{2}$.

Both Hessians have rank $1$, but $\lambda(w_{1}) = \frac{3}{4}\neq \frac{1}{2}= \lambda(w_{2})$. The difference is that the flat direction in $L_{2}$ is *exactly* flat (the minimisers form a line), while in $L_{1}$ it is only flat to second order but quartic beyond that. The LLC detects this distinction; the Hessian rank does not.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 3.7 (The cubically-parameterised loss).** We can make a quadratic loss degenerate by changing the parameterisation. Let the *cubically-parameterised loss* be

$$
L(\mu) = \tfrac{1}{2}(\mu^{3} - \mu_{0}^{3})^{2}, \qquad \mu \in \mathbb{R}
$$

obtained from the ordinary quadratic loss $\ell(\theta) = \frac{1}{2}(\theta - \theta_{0})^{2}$ via the reparameterisation $\theta = \mu^{3}$, $\theta_{0} = \mu_{0}^{3}$.

**(a)** Show that the cubically-parameterised loss is just as expressive as the ordinary quadratic loss: that is, they both have the same set of achievable minima.

**(b)** Compute the Hessian $L''(\mu_{0})$ to show that the loss is degenerate at its minimum when $\mu_{0} = 0$, and non-degenerate when $\mu_{0} \neq 0$.

**(c)** Give an explicit formula for $V(\epsilon)$ when $\mu_{0} = 0$ and $\mu_{0} \neq 0$ separately.

**(d)** Use your answer to part (c) to find the learning coefficient for $\mu_{0}=0$ and for $\mu_{0}\neq0$. Given that the model is non-degenerate when $\mu_{0} \neq 0$, we expect the learning coefficient to be $d/2$ in that case; compare your answer. How does the cubically-parameterised loss at $\mu_{0} = 0$ differ from the ordinary quadratic loss?

**(e)** Instead of taking $\epsilon \to 0$ to get the learning coefficient, fix a small but nonzero value for $\epsilon$, such as $\epsilon = 0.01$. Plot $V(\epsilon)$ as a function of $\mu_{0}$. As we saw from (d), the learning coefficient changes discontinuously when $\mu_{0} = 0$—what happens with $V(\epsilon)$ as $\mu_{0}$ gets close to zero? What changes if you make $\epsilon$ smaller or larger?

Even though the asymptotic *learning coefficient* ($\epsilon \to 0$) only changes when $\mu_{0} = 0$ exactly, note how the non-asymptotic *volume* ($\epsilon$ finite) is affected in a larger neighbourhood.
:::

^ex-cubic-parameterisation


:::callout {title="Solution" tone="green" collapse="closed"}

1. The cubically-parameterised loss $L(\mu) = \tfrac{1}{2}(\mu^{3} - \mu_{0}^{3})^{2}$ vanishes if and only if $\mu^{3} = \mu_{0}^{3}$, i.e.  $\mu = \mu_{0}$ (since $t \mapsto t^{3}$ is a bijection on $\mathbb{R}$). The ordinary quadratic loss $\ell(\theta) = \tfrac{1}{2}(\theta - \theta_{0})^{2}$ vanishes if and only if $\theta = \theta_{0}$. Since for every $\theta_{0} \in \mathbb{R}$ we can write $\theta_{0} = \mu_{0}^{3}$ for a unique $\mu_{0} = \theta_{0}^{1/3}$, both losses achieve their minimum value of zero at exactly the same set of "targets" $\theta_{0} \in \mathbb{R}$, so the set of achievable minima is the same.
2. Computing derivatives:

$$
\begin{aligned}L'(\mu)&= 3\mu^{2}(\mu^{3} - \mu_{0}^{3}), \\ L''(\mu)&= 6\mu(\mu^{3} - \mu_{0}^{3}) + 9\mu^{4}.\end{aligned}
$$

At the minimum $\mu = \mu_{0}$: $L''(\mu_{0}) = 6\mu_{0} \cdot 0 + 9\mu_{0}^{4} = 9\mu_{0}^{4}$.

- If $\mu_{0} = 0$: $L''(0) = 0$, so the Hessian vanishes and the loss is degenerate at its minimum.
- If $\mu_{0} \neq 0$: $L''(\mu_{0}) = 9\mu_{0}^{4} > 0$, so the loss is non-degenerate.
3. We compute $V(\epsilon) = \mathrm{vol}(\{\mu \in \mathbb{R} : L(\mu) < \epsilon\})$ in each case.

*Case $\mu_{0} = 0$.* When $\mu_{0} = 0$ the loss simplifies to $L(\mu) = \tfrac{1}{2}\mu^{6}$, so

$$
V(\epsilon) = \int_{\frac{1}{2}\mu^6 < \epsilon}d\mu = \int_{|\mu| < (2\epsilon)^{1/6}}d\mu = 2(2\epsilon)^{1/6}= 2^{7/6}\,\epsilon^{1/6}.
$$

*Case $\mu_{0} \neq 0$.* The sublevel set condition $L(\mu) < \epsilon$ is $\tfrac{1}{2}(\mu^{3} - \mu_{0}^{3})^{2} < \epsilon$, i.e.

$$
\mu_{0}^{3} - \sqrt{2\epsilon}\;<\; \mu^{3} \;<\; \mu_{0}^{3} + \sqrt{2\epsilon}.
$$

Since the cube root is monotone on $\mathbb{R}$, this is equivalent to

$$
\bigl(\mu_{0}^{3} - \sqrt{2\epsilon}\bigr)^{1/3}\;<\; \mu \;<\; \bigl(\mu_{0}^{3} + \sqrt{2\epsilon}\bigr)^{1/3},
$$

and therefore

$$
V(\epsilon) = \bigl(\mu_{0}^{3} + \sqrt{2\epsilon}\bigr)^{1/3}- \bigl(\mu_{0}^{3} - \sqrt{2\epsilon}\bigr)^{1/3}.
$$
4. **Case $\mu_{0} = 0$:** $V(\epsilon) \propto \epsilon^{1/6}$, so $\lambda = \tfrac{1}{6}$.

**Case $\mu_{0} \neq 0$:** For small $\epsilon$ we expand by factoring out $\mu_{0}$:

$$
V(\epsilon) = \mu_{0} \left[ \left(1 + \frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}\right)^{\!1/3}- \left(1 - \frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}\right)^{\!1/3}\right].
$$

Applying the binomial expansion $(1+x)^{1/3}= 1 + \tfrac{1}{3}x + o(x)$ to each term with $x = \pm\frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}$, the constant terms cancel and the linear terms add:

$$
V(\epsilon) = \mu_{0} \left[ \frac{1}{3}\frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}+ \frac{1}{3}\frac{\sqrt{2\epsilon}}{\mu_{0}^{3}}+ o(\epsilon^{1/2}) \right] = \frac{2\sqrt{2}}{3\mu_{0}^{2}}\,\epsilon^{1/2}+ o(\epsilon^{1/2}).
$$

In the non-degenerate case $\mu_{0} \neq 0$, we recover the regular value $\lambda = d/2 = 1/2$ as expected. In the degenerate case $\mu_{0} = 0$, $\lambda = 1/6 < 1/2$: the singularity at $\mu = 0$ (where the loss vanishes to sixth order rather than second order) makes the model effectively simpler than its parameter count suggests.
5. From part (c), for fixed $\epsilon > 0$ we plot

$$
V(\epsilon;\, \mu_{0}) = \bigl(\mu_{0}^{3} + \sqrt{2\epsilon}\bigr)^{1/3}- \bigl(\mu_{0}^{3} - \sqrt{2\epsilon}\bigr)^{1/3}
$$

The function is a smooth, symmetric bump centred at $\mu_{0} = 0$ with no discontinuity. Making $\epsilon$ smaller narrows the bump and lowers the peak; making $\epsilon$ larger widens it. Despite the learning coefficient jumping discontinuously from $1/2$ to $1/6$ at $\mu_{0} = 0$ exactly, the finite-$\epsilon$ volume transitions smoothly, with the singularity's influence confined to a neighbourhood that shrinks as $\epsilon \to 0$.

:::

\### 3.2 Perspectives on the local learning coefficient

In this section, we survey several alternative perspectives on the LLC, from information theory, algebraic geometry, and geometric measure theory.

**Information-theoretic interpretation.**

The LLC also admits a natural interpretation in terms of information ([[#^bib-lau-2025|Lau et al. 2025]]). The number of bits needed to specify the sublevel set $B(w^{*}, \epsilon)$ within the ball $B(w^{*})$ is

$$
-\log_{2} \frac{V(\epsilon)}{\mathrm{Vol}(B(w^{*}))}.
$$

For small $\epsilon$ and $\mu(w^{*}) = 1$, this is approximately $-\lambda(w^{*}) \log_{2} \epsilon + O(\log_{2} \log_{2} \epsilon)$. In particular, the number of *additional* bits needed to halve an already small error tolerance from $\epsilon$ to $\epsilon/2$ is

$$
-\log_{2} \frac{V(\epsilon / 2)}{V(\epsilon)}\approx \lambda(w^{*}).
$$

That is, the LLC $\lambda(w^{*})$ measures the number of bits required to halve the error near $w^{*}$.

**Local learning coefficient via algebraic geometry.**

We explore an algebro-geometric perspective on the learning coefficient due to [[#^bib-watanabe2009|Watanabe 2009]]. Note that this section is more advanced than the remainder of this tutorial, and should be considered optional. When $L(w)$ is a real analytic function, Hironaka's resolution of singularities theorem guarantees the existence of a smooth map $g \colon M \to \mathcal{W}$ from an analytic manifold $M$ and local coordinates $u = (u_{1}, \ldots, u_{d})$ that *monomialise* the loss near $w^{*}$:

$$
L(g(u)) - L(w^{*}) = u_{1}^{2k_1}\cdots u_{d}^{2k_d}, \qquad dw = b(u)\, u_{1}^{h_1}\cdots u_{d}^{h_d}\, du,
$$

where $b(u) > 0$ is smooth and the exponents $k_{j}, h_{j}$ are non-negative integers. In these coordinates, the volume integral $V(\epsilon)$ can be evaluated explicitly, yielding the asymptotic form of [[#^def-llc|Definition 3.1]] and giving


$$
\lambda(w^{*}) \;=\; \min_{\text{coordinate charts}}\; \min_{j:\, k_j > 0}\frac{h_{j} + 1}{2k_{j}}\,.
$$


^eq-rlct


The resolution map $g$ is far from unique, and different choices produce different exponents $k_{j}, h_{j}$. $\lambda(w^{*})$ is nevertheless well-defined which can be seen from (another) equivalent definition using the **local zeta function**:


$$
\zeta(z,\, w^{*}) \;=\; \int_{B(w^*)}\bigl(L(w) - L(w^{*})\bigr)^{\!z}\, dw\,,
$$


^eq-local-zeta


which converges for $\operatorname{Re}(z) > 0$ and extends to a meromorphic function on $\mathbb{C}$ whose poles are all real, negative, and rational. The LLC $\lambda(w^{*})$ is precisely the negative of the largest pole, and the multiplicity $\mu(w^{*})$ is the multiplicity of this pole. Since [[#^eq-local-zeta|(44)]] makes no reference to any resolution, $\lambda(w^{*})$ depends only on $L$ and $w^{*}$.

In the algebraic geometry literature, $\lambda(w^{*})$ is called the **real log canonical threshold (RLCT)** of $L$ at $w^{*}$. We collect several consequences of this perspective.

1. The fact that the LLC is a rational number follows directly from equation [[#^eq-rlct|(43)]].
2. Equation [[#^eq-rlct|(43)]] suggests that we can compute $\lambda(w^{*})$ analytically by constructing an explicit resolution of singularities for $L(w) - L(w^{*})$ and reading off the exponents. This is difficult in practice for neural network loss functions, but has been achieved for some architectures, as we will see in [[#3.3 Local learning coefficients of deep linear networks|Subsection 3.3]].
3. In [[#4. Degeneracy and Bayesian deep learning|Section 4]] we will state Watanabe's free energy formula connecting the Bayesian free energy to the LLC. The proof of this result makes repeated use of the monomialisation of the loss.

:::callout {title="Exercise" tone="blue"}
**Exercise 3.8 (Computing the LLC via the RLCT).** Suppose that $L(w) = w_{1}^{2k_1}\cdots w_{d}^{2k_d}$ near $w^{*} = 0$, where $k_{j} \geq 0$ are integers with at least one $k_{j} > 0$. Show that

$$
\lambda(0) = \min_{j:\, k_j > 0}\frac{1}{2k_{j}}\,.
$$
:::

^ex-rlct-computation


:::callout {title="Solution" tone="green" collapse="closed"}

The loss $L(w) = w_{1}^{2k_1}\cdots w_{d}^{2k_d}$ is already in monomial form, so the identity map $g = \mathrm{id}$ serves as a (trivial) resolution of singularities with $dw = 1 \cdot du$, i.e. $h_{j} = 0$ for all $j$. Substituting into [[#^eq-rlct|(43)]] gives

$$
\lambda(0) \;=\; \min_{j:\, k_j > 0}\frac{0 + 1}{2k_{j}}\;=\; \min_{j:\, k_j > 0}\frac{1}{2k_{j}}\,.
$$

:::

**Local learning coefficient as a fractal dimension.**

The LLC admits a geometric interpretation: it is a *fractal dimension* of the parameter space, as measured through the lens of the loss function. To make this precise, we recall a standard notion from fractal analysis.

:::callout {title="Definition" tone="purple"}

**Definition 3.2 (Hölder exponent).** Let $(X, \rho)$ be a (pseudo-)metric space and $\nu$ a measure on $X$. The **Hölder exponent** (or **local dimension**) $\alpha(x)$ of $\nu$ at a point $x \in X$ is given by


$$
\alpha(x) = \lim_{\epsilon \to 0}\frac{\log \nu(B_{\epsilon}(x))}{\log \epsilon},
$$


^eq-holder-exp


where $B_{\epsilon}(x)$ is the ball of radius $\epsilon$ centred at $x$. Equivalently, $\alpha(x)$ is the unique real number such that

$$
\nu(B_{\epsilon}(x)) = O(\epsilon^{\alpha(x)}) \qquad \text{as }\epsilon \to 0.
$$

:::

^def-holder-exponent


The Hölder exponent generalises the notion of dimension: when $\nu$ is the Lebesgue measure on $\mathbb{R}^{d}$ and $\rho$ is the Euclidean metric, every point has $\alpha(x) = d$, but for measures concentrated on fractal sets the exponent can be non-integer. Notice that the formula [[#^eq-holder-exp|(45)]] has a similar form to the definition of the local learning coefficient [[#^eq-llc-formula|(38)]]. To make this connection precise, we introduce a pseudo-metric induced by the loss function.

:::callout {title="Definition" tone="purple"}

**Definition 3.3 (Loss pseudo-metric).** The **loss pseudo-metric** on $\mathcal{W}$ is defined by

$$
\rho(w,u) = |L(w) - L(u)|.
$$

:::

^def-loss-metric


:::callout {title="Note" tone="neutral"}

**Remark.** $\rho$ is only a pseudo-metric as the distance between two distinct points can be zero.

:::

Under this pseudo-metric, the sublevel set [[#^eq-sublevel-set|(34)]] is precisely the $\epsilon$-ball around $w^{*}$:

$$
B(w^{*}, \epsilon) = \{ w \in B(w^{*}) \mid \rho(w, w^{*}) < \epsilon \},
$$

so $V(\epsilon) = \nu(B(w^{*}, \epsilon))$.

:::callout {title="Exercise" tone="blue"}
**Exercise 3.9 (Holder exponent and learning coefficient).** Let $\alpha(w^{*})$ be the Hölder exponent of the Lebesgue measure on $\mathcal{W}$ at $w^{*}$ under the loss pseudo-metric. Show that

$$
\lambda(w^{*}) = \alpha(w^{*}).
$$
:::

^ex-holder-llc


:::callout {title="Solution" tone="green" collapse="closed"}

Under the loss pseudo-metric $\rho(w,u) = |L(w) - L(u)|$, the $\epsilon$-ball centred at $w^{*}$ (within $B(w^{*})$) is

$$
B_{\epsilon}(w^{*}) = \{w \in B(w^{*}) : |L(w) - L(w^{*})| < \epsilon\}.
$$

Since $w^{*}$ is a local minimum and $L(w) \geq L(w^{*})$ on $B(w^{*})$, this simplifies to $B_{\epsilon}(w^{*}) = \{w \in B(w^{*}) : L(w) - L(w^{*}) < \epsilon\} = B(w^{*},\epsilon)$, the sublevel set from [[#^eq-sublevel-set|(34)]]. In particular, $\nu(B_{\epsilon}(w^{*})) = V(\epsilon)$ where $\nu$ is Lebesgue measure.

The Holder exponent is therefore

$$
\alpha(w^{*}) = \lim_{\epsilon\to 0}\frac{\log \nu(B_{\epsilon}(w^{*}))}{\log\epsilon}= \lim_{\epsilon\to 0}\frac{\log V(\epsilon)}{\log\epsilon}= \lambda
$$

by Equation [[#^eq-solve-llc|(39)]]

:::

\### 3.3 Local learning coefficients of deep linear networks

Having established the local learning coefficient as a measure of degeneracy in the loss landscape, we now compute it explicitly for the two-layer deep linear network introduced in [[#1. Preliminaries|Section 1]]. In [[#2. What is degeneracy?|Section 2]], we saw that DLN parameters exhibit varying degrees of degeneracy depending on the ranks of the component matrices ([[#^ex-dln-degeneracy|Exercise 2.9]], [[#^rem-rank|Remark 2.2]]). The LLC makes this hierarchy quantitative: different ranks correspond to different learning coefficients, confirming that lower-rank parameters are geometrically "simpler."

Consider the two-layer DLN $f_{A,B}(x) = BAx$ with $A \in \mathbb{R}^{H \times M}$ and $B \in \mathbb{R}^{N \times H}$, so the parameter space is $\mathcal{W} = \mathbb{R}^{(M+N)H}$. Suppose the true input–output relationship is $y = B_{0} A_{0} x$ where $A_{0} \in \mathbb{R}^{H \times M}$, $B_{0} \in \mathbb{R}^{N \times H}$, and $r = \mathrm{rank}(B_{0} A_{0})$, and consider the population loss

$$
L(A, B) = \mathbb{E}_{x \sim q(x)}\!\left[\|BAx - B_{0} A_{0} x\|^{2}\right],
$$

where $q(x)$ has full-rank covariance. The set of minima of this loss function is $W_{0} = \{(A, B) : BA = B_{0} A_{0}\}$. [[#^bib-aoyagi-watanabe2005|Aoyagi & Watanabe 2005]] derived an exact formula for the learning coefficient at these minima.

:::callout {title="Theorem" tone="purple"}

**Theorem 3.4 ([[#^bib-aoyagi-watanabe2005|Aoyagi & Watanabe 2005]]).** For the two-layer DLN $f_{A,B}(x) = BAx$ with $A \in \mathbb{R}^{H \times M}$, $B \in \mathbb{R}^{N \times H}$, and true parameter $(A_{0}, B_{0})$ with $r = \mathrm{rank}(B_{0} A_{0})$, at any minimum $w^{*} \in W_{0}$ the local learning coefficient $\lambda$ and its multiplicity $\mu$ are given by the following cases:

1. If $N + r \leq M + H$,   $M + r \leq N + H$,   and   $H + r \leq M + N$:

1. If $M + H + N + r$ is even, then $\mu = 1$ and

$$
\lambda = \frac{-(H+r)^{2} - M^{2} - N^{2} + 2(H+r)M + 2(H+r)N + 2MN}{8}.
$$
2. If $M + H + N + r$ is odd, then $\mu = 2$ and

$$
\lambda = \frac{-(H+r)^{2} - M^{2} - N^{2} + 2(H+r)M + 2(H+r)N + 2MN + 1}{8}.
$$
2. If $M + H < N + r$, then $\mu = 1$ and $\displaystyle\lambda = \frac{HM - Hr + Nr}{2}$.
3. If $N + H < M + r$, then $\mu = 1$ and $\displaystyle\lambda = \frac{HN - Hr + Mr}{2}$.
4. If $M + N < H + r$, then $\mu = 1$ and $\displaystyle\lambda = \frac{MN}{2}$.

:::

^thm-aoyagi-watanabe


:::callout {title="Exercise" tone="blue"}
**Exercise 3.10 (Learning coefficients of two-layer DLNs).** Consider the constant-width two-layer DLN from [[#^ex-dln-degeneracy|Exercise 2.9]]: $y = BAx$, where $x \in \mathbb{R}^{m}$ are the inputs, $y \in \mathbb{R}^{m}$ are the outputs, and $A, B \in \mathbb{R}^{m \times m}$ are linear transformations. The parameter space is $\mathcal{W} = \mathbb{R}^{2m^2}$ and the parameters are the pair $(A, B) \in \mathcal{W}$.

**(a)** Aoyagi & Watanabe do not assume the network is constant-width, like we do. Simplify their formula for $\lambda$ using this assumption.

**(b)** How does the learning coefficient $\lambda$ depend on $r$, the rank of $B_{0} A_{0}$? Compare with the results of [[#^ex-dln-degeneracy|Exercise 2.9(d)]].

**(c)** How does $\lambda$ compare with the effective parameter count $d/2$ of a regular model? What does this tell us about the role of singularities in the two-layer DLN?
:::

^ex-dln-lc


:::callout {title="Solution" tone="green" collapse="closed"}

1. We first check which case of [[#^thm-aoyagi-watanabe|Theorem 3.4]] applies. Setting $M = N = H = m$, the three conditions of Case 1 each reduce to $m + r \leq 2m$, i.e. $r \leq m$, which always holds. So we are always in Case 1. The parity condition is on $M + H + N + r = 3m + r$, which has the same parity as $m + r$.

**Case 1(a):** $m + r$ even. Setting $M = N = H = m$ in the formula:

$$
\begin{aligned}\lambda&= \frac{-(m+r)^{2} - m^{2} - m^{2} + 2(m+r)m + 2(m+r)m + 2m^{2}}{8}\\&= \frac{-(m+r)^{2} + 4m(m+r)}{8}\\&= \frac{(m+r)\bigl(4m - (m+r)\bigr)}{8}\\&= \frac{(m+r)(3m-r)}{8},\end{aligned}
$$

with $\mu = 1$.

**Case 1(b):** $m + r$ odd. The same calculation gives

$$
\lambda = \frac{(m+r)(3m - r) + 1}{8},
$$

with $\mu = 2$.
2. Differentiating with respect to $r$:

$$
\frac{d\lambda}{dr}=\frac{1}{8}\frac{d}{dr}\!\left[(m+r)(3m-r)\right] = \frac{1}{8}\left[(3m - r) - (m + r)\right] = \frac{1}{4}(m - r) \geq 0,
$$

so $\lambda$ is increasing in $r$ therefore **lower rank $\implies$ lower $\lambda$**. This is consistent with [[#^ex-dln-degeneracy|Exercise 2.9(d)]] where we saw that at lower-rank parameters, more directions in parameter space are degenerate.
3. The parameter space is $\mathcal{W} = \mathbb{R}^{2m^2}$, so the regular-model baseline is $d/2 = m^{2}$. At full rank $r = m$:

$$
\lambda = \frac{(2m)(2m)}{8}= \frac{m^{2}}{2}= \frac{d}{4},
$$

which is already half the regular-model value. At rank $r = 0$:

$$
\lambda = \frac{m \cdot 3m}{8}= \frac{3m^{2}}{8}= \frac{3d}{16},
$$

even smaller. In fact $\lambda < d/2$ for every rank $0 \leq r \leq m$.

This tells us that the two-layer DLN is singular at every point in its loss landscape, even at full-rank parameters.

:::

\## 4. Degeneracy and Bayesian deep learning

In [[#2. What is degeneracy?|Section 2]] and [[#3. The degeneracy hierarchy|3]], we studied the geometry of degeneracy in parameter space and introduced the local learning coefficient $\lambda(w^{*})$ as a measure of the degree of degeneracy at a local minimum $w^{*}$. We now show that this geometry has consequences for learning (in the Bayesian setting). In particular, it creates a trade-off between model fit and model complexity that drives learning, providing a mechanism for *internal model selection*.

\### 4.1 Watanabe's free energy formula

Recall the Bayesian learning setup from [[#1.4 Bayesian deep learning|Subsection 1.4]]. We have a parameter–distribution map $\Psi : \mathcal{W} \to \mathcal{D}$ sending each parameter $w$ to a conditional distribution with density $p(y \mid x, w)$, a smooth positive prior $\varphi$ on $\mathcal{W}$, and a data set of $n$ i.i.d. examples from a data distribution $q$. Take the loss function to be the negative log-likelihood

$$
L_{n}(w) = -\frac{1}{n}\sum_{i=1}^{n} \log p(y^{(i)}\mid x^{(i)}, w), \qquad L(w) = \mathbb{E}_{(x,y) \sim q}\!\left[-\log p(y \mid x, w)\right].
$$

The posterior $\pi_{n}$ is given by Bayes' rule [[#^eq-posterior|(13)]] and as we saw in [[#^ex-posterior-free-energy|Exercise 1.7]] and [[#^ex-partition-decomposition|1.8]] it concentrates around regions of parameter space with the lowest local free energy $F_{n}(\mathcal{U})$ ([[#^def-local-free-energy|Definition 1.6]]).

We now state one of the main results of SLT: an asymptotic expansion of $F_{n}(\mathcal{U})$ as $n \to \infty$. Under certain technical assumptions on the statistical model ([[#^bib-watanabe2018|Watanabe 2018]]; see [[#^bib-lau2025|Lau 2025]], § 2.3.1 for a summary), we have the following theorem.

:::callout {title="Theorem" tone="purple"}

**Theorem 4.1 (Local free energy formula).** Suppose $\mathcal{U} \subseteq \mathcal{W}$ contains at least one minimiser of $L$, and let $w^{*} \in \mathcal{U}$ be any such minimiser. Define $\lambda_{\mathcal{U}}$ as the smallest local learning coefficient among all minimisers in $\mathcal{U}$, and let $\mu_{\mathcal{U}}$ be the maximum local multiplicity associated with $\lambda_{\mathcal{U}}$. Then, as $n \to \infty$,


$$
F_{n}(\mathcal{U}) = nL_{n}(w^{*}) + \lambda_{\mathcal{U}}\log n - (\mu_{\mathcal{U}}- 1)\log \log n + O_{p}(1).
$$


^eq-fef


:::

^thm-fef


:::callout {title="Note" tone="neutral"}

**Remark.** Since $L_{n}(w^{*})$ is a random variable, so is $F_{n}(\mathcal{U})$. The expansion [[#^eq-fef|Equation 49]] is an asymptotic statement about random variables where the remainder $O_{p}(1)$ denotes a term that is bounded in probability as $n \to \infty$.

:::

To understand what this expansion tells us about Bayesian learning, note that the two leading terms of this expansion have transparent interpretations:

$$
F_{n} \;\approx\; \underbrace{n L_n\vphantom{\lambda}}_{\text{data fit}}\;+\; \underbrace{\lambda \log n}_{\text{complexity}}
$$

Let $w_{1}, w_{2} \in \mathcal{W}$ be minimisers of the population loss with $L(w_{1}) = L(w_{2})$ and $\lambda(w_{1}) \leq \lambda(w_{2})$. Then for fixed large $n$, the free energy of a neighbourhood of $w_{1}$ is smaller than that of $w_{2}$, so the posterior concentrates around the simpler solution $w_{1}$.

This is an example of **internal model selection** where there are two equally good solutions that minimise the population loss. However, our learning algorithm (Bayesian updating) prefers one solution over the other, in particular the one with lower complexity.

:::callout {title="Note" tone="neutral"}

**Remark (Regular models and the BIC).** When the Hessian $\nabla^{2} L(w^{*})$ is non-degenerate, $\lambda(w^{*}) = d/2$ and $\mu(w^{*}) = 1$ by [[#^ex-llc-regular-case|Exercise 3.1]]. The free energy formula then reduces to $F_{n} \approx n L_{n}(w^{*}) + \frac{d}{2}\log n$, recovering the Bayesian Information Criterion from classical statistics.

:::

:::callout {title="Exercise" tone="blue"}
**Exercise 4.1 (Numerical demonstration of the free energy formula).** Consider the statistical model underlying the cubically-parameterised loss from [[#^ex-cubic-parameterisation|Exercise 3.7]]. The parameter $\mu \in \mathbb{R}$ indexes the family of normal distributions

$$
p(x \mid \mu) = (2\pi)^{-1/2}\exp\!\left(-\frac{1}{2}(x - \mu^{3})^{2}\right).
$$

Suppose the true distribution is

$$
q(x) = (2\pi)^{-1/2}\exp\!\left(-\frac{1}{2}(x - \mu_{0}^{3})^{2}\right)
$$

for some fixed $\mu_{0}$, and equip the model with a standard normal prior

$$
\varphi(\mu) = (2\pi)^{-1/2}\exp\!\left(-\frac{1}{2}\mu^{2}\right).
$$

[*Note:* The following exercises are intended to be attempted with a numerical programming framework such as Python or Julia, rather than by hand.]

**(a)** For $\mu_{0} = 0$, numerically compute the free energy $F_{n}$ for many values of $n$ between $n = 100$ and $n = 10{,}000$. Compare the computed values against the asymptotic estimate $F_{n} \approx nL_{n} + \lambda \log n$, using the value of $\lambda$ from [[#^ex-cubic-parameterisation|Exercise 3.7(d)]].

**(b)** Repeat part (a) with $\mu_{0} = 5$.

**(c)** Repeat part (a) with $\mu_{0} = 0.1$. Note that $\mu_{0} = 0.1 \neq 0$, so asymptotically $\lambda = 1/2$, as in part (b). However, observe how for moderate $n$ the free energy behaves more like part (a) than part (b). This is another manifestation of the phenomenon from [[#^ex-cubic-parameterisation|Exercise 3.7(e)]]: the effects of the singularity at $\mu = 0$ extend into a neighbourhood around it.
:::

^ex-fef-numerical


:::callout {title="Solution" tone="green" collapse="closed"}

This exercise is computational. We outline the procedure and key observations.

The model is $p(x \mid \mu) = (2\pi)^{-1/2}\exp\!\big({-}\tfrac{1}{2}(x - \mu^{3})^{2}\big)$ with prior $\varphi(\mu) = (2\pi)^{-1/2}\exp(-\mu^{2}/2)$ and true distribution $q(x) = (2\pi)^{-1/2}\exp\!\big({-}\tfrac{1}{2}(x-\mu_{0}^{3})^{2}\big)$.

For each $n$, sample $x^{(1)}, \ldots, x^{(n)}\sim q$ and compute

$$
Z_{n} = \int_{-\infty}^{\infty}\varphi(\mu) \prod_{i=1}^{n} p(x^{(i)}\mid \mu)\, d\mu
$$

the then set $F_{n} = -\log Z_{n}$.

The empirical loss is

$$
L_{n}(\mu) = -\frac{1}{n}\sum_{i=1}^{n} \log p(x^{(i)}\mid \mu) = \frac{1}{2}\log(2\pi) + \frac{1}{2n}\sum_{i=1}^{n} (x^{(i)}- \mu^{3})^{2}.
$$

1. For $\mu_{0} = 0$, the LLC is $\lambda = 1/6$ ([[#^ex-cubic-parameterisation|Exercise 3.7]]). Plot $F_{n}$ against $n$ and compare with the asymptotic estimate $\hat F_{n} = n L_{n}(0) + \tfrac{1}{6}\log n$. For large $n$, the two curves should agree up to an $O(1)$ offset: $F_{n} - \hat F_{n}$ should stabilise around a constant.
2. For $\mu_{0} = 5$, the LLC is $\lambda = 1/2$ (regular case). The asymptotic estimate is $\hat F_{n} = n L_{n}(5) + \tfrac{1}{2}\log n$.
3. For $\mu_{0} = 0.1$, the asymptotic LLC is $\lambda = 1/2$ (since $\mu_{0} \neq 0$). However, the minimum of $L$ is at $\mu = \mu_{0} = 0.1$, very close to the singularity at $\mu = 0$ where $\lambda = 1/6$. For moderate $n$, the posterior is spread broadly enough that it "feels" the nearby singularity, and $F_{n}$ behaves more like the $\lambda = 1/6$ regime from part (a). Only for sufficiently large $n$ does the posterior concentrate tightly enough around $\mu_{0} = 0.1$ for the regular $\lambda = 1/2$ asymptotics to take hold. This demonstrates that the singularity at $\mu = 0$ influences learning even when $\mu_{0} \neq 0$, provided $\mu_{0}$ is close to the singular point.

:::

\### 4.2 Bayesian phase transitions

So far we have looked at the consequence of the free energy formula when considering $n$ to be fixed. However, we also find it interesting to see what it tells us about changes in the posterior as $n$ increases.

For the rest of this section, assume $n$ is sufficiently large that (i) the free energy can be approximated by the first two terms in its expansion, and (ii) $L_{n} \approx L$ by the law of large numbers, so that the empirical loss can be treated as approximately constant in $n$.

Consider two disjoint regions $\mathcal{U}, \mathcal{V} \subseteq \mathcal{W}$, containing minimisers $u^{\ast}$ and $v^{\ast}$ of the population loss $L$ with local learning coefficients $\lambda_{\mathcal{U}}$ and $\lambda_{\mathcal{V}}$ respectively. Applying the free energy formula to each region, the log posterior odds between the two regions satisfy


$$
\log \frac{\pi_{n}(\mathcal{U})}{\pi_{n}(\mathcal{V})}= F_{n}(\mathcal{V}) - F_{n}(\mathcal{U}) \approx n\,\Delta L_{n} + \Delta\lambda \cdot \log n
$$


^eq-log-odds


where $\Delta L_{n} = L_{n}(v^{\ast}) - L_{n}(u^{\ast})$ and $\Delta\lambda = \lambda_{\mathcal{V}}- \lambda_{\mathcal{U}}$.

Consider the case when one region is more accurate but more complex than the other i.e.

$$
L_{n}(u^{\ast}) > L_{n}(v^{\ast}) \qquad\text{and}\qquad \lambda_{\mathcal{U}}< \lambda_{\mathcal{V}}.
$$

Then $\Delta L_{n} < 0$ and $\Delta\lambda > 0$, so the two terms in [[#^eq-log-odds|(50)]] have opposite signs. For smaller $n$, the $\Delta\lambda \cdot \log n$ term dominates so the log posterior odds is negative meaning the posterior prefers $\mathcal{U}$ (the simpler, less accurate region). As $n$ increases, the linear term $n\,\Delta L_{n}$ eventually dominates the logarithmic term, and the posterior shifts to prefer $\mathcal{V}$ (the more complex, more accurate region). Setting the leading terms equal, this change occurs at a critical sample size $n^{*}$ satisfying


$$
\frac{n^{*}}{\log n^{*}}\approx \frac{\Delta\lambda}{\lvert\Delta L_{n}\rvert}.
$$


^eq-critical-n


At $n = n^{*}$, the posterior undergoes a **Bayesian phase transition**: the region that dominates the posterior changes abruptly.

:::callout {title="Exercise" tone="blue"}
**Exercise 4.2 (Exploring phase transitions).** We show how *phase transitions* can occur when different local free energies change at different rates.

**(a)** Suppose we partition the overall parameter space into a disjoint union $\mathcal{W} = \mathcal{U} \sqcup \mathcal{V}$. Denote the overall free energy by $F_{n}$ and the local free energies by $F_{n}(\mathcal{U})$ and $F_{n}(\mathcal{V})$, respectively. Show that the relationship

$$
F_{n} = -\log(e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})})
$$

holds.

**(b)** Suppose $F_{n}(\mathcal{U}) \approx 0.3n + 20 \log n$ and $F_{n}(\mathcal{V}) \approx 0.5n + 2 \log n$. Plot the overall free energy $F(n)$. Compare against $\min\{F_{n}(U), F_{n}(\mathcal{V})\}$. What happens around $n = 570$?

**(c)** In statistical physics, a phase transition is traditionally defined as a discontinuity (or rapid change, for finite-size systems) in the derivatives of the free energy. Plot $\frac{d}{dn}F_{n}$ and explain why this justifies calling the phenomenon from b) a phase transition.

**(d)** Change the coefficients of the terms in b). How does this change when a phase transition occurs? Does a phase transition always occur?
:::

^ex-phase-transitions


:::callout {title="Solution" tone="green" collapse="closed"}

1. By definition, the partition function is

$$
Z_{n} = \int_{\mathcal{W}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw.
$$

Since $\mathcal{W} = \mathcal{U} \sqcup \mathcal{V}$ is a disjoint union, the integral splits additively:

$$
Z_{n} = \int_{\mathcal{U}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw + \int_{\mathcal{V}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw = Z_{n}(\mathcal{U}) + Z_{n}(\mathcal{V}).
$$

Recalling that $F_{n} = -\log Z_{n}$ and similarly for the local free energies,

$$
Z_{n} = e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})},
$$

and taking the negative logarithm gives

$$
F_{n} = -\log Z_{n} = -\log(e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})}).
$$
2. The curves $F_{n}$ and $\min(F_{n}(\mathcal{U}), F_{n}(\mathcal{V}))$ are nearly identical, both track whichever local free energy is smaller. However, $F_{n}$ is smooth whereas $\min(F_{n}(\mathcal{U}), F_{n}(\mathcal{V}))$ has a kink at $n \approx 570$, where $F_{n}(\mathcal{U}) = F_{n}(\mathcal{V})$. For $n \lesssim 570$ the simpler region $\mathcal{V}$ (lower $\lambda$) dominates; for $n \gtrsim 570$ the lower loss region $\mathcal{U}$ (lower loss coefficient) dominates.
3. Differentiating the log-sum-exp from (a),

$$
\frac{d}{dn}F_{n} = \frac{\frac{d}{dn}F_{n}(\mathcal{U})\,e^{-F_n(\mathcal{U})}+ \frac{d}{dn}F_{n}(\mathcal{V})\,e^{-F_n(\mathcal{V})}}{e^{-F_n(\mathcal{U})}+ e^{-F_n(\mathcal{V})}},
$$

Plotting this reveals a steep step around $n \approx 570$, transitioning from $\frac{d}{dn}F_{n}(\mathcal{V}) \approx 0.5$ to $\frac{d}{dn}F_{n}(\mathcal{U}) \approx 0.3$. This rapid change in the derivative of $F_{n}$ is a smooth approximation of a discontinuity, justifying the term *phase transition*.
4. Write $F_{n}(\mathcal{U}) \approx L_{\mathcal{U}} \, n + \lambda_{\mathcal{U}} \log n$ and $F_{n}(\mathcal{V}) \approx L_{\mathcal{V}} \, n + \lambda_{\mathcal{V}} \log n$, and set $\Delta L = L_{\mathcal{U}} - L_{\mathcal{V}}$ and $\Delta\lambda = \lambda_{\mathcal{U}} - \lambda_{\mathcal{V}}$. The critical sample size $n^{*}$ where the phase transition occurs satisfies

$$
\Delta L \cdot n^{*} = -\Delta\lambda \cdot \log n^{*}, \qquad\text{i.e.}\qquad \frac{n^{*}}{\log n^{*}}= -\frac{\Delta\lambda}{\Delta L}
$$

Since $n^{*}/\log n^{*}$ is positive, a solution exists if and only if $-\Delta\lambda / \Delta L > 0$, i.e. $\Delta L$ and $\Delta\lambda$ have *opposite signs*. A phase transition occurs precisely when one region fits better while the other is simpler ($\Delta L$ and $\Delta\lambda$ have opposite signs). If both fit and complexity favour the same region, that region dominates for all $n$ and no phase transition occurs.

$n^{*}/\log n^{*}$ is monotonically increasing for $n > e$ so for such $n$, increasing $|\Delta \lambda|$ increases $n^{*}$ and increasing $\Delta L$ decreases $n^{*}$.

:::

\## 5. Further readings

We conclude by providing several pointers to additional literature and resources for those interested in investigating singular learning theory (SLT) in more detail.

\### 5.1 Other introductions to singular learning theory

For alternative introductions to SLT, see the following.

- [[#^bib-wei-2023|Wei et al. 2023]] "Deep Learning is Singular, and That's Good," a technical position paper surveying some implications of SLT for deep learning.
- [[#^bib-carroll2023|Carroll 2023]] "Distilling singular learning theory," a LessWrong sequence introducing Watanabe's free energy formula and discussing an example of a Bayesian phase transition in a small neural network.
- Lecture recordings from the *SLT & Alignment Summit, 2023*. In particular:

- See the "SLT Low Road" lectures ([[#^bib-lau-chen2023|Lau & Chen 2023]]) for an outline of the derivation of Watanabe's free energy formula.
- See the "SLT High Road" lectures ([[#^bib-murfet-carroll2023|Murfet & Carroll 2023]]) for a discussion of the free energy formula's implications including Bayesian phase transitions.
- [[#^bib-lau2025|Lau 2025]], Chapter 2, "Singular Learning Theory Background", a self-contained technical introduction to the main results of SLT with illustrative examples.

See [[#^bib-furman2024|Furman 2024]] for a list of mathematical exercises. There is some overlap with exercises included in this tutorial, but there are also several additional exercises.

For a more in-depth introduction to the theoretical foundations of SLT, see Watanabe's two research monographs.

- [[#^bib-watanabe2009|Watanabe 2009]] "Algebraic Geometry and Statistical Learning Theory," colloquially known as "the grey book." Derives the free energy formula in the realisable case along with other results concerning generalisation properties of Bayesian inference and maximum a posteriori inference.
- [[#^bib-watanabe2018|Watanabe 2018]] "Mathematical Theory of Bayesian Statistics," colloquially known as "the green book." An alternative presentation of the free energy formula generalised to the non-realisable case, among other results. Compared to the grey book, the green book has an updated presentation of the main results, but does not contain all of the details of the proofs of the main results from the grey book.

While the theoretical foundation of SLT is described across many research papers by Watanabe and others, the main results are collected in self-contained form in these monographs. Watanabe offers a set of lecture slides ([[#^bib-watanabe2023|Watanabe 2023]]) which may serve as a useful guide to the "big picture" while working through the details in the books. Other key papers include [[#^bib-watanabe2007|Watanabe 2007]]; [[#^bib-watanabe2013|Watanabe 2013]]. See [[#^bib-watanabe2024survey|Watanabe 2024]] for a more detailed survey.

\### 5.2 Recent work on singular deep learning

Over the last few years, a community of researchers have pursued the application of SLT to advancing the science and safety of deep learning. Some of the ideas behind this research are discussed by [[#^bib-hoogland-2023|Hoogland et al. 2023]]; [[#^bib-skalse-2023|Skalse 2023]]; [[#^bib-pepinlehalleur-2025|Pepin Lehalleur et al. 2025]]; [[#^bib-furman2026|Furman 2026]]. We briefly survey some key topics in this emerging literature.

**Characterising and estimating degeneracy in practice.**  We have seen examples of parameter–function map degeneracy in simple neural networks. Symmetries of neural network parameter–function maps have long been studied, however often the emphasis has been on discrete or globally continuous symmetries rather than additional symmetries localised to subsets of parameter space (see [[#^bib-farrugiaroberts2022|Farrugia-Roberts 2022]], § 2.3, for a survey). For two-layer hyperbolic tangent networks, [[#^bib-farrugiaroberts2024|Farrugia-Roberts 2024]] characterises the regions of parameter space which display additional degeneracy, and [[#^bib-farrugiaroberts2023|Farrugia-Roberts 2023]] characterises degenerate directions in the parameter–function map.

As discussed, analytically calculating the (local) learning coefficient for deep neural networks is challenging. However, precise formulas have been derived for multi-layer deep linear networks ([[#^bib-aoyagi-watanabe2005|Aoyagi & Watanabe 2005]]; [[#^bib-aoyagi2024|Aoyagi 2024]]), two-layer hyperbolic tangent networks ([[#^bib-aoyagi2009|Aoyagi 2009]]), and certain other architectures. These results assume data is generated from a known "teacher" model.

In practice, we lack knowledge of the true data generating process, and we use more complex architectures. Much work has therefore built on the foundational methods of estimating the local learning coefficient with scalable Markov chain Monte Carlo methods ([[#^bib-lau-2025|Lau et al. 2025]]; [[#^bib-hitchcock-hoogland2025|Hitchcock & Hoogland 2025]]). For a practical introduction to learning coefficient estimation, see [[#^bib-furman2023|Furman 2023]]. [[#^bib-chen-murfet2025|Chen & Murfet 2025]] characterises the sensitivity of local learning coefficient estimation to patterns in sequence models.

**Bayesian phase transitions and stagewise development.**  As we have discussed, Watanabe's free energy formula suggests Bayesian deep learning should undergo Bayesian phase transitions under certain conditions. [[#^bib-carroll2021|Carroll 2021]] studied Bayesian phase transitions in small ReLU networks, and [[#^bib-chen-2023|Chen et al. 2023]] studied Bayesian phase transitions in a small feature autoencoder (the "toy model of superposition" from [[#^bib-elhage-2022|Elhage et al. 2022]]).

In practice, we use stochastic gradient-based optimisation, rather than Bayesian learning, to train neural networks. However, the Bayesian case serves as a model system from which we can derive empirically testable predictions. [[#^bib-chen-2023|Chen et al. 2023]] formulate the *Bayesian antecedent hypothesis*, the empirical conjecture that observed phase transitions in trained neural networks correspond to Bayesian phase transitions modelled by Watanabe's free energy formula. [[#^bib-chen-2023|Chen et al. 2023]] study such *dynamical phase transitions* in their toy autoencoder and observe a temporal correspondence between phase changes and estimated LLC increases consistent with the free energy formula.

[[#^bib-wang-2024|Wang et al. 2024]]; [[#^bib-hoogland-2025|Hoogland et al. 2025]] scale this methodology to transformers trained on natural language, finding similar *stagewise development* phenomena with changes in behaviour and internal structure accompanied by LLC changes. [[#^bib-panickssery-vaintrob2023|Panickssery & Vaintrob 2023]]; [[#^bib-hoogland-2025|Hoogland et al. 2025]]; [[#^bib-carroll-2025|Carroll et al. 2025]]; [[#^bib-urdshals-urdshals2025|Urdshals & Urdshals 2025]] also study developmental stages in transformers trained on synthetic data. [[#^bib-elliott-2026|Elliott et al. 2026]] extends this study to a case of goal misgeneralisation in deep reinforcement learning.

**Degeneracy, interpretability, and patterning.**  The LLC provides a single number representing the effective dimensionality of a model. We can derive from the same principles—asymptotic properties of the posterior that reflect degeneracies in the model—more fine-grained tools for probing the internal computational structures of neural networks and how they depend on data.

- *Weight- and data-refined LLCs:* [[#^bib-wang-2025differentiation|Wang et al. 2025]] compute LLCs of individual transformer modules (e.g., different attention heads) or with respect to different subsets of a data set (e.g., natural language versus code). Observing these refined quantities over training reveals modules developing different structures specialising to different kinds of data.
- *Susceptibilities:* Drawing inspiration from electromagnetic susceptibilities in physics [[#^bib-baker-2025|Baker et al. 2025]]; [[#^bib-wang-2025embryology|Wang et al. 2025]]; [[#^bib-gordon-2026|Gordon et al. 2026]] develop and apply a methodology for computing loss susceptibilities so as to reveal more fine-grained information about how model internals relate to data.
- *Bayesian influence functions:* Similarly, drawing inspiration from training data attribution in statistics, [[#^bib-kreer-2025|Kreer et al. 2025]]; [[#^bib-lee-2025|Lee et al. 2025]]; [[#^bib-adam-2025|Adam et al. 2025]] develop a Bayesian generalisation of classical influence functions that allows the influence functions to be sensitive to higher-order degeneracy in the model.

Weight- and data-refined LLCs are themselves LLCs with a different model or data set, and so the same scalable Markov chain Monte Carlo methods can be used to estimate them as for LLCs. Moreover, like the LLC, susceptibilities and Bayesian influence functions can be approximated as expectations over a localised posterior distribution, and so similar estimation methods can be used for these quantities too.

[[#^bib-wang-murfet2026|Wang & Murfet 2026]] develop a methodology, *patterning*, for making targeted changes to the training distribution so as to elicit certain changes in the development of neural network internal structure or generalisation behaviour.

**Foundations of singular deep learning.**

There has been some work on developing the foundational theory of SLT and deep learning.

For example, [[#^bib-elliott-2026|Elliott et al. 2026]] generalise Watanabe's free energy formula from Bayesian inference to a generalised non-stationary energy-based inference setting, so as to account for stagewise development in deep reinforcement learning.

Beyond the setting of Bayesian inference, the general role degeneracy plays in the learning dynamics of stochastic gradient-based optimisation remains to be characterised.

Finally, there has been some attempt to theoretically investigate the links between degeneracy in deep learning and computational structure in models.

[[#^bib-clift-2021|Clift et al. 2021]]; [[#^bib-waring2021|Waring 2021]]; [[#^bib-xu2021|Xu 2021]]; [[#^bib-murfet2024|Murfet 2024]]; [[#^bib-murfet-troiani2025|Murfet & Troiani 2025]] study degeneracies in a statistical model based on a parameterisation of the space of Turing machine programs, exploring links between degeneracy and computational structure.

[[#^bib-lau2025|Lau 2025]], Chapter 5 and [[#^bib-urdshals-2025|Urdshals et al. 2025]] develop a theory of minimum description length in degenerate statistical models.

\## References


Maxwell Adam, Zach Furman, and Jesse Hoogland (2025). [*The Loss Kernel: A Geometric Probe for Deep Learning Interpretability*](https://arxiv.org/abs/2509.26537). arXiv:2509.26537.


^bib-adam-2025


Miki Aoyagi and Sumio Watanabe (2005). *Stochastic complexities of reduced rank regression in Bayesian estimation*. Neural Networks.


^bib-aoyagi-watanabe2005


Miki Aoyagi (2009). *Log canonical threshold of Vandermonde matrix type singularities and generalization error of a three layered neural network in Bayesian estimation*. International Journal of Pure and Applied Mathematics.


^bib-aoyagi2009


Miki Aoyagi (2024). *Consideration on the learning efficiency of multiple-layered neural networks with linear units*. Neural Networks.


^bib-aoyagi2024


Garrett Baker, George Wang, Jesse Hoogland, and Daniel Murfet (2025). [*Structural Inference: Interpreting Small Language Models with Susceptibilities*](https://arxiv.org/abs/2504.18274). arXiv:2504.18274.


^bib-baker-2025


Liam Carroll (2021). [*Phase Transitions in Neural Networks*](https://therisingsea.org/notes/MSc-Carroll.pdf). School of Mathematics and Statistics, the University of Melbourne.


^bib-carroll2021


Liam Carroll (2023). [*Distilling Singular Learning Theory*](https://www.lesswrong.com/s/czrXjvCLsqGepybHC).


^bib-carroll2023


Liam Carroll, Jesse Hoogland, Matthew Farrugia-Roberts, and Daniel Murfet (2025). [*Dynamics of Transient Structure in In-Context Linear Regression Transformers*](https://arxiv.org/abs/2501.17745). arXiv:2501.17745.


^bib-carroll-2025


Zhongtian Chen and Daniel Murfet (2025). [*Modes of Sequence Models and Learning Coefficients*](https://arxiv.org/abs/2504.18048). arXiv:2504.18048.


^bib-chen-murfet2025


Zhongtian Chen, Edmund Lau, Jake Mendel, Susan Wei, and Daniel Murfet (2023). [*Dynamical versus Bayesian Phase Transitions in a Toy Model of Superposition*](https://arxiv.org/abs/2310.06301). arXiv:2310.06301.


^bib-chen-2023


James Clift, Daniel Murfet, and James Wallbridge (2021). [*Geometry of Program Synthesis*](https://arxiv.org/abs/2103.16080). arXiv:2103.16080.


^bib-clift-2021


Nelson Elhage, Tristan Hume, Catherine Olsson, Nicholas Schiefer, Tom Henighan, Shauna Kravec, Zac Hatfield-Dodds, Robert Lasenby, Dawn Drain, Carol Chen, Roger Grosse, Sam McCandlish, Jared Kaplan, Dario Amodei, Martin Wattenberg, and Christopher Olah (2022). *Toy Models of Superposition*. Transformer Circuits Thread.


^bib-elhage-2022


Chris Elliott, Einar Urdshals, David Quarel, Matthew Farrugia-Roberts, and Daniel Murfet (2026). [*Stagewise Reinforcement Learning and the Geometry of the Regret Landscape*](https://arxiv.org/abs/2601.07524). arXiv:2601.07524.


^bib-elliott-2026


Matthew Farrugia-Roberts (2022). [*Structural Degeneracy in Neural Networks*](https://far.in.net/mthesis). School of Computing and Information Systems, the University of Melbourne.


^bib-farrugiaroberts2022


Matthew Farrugia-Roberts (2023). [*Functional Equivalence and Path Connectivity of Reducible Hyperbolic Tangent Networks*](https://proceedings.neurips.cc/paper_files/paper/2023/hash/fb64a43508e0cfe53ee6179ff31ea900-Abstract-Conference.html). Advances in Neural Information Processing Systems 36.


^bib-farrugiaroberts2023


Matthew Farrugia-Roberts (2024). [*Losslessly Compressible Neural Network Parameters*](https://openreview.net/forum?id=VhhsbII0Lk). Workshop on Machine Learning and Compression.


^bib-farrugiaroberts2024


Zach Furman (2023). [*Introduction to RLCT estimation*](https://github.com/zfurman56/intro-lc-estimation/).


^bib-furman2023


Zach Furman (2024). [*Singular learning theory: Exercises*](https://www.lesswrong.com/posts/3HYqTAi4kD35G3BzQ/).


^bib-furman2024


Zach Furman (2026). *Deep learning as program synthesis*.


^bib-furman2026


Andrew Gordon, Garrett Baker, George Wang, William Snell, Stan van Wingerden, and Daniel Murfet (2026). [*Towards Spectroscopy: Susceptibility Clusters in Language Models*](https://arxiv.org/abs/2601.12703). arXiv:2601.12703.


^bib-gordon-2026


Rohan Hitchcock and Jesse Hoogland (2025). [*From Global to Local: A Scalable Benchmark for Local Posterior Sampling*](https://arxiv.org/abs/2507.21449). arXiv:2507.21449.


^bib-hitchcock-hoogland2025


Jesse Hoogland, Alexander Gietelink Oldenziel, Daniel Murfet, and Stan van Wingerden (2023). [*Towards Developmental Interpretability*](https://www.alignmentforum.org/posts/TjaeCWvLZtEDAS5Ex/).


^bib-hoogland-2023


Jesse Hoogland, George Wang, Matthew Farrugia-Roberts, Liam Carroll, Susan Wei, and Daniel Murfet (2025). *Loss Landscape Degeneracy and Stagewise Development in Transformers*. Transactions on Machine Learning Research.


^bib-hoogland-2025


Philipp Alexander Kreer, Wilson Wu, Maxwell Adam, Zach Furman, and Jesse Hoogland (2025). [*Bayesian Influence Functions for Hessian-Free Data Attribution*](https://arxiv.org/abs/2509.26544). arXiv:2509.26544.


^bib-kreer-2025


Edmund Lau and Zhongtian Chen (2023). [*Singular Learning Theory: The Low Road*](https://www.youtube.com/playlist?list=PL4vaU_gO_6LIf5CHU3Z3CT39fha55pe16).


^bib-lau-chen2023


Edmund Lau (2025). *A Singular Perspective on Machine Learning*. School of Mathematics and Statistics, the University of Melbourne.


^bib-lau2025


Edmund Lau, Zach Furman, George Wang, Daniel Murfet, and Susan Wei (2025). [*The Local Learning Coefficient: A Singularity-Aware Complexity Measure*](https://openreview.net/forum?id=1av51ZlsuL). The 28th International Conference on Artificial Intelligence and Statistics.


^bib-lau-2025


Jin Hwa Lee, Matthew Smith, Maxwell Adam, and Jesse Hoogland (2025). [*Influence Dynamics and Stagewise Data Attribution*](https://arxiv.org/abs/2510.12071). arXiv:2510.12071.


^bib-lee-2025


Daniel Murfet and Liam Carroll (2023). [*Singular Learning Theory: The High Road*](https://www.youtube.com/playlist?list=PL4vaU_gO_6LJ4isj5DESGg4OwfVEk98Y-).


^bib-murfet-carroll2023


Daniel Murfet and Will Troiani (2025). [*Programs as Singularities*](https://arxiv.org/abs/2504.08075). arXiv:2504.08075.


^bib-murfet-troiani2025


Daniel Murfet (2024). [*Simple versus short: Higher-order degeneracy and error-correction*](https://www.alignmentforum.org/posts/nWRj6Ey8e5siAEXbK/).


^bib-murfet2024


Nina Panickssery and Dmitry Vaintrob (2023). [*Investigating the learning coefficient of modular addition*](https://www.alignmentforum.org/posts/4v3hMuKfsGatLXPgt).


^bib-panickssery-vaintrob2023


Simon Pepin Lehalleur, Jesse Hoogland, Matthew Farrugia-Roberts, Susan Wei, Alexander Gietelink Oldenziel, George Wang, Liam Carroll, and Daniel Murfet (2025). [*You Are What You Eat--AI Alignment Requires Understanding How Data Shapes Structure and Generalisation*](https://arxiv.org/abs/2502.05475). arXiv:2502.05475.


^bib-pepinlehalleur-2025


Joar Skalse (2023). [*My criticism of singular learning theory*](https://www.alignmentforum.org/posts/ALJYj4PpkqyseL7kZ/).


^bib-skalse-2023


Einar Urdshals and Jasmina Urdshals (2025). [*Structure Development in List-Sorting Transformers*](https://arxiv.org/abs/2501.18666). arXiv:2501.18666.


^bib-urdshals-urdshals2025


Einar Urdshals, Edmund Lau, Jesse Hoogland, Stan van Wingerden, and Daniel Murfet (2025). [*Compressibility Measures Complexity: Minimum Description Length Meets Singular Learning Theory*](https://arxiv.org/abs/2510.12077). arXiv:2510.12077.


^bib-urdshals-2025


George Wang and Daniel Murfet (2026). [*Patterning: The Dual of Interpretability*](https://arxiv.org/abs/2601.13548). arXiv:2601.13548.


^bib-wang-murfet2026


George Wang, Matthew Farrugia-Roberts, Jesse Hoogland, Liam Carroll, Susan Wei, and Daniel Murfet (2024). [*Loss landscape geometry reveals stagewise development of transformers*](https://openreview.net/forum?id=2JabyZjM5H). High-dimensional Learning Dynamics 2024: The Emergence of Structure and Reasoning.


^bib-wang-2024


George Wang, Jesse Hoogland, Stan van Wingerden, Zach Furman, and Daniel Murfet (2025). [*Differentiation and Specialization of Attention Heads via the Refined Local Learning Coefficient*](https://openreview.net/forum?id=SUc1UOWndp). International Conference on Learning Representations.


^bib-wang-2025differentiation


George Wang, Garrett Baker, Andrew Gordon, and Daniel Murfet (2025). [*Embryology of a Language Model*](https://arxiv.org/abs/2508.00331). arXiv:2508.00331.


^bib-wang-2025embryology


Thomas Waring (2021). [*Geometric Perspectives on Program Synthesis and Semantics*](https://therisingsea.org/notes/MSc-Waring.pdf). School of Mathematics and Statistics, the University of Melbourne.


^bib-waring2021


Sumio Watanabe (2007). *Almost all learning machines are singular*. IEEE Symposium on Foundations of Computational Intelligence.


^bib-watanabe2007


Sumio Watanabe (2009). *Algebraic Geometry and Statistical Learning Theory*. Cambridge University Press.


^bib-watanabe2009


Sumio Watanabe (2013). *A widely applicable Bayesian information criterion*. The Journal of Machine Learning Research.


^bib-watanabe2013


Sumio Watanabe (2018). *Mathematical Theory of Bayesian Statistics*. Chapman and Hall/CRC.


^bib-watanabe2018


Sumio Watanabe (2023). *Singular Learning Theory, parts (1) and (2)*.


^bib-watanabe2023


Sumio Watanabe (2024). *Recent Advances in Algebraic Geometry and Bayesian statistics*. Information Geometry.


^bib-watanabe2024survey


Susan Wei, Daniel Murfet, Mingming Gong, Hui Li, Jesse Gell-Redman, and Thomas Quella (2023). *Deep Learning Is Singular, and That's Good*. IEEE Transactions on Neural Networks and Learning Systems.


^bib-wei-2023


Adrian K. Xu (2021). [*Smooth relaxation preserving Turing machines*](https://arxiv.org/abs/2106.00956). arXiv:2106.00956.


^bib-xu2021

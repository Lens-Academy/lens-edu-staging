---
id: '6398339b-6e70-4456-a64e-c577ce2ccdde'
title: "B.3.2 Neural networks and loss functions"
tldr: "Defines neural networks as parameter-function maps with examples (linear neuron, deep linear network, MLP), then loss functions, population and empirical loss."
summary_for_tutor: "This is Section 1.1 and 1.2 of worksheet B.3 (singular learning theory). It defines the parameter-function map Phi from parameter space W to hypothesis class F, Examples 1.1 to 1.4 (linear neuron, multi-linear network, two-layer deep linear network f_{A,B}(x)=BAx, MLP f_{A,B}(x)=B sigma(Ax)), per-example loss, squared error, cross entropy, population loss L(w), empirical loss L_n(w) and SGD. It contains Exercises 1.1 (biased neurons) and 1.2 (empirical versus population loss) with collapsed solutions. Keep the notation Phi, f_w, W, L, L_n. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## 1. Preliminaries

In this section, we introduce basic terminology and notation for supervised deep learning and supervised Bayesian deep learning, along with some example neural network architectures and statistical models that we will repeatedly study throughout the tutorial.

\### 1.1 Neural networks and parameter–function maps

Let $${\mathcal{X}}$$ denote a space of network inputs (e.g., a space of images or token sequences encoded as vectors), and let $${\mathcal{Y}}$$ denote a space of outputs (e.g., a space of numerical scores, class distributions, or next-token distributions).

Informally, a neural network architecture is a specification for how various **parameters** (e.g., neuron connection strengths / weights or neuron activation thresholds / biases) combine with input signals and each other to describe a function from $${\mathcal{X}}$$ to $${\mathcal{Y}}$$.

Formally, a neural network architecture essentially comprises a **parameter–function map** $$\Phi : {\mathcal{W}} \to {\mathcal{F}}$$, where $${\mathcal{W}} \subseteq {\mathbb{R}}^{d}$$ is a $$d$$-dimensional **parameter space** and $${\mathcal{F}} \subseteq {\mathcal{Y}}^{{\mathcal{X}}}$$ is some **hypothesis class** of functions from $${\mathcal{X}}$$ to $${\mathcal{Y}}$$.

It is sometimes convenient to refer to the function $$\Phi(w) : {\mathcal{X}} \to {\mathcal{Y}}$$ as $$f_{w} : {\mathcal{X}} \to {\mathcal{Y}}$$.

Throughout the rest of this tutorial, we will study many different neural network architectures (parameter–function maps). The rest of this section explores some generally useful examples and some terminological points. To begin with, we have the following remark.

:::callout {title="Note" tone="blue"}

**Remark (Parameters).** Note that the term "parameter" has two senses:

1. A "parameter" is an individual dimension of parameter space (e.g., "initialise this parameter to the value $$0.0$$," or "this neural network has billions of parameters"). A loose synonym in this case is "weight."
2. A "parameter" is also a particular point in the parameter space (e.g., "this parameter is a local minimum of the loss function," or "the zero locus of this loss function contains a continuum of parameters"). A loose synonym in this case is "weight vector."

Both senses are in common usage in the literature as in this tutorial.

:::

The simplest neural network architecture models a single "neuron" with $$d$$ inputs $$x_{1}, \ldots x_{d}$$. Each input $$x_{i}$$ is multiplied by an incoming weight $$w_{i}$$ to produce the neuron's output. We formalise this case in Example 1.1.

:::callout {title="Tip" tone="green"}

**Example 1.1 (A linear neuron).** Let $${\mathcal{X}} = {\mathbb{R}}^{d}$$ for some positive integer $$d$$ and let $${\mathcal{Y}} = {\mathbb{R}}$$. Define a parameter space $${\mathcal{W}} = {\mathbb{R}}^{d}$$. Define a parameter–function map that maps a column vector $$w \in {\mathcal{W}}$$ to the function $$f_{w} : {\mathbb{R}}^{d} \to {\mathbb{R}}$$ such that for $$x \in {\mathbb{R}}^{d}$$,

$$
f_{w}(x) = w^{\top} x = \sum_{i=1}^{d} w_{i} x_{i}.
$$

:::

Let us generalise this basic neural network in three ways: to add multiple outputs, "depth," and non-linearity. First, we can generalise from a scalar output to a vector output as follows.

:::callout {title="Tip" tone="green"}

**Example 1.2 (Multi-linear neural network).** Let $${\mathcal{X}} = {\mathcal{Y}} = {\mathbb{R}}^{m}$$ for some positive integer $$m$$. Define a parameter space $${\mathcal{W}} = {\mathbb{R}}^{m^2}$$. Let each parameter $$w \in {\mathcal{W}}$$ encode an $$m \times m$$ matrix $$W \in {\mathbb{R}}^{m \times m}$$. The parameter–function map transforms each parameter $$w \in {\mathcal{W}}$$ to a function $$f_{w} : {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$$ such that for $$x \in {\mathbb{R}}^{m}$$,

$$
f_{w}(x) = W x.
$$

:::

If we take each row of $$W$$ to encode the weight vector of a linear neuron (Example 1.1), we see that we have produced $$m$$ outputs by stacking $$m$$ independent linear neurons together. Such a group of neurons is called a **layer**.

:::callout {title="Note" tone="blue"}

**Remark (Encodings).** In Example 1.2, the parameter space is formally $${\mathcal{W}} = {\mathbb{R}}^{m^2}$$, but we find it convenient to identify each parameter vector $$w \in {\mathbb{R}}^{m^2}$$ with the $$m \times m$$ matrix $$W$$ it encodes. We would thus write $$f_{W}$$ in place of $$f_{w}$$. More generally, whenever the parameters of an architecture naturally decompose into named matrices or vectors, we index the parameter–function map by these structured objects directly rather than by the underlying vector $$w$$. The remaining examples in this section demonstrate this convention, and we continue to use it throughout this tutorial.

:::

Next, let's add *depth* to our neural network by composing two layers together.

:::callout {title="Tip" tone="green"}

**Example 1.3 (Deep linear network; DLN).** Let $${\mathcal{X}} = {\mathcal{Y}} = {\mathbb{R}}^{m}$$ for some positive integer $$m$$. Let $$h$$ be a positive integer and define the parameter space $${\mathcal{W}} = {\mathbb{R}}^{2mh}$$, with each parameter encoding a pair of matrices $$A \in {\mathbb{R}}^{h \times m}$$ and $$B \in {\mathbb{R}}^{m \times h}$$. The parameter–function map sends $$(A, B)$$ to $$f_{A,B}: {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$$ such that for $$x \in {\mathbb{R}}^{m}$$,

$$
f_{A,B}(x) = B A x.
$$

:::

The above architecture is called a two-layer **deep linear network (DLN)**. The architecture can be interpreted as composing two multi-linear neural networks. The vector of outputs of the neurons of the first network becomes the vector of inputs to the second network. The intermediate output vectors are called **activations**.

Note that if $$h \geq m$$, the two-layer DLN architecture indexes the same hypothesis class as in Example 1.2, that of linear transforms on $${\mathbb{R}}^{m}$$. If $$h < m$$, the hypothesis class includes only transforms with rank up to $$h$$.

Finally, we'll add *non-linearity* between pairs of layers. To do so, we introduce a non-linear scalar function $$\sigma : {\mathbb{R}} \to {\mathbb{R}}$$, called an *activation function*, to transform the output of each intermediate neuron. Common examples of activation functions, which we will study in this tutorial, include the following:

1. The **hyperbolic tangent** function $$\displaystyle \tanh(z) = \frac{e^{z}-e^{-z}}{e^{z} + e^{-z}}$$.
2. The **rectified linear unit (ReLU)** function $${\mathrm{relu}}(z) = \max(z, 0)$$.

This results in the following non-linear neural network architecture.

:::callout {title="Tip" tone="green"}

**Example 1.4 (Multi-layer perceptron; MLP).** Define input, output, and parameter spaces as in Example 1.3. Let $$\sigma : {\mathbb{R}} \to {\mathbb{R}}$$ be an activation function. The parameter–function map sends $$(A, B)$$ to the function $$f_{A,B}: {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$$ such that for $$x \in {\mathbb{R}}^{m}$$,

$$
f_{A,B}(x) = B \cdot \sigma( A x ),
$$

where we lift the activation function to operate element-wise over column vectors $$A x \in {\mathbb{R}}^{h}$$.

:::
This kind of architecture is called a **multi-layer perceptron (MLP).** Note that the two-layer DLN is recovered if we use the identity function as an activation function. However, if we use a non-linear activation function, we can index a much richer hypothesis class.

The expressivity of these architectures is limited, however, by the omission of a basic detail—the inclusion of a bias parameter for each neuron. We invite the reader to correct this omission as our first exercise, which serves as a chance to familiarise oneself with the concept of a parameter–function map.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.1 (Biased neurons).** A biased neuron is a neuron with an additional parameter that is added to the weighted sum of its inputs before it produces its output. Bias parameters allow each layer to represent an *affine* transform, rather than just a linear transform. For each of Examples 1.1, 1.2, 1.3 and 1.4, extend the example to use biased neurons. Precisely define the parameter space and the parameter–function map in each case.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

For each architecture, we add a bias vector to each layer's output before the next transformation (or activation function) is applied.

**(a)** **A linear neuron with bias** (Example 1.1). Let $${\mathcal{W}} = {\mathbb{R}}^{d+1}$$, encoding a weight vector $$w \in {\mathbb{R}}^{d}$$ and a scalar bias $$b \in {\mathbb{R}}$$. The parameter–function map sends $$(w, b)$$ to $$f_{w,b}: {\mathbb{R}}^{d} \to {\mathbb{R}}$$ defined by

$$
f_{w,b}(x) = w^{\top} x + b.
$$

**(b)** **Multi-linear neural network with bias** (Example 1.2). Let $${\mathcal{W}} = {\mathbb{R}}^{m^2 + m}$$, encoding a matrix $$W \in {\mathbb{R}}^{m \times m}$$ and a bias vector $$b \in {\mathbb{R}}^{m}$$. The parameter–function map sends $$(W, b)$$ to $$f_{W,b}: {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$$ defined by

$$
f_{W,b}(x) = Wx + b.
$$

**(c)** **Deep linear network with bias** (Example 1.3). Let $${\mathcal{W}} = {\mathbb{R}}^{2mh + h + m}$$, encoding matrices $$A \in {\mathbb{R}}^{h \times m}$$, $$B \in {\mathbb{R}}^{m \times h}$$ and bias vectors $$b_{A} \in {\mathbb{R}}^{h}$$, $$b_{B} \in {\mathbb{R}}^{m}$$. The parameter–function map sends $$(A, b_{A}, B, b_{B})$$ to $$f_{w} : {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$$ defined by

$$
f_{w}(x) = B(Ax + b_{A}) + b_{B}.
$$

**(d)** **Multi-layer perceptron with bias** (Example 1.4). The parameter space is $${\mathcal{W}} = {\mathbb{R}}^{2mh + h + m}$$ as above. The parameter–function map sends $$(A, b_{A}, B, b_{B})$$ to $$f_{w} : {\mathbb{R}}^{m} \to {\mathbb{R}}^{m}$$ defined by

$$
f_{w}(x) = B \cdot \sigma(Ax + b_{A}) + b_{B}.
$$

:::

Modern deep learning leverages more involved parameter–function maps. Neural network architectures are typically defined in a modular fashion, including linear (or affine) layers and non-linear layers like the above, along with more specialised layers (well-known examples including convolutional layers, residual layers, and attention layers).

\### 1.2 Supervised deep learning and loss functions

In a typical supervised deep learning setting, we are given a data set of pairs $$(x^{(1)}, y^{(1)}),$$ $$\ldots,$$ $$(x^{(n)}, y^{(n)}) \in {\mathcal{X}} \times {\mathcal{Y}}$$. These pairs exemplify inputs and their corresponding (possibly noisy) outputs from an unknown target function $$f : {\mathcal{X}} \to {\mathcal{Y}}$$ which we would like to approximate using a neural network. That is, we would like to find a parameter $$w \in {\mathcal{W}}$$ such that the corresponding function $$f_{w}$$ approximates the target function $$f$$.

Formally, given an example $$(x, y) \in {\mathcal{X}} \times {\mathcal{Y}}$$, define a **per-example loss** function $$L_{x,y}: {\mathcal{W}} \to {\mathbb{R}}$$ to measure the deviation of $$f_{w}(x)$$ from the output $$y$$. A typical loss function for vector outputs $${\mathcal{Y}} \subset {\mathbb{R}}^{m}$$ is to use the **squared error** loss

$$
L_{x,y}(w) = \|f_{w}(x) - y\|^{2}.
$$

If $${\mathcal{Y}} = \Delta^{m-1}$$ is a space of discrete distributions over $$m$$ objects, it is typical to use **cross entropy** loss

$$
L_{x,y}(w) = - \sum_{i=1}^{m} y(i) \log f_{w}(i \mid x).
$$

Given a per-example loss function and a **data distribution** $$q \in \Delta({\mathcal{X}}\times{\mathcal{Y}})$$ over the space of examples (representing our possibly-noisy target function), we formalise the objective of supervised learning as finding $$w \in {\mathcal{W}}$$ so as to minimise the **population loss** function $$L : {\mathcal{W}} \to {\mathbb{R}}$$ defined such that

$$
L(w) = {\mathbb{E}}_{(x,y) \sim q}[L_{x,y}(w)].
$$

The population loss aggregates differences on outputs for individual inputs into an overall measure of difference between $$f_{w}$$ and the target function.

In practice, we often can't evaluate the population loss over the entire input/output space. We instead optimise an estimator based on our data set of $$n$$ input–output pairs assumed to be sampled independently and identically from $$q$$. Define an **empirical loss** function $$L_{n} : {\mathcal{W}} \to {\mathbb{R}}$$ such that

$$
L_{n}(w) = \frac{1}{n}\sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w).
$$

If the per-example loss is squared error, the empirical loss is known as the **mean squared error** objective.

$$
L_{n}(w) = \frac{1}{n}\sum_{i=1}^{n} \left\| f_{w}(x^{(i)}) - y^{(i)}\right\|^{2}.
$$

:::callout {title="Exercise" tone="amber"}
**Exercise 1.2 (Empirical loss and population loss).** Fix $$w \in {\mathcal{W}}$$. Prove the following properties of the relationship between the empirical loss $$L_{n}(w)$$ and the population loss $$L(w)$$.

**(a)** For any $$n$$, the empirical loss is an unbiased estimator of the population loss. That is,

$$
{\mathbb{E}}_{(x^{(i)}, y^{(i)}) \sim q}[L_{n}(w)] - L(w) = 0.
$$

**(b)** As $$n \to \infty$$, the empirical loss converges almost surely to the population loss.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since the data pairs $$(x^{(i)}, y^{(i)})$$ are sampled independently and identically from $$q$$, each per-example loss $$L_{x^{(i)},y^{(i)}}(w)$$ is an identically distributed random variable with expectation

$$
{\mathbb{E}}_{(x,y)\sim q}[L_{x,y}(w)] = L(w).
$$

Therefore, by linearity of expectation,

$$
\begin{aligned}{\mathbb{E}}[L_{n}(w)]&= {\mathbb{E}}\left[\frac{1}{n}\sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w)\right] = \frac{1}{n}\sum_{i=1}^{n} {\mathbb{E}}[L_{x^{(i)},y^{(i)}}(w)] \\&= \frac{1}{n}\cdot n \cdot L(w) = L(w).\end{aligned}
$$

**(b)** The random variables $$L_{x^{(1)},y^{(1)}}(w), L_{x^{(2)},y^{(2)}}(w), \ldots$$ are independent and identically distributed with common mean $$L(w)$$. By the strong law of large numbers,

$$
L_{n}(w) = \frac{1}{n}\sum_{i=1}^{n} L_{x^{(i)},y^{(i)}}(w) \xrightarrow{n\to\infty}L(w)
$$

almost surely.

:::

Given a loss function, a **training algorithm** is a search algorithm that aims to find $$w \in {\mathcal{W}}$$ such that the loss is approximately minimised. Most modern deep learning algorithms are variants of **stochastic gradient descent (SGD)**, which implements an iterative gradient-based local search of the parameter space using empirical loss on subsamples of the data set.

Through many impressive feats of computer science and hardware/software engineering, we are able to run such training algorithms to find low-loss parameters within parameter spaces with billions of dimensions. The details are vitally important to the success of modern deep learning, but are beyond the scope of this tutorial. We only mention SGD in order to emphasise that *any local search method depends intimately on the properties of the parameter–function map.*

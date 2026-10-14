---
id: 'f7ad1f01-6228-42cc-af9a-e521c8fb6f33'
title: "B.6.5 Large width at initialization: Gaussian processes"
tldr: "Notation for MLPs, fan-in normalization of a wide network, and Gaussian processes: Wick's theorem, cumulants and the action."
summary_for_tutor: "Sections 3, 3.1-3.3 of Iliad worksheet B.6 Physics of Deep Learning. Covers the MLP notation (L, N_l, z^(l), phi), why the 1/sqrt(fan-in) prefactor keeps preactivations of order one, the equivalence with width-dependent variances, Gaussian processes with kernel K, the physics definition via a functional integral, Wick/Isserlis theorem, and cumulants as a measure of non-Gaussianity. Contains Exercise 3.1 (Wick's theorem) with a collapsed solution. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\## 3. Large width at initialization: the Gaussian process limit

The next few sections are all about different limits in neural networks, in which some parameter(s) become large. Such limits are where physical/statistical analyses really shine. Studying them teaches some basic lessons about how we should (and should not) initialize networks, and how to choose other hyperparameters. It also leads to analytically solvable models that display many properties we see in practice: lazy vs. rich learning, double descent, phase transitions, scaling laws for optimal learning. For further pedagogical references on much of this material, we recommend (Roberts et al. 2022; Spiliopoulos et al. 2025; Ringel et al. 2025) and the online lectures (Hanin 2026).

We'll begin in this section with a classic result (Neal 1996; Lee et al. 2018; Yang 2019; Hanin 2023) about increasing the width of a network at fixed depth and training-sample size.

Modern neural networks are more sophisticated than the simple MLP's discussed here, but they share many of the same features. Layer norms solve the problem of trainability at large depth, but the analysis of rich/lazy regimes, feature learning, and hyperparameter scaling is still relevant. See *e.g.* the discussion of $$\mu P$$ in Section 5.5.

\### 3.1 Notation

We'll use the following notation for neural networks and training data.

- $$\theta\in {\mathbb{R}}^{P}$$ trainable network parameters (weights, biases)
- $$(x^{\mu},y^{\mu})_{\mu=1}^{n}$$ training data samples, with $$x^{\mu}\in {\mathbb{R}}^{d}$$ and $$y^{\mu}\in {\mathbb{R}}$$ (unless otherwise stated)
- $$f_{\theta}:{\mathbb{R}}^{d}\to {\mathbb{R}}$$ network function

For MLP's in particular (also called FCN's = fully connected networks)

- $$\{z_{i}^{(\ell)}\}_{i=1}^{N_\ell}$$ pre-activations in layer $$\ell\in \{0,...,L+1\}$$
- $$L=$$ number of hidden layers (depth); $$N_{\ell} =$$ width of $$\ell$$'th layer; $$N_{0}=d$$ and $$N_{L+1}=1$$. We will often take constant hidden depth, $$N_{1}=...=N_{L}=N$$.
- $$\phi:{\mathbb{R}}\to {\mathbb{R}}$$ activation function (assumed the same in all layers except the first)
- network recursion $$z_{i}^{(\ell)}= \begin{cases}\frac{1}{\sqrt{N_{\ell-1}}}\sum_{j=1}^{N_{\ell-1}}w^{(\ell)}_{ij}\,\phi(z^{(\ell-1)}_{j})+ b^{(\ell)}_{i}&\ell\geq 2 \\[.2cm] \frac{1}{\sqrt{d}}\sum_{j=1}^{d}w^{(1)}_{ij}\,x_{j}+ b^{(1)}_{i}&\ell = 1\end{cases}$$
with $$z^{(0)}= x$$ and $$z^{(L+1)}= f$$; parameters are $$\theta = \{w^{(\ell)},b^{(\ell)}\}_{\ell=1}^{L+1}$$ . The explicit factors of $$1/\sqrt{N_{\ell-1}}$$ are a normalization convention, explained in Section 3.2: with them in place, all weights and biases can be taken of order one.

\### 3.2 Normalizing the network

Consider a fully connected network of depth $$L$$ with layer widths $$N_{\ell}$$ as in Section 3.1. Suppose we keep $$L$$ fixed but make the $$N_{\ell}$$ very large. Suppose also that the network is initialized randomly, with all weights and biases drawn independently from normal distributions of *order-one* variance,

$$
w_{ij}^{(\ell)}\sim {{\mathcal N}}(0,\sigma_{w})\,,\qquad b_{i}^{(\ell)}\sim {{\mathcal N}}(0,\sigma_{b})\,,
$$

with $$\sigma_{w},\sigma_{b}$$ fixed as the widths grow. (Here and throughout, $${{\mathcal N}}(0,\sigma)$$ denotes a Gaussian of *variance* $$\sigma$$. Letting the variances depend on the layer changes nothing below.) The question is how to normalize the sums in the network recursion so that preactivations stay of order one from layer to layer. From

$$
z_{i}^{(\ell)}= \frac{1}{\sqrt{N_{\ell-1}}}\, w_{i}^{(\ell)}\cdot \phi(z^{(\ell-1)}) + b_{i}^{(\ell)}
$$

(where we've written $$w_{i}=(w_{i,1},...,w_{i,N_{\ell-1}})$$ and $$z^{(\ell-1)}= (z^{(\ell-1)}_{1},...,z^{(\ell-1)}_{N_{\ell-1}})$$ as vectors) we get

$$
\begin{aligned}\text{Var}(z_{i}^{(\ell)})&= \frac{1}{N_{\ell-1}}\sum_{j=1}^{N_{\ell-1}}\text{Var}\big(w_{ij}^{(\ell)}\big)\, {\mathbb{E}}\Big[\phi\big(z_{j}^{(\ell-1)}\big)^{2}\Big] \;+\; \text{Var}\big(b_{i}^{(\ell)}\big) \notag \\&= \sigma_{w} \cdot \frac{1}{N_{\ell-1}}\sum_{j=1}^{N_{\ell-1}}\Big( \text{Var}\big(\phi(z_{j}^{(\ell-1)})\big)+{\mathbb{E}}\big[\phi(z_{j}^{(\ell-1)})\big]^{2}\Big) +\sigma_{b}\,.\end{aligned}
$$

Here we've conditioned on the previous layer, and used that for independent mean-zero $$X$$ and arbitrary $$Y$$, $$\text{Var}(XY) = \text{Var}(X)\,{\mathbb{E}}[Y^{2}]$$, along with additivity of variance for independent summands. The average in the second line involves only the activation function and the order-one preactivations of the previous layer, so it stays of order one as $$N_{\ell-1}\to\infty$$. (We'll sharpen this estimate in Section 3.7.) Thus

$$
\text{Var}(z_{i}^{(\ell)}) \approx \sigma_{w}\cdot O(1) + \sigma_{b} = O(1)\,.
$$

The prefactor $$1/\sqrt{N_{\ell-1}}$$, the square root of the number of inputs (the "fan-in") feeding each neuron, is exactly what keeps the preactivations of order one at large width. We call this the *fan-in normalization*; it goes back to LeCun and collaborators in the 90's (LeCun et al. 1998). In Section 4 it will also be called the *NTK normalization*, and in Section 5 we will meet the alternative *mean-field normalization*, in which the output layer carries $$1/N$$ instead of $$1/\sqrt{N}$$.

:::callout {title="Note" tone="blue"}

**Remark (other conventions).** Common practice, and the convention of much of the literature, is to put no explicit prefactors in the network and instead to initialize with width-dependent variances,

$$
\tilde w^{(\ell)}_{ij}:= \frac{w^{(\ell)}_{ij}}{\sqrt{N_{\ell-1}}}\;\sim\; {{\mathcal N}}\Big(0,\frac{\sigma_{w}}{N_{\ell-1}}\Big)\,.
$$

At initialization the two conventions describe *exactly* the same distribution of network functions: (3.5) is a change of variables on parameter space, and the network function is the same function of $$x$$. Everything in this section, which concerns initialization only, is insensitive to the choice. During training, however, the two conventions are *not* equivalent: gradient descent is not invariant under rescaling coordinates on parameter space, as we will explain in Section 4.3. Keeping every parameter of order one, with the factors of $$N$$ displayed explicitly in the network function, makes the comparison between different scaling limits transparent, and it is the convention we use throughout these notes. When reading the literature, expect the factors of $$N$$ to sit in the variances instead, and translate with (3.5).

:::

\### 3.3 Gaussian processes

A *Gaussian process* $$f:{\mathbb{R}}^{m}\to {\mathbb{R}}$$ with mean function $$\mu$$ and covariance kernel $$K$$ is a random function such that on any $$p$$ inputs $$(x^{1},...,x^{p})\in ({\mathbb{R}}^{m})^{p}$$ the vector of function values is Gaussian

$$
\begin{pmatrix}f(x^{1}) \\ \vdots \\ f(x^{p})\end{pmatrix} \sim {{\mathcal N}} \left( \begin{pmatrix}\mu(x^{1}) \\ \vdots \\ \mu(x^{p})\end{pmatrix}, \begin{pmatrix}K(x^{1},x^{1})&\cdots&K(x^{1},x^{p}) \\ \vdots&\ddots&\vdots \\ K(x^{p},x^{1})&\cdots&K(x^{p},x^{p})\end{pmatrix} \right)\,.
$$

Here $$\mu:{\mathbb{R}}^{m}\to {\mathbb{R}}$$ and $$K:{\mathbb{R}}^{m}\times {\mathbb{R}}^{m}\to {\mathbb{R}}$$ are fixed, deterministic functions that control the mean and covariance of any tuple of values of $$f$$. The function $$K$$, often called the kernel of the process, is symmetric: $$K(x,x')=K(x',x)$$.

Let `$$dx$$' denote a measure on $${\mathbb{R}}^{m}$$ (it need not be the usual Lebesgue measure). If $$K$$, as integral kernel, has an inverse $$K^{-1}$$ satisfying

$$
\int dx' K^{-1}(x,x') K(x',x'') = \delta(x-x'')
$$

then there's also a "physics definition" of a Gaussian process. It's not entirely rigorous, as it invokes multi-dimensional functional integrals. Mathematically, it's best thought of as a heuristic tool, which comes with a package of axiomatic manipulations whose actual results can (and should) all be fully justified by other means. The manipulations are all quite intuitive, though, and familiar to quantum field theorists, so we mention this formalism here. The idea is that, just like a single Gaussian variable `$$z$$' has a probability measure

$$
P(z) = \frac{1}{Z}e^{-\frac{1}{2}K^{-1}(z-\mu)^2}\,,\qquad Z = \int dz\,e^{-\frac{1}{2}K^{-1}(z-\mu)^2}= \sqrt{2\pi K}\,,
$$

a Gaussian process $$f$$ has a (non-rigorous) measure

$$
\begin{aligned}P[f]&= \frac{1}{Z}e^{\textstyle-\frac{1}{2} \int dx\,dx'\, (f(x)-\mu(x)) K^{-1}(x,x')(f(x')-\mu(x'))}\,, \notag \\ Z&\; \text{`='}\int Df\, e^{\textstyle-\frac{1}{2} \int dx\,dx'\, (f(x)-\mu(x)) K^{-1}(x,x')(f(x')-\mu(x'))}\,.\end{aligned}
$$

If the kernel and the measure theory on the input space $${\mathbb{R}}^{m}$$ are nice enough to allow $$K$$ to be diagonalized, with a discrete basis of orthonormal eigenfunctions $$\{\phi_{k}(x)\}_{k=1}^{\infty}$$ and eigenvalues $$\lambda_{1}\geq \lambda_{2}\geq\ldots > 0$$ (so that $$K^{-1}$$ has eigenvalues $$1/\lambda_{k}$$), then $$P[f]$$ can be understood as an infinite-dimensional Gaussian. Writing $$f(x)-\mu(x) = \sum_{k=1}^{\infty} a_{k} \phi_{k}(x)$$,

$$
P[f] = \frac{1}{Z}e^{\textstyle -\frac{1}{2}\sum_{k=1}^\infty a_k^2/\lambda_k}\,,\qquad Z = \prod_{k=1}^{\infty} (2\pi \lambda_{k})^{1/2}\,.
$$

One virtue of the physics formalism is that it organizes expectation values of products of $$f(x)$$'s. Let $$\mu=0$$ for simplicity (to generalize to any $$\mu$$, just shift $$f\mapsto f-\mu$$ below). Let $$J:{\mathbb{R}}^{m}\to {\mathbb{R}}$$ be an arbitrary (nice...) function and define

$$
Z[J] = \int Df\, e^{\textstyle -\frac{1}{2}\int dx\,dx'\, f(x)K^{-1}(x,x')f(x') + \int dx\, J(x)f(x)}\,.
$$

The integral evaluates formally to

$$
Z[J] = Z[0] \cdot e^{\textstyle \frac{1}{2} \int dx\,dx'\, J(x) K(x,x') J(x')}\,.
$$

Then expectation values can be expressed via derivatives, which by (3.12) become

$$
\begin{aligned}{\mathbb{E}}\big[ f(x^{1})...f(x^{p})\big]&= \frac{1}{Z[0]}\frac{\delta}{\delta J(x^{1})}...\frac{\delta}{\delta J(x^{p})}Z[J]\bigg|_{J=0}\\&= \sum_{\text{pairs}\,\{i_1,i_2\}\cup...\cup\{i_{p-1},i_p\}=\{1,2,...,p\}}\prod_{j=1}^{p/2}K(x^{i_{2j-1}},x^{i_{2j}})\,. \end{aligned}
$$

The sum is over partitions of $$\{1,...,p\}$$ into pairs, and vanishes if $$p$$ is odd. Eqn. (3.14) is called Wick's Theorem in QFT, Isserlis's Theorem in probability (and it's correct, despite the non-rigorous derivation here).

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (Wick's theorem).** If you haven't seen this before, derive (3.12) by completing the square in (3.11), and then derive (3.14) by differentiating. Check the first two cases explicitly: $${\mathbb{E}}[f(x^{1})f(x^{2})] = K(x^{1},x^{2})$$, and $${\mathbb{E}}[f(x^{1})f(x^{2})f(x^{3})f(x^{4})] = K^{12}K^{34}+K^{13}K^{24}+K^{14}K^{23}$$ (with $$K^{ij}=K(x^{i},x^{j})$$). How many terms appear at $$p=6$$?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Complete the square: shifting $$f \to f + K J$$ (schematically, $$f(x) \to f(x) + \int dx' K(x,x')J(x')$$) decouples the source, leaving $$Z[J] = Z[0]\, e^{\frac{1}{2} \int J K J}$$. Each derivative $$\delta/\delta J(x^{i})$$ acting on the exponential either brings down a factor $$\int K(x^{i},\cdot)J$$ (which must later be hit by another derivative, else it dies at $$J=0$$) or closes a pair by hitting a previously produced factor, contributing $$K(x^{i},x^{j})$$. Every surviving term therefore corresponds to a perfect pairing of $$\{1,\dots,p\}$$. For $$p=2$$ this gives $$K(x^{1},x^{2})$$; for $$p=4$$, the three pairings $$K^{12}K^{34}+K^{13}K^{24}+K^{14}K^{23}$$; for $$p=6$$ there are $$5!! = 15$$ terms; in general $$(p-1)!!$$.

:::

Another virtue of the physics formalism is that it neatly connects *higher cumulants* to *deviations from Gaussianity*. In general, the $$p$$-th cumulant $$\kappa_{p}(X_{1},...,X_{p})$$ of random variables $$X_{1},...,X_{p}$$ is defined recursively via

$$
{\mathbb{E}}(X_{1}\cdots X_{p}) = \sum_{\text{partition $\Pi$ of $\{1,...,p\}$}}\;\prod_{\text{blocks $\{i_{1},...,i_{k}\}\subset \Pi$}}\kappa_{k}(X_{i_1},...,X_{i_k})
$$

For example, $$\kappa_{1}(X)={\mathbb{E}}(X)$$, $$\kappa_{2}(X_{1},X_{2})=\text{Cov}(X_{1},X_{2}) = {\mathbb{E}}(X_{1}X_{2})-{\mathbb{E}}(X_{1})E(X_{2})$$. In physics, the $$\kappa_{p}$$'s are called connected correlation functions; they measure the part of a joint expectation that's not captured by expectations of subsets of the variables involved. For a Gaussian process,

$$
\kappa_{2}(f(x^{1}),f(x^{2}))=K(x^{1},x^{2})\,;\qquad \kappa_{p}(f(x^{1}),...,f(x^{p})) = 0\quad\text{for all $p>2$}\,,
$$

as can easily be seen directly from (3.14), where joint expectations for $$p>2$$ all factor into products of pairs. Thus, nonvanishing higher $$\kappa_{p}$$'s are a measure of non-Gaussianity.

This appears in the functional-integral formalism as follows. Suppose that $$f:{\mathbb{R}}^{m}\to {\mathbb{R}}$$ is a random function that's governed by a functional probability distribution

$$
P[f] = \frac{1}{Z}\,e^{\textstyle-S[f]}\,,
$$

for some functional $$S:\{\text{functions }f\}\to {\mathbb{R}}$$. (In physics $$S$$ is called the action.) Then just as in (3.11), we can introduce the generating function

$$
\begin{aligned}Z[J]&:= \int Df\, e^{\textstyle-S[f]+\int dx\, J(x)f(x)}\notag \\ \Rightarrow\quad {\mathbb{E}}\big[f(x^{1})...f(x^{p})\big]&= \frac{1}{Z[0]}\frac{\delta}{\delta J(x^{1})}...\frac{\delta}{\delta J(x^{p})}Z[J]\bigg|_{J=0}\end{aligned}
$$

The cumulants appear naturally as derivatives of $$\log Z[J]$$, otherwise known as the (sourced) free energy:

$$
\kappa_{p}(f(x^{1}),...,f(x^{p})) = \frac{\delta}{\delta J(x^{1})}...\frac{\delta}{\delta J(x^{p})}\log Z[J] \bigg|_{J=0}\,,
$$

which in turn means (formally) that

$$
Z[J] = \exp\sum_{p=1}^{\infty} \frac{1}{p!}\int dx^{1}...dx^{p}\, \kappa_{p}(f(x^{1}),...,f(x^{p}))\,J(x^{1})...J(x^{p})\,,
$$

a generating function of cumulants. The original $$S[f]$$ is the inverse Legendre transform of $$\log Z[J]$$ (by definition of $$Z[J]$$). Expanded as a formal series in the cumulants (assuming they are small), and assuming $${\mathbb{E}}[f(x)]=0$$ for simplicity, it takes the form

$$
\begin{aligned}S[f] =&\; \frac{1}{2}\int dx^{1}\, dx^{2}\, \kappa_{2}^{-1}(x^{1},x^{2}) f(x^{1})f(x^{2}) \notag \\&- \int dx^{1} dx^{2} dx^{3}\, dy^{1} dy^{2} dy^{3}\; \kappa_{2}^{-1}(x^{1},y^{1})\,\kappa_{2}^{-1}(x^{2},y^{2}) \notag \\&\hspace{1in}\times\, \kappa_{2}^{-1}(x^{3},y^{3})\,\kappa_{3}(y^{1},y^{2},y^{3})\,f(x^{1})f(x^{2})f(x^{3}) \notag \\&- \int dx^{1} dx^{2} dx^{3} dx^{4}\, (\kappa_{2}^{-1})^{4}\big[ \kappa_{4} - \kappa_{3}\kappa_{2}^{-1}\kappa_{3}\;\;\text{terms}\big] \notag \\&\hspace{1in}\times\, f(x^{1})f(x^{2})f(x^{3})f(x^{4})\; - \ldots\end{aligned}
$$

Physicists might recognize this as a sum of Feynman diagrams, with cumulants giving the vertices. A key structure is that the $$p$$-th order term in the effective action contains only $$\kappa_{p}$$ and lower cumulants. In particular, $$f$$ is a Gaussian process if and only if $$S[f]$$ is quadratic; and small deviations from Gaussianity, measured by cumulants, provide the higher-order terms in $$S[f]$$.

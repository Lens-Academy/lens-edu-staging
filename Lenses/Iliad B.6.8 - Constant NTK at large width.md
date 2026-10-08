---
id: 'ab51085c-4c5a-4ada-908e-8258c78978d5'
title: "B.6.8 Constant NTK at large width"
tldr: "Features as singular vectors of the Jacobian and NTK eigenvectors, then the theorem that the NTK stays constant at large width, with a sketch of its proof."
summary_for_tutor: "Sections 4.2-4.3 of Iliad worksheet B.6 Physics of Deep Learning. Covers the Jacobian SVD, feature learning as change of the NTK, the Fisher information remark, the size of the NTK in the fan-in normalization, how to scale the learning rate, the small-Hessian argument, per-weight motion of order 1/sqrt(N), and linearization of the network as N goes to infinity. Keep Theta, J=USV^T, s_i^2, Delta^mu. No exercises in this lens."
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
\### 4.2 Features

The Jacobian matrix $$J^{\mu}{}_{i}=\partial f^{\mu}/\partial \theta^{i}$$ measures how function values on the training data depend on small variations of the network weights. Assuming there are more parameters than training data, its singular value decomposition looks like

$$
J = USV^{T}\,,\qquad S = \bigg[\text{diag}(s_{1},...,s_{n})\;\; \mathbf{0}_{n\times (P-n)}\bigg]\,.
$$

The right singular vectors (columns of $$V$$) define natural modes in parameter space, while the left singular vectors (columns of $$U$$) are the natural modes in function-value space — where "natural" means with respect to how network outputs depend on weights. The $$n$$ left singular vectors (together with their singular values $$s_{i}$$) can be thought of, abstractly, as the *features* that a network has learned. A common definition of feature *learning* is that these singular vectors+values change during training.

The analysis of features can equivalently be performed via the NTK. As a matrix, we've got

$$
\Theta = JJ^{T} = US^{2}U^{T}\,,
$$

with eigenvectors = the feature vectors, and eigenvalues = $$\{s_{i}^{2}\}$$ . Thus feature learning happens when the NTK changes during training.

:::callout {title="Note" tone="blue"}

**Remark.** A closely related "dual" object that appears in other parts of learning theory is the Fisher information metric on parameter space $${\mathbb{R}}^{P}$$. Its empirical version is

$$
\mathcal{F} := J^{T}J = f^{*}(\delta)\,,
$$

the pull-back (via the network function) of constant Euclidean metric on the space of function values on the training data. In coordinates, $$\mathcal{F}_{ij}=\frac{\partial f^{\mu}}{\partial \theta^{i}}\delta_{\mu\nu}\frac{\partial f^{\mu}}{\partial \theta^{j}}$$.

The Fisher metric has eigenvalues $$(s_{1}^{2},...,s_{n}^{2},\overbrace{0,...,0}^{P-n})$$, and is automatically degenerate when $$P>n$$ (more parameters than training data points). This is one of the starting points of singular learning theory.

:::

\### 4.3 Constant NTK at large width

Now we get to the main theoretical result and simplification of this section. Suppose we've got an MLP of fixed depth $$L$$, and fixed training data size $$n$$, and take the width of all hidden layers to infinity. We'll assume the hidden widths all scale in a similar way $$N_{L},N_{L-1},...,N_{1}\approx N\to \infty$$, and we initialize the network the standard way from Section 3.2. We want to show that for almost all samples of training data,

- The NTK $$\Theta^{\mu\nu}$$ remains constant throughout training, up to corrections that vanish as $$N\to\infty$$.
- The network itself linearizes: at any training time $$t$$, $$f_{\theta(t)}(x) =f_{\theta_0}(x) + (\theta(t)-\theta_{0})\cdot\nabla_{\theta} f_{\theta_0}(x)$$

A rigorous derivation is somewhat technical, and we refer the reader to (Du et al. 2019; Jacot et al. 2018), (Roberts et al. 2022, Ch. 11), (Spiliopoulos et al. 2025, Ch. 20) for complete arguments, explained from a variety of different perspectives. We'll just sketch the key ideas behind the result. See also (Hanin 2026, Lecture 3).

We'll simplify life by setting biases to zero, so the network becomes

$$
f_{\theta}(x) = z^{(L+1)}(x)\,,\quad z^{(\ell)}_{i} = \frac{1}{\sqrt{N_{\ell-1}}}\sum_{j} w_{ij}^{(\ell)}\phi(z_{j}^{(\ell-1)})\,,\quad w^{(\ell)}_{ij}\sim{{\mathcal N}}(0,\sigma_{w})\,,
$$

in the fan-in normalization of Section 3.2, with order-one weights.

*Size of the NTK.* The first task is to estimate how large the NTK is at large width, because that decides how the learning rate must scale. By the chain rule, the gradient with respect to the layer-$$\ell$$ weights is an outer product,

$$
\frac{\partial f}{\partial w^{(\ell)}_{ij}}= \frac{1}{\sqrt{N_{\ell-1}}}\;\beta^{(\ell)}_{i}\;\phi(z^{(\ell-1)}_{j})\,,\qquad \beta^{(\ell)}_{i} := \frac{\partial f}{\partial z^{(\ell)}_{i}}\,,
$$

where the backpropagated sensitivities $$\beta^{(\ell)}$$ obey $$\beta^{(L+1)}= 1$$ and

$$
\beta^{(\ell)}_{i} = \phi'(z^{(\ell)}_{i})\,\frac{1}{\sqrt{N_{\ell}}}\sum_{k} w^{(\ell+1)}_{ki}\,\beta^{(\ell+1)}_{k}\,.
$$

The NTK is a sum over layers,

$$
\begin{aligned}\Theta^{\mu\nu}&= \sum_{\ell=1}^{L+1}\sum_{i,j}\frac{\partial f^{\mu}}{\partial w^{(\ell)}_{ij}}\frac{\partial f^{\nu}}{\partial w^{(\ell)}_{ij}}\notag \\&= \sum_{\ell=1}^{L+1}\underbrace{\Big[\sum_i \beta^{(\ell)}_i(x^\mu)\,\beta^{(\ell)}_i(x^\nu)\Big]}_{B^{(\ell)}_{\mu\nu}}\; \underbrace{\Big[\frac{1}{N_{\ell-1}}\sum_j \phi(z^{(\ell-1)}_j(x^\mu))\,\phi(z^{(\ell-1)}_j(x^\nu))\Big]}_{\to\;\bar K^{(\ell)}_{\mu\nu}/\sigma_w}\,. \end{aligned}
$$

The second bracket is an average of $$N_{\ell-1}$$ terms. At initialization and large width, the law of large numbers replaces it by $$\bar K^{(\ell)}_{\mu\nu}/\sigma_{w}$$, the Gaussian-process kernel of (3.30) evaluated on the two inputs, which is of order one. (For $$\ell=1$$ the bracket is exactly $$x^{\mu}\cdot x^{\nu}/d$$, which is $$\bar K^{(1)}_{\mu\nu}/\sigma_{w}$$.) The first bracket is handled by the same recursion run backwards. Define

$$
\dot{\bar K}^{(\ell)}_{\mu\nu}= \dot{\bar K}^{(\ell)}(x^{\mu},x^{\nu}):= {\mathbb{E}}\big[ \phi'(z^{(\ell-1)}_{i}(x^{\mu}))\,\phi'(z^{(\ell-1)}_{i}(x^{\nu}))\big] \qquad \text{(for any fixed $i$)}\,,
$$

which is of order one for reasonable activation functions. Using the independence at initialization of the weights $$w^{(\ell+1)}$$ from everything below them, one finds $$B^{(\ell)}_{\mu\nu}\approx \sigma_{w}\,\dot{\bar K}^{(\ell+1)}_{\mu\nu}\,B^{(\ell+1)}_{\mu\nu}$$ with $$B^{(L+1)}_{\mu\nu}=1$$, and hence

$$
{\mathbb{E}}\big[\Theta^{\mu\nu}\big] \;\approx\; \sum_{\ell=1}^{L+1}\sigma_{w}^{L-\ell}\; \dot{\bar K}^{(L+1)}_{\mu\nu}\cdots \dot{\bar K}^{(\ell+1)}_{\mu\nu}\; \bar K^{(\ell)}_{\mu\nu}\,.
$$

This is a sum of $$L+1$$ terms, each of order one, with no factors of $$N$$ anywhere: *in the fan-in normalization the NTK is of order one at large width*, and every layer contributes to it at the same order. (Equation (4.23) is the standard recursion for the infinite-width NTK (Jacot et al. 2018).) By (4.10), an order-one learning rate $$\eta$$ then moves the function values $$f^{\mu}$$ by an order-one amount per unit time, which is what we want, and no rescaling of $$\eta$$ with width is needed in this convention. For the one-hidden-layer network $$f = \frac{1}{\sqrt{N}}\sum_{i} c_{i}\phi(a_{i}\cdot x)$$ one can check this by hand:

$$
\Theta^{\mu\nu}= \frac{1}{N}\sum_{i=1}^{N}\Big[\phi(a_{i}\cdot x^{\mu})\,\phi(a_{i}\cdot x^{\nu}) + c_{i}^{2}\,\phi'(a_{i}\cdot x^{\mu})\,\phi'(a_{i}\cdot x^{\nu})\;x^{\mu}\!\cdot x^{\nu}\Big] = O(1)\,,
$$

an average of $$N$$ order-one terms. (Here and below we absorb the first-layer factor $$1/\sqrt{d}$$ into the inputs $$x$$, since $$d$$ is fixed.)

:::callout {title="Note" tone="blue"}

**How to scale the learning rate.** The rule just used is general, and we will use it again in Section 5. What must stay of order one as $$N\to\infty$$ is the *motion of the network values*, $$\frac{d}{dt}f^{\mu} = -\eta\,\Theta^{\mu\nu}\,\partial{{\mathcal L}}^{(f)}/\partial f^{\nu}$$, since those are what fit the data. So: work out how the NTK scales with $$N$$, and choose $$\eta$$ so that $$\eta\,\Theta = O(1)$$. In the fan-in normalization $$\Theta = O(1)$$ and $$\eta = O(1)$$. In the mean-field normalization of Section 5, $$\Theta = O(1/N)$$ and $$\eta$$ must grow like $$N$$.

Other conventions for the parameters are changes of variables, and they can be compared through the same rule. Suppose one puts no prefactors in the network and initializes $$\tilde w^{(\ell)}= w^{(\ell)}/\sqrt{N_{\ell-1}}\sim{{\mathcal N}}(0,\sigma_{w}/N_{\ell-1})$$ as in (3.5). Gradient flow with respect to the Euclidean metric $$\sum(d\tilde w)^{2}$$ is *not* the same flow as gradient flow with respect to $$\sum(dw)^{2}$$. Under the change of variables, the inverse metric $$\delta^{ij}$$ of Section 4.1.1 picks up a factor $$N_{\ell-1}$$ in every layer-$$\ell$$ block, so that in the original coordinates the flow reads $$\dot w^{(\ell)}= -\eta\,N_{\ell-1}\,\partial{{\mathcal L}}/\partial w^{(\ell)}$$. The NTK computed in the $$\tilde w$$ coordinates is correspondingly larger, $$\tilde\Theta = \sum_{\ell} N_{\ell-1}\,\Theta_{(\ell)}$$ in terms of the layer contributions of (4.21), and an order-one motion of $$f$$ then requires $$\tilde\eta\sim 1/N$$. A rescaling of the parameters is thus equivalent to a layer-dependent rescaling of the learning rate, and two conventions define the same training dynamics only if their learning rates are matched layer by layer. With a *single* learning rate $$\tilde\eta\sim1/N$$ in the $$\tilde w$$ convention, for instance, the hidden layers move as in the fan-in normalization, but the first layer, whose fan-in $$d$$ does not grow with $$N$$, is effectively frozen. When comparing learning rates across papers, first translate the parametrizations into one another; for a systematic treatment, see (Yang & Hu 2021).

:::

**Caution**: the estimate (4.23) is at fixed depth $$L$$ and fixed data size $$n$$. The NTK grows like $$L$$ with depth, and the operator norm of the $$n\times n$$ matrix $$\Theta$$ grows with $$n$$, so for deep networks or large datasets the learning rate must shrink accordingly, and the constant-NTK statements below need $$n$$ and $$L$$ to stay small compared with $$N$$.

*The Hessian is small.* To see that the NTK is approximately constant during training, we consider its time derivative, which by Exercise 4.2 is bounded by the operator norm of the Hessian of the network function,

$$
\Big\|\frac{d}{dt}\Theta\Big\| \lesssim \eta\, \| \nabla_{\theta}^{2} f \| \cdot \|\Theta\|\cdot|\Delta|\,.
$$

The Hessian is a very large but very sparse matrix, and in the fan-in normalization its operator norm is small. We'll sketch how this works for one hidden layer ($$L=1$$) with one-dimensional output, following (Hanin 2026, Lecture 3). Writing

$$
f_{\theta}(x) = \frac{1}{\sqrt{N}}\sum_{i=1}^{N}c_{i}\, \phi(a_{i}\cdot x)\,,\qquad c_{i}\in {\mathbb{R}}\,,\quad a_{i}\in {\mathbb{R}}^{d}\,,
$$

the Hessian splits into blocks, one per hidden neuron,

$$
\nabla_{\theta}^{2} f_{\theta}(x) = \bigoplus_{i=1}^{N}(\nabla_{\theta}^{2} f)_{i}\,,\qquad (\nabla_{\theta}^{2} f)_{i} = \frac{1}{\sqrt{N}}\begin{pmatrix}0&\phi'(a_{i}\cdot x)\, x^{T} \\ \phi'(a_{i}\cdot x)\, x&c_{i}\, \phi''(a_{i}\cdot x)\, x x^{T}\end{pmatrix}\,.
$$

The operator norm of a block-diagonal matrix is the largest operator norm of its blocks. Each block has fixed size $$(d+1)\times(d+1)$$, contains only order-one quantities (at least at initialization), and carries an explicit factor $$1/\sqrt{N}$$. Thus

$$
\| \nabla_{\theta}^{2} f\| = \max_{i=1,...,N}\| (\nabla_{\theta}^{2} f)_{i}\| = O\Big(\frac{1}{\sqrt{N}}\Big)\qquad \text{as $N\to\infty$}\,.
$$

It's reasonable to expect that this bound continues to hold during training, and with a bit more work it can be proven (though we won't do it here). It also holds for networks of arbitrary fixed depth. A more careful analysis, keeping track of cancellations among the fluctuating terms, improves the resulting bound on the kernel drift to $$O(1/N)$$; the crude $$O(1/\sqrt{N})$$ is enough for the argument.

*Putting the pieces together.* First, the parameters do not move far in total. From $$\dot\theta = -\eta\sum_{\mu}\Delta^{\mu}\nabla_{\theta} f^{\mu}$$,

$$
|\dot\theta|^{2} = \eta^{2}\Big|\sum_{\mu=1}^{n}\Delta^{\mu}\nabla_{\theta} f^{\mu}\Big|^{2} \leq \eta^{2}\,|\Delta|^{2}\,|\nabla_{\theta} f|^{2} \leq \eta^{2}\,n\,|\Delta|^{2}\,\|\Theta\| = O(1)\,,
$$

where $$|\nabla_{\theta} f|^{2} = \sum_{\mu}\Theta^{\mu\mu}= \mathrm{tr}\,\Theta$$. So by the mean value theorem, $$\theta(t)-\theta_{0} = t\,\dot\theta(\bar t)$$ for some $$\bar t\in[0,t]$$, and

$$
|\theta(t)-\theta_{0}| = O(1)\qquad\text{for any fixed }t\,.
$$

An order-one total displacement, shared among $$P\approx Nd$$ parameters, means that each individual weight moves only by $$O(1/\sqrt{N})$$: relative to its order-one initial value, every weight barely changes. Second, the kernel freezes. By (4.25) and (4.28),

$$
\big\|\Theta(t) - \Theta(0)\big\| \leq t\, \|\dot\Theta(\bar t)\| \lesssim t\,\eta\,\|\nabla_{\theta}^{2} f\|\,\|\Theta\|\,|\Delta| = O\Big(\frac{1}{\sqrt{N}}\Big)\,,
$$

so the order-one kernel $$\Theta$$ becomes constant as $$N\to\infty$$. Third, the network linearizes. By Taylor's theorem with remainder,

$$
f_{\theta}(x)-f_{\theta_0}(x) = \nabla_{\theta} f(x)\big|_{\theta_0}\cdot (\theta-\theta_{0}) +\frac{1}{2}(\theta-\theta_{0})\cdot \nabla_{\theta}^{2} f(x)\big|_{\bar\theta}\cdot (\theta-\theta_{0})
$$

for some $$\bar\theta$$ on the segment between $$\theta_{0}$$ and $$\theta$$. Setting $$\theta=\theta(t)$$ and using (4.30) and (4.28), the quadratic term is bounded by

$$
\Big|\frac{1}{2}(\theta-\theta_{0})\cdot \nabla_{\theta}^{2} f(x)\big|_{\bar\theta}\cdot (\theta-\theta_{0})\Big| \leq \frac{1}{2}\|\nabla_{\theta}^{2} f\|\; |\theta-\theta_{0}|^{2} = O\Big( \frac{1}{\sqrt{N}}\Big)\cdot O(1)\,,
$$

so the linear approximation becomes exact as $$N\to\infty$$, even though the linear term, and with it the network function, moves by an order-one amount. In words: each of the $$N$$ neurons has $$O(1/\sqrt{N})$$ leverage on the output, so an order-one change in $$f$$ can be assembled from $$O(1/\sqrt{N})$$ changes in every weight, and changes that small leave the features $$\nabla_{\theta} f$$ untouched.

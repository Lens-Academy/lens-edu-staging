---
id: '058b6547-7a00-42d7-aa50-f4689e333951'
title: "B.6.6 The NNGP correspondence and depth over width"
tldr: "How a wide network at initialization becomes a Gaussian process (NNGP), the functional-integral derivation, the L/N ratio and the edge of chaos."
summary_for_tutor: "Sections 3.4-3.7 of Iliad worksheet B.6 Physics of Deep Learning. Covers the NNGP correspondence by induction over layers with the deterministic kernel recursion, closed-form kernels (ReLU, erf), the functional-integral derivation for one hidden layer, why depth over width L/N controls non-Gaussianity (deep linear network analysis, Hanin lecture 2), and the edge of chaos with critical depth. Contains Exercise 3.2 (NNGP empirically, lab) and Exercise 3.3 (depth-to-width ratios in the wild), both with collapsed solutions. Keep K-bar^(l), sigma_w, L/N. Let the student attempt each exercise before revealing or paraphrasing a solution."
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
\### 3.4 The NNGP correspondence

A classic result in the theory of neural networks is that, at fixed depth and large width, with the fan-in normalization of Section 3.2, the network function at initialization converges to a Gaussian process. The theorem appeared in the 90's (Neal 1996) for a single hidden layer, and was generalized more recently to deeper networks and different architectures, *cf.* (Lee et al. 2018; Yang 2019; Hanin 2023).

In this theorem, the source of stochasticity in the network function comes from the random initializations of network parameters. One can think of randomly initializing a swarm of networks and asking what sorts of values the network function outputs. The result is significant because of its universality, and because it feeds into (and greatly simplifies) further analyses of training.

The derivation proceeds via induction. We'll just sketch it here, for MLP's.

[^2]

For simplicity we'll assume that biases have been set to zero, and that all weights have the same order-one variance $$\sigma_{w}$$, as in (3.1), with the fan-in normalization of Section 3.2.

In the first network layer, the preactivations are

$$
z_{i}^{(1)}(x) = \frac{1}{\sqrt{d}}\sum_{j=1}^{d} w_{ij}^{(1)}x_{j}\,,\qquad w_{ij}^{(1)}\sim {{\mathcal N}}(0,\sigma_{w})\,.
$$

At fixed $$x$$, each $$z_{i}^{(1)}(x)$$ is a sum of $$d$$ i.i.d. Gaussian variables (with coefficients $$x_{j}$$), and thus is Gaussian itself, with $${\mathbb{E}}[z_{i}^{(1)}] = 0$$ and

$$
\text{Cov}\big(z_{i}^{(1)}(x),z_{i}^{(1)}(x')\big) = \frac{1}{d}\sum_{j,j'=1}^{d} \underbrace{\text{Cov}(w_{ij},w_{ij'})}_{\delta_{jj'} \sigma_w}x_{j} x'_{j'}= \sigma_{w}\frac{x\cdot x'}{d}\,,
$$

thus $$z_{i}^{(1)}$$ is a Gaussian process (GP) with

$$
z_{i}^{(1)}\sim {{\mathcal N}}(0,K^{(1)})\,,\qquad K^{(1)}(x,x') = \sigma_{w}\frac{x\cdot x'}{d}\,.
$$

In the second layer, we've got

$$
z_{i}^{(2)}= \frac{1}{\sqrt{N_{1}}}\sum_{j=1}^{N_1}w_{ij}^{(2)}\phi(z_{j}^{(1)})\,,\qquad w_{ij}^{(2)}\sim {{\mathcal N}}(0,\sigma_{w})\,.
$$

*If we condition on the preactivations of the first layer*, the same argument gives

$$
z_{i}^{(2)}\sim {{\mathcal N}}(0,K^{(2)})\,,\qquad K^{(2)}(z^{(1)},z^{(1)}{}') = \sigma_{w}\frac{\phi(z^{(1)})\cdot \phi(z^{(1)}{}')}{N_{1}}\,.
$$

Thus we again get a Gaussian process. The problem is that if we don't condition on the preactivations, the kernel of this GP is not deterministic, but becomes a random variable itself: $$\phi(z^{(1)})\cdot \phi(z^{(1)}{}')$$. This is where the infinite-width limit comes in. Heuristically, the central limit theorem implies that the sum of products of (non-Gaussian!) random variables on the LHS of (3.25) will become Gaussian as $$N_{1}\to\infty$$. More concretely, we can calculate and bound the variance

$$
\begin{aligned}\text{Var}\big(K^{(2)}(z^{(1)},z^{(1)}{}')\big)&= \frac{\sigma_{w}^{2}}{N_{1}^{2}}\text{Var}\big(\phi(z^{(1)})\cdot \phi(z^{(1)}{}')\big) \\&= \frac{\sigma_{w}^{2}}{N_{1}^{2}}N_{1} \cdot \text{Var}\big(\phi(z_{1}^{(1)}) \phi(z_{1}^{(1)}{}')\big) \to 0 \quad\text{as $N_{1}\to\infty$}\end{aligned}
$$

as long as the first-layer preactivations are order one (independent of $$N_{1}$$), and the activation function is reasonable (any standard choice will be). Thus, as $$N_{1}\to\infty$$, we can replace the stochastic kernel $$K^{(2)}$$ by its expectation,

$$
\bar K^{(2)}(x,x') := \sigma_{w} \, {\mathbb{E}}_{z_1^{(1)}(x),z_1^{(1)}(x')\sim {{\mathcal N}}(0,K^{(1)})}[ \phi(z_{1}^{(1)}(x)) \phi(z_{1}^{(1)}(x')) ]
$$

Each subsequent layer is the same. At infinite width, the kernels become deterministic, and obey a recursion

$$
\bar K^{(\ell)}(x,x') = \sigma_{w}\, {\mathbb{E}}_{u(x),u(x') \sim {{\mathcal N}}(0,\bar K^{(\ell-1)})}[ \phi(u(x)) \phi(u(x')) ]\,,
$$

with $$\bar K^{L+1}(x,x')$$ ultimately governing a GP for the network function $$f(x)$$.

:::callout {title="Note" tone="blue"}

**Remark (exact kernels).** For a few special activation functions, the Gaussian expectation in (3.30) can be evaluated in closed form, giving explicit NNGP kernels. Write $$K_{11}=\bar K^{(\ell-1)}(x,x)$$, $$K_{22}=\bar K^{(\ell-1)}(x',x')$$ and $$K_{12}=\bar K^{(\ell-1)}(x,x')$$ for the previous layer's kernel values. For ReLU, $$\phi(u)=\max(u,0)$$, one finds the *arc-cosine kernel* of Cho and Saul (Cho & Saul 2009),

$$
\begin{aligned}\bar K^{(\ell)}(x,x')&= \frac{\sigma_w}{2\pi}\,\sqrt{K_{11}K_{22}}\;\Big(\sin\vartheta + (\pi - \vartheta)\cos\vartheta\Big)\,, \\ \cos\vartheta&= \frac{K_{12}}{\sqrt{K_{11}K_{22}}}\,,\end{aligned}
$$

and for the sigmoid-like activation $$\phi = \mathrm{erf}$$ Williams (Williams 1997) found

$$
\bar K^{(\ell)}(x,x') = \frac{2\sigma_{w}}{\pi}\, \arcsin\!\left(\frac{2K_{12}}{\sqrt{(1+2K_{11})(1+2K_{22})}}\right)\,.
$$

Iterating either formula through the layers gives the exact infinite-width kernel of a deep ReLU or erf network in a few lines of code. (Deriving (3.31)–(3.32) is a pleasant but somewhat lengthy Gaussian-integral workout.)

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.2 (The NNGP correspondence, empirically (lab)).** Fix two unit-norm inputs $$x, x'\in{\mathbb{R}}^{d}$$ with, say, $$d=8$$ and $$x\cdot x' = 0.5$$. For widths $$N \in \{3, 30, 300\}$$, sample $$M = 10^{4}$$ independent initializations of the one-hidden-layer erf network $$f(x) = \frac{1}{\sqrt{N}}\sum_{i=1}^{N} c_{i}\, \mathrm{erf}\big(a_{i}\cdot x/\sqrt{d}\big)$$ with $$c_{i}, a_{ij}\sim{{\mathcal N}}(0,1)$$ (that is, $$\sigma_{w} = 1$$).

**(a)** Make a histogram of the values $$f(x)$$ across the ensemble, and overlay the Gaussian density with the variance $$\bar K^{(2)}(x,x)$$ predicted by (3.32); watch the visibly non-Gaussian $$N=3$$ histogram converge.

**(b)** Make a scatter plot of the pairs $$\big(f(x), f(x')\big)$$ and compare the sample $$2\times2$$ covariance with the predicted kernel matrix.

**(c)** For each initialization, record the stochastic kernel $$K^{(2)}$$ of (3.26), and verify that its variance across initializations decays like $$1/N$$ (that's the mechanism by which the kernel becomes deterministic).
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Everything is closed-form thanks to the erf kernel (3.32), which is the point of choosing erf. Expected observations:

**(a)** at $$N=3$$ the histogram has visibly heavy tails and excess kurtosis (the output is a sum of only three i.i.d. non-Gaussian terms); at $$N=30$$ deviations are still detectable; at $$N=300$$ the histogram is indistinguishable from the predicted Gaussian at this sample size.

**(b)** The sample covariance matches the $$2\times2$$ kernel matrix built from (3.32) to within the Monte Carlo error $$O(M^{-1/2})$$.

**(c)** A log–log plot of $$\mathrm{Var}(K^{(2)})$$ against $$N$$ has slope $$-1$$, as in the variance computation of Section 3.4. The whole lab is $$\sim$$20 lines of NumPy; the one subtlety is to histogram over *initializations* at fixed inputs, not over inputs.

:::

\### 3.5 NNGP via functional integrals

One can also analyze large width at initialization via functional integrals. This just reorganizes the above steps. We'll illustrate how it works for a network with one hidden layer and zero biases, $$N_{2}=1,\,N_{1}=N,\,N_{0}=d$$,

$$
f(x) = \frac{1}{\sqrt{N}}\sum_{i=1}^{N} c_{i}\,\phi\Big(\frac{1}{\sqrt{d}}\,a_{i}\cdot x\Big)\,,\qquad c_{i}\in {\mathbb{R}},\;a_{i},x\in {\mathbb{R}}^{d}\,.
$$

The initial distribution of weights, all of variance $$\sigma_{w}$$, is

$$
P(c,a) = \frac{1}{Z}\,e^{\textstyle -\frac{1}{2\sigma_{w}}|c|^2-\frac{1}{2\sigma_{w}}|a|^2}\,.
$$

To push this forward to a distribution on the first-layer preactivations $$z_{i}=\frac{1}{\sqrt{d}}a_{i}\cdot x$$, we integrate against a delta function:

$$
P(c,z)= \int da\, P(c,a)\,\prod_{i}\delta\Big(z_{i}(x)-\tfrac{1}{\sqrt{d}}a_{i}\cdot x\Big)\,.
$$

Here the $$z_{i}(x)$$ are *arbitrary* functions of $$x$$, and are only tied to the network values $$\frac{1}{\sqrt{d}}a_{i}\cdot x$$ via the delta functions. Eqn. (3.35) represents a functional probability density on the functions $$z_{i}$$. To evaluate it, introduce a second set of "Lagrange multiplier" functions $$\tilde z_{i}$$, and write

$$
\delta\Big(z_{i}(x)-\tfrac{1}{\sqrt{d}}a_{i}\cdot x\Big) = \int D\tilde z_{i}\, e^{\textstyle i \int dx\, \tilde z_i(x) (z_i(x)-\frac{1}{\sqrt{d}}a_i\cdot x)}\,,
$$

and then do the exact Gaussian integral over $$a$$'s, and then over $$\tilde z$$'s:

$$
\begin{aligned}P(c,z)&= \frac{1}{Z}\int da\,D\tilde z\, \exp\bigg[\textstyle -\frac{1}{2\sigma_{w}}|c|^{2}-\sum_{i} \frac{1}{2\sigma_{w}}|a_{i}|^{2} \notag \\&\hspace{1.5in}\textstyle + i \sum_{i} \int dx\, \tilde z_{i}(x)(z_{i}(x)-\frac{1}{\sqrt{d}}a_{i}\cdot x)\bigg] \\&= \frac{1}{Z}\int da\,D\tilde z\, \exp\bigg[\textstyle -\frac{1}{2\sigma_{w}}|c|^{2}+\sum_{i}\Big[- \frac{1}{2\sigma_{w}}\big(a_{i}+\frac{i\sigma_{w}}{\sqrt{d}}\int dx\,\tilde z_{i}(x) x\big)^{2} \notag \\&\hspace{.4in}\textstyle-\frac{\sigma_{w}}{2d}\int dx\,dx'\, \tilde z_{i}(x) (x\cdot x') \tilde z_{i}(x') + i \int dx\, \tilde z_{i}(x)z_{i}(x)\Big]\bigg] \\&= \frac{1}{Z'}\int D\tilde z\,\exp\bigg[\textstyle -\frac{1}{2\sigma_{w}}|c|^{2}-\frac{\sigma_{w}}{2d}\sum_{i}\int dx\,dx'\, \tilde z_{i}(x) (x\cdot x') \tilde z_{i}(x') \notag \\&\hspace{1.5in}\textstyle + i \sum_{i}\int dx\, \tilde z_{i}(x)z_{i}(x)\bigg] \\&= \frac{1}{Z''}\exp\bigg[\textstyle -\frac{1}{2\sigma_{w}}|c|^{2} - \frac{1}{2\sigma_{w}}\sum_{i} \int dx\,dx'\, z_{i}(x) \big(\frac{x\cdot x'}{d}\big)^{-1}z_{i}(x')\bigg]\,.\end{aligned}
$$

We clearly see the first-layer GP kernel $$K^{(1)}(x,x') = \frac{\sigma_{w}}{d}x\cdot x'$$ appearing.

To push-forward to the network outputs $$f = \frac{1}{\sqrt{N}}c\cdot \phi(z)$$, we just do this again:

$$
\begin{aligned}P(f)&= \int dc\,Dz\, P(c,z)\, \delta\Big(f(x)-\tfrac{1}{\sqrt{N}}c\cdot \phi(z(x))\Big) \\&= \frac{1}{Z''}\int dc\,Dz\,D\tilde f\, \exp\bigg[\textstyle -\frac{1}{2\sigma_{w}}|c|^{2} \notag \\&\hspace{1in}\textstyle - \frac{1}{2\sigma_{w}}\sum_{i} \int dx\,dx'\, z_{i}(x) \big(\frac{x\cdot x'}{d}\big)^{-1}z_{i}(x') \notag \\&\hspace{1in}\textstyle + i\int dx \tilde f(x)(f(x)-\frac{1}{\sqrt{N}}c\cdot \phi(z(x)))\bigg] \\&\hspace{-.2in}= \frac{1}{Z'''}\int Dz\,D\tilde f\, \exp\bigg[\textstyle - \frac{1}{2\sigma_{w}}\int dx\,dx'\, \big(\frac{x\cdot x'}{d}\big)^{-1}z(x)\cdot z(x') \notag \\&\hspace{.3in}\textstyle - \frac{\sigma_{w}}{2N}\int dx\,dx' \tilde f(x)[\phi(z(x))\cdot \phi(z(x'))]\tilde f(x') +i\int dx\, \tilde f(x) f(x)\bigg]\end{aligned}
$$

The problem is that it's now impossible to do the integral over the $$z$$'s exactly, because (for general activation function $$\phi$$) the action is no longer quadratic in them. However, as $$N\to \infty$$, we can treat $$\exp\big[- \frac{\sigma_{w}}{2N}\int dx\,dx' \tilde f(x)[\phi(z(x))\cdot \phi(z(x'))]\tilde f(x')\big]$$ as a perturbation, and approximate the *exponent* $$[\phi(z(x))\cdot \phi(z(x'))]$$ by its expectation value under the Gaussian measure $$\exp\big[- \frac{1}{2\sigma_{w}}\int dx\,dx'\, \big(\frac{x\cdot x'}{d}\big)^{-1}z(x)\cdot z(x')\big]$$ (with kernel $$K^{(1)}$$) on the $$z$$'s. To be clear, the approximation that's happening is of the form

$$
{\mathbb{E}} \,e^{\frac{1}{N} X}= e^{\frac{1}{N} {\mathbb{E}} X}+ O(\text{Var}(X)/N^{2})
$$

Up to $$O(1/N)$$ corrections, that produces the deterministic kernel of the previous section,

$$
\bar K^{(2)}(x,x') = \sigma_{w}\, {\mathbb{E}}_{z\sim {{\mathcal N}}(0,K^{(1)})}\big[ \phi(z(x))\, \phi(z(x'))\big]\,,
$$

and we get

$$
\begin{aligned}P(f)&= \frac{1}{Z''''}\int D\tilde f\, \exp\bigg[\textstyle -\frac{1}{2}\int dx\, dx'\, \tilde f(x) \bar K^{(2)}(x,x') \tilde f(x') \notag \\&\hspace{1.5in}\textstyle + i\int dx\, \tilde f(x) f(x)\bigg] + O\Big(\frac{1}{N}\Big) \\&= \frac{1}{Z'''''}\exp\bigg[\textstyle -\frac{1}{2}\int dx\, dx'\, f(x) \bar K^{(2)}(x,x')^{-1}f(x')\bigg] +O\Big(\frac{1}{N}\Big) \,.\end{aligned}
$$

\### 3.6 L/N

The inductive argument of Section 3.4 does not hold at infinite $$L$$. There are two potential problems.

First, a factor of $$\sigma_{w}$$ appears with every layer. These factors will accumulate, and can lead either to vanishing kernels (which also turns out to imply vanishing gradients during training), in which case the network will collapse; or to unbounded kernels (and increasingly large gradients), in which case the network will be chaotic and again untrainable. We'll revisit this in Section 3.7. With careful tuning, the issue can be avoided. For example, in a deep linear network (DLN) with $$\phi(z)=z$$, one can just take $$\sigma_{w}=1$$, known as LeCun initialization (LeCun et al. 1998). In a ReLU network, the correct choice instead is $$\sigma_{w}=2$$, known as He initialization (He et al. 2015).

Even with $$\sigma_{w}$$ tuned, according to the activation function, so that on average the GP kernels remain order-one from layer to layer, non-Gaussianities can still accumulate. The upshot is that it is not width alone, say of typical size $$N$$, but rather the ratio $$L/N$$ of depth-to-width that controls the effective behavior of a network — including its departure from pure Gaussianity at large $$N$$.

This behavior is analyzed in Chapters 3-4 of (Roberts et al. 2022) using functional-integral methods. In particular, Chapter 3 considers the simple example of DLN's, and produces exact recursion relations for higher cumulants of preactivations in each layer. It is shown that in a network of constant hidden width $$N$$, the leading non-Gaussianity is

$$
\begin{aligned}\kappa_{4}^{(L+1)}&= \Big[ \Big(1+\frac{2}{N}\Big)^{L}-1\Big](\kappa_{2}^{(L+1)})^{2} \\&= \Big[(e^{2L/N}-1)-\frac{1}{N}\frac{2L}{N}e^{2L/N}+O(N^{-2})\Big](\kappa_{2}^{(L+1)})^{2}\,,\end{aligned}
$$

where the expansion on the RHS is at finite $$L/N$$ and $$L,N\to\infty$$. For small $$L/N$$, the non-Gaussianity remains small but finite, of size $$L/N$$. For large $$L/N$$, $$\kappa_{4}^{(L+1)}$$ blows up, as do all the other cumulants. The network outputs will fluctuate chaotically from one instantiation to another, and the network again becomes untrainable.

Here's a more direct analysis, in a special case, following (Hanin 2026, Lecture 2). Consider a DLN of length $$L$$ with input and hidden layers all of width $$N$$:

$$
\begin{aligned}z^{(\ell)}&= \frac{1}{\sqrt{N}}\,w^{(\ell)}z^{(\ell-1)}\,,\qquad z^{(0)}=x\,, \\ f(x)&= z^{(L+1)}=N^{-\frac{L+1}{2}}\,w^{(L+1)}\cdots w^{(1)}x\,,\end{aligned}
$$

with $$w_{ij}^{(\ell)}\sim {{\mathcal N}}(0,1)$$, i.e. $$\sigma_{w}=1$$ (and input dimension $$d=N$$). Conditional on $$z^{(\ell-1)}$$, the vector $$z^{(\ell)}$$ is Gaussian $$z^{(\ell)}\sim {{\mathcal N}}\big(0,\frac{1}{N}I_{N} |z^{(\ell-1)}|^{2}\big)$$, so its norm satisfies the recursion

$$
|z^{(\ell)}|^{2} \sim |z^{(\ell-1)}|^{2} \frac{\chi^{2}_{N}}{N}\,.
$$

(Recall that $$\chi^{2}_{N}$$ is the distribution of the sum of squares of $$N$$ i.i.d. standard Gaussian variables.) Let's normalize the input so that $$|x|=1$$. Then the recursion implies that

$$
|f(x)|^{2} \overset{d}{=}\prod_{k=1}^{L+1}\frac{\chi^{2}_{N}}{N}= \exp\sum_{k=1}^{L+1}\big(\log \chi^{2}_{N}-\log N\big)\,,
$$

with each factor of $$\chi^{2}_{N}$$ independent. At large $$N$$, we have $$\log \chi_{N}^{2}-\log N = {{\mathcal N}}(-\frac{1}{N},\frac{2}{N})+O(\frac{1}{N^{2}})$$, so at large $$N,L$$ with $$L/N$$ fixed

$$
|f(x)|^{2} \overset{d}= e^{\textstyle {{\mathcal N}}(-\frac{L}{N},2\frac{L}{N})}\,,
$$

up to higher $$O(\frac{1}{N^{2}}$$ corrections. Thus, as $$L/N$$ grows, the expectation of $${\mathbb{E}}|f(x)|\to 0$$ but the variance and higher cumulants blow up.

The lesson once again is

- $$N\to \infty$$, $$L/N=0$$: Gaussian process, no correlations across layers (and, as we'll see in Section 4, no "feature learning").
- $$N,L\to \infty$$, $$L/N$$ small: controlled correlations, trainable network (and, as we'll see, feature learning during training). In open-weight LLM's today, $$L/N\approx 0.005$$–$$0.01$$; see Exercise 3.3.
- $$N,L\to\infty$$, $$L/N$$ large: chaotic and untrainable.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.3 (★) (Depth-to-width ratios in the wild).** Look up the depth $$L$$ (number of transformer blocks) and the width $$N$$ (model/embedding dimension) for a few families of open-weight language models — *e.g.* GPT-2, the Llama family, the Qwen family — and compute $$L/N$$ for each. How much does the ratio vary across families, across sizes within a family, and across the years? Is everyone training in the "controlled correlations" window?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Representative numbers at the time of writing (take the width $$N$$ to be the model/embedding dimension): GPT-2 small has $$L/N = 12/768 \approx 0.016$$ and GPT-2 XL $$48/1600 = 0.030$$; Llama-2-7B has $$32/4096 \approx 0.008$$; Llama-2-70B, $$80/8192 \approx 0.010$$; Llama-3-405B, $$126/16384 \approx 0.008$$. The striking finding is how *stable* the ratio is: modern open-weight families cluster around $$L/N \sim 0.005$$–$$0.01$$ across two orders of magnitude in parameter count, comfortably inside the "controlled correlations" window, with the earliest (GPT-2-era) models running noticeably deeper for their width. Whether this stability reflects tuned wisdom or copied convention is a fair discussion question.

:::

\### 3.7 Edge of chaos

We briefly remark that the analysis of how to tune initialization variances $$\sigma_{w},\sigma_{b}$$ (etc.) leading to stable network behavior over a large number of layers (the first point in Section 3.6) is sometimes called finding the "edge of chaos."

The term dates back to dynamical systems theory from the 80's and 90's, referring to the boundary between ordered and chaotic phases. It was adapted to neural networks around 2016 (Poole et al. 2016; Schoenholz et al. 2017). The idea was to treat the progression through layers of a network as a dynamical system, and to ask: given two nearby inputs $$x,x'$$, for what range of hyperparameters ($$\sigma_{w},\sigma_{b}$$, etc.) and to what depth do they remain nearby, without either a) collapsing; or (b) blowing up chaotically (with no correlation). The analysis roughly amounts to making sure the kernel recursion of (3.26), (3.30) leads to kernels that neither collapse nor blow up. Doing it carefully, theoretically, can produce elementary trainable networks (with no layer norms!) over 10,000 layers deep (Xiao et al. 2018).

![Order/chaos phase diagram for a tanh network, with shading indicating the critical depth to which a network is trainable.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-qft-eoc-phase-a2fd0596.png)

Order/chaos phase diagram for a tanh network, with shading indicating the critical depth to which a network is trainable.

For MLP's with ReLu activations, the edge of chaos is just the one point $$\sigma_{w}=2,\,\sigma_{b}=0$$. Moving slightly away from this point, one can estimate the "critical depth" $$L_{c}$$ at which the network either collapses or blows up – see (Schoenholz et al. 2017). For MLP's with other activation functions, the edge of chaos is more interesting. For $$\phi=\tanh$$, the phase diagram is shown in Figure 5.

The quantity `$$\chi_{1}$$' that controls the critical depth ($$L_{c}= -1/\log \chi_{1}$$) is the derivative of the layer-to-layer kernel recursion at its fixed point, which measures how fast nearby inputs separate. Importantly, the same quantity $$\chi_{1}$$ also controls the size of gradients as they back-prop through a network *during training*. There's a direct link between behavior at initialization and behavior during training. We come to training next.

[^2]: For transformers, the limit analogous to "large width" that leads to a Gaussian process is a large number of attention heads.

---
id: '23f55b85-d09f-4e6c-9bab-4f52a1f51c46'
title: "B.5.6 Bayesian influence functions"
tldr: "Introduces susceptibilities and the Bayesian influence function as a covariance under the tempered posterior, with Exercise 3.1 proving it, then localization, SGLD estimation and a Bayesian linear regression example."
summary_for_tutor: "Section 3 intro and 3.1 of Iliad worksheet B.5 Data Attribution: susceptibilities (Baker et al. 2026), the tempered posterior, Definition 3.1 (Bayesian influence function), Exercise 3.1 (the BIF is a covariance, with collapsed solution), a statistical-physics remark on fluctuation-response, localization with strength gamma, practical computation by SGLD, and Example 3.2 (Bayesian linear regression). Keep Cov(L_i, phi) and the sign convention. Let the student attempt each exercise before revealing or paraphrasing a solution."
source_url: https://iliad-intensive.org/learning/data-attribution/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 3. Bayesian Influence Functions

Classical influence functions give a first-order approximation to the change in a *point estimate* $$w^{*}$$ when the training data is perturbed. The Bayesian reformulation replaces this point estimate by a *distribution* over parameters: if we perturb the training data, how does our posterior over the parameter space change? This leads naturally to the Bayesian generalization of influence functions introduced in Kreer et al. 2026. In the setting of Equation 1 we set $$\pi(\beta)$$ not to be a single weight, but a whole distribution over parameters $$p_{\beta}$$, namely the posterior.

**Susceptibilities.**  The Bayesian influence function is one instance of a more general object studied by Baker et al. 2026. Given a tempered Gibbs posterior $$p_{\beta} \propto e^{-\beta L(w)}\varphi(w)$$ at inverse temperature $$\beta$$, any pair of observables $$\phi,\psi:W\to{\mathbb{R}}$$ defines a *susceptibility*

$$
\chi(\phi\,|\,\psi) \;:=\; \frac{\partial}{\partial h}\,{\mathbb{E}}_{p_h}[\phi(w)]\bigg|_{h=0}, \qquad p_{h} \;\propto\; e^{-\beta\bigl(L(w) - h\,\psi(w)\bigr)}\,\varphi(w).
$$

The differentiation argument we will apply in Exercise 3.1 shows $$\chi(\phi\,|\,\psi) = \beta\,\mathrm{Cov}_{p_\beta}(\phi,\psi)$$ in full generality. Taking $$\psi = -L(\cdot,z_{i})$$ gives the Bayesian influence function developed below. Other choices of $$(\phi,\psi)$$ yield other sensitivity notions, see e.g. the refined learning coefficients (Baker et al. 2026, Appendix D.2). We will not need the general framework again; we mention it only to locate the BIF within the wider susceptibility family.

\### 3.1 Bayesian influence functions

We now specialize the susceptibility story to data attribution. Instead of asking "how does $$\phi(w^{*})$$ change when we perturb the training weights?" (Definition 2.2) we ask "how does $${\mathbb{E}}_{w\sim p}[\phi(w)]$$ change?" The answer turns out to be remarkably clean: the derivative becomes a covariance, and the Hessian inversion of the classical formula is replaced by posterior sampling.

**The tempered posterior.**  Given training data $$\mathcal{D}= \{z_{1},\dots,z_{n}\}$$ with per-sample losses $$L(w,z_{i})$$, sample weights $$\beta = (\beta_{1},\dots,\beta_{n})$$, and a prior $$\varphi(w)$$, define the *tempered posterior*

$$
p_{\beta}(w\mid\mathcal{D}) \;\propto\; \exp\!\Bigl(-\sum_{i=1}^{n} \beta_{i}\, L(w,z_{i})\Bigr)\,\varphi(w).
$$

When $$\beta = \mathbf{1}$$ and the loss is a negative log-likelihood, this is the standard Bayesian posterior. When the losses are not log-likelihoods, $$p_{\beta}$$ is a *Gibbs measure*; the mathematics is identical.

:::callout {title="Definition" tone="blue"}

**Definition 3.1 (Bayesian influence function).** The *Bayesian influence function* (BIF) of training example $$z_{i}$$ on the observable $$\phi$$ is the derivative of the posterior expectation of $$\phi$$ with respect to the sample weight $$\beta_{i}$$:

$$
\mathrm{BIF}(z_{i},\phi) \;:=\; \frac{\partial}{\partial\beta_{i}}\,{\mathbb{E}}_{w\sim p_\beta}[\phi(w)]\bigg\rvert_{\beta=\mathbf{1}}.
$$

:::

The definition is the natural Bayesian analogue of Definition 2.2: replace $$\phi(w^{*}(\beta))$$ with $${\mathbb{E}}_{p_\beta}[\phi(w)]$$. The following exercise shows that this derivative has a clean closed form. Recall that for two real-valued random variables $$X$$ and $$Y$$ defined on the same probability space, the *covariance* is

$$
\mathrm{Cov}(X,Y) \;=\; {\mathbb{E}}[XY] - {\mathbb{E}}[X]\,{\mathbb{E}}[Y].
$$

When $$X$$ and $$Y$$ are functions of the random parameter $$w\sim p$$, we write $$\mathrm{Cov}_{w\sim p}(X(w),Y(w))$$ to indicate that the expectation is taken over the posterior $$p$$. If $$\phi$$ is vector-valued ($$\phi:W\to{\mathbb{R}}^{d}$$), the covariance $$\mathrm{Cov}(X,\phi)$$ is the vector whose $$j$$-th entry is $$\mathrm{Cov}(X,\phi_{j})$$.

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1 (The BIF is a covariance).** Let $$p_{\beta}(w\mid\mathcal{D})$$ be the tempered posterior of Equation 8 and write $$p = p_{\mathbf{1}}$$ for the unperturbed posterior. By differentiating $${\mathbb{E}}_{p_\beta}[\phi(w)] = \int \phi(w)\,p_{\beta}(w\mid\mathcal{D})\,dw$$ with respect to $$\beta_{i}$$, show that

$$
\boxed{\;\mathrm{BIF}(z_i,\phi) \;=\; -\,\mathrm{Cov}_{w\sim p}\bigl(L(w,z_i),\;\phi(w)\bigr).\;}
$$

*Hint:* Write $$p_{\beta} \propto e^{-\sum_j \beta_j L(w,z_j)}\varphi(w)$$ and differentiate the ratio $$\int \phi\, p_{\beta}\,dw \,/\, \int p_{\beta}\,dw$$ using the quotient rule. The key identity is $$\partial_{\beta_i}\log Z(\beta) = -{\mathbb{E}}_{p_\beta}[L(w,z_{i})]$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Write $$Z(\beta) = \int \exp(-\sum_{j} \beta_{j} L(w,z_{j}))\,\varphi(w)\,dw$$ for the normalizing constant, so that

$$
{\mathbb{E}}_{p_\beta}[\phi(w)] \;=\; \frac{1}{Z(\beta)}\int \phi(w)\,\exp\!\Bigl(-\sum_{j} \beta_{j} L(w,z_{j})\Bigr)\,\varphi(w)\,dw.
$$

Differentiating with respect to $$\beta_{i}$$ and applying the quotient rule:

$$
\begin{aligned}\frac{\partial}{\partial\beta_{i}}\,{\mathbb{E}}_{p_\beta}[\phi]&\;=\; \frac{1}{Z}\int \phi(w)\bigl(-L(w,z_{i})\bigr)\,e^{-\sum_j\beta_j L_j}\,\varphi\,dw \\&\qquad\;-\; \frac{1}{Z^{2}}\cdot\frac{\partial Z}{\partial\beta_{i}}\int \phi\,e^{-\sum_j\beta_j L_j}\,\varphi\,dw.\end{aligned}
$$

The first term is $$-{\mathbb{E}}_{p_\beta}[\phi(w)\,L(w,z_{i})]$$. For the second, $$\partial_{\beta_i}Z = -Z\,{\mathbb{E}}_{p_\beta}[L(w,z_{i})]$$, so it equals $$+{\mathbb{E}}_{p_\beta}[L(w,z_{i})]\,{\mathbb{E}}_{p_\beta}[\phi(w)]$$. Evaluating at $$\beta=\mathbf{1}$$:

$$
\mathrm{BIF}(z_{i},\phi) = -{\mathbb{E}}_{p}[\phi\cdot L_{i}] + {\mathbb{E}}_{p}[\phi]\,{\mathbb{E}}_{p}[L_{i}] = -\mathrm{Cov}_{w\sim p}(L(w,z_{i}),\,\phi(w)).
$$

Structurally: in the classical IF, the "correlation" between $$L_{i}$$ and $$\phi$$ is mediated by the inverse Hessian acting on their gradients at a point; in the BIF it is mediated by the full posterior distribution. The inverse Hessian is how a Gaussian posterior would produce a covariance (as we will see in Exercise 3.2), so the BIF strictly generalizes the classical formula.

:::

:::callout {title="Note" tone="blue"}

**Remark (Statistical physics).** The identity $$\partial_{\beta_i}{\mathbb{E}}[\phi] = -\mathrm{Cov}(L_{i},\phi)$$ is a standard fluctuation–response relation in statistical physics: the response of an observable to a change in an external field equals the covariance of that observable with the conjugate energy.

:::

**Localization.**  Computing expectations over the global posterior $$p(w\mid\mathcal{D})$$ is generally intractable for neural networks, and we are typically interested in the behavior of a specific trained checkpoint $$w^{*}$$, not a global Bayesian average. Following Kreer et al. 2026, we *localize* the posterior by adding a Gaussian penalty centered at $$w^{*}$$:

$$
p_{\gamma}(w\mid\mathcal{D},w^{*}) \;\propto\; \exp\!\Bigl(-\sum_{i=1}^{n} L(w,z_{i}) - \frac{\gamma}{2}\|w - w^{*}\|^{2}\Bigr),
$$

where $$\gamma > 0$$ is a *localization strength* that controls how tightly the posterior concentrates around $$w^{*}$$. The *local BIF* is then

$$
\mathrm{BIF}_{\gamma}(z_{i},\phi) \;=\; -\,\mathrm{Cov}_{\gamma}\bigl(L(w,z_{i}),\;\phi(w)\bigr),
$$

where $$\mathrm{Cov}_{\gamma}$$ denotes covariance under $$p_{\gamma}$$. We will see in Exercise 3.2 that the localization parameter $$\gamma$$ plays exactly the role of the damping parameter $$\lambda$$ in the PBRF formula (6).

**Practical computation via SGLD.**  The local BIF requires estimating a covariance under $$p_{\gamma}$$. This is done by drawing samples from $$p_{\gamma}$$ using stochastic gradient Langevin dynamics (SGLD), which adds calibrated Gaussian noise to SGD updates:

$$
w_{t+1}\;=\; w_{t} - \frac{\epsilon}{2}\Bigl(\frac{n}{m}\sum_{k\in B_t}\nabla_{w} L(w_{t},z_{k}) + \gamma(w_{t} - w^{*})\Bigr) + \eta_{t},
$$

where $$\eta_{t}\sim\mathcal{N}(0,\epsilon\, I)$$, $$B_{t}$$ is a mini-batch of size $$m$$ and $$\epsilon$$ is the step size. After a burn-in period, the iterates $$\{w_{t}\}$$ are approximately distributed according to $$p_{\gamma}$$, and the covariance in (11) is estimated by the sample covariance of $$(L(w_{t},z_{i}),\phi(w_{t}))$$ across draws. Running multiple independent chains from $$w^{*}$$ improves coverage.

:::callout {title="Tip" tone="green"}

**Example 3.2 (Bayesian linear regression).** Take the linear regression setup of Exercise 2.2 with a Gaussian prior $$w\sim\mathcal{N}(0,\tau^{2}I)$$ added. The posterior is conjugate: $$w\mid\mathcal{D}\sim\mathcal{N}(\mu,V)$$ with $$V = (\tau^{-2}I + \sigma^{-2}A)^{-1}$$ and $$\mu = \sigma^{-2}V\sum_{i} x_{i} y_{i}$$. A direct Gaussian-moment computation applied to (9) with the observable $$\phi(w) = w$$ gives

$$
\mathrm{BIF}(z_{j}, w) \;=\; -\mathrm{Cov}_{p}\bigl(L(w,z_{j}),\,w\bigr) \;=\; \frac{V\, x_{j}\, r_{j}}{\sigma^{2}}\;=\; (A + \lambda I)^{-1}\,x_{j}\,r_{j}
$$

where $$r_{j} = y_{j} - x_{j}^{\top}\mu$$ is the posterior-mean residual and $$\lambda := \sigma^{2}/\tau^{2}$$. This is the *damped* influence function with the damping parameter $$\lambda$$ equal to the ratio of observation noise to prior variance. In the flat-prior limit $$\tau\to\infty$$ we have $$\lambda\to 0$$, $$\mu\to w^{*}$$, and we recover the classical IF of Exercise 2.2.

:::

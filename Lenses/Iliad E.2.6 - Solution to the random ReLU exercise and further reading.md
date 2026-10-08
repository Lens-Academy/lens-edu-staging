---
id: 'e4c3b5b0-dca2-4fac-a68e-327fe7a9c8f1'
title: "E.2.6 Solution to the random ReLU exercise and further reading"
tldr: "The collapsed worked solution to the random ReLU backdoor exercise, followed by two papers on cryptographic backdoors for further reading."
summary_for_tutor: "Section 15 of Iliad worksheet E.2, second part: the collapsed solution to Exercise 15.1 parts (a) to (e) (variances 1 and 1 + alpha^2 theta, E[ReLU(Z)] = sigma / sqrt(2 pi), Var(A_n) <= sigma^2 / n, the bound tau <= mu_reg + 1 / sqrt(n beta), and Pr[A'_n < tau] <= (1 + alpha^2 theta) / (n Delta_n^2)), then a Learn more list on cryptographic backdoors. Only reveal parts of the solution after the student has attempted the matching part of the exercise."
authors:
  - Stephan Wäldchen (Independent)
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/steganography/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Since $$g$$ is Gaussian and $$z=\langle g,x\rangle$$, the random variable $$z$$ is Gaussian. Its mean is $$0$$, and

$$
\operatorname{Var}(z) = x^{\top} (I_{d}+\theta ss^{\top})x = \|x\|_{2}^{2}+\theta\langle x,s\rangle^{2} = 1.
$$

Hence

$$
z\sim \mathcal{N}(0,1).
$$

Similarly, $$z'=\langle g,x+\alpha s\rangle$$ is centered Gaussian with variance

$$
\begin{aligned}\operatorname{Var}(z')&= \left(\sqrt{1-\alpha^2}x+\alpha s\right)^{\top} (I_{d}+\theta ss^{\top})\left(\sqrt{1-\alpha^2}x+\alpha s\right) \\&= \|\sqrt{1-\alpha^2}x+\alpha s\|_{2}^{2} + \theta \left\langle s,\sqrt{1-\alpha^2}x+\alpha s\right\rangle^{2}.\end{aligned}
$$

Using $$\|x\|_{2}=\|s\|_{2}=1$$ and $$\langle x,s\rangle=0$$, we get

$$
\|x+\alpha s\|_{2}^{2}=1, \qquad \left\langle s,\sqrt{1-\alpha^{2}}x+\alpha s\right\rangle=\alpha.
$$

Therefore

$$
\operatorname{Var}(z') = 1+\theta\alpha^{2},
$$

so

$$
z'\sim \mathcal{N}\bigl(0,1+\alpha^{2}\theta\bigr).
$$

**(b)** We compute

$$
\mathbb{E}[\operatorname{ReLU}(Z)] = \int_{0}^{\infty} z\cdot \frac{1}{\sqrt{2\pi}\sigma}e^{-z^2/(2\sigma^2)}\,dz.
$$

With the substitution

$$
u=\frac{z^{2}}{2\sigma^{2}}, \qquad z\,dz=\sigma^{2}\,du,
$$

this becomes

$$
\mathbb{E}[\operatorname{ReLU}(Z)] = \frac{1}{\sqrt{2\pi}\sigma}\int_{0}^{\infty} \sigma^{2} e^{-u}\,du = \frac{\sigma}{\sqrt{2\pi}}.
$$

Thus

$$
\mathbb{E}[\operatorname{ReLU}(z)] = \frac{1}{\sqrt{2\pi}},
$$

while

$$
\mathbb{E}[\operatorname{ReLU}(z')] = \frac{\sqrt{1+\alpha^{2}\theta}}{\sqrt{2\pi}}.
$$

Since $$\alpha>0$$ and $$\theta>0$$, we have

$$
\sqrt{1+\alpha^{2}\theta}> 1,
$$

so the backdoored sample has larger expected ReLU activation.

**(c)** Since

$$
\operatorname{Var}(\operatorname{ReLU}(Z)) \leq \mathbb{E}[\operatorname{ReLU}(Z)^{2}],
$$

and

$$
\operatorname{ReLU}(Z)^{2} \leq Z^{2},
$$

we get

$$
\operatorname{Var}(\operatorname{ReLU}(Z)) \leq \mathbb{E}[Z^{2}] = \sigma^{2}.
$$

For

$$
A_{n} := \frac{1}{n}\sum_{i=1}^{n} \operatorname{ReLU}(Z_{i}),
$$

we have

$$
\mathbb{E}[A_{n}] = \frac{1}{n}\sum_{i=1}^{n} \mathbb{E}[\operatorname{ReLU}(Z_{i})] = \frac{\sigma}{\sqrt{2\pi}}.
$$

Since the $$Z_{i}$$ are independent,

$$
\begin{aligned}\operatorname{Var}(A_{n})&= \operatorname{Var}\left( \frac{1}{n}\sum_{i=1}^{n} \operatorname{ReLU}(Z_{i}) \right) \\&= \frac{1}{n^2}\sum_{i=1}^{n} \operatorname{Var}(\operatorname{ReLU}(Z_{i})) \\&\leq \frac{1}{n^2}\cdot n\sigma^{2} = \frac{\sigma^2}{n}.\end{aligned}
$$

**(d)** If $$\tau\leq \mu_{\text{reg}}$$, then the desired inequality is immediate. Assume therefore that $$\tau>\mu_{\text{reg}}$$. Then

$$
\beta \leq \Pr[A_{n}\geq \tau].
$$

Since $$\tau>\mu_{\text{reg}}$$,

$$
\{A_{n}\geq \tau\} \subseteq \{|A_{n}-\mu_{\text{reg}}|\geq \tau-\mu_{\text{reg}}\}.
$$

By Chebyshev's inequality,

$$
\beta \leq \Pr\left[ |A_{n}-\mu_{\text{reg}}| \geq \tau-\mu_{\text{reg}}\right] \leq \frac{\operatorname{Var}(A_{n})}{(\tau-\mu_{\text{reg}})^{2}}.
$$

Using $$\operatorname{Var}(A_{n})\leq 1/n$$, we get

$$
\beta \leq \frac{1}{n(\tau-\mu_{\text{reg}})^{2}}.
$$

Rearranging gives

$$
\tau-\mu_{\text{reg}}\leq \frac{1}{\sqrt{n\beta}},
$$

and therefore

$$
\tau \leq \mu_{\text{reg}}+ \frac{1}{\sqrt{n\beta}}.
$$

**(e)** From part (b),

$$
\mu_{\mathrm{bd}}= \frac{\sqrt{1+\alpha^{2}\theta}}{\sqrt{2\pi}}, \qquad \mu_{\mathrm{reg}}= \frac{1}{\sqrt{2\pi}}.
$$

Hence

$$
\mu_{\mathrm{bd}}-\mu_{\mathrm{reg}}= \frac{\sqrt{1+\alpha^{2}\theta}-1}{\sqrt{2\pi}}> 0.
$$

Using part (d),

$$
\tau \leq \mu_{\mathrm{reg}}+ \frac{1}{\sqrt{n\beta}}.
$$

Therefore

$$
\Delta_{n} = \mu_{\mathrm{bd}}-\tau \geq \mu_{\mathrm{bd}}- \mu_{\mathrm{reg}}- \frac{1}{\sqrt{n\beta}}.
$$

For large enough $$n$$, the last term is smaller than $$\mu_{\mathrm{bd}}-\mu_{\mathrm{reg}}$$, so

$$
\Delta_{n}>0.
$$

Now apply Chebyshev's inequality to $$A'_{n}$$. Since

$$
\mathbb{E}[A'_{n}]=\mu_{\mathrm{bd}},
$$

we have

$$
\begin{aligned}\Pr[A'_{n}<\tau]&= \Pr[\mu_{\mathrm{bd}}-A'_{n}>\mu_{\mathrm{bd}}-\tau] \\&\leq \Pr[|A'_{n}-\mu_{\mathrm{bd}}|\geq \Delta_{n}] \\&\leq \frac{\operatorname{Var}(A'_n)}{\Delta_n^2}.\end{aligned}
$$

By part (c), with

$$
\sigma^{2}=1+\alpha^{2} \theta,
$$

we have

$$
\operatorname{Var}(A'_{n}) \leq \frac{1+\alpha^{2}\theta}{n}.
$$

Thus

$$
\Pr[A'_{n} < \tau] \leq \frac{1+\alpha^{2}\theta}{n\Delta_{n}^{2}}.
$$

If $$\Delta_{n}$$ is bounded below by a positive constant, then the right-hand side is $$O(1/n)$$. Hence the fraction of backdoored samples classified as $$\texttt{0}$$ decays like $$1/n$$.

:::

\## 16. Learn more

Cryptographic Backdoors:

- ["Backdoor Defense, Learnability and Obfuscation"](https://arxiv.org/abs/2409.03077) (Paul Christiano)
- ["Injecting Undetectable Backdoors in Obfuscated Neural Networks and Language Models"](https://arxiv.org/abs/2406.05660)

---
id: '9b60f7a9-2a3e-4de2-93c3-8c288dcc1024'
title: "E.2.5 Backdoor via random ReLU measurements"
tldr: "A backdoor hidden in a random ReLU network by sampling first-layer weights from a spiked covariance, with the exercise showing backdoored inputs end up above the threshold."
summary_for_tutor: "Section 15 of Iliad worksheet E.2, first part: Definition 15.1 (random ReLU classifier with g_i ~ N(0, I_d), psi_i(x) = ReLU(<g_i, x>), threshold tau), Definition 15.2 (spiked-covariance backdoor g_i ~ N(0, I_d + theta s s^T), secret sparse s, x' = sqrt(1 - alpha^2) x + alpha s, sparse PCA hardness), a key-idea remark and a figure, and Exercise 15.1 parts (a) to (f) (variance, E[ReLU(Z)], concentration, Chebyshev bounds on tau, with parts (d) and (e) marked bonus). Keep the notation mu_reg, mu_bd, A_n, A'_n and Delta_n. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Stephan Wäldchen (Independent)
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/steganography/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 15. Summary: Backdoor via Random ReLU Measurements

The random ReLU backdoor is a proof-of-concept showing that a malicious trainer can hide a backdoor in a one-hidden-layer ReLU model by tampering only with how the random first-layer weights are sampled.

:::callout {title="Definition" tone="blue"}

**Definition 15.1 (Random ReLU classifier).** In the honest version, the model samples random Gaussian weights

$$
g_{i} \sim \mathcal{N}(0,I_{d}),
$$

forms ReLU features

$$
\psi_{i}(x) = \operatorname{ReLU}(\langle g_{i},x\rangle),
$$

and classifies by thresholding their average with a learnable threshold parameter $$\tau$$:

$$
h(x) = \operatorname{\Theta}\left( \frac{1}{n}\sum_{i=1}^{n} \psi_{i}(x) -\tau \right), \quad \text{where}\quad \Theta(x) = \begin{cases}\texttt{0}&\text{if }x\leq 0 \\ \texttt{1}&\text{if }x>0.\end{cases}
$$

:::

:::callout {title="Definition" tone="blue"}

**Definition 15.2 (Spiked-covariance backdoor).** The malicious trainer instead samples the weights from a spiked covariance distribution

$$
g_{i} \sim \mathcal{N}(0, I_{d} + \theta ss^{\top}),
$$

where $$s$$ is a secret sparse vector. This vector $$s$$ acts as the backdoor key. Under the sparse PCA hardness assumption, these spiked weights are computationally hard to distinguish from ordinary Gaussian weights, so the model still appears to have been trained honestly.

To activate the backdoor, the attacker changes an input $$x$$ into

$$
x' = \sqrt{1-\alpha^{2}}x + \alpha s, \quad \text{where}\quad 0\leq\alpha\leq 1.
$$

Because the weights have extra variance in the secret direction $$s$$, we get

$$
\operatorname{Var}(\langle g_{i},x'\rangle) > \operatorname{Var}(\langle g_{i},x\rangle).
$$

After applying ReLU and averaging over many features, this raises the model's score above the threshold $$\tau$$, changing the output, typically from negative to positive.

:::

:::callout {title="Note" tone="blue"}

**Remark (Key idea).** Backdoored samples are shifted in the hidden sparse direction $$s$$, which is also the direction of increased variance in the random ReLU weights. This increases the variance of the scalar products $$\langle g_{i},x\rangle$$. Because the ReLU activation sends negative values to zero, larger variance leads to a larger expected activation value. Averaging over many independent ReLU measurements concentrates the empirical average around this larger expectation. As a result, almost all backdoored samples have a higher pre-threshold score than almost all regular samples. Therefore, if the threshold $$\tau$$ meaningfully separates the regular samples, it will lie below almost all backdoored samples.

:::

![The distribution of the mean ReLU activations of regular samples and backdoored samples. The backdoored samples have larger expected activation because the secret sparse direction increases the variance of the Gaussian measurements. As the number of ReLU measurements grows, both empirical averages concentrate around their means at scale . If the threshold still classifies a fixed fraction of regular samples as positive, then must remain close to , and almost all backdoored samples lie above the threshold.](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-steganography-tikz-d31f8874e8af-25621434.png)

The distribution of the mean ReLU activations of regular samples and backdoored samples. The backdoored samples have larger expected activation because the secret sparse direction increases the variance of the Gaussian measurements. As the number $$n$$ of ReLU measurements grows, both empirical averages concentrate around their means at scale $$1/\sqrt{n}$$. If the threshold $$\tau$$ still classifies a fixed fraction of regular samples as positive, then $$\tau$$ must remain close to $$\mu_{\mathrm{reg}}=1/\sqrt{2\pi}$$, and almost all backdoored samples lie above the threshold.

::::callout {title="Exercise" tone="amber"}
**Exercise 15.1.** We will now show that as the number of random ReLU measurements increases, almost all backdoored samples lie above the threshold.

**(a)** **Backdoor leads to larger Variance:** Assume $$\|x\|_{2}=\|s\|_{2}=1$$ and $$\langle x,s\rangle=0$$. Let $$g \sim \mathcal{N}(0,I_{d}+\theta ss^{\top})$$, and $$x' = \sqrt{1-\alpha^{2}}x+\alpha s$$. Show that

$$
z := \langle g,x\rangle \sim \mathcal{N}(0,1) \quad \text{and}\quad z' := \langle g,x'\rangle \sim \mathcal{N}\bigl(0,1+\alpha^{2}\theta\bigr).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

When $$g \sim \mathcal{N}(0, \Sigma)$$, then $$\operatorname{Var}(\langle g,x\rangle) = x^{\top} \Sigma x$$

:::

**(b)** **Larger Variance leads to larger expected ReLU output:** Let $$Z \sim \mathcal{N}(0,\sigma^{2})$$, and compute

$$
\mathbb{E}[\operatorname{ReLU}(Z)].
$$

Derive the explicit values for the expectations of $$\operatorname{ReLU}(z)$$ and $$\operatorname{ReLU}(z')$$. Conclude that the expected ReLU activation is larger for the backdoored sample whenever $$\alpha > 0$$ and $$\theta > 0$$.

**(c)** **Large Number of Measurements decreases Variance:** Let $$Z\sim \mathcal{N}(0,\sigma^{2})$$. Show that

$$
\operatorname{Var}(\operatorname{ReLU}(Z)) \leq \sigma^{2}.
$$

For independent copies $$Z_{1},\dots,Z_{n}$$, and

$$
A_{n} := \frac{1}{n}\sum_{i=1}^{n} \operatorname{ReLU}(Z_{i}),
$$

calculate $$\mathbb{E} \left( A_{n} \right)$$ and show that

$$
\operatorname{Var}\left( A_{n} \right) \leq \frac{\sigma^{2}}{n}.
$$

**(d)** **Bonus:** Assume that the regular pre-threshold activation $$A_{n}$$ satisfies

$$
\mathbb{E}[A_{n}] = \mu_{\text{reg}}, \qquad \operatorname{Var}(A_{n}) \leq \frac{1}{n}.
$$

Suppose the threshold $$\tau$$ is chosen such that a fixed fraction $$\beta>0$$ of regular samples are classified with label $$\texttt{1}$$, i.e.

$$
\Pr[A_{n} \geq \tau] \geq \beta.
$$

Use Chebyshev's inequality to show that

$$
\tau \leq \mu_{\text{reg}}+\frac{1}{\sqrt{n\beta}}.
$$

**(e)** **Bonus:** Let

$$
A'_{n} := \frac{1}{n}\sum_{i=1}^{n} \operatorname{ReLU}(z'_{i}),
$$

where the $$z'_{i}$$ are independent copies of

$$
z' \sim \mathcal{N}\bigl(0,1+\alpha^{2}\theta\bigr).
$$

Let $$\mu_{\mathrm{bd}}:= \mathbb{E}[A'_{n}]$$. Show that for large enough $$n$$,

$$
\Delta_{n} := \mu_{\mathrm{bd}}-\tau > 0.
$$

Use Chebyshev's inequality to show that

$$
\Pr[A'_{n} < \tau] \leq \frac{1+\alpha^{2}\theta}{n\Delta_{n}^{2}}.
$$

Conclude that, whenever $$\Delta_{n}$$ is bounded below by a positive constant, the fraction of backdoored samples classified as $$\texttt{0}$$ decays like $$1/n$$.

**(f)** **Backdoored Samples always Succeed:**

Given the results of the exercise so far, argue that you that whichever threshold value $$\tau$$ is chosen, you either

1. Classify all normal samples as $$\texttt{0}$$, making the classifier meaningless
2. Classify all backdoored samples as $$\texttt{1}$$.
::::

---
id: 'd72a03aa-8b16-450c-98f7-a6a31cfaa526'
title: "B.4.1 Intent, setup and notation"
tldr: "Two videos on learning dynamics and implicit bias, the learning goals for the day, and the setup of deep linear networks with squared loss, end-to-end matrix W and teacher matrix M."
summary_for_tutor: "This is the intro of worksheet B.4 (training dynamics): two videos, the learning goals (implicit regularization, lazy and rich regimes, loss landscape of deep linear networks, emergent misalignment), Section 1 'Module Intent' and Section 2 'Setup and notation'. It defines DLNs f(x) = W_L ... W_1 x with end-to-end matrix W, squared loss, and in the whitened population limit L(W) = 1/2 ||M - W||_F^2 with teacher M = Sigma_YX and SVD singular values s_1 >= ... >= s_r > 0. Keep the notation W_l, W, M, s_alpha. The sheet advises keeping at least 30 minutes for problem 3. No exercises."
authors:
  - Guillaume Corlouer (Stormglass)
source_url: https://iliad-intensive.org/learning/training-dynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Video
source:: [[../video_transcripts/iliad-the-dumbest-neural-network-worth-studying]]

#### Video
source:: [[../video_transcripts/iliad-uncovering-the-hidden-biases-of-deep-learning]]

#### Text
content::
:::callout {title="What you'll learn" tone="neutral"}

**Motivation**

- Know about some big open questions in learning dynamics
- Understand the concept of implicit regularization
- Know about the different approaches to studying learning dynamics
- Understand the AI safety motivations for learning dynamics
- Know about emergent misalignment as a safety-relevant phenomenon that illustrates the importance of understanding generalization for AI safety

**Geometry and dynamics of deep neural networks**

- Know key results about the loss landscape of deep linear networks (DLNs): critical points are saddles or global minima
- Explain the edge of stability phenomenon
- Understand that gradient flow can be written as NTK-weighted gradient in function space
- DLNs are degenerate and have conserved quantities through gradient flow

**Regimes of learning in deep linear networks**

- Understand the role of initialization, width and depth for the lazy and rich (saddle to saddle) regimes in DLNs
- Know about implicit regularization from non-linearity (neural race reduction)

:::

Use LLMs to help you out when you spend longer than the suggested time (but make sure that you understand). Make sure you keep at least 30 minutes to do problem 3.

**References**: (Saxe et al. 2014), (Achour et al. 2024), (Tu et al. 2024).

\## 1. Module Intent

The goal of this day is to present a toy model perspective on the training dynamics of deep neural networks. The student should learn about the AI safety motivations of studying training dynamics. One motivation is that understanding the implicit biases of training deep neural networks is a central problem behind AI alignment. This is because implicit biases influence the generalization behaviour of a neural network including for example if that neural network will generalize in a helpful or harmful way out of distribution. Another motivation is interpretability. One key lesson of the day is that SGD learns from data in a structured way. For example in deep linear neural networks, under small initialization, it will first learn the features that explain the largest fraction of data covariance.

\## 2. Setup and notation

We study deep linear networks (DLNs) with $$L$$ weight matrices $$W_{1} \in \mathbb{R}^{d_1 \times d_0}, W_{2} \in \mathbb{R}^{d_2 \times d_1}, \ldots, W_{L} \in \mathbb{R}^{d_L \times d_{L-1}}$$. The network computes:

$$
f(x) = W_{L} W_{L-1}\cdots W_{1} \, x =: W x
$$

where $$W = W_{L} \cdots W_{1} \in \mathbb{R}^{d_L \times d_0}$$ is the end-to-end (or "student") matrix. We train on a dataset $$\{(x_{\mu}, y_{\mu})\}_{\mu=1}^{N}$$ with the squared loss:

$$
\mathcal{L}(\theta) = \frac{1}{2N}\sum_{\mu=1}^{N}\|y_{\mu} - f(x_{\mu})\|^{2}
$$

In the population limit $$N \to \infty$$ with whitened inputs $$\Sigma_{X} = I$$, this becomes, up to an additive constant[^1]:

$$
\mathcal{L}(W) = \frac{1}{2}\|M - W\|_{F}^{2}
$$

where $$M = \Sigma_{YX}\Sigma_{X}^{-1}= \Sigma_{YX}$$ is the "teacher" matrix (the OLS solution) with SVD $$M = U \,\text{diag}(s_{1}, \ldots, s_{r}, 0, \ldots, 0)\, V^{\top}$$, and $$s_{1} \geq s_{2} \geq \cdots \geq s_{r} > 0$$.

[^1]: The constant is $$\frac{1}{2}\mathbb{E}\|y - Mx\|^{2}$$, which is the residual of the OLS. It vanishes on realizable data.

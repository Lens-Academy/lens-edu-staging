---
id: '9f9cd19e-6b4c-4d11-9635-675a98948b68'
title: "D.1.2.8 Exact policy evaluation"
tldr: "Solves policy evaluation exactly as a linear system, v = (I - gamma P)^{-1} r, and proves the matrix is invertible using the Neumann series."
summary_for_tutor: "Section 7 of worksheet D.1.2: Exact policy evaluation for a deterministic policy. Definition 7.1 (v^pi, P^pi, R^pi, r^pi), Fact 7.2 (Neumann series), Exercise 7.1 (v^pi = (I - gamma P^pi)^{-1} r^pi) and Exercise 7.2 (I - gamma P^pi is invertible, giving v^pi as a sum of gamma^k (P^pi)^k r^pi). Ends with a remark on stochastic policies and the references. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/reinforcement-learning/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 7. Exact policy evaluation

In Exercise 3.4, we showed that iterating $\mathcal{B}_{\pi}$ converges to $V_{\pi}$; this is the numerical policy evaluation scheme used in the ARENA materials. When the state space is finite and the dynamics $(T, R)$ are known, there is also an *exact* (closed-form) solution: the Bellman equation becomes a linear system that can be solved directly. In this problem we derive that closed form for deterministic policies.

:::callout {title="Definition" tone="blue"}

**Definition 7.1 (Matrix-vector notation for a deterministic policy).** Fix a deterministic policy $\pi$. Treating the value function as a vector in $\mathbb{R}^{|{\mathcal{S}}|}$, define:

- $\mathbf{v}^{\pi} \in \mathbb{R}^{|{\mathcal{S}}|}$ with $\mathbf{v}^{\pi}_{s} := V_{\pi}(s)$,
- $\mathbf{P}^{\pi} \in \mathbb{R}^{|{\mathcal{S}}| \times |{\mathcal{S}}|}$ with $\mathbf{P}^{\pi}_{s,s'}:= T(s' \mid s, \pi(s))$ (the **transition matrix** under $\pi$),
- $\mathbf{R}^{\pi} \in \mathbb{R}^{|{\mathcal{S}}| \times |{\mathcal{S}}|}$ with $\mathbf{R}^{\pi}_{s,s'}:= R(s, \pi(s), s')$ (the **reward matrix**),
- $\mathbf{r}^{\pi} \in \mathbb{R}^{|{\mathcal{S}}|}$ with $\mathbf{r}^{\pi}_{s} := \sum_{s'}\mathbf{P}^{\pi}_{s,s'}\, \mathbf{R}^{\pi}_{s,s'}= \sum_{s'}T(s' \mid s, \pi(s))\, R(s, \pi(s), s')$ (the **expected immediate reward**).

:::

:::callout {title="Note" tone="blue"}

**Fact 7.2 (Neumann series).** Equip $\mathbb{R}^{n \times n}$ with the induced $\infty$-norm

$$
\|\mathbf{A}\|_{\infty} \;:=\; \max_{i} \sum_{j} |\mathbf{A}_{ij}| \qquad \text{(maximum absolute row sum).}
$$

If $\|\mathbf{A}\|_{\infty} < 1$, then $\mathbf{I}- \mathbf{A}$ is invertible, and

$$
(\mathbf{I}- \mathbf{A})^{-1}\;=\; \sum_{k=0}^{\infty}\mathbf{A}^{k}.
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 7.1.** Starting from the Bellman equation (Exercise 1.1) applied to a deterministic policy $\pi$, show that
:::callout {title="Note" tone="blue"}

**Exact Policy Evaluation**

$$
\mathbf{v}^{\pi} \;=\; (\mathbf{I}- \gamma\, \mathbf{P}^{\pi})^{-1}\, \mathbf{r}^{\pi},
$$

:::
assuming $\mathbf{I}- \gamma\, \mathbf{P}^{\pi}$ is invertible (which we prove in Exercise 7.2).

:::callout {title="Hint" tone="neutral" collapse="closed"}

Specialize the Bellman equation to a deterministic policy and write the resulting system of $|{\mathcal{S}}|$ equations in matrix-vector form.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Since $\pi$ is deterministic, $\pi(a \mid s) = \llbracket a = \pi(s) \rrbracket$, and the Bellman equation from Exercise 1.1 collapses the sum over actions:

$$
V_{\pi}(s) \;=\; \sum_{s' \in {\mathcal{S}}}T(s' \mid s, \pi(s))\bigl(R(s, \pi(s), s') + \gamma\, V_{\pi}(s')\bigr).
$$

Splitting the reward and value terms and rewriting with the matrix notation of Definition 7.1:

$$
\begin{aligned}\mathbf{v}^{\pi}_{s}&= \sum_{s'}\mathbf{P}^{\pi}_{s,s'}\, \mathbf{R}^{\pi}_{s,s'}+ \gamma \sum_{s'}\mathbf{P}^{\pi}_{s,s'}\, \mathbf{v}^{\pi}_{s'}= \mathbf{r}^{\pi}_{s} + \gamma\, (\mathbf{P}^{\pi} \mathbf{v}^{\pi})_{s}.\end{aligned}
$$

This holds for every $s$, so in vector form

$$
\mathbf{v}^{\pi} \;=\; \mathbf{r}^{\pi} + \gamma\, \mathbf{P}^{\pi} \mathbf{v}^{\pi} \;\;\Longleftrightarrow\;\; (\mathbf{I}- \gamma\, \mathbf{P}^{\pi})\, \mathbf{v}^{\pi} \;=\; \mathbf{r}^{\pi}.
$$

Assuming $\mathbf{I}- \gamma\, \mathbf{P}^{\pi}$ is invertible, left-multiplying by its inverse gives $\mathbf{v}^{\pi} = (\mathbf{I}- \gamma\, \mathbf{P}^{\pi})^{-1}\, \mathbf{r}^{\pi}$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 7.2.** Prove that $\mathbf{I}- \gamma\, \mathbf{P}^{\pi}$ is invertible for any deterministic policy $\pi$ and any $\gamma \in (0, 1)$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Apply Fact 7.2.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The matrix $\mathbf{P}^{\pi}$ is **row-stochastic**: $\mathbf{P}^{\pi}_{s,s'}\ge 0$ and $\sum_{s'}\mathbf{P}^{\pi}_{s,s'}= \sum_{s'}T(s' \mid s, \pi(s)) = 1$ for every $s$. Therefore

$$
\|\mathbf{P}^{\pi}\|_{\infty} \;=\; \max_{s} \sum_{s'}|\mathbf{P}^{\pi}_{s,s'}| \;=\; \max_{s} \sum_{s'}\mathbf{P}^{\pi}_{s,s'}\;=\; 1,
$$

and so $\|\gamma\, \mathbf{P}^{\pi}\|_{\infty} = \gamma < 1$. By the Neumann series (Fact 7.2), $\mathbf{I}- \gamma\, \mathbf{P}^{\pi}$ is invertible, with

$$
(\mathbf{I}- \gamma\, \mathbf{P}^{\pi})^{-1}\;=\; \sum_{k=0}^{\infty}(\gamma\, \mathbf{P}^{\pi})^{k} \;=\; \sum_{k=0}^{\infty}\gamma^{k}\, (\mathbf{P}^{\pi})^{k}.
$$

Combining with Exercise 7.1,

$$
\mathbf{v}^{\pi} \;=\; \sum_{k=0}^{\infty}\gamma^{k}\, (\mathbf{P}^{\pi})^{k}\, \mathbf{r}^{\pi},
$$

which has a direct interpretation: $(\mathbf{P}^{\pi})^{k} \mathbf{r}^{\pi}$ is the vector of expected rewards exactly $k$ steps into the future under $\pi$, and $\mathbf{v}^{\pi}$ is their discounted sum.

:::

:::callout {title="Note" tone="blue"}

**Remark.** The same derivation extends to stochastic policies by defining $\mathbf{P}^{\pi}_{s,s'}= \sum_{a}\pi(a \mid s)\, T(s' \mid s, a)$ and $\mathbf{r}^{\pi}_{s} = \sum_{a}\pi(a \mid s) \sum_{s'}T(s' \mid s, a)\, R(s, a, s')$. The matrix $\mathbf{P}^{\pi}$ remains row-stochastic, so the argument above applies unchanged.

:::

\## References

M. L. Puterman (1994). *Markov Decision Processes --- Discrete Stochastic Dynamic Programming*. Wiley.

John N. Tsitsiklis (1994). *Asynchronous Stochastic Approximation and Q-Learning*. Machine Learning.

[^1]: Noting that ${\mathcal{S}} \times {\mathcal{A}} \times {\mathcal{S}}$ is a finite set, this implies that the rewards are bounded above by $R_{\text{max}}= \max_{s,a,s'}R(s,a,s')$.

---
id: 'bda44307-f658-42bb-a24b-3fa44b3e29c5'
title: "D.3.2.6 The expectimax form of AIXI"
tldr: "Unrolls the definition of AIXI into the expectimax expression: alternating maximization over actions and mixture expectation over percepts."
summary_for_tutor: "Section 5 of worksheet D.3.2: The expectimax form of AIXI. Exercise 5.1 proves V_xi^{*,m} = (1-gamma) max sum xi ... max sum xi G by backward induction on t, using the expectimax operator with composition (E1) and affine pass-through (E2), then takes m to infinity to get the action pi_xi^*(ae_{<t}) as an argmax. Hint and collapsed solution are given. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. The Expectimax Form of AIXI

We have specified AIXI only implicitly, as the Bayes-optimal policy $\pi_{\xi}^{*}$ (Definition 0.4). We now unroll this definition into the explicit **expectimax** expression: an alternating sequence of maximizations over actions and $\xi$-expectations over percepts.

::::callout {title="Exercise" tone="amber"}
**Exercise 5.1 (Expectimax form of AIXI) [20].** By iterating the finite-horizon Bellman optimality equation (Exercise 2.4), show that

$$
\begin{aligned}V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~=~ (1-\gamma)&\max_{a_t}\sum_{e_t}\xi(e_{t} \mid {\text{\ae}}_{<t}a_{t}) \\&\max_{a_{t+1}}\sum_{e_{t+1}}\xi(e_{t+1}\mid {\text{\ae}}_{<t+1}a_{t+1}) \cdots \\ \cdots&\max_{a_m}\sum_{e_m}\xi(e_{m} \mid {\text{\ae}}_{<m}a_{m}) \,G_{t-1:m}\end{aligned}
$$

and hence, collecting the percept factors with the chain rule (Exercise 0.2) and taking $m \to \infty$ (Exercises 2.5 and 2.7), that AIXI selects the action

$$
\begin{aligned}a_{t}&~=~ \pi_{\xi}^{*}({\text{\ae}}_{<t}) \\&~\in~ {\operatorname*{arg\,max}}_{a_t}\lim_{m\to\infty}\sum_{e_t}\max_{a_{t+1}}\sum_{e_{t+1}}\cdots \max_{a_m}\sum_{e_m}\xi(e_{t:m}\mid {\text{\ae}}_{<t}\, a_{t:m}) \,G_{t-1:m}\end{aligned}
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Prove the first display by backward induction on $t$ from $m$ down to $1$, using the finite-horizon Bellman optimality equation (Exercise 2.4) and the return recursion $G_{t-1:m}= r_{t} + \gamma\, G_{t:m}$ (Definition 0.3). At each step the leftover reward term $(1-\gamma)\, r_{t}$ is constant in the deeper variables; carry it inward using $\sum_{e_k}\xi(e_{k} \mid {\text{\ae}}_{<k}a_{k}) = 1$ and $c + \max(\cdot) = \max(c + \cdot)$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Abbreviate the one-step predictor $\xi_{k} := \xi(e_{k} \mid {\text{\ae}}_{<k}a_{k})$, and write the **expectimax operator** over steps $i, \ldots, j$ as

$$
{\mathop{\overset{\max}{\sum}}\limits}_{i:j}~:=~ \max_{a_i}\sum_{e_i}\xi_{i}\, \max_{a_{i+1}}\sum_{e_{i+1}}\xi_{i+1}\cdots \max_{a_j}\sum_{e_j}\xi_{j},
$$

the alternating "maximize over the action, average over the percept" chain, with the $\xi_{k}$ weights built in; the single step is ${\mathop{\overset{\max}{\sum}}\limits}_{k} := \max_{a_k}\sum_{e_k}\xi_{k}$. Two facts:

- **(E1) Composition:** ${\mathop{\overset{\max}{\sum}}\limits}_{i:j}= {\mathop{\overset{\max}{\sum}}\limits}_{i}\, {\mathop{\overset{\max}{\sum}}\limits}_{i+1:j}$, by nesting the definition.
- **(E2) Affine pass-through:** for any $c \in \mathbb{R}$ and $\lambda \geq 0$ not depending on $(a_{i}, e_{i}, \ldots, a_{j}, e_{j})$,

$$
c + \lambda\, {\mathop{\overset{\max}{\sum}}\limits}_{i:j}X ~=~ {\mathop{\overset{\max}{\sum}}\limits}_{i:j}(c + \lambda X),
$$

since each layer has $\sum_{e_k}\xi_{k} = 1$ (so $\sum_{e_k}\xi_{k}(c+\lambda Y) = c + \lambda \sum_{e_k}\xi_{k} Y$) and $\max_{a}(c + \lambda\, g(a)) = c + \lambda \max_{a} g(a)$ for $\lambda \geq 0$.

We prove by backward induction on $t = m, m-1, \ldots, 1$ that

$$
V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~=~ (1-\gamma)\, {\mathop{\overset{\max}{\sum}}\limits}_{t:m}\, G_{t-1:m}.
$$

*Base case $t = m$.* Here $G_{m-1:m}= r_{m}$ and $V_{\xi}^{*,m}({\text{\ae}}_{1:m}) = 0$ (the return past the horizon is empty, $G_{m:m}= 0$). The Bellman optimality equation (Exercise 2.4) for $\nu = \xi$ gives

$$
V_{\xi}^{*,m}({\text{\ae}}_{<m}) ~=~ \max_{a_m}\sum_{e_m}\xi_{m} \big[(1-\gamma)\, r_{m} + \gamma \cdot 0\big] ~=~ (1-\gamma)\, {\mathop{\overset{\max}{\sum}}\limits}_{m:m}\, G_{m-1:m}.
$$

*Inductive step.* Assume the claim at time $t+1$, i.e. $V_{\xi}^{*,m}({\text{\ae}}_{1:t}) = (1-\gamma)\, {\mathop{\overset{\max}{\sum}}\limits}_{t+1:m}\, G_{t:m}$ for every length-$t$ history (recall ${\text{\ae}}_{<t+1}= {\text{\ae}}_{1:t}$). The Bellman optimality equation (Exercise 2.4) at time $t$ reads

$$
V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~=~ {\mathop{\overset{\max}{\sum}}\limits}_{t} \big[(1-\gamma)\, r_{t} + \gamma\, V_{\xi}^{*,m}({\text{\ae}}_{1:t})\big].
$$

Substituting the inductive hypothesis and pulling out $(1-\gamma)$,

$$
V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~=~ (1-\gamma)\, {\mathop{\overset{\max}{\sum}}\limits}_{t} \big[r_{t} + \gamma\, {\mathop{\overset{\max}{\sum}}\limits}_{t+1:m}\, G_{t:m}\big].
$$

As $r_{t}$ and $\gamma$ do not depend on $(a_{t+1}, e_{t+1}, \ldots, a_{m}, e_{m})$, property (E2) carries them inside the inner operator, and the return recursion $G_{t-1:m}= r_{t} + \gamma\, G_{t:m}$ (Definition 0.3) gives

$$
r_{t} + \gamma\, {\mathop{\overset{\max}{\sum}}\limits}_{t+1:m}\, G_{t:m}~\overset{(E2)}{=}~ {\mathop{\overset{\max}{\sum}}\limits}_{t+1:m}(r_{t} + \gamma\, G_{t:m}) ~=~ {\mathop{\overset{\max}{\sum}}\limits}_{t+1:m}\, G_{t-1:m}.
$$

Recombining the two operators by (E1),

$$
V_{\xi}^{*,m}({\text{\ae}}_{<t}) ~=~ (1-\gamma)\, {\mathop{\overset{\max}{\sum}}\limits}_{t}\, {\mathop{\overset{\max}{\sum}}\limits}_{t+1:m}\, G_{t-1:m}~=~ (1-\gamma)\, {\mathop{\overset{\max}{\sum}}\limits}_{t:m}\, G_{t-1:m},
$$

which expands back into the $\max/\sum$ layers of the first display.

*Infinite horizon and the action.* Taking $m \to \infty$ (Exercises 2.5 and 2.7), $G_{t-1:m}\to G_{\geq t-1}$ and the chain extends indefinitely, so $V_{\xi}^{*}({\text{\ae}}_{<t}) = (1-\gamma)\, {\mathop{\overset{\max}{\sum}}\limits}_{t:\infty}\, G_{\geq t-1}$. Collecting the per-step factors by the chain rule (Exercise 0.2, iterated), $\prod_{k=t}^{m}\xi_{k} = \xi(e_{t:m}\mid {\text{\ae}}_{<t}\, a_{t:m})$. A Bayes-optimal action maximizes this expression; peeling the outer $\max_{a_t}$ off as an ${\operatorname*{arg\,max}}$ and dropping the positive constant $(1-\gamma)$ (which does not move the maximizer) gives the stated action.

:::

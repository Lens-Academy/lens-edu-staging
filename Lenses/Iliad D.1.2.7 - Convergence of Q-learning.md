---
id: 'f5f3b3cf-a258-4049-bca1-214c7882e778'
title: "D.1.2.7 Convergence of Q-learning"
tldr: "States a stochastic approximation theorem for contractions and uses it to prove that Q-learning converges to the optimal action-value function with probability 1."
summary_for_tutor: "Section 6 of Iliad worksheet D.1.2: Convergence of Q-learning. Theorem 6.1 (Tsitsiklis 1994, Theorem 3, stated without proof) with learning-rate and noise conditions, then the Q-learning update. Exercises 6.1-6.6: B on Q-functions is a gamma-contraction, Q* is its unique fixed point, rewrite Q-learning in the form of Theorem 6.1, zero-mean noise, variance bound C(1 + ||Q_t||^2), and the learning-rate conditions sum alpha = infinity and sum alpha^2 < infinity. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/reinforcement-learning/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 6. Convergence of Q-learning

The policy improvement theorem from Section 4 shows that we can in principle find an optimal policy in MDPs. However, it makes the uncomfortable assumption that we know the environment dynamics via the transition kernel $T$. In this problem, we prove that $Q$-learning, which does not make such an assumption, converges to the optimal action-value function, from which one can trivially extract an optimal policy by choosing actions greedily.

\### Stochastic approximation theorem

We will make use of the following stochastic approximation result, which we state without proof:

:::callout {title="Theorem" tone="green"}

**Theorem 6.1 (Stochastic Approximation for Contractions (Tsitsiklis 1994, Theorem 3)).** Let $\mathcal{X}= \{x : I \to \mathbb{R}\}$ be the space of real-valued functions on a finite set $I$, equipped with the sup-norm $\|x\|_{\infty} = \max_{i} |x(i)|$. Let $F : \mathcal{X}\to \mathcal{X}$ be a contraction mapping with factor $\gamma \in [0,1)$ and unique fixed point $x^{*}$.

Fix an initial iterate $x_{0} \in \mathcal{X}$, and for each $t \geq 0$ let $\alpha_{t} : I \to [0,1]$ be a **learning rate** function and $w_{t} : I \to \mathbb{R}$ a random **noise** function (both functions on $I$, one value per coordinate). Consider the stochastic iteration

$$
x_{t+1}(i) = (1 - \alpha_{t}(i))\, x_{t}(i) + \alpha_{t}(i)\bigl[F(x_{t})(i) + w_{t}(i)\bigr] \qquad \text{for all }i \in I,
$$

where updates are applied to a single coordinate $i = i_{t}$ at each step (i.e. $\alpha_{t}(i) = 0$ for $i \neq i_{t}$). Suppose:

**(a)** **(Learning rate)** For each $i \in I$:

$$
\sum_{t=0}^{\infty}\alpha_{t}(i) = \infty, \qquad \sum_{t=0}^{\infty}\alpha_{t}(i)^{2} < \infty, \qquad \alpha_{t}(i) \in [0,1].
$$

**(b)** **(Noise)** For each $i \in I$, conditioned on the history $\mathcal{F}_{t} = \{x_{0}, \alpha_{0}, w_{0}, \alpha_{1}, w_{1}, \ldots, \alpha_{t-1}, w_{t-1}, x_{t}, \alpha_{t}\}$, the noise has zero mean and bounded variance:

$$
\mathbb{E}\big[w_{t}(i) \mid \mathcal{F}_{t}\big] = 0, \qquad \mathbb{E}\big[w_{t}(i)^{2} \mid \mathcal{F}_{t}\big] \le C\bigl(1 + \|x_{t}\|_{\infty}^{2}\bigr)
$$

for some constant $C > 0$.

Then $x_{t}(i) \to x^{*}(i)$ for all $i \in I$, with probability $1$.

:::

*What is stochastic?* The randomness of the iteration is carried by the noise: each $w_{t}(i)$ is a real-valued random variable, and $w_{t}$ is a random element of $\mathbb{R}^{I}$. Consequently, the iterates $x_{1}, x_{2}, \ldots$ are random (they depend on past noise $w_{0}, \ldots, w_{t-1}$), and the learning rates $\alpha_{t}(i)$ may be random as well if they depend on the history—e.g. on which coordinate was just visited. The contraction $F$, its fixed point $x^{*}$, the update rule itself, and the initial iterate $x_{0}$ are all deterministic. The theorem asserts that despite the noise, the random sequence $(x_{t})$ converges pointwise to $x^{*}$ almost surely.

*Remark on "with probability $1$".* The conclusion $x_{t}(i) \to x^{*}(i)$ with probability $1$ (also called **almost sure convergence**) means

$$
P\!\left(\lim_{t \to \infty}x_{t}(i) = x^{*}(i)\right) = 1 \quad \text{for all }i \in I.
$$

In other words, the probability that a run of the stochastic iteration fails to converge to $x^{*}$ is zero.

*Why should we believe this?* It helps to build up the result in three layers of increasing complexity.

**Layer 1: no noise, all coordinates at once.** If $w_{t} = 0$ and $\alpha_{t}(i) = 1$ for all $i$ and $t$, the iteration reduces to $x_{t+1}= F(x_{t})$. This converges to $x^{*}$ by Theorem 3.1.

**Layer 2: noise, but all coordinates at once.** Now suppose we observe $F(x_{t}) + w_{t}$ instead of $F(x_{t})$, and use a decreasing step size:

$$
x_{t+1}= (1 - \alpha_{t})\,x_{t} + \alpha_{t}\bigl[F(x_{t}) + w_{t}\bigr] = x_{t} + \alpha_{t}\bigl[\underbrace{F(x_t) - x_t}_{\text{signal}}+ \underbrace{w_t}_{\text{noise}}\bigr].
$$

The signal $F(x_{t}) - x_{t}$ always points toward $x^{*}$ (this is what the contraction property buys us). The noise $w_{t}$ is mean-zero, so it pushes us in random directions that partially cancel over time. The two conditions on the step size mediate between signal and noise:

- $\sum \alpha_{t} = \infty$ ensures the total step size is large enough to reach $x^{*}$ from any starting point.
- $\sum \alpha_{t}^{2} < \infty$ ensures the noise averages out. Each noise term $w_{t}$ enters the iteration scaled by $\alpha_{t}$, contributing a random displacement of size $\alpha_{t} w_{t}$. Although these displacements are not independent (each depends on the current iterate $x_{t}$), they are mean-zero conditioned on the past. For such sequences, the variance of the cumulative sum is the sum of the individual variances, which is proportional to $\sum \alpha_{t}^{2}$. Since this is finite, the total random drift converges and cannot overwhelm the steady pull of the signal toward $x^{*}$.

The signal accumulates coherently (always pulling toward $x^{*}$), while the noise averages out.

**Layer 3: one coordinate at a time.** The iteration updates only one coordinate $i = i_{t}$ per step, while the others stay frozen. This makes the analysis more difficult since the target $F(x_{t})(i)$ depends on all coordinates, including stale ones. The condition $\sum_{t} \alpha_{t}(i) = \infty$ for each $i$ ensures no coordinate is permanently neglected, and the contraction property of $F$ provides enough global coupling to prevent coordinates from drifting apart. Making this rigorous is the main technical content of the proof.

\### The problem

Consider the following generalization of the Q-learning update from the ARENA materials, now with a time-varying learning rate $\alpha_{t} > 0$: given a current estimate $Q_{t} : {\mathcal{S}} \times {\mathcal{A}} \to \mathbb{R}$ and an observed transition $(s_{t}, a_{t}, r_{t+1}, s_{t+1})$ where $s_{t+1}\sim T(\cdot \mid s_{t}, a_{t})$ and $r_{t+1}= R(s_{t}, a_{t}, s_{t+1})$, the update is

:::callout {title="Note" tone="blue"}

**Q-Learning Update**

$$
Q_{t+1}(s_{t}, a_{t}) = Q_{t}(s_{t}, a_{t}) + \alpha_{t}\bigl(r_{t+1}+ \gamma \max_{a' \in {\mathcal{A}}}Q_{t}(s_{t+1}, a') - Q_{t}(s_{t}, a_{t})\bigr),
$$

:::
with $Q_{t+1}(s,a) = Q_{t}(s,a)$ for all $(s,a) \neq (s_{t}, a_{t})$. We will show that, under appropriate conditions, Q-learning converges to the optimal action-value function $Q^{*}$.

Let $\mathcal{Q}= \{Q : {\mathcal{S}} \times {\mathcal{A}} \to \mathbb{R}\}$ denote the space of action-value functions, equipped with the sup-norm $\|Q\|_{\infty} = \max_{s,a}|Q(s,a)|$.

::::callout {title="Exercise" tone="amber"}
**Exercise 6.1.** Overloading the notation from Definition 3.2, define the **Bellman optimality operator** on action-value functions, $\mathcal{B}: \mathcal{Q}\to \mathcal{Q}$, by
:::callout {title="Note" tone="blue"}

**Bellman Q-Operator**

$$
(\mathcal{B}Q)(s,a) \coloneqq \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl[R(s,a,s') + \gamma \max_{a' \in {\mathcal{A}}}Q(s', a')\bigr].
$$

:::
(Here $\mathcal{B}$ takes a $Q$-function to a $Q$-function, whereas the earlier $\mathcal{B}$ in Definition 3.2 takes a $V$-function to a $V$-function — whether $\mathcal{B}$ denotes the $V$- or $Q$-version is always clear from its argument.) Show that $\mathcal{B}$ is a $\gamma$-contraction on $(\mathcal{Q}, \|\cdot\|_{\infty})$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

This is similar to the proof of Exercise 3.2.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Fix $Q, Q' \in \mathcal{Q}$ and $(s,a) \in {\mathcal{S}} \times {\mathcal{A}}$. By the inequality from Exercise 3.1 (applied at each $s'$) and the triangle inequality:

$$
\begin{aligned}&\bigl|(\mathcal{B}Q)(s,a) - (\mathcal{B}Q')(s,a)\bigr| \\&\quad= \left|\sum_{s'}T(s' \mid s,a)\,\gamma\Bigl(\max_{a'}Q(s',a') - \max_{a'}Q'(s',a')\Bigr)\right| \\&\quad\le \sum_{s'}T(s' \mid s,a)\,\gamma\,\max_{a'}\bigl|Q(s',a') - Q'(s',a')\bigr| \\&\quad\le \sum_{s'}T(s' \mid s,a)\,\gamma\,\max_{a', s''}\bigl|Q(s'',a') - Q'(s'',a')\bigr| \\&\quad\le \gamma\,\|Q - Q'\|_{\infty}.\end{aligned}
$$

Taking the maximum over $(s,a)$ gives $\|\mathcal{B}Q - \mathcal{B}Q'\|_{\infty} \le \gamma\,\|Q - Q'\|_{\infty}$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 6.2.** Define $Q^{*} \coloneqq Q_{\pi^*}$, the action-value function of the optimal policy $\pi^{*}$ from Section 3. We now show Bellman optimality equations and their consequences.

**(a)** Show that $Q^{*}(s,a) = \sum_{s' \in {\mathcal{S}}}T(s' \mid s, a)\bigl[R(s,a,s') + \gamma\, V^{*}(s')\bigr]$.

**(b)** Show that $V^{*}(s) = \max_{a \in {\mathcal{A}}}Q^{*}(s,a)$.

**(c)** Conclude that $Q^{*}$ is the unique fixed point of $\mathcal{B}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** By Exercise 1.2(b) applied to $\pi^{*}$:

$$
Q_{\pi^*}(s,a) = \sum_{s' \in {\mathcal{S}}}T(s' \mid s,a)\bigl[R(s,a,s') + \gamma\, V_{\pi^*}(s')\bigr].
$$

By Exercise 3.6, $V_{\pi^*}= V^{*}$. Substituting gives the result.

**(b)** By Exercise 1.2(a), $V_{\pi^*}(s) = \sum_{a}\pi^{*}(a \mid s)\, Q_{\pi^*}(s,a)$. Since $\pi^{*}$ is the greedy policy with respect to $V^{*}$ (Exercises 3.5 and 3.6), it is deterministic and selects $\pi^{*}(s) \in {\operatorname*{arg\,max}}_{a} \sum_{s'}T(s' \mid s,a)[R(s,a,s') + \gamma\, V^{*}(s')]$. By Exercise 6.2(a), the inner expression equals $Q^{*}(s,a)$, so $\pi^{*}(s) \in {\operatorname*{arg\,max}}_{a} Q^{*}(s,a)$. Since $\pi^{*}$ is deterministic, $V^{*}(s) = V_{\pi^*}(s) = Q_{\pi^*}(s, \pi^{*}(s)) = Q^{*}(s, \pi^{*}(s)) = \max_{a} Q^{*}(s,a)$.

**(c)** Substituting Exercise 6.2(b) into Exercise 6.2(a):

$$
Q^{*}(s,a) = \sum_{s'}T(s' \mid s,a)\bigl[R(s,a,s') + \gamma \max_{a'}Q^{*}(s',a')\bigr] = (\mathcal{B}Q^{*})(s,a).
$$

So $Q^{*}$ is a fixed point of $\mathcal{B}$. Uniqueness follows from Exercise 6.1 and Theorem 3.1.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 6.3.** Rewrite the Q-learning update in the form of Theorem 6.1:

$$
x_{t+1}(i) = (1 - \alpha_{t}(i))\, x_{t}(i) + \alpha_{t}(i)\bigl[F(x_{t})(i) + w_{t}(i)\bigr].
$$

Specifically, identify the index set $I$, the mapping $F$, the iterates $x_{t}$, and the learning rates $\alpha_{t}(i)$. Then give an explicit expression for the noise $w_{t}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The identifications are:

- Index set: $I = {\mathcal{S}} \times {\mathcal{A}}$.
- Iterates: $x_{t} = Q_{t}$.
- Contraction: $F = \mathcal{B}$, with fixed point $x^{*} = Q^{*}$ (Exercise 6.2).
- Learning rates: $\alpha_{t}(s,a) = \alpha_{t} \cdot \llbracket (s,a) = (s_{t}, a_{t}) \rrbracket$.

With these identifications, the Q-learning update becomes

$$
Q_{t+1}(s,a) = (1 - \alpha_{t}(s,a))\, Q_{t}(s,a) + \alpha_{t}(s,a)\bigl[(\mathcal{B}Q_{t})(s,a) + w_{t}(s,a)\bigr],
$$

where the noise at the updated coordinate is

$$
w_{t}(s_{t}, a_{t}) = R(s_{t}, a_{t}, s_{t+1}) + \gamma \max_{a'}Q_{t}(s_{t+1}, a') - (\mathcal{B}Q_{t})(s_{t}, a_{t}),
$$

i.e. the difference between the sampled target (using the single transition $s_{t+1}$) and its expectation over all possible transitions. For $(s,a) \neq (s_{t}, a_{t})$, we set $w_{t}(s,a) = 0$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 6.4.** Show that the noise satisfies $\mathbb{E}[w_{t}(s,a) \mid \mathcal{F}_{t}] = 0$ for all $(s,a) \in {\mathcal{S}} \times {\mathcal{A}}$, where $\mathcal{F}_{t}$ denotes the history up to time $t$ as in Theorem 6.1.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Conditioned on $\mathcal{F}_{t}$, the quantities $Q_{t}$, $s_{t}$, and $a_{t}$ are all determined. What is the only remaining source of randomness?

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Conditioned on $\mathcal{F}_{t}$, the quantities $Q_{t}$, $s_{t}$, $a_{t}$ are all determined. The only remaining randomness is in $s_{t+1}\sim T(\cdot \mid s_{t}, a_{t})$. Therefore:

$$
\begin{aligned}&\mathbb{E}[w_{t}(s_{t}, a_{t}) \mid \mathcal{F}_{t}] \\&\quad= \mathbb{E}\bigl[R(s_{t}, a_{t}, s_{t+1}) + \gamma \max_{a'}Q_{t}(s_{t+1}, a') \mid \mathcal{F}_{t}\bigr] - (\mathcal{B}Q_{t})(s_{t}, a_{t}) \\&\quad= \sum_{s'}T(s' \mid s_{t}, a_{t})\bigl[R(s_{t}, a_{t}, s') + \gamma \max_{a'}Q_{t}(s', a')\bigr] - (\mathcal{B}Q_{t})(s_{t}, a_{t}) \\&\quad= (\mathcal{B}Q_{t})(s_{t}, a_{t}) - (\mathcal{B}Q_{t})(s_{t}, a_{t}) = 0.\end{aligned}
$$

For $(s,a) \neq (s_{t}, a_{t})$, we have $w_{t}(s,a) = 0$ by definition, so $\mathbb{E}[w_{t}(s,a) \mid \mathcal{F}_{t}] = 0$ trivially.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 6.5.** Assume $|R(s,a,s')| \le R_{\max}$ for all $s, a, s'$. Show that there exists a constant $C > 0$ (depending only on $R_{\max}$ and $\gamma$) such that

$$
\mathbb{E}\bigl[w_{t}(s,a)^{2} \mid \mathcal{F}_{t}\bigr] \le C\bigl(1 + \|Q_{t}\|_{\infty}^{2}\bigr).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

First show that $|w_{t}(s_{t}, a_{t})| \le 2(R_{\max}+ \gamma\, \|Q_{t}\|_{\infty})$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*Step 1: a pointwise bound on $w_{t}$.* Using $|R(s_{t}, a_{t}, s_{t+1})| \le R_{\max}$ and $|\max_{a'}Q_{t}(s_{t+1}, a')| \le \|Q_{t}\|_{\infty}$, the sampled target satisfies

$$
\bigl|R(s_{t}, a_{t}, s_{t+1}) + \gamma \max_{a'}Q_{t}(s_{t+1}, a')\bigr| \le R_{\max}+ \gamma\,\|Q_{t}\|_{\infty}.
$$

The same bound holds for $|(\mathcal{B}Q_{t})(s_{t}, a_{t})|$, since it is a convex combination (over $s'$) of terms each bounded by $R_{\max}+ \gamma\,\|Q_{t}\|_{\infty}$. By the triangle inequality:

$$
|w_{t}(s_{t}, a_{t})| \;\le\; 2\bigl(R_{\max}+ \gamma\,\|Q_{t}\|_{\infty}\bigr).
$$

This bound holds for *every* realization of $s_{t+1}$, not just in expectation.

*Step 2: passing to the conditional second moment.* Squaring the pointwise bound,

$$
w_{t}(s_{t}, a_{t})^{2} \;\le\; 4\bigl(R_{\max}+ \gamma\,\|Q_{t}\|_{\infty}\bigr)^{2} \quad \text{a.s.}
$$

Taking conditional expectation of both sides given $\mathcal{F}_{t}$ preserves the inequality (monotonicity of conditional expectation):

$$
\mathbb{E}\!\left[w_{t}(s_{t}, a_{t})^{2} \mid \mathcal{F}_{t}\right] \;\le\; \mathbb{E}\!\left[\,4(R_{\max}+ \gamma\,\|Q_{t}\|_{\infty})^{2} \mid \mathcal{F}_{t}\right].
$$

Now we simplify the right-hand side. It is a function of $Q_{t}$ (and the constants $R_{\max}, \gamma$), and $Q_{t}$ is determined once we condition on $\mathcal{F}_{t}$ (recall $\mathcal{F}_{t}$ records $Q_{0}, Q_{1}, \ldots, Q_{t}$). So the right-hand side is **$\mathcal{F}_{t}$-measurable**: given the history, it is a fixed real number, not random. Conditional expectation acts as the identity on $\mathcal{F}_{t}$-measurable quantities — i.e. $\mathbb{E}[Y \mid \mathcal{F}_{t}] = Y$ when $Y$ is $\mathcal{F}_{t}$-measurable — so

$$
\mathbb{E}\!\left[\,4(R_{\max}+ \gamma\,\|Q_{t}\|_{\infty})^{2} \mid \mathcal{F}_{t}\right] \;=\; 4\bigl(R_{\max}+ \gamma\,\|Q_{t}\|_{\infty}\bigr)^{2}.
$$

Combining,

$$
\mathbb{E}\!\left[w_{t}(s_{t}, a_{t})^{2} \mid \mathcal{F}_{t}\right] \;\le\; 4\bigl(R_{\max}+ \gamma\,\|Q_{t}\|_{\infty}\bigr)^{2}.
$$

*Step 3: putting it in the required form.* We want a constant $C$ such that the right-hand side is bounded by $C(1 + \|Q_{t}\|_{\infty}^{2})$. Applying $(a+b)^{2} \le 2(a^{2} + b^{2})$ with $a = R_{\max}$, $b = \gamma\,\|Q_{t}\|_{\infty}$:

$$
\begin{aligned}4\bigl(R_{\max}+ \gamma\,\|Q_{t}\|_{\infty}\bigr)^{2}&\le 8\bigl(R_{\max}^{2} + \gamma^{2}\,\|Q_{t}\|_{\infty}^{2}\bigr) \\&\le 8\max\!\bigl(R_{\max}^{2},\, \gamma^{2}\bigr)\bigl(1 + \|Q_{t}\|_{\infty}^{2}\bigr).\end{aligned}
$$

So $C = 8\max(R_{\max}^{2}, \gamma^{2})$ works. For $(s,a) \neq (s_{t}, a_{t})$, we have $w_{t}(s,a) = 0$, so the bound holds trivially with the same $C$.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 6.6.** Conclude: state the conditions on the learning rate schedule and the exploration policy under which Q-learning converges, i.e. $Q_{t} \to Q^{*}$ with probability $1$.
:::callout {title="Note" tone="blue"}

**Remark.** The ARENA implementation uses a constant learning rate $\alpha$, which does not satisfy $\sum_{t} \alpha_{t}(s,a)^{2} < \infty$. In practice, constant-rate Q-learning does not converge exactly but oscillates in a neighbourhood of $Q^{*}$ whose size shrinks with $\alpha$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercises 6.1–6.5, the Q-learning iteration satisfies all the hypotheses of Theorem 6.1, provided the learning rate conditions hold: for each $(s,a) \in {\mathcal{S}} \times {\mathcal{A}}$,

$$
\sum_{t=0}^{\infty}\alpha_{t}(s,a) = \infty, \qquad \sum_{t=0}^{\infty}\alpha_{t}(s,a)^{2} < \infty, \qquad \alpha_{t}(s,a) \in [0,1].
$$

Under these conditions, Theorem 6.1 gives $Q_{t} \to Q^{*}$ with probability $1$.

Note that the first condition already implies that each state-action pair $(s,a)$ must be visited infinitely often. A concrete way to achieve all three conditions is to use an exploration policy that visits every $(s,a)$ infinitely often together with a per-coordinate learning rate $\alpha_{t}(s,a) = 1/n_{t}(s,a)$, where $n_{t}(s,a)$ counts the number of visits to $(s,a)$ up to time $t$. This satisfies $\sum \alpha_{t}(s,a) = \sum_{k=1}^{\infty} 1/k = \infty$ and $\sum \alpha_{t}(s,a)^{2} = \sum_{k=1}^{\infty} 1/k^{2} < \infty$.

:::

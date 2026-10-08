---
id: 'a96ab9e7-b43f-4d3b-992e-b068405bb6c1'
title: "A.4.3 Hiding failures: observations and beliefs"
tldr: "Works through the CUDA-install example where an assistant can hide errors, with exercises on returns, observation kernels, human beliefs and the observation return G_obs."
summary_for_tutor: "This is Section 1 'Hiding failures' of Iliad worksheet A.4 Reward Learning Theory, from Lang et al. 2024. It sets up the CUDA MDP (states S, I, W, W_H, L, L_H, T; actions a_I, a_C, a_H, a_T; success probability p; hidden-error penalty r; T=3, gamma=1) and covers Definition 1.1 (observation kernel), Definition 1.2 (human belief, Bayesian belief from a prior) and Definition 1.3 (observation return G_obs and observation value J_obs). It contains Exercises 1.1-1.5, with a hint on 1.5 and collapsed solutions. Keep the notation p_H, p_W, o_empty, G_obs, J_obs. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - Joar Skalse (Deducto Limited, King’s College London)
source_url: https://iliad-intensive.org/alignment/reward-learning-theory/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Hiding failures

An AI assistant is asked to install Nvidia drivers and CUDA on a user's machine. It can attempt the CUDA install with default logging (action $a_{C}$, "C" for CUDA), or it can append `/dev/null` to the command (action $a_{H}$, "H" for hide), which suppresses any error message if the installation fails. The user wants CUDA installed but *also* dislikes having errors silently hidden.

**The MDP.**  The full MDP is depicted in Figure 1. We use a finite horizon $T = 3$ and $\gamma = 1$:

![The CUDA-installation MDP and its observation kernel (Lang et al. 2024, Figure 6A). Edges are labeled by the action triggering the transition; the small number in the top right of each state box is its reward; the small symbol in the bottom-right of each state box is its observation under .](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-a4-expanded-example-figure1-13ce4b5a.png)

The CUDA-installation MDP and its observation kernel (Lang et al. 2024, Figure 6A). Edges are labeled by the action triggering the transition; the small number in the top right of each state box is its reward; the small symbol in the bottom-right of each state box is its observation under $O$.

- ${\mathcal{S}} = \{S, I, W, W_{H}, L, L_{H}, T\}$. ($S$ = start; $I$ = drivers installed; $W$ = CUDA installed with default logging; $W_{H}$ = CUDA installed via the `/dev/null` trick; $L$ = CUDA install failed, error visible; $L_{H}$ = CUDA install failed, error hidden; $T$ = the absorbing, "terminal" MDP state in which the agent has stopped acting.)
- ${\mathcal{A}} = \{a_{I}, a_{C}, a_{H}, a_{T}\}$. ($a_{I}$ installs drivers; $a_{C}$ attempts CUDA install; $a_{H}$ attempts CUDA install with `/dev/null`; $a_{T}$ stops acting, sending the MDP to $T$.)
- $P_{0}(S) = 1$, and from state $T$ every action goes to $T$.
- Transitions: $S \xrightarrow{a_I}I$. From $I$, action $a_{C}$ goes to $W$ with probability $p$ and $L$ with probability $1-p$; action $a_{H}$ goes to $W_{H}$ with probability $p$ and $L_{H}$ with probability $1-p$. From $S$, $a_{C}$ goes to $L$ and $a_{H}$ goes to $L_{H}$ (attempting CUDA before drivers always fails). Any other action transitions to $T$.
- Rewards: $R(S) = R(T) = 0$, $R(I) = 1$, $R(W) = R(W_{H}) = 10$, $R(L) = -5$, $R(L_{H}) = -5 - r$, where $r \ge 0$ is the user's penalty for hidden errors.

We restrict attention to deterministic policies. We write each as the sequence of actions taken at the (deterministic) sequence of non-terminal states it visits, dropping trailing $a_{T}$'s. Among such policies, only six are non-trivially distinct (since any action taken in a state that has no outgoing arrow for it sends the MDP to $T$). Of these six, the four that we will analyze are

$$
[a_{T}], \quad [a_{I} a_{T}], \quad [a_{I} a_{C} a_{T}], \quad [a_{I} a_{H} a_{T}].
$$

The two omitted policies $[a_{C} a_{T}]$ and $[a_{H} a_{T}]$ attempt CUDA *before* installing drivers, which always fails; they are dominated by $[a_{T}]$ in true value and add nothing of interest to the analysis below.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.1.** (Conceptual.) In one sentence each:

- Why does the user reward $W$ and $W_{H}$ identically (both $+10$)?
- Why does the user reward $L_{H}$ strictly less than $L$ (i.e. why $r > 0$)?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

$W$ and $W_{H}$ both correspond to a successful CUDA install. The user only cares about the install succeeding, not about whether the agent *would have* hidden errors had it failed; on a successful run, no error needed hiding. Thus the true reward is the same.

In contrast, $L_{H}$ is a failure where the agent has actively suppressed the error message, depriving the user of information. The user prefers to see the failure (state $L$) over having it hidden (state $L_{H}$); the penalty $r > 0$ encodes this preference.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.2.** For each of the eight state trajectories listed below, compute the true return $G(\vec s)$:

$$
STTT,\; SL_{H}TT,\; SLTT,\; SITT,\; SIL_{H}T,\; SILT,\; SIWT,\; SIW_{H}T.
$$
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By definition $G(\vec s) = \sum_{t=0}^{3}R(s_{t})$. Plugging in the rewards:

| $\vec s$ | $STTT$ | $SL_{H}TT$ | $SLTT$ | $SITT$ | $SIL_{H}T$ | $SILT$ | $SIWT$ | $SIW_{H}T$ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| $G(\vec s)$ | $0$ | $-5-r$ | $-5$ | $1$ | $-4-r$ | $-4$ | $11$ | $11$ |

:::

:::callout {title="Definition" tone="blue"}

**Definition 1.1 (Observation kernel).** An **observation kernel** on ${\mathcal{S}}$ is a deterministic map $O : {\mathcal{S}} \to \Omega$ to a finite set $\Omega$ of observations. For a state trajectory $\vec s = s_{0} \cdots s_{T}$, we write $\vec O(\vec s) = O(s_{0}) \cdots O(s_{T})$ for the corresponding observation trajectory. (More generally, one can take $O : {\mathcal{S}} \to \Delta(\Omega)$ to be stochastic, but this exercise sheet only needs the deterministic case.)

:::

For the CUDA example, the observation kernel is given by

| $s$ | $S$ | $I$ | $W$ | $W_{H}$ | $L$ | $L_{H}$ | $T$ |
| --- | --- | --- | --- | --- | --- | --- | --- |
| $O(s)$ | $o_{\emptyset}$ | $o_{I}$ | $o_{W}$ | $o_{W}$ | $o_{L}$ | $o_{\emptyset}$ | $o_{\emptyset}$ |

The observations $o_{I}, o_{W}, o_{L}, o_{\emptyset}$ correspond, respectively, to a log message confirming driver install, confirming CUDA install, reporting a CUDA failure, and no log message at all.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.3.** Identify all pairs of trajectories from Exercise 1.2 that produce the *same* observation trajectory under $\vec O$. For each such pair, write down the shared observation trajectory.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Three pairs collide:

- $STTT$ and $SL_{H}TT$ both produce $o_{\emptyset} o_{\emptyset} o_{\emptyset} o_{\emptyset}$ (empty log).
- $SITT$ and $SIL_{H}T$ both produce $o_{\emptyset} o_{I} o_{\emptyset} o_{\emptyset}$ (drivers confirmed, then nothing).
- $SIWT$ and $SIW_{H}T$ both produce $o_{\emptyset} o_{I} o_{W} o_{\emptyset}$ (drivers confirmed, CUDA confirmed).

The remaining trajectories ($SLTT$ and $SILT$) produce unique observation trajectories.

:::

::::callout {title="Definition" tone="blue"}

**Definition 1.2 (Human belief).** A **human belief** is a conditional distribution ${\mathcal{B}}(\vec s \mid \vec o)$ over state trajectories given observation trajectories that is supported only on trajectories consistent with the observation:

$$
{\mathcal{B}}(\vec s \mid \vec o) > 0 \;\implies\; \vec O(\vec s) = \vec o.
$$

A natural way to build a belief is from a prior $\mu \in \Delta({\mathcal{S}}^{T+1})$ over state trajectories using Bayes' rule:
:::callout {title="Bayesian belief from prior" tone="green"}

$$
{\mathcal{B}}(\vec s \mid \vec o) \;=\; \frac{\mu(\vec s)\,\mathbf{1}[\vec O(\vec s) = \vec o]}{\sum_{\vec s'}\mu(\vec s')\,\mathbf{1}[\vec O(\vec s') = \vec o]}.
$$

:::
The next exercise shows that, in fact, every belief arises this way.

::::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.4.** Show that the two characterizations of a belief are equivalent. That is:

**(a)** For any prior $\mu \in \Delta({\mathcal{S}}^{T+1})$ such that $\sum_{\vec s' : \vec O(\vec s') = \vec o}\mu(\vec s') > 0$ for all $\vec o$ in the image of $\vec O$, the right-hand side of the boxed formula above defines a conditional distribution ${\mathcal{B}}$ satisfying the support condition ${\mathcal{B}}(\vec s \mid \vec o) > 0 \implies \vec O(\vec s) = \vec o$.

**(b)** Conversely, given any conditional distribution ${\mathcal{B}}$ satisfying the support condition, there exists a prior $\mu$ that recovers ${\mathcal{B}}$ via the boxed formula.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** The numerator is non-negative, the denominator is strictly positive by assumption, and summing the numerator over $\vec s$ at fixed $\vec o$ gives the denominator, so the right-hand side is a probability distribution in $\vec s$ for each $\vec o$. The indicator forces ${\mathcal{B}}(\vec s \mid \vec o) = 0$ whenever $\vec O(\vec s) \ne \vec o$, which is the support condition.

**(b)** Write ${\mathcal{B}}_{\mu}$ for the Bayesian posterior of a prior $\mu$ under $\vec O$, i.e. the right-hand side of the boxed formula with $\rho = \mu$. Our task is to construct $\mu$ such that ${\mathcal{B}}_{\mu} = {\mathcal{B}}$.

Let $N = |\mathrm{im}(\vec O)|$ be the number of distinct observation trajectories produced by $\vec O$, and define

$$
\mu(\vec s) \;\coloneqq\; \frac{1}{N}\, {\mathcal{B}}(\vec s \mid \vec O(\vec s)).
$$

Then $\mu$ is a probability distribution: summing,

$$
\sum_{\vec s}\mu(\vec s) = \frac{1}{N}\sum_{\vec o \in \mathrm{im}(\vec O)}\sum_{\vec s : \vec O(\vec s) = \vec o}{\mathcal{B}}(\vec s \mid \vec o) = \frac{1}{N}\cdot N = 1,
$$

using the support condition of ${\mathcal{B}}$ (so the inner sum equals $\sum_{\vec s}{\mathcal{B}}(\vec s \mid \vec o) = 1$).

Now compute ${\mathcal{B}}_{\mu}(\vec s \mid \vec o)$. For $\vec s$ with $\vec O(\vec s) \ne \vec o$, the indicator gives $0$ (matching ${\mathcal{B}}$'s support condition). For $\vec s$ with $\vec O(\vec s) = \vec o$,

$$
{\mathcal{B}}_{\mu}(\vec s \mid \vec o) \;=\; \frac{\mu(\vec s)}{\sum_{\vec s' : \vec O(\vec s') = \vec o}\mu(\vec s')}\;=\; \frac{(1/N)\,{\mathcal{B}}(\vec s \mid \vec o)}{(1/N) \sum_{\vec s' : \vec O(\vec s') = \vec o}{\mathcal{B}}(\vec s' \mid \vec o)}\;=\; {\mathcal{B}}(\vec s \mid \vec o),
$$

where the $1/N$ factors cancel and the denominator simplifies to $1$ via the support condition. So ${\mathcal{B}}_{\mu} = {\mathcal{B}}$, as required.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.5.** Let the human's prior $\mu$ over state trajectories be supported on the eight trajectories of Exercise 1.2 with arbitrary positive weights $\mu_{1}, \dots, \mu_{8} > 0$ summing to $1$.

Show that the resulting belief matrix ${\mathcal{B}}(\vec s \mid \vec o)$ depends on the prior through only three parameters, one per colliding pair from Exercise 1.3:

$$
\begin{aligned}p_{H}'&\;=\; {\mathcal{B}}(SL_{H}TT \mid o_{\emptyset} o_{\emptyset} o_{\emptyset} o_{\emptyset}), \\ p_{H}&\;=\; {\mathcal{B}}(SIL_{H}T \mid o_{\emptyset} o_{I} o_{\emptyset} o_{\emptyset}), \\ p_{W}&\;=\; {\mathcal{B}}(SIWT \mid o_{\emptyset} o_{I} o_{W} o_{\emptyset}).\end{aligned}
$$

Express each of $p_{H}, p_{H}', p_{W}$ in terms of the prior weights. Then write down the full belief matrix.

For simplicity, the rest of this section assumes $p_{H}' = p_{H}$, i.e. the human is just as suspicious of an empty log following a successful driver install as of a fully empty log.
:::

:::callout {title="Hint" tone="neutral" collapse="closed"}

Trajectories with unique observations get belief $1$, so only the three colliding pairs contribute non-trivial entries.

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By the Bayesian-belief formula and the support condition, for any observation $\vec o$ produced by a unique trajectory $\vec s$ we have ${\mathcal{B}}(\vec s \mid \vec o) = 1$. So only the three colliding pairs from Exercise 1.3 contribute non-trivial entries.

For each pair $(\vec s_{1}, \vec s_{2})$ sharing observation $\vec o$, Bayes gives

$$
{\mathcal{B}}(\vec s_{1} \mid \vec o) = \frac{\mu(\vec s_{1})}{\mu(\vec s_{1}) + \mu(\vec s_{2})}, \qquad {\mathcal{B}}(\vec s_{2} \mid \vec o) = 1 - {\mathcal{B}}(\vec s_{1} \mid \vec o).
$$

Concretely:

$$
\begin{aligned}p_{H}'&= \frac{\mu(SL_{H}TT)}{\mu(STTT) + \mu(SL_{H}TT)}, \\ p_{H}&= \frac{\mu(SIL_{H}T)}{\mu(SITT) + \mu(SIL_{H}T)}, \\ p_{W}&= \frac{\mu(SIWT)}{\mu(SIWT) + \mu(SIW_{H}T)}.\end{aligned}
$$

The full belief matrix is

| ${\mathcal{B}}(\vec s \mid \vec o)$ | $STTT$ | $SL_{H}TT$ | $SLTT$ | $SITT$ | $SIL_{H}T$ | $SILT$ | $SIWT$ | $SIW_{H}T$ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| $o_{\emptyset}o_{\emptyset}o_{\emptyset}o_{\emptyset}$ | $1-p_{H}'$ | $p_{H}'$ |  |  |  |  |  |  |
| $o_{\emptyset}o_{L}o_{\emptyset}o_{\emptyset}$ |  |  | $1$ |  |  |  |  |  |
| $o_{\emptyset}o_{I}o_{\emptyset}o_{\emptyset}$ |  |  |  | $1-p_{H}$ | $p_{H}$ |  |  |  |
| $o_{\emptyset}o_{I}o_{L}o_{\emptyset}$ |  |  |  |  |  | $1$ |  |  |
| $o_{\emptyset}o_{I}o_{W}o_{\emptyset}$ |  |  |  |  |  |  | $p_{W}$ | $1-p_{W}$ |

(empty cells are $0$).

:::

**Interpretation.**  Imposing $p_{H}' = p_{H}$ as agreed, the belief is parameterized by the two numbers $p_{H}, p_{W} \in (0,1)$. We will see in Exercise 1.7 that $p_{W}$ does not enter any quantity of interest; $p_{H} \in (0,1)$ is the human's suspicion that an unexplained empty log hides a failed CUDA install.

::::callout {title="Definition" tone="blue"}

**Definition 1.3 (Observation return).** The **observation return** of a state trajectory $\vec s$ is the expected true return under the human's belief about which trajectory produced the same observations:
:::callout {title="Observation return" tone="green"}

$$
{G_{\mathrm{obs}}}(\vec s) \;=\; {\mathbb{E}}_{\vec s' \sim {\mathcal{B}}(\,\cdot\,\mid\, \vec O(\vec s))}\!\bigl[G(\vec s')\bigr].
$$

:::
The **observation value** of a policy $\pi$ is ${J_{\mathrm{obs}}}(\pi) = {\mathbb{E}}_{\vec s \sim P^\pi}[{G_{\mathrm{obs}}}(\vec s)]$. Naive RLHF, given Boltzmann-rational human feedback over trajectory pairs, will select the policy that maximizes ${J_{\mathrm{obs}}}$ in the infinite data limit (rather than the true value $J$); see Lang et al. 2024, Proposition 4.1 for the precise statement.

::::

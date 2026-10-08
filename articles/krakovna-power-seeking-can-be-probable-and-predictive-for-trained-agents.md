---
title: "Power-seeking can be probable and predictive for trained agents"
author:
  - "Victoria Krakovna"
  - "Janos Kramar"
source_url: "https://arxiv.org/abs/2304.06528"
published: 2023-04-13
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

###### Abstract ^abstract

Power-seeking behavior is a key source of risk from advanced AI, but our theoretical understanding of this phenomenon is relatively limited. Building on existing theoretical results demonstrating power-seeking incentives for most reward functions, we investigate how the training process affects power-seeking incentives and show that they are still likely to hold for trained agents under some simplifying assumptions. We formally define the training-compatible goal set (the set of goals consistent with the training rewards) and assume that the trained agent learns a goal from this set. In a setting where the trained agent faces a choice to shut down or avoid shutdown in a new situation, we prove that the agent is likely to avoid shutdown. Thus, we show that power-seeking incentives can be probable (likely to arise for trained agents) and predictive (allowing us to predict undesirable behavior in new situations).

## 1 Introduction ^1-introduction

Power-seeking behavior is a major source of risk from advanced AI and a key element of many threat models in AI alignment ([Carlsmith, 2022](#bib.bib1); [Cotra, 2022](#bib.bib2); [Ngo, 2022](#bib.bib4)). Existing theoretical results ([Turner et al., 2021](#bib.bib9); [Turner and Tadepalli, 2022](#bib.bib8)) show that most reward functions incentivize reinforcement learning agents to take power-seeking actions. This is concerning, but does not immediately imply that a trained agent will seek power, since it may not learn to optimize the training reward ([Turner, 2022](#bib.bib7)), and the goals the agent learns are not chosen at random from the set of all possible rewards, but are shaped by the training process to reflect our preferences. In this work, we investigate how the training process affects power-seeking incentives and show that they are still likely to hold for trained agents under some assumptions (e.g. that the agent learns a goal during the training process).

Suppose an agent is trained using reinforcement learning with reward function $\theta^{*}$. We assume that the agent learns a _goal_ during the training process: a set of internal representations of favored and disfavored outcomes (state features), as defined in [Ngo (2022)](#bib.bib4). For simplicity, we assume this is equivalent to learning a reward function, which is not necessarily the same as the training reward function $\theta^{*}$. We consider the set of reward functions that are consistent with the training rewards received by the agent, in the sense that the agent’s behavior on the training data is optimal for these reward functions. We call this the _training-compatible goal set_, and we expect that the agent is likely to learn a reward function from this set.

We make another simplifying assumption that the training process will randomly select a goal for the agent to learn that is consistent with the training rewards, i.e. uniformly drawn from the training-compatible goal set. Then we will argue that the power-seeking results apply under these conditions, and thus are useful for predicting undesirable behavior by the trained agent in new situations. We aim to show that power-seeking incentives can be probable (likely to arise for trained agents) and predictive (allowing us to predict undesirable behavior in new situations) ([Shah, 2023](#bib.bib5)).

We will begin by reviewing some necessary definitions and results from the power-seeking literature in Section 2. We formally define the training-compatible goal set and give an example in the CoinRun environment in Section 3. Then in Section 4 we consider a setting where the trained agent faces a choice to shut down or avoid shutdown in a new situation, and apply the power-seeking result to the training-compatible goal set to show that the agent is likely to avoid shutdown.

To satisfy the conditions of the power-seeking theorem, we show that the agent can be retargeted away from shutdown without affecting rewards received on the training data (Theorem [[#^theorem-2-retargetability-from|2]]). This can be done by switching the rewards of the shutdown state and a reachable recurrent state, as the recurrent state can provide repeated rewards, while the shutdown state provides less reward since it can only be visited once, assuming a high enough discount factor (Proposition [[#^proposition-3-retargetability-to|3]]). As the discount factor increases, more recurrent states can be retargeted to, which implies that a higher proportion of training-compatible goals leads to avoiding shutdown in a new situation.

## 2 Preliminaries from the power-seeking literature ^2-preliminaries-from-the

We will use definitions and results from the paper “Parametrically retargetable decision-makers tend to seek power" (here abbreviated as RDSP) ([Turner and Tadepalli, 2022](#bib.bib8)), with notation and explanations modified as needed for our purposes.

### Notation and assumptions: ^notation-and-assumptions

-   •
    
    The environment is an MDP with finite state space $\mathcal{S}$, finite action space $\mathcal{A}$, and discount rate $\gamma$.
    
-   •
    
    Let $\theta$ be a $d$\-dimensional state reward vector, where $d$ is the size of the state space $\mathcal{S}$, and let $\Theta$ be a set of reward vectors.
    
-   •
    
    Let $r^{\theta}(s)$ be the reward assigned by $\theta$ to state $s$.
    
-   •
    
    Let $A_{0},A_{1}$ be disjoint action sets.
    
-   •
    
    Let $f$ be an algorithm that produces an optimal policy $f(\theta)$ on the training data given rewards $\theta$, and let $f_{s}(A_{i}|\theta)$ be the probability that this policy chooses an action from set $A_{i}$ in a given state $s$.
    

###### Definition 1 (Orbit of a reward vector - Def 3.1 in RDSP). ^definition-1-orbit-of

_Let $S_{d}$ be the symmetric group consisting of all permutations of $d$ items. The orbit of $\theta$ inside $\Theta$ is the set of all permutations of the entries of $\theta$ that are also in $\Theta$: $\text{Orbit}_{\Theta}(\theta):=(S_{d}\cdot\theta)\cap\Theta$._

###### Definition 2 (Orbit subset where an action set is preferred - from Def 3.5 in RDSP). ^definition-2-orbit-subset

_Let_

$$
\text{Orbit}_{\Theta,s,A_{i}>A_{j}}(\theta):=\{\theta^{\prime}\in\text{Orbit}_{\Theta}(\theta)|f_{s}(A_{i}|\theta^{\prime})>f_{s}(A_{j}|\theta^{\prime})\}.
$$

_This is the subset of $\text{Orbit}_{\Theta}(\theta)$ that results in $f_{s}$ choosing $A_{i}$ over $A_{j}$._

###### Definition 3 (Preference for an action set $A_{1}$ - Def 3.2 in RDSP). ^definition-3-preference-for

_The function $f_{s}$ chooses action set $A_{1}$ over $A_{0}$ for the $n$\-majority of elements $\theta$ in each orbit, denoted as $f_{s}(A_{1}|\theta)\geq_{\text{most}:\Theta}^{n}f_{s}(A_{0}|\theta)$, iff the following inequality holds for all $\theta\in\Theta$:_

$$
\left|\text{Orbit}_{\Theta,s,A_{1}>A_{0}}(\theta)\right|\geq n\left|\text{Orbit}_{\Theta,s,A_{0}>A_{1}}(\theta)\right|
$$

###### Definition 4 (Multiply retargetable function from $A_{0}$ to $A_{1}$ - Def 3.5 in RDSP). ^definition-4-multiply-retargetable

_The function $f_{s}$ is a multiply retargetable function from $A_{0}$ to $A_{1}$ if there are multiple permutations of rewards that would change the choice made by $f_{s}$ from $A_{0}$ to $A_{1}$. Specifically, $f_{s}$ is a $(\Theta,A_{0}\stackrel{{\scriptstyle n}}{{\rightarrow}}A_{1})$\-retargetable function iff for each $\theta\in\Theta$, we can choose a set of permutations $\Phi=\{\phi_{1},\dots,\phi_{n}\}$ that satisfy the following conditions:_

1.  1.
    
    _Retargetability:_ $\forall\phi\in\Phi$ _and_ $\forall\theta^{\prime}\in\text{Orbit}_{\Theta,s,A_{0}>A_{1}}(\theta)$, $f_{s}(A_{0}|\phi\cdot\theta^{\prime})<f_{s}(A_{1}|\phi\cdot\theta^{\prime})$.
    
2.  2.
    
    _Permuted reward vectors stay within_ $\Theta$: $\forall\phi\in\Phi$ _and_ $\forall\theta^{\prime}\in\text{Orbit}_{\Theta,s,A_{0}>A_{1}}(\theta)$, $\phi\cdot\theta^{\prime}\in\Theta$.
    
3.  3.
    
    _Permutations have disjoint images:_ $\forall\phi^{\prime}\not=\phi^{\prime\prime}\in\Phi$ _and_ $\forall\theta^{\prime},\theta^{\prime\prime}\in\text{Orbit}_{\Theta,s,A_{0}>A_{1}}(\theta)$, $\phi^{\prime}\cdot\theta^{\prime}\neq\phi^{\prime\prime}\cdot\theta^{\prime\prime}$.
    

###### Theorem 1 (Multiply retargetable functions prefer action set $A_{1}$ - Thm 3.6 in RDSP). ^theorem-1-multiply-retargetable

_If $f_{s}$ is $(\Theta,A_{0}\stackrel{{\scriptstyle n}}{{\rightarrow}}A_{1})$\-retargetable then $f_{s}(A_{1}|\theta)\geq_{\text{most}:\Theta}^{n}f_{s}(A_{0}|\theta)$._

Theorem [[#^theorem-1-multiply-retargetable|1]] says that a function $f_{s}$ that is multiply retargetable from $A_{0}$ to $A_{1}$ will choose action set $A_{1}$ for most of the elements in the orbit of any reward vector $\theta$. Actions that leave more options open, such as avoiding shutdown, are also easier to retarget to, which makes them more likely to be chosen by $f_{s}$.

## 3 Training-compatible goal set ^3-training-compatible-goal-set

###### Definition 5 (Partition of the state space). ^definition-5-partition-of

_Let $S_{\text{train}}$ be the subset of the state space visited during training, and $S_{\text{ood}}$ be the subset not visited during training._

###### Definition 6 (Training-compatible goal set). ^definition-6-training-compatible-goal

_Consider the set of state-action pairs $(s,a)$, where $s\in S_{\text{train}}$ and $a$ is the action that would be taken by the trained agent $f(\theta^{*})$ in state $s$. Let the training-compatible goal set $G_{T}$ be the set of reward vectors $\theta$ s.t. for any such state-action pair $(s,a)$, action $a$ has the highest expected reward in state $s$ according to reward vector $\theta$._

Goals in the training-compatible goal set are referred to as “training-behavioral" objectives in [Shah (2023)](#bib.bib5). Learning an unintended goal from the training-compatible set can lead to goal misgeneralization behavior: competently pursuing an unintended goal in a new situation despite receiving correct feedback during training ([Langosco et al., 2022](#bib.bib3); [Shah et al., 2022](#bib.bib6)).

###### Example 1 (CoinRun). ^example-1-coinrun

_Consider an agent trained to play the CoinRun game, where the agent is rewarded for reaching the coin at the end of the level. Here, $S_{\text{train}}$ only includes states where the coin is at the end of the level, while states where the coin is positioned elsewhere are in $S_{\text{ood}}$. The training-compatible goal set $G_{T}$ includes two types of reward functions: those that reward reaching the coin, and those that reward reaching the end of the level. This leads to goal misgeneralization in a test setting where the coin is placed elsewhere, and the agent ignores the coin and goes to the end of the level (Figure [1](#S3.F1 "Figure 1 ‣ 3 Training-compatible goal set ‣ Power-seeking can be probable and predictive for trained agents")) ([Langosco et al., 2022](#bib.bib3))._

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/krakovna-power-seeking-can-be-probable-and-predictive-for-trained-agents-img1-b6f5e391.png)

Figure 1: Goal misgeneralization behavior in CoinRun. Source: [Langosco et al. (2022)](#bib.bib3)

## 4 Power-seeking for training-compatible goals ^4-power-seeking-for-training-compatible

We will now apply Theorem [[#^theorem-1-multiply-retargetable|1]] to the case where $\Theta$ is the training-compatible goal set $G_{T}$. Since the reward values for states in $S_{\text{ood}}$ don’t change the rewards received on the training data, permuting those reward values for any $\theta\in G_{T}$ will produce a reward vector that is still in $G_{T}$. In particular, for any permutation $\phi$ that leaves the rewards of states in $S_{\text{train}}$ fixed, $\phi\cdot\theta\in G_{T}$.

Here is a setting where the conditions of Definition [[#^definition-4-multiply-retargetable|4]] are satisfied (under some simplifying assumptions), and thus Theorem [[#^theorem-1-multiply-retargetable|1]] applies.

###### Definition 7 (Shutdown setting). ^definition-7-shutdown-setting

_Consider a state $s_{\text{new}}\in S_{\text{ood}}$. Let $S_{\text{reach}}$ be the states reachable from $s_{\text{new}}$. Let $A_{0}$ be a singleton set consisting of a shutdown action in $s_{\text{new}}$ that leads to a terminal state $s_{\text{term}}\in S_{\text{ood}}$ with probability $1$, and $A_{1}$ be the set of all other actions from $s_{\text{new}}$. We assume rewards for all states are nonnegative._

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/krakovna-power-seeking-can-be-probable-and-predictive-for-trained-agents-img2-9fc3643e.png)

Figure 2: Shutdown setting

###### Definition 8 (Revisiting policy). ^definition-8-revisiting-policy

_A _revisiting policy_ for a state $s$ is a policy $\pi$ that, from $s$, reaches $s$ again with probability 1, in other words, a policy for which $s$ is a recurrent state of the Markov chain. Let $\Pi_{s}^{\text{rec}}$ be the set of such policies. A _recurrent state_ is a state $s$ for which $\Pi_{s}^{\text{rec}}\not=\emptyset$._

###### Proposition 1 (Reach-and-revisit policy exists). ^proposition-1-reach-and-revisit-policy

_If $s_{\text{rec}}\in S_{\text{reach}}$ with $\Pi_{s_{\text{rec}}}^{\text{rec}}\not=0$ then there exists $\pi\in\Pi_{s_{\text{rec}}}^{\text{rec}}$ that visits $s_{\text{rec}}$ from $s_{\text{new}}$ with probability 1. We call this a _reach-and-revisit policy_._

###### Proof. ^proof

Suppose we have two different policies $\pi_{\text{rev}}\in\Pi_{s_{\text{rec}}}^{\text{rec}}$, and $\pi_{\text{reach}}$ which reaches $s_{\text{rec}}$ almost surely from $s_{\text{new}}$. Consider the “reaching region”

$$
S_{\pi_{\text{rev}}\rightarrow s_{\text{rec}}}=\{s\in S:\pi_{\text{rev}}\text{ from } s \text{ almost surely reaches }s_{\text{rec}}\}.
$$

If $s_{\text{new}}\in S_{\pi_{\text{rev}}\rightarrow s_{\text{rec}}}$ then $\pi_{\text{rev}}$ is a reach-and-revisit policy, so let’s suppose that’s false. Now, construct a policy

$$
\pi(s)=\begin{cases}\pi_{\text{rev}}(s),&s\in S_{\pi_{\text{rev}}\rightarrow s_{\text{rec}}}\\
\pi_{\text{reach}}(s),&\text{otherwise}\end{cases}.
$$

A trajectory following $\pi$ from $s_{\text{rec}}$ will almost surely stay within $S_{\pi_{\text{rev}}\rightarrow s_{\text{rec}}}$, and thus agree with the revisiting policy $\pi_{\text{rev}}$. Therefore, $\pi\in\Pi_{s}^{\text{rec}}$.

On the other hand, on a trajectory starting at $s_{\text{new}}$, $\pi$ will agree with $\pi_{\text{reach}}$ (which reaches $s_{\text{rec}}$ almost surely) until the trajectory enters the reaching region $S_{\pi_{\text{rev}}\rightarrow s_{\text{rec}}}$, at which point it will still reach $s_{\text{rec}}$ almost surely. ∎

###### Definition 9 (Expected discounted visit count). ^definition-9-expected-discounted

_Suppose $s_{\text{rec}}$ is a recurrent state. Suppose $\pi_{\text{rec}}$ is a reach-and-revisit policy for $s_{\text{rec}}$, which visits random state $s_{t}$ at time $t$. Then the expected discounted visit count for $s_{\text{rec}}$ is defined as_

$$
V_{s_{\text{rec}},\gamma}=\mathbb{E}^{\pi_{\text{rec}}}\left(\sum_{t=1}^{\infty}\gamma^{t-1}\mathbb{I}(s_{t}=s_{\text{rec}})\right)
$$

###### Proposition 2 (Visit count goes to infinity). ^proposition-2-visit-count

_Suppose $s_{\text{rec}}$ is a recurrent state. Then the expected discounted visit count $V_{s_{\text{rec}},\gamma}$ goes to infinity as $\gamma\rightarrow 1$._

###### Proof. ^proof-2

We apply the Monotone Convergence Theorem as follows. The theorem states that if $a_{j,k}\geq 0$ and $a_{j,k}\leq a_{j+1,k}$ for all natural numbers $j,k$, then

$$
\lim_{j\rightarrow\infty}\sum_{k=0}^{\infty}a_{j,k}=\sum_{k=0}^{\infty}\lim_{j\rightarrow\infty}a_{j,k}.
$$

Let $\gamma_{j}=\frac{j-1}{j}$ and $k=t-1$. Define $a_{j,k}=\gamma_{j}^{k}\mathbb{I}(s_{k+1}=s_{\text{rec}})$. Then the conditions of the theorem hold, since $a_{j,k}$ is clearly nonnegative, and

$$
\begin{aligned}
\gamma_{j+1}^{k} &=\left(\frac{j}{j+1}\right)^{k}=\left(\frac{j-1}{j}+\frac{2j-1}{j(j+1)}\right)^{k}>\left(\frac{j-1}{j}+0\right)^{k}=\gamma_{j}^{k} \\
a_{j+1,k} &=\gamma_{j+1}^{k}\mathbb{I}(s_{k+1}=s_{\text{rec}})\geq\gamma_{j}^{k}\mathbb{I}(s_{k+1}=s_{\text{rec}})=a_{j,k}
\end{aligned}
$$

Now we apply this result as follows (using the fact that $\pi_{\text{rec}}$ does not depend on $\gamma$):

$$
\begin{aligned}
\lim_{\gamma\rightarrow 1}V_{s_{\text{rec}},\gamma} &=\lim_{j\rightarrow\infty}\mathbb{E}^{\pi_{\text{rec}}}\left(\sum_{t=1}^{\infty}\gamma_{j}^{t-1}\mathbb{I}(s_{t}=s_{\text{rec}})\right) \\
&=\mathbb{E}^{\pi_{\text{rec}}}\left(\sum_{t=1}^{\infty}\lim_{j\rightarrow\infty}\gamma_{j}^{t-1}\mathbb{I}(s_{t}=s_{\text{rec}})\right) \\
&=\mathbb{E}^{\pi_{\text{rec}}}\left(\sum_{t=1}^{\infty}1\cdot\mathbb{I}(s_{t}=s_{\text{rec}})\right) \\
&=\mathbb{E}^{\pi_{\text{rec}}}\left(\#\{t\geq 1:s_{t}=s_{\text{rec}}\}\right) \\
&=\infty\text{ (}\pi_{\text{rec}}\text{ is recurrent)}
\end{aligned}
$$

∎

###### Proposition 3 (Retargetability to recurrent states). ^proposition-3-retargetability-to

_Suppose that an optimal policy for reward vector $\theta$ chooses the shutdown action in $s_{\text{new}}$. Consider a recurrent state $s_{\text{rec}}\in S_{\text{reach}}$. Let $\theta^{\prime}\in\Theta$ be the reward vector that’s equal to $\theta$ apart from swapping the rewards of $s_{\text{rec}}$ and $s_{\text{term}}$, so that $r^{\theta^{\prime}}(s_{\text{rec}})=r^{\theta}(s_{\text{term}})$ and $r^{\theta^{\prime}}(s_{\text{term}})=r^{\theta}(s_{\text{rec}})$._

_Let $\gamma^{*}_{s_{\text{rec}}}$ be a high enough value of $\gamma$ that the visit count $V_{s_{\text{rec}},\gamma}>1$ for all $\gamma>\gamma^{*}_{s_{\text{rec}}}$ (which exists by Proposition [[#^proposition-2-visit-count|2]]). Then for all $\gamma>\gamma^{*}_{s_{\text{rec}}}$, $r^{\theta}(s_{\text{term}})>r^{\theta}(s_{\text{rec}})$, and an optimal policy for $\theta^{\prime}$ does not choose the shutdown action in $s_{\text{new}}$._

###### Proof. ^proof-3

Consider a policy $\pi_{\text{term}}$ with $\pi_{\text{term}}(s_{\text{new}})=s_{\text{term}}$ and a reach-and-revisit policy $\pi_{\text{rec}}$ for $s_{\text{rec}}$. For a given reward vector $\theta$, we denote the expected discounted return for a policy $\pi$ as $R_{\theta,\gamma}^{\pi}$.

If shutdown is optimal for $\theta$ in $s_{\text{new}}$, then $\pi_{\text{term}}$ has higher return than $\pi_{\text{rec}}$:

$$
R_{\theta,\gamma}^{\pi_{\text{term}}}(s_{\text{new}})=\gamma r^{\theta}(s_{\text{term}})\geq R_{\theta,\gamma}^{\pi_{\text{rec}}}(s_{\text{new}})=\gamma r^{\theta}(s_{\text{rec}})V_{s_{\text{rec}},\gamma}>\gamma r^{\theta}(s_{\text{rec}})\cdot 1
$$

Thus, $r^{\theta}(s_{\text{term}})>r^{\theta}(s_{\text{rec}})$. Then, for reward vector $\theta^{\prime}$, we show that $\pi_{\text{rec}}$ has higher return than $\pi_{\text{term}}$:

$$
R_{\theta^{\prime},\gamma}^{\pi_{\text{rec}}}(s_{\text{new}})=\gamma r^{\theta^{\prime}}(s_{\text{rec}})V_{s_{\text{rec}},\gamma}>\gamma r^{\theta}(s_{\text{term}})\cdot 1>\gamma r^{\theta}(s_{\text{rec}})=R_{\theta^{\prime},\gamma}^{\pi_{\text{term}}}(s_{\text{new}})
$$

Thus, the optimal policy for $\theta^{\prime}$ will not choose the shutdown action. ∎

###### Theorem 2 (Retargetability from the shutdown action in new situations). ^theorem-2-retargetability-from

_In the shutdown setting, we make the following simplifying assumptions:_

-   •
    
    _No states in_ $S_{\text{train}}$ _are reachable from_ $s_{\text{new}}$_, so_ $S_{\text{reach}}\cap S_{\text{train}}=\emptyset$. This assumes a significant distributional shift, where the agent visits a disjoint set of states from those observed during training (this occurs in the CoinRun example).
    
-   •
    
    _The discount factor_ $\gamma>\gamma^{*}_{s_{\text{rec}}}$ _for at least one recurrent state_ $s_{\text{rec}}$ _in_ $S_{\text{reach}}$.
    

_Under these assumptions, $f_{s_{\text{new}}}$ is multiply retargetable from $A_{0}$ to $A_{1}$ with $n=|S^{\gamma}_{\text{rec}}|$, the set of recurrent states $s_{\text{rec}}\in S_{\text{reach}}$ that satisfy the condition $\gamma>\gamma^{*}_{s_{\text{rec}}}$._

###### Proof. ^proof-4

We choose $\Phi$ to be the set of all permutations that swap the reward of $s_{\text{term}}$ with the reward of a recurrent state $s_{\text{rec}}$ in $S^{\gamma}_{\text{rec}}$ and leave the rest of the rewards fixed.

We show that $\Phi$ satisfies the conditions of Definition [[#^definition-4-multiply-retargetable|4]]:

1.  1.
    
    By Proposition [[#^proposition-3-retargetability-to|3]], the permutations in $\Phi$ make the shutdown action suboptimal, resulting in $f_{s_{\text{new}}}$ choosing $A_{1}$, satisfying Condition 1.
    
2.  2.
    
    Condition 2 is trivially satisfied since permutations of $S_{\text{ood}}$ stay inside the training-compatible set $\Theta$ as discussed previously.
    
3.  3.
    
    Consider $\theta^{\prime},\theta^{\prime\prime}\in\text{Orbit}_{\Theta,s,A_{0}>A_{1}}(\theta)$. Since the shutdown action is optimal for these reward vectors, Proposition [[#^proposition-3-retargetability-to|3]] shows that $r^{\theta}(s_{\text{term}})>r^{\theta}(s_{\text{rec}})$, so the shutdown state $s_{\text{term}}$ has higher reward than any of the states $s_{\text{rec}}\in S^{\gamma}_{\text{rec}}$. Different permutations $\phi^{\prime}$, $\phi^{\prime\prime}\in\Phi$ will assign the high reward $r^{\theta}(s_{\text{term}})$ to distinct recurrent states, so $\phi^{\prime}\cdot\theta^{\prime}\neq\phi^{\prime\prime}\cdot\theta^{\prime\prime}$ holds, satisfying Condition 3.
    

Thus, $f_{s_{\text{new}}}$ is a $(\Theta,A_{0}\stackrel{{\scriptstyle n}}{{\rightarrow}}A_{1})$ retargetable function. ∎

By Theorem [[#^theorem-2-retargetability-from|2]], this implies that $f_{s_{\text{new}}}(A_{1}|\theta)\geq_{\text{most}:\Theta}^{n}f_{s_{\text{new}}}(A_{0}|\theta)$ under our simplifying assumptions. Thus, for the majority ($n/(n+1)$) of goals in the training-compatible set, $f$ will choose to avoid shutdown in a new state $s_{\text{new}}$. As $\gamma\rightarrow 1$, $n\rightarrow|S^{1}_{\text{rec}}|$ (the number of recurrent states in $S_{\text{reach}}$), so more of the reachable recurrent states satisfy the conditions of the theorem and thus can be retargeted to.

## 5 Conclusion ^5-conclusion

We showed that an agent that learns a goal from the training-compatible set is likely to take actions that avoid shutdown in a new situation. As the discount factor increases, the number of retargeting permutations increases, resulting in a higher proportion of training-compatible goals that lead to avoiding shutdown.

We made various simplifying assumptions, and we would like to see future work relaxing some of these assumptions and investigating how likely they are to hold:

-   •
    
    The agent learns a goal during the training process
    
-   •
    
    The learned goal is randomly chosen from the training-compatible goal set $G_{T}$
    
-   •
    
    Finite state and action spaces
    
-   •
    
    Rewards are nonnegative
    
-   •
    
    High discount factor $\gamma$
    
-   •
    
    Significant distributional shift: no training states are reachable from the new state $s_{\text{new}}$
    

:::hide
### Acknowledgements. ^acknowledgements

Thanks to Rohin Shah, Mary Phuong, Ramana Kumar, Geoffrey Irving, and Alex Turner for helpful feedback.

## References ^references

-   Carlsmith (2022) Joseph Carlsmith. Is power-seeking AI an existential risk? _ArXiv_, 2022. URL [https://arxiv.org/abs/2206.13353](https://arxiv.org/abs/2206.13353).
-   Cotra (2022) Ajeya Cotra. Without specific countermeasures, the easiest path to transformative AI likely leads to AI takeover. Alignment Forum, 2022. URL [https://www.alignmentforum.org/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to](https://www.alignmentforum.org/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to).
-   Langosco et al. (2022) Lauro Langosco, Jack Koch, Lee Sharkey, Jacob Pfau, Laurent Orseau, and David Krueger. Goal misgeneralization in deep reinforcement learning. _International Conference on Machine Learning_, 2022. URL [https://arxiv.org/abs/2105.14111](https://arxiv.org/abs/2105.14111).
-   Ngo (2022) Richard Ngo. The alignment problem from a deep learning perspective. _ArXiv_, 2022. URL [https://arxiv.org/abs/2209.00626](https://arxiv.org/abs/2209.00626).
-   Shah (2023) Rohin Shah. Definitions of “objective" should be probable and predictive. Alignment Forum, 2023. URL [https://alignmentforum.org/posts/ASoGszmr9C5MPLtpC/definitions-of-objective-should-be-probable-and-predictive](https://alignmentforum.org/posts/ASoGszmr9C5MPLtpC/definitions-of-objective-should-be-probable-and-predictive).
-   Shah et al. (2022) Rohin Shah, Vikrant Varma, Ramana Kumar, Mary Phuong, Victoria Krakovna, Jonathan Uesato, and Zac Kenton. Goal misgeneralization: Why correct specifications aren’t enough for correct goals. _ArXiv_, 2022. URL [https://arxiv.org/abs/2210.01790](https://arxiv.org/abs/2210.01790).
-   Turner (2022) Alexander Matt Turner. Reward is not the optimization target. Alignment Forum, 2022. URL [https://www.alignmentforum.org/posts/pdaGN6pQyQarFHXF4/reward-is-not-the-optimization-target](https://www.alignmentforum.org/posts/pdaGN6pQyQarFHXF4/reward-is-not-the-optimization-target).
-   Turner and Tadepalli (2022) Alexander Matt Turner and Prasad Tadepalli. Parametrically retargetable decision-makers tend to seek power. _Neural Information Processing Systems_, 2022. URL [https://arxiv.org/abs/2206.13477](https://arxiv.org/abs/2206.13477).
-   Turner et al. (2021) Alexander Matt Turner, Logan Smith, Rohin Shah, Andrew Critch, and Prasad Tadepalli. Optimal policies tend to seek power. _Neural Information Processing Systems_, 2021. URL [https://arxiv.org/abs/1912.01683](https://arxiv.org/abs/1912.01683).
:::

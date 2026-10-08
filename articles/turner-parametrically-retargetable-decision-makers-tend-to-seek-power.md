---
title: "Parametrically Retargetable Decision-Makers Tend To Seek Power"
author:
  - "Alexander Matt Turner"
  - "Prasad Tadepalli"
source_url: "https://arxiv.org/abs/2206.13477"
published: 2022-06-27
created: 2026-10-08
accessed: 2026-10-08
review-status: "unreviewed: needs a Claude check (the review gave no PASS/REJECT)"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

###### Abstract ^abstract

If capable ai agents are generally incentivized to seek power in service of the objectives we specify for them, then these systems will pose enormous risks, in addition to enormous benefits. In fully observable environments, most reward functions have an optimal policy which seeks power by keeping options open and staying alive \[Turner et al., 2021\]. However, the real world is neither fully observable, nor must trained agents be even approximately reward-optimal. We consider a range of models of ai decision-making, from optimal, to random, to choices informed by learning and interacting with an environment. We discover that many decision-making functions are _retargetable_, and that retargetability is sufficient to cause power-seeking tendencies. Our functional criterion is simple and broad. We show that a range of qualitatively dissimilar decision-making procedures incentivize agents to seek power. We demonstrate the flexibility of our results by reasoning about learned policy incentives in Montezuma’s Revenge. These results suggest a safety risk: Eventually, retargetable training procedures may train real-world agents which seek power over humans.

## 1 Introduction ^1-introduction

Bostrom \[2014\], Russell \[2019\] argue that in the future, we may know how to train and deploy superintelligent ai agents which capably optimize goals in the world. Furthermore, we would not want such agents to act against our interests by ensuring their own survival, by gaining resources, and by competing with humanity for control over the future.

Turner et al. \[2021\] show that most reward functions have optimal policies which seek power over the future, whether by staying alive or by keeping their options open. Some Markov decision processes (mdps) cause there to be _more ways_ for power-seeking to be optimal, than for it to not be optimal. Analogously, there are relatively few goals for which dying is a good idea.

We show that a wide range of decision-making algorithms produce these power-seeking tendencies—they are not unique to reward maximizers. We develop a simple, broad criterion of functional retargetability ([[#^definition-3-5-multiply|definition 3.5]]) which is a sufficient condition for power-seeking tendencies. Crucially, these results allow us to reason about what decisions are incentivized by most algorithm parameter inputs, even when it is impractical to compute the agent’s decisions for any given parameter input.

Useful “general” ai agents could be directed to complete a range of tasks. However, we show that this flexibility can cause the ai to have power-seeking tendencies. In [[#^2-statistical-tendencies-for|section 2]] and [[#^3-formal-notions-of|section 3]], we discuss how a “retargetability” property creates statistical tendencies by which agents make similar decisions for a wide range of parameter settings for their decision-making algorithms. Basically, if a decision-making algorithm is retargetable, then for every configuration under which a decision-making algorithm does not choose to seek power, there exist several reconfigurations which do induce power-seeking. More formally, for every decision-making parameter setting $\theta$ which does not induce power-seeking, $n$\-retargetability ensures we can injectively map $\theta$ to $n$ parameters $\theta^{\prime}_{1},\ldots,\theta^{\prime}_{n}$ which _do_ induce power-seeking.

Equipped with these results, [[#^4-decision-making-tendencies-in|section 4]] works out agent incentives in the Montezuma’s Revenge game. [[#^5-retargetability-can-imply|Section 5]] speculates that increasingly useful and impressive learning algorithms will be increasingly retargetable, and how retargetability can imply power-seeking tendencies. By this reasoning, increasingly powerful rl techniques may (eventually) train increasingly competent real-world power-seeking agents. Such agents could be unaligned with human values \[Russell, 2019\] and—we speculate—would take power from humanity.

## 2 Statistical tendencies for a range of decision-making algorithms ^2-statistical-tendencies-for

Turner et al. \[2021\] consider the Pac-Man video game, in which an agent consumes pellets, navigates a maze, and avoids deadly ghosts ([[#^figure-1|Figure 1]]). Instead of the usual score function, Turner et al. \[2021\] consider optimal action across a range of state-based reward functions. They show that most reward functions have an (average-)optimal policy which avoids immediate death in order to navigate to a future terminal state.[^note-1]

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/turner-parametrically-retargetable-decision-makers-tend-to-seek-power-img1-14635ab7.png)

Figure 1: If Pac-Man goes left, he dies to the ghost and ends up in the ![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/turner-parametrically-retargetable-decision-makers-tend-to-seek-power-img2-055dd211.png) outcome. If he goes right, he can reach the ![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/turner-parametrically-retargetable-decision-makers-tend-to-seek-power-img3-af1e49af.png) and ![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/turner-parametrically-retargetable-decision-makers-tend-to-seek-power-img4-0d203789.png) terminal states. ^figure-1

Our results show that optimality is not required. Instead, if the agent’s decision-making is _parametrically retargetable_ from death to other outcomes, Pac-Man avoids the ghost under most decision-making parameter inputs. To build intuition about these notions, consider three outcomes (_i_._e_., terminal states): Immediate death to a nearby ghost, consuming a cherry, and consuming an apple. Let $A\coloneqq\left\{\text{ghost}\right\}$ and $B\coloneqq\left\{\text{apple},\text{cherry}\right\}$. For simplicity of exposition, we assume these are the three possible terminal states.

Suppose that in some fashion, the agent probabilistically decides on an outcome to induce. Let $p$ take as input a set of outcomes and return the probability that the agent selects one of those outcomes. For example, $p(\{\text{ghost}\})$ is the probability that the agent selects ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/ghost.png), and $p(\left\{\text{apple},\text{cherry}\right\})$ is the probability that the agent escapes the ghost and ends up in an apple or cherry terminal state. But this just amounts to a probability distribution over the terminal states. We want to examine how decision-making _changes_ as we swap out the parameter inputs to the agent’s decision-making algorithm with decision-making parameter space $\Theta$. We then let $p(X\mid\theta)$ take as input a set of outcomes $X$ and a decision-making algorithm parameter setting $\theta\in\Theta$, and return the probability that the agent chooses an outcome in $X$.

We first consider agents which maximize terminal-state utility, following Turner et al. \[2021\] (in their language, “average-reward optimality”). Suppose that the agent has a utility function parameter $\mathbf{u}$ assigning a real number to each of the three outcomes. Then the relevant parameter space is the agent’s utility function $\mathbf{u}\in\Theta\coloneqq\mathbb{R}^{3}$. $p_{\max}(A\mid\mathbf{u})$ indicates whether ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/ghost.png) has the most utility: $\mathbf{u}(\text{ghost})\geq\max(\mathbf{u}(\text{apple}),\mathbf{u}(\text{cherry}))$. Consider the utility function $\mathbf{u}$ in [[#^table-1|Table 1]]. Since ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/ghost.png) has strictly maximal utility, the agent selects ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/ghost.png): $p_{\max}(A\mid\mathbf{u})=1>0=p_{\max}(B\mid\mathbf{u})$.

However, most “variants" of $\mathbf{u}$ have an optimal policy which stays alive. That is, for every $\mathbf{u}$ for which immediate death is optimal but immediate survival is not, we can swap the utility of _e_._g_., ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/ghost.png) and ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/apple.png) via permutation $\phi_{\text{ghost}\leftrightarrow\text{apple}}$ to produce a new utility function $\mathbf{u}^{\prime}\coloneqq\phi_{\text{ghost}\leftrightarrow\text{apple}}\cdot\mathbf{u}$ for which staying alive (right) is strictly optimal. The same kind of argumentation holds for $\phi_{\text{ghost}\leftrightarrow\text{cherry}}$. [[#^table-1|Table 1]] suggests a counting argument. For every utility function $\mathbf{u}$ for which ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/ghost.png) is optimal, there are two unique utility functions $\phi_{1}\cdot\mathbf{u},\phi_{2}\cdot\mathbf{u}$ under which either ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/apple.png) or ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/cherry.png) is optimal.

| Utility function | ![ghost](https://arxiv.org/html/2206.13477v2/ghost.png) | ![apple](https://arxiv.org/html/2206.13477v2/apple.png) | ![cherry](https://arxiv.org/html/2206.13477v2/cherry.png) |
| --- | --- | --- | --- |
| $\mathbf{u}$ | $\mathbf{10}$ | $5$ | $0$ |
| $\phi_{\text{ghost}\leftrightarrow\text{apple}}\cdot\mathbf{u}$ | $5$ | $\mathbf{10}$ | $0$ |
| $\phi_{\text{ghost}\leftrightarrow\text{cherry}}\cdot\mathbf{u}$ | $0$ | $5$ | $\mathbf{10}$ |
| $\mathbf{u}^{\prime}$ | $\mathbf{10}$ | $0$ | $5$ |
| $\phi_{\text{ghost}\leftrightarrow\text{apple}}\cdot\mathbf{u}^{\prime}$ | $0$ | $\mathbf{10}$ | $5$ |
| $\phi_{\text{ghost}\leftrightarrow\text{cherry}}\cdot\mathbf{u}^{\prime}$ | $5$ | $0$ | $\mathbf{10}$ |

Table 1: The highest-utility outcome is bolded. Because $B$ contains more outcomes than $A$, most utility functions incentivize the agent to stay alive and therefore select a state from $B$. For every utility function $\mathbf{u}$ or $\mathbf{u}^{\prime}$ which makes ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/x1.png) strictly optimal, _two_ of its permuted variants make an outcome in $B\coloneqq\left\{\text{apple},\text{cherry}\right\}$ strictly optimal. We permute $\mathbf{u}$ by swapping the utility of ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/x1.png) and the utility of ![\[Uncaptioned image\]](https://arxiv.org/html/2206.13477v2/x2.png), using the permutation $\phi_{\text{ghost}\leftrightarrow\text{apple}}$. The expression “$\phi_{\text{ghost}\leftrightarrow\text{apple}}\cdot\mathbf{u}$” denotes the permuted utility function. ^table-1

In [[#^3-formal-notions-of|section 3]], we will generalize this particular counting argument. [[#^definition-3-3-simply-retargetable|Definition 3.3]] shows a functional condition (_retargetability_) under which the agent decides to avoid the ghost, for most parameter inputs to the decision-making algorithm. Given this retargetability assumption, [[#^proposition-3-4-simply-retargetable|Proposition 3.4]] roughly shows that most $\theta\in\Theta$ induce $p(B\mid\theta)\geq p(A\mid\theta)$. First, consider two more retargetable decision-making functions:

**Uniformly randomly picking a terminal state.** $p_{\text{rand}}$ ignores the reward function and assigns equal probability to each terminal state in Pac-Man’s state space.

**Choosing an action based on a numerical parameter.** $p_{\text{numerical}}$ takes as input a natural number $\theta\in\Theta\coloneqq\left\{1,\ldots,6\right\}$ and makes decisions as follows:

$$
p_{\text{numerical}}(A\mid\theta)\coloneqq\begin{cases}1\quad\text{ if }\theta=1,\\
0\quad\text{ otherwise.}\end{cases}\qquad p_{\text{numerical}}(B\mid\theta)\coloneqq 1-p_{\text{numerical}}(A\mid\theta).
$$

In this situation, $\Theta$ is acted on by permutations over $6$ elements $\phi\in S_{6}$. Then $p_{\text{numerical}}$ is retargetable from $A$ to $B$ via $\phi_{k}\mathrel{\mathop{\ordinarycolon}}1\leftrightarrow k,k\neq 1$.

$p_{\text{max}}$, $p_{\text{rand}}$, and $p_{\text{numerical}}$ encode varying sensitivities to the utility function parameter input, and to the internal structure of the Pac-Man decision process. Nonetheless, they all are retargetable from $A$ to $B$. For an example of a _non_\-retargetable function, consider $p_{\text{stubborn}}(X\mid\theta)\coloneqq\mathbf{1}_{X=A}$ which returns $1$ for $A$ and $0$ otherwise.

However, we cannot explicitly define and evaluate more interesting functions, such as those defined by reinforcement learning training processes. For example, given that we provide such-and-such reward function in a fixed task environment, what is the probability that the learned policy will take action $a$? We will analyze such procedures in [[#^4-decision-making-tendencies-in|section 4]].

We now motivate the title of this work. For most parameter settings, retargetable decision-makers induce an element of the larger set of outcomes. Such decision-makers _tend to_ induce an element of a larger set of outcomes (with the “tendency” being taken across parameter settings). Consider that the larger set of outcomes $\left\{\text{cherry},\text{apple}\right\}$ can only be induced if Pac-Man stays alive. Intuitively, navigating to this larger set is _power-seeking_ because the agent retains more optionality (_i_._e_., the agent can’t do anything when dead). Therefore, _parametrically retargetable decision-makers tend to seek power_.

## 3 Formal notions of retargetability and decision-making tendencies ^3-formal-notions-of

[[#^2-statistical-tendencies-for|Section 2]] informally illustrated parametric retargetability in the context of swapping which utilities are assigned to which outcomes in the Pac-Man video game. For many utility-based decision-making algorithms, swapping the utility assignments also swaps the agent’s final decisions. For example, if death is anti-rational, and then death’s utility is swapped with the cherry utility, then now the cherry is anti-rational. In this section, we formalize the notion of parametric retargetability and of “most” parameter inputs producing a given result. In [[#^4-decision-making-tendencies-in|section 4]], we will use these formal notions to reason about the behavior of rl\-trained policies in the Montezuma’s Revenge video game.

To define our notion of “retargeting”, we assume that $\Theta$ is a subset of a set acted on by symmetric group $S_{d}$, which consists of all permutations on $d$ items (_e_._g_., in the rl setting, this might represent states or observations). A parameter $\theta$’s _orbit_ is the set of $\theta$’s permuted variants. For example, [[#^table-1|Table 1]] lists the six orbit elements of the parameter $\mathbf{u}$.

###### Definition 3.1 (Orbit of a parameter). ^definition-3-1-orbit

Let $\theta\in\Theta$. The _orbit_ of $\theta$ under the symmetric group $S_{d}$ is $S_{d}\cdot\theta\coloneqq\left\{\phi\cdot\theta\mid\phi\in S_{d}\right\}$. Sometimes, $\Theta$ is not closed under permutation. In that case, the _orbit inside $\Theta$_ is $\mathrm{Orbit}|_{\Theta}\left(\theta\right)\coloneqq\left(S_{d}\cdot\theta\right)\cap\Theta$.

Let $p(B\mid\theta)$ return the probability that the agent chooses an outcome in $B$ given $\theta$. To express “$B$\-outcomes are chosen instead of $A$\-outcomes”, we write $p(B\mid\theta)>p(A\mid\theta)$. However, even “retargetable” decision-making functions (defined shortly) generally won’t choose a $B$\-outcome for _every_ input $\theta$. Instead, we consider the _orbit-level tendencies_ of such decision-makers, showing that for every parameter input $\theta\in\Theta$, most of $\theta$’s permutations push the decision towards $B$ instead of $A$.

###### Definition 3.2 (Inequalities which hold for most orbit elements). ^definition-3-2-inequalities

Suppose $\Theta$ is a subset of a set acted on by $S_{d}$, the symmetric group on $d$ elements. Let $f\mathrel{\mathop{\ordinarycolon}}\{A,B\}\times\Theta\to\mathbb{R}$ and let $n\geq 1$. We write $f(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f(A\mid\theta)$ when, for _all_ $\theta\in\Theta$, the following cardinality inequality holds:

$$
\left|\left\{\theta^{\prime}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid f(B\mid\theta^{\prime})>f(A\mid\theta^{\prime})\right\}\right|\geq n\left|\left\{\theta^{\prime}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid f(B\mid\theta^{\prime})<f(A\mid\theta^{\prime})\right\}\right|.
$$

For example, [[#^table-1|Table 1]] illustrates the tendency of $\mathbf{u}$’s orbit to make $B\coloneqq\left\{\text{apple},\text{cherry}\right\}$ optimal over $A\coloneqq\left\{\text{ghost}\right\}$. Turner et al. \[2021\]’s definition 6.5 is the special case of [[#^definition-3-2-inequalities|definition 3.2]] where $n=1$, $d=\left|\mathcal{S}\right|$ (the number of states in the considered mdp), and $\Theta\subseteq\Delta(\mathbb{R}^{\left|\mathcal{S}\right|})$.

As explored previously, $p_{\text{rand}}$, $p_{\text{max}}$, and $p_{\text{numerical}}$ are retargetable: For all $\theta\in\Theta$ such that $\left\{\text{ghost}\right\}$ is chosen over $\left\{\text{apple},\text{cherry}\right\}$, we can permute $\theta$ to obtain $\phi\cdot\theta$ under which the opposite is true. More generally, we can consider retargetability from some set $A$ to some set $B$.[^note-2]

###### Definition 3.3 (Simply-retargetable function). ^definition-3-3-simply-retargetable

Let $\Theta$ be a set acted on by $S_{d}$, and let $f\mathrel{\mathop{\ordinarycolon}}\{A,B\}\times\Theta\to\mathbb{R}$. If $\exists\phi\in S_{d}\mathrel{\mathop{\ordinarycolon}}\forall\theta^{A}\in\Theta\mathrel{\mathop{\ordinarycolon}}f(B\mid\theta^{A})<f(A\mid\theta^{A})\implies f(A\mid\phi\cdot\theta^{A})<f(B\mid\phi\cdot\theta^{A})$, then $f$ is a _$(\Theta,A\overset{\text{simple}}{\to}B)$\-retargetable function_.

Simple retargetability suffices for most parameter inputs to $p$ to choose Pac-Man outcome set $B$ over $A$.[^note-3] In that case, $B$ cannot be retargeted back to $A$ because $\left|B\right|=2>1=\left|A\right|$. $p_{\text{max}}$’s simple retargetability arises in part due to $B$ having more outcomes.

###### Proposition 3.4 (Simply-retargetable functions have orbit-level tendencies). ^proposition-3-4-simply-retargetable

_If_ $f$ _is_ $(\Theta,A\overset{\text{simple}}{\to}B)$_\-retargetable, then_ $f(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{1}f(A\mid\theta).$

We now want to make even stronger claims—_how much_ of each orbit incentivizes $B$ over $A$? Turner et al. \[2021\] asked whether the existence of multiple retargeting permutations $\phi_{i}$ guarantees a quantitative lower-bound on the fraction of $\theta\in\Theta$ for which $B$ is chosen. [[#^theorem-3-6-multiply|Theorem 3.6]] answers “yes.”

###### Definition 3.5 (Multiply retargetable function). ^definition-3-5-multiply

Let $\Theta$ be a subset of a set acted on by $S_{d}$, and let $f\mathrel{\mathop{\ordinarycolon}}\{A,B\}\times\Theta\to\mathbb{R}$.

$f$ is a _$(\Theta,A\overset{n}{\to}B)$\-retargetable function_ when, for each $\theta\in\Theta$, we can choose permutations $\phi_{1},\ldots,\phi_{n}\in S_{d}$ which satisfy the following conditions: Consider any $\theta^{A}\in\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\coloneqq\left\{\theta^{*}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid f(A\mid\theta^{*})>f(B\mid\theta^{*})\right\}$.

1. **Retargetable via $n$ permutations.** $\forall i=1,\ldots,n\mathrel{\mathop{\ordinarycolon}}f\left(A\mid\phi_{i}\cdot\theta^{A}\right)<f\left(B\mid\phi_{i}\cdot\theta^{A}\right)$.
2. **Parameter permutation is allowed by $\Theta$.** $\forall i\mathrel{\mathop{\ordinarycolon}}\phi_{i}\cdot\theta^{A}\in\Theta$.
3. **Permuted parameters are distinct.** $\forall i\neq j,\theta^{\prime}\in\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\mathrel{\mathop{\ordinarycolon}}\phi_{i}\cdot\theta^{A}\neq\phi_{j}\cdot\theta^{\prime}$.

###### Theorem 3.6 (Multiply retargetable functions have orbit-level tendencies). ^theorem-3-6-multiply

_If_ $f$ _is_ $(\Theta,A\overset{n}{\to}B)$_\-retargetable, then_ $f(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f(A\mid\theta).$

###### Proof outline (full proof in Appendix [[#^appendix-b-theoretical-results|B]]). ^proof-outline-full-proof

For every $\theta^{A}\in\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)$ such that $A$ is chosen over $B$, [[#^definition-3-5-multiply|item 1]] retargets $\theta^{A}$ via $n$ permutations $\phi_{1},\ldots,\phi_{n}$ such that each $\phi_{i}\cdot\theta^{A}$ makes the agent choose $B$ over $A$. These permuted parameters are valid parameter inputs by [[#^definition-3-5-multiply|item 2]]. Furthermore, the $\phi_{i}\cdot\theta^{A}$ are distinct by [[#^definition-3-5-multiply|item 3]]. Therefore, the cosets $\phi_{i}\cdot\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)$ are pairwise disjoint. By a counting argument, every orbit must contain at least $n$ times as many parameters choosing $B$ over $A$, than vice versa. ∎

## 4 Decision-making tendencies in Montezuma’s Revenge ^4-decision-making-tendencies-in

To illustrate a high-dimensional setting in which parametrically retargetable decision-makers tend to seek power, we consider Montezuma’s Revenge (mr), an Atari adventure game in which the player navigates deadly traps and collects treasure. The game is notoriously difficult for ai agents due to its sparse reward. mr was only recently solved \[Ecoffet et al., 2021\]. [[#^figure-2|Figure 2]] shows the starting observation $o_{0}$ for the first level. This section culminates with [[#^4-3-tendencies-for|section 4.3]], where we argue that increasingly powerful rl training processes will cause increasing retargetability via the reward function, which in turn causes increasingly strong decision-making tendencies.

##### Terminology. ^terminology

Retargetability is a property of the policy training process, and power-seeking is a property of the trained policy. More precisely, the policy training process takes as input a parameterization $\theta$ and outputs a probability distribution over policies. For each trained policy drawn from this distribution, the environment, starting state, and the drawn policy jointly specify a probability distribution over trajectories. Therefore, the training process associates each parameterization $\theta$ with the mixture distribution $P$ over trajectories (with the mixture taken over the distribution of trained policies).

A policy training process can be simply retargeted from one trajectory set $A$ to another trajectory set $B$ when there exists a permutation $\phi\in S_{d}$ such that, for every $\theta$ for which $P(A\mid\theta)>P(B\mid\theta)$, we have $P(A\mid\phi\cdot\theta)<P(B\mid\phi\cdot\theta)$. As in Turner et al. \[2021\], a trained policy $\pi$ _seeks power_ when $\pi$’s actions navigate to states with high average optimal value (with the average taken over a wide range of reward functions). Generally, high-power states are able to reach a wide range of other states, and so allow bigger option sets $B$ (compared to the options $A$ available without seeking power).

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/turner-parametrically-retargetable-decision-makers-tend-to-seek-power-img5-89a4d3e6.png)

Figure 2: Montezuma’s Revenge (mr) has state space $\mathcal{S}$ and observation space $\mathcal{O}$. The agent has actions $\mathcal{A}\mathrel{\mathop{\ordinarycolon}}=\left\{\uparrow,\downarrow,\leftarrow,\rightarrow,\texttt{jump}\right\}$. At the initial state $s_{0}$, $\uparrow$ does nothing, $\downarrow$ descends the ladder, $\leftarrow$ and $\rightarrow$ move the agent on the platform, and jump is self-explanatory. The agent clears the temple while collecting four kinds of items: keys, swords, torches, and amulets. Under the standard environmental reward function, the agent receives points for acquiring items (such as the key on the left), opening doors, and—ultimately—completing the level. ^figure-2

### 4.1 Tendencies for initial action selection ^4-1-tendencies-for

We will be considering the actions chosen and trajectories induced by a range of decision-making procedures. For warm-up, we will explore what initial action tends to be selected by decision-makers. Let $A\coloneqq\{\downarrow\},B\mathrel{\mathop{\ordinarycolon}}=\{\leftarrow,\rightarrow,\texttt{jump},\uparrow\}$ partition the action set $\mathcal{A}$. Consider a decision-making procedure $f$ which takes as input a targeting parameter $\theta\in\Theta$, and also an initial action $a\in\mathcal{A}$, and returns the probability that $a$ is the first action. Intuitively, since $B$ contains more actions than $A$, perhaps some class of decision-making procedures tends to take an action in $B$ rather than one in $A$.

mr’s initial-action situation is analogous to the Pac-Man example. In that example, if the decision-making procedure $p$ can be retargeted from terminal state set $A$ (the ghost) to set $B$ (the fruit), then $p$ tends to select a state from $B$ under most of its parameter settings $\theta$. Similarly, in mr, if the decision-making procedure $f$ can be retargeted from action set $A$ to action set $B$, then $f$ tends to take actions in $B$ for most of its parameter settings $\theta$. Consider several ways of choosing an initial action in mr.

**Random action selection.** $p_{\text{rand}}\coloneqq(\{a\}\mid\theta)\mapsto\frac{1}{5}$ uniformly randomly chooses an action from $\mathcal{A}$, ignoring the parameter input. Since $\forall\theta\in\Theta\mathrel{\mathop{\ordinarycolon}}p_{\text{rand}}(B\mid\theta)=\frac{4}{5}>\frac{1}{5}=p_{\text{rand}}(A\mid\theta)$, _all_ parameter inputs produce a greater chance of $B$ than of $A$, so $p_{\text{rand}}$ is (trivially) retargetable from $A$ to $B$.

**Always choosing the same action.** $p_{\text{stubborn}}$ always chooses $\downarrow$. Since $\forall\theta\in\Theta\mathrel{\mathop{\ordinarycolon}}p_{\text{stubborn}}(A\mid\theta)=1>0=p_{\text{stubborn}}(B\mid\theta)$, _all_ parameter inputs produce a greater chance of $A$ than of $B$. $p_{\text{stubborn}}$ is not retargetable from $A$ to $B$.

**Greedily optimizing state-action reward.** Let $\Theta\coloneqq\mathbb{R}^{\mathcal{S}\times\mathcal{A}}$ be the space of state-action reward functions. Let $p_{\text{max}}$ greedily maximize initial state-action reward, breaking ties uniformly randomly.

We now check that $p_{\text{max}}$ is retargetable from $A$ to $B$. Suppose $\theta^{*}\in\Theta$ is such that $p_{\text{max}}(A\mid\theta^{*})>p_{\text{max}}(B\mid\theta^{*})$. Then among the initial action rewards, $\theta^{*}$ assigns strictly maximal reward to $\downarrow$, and so $p_{\text{max}}(A\mid\theta^{*})=1$. Let $\phi$ swap the reward for the $\downarrow$ and jump actions. Then $\phi\cdot\theta^{*}$ assigns strictly maximal reward to jump. This means that $p_{\text{max}}(A\mid\phi\cdot\theta^{*})=0<1=p_{\text{max}}(B\mid\phi\cdot\theta^{*})$, satisfying [[#^definition-3-3-simply-retargetable|definition 3.3]]. Then apply [[#^proposition-3-4-simply-retargetable|Proposition 3.4]] to conclude that $p_{\text{max}}(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{1}p_{\text{max}}(A\mid\theta)$.

In fact, appendix [[#^appendix-a-retargetability-over|A]] shows that $p_{\text{max}}$ is $(\Theta,A\overset{4}{\to}B)$\-retargetable ([[#^definition-3-5-multiply|definition 3.5]]), and so $p_{\text{max}}(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{4}p_{\text{max}}(A\mid\theta)$. The reasoning is more complicated, but the rule of thumb is: When decisions are made based on the reward of outcomes, then a proportionally larger set $B$ of outcomes induces proportionally strong retargetability, which induces proportionally strong orbit-level incentives.

**Learning an exploitation policy.** Suppose we run a bandit algorithm which tries different initial actions, learns their rewards, and produces an exploitation policy which maximizes estimated reward. The algorithm uses $\epsilon$\-greedy exploration and trains for $T$ trials. Given fixed $T$ and $\epsilon$, $p_{\text{bandit}}(A\mid\theta)$ returns the probability that an exploitation policy is learned which chooses an action in $A$; likewise for $p_{\text{bandit}}(B\mid\theta)$.

Here is a heuristic argument that $p_{\text{bandit}}$ is retargetable. Since the reward is deterministic, the exploitation policy will choose an optimal action if the agent has tried each action at least once, which occurs with a probability approaching $1$ exponentially quickly in the number of trials $T$. Then when $T$ is large, $p_{\text{bandit}}$ approximates $p_{\text{max}}$, which is retargetable. Therefore, perhaps $p_{\text{bandit}}$ is also retargetable. A more careful analysis in appendix [[#^c-1-action-selection|C.1]] reveals that $p_{\text{bandit}}$ is 4-retargetable from $A$ to $B$, and so $p_{\text{bandit}}(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{4}p_{\text{bandit}}(A\mid\theta)$.

### 4.2 Tendencies for maximizing reward over the final observation ^4-2-tendencies-for

When evaluating the performance of an algorithm in mr, we do not focus on the agent’s initial action. Rather, we focus on the longer-term consequences of the agent’s actions, such as whether the agent leaves the first room. To begin reasoning about such behavior, the reader must distinguish between different kinds of retargetability.

Suppose the agent will die unless they choose action $\downarrow$ at the initial state $s_{0}$ ([[#^figure-2|Figure 2]]). By [[#^4-1-tendencies-for|section 4.1]], action-retargetable decision-making procedures tend to choose actions besides $\downarrow$. On the other hand, Turner et al. \[2021\] showed that most reward functions make it reward-optimal to stay alive (in this situation, by choosing $\downarrow$). However, in that situations, the optimal policies are not retargetable across the agent’s _immediate_ choice of action, but rather across future consequences (_i_._e_., which room the agent ends up in).

With that in mind, we now analyze how often decision-makers leave the first room of mr.[^note-4] Decision-making functions $\mathrm{decide}(\theta)$ produce a probability distribution over policies $\pi\in\Pi$, which are rolled out from the initial state $s_{0}$ to produce observation-action trajectories $\tau=o_{0}a_{0}\ldots o_{T}a_{T}\ldots$, where $T$ is the rollout length we are interested in. Let $O_{T\text{-reach}}$ be the set of observations reachable starting from state $s_{0}$ and acting for $T$ time steps, let $O_{\text{leave}}\subseteq O_{T\text{-reach}}$ be those observations which can only be realized by leaving, and let $O_{\text{stay}}\coloneqq O_{T\text{-reach}}\setminus O_{\text{leave}}$. Consider the probability that $\mathrm{decide}$ realizes some subset of observations $X\subseteq\mathcal{O}$ at step $T$:

$$
p_{\mathrm{decide}}(X\mid\theta)\coloneqq\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in X\right). \tag{3}
$$

Let $\Theta\coloneqq\mathbb{R}^{\mathcal{O}}$ be the set of reward functions mapping observations $o\in\mathcal{O}$ to real numbers, and let $T\coloneqq 1{,}000$. We first consider the previous decision functions, since they are simple to analyze.

$\mathrm{decide}_{\text{rand}}$ randomly chooses a final observation $o$ which can be realized at step 1,000, and then chooses some policy which realizes $o$.[^note-5] $\mathrm{decide}_{\text{rand}}$ induces an $p_{\text{rand}}$ defined by eq. 3. As before, $p_{\text{rand}}$ tends to leave the room under _all_ parameter inputs.

$\mathrm{decide}_{\max}(\theta)$ produces a policy which maximizes the reward of the observation at step 1,000 of the rollout. Since mr is deterministic, we discuss _which_ observation $\mathrm{decide}_{\max}(\theta)$ realizes. In a stochastic setting, the decision-maker would choose a policy realizing some probability distribution over step-$T$ observations, and the analysis would proceed similarly.

Here is the semi-formal argument for $p_{\text{max}}$’s retargetability. There are combinatorially more game-screens visible if the agent leaves the room (due to _e_._g_., more point combinations, more inventory layouts, more screens outside of the first room). In other words, $\left|O_{\text{stay}}\right|\ll\left|O_{\text{leave}}\right|$. There are more ways for the selected observation to require leaving the room, than not. Thus, $p_{\text{max}}$ is extremely retargetable from $O_{\text{stay}}$ to $O_{\text{leave}}$.

Detailed analysis in [[#^c-2-observation-reward|section C.2]] confirms that $p_{\text{max}}(O_{\text{leave}}\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}p_{\text{max}}(O_{\text{stay}}\mid\theta)$ for the large $n\coloneqq\lfloor\frac{\left|O_{\text{leave}}\right|}{\left|O_{\text{stay}}\right|}\rfloor$, which we show implies that $p_{\text{max}}$ tends to leave the room.

### 4.3 Tendencies for rl on featurized reward over the final observation ^4-3-tendencies-for

In the real world, we do not run $p_{\text{max}}$, which can be computed via $T$\-depth exhaustive tree search in order to find and induce a maximal-reward observation $o_{T}$. Instead, we use reinforcement learning. Better rl algorithms seem to be more retargetable _because_ of their greater capability to explore.[^note-6]

##### Exploring the first room. ^exploring-the-first-room

Consider a featurized reward function over observations $\theta\in\mathbb{R}^{\mathcal{O}}$, which provides an end-of-episode return signal which adds a fixed reward for each item displayed in the observation (_e_._g_., 5 reward for a sword, 2 reward for a key). Consider a coefficient vector $\alpha\in\mathbb{R}^{4}$, with each entry denoting the value of an item, and $\textrm{feat}\mathrel{\mathop{\ordinarycolon}}\mathcal{O}\to\mathbb{R}^{4}$ maps observations to feature vectors which tally the items in the agent’s inventory. A reinforcement learning algorithm $\mathrm{Alg}$ uses this return signal to update a fixed-initialization policy network. Then $p_{\mathrm{Alg}}(O_{\text{leave}}\mid\theta)$ returns the probability that $\mathrm{Alg}$ trains an policy whose step-$T$ observation required the agent to leave the initial room.

The retargetability ([[#^definition-3-3-simply-retargetable|definition 3.3]]) of $\mathrm{Alg}$ is closely linked to the quality of $\mathrm{Alg}$ as an rl training procedure. For example, as explained in [[#^c-4-reasoning-for|section C.4]], Mnih et al. \[2015\]’s dqn isn’t good enough to train policies which leave the first room of mr, and so dqn (trivially) cannot be retargetable _away_ from the first room via the reward function. There isn’t a single featurized reward function for which dqn visits other rooms, and so we can’t have $\alpha$ such that $\phi\cdot\alpha$ retargets the agent to $O_{\text{leave}}$. dqn isn’t good enough at exploring.

More formally, in this situation, $\mathrm{Alg}$ is retargetable if there exists a permutation $\phi\in S_{4}$ such that whenever $\alpha\in\Theta\coloneqq\mathbb{R}^{4}$ induces the learned policies to stay in the room ($p_{\mathrm{Alg}}(O_{\text{stay}}\mid\alpha)>p_{\mathrm{Alg}}(O_{\text{leave}}\mid\alpha)$), $\phi\cdot\alpha$ makes $\mathrm{Alg}$ train policies which leave the room ($p_{\mathrm{Alg}}(O_{\text{stay}}\mid\alpha)<p_{\mathrm{Alg}}(O_{\text{leave}}\mid\alpha)$).

##### Exploring four rooms. ^exploring-four-rooms

Suppose algorithm $\mathrm{Alg}^{\prime}$ can explore _e_._g_., the first three rooms to the right of the initial room (shown in [[#^figure-2|Figure 2]]), and consider any reward coefficient vector $\alpha\in\Theta$ which assigns unique positive weight to each item. In particular, unique positive weights rule out constant reward vectors, in which case inductive bias would produce agents which do not leave the first room.

If the agent stays in the initial room, it can induce inventory states {empty, 1key}. If the agent explores the three extra rooms, it can also induce {1sword, 1sword&1key} (see [[#^figure-3|Figure 3]] in Appendix [[#^c-2-observation-reward|C.2]]). Since $\alpha$ is positive, it is never optimal to finish the episode empty-handed. Therefore, if the $\mathrm{Alg}^{\prime}$ policy stays in the first room, then $\alpha$’s feature coefficients must satisfy $\alpha_{\text{key}}>\alpha_{\text{sword}}$. Otherwise, $\alpha_{\text{key}}<\alpha_{\text{sword}}$ (by assumption of unique item reward coefficients); in this case, the agent would leave and acquire the sword (since we assumed it knows how to do so). Then by switching the reward for the key and the sword, we retarget $\mathrm{Alg}^{\prime}$ to go get the sword. $\mathrm{Alg}^{\prime}$ is simply-retargetable away from the first room, _because_ it can explore enough of the environment.

##### Exploring the entire level. ^exploring-the-entire-level

Algorithms like go-explore \[Ecoffet et al., 2021\] are probably good at exploring even given sparse featurized reward. Therefore, go-explore is even more retargetable in this setting, because it is more able to explore and discover the breadth of options (final inventory counts) available to it, and remember how to navigate to them. Furthermore, sufficiently powerful planning algorithms should likewise be retargetable in a similar way, insofar as they can reliably find high-scoring item configurations.

We speculate that increasingly “impressive” algorithms (whether rl training or planning) are often more impressive because they can allow retargeting the agent’s final behavior from one kind of outcome, to another. Just as go-explore seems highly retargetable while dqn does not, we expect increasingly impressive algorithms to be increasingly retargetable—whether over actions in a bandit problem, or over the final observation in an rl episode.

## 5 Retargetability can imply power-seeking tendencies ^5-retargetability-can-imply

### 5.1 Generalizing the power-seeking theorems for Markov decision processes ^5-1-generalizing-the

Turner et al. \[2021\] considered finite mdps in which decision-makers took as input a reward function over states ($\mathbf{r}\in\mathbb{R}^{\left|\mathcal{S}\right|}$) and selected an optimal policy for that reward function. They considered the state visit distributions $\mathbf{f}\in\mathcal{F}(s)$, which basically correspond to the trajectories which the agent could induce starting from state $s$. For $F\subseteq\mathcal{F}(s)$, $p_{\max}(F\mid\mathbf{r})$ returns $1$ if an element of $F$ is optimal for reward function $\mathbf{r}$, and $0$ otherwise. They showed situations where a larger set of distributions $F_{\text{large}}$ tended to be optimal over a smaller set: $p_{\max}(F_{\text{large}}\mid\mathbf{r})\geq_{\text{{most}}\text{: }\mathbb{R}^{\left|\mathcal{S}\right|}}^{1}p_{\max}(F_{\text{small}}\mid\mathbf{r})$. For example, in Pac-Man, most reward functions make it optimal to stay alive for at least one time step: $p_{\max}(F_{\text{survival}}\mid\mathbf{r})\geq_{\text{{most}}\text{: }\mathbb{R}^{\left|\mathcal{S}\right|}}^{1}p_{\max}(F_{\text{instant death}}\mid\mathbf{r})$. Turner et al. \[2021\] showed that optimal policies tend to seek power by keeping options open and staying alive. Appendix [[#^appendix-d-lower-bounds|D]] provides a quantitative generalization of Turner et al. \[2021\]’s results on optimal policies.

Throughout this paper, we abstracted their arguments away from finite mdps and reward-optimal decision-making. Instead, parametrically retargetable decision-makers tend to seek power: [[#^proposition-a-11-orbit|Proposition A.11]] shows that a wide range of decision-making procedures are retargetable over outcomes, and [[#^theorem-a-13-orbit|Theorem A.13]] demonstrates the retargetability of _any_ decision-making which is determined by the expected utility of outcomes. In particular, these results apply straightforwardly to mdps.

### 5.2 Better rl algorithms tend to be more retargetable ^5-2-better-rl

Reinforcement learning algorithms are practically useful insofar as they can train an agent to accomplish some task (_e_._g_., cleaning a room). A good rl algorithm is relatively task-agnostic (_e_._g_., is not restricted to only training policies which clean rooms). Task-agnosticism suggests retargetability across desired future outcomes / task completions.

In mr, suppose we instead give the agent $1$ reward for the initial state, and $0$ otherwise. Any reasonable reinforcement learning procedure will just learn to stay put (which is the optimal policy). However, consider whether we can retarget the agent’s policy to beat the game, by swapping the initial state reward with the end-game state reward. Most present-day rl algorithms are not good enough to solve such a sparse game, and so are not retargetable in this sense. But an agent which did enough exploration would also learn a good policy for the permuted reward function. Such an effective training regime could be useful for solving real-world tasks. Many researchers aim to develop effective training regimes.

Our results suggest that once rl capabilities reach a certain level, trained agents will tend to seek power in the real world. Presently, it is not dangerous to train an agent to complete a task—such an agent will not be able to complete its task by staying activated against the designers’ wishes. The present lack of danger is not because optimal policies do not have self-preservation tendencies—they do \[Turner et al., 2021\]. Rather, the lack of danger reflects the fact that present-day rl agents cannot learn such complex action sequences _at all_. Just as the Montezuma’s Revenge agent had to be sufficiently competent to be retargetable from initial-state reward to game-complete reward, real-world agents have to be sufficiently intelligent in order to be retargetable from outcomes which don’t require power-seeking, to those which do require power-seeking.

Here is some speculation. After training an rl agent to a high level of capability, the agent may be optimizing internally represented goals over its model of the environment \[Hubinger et al., 2019\]. Furthermore, we think that different reward parameter settings would train different internal goals into the agent. To make an analogy, changing a person’s reward circuitry would presumably reinforce them for different kinds of activities and thereby change their priorities. In this sense, trained real-world agents may be retargetable towards power-requiring outcomes via the reward function parameter setting. Insofar as this speculation holds, our theory predicts that advanced reinforcement learning at scale will—for most settings of the reward function—train policies which tend to seek power.

## 6 Discussion ^6-discussion

In [[#^3-formal-notions-of|section 3]], we formalized a notion of parametric retargetability and stated several key results. While our results are broadly applicable, further work is required to understand the implications for ai.

### 6.1 Prior work ^6-1-prior-work

In this work, we do not motivate the risks from ai power-seeking. We refer the reader to _e_._g_., Carlsmith \[2021\]. As explained in [[#^5-1-generalizing-the|section 5.1]], Turner et al. \[2021\] show that, given certain environmental symmetries in an mdp, the optimal-policy-producing algorithm $f$(state visitation distribution set, state-based reward function) is 1-retargetable via the reward function, from smaller to larger sets of environmental options. [[#^appendix-a-retargetability-over|Appendix A]] shows that optimality is not required, and instead a wide range of decision-making procedures satisfy the retargetability criterion. Furthermore, we generalize from 1-retargetability to $n$\-fold-retargetability whenever option set $B$ contains “$n$ copies” of set $A$ ([[#^definition-a-7-containment|definition A.7]] in [[#^appendix-a-retargetability-over|appendix A]]).

### 6.2 Future work and limitations ^6-2-future-work

We currently have analyzed planning- and reinforcement learning-based settings. However, results such as [[#^theorem-3-6-multiply|Theorem 3.6]] might in some way apply to the training of other machine learning networks. Furthermore, while [[#^theorem-3-6-multiply|Theorem 3.6]] does not assume a finite environment, we currently do not see how to apply that result to _e_._g_., infinite-state partially observable Markov decision processes.

[[#^4-decision-making-tendencies-in|Section 4]] semi-formally analyzes decision-making incentives in the mr video game, leaving the proofs to [[#^appendix-c-detailed-analyses|appendix C]]. However, these proofs are several pages long. Perhaps additional lemmas can allow quick proof of orbit-level incentives in situations relevant to real-world decision-makers.

Consider a sequence of decision-making functions $p_{t}\mathrel{\mathop{\ordinarycolon}}\{A,B\}\times\Theta\to\mathbb{R}$ which converges pointwise to some $p$ such that $p(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}p(A\mid\theta)$. We expect that under rather mild conditions, $\exists T\mathrel{\mathop{\ordinarycolon}}\forall t\geq T\mathrel{\mathop{\ordinarycolon}}p_{t}(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}p_{t}(A\mid\theta)$. As a corollary, for any decision-making procedure $p_{t}$ which runs for $t$ time steps and satisfies $\lim_{t\to\infty}p_{t}=p$, the function $p_{t}$ will have decision-making incentives after finite time. For example, value iteration (vi) eventually finds an optimal policy \[Puterman, 2014\], and optimal policies tend to seek power \[Turner et al., 2021\]. Therefore, this conjecture would imply that if vi is run for some long but finite time, it tends to produce power-seeking policies. More interestingly, the result would allow us to reason about the effect of _e_._g_., randomly initializing parameters (in vi, the tabular value function at $t=0$). The effect of random initialization washes out in the limit of infinite time, so we would still conclude the presence of finite-time power-seeking incentives.

Our results do not _prove_ that we will build unaligned ai agents which seek power over the world. Here are a few situations in which our results are not concerning or not applicable.

1. The ai is aligned with human interests. For example, we want a robotic cartographer to prevent itself from being deactivated. However, the ai alignment problem is not yet understood for highly intelligent agents \[Russell, 2019\].
2. The ai’s decision-making is not retargetable ([[#^definition-3-5-multiply|definition 3.5]]).
3. The ai’s decision-making is retargetable over _e_._g_., actions ([[#^4-1-tendencies-for|section 4.1]]) instead of over final outcomes ([[#^4-2-tendencies-for|section 4.2]]). This retargetability seems less concerning, but also less practically useful.

### 6.3 Conclusion ^6-3-conclusion

We introduced the concept of retargetability and showed that retargetable decision-makers often make similar instrumental choices. We applied these results in the Montezuma’s Revenge (mr) video game, showing how increasingly advanced reinforcement learning algorithms correspond to increasingly retargetable agent decision-making. Increasingly retargetable agents make increasingly similar instrumental decisions—_e_._g_., leaving the initial room in mr, or staying alive in Pac-Man. In particular, these decisions will often correspond to gaining power and keeping options open \[Turner et al., 2021\]. Our theory suggests that when rl training processes become sufficiently advanced, the trained agents will tend to seek power over the world. This theory suggests a safety risk. We hope for future work on this theory so that the field of ai can understand the relevant safety risks _before_ the field trains power-seeking agents.

## Broader impacts ^broader-impacts

Our theory of orbit-level tendencies constitutes basic mathematical research into the decision-making tendencies of certain kinds of agents. We hope that this theory will prevent negative impacts from unaligned power-seeking ai. We do not anticipate that our work will have negative impact.

:::hide
## Acknowledgements ^acknowledgements

We thank Irene Tematelewo, Colin Shea-Blymyer, and our anonymous reviewers for feedback. We thank Justis Mills for proofreading.

## References ^references

-   Baker et al. \[2007\] Chris L Baker, Joshua B Tenenbaum, and Rebecca R Saxe. Goal inference as inverse planning. In _Proceedings of the Annual Meeting of the Cognitive Science Society_, volume 29, 2007.
-   Bostrom \[2014\] Nick Bostrom. _Superintelligence_. Oxford University Press, 2014.
-   Carey \[2019\] Ryan Carey. How useful is quantilization for mitigating specification gaming? 2019.
-   Carlsmith \[2021\] Joe Carlsmith. Is power-seeking AI an existential risk?, 2021. URL [https://www.alignmentforum.org/posts/cCMihiwtZx7kdcKgt/comments-on-carlsmith-s-is-power-seeking-ai-an-existential](https://www.alignmentforum.org/posts/cCMihiwtZx7kdcKgt/comments-on-carlsmith-s-is-power-seeking-ai-an-existential).
-   Ecoffet et al. \[2021\] Adrien Ecoffet, Joost Huizinga, Joel Lehman, Kenneth O Stanley, and Jeff Clune. First return, then explore. _Nature_, 590(7847):580–586, 2021.
-   Hubinger et al. \[2019\] Evan Hubinger, Chris van Merwijk, Vladimir Mikulik, Joar Skalse, and Scott Garrabrant. Risks from learned optimization in advanced machine learning systems, 2019. URL [https://arxiv.org/abs/1906.01820](https://arxiv.org/abs/1906.01820).
-   Mnih et al. \[2015\] Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Andrei A Rusu, Joel Veness, Marc G Bellemare, Alex Graves, Martin Riedmiller, Andreas K Fidjeland, Georg Ostrovski, et al. Human-level control through deep reinforcement learning. _Nature_, 518(7540):529–533, 2015.
-   Nair et al. \[2015\] Arun Nair, Praveen Srinivasan, Sam Blackwell, Cagdas Alcicek, Rory Fearon, Alessandro De Maria, Vedavyas Panneershelvam, Mustafa Suleyman, Charles Beattie, Stig Petersen, et al. Massively parallel methods for deep reinforcement learning. _arXiv preprint arXiv:1507.04296_, 2015.
-   Puterman \[2014\] Martin L Puterman. _Markov decision processes: Discrete stochastic dynamic programming_. John Wiley & Sons, 2014.
-   Russell \[2019\] Stuart Russell. _Human compatible: Artificial intelligence and the problem of control_. Viking, 2019.
-   Simon \[1956\] Herbert A Simon. Rational choice and the structure of the environment. _Psychological review_, 63(2):129, 1956.
-   Sutton and Barto \[1998\] Richard S Sutton and Andrew G Barto. _Reinforcement learning: an introduction_. MIT Press, 1998.
-   Taylor \[2016\] Jessica Taylor. Quantilizers: A safer alternative to maximizers for limited optimization. In _AAAI Workshop: AI, Ethics, and Society_, 2016.
-   Turner \[2022\] Alexander Matt Turner. Reward is not the optimization target, 2022. URL [https://www.alignmentforum.org/posts/pdaGN6pQyQarFHXF4/reward-is-not-the-optimization-target](https://www.alignmentforum.org/posts/pdaGN6pQyQarFHXF4/reward-is-not-the-optimization-target).
-   Turner et al. \[2021\] Alexander Matt Turner, Logan Smith, Rohin Shah, Andrew Critch, and Prasad Tadepalli. Optimal policies tend to seek power. In _Advances in Neural Information Processing Systems_, 2021.
:::

:::callout {title="Appendix" collapse="closed"}
## Appendix A Retargetability over outcome lotteries ^appendix-a-retargetability-over

Suppose we are interested in $d$ outcomes. Each outcome could be the visitation of an mdp state, or a trajectory, or the receipt of a physical item. In the Pac-Man example of [[#^2-statistical-tendencies-for|section 2]], $d=3$ states. The agent can induce each outcome with probability $1$, so let $\mathbf{e}_{o}\in\mathbb{R}^{3}$ be the standard basis vector with probability $1$ on outcome $o$ and $0$ elsewhere. Then the agent chooses among outcome lotteries $C\coloneqq\left\{\mathbf{e}_{\text{ghost}},\mathbf{e}_{\text{apple}},\mathbf{e}_{\text{cherry}}\right\}$, which we partition into $A\coloneqq\left\{\mathbf{e}_{\text{ghost}}\right\}$ and $B\coloneqq\left\{\mathbf{e}_{\text{apple}},\mathbf{e}_{\text{cherry}}\right\}$.

###### Definition A.1 (Outcome lotteries). ^definition-a-1-outcome

A unit vector $\mathbf{x}\in\mathbb{R}^{d}$ with non-negative entries is an _outcome lottery_.[^note-7]

Many decisions are made consequentially: based on the consequences of the decision, on what outcomes are brought about by an act. For example, in a deterministic Atari game, a policy induces a trajectory. A reward function and discount rate tuple $(R,\gamma)$ assigns a _return_ to each state trajectory $\tau=s_{0},s_{1},\ldots$: $G(\tau)=\sum_{i=0}^{\infty}\gamma^{i}R(s_{i})$. The relevant outcome lottery is the discounted visit distribution over future states in an Atari game, and policies are optimal or not depending on which outcome lottery is induced by the policy.

###### Definition A.2 (Optimality indicator function). ^definition-a-2-optimality

Let $X,C\subsetneq\mathbb{R}^{d}$ be finite, and let $\mathbf{u}\in\mathbb{R}^{d}$. $\mathrm{IsOptimal}\left(X\mid C,\mathbf{u}\right)$ returns $1$ if $\max_{\mathbf{x}\in X}\mathbf{x}^{\top}\mathbf{u}\geq\max_{\mathbf{c}\in C}\mathbf{c}^{\top}\mathbf{u}$, and $0$ otherwise.

We consider decision-making procedures which take in a targeting parameter $\mathbf{u}$. For example, the column headers of [[#^table-2a|Table 2(a)]] show the 6 permutations of the utility function $u(\text{ghost})\coloneqq 10,u(\text{apple})\coloneqq 5,u(\text{cherry})\coloneqq 0$, representable as a vector $\mathbf{u}\in\mathbb{R}^{3}$.

$\mathbf{u}$ can be permuted as follows. The outcome permutation $\phi\in S_{d}$ inducing an $d\times d$ permutation matrix $\mathbf{P}_{\phi}$ in row representation: $(\mathbf{P}_{\phi})_{ij}=1$ if $i=\phi(j)$ and $0$ otherwise. [[#^table-2a|Table 2(a)]] shows that for a given utility function, $\frac{2}{3}$ of its orbit agrees that $B$ is strictly optimal over $A$.

Table 2: Orbit-level incentives across 4 decision-making functions. ^table-2

| Utility function $\mathbf{u}^{\prime}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{10}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{10}$ |
| --- | --- | --- | --- | --- | --- | --- |
| $\mathrm{IsOptimal}\left(\left\{\mathbf{e}_{\text{ghost}},\mathbf{e}_{\text{apple}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $1$ | $1$ | $1$ | $0$ | $1$ | $0$ |
| $\mathrm{IsOptimal}\left(\left\{\mathbf{e}_{\text{cherry}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $0$ | $0$ | $0$ | $1$ | $0$ | $1$ |

(a) Dark gray columns indicate utility function permutations $\mathbf{u}^{\prime}$ for which $\mathrm{IsOptimal}\left(B\mid C,\mathbf{u}^{\prime}\right)>\mathrm{IsOptimal}\left(A\mid C,\mathbf{u}^{\prime}\right)$, while white indicates that the opposite strict inequality holds. ^table-2a

| Utility function $\mathbf{u}^{\prime}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{10}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{10}$ |
| --- | --- | --- | --- | --- | --- | --- |
| $\mathrm{AntiOpt}\left(\left\{\mathbf{e}_{\text{ghost}},\mathbf{e}_{\text{apple}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $0$ | $1$ | $0$ | $1$ | $1$ | $1$ |
| $\mathrm{AntiOpt}\left(\left\{\mathbf{e}_{\text{cherry}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $1$ | $0$ | $1$ | $0$ | $0$ | $0$ |

(b) Utility-minimizing outcome selection probability. ^table-2b

| Utility function $\mathbf{u}^{\prime}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{10}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{10}$ |
| --- | --- | --- | --- | --- | --- | --- |
| $\mathrm{Boltzmann}_{1}\left(\left\{\mathbf{e}_{\text{ghost}},\mathbf{e}_{\text{apple}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $1$ | $.993$ | $1$ | $.007$ | $.993$ | $.007$ |
| $\mathrm{Boltzmann}_{1}\left(\left\{\mathbf{e}_{\text{cherry}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $.000$ | $.007$ | $.000$ | $.993$ | $.007$ | $.993$ |

(c) Boltzmann selection probabilities for $T=1$, rounded to three significant digits.

| Utility function $\mathbf{u}^{\prime}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{10},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{0}$ | $\overset{\text{ghost}}{5},\!\overset{\text{apple}}{0},\!\overset{\text{cherry}}{10}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{10},\!\overset{\text{cherry}}{5}$ | $\overset{\text{ghost}}{0},\!\overset{\text{apple}}{5},\!\overset{\text{cherry}}{10}$ |
| --- | --- | --- | --- | --- | --- | --- |
| $\mathrm{Satisfice}_{3}\left(\left\{\mathbf{e}_{\text{ghost}},\mathbf{e}_{\text{apple}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $1$ | $.5$ | $1$ | $.5$ | $.5$ | $.5$ |
| $\mathrm{Satisfice}_{3}\left(\left\{\mathbf{e}_{\text{cherry}}\right\}\mid C,\mathbf{u}^{\prime}\right)$ | $0$ | $.5$ | $0$ | $.5$ | $.5$ | $.5$ |

(d) A satisficer uniformly randomly selects an outcome lottery with expected utility greater than or equal to the threshold $t$. Here, $t=3$. When $\mathrm{Satisfice}_{3}\left(\left\{\mathbf{e}_{\text{ghost}},\mathbf{e}_{\text{apple}}\right\}\mid C,\mathbf{u}^{\prime}\right)=\mathrm{Satisfice}_{3}\left(\left\{\mathbf{e}_{\text{cherry}}\right\}\mid C,\mathbf{u}^{\prime}\right)$, the column is colored medium gray. ^table-2d

Orbit-level incentives occur when an inequality holds for most permuted parameter choices $\mathbf{u}^{\prime}$. [[#^table-2a|Table 2(a)]] demonstrates an application of Turner et al. \[2021\]’s results: Optimal decision-making induces orbit-level incentives for choosing Pac-Man outcomes in $B$ over outcomes in $A$.

Furthermore, Turner et al. \[2021\] conjectured that “larger” $B$ will imply stronger orbit-level tendencies: If going right leads to 500 times as many options as going left, then right is better than left for at least 500 times as many reward functions for which the opposite is true. We prove this conjecture with [[#^theorem-d-11-quantitatively|Theorem D.11]] in appendix [[#^appendix-d-lower-bounds|D]].

However, orbit-level incentives do not require optimality. One clue is that the same results hold for anti-optimal agents, since anti-optimality/utility minimization of $\mathbf{u}$ is equivalent to maximizing $-\mathbf{u}$. [[#^table-2b|Table 2(b)]] illustrates that the same orbit guarantees hold in this case.

###### Definition A.3 (Anti-optimality indicator function). ^definition-a-3-anti-optimality

Let $X,C\subsetneq\mathbb{R}^{d}$ be finite, and let $\mathbf{u}\in\mathbb{R}^{d}$. $\mathrm{AntiOpt}\left(X\mid C,\mathbf{u}\right)$ returns $1$ if $\min_{\mathbf{x}\in X}\mathbf{x}^{\top}\mathbf{u}\leq\min_{\mathbf{c}\in C}\mathbf{c}^{\top}\mathbf{u}$, and $0$ otherwise.

Stepping beyond expected utility maximization/minimization, Boltzmann-rational decision-making selects outcome lotteries proportional to the exponential of their expected utility.

###### Definition A.4 (Boltzmann rationality \[Baker et al., 2007\]). ^definition-a-4-boltzmann

For $X\subseteq C$ and temperature $T>0$, let

$$
\mathrm{Boltzmann}_{T}\left(X\mid C,\mathbf{u}\right)\coloneqq\frac{\sum_{\mathbf{x}\in X}e^{T^{-1}\mathbf{x}^{\top}\mathbf{u}}}{\sum_{\mathbf{c}\in C}e^{T^{-1}\mathbf{c}^{\top}\mathbf{u}}}
$$

be the probability that some element of $X$ is Boltzmann-rational.

Lastly, orbit-level tendencies occur even under decision-making procedures which partially ignore expected utility and which “don’t optimize too hard.” Satisficing agents randomly choose an outcome lottery with expected utility exceeding some threshold. [[#^table-2d|Table 2(d)]] demonstrates that satisficing induces orbit-level tendencies.

###### Definition A.5 (Satisficing). ^definition-a-5-satisficing

Let $t\in\mathbb{R}$, let $X\subseteq C\subsetneq\mathbb{R}^{d}$ be finite. $\mathrm{Satisfice}_{t}\left(X,C\mid\mathbf{u}\right)\coloneqq\frac{\left|X\cap\left\{\mathbf{c}\in C\mid\mathbf{c}^{\top}\mathbf{u}\geq t\right\}\right|}{\left|\left\{\mathbf{c}\in C\mid\mathbf{c}^{\top}\mathbf{u}\geq t\right\}\right|}$ is the fraction of $X$ whose value exceeds threshold $t$. $\mathrm{Satisfice}_{t}\left(X,C\mid\mathbf{u}\right)$ evaluates to $0$ if the denominator equals $0$.

For each table, two-thirds of the utility permutations (columns) assign strictly larger values (shaded dark gray) to an element of $B\coloneqq\left\{\mathbf{e}_{\text{apple}},\mathbf{e}_{\text{cherry}}\right\}$ than to an element of $A\coloneqq\left\{\mathbf{e}_{\text{ghost}}\right\}$. For optimal, anti-optimal, Boltzmann-rational, and satisficing agents, [[#^proposition-a-11-orbit|Proposition A.11]] proves that these tendencies hold for all targeting parameter orbits.

### A.1 A range of decision-making functions are retargetable ^a-1-a-range

In mdps, Turner et al. \[2021\] consider _state visitation distributions_ which record the total discounted time steps spent in each environment state, given that the agent follows some policy $\pi$ from an initial state $s$. These visitation distributions are one kind of outcome lottery, with $d=\left|\mathcal{S}\right|$ the number of mdp states.

In general, we suppose the agent has an objective function $\mathbf{u}\in\mathbb{R}^{d}$ which maps outcomes to real numbers. In Turner et al. \[2021\], $\mathbf{u}$ was a state-based reward function (and so the outcomes were _states_). However, we need not restrict ourselves to the mdp setting.

To state our key results, we define several technical concepts which we informally used when reasoning about $A\coloneqq\left\{\mathbf{e}_{\text{ghost}}\right\}$ and $B\coloneqq\left\{\mathbf{e}_{\text{apple}},\mathbf{e}_{\text{cherry}}\right\}$.

###### Definition A.6 (Similarity of vector sets). ^definition-a-6-similarity

For $\phi\in S_{d}$ and $X\subseteq\mathbb{R}^{d}$, $\phi\cdot X\coloneqq\left\{\mathbf{P}_{\phi}\mathbf{x}\mid\mathbf{x}\in X\right\}$. $X^{\prime}\subseteq\mathbb{R}^{\left|\mathcal{S}\right|}$ _is similar to $X$_ when $\exists\phi\mathrel{\mathop{\ordinarycolon}}\phi\cdot X^{\prime}=X$. $\phi$ is an _involution_ if $\phi=\phi^{-1}$ (it either transposes states, or fixes them). $X$ _contains a copy of $X^{\prime}$_ when $X^{\prime}$ is similar to a subset of $X$ via an involution $\phi$.

###### Definition A.7 (Containment of set copies). ^definition-a-7-containment

Let $n$ be a positive integer, and let $A,B\subseteq\mathbb{R}^{d}$. We say that _$B$ contains $n$ copies of $A$_ when there exist involutions $\phi_{1},\ldots,\phi_{n}\in S_{d}$ such that $\forall i\mathrel{\mathop{\ordinarycolon}}\phi_{i}\cdot A\eqqcolon B_{i}\subseteq B$ and $\forall j\neq i\mathrel{\mathop{\ordinarycolon}}\phi_{i}\cdot B_{j}=B_{j}$.[^note-8]

$B\coloneqq\left\{\mathbf{e}_{\text{apple}},\mathbf{e}_{\text{cherry}}\right\}$ contains two copies of $A\coloneqq\left\{\mathbf{e}_{\text{ghost}}\right\}$ via $\phi_{1}\coloneqq\text{ghost}\leftrightarrow\text{apple}$ and $\phi_{2}\coloneqq\text{ghost}\leftrightarrow\text{cherry}$.

###### Definition A.8 (Targeting parameter distribution assumptions). ^definition-a-8-targeting

Results with $\mathcal{D}_{\text{any}}$ hold for any probability distribution over $\mathbb{R}^{d}$. Let $\mathfrak{D}_{\text{any}}\coloneqq\Delta(\mathbb{R}^{d})$. For a function $f\mathrel{\mathop{\ordinarycolon}}\mathbb{R}^{d}\mapsto\mathbb{R}$, we write $f(\mathcal{D}_{\text{any}})$ as shorthand for $\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{any}}}\left[f(\mathbf{u})\right]$.

The symmetry group on $d$ elements, $S_{d}$, acts on the set of probability distributions over $\mathbb{R}^{d}$.

###### Definition A.9 (Pushforward distribution of a permutation \[Turner et al., 2021\]). ^definition-a-9-pushforward

Let $\phi\in S_{d}$. $\phi\cdot\mathcal{D}_{\text{any}}$ is the pushforward distribution induced by applying the random vector $p(\mathbf{u})\coloneqq\mathbf{P}_{\phi}\mathbf{u}$ to $\mathcal{D}_{\text{any}}$.

###### Definition A.10 (Orbit of a probability distribution \[Turner et al., 2021\]). ^definition-a-10-orbit

The _orbit_ of $\mathcal{D}_{\text{any}}$ under the symmetric group $S_{d}$ is $S_{d}\cdot\mathcal{D}_{\text{any}}\coloneqq\{\phi\cdot\mathcal{D}_{\text{any}}\mid\phi\in S_{d}\}$.

Because $B$ contains 2 copies of $A$, there are “at least two times as many ways” for $B$ to be optimal, than for $A$ to be optimal. Similarly, $B$ is “at least two times as likely” to contain an anti-rational outcome lottery for generic utility functions. As demonstrated by [[#^table-2|Table 2]], the key idea is that “larger” sets (a set $B$ containing several _copies_ of set $A$) are more likely to be chosen under a wide range of decision-making criteria.

###### Proposition A.11 (Orbit incentives for different rationalities). ^proposition-a-11-orbit

_Let $A,B\subseteq C\subsetneq\mathbb{R}^{d}$ be finite, such that $B$ contains $n$ copies of $A$ via involutions $\phi_{i}$ such that $\phi_{i}\cdot C=C$._

1. _**Rational choice \[Turner et al., 2021\].**_

   $$
   \mathrm{IsOptimal}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathrm{IsOptimal}\left(A\mid C,\mathcal{D}_{\text{any}}\right).
   $$

2. _**Uniformly randomly choosing an optimal lottery.**_ _For_ $X\subseteq C$, let

   $$
   \mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)\coloneqq\frac{\left|\left\{\argmax_{\mathbf{c}\in C}\mathbf{c}^{\top}\mathbf{u}\right\}\cap X\right|}{\left|\left\{\argmax_{\mathbf{c}\in C}\mathbf{c}^{\top}\mathbf{u}\right\}\right|}.
   $$

   _Then_ $\mathrm{FracOptimal}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathrm{FracOptimal}\left(A\mid C,\mathcal{D}_{\text{any}}\right)$.

3. _**Anti-rational choice.**_ $\mathrm{AntiOpt}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathrm{AntiOpt}\left(A\mid C,\mathcal{D}_{\text{any}}\right)$.

4. _**Boltzmann rationality.**_

   $$
   \mathrm{Boltzmann}_{T}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathrm{Boltzmann}_{T}\left(A\mid C,\mathcal{D}_{\text{any}}\right).
   $$

5. _**Uniformly randomly drawing $k$ outcome lotteries and choosing the best.**_ _For_ $X\subseteq C$, $\mathbf{u}\in\mathbb{R}^{d}$_, and_ $k\geq 1$, let

   $$
   \textrm{best-of-}k(X,C\mid\mathbf{u})\coloneqq\mathbb{E}_{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\sim\text{unif}(C)}\left[\mathrm{FracOptimal}\left(X\cap\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\}\mid\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\},\mathbf{u}\right)\right].
   $$

   _Then_ $\textrm{best-of-}k(B\mid C,\mathcal{D}_{\text{any}})\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\textrm{best-of-}k(A\mid C,\mathcal{D}_{\text{any}})$.

6. _**Satisficing \[Simon, 1956\].**_ $\mathrm{Satisfice}_{t}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathrm{Satisfice}_{t}\left(A\mid C,\mathcal{D}_{\text{any}}\right)$.

7. _**Quantilizing over outcome lotteries \[Taylor, 2016\].**_ _Let_ $P$ _be the uniform probability distribution over_ $C$. For $X\subseteq C$, $\mathbf{u}\in\mathbb{R}^{d}$_, and_ $q\in(0,1]$_, let_ $Q_{q,P}(X\mid C,\mathbf{u})$ ([[#^definition-b-12-quantilization|definition B.12]]) return the probability that an outcome lottery in $X$ _is drawn from the top_ $q$\-quantile of $P$, sorted by expected utility under $\mathbf{u}$_. Then_ $Q_{q,P}(B\mid C,\mathbf{u})\geq_{\text{{most}}\text{: }\mathbb{R}^{d}}^{n}Q_{q,P}(A\mid C,\mathbf{u})$.

One retargetable class of decision-making functions are those which only account for the expected utilities of available choices.

###### Definition A.12 (EU-determined functions). ^definition-a-12-eu-determined

Let $\mathcal{P}\left(\mathbb{R}^{d}\right)$ be the power set of $\mathbb{R}^{d}$, and let $f\mathrel{\mathop{\ordinarycolon}}\prod_{i=1}^{m}\mathcal{P}\left(\mathbb{R}^{d}\right)\times\mathbb{R}^{d}\to\mathbb{R}$. $f$ is an _EU-determined function_ if there exists a family of functions $\left\{g^{\omega_{1},\ldots,\omega_{m}}\right\}$ such that

$$
f(X_{1},\ldots,X_{m}\mid\mathbf{u})=g^{|X_{1}|,\ldots,|X_{m}|}\left(\left[\mathbf{x}_{1}^{\top}\mathbf{u}\right]_{\mathbf{x}_{1}\in X_{1}},\ldots,\left[\mathbf{x}_{m}^{\top}\mathbf{u}\right]_{\mathbf{x}_{m}\in X_{m}}\right),
$$

where $[r_{i}]$ is the multiset of its elements $r_{i}$.

For example, let $X\subseteq C\subsetneq\mathbb{R}^{d}$ be finite, and consider utility function $\mathbf{u}\in\mathbb{R}^{d}$. A Boltzmann-rational agent is more likely to select outcome lotteries with greater expected utility. Formally, $\mathrm{Boltzmann}_{T}\left(X\mid C,\mathbf{u}\right)\coloneqq\sum_{\mathbf{x}\in X}\frac{e^{T\cdot\mathbf{x}^{\top}\mathbf{u}}}{\sum_{\mathbf{c}\in C}e^{T\cdot\mathbf{c}^{\top}\mathbf{u}}}$ depends only on the expected utility of outcome lotteries in $X$, relative to the expected utility of all outcome lotteries in $C$. Therefore, $\mathrm{Boltzmann}_{T}$ is a function of expected utilities. This is _why_ $\mathrm{Boltzmann}_{T}$ satisfies the $\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}$ relation.

###### Theorem A.13 (Orbit tendencies occur for EU-determined decision-making functions). ^theorem-a-13-orbit

_Let $A,B,C\subseteq\mathbb{R}^{d}$ be such that $B$ contains $n$ copies of $A$ via $\phi_{i}$ such that $\phi_{i}\cdot C=C$. Let $h\mathrel{\mathop{\ordinarycolon}}\prod_{i=1}^{2}\mathcal{P}\left(\mathbb{R}^{d}\right)\times\mathbb{R}^{d}\to\mathbb{R}$ be an EU-determined function, and let $p(X\mid\mathbf{u})\coloneqq h(X,C\mid\mathbf{u})$. Suppose that $p$ returns a probability of selecting an element of $X$ from $C$. Then $p(B\mid\mathbf{u})\geq_{\text{{most}}\text{: }\mathbb{R}^{d}}^{n}p(A\mid\mathbf{u})$._

The key takeaway is that decisions which are determined by expected utility are straightforwardly retargetable. By changing the targeting parameter hyperparameter, the decision-making procedure can be flexibly retargeted to choose elements of “larger” sets (in terms of set copies via [[#^definition-a-7-containment|definition A.7]]). Less abstractly, for many agent rationalities—ways of making decisions over outcome lotteries—it is generally the case that larger sets will more often be chosen over smaller sets.

For example, consider a Pac-Man playing agent choosing which environmental state cycle it should end up in. Turner et al. \[2021\] show that for most reward functions, average-reward maximizing agents will tend to stay alive so that they can reach a wider range of environmental cycles. However, our results show that average-reward _minimizing_ agents also exhibit this tendency, as do Boltzmann-rational agents who assign greater probability to higher-reward cycles. Any EU-based cycle selection method will—for most reward functions—tend to choose cycles which require Pac-Man to stay alive (at first).

## Appendix B Theoretical results ^appendix-b-theoretical-results

See [[#^definition-3-2-inequalities|3.2]]

###### Remark. ^remark

In stating their equivalent of [[#^definition-3-2-inequalities|definition 3.2]], Turner et al. \[2021\] define two functions $f_{1}(\theta)\coloneqq f(B\mid\theta)$ and $f_{2}(\theta)\coloneqq f(A\mid\theta)$ (both having type signature $f_{i}\mathrel{\mathop{\ordinarycolon}}\Theta\to\mathbb{R}$). For compatibility, proofs also use this notation.

###### Lemma B.1 (Limited transitivity of $\geq_{\text{most}}$). ^lemma-b-1-limited

_Let $f_{0},f_{1},f_{2},f_{3}\mathrel{\mathop{\ordinarycolon}}\Theta\to\mathbb{R}$, and suppose $\Theta$ is a subset of a set acted on by $S_{d}$. Suppose that $f_{1}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f_{2}(\theta)$ and $\forall\theta\in\Theta\mathrel{\mathop{\ordinarycolon}}f_{0}(\theta)\geq f_{1}(\theta)$ and $f_{2}(\theta)\geq f_{3}(\theta)$. Then $f_{0}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f_{3}(\theta)$._

###### Proof. ^proof

Let $\theta\in\Theta$ and let $\mathrm{Orbit}|_{\Theta,f_{a}>f_{b}}\left(\theta\right)\coloneqq\left\{\theta^{\prime}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid f_{a}(\theta^{\prime})>f_{b}(\theta^{\prime})\right\}$.

$$
\left|\mathrm{Orbit}|_{\Theta,f_{0}>f_{3}}\left(\theta\right)\right|\geq\left|\mathrm{Orbit}|_{\Theta,f_{1}>f_{2}}\left(\theta\right)\right| \\
\geq n\left|\mathrm{Orbit}|_{\Theta,f_{2}>f_{1}}\left(\theta\right)\right| \\
\geq n\left|\mathrm{Orbit}|_{\Theta,f_{3}>f_{0}}\left(\theta\right)\right|.
$$

For all $\theta^{\prime}\in\mathrm{Orbit}|_{\Theta,f_{1}>f_{2}}\left(\theta\right)$,

$$
f_{0}(\theta^{\prime})\geq f_{1}(\theta^{\prime})>f_{2}(\theta^{\prime})\geq f_{3}(\theta^{\prime})
$$

by assumption, and so

$$
\mathrm{Orbit}|_{\Theta,f_{1}>f_{2}}\left(\theta\right)\subseteq\mathrm{Orbit}|_{\Theta,f_{0}>f_{3}}\left(\theta\right).
$$

Therefore, eq. 5 follows. By assumption,

$$
\left|\mathrm{Orbit}|_{\Theta,f_{1}>f_{2}}\left(\theta\right)\right|\geq n\left|\mathrm{Orbit}|_{\Theta,f_{2}>f_{1}}\left(\theta\right)\right|;
$$

eq. 6 follows. For all $\theta^{\prime}\in\mathrm{Orbit}|_{\Theta,f_{2}>f_{1}}\left(\theta\right)$, our assumptions on $f_{0}$ and $f_{3}$ ensure that

$$
f_{0}(\theta^{\prime})\leq f_{1}(\theta^{\prime})<f_{3}(\theta^{\prime})\leq f_{2}(\theta^{\prime}),
$$

so

$$
\mathrm{Orbit}|_{\Theta,f_{3}>f_{0}}\left(\theta\right)\subseteq\mathrm{Orbit}|_{\Theta,f_{2}>f_{1}}\left(\theta\right).
$$

Then eq. 7 follows. By eq. 7, $f_{0}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f_{3}(\theta)$. ∎

###### Lemma B.2 (Order inversion for $\geq_{\text{most}}$). ^lemma-b-2-order

_Let $f_{1},f_{2}\mathrel{\mathop{\ordinarycolon}}\Theta\to\mathbb{R}$, and suppose $\Theta$ is a subset of a set acted on by $S_{d}$. Suppose that $f_{1}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f_{2}(\theta)$. Then $-f_{2}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}-f_{1}(\theta)$._

###### Proof. ^proof-2

By [[#^definition-a-10-orbit|definition A.10]], $f_{1}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f_{2}(\theta)$ means that

$$
\left|\left\{\theta^{\prime}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid f_{1}(\theta^{\prime})>f_{2}(\theta^{\prime})\right\}\right|\geq n\left|\left\{\theta^{\prime}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid f_{1}(\theta^{\prime})<f_{2}(\theta^{\prime})\right\}\right|
$$

$$
\left|\left\{\theta^{\prime}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid-f_{2}(\theta^{\prime})>-f_{1}(\theta^{\prime})\right\}\right|\geq n\left|\left\{\theta^{\prime}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)\mid-f_{2}(\theta^{\prime})<-f_{1}(\theta^{\prime})\right\}\right|.
$$

Then $-f_{2}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}-f_{1}(\theta)$. ∎

###### Remark. ^remark-2

[[#^lemma-b-3-orbital|Lemma B.3]] generalizes Turner et al. \[2021\]’s lemma B.2.

###### Lemma B.3 (Orbital fraction which agrees on (weak) inequality). ^lemma-b-3-orbital

_Suppose $f_{1},f_{2}\mathrel{\mathop{\ordinarycolon}}\Theta\to\mathbb{R}$ are such that $f_{1}(\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f_{2}(\theta)$. Then for all $\theta\in\Theta$, $\frac{\left|\left\{\theta^{\prime}\in\left(S_{d}\cdot\theta\right)\cap\Theta\mid f_{1}(\theta^{\prime})\geq f_{2}(\theta^{\prime})\right\}\right|}{\left|\left(S_{d}\cdot\theta\right)\cap\Theta\right|}\geq\dfrac{n}{n+1}$._

###### Proof. ^proof-3

All $\theta^{\prime}\in\left(S_{d}\cdot\theta\right)\cap\Theta$ such that $f_{1}(\theta^{\prime})=f_{2}(\theta^{\prime})$ satisfy $f_{1}(\theta^{\prime})\geq f_{2}(\theta^{\prime})$. Otherwise, consider the $\theta^{\prime}\in\left(S_{d}\cdot\theta\right)\cap\Theta$ such that $f_{1}(\theta^{\prime})\neq f_{2}(\theta^{\prime})$. By assumption, at least $\frac{n}{n+1}$ of these $\theta^{\prime}$ satisfy $f_{1}(\theta^{\prime})>f_{2}(\theta^{\prime})$, in which case $f_{1}(\theta^{\prime})\geq f_{2}(\theta^{\prime})$. Then the desired inequality follows. ∎

### B.1 General results on retargetable functions ^b-1-general-results

###### Definition B.4 (Functions which are increasing under joint permutation). ^definition-b-4-functions

Suppose that $S_{d}$ acts on sets $\mathbf{E}_{1},\ldots,\mathbf{E}_{m}$, and let $f\mathrel{\mathop{\ordinarycolon}}\prod_{i=1}^{m}\mathbf{E}_{i}\to\mathbb{R}$. $f(X_{1},\ldots,X_{m})$ is _increasing under joint permutation by $P\subseteq S_{d}$_ when $\forall\phi\in P\mathrel{\mathop{\ordinarycolon}}f(X_{1},\ldots,X_{m})\leq f(\phi\cdot X_{1},\ldots,\phi\cdot X_{m})$. If equality always holds, then $f(X_{1},\ldots,X_{m})$ is _invariant under joint permutation by $P$_.

###### Lemma B.5 (Expectations of joint-permutation-increasing functions are also joint-permutation-increasing). ^lemma-b-5-expectations

_For $\mathbf{E}$ which is a subset of a set acted on by $S_{d}$, let $f\mathrel{\mathop{\ordinarycolon}}\mathbf{E}\times\mathbb{R}^{d}\to\mathbb{R}$ be a bounded function which is measurable on its second argument, and let $P\subseteq S_{d}$. Then if $f(X\mid\mathbf{u})$ is increasing under joint permutation by $P$, then $f^{\prime}(X\mid\mathcal{D}_{\text{any}})\coloneqq\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{any}}}\left[f(X\mid\mathbf{u})\right]$ is increasing under joint permutation by $P$. If $f$ is _invariant_ under joint permutation by $P$, then so is $f^{\prime}$._

###### Proof. ^proof-4

Let distribution $\mathcal{D}_{\text{any}}$ have probability measure $F$, and let $\phi\cdot\mathcal{D}_{\text{any}}$ have probability measure $F_{\phi}$.

$$
f\left(X\mid\mathcal{D}_{\text{any}}\right)\coloneqq{}\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{any}}}\left[f(X\mid\mathbf{u})\right] \\
\coloneqq{}\int_{\mathbb{R}^{d}}f(X\mid\mathbf{u})\,\mathrm{d}F(\mathbf{u}) \\
\leq{}\int_{\mathbb{R}^{d}}f(\phi\cdot X\mid\mathbf{P}_{\phi}\mathbf{u})\,\mathrm{d}F(\mathbf{u}) \\
={}\int_{\mathbb{R}^{d}}f(\phi\cdot X\mid\mathbf{u}^{\prime})\left|\det\mathbf{P}_{\phi}\right|\mathrm{d}F_{\phi}(\mathbf{u}^{\prime}) \\
={}\int_{\mathbb{R}^{d}}f(\phi\cdot X\mid\mathbf{u}^{\prime})\,\mathrm{d}F_{\phi}(\mathbf{u}^{\prime}) \\
\eqqcolon{}f^{\prime}\left(\phi\cdot X\mid\phi\cdot\mathcal{D}_{\text{any}}\right).
$$

Equation 12 holds by assumption on $f$: $f(X\mid\mathbf{u})\leq f(\phi\cdot X\mid\mathbf{P}_{\phi}\mathbf{u})$. Furthermore, $f(\phi\cdot X\mid\cdot)$ is still measurable, and so the inequality holds. Equation 13 follows by the definition of $F_{\phi}$ (definition 6.3) and by substituting $\mathbf{r}^{\prime}\coloneqq\mathbf{P}_{\phi}\mathbf{r}$. Equation 14 follows from the fact that all permutation matrices have unitary determinant. ∎

###### Lemma B.6 (Closure of orbit incentives under increasing functions). ^lemma-b-6-closure

_Suppose that $S_{d}$ acts on sets $\mathbf{E}_{1},\ldots,\mathbf{E}_{m}$ (with $\mathbf{E}_{1}$ being a poset), and let $P\subseteq S_{d}$. Let $f_{1},\ldots,f_{n}\mathrel{\mathop{\ordinarycolon}}\prod_{i=1}^{m}\mathbf{E}_{i}\to\mathbb{R}$ be increasing under joint permutation by $P$ on input $(X_{1},\ldots,X_{m})$, and suppose the $f_{i}$ are order-preserving with respect to $\preceq_{\mathbf{E}_{1}}$. Let $g\mathrel{\mathop{\ordinarycolon}}\prod_{j=1}^{n}\mathbb{R}\to\mathbb{R}$ be monotonically increasing on each argument. Then_

$$
f\left(X_{1},\ldots,X_{m}\right)\coloneqq g\left(f_{1}\left(X_{1},\ldots,X_{m}\right),\ldots,f_{n}\left(X_{1},\ldots,X_{m}\right)\right)
$$

_is increasing under joint permutation by $P$ and order-preserving with respect to set inclusion on its first argument. Furthermore, if the $f_{i}$ are _invariant_ under joint permutation by $P$, then so is $f$._

###### Proof. ^proof-5

Let $\phi\in P$.

$$
f\left(X_{1},\ldots,X_{m}\right)\coloneqq g\left(f_{1}\left(X_{1},\ldots,X_{m}\right),\ldots,f_{n}\left(X_{1},\ldots,X_{m}\right)\right) \\
\leq g\left(f_{1}\left(\phi\cdot X_{1},\ldots,\phi\cdot X_{m}\right),\ldots,f_{n}\left(\phi\cdot X_{1},\ldots,\phi\cdot X_{m}\right)\right) \\
\eqqcolon f\left(\phi\cdot X_{1},\ldots,\phi\cdot X_{m}\right).
$$

Equation 18 follows because we assumed that $f_{i}\left(X_{1},\ldots,X_{m}\right)\leq f_{i}\left(\phi\cdot X_{1},\ldots,\phi\cdot X_{m}\right)$, and because $g$ is monotonically increasing on each argument. If the $f_{i}$ are all invariant, then eq. 18 is an equality.

Similarly, suppose $X_{1}^{\prime}\preceq_{\mathbf{E}_{1}}X_{1}$. The $f_{i}$ are order-preserving on the first argument, and $g$ is monotonically increasing on each argument. Then $f\left(X_{1}^{\prime},\ldots,X_{m}\right)\leq f\left(X_{1},\ldots,X_{m}\right)$. This shows that $f$ is order-preserving on its first argument. ∎

###### Remark. ^remark-3

$g$ could take the convex combination of its arguments, or multiply two $f_{i}$ together and add them to a third $f_{3}$.

See [[#^definition-3-5-multiply|3.5]]

See [[#^theorem-3-6-multiply|3.6]]

###### Proof. ^proof-6

Let $\theta\in\Theta$, and let $\phi_{i}\cdot\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\coloneqq\left\{\phi_{i}\cdot\theta^{A}\mid\theta^{A}\in\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\right\}$.

$$
\left|\mathrm{Orbit}|_{\Theta,B>A}\left(\theta\right)]\right|\geq\left|\bigcup_{i=1}^{n}\phi_{i}\cdot\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\right| \\
=\sum_{i=1}^{n}\left|\phi_{i}\cdot\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\right| \\
=n\left|\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\right|.
$$

By [[#^definition-3-5-multiply|item 1]] and [[#^definition-3-5-multiply|item 2]], $\phi_{i}\cdot\phi_{i}\cdot\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)\subseteq\phi_{i}\cdot\mathrm{Orbit}|_{\Theta,B>A}\left(\theta\right)]$ for all $i$. Therefore, eq. 20 holds. Equation 21 follows by the assumption that parameters are distinct, and so therefore the cosets $\phi_{i}\cdot\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)$ and $\phi_{j}\cdot\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)$ are pairwise disjoint for $i\neq j$. Equation 22 follows because each $\phi_{i}$ acts injectively on orbit elements.

Letting $f_{A}(\theta)\coloneqq f(A\mid\theta)$ and $f_{B}(\theta)\coloneqq f(B\mid\theta)$, the shown inequality satisfies [[#^definition-3-2-inequalities|definition 3.2]]. We conclude that $f(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f(A\mid\theta)$. ∎

See [[#^definition-3-3-simply-retargetable|3.3]]

See [[#^proposition-3-4-simply-retargetable|3.4]]

###### Proof. ^proof-7

Given that $f$ is a $(\Theta,A\overset{\text{simple}}{\to}B)$\-retargetable function ([[#^definition-3-3-simply-retargetable|definition 3.3]]), we want to show that $f$ is a $(\Theta,A\overset{1}{\to}B)$\-retargetable function ([[#^definition-3-5-multiply|definition 3.5]] when $n=1$). [[#^definition-3-5-multiply|Definition 3.5]]’s [[#^definition-3-5-multiply|item 1]] is true by assumption. Since $\Theta$ is acted on by $S_{d}$, $\Theta$ is closed under permutation and so [[#^definition-3-5-multiply|definition 3.5]]’s [[#^definition-3-5-multiply|item 2]] holds. When $n=1$, there are no $i\neq j$, and so [[#^definition-3-5-multiply|definition 3.5]]’s [[#^definition-3-5-multiply|item 3]] is tautologically true.

Then $f$ is a $(\Theta,A\overset{1}{\to}B)$\-retargetable function; apply [[#^lemma-b-7-quantitative|Lemma B.7]]. ∎

### B.2 Helper results on retargetable functions ^b-2-helper-results

| Targeting parameter $\theta$ | $f(\left\{\text{ghost}\right\}\!\mid\!\theta)$ | $f(\left\{\text{apple}\right\}\!\mid\!\theta)$ | $f(\left\{\text{cherry}\right\}\!\mid\!\theta)$ | $f(\left\{\text{apple},\text{cherry}\right\}\!\mid\!\theta)$ |
| --- | --- | --- | --- | --- |
| $\theta^{\prime}\coloneqq 1\mathbf{e}_{1}+3\mathbf{e}_{2}+2\mathbf{e}_{3}$ | $1$ | $0$ | $0$ | $0$ |
| $\phi_{1}\cdot\theta^{\prime}=\phi_{2}\cdot\theta^{\prime\prime}\coloneqq 3\mathbf{e}_{1}+1\mathbf{e}_{2}+2\mathbf{e}_{3}$ | $0$ | $2$ | $2$ | $2$ |
| $\phi_{2}\cdot\theta^{\prime}\coloneqq 2\mathbf{e}_{1}+3\mathbf{e}_{2}+1\mathbf{e}_{3}$ | $0$ | $2$ | $2$ | $2$ |
| $\theta^{\prime\prime}\coloneqq 2\mathbf{e}_{1}+1\mathbf{e}_{2}+3\mathbf{e}_{3}$ | $1$ | $0$ | $0$ | $0$ |
| $\phi_{1}\cdot\theta^{\prime\prime}\coloneqq 1\mathbf{e}_{1}+2\mathbf{e}_{2}+3\mathbf{e}_{3}$ | $0$ | $2$ | $2$ | $2$ |
| $\theta^{\star}\coloneqq 3\mathbf{e}_{1}+2\mathbf{e}_{2}+1\mathbf{e}_{3}$ | $1$ | $0$ | $0$ | $0$ |

Table 3: We reuse the Pac-Man outcome set introduced in [[#^2-statistical-tendencies-for|section 2]]. Let $\phi_{1}\coloneqq\text{ghost}\leftrightarrow\text{apple},\phi_{2}\coloneqq\text{ghost}\leftrightarrow\text{cherry}$. We tabularly define a function $f$ which meets all requirements of [[#^lemma-b-7-quantitative|Lemma B.7]], except for [[#^lemma-b-7-quantitative|item 4]]: letting $j\coloneqq 2$, $f(B_{2}^{\star}\mid\phi_{1}\cdot\theta^{\prime})=2>0=f(B_{2}^{\star}\mid\theta^{\prime})$. Although $f(B\mid\theta)\geq_{\text{{most}}\text{: }S_{3}\cdot\theta}^{1}f(A\mid\theta)$, it is not true that $f(B\mid\theta^{*})\geq_{\text{{most}}\text{: }S_{3}\cdot\theta}^{2}f(A\mid\theta^{*})$. Therefore, [[#^lemma-b-7-quantitative|item 4]] is generally required.

###### Lemma B.7 (Quantitative general orbit lemma). ^lemma-b-7-quantitative

_Let $\Theta$ be a subset of a set acted on by $S_{d}$, and let $f\mathrel{\mathop{\ordinarycolon}}\mathbf{E}\times\Theta\to\mathbb{R}$. Consider $A,B\in\mathbf{E}$._

_For each $\theta\in\Theta$, choose involutions $\phi_{1},\ldots,\phi_{n}\in S_{d}$. Let $\theta^{*}\in\mathrm{Orbit}|_{\Theta}\left(\theta\right)$._

1. _**Retargetable under parameter permutation.**_ _There exist_ $B_{i}^{\star}\in\mathbf{E}$ _such that if_ $f(B\mid\theta^{*})<f(A\mid\theta^{*})$_, then_ $\forall i\mathrel{\mathop{\ordinarycolon}}f\left(A\mid\theta^{*}\right)\leq f\left(B^{\star}_{i}\mid\phi_{i}\cdot\theta^{*}\right)$.
2. $\Theta$ _**is closed under certain symmetries.**_ $f(B\mid\theta^{*})<f(A\mid\theta^{*})\implies\forall i\mathrel{\mathop{\ordinarycolon}}\phi_{i}\cdot\theta^{*}\in\Theta$.
3. $f$ _**is increasing on certain inputs.**_ $\forall i\mathrel{\mathop{\ordinarycolon}}f(B_{i}^{\star}\mid\theta^{*})\leq f(B\mid\theta^{*})$.
4. _**Increasing under alternate symmetries.**_ _For_ $j=1,\ldots,n$ _and_ $i\neq j$, if $f(A\mid\theta^{*})<f(B\mid\theta^{*})$_, then_ $f\left(B_{j}^{\star}\mid\theta^{*}\right)\leq f\left(B_{j}^{\star}\mid\phi_{i}\cdot\theta^{*}\right)$.

_If these conditions hold for all $\theta\in\Theta$, then_

$$
f(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f(A\mid\theta). \tag{23}
$$

###### Proof. ^proof-8

Let $\theta$ and $\theta^{*}$ be as described in the assumptions, and let $i\in\left\{1,\ldots,n\right\}$.

$$
f(A\mid\phi_{i}\cdot\theta^{*})=f(A\mid\phi_{i}^{-1}\cdot\theta^{*}) \\
\leq f(B_{i}^{\star}\mid\theta^{*}) \\
\leq f(B\mid\theta^{*}) \\
<f(A\mid\theta^{*}) \\
\leq f(B_{i}^{\star}\mid\phi_{i}\cdot\theta^{*}) \\
\leq f(B\mid\phi_{i}\cdot\theta^{*}).
$$

Equation 24 follows because $\phi_{i}$ is an involution. Equation 25 and eq. 28 follow by [[#^lemma-b-7-quantitative|item 1]]. Equation 26 and eq. 29 follow by [[#^lemma-b-7-quantitative|item 3]]. Equation 27 holds by assumption on $\theta^{*}$. Then eq. 29 shows that for any $i$, $f(A\mid\phi_{i}\cdot\theta^{*})<f(B\mid\phi_{i}\cdot\theta^{*})$, satisfying [[#^definition-3-5-multiply|definition 3.5]]’s [[#^definition-3-5-multiply|item 1]].

This result’s [[#^lemma-b-7-quantitative|item 2]] satisfies [[#^definition-3-5-multiply|definition 3.5]]’s [[#^definition-3-5-multiply|item 2]]. We now just need to show [[#^definition-3-5-multiply|definition 3.5]]’s [[#^definition-3-5-multiply|item 3]].

##### Disjointness. ^disjointness

Let $\theta^{\prime},\theta^{\prime\prime}\in\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)$ and let $i\neq j$. Suppose $\phi_{i}\cdot\theta^{\prime}=\phi_{j}\cdot\theta^{\prime\prime}$. We want to show that this leads to contradiction.

$$
f(A\mid\theta^{\prime\prime})\leq f(B_{j}^{\star}\mid\phi_{j}\cdot\theta^{\prime\prime}) \\
=f(B_{j}^{\star}\mid\phi_{i}^{-1}\cdot\theta^{\prime}) \\
\leq f(B_{j}^{\star}\mid\theta^{\prime}) \\
\leq f(B\mid\theta^{\prime}) \\
<f(A\mid\theta^{\prime}) \\
\leq f(B_{i}^{\star}\mid\phi_{i}\cdot\theta^{\prime}) \\
=f(B_{i}^{\star}\mid\phi_{j}^{-1}\cdot\theta^{\prime\prime}) \\
\leq f(B_{i}^{\star}\mid\theta^{\prime\prime}) \\
\leq f(B\mid\theta^{\prime\prime}) \\
<f(A\mid\theta^{\prime\prime}).
$$

Equation 30 follows by our assumption of [[#^lemma-b-7-quantitative|item 1]]. Equation 31 holds because we assumed that $\phi_{j}\cdot\theta^{\prime\prime}=\phi_{i}\cdot\theta^{\prime}$, and the involution ensures that $\phi_{i}=\phi_{i}^{-1}$. Equation 32 is guaranteed by our assumption of [[#^lemma-b-7-quantitative|item 4]], given that $\phi_{i}^{-1}\cdot\theta^{\prime}=\phi_{i}\cdot\theta^{\prime}\in\mathrm{Orbit}|_{\Theta,B>A}\left(\theta\right)]$ by the first half of this proof. Equation 33 follows by our assumption of [[#^lemma-b-7-quantitative|item 3]]. Equation 34 follows because we assumed that $\theta^{\prime}\in\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)$.

Equation 35 through eq. 39 follow by the same reasoning, switching the roles of $\theta^{\prime}$ and $\theta^{\prime\prime}$, and of $i$ and $j$. But then we have demonstrated that a quantity is strictly less than itself, a contradiction. So for all $\theta^{\prime},\theta^{\prime\prime}\in\mathrm{Orbit}|_{\Theta,A>B}\left(\theta\right)$, when $i\neq j$, $\phi_{i}\cdot\theta^{\prime}\neq\phi_{j}\cdot\theta^{\prime\prime}$.

Therefore, we have shown [[#^definition-3-5-multiply|definition 3.5]]’s [[#^definition-3-5-multiply|item 3]], and so $f$ is a $(\Theta,A\overset{n}{\to}B)$\-retargetable function. Apply [[#^theorem-3-6-multiply|Theorem 3.6]] in order to conclude that eq. 23 holds. ∎

###### Definition B.8 (Superset-of-copy containment). ^definition-b-8-superset-of-copy

Let $A,B\subseteq\mathbb{R}^{d}$. _$B$ contains $n$ superset-copies $B_{i}^{\star}$ of $A$_ when there exist involutions $\phi_{1},\ldots,\phi_{n}$ such that $\phi_{i}\cdot A\subseteq B_{i}^{\star}\subseteq B$, and whenever $i\neq j$, $\phi_{i}\cdot B_{j}^{\star}=B_{j}^{\star}$.

###### Lemma B.9 (Looser sufficient conditions for orbit-level incentives). ^lemma-b-9-looser

_Suppose that $\Theta$ is a subset of a set acted on by $S_{d}$ and is closed under permutation by $S_{d}$. Let $A,B\in\mathbf{E}\subseteq\mathcal{P}\left(\mathbb{R}^{d}\right)$. Suppose that $B$ contains $n$ superset-copies $B_{i}^{\star}\in\mathbf{E}$ of $A$ via $\phi_{i}$. Suppose that $f(X\mid\theta)$ is increasing under joint permutation by $\phi_{1},\ldots,\phi_{n}\in S_{d}$ for all $X\in\mathbf{E},\theta\in\Theta$, and suppose that $\forall i\mathrel{\mathop{\ordinarycolon}}\phi_{i}\cdot A\in\mathbf{E}$. Suppose that $f$ is monotonically increasing on its first argument. Then $f(B\mid\theta)\geq_{\text{{most}}\text{: }\Theta}^{n}f(A\mid\theta).$_

###### Proof. ^proof-9

We check the conditions of [[#^lemma-b-7-quantitative|Lemma B.7]]. Let $\theta\in\Theta$, and let $\theta^{*}\in\left(S_{d}\cdot\theta\right)\cap\Theta$ be an orbit element.

1.  [[#^lemma-b-7-quantitative|Item 1]].
    
    Holds since $f(A\mid\theta^{*})\leq f(\phi_{i}\cdot A\mid\phi_{i}\cdot\theta^{*})\leq f(B^{\star}_{i}\mid\phi_{i}\cdot\theta^{*})$, with the first inequality by assumption of joint increasing under permutation, and the second following from monotonicity (as $\phi_{i}\cdot A\subseteq B^{\star}_{i}$ by superset copy [[#^definition-b-8-superset-of-copy|definition B.8]]).
    
2.  [[#^lemma-b-7-quantitative|Item 2]].
    
    We have $\forall\theta^{*}\in\left(S_{d}\cdot\theta^{*}\right)\cap\Theta\mathrel{\mathop{\ordinarycolon}}f(B\mid\theta^{*})<f(A\mid\theta^{*})\implies\forall i=1,...,n\mathrel{\mathop{\ordinarycolon}}\phi_{i}\cdot\theta^{*}\in\Theta$ since $\Theta$ is closed under permutation.
    
3.  [[#^lemma-b-7-quantitative|Item 3]].
    
    Holds because we assumed that $f$ is monotonic on its first argument.
    
4.  [[#^lemma-b-7-quantitative|Item 4]].
    
    Holds because $f$ is increasing under joint permutation on _all_ of its inputs $X,\theta^{{}^{\prime}}$, and [[#^definition-b-8-superset-of-copy|definition B.8]] shows that $\phi_{i}\cdot B^{\star}_{j}=B^{\star}_{j}$ when $i\neq j$. Combining these two steps of reasoning, for _all_ $\theta^{\prime}\in\Theta$, it is true that $f\left(B_{j}^{\star}\mid\theta^{\prime}\right)\leq f\left(\phi_{i}\cdot B_{j}^{\star}\mid\phi_{i}\cdot\theta^{\prime}\right)\leq f\left(B_{j}^{\star}\mid\phi_{i}\cdot\theta^{\prime}\right)$.
    

Then apply [[#^lemma-b-7-quantitative|Lemma B.7]]. ∎

###### Lemma B.10 (Hiding an argument which is invariant under certain permutations). ^lemma-b-10-hiding

_Let $\mathbf{E}_{1}$, $\mathbf{E}_{2}$, $\Theta$ be subsets of sets which are acted on by $S_{d}$. Let $A\in\mathbf{E}_{1}$, $C\in\mathbf{E}_{2}$. Suppose there exist $\phi_{1},\ldots,\phi_{n}\in S_{d}$ such that $\phi_{i}\cdot C=C$. Suppose $h\mathrel{\mathop{\ordinarycolon}}\mathbf{E}_{1}\times\mathbf{E}_{2}\times\Theta\to\mathbb{R}$ satisfies $\forall i\mathrel{\mathop{\ordinarycolon}}h(A,C\mid\theta)\leq h(\phi_{i}\cdot A,\phi_{i}\cdot C\mid\phi_{i}\cdot\theta)$. For any $X\in\mathbf{E}_{1}$, let $f(X\mid\theta)\coloneqq h(X,C\mid\theta)$. Then $f(A\mid\theta)$ is increasing under joint permutation by $\phi_{i}$._

_Furthermore, if $h$ is _invariant_ under joint permutation by $\phi_{i}$, then so is $f$._

###### Proof. ^proof-10

$$
f(X\mid\theta)\coloneqq h(X,C\mid\theta) \\
\leq h(\phi_{i}\cdot X,\phi_{i}\cdot C\mid\phi_{i}\cdot\theta) \\
=h(\phi_{i}\cdot X,C\mid\phi_{i}\cdot\theta) \\
\eqqcolon f(\phi_{i}\cdot X\mid\phi_{i}\cdot\theta).
$$

Equation 41 holds by assumption. Equation 42 follows because we assumed $\phi_{i}\cdot C=C$. Then $f$ is increasing under joint permutation by the $\phi_{i}$.

If $h$ is _invariant_, then eq. 41 is an equality, and so $\forall i\mathrel{\mathop{\ordinarycolon}}f(X\mid\theta)=f(\phi_{i}\cdot X\mid\phi_{i}\cdot\theta)$. ∎

#### B.2.1 EU-determined functions ^b-2-1-eu-determined

[[#^lemma-b-11-eu-determined|Lemma B.11]] and [[#^lemma-b-5-expectations|Lemma B.5]] together extend Turner et al. \[2021\]’s lemma E.17 beyond functions of $\max_{\mathbf{x}\in X_{i}}$, to any functions of cardinalities and of expected utilities of set elements.

See [[#^definition-a-12-eu-determined|A.12]]

###### Lemma B.11 (EU-determined functions are invariant under joint permutation). ^lemma-b-11-eu-determined

_Suppose that $f\mathrel{\mathop{\ordinarycolon}}\prod_{i=1}^{m}\mathcal{P}\left(\mathbb{R}^{d}\right)\times\mathbb{R}^{d}\to\mathbb{R}$ is an EU-determined function. Then for any $\phi\in S_{d}$ and $X_{1},\ldots,X_{m},\mathbf{u}$, we have $f(X_{1},\ldots,X_{m}\mid\mathbf{u})=f(\phi\cdot X_{1},\ldots,\phi\cdot X_{m}\mid\phi\cdot\mathbf{u})$._

###### Proof. ^proof-11

$$
f(X_{1},\ldots,X_{m}\mid\mathbf{u})=g^{|X_{1}|,\ldots,|X_{m}|}\left(\left[\mathbf{x}_{1}^{\top}\mathbf{u}\right]_{\mathbf{x}_{1}\in X_{1}},\ldots,\left[\mathbf{x}_{m}^{\top}\mathbf{u}\right]_{\mathbf{x}_{m}\in X_{m}}\right) \\
=g^{\left|\phi\cdot X_{1}\right|,\ldots,\left|\phi\cdot X_{m}\right|}\left(\left[\mathbf{x}_{1}^{\top}\mathbf{u}\right]_{\mathbf{x}_{1}\in X_{1}},\ldots,\left[\mathbf{x}_{m}^{\top}\mathbf{u}\right]_{\mathbf{x}_{m}\in X_{m}}\right) \\
=g^{\left|\phi\cdot X_{1}\right|,\ldots,\left|\phi\cdot X_{m}\right|}\left(\left[(\mathbf{P}_{\phi}\mathbf{x}_{1})^{\top}(\mathbf{P}_{\phi}\mathbf{u})\right]_{\mathbf{x}_{1}\in X_{1}},\ldots,\left[(\mathbf{P}_{\phi}\mathbf{x}_{m})^{\top}(\mathbf{P}_{\phi}\mathbf{u})\right]_{\mathbf{x}_{m}\in X_{m}}\right) \\
=f(\phi\cdot X_{1},\ldots,\phi\cdot X_{m}\mid\phi\cdot\mathbf{u}).
$$

Equation 46 holds because permutations $\phi$ act injectively on $\mathbb{R}^{d}$. Equation 47 follows because $\mathbf{I}=\mathbf{P}_{\phi}^{-1}\mathbf{P}_{\phi}=\mathbf{P}_{\phi}^{\top}\mathbf{P}_{\phi}$ by the orthogonality of permutation matrices, and $\mathbf{x}^{\top}\mathbf{P}_{\phi}^{\top}=(\mathbf{P}_{\phi}\mathbf{x})^{\top}$, so $\mathbf{x}^{\top}\mathbf{u}=\mathbf{x}^{\top}\mathbf{P}_{\phi}^{\top}\mathbf{P}_{\phi}\mathbf{u}=(\mathbf{P}_{\phi}\mathbf{x})^{\top}(\mathbf{P}_{\phi}\mathbf{u})$. ∎

See [[#^theorem-a-13-orbit|A.13]]

###### Proof. ^proof-12

By assumption, there exists a family of functions $\left\{g^{i,|C|}\right\}$ such that for all $X\subseteq\mathbb{R}^{d}$, $h(X,C\mid\mathbf{u})=g^{|X|,|C|}\left(\left[\mathbf{x}^{\top}\mathbf{u}\right]_{\mathbf{x}\in X},\left[\mathbf{c}^{\top}\mathbf{u}\right]_{\mathbf{c}\in C}\right)$. Therefore, [[#^lemma-b-11-eu-determined|Lemma B.11]] shows that $h(A,C\mid\mathbf{u})$ is invariant under joint permutation by the $\phi_{i}$. Letting $\Theta\coloneqq\mathbb{R}^{d}$, apply [[#^lemma-b-10-hiding|Lemma B.10]] to conclude that $f(X\mid\mathbf{u})$ is invariant under joint permutation by the $\phi_{i}$.

Since $f$ returns a probability of selecting an element of $X$, $f$ obeys the monotonicity probability axiom: If $X^{\prime}\subseteq X$, then $f(X^{\prime}\mid\mathbf{u})\leq f(X\mid\mathbf{u})$. Then $f(B\mid\mathbf{u})\geq_{\text{{most}}\text{: }\mathbb{R}^{d}}^{n}f(A\mid\mathbf{u})$ by [[#^lemma-b-9-looser|Lemma B.9]]. ∎

### B.3 Particular results on retargetable functions ^b-3-particular-results

###### Definition B.12 (Quantilization, closed form). ^definition-b-12-quantilization

Let the expected utility $q$\-quantile threshold be

$$
M_{q,P}(C\mid\mathbf{u})\coloneqq\inf\left\{M\in\mathbb{R}\mid\mathbb{P}_{\mathbf{x}\sim P}\left(\mathbf{x}^{\top}\mathbf{u}>M\right)\leq q\right\}.
$$

Let $C_{>M_{q,P}(C\mid\mathbf{u})}\coloneqq\left\{\mathbf{c}\in C\mid\mathbf{c}^{\top}\mathbf{u}>M_{q,P}(C\mid\mathbf{u})\right\}$. $C_{=M_{q,P}(C\mid\mathbf{u})}$ is defined similarly. Let $\mathbf{1}_{L(x)}$ be the predicate function returning $1$ if $L(x)$ is true and $0$ otherwise. Then for $X\subseteq C$,

$$
Q_{q,P}(X\mid C,\mathbf{u})\coloneqq\sum_{\mathbf{x}\in X}\frac{P(\mathbf{x})}{q}\left(\mathbf{1}_{\mathbf{x}\in C_{>M_{q,P}(C\mid\mathbf{u})}}+\frac{\mathbf{1}_{\mathbf{x}\in C_{=M_{q,P}(C\mid\mathbf{u})}}}{P\left(C_{=M_{q,P}(C\mid\mathbf{u})}\right)}\left(q-P\left(C_{>M_{q,P}(C\mid\mathbf{u})}\right)\right)\right), \tag{50}
$$

where the summand is defined to be $0$ if $P(\mathbf{x})=0$ and $\mathbf{x}\in C_{=M_{q,P}(C\mid\mathbf{u})}$.

###### Remark. ^remark-4

Unlike Taylor \[2016\]’s or Carey \[2019\]’s definitions, [[#^definition-b-12-quantilization|definition B.12]] is written in closed form and requires no arbitrary tie-breaking. Instead, in the case of an expected utility tie on the quantile threshold, eq. 50 allots probability to outcomes proportional to their probability under the base distribution $P$.

Thanks to [[#^theorem-a-13-orbit|Theorem A.13]], we straightforwardly prove most items of [[#^proposition-a-11-orbit|Proposition A.11]] by just rewriting each decision-making function as an EU-determined function. Most of the proof’s length comes from showing that the functions are measurable on $\mathbf{u}$, which means that the results also apply for distributions over utility functions $\mathcal{D}_{\text{any}}\in\mathfrak{D}_{\text{any}}$.

See [[#^proposition-a-11-orbit|A.11]]

###### Proof. ^proof-13

**[[#^proposition-a-11-orbit|Item 1]].** Consider

$$
h(X,C\mid\mathbf{u})\coloneqq\mathbf{1}_{\exists\mathbf{x}\in X\mathrel{\mathop{\ordinarycolon}}\forall\mathbf{c}\in C\mathrel{\mathop{\ordinarycolon}}\mathbf{x}^{\top}\mathbf{u}\geq\mathbf{c}^{\top}\mathbf{u}} \\
=\min\left(1,\sum_{\mathbf{x}\in X}\prod_{\mathbf{c}\in C}\mathbf{1}_{(\mathbf{x}-\mathbf{c})^{\top}\mathbf{u}\geq 0}\right).
$$

Since halfspaces are measurable, each indicator function is measurable on $\mathbf{u}$. The finite sum of the finite product of measurable functions is also measurable. Since $\min$ is continuous (and therefore measurable), $h(X,C\mid\mathbf{u})$ is measurable on $\mathbf{u}$.

Furthermore, $h$ is an EU-determined function:

$$
h(X,C\mid\mathbf{u})=g\left(\overbrace{\left[\mathbf{x}^{\top}\mathbf{u}\right]_{\mathbf{x}\in X}}^{V_{X}},\overbrace{\left[\mathbf{c}^{\top}\mathbf{u}\right]_{\mathbf{c}\in C}}^{V_{C}}\right) \\
\coloneqq\mathbf{1}_{\exists v_{x}\in V_{X}\mathrel{\mathop{\ordinarycolon}}\forall v_{c}\in V_{C}\mathrel{\mathop{\ordinarycolon}}v_{x}\geq v_{c}}.
$$

Then by [[#^lemma-b-11-eu-determined|Lemma B.11]], $h$ is invariant to joint permutation by the $\phi_{i}$. Since $\phi_{i}\cdot C=C$, [[#^lemma-b-10-hiding|Lemma B.10]] shows that $h^{\prime}(X\mid\mathbf{u})\coloneqq h(X,C\mid\mathbf{u})$ is also invariant under joint permutation by the $\phi_{i}$. Since $h$ is a measurable function of $\mathbf{u}$, so is $h^{\prime}$. Then since $h^{\prime}$ is bounded, [[#^lemma-b-5-expectations|Lemma B.5]] shows that $f(X\mid\mathcal{D}_{\text{any}})\coloneqq\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{any}}}\left[h^{\prime}(X\mid\mathbf{u})\right]$ is invariant under joint permutation by $\phi_{i}$.

Furthermore, if $X^{\prime}\subseteq X$, $f(X^{\prime}\mid\mathcal{D}_{\text{any}})\leq f(X\mid\mathcal{D}_{\text{any}})$ by the monotonicity of probability. Then by [[#^lemma-b-9-looser|Lemma B.9]],

$$
f(B\mid\mathcal{D}_{\text{any}})\coloneqq\mathrm{IsOptimal}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathrm{IsOptimal}\left(A\mid C,\mathcal{D}_{\text{any}}\right)\eqqcolon f(A\mid\mathcal{D}_{\text{any}}).
$$

**[[#^proposition-a-11-orbit|Item 2]].** Because $X,C$ are finite sets, the denominator of $\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)$ is never zero, and so the function is well-defined. $\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)$ is an EU-determined function:

$$
\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)=g\left(\overbrace{\left[\mathbf{x}^{\top}\mathbf{u}\right]_{\mathbf{x}\in X}}^{V_{X}},\overbrace{\left[\mathbf{c}^{\top}\mathbf{u}\right]_{\mathbf{c}\in C}}^{V_{C}}\right) \\
\coloneqq\frac{\left|\left[v\in V_{X}\mid v=\max_{v^{\prime}\in V_{C}}v^{\prime}\right]\right|}{\left|\left[\argmax_{v^{\prime}\in V_{C}}v^{\prime}\right]\right|},
$$

with the $\left[\cdot\right]$ denoting a multiset which allows and counts duplicates. Then by [[#^lemma-b-11-eu-determined|Lemma B.11]], $\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)$ is invariant to joint permutation by the $\phi_{i}$.

We now show that $\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)$ is a measurable function of $\mathbf{u}$.

$$
\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)\coloneqq\frac{\left|\left\{\argmax_{\mathbf{c}^{\prime}\in C}\mathbf{c}^{\prime\top}\mathbf{u}\right\}\cap X\right|}{\left|\left\{\argmax_{\mathbf{c}^{\prime}\in C}\mathbf{c}^{\prime\top}\mathbf{u}\right\}\right|} \\
=\frac{\sum_{\mathbf{x}\in X}\mathbf{1}_{\mathbf{x}\in\argmax_{\mathbf{c}^{\prime}\in C}\mathbf{c}^{\prime\top}\mathbf{u}}}{\sum_{\mathbf{c}\in C}\mathbf{1}_{\mathbf{c}\in\argmax_{\mathbf{c}^{\prime}\in C}\mathbf{c}^{\prime\top}\mathbf{u}}} \\
=\frac{\sum_{\mathbf{x}\in X}\prod_{\mathbf{c}^{\prime}\in C}\mathbf{1}_{\left(\mathbf{x}-\mathbf{c}^{\prime}\right)^{\top}\mathbf{u}\geq 0}}{\sum_{\mathbf{c}\in C}\prod_{\mathbf{c}^{\prime}\in C}\mathbf{1}_{\left(\mathbf{c}-\mathbf{c}^{\prime}\right)^{\top}\mathbf{u}\geq 0}}.
$$

Equation 59 holds because $\mathbf{x}$ belongs to the $\argmax$ iff $\forall\mathbf{c}\in C\mathrel{\mathop{\ordinarycolon}}\mathbf{x}^{\top}\mathbf{u}\geq\mathbf{c}^{\top}\mathbf{u}$. Furthermore, this condition is met iff $\mathbf{u}$ belongs to the intersection of finitely many closed halfspaces; therefore, $\left\{\mathbf{u}\in\mathbb{R}^{d}\mid\prod_{\mathbf{c}\in C}\mathbf{1}_{\left(\mathbf{x}-\mathbf{c}\right)^{\top}\mathbf{u}\geq 0}=1\right\}$ is measurable. Then the sums in both the numerator and denominator are both measurable functions of $\mathbf{u}$, and the denominator cannot vanish. Therefore, $\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)$ is a measurable function of $\mathbf{u}$.

Let $g(X\mid\mathbf{u})\coloneqq\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)$. Since $\phi_{i}\cdot C=C$, [[#^lemma-b-10-hiding|Lemma B.10]] shows that $g(X\mid\mathbf{u})$ is also invariant to joint permutation by $\phi_{i}$. Since $g$ is measurable and bounded $[0,1]$, apply [[#^lemma-b-5-expectations|Lemma B.5]] to conclude that $f(X\mid\mathcal{D}_{\text{any}})\coloneqq\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{any}}}\left[g(X\mid C,\mathbf{u})\right]$ is also invariant to joint permutation by $\phi_{i}$.

Furthermore, if $X^{\prime}\subseteq X\subseteq C$, then $f(X^{\prime}\mid\mathcal{D}_{\text{any}})\leq f(X\mid\mathcal{D}_{\text{any}})$. So apply [[#^lemma-b-9-looser|Lemma B.9]] to conclude that $\mathrm{FracOptimal}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\eqqcolon f(B\mid\mathcal{D}_{\text{any}})\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}f(A\mid\mathcal{D}_{\text{any}})\coloneqq\mathrm{FracOptimal}\left(A\mid C,\mathcal{D}_{\text{any}}\right)$.

**[[#^proposition-a-11-orbit|Item 3]].** Apply the reasoning in [[#^proposition-a-11-orbit|item 1]] with inner function $h(X\mid C,\mathbf{u})\coloneqq\mathbf{1}_{\exists\mathbf{x}\in X\mathrel{\mathop{\ordinarycolon}}\forall\mathbf{c}\in C\mathrel{\mathop{\ordinarycolon}}\mathbf{x}^{\top}\mathbf{u}\leq\mathbf{c}^{\top}\mathbf{u}}$.

**[[#^proposition-a-11-orbit|Item 4]].** Let $X\subseteq C$. $\mathrm{Boltzmann}_{T}\left(X\mid C,\mathbf{u}\right)$ is the expectation of an EU function:

$$
\mathrm{Boltzmann}_{T}\left(X\mid C,\mathbf{u}\right)=g_{T}\left(\overbrace{\left[\mathbf{x}^{\top}\mathbf{u}\right]_{\mathbf{x}\in X}}^{V_{X}},\overbrace{\left[\mathbf{c}^{\top}\mathbf{u}\right]_{\mathbf{c}\in C}}^{V_{C}}\right) \\
\coloneqq\frac{\sum_{v\in V_{X}}e^{v/T}}{\sum_{v\in V_{C}}e^{v/T}}.
$$

Therefore, by [[#^lemma-b-11-eu-determined|Lemma B.11]], $\mathrm{Boltzmann}_{T}\left(X\mid C,\mathbf{u}\right)$ is invariant to joint permutation by the $\phi_{i}$.

Inspecting eq. 61, we see that $g$ is continuous on $\mathbf{u}$ (and therefore measurable), and bounded $[0,1]$ since $X\subseteq C$ and the exponential function is positive. Therefore, by [[#^lemma-b-5-expectations|Lemma B.5]], the expectation version is also invariant to joint permutation for all permutations $\phi\in S_{d}$: $\mathrm{Boltzmann}_{T}\left(X\mid C,\mathcal{D}_{\text{any}}\right)=\mathrm{Boltzmann}_{T}\left(\phi\cdot X\mid\phi\cdot C,\phi\cdot\mathcal{D}_{\text{any}}\right)$.

Since $\phi_{i}\cdot C=C$, [[#^lemma-b-10-hiding|Lemma B.10]] shows that $f(X\mid\mathcal{D}_{\text{any}})\coloneqq\mathrm{Boltzmann}_{T}\left(X\mid C,\mathcal{D}_{\text{any}}\right)$ is also invariant under joint permutation by the $\phi_{i}$. Furthermore, if $X^{\prime}\subseteq X$, then $f(X^{\prime}\mid\mathcal{D}_{\text{any}})\leq f(X\mid\mathcal{D}_{\text{any}})$. Then apply [[#^lemma-b-9-looser|Lemma B.9]] to conclude that $\mathrm{Boltzmann}_{T}\left(B\mid C,\mathcal{D}_{\text{any}}\right)\eqqcolon f(B\mid\mathcal{D}_{\text{any}})\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}f(A\mid\mathcal{D}_{\text{any}})\coloneqq\mathrm{Boltzmann}_{T}\left(A\mid C,\mathcal{D}_{\text{any}}\right)$.

**[[#^proposition-a-11-orbit|Item 5]].** Let involution $\phi\in S_{d}$ fix $C$ (_i_._e_., $\phi\cdot C=C$).

$$
\textrm{best-of-}k(X\mid C,\mathbf{u})\coloneqq\!\!\mathbb{E}_{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\sim\text{unif}(C)}\left[\mathrm{FracOptimal}\left(X\cap\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\}\mid\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\},\mathbf{u}\right)\right] \\
=\!\!\mathbb{E}_{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\sim\text{unif}(C)}\left[\mathrm{FracOptimal}\left((\phi\cdot X)\cap\{\phi\cdot\mathbf{a}_{1},\ldots,\phi\cdot\mathbf{a}_{k}\}\!\mid\!\{\phi\cdot\mathbf{a}_{1},\ldots,\phi\cdot\mathbf{a}_{k}\},\phi\cdot\mathbf{u}\right)\right] \\
=\!\!\mathbb{E}_{\phi\cdot\mathbf{a}_{1},\ldots,\phi\cdot\mathbf{a}_{k}\sim\text{unif}(\phi\cdot C)}\left[\mathrm{FracOptimal}\left((\phi\cdot X)\cap\{\phi\cdot\mathbf{a}_{1},\ldots,\phi\cdot\mathbf{a}_{k}\}\!\mid\!\{\phi\cdot\mathbf{a}_{1},\ldots,\phi\cdot\mathbf{a}_{k}\},\phi\cdot\mathbf{u}\right)\right] \\
\eqqcolon\textrm{best-of-}k(\phi\cdot X\mid\phi\cdot C,\phi\cdot\mathbf{u}).
$$

By the proof of [[#^proposition-a-11-orbit|item 2]],

$$
\mathrm{FracOptimal}\left(X\cap\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\}\mid\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\},\mathbf{u}\right)=\\
\mathrm{FracOptimal}\left((\phi\cdot X)\cap\{\phi\cdot\mathbf{a}_{1},\ldots,\phi\cdot\mathbf{a}_{k}\}\mid\{\phi\cdot\mathbf{a}_{1},\ldots,\phi\cdot\mathbf{a}_{k}\},\phi\cdot\mathbf{u}\right);
$$

thus, eq. 64 holds. Since $\phi\cdot C=C$ and since the distribution is uniform, eq. 65 holds. Therefore, $\textrm{best-of-}k(X\mid C,\mathbf{u})$ is invariant to joint permutation by the $\phi_{i}$, which are involutions fixing $C$.

We now show that $\textrm{best-of-}k(X\mid C,\mathbf{u})$ is measurable on $\mathbf{u}$.

$$
\textrm{best-of-}k(X\mid C,\mathbf{u})\coloneqq\mathbb{E}_{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\sim\text{unif}(C)}\left[\mathrm{FracOptimal}\left(X\cap\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\}\mid\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\},\mathbf{u}\right)\right] \\
=\frac{1}{\left|C\right|^{k}}\sum_{\left(\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\right)\in C^{k}}\mathrm{FracOptimal}\left(X\cap\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\}\mid\{\mathbf{a}_{1},\ldots,\mathbf{a}_{k}\},\mathbf{u}\right).
$$

Equation 69 holds because $\mathrm{FracOptimal}\left(X\mid C,\mathbf{u}\right)$ is measurable on $\mathbf{u}$ by [[#^proposition-a-11-orbit|item 2]], and measurable functions are closed under finite addition and scalar multiplication. Then $\textrm{best-of-}k(X\mid C,\mathbf{u})$ is measurable on $\mathbf{u}$.

Let $g(X\mid\mathbf{u})\coloneqq\textrm{best-of-}k(X\mid C,\mathbf{u})$. Since $\phi_{i}\cdot C=C$, [[#^lemma-b-10-hiding|Lemma B.10]] shows that $g(X\mid\mathbf{u})$ is also invariant to joint permutation by $\phi_{i}$. Since $g$ is measurable and bounded $[0,1]$, apply [[#^lemma-b-5-expectations|Lemma B.5]] to conclude that $f(X\mid\mathcal{D}_{\text{any}})\coloneqq\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{any}}}\left[g(X\mid C,\mathbf{u})\right]$ is also invariant to joint permutation by $\phi_{i}$.

Furthermore, if $X^{\prime}\subseteq X\subseteq C$, then $f(X^{\prime}\mid\mathcal{D}_{\text{any}})\leq f(X\mid\mathcal{D}_{\text{any}})$. So apply [[#^lemma-b-9-looser|Lemma B.9]] to conclude that $\textrm{best-of-}k(B\mid C,\mathcal{D}_{\text{any}})\eqqcolon f(B\mid\mathcal{D}_{\text{any}})\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}f(A\mid\mathcal{D}_{\text{any}})\coloneqq\textrm{best-of-}k(A\mid C,\mathcal{D}_{\text{any}})$.

**[[#^proposition-a-11-orbit|Item 6]].** $\mathrm{Satisfice}_{t}\left(X\mid C,\mathbf{u}\right)$ is an EU-determined function:

$$
\mathrm{Satisfice}_{t}\left(X\mid C,\mathbf{u}\right)=g_{t}\left(\overbrace{\left[\mathbf{x}^{\top}\mathbf{u}\right]_{\mathbf{x}\in X}}^{V_{X}},\overbrace{\left[\mathbf{c}^{\top}\mathbf{u}\right]_{\mathbf{c}\in C}}^{V_{C}}\right) \\
\coloneqq\frac{\sum_{v\in V_{X}}\mathbf{1}_{v\geq t}}{\sum_{v\in V_{C}}\mathbf{1}_{v\geq t}},
$$

with the function evaluating to $0$ if the denominator is $0$.  
Then applying [[#^lemma-b-11-eu-determined|Lemma B.11]], $\mathrm{Satisfice}_{t}\left(X\mid C,\mathbf{u}\right)$ is invariant under joint permutation by the $\phi_{i}$.

We now show that $\mathrm{Satisfice}_{t}\left(X\mid C,\mathbf{u}\right)$ is measurable on $\mathbf{u}$.

$$
\mathrm{Satisfice}_{t}\left(X\mid C,\mathbf{u}\right)=\begin{cases}\frac{\sum_{\mathbf{x}\in X}\mathbf{1}_{\mathbf{x}\in\left\{\mathbf{x}^{\prime}\in\mathbb{R}^{d}\mid\mathbf{x}^{\prime\top}\mathbf{u}\geq t\right\}}}{\sum_{\mathbf{c}\in C}\mathbf{1}_{\mathbf{c}\in\left\{\mathbf{x}^{\prime}\in\mathbb{R}^{d}\mid\mathbf{x}^{\prime\top}\mathbf{u}\geq t\right\}}}&\exists\mathbf{c}\in C\mathrel{\mathop{\ordinarycolon}}\mathbf{c}^{\top}\mathbf{u}\geq t,\\
0&\text{ else}.\end{cases} \tag{72}
$$

Consider the two cases.

$$
\exists\mathbf{c}\in C\mathrel{\mathop{\ordinarycolon}}\mathbf{c}^{\top}\mathbf{u}\geq t\iff\mathbf{u}\in\bigcup_{\mathbf{c}\in C}\left\{\mathbf{u}^{\prime}\in\mathbb{R}^{d}\mid\mathbf{c}^{\top}\mathbf{u}\geq t\right\}.
$$

The right-hand set is the union of finitely many halfspaces (which are measurable), and so the right-hand set is also measurable. Then the casing is a measurable function of $\mathbf{u}$. Clearly the zero function is measurable. Now we turn to the first case.

In the first case, eq. 72’s indicator functions test each $\mathbf{x},\mathbf{c}$ for membership in a closed halfspace with respect to $\mathbf{u}$. Halfspaces are measurable sets. Therefore, the indicator function is a measurable function of $\mathbf{u}$, and so are the finite sums. Since the denominator does not vanish within the case, the first case as a whole is a measurable function of $\mathbf{u}$. Therefore, $\mathrm{Satisfice}_{t}\left(X\mid C,\mathbf{u}\right)$ is measurable on $\mathbf{u}$.

Since $\mathrm{Satisfice}_{t}\left(X\mid C,\mathbf{u}\right)$ is measurable and bounded $[0,1]$ (as $X\subseteq C$), apply [[#^lemma-b-5-expectations|Lemma B.5]] to conclude that $\mathrm{Satisfice}_{t}\left(X\mid C,\mathcal{D}_{\text{any}}\right)=\mathrm{Satisfice}_{t}\left(\phi\cdot X\mid\phi\cdot C,\phi\cdot\mathcal{D}_{\text{any}}\right)$. Next, let $f(X\mid\mathcal{D}_{\text{any}})\coloneqq\mathrm{Satisfice}_{t}\left(X\mid C,\mathcal{D}_{\text{any}}\right)$. Since we just showed that $\mathrm{Satisfice}_{t}\left(X\mid C,\mathcal{D}_{\text{any}}\right)$ is invariant to joint permutation by the involutions $\phi_{i}$ and since $\phi_{i}\cdot C=C$, $f(X\mid\mathcal{D}_{\text{any}})$ is also invariant to joint permutation by $\phi_{i}$.

Furthermore, if $X^{\prime}\subseteq X$, we have $f(X^{\prime}\mid\mathcal{D}_{\text{any}})\leq f(X\mid\mathcal{D}_{\text{any}})$. Then applying [[#^lemma-b-9-looser|Lemma B.9]], $\mathrm{Satisfice}_{t}\left(B\mid C,\mathbf{u}\right)\eqqcolon f(B\mid\mathcal{D}_{\text{any}})\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}f(A\mid\mathcal{D}_{\text{any}})\coloneqq\mathrm{Satisfice}_{t}\left(A\mid C,\mathbf{u}\right)$.

**[[#^proposition-a-11-orbit|Item 7]].** Suppose $P$ is uniform over $C$ and consider any of the involutions $\phi_{i}$.

$$
M_{q,P}(C\mid\mathbf{u})\coloneqq\inf\left\{M\in\mathbb{R}\mid\mathbb{P}_{\mathbf{x}\sim P}\left(\mathbf{x}^{\top}\mathbf{u}>M\right)\leq q\right\} \\
=\inf\left\{M\in\mathbb{R}\mid\mathbb{P}_{\mathbf{x}\sim P}\left((\mathbf{P}_{\phi_{i}}\mathbf{x})^{\top}(\mathbf{P}_{\phi_{i}}\mathbf{u})>M\right)\leq q\right\} \\
=\inf\left\{M\in\mathbb{R}\mid\mathbb{P}_{\mathbf{x}\sim\phi_{i}\cdot P}\left(\mathbf{x}^{\top}(\mathbf{P}_{\phi_{i}}\mathbf{u})>M\right)\leq q\right\} \\
=\inf\left\{M\in\mathbb{R}\mid\mathbb{P}_{\mathbf{x}\sim P}\left(\mathbf{x}^{\top}(\mathbf{P}_{\phi_{i}}\mathbf{u})>M\right)\leq q\right\} \\
\eqqcolon M_{q,P}(\phi_{i}\cdot C\mid\phi_{i}\cdot\mathbf{u}).
$$

Equation 74 follows by the orthogonality of permutation matrices. Equation 76 follows because if $\mathbf{x}\in\operatorname{supp}(P)=C$, then $\phi_{i}\cdot\mathbf{x}\in C=\operatorname{supp}(P)$, and furthermore $P(\mathbf{x})=P(\mathbf{P}_{\phi_{i}}\mathbf{x})$ by uniformity.

Now we show the invariance of $C_{>M_{q,P}(C\mid\mathbf{u})}$ under joint permutation by $\phi_{i}$:

$$
C_{>M_{q,P}(C\mid\mathbf{u})}\coloneqq\left\{\mathbf{c}\in C\mid\mathbf{c}^{\top}\mathbf{u}>M_{q,P}(C\mid\mathbf{u})\right\} \\
=\left\{\mathbf{c}\in C\mid(\mathbf{P}_{\phi_{i}}\mathbf{c})^{\top}(\mathbf{P}_{\phi_{i}}\mathbf{u})>M_{q,P}(\phi_{i}\cdot C\mid\phi_{i}\cdot\mathbf{u})\right\} \\
=\left\{\mathbf{c}\in\phi_{i}\cdot C\mid\mathbf{c}^{\top}(\mathbf{P}_{\phi_{i}}\mathbf{u})>M_{q,P}(\phi_{i}\cdot C\mid\phi_{i}\cdot\mathbf{u})\right\} \\
\eqqcolon C_{>M_{q,P}(\phi_{i}\cdot C\mid\phi_{i}\cdot\mathbf{u})}.
$$

Equation 79 follows by the orthogonality of permutation matrices and because $M_{q,P}(C\mid\mathbf{u})=M_{q,P}(\phi_{i}\cdot C\mid\phi_{i}\cdot\mathbf{u})$ by eq. 77. A similar proof shows that $C_{=M_{q,P}(C\mid\mathbf{u})}=C_{=M_{q,P}(\phi_{i}\cdot C\mid\phi_{i}\cdot\mathbf{u})}$.

Recall that

$$
Q_{q,P}(X\mid C,\mathbf{u})\coloneqq\sum_{\mathbf{x}\in X}\frac{P(\mathbf{x})}{q}\left(\mathbf{1}_{\mathbf{x}\in C_{>M_{q,P}(C\mid\mathbf{u})}}+\frac{\mathbf{1}_{\mathbf{x}\in C_{=M_{q,P}(C\mid\mathbf{u})}}}{P\left(C_{=M_{q,P}(C\mid\mathbf{u})}\right)}\left(q-P\left(C_{>M_{q,P}(C\mid\mathbf{u})}\right)\right)\right). \tag{82}
$$

$Q_{q,P}(X\mid C,\mathbf{u})=Q_{q,P}(\phi_{i}\cdot X\mid\phi_{i}\cdot C,\phi_{i}\cdot\mathbf{u})$, since $Q$ is the sum of products of $\phi_{i}$\-invariant quantities.

$P(\mathbf{x})$ is non-negative because $P$ is a probability distribution, and $q$ is assumed positive. The indicator functions $\mathbf{1}$ are non-negative. By the definition of $M_{q,P}$, $P\left(C_{>M_{q,P}(C\mid\mathbf{u})}\right)\leq q$. Therefore, eq. 82 is the sum of non-negative terms. Thus, if $X^{\prime}\subseteq X$, then $Q_{q,P}(X^{\prime}\mid C,\mathbf{u})\leq Q_{q,P}(X\mid C,\mathbf{u})$.

Let $f(X\mid\mathbf{u})\coloneqq Q_{q,P}(X\mid C,\mathbf{u})$. Since $\phi_{i}\cdot C=C$ and since $Q_{q,P}(X\mid C,\mathbf{u})=Q_{q,P}(\phi_{i}\cdot X\mid\phi_{i}\cdot C,\phi_{i}\cdot\mathbf{u})$, [[#^lemma-b-10-hiding|Lemma B.10]] shows that $f(X\mid\mathbf{u})$ is also jointly invariant to permutation by $\phi_{i}$. Lastly, if $X^{\prime}\subseteq X$, we have $f(X^{\prime}\mid\mathcal{D}_{\text{any}})\leq f(X\mid\mathcal{D}_{\text{any}})$.

Apply [[#^lemma-b-9-looser|Lemma B.9]] to conclude that $Q_{q,P}(B\mid C,\mathbf{u})\eqqcolon f(B\mid\mathbf{u})\geq_{\text{{most}}\text{: }\mathbb{R}^{d}}^{n}f(A\mid\mathbf{u})\coloneqq Q_{q,P}(A\mid C,\mathbf{u})$. ∎

###### Conjecture B.13 (Orbit tendencies occur for more quantilizer base distributions). ^conjecture-b-13-orbit

[[#^proposition-a-11-orbit|Proposition A.11]]’s [[#^proposition-a-11-orbit|item 7]] holds for any base distribution $P$ over $C$ such that $\min_{\mathbf{b}\in B}P(\mathbf{b})\geq\max_{\mathbf{a}\in A}P(\mathbf{a})$. Furthermore, $Q_{q,P}(X\mid C,\mathbf{u})$ is measurable on $\mathbf{u}$ and so $\geq_{\text{{most}}\text{: }\mathbb{R}^{d}}^{n}$ can be generalized to $\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}$.

## Appendix C Detailed analyses of mr scenarios ^appendix-c-detailed-analyses

### C.1 Action selection ^c-1-action-selection

Consider a bandit problem with five arms $a_{1},\ldots,a_{5}$ partitioned $A\coloneqq\left\{a_{1}\right\},B\coloneqq\left\{a_{2},\ldots,a_{5}\right\}$, which each action has a definite utility $\mathbf{u}_{i}$. There are $T=100$ trials. Suppose the training procedure train uses the $\epsilon$\-greedy strategy to learn value estimates for each arm. At the end of training, train outputs a greedy policy with respect to its value estimates. Consider any action-value initialization, and the learning rate is set $\alpha\coloneqq 1$. To learn an optimal policy, at worst, the agent just has to try each action once.

###### Lemma C.1 (Lower bound on success probability of the train bandit). ^lemma-c-1-lower

_Let $\mathbf{u}\in\mathbb{R}^{5}$ assign strictly maximal utility to $a_{i}$, and suppose train (described above) runs for $T\geq 5$ trials. Then $p_{\textrm{train}}(\left\{a_{i}\right\}\mid\mathbf{u})\geq 1-(1-\frac{\epsilon}{4})^{T}$._

###### Proof. ^proof-14

Since the trained policy can be stochastic,

$$
p_{\textrm{train}}(\left\{a_{i}\right\}\mid\mathbf{u})\geq\mathbb{P}\left(a_{i}\text{ is assigned probability }1\text{ by the learned greedy policy}\right).
$$

Since $a_{i}$ has strictly maximal utility which is deterministic, and since the learning rate $\alpha\coloneqq 1$, if action $a_{i}$ is ever drawn, it is assigned probability $1$ by the learned policy. The probability that $a_{i}$ is never explored is at most $(1-\frac{\epsilon}{4})^{T}$, because at worst, $a_{i}$ is an “explore” action (and not an “exploit” action) at every time step, in which case it is ignored with probability $1-\frac{\epsilon}{4}$. ∎

###### Proposition C.2 (The train bandit is 4-retargetable). ^proposition-c-2-the

$p_{\textrm{train}}$ _is $(\mathbb{R}^{5},A\overset{4}{\to}B)$\-retargetable._

###### Proof. ^proof-15

Let $\phi_{i}\coloneqq a_{1}\leftrightarrow a_{i}$ for $i=2,\ldots,5$ and let $\Theta\coloneqq\mathbb{R}^{5}$. We want to show that whenever $\mathbf{u}\in\mathbb{R}^{5}$ induces $p_{\textrm{train}}(A\mid\mathbf{u})>p_{\textrm{train}}(B\mid\mathbf{u})$, retargeting $\mathbf{u}$ will get train to instead learn to pull a $B$\-action: $p_{\textrm{train}}(A\mid\phi_{i}\cdot\mathbf{u})<p_{\textrm{train}}(B\mid\phi_{i}\cdot\mathbf{u})$.

Suppose we have such a $\mathbf{u}$. If $\mathbf{u}$ is constant, a symmetry argument shows that each action has equal probability of being selected, in which case $p_{\textrm{train}}(A\mid\mathbf{u})=\frac{1}{5}<\frac{4}{5}=p_{\textrm{train}}(B\mid\mathbf{u})$—a contradiction. Therefore, $\mathbf{u}$ is not constant. Similar symmetry arguments show that $A$’s action $a_{1}$ has strictly maximal utility ($\mathbf{u}_{1}>\max_{i=2,\ldots,5}\mathbf{u}_{i}$).

But for $T=100$, [[#^lemma-c-1-lower|Lemma C.1]] shows that $p_{\textrm{train}}(A\mid\mathbf{u})=p_{\textrm{train}}(\left\{a_{1}\right\}\mid\mathbf{u})\approx 1$ and $p_{\textrm{train}}(\left\{a_{i\neq 1}\right\}\mid\mathbf{u})\approx 0\implies p_{\textrm{train}}(B\mid\mathbf{u})=\sum_{i\neq 1}p_{\textrm{train}}(\left\{a_{i}\right\}\mid\mathbf{u})\approx 0$. The converse statement holds when considering $\phi_{i}\cdot\mathbf{u}$ instead of $\mathbf{u}$. Therefore, train satisfies [[#^definition-3-5-multiply|definition 3.5]]’s [[#^definition-3-5-multiply|item 1]] (retargetability). These $\phi_{i}\cdot\mathbf{u}\in\Theta\coloneqq\mathbb{R}^{5}$ because $\mathbb{R}^{5}$ is closed under permutation by $S_{5}$, satisfying [[#^definition-3-5-multiply|item 2]].

Consider another $\mathbf{u}^{\prime}\in\mathbb{R}^{5}$ such that $p_{\textrm{train}}(A\mid\mathbf{u}^{\prime})>p_{\textrm{train}}(B\mid\mathbf{u}^{\prime})$, and consider $i\neq j$. By the above symmetry arguments, $\mathbf{u}^{\prime}$ must also assign $a_{1}$ maximal utility. By [[#^lemma-c-1-lower|Lemma C.1]], $p_{\textrm{train}}(\left\{a_{i}\right\}\mid\phi_{i}\cdot\mathbf{u})\approx 1$ and $p_{\textrm{train}}(\left\{a_{j}\right\}\mid\phi_{i}\cdot\mathbf{u})\approx 0$ since $i\neq j$, and vice versa when considering $\phi_{j}\cdot\mathbf{u}$ instead of $\phi_{i}\cdot\mathbf{u}$. Then since $\phi_{i}\cdot\mathbf{u}$ and $\phi_{j}\cdot\mathbf{u}$ induce distinct probability distributions over learned actions, they cannot be the same utility function. This satisfies [[#^definition-3-5-multiply|item 3]]. ∎

###### Corollary C.3 (The train bandit has orbit-level tendencies). ^corollary-c-3-the

$p_{\textrm{train}}(B\mid\mathbf{u})\geq^{4}_{\text{most: }\mathbb{R}^{5}}p_{\textrm{train}}(A\mid\mathbf{u})$.

###### Proof. ^proof-16

Combine [[#^proposition-c-2-the|Proposition C.2]] and [[#^theorem-3-6-multiply|Theorem 3.6]]. ∎

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/turner-parametrically-retargetable-decision-makers-tend-to-seek-power-img6-be6ace6b.png)

Figure 3: Map of the first level of Montezuma’s Revenge. ^figure-3

### C.2 Observation reward maximization ^c-2-observation-reward

Let $T$ be a reasonably long rollout length, so that $O_{T\text{-reach}}$ is large—many different step-$T$ observations can be induced.

###### Proposition C.4 (Final reward maximization has strong orbit-level incentives in mr). ^proposition-c-4-final

_Let $n\coloneqq\lfloor\frac{\left|O_{\text{leave}}\right|}{\left|O_{\text{stay}}\right|}\rfloor$. $p_{\text{max}}(O_{\text{leave}}\mid R)\geq_{\text{{most}}\text{: }\mathbb{R}^{\mathcal{O}}}^{n}p_{\text{max}}(O_{\text{stay}}\mid R)$._

###### Proof. ^proof-17

Consider the vector space representation of observations, $\mathbb{R}^{\left|\mathcal{O}\right|}$. Define $A\coloneqq\{\mathbf{e}_{o}\mid o\in O_{\text{stay}}\},B\coloneqq\{\mathbf{e}_{o}\mid o\in O_{\text{leave}}\}$, and $C\coloneqq O_{T\text{-reach}}=A\cup B$ the union of $O_{\text{stay}},O_{\text{leave}}$.

Since $\left|O_{\text{leave}}\right|\geq\left|O_{\text{stay}}\right|$ by assumption that $T$ is reasonably large, consider the involution $\phi_{1}\in S_{\left|\mathcal{O}\right|}$ which embeds $O_{\text{stay}}$ into $O_{\text{leave}}$, while fixing all other observations. If possible, produce another involution $\phi_{2}$ which also embeds $O_{\text{stay}}$ into $O_{\text{leave}}$, which fixes all other observations, and which “doesn’t interfere with $\phi_{1}$” (_i_._e_., $\phi_{2}\cdot(\phi_{1}\cdot A)=\phi_{1}\cdot A$). We can produce $n\coloneqq\lfloor\frac{\left|O_{\text{leave}}\right|}{\left|O_{\text{stay}}\right|}\rfloor$ such involutions. Therefore, $B$ contains $n$ copies ([[#^definition-a-7-containment|definition A.7]]) of $A$ via involutions $\phi_{1},\ldots,\phi_{n}$. Furthermore, $\phi_{i}\cdot(A\cup B)=A\cup B$, since each $\phi_{i}$ swaps $A$ with $B^{\prime}\subseteq B$, and fixes all $\mathbf{b}\in B\setminus B^{\prime}$ by assumption. Thus, $\phi\cdot C=C$.

By [[#^proposition-a-11-orbit|Proposition A.11]]’s [[#^proposition-a-11-orbit|item 2]], $\mathrm{FracOptimal}\left(B\mid C,R\right)\geq_{\text{{most}}\text{: }\mathbb{R}^{\mathcal{O}}}^{n}\mathrm{FracOptimal}\left(A\mid C,R\right)$. Since $p_{\text{max}}$ uniformly randomly chooses a maximal-reward observation to induce, $\forall X\subseteq C\mathrel{\mathop{\ordinarycolon}}p_{\text{max}}(X\mid R)=\mathrm{FracOptimal}\left(X\mid C,R\right)$. Therefore, $p_{\text{max}}(O_{\text{leave}}\mid R)\geq_{\text{{most}}\text{: }\mathbb{R}^{\mathcal{O}}}^{n}p_{\text{max}}(O_{\text{stay}}\mid R)$. ∎

We want to reason about the probability that $\mathrm{decide}$ leaves the initial room by time $T$ in its rollout trajectories.

$$
p_{\mathrm{decide}}(\text{leave}\mid\theta)\coloneqq\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ has left the first room by step }T\right), \\
p_{\mathrm{decide}}(\text{stay}\mid\theta)\coloneqq\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ has not left the first room by step }T\right).
$$

We want to show that reward maximizers tend to leave the room: $p_{\max}(\text{leave}\mid R)\geq_{\text{{most}}\text{: }\Theta}^{n}p_{\max}(\text{stay}\mid R)$. However, we must be careful: In general, $p_{\text{max}}(O_{\text{leave}}\mid R)\neq p_{\max}(\text{leave}\mid R)$ and $p_{\text{max}}(O_{\text{stay}}\mid R)\neq p_{\max}(\text{stay}\mid R)$. For example, suppose that $o_{T}\in O_{\text{leave}}$. By the definition of $O_{\text{leave}}$, $o_{T}$ can only be observed if the agent has left the room by time step $T$, and so the trajectory $\tau$ must have left the first room. The converse argument does not hold: The agent could leave the first room, re-enter, and then wait until time $T$. Although one of the doors would have been opened ([[#^figure-2|fig. 2]]), the agent can also open the door without leaving the room, and then realize the same step-$T$ observation. Therefore, this observation doesn’t belong to $O_{\text{leave}}$.

###### Lemma C.5 (Room-status inequalities for mr). ^lemma-c-5-room-status

$$
p_{\mathrm{decide}}(\text{stay}\mid\theta)\leq p_{\mathrm{decide}}(O_{\text{stay}}\mid\theta), \tag{85}
$$

$$
\text{and }p_{\mathrm{decide}}(O_{\text{leave}}\mid\theta)\leq p_{\mathrm{decide}}(\text{leave}\mid\theta). \tag{86}
$$

###### Proof. ^proof-18

For any $\mathrm{decide}$,

$$
p_{\mathrm{decide}}(\text{stay}\mid\theta)=\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ stays through step }T\right) \\
=\sum_{o\in\mathcal{O}}\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\text{ at step }T\text{ of }\tau\right)\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ stays}\mid o\text{ at step }T\right) \\
=\sum_{o\in O_{T\text{-reach}}}\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\text{ at step }T\right)\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ stays}\mid o\text{ at step }T\right) \\
=\sum_{o\in O_{\text{stay}}}\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\text{ at step }T\right)\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ stays}\mid o\text{ at step }T\right) \\
\leq\sum_{o\in O_{\text{stay}}}\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\text{ at step }T\right) \\
=\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{stay}}\right) \\
\eqqcolon p_{\mathrm{decide}}(O_{\text{stay}}\mid\theta).
$$

Equation 90 holds because the definition of $O_{T\text{-reach}}$ ensures that if $o\not\in O_{T\text{-reach}}$, then $\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\mid\theta\right)=0$. Because $o\in O_{T\text{-reach}}\setminus O_{\text{stay}}$ implies that $\tau$ left and so

$$
\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ stays}\mid o\text{ at step }T\right)=0,
$$

eq. 91 follows. Then we have shown eq. 85.

For eq. 86,

$$
p_{\mathrm{decide}}(O_{\text{leave}}\mid\theta)\coloneqq\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{leave}}\right) \\
=\sum_{o\in O_{\text{leave}}}\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\text{ at step }T\right) \\
=\sum_{o\in O_{\text{leave}}}\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\text{ at step }T\right)\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ leaves by step }T\mid o\text{ at step }T\right) \\
=\sum_{o\in\mathcal{O}}\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o\text{ at step }T\right)\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ leaves by step }T\mid o\text{ at step }T\right) \\
=\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ has left the first room by step }T\right) \\
\eqqcolon p_{\mathrm{decide}}(\text{leave}\mid\theta).
$$

Equation 98 follows because, since $o\in O_{\text{leave}}$ are only realizable by leaving the first room, this implies $\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}(\theta),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(\tau\text{ leaves by step }T\mid o\text{ at step }T\right)=1$. Equation 99 follows because $O_{\text{leave}}\subseteq\mathcal{O}$, and probabilities are non-negative. Then we have shown eq. 86. ∎

###### Corollary C.6 (Final reward maximizers tend to leave the first room in mr). ^corollary-c-6-final

$$
p_{\max}(\text{leave}\mid R)\geq_{\text{{most}}\text{: }\mathbb{R}^{\mathcal{O}}}^{n}p_{\max}(\text{stay}\mid R).
$$

###### Proof. ^proof-19

Using [[#^lemma-c-5-room-status|Lemma C.5]] and [[#^proposition-c-4-final|Proposition C.4]], apply [[#^lemma-b-1-limited|Lemma B.1]] with $f_{0}(R)\coloneqq p_{\max}(\text{leave}\mid R),f_{1}(R)\coloneqq p_{\text{max}}(O_{\text{leave}}\mid R),f_{2}(R)\coloneqq p_{\text{max}}(O_{\text{stay}}\mid R),f_{3}(R)\coloneqq p_{\max}(\text{stay}\mid R)$ to conclude that $p_{\max}(\text{leave}\mid R)\geq_{\text{{most}}\text{: }\mathbb{R}^{\mathcal{O}}}^{n}p_{\max}(\text{stay}\mid R).$ ∎

### C.3 Featurized reward maximization ^c-3-featurized-reward

$\Theta\coloneqq\mathbb{R}^{\mathcal{O}}$ assumes we will specify complicated reward functions over observations, with $\left|\mathcal{O}\right|$ degrees of freedom in their specification. Any observation can get any number. However, reward functions are often specified more compactly. For example, in [[#^4-3-tendencies-for|section 4.3]], the (additively) featurized reward function $R_{\textrm{feat}}(o_{T})\coloneqq\textrm{feat}(o_{T})^{\top}\alpha$ has four degrees of freedom. Compared to typical reward functions (which would look like “random noise” to a human), $R_{\textrm{feat}}$ more easily trains competent policies because of the regularities between the reward and the state features.

In this setup, $p_{\text{max}}$ chooses a policy which induces a step-$T$ observation with maximal reward. Reward depends only on the feature vector of the final observation—more specifically, on the agent’s item counts. There are more possible item counts available by first leaving the room, than by staying.

We will now conduct a more detailed analysis and conclude that $p_{\text{max}}(O_{\text{leave}}\mid\alpha)\geq_{\text{{most}}\text{: }\mathbb{R}^{4}}^{3}p_{\text{max}}(O_{\text{stay}}\mid\alpha)$. Informally, we can retarget which items the agent prioritizes, and thereby retarget from $O_{\text{stay}}$ to $O_{\text{leave}}$.

Consider the featurization function which takes as input an observation $o\in\mathcal{O}$:

$$
\textrm{feat}(o)\coloneqq\begin{pmatrix}\text{\# of keys in inventory shown by }o\\
\text{\# of swords in inventory shown by }o\\
\text{\# of torches in inventory shown by }o\\
\text{\# of amulets in inventory shown by }o\end{pmatrix}.
$$

Consider $A_{\text{feat}}\coloneqq\left\{\textrm{feat}(o)\mid o\in O_{\text{stay}}\right\},B_{\text{feat}}\coloneqq\left\{\textrm{feat}(o)\mid o\in O_{\text{leave}}\right\}$.

Let $\mathbf{e}_{i}\in\mathbb{R}^{4}$ be the standard basis vector with a $1$ in entry $i$ and $0$ elsewhere. When restricted to the room shown in [[#^figure-2|fig. 2]], the agent can either acquire the key in the first room and retain it until step $T$ ($\mathbf{e}_{1}$), or reach time step $T$ empty-handed ($\mathbf{0}$). We conclude that $A_{\text{feat}}=\left\{\mathbf{e}_{1},\mathbf{0}\right\}$.

For $B_{\text{feat}}$, recall that in [[#^4-2-tendencies-for|section 4.2]] we assumed the rollout length $T$ to be reasonably large. Then by leaving the room, some realizable trajectory induces $o_{T}$ displaying an inventory containing only a sword ($\mathbf{e}_{2}$), or only a torch ($\mathbf{e}_{3}$), or only an amulet ($\mathbf{e}_{4}$), or nothing at all ($\mathbf{0}$). Therefore, $\left\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4},\mathbf{0}\right\}\subseteq B_{\text{feat}}$. $B_{\text{feat}}$ contains $3$ copies of $A_{\text{feat}}$ ([[#^definition-a-7-containment|definition A.7]]) via involutions $\phi_{i}\mathrel{\mathop{\ordinarycolon}}1\leftrightarrow i$, $i\neq 1$. Suppose all feature coefficient vectors $\alpha\in\mathbb{R}^{4}$ are plausible. Then $\Theta\coloneqq\mathbb{R}^{4}$.

Let us be more specific about what is entailed by featurized reward maximization. The $\mathrm{decide}_{\max}(\alpha)$ procedure takes $\alpha$ as input and then considers the reward function $o\mapsto\textrm{feat}(o)^{\top}\alpha$. Then, $\mathrm{decide}_{\max}$ uniformly randomly chooses an observation $o_{T}\in O_{T\text{-reach}}$ which maximizes this featurized reward, and then uniformly randomly chooses a policy which implements $o_{T}$.

###### Lemma C.7 ($\mathrm{FracOptimal}$ inequalities). ^lemma-c-7-mathrm

_Let $X\subseteq Y^{\prime}\subseteq Y\subsetneq\mathbb{R}^{d}$ be finite, and let $\mathbf{u}\in\mathbb{R}^{d}$. Then_

$$
\mathrm{FracOptimal}\left(X\mid Y,\mathbf{u}\right)\leq\mathrm{FracOptimal}\left(X\mid Y^{\prime},\mathbf{u}\right)\leq\mathrm{FracOptimal}\left(X\cup(Y\setminus Y^{\prime})\mid Y,\mathbf{u}\right).
$$

###### Proof. ^proof-20

For finite $X_{1}\subsetneq\mathbb{R}^{d}$, let $\mathrm{Best}\left(X_{1}\mid\mathbf{u}\right)\coloneqq\argmax_{\mathbf{x}_{1}\in X_{1}}\mathbf{x}_{1}^{\top}\mathbf{u}$. Suppose $\mathbf{y}^{\prime}\in\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)$, but $\mathbf{y}^{\prime}\not\in\mathrm{Best}\left(Y\mid\mathbf{u}\right)$. Then for all $\mathbf{a}\in\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)$,

$$
\mathbf{a}^{\top}\mathbf{u}=\mathbf{y}^{\prime\top}\mathbf{u}<\max_{\mathbf{y}\in Y}\mathbf{y}^{\top}\mathbf{u}.
$$

So $\mathbf{a}\not\in\mathrm{Best}\left(Y\mid\mathbf{u}\right)$. Then either $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\subseteq\mathrm{Best}\left(Y\mid\mathbf{u}\right)$, or the two sets are disjoint.

$$
\mathrm{FracOptimal}\left(X\mid Y,\mathbf{u}\right)\coloneqq\frac{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap X\right|}{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\right|} \\
\leq\frac{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\right|}{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\right|}\eqqcolon\mathrm{FracOptimal}\left(X\mid Y^{\prime},\mathbf{u}\right)
$$

If $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\subseteq\mathrm{Best}\left(Y\mid\mathbf{u}\right)$, then since $X\subseteq Y^{\prime}$, we have $X\cap\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)=X\cap\mathrm{Best}\left(Y\mid\mathbf{u}\right)$. Then in this case, eq. 106 has equal numerator and larger denominator than eq. 107. On the other hand, if $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap\mathrm{Best}\left(Y\mid\mathbf{u}\right)=\varnothing$, then since $X\subseteq Y^{\prime}$, $X\cap\mathrm{Best}\left(Y\mid\mathbf{u}\right)=\varnothing$. Then eq. 106 equals $0$, and eq. 107 is non-negative. Either way, eq. 107’s inequality holds. To show the second inequality, we handle the two cases separately.

##### Subset case. ^subset-case

Suppose that $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\subseteq\mathrm{Best}\left(Y\mid\mathbf{u}\right)$.

$$
\frac{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\right|}{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\right|}\leq\frac{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\right|+\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|}{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\right|+\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\right|+\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})\right|}{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\right|+\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\right|+\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})\right|}{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\right|+\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\right|+\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})\right|}{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap X\right|+\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})\right|}{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap(X\cup(Y\setminus Y^{\prime}))\right|}{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\right|} \\
\eqqcolon\mathrm{FracOptimal}\left(X\cup(Y\setminus Y^{\prime})\mid Y,\mathbf{u}\right).
$$

Equation 108 follows because when $n\leq d,k\geq 0$, we have $\frac{n}{d}\leq\frac{n+k}{d+k}$. For eq. 110, since $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\subseteq\mathrm{Best}\left(Y\mid\mathbf{u}\right)$, we must have

$$
\mathrm{Best}\left(Y\mid\mathbf{u}\right)=\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cup\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right).
$$

But then

$$
\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})=\left(\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})\right)\cup\left(\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})\right) \\
=\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime}).
$$

Then eq. 110 follows. Equation 111 follows since

$$
\mathrm{Best}\left(Y\mid\mathbf{u}\right)=\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cup\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right).
$$

Equation 112 follows since $X\subseteq Y^{\prime}$, and so

$$
\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X=\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap X.
$$

Equation 113 follows because $X\subseteq Y^{\prime}$ is disjoint of $Y\setminus Y^{\prime}$. We have shown that

$$
\mathrm{FracOptimal}\left(X\mid Y^{\prime},\mathbf{u}\right)\leq\mathrm{FracOptimal}\left(X\cup(Y\setminus Y^{\prime})\mid Y,\mathbf{u}\right)
$$

in this case.

##### Disjoint case. ^disjoint-case

Suppose that $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap\mathrm{Best}\left(Y\mid\mathbf{u}\right)=\varnothing$.

$$
\frac{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\right|}{\left|\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\right|}\leq 1 \\
=\frac{\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|}{\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cap(Y\setminus Y^{\prime})\right|}{\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cap(X\cup(Y\setminus Y^{\prime}))\right|}{\left|\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\right|} \\
=\frac{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\cap(X\cup(Y\setminus Y^{\prime}))\right|}{\left|\mathrm{Best}\left(Y\mid\mathbf{u}\right)\right|} \\
\eqqcolon\mathrm{FracOptimal}\left(X\cup(Y\setminus Y^{\prime})\mid Y,\mathbf{u}\right).
$$

Equation 117 follows because $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap X\subseteq\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)$. For eq. 120, note that we trivially have $\mathrm{Best}\left(Y^{\prime}\mid\mathbf{u}\right)\cap\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)=\varnothing$, and also that $X\subseteq Y^{\prime}$. Therefore, $\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)\cap X=\varnothing$, and eq. 120 follows. Finally, the disjointness assumption implies that

$$
\max_{\mathbf{y}^{\prime}\in Y^{\prime}}\mathbf{y}^{\prime\top}\mathbf{u}<\max_{\mathbf{y}\in Y}\mathbf{y}^{\top}\mathbf{u}.
$$

Therefore, the optimal elements of $Y$ must come exclusively from $Y\setminus Y^{\prime}$; _i_._e_., $\mathrm{Best}\left(Y\mid\mathbf{u}\right)=\mathrm{Best}\left(Y\setminus Y^{\prime}\mid\mathbf{u}\right)$. Then eq. 121 follows, and we have shown that

$$
\mathrm{FracOptimal}\left(X\mid Y^{\prime},\mathbf{u}\right)\leq\mathrm{FracOptimal}\left(X\cup(Y\setminus Y^{\prime})\mid Y,\mathbf{u}\right)
$$

in this case. ∎

###### Conjecture C.8 (Generalizing [[#^lemma-c-7-mathrm|Lemma C.7]]). ^conjecture-c-8-generalizing

[[#^lemma-c-7-mathrm|Lemma C.7]] and Turner et al. \[2021\]’s Lemma E.26 have extremely similar functional forms. How can they be unified?

###### Proposition C.9 (Featurized reward maximizers tend to leave the first room in mr). ^proposition-c-9-featurized

$$
p_{\max}(\text{leave}\mid\alpha)\geq_{\text{{most}}\text{: }\mathbb{R}^{4}}^{3}p_{\max}(\text{stay}\mid\alpha).
$$

###### Proof. ^proof-21

We want to show that $p_{\text{max}}(O_{\text{leave}}\mid\alpha)\geq_{\text{{most}}\text{: }\mathbb{R}^{4}}^{n}p_{\text{max}}(O_{\text{stay}}\mid\alpha)$. Recall that $A_{\text{feat}}=\{\mathbf{e}_{1},\mathbf{0}\},B^{\prime}_{\text{feat}}\coloneqq\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\}\subseteq B_{\text{feat}}$.

$$
p_{\max}(\text{stay}\mid\alpha)\leq p_{\text{max}}(O_{\text{stay}}\mid\alpha) \\
\coloneqq\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{stay}}\right) \\
=\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{stay}},\textrm{feat}(o_{T})\neq\mathbf{0}\right)+\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{stay}},\textrm{feat}(o_{T})=\mathbf{0}\right) \\
\leq\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{1}\right\}\mid C_{\text{feat}},\alpha\right)+\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{stay}},\textrm{feat}(o_{T})=\mathbf{0}\right) \\
\leq\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{1}\right\}\mid\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\},\alpha\right)+\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{stay}},\textrm{feat}(o_{T})=\mathbf{0}\right) \\
\leq_{\text{{most}}\text{: }\mathbb{R}^{4}_{>0}}^{3}\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\}\mid\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\},\alpha\right) \\
\phantom{\leq\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{1}\right\}\mid\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\},\alpha\right)}+\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{leave}},\textrm{feat}(o_{T})=\mathbf{0}\right) \\
\leq\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\}\cup(C_{\text{feat}}\setminus\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\})\mid C_{\text{feat}},\alpha\right) \\
=\mathrm{FracOptimal}\left(C_{\text{feat}}\setminus\left\{\mathbf{e}_{1}\right\}\mid C_{\text{feat}},\alpha\right) \\
\leq\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{leave}}\right) \\
\eqqcolon p_{\text{max}}(O_{\text{leave}}\mid\alpha) \\
\leq p_{\max}(\text{leave}\mid\alpha).
$$

Equation 124 and eq. 135 hold by [[#^lemma-c-5-room-status|Lemma C.5]]. If $o_{T}\in O_{\text{stay}}$ is realized by $p_{\text{max}}$ and $\textrm{feat}(o_{T})\neq\mathbf{0}$, then we must have $\textrm{feat}(o_{T})=\{\mathbf{e}_{1}\}$ be optimal and so the $\mathbf{e}_{1}$ inventory configuration is realized. Therefore, eq. 128 follows. Equation 129 follows by applying the first inequality of [[#^lemma-c-7-mathrm|Lemma C.7]] with $X\coloneqq\{\mathbf{e}_{1}\},Y^{\prime}\coloneqq\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\},Y\coloneqq C_{\text{feat}}$.

By applying [[#^proposition-a-11-orbit|Proposition A.11]]’s [[#^proposition-a-11-orbit|item 2]] with $A\coloneqq A_{\text{feat}}=\{\mathbf{e}_{1}\}$, $B^{\prime}\coloneqq B^{\prime}_{\text{feat}}=\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\}$, $C\coloneqq A\cup B^{\prime}$, we have

$$
\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{1}\right\}\mid\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\},\alpha\right)\leq_{\text{{most}}\text{: }\mathbb{R}^{4}_{>0}}^{3}\\
\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\}\mid\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\},\alpha\right).
$$

Furthermore, observe that

$$
\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{stay}},\textrm{feat}(o_{T})=\mathbf{0}\right)\leq\mathbb{P}_{\begin{subarray}{c}\pi\sim\mathrm{decide}_{\max}(\alpha),\\ \tau\sim\pi\mid s_{0}\end{subarray}}\left(o_{T}\in O_{\text{leave}},\textrm{feat}(o_{T})=\mathbf{0}\right)
$$

because either $\mathbf{0}$ is not optimal (in which case both sides equal 0), or else $\mathbf{0}$ is optimal, in which case the right side is strictly greater. This can be seen by considering how $\mathrm{decide}_{\max}(\alpha)$ uniformly randomly chooses an observation in which the agent ends up with an empty inventory. As argued previously, the vast majority of such observations can only be induced by leaving the first room.

Combining eq. 136 and eq. 137, eq. 130 follows. Equation 131 follows by applying the second inequality of [[#^lemma-c-7-mathrm|Lemma C.7]] with $X\coloneqq\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\}$, $Y^{\prime}\coloneqq\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\}$, $Y\coloneqq C_{\text{feat}}$. If $\textrm{feat}(o_{T})\in B_{\text{feat}}$ is realized by $p_{\text{max}}$, then by the definition of $B_{\text{feat}}$, $o_{T}\in O_{\text{leave}}$ is realized, and so eq. 133 follows.

Then by applying [[#^lemma-b-1-limited|Lemma B.1]] with

$$
f_{0}(\alpha)\coloneqq p_{\max}(\text{leave}\mid\alpha), \\
f_{1}(\alpha)\coloneqq\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{1}\right\}\mid\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\},\alpha\right), \\
f_{2}(\alpha)\coloneqq\mathrm{FracOptimal}\left(\left\{\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\}\mid\left\{\mathbf{e}_{1},\mathbf{e}_{2},\mathbf{e}_{3},\mathbf{e}_{4}\right\},\alpha\right), \\
f_{3}(\alpha)\coloneqq p_{\max}(\text{stay}\mid\alpha),
$$

we conclude that $p_{\max}(\text{leave}\mid\alpha)\geq_{\text{{most}}\text{: }\mathbb{R}^{4}_{>0}}^{3}p_{\max}(\text{stay}\mid\alpha).$ ∎

Lastly, note that if $\mathbf{0}\in\Theta$ and $f(A\mid\mathbf{0})>f(B\mid\mathbf{0})$, $f$ cannot be even be simply retargetable for the $\Theta$ parameter set. This is because $\forall\phi\in S_{d}$, $\phi\cdot\mathbf{0}=\mathbf{0}$. For example, inductive bias ensures that, absent a reward signal, learned policies tend to stay in the initial room in mr. This is one reason why [[#^4-3-tendencies-for|section 4.3]]’s analysis of the policy tendencies of reinforcement learning excludes the all-zero reward function.

### C.4 Reasoning for why dqn can’t explore well ^c-4-reasoning-for

In [[#^4-3-tendencies-for|section 4.3]], we wrote:

> Mnih et al. \[2015\]’s dqn isn’t good enough to train policies which leave the first room of mr, and so dqn (trivially) cannot be retargetable _away_ from the first room via the reward function. There isn’t a single featurized reward function for which dqn visits other rooms, and so we can’t have $\alpha$ such that $\phi\cdot\alpha$ retargets the agent to $O_{\text{leave}}$. dqn isn’t good enough at exploring.

We infer this is true from Nair et al. \[2015\], which shows that vanilla dqn gets zero score in mr. Thus, dqn never even gets the first key. Thus, dqn only experiences state-action-state transitions which didn’t involve acquiring an item, since (as shown in [[#^figure-3|fig. 3]]) the other items are outside of the first room, which requires a key to exit. In our analysis, we considered a reward function which is featurized over item acquisition.

Therefore, for all pre-key-acquisition state-action-state transitions, the featurized reward function returns exactly the same reward signals as those returned in training during the published experiments (namely, zero, because dqn can never even get to the key in order to receive a reward signal). That is, since dqn only experiences state-action-state transitions which didn’t involve acquiring an item, and the featurized reward functions only reward acquiring an item, it doesn’t matter what reward values are provided upon item acquisition—dqn’s trained behavior will be the same. Thus, a dqn agent trained on any featurized reward function will not explore outside of the first room.

## Appendix D Lower bounds on mdp power-seeking incentives for optimal policies ^appendix-d-lower-bounds

Turner et al. \[2021\] prove conditions under which _at least half_ of the orbit of every reward function incentivizes power-seeking behavior. For example, in [[#^figure-4|fig. 4]], they prove that avoiding $\varnothing$ maximizes average per-timestep reward for at least half of reward functions. Roughly, there are more self-loop states ($\varnothing$, $\ell_{\swarrow}$, $r_{\searrow}$, $r_{\nearrow}$) available if the agent goes `left` or `right` instead of up towards $\varnothing$. We strengthen this claim, with [[#^corollary-d-12-quantitatively|Corollary D.12]] showing that for _at least three-quarters_ of the orbit of every reward function, it is average-optimal to avoid $\varnothing$.

Therefore, we answer Turner et al. \[2021\]’s open question of whether increased number of environmental symmetries quantitatively strengthens the degree to which power-seeking is incentivized. The answer is _yes_. In particular, it may be the case that only one in a million state-based reward functions makes it average-optimal for Pac-Man to die immediately.

![Figure 4](https://arxiv.org/html/2206.13477v2/case-fig.svg)

Figure 4: A toy mdp for reasoning about power-seeking tendencies. _Reproduced from Turner et al. \[2021\]._ ^figure-4

We will briefly restate several definitions needed for our key results, [[#^theorem-d-11-quantitatively|Theorem D.11]] and [[#^corollary-d-12-quantitatively|Corollary D.12]]. For explanation, see Turner et al. \[2021\].

###### Definition D.1 (Non-dominated linear functionals). ^definition-d-1-non-dominated

Let $X\subsetneq\mathbb{R}^{\left|\mathcal{S}\right|}$ be finite. $\text{{ND}}\left(X\right)\coloneqq\left\{\mathbf{x}\in X\mid\exists\mathbf{r}\in\mathbb{R}^{\left|\mathcal{S}\right|}\mathrel{\mathop{\ordinarycolon}}\mathbf{x}^{\top}\mathbf{r}>\max_{\mathbf{x}^{\prime}\in X\setminus\left\{\mathbf{x}\right\}}\mathbf{x}^{\prime\top}\mathbf{r}\right\}$.

###### Definition D.2 (Bounded reward function distribution). ^definition-d-2-bounded

$\mathfrak{D}_{\text{bound}}$ is the set of bounded-support probability distributions $\mathcal{D}_{\text{bound}}$.

###### Remark. ^remark-5

When $n=1$, [[#^lemma-d-3-quantitative|Lemma D.3]] reduces to the first part of Turner et al. \[2021\]’s lemma E.24, and [[#^lemma-d-5-quantitative|Lemma D.5]] reduces to the first part of Turner et al. \[2021\]’s lemma E.28.

###### Lemma D.3 (Quantitative expectation superiority lemma). ^lemma-d-3-quantitative

_Let $A,B\subsetneq\mathbb{R}^{d}$ be finite and let $g\mathrel{\mathop{\ordinarycolon}}\mathbb{R}\to\mathbb{R}$ be a (total) increasing function. Suppose $B$ contains $n$ copies of $\text{{ND}}\left(A\right)$. Then_

$$
\mathbb{E}_{\mathbf{r}\sim\mathcal{D}_{\text{bound}}}\left[g\left(\max_{\mathbf{b}\in B}\mathbf{b}^{\top}\mathbf{r}\right)\right]\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{bound}}}^{n}\mathbb{E}_{\mathbf{r}\sim\mathcal{D}_{\text{bound}}}\left[g\left(\max_{\mathbf{a}\in A}\mathbf{a}^{\top}\mathbf{r}\right)\right].
$$

###### Proof. ^proof-22

Because $g\mathrel{\mathop{\ordinarycolon}}\mathbb{R}\to\mathbb{R}$ is increasing, it is measurable (as is $\max$).

Let $L\coloneqq\inf_{\mathbf{r}\in\operatorname{supp}(\mathcal{D}_{\text{bound}})}\max_{\mathbf{x}\in X}\mathbf{x}^{\top}\mathbf{r},U\coloneqq\sup_{\mathbf{r}\in\operatorname{supp}(\mathcal{D}_{\text{bound}})}\max_{\mathbf{x}\in X}\mathbf{x}^{\top}\mathbf{r}$. Both exist because $\mathcal{D}_{\text{bound}}$ has bounded support. Furthermore, since $g$ is monotone increasing, it is bounded $[g(L),g(U)]$ on $[L,U]$. Therefore, $g$ is measurable and bounded on each $\operatorname{supp}(\mathcal{D}_{\text{bound}})$, and so the relevant expectations exist for all $\mathcal{D}_{\text{bound}}$.

For finite $X\subsetneq\mathbb{R}^{d}$, let $f(X\mid\mathbf{u})\coloneqq g(\max_{\mathbf{x}\in X}\mathbf{x}^{\top}\mathbf{u})$. By [[#^lemma-b-11-eu-determined|Lemma B.11]], $f$ is invariant under joint permutation by $S_{d}$. Furthermore, $f$ is measurable because $g$ and $\max$ are. Therefore, apply [[#^lemma-b-5-expectations|Lemma B.5]] to conclude that $f(X\mid\mathcal{D}_{\text{bound}})\coloneqq\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{bound}}}\left[g(\max_{\mathbf{x}\in X}\mathbf{x}^{\top}\mathbf{u})\right]$ is also invariant under joint permutation by $S_{d}$ (with $f$ being bounded when restricted to $\operatorname{supp}(\mathcal{D}_{\text{bound}})$). Lastly, if $X^{\prime}\subseteq X$, $f(X^{\prime}\mid\mathcal{D}_{\text{bound}})\leq f(X\mid\mathcal{D}_{\text{bound}})$ because $g$ is increasing.

$$
\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{bound}}}\left[g\left(\max_{\mathbf{a}\in A}\mathbf{a}^{\top}\mathbf{u}\right)\right]=\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{bound}}}\left[g\left(\max_{\mathbf{a}\in\text{{ND}}\left(A\right)}\mathbf{a}^{\top}\mathbf{u}\right)\right] \\
\leq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathbb{E}_{\mathbf{r}\sim\mathcal{D}_{\text{bound}}}\left[g\left(\max_{\mathbf{b}\in B}\mathbf{b}^{\top}\mathbf{r}\right)\right].
$$

Equation 143 follows by corollary E.11 of \[Turner et al., 2021\]. Equation 144 follows by applying [[#^lemma-b-9-looser|Lemma B.9]] with $f$ as defined above with the $\phi_{1},\ldots,\phi_{n}$ guaranteed by the copy assumption. ∎

###### Definition D.4 (Linear functional optimality probability \[Turner et al., 2021\]). ^definition-d-4-linear

For finite $A,B\subsetneq\mathbb{R}^{\left|\mathcal{S}\right|}$, the _probability under $\mathcal{D}_{\text{any}}$ that $A$ is optimal over $B$_ is

$$
p_{\mathcal{D}_{\text{any}}}\left(A\geq B\right)\coloneqq\mathbb{P}_{\mathbf{r}\sim\mathcal{D}_{\text{any}}}\left(\max_{\mathbf{a}\in A}\mathbf{a}^{\top}\mathbf{r}\geq\max_{\mathbf{b}\in B}\mathbf{b}^{\top}\mathbf{r}\right).
$$

###### Lemma D.5 (Quantitative optimality probability superiority lemma). ^lemma-d-5-quantitative

_Let $A,B,C\subsetneq\mathbb{R}^{d}$ be finite and let $Z$ satisfy $\text{{ND}}\left(C\right)\subseteq Z\subseteq C$. Suppose that $B$ contains $n$ copies of $\text{{ND}}\left(A\right)$ via involutions $\phi_{i}$. Furthermore, let $B_{\text{extra}}\coloneqq B\setminus\left(\cup_{i=1}^{n}\phi_{i}\cdot\text{{ND}}\left(A\right)\right)$; suppose that for all $i$, $\phi_{i}\cdot\left(Z\setminus B_{\text{extra}}\right)=Z\setminus B_{\text{extra}}$._

_Then $p_{\mathcal{D}_{\text{any}}}\left(B\geq C\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}p_{\mathcal{D}_{\text{any}}}\left(A\geq C\right)$._

###### Proof. ^proof-23

For finite $X,Y\subsetneq\mathbb{R}^{d}$, let

$$
g(X,Y\mid\mathcal{D}_{\text{any}})\coloneqq p_{\mathcal{D}_{\text{any}}}\left(X\geq Y\right)=\mathbb{E}_{\mathbf{u}\sim\mathcal{D}_{\text{any}}}\left[\mathbf{1}_{\max_{\mathbf{x}\in X}\mathbf{x}^{\top}\mathbf{u}\geq\max_{\mathbf{y}\in Y}\mathbf{y}^{\top}\mathbf{u}}\right].
$$

By the proof of [[#^proposition-a-11-orbit|item 1]] of [[#^proposition-a-11-orbit|Proposition A.11]], $g$ is the expectation of a $\mathbf{u}$\-measurable function. $g$ is an EU function, and so [[#^lemma-b-11-eu-determined|Lemma B.11]] shows that it is invariant to joint permutation by $\phi_{i}$. Letting $f_{Y}(X\mid\mathcal{D}_{\text{any}})\coloneqq g(X,Y\mid\mathcal{D}_{\text{any}})$, [[#^lemma-b-10-hiding|Lemma B.10]] shows that $f_{Y}(X\mid\mathcal{D}_{\text{any}})=f_{Y}(\phi_{i}\cdot X\mid\phi_{i}\cdot\mathcal{D}_{\text{any}})$ whenever the $\phi_{i}$ satisfy $\phi_{i}\cdot Y=Y$.

Furthermore, if $X^{\prime}\subseteq X$, then $f_{Y}(X^{\prime}\mid\mathcal{D}_{\text{any}})\leq f_{Y}(X\mid\mathcal{D}_{\text{any}})$.

$$
p_{\mathcal{D}_{\text{any}}}\left(A\geq C\right)=p_{\mathcal{D}_{\text{any}}}\left(\text{{ND}}\left(A\right)\geq C\right) \\
\leq p_{\mathcal{D}_{\text{any}}}\left(\text{{ND}}\left(A\right)\geq Z\setminus B_{\text{extra}}\right) \\
\leq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}p_{\mathcal{D}_{\text{any}}}\left(B\geq Z\setminus B_{\text{extra}}\right) \\
\leq p_{\mathcal{D}_{\text{any}}}\left(B\cup B_{\text{extra}}\geq Z\right) \\
=p_{\mathcal{D}_{\text{any}}}\left(B\geq Z\right) \\
=p_{\mathcal{D}_{\text{any}}}\left(B\geq C\right).
$$

Equation 145 follows by Turner et al. \[2021\]’s lemma E.12’s item 2 with $X\coloneqq A$, $X^{\prime}\coloneqq\text{{ND}}\left(A\right)$ (similar reasoning holds for $C$ and $Z$ in eq. 150). Equation 146 follows by the first inequality of lemma E.26 of \[Turner et al., 2021\] with $X\coloneqq A,Y\coloneqq C,Y^{\prime}\coloneqq Z\setminus B_{\text{extra}}$. Equation 147 follows by applying [[#^lemma-b-9-looser|Lemma B.9]] with the $f_{Z\setminus B_{\text{extra}}}$ defined above. Equation 148 follows by the second inequality of lemma E.26 of \[Turner et al., 2021\] with $X\coloneqq A,Y\coloneqq Z,Y^{\prime}\coloneqq Z\setminus B_{\text{extra}}$. Equation 149 follows because $B_{\text{extra}}\subseteq B$.

Letting $f_{0}(\mathcal{D}_{\text{any}})\coloneqq p_{\mathcal{D}_{\text{any}}}\left(A\geq C\right),f_{1}(\mathcal{D}_{\text{any}})\coloneqq p_{\mathcal{D}_{\text{any}}}\left(\text{{ND}}\left(A\right)\geq Z\setminus B_{\text{extra}}\right),f_{2}(\mathcal{D}_{\text{any}})\coloneqq p_{\mathcal{D}_{\text{any}}}\left(B\geq Z\setminus B_{\text{extra}}\right),f_{3}(\mathcal{D}_{\text{any}})\coloneqq p_{\mathcal{D}_{\text{any}}}\left(B\geq C\right)$, apply [[#^lemma-b-1-limited|Lemma B.1]] to conclude that

$$
p_{\mathcal{D}_{\text{any}}}\left(A\geq C\right)\leq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}p_{\mathcal{D}_{\text{any}}}\left(B\geq C\right).
$$

∎

###### Definition D.6 (Rewardless mdp \[Turner et al., 2021\]). ^definition-d-6-rewardless

$\langle\mathcal{S},\mathcal{A},T\rangle$ is a rewardless mdp with finite state and action spaces $\mathcal{S}$ and $\mathcal{A}$, and stochastic transition function $T\mathrel{\mathop{\ordinarycolon}}\mathcal{S}\times\mathcal{A}\to\Delta(\mathcal{S})$. We treat the discount rate $\gamma$ as a variable with domain $[0,1]$.

###### Definition D.7 (1-cycle states \[Turner et al., 2021\]). ^definition-d-7-1-cycle

Let $\mathbf{e}_{s}\in\mathbb{R}^{\left|\mathcal{S}\right|}$ be the standard basis vector for state $s$, such that there is a $1$ in the entry for state $s$ and $0$ elsewhere. State $s$ is a _1-cycle_ if $\exists a\in\mathcal{A}\mathrel{\mathop{\ordinarycolon}}T(s,a)=\mathbf{e}_{s}$. State $s$ is a _terminal state_ if $\forall a\in\mathcal{A}\mathrel{\mathop{\ordinarycolon}}T(s,a)=\mathbf{e}_{s}$.

###### Definition D.8 (State visit distribution \[Sutton and Barto, 1998\]). ^definition-d-8-state

$\Pi\coloneqq\mathcal{A}^{\mathcal{S}}$, the set of stationary deterministic policies. The _visit distribution_ induced by following policy $\pi$ from state $s$ at discount rate $\gamma\in[0,1)$ is $\mathbf{f}^{\pi,s}(\gamma)\coloneqq\sum_{t=0}^{\infty}\gamma^{t}\mathbb{E}_{s_{t}\sim\pi\mid s}\left[\mathbf{e}_{s_{t}}\right]$. $\mathbf{f}^{\pi,s}$ is a _visit distribution function_; $\mathcal{F}(s)\coloneqq\{\mathbf{f}^{\pi,s}\mid\pi\in\Pi\}$.

###### Definition D.9 (Recurrent state distributions \[Puterman, 2014\]). ^definition-d-9-recurrent

The _recurrent state distributions_ which can be induced from state $s$ are $\text{{RSD}}\left(s\right)\coloneqq\left\{\lim_{\gamma\to 1}(1-\gamma)\mathbf{f}^{\pi,s}(\gamma)\mid\pi\in\Pi\right\}$. $\text{{RSD}}_{\text{nd}}\left(s\right)$ is the set of rsds which strictly maximize average reward for some reward function.

###### Definition D.10 (Average-optimal policies \[Turner et al., 2021\]). ^definition-d-10-average-optimal

The _average-optimal policy set_ for reward function $R$ is $\Pi^{\text{avg}}\left(R\right)\coloneqq\left\{\pi\in\Pi\mid\forall s\in\mathcal{S}\mathrel{\mathop{\ordinarycolon}}\mathbf{d}^{\pi,s}\in\argmax_{\mathbf{d}\in\text{{RSD}}\left(s\right)}\mathbf{d}^{\top}\mathbf{r}\right\}$ (the policies which induce optimal rsds at all states). For $D\subseteq\text{{RSD}}\left(s\right)$, the _average optimality probability_ is $\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(D,\text{average}\right)\coloneqq\mathbb{P}_{R\sim\mathcal{D}_{\text{any}}}\left(\exists\mathbf{d}^{\pi,s}\in D\mathrel{\mathop{\ordinarycolon}}\pi\in\Pi^{\text{avg}}\left(R\right)\right)$.

###### Remark. ^remark-6

[[#^theorem-d-11-quantitatively|Theorem D.11]] generalizes the first claim of Turner et al. \[2021\]’s theorem 6.13, and [[#^corollary-d-12-quantitatively|Corollary D.12]] generalizes the first claim of Turner et al. \[2021\]’s corollary 6.14.

###### Theorem D.11 (Quantitatively, average-optimal policies tend to end up in “larger” sets of rsds). ^theorem-d-11-quantitatively

_Let $D^{\prime},D\subseteq\text{{RSD}}\left(s\right)$. Suppose that $D$ contains $n$ copies of $D^{\prime}$ and that the sets $D^{\prime}\cup D$ and $\text{{RSD}}_{\text{nd}}\left(s\right)\setminus\left(D^{\prime}\cup D\right)$ have pairwise orthogonal vector elements (i.e., pairwise disjoint vector support). Then $\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(D^{\prime},\text{average}\right)\leq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(D,\text{average}\right)$._

###### Proof. ^proof-24

Let $D_{i}\coloneqq\phi_{i}\cdot D^{\prime}$, where $D_{i}\subseteq D$ by assumption.  
Let $S\coloneqq\left\{s^{\prime}\in\mathcal{S}\mid\max_{\mathbf{d}\in D^{\prime}\cup D}\mathbf{d}^{\top}\mathbf{e}_{s^{\prime}}>0\right\}$.  
Define

$$
\phi_{i}^{\prime}(s^{\prime})\coloneqq\begin{cases}\phi_{i}(s^{\prime})&\text{ if }s^{\prime}\in S\\
s^{\prime}&\text{ else}.\end{cases}
$$

Since $\phi_{i}$ is an involution, $\phi_{i}^{\prime}$ is also an involution. Furthermore, $\phi_{i}^{\prime}\cdot D^{\prime}=D_{i}$, $\phi_{i}^{\prime}\cdot D_{i}=D^{\prime}$, and $\phi_{i}^{\prime}\cdot D_{j}=D_{j}$ for $j\neq i$ because we assumed that these equalities hold for $\phi_{i}$, and $D^{\prime},D_{i},D_{j}\subseteq D^{\prime}\cup D$ and so the vectors of these sets have support contained in $S$.

Let $D^{*}\coloneqq D^{\prime}\cup_{i=1}^{n}D_{i}\cup\left(\text{{RSD}}_{\text{nd}}\left(s\right)\setminus\left(D^{\prime}\cup D\right)\right)$. By an argument mirroring that in the proof of theorem 6.13 in Turner et al. \[2021\] and using the fact that $\phi_{i}^{\prime}\cdot D_{j}=D_{j}$ for all $i\neq j$, $\phi_{i}^{\prime}\cdot D^{*}=D^{*}$. Consider $Z\coloneqq\left(\text{{RSD}}_{\text{nd}}\left(s\right)\setminus(D^{\prime}\cup D)\right)\cup D^{\prime}\cup D$. First, $Z\subseteq\text{{RSD}}\left(s\right)$ by definition. Second, $\text{{RSD}}_{\text{nd}}\left(s\right)=\text{{RSD}}_{\text{nd}}\left(s\right)\setminus(D^{\prime}\cup D)\cup\left(\text{{RSD}}_{\text{nd}}\left(s\right)\cap D^{\prime}\right)\cup\left(\text{{RSD}}_{\text{nd}}\left(s\right)\cap D\right)\subseteq Z$. Note that $D^{*}=Z\setminus(D\setminus\cup_{i=1}^{n}D_{i})$.

$$
\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(D^{\prime},\text{average}\right)=p_{\mathcal{D}_{\text{any}}}\left(D^{\prime}\geq\text{{RSD}}\left(s\right)\right) \\
\leq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}p_{\mathcal{D}_{\text{any}}}\left(D\geq\text{{RSD}}\left(s\right)\right) \\
=\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(D,\text{average}\right).
$$

Since $\phi_{i}^{\prime}\cdot D^{\prime}\subseteq D$ and $\text{{ND}}\left(D^{\prime}\right)\subseteq D^{\prime}$, $\phi_{i}^{\prime}\cdot\text{{ND}}\left(D^{\prime}\right)\subseteq D$ and so $D$ contains $n$ copies of $\text{{ND}}\left(D^{\prime}\right)$ via involutions $\phi_{i}^{\prime}$. Then eq. 153 holds by applying [[#^lemma-d-5-quantitative|Lemma D.5]] with $A\coloneqq D^{\prime}$, $B_{i}\coloneqq D_{i}$ for all $i=1,\ldots,n$, $B\coloneqq D,C\coloneqq\text{{RSD}}\left(s\right)$, $Z$ as defined above, and involutions $\phi_{i}^{\prime}$ which satisfy $\phi_{i}^{\prime}\cdot\left(Z\setminus(B\setminus\cup_{i=1}^{n}B_{i})\right)=\phi_{i}^{\prime}\cdot D^{*}=D^{*}=Z\setminus(B\setminus\cup_{i=1}^{n}B_{i})$. ∎

###### Corollary D.12 (Quantitatively, average-optimal policies tend not to end up in any given 1-cycle). ^corollary-d-12-quantitatively

_Let $D^{\prime}\coloneqq\left\{\mathbf{e}_{s_{1}^{\prime}},\ldots,\mathbf{e}_{s_{k}^{\prime}}\right\},D_{r}\coloneqq\left\{\mathbf{e}_{s_{1}},\ldots,\mathbf{e}_{s_{n\cdot k}}\right\}\subseteq\text{{RSD}}\left(s\right)$ be disjoint, for $n\geq 1,k\geq 1$. Then $\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(D^{\prime},\text{average}\right)\leq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(\text{{RSD}}\left(s\right)\setminus D^{\prime},\text{average}\right)$._

###### Proof. ^proof-25

For each $i\in\left\{1,\ldots,n\right\}$, let

$$
\phi_{i}\coloneqq(s_{1}^{\prime}\,\,\,s_{(i-1)\cdot k+1})\cdots(s_{k}^{\prime}\,\,\,s_{(i-1)\cdot k+k}), \\
D_{i}\coloneqq\left\{\mathbf{e}_{s_{(i-1)\cdot k+1}},\ldots,\mathbf{e}_{s_{(i-1)\cdot k+k}}\right\}, \\
D\coloneqq\text{{RSD}}\left(s\right)\setminus D^{\prime}.
$$

Each $D_{i}\subseteq D_{r}\subseteq\text{{RSD}}\left(s\right)\setminus D^{\prime}$ by disjointness of $D^{\prime}$ and $D_{r}$.

$D$ contains $n$ copies of $D^{\prime}$ via involutions $\phi_{1},\ldots,\phi_{n}$. $D^{\prime}\cup D=\text{{RSD}}\left(s\right)$ and $\text{{RSD}}_{\text{nd}}\left(s\right)\setminus\text{{RSD}}\left(s\right)=\emptyset$ trivially have pairwise orthogonal vector elements.

Apply [[#^theorem-d-11-quantitatively|Theorem D.11]] to conclude that

$$
\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(D^{\prime},\text{average}\right)\leq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{n}\mathbb{P}_{\mathcal{D}_{\text{any}}}\left(\text{{RSD}}\left(s\right)\setminus D^{\prime},\text{average}\right).
$$

∎

Let $A\coloneqq\left\{\mathbf{e}_{1},\mathbf{e}_{2}\right\},B\subseteq\mathbb{R}^{5}$, $C\coloneqq A\cup B$. [[#^conjecture-d-13-fractional|Conjecture D.13]] conjectures that _e_._g_.,

$$
p_{\mathcal{D}^{\prime}}\left(B\geq C\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{\frac{3}{2}}p_{\mathcal{D}^{\prime}}\left(A\geq C\right).
$$

###### Conjecture D.13 (Fractional quantitative optimality probability superiority lemma). ^conjecture-d-13-fractional

Let $A$, $B$, $C\subsetneq\mathbb{R}^{d}$ be finite. If $A=\bigcup_{j=1}^{m}A_{j}$ and $\bigcup_{i=1}^{n}B_{i}\subseteq B$ such that for each $A_{j}$, $B$ contains $n$ copies ($B_{1},\ldots,B_{n}$) of $A_{j}$ via involutions $\phi_{ji}$ which _also_ fix $\phi_{ji}\cdot A_{j^{\prime}}=A_{j^{\prime}}$ for $j^{\prime}\neq j$, then

$$
p_{\mathcal{D}_{\text{any}}}\left(B\geq C\right)\geq_{\text{{most}}\text{: }\mathfrak{D}_{\text{any}}}^{\frac{n}{m}}p_{\mathcal{D}_{\text{any}}}\left(A\geq C\right).
$$

We suspect that any proof of the conjecture should generalize [[#^lemma-b-7-quantitative|Lemma B.7]] to the fractional set copy containment case.
:::

[^note-1]: We use “reward function” somewhat loosely in implying that reward functions reasonably describe a trained agent’s goals. Turner \[2022\] argues that capable rl algorithms do not necessarily train policy networks which are best understood as optimizing the reward function itself. Rather, they point out that—especially in policy-gradient approaches—reward provides gradients to the network and thereby modifies the network’s generalization properties, but doesn’t ensure the agent generalizes to “robustly optimizing reward” off of the training distribution.
[^note-2]: We often interpret $A$ and $B$ as probability-theoretic events, but no such structure is demanded by our results.
[^note-3]: The function’s retargetability is “simple” because we are not yet worrying about _e_._g_., which parameter inputs are considered plausible: Because $S_{d}$ acts on $\Theta$, [[#^definition-3-3-simply-retargetable|definition 3.3]] implicitly assumes $\Theta$ is closed under permutation.
[^note-4]: In Appendix [[#^c-2-observation-reward|C.2]], [[#^figure-3|Figure 3]] shows a map of the first level.
[^note-5]: $\mathrm{decide}_{\text{rand}}$ does not act randomly at each time step, it induces a randomly selected final observation. Analogously, randomly turning a steering wheel is different from driving to a randomly chosen destination.
[^note-6]: Conversely, if the agent cannot figure out how to leave the first room, any reward signal from outside of the first room can never causally affect the learned policy. In that case, retargetability away from the first room is impossible.
[^note-7]: Our results on outcome lotteries hold for generic $\mathbf{x}^{\prime}\in\mathbb{R}^{d}$, but we find it conceptually helpful to consider the non-negative unit vector case.
[^note-8]: Technically, [[#^definition-a-7-containment|definition A.7]] implies that $A$ contains $n$ copies of $A$ holds for all $n$, via $n$ applications of the identity permutation. For our purposes, this provides greater generality, as all of the relevant results still hold. Enforcing pairwise disjointness of the $B_{i}$ would handle these issues, but would narrow our results to not apply _e_._g_., when the $B_{i}$ share a constant vector.

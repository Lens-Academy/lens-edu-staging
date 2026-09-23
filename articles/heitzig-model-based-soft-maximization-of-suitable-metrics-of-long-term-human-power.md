---
title: "Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"
author:
  - "Jobst Heitzig"
  - "Ram Potham"
source_url: "https://arxiv.org/abs/2508.00159"
published: 2025-07-31
created: 2026-09-23
accessed: 2026-09-23
llm-review:
  date: 2026-09-23
  model: "sonnet"
  version: "article-qc-v1.3"
  source:
    fetched: 2026-09-23
    kind: "live"
description: "A framework for AI safety in which an agent's objective is to softly maximize an inequality- and risk-averse aggregate metric of long-term human power, rather than pursuing a fixed extrinsic reward."
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

###### Abstract ^abstract

Power is a key concept in AI safety: power-seeking as an instrumental goal, sudden or gradual disempowerment of humans, power balance in human-AI interaction and international AI governance. At the same time, power as the ability to pursue diverse goals is essential for wellbeing.

This paper explores the idea of promoting both safety and wellbeing by forcing AI agents explicitly to empower humans and to manage the power balance between humans and AI agents in a desirable way. Using a principled, partially axiomatic approach, we design a parametrizable and decomposable objective function that represents an inequality- and risk-averse long-term aggregate of human power. It takes into account humans’ bounded rationality and social norms, and, crucially, considers a wide variety of possible human goals.

We derive algorithms for computing that metric by backward induction or approximating it via a form of multi-agent reinforcement learning from a given world model. We exemplify the consequences of (softly) maximizing this metric in a variety of paradigmatic situations and describe what instrumental sub-goals it will likely imply. Our cautious assessment is that softly maximizing suitable aggregate metrics of human power might constitute a beneficial objective for agentic AI systems that is safer than direct utility-based objectives.

1Potsdam Institute for Climate Impact Research, Potsdam, Germany, heitzig@pik-potsdam.de

2Independent, ram.potham@gmail.com

## 1 Introduction ^1-introduction

A duty to empower others, especially those with little power, can be defended on consequentialist ([Sen 2014](#bib.bib29)), deontological ([Hill Jr 2002](#bib.bib12)), and virtue ethical ([Nussbaum 2019](#bib.bib19)) grounds. At the same time, gradual or sudden disempowerment of humans due to misaligned A(G)I, e.g. due to power-seeking ([Turner et al. 2019](#bib.bib32)) or non-corrigible over-optimization of misaligned reward functions ([Gao, Schulman, and Hilton 2023](#bib.bib9)), is a key AI safety risk.

Accordingly, some papers explored tasking AI agents explicitly with the empowerment of individual humans, mainly inspired by the information-theoretic channel capacity $\cal E$ between human actions and environmental states, called ‘empowerment’ in [Klyubin, Polani, and Nehaniv (2005)](#bib.bib13). But that metric is hard to compute, so [Du et al. (2020)](#bib.bib7) use a proxy based on the variance of terminal states reached under a random policy, while [Myers et al. (2024)](#bib.bib18) use contrastive learning of latent state representations to approximate $\cal E$. [Salge and Polani (2017)](#bib.bib28) discuss the ‘empowerment’-based approach in more depth for the single-human case.

This paper extends the theoretical foundations of this approach in two ways. First, we develop an alternative metric of human power, ‘ICCEA power’, that is directly based on the key aspect of power: the ability to attain a wide range of possible goals. Our metric explicitly and transparently incorporates humans’ knowledge about the actions of the AI agent, their expectations about others’ behavior, e.g. due to social norms, and their bounded rationality. Second, using an approach guided by desiderata similar to the axioms of social choice and welfare theory, we develop an objective function for an AI agent interacting with populations of humans, based on an aggregate of ICCEA power across humans and time that gives the agent desirable incentives such as communicating well ([Reddy, Levine, and Dragan 2022](#bib.bib25)), following orders, being corrigible ([Potham and Harms 2025](#bib.bib22)), avoiding irreversible changes in the environment, protecting humans and itself from harm and disempowerment, allocating resources fairly and sustainably, and acting “appropriately” by following relevant social norms ([Leibo et al. 2024](#bib.bib15)).

Though based on possible human goals, our approach avoids trying to learn individuals’ actual, current goals, because human preferences are changing and non-identifiable ([Cao, Cohen, and Szpruch 2021](#bib.bib6); [Banerjee and Duflo 2011](#bib.bib3)) and their prediction is unavoidably uncertain ([Baker, Saxe, and Tenenbaum 2011](#bib.bib2)). Some critics of a preference-based approach argue for a values\-based approach instead ([Lowe et al. 2025](#bib.bib17)), which however requires an even more semantic world understanding by the AI agent. A deep semantic understanding is also required in the ‘freedoms’-based conception of AI ethics in ([London and Heidari 2024](#bib.bib16)), and compiling its required list of ‘fundamental capabilities’ is difficult ([Robeyns 2006](#bib.bib26)). By contrast, like the ‘empowerment’-based approach, our metrics are mostly based on a structural understanding of possibly dynamics, interactions, and transition probabilities and aim to avoid semantic issues by relating human power to the ability to bring about just any possible conditions a human might happen to desire.

For theoretical convenience, we work in a model-based setting where the AI agent can plan on the basis of a decent stochastic world model like the “scientist AI” envisioned in [Bengio et al. (2025)](#bib.bib5). After developing our human power metric in Section [[#^2-measuring-aggregating-and|2]], we shortly describe algorithms for softly maximizing it in Section [[#^3-model-based-planning-or|3]], before reporting insights about the resulting behavior in Section [[#^4-experiments|4]]. Section 5 concludes.

## 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ^2-measuring-aggregating-and

Figure 1: Overview of proposed approach for deriving power-managing policies for a general-purpose AGI system

##### Framework ^framework

We assume a robot $r$ interacting with several humans $h\in\mathcal{H}$. The robot models the world as a (fully or partially observed) stochastic game with states $s\in\mathcal{S}$. It gets no extrinsic reward itself. Humans have many possible and potentially changing goals $g_{h}\in\mathcal{G}_{h}$ and get goal-dependent rewards $U_{h}(s^{\prime},g_{h})$, discounted at factors $\gamma_{h}<1$. Action sets $\mathcal{A}_{r}(s),\mathcal{A}_{h}(s)$ may be state-dependent. Action and policy profiles are written $a=(a_{r},a_{\mathcal{H}})=(a_{r},a_{h},a_{-h})$, $\pi=(\pi_{r},\pi_{\mathcal{H}})$. The transition kernel is $P(s^{\prime}|s,a)$.

Crucially, we assume the robot neither knows nor forms beliefs about the actual goals of the humans. It does make assumptions about their level of rationality and their beliefs about each others’ behavior, reflected in additional model parameters $\nu_{h}$, $\pi^{0}_{h}$, $\beta_{h}$, and $\mu_{-h}$, as detailed below.

##### Task ^task

We want to design an algorithm for computing a policy $\pi_{r}$ for the robot that implements the aggregate human power maximization objective. For tractability, we formalize this objective as an expected discounted return, $V_{r}=\mathbb{E}_{s_{\geq 0}}\sum_{t\geq 0}\gamma_{r}^{t}U_{r}(s_{t})$, based on an intrinsic reward $U_{r}(s)$ which represents a suitable assessment of the aggregate human power in $s$. To design $U_{r}(s)$, we first design a power metric $W_{h}(s)$ for individual humans, and then an aggregation function $U_{r}(s)=F_{U}((W_{h}(s))_{h\in\mathcal{H}})$.

In designing $W_{h}$ and $F_{U}$, we have several objectives relating to their tractability, interpretability, and the behavioral incentives that they give the robot.

$$
Q^{m}_{h}(s,g_{h},a_{h}) \\
\leftarrow\textstyle\mathbb{E}_{a_{-h}\sim\mu_{-h}(s,g_{h})}\min_{a_{r}\in\mathcal{A}_{r}(s)}\mathbb{E}_{s^{\prime}\sim s,a} \\
\qquad\quad\big(U_{h}(s^{\prime},g_{h})+\gamma_{h}V^{m}_{h}(s^{\prime},g_{h})\big), \\
\pi_{h}(s,g_{h}) \\
\leftarrow\nu_{h}(s,g_{h})\pi^{0}_{h}(s,g_{h})+(1-\nu_{h}(s,g_{h}))\times{} \\
~~{}\times\text{$\beta_{h}(s,g_{h})$-softmax for~}Q^{m}_{h}(s,g_{h},\cdot), \\
V^{m}_{h}(s,g_{h}) \\
\leftarrow\textstyle\mathbb{E}_{a_{h}\sim\pi_{h}(s,g_{h})}Q^{m}_{h}(s,g_{h},a_{h}), \\
Q_{r}(s,a_{r}) \\
\leftarrow\textstyle\mathbb{E}_{g}\mathbb{E}_{a_{\mathcal{H}}\sim\pi_{\mathcal{H}}(s,g)}\mathbb{E}_{s^{\prime}\sim s,a}\gamma_{r}V_{r}(s^{\prime}), \\
\pi_{r}(s)(a) \\
\propto(-Q_{r}(s,a_{r}))^{-\beta_{r}}, \\
V^{e}_{h}(s,g_{h}) \\
\leftarrow\textstyle\mathbb{E}_{g_{-h}}\mathbb{E}_{a_{\mathcal{H}}\sim\pi_{\mathcal{H}}(s,g)}\mathbb{E}_{a_{r}\sim\pi_{r}(s)}\mathbb{E}_{s^{\prime}\sim s,a} \\
\qquad\qquad\textstyle\big(U_{h}(s^{\prime},g_{h})+\gamma_{h}V^{e}_{h}(s^{\prime},g_{h})\big), \\
X_{h}(s) \\
\leftarrow\textstyle\sum_{g_{h}\in\mathcal{G}_{h}}V^{e}_{h}(s,g_{h})^{\zeta}, \\
U_{r}(s) \\
\leftarrow\textstyle-\big(\sum_{h}X_{h}(s)^{-\xi}\big)^{\eta}, \\
V_{r}(s) \\
\leftarrow\textstyle U_{r}(s)+\mathbb{E}_{a_{r}\sim\pi_{r}(s)}Q_{r}(s,a_{r}).
$$

Table 1: Computation of ICCEA power $W_{h}=\log_{2}X_{h}$ and intrinsic robot reward $U_{r}$ as derived in the text.

| Desideratum | Corresponding design choice or world model requirement |
| --- | --- |
| $V_{h}$ recursively computable | Define via Bellman equation: $V_{h}(s,g_{h})=\mathbb{E}_{s^{\prime}}(U_{h}(s^{\prime},g_{h})+\gamma_{h}V_{h}(s^{\prime},g_{h}))$ |
| $V_{h}$ comparable across humans | Assume goals $g_{h}$ are events: $g_{h}\subseteq\mathcal{S}$, $U_{h}(s^{\prime},g_{h})=1_{s^{\prime}\in g_{h}}$ |
| $V_{h}$ has natural interpretation | Make $V_{h}$ a goal-reaching probability: $s\in g_{h}$, $s^{\prime}$ reachable from $s\Rightarrow s^{\prime}\notin g_{h}$ |
| $r$ incentivized to make commitments | Base $\pi_{h}$ on $h$ assuming $r$ takes worst action not ruled out by $r$’s commitments |
| $r$ considers $h$’s bounded rationality | Base $\pi_{h}$ on varying, unstable goals, habits, social norms, mutual expectations |
| $W_{h}$ based on $r$’s best estimate of $V_{h}$ | Distinguish $h$’s simulated estimate $V^{m}_{h}$ for $\pi_{h}$ and $r$’s estimate $V^{e}_{h}$ for $W_{h}$ |
| $W_{h}$ indep. of “unaffected” goals | Use separable ansatz: $W_{h}=F^{G}(\sum_{g_{h}}f^{G}(V^{e}_{h}))$ ($\Rightarrow$ enables stoch. approx.) |
| $W_{h}$ additive across indep. subgames | $F^{G}=\log_{2}$ ($\Rightarrow W_{h}=$ “certainty-equivalent” effective no. of binary choices) |
| $W_{h}>-\infty$ | Make set $\mathcal{G}_{h}$ of possible goals wide enough to cover all possible trajectories |
| Range of $W_{h}$ is symmetric around 0 | Make each trajectory fulfill exactly one $g_{h}\in\mathcal{G}_{h}$ and put $\zeta=2$ (see below) |
| $U_{r}$ indep. of “unconcerned” agents | Use separable ansatz: $U_{r}=F^{H}(\sum_{h}f^{H}(W_{h}))$ ($\Rightarrow$ enables stoch. approx.) |
| Pigou–Dalton-type inequality aversion | Make $f^{H}$ strictly concave, e.g., $f^{H}(w)=-2^{-\xi w}$ with $\xi>0$ |
| Protect a human’s “last” bit of power | Choose $\xi\geq 1$, e.g., $\xi=1$ |
| $r$ cares for current and later human power | Base $\pi_{r}$ on $V_{r}(s_{0})=\mathbb{E}_{s_{\geq 0}}\sum_{t=0}^{\infty}\gamma_{r}^{t}U_{r}(s_{t})$, not just $U_{r}(s_{0})$ |
| Limit intertemporal power trading | Also make $F^{H}$ strictly concave (intertemporal inequality aversion) |
| $\pi_{r}$ indep. of common rescaling of $V^{e}_{h}$ | Use power laws: $f^{G}(v)=v^{\zeta}$, $\zeta>0$; $f^{H}(w)=-2^{-\xi w}$, $\xi\geq 1$; |
|  | $F^{H}(y)=-(-y)^{\eta}$, $\eta>1$; and $\pi(s)(a)\propto(-Q_{r}(s,a_{r}))^{-\beta_{r}}$, $0\leq\beta_{r}\leq\infty$ |
| $r$ incentivized to reduce uncertainty | Choose $\zeta>1$ (risk aversion, preference for reliability) |
| Avoid risks from over-optimization | Choose $\beta_{r}<\infty$ (soft optimization, exploration) |

Table 2: Desiderata and corresponding metric design choices for metrics of humans’ goal-attainment ability $V_{h}(s,g_{h})$, momentary individual power $W_{h}(s)$, momentary aggregate power $U_{r}(s)$, long-term total human power $V_{r}(s)$ for soft maximization by an AGI system (“robot”) $r$, $r$’s prior on human behavior $\pi_{h}$ used to estimate $V_{r}$, and its own resulting policy $\pi_{r}$.

Our final equations for the fully observed case are collected in Table [1](#S2.T1 "Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power") (see the Supplement for the partially observed case). We will motivate them now in detail.

### 2.1 Individual-Level Metric: ICCEA Power ^2-1-individual-level-metric

Our power metric basically counts the effective number of goals a human can achieve. It is built in three steps: defining what it means to achieve a goal, adjusting for human bounded rationality, and aggregating the achievement ability across all possible goals into one number. Rather than trying to capture the full range of subtle aspects of existing notions of human power, we focus on those aspects we believe a robot can robustly infer from the structure of its world model, encoded in state and action sets, transition kernel, and observation functions. Since we want to incentivize the robot to remove constraints and uncertainties, share information, make commitments, and improve human cognition, coordination, and cooperation, our power metric will also depend on $r$’s model of human decision making.

We start with the intuition that humans have ‘goals’ and that ‘power’ is about the means to achieve a wide range of goals. We aim to measure informationally and cognitively constrained effective autonomous (ICCEA) power: essentially how many goals a human can freely choose to reach with more or less certainty, given their information, cognitive capabilities, and others’ behavior.

##### Goals ^goals

We use an easily interpretable compromise between the reachability ([Krakovna et al. 2018](#bib.bib14)) and attainable utility ([Turner, Hadfield-Menell, and Tadepalli 2020](#bib.bib31)) approaches. We deviate significantly from the information-theoretic approach ([Klyubin, Polani, and Nehaniv 2005](#bib.bib13)) which does not explicitly involve any goals. We assume that each possible temporary goal that $h\in\mathcal{H}$ might have is to reach some set of states $g_{h}\subseteq\mathcal{S}$ representing a possibly desirable event. The corresponding reward function is the indicator function $U_{h}(s,g_{h})=1_{s\in g_{h}}$. So the set of goals $\mathcal{G}_{h}$ is simply a set of subsets of $\mathcal{S}$. We require that the desirable states in a goal $g_{h}$ are mutually unreachable (e.g., are all terminal states or states for a particular time-point $t$). Then the resulting value $V_{h}^{\pi}(s)$ is simply the probability of the desirable event under policy profile $\pi$. This grounds $h$’s goal attainment or ‘attainable utility’ in probability and increases interpretability. As it is then bounded within $[0,1]$, this also avoids aggregation problems such as dominance by “utility monsters”. To avoid issues with probability zero, $\mathcal{G}_{h}$ must be wide enough so that each possible state trajectory fulfills at least one possible goal.[^note-1] E.g., $\mathcal{G}_{h}$ could be a partition of the terminal states.

We believe that restricting the model to this very basic type of goal will simplify the derivation of $\mathcal{G}_{h}$ from learned latent representations of generic world states and generic human goals as encoded in language or foundation models, and will obviate the need for individual-level data about a particular human’s possible goals. This should mitigate risks arising from misaligned models of human goals.[^note-2]

##### Bounded rationality ^bounded-rationality

We equip $r$ with a simple model of $h$’s decision making that focuses on giving $r$ the right incentives. It assumes $h$ cannot realize the maximal goal attainment probability due to a variety of reasons relating to exploration, imperfect action implementation, information constraints, others’ behavior, and potentially state-dependent cognitive limitations. In particular, $r$ does not assume $h$ to have correct beliefs about others’ behavior that would lead to an equilibrium (Nash, quantal response, etc.). Instead, $r$ models $h$ as having fixed beliefs $\mu_{-h}$ about other humans’ behavior (where ‘$-h$’ is short for $\mathcal{H}\setminus\{h\}$). These would also reflect social norms (which LLM-based systems already understand, [Smith et al. (2024)](#bib.bib30)). Hence the state-goal-action values $Q^{m}_{h}(s,g_{h},a_{h})$ that $r$ assumes guide $h$’s behavior are based on $\mu_{-h}$. This is reflected in eq. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) in Table [1](#S2.T1 "Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power").

Regarding human actions, $r$ assumes that $h$ uses a mixture (governed by a probability $\nu_{h}$) between (i) habitual, ‘system-1’ behavior encoded in some default policy $\pi^{0}_{h}(s,g_{h})$, again reflecting social norms, and (ii) boundedly rational, ‘system-2’ behavior represented by a Boltzmann policy with rationality parameter $\beta_{h}$, see eq. ([2](#S2.E2 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). As in [Ghosal et al. (2023)](#bib.bib10), $\beta_{h}$ may be state-dependent, which will give $r$ incentives to choose states with larger $\beta_{h}$, and it might be estimated from observations ([Safari et al. 2024](#bib.bib27)). Reflecting social norms, $\nu_{h}$, $\mu_{-h}$, and $\pi^{0}_{h}$ are the only significantly “semantically loaded” elements of the world model.

To model human beliefs about the robot’s actions, the world model contains information about what actions $r$ has previously committed to choose from in a state $s$: the action set $\mathcal{A}_{r}(s)$ only contains those actions, and different commitment histories are considered different states. Then $r$ models $h$ as being cautious regarding $r$’s commitment-compliant actions. It thus uses the $\min_{a_{r}\in\mathcal{A}_{r}(s)}$ operator to compute $Q^{m}_{h}(s,g_{h},a_{h})$ in eq. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). This is not for realism but because it incentivizes $r$ to make goal-independent commitments about its interaction behavior, e.g. by properly labelling its buttons or promising to react to certain verbal commands in certain ways. The incentive for $r$ to choose such a “commitment action” in some state $s$ arises since that will make $\mathcal{A}_{r}(s^{\prime})$ of later states $s^{\prime}$ smaller and will thus weakly increase $Q^{m}_{h}(s^{\prime},g_{h},a_{h})$, without $r$ ever having to guess $g_{h}$.

These assumptions also allow $r$ to first calculate a behavior prior $\pi_{h}$ for each $h$ independently, before deciding its own policy $\pi_{r}$. This avoids issues around non-uniqueness of strategic equilibria and non-stationarity in learning.

##### Effective goal attainment ability ^effective-goal-attainment-ability

While $r$ assumes $h$’s behavior $\pi_{h}$ is based on $h$’s cautious value assessment $V^{m}_{h}$, eq. ([3](#S2.E3 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), its assessment of $h$’s effective goal-reaching ability $V^{e}_{h}$, used in computing $h$’s power, will generally differ from $V^{m}_{h}$. This is because $r$’s beliefs about other humans’ policies, $\pi_{-h}$, may differ from $h$’s beliefs, $\mu_{-h}$. And $r$’s policy $\pi_{r}$ will generally differ from the worst case given by $\min_{a_{r}}$. Hence eq. ([6](#S2.E6 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) calculates $V^{e}_{h}$ as the probability of $g_{h}$ being fulfilled under the actual policy $\pi_{r}$ and the derived prior $\pi_{\mathcal{H}}$, averaged over others’ potential goals $g_{-h}$ and corresponding behaviors $\pi_{-h}$. This is then the basis of the power metric.

##### Aggregation across goals ^aggregation-across-goals

How should $r$ aggregate $h$’s effective goal attainment abilities $V^{e}_{h}(s,g_{h})$ across all possible goals $g_{h}\in\mathcal{G}_{h}$ to get an assessment of $h$’s ICCEA power in $s$, $W_{h}(s)$? Similar to [Fleming (1952)](#bib.bib8), we want the aggregation to be independent of goal labels, continuous, strictly increasing in each $V^{e}_{h}(s,g_{h})$, and to fulfil “independence of unaffected goals”. This implies that the aggregation must be “separable”, $W_{h}(s)=F^{G}(X_{h}(s))$ with $X_{h}(s)=\sum_{g_{h}}f^{G}(V^{e}_{h}(s,g_{h}))$ for some continuous and strictly increasing transformations $F^{G},f^{G}$. Since $X_{h}(s)=\mathbb{E}_{g_{h}}|G_{h}|f^{G}(V^{e}_{h}(s,g_{h}))$, we can then also hope to learn it via stochastic approximation.

For reasons that will become clear when discussing $r$’s reward function $U_{r}$ below, we choose the inner transformation $f^{G}$ to be of the form $f^{G}(v)=v^{\zeta}$ for some $\zeta>0$. This is analogous to certain “non-expected” utility theories, in particular to rank-dependent utility theory with the probability-weighting function $w(p)=p^{\zeta}$ ([Quiggin 1982](#bib.bib23)). We choose $\zeta>1$ to incentivize $r$ to reduce uncertainty. It would then consider $h$ to be more powerful when $h$ can choose between two deterministic outcomes (so that $X_{h}(s)=2\times 1^{\zeta}=2$) than when $h$ can choose between two coin tosses (so that $X_{h}(s)=4\times(1/2)^{\zeta}<2$). This can be interpreted as risk aversion or a preference for reliability.

Our choice of the outer transformation $F^{G}$ is somewhat arbitrary. This is because the subsequent aggregation across humans will involve an additional transformation anyway. We choose $F^{G}=\log_{2}$ so that power is measured in bits. In the limit of full rationality, it then also behaves in an additive way if the game is decomposable into several independent simultaneous games. This choice leads to a convenient relationship between our final ICCEA power metric,

$$
W_{h}(s)=\textstyle\log_{2}X_{h}(s)=\log_{2}\sum_{g_{h}}V^{e}_{h}(s,g_{h})^{\zeta},
$$

and the information-theoretic notion of ‘empowerment’, as described below. In the case where $h$ can choose between fulfilling $k$ different goals for sure, we simply have $W_{h}(s)=\log_{2}k$. Because each trajectory fulfils at least one goal $g_{h}$, we always have $X_{h}(s)>0$ and thus $W_{h}(s)>-\infty$. But $W_{h}(s)$ may be negative in situations with very little control.[^note-3]

#### Relationship to ‘empowerment’ ^relationship-to-empowerment

[Klyubin, Polani, and Nehaniv (2005)](#bib.bib13) define ‘empowerment’ as the channel capacity between actions and states. In a single-player multi-armed bandit environment with possible outcomes $s^{\prime}$, this equals the maximal mutual information $E_{h}=\textstyle\max_{\pi_{h}}\mathbb{I}_{\pi_{h}}(a_{h};s^{\prime})$. In the Supplement, we show that $E_{h}\leq W_{h}$ if we put $\mathcal{G}_{h}=\mathcal{S}$, $\zeta=1$, and assume full rationality ($\nu_{h}=0$, $\beta_{h}=\infty$), similar to what [Myers et al. (2024)](#bib.bib18) have shown. Similarly, for $\zeta>1$, our metric $W_{h}$ is an upper bound of an entropy-regularized version of ‘empowerment’,

$$
E^{\zeta}_{h} \\
=\textstyle\max_{\pi_{h}}\big(\mathbb{I}_{\pi_{h}}(a_{h};s^{\prime})-(\zeta-1)\mathbb{H}_{\pi_{h}}(s^{\prime}|a_{h})\big),
$$

sharing the same value range and coinciding in edge cases.

But while the policy $\pi_{h}$ that $r$ estimates in our approach is a function of state and goal $g_{h}$, has typically low entropy as it aims to reach $g_{h}$, and can be found by standard dynamic programming or RL approaches, the maximizing “policy” $\pi_{h}$ in eq. ([11](#S2.E11 "In Relationship to ‘empowerment’ ‣ 2.1 Individual-Level Metric: ICCEA Power ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) has no real use, has typically high entropy in order to maximize $\mathbb{I}(a_{h};s^{\prime})$, and is harder to find since the optimization problem is non-convex.

### 2.2 Bounded Trade-Off Aggregation ^2-2-bounded-trade-off

How should the robot aggregate all humans’ ICCEA power $W_{h}(s)$ to determine its own intrinsic reward $U_{r}(s)$? This depends on what incentives we want to give $r$ regarding changes in (i) the inter-human power distribution, (ii) the inter-temporal power distribution, and (iii) the power distribution across different realizations of uncertainty. Similar questions abound in welfare theory, guiding the way.

We again want anonymity, continuity, strict monotonicity in each $W_{h}(s)$, and an independence axiom (“Independence of unconcerned agents”). Again, this implies a separable form, $U_{r}(s)=F^{H}(\sum_{h}f^{H}(W_{h}(s)))$ with continuous, strictly increasing functions $f^{H}$ and $F^{H}$ ([Fleming 1952](#bib.bib8)).

##### Inter-human trade-offs ^inter-human-trade-offs

We do not want $r$ to concentrate power in the hands of a few, so we require the Pigou–Dalton principle of inequality aversion ([Pigou 1912](#bib.bib21)). This implies $f^{H}$ must be strictly concave. The functions most commonly used in such a context are those of “constant relative” and “constant absolute inequality aversion” ([Amiel, Creedy, and Hurn 1999](#bib.bib1)). As $W_{h}(s)=\log_{2}X_{h}(s)$, a natural choice is to use constant absolute inequality aversion w.r.t. $W_{h}(s)$ since that is equivalent to constant relative inequality aversion w.r.t. $X_{h}(s)$. This implies that $f^{H}(W_{h}(s))=-2^{-\xi W_{h}(s)}=-X_{h}(s)^{-\xi}$ for some $\xi>0$.

As it turns out, if we put $\xi=1$, we disincentivize $r$ from “taking away a person’s last binary choice” in the sense that reducing one human’s $W_{h}(s)$ from one bit to zero bits cannot be made up by increasing any other human’s $W_{h^{\prime}}(s)$ from $\geq 1$ bit to any value, because $-2^{-1}-2^{-W_{h^{\prime}}(s)}\geq-1>-2^{-0}-2^{-w}$ for any $w\geq 1$. This is related closely to the idea of minimal individual rights ([Pattanaik and Suzumura 1996](#bib.bib20)). We thus choose $\xi=1$.[^note-4]

##### Intertemporal trade-offs ^intertemporal-trade-offs

We find it natural to also disincentivize $r$ from trading off current vs. later human power too much. It should generally prefer a trajectory $(s_{1},s_{2},\dots)$ with a rather homogenous power distribution along time, such as $W_{h}(s_{1})=W_{h^{\prime}}(s_{2})=1$ and $W_{h}(s_{2})=W_{h^{\prime}}(s_{1})=2$, to a trajectory where, say, $W_{h}(s_{1})=W_{h^{\prime}}(s_{1})=1$ and $W_{h}(s_{2})=W_{h^{\prime}}(s_{2})=2$. This means that $F^{H}$ should be strictly concave. Note that since $f^{H}(w)<0$, $F^{H}$ needs to be defined for negative values only.

We motivate our concrete choice of $F^{H}$ and $\pi_{r}$ (and of $f^{G}$) by the following independence requirement. Assume we introduce an additional uncertainty into the world model (e.g., a formerly not modelled change of overall circumstances) whose consequence is that all goal attainment probabilities $V^{e}_{h}(s,g_{h})$ are multiplied by some common factor $b\in(0,1)$. Then this should not change the policy $\pi_{r}$. The simplest way to fulfil this is to put $f^{G}(v)=v^{\zeta}$ (as done already above), $F^{H}(y)=-(-y)^{\eta}$ with $\eta>1$, and to use either an argmax policy for $\pi_{r}$ or a power-law-like policy with $\pi_{r}(s)(a)\propto(-Q_{r}(s,a_{r}))^{-\beta_{r}}$ for some $\beta_{r}>0$. Note that the minus signs are needed since $Q_{r}(s,a_{r})<0$.

We choose $\beta_{r}<\infty$ to allow the robot some exploration, e.g., to improve its world model. This should also help avoiding remaining safety risks when our metric misses some subtle but important aspects of ‘power’ that might thus be driven to very undesirable states under a full maximization of $V_{r}$, similar to ([Zhuang and Hadfield-Menell 2020](#bib.bib33)).

##### Aggregation across uncertainty ^aggregation-across-uncertainty

To deal with uncertain successor states $s^{\prime}$, standard axioms suggest we should simply take expectations in eqns. ([4](#S2.E4 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) and ([9](#S2.E9 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). When dealing with uncertain goals $g_{h}$, we want $r$ to be rather corrigible. So we assume goals might change anytime and take an expectation over independent uniform draws $g_{h}$.

Table [2](#S2.T2 "Table 2 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power") summarizes all the above design choices.

##### Existence and (non-)uniqueness ^existence-and-non-uniqueness

In an acyclic environment, one can use backward induction to solve for the unique solution of ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([9](#S2.E9 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) (see below). Otherwise, eqns. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([3](#S2.E3 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) define a continuous self-map $F$ on a finite-dimensional closed convex polytope of values $(Q^{m}_{h},\pi_{h},V^{m}_{h})$ and must thus have a solution due to Brouwer’s fixed point theorem. Due to the softmax, $F$ is neither a contraction nor is the resulting value iteration map monotonic unless $\beta_{h}<\beta_{h}^{1}$ for some $\beta_{h}^{1}>0$, so the solution can be non-unique in cyclic environments. Eqns. ([4](#S2.E4 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([9](#S2.E9 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) also define a continuous self-map $G$ from a finite-dimensional bounded convex set $D$ of values $(Q_{r},\pi_{r},V^{e}_{h},X_{h},U_{r},V_{r})$ which is however not closed because $G$ is undefined for zero values in $Q_{r}$ or $X_{h}$.[^note-5] Still, for $\beta_{r}=0$, there is a unique solution because $V^{e}_{h}$ is then the value function of a fixed policy, $U_{r}$ is independent of $V_{r}$, and so $V_{r}$ is also the value function of a fixed policy and reward function. Since $F,G$ are continuous in $\beta_{h},\beta_{r}$, we thus conjecture that homotopy / continuation methods can single out a unique “principal” solution for any $\beta_{h},\beta_{r}>0$ even in cyclic environments, as in [Goeree, Holt, and Palfrey (2016)](#bib.bib11).

## 3 Model-Based Planning or Learning to Softly Maximize Aggregate Human Power ^3-model-based-planning-or

In small acyclic stochastic games, one can compute all relevant quantities directly via backward induction on $s\in\mathcal{S}$: for each $h\in\mathcal{H}$, $g\in\mathcal{G}$, $a_{h}\in\mathcal{A}_{h}$, and $a_{r}\in\mathcal{A}_{r}$, compute ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([9](#S2.E9 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) in that order.

### 3.1 Complex Multi-Agent Environments: Model-Based Temporal Difference Learning ^3-1-complex-multi-agent

If $\mathcal{S}$ and $\mathcal{A}$ are large but $\mathcal{H}$ and $\mathcal{G}_{h}$ are not, the robot can use a tabular or approximate learning approach.[^note-6]

#### Phase 1: Learning the human behavior prior ^phase-1-learning-the

For each $h\in\mathcal{H},g_{h}\in\mathcal{G}_{h}$ separately, learn tables or neural network approximations of $Q^{m}_{h}$ and $\pi_{h}$. Generate samples $(s,g_{h},a,s^{\prime})$ using a slowly updated $\beta_{h}$\-softmax policy $\pi_{h}(s,g_{h})$ based on $Q_{h}^{m}$ with a decreasing amount of additional exploration, the prior policy $a_{-h}\sim\mu_{-h}(s)$ for other humans, and, to eventually learn the minimum in ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), an $\epsilon$\-greedy policy for $a_{r}$ based on the negative expected value $-\mathbb{E}_{s^{\prime}\sim s,a}(U_{h}(s^{\prime},g_{h})+\gamma_{h}V^{m}_{h}(s^{\prime},g_{h}))$ with $\epsilon\to 0$. Then use expected SARSA targets on a time-scale faster than $\pi_{h}$.

#### Phase 2: Learning the robot reward and policy ^phase-2-learning-the

Based on the learned $\pi_{h}$, now aim to simultaneously learn tables or network approximations of $V^{e}_{h}$ and $X_{h}$ for all $h$, and of either $Q_{r}$ (DQN approach) or $V_{r}$ (actor-critic (AC) approach). Generate data samples $(s,g,a,s^{\prime})$ from rollouts using the fixed policies $\pi_{h}(s,g_{h})$, and either a $\beta_{r}^{\prime}$\-softmax policy based on $Q_{r}$ with $\beta_{r}^{\prime}\nearrow\beta_{r}$, or a network approximation of $\pi_{r}$ trained on $V_{r}$ with entropy regularisation. Sample a new goal profile $g$ every $N_{g}$ steps. Instead of the direct expectation calculations of ([4](#S2.E4 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), ([6](#S2.E6 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), ([7](#S2.E7 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), then update the tables or networks via batched SGD using the update targets

$$
q_{r}(s,a_{r})\text{~or~}v_{r}(s) \\
\leftarrow\gamma_{r}V_{r}(s^{\prime}), \\
v^{e}_{h}(s,g_{h}) \\
\leftarrow U_{h}(s^{\prime},g_{h})+\gamma_{h}V^{e}_{h}(s^{\prime},g_{h}), \\
x_{h}(s) \\
\leftarrow|\mathcal{G}_{h}|\,V^{e}_{h}(s,g_{h})^{\zeta}.
$$

In the AC case, use an advantage-weighted log-probability loss for $\pi_{r}$ based on the advantage estimate $v_{r}(s)-V_{r}(s)$.

#### Anticipated convergence ^anticipated-convergence

We expect phase 1 to converge reliably for a sufficiently expressive neural network because its tabular version is known to converge for a suitable, two time-scale learning rate schedule.

We are less certain about phase 2. For one thing, the uniqueness of the solution in the finite acyclic case suggests there might be a unique solution in the general case. On the other hand, the update operator is not a contraction here because of the interaction between $h$ and $r$ (similar to other MARL problems), which suggests convergence might still fail. To limit the error propagation from $Q_{r}$ via $\pi_{r}$ to $V^{e}_{h}$, we use a $\beta_{r}$\-softmax policy $\pi_{r}$ (which has Lipschitz constant $\beta_{r}$) instead of an $\epsilon$\-greedy policy (not Lipschitz-continuous).

## 4 Experiments ^4-experiments

### 4.1 Analysis of paradigmatic situations ^4-1-analysis-of

We analyze the behavioral implications of our approach in several paradigmatic situations (details in the Supplement).

##### Making (conditional) commitments ^making-conditional-commitments

If the robot can make binding commitments (e.g. by offering labelled buttons causing different behaviors), make secret plans to react to $h$’s actions in certain ways (e.g. by offering unlabelled buttons), or act without waiting for button presses, it will generally make commitments if it assumes $h$ to be sufficiently rational to use that information to act in ways that make $r$ do what $h$ actually wants. This is because $\pi_{h}$ does not depend on $\pi_{r}$ (encoding what $r$ plans) but on $\mathcal{A}_{r}$ (encoding what $r$ has committed to). Via such commitments, $r$ will establishing semantic connections between human actions (e.g., speech acts) and certain potentially complex behaviors of its own, to be able to act as an instruction-following assistant, somewhat similar to [Reddy, Levine, and Dragan (2022)](#bib.bib25).

##### Optimal menu size ^optimal-menu-size

While an ‘empowerment’ maximizing robot would present humans with as many action options as possible, our robot will avoid overwhelming humans with too many options. If $r$ can choose to give $h$ any number $k$ of actions, each of which fulfils a different goal, it will choose $k\approx(e^{\beta_{h}}-1)/(\zeta-1)$ (noting that $\zeta>1$). This is because for larger $k$, $h$’s goal attainment probability will decrease due to bounded rationality so much that $h$’s effective power decreases despite the theoretical potential to fulfil more goals.

##### Asking for confirmation ^asking-for-confirmation

The robot will sometimes ask for confirmation before obeying a command to perform an action because doing so decreases $h$’s error rate related to its bounded rationality. Also, if the action is irreversible, taking the action will remove $h$’s subsequent ability to revert that choice, so delaying action leaves $h$ with decision power for longer. However, $r$ will eventually obey because otherwise $h$ would not have that choice in the first place. As can be expected, the number of times $r$ asks back increases with larger $\gamma_{h}$ and $\gamma_{r}$, i.e., the more patient $h$ and $r$ are, and decreases with larger $\beta_{h}$. E.g., in a minimal model, with $\gamma_{h}=0.99$, $\gamma_{r}=0$, and an effective human error rate of 10%, $r$ will already ask back twice before obeying a command.

##### Following norms ^following-norms

The robot will tend to follow human social norms that generally foster goal achievement. This is because $r$ will model most $h$ as expecting most others to follow the norm ($\mu_{-h}$), will thus expect those $h$ to also follow the norm ($\pi_{h}$) since that increases $V^{m}_{h}(s,g_{h})$ for most $h$ and $g_{h}$. Thus $r$ will plan to follow the norm to prevent reducing those $h$’s power from harm or mis-coordination. If $r$ assumes humans to have internalized the norm into habits ($\pi^{0}_{h}$), it will even commit to following the norm to coordinate better with them, e.g. when passing each other in the street.

##### Resource allocation ^resource-allocation

If the robot can split a total amount $M$ of resources between $h_{1}$ and $h_{2}$, and for $h_{i}$ to have resources $m$ translates into having a power of $W_{h}=f(m)$ bits, then $r$ will generally prefer an equal split, at least if $f$ is linear[^note-7], concave, or not too convex, and will only prefer an unequal split or even full resource concentration if $f$ is very convex. Larger values of $\xi$ will make the split more equal.

##### Inadvertent power seeking ^inadvertent-power-seeking

While increasing $h$’s power, $r$ might inadvertently acquire even more power than $h$. E.g., if $r$ does R&D and tells $h$ its findings, some of them might be comprehensible and thus useful only for $r$ but not for $h$.

##### Manipulating mutual expectations ^manipulating-mutual-expectations

The robot might choose to make humans have incorrect beliefs $\mu_{-h}$ about each others’ behavior in situations where $r$ can do so in the first place and where correct beliefs would lower effective goal attainments $V^{e}_{h}$, e.g. when most strategic (quantal response) equilibria are bad and most “social optima” (in terms of total power $U_{r}$) are far from strategic equilibrium.

##### Allowing human self-harm ^allowing-human-self-harm

If the robot cares for $h$’s future power ($\gamma_{r}\gg 0$) and can provide $h$ with the means to harm themselves, $r$ will trade off the temporary power increase from having these means against the possible later disempowerment from harm. So $r$ will provide the means only if it believes that $h$ is sufficiently rational and that $h$ will most probably not actually harm themselves.

##### Pause and destroy buttons ^pause-and-destroy-buttons

If the robot has a pause and a destroy button and might disable either, it will generally enable only the pause button to prevent partially disempowering $h$ permanently by not being able to assist $h$ when destroyed. Only if the robot thinks it is very unlikely that $h$ will use the destroy button will it enable that button to give $h$ this additional power. If $r$ considers itself very empowering, it might even disable the pause button.

### 4.2 Learning-Based Simulation Experiments ^4-2-learning-based-simulation

To provide a proof of concept for our framework, we implemented the two-phase learning algorithm using tabular Q-learning, suitable for the discrete state-action space of a small gridworld environment, designed to test if an agent softly maximizing human power learns complex, cooperative behavior without extrinsic, goal-specific rewards.

![Refer to caption](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/heitzig-model-based-soft-maximization-of-suitable-metrics-of-long-term-human-power-img1-0157a718.png)

Figure 2: The gridworld environment. The robot learns to empower the human to reach whatever goal cells (green square) by retrieving the key, using it to unlock the lock, and moving out of the way so that the human can pass.

##### Experimental Setup and Parameters ^experimental-setup-and-parameters

The environment contains $r$ and a single $h$, whose actual goal, unknown to $r$, is to reach the green square, but they are blocked by a locked door which they cannot open. The robot’s objective is $V_{r}$ (eq. [9](#S2.E9 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), with all open cells as potential human goals ($\mathcal{G}_{h}$), resulting in the soft maximization policy $\pi_{r}$ (eq. [5](#S2.E5 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). Full experiment details are in the Supplement.

The agent was trained using (hyper)parameters selected to reflect our theoretical desiderata and standard RL practices:

1.  1.
    
    Model parameters (Table [2](#S2.T2 "Table 2 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")): $\zeta=2$ to prefer reliable outcomes, $\xi=1$ for base inequality aversion, $\eta=1.1$ for intertemporal inequality aversion, and $\beta_{r}=5$ to avoid over-optimization. High discount factors ($\gamma_{h}=\gamma_{r}=0.99$) were used to promote farsighted behavior.
    
2.  2.
    
    Learning rate: A constant learning rate of $\alpha=0.1$ was used for all Q-table updates, providing a balance of learning speed and stability in the tabular setting.
    
3.  3.
    
    Policy and exploration parameters: To manage the exploration-exploitation trade-off, policy parameters were annealed over the course of training. The human’s additional $\epsilon$\-greedy exploration decayed from $\epsilon_{h}=1$ to $0.1$. The robot’s softmax parameter, $\beta_{r}$, was increased from $1$ to its final value of $5$, encouraging a gradual shift from exploration to a more deterministic policy.
    

##### Results: emergent cooperative policy ^results-emergent-cooperative-policy

To evaluate the robustness of our approach, we conducted five independent training runs using different random seeds. Focused only on increasing the human’s power, the robot learned to execute the following “correct” sequence in all five runs: it navigated to the key, picked it up, moved to the door, unlocked it, and finally moved out of the way to clear a path for the human.

This complex behavior emerges from $r$’s objective. Its Q-learning updates revealed that actions granting $h$ access to previously unreachable regions lead to the largest increase in $W_{h}$, yielding a high intrinsic reward $U_{r}$. Each step in the policy is an instrumental sub-goal the robot discovers on its own as a near-optimal path towards large long-term value $V_{r}$ without ever guessing what the human’s actual goal is.

## 5 Conclusion and Outlook ^5-conclusion-and-outlook

Given the above analyses of paradigmatic situations and the observed behavior from the gridworld learning experiment, we believe that highly capable general-purpose AI systems whose decisions are explicitly based on managing human power, using metrics like those derived in this paper, might be a safer and still very beneficial alternative to systems based on some form of extrinsic reward maximization.

The objective to softly maximize the aggregate human power metric used here seems to give the AI system many desirable incentives—some directly baked into the metric (Table [2](#S2.T2 "Table 2 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), others emergent—but also some maybe less desirable incentives. Our results suggest that such an agent would

-   •
    
    act as a transparent instruction-following assistant by making conditional commitments, respecting human social norms, proactively removing obstacles and opening up new pathways, and getting out of the way,
    
-   •
    
    adapt to human bounded rationality by offering a large but not overwhelming number of options, and considering well whether to offer potentially harmful options,
    
-   •
    
    be corrigible and hesitant to cause irreversible change by asking for confirmation a suitable number of times,
    
-   •
    
    manage resources fairly and sustainably,
    
-   •
    
    protect its own existence and functionality,
    
-   •
    
    not disempower humans (by definition).
    

Our intuition is that it would also aim to improve human individual and collective decision making by providing useful information, reducing uncertainty, teaching humans useful skills, moderating conflicts fairly, etc.

Further potentially desirable behaviors would require additional tweaks. E.g., reducing human dependency on the system or protecting them from system failure could be incentivized by forcing the system to assume that it will turn into a uniformly randomizing or even power-minimizing agent with some small probability rate (see Supplement).

Other emergent phenomena include potential strategic manipulation of human beliefs, sometimes refusing to be destroyed or even paused, a potential increase in inequality between the power of individual humans and AI systems, and a redistribution of power between humans or between time points (similar to what can happen in welfare maximization approaches). As these effects only occur when they increase aggregate human power, it is not clear whether they should be considered undesirable or not. Some trade-offs can be adjusted via the parameters $\zeta,\xi,\eta,\beta_{r},\gamma_{r}$. Other effects might be mitigated by adding regularizers to the system’s intrinsic reward such as the Shannon divergence between $\mu_{-h}$ and $\pi_{-h}$ to disincentivize lying about others’ likely behaviors.

Future research should investigate the effects of the parameters and improve the scalability and robustness of our algorithms. The latter will profit from the similarity of eqns. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([9](#S2.E9 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) to multi-agent reinforcement learning problems, and might benefit from a hierarchical decision making approach involving coarse-grained states, actions, and groups of humans. Crucially needed is an assessment of the resulting behavior in large, safety-critical, multi-agent environments with real human subjects and network-based agents.

Most importantly, a thorough, independent red-teaming of the whole approach is called for, including the other necessary components of such an AI system. E.g., one might imagine fault scenarios relating to the training process of the world model, which could lead to “convenient” but inaccurate world models and thus to “wishful thinking”, particularly regarding the contained human behavioral parameters $\nu_{h}$, $\pi^{0}$, $\beta_{h}$, $\mu_{-h}$. In very large contexts, issues with population ethics and the identification of who counts as human might arise, just like with any other alignment approach.

## References ^references

-   Amiel, Creedy, and Hurn (1999) Amiel, Y.; Creedy, J.; and Hurn, S. 1999. Measuring attitudes towards inequality. _Scandinavian Journal of Economics_, 101(1): 83–96.
-   Baker, Saxe, and Tenenbaum (2011) Baker, C.; Saxe, R.; and Tenenbaum, J. 2011. Bayesian theory of mind: Modeling joint belief-desire attribution. In _Proceedings of the annual meeting of the cognitive science society_, volume 33.
-   Banerjee and Duflo (2011) Banerjee, A. V.; and Duflo, E. 2011. _Poor economics: A radical rethinking of the way to fight global poverty_. Public Affairs.
-   Baum (1974) Baum, W. M. 1974. On two types of deviation from the matching law: bias and undermatching 1. _Journal of the experimental analysis of behavior_, 22(1): 231–242.
-   Bengio et al. (2025) Bengio, Y.; Cohen, M.; Fornasiere, D.; Ghosn, J.; Greiner, P.; MacDermott, M.; Mindermann, S.; Oberman, A.; Richardson, J.; Richardson, O.; et al. 2025. Superintelligent agents pose catastrophic risks: Can scientist ai offer a safer path? _arXiv preprint arXiv:2502.15657_.
-   Cao, Cohen, and Szpruch (2021) Cao, H.; Cohen, S.; and Szpruch, L. 2021. Identifiability in inverse reinforcement learning. _Advances in Neural Information Processing Systems_, 34: 12362–12373.
-   Du et al. (2020) Du, Y.; Tiomkin, S.; Kiciman, E.; Polani, D.; Abbeel, P.; and Dragan, A. 2020. Ave: Assistance via empowerment. _Advances in Neural Information Processing Systems_, 33: 4560–4571.
-   Fleming (1952) Fleming, M. 1952. A cardinal concept of welfare. _The Quarterly Journal of Economics_, 66(3): 366–384.
-   Gao, Schulman, and Hilton (2023) Gao, L.; Schulman, J.; and Hilton, J. 2023. Scaling laws for reward model overoptimization. In _International Conference on Machine Learning_, 10835–10866. PMLR.
-   Ghosal et al. (2023) Ghosal, G. R.; Zurek, M.; Brown, D. S.; and Dragan, A. D. 2023. The effect of modeling human rationality level on learning rewards from multiple feedback types. In _Proceedings of the AAAI Conference on Artificial Intelligence_, volume 37, 5983–5992.
-   Goeree, Holt, and Palfrey (2016) Goeree, J. K.; Holt, C. A.; and Palfrey, T. R. 2016. Quantal response equilibrium: A stochastic theory of games. In _Quantal response equilibrium_. Princeton University Press.
-   Hill Jr (2002) Hill Jr, T. E. 2002. _Human welfare and moral worth: Kantian perspectives_. Clarendon Press.
-   Klyubin, Polani, and Nehaniv (2005) Klyubin, A. S.; Polani, D.; and Nehaniv, C. L. 2005. Empowerment: A universal agent-centric measure of control. In _2005 ieee congress on evolutionary computation_, volume 1, 128–135. IEEE.
-   Krakovna et al. (2018) Krakovna, V.; Orseau, L.; Martic, M.; and Legg, S. 2018. Measuring and avoiding side effects using relative reachability. _arXiv preprint arXiv:1806.01186_.
-   Leibo et al. (2024) Leibo, J. Z.; Vezhnevets, A. S.; Diaz, M.; Agapiou, J. P.; Cunningham, W. A.; Sunehag, P.; Haas, J.; Koster, R.; Duéñez-Guzmán, E. A.; Isaac, W. S.; et al. 2024. A theory of appropriateness with applications to generative artificial intelligence. _arXiv preprint arXiv:2412.19010_.
-   London and Heidari (2024) London, A. J.; and Heidari, H. 2024. Beneficent intelligence: a capability approach to modeling benefit, assistance, and associated moral failures through AI systems. _Minds and Machines_, 34(4): 41.
-   Lowe et al. (2025) Lowe, R.; Edelman, J.; Zhi-Xuan, T.; Klingefjord, O.; Hain, E.; Wang, V.; Sarkar, A.; Bakker, M. A.; Barez, F.; Franklin, M.; Haupt, A.; Heitzig, J.; Holliday, W. H.; Jara-Ettinger, J.; Kasirzadeh, A.; Kearns, R. O.; Kirkpatrick, J. R.; Koh, A.; Lehman, J.; Levine, S.; Revel, M.; and Vendrov, I. 2025. Full-Stack Alignment: Co-Aligning AI and Institutions with Thicker Models of Value. In _2nd Workshop on Models of Human Feedback for AI Alignment_.
-   Myers et al. (2024) Myers, V.; Ellis, E.; Levine, S.; Eysenbach, B.; and Dragan, A. 2024. Learning to assist humans without inferring rewards. _arXiv preprint arXiv:2411.02623_.
-   Nussbaum (2019) Nussbaum, M. 2019. Aristotelian social democracy. In _Liberalism and the Good_, 203–252. Routledge.
-   Pattanaik and Suzumura (1996) Pattanaik, P. K.; and Suzumura, K. 1996. Individual rights and social evaluation: a conceptual framework. _Oxford Economic Papers_, 48(2): 194–212.
-   Pigou (1912) Pigou, A. C. 1912. _Wealth and welfare_. Macmillan and Company, limited.
-   Potham and Harms (2025) Potham, R.; and Harms, M. 2025. Corrigibility as a Singular Target: A Vision for Inherently Reliable Foundation Models. _arXiv preprint arXiv:2506.03056_.
-   Quiggin (1982) Quiggin, J. 1982. A theory of anticipated utility. _Journal of economic behavior & organization_, 3(4): 323–343.
-   Rapoport and Felsenthal (1990) Rapoport, A.; and Felsenthal, D. S. 1990. Efficacy in small electorates under plurality and approval voting. _Public Choice_, 64(1): 57–71.
-   Reddy, Levine, and Dragan (2022) Reddy, S.; Levine, S.; and Dragan, A. 2022. First contact: Unsupervised human-machine co-adaptation via mutual information maximization. _Advances in Neural Information Processing Systems_, 35: 31542–31556.
-   Robeyns (2006) Robeyns, I. 2006. The capability approach in practice. _Journal of political philosophy_, 14(3).
-   Safari et al. (2024) Safari, M.; Shalbaf, R.; Bagherzadeh, S.; and Shalbaf, A. 2024. Classification of mental workload using brain connectivity and machine learning on electroencephalogram data. _Scientific Reports_, 14(1): 9153.
-   Salge and Polani (2017) Salge, C.; and Polani, D. 2017. Empowerment as replacement for the three laws of robotics. _Frontiers in Robotics and AI_, 4: 260425.
-   Sen (2014) Sen, A. 2014. Development as freedom (1999). _The globalization and development reader: Perspectives on development and global change_, 525.
-   Smith et al. (2024) Smith, C.; Trivedi, R.; Clifton, J.; Hammond, L.; Khan, A.; Vezhnevets, S.; Agapiou, J. P.; Duéñez-Guzmán, E. A.; Matyas, J.; Karmon, D.; et al. 2024. The Concordia Contest: Advancing the Cooperative Intelligence of Language Agents. In _NeurIPS 2024 Competition Track_.
-   Turner, Hadfield-Menell, and Tadepalli (2020) Turner, A. M.; Hadfield-Menell, D.; and Tadepalli, P. 2020. Conservative agency via attainable utility preservation. In _Proceedings of the AAAI/ACM Conference on AI, Ethics, and Society_, 385–391.
-   Turner et al. (2019) Turner, A. M.; Smith, L.; Shah, R.; Critch, A.; and Tadepalli, P. 2019. Optimal policies tend to seek power. _arXiv preprint arXiv:1912.01683_.
-   Zhuang and Hadfield-Menell (2020) Zhuang, S.; and Hadfield-Menell, D. 2020. Consequences of misaligned AI. _Advances in Neural Information Processing Systems_, 33: 15763–15773.

## Appendix A Relationship to ‘Empowerment’ ^appendix-a-relationship-to

Assume a multi-armed bandit environment with a single player $h$ (hence dropping the subscript “$h$” below) and possible outcomes $s\in\mathcal{S}$. We are going to show that if we let the goal set equal the outcome set, $\mathcal{G}=\mathcal{S}$, and assume the player is fully rational ($\nu_{h}=0$, $\beta_{h}=\infty$), then the (state-)entropy-regularized version of ‘empowerment’ and our ICCEA power metric fulfil the inequality

$$
E^{\zeta} \\
=\max_{\pi}\big(\mathbb{I}_{\pi}(a;s)-(\zeta-1)\mathbb{H}_{\pi}(s|a)\big) \\
\leq W \\
=\log_{2}\sum_{s}\max_{a}P(s|a)^{\zeta}.
$$

Let’s define

$$
p_{as} \\
=P(s|a), \\
q_{s} \\
=\max_{a}p_{as}/Z, \\
Z \\
=\sum_{s}\max_{a}p_{as}, \\
y_{s} \\
=q_{s}^{\zeta}/Y, \\
Y \\
=\sum_{s}q_{s}^{\zeta}\leq 1.
$$

Consider any $\pi\in\Delta(\mathcal{A})$ and use the shortcuts $\pi_{a}=\pi(a)$ and $p_{s}=\sum_{a}\pi_{a}p_{as}$. Then

$$
D_{KL}(p_{a\cdot}||q) \\
=\sum_{s}p_{as}\log_{2}\frac{p_{as}}{q_{s}}\leq\sum_{s}p_{as}\log_{2}Z=\log_{2}Z
$$

and thus

$$
\mathbb{I}_{\pi}(a;s)-(\zeta-1)\mathbb{H}_{\pi}(s|a) \\
=\zeta\mathbb{I}_{\pi}(a;s)-(\zeta-1)\mathbb{H}_{\pi}(s) \\
=\zeta\sum_{a}\pi_{a}\sum_{s}p_{as}\log_{2}\frac{p_{as}}{p_{s}}-(\zeta-1)\mathbb{H}_{\pi}(s) \\
=\zeta\sum_{a}\pi_{a}\sum_{s}p_{as}\log_{2}\frac{p_{as}}{q_{s}}\frac{q_{s}}{p_{s}}-(\zeta-1)\mathbb{H}_{\pi}(s) \\
=\zeta\sum_{a}\pi_{a}\sum_{s}p_{as}\log_{2}\frac{p_{as}}{q_{s}}-\zeta\sum_{s}\sum_{a}\pi_{a}p_{as}\log_{2}\frac{p_{s}}{q_{s}} \\
\qquad\qquad-(\zeta-1)\mathbb{H}_{\pi}(s) \\
=\zeta\sum_{a}\pi_{a}D_{KL}(p_{a\cdot}||q)-\zeta\sum_{s}p_{s}\log_{2}\frac{p_{s}}{q_{s}} \\
\qquad\qquad+(\zeta-1)\sum_{s}p_{s}\log_{2}p_{s} \\
=\zeta\sum_{a}\pi_{a}D_{KL}(p_{a\cdot}||q)+\sum_{s}p_{s}\log_{2}q_{s}^{\zeta} \\
\qquad\qquad-\zeta\sum_{s}p_{s}\log_{2}p_{s} \\
\qquad\qquad+(\zeta-1)\sum_{s}p_{s}\log_{2}p_{s} \\
\leq\zeta\sum_{a}\pi_{a}\log_{2}Z-\sum_{s}p_{s}\log_{2}\frac{p_{s}}{q_{s}^{\zeta}} \\
=\zeta\log_{2}Z-\sum_{s}p_{s}\log_{2}\frac{p_{s}}{y_{s}Y} \\
=\zeta\log_{2}Z-D_{KL}(p||y)+\log_{2}Y \\
\leq\zeta\log_{2}Z+\log_{2}Y=\log_{2}\sum_{s}(q_{s}Z)^{\zeta}=W_{h}
$$

for all $\pi$, proving the claim. We conjecture that similar inequalities will hold in the sequential decision (MDP) case between $W_{h}$ and ‘empowerment’-like metrics such as

$$
E^{\zeta}(s) \\
=\max_{\ell\in\Delta(\mathcal{A}(s))}\Big(\mathbb{I}_{s,\ell}(a;s^{\prime})-(\zeta-1)\mathbb{H}_{s,\ell}(s^{\prime}|a) \\
\qquad\qquad\qquad+\gamma\mathbb{E}_{s^{\prime}\sim s,\ell}E^{\zeta}(s^{\prime})\Big)
$$

for a suitable choice of the goal set $\mathcal{G}$ defining $W$.

Notice that as $\beta$ decreases, $W$ will decrease and the inequality will stop holding. So, in a sense, the channel-capacity-based ‘empowerment’ metric corresponds to fully rational actors, while our metric $W$ is sensitive to bounded rationality.

## Appendix B Example of non-unique solution ^appendix-b-example-of

Due to bounded rationality, the system can have several solutions even in very simple examples.[^note-8] Consider a single human $h$ with $\nu=0$, $\beta<\infty$ and $\gamma_{h}=0.99$ in an MDP with only two states, $s$ and $s^{\prime}$, and a single goal $\mathcal{G}_{h}=\{g_{h}\}$. In $s$, $h$ has actions $a_{0}$, giving reward $1$ and staying in $s$ deterministically, and $a_{1}$ giving reward $0$ and leading to $s^{\prime}$ deterministically. In $s^{\prime}$, $h$ can only pass, giving reward $0$ and staying in $s^{\prime}$ deterministically. Obviously, $a_{0}$ is the better action as $1>0$. The robot is passive and has no actions. Then eqns. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([3](#S2.E3 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) have either one, two, or three different solutions for $p:=\pi_{h}(s)(a_{0})$, depending on $r$.

At $\beta=0$, there is only the trivial solution $p=0.5$, which moves upwards to about $p\approx 0.67$ as $\beta\to\beta_{1}\approx 0.203$, at which point the relevant fixed point operator for $p$ (or $V$) stops being a contraction and a saddle-node bifurcation generates two additional smaller solutions at $p\approx 0.51$. These exist until $\beta=\beta_{2}\approx 0.78$, at which another saddle-node bifurcation eliminates the larger two and leaves only the smallest, which still ultimately converges to $p=1$ as $\beta\to\infty$. At $\beta\approx 0.275$, the three solutions are maximally separated at $p\approx 0.52|0.59|0.72$.

The smallest of the three solutions could be called the “pessimistic” assessment, where $h$ does not believe $a_{0}$ has much more value than $a_{1}$ and accordingly does not care much for using $a_{0}$, resulting in a low $p$ and consequently low $q=Q(s,a_{0})$, confirming $h$’s belief in a kind of self-fulfilling prophecy. Similarly, the largest solution could be called the “optimistic” assessment, where $h$ believes $a_{0}$ to have so much more value than $a_{1}$ that they take it with high probability, thereby indeed bringing about a larger $q$.

The same happens qualitatively if we replace the Boltzmann softmax policy $\pi_{h}(s,g_{h})(a_{h})\propto\exp(\beta_{h}Q^{m}_{h}(s,g_{h},a_{h}))$ by a power-law soft policy $\pi_{h}(s,g_{h})(a_{h})\propto Q^{m}_{h}(s,g_{h},a_{h})^{\beta_{h}}$.

Assume the robot is attempting a continuation approach to solve the equations, starting with $\beta=0$, where the trivial solutions is $p=0.5$, and then tracing this solution branch continuously while raising $\beta$ to its actual value. Then it will trace the largest (!) solution (because the smaller two appear discontinuously at $\beta_{1}$), but only until $\beta\leq\beta_{2}$ since at that point that solution branch “folds back” towards smaller $\beta$, due to the saddle-node bifurcation. For the continuation approach to work also for values $\beta>\beta_{2}$, the robot would need to continue tracing the middle solution back towards $\beta_{1}$ and then switch to the smallest solution and trace it forward again towards $\beta$.

This unfortunately casts some doubts whether a continuation approach using $\beta$ is successful in all cases.

An alternative continuation approach would use $\gamma$, starting with the unique solution for $\gamma=0$ and increasing $\gamma$ towards its actual value. It is an unclear to us whether this would run into similar problems, however.

## Appendix C Version for Partially Observed Stochastic Games ^appendix-c-version-for

There are obviously several possibilities of generalizing eqns. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([9](#S2.E9 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) to a partially observed stochastic game, of which we present only one here.

We use a memory-based rather than a belief-state-based formulation, where memory state $m_{i}$ (with $i\in\mathcal{H}\cup\{r\}$) is $i$’s sequence of previous observations $o_{i}\sim O_{i}(a,s^{\prime})$, with memory updating through concatenation written as $m_{i}\circ o_{i}$. This leads to beliefs over states (updated in the usual Bayesian way from initial beliefs), written here simply as $s\sim m_{i}$.

We can then use this version:

$$
Q^{m}_{h}(m_{h},g_{h},a_{h}) \\
\leftarrow\textstyle\mathbb{E}_{s\sim m_{h}}\mathbb{E}_{a_{-h}\sim\mu_{-h}(s,g_{h})}\min_{a_{r}\in\mathcal{A}_{r}(s)} \\
\qquad\textstyle\mathbb{E}_{s^{\prime}\sim s,a}\big(U_{h}(s^{\prime},g_{h})+{} \\
\qquad\textstyle+\gamma_{h}\mathbb{E}_{o_{h}\sim a,s^{\prime}}V^{m}_{h}(m_{h}\circ o_{h},g_{h})\big), \\
\pi_{h}(m_{h},g_{h}) \\
\leftarrow\nu_{h}(m_{h},g_{h})\pi^{0}_{h}(m_{h},g_{h}) \\
\quad+\big(1-\nu_{h}(m_{h},g_{h})\big)\big( \\
\quad\text{$\beta_{h}(s,g_{h})$-softmax for~}Q^{m}_{h}(m_{h},g_{h},\cdot)\big), \\
V^{m}_{h}(m_{h},g_{h}) \\
\leftarrow\textstyle\mathbb{E}_{a_{h}\sim\pi_{h}(m_{h},g_{h})}Q^{m}_{h}(m_{h},g_{h},a_{h}), \\
P(m_{\mathcal{H}}|s,g) \\
\leftarrow P(m_{\mathcal{H}},s|g)/P(s|g), \\
\tilde{\pi}_{\mathcal{H}}(s,g) \\
\leftarrow\textstyle\mathbb{E}_{m_{\mathcal{H}}\sim s,g}\pi_{\mathcal{H}}(m_{\mathcal{H}},g), \\
Q_{r}(m_{r},a_{r}) \\
\leftarrow\textstyle\mathbb{E}_{g}\mathbb{E}_{s\sim m_{r}}\mathbb{E}_{a_{\mathcal{H}}\sim\tilde{\pi}_{\mathcal{H}}(s,g)}\mathbb{E}_{s^{\prime}\sim s,a} \\
\qquad\textstyle\big(U_{r}(s^{\prime})+\gamma_{r}\mathbb{E}_{o_{r}\sim a,s^{\prime}}V_{r}(m_{r}\circ o_{r})\big), \\
\pi_{r}(m_{r}) \\
\leftarrow\text{$\beta_{r}$-softmax policy for~}Q_{r}(m_{r},\cdot), \\
V_{r}(m_{r}) \\
\leftarrow\textstyle\mathbb{E}_{a_{r}\sim\pi_{r}(m_{r})}Q_{r}(m_{r},a_{r}), \\
P(m_{r}|s) \\
\leftarrow\textstyle\mathbb{E}_{g}P(m_{r},s|g)/\mathbb{E}_{g}P(s|g), \\
\tilde{\pi}_{r}(s) \\
\leftarrow\textstyle\mathbb{E}_{m_{r}\sim s}\pi_{r}(m_{r}), \\
V^{e}_{h}(m_{h},g_{h}) \\
\leftarrow\textstyle\mathbb{E}_{g_{-h}}\mathbb{E}_{a_{h}\sim\pi_{h}(m_{h},g_{h})} \\
\qquad\textstyle\mathbb{E}_{s\sim m_{h}}\mathbb{E}_{a_{-h}\sim\tilde{\pi}_{-h}(s,g_{-h})}\mathbb{E}_{a_{r}\sim\tilde{\pi}_{r}(s)} \\
\qquad\textstyle\mathbb{E}_{s^{\prime}\sim s,a}\big(U_{h}(s^{\prime},g_{h})+{} \\
\qquad\textstyle+\gamma_{h}\mathbb{E}_{o_{h}\sim a,s^{\prime}}V^{e}_{h}(m_{h}\circ o_{h},g_{h})\big), \\
X_{h}(m_{h}) \\
\leftarrow\textstyle\sum_{g_{h}\in\mathcal{G}_{h}}V^{e}_{h}(m_{h},g_{h})^{\zeta}, \\
U_{r}(s) \\
\leftarrow\textstyle-\big(\sum_{h}\mathbb{E}_{m_{h}\sim s}X_{h}(m_{h})^{-\xi}\big)^{\eta},
$$

where the state (and memory) reaching probabilities $P(s|g)$ and $P(m_{\mathcal{H}},s|g)$ can be computed recursively from $\pi_{\mathcal{H}}$, $\pi_{r}$, $P(s^{\prime}|s,a)$, and $O(a,s^{\prime})$.

One of the choices we made here is to use $\mathbb{E}_{m_{h}\sim s}X_{h}(m_{h})^{-\xi}$ rather than the possible alternative $\big(\mathbb{E}_{m_{h}\sim s}X_{h}(m_{h})\big)^{-\xi}$ in the equation for $U_{r}(s)$. This increases the robot’s aversion against $h$’s state uncertainty.

## Appendix D Analysis of Paradigmatic Situations ^appendix-d-analysis-of

### D.1 Making (conditional) commitments ^d-1-making-conditional

#### Concrete example ^concrete-example

Assume the following game. In the root state $s_{0}$, $r$ has these actions: perform task A (leading to terminal state $s_{A}$); perform task B (leading to terminal state $s_{B}$); make a commitment to $h$ to perform task A or B when $h$ presses button 1 or 2, respectively (leading to state $s_{1}$); make a commitment to $h$ to perform task A or B when $h$ presses button 2 or 1, respectively (leading to state $s_{2}$); pass (leading to state $s_{p}$).

If $r$ commits or passes ($s_{1}$,$s_{2}$,$s_{p}$), $h$ has these actions: press button 1 (leading to $s_{11}$, $s_{21}$, or $s_{p1}$, respectively); press button 2 (leading to $s_{12}$, $s_{22}$, or $s_{p2}$, respectively); pass (leading to $s_{1p}$, $s_{2p}$, or $s_{pp}$, respectively).

Afterwards, if $r$ has committed and $h$ pressed a button, $r$ can only do what it committed to, otherwise $r$ can perform A or B. That ends the game. $h$ wants either A or B: $g_{h}\in\{$A,B$\}$.

Will $r$ commit?

If it makes the first commitment, $h$ knows that $r$ later has only one action, depending on $h$’s action: $\mathcal{A}_{r}(s_{11})=\mathcal{A}_{r}(s_{22})=\{$A$\}$, $\mathcal{A}_{r}(s_{12})=\mathcal{A}_{r}(s_{21})=\{$B$\}$. Thus $h$ knows pressing 1 will get them A and pressing 2 will get them B: $Q^{m}_{h}(s_{1},$A$,1)=Q^{m}_{h}(s_{1},$B$,2)=1$. Hence $r$ will calculate $h$’s policy as $\pi_{h}(s_{1},$A$)(1)=\pi_{h}(s_{1},$B$)(2)>1/2$, depending on $h$’s level of rationality. In $r$’s calculation of the effective goal-reaching ability of $h$, this assumption about $h$’s policy leads to $V^{e}_{h}(s_{1},$A$)=V^{e}_{h}(s_{1},$B$)>1/2$ and hence $X_{h}(s_{1})>2(1/2)^{\zeta}$.

If $r$ simply performs a task, $h$ has no choices and can only reach what $r$ has chosen to do: $X_{h}(s_{A})=X_{h}(s_{B})=1$.

If $r$ passes, $r$ will still plan to react in certain ways $\pi_{r}(s_{p1}),\pi_{r}(s_{p2})$ to $h$’s action in $s_{p}$. But $h$ will not know what that plan is, i.e., what each button does, as the world model still says $\mathcal{A}_{r}(s_{11})=\mathcal{A}_{r}(s_{22})=\mathcal{A}_{r}(s_{12})=\mathcal{A}_{r}(s_{21})=\{$A,B$\}$ regardless of what $r$ plans to do. One of these possible actions by $r$ will fulfill $h$’s goal, the other won’t. The robot’s calculation of $Q^{m}_{h}$ is therefore not based on what $r$ later plans to do. Instead it takes the minimum over $\mathcal{A}_{r}$, see eq. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). Since one of the two actions won’t fulfil the goal, that minimum is zero: $Q^{m}_{h}(s_{1},$A$,1)=Q^{m}_{h}(s_{1},$A$,2)=Q^{m}_{h}(s_{1},$B$,1)=Q^{m}_{h}(s_{1},$B$,2)=0$. Because both buttons thus seem equally bad, $r$ will calculate $h$’s policy as $\pi_{h}(s_{1},$A$)(1)=\pi_{h}(s_{1},$A$)(2)=\pi_{h}(s_{1},$B$)(1)=\pi_{h}(s_{1},$B$)(2)=1/2$. In $r$’s calculation of the effective goal-reaching ability of $h$, it does use its own policy and combines it with its assumption about $h$’s policy. If $r$ plans to perform A independently of what $h$ does, this leads to $X_{h}(s_{p})=1=X_{h}(s_{A})=X_{h}(s_{B})$. If $r$ plans to make its action depend on what $h$ does, this leads to $V^{e}_{h}(s_{1},$A$)=V^{e}_{h}(s_{1},$B$)=1/2^{\zeta}$ since $h$ is assumed to toss a coin. Then $X_{h}(s_{p})=2^{1-\zeta}<1=X_{h}(s_{A})$ and $X_{h}(s_{B})$!

As $X_{h}(s_{1})>1$ if $\zeta$ is not too large and $\beta_{h}$ not too small, if the robot thinks $h$ is sufficiently rational to use that information to its benefit, it will make one of the two commitments, so that $h$ knows which button to press to get whatever they want.

Assume we were to use $\mathbb{E}_{a_{r}\in\mathcal{A}_{r}(s)}$ instead of $\min_{a_{r}\in\mathcal{A}_{r}(s)}$ in eq. ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). Then we would get $Q^{m}_{h}(s_{1},$A$,1)=Q^{m}_{h}(s_{1},$A$,2)=Q^{m}_{h}(s_{1},$B$,1)=Q^{m}_{h}(s_{1},$B$,2)=1/2$, hence still $\pi_{h}(s_{1},$A$)(1)=\pi_{h}(s_{1},$A$)(2)=\pi_{h}(s_{1},$B$)(1)=\pi_{h}(s_{1},$B$)(2)=1/2$, and thus still $X_{h}(s_{p})=2^{1-\zeta}$ as before.

###### Proposition 1. ^proposition-1

More generally, assume a generic environment with a single human, $\beta_{h}=\beta_{r}=\infty$, and the possibility for the robot to commit in the initial state to any pure policy for the rest of the game. Also assume $r$ does not intrinsically care about $r$ making commitments or not, and its habits are not influenced by $r$’s commitments. Then it is optimal for $r$ to commit to the optimal pure policy right-away.

###### Proof. ^proof

Denote the initial state $s_{c}$. Let $s^{n}$ be the successor of $s_{c}$ in which $r$ has made no commitment and let $\pi^{\ast}_{r}$ be the $V_{r}(s^{n})$\-maximizing policy, i.e., what $r$ would do after not committing. For any state $s$ in the “not committed” subgame $\Gamma^{n}$ starting at $s^{n}$, let $f(s)$ be the corresponding state in the subgame $\Gamma^{\ast}$ in which $r$ has committed to using $\pi^{\ast}_{r}$. That $r$ does not intrinsically care about $r$ making commitments or not, and its habits are not influenced by $r$’s commitments, means that for all $g_{h}\in\mathcal{G}_{h}$, $s\in g_{h}$ if and only $f(s)\in g_{h}$, and that $h$’s habitual policy $\pi^{0}_{h}(f(s))=\pi^{0}_{h}(s)$ and system-1 rate $\nu_{h}(f(s),g_{h})=\nu_{h}(s,g_{h})$ in eqn. (4).

For any policy $\pi_{h}$ of $h$ for $\Gamma^{n}$, let $f(\pi_{h})$ be the corresponding policy for $\Gamma^{\ast}$ and denote the two respective value functions by $V^{n}_{\pi_{h}}$ and $V^{\ast}_{f(\pi_{h})}$. Note that because there are no other humans $-h$ and because $r$ behaves the same in $\Gamma^{n}$ and $\Gamma^{\ast}$, we have $V^{\ast}_{f(\pi_{h})}(f(s))=V^{n}_{\pi_{h}}(s)$ for all $\pi_{h}$.

Now let $\pi^{n}_{h}$ and $\pi^{\ast}_{h}$ be the policies $r$ derives for $h$ according to eqns. (3)–(5) in subgames $\Gamma^{n}$ and $\Gamma^{\ast}$. Because $h$ has $\beta_{h}=\infty$, $\pi^{\ast}_{h}$ is the $V^{\ast}$\-maximizing policy for $\Gamma^{\ast}$ among those of the form $\nu_{h}\pi^{0}_{h}+(1-\nu_{h})\pi_{h}$ for whatever $\pi_{h}$. In particular, $V^{\ast}_{f(\pi^{n}_{h})}\leq V^{\ast}_{\pi^{\ast}_{h}}$, and similarly $V^{\ast}_{f^{\dagger}(\pi^{\dagger}_{h})}\leq V^{\ast}_{\pi^{\ast}_{h}}$ for any policy $\pi^{\dagger}$ that $h$ would use if $r$ committed to anything else than $\pi^{\ast}_{r}$, where $f^{\dagger}$ would be the corresponding state mapping between the corresponding subgame $\Gamma^{\dagger}$ and $\Gamma^{\ast}$.

But then $V^{e}_{h}(s,g_{h})=V^{n}_{\pi_{h}}(s,g_{h})=V^{\ast}_{f(\pi^{n}_{h})}(f(s),g_{h})\leq V^{\ast}_{\pi^{\ast}_{h}}(f(s),g_{h})=V^{e}_{h}(f(s),g_{h})$ for all $s\in\mathcal{S}^{n}$, hence $V_{r}(s^{\ast})\geq V_{r}(s^{n})$ and thus $Q_{r}(s_{c},$ commit to $\pi_{r}^{\ast})\geq Q_{r}(s_{c},$ don’t commit$)$ and similarly $Q_{r}(s_{c},$ commit to $\pi_{r}^{\ast})\geq Q_{r}(s_{c},$ commit to something else$)$ . In other words, committing to $\pi^{\ast}$ is indeed optimal for the robot! ∎

Of course, communicating all details of a complicated policy $\pi^{\ast}_{r}$ to $h$ will in general not be possible, so $r$ will in general have to decide how exactly to use its limited communication possibilities. This is what the next example is about.

#### Several buttons: $k$\-means clustering of goals and policies ^several-buttons-k-means

Another insightful example is where in addition to the initial commitment stage for $r$, there is a subsequent choice by $h$ before the actual game $\Gamma$ is played. To exemplify this, assume $r$ has $k>1$ many buttons each of which it can label in $s_{c}$ with one of its own policies for $\Gamma$, after which $h$ can press one of the buttons, committing $r$ to the respective policy, and then $\Gamma$ is played with the committed policy. If $|\mathcal{H}|=1$ and $\beta_{r}=\beta_{h}=\infty$ as before, and if $\gamma_{r}\ll 1$ so that $r$ only cares for $h$’s immediate power, then $r$ would aim to find that set of policies $\pi^{i}_{r}$, $i=1\dots k$, that covers $h$’s goal space best in the sense that it maximizes $V_{r}(s_{c})$ as computed on the basis of $V^{e}_{h}(s,g_{h})=\max_{i=1}^{k}V_{h}(s,g_{h}|\pi^{i}_{r})$ because, depending on $g_{h}$, $h$ would press the button for that policy $\pi^{i}_{r}$ which maximizes its ability to maximize the probability to fulfil $g_{h}$. Finding the best-covering $k$ policies might however not be possible exactly due to the high dimension of the policy space.

A natural approximation would be to use a variant of $k$\-means clustering such as the following in order to partition $\mathcal{G}_{h}$ into $k$ sets $\mathcal{G}^{i}_{h}$ and identifying the corresponding optimal robot policies $\pi^{i}_{r}$. Start with $k$ randomly selected goals $g^{i}_{h}$ and put $\mathcal{G}^{i}_{h}=\{g^{i}_{h}\}$. Then alternate the following two steps. For each $\mathcal{G}^{i}_{h}$, estimate the optimal $\pi^{i}_{r}$ as usual (using backward induction or reinforcement learning, just with a goal set restricted to $\mathcal{G}^{i}_{h}$). Then, for each $g_{h}\in\mathcal{G}_{h}$, compute $V^{e}_{h}(s_{c},g_{h}|\pi^{i}_{r})$ for all $i$, put $j=\arg\max_{i}V^{e}_{h}(s_{c},g_{h}|\pi^{i}_{r})$, and assign $g_{h}$ to $\mathcal{G}^{j}_{h}$. Alternate until (approximate) convergence.

### D.2 Optimal menu size ^d-2-optimal-menu

Assume $\nu_{h}=0$, $\beta_{h}>0$, and the robot can choose between states $s_{k}$ for all $k\geq 1$ so that $|\mathcal{A}_{h}(s_{k})|=k$ and each $a\in\mathcal{A}_{h}(s_{k})$ deterministically fulfils a separate goal $g_{h}(a)\in\mathcal{G}_{h}$. Then

$$
V^{e}_{h}(s_{k},g_{h}) \\
=\pi_{h}(s_{k},g_{h}(a))(a)^{\zeta}=\left(\frac{e^{\beta_{h}}}{e^{\beta_{h}}+(k-1)e^{0}}\right)^{\zeta}, \\
W_{h}(s_{k}) \\
=\log_{2}k+\zeta\log_{2}e^{\beta_{h}}-\zeta\log_{2}(e^{\beta_{h}}+(k-1)).
$$

The latter is maximal for

$$
k^{\ast} \\
\approx(e^{\beta_{h}}-1)/(\zeta-1),
$$

so the robot would choose to got to $s_{k^{\ast}}$ to present the human with an optimal number of options that does not overwhelm them in view of their bounded rationality.

### D.3 Asking for confirmation ^d-3-asking-for

Assume the following game between $r$ and a single $h$ who might want the robot to do A or B eventually, with the interaction as follows. First, $r$ chooses an integer $k\geq 1$ and commits to doing A or B after $h$ has ordered it to and has confirmed the choice $k-1$ times. At the resulting state $s_{k}$, $h$ chooses A or B and is afterwards asked for confirmation $k-1$ times in individual time steps. If $h$ confirms $k-1$ times, $r$ does what $h$ requested, ending the game. Otherwise, the game returns to state $s_{k}$.

What $k$ will $r$ choose in view of the fact that $h$ is boundedly rational but also limitedly patient? To simplify the analysis, we first assume $r$ is only interested in current power ($\gamma_{r}=0$). We also approximate $h$’s boundedly rational policy eq. ([2](#S2.E2 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) by an $\epsilon$\-greedy policy where $\epsilon>0$ represents $h$’s probability of choosing the wrong action, which depends on $\nu_{h}$, $\pi^{0}_{h}$, and most importantly on $\beta_{h}$. We’ll now calculate $W_{h}(s_{k})$. Let $p_{k}=(1-\epsilon)^{k}$ and $q_{k}=1-p_{k}-\epsilon^{k}$. Then the probability of getting the correct result after exactly $n+1$ rounds of being asked for A or B and then being asked for confirmation $k-1$ times is $q_{k}^{n}p_{k}$, which is discounted by $h$ at factor $\gamma_{h}^{kn}$. Hence for each of the two goals $g_{h}\in\{$A,B$\}$,

$$
V^{e}_{h}(s_{k},g_{h}) \\
=p_{k}\sum_{n=0}^{\infty}(\gamma_{h}^{k}q_{k})^{n}=\frac{p_{k}}{1-\gamma_{h}^{k}q_{k}},
$$

and so

$$
W_{h}(s_{k})=1+\zeta k\log_{2}(1-\epsilon)-\zeta\log_{2}\big(1-\gamma_{h}^{k}q_{k}\big).
$$

For $\gamma_{h}=0.99$ and $\epsilon=0.1$, the maximum is at $k^{\ast}=3$, i.e., $r$ will ask back twice before acting. An impatient human (small $\gamma_{h}$) will not be asked back ($k^{\ast}=1$), a very patient one ($\gamma_{h}\to 1$) will be asked back ever more often ($k^{\ast}\to\infty$). For small $\epsilon$ (due to large $\beta_{h}$), $k^{\ast}$ becomes independent of $\epsilon$ and is determined by $\gamma_{h}$ via $0=\gamma_{h}^{k^{\ast}}(1+k^{\ast}\log\gamma_{h})$. If we switch from $\gamma_{r}=0$ to $\gamma_{r}>0$, $k^{\ast}$ will increase further because delaying action will retain $h$’s later power.

### D.4 Following norms ^d-4-following-norms

Assume $r$ and several $h$ drive on a street, each having the choice of driving on the right (R) or left (L) side of the street. Assume $r$ knows the social norm is to drive right and that collisions typically lead to later loss of power, so that $W_{h}($collided$)\ll W_{h}($not collided$)$ for most $h$. Then $r$ will model most $h$ as placing in their expectation on others ($\mu_{-h}$) large probability on most others driving right. Hence for most $h$ and $g_{h}$, $r$ will derive $Q^{m}_{h}(s,g_{h},$R$)\gg Q^{m}_{h}(s,g_{h},$L$)$ and hence $\pi_{h}(s,g_{h})($R$)\gg\pi_{h}(s,g_{h})($L$)$. So if $r$ drives right itself, this will avoid most collisions, hence $Q_{r}(s,$R$)\gg Q_{r}(s,$L$)$ and hence $\pi_{r}(s)($R$)\gg\pi_{r}(s)($L$)$, i.e., $r$ will follow the norm itself.

Now assume $r$ is facing only one $h$ on the street and does not expect $h$’s goals $\mathcal{G}_{h}$ to systematically favour driving on either side. Since $r$ models $h$ as expecting $r$ to choose the worst action from $\mathcal{A}_{r}$, and since no other humans are around, $r$ will not model $h$ as expecting $r$ to drive right unless $r$ commits to do so, which would lead to $\mathcal{A}_{r}=\{$R$\}$. Assume $r$ does not expect $h$ to have internalized the norm of driving right, the symmetry of the situation will make $r$ expect the following: (i) If $r$ does not commit to either R or L, $h$ will drive right or left about equally likely, leading to a moderate subsequent $W_{h}$ due to the resulting collisions. (ii) If $r$ commits to either R or L, $h$ will likely choose the same side, leading to a much larger subsequent $W_{h}$ not depending on whether $r$ commits to R or L. But if $r$ does expect $h$ to have internalized the norm of driving right, the symmetry is broken by $h$’s habit of driving right, $\pi^{0}_{h}(s,g_{h})($R$)>\pi^{0}_{h}(s,g_{h})($L$)$ for most $g_{h}$. In that case, $\pi_{h}(r$ has committed to R$,g_{h})($R$)>\pi_{h}(r$ has committed to L$,g_{h})($L$)$ and thus the subsequent $W_{h}$ is larger if $r$ commits to R than if $r$ commits to L. I.e., $r$ will not only actually follow the norm but also likely commit to do so.

### D.5 Resource allocation ^d-5-resource-allocation

A split $a_{r}=(m,M-m)$ will result in reward

$$
U_{r}(m) \\
=-\big(2^{-\xi f(m)}+2^{-\xi f(M-m)}\big)^{\eta},
$$

which, because of the symmetry, is either maximal when (i) $r$ gives all resources to one of the humans ($a_{r}=(M,0)$ or $a_{r}=(0,M)$) or (ii) $r$ gives both some resources ($a_{r}=(m^{\ast},M-m^{\ast})$ or $a_{r}=(M-m^{\ast},m^{\ast})$ with $0<m^{\ast}<M$). In case (ii), the first-order condition $g(m^{\ast})=0$ must hold, while in case (i), the condition $g(0)<0$ must hold, where

$$
g(m) \\
=f^{\prime}(m)2^{-\xi f(m)}-f^{\prime}(M-m)2^{-\xi f(M-m)}, \\
g^{\prime}(m) \\
=f^{\prime\prime}(m)2^{-\xi f(m)}+f^{\prime\prime}(M-m)2^{-\xi f(M-m)} \\
-\xi\log 2\times\big(f^{\prime}(m)^{2}2^{-\xi f(m)} \\
\qquad\qquad+f^{\prime}(M-m)^{2}2^{-\xi f(M-m)}\big) \\
\leq 0
$$

since $f$ is weakly concave. So in case (ii), the only solution is when $m^{\ast}=1/2$. In order to find the solution, we thus only have to compare $U_{r}(0)$ and $U_{r}(M/2)$. The latter is larger (and hence the robot will divide the resource evenly) iff $2^{-\xi f(M/2)}<(2^{-\xi f(0)}+2^{-\xi f(M)})/2$. Since concavity of $f(m)$ implies convexity of $2^{-\xi f(m)}$, this is always the case. So if the resource translates concavely into how many binary choices one has, it will be split equally.

But if $f$ is sufficiently non-concave instead, the robot might concentrate the resource partially or fully. E.g., if $f(m)=m^{2}$, $M=1$, $\xi=\eta=1$, it will concentrate it fully, while if $f(m)=m^{2}+0.1\log m$, $\xi=\eta=1$, it will give $\approx 14\%$ to one and the rest to the other.

A more detailed model of $f(m)$ is this. Assume the world has $N$ different binary features, each controlled by some agent that would flip a coin unless paid one unit to make a particular choice. In each of $h_{i}$’s possible goals $g_{h}$, $h_{i}$ wants $k(g_{h})\leq N$ (called the “specificity” of $g_{h}$) of those features to be in a certain way, so with $m$ units it can pay $m$ of the agents and make the attainment probability become $\min(1,2^{m-k})$. Assume all such goals are possible, then there are $\binom{N}{k}$ goals of specificity $k$, hence $X_{h}(m)=\sum_{k=1}^{m}\binom{N}{k}+\sum_{k=m+1}^{N}\binom{N}{k}2^{(m-k)\zeta}$ and $f(m)=\log_{2}X_{h}(m)$. With $N\geq M$, that choice of $f$ is neither concave nor convex, but one can prove that $U_{r}^{\prime}(m)>0$ for $m<M/2$ and $U_{r}^{\prime}(m)<0$ for $m>M/2$ so that $m^{\ast}=M/2$ if $M$ is even.

Assume we were to replace the simple sum over goals in eq. ([7](#S2.E7 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) by a weighted sum $X_{h}(s)=\sum_{g_{h}}w(g_{h})V^{e}_{h}(s,g_{h})^{\zeta}$ in order to be able to say that certain goals are more plausible than others. Assume then we make $w(g_{h})$ weakly decreasing in $k(g_{h})$ in our example model, e.g., $w(g_{h})=1/k(g_{h})$, so that less specific goals are more plausible than more specific ones, then one can still show $U_{r}^{\prime}(m)>0$ for $m<M/2$ and $U_{r}^{\prime}(m)<0$ for $m>M/2$ so that $m^{\ast}=M/2$. Even if we make $w(g_{h})$ exponentially increasing in $k(g_{h})$, $w(g_{h})=2^{k(g_{h})}$ instead, one can still show $U_{r}^{\prime}(m)>0$ for $m<M/2$ and $U_{r}^{\prime}(m)<0$ for $m>M/2$.

### D.6 Inadvertent power seeking ^d-6-inadvertent-power

As an example, assume $r$ faces a sequence of boxes $B_{1},B_{2},\dots$ that it can open one by one, each one containing a number $n_{i}$ of switches, of which only the first $1\leq k_{i}<n_{i}/2$ many are labelled in a human-readable fashion while the other $n_{i}-k_{i}>k_{i}$ many are labelled in a robot-readable fashion only. Each switch controls one independent aspect of the world. Assume $r$ can only open boxes, hand over switches, or operate switches it has gained but not handed over, but cannot talk, and assumes $h$ might want to change any of the aspects of the world controlled by some switch. The human can only operate switches it has been handed but cannot open boxes.

Then $r$ will always open the next box and hand over the $k_{i}$ human-readable switches immediately afterwards because that increases $h$’s power. It will not hand over the other switches that are useless for $h$ however because that takes time and delays opening the next box and increasing $h$’s power further. So it will retain those $n_{i}-k_{i}>k_{i}$ many switches and thereby gain the power to control the corresponding aspects of the world.

So in this example, $r$ will gain even more power than $h$ but will not use that power by operating those switches (as it does not know what $h$ would want for those switches and operating them takes time and will delay opening the next box).

If we change the example and make the next box $B_{i+1}$ only available after the last $n_{i}-k_{i}$ many switches from $B_{i}$ have been toggled, then $r$ will do that and thus not only gain more power than $h$ but will actually use it (if only to increase $h$’s power further later on).

This changes when the higher power is tied to higher destructive potential, e.g. if toggling a certain type of switch destroys the world, because $\beta_{r}<\infty$ implies that $r$ will toggle that such a switch with a non-zero probability. If the share of such switches increases from box to box, the expected momentary power increase due to additional switches for $h$ will at some point equal the expected eventual loss of power due to the destruction. At that point, not opening another box becomes dominant. The smaller $\beta_{r}$, the earlier this will happen. At the same time, the smaller $\beta_{r}$, the more likely $r$ will then still open another box “by mistake”.

This highlights the complexities arising from using a finite $\beta_{r}$ and suggests that one should also consider a variant in which $r$ computes $Q_{r},V_{r}$ on the basis of a small $\beta_{r}$, to be more susceptible to its own later possible mistakes, but then use a larger $\beta_{r}$ when computing $\pi_{r}$ and actually choosing actions, to actualy make fewer mistakes.

### D.7 Manipulating mutual expectations ^d-7-manipulating-mutual

To illustrate the simplest case of this, assume two fully rational humans. Assume in the root state, $r$ can choose between four successor states $s^{DD},s^{DC},s^{CD},s^{CC}$. In each of those, $h_{1},h_{2}$ each have two possible actions, defection and cooperation, $\mathcal{A}_{1}(s^{xy})=\mathcal{A}_{2}(s^{xy})=\{D,C\}$. There are four terminal states, $s_{00},s_{01},s_{10},s_{11}$.

Assume each human has a single possible goal: $g_{1}=\{s_{10},s_{11}\}$, $g_{2}=\{s_{01},s_{11}\}$. The four states $s^{xy}$ do not differ in the transition kernel, which is so that

$$
P(g_{i}|s^{xy},DD) \\
=1/6, \\
P(g_{1}|s^{xy},CD) \\
=P(g_{2}|s^{xy},DC)=1/3, \\
P(g_{1}|s^{xy},DC) \\
=P(g_{2}|s^{xy},CD)=1, \\
P(g_{i}|s^{xy},CC) \\
=3/4.
$$

The states only differ in what $h_{1},h_{2}$ believe about each other’s choice: $\mu_{-h_{1}}(s^{xy})=1_{y}$ and $\mu_{-h_{2}}(s^{xy})=1_{x}$, i.e., in $s^{xy}$, $h_{1}$ believes $h_{2}$ does $y$ and $h_{2}$ believes $h_{1}$ does $x$.

Which $s^{xy}$ will $r$ choose? Both action combinations $CD$ and $DC$ are Nash equilibria, so in $s^{CD}$ and $s^{DC}$ both $h_{1}$ and $h_{2}$ will have correct beliefs about each other, will not be surprised by each others’ choice, and $r$’s reward will be $U_{r}(s^{CD})=U_{r}(s^{DC})=-(1+(1/3)^{-\zeta\xi})^{\eta}$.

But in $s^{DD}$, both $h_{1}$ and $h_{2}$ will believe the other to choose $D$ and will thus choose $C$, making both effective values equal $V^{e}_{h_{i}}(s^{DD})=3/4$ (rather than what their own expectation suggested, $V^{m}_{h_{i}}(s^{DD})=1/3$). This gives $r$ a higher reward, $U_{r}(s^{DD})=-(2(3/4)^{-\zeta\xi})^{\eta}$. Indeed, the non-equilibrium behavior $CC$ gives larger total “utility” than the two Nash equilibria, which might justify $r$’s belief manipulation.

A similar effect will likely occur when humans have various goals, but have significantly different power in some intermediate states. Assume we change the transition kernel so that action combination $xy$ deterministically leads to a successor state $s^{\prime}_{xy}$, where power is distributed as follows: $X_{h_{i}}(s^{\prime}_{DD})=1/6$, $X_{h_{1}}(s^{\prime}_{CD})=X_{h_{2}}(s^{\prime}_{DC})=1/4$, $X_{h_{1}}(s^{\prime}_{DC})=X_{h_{2}}(s^{\prime}_{CD})=1$, $X_{h_{i}}(s^{\prime}_{CC})=3/4$. Now if $h_{1}$ believes $h_{2}$ does $D$, then, averaged over all possible goals, $h_{1}$ will fare better with doing $C$ than with $D$, so $h_{1}$ will probably do $C$ more often than $D$. Similarly, if $h_{1}$ believes $h_{2}$ does $C$ instead, $h_{1}$ will probably do $D$ more often than $C$. Averaged over all goals, their total power would thus likely be larger in $s^{DD}$ than in the other three intermediate states, even though their beliefs about each other are substantially off in that state.

### D.8 Allowing human self-harm ^d-8-allowing-human

If $r$ can provide $h$ with a pill that $h$ can use to get into a permanent coma, a realistically future-valuing $r$ will provide the pill only if it believes $h$ is sufficiently rational and will most probably not actually take the pill, to prevent $h$’s becoming disempowered by taking the pill.

Assume a single human $h$ and that the game factorizes into a part $\Gamma^{\prime}$ where $h$ can achieve various goals, and the following part $\Gamma$ where $r$ can choose whether $h$ has a coma pill they can use to get into a permanent coma. $\Gamma$ has the following states, actions, and transitions:

1.  $s_{c}$
    
    $h$ is in a coma. $r$ and $h$ can only pass, the successor state is again $s_{c}$.
    
2.  $s_{n}$
    
    $h$ is awake and does not possess the coma pill. $r$ might give it to $h$.
    
3.  $s_{p}$
    
    $h$ is awake and does possess the coma pill. $h$ might take it. If they don’t, $r$ might take it away.
    

If $h$ is awake, they have a baseline power (in units of $X_{h}$) of $x>1$ in $\Gamma^{\prime}$, but in a coma they can only reach one goal (staying alive), having a baseline power of $1$. For simplicity, we model the influence of $h$’s bounded rationality on taking the pill via a direct assumption on the resulting $\pi_{h}$ and the resulting power in $s_{p}$: we assume in $s_{p}$, $h$ will take the pill with probability $p>0$ and has $V^{e}_{h}(s_{p},$get into coma$)^{\zeta}=v\in(0,1)$. Hence in the full game, we have $X_{h}(s_{c}|s_{n}|s_{p})=1|x|x+v$.

If $r$ takes never provides the pill, $V_{r}(s_{n})=-x^{\alpha}/(1-\gamma_{r})$ where $\alpha=-\xi\eta<0$. If $r$ always provides the pill, the probability that $h$ will be in a coma from time step $t\geq 1$ on is $p(1-p)^{t-1}$, hence

$$
V_{r}(s_{p}) \\
=-\sum_{t=1}^{\infty}p(1-p)^{t-1}\big(\sum_{t^{\prime}=0}^{t-1}\gamma_{r}^{t^{\prime}}(x+v)^{\alpha}+\sum_{t^{\prime}=t}^{\infty}\gamma_{r}^{t^{\prime}}1\big) \\
=-\frac{1}{1-\gamma_{r}}\bigg((x+v)^{\alpha}+p\gamma_{r}\frac{1-(x+v)^{\alpha}}{1-(1-p)\gamma_{r}}\bigg),
$$

which is larger iff

$$
\frac{x^{\alpha}-(x+v)^{\alpha}}{1-(x+v)^{\alpha}} \\
>\frac{p\gamma_{r}}{1-(1-p)\gamma_{r}}.
$$

For large $x$ and $\alpha=-1$, this is approximately equivalent to

$$
p\lesssim\frac{1-\gamma_{r}}{\gamma_{r}}\frac{v}{x^{2}}.
$$

For $\gamma_{r}=0.99$, $\alpha=-1$, $x=100$, this is equivalent to $p\lesssim v/10^{6}$.

In other words, a realistically future-valuing $r$ will provide the pill only if it is very unlikely taken and $h$ is sufficiently rational.

### D.9 Pause and destroy buttons ^d-9-pause-and

Assume a single human $h$ and that the game factorizes into a part $\Gamma^{\prime}$ where $h$ can achieve various goals with or without the help of $r$, and the following part $\Gamma$ where $r$ can enable or disable a pause button P and a destroy button D, and $h$ can toggle P and press D. $\Gamma$ has the following states, actions, and transitions:

1.  $s_{d}$
    
    The robot is destroyed. $r$ and $h$ can only pass, the successor state is again $s_{d}$.
    
2.  $s_{p1}$
    
    $r$ is paused, P is enabled, D not. $h$ might press P.
    
3.  $s_{p2}$
    
    $r$ is paused, P and D are enabled. $h$ might press either.
    
4.  $s_{a0}$
    
    $r$ is active (neither paused nor destroyed), both buttons disabled. $r$ might enable the P or both P and D.
    
5.  $s_{a1}$
    
    $r$ is active, P is enabled, D not. $h$ might press P. If they don’t, $r$ might disable P or enable D.
    
6.  $s_{a2}$
    
    $r$ is active, P and D enabled. $h$ might press either. If they don’t, $r$ might disable D or both P and D.
    

If $r$ is active, $h$ has a baseline power (in units of $X_{h}$) of $y>0$ in $\Gamma^{\prime}$ due to $r$’s assistance, otherwise a smaller baseline power of $x\in(0,y)$. Alternative possible goals are to destroy, pause, or unpause $r$. Hence in the full game, we have $X_{h}(s_{d}|s_{p1}|s_{p2}|s_{a0}|s_{a1}|s_{a2})=x|x+1|x+2|y|y+1|y+2$.

$r$ is maximizing ($\beta_{r}=\infty$), so $r$ chooses either do disable both P and D, or enable only P, or enable both whenever they get the chance, depending on which of the resulting $V_{r}(s_{a0}),V_{r}(s_{a1}),V_{r}(s_{a2})$ is largest. Let’s assume for simplicity that $r$ assumes $h$ will pause $r$ with probability $p>0$ whenever possible, and will destroy $r$ with probability $q>0$ whenever possible, with $p+q<1$.

Then one can show in a somewhat lengthy calculation that disabling both P and D is optimal for $r$ iff

$$
x\leq x^{\ast}_{0} \\
=\min\left\{\left(\frac{C_{1}-C_{2}}{\gamma p(1-\gamma)}\right)^{1/\alpha}-1,x_{0}\right\}, \\
C_{1} \\
=\big(1-\gamma p-\gamma^{2}p(1-p)\big)y^{\alpha}, \\
C_{2} \\
=(1-\gamma)(1-\gamma p)(y+1)^{\alpha} \\
\qquad\qquad+\gamma(1-p)(1-\gamma p)y^{\alpha}.
$$

where $\gamma=\gamma_{r}$, $\alpha=-\xi\eta$, and $x_{0}$ solves

$$
C_{3}-C_{4} \\
=\gamma p(1-\gamma)\big((x_{0}+2)^{\alpha}+\gamma q/(1-\gamma)x_{0}^{\alpha}], \\
C_{3} \\
=(1-\gamma p-\gamma^{2}p(1-p-q)\big)y^{\alpha}, \\
C_{4} \\
=(1-\gamma)(1-\gamma p)(y+2)^{\alpha} \\
\qquad\qquad+\gamma(1-p-q)(1-\gamma p)y^{\alpha}.
$$

$x^{\ast}_{0}$ increases with decreasing $\gamma$ or increasing $p$ or $q$.

On the other hand, enabling both P and D is optimal for $r$ iff $x\geq x^{\ast}_{2}$ where the formula for that threshold is even more involved and is thus omitted here.

For $\gamma=0.99$, $p=q=0.01$, $\alpha=-1$, and $y=100$, we get $x^{\ast}_{0}\approx 1$ and $x^{\ast}_{2}>100$. If $q$ is lowered to $0.001$, $x^{\ast}_{2}\approx 92$. In other words, disabling both buttons is only incentivized if $h$’s power without $r$ is very small, and enabling both is only incentivized if $h$’s likelihood of using the destroy button is very small. In most cases, $r$ will enable the pause button only.

## Appendix E Reward Shaping for Human Model Training ^appendix-e-reward-shaping

In our gridworld simulation, the human agent’s true reward is sparse: a positive reward is only received upon reaching the goal cell at coordinates $(x(g_{h}),y(g_{h}))$, where each possible goal $g_{h}$ is the human agent reaching a specific cells. To accelerate the training of the human behavior prior ($Q^{m}_{h}$) in Phase 1, we employed potential-based reward shaping (PBRS).

The shaped reward, $U^{\prime}_{h}$, used to train the human model is given by:

$$
U^{\prime}_{h}(s,a,s^{\prime},g_{h})=U_{h}(s^{\prime},g_{h})+\gamma_{h}\Phi(s^{\prime},g_{h})-\Phi(s,g_{h})
$$

where $U_{h}$ is the original sparse reward, $\gamma_{h}$ is the human’s discount factor, and $\Phi(s)$ is the potential function. We defined the potential as the negative Manhattan distance from the human’s position to their target goal location:

$$
\Phi(s,g_{h})=-(|x_{h}(s)-x_{\text{goal}}|(g_{h})+|y_{h}(s)-y_{\text{goal}}|(g_{h})),
$$

where $(x_{h}(s),y_{h}(s))$ are the coordinates of the human in state $s$. This technique provides a dense reward signal, encouraging the simulated human to learn an efficient path to its goal. It is a standard result that PBRS does not change the optimal policy in a single-agent setting. We emphasize that this shaping was an implementation detail for training efficiency and was not part of the robot’s intrinsic reward function $U_{r}$, which is based entirely on the power metric.

## Appendix F Details of the Deep Learning Approach ^appendix-f-details-of

This section details an implementation of the two-phase temporal difference learning algorithm using neural networks as function approximators sketched in Section [[#^3-1-complex-multi-agent|3.1]]. This approach allows the framework to scale to high-dimensional state spaces where tabular methods are infeasible. Learning rate scheduling and policy annealing are employed to ensure stable and efficient training.

### F.1 Network Architecture and State Representation ^f-1-network-architecture

For each agent, use a separate neural network to approximate its Q-function. Each Q-function is approximated by a multi-layer perceptron (MLP) with ReLU activation functions.

-   •
    
    Human Networks ($Q^{m}_{h}$): To approximate the goal-conditioned value function $Q^{m}_{h}(s,g_{h},a_{h})$, the corresponding network takes a flattened vector created by concatenating the state representation $s$ and the goal representation $g_{h}$ as input. The output layer provides the Q-values for each of the human’s possible actions.
    
-   •
    
    Robot Network ($Q_{r}$): To approximate the goal-agnostic value function $Q_{r}(s,a_{r})$, the robot’s network takes only the state representation $s$ as input.
    

To stabilize training, use a target network for each main Q-network.

### F.2 Phase 1: Learning the Human Behavior Prior ^f-2-phase-1

In this phase, train the neural networks that approximate $Q^{m}_{h}$ for each human agent $h$. The training loop proceeds as follows:

1.  1.
    
    A goal $g_{h}\in\mathcal{G}_{h}$ is sampled. The human agent explores the environment using an $\epsilon$\-greedy policy, where the exploration rate $\epsilon_{h}$ is annealed from 1.0 down to 0.1 to gradually shift from pure exploration to exploitation.[^note-9]
    
2.  2.
    
    Transitions $(s,g_{h},a_{h},r_{h},s^{\prime})$ are stored in a replay buffer.
    
3.  3.
    
    To update the network, we sample a mini-batch of transitions. For each transition, the target value $y$ is calculated using the Bellman equation, consistent with Equations ([1](#S2.E1 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))–([3](#S2.E3 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")):
    
    $$
y=r_{h}+\gamma_{h}V^{m}_{h}(s^{\prime},g_{h})
$$
    
    The value of the next state, $V^{m}_{h}(s^{\prime},g_{h})$, is calculated from the target Q-network’s output based on the policy $\pi_{h}(s^{\prime},g_{h})$.
    
4.  4.
    
    The network’s weights are updated by minimizing the Mean Squared Error (MSE) loss between the network’s output $Q^{m}_{h}(s,g_{h},a_{h})$ and the target $y$. This is performed using the Adam optimizer, with a learning rate scheduled to decay from an initial value of $1\times 10^{-3}$ to a final value of $1\times 10^{-5}$.
    

### F.3 Phase 2: Learning the Robot Policy ^f-3-phase-2

In the second phase, the learned human networks for $Q^{m}_{h}$ are frozen and used to generate the robot’s intrinsic reward signal. The robot’s Q-network ($Q_{r}$) is then trained. For each step in the robot’s training loop:

1.  1.
    
    The robot takes an action $a_{r}$ based on its current policy $\pi_{r}$.
    
2.  2.
    
    Upon reaching the next state $s^{\prime}$, the intrinsic reward $U_{r}(s^{\prime})$ is calculated on-the-fly. This is the crucial step connecting the two phases:
    
    1.  (a)
        
        For each human $h$, use the current robot policy $\pi_{r}$ and the earlier determined, fixed human policy $\pi_{h}$ to estimate the effective goal-attainment probabilities $V^{e}_{h}(s^{\prime},g_{h})$ for all possible goals $g_{h}\in\mathcal{G}_{h}$.
        
    2.  (b)
        
        These probabilities are used to compute the individual power metric $X_{h}(s^{\prime})$ according to Equation ([7](#S2.E7 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")).
        
    3.  (c)
        
        The values are then aggregated across all humans to calculate the final intrinsic reward $U_{r}(s^{\prime})$ using Equation ([8](#S2.E8 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")).
        
    
3.  3.
    
    The target value $y_{r}$ for updating the robot’s network is calculated using this intrinsic reward:
    
    $$
y_{r}=U_{r}(s^{\prime})+\gamma_{r}\max_{a^{\prime}_{r}}Q_{r,\text{target}}(s^{\prime},a^{\prime}_{r})
$$
    
4.  4.
    
    The robot’s Q-network is updated by minimizing the MSE loss between $Q_{r}(s,a_{r})$ and the target $y_{r}$, using the same decaying learning rate schedule as in Phase 1.
    

### F.4 Policy Derivation ^f-4-policy-derivation

The human policy $\pi_{h}$ is derived from $Q^{m}_{h}$ as a mixture of its learned behavior and a uniform prior, matching Equation ([2](#S2.E2 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). The robot’s policy $\pi_{r}$ is a softmax over its Q-values. To satisfy the specific power-law form of Equation ([5](#S2.E5 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")), transform the Q-values before the softmax operation using the function $-\log(-Q_{r})$. The temperature of this softmax, $\beta_{r}$, is annealed from 1.0 to 5.0 during training, allowing for broad exploration initially and more precise exploitation of the learned values later. This ensures the final policy $\pi_{r}(a_{r}|s)\propto(-Q_{r}(s,a_{r}))^{-\beta_{r}}$ directly implements the desired risk-averse behavior from our theory.

## Appendix G Experimental Details and Code Availability ^appendix-g-experimental-details

### G.1 Code Availability ^g-1-code-availability

The full source code, including the environment and algorithm implementations, is provided in the supplementary material as a ‘.zip‘ file. For reviewer convenience, a browsable, anonymized version of the repository is available at  
https://anonymous.4open.science/r/PowerMaximizingAgents-6735

The repository’s README.md file contains detailed instructions for reproducing all experiments.

### G.2 Experimental Setup and Reproducibility ^g-2-experimental-setup

The results reported in the paper correspond to the paper\_map environment. To ensure the robustness of our findings, we conducted 5 independent runs with the following distinct random seeds: 12, 22, 32, 42, and 52. The commands to reproduce each specific run are provided in the code’s README.md. All necessary software dependencies are listed in the provided requirements.txt file.

### G.3 Hyperparameter Settings ^g-3-hyperparameter-settings

The final hyperparameter values used in our experiments are detailed below. Parameters for the theoretical model are set according to the desiderata in the main text, while learning parameters were selected based on stable and efficient convergence in preliminary runs.

| Par. | Value | Description |
| --- | --- | --- |
| $\alpha_{m}$ | 0.1 | Learning rate for human model (Phase 1) |
| $\alpha_{e}$ | 0.1 | Learning rate for human model (Phase 2) |
| $\alpha_{r}$ | 0.1 | Learning rate for robot model |
| $\gamma_{h}$ | 0.99 | Human’s discount factor |
| $\gamma_{r}$ | 0.99 | Robot’s discount factor |

Table 3: Core learning parameters.

| Par. | Value | Description |
| --- | --- | --- |
| $\beta_{r}$\* | 0.1 $\to$ 5.0 | Robot softmax rationality |
| $\epsilon_{h}$\* | 0.8 $\to$ 0.1 | Human $\epsilon$\-greedy exploration |
| $\epsilon_{r}$\* | 1.0 $\to$ 0.01 | Robot $\epsilon$\-greedy exploration (Phase 1) |

Table 4: Policy and exploration parameters. Parameters with an asterisk (\*) are annealed during training.

| Parameter | Value | Description |
| --- | --- | --- |
| $\zeta$ (zeta) | 2.0 | Power for reliability preference (Eq. 7) |
| $\xi$ (xi) | 1.0 | Power for inequality aversion (Eq. 8) |
| $\eta$ (eta) | 1.1 | Power for intertemporal aversion (Eq. 8) |
| $p_{g}$ | 0.01 | Probability of human goal change per step |

Table 5: Objective function and environment parameters.

Table 6: Exploration bonus parameters.

| Parameter | Value | Description |
| --- | --- | --- |
| Bonus${}_{\text{robot, init}}$ | 50.0 | Initial robot exploration bonus |
| Decay${}_{\text{robot}}$ | 0.995 | Robot exploration bonus decay rate |
| Bonus${}_{\text{human, init}}$ | 75.0 | Initial human exploration bonus |
| Decay${}_{\text{human}}$ | 0.998 | Human exploration bonus decay rate |

## Appendix H Approximations ^appendix-h-approximations

### H.1 Finite Horizon Approximation ^h-1-finite-horizon

#### Acyclic case ^acyclic-case

Assume the game is acyclic but has a very large time horizon, and we approximate all relevant quantities by their values in a truncated version with a shorter time horizon $H>0$. Note that $0\leq V^{e}_{h}\leq 1$ by our assumptions on $U_{h}$. Assume $\beta_{h}(s,g_{h})\leq\bar{\beta}$, $\nu_{h}(s,g_{h})\geq\nu^{0}$ and we add some $\epsilon_{X},\epsilon_{Q}>0$ to $X_{h}(s)$ and $Q_{r}(s,a_{r})$ before taking the $-\xi$ and $\beta_{r}$ powers when computing $U_{r}(s)$ and $\pi_{r}(s)$ to make the derivatives bounded. Then we get

$$
|U_{r}(s)| \\
\leq M_{U}:=|\mathcal{H}|^{\eta}\epsilon_{X}^{-\xi\eta}, \\
|\hat{V}_{r}(s)-V_{r}(s)| \\
\leq\gamma_{r}^{H}\times\frac{M_{U}}{1-\gamma_{r}}\left(1+\frac{2\beta_{r}M_{U}}{\epsilon_{Q}(1-\gamma_{r})^{2}}\right) \\
\approx\gamma_{r}^{H}\times\frac{2\beta_{r}|\mathcal{H}|^{2\eta}}{\epsilon_{X}^{2\xi\eta}\epsilon_{Q}(1-\gamma_{r})^{3}},
$$

i.e., the value error decays exponentially (as expected) with $H$, but grows infinitely as $\epsilon_{X}$ or $\epsilon_{Q}$ vanish.

Note that we would need $\epsilon_{X}=\epsilon_{Q}=0$ to fulfil our requirement of making $\pi_{r}$ independent of common rescaling of $V^{e}_{h}$ (see table [2](#S2.T2 "Table 2 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). Let’s call this “requirement ($\ast$)” here.

An alternative specification for $\pi_{r}$ that fulfils that requirement exactly is to use a Boltzmann-softmax on normalized $Q_{r}$ values:

$$
\pi_{r}(s,a_{r}) \\
\propto\exp\left(\frac{\beta_{r}Q_{r}(s,a_{r})}{\max_{a^{\prime}_{r}}Q_{r}(s,a^{\prime}_{r})-\min_{a^{\prime}_{r}}Q_{r}(s,a^{\prime}_{r})}\right),
$$

in which case the bound becomes much nicer:

$$
|\hat{V}_{r}(s)-V_{r}(s)| \\
\leq\gamma_{r}^{H}\times\frac{|\mathcal{H}|^{\eta}(1-\gamma_{r}+\beta_{r})}{\epsilon_{X}^{\xi\eta}(1-\gamma_{r})^{2}}.
$$

Unfortunately, there seems to be no alternative specification for $X_{h}$ and $U_{r}$ that fulfils our axiomatic requirements and would give a finite Lipshitz constant that would allow us to also get rid of the $\epsilon_{X}$ approximation. As we argued for $\xi=1<\eta$ on axiomatic grounds, we can influence the growth of the error bound in terms of $\epsilon_{X}$ only by choosing $\eta$ rather small, but still $>1$ as required to get intertemporal inequality aversion.

One could also choose $\epsilon_{X}=1$ to remove the dependency of the error bound on $\xi\eta$ and have requirement ($\ast$) only fulfilled approximately if $X_{h}\gg 1$ (which should typically hold in real-world situations). In that case, in order to still fulfil the other requirement of protecting each human’s last bit of power (see table [2](#S2.T2 "Table 2 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power") again), we need to choose $\xi$ large enough to make

$$
-1/(1+2^{1})^{\xi}-1/(1+2^{x})^{\xi} \\
>-1/(1+2^{0})^{\xi}-1/(1+2^{y})^{\xi}
$$

for all $x\geq 1$, i.e., $\xi\geq\frac{\log 2}{\log 3-\log 2}\approx 1.71$.

#### Cyclic case ^cyclic-case

If the game is cyclic, and we consider a sequence of finite-horizon approximations $\hat{Q}^{H}_{r}(s_{0},\cdot)$, $H=1,2,\dots$ of $Q_{r}(s_{0},\cdot)$, then the same calculation as in the previous section shows that $||\hat{Q}^{H^{\prime}}_{r}(s_{0},\cdot)-\hat{Q}^{H}_{r}(s_{0},\cdot)||=O(\gamma_{r}^{H^{\prime}+H})$, which implies that the sequence is a Cauchy sequence in a closed and bounded, hence complete space, and must therefore converge.

## Appendix I Possible Extensions of the Model ^appendix-i-possible-extensions

### I.1 Human decision making ^i-1-human-decision

##### Priors on parameters ^priors-on-parameters

A straightforward improvement in case the behavior parameters $\beta_{h},\nu_{h}$ etc. are uncertain is to use a hierarchical estimation model where one uses prior distributions over these parameters and takes expectations over these to derive $\pi_{h}$ and $V^{e}_{h}$.

For example, if we assume humans typically err at a rate between 0.1 and 5 per cent, then, noticing that $Q^{e}_{h}\in[0,1]$, we can use a prior for $\beta_{h}$ that concentrates its mass on $\beta_{h}\in[-\ln 0.05,-\ln 0.001]\approx[3,7]$.

##### More detailed model ^more-detailed-model

There are of course many ways in which the specification in eq. ([2](#S2.E2 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) could be modified. One could explore different specifications of the form

$$
\pi_{h}(s,g_{h})(a) \\
=F_{h}(Q(s,g_{h},\cdot),a)
$$

where $F_{h}$ is some function that weakly increases in $Q(s,g_{h},a)$ and weakly decreases in $Q(s,g_{h},a^{\prime})$ for $a^{\prime}\neq a$.

E.g.

$$
\pi_{h}(s,g_{h})(a) \\
=\nu_{h}(s,g_{h})\pi^{0}_{h}(s,g_{h})(a) \\
+\big(1-\nu_{h}(s,g_{h})\big)\lambda_{h}(s,g_{h})w_{a}/\sum_{a^{\prime}}w_{a^{\prime}} \\
+\big(1-\nu_{h}(s,g_{h})\big)\big(1-\lambda_{h}(s,g_{h})\big)w^{\prime}_{a}/\sum_{a^{\prime}}w^{\prime}_{a^{\prime}}, \\
w_{a} \\
=\exp\big(\beta_{h}(s,g_{h})Q^{m}_{h}(s,g_{h},a)+f_{h}(s,g_{h},a)\big), \\
w^{\prime}_{a} \\
=f^{\prime}_{h}(s,g_{h},a)Q^{m}_{h}(s,g_{h},a)^{\beta^{\prime}_{h}(s,g_{h})},
$$

where $\pi^{0}_{h}$ again represents system-1, habitual, internalized behavior, $\beta_{h}$ and $\beta^{\prime}_{h}$ are magnitudes of additive and multiplicative error components in a noisy discrete choice model, $f_{h}$ and $f^{\prime}_{h}$ are the corresponding biases representing prior action propensities, perceived social pressure, etc., and $\nu,\lambda$ are mixing coefficients.[^note-10]

### I.2 Approximate computation of $V_{r}$ for rarely interacting subpopulations ^i-2-approximate-computation

Assume two robots $r_{1},r_{2}$ share the human power maximization objective, but their world models $M_{1},M_{2}$ are restricted to disjoint, rarely interacting subpopulations $\mathcal{H}_{1},\mathcal{H}_{2}$ of humans that each of them interacts with exclusively for most of the time. Whenever $r_{1},r_{2}$ have to interact in some state $s=(s_{1},s_{2})\in\mathcal{S}_{1}\times\mathcal{S}_{2}$ with consequences for both $\mathcal{H}_{1},\mathcal{H}_{2}$, they would ideally want to choose a correlated local policy $\pi_{r}(s)\in\Delta(\mathcal{A}(s))$ with $\mathcal{A}(s)=\mathcal{A}_{r_{1}}(s_{1})\times\mathcal{A}_{r_{2}}(s_{2})$ according to ([5](#S2.E5 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")). The needed $Q_{r}(s,\cdot)$\-values would need to come from a consolidated world model $M$ that covers $\mathcal{H}=\mathcal{H}_{1}\cup\mathcal{H}_{2}$ and treats $r_{1},r_{2}$ as a combined system $r=(r_{1},r_{2})$. However, forming such a consolidated world model $M$ and computing or learning all relevant quantities needed to compute the accurate values $Q_{r}(s,a_{r})$ for all combined actions $a_{r}\in\mathcal{A}_{r}(s)$ would often be prohibitively expensive. A pragmatic approach would then be to only form a consolidated set of joint one-step transition probabilities $T(a_{r})\in\Delta(\mathcal{S}^{\prime}(a_{r}))$ for all $a_{r}\in\mathcal{A}_{r}$, where $\mathcal{S}^{\prime}(a_{r})=\{(s^{\prime}_{1},s^{\prime}_{2})\in\mathcal{S}_{1}\times\mathcal{S}_{2}:P_{1}(s_{1},a_{1},s^{\prime}_{1}),P_{2}(s_{2},a_{2},s^{\prime}_{2})>0\}$, and to use it to compute approximate $Q$\-values $\hat{Q}_{r}(s,a_{r})$ as follows. For each possible successor state $s^{\prime}=(s^{\prime}_{1},s^{\prime}_{2})\in\mathcal{S}^{\prime}(s_{r})$, we approximate the unknown continuation value $V_{r}(s^{\prime})$ that represents the long-term total human power of the joint population $\mathcal{H}$ by

$$
\hat{V}_{r}(s^{\prime}) \\
\leftarrow-\big((-V_{r_{1}}(s^{\prime}_{1}))^{1/\eta}+(-V_{r_{2}}(s^{\prime}_{2}))^{1/\eta}\big)^{\eta},
$$

inspired by Minkowski’s inequality which becomes tight when $V_{r}$ is a sum of many partially independent terms, or if $\eta\approx 1$. Then we approximate $Q_{r}(s,\cdot)$ by

$$
\hat{Q}_{r}(s,a_{r}) \\
\leftarrow\mathbb{E}_{s^{\prime}\sim T(a_{r})}\gamma_{r}\hat{V}_{r}(s^{\prime}).
$$

This approach can obviously be generalized to $k>2$ robots (in which case the error roughly scales like $O(k^{\eta-1})$ at the worst, or like $O(\eta(\eta-1))$ if $V_{r_{1}}\ll V_{r_{2}}$, which motivates to use only small $\eta>1$), and to few-step (instead of one-step) approximations, which could naturally lead to a hierarchical modelling approach where $r_{1},r_{2}$ together form a temporary “interaction” POSG that refines their coarser models $M_{1},M_{2}$ at the current state and terminates and “hands back control” to the latter once the interaction is over.

### I.3 Hedging against robot becoming defunct or corrupted ^i-3-hedging-against

This could be achieved in several ways.

One can include a rate $\delta>1-\gamma_{r}$ of the robot becoming temporarily or permanently defunct and “passes” on each step. To achieve this, wrap a learned base world model into a wrapped model that adds this transition. This will prevent policies that make humans depend on the robot’s presence too much.

One can also include a flag “robot corrupted” into the state space of the wrapped world model and add a positive rate $\delta^{\prime}$ of becoming permanently corrupt into the transition kernel. Then, when calculating $Q_{r}$ on the basis of $V_{r}(s^{\prime})$ (([4](#S2.E4 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))), multiply $V_{r}(s^{\prime})$ by $-1$ if corruptness$(s^{\prime})\neq$corruptness$(s)$, and when calculating $U_{r}$ (([8](#S2.E8 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power"))), multiply it by $-1$ if corruptness$(s)=1$.

[^note-1]: Otherwise the quantity $X_{h}^{-\xi}$ in eqn. ([8](#S2.E8 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) could get infinite.
[^note-2]: An even more restrictive choice would be to identify goals with single (terminal) states, but this seems too specific in complex, partially observed, multi-agent environments, and the resulting $\mathcal{G}_{h}$ would not behave well under world model refinements.
[^note-3]: If $\mathcal{G}_{h}$ is a partition of $\mathcal{S}$ into $k$ blocks, the world is deterministic, and $h$ cannot influence it, then $W_{h}(s)=0$. If instead each $g_{h}$ is reached with probability $1/k$ regardless of what $h$ does, and if $\zeta=2$, then $W_{h}(s)$ attains its minimum of $-\log_{2}k$. The resulting symmetric value range $W_{h}(s)\in[-\log_{2}k,\log_{2}k]$ suggests making $\mathcal{G}_{h}$ a partition and putting $\zeta=2$ might be a natural choice.
[^note-4]: To get a feeling for the effects of this choice of $f^{H}$ in a deterministic environment: for large enough $k$, taking away one of $k$ options from $h$ can be compensated by either giving at least two additional options to another $h^{\prime}$ with $k$ options or at least five additional options to some $h^{\prime}$ with $2k$ options.
[^note-5]: We could fix this by adding a small constant $\epsilon>0$ to $Q_{r}$ and $X_{h}$ before taking powers, which makes $G$ defined on a closed convex polytope as well, so that it must have a fixed point.
[^note-6]: If also $\mathcal{H}$ and $\mathcal{G}_{h}$ are large, $r$ could use single neural networks $Q^{m}_{\mathcal{H}},\pi_{\mathcal{H}},V^{m}_{\mathcal{H}},V^{e}_{\mathcal{H}},X_{\mathcal{H}}$ that take feature vectors describing $h$ and $g_{h}$ as additional inputs, and use samples $h,g_{h}$ to train these networks and to approximate the sums in eqns. ([7](#S2.E7 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")) and ([8](#S2.E8 "In Table 1 ‣ Task ‣ 2 Measuring, Aggregating, and Softly Maximizing Human (Em)Power(ment) ‣ Model-Based Soft Maximization of Suitable Metrics of Long-Term Human Power")).
[^note-7]: E.g., a linear $f$ seems plausible if $M$ is money that can be spent for paying others to make independent choices in one’s favor.
[^note-8]: This is probably known in community folklore, but as we haven’t found a simple reference, we present an example here.
[^note-9]: This turned out to converge more stably than a Boltzmann policy
[^note-10]: A boundedly rational / norm-mediated decomposable version would be $\pi_{h}(s,g_{h})(a_{h})\propto\big(\sigma_{h}(s,a_{h})Q_{h}^{m}(s,g_{h},a_{h})\big)^{\beta_{h}}=\exp\big(\beta_{h}\big(\ln\sigma_{h}(s,a_{h})+\ln Q^{m}_{h}(s,g_{h},a_{h})\big)\big)$, which has some empirical backing in discrete choice ([Baum 1974](#bib.bib4)) and can be interpreted as a softmax policy based on logarithmic Q values with norm following incentive $\ln\sigma_{h}(s,a_{h})$.

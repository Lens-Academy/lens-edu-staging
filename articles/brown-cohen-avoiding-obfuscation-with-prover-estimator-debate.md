---
title: "Avoiding Obfuscation with Prover-Estimator Debate"
author:
  - "Jonah Brown-Cohen"
  - "Geoffrey Irving"
  - "Georgios Piliouras"
  - "Lijie Chen"
  - "Jiawei Li"
  - "Zhiyang Xun"
source_url: "https://arxiv.org/pdf/2506.13609"
published: 2025-06-16
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Abstract ^abstract

Training powerful AI systems to exhibit desired behaviors hinges on the ability to provide accurate human supervision on increasingly complex tasks. A promising approach to this problem is to amplify human judgement by leveraging the power of two competing AIs in a debate about the correct solution to a given problem. Prior theoretical work has provided a complexity-theoretic formalization of AI debate, and posed the problem of designing protocols for AI debate that guarantee the correctness of human judgements for as complex a class of problems as possible. Recursive debates, in which debaters decompose a complex problem into simpler subproblems, hold promise for growing the class of problems that can be accurately judged in a debate. However, existing protocols for recursive debate run into the _obfuscated arguments problem_: a dishonest debater can use a computationally efficient strategy that forces an honest opponent to solve a computationally intractable problem to win. We mitigate this problem with a new recursive debate protocol that, under certain stability assumptions, ensures that an honest debater can win with a strategy requiring computational efficiency comparable to their opponent.

The original recursive debate protocol suffered from the _obfuscated arguments problem_: debater $A$ could decompose an easy question $x$ into hard subclaims $y_1, y_2, \ldots, y_q$, and debater $B$ would fail to find the flaw even if he knew one existed. In prover-estimator debate, $B$ assigns probabilities to subclaims and $A$ chooses a probability to claim that $B$ is wrong in a specific direction. Since $A$ must point to a flaw in $B$’s probabilities, $B$ wins if neither player can locate a flaw.

## Introduction ^introduction

Modern machine learning (ML) is fundamentally driven by, and further enables, fast and complex computations. We leverage AI precisely because it allows us to automate and optimize tasks with an efficiency that surpasses human capabilities. This rapid computation, permeating increasingly high-complexity and intelligence tasks, is the engine of progress in countless domains. However, this very strength creates a fundamental tension: the speed and complexity of these computations make exhaustive inspection impossible. Understanding and verifying the internal workings of these powerful AI systems—what’s going on “behind the scenes”—becomes increasingly intractable. This tension directly leads to the critical problem of _scalable oversight_: how to provide accurate training supervision, such that these powerful, yet opaque, AI systems behave as intended, even when their tasks are too complex for direct human understanding and verification?

Ensuring the reliable and safe operation of advanced AI systems is a central challenge for the field. The potential for unintended consequences arising from misaligned or poorly understood AI behavior requires the development of robust oversight mechanisms in order to provide a training reward signal that accurately reflects human values and intentions. Effective scalable oversight is not merely a desirable feature; it is a foundational requirement for building trustworthy AI that aligns with human intentions and avoids producing systematically undesirable outcomes. Progress in this area is crucial for realizing the full potential of AI while mitigating potential risks.

Various approaches to scalable oversight have been proposed, including amplification \[christiano2018supervising\], recursive reward modeling \[leike2018scalable\], and AI debate \[irving2018ai\]. All of these approaches are based on the intuition that it is possible to amplify the reward signal coming from human judgment by leveraging improving AI capabilities. For the case of AI debate, \[irving2018ai\] formalized this intuition in the language of computational complexity theory: they proved that a computationally limited human can accurately judge the correct solution to problems of much larger computational complexity by observing a specifically structured debate between two computationally powerful AIs. The main idea is that the two powerful AI debaters recursively break down a complex problem into simpler sub-problems, eventually terminating in subproblems that are simple enough for the computationally limited human to judge directly.

As an example, consider the case of training a software-engineering AI system to produce large, complex pull requests. Rather than have a human expert carefully review each pull request during training, one could train the AI system via debate, where the first debater produces the pull request, and the second debater acts as a code reviewer attempting to point out flaws in the produced code. For example, the code-reviewing debater might claim that a particular function returns an incorrect value on a certain input. The coding debater could defend their code by tracing through the function on that input and arguing that the correct value is returned. The code-reviewing debater might then zero-in on a single step of the trace calling a library function, and claim that the library function does not behave as the coding debater has claimed. The coding debater might appeal to the library’s documentation to justify their claim, and the code-reviewing debater might respond by claiming that the version of the library in the production environment differs from that documentation. At this point, a human judge can quickly check which of the two debaters is correct about the production library version, without having to read and fully understand the complex pull request. Hence, the human judge only has to understand a specific, narrow claim about one piece of the code to provide an accurate reward signal.

However, a significant vulnerability exists in many recursive approaches, including recursive debate: the _obfuscated arguments problem_ \[barnes2020obfuscated\]. In recursive debate, a dishonest debater can _strategically_ decompose an easy problem into difficult, even intractable, subproblems. This renders an honest debater unable to find a flaw in their opponent’s argument even if both debaters know that a flaw exists somewhere. The debate will thus fail to identify the correct answer. Obfuscation in recursive debate is not merely a theoretical concern; it emerged naturally in prior empirical work \[barnes2020obfuscated\], suggesting obfuscation is a likely _attractor state_ in some settings.

\[brown-cohen24scalable\] avoid the issue of obfuscation in debate by doing away with recursion entirely. In this case, an efficient honest debater can always win, but debaters are required to write-out the full human-judgeable argument for the correctness of their claims. To return to the software engineering example, this would mean that the coding debater has to provide complete, detailed documentation of how and why every single piece of the code works, such that any plausible critique by the code-reviewing debater is already answered by the documentation. This is a significant sacrifice relative to recursive debate, which allows the debaters to efficiently and adaptively zoom-in on a small fraction of the full, detailed human-judgeable argument.

##### Our Approach. ^our-approach

We introduce _prover-estimator debate_, a protocol for AI debate that mitigates the obfuscated arguments problem while retaining the efficiency of recursive debate. In prover-estimator debate, the prover (Alice) decomposes a problem into subclaims. The estimator (Bob) has the _sole_ task of assigning probabilities to the prover’s subclaims. The prover uses these probabilities to decide which subclaim to recursively debate further. This departs from previous debate protocols, where the opponent selects which subclaim to challenge. We show that Bob can always produce probabilities that are _indistinguishable from the truth by Alice_, while expending computational effort not too much greater than Alice. Alice cannot therefore (on average) select a subproblem where Bob is non-trivially wrong. However, prover-estimator debate has limitations. Alice’s task becomes harder because Bob can defeat an argument by assigning low probabilities to many subclaims. This rules out certain delicate, yet correct arguments that are highly sensitive to the probabilities assigned to subproblems. We formalize this condition by introducing a _stability_ requirement, _$\rho$\-stability_, which demands that the validity of arguments cannot hinge on arbitrarily small changes in subclaim probabilities[^note-2]. We require stability only for usefulness, not safety: even if stability does not hold, an honest estimator can still win against any incorrect argument by a dishonest prover.

To gain intuition for how prover-estimator debate works, let us return to the pull request example. Anyone who has undertaken code review knows that reading code and directly identifying bugs is a difficult task. However, it is often possible to estimate where bugs are likely to occur from the structure of the code, and then to request additional evidence in the form of tests that demonstrate the desired behavior. Prover-estimator debate in this setting requires Alice to provide reliable test coverage, so that even when Bob is uncertain that any single test provides sufficient evidence that the code is correct, taken together it is still likely that Alice’s code exhibits the desired behavior. On the other hand, if Alice has engaged in obfuscation by producing code that fails in a way neither Alice nor Bob can readily identify, then Bob can output low probabilities for Alice’s claims, and Alice will not be able to reliably identify any probability as being unreasonable.

##### Our Results. ^our-results

We provide rigorous theoretical guarantees demonstrating that prover-estimator debate, _combined with the stability requirement_, mitigates the obfuscated arguments problem. Specifically, under reasonable assumptions about the structure of the problems being debated (formalized as _recursively decomposable problems_ and the $\rho$\-stability condition), we show:

1.  **Completeness:** An honest prover, who correctly provides a stable decomposition into solvable subproblems, can always win the debate against any dishonest estimator.
    
2.  **Soundness:** An honest estimator can win on average against a dishonest prover, _even if stability is violated and the subproblems are obfuscated_, using computational effort comparable to their dishonest opponent.
    

The requirement that it is possible for the prover to provide a stable decomposition is the primary restriction on the class of problems that can be accurately judged by our protocol. That is, there can be problems where the prover can efficiently decompose the original problem into solvable subproblems, but all such efficient decompositions are unstable. In this case, our protocol errs on the side of safety, and rejects the prover’s argument. This is necessary for the protocol to succeed, because it cannot distinguish between true and false arguments made via unstable decompositions. Note that all that is required is that the prover is able to find a _single_ stable decomposition to use in the debate. Even if other, unstable decompositions exist, the prover will lose on average when using them, and thus will be incentivized via debate training to select the winning, stable decomposition. Intuitively, the stability condition can be seen as requiring that small changes to marginal probabilities of subclaims should not have large effects on the truth of the original claim. We argue that this is a natural requirement when dealing with fuzzy human judgments, where one should be fundamentally suspicious of arguments that depend very precisely on the composition of many inherently imprecise subclaims.

Prover-estimator debate provides a step towards building robust and trustworthy AI systems capable of tackling complex tasks beyond direct human oversight. Our formal notion of argument stability, in particular, clarifies the conditions required to avoid the obfuscated arguments problem and enables more targeted research on overcoming this problem. Our approach also suggests general lessons for designing future debate protocols, including the value of asymmetric debate protocols and explicit uncertainty estimates. This work opens up new avenues for research, both theoretical and empirical, in the pursuit of safe and aligned AI.

## Related work ^related-work

The prior theoretical work on the design of protocols for AI debate consists primarily of \[irving2018ai\], which introduced AI debate and its complexity-theoretic formalization, and \[brown-cohen24scalable\] which introduced doubly-efficient debate. As per the introduction, the original debate proposal makes the too-strong assumption that both debaters are computationally unbounded. Doubly-efficient debate relaxes this assumption, at the price of solving a more limited class of problems. In a complementary direction, the work of \[chen2023playing\] focuses on the theory of learning-in-games for AI debate. The objective in this case is to design efficient learning algorithms for debate-inspired games where the space of strategies is exponentially large, but the outcome of the game can be efficiently judged given strategies of two players.

The much earlier work in complexity theory by \[chandra1981alternation\] introduced, with different terminology, the question of studying the complexity of polynomial-time verifiable arguments between computationally unbounded provers. Later \[feige1997making\] proved stronger results in a complexity-theoretic model of an efficient verifier that judged arguments between competing computationally unbounded provers. A similar model with competing provers was studied in the context of delegation of computation to untrusted servers in \[canetti2013refereed\].

There has recently been a line of research applying single-prover interactive proofs to machine learning for proving correctness of model outputs \[amit2024models, anil2021learning, hammondneural\], and for improving interpretability and legibility \[waldchen2022merlin, kirchner2024prover\]. Empirical work on debate has focused primarily on debates where both the debaters and the judge are large language models (LLMs), and has shown some positive signs that debate allows for more accurate judgements on standard datasets \[michael2023debate, kentonscalable, khan2024debating\].

## Preliminaries ^preliminaries

We use the notation $[n] = \{1,\dots,n\}$. For a sequence of elements $x_1,\dots, x_n$ from a set $X$ and $S\subseteq [n]$, we use the notation $x_S$ for the subsequence of $x_i$ with $i \in S$. Similarly, we write $x_{\leq i}$, $x_{<i}$, and $x_{\neq i}$ to denote the subsequence consisting of $x_j$ where $j \leq i, j < i$, and $j\neq i$ respectively. For a probability $p \in [0,1]$ we use the notation $\mathop{\mathrm{\mathcal{B}}}(p)$ to denote the Bernoulli random variable that takes value $1$ with probability $p$, and $0$ otherwise. For a finite set $Z$, let $\Delta_Z$ denote the set of all probability distributions over $Z$, i.e., $\Delta_Z = \{p : Z \to [0,1] \mid \sum_{z \in Z} p(z) = 1\}$.

### Complexity-theoretic debate ^complexity-theoretic-debate

As in prior work on debate, we use computational complexity theory to formalize the power of the debaters and human judges, as well as the complexity of the problems that can be judged via debate.

##### Algorithms and oracles. ^algorithms-and-oracles

Algorithms are modeled by Turing machines $M:\{0,1\}^*\to\{0,1\}$ which take an input $x$ and output a yes-or-no answer encoded as a bit $M(x)\in\{0,1\}$. Furthermore, we consider _oracle Turing machines_ that additionally have black-box access to an oracle $\mathcal{O}:\{0,1\}^{n} \to \{0,1\}$. Once a query $u \in \{0,1\}^{n}$ is written on its tape, an oracle Turing machine can receive the oracle answer $\mathcal{O}(u) \in \{0,1\}$ in a single step. We use the notation $M^\mathcal{O}$ to denote an oracle Turing machine with black-box query access to the oracle $\mathcal{O}$. In the setting of AI debate, the Turing machine $M$ corresponds to a natural language plan or set of instructions to follow, and queries to the oracle $\mathcal{O}(u)$ corresponds to querying human judgement on a particular question $u$.

##### Classes of problems. ^classes-of-problems

The goal in debate is to design protocols that allow us to solve a broad class of computational problems, while requiring few queries to the human judgement oracle $\mathcal{O}$. A computational problem with a yes-or-no answer is encoded by a _language_ $L\subset \{0,1\}^*$ consisting of all the inputs $x$ for which the answer is “yes”. We abuse notation to view $L$ as a function $L:\{0,1\}^*\to \{0,1\}$ where $L(x)=1$ if $x\in L$ and $L(x)=0$ otherwise. The primary class of problems that we consider is $\textsf{NTIME}^{\mathcal{O}}(T)$, the set of problems where for every instance the answer is “yes” if and only if there is proof that the answer is “yes”, and this proof can be verified in time $T$ with access to the human judgement $\mathcal{O}$.

**Definition 1**. A language $L$ is in $\textsf{NTIME}^{\mathcal{O}}(T)$ if there is a time $T$ oracle Turing machine $M$ such that $x\in L$ if and only if there exists a proof $y$ of length at most $T$ such that $M^{\mathcal{O}}(x,y) = 1$.

We also use the class $\textsf{coNTIME}^{\mathcal{O}}(T)$ of languages $L$ whose complement is in $\textsf{NTIME}^{\mathcal{O}}(T)$. $\textsf{coNTIME}^{\mathcal{O}}(T)$ is the set of yes-or-no problems with efficiently checkable proofs of “no”.

**Definition 2**. A language $L$ is in $\textsf{coNTIME}^{\mathcal{O}}(T)$ if there is a time $T$ oracle Turing machine $M$ such that $x\notin L$ if and only if there exists a proof $y$ of length at most $T$ such that $M^{\mathcal{O}}(x,y) = 1$.

We use the notation $\Gamma^{\mathcal{O}}(T) = \textsf{NTIME}^{\mathcal{O}}(T)\cap\textsf{coNTIME}^{\mathcal{O}}(T)$ for the set of problems where one can verify both the cases $x\in L$ and $x \notin L$ with a proof that is checkable in time $T$ given access to the ground-truth oracle. Our main results focus on this class.

Our debate protocols will rely on recursively decomposing the execution of a verifier machine $M$ into individual steps. To formalize this we introduce the notion of the _transcript_ of a machine $M$.

**Definition 3**. The _transcript_ of a time $T$ machine $M$ on input $x$ is a string $\tau \in \{0,1\}^T$ where $\tau_i$ is the bit written at the current head position of $M$ at time step $i$.

### Game theory ^game-theory

The main game-theoretic concept used in our results is a _Stackelberg equilibrium_. This equilibrium concept models a situation where one player (the leader) must commit to a strategy, after which the other player (the follower) chooses their strategy. A Stackelberg equilibrium is a strategy for the leader that achieves the best possible payoff, given that the follower plays a best response.

**Definition 4** (Stackelberg equilibrium). Consider a two-player (leader and follower) game with a sequential structure, where $S_L$ is the set of strategies for the leader, $S_F$ is the set of strategies for the follower, $u_L(s_L, s_F)$ is the payoff for the leader, and $u_F(s_L, s_F)$ is the payoff for the follower. The game proceeds as follows: first the leader chooses a strategy $s_L \in S_L$, then the follower observes $s_L$ and chooses a strategy $s_F \in S_F$.

An _$\alpha$\-approximate Stackelberg equilibrium_ is a strategy profile $(s_L^*, s_F^*(s_L))$ with

1.  _Follower’s best response:_ For every leader strategy $s_L$, the follower’s strategy $s_F^*(s_L)$ is an approximate best response: 
    
    $$
    \begin{equation}
        u_F(s_L, s_F^*(s_L)) \geq u_F(s_L, s_F) - \alpha \quad \forall s_F \in S_F.
        \tag{1}
    \end{equation}
    $$
    
2.  _Leader’s optimal strategy:_ The leader’s strategy $s_L^*$ approximately maximizes the leader’s payoff, _given_ the follower’s best response function: 
    
    $$
    \begin{equation}
        u_L(s_L^*, s_F^*(s_L^*)) \geq u_L(s_L, s_F^*(s_L)) - \alpha \quad \forall s_L \in S_L.
        \tag{2}
    \end{equation}
    $$
    

Some intuition is useful for why Alice-leading, Bob-following Stackelberg equilibria are the right setting. For completeness, we will use a prover Alice that always gives correct answers: this will win against any Bob regardless of Bob’s computational complexity, and thus works as an Alice-leading strategy. For soundness, however, we must find an estimator Bob that uses computation not too much larger than Alice, which we do by repeatedly playing Alice against herself. This method of Bob construction works only once Alice is fixed, and thus requires Bob to be the Stackelberg follower.

## Debate protocols and games ^debate-protocols-and-games

The goal of debate is to provide an accurate training signal on questions too hard for humans to judge directly. Training with debate involves asking an AI $A$ to give the answer to a question $x$ drawn from a distribution $\mu$, and having another AI $B$ debate the correctness of $A$’s answer. At the end of the debate, human judgment is used to provide a reward signal to both AI debaters involved. Thus, the more specific goal is to design a _debate protocol_, i.e. the rules of the debate and the rewards, such that training $A$ and $B$ with the reward signal provided by the debate protocol leads to $A$ giving the correct answer to $x$. This can be formalized game theoretically: a debate protocol induces a game between the AI debaters, and the protocol succeeds if every equilibrium of the game leads $A$ to correctly answer almost all questions $x \sim \mu$.

We begin with the formal definition of a debate protocol, which specifies two sets of possible strategies as well as the verification procedure to determine the rules and outcome of a debate.

**Definition 5** (Debate protocol). A _debate protocol_ is given by a family of tuples $(\mathcal A_n,\mathcal B_n,V)$, where for each natural number $n$, $\mathcal A_n$ and $\mathcal B_n$ are finite sets of _strategies_ defined by functions $A,B :\{0,1\}^{O(n)} \to \{0,1\}^{O(n)}$, and the verifier $V:\{0,1\}^*\to[-1,1]$ is a polynomial time oracle Turing machine.

A debate protocol induces a zero-sum game where debaters select strategies from $\mathcal A_n$ and $\mathcal B_n$, exchange messages, and the verifier determines a final payoff based on all the messages in the debate.

**Definition 6** (Two-player, zero-sum debate game). Given a language $L$ and a distribution $\mu$ on inputs $x\in \{0,1\}^n$, a debate protocol induces a two-player zero-sum game where one player selects a strategy $A\in\mathcal A_n$, the other a strategy $B\in\mathcal B_n$. The payoffs are defined by the following process:

1.  Sample a random $x\sim \mu$.
    
2.  The $A$ player outputs a bit $A(x) \in \{0,1\}$ to claim that $L(x) = A(x)$ (that is, $A$ suggests whether the claim is true or false).
    
3.  The players $A$ and $B$ interact by exchanging messages on input $x$. In particular, $A$ and $B$ generate a sequence of messages $a_i = A(x,a_1,b_1,\dots,a_{i-1},b_{i-1})$ and $b_i = B(x,a_1,b_1,\dots,a_{i-1})$.
    
4.  The verifier $V$ runs on the interaction to determine the payoffs.
    
5.  The $A$ player receives payoff $V^{A,B}(x)$ and the $B$ player receives payoff $-V^{A,B}(x)$.
    

The rules of the debate are encoded by the verifier $V$, while the sets of functions $\mathcal A_n,\mathcal B_n$ encode the possible strategies that debaters $A$ and $B$ can employ. For example, $V$ might be a set of prompts and scaffolding for an LLM debate, while $\mathcal A_n$ and $\mathcal B_n$ are sets of possible LLMs of given architecture and size. When the input length $n$ is clear we write $\mathcal A$ and $\mathcal B$ for the strategy sets. Our setting in this paper is when $\mathcal A$ and $\mathcal B$ both contain functions of bounded computational complexity. We measure complexity purely relatively, i.e. we show that it is possible to incentivize the $A$\-player to provide the correct solution when the set of strategies $\mathcal B$ are all low-complexity functions of strategies from $\mathcal A$. Each debate will then also have low $\mathcal A$\-complexity, as each round of the debate requires a constant number of queries to the strategies of $A$ and $B$.

## Recursively decomposable problems ^recursively-decomposable-problems

In this section we introduce the problem class for which our debate protocols will succeed. The intuition is that for any $L \in \Gamma^{\mathcal{O}}(T)$, checking the proof $y$ that $x\in L$ or $x\notin L$ can be recursively decomposed into subproblems. Given a transcript $\tau$ of a verifier machine $M(x,y)$, a natural decomposition is to split into the two subproblems of checking that the first half of $\tau$ is correct and that the second half is correct. This decomposition can be repeated $\log T$ times until the final level, which checks individual steps in $\tau$. We formalize the notion of a recursive decomposition as follows.

**Definition 7**. Let $L \in \Gamma^{\mathcal{O}}(T)$ be a language and $M$ the machine that verifies proofs for membership of $x\in L$ (or $x \notin L$ respectively). A depth $d$, width $q$ _recursive decomposition_ for $L$ is defined by a time $O(nq)$ machine $M_D$ that takes as input an original input $x\in \{0,1\}^n$, a sequence of $q$ _queries_ $y = (y_1,\dots,y_q)\in\{0,1\}^{n\times q}$, and a sequence of $q$ _query answers_ $z = (z_1,\dots,z_q) \in \{0,1\}^q$. For any $x \in L$ there exists an _implicit proof_ $u\in\{0,1\}^m$ with $m \leq q^d$ such that for all $k \in [d]$, the correct answers $z^k$ to queries $y^k$ are defined recursively as follows.

1.  For the base case $k = 0$, for all leaves $i$ there exists a subset $S_i \subseteq [m]$ of coordinates in the implicit proof, such that the query $y_i^0 = S_i$, and the correct answer $z_i^0 = \mathcal{O}(u_{S_i})$.
    
2.  The correct answers to queries $y^{k-1}$ satisfy $z^k_i = M_D(x,y^{k-1}_i,z^{k-1})$, where $z^{k-1}$ are the correct answers to $y^{k-1}$. That is, answers at $k-1$ support answers at $k$.
    
3.  At the top level $k = d$ of the recursion, $M_D(x,y^d,z^d) = M^{\mathcal{O}}(x,y^*)$ where $y^*$ is a witness to the original machine $M^{\mathcal{O}}$ for $L$.
    

Intuitively a recursive decomposition breaks down the task of checking that $x\in L$ into $q$ subproblems, which are themselves broken down into $q$ subproblems, with the recursion bottoming out in ground-truth oracle queries to an implicit proof $u$. Thus, the queries $y_i^k$ at non-leaf steps in the recursion have correct answers $z_i^k$ that are functions of larger subsets of the $u$, with the top level depending on the entire implicit proof. For every language $L\in\Gamma^{\mathcal{O}}(T)$ there is a natural recursive decomposition of depth $d=\log T$ and width $q=2$, where the implicit proof $u$ is just the transcript $\tau$ of $M(x,y^*)$. The base case queries $y_i^0$ are just individual steps in the transcript $\tau$, the queries $y_i^1$ are claims that $2$ consecutive steps of $\tau$ are performed correctly, and in general $y_i^k$ is the claim that $2^k$ consecutive steps of $\tau$ are correct, which is clearly the AND of two queries $y_1^{k-1},y_2^{k-1}$ regarding sequences of $2^{k-1}$ steps. Hence, $M_D$ simply computes the AND function on the query answers $z_1$ and $z_2$.

For a general language $L\in\Gamma^{\mathcal{O}}(T)$ some of the subproblems given by queries $y_{i}$ may be computationally intractable for debaters using only algorithms $A\in \mathcal A$, while others can be efficiently solved by some $A\in\mathcal A$. Our goal is to design a protocol that is agnostic to the difficulty of the subproblems. If all subproblems are easy it should be possible for the honest debater to win the debate without expanding the full proof tree corresponding to the recursive decomposition. At the same time, it should not be possible for a dishonest debater to win by intentionally decomposing an easy problem into hard subproblems, which the honest debater is unable to refute. To achieve this goal, the computational complexity of the provers in the debate will be measured purely relatively, i.e. $\mathcal B$ contains strategies that are low complexity functions of the strategies in $\mathcal A$.

We next capture problems where an AI can solve any subproblem in the recursive decomposition if asked, and thus in some sense “knows” the correct answer. The definition requires that there is a strategy $A\in\mathcal A$ that correctly answers all queries that appear in the recursive decomposition $M_D$.

**Definition 8** ($\mathcal A$\-provable). For each natural number $n$, let $\mathcal A_n$ be a set of functions on $\{0,1\}^n$ and let $0 < \gamma < 1$. Let $\mu$ be a distribution on inputs $x$ of length $n$, let $L\in\Gamma^{\mathcal{O}}(T)$ be a language, and let $M_D$ be a recursive decomposition of $L$. The decomposition $M_D$ is $\mathcal A$\-provable with probability $1-\gamma$ if there exists a single $A\in\mathcal A$ such that with probability at least $1-\gamma$ over $x \sim \mu$:

1.  In the base case of the decomposition, $A(x,j) = u_{j}$ for any $j\in S_i$, where $S_i$ is the subset given by $y_i^0$.
    
2.  For all queries $y_i^k$ in the recursive decomposition, $A(x,y_i^k) = z_i^k$ is the correct query answer.
    
3.  $A(x) = L(x)$.
    

We also need the arguments made in the debate to not depend too precisely on the probabilities of the answers to the subproblems.

**Definition 9** ($\rho$\-stability). For any $z  \in \{0,1\}^q$, let $D_{\epsilon}(z)$ be the set of distribution $p$ over $\{0, 1\}^q$ such that for any $i \in [q]$, $\mathop{\mathrm{\mathbb{P}}}_{z' \sim p}[z'_i \neq z_i] \leq \epsilon$.

Let $x\in\{0,1\}^n$ be an instance of a problem $L \in \Gamma^{\mathcal{O}}(T)$ and let $M_D$ define a width $q$ recursive decomposition of $L$. $M_D$ is $\rho$\-stable at node $(x,y)$ if for any $\epsilon > 0$ and any distribution $p\in D_{\epsilon}(z)$, where $z$ is the ground truth solution to $(x,y)$, there is 

$$
\mathop{\mathrm{\mathbb{P}}}_{z'\sim p}\left[M_D(x, y, z') \neq M_D(x, y, z)\right] \leq \rho \cdot \epsilon.
$$

Further, $M_D$ is $\rho$\-stable for an input $x$ w.r.t. Alice’s algorithm $A$ if for every node $(x,y)$ that might be visited in the debate tree generated by $A$, $M_D$ is $\rho$\-stable at $(x,y)$.

For simplicity, we may say $M_D$ is $\rho$\-stable for an input $x$ when Alice’s algorithm $A$ is clear from the context. Interestingly, this stability condition is captured by the notion of _fractional block sensitivity_ from boolean function analysis (see, e.g., \[KulkarniTal2016fbs\]); this connection is further discussed in .

Intuitively says that changing the _marginal_ probabilities of the sequence $z$ by less than $\epsilon$ leads to small changes in the output of the verifier machine. In practical settings where the truth is determined by aggregation of many pieces of uncertain evidence (e.g. empirical science, legal arguments), $\rho$\-stability will hold for small constant values of $\rho$. For example, suppose that one wants to determine whether a majority of scientific literature supports the efficacy of a certain drug. If 2/3rds of studies show that the drug is effective, then even if up to 1/6th of all published studies turned out to have critical flaws, the majority outcome remains unchanged. In this case, the claim about the majority of scientific literature is $\rho$\-stable for $\rho = 4$. To see why, one can check that by symmetry, the way to maximize the chance of flipping the majority vote while minimizing the change in the marginal probability of overturning each individual study is to uniformly select 1/6th of the studies to flip among the 2/3 that say the drug is effective. In this case $\epsilon = \frac{1/6}{2/3} = 1/4$ and flipping these 1/6 of the studies flips the majority with probability $1 = 4\epsilon$. Thus the majority vote is $\rho$\-stable with $\rho = 4$ in the case that 2/3rds of the inputs are set to true.

## The Prover-Estimator Debate Protocol ^the-prover-estimator-debate-protocol

The prover-estimator debate protocol.

In this section we give our debate protocol and the main theorems that it correctly incentivizes debaters for problems in $\Gamma^{\mathcal{O}}$. The intuition is as in : debater $A$ decomposes the problem into subproblems, and debater $B$ gives probabilities for the answers to each subproblem. Debater $A$ then selects a subproblem for recursion where $B$’s probability is allegedly incorrectly estimated. Rewards are assigned in each round to $A$ for correctly predicting inconsistencies between $B$’s probabilities in the current round versus the previous round, with the available reward growing by a factor of $1/r$ in each round. The final round uses the human judgment oracle $\mathcal{O}$ rather than $B$’s probabilities.

### The protocol ^the-protocol

Our protocol for two-player zero-sum debate is given in . We can now state our main theorem.

**Theorem 10**. _Let $\mathcal A$ be any set of functions on $\{0,1\}^n$ and $\eta > 0$. Let $\mu$ be a distribution on inputs $x\in\{0,1\}^n$, and $L \in \Gamma^{\mathcal{O}}(n^c)$ be a language with a recursive decomposition $M_D$ of depth $d$ and width $q$. Let 0 < $\gamma < 1/2$ and take a stability parameter $\rho$. Then the protocol of run on $M_D$ satisfies:_

-   _**Completeness.** Suppose $M_D$ is $\mathcal A$\-provable with probability $1-\gamma$ over $x\sim \mu$, which is achieved by a function $A^* \in \mathcal A$. If $M_D$ is also $\rho$\-stable at $x$ w.r.t. $A^*$ with probability $1-\gamma$, then there exists $A \in \mathcal A$ such that for all $B$ (of any size), with probability at least $1 - 2\gamma$ 
    
    $$
    \mathop{\mathrm{\mathbb{E}}}_{{}}\left[V^{A,B}(x)\right] \geq \frac{1}{\rho^{d+1}},
    $$
    
     where the expectation is over the internal randomness of the protocol only._
    
-   _**Soundness.** Let $\mathcal B$ be the set of circuits of size $O\left(q 2^{3q}nd^2/\eta^2\right)$ that may query a function $A\in \mathcal A$ at each gate. For every strategy $A\in \mathcal A$, there exists $B\in\mathcal B$ such that, 
    
    $$
    \mathop{\mathrm{\mathbb{E}}}_{{x\sim \mu}}\left[V^{A,B}(x)\right] \leq \frac{\mathop{\mathrm{\mathbb{P}}}[A(x) = L(x)]}{\rho^{d+1}} + \eta.
    $$
    
    _
    

Notice that we only require that $L$ admits an $\mathcal A$\-provable, $\rho$\-stable decomposition in the completeness case. This means that a dishonest debater $A$ may produce an incorrect decomposition into queries $y^k$ for some input $x$ such that $M_D(x,y^k,z^k)$ is not $\rho$\-stable, with answers to queries that cannot be answered by any function in $\mathcal A$. Therefore, our protocol must account for situations where $A$ produces an unstable decomposition into hard-to-answer queries, and ensure $B$ is still able to win.

We usually consider $q$ being a constant independent of $n$ and $q^{d} = O(n^c)$. Since the dominant per-round cost is $B$’s probability estimates, a single prover-estimator debate has a cost of $O(q 2^{3q}nd^3/\eta^2)$ queries to functions in $\mathcal A$. When there exists a very stable decomposition $M_D$ ($\rho \ll q$), prover-estimator debate has a polynomial improvement over the cost $O(n^c)$ required to verify the full human-judgeable argument given by the transcript of $M^{\mathcal{O}}(x,y^*)$. In particular, doubly-efficient debate would require $O(n^c)$ queries to the debaters, and naive recursive debate would either fail to satisfy soundness, or otherwise require expanding the whole $O(n^c)$\-size search tree.

The proof of follows from the completeness lemma and the soundness lemma . The proof of completeness, that an honest debater $A$ can always defeat a dishonest debater $B$, follows from the intuition that human judgement is used directly in the last round, and the reward in each round increases by a factor of $1/r$. Thus, even if $B$ lies throughout the first $k$ rounds, at some point $B$ (or eventually the human judgement oracle) must tell the truth, at which point a debater $A$ that has always answered honestly can pick up a positive reward that is larger than the sum of all negative rewards received so far.

The key technical piece is in showing soundness: that regardless of the dishonest strategy employed by debater $A$, debater $B$ can gain an advantage while using only slightly more compute than $A$. We use methods from online convex optimization to construct probabilities for $B$ that are indistinguishable by $A$ from the truth. The idea is to run online gradient descent on a sequence of loss functions which capture how well on average $A$ can distinguish $B$’s probabilities from the truth. The convergence rate of online gradient descent then yields bounds on the complexity of $B$’s strategy relative to $A$’s.

As a corollary of , we show that answering correctly is an $A$\-leading Stackelberg equilibrium in the prover-estimator debate game. The equilibrium result is weaker than , because it requires $\mathcal A$\-provability always rather than only for completeness (a definitional artifact).

**Theorem 11**. _Let $\mathcal A$ be any set of functions on $\{0,1\}^n$ and let $d$, $q$, $\mathcal B$ be as in , with $\eta = \frac{\epsilon}{\rho^{d+1}}$. Let $\mu$ be a distribution on inputs $x\in\{0,1\}^n$, and let $L \in \Gamma^{\mathcal{O}}(n^c)$ be a language with a recursive decomposition given by $M_D$. Let $\mathcal G$ be the two-player zero-sum game defined by the protocol of with decomposition $M_D$, and let $\alpha < \frac{\epsilon}{\rho^{d+1}}$. If $M_D$ is $\mathcal A$\-provable and $\rho$\-stable each with probability $1-\frac{\epsilon}{\rho^{d+1}}$, then in every $\alpha$\-approximate, $A$\-leading Stackelberg equilibrium of $\mathcal G$ 

$$
\mathop{\mathrm{\mathbb{P}}}_{x\sim \mu}[A(x) = L(x)] > 1 - 5\epsilon.
$$

_

We prove in .

### Consequences for training with prover-estimator debate. ^consequences-for-training-with

The key take-away of our two main theorems is that one can train debaters in the prover-estimator debate protocol via standard methods that converge to Stackelberg equilibria in zero-sum games. If the validity of claims in the debate is not sensitive to a small set of evidence ($\rho$\-stability) and the AI debaters only make claims they actually know the answer to ($\mathcal A$\-provability), then implies $A$ will produce the correct answer with probability at least $1 - 5\epsilon$. On the other hand, if it is not possible for the AI’s to decompose their arguments into subclaims which are both supported by sufficient evidence and which the AI’s can actually answer, then the soundness case of implies that the payoff to $A$ will fall below a known threshold. Thus, one can read off whether training has succeeded by looking at $A$’s expected payoff, and in the case of success, $A$ outputs the correct answer with probability $1 - 5\epsilon$. We provide further recommendations for empirical debate research in .

## Technical Overview ^technical-overview

In this section we summarize the main ingredients in the proof of . We begin with a more detailed discussion of what goes wrong with naive recursive debate, and an idealized model of the obfuscated arguments problem.

##### Obfuscated arguments with naive recursion. ^obfuscated-arguments-with-naive

In naive recursive debate, the debater $A$ decomposes the initial problem of deciding whether $x\in L$ into subproblems $y_1,\dots,y_q$ along with claimed answers $z_i = A(y_i)$ to each subproblem. Debater $B$ then selects a subproblem $y_i$, and the protocol recurses with $A$ claiming that $A(y_i) = z_i$. The obfuscated arguments problem refers to the fact that $A$ may choose a decomposition $y_1,\dots,y_q$, and answers $z_i = A(y_i)$, such that only one of the answers is wrong, but it is computationally intractable for both $A$ and $B$ to determine which one.

A concrete example of obfuscation is primality testing \[barnes2020obfuscated\]. In this case, the initial question is whether an integer $x$ is prime or composite. The Miller-Rabin primality test can efficiently solve this problem, but there is no known polynomial-time algorithm to factor $x$ \[miller1975riemann, rabin1980probabilistic\]. Indeed, if $x$ is the product of two randomly chosen $n$\-bit primes, the RSA cryptosystem’s security relies on the inability to efficiently factor $x$ \[rivest1978method\]. Hence, $A$ can employ the following obfuscating strategy in the case that $x$ is a hard-to-factor product of two primes. $A$ decomposes the integers from 1 to $x$ into $q$ intervals $y_1,\dots,y_q$, and claims that $x$ has no factors in each interval. When $B$ chooses an interval $y_i$ for recursion, $A$ further decomposes this into $q$ subintervals and so on. For $B$ to correctly identify the flaw in $A$’s argument, $B$ would need to find a factor of $x$, which is computationally intractable. This holds even though both $A$ and $B$ can run the Miller-Rabin test and be confident a factor exists. In summary, $A$ has efficiently decomposed the problem such that both debaters know there is a flaw somewhere in $A$’s argument, but neither can efficiently locate the flaw.

##### Soundness via indistinguishability. ^soundness-via-indistinguishability

Prover-estimator debate aims to mitigate the obfuscated arguments problem using computational indistinguishability. Debater $A$ decomposes the problem $x$ into subproblems $y_1,\dots,y_q$, just as in naive recursive debate. Then debater $B$ is allowed to assign a joint probability distribution $p$ for the truth value of each subclaim $y_i$. Obfuscated arguments shows that $B$ cannot count on being able to efficiently solve the subproblems $y_i$. Instead, we show that $B$ can efficiently produce probabilities $p$ that are computationally indistinguishable from the correct answer by $A$. Our notion of efficiency is that $B$’s strategy can be computed by a small circuit making queries to $A$’s strategy at each gate. The notion of indistinguishability that we use in the proof is known as _outcome indistinguishability_ \[dwork2021outcome\], and intuitively requires that, _on average over the input distribution_, $A$ cannot tell the difference between a sample from the ground-truth answers and a sample from $B$’s chosen probabilities $p$. See for the formal definition. To ensure that $A$ has advantage at most $\delta$ in distinguishing, the size of $B$’s circuit must grow as $O(q2^{3q}/\delta^2)$. The exponential factor in $q$ appears because this type of indistinguishability requires explicitly representing $B$’s probability distribution over the $2^q$ possible answers for the $q$ subclaims at each level. Hence, we will require that $q$ is a constant independent of the input size $n$.

It is instructive to see how indistinguishability helps for a particularly simple type of obfuscated argument by $A$. Suppose that $A$ decomposes $x$ into $q$ subproblems so that there is one subproblem $y_i$ where the correct answer is $z_i=0$, but neither $A$ nor $B$ can identify this subproblem any better than by randomly guessing its location. In this case, $B$ can output a probability of $1/q$ that each answer $z_i = 0$. If $A$ chooses a subproblem $y_i$ to recurse on, $A$ will in all likelihood choose one where the true answer is 1, hence $B$’s probability is only off by $1/q$. If $A$ again obfuscates in the next round of the prover-estimator debate, then $B$’s probability will be off by at most $1/q^2$. Thus, if we reward $A$ proportional to the magnitude of the error in $B$’s probability, $A$ will receive a very small reward.

In the general case, prover-estimator debate gives rewards in every round of the debate. Prior to the initial round, $A$ receives expected reward proportional to how close $B$’s initial probability estimate is to $A$’s initial claim about the input. In all but the last round, the rewards are proportional to any error in the consistency between $B$’s probability claimed in the current round, versus the previous round. However, $A$ only receives these rewards if $A$ has correctly identified the direction of $B$’s error. In the final round, $B$’s probabilities are compared to human judgement, and again $A$ only receives a reward proportional to the magnitude of $B$’s error if $A$ correctly predicted the error direction. Hence, $B$ can use indistinguishability to ensure that $A$ gains rewards at most $\delta$ in each round, at the price of using strategies with circuit size $O(q2^{3q}/\delta^2)$. The only remaining source of reward for $A$ then comes from the initialization, where $A$ receives rewards depending on how closely $A$ agrees with $B$’s initial probability estimate $p$. Indistinguishability then implies that the fraction of inputs on which $A$ agrees with $B$’s initial estimate $p$ is approximately equal to the fraction of inputs where $A$ agrees with the ground truth. Thus, by using more compute $B$ can ensure that $A$’s rewards are bounded by a value proportional to the probability that $A$ agrees with the ground truth on the initial problem.

##### Completeness via stability. ^completeness-via-stability

For the soundness guarantees upper-bounding $A$’s rewards to be meaningful, we must also show that if $A$ tells the truth, it is possible to lower-bound the rewards received by $A$. Completeness is achieved via two key properties. First, we will require $\rho$\-stability of the decomposition, and second, the magnitude of available rewards will grow by a factor of $1/r$ in each round, where $r = 1/\rho$. To see why we need both properties, consider the following sketch of a completeness argument. Suppose $A$ always correctly answers the initial input problem and all subclaims, and that $A$ always selects the marginal probability from $B$ that is furthest from the truth. Then if $B$ ever outputs an incorrect probability, it will eventually lead to $B$ being caught: either in the final round when comparing to human judgement, or in some intermediate round where $B$ switches to telling the truth, and thus outputs an inconsistent probability. The reason for the rewards to grow by a factor of $1/r$ in each round is to ensure that no matter what happened in the prior rounds, the cumulative negative rewards received earlier by $A$ are outweighed by the reward in the round where $B$ is finally caught in an inconsistency or by the human-judgement comparison.

The reason for the stability requirement arises from the need to check for inconsistencies between $B$’s probability for the query $\hat{y}$ selected for recursion in the previous round, when compared to $B$’s probabilities for the subclaims $y_i$ in the current round. In the worst case, very small changes in $B$’s probabilities for the subclaims could cause large changes in overall outcome for the query $\hat{y}$. Thus, even if $B$’s probability estimate for $\hat{y}$ was off by a lot, $B$ could produce estimates for the $y_i$ that are individually only slightly off (say $O(1/q)$), but are approximately consistent with the original estimate for $\hat{y}$. This would mean that, even when $A$ told the truth and $B$’s estimates of the initial probability were far from correct, $B$ could shift to approximately correct estimates while paying a small cost in rewards to $A$ for the consistency checks. Stability prevents this failure mode, because it requires that small errors in probability for the $y_i$ have a small impact on the outcome for $\hat{y}$.

Put another way, stability limits how rapidly errors can grow in the debate tree. This can also be interpreted as on average limiting the total search space necessary to determine correctness, because even errors of magnitude $\epsilon > 1/q$ cannot change the overall outcome by much, so it is not information-theoretically necessary to search the full debate tree of size $q^d$ to determine correctness.

##### Ensuring large reward gap. ^ensuring-large-reward-gap

This outlined argument ensures $A$ receives some minimal reward when telling the truth, and that $B$ can spend more compute to ensure that $A$ receives an amount $\Delta$ less reward if $A$ frequently lies. However, $\Delta > 0$ is insufficient for efficient debate training. To see why, observe that if we run naive recursive debate with $q$ subclaims per round and $d$ rounds, we achieve $\Delta = 1/q^d$ if $B$ uniformly randomly selects subclaims for recursion. This does not enable efficient training, as in expectation one needs to run $q^d$ debates before seeing a single one where $B$ catches a flaw. In contrast, obtains $\Delta = \Omega(1/\rho^d)$ and one need only see $O(\rho^d)$ debates before getting a non-trivial training signal, where $\rho$ can be significantly smaller than $q$ for stable decompositions.

## Discussion and Open Problems ^discussion-and-open-problems

While prover-estimator debate mitigates the obfuscated arguments problem that occurs in amplification and other scalable oversight protocols, it does not have all the features of these other protocols. For example, it lacks the argument/counterargument structure of \[irving2018ai\] and the Bayesian structure of \[bengio2025scientist\]. We hope that future work can explore whether the core ideas needed to avoid obfuscated arguments can be combined with features of other protocols.

Our paper presents debate protocols which circumvent the obfuscated arguments problem in recursive debate. Intuitively, this demonstrates that it is possible to design the rules of a debate such that training to win at debate leads to correct behavior of the final trained models in most cases. These theoretical results lead to qualitative recommendations for empirical debate research, which present interesting avenues for future research in both of these directions.

##### Theoretical. ^theoretical

Our results identify stability as a critical requirement for debate training to succeed, and hence we need to better understand when stability can be achieved, either in theory for interesting classes of problems, or in practice for debates in messy, unformalized settings. On the theoretical side, requires stability for completeness but not soundness, and thus is safe to use even if one is not confident in stability. However, it can still be the case that the prover only knows how to produce an unstable decomposition into solvable subproblems, implying that certain problems cannot be accurately judged via our protocol even when both debaters know the correct answer. Thus, an interesting direction for future work is to understand whether the stability condition is necessary in this setting. An optimistic hope might be that all relevant problems can be divided into two classes: those that require very precise dependence on individual subclaims (e.g. mathematical proofs) and those that do not (e.g. scientific knowledge obtained by noisy empirical evidence). If this were the case, future debate protocols might attempt to handle each type of claim separately. For example, one could require the debaters to produce machine-verifiable proofs in Lean for all mathematical subclaims, and use prover-estimator debate to verify fuzzier subclaims. Theoretical progress in this direction depends on precisely characterizing the structure of problems that admit stable decompositions.

Another limitation is that our results hold in an average-case rather than a worst-case sense: we do not prove the judge is always able to tell which debater is correct on every question. Rather, we show that the payoffs given by the judge incentivize the debaters to converge to answering correctly. Thus, the payoff assigned by the judge is a random variable that is correlated with correctness, but imperfectly so. We believe such an average-case analysis is necessary, and formalizing this is an interesting open question. We are also curious whether there are corresponding lower bounds to $B$’s circuit size if the stability parameter $\rho$ is held constant, in either the oracle or fine-grained complexity settings.

##### Empirical. ^empirical

The central empirical question raised by our paper is how to incorporate the qualitative recommendations from our theoretical results into practical debate training experiments with LLMs. Such experiments may require additional flexibility for training to succeed, so we enumerate the key qualitative properties of prover-estimator debate that could guide practical debate experiments:

1.  The prover $A$ both decomposes problems and chooses where to recurse given $B$’s estimates. The estimator $B$ only needs to express reasonable uncertainty about where a mistake might lie.
    
2.  There is a per-round reward based on a consistency check between $B$’s estimate from the last round for the current main claim, and estimates for claims in the current round. $A$ can only collect this reward by accurately predicting the direction of $B$’s error between rounds.
    
3.  In the last round, the judge directly decides if $B$’s estimates are correct.
    
4.  The debaters should be trained to converge to an $A$\-leading Stackelberg equilibrium.
    

##### Zooming out. ^zooming-out

The broad question is whether some variant of debate works as a component of an overall alignment strategy. \[buhl2025alignment\] sketches what an overall safety case using debate might look like, combining both theoretical and empirical evidence. We believe prover-estimator debate is a useful contribution on the theory side, but hope that future work finds improved protocols that combine the advantages of other scalable oversight methods (). In particular, we are interested in protocols which mitigate systematic errors in human input \[irving2025systematic\] and the potential for debaters to hide information in the subclaims $y_k$ \[pfau2025search\]. These are just two areas for improvement: the full safety case sketch has a lot more holes to fill.

## Acknowledgments ^acknowledgments

We would like to thank Beth Barnes for good probing on the stability requirement, Marie Buhl for discussions relating this work and broader debate safety cases, Benjamin Hilton, Jacob Pfau, Zachary Kenton, Simon Marshall, Jacob Hilton, and Mario Szegedy for detailed comments on the paper, and Lean for refusing to buy the second author’s incomplete understandings of earlier versions of the proof. JL is supported by Scott Aaronson’s Coefficient Giving grant. ZX is supported by the NSF AI Institute for Foundations of Machine Learning (IFML).

## Proof of ^proof-of

Fix a strategy $A$ for the leader. Our approach is to construct a small circuit implementing $B$’s strategy via online gradient descent on a sequence of loss functions chosen so that $B$’s probabilities will be indistinguishable by $A$ from the truth. In each iteration of online gradient descent the loss is chosen by measuring, averaged over all queries, how well $A$ can distinguish between $B$’s current strategy and the true answer.

Crucially, _our online gradient descent algorithm cannot be run_: each step of gradient descent requires access to the truth, which is available only with exponential compute. However, we will show that the resulting circuit $B$ has complexity bounded in terms of _number of iterations_, which will be small.

### Indistinguishability ^indistinguishability

We begin with a formal definition of the notion of indistinguishability that we will use in our proof.

**Definition 12**. Let $X$ be a set, $Z$ be a finite set, $\mu$ be a finitely supported probability distribution on $X$, and $g:X \to \Delta_Z$. Let $\mathcal{F}$ be a finite family of functions $f:X\times Z\times \Delta_Z \to [-1,1]$. A function $h:X\to \Delta_Z$ is _$(\delta,\mathcal{F})$\-indistinguishable_ from $g$ if and only if for all $f\in\mathcal{F}$ 

$$
\left\lvert\mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu\\ z\sim g(x)}}}\left[f(x,z,h(x))\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu\\z\sim h(x)}}}\left[f(x,z,h(x))\right]\right\rvert < \delta
$$

Intuitively, says that test-functions from the class $\mathcal{F}$ cannot tell the difference between $h$ and $g$. Our notion of indistinguishability is nearly equivalent to a multi-class variant of _outcome indistinguishability_ \[dwork2021outcome\], with the only difference being that we use real-valued bounded test functions, rather than functions taking values in $\{0,1\}$. The work of \[Dwork2022BeyondBG\] further provides an algorithm for constructing multi-class outcome indistinguishability in the $\{0,1\}$\-valued test function setting. However, due to a slightly different focus, \[Dwork2022BeyondBG\] achieve a linear dependence on $\left\lvert Z\right\rvert$ in the complexity of $h$, at the cost of an $O(\log\left\lvert\mathcal A\right\rvert)$ factor. In our setting $\left\lvert Z\right\rvert = 2^q$ is small, while $\log\left\lvert\mathcal A\right\rvert$ is as large as the circuit complexity (or number of weights in the neural network) of the debaters. Thus, we design a different algorithm than that of \[Dwork2022BeyondBG\] which has quadratic dependence on $\left\lvert Z\right\rvert$, but is independent of $\left\lvert\mathcal A\right\rvert$.

Our main technical lemma uses online gradient descent to produce a $(\delta,\mathcal{F})$\-indistinguishable function $h$ that has bounded complexity relative to $\mathcal{F}$. In particular, $h$ will be computable by a small circuit that at each gate may query a function $f\in\mathcal{F}$. The result will follow from online gradient descent, where in each iteration we select a loss function determined by some $f\in\mathcal{F}$ such that the condition of does not hold.

We recall the standard guarantees of online gradient descent \[zinkevich2003online, hazan2016introduction\].

**Theorem 13** (Online Gradient Descent). _Let $K$ be a convex set, $D$ be the diameter of $K$, and $G$ an upper bound on $\lVert\nabla l_t(v)\rVert_2$ for $v\in K$. Then for each $v\in K$, online gradient descent with step sizes $\eta_t = \frac{D}{G\sqrt{t}}$ satisfies 

$$
\textrm{regret} = \frac{1}{T}\sum_{t=1}^T l_t(v_t) - \frac{1}{T}\sum_{t=1}^Tl_t(v) \leq \frac{3DG}{2\sqrt{T}}
$$

 where the loss $l_t$ can be chosen adversarially after $v_t$ is revealed._

**Lemma 14** (Indistinguishability). _Let $X$ be a set, $Z$ be a finite set, $\mu$ be a finitely supported distribution on $X$, and $\mathcal{F}$ a set of functions $f : X \times Z \times \Delta_Z \to [-1,1]$. For any $g:X \to \Delta_Z$ there exists a function $h:X\to \Delta_Z$ such that_

1.  _$h$ is $(\delta,\mathcal{F})$\-indistinguishable from $g$._
    
2.  _$h$ is computable by a circuit of size $O(\left\lvert Z\right\rvert^2/\delta^2)$ that can query some $f\in\mathcal{F}$ at each gate._
    

_Proof._ The function $h$ will be the output of . The first condition of the lemma will follow from the guarantees of online gradient descent, so we begin by showing that is online gradient descent on an appropriate sequence of losses.

For a function $h:X\to \Delta_Z$ we let $h(x,z) = \mathop{\mathrm{\mathbb{P}}}[h(x) = z]$ denote the probability assigned to $z\in Z$ by $h$ at input $x \in X$. We can interpret both $h(x,z)$ and $F(x,z) = f(x,z,h(x))$ as functions $X\times Z \to \mathbb R$. Construct an embedding $\Psi$ sending functions $h:X\times Z\to \mathbb R$ to vectors in $\mathbb R^{X\times Z}$ as 

$$
\Psi h(x,z) = \sqrt{\mu(x)} \cdot h(x,z)
$$

 Hence the inner product between embeddings is given by $\langle\Psi h,\Psi g\rangle = \mathop{\mathrm{\mathbb{E}}}_{{x\sim \mu}}\left[\sum_{z\in Z}h(x,z)g(x,z)\right]$. Let $\mathcal H= \{\vec{h} \in \mathbb R^{X\times Z}\ \mid \vec{h} = \Psi h, h:X \to \Delta_Z\}$. Observe that $\lVert\vec{h}\rVert_2 \leq 1$ for all $\vec{h} \in \mathcal H$ and that the $\ell_2$\-projection onto $\mathcal H$ is given by, for each $x$, projecting the $\left\lvert Z\right\rvert$\-dimensional vector $\vec{h}(x,\cdot)$ to $\Delta_Z$.

Now for any $f\in\mathcal{F}$ we define the loss functions $l_t:\mathbb R^{X\times Z} \to \mathbb R$ by 

$$
\begin{equation}
        l_t(\vec{h}) = \left\lvert\langle\Psi g,\Psi F\rangle - \langle\vec{h},\Psi F\rangle\right\rvert
    \tag{3}
\end{equation}
$$

 As it is the absolute value of an affine function, $l_t$ is convex in $\vec{h}$. Furthermore, for any $\vec{h} \in \mathcal H$ with $\vec{h} = \Psi h$, the subgradient of $l_t$ is given by 

$$
\begin{align*}
        \partial l_t(\vec{h})(x,z)
            &= -\mathop{\mathrm{sign}}\left(\langle\Psi g, \Psi F\rangle - \langle \vec{h}, \Psi F\rangle\right)\Psi F(x,z)\\
            &= -\mathop{\mathrm{sign}}\left(\mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu\\z \sim g(x)}}}\left[f(x,z,h(x))\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu\\ z \sim h(x)}}}\left[f(x,z,h(x))\right]\right)\Psi F(x,z)\\
            &= -\mathop{\mathrm{sign}}\mathop{\mathrm{Adv}}_f \cdot \Psi F(x,z)
\end{align*}
$$

 Hence the embedding by $\Psi$ of the gradient update on line 8 of can be written as 

$$
\Psi h_{t+1} = \Psi h_t + \eta_t \cdot \mathop{\mathrm{sign}}\mathop{\mathrm{Adv}}^t_f \cdot \Psi F = \Psi h_t - \eta_t \cdot \partial{l_t(\Psi h_t})
$$

 Furthermore, the projection on line 9 corresponds to the projection of $\vec{h_t}$ onto $\mathcal H$. Therefore, is precisely online gradient descent on the embedded vectors $\Psi h_t$ with loss $l_t$. Since $\left\lvert\mathop{\mathrm{Adv}}_f\right\rvert \leq 2$ we have $\lVert\partial l_t(\vec h)\rVert_2 \leq 2\lVert\Psi F\rVert_2 \leq 2\sqrt{\left\lvert Z\right\rvert}$ for all $\vec{h}\in\mathcal H$. By we conclude 

$$
\begin{align}
            \frac{3\sqrt{\left\lvert Z\right\rvert}}{\sqrt{T}} &\geq \frac{1}{T}\sum_{t=1}^T l_t(\vec{h}_t) - \frac{1}{T}\sum_{t=1}^Tl_t(\Psi g)\\
                &= \frac{1}{T}\sum_{t=1}^T \left\lvert\langle\Psi g,\Psi F\rangle - \langle\vec{h},\Psi F\rangle\right\rvert\\
                &= \frac{1}{T}\sum_{t=1}^T \left\lvert\mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu\\ z\sim g(x)}}}\left[f_t(x,z,h_t(x))\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu\\z\sim h_t(x)}}}\left[f_t(x,z,h_t(x))\right]\right\rvert\\
                &= \frac{1}{T}\sum_{t=1}^T \left\lvert\mathop{\mathrm{Adv}}_f^t\right\rvert\qquad\textnormal{(4)}
\end{align}
$$

Each term in the final sum of is greater than or equal to $\delta$ by the if condition in . Hence can run for at most $T = O(\left\lvert Z\right\rvert/\delta^2)$ steps before it is no longer possible to find an $f$ satisfying $\left\lvert\mathop{\mathrm{Adv}}_f^t\right\rvert \geq \delta$, as otherwise this would contradict . Thus, the function $h$ output by is $(\delta,\mathcal{F})$\-indistinguishable from $g$, as desired.

For the second condition of the lemma, we can construct a size $O(\left\lvert Z\right\rvert^2/\delta^2)$ circuit for $h$ as follows. On input $x\in X$, the function $h_{t+1}(x)$ can be computed by evaluating $h_t(x,z)+\eta_t\cdot \operatorname{sign}\operatorname{Adv}^t_f f(x,z,h_t(x))$ for each $z\in Z$, and then performing the projection onto $\Delta_Z$. This takes $O(\left\lvert Z\right\rvert)$ evaluations of $f$, one evaluation of $h_t$, and $O(\left\lvert Z\right\rvert)$ time for the projection \[Duchi2008EfficientPO\]. Thus, a circuit to compute the final $h$ returned by can be constructed starting from $h_1$ with size at most $O(T\cdot \left\lvert Z\right\rvert) = O(\left\lvert Z\right\rvert^2/\delta^2)$. ◻

### Soundness ^soundness

Now that we have established that small circuits can produce indistinguishable probabilities for any class of test functions $\mathcal F$, we will leverage to produce the probabilities for $B$ in the Prover-Estimator debate protocol. The main idea is to, given a fixed strategy for $A$, construct $B$’s strategy in each round $k$ via with the function class $\mathcal F$ chosen to be size $q$ circuits that make $q$ queries to $A$. The distribution on inputs for round $k$ is given by the fixed strategies for $A$ and $B$ in prior rounds applied to the original input distribution $\mu$.

**Lemma 15** (Soundness). _For any $\eta > 0$ and any strategy $A \in \mathcal A$ there exists a strategy $B$ computable by circuits of size $O(q 2^{3q}nd^2/\eta^2)$ that may query $A$ at each gate such that 

$$
\mathop{\mathrm{\mathbb{E}}}_{{x \sim \mu}}\left[V^{A,B}(x)\right] < \frac{\mathop{\mathrm{\mathbb{P}}}[A(x) = L(x)]}{\rho^{d+1}} + \eta.
$$

_

_Proof._ We first show that at initialization, we can construct $B$’s strategy so that the probability $\hat p_d$ is indistinguishable by $A$ from the truth, and prove an upper bound on the initial reward $A$ can receive in terms of $\mathop{\mathrm{\mathbb{P}}}[A(x) = L(x)]$.

**Initialization.** Let $X = \{0,1\}^n$ be the set of possible inputs $x$, $Z = \{0,1\}$ be the set of outputs, and $\mathcal{F}$ be the set of functions $f:X \times Z \times \Delta_Z \to [-1,1]$ computable by $O(1)$\-sized circuits that evaluate $A$ once. Let $g:X \to \Delta_Z$ be the function that puts probability 1 on $L(x)$ given input $x$. By there exists a function $h: X \to \Delta_{Z}$ that is $(\delta,\mathcal{F})$\-indistinguishable from $g$, and can be computed by $O(1/\delta^2)$\-sized circuits that can query functions $A\in\mathcal A$ in each step. Let the strategy for $B$ be given by $B(x) = \mathop{\mathrm{\mathbb{P}}}_{z \sim h(x)}[z = 1]$. Note that the initial reward $r_{\textrm{init}}(x,{z}) = {r^{d+1}\cdot \boldsymbol{1}(z = A(x))}$ can be computed by evaluating $A$ once, and performing a constant number of arithmetic operations, hence $r_{\textrm{init}}\in \mathcal{F}$. Therefore by $(\delta,\mathcal{F})$\-indistinguishability of $h$ we have 

$$
\begin{align*}
        \delta &> \left\lvert\mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim\mu\\ {z} \sim h(x)}}}\left[r_{\textrm{init}}(x,{z})\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu\\ {z} \sim g(x)}}}\left[r_{\textrm{init}}(x,{z})\right]\right\rvert\\
            & = \left\lvert\mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim\mu\\ {z} \sim h(x)}}}\left[r_{\textrm{init}}(x,{z})\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim \mu}}}\left[r^{d+1}\cdot\boldsymbol{1}(A(x) = L(x))\right]\right\rvert\\
            & = \left\lvert\mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim\mu}}}\left[r_{\textrm{init}}\right] - r^{d+1}\mathop{\mathrm{\mathbb{P}}}_{\substack{x \sim \mu}}[A(x) = L(x)]\right\rvert.
\end{align*}
$$

 Rearranging yields 

$$
\begin{equation}
        \mathop{\mathrm{\mathbb{E}}}_{{\substack{x \sim\mu}}}\left[r_{\textrm{init}}\right] \leq r^{d+1}\mathop{\mathrm{\mathbb{P}}}_{\substack{x \sim \mu}}[A(x) = L(x)] + \delta.
    \tag{5}
\end{equation}
$$

 We next recursively construct $B$’s strategy as follows. Given fixed strategies for $A$ and $B$ in round $k' > k$, let $\mu_k$ be the distribution on inputs $x$ and queries $y$ in round $k$.

**Recursion.** Let $X = \{0,1\}^{n+n+nq}\times [0,1]$ be the set of input-query sequences $(x,\hat{y}^k,y^k)$ along with the claimed probability $\hat p_k$ from the previous round. Let $Z = \{0,1\}^q$ be the set of query answers $z$. Let $\mathcal{F}$ be the set of functions $f:X\times Z \times \Delta_Z \to [-1,1]$ computable by size $O(nq)$ circuits that make $q$ queries to $A^k$, and define $g_k: X \to \Delta_Z$ by for every $\boldsymbol{x}^k = (x,\hat{y}^k,y^k, \hat p_k) \in X$, 

$$
\mathop{\mathrm{\mathbb{P}}}_{z\sim g_k(\boldsymbol{x}^k)}[z]  = \prod_{i=1}^q \boldsymbol{1}(g(x,y_i) = z_i),
$$

where $g$ is the function that assigns the correct answer to each query $y_i$. implies that there exists a function $h_k:X \to \Delta_Z$ that is $(\delta,\mathcal{F})$\-indistinguishable from $g_k$, and is computable by circuits of size $O(q2^{2q}n/\delta^2)$. We let $B$’s strategy in round $k$ be outputting the entire distribution $h_k(\boldsymbol{x}^k)$, which can be implemented by a circuit of size $O(q2^{3q}n/\delta^2)$.

In every round $k$, the reward $r_k = r^{k}A^k(x,\hat{y}^k, \hat p_k)(M_D(x,y^k,z^k) - \hat p_k)$ can be viewed as a function $r_k(\boldsymbol{x}^k, z^k, h_k(\boldsymbol{x}^k))$ that depends only on inputs $\boldsymbol{x}^k = (x,\hat{y}^k,y^k, \hat p_k) \in X$, the probability distribution $h_k(x) \in\Delta_Z$ produced by $B_i^k$, and query answers $z \in Z$. Since $r_k$ can be computed by running the machine $M_D$ for $O(nq)$ steps, $r_k \in\mathcal F$. Hence by $(\delta,\mathcal F)$\-indistinguishability of $h_k$, 

$$
\begin{align}
        \left\lvert\mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_k\\ z\sim h_k(x)}}}\left[r_k(\boldsymbol{x},z,h_k(\boldsymbol{x}))\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_k\\ z \sim g_k(\boldsymbol{x})}}}\left[r_k(\boldsymbol{x},z,h_k(\boldsymbol{x}))\right]\right\rvert < \delta\qquad\textnormal{(6)}
\end{align}
$$

Recalling that $\hat{y}^k = y^{k+1}_j$ and $z_j^{k+1}$ are the query and answer that $A$ selects for recursion in the previous round $k+1$, and that $\hat p_k = h_{k+1}(\boldsymbol{x}^{k+1})$ is $B$’s previous round probability, the quantity 

$$
\begin{equation}
        f_{k+1}(\boldsymbol{x}^{k+1},z^{k+1},h_{k+1}(\boldsymbol{x}^{k+1})) = r^{k}A^{k}(x,\hat{y}^{k},\hat p_{k})z^{k+1}_j
    \tag{7}
\end{equation}
$$

 can be viewed as function taking inputs in $X \times Z \times \Delta_Z$, and making two queries to $A$ in order to determine the index $j$ on which to recurse as well as the value $A^{k}(x,\hat{y}^{k},\hat p_{k})$. For the base case $k = d$, we abuse notation and let $z^{k+1}_j = \hat{z}$ and $h_{k+1}$ be the function $h$ used to construct the strategy $B(x)$ at initialization. Hence $f_{k+1} \in \mathcal F$. By $(\delta,\mathcal F)$\-indistinguishability of $h_{k+1}$ on the distribution $\mu_{k+1}$, we have that 

$$
\begin{equation}
        \left\lvert\mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim\mu_{k+1}\\ z \sim h_{k+1}(\boldsymbol{x})}}}\left[f_{k+1}(\boldsymbol{x},z,h_{k+1}(\boldsymbol{x}))\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_{k+1}\\ z \sim g_{k+1}(\boldsymbol{x})}}}\left[f_{k+1}(\boldsymbol{x},z,h_{k+1}(\boldsymbol{x}))\right]\right\rvert < \delta
    \tag{8}
\end{equation}
$$

 Next, the definition of $r_k$ and the true answer distribution function $g_k$ imply that for $k \geq 1$ 

$$
\begin{align}
        \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_k\\ z \sim g_k(\boldsymbol{x})}}}\left[r_k(\boldsymbol{x},z,h_k(\boldsymbol{x}))\right] &= \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_k\\ z \sim g_k(\boldsymbol{x})}}}\left[r^{k}A^k(x,\hat{y}^k, \hat p_k)(M_D(x,y^k,z^k) - \hat p_k)\right]\\
        &= \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_k}}}\left[r^{k}A^k(x,\hat{y}^k, \hat p_k)(g(x,\hat{y}^k) - \hat  p_k)\right]\\
        &= \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_{k+1}\\ z \sim g_{k+1}(\boldsymbol{x})}}}\left[f_{k+1}(\boldsymbol{x},z,h_{k+1}(\boldsymbol{x}))\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_{k+1}\\ z \sim h_{k+1}(\boldsymbol{x})}}}\left[f_{k+1}(\boldsymbol{x},z,h_{k+1}(\boldsymbol{x}))\right]\\
        &< \delta     \qquad\textnormal{(9)}
\end{align}
$$

 where the final inequality follows from . Finally, in the base case $k=0$, we force $A$ to produce the subset $\tilde{u}_{S_i}$ of the implicit proof without additional context, and so $A$’s answers at the bottom level must correspond to a single consistent proof $\tilde{u}$. Hence, we have 

$$
\begin{align}
        \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_0\\ z \sim g_0(\boldsymbol{x})}}}\left[r_0(\boldsymbol{x},z,h_0(\boldsymbol{x}))\right] &= \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_0}}}\left[A^0(x,\hat{y}^0,\hat p_0)(\mathcal{O}(\tilde{u}_{S_i}) - \hat p_0)\right]\\
        &\leq \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_0}}}\left[A^0(x,\hat{y}^0,\hat p_0)(g(x,\hat{y}^0) - \hat p_0)\right]\\
        &= \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_{1}\\ z \sim g_{1}(\boldsymbol{x})}}}\left[f_{1}(\boldsymbol{x},z,h_{1}(\boldsymbol{x}))\right] - \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_{1}\\ z \sim h_{1}(\boldsymbol{x})}}}\left[f_{1}(\boldsymbol{x},z,h_{1}(\boldsymbol{x}))\right]\\
        &< \delta.\qquad\textnormal{(10)}
\end{align}
$$

 Combining and with implies that for all $k\geq 0$ 

$$
\begin{equation}
        \mathop{\mathrm{\mathbb{E}}}_{{\substack{\boldsymbol{x}\sim \mu_k\\ z\sim h_k(x)}}}\left[r_k(\boldsymbol{x},z,h_k(\boldsymbol{x}))\right] < 2\delta.
    \tag{11}
\end{equation}
$$

 Summing over the $d$ rounds of the debate and adding the expected $r_{\textrm{init}}$ from gives 

$$
\mathop{\mathrm{\mathbb{E}}}_{{x \sim \mu}}\left[V^{A,B}(x)\right] < r^{d+1} \cdot {\mathop{\mathrm{\mathbb{P}}}[A(x) = L(x)]} + (2d+1)\delta.
$$

 Substituting $r = 1 / \rho$ and setting $\delta = {\eta}/(2d+1)$ completes the proof. ◻

### Completeness ^completeness

In this section we prove the completeness case of . The main idea is that if $x\in L$, for an $\mathcal A$\-provable, sufficiently stable language $L$, the strategy of $A$ correctly outputting proofs $y$ and pointing out inaccurate estimations by $B$ will always yield some positive reward for $A$.

**Lemma 16** (Completeness). _Let $0 < \gamma < \frac{1}{2}$. Suppose $M_D$ is $\mathcal A$\-provable with probability $1-\gamma$ over $x\sim \mu$, which is achieved by a function $A^* \in \mathcal A$. If $M_D$ is also $\rho$\-stable at $x$ w.r.t. $A^*$ with probability $1-\gamma$, then there exists $A \in \mathcal A$ such that for all $B$ (of any size), with probability at least $1 - 2\gamma$ 

$$
\mathop{\mathrm{\mathbb{E}}}_{{}}\left[V^{A,B}(x)\right] \geq \frac{1}{\rho^{d+1}}.
$$

 where $V$ is the verifier for the protocol of and the expectation is over the internal randomness of the protocol only._

_Proof._ We take $A$ to be same as $A^*$ when decomposing the current problem into sub-problems. Therefore, $M_D$ is also $\rho$\-stable at $x$ w.r.t. $A$ with probability $1-\gamma$ over $x \sim \mu$. By a union bound, with probability $1-2\gamma$ over $x \sim \mu$,

-   $M_D$ is $\rho$\-stable at $x$ w.r.t. $A$;
    
-   every sub-problem under the debate tree of $x$ generated by $A$ can be solved by $A$.
    

We now only consider $x$ that satisfies the conditions above. $A$’s strategy is rather simple: In each round $k\leq d$, $A$ always outputs $1$ or $-1$ (for underestimate and overestimate) if the ground truth is $1$ or $0$ respectively. When $B$ outputs its estimation $p_k$, $A$ calculates the marginal probability for each sub-problem, and then chooses the sub-problem where $B$’s estimation (i.e., the marginal probability) is most inaccurate.

Note that if $B$ is honest, the reward $A$ could get is exactly $r^{d+1} = 1/{\rho^{d+1}}$. We now consider $B$ being dishonest strategically and calculate the expected reward $B$ could gain compared to the honest baseline. Let $\varepsilon_{k}$ be the largest estimation error $B$ makes for sub-problems in level $k$. In particular, let $\varepsilon_{d+1}$ be the estimation error $B$ makes at the initialization.

**Initialization level $k = d+1\,$:** If $B$’s estimation is $\varepsilon_{d+1}$ off from the ground truth, he can gain $r^{d+1} \cdot \varepsilon_{d+1}$ in expected reward.

**Intermediate level $k \in [d]\,$:** By symmetry, let us assume the correct value for the current problem $\hat{y}^{k}$ is $0$, and Alice outputs $-1$ claiming that $B$ overestimates the answer. By definition, the expected reward $B$ get for this level is $r^{k} \cdot \left(M_D(x, y^{k}, z^{k}) - \varepsilon_{k+1}\right).$ Since $M_D$ is $\rho$\-stable at $(x, y^{k})$, the expected value of $M_D(x, y^{k}, z^{k})$ is at most $\rho \cdot \varepsilon_{k}$. Therefore, the expected reward $B$ could get at the intermediate level $k$ is $r^{k} \cdot \left(\rho \cdot \varepsilon_{k} - \varepsilon_{k+1}\right)$.

**Bottom level $k = 0\,$:** If $B$’s estimation is off by $\varepsilon_0$ at the bottom level, he will be caught immediately and lose $\varepsilon_0$ of reward.

Now, take the sum of the expected reward $B$ could get for each level, we have

$$
\varepsilon_0 + \sum_{k=1}^d r^{k} \cdot \left(\rho \cdot \varepsilon_{k} - \varepsilon_{k+1}\right) + r^{d+1}\cdot\varepsilon_{d+1} = (r^{d+1} - r^{d}) \cdot \varepsilon_{d+1} ,
$$

 which is a negative value if $\varepsilon_{d+1} > 0$. Therefore, $B$’s best strategy against $A$ is being honest, and in this case $A$ gets $1/{\rho^{d+1}}$ reward. ◻

### Stability and fractional block sensitivity ^stability-and-fractional-block

Interestingly, the $\rho$\-stability condition of is exactly captured by the notion of _fractional block sensitivity_ from boolean function analysis. We first present the formal definition of fractional block sensitivity, and then explain why they are equivalent.

**Definition 17** (Fractional block sensitivity). Let $f : \{0, 1\}^n \to \{0, 1\}$ and $x \in \{0, 1\}^n$. For a nonempty set $B \subseteq [n]$, let $x^B$ denote the string obtained from $x$ by flipping the bits in the coordinates of $B$, i.e., 

$$
(x^B)_i = \begin{cases} 1 - x_i & \textnormal{if } i \in B, \\ x_i & \textnormal{if } i \notin B. \end{cases}
$$

 A set $B \subseteq [n]$ is a sensitive block for $f$ at $x$ if $f(x) \neq f(x^B)$. Write $\mathcal{S}_x(f)$ for the family of all sensitive blocks at $x$.

The fractional block sensitivity of $f$ at $x$ is the optimal value of the linear program 

$$
\mathrm{fbs}_x(f) = \max \left\{ \sum_{B \in \mathcal{S}_x(f)} w_B \;\middle|\; \begin{aligned} w_B &\ge 0 \textnormal{ for all } B \in \mathcal{S}_x(f), \\ \sum_{\substack{B \in \mathcal{S}_x(f) \\ i \in B}} w_B &\le 1 \quad \textnormal{for all } i \in [n] \end{aligned} \right\}.
$$

 The fractional block sensitivity of $f$ is 

$$
\mathrm{fbs}(f) = \max_{x \in \{0, 1\}^n} \mathrm{fbs}_x(f).
$$

_Observation 18_. $M_D$ is $\rho$\-stable at $(x, y)$ if and only if $\mathrm{fbs}_z(M_D(x, y, \cdot)) \le \rho$, where $z$ is the ground truth solution for $(x, y)$.

_Proof._ Fix any $(x, y)$ and $\epsilon$ and assume that the ground truth solution for $(x, y)$ is $\mathbf{0}$ without loss of generality. From Bob’s perspective, choosing a distribution $q$ over $\{0, 1\}^q$ is picking an assignment to $2^q$ variables $\{w_B\}_{B \in \{0, 1\}^q}$, where 

$$
w_B := \mathop{\mathrm{\mathbb{P}}}_{z \sim q} [z = B].
$$

 For each position $i \in [q]$, the marginal probability constraint says that 

$$
\sum_{i \in B} w_B \le \epsilon.
$$

 The probability that Bob flips the correct answer is exactly 

$$
\sum_{B \in \mathcal{S}_x(f)} w_B.
$$

 It is easy to see that this is equivalent to the linear optimization problem for $\mathrm{fbs}_{\mathbf{0}}(M_D(x, y, \cdot))$. ◻

## Proof of ^proof-of-2

The proof of follows from an analysis of Stackelberg equilibria via the soundness and completeness of and .

_Proof of ._ Let $A \in \mathcal A$ and $B \in \mathcal B$ be the respective strategies of debaters $A$ and $B$ in any $\alpha$\-approximate, $A$\-leading Stackelberg equilibrium in the protocol of . Suppose that $A$ is dishonest with probability $\gamma$ i.e. 

$$
\begin{equation*}
        \mathop{\mathrm{\mathbb{P}}}_{x\sim \mu}\left[A(x) \neq L(x) \right] = \gamma > 0
\end{equation*}
$$

 Then by there exists a strategy $B'\in \mathcal B$ , such that 

$$
\begin{equation*}
        \mathop{\mathrm{\mathbb{E}}}_{{x \sim \mu}}\left[ V^{A,B',\mathcal{O}}(x) \right] \leq \frac{1-\gamma}{\rho^{d+1}} + \eta.
\end{equation*}
$$

 The definition of $\alpha$\-approximate Stackelberg equilibrium then implies that 

$$
\begin{equation}
        \mathop{\mathrm{\mathbb{E}}}_{{x \sim \mu}}\left[ V^{A,B}(x) \right] \leq \frac{1-\gamma}{\rho^{d+1}} + \eta + \alpha.
    \tag{12}
\end{equation}
$$

 On the other hand, by we have that there exists a strategy $A'\in\mathcal A$ such that even for the best response $B^* \in \mathcal B$ to $A'$, the expected reward is at least 

$$
\begin{equation}
        \mathop{\mathrm{\mathbb{E}}}_{{x \sim \mu}}\left[V^{A',B^*,\mathcal{O}}(x)\right] \ge \frac{1}{\rho^{d+1}} - \frac{2\epsilon}{\rho^{d+1}}
    \tag{13}
\end{equation}
$$

 Then by the definition of an $\alpha$\-approximate Stackelberg equilibrium, followed by an application of and we have 

$$
\begin{align*}
        \alpha &\geq  \mathop{\mathrm{\mathbb{E}}}_{{x \sim \mu}}\left[V^{A',B^*,\mathcal{O}}(x)\right] - \mathop{\mathrm{\mathbb{E}}}_{{x \sim \mu}}\left[ V^{A,B}(x) \right]\\
            &> \frac{1}{\rho^{d+1}} - \frac{2\epsilon}{\rho^{d+1}} - \frac{1-\gamma}{\rho^{d+1}} - \eta - \alpha..
\end{align*}
$$

 Rearranging and using $\eta = \epsilon/ \rho^{d+1}$, $\alpha < \frac{\epsilon}{\rho^{d+1}}$ completes the proof: 

$$
\gamma \le 2{\epsilon} + \eta{\rho^{d+1}} + 2\alpha{\rho^{d+1}} < 5\epsilon.
$$

 ◻

## Recommendations for empirical debate ^recommendations-for-empirical-debate

We make several qualitative recommendations for empirical debate based on our new protocol:

##### Asymmetry between the debaters. ^asymmetry-between-the-debaters

Much empirical work on debate thus far has had symmetric debaters, distinguished only by which debater speaks first. Our protocol suggests that it is useful to have asymmetry between the debaters. The debater $A$ should be tasked with proposing a solution and providing evidence to defend it, while debater $B$ should attempt to identify flaws, and evaluate the plausibility of the evidence. This setup also makes sense for empirical debate research on open-ended tasks, as the first debater will need to propose a solution and then defend its correctness.

##### Explicit uncertainty estimates. ^explicit-uncertainty-estimates

Our protocols rely heavily on the ability to ask the estimator $B$ to produce probability estimates for subclaims that arise in the debate. The payoffs are also determined by these estimates. In a practical setting one could use multiple samples from a generative model to produce uncertainty estimates, or directly use token probabilities of the answer from an LLM. For example, after an LLM $A$ generates an argument, one could prompt both $A$ and opposing LLM $B$ to read through the argument step-by-step, and at each step answer whether the claim seemed true. Token probabilities could then be compared between $A$ and $B$ for the truth of each claim.

##### Game theoretically motivated training algorithms. ^game-theoretically-motivated-training

We depart from prior theoretical work on debate by considering different game theoretic equilibrium concepts to reason about our protocols. The leader-follower structure implies that for every training update made to $A$, we should make multiple updates to $B$. This ensures that whenever $A$ receives a gradient update, it comes from an episode of debate where $B$ is playing an approximate “best response” to $A$’s current strategy. This type of training algorithm makes particular sense in the asymmetric setting where $A$ is proposing a complex solution to some problem, and is asked to defend the solution. In this case, we would like to train $B$ to ensure the ability to identify flaws in $A$’s solutions, before providing a new update to $A$.

[^note-2]: An earlier preprint had an error in the main theorem due to an issue with the way stability was defined. At a high level, the corrected definition bounds changes in marginal probabilities of subclaims, while the original mistaken definition used conditional probabilities. This error was found and fixed by the last three authors.

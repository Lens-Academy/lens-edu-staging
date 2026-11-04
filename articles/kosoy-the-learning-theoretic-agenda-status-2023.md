---
title: "The Learning-Theoretic Agenda: Status 2023"
author:
  - "Vanessa Kosoy"
source_url: "https://www.lesswrong.com/posts/ZwshvqiqCvXPsZEct/the-learning-theoretic-agenda-status-2023"
published: 2023-04-19
created: 2026-11-04
accessed: 2026-11-04
llm-review:
  date: 2026-11-04
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-11-04
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

**TLDR:** I give an overview of (i) the key problems that the learning-theoretic AI alignment research agenda is trying to solve, (ii) the insights we have so far about these problems and (iii) the research directions I know for attacking these problems. I also describe "Physicalist Superimitation" (previously knows as "PreDCA"): a hypothesized alignment protocol based on infra-Bayesian physicalism that is designed to reliably learn and act on the user's values.

_I wish to thank Steven Byrnes, Abram Demski, Daniel Filan, Felix Harder, Alexander Gietelink Oldenziel, John S. Wentworth_[^note-1] _and my spouse Marcus Ogren for reviewing a draft of this article, finding errors and making helpful comments and suggestions. Any remaining flaws are entirely my fault._ 

# Preamble ^preamble

I already [described](https://www.lesswrong.com/posts/5bd75cc58225bf0670375575/the-learning-theoretic-ai-alignment-research-agenda) the learning-theoretic agenda (henceforth LTA) in 2018. While the overall spirit stayed similar, naturally LTA has evolved since then, with new results and research directions, and slightly different priorities. This calls for an updated exposition.

There are several reasons why I decided that writing this article is especially important at this point:

-   Most of the written output of LTA focuses on the technical, mathy side. This leaves people confused about the motivation for those inquiries, and how they fit into the big picture. I find myself having to explain it again and again in private conversations, and it seems more efficient to have a written reference.
-   In particular, LTA is often conflated with infra-Bayesianism. While infra-Bayesianism is a notable part, it is not the only part, and without context it's not even clear why it is relevant to alignment.
-   Soares has recently [argued](https://www.lesswrong.com/posts/4ujM6KBN4CyABCdJt/ai-alignment-researchers-don-t-seem-to-stack) that alignment researchers don't "stack", meaning that it doesn't help much to add more researchers to the same programme. I think that for LTA, this is not at all the case. On the contrary, there is a variety of shovel-ready problems that can be attacked in parallel. With this in mind, it's especially important to explain LTA in order to get more people on board.
-   In particular, ALTER has announced a [prize](https://www.lesswrong.com/posts/8BL7w55PS4rWYmrmv/prize-and-fast-track-to-alignment-research-at-alter) designed to encourage work on LTA. I expect this article to be a useful resource for researchers who decide to compete.
-   It seemed important to explain Physicalist Superimitation better, and this is hard to do without the broader context.

I am fairly optimistic that LTA leads to a solution to alignment. On the other hand, it's much harder to say whether the solution will arrive in time. I think that the rate of progress relative to person-hours invested was pretty good so far, and we didn't hit any obstacle that cast doubt on the entire endeavor. At the same time, in _absolute_ terms we still have most of the work in front of us. In the coming years, I am planning to put considerable effort into scaling up: getting more researchers on board, and hopefully accelerating progress by a significant factor.

# Philosophy ^philosophy

_The philosophy of LTA was_ [_covered_](https://www.lesswrong.com/posts/5bd75cc58225bf0670375575/the-learning-theoretic-ai-alignment-research-agenda#Philosophy) _in the original article, I mostly stand behind what I wrote there and don't want to repeat it. The goal of this section is merely to recap and add a couple of points._

The goal of LTA is creating a general mathematical theory of intelligent agents. There are a number of reasons why this is necessary for AI alignment:

-   Having a mathematical theory enables constructing models in which we can prove that a particular AI design is aligned (or unaligned), or at least form rigorous and strongly supported conjectures (similar to the role $\mathrm{P}\ne\mathrm{NP}$  in cryptography). While such a proof doesn't imply absolute confidence, it does allow us to reduce the problem to becoming confident in the _assumptions_ of the model. This is a much better situation than dealing with a sequence of heuristic steps, each of which might be erroneous and/or hiding assumptions that are not stated clearly. Of course, similarly to how in cybersecurity having a provably secure protocol doesn't protect you from e.g. someone using their birthday for a password, here too we will need to meticulously verify that the assumptions hold in the actual implementation. This might require knowledge from domains outside of theoretical computer science, e.g. physics, cognitive science, evolutionary biology etc.
-   Empirical data is insufficient in itself, since without an underlying theory it's very hard to be confident about how the results extrapolate to new domains, scales, architectures and algorithms. On the other hand, the combination of theory and experiment can be extremely powerful for such extrapolation, even if the theory cannot produce quantitative predictions ab initio on its own.
-   Even if we don't do any explicit calculations using the theory about the AI we are designing, merely knowing the theory leads to much better intuitions, and equips us with the right vocabulary to reason about the problem. To give an analogy, it is much easier to reason about designing engines if you're familiar with concepts such as "heat", "work", "temperature", "entropy", even if you're just reasoning informally rather than actually calculating.

After I wrote the original article about LTA, more was written about the feasibility and importance of mathematics for alignment, both [by](https://www.lesswrong.com/posts/suxvE2ddnYMPJN9HD/realism-about-rationality?commentId=uGePTr7mcjhS9sDJY) [me](https://www.lesswrong.com/posts/qpbYwTqKQG8G7mdFK/the-reasonable-effectiveness-of-mathematics-or-ai-vs) and by [others](https://www.lesswrong.com/posts/Gg9a4y8reWKtLe3Tn/the-rocket-alignment-problem).

Why is LTA concerned specifically with agents? Aren't there AI systems which are not agents? The reason is: the sort of risks I want to address are risks that arise from AIs displaying agentic behavior (i.e. building sophisticated models of the world and using these models to construct plans that pursue unaligned goals, with catastrophic consequences), and the sort of solution I envision also relies on AIs displaying agentic behavior (i.e. building sophisticated models of the world and using these models to construct plans that pursue an aligned goal, s.t. the result is protecting humanity from unaligned AI).

Finally, I want to address a common point of confusion. Sometimes I tell someone about subproblems in LTA and they respond by trying to understand why each individual subproblem (e.g. nonrealizability, or cartesian privilege, or value ontology) is relevant to alignment. Often there _are_ some specific ways in which the subproblem can be connected to alignment. But the more important point is that _any_ fundamental question about intelligent agency is relevant to alignment, just because without answering this question we cannot understand intelligent agency. For any aspect of intelligent agency that we don't understand and any AI that we design, one of the two will hold: either the AI lacks this aspect, in which case it is probably insufficient to protect humanity, or the AI has this aspect but we don't understand why or how, in which case it is probably unaligned (because alignment is a small target, and significant unaccounted for phenomena are likely to make you miss).

# Key Problems ^key-problems

The starting point of LTA is Marcus Hutter's [AIXI](https://link.springer.com/book/10.1007/b138233): a simplistic model of ideal agency.

Intuitively, an "intelligent agent" is a system that builds sophisticated models of the world and uses them to construct and execute plans that lead to particular goals (see also [Yudkwosky](https://www.lesswrong.com/posts/yLeEPFnnB9wE7KLx2/efficient-cross-domain-optimization)). Building models implies starting from a state of ignorance and updating on observations, which can be formalized by Bayesian probability theory. Building sophisticated models requires using Occam's razor, which can be formalized by the [Solomonoff prior](http://www.scholarpedia.org/article/Algorithmic_probability). Constructing and executing plans can be formalized as maximizing expected utility. Putting all these ingredients together gives us AIXI.

However, there are both important gaps both in our understanding of AIXI-like agents, and significant weaknesses in the AIXI framework itself. Solving these problems is the natural framing for the entire foundational[^note-2] part of LTA.

## Problem 1: Computational Resource Constraints ^problem-1-computational-resource

AIXI is uncomputable. Obviously, real-world agents are not only computable but operate under strong computational resource constraints. This doesn't mean AIXI is not a useful _toy model_ for studying the interaction of Occam's razor with Bayesian optimization or reinforcement learning. However, it _is_ a major limitation.

One obvious attempted solution is to impose some computational resource constraints on the programs that appear in Solomonoff's prior, for example as in Schmidhuber's [speed prior](https://people.idsia.ch/~juergen/speedprior.html) or in some other way. This typically leads to agents that are computable but still computationally intractable. Relatedly, a recent [line of research](https://arxiv.org/abs/2009.11514) connects the hardness of time-bounded Kolmogorov complexity with the existence of one-way functions.

On the other hand, we know some priors for which asymptotic Bayes-optimality is possible in polynomial time, for example priors supported on Markov decision processes (MDPs) with a small (i.e. polynomial in the security parameter) number of states. Some stronger feasible models are also known, e.g. MDPs with linear features or kernel-MDPs. However, all such priors have significant shortcomings:

-   They require the MDP to be communicating, i.e. contain no irreversible transitions (a.k.a. "traps"). This is obviously not true in the real-world, where e.g. jumping off a cliff is often irreversible. Indeed, without this assumption approximating the Bayes-optimal policy is [NP-hard](https://cstheory.stackexchange.com/questions/41396/is-bayes-optimal-rl-of-a-finite-set-of-dfas-feasible), even for a small number of deterministic hypotheses.
-   They usually don't embody any sort of Occam's razor.
-   They are not rich enough to capture sophisticated models of the real world.

## Problem 2: Frequentist Guarantees ^problem-2-frequentist-guarantees

AIXI is Bayes-optimal (by definition) but is not necessarily optimal in any sense for any particular environment. In contrast, in statistical learning theory we usually demand a _frequentist_ guarantee, i.e. that a learning algorithm converges to optimality (in some sense) for any[^note-3] data source (subject to some assumptions which depend on the setting). Such guarantees are important for several reasons:

-   _Learning_ is a key ability of intelligent agents, and played a fundamental role in AI progress in recent decades. A natural way to operationalize learning is: an agent learned a fact when its behavior is optimal conditional on this fact. In other words, learning which of a set of hypotheses is true means converging to optimal behavior for the true hypothesis, i.e. precisely a frequentist guarantee. This means that a theory of frequentist guarantees tell us both _which_ facts agents can learn and how _fast_ they learn them (or how much data they require to learn them). These are important questions that a theory of intelligent agents has to answer. In particular, it is required to analyze the feasibility of alignment protocols: e.g. if we expect the AI to learn human values, we need to make sure it has sufficient information to learn them within a practical time frame.
-   A Bayes-optimal algorithm does well on average across some large ensemble of possible universes. But in reality, we only observe one universe (which is not even in the ensemble: see Subproblem 2.3 below). Without frequentist guarantees, it's not clear why would a Bayes-optimal algorithm do especially well in our specific universe, or why should algorithms that do well in our specific universe be Bayes-optimal.
-   Evolution selected humans by their performance in the ancestral environment, which involved e.g. gathering berries and running away from lions. But they turned out to perform reasonably well in very different environments that require e.g. writing code or designing rockets. This hints at the existence of some underlying frequentist guarantee as a key property of intelligent agents.

Moreover, in addition to single-agent frequentist guarantees it is desirable to derive _multi-agent_ frequentist guarantees. Interactions between agents are quite important in the real-world, and have significance specifically for AI alignment as well (AI-human, AI-other AI, AI-acausal trade partner, to some extent human-human too). A multi-agent frequentist guarantee can take the form of convergence to a particular game-theoretic solution concept, or an asymptotic lower bound on expected utilities corresponding to some notion of game value.

There are multiple difficulties in deriving frequentist guarantees for AIXI-like agents. The first two difficulties ("traps" and "password guessing games" below) are not problems with the agent, but rather with the way conventional frequentist guarantees are defined (which are nonetheless non-trivial to solve). The third difficulty (nonrealizability) might be a problem with the way the agent is defined.

### Subproblem 2.1: Traps ^subproblem-2-1-traps

The most common type of frequentist guarantee in reinforcement learning (RL) is regret bounds[^note-4]. However, AIXI doesn't satisfy any regret bound w.r.t. the underlying hypothesis class (i.e. the class of all computable environments) because these hypotheses involve irreversible transitions (traps). For example, suppose that in environment 1 taking action A sends you to a sink state with reward $-1$, whereas taking action B sends you to a sink state with reward $+1$, and in environment 2 the opposite is true. Obviously a hypothesis class which contains both environments doesn't admit a regret bound.

This problem is especially acute in the multi-agent setting, because other agents have memory. Either it's impossible to erase memory in which case the environment is irreversible by design, or it's possible to erase memory which breaks conventional learning theory in other ways.

### Subproblem 2.2: Password guessing games ^subproblem-2-2-password

What if we arbitrarily rule out traps? Consider an agent with action set $\mathcal{A}$ and observation set $\mathcal{O}$. Suppose that the reward is a function of the last observation only $r:\mathcal{O}\rightarrow\mathbb{R}$. We can specify an environment[^note-5] $\mu:(\mathcal{O}\times\mathcal{A})^*\rightarrow\Delta\mathcal{O}$ by providing a communicating MDP with state set $\mathcal{S}$ and action set $\mathcal{B}$ augmented by representation mappings

$$
\sigma: (\mathcal{O}\times\mathcal{A})^*\times\mathcal{O}\rightarrow\mathcal{S}
$$

$$
\alpha:  (\mathcal{O}\times\mathcal{A})^*\rightarrow\mathcal{B}
$$

$$
\omega: \mathcal{S}\rightarrow\mathcal{O}
$$

Here, $\alpha(ha)$ is required to be an onto mapping from $\mathcal{A}$ to $\mathcal{B}$ for any $h\in(\mathcal{O}\times\mathcal{A})^*\times\mathcal{O}$. Also, we require that for any $h\in(\mathcal{O}\times\mathcal{A})^*$ and $o\in\mathcal{O}$

$$
\omega(\sigma(ho))=o
$$

However, this only enables a fairly weak regret bound. Naively, it seems reasonable to expect a regret bound of the form $\tilde{O}(K^\alpha \tau^\beta T^\delta)$ where $K$ is the Kolmogorov complexity of the MDP+representation, $\tau$ is the diameter[^note-6] and $T$ is the time horizon[^note-7], and $\alpha,\beta,\delta$ are constants s.t. $\delta<1$. Indeed, $K$ can be regarded as the amount of information that needs to be learned and e.g. [Russo and Van Roy](https://arxiv.org/abs/1403.5341) showed that in a bandit setting regret scales as the square root of the entropy of the prior (which also expresses the amount of information to be learned). However, this is impossible, as can be seen from the following example.

Fix $n\in\mathbb{N}$ and $p\in\{0,1\}^{n+1}$ (the "password"), let the action set be $\mathcal{B}:=\{0,1\}$ and the state space be $\mathcal{S}:=\{0,1\}^{\leq n} \sqcup \{\top\}$. We think of a state $s\in\{0,1\}^{\leq n}$ as "the agent entered the string of bits $s$ into the terminal". The initial state is $\epsilon$ (the empty string). The transition kernel works as follows:

In state $s\in\{0,1\}^{<n}$, taking action $i$ produces the state $si$ (i.e. the agent enters the digit $i$). In state $s\in\{0,1\}^n$, taking action $i$ produces the state $\top$ if $si=p$ (the agent entered the correct password) or state $\epsilon$ (the agent entered an incorrect password and has to start from the beginning). In state $\top$ taking action $0$ stays in state $\top$ and taking action $1$ produces state $\epsilon$ (restarts the game).

All states have reward $0$ except for the state $\top$ which has reward $1$.

Obviously the agent needs time $2^n$ to learn the correct password, in expectation w.r.t. the uniform distribution over passwords. At the same time, $K\approx n$ and $\tau=n+1$. This is incompatible with having a regret bound of the desired form.

### Subproblem 2.3: Nonrealizability ^subproblem-2-3-nonrealizability

As we discussed in Problem 1, a realistic agent cannot be Bayes-optimal for a prior over all computable environments. Typically, each hypothesis in the prior has to admit a computationally feasible approximately optimal policy in order for it to be feasible to approximate Bayes-optimality (in particular this has to be the case if the prior is learnable), which usually implies the hypotheses are computationally feasible to simulate[^note-8]. However, in this situation we can no longer assume the true environment is within the hypothesis class. Even for AIXI itself, it is not really fair to assume the environment is computable since that would exclude environments that contain e.g. other AIXIs.

A setting in which the true environment is not in the hypothesis class is known in learning theory as "nonrealizable". For offline (classification/regression) and online learning, there is a rich theory of nonrealizable learning[^note-9]. However, for RL (which, among classical learning theory frameworks, is the most relevant for agents), the nonrealizable setting is much less understood (although there are some results, e.g. [Zanette et al](https://arxiv.org/abs/2003.00153)).

Therefore, even if we arbitrarily assume away traps, and are willing to accept a factor of $2^K$ in the regret bound, a satisfactory theory of frequentist guarantees would require good understanding of nonrealizable RL.

This problem is also especially acute in the multi-agent case, because it's rarely the case that each agent is a realizable environment from the perspective of the other agent (roughly speaking, if Alice would simulate Bob simulating Alice, Alice would enter an infinite loop). This is known as the "grain of truth" problem[^note-10]. One attempt to solve the problem is by [Leike, Taylor and Fallenstein](https://arxiv.org/abs/1609.05058), using agents that are equipped with "reflective oracles". However, there are many different reflective oracles, and the solution relies on all agents in the system to use the same one, i.e. that the design of the agents has been essentially centrally coordinated to make them compatible.

## Problem 3: Value Ontology ^problem-3-value-ontology

AIXI's utility function depends on its direct observations. This is also assumed in RL theory. While this might be a legitimate type of agent, it is insufficiently general. We can easily imagine agents that place value on parameters they don't directly observe (e.g. the number of paperclips in the observable universe, or the number of people who suffer from malaria). Arguably, humans are such agents.

The obvious workaround is to translate the utility function from its original domain to observations by taking a conditional expectation. That is, suppose the utility function is $U:X\rightarrow\mathbb{R}$ for some space $X$, let $D$ be the space of everything that is directly observed (e.g. action-observation time sequences) and suppose we have some prior over $X \times D$. Then, we can define $U':D\rightarrow\mathbb{R}$ by

$$
U'(d):=\mathrm{E}\left[U(x)\middle|d\right]
$$

However, there are problems with this:

-   In order to have reasonable computational complexity and frequentist guarantees, we will need to make assumptions about the utility function. While such assumptions can be natural for $U$, they make much less sense for $U'$ unless we can somehow justify them via the prior over $X \times D$. Without a theory that explicitly talks about $U$ and $D$ it is impossible to know whether such justification is possible.
-   Even if $U'$ satisfies the required assumptions, a frequentist guarantee about $U'$ does not necessarily imply an analogous frequentist guarantee about $U$. That's because the transformation above involves taking expected value which implicitly mixes different "possible universes", while a frequentist guarantee is supposed to refer to a particular universe.
-   Different agents have different observation spaces and there is no natural joint prior on all of them. This means it's impossible to talk about different agents having "aligned" preferences.

Therefore, it is desirable to have a theory in which it is possible to explicitly talk about utility functions with domains other than observations. (See also [de Blanc](https://intelligence.org/files/OntologicalCrises.pdf).)

## Problem 4: Cartesian Privilege ^problem-4-cartesian-privilege

The formalization of Occam's razor in AIXI relates to the description complexity of hypotheses represented in terms of the agent's actions $\mathcal{A}$ and observations $\mathcal{O}$ (as functions $(\mathcal{O}\times\mathcal{A})^*\rightarrow\Delta\mathcal{O}$). However, this is not how Occam's razor is used in science. When we talk about a "simple" or "elegant" scientific theory, we refer to the equations governing the fundamental degrees of freedom on that theory (e.g. particles, or fields or strings), _not_ to the equations that would be needed to describe the RGB values of points on a person's retina. Indeed, expressing physics via the latter equations would be horrifically complicated.

In other words, AIXI-like agents believe they occupy a privileged position in the universe, which has various pathological consequences. See "[infra-Bayesian physicalism](https://www.lesswrong.com/posts/gHgs2e2J5azvGFatb/infra-bayesian-physicalism-a-formal-theory-of-naturalized)" for more discussion and [Demski and Garrabrant](https://arxiv.org/abs/1902.09469) for related prior work.

## Problem 5: Descriptive Agent Theory ^problem-5-descriptive-agent

The framing of AIXI is: given certain subjective choices (e.g. universal Turing machine and utility function), what is an ideal agent? However, in the real-world agents are not ideal. Moreover, we want to be able to understand which systems are agents, and what kind of agents they are, without already assuming e.g. a specific utility function. In particular, such a theory would have applications to:

-   Value learning, by regarding humans as agents.
-   Studying "accidental" formation of agents, e.g. via evolution or as mesa-optimizers (related: Wentworth's [selection theorems](https://www.lesswrong.com/posts/G2Lne2Fi7Qra5Lbuf/selection-theorems-a-program-for-understanding-agents) programme).

[Legg and Hutter](https://arxiv.org/abs/cs/0605024) defined an intelligence measure that for every policy produces a number determining its intelligence, s.t. AIXI has maximal intelligence. The measure is essentially the policy's expected utility w.r.t. the Solomonoff prior. This allows us to talk how close any given system is to an ideal agent. However, it suffers from two major limitations (in addition to the other problems of AIXI discussed before):

-   It depends on the choice of universal Turning machine (UTM). While the same is true of everything in algorithmic information theory, usually we have theorems that limit this dependence. For example, Kolmogorov complexity only changes by $O(1)$ when we switch to a different UTM. On the other hand, the Legg-Hutter measure doesn't have any such property (except in the asymptotic in which it approaches 0, which is pretty meaningless).
-   It depends on the choice of utility function. Technically, they don't make an explicit choice but instead assume the reward is one of the observation channels. In practice, this _is_ a choice (and a very restrictive one).

Moreover, naive attempts to ascribe a utility function to a policy run into difficulties. Specifically, any policy can arguably be ascribed a utility function which rewards following precisely this policy. With respect to such a utility function, the policy is Bayes-optimal for any prior. [Armstrong and Mindermann](https://arxiv.org/abs/1712.05812) have argued on the basis of this type of reasoning that ascribing a utility function is essentially impossible in a purely behaviorist framework (but I argue the opposite, see [[#^direction-17-5-inferring|Direction 17.5]] below).

## Nonproblem: Expected Utility ^nonproblem-expected-utility

Finally, I want to briefly discuss one issue which I _don't_ consider a key problem. Namely, the reliance of AIXI on expected utility maximization.

Expected utility is often justified by coherence theorems such as [von Neumann–Morgenstern](https://en.wikipedia.org/wiki/Von_Neumann%E2%80%93Morgenstern_utility_theorem) (VNM) and Savage. These theorems are indeed important: they show that a small number of natural assumptions produce a fairly narrow mathematical object (expected utility). This should indeed increase our credence in expected utility as a useful model. Often, objections are put forward that argue with individual assumptions. IMO these objections miss the point: a coherence theorem is a piece of evidence, not a completely watertight proof that expected utility is philosophically correct. And, if expected utility is philosophically correct, such a watertight proof is still not something we should expect to exist (what would it even look like?)

The more important justification of expected utility is the large body of work it supports: control theory, game theory, reinforcement learning theory etc. The methodology I believe in is, start with _plausible_ assumptions and try to build a theory. If the theory that results is rich, has synergy with other bodies of knowledge, has explanatory power, is useful in practice, each of these is evidence that it's on the right track. (And if we failed to build such a theory, we probably also learned something.)

Another objection that is often raised is "humans have no utility function". This is ostensibly supported by research in behavioral economics which shows that humans behave irrationally. I consider this deeply unconvincing. For one thing, I suspect that a large part of that research doesn't replicate. But even putting that aside, the interesting thing about irrational behavior is that we _recognize_ it as irrational: i.e. learning about it makes you behave differently (unless it's so minor that it isn't worth the effort). This already indicates that this irrationality is better viewed not as a fundamental fact about human preferences, but as some combination of:

-   Computational or informational resource constraints
-   Error terms that vanish in the relevant asymptotic regime
-   Random noise or some other effect that's not part of the cognitive algorithm

All of this is not to say that expected utility cannot be questioned. Rather that a _productive_ objection would be to either come up with a demonstrably superior alternative, or at least a good argument why some extremely _concrete_ problem cannot be solved without an alternative to expected utility. Lacking that, the best strategy is to press forward unless and until we encounter such a problem.

Now, we actually _do_ have examples where deviating from purist VNM in specific ways is useful, e.g.:

-   [Infra-Bayesianism](https://www.lesswrong.com/posts/zB4f7QqKhBHa5b37a/introduction-to-the-infra-bayesianism-sequence), where the conventional notion of "expectation" is replaced by some non-linear concave functional.
-   Taylor's [quantilization](https://intelligence.org/files/QuantilizersSaferAlternative.pdf), where instead of _maximizing_ expected utility we sample a random choice out of some top fraction of choices.
-   [Nash bargaining](https://en.wikipedia.org/wiki/Cooperative_bargaining), where we maximize the product of several expected utilities (see also Garrabrant's "[geometric rationality](https://www.lesswrong.com/s/4hmf7rdfuXDJkxhfg)" sequence).

However, these examples came about from studying various concrete problems, not from arguing with the VNM model per se. Moreover, all of these examples can still be mathematically recast in VNM form: infra-Bayesianism can be regarded as a VNM zero-sum game (against "Murphy"), quantilization and Nash bargaining can be regarded as special cases of infra-Bayesianism (as will be discussed in an ~upcoming~ [article](https://www.lesswrong.com/posts/d96dDEYMfnN2St3Bj/infrafunctions-and-robust-optimization) by Appel). Therefore, even here the theory built around the VNM model remains useful.

# Research Directions ^research-directions

This section focuses entirely on the foundational part of the programme. I will mention some of the applied part in the next section (although different applications are also possible, e.g. studying quantilization or IDA), but for the most part I believe the foundational part to be the top priority.

In the following, I roughly grouped the research directions by the problems they are trying to address. However, the real relationship between directions and problems is many-to-many: a single direction can have implications on many problems. Moreover, there are many connections between the different directions. And, even for directions that are not especially connected at present, if they are successful, we will be faced with the task of merging them into a unified theory.

## Subproblem 1.1: Frugal Universal (Infra-)Prior ^subproblem-1-1-frugal

One part of solving Problem 1 (computational resource constraints) is finding a prior (more precisely a family of priors) with the following properties:

-   Formalizes Occam's razor, i.e. assigns higher probability to hypotheses that are simpler to describe.
-   Sufficiently rich to contain sophisticated models applicable to the real-world.
-   The (approximately) optimal policy for each hypothesis is feasible to find. Possible operationalization of "feasible": polynomial time in history length and description length of hypothesis.
-   If we assume away traps, there is a feasible learning algorithm with a good regret bound. Possible operationalization: polynomial time in history length, regret bound similar to what was described in section "Problem 2.2" above. (This desideratum is probably strictly stronger than the previous bullet point.)

More generally, we might want an infra-prior (see [[#^direction-3-infra-bayesian-rl|Direction 3]] below), or a metacognitive (infra-)prior (see [[#^direction-6-metacognitive-agents|Direction 6]] below), or a physicalist infra-prior (see [[#^direction-18-infra-bayesian-physicalism|Direction 18]] below) with analogous properties.

### Direction 1: Frugal Compositional Languages ^direction-1-frugal-compositional

The time complexity of finding the optimal policy for a generic (tabular) MDP scales with its number of states. The same is true of the sample complexity of learning an unknown generic MDP. However, the number of states in a sophisticated model of the real world has to be enormous. For example, if I reason about the world as it's comprised of $n$ objects with $m$ possible states each, the over number of states is already $m^n$.

Therefore, any realistic RL algorithm has to exploit some _structure_ in its environment. For example, the environment might be comprised of spatially separated parts, or different processes happening on different spatial scales, or different processing happening on different temporal scales. We want to find an appropriate _compositional language_ for describing such structure.

The compositional language used by AIXI is that of programs for some fixed UTM. This language is very powerful, but also unfeasible to work with, because programs can consume arbitrarily large amounts of computational resources or even fail to halt altogether. Imposing ad hoc computational resource bounds also doesn't work well, perhaps because such bounds are extraneous to the compositional properties of the language.

Arguably we need some new "frugal" compositional language. Here are the candidate starting points I currently know. It is possible that the right answer will involve combining several of them.

**Direction 1.1: Compositional Polytope-MDPs**

[Compositional polytope-MDPs](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=cusSXZSYskdfAH8wX) is a language with two operations: union of asynchronous noninteracting parts and time hierarchy. Importantly, the optimal policy is computable in time polynomial in description length. The time hierarchy operation also offers a natural formalization for the notion of "instrumental values".

Further research might involve:

-   Incorporating the state/action representation into the semantics.
-   Proving regret bounds for hypotheses classes based on this language, first with arbitrary and then with computationally efficient algorithms.
-   Extending the language with more operations.
-   Creating an infra-Bayesian version.

**Direction 1.2: String Machines (for RL)**

[String machines](https://www.lesswrong.com/posts/jxE47v3aezEYaydg9/compositional-language-for-hypotheses-about-computations) is a category-theoretic framework that allows constructing automata and transducers from string diagrams[^note-11] (that can be probabilistic). In particular, it can be used to describe MDPs. In fact, there is a version of it that allows constructing arbitrary Turing machines, but there are natural ways to "throttle" to expressiveness of the language.

Further research might involve:

-   Understanding the expressiveness of the language better, in terms of complexity classes and maybe parameterized complexity classes. \[**EDIT:** See also initial foray using [filtered string machines](https://www.lesswrong.com/posts/zy2AECRAi8Nuu5XMk/introducing-complexity-constraints-and-establishing).\]
-   In particular, understanding how it depends on the categories used.
-   Studying control/learning algorithms for hypotheses based on the language.

**Direction 1.3: Infra-Bayesian Logic**

[Infra-Bayesian logic](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=6BhuJdyMScbyQeeac) is a sort of higher-order logic where the semantics has infradistributions instead of sets corresponding to predicates, and can be viewed as a synthesis of logic and probability theory. In particular, it is fairly natural for describing infra-(PO)MDPs because the main part of the latter is the transition infrakernel.

However, the semantics are not fully defined because of some technical difficulties. There is also a first-order version which _is_ fully defined but seems less natural for describing RL hypotheses. Finally, there are hints that propositional infra-Bayesian logic might be more computationally tractable than classical propositional logic, but it's as yet [unclear](https://www.lesswrong.com/posts/cYJqGWuBwymLdFpLT/non-unitary-quantum-logic-seri-mats-research-sprint).

### Direction 2: Deep Learning Theory ^direction-2-deep-learning

It seems plausible that deep learning algorithms (e.g. transformers) are already learning algorithms for the frugal universal prior. Therefore, building a rigorous theory of deep learning (in particular, its inductive biases and generalization properties) is another potential path to understanding this prior and its properties.

While this is a relevant research direction, I don't prioritize it for two reasons:

-   It already receives a lot of attention in mainstream academia (some [examples](https://www.lesswrong.com/posts/pcomQ4Fwi7FnfBZBR/how-does-gradient-descent-interact-with-goodhart?commentId=347zabMr2Cy3S6dy7), another interesting approach is [singular learning theory](https://www.lesswrong.com/s/mqwA5FcL6SrHEQzox)).
-   Substantial breakthroughs here might have major capability implications. (Although this is a consideration that might be relevant to some other directions in LTA as well.)

Nevertheless, it is a type of research that has implications on LTA and alignment researchers can reasonably consider to participate in it, if they feel especially well positioned for it and have the discipline and judgement required to self-censor if necessary.

## Subproblem 2.3: Nonrealizability ^subproblem-2-3-nonrealizability-2

The research directions below are different ways to get frequentist guarantees in the nonrealizable setting, but they are not necessarily mutually incompatible. In addition to exploring each approach separately, it can be interesting to study various combinations.

### Direction 3: Infra-Bayesian RL ^direction-3-infra-bayesian-rl

[Infra-Bayesian RL](https://www.lesswrong.com/posts/zB4f7QqKhBHa5b37a/introduction-to-the-infra-bayesianism-sequence) (IBRL) is a way to combine reinforcement learning theory with imprecise probabilities which produces a specific kind of frequentist guarantee in the nonrealizable setting (infra-Bayesian regret). A rough summary of the results we got in this framework so far:

-   There is a dynamically consistent [update rule](https://www.lesswrong.com/s/CmrW8fCmSLK7E25sa/p/e8qFDMzs2u9xf5ie6#Definition_28__Belief_Function_Update) for a notion of imprecise beliefs that generalizes credal sets (infradistributions). This rule is equivalent to the one described by [Gilboa and Schmeidler](https://www.sciencedirect.com/science/article/pii/S0022053183710033) but we represented it using different mathematical language (concave functional or convex set, related by Legendre-Fenchel duality, instead of an order on functions).
-   Newcombian environments (where naive causality is violated) can be [represented](https://www.lesswrong.com/s/CmrW8fCmSLK7E25sa/p/e8qFDMzs2u9xf5ie6#Hypothesis_Translation_Theorems) as causal infra-Bayesian laws.
-   Infra-Bayesian laws can [express](https://www.lesswrong.com/s/CmrW8fCmSLK7E25sa/p/SYeuMzspmwoQABWdw#Section_8__Environment_Forming_Constraints) a very large variety of possible frequentist desiderata.
-   [Miscellaneous](https://www.lesswrong.com/s/CmrW8fCmSLK7E25sa/p/idP5E5XhJGh9T5Yq9) [results](https://www.lesswrong.com/s/CmrW8fCmSLK7E25sa/p/vrbidMiczaoHBhZGp) [about](https://www.lesswrong.com/s/CmrW8fCmSLK7E25sa/p/SYeuMzspmwoQABWdw) [the](https://www.lesswrong.com/s/CmrW8fCmSLK7E25sa/p/PrYbdKcj89f8swCkr) mathematical properties of infradistributions, e.g. topological, information-theoretic and category-theoretic
-   An analysis of regret for an infra-Bayesian generalization of stochastic linear bandits. This is an ~upcoming~ paper: "[Imprecise Multi-Armed Bandits](https://www.lesswrong.com/posts/zyN7K8NB8RzAft7KZ/linear-infra-bayesian-bandits)" (IMAB).

In particular, the result about Newcombian environments and also infra-Bayesian physicalism (see [[#^direction-18-infra-bayesian-physicalism|Direction 18]] below) are two products of infra-Bayesianism that I don't see, at present, how to reproduce with any of the alternative approaches to nonrealizability.

Directions for further research include:

-   (Direction 3.1) Extending the results of IMAB to full-fledged IBRL. In particular, it might be interesting to get a result that subsumes [Tian et al](https://arxiv.org/abs/2010.15020) as a special case.
-   (Direction 3.2) Finding an infra-Bayesian analogue for Russo-Van Roy ("eluder") [dimension](https://web.stanford.edu/~bvr/pubs/Eluder.pdf). \[**EDIT:** We did even better, namely, created [infra-Bayesian decision-estimation theory](https://www.lesswrong.com/posts/LgLez8aeK24PbyyQJ/new-paper-infra-bayesian-decision-estimation-theory).\]
-   (Direction 3.3) Analyzing the computational complexity of learning in the IMAB setting.
-   (Direction 3.4) Studying versions of the IMAB setting with non-crisp infradistributions.

### Direction 4: Exploiting properties of simplicity priors ^direction-4-exploiting-properties

In general, Bayesian inference has only fairly weak guarantees in the nonrealizable setting. However, simplicity priors might produce stronger guarantees. In particular, [Lattimore, Hutter and Gavane](https://arxiv.org/abs/1107.5531) (LHG) showed[^note-12] that (a specific version of) Solomonoff induction converges to predicting a deterministic computable subsequence even when the full sequence is uncomputable.

Directions for further research include:

-   (Direction 4.1) Generalizing LHG to stochastic subsequences (this is stated as an open problem in the paper).
-   (Direction 4.2) Nonrealizable guarantees for RL with a Solomonoff prior.
-   (Direction 4.3) Generalizing LHG to bounded versions of the Solomonoff prior, e.g. a version with bounded space complexity (this might be easier to study than bounded time complexity, since PSPACE is in some ways a simpler class than P, e.g. APSPACE = NPSPACE = PSPACE).

### Direction 5: Agnostic RL ^direction-5-agnostic-rl

The conventional approach to nonrealizability in offline and online learning is to replace convergence to the true hypothesis with convergence to the hypothesis closest to the truth. Similarly, in RL, given some natural metric or [divergence](https://en.wikipedia.org/wiki/Divergence_\(statistics\)) $d$ on the space of environments, we can try to prove regret bounds of the form

$$
\mathrm{Reg}(T)= o(T)+\inf_{\mu\in\mathcal{H}}d\left(\mu,\mu^*\right)\cdot T
$$

Here, $T$ is the time horizon, $\mathcal{H}$ is the hypothesis class and $\mu^*$ is the true environment.

That is, we allow a sublinear term (as in the realizable case) and a linear term which scales with the distance of $\mu^*$ from $\mathcal{H}$. Indeed, a result of this form was proven in [Zanette et al](https://arxiv.org/abs/2003.00153), although in a model-free setting (i.e. instead of the environments themselves they consider their corresponding state-action value functions, although their divergence also depends directly on the environment).

At least superficially, a potential drawback of this approach is that Bayes-optimality doesn't imply this "agnostic" regret bound (AFAICT), as opposed to ordinary regret bound of the realizable setting. There is also no immediately obvious agnostic analogue of Bayesian regret. However, we can rectify this by recasting the setting in IBRL language. Indeed, for any $\mu\in\mathcal{H}$ it is possible to construct a (non-crisp) infra-Bayesian law[^note-13] $\Lambda_\mu$ s.t., for any policy $\pi$ and $f:(\mathcal{O}\times\mathcal{A})^*\rightarrow[0,1]$:

$$
\mathbb{E}_{\Lambda_\mu\pi}[f]=\min_{\mu'}\left(\mathbb{E}_{\mu'\pi}[f]+d(\mu,\mu')\right)
$$

Notice that when $d$ is total variation distance, we can take $\Lambda_\mu=\mu$.  

Then, learning the hypothesis class $\{\Lambda_\mu\mid\mu\in\mathcal{H}\}$ is equivalent to agnostically learning $\mathcal{H}$. Moreover, IBRL does have Bayesian regret, and a notion of Bayes-optimality that implies infra-Bayesian regret bounds, which thereby carries over to agnostic RL.

A few examples of directions for further research:

-   (Direction 5.1) Finding an agnostic version of the regret bound in [Jin, Liu and Miryoosefi](https://arxiv.org/abs/2102.00815) (their bound uses the so called Bellman-Eluder dimension of the hypothesis class, as opposed to the much more restrictive linear dimension of Zanette et al.)
-   (Direction 5.2) Studying model-based agnostic regret bounds[^note-14].
-   (Direction 5.3) Combining agnostic results with other IBRL results, e.g. with IMAB.

## Subproblem 1.2/2.1: Traps ^subproblem-1-2-2

Allowing traps in the environment creates two different problems:

-   (Subproblem 1.2) Bayes-optimality becomes intractable in a very strong sense (even for a small number of deterministic MDP hypotheses with small number of states).
-   (Subproblem 2.1) It's not clear how to to talk about learnability and learning rates.

It makes some sense to consider these problems together, but different direction emphasize different sides.

### Direction 6: Metacognitive Agents ^direction-6-metacognitive-agents

This research direction is motivated not only by traps, but also by producing especially strong frequentist guarantees via metacognition (a form of self-improvement). More speculatively, this model might be also applicable to humans (and related specifically to conscious reasoning), which makes it relevant to superimitation (see [[#^superimitation|relevant section]] below). It was originally called [Turing RL](https://www.lesswrong.com/posts/3qXE6fK47JhSfkpnB/do-sufficiently-advanced-agents-use-logic?commentId=fEKc88NbDWZavkW9o), but that name seems incorrect now because "RL" assumes learnability (no traps).

In a metacognitive agent, in addition to the usual "external" interfaces (actions and observations), there is also an "internal" interface that allows the agent to execute arbitrary programs and observe their outputs. This allows us to use a learning algorithm to form subjective beliefs about computations. The beliefs can be entangled with the agent's beliefs about the external world.

For example, let $\Lambda$ be the set of all lambda terms. Then our agent might have a belief $\Theta$ over $\Gamma:=2^{\Lambda\times\Lambda}$ that refers to the relation of $\beta$\-equivalence on $\Lambda$. In a Bayesian framework $\Theta$ is a distribution, and the agent might also have a belief about the external world that takes the form of an RL environment that depends on a point in the support of $\Theta$. In an infra-Bayesian framework, $\Theta$ is an infradistribution and there is an appropriate way to define a notion of "law" s.t. $\Theta$ is its marginal[^note-15].

However, it might be more interesting to put all beliefs about the world "inside quotation". Indeed, let $\zeta$ be a prior about the external world that a program can sample from: for example the unnormalized Solomonoff prior. Given a $\beta$\-equivalence oracle, we can sample this prior using some oracle machine $M$ (since such an oracle allows to instantly know whether a given program produces given output). Since any point in $\Gamma$ has the right type signature to serve as such an oracle, we can construct a kernel $Z$ from $\Gamma$ into the external world s.t. $Z(y)$ is defined by plugging the oracle $y$ into $M$. We can then combine any $\Theta$ with $Z$ (i.e. form the semidirect product $\Theta\ltimes Z$) to obtain the overall belief.

Notice that this setting is inherently nonrealizable, since the ground truth about $\Gamma$ is uncomputable. On the other hand, the nonrealizability of the external world can in principle be circumvented, because we have computationally simple hypotheses of the form "the external world behaves according to program $P$". Moreover, even "the external world is sampled from the unnormalized Solomonoff prior" is a computationally simple hypothesis. Hence, as long as the world is computable, we can describe it exactly modulo uncertainty about computations.

While the external world can contain irreversible transitions, it seems reasonable to employ an approximation in which executing most[^note-16] programs doesn't have irreversible harmful side-effects. As a consequence, if the agent survives long enough, it can learn most facts about computations. In the "quoted prior" setting, it will then use what it learned about computations to approximate Bayes-optimal behavior in the external world, which addresses subproblem 1.2. Moreover, since some hypotheses assert quoted priors about _computations_, it can arguably use what it learned to improve its own learning algorithm.

This framework is closely related to MIRI's notion of "logical uncertainty". Hence, it makes sense to compare it Garrabrant's [logical induction](https://arxiv.org/abs/1609.03543) (LI). While LI might turn out to have a useful role in this framework, in itself, LI doesn't address some key relevant questions:

-   LI is focused entirely on epistemology, and the guarantee it satisfies reflects that. On the other hand, we are interested in the agent's performance as measured by achieving goals (expected utility) in the external world, and want guarantees that reflect it.
-   The guarantees of LI are purely asymptotic, without especially useful rates on convergence. Indeed, LI assumes learning from a fixed sequence of theorems that are revealed to the algorithm, which is bound to be astronomically inefficient. On the other hand, a metacognitive agent should decide which programs to run online in some manner that guarantees good sample complexity.
-   LI in its present form is not concerned with computational complexity, while we are ultimately interested in models that are computationally feasible (although it might be useful to consider more or less realistic models of computational resource constraints).
-   LI doesn't use what it has learned to improve its own learning process.

There are several potential starting points for research into metacognitive agents:

**Direction 6.1: Bayesian planning via query-based learning of computations**

Arguably tree automata and more generally [string machines](https://www.lesswrong.com/posts/jxE47v3aezEYaydg9/compositional-language-for-hypotheses-about-computations) are a natural class of hypotheses about computations. Therefore, we can try building on existing research in automata inference[^note-17]. This field is infamous for its many impossibility results, but there is one model of learning that has been quite successful. Namely, learning automata assuming two types of allowed queries:

-   Running the unknown automaton on specific input.
-   Stating a hypothesis automaton, and receiving a counterexample if the hypothesis is false. (By "counterexample", we mean an input on which the hypothesis automaton produces a different answer from the true automaton.)

That is, algorithms exist that guarantee convergence to a correct automaton with a number of queries that is polynomial in minimal automaton size.

In our setting, the first type of query can be implemented by running a specific program. The second type of query cannot be implemented directly, but is effectively available in various natural setups. For example:

-   If we are interested in PAC-learning w.r.t. a known distribution over programs, we can implement the counterexample query by sampling from the distribution and testing the hypothesis on the sample.
-   If we want the algorithm to answer a sequence of questions of the form "predict the output of this program", we can implement the counterexample query by answering according to the current hypothesis, which leads to a polynomial mistake bound.

Therefore, it is a natural question whether we can implement Bayesian planning by some protocol of this type, assuming (for starters) that it is possible to efficiently sample from the prior. For example, assume that the hypothesis about computations translates to a hypothetical infra-Bayesian coarsening (or Bayesian approximation?) of the prior for which optimal planning is feasible. Assume also that there if resulting policy performs less well than promised on the true prior, there is some way to produce a counterexample to the hypothesis about computations. Then, counterexample queries are effectively available. 

Automata learning might also be feasible in a setting where the automaton generates a sequence that we need to predict. (At least for a deterministic automaton this is trivial because the sequence is periodic.) Speculatively, the amount of available computational resources can be treated as defining a "sequence" (possibly related to "[logical time](https://www.lesswrong.com/posts/dKAJqBDZRMMsaaYo5/in-logical-time-all-games-are-iterated-games)") and this can be exploited to get guarantees even when the prior cannot be sampled efficiently.

**Direction 6.2: Expressiveness of string machines**

String machines are a potential starting point for finding a frugal universal prior for metacognitive agents. In order to strike the right balance between "frugality" and "universality" we need to understand the expressiveness of the string language and the computational complexity of evaluating string machines (or answering more complicated questions about string machines) under various assumptions. In particular, parameterized complexity theory might be relevant here, since there seem to be more relevant parameters than just description size (e.g. the number of meta-vertex levels we allow).

**Direction 6.3: Query learning of string machines**

We can also study the sample complexity of learning string machines in the two-type query model above. While existing results guarantee learning with a number of queries polynomial in the _number of states_ of an automaton, we would like query complexity to scale well with the _description size_ of an automaton in string language. More general string machines are not even automata.

### Direction 7: Approximation algorithms for Bayesian planning ^direction-7-approximation-algorithms

Subproblem 1.2 comes from an NP-hardness result, but that still leaves room for studying approximation algorithms. There are many NP-hard optimization problems for which we have conjectured optimal approximation ratios (e.g. based on the PCP theorem or the unique games conjecture). It is conceivable that we can prove a result of this form for Bayesian planning. Some approaches:

-   (Direction 7.1) Fix a prior $\zeta$ over set of MDPs with state set $\mathcal{S}$ and action set $\mathcal{A}$, and an arbitrary stationary policy $\pi_0:\mathcal{S}\rightarrow\mathcal{A}$. Let $\pi^*$ be the (unknown) Bayes-optimal policy. For any policy $\pi$ we can consider the approximation ratio

$$
\frac{\mathbb{E}_{\zeta\pi}[U]-\mathbb{E}_{\zeta\pi_0}[U]}{\mathbb{E}_{\zeta\pi^*}[U]-\mathbb{E}_{\zeta\pi_0}[U]}
$$

-   (Direction 7.2) Finding the Bayes-optimal policy is NP-hard, but is it NP-easy? If it is e.g. PSPACE-hard then it seems significantly less likely that we can get optimal approximation results.

### Direction 8: Expanding Safety Envelope ^direction-8-expanding-safety

The [Expanding Safety Envelope](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=ndjGcYd39SmYYsHme) (XSE) is an approach to traps which can be summarized as follows:

-   Assume there is some a priori known safe baseline policy, or more generally a non-empty set of known safe actions at every state reachable by these actions.
-   Exploring the known safe actions might be sufficient to discover new safe actions. Exploring the new safe actions might be sufficient to discover even more safe actions, etc.
-   Therefore, we can study guarantees that compare asymptotic performance to the policy which is optimal among those restricted to discoverable safe actions.

One significant limitation of this approach is, when using a rich prior, discovery of new safe actions can at best be approximate. While we can study variants where we sometimes try risky actions, guaranteeing any sort of optimality there is likely to be intractable. However, maybe it is feasible to require that, whenever the posterior admits an approximation (e.g. in the sense of total variation distance) by a prior with iteratively discoverable safe actions, we get a corresponding lower bound on the performance of our algorithm starting from this point.

## Better regret bounds for simple priors ^better-regret-bounds-for

This section is a grab bag of research directions about improving regret bound theory for simple hypothesis classes based on MDPs. They are not directly related to AIXI, but rather fit perfectly within classical RL theory[^note-18]. However, it seems plausible that they are necessary pieces of the bigger puzzle (i.e. for a full solution of Problem 2).

### Direction 9: Unifilar MDPs ^direction-9-unifilar-mdps

\[**EDIT:** What I called "unifilar MDP" is already known in the literature under the name "regular decision process" (RDP): see [Ronca and De Giacomo](https://arxiv.org/abs/2105.06784). Notably, Subproblem 2.2 (password games) already emerges in learning RDPs with small number of states. Ronca and De Giacomo address it by assuming that the uniformly random policy has a high probability to reach every RDP state: a condition which is clearly insufficiently general, but does serve as an interesting starting point.\]

Most of RL theory literature focuses on learning an MDP with a known state space, implicitly assume a known representation. [Ortner et al](https://proceedings.neurips.cc/paper/2019/hash/9b8b50fb590c590ffbf1295ce92258dc-Abstract.html) prove a regret bound in a setting with unknown representation, but it scales with the _cardinality_ of the set of possible representations. For real-world agents, I expect this cardinality to be something like doubly-exponentially large, so their bound is extremely weak. 

As a first step towards a better theory of representation learning, I propose the following setting. Fix action set $\mathcal{A}$ and observation set $\mathcal{O}$. Then, a _unifilar MDP_ (UMDP: combination of MDP and unifilar hidden Markov model) $\mathcal{M}$ consists of the following data: the state set $\mathcal{S}$, the initial observation distribution $\beta_0\in\Delta\mathcal{O}$, the state initialization function $\iota:\mathcal{O}\rightarrow\mathcal{S}$, the response kernel $\rho:\mathcal{S}\times\mathcal{A}\rightarrow\Delta\mathcal{O}$ and the transition function $T:\mathcal{S}\times\mathcal{A}\times\mathcal{O}\rightarrow\mathcal{S}$. The interaction of a policy $\pi$ with a UMDP works as follows:

-   First, the first observation $b_0\in\mathcal{O}$ is sampled from $\beta_0$.
-   Second, the state is initialized to $s_0=\iota(b_0)$.
-   After every observation $b_i\in\mathcal{O}$:
    -   $\pi$ selects an action $a_i\in\mathcal{A}$.
    -   The next observation $b_{i+1}\in\mathcal{O}$ is sampled from $\rho(s_i,a_i)$.
    -   The next state is set to $s_{i+1}=T(s_i,a_i,b_{i+1})$.

Notice that the state at any moment of time can be recovered from the observation-action history, i.e. the above data defines some $\sigma^\mathcal{M}:(\mathcal{O}\times\mathcal{A})^*\times\mathcal{O}\rightarrow\mathcal{S}$. Hence this is indeed an MDP rather than a POMDP.

Fix a reward function $r:(\mathcal{O}\times\mathcal{A})^*\rightarrow[0,1]$ that can itself be represented by a deterministic finite state machine. We then constrain $\mathcal{M}$ by requiring that there exists some $r^{\mathcal{M}}:\mathcal{S}\times\mathcal{A}\rightarrow[0,1]$ s.t. for any $h\in(\mathcal{O}\times\mathcal{A})^*\times\mathcal{O}$ and $a\in\mathcal{A}$ we have

$$
r(ha)=r^{\mathcal{M}}(\sigma^\mathcal{M}(h),a)
$$

The problem is then proving the existence of an algorithm for interacting with an unknown communicating UMDP $\mathcal{M}$ compatible with $r$ which satisfies a regret bound that scales with $\mathcal{M}$'s number of states, number of actions and diameter.

### Direction 10: Foreground MDPs ^direction-10-foreground-mdps

Regret bounds in (lifelong/non-episodic) RL scale with MDP diameter because of the need to rule out traps. On the other hand, sequence prediction / online learning requires no such constraint and even allows environments with infinitely many states. However, sequence prediction / online learning can also be regarded as a degenerate special case of RL. This suggests that there should be a natural theory that combines both.

Motivated by the above, I propose to study MDPs of the following form. Assume that the state set of the MDP factors as $\mathcal{S}=\mathcal{S}_{\text{back}}\times\mathcal{S}_{\text{fore}}$ (background and foreground). Moreover, there is some $T_\text{back}:\mathcal{S}_\text{back}\rightarrow\Delta\mathcal{S}_\text{back}$ s.t. the $\mathcal{S}_\text{back}$\-marginal distribution of $T(s,t,a)$ is $T_\text{back}(s)$ for any $s\in\mathcal{S}_\text{back}$, $t\in\mathcal{S}_\text{fore}$ and $a\in\mathcal{A}$, where $T$ is the transition kernel of the MDP. That is, the background dynamics depends neither on the foreground state nor on the agent's actions. On the other hand, the foreground dynamics can depend both on the background state and the agent's actions.

We can then define a notion of diameter for the foreground only, and derive regret bounds that scale with it. Such a regret bound can scale with the total number of states, or with some dimension parameter (see Direction 11 below). In the latter case, $\mathcal{S}_\text{back}$ can be infinite. 

### Direction 11: Canonical RL Dimension ^direction-11-canonical-rl

\[**EDIT:** [Foster et al](https://arxiv.org/pdf/2112.13487.pdf) achieved significant progress on this, which I didn't know at the time of writing.\]

This direction already receives some attention in mainstream academia, so it might be of relatively lower priority.

In multiple areas of learning theory, we have a fairly complete characterization of how sample complexity depends on the hypothesis class. In many cases, the key parameter of the hypothesis class is some type of "dimension". For example:

-   For binary classification, Vapnik–Chervonenkis dimension
-   For multi-class learning, Natarajan dimension
-   For online learning, Littlestone dimension

In RL, our understanding is less good. We do have some results of similar nature, most of them derived from Russo and Van Roy's "eluder" dimension. For example [Jin, Liu and Miryoosefi](https://arxiv.org/abs/2102.00815) demonstrate a model-free regret bound that scales with "Bellman-Eluder" dimension and the logarithm of a covering number (the later can be said to correspond to [Minkowski-Bouligand](https://en.wikipedia.org/wiki/Minkowski%E2%80%93Bouligand_dimension) dimension). However, we don't have matching _lower bounds_ for these results. This means that we don't know whether the results we have cannot be subsumed by some better theory (indeed, [Du et al](https://arxiv.org/abs/2103.10897) show results that are neither strictly weaker nor strictly stronger than Jin, Liu and Miryoosefi). In contrast, the flavors of learning theory mentioned above come with proofs that their notions of dimension are optimal (albeit, only under the assumption of a worst-case distribution).

## Direction 12: Epistemic Regret Bounds ^direction-12-epistemic-regret

This direction attempts to address Subproblem 2.2.

The motivating intuition is: formulating the correct frequentist guarantee requires correctly distinguishing between _epistemic_ and _aleatoric_ uncertainty. The problem with password games is that the password is completely random information that is impossible to infer by any method other than brute force. Hence, we should treat this information as part of "aleatoric" uncertainty.

Let's recall the definition of Bayesian regret. Let $\mathcal{H}$ be a set representing hypotheses and $\zeta\in\Delta\mathcal{H}$ the prior. Since each hypothesis defines an environment, we have a mapping 

$$
\mu:\mathcal{H}\times\left(\mathcal{O}\times\mathcal{A}\right)^*\rightarrow\Delta\mathcal{O}
$$

The Bayesian regret of a policy $\pi$ is given by

$$
\mathrm{BReg}(\pi,T):=\mathbb{E}_{\theta\sim\zeta}\left[\max_{\pi'}\mathbb{E}_{\mu\pi'}\left[\sum_{i=0}^{T-1}r_i\middle|\theta\right]-\mathbb{E}_{\mu\pi}\left[\sum_{i=0}^{T-1}r_i\middle|\theta\right]\right]
$$

Here $T$ is the time horizon, and $r_i$ is the reward at time $i$.

For any environment $\nu:(\mathcal{O}\times\mathcal{A})^*\rightarrow\Delta\mathcal{O}$ and history $h=o_0a_0\ldots o_{n-1}a_{n-1}o_n$, denote

$$
\nu^\text{abs}(h):=\prod_{i=0}^n \nu\left(o_i\middle|o_0a_0\ldots o_{i-1} a_{i-1}\right)
$$

That is, $\nu^\text{abs}(h)$ is the probability that $\nu$ produces $h$ assuming a deterministic policy compatible with the actions in $h$.

Notice that minimizing Bayesian regret is equivalent to maximizing expected utility. However, expected utility only depends on $\mu$ and $\zeta$ via $\mu_{\text{Bayes}}:(\mathcal{O}\times\mathcal{A})^*\rightarrow\Delta\mathcal{O}$ defined by

$$
\mu_{\text{Bayes}}:=\mathbb{E}_{\theta\sim\zeta}[\mu(\theta)]
$$

Here, the expectation is in the sense of the Bayes' rule for environments, not pointwise. That is, first $\theta$ is sampled out of $\zeta$ and then the agent faces the environment $\mu(\theta)$. Explicitly:

$$
\mu_\text{Bayes}(ha)=\frac{\mathbb{E}_{\theta\sim\zeta}\left[\mu^\text{abs}(h\mid\theta)\mu(ha\mid\theta)\right]}{\mathbb{E}_{\theta\sim\zeta}\left[\mu^\text{abs}(h\mid\theta)\right]}
$$

On the other hand, Bayesian regret depends directly on $\mu$ and $\zeta$. Indeed, the minimal Bayesian regret is typically non-zero even for learnable $\mathcal{H}$. On the other hand, if we took $\mathcal{H}'$ to be a single element set $\{\theta_0\}$ and defined $\mu':\mathcal{H}'\times\left(\mathcal{O}\times\mathcal{A}\right)^*\rightarrow\Delta\mathcal{O}$ by $\mu'(\theta_0)=\mu_{\text{Bayes}}$, we would get $\mu'_{\text{Bayes}}=\mu_{\text{Bayes}}$ but the corresponding Bayesian regret of the Bayes-optimal policy would vanish.

This means that the definition of Bayesian regret treats the uncertainty coming from $\zeta$ and the uncertainty coming from the stochasticity of $\mu$ differently. We can call the former "epistemic" and the latter "aleatoric". Intuitively, the $T$\-dependence of Bayesian regret measures the rate at which the agent reduces its goal-relevant epistemic uncertainty, and it is sublinear iff the agent asymptotically reduces it to 0 i.e. learns all the "epistemic information" it needs. On the other hand, we don't expect the agent to learn all "aleatoric information" but only to maximize expected utility w.r.t. to aleatoric uncertainty.

In the case of the Solomonoff prior, the naive approach regards the uncertainty about the program for the UTM as epistemic uncertainty and the uncertainty corresponding to the probabilities computed by that program as aleatoric uncertainty. However, in algorithmic statistics[^cite-19] there are more nuanced tools to separate "structured" and "random" information, like the notion of "sophistication".

Given any string $x\in\{0,1\}^*$, we can consider ways to represent it as running program $p$ (which we assume to halt on _all_ inputs) on input $y$. Let's constrain this representation to be nearly-optimal compression, i.e. require that for some some "small" number $c\in\mathbb{N}$

$$
|p|+|y|\leq K(x)+c
$$

The minimal length of $p$ over all such representations is called the $c$\-_sophistication_ of $x$ and can be interpreted as the amount of "structured" information in $x$. In our case, the minimal $p$ of an MDP might be considered as the "epistemic" information it contains, which leads to a novel decomposition of the Solomonoff prior into some $\zeta$ and $\mu$. Care might be required for choosing $c$. For example, maybe we can set $c=\log K(x)$.

In purely frequentist terms, we can hope for a regret bound of e.g. the form 

$$
\tilde{O}\left(P^\alpha 2^{\eta(K+c(K)-P)} \tau^\beta T^\delta\right)
$$

Here $P$ is the $c(K)$\-sophistication of the MDP+representation (s.t. $K+c(K)-P$ is the amount of "random" information) and $\eta$ is another constant.

More generally, instead of a single MDP we can consider a computable distribution $\xi$ over a $D$\-dimensional family of MDPs of diameter at most $\tau$, using some notion of dimension from RL theory (see Direction 11 above). Then, we can expect that the average ($\xi$\-Bayesian) regret of the family can be bounded by

$$
\tilde{O}\left(P^\alpha 2^{\eta(K+c(K)-P)} \tau^\beta D^\kappa T^\delta\right)
$$

Here $\kappa$ is yet another constant, whereas $P$ and $K$ refer to the sophistication and Kolmogorov complexity of $\xi$.

Given an appropriate notion of "computable distribution over MDPs", this would encompass learning of MDPs with arbitrary (uncomputable) transition probabilities.

## Subproblem 2.4: Multi-Agent Guarantees ^subproblem-2-4-multi-agent

One special case is completely straightforward in IBRL, namely two-player zero-sum games: IBRL essentially _is_ a zero-sum game, so it's enough that each player views the other as "Murphy". So, for example two IBRL agents equipped with sources of randomness (s.t. effectively their actions are lotteries over game moves) playing a stochastic game necessarily converge to a Nash equilibrium, assuming that the corresponding infra-MDPs are in their respective hypothesis classes.

Beyond that, there are roughly two approaches to multi-agent guarantees:

-   (Subproblem 2.4.1) Trying to derive additional parts of classical game theory from learning theory.
-   (Subproblem 2.4.2) Trying to derive [_superrational_](https://en.wikipedia.org/wiki/Superrationality) behavior from learning theory.

AFAIK either of the following possibilities is conceivable:

-   (World 2.4.1) Subproblem 2.4.2 requires theory built on top of the theory required for Subproblem 2.4.1.
-   (World 2.4.2) Subproblems 2.4.1 and 2.4.2 are partially or even largely independent.
-   (World 2.4.3) Subproblem 2.4.1 is not a reasonable desideratum at all.

Different directions below have different relationships with these worlds.

\[**EDIT:** See also [Infra-Bayesian Haggling](https://www.lesswrong.com/posts/gBgw7mbLNYv5qzDLG/infra-bayesian-haggling), a new direction for Worlds 2.4.2/3\]

### Direction 13: Population Games ^direction-13-population-games

This direction is motivated by Worlds 2.4.1/2.

A [population game](https://www.lesswrong.com/posts/HNnRCPe2CejfupSow/fixed-points-in-mortal-population-games) is a setting where large populations of players play against each other by being sorted into random groups on each turn, s.t. the probability to meet the same opponent twice is negligible. This setting is designed to reduce incentives for superrationality, although it's still unclear whether this is sufficient to justify classical game theory.

An appealing feature of this setting is that it can be naturally interpreted as a dynamical system. For learning agents satisfying very mild assumptions, every fixed point corresponds to an $\epsilon$\-Nash equilibrium (where $\epsilon\rightarrow0$ as the geometric time discount constant $\gamma\rightarrow1$). Moreover, a fixed point exists for any tuple of player policies.

It is therefore natural to ask whether any of the fixed points have to be attractors (under some assumptions about the learning algorithms), study their attraction basins, study other fixed submanifolds etc.

### Direction 14: Logit equilibria of finite-state repeated games ^direction-14-logit-equilibria

This direction is motivated by World 2.4.1. (See [this](https://www.lesswrong.com/posts/5bd75cc58225bf0670375058/superrationality-in-arbitrary-games) for early thinking on the topic.)

A [logit equilibrium](https://en.wikipedia.org/wiki/Quantal_response_equilibrium) is defined similarly to a Nash equilibrium with "optimal response" replaced by "soft-optimal response" (i.e. the players behave according to the softmax distribution associated with the expected payoffs of different plays for fixed opponent distributions). Consider the iterated prisoner's dilemma where each player's pure strategies are constrained to be of the form:

-   Choose some play $p_0$ ($C$ or $D$) on round number 0.
-   Choose some mapping $f:\{C,D\}\rightarrow\{C,D\}$. On round $i>0$, play according to $p_i=f(q_{i-1})$ where $q_{i-1}$ is the opponent's play on the previous round.

In particular, tit-for-tat corresponds to $p_0=C$ and $f(q)=q$.

For geometric time discount $\gamma$ close to 1, both always-defect/always-defect and tit-for-tat/tit-for-tat are Nash equilibria. Moreover, tit-for-tat/tit-for-tat is also an approximate logit equilibrium for softmax parameters[^note-20]

$$
\lambda=\omega\left(1-\gamma\right)
$$

However, always-defect/always-defect is _not_ an approximate logit equilibrium as long as

$$
\lambda=o\left(1\right)
$$

This happens for the following reason. Tit-for-tat is almost as good a response to always-defect as always-defect: it only loses $O(1)$ utility because of round 0. Therefore, the soft-optimal response to always-defect is a mixture of at least always-defect _and_ tit-for-tat. Moreover, the soft-optimal response to a mixture of always-defect and tit-for-tat places little probability on always-defect, because tit-for-tat does much better.

As a result, in this asymptotic regime logit equilibrium entails a probability approaching 1 of cooperating forever. More generally, I propose the following conjecture: in any repeated (or even stochastic?) game in which we constrain the strategies to be finite state machines (with/without a uniform bound on the number of states?), while allowing a sufficient number of states, any logit equilibrium converges to Pareto efficiency in the asymptotic regime above.

This seems like a potential method of obtaining superrational behavior as a corollary of classical game theory in some situations.

### Direction 15: Infra-Bayesian Veil of Ignorance ^direction-15-infra-bayesian-veil

This direction is motivated by Worlds 2.4.2/3.

As a warm-up, consider a repeated symmetric game between two agents who are copies of each other, either without randomization or with both using the same random generator. In this setting, each agent learns that the other parrots its actions precisely. Therefore, even a simple learning algorithm will converge to the symmetric Pareto efficient outcome.

**Direction 15.1: IBRL with exact clones**

What if the game is not symmetric, or there is randomization which breaks the symmetry? If we assume all the agents are exact clones (i.e. they execute the exact same code / follow the exact same policy), each agent can regard this as a Newcombian environment (the clones are implemented by "Omega"). And, we know that Newcombian environments can be represented as infra-Bayesian laws. We will call it the _clone law_ in this case.

Notice that, even though exact clones must have the same utility function, this doesn't rule out asymmetric games. Indeed, the utility functions are the same _in terms of the particular agent's actions and observations_, but this is consistent with each agent identifying their own role ("which clone/player am I") and receiving payoffs accordingly. As a simple example, we can imagine the payoff being a part of the observation channel.

Notice also that the clone law is _not_ a convex combination of laws corresponding to the different roles the agent can play. Rather, the clone law requires Murphy to predict the behavior of the agent in each possible role _in advance_ of the random role selection. This way pseudocausality is ensured (i.e. Murphy can't "cheat" by only predicting the behavior of one role correctly.)

Moreover, two clone laws which are identical except for a different probability distribution over roles typically cannot coexist in the same learnable hypothesis class. This is because there is no way to infer the distribution over roles from observations. Instead, we should think of this distribution as determined by the prior. Indeed, mixing two clone laws is equivalent to mixing the role distributions in the $\gamma\rightarrow1$ limit, as long as the role distributions have full support. Hence, we can imagine all clone laws for the same game inside the prior effectively aggregating into a single clone law with the average role distribution. 

The optimal policy for the clone law is maximizing the linear combination of utilities of different roles according to the prior distribution over roles. Hence, the prior determines which point on the Pareto frontier is selected, and can be regarded as defining a "notion of fairness".

One issue with clone laws is that they cannot be represented as e.g. infra-POMDPs with a finite number of states (the state has to encode Murphy's prediction i.e. the entire relevant part of the policy). This leads to a concrete research problem: _find natural hypotheses classes containing clone laws that admit efficient learning algorithms_.

**Direction 15.2: IBRL with inexact clones**

What if we want to allow agents with different utility functions? One trick to achieve this is postulate that the agent receives a description of its utility function upon waking up (e.g. in the form of a program, if it's a metacognitive agent). This way, the policy has to account for all admissible utility functions. It is possible that we can apply similar methods without this trick, using instead the observation that most utility functions can appear as _instrumental_ _goals_ in some situations (e.g. using the formalization of compositional polytope-MDPs).

What if the agents have different priors (in particular over utility functions but also in general)? Now they are not exact clones anymore. However, it is conceivable that their policies are still _similar_ in some sense that can be used to represent the setting as Newcombian. For example, we can equip the space of utility functions with some metric. We can then define a metric on _policies_ via the Hausdorff distance between their _graphs_.

As a toy model, we can consider a fixed game in normal form, with the agent having some prior over:

-   Role (player)
-   Payoff matrix
-   Distance of opponents from itself

We can then try to prove that, under some assumptions, priors that are "close" (according to some divergence) lead to policies that are close. Moreover, when agents with close priors are facing each other (and know their mutual distances are small), they should play close to Pareto efficiency. It would be fascinating if we could recover something like Yudkowky's [proposal](https://www.lesswrong.com/posts/z2YwmzuT7nWx62Kfh/cooperating-with-agents-with-different-ideas-of-fairness).

In particular, consider a game with a _unique_ Pareto efficient outcome. Assume that all admissible payoff matrices are monotonically increasing transformations of each other. Then, the agents will always play Pareto efficiently, because doing so unconditionally guarantees that all opponents will do the same thing, for any finite distance from opponents. (In particular, the actual distance is 0).

## Direction 16: Hidden Rewards ^direction-16-hidden-rewards

This direction attempts to address Problem 3 (value ontology).

In order to define a utility function, we need some ontology $\Omega$ to specify its domain. One natural way to represent an ontology is using an infra-POMDP. That is, we have the state set $\mathcal{S}_0$, the initial infradistribution $\sigma_0\in\Box\mathcal{S}_0$, the observation mapping $\omega_0:\mathcal{S}_0\rightarrow\mathcal{O}$ and the transition infrakernel $T_0:\mathcal{S}_0\times\mathcal{A}\rightarrow\Box\mathcal{S}_0$. Here, $\Box\mathcal{S}_0$ stands for credal sets over $\mathcal{S}_0$, i.e. non-empty closed convex subsets of $\Delta\mathcal{S}_0$ (we can also allow more general infradistributions). The reason we're using an infra-POMDP instead of a POMDP is, we don't want $\Omega$ to fully specify the environment.

To specify an environment over $\Omega$ (in ontology $\Omega$), we consider a _maximal refinement_ of the infra-POMDP (we call this a _hidden environment_[^note-21]). That is, a state set $\mathcal{S}$, an initial distribution $\sigma\in\Delta\mathcal{S}$, an observation mapping $\omega:\mathcal{S}\rightarrow\mathcal{O}$, a transition kernel $T:\mathcal{S}\times\mathcal{A}\rightarrow\Delta\mathcal{S}$ and a translation mapping $\lambda:\mathcal{S}\rightarrow\mathcal{S}_0$ s.t. the following conditions hold:

-   $\lambda_*\sigma\in\sigma_0$
-   $\omega=\omega_0\circ\lambda$
-   For all $s\in\mathcal{S}$ and $a\in\mathcal{A}$: $\lambda_*T(s,a)\in T_0(\lambda(s),a)$

If we want to do IBRL rather than Bayesian RL, we can consider general (non-maximal) refinements, i.e. refinements that are infra-POMDPs rather than POMDPs.

To specify a reward function over $\Omega$ ("hidden reward function"), we consider a function $r:\mathcal{S}_0\times\mathcal{A}\rightarrow\mathbb{R}$. More generally, we can allow bounded functions $r:(\mathcal{S}_0\times\mathcal{A})^*\rightarrow\mathbb{R}$. Given a reward function, the corresponding utility function is defined as usual i.e. as a time-discount sum of rewards.

An interesting special case of a hidden environment is a UMDP equipped with a translation mapping. We will call it a _relative_ UMPD (RUMDP). Assuming a hidden reward function of the form $r:\mathcal{S}_0\times\mathcal{A}\rightarrow\mathbb{R}$, it admits efficiently computing the optimal policy.

Given hidden environments/rewards instead of observable (i.e. ordinary) environments/rewards, it is straightforward to define analogues to concepts from RL theory such as prior, Bayes-optimality, regret, learnability etc.

### Direction 16.1: Agency with partial monitoring ^direction-16-1-agency

Learnability is more difficult to establish with hidden reward functions than with observable reward functions, since ruling out traps is insufficient (see Example 1 [here](https://www.lesswrong.com/posts/aAzApjEpdYwAxnsAS/reinforcement-learning-with-imperceptible-rewards#Example_1)). For stateless environments, we already have the closely related theory of partial monitoring, which provides a comprehensive classification of possible regret bounds[^note-22]. Therefore, we can try building an extension of this theory to our RL-like setting.

### Direction 16.2: Specifying semi-instrumental reward functions ^direction-16-2-specifying

A related setting in which learnability is established is [instrumental reward functions](https://www.lesswrong.com/posts/aAzApjEpdYwAxnsAS/reinforcement-learning-with-imperceptible-rewards#A_Regret_Bound_for_RL_with_Instrumental_Rewards) (and very likely we can extend that to semi-instrumental reward functions as well). Its drawback is that (as opposed to hidden rewards) it doesn't come with a simple natural way to specify reward function. A formal relationship between the two frameworks could allow us enjoying both worlds.

Given any hidden reward function $r$, we can ask whether there exists a semi-instrumental reward function $\mathcal{R}$ s.t. for any hidden environment $\mu$ and history $h\in(\mathcal{S}_0\times\mathcal{A})^*$ compatible with $\mu$

$$
\mathcal{R}(h,\mathcal{I}(\mu\mid h))=r(h)
$$

Here, $\mathcal{I}(\mu\mid h)$ stands for the instrumental state corresponding to $\mu\mid h$, and we abuse notation on the left hand side by implicitly projecting $h$ to $(\mathcal{O}\times\mathcal{A})^*$ using $\omega_0$.

The problem, then, is to characterize hidden reward functions with this property. Also, we can try to characterize $\Omega$ for which all hidden reward functions have this property.

### Direction 16.3: Undogmatic Ontologies ^direction-16-3-undogmatic

Every hidden environment defines an observable environment. However, for an arbitrary $\Omega$, not every observable environment can be obtained this way. In other words, $\Omega$ constraints what the agent can expect to see. Arguably, this is undesirable: why would the real world agree with an ontology which is just an arbitrary/subjective feature of the agent's axiology?

Hence, it is natural to consider _undogmatic_ ontologies: $\Omega$ that admit all observable environments. However, it seems tricky to find pairs of $\Omega$ and a hidden reward function $r$ that simultaneously satisfy all of the following conditions:

-   $\Omega$ is undogmatic.
-   The class of all communicating RUMDPs over $\Omega$ is learnable for $r$.
-   $r$ is not reducible to an observable reward function. That is, there is no $r':(\mathcal{O}\times\mathcal{A})^*\rightarrow\mathbb{R}$ s.t. for any $h\in(\mathcal{S}_0\times\mathcal{A})^*$ it holds that $r(h)=r'(h)$.

As an existence proof, we can consider the ontology whose states are instrumental states ($\mathcal{S}_0=\mathcal{IS}_\omega$) and initialization is completely uncertain ($\sigma_0=\top_{\mathcal{S}_0}$), and $r$ corresponding to any instrumental reward function. It would be interesting to find a good general characterization. ~In particular, I don't even know whether~ $\mathcal{S}_0$ ~can be finite.~ \[**EDIT:** [Here](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=3YtzuSJ8indg7v9s2) is a way to construct many examples, including finite ones.\]

### Direction 16.3: Bayes-optimal planning for communicating RUMDPs ^direction-16-3-bayes-optimal

We know that approximating Bayes-optimal planning is intractable for MDPs with traps. However, maybe for communicating RUMDPs it is tractable even when they form an unlearnable class. This seems like an interesting question to investigate.

## Direction 17: Algorithmic Descriptive Agency Measure (ADAM) ^direction-17-algorithmic-descriptive

This direction attempts to address Problem 5 (descriptive agent theory).

ADAM is a formal way of quantifying the extent to which some arbitrary policy $\pi:(\mathcal{O}\times\mathcal{A})^*\times\mathcal{O}\rightarrow\mathcal{A}$ is "agentic".

Fix some UTM $M_0$.

We will consider computable utility functions of the form $U:(\mathcal{O}\times\mathcal{A})^\omega\rightarrow[0,1]$. Notice that such a function is automatically continuous. Since it is computable, we can talk about its Kolmogorov complexity $K(U)$ (w.r.t. $M_0$).

Also, for any UTM $M$ we denote $\zeta_M$ the corresponding Solomonoff (semi-)environment (prior). We can talk about $K(M)$: the Kolmogorov complexity of $M$ w.r.t. $M_0$. Also, given $U$ as above we can consider the _joint_ Kolmogorov complexity $K(U,M)$.

We can now tentatively define ADAM by

$$
\mathrm{g}(\pi):=\sup_{U,M}\left(\min_{\pi':\mathbb{E}_{\zeta_M\pi'}[U]\geq\mathbb{E}_{\zeta_M\pi}[U]}K(\pi')-K(U,M)\right)
$$

Here the maximum is over all computable utility functions $U$ and UTMs $M$.

Intuitively, we are looking for a way to interpret $\pi$ as maximizing $U$ w.r.t. prior $\zeta_M$ s.t., on the one hand, $\pi$ does a good job at maximizing (enforced by the first term), and on the other hand, this interpretation is not contrived (enforced by the second term). 

Notice that $\mathrm{g}$ inherits all the other problems of AIXI. Hence, we will ultimately need to modify it according to the respective solutions (e.g. use frugal universal priors and their associated complexity measure instead of Solomonoff priors and Kolmogorov complexity).

$\mathrm{g}$ has a few easy to check nice properties:

1.  The AIXI policy $\pi^*$ has $\mathrm{g}(\pi^*)=+\infty$.
2.  Any computable policy $\pi$ has $\mathrm{g}(\pi)\lesssim K(\pi)<+\infty$. This allows us to intuitively interpret $\mathrm{g}(\pi)$ as something like "how many of the bits needed to describe $\pi$ are contributing to its agency".
3.  For every $n\in\mathbb{N}$ there is a computable policy $\pi_n$ s.t. $\mathrm{g}(\pi_n)\approx K(\pi_n)\geq n$.
4.  Changing the UTM only changes $\mathrm{g}$ by $O(1)$.

However, at present I don't know much else about its properties. This leaves a lot of questions to explore:

### Direction 17.1: Comparing ADAM variants ^direction-17-1-comparing

Here are some superficially similar definitions:

$$
\mathrm{g}'(\pi):=\sup_{U,M}\left(\log\frac{1}{\Pr_{\pi'\sim\xi}\left[\mathbb{E}_{\zeta_M\pi'}[U]\geq\mathbb{E}_{\zeta_M\pi}[U]\right]}-K(U,M)\right)
$$

$$
\mathrm{g}''(\pi):=\log\mathbb{E}_{U,M\sim\psi}\left[\frac{1}{\Pr_{\pi'\sim\xi}\left[\mathbb{E}_{\zeta_M\pi'}[U]\geq\mathbb{E}_{\zeta_M\pi}[U]\right]}\right]
$$

Here, $\xi$ is a Solomonoff prior over policies and $\psi$ is a Solomonoff prior over utility functions and UTMs[^note-23].

At present, I slightly prefer $\mathrm{g}$ over $\mathrm{g}'$ and $\mathrm{g}''$ because for the latter two, I don't know property 3 above (I know that e.g.  $\mathrm{g}'(\pi_n)\geq n$ but not $\mathrm{g}'(\pi_n)\approx K(\pi_n)$).

It is easy to see that

$$
\mathrm{g}(\pi)\gtrsim \mathrm{g}'(\pi)\lesssim \mathrm{g}''(\pi)
$$

**Open problem:** Are $\mathrm{g}',\mathrm{g}''$ the same as $\mathrm{g}$ up to $O(1)$?

### Direction 17.2: ADAM of random policies ^direction-17-2-adam

Deterministically generating an object of high Kolmogorov complexity is hard: for any program $p$ that outputs a bitstring $x$ we have $K(x)\leq|p|$, so generating $x$ with very high $K(x)$ requires a very long program. Since $\mathrm{g}(\pi)\lesssim K(\pi)$, this means that deterministically generating an agentic policy is also hard. But, _randomly_ generating an object of high Kolomogorov complexity is easy: most bitstrings $x$ of length $k$ have $K(x)\approx k$. On the other hand, I expect most policies to be unagentic.

**Conjecture:** For any computable $\varpi:\{0,1\}^\omega\times(\mathcal{O}\times\mathcal{A})^*\times\mathcal{O}\rightarrow\mathcal{A}$, we have

$$
\mathbb{E}_{r\sim\mu_0}\left[\mathrm{g}(\varpi(r))\right]\lesssim K(\varpi)
$$

Here, $\varpi$ is computable in the sense that it's a Turing machine that receives the first argument on a separate input tape, and $\mu_0\in\Delta\{0,1\}^\omega$ is the IID fair coin.

### Direction 17.3: ADAM Hierarchy Theorem ^direction-17-3-adam

It would be interesting to understand how dense the possible values of $\mathrm{g}$ are. That is, find a function $f:\mathbb{N}\rightarrow\mathbb{N}$, as slow growing as we can, s.t. for every $n\in\mathbb{N}$ there is a policy $\pi$ for which

$$
n\leq\mathrm{g}(\pi)\leq f(n)
$$

### Direction 17.4: ADAM for finite-state policies ^direction-17-4-adam

Consider policies that can be implemented by a deterministic finite state machine. That is, such a machine has a finite state set $\mathcal{S}$, an initial state $s_0\in\mathcal{S}$ and a transition function $T:\mathcal{S}\times\mathcal{O}\rightarrow\mathcal{S}\times\mathcal{A}$. Suppose that $|\mathcal{S}|=n$. Clearly, the policy $\pi$ implemented by the machine has

$$
\mathrm{g}(\pi)\lesssim K(\pi)={O\left(n \log n\right)}
$$

**Open problem:** Is this bound on $\mathrm{g}(\pi)$ in terms of $n$ close to tight? Are there infinitely many $n\in\mathbb{N}$ s.t. for some $n$\-state policy $\pi$ it holds that $\mathrm{g}(\pi)={\Omega(n)}$?

### Direction 17.5: Inferring the utility function ^direction-17-5-inferring

Given an agentic policy, can we infer its utility function and prior? For simplicity, let's start with the case when the prior is known[^note-24]. For this purpose, we can consider the "semidescriptive" agency measure

$$
\mathrm{g}_0(\pi):=\sup_{U}\left(\min_{\pi':\mathbb{E}_{\zeta\pi'}[U]\geq\mathbb{E}_{\zeta\pi}[U]}K(\pi')-K(U)\right)
$$

Here, $\zeta:=\zeta_{M_0}$.

The obvious candidates for the utility function associated with $\pi$ are all $U$ that attain the supremum on the right hand side, or at least come close to attaining the supremum. Notice that the contrived utility function $U^\text{con}_\pi$ which just rewards behavior according to $\pi$ will typically fail this criterion: $K(U^\text{con}_\pi)\approx K(\pi)$ and hence the expression inside the maximum is $\lesssim 0$ when $U=U^\text{con}_\pi$.

As opposed to $\mathrm{g}$, $\mathrm{g}_0$ is not approximately UTM invariant, strictly speaking. However, it is still approximately invariant w.r.t. changing the UTM used for defining $K(\pi')$ and $K(U)$ while holding $\zeta$ fixed. That is, we imagine the Kolmogorov complexities defined w.r.t. some UTM $M_1$ and $\zeta$ w.r.t. a different UTM $M_0$, and we have approximate invariance w.r.t. changing $M_1$.

This raises the question of whether the inferred utility function is at least somewhat stable w.r.t. changing $M_1$. Intuitively, it is unlikely to be the case for arbitrary $\pi$: there is no canonical way to ascribe a utility function to a rock. However, we can expect it to be the case for agentic $\pi$, i.e. in the limit $\mathrm{g}_0(\pi)\gg 0$.

To simply matters even further, let's focus on the case $\mathrm{g}_0(\pi)=+\infty$. Moreover, let's assume that there is exists a computable $U$ s.t. $\pi$ is the associated AIXI[^note-25], i.e.

$$
\pi=\arg\max_{\pi'} \mathbb{E}_{\zeta\pi'}[U]
$$

We probably still don't have full uniqueness since small changes in rewards that happen a bounded number of times can be insufficient to affect the optimal policy. However, the _asymptotic_ rewards might be unique. Formally, I propose the following uniqueness conjecture.

**Definition:** Given a topological space $X$ and bounded function $u,v:X\rightarrow\mathbb{R}$, $u$ and $v$ are said to be _locally equivalent utility functions_ when for any $x\in X$ there is $V$ an open neighborhood of $x$, $\alpha>0$ and $\beta\in\mathbb{R}$ s.t. for any $y\in V$

$$
u(y)=\alpha v(y)+\beta
$$

**Conjecture:** Let $\pi^*$ be a policy and $U_{1,2}$ computable utility functions s.t. $\pi^*$ is AIXI for both $U_1$ and $U_2$. Then $U_1$ and $U_2$ are locally equivalent in the sense of the product topology on $(\mathcal{O}\times\mathcal{A})^\omega$.

\[**EDIT:** The Conjecture as stated is false, but other versions might be true, see discussion [here](https://www.lesswrong.com/posts/ZwshvqiqCvXPsZEct/the-learning-theoretic-agenda-status-2023?commentId=BF66hCBsNdBYBAWFx#comments).\]

## Direction 18: Infra-Bayesian Physicalism ^direction-18-infra-bayesian-physicalism

\[**EDIT:** We renamed it to "[Formal Computational Realism](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=cxnBT27fwudgFiAWq)" (FCR).\]

This research direction attempts to address Problem 4.

[Infra-Bayesian Physicalism](https://www.lesswrong.com/posts/gHgs2e2J5azvGFatb/infra-bayesian-physicalism-a-formal-theory-of-naturalized) (IBP) is a framework that builds on metacognitve agents, introducing a way to talk about hypotheses, priors and counterfactuals that does away with cartesian privilege. 

IBP comes with an agent-independent ontology for values, which provides another possible answer to Problem 3. There might be a natural way to translate hidden rewards to the IBP framework (see [original article](https://www.lesswrong.com/posts/gHgs2e2J5azvGFatb/infra-bayesian-physicalism-a-formal-theory-of-naturalized#Unobservable_states)), so these two answers are not mutually exclusive. However, the price tag is a bizarre constraint on values which we call the "monotonicity principle", for which I only have wildly speculative explanations at present. Hopefully, further research can shed some light on the question.

\[**EDIT:** We now have a seemingly satisfactory [solution](https://www.lesswrong.com/posts/DobZ62XMdiPigii9H/non-monotonic-infra-bayesian-physicalism) to monotonicity.\]

IBP also has an interesting relationship with ADAM: it seems that in that framework it's impossible to define an "ideal" agent, but we have to be content with defining an [agency measure](https://www.lesswrong.com/posts/gHgs2e2J5azvGFatb/infra-bayesian-physicalism-a-formal-theory-of-naturalized#Evaluating_agents). At the very least, "ideal agent" is a less natural object in that context.

See the [original article](https://www.lesswrong.com/posts/gHgs2e2J5azvGFatb/infra-bayesian-physicalism-a-formal-theory-of-naturalized#Future_research_directions) for concrete directions for further research.

# Physicalist Superimitation ^physicalist-superimitation

\[EDIT: We renamed it to "[Computational Superimitation](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=cxnBT27fwudgFiAWq)" (COSI).\]

## Motivation ^motivation

Physicalist Superimitation (PSI) is a (currently informal) approach to creating a rigorous alignment protocol, i.e a formal abstract model of a (hopefully feasible) AGI design that will be provably aligned under some (hopefully realistic) assumptions.

PSI is not the main motivation for LTA. The case for creating a mathematical theory of intelligent agents, both in general and even in particular via LTA, is much more robust than the case for PSI specifically. Moreover, I expect the theory produced by LTA to be applicable to analyzing many different alignment protocols (e.g. [IDA](https://arxiv.org/abs/1810.08575), [debate](https://arxiv.org/abs/1805.00899) or [AQRL](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=bgWYzaBgdPCzmrhBh)), not just to PSI. 

However, there are several reasons why discussing PSI here seems important:

-   PSI is a demonstration of one relatively concrete way how LTA might produce a full solution for alignment. Even if it's ultimately not the right approach, it gives us some intuition about how theory can cache out into novel solutions.
-   PSI offers unique advantages that all competing approaches lack AFAICT. Namely, I think that PSI is the only protocol that has a story for robust inner alignment. Certainly if we also require a plan for formalizing the story. At the same time it also doesn't handicap the AI's capability much[^note-26]: the AI is optimizing directly towards goals in the world, without e.g. routing through prediction or through human understanding of plans, and also without any constraints on the AI's knowledge, methods or magnitude of impact.
-   Thinking about alignment protocols and attack vectors is a useful way of noticing flaws in our models, or understanding their implications better. For example, thinking about Christiano's [acausal attack](https://ordinaryideas.wordpress.com/2016/11/30/what-does-the-universal-prior-actually-look-like/) made me formulate Problem 4, even though the problem can be justified without explicitly referring to alignment.

## Superimitation ^superimitation

The first component of PSI is _superimitation_: an agent (henceforth: the "imitator") that receives the policy of another agent (henceforth: the "original"), and produces behavior which pursues the same goals but _significantly_ _better_. (Later, we will apply the framework in a way in which the role of "policy" is played by something broader than externally visible behavior: the required "behaviorist" assumptions about values are a lot weaker than they might seem.) This is different from mainstream research in inverse reinforcement learning where the goal is usually producing behavior which is merely equally good, or better only by the virtue of being less noisy. For now, we will put aside the question of _how_ to obtain the original policy (but, see Agent Detection below). 

While PSI heavily leans on IBP, basic superimitation can be formulated and studied in a cartesian setting as well. In fact, starting the research from a cartesian setting seems like the reasonable approach. More concretely, the starting point can be ADAM and in particular Direction 17.5.

However, the successful completion of Direction 17.5 is would still fall short of a model of superimitation. Indeed, presumably the utility function can only be inferred (more or less) perfectly in the limit $\mathrm{g}\gg0$, but in this limit the original is already optimal and cannot be improved upon. And, for any finite $\mathrm{g}$, the inaccuracy of the inference might negate any improved optimization. Therefore we need to add to our model some mechanism by which the imitator gains an _advantage_ over the original.

One advantage mechanism is allowing the imitator more actions and/or observations. Examples of operationalizations:

-   The original action set is $\mathcal{A}$, the original observation set is $\mathcal{O}$, the imitator action set is $\mathcal{A}'$, the imitator observation set is $\mathcal{O}'$ and we are given surjections $f:\mathcal{A}'\rightarrow\mathcal{A}$ and $g:\mathcal{O}'\rightarrow\mathcal{O}$. The imitator optimizes the utility function $U':(\mathcal{O}'\times\mathcal{A}')^\omega\rightarrow\mathbb{R}$ which is obtained by _pulling back_ the original utility function $U:(\mathcal{O}\times\mathcal{A})^\omega\rightarrow\mathbb{R}$ using $f$ and $g$. (One problem with this is: the AI having e.g. the apparent experience of a person enjoying themself is very different from the person having that experience.)
-   The original and the imitator act in parallel, like in [CIRL](https://arxiv.org/abs/1606.03137) (but, unlike in CIRL, the imitator knows the original's full policy in advance), the imitator can observe the original's observations and actions (as well as its own), and optimizes the original's utility function. (Some problems with this are: it is an [experience machine](https://en.wikipedia.org/wiki/Experience_machine), not to mention that it's unclear how to practically implement an imitator that can fully observe the original.)

The parenthetical issues related to the domain of the utility function can hopefully be addressed given a solution of Problem 3. But, even putting these aside, this mechanisms seems somewhat disappointing: we want the AI to be superhuman not only thanks to better input/output channels, but also thanks to some deeper notion of "cognitive power". In other words, the resulting system might be very uncompetitive.

An improved advantage mechanism is suggested by the framework of metacognitive agents. The imitator can have superior computing hardware which allows it run computations faster than the original (via the internal interface), or even run computations that the original cannot run[^note-27]. It has some formal similarity to the first mechanism, since the computing hardware can be regarded as a type of input/output channel, but seems like a better model of "cognitive power".

### Applicable to humans ^applicable-to-humans

I often hear objections along the lines of "but humans don't have utility functions / are not rational / are not coherent / are not agents". I think that that reasoning is confused.

I already touched on this topic in the section [[#^nonproblem-expected-utility|Nonproblem]] above. But, in the context of alignment, there is a different important argument: alignment is fundamentally a _normative_ problem. Whenever we talk about whether an AI is "aligned" or "good" or "safe" we're using value-laden concepts that only makes sense within a _model_ (approximation) in which we actually possess (more or less) well-defined values. Whenever we discuss what AI design we should _choose_, we're working on a problem that only makes sense within a _model_ in which we are rational agents that make choices according to our values. Let's call this model "the anthroposinepic[^note-28] view".

This is not to say that the anthroposinepic view is a perfect description of reality. The map is not the territory, all models are wrong - but some are useful. For example, "the center of mass of the sun" is also not a well-defined concept: it's not clear which particles are part of the sun, in QFT particle positions are inherently fuzzy within the Compton wavelength, and in quantum gravity _any_ notion of position is probably approximate at best. Nevertheless there are many contexts in astrophysics in which speaking of the center of mass of the sun is perfectly sensible. Similarly, there are contexts in which the anthroposinepic view is perfectly sensible: in particular normative questions, since they assume this view from the onset!

Another objection of similar flavor is: what if humans are actually made of multiple coexisting agents (see e.g. [Sotala](https://www.lesswrong.com/s/ZbmRyDN8TCpBTZSip)), or have dynamically inconsistent preferences (i.e. a utility function that varies over time, such as [hyperbolic discounting](https://en.wikipedia.org/wiki/Hyperbolic_discounting))? My answer is: maybe it means that we will have to extend the framework to deal with those possibilities. But it's also possible that it's unnecessary or that it works out "automatically": multiple agents (coexisting or distributed along the subjective timeline) behave effectively as a single agent (thanks to superrationality). My methodology it to always start with the simplest model (in this case, humans as unitary agents) and only go beyond it when:

-   The simple model is well-understood.
-   It is clear that the simple model is inadequate.

Most importantly, I don't think this debate can be definitely resolved purely by philosophical arguments. Instead, we should study the emerging theory, check whether it satisfies intuitive desiderata, cross-reference it with cognitive science, and see what it says about the edge cases in which philosophical confusion arises. If the theory is correct, it will ultimately serve as a source of intuition which will lay all philosophical confusion to rest. And if it isn't, well, then we will see where it breaks and grow wiser from that too.

## Agent Detection ^agent-detection

Superimitation assumes we can access the original's policy. In the context of an alignment protocol, this assumption has major issues:

-   Maybe we can observe human behavior over time, but how do we know what the human would do in counterfactual scenarios?
-   Where to draw the boundary around the original agent? (related: Critch's "boundaries" [sequence](https://www.lesswrong.com/s/LWJsgNYE8wzv49yEc)) What constitutes human input/outputs? Retina illuminance and muscle contraction? Neuron membrane potentials on the physical boundary of the brain? Of the cortex? Is inner monologue part of input/output?
-   Even if we know where to draw the boundary, how do we point the AI to this boundary? If we e.g. connect the human's muscles to sensors that send signals to the AI, will the AI learn a "pointer" to muscles, or a pointer to the sensors?

PSI addresses this by combining IBP and ADAM. IBP provides us with a rigorous notion of "which computations is the universe running". ADAM provides us with a rigorous way to decide which sequences of computations are agents. Putting the two together should allow specifying an "agent detector": a mathematical operator that transforms any given hypotheses about the universe into the collections of agents that inhabit this universe. 

This can solve the problems above modulo the question of _which_ agent should we superimitate (for this, see User Identification below). That said, I don't know how the solution would cache out in practice for humans. It would be fascinating to combine this theory with brain science when the former is much more mature. Speculatively, I suspect that a metacognitive version of ADAM would interpret some of human inner mental life as input/output through the internal interface.

Also, I think that there might be some formal relation between this "physicalist agent detector" and some version of Garrabrant's [Cartesian Frames](https://arxiv.org/abs/2109.10996), but I won't try to articulate it here.

## User Identification ^user-identification

We don't want the AI to superimitate any and all agents. Some of those agents might be descendants of the AI. Some of those agents might be other AIs, aliens and animals. We don't necessarily want the AI to superimitate humans who lived in the past either.

For now, let's make the simplifying assumption that there is a single human we want the AI to imitate: the "user". Generalizing the method to groups of humans is left as an exercise to the reader[^note-29].

It [seems](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=oFCXkLAMbYXWLEs2W) that IBP has a natural notion of causality. Since IBP is a computationalist framework, this notion talks about causal relationships between _instantiated computations_. Specifically, the results of some computations control the instantiation or input[^note-30] of other computations. Since an agent is a type of computation, this gives us a notion of causality between agents: the action Alice takes in a particular Alice-counterfactual can affect the observation Bob makes in a particular Bob-counterfactual.

We can use causality to design a protocol for user identification. For example, imagine that the AI wakes up in a room with the user. The user can observe all of the AI's outputs (e.g. characters on a terminal) and the AI can observe many of the user's outputs (e.g. through a camera pointed at the user). This creates a short and tight causal loop between the user and the AI during the AI's early history that doesn't exist between the AI and any other agent[^note-31].

Moreover, we can use causality to specify the point on the user's subjective timeline at which the AI begins to influence them. The AI is designed to superimitate only the user's _past_: this way there is no perverse incentive to modify the user. Since agents in this framework are _programs_, this still allows access to the user's entire policy. (Although we still need a to disambiguate between equivalent problems, probably based on description complexity.)

## Full Specification ^full-specification

We can now put all the pieces of PSI together:

1.  For each hypothesis in the prior:
    1.  Identify all agents.
    2.  Out of all agents, identify the user.
    3.  If there are multiple users or no user, discard this hypothesis.
    4.  Infer the user's utility function.
2.  Choose policy that maximizes prior expected utility (where in each hypothesis, the utility of its respective user is counted).

At least, this is the simplest version. The above is probably not the best way to aggregate preferences across hypotheses, since, for example, it doesn't facilitate acausal trade. Here are additional steps that can fix it

-   (Step 3) For each hypothesis, infer the user's prior.
-   (Step 4) Perform Nash bargaining between all possible users (with their respective priors and utility functions), using the previously selected policy as a disagreement point.

Notice that all this is just an (informal) specification of the function we're optimizing, it's _not_ the algorithm used for optimization. Similarly to how asymptotic Bayes-optimality can be achieved (for certain priors, e.g. small MDPs) by a feasible learning algorithm, without actually tracking every possible hypothesis and calculating the true Bayesian update, this specification can (hopefully) be approximated by some feasible algorithm the details of which we currently don't know (and which we will only begin to describe after substantial additional progress on the foundational part of LTA).

## Alignment Guarantee ^alignment-guarantee

### Formal Alignment Criterion ^formal-alignment-criterion

How to formally define alignment? An appealing approach is, formalizing the following criterion:

**Criterion A:** _An AI is (approximately) aligned when it (approximately) optimizes the expectation of the user's utility function_ $U_\mathrm{usr}$ _with respect to the user's beliefs_ $\Theta_\mathrm{usr}$.

Indeed, if I am the user, and I am choosing which AI to run, and I am an agent with a utility function $U_\mathrm{usr}$ and beliefs $\Theta_\mathrm{usr}$, clearly it is rational for me (given my subjective epistemic vantage point) to choose an AI satisfying Criterion A.

This might seem confusing at first: shouldn't I want the AI to have more accurate beliefs than the beliefs I hold myself? But, this isn't a contradiction. If we imagine the AI as having access to more _new evidence_ than the user, then starting from the same beliefs it arrives at a better outcome. This is closely related to the "advantage mechanisms" we discussed in the section on superimitation.

We will call the part of Criterion A about $U_\mathrm{usr}$ _axiological alignment_. It is more or less the same as "outer alignment". We will call the part of criterion A about $\Theta_\text{usr}$ _epistemic alignment_. It is closely related to (and implies) "inner alignment". The last point might be confusing so let's dwell on it a little.

Inner misalignment is usually defined as the formation of malign mesa-optimizers: models produced by the learning algorithm which are in themselves malign agents (see [Hubinger et al](https://arxiv.org/abs/1906.01820)). In learning theory, possible models correspond to _hypotheses_ in the hypothesis class of algorithm. If the AI's starting beliefs are sufficiently different from $\Theta_\mathrm{usr}$ (it is epistemically misaligned), it might converge to a hypothesis that the user would not have endorsed. Such a hypothesis may lead to actions that are catastrophic from the user's point of view: for example, because the hypothesis encodes a malign agent. Two (not mutually exclusive) examples:

-   Christiano's acausal attack, where the malign hypothesis is a certain _simulation hypothesis_.
-   If the AI is a metacognitive agent that dogmatically believes running computations through the internal interface _never_ has side effects, it might end up running a simulation of a malign agent which will escape the "box". (This is a [non-Cartesian daemon](https://www.lesswrong.com/posts/5bd75cc58225bf0670375575/the-learning-theoretic-ai-alignment-research-agenda#Taming_daemons).)

Finally, notice that Criterion A is an approach to formalizing _alignment_, not formalizing [corrigibility](https://arbital.com/p/corrigibility/). Corrigibility seems to me a not especially natural concept, which is henceforth especially difficult to formalize and therefore also especially difficult to implement. For this reason, I am relatively pessimistic about approaches based on corrigibility (which PSI is not). That said, some weak versions of corrigibility might be feasible, e.g. the [Hippocractic principle](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=jMitxvhFceaheD5zb).

In the following subsections, I will give a rough outline of why I think that it might be possible to prove a formal alignment guarantee about PSI, along the lines of Criterion A.

### Axiological alignment of PSI ^axiological-alignment-of-psi

The axiological alignment of PSI relies on the ultimate success of the ADAM research direction (in conjunction with the necessary parts of the rest of the foundational programme). However, the fact PSI relies on physicalism makes the following problem especially acute: _should PSI use cartesian-ADAM (i.e. model the user as a cartesian agent) or physicalist-ADAM (i.e. model the user as a physicalist agent)?_

Currently I see the following possibilities:

-   Humans should be regarded as physicalist agents, PSI should be based on physicalist-ADAM and the AI should be an IBP agent. This would require explaining why the monotonicity principle can be applicable to the "human reflective equilibrium". \[**EDIT:** Seems like this is [not necessary](https://www.lesswrong.com/posts/DobZ62XMdiPigii9H/non-monotonic-infra-bayesian-physicalism).\] While I can imagine _some_ ways this can happen, they all require biting bullets. Alternatively, it might be possible to extend or overhaul the IBP framework, in a way that gets rid of monotonicity.
-   Humans should be regarded as cartesian agents and PSI should be based on cartesian-ADAM. Instead of an IBP agent, the AI should be a [_transcartesian_](https://www.lesswrong.com/posts/dPmmuaz9szk26BkmD/vanessa-kosoy-s-shortform?commentId=HvfuKrBuA2iRxgfsy) agent: i.e. based on some framework for agents which assign cartesian privilege to a _different_ agent (in this case the user). I can see a sketch of how this would be formalized (using similar mathematical building blocks as IBP), but this is very early stage at the moment.
-   Humans should be regarded as cartesian agents, PSI should be based on cartesian-ADAM but the AI should still be an IBP agent. The problem is, this requires translating the user's cartesian utility function into a physicalist utility function that PSI can optimize (e.g. using the techniques in [section 3](https://www.lesswrong.com/posts/gHgs2e2J5azvGFatb/infra-bayesian-physicalism-a-formal-theory-of-naturalized#3__Constructing_loss_functions) of the article about IBP). Because of the monotonicity principle, this would mean PSI is not really axiologically aligned: the user might place negative value on running certain computations which PSI will ignore. However, _maa...aaybe_ the difference is not significant, since PSI doesn't have strong incentives to instantiate those computations.

### Epistemic alignment of PSI ^epistemic-alignment-of-psi

The case for the epistemic alignment of PSI relies on the following (informal) conjecture:

**Physicalist Agreement Conjecture (PhyAC):** _Two IBP agents in the same universe that start with similar priors, and share most of their evidence, will converge to similar posteriors_[^note-32].

Notice that this is _not_ the case for _cartesian_ agents. This is because cartesian agents with _syntactically_ similar priors have very different priors _semantically_: each prior refers to the respective agent's actions and observation. Each agent assumes cartesian privilege for _itself_ but not for the other agent.

A strong demonstration for how it fails with cartesian agents is through simulation hypotheses: if Alice is much more influential than Bob, then Alice will assign a simulation hypothesis much more credence than Bob. Even if both Alice and Bob end up believing simulation hypotheses, they will often be _different_ simulation hypothesis: each will postulate the kind of simulators that would have incentives to simulate that person's respective subjective viewpoint.

On the other hand, for IBP agents this argument doesn't work anymore. For example, suppose that universe A has simulators with incentives to simulate Alice's viewpoint. Since Alice observes Bob fairly closely (by assumption of PhyAC), simulating Alice's viewpoint requires also running a simulation of Bob. Moreover, since Bob is an IBP agent, and IBP is computationalist, this implies that Bob expects to experience this simulation (created for Alice's sake) as well. Hence, both of them assign similar credence to being in universe A.

In the case of PSI, a possible objection is, maybe the simulators only need a low fidelity simulation of the user to fool the AI, which the user wouldn't identify as themself. This is unclear (since this low-fidelity simulation has to be good enough to be indistinguishable for the AI from the null hypothesis that we're not in a simulation). However, if this _is_ a concern, we can imagine a version of the agent detector that would also accept low fidelity simulations.

If the user is an IBP agent, PhyAC can be applicable to prove epistemic alignment of PSI. Is the user an IBP agent? This is unclear, but it's essentially the same debate as in the previous subsection.

Another concern is, even assuming that the user is an IBP agent, how similar is its prior to whatever prior we put into PSI? Presumably, the difference should be comparable to using Solomonoff induction with different UTMs, but hopefully not _too_ different (i.e. the associated bisimulation is not too complex). As long as we are in a learnable setting, this doesn't matter. In reality, there are traps, so it _does_ matter: but perhaps not critically. Alternatively, we might need to modify the specification of PSI to make stronger use of the inferred user prior in order to close this gap.

## A Plan ^a-plan

Assuming PSI _is_ the correct approach to aligning AI, how would we get from here to a practical implementation? I imagine the plan roughly as follows:

1.  Develop the foundational programme of LTA, until we have fairly good solutions to Problems 1-5 and maybe to other problems that will crystallize in the process.
2.  Continue fleshing out and improving PSI. I see some of it happening in parallel with step 1, but for the most part this is at best second priority until step 1 is much more advanced. In the process, I expect our model of PSI to evolve through roughly the following phases:
    1.  **Informal model:** The model is _inspired_ by mathematical ideas but is not fully rigorous yet. This where we are now. It gradually acquires more details and precision, until we are ready to formalize at least a part of it.
    2.  **Toy model:** The model is rigorous but makes simplifying assumptions that are completely unrealistic. We study the toy model's formal properties (including alignment), while gradually moving to more realistic assumptions. One axis along which this evolution can happen is computational resource constraints. For example, it can be the following progression:
        1.  Require only computability or not even that.
        2.  Require polynomial space in hypothesis description length. Alternatively, require polynomial time in number of hypothesis-states.
        3.  Require polynomial time in hypothesis description length.
    3.  **(Semi-)Realistic model:** The assumptions are sufficiently realistic that we could conceivably implement the model at least in some utopian scenario (e.g. if all capability research stopped and we had 100 years to bootstrap the AI). We continue moving to more realistic assumptions, while also gaining semiformal understanding about which properties of the model are crucial to alignment and which aren't.
3.  Study those questions outside of theoretical computer science the answers to which are needed as inputs to the AI's design or as parameters to the alignment guarantees. This might be possible in parallel to step 2 or at least to the late phases of step 2.
4.  Build a real-life implementation of PSI. This might be anywhere on the spectrum from (on one end) implementing an algorithm with formal guarantees and formally verifying the guarantees on the production code to (on the other end) implementing an algorithm which is only loosely based on the formal model, while using the understanding we gained from the theory to convincingly argue that the differences between the model and the implementation are immaterial. The algorithm might or might not bear strong resemblance to deep learning, depending primarily on the results of research into Problem 1. In any case, it will involve much engineering work and security mindset to make sure that the assumptions of the alignment guarantee actually apply.

# Summary ^summary

In this article, I tried to convey the following points:

-   LTA sets out to create a general mathematical theory of intelligent agents. It has a concrete, actionable plan for achieving this goal.
-   LTA also has an end-to-end proposal for solving alignment (PSI), although at this stage it is still fairly speculative. Nevertheless, this proposal brings some unique advantages.
-   LTA has a substantial number of fairly concrete, shovel-ready research directions. There is substantial room for accelerating LTA by recruiting researchers to attack many of those directions in parallel.

There is a lot of work and perhaps not that much time. I hope that this article will inspire more researchers to joint the effort. See you all in 2028[^note-33]!

[^note-1]: listed alphabetically by last name
[^note-2]: By "foundational part" I mean the theory of intelligent agents qua intelligent agents, as opposed to the "applied part" where we use this theory to study alignment per se.
[^note-3]: Sometimes we are content with "any except for a set of prior probability 0", such as when we only bound the Bayesian regret in a Bayesian online/bandit/reinforcement learning setting.
[^note-4]: See e.g. [Lattimore and Szepesvari](https://tor-lattimore.com/downloads/book/book.pdf) for an introduction to regret bounds, in particular section 38 talks about reinforcement learning.
[^note-5]: Here, we assume that the first observation comes before of the first action, in contrast to my usual convention, because this time it's more convenient.
[^note-6]: The diameter is the maximal expected time to reach one state from another state. The bound has to scale with $\tau$ since as $\tau\rightarrow\infty$, a trap can develop. Alternative parameterizations are also possible, such as using mixing time or [bias span](https://arxiv.org/abs/1906.05110). The latter might be advantageous since bounding the diameter also caps the number of states at $O(2^\tau)$, whereas bounding bias span allows an infinite number of states. On the other hand, the bias span depends on the reward function.
[^note-7]: Alternatively, we can consider geometric time discount $\gamma$, in which case $T$ is replaced by $\frac{1}{1-\gamma}$.
[^note-8]: The existence of a computationally feasible optimal policy is usually a much stronger condition than the computational feasibility of simulation: for example finding an approximately optimal policy for a POMDP is PSPACE-hard while simulating it in P. Of course there are degenerate cases in which the optimal policy is easy even though simulation is hard.
[^note-9]: See e.g. [Shalev-Shwartz and Ben-David](https://www.cs.huji.ac.il/~shais/UnderstandingMachineLearning/understanding-machine-learning-theory-algorithms.pdf).
[^note-10]: The name comes from [Kalai and Lehrer](https://www.jstor.org/stable/2951492).
[^note-11]: I haven't properly studied the prior work relating automata to category theory (which definitely exists) so I make no strong claims to originality here.
[^note-12]: The paper uses a theorem stated without proof, for which the citation given is "Lempp, Miller, Ng and Turetsky, 2010, unpublished, private communication". However, Lattimore kindly provided me with this unpulished communication upon request, and, to the best of my judgement, the proof is valid.
[^note-13]: Infra-Bayesian laws were originally called "belief functions" in the infra-Bayesianism sequence.
[^note-14]: I haven't done a sufficiently thorough literature survey, so there might already be such results.
[^note-15]: It's not just a law that depends on a point in the support of $\Theta$ because there is no disintegration theorem for infradistributions. See [this](https://www.lesswrong.com/posts/gHgs2e2J5azvGFatb/infra-bayesian-physicalism-a-formal-theory-of-naturalized#Turing_laws).
[^note-16]: While running _most_ programs doesn't have irreversible harmful side-effects, but it probably doesn't hold for _all_ programs: for example we can imagine code that uses some hardware exploit. In particular, this is related to what I previous called [non-cartesian daemons](https://www.lesswrong.com/posts/5bd75cc58225bf0670375575/the-learning-theoretic-ai-alignment-research-agenda#Taming_daemons). It should be possible to get guarantees that take this into account by e.g. somewhat randomizing the precise code we run each time (it might be related to quantilization).
[^note-17]: See e.g. [Kearns and Vazirani](https://direct.mit.edu/books/book/2604/An-Introduction-to-Computational-Learning-Theory) chapter 8, [Higuera 2004](http://pagesperso.lina.univ-nantes.fr/~cdlh/papers/bibliography_survey.pdf) and [Higuera 2010](https://www.cambridge.org/core/books/grammatical-inference/CEEB229AC5A80DFC6436D860AC79434F).
[^note-18]: As a consequence, this section carries an especially high risk of missing some pertinent known results that I'm unfamiliar with.
[^cite-19]: See e.g. [Vereshchagin and Shen](https://arxiv.org/pdf/1607.08077.pdf).
[^note-20]: The convention I'm using here doesn't normalize the sum of payoffs over time, i.e. $U_{\mathrm{tot}}=\sum_{i=0}^\infty\gamma^iU_i$ and the probability of playing a strategy is proportional to $\exp(\lambda\mathbb{E}[U_\mathrm{tot}])$.
[^note-21]: It would be more natural to say that the hidden environment is an equivalence class of such objects, where two are considered equivalent if it is not possible to distinguish them in terms of actions and states in $\mathcal{S}_0$. However, the distinction is not critical for the exposition.
[^note-22]: See e.g. chapter 37 in [Lattimore and Szepesvari](https://tor-lattimore.com/downloads/book/book.pdf).
[^note-23]: Or maybe just TMs, that would still allow making sense of $\zeta_M$ as the lower semicomputable environment computed by $M$.
[^note-24]: If we want to infer the utility function and the prior simultaneously, we probably need to take into account that some ways to redefine both of them together produce an equivalent decision problem. Hence, it makes sense to focus on recovering their _product_. Formally, any environment $\zeta$ corresponds to a measure $\zeta^\text{pol}$ on $(\mathcal{O}\times\mathcal{A})^\omega$ s.t. for any $\pi$, the distribution induced by $\zeta$ and $\pi$ is equal to $\zeta^\text{pol}\chi_\pi$, where $\chi_\pi$ is the function that's 1 on sequences compatible with $\pi$ and 0 otherwise. We can then define the _utility measure_ to be the product $U\zeta^\text{pol}$.
[^note-25]: This doesn't seem to automatically follow from the assumption $\mathrm{g}_0(\pi)=+\infty$. However, it might be possible to show that there is always at least an uncomputable utility function that can be computed with a slow-growing amount of advice.
[^note-26]: There might still be alignment overhead. Specifically, (i) the unusual structure of the loss function, (ii) prior shaping to deal with potential traps and (iii) prior shaping to deal with potential side-effects of computations, might incur overhead. We need to return to this question when we have better models. Maybe the overhead is small, or maybe we can prove that significant overhead is unavoidable.
[^note-27]: Technically, the mathematical analysis will probably need to focus on the asymptotic in which the agents can run all computations, but the original and the imitator can converge to this limit with different speeds.
[^note-28]: from Greek: anthropos (human) + sinepis (coherent, according to ChatGPT)
[^note-29]: Speculatively, we might not even have to do that: the AI itself can facilitate superrational cooperation between all agents who could affect the creation of this or similar AI.
[^note-30]: Input is a special case of instantiation: saying that program $p$ runs with input $x$ is equivalent to saying that the computation $p(x)$ is instantiated.
[^note-31]: We would have to be careful to set the ADAM threshold correctly and make sure the room indeed doesn't contain other agents. Otherwise, we are risking the AI version of "[The Fly](https://en.wikipedia.org/wiki/The_Fly_\(1986_film\))".
[^note-32]: In some "behaviorist" sense. IBP doesn't really have an update rule, and therefore there is no well-defined "posterior" in general.
[^note-33]: I hope...

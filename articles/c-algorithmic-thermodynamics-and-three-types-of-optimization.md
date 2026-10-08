---
title: "Algorithmic thermodynamics and three types of optimization"
author:
  - "Daniel C"
  - "Aram Ebtekar"
source_url: "https://www.lesswrong.com/posts/CJRxQiTKEzior7jGq/algorithmic-thermodynamics-and-three-types-of-optimization"
published: 2025-12-08
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "opus"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "Context: I (Daniel C) have been working with Aram Ebtekar on various directions in his work on algorithmic thermodynamics and the causal arrow of time…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_Context: I (Daniel C) have been working with Aram Ebtekar on various directions in his work on_ [_algorithmic thermodynamics_](https://arxiv.org/abs/2308.06927) _and the_ [_causal arrow of time_](https://www.mdpi.com/1099-4300/26/9/776)_. This post explores some implications of algorithmic thermodynamics on the concept of optimization. All mistakes are my (Daniel's) own._

A typical picture of [optimization](https://www.lesswrong.com/posts/znfkdCoHMANwqc2WE/the-ground-of-optimization-1) is when an agent causes the environment to have a convergent attractor: When you have an agent that is trying to steer a system towards particular target configurations, you can predict that the system will likely end up in those target configurations even if you have significant uncertainty over the initial configurations of the subsystem. 

Some examples:

-   When a person tries to build a house, the raw materials might initially be scattered in various possible locations, but they will all end up in a narrow configuration where the house is built according to the architect's plans.
-   When a chess player is trying to checkmate their opponent, the pieces might start in many possible mid-game configurations, but a skilled player will reliably steer many of these initial positions toward configurations where their opponent's king is trapped.

This view of optimization can be framed as a form of entropy reduction. Initially, we have high uncertainty about which configuration the system occupies: There are many possible initial states the raw materials or chess pieces could be in. The optimizing process reduces this uncertainty, concentrating probability mass from a broad initial distribution into a tight final distribution.

However, note that this entropy reduction cannot occur globally for two related reasons: the second law of thermodynamics and the reversibility of the laws of physics. The second law directly states that the total entropy of an isolated system tends to increase over time, which forbids global entropy reduction. Similarly, reversibility of the microscopic dynamics requires that each initial microstate maps to a distinct final microstate, which is incompatible with our "convergent attractor" picture where many initial states funnel to the same final state. In fact, within the framework of stochastic thermodynamics, the derivation of the second law is closely linked to the reversibility of the underlying physics. Roughly speaking, the reversibility of the underlying laws of physics allows us to define coarse-grained macrostates of the system where the dynamics are approximately Markovian. Once we have this Markovian structure,  we can derive the second law of thermodynamics as a mathematical consequence:

:::callout {title="Second law from reversibility of physics" collapse="closed"}
Stochastic thermodynamics operates on coarse-grained macrostates rather than exact microstates.[^cite-ebtekar-hutter-theorem-1] Let $X$ denote the space of macrostates. We translate reversibility of underlying physical laws into Markovian dynamics on these macrostates, allowing us to model thermodynamic systems as Markov processes.

For systems with discrete state spaces and time evolution, the translation is straightforward. Macrostates form a partition over the microstates of an underlying system that evolves deterministically and reversibly. The transition probability $P(y,x)$ is simply the fraction of microstates in $x$ that evolve into macrostate $y$ after one time step. We define $\pi$ as the stationary measure of $P$—the (often unique) measure satisfying $P\pi = \pi$, where $P\pi(y)=\sum_{x\in X}P(y,x)\pi(x)$. 

For classical Hamiltonian mechanics where we have a continuous phase space, we discretize the phase space into cells and assume the cell dynamics are Markovian (known as a Markovian coarse-graining). The transition probability $P_{\Delta t}(y,x)$ represents the fraction of phase space volume in cell $x$ that flows into cell $y$ under time evolution for duration $\Delta t$. Liouville's theorem guarantees that phase space volume is preserved under Hamiltonian evolution, ensuring the stationary measure $\pi(x)$ corresponds to the Liouville measure (the phase space volume of cell $x$).

We define the **dual probabilities** as $\tilde{P}(x, y) := \frac{P(y, x)\pi(x)}{\pi(y)}$, which represent the fraction of the microstates in $y$ that were mapped from microstates in $x$. By Bayes' rule, these are the reverse-time transition probabilities (only) when $x$ is sampled from the stationary measure $\pi$. 

We define the **stochastic entropy** as $\hat{H}_\pi(x, \mu) := \log \frac{\pi(x)}{\mu(x)}$, which measures the entropy of an individual state. The **generalized Gibbs-Shannon entropy** $H_\pi(\mu) := \langle \hat{H}_\pi(X, \mu) \rangle_{X \sim \mu} = \sum_{x \in X} \mu(x) \log \frac{\pi(x)}{\mu(x)}$ is the expectation of stochastic entropy. Note that this differs from the standard Shannon entropy because we're operating on coarse-grained macrostates rather than uniform microstates. If the stationary measure $\pi$ is the counting measure with every macrostate equally likely (i.e., if the discrete cells in our Markovian coarse-graining have equal volume), then we can omit $\pi$ and recover the usual Shannon entropy.

Now, if we have $\mu$ as the initial distribution of $X$, which evolves to $P\mu$ under our transition probabilities, then the **stochastic entropy production** that occurs when we transition from the state $x$ to $y$ is

$$
\Delta \hat{H}_\pi := \hat{H}_\pi(y, P\mu) - \hat{H}_\pi(x, \mu)
$$

We will attempt to prove that its expectation, the **Gibbs-Shannon entropy production,** is nonnegative:

Actually, the derivation does not require stationarity ($P\pi=\pi$). In the general case, we define stochastic entropy production by $\Delta \hat{H}_\pi := \hat{H}_{P\pi}(y, P\mu) - \hat{H}_\pi(x, \mu)$, and the dual probabilities by $\tilde{P}(x, y) := \frac{P(y, x)\pi(x)}{P\pi(y)}\implies \frac{\tilde{P}(x, y)}{P(y,x)}=\frac{\pi(x)}{P\pi(y)}$

Given these,  we have:

$$
\begin{align*}&\left\langle 2^{-\Delta \hat{H}_\pi} \mid X \right\rangle \\&= \left\langle 2^{\hat{H}_\pi(X,\mu) - \hat{H}_{P\pi}(Y,P\mu)} \mid X \right\rangle = \left\langle \frac{2^{\log(\pi(X)/\mu(X))}}{2^{\log(P\pi(Y)/P\mu(Y))}} \mid X \right\rangle \\&= \left\langle \frac{\pi(X) P\mu(Y)}{P\pi(Y) \mu(X)} \mid X \right\rangle = \left\langle \frac{\tilde{P}(X, Y) P\mu(Y)}{P(Y, X) \mu(X)} \mid X \right\rangle \\&= \sum_{y \in \mathcal{Y}} P(y, X) \frac{\tilde{P}(X, y) P\mu(y)}{P(y, X) \mu(X)} = \frac{\sum_{y \in \mathcal{Y}} \tilde{P}(X, y) P\mu(y)}{\mu(X)} \\&= \frac{\tilde{P}P\mu(X)}{\mu(X)}\end{align*}
$$

Where $\langle\cdot|X\rangle$ denotes conditional expectation given the random variable $X$.

Then, by the law of total expectation, we have:

$$
\begin{align*}\left\langle 2^{-\Delta H_\pi} \right\rangle_{X\sim\mu} &= \left\langle \left\langle 2^{-\Delta H_\pi} \mid X \right\rangle \right\rangle_{X\sim\mu} = \left\langle \frac{\tilde{P}P\mu(X)}{\mu(X)} \right\rangle_{X\sim\mu} = \sum_{x \in \mathcal{X}} \tilde{P}P\mu(x) = 1.\end{align*}
$$

Applying Jensen's inequality to the above equality, we conclude that the **Gibbs-Shannon** entropy production is non-negative:

$$
\Delta H_\pi := H_{P\pi}(P\mu) - H_\pi(\mu) = \left\langle \Delta\hat{ H}_\pi \right\rangle \geq 0.
$$

In summary, the reversible, deterministic laws of physics at the microscopic level permit a Markovian coarse-graining into macrostates, where transition probabilities preserve the underlying reversibility through the dual probability relationship. From this Markovian structure, we can derive the second law of thermodynamics in the form of nonnegative entropy production.
:::

Given the reversibility of physics and the second law of thermodynamics, we cannot achieve global entropy reduction. Instead, optimization can only reduce the entropy of a subsystem, and we must ensure that total entropy does not decrease while the underlying microscopic dynamics remain reversible. This constraint changes our "convergent attractor" picture of optimization: while an optimizing agent can funnel a subsystem from many initial configurations toward a narrow set of target states, it can only do so by carefully managing the entropy balance with its environment, ensuring that the information squeezed out of the optimized subsystem is properly accounted for in the larger system.

# A typology of optimization under information conservation ^a-typology-of-optimization

Given the constraints imposed by reversibility and the second law of thermodynamics, can we classify all the ways an optimizing agent can maintain these requirements while reducing the entropy of a subsystem? That is, how can an agent achieve the "convergent attractor" behavior of optimization while ensuring that global entropy production remains non-negative?

Suppose that we decompose our universe into the agent $A$, the subsystem $S$ that the agent is trying to optimize, and the rest of the environment $E$. Optimization results in entropy reduction in the subsystem $S$, and we must make sure that the global entropy $H(A,S,E)$ doesn't decrease. There are three ways this can happen:

-   **Type 1**: The agent can dump waste heat into the environment during the process of optimization, counteracting the entropy reduction of the subsystem
-   **Type 2**: The agent can reduce the entropy of the subsystem through "measurement", and transfer the entropy of the subsystem into the agent's own memory.
    -   This is basically how Maxwell's demons work: In the classic setup for Maxwell's demon, we have a room of ideal gas divided by a partition. This partition has a small door that can be controlled to allow or block gas molecules from moving between the two sections. In principle, a "demon" can open this door each time a gas particle approaches from the left, and to close it each time a molecule approaches from the right. Eventually all the gas particles would all be on the right side of the room, resulting in entropy reduction as we would have less uncertainty about the positions of the gas particles.
    -   The reversibility of physical laws means the demon must retain information about where each particle originally started. To see this, suppose you observe a particle on the right side. Two possible pasts could have led to this—either the particle began on the right and stayed there, or it began on the left and the demon let it through. Since these two histories produce identical final arrangements of gas particles, you can't tell them apart just by observing the gas particles alone. Yet reversibility demands we could theoretically reconstruct the past from the present state. This is only possible if the demon's memory preserves a record of each particle's "past". Consequently, while the gas's entropy appears to decrease, the entropy of the demon's memory increases by at least as much, preventing reduction of global entropy.
-   **Type 3**: We've seen how to counteract entropy reduction of a subsystem by increasing entropy of either the environment or the agent. Is it possible to reduce entropy of the subsystem without increasing entropy elsewhere? Yep! Specifically, the agent can leverage its mutual information with the subsystem to perform optimization without entropy production. Consider the following setup[^cite-engines-of-cognition]:
    -   Suppose that the agent and the subsystem have some mutual information $I(S_t;A_t)$ with each other.
    -   For simplicity, assume that the environment is independent of both the agent and the subsystem, which means that the joint entropy $H(S_t,A_t,E_t)$ at time $t$ decomposes to $H(A_t)+H(S_t)- I(S_t;A_t)+H(E_t)$.
    -   We "erase" the copy of mutual information inside $S_t$ without making any changes to the agent or the environment. By erasing the mutual information in the subsystem, we have: 
        
        $$
        H(S_{t+1})=H(S_t)-I(S_t;A_t)
        $$

        and $I(S_{t+1};A_{t+1})=0$. So there is entropy reduction in the subsystem.
        
        The joint entropy becomes:

        $$
        H(A_{t+1})+H(S_{t+1})+H(E_{t+1})= H(A_t)+H(S_t)- I(S_t;A_t)+H(E_t)
        $$

        which is exactly the same as before. The mutual information between the agent and the subsystem allows us to reduce entropy of the subsystem without increasing entropy in either the agent or the environment.
        
    -   Another way to interpret this is to reconsider the setup of Maxwell's demon: The Maxwell's demon performs the measurement and reduces entropy of the room in a single step, but alternatively we can break down the interaction so it "copies" information about the gas particles first, and then uses that information to control the door & reduce entropy. In this second step, the demon would be leveraging the mutual information between the room and itself to reduce entropy of the room, and it can do so without (further) increasing entropy in its own memory.

To recap, there are three ways that an embedded agent can optimize a subsystem under information conservation:

-   Optimize a subsystem while dumping waste heat into the environment
-   Optimize a subsystem through "measurement", absorbing its complexity into the agent's memory
-   Leverage existing mutual information to optimize a subsystem by "erasing" the copy of mutual information in the subsystem. 

# Entropy should be objective ^entropy-should-be-objective

Entropy is supposed to capture "the capacity to do work", which is really the same as the capacity to perform optimization. Consider again the setup of Maxwell's demon: The demon stores information about the gas particle configurations inside its own memory, thereby increasing the entropy of its memory. If the demon's memory has a finite state space, then the difference between the size of the demon's memory and the memory's existing entropy represents the demon's remaining capacity to do work, as that's the amount of "free memory" that can be used to store further information about the room of ideal gas. A greater amount of entropy leads to a smaller amount of "free memory" available for optimization. In particular, the amount of free memory should be an objective feature of the memory state itself, since it's supposed to represent the demon's objective capacity to perform optimization on the room of ideal gas.

:::callout {title="Details" collapse="closed"}
To formalize this more rigorously, suppose that the state space of the demon's memory is $B^m$ ($B := \{0,1\}$), the demon may store information as a binary string inside its memory, and we always mark the end of the binary string by 1 to separate it from the "free memory".

In other words, the demon's memory contains a string of the form $s10^n\in B^m$, where $s$ is a binary string and $n=m-|s|-1$. We can think of $n$ as representing the size of "free memory" that can be used to store information and therefore perform optimization, whereas $|s|$ represents the amount of used memory. In particular, for each $k$, we group all strings of the form $s10^n$ into the same macrostate, labeled by $k:=|s|=m-n-1$.

Now, if the stationary measure assigns equal mass to all strings in $B^m$, then the entropy of the macrostate $k$ will be exactly $k$, since there are exactly $k$ random bits given this macrostate (the other $m-k-1$ bits taken up by $10^n$ are deterministic).

As a result, when a demon stores new information inside its memory, it will have to use up more memory and therefore increase $k$. Entropy production occurs because we're "forgetting" the exact microstate the memory is in when we condition on the macrovariable.
:::

However, this intuitive objectivity comes into conflict with existing definitions of entropy, as they rely on a subjective distribution. For instance, in stochastic thermodynamics, the stochastic entropy (or Shannon codelength) of a state $x$ given a distribution $\mu$ is defined as $\hat{H}(x,\mu)=-\log\mu(x)$ when the stationary measure is the counting measure, with our familiar Gibbs-Shannon entropy defined as the expectation of the Shannon codelength. In particular, the entropy of an individual state is undefined unless we also specify the distribution $\mu$. To translate this to the setting of Maxwell's demon, we would have to say that the demon's "capacity to do work" somehow depends on our subjective distribution over the memory states of the demon, which raises puzzling questions such as: "If our subjective distribution over the memory states has changed, does that affect the demon's actual capacity to do work?" It seems obvious that demon's physical ability to perform useful work on the gas particles should not depend on an external observer's beliefs about its memory configuration. Yet standard formulations of entropy seem to make this objective physical capacity fundamentally observer-dependent.

In contrast with the subjectivity in traditional definitions of entropy, [algorithmic thermodynamics](https://arxiv.org/abs/2308.06927) defines the information content of a physical state as an objective feature of that state. Similar to stochastic thermodynamics, it relies on a Markovian coarse-graining of the system with coarse-grained state space $X$. However, instead of defining a subjective distribution $\mu$ over $X$, it simply assigns a binary string encoding to each coarse-grained state $x\in X$. Under the counting measure, the algorithmic entropy of a state $x$ reduces to the Kolmogorov complexity of its binary encoding $K(x)$, which measures the length of the shortest program that can generate that encoding. _Intuitively, a state in which all particles are concentrated in one location would have low entropy, because the repeated coordinates can be printed by a short program._ While algorithmic entropy depends on a choice of universal computer, it has been argued that the effect of this dependence is small for all realistic pairs of computers we might want to compare[^cite-ebtekar-hutter-page-5], allowing us to treat algorithmic entropy as a state function that represents system's actual capacity to do work from an individual state.

In algorithmic thermodynamics, we also have a version of the second law of thermodynamics that originates from Levin's principle of randomness conservation, giving probabilistic guarantees on the nondecrease of algorithmic entropy. Additionally, it offers a new interpretation of Gibbs-Shannon entropy: while algorithmic entropy captures the system's actual capacity to do work given an individual state, the Gibbs-Shannon entropy represents the _expected_ capacity to do work when our state is sampled according to a prior distribution $\mu$, and when that distribution is known a priori.

When we analyze Maxwell's demon under the lens of algorithmic thermodynamics, we find that if the content of the demon's memory is somehow compressible, then the demon can in principle leverage universal computation to compress that content, thereby freeing up more available capacity to store information and perform optimization. On the other hand, if the content of its memory were incompressible, then the unused memory represents the demon's actual remaining capacity to do work, which is objective because there is no way to increase available memory without physically destroying information. This capacity does not depend on our subjective distribution over the demon's memory states; the compressibility of the memory state is an intrinsic property of the physical configuration itself, making the demon's optimization capacity observer-independent.

# Implications of algorithmic thermodynamics on optimization ^implications-of-algorithmic-thermodynami

What are the implications for our understanding of optimization now that we've refined our understanding of entropy through algorithmic thermodynamics? How does this foundation change our analysis of the three types of optimization we identified earlier?

-   For the first type of optimization where we're dumping waste heat into the environment, algorithmic thermodynamics tells us that if the system's initial state has any compressible structure or patterns, then we can use universal computation to find a compressed representation of that waste heat before releasing it into the environment. This compression process reduces the amount of entropy we ultimately produce in the environment. (Note that this compression must happen before the waste heat mixes with and thermalizes in the environment, as thermalization destroys the compressible structure.)
-   For the second type of optimization, where the agent optimizes a subsystem through measurement, we've already seen how this works with Maxwell's demon: if the configuration of gas particles turns out to be compressible, the demon can leverage this compression to reduce the memory required for a given amount of optimization. Importantly, there is a dual relationship here—while the algorithmic entropy of the demon's memory measures the demon's remaining capacity to do work, the algorithmic entropy of the ideal gas configuration represents the minimum resources required to perform that work. 
-   For the third type of optimization where we leverage mutual information to optimize a subsystem, algorithmic thermodynamics tells us that the relevant notion is algorithmic mutual information. Importantly, algorithmic mutual information is an objective feature derivable from the physical states of the agent and subsystem: We need only consider how much the shortest description length of one system changes when the other is given, rather than whether they are "correlated" under some subjective distribution. In the Maxwell's demon scenario, if the room's gas configuration has low algorithmic entropy, the demon can use a short program to compute that configuration, thereby leveraging algorithmic mutual information to erase entropy in the room. The duality we observed earlier appears again here: the Kolmogorov complexity of the room's gas configuration both represents the minimal memory required to store measurements during Type 2 optimization, and represents the minimal amount of knowledge the demon needs to clear the room's entropy during Type 3 optimization. 
-   More broadly, in agent foundations we often model agents as having subjective beliefs about the distribution of their environment; algorithmic thermodynamics reminds us that these beliefs must be physically encoded within the agent somehow, and this physical encoding has a definite amount of algorithmic mutual information with the environment, which objectively determines the agent's capacity for optimization. This also clarifies the apparent subjectivity in traditional definitions of entropy: The subjectivity seemed problematic because when our subjective distribution over Maxwell's demon's memory states changes, it appears as though the demon's actual capacity to perform optimization also changes. But when we update our subjective distribution, that update must be physically represented in our own minds—we have gained algorithmic mutual information with the demon's memory state. This mutual information is real and can actually be leveraged to help free up the demon's memory (via Type 3 optimization), which is why the demon seems to have more capacity to do work from our informed, embedded perspective.

# Takeaways ^takeaways

-   Due to the second law and reversibility of physics, we cannot have reduction in global entropy, which means an agent can only perform optimization on a subsystem while total entropy production remains non-negative.
-   There are three ways this can happen: An agent can reduce entropy of a subsystem by expelling waste heat in the environment, absorbing entropy into its memory, or leveraging mutual information with the subsystem for optimization.
-   Entropy is supposed to measure a system's capacity to perform optimization. Algorithmic entropy makes this an objective property of the individual state.
-   Under this reframing of entropy, algorithmic thermodynamics allows us to leverage universal computation to compress the waste heat produced in Type 1 optimization, and save the memory required in Type 2 optimization as well as the bits of knowledge required in Type 3 optimization.

[^cite-ebtekar-hutter-theorem-1]: Theorem 1 in Aram Ebtekar and Marcus Hutter. Foundations of algorithmic thermodynamics. Physical Review E, 2025.
[^cite-engines-of-cognition]: [Engines of cognition](https://www.lesswrong.com/posts/QkX2bAkwG2EpGvNug/the-second-law-of-thermodynamics-and-engines-of-cognition) explains the same idea
[^cite-ebtekar-hutter-page-5]: Page 5 of Aram Ebtekar and Marcus Hutter. Foundations of algorithmic thermodynamics. Physical Review E, 2025.

---
id: 'fd3f1ec8-9866-4818-ab2f-0c65963f704c'
title: "C.4.7 Condensation in context"
tldr: "How condensation relates to natural latents, sufficient statistics, common information, computational mechanics and graphical models, what information theory leaves out, and the link to AI safety."
summary_for_tutor: "This is Section 4 (Condensation in context) of Iliad worksheet C.4 Condensation: 4.1 What the result says, 4.2 Connections to prior work (natural latents, sufficient statistics, common information, computational mechanics, graphical models and the information bottleneck), 4.3 What information theory leaves out (an encoding and access to its inverse, rare events and average error), 4.4 The connection to AI safety (five steps from corresponding information to safer systems) and 4.5 Discussion with three prompts. The student should keep the distinction between informational correspondence and learning, finding or using a translation."
authors:
  - Satya Benson
source_url: https://iliad-intensive.org/interpretability/condensation/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Condensation in context

\### 4.1 What the result says

LVM alone leaves considerable freedom. The additional reconstruction and Markov conditions constrain where shared information can reside. The correspondence theorem compares two models satisfying these conditions, that is, two joint laws extending the same observable law: their towers at the same address determine one another, exactly or with a controlled conditional-entropy error. The theorem does not give a learning algorithm, and a perfect condensation need not exist, as Section 2.2.1 shows.

This provides a conditional sense of objectivity: once the observables and the conditions are fixed, agreement in information content follows from each model's relationship to the observations, not from a shared vocabulary. The theorem does not choose the observables, and changing them may change the information that must correspond.

\### 4.2 Connections to prior work

\#### 4.2.1 Natural latents

Wentworth and Lorell ask when one agent's latent is guaranteed to be a function of another's (Wentworth & Lorell 2025). A latent $$\Lambda$$ over observables $$X_{1},\ldots,X_{n}$$ is a *mediator* if the $$X_{i}$$ are independent given $$\Lambda$$, and a *redund* if it is determined by each $$X_{i}$$ individually; a *natural latent* is both. Their first theorem, that a mediator determines any redund, is for two observations the two-witness lemma (Lemma 2.8) with the observations as witnesses. Two natural latents over the same observables therefore determine one another.

For two observations, the top latent of a perfect condensation is a natural latent: reconstruction makes $$Y_{\{1,2\}}$$ a redund, and the Markov condition with LVM makes $$X_{1},X_{2}$$ independent given it. Condensation asks for a latent at every address rather than one latent for the whole family, and its correspondence theorem compares all the towers at once. Gillen and Chiang show that natural-latent agreement is a special case of condensation's agreement theorem (Gillen & Chiang 2026).

\#### 4.2.2 Sufficient statistics

For a fixed joint law of $$(X,V)$$, a statistic $$T=f(X)$$ is sufficient for predicting $$V$$ when

$$
I(X;V\mid T)=0.
$$

Knowing $$X$$ then gives no predictive information about $$V$$ beyond $$T$$. For finite alphabets, grouping values $$x$$ with the same conditional distribution $$P(V\mid X=x)$$ gives a minimal such statistic, on the support of $$X$$. This differs from parametric sufficiency, where the conditional law of the sample given a statistic must be independent of the unknown parameter. Both formulations ask which distinctions must be retained for an inference task.

Predictive sufficiency does not say that $$T$$ determines the realized value of $$V$$. Condensation's LVM condition does demand determination, using the whole contributing family, including residual variables.

A sufficient statistic is by construction a function of $$X$$. A latent need not be, because reconstruction is asked for only up to a defect: that leaves room for latents which are parameters of a law rather than functions of the observations. The additional question here is how to organize a family of latent parts across many specified observables. See Fisher 1922 and Shalizi's account of predictive sufficiency (Shalizi 2019).

\#### 4.2.3 Common information

Two older questions distinguish requirements that appear together in the perfect case. The maximal deterministic common part of $$X_{1},X_{2}$$ is a variable $$K$$ recoverable from either observation, through which every other common function factors. Its entropy is the Gacs–Korner common information. Wyner's common information instead minimizes $$I(X_{1},X_{2};W)$$ over extensions satisfying $$X_{1}\perp X_{2}\mid W$$. Such a $$W$$ need not be separately recoverable from the observations.

If $$W$$ is both separately recoverable and screens off dependence, then

$$
I(X_{1};X_{2})=H(W)+I(X_{1};X_{2}\mid W)=H(W).
$$

Moreover, every common function $$K$$ is determined by $$W$$: the two-witness lemma, with witnesses $$X_{1},X_{2}$$ and common part $$W$$, gives $$H(K\mid W)=0$$. So $$W$$ is the Gacs–Korner common part, and the three quantities coincide: the Gacs–Korner common information, Wyner's common information and $$I(X_{1};X_{2})$$ all equal $$H(W)$$. For two observations, the top latent of a perfect condensation is such a $$W$$.

It is restrictive: for the noisy pair of Section 2.2.1, every common function is constant although $$I(X_{1};X_{2})=1-h_{2}(q)>0$$. Recoverable common information and mutual information differ.

Condensation extends this from two observations to a family of subset-addressed latents. See G'acs & K"orner 1973 and Liu, Xu and Chen's extension of Wyner's common information (Liu et al. 2010).

\#### 4.2.4 Computational mechanics

Computational mechanics groups past histories according to their conditional distributions over futures. Its causal states have predictive optimality, minimality, and uniqueness properties. This is an important precedent for characterizing such a construction through informational requirements.

The present setup starts from a family of jointly distributed questions rather than a distinguished past/future split, and its formulation is static: time and learning are not required. It characterizes families of latents associated with different observable subsets. See Shalizi & Crutchfield 2001.

\#### 4.2.5 Graphical models and the information bottleneck

The Markov condition in condensation is a graphical-model condition. A subset-ordered directed graph places larger addresses above smaller ones. Under the corresponding factorization, the latent joint law is

$$
P(y)=\prod_{A\ne\varnothing}P(y_{A}\mid y_{\supsetneq A}).
$$

A factorization alone does not ensure that observations recover the latents, or that different latent models correspond. Those are additional requirements. Eisenstat discusses this connection explicitly in Definition 5.8 and Example 6.3 of the condensation paper (Eisenstat 2025).

The information bottleneck compresses an input $$X$$ into $$T$$ while retaining information about a specified relevance variable $$V$$. A standard objective is

$$
I(X;T)-\beta I(T;V), \qquad T\perp V\mid X.
$$

Our condensation problem instead involves many addressed latents, LVM, and conditions across observable sets. See Tishby et al. 1999.

\### 4.3 What information theory leaves out

\#### 4.3.1 An encoding and access to its inverse

Let $$X$$ be uniform on $$\{1,\ldots,N\}$$ and let $$Y=\pi(X)$$ for a fixed permutation $$\pi$$. Then

$$
H(X\mid Y)=H(Y\mid X)=0.
$$

This is exact correspondence whether $$\pi$$ is the identity or a large unstructured lookup table. The entropies do not charge for describing the table, learning it, storing it, or using it. For a finite table an inverse exists and is computable; that does not make it available to a particular learner.

For a concrete learning distinction, draw $$\pi$$ uniformly from all permutations and reveal $$m<N$$ distinct input–output pairs. Conditional on those pairs, the image of a previously unseen input is uniform over the $$N-m$$ unused outputs. The best success probability without further information is $$1/(N-m)$$. For every fixed permutation the correspondence entropy is zero, yet a learner with few examples cannot predict an unseen pairing.

Computation is a separate question, even when a transformation has a short known description. Fix a large prime $$p$$ and a generator $$g$$ of the multiplicative group modulo $$p$$, and let $$Y=g^{X} \bmod p$$ for $$X$$ uniform on $$\{1,\ldots,p-1\}$$. Then $$X$$ and $$Y$$ determine one another, and the map has a one-line description that is fast to compute. Inverting it is the discrete-logarithm problem, believed to be hard for suitable $$p$$. Entropy does not see the difference.

\#### 4.3.2 Rare events and average error

Let $$E\sim\operatorname{Bernoulli}(p)$$. Define $$R=0$$ when $$E=0$$ and, when $$E=1$$, let $$R$$ be uniform over $$M$$ other values. Since $$R$$ reveals $$E$$,

$$
H(R)=h_{2}(p)+p\log_{2} M.
$$

For $$p=10^{-6}$$ and $$M=2^{10^6}$$, the rare branch contributes one full bit. An independent sample of size $$m$$ misses that branch with probability $$(1-p)^{m}$$. Large informational contributions can be absent from a small dataset.

Conversely, suppose a variable $$T$$ records $$E$$, and records the value of a fair bit $$D$$, independent of $$E$$, only when $$E=0$$. Then

$$
H(D\mid T)=p.
$$

The average uncertainty is small, but conditional on the rare event $$E=1$$, the bit is entirely unknown. Entropy is an average informational quantity, not a measure of the consequences of errors.

These examples distinguish informational equivalence, statistical access, and performance on important cases. A useful translation needs guarantees about all three.

\### 4.4 The connection to AI safety

1. **Corresponding information.** Under the reconstruction and Markov conditions, the theorem gives correspondence between specified families of latents in two models of the same observables.
2. **Concepts of actual agents.** To apply that result, we need to identify suitable variables in actual agents and establish the relevant conditions, including how their observables relate. The theorem does not show that learning procedures produce such models. That many kinds of agents learn such concepts is a version of the natural abstraction hypothesis (Wentworth 2021).
3. **A usable translation.** Informational correspondence could support identifying which of an AI's latents carries something humans care about. We must still find the correspondence with available data and computation, and connect it to the particular human distinction of interest. This is the ontology-identification problem at the heart of eliciting latent knowledge (Christiano et al. 2021).
4. **Interpretation and specification.** A usable translation could help interpret predictions or express objectives in an AI's world model. This requires preserving relevant distinctions when circumstances or models change.
5. **Safer systems.** Better interpretation and specification could improve oversight and alignment. Sharing concepts does not entail sharing values, reporting faithfully, or following an intended objective.

The first step is the mathematical result of this lesson. The subsequent steps state a research program and the additional work required to connect it to safety.

\### 4.5 Discussion

1. **Comparing with prior work.** Choose a comparison from Section 4.2. State one mathematical similarity and one difference in what is being characterized. If it relates to one of the condensation conditions, say how.
2. **Choosing the questions.** Consider two agents describing the same physical system, one using local measurements and another using a different collection of measurements. What would have to be established before applying a theorem that assumes the same observables? Distinguish changing value labels from changing which distinctions an observable makes. Identify one restriction on observable choice that seems justified for a concrete application.
3. **What would count as a useful translation?** Suppose two latent tuples $$U,V$$ satisfy $$H(U\mid V)=H(V\mid U)=0$$. Specify an additional test that would make this correspondence useful for interpreting a learned model. State what access the test requires: paired samples, interventions, model internals, or a known decoder. Which part of the permutation example would that access resolve?
4. **From correspondence to oversight.** Choose one human distinction that matters for evaluating an AI's behavior. Trace the steps from a correspondence theorem to an oversight procedure that uses that distinction, using the chain in Section 4.4; say where it breaks. Name a failure that could occur despite exact informational correspondence, and state what additional evidence would address it.

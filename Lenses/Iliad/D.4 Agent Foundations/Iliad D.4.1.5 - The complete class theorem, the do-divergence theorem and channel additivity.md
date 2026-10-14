---
id: '36a08a5d-830f-421d-b194-95074be14cd9'
title: "D.4.1.5 The complete class theorem, the do-divergence theorem and channel additivity"
tldr: "Exercises on the complete class theorem (admissible rules are Bayes-optimal), the do-divergence theorem bounding steering by mutual information, and channel additivity."
summary_for_tutor: "End of Section 3 'Exercises' of Iliad worksheet D.4.1 Agent Foundations. Exercise 3.3 (a-c) builds up decision rules, risk vectors, admissibility, Bayes-optimality, Example 3.1 (umbrella) and Theorem 3.2 (Complete Class). Exercise 3.4 proves D_KL(P[X] || P[X | do(A)]) <= MI(A; O). Exercise 3.5 (a-c) shows MI(X;Y) = MI(X1;Y1) + MI(X2;Y2) - MI(Y1;Y2) and that independent inputs are optimal. Hints and collapsed solutions are included. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/agent-foundations/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
::::callout {title="Exercise" tone="amber"}
**Exercise 3.3 (The Complete Class Theorem).** **The setup: decision-making under uncertainty.** Imagine you must choose an action, but you don't know which *environment* you are in. There are finitely many actions $$\mathcal{A}= \{a_{1}, \ldots, a_{k}\}$$ and finitely many possible environments $$\Omega = \{\omega_{1}, \ldots, \omega_{n}\}$$. If you take action $$a$$ and the true environment turns out to be $$\omega$$, you receive a reward $$u(a, \omega) \in \mathbb{R}$$.

:::callout {title="Tip" tone="green"}

**Example 3.1.** You are deciding whether to carry an umbrella ($$a_{1}$$) or not ($$a_{2}$$). The environment is either "rainy" ($$\omega_{1}$$) or "sunny" ($$\omega_{2}$$). The rewards might be:

$$
\begin{array}{c|cc}& \omega_1 \text{ (rain)} & \omega_2 \text{ (sun)} \\ \hline a_1 \text{ (umbrella)} & 8 & 5 \\ a_2 \text{ (no umbrella)} & 2 & 10\end{array}
$$

:::

**Decision rules.** A *decision rule* $$\delta = (\lambda_{1}, \ldots, \lambda_{k})$$ is a (possibly randomized) strategy: you play action $$a_{j}$$ with probability $$\lambda_{j}$$, where $$\lambda_{j} \geq 0$$ and $$\sum_{j=1}^{k} \lambda_{j} = 1$$. A *pure* decision rule puts all its weight on a single action (e.g. "always carry the umbrella"). A *mixed* rule randomizes (e.g. "carry the umbrella with probability $$0.7$$").

The *reward of $$\delta$$ in environment $$\omega$$* is the average reward under the randomization:

$$
u(\delta, \omega) \;:=\; \sum_{j=1}^{k} \lambda_{j}\, u(a_{j}, \omega).
$$

**Risk vectors and the risk set.** To compare decision rules across all environments simultaneously, we package the rewards into a single vector. The *risk vector* of a decision rule $$\delta$$ is

$$
r(\delta) \;=\; \bigl(u(\delta, \omega_{1}),\; \ldots,\; u(\delta, \omega_{n})\bigr) \;\in\; \mathbb{R}^{n}.
$$

Each coordinate records how well $$\delta$$ performs in one environment. In the umbrella example, $$r(a_{1}) = (8, 5)$$ and $$r(a_{2}) = (2, 10)$$.

The *risk set* $$\mathcal{R}$$ is the set of all risk vectors achievable by some decision rule:

$$
\mathcal{R}\;=\; \Bigl\{\sum_{j=1}^{k} \lambda_{j}\, r(a_{j}) \;:\; \lambda_{j} \geq 0,\; \sum_{j=1}^{k} \lambda_{j} = 1\Bigr\}.
$$

Geometrically, $$\mathcal{R}$$ is the *convex hull* of the pure-action risk vectors $$\{r(a_{1}), \ldots, r(a_{k})\}$$: the set of all weighted averages of these points.

**Admissibility (not being dominated).** A decision rule $$\delta$$ is *admissible* if there is no other rule $$\delta'$$ that does at least as well as $$\delta$$ in *every* environment and strictly better in at least one. If such a $$\delta'$$ exists, we say $$\delta'$$ *dominates* $$\delta$$, and any rational agent should prefer $$\delta'$$ — after all, switching from $$\delta$$ to $$\delta'$$ never hurts and sometimes helps, regardless of which environment is the true one.

The *Pareto frontier* $$\mathcal{F}\subseteq \mathcal{R}$$ is the set of risk vectors of all admissible decision rules. A pure action $$a_{j}$$ is *Pareto-optimal* if $$r(a_{j}) \in \mathcal{F}$$.

**Bayesian expected utility.** A different approach to decision-making is to assign a *prior* $$\pi = (\pi_{1}, \ldots, \pi_{n})$$ representing your beliefs about how likely each environment is, where $$\pi_{i} \geq 0$$ and $$\sum_{i} \pi_{i} = 1$$. (For example, $$\pi = (0.3, 0.7)$$ means you believe there is a $$30\%$$ chance of rain.) The *expected utility* of $$\delta$$ under $$\pi$$ is the weighted average reward:

$$
\mathrm{EU}(\delta, \pi) \;:=\; \sum_{i=1}^{n} \pi_{i}\, u(\delta, \omega_{i}) \;=\; \pi \cdot r(\delta).
$$

A decision rule $$\delta$$ is *Bayes-optimal* under $$\pi$$ if it achieves the highest expected utility among all decision rules: $$\mathrm{EU}(\delta, \pi) \geq \mathrm{EU}(\delta', \pi)$$ for all $$\delta'$$.

**The theorem.** These two approaches to rational decision-making — admissibility ("never use a dominated strategy") and Bayesian expected utility maximization ("assign beliefs and maximize average reward") — turn out to characterize exactly the same set of decision rules:

:::callout {title="Theorem" tone="green"}

**Theorem 3.2 (Complete Class).** Every admissible decision rule is Bayes-optimal under some prior $$\pi$$ with $$\pi_{i} > 0$$ for all $$i$$. Conversely, every Bayes-optimal rule under such a prior is admissible.

:::

In other words: the decision rules that survive the "no domination" criterion are precisely those that arise from maximizing expected utility under some set of beliefs that doesn't rule out any environment entirely. This is significant because admissibility is an extremely weak rationality requirement — it says only that you shouldn't use a strategy when a strictly better one is available — yet it already forces expected utility maximization.

**(a)** Show the following two facts:
**(i)** Any admissible decision rule $$\delta = \sum_{j} \lambda_{j}\, a_{j}$$ places zero weight on dominated pure actions: $$\lambda_{j} = 0$$ whenever $$a_{j}$$ is not Pareto-optimal. (In other words, the Pareto frontier $$\mathcal{F}$$ is contained in the convex hull of the Pareto-optimal pure actions alone.)
:::callout {title="Hint" tone="neutral" collapse="closed"}

If $$\delta$$ places positive weight on a dominated pure action $$a_{j}$$, replace $$a_{j}$$ with the action that dominates it. Does the resulting rule dominate $$\delta$$?

:::

**(ii)** Every Bayes-optimal rule under a prior $$\pi$$ with $$\pi_{i} > 0$$ for all $$i$$ is admissible.
:::callout {title="Hint" tone="neutral" collapse="closed"}

If some $$\delta'$$ dominated $$\delta$$, compare their expected utilities. What does $$\pi_{i} > 0$$ ensure?

:::

**(b)** A *face* $$F$$ of the Pareto frontier is a maximal convex subset of $$\mathcal{F}$$ of the form

$$
F \;=\; \Bigl\{\sum_{l=1}^{p} \mu_{l}\, r(a_{i_l}) \;:\; \mu_{l} \geq 0,\; \sum_{l=1}^{p} \mu_{l} = 1\Bigr\}
$$

for some subset of Pareto-optimal pure actions $$\{a_{i_1}, \ldots, a_{i_p}\}$$. Define the *difference vectors* $$v_{l} := r(a_{i_l}) - r(a_{i_1})$$ for $$l = 2, \ldots, p$$, and let $$H = \mathrm{span}\{v_{2}, \ldots, v_{p}\}$$. Show that $$H$$ consists precisely of the directions along which one can move within $$F$$: that is, if $$r(\delta) \in F$$, then $$r(\delta) + h \in F$$ for some $$h$$ only if $$h \in H$$.

**(c)** Let $$\pi$$ be a vector perpendicular to the subspace $$H$$ from Exercise 3.3(b), normalized so that $$\pi_{i} > 0$$ for all $$i$$ and $$\sum_{i} \pi_{i} = 1$$. You may assume that the entire risk set $$\mathcal{R}$$ lies on one side of the hyperplane defined by $$H$$ (i.e. no point in $$\mathcal{R}$$ scores strictly higher under $$\pi$$ than the points on $$F$$). Show that:
**(i)** $$\mathrm{EU}(\delta, \pi)$$ takes the same value for all $$\delta$$ with $$r(\delta) \in F$$.

**(ii)** Every rule on the face $$F$$ is Bayes-optimal under $$\pi$$.

Conclude the Complete Class Theorem: every admissible rule lies on some face of $$\mathcal{F}$$, and the prior $$\pi$$ constructed from that face makes it Bayes-optimal.
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Higher reward is better; $$\delta'$$ *dominates* $$\delta$$ if $$r(\delta')\ge{r(\delta)}$$ coordinatewise with strict inequality in some coordinate. $${r(\delta)}$$ is linear in the mixing weights, $$R=\operatorname{conv}\{r(a_{1}),\dots,r(a_{k})\}$$, and $${\operatorname{EU}}(\delta,\pi)=\pi\cdot{r(\delta)}$$.

**(a)** *(i)* An admissible $$\delta=\sum_{j}\lambda_{j} a_{j}$$ puts $$\lambda_{j}=0$$ on every non-Pareto-optimal (dominated) $$a_{j}$$.

*Solution.*  Suppose $$\lambda_{j}>0$$ for a dominated $$a_{j}$$, and let $$\delta'$$ dominate it: $$r(\delta')\ge r(a_{j})$$ with strict inequality in some coordinate $$i_{0}$$. Replace the weight on $$a_{j}$$ by $$\delta'$$, i.e. play $$\delta'$$ with the probability $$\lambda_{j}$$ formerly on $$a_{j}$$. This is a valid rule $$\hat\delta$$ with

$$
r(\hat\delta)={r(\delta)}+\lambda_{j}\big(r(\delta')-r(a_{j})\big)\ge{r(\delta)},
$$

and strict in coordinate $$i_{0}$$ (since $$\lambda_{j}>0$$). So $$\hat\delta$$ dominates $$\delta$$, contradicting admissibility. Hence $$\lambda_{j}=0$$, i.e. $$F\subseteq\operatorname{conv}\{\text{Pareto-optimal pure actions}\}$$. $$\square$$

*(ii)* Every Bayes-optimal rule under a prior $$\pi$$ with $$\pi_{i}>0$$ for all $$i$$ is admissible.

*Solution.*  If $$\delta'$$ dominated such a $$\delta$$, then with $$r(\delta')_{i_0}>{r(\delta)}_{i_0}$$,

$$
{\operatorname{EU}}(\delta',\pi)-{\operatorname{EU}}(\delta,\pi)=\sum_{i}\pi_{i}\big(r(\delta')_{i}-{r(\delta)}_{i}\big)\ge\pi_{i_0}\big(r(\delta')_{i_0}-{r(\delta)}_{i_0}\big)>0,
$$

since every term is $$\ge0$$ and the $$i_{0}$$ term is $$>0$$. This contradicts Bayes-optimality, so $$\delta$$ is admissible. $$\square$$

**(b)** For a face $$\mathcal{F}=\{\sum_{l=1}^{p}\mu_{l}\,r(a_{i_l}):\mu_{l}\ge0,\ \sum_{l}\mu_{l}=1\}$$ with $$v_{l}:=r(a_{i_l})-r(a_{i_1})$$ and $$H=\operatorname{span}\{v_{2},\dots,v_{p}\}$$: $$H$$ is exactly the set of directions tangent to $$\mathcal{F}$$.

*Solution.*  Any point of $$\mathcal{F}$$ equals $$r(a_{i_1})+\sum_{l\ge2}\mu_{l} v_{l}$$, so $$\mathcal{F}\subseteq r(a_{i_1})+H$$. Take $$x,x+h\in\mathcal{F}$$, say $$x=\sum_{l}\mu_{l} r(a_{i_l})$$ and $$x+h=\sum_{l}\mu_{l}' r(a_{i_l})$$ with $$\sum_{l}\mu_{l}=\sum_{l}\mu_{l}'=1$$. Then

$$
h=\sum_{l}(\mu_{l}'-\mu_{l})\,r(a_{i_l})=\sum_{l\ge2}(\mu_{l}'-\mu_{l})\,v_{l}\in H,
$$

using $$\sum_{l}(\mu_{l}'-\mu_{l})=0$$ to eliminate the $$r(a_{i_1})$$ term. Hence moving within $$\mathcal{F}$$ requires $$h\in H$$. Conversely, from any relative-interior point ($$\mu_{l}>0$$) every $$h\in H$$ is realized: $$x+\varepsilon h\in\mathcal{F}$$ for small $$\varepsilon>0$$. So the tangent directions of $$\mathcal{F}$$ are precisely $$H$$. $$\square$$

**(c)** Let $$\pi\perp H$$ be normalized so $$\pi_{i}>0$$ and $$\sum_{i}\pi_{i}=1$$, and assume no point of $$R$$ scores strictly higher under $$\pi$$ than the points of $$\mathcal{F}$$.

*Solution.*  *(i)* For $$x,x'\in\mathcal{F}$$ we have $$x-x'\in H$$ by Exercise 3.3(b), so $$\pi\cdot(x-x')=0$$. Thus $$\pi\cdot{r(\delta)}$$ equals a common value $$c$$ for all $$\delta$$ with $${r(\delta)}\in\mathcal{F}$$.

*(ii)* Picture $$\pi$$ as the *outward* normal of the supporting hyperplane $$\{x:\pi\cdot x=c\}$$: by assumption the whole risk set lies on the inner side, $$\pi\cdot x\le c$$ for all $$x\in R$$, touching the hyperplane exactly along the face $$\mathcal{F}$$. Fix any $${r(\delta)}\in\mathcal{F}$$ (so $${\operatorname{EU}}(\delta,\pi)=c$$) and any other rule $$\delta'$$. The step from the face point $${r(\delta)}$$ to $$r(\delta')\in R$$ heads back into the risk set, i.e. against the outward normal, so its dot product with $$\pi$$ is non-positive:

$$
\pi\cdot\big(r(\delta')-{r(\delta)}\big)\le 0,\qquad\text{equivalently}\qquad {\operatorname{EU}}(\delta',\pi)\le{\operatorname{EU}}(\delta,\pi).
$$

Since this holds for every $$\delta'$$, each rule with $${r(\delta)}\in\mathcal{F}$$ maximizes expected utility, i.e. is Bayes-optimal under $$\pi$$.

*Conclusion.* If $$\delta$$ is admissible then $${r(\delta)}\in F$$ lies on some face $$\mathcal{F}$$; the prior $$\pi$$ built from $$\mathcal{F}$$ has all $$\pi_{i}>0$$ and, by (ii), makes $$\delta$$ Bayes-optimal. Conversely, by part (ii) of Exercise 3.3(a) every Bayes-optimal rule under a strictly positive prior is admissible. The two classes coincide. $$\square$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 3.4 (The Do-Divergence Theorem).** **Motivation: optimization as steering.** A useful way to think about what it means for an agent to be *optimizing* is that it reliably steers the world into a narrow set of outcomes — outcomes that would be extremely unlikely to arise out of any random process . A thermostat keeps a room at 20 ∘ C despite varying weather; a chess player steers toward checkmate despite the opponent's moves. In each case, the actual outcome is concentrated in a small region of possibility space, whereas without the agent's intervention, outcomes would be spread broadly.

This exercise makes that intuition precise in an information-theoretic setting. We will show that an agent's ability to concentrate outcomes ("steer") is bounded by the amount of information the agent extracts from its observations.

**Background: KL divergence.** Given two probability distributions $$p$$ and $$q$$ over the same set of outcomes, the *Kullback–Leibler (KL) divergence* from $$q$$ to $$p$$ is

$$
D_{\mathrm{KL}}(p \,\|\, q) \;:=\; \sum_{x} p(x) \log \frac{p(x)}{q(x)}.
$$

This quantity is always $$\geq 0$$, and equals $$0$$ only when $$p = q$$. It measures how "different" $$p$$ is from $$q$$, with a particular asymmetry: $$D_{\mathrm{KL}}(p \| q)$$ is large when $$p$$ places significant probability on outcomes where $$q$$ assigns very little. In other words, it is large precisely when $$p$$ concentrates on outcomes that would be *surprising* under $$q$$. This can be seen as a signature of optimization: the agent's policy makes certain outcomes likely that would be very unlikely under a baseline policy.

**Background: mutual information.** The *mutual information* between two random variables $$A$$ and $$O$$ is

$$
\mathrm{MI}(A;\, O) \;:=\; D_{\mathrm{KL}}\bigl(P[A, O] \,\big\|\, P[A]\,P[O]\bigr) \;=\; \sum_{a, o}P[a, o] \log \frac{P[a, o]}{P[a]\,P[o]}.
$$

This measures how much knowing $$O$$ tells you about $$A$$ (and vice versa). It is zero when $$A$$ and $$O$$ are independent, and large when they are tightly coupled.

**Setup.** Consider an agent (the "demon") that observes some information $$O$$ about the world and then takes an action $$A$$ based on what it observed. The action and observation together produce an outcome $$X$$. The joint distribution is

$$
P[X, A, O] \;=\; P[X \mid A, O]\; P[A \mid O]\; P[O].
$$

The factor $$P[A \mid O]$$ encodes the demon's *policy*: how it chooses actions as a function of its observations.

Now consider a *blind baseline*: the demon still acts, but ignores its observations, choosing actions independently of $$O$$. We write the blind baseline distribution as

$$
P[X, A, O \mid do(A)] \;=\; P[X \mid A, O]\; P[A]\; P[O].
$$

The notation $$do(A)$$ means we have "intervened" on the action, replacing the demon's observation-dependent policy $$P[A \mid O]$$ with the marginal $$P[A]$$ (the overall frequency of each action, ignoring which observations prompted them). The mechanism $$P[X \mid A, O]$$ by which actions and observations produce outcomes is unchanged — only the demon's strategy has been lobotomized.

**The theorem.** Prove the Do-Divergence Theorem:

$$
D_{\mathrm{KL}}\bigl(P[X] \,\big\|\, P[X \mid do(A)]\bigr) \;\leq\; \mathrm{MI}(A;\, O).
$$

The left side measures how much the sighted demon's outcome distribution differs from the blind baseline's. In the language of steering: it measures how much the demon has concentrated outcomes into regions that would be unlikely without observation-dependent action. The right side is the mutual information between actions and observations — how much the demon's actions depend on what it sees. The theorem says that **the degree of steering is bounded by the information the demon uses**.

*Useful fact:*

- **Monotonicity of KL divergence.** For any two joint distributions $$p(x,y)$$ and $$q(x,y)$$, marginalizing out $$y$$ can only decrease KL divergence: $$D_{\mathrm{KL}}(p(x) \,\|\, q(x)) \leq D_{\mathrm{KL}}(p(x,y) \,\|\, q(x,y))$$. (Intuitively: forgetting information can only make two distributions look more similar, never less.)

:::callout {title="Hint" tone="neutral" collapse="closed"}

Compute $$D_{\mathrm{KL}}(P[X, A, O] \,\|\, P[X, A, O \mid do(A)])$$ by expanding the log ratio using the factorizations above

:::

:::callout {title="Note" tone="blue"}

**Remark (Maxwell's demon and the thermodynamics of optimization).** Maxwell's demon is a thought experiment in which a tiny intelligent being controls a door between two halves of a box of gas. By observing each molecule's position and selectively opening the door, the demon can sort all molecules to one side, creating a highly ordered (low-entropy) state from an initially disordered one. In our notation: the outcome $$X$$ is the final configuration of molecules, the observations $$O$$ are the demon's measurements of molecular positions, and the actions $$A$$ are its door openings.

Under the blind baseline (opening the door at random), molecules are roughly equally likely to be on either side, so $$P[X \mid do(A)]$$ is spread broadly. If the demon perfectly sorts all $$n$$ molecules to the right, $$P[X]$$ is concentrated on a single configuration, and the KL divergence between these distributions is $$n \log 2$$ (i.e. $$n$$ bits). The theorem therefore says that perfectly sorting $$n$$ molecules requires $$\mathrm{MI}(A; O) \geq n$$ bits: the demon must gather at least $$n$$ bits of information about the molecules to reduce the gas's entropy by $$n$$ bits. This illustrates the idea that any agent that steers a system into a narrow, unlikely region of outcome space (low entropy) must pay for this steering with mutual information.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Write $$\Pr[X,A,O]=\Pr[X\mid A,O]\Pr[A\mid O]\Pr[O]$$ and the blind baseline $$\Pr[X,A,O\mid\mathrm{do}(A)]=\Pr[X\mid A,O]\Pr[A]\Pr[O]$$.

**Claim.** $${D_{\mathrm{KL}}}\!\big(\Pr[X]\,\big\|\,\Pr[X\mid\mathrm{do}(A)]\big)\le{\operatorname{MI}}(A;O)$$.

*Solution.*  Compute the divergence between the full joints. The factors $$\Pr[X\mid A,O]$$ and $$\Pr[O]$$ cancel in the log-ratio:

$$
{D_{\mathrm{KL}}}\!\big(\Pr[X,A,O]\,\big\|\,\Pr[X,A,O\mid\mathrm{do}(A)]\big) =\sum_{x,a,o}\Pr[x,a,o]\log\frac{\Pr[a\mid o]}{\Pr[a]}.
$$

The summand depends only on $$a,o$$; marginalizing $$x$$ and using $$\Pr[a\mid o]/\Pr[a]=\Pr[a,o]/(\Pr[a]\Pr[o])$$,

$$
=\sum_{a,o}\Pr[a,o]\log\frac{\Pr[a,o]}{\Pr[a]\Pr[o]}={\operatorname{MI}}(A;O).
$$

Marginalizing the two joints down to $$X$$ sends them to $$\Pr[X]$$ and $$\Pr[X\mid\mathrm{do}(A)]=\sum_{a,o}\Pr[X\mid a,o]\Pr[a]\Pr[o]$$ respectively, so monotonicity of KL under marginalization gives

$$
\begin{aligned}{D_{\mathrm{KL}}}\!\big(\Pr[X]\,\big\|\,\Pr[X\mid\mathrm{do}(A)]\big)&\le{D_{\mathrm{KL}}}\!\big(\Pr[X,A,O]\,\big\|\,\Pr[X,A,O\mid\mathrm{do}(A)]\big)\\&={\operatorname{MI}}(A;O). \end{aligned}
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 3.5 (Channel Additivity).** Consider two independent channels $$X_{1} \to Y_{1}$$ and $$X_{2} \to Y_{2}$$ with a fixed joint channel

$$
P[Y \mid X] \;=\; P[Y_{1} \mid X_{1}]\, P[Y_{2} \mid X_{2}].
$$

That is, output $$Y_{1}$$ depends only on input $$X_{1}$$, and $$Y_{2}$$ depends only on $$X_{2}$$; the two channels do not interact. We are free to choose the input distribution $$P[X]$$ (which may correlate $$X_{1}$$ and $$X_{2}$$), and the joint distribution over everything is then $$P[Y, X] = P[Y \mid X]\, P[X]$$. The goal is to maximize the mutual information $$\mathrm{MI}(X;\, Y)$$, called the *information throughput* of the channel.

**(a)** Show that for any input distribution $$P[X]$$,

$$
\mathrm{MI}(X;\, Y) \;=\; \mathrm{MI}(X_{1};\, Y_{1}) \;+\; \mathrm{MI}(X_{2};\, Y_{2}) \;-\; \mathrm{MI}(Y_{1};\, Y_{2}).
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Write each mutual information as a KL divergence between the joint and the product of marginals, expand the log ratios using the channel factorization, and collect terms.

:::

**(b)** Given any input distribution $$P[X_{1}, X_{2}]$$, define

$$
Q[X_{1}, X_{2}] \;:=\; P[X_{1}]\, P[X_{2}],
$$

i.e. the product of the marginals. Show that $$\mathrm{MI}_{Q}(X;\, Y) \geq \mathrm{MI}_{P}(X;\, Y)$$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Under $$Q$$, the inputs are independent. What happens to $$\mathrm{MI}(Y_{1};\, Y_{2})$$ when $$X_{1} \perp\!\!\!\perp X_{2}$$, given the channel factorization? Use Exercise 3.5(a).

:::

**(c)** Use Exercise 3.5(b) to conclude that there always exists a throughput-maximizing input distribution under which $$X_{1} \perp\!\!\!\perp X_{2}$$.

:::callout {title="Note" tone="blue"}

**Remark.** This result has a natural interpretation in terms of optimization and agency. Think of $$X$$ as the actions of an agent and $$Y$$ as the outcomes it cares about. The channel $$P[Y \mid X]$$ — how actions influence outcomes — is fixed by the environment and outside the agent's control; the agent only gets to choose its policy $$P[X]$$. The factorization condition on $$P[Y \mid X]$$ says that the environment is *modular*: the two groups of outcomes $$Y_{1}$$ and $$Y_{2}$$ are each influenced only by their respective actions $$X_{1}$$ and $$X_{2}$$. Our theorem says that if the environment is modular in this sense, then the agent can always find an optimal policy that is modular in a corresponding sense — specifically, the two groups of actions need not be coordinated at all and can be chosen independently.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The channel factorizes as $$P[Y\mid X]=P[Y_{1}\mid X_{1}]P[Y_{2}\mid X_{2}]$$, and $$P[Y,X]=P[Y\mid X]P[X]$$.

**(a)** $${\operatorname{MI}}(X;Y)={\operatorname{MI}}(X_{1};Y_{1})+{\operatorname{MI}}(X_{2};Y_{2})-{\operatorname{MI}}(Y_{1};Y_{2})$$.

*Solution.*  Using $$P[x,y]=P[y\mid x]P[x]$$ and the factorization,

$$
{\operatorname{MI}}(X;Y)=\sum_{x,y}P[x,y]\log\frac{P[y\mid x]}{P[y]}=\sum_{x,y}P[x,y]\log\frac{P[y_{1}\mid x_{1}]P[y_{2}\mid x_{2}]}{P[y_{1},y_{2}]}.
$$

The three terms on the right are, respectively,

$$
{\operatorname{MI}}(X_{1};Y_{1})=\sum P[x,y]\log\tfrac{P[y_1\mid x_1]}{P[y_1]},\quad {\operatorname{MI}}(X_{2};Y_{2})=\sum P[x,y]\log\tfrac{P[y_2\mid x_2]}{P[y_2]},
$$

$$
{\operatorname{MI}}(Y_{1};Y_{2})=\sum P[x,y]\log\tfrac{P[y_1,y_2]}{P[y_1]P[y_2]},
$$

each written over the full joint (the first depends only on $$x_{1},y_{1}$$, etc.). Then

$$
\begin{aligned}{\operatorname{MI}}(X_{1};Y_{1})&+{\operatorname{MI}}(X_{2};Y_{2})-{\operatorname{MI}}(Y_{1};Y_{2})\\&=\sum_{x,y}P[x,y]\log\frac{P[y_{1}\mid x_{1}]P[y_{2}\mid x_{2}]}{P[y_{1},y_{2}]}={\operatorname{MI}}(X;Y). {{\square}}\end{aligned}
$$

**(b)** For $$Q[X_{1},X_{2}]:=P[X_{1}]P[X_{2}]$$, $${\operatorname{MI}}_{Q}(X;Y)\ge{\operatorname{MI}}_{P}(X;Y)$$.

*Solution.*  $$Q$$ keeps the marginals $$Q[X_{i}]=P[X_{i}]$$ and the channel, so $${\operatorname{MI}}_{Q}(X_{i};Y_{i})={\operatorname{MI}}_{P}(X_{i};Y_{i})$$ for $$i=1,2$$ ($${\operatorname{MI}}(X_{i};Y_{i})$$ depends only on $$P[X_{i}]$$ and $$P[Y_{i}\mid X_{i}]$$). Under $$Q$$ the inputs are independent, so the outputs are too:

$$
Q[y_{1},y_{2}]=\sum_{x_1,x_2}Q[x_{1}]Q[x_{2}]P[y_{1}\mid x_{1}]P[y_{2}\mid x_{2}]=Q[y_{1}]\,Q[y_{2}],
$$

hence $${\operatorname{MI}}_{Q}(Y_{1};Y_{2})=0$$. Applying Exercise 3.5(a) under each distribution,

$$
\begin{aligned}{\operatorname{MI}}_{Q}(X;Y)&={\operatorname{MI}}_{P}(X_{1};Y_{1})+{\operatorname{MI}}_{P}(X_{2};Y_{2})\\&={\operatorname{MI}}_{P}(X;Y)+{\operatorname{MI}}_{P}(Y_{1};Y_{2})\ge{\operatorname{MI}}_{P}(X;Y),\end{aligned}
$$

the last step using $${\operatorname{MI}}_{P}(Y_{1};Y_{2})\ge0$$. $$\square$$

**(c)** A throughput-maximizing input with $$X_{1}\perp X_{2}$$ always exists.

*Solution.*  The input simplex is compact and $${\operatorname{MI}}(X;Y)$$ continuous, so a maximizer $$P^{*}$$ exists. Let $$Q^{*}:=P^{*}[X_{1}]P^{*}[X_{2}]$$. By Exercise 3.5(b), $${\operatorname{MI}}_{Q^*}(X;Y)\ge{\operatorname{MI}}_{P^*}(X;Y)=\max$$, so $$Q^{*}$$ is also a maximizer, and under $$Q^{*}$$ the inputs are independent. $$\square$$

:::

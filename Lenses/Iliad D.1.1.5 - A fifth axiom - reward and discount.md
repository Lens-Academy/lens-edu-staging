---
id: '02807df7-8033-4b5a-9259-6402140fb56c'
title: "D.1.1.5 A fifth axiom: reward and discount"
tldr: "Adds a fifth axiom, temporal gamma-indifference, and shows that it is exactly what gives a reward and discount representation of utility; also separates preference, utility and reward."
summary_for_tutor: "This is Section 6 of Iliad worksheet D.1.1 Preferences to Rewards. It defines Axiom 5 (temporal gamma-indifference), Theorem 6.1 (Markov reward representation after Bowling et al.: u(t.h) = r(t) + gamma(t) u(h)), the unrolled utility of a trajectory, the constant-gamma and gamma=1 special cases, a remark on MDPs versus POMDPs, and a note that utility is not reward. It contains Exercise 6.1 (guided proof, parts a-h, including the reward transformation r' = b r + (1 - gamma) a) with collapsed solutions. Keep the notation T, t.h, r(t), gamma(t). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Fernando E. Rosas
source_url: https://iliad-intensive.org/agency/preferences-to-rewards/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 6. A fifth axiom: reward and discount

The vNM theorem gives an expected-utility representation over lotteries of whole trajectories, but it does not yet tell us that utility can be generated *locally* from stepwise rewards.

To investigate the possibility of localizing utility over time, let us denote by $T \coloneqq {\mathcal{O}}\times {\mathcal{A}}$ the set of one-step transitions. For $t\in T$ and $h\in {\mathcal{H}}^{*}$, write $t\cdot h$ for the trajectory obtained by prepending $t$ to $h$, and extend this operation to lotteries by

$$
t\cdot \mu \coloneqq \sum_{i} p_{i} \delta_{t\cdot h_i}\qquad \text{when }\mu=\sum_{i} p_{i} \delta_{h_i}.
$$

Now, using a vNM utility $u(h)$ one can always define a continuation-dependent increment as

$$
r(t;h) \coloneqq u(t\cdot h)-u(h).
$$

However, this increment may depend on the whole continuation $h$. What is missing is a temporal condition ensuring that the effect of prepending a transition depends only on that transition itself. Following (Bowling et al. 2023), this can be explored with the following additional axiom.

:::callout {title="Note" tone="blue"}

**Axiom 5 (Temporal $\gamma$-indifference).** There exists a function $\gamma\colon T\to[0,1]$ such that for all $\mu,\nu\in\Delta({\mathcal{H}}^{*})$ and all $t\in T$,

$$
\frac{1}{1+\gamma(t)}(t\cdot \mu)+\frac{\gamma(t)}{1+\gamma(t)}\nu \sim \frac{1}{1+\gamma(t)}(t\cdot \nu)+\frac{\gamma(t)}{1+\gamma(t)}\mu.
$$

:::

Under expected utility, the indifference above is equivalent to

$$
u(t\cdot \mu)+\gamma(t)u(\nu)=u(t\cdot \nu)+\gamma(t)u(\mu),
$$

which can be rearranged as

$$
u(t\cdot \mu)-u(t\cdot \nu)=\gamma(t)\bigl(u(\mu)-u(\nu)\bigr).
$$

So the effect of prepending the same transition $t$ is to rescale the utility difference between two continuations by a factor $\gamma(t)$. In that sense, $\gamma(t)$ measures how much the future still matters after the step $t$ has occurred. When $\gamma(t)=1$, future differences are preserved without discount at that step. When $0<\gamma(t)<1$, the future still matters but is damped. When $\gamma(t)=0$, once $t$ has occurred the continuation no longer affects the comparison. Bowling's axiom is closely related to the transition-dependent discounting discussed by White 2017 and Pitis 2019.

Bowling et al. show that adding this axiom to the four vNM axioms is necessary and sufficient for a discounted-reward representation of preferences.

:::callout {title="Theorem" tone="green"}

**Theorem 6.1 (Markov reward representation, after Bowling et al.).** A weak preference relation $\succcurlyeq$ on $\Delta({\mathcal{H}}^{*})$ satisfies completeness, transitivity, continuity, independence, and temporal $\gamma$-indifference if and only if there exist functions $u\colon {\mathcal{H}}^{*}\to{\mathbb{R}}$, $r\colon T\to{\mathbb{R}}$, and $\gamma\colon T\to[0,1]$ such that $u(\varepsilon)=0$,

$$
u(t\cdot h)=r(t)+\gamma(t)u(h),
$$

and, for all lotteries $\mu,\nu\in\Delta({\mathcal{H}}^{*})$,

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad \sum_{h\in{\mathcal{H}}^*}\mu(h)u(h)\geq \sum_{h\in{\mathcal{H}}^*}\nu(h)u(h).
$$

Moreover, $r$ is unique up to positive scale, and $\gamma$ is the same function appearing in the fifth axiom (Bowling et al. 2023).

:::

This theorem sharpens the vNM result in exactly the way reinforcement learning needs. Utility is no longer an arbitrary scalar attached to a complete trajectory; it is generated recursively from a local reward and a local weight on the future. Unrolling the recursion for a trajectory $h=(t_{1},t_{2},\dots,t_{n})$ gives

$$
u(h)=r(t_{1})+\gamma(t_{1})r(t_{2})+\gamma(t_{1})\gamma(t_{2})r(t_{3})+\cdots+ \Bigg(\prod_{i=1}^{n-1}\gamma(t_{i})\Bigg)r(t_{n}).
$$

Thus the fifth axiom is what allows utility over whole trajectories to be decomposed into local reward and discounting. Two familiar special cases are worth highlighting.

- If $\gamma(t)\equiv \gamma$ is constant, then

$$
u(h)=\sum_{k=1}^{n} \gamma^{k-1}r(t_{k}),
$$

which is the standard discounted-return objective.
- If $\gamma(t)\equiv 1$, then

$$
u(h)=\sum_{k=1}^{n} r(t_{k}),
$$

so utility is simply the additive cumulative reward.

In summary, the step from vNM utility over whole trajectories to RL-style reward requires one more axiom. That axiom simultaneously identifies both the local reward signal and the form of discounting.

:::callout {title="Note" tone="blue"}

**Remark (MDPs, POMDPs, and locality).** The locality result of this section is especially natural in fully observed MDPs, where one often expects reward to depend only on the current state transition. In the present note, however, the primitive histories are sequences of observations and actions, and the corresponding local reward has the form $r\colon {\mathcal{O}}\times {\mathcal{A}}\to{\mathbb{R}}$. In partially observed settings this can be restrictive: a goal may be Markov in the hidden state, in the agent's belief state, or in some augmented memory state, without being reducible to a function of the current observation-action pair alone. In that sense, the fifth axiom should be read as characterizing when preferences admit a reward that is local in the chosen representation of experience. If the raw observation stream is too coarse, one may need to enrich the state description before a Markov reward representation becomes available (Bowling et al. 2023).

:::

:::callout {title="Note" tone="blue"}

**Utility is not reward.**

It is helpful to keep the following four different objects apart.

- *Preference* is the primitive relation $\succcurlyeq$. It says only which trajectories or lotteries are weakly preferred to which others.
- *Preference utility* (`F1') is an ordinal representation of preferences over deterministic trajectories. Under completeness and transitivity, it is any function $u_{\mathrm{ord}}$ such that

$$
h\succcurlyeq h' \quad\Longleftrightarrow\quad u_{\mathrm{ord}}(h)\geq u_{\mathrm{ord}}(h').
$$

It is unique only up to strictly increasing transformations (Fishburn 1970).
- *vNM utility* (`F2') is the stronger, cardinal utility that appears when preferences over lotteries satisfy the vNM axioms. It is the function $u_{\mathrm{vNM}}$ for which

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad \sum_{h} \mu(h)u_{\mathrm{vNM}}(h)\geq \sum_{h} \nu(h)u_{\mathrm{vNM}}(h).
$$

It is unique only up to positive affine transformations (von Neumann & Morgenstern 1944). Thus `F2' refines `F1': it agrees with it on the ranking of certain trajectories, but adds the extra structure needed to compare lotteries.
- *Reward* is not either of these utilities. A reward function $r(t)$ is a *local* representation introduced only after adding temporal structure. In the present framework, reward appears when the fifth axiom allows utility to be written recursively as

$$
u(t\cdot h)=r(t)+\gamma(t)u(h).
$$

So reward is a way of *decomposing* utility over complete trajectories into stepwise contributions. It is therefore downstream of preference, and even downstream of vNM utility. This is why different reward functions can encode the same utility or the same preference ordering, a point we return to in the next section (Bowling et al. 2023).

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 6.1 (Guided proof of the Markov reward representation theorem).** Assume the hypotheses of Exercise 5.1 together with temporal $\gamma$-indifference, and let $u$ be a vNM utility representation over trajectories.

**(a)** Apply expected utility to temporal $\gamma$-indifference and show that for all lotteries $\mu,\nu\in\Delta({\mathcal{H}}^{*})$ and all transitions $t\in T$,

$$
u(t\cdot \mu)+\gamma(t)u(\nu)=u(t\cdot \nu)+\gamma(t)u(\mu).
$$

**(b)** Rearrange part (a) to prove that

$$
u(t\cdot \mu)-\gamma(t)u(\mu)
$$

is independent of the choice of $\mu$.

**(c)** Define

$$
r(t)\coloneqq u(t\cdot \mu)-\gamma(t)u(\mu)
$$

for any $\mu$. Deduce that for every deterministic trajectory $h$,

$$
u(t\cdot h)=r(t)+\gamma(t)u(h).
$$

**(d)** Show that this recursion extends to lotteries by linearity:

$$
u(t\cdot \mu)=r(t)+\gamma(t)u(\mu).
$$

**(e)** Prove the converse direction: if $u$, $r$, and $\gamma$ satisfy

$$
u(t\cdot h)=r(t)+\gamma(t)u(h)
$$

for all $t$ and $h$, and if $u$ extends linearly to lotteries, then temporal $\gamma$-indifference holds.

**(f)** Unroll the recursion along a finite trajectory $h=(t_{1},\dots,t_{n})$ and derive

$$
u(h)=r(t_{1})+\gamma(t_{1})r(t_{2})+\gamma(t_{1})\gamma(t_{2})r(t_{3})+\cdots+ \Bigg(\prod_{i=1}^{n-1}\gamma(t_{i})\Bigg)r(t_{n}).
$$

**(g)** Show that when $\gamma(t)\equiv \gamma$ is constant, the previous formula reduces to standard discounted return, and when $\gamma(t)\equiv 1$ it reduces to additive cumulative reward.

**(h)** Show that if $u' = a+bu$, then the corresponding reward must be

$$
r'(t)=br(t)+(1-\gamma(t))a.
$$

Interpret this as a source of reward non-uniqueness.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Apply $u$ (in expected-utility form) to both sides of the axiom's indifference and multiply by $1+\gamma(t)$:

$$
u(t\cdot\mu)+\gamma(t)u(\nu)=u(t\cdot\nu)+\gamma(t)u(\mu).
$$

**(b)** Rearranging, $u(t\cdot\mu)-\gamma(t)u(\mu)=u(t\cdot\nu)-\gamma(t)u(\nu)$ for *all* $\mu,\nu$: the quantity does not depend on which lottery is used to compute it.

**(c)** By (b) the definition of $r(t)$ is unambiguous. Taking $\mu$ to be the point mass on a deterministic continuation $h$ gives $u(t\cdot h)=r(t)+\gamma(t)u(h)$.

**(d)** $t\cdot\mu$ is the pushforward of $\mu$ under prepending $t$, and $u$ is linear on lotteries, so $u(t\cdot\mu)=\mathbb{E}_{h\sim\mu}\bigl[u(t\cdot h)\bigr] =\mathbb{E}_{h\sim\mu}\bigl[r(t)+\gamma(t)u(h)\bigr]=r(t)+\gamma(t)u(\mu)$.

**(e)** With the recursion and linearity, $u(t\cdot\mu)+\gamma(t)u(\nu)=r(t)+\gamma(t)\bigl(u(\mu)+u(\nu)\bigr)$, which is symmetric under $\mu\leftrightarrow\nu$; hence $u(t\cdot\mu)+\gamma(t)u(\nu)=u(t\cdot\nu)+\gamma(t)u(\mu)$. Dividing by $1+\gamma(t)$ shows both mixtures in the axiom have equal expected utility, and since $u$ represents $\succcurlyeq$, they are indifferent.

**(f)** Normalise $u(\varepsilon)=0$ (allowed by affine freedom). Induction on $n$: $u(h)=r(t_{1})+\gamma(t_{1})\,u\bigl((t_{2},\dots,t_{n})\bigr)$, and expanding the inner term yields

$$
u(h)=r(t_{1})+\gamma(t_{1})r(t_{2})+\gamma(t_{1})\gamma(t_{2})r(t_{3})+\cdots+ \Bigl(\prod_{i=1}^{n-1}\gamma(t_{i})\Bigr)r(t_{n}).
$$

**(g)** If $\gamma(t)\equiv\gamma$, the product $\prod_{i<k}\gamma(t_{i})$ is $\gamma^{k-1}$ and $u(h)=\sum_{k} \gamma^{k-1}r(t_{k})$: discounted return. If $\gamma\equiv 1$ every product is $1$ and $u(h)=\sum_{k} r(t_{k})$: additive cumulative reward.

**(h)** $r'(t)=u'(t\cdot\mu)-\gamma(t)u'(\mu) =\bigl(a+b\,u(t\cdot\mu)\bigr)-\gamma(t)\bigl(a+b\,u(\mu)\bigr) =b\,r(t)+(1-\gamma(t))a$. The same preferences thus admit a family of reward functions: even with $\gamma$ fixed, $r$ is only determined up to a positive scaling and an additive shift modulated by $1-\gamma(t)$.

:::

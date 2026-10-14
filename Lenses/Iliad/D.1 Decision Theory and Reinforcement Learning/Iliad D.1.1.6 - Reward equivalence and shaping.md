---
id: 'dcf20af3-e369-481d-81c0-66f9d31a1615'
title: "D.1.1.6 Reward equivalence and shaping"
tldr: "Shows that many reward functions encode the same preferences, through affine changes of utility and potential-based reward shaping, with an exercise on the boundary term."
summary_for_tutor: "This is Section 7 of worksheet D.1.1 (preferences to rewards). It covers uniqueness of reward once u and gamma are fixed, Proposition 7.1 (affine transformations of utility and the induced reward), Proposition 7.2 (potential-based shaping changes utility only by a boundary term, for gamma=1 and constant gamma) and reward design as underdetermined. It contains Exercise 7.1 (a-c) with collapsed solutions. Keep the notation Phi, r_Phi, u'. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Fernando E. Rosas
source_url: https://iliad-intensive.org/agency/preferences-to-rewards/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 7. Reward equivalence and shaping

The preceding theorem shows how to pass from utility over lotteries of trajectories to a local reward representation. But it also raises an important question: how unique is that reward? The answer has two parts. If one fixes a particular utility function $$u$$ and a particular discount function $$\gamma$$, then the reward is determined. But if one changes the numerical representative of the same preference relation, or allows shaping transformations, then many different rewards can encode the same underlying ordering.

First observe that once $$u$$ and $$\gamma$$ are fixed, the reward is fixed as well. Indeed, if

$$
u(t\cdot h)=r(t)+\gamma(t)u(h)
$$

for all $$t\in T$$ and $$h\in{\mathcal{H}}^{*}$$, then necessarily

$$
r(t)=u(t\cdot h)-\gamma(t)u(h),
$$

and the right-hand side must be independent of the continuation $$h$$. So the non-uniqueness of reward does not come from ambiguity inside a fixed recursive representation. It comes from the fact that utility itself is not unique as a numerical object.

:::callout {title="Theorem" tone="green"}

**Proposition 7.1 (Multiple rewards can encode the same preference relation).** Suppose $$u\colon {\mathcal{H}}^{*}\to{\mathbb{R}}$$, $$r\colon T\to{\mathbb{R}}$$, and $$\gamma\colon T\to[0,1]$$ satisfy

$$
u(t\cdot h)=r(t)+\gamma(t)u(h)
$$

for all $$t\in T$$ and $$h\in{\mathcal{H}}^{*}$$, and that preferences over lotteries are represented by the expected value of $$u$$. For any $$a\in{\mathbb{R}}$$ and $$b>0$$, define

$$
u'(h)=a+bu(h) \qquad\text{and}\qquad r'(t)=br(t)+(1-\gamma(t))a.
$$

Then $$u'(t\cdot h)=r'(t)+\gamma(t)u'(h)$$ for all $$t\in T$$ and $$h\in{\mathcal{H}}^{*}$$, and the expected value of $$u'$$ represents the same preference relation as the expected value of $$u$$.

:::

The proposition shows that reward non-uniqueness already appears at the level of affine reparameterizations of utility: changing the numerical representative of the same vNM preference relation generally changes the associated reward function as well. This point is especially simple under the normalization $$u(\varepsilon)=0$$ used in the previous section. Then the additive degree of freedom disappears, and one is left only with positive rescalings:

$$
u'(h)=bu(h), \qquad r'(t)=br(t).
$$

So in the normalized setting reward is unique only up to choice of units.

There is also a second, less trivial kind of non-uniqueness, in which one changes rewards while leaving the induced trajectory ordering unchanged, first studied by Ng et al. 1999.

:::callout {title="Theorem" tone="green"}

**Proposition 7.2 (Potential-based shaping changes utility only by a boundary term).** Consider a state-based setting with transitions $$t=(s,a,s')$$ and a potential function $$\Phi$$ on states.

1. If $$\gamma\equiv 1$$ and $$r_{\Phi}(s,a,s') \coloneqq r(s,a,s')+\Phi(s')-\Phi(s)$$, then

$$
\sum_{k=1}^{n} r_{\Phi}(t_{k}) = \sum_{k=1}^{n} r(t_{k})+\Phi(s_{n})-\Phi(s_{0})
$$

for any trajectory $$\tau=(t_{1},\dots,t_{n})$$ from $$s_{0}$$ to $$s_{n}$$.
2. If $$\gamma\in(0,1)$$ is constant and $$r_{\Phi}(s,a,s') \coloneqq r(s,a,s')+\gamma \Phi(s')-\Phi(s)$$, then

$$
\sum_{k=1}^{n} \gamma^{k-1}r_{\Phi}(t_{k}) = \sum_{k=1}^{n} \gamma^{k-1}r(t_{k})-\Phi(s_{0})+\gamma^{n}\Phi(s_{n}).
$$

:::

The previous result shows that shaping $$r$$ into $$r_{\Phi}$$ changes utility only by a boundary term. In particular, if all compared trajectories share the same start state and terminal potential, then the induced preference ordering is unchanged; if the boundary term vanishes on all admissible trajectories, then even the numerical utility is unchanged.

The general lesson is that the same preferences admit many different reward functions, so no single one of them is canonical. Some transformations, such as positive scaling, merely change the numerical units. Others, such as potential-based shaping, redistribute value along the trajectory while leaving the overall preference over complete trajectories unchanged. This is why reward design is often underdetermined: what matters behaviorally is not a raw reward function in isolation, but the utility and preference structure it induces.

:::callout {title="Exercise" tone="amber"}
**Exercise 7.1 (Reward shaping).** Assume additive reward with $$\gamma\equiv 1$$ and define

$$
r_{\Phi}(s,a,s')=r(s,a,s')+\Phi(s')-\Phi(s).
$$

**(a)** Show that along any finite trajectory $$(t_{1},\dots,t_{n})$$ the total shaped reward differs from the original total reward by the boundary term $$\Phi(s_{n})-\Phi(s_{0})$$.

**(b)** Under what condition on the admissible trajectories does this shaping leave utility exactly unchanged?

**(c)** Under what weaker condition does it leave only the induced preference ordering unchanged?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Writing $$t_{i}=(s_{i-1},a_{i},s_{i})$$, the shaped total is

$$
\sum_{i=1}^{n}r_{\Phi}(t_{i}) =\sum_{i=1}^{n}r(t_{i})+\sum_{i=1}^{n}\bigl(\Phi(s_{i})-\Phi(s_{i-1})\bigr) =\sum_{i=1}^{n}r(t_{i})+\Phi(s_{n})-\Phi(s_{0}),
$$

since the middle sum telescopes.

**(b)** Utility is exactly unchanged iff the boundary term vanishes on every admissible trajectory, i.e. $$\Phi(s_{n})=\Phi(s_{0})$$ throughout — for example when all trajectories start in a fixed $$s_{0}$$ and $$\Phi$$ takes the value $$\Phi(s_{0})$$ on every reachable terminal state.

**(c)** Only the ordering is at stake if the boundary term is the *same constant* $$c$$ for all compared trajectories: then every utility shifts by $$c$$ and the induced ranking is untouched. A fixed start state together with $$\Phi$$ constant on the reachable terminal states suffices, whatever that constant is.

:::

\## 8. Conclusion

The main lesson of this note is that, in sequential settings, the primitive object is not a one-step reward but a preference over complete trajectories. From that starting point one can distinguish several layers of structure. Completeness and transitivity yield an ordinal utility over deterministic trajectories. Once lotteries are introduced, continuity and independence refine that ordinal picture into a von Neumann–Morgenstern utility, which agrees with the ranking of certain trajectories but carries strictly more information because it calibrates trade-offs between risky prospects.

This separation of layers clarifies both what expected utility achieves and what it leaves out. It explains why "utility" in economics can refer either to an ordinal representation of certain preferences or to a cardinal object suitable for evaluating lotteries. It also shows what fails when particular axioms are dropped: without completeness or transitivity, scalar representation itself can fail; without continuity or independence, one may still have meaningful preferences, but no longer the linear expectation form of vNM. In that sense, expected utility is not the whole of rationality, but a particular and mathematically powerful strengthening of it.

The final step is to see that even vNM utility is not yet reward. To obtain a local reward-and-discount representation one needs additional temporal structure, captured here by Bowling et al.'s fifth axiom. Under that axiom, utility over whole trajectories admits a recursive decomposition into local reward and discounting. But even then reward is not unique: affine changes of utility induce corresponding changes of reward, and potential-based shaping can redistribute value along a trajectory while preserving the underlying ordering. Moreover, the locality of reward depends on the chosen representation of experience, which is natural in fully observed MDPs but can be restrictive in partially observed settings unless the state is suitably enriched. The reward hypothesis, understood in this way, is therefore best read not as the claim that goals are primitively rewards, but as the claim that sufficiently structured preferences over trajectories can be represented by rewards.

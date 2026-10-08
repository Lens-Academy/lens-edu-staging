---
id: 'a6af2403-1a67-4cef-ba4c-711a4395009c'
title: "D.3.2.11 Proving the self-optimizing property"
tldr: "Completes the proof of the self-optimizing property for finite model classes by combining the posterior, likelihood ratio and change-of-measure results."
summary_for_tutor: "Section 11 of worksheet D.3.2: Proving the self-optimizing property (Theorem 9.2). Defines the suboptimality gap delta_{nu,t} and has Exercises 11.1 (chain of inequalities with pi_xi^* and the self-optimizing policy), 11.2 (vanishing posterior when X_{nu,infinity} = 0), 11.3 (transferring convergence via Exercise 10.3), 11.4 (single-term convergence) and 11.5 (combine to prove Theorem 9.2), with a remark on countable M. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 11. Proving the Self-Optimizing Property

Fix a policy $$\tilde\pi$$ that is self-optimizing for $${\mathcal{M}}$$ with respect to $$\pi$$ (Definition 9.1): its existence is the hypothesis of Theorem 9.2. For each $$\nu \in {\mathcal{M}}$$, define the **suboptimality gap**

$$
\delta_{\nu,t}: {\mathcal{H}}^{t-1}\to [0,1], \qquad \delta_{\nu,t}({\text{\ae}}_{<t}) ~:=~ V_{\nu}^{*}({\text{\ae}}_{<t}) - V_{\nu}^{\tilde\pi}({\text{\ae}}_{<t}).
$$

As with $$X_{\nu,t}$$, we write $$\delta_{\nu,t}$$ without its argument when convenient: "$$\delta_{\nu,t}\to 0$$ $$\mu^{\pi}$$-a.s." means $$\delta_{\nu,t}({\text{\ae}}_{<t}) \to 0$$ on every infinite history outside a $$\mu^{\pi}$$-null set, and similarly for "$$\delta_{\nu,t}\leq 1$$" etc.

::::callout {title="Exercise" tone="amber"}
**Exercise 11.1 (Chain of inequalities) [20].** Show:

$$
0 ~\leq~ w(\mu \mid {\text{\ae}}_{<t}) \big[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\big] ~\leq~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \delta_{\nu,t}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use $$V_{\xi}^{\pi_\xi^*}\geq V_{\xi}^{\tilde\pi}$$ and Exercise 4.2.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We establish two inequalities and chain them.

*First inequality: isolate the $$\mu$$-term.* For each $$\nu \in {\mathcal{M}}$$, the optimal value is at least the value of any policy: $$V_{\nu}^{*}({\text{\ae}}_{<t}) \geq V_{\nu}^{\pi_\xi^*}({\text{\ae}}_{<t})$$, so $$V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}\geq 0$$. Since the posterior weights $$w(\nu \mid {\text{\ae}}_{<t}) \geq 0$$, every term in $$\sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})[V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}]$$ is non-negative. The $$\mu$$-term is one such term:

$$
w(\mu \mid {\text{\ae}}_{<t})\big[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\big] ~\leq~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\big[V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}\big].
$$

*Second inequality: replace $$\pi_{\xi}^{*}$$ with $$\tilde\pi$$.* By definition of the optimal value, $$V_{\xi}^{*}({\text{\ae}}_{<t}) \geq V_{\xi}^{\tilde\pi}({\text{\ae}}_{<t})$$. Expanding both sides using infinite-horizon linearity (Exercise 4.2, applied to the fixed policies $$\pi_{\xi}^{*}$$ and $$\tilde\pi$$):

$$
\begin{aligned}\sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\pi_\xi^*}({\text{\ae}}_{<t}) ~&=~ V_{\xi}^{*}({\text{\ae}}_{<t}) ~\geq~ V_{\xi}^{\tilde\pi}({\text{\ae}}_{<t}) \\ ~&=~ \sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})\, V_{\nu}^{\tilde\pi}({\text{\ae}}_{<t}).\end{aligned}
$$

Rearranging: $$\sum_{\nu} w(\nu)[V_{\nu}^{*} - V_{\nu}^{\pi_\xi^*}] \leq \sum_{\nu} w(\nu)[V_{\nu}^{*} - V_{\nu}^{\tilde\pi}] = \sum_{\nu} w(\nu)\, \delta_{\nu,t}$$.

*Chaining:*

$$
0 ~\leq~ w(\mu \mid {\text{\ae}}_{<t})\big[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\big] ~\leq~ \sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \delta_{\nu,t}.
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 11.2 (Vanishing posterior) [10].** Show: if $$X_{\nu,\infty}= 0$$ then $$w(\nu \mid {\text{\ae}}_{<t}) \to 0$$ $$\mu^{\pi}$$-a.s.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Show $$w(\nu \mid {\text{\ae}}_{<t}) = w_{\nu} X_{\nu,t-1}/X_{\xi,t-1}$$ and use Exercise 9.3.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

From the posterior weight formula, dividing numerator and denominator by $$\mu({\text{\ae}}_{<t})$$:

$$
w(\nu \mid {\text{\ae}}_{<t}) ~=~ w_{\nu} \cdot \frac{\nu({\text{\ae}}_{<t})}{\xi({\text{\ae}}_{<t})}~=~ w_{\nu} \cdot \frac{\nu({\text{\ae}}_{<t})/\mu({\text{\ae}}_{<t})}{\xi({\text{\ae}}_{<t})/\mu({\text{\ae}}_{<t})}~=~ \frac{w_{\nu} \cdot X_{\nu,t-1}}{X_{\xi,t-1}},
$$

where $$X_{\nu,t-1}$$ and $$X_{\xi,t-1}$$ are evaluated at the length-$$(t{-}1)$$ history $${\text{\ae}}_{<t}$$.

If $$X_{\nu,\infty}= 0$$, then $$X_{\nu,t-1}\to 0$$ $$\mu^{\pi}$$-a.s. (Exercise 9.2). Since $$X_{\xi,t-1}\geq w_{\mu} > 0$$ always (Exercise 9.3), the ratio $$w(\nu \mid {\text{\ae}}_{<t}) = w_{\nu} X_{\nu,t-1}/X_{\xi,t-1}\to 0$$ $$\mu^{\pi}$$-a.s.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 11.3 (Transferring convergence) [20].** Let $$F := \{{\text{\ae}}_{1:\infty}: \delta_{\nu,t}({\text{\ae}}_{<t}) \not\to 0\}$$, the set of infinite histories on which the suboptimality gap fails to vanish. Show that $$\mu^{\pi}\big[F \cap \{X_{\nu,\infty}> 0\}\big] = 0$$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Self-optimizing (Definition 9.1) gives $$\nu^{\pi}[F] = 0$$. Apply Exercise 10.3 with $$E = F$$ and $$\varepsilon = 1/n$$ to conclude $$\mu^{\pi}[F \cap \{X_{\nu,\infty}\geq 1/n\}] = 0$$ for each $$n \geq 1$$. Then note $$\{X_{\nu,\infty}> 0\} = \bigcup_{n \geq 1}\{X_{\nu,\infty}\geq 1/n\}$$ and take the countable union (Definition 7.1).

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*Step 1: $$F$$ is $$\nu^{\pi}$$-null.* By the self-optimizing assumption (Definition 9.1), under $$\nu^{\pi}$$ the suboptimality gap $$\delta_{\nu,t}$$ vanishes, so $$\nu^{\pi}[F] = 0$$.

*Step 2: Apply Exercise 10.3.* For each $$n \geq 1$$, take $$E = F$$ and $$\varepsilon = 1/n$$:

$$
\mu^{\pi}\!\big[F \cap \{X_{\nu,\infty}\geq 1/n\}\big] ~\leq~ \frac{\nu^{\pi}[F]}{1/n}~=~ 0.
$$

*Step 3: Countable union.* The level sets of $$X_{\nu,\infty}$$ form a nested increasing family: $$\{X_{\nu,\infty}> 0\} = \bigcup_{n \geq 1}\{X_{\nu,\infty}\geq 1/n\}$$. Intersecting with $$F$$ gives $$F \cap \{X_{\nu,\infty}> 0\} = \bigcup_{n \geq 1}\big(F \cap \{X_{\nu,\infty}\geq 1/n\}\big)$$, a countable union. By countable subadditivity (Definition 7.1):

$$
\begin{aligned}\mu^{\pi}\!\big[F \cap \{X_{\nu,\infty}> 0\}\big] ~=~&\mu^{\pi}\!\Big[\textstyle\bigcup_{n}F \cap \{X_{\nu,\infty}\geq 1/n\}\Big] \\ ~\leq~ \sum_{n \geq 1}\,&\mu^{\pi}\!\big[F \cap \{X_{\nu,\infty}\geq 1/n\}\big] ~=~ 0.\end{aligned}
$$

*What this says.* "$$\delta_{\nu,t}\to 0$$ $$\mu^{\pi}$$-a.s. on $$\{X_{\nu,\infty}> 0\}$$" is shorthand for exactly this event statement: among infinite histories on which the likelihood ratio stays bounded away from zero, all but a $$\mu^{\pi}$$-null subset are ones where $$\delta_{\nu,t}({\text{\ae}}_{<t}) \to 0$$. We do *not* claim convergence on histories where $$X_{\nu,\infty}= 0$$: that case is handled separately in Exercise 11.2 via the posterior weight.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 11.4 (Single-term convergence) [10].** Combine Exercise 11.2 and Exercise 11.3 to show $$w(\nu \mid {\text{\ae}}_{<t}) \delta_{\nu,t}\to 0$$ $$\mu^{\pi}$$-a.s.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Fix $$\nu \in {\mathcal{M}}$$. We show $$w(\nu \mid {\text{\ae}}_{<t})\, \delta_{\nu,t}\to 0$$ $$\mu^{\pi}$$-a.s. by considering two exhaustive cases:

*Case 1: $$X_{\nu,\infty}= 0$$.* By Exercise 11.2, $$w(\nu \mid {\text{\ae}}_{<t}) \to 0$$. Since $$\delta_{\nu,t}\in [0,1]$$ (Exercise 1.3), the product $$w(\nu \mid {\text{\ae}}_{<t}) \cdot \delta_{\nu,t}\leq 1 \cdot w(\nu \mid {\text{\ae}}_{<t}) \to 0$$.

*Case 2: $$X_{\nu,\infty}> 0$$.* By Exercise 11.3, $$\delta_{\nu,t}\to 0$$. Since $$w(\nu \mid {\text{\ae}}_{<t}) \leq 1$$ (posterior weights are at most 1), the product $$w(\nu \mid {\text{\ae}}_{<t}) \cdot \delta_{\nu,t}\leq 1 \cdot \delta_{\nu,t}\to 0$$.

These two cases cover all infinite histories ($$\mu^{\pi}$$-a.s.), so $$w(\nu \mid {\text{\ae}}_{<t})\, \delta_{\nu,t}\to 0$$ $$\mu^{\pi}$$-a.s.

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 11.5 (Self-Optimizing Theorem) [15].** Combine Exercise 11.4, Exercise 11.1, Exercise 9.3 to finally prove the main result of Theorem 9.2.

:::callout {title="Hint" tone="neutral" collapse="closed"}

$$w(\mu \mid {\text{\ae}}_{<t}) = w_{\mu}/X_{\xi,t-1}$$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Since $${\mathcal{M}} = \{\nu_{1}, \ldots, \nu_{N}\}$$ is finite, we can sum Exercise 11.4 over all $$\nu \in {\mathcal{M}}$$:

$$
\sum_{\nu \in {\mathcal{M}}}w(\nu \mid {\text{\ae}}_{<t})\, \delta_{\nu,t}~\longrightarrow~ 0 \qquad \mu^{\pi}\text{-a.s.}
$$

From Exercise 11.1:

$$
0 ~\leq~ w(\mu \mid {\text{\ae}}_{<t})\big[V_{\mu}^{*}({\text{\ae}}_{<t}) - V_{\mu}^{\pi_\xi^*}({\text{\ae}}_{<t})\big] ~\leq~ \sum_{\nu} w(\nu \mid {\text{\ae}}_{<t})\, \delta_{\nu,t}~\longrightarrow~ 0.
$$

So $$w(\mu \mid {\text{\ae}}_{<t})[V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}] \to 0$$ $$\mu^{\pi}$$-a.s.

It remains to divide by $$w(\mu \mid {\text{\ae}}_{<t})$$. From Exercise 9.3:

$$
w(\mu \mid {\text{\ae}}_{<t}) ~=~ \frac{w_{\mu}}{X_{\xi,t-1}}.
$$

Fix an infinite history outside the (single) $$\mu^{\pi}$$-null set on which $$X_{\xi,t}\to X_{\xi,\infty}< \infty$$ fails. Along this history:

- $$X_{\xi,t-1}\to X_{\xi,\infty}$$, a finite positive number (with $$X_{\xi,\infty}\geq w_{\mu} > 0$$ by Exercise 9.3).
- Hence $$w(\mu \mid {\text{\ae}}_{<t}) = w_{\mu} / X_{\xi,t-1}\to w_{\mu} / X_{\xi,\infty}> 0$$, so eventually $$w(\mu \mid {\text{\ae}}_{<t}) \geq w_{\mu} / (2 X_{\xi,\infty}) > 0$$.

Dividing the convergence $$w(\mu \mid {\text{\ae}}_{<t}) (V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}) \to 0$$ by this positive (per-history) lower bound, and using $$V_{\mu}^{*} - V_{\mu}^{\pi_\xi^*}\geq 0$$:

$$
V_{\mu}^{*}({\text{\ae}}_{<t}) - V_{\mu}^{\pi_\xi^*}({\text{\ae}}_{<t}) ~\longrightarrow~ 0 \qquad \mu^{\pi}\text{-a.s.}
$$

This completes the proof of Theorem 9.2.

:::

:::callout {title="Note" tone="blue"}

**Remark.** We do not need to know which policy $$\tilde\pi$$ is self-optimizing, or whether it is computable. Mere existence suffices. For countable $${\mathcal{M}}$$, this final step is harder: a countable sum of $$\mu^{\pi}$$-a.s.-convergent sequences need not converge $$\mu^{\pi}$$-a.s. The general proof uses a "convergence of mixture tails" argument (Hutter 2005, Lem. 5.28).

:::

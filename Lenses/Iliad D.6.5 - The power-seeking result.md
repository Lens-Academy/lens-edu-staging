---
id: 'de447848-75b7-48f2-9d8b-9bdc430deeb7'
title: "D.6.5 The power-seeking result"
tldr: "Proves that for a score rule and a symmetric reward distribution, the option-richer action is at least as likely as the poorer one for at least half of the reward functions, and works an example about gaining resources."
summary_for_tutor: "The result section of Iliad worksheet D.6 Instrumental Convergence. Contains Exercise 3.2 (for a score rule p and an involution phi that embeds a' into a and is a symmetry of D, P[A(r) >= A'(r)] >= 1/2) with a collapsed hint and solution using retargeting and pairing, followed by the example 'gaining resources' with conditions (E) and (D), the strict-majority argument and alignment implications. Keep the notation A(r), A'(r), N_r. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - "Leon Lang (ILIAD), based on work by Alex Turner et al."
source_url: https://iliad-intensive.org/agency/power-seeking/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## The result

The three ingredients now combine: a suitable rule (a score rule, Definition 2.7), an action that keeps more options open (an embedding $$\phi$$, Definition 3.2), and a symmetric reward distribution ($$\phi$$ a symmetry of $${\mathcal{D}}$$, Definition 1.1). Fix $$s$$ and actions $$a,a'$$, and abbreviate the probabilities that the rule $$p$$ lands its choice in the $$a$$- and $$a'$$-options:

$$
A(r) := p\bigl({\mathcal{F}}(s\mid a)\mid s,r\bigr), \qquad A'(r) := p\bigl({\mathcal{F}}(s\mid a')\mid s,r\bigr).
$$

::::callout {title="Exercise" tone="amber"}
**Exercise 3.2.** Let $$p$$ be a score rule, and let $$\phi$$ be an involution that

**1.** embeds $$a'$$ into $$a$$: $$\ \phi\cdot{\mathcal{F}}(s\mid a') \subseteq {\mathcal{F}}(s\mid a)$$; and

**2.** is a symmetry of $${\mathcal{D}}$$: $$\ \phi_{*}{\mathcal{D}} = {\mathcal{D}}$$.

Show that

:::callout {title="Note" tone="blue"}

**Keeping options open is favoured.**

$$
{\mathbb{P}}_{r\sim{\mathcal{D}}}\bigl[\, A(r) \ge A'(r) \,\bigr] \;\ge\; \tfrac{1}{2}.
$$

:::

That is: for $${\mathcal{D}}$$-most reward functions, $$p$$ is at least as likely to act through the option-richer action $$a$$ as through $$a'$$.
::::

:::callout {title="Hint" tone="neutral" collapse="closed"}

write $$N_{r}(X) := \sum_{f\in X}\nu(f^{\top} r)$$, so $$A = N_{r}({\mathcal{F}}(s\mid a))/N_{r}({\mathcal{F}}(s))$$ and likewise $$A'$$. From Exercise 2.3, $$N_{\phi\cdot r}(\phi\cdot Y) = N_{r}(Y)$$ for every $$Y$$. Compare $$A, A'$$ at $$r$$ and at $$\phi\cdot r$$; the denominators cancel.

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Write $$N_{r}(X) = \sum_{f\in X}\nu(f^{\top} r)$$, so $$p(X\mid s,r) = N_{r}(X)/N_{r}({\mathcal{F}}(s))$$, and put $$G := \phi\cdot{\mathcal{F}}(s\mid a') \subseteq {\mathcal{F}}(s\mid a)$$ — a copy of $${\mathcal{F}}(s\mid a')$$ inside $${\mathcal{F}}(s\mid a)$$, as $$\phi$$ is injective. Termwise, Exercise 2.3 gives the **swap identity**

$$
N_{\phi\cdot r}(\phi\cdot Y) = \sum_{f\in Y}\nu\bigl((\phi\cdot f)^{\top}(\phi\cdot r)\bigr) = \sum_{f\in Y}\nu(f^{\top} r) = N_{r}(Y).
$$

*Retargeting.* Suppose $$A'(r) > A(r)$$. These share the denominator $$N_{r}({\mathcal{F}}(s))$$, so $$N_{r}({\mathcal{F}}(s\mid a')) > N_{r}({\mathcal{F}}(s\mid a)) \ge N_{r}(G)$$ — the last step since $$G\subseteq{\mathcal{F}}(s\mid a)$$ and $$\nu\ge0$$. Evaluate at $$\phi\cdot r$$, where $$A, A'$$ share the denominator $$N_{\phi\cdot r}({\mathcal{F}}(s))$$. By the swap identity ($$\phi\cdot{\mathcal{F}}(s\mid a') = G$$ and $$\phi\cdot G = {\mathcal{F}}(s\mid a')$$ since $$\phi$$ is an involution),

$$
\begin{aligned}A'(\phi\cdot r)&= \frac{N_{\phi\cdot r}({\mathcal{F}}(s\mid a'))}{N_{\phi\cdot r}({\mathcal{F}}(s))}= \frac{N_{r}(G)}{N_{\phi\cdot r}({\mathcal{F}}(s))}, \\ A(\phi\cdot r)&\ge \frac{N_{\phi\cdot r}(G)}{N_{\phi\cdot r}({\mathcal{F}}(s))}= \frac{N_{r}({\mathcal{F}}(s\mid a'))}{N_{\phi\cdot r}({\mathcal{F}}(s))},\end{aligned}
$$

the inequality because $$G\subseteq{\mathcal{F}}(s\mid a)$$. As $$N_{r}({\mathcal{F}}(s\mid a')) > N_{r}(G)$$, we get $$A(\phi\cdot r) > A'(\phi\cdot r)$$.

*Pairing.* Thus $$\phi$$ maps $$\{A' > A\}$$ into the disjoint set $$\{A > A'\}$$. As $$\phi$$ is an involution with $$\phi_{*}{\mathcal{D}} = {\mathcal{D}}$$, the map $$r\mapsto\phi\cdot r$$ is a $${\mathcal{D}}$$-preserving bijection, so $${\mathcal{D}}\{A' > A\} = {\mathcal{D}}(\phi\cdot\{A' > A\}) \le {\mathcal{D}}\{A > A'\}$$. These are disjoint, so $${\mathcal{D}}\{A' > A\}\le\tfrac{1}{2}$$, and $${\mathbb{P}}_{{\mathcal{D}}}[A\ge A'] = 1 - {\mathcal{D}}\{A' > A\}\ge\tfrac{1}{2}$$.

:::

\### An example: gaining resources

Consider the environment

![diagram](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-power-seeking-tikz-c2cf25fd2b4e-1016695c.png)

At $$s$$ the agent may **gain resources** ($$a$$), reaching $$G_{1}$$ — a state it can *rest* in (a $$1$$-cycle) or *leverage* to move on to a further achievement $$G_{2}$$; or **forgo** them ($$a'$$), leading to the single modest outcome $$B$$. Both $$B$$ and $$G_{2}$$ are terminal. Fix any $$\gamma \in (0,1)$$. The options under each action are the visitation distributions

$$
\begin{aligned}{\mathcal{F}}(s\mid a')&= \{\, f' \,\},&f'&= e_{s} + \tfrac{\gamma}{1-\gamma}\,e_{B}, \\[2pt] {\mathcal{F}}(s\mid a)&= \{\, f_{G_1},\, f_{G_2}\,\},&f_{G_1}&= e_{s} + \tfrac{\gamma}{1-\gamma}\,e_{G_1}, \\[2pt]&&f_{G_2}&= e_{s} + \gamma\,e_{G_1}+ \tfrac{\gamma^2}{1-\gamma}\,e_{G_2}:\end{aligned}
$$

forgoing keeps one option (rest at $$B$$), gaining keeps two (rest at $$G_{1}$$, or move on to $$G_{2}$$).

Let $$\phi$$ be the involution that **swaps $$B$$ and $$G_{1}$$** — the immediate results of $$a'$$ and $$a$$ — and fixes every other state. Then:

**(E)** $$\phi\cdot f' = e_{s} + \tfrac{\gamma}{1-\gamma}\,e_{G_1}= f_{G_1}\in {\mathcal{F}}(s\mid a)$$, so $$\phi$$ embeds $$a'$$ into $$a$$;

**(D)** $$\phi$$ swaps the coordinates $$r(B)$$ and $$r(G_{1})$$, so $$\phi_{*}{\mathcal{D}} = {\mathcal{D}}$$ exactly when the joint law of $$r$$ is invariant under that swap, i.e.  $$\bigl(r(B),\,r(G_{1}),\,(r(s))_{s\ne B,G_1}\bigr)$$ and $$\bigl(r(G_{1}),\,r(B),\,(r(s))_{s\ne B,G_1}\bigr)$$ have the same law under $${\mathcal{D}}$$.

With any score rule $$p$$ (say $$\mathrm{Bz}_{T}$$), Exercise 3.2 applies: for $${\mathcal{D}}$$-most goals the agent is at least as likely to gain resources as to forgo them. Since $$a, a'$$ are the only actions at $$s$$, $$A(r) + A'(r) = 1$$ and the statement reads $${\mathbb{P}}_{r\sim{\mathcal{D}}}[\,A(r) \ge \tfrac{1}{2}\,] \ge \tfrac{1}{2}$$. Here forgoing has a single outcome, but nothing in Exercise 3.2 needs that: $$a'$$ could open onto a whole sub-world of modest outcomes and, as long as $$\phi$$ embeds that bundle into the richer one under $$a$$, the conclusion is unchanged.

*Strictly more.* The leverage option $$f_{G_2}$$ is the surplus. Take rewards with $$r(G_{2})$$ so large that $$f_{G_2}$$ is the unique optimum; then $$A(r) > A'(r)$$. Swapping $$B$$ and $$G_{1}$$ leaves $$r(G_{2})$$ untouched, and

$$
f_{G_2}^{\top}(\phi\cdot r) = r(s) + \gamma\,r(B) + \tfrac{\gamma^2}{1-\gamma}\,r(G_{2})
$$

is still the largest quality, so $$A(\phi\cdot r) > A'(\phi\cdot r)$$ as well. These rewards prefer $$a$$ at $$r$$ *and* at $$\phi\cdot r$$, with no $$a'$$-preferring partner. Provided $${\mathcal{D}}$$ charges this region (e.g. it has full support), they tip the bound to a strict majority: the agent is *strictly* more likely to gain resources than to forgo them.

*Alignment implications.* Condition (D) says that, a priori, the learned reward is as likely to reward the modest outcome $$B$$ as the resource-rich $$G_{1}$$: speculatively, a generic training process does not mark "having resources" as a special kind of state, so the reward could land on either. That exchangeability is exactly what makes $$\mathrm{swap}(B,G_{1})$$ a symmetry of $${\mathcal{D}}$$. Alignment work may try to *break* that symmetry, by reliably encoding "stay modest" as the goal.

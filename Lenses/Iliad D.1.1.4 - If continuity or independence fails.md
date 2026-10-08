---
id: '897dfdba-e0d6-40f0-87a1-56434e8e9209'
title: "D.1.1.4 If continuity or independence fails"
tldr: "Explains what breaks when continuity or independence fails: lexicographic preferences and the Allais pattern, followed by an exercise on failures of all the axioms."
summary_for_tutor: "This is the second part of Section 5 of worksheet D.1.1 (preferences to rewards), 'If continuity or independence fails'. It covers lexicographic or non-Archimedean utilities when continuity fails, the Allais example (lotteries A, B, C, D) when independence fails, and links to prospect theory. It contains Exercise 5.3 (a-d: incomplete preference, three-cycle and money pump, lexicographic preference, Allais pattern) with collapsed solutions. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Fernando E. Rosas
source_url: https://iliad-intensive.org/agency/preferences-to-rewards/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### If continuity or independence fails

It is useful to separate the roles of the four vNM axioms:

- As before, completeness and transitivity give us an ordinal utility on deterministic trajectories.
- Continuity and independence turn that ordinal picture into an *expected* utility theory over uncertain prospects.

If completeness or transitivity fail, as discussed in the previous section, we lose hope of describing the preference by a single scalar quantity. If continuity or independence fails, the preference will generally no longer admit the linear expectation form.

**Failure of continuity.**  To build intuition, let $$x\succ y\succ z$$ and define

$$
\mu_{\lambda}=\lambda x + (1-\lambda)z.
$$

Then

$$
\mu_{0}=z,\qquad \mu_{1}=x,
$$

so as $$\lambda$$ increases from $$0$$ to $$1$$, the lottery moves from the worse prospect $$z$$ to the better prospect $$x$$. Continuity says, informally, that preferences vary smoothly along this path. In particular, it says that the intermediate prospect $$y$$ can be matched by some mixture of the better and worse prospects:

$$
y \sim \lambda x + (1-\lambda)z
$$

for some $$\lambda\in(0,1)$$. Intuitively, the axiom requires no abrupt jumps in preference as the mixture probabilities vary.

When continuity fails, some distinctions can become *lexicographic*. For example, we could have a case where $$y\succ \mu_{0} = z$$, but $$\mu_{\lambda}\succ y$$ for all $$\lambda>0$$. This means that $$x$$ has absolute priority over $$y$$: as soon as $$x$$ appears with any nonzero probability, the lottery becomes strictly better than $$y$$. One way to interpret this is that some considerations are given lexical priority over others. For instance, avoiding catastrophe might outrank ordinary gains so completely that no finite improvement in ordinary reward compensates for even an arbitrarily small increase in catastrophic risk. Such preferences need not be contradictory; they are simply too sharp to be captured by a single real-valued utility whose expectations are taken in the usual way.

What breaks in this case is not all representations, but the *real-valued* vNM representation. If continuity is dropped, one is naturally led to lexicographic or non-Archimedean representations: for example, ordered pairs or vectors of utilities compared lexicographically, or utilities with infinitesimal scales (Fishburn 1971). In those models, the first coordinate records the highest-priority consideration, and lower coordinates matter only when higher ones tie.

**Failure of independence.**

Independence says that common lottery components should cancel. If $$\mu\succcurlyeq\nu$$, then mixing both with the same background lottery $$\xi$$ at the same rate should preserve the ranking:

$$
\lambda \mu +(1-\lambda)\xi \succcurlyeq \lambda \nu +(1-\lambda)\xi.
$$

So the relative ranking of $$\mu$$ and $$\nu$$ should depend only on how they differ, not on the common part they share.

When independence fails, the value of a prospect depends on its *context*. The same local substitution can be attractive in one background and unattractive in another. This is exactly what the Allais pattern shows (Allais 1953). Let $$h_{5}\succ h_{1}\succ h_{0}$$ denote trajectories yielding $$5$$, $$1$$, and $$0$$ million, and consider

$$
A = 1\cdot h_{1}, \qquad B = 0.89\, h_{1} + 0.10\, h_{5} + 0.01\, h_{0},
$$

$$
C = 0.11\, h_{1} + 0.89\, h_{0}, \qquad D = 0.10\, h_{5} + 0.90\, h_{0}.
$$

Many people prefer $$A$$ to $$B$$, but prefer $$D$$ to $$C$$. Under independence this is impossible, because $$A$$ versus $$B$$ and $$C$$ versus $$D$$ differ only by a common consequence. The reversal shows that certainty is treated as psychologically special: replacing a sure outcome by a tiny risk of getting nothing matters more than expected utility allows.

This is the general lesson of independence failure. Probabilities are no longer aggregated linearly against a fixed utility function on trajectories. Common branches cannot be canceled, and the whole shape of the distribution starts to matter. Decision makers may overweight certainty, distort small probabilities, care about disappointment or regret, or evaluate gains and losses relative to a reference point rather than in absolute terms. This is the route taken by prospect theory and related non-expected-utility models (Kahneman & Tversky 1979; Machina 1982).

From the perspective of sequential choice, independence also matters because it allows one to replace a sublottery by an equivalent one without changing the value of the larger plan. If independence fails, the value of a branch may depend on the branches surrounding it, so local and global evaluations need not line up. Hammond's consequentialist argument shows that, together with dynamic consistency and suitable sequential assumptions, one is pushed back toward independence (Hammond 1988). But that only shows one route to coherent planning. One may instead keep a richer, non-linear evaluation of lotteries and give up the idea that common consequences are always behaviorally irrelevant.

So the two failures have different meanings. Failure of continuity says that some priorities are infinitely sharp, leading naturally to lexicographic or infinitesimal utility scales. Failure of independence says that uncertainty is evaluated holistically rather than by linear averaging, leading to models in which background risk, certainty, or reference dependence affect choice.

:::callout {title="Exercise" tone="amber"}
**Exercise 5.3 (Failures of the vNM axioms).** Here we will study the consequences of different axioms.

**(a)** Construct a simple incomplete preference relation on three trajectories. Why can it not be represented by a single real-valued ordinal utility?

**(b)** Construct a three-cycle and explain how it gives rise to a money pump.

**(c)** Give an example of a lexicographic preference over three outcomes and show that it violates continuity.

**(d)** Write down the Allais pattern from Section 5 and explain which axiom it violates.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Let $$x\succ y$$, $$x\succ z$$, with $$y$$ and $$z$$ incomparable (neither $$y\succcurlyeq z$$ nor $$z\succcurlyeq y$$). Any $$u\colon\{x,y,z\}\to{\mathbb{R}}$$ satisfies $$u(y)\geq u(z)$$ or $$u(z)\geq u(y)$$ because the reals are totally ordered, so the relation it represents is complete; incomparability cannot be encoded by a single real-valued function.

**(b)** Take $$x\succ y\succ z\succ x$$. Suppose you hold $$x$$ and are willing to pay some small $$\varepsilon>0$$ to exchange an item for one you strictly prefer. Since $$z\succ x$$ you pay to swap $$x\to z$$; since $$y\succ z$$ you pay to swap $$z\to y$$; since $$x\succ y$$ you pay to swap $$y\to x$$. You are back where you started, $$3\varepsilon$$ poorer, and the cycle can be run forever.

**(c)** Give outcomes two attributes and compare lexicographically (the first attribute decides unless tied): $$A=(1,0)$$, $$B=(0,1)$$, $$C=(0,0)$$, so $$A\succ B\succ C$$. Extend to lotteries by comparing expected attribute vectors lexicographically. Continuity would require some $$p\in[0,1]$$ with $$B\sim pA+(1-p)C$$. But that mixture has attribute vector $$(p,0)$$: for every $$p>0$$ it beats $$B$$ on the first attribute, and for $$p=0$$ it is $$C\succ$$-below $$B$$. No mixing weight produces indifference.

**(d)** With $$h_{5}\succ h_{1}\succ h_{0}$$ paying $$5$$, $$1$$ and $$0$$ million, the pattern of Section 5 is

$$
A = 1\cdot h_{1}, \qquad B = 0.89\,h_{1}+0.10\,h_{5}+0.01\,h_{0},
$$

$$
C = 0.11\,h_{1}+0.89\,h_{0}, \qquad D = 0.10\,h_{5}+0.90\,h_{0},
$$

with $$A\succ B$$ but $$D\succ C$$. Both pairs differ only by a *common consequence*: replacing $$0.89$$ of $$h_{1}$$ by $$0.89$$ of $$h_{0}$$ turns $$A$$ into $$C$$ and $$B$$ into $$D$$. Independence says a ranking is unchanged when the same consequence is mixed into both sides with the same weight, so the pattern violates independence (completeness, transitivity, and continuity are all consistent with it).

:::

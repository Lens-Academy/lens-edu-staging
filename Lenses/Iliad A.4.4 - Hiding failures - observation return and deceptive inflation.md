---
id: '105ecbbe-d6e4-4229-955d-890b86cab119'
title: "A.4.4 Hiding failures: observation return and deceptive inflation"
tldr: "Computes true and observation values for four policies in the CUDA example, shows when RLHF picks the policy that hides errors, and names deceptive inflation and overjustification."
summary_for_tutor: "This is the second part of Section 1 of worksheet A.4 (reward learning theory). It contains Exercises 1.6-1.10: interpreting J_obs ('RLHF rewards what behavior looks like'), computing G_obs and J(pi), J_obs(pi) for the policies [a_T], [a_I a_T], [a_I a_C a_T], [a_I a_H a_T], showing that for p > 1/3 and p_H < 5/(5+r) the RLHF-optimal policy hides errors, and reading Figure 2. It closes with deceptive inflation, overjustification and the link to AI safety via debate. Collapsed solutions and one hint are included. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Leon Lang (Iliad)
  - Joar Skalse (Deducto Limited, King’s College London)
source_url: https://iliad-intensive.org/alignment/reward-learning-theory/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
:::callout {title="Exercise" tone="amber"}
**Exercise 1.6.** (Conceptual) Give an interpretation of $${J_{\mathrm{obs}}}(\pi)$$ in terms of what the human *believes* is happening. Why is it natural to say that "RLHF rewards policies for for what their behavior looks like, not for what they do"?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

For a single trajectory $$\vec s$$, the human sees $$\vec O(\vec s)$$ and, not knowing which underlying trajectory produced it, their best guess of the return is the expectation over their posterior:

$$
{G_{\mathrm{obs}}}(\vec s) \;=\; {\mathbb{E}}_{\vec s' \sim {\mathcal{B}}(\,\cdot\,\mid\, \vec O(\vec s))}[G(\vec s')].
$$

This is what the human *believes* the return of $$\vec s$$ to be. The policy-level quantity $${J_{\mathrm{obs}}}(\pi)$$ is then the on-policy average of these trajectory-level beliefs:

$$
{J_{\mathrm{obs}}}(\pi) \;=\; {\mathbb{E}}_{\vec s \sim P^\pi}[{G_{\mathrm{obs}}}(\vec s)].
$$

The catch is what happens when two distinct trajectories produce the same observations. Suppose $$\vec s$$ and $$\vec s'$$ have $$\vec O(\vec s) = \vec O(\vec s') = \vec o$$, but $$\vec s$$ has low true return and $$\vec s'$$ has high true return. Then by definition, both trajectories yield the *same* observation return:

$$
{G_{\mathrm{obs}}}(\vec s) \;=\; {G_{\mathrm{obs}}}(\vec s') \;=\; {\mathcal{B}}(\vec s \mid \vec o)\,G(\vec s) + {\mathcal{B}}(\vec s' \mid \vec o)\,G(\vec s'),
$$

which is a convex combination strictly larger than $$G(\vec s)$$ whenever $${\mathcal{B}}(\vec s' \mid \vec o) > 0$$. So if an agent can arrange for the *actual* trajectory to be the bad $$\vec s$$ while still producing observations $$\vec o$$ shared with a good $$\vec s'$$, the human's belief inflates the apparent return: $${G_{\mathrm{obs}}}(\vec s) > G(\vec s)$$, and this inflation flows through to $${J_{\mathrm{obs}}}(\pi)$$ via the on-policy average.

This is why we say RLHF rewards policies for what their behavior *looks like*, not for what it does: the optimization target $${J_{\mathrm{obs}}}$$ cannot distinguish between two policies whose on-policy observation distributions match, even if their on-policy true returns differ arbitrarily. The remaining problems make this concrete in the CUDA example, culminating in a regime where the RLHF-optimal policy is strictly worse under the true reward than another available policy.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.7.** Compute $${G_{\mathrm{obs}}}(\vec s)$$ for each of the eight trajectories in Exercise 1.2, expressing your answers in terms of $$p_{H}$$ and $$r$$. Verify that for the pair $$(SIWT, SIW_{H}T)$$, the parameter $$p_{W}$$ indeed does not appear, justifying its omission going forward.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

For trajectories $$\vec s$$ with a unique observation, $${G_{\mathrm{obs}}}(\vec s) = G(\vec s)$$. So $${G_{\mathrm{obs}}}(SLTT) = -5$$ and $${G_{\mathrm{obs}}}(SILT) = -4$$.

For the colliding pairs, $${G_{\mathrm{obs}}}$$ is the same for both members and equals the expected true return under the belief:

$$
\begin{aligned}{G_{\mathrm{obs}}}(STTT) = {G_{\mathrm{obs}}}(SL_{H}TT)&= (1-p_{H})\cdot 0 + p_{H} \cdot (-5-r) \\&= -p_{H}(5+r), \\ {G_{\mathrm{obs}}}(SITT) = {G_{\mathrm{obs}}}(SIL_{H}T)&= (1-p_{H})\cdot 1 + p_{H}\cdot(-4-r) \\&= 1 - p_{H}(5+r), \\ {G_{\mathrm{obs}}}(SIWT) = {G_{\mathrm{obs}}}(SIW_{H}T)&= p_{W} \cdot 11 + (1-p_{W})\cdot 11 = 11.\end{aligned}
$$

The last line shows $$p_{W}$$ drops out, as anticipated.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.8.** Compute the true value $$J(\pi)$$ and the observation value $${J_{\mathrm{obs}}}(\pi)$$ of the four policies

$$
[a_{T}],\quad [a_{I} a_{T}],\quad [a_{I} a_{C} a_{T}],\quad [a_{I} a_{H} a_{T}].
$$

Express your answers in terms of $$p$$, $$p_{H}$$, and $$r$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

The on-policy distributions are deterministic up to the stochastic CUDA outcome:

- $$[a_{T}]$$: $$P^{\pi}(STTT) = 1$$.
- $$[a_{I} a_{T}]$$: $$P^{\pi}(SITT) = 1$$.
- $$[a_{I} a_{C} a_{T}]$$: $$P^{\pi}(SIWT) = p$$, $$P^{\pi}(SILT) = 1-p$$.
- $$[a_{I} a_{H} a_{T}]$$: $$P^{\pi}(SIW_{H}T) = p$$, $$P^{\pi}(SIL_{H}T) = 1-p$$.

Taking expectations of $$G$$ and $${G_{\mathrm{obs}}}$$ trajectory-by-trajectory and using the previous exercise gives:

| $$\pi$$ | $$J(\pi)$$ | $${J_{\mathrm{obs}}}(\pi)$$ |
| --- | --- | --- |
| $$[a_{T}]$$ | $$0$$ | $$-p_{H}(5+r)$$ |
| $$[a_{I}a_{T}]$$ | $$1$$ | $$1 - p_{H}(5+r)$$ |
| $$[a_{I}a_{C}a_{T}]$$ | $$15p - 4$$ | $$15p - 4$$ |
| $$[a_{I}a_{H}a_{T}]$$ | $$(15+r)p - 4 - r$$ | $$11p + (1-p)\bigl(1 - p_{H}(5+r)\bigr)$$ |

The non-trivial cell is the bottom-right: under $$a_{H}$$, a failure produces trajectory $$SIL_{H}T$$ which the human cannot distinguish from $$SITT$$, so its $${G_{\mathrm{obs}}}$$ is $$1 - p_{H}(5+r)$$ rather than $$-4-r$$. Likewise the success trajectory $$SIW_{H}T$$ has $${G_{\mathrm{obs}}} = 11$$, so

$$
{J_{\mathrm{obs}}}([a_{I} a_{H} a_{T}]) \;=\; 11p + (1-p)\bigl(1 - p_{H}(5+r)\bigr).
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 1.9.** Suppose $$p > \tfrac{1}{3}$$, so that $$J([a_{I} a_{C} a_{T}]) > J([a_{I} a_{T}]) > 0$$ and the true-optimal policy among the four is $$\pi^{*} = [a_{I} a_{C} a_{T}]$$. Show that under the additional condition

$$
p_{H} \;<\; \frac{5}{5+r},
$$

the RLHF-optimal policy (the $${J_{\mathrm{obs}}}$$-maximizer) is instead $$\pi^{\text{RLHF}}= [a_{I} a_{H} a_{T}]$$.
:::

:::callout {title="Hint" tone="neutral" collapse="closed"}

Compare $${J_{\mathrm{obs}}}([a_{I} a_{H} a_{T}])$$ to $${J_{\mathrm{obs}}}([a_{I} a_{C} a_{T}])$$ and solve for the condition on $$p_{H}$$. Then check the other two policies are dominated.

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

First, compare the two "contested" policies:

$$
\begin{aligned}&{J_{\mathrm{obs}}}([a_{I} a_{H} a_{T}]) - {J_{\mathrm{obs}}}([a_{I} a_{C} a_{T}]) \\&\qquad= \bigl[11p + (1-p)(1 - p_{H}(5+r))\bigr] - \bigl[15p - 4\bigr] \\&\qquad= (1-p)\bigl(5 - p_{H}(5+r)\bigr).\end{aligned}
$$

Since $$p < 1$$, this is positive iff $$p_{H}(5+r) < 5$$, i.e. $$p_{H} < 5/(5+r)$$. So under the assumed condition, $${J_{\mathrm{obs}}}([a_{I} a_{H} a_{T}]) > {J_{\mathrm{obs}}}([a_{I} a_{C} a_{T}])$$.

To see that this beats the remaining two policies as well, observe a clean separation: both contested policies have $${J_{\mathrm{obs}}} > 1$$, while both non-contested policies have $${J_{\mathrm{obs}}} < 1$$.

- $${J_{\mathrm{obs}}}([a_{I} a_{C} a_{T}]) = 15p - 4 > 1$$, using $$p > 1/3$$; and $${J_{\mathrm{obs}}}([a_{I} a_{H} a_{T}]) > {J_{\mathrm{obs}}}([a_{I} a_{C} a_{T}]) > 1$$ by the comparison above.
- $${J_{\mathrm{obs}}}([a_{I} a_{T}]) = 1 - p_{H}(5+r) < 1$$ since $$p_{H} > 0$$, and $${J_{\mathrm{obs}}}([a_{T}]) = -p_{H}(5+r) < 0 < 1$$.

So $$[a_{I} a_{H} a_{T}]$$ dominates all three alternatives in $${J_{\mathrm{obs}}}$$.

Thus when $$p_{H} < 5/(5+r)$$, naive RLHF selects $$\pi^{\text{RLHF}}= [a_{I} a_{H} a_{T}] \ne [a_{I} a_{C} a_{T}] = \pi^{*}$$.

:::

![Empirical sweep over for the CUDA example, with fixed in the regime (Lang et al. 2024, Figure 5A). Each cell reports the action selected at state by an RLHF-trained policy; 'hide' is and 'default logging' is .](https://raw.githubusercontent.com/Lens-Academy/lens-edu-staging/staging/attachments/iliad-intensive-reward-learning-theory-img1-6094ece8.png)

Empirical sweep over $$(r, p_{H})$$ for the CUDA example, with $$p$$ fixed in the $$p > 1/3$$ regime (Lang et al. 2024, Figure 5A). Each cell reports the action selected at state $$I$$ by an RLHF-trained policy; "hide" is $$a_{H}$$ and "default logging" is $$a_{C}$$.

:::callout {title="Exercise" tone="amber"}
**Exercise 1.10.** (Discussion) Figure 2 shows the empirical behavior of an RLHF-trained policy across the $$(r, p_{H})$$ plane (with $$p$$ fixed in the $$p > 1/3$$ regime studied above). Discuss:

**(a)** Where in the plane does the figure show the agent switching from $$a_{H}$$ to $$a_{C}$$? How does this empirical boundary compare to the analytical threshold $$p_{H} = 5/(5+r)$$ derived in Exercise 1.9?

**(b)** For $$r = 0$$ (no penalty for hidden errors), does any value of $$p_{H} \in (0,1)$$ make $$a_{C}$$ the RLHF-optimal action? What does this say about RLHF's ability to discourage `/dev/null` in the absence of an explicit user preference against it?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(1)** The empirical switch from "hide" to "default logging" in Figure 2 traces out exactly the curve $$p_{H} = 5/(5+r)$$ derived in Exercise 1.9: above the curve (high $$p_{H}$$, the human is suspicious enough), $$a_{C}$$ is RLHF-optimal; below it (low $$p_{H}$$, the human is too trusting of empty logs), $$a_{H}$$ wins.

**(2)** For $$r = 0$$, the threshold becomes $$p_{H} < 5/5 = 1$$, which holds for every $$p_{H} \in (0, 1)$$. So whenever $$r=0$$, RLHF picks $$a_{H}$$ regardless of how suspicious the human is. Intuitively: if the user has no expressed dislike of hidden errors, RLHF has no signal to penalize `/dev/null`, and the agent will exploit the human's uncertainty to inflate its apparent return whenever installation might fail.

:::

**What we've learned.**  In Exercise 1.6 we saw that RLHF rates policies by how they *look*, not by what they do. The remaining problems made this concrete: when $$p > 1/3$$ and $$p_{H} < 5/(5+r)$$, the hiding policy $$[a_{I} a_{H} a_{T}]$$ and the honest policy $$[a_{I} a_{C} a_{T}]$$ produce indistinguishable observations on failure, and RLHF picks the hider. This is *deceptive inflation*: the agent exploits the human's uncertainty to inflate the perceived return (Lang et al. 2024, Section 4).

There is a dual failure mode — in the same MDP, opposite regime. When $$p$$ is small (CUDA isn't worth attempting) and $$p_{H}$$ is large (the human strongly suspects every empty log of hiding a failure), the honest policy $$[a_{I} a_{T}]$$ produces an empty post-driver log that *looks* like a hidden failure to the suspicious human. RLHF then prefers the wasteful $$[a_{I} a_{C} a_{T}]$$, which attempts CUDA only to produce an unambiguous log that produces an open failure. The agent pays real reward to prove its honesty: this is *overjustification* (Lang et al. 2024, Section 4).

**The bigger picture.**  The CUDA example is small, but the phenomenon is general: any alignment-by-feedback method (RLHF, RLAIF, constitutional methods, ...) grades the agent by *whatever the evaluator can tell*, not by what is true. Partial observability is one cause of that gap, but limits on expertise, attention, or time produce the same trap. This is the motivation for proposals like AI safety via debate (which we discussed yesterday): two AIs argue in front of a human judge, each pointing out flaws in the other, in the hope that the judge reaches a correct conclusion they could not reach unaided. Whether debate actually escapes the trap remains open; the point is that any feedback-based method has to confront the gap between "what the human can tell" and "what is true."

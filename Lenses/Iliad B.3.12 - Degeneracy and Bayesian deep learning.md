---
id: '913f3fa1-a881-4303-9c83-ceafd8dbf602'
title: "B.3.12 Degeneracy and Bayesian deep learning"
tldr: "States Watanabe's free energy formula linking the learning coefficient to Bayesian learning, and explains Bayesian phase transitions as the sample size grows."
summary_for_tutor: "This is Section 4.1 and 4.2 of Iliad worksheet B.3 Singular Learning Theory. It gives Theorem 4.1 (local free energy formula F_n(U) = n L_n(w*) + lambda_U log n - (mu_U - 1) log log n + O_p(1)), the interpretation as data fit plus complexity, internal model selection, the BIC remark for regular models, and Bayesian phase transitions with the critical sample size n*. It contains Exercises 4.1 (numerical demonstration for the cubic model) and 4.2 (exploring phase transitions) with collapsed solutions. Keep the notation F_n, lambda, n*. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Kai Ogden (University of Oxford)
  - Matthew Farrugia-Roberts (University of Oxford)
  - Zach Furman (The University of Melbourne)
source_url: https://iliad-intensive.org/learning/singular-learning-theory/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 4. Degeneracy and Bayesian deep learning

In Sections 2 and 3, we studied the geometry of degeneracy in parameter space and introduced the local learning coefficient $\lambda(w^{*})$ as a measure of the degree of degeneracy at a local minimum $w^{*}$. We now show that this geometry has consequences for learning (in the Bayesian setting). In particular, it creates a trade-off between model fit and model complexity that drives learning, providing a mechanism for *internal model selection*.

\### 4.1 Watanabe's free energy formula

Recall the Bayesian learning setup from Section 1.4. We have a parameter–distribution map $\Psi : {\mathcal{W}} \to {\mathcal{D}}$ sending each parameter $w$ to a conditional distribution with density $p(y \mid x, w)$, a smooth positive prior $\varphi$ on ${\mathcal{W}}$, and a data set of $n$ i.i.d. examples from a data distribution $q$. Take the loss function to be the negative log-likelihood

$$
L_{n}(w) = -\frac{1}{n}\sum_{i=1}^{n} \log p(y^{(i)}\mid x^{(i)}, w), \qquad L(w) = {\mathbb{E}}_{(x,y) \sim q}\!\left[-\log p(y \mid x, w)\right].
$$

The posterior $\pi_{n}$ is given by Bayes' rule (13) and as we saw in Exercises 1.7 and 1.8 it concentrates around regions of parameter space with the lowest local free energy $F_{n}({\mathcal{U}})$ (Definition 1.6).

We now state one of the main results of SLT: an asymptotic expansion of $F_{n}({\mathcal{U}})$ as $n \to \infty$. Under certain technical assumptions on the statistical model (Watanabe 2018; see Lau 2025, § 2.3.1 for a summary), we have the following theorem.

:::callout {title="Theorem" tone="green"}

**Theorem 4.1 (Local free energy formula).** Suppose ${\mathcal{U}} \subseteq {\mathcal{W}}$ contains at least one minimiser of $L$, and let $w^{*} \in {\mathcal{U}}$ be any such minimiser. Define $\lambda_{{\mathcal{U}}}$ as the smallest local learning coefficient among all minimisers in ${\mathcal{U}}$, and let $\mu_{{\mathcal{U}}}$ be the maximum local multiplicity associated with $\lambda_{{\mathcal{U}}}$. Then, as $n \to \infty$,

$$
F_{n}({\mathcal{U}}) = nL_{n}(w^{*}) + \lambda_{{\mathcal{U}}}\log n - (\mu_{{\mathcal{U}}}- 1)\log \log n + O_{p}(1).
$$

:::

:::callout {title="Note" tone="blue"}

**Remark.** Since $L_{n}(w^{*})$ is a random variable, so is $F_{n}({\mathcal{U}})$. The expansion Equation 49 is an asymptotic statement about random variables where the remainder $O_{p}(1)$ denotes a term that is bounded in probability as $n \to \infty$.

:::

To understand what this expansion tells us about Bayesian learning, note that the two leading terms of this expansion have transparent interpretations:

$$
F_{n} \;\approx\; \underbrace{n L_n\vphantom{\lambda}}_{\text{data fit}}\;+\; \underbrace{\lambda \log n}_{\text{complexity}}
$$

Let $w_{1}, w_{2} \in {\mathcal{W}}$ be minimisers of the population loss with $L(w_{1}) = L(w_{2})$ and $\lambda(w_{1}) \leq \lambda(w_{2})$. Then for fixed large $n$, the free energy of a neighbourhood of $w_{1}$ is smaller than that of $w_{2}$, so the posterior concentrates around the simpler solution $w_{1}$.

This is an example of **internal model selection** where there are two equally good solutions that minimise the population loss. However, our learning algorithm (Bayesian updating) prefers one solution over the other, in particular the one with lower complexity.

:::callout {title="Note" tone="blue"}

**Remark (Regular models and the BIC).** When the Hessian $\nabla^{2} L(w^{*})$ is non-degenerate, $\lambda(w^{*}) = d/2$ and $\mu(w^{*}) = 1$ by Exercise 3.1. The free energy formula then reduces to $F_{n} \approx n L_{n}(w^{*}) + \frac{d}{2}\log n$, recovering the Bayesian Information Criterion from classical statistics.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 4.1 (Numerical demonstration of the free energy formula).** Consider the statistical model underlying the cubically-parameterised loss from Exercise 3.7. The parameter $\mu \in {\mathbb{R}}$ indexes the family of normal distributions

$$
p(x \mid \mu) = (2\pi)^{-1/2}\exp\!\left(-\frac{1}{2}(x - \mu^{3})^{2}\right).
$$

Suppose the true distribution is

$$
q(x) = (2\pi)^{-1/2}\exp\!\left(-\frac{1}{2}(x - \mu_{0}^{3})^{2}\right)
$$

for some fixed $\mu_{0}$, and equip the model with a standard normal prior

$$
\varphi(\mu) = (2\pi)^{-1/2}\exp\!\left(-\frac{1}{2}\mu^{2}\right).
$$

[*Note:* The following exercises are intended to be attempted with a numerical programming framework such as Python or Julia, rather than by hand.]

**(a)** For $\mu_{0} = 0$, numerically compute the free energy $F_{n}$ for many values of $n$ between $n = 100$ and $n = 10{,}000$. Compare the computed values against the asymptotic estimate $F_{n} \approx nL_{n} + \lambda \log n$, using the value of $\lambda$ from Exercise 3.7(d).

**(b)** Repeat part (a) with $\mu_{0} = 5$.

**(c)** Repeat part (a) with $\mu_{0} = 0.1$. Note that $\mu_{0} = 0.1 \neq 0$, so asymptotically $\lambda = 1/2$, as in part (b). However, observe how for moderate $n$ the free energy behaves more like part (a) than part (b). This is another manifestation of the phenomenon from Exercise 3.7(e): the effects of the singularity at $\mu = 0$ extend into a neighbourhood around it.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

This exercise is computational. We outline the procedure and key observations.

The model is $p(x \mid \mu) = (2\pi)^{-1/2}\exp\!\big({-}\tfrac{1}{2}(x - \mu^{3})^{2}\big)$ with prior $\varphi(\mu) = (2\pi)^{-1/2}\exp(-\mu^{2}/2)$ and true distribution $q(x) = (2\pi)^{-1/2}\exp\!\big({-}\tfrac{1}{2}(x-\mu_{0}^{3})^{2}\big)$.

For each $n$, sample $x^{(1)}, \ldots, x^{(n)}\sim q$ and compute

$$
Z_{n} = \int_{-\infty}^{\infty}\varphi(\mu) \prod_{i=1}^{n} p(x^{(i)}\mid \mu)\, d\mu
$$

then set $F_{n} = -\log Z_{n}$.

The empirical loss is

$$
L_{n}(\mu) = -\frac{1}{n}\sum_{i=1}^{n} \log p(x^{(i)}\mid \mu) = \frac{1}{2}\log(2\pi) + \frac{1}{2n}\sum_{i=1}^{n} (x^{(i)}- \mu^{3})^{2}.
$$

**(a)** For $\mu_{0} = 0$, the LLC is $\lambda = 1/6$ (Exercise 3.7). Plot $F_{n}$ against $n$ and compare with the asymptotic estimate $\hat F_{n} = n L_{n}(0) + \tfrac{1}{6}\log n$. For large $n$, the two curves should agree up to an $O(1)$ offset: $F_{n} - \hat F_{n}$ should stabilise around a constant.

**(b)** For $\mu_{0} = 5$, the LLC is $\lambda = 1/2$ (regular case). The asymptotic estimate is $\hat F_{n} = n L_{n}(5) + \tfrac{1}{2}\log n$.

**(c)** For $\mu_{0} = 0.1$, the asymptotic LLC is $\lambda = 1/2$ (since $\mu_{0} \neq 0$). However, the minimum of $L$ is at $\mu = \mu_{0} = 0.1$, very close to the singularity at $\mu = 0$ where $\lambda = 1/6$. For moderate $n$, the posterior is spread broadly enough that it "feels" the nearby singularity, and $F_{n}$ behaves more like the $\lambda = 1/6$ regime from part (a). Only for sufficiently large $n$ does the posterior concentrate tightly enough around $\mu_{0} = 0.1$ for the regular $\lambda = 1/2$ asymptotics to take hold. This demonstrates that the singularity at $\mu = 0$ influences learning even when $\mu_{0} \neq 0$, provided $\mu_{0}$ is close to the singular point.

:::

\### 4.2 Bayesian phase transitions

So far we have looked at the consequence of the free energy formula when considering $n$ to be fixed. However, we also find it interesting to see what it tells us about changes in the posterior as $n$ increases.

For the rest of this section, assume $n$ is sufficiently large that (i) the free energy can be approximated by the first two terms in its expansion, and (ii) $L_{n} \approx L$ by the law of large numbers, so that the empirical loss can be treated as approximately constant in $n$.

Consider two disjoint regions ${\mathcal{U}}, {\mathcal{V}} \subseteq {\mathcal{W}}$, containing minimisers $u^{\ast}$ and $v^{\ast}$ of the population loss $L$ with local learning coefficients $\lambda_{{\mathcal{U}}}$ and $\lambda_{{\mathcal{V}}}$ respectively. Applying the free energy formula to each region, the log posterior odds between the two regions satisfy

$$
\log \frac{\pi_{n}({\mathcal{U}})}{\pi_{n}({\mathcal{V}})}= F_{n}({\mathcal{V}}) - F_{n}({\mathcal{U}}) \approx n\,\Delta L_{n} + \Delta\lambda \cdot \log n
$$

where $\Delta L_{n} = L_{n}(v^{\ast}) - L_{n}(u^{\ast})$ and $\Delta\lambda = \lambda_{{\mathcal{V}}}- \lambda_{{\mathcal{U}}}$.

Consider the case when one region is more accurate but more complex than the other, i.e.

$$
L_{n}(u^{\ast}) > L_{n}(v^{\ast}) \qquad\text{and}\qquad \lambda_{{\mathcal{U}}}< \lambda_{{\mathcal{V}}}.
$$

Then $\Delta L_{n} < 0$ and $\Delta\lambda > 0$, so the two terms in (50) have opposite signs. For smaller $n$, the $\Delta\lambda \cdot \log n$ term dominates so the log posterior odds is negative meaning the posterior prefers ${\mathcal{U}}$ (the simpler, less accurate region). As $n$ increases, the linear term $n\,\Delta L_{n}$ eventually dominates the logarithmic term, and the posterior shifts to prefer ${\mathcal{V}}$ (the more complex, more accurate region). Setting the leading terms equal, this change occurs at a critical sample size $n^{*}$ satisfying

$$
\frac{n^{*}}{\log n^{*}}\approx \frac{\Delta\lambda}{\lvert\Delta L_{n}\rvert}.
$$

At $n = n^{*}$, the posterior undergoes a **Bayesian phase transition**: the region that dominates the posterior changes abruptly.

:::callout {title="Exercise" tone="amber"}
**Exercise 4.2 (Exploring phase transitions).** We show how *phase transitions* can occur when different local free energies change at different rates.

**(a)** Suppose we partition the overall parameter space into a disjoint union ${\mathcal{W}} = {\mathcal{U}} \sqcup {\mathcal{V}}$. Denote the overall free energy by $F_{n}$ and the local free energies by $F_{n}({\mathcal{U}})$ and $F_{n}({\mathcal{V}})$, respectively. Show that the relationship

$$
F_{n} = -\log(e^{-F_n({\mathcal{U}})}+ e^{-F_n({\mathcal{V}})})
$$

holds.

**(b)** Suppose $F_{n}({\mathcal{U}}) \approx 0.3n + 20 \log n$ and $F_{n}({\mathcal{V}}) \approx 0.5n + 2 \log n$. Plot the overall free energy $F(n)$. Compare against $\min\{F_{n}(U), F_{n}({\mathcal{V}})\}$. What happens around $n = 570$?

**(c)** In statistical physics, a phase transition is traditionally defined as a discontinuity (or rapid change, for finite-size systems) in the derivatives of the free energy. Plot $\frac{d}{dn}F_{n}$ and explain why this justifies calling the phenomenon from b) a phase transition.

**(d)** Change the coefficients of the terms in b). How does this change when a phase transition occurs? Does a phase transition always occur?
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** By definition, the partition function is

$$
Z_{n} = \int_{{\mathcal{W}}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw.
$$

Since ${\mathcal{W}} = {\mathcal{U}} \sqcup {\mathcal{V}}$ is a disjoint union, the integral splits additively:

$$
\begin{aligned}Z_{n}&= \int_{{\mathcal{U}}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw + \int_{{\mathcal{V}}} \varphi(w) \prod_{i=1}^{n} p(x^{(i)}\mid w)\, dw \\&= Z_{n}({\mathcal{U}}) + Z_{n}({\mathcal{V}}).\end{aligned}
$$

Recalling that $F_{n} = -\log Z_{n}$ and similarly for the local free energies,

$$
Z_{n} = e^{-F_n({\mathcal{U}})}+ e^{-F_n({\mathcal{V}})},
$$

and taking the negative logarithm gives

$$
F_{n} = -\log Z_{n} = -\log(e^{-F_n({\mathcal{U}})}+ e^{-F_n({\mathcal{V}})}).
$$

**(b)** The curves $F_{n}$ and $\min(F_{n}({\mathcal{U}}), F_{n}({\mathcal{V}}))$ are nearly identical, both track whichever local free energy is smaller. However, $F_{n}$ is smooth whereas $\min(F_{n}({\mathcal{U}}), F_{n}({\mathcal{V}}))$ has a kink at $n \approx 570$, where $F_{n}({\mathcal{U}}) = F_{n}({\mathcal{V}})$. For $n \lesssim 570$ the simpler region ${\mathcal{V}}$ (lower $\lambda$) dominates; for $n \gtrsim 570$ the lower loss region ${\mathcal{U}}$ (lower loss coefficient) dominates.

**(c)** Differentiating the log-sum-exp from (a),

$$
\frac{d}{dn}F_{n} = \frac{\frac{d}{dn}F_{n}({\mathcal{U}})\,e^{-F_n({\mathcal{U}})}+ \frac{d}{dn}F_{n}({\mathcal{V}})\,e^{-F_n({\mathcal{V}})}}{e^{-F_n({\mathcal{U}})}+ e^{-F_n({\mathcal{V}})}},
$$

Plotting this reveals a steep step around $n \approx 570$, transitioning from $\frac{d}{dn}F_{n}({\mathcal{V}}) \approx 0.5$ to $\frac{d}{dn}F_{n}({\mathcal{U}}) \approx 0.3$. This rapid change in the derivative of $F_{n}$ is a smooth approximation of a discontinuity, justifying the term *phase transition*.

**(d)** Write $F_{n}({\mathcal{U}}) \approx L_{{\mathcal{U}}} \, n + \lambda_{{\mathcal{U}}} \log n$ and $F_{n}({\mathcal{V}}) \approx L_{{\mathcal{V}}} \, n + \lambda_{{\mathcal{V}}} \log n$, and set $\Delta L = L_{{\mathcal{U}}} - L_{{\mathcal{V}}}$ and $\Delta\lambda = \lambda_{{\mathcal{U}}} - \lambda_{{\mathcal{V}}}$. The critical sample size $n^{*}$ where the phase transition occurs satisfies

$$
\Delta L \cdot n^{*} = -\Delta\lambda \cdot \log n^{*}, \qquad\text{i.e.}\qquad \frac{n^{*}}{\log n^{*}}= -\frac{\Delta\lambda}{\Delta L}
$$

Since $n^{*}/\log n^{*}$ is positive, a solution exists if and only if $-\Delta\lambda / \Delta L > 0$, i.e. $\Delta L$ and $\Delta\lambda$ have *opposite signs*. A phase transition occurs precisely when one region fits better while the other is simpler ($\Delta L$ and $\Delta\lambda$ have opposite signs). If both fit and complexity favour the same region, that region dominates for all $n$ and no phase transition occurs.

$n^{*}/\log n^{*}$ is monotonically increasing for $n > e$ so for such $n$, increasing $|\Delta \lambda|$ increases $n^{*}$ and increasing $\Delta L$ decreases $n^{*}$.

:::

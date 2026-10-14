---
id: '1f69e5d0-0e0f-4dbe-8d18-7bd73a435a43'
title: "D.3.2.10 Change of measure"
tldr: "Shows that probabilities under one environment equal expectations of the likelihood ratio under another, and derives a Markov-type inequality for changing measure."
summary_for_tutor: "Section 10 of worksheet D.3.2: Change of measure. Exercise 10.1 (nu^pi[ae_{1:m} in A] = E_{mu^pi}[X_{nu,m} 1_A]), Exercise 10.2 (given without proof: the identity extends to infinite histories with X_{nu,infinity} as a Radon-Nikodym derivative) and Exercise 10.3 (mu^pi[E and X_{nu,infinity} >= epsilon] <= nu^pi[E]/epsilon). Hints and collapsed solutions are given for 10.1 and 10.3. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 10. Change of Measure

::::callout {title="Exercise" tone="amber"}
**Exercise 10.1 [15].** Let $$A$$ be a set of finite histories of length $$m$$. Show:

$$
\nu^{\pi}[{\text{\ae}}_{1:m}\in A] ~=~ {\mathbb{E}}_{\mu^\pi}\big[X_{\nu,m}\cdot \llbracket {\text{\ae}}_{1:m}\in A \rrbracket\big].
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use Exercise 0.1 to show $$\nu^{\pi}/\mu^{\pi} = \nu/\mu = X_{\nu,m}$$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Exercise 0.1, $$\nu^{\pi}({\text{\ae}}'_{1:m}) = \pi({\text{\ae}}'_{1:m}) \cdot \nu({\text{\ae}}'_{1:m})$$ and $$\mu^{\pi}({\text{\ae}}'_{1:m}) = \pi({\text{\ae}}'_{1:m}) \cdot \mu({\text{\ae}}'_{1:m})$$. For any history $${\text{\ae}}'_{1:m}$$ with $$\mu^{\pi}({\text{\ae}}'_{1:m}) > 0$$, the policy factors cancel:

$$
\begin{aligned}\nu^{\pi}({\text{\ae}}'_{1:m}) ~&=~ \frac{\nu^{\pi}({\text{\ae}}'_{1:m})}{\mu^{\pi}({\text{\ae}}'_{1:m})}\cdot \mu^{\pi}({\text{\ae}}'_{1:m}) ~=~ \frac{\nu({\text{\ae}}'_{1:m})}{\mu({\text{\ae}}'_{1:m})}\cdot \mu^{\pi}({\text{\ae}}'_{1:m}) \\ ~&=~ X_{\nu,m}({\text{\ae}}'_{1:m}) \cdot \mu^{\pi}({\text{\ae}}'_{1:m}).\end{aligned}
$$

For histories with $$\mu^{\pi}({\text{\ae}}'_{1:m}) = 0$$: since $$\mu^{\pi} = \pi \cdot \mu$$, some $$\pi(a_{k} \mid {\text{\ae}}'_{<k}) = 0$$, which forces $$\nu^{\pi}({\text{\ae}}'_{1:m}) = 0$$ too (the same $$\pi$$-factor appears in $$\nu^{\pi} = \pi \cdot \nu$$). So both sides are zero.

Summing over $${\text{\ae}}'_{1:m}\in A$$:

$$
\begin{aligned}\nu^{\pi}[{\text{\ae}}_{1:m}\in A] ~&=~ \sum_{{\text{\ae}}'_{1:m} \in A}\nu^{\pi}({\text{\ae}}'_{1:m}) ~=~ \sum_{{\text{\ae}}'_{1:m} \in A}X_{\nu,m}({\text{\ae}}'_{1:m}) \cdot \mu^{\pi}({\text{\ae}}'_{1:m}) \\ ~&=~ {\mathbb{E}}_{\mu^\pi}\big[X_{\nu,m}\cdot \llbracket {\text{\ae}}_{1:m}\in A \rrbracket\big].\end{aligned}
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 10.2.** (Given.) The identity extends to infinite histories: for any event $$A \subseteq ({\mathcal{A}} \times {\mathcal{E}})^{\infty}$$,

$$
\nu^{\pi}[A] ~=~ {\mathbb{E}}_{\mu^\pi}\big[X_{\nu,\infty}\cdot \llbracket {\text{\ae}}_{1:\infty}\in A \rrbracket\big].
$$

This says that $$X_{\nu,\infty}$$ plays the role of the Radon–Nikodym derivative $$\mathrm{d}\nu^{\pi}/\mathrm{d}\mu^{\pi}$$ on the space of infinite histories. The proof rests on two ingredients beyond the scope of this worksheet:

- **$$L^{1}$$ martingale convergence** (closed martingale / Levy's upward theorem): since $${\mathbb{E}}_{\mu^\pi}[X_{\nu,t}] = 1$$ for every $$t$$, the non-negative $$\mu^{\pi}$$-martingale $$(X_{\nu,t})$$ is uniformly integrable, so $$X_{\nu,t}\to X_{\nu,\infty}$$ in $$L^{1}(\mu^{\pi})$$, not merely $$\mu^{\pi}$$-a.s. This lets us pass the $$t\to\infty$$ limit through the expectation.
- **Uniqueness of measure extension** (Caratheodory / $$\pi$$–$$\lambda$$ theorem): both sides of the identity are finite measures on $$({\mathcal{A}}\times{\mathcal{E}})^{\infty}$$; the finite-history identity (Exercise 10.1) shows they agree on all cylinder events $$A = A_{0} \times ({\mathcal{A}}\times{\mathcal{E}})^{\infty}$$, and cylinders generate the full event $$\sigma$$-algebra, so agreement extends uniquely to every event.

We omit the proof and use this identity freely below.
:::

::::callout {title="Exercise" tone="amber"}
**Exercise 10.3 (Markov inequality for change of measure) [15].** Let $$E$$ be an event of infinite histories. For any $$\varepsilon > 0$$, show that

$$
\mu^{\pi}\big[E \cap \{X_{\nu,\infty}\geq \varepsilon\}\big] ~\leq~ \frac{\nu^{\pi}[E]}{\varepsilon}.
$$

:::callout {title="Hint" tone="neutral" collapse="closed"}

On $$E \cap \{X_{\nu,\infty}\geq \varepsilon\}$$, $$X_{\nu,\infty}\geq \varepsilon$$ pointwise. Take $$\mu^{\pi}$$-expectations and apply Exercise 10.2.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Let $$E_{\varepsilon} := E \cap \{X_{\nu,\infty}\geq \varepsilon\}$$. On $$E_{\varepsilon}$$, $$X_{\nu,\infty}\geq \varepsilon$$, so pointwise

$$
X_{\nu,\infty}\cdot \llbracket {\text{\ae}}_{1:\infty}\in E_{\varepsilon} \rrbracket ~\geq~ \varepsilon \cdot \llbracket {\text{\ae}}_{1:\infty}\in E_{\varepsilon} \rrbracket.
$$

Take $$\mu^{\pi}$$-expectations and apply Exercise 10.2:

$$
\nu^{\pi}[E_{\varepsilon}] ~=~ {\mathbb{E}}_{\mu^\pi}\big[X_{\nu,\infty}\cdot \llbracket {\text{\ae}}_{1:\infty}\in E_{\varepsilon} \rrbracket\big] ~\geq~ \varepsilon \cdot {\mathbb{E}}_{\mu^\pi}\big[\llbracket {\text{\ae}}_{1:\infty}\in E_{\varepsilon} \rrbracket\big] ~=~ \varepsilon \cdot \mu^{\pi}[E_{\varepsilon}].
$$

Since $$E_{\varepsilon} \subseteq E$$, $$\nu^{\pi}[E_{\varepsilon}] \leq \nu^{\pi}[E]$$. Dividing by $$\varepsilon$$ gives $$\mu^{\pi}[E_{\varepsilon}] \leq \nu^{\pi}[E]/\varepsilon$$.

*Interpretation.* A likelihood ratio of at least $$\varepsilon$$ forces $$\nu^{\pi}$$ and $$\mu^{\pi}$$ measures of an event to be comparable: $$\mu^{\pi}$$ of the event can exceed $$\nu^{\pi}$$ of it only by the factor $$1/\varepsilon$$. In particular, if $$\nu^{\pi}$$ vanishes on $$E$$, so does $$\mu^{\pi}$$ on the part where the likelihood ratio stays bounded away from zero.

:::

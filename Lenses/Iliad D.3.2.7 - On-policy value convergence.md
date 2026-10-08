---
id: '07677b18-9575-45d2-897e-cf98136de0b0'
title: "D.3.2.7 On-policy value convergence"
tldr: "Bounds value differences by total variation distance, then proves that the mixture's value for any fixed policy converges to the true environment's value, using Blackwell-Dubins."
summary_for_tutor: "Sections 6 and 7 of Iliad worksheet D.3.2: Bounding expectation differences by total variation, and on-policy value convergence. Definitions 6.1-6.2 (total variation, expectation), 7.1-7.5 (probability of events, covering, almost-sure convergence), Theorem 7.6 and Fact 7.7 (Blackwell-Dubins, stated without proof). Exercises 6.1 (|E_P f - E_Q f| <= c TV), 7.1 (finite-horizon TV bound), 7.2 (xi^pi covers mu^pi), 7.3 (prove Theorem 7.6) and 7.4 (prove Fact 7.7, rated [40]). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - David Quarel (ARENA)
source_url: https://iliad-intensive.org/agency/aixi/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## On-Policy Value Convergence

The following problems prove the first two main results: on-policy value convergence (Section 7), and that AIXI can't be fooled in deterministic environments (Section 8). The path to the self-optimizing property (advanced stretch goal) resumes at Section 9.

\## 6. Bounding Expectation Differences by Total Variation

:::callout {title="Definition" tone="blue"}

**Definition 6.1 (Total variation distance).** The **total variation distance** between probability measures $P$ and $Q$ on a countable set $\Omega$ is ${\mathrm{TV}}[\Omega](P, Q) := \sup_{S \subseteq \Omega}|P(S) - Q(S)|$, where $P(S) := \sum_{\omega \in S}P(\omega)$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 6.2 (Expectation under $P$).** For a probability measure $P$ on a countable set $\Omega$ and a function $f : \Omega \to \mathbb{R}$, the **expectation** of $f$ under $P$ is ${\mathbb{E}}_{P}[f] := \sum_{\omega \in \Omega}f(\omega)\, P(\omega)$.

:::

The following technical lemma is needed for the on-policy value convergence proof.

::::callout {title="Exercise" tone="amber"}
**Exercise 6.1 (∗) [15].** Let $f : \Omega \to [0, c]$. Show that $\big|{\mathbb{E}}_{P}[f] - {\mathbb{E}}_{Q}[f]\big| \leq c \cdot {\mathrm{TV}}[\Omega](P, Q)$.

:::callout {title="Hint" tone="neutral" collapse="closed"}

Define $A^{+} = \{\omega \in \Omega : P(\omega) \geq Q(\omega)\}$ and decompose the expectation difference as a sum over $A^{+}$ and its complement $A^{-} = \Omega \setminus A^{+}$.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Write out the expectation difference using Definition 6.2:

$$
{\mathbb{E}}_{P}[f] - {\mathbb{E}}_{Q}[f] ~=~ \sum_{\omega \in \Omega}f(\omega)\big(P(\omega) - Q(\omega)\big).
$$

Define $A^{+} := \{\omega \in \Omega : P(\omega) \geq Q(\omega)\}$ and $A^{-} := \Omega \setminus A^{+}$, and split the sum:

$$
{\mathbb{E}}_{P}[f] - {\mathbb{E}}_{Q}[f] ~=~ \sum_{\omega \in A^+}f(\omega)\big(P(\omega) - Q(\omega)\big) ~+~ \sum_{\omega \in A^-}f(\omega)\big(P(\omega) - Q(\omega)\big).
$$

*Bounding the sum over $A^{+}$.* On $A^{+}$, $P(\omega) - Q(\omega) \geq 0$ and $f(\omega) \leq c$, so:

$$
\begin{aligned}\sum_{\omega \in A^+}f(\omega)\big(P(\omega) - Q(\omega)\big) ~&\leq~ c \sum_{\omega \in A^+}\big(P(\omega) - Q(\omega)\big) \\ ~&=~ c \cdot \big(P(A^{+}) - Q(A^{+})\big) \\ ~&\leq~ c \cdot \sup_{S} |P(S) - Q(S)| \\ ~&=~ c \cdot {\mathrm{TV}}[\Omega](P, Q).\end{aligned}
$$

*Bounding the sum over $A^{-}$.* On $A^{-}$, $P(\omega) - Q(\omega) < 0$ and $f(\omega) \geq 0$, so every term $f(\omega)(P(\omega) - Q(\omega)) \leq 0$:

$$
\sum_{\omega \in A^-}f(\omega)\big(P(\omega) - Q(\omega)\big) ~\leq~ 0.
$$

*Combining.* ${\mathbb{E}}_{P}[f] - {\mathbb{E}}_{Q}[f] \leq c \cdot {\mathrm{TV}}[\Omega](P,Q) + 0 = c \cdot {\mathrm{TV}}[\Omega](P,Q)$.

*The other direction.* Swapping $P$ and $Q$: define $\tilde{A}^{+} = \{\omega : Q(\omega) \geq P(\omega)\} = A^{-}$. The same argument gives ${\mathbb{E}}_{Q}[f] - {\mathbb{E}}_{P}[f] \leq c \cdot {\mathrm{TV}}[\Omega](Q, P) = c \cdot {\mathrm{TV}}[\Omega](P, Q)$.

Therefore $|{\mathbb{E}}_{P}[f] - {\mathbb{E}}_{Q}[f]| \leq c \cdot {\mathrm{TV}}[\Omega](P, Q)$.

:::

\## 7. On-Policy Value Convergence of Bayes

The following definitions are needed for the on-policy value convergence theorem.

:::callout {title="Definition" tone="blue"}

**Definition 7.1 (Probability of events).** A **finite-length event** is a set $A \subseteq ({\mathcal{A}} \times {\mathcal{E}})^{t}$ of histories of fixed length $t$. Its probability under $\nu^{\pi}$ is

$$
\nu^{\pi}(A) ~:=~ \sum_{{\text{\ae}}_{1:t} \in A}\nu^{\pi}({\text{\ae}}_{1:t}).
$$

An **event on infinite histories** is any set built from finite-length events by countable unions, intersections, and complements.[^3] Probabilities of such events are uniquely determined by two properties:

- **Normalization:** $\nu^{\pi}\!\big(({\mathcal{A}} \times {\mathcal{E}})^{\infty}\big) = 1$.
- **Countable additivity:** if $A_{1}, A_{2}, \ldots$ are pairwise disjoint events, then $\nu^{\pi}\!\big(\bigcup_{n=1}^{\infty} A_{n}\big) = \sum_{n=1}^{\infty} \nu^{\pi}(A_{n})$.

From these, all standard rules of probability can be derived (e.g. $\nu^{\pi}(A \cup B) = \nu^{\pi}(A) + \nu^{\pi}(B) - \nu^{\pi}(A \cap B)$, etc.), though we will not prove them here. Two derived properties we use explicitly:

- **Complement:** $\nu^{\pi}(A^{c}) = 1 - \nu^{\pi}(A)$.
- **Monotone limits:** if $A_{1} \supseteq A_{2} \supseteq \cdots$, then $\nu^{\pi}\!\big(\bigcap_{n=1}^{\infty} A_{n}\big) = \lim_{n \to \infty}\nu^{\pi}(A_{n})$.

Further useful notions:

- **Conditional probability:** The probability of event $A$ given observed history ${\text{\ae}}_{<t}$ is

$$
\nu^{\pi}(A \mid {\text{\ae}}_{<t}) ~:=~ \frac{\nu^{\pi}(\{{\text{\ae}}_{<t}h : h \in A\})}{\nu^{\pi}({\text{\ae}}_{<t})}.
$$

:::

:::callout {title="Tip" tone="green"}

**Example 7.2 (A fair coin shows 1 infinitely often).** Let ${\mathcal{A}} = {\mathcal{O}} = \{0,1\}$, ${\mathcal{R}} = \{0\}$, and let $\nu$ be a fair coin that ignores the action: $\nu(o_{t} = 1 \mid {\text{\ae}}_{<t}\, a_{t}) = \tfrac{1}{2}$ for all ${\text{\ae}}_{<t}, a_{t}$. Consider the event $F := \text{``}o_{t} = 1\text{ for infinitely many }t\text{''}$.

*Step 1: Build $F^{c}$ from finite-prefix events.* For each $t$, the set $\{o_{t} = 0\} := \{{\text{\ae}}_{1:t}: o_{t} = 0\}$ is a finite-length event. For each $N$ and $T \geq N$, the set $D_{N,T}:= \bigcap_{t=N}^{T}\{o_{t} = 0\}$ is also a finite-length event (determined by time $T$). Define $C_{N} := \bigcap_{t=N}^{\infty}\{o_{t} = 0\}$ ("all zeros from time $N$ onwards"): this is an infinite-history event, built as a countable intersection of finite-length events. Then $F^{c} = \bigcup_{N=1}^{\infty} C_{N}$ ("eventually all zeros").

*Step 2: Compute $\nu^{\pi}(C_{N}) = 0$.* Since $D_{N,T}\supseteq D_{N,T+1}\supseteq \cdots$ (adding more constraints), the monotone limit property (for decreasing sets) gives:

$$
\nu^{\pi}(C_{N}) ~=~ \lim_{T \to \infty}\nu^{\pi}(D_{N,T}) ~=~ \lim_{T \to \infty}\left(\tfrac{1}{2}\right)^{T - N + 1}~=~ 0.
$$

(The probability $\nu^{\pi}(D_{N,T}) = (1/2)^{T-N+1}$ is independent of $\pi$, since $\nu$ ignores actions.)

*Step 3:* By countable additivity: $\nu^{\pi}(F^{c}) \leq \sum_{N=1}^{\infty} \nu^{\pi}(C_{N}) = 0$, so $\nu^{\pi}(F) = 1$. A fair coin shows 1 infinitely often, almost surely.

As such, $F^{c}$ (the set of all infinite histories containing only finitely many 1s) is a $\nu^{\pi}$-measure-zero set. Such histories "exist" as infinite sequences, but occur with probability zero.

:::

:::callout {title="Definition" tone="blue"}

**Definition 7.3 (Covering[^4]).** We say $Q$ **covers** $P$ if $Q$ is positive everywhere $P$ is: $P(A) > 0 \implies Q(A) > 0$ for all events $A$. Equivalently: any event that $Q$ rules out, $P$ also rules out. By Section 3, $\xi^{\pi}$ covers $\mu^{\pi}$.

:::

:::callout {title="Definition" tone="blue"}

**Definition 7.4 (Convergence $\nu^{\pi}$-almost surely).** Let $f_{t} : {\mathcal{H}}^{t-1}\to \mathbb{R}$ be a sequence of functions, where $f_{t}$ depends on the history ${\text{\ae}}_{<t}$ of length $t-1$. We write $f_{t}({\text{\ae}}_{<t}) \to 0$ $\nu^{\pi}$**-almost surely** ($\nu^{\pi}$-a.s.) if

$$
\nu^{\pi}\!\Big(\Big\{{\text{\ae}}_{1:\infty}: f_{t}({\text{\ae}}_{<t}) \not\to 0\Big\}\Big) = 0.
$$

This set is built from finite-prefix conditions: $\{f_{t} \not\to 0\} = \bigcup_{n=1}^{\infty} \bigcap_{N=1}^{\infty} \bigcup_{t=N}^{\infty} \big\{|f_{t}({\text{\ae}}_{<t})| > \tfrac{1}{n}\big\}$, so its probability is well-defined (Definition 7.1).

:::

:::callout {title="Tip" tone="green"}

**Example 7.5 (Unpacking "$f_{t}\not\to 0$").** The set $\{f_{t} \not\to 0\}$ looks intimidating, but it reads naturally from the inside out:

- $\big\{|f_{t}({\text{\ae}}_{<t})| > \tfrac{1}{n}\big\}$ is a finite-length event: "at time $t$, the function is at least $\tfrac{1}{n}$ away from zero."
- $\bigcup_{t=N}^{\infty} \big\{|f_{t}| > \tfrac{1}{n}\big\}$: "at *some* time $t \geq N$, $f_{t}$ is at least $\tfrac{1}{n}$ away from zero."
- $\bigcap_{N=1}^{\infty} \bigcup_{t=N}^{\infty} \big\{|f_{t}| > \tfrac{1}{n}\big\}$: "for *every* $N$, there is some $t \geq N$ where $f_{t}$ is at least $\tfrac{1}{n}$ from zero", i.e., $f_{t}$ exceeds $\tfrac{1}{n}$ *infinitely often*.
- $\bigcup_{n=1}^{\infty} \bigcap_{N=1}^{\infty} \bigcup_{t=N}^{\infty} \big\{|f_{t}| > \tfrac{1}{n}\big\}$: "for *some* $\tfrac{1}{n}> 0$, $f_{t}$ exceeds $\tfrac{1}{n}$ infinitely often."

This last condition is exactly $\{f_{t} \not\to 0\}$: convergence $f_{t} \to 0$ means that for *every* $\varepsilon > 0$, $|f_{t}| \leq \varepsilon$ for all sufficiently large $t$. Its negation is that *some* $\varepsilon > 0$ is exceeded infinitely often.

Each layer is a countable union or intersection of the previous, so the whole set is a well-defined event on infinite histories.

:::

The Bayesian agent uses the mixture $\xi$ because the true environment $\mu$ is unknown. A natural question: does planning with $\xi$ eventually become as good as planning with $\mu$? The following theorem says *yes*: the value of any fixed policy $\pi$, as evaluated by $\xi$, converges to the value under the true environment $\mu$, along histories that $\mu^{\pi}$ actually generates.[^5] This tells us that the Bayesian mixture "learns" to predict the true environment's value, on policy.

:::callout {title="Theorem" tone="green"}

**Theorem 7.6 (On-policy value convergence; (Hutter et al. 2024, Theorem 7.3.1)).** For any $\mu \in {\mathcal{M}}$ and any policy $\pi$: $V_{\xi}^{\pi}({\text{\ae}}_{<t}) - V_{\mu}^{\pi}({\text{\ae}}_{<t}) \to 0$ as $t \to \infty$, $\mu^{\pi}$-almost surely. That is, the set of infinite histories along which the value difference does not vanish has $\mu^{\pi}$-probability zero:

$$
\mu^{\pi}\!\Big(\Big\{{\text{\ae}}_{1:\infty}: V_{\xi}^{\pi}({\text{\ae}}_{<t}) - V_{\mu}^{\pi}({\text{\ae}}_{<t}) \not\to 0\Big\}\Big) = 0.
$$

:::

The proof reduces to a finite-horizon TV bound (Exercise 7.1), a covering argument (Exercise 7.2), and the Blackwell–Dubins theorem (Exercise 7.3). The only ingredient we do not prove is Blackwell–Dubins itself, which we state as a given fact.

:::callout {title="Exercise" tone="amber"}
**Exercise 7.1 (Finite-horizon TV bound on value difference) [10].** Using Section 6, show that for finite $m$:

$$
\big|V_{\xi}^{\pi,m}({\text{\ae}}_{<t}) - V_{\mu}^{\pi,m}({\text{\ae}}_{<t})\big| ~\leq~ {\mathrm{TV}}[{\mathcal{H}}^{m-t+1}]\!\big(\xi^{\pi}(\cdot \mid {\text{\ae}}_{<t}),\; \mu^{\pi}(\cdot \mid {\text{\ae}}_{<t})\big),
$$

where ${\mathcal{H}}^{m-t+1}:= ({\mathcal{A}} \times {\mathcal{E}})^{m-t+1}$ is the set of all future history segments ${\text{\ae}}_{t:m}$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We want to apply Section 6. Identify:

- $\Omega := {\mathcal{H}}^{m-t+1}= ({\mathcal{A}} \times {\mathcal{E}})^{m-t+1}$, the finite set of future history segments ${\text{\ae}}_{t:m}$.
- $P := \mu^{\pi}(\cdot \mid {\text{\ae}}_{<t})$ and $Q := \xi^{\pi}(\cdot \mid {\text{\ae}}_{<t})$, the conditional measures over $\Omega$.
- $f({\text{\ae}}_{t:m}) := (1-\gamma)G_{t-1:m}$, which satisfies $f \in [0,1]$ by Exercise 1.3 (so $c = 1$).

Then $V_{\nu}^{\pi,m}({\text{\ae}}_{<t}) = \sum_{{\text{\ae}}_{t:m}}\nu^{\pi}({\text{\ae}}_{t:m}\mid {\text{\ae}}_{<t})\, f({\text{\ae}}_{t:m})$ is exactly ${\mathbb{E}}_{P}[f]$ (for $\nu = \mu$) or ${\mathbb{E}}_{Q}[f]$ (for $\nu = \xi$). Applying Section 6:

$$
\big|V_{\xi}^{\pi,m}({\text{\ae}}_{<t}) - V_{\mu}^{\pi,m}({\text{\ae}}_{<t})\big| ~=~ \big|{\mathbb{E}}_{Q}[f] - {\mathbb{E}}_{P}[f]\big| ~\leq~ 1 \cdot {\mathrm{TV}}[{\mathcal{H}}^{m-t+1}](P, Q).
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 7.2 (Covering) [05].** Show that $\xi^{\pi}$ covers $\mu^{\pi}$ (Definition 7.3).

:::callout {title="Hint" tone="neutral" collapse="closed"}

Use Section 3.

:::
::::

:::callout {title="Solution" tone="neutral" collapse="closed"}

By Section 3, $\xi^{\pi}({\text{\ae}}_{1:m}) \geq w_{\mu} \cdot \mu^{\pi}({\text{\ae}}_{1:m})$ for all histories and all $m$. So for any event $A$: $\mu^{\pi}(A) > 0 \implies \xi^{\pi}(A) \geq w_{\mu} \cdot \mu^{\pi}(A) > 0$. Hence $\xi^{\pi}$ covers $\mu^{\pi}$.

:::

To complete the proof, we need the TV distance on finite segments to vanish $\mu^{\pi}$-a.s. as $t \to \infty$. This follows from the following deep result, which we state without proof:

:::callout {title="Note" tone="blue"}

**Fact 7.7 (Blackwell–Dubins merging of opinions (Blackwell & Dubins 1962)).** If $Q$ covers $P$, then $\sup_{S} |P(S \mid {\text{\ae}}_{<t}) - Q(S \mid {\text{\ae}}_{<t})| \to 0$ $P$-almost surely, where the supremum ranges over all measurable events $S$ (including events on infinite histories).

:::

The proof of Blackwell–Dubins requires the Radon–Nikodym derivative and Levy's martingale convergence theorem: tools from measure theory that are beyond the scope of this sheet. See (Hutter et al. 2024, Chapter 3.9) for discussion.

:::callout {title="Exercise" tone="amber"}
**Exercise 7.3 (On-policy convergence) [15].** Using Fact 7.7, Exercise 7.1 and Exercise 7.2, prove Theorem 7.6.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

*Step 1: Finite-horizon bound.* By Exercise 7.1, for each finite $m$:

$$
\begin{aligned}\big|V_{\xi}^{\pi,m}({\text{\ae}}_{<t}) - V_{\mu}^{\pi,m}({\text{\ae}}_{<t})\big| ~&\leq~ {\mathrm{TV}}[{\mathcal{H}}^{m-t+1}]\!\big(\xi^{\pi}(\cdot \mid {\text{\ae}}_{<t}),\, \mu^{\pi}(\cdot \mid {\text{\ae}}_{<t})\big) \\ ~&\leq~ \sup_{S} \big|\xi^{\pi}(S \mid {\text{\ae}}_{<t}) - \mu^{\pi}(S \mid {\text{\ae}}_{<t})\big|,\end{aligned}
$$

where the second inequality uses that the sup over subsets of ${\mathcal{H}}^{m-t+1}$ is at most the sup over all measurable events.

*Step 2: Take $m \to \infty$.* The LHS converges to $|V_{\xi}^{\pi}({\text{\ae}}_{<t}) - V_{\mu}^{\pi}({\text{\ae}}_{<t})|$ (by definition of the infinite-horizon value as the pointwise limit). The RHS does not depend on $m$. Hence

$$
\big|V_{\xi}^{\pi}({\text{\ae}}_{<t}) - V_{\mu}^{\pi}({\text{\ae}}_{<t})\big| ~\leq~ \sup_{S} \big|\xi^{\pi}(S \mid {\text{\ae}}_{<t}) - \mu^{\pi}(S \mid {\text{\ae}}_{<t})\big|.
$$

*Step 3: Take $t \to \infty$.* By Exercise 7.2, $\xi^{\pi}$ covers $\mu^{\pi}$. By Fact 7.7 (Blackwell–Dubins) with $P = \mu^{\pi}$ and $Q = \xi^{\pi}$, the RHS tends to $0$ as $t \to \infty$, $\mu^{\pi}$-a.s. Therefore

$$
\big|V_{\xi}^{\pi}({\text{\ae}}_{<t}) - V_{\mu}^{\pi}({\text{\ae}}_{<t})\big| ~\to~ 0 \qquad \mu^{\pi}\text{-a.s.}
$$

:::

::::callout {title="Exercise" tone="amber"}
**Exercise 7.4 (∗) [40].** Prove Fact 7.7.

:::callout {title="Hint" tone="neutral" collapse="closed"}

See (Blackwell & Dubins 1962). The proof uses the Radon–Nikodym derivative $dP/dQ$, Levy's martingale convergence theorem, and the Lebesgue decomposition. No elementary proof is known that avoids graduate-level measure theory.

:::
::::

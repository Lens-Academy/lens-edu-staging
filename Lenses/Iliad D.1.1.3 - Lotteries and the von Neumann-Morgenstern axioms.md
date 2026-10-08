---
id: '468897ad-ff7b-4fcf-ac8e-e0c2690b79e3'
title: "D.1.1.3 Lotteries and the von Neumann-Morgenstern axioms"
tldr: "Introduces lotteries over trajectories, the four von Neumann-Morgenstern axioms and the expected utility theorem, with a guided proof and the difference between ordinal and vNM utility."
summary_for_tutor: "This is Section 5 of Iliad worksheet D.1.1 Preferences to Rewards. It defines lotteries, Axioms 1-4 (completeness, transitivity, continuity, independence), Theorem 5.1 (von Neumann-Morgenstern, with affine uniqueness) and its proof, and the distinction between ordinal utility (F1) and vNM utility (F2). It contains Exercise 5.1 (guided proof, parts a-h) and Exercise 5.2 (ordinal versus vNM utility), with collapsed solutions. Keep the notation Delta(X), u, U(mu), b and w for best and worst. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Fernando E. Rosas
source_url: https://iliad-intensive.org/agency/preferences-to-rewards/
upstream_commit: '11944e29333e1e2a2a0c0d93b6398a6df5598ab3'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. Lotteries and the von Neumann–Morgenstern axioms

Up to this point, we have just considered preferences over a countable set ${\mathcal{H}}^{*}$ without considering stochasticity. To introduce uncertainty, we expand the domain from trajectories to lotteries over trajectories.

Let $\Delta(X)$ for $X\subset{\mathcal{H}}^{*}$ denote the set of probability distributions over $X$. An element $\mu\in\Delta(X)$ can be expressed as

$$
\mu = \sum_{i}p_{i} \delta_{x_i},
$$

which should be read as a lottery that yields outcome $x_{i}$ with probability $p_{i}$. The outcome $x$ is identified with the degenerate lottery $\delta_{x}$. In this way, preferences over outcomes can be viewed as a special case of preferences over lotteries. Furthermore, for $\mu,\nu \in \Delta(X)$ and $\lambda \in [0,1]$, write

$$
\lambda \mu + (1-\lambda)\nu
$$

for the compound lottery that first flips a coin with bias $\lambda$, then samples from $\mu$ or $\nu$ accordingly.

The von Neumann–Morgenstern (vNM) framework studies weak preference relations $\succcurlyeq$ over $\Delta(X)$ and asks when such preferences admit an expected-utility representation (von Neumann & Morgenstern 1944). The framework considers four axioms on preferences over lotteries.

:::callout {title="Note" tone="blue"}

**Axiom 1 (Completeness).** For all $\mu,\nu\in\Delta(X)$, either $\mu\succcurlyeq \nu$ or $\nu\succcurlyeq \mu$ (or both).

:::

:::callout {title="Note" tone="blue"}

**Axiom 2 (Transitivity).** For all $\mu,\nu,\xi\in\Delta(X)$, if $\mu\succcurlyeq\nu$ and $\nu\succcurlyeq\xi$, then $\mu\succcurlyeq\xi$.

:::

:::callout {title="Note" tone="blue"}

**Axiom 3 (Continuity).** For all $\mu,\nu,\xi\in\Delta(X)$ with $\mu\succcurlyeq\nu\succcurlyeq\xi$, there exists $\lambda\in[0,1]$ such that

$$
\nu \sim \lambda \mu + (1-\lambda)\xi.
$$

:::

:::callout {title="Note" tone="blue"}

**Axiom 4 (Independence).** For all $\mu,\nu,\xi\in\Delta(X)$ and $\lambda\in(0,1)$,

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad \lambda \mu + (1-\lambda)\xi \succcurlyeq \lambda \nu + (1-\lambda)\xi.
$$

:::

We already know about completeness and transitivity from the previous section; the new players are continuity and independence. Continuity says intermediate prospects admit a break-even mixture between better and worse ones. Independence says that if $\mu$ is preferred to $\nu$, then mixing both with the same background lottery $\xi$ should not reverse that preference.

The natural question is therefore when a preference over lotteries can be represented by the expectation of a utility function on trajectories:

$$
U(\mu)=\sum_{x\in X}\mu(x)u(x).
$$

This formulation says that the value of a lottery is the probability-weighted average of the utilities of its possible trajectories. In its simplest finite-outcome form, this question is answered by the celebrated vNM theorem.

:::callout {title="Theorem" tone="green"}

**Theorem 5.1 (von Neumann–Morgenstern).** Let $X\subseteq {\mathcal{H}}^{*}$ be finite. A weak preference relation $\succcurlyeq$ on $\Delta(X)$ satisfies completeness, transitivity, continuity, and independence if and only if there exists a function $u\colon X\to{\mathbb{R}}$ such that for all lotteries $\mu,\nu\in\Delta(X)$,

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad \sum_{x\in X}\mu(x)u(x)\geq \sum_{x\in X}\nu(x)u(x).
$$

Moreover, $u$ is unique up to positive affine transformations:

$$
u'(x)=a+bu(x), \qquad b>0.
$$

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

We first prove the easy direction: if preferences admit an expected-utility representation, then they satisfy the four axioms.

Completeness and transitivity follow immediately from the total order on ${\mathbb{R}}$. Continuity follows because if $\mu\succcurlyeq\nu\succcurlyeq\xi$ then $U(\mu)\geq U(\nu)\geq U(\xi)$, so one can choose $\lambda\in[0,1]$ such that

$$
U(\nu)=\lambda U(\mu)+(1-\lambda)U(\xi).
$$

Hence

$$
\nu \sim \lambda \mu +(1-\lambda)\xi.
$$

Finally, independence follows from linearity:

$$
U(\lambda \mu +(1-\lambda)\xi) = \lambda U(\mu)+(1-\lambda)U(\xi).
$$

Therefore

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad \lambda \mu +(1-\lambda)\xi \succcurlyeq \lambda \nu +(1-\lambda)\xi.
$$

We now prove the converse direction, namely that the four axioms imply an expected-utility representation.

1. *Pick best and worst outcomes (completeness and transitivity).* Because $X$ is finite and the restriction of $\succcurlyeq$ to degenerate lotteries is complete and transitive, either all outcomes in $X$ are indifferent or there exist $b,w\in X$ such that

$$
b\succcurlyeq x \succcurlyeq w \qquad \text{for all }x\in X.
$$

If all outcomes are indifferent, then the constant utility function already represents the preference relation. So we may assume $b\succ w$.
2. *Calibrate each outcome against $b$ and $w$ (continuity).* For $x=b$ set $u(x)=1$, and for $x=w$ set $u(x)=0$. For $b\succ x \succ w$, continuity gives some $u(x)\in(0,1)$ such that

$$
x \sim u(x)b+\big(1-u(x)\big)w.
$$

Thus every outcome is indifferent to a lottery over the two benchmark outcomes $b$ and $w$.
3. *Compare the benchmark lotteries (independence and transitivity).* We first show that for $x,x'\in X$,

$$
x\succcurlyeq x' \quad\Longleftrightarrow\quad u(x)\geq u(x').
$$

For $\lambda\in[0,1]$, write

$$
C_{\lambda} \coloneqq \lambda b +(1-\lambda)w.
$$

We claim that if $\alpha>\beta$, then $C_{\alpha} \succ C_{\beta}$. Indeed, if $\alpha=1$, then $C_{\alpha}=b$, and independence applied to $b\succ w$ with mixing weight $\beta$ and background lottery $b$ gives

$$
b \succ \beta b +(1-\beta)w = C_{\beta}.
$$

So it remains to consider the case $\alpha<1$. Define

$$
\rho \coloneqq \frac{\alpha-\beta}{1-\beta}\in(0,1).
$$

Since $b\succ w$, independence gives

$$
\rho b +(1-\rho)C_{\beta} \succ \rho w +(1-\rho)C_{\beta}.
$$

But the left-hand side is exactly $C_{\alpha}$, while the right-hand side is $C_{\beta}$. Hence larger values of $\lambda$ yield strictly better benchmark lotteries. Together with Step 2 and transitivity, this proves the displayed equivalence above.
4. *Reduce an arbitrary lottery to a benchmark lottery (independence).* Let

$$
\mu=\sum_{i} p_{i} x_{i}.
$$

By Step 2, each $x_{i}$ is indifferent to $C_{u(x_i)}$. Replacing each $x_{i}$ by the corresponding $C_{u(x_i)}$ inside $\mu$, one at a time, and using independence together with transitivity, yields

$$
\mu \sim \sum_{i} p_{i} C_{u(x_i)}.
$$

By ordinary probability arithmetic, the compound lottery on the right reduces to

$$
\sum_{i} p_{i} C_{u(x_i)}\sim U(\mu)b+(1-U(\mu))w, \qquad U(\mu)\coloneqq \sum_{i} p_{i} u(x_{i}).
$$
5. *Conclude the expected-utility representation.* Applying Step 3 to the benchmark lotteries from Step 4, we obtain

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad U(\mu)\geq U(\nu).
$$

This is exactly the desired expected-utility representation.

It remains to prove affine uniqueness, which uses continuity, independence, and the representation just obtained. Suppose $u'$ is another expected-utility representation of the same preference relation. Let

$$
a\coloneqq u'(w), \qquad c\coloneqq u'(b)-u'(w)>0.
$$

For any $x\in X$, Step 2 gives

$$
x \sim u(x)b+(1-u(x))w.
$$

Since $u'$ also represents the same preferences, indifference implies equality of expected $u'$-value:

$$
u'(x)=u(x)u'(b)+(1-u(x))u'(w)=a+cu(x).
$$

So $u'$ is a positive affine transformation of $u$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.1 (Guided proof of the von Neumann–Morgenstern theorem).** Assume $X\subseteq {\mathcal{H}}^{*}$ is finite and that $\succcurlyeq$ on $\Delta(X)$ satisfies completeness, transitivity, continuity, and independence.

**(a)** Show that there exist trajectories $b,w\in X$ such that $b\succcurlyeq h \succcurlyeq w$ for every $h\in X$.

**(b)** Using continuity, show that for every $h\in X$ there exists $u(h)\in[0,1]$ such that

$$
h \sim u(h)b+(1-u(h))w.
$$

**(c)** Use transitivity to show that if

$$
h \sim u(h)b+(1-u(h))w \quad\text{and}\quad h' \sim u(h')b+(1-u(h'))w,
$$

then

$$
h\succcurlyeq h' \quad\Longleftrightarrow\quad u(h)\geq u(h').
$$

**(d)** Let

$$
\mu=\sum_{i} p_{i} h_{i}.
$$

Use independence repeatedly to replace each $h_{i}$ by the equivalent lottery $u(h_{i})b+(1-u(h_{i}))w$ and show that

$$
\mu \sim \sum_{i} p_{i}\bigl(u(h_{i})b+(1-u(h_{i}))w\bigr).
$$

**(e)** Reduce the compound lottery in part (d) to a simple lottery and prove that

$$
\mu \sim U(\mu)b+(1-U(\mu))w, \qquad U(\mu)\coloneqq \sum_{i} p_{i} u(h_{i}).
$$

**(f)** Show that

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad U(\mu)\geq U(\nu).
$$

This gives the expected-utility representation.

**(g)** Prove affine uniqueness: if $u'$ also represents the same preference relation in expected-utility form, then $u'=a+bu$ for some $a\in{\mathbb{R}}$ and $b>0$.

**(h)** Prove the converse direction: if preferences admit an expected-utility representation, then they satisfy completeness, transitivity, continuity, and independence.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** Induction on $|X|$. A single trajectory is its own best and worst element. Given a maximal $b'$ and minimal $w'$ for $X\setminus\{h\}$, completeness compares $h$ with each of them and transitivity makes the better of $\{h,b'\}$ maximal and the worse of $\{h,w'\}$ minimal for $X$.

**(b)** If $b\sim w$ then every $h$ is indifferent to both and any constant $u$ works. Otherwise $b\succ w$. By (a) we have $b\succcurlyeq h\succcurlyeq w$, so continuity applied to the triple $(b,h,w)$ gives directly some $\lambda\in[0,1]$ with $h\sim \lambda b+(1-\lambda)w$; set $u(h)\coloneqq\lambda$. For uniqueness, independence implies the mixtures $\alpha b+(1-\alpha)w$ are strictly increasing in $\alpha$ when $b\succ w$, so two different weights cannot both be indifferent to $h$.

**(c)** Suppose $u(h)\geq u(h')$. Mixture monotonicity gives $u(h)b+(1-u(h))w \succcurlyeq u(h')b+(1-u(h'))w$, and chaining the two calibrating indifferences through transitivity yields $h\succcurlyeq h'$. If $u(h)<u(h')$ the same argument gives $h'\succ h$. Together: $h\succcurlyeq h'\iff u(h)\geq u(h')$.

**(d)** Independence states that $\mu\sim\nu$ implies $p\mu+(1-p)\lambda \sim p\nu+(1-p)\lambda$. View $\mu$ as a mixture in which $h_{1}$ appears with weight $p_{1}$ against the rest; replacing $h_{1}$ by its calibrated equivalent $u(h_{1})b+(1-u(h_{1}))w$ therefore leaves the whole lottery indifferent. Doing this for each $h_{i}$ in turn — finitely many steps — and chaining with transitivity gives $\mu\sim\sum_{i} p_{i}\bigl(u(h_{i})b+(1-u(h_{i}))w\bigr)$.

**(e)** The right-hand side is a compound lottery whose only outcomes are $b$ and $w$; it awards $b$ with total probability $\sum_{i} p_{i} u(h_{i})=U(\mu)$. Identifying a compound lottery with the simple lottery it induces gives $\mu\sim U(\mu)b+(1-U(\mu))w$.

**(f)** By (e), $\mu$ and $\nu$ are indifferent to calibrated $b$–$w$ mixtures with weights $U(\mu)$ and $U(\nu)$; by mixture monotonicity and transitivity, $\mu\succcurlyeq\nu\iff U(\mu)\geq U(\nu)$.

**(g)** Apply the $u'$-representation to the calibration of $h$:

$$
\begin{aligned}u'(h)&=U'\bigl(u(h)b+(1-u(h))w\bigr)=u(h)\,u'(b)+(1-u(h))\,u'(w) \\&=u'(w)+\bigl(u'(b)-u'(w)\bigr)u(h).\end{aligned}
$$

This is the required form $u'=a+b\,u$, with intercept $u'(w)$ and slope $u'(b)-u'(w)$, the latter strictly positive because $b\succ w$ and $u'$ represents $\succcurlyeq$. (Note the statement's scalars $a,b$ are unrelated to the trajectories $b,w$ of part (a); the letter $b$ does double duty here, so read $u'(b)$ as the utility of the best trajectory throughout.)

**(h)** Let $\mu\succcurlyeq\nu\iff \mathbb{E}_{\mu}[u]\geq\mathbb{E}_{\nu}[u]$. Completeness and transitivity are inherited from the total order on ${\mathbb{R}}$. Continuity: $p\mapsto \mathbb{E}_{p\mu+(1-p)\lambda}[u] =p\,\mathbb{E}_{\mu}[u]+(1-p)\,\mathbb{E}_{\lambda}[u]$ is continuous, so upper and lower contour sets in $p$ are closed. Independence: mixing both sides with $\lambda$ adds the same $(1-p)\mathbb{E}_{\lambda}[u]$ and scales the difference by $p>0$, leaving the comparison unchanged.

:::

In contrast to our previous result, vNM utility is *cardinal* up to positive affine transformations, not merely ordinal. A general monotone transformation would destroy the expectation formula. The independence axiom forces exactly the amount of structure needed for linear averaging.

:::callout {title="Note" tone="blue"}

**Two notions of utility.**

In economics it is standard to distinguish two different notions of utility (Kreps 1988; Mas-Colell et al. 1995).

The first is *ordinal utility*, also known as *preference utility* or `F1', which represents preferences over certain outcomes. This is the object obtained in Proposition 4.3: if preferences over deterministic trajectories are complete and transitive, then there exists a function $u_{\mathrm{ord}}$ such that

$$
h\succcurlyeq h' \quad\Longleftrightarrow\quad u_{\mathrm{ord}}(h)\geq u_{\mathrm{ord}}(h').
$$

Only the ranking matters. Any strictly increasing transformation of $u_{\mathrm{ord}}$ represents the same preferences (Fishburn 1970).

The second is *von Neumann–Morgenstern utility*, also called `F2'. This is the function $u_{\mathrm{vNM}}$ that appears inside the expectation operator when preferences over lotteries satisfy continuity and independence:

$$
\mu\succcurlyeq\nu \quad\Longleftrightarrow\quad \sum_{h} \mu(h)u_{\mathrm{vNM}}(h)\geq \sum_{h} \nu(h)u_{\mathrm{vNM}}(h).
$$

Unlike ordinal utility, $u_{\mathrm{vNM}}$ is unique only up to positive affine transformations. Its numerical differences therefore carry behavioral content: they determine which mixtures an agent is willing to accept, and so encode the agent's attitudes toward risk and gambling structure (von Neumann & Morgenstern 1944; Mas-Colell et al. 1995).

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 5.2 (Ordinal versus vNM utility).** Let $x,y,z\in{\mathcal{H}}^{*}$ satisfy $x\succ y\succ z$.

**(a)** Give two different ordinal utility functions $u_{1},u_{2}\colon{\mathcal{H}}^{*}\to{\mathbb{R}}$ that represent the same ranking of $x,y,z$.

**(b)** Explain why these two functions are equally good as ordinal representations.

**(c)** Suppose in addition that

$$
y \sim \tfrac{1}{2}x + \tfrac{1}{2}z.
$$

Show that not every strictly increasing transformation of a vNM utility can preserve this indifference.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

**(a)** For instance $u_{1}(x,y,z)=(2,1,0)$ and $u_{2}(x,y,z)=(100,5,-3)$.

**(b)** An ordinal representation encodes only the ranking: $u$ represents $\succcurlyeq$ iff $u(h)\geq u(h')\iff h\succcurlyeq h'$, and both functions induce $x\succ y\succ z$. Composing with any strictly increasing map preserves exactly this information, so no ordinal criterion can distinguish $u_{1}$ from $u_{2}$.

**(c)** Under expected utility the indifference forces $u(y)=\tfrac{1}{2}u(x)+\tfrac{1}{2}u(z)$. Take the vNM utility $u(x,y,z)=(1,\tfrac{1}{2},0)$ and the strictly increasing map $f(s)=s^{3}$. Then $(f\circ u)(x,y,z)=(1,\tfrac{1}{8},0)$, while the lottery $\tfrac{1}{2}x+\tfrac{1}{2}z$ has expected value $\tfrac{1}{2}$. Since $\tfrac{1}{8}\neq\tfrac{1}{2}$, the relation represented by $f\circ u$ strictly prefers the lottery to $y$: the indifference is destroyed. Only positive affine transformations preserve all such midpoint identities, which is the uniqueness part of the vNM theorem.

:::

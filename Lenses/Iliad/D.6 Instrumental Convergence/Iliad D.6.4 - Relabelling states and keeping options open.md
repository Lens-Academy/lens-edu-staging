---
id: '50d7337b-dc0c-4a1e-930b-9cfd0b426259'
title: "D.6.4 Relabelling states and keeping options open"
tldr: "Shows how permutations act on rewards and options and preserve quality, then defines what it means for one action to keep at least as many options open as another."
summary_for_tutor: "Final part of section 2 and section 3 of Iliad worksheet D.6 Instrumental Convergence. Contains Definition 2.8 (permutation action) and Exercise 2.3 with collapsed solution (inner products are preserved), Definition 3.1 (options under an action F(s|a)), Definition 3.2 (containment up to relabelling), Definition 3.3 (one-sided dynamics embedding) and Exercise 3.1 with a collapsed hint and solution (an embedding gives phi.F(s|a') contained in F(s|a)). Keep the notation phi, F(s|a), R'. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - "Leon Lang (ILIAD), based on work by Alex Turner et al."
source_url: https://iliad-intensive.org/agency/power-seeking/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### Relabelling states

In Definition 1.1 a permutation relabelled a reward function; the same relabelling acts on options too. We record the action and the one property of it we will need later: it preserves quality.

:::callout {title="Definition" tone="blue"}

**Definition 2.8 (Permutation action).** A permutation $$\phi$$ of the state set $${\mathcal{S}}$$ acts on $${\mathbb{R}}^{d} \cong {\mathbb{R}}^{{\mathcal{S}}}$$ by permuting coordinates: it sends $$x \in {\mathbb{R}}^{d}$$ to the vector $$\phi \cdot x$$ with

$$
(\phi \cdot x)_{s}\coloneqq x_{\phi^{-1}(s)}
$$

and a set of options $$X$$ to

$$
\phi \cdot X \coloneqq \{\, \phi \cdot f : f \in X \,\}.
$$

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 2.3.** Show that the permutation action preserves inner products: for every permutation $$\phi$$ and all $$x, y \in {\mathbb{R}}^{d}$$,

$$
(\phi \cdot x)^{\top} (\phi \cdot y) = x^{\top} y .
$$

In particular, relabelling a reward and an option together leaves the quality unchanged: $$(\phi \cdot f)^{\top} (\phi \cdot r) = f^{\top} r$$.
:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

Writing out the inner product and reindexing the sum by $$s' = \phi^{-1}(s)$$ (a bijection of $${\mathcal{S}}$$):

$$
(\phi \cdot x)^{\top} (\phi \cdot y) = \sum_{s \in {\mathcal{S}}}(\phi \cdot x)_{s}\, (\phi \cdot y)_{s}= \sum_{s \in {\mathcal{S}}}x_{\phi^{-1}(s)}\, y_{\phi^{-1}(s)}= \sum_{s' \in {\mathcal{S}}}x_{s'}\, y_{s'}= x^{\top} y .
$$

:::

\## 3. Keeping options open

We now take up point (3): what it means for one action to keep more options open than another. The options realizable from $$s$$ decompose according to the first action taken.

:::callout {title="Definition" tone="blue"}

**Definition 3.1 (Options under an action).** For an action $$a$$ at $$s$$, the **options under $$a$$** are the visitation distributions realizable from $$s$$ when the first action is $$a$$:

$$
{\mathcal{F}}(s \mid a) \;:=\; \bigl\{\, f^{\pi}(s) : \pi \text{ a policy with }\pi(s) = a \,\bigr\} \ \subseteq\ {\mathcal{F}}(s).
$$

:::

The right comparison is *containment up to relabelling*: $$a$$ is at least as rich as $$a'$$ when every option available after $$a'$$ has a relabelled twin available after $$a$$.

:::callout {title="Definition" tone="blue"}

**Definition 3.2 (Keeping at least as many options open).** $${\mathcal{F}}(s\mid a)$$ **contains a copy of** $${\mathcal{F}}(s\mid a')$$ if $$\phi \cdot {\mathcal{F}}(s\mid a') \subseteq {\mathcal{F}}(s\mid a)$$ for some permutation $$\phi$$ of $${\mathcal{S}}$$. When this holds we say **$$a$$ keeps at least as many options open as $$a'$$ at $$s$$**.

:::

The containment quantifies over all policies, so it is awkward to check directly. It follows from a *one-sided* structural condition on the dynamics: $$\phi$$ need only embed the part of the environment reachable after $$a'$$ into the part reachable after $$a$$, and may leave the $$a$$-branch with extra room.

:::callout {title="Definition" tone="blue"}

**Definition 3.3 (One-sided dynamics embedding).** Let $$R'$$ be the set of states reachable from $$s$$ along a trajectory whose first action is $$a'$$ (so $$s \in R'$$). A permutation $$\phi$$ of $${\mathcal{S}}$$ with $$\phi(s) = s$$ **embeds $$a'$$ into $$a$$ at $$s$$** if

1. $$T(\phi(s'') \mid s, a) = T(s'' \mid s, a')$$ for all $$s''$$; and
2. for every $$s' \in R'$$ with $$s' \ne s$$ and every action $$b$$, there is an action $$b'$$ with $$T(\phi(s'') \mid \phi(s'), b') = T(s'' \mid s', b)$$ for all $$s''$$.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 3.1.** Show that if $$\phi$$ embeds $$a'$$ into $$a$$ at $$s$$, then $$\phi \cdot {\mathcal{F}}(s\mid a') \subseteq {\mathcal{F}}(s\mid a)$$ — so $$a$$ keeps at least as many options open as $$a'$$ at $$s$$.
:::

:::callout {title="Hint" tone="neutral" collapse="closed"}

given a policy $$\pi$$ with $$\pi(s)=a'$$, relabel it into a policy $$\rho$$ with $$\rho(s)=a$$ and $$f^{\rho}(s) = \phi \cdot f^{\pi}(s)$$.

:::

:::callout {title="Solution" tone="neutral" collapse="closed"}

We use two facts: the $$s'$$-th column of the transition matrix is the one-step law $$T^{\pi} e_{s'}= T(\cdot\mid s',\pi(s'))$$ (with $$T^{\pi}$$ linear), and relabelling sends indicators to indicators, $$\phi\cdot e_{s'}= e_{\phi(s')}$$ (with $$\phi\cdot$$ linear).

Fix a policy $$\pi$$ with $$\pi(s) = a'$$, and define a policy $$\rho$$ by $$\rho(s) := a$$ and, for each $$s' \in R'$$ with $$s' \ne s$$, $$\rho(\phi(s')) := b'$$, the action supplied by (ii) for $$b = \pi(s')$$ (arbitrary off $$\phi(R')$$; $$\phi$$ is injective, so this is unambiguous).

*The $$a'$$-dynamics stay in $$R'$$.* If $$v$$ is supported on $$R'$$, so is $$T^{\pi} v$$: from any $$s' \in R'$$ the $$\pi$$-successors are again reachable from $$s$$ via $$a'$$, hence lie in $$R'$$. In particular $$(T^{\pi})^{t} e_{s}$$ is supported on $$R'$$ for every $$t$$.

*Intertwining on $$R'$$.* For every $$s' \in R'$$,

$$
T^{\rho} e_{\phi(s')}= T(\cdot \mid \phi(s'),\, \rho(\phi(s'))) = \phi \cdot T(\cdot\mid s',\, \pi(s')) = \phi\cdot(T^{\pi} e_{s'}),
$$

where for $$s' = s$$ this is (i) (using $$\pi(s)=a'$$ and $$\rho(s)=a$$), and for $$s' \ne s$$ it is (ii) (with $$b = \pi(s')$$). Hence, for $$v$$ supported on $$R'$$,

$$
T^{\rho}(\phi\cdot v) = \sum_{s'\in R'}v_{s'}\, T^{\rho} e_{\phi(s')}= \sum_{s'\in R'}v_{s'}\, \phi\cdot(T^{\pi} e_{s'}) = \phi\cdot(T^{\pi} v).
$$

*Iterating.* By induction $$(T^{\rho})^{t} e_{s} = \phi\cdot(T^{\pi})^{t} e_{s}$$ for every $$t$$: the base case is $$\phi\cdot e_{s} = e_{\phi(s)}= e_{s}$$, and the step applies the intertwining to $$v = (T^{\pi})^{t} e_{s}$$, which is supported on $$R'$$. Summing the discounted series, $$f^{\rho}(s) = \phi\cdot f^{\pi}(s)$$. Since $$\rho(s) = a$$, we have $$f^{\rho}(s) \in {\mathcal{F}}(s\mid a)$$, so $$\phi\cdot f^{\pi}(s) \in {\mathcal{F}}(s\mid a)$$; as $$\pi$$ ranged over all policies with $$\pi(s)=a'$$, this gives $$\phi\cdot{\mathcal{F}}(s\mid a') \subseteq {\mathcal{F}}(s\mid a)$$.

:::

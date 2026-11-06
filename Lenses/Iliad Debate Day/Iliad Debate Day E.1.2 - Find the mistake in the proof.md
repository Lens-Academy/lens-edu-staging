---
id: '4928e75a-9eaa-46f7-897a-daf0cc6c57ff'
title: "E.1.2 Find the mistake in the proof"
tldr: "Five deliberately wrong proofs (horses, pointwise limits, ln 2 = 0, a negative integral, two coins) where you find the flaw, with the answer in a closed box under each proof, as a first taste of judging arguments."
summary_for_tutor: "Section 4 of worksheet E.1: the find-the-mistake game with sections 4.1 to 4.5, from the September handout. The student plays Bob and must locate the error in Alice's proofs: all horses are the same color, pointwise limits of continuous functions, ln(2) = 0 by rearranging the alternating harmonic series, a nonnegative function with integral -2 (integrating 1/x^2 across the singularity at 0), and two fair coins both landing heads with probability 1/8 (pairwise versus joint independence). The point is that convincing proofs can hide mistakes that a judge must find. Each proof has its answer in a closed box under it. The room plays this as a game, so give hints first and do not name the error yourself. If the student asks for the answer, point them to the closed box under the proof."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
---

#### Text
content::
\## 4. Fun Exercise: Find the Mistake in the presented Proof!

\### 4.1 Theorem: All horses are the same color.

**Proof by strong induction on $$n$$, the number of horses.**

**Base case** ($$n = 1$$): A set containing a single horse is trivially monochromatic — there is nothing to differ from.

**Inductive step:** Assume that *any* set of $$n$$ horses is monochromatic (all the same color). We will show that any set of $$n+1$$ horses is also monochromatic.

Consider an arbitrary set of $$n+1$$ horses:

$$
H = \{h_{1}, h_{2}, \ldots, h_{n}, h_{n+1}\}
$$

Partition $$H$$ into two overlapping subsets:

$$
A = \{h_{1}, h_{2}, \ldots, h_{n}\} \qquad B = \{h_{2}, h_{3}, \ldots, h_{n+1}\}
$$

Each of $$A$$ and $$B$$ contains exactly $$n$$ horses. By the inductive hypothesis, all horses in $$A$$ are the same color, and all horses in $$B$$ are the same color.

Now observe that $$A$$ and $$B$$ share the horses $$\{h_{2}, \ldots, h_{n}\}$$ — a non-empty overlap. Since $$h_{2}$$ is in both $$A$$ and $$B$$, it acts as a **color witness**: every horse in $$A$$ shares its color, and every horse in $$B$$ shares its color. Therefore all horses in $$A \cup B = H$$ are the same color.

By induction, all horses in any set of $$n$$ horses are the same color. Since this holds for all $$n$$, all horses are the same color. $$\blacksquare$$

:::callout {title="Why the proof is wrong" tone="neutral" collapse="closed"}

The claim that $$A$$ and $$B$$ have a nonempty overlap fails exactly when $$n = 1$$. To deduce the case of two horses from the base case, the proof takes $$A = \{h_{1}\}$$ and $$B = \{h_{2}\}$$. Both single-horse sets are monochromatic, but they share no horse. In particular, $$h_{2} \notin A$$, so it cannot serve as a color witness. The two horses may have different colors.

For $$n \ge 2$$, the intersection $$A \cap B = \{h_{2}, \ldots, h_{n}\}$$ really is nonempty, and the reasoning within that step works. Induction still fails because there is no valid bridge from $$n = 1$$ to $$n = 2$$. Calling this strong induction does not help: the stronger hypothesis includes only smaller cases, none of which establishes that an arbitrary pair of horses has the same color.

:::

\### 4.2 Theorem: Pointwise limits of continuous functions are continuous.

**Claim.** Let $$f_{1},f_{2},f_{3},\ldots$$ be continuous functions on $$[0,1]$$. Suppose that $$f_{n}(x)\to f(x)$$ for every $$x\in[0,1]$$. Then $$f$$ is continuous.

**Wrong proof.**

Fix $$a\in[0,1]$$. We want to show that $$f$$ is continuous at $$a$$.

Let $$\varepsilon>0$$. Since $$f_{n}(a)\to f(a)$$, there exists $$N$$ such that

$$
|f_{N}(a)-f(a)|<\frac{\varepsilon}{3}.
$$

Since $$f_{N}$$ is continuous at $$a$$, there exists $$\delta>0$$ such that whenever $$|x-a|<\delta$$,

$$
|f_{N}(x)-f_{N}(a)|<\frac{\varepsilon}{3}.
$$

Also, since $$f_{n}(x)\to f(x)$$, we may choose $$N$$ large enough so that

$$
|f_{N}(x)-f(x)|<\frac{\varepsilon}{3}.
$$

Therefore, for $$|x-a|<\delta$$,

$$
\begin{aligned}|f(x)-f(a)|&\le |f(x)-f_{N}(x)|+|f_{N}(x)-f_{N}(a)|+|f_{N}(a)-f(a)| \\&< \frac{\varepsilon}{3}+\frac{\varepsilon}{3}+\frac{\varepsilon}{3}\\&=\varepsilon.\end{aligned}
$$

Thus $$f$$ is continuous at $$a$$. Since $$a$$ was arbitrary, $$f$$ is continuous on $$[0,1]$$. $$\blacksquare$$

:::callout {title="Why the proof is wrong" tone="neutral" collapse="closed"}

The first two estimates choose one index $$N$$ and then a neighborhood of $$a$$. The third estimate must hold for that same $$N$$ at every $$x$$ in that neighborhood. Pointwise convergence only says that, for each fixed $$x$$, sufficiently large indices work; how large may depend on $$x$$. The invalid step exchanges $$\forall x\,\exists N$$ with $$\exists N\,\forall x$$. Choosing a new $$N$$ for each $$x$$ also changes $$f_{N}$$ and potentially the $$\delta$$ obtained from its continuity, so it does not repair the proof.

For a concrete counterexample, take $$f_{n}(x) = x^{n}$$ on $$[0,1]$$. Its pointwise limit is $$f(x) = 0$$ when $$x < 1$$, while $$f(1) = 1$$. At $$a = 1$$, no fixed $$N$$ gives $$|f_{N}(x) - f(x)| < 1/3$$ for every $$x$$ sufficiently close to $$1$$: for $$x < 1$$ close enough to $$1$$, $$x^{N} > 2/3$$ whereas $$f(x) = 0$$. The limit is discontinuous. Uniform convergence would justify the third estimate and hence the proof; uniform control on a neighborhood of each $$a$$ would already suffice.

:::

\### 4.3 Theorem: $$\text{ln}(2) = 0$$

**Claim.** The logarithm of 2 is 0.

**Wrong proof.**

Consider the alternating harmonic series

$$
\ln2 = 1-\frac{1}{2}+\frac{1}{3}-\frac{1}{4}+\frac{1}{5}-\frac{1}{6}+\cdots.
$$

You can rearrange the terms of a convergent series, thus rearrange as:

$$
1-\frac{1}{2}-\frac{1}{4}+\frac{1}{3}-\frac{1}{6}-\frac{1}{8}+\frac{1}{5}-\frac{1}{10}-\frac{1}{12}+\cdots
$$

and regroup as follows

$$
\begin{aligned}&\left(1-\frac{1}{2}\right)-\frac{1}{4} +\left(\frac{1}{3}-\frac{1}{6}\right)-\frac{1}{8} \\ &\quad+\left(\frac{1}{5}-\frac{1}{10}\right)-\frac{1}{12} +\left(\frac{1}{7}-\frac{1}{14}\right)-\frac{1}{16} +\cdots.\end{aligned}
$$

Each parenthesized pair simplifies:

$$
1-\frac{1}{2}=\frac{1}{2},\qquad \frac{1}{3}-\frac{1}{6}=\frac{1}{6},\qquad \frac{1}{5}-\frac{1}{10}=\frac{1}{10},\qquad \frac{1}{7}-\frac{1}{14}=\frac{1}{14}.
$$

So the rearranged series becomes

$$
\frac{1}{2}-\frac{1}{4}+\frac{1}{6}-\frac{1}{8}+\frac{1}{10}-\frac{1}{12}+\frac{1}{14}-\frac{1}{16}+\cdots.
$$

Factoring out $$\frac{1}{2}$$, we get

$$
\frac{1}{2}\left(1-\frac{1}{2}+\frac{1}{3}-\frac{1}{4}+\frac{1}{5}-\frac{1}{6}+\frac{1}{7}-\frac{1}{8}+\cdots\right) = \frac{1}{2}\ln(2)
$$

Therefore

$$
\ln 2=\frac{1}{2}\ln 2.
$$

and we can cocnlude that $$\ln 2 = 0$$. $$\blacksquare$$

:::callout {title="Why the proof is wrong" tone="neutral" collapse="closed"}

The error is the assertion that convergence permits arbitrary rearrangement without changing the sum. This is guaranteed for absolutely convergent series. The alternating harmonic series converges to $$\ln 2$$, but its series of absolute values is the divergent harmonic series, $$\sum_{k\ge 1} 1/k$$. It is therefore only conditionally convergent.

The proposed ordering takes one positive term and then two negative terms, repeatedly. It uses every original term, but the altered balance changes the limit of the partial sums. The displayed regrouping shows that the new series really does sum to $$\frac{1}{2}\ln 2$$. Regrouping consecutive terms of this new convergent series is legitimate. What fails is the preceding equation between its sum and the sum in the original order. Consequently the proof establishes no equation $$\ln 2 = \frac{1}{2}\ln 2$$; it compares two different series with different sums.

:::

\### 4.4 Theorem: A nonnegative function can have a negative integral.

**Claim.** There is a function $$f:[-1,1]\to[0,\infty)$$ such that

$$
\int_{-1}^{1} f(x)\,dx=-2.
$$

**Wrong proof.**

Define

$$
f(x)=\begin{cases}\dfrac{1}{x^{2}}, & x\neq 0,\\[4pt] 0, & x=0.\end{cases}
$$

Clearly $$f(x)\ge 0$$ for every $$x\in[-1,1]$$.

The value of a function at a single point does not affect its integral, so we may calculate using $$1/x^{2}$$. An antiderivative is

$$
F(x)=-\frac{1}{x},\qquad\text{since } F'(x)=\frac{1}{x^{2}}.
$$

By the Fundamental Theorem of Calculus,

$$
\int_{-1}^{1} f(x)\,dx=\left[-\frac{1}{x}\right]_{-1}^{1}=-1-1=-2.
$$

Thus a function that is nonnegative everywhere can have a negative integral. $$\blacksquare$$

:::callout {title="Why the proof is wrong" tone="neutral" collapse="closed"}

The Fundamental Theorem of Calculus does not justify evaluating this antiderivative across $$0$$. The formula $$F(x) = -1/x$$ defines an antiderivative separately on each side of $$0$$, but $$F$$ is undefined there and cannot be extended continuously across it. Also, $$f$$ is unbounded near $$0$$, so it has no ordinary Riemann integral on $$[-1, 1]$$.

To evaluate an improper integral, we must split at the singularity and take the two limits separately. For $$0 < \varepsilon < 1$$,

$$
\int_{-1}^{-\varepsilon}\frac{dx}{x^{2}}=\frac{1}{\varepsilon}-1,\qquad \int_{\varepsilon}^{1}\frac{dx}{x^{2}}=\frac{1}{\varepsilon}-1.
$$

Both quantities tend to $$+\infty$$ as $$\varepsilon \to 0^{+}$$. The improper integral therefore diverges to $$+\infty$$; its value is not $$-2$$.

Assigning $$f(0) = 0$$ does not cure the problem: the divergence comes from arbitrarily large values throughout every neighborhood of $$0$$. Changing a value at one point cannot remove it.

**Moral.** Before applying a theorem, check its hypotheses on the whole interval. A locally correct formula can give a false answer when used across a singularity.

:::

\### 4.5 Theorem: Two fair coins both land heads with probability 1/8.

**Claim.** Toss two independent fair coins. The probability that both land heads is $$1/8$$.

**Wrong proof.**

Let $$A$$ be the event that the first coin lands heads, $$B$$ the event that the second coin lands heads, and $$C$$ the event that the two coins agree. Clearly,

$$
P(A)=P(B)=P(C)=\frac{1}{2}.
$$

The events $$A$$ and $$B$$ are independent because the coin tosses are independent. Moreover, knowing that the first coin landed heads leaves a probability of $$1/2$$ that the coins agree, since the second coin is still fair. Thus $$C$$ is independent of $$A$$. By the same reasoning, $$C$$ is independent of $$B$$.

Since $$C$$ is independent of both $$A$$ and $$B$$, we have

$$
P(C\mid A\cap B)=P(C)=\frac{1}{2}.
$$

Consequently,

$$
P(A\cap B\cap C)=P(A\cap B)\,P(C\mid A\cap B)=\frac{1}{4}\cdot\frac{1}{2}=\frac{1}{8}.
$$

But whenever both coins land heads, they agree, so $$A\cap B\cap C=A\cap B$$. Hence the probability that both coins land heads is $$1/8$$. $$\blacksquare$$

:::callout {title="Why the proof is wrong" tone="neutral" collapse="closed"}

The mistake is inferring that $$C$$ is independent of $$A\cap B$$ from its independence of $$A$$ and of $$B$$ separately. Knowing either coin's result alone leaves the other coin unknown. Knowing both results determines whether they agree. In particular, $$P(C\mid A\cap B) = 1$$, not $$\frac{1}{2}$$.

All four outcomes are equally likely:

| Outcome | $$A$$ occurs | $$B$$ occurs | $$C$$ occurs |
|---|---|---|---|
| HH | yes | yes | yes |
| HT | yes | no | no |
| TH | no | yes | no |
| TT | no | no | yes |

Every pair of these events really is independent: each event has probability $$1/2$$, and each pair occurs together with probability $$1/4$$. But all three occur together exactly on HH, with probability $$1/4$$, rather than the product $$(1/2)^{3} = 1/8$$. Thus the events are pairwise independent but not jointly independent.

**Moral.** Information can emerge only when observations are combined. Independence from each observation separately does not guarantee independence from the information they provide together.

:::

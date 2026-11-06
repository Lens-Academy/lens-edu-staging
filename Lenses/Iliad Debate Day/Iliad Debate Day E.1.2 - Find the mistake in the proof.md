---
id: '4928e75a-9eaa-46f7-897a-daf0cc6c57ff'
title: "E.1.2 Find the mistake in the proof"
tldr: "Five deliberately wrong proofs (horses, pointwise limits, ln 2 = 0, a negative integral, two coins) where you find the flaw, as a first taste of judging arguments."
summary_for_tutor: "Section 4 of worksheet E.1: the find-the-mistake game with sections 4.1 to 4.5, from the September handout. The student plays Bob and must locate the error in Alice's proofs: all horses are the same color, pointwise limits of continuous functions, ln(2) = 0 by rearranging the alternating harmonic series, a nonnegative function with integral -2 (integrating 1/x^2 across the singularity at 0), and two fair coins both landing heads with probability 1/8 (pairwise versus joint independence). The point is that convincing proofs can hide mistakes that a judge must find. The room plays this as a game, so give hints only and do not name the error, even when asked."
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

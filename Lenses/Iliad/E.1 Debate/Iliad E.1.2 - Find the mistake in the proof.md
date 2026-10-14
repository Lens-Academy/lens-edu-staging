---
id: 'dcf64535-27d0-4521-80b0-25a76e449c5f'
title: "E.1.2 Find the mistake in the proof"
tldr: "Five deliberately wrong proofs (horses, pointwise limits, ln 2 = 0, Q versus N, Hilbert spaces) where you find the flaw, as a first taste of judging arguments."
summary_for_tutor: "Section 4 of Iliad worksheet E.1: the 'find the mistake' game with sections 4.1 to 4.5. The student plays Bob and must locate the error in Alice's proofs: all horses are the same color, pointwise limits of continuous functions, ln(2) = 0 by rearranging the alternating harmonic series, Q and N cardinality (false proof and hint, collapsed), and eigenvectors of symmetric operators on a Hilbert space (false proof and hint, collapsed). The point is that convincing proofs can hide mistakes that a judge must find. Let the student look for the error before revealing hints or naming it."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
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

\### 4.4 Theorem: $$\mathbb{Q}$$ and $$\mathbb{N}$$ have the same cardinality

:::callout {title="Deliberately false proof" tone="neutral" collapse="closed"}

Assume for contradiction that there is a bijection

$$
f:\mathbb{Z}\to\mathbb{Q}.
$$

Transport the usual order on $$\mathbb{Z}$$ to an order $$\prec$$ on $$\mathbb{Q}$$ by declaring

$$
p\prec q \quad\Longleftrightarrow\quad f^{-1}(p)<f^{-1}(q).
$$

Then $$(\mathbb{Q},\prec)$$ is order-isomorphic to $$(\mathbb{Z},<)$$. In particular:

- every nonempty subset of $$\mathbb{Q}$$ that is bounded above with respect to $$\prec$$ has a $$\prec$$-maximum if and only if the corresponding statement holds in $$\mathbb{Z}$$;
- every element has an immediate predecessor and successor with respect to $$\prec$$.

Now consider the usual order $$<$$ on $$\mathbb{Q}$$. Since $$\mathbb{Q}$$ is dense and has no endpoints, every nonempty interval

$$
(a,b)\cap\mathbb{Q}
$$

contains infinitely many rationals. Hence no such interval can have a least or greatest element.

But order-theoretic properties are preserved under bijection, so the transported order $$\prec$$ must share these features with the usual order on $$\mathbb{Q}$$. This is impossible, since under $$\prec$$ every element has an immediate predecessor and successor.

Therefore no bijection $$f:\mathbb{Z}\to\mathbb{Q}$$ exists, and so $$|\mathbb{Z}|\neq|\mathbb{Q}|$$.

:::

:::callout {title="Hint" tone="neutral" collapse="closed"}

A bijection of sets preserves cardinality, but which additional structures does it preserve automatically?

:::

\### 4.5 Hilbert Spaces

:::callout {title="Deliberately false proof" tone="neutral" collapse="closed"}

Let $$H$$ be a Hilbert space, and let $$T:H\to H$$ be a symmetric operator, so that

$$
\langle Tx,y\rangle=\langle x,Ty\rangle \qquad \text{for all }x,y\in H.
$$

We show that $$H$$ admits an orthonormal basis consisting of eigenvectors of $$T$$.

Consider the quadratic form

$$
q(x)=\langle Tx,x\rangle
$$

on the unit sphere

$$
S=\{x\in H:\|x\|=1\}.
$$

Since $$q$$ is continuous and $$S$$ is weakly compact in $$H$$, the function $$q$$ attains its maximum at some unit vector $$u\in H$$.

We claim that $$u$$ is an eigenvector of $$T$$. Indeed, let $$v\in H$$ satisfy $$\langle u,v\rangle=0$$, and consider

$$
\varphi(t)=q\!\left(\frac{u+tv}{\|u+tv\|}\right).
$$

Since $$u$$ maximizes $$q$$ on the unit sphere, we must have $$\varphi'(0)=0$$. A straightforward differentiation gives

$$
\varphi'(0)=2\operatorname{Re}\langle Tu,v\rangle.
$$

Hence $$\langle Tu,v\rangle=0$$ for every $$v\perp u$$. Therefore $$Tu$$ lies in $$\operatorname{span}\{u\}$$, so

$$
Tu=\lambda u
$$

for some $$\lambda\in\mathbb{R}$$. Thus $$u$$ is an eigenvector.

Now let

$$
H_{1}=u^{\perp}.
$$

Because $$T$$ is symmetric, $$H_{1}$$ is $$T$$-invariant: if $$x\in H_{1}$$, then

$$
\langle Tx,u\rangle=\langle x,Tu\rangle=\lambda\langle x,u\rangle=0,
$$

so $$Tx\in H_{1}$$.

Restrict $$T$$ to $$H_{1}$$. The restriction is again symmetric, so by the same argument there exists a unit eigenvector $$u_{2}\in H_{1}$$. Continuing inductively, we construct an orthonormal sequence of eigenvectors

$$
u_{1},u_{2},u_{3},\dots
$$

with corresponding invariant orthogonal complements

$$
H_{n+1}=(\operatorname{span}\{u_{1},\dots,u_{n}\})^{\perp}.
$$

Let

$$
M=\overline{\operatorname{span}}\{u_{1},u_{2},\dots\}.
$$

Then $$M$$ is $$T$$-invariant, and so is $$M^{\perp}$$. If $$M^{\perp}\neq\{0\}$$, we may apply the same maximization argument to the restriction $$T|_{M^\perp}$$ and obtain another eigenvector orthogonal to all previous ones, contradicting the maximality of the family $$\{u_{n}\}$$. Hence $$M^{\perp}=\{0\}$$, so

$$
H=\overline{\operatorname{span}}\{u_{1},u_{2},\dots\}.
$$

Therefore $$\{u_{n}\}$$ is an orthonormal basis of $$H$$ consisting of eigenvectors of $$T$$.

:::

:::callout {title="Hint" tone="neutral" collapse="closed"}

Look very carefully at the step where the quadratic form

$$
q(x)=\langle Tx,x\rangle
$$

is asserted to attain its maximum on the unit sphere. What topology is being used, and is $$q$$ actually continuous for that topology?

:::

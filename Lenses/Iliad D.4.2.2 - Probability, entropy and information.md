---
id: 'c5a389da-5035-44ef-b35f-c1602945fa2d'
title: "D.4.2.2 Probability, entropy and information"
tldr: "The information theory used later: random variables and notation, Shannon entropy, the coding interpretation, conditional entropy, mutual information, KL divergence and the log-sum inequality."
summary_for_tutor: "Section 2 (2.1-2.5) of Iliad worksheet D.4.2. Definitions: Shannon entropy H(X) (Def. 2.1), Shannon codelength Ĥ(x, μ) = log 1/μ(x) (Def. 2.4), conditional entropy (2.5), mutual information I(X;Y) (2.6), KL divergence D(μ || ν) (2.8), with Examples 2.2, 2.3, 2.7 and Lemma 2.9 (log-sum inequality) with a proof. Keep the notation H, Ĥ, I, D. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 2. Theoretical foundations: probability, entropy, and information

This section develops the probabilistic and information-theoretic apparatus on which the remainder of these notes relies. Readers already acquainted with Shannon entropy and mutual information may treat this section as reference material; however, we draw attention to the two components on which the later development relies most heavily: the coding interpretation of Section 2.3, which recurs throughout these notes, and the log-sum inequality (Lemma 2.9), which underpins our proof of the second law.

\### 2.1 Random variables and notation

Throughout, capital letters $$X, Y, Z$$ denote random variables taking values in countable (finite or countably infinite) sets, and lowercase letters $$x, y, z$$ denote particular values. We write $$\mu(x)$$ for the probability that $$X = x$$ when the distribution is called $$\mu$$, and we refer interchangeably to "the distribution of $$X$$" or "the ensemble" when speaking of $$\mu$$. A joint random variable $$(X, Y)$$ has a joint distribution, and the conditional probability of $$y$$ given $$x$$ is written $$P(y \mid x)$$. All logarithms in these notes are base 2, so that information is measured in bits; the natural-log versions of every formula differ only by a factor of $$\ln 2$$.

\### 2.2 Entropy

With this notation in place, we begin by introducing the central quantity of information theory, which measures the uncertainty associated with a random variable.

:::callout {title="Definition" tone="blue"}

**Definition 2.1 (Shannon Entropy).** The *Shannon entropy* of a random variable $$X$$ with distribution $$\mu$$ is

$$
H(X) \;:=\; \sum_{x}\mu(x) \log \frac{1}{\mu(x)},
$$

with the convention that terms with $$\mu(x) = 0$$ contribute zero. We also write $$H(\mu)$$ for the same quantity when we wish to emphasize the distribution rather than the variable.

:::

Entropy quantifies uncertainty, namely the amount that an observer does not yet know about the value of $$X$$ before observing it. We present several examples to calibrate the scale.

:::callout {title="Tip" tone="green"}

**Example 2.2 (Calibration of the Entropy Scale).** A fair coin has entropy $$\frac{1}{2}\log 2 + \frac{1}{2}\log 2 = 1$$ bit, while a deterministic variable (one whose value is certain) has entropy $$0$$ bits. A uniform distribution over all binary strings of length $$n$$ has entropy $$n$$ bits, and $$n$$ bits is the maximum possible entropy for a variable with $$2^{n}$$ possible values, reflecting the fact that uniform distributions are the most uncertain ones. A *biased* coin that lands heads with probability $$p$$ has entropy $$h(p) := p \log \frac{1}{p}+ (1-p)\log\frac{1}{1-p}$$, and two values of this function play a role in later sections of these notes: $$h(0.2) \approx 0.72$$ bits and $$h(0.1) \approx 0.47$$ bits. A coin biased toward one outcome is more predictable than a fair coin and consequently carries less than one bit of uncertainty.

:::

\### 2.3 The coding interpretation

Of the available interpretations of entropy, the one on which we rely most heavily is entropy as data compression. Suppose that the value of $$X$$ must be transmitted to a colleague in binary, and that the objective is to minimize the average number of bits sent. The governing principle is to assign short codewords to the likely values and long codewords to the unlikely values, thereby reducing the expected description length by exploiting the structure of the distribution. Shannon's source coding theorem renders this principle precise: there exists a code (a prefix-free assignment of binary strings to outcomes) whose codeword for outcome $$x$$ has length essentially $$\log \frac{1}{\mu(x)}$$ bits, and no code can achieve a smaller average length than the entropy. Consequently,

$$
\begin{gathered}H(X) \;=\; \text{the minimum average number of bits}\\ \text{needed to describe a sample of }X .\end{gathered}
$$

:::callout {title="Tip" tone="green"}

**Example 2.3 (A Small Optimal Code).** Let $$X$$ take four values with probabilities $$\frac{1}{2}, \frac{1}{4}, \frac{1}{8}, \frac{1}{8}$$, and assign the codewords $$\mathtt{0}$$, $$\mathtt{10}$$, $$\mathtt{110}$$, $$\mathtt{111}$$. Each codeword for an outcome of probability $$2^{-\ell}$$ has length exactly $$\ell = \log \frac{1}{\mu(x)}$$, and the average length is $$\frac{1}{2}\cdot 1 + \frac{1}{4}\cdot 2 + \frac{1}{8}\cdot 3 + \frac{1}{8}\cdot 3 = 1.75$$ bits, which equals $$H(X)$$ exactly, confirming that the entropy is attained by a code whose codeword lengths match the ideal lengths $$\log \frac{1}{\mu(x)}$$.

:::

We now assign a name to the quantity inside this expectation, since the central argument of Section 6 turns on the distinction between the individual quantity and its average.

:::callout {title="Definition" tone="blue"}

**Definition 2.4 (Shannon Codelength, Also Called Stochastic Entropy or Surprisal).** For an individual outcome $$x$$ under distribution $$\mu$$, the *Shannon codelength* is

$$
\hat H(x, \mu) \;:=\; \log \frac{1}{\mu(x)}.
$$

This quantity is the length of the codeword assigned to $$x$$ under the code optimized for $$\mu$$, and the entropy is its mean: $$H(\mu) = \left\langle \hat H(X,\mu) \right\rangle_{X \sim \mu}$$.

:::

We emphasize the dependency structure of this definition. The codelength $$\hat H(x, \mu)$$ is a property of the *pair* consisting of an outcome and a distribution—the same physical outcome $$x$$ receives a short codelength under a distribution that anticipated it and a long codelength under a distribution that did not. At this stage, no notion of "the entropy of an individual outcome $$x$$" exists on its own, in the absence of a distribution against which the outcome is read. This observation becomes the crux of Section 6.

\### 2.4 Joint and conditional entropy, and mutual information

Having interpreted entropy as an optimal description length, we now extend these notions to pairs of random variables, characterizing both the uncertainty that remains in one variable once another is known and the information that the two variables share.

:::callout {title="Definition" tone="blue"}

**Definition 2.5 (Conditional Entropy).** For jointly distributed $$X, Y$$, the *conditional entropy* of $$X$$ given $$Y$$ is

$$
H(X \mid Y) \;:=\; H(X, Y) - H(Y),
$$

where $$H(X,Y)$$ is the entropy of the pair. Equivalently, $$H(X \mid Y)$$ is the average, taken over values $$y$$, of the entropy of the conditional distribution of $$X$$ given $$Y = y$$; it measures the uncertainty about $$X$$ that remains once $$Y$$ is known.

:::

The rearranged identity $$H(X,Y) = H(Y) + H(X \mid Y)$$ is called the *chain rule*, and it admits a transparent coding interpretation: to describe the pair, one first describes $$Y$$ at an average cost of $$H(Y)$$ bits, and then describes $$X$$ using a code adapted to the known value of $$Y$$ at an average cost of $$H(X \mid Y)$$ bits.

:::callout {title="Definition" tone="blue"}

**Definition 2.6 (Mutual Information).** The *mutual information* between $$X$$ and $$Y$$ is

$$
\begin{aligned}I(X;Y) \;&:=\; H(X) + H(Y) - H(X,Y)\\ \;&=\; H(X) - H(X \mid Y) \;=\; H(Y) - H(Y \mid X).\end{aligned}
$$

:::

Mutual information is the average number of bits that knowledge of $$Y$$ saves in describing $$X$$; by the symmetry of the definition, it is equally the number of bits that knowledge of $$X$$ saves in describing $$Y$$. It vanishes exactly when $$X$$ and $$Y$$ are independent, and it is never negative, a fact we prove below. Mutual information serves as the standard measure of "how much one part of the world knows about another", an informal phrase that recurs many times in these notes.

:::callout {title="Tip" tone="green"}

**Example 2.7 (Calibration of Mutual Information).** Let $$X = (B_{1}, B_{2})$$ consist of two independent fair bits, and let $$Y = B_{1}$$ be the first of them. Then $$H(X) = 2$$, and once $$Y$$ is known only the second bit remains uncertain, so that $$H(X \mid Y) = 1$$ and $$I(X;Y) = 1$$ bit: $$Y$$ contains exactly one bit of information about $$X$$. If instead $$Y$$ were an independent coin flip, $$I(X;Y)$$ would equal $$0$$; if $$Y$$ were a full copy of $$X$$, $$I(X;Y)$$ would equal $$2$$ bits, the whole entropy of $$X$$, confirming that in this example the mutual information varies from zero under independence to the full entropy of $$X$$ when $$Y$$ determines $$X$$.

:::

\### 2.5 Divergence and two fundamental inequalities

Having quantified the information shared between two variables, we now introduce a measure of the discrepancy between two distributions, from which the inequalities underlying our subsequent analysis follow.

:::callout {title="Definition" tone="blue"}

**Definition 2.8 (Kullback–Leibler Divergence).** For two distributions $$\mu, \nu$$ on the same countable set,

$$
D(\mu \,\|\, \nu) \;:=\; \sum_{x} \mu(x) \log \frac{\mu(x)}{\nu(x)}.
$$

:::

In coding terms, $$D(\mu \| \nu)$$ quantifies the cost of holding a mistaken model of the source: if the true distribution is $$\mu$$ but compression is performed with the code optimized for $$\nu$$, the average expenditure is $$H(\mu) + D(\mu\|\nu)$$ bits rather than $$H(\mu)$$. The definition remains meaningful, and we will make use of it, even when the reference $$\nu$$ is an unnormalized nonnegative measure rather than a probability distribution.

Both of the inequalities required for our analysis follow from a single elementary property of the convex function $$t \mapsto t \log t$$.

:::callout {title="Theorem" tone="green"}

**Lemma 2.9 (Log-Sum Inequality).** Let $$a_{1}, a_{2}, \dots$$ and $$b_{1}, b_{2}, \dots$$ be nonnegative reals with finite sums $$a := \sum_{i} a_{i}$$ and $$b := \sum_{i} b_{i} > 0$$. Then

$$
\sum_{i} a_{i} \log \frac{a_{i}}{b_{i}}\;\ge\; a \log \frac{a}{b},
$$

with the conventions $$0 \log \frac{0}{b}= 0$$ and $$a \log \frac{a}{0}= +\infty$$ for $$a > 0$$.

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

The function $$\varphi(t) = t \log t$$ is convex on $$[0, \infty)$$. We apply Jensen's inequality (which states that for convex $$\varphi$$, the average of $$\varphi$$ is at least $$\varphi$$ of the average) with weights $$w_{i} = b_{i} / b$$ and points $$t_{i} = a_{i} / b_{i}$$:

$$
\sum_{i} \frac{b_{i}}{b}\, \varphi\!\Big(\frac{a_{i}}{b_{i}}\Big) \;\ge\; \varphi\!\Big(\sum_{i} \frac{b_{i}}{b}\cdot \frac{a_{i}}{b_{i}}\Big) \;=\; \varphi\!\Big(\frac{a}{b}\Big).
$$

Multiplying both sides by $$b$$ and simplifying $$b_{i} \cdot \frac{a_{i}}{b_{i}}\log\frac{a_{i}}{b_{i}}= a_{i} \log \frac{a_{i}}{b_{i}}$$ yields the claim.

:::

Taking the $$a_{i}$$ and $$b_{i}$$ to be the probabilities of two distributions (so that $$a = b = 1$$) yields *Gibbs' inequality*: $$D(\mu \| \nu) \ge 0$$, with equality only when $$\mu = \nu$$. Nonnegativity of mutual information follows because $$I(X;Y) = D\big(\text{joint distribution}\,\|\, \text{product of marginals}\big) \ge 0$$. The second consequence, which we prove at its point of use in Section 4, is the *data processing inequality* for divergence: passing two distributions through the same noisy channel can only bring them closer together.

Having established these information-theoretic foundations, we now turn to the principal subject of these notes.

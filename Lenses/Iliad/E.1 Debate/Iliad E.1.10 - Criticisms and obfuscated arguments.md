---
id: 'fbf1aa5b-8cd0-4e4d-a497-0af75deb58a5'
title: "E.1.10 Criticisms and obfuscated arguments"
tldr: "Standard criticisms of debate, then obfuscated arguments, where a false claim is split into subclaims with a hidden error, shown with a prime-checking example."
summary_for_tutor: "Sections 16 and 17 of Iliad worksheet E.1: a list of criticisms of AI safety via debate (obfuscated arguments, judges running code, no exploration guarantees, collusion, imperfect judges), Definition 17.1 (obfuscation in naive recursive debate), Example 17.2 (prime-checking with n = 221 and intervals I_1 to I_4), and Exercise 17.1 (decompose any statement into an obfuscated argument, with hint). Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 16. Criticisms: The Debate around "Debate"

A series of criticisms and caveats have been leveled at the whole idea of AI safety via debate. The following list are the ones which are accepted and actively worked on by debate researchers.

- The most important is **Obfuscated Arguments**, raised by Beth Barnes. This refers to the fact that for computationally bounded provers, a viable strategy for a malicious prover is to "decompose" a false argument into a series of arguments, where most are correct but a small number is false and it is computationally hard to find out which are false. A common example is the claim "N is a prime number" which can be easily refuted by stochastic primality testing. But if Alice partitions this into subclaims \{"N has no prime factor in the interval I_1", N has no prime factor in the interval I_2", ...\} where the intervals cover the numbers from 2 to sqrt(N), then it is computationally hard to find out which of these subclaims is wrong, even though Bob knows at least one has to be. It is much harder to find out where the prime factors are than to assert that at least two exist.
- The best strategy for a prover to win might be to get the human judge to run code as part of an experiment to settle the argument that would then have malicious consequences and force the human judge to reward the dishonest debater.
- The training setup for debate has no exploration guarantees that ensure that an existing successful strategy will even be found by the provers.
- The provers might collude against the human overseers. While this is disincentivised on an agent level by the setup, since an honest prover can maximise their reward with an honest strategy, it might nevertheless occur and be stable during training, because there isn't enough exploration of strategies.
- The judges are not perfect and have biases that can be exploited by a malicious prover.

\## 17. Obfuscation

One problem that arises when the provers Alice and Bob are restricted in their computational power is *Obfuscated Arguments*.

:::callout {title="Definition" tone="blue"}

**Definition 17.1 (Obfuscation in naive recursive debate).** An argument is *obfuscated* if a dishonest debater can decompose a top-level claim into subclaims $$q_{1},\dots,q_{m}$$ with claimed answers $$a_{1},\dots,a_{m}$$ such that:

1. the overall argument is false,
2. only a small number of the claimed answers $$a_{i}$$ are false (in the paper's idealized model, exactly one),
3. but it is computationally intractable for the debaters to determine which subclaim is false.

:::

:::callout {title="Tip" tone="green"}

**Example 17.2 (Prime-checking as obfuscation).** Suppose Alice claims that a number $$n$$ is prime, while it is in fact composite. This is easy to disprove through primality testing. But Alice partitions the interval of possible divisors

$$
D_{n} = [2,\lfloor \sqrt{n}\rfloor]
$$

into subintervals $$I_{1},\dots,I_{m}$$, and asserts for each $$k$$ that $$I_{k}$$ contains no divisor of $$n$$.

Her overall argument is false, because at least one interval contains a factor. But all the other subclaims can be true, and Bob can only refute Alice by identifying the unique bad interval. If locating that interval is computationally intractable, then the falsehood is effectively hidden inside an otherwise correct decomposition.

For example, if $$n=221$$, then $$D_{221}=\{2,\dots,14\}$$, and we may choose

$$
I_{1}=\{2,3,4\},\quad I_{2}=\{5,6,7\},\quad I_{3}=\{8,9,10\},\quad I_{4}=\{11,12,13,14\}.
$$

A dishonest debater Alice argues:

$$
\forall k\in\{1,\dots,m\},\quad \text{``there is no divisor of $n$ in $I_{k}$.''}
$$

From this she concludes that $$n$$ has no nontrivial divisor, and hence is prime.

If $$n$$ is composite, then at least one of these subclaims must be false. In the case $$n=221$$, the first three subclaims are true, but the fourth is false because

$$
13 \in I_{4} \qquad\text{and}\qquad 13 \mid 221.
$$

So Alice's overall argument is false, but the error is localized to a single interval. If there are many such intervals and locating the bad one is computationally difficult, then Alice's argument is an example of an obfuscated argument.

:::

:::callout {title="Exercise" tone="amber"}
**Exercise 17.1.** Show that you can decompose any statement into an obfuscated argument. Hint: Re-use the hardness of a problem like prime-factorisation, as well as the concept of vacuous truth, or truth by false premise, i.e., that $$A\rightarrow B$$ is true, whenever $$A$$ is false.
:::

---
title: "A computational no-coincidence principle"
author:
  - "Eric Neyman"
source_url: "https://www.lesswrong.com/posts/Xt9r4SNNuYxW83tmo/a-computational-no-coincidence-principle"
published: 2025-02-14
created: 2026-10-08
accessed: 2026-10-08
llm-review:
  date: 2026-10-08
  model: "sonnet"
  version: "article-qc-v1.4"
  source:
    fetched: 2026-10-08
    kind: "live"
description: "This post presents a conjecture formulated at the Alignment Research Center in 2023. Our belief in the conjecture is at least partly load-bearing for…"
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

_This post presents a conjecture formulated at the_ [_Alignment Research Center_](https://www.alignment.org/theory/) _in 2023. Our belief in the conjecture is at least partly load-bearing for our belief in ARC's overall agenda. We haven't directly worked on the conjecture for a while now, but we believe the conjecture is interesting in its own right._

In a [recent paper](https://mxphi.com/wp-content/uploads/2023/04/MxPhi-Gowers2023.pdf) in _Annals of Mathematics and Philosophy,_ Fields medalist Timothy Gowers asks why mathematicians sometimes believe that unproved statements are likely to be true. For example, it is unknown whether $\pi$  is a normal number (which, roughly speaking, means that every digit appears in $\pi$ with equal frequency), yet this is widely believed. Gowers proposes that there is no sign of any _reason_ for $\pi$ to be non-normal -- especially not one that would fail to reveal itself in the first million digits -- and in the absence of any such reason, any deviation from normality would be an outrageous coincidence. Thus, the likely normality of $\pi$ is inferred from the following general principle:

**No-coincidence principle** (Gowers): _If an apparently outrageous coincidence happens in mathematics, then there is a reason for it._

In other words: suppose that the digit 3 accounts for not 10% but 11% of digits in the decimal expansion of $\pi$ . Intuitively, there ought to be an explanation of this fact: maybe not a proof, but _something_ that someone could say to me that would make me say, "Oh, I get it now, it makes sense that 3 appears more than 10% of the time in $\pi$".

(For an apparently outrageous coincidence that turns out to be true, check out [Chebyshev's bias](https://en.wikipedia.org/wiki/Chebyshev's_bias): in a sense, primes that are 3 mod 4 are more common than primes that are 1 mod 4. As expected by Gowers' no-coincidence principle, we have a [heuristic understanding](https://terrytao.wordpress.com/2016/03/14/biases-between-consecutive-primes/) for why this should be true. However, we only have a [proof](https://projecteuclid.org/journals/experimental-mathematics/volume-3/issue-3/Chebyshevs-bias/em/1048515870.pdf) conditioned on strong forms of the Riemann hypothesis.)

The no-coincidence principle is profound, but also informal. The purpose of this post is to propose a formalization, so that we can at least ask whether or not it's true. In this post, I will:

-   State ARC's _computational no-coincidence conjecture,_ which is our best attempt at formalizing Gowers' no-coincidence principle (in a restricted setting).
-   Explain how we came up with the statement: why this one, and not a different one.
-   Explain why I think theoretical computer scientists should find our conjecture compelling.
-   Explain why we care about the conjecture.

## Our no-coincidence conjecture ^our-no-coincidence-conjecture

Here is our best attempt to capture the spirit of Gowers' no-coincidence principle in a formal mathematical statement:

**Computational no-coincidence conjecture:** _For a reversible_[^note-1] _circuit_ $C: \{0,1\}^{3n} \to \{0,1\}^{3n}$_, let_ $P(C)$ _be the property that there is no input_ $x$ _to_ $C$ _that ends in_ $n$ _zeros, such that_ $C(x)$ _also ends in_ $n$ _zeros. There exists a polynomial-time verification algorithm V that receives as input:_

-   _A reversible circuit_ $C: \{0,1\}^{3n} \to \{0,1\}^{3n}$
-   _An advice string_ $\pi$

_such that:_

-   _For all_ $C$ such that $P(C)$ _is true, there exists_ $\pi$ _with length polynomial_[^note-2] _in the size of_ $C$_, such that_ $V(C, \pi)=1$.
-   _For 99% of random_[^note-3] _reversible circuits_ $C$_, no such_ $\pi$ _exists._

Here, $P(C)$ plays the role of the "apparently outrageous coincidence". To see why it's so outrageous, let's do some math.

It is conjectured that random depth-$\tilde{O}(n)$ reversible circuits are pseudorandom permutations (see e.g. page 5 [here](https://arxiv.org/pdf/2502.07159)), so let's model a random reversible circuit as an _actually_ random permutation of $\{0,1\}^{3n}$. There are $2^{2n}$ inputs $x$ that end in $n$ zeros, and for each of these, the probability that $C(x)$ ends in $n$ zeros is $2^{-n}$ (approximately independently). So the probability that _none_ of these $2^{2n}$ inputs are mapped to an input that ends in $n$ zeros is roughly

$$
(1-2^{-n})^{2^{2n}} \approx e^{-2^n}.
$$

Now, obviously the _actual_ probability that a randomly chosen reversible circuit satisfies $P$ is much higher than that (there are only exponentially many polynomial-size circuits, and e.g. the circuit $C(x)=\overline{x}$ that negates all bits satisfies $P$). This discrepancy comes from our choice to model random reversible circuits as truly random permutations.

However, the fact that a random circuit is so unlikely to satisfy $P$ "by chance" suggests that any circuit that _does_ satisfy $P$ has some kind of _special structure_ that explains "why" it satisfies $P$. (For example, the aforementioned circuit $C(x)=\overline{x}$, implemented as $3n$ parallel NOT gates, has a very clear structure.) In this context, our no-coincidence conjecture states: such structure can be expressed in a polynomial-length advice string.[^note-4]

In other words, we believe that there is a "formal language" for expressing different kinds of structure that can give rise to circuits that satisfy $P$.[^note-5] All circuits that satisfy $P$ have some such structure, while most random circuits have no such structure.[^note-6]

## How we came up with the statement ^how-we-came-up

Gowers' no-coincidence principle speaks of "apparently outrageous coincidences". We wanted some simple yet expansive domain in which we could speak of outrageous coincidences, and boolean circuits were a natural one.[^note-7] Our first attempt at formalization was to consider the family of circuits $C:\{0,1\}^n \to \{0,1\}$ and to let the "outrageous coincidence" be the property $P(C)$ be that $C$ outputs 1 on every input.

The resulting no-coincidence conjecture was then: _There exists a polynomial-time verification algorithm V that receives as input a boolean circuit_ $C: \{0,1\}^n \to \{0,1\}$ _and an advice string_ $\pi$_, such that for any_ $C$ _that always outputs 1, there is a polynomial-length_ $\pi$ _such that_ $V(C, \pi) = 1$_, but for 99% of random circuits, no such_ $\pi$ _exists._

Unfortunately, this statement was uncompelling for two reasons:

-   Random circuits (unlike random reversible circuits) do not behave like random functions. In fact, some of the most natural distributions of random circuits (e.g. sufficiently deep layered circuits) mostly consist of circuits that are equivalent to the constant-0 or constant-1 function (and so the "always outputs 1" property is not surprising at all).
-   Even if we managed to avoid the above problem with a clever choice of distribution, a verifier $V$ could succeed by running $C$ on a small number of random (or pseudorandom) inputs, and outputting $1$ if $C$ returned 1 every time. $V$ doesn't even need an advice string!

Our next attempt was to consider the family of circuits $C: \{0,1\}^{2n} \to \{0, 1\}^n$ and the property $P(C)$ that $C$ never outputs the all-zeros string. (On a naive analysis, this is unlikely to happen "by chance", since there are way more inputs than possible outputs.) This modification resolved the second issue (even if $C$ outputs the all-zeros string on some inputs, _finding_ any such input by sampling may be infeasible.) However, the first issue remained.

To the best of our knowledge, the "reversible circuits" formulation above (which is similar in spirit to the previous formulation but inherits the [nice properties](https://arxiv.org/abs/2502.07159) of random reversible circuits) resolves the first issue as well.

Ultimately, though, we are not wedded to our particular formulation. Perhaps there is some clever sampling-based verifier that "trivializes" our conjecture as well, in which case we would want to revise it. We are ultimately interested in the informal claim that if a circuit exhibits a very surprising property, it is possible to point out some internal structure of the circuit that will "explain" to a verifier why the surprising property holds.

## Thoughts for theoretical computer scientists ^thoughts-for-theoretical-computer

I think that complexity theorists ought to find our conjecture really compelling and deep. This is for a few reasons:

-   In a sense, our conjecture is a (much) weaker version of NP = coNP. Concretely, it is coNP-hard to determine if $P(C)$ is true for a reversible circuit $C$.[^note-8] Thus, if 99% were changed to 100% in the statement of the conjecture, the resulting statement would be equivalent to NP = coNP. We think that our weakening is natural and -- to our knowledge -- new.
-   If the conjecture is true and $V$ is one such verifier, then $V$ is a really interesting object that is somewhat analogous to a proof verifier. Essentially, $V$ is a verifier for "heuristic arguments" about the plausibility of $P(C)$, and the $\pi$ that causes $V$ to accept is a heuristic argument, written in some formal language that $V$ interprets. Thus, finding a $V$ that makes the conjecture true would be a step toward formalizing heuristic arguments (see more in our earlier work, [Formalizing the presumption of independence](https://arxiv.org/abs/2211.06738)).[^note-9]
-   While our conjecture statement is reminiscent of many complexity-theoretic conjectures,[^note-10] our reason for believing it is quite different from the reasons why computer scientists generally believe complexity-theoretic conjectures. It rests on an intuition similar to the one that underpins Gowers' no-coincidence principle. Concretely: if a fact about a circuit is too unlikely to be true simply "by chance", then there ought to be an explanation involving the internal structure of the circuit that explains the fact. The conjecture thus leverages complexity theory to bring a new perspective to an important topic in mathematical philosophy.

## Why we care ^why-we-care

At ARC, we are interested in finding explanations of neural network behavior. Concretely, a trained neural net (such as GPT-4) exhibits a really surprising property: it gets low loss on the training set (far lower than a random neural net). We are interested in understanding the structural properties of the neural net that result in it getting low loss.

Our notion of an explanation is related to, but different from, interpretations sought after by [mechanistic interpretability](https://www.transformer-circuits.pub/2022/mech-interp-essay) researchers. The main commonality is that we also seek a mechanistic understanding of neural nets via a close analysis of their internals. Our methods might also be similar: [we are interested](https://www.alignment.org/blog/estimating-tail-risk-in-neural-networks/) in learning generative models of neural activations, much as Anthropic's interpretability team learned sparse autoencoders for neural features using [dictionary learning](https://transformer-circuits.pub/2023/monosemantic-features). However, there are important differences:

-   We do not seek an explanation that can be understood by humans. Instead, we hope to use our explanations to solve formally specified safety-relevant tasks such as [mechanistic anomaly detection](https://www.alignment.org/blog/mechanistic-anomaly-detection-and-elk/) and [tail risk estimation](https://www.alignment.org/blog/estimating-tail-risk-in-neural-networks/).[^note-11]
-   We seek to understand neural networks _in their entirety:_ enough that we can fully explain the mechanisms by which a neural net is able to achieve such low loss on its training set. This likely means that we cannot make convenient assumptions, like features being [linearly represented](https://arxiv.org/abs/2311.03658) in the neural activations. Our explanations, then, must be far more versatile than the ones that are typically sought after in interpretability research.

One might reasonably ask: why do we believe that such explanations _exist?_ In other words, maybe we can understand some bits and pieces of neural network behavior, but not fully explain the internal structural properties that result in the model's behavior.

Our belief in the existence of such explanations follows from a more general belief: that _all_ surprising mathematical structure has an explanation, in the sense of Gowers' no-coincidence principle.

From our discussions with other researchers, we have gotten the impression that some agree with this overarching intuition while others do not. On the other hand, it seems difficult to argue about the truth or falsehood of such an informal statement. Thus, our attempt at formalization is in part motivated by wanting to explain more concretely what we believe.

If our conjecture is false,[^note-12] we would like to know. It may cause us to lose faith in our belief that neural networks are explainable (in the way that we are using the word "explainable"), and to pivot to a new research direction.

[^note-1]: A circuit is _reversible_ if every gate is a bijective function, see e.g. the [Toffoli gate](https://en.wikipedia.org/wiki/Toffoli_gate).
[^note-2]: In fact, we believe that this is probably true if $\pi$ must be quasi-linear, i.e. $\tilde{O}(|C|)$.
[^note-3]: We think that the distribution over random circuits probably doesn't matter too much for the formal statement, so long as the circuits are deep enough to ensure good mixing. But to be concrete, we could say that a random circuit consists of $n^2$ layers. Each layer has $n$ gates with three inputs and three outputs, such that each of the $3n$ wires is an input to exactly one gate (with wires randomly assigned to gate). Each gate is uniformly chosen among the 8! bijective functions from $\{0,1\}^3$ to $\{0,1\}^3$. For some prior work on random reversible circuits, see [Gay et al. (2025)](https://arxiv.org/abs/2502.07159).
[^note-4]: Technically, our conjecture makes a weaker claim. For instance, there might be a verifier for which the advice string $\pi$ does not necessarily have a natural interpretation as pointing out structural properties of $C$. Ultimately, though, we are interested in finding a verifier that accepts or rejects $C$ based on a structural explanation of the circuit; our no-coincidence conjecture is our best attempt to formalize that claim, even if it is imperfect.
[^note-5]: This is analogous to how there is a formal language for mathematical proofs, and a proof verifier that checks whether a proof is valid. But in our case, $\pi$ is valid if it provides "compelling evidence" that $P(C)$ may be true. A verifier can sometimes accept $(C,\pi)$ even if $P(C)$ is false, so long as it does not do so for too many random circuits; thus, our soundness condition is weaker than the soundness condition for proofs.
[^note-6]: _Some_ circuits that do not satisfy $P$ may have a structure that causes $V$ to accept. This is inevitable. Consider for instance a reversible circuit $C$ that does not do anything with the first $n$ bits of the input, while having no discernible structure on the last $2n$ bits. The heuristic estimate we gave before now suggests a roughly $1/e$ chance that $P(C)$ is true. Since $V$ must be able to output 1 on every $C$ for which $P(C)$ is true, the structural observation that the first $n$ bits are left alone ought to be enough to cause $V$ to output 1.
[^note-7]: After all, many mathematical propositions can be written as statements about boolean circuits. Consider the Goldbach conjecture: every even number greater than 2 can be written as a sum of two primes. We can write this as: for all $k>1$, there exist $p$ and $q$ such that $p+q=2k$ and for all $a,b>1$, $ab\neq p$ and $ab\neq q$. Consider a circuit $C(k, p, q, a, b)$ that outputs $1$ if $p + q = 2k$, $ab \neq p$, and $ab \neq q$. Then Goldbach's conjecture is equivalent to "For all $k$ there exist $p$, $q$ such that for all $a$, $b$, $C(k, p, q, a, b) = 1$." (Or to be more precise, there is a family of such circuits, one for every possible size of $k$, and Goldbach's conjecture is equivalent to this statement being true for all circuits in the family.)
[^note-8]: We reduce from Circuit-SAT. Let $C: \{0, 1\}^n \to \{0, 1\}$ be a boolean circuit. For $x, y, z \in \{0, 1\}^n$, let $C'(x, y, z)$ be equal to $(x, y, z)$ if $C(x) = 1$ and $(x, y, \overline{z})$ if $C(x) = 0$, where $\overline{z}$ is the bitwise NOT of $z$. Then $C'$ is reversible, and $P(C')$ is true if and only if $C$ is satisfiable.
[^note-9]: If our conjecture is true, we think it is probably independent of ZFC. (This is because we expect it to be impossible to rule out that _some_ $C$ satisfies $P$ just by chance, despite the incredible implausibility.) Despite that, it seems realistic to us to find a specific verifier $V$ that would likely satisfy the conjecture statement (even if this could never be proven).
[^note-10]: Save perhaps for the "random circuit" bit, although that's not unprecedented either.
[^note-11]: This is mainly because we do not think it is safe to assume that safety-relevant internal structures will be understandable to humans.
[^note-12]: At least assuming that we have not messed up the conjecture statement. Perhaps it will be false for a reason that has nothing to do with the existence of explanations for circuit behavior, in a way that we have not anticipated. (But we think that our conjecture is more likely to be _true_ for unsatisfying reasons, than false for unsatisfying reasons.)

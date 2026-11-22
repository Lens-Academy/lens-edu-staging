---
title: "Formalizing the presumption of independence"
author:
  - "Paul Christiano"
  - "Eric Neyman"
  - "Mark Xu"
source_url: "https://arxiv.org/abs/2211.06738"
published: 2022-11-12
created: 2026-11-22
accessed: 2026-11-22
llm-review:
  date: 2026-11-22
  model: "sonnet"
  version: "article-qc-v1.5"
  source:
    fetched: 2026-11-22
    kind: "live"
description:
tags:
  - "article-importer"
---

%%
Add discussion note here:

...

%%

## Abstract ^abstract

Mathematical proof aims to deliver confident conclusions, but a very similar process of deduction can be used to make uncertain estimates that are open to revision. A key ingredient in such reasoning is the use of a “default” estimate of $\mathbb{E}\left[XY\right] = \mathbb{E}\left[X\right] \mathbb{E}\left[Y\right]$ in the absence of any specific information about the correlation between $X$ and $Y$, which we call _the presumption of independence_. Reasoning based on this heuristic is commonplace, intuitively compelling, and often quite successful—but completely informal.

In this paper we introduce the concept of a heuristic estimator as a potential formalization of this type of defeasible reasoning. We introduce a set of intuitively desirable coherence properties for heuristic estimators that are not satisfied by any existing candidates. Then we present our main open problem: is there a heuristic estimator that formalizes intuitively valid applications of the presumption of independence without also accepting spurious arguments?

## Introduction ^introduction

Many formally-specified questions are very hard to settle with proofs. There are famous examples like the twin prime conjecture, but also countless more mundane examples like how quickly the temperature of a simulated room would change if the window were opened.

Even when we cannot prove a theorem, we can often deductively arrive at a reasonable best guess about the truth of a claim or the behavior of a system. We can make probabilistic arguments about the structure of the primes to estimate the density of twin primes, or about small molecules moving randomly in order to estimate the rate of heat transfer.

This reasoning requires making best guesses about quantities that we can’t calculate exactly. We can often do this using the _presumption of independence_: when trying to estimate $\mathbb{E}\left[XY\right]$ without any knowledge about the relationship between $X$ and $Y$, we can use $\mathbb{E}\left[X\right]\mathbb{E}\left[Y\right]$ as a default guess rather than remaining completely agnostic. For example, we can provisionally treat “$x$ is prime” and “$x+2$ is prime” as independent, or treat the velocities of different air molecules as uncorrelated.

This principle is sufficient to make plausible estimates about a very wide range of mathematical quantities. But it is not clear how to formalize this kind of defeasible reasoning, nor is it clear how to generalize our default guess to the situation where we have arbitrary partial information about how $X$ and $Y$ are related.

Heuristic reasoning using the presumption of independence is distinct from running experiments or Monte Carlo simulations. We are not merely observing a lot of twin primes and inferring that there are probably infinitely many of them, or running simulations of a room and observing how quickly the temperature changes—we have found a good reason that our answer _should be_ right unless there is additional structure that we’ve overlooked which changes the answer.

We emphasize that this is not a novel proposal; the presumption of independence is a common ingredient in existing heuristic arguments and has been explicitly articulated in essentially this form by \[23\]. The purpose of this paper is to clarify the meta-problem of formalizing this principle.

In Sections [[#^example-the-twin-prime|1]] and [[#^other-examples|2]] we discuss informal examples of such reasoning in number theory, combinatorics, and dynamical systems. In Section [[#^heuristic-estimators|3]] we introduce the concept of a _heuristic estimator_ to formalize defeasible reasoning based on heuristic arguments. In Section [[#^desirable-properties-for-heuristic|4]] we introduce a set of coherence conditions for heuristic estimators which we believe should be satisfied by any adequate formalization of the presumption of independence. In Section [[#^formalizing-intuitively-valid-heuristic|5]] we precisely state the problem of finding a heuristic estimator that formalizes a given set of informal heuristic arguments. Finally in Section [[#^circuits-as-a-setting|6]] we propose heuristic evaluation of boolean circuits as a simple domain for studying heuristic estimators.

In the appendices we discuss a number of subtleties and conjectures, describe a simple formalization of the presumption of independence that proves to be inadequate, and discuss potential applications of heuristic arguments in machine learning.

## Example: the twin prime conjecture ^example-the-twin-prime

There are many existing examples of heuristic arguments, especially in number theory; \[23\] presents the twin prime conjecture as a simple example, and in this section we essentially reiterate that presentation.

**Question 1**. _A twin prime pair is a pair of integers $\left(x, x+2\right)$ which are both prime. How many twin prime pairs are there with $x \leq N$?_

By the prime number theorem, a _random_ integer between $1$ and $N$ is prime with probability roughly[^note-1] $\frac 1{\ln{N}}$. So we have: 

$$
\begin{align*}
    \mathbb{P}_{x \sim \left\{1, 2, \ldots, N\right\}}\left(\textnormal{\(x\) is prime}\right) = \mathbb{P}_{x \sim \left\{1, 2, \ldots, N\right\}}\left(\textnormal{\(x+2\) is prime}\right) = \frac 1{\ln{N}}
\end{align*}
$$

 However, it is extraordinarily difficult to calculate $\mathbb{P}\left(\textnormal{\(x\) is prime and \(x + 2\) is prime}\right)$. To make a best guess about this probability, we will need to make some defeasible assumption:

The presumption of independence.

If we have estimates for $\mathbb{P}\left(A\right)$ and $\mathbb{P}\left(B\right)$ but know nothing about how $A$ and $B$ are related, then we presume that the events are independent and estimate $\mathbb{P}\left(A \wedge B\right) \approx \mathbb{P}\left(A\right) \mathbb{P}\left(B\right)$. This presumption can be overturned, and our estimate revised, if we later notice a way that $A$ and $B$ are related.

This principle is called the “basic heuristic” in \[23\], and following their usage we will call an argument using it a _probabilistic heuristic argument_. This principle seems almost inevitable if we are committed to making _some_ best guess about $\mathbb{P}\left(A \wedge B\right)$—after all we have no reason to guess either a positive or negative correlation.

Using the presumption of independence, we estimate: 

$$
\begin{align*}
    \mathbb{P}_{x \leq N}\left(\textnormal{\(x\) is prime} \wedge \textnormal{\(x+2\) is prime}\right)
    &\approx \mathbb{P}_{x \leq N}\left(\textnormal{\(x\) is prime}\right) \times \mathbb{P}_{x \leq N}\left(\textnormal{\(x+2\) is prime}\right) \\
    &= \frac 1{\ln{N}} \times \frac 1{\ln N} = \frac 1{\ln^2 N}.
\end{align*}
$$

 So we expect $\frac {N}{\ln^2 N}$ twin primes less than $N$. The twin prime conjecture is the statement that there are infinitely many twin primes; by applying the presumption of independence again[^note-2] we estimate $\mathbb{P}\left(\textnormal{twin prime conjecture}\right) = 1$.

Our estimate for the number of twin primes is uncertain for two reasons:

Chance.

There may be surprisingly few or surprisingly many twin primes “by chance.” For example, this same methodology expects that a random pair $(x, x+2)$ between $10,000$ and $10,100$ has about a $1/100$ chance of being a twin prime, and so on average there will be about $1$ twin prime pair in that range. But we would not be too surprised to find that there were actually no twin primes in the interval, or that there were multiple.[^note-3]

Defeasibility.

More importantly, this estimate could change completely if we later noticed a reason that $\left(\textnormal{\(x\) is prime}\right)$ and $\left(\textnormal{\(x+2\) is prime}\right)$ are correlated.

For example, if we had instead been trying to estimate the number of pairs $\left(x, x+1\right)$ that are both primes, we would have _also_ concluded that there should be about $\frac N{\ln^2 N}$ and that there should be infinitely many with probability $1$. But eventually we may notice that at least one of $x$ and $x+1$ is divisible by $2$, and so for $x > 2$ these events are perfectly anticorrelated. So our conclusion was wrong even though we gave it probability of $1$. The probabilities we assign do not capture the possibility of this kind of revision—they quantify only the uncertainty from “chance” and not from defeasibility.

For the twin prime conjecture there are a few considerations that slightly change the estimate $\frac {N}{\ln^2 N}$. Most importantly, if $x$ is prime then $x+2$ is also odd and hence twice as likely to be a prime. The net effect of all known corrections is to increase our estimate by about 30% from $\frac {N}{\ln^2 N}$ to $\frac {2 C_2 N}{\ln^2 N}$, where $C_2 = 0.660\ldots$ is called the _twin prime constant_,[^note-4] but until we have a proof we cannot rule out the possibility of finding a new consideration that totally changes our estimate.

Despite these limitations, we think that probabilistic heuristic arguments can give us reasonable best guesses about the truth of mathematical statements.

The other side of these limitations is that it is typically _much_ easier to make a heuristic estimate than to find a proof. Intuitively, a heuristic estimate represents a best guess given whatever structure and correlations we have noticed so far, whereas a proof requires ruling out the possibility of _any_ other correlations or coincidences. This is much harder and usually requires completely different techniques.

## Other examples ^other-examples

We can use the presumption of independence to produce heuristic estimates across a wide variety of domains:

Diffusion.

Suppose that I have a frictionless pool table with a line down the middle dividing it in half. I place 15 perfectly elastic pool balls at random on the left half of the table each with an initial velocity of 1 meter per second in a random direction. After twenty seconds, what is the probability that most of the balls are still on the left half of the table?

Exactly tracking how the distribution of balls changes over time is completely intractable. But we could summarize it by separately considering the distribution over each ball’s position and velocity. If we treat these quantities as independent for different balls, then it becomes easy to track how they evolve over time. Under this simplification the positions quickly converge to uniform. Within 20 seconds each ball has almost exactly a $50\%$ chance of being on either half of the table, and so the probability of most of them being on the left half is also $50\%$. (We discuss this example in more detail in Appendix [[#^billiard-balls|9.3]].)

Hash functions.

SHA-256 is a complex circuit with $256$ bit outputs. What is the probability that there exists a $256$ bit string $x$ such that $\textnormal{SHA-256}\left(x\right)$ is all zeros?

To answer this question we want to understand the output distribution of SHA-256 if we sample the input bits uniformly and independently. This is very hard to compute exactly, but it is quite easy to compute the probability distribution over each intermediate value computed by SHA-256 _if we assume that each operation’s inputs are independent_. Under this approximation we find that essentially every intermediate value is uniformly random, and in particular the output bits are unbiased.

If we further assume that those output bits are independent, then there is a $2^{-256}$ chance that any given value $\textnormal{SHA-256}\left(x\right)$ has all $256$ bits equal to $0$. If these different values of $\textnormal{SHA-256}\left(x\right)$ are themselves independent, then there is a probability of $1 - \left(1 - 2^{-256}\right)^{2^{256}} \approx 1 - 1/e$ that at least one output is all zeros.

The prime number theorem.

Our analysis of the twin prime conjecture relied heavily on the claim that a random number $x$ has a $\frac 1{\ln x}$ chance of being prime.

We can derive this fact heuristically by noticing that $x$ is prime if and only if it has no prime divisors, and treating each event $p|x$ as independent with probability $\frac 1p$. This implies 

$$
\mathbb{P}\left(\textnormal{\(x\) is prime}\right) = \prod_{\textnormal{prime \(p\)} < x} \left(1 - \frac 1p\right)
$$

 and gives us an estimate for $\mathbb{P}\left(\textnormal{\(x\) is prime}\right)$ that depends on the number and distribution of smaller primes. By solving the resulting recurrence relation we conclude that $\mathbb{P}\left(\textnormal{\(x\) is prime}\right) = \frac 1{\ln x} + O\left(\frac 1{\ln^2 x}\right)$.

Note that in all of these cases the _only_ heuristic step is the presumption of independence—the rest of the argument is deductively valid. We walk through more examples in Appendix [[#^examples-of-heuristic-arguments|9]], each of which is also a deductively valid argument combined with a suitable generalization of the presumption of independence.

This is not the only possible kind of heuristic argument. For example, we might conclude that a theorem is likely to be true based on checking enough special cases, or conclude that a theorem is likely to be false because it involves a constant like $3.14158$ that looks like it _should_ be $\pi$.

But the presumption of independence seems like an extremely general and powerful tool, which is sufficient to produce useful heuristic estimates across a broad range of domains. This is easiest to assess in mathematics and especially number theory, where we believe there are probabilistic heuristic arguments for a significant majority of open problems,[^note-5] but we believe that it is also effective in other domains where efficacy is harder to quantify.

## Heuristic estimators ^heuristic-estimators

What would it look like to formalize this kind of reasoning?

We can formalize a traditional proof system by specifying a language for proofs and defining a proof verifier $V$: an efficient program which takes as input a statement $\varphi$ and a putative proof $\pi$, and then outputs a judgment $V\left(\varphi, \pi\right) \in \left\{\top, \bot, ?\right\}$. The outputs $\top$ or $\bot$ indicate that $\pi$ was a proof or disproof of $\varphi$ and in these cases we might say that $V$ confidently “believes” $\varphi$ to be true or false. The output $?$ indicates that $\pi$ was not a valid proof and so $V$ is agnostic about $\varphi$.

We will aim to formalize heuristic arguments by specifying a language for heuristic arguments and defining an analogous _heuristic estimator_ $\widetilde{\mathbb{P}}$: an efficient program which takes as input a statement $\varphi$ and a **set** of heuristic arguments $\pi_1, \pi_2, \ldots, \pi_n$, then outputs a best guess $\widetilde{\mathbb{P}}\left(\varphi, \pi_1, \ldots, \pi_n\right) \in [0, 1]$ about the probability of $\varphi$.

The major conceptual difference between a heuristic estimator and a proof verifier is that a heuristic estimator _always_ outputs a best guess in light of the available arguments, whereas a proof verifier effectively remains agnostic until finding a proof. These estimates are subject to revision and need not be calibrated, but we do still expect them to satisfy simple coherence properties (see Section [[#^desirable-properties-for-heuristic|4]]). As a special case, $\widetilde{\mathbb{P}}\left(\varphi\right)$ should produce a default estimate before seeing any arguments at all.[^note-6]

The reason we consider a set of arguments rather than just one is that any given argument is defeasible and open to revision. If Alice points out a reason to think that $\varphi$ is true and Bob points out a reason to think that $\varphi$ is false, we want to be able to combine those arguments to arrive at an all-things-considered best guess about $\varphi$. This was not necessary for proof verifiers because a single proof settles the question.

Our goal is to find a natural heuristic estimator $\widetilde{\mathbb{P}}$ that is able to recognize the kind of argument presented in Section [[#^example-the-twin-prime|1]]. That is, after seeing such an argument it should output that the twin prime conjecture is almost certainly true, and then it should only revise that conclusion if given another argument $\pi_i$ that undermines one of the independence assumptions and suggests an alternative estimate. We formalize this goal in Section [[#^formalizing-intuitively-valid-heuristic|5]].

Rather than only evaluating the truth of propositions, we will generalize further to heuristic estimators $\widetilde{\mathbb{E}}$ for arbitrary quantities. In this case we take $X$ to be a formal expression defining a real number, and interpret $\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right)$ as a “subjective expected value” of $X$.[^note-7] Of course we can recover $\widetilde{\mathbb{P}}$ as the expectation of the indicator function $\mathbf{1}_{\varphi}$.

### A bad example of a heuristic estimator ^a-bad-example-of

To illustrate the definition, we can define a heuristic estimator $\widetilde{\mathbb{E}}$ that treats $X$ as uniformly random between the lowest and highest possible value:

-   **What is an argument $\pi_i$?** An argument $\pi_i$ must be a proof that $\ell \leq X \leq h$ for some real numbers $\ell$ and $h$.
    
-   **What is $\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right)$?** Let $\ell^*$ be the maximum of the lower bounds proven by any of the $\pi_i$, and let $h^*$ be the minimum of the upper bounds. Define $\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right)$ to be the average of those bounds $\frac{\ell^* + h^*}{2}$, with the convention that $\frac{-\infty + \infty}{2} = 0$ so that $\widetilde{\mathbb{E}}\left(X\right) = 0$.
    

We consider this heuristic estimator extremely unreasonable. To see why, suppose that $A, B \in \left\{0, 1\right\}$ have complex definitions such that it is hard to prove anything about them or about how they relate. We would expect a good heuristic estimator to treat each of them as uniformly random, and to converge to an estimate $\widetilde{\mathbb{E}}\left(AB, \pi_1, \ldots, \pi_n\right) = \frac 14$ once all relevant arguments are pointed out. But if the only thing we can **prove** is that $AB \in \left\{0, 1\right\}$, then this estimator will instead converge to the estimate $\widetilde{\mathbb{E}}\left(AB, \pi_1, \ldots, \pi_n\right) = \frac 12$.

In fact, after seeing the relevant arguments this estimator converges to: 

$$
\begin{gather*}
    \widetilde{\mathbb{E}}\left(AB\right) = \widetilde{\mathbb{E}}\left(A(1-B)\right) = \widetilde{\mathbb{E}}\left((1-A)B\right) = \widetilde{\mathbb{E}}\left((1-A)(1-B)\right) = \frac 12 \\
    \widetilde{\mathbb{E}}\left(AB  + A(1-B) + (1-A) B + (1-A)(1-B)\right) = \widetilde{\mathbb{E}}\left(1\right) = 1
\end{gather*}
$$

 and so $\widetilde{\mathbb{E}}$ is not even linear.

## Desirable properties for heuristic estimators ^desirable-properties-for-heuristic

A heuristic estimator $\widetilde{\mathbb{E}}$ should behave like an expectation. That is, for any sequence of arguments $\pi_1, \ldots, \pi_n$ it should satisfy:

-   **Constant expectations.** For any constant $c$, 
    
    $$
    \widetilde{\mathbb{E}}\left(c, \pi_1, \ldots, \pi_n\right) = c.
    $$
    
-   **Linearity of expectation.** For any quantities $X, Y$ and constants $a, b$, 
    
    $$
    \widetilde{\mathbb{E}}\left(aX + bY, \pi_1, \ldots, \pi_n\right) = a\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right) + b\widetilde{\mathbb{E}}\left(Y, \pi_1, \ldots, \pi_n\right).
    $$
    

A good estimator $\widetilde{\mathbb{E}}$ should revise its estimates based on arguments, which should be at least as expressive as traditional proofs:

-   **Respect for proofs.** If $\pi$ is a proof that $X \geq 0$, then there should be an analogous heuristic argument $\pi_*$ such that for any $\pi_1, \ldots, \pi_n$, 
    
    $$
    \widetilde{\mathbb{E}}\left(X, \pi_*, \pi_1, \ldots, \pi_n\right) \geq 0.
    $$
    

This property depends on the choice of proof system; we are looking for heuristic estimators that respect as many proofs as possible. Together with linearity of expectation, respect for proofs implies that if $X$ and $Y$ are provably equal, then there is a $\pi_*$ such that $\widetilde{\mathbb{E}}\left(X, \pi_*, \pi_1, \ldots, \pi_n\right) = \widetilde{\mathbb{E}}\left(Y, \pi_*, \pi_1, \ldots, \pi_n\right)$ for any $\pi_1, \ldots, \pi_n$.

A reasonable estimator $\widetilde{\mathbb{E}}$ should not revise its beliefs if we provide an irrelevant argument $\pi_*$, or if we repeat or rearrange arguments:

-   **Independence of irrelevant arguments (informal).** If $\pi_*$ is irrelevant to the value of $X$, then 
    
    $$
    \widetilde{\mathbb{E}}\left(X, \pi_*, \pi_1, \ldots, \pi_n\right) = \widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right).
    $$
    
-   **Invariance to repetition and rearrangement.** If $\left\{\pi_1, \ldots, \pi_n\right\} = \left\{\pi_1', \ldots, \pi_m'\right\}$, i.e. if the two sequences of arguments are the same up to repetition and rearrangement, then 
    
    $$
    \widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right) = \widetilde{\mathbb{E}}\left(X, \pi_1', \ldots, \pi_m'\right).
    $$
    

Finally, we are particularly interested in heuristic estimators that capture the presumption of independence.

-   **Presumption of independence (informal).** If $\pi_1, \ldots, \pi_n$ do not provide any reason to think that $X$ and $Y$ are related, then 
    
    $$
    \widetilde{\mathbb{E}}\left(XY, \pi_1, \ldots, \pi_n\right) = \widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right) \widetilde{\mathbb{E}}\left(Y, \pi_1, \ldots, \pi_n\right).
    $$
    

These six properties are not necessarily sufficient to conclude that a heuristic estimator is reasonable, but we are not aware of any estimator that satisfies them. We believe that finding such an estimator would be a promising step forward.

### Heuristic arguments sometimes make estimates worse ^heuristic-arguments-sometimes-make

One desirable property was conspicuously missing from the above list:

-   **Monotonic improvement.** For any $\pi_*$ and any $X$, 
    
    $$
    \left|\widetilde{\mathbb{E}}\left(X, \pi_*, \pi_1, \ldots, \pi_n\right) - X\right| \leq \left|\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right) - X\right|.
    $$
    

Unfortunately, no matter how good an estimator $\widetilde{\mathbb{E}}$ we find, we do not expect monotonic improvement. That is, we think it is possible for valid arguments to push even an ideal reasoner’s beliefs in the wrong direction.

To see this, suppose we are trying to estimate $A+B+C$ where $A, B, C \in \left\{+1, -1\right\}$. Assume that $\widetilde{\mathbb{E}}\left(A\right) = \widetilde{\mathbb{E}}\left(B\right) = \widetilde{\mathbb{E}}\left(C\right) = 0$, so $\widetilde{\mathbb{E}}\left(A+B+C\right) = 0$. Suppose that $\pi_A$ is a proof that $A = 1$. Then we expect $\widetilde{\mathbb{E}}\left(A+B+C, \pi_A\right) = 1$. But it may turn out by chance that $B=C=-1$, in which case $A+B+C=-1$ and the argument $\pi_A$ happened to push $\widetilde{\mathbb{E}}$’s estimate in the wrong direction. This means that even if we are searching for arguments in an unbiased way, they will sometimes happen to make our estimate worse by chance. And if someone searches for adversarially misleading estimates, they will usually be able to succeed.

In Appendix [[#^cherry-picking-arguments|13]] we discuss a sequence of increasingly severe versions of this problem, and explore the behavior of heuristic estimators when given adversarially-selected arguments. Despite the fact that arguments do not always improve estimates, we still believe that formalizing heuristic arguments can help clarify which arguments we ought to consider valid and how we should update our beliefs in light of them.

## Formalizing intuitively valid heuristic arguments ^formalizing-intuitively-valid-heuristic

One of our main goals is to find a heuristic estimator $\widetilde{\mathbb{E}}$ that is able to accept as many intuitively valid heuristic arguments as possible without also accepting spurious arguments. In this section we try to make this goal more precise.

We have already seen a few examples of informal heuristic arguments based on the presumption of independence. In Appendix [[#^examples-of-heuristic-arguments|9]] we present three more detailed examples. Each example can be described as a triple $\left(X, \mu, \widetilde{\pi}\right)$, where $\widetilde{\pi}$ is an informal heuristic argument that $\mathbb{E}\left[X\right] = \mu$. For example, $X$ could be the number of twin primes less than $2^{256}$ and $\widetilde{\pi}$ could be the informal argument in Section [[#^example-the-twin-prime|1]].

For a given triple $\left(X, \mu, \widetilde{\pi}\right)$, we can capture whether $\widetilde{\mathbb{E}}$ accepts $\widetilde{\pi}$ by asking whether there exists a formalization $\pi$ of $\widetilde{\pi}$ such that 

$$
\widetilde{\mathbb{E}}\left(X, \pi\right) = \mu.
$$

 It is less clear how to precisely state the requirement that $\widetilde{\mathbb{E}}$ does not also accept spurious arguments because we have not defined what a “spurious argument” is.

Fortunately, in many cases we would be very surprised to find significant revisions to the estimate $\mu$. For example, any significant revision to the heuristic estimate for the number of twin primes in Section [[#^example-the-twin-prime|1]] would be a major and surprising development in number theory. In these cases, we think that _any_ argument that changes $\widetilde{\mathbb{E}}$’s estimate from $\mu$ is likely to be spurious. So we expect $\widetilde{\mathbb{E}}$ to satisfy: 

$$
\begin{equation}
\exists \pi \colon \forall \left\{\pi_1, \pi_2, \ldots, \pi_n\right\} \ni \pi \colon
\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right) \approx \mu,
\tag{1}
\end{equation}
$$

 where it should be straightforward (but potentially laborious) to construct $\pi$ from $\widetilde{\pi}$. In words, it should be possible to produce a formalization $\pi$ of $\widetilde{\pi}$ such that if we present $\pi$ to $\widetilde{\mathbb{E}}$ it produces an estimate close[^note-8] to $\mu$, even if we also provide $\widetilde{\mathbb{E}}$ a set of adversarially misleading arguments.

So any set of triples $\left(X, \mu, \widetilde{\pi}\right)$ leads to a simple open problem: find a heuristic estimator that satisfies Equation 1 for as many triples in that set as possible.

Of course it is possible to satisfy this property for any finite set of triples $(X, \mu, \widetilde{\pi})$ by specifying the expected answers directly as part of the definition of $\widetilde{\mathbb{E}}$. So to make the problem challenging we want to search for an $\widetilde{\mathbb{E}}$ that also works for a larger set of similar “held out” examples $\widetilde{\mathbb{E}}$.[^note-9] Fortunately it is easy to generate a very large number of examples of intuitively compelling heuristic arguments for which significant revisions would be surprising, leading to a large set of triples $\left(X, \mu, \widetilde{\pi}\right)$ that can be used to evaluate a proposed estimator $\widetilde{\mathbb{E}}$. In this document we provide only a small list of examples to illustrate the problem, but we expect to publish a larger list of examples in the future and to maintain a large private “test set” that we can use to evaluate proposed estimators.

The wider the distribution for which $\widetilde{\mathbb{E}}$ works the better, but finding an estimator $\widetilde{\mathbb{E}}$ for even a narrow domain already seems challenging. For example, we believe that a significant majority of plausible conjectures in number theory are supported by a probabilistic heuristic argument. Some of those conjectures can be settled by the Cramër model of the primes or the Diophantine equation heuristic described in Appendix [[#^fermats-last-theorem-note-14|9.1]]. But many of them require _ad hoc_ heuristic arguments, and we think that it is a difficult challenge to write down a verifier that satisfies Equation 1 for a significant fraction of those cases. While there are many simple ways to formalize more general probabilistic heuristic arguments, most of them require unformalized judgment calls, and we believe that any existing fully precise $\widetilde{\mathbb{E}}$ would also accept spurious arguments for incorrect conclusions.

## Circuits as a setting to study heuristic arguments ^circuits-as-a-setting

We are ultimately interested in formalizing the entire range of heuristic arguments that are used in mathematical practice. But it is helpful to have a simplified setting both to illustrate the challenge and to study candidate algorithms.

We propose circuit evaluation as a simple but challenging domain: given a circuit $C\colon \left\{0, 1\right\}^{n} \rightarrow \left\{0, 1\right\}$ estimate the probability that $C(z) = 1$ for a uniformly random input $z$. In this section we describe the task, present a very simple algorithm, and discuss why we consider the challenge interesting.

### Task definition ^task-definition

A simple boolean circuit. The output node $x_m$ is at the bottom of the figure, while the input nodes at the top of the figure are labeled with $z_1$, $z_2$, and $z_3$. In blue we have shown the result of evaluating the circuit on the input triple $\left(z_1, z_2, z_3\right) = \left(1, 1, 0\right)$. For example, the output XOR gate is equal to $0$ because its two inputs are both equal to $1$ and $\textnormal{XOR}(1, 1) = 0$. So $C\left(1, 1, 0\right) = 0$.

Informally, a boolean circuit is a recipe for computing an output value $x_m$ by starting with a set of inputs $z_1, \ldots, z_n$ and then applying a fixed sequence of boolean operations.

Formally, a boolean circuit with $n$ inputs is defined as a set of $m$ nodes $x_1, \ldots, x_m$, where each node $x_k$ is either:

-   An input node labeled with an integer $i_k \in \left\{1, \ldots, n\right\}$.
    
-   A binary gate labeled with a boolean operation $f_k \in \left\{\textnormal{AND}, \textnormal{OR}, \textnormal{XOR}, \ldots\right\}$ and the indices of two inputs $a_k, b_k \in \left\{1, \ldots, k-1\right\}$.
    

A simple circuit is depicted in Figure 1.

To evaluate a circuit on an input $z = \left(z_1, \ldots, z_n\right) \in \left\{0, 1\right\}^{n}$, we proceed through the nodes in order: the value of an input node labeled with $i_k$ is equal to $z_{i_k}$, and the value of a binary gate labeled with $f_k$ is equal to $f_k$ applied to the values of the two inputs $x_{a_k}$ and $x_{b_k}$. The output $C\left(z\right)$ of the circuit is the value of the final node $x_m$.

We write $\mathbb{P}\left(C\right)$ for the probability that $C\left(z\right) = 1$ when $z$ is uniformly random.

We are interested in finding a heuristic estimator $\widetilde{\mathbb{E}}\left(\mathbb{P}\left(C\right), \pi_1, \ldots, \pi_n\right)$ that satisfies the kind of desiderata introduced in Section [[#^desirable-properties-for-heuristic|4]] and is able to formalize a variety of intuitively valid heuristic arguments about $\mathbb{P}\left(C\right)$ in the sense introduced in Section [[#^formalizing-intuitively-valid-heuristic|5]]. We will write $\widetilde{\mathbb{E}}\left(C\right)$ instead of $\widetilde{\mathbb{E}}\left(\mathbb{P}\left(C\right)\right)$.[^note-10]

For example, if $\pi_1$ proves that the output of $C$ is equal to the conjunction of $k$ unbiased and apparently unrelated intermediate values, then we should have $\widetilde{\mathbb{E}}\left(C, \pi_1\right) \approx 2^{-k}$. If $\pi_2$ proves that actually two of these intermediate values are almost always equal, then that should cause $\widetilde{\mathbb{E}}\left(C, \pi_1, \pi_2\right)$ to rise to roughly $2^{-k+1}$. As we consider more and more intuitively compelling arguments $\widetilde{\mathbb{E}}$ should continue to update in the expected way.

Instead of considering a heuristic estimator, we could compute a Monte Carlo estimate for $\mathbb{P}\left(C\right)$ by randomly sampling inputs and calculating the empirical mean of $C(z)$. A heuristic estimator can have two advantages over the Monte Carlo estimator:

-   If $\mathbb{P}\left(C\right)$ is very close to $0$, then $\widetilde{\mathbb{E}}$ can be _much_ faster. It would require about $2^{256}$ samples to distinguish $\mathbb{P}\left(C\right)= 2^{-256}$ from $\mathbb{P}\left(C\right)= 2^{-512}$, but for many circuits we can make heuristic arguments that distinguish these cases using exponentially less time. This is similar to the use of propositional logic to establish a tautology without needing to consider every setting of every variable.
    
-   We are interested in estimators $\widetilde{\mathbb{E}}$ that deterministically analyze the structure of $C$ rather than measuring $\mathbb{P}\left(C\right)$ by random sampling, because we think that this kind of analysis reveals something about _why_ $\mathbb{P}\left(C\right)$ takes on the value that it does. Although we cannot formalize this distinction precisely, we think it is important and discuss it in Appendix [[#^inductive-vs-deductive-arguments|10]].
    

In red we have written the intermediate values $\widetilde{\mathbb{E}}\left(x_k\right)$ computed by assuming that all gates are independent for the simple circuit from Figure 1.. We obtain the estimate $\widetilde{\mathbb{E}}\left(C\right) = 30/64 = \left(3/8\right)\left(5/8\right) + \left(5/8\right)\left(3/8\right)$. The estimate of $\widetilde{\mathbb{E}}\left(C\right)$ would be correct if the two AND gates were independent and each equal to $1$ with probability $3/8$, but actually they are highly correlated (since they have a common input). The true value is $\mathbb{P}\left(C\right)= 2/8$: the circuit returns $1$ if and only if $\left(z_1, z_2, z_3\right)$ is either $\left(1, 0, 0\right)$ or $\left(0, 0, 1\right)$.

### A simple algorithm: assume all nodes are independent ^a-simple-algorithm-assume

One of the simplest possible algorithms is to apply the presumption of independence to every gate in order to estimate $\widetilde{\mathbb{E}}\left(x_k\right)$, the probability that node $x_k$ has value $1$ for random inputs $z_1, \ldots, z_n$:

-   If $x_k$ is an input node, then $\widetilde{\mathbb{E}}\left(x_k\right) = \frac 12$.
    
-   If $x_k = \textnormal{AND}\left(x_{a_k}, x_{b_k}\right)$, then $\widetilde{\mathbb{E}}\left(x_k\right) = \widetilde{\mathbb{E}}\left(x_{a_k}\right) \widetilde{\mathbb{E}}\left(x_{b_k}\right)$; if $x_k = \textnormal{OR}\left(x_{a_k}, x_{b_k}\right)$ then $\widetilde{\mathbb{E}}\left(x_k\right) = 1 - \left( 1 - \widetilde{\mathbb{E}}\left(x_{a_k}\right) \right)\left(1 - \widetilde{\mathbb{E}}\left(x_{b_k}\right)\right)$; and similarly for other functions.
    

Finally we output $\widetilde{\mathbb{E}}\left(C\right) = \widetilde{\mathbb{E}}\left(x_m\right)$. We work through an example of this algorithm in Figure 2.

We can define more accurate estimates by tracking not only the probabilities $\widetilde{\mathbb{E}}\left(x_k\right)$ that individual node are $1$, but various higher-order correlations amongst the nodes. For example, we might track the joint distribution of every pair of nodes $\widetilde{\mathbb{E}}\left(x_i \wedge x_j\right)$, or we might track the expectation of particular large parities $\widetilde{\mathbb{E}}\left(x_{i_1} \oplus x_{i_2} \oplus \cdots \oplus x_{i_k}\right)$ that are important for understanding the behavior of the circuit.

In Appendix [[#^cumulant-propagation|12]] we present an estimator $\widetilde{\mathbb{E}}$ which takes arbitrary “advice” $\pi_1, \ldots, \pi_k$ about which correlations to track, and uses it to produce a heuristic estimate for $\mathbb{P}\left(C\right)$. Unfortunately, this estimator often produces implausible values $\widetilde{\mathbb{E}}\left(C\right) \not\in [0, 1]$. We are interested in a better estimator that is able to capture the same intuitively valid arguments about $\mathbb{P}\left(C\right)$ while also satisfying the desiderata from Section [[#^desirable-properties-for-heuristic|4]].

### Why care about circuits? ^why-care-about-circuits

We view heuristic circuit evaluation as a natural generalization of verifying propositional tautologies.[^note-11] Rather than asking whether an expression is _guaranteed_ to be true or false without knowing anything about its inputs, we are instead asking how _likely_ it is to be true given uniform ignorance about its inputs.

We are particularly optimistic about formalizing informal heuristic arguments that do not involve quantifiers or abstractions. Such heuristic arguments seem to be analogous to proofs in propositional logic, but despite their simplicity we nevertheless cannot write down any estimator $\widetilde{\mathbb{E}}$ which is able to capture them.

We believe that heuristically evaluating circuits is a stepping stone to formalizing general heuristic arguments in the same way that propositional logic is a stepping stone towards first-order logic. We can view the set of statements in an argument as a kind of “advice” about which propositions or quantities to pay attention to. If we understood how to propagate our uncertainty from one quantity to another in a circuit then we could plausibly apply similar ideas to propagate uncertainty within a more complex argument. Conversely if we are unable to produce coherent probability estimates for circuits then it seems unlikely that we can produce reasonable probability estimates for the statements arising in a complex argument.

In particular, trying to heuristically evaluate circuits forces us to formalize and generalize the “presumption of independence.” For example, we need to handle cases where we have information about the _pairwise_ interactions between $x_1$, $x_2$, and $x_3$, and want to make a guess about the conjunction $x_1 \wedge x_2 \wedge x_3$. Generalizing the presumption of independence in a coherent way appears to be quite challenging, and we think it is the largest difficutly separating the formalization of proofs from the formalization of heuristic arguments.

## Related work ^related-work

There are many examples of probabilistic heuristic arguments in the literature across a very wide range of domains (e.g. \[7, 21, 17, 11, 3\]), and many discussions of the philosophy of applying heuristic arguments to unprovable statements (e.g. \[6, 9\]). But we are aware of very little work on formalizing these standards or attempting to investigate heuristic arguments formally.

The most similar presentation we have encountered is the blog post \[23\], which discusses the idea of assigning probabilities to deterministic claims and presents two “probabilistic heuristics:”

Basic heuristic

“If two or more of these heuristically probabilistic events have no obvious reason to be strongly correlated to each other, then we should expect them to behave as if they were (jointly) independent.”

Advanced heuristic

“If two or more of these heuristically probabilistic events have _some_ obvious correlation between them, but no further correlations are suspected, then we should expect them to behave as if they were conditionally independent, relative to whatever data is causing the correlation.”

We are not proposing any revisions to these heuristics. The main difference is that we are optimistic about capturing them as part of a more general formal framework; in this document we try to state that meta-problem. In Appendix [[#^cumulant-propagation|12]] we describe our best attempt to design such a general framework and explain why we consider it inadequate.

There are other types of reasoning that are distinct from heuristic arguments, but close enough to be worth distinguishing specifically.

**Random models in number theory.** The closest thing to a formalization of heuristic argument is the explicit use of random models as surrogates for complex objects. Most famous is the Cramér model of the primes \[7\], which suggests that a statement is likely to be true of the primes if it is true with high probability for a random set in which each integer $x > 1$ is included with probability $\frac 1{\ln x}$. Similarly, Erdős and Ulam analyze Fermat’s last theorem by proving that the analogous statement would almost surely be true if we replaced the perfect $n^{\textnormal{th}}$ powers with a random set of similar density \[11\]. We are unsatisfied by these arguments for a few closely related reasons:

-   Each such model applies to a relatively narrow range of questions—we are interested in finding more general rules that could be used to evaluate a wide range of questions (ideally across a wide range of domains). To do so, we would like to derive principles like the Cramér model from simpler principles, rather than including them in a very long list of “heuristic axioms.”
    
-   Even within a domain, the applicability of these random models is usually evaluated by informal judgment. For example, the Cramér model is usually considered to be applicable only for “global” questions in an informal sense \[22\]. We would like to formalize this judgment of applicability, and capture it in a concrete heuristic estimator.
    
-   Even when such models apply, we need to consider correction terms in order to get accurate estimates—for example the actual density of twin primes is about $30\%$ higher than the estimate from the Cramér model. How do we formalize the process for making this kind of correction without allowing the model to produce arbitrary conclusions?[^note-12]
    
-   Beyond these difficulties, we are interested in formalizing the many heuristic arguments which are not captured by any such random surrogate (including the arguments about billiard balls and SHA-256 discussed in Section [[#^other-examples|2]]).
    

**Interactive proofs.** There is a large literature exploring protocols by which powerful provers can convince bounded verifiers of complex claims even in cases where there is no short traditional proof (for the introduction of this concept see \[16\]). However none of these systems capture the kind of informal heuristic arguments we discuss in this document, and they often require extraordinarily powerful provers. For example, while there are known interactive proof systems that allow us to efficiently verify any statement that has an exponentially-long proof, these systems require the _prover_ to do exponential computation. Heuristic estimators can be viewed as a type of interactive proof system with very weak guarantees, but which are hopefully able to produce reasonable estimates for realistically limited provers.

**Formalizations of logical uncertainty.** Several authors have explored mechanisms for assigning probabilities to arbitrary sentences of logic (e.g. \[13, 18, 8, 14\]). However these approaches have primarily focused on establishing coherence conditions and on capturing _inductive_ reasoning, i.e. ensuring that a reasoner eventually successfully predicts $\varphi\left(n\right)$ given observations of $\varphi\left(1\right), \varphi\left(2\right), \ldots \varphi\left(n-1\right)$. These systems would not automatically recognize intuitively valid heuristic arguments, e.g. they would not revise the probability they assign to the twin prime conjecture after noticing the heuristic argument presented in Section [[#^example-the-twin-prime|1]], although they would eventually _learn_ to trust these arguments after observing them producing good predictions in practice.[^note-13] Indeed, we can view ourselves as reasoners in exactly this situation, trying to understand and formalize a type of reasoning that appears to often make good predictions in practice. Formalizations of inductive reasoning may help clarify the standards we should use for evaluating a proposed heuristic estimator, but do not constitute a good heuristic estimator themselves.

## Conclusion ^conclusion

Heuristic arguments based on the presumption of independence often converge to empirically reasonable estimates and can be intuitively compelling, yet there is no existing formal framework for representing or validating this kind of reasoning. In this paper we introduced a simple definition of a “heuristic estimator,” and stated a few open problems:

-   Finding any estimator that satisfies the desiderata in Section [[#^desirable-properties-for-heuristic|4]].
    
-   Formalizing as many intuitively valid heuristic arguments as possible (Section [[#^formalizing-intuitively-valid-heuristic|5]]).
    
-   Finding better heuristic estimators for the output probability $\mathbb{P}\left(C\right)$ of a logical circuit $C$ (Section [[#^circuits-as-a-setting|6]]).
    

Formalizing the previously-informal notion of proof played a central role in modern mathematics and computer science, and in the best case formalizing heuristic arguments could open up analogous intellectual territory. If successful, it may also help improve our ability to verify reasoning about complex questions, like those emerging in modern machine learning, for which we expect formal proof to be impossible.

We have given a high-level overview of the questions we find most exciting. In the appendices we explore heuristic arguments in more depth:

-   In Appendix [[#^examples-of-heuristic-arguments|9]] we provide three additional examples of heuristic arguments to illustrate the breadth of applicability, highlight some important subtleties, and provide test cases for the open problem presented in Section [[#^formalizing-intuitively-valid-heuristic|5]].
    
-   In Appendix [[#^inductive-vs-deductive-arguments|10]] we introduce a distinction between “inductive” and “deductive” arguments, and explain why we believe probabilistic heuristic arguments may help capture the _reason why_ a statement is true.
    
-   In Appendix [[#^soundness|11]] we present the strong conjecture that any true mathematical sentence has a deductive heuristic argument for its plausibility.
    
-   In Appendix [[#^cumulant-propagation|12]] we present a formalization of the presumption of independence in terms of the joint cumulants of several variables. We use this to define cumulant propagation, a simple heuristic estimator for the expected output of an arithmetic circuit with Gaussian inputs, and explain why we find this estimator inadequate.
    
-   In Appendix [[#^cherry-picking-arguments|13]] we explore some examples where cherry-picking prevents heuristic estimators from converging to reasonable estimates in finite time.
    
-   In Appendix [[#^applications-to-machine-learning|14]] we briefly discuss some potential applications of heuristic arguments in machine learning.
    

## References ^references

-   \[1\] Nima Anari, Leonid Gurvits, Shayan Oveis Gharan, and Amin Saberi, _Simply exponential approximation of the permanent of positive semidefinite matrices_, 2017 IEEE 58th Annual Symposium on Foundations of Computer Science (FOCS), IEEE, 2017, pp. 914–925.
    
-   \[2\] Boaz Barak, Oded Goldreich, Rusell Impagliazzo, Steven Rudich, Amit Sahai, Salil Vadhan, and Ke Yang, _On the (im) possibility of obfuscating programs_, Annual international cryptology conference, Springer, 2001, pp. 1–18.
    
-   \[3\] F Cornu and HJ Hilhorst, _Density decay and growth of correlations in the game of life_, Journal of Statistical Mechanics: Theory and Experiment **2019** (2019), no. 1, 013212.
    
-   \[4\] Pafnuty Lvovich Chebyshev, _Letter from professor tchébycheva m. fuss on a new theéorem relating to prime numbers contained in the forms 4n+ 1 and 4n+ 3_, 208.
    
-   \[5\] Paul Christiano, _Non-omniscience, probabilistic inference, and metamathematics_, 2014.
    
-   \[6\] John H Conway, _On unsettleable arithmetical problems_, The American Mathematical Monthly **120** (2013), no. 3, 192–198.
    
-   \[7\] Harald Cramér, _On the order of magnitude of the difference between consecutive prime numbers_, Acta arithmetica **2** (1936), 23–46.
    
-   \[8\] Abram Demski, _Logical prior probability_, International Conference on Artificial General Intelligence, Springer, 2012, pp. 50–59.
    
-   \[9\] Freeman Dyson, What We Believe but Cannot Prove (John Brockman, ed.), Harper Perennial, 2006, pp. 82–83.
    
-   \[10\] Noam D Elkies, _On a^4+b^4+c^4=d^4_, Mathematics of Computation (1988), 825–835.
    
-   \[11\] P Erdös and S Ulam, _Some probabilistic remarks on fermat’s last theorem_, The Rocky Mountain Journal of Mathematics **1** (1971), no. 4, 613–616.
    
-   \[12\] Roger E Frye, _Finding 95800 4+ 217519 4+ 414560 4= 422481 4 on the connection machine_, Proceedings of supercomputing, vol. 88, 1988, pp. 106–116.
    
-   \[13\] Haim Gaifman, _Reasoning with limited resources and assigning probabilities to arithmetical statements_, Synthese **140** (2004), no. 1/2, 97–119.
    
-   \[14\] Scott Garrabrant, Tsvi Benson-Tilsen, Andrew Critch, Nate Soares, and Jessica Taylor, _Logical induction_, arXiv preprint arXiv:1609.03543 (2016).
    
-   \[15\] Andrew Granville and Greg Martin, _Prime number races_, The American Mathematical Monthly **113** (2006), no. 1, 1–33.
    
-   \[16\] Shafi Goldwasser, Silvio Micali, and Charles Rackoff, _The knowledge complexity of interactive proof systems_, SIAM J. COMPUT **18** (1989), no. 1, 186–208.
    
-   \[17\] Bogdan Grechuk, _Diophantine equations: a systematic approach_, arXiv preprint arXiv:2108.08705 (2021).
    
-   \[18\] Marcus Hutter, John W. Lloyd, Kee Siong Ng, and William T. B. Uther, _Probabilities on sentences in an expressive logic_, CoRR **abs/1209.2620** (2012).
    
-   \[19\] Jerzy Kaczorowski, _On the distribution of primes (mod4)_, Analysis **15** (1995), no. 2, 159–172.
    
-   \[20\] Martin Hugo Löb, _Solution of a problem of leon henkin_, The Journal of Symbolic Logic **20** (1955), no. 2, 115–118.
    
-   \[21\] Marc Mézard and Riccardo Zecchina, _Random k-satisfiability problem: From an analytic solution to an efficient algorithm_, Physical Review E **66** (2002), no. 5, 056126.
    
-   \[22\] János Pintz, _Cramér vs. Cramér. On Cramér’s probabilistic model for primes_, Functiones et Approximatio Commentarii Mathematici **37** (2007), no. 2, 361 – 376.
    
-   \[23\] Terence Tao, _The probabilistic heuristic justification of the ABC conjecture_, [terrytao.wordpress.com](https://terrytao.wordpress.com/2012/09/18/the-probabilistic-heuristic-justification-of-the-abc-conjecture/), Sep 2012.
    
-   \[24\] Brent Waters, _A punctured programming approach to adaptively secure functional encryption_, Annual Cryptology Conference, Springer, 2015, pp. 678–697.
    

:::callout {title="Appendix" collapse="closed"}
## Examples of heuristic arguments ^examples-of-heuristic-arguments

### Fermat’s last theorem[^note-14] ^fermats-last-theorem-note-14

**Question 2**. _For which integers $n$ does the equation $a^n + b^n = c^n$ have any solutions with $a, b, c > 0$?_

We will start by asking: for a given $a > 0$, how likely is it that there is a solution $a^n + b^n = c^n$ with $b \leq a$? Equivalently we can ask: is there an $x \in (a^n, 2 a^n]$ that satisfies both $\exists b \colon x = a^n + b^n$ and $\exists c \colon x = c^n$?

It is easy to calculate the probability that a random $x \in (a^n, 2 a^n]$ is of the form $a^n + b^n$: there are $a^n$ numbers in the interval and exactly $a$ numbers of the form $a^n + b^n$, namely $a^n + 1, a^n + 2^n, \ldots, a^n + a^n$. So the probability that a random $x \in (a^n, 2a^n]$ is of this form is $\frac {a}{a^n}$.

Similarly, there are $\left \lfloor \left(\sqrt[n]{2} - 1\right) a \right \rfloor$ numbers of the form $c^n$, namely $(a+1)^n, (a+2)^n, \ldots, \lfloor a \sqrt[n]{2}  \rfloor^n$. So the probability that a random $x \in (a^n, 2a^n]$ is of this form is $\frac {\left \lfloor \left(\sqrt[n]{2} - 1\right) a \right \rfloor}{a^n}$.

It is very hard to calculate the probability that both of these events happen at once, but we can apply the presumption of independence and estimate: 

$$
\begin{align*}
    \mathbb{P}_{x}\left(\exists b \colon x = a^n + b^n \wedge \exists c \colon x = c^n\right)
    &\approx \mathbb{P}_{x}\left(\exists b \colon x = a^n + b^n\right)\mathbb{P}_{x}\left(\exists c \colon x = c^n\right) \\
    &= \frac {a}{a^n} \times \frac{\left \lfloor \left(\sqrt[n]{2} - 1\right) a \right \rfloor}{a^n} \\
    &= \frac {\left \lfloor \left(\sqrt[n]{2} - 1\right) a \right \rfloor}{a^{2n - 1}}
\end{align*}
$$

 Note that for $n > 1$ this probability is less than $\frac 1{a^n}$, and so it cannot be the real probability for a randomly chosen $x$ (which will be $\frac 1{a^n}$ as long as there is even a single example). We are unsure whether the true probability is larger or smaller, and this number reflects our uncertainty both about the random choice of $x$ but also about how the $n^{\textnormal{th}}$ powers are distributed in the interval. This is an immediate consequence of the presumption of independence.

Now we want to estimate the probability that there is _any_ $x$ satisfying both properties. For that purpose we apply the presumption of independence again, and treat each event of the form $\left(\exists b \colon x = a^n + b^n\right) \wedge \left(\exists c \colon x = c^n\right)$ as independent from the others That gives us an estimate of: 

$$
\begin{align*}
    \mathbb{P}\left(\exists b, c \colon a^n + b^n = c^n\right)
    &= \mathbb{P}\left(\exists x \colon \left(\exists b \colon x = a^n + b^n\right) \wedge \left(\exists c \colon x = c^n\right)\right) \\
    &= 1 - \mathbb{P}\left(\forall x \colon \neg\left(\left(\exists b \colon x = a^n + b^n\right) \wedge \left(\exists c \colon x = c^n\right)\right)\right) \\
    &\approx 1 - \left(1 - \frac {\left \lfloor \left(\sqrt[n]{2} - 1\right) a \right \rfloor}{a^{2n-1}}\right)^{a^n} \\
    &\approx \frac {\left \lfloor \left(\sqrt[n]{2} - 1\right) a \right \rfloor}{a^{n-1}}
\end{align*}
$$

Finally we want to calculate the probability that this event occurs for _any_ $a > 0$. To do this we apply the presumption of independence one last time: 

$$
\begin{align*}
    \mathbb{P}\left(\exists a, b, c \colon a^n + b^n = c^n\right)
    &= 1 - \mathbb{P}\left(\forall a \colon  \neg \exists b, c \colon a^n + b^n = c^n\right) \\
    &\approx 1 - \prod_{a = 2}^{\infty} \left(1 - \frac {\left \lfloor \left(\sqrt[n]{2} - 1\right) a \right \rfloor}{a^{n-1}}\right)
\end{align*}
$$

 Approximating the infinite product we get:

| $n$ | $\mathbb{P}\left(\exists a, b, c \colon a^n + b^n = c^n\right)$ |
| --- | --- |
| $2$ | $1$ |
| $3$ | $1$ |
| $4$ | $2.8\%$ |
| $5$ | $0.14\%$ |
| $\sum_{n \geq 6}$ | $0.005\%$ |

So we expect there to be a solution for $n \leq 3$ and for there to probably be no solution for $n > 3$.[^note-15] This is because the expected number of solutions is roughly $\sum \frac 1{a^{n-2}}$ which diverges for $n=2$, diverges very slowly for $n = 3$, and converges for $n > 3$.

These estimates are all defeasible and so are subject to revision, even the estimates of $100\%$. The numbers in this table reflect the uncertainty from _chance_, but not the prospect of finding new considerations that show that there is a correlation between the events $x = a^n + b^n$ and $x = c^n$, or between the existence of solutions for different values of $a$.

#### Checking small cases ^checking-small-cases

We estimated a $2.8\%$ chance that $\exists a, b, c \colon a^4 + b^4 = c^4$. This was implicitly made up of intermediate estimates like a $0.5\%$ chance that there is a solution with $b \leq a = 6$. A very simple way that we could revise this probability is by checking some of those concrete intermediate estimates, e.g. by checking whether there is any $b \in \left\{1, 2, 3, 4, 5, 6\right\}$ such that $6^n + b^n$ is a perfect $4^{\textnormal{th}}$ power. If we find one then our probability of a solution will immediately go up to $100\%$, and every time we fail to find one our probability of there being any solution will go down slightly.

In fact there is only a single perfect $4^{\textnormal{th}}$ power in the interval $(6^4, 2 \times 6^4]$, which is $7^4 = 2401$. The difference $7^4 - 6^4$ is strictly between $4^4$ and $5^4$. So $a^4 + b^4 = c^4$ has no solutions with $b \leq a = 6$.

This is technically a failure of our presumption of independence: it turned out that the events $x = 6^4 + b^4$ and $x = c^4$ were anticorrelated. This anticorrelation need not be for any deeper reason—indeed we assigned this outcome a $99.5\%$ probability. It could just be because there are only finitely many $x$ and it just so happened that none of them satisfied both properties.

After making this correction, our probability for any solution with $n = 4$ falls from $2.8\%$ down to $2.3\%$. Checking small cases like this can quickly make us very confident that there are no solutions to $a^n + b^n = c^n$ for _any_ $n > 3$, because the probability of a solution existing decays very rapidly as $a$ and $n$ grow. After checking a modest number of cases we conclude that there is a $99.99\%$ chance that there are no solutions. Of course this estimate is still defeasible, just like our $100\%$ estimates for $n = 2$ or $n = 3$.

#### Correlations between solutions for different values of $a$ ^correlations-between-solutions-for

We assumed that the events $\exists b, c \colon a^n + b^n = c^n$ were independent for different values of $a$. If those events were positively correlated then there could be a smaller probability that one of them is true, and if they were negatively correlated there could be a (slightly) larger probability.

In fact there is at least one obvious and important correlation: for any $k > 1$, we have 

$$
a^n + b^n = c^n \Leftrightarrow (ka)^n + (kb)^n = (kc)^n.
$$

 Turning this around, if $a^n + b^n = c^n$ and $k > 1$ divides both $a$ and $b$, then $\left(\frac ak\right)^n + \left(\frac bk\right)^n = \left(\frac ck\right)^n$ is also a solution.

So if we condition on not having found any solutions with $a' < a$, that means that $x$ _cannot_ simultaneously be of the form $a^n + b^n$ and $c^n$ unless $x$ is relatively prime to $a$. On average[^note-16] this leaves us with only $\frac 6{\pi^2} a^n$ values of $x$ instead of $a^n$, and so decreases our total estimate for the probability of a solution by $\frac 6{\pi^2} = 0.61\ldots$.

Now our estimate for $n = 4$ has fallen from $2.3\%$ to $1.4\%$.

#### Correlations between $x = a^n + b^n$ and $x = c^n$ ^correlations-between-x-a

We have assumed that the events $\exists b \colon x = a^n + b^n$ and $\exists c \colon x = c^n$ are independent if $a$ and $b$ are relatively prime. But there are at least a few reasons for them to be correlated, and as we notice these considerations we should change our prediction for the probability that both of them occur:

-   Numbers of the form $a^n + b^n$ are not uniformly distributed over the range $(a^n, 2a^n]$, they are much more common closer to the bottom of the range. Similarly, numbers of the form $c^n$ are somewhat more common close to the bottom end of the range. A random number in the interval $(x - \varepsilon, x+ \varepsilon)$ has a probability of about $\frac 1{n x^{(n-1)/n}}$ of being a perfect $n^{\textnormal{th}}$ powers (since the difference between consecutive $n^{\textnormal{th}}$ powers in this range is roughly $n x^{(n-1)/n}$) and about $\frac 1{n (x - a)^{n/(n-1)}}$ of being of the form $a^n + b^n$. If we take the sum over a large number of intervals of this form, we converge to the estimate 
    
    $$
    \int_{x = a^n}^{2 a^n} \frac 1{n x^{(n-1)/n}} \times \frac 1{n(x-a)^{(n-1)/n}} dx.
    $$
    
     Plugging $n = 4$ we get a number about $18\%$ higher than our previous estimate of $\frac{\sqrt[4]{2} - 1}{a^{n-2}}$, and so our estimate rises from $1.4\%$ to $1.7\%$.
    
-   The $n^{\textnormal{th}}$ powers are not not uniformly distributed modulo primes, and so this can introduce another correlation between the events $x = a^n + b^n$ and $x = c^n$. For example, every $4^{\textnormal{th}}$ power is congruent to either $0$ or $1$ mod $5$. In order to get a more precise estimate for $\mathbb{P}\left(x = a^n + b^n \wedge x = c^n\right)$, we can compute: 
    
    $$
    \begin{align*}
                &\mathbb{P}\left(\exists b \colon x = a^n + b^n \wedge \exists c \colon x = c^n\right)\\
                &=\sum_{r} \mathbb{P}\left(x = r\; \mathrm{mod}\;{5}\right) \mathbb{P}\left(\exists b \colon x = a^n + b^n \wedge \exists c \colon x = c^n\left\vert x = r\; \mathrm{mod}\;{5}\right.\right) \\
                &\approx\sum_{r} \mathbb{P}\left(x = r\; \mathrm{mod}\;{5}\right)
    \mathbb{P}\left(\exists b \colon x = a^n + b^n\left\vert x = r\; \mathrm{mod}\;{5}\right.\right) \mathbb{P}\left(\exists c \colon x = c^n\left\vert x = r\; \mathrm{mod}\;{5}\right.\right)
    \end{align*}
    $$
    
     This sum leads to an estimate $4/3$ higher than our previous estimate[^note-17] and so brings us from a $1.7\%$ probability of a solution up to $2.2\%$. There are similar adjustments for other divisors. which do not point in a consistent direction.
    

#### The case $n = 3$ ^the-case-n-3

We predicted that $a^n + b^n = c^n$ almost surely has a solution for $n = 2, 3$. For $n = 2$ we predict a large number of solutions and we can quickly find one, e.g. $3^2 + 4^2 = 5^2$. For $n = 3$ we predict a very small number of solutions—we expect about $1$ solution for $a, b \leq 100$, $2$ solutions for $a, b \leq 10000$, and $3$ solutions for $a, b \leq 1000000$. But if we actually check all values up to a million, we do not find any. This is not decisive evidence that we have made a mistake—we assigned this outcome a probability of about $1 / e^3 \approx 5\%$—but it does suggest that something may be wrong.

We have already seen that there is one correlation between the equation having solutions for different values of $a, a'$. Taking that correlation into account only decreased the expected number of solutions by a factor of $\frac 6{\pi^2}$, but there are other more subtle correlations.

For example, if $a^3 + b^3 = c^3$, then we can compute that: 

$$
\begin{equation}
    \left(a^9 + 6 a^3 b^3 + 3 b^3 a^6 - b^9\right)^3 + \left(-a^9 + 3 a^6 b^3 + 6 a^3 b^6 + b^9\right)^3 = \left(3abc(a^6 + a^3 b^3 + b^3)\right)^3
\tag{2}
\end{equation}
$$

 and hence a single solution generates an infinite family of solutions by a second mechanism different from multiplying all of $a$, $b$, and $c$ by a constant $k > 1$.

This suggests that our independence assumption may break down. In fact, by doing some much more careful analysis we can show that _every_ large solution to $a^3 + b^3 = c^3$ is generated by applying Equation 2 to smaller solutions, and hence if there are no solutions for small values of $a$ then there are no solutions at all.

This gives us a much more dramatic revision of a heuristic conclusion than anything we had seen so far. Observing Equation 2 is much easier than proving Fermat’s last theorem (it was done centuries earlier) but it is still extremely non-trivial and causes us to revise the probability of a solution existing from $1$ down to $0$.

This revision is very distinctive to the equation $a^3 + b^3 = c^3$, and typically when the naive heuristic suggests a very small number of solutions this is correct. For example, in 1769 Euler conjectured that there would also be no solutions to 

$$
a^4 + b^4 + c^4 = d^4.
$$

 In this case our basic heuristic argument again predicts that there should be infinitely many solutions but that they should be very sparse. In fact Euler’s conjecture was disproven in 1988 \[10\]. The smallest counterexample (from \[12\]) is: 

$$
95800^4 + 217519^4 + 414560^4 = 422481^4.
$$

### Hamiltonian cycles ^hamiltonian-cycles

A weighted directed graph $G$ is a set of vertices $V$ and an edge-weighting function $E\colon V \times V \rightarrow \mathbb{R}$. (we indicate that an edge is absent by taking $E\left(u, v\right) = 0$). A _Hamiltonian cycle_ in $G$ is a cycle that passes through each vertex in $G$ exactly once, and the _weight_ of a cycle is the product of the edge weights.

For any given graph $G$, we can ask:

**Question 3**. _What is the total weight of all Hamiltonian cycles in $G$?_

Even approximating the total weight of all Hamiltonian cycles is an extremely difficult problem.[^note-18] In this section we discuss heuristic estimators for this quantity.

A weighted directed graph is shown. If $u$ and $v$ are not connected by an arrow then $E\left(u, v\right) = 0$. A Hamiltonian cycle with weight $-1 \times 3 \times 2 \times 2 \times -3 = 36$ is highlighted in red.

#### The naive estimate ^the-naive-estimate

Let $W = \frac 1{n(n-1)} \sum_{u, v} E\left(u, v\right)$ be the average weight of a randomly chosen edge from $G$ (including $0$ weights). If we pick $n$ edges from $G$ independently at random, then the expected product of their weights is exactly $W^n$.

There are $(n-1)!$ Hamiltonian cycles. If we assume that the average weight of these cycles is the same as the average weight of a random set of $n$ edges, then the total weight of all Hamiltonian cycles is 

$$
S_0 = (n-1)! W^n.
$$

 This corresponds to the presumption that if we pick $n$ edges uniformly at random, their total weight is uncorrelated with whether they are a Hamiltonian cycle.

#### Estimates based on incoming or outgoing edges ^estimates-based-on-incoming

Every Hamiltonian cycle must have exactly one outgoing edge from each vertex $u$. So if we notice that a vertex $u$ has no outgoing edges with non-zero weight then every Hamiltonian cycle has weight zero, and the probability of being a Hamiltonian cycle is _not_ independent of the weight. More generally, if someone points out that certain vertices have a very small weight of outgoing edges, then it introduces a correlation between weight and being a Hamiltonian cycle. We can incorporate this correction to get a more precise estimate.

Instead of picking $n$ edges at random, we could pick an outgoing edge from each vertex at random. Let $W_{u\rightarrow} = \frac 1{n-1} \sum_v E\left(u, v\right)$ be the expected weight of a random outgoing edge from $u$. Then if we pick one outgoing edge from each vertex, the expected product of their weights is $\prod_u W_{u\rightarrow}$.

For $n$ edges chosen in this way, we could again assume that the weight of the set is independent of whether it is a Hamiltonian cycle. If so, then the total weight of all Hamiltonian cycles would be: 

$$
S_{\textnormal{out}} = (n-1)! \prod_u W_{u \rightarrow}.
$$

 We can confirm empirically that this gives us a better estimator for small random graphs.

We could have done the same thing for incoming edges instead of outgoing edges, obtaining the estimate 

$$
S_{\textnormal{in}} = (n-1)! \prod_v W_{\rightarrow v}
$$

 where $W_{\rightarrow v} = \sum_u E\left(u, v\right)$.

#### Combining $S_{\textnormal{in}}$ and $S_{\textnormal{out}}$ ^combining-s-textnormal-in

The two estimates $S_{\textnormal{out}}$ and $S_{\textnormal{in}}$ can be very different from each other, and even have different signs.

This illustrates one of the core challenges in constructing a heuristic estimator: if we are given two different arguments $\pi_1$ and $\pi_2$, how can we combine them to arrive at an estimate that reflects all the information from both? If there were cases without any intuitively plausible way to do this kind of merging, then it would provide a serious obstacle to our goal of defining a heuristic estimator that aligns with our intuitions about validity.

In this case there turns out to be a relatively simple way to integrate the estimates by applying the presumption of independence one more time.

First we will describe how to do this when all of the edge weights are positive, and then describe how to adapt it to handle negative weights.

We imagine selecting a sequence of $n$ (not necessarily distinct) edges each with probability proportional to its weight. Let $E_{\textnormal{cycle}}$ be the event that these edges form a cycle. The total weight of Hamiltonian paths is exactly equal to $n^n(n-1)^n W^n \mathbb{P}\left(E_{\textnormal{cycle}}\right)$, and so we can restate our goal as estimating $\mathbb{P}\left(E_{\textnormal{cycle}}\right)$. Our original presumption of independence was that $\mathbb{P}\left(E_{\textnormal{cycle}}\right) \approx \frac{n^n (n-1)^n}{(n-1)!}$, the same as if we had picked the edges uniformly at random.

We can also consider the events $E_{\textnormal{out}}$ and $E_{\textnormal{in}}$ that our random set of edges has exactly one outgoing edge from each vertex or exactly one incoming edge to each vertex. We know that $E_{\textnormal{cycle}}\subset E_{\textnormal{out}}\cap E_{\textnormal{in}}$.

The estimate $S_{\textnormal{out}}$ improves upon $S$ by exactly computing $\mathbb{P}\left(E_{\textnormal{out}}\right)$ and then assuming that $\mathbb{P}\left(E_{\textnormal{cycle}}\left\vert E_{\textnormal{out}}\right.\right) = \frac {(n-1)!}{(n-1)^n}$ (which is equivalent to saying that for a uniformly random set of edges satisfying $E_{\textnormal{out}}$, the product of the weights is independent from whether the edges form a cycle). Similarly, $S_{\textnormal{in}}$ computes $\mathbb{P}\left(E_{\textnormal{in}}\right)$ and then assumes $\mathbb{P}\left(E_{\textnormal{cycle}}\left\vert E_{\textnormal{in}}\right.\right) = \frac{(n-1)!}{(n-1)^n}$.

We could get a better estimate if we could exactly compute $\mathbb{P}\left(E_{\textnormal{in}}\cap E_{\textnormal{out}}\right)$, and then assume that $\mathbb{P}\left(E_{\textnormal{cycle}}\left\vert E_{\textnormal{in}}\cap E_{\textnormal{out}}\right.\right) = \frac 1n$ (which is equivalent to saying that for a uniformly random set of edges satisfying $E_{\textnormal{out}}\cap E_{\textnormal{in}}$, the product of weights is independent from whether the edges form a cycle).

We cannot compute $\mathbb{P}\left(E_{\textnormal{out}}\cap E_{\textnormal{in}}\right)$ but once we are looking at the problem this way it is easy to apply the presumption of independence again to estimate $\mathbb{P}\left(E_{\textnormal{in}}\cap E_{\textnormal{out}}\right) \approx \mathbb{P}\left(E_{\textnormal{in}}\right)\mathbb{P}\left(E_{\textnormal{out}}\right)$.

Putting it all together, this gives us the estimate 

$$
\begin{equation}
S_{\textnormal{in+out}} = (n-1)! \frac{S_{\textnormal{in}} S_{\textnormal{out}}}{S_0}.
\tag{3}
\end{equation}
$$

This estimate is based on assuming independence for edges sampled with probability proportional to their weight, so it only applies if all edge weights are positive. To generalize, we can consider the estimates $S_{\textnormal{in}}^+, S_{\textnormal{out}}^+, S_0^+$ consisting only of cycles where the product of edge weights is positive, and compute $S_{\textnormal{in+out}}^+$ using the analog of Equation 3. Separately we can compute $S_{\textnormal{in+out}}^-$ consisting of only terms where the product of edge weights is negative, and then define $S_{\textnormal{in+out}} = S_{\textnormal{in+out}}^+ - S_{\textnormal{in+out}}^-$. It turns out to be straightforward to compute all of these quantities, although this methodology can lead to particularly large multiplicative errors in cases where $S_{\textnormal{in+out}}^+ \approx S_{\textnormal{in+out}}^-$ (as expected given that the problem is #P-hard).

#### The $E_{\textnormal{unique}}$ correction ^the-e-textnormal-unique

If we evaluate the estimator $S_{\textnormal{in+out}}$, we find that it is better than either $S_{\textnormal{in}}$ or $S_{\textnormal{out}}$ for many distributions over graphs. But there are some natural distributions (like power law distributed weights) where it is actually much worse than even the naive estimator $S_0$. One of our motivating beliefs, discussed in more detail in Section [[#^soundness|11]], is that _whenever_ we observe this kind of empirical failure it means there is some heuristic argument that we are overlooking.

In this case the story is relatively simple. We assumed that the events $E_{\textnormal{in}}$ and $E_{\textnormal{out}}$ were independent if we sample sets of edges with probability proportional to their weights. But these two events have an obvious correlation: we are sampling sequences of edges with replacement, and if we pick the same edge twice then _neither_ of these events will be true. When the distribution of edge weights is heavy-tailed, this is a very common reason for $E_{\textnormal{in}}$ or $E_{\textnormal{out}}$ to fail, and so the independence assumption is badly wrong.

Let $E_{\textnormal{unique}}$ be the event that no edge appears twice. Rather than assuming that $E_{\textnormal{in}}$ and $E_{\textnormal{out}}$ are independent, we would like to assume that they are conditionally independent given $E_{\textnormal{unique}}$. That is, we would like to estimate: 

$$
\begin{align*}
    \mathbb{P}\left(E_{\textnormal{in}}\cap E_{\textnormal{out}}\right)
    &= \mathbb{P}\left(E_{\textnormal{unique}}\right) \mathbb{P}\left(E_{\textnormal{in}}\cap E_{\textnormal{out}}\left\vert E_{\textnormal{unique}}\right.\right) \\
    &\approx \mathbb{P}\left(E_{\textnormal{unique}}\right) \mathbb{P}\left(E_{\textnormal{in}}\left\vert E_{\textnormal{unique}}\right.\right) \mathbb{P}\left(E_{\textnormal{out}}\left\vert E_{\textnormal{unique}}\right.\right) \\
    &= \frac{\mathbb{P}\left(E_{\textnormal{in}}\right) \mathbb{P}\left(E_{\textnormal{out}}\right)}{\mathbb{P}\left(E_{\textnormal{unique}}\right)}.
\end{align*}
$$

 This suggests that we should multiply the estimator $S_{\textnormal{in+out}}$ by $\mathbb{P}\left(E_{\textnormal{unique}}\right)$.

Computing $E_{\textnormal{unique}}$ exactly is not easy, but we can again give a heuristic estimator for it. For a given edge $(u, v)$, the probability of $(u, v)$ appearing either $0$ or $1$ times in a random sequence is exactly $(1 - p)^n + n p (1 - p)^{n-1}$, where $p = \frac {E\left(u, v\right)}{W}$ is the probability that $(u, v)$ is picked at each step.

If we assume that these events are independent across all the edges $(u, v)$, then we obtain an estimate for $\mathbb{P}\left(E_{\textnormal{unique}}\right)$. Multiplying $S_{\textnormal{in+out}}$ by this estimate for $\mathbb{P}\left(E_{\textnormal{unique}}\right)$ results in a new estimate for the sum of the Hamiltonian cycle weights, and empirically we find that the resulting estimate is typically significantly better than either $S_{\textnormal{in}}$ or $S_{\textnormal{out}}$.

Of course these events are not really independent (since if $(u, v)$ appears $0$ or $1$ times then it slightly decreases the probability that another edge $(u', v')$ will appear $0$ or $1$ times), but the assumption is quite close in many cases. If a new heuristic argument led us to have a better estimate for $\mathbb{P}\left(E_{\textnormal{unique}}\right)$, then we would use that improved estimate instead.

#### Considering concrete paths ^considering-concrete-paths

A very different way to heuristically argue is to exhibit particular Hamiltonian cycles and compute their weight.

That is, we are interested in the sum 

$$
S = \sum_{x \in \mathcal{X}} f\left(x\right)
$$

 where $\mathcal{X}$ is the space of Hamiltonian cycles and $f$ is the weight.

In the past sections we have shown a series of increasingly sophisticated ways to derive a heuristic estimate for the average value $f\left(x\right)$ over $\mathcal{X}$. Write $\widetilde{\mathbb{E}}\left(f, \pi\right)$ for our heuristic estimate of the average, however we arrived at that estimate.

A particularly simple heuristic argument $\pi_x$ consists of a concrete $x$ together with a calculation of the value $f(x)$. For a reasonable heuristic verifier, we claim we should have: 

$$
\begin{equation*}
    \widetilde{\mathbb{E}}\left(S, \pi, \pi_{x_1}, \ldots, \pi_{x_k}\right) =
    \left|\mathcal{X}\right| + \sum_{i = 1}^k \left(f(x_i) - \widetilde{\mathbb{E}}\left(f, \pi\right)\right)
\end{equation*}
$$

 That is, when $\widetilde{\mathbb{E}}$ sees that a particular value $f(x_i)$ is $\delta_i$ higher than it expected, it increases its estimate for $S$ by $\delta_i$.[^note-19]

We think that $\widetilde{\mathbb{E}}$ should clearly change its estimate in this way. You could also argue that it should change its estimate in a more fundamental way: if $f(x_i)$ was higher than $\widetilde{\mathbb{E}}\left(f, \pi\right)$, it suggests that $\widetilde{\mathbb{E}}\left(f, \pi\right)$ should be larger. This is the underlying intuition behind a Monte Carlo estimate—the random values we explore give us a reasonable indication of the typical behavior of $f$, and so we should update our estimate for $S$ based not only on the tiny number of values we saw explicitly but on the assumption that unobserved values will behave similarly.

Roughly speaking, we consider the linear contribution from $f(x_i) \rightarrow S$ to be a “causal” contribution, roughly mirroring traditional deduction where we evaluate individual factors that directly make a statement true or false. In contrast, we consider the contribution from $f(x_i)$ to $\widetilde{\mathbb{E}}\left(f\right)$ to be an _inductive_ update, where we change our beliefs about $\widetilde{\mathbb{E}}\left(f\right)$ by observing evidence about $f$’s behavior and inferring that there are likely to be common factors that affect its behavior in every case. We are particularly interested in _deductive_ heuristic verifiers that do not make this kind of inductive update. We explore this distinction in much more detail in Appendix [[#^inductive-vs-deductive-arguments|10]].

### Billiard balls ^billiard-balls

**Question 4**. _Consider 15 perfectly elastic balls with radius 1 centimeter on a frictionless pool table measuring 1 meter by 2 meters. A line is drawn down the middle of the table dividing it into two 1 meter by 1 meter squares. Suppose that we choose the initial positions of the balls uniformly at random from the left half of the table, and we give each ball an initial velocity of 1 meter per second in a random direction. After 20 seconds, what is the probability that a majority of the 15 balls will be back on the left half of the table?_

One way we could estimate the answer is by performing a set of simulations with random initial conditions. We find that unsatisfying for two reasons. First, it performs badly if we want to get precise estimates (e.g. for estimating probabilities very close to $0$ or very small biases away from a 50/50 chance). More importantly but harder to formalize, in Appendix [[#^inductive-vs-deductive-arguments|10]] we try to explain the intuitive sense in which a deterministic deductive argument tells us something that we do not learn from doing Monte Carlo estimate.

So in this section we will present a deterministic but heuristic alternative to the Monte Carlo estimate.

#### Stochastic differential equations ^stochastic-differential-equations

The state of the table at any given time is described by $60$ numbers: the $x$ and $y$ position and velocity of each of the $15$ balls. It is easy to describe the initial configuration of the pool balls as a distribution over this space, but as time passes the probability distribution quickly becomes extremely messy and has no short description.

One way we can track the evolution is by making a set of independence assumptions in order to describe the this distribution more compactly. The simplest independence assumption is that all $60$ of these numbers are independent at any given time. We will take a slightly more accurate assumption, where we consider the correlation between a single ball’s position and velocity but assume that different balls are independent.

Under this assumption we need to track a distribution $p^t$ over tuples $(x, y, \dot{x}, \dot{y}) \in \mathbb{R}^4$. We’ll define coordinates so that the table’s walls are at $x = \pm 1$, $y = 0$, and $y = 1$, with the left half of the table being the set $x < 0$.

Initially, $p^0$ has $(x, y)$ uniform over $[-1, 0] \times [0, 1]$ and $(\dot{x}, \dot{y})$ uniform over the unit circle.

If we ignore collisions between balls, then the evolution of $p^t$ is very simple. Over a short interval of time $\Delta t$, we have: 

$$
\begin{align*}
    x &\gets x + (\Delta t) \dot{x} \\
    y &\gets y + (\Delta t) \dot{y}
\end{align*}
$$

 If either of these positions goes outside of the billiard table $[-1, 1] \times [0, 1]$, we reflect it across the wall to put it back in the table and we negate the associated velocity.

The collisions between balls introduce a much more complex stochastic change to $\dot{x}$ and $\dot{y}$. This is where we use the presumption of independence. For a given pair of not-initially-overlapping tuples of positions and velocities, $B_0 = (x_0, y_0, \dot{x}_0, \dot{y_0})$ and $B_1 = (x_1, y_1, \dot{x}_1, \dot{y_1})$, it’s easy to compute whether two balls with those parameters would collide over the next $\Delta t$ seconds and if so what the resulting velocities would be. The limiting rate of collision as $\Delta t \rightarrow 0$ is 

$$
c\left(B_0, B_1\right) =
    \left(\dot{x}_0 - \dot{x}_1\right) \left(x_0 - x_1\right) + \left(\dot{y}_0 - \dot{y}_1\right)\left(y_0 - y_1\right)
$$

 if $B_0$ and $B_1$ are exactly $2$ centimeters apart and $0$ otherwise. If a collision occurs, the new velocity for ball $0$ is $\left(\dot{x}_c(B_0, B_1), \dot{y}_c(B_0, B_1)\right)$, where 

$$
\begin{align*}
    \dot{x}\left(B_0, B_1\right) &= \dot{x_0} + c\left(B_0, B_1\right) (x_0 - x_1) \\
    \dot{y}\left(B_0, B_1\right) &= \dot{y_0} + c\left(B_0, B_1\right) (y_0 - y_1)
\end{align*}
$$

Given a probability distribution $p^t$ over $\mathbb{R}^4$ and a given tuple $B = (x, y, \dot{x}, \dot{y})$, let $S$ be the set of tuples $B'$ that are just touching $B$. We can compute the limiting probability of a collision with another ball in the next $\Delta t$ seconds, as $\Delta t \rightarrow 0$, as: 

$$
C^t(B) = 14 \int_{B' \in S}
p^t\left(B'\right) c\left(B, B'\right) dB'.
$$

 We’ve picked up a factor of $14$ because there are $14$ other balls with which any given ball could collide.

If a collision occurs, the distribution over new velocities is the distribution over $\left(\dot{x}\left(B, B'\right), \dot{y}\left(B, B'\right)\right)$ for $B'$ sampled from $S$ with probability proportional to $p^t\left(B'\right)c\left(B, B'\right)$. Again, this can be computed as a $3$\-dimensional integral of $p^t$.

We now have a set of stochastic differential equations on $\mathbb{R}^4$ with jumps corresponding to collisions; the presumption of independence has reduced a $60$\-dimensional problem to a $4$\-dimensional problem. Although there are better approaches, we can approximate the solution to such equations by the “brute-force” method of dividing $\mathbb{R}^4$ into $O\left(\frac 1{\varepsilon^4}\right)$ small hypercubes with side length $\varepsilon$ and tracking how each of them evolves over timesteps of length $\varepsilon$. This gives us an approximation to the final distribution to within $O\left(\varepsilon^2 t\right)$ error in time $O\left(\frac {t}{\varepsilon^6}\right)$.

Once we have a solution in hand we can compute the probability $p$ that any given pool ball is on the left half of the table. We find that the result decays exponentially with $t$ and by 20 seconds it is extremely close to $\frac 12$. Then to estimate the probability that most balls are on the left half of the table we can apply the presumption of independence again.

Note that this algorithm runs in time independent of the number of pool balls, and so we could have applied the same analysis to a set of $10^{20}$ gas molecules rather than $15$ pool balls. For such systems even doing a Monte Carlo estimate would be intractable.

#### Defeasibility ^defeasibility

These differential equations are only heuristically accurate, and there could be important patterns that are destroyed by the presumption of independence.

A simple example is that if _all_ the pool balls are initially traveling almost exactly straight up and down, and if they start off with sufficiently different $x$ positions, then they will stay on the left half of the table and moreover they will never collide and so never change their velocity. It turns out that for large $t$ this possibility drives most of the bias towards the left half of the table—for large $t$ it suggests a bias of roughly $O\left(\frac {1}{t^{15}}\right)$, whereas the bias from the estimate above decays exponentially with $t$.[^note-20] This possibility is completely ignored by the presumption of independence, because it gives any given pair of balls a new independent chance to collide in any given timestep.

As a much more exotic example, this kind of heuristic estimate would give completely wrong conclusions about a physical system that gives rise to complex life. Thus _proving_ that any estimate of this form is accurate effectively requires proving that the evolution of life is rare in the system we’re considering. For interesting large systems that seems incredibly challenging,[^note-21] and helps illustrate why proofs will typically be impossible.

## Inductive vs deductive arguments ^inductive-vs-deductive-arguments

### Proof vs evidence ^proof-vs-evidence

Consider the problem of estimating $\mathbb{P}\left(C\right)$, the probability that a circuit $C$ outputs $1$ for uniformly random inputs. Rather than using a heuristic estimator, we could use a Monte Carlo estimate: draw some inputs $\left\{z_i\right\}_i$ at random and evaluate the empirical mean of $C\left(z_i\right)$.

If we test 1000 samples and find that $C\left(z\right) = 1$ for every one of them, then that gives us strong evidence that $\mathbb{P}\left(C\right)$ is close to $1$. In fact, this is much more convincing than a heuristic estimate that $\mathbb{P}\left(C\right)\approx 1$, because there is no way we could have overlooked a key consideration.

Yet we find this estimate unsatisfying and think it is still meaningful to look for a heuristic argument for $\mathbb{P}\left(C\right)$. The Monte Carlo estimate gives us evidence that there is some structural feature of $C$ causing it to output $1$ most of the time, but it doesn’t help us see what that structure is—it doesn’t show us _why_ $C$ outputs $1$. We are left with a mystery that we could explain by studying the circuit further.

In contrast, we believe that a short **proof** that $\forall z \colon C\left(z\right) = 1$ would illuminate the relevant structure of $C$ and at least partially explain the phenomenon. We don’t know how to formalize this idea, but we can point to some related observations:

-   A proof shows us what properties of $C$ led it to always output $1$, and so show us how we could change $C$ while preserving this property.
    
-   We can make a Monte Carlo estimate regardless of how well we understand the circuit $C$, and in fact we could get the same estimate even if $C$ was cryptographically obfuscated. But efficiently proving that $C$ always outputs $1$ requires de-obfuscating it.[^note-22] Obfuscation is an extreme case, but more generally it seems like proofs require us to identify the important structure in $C$ rather than leaving it implicit.
    
-   Intuitively proofs do often “feel like” explanations once we understand them,[^note-23] even if they are initially opaque. This is a relatively common intuition amongst mathematicians even if it lacks a clear philosophical basis, though note the important quantitative caveat about long proofs in Section [[#^explanation-seems-to-be|10.6]].
    

### Can heuristic arguments also be explanations? ^can-heuristic-arguments-also

When discussing the difference between proofs and Monte Carlo estimates it is tempting to focus on the certainty that proofs provide: even if $C(z) = 1$ in 1000 random cases the best we can say is that $\mathbb{E}\left[C\right]$ is probably not much less than $0.999$, and it could even turn out that $\mathbb{E}\left[C\right] = 0.5$ and we just happened to draw an extreme set of samples.

But the fact that proofs give us certainty seems orthogonal to any of the advantages discussed in the last section. The point is that a proof elucidates the structure of $C$, not that it rules out the possibility of error. If that’s the case, then a heuristic argument could potentially provide the same kind of elucidation even though it doesn’t provide the certainty.

Our intuition is that heuristic arguments based on the presumption of independence do show us “why” the corresponding statement is true. For example, we think that if the twin prime conjecture is true it is likely to be “because” of the argument presented in Section [[#^example-the-twin-prime|1]], and we should not necessarily expect to discover some further facts about the distribution of primes.[^note-24]

However, not all heuristic estimators have this property: based on the definition of “heuristic estimator” in Section [[#^heuristic-estimators|3]], a Monte Carlo estimator for $X$ would be an example of a valid heuristic estimator.

So we would often like to restrict our attention to a narrower class of heuristic estimators that we will call _deductive_ estimators which mirror the deductive structure of proofs (in contrast with what we describe as the _inductive_ structure of a Monte Carlo estimate). Unsurprisingly we can’t define this notion formally either. But we can use it to inform the choice of examples for the formalization problem posed in Section [[#^formalizing-intuitively-valid-heuristic|5]], and to guide our search for algorithms.

### Randomization does not capture this distinction ^randomization-does-not-capture

Monte Carlo estimates are inherently random while proofs are inherently deterministic. So perhaps if we require a heuristic estimator to be deterministic then we could ensure that heuristic estimators have some of the same explanatory benefit as proofs.

We think this doesn’t work. Consider a pseudorandom Monte Carlo algorithm that estimates $\mathbb{E}\left[C\right]$ by evaluating $C$ at the values $f\left(0\right), f\left(1\right), \ldots, f\left(k\right)$ for some complicated and random-looking function $f$.

It is strongly believed that there exist formally pseudorandom functions such that this pseudorandom Monte Carlo estimate will also converge to the correct value for _every_ circuit $C$. Yet the pseudorandom Monte Carlo estimate tells us no more than the random one did. The failure to show _why_ $C$ outputs $1$ wasn’t due to the use of randomness, but due to the nature of the inference about $C$.

This leaves us searching for a better way to formalize the difference between a Monte Carlo estimate and a proof.

### Induction vs deduction ^induction-vs-deduction

An illustration of a causal model. Arrows represent a direct dependence of one variable on another. To fully specify a model, we would need to describe the domain of each variable and the conditional probability distributions $p\left(x_2\left\vert x_1\right.\right)$, $p\left(x_3\left\vert x_1, x_2\right.\right)$, $p\left(x_4\left\vert x_2, x_3\right.\right)$, and $p\left(x_1\right)$.

Our intuitive distinction between induction and deduction is heavily informed by the analogy of reasoning in a causal model. A causal model defines a probability distribution over a set of variables $\left\{x_1, \ldots, x_T\right\}$ by defining the conditional probability distributions for each variable $x_t$ given a set of values for the previous variables $\left\{x_1, \ldots, x_{t-1}\right\}$. We often imagine the case where each variable $x_t$ depends directly on only a few of the variables $x_i$ for $i < t$, and is conditionally independent of the others; we illustrate such a model in Figure 4. Many reasoning problems can be viewed as inferring the conditional probability distribution of a variable $x_i$ given the values of some other variables $\left\{x_j\right\}$.

We can divide up this inference problem into two parts:

Forwards.

Given values for some early variables $\left\{x_1, x_2, \ldots, x_t\right\}$, we can repeatedly apply the conditional probability definition in order to compute the distribution of each of $\left\{x_{t+1}, x_{t+2}, \ldots, x_T\right\}$ given $\left\{x_1, \ldots, x_t\right\}$.

Backwards.

If we’re given a some later value $x_t$ and want to infer the distribution over an earlier value $x_1$, then we need to also solve an inverse problem: for each way possible value of $x_1$ we compute $p\left(x_t\left\vert x_1\right.\right)$, and then we apply Bayes’ rule to compute $p\left(x_1\left\vert x_t\right.\right) \propto \frac{p\left(x_t\left\vert x_1\right.\right)}{p\left(x_1\right)}$.

Most realistic problems require both kinds of reasoning. For example, if I want to know $p\left(x_7\left\vert x_4\right.\right)$, I need to infer the distribution over $\left\{x_1, x_2, x_3\right\}$ given the value of $x_4$, and then use those to compute the distribution over $x_5$, then $x_6$, then $x_7$.

These two steps aren’t always or even usually distinguished in inference algorithms, but we still find it helpful to think of the two separately. We think of the first as “reasoning forwards” from premises to conclusions, in a way that closely mirrors the flow of logical implication in a proof. We think of the second as “reasoning backwards” and trying to infer the most likely explanation for some data.

In a causal model we are working with _bona fide_ probability distributions, whereas a heuristic estimator $\widetilde{\mathbb{E}}\left(X\right)$ is working with its uncertainty about some deterministic quantity $X$. Despite the differences, we find the analogy to causal models helpful and we still expect the same kind of “forwards” and “backwards” reasoning to occur in realistic examples of reasoning about unknown but deterministic quantities $X$.

Now we can explain why we think a Monte Carlo estimate for $\mathbb{E}\left[C\right]$ involves “inductive” reasoning. The intuitive picture is illustrated in Figure 5; the circuit $C$ has a mathematical definition, which logically entails some facts about $C$, which in turn cause it to output $0$ or $1$ more often. A Monte Carlo estimate doesn’t try to discover those underlying facts, but instead observes various values $C\left(z_i\right)$ that are “downstream” of facts about $C$. If it observes a bias then it implicitly infers that there must have been some fact about $C$ leading to a bias, and uses that to make predictions about new values $C\left(z_i\right)$.

We are instead interested in focusing on what we will call _deductive_ heuristic estimators, which deduce the relevant structural facts about $C$ directly from the definition, rather than inferring their existence from downstream consequences.

In the analogy to causal models, a heuristic estimator is more like calculating the prior distribution over $x_2$ by calculating $p\left(x_1\right)p\left(x_2\left\vert x_1\right.\right)$, whereas a Monte Carlo estimate is more like observing $x_3$ and then doing a Bayesian update to adjust $p\left(x_2\left\vert x_3\right.\right)$ by the likelihood ratio $p\left(x_3\left\vert x_2\right.\right)$.

Intuitively the structure of $C$ is “logically upstream” of particular computations $C\left(z_i\right)$.

We expect realistic reasoning to involve both this kind of “forwards” reasoning from premises to conclusions, and “backwards” Bayesian updating to adjust that prior based on observations.[^note-25] We are particularly interested in deductive heuristic estimators, which try to isolate one part of this process, for a few reasons:

-   We believe that less work has been put into formalizing the deductive part of the process, and the existence of simple arguments that are convincing but totally unformalized suggests that there may be significant low-hanging fruit for formalization. In contrast there is a much larger literature on approximate inference that focuses on the the inductive part of the problem.
    
-   We think that it is very unlikely that there’s a simple formalization of all reasoning about uncertain quantities. The purely deductive fragment seems much simpler and more likely to be governed by general principles (in analogy with logical deduction).
    
-   We are interested in understanding “why” ML systems behave in a certain way, and tentatively hope that deductive heuristic estimators can shed some light on such questions for the reasons discussed at the beginning of this section.[^note-26]
    

### Example: estimating sums ^example-estimating-sums

In Section [[#^considering-concrete-paths|9.2.5]] we discussed heuristic estimators for a sum $S = \sum_{x \in \mathcal{X}} f(x)$, and we considered heuristic arguments that simply compute $f\left(x_i\right)$ for concrete values $x_i$.

We think that such arguments should change the estimates for **both** inductive and deductive reasons, but the quantitative nature of the change is very different:

-   For a deductive heuristic estimator, learning that $f\left(x_i\right)$ is $1$ unit larger than we thought directly implies that $S$ will be $1$ unit larger than we thought—because $f(x_i)$ is one of the terms in $S$.
    
-   If we are also reasoning inductively, then each value $f\left(x_i\right)$ also provides _evidence_ about the other values $f\left(x_j\right)$. Thus seeing 1000 random examples and finding they all have a value of $7$ can lead to an estimate for $S$ of $7\left|\mathcal{X}\right|$, even if $\left|\mathcal{X}\right| = 2^{256}$ so that the direct impact of these examples is negligible.
    

The inductive reasoning generally leads to _much_ larger revisions. But it also behaves qualitatively differently in several important ways:

-   The size of the inductive update depends a lot on how many examples we’ve already seen (and on our prior distribution over the behavior of $f$) whereas the size of the deductive update depends only on the difference between the observed value $f\left(x_i\right)$ and our previous best guess $\widetilde{\mathbb{E}}\left(f\left(x_i\right)\right)$.
    
-   The inductive update depends on how the $x_i$ was chosen and whether it is representative of other values, whereas the deductive update depends only on the fact that $f\left(x_i\right)$ appears in the sum $S$.
    

### Explanation seems to be quantitative ^explanation-seems-to-be

We can always prove $\forall z \colon C\left(z\right) = 1$ in a completely unenlightening way by exhaustively checking every possible value of $z$.

In our view an exhaustive proof is a valid deductive heuristic estimate, and does constitute an explanation of the underlying phenomenon—we just consider it a _bad_ explanation in a quantitative sense. In this section we’ll try to lay out some of the underlying intuitions even though we can’t formalize them.

An exhaustive proof has $2^n$ steps, one for each input to $C$, and each of these steps seems to work out “by coincidence.” We started out with a mystery of why $\forall z \colon C\left(z\right) = 1$ was true despite having heuristic probability $2^{-n}$; but now we have the mystery of why every one of the $2^n$ steps of the proof happened to work out. The proof was no less surprising than the phenomenon-to-be-explained and we’ve made no progress.

Given an explanation $\pi$ of a phenomenon $\varphi$, we can ask _how surprised we feel in total_ after seeing the explanation—including both how surprising the property now seems (measured by $\widetilde{\mathbb{E}}\left(\varphi, \pi\right)$) as well as how surprised we are by the existence of $\pi$ itself.

We don’t know how to quantify how surprising $\pi$ is, but intuitively it is closely related to length: some steps of $\pi$ will involve coincidences, and we effectively want to sum up surprisingness across those steps. If we neglect the subtleties and just treat _every_ step as surprising, then we could define the quality of an explanation $\pi$ to be: 

$$
\log \widetilde{\mathbb{E}}\left(\varphi, \pi\right) - \left|\pi\right|.
$$

 This picture roughly mirrors an evaluation of a Bayesian hypothesis as the log prior probability plus the log likelihood of the data. This exact form seems unreasonable since $\left|\pi\right|$ doesn’t capture nuances in how surprising $\pi$ is, but it seems like some more sophisticated formula along these lines could give us a sense of how well a heuristic argument $\pi$ explains the phenomenon $\varphi$.

## Soundness ^soundness

Suppose that we empirically discovered that after some point the twin primes simply stopped appearing at the expected rate. That is, we start checking the primes $p_1, p_2, \ldots$ greater than $N$, and we find that $p+2$ is a composite in every single case we check.

After checking $10 \log{N}$ candidate primes and not finding any twins we think that something is likely wrong; we assigned a probability of only $0.005\%$ to seeing a stretch this long without any twin primes. After $100 \log{N}$ examples our probability is down to $0.000000000000000000000000000000000000004\%$.

Of course we should not keep betting that $p+2$ will be prime with probability $\frac 1{\log p}$. At some point the inductive inference clearly trumps the deductive heuristic argument and we should not expect to see more twin primes. But this raises the question: was there _necessarily_ some argument we overlooked, some deductive heuristic argument that would have revised our probability estimate if we had noticed it? Should we confidently expect that we’ll learn something if we keep investigating this phenomenon?

It seems implausible that there could be no more twin primes “by coincidence.” But could it happen for a reason that is completely beyond our understanding?

### Are all true statements heuristically plausible? ^are-all-true-statements

For a given heuristic estimator $\widetilde{\mathbb{E}}$, we say that a sentence $\varphi$ is _heuristically implausible_ if for any $\varepsilon> 0$ there is a set of arguments $\pi_1, \ldots, \pi_n$ that can convince $\widetilde{\mathbb{E}}$ that $\widetilde{\mathbb{E}}\left(\varphi, \pi_1, \ldots, \pi_n\right) < \varepsilon$, and moreover such that there is no further set of arguments $\pi_{n+1}, \ldots, \pi_m$ such that $\widetilde{\mathbb{E}}\left(\varphi, \pi_1, \ldots, \pi_m\right) > \varepsilon$. Otherwise we say that $\varphi$ is heuristically plausible.

That is, $\varphi$ is heuristically plausible iff $\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)> 0$, where we define: 

$$
\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right) = \inf_{\pi_1, \ldots, \pi_{n}}
\mathop{\smash{\mathrm{sup}}}_{\pi_{n+1}, \ldots, \pi_m} \widetilde{\mathbb{E}}\left(\varphi, \pi_1, \ldots, \pi_m\right).
$$

For example, the argument in Section [[#^example-the-twin-prime|1]] implies that it is heuristically implausible that there are only finitely many twin primes, unless there is some further heuristic argument $\pi$ that the events ($x$ is prime) and ($x+2$ is prime) are anticorrelated.

We’ll say that a heuristic estimator is sound[^note-27] if every true statement $\varphi$ is heuristically plausible.

This may look like a very weak statement because we are only requiring $\widetilde{\mathbb{E}}$ to assign _non-zero_ probability to true statements $\varphi$. Nevertheless, asserting that a particular heuristic estimator is sound can be an extremely strong statement.

For example, suppose that $\varphi$ is a computable property of natural numbers. Unless the heuristic probability of $\varphi\left(n\right)$ approaches $1$ sufficiently quickly for large values of $n$, we heuristically expect $\mathbb{P}\left(\forall n \colon \varphi\left(n\right)\right) = 0$. So for any heuristically sound verifier and any computable property $\varphi$ that holds for all integers, there must be a heuristic argument that $\mathbb{P}\left(\varphi\left(n\right)\right)$ is extremely close to $1$ for large values of $n$.

It’s likely to be difficult or impossible to prove that any interesting heuristic estimator is sound. Proving this would require showing that there are never any “grand coincidences” that make a universally quantified statement true by chance alone. But it’s unclear what techniques could possibly prove the absence of coincidences for even a single sentence $\forall n \colon \varphi\left(n\right)$.

Merely finding a deductive heuristic estimator which is _plausibly_ sound would be extremely interesting. We could summarize such a result as saying that “everything happens for a reason”—every true universally quantified statement is explained by some heuristic argument accepted by $\widetilde{\mathbb{E}}$.

### Trivial forms of soundness ^trivial-forms-of-soundness

Some heuristic estimators $\widetilde{\mathbb{E}}$ are sound for uninteresting reasons.

**Non-dogmatic.** If $\widetilde{\mathbb{E}}$ never assigns probability $0$ to any sentence unless it finds a disproof, then it will be sound as long as the underlying proof system is sound. Non-dogmatism seems like a reasonable epistemic principle, and it is a defining property for many existing algorithms for assigning probabilities to logical sentences (e.g. \[13, 8, 14, 5, 18\]). We are interested in asking: is non-dogmatism a _fundamental_ epistemic principle, such that we should think of any sentence $\varphi$ as having some probability of being true “just because”?

**Easily persuadable.** Our definition of plausibility requires that for every argument $\pi^-$ that $\varphi$ has probability $0$, there is a counterargument $\pi^+$ showing that $\varphi$ has non-zero probability after all. This property is trivially satisfied if the “second arguer wins,” e.g. if $\widetilde{\mathbb{E}}$ simply defers to the longest argument it sees. Soundness does not guarantee that an estimator is reasonable or expressive in any interesting sense; soundness is only interesting for heuristic estimators that have other desirable properties.

**Moved by inductive evidence.** There is nothing in the definition of a heuristic estimator that prevents it from accepting arguments like: “$\varphi\left(n\right)$ has been true for the first $10^{100}$ values of $n$, so I’ll give a 50% chance to $\forall n \colon \varphi\left(n\right)$.”[^note-28] If in fact $\forall n \colon \varphi\left(n\right)$, then it is possible to exhibit an arbitrarily long list of positive examples. Thus any heuristic estimator that accepts inductive evidence is likely to be sound. We only consider soundness interesting for what we called _deductive_ heuristic estimators in Section [[#^inductive-vs-deductive-arguments|10]].

**Moved by hypothetical reasons.** Even if we haven’t yet found any structure in the primes that could cause the twin prime conjecture to fail, we think that a reasonable heuristic estimator could be open to heuristic arguments about the probability that there exists some structure we haven’t yet noticed. This _might_ ensure that almost any statement is heuristically plausible, if the estimator always holds out enough hope for the possibility that there is a key structural fact that it hasn’t yet noticed. We are interested in asking: was that hope justified—e.g. was it _actually_ the case that if the twin conjecture fails it’s because there is a concrete reason for an anticorrelation? Or could our heuristic estimator avoid assigning probability 100% only by forever holding out the possibility of seeing a hypothetical counterargument $\pi$ that doesn’t actually exist?

### Quantitative soundness ^quantitative-soundness

So far we’ve considered the weak condition $\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)> 0$. We expect an ideal heuristic estimator to assign true sentences probability significantly more than zero—but exactly how much more?

On the one hand, we expect there to be true sentences of length $k$ that are assigned probability $O\left(2^{-k}\right)$. For example, let $X$ be the definition of an algorithmically random real number[^note-29] and consider the statement that the first $k$ bits of $X$ are $0.x_0x_1\ldots x_k$ for some particular $x_i \in \left\{0, 1\right\}$. One of these $2^k$ statements will turn out to be true, but we don’t expect any heuristic estimator to be able to guess which one with probability better than chance.

On the other hand, consider the set of true sentences $\varphi$ with length $\left|\varphi\right| < k$ such that[^note-30] $\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)< 2^{-k}$. There are at most $2^k$ such sentences. And if $\widetilde{\mathbb{E}}$ is “well-calibrated,” then each of these sentences ought to be true with probability less than $2^{-k}$. Therefore in expectation at most $1$ of these sentences will turn out to be true.

In fact, the same argument suggests that there are expected to be at most $\varepsilon$ true sentences of _any_ length such that $\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)< \varepsilon 2^{-\left|\varphi\right|}$.

This gives us a quantitative version of the soundness condition from the last section: 

$$
\begin{equation}
\tag{\(\varepsilon\)-soundness}
    \textnormal{For all true sentences \(\varphi\):\,}
    \inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)> \varepsilon 2^{-\left|\varphi\right|}
\end{equation}
$$

 We expect a good verifier to satisfy this condition for a sufficiently small constant $\varepsilon$. In fact this requirement is fairly likely to be true even for $\varepsilon= 1$, but it is heuristically almost surely true as $\varepsilon\rightarrow 0$.

### Empirical predictions ^empirical-predictions

Mathematicians often discover initially-unexplained empirical regularities. For example, in 1853 Chebyshev \[4\] observed that if you divide a random prime number by $4$ the remainder is $3$ slightly more often than it is $1$—even though we might have heuristically expected those two events to be equally common. In fact it seems to be the case that for almost all[^note-31] $N$, a majority of primes less than $N$ have remainder $3$ mod $4$. After discovering this fact, how confident should Chebyshev have been that mathematicians would eventually find a clear explanation?[^note-32]

The existence of a sound heuristic estimator is closely related to a more general empirical prediction about the practice of mathematics: every time we find an empirical regularity like Chebyshev’s bias, we will eventually be able to find a concrete heuristic argument explaining why the regularity occurs.

We don’t have a concrete heuristic estimator so we can’t evaluate the claim formally, but we can still ask whether mathematicians find an **informal** heuristic argument. Similarly, we don’t have infinite time so we can’t ask whether we will eventually find such an argument, but we can ask whether we typically find them **quickly**. For example we can ask: how many observed empirical regularities are currently unexplained despite a significant effort? How reliably and quickly we can find an explanation for a currently-unexplained empirical regularity if we decide to investigate it thoroughly?

If we ask the analogous question for proofs the situation looks bleak: most domains of mathematics are full of unproven conjectures that are strongly believed. Moreover it is not hard to spend an afternoon experimenting with numbers to arrive at a novel conjecture that is probably true but unlikely to be resolved even given decades of effort.

But if we consider heuristic arguments as well as proofs then it appears to us that a significant majority of well-studied empirical regularities have been adequately explained.[^note-33] Similarly, it seems quite challenging and noteworthy to discover empirical regularities that don’t have a simple heuristic explanation. And if a currently-unexplained regularity was selected and investigated thoroughly, we believe it is very likely that an explanation could be found within months or potentially years rather than decades.

In our experience it isn’t controversial to suggest that there almost certainly _exists_ an explanation for any given empirical regularity. The alternative, that such regularities can be fundamentally inexplicable coincidences, seems to be considered unlikely. What is striking about the current situation is that despite this historical pattern we don’t have any candidate formalization of what we mean by “explanation.” If this is really a robust pattern, then that strikes us as a deep fact about the nature of mathematics, and we expect that there is _some_ better definition of explanation than “a paper that leaves mathematicians feeling convinced that the phenomenon is plausible.”

The best candidate counterexample we are aware of is the consistency of strong axiom systems, which we will discuss in Section [[#^consistency-statements|11.6]]. Reasoning about “explanations” for consistency claims is very subtle and probably requires having a more precise definition of what constitutes an explanation, so for now we think it’s hard to tell whether consistency statements have plausibility arguments. The empirical prediction discussed in this section seems interesting even if we explicitly set aside these cases. As we discuss in Section [[#^other-failures-of-proofs|11.7]] we don’t believe that consistency statements are the most important way in which proof systems are incomplete.

### Incompleteness and diagonalization ^incompleteness-and-diagonalization

Soundness is the requirement that $\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)> 0$ whenever $\varphi$ is true. We could also consider completeness, the property that $\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)= 1$ whenever $\varphi$ is true (or the even stronger property $\sup \inf \widetilde{\mathbb{E}}\left(\varphi, \pi\right) = 1$).

We don’t think that we should expect such a strong principle to hold even if $\widetilde{\mathbb{E}}$ is an ideal formalization of heuristic reasoning. No matter how good we are at reasoning, there are many complicated questions where we shouldn’t expect to get to a confident answer no matter how many arguments we see.

Unsurprisingly, we can also show that this property is impossible via a diagonalization argument. Define $G$ by quining such that: 

$$
G \Leftrightarrow \inf \sup \widetilde{\mathbb{E}}\left(G\right) < 1.
$$

 If $\inf \sup \widetilde{\mathbb{E}}\left(G\right) = 1$, then $G$ is false and hence $\neg G$ is a true statement with $\inf \sup \widetilde{\mathbb{E}}\left(\neg G\right) = 0$. Thus it can’t possibly be the case that $\inf \sup \widetilde{\mathbb{E}}\left(\varphi\right)= 1$ for every true sentence $\varphi$.

We are aware of no similar diagonalization obstruction to satisfying soundness. Here are some examples of self-referential sentences $G$ and possible ways that a heuristic estimator could handle them while being consistent with soundness:

$G \coloneqq \sup \inf \widetilde{\mathbb{E}}\left(G\right) = 0$.

We expect $G$ to be true, and to have $\inf \sup \widetilde{\mathbb{E}}\left(G\right) = 1$. No matter what argument $\pi$ you make suggesting that $G$ is true, there is another argument $\pi'$ suggesting that actually $G$ is false, perhaps by pointing out that $\widetilde{\mathbb{E}}\left(G, \pi\right)$ is large. We expect this process to go on forever and for $\widetilde{\mathbb{E}}$ to oscillate indefinitely. This is closely related to the examples in Section [[#^cherry-picking-arguments|13]], which give a simpler argument that we could not achieve the stronger form of soundness $\varphi\Rightarrow \sup \inf \widetilde{\mathbb{E}}\left(\varphi\right) > 0$.

$G \coloneqq \inf \sup \widetilde{\mathbb{E}}\left(G\right) = 0$.

We expect $G$ to be false, and to have $\inf \sup \widetilde{\mathbb{E}}\left(G\right) = 1$. This is a similar case where arguments cause $\widetilde{\mathbb{E}}$ to oscillate indefinitely. In these cases, the “innermost quantifier wins.”

$G \coloneqq \inf \sup \widetilde{\mathbb{E}}\left(G\right) < 1$.

We expect $G$ to be true, with $\inf \sup \widetilde{\mathbb{E}}\left(G\right) = 1 - \varepsilon$ where $\varepsilon> 0$ is $\widetilde{\mathbb{E}}$’s limiting probability that $\widetilde{\mathbb{E}}$ is unsound. Soundness is compatible with a model being uncertain about its own soundness.

$G \coloneqq \sup_{\pi} \widetilde{\mathbb{E}}\left(G, \pi\right) < 1$.

We expect $G$ to be false with $\inf \sup \widetilde{\mathbb{E}}\left(G\right) = 0$. This is an existentially quantified statement, so we expect there to be a simple argument $\pi^*$ such that $\widetilde{\mathbb{E}}\left(G, \pi^*\right) = 1$. Computing $\pi^*$ is a simple proof that $G$ is false, and hence $\inf \sup \widetilde{\mathbb{E}}\left(G\right) = 0$.

It’s not clear that a heuristic estimator should behave in these ways, but these behaviors are consistent with soundness and we consider them reasonable options suggesting that our goals for heuristic estimators are mild enough to be compatible with self-reference. Allowing models to be unsure about their own soundness, and allowing their probabilities to oscillate indefinitely, seem to avoid most plausible paradoxes.

### Consistency statements ^consistency-statements

A central example of a true statement that is unprovable in a theory $T$ is the consistency $\mathrm{Con}\left(T\right)$ of $T$ itself. It’s natural to wonder if it’s possible to make a heuristic argument that $T$ is consistent without needing to use axioms beyond $T$. If it’s not, then this might be a counterexample to the empirical prediction in Section [[#^empirical-predictions|11.4]] and a way to show that interesting forms of heuristic soundness are unachievable.

Overall we’ll argue that it’s premature to try to answer this question—there is no obvious diagonalization obstruction, and there are plausible arguments for consistency, but we can’t really evaluate those arguments without having a much clearer picture of how a hypothetical deductive estimator would work.

This section ventures into even more ungrounded speculation, and so we recommend that most readers skip it unless they find the question particularly interesting.

#### The problem ^the-problem

To illustrate the issue, let’s work within ZFC[^note-34] and consider the statement: 

$$
\mathrm{Con}\left(\mathrm{ZFC}\right)\coloneqq \forall \pi \colon \textnormal{\(\pi\) is not a proof of a contradiction in ZFC.}
$$

 There is a simple heuristic argument that $\mathrm{Con}\left(\mathrm{ZFC}\right)$ should be false: there infinitely many possible proofs, and if we treat each of them as having some independent chance of deriving a contradiction then almost surely one of them will.[^note-35] So in order to be sound, we need to find a heuristic argument $\pi$ that explains why $\mathrm{Con}\left(\mathrm{ZFC}\right)$ is plausible after all.

We’ll consider two plausible ways that we could heuristically argue for $\mathrm{Con}\left(\mathrm{ZFC}\right)$.

#### Set-theoretic approach ^set-theoretic-approach

One way to argue that ZFC is consistent is to find a transitive model for ZFC, i.e. a set $M$ such that each axiom of ZFC is true when the quantifiers range over $M$. If we have such a model, then we can inductively show that ZFC only proves statements $\varphi$ that are true of $M$, and hence that ZFC can’t derive a contradiction.

At face value arguing for the existence of such an $M$ isn’t necessarily any easier than arguing for $\mathrm{Con}\left(\mathrm{ZFC}\right)$: the axioms of ZFC themselves specify an infinite list of claims about $M$, and so the existence of a set $M$ satisfying all of them is heuristically implausible.

However, the axioms of ZFC have a special structure that makes it plausible that we can satisfy them all. In particular, $M$ is a transitive model of ZFC if and only if it contains the integers and is closed under a few fundamental operations—taking finite collections, unions, power sets, or forming a set $\left\{f(x)\left\vert x \in S\right.\right\}$ for a function $f$ and a set $S \in M$.

ZFC is able to build very large sets that nearly satisfy these properties by starting from the integers and then iteratively adding more and more sets.[^note-36] Using this idea it can prove that such a transitive model $M$ exists as long as there is an _inaccessible cardinal_ $\kappa$: a set bigger than any union[^note-37] or power set of smaller sets. We have no idea whatsoever whether the existence of an inaccessible cardinal is heuristically plausible. There are potential arguments on both sides, but arbitrating the question seems impossible or meaningless given our current state of uncertainty about how a hypothetical heuristic estimator would work.

The main point we want to make is that the special structure of ZFC does appear to give us a concrete reason to think that ZFC may be consistent via the construction of the cumulative hierarchy. This argument can be appreciated within ZFC even if ZFC cannot establish the existence of an inaccessible cardinal and therefore cannot tell whether the process goes on long enough to actually produce a transitive model. This leaves the heuristic status of the consistency of ZFC highly unclear, even though we heuristically expect that _most_ sets of axioms are inconsistent.

#### Explicit reflection principle ^explicit-reflection-principle

We can formalize the idea of one proof system $T_1$ trusting another $T_2$, about a statement $\varphi$, by asking whether $T_1$ proves a theorem like: “If $T_2$ proves $\varphi$, then $\varphi$ is true.” Löb’s theorem \[20\] states that if a proof system trusts itself about a statement $\varphi$, then it can immediately prove $\varphi$. Thus it’s impossible for a proof system to trust itself except when it already knows the answer.

What would it mean for a deductive heuristic estimator to trust itself? Imagine that we find an argument $\pi$ which tells us not that $X$ is large but that there _exists_ an argument $\pi'$ that $X$ is large. If $\widetilde{\mathbb{E}}$ trusts itself, then $\pi$ should already be enough to change its beliefs about $X$—we shouldn’t have to actually find the argument $\pi'$ and present it to $\widetilde{\mathbb{E}}$ explicitly. We could imagine adding an explicit deduction rule that allows $\widetilde{\mathbb{E}}$ to make this inference.

We can’t really meaningfully investigate this kind of deduction rule without having a much clearer picture of how a deductive heuristic estimator might work. But it’s worth noting that Löb’s theorem and similar obstructions don’t seem to apply, and it seems plausible for a deductive heuristic estimator to trust itself in this sense. The key difference is that $\widetilde{\mathbb{E}}$ considers the existence of $\pi'$ for which $\widetilde{\mathbb{E}}\left(X, \pi'\right)$ is large to be _prima facie_ reason to believe that $X$ is large, but this does **not** correspond to $\widetilde{\mathbb{E}}$ assigning high probability to any material implication of the form $(\textnormal{\(\widetilde{\mathbb{E}}\left(X, \pi'\right)\) is large}) \Rightarrow (\textnormal{\(X\) is large})$.

If a heuristic estimator both accepted the axioms of ZFC and trusted itself in this way then it may be able to directly deduce that the axioms of ZFC are almost surely consistent:

-   For any finite set of axioms from ZFC, ZFC can prove that those axioms are consistent. Moreover, ZFC can _prove_ that for any finite set of axioms, there is a proof in ZFC that those axioms are consistent.
    
-   If our heuristic estimator considers the mere existence of an argument to be persuasive, then proving that there exists an argument for every set of axioms is enough to infer that every set of axioms is almost surely consistent.
    
-   There are only countably many sets of axioms, and so if our estimator knows that every one of them is almost surely consistent then it can conclude that it is almost surely the case that every one of them is consistent, and hence that ZFC itself is consistent.
    

This estimate is defeasible, and e.g. if ZFC later found a proof of a contradiction then it would of course conclude that ZFC wasn’t consistent after all (though at that point it would have bigger problems since it would be possible to make convincing arguments for arbitrary claims).

### Other failures of proofs ^other-failures-of-proofs

Although Gödelian statements are the most famous failure of proofs, it seems likely to us that unprovability is ubiquitous. Our position on these questions is similar to the one expressed by Conway in \[6\].

We think of Gödelian statements as an interesting challenge case for soundness of a heuristic estimator, but we _don’t_ think of proving Gödelian statements as the central way in which heuristic estimators overcome the incompleteness of proof systems.

For a more prosaic example of incompleteness, take $f\colon \mathbb{N} \rightarrow \left\{0, 1\right\}$ to be a complex function with no apparent structure or bias towards $0$ or $1$. Then consider the statement: 

$$
\varphi\left(f\right) \coloneqq \forall N > 100: \sum_{n = 1}^{N} f(n) > 0.01 N.
$$

 Heuristically this statement is almost surely true and can fail only if $f$ has some special structure that we’ve overlooked. But on the other hand, it seems that $\varphi\left(f\right)$ can only be proven if $f$ has special structure that can be leveraged by a proof. So a structureless $f$ would make $\varphi\left(f\right)$ both true and unprovable.

How we can we reconcile this pessimistic view with the empirical success of mathematicians at proving theorems?

-   If we write down a simple function, it is quite likely to have plenty of structure (even if there is no obvious structure at a first glance). Indeed, cryptographers spend a great deal of effort trying to find simple functions without any special structure that would make them amenable to cryptanalysis, and naı̈vely choosing “random-looking” functions rarely succeeds. Writing down a concrete simple function $f$ for which $\varphi\left(f\right)$ is unprovable strikes us as a very similar challenge. That said, we expect many such functions to exist and to be extremely “mundane,” looking more like cryptographic hash functions than self-referential sentences.
    
-   Mathematicians systematically avoid areas without the kind of structure that facilitates proofs. For example the Collatz conjecture concerns a very simple function (much simpler than almost any function that has been found sufficiently “structureless” to be usable in cryptography), and we could imagine a rich sister field to number theory proving simple statements about similar dynamical systems. But it doesn’t exist in part because mathematicians have gotten very little traction on proving statements of this type. Number theory has flourished precisely because mathematicians have been able to say interesting things about the primes for thousands of years.
    

We believe these two facts largely explain the empirical success of proofs, and are consistent with a perspective where unprovability is the “default” situation except when special structure makes proof possible.

Regardless of whether this perspective on unprovability is correct, one special feature of Gödelian statements is that it is easy to _prove_ that they are unprovable (in a stronger theory). In contrast, in the case of a typical “structureless” function $f$, we expect it to be unprovable that $\varphi\left(f\right)$ is unprovable. So even if this kind of unprovability were ubiquitous, Gödelian statements would likely remain the prototypical examples of unprovable sentences. This mirrors the situation in complexity theory, where it is suspected that “generic” functions cannot be efficiently computed, but diagonalization arguments are practically the only source of _provably_ hard-to-compute functions.

### Quantitative bounds on argument length? ^quantitative-bounds-on-argument

We are often interested in statements about strictly finite objects, for example the claim that $\forall x \colon C\left(x\right) = 1$ for a particular circuit $C\colon \left\{0, 1\right\}^{m} \rightarrow \left\{0, 1\right\}$. In these cases heuristic soundness is trivial, because there is a finite proof of the statement by exhaustively considering every possible input $x$.

Nevertheless we would consider a heuristic estimator unreasonable if $\forall x \colon C\left(x\right) = 1$ but the only way to heuristically argue for this fact was to exhaustively consider every input.

Intuitively this is damning because the fact that an exhaustive proof derives the conclusion $\forall x \colon C\left(x\right)=1$ is _itself_ surprising—in fact just as surprising as the original claim.

We discuss this idea informally in Section [[#^explanation-seems-to-be|10.6]], where we introduce the notion of an explanation $\pi$’s _quality_, taking into account both $\widetilde{\mathbb{E}}\left(\varphi, \pi\right)$ as well as the surprisingness of $\pi$ itself. Intuitively we expect that an arbitrary statement $\varphi$ ought to have an explanation of sufficiently high quality. We don’t know how to define the quality of an explanation, but if we use $\left|\pi\right|$ as an estimate for the surprisingness of $\pi$ then we obtain the following stronger form of soundness: 

$$
\begin{equation*}
\exists \delta \colon \textnormal{For all true sentences \(\varphi\):\,}
    \forall \pi^- \colon \exists \pi^+ \colon
    \left|\pi^+\right| - \log \widetilde{\mathbb{E}}\left(\varphi, \pi^-, \pi^+\right) < \left|\varphi\right| + \left|\pi^-\right| + \delta
\end{equation*}
$$

 The intuitive justification for this principle similar to the justification for soundness itself but much weaker. We need to include $\left|\pi^-\right|$ based on the concerns raised in Appendix [[#^cherry-picking-arguments|13]], and we don’t think that this correction term fully handles the problem raised there. Nevertheless, we think it is quite plausible that there is _some_ quantitative form of soundness that is interesting even for finite claims and is satisfied by an appropriate deductive heuristic estimator.

## Cumulant propagation ^cumulant-propagation

In Section [[#^circuits-as-a-setting|6]] we introduced the problem of estimating the output probability $\mathbb{P}\left(C\right)$ for a boolean circuit $C$. In this section we will describe an algorithm for an even simpler problem: estimating the expected output $\mathbb{E}\left[C\right]$ for an _arithmetic_ circuit $C\colon \mathbb{R}^n \rightarrow \mathbb{R}$ when run on independent Gaussian inputs. In this simple setting we can improve over the naive algorithm which simply treats all gates as independent, by tracking the expectation of every degree $k$ polynomial for some constant $k$. We present this algorithm in Section [[#^cumulant-propagation-2|12.6]].

Often many of these correlations will be small, and so we’d like to design a faster algorithm that pays attention to a specific subset of polynomials specified in an argument $\pi$, and continues to treat other variables as independent. Unfortunately, when we do this our algorithm can produce inconsistent estimates with $\mathbb{E}\left[f^2\right] < 0$ for a real-valued polynomial $f$. We explore this difficulty in Section [[#^cumulant-propagation-and-sums|12.7]].

We believe that there likely exists an estimation algorithm that corrects these deficiencies. Finding such an algorithm is our current research priority for formalizing the presumption of independence.

### Arithmetic circuits ^arithmetic-circuits

An arithmetic circuit is exactly analogous to boolean circuits as defined in Section [[#^task-definition|6.1]] except with node values being real instead of boolean, additional “constant wires” whose value is a fixed constant $c \in \mathbb{R}$, and operations being either addition or multiplication rather than an arbitrary boolean function.

Formally, an arithmetic circuit $C$ with $n$ inputs consists of a set of nodes $x_1, x_2, \ldots, x_m$. Each node $x_k$ is labeled as one of:

-   An input wire labeled with an integer $i_k \in \left\{1, 2, \ldots, m\right\}$. For convenience we will assume that there is exactly one input wire with each label.
    
-   A constant wire labeled with real number $c_k \in \mathbb{R}$.
    
-   A sum gate labeled with a pair $a_k, b_k \in \left\{1, 2, \ldots, k-1\right\}$.
    
-   A product gate labeled with a pair $a_k, b_k \in \left\{1, 2, \ldots, k-1\right\}$.
    

To evaluate $C\left(z_1, \ldots, z_n\right)$ we iterate through the wires in order and compute a value $x_k\left(z_1, \ldots, z_n\right)$ for each of them:

-   If $x_k$ is an input wire labeled with $i$, then $x_k\left(z_1, \ldots, z_n\right) = z_i$.
    
-   If $x_k$ is a constant gate labeled with $c_k$, then $x_k\left(z_1, \ldots, z_n\right) = c_k$.
    
-   If $x_k$ is a sum gate labeled with $a_k, b_k$, then $x_k\left(z_1, \ldots, z_n\right) = x_{a_k}\left(z_1, \ldots, z_n\right) + x_{b_k}\left(z_1, \ldots, z_n\right)$.
    
-   If $x_k$ is a product gate labeled with $a_k, b_k$, then $x_k\left(z_1, \ldots, z_n\right) = x_{a_k}\left(z_1, \ldots, z_n\right) \times x_{b_k}\left(z_1, \ldots, z_n\right)$.
    

Then we define $C\left(z_1, \ldots, z_n\right) = x_{m}\left(z_1, \ldots, z_n\right)$.

Given an arithmetic circuit $C$ and a distribution $\mathcal{D}$ over $\mathbb{R}^m$, we define $\mathbb{E}_{\mathcal{D}}\left[C\right] = \mathbb{E}_{z_1, \ldots, z_n \sim \mathcal{D}}\left[C\left(z_1, \ldots, z_n\right)\right]$.

We will consider heuristic verifiers for estimating $\mathbb{E}_{\mathcal{N}\left(0, I\right)}\left[C\right]$, the expected output of $C$ when run on independent standard normal inputs. We will later see how to generalize this algorithm to other input distributions.

### Mean propagation ^mean-propagation

If we ignore _all_ correlations between intermediate values $x_k$, we obtain a very simple estimator $\widetilde{\mathbb{E}}$ we call “mean propagation.” This is precisely analogous to the simple estimator for boolean circuits introduced in Section [[#^a-simple-algorithm-assume|6.2]].

We will iterate through the nodes in order, and for each node $x_k$ we will compute an estimate $\mu_k$ of its mean as follows:

-   If $x_k = c_k$ is a constant wire, then $\mu_k = c_k$.
    
-   If $x_k = z_{i_k}$ is an input wire, then $\mu_k = 0$ (since $z_{i_k} \sim N(0, 1)$).
    
-   If $x_k = x_{a_k} + x_{b_k}$ is a sum gate, then $\mu_k = \mu_{a_k} + \mu_{b_k}$. If the estimates for the input wires are accurate, then $\mu_k$ is exactly accurate by linearity of expectation.
    
-   If $x_k = x_{a_k} x_{b_k}$ is a product gate, then $\mu_k = \mu_{a_k} \mu_{b_k}$.
    

An example of this process is illustrated in Figure 6.

The result of mean propagation on a simple circuit. The values $\mu_i$ are written in red beside the corresponding $x_i$.

This estimate is “better than nothing” in that we expect it to typically do better than simply assuming the output of a circuit is $0$. It’s not easy to define a formal sense in which we can prove that this is actually better than nothing, and so for now we will mostly leave this as an intuitive statement.

Regardless of whether this is better than nothing, it is certainly not a _great_ estimate. For example, it approximates the mean of $z_i^2$ as $0$ even though $z_i$ is a standard normal.

### Covariance propagation ^covariance-propagation

Instead of merely maintaining an estimate for the means of nodes $\mu_k$, we can also maintain estimates $\sigma_{kk}$ for the variance of each node and $\sigma_{jk}$ for the covariance for each pair of nodes. Now when we consider a new node $k$, we compute estimates $\sigma_{jk}$ for every node $j \leq k$. We can compute these estimates using update rules similar to the last section, but using a slightly more complex “independence” assumption.

In particular, when we are given a product gate like $x_k = x_i x_j$, we can exactly compute the mean of $x_k$ as $\mu_i \mu_j + \sigma_{ij}$. But in order to compute the covariance of $x_k$ with $x_{\ell}$, we need to reason about the three-way interaction of $x_i$, $x_j$, and $x_{\ell}$ given only the covariances. To do this, we will assume that $x_i$, $x_j$, and $x_{\ell}$ are jointly Gaussian. In this case it is easy to compute that 

$$
\sigma_{k\ell} = \sigma_{i\ell} \mu_j + \mu_i \sigma_{j \ell}
$$

 while 

$$
\sigma_{kk} = \sigma_{ij}^2 + 2\sigma_{ij}\mu_i\mu_j + \sigma_{ii} \sigma_{jj}
+ \sigma_{ii} \mu_j^2 + \sigma_{jj} \mu_i^2.
$$

Why assume that the $x_i$ are jointly Gaussian? The simplest justification is that this is the maximum entropy distribution given a particular covariance matrix. Another intuition is that if they deviate from joint normality, it’s not at all clear which way we should expect the deviation to push. In Section [[#^generalizing-independence-with-cumulants|12.5]] we will generalize this assumption further and give an additional argument that it is a natural generalization of the presumption of independence.

Putting this altogether, the algorithm is:

-   If $x_k = c_k$ is a constant wire, then $\mu_k = c_k$, $\sigma_{jk} = 0$ for all $j$.
    
-   If $x_k$ is an input wire, then $\mu_k = 0$, $\sigma_{jk} = 0$ for $j < k$, and $\sigma_{kk} = 1$.
    
-   If $x_k = x_{a_k} + x_{b_k}$ is a sum wire, then $\mu_k = \mu_{a_k} + \mu_{b_k}$, $\sigma_{jk} = \sigma_{ja_k} + \sigma_{jb_k}$ for $j < k$, and $\sigma_{kk} = \sigma_{a_k a_k} + 2 \sigma_{a_k b_k} + \sigma_{b_k b_k}$.
    
-   If $x_k = x_{a_k} x_{b_k}$, then 
    
    $$
    \begin{align*}
                \mu_k &= \mu_{a_k} \mu_{b_k} + \sigma_{a_k b_k},\\
                \sigma_{jk} &= \sigma_{ja_k} \mu_{b_k} + \sigma_{jb_k}\mu_{a_k},\\
                \sigma_{kk} &= \sigma_{a_kb_k}^2 + 2\sigma_{a_kb_k}\mu_{a_k}\mu_{b_k} + \sigma_{a_ka_k} \sigma_{b_kb_k}
                + \sigma_{a_ka_k} \mu_{b_k}^2 + \sigma_{b_kb_k} \mu_{a_k}^2.
    \end{align*}
    $$
    

In Figure 7 we illustrate how this process produces a different estimate for the circuit from Figure 6.

In blue we show how covariance propagation gets a different estimate than mean propagation. The dotted blue lines indicate pair of nodes that are computed to have covariance $1$, reflecting the computation: $1 = \operatorname{Cov}\left(z_2, z_2\right) \rightarrow \operatorname{Cov}\left(1 + z_2, z_2\right) \rightarrow \operatorname{Cov}\left(1 + z_2, z_1 + z_2\right) \rightarrow \mathbb{E}\left[(z_1 + z_2)(1 + z_2)\right]$. The other covariances are either $0$ or irrelevant to the computation.

Empirically we’ve found this estimate is often much more reasonable than simply propagating means; for example we’ve evaluated it for small random circuits or shallow neural networks. But it remains hard to justify that statement in any formal sense, or even to justify the claim that it is a “sound” estimator, since it is easy to construct circuits where it gives a worse estimate than nothing. We could try to formalize soundness by considering particular random distributions over circuits, but the results are then very specific to the particular distribution and do not obviously apply to any realistic circuit. For now we will mostly leave this as an intuitive claim.

### Sparse covariance propagation ^sparse-covariance-propagation

Covariance propagation gives us a $n^2$ time algorithm for estimating the output of a circuit with $n$ gates. If we want a faster algorithm, we could try to pay attention to a subset of “important” covariances. This introduces a role for arguments $\pi$, which can point out a set of covariances to pay attention to.

We will take an “argument” $\pi$ to be a set of pairs of indices $\left\{(i, j)\right\}$ for which we should track covariances. We compute our estimate exactly as in covariance propagation, but we only compute covariances $\sigma_{ij}$ for pairs $\left(i, j\right) \in \pi$. Whenever a term $\sigma_{ij}$ with $\left(i, j\right)\not\in\pi$ occurs inside an update step, we replace it with $0$.

Given a set of arguments $\pi_1, \ldots, \pi_n$, we just apply the same algorithm to the union $\pi = \pi_1 \cup \ldots \cup \pi_n$.

The estimate $V\left(\mathbb{E}_{\mathcal{D}}\left[C\right], \pi_1, \ldots, \pi_n\right)$ can be computed in time $O\left(\left|C\right| + \left|\bigcup_i \pi_i\right|\right)$ and converges to the output of variance propagation as $\bigcup_i \pi_i \rightarrow C \times C$. How quickly it converges depends on the details of the circuit and on how well the arguments $\pi_i$ capture the important sources of variances.

### Generalizing independence with cumulants ^generalizing-independence-with-cumulants

Mean propagation is organized around the “naive guess” $\mathbb{E}\left[x_i x_j\right] = \mathbb{E}\left[x_i\right] \mathbb{E}\left[x_j\right]$, which we justified by appealing to the presumption of independence. Covariance propagation is organized around a similar naive guess, that $\operatorname{Cov}\left(x_i x_j, x_{\ell}\right) = \operatorname{Cov}\left(x_i, x_{\ell}\right)\mathbb{E}\left[x_j\right] + \operatorname{Cov}\left(x_j, x_{\ell}\right)\mathbb{E}\left[x_i\right]$, which we justified by assuming that the $x_i$ were jointly normal (or equivalently taking a maximum entropy distribution).

In order to deal with higher-order correlations, we need to generalize these guesses. We will do this by generalizing a particular definition of independence based on _joint cumulants_.

For any random variables $X_1, \ldots, X_n$, the joint cumulants $\kappa\left(X_1, \ldots, X_n\right)$ are defined via the following identity relating them to the moments: 

$$
\begin{equation}
    \mathbb{E}\left[X_1 X_2 \ldots X_n\right] = \sum_{\substack{\textnormal{\(\pi\) a partition} \\ \textnormal{of \(\left\{1, 2, \ldots n\right\}\)}}} \prod_{\substack{\left\{i_1, i_2, \ldots, i_k\right\} \\ \textnormal{a part of \(\pi\)}}} \kappa\left(X_{i_1}, X_{i_2}, \ldots, X_{i_k}\right)
\tag{4}
\end{equation}
$$

 Intuitively, we often think of the cumulants $\kappa\left(X_1, \ldots, X_n\right)$ as representing the “intrinsically $n^{\textnormal{th}}$ order” part of the expectation $\mathbb{E}\left[X_1 \ldots X_n\right]$, and then we obtain the full expectation by summing up over contributions from all of these intrinsic relationships amongst subsets of the variables.

Formally, many of the nice properties of the joint cumulants come from an equivalent definition as the coefficients of the _logarithm_ of the moment generating function. They are also essentially the unique statistic such that if the $X_i$ are independent from all of the $Y_i$, then $\kappa\left(X_1 + Y_1, \ldots, X_n + Y_n\right) = \kappa\left(X_1, \ldots, X_n\right) + \kappa\left(Y_1, \ldots, Y_n\right)$, and have many other nice properties that lead them to occur frequently in statistics.

As special cases we have $\kappa\left(X\right) = \mathbb{E}\left[X\right]$ and $\kappa\left(X, Y\right) = \operatorname{Cov}\left(X, Y\right)$. We can obtain a recursive definition for $\kappa\left(X_1, \ldots, X_n\right)$ in general by solving Equation 4. For example, 

$$
\begin{equation}
    \kappa\left(X, Y, Z\right) = \mathbb{E}\left[XYZ\right] - \mathbb{E}\left[X\right]\mathbb{E}\left[Y\right]\mathbb{E}\left[Z\right] - \operatorname{Cov}\left(X, Y\right)\mathbb{E}\left[Z\right] - \operatorname{Cov}\left(X, Z\right)\mathbb{E}\left[Y\right] - \operatorname{Cov}\left(Y, Z\right)\mathbb{E}\left[X\right]
\tag{5}
\end{equation}
$$

If two variables $X$ and $Y$ are independent then _any_ cumulant involving both $X$ and $Y$ (and no other variables) is zero. In fact, for bounded variables this is equivalent to independence. This suggests a generalization of independence: we say that $X_1, X_2, \ldots, X_n$ have “no $n$\-way interactions” if any cumulant involving all of $X_1, \ldots, X_n$ (and no other variables) is zero. Of course this assumption can be overturned by noticing an $n$\-way interaction, but we propose it as a reasonable default guess.

This directly allows us to make a guess about $\mathbb{E}\left[X_1 X_2 \ldots X_n\right]$ given only lower-order information. For example, if we know the covariances of $X, Y, Z$ and assume that $\kappa\left(X, Y, Z\right) = 0$, then Equation 5 implies a guess about $\mathbb{E}\left[XYZ\right]$. In fact Gaussians have third and higher cumulants equal to zero, and so treating $3$ variables as jointly normal corresponds exactly to this special case with $n = 3$.

We won’t try to argue that this is the “right” guess, because we think that it isn’t (we’ll return to this issue in Section [[#^cumulant-propagation-and-sums|12.7]]). We do think it is better than nothing and it’s not _obvious_ how to improve on it. For example, if we want to infer $\mathbb{E}\left[XYZW\right]$ from knowledge of the second and third moments, we believe that this algorithm is much better than simply ignoring the third moments and treating $X, Y, Z, W$ as jointly Gaussian. We won’t make this claim precise.

Before explaining why we don’t yet think this is the “right” answer, we’ll show how we can use the “joint cumulants are zero” assumption in order to write down a natural generalization of covariance propagation to handle higher order interactions.

### Cumulant propagation ^cumulant-propagation-2

Using cumulants, we can generalize covariance propagation: instead of estimating the covariances $\operatorname{Cov}\left(x_i, x_j\right)$ we estimate the $n^{\textnormal{th}}$ cumulants $\kappa\left(x_{i_1}, x_{i_2}, \ldots, x_{i_n}\right)$. The update rules are now more complex, but they can still be derived directly from Equation 4. As in covariance propagation, we consider the nodes in order $x_1, x_2, \ldots x_{m}$. Whenever we consider a new node $x_k$, we can estimate the cumulants involving $x_k$ by using the definition of $x_k$, Equation 4, and the assumption that unknown cumulants are zero.

In practice, we find that tracking these higher cumulants continues to improve our estimates at the expense of additional compute (we don’t report experiments here).

As in sparse covariance propagation, we can potentially make this algorithm faster by considering a set $\pi$ of tuples $\left(x_{i_1}, \ldots, x_{i_r}\right)$ and only tracking cumulants for tuples in $\pi$ (rather than tracking all $n^{\textnormal{th}}$ cumulants for some fixed $n$). Whenever a cumulant we are not tracking appears in an equation, we assume that it is zero. For covariance propagation this only reduced the computational cost from $\left|C\right|^2$ to $\left|C\right|$, but if we are considering very large cumulants then this can mean the difference between exponential and polynomial time.

We present the pseudocode for this procedure in Algorithm 1. As written it involves an exponentially large sum over all partitions of $\left\{2, 3, \ldots, r\right\}$, but the overall algorithm can easily be sped up to $\widetilde{O}\left(\left|\pi\right|^2\right)$ by doing some elementary combinatorics and only considering non-zero terms in the sum.

Sort each $\left(x_{i_1}, \ldots, x_{i_r}\right) \in \pi$ so that $i_1 \geq \ldots \geq i_r$ $\left(S_1, S_2, \ldots, S_N\right) \gets \textnormal{the list of sorted tuples in \(\pi\), sorted in lexicographic order}$ $\left(x_{i_1}, \ldots, x_{i_r}\right) \gets S_i$ $\kappa\left(S_i\right) \gets c$ $\kappa\left(S_i\right) \gets 1$ $\kappa\left(S_i\right) \gets \mathrm{Lookup}\left(x_a, x_{i_2}, \ldots, x_{i_r}\right) + \mathrm{Lookup}\left(x_b, x_{i_2}, \ldots, x_{i_r}\right)$ $\kappa\left(S_i\right) \gets \mathrm{Lookup}\left(x_a, x_b, x_{i_2}, \ldots, x_{i_r}\right)$ $\kappa\left(S_i\right) \gets  \kappa\left(S_i\right) + \mathrm{Lookup}\left(x_a, x_{i_{j_1}}, \ldots, x_{i_{j_a}}\right) \mathrm{Lookup}\left(x_a, x_{i_{k_1}}, \ldots, x_{i_{k_b}}\right)$ $\mathrm{Lookup}\left(x_{m}\right)$

We have not argued that this is a particularly expressive proof system for realistic problems. We offer it primarily to give a concrete illustration of what a heuristic argument can look like and how the “presumption of independence” can be used to produce anytime estimates for quantities that are very hard to estimate exactly. We are tentatively optimistic that similar ideas can be generalized to obtain much better estimates for a broad range of claims, but for now that is only a vague intuitive hope. In order to actually obtain good estimates, we would likely need to address the many limitations in Algorithm 1. In the next section we list some of these problems.

### Cumulant propagation and sums of squares ^cumulant-propagation-and-sums

Cumulant propagation satisfies all of the desiderata in Section [[#^desirable-properties-for-heuristic|4]], except for _respect for proofs_. In particular, cumulant propagation often produces negative estimates $\widetilde{\mathbb{E}}\left(X^2\right) < 0$ even though it is easy to prove that $X^2 \geq 0$.

We could fix this problem by truncating cumulant propagation’s estimates—whenever we have $\widetilde{\mathbb{E}}\left(f\right) < 0$, and $\pi$ is a representation of $f$ as a sum of squares, then we could define $\widetilde{\mathbb{E}}\left(f, \pi\right) = 0$. We consider this response highly unsatisfying. In addition to throwing away all the information that went into the estimate of $\widetilde{\mathbb{E}}\left(f\right)$, and producing an implausible estimate exactly on the boundary of possibility, a simple version of this approach will also violate linearity of expectation.

Another approach would be to simply ignore the arguments raised by cumulant propagation. For example, if $\mathbb{E}\left[A\right] = \mathbb{E}\left[B\right] = \mathbb{E}\left[C\right] = \mathbb{E}\left[D\right] = 0$, but $\operatorname{Cov}\left(A, B\right) = \operatorname{Cov}\left(C, D\right) = 1$ then we could treat $\mathbb{E}\left[ABCD\right] = \mathbb{E}\left[A\right]\mathbb{E}\left[B\right]\mathbb{E}\left[C\right]\mathbb{E}\left[D\right] = 0$ by default. We consider this unsatisfying because the non-zero covariances feel like a strong _prima facie_ argument about the value of $\mathbb{E}\left[ABCD\right]$. Neglecting it seems to be ignoring important information, and once we go down that road it seems plausible we need to neglect essentially _all_ information. This can be true even if this type of argument, taken in isolation, can lead to a clearly unreasonable estimates.

Instead we’d like to find a heuristic estimator that allows us to capture the kinds of considerations raised by cumulant propagation while respecting the coherence properties in Section [[#^desirable-properties-for-heuristic|4]]—including respect for sum-of-squares proofs.

Although sum-of-squares is a specific proof system, it is quite powerful and flexible[^note-38], and we think that finding an estimator that respects sum-of-squares proofs would be a major step towards formalizing the presumption of independence in general. Although we won’t discuss the connection in detail, cumulant propagation also assigns estimates $\widetilde{\mathbb{E}}\left(C\right) \not\in[0, 1]$ for arithmetizations of boolean circuits run on boolean inputs, and we believe this failure is closely connected to negativity of squares.

In this section we will briefly discuss a few cases where cumulant propagation can produce a negative estimate for an expectation $\widetilde{\mathbb{E}}\left(X^2\right)$.

#### Imputing missing moments ^imputing-missing-moments

Suppose that I’m tracking the following means and covariances: 

$$
\begin{gather*}
    \mathbb{E}\left[X\right] = \mathbb{E}\left[Y\right] = \mathbb{E}\left[Z\right] = 0, \\
    \operatorname{Var}\left(X\right) = \operatorname{Var}\left(Y\right) = \operatorname{Var}\left(Z\right) = 1, \\
    \operatorname{Cov}\left(X, Y\right) = \operatorname{Cov}\left(Y, Z\right) = 0.9, \\
\end{gather*}
$$

 but I don’t know $\operatorname{Cov}\left(X, Z\right)$. That is, my beliefs about the covariance of $X$, $Y$, $Z$ are represented by the matrix 

$$
\begin{pmatrix}
    1 & 0.9 & ?? \\
    0.9 & 1 & 0.9 \\
    ?? & 0.9 & 1
\end{pmatrix}
$$

Now suppose we calculate $\mathbb{E}\left[(X - 2Y + Z)^2\right]$ by filling in the missing entry as zero: 

$$
\begin{align*}
    \mathbb{E}\left[(X - 2Y + Z)^2\right] &= \mathbb{E}\left[X^2\right] + 4\mathbb{E}\left[Y^2\right] + \mathbb{E}\left[Z^2\right] - 4 \mathbb{E}\left[XY\right] - 4 \mathbb{E}\left[YZ\right]  + 2 \mathbb{E}\left[XZ\right] \\
                       &= 6 - 4 \operatorname{Cov}\left(X, Y\right) - 4 \operatorname{Cov}\left(Y, Z\right) + 2 \operatorname{Cov}\left(X, Z\right) \\
                       &= -1.2 + 2 \operatorname{Cov}\left(X, Z\right) \\
                       &< 0
\end{align*}
$$

 Cumulant propagation assumes that $\operatorname{Cov}\left(X, Z\right) = 0$ since it is unknown, and therefore estimates $\mathbb{E}\left[(X-2Y+Z)^2\right] < 0$.

If we apply maximum entropy with the known covariances, we would instead make the default guess 

$$
\operatorname{Cov}\left(X, Z\right) = \frac{\operatorname{Cov}\left(X, Y\right) \operatorname{Cov}\left(Y, Z\right)}{\operatorname{Var}\left(Y\right)}
$$

 and this guess would guarantee that $\mathbb{E}\left[p(X, Y, Z)^2\right] \geq 0$ for any polynomial $p$. Other perspectives suggest the same heuristic estimate in this case, and we think it it’s quite likely to be the “right” one.

We could fix this problem in $O\left(n^2\right)$ time by finding the maximum entropy distribution consistent with a given set of moments, or by simply ensuring that we track _every_ second moment. So we only produce negative estimates if we try to use sparsity to do a heuristic evaluation in time $o\left(n^2\right)$.

We consider this a problem, but we expect some readers to be less concerned since fixing the problem requires only a polynomial time slowdown. Unfortunately, the same problem can occur when imputing higher moments, and in that case we do not know how to fix it without an exponential slowdown.

As a simple example, suppose that we are tracking the following cumulants: 

$$
\begin{align*}
    \mathbb{E}\left[X\right] = 0,\\
    \operatorname{Var}\left(X\right) = 1, \\
    \kappa_3\left(X\right) = \kappa\left(X, X, X\right) = 0, \\
    \kappa_4\left(X\right) = 100, \\
    \kappa_5\left(X\right) = 0,
\end{align*}
$$

 but are not tracking $\kappa_6\left(X\right)$. Then cumulant propagation assumes it is zero, and so $\mathbb{E}\left[X^6\right] = 15 \kappa_2\left(X\right)^3 + 15 \kappa_2\left(X\right) \kappa_4\left(X\right) = 1515$. But that implies: 

$$
\begin{align*}
    \mathbb{E}\left[\left(100 X - X^3\right)^2\right]
    &= 10000\mathbb{E}\left[X^2\right] - 200 \mathbb{E}\left[X^4\right] + \mathbb{E}\left[X^6\right] \\
    &= 10000 - 20000 + 1515 \\
    &= -8485 < 0
\end{align*}
$$

 This suggests that assuming $\kappa_6\left(X\right) = 0$ is not reasonable.

In fact there is no maximum entropy distribution subject to these limitations. You can obtain entropy arbitrarily close to a Gaussian with variance $1$ by taking $X$ to be a mixture with $(1 - \varepsilon)$ probability of being Gaussian and $\varepsilon$ probability of being equal to $\sqrt[4]{\frac {97}{\varepsilon}}$. In the limit as $\varepsilon\rightarrow 0$ the entropy approaches the entropy of a Gaussian, while $\kappa_6\left(X\right) \rightarrow \infty$. Regardless of whether or not $\kappa_6\left(X\right) = \infty$ is a reasonable best guess, this differs considerably from cumulant propagation and we don’t think it can serve as the basis for a reasonable algorithm for heuristic evaluation of arithmetic circuits.

A similar failure can arise if we know the joint distribution of any set of $5$ variables from $X_1, X_2, \ldots, X_6$ but don’t know the cumulant $\kappa\left(X_1, X_2, \ldots, X_6\right)$. In this case there is a maximum entropy distribution, for which $\mathbb{E}\left[X_1 X_2 \ldots X_6\right]$ can be expressed as a sum of rational functions of the known moments of the $X_i$. But we do not know how to approximate this best guess polynomial time and so we are interested in computationally tractable approximations which still respect coherence properties.

#### Sparse covariance propagation for linear circuits ^sparse-covariance-propagation-for

So far we’ve talked about inferring missing moments and argued that the way cumulant propagation handles this problem will lead directly to negative expectations for squares. But it’s not clear that a successful alternative to cumulant propagation needs to ever infer missing moments, rather than following a completely different strategy. In this section and the next one, we describe estimation problems where we don’t know any reasonable efficient heuristic estimator.

Suppose that $z_1, \ldots, z_n$ are independent Gaussian inputs, that $A \in \mathbb{R}^{m \times m}, B \in \mathbb{R}^{m \times m}$ are linear maps, and that $y = A z$ is a vector of $m$ intermediates, and $x = B y$ is a vector of $m$ outputs. Suppose that we want to estimate each of the variances $\operatorname{Var}\left(x_i\right)$.

We can compute exactly that 

$$
\begin{align*}
    \operatorname{Var}\left(x_i\right) &= \operatorname{Cov}\left(\sum_j B_{ij} y_j, \sum_j B_{ij}, y_j\right) \\
              &= \sum_{j,k} B_{ij} B_{ik} \operatorname{Cov}\left(y_j, y_k\right) \\
              &= \sum_{j,k} B_{ij} B_{ik} \operatorname{Cov}\left(\sum_l A_{jl} z_l, \sum_l A_{kl} z_l\right) \\
              &= \sum_{j,k, l} B_{ij} B_{ik} A_{jl} A_{kl}
\end{align*}
$$

 So estimating the variances of the $x_i$ amounts to computing all $n$ of these sums. Each sum involves $m^3$ terms. We can compute all of these sums at once by doing 3 matrix multiplications, in time $O\left(m^{\omega}\right)$, but we are interested in finding a significantly faster algorithm.

An equivalent way to think about this sum is that we are given a list of vectors $v_i$ corresponding to the rows of $A$, and we want to compute $\lvert \sum \alpha_i v_i \rvert^2$ for $m$ different vectors $\alpha$.

Sparse covariance propagation corresponds to one way to estimate this sum. By tracking only $O\left(m\right)$ of the terms $\operatorname{Cov}\left(y_j, y_k\right)$, we can obtain the following estimate in time $O\left(m^2\right)$:

-   Choose a list $S$ of $O\left(m\right)$ pairs $(j, k)$.
    
-   For each pair $(j, k) \in S$, compute $\operatorname{Cov}\left(y_j, y_k\right) = \left(AA^T\right)_{jk} = \sum_l A_{jl} A_{kl}$. Each of these $O\left(m\right)$ sums takes $m$ time to compute.
    
-   For each $i$, compute $\sum_{(j, k) \in S} B_{ij} B_{ik} \left(AA^T\right)_{jk}$. Use this as our estimator for $\operatorname{Var}\left(x_i\right)$. Each of these $m$ sums takes $O\left(m\right)$ time to compute.
    

We wanted to calculate $\operatorname{Var}\left(x_i\right)$ which is a sum of $m^3$ terms of the form $B_{ij} B_{ik} A_{jl} A_{kl}$. This approximation takes a sum of $O\left(m^2\right)$ terms and then approximates the rest as $0$.

In some cases this sparse approximation captures a significant part of the full sum. For example, if each row of $A$ is obtained by applying a random small rotation to the previous row, then $\sum_l A_{jl} A_{kl}$ decays exponentially with $\left|j-k\right|$, and so taking the set of terms near the diagonal can give you an extremely good approximation.

However, this estimate can be negative in a way that exactly mirrors the failure discussed in the previous section, so it’s clearly not the _most_ reasonable estimate. Suppose that we take $S = \left\{(j, k) : \left|j - k\right|\leq 1\right\}$, and compute $\operatorname{Var}\left(y_j\right) = 1$ and $\operatorname{Cov}\left(y_j, y_{j+1}\right) = 0.9$. The case $n = 5$ is illustrated in Figure 8.

$$
\begin{pmatrix}
        1 & 0.9 & ? & ? & ?\\
        0.9 & 1 & 0.9 & ? & ?\\
        ? & 0.9 & 1 & 0.9 & ?\\
        ? & ? & 0.9 & 1 & 0.9\\
        ? & ? & ? & 0.9 & 1\\
    \end{pmatrix}
$$

Suppose $(AA^T)_{ij} = \operatorname{Cov}\left(y_i, y_j\right)$ is indicated above, where we’ve computed covariances only for $\left|i - j\right| \leq 1$. If we simply drop the terms marked $?$, we obtain the estimate $\operatorname{Var}\left(y_1 - y_2 + y_3 - y_4 + y_5\right) = -2.2$. It would be better to make the maximum entropy guess $0.9^k$ for the covariances $\operatorname{Cov}\left(y_i, y_j\right)$ with $\left|i - j\right| = k$. This results in the estimate around $+1$ instead of $-2.2$. For tree sparsity patterns, it is possible to compute this maximum entropy estimate for $\operatorname{Var}\left(\sum \alpha_i y_i\right)$ in time $O\left(m\right)$.

Now consider the case where a row of $B$ consists of alternating signs, i.e where $x_i = \sum_{j} \left(-1\right)^j y_j$. Our estimate is: 

$$
\begin{align*}
    \operatorname{Var}\left(x_i\right) &= \sum_j \operatorname{Var}\left(y_j\right) + 2 \sum_j \operatorname{Cov}\left(y_j, y_{j+1}\right) \\
              &= m - 1.8 (m - 1) \\
              &< 0
\end{align*}
$$

 At this point it’s not clear what we should estimate for $\operatorname{Var}\left(x_i\right)$. We were interested in the sum of $m^3$ terms, which we knew would be positive. We’ve added up $m^2$ of those terms and found the sum to be negative. The question is what estimate we give for the remaining terms. Simply estimating $\operatorname{Var}\left(x_i\right) = 0$ amounts to assuming that the unobserved terms exactly cancel the observed terms, which seems like a bad estimate that throws away information.

In the special case where we know $\operatorname{Var}\left(y_j\right)$ and $\operatorname{Cov}\left(y_j, y_{j+1}\right)$ we believe this question has a nice answer. Namely, we should make the maximum entropy assumption that 

$$
\operatorname{Cov}\left(y_j, y_k\right) = \frac{ \operatorname{Cov}\left(y_j, y_{j+1}\right) \operatorname{Cov}\left(y_{j+1}, y_{j+2}\right) \ldots \operatorname{Cov}\left(y_{k-1}, y_k\right)}
{\operatorname{Var}\left(y_{j+1}\right)\operatorname{Var}\left(y_{j+2}\right)\ldots\operatorname{Var}\left(y_{k-1}\right)}.
$$

 It turns out that this always results in a non-negative estimate for $\operatorname{Var}\left(x_i\right)$, and moreover that the estimate can be computed in linear time using dynamic programming.

We don’t know whether it is possible to generalize this algorithm. But at any rate, we think that it should be possible to find a better estimate than $\operatorname{Var}\left(x_i\right) = 0$. If this is _not_ possible then in our view it calls into question some of our optimistic intuitions about how anytime estimates should work and why it should be possible to produce them.

#### Estimating the permanent of a PSD matrix ^estimating-the-permanent-of

In this section we describe an estimation problem where we don’t know how to obtain reasonable estimates in polynomial time. We discuss the connection to cumulant propagation at the end of the section.

For an $n \times n$ matrix $A$, define the permanent 

$$
\mathop{\mathrm{perm}}\left(A\right) = \sum_{\sigma} \prod_i A_{i\sigma\left(i\right)}
$$

 where the sum is taken over every permutation $\sigma\colon \left\{1, 2, \ldots, n\right\} \rightarrow \left\{1, 2, \ldots, n\right\}$. Computing or even approximating the permanent is very difficult.

One way to learn about $\mathop{\mathrm{perm}}\left(A\right)$ is to compute 

$$
\widetilde{\mathbb{E}}\left(\mathop{\mathrm{perm}}\left(A\right), \pi\right) = \sum_{\sigma \in \pi} \prod_i A_{i\sigma\left(i\right)}
$$

 for a particular set of permutations $\pi = \left\{\sigma_1, \ldots, \sigma_m\right\}$. As discussed in Section [[#^considering-concrete-paths|9.2.5]], computing the sum of a subset of terms gives us a heuristic estimate for the full sum. This is usually a poor estimate unless the set $\pi$ is exponentially large. But if $A$ is very structured or sparse it can be possible for a small set of terms to capture a significant part of the sum, and so this heuristic argument can sometimes have a meaningful effect.

If $A$ is positive semi-definite, i.e. if it can be written in the form $A_{ij} = \langle v^i, v^j \rangle$ for a list of vectors $v^i \in \mathbb{R}^n$, then $\mathop{\mathrm{perm}}\left(A\right)$ can be written as a sum of squares and so must be non-negative: 

$$
\mathop{\mathrm{perm}}\left(A\right) = \frac 1{n!} \sum_{r_1, r_2, \ldots, r_n \in \left\{1, 2, \ldots, n\right\}}
\left(\sum_{\sigma} \prod_i v^{\sigma\left(i\right)}_{r_i}\right)^2.
$$

 The exact form of this sum of squares is not important; what matters is that we have a simple proof of non-negativity.[^note-39]

Unfortunately, we can have $\widetilde{\mathbb{E}}\left(\mathop{\mathrm{perm}}\left(A\right), \pi\right) < 0$. This leaves us in the same situation as in the preceding two sections: clearly we’d be better off just outputting $0$ rather than a negative estimate for $\mathop{\mathrm{perm}}\left(A\right)$. But outputting $0$ involves assuming that the unobserved terms in the sum $\mathop{\mathrm{perm}}\left(A\right)$ exactly cancel out the observed terms, which again seems like a bad estimate that throws away information and leads to incoherence. So it’s natural to ask: can we do better?

We are aware of a strictly better estimator in the special case where the permutations $\sigma_1, \ldots, \sigma_m$ commute and therefore generate an abelian group $G \subset S_n$. In this case it turns out to be possible to construct a set of random variables such that each term $\prod_i A_{i \sigma\left(i\right)}$ is a pairwise correlation. We can then obtain a reasonable estimate of $\mathop{\mathrm{perm}}\left(A\right)$ by making a maximum entropy assumption about those variables. Unfortunately, it is not clear how to generalize this idea to general sets of permutations $\pi$.

Computing $\mathop{\mathrm{perm}}\left(A\right)$ for a PSD matrix $A$ is closely related to computing $\mathbb{E}\left[\left(X_1 \ldots X_n\right)^2\right]$ where the $X_i$ have covariance matrix $A$. In fact, $\mathbb{E}\left[\left(X_1 \ldots X_n\right)^2\right]$ is represented by the same sum as the permanent, but where each term $\prod_i A_{i \sigma\left(i\right)}$ is multiplied by a factor of $2^{\left|\sigma\right|}$ where $\left|\sigma\right|$ is the number of cycles in $\sigma$. Pointing out particular non-zero terms is one way to approximate this sum, and this corresponds to cumulant propagation when the set of observed cumulants takes a particular special form. Thus cumulant propagation can produce negative estimates for $\mathbb{E}\left[\left(X_1 \ldots X_n\right)^2\right]$ in a way that is analogous to our negative estimates for the permanent. The factor of $2^{\left|\sigma\right|}$ means that the two problems aren’t exactly equivalent, but similar difficulties seem to arise in both cases. Moreover, a reasonable heuristic estimator should ultimately be able to handle both of these cases, and so we regard it as a reasonable test case for formalizing heuristic arguments.

## Cherry-picking arguments ^cherry-picking-arguments

In Section [[#^heuristic-arguments-sometimes-make|4.1]] we argued that heuristic arguments don’t always bring our estimates closer to reality. That is, if we form an estimate based on adversarially chosen arguments then we can reliably do worse than if we had made a completely naive guess. This is a difference from the situation with proofs, where a proof always gets you closer to the truth no matter where it came from.

In this section we present a few examples showing that various simple fixes do not address the problem. We then discuss why we think heuristic estimators are valuable despite these limitations, and suggest a weaker convergence bound that we think may be achievable.

### Arguments can make estimates worse ^arguments-can-make-estimates

All of our examples will involve quantities of the form $X = \sum_{x \in \mathcal{X}} \alpha_x f\left(x\right)$. We will assume that $\widetilde{\mathbb{E}}\left(f(x)\right) = 0$ for a generic $x$, i.e. that $\widetilde{\mathbb{E}}$ sees no reason that $f$ should be biased to be positive or negative. We’ll also assume that $\widetilde{\mathbb{E}}$ sees no correlation between different values of $f$, and more generally that the only way $\widetilde{\mathbb{E}}$ ever changes its mind about any value $f(x)$ is by computing it.

For any $x \in X$, we write $\pi_x$ for the argument that exactly calculates a single value $f(x)$. As discussed in Section [[#^considering-concrete-paths|9.2.5]], we expect a reasonable heuristic estimator to satisfy: 

$$
\widetilde{\mathbb{E}}\left(X, \pi_{x_1}, \ldots, \pi_{x_k}\right) = \sum \alpha_{x_k} f\left(x_k\right).
$$

In Section [[#^heuristic-arguments-sometimes-make|4.1]] we considered finite sums $\sum_{x=1}^n f(x)$ where each $f\left(x\right) = \pm 1$. We observed that typically there will be particular values $f(x)$ which have the opposite sign from $X$. For any such $x$, $\widetilde{\mathbb{E}}\left(X, \pi_x\right)$ will be a worse estimate than $\widetilde{\mathbb{E}}\left(X\right)$. If $x_1, \ldots, x_k$ is the list of all $x$ for which $f(x)$ has the opposite sign from $X$, then $\widetilde{\mathbb{E}}\left(X, \pi_{x_1}, \ldots, \pi_{x_k}\right)$ can be an arbitrarily bad estimate for $X$.

### $\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right)$ does not always converge ^widetilde-mathbb-e-parentheses

Although it is possible to cherry-pick arguments pointing in the wrong direction, we might still hope that if we give $\widetilde{\mathbb{E}}$ _enough_ good arguments then it will eventually converge to the truth, and that the resulting correct estimate will be robust even if we supply additional cherry-picked arguments.

Unfortunately this does not seem to be the case in general. Suppose that 

$$
X = \sum_{x = 1}^{\infty} \frac {f(x)}{x^s}
$$

 for a constant $1/2 < s < 1$, where each $f(x)$ is $\pm 1$.

Then we have 

$$
\begin{align*}
    \mathbb{E}\left[X^2\right] &= \sum_{x = 1}^{\infty} \frac{f(x)^2}{x^{2s}} \\
             &= \sum_{x = 1}^{\infty} \frac 1{x^{2s}} \\
\end{align*}
$$

 which converges for every $s > 1/2$. Thus $\mathbb{E}\left[X^2\right]$ is finite and so $X$ is finite almost surely. (This is a probabilistic argument that we are making on the outside, not a heuristic argument that $\widetilde{\mathbb{E}}$ is evaluating.)

But on the other hand, we have: 

$$
\begin{align*}
    \mathbb{E}\left[\sum_{x : f(x) > 0} \frac {f(x)}{x^s}\right]
    &= \sum_{x = 1}^{\infty} \frac {1}{2 x^s} \\
    &= \infty
\end{align*}
$$

 As a result, no matter how many arguments $\pi_x$ we have seen, it’s most likely the case that the estimate $\widetilde{\mathbb{E}}\left(X\right)$ can be driven arbitrarily high by presenting additional arguments $\pi_x$ for $x$ with $f(x) > 0$. Similarly, $\widetilde{\mathbb{E}}\left(X\right)$ can be driven arbitrarily low by presenting $\pi_x$ for $f(x) < 0$.

This issue is clearest in the case of infinite sums, where $\widetilde{\mathbb{E}}$ literally never converges. However this also corresponds to a serious quantitative failure for finite sums: even if the variance of $\sum_{x \in \mathcal{X}} \alpha_x f(x)$ is $\varepsilon^2$, cherry-picking arguments can still lead us to overestimate or underestimate $X$ by $\varepsilon\sqrt{\left|X\right|}$, and we do not converge until $\widetilde{\mathbb{E}}$ has computed the value $f(x)$ for a large fraction of all $x \in \mathcal{X}$.

### Debate does not lead to convergence ^debate-does-not-lead

So far we’ve argued that there _exist_ arguments $\pi$ that would cause $\widetilde{\mathbb{E}}$ to produce bad estimates. But instead of considering adversarially chosen arguments designed to mislead, we could imagine the result of a debate where some arguments are chosen to make $\widetilde{\mathbb{E}}\left(X\right)$ large and others are chosen to make $\widetilde{\mathbb{E}}\left(X\right)$ small. That is, we could consider the estimate 

$$
\begin{equation*}
\max_{\pi_1} \min_{\pi_2} \max_{\pi_3} \ldots \widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right),
\end{equation*}
$$

 perhaps with a restriction on the length of each argument $\pi_i$.

Unfortunately this approach also does not produce good estimates. For example suppose that instead of $f(x) = \pm 1$, each $f(x)$ has a $1/3$ probability of being equal to $2$ and a $2/3$ probability of being equal to $-1$. And suppose each argument $\pi_{x}$ has equal length. Then consider the same sum as before: 

$$
X = \sum_{x = 1}^{\infty} \frac {f(x)}{x^s},
$$

 for a constant $1/2 < s < 1$.

It’s easy to see that $X$ almost surely converges to a finite value. But arguments that $X$ is large are “more efficient” since each of them gives us a value where $f(x) = 2$, while each argument that $X$ is small gives us one value where $f(x) = -1$. This means that in the limit our estimates for $X$ converge to $+\infty$ instead of the correct finite value.

More precisely, let $x^+_1, x^+_2, \ldots$ and $x^-_1, x^-_2, \ldots$ be the enumeration of integers $x$ where $f(x) = 2$ and $f(x) = -1$ respectively. Then $x^+_k$ is roughly $3k$, while $x^-_k$ is roughly $(3/2)k$, so we have: 

$$
\begin{align*}
    \max_{\pi_1} \min_{\pi_2} \max_{\pi_3} \ldots \widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right)
    &=\widetilde{\mathbb{E}}\left(X, \pi_{x^+_1}, \pi_{x^-_1}, \ldots, \pi_{x^+_{n/2}}, \pi_{x^-_{n/2}}\right) \\
    &= \sum_{i = 1}^{n/2} \frac {f\left(x^+_i\right)}{\left(x^+_i\right)^s} +
        \sum_{i = 1}^{n/2} \frac {f\left(x^-_i\right)}{\left(x^-_i\right)^s} \\
    &= 2 \sum_{i = 1}^{n/2} \frac {1}{\left(x^+_i\right)^s} - \sum_{i = 1}^{n/2} \frac 1{\left(x^-_i\right)^s} \\
    &\approx 2 \sum_{i = 1}^{n/2} \frac 1{(3 i)^s} - \sum_{i = 1}^{n/2} \frac 1{\left(3i/2\right)^s} \\
    &= \left(\frac 2{3^s} - \frac {2^s}{3^s}\right) \sum_{i = 1}^{n/2} \frac 1{i^s} \\
    &\rightarrow  \infty
\end{align*}
$$

### Provable bounds do not lead to convergence ^provable-bounds-do-not

So far we’ve seen problems for quantities $X$ that are defined as convergent but not absolutely convergent series, for which there is no provable bound on $X$. We might hope that if we can prove $\ell \leq X \leq h$ then we can converge in finite time and bound the damage done by cherry-picking based on $h - \ell$.

Unfortunately this also seems to be impossible.

Define the function $\sigma\colon \mathbb{R} \rightarrow [-1, 1]$ via 

$$
\sigma\left(x\right) = \begin{cases}
        -1 & \textnormal{for \(x < -1\)} \\
        \phantom{-}x & \textnormal{for \(-1 < x < 1\)} \\
        \phantom{-}1 & \textnormal{for \(1 < x\)}
    \end{cases}
$$

 Consider the quantity 

$$
X = \inf_{n} \mathop{\smash{\mathrm{sup}}}_{N > n} \sigma\left(\sum_{x = 1}^N \frac {f(x)}{x^{2/3}}\right),
$$

 where $f(x) = \pm 1$ is unbiased and independent for different values of $x$. If we choose any set $x_1 < \ldots < x_k$ such that 

$$
\sum_{i=1}^k \frac{f(x_i)}{x_i^{2/3}} < -100,
$$

 then we claim that $\widetilde{\mathbb{E}}\left(X, \pi_{x_1}, \ldots, \pi_{x_k}\right) \approx -1$. This is because $\widetilde{\mathbb{E}}$’s estimate for variance of $\sum \frac{f(x)}{x^{2/3}}$ is about $3.6$, and so it assigns a $<0.1\%$ chance that the sum of the remaining terms is more than $99$, and by a more careful analysis and union bound we could compute that it assigns at most a $<1\%$ chance that any of the partial sums of the remaining terms is ever more than $99$. It therefore has less than a $1\%$ chance that any of the partial sums for $N > x_k$ is ever more than $99$, and hence less than $1\%$ chance that the inf sup is more than $-1$. As a result, $\widetilde{\mathbb{E}}$ should be at most $-0.99$.

Similarly, if we choose a set of $x_i$ for which the partial sum is more than $100$, we have $\widetilde{\mathbb{E}}\left(X, \pi_{x_1}, \ldots, \pi_{x_k}\right) > 0.99$.

Because $\sum x^{-2/3} \rightarrow \infty$, no matter how many $x_i$ we have already calculated, we can always find a suitable larger set of $x_i$ for which the sum is either less than $-100$ or more than $100$. As a result $\widetilde{\mathbb{E}}$ never converges but can be made to oscillate back and forth between $-1$ and $1$ forever, regardless of the true value of $X$.

(By combining this with a variant of the counterexample from the last section, we can also obtain a case where a debate would oscillate forever.)

### Where this leaves us ^where-this-leaves-us

Heuristic estimates $\widetilde{\mathbb{E}}\left(X, \pi_1, \ldots, \pi_n\right)$ can be systematically inaccurate if the arguments $\pi_1, \ldots, \pi_n$ are adversarially chosen. They fail to converge even if we have a provable bound on $X$. And eliciting arguments from two competing debaters does not address this difficulty.

This suggests that we need to be careful when interpreting heuristic estimates derived from untrusted arguments. In order to produce robust estimates _conditioned_ on the set of arguments $\pi_1, \ldots, \pi_n$ we would need to have reasonable beliefs about how the arguments $\pi_i$ were selected and then revise our beliefs not only based on the content of those arguments but also based on the evidence about the process that produced those arguments. For example, if we see a particular argument $\pi$ and know that it was chosen to maximize $\widetilde{\mathbb{E}}\left(X, \pi\right)$, then we would need to update our beliefs based on the fact that no stronger argument was found. This kind of reasoning cannot be captured in the setting of a heuristic estimator that makes no assumptions about how the arguments $\pi_i$ were selected.

We do not think that these issues interfere with interpreting $\widetilde{\mathbb{E}}$ as a reasonable belief in light of the arguments $\pi_1, \ldots, \pi_n$, in the case where those arguments were not cherry-picked. Moreover, we think that studying heuristic estimators can still clarify a key part of how we should revise our beliefs based on the contents of arguments, even if it does not capture fully general Bayesian reasoning about the source of those arguments.

Fortunately, it currently seems like these issues are restricted to “poorly behaved” functions $X$, rather than occurring for arbitrary quantities.[^note-40] This is what makes it plausible that we can achieve our ambitious goal in Section [[#^formalizing-intuitively-valid-heuristic|5]], which effectively requires that $\widetilde{\mathbb{E}}$ quickly converge to a reasonable estimate. If it turned out that a more subtle version of cherry-picking could cause convergence problems when estimating arbitrary quantities $X$, it would make this goal impossible and would call into question the entire project of formalizing heuristic arguments.

## Applications to machine learning ^applications-to-machine-learning

Our interest in heuristic arguments is ultimately motivated by potential applications to machine learning. We’ll briefly describe this motivation here, but mostly defer the discussion to future articles.

In modern machine learning, we understand the behavior of large neural networks primarily by running them on a huge number of examples. To select a model, we pick parameters that perform well on a set of training examples (“empirical risk minimization”). To determine that a model is safe, we measure its behavior on a set of held out validation examples.

Empirical risk minimization has a hard time estimating low-probability risks, predicting the behavior of a system on novel input distributions, or identifying when a model is giving an answer for an unexpected reason. We are concerned that over the long term these limitations could lead to catastrophic alignment failures.

Researchers in AI alignment are extremely interested in other strategies for learning about models that could overcome these limitations of empirical risk minimization, including _interpretability_ and _formal verification_. But in practice both approaches are quite difficult to apply to state of the art models, and there are plausible stories for why these might be fundamental difficulties:

-   Interpretability typically aims to help humans “understand what the model is doing.” But it’s not clear whether all models actually operate in a way that is amenable to human understanding, or even exactly what we mean by “understanding.”
    
-   Formal verification is an incredibly demanding standard which delivers perfect confidence. It’s not clear we have any right to expect formal proofs even for very simple properties of very small models.
    

We are interested in formalizing heuristic arguments because they seem like a third option for analyzing ML systems that might be easier than either interpretability or formal verification.

|  | Human understandable | Machine verifiable |
| --- | --- | --- |
| Confident and final |  | Formal proof |
| Uncertain and defeasible | Interpretability | **Formal heuristic argument** |

More concretely, we are particularly interested in two applications of formal heuristic arguments:

Avoiding catastrophic failures.

Heuristic arguments can let us better estimate the probability of rare failures, or failures which occur only on novel distributions where we cannot easily draw samples. This can be used during validation to estimate risk, or potentially during training to further reduce risk.

Eliciting latent knowledge.

Heuristic arguments may let us see “why” a model makes its predictions. We could potentially use them to distinguish cases where similar behaviors are produced by very different mechanisms—for example distinguishing cases where a model predicts that a smiling human face will show up on camera because it predicts there will actually be a smiling human in the room, from cases where it makes the same prediction because it predicts that the camera will be tampered with. Achieving this goal requires a “deductive” heuristic estimator in the sense described in Section [[#^inductive-vs-deductive-arguments|10]].

Neither of these applications is straightforward, and it should not be obvious that heuristic arguments would allow us to achieve either goal. But we hope they can illustrate the kind of application of heuristic estimators we have in mind, and to help explain our optimism that new strategies for reasoning about learned models could open new angles of attack on AI alignment. We’ll discuss these applications in much more detail in future articles.

:::


[^note-1]: Throughout this section we will ignore $o\left(\frac 1{\ln N}\right)$ correction terms.
[^note-2]: The expected number of twin primes less than $N$ approaches infinity as $N$ grows. So if we treat each event of the form ($x$ is prime and $x+2$ is prime) as independent, then with probability $1$ infinitely many of them occur.
[^note-3]: If we apply the presumption of independence again then we can predict that the number of twin prime pairs in the interval is approximately Poisson with mean 1—the same as the count of heads if you flip $100$ coins each with a $1\%$ probability of heads.
[^note-4]: This constant is derived from the obvious negative correlation between the events ($p$ divides $x$) and ($p$ divides $x+2$) for $p > 2$. The Hardy-Littlewood conjecture implies that this is the true asymptotic density of the twin primes, i.e. that there are no further corrections. This conjecture appears to agree with experimental data but is expected to be extremely difficult to prove. There are other correction terms, which meaningfully change the expected number of twin primes between $10,000$ and $10,100$ but are asymptotically negligible in $N$.
[^note-5]: For example, we reviewed the list of 105 pages in the Wikipedia category [“Unsolved problems in number theory.”](https://en.wikipedia.org/wiki/Category:Unsolved_problems_in_number_theory) Based on random sampling, we estimate that for more than 75% of these conjectures the authors would be able to find a probabilistic heuristic argument that we find convincing. (About 30% are justified by the Cramér random model of the primes, and about 6% are justified by the kind of Diophantine equation heuristic discussed in Appendix [[#^fermats-last-theorem-note-14|9.1]].) The counterexamples primarily involve non-elementary statements or arguments that are difficult to assess without expertise in number theory, and we believe that a domain expert could probably give probabilistic heuristic arguments for more than 90% of these statements. Those estimates should not be taken too seriously, especially given that we don’t have a formalization of heuristic arguments that we can use to reduce experimenter bias or assess how often it is possible to give spurious arguments for incorrect conclusions. But we think they still give some general indication that the presumption of independence is often sufficient to justify plausible conjectures.
[^note-6]: For example, we could define a very bad estimate $\widetilde{\mathbb{P}}\left(\varphi\right)$ based purely on the presumption of independence and the structure of $\varphi$. We can take $\widetilde{\mathbb{P}}\left(A \wedge B\right) = \widetilde{\mathbb{P}}\left(A\right) \widetilde{\mathbb{P}}\left(B\right)$, and treat $\widetilde{\mathbb{P}}\left(\forall x \colon \varphi\left(x\right)\right)$ as an a very large conjunction. As a result, almost any universally quantified statement will have $0$ probability by default.
[^note-7]: This definition is most straightforward if $X$ is bounded, i.e. if we have a proof that $\ell \leq X \leq h$ for some particular real numbers $\ell$ and $h$. If there are no provable bounds on $X$ then the expectation may be infinite or undefined. For now we will set this issue aside; a concerned reader can restrict their attention to quantities $X \in [0, 1]$.
[^note-8]: The quantitative closeness depends on the problem, and in particular on how much we think that further valid arguments should be able to change $\widetilde{\mathbb{E}}$’s views. For example, in the case of estimating the number of twin primes less than $N$, we expect the correction to be asymptotically negligible in $N$, and any non-negligible correction would contradict the Hardy-Littlewood conjecture. In the case of estimating the probability of a zero of SHA-256, it is easy to find arguments resulting in adjustments on the order of $2^{-256}$, but any argument leading to a revision of say $2^{-128}$ would be a major development in cryptanalysis.
[^note-9]: Alternatively we could search for a sufficiently simple estimator that satisfies Equation 1. Or we could informally evaluate a proposed estimator based on an intuitive judgment about whether it looks like it would it generalize to new claims.
[^note-10]: This notational difference suggests a more subtle difference in how $\widetilde{\mathbb{E}}$ actually performs the estimate. We will often describe heuristic estimators that effectively consider each input $z_i$ as an unknown boolean variable with probability $1/2$, rather than estimators that consider a sum over the set of all possible inputs $z_i$. In particular, $\widetilde{\mathbb{E}}$ estimates $\mathbb{P}\left(C\right)$ in the same way that it would estimate the value of $C$ when run on a set of $m$ uncomputable and apparently unbiased inputs. For estimators with this form, it is more correct to talk about $\widetilde{\mathbb{E}}\left(C(z)\right)$ rather than $\widetilde{\mathbb{E}}\left(\mathbb{P}\left(C\right)\right)$, where $z$ is a special symbol representing an unknown set of inputs specified to have a uniform distribution. These two perspectives are essentially equivalent due to linearity of expectation.
[^note-11]: To be more precisely analogous we could consider heuristic evaluation of _formulas_ instead of circuits, i.e. we could require that each node be used at most once as the input to another gate. This even simpler problem also seems challenging and interesting.
[^note-12]: For example, if we extend the Cramér model by allowing an argument to prove _any_ property $\varphi$ of the primes and then treating the primes as a random set satisfying that property, then we can trivially produce arbitrary conclusions.
[^note-13]: Similarly, a neural network trained to predict the truth of mathematical statements may eventually learn to be a good heuristic estimator, but our goal is to understand _what such a model learns_ rather than to describe the process for learning. (Though as discussed in Appendix [[#^applications-to-machine-learning|14]], and our primary interest is in using heuristic arguments to reason _about_ neural networks, rather than expecting them to capture the kind of reasoning performed _by_ neural networks.)
[^note-14]: This heuristic argument for Fermat’s last theorem is standard, essentially the same as the one appearing in \[11\] and \[23\].
[^note-15]: Note that the heuristic argument is wrong about the case $n = 3$, see Section [[#^the-case-n-3|9.1.4]].
[^note-16]: We actually care about a particular weighted sum of values of $a$ that focuses on small values, and so we could make a more precise estimate here either by calculating exactly or by performing another heuristic estimate. But we can ignore these factors by presuming that $\varphi\left(a\right)/a$ is independent of $1/a^{n-2}$.
[^note-17]: Keeping in mind that we also want to condition on no solutions with $a' < a$, and therefore only consider values of $x$ that are relatively prime to $a$. So we can separately consider the case where $a$ is divisible by $5$, in which $x$ is not divisible by $5$, and the case where $a$ is not divisible by $5$ such that $x$ is uniformly random mod $5$.
[^note-18]: Determining whether there are any cycles with non-zero weight is NP-hard, and if the weights can be positive or negative then even determining the sign of the total weight of Hamiltonian cycles is #P-hard.
[^note-19]: To be more precise, we really want to use $\widetilde{\mathbb{E}}$ to estimate the typical value of $f$ on $\mathcal{X}\setminus \left\{x_1, \ldots, x_k\right\}$. In the case of Hamiltonian cycles this introduces an extremely small correction: if we have seen a single cycle, then each of the edges in that cycle only appears with probability $\frac 1{n-1} - O\left(\frac 1{(n-1)!}\right)$ amongst the remaining $(n-1)!$ cycles. So instead of using a uniform distribution over edges we should revise all of our arguments to use this slightly non-uniform distribution. But this correction is very tiny unless $k$ is close to $(n-1)!$.
[^note-20]: The bias drops off as $\frac 1{t^{15}}$ because there is a probability of $O\left(\frac 1t\right)$ that any given pool ball is close enough to traveling perfectly up and down that it will remain roughly at the same $x$ coordinate for $t$ seconds. We need this event to occur for $15$ independent balls.
[^note-21]: It seems challenging to rule out even for a very large pool table. A small imbalance of pool balls towards the left half of the table provides a potential source of free energy, and while it seems difficult to build robust replicators out of pool balls we do not see how to rule out the possibility. (In this case it _might_ be possible to provably rule out life because the imbalance of pool balls is the only source of free energy and decays exponentially quickly, but if there had been any dynamics with longer timescales it no longer seems possible.) Note that the picture would be much simpler if we had initialized every pool ball randomly rather than restricting to the left half of the table.
[^note-22]: Intuitively it shouldn’t be possible to prove anything about an obfuscated circuit, but we can also prove this formally in the case of proving $\forall z \colon C\left(z\right) = 1$ under indistinguishability obfuscation \[2\] by using the “punctured programming” approach \[24\]. Let $f$ be an indistinguishability obfuscator, such that it is computationally difficult to distinguish $f\left(C\right)$ from $f\left(C'\right)$ whenever $C$ and $C'$ implement the same functionality. We’ll show that we can’t distinguish $f(C)$ from a circuit that outputs $0$ on a single pseudorandomly chosen input, and therefore we can’t prove $\forall z \colon f(C)(z) = 1$. Let $g\colon \left\{0, 1\right\}^{m+1} \rightarrow \left\{0, 1\right\}^{m+1}$ be a one-way function, and define $C'(z) = 0$ if $g(0z) = 0^{m+1}$ and $C'(z) = C(z)$ otherwise. Then there is a half chance that $C' = C$, in which case we can’t distinguish $f(C)$ from $f(C')$. But even if we are given $C'$, we can’t tell the difference between cases where $g^{-1}\left(0^{m+1}\right)$ starts with $0$, in which case $C'$ is equal to $0$ on a single point, from cases where $g^{-1}\left(0^{m+1}\right)$ starts with $1$, in which case $C'$ equals $C$. So we also can’t distinguish $f(C)$ from $f(C')$ in cases where $C'$ outputs $0$ on a single input.
[^note-23]: There is a large philosophical literature on whether and when proofs are “explanatory.” We don’t intend to address the full complexity of that question, but just to make the much more mild claim that a proof is _more_ like an explanation than a Monte Carlo estimate is. A more precise statement of our view is that **short, constructive** proofs behave like explanations, but we won’t defend even that weaker claim.
[^note-24]: One distinction with proofs is that we might find other structure about the primes that either makes the twin prime conjecture false or makes it true for a completely different reason. Sometimes this indicates that our initial explanation was wrong, but it can also be the case that a single claim has multiple sufficient explanations. For example, $A \vee B$ will often have two sufficient explanations, neither of which is wrong.
[^note-25]: Though in the case of Monte Carlo estimates, we can often obtain likelihood ratios so large that they completely overwhelm the prior.
[^note-26]: We plan to discuss this hope in more detail in a forthcoming article, along with some recent examples of using this approach to solve problems in AI safety. We still have a lot of uncertainty but have some indication that this plan is coherent.
[^note-27]: We call this property _soundness_ in analogy with logical soundness because it means that if $\widetilde{\mathbb{E}}$ is very confident about a statement, and nothing can change its mind, then the statement is true. By analogy we might use _completeness_ for the property that $\widetilde{\mathbb{E}}$ eventually becomes confident about every true statement, which we discuss in Section [[#^incompleteness-and-diagonalization|11.5]].
[^note-28]: Though note that it is not easy to accept such arguments while satisfying the desiderata in Section [[#^desirable-properties-for-heuristic|4]].
[^note-29]: For example Chaitin’s Omega, the probability that a randomly chosen Turing machine halts. The key feature of such numbers is that for any computable process, the probability of guessing the first $k$ bits of the number correctly provably decays like $c 2^{-k}$ for some constant $c$.
[^note-30]: We’ll consider the length $\left|\varphi\right|$ of a sentences when it is written in binary in some particular prefix-free encoding, i.e. a representation such that no syntactically valid sentence is a prefix of any other and hence $\sum_{\varphi} 2^{-\left|\varphi\right|} \leq 1$.
[^note-31]: The set of $N$ satisfying this property has logarithmic density more than 99%. It is straightforward but slightly subtle to translate this into a true statement of the form $\forall n \colon \varphi\left(n\right)$.
[^note-32]: \[15\] contains a clear discussion of this and other similar phenomena. In fact there is a heuristic argument that the prime powers ought to be uniform mod $4$, and hence that the primes themselves must be biased towards $1$, though we don’t believe this argument was recognized for many decades after Chebyshev’s observation. This can be derived from a generalization of the Riemann hypothesis, which also has no proof but is heuristically supported, see \[19\].
[^note-33]: We don’t believe that this observation is the result of a selection effect. Many researchers would consider a completely-inexplicable empirical regularity to be extremely interesting, and so we would expect potential counterexamples to this empirical regularity to be particularly **unlikely** to be forgotten.
[^note-34]: We are working with ZFC rather than a theory of arithmetic because it seems that set theory really is necessary in order to carry out the kind of intuitive argument that mathematicians make for the consistency of weaker systems—we believe that axiom systems are consistent because they have models, and so we need a theory rich enough to be able to talk about such models. Unfortunately using an expressive enough set theory to capture such arguments makes it even harder to think about how a hypothetical heuristic estimator might work.
[^note-35]: This comes down to a counting argument and isn’t entirely clear. In particular, we need to consider the number of valid $n$\-step proofs, together with the heuristic probability that a particular $n$\-step proof derives a contradiction given that no smaller proof has. We won’t discuss this argument, but we think that a reasonable heuristic estimator would probably conclude that any given set of axioms is almost surely inconsistent as a default until it sees something about the structure of the axioms that explains why they could be consistent.
[^note-36]: Technically we start with $V_0 = \emptyset$, define $V_{n+1} = \mathcal{P}\left(V_n\right)$, and define $V_\alpha = \cup_{\beta < \alpha} V_{\beta}$ for each limit ordinal $\alpha$. ZFC is able to construct $V_{\alpha}$ for every ordinal $\alpha$, and can prove that $V_{\kappa}$ is a transitive model of ZFC whenever $\kappa$ is an inaccessible cardinal.
[^note-37]: I.e. $\kappa$ is bigger than $\cup_{x \in S} x$ for any set $S$ smaller than $\kappa$ each of whose elements is smaller than $\kappa$.
[^note-38]: For example, positive expectations for sums of squares is a sufficient condition for a set of moments to be realizable, and sum of squares proofs play a central role in the theory of approximate constraint satisfaction.
[^note-39]: No algorithm is known for computing the permanent even for PSD matrices. The best known approximation is given by \[1\] and has exponential error.
[^note-40]: It seems plausible that there is some analog of absolute integrability which would cause $\widetilde{\mathbb{E}}$ to converge, but it is not clear how to define such a notion and disappointing that it would not follow from a provable bound.

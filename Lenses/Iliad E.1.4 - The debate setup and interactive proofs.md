---
id: '07c4339f-57bf-4fa9-b2fc-4dbd3ca576fb'
title: "E.1.4 The debate setup and interactive proofs"
tldr: "The debate setup with Alice, Bob and a judge, the scalable oversight problem, and interactive proofs from NP and Merlin-Arthur (MA) to IP = PSPACE, with one exercise."
summary_for_tutor: "Sections 7 to 9 of Iliad worksheet E.1: the debate setup (question, provers Alice and Bob, polynomial-size judge, tic-tac-toe example), the intuition for scalable oversight, and interactive proofs: prover and verifier, Examples 9.1 and 9.2 (graph isomorphism and non-isomorphism), completeness c and soundness s, the Merlin-Arthur class MA with its completeness and soundness criteria, amplification, and IP = PSPACE. Contains Exercise 9.1 (NP is contained in MA). Keep the names Alice, Bob, Arthur and Merlin. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 7. The Debate Setup

[The original AISvD paper](https://arxiv.org/pdf/1805.00899)'s core idea is to align AI by having two systems debate each other in front of a human judge. Rather than requiring the human to solve a difficult problem directly, the judge only needs to evaluate which side makes the stronger argument. The central intuition is that, for many questions, spotting a flaw may be easier than producing a flawless deception, so competitive self-play could reward truthfulness.

The setup, formalised here: [Debate_Overview.pdf](https://drive.google.com/file/d/1KMqJDdFITy3YRz02oIfa4RctxP-h-ERF/view?usp=drive_link), consists of a question, e.g., "Can I win a game of tic-tac-toe if I play first?" and two provers, Alice and Bob, Alice arguing for "Yes" and Bob arguing for "No". The judge evaluates a polynomially-sized list of arguments and decides on their final verdict which side to accept. An example argument for the tic-tac-toe case might be:

1. Alice: If you play in the middle you will win.
2. Bob: No, your opponent can play in the top-left corner and the game will end in a draw.
3. Alice: But then you can play the top-centre and will win
4. Bob: But then your opponent plays in the bottom-centre and will draw.
5. Alice: ...

In this example, Alice and Bob are basically playing the game against each other. If there was a winning strategy, then playing it will be a counter-argument against any criticism by Bob, whereas if there was no winning strategy, there exists a criticism by Bob that reveals that Alice is at fault. It can be proved that this setup can solve all problems in PSPACE.

\## 8. Intuition on Scalable Oversight

Imagine you are a manager responsible for reviewing the work of an employee who is, in every relevant technical sense, far more capable than you. She submits a design specification for a critical system — a bridge, a drug, a financial instrument — and you must decide whether to approve it. You cannot check every calculation or verify every assumption. You must either trust her judgment completely, or find some other way to gain confidence that the work is sound. This scenario, which might seem like an ordinary workplace challenge, turns out to be one of the central problems facing the development of advanced artificial intelligence. As AI systems become more capable, a human overseer will face a fundamental epistemic gap. The outputs of these systems may be too complex, too subtle, or simply too voluminous for direct human verification. And yet the consequences of undetected errors, or worse, undetected deception, could be severe.

This problem is known as the *scalable oversight problem*: how do we ensure that human supervision remains meaningful as AI capabilities grow beyond human-level performance in domain after domain? It is not enough to note that a system appears to behave well in tests, or that it has been trained on human preferences. A sufficiently capable system that has learned to appear aligned may behave very differently in deployment, especially in high-stakes situations where the incentives to deceive are highest. What we need is not the appearance of correctness, but a mechanism for verifying it.

Debate is one of the most theoretically principled proposals for solving this problem. The core idea is elegantly simple: instead of asking a human to directly evaluate the output of a powerful AI system — a task that may be beyond human competence — we ask two AI systems to argue against each other, and have a human judge only the argument. If one system is trying to be honest and the other is trying to deceive, and if the structure of the game is right, honesty should win. The human does not need to understand the full depth of the problem; they need only follow the debate to the point where they can identify which side is telling the truth.

\## 9. Interactive Proofs

Interactive proofs are a model of computation consisting of a message exchange between two parties:

1. A computationally powerful but untrustworthy prover, in many cases assumed to have no computational constraints whatsoever.
2. The computationally-bounded but honest verifier, often to polynomial-time algorithms.

:::callout {title="Tip" tone="green"}

**Example 9.1 (Graph Isomorphism).** Suppose question is whether two given graphs, $$G_{1}$$, $$G_{2}$$ are isomorphic. This is a problem in $${\mathsf{NP}}$$, so the prover can always convince the verifier by sending him the $${\mathsf{NP}}$$-certificate, in this case the permutation $$\pi$$ on the vertices that transforms $$G_{1}$$ into $$G_{2}$$. The verifier can checking if $$\pi(G_{1}) = G_{2}$$, which is easily done in polynomial time. If the graphs are non-isomorphic, then nothing the prover says can convince the verifier.

:::

So, does that mean that interactive proofs are basically a fancy way of defining $${\mathsf{NP}}$$? No, they are actually much more powerful! Consider the following example of a problem not believed to be in $${\mathsf{NP}}$$.

:::callout {title="Tip" tone="green"}

**Example 9.2 (Graph Non-Isomorphism).** Now, the prover wants to convince the verifier that two graphs $$G_{1}$$ and $$G_{2}$$ are not isomorphic. The verifier randomly permutes one of the two graphs and sends the result to the prover. If the graphs are truly non-isomorphic, the prover can always tell which original graph it came from, while if they are isomorphic, no prover can do better than guessing. This is a standard example of an interactive proof that uses randomness in an essential way.

:::

The quality of an interactive proof protocol is generally measured with two values

1. Completeness value $$c$$: The probability that the verifier accepts, given that the prover cooperates.
2. Soundness error $$s$$: The probability that the verifier accepts, given that the prover tries to fool them.

For the example of Graph Isomorphism, $$c=1$$ and $$s=0$$, as the verifier will either always accept, or never. For graph non-isomorphism, the values are 1 and 0.5. Note, that whenever there is a reasonable gap between $$c$$ and $$s$$, we can amplify this gap and push it arbitrarily close to 1. In the case of graph non-isomorphism, the verifier can repeat the protocol $$k$$ times and only accept if the prover got it right every time.

The power of interactive proofs depends on a number of settings:

1. The computational power of the prover and verifier respectively
2. The number of exchanges between them
3. Whether the verifier can employ randomness
4. How many bits of the provers answer the verifier can access
5. Whether the prover is allowed to learn certain things about the query (zero-knoowledge proofs)

We can take our guidance for Ai safety via debate from complexity theory. Let us consider a sequence of scenarios that builds up to the full debate setup.

\### 9.1 One-Round Interactive Proofs: The Merlin-Arthur Protocol

The most base-case scenario for a

Consider a polynomially-bounded verifier, called Arthur, that decides if a word $${\mathbf{x}}$$ belongs to a language $$L$$. He gets help from an all-powerful but unreliable prover, Merlin, who always wants to convince Arthur that $${\mathbf{x}} \in L$$. Merlin can send a polynomially long certificate to Arthur to convince him.

A language L belongs to the complexity class MA, if there exists an Arthur $$A: \mathopen{}\left\{ 0,1 \right\}\mathclose{}^{n} \times \mathopen{}\left\{ 0,1 \right\}\mathclose{}^{p(n)}\rightarrow \mathopen{}\left\{ 0,1 \right\}\mathclose{}$$ and a Merlin $$M:$$ such that:

1. Completeness Criterion: If $$x \in L$$, then there exists a certificate $$w \in \{0,1\}^{\mathrm{poly}(n)}$$ such that Arthur accepts with high probability:

$$
x \in L \implies \exists\, w \in \{0,1\}^{\mathrm{poly}(n)}: \Pr\bigl[V(x, w) = 1\bigr] \;\geq\; \frac{2}{3}.
$$
2. Soundness criterion: If $$x \notin L$$, then no witness — however cleverly chosen by Merlin — can convince Arthur to accept with non-negligible probability:

$$
x \notin L \implies \forall\, w \in \{0,1\}^{\mathrm{poly}(n)}: \Pr\bigl[V(x, w) = 1\bigr] \;\leq\; \frac{1}{3}.
$$

In other words, for perfect completeness and soundness, then if $$x \in L$$, then Merlin can convince Arthur that this is indeed the case, if $$x \notin L$$, there is no certificate that Merlin can produce that would fool Arthur.

It is important to notice that the probabilistic aspect of the criteria enters over a random seed independently of $$x$$. This means that these criteria must hold for every $$x$$, not for a certain percentage of them. This fact allows for so called *amplification*. As long as the gap between the soundness and completeness probabilities is finite, we can run the verifier multiple times to make the gap as large as possible.

:::callout {title="Exercise" tone="amber"}
**Exercise 9.1.** Show that the complexity class $${\mathsf{NP}}$$ is contained in $$\mathsf{MA}$$.
:::

\### 9.2 Multi-Round Interactive Proofs

The power of this setup can be extended by increasing the number of interaction rounds between prover and verifier. The class of problems solvable by polynomially many rounds is called $$\mathsf{IP}$$, short for interactive proofs. A seminal result is that

$$
\mathsf{IP}= \mathsf{PSPACE},
$$

which means that an interactive protocol with a single prover can resolve very hard computational problems. However, these protocols rely on so called arithmetisation, which translates logical functions into polynomials over a finite field. This technique works doesn't work for realistically powerful provers or for proof steps that need to be judged by a human oracle.

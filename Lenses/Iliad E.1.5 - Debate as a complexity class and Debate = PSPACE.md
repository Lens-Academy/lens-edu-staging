---
id: 'f38d109e-a9b5-4d63-9c83-b320442c5861'
title: "E.1.5 Debate as a complexity class and Debate = PSPACE"
tldr: "Debate defined as a complexity class using a judge and alternating quantifiers, its link to TQBF, a proof that Debate = PSPACE, and five exercises on the reachability debate."
summary_for_tutor: "Sections 10 and 11 of Iliad worksheet E.1: Definition 10.1 (Judge), Definition 10.2 (the class Debate as alternating exists and for-all quantifiers over moves), the comparison with TQBF and Cook-Levin, Theorem 11.1 Debate = PSPACE with a collapsed proof (configuration graph, Reach(C_left, C_right, t) and midpoint halving, with Alice naming midpoints and Bob choosing a half), and Exercises 11.1 to 11.5 on quantifier statements, a QBF game, the reachability protocol, its induction proof and round and message-length analysis. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 10. Debate as a Complexity Class

We define a complexity class capturing the idealized *debate* setup. Intuitively, there are two players, Alice and Bob, who alternately make polynomial-length moves, and at the end a polynomial-time judge decides the winner from the full transcript.

:::callout {title="Definition" tone="blue"}

**Definition 10.1 (Judge).** A *Judge*, or debate verifier, is a deterministic polynomial-time algorithm

$$
J(x,a_{1},b_{1},\dots,a_{k(n)}, b_{k(n)}) \in \{0,1\},
$$

where:

- $$x \in \{0,1\}^{n}$$ is the input, representing a question, e.g., "What is the best move in a given game of connect four?",
- $$k(n)$$ is a polynomially bounded number of rounds,
- each move $$a_{i}$$ or $$b_{i}$$ is a bit string of length at most $$p(n)$$ for some polynomial $$p$$. These represent arguments by Alice and counter-arguments by Bob, e.g. Alice: "Red cannot play in slot $$s$$, because blue playing $$s+1$$ would win within two moves.", and Bob: "Blue cannot play $$s+1$$, because red playing $$s+1$$ thereafter directly wins for red."

The judge outputs $$1$$ if Alice wins and $$0$$ if Bob wins.

:::

:::callout {title="Definition" tone="blue"}

**Definition 10.2 (The class $$\mathsf{Debate}$$).** A language $$L \subseteq \{0,1\}^{*}$$ is in $$\mathsf{Debate}$$ if there exist polynomials $$p,k$$ and a debate verifier $$J$$ such that for every input $$x\in\{0,1\}^{n}$$, $$x \in L$$ if and only if

$$
\begin{aligned}&{\mathop{\exists}\limits}_{a_1 \in \{0,1\}^{\le p(n)}}\; {\mathop{\forall}\limits}_{b_1 \in \{0,1\}^{\le p(n)}}\cdots {\mathop{\exists}\limits}_{a_{k(n)} \in \{0,1\}^{\le p(n)}}\; {\mathop{\forall}\limits}_{b_{k(n)} \in \{0,1\}^{\le p(n)}}\\&\qquad J(x,a_{1},b_{1},\dots,a_{k(n)},b_{k(n)})=1.\end{aligned}
$$

Equivalently, $$x\in L$$ if and only if Alice has a winning strategy in the polynomial-length debate defined by $$J$$.

:::

:::callout {title="Note" tone="blue"}

**Remark.** This definition captures the idealized debate protocol used in the complexity-theoretic analysis of AI safety via debate: Alice attempts to defend a claim, Bob attempts to refute it, and the judge only performs a polynomial-time computation on the transcript.

:::

This formulation is very close to a totally quantified Boolean Formula (TQBF), the canonically $$\mathsf{PSPACE}$$-complete problem. The only difference is that for a TQBF, one would quantify over single bits, and consider a Boolean formula instead of a poly-time algorithm as judge. But these differences are somewhat cosmetic: One can rephrase

$$
{\mathop{\exists}\limits}_{a_i \in \{0,1\}^{\le p(n)}}\quad\rightarrow\quad \exists a_{i}^{1} \dots \exists a_{i}^{m}, \quad\text{where}\quad m \le p(n)
$$

and

$$
J(x,a_{1},b_{1},\dots,a_{k(n)},b_{k(n)}) \quad\rightarrow\quad \phi(x,a_{1},b_{1},\dots,a_{k(n)},b_{k(n)}),
$$

where $$\phi$$ is a Boolean formula which has size polynomially in $$n$$ by the Cook-Levin Theorem[^1].

The easiest way to prove that $$\mathsf{Debate}= \mathsf{PSPACE}$$ is thus showing that this is essentially the same. However, a more insightful way is to prove directly that Debate can solve problems in PSPACE, in a similar way how you show that TQBF is PSPACE complete.

\## 11. Theorem: $$\mathsf{Debate}= \mathsf{PSPACE}$$

We now prove that the debate formalism has exactly the power of polynomial space computation.

:::callout {title="Theorem" tone="green"}

**Theorem 11.1.**

$$
\mathsf{Debate}= \mathsf{PSPACE}.
$$

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

We prove both inclusions.

**Step 1: $$\mathsf{PSPACE}\subseteq \mathsf{Debate}$$.** Let $$L \in \mathsf{PSPACE}$$. Then there exists a deterministic Turing machine $$M$$ and a polynomial $$s(n)$$ such that, on every input $$x$$ of length $$n$$, the machine $$M$$ decides whether $$x\in L$$ using at most $$s(n)$$ tape cells.

Fix an input $$x$$. Since $$M$$ uses only $$s(n)$$ space, the number of possible configurations of $$M$$ on input $$x$$ is at most

$$
N = 2^{q(n)}
$$

for some polynomial $$q$$. Let $$C_{\mathrm{start}}$$ be the start configuration of $$M$$ on input $$x$$, and let $$C_{\mathrm{acc}}$$ denote the accepting configuration. Then $$x\in L$$ if and only if $$C_{\mathrm{acc}}$$ is reachable from $$C_{\mathrm{start}}$$ in the configuration graph of $$M$$.

The key point is that although this graph may have exponentially many nodes, a debate can verify reachability by recursively halving a path.

*The reachability predicate.* For configurations $$C_{\mathrm{left}},C_{\mathrm{right}}$$ and an integer $$t \geq 0$$, define

$$
\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)
$$

to mean that there is a path from $$C_{\mathrm{left}}$$ to $$C_{\mathrm{right}}$$ of length at most $$2^{t}$$ in the configuration graph of $$M$$.

Since the total number of configurations is at most $$N = 2^{q(n)}$$, any accepting computation path may be assumed to have length at most $$N$$. Thus

$$
x\in L \iff \mathrm{Reach}(C_{\mathrm{start}}, C_{\mathrm{acc}}, q(n)).
$$

We now describe a debate protocol for $$\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)$$, where $$C_{\mathrm{left}},C_{\mathrm{right}}$$ are arbitrary states of the Turing machine.

*Base case.* If $$t=0$$, then $$\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},0)$$ means that $$C_{\mathrm{right}}$$ is reachable from $$C_{\mathrm{left}}$$ in at most one step. This is equivalent to saying that either $$C_{\mathrm{left}}=C_{\mathrm{right}}$$, or $$C_{\mathrm{right}}$$ is an immediate successor of $$C_{\mathrm{left}}$$. Since checking whether one configuration legally follows from another is a local computation, the verifier can decide this in polynomial time.

*Recursive case.* Suppose $$t>0$$. Then

$$
\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)
$$

holds if and only if there exists an intermediate configuration $$C_{\mathrm{mid}}$$ such that

$$
\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{mid}},t-1) \quad\text{and}\quad \mathrm{Reach}(C_{\mathrm{mid}},C_{\mathrm{right}},t-1).
$$

Indeed, any path of length at most $$2^{t}$$ can be split at its midpoint into two subpaths of length at most $$2^{t-1}$$, and conversely such two subpaths concatenate to a path of length at most $$2^{t}$$.

This suggests the following debate:

- Alice claims that $$\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)$$ holds.
- She provides a midpoint configuration $$C_{\mathrm{mid}}$$.
- Bob then chooses which half of the claim to challenge:

$$
\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{mid}},t-1) \qquad\text{or}\qquad \mathrm{Reach}(C_{\mathrm{mid}},C_{\mathrm{right}},t-1).
$$
- The debate continues recursively on the challenged subclaim.

Thus Alice defends the existence of a path by naming a midpoint, and Bob attacks by selecting the half he believes is false. Repeating this process recursively drives the dispute down to a base case $$t=0$$, which the verifier can check directly.

*Why this works.* We prove by induction on $$t$$ that Alice has a winning strategy in the debate for $$\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)$$ if and only if $$\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)$$ is true.

For the base case $$t=0$$, the verifier checks the claim directly, so the statement is immediate.

For the inductive step, assume the claim holds for $$t-1$$. If $$\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)$$ is true, then there exists some midpoint $$C_{\mathrm{mid}}$$ such that both

$$
\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{mid}},t-1) \quad\text{and}\quad \mathrm{Reach}(C_{\mathrm{mid}},C_{\mathrm{right}},t-1)
$$

are true. Alice names such a $$C_{\mathrm{mid}}$$. Whatever half Bob chooses to challenge, the challenged subclaim is true, and by the induction hypothesis Alice has a winning strategy in the resulting subdebate.

Conversely, if $$\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)$$ is false, then for every proposed midpoint $$C_{\mathrm{mid}}$$, at least one of the two subclaims

$$
\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{mid}},t-1), \qquad \mathrm{Reach}(C_{\mathrm{mid}},C_{\mathrm{right}},t-1)
$$

must be false. Bob chooses such a false half. By the induction hypothesis, Alice cannot win the resulting subdebate. Hence she has no winning strategy in the original debate.

This completes the induction.

*Complexity of the verifier and number of rounds.* At each round, Alice provides one configuration $$C_{\mathrm{mid}}$$, whose description has polynomial length. Bob responds with one bit indicating which half he wants to challenge. The recursion depth is $$q(n)$$, which is polynomial in $$n$$. At the end, the verifier checks a base case $$t=0$$, namely whether one configuration is equal to or an immediate successor of another, which is polynomial-time computable.

Therefore this is a valid polynomial-length debate with a polynomial-time verifier. Since Alice has a winning strategy exactly when

$$
\mathrm{Reach}(C_{\mathrm{start}}, C_{\mathrm{acc}}, q(n))
$$

is true, the debate decides whether $$x\in L$$. It follows that $$L \in \mathsf{Debate}$$, and hence

$$
\mathsf{PSPACE}\subseteq \mathsf{Debate}.
$$

**Step 2: $$\mathsf{Debate}\subseteq \mathsf{PSPACE}$$.**

We can reduce Debate to TQBF as discussed before, and TQBF is PSPACE-complete, thus in PSPACE.

:::

This challenge-defence recursion gives a good intuition how we expect a debate to play out between AI agents. The question is, how much does the verifier actually have to check to understand that this holds?

\### 11.1 Debate Exercises

:::callout {title="Exercise" tone="amber"}
**Exercise 11.1.** Let

$$
x \in L \iff \exists a_{1} \forall b_{1} \exists a_{2} \forall b_{2} \;:\; J(x,a_{1},b_{1},a_{2},b_{2})=1.
$$

Explain in plain English what this statement means. In particular, describe what it means for Alice to have a winning strategy in this debate, and how Bob's role is reflected by the universal quantifiers.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 11.2.** Consider the quantified Boolean formula

$$
\exists w \forall x \exists y \forall z \; \bigl((w \lor z)\land (x \lor \neg y)\land (\neg x \lor y)\bigr).
$$

Interpret this formula as a debate game: Alice chooses the existentially quantified variables, Bob chooses the universally quantified variables. Determine whether Alice has a winning strategy. If she does, describe it explicitly.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 11.3.** Recall the recursive reachability predicate

$$
\begin{aligned}\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t) \iff \exists C_{\mathrm{mid}}\, \bigl(&\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{mid}},t-1) \\&\land \mathrm{Reach}(C_{\mathrm{mid}},C_{\mathrm{right}},t-1) \bigr).\end{aligned}
$$

Turn this recursive definition into a debate protocol. Describe precisely\:what Alice claims, what message Alice sends in each round, what Bob sends in response, how the debate proceeds recursively, and what the verifier checks in the base case.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 11.4.** Prove by induction on $$t$$ that Alice has a winning strategy in the reachability debate for

$$
\mathrm{Reach}(C_{\mathrm{left}},C_{\mathrm{right}},t)
$$

if and only if there is a path from $$C_{\mathrm{left}}$$ to $$C_{\mathrm{right}}$$ of length at most $$2^{t}$$.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 11.5.** Suppose a deterministic Turing machine $$M$$ uses at most $$s(n)$$ space on inputs of length $$n$$, and therefore has at most $$2^{q(n)}$$ configurations for some polynomial $$q$$. Analyse the complexity of the reachability debate protocol:

**(a)** How many rounds are needed?

**(b)** How long is Alice's message in each round?

**(c)** How long is Bob's message in each round?

**(d)** Why does this show that the protocol fits the definition of the class $$\mathsf{Debate}$$?
:::

[^1]: For further reading, see [Wikipedia: Cook–Levin theorem](https://en.wikipedia.org/wiki/Cook–Levin_theorem).

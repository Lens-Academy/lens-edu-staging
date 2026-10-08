---
id: '475be19e-3509-4fae-a510-74cc43dfa378'
title: "E.1.8 Equivalence of cross-examination and exponential precommitment"
tldr: "A formal proof that cross-examination (CX) equals exponential precommitment (EPC) with local oracle access in the deterministic setting."
summary_for_tutor: "Section 14 of Iliad worksheet E.1: Definition 14.1 (exponential precommitment, class EPC, oracle verifier V^A), Theorem 14.2 CX = EPC with a collapsed two-direction proof (Alice's strategy as a lookup table over Q_n, Bob's strategy encoded as a challenge string b), and two remarks on why the equivalence needs deterministic Alice strategies and what it means conceptually."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 14. Equivalence of Cross-Examination and Exponential Precommitment

We now give a clean formal proof that deterministic cross-examination is exactly as powerful as exponential precommitment with local oracle access.

The key idea is simple. In the cross-examination model, Alice is never required to reveal her entire exponentially large object at once. Instead, Bob and the verifier may query fresh copies of Alice at polynomially many local views. Since each such local view has polynomial length, the set of all possible local views has exponential size. Thus a deterministic Alice strategy is exactly the same thing as an exponentially large lookup table giving her answer at every possible local view.

We work in the deterministic setting.

:::callout {title="Definition" tone="blue"}

**Definition 14.1 (Exponential precommitment).** A language $$L \subseteq \{0,1\}^{*}$$ is in $$\mathsf{EPC}$$ if there exist a deterministic polynomial-time oracle verifier $$V$$ and polynomials $$p,q$$ such that for every input $$x \in \{0,1\}^{n}$$,

$$
x \in L \iff \exists A : \{0,1\}^{p(n)}\to \{0,1\}^{q(n)}\;\forall b \in \{0,1\}^{p(n)}\;:\; V^{A}(x,b)=1,
$$

and

$$
x \notin L \iff \forall A : \{0,1\}^{p(n)}\to \{0,1\}^{q(n)}\;\exists b \in \{0,1\}^{p(n)}\;:\; V^{A}(x,b)=0.
$$

Here $$V$$ may make at most $$p(n)$$ adaptive oracle queries to $$A$$, each of length at most $$p(n)$$, and each oracle answer has length at most $$q(n)$$.

:::

:::callout {title="Theorem" tone="green"}

**Theorem 14.2.**

$$
\mathsf{CX}= \mathsf{EPC}.
$$

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

We prove both inclusions.

**Step 1: $$\mathsf{CX}\subseteq \mathsf{EPC}$$.**

Assume $$L \in \mathsf{CX}$$, witnessed by a verifier $$U$$ and polynomial $$r$$.

Fix an input $$x \in \{0,1\}^{n}$$. Let

$$
Q_{n} := \{0,1\}^{\le r(n)}
$$

denote the set of all possible local queries that could ever be sent to Alice. Since each query has length at most $$r(n)$$,

$$
|Q_{n}| \le 2^{r(n)+1},
$$

so $$Q_{n}$$ has exponential size.

Now fix any deterministic Alice strategy $$\mathcal{A}$$. Because $$\mathcal{A}$$ is deterministic, it induces a function

$$
A_{\mathcal{A}}: Q_{n} \to \{0,1\}^{\le r(n)}
$$

defined by

$$
A_{\mathcal{A}}(q) := \text{the reply that }\mathcal{A} \text{ gives on query }q.
$$

Thus $$A_{\mathcal{A}}$$ is an exponentially large lookup table encoding Alice's answer to every possible local query.

We now construct an exponential-precommitment verifier $$V$$ that simulates the cross-examination protocol.

Given input $$x$$, challenge string $$b$$, and oracle access to a table $$A$$, the verifier $$V^{A}(x,b)$$ interprets $$b$$ as a complete description of a Bob strategy $$\mathcal{B}_{b}$$. Since Bob's interaction with the verifier has at most $$r(n)$$ rounds and all messages have length at most $$r(n)$$, the full behavior of Bob can be encoded by a polynomial-length string $$b$$. The verifier $$V$$ then simulates the protocol $$U$$ on input $$x$$, answering every query to Alice by looking up the appropriate value in the oracle table $$A$$, and answering every move of Bob according to the strategy encoded by $$b$$.

Because $$U$$ is polynomial-time and asks only polynomially many queries, this simulation is polynomial-time.

We claim that for every deterministic Alice strategy $$\mathcal{A}$$ and every deterministic Bob strategy $$\mathcal{B}^{\mathcal{A}}$$, if $$A_{\mathcal{A}}$$ is the table induced by $$\mathcal{A}$$ and $$b_{\mathcal{B}}$$ is the encoding of $$\mathcal{B}$$, then

$$
U^{\mathcal{A},\mathcal{B}}(x) = V^{A_{\mathcal{A}}}(x,b_{\mathcal{B}}).
$$

Indeed, both procedures generate exactly the same transcript: whenever the original protocol queries Alice on some local view $$q$$, the simulated verifier looks up exactly the same answer $$A_{\mathcal{A}}(q)$$. Since Bob is also encoded faithfully, every subsequent verifier/Bob/Alice message is identical.

Therefore:

- if $$x \in L$$, then there exists an Alice strategy $$\mathcal{A}$$ such that $$U^{\mathcal{A},\mathcal{B}}(x)=1$$ for every Bob strategy $$\mathcal{B}$$. Hence, for the corresponding table $$A_{\mathcal{A}}$$, we have

$$
V^{A_{\mathcal{A}}}(x,b)=1 \qquad \text{for every challenge string }b,
$$

so $$x \in \mathsf{EPC}$$;
- if $$x \notin L$$, then for every Alice strategy $$\mathcal{A}$$ there exists a Bob strategy $$\mathcal{B}$$ such that $$U^{\mathcal{A},\mathcal{B}}(x)=0$$. Hence for every induced table $$A_{\mathcal{A}}$$, there exists a challenge string $$b_{\mathcal{B}}$$ such that

$$
V^{A_{\mathcal{A}}}(x,b_{\mathcal{B}})=0.
$$

Thus $$L \in \mathsf{EPC}$$, and so

$$
\mathsf{CX}\subseteq \mathsf{EPC}.
$$

**Step 2: $$\mathsf{EPC}\subseteq \mathsf{CX}$$.**

Now assume $$L \in \mathsf{EPC}$$, witnessed by an oracle verifier $$V$$ and polynomials $$p,q$$.

We construct a cross-examination protocol deciding $$L$$.

In the new protocol, Alice's strategy $$\mathcal{A}$$ is simply an oracle implementation of the exponentially large precommitted table $$A$$. Concretely, on any query $$q \in \{0,1\}^{p(n)}$$, Alice replies with

$$
\mathcal{A}(q) := A(q).
$$

Bob's role is to provide the original polynomial-size challenge string $$b$$. Since Bob in the cross-examination model may send polynomial-length messages, he can send $$b$$ directly to the verifier. The verifier $$U$$ then simulates the original precommitment verifier $$V^{A}(x,b)$$ by querying Alice whenever $$V$$ would query the oracle $$A$$.

Because $$V$$ runs in polynomial time and makes only polynomially many oracle queries, the verifier $$U$$ also runs in polynomial time and makes only polynomially many queries to Alice. Bob does not even need to query copies of Alice in this simulation, although the model allows him to.

Again the simulation is exact:

$$
U^{\mathcal{A},\mathcal{B_b}}(x)=V^{A}(x,b),
$$

where $$\mathcal{B}_{b}$$ denotes the Bob strategy that simply supplies the challenge string $$b$$.

Therefore:

- if $$x \in L$$, then there exists a table $$A$$ such that $$V^{A}(x,b)=1$$ for every $$b$$. The corresponding Alice strategy $$\mathcal{A}$$ therefore satisfies

$$
U^{\mathcal{A},\mathcal{B}}(x)=1 \qquad \text{for every Bob strategy }\mathcal{B};
$$
- if $$x \notin L$$, then for every table $$A$$ there exists some challenge $$b$$ such that $$V^{A}(x,b)=0$$. Hence for every corresponding Alice strategy $$\mathcal{A}$$, the Bob strategy $$\mathcal{B}_{b}$$ forces

$$
U^{\mathcal{A},\mathcal{B_b}}(x)=0.
$$

Thus $$L \in \mathsf{CX}$$, and so

$$
\mathsf{EPC}\subseteq \mathsf{CX}.
$$

Combining the two inclusions yields

$$
\mathsf{CX}= \mathsf{EPC}.
$$

:::

:::callout {title="Note" tone="blue"}

**Remark.** The equivalence is exact only because we are working in the deterministic setting. If Alice were allowed fresh randomness on different copies, then a single fixed lookup table would no longer capture her behavior. In that case, the correct analogue of precommitment would be a distribution over exponentially large tables, or equivalently a precommitted random seed.

:::

:::callout {title="Note" tone="blue"}

**Remark.** Conceptually, the theorem says that cross-examination does not give more than exponential precommitment. A deterministic Alice strategy is already just an exponentially large table of answers to every possible local query. Cross-examination merely gives Bob and the verifier adaptive local access to that table.

:::

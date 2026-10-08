---
id: '26626855-96e5-46ee-974d-9fa3528e20cd'
title: "E.1.9 Cross-examination as exponential precommitment"
tldr: "A second formalization of the same idea: local cross-examination protocols and precommitment protocols are equivalent, so cross-examination equals precommitment to an exponential table."
summary_for_tutor: "Section 15 of Iliad worksheet E.1: Definitions 15.1 and 15.2 (local cross-examination and exponential precommitment protocols with Q_n = {0,1}^m(n), Sigma_n, A_x and a committed table w), Definition 15.3 (classes CX_loc and PC_loc), Theorem 15.4 CX_loc = PC_loc with a collapsed proof by matching query-answer histories, and two remarks about random access to a huge implicit table and deterministic strategies."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 15. Cross-examination as exponential precommitment

We now formalize the idea that, in the local-query setting, cross-examination is exactly equivalent to allowing Alice to precommit to an exponentially long table of answers and then letting Bob and the verifier inspect only polynomially many entries.

:::callout {title="Definition" tone="blue"}

**Definition 15.1 (Local cross-examination protocol).** Fix polynomials $$m,\ell,r$$, and for each input length $$n$$ define

$$
Q_{n} := \{0,1\}^{m(n)}\qquad\text{and}\qquad \Sigma_{n} := \{0,1\}^{\ell(n)}.
$$

A *local cross-examination protocol* consists of a deterministic polynomial-time verifier $$V$$ and proceeds as follows on input $$x\in\{0,1\}^{n}$$:

1. Alice's strategy is a deterministic function

$$
A_{x} : Q_{n} \to \Sigma_{n}.
$$

Intuitively, a fresh independent copy of Alice, when asked query $$q\in Q_{n}$$, returns the answer $$A_{x}(q)$$.
2. Bob interacts with the verifier for at most $$r(n)$$ rounds. In round $$i$$, based on $$x$$ and the previous history

$$
h_{i-1}= ((q_{1},\alpha_{1}),\dots,(q_{i-1},\alpha_{i-1})),
$$

Bob chooses a query $$q_{i} \in Q_{n}$$.
3. The verifier sends $$q_{i}$$ to a fresh independent copy of Alice and receives

$$
\alpha_{i} = A_{x}(q_{i})\in\Sigma_{n}.
$$
4. After at most $$r(n)$$ rounds, the verifier outputs

$$
V(x,h_{s})\in\{0,1\},
$$

where $$h_{s}=((q_{1},\alpha_{1}),\dots,(q_{s},\alpha_{s}))$$ is the full query-answer history.

:::

:::callout {title="Definition" tone="blue"}

**Definition 15.2 (Exponential precommitment protocol).** Fix the same parameters $$m,\ell,r$$. A *precommitment protocol* consists of a deterministic polynomial-time verifier $$V$$ and proceeds as follows on input $$x\in\{0,1\}^{n}$$:

1. Alice first outputs a table

$$
w \in \Sigma_{n}^{Q_n}.
$$

Equivalently, $$w$$ is a function

$$
w : Q_{n} \to \Sigma_{n}.
$$
2. Bob interacts with the verifier for at most $$r(n)$$ rounds. In round $$i$$, based on $$x$$ and the previous history

$$
h_{i-1}= ((q_{1},\alpha_{1}),\dots,(q_{i-1},\alpha_{i-1})),
$$

Bob chooses a query $$q_{i}\in Q_{n}$$.
3. Instead of querying a fresh copy of Alice, the verifier simply reads the committed table entry

$$
\alpha_{i} = w(q_{i})\in \Sigma_{n}.
$$
4. After at most $$r(n)$$ rounds, the verifier outputs

$$
V(x,h_{s})\in\{0,1\}.
$$

:::

:::callout {title="Definition" tone="blue"}

**Definition 15.3 (The classes $$\mathsf{CX}_{\mathrm{loc}}$$ and $$\mathsf{PC}_{\mathrm{loc}}$$).** A language $$L\subseteq\{0,1\}^{*}$$ is in $$\mathsf{CX}_{\mathrm{loc}}$$ if there exists a local cross-examination protocol such that:

- if $$x\in L$$, then there exists an Alice strategy $$A_{x}$$ such that for every Bob strategy, the verifier accepts;
- if $$x\notin L$$, then there exists a Bob strategy such that for every Alice strategy $$A_{x}$$, the verifier rejects.

Similarly, $$L\in \mathsf{PC}_{\mathrm{loc}}$$ if the same holds for a precommitment protocol.

:::

:::callout {title="Theorem" tone="green"}

**Theorem 15.4.**

$$
\mathsf{CX}_{\mathrm{loc}}= \mathsf{PC}_{\mathrm{loc}}.
$$

In particular, since $$|Q_{n}| = 2^{m(n)}$$, local cross-examination is exactly as powerful as precommitment to a table of length

$$
2^{m(n)}\cdot \ell(n),
$$

which is exponential whenever $$m(n)$$ is polynomial.

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

We prove both inclusions.

**($$\mathsf{CX}_{\mathrm{loc}}\subseteq \mathsf{PC}_{\mathrm{loc}}$$).** Suppose $$L\in \mathsf{CX}_{\mathrm{loc}}$$, witnessed by some local cross-examination protocol.

Fix an input $$x\in\{0,1\}^{n}$$, and let $$A_{x}:Q_{n}\to\Sigma_{n}$$ be any deterministic Alice strategy in the cross-examination protocol. Define the corresponding committed table $$w_{A_x}\in \Sigma_{n}^{Q_n}$$ by

$$
w_{A_x}(q) := A_{x}(q) \qquad\text{for every }q\in Q_{n}.
$$

We now simulate the cross-examination protocol by a precommitment protocol in which Alice commits to the table $$w_{A_x}$$. Whenever Bob chooses a query $$q_{i}$$, the precommitment verifier reads

$$
w_{A_x}(q_{i})=A_{x}(q_{i}),
$$

which is exactly the answer that a fresh independent copy of Alice would have returned in the original cross-examination protocol.

We claim that, against any Bob strategy, the two protocols generate exactly the same history

$$
h_{s}=((q_{1},\alpha_{1}),\dots,(q_{s},\alpha_{s})).
$$

This follows by induction on the round number $$i$$: if the histories agree up to round $$i-1$$, then Bob chooses the same next query $$q_{i}$$ in both protocols, because Bob's choice depends only on $$x$$ and the previous history. The answer returned is the same, since both protocols return $$A_{x}(q_{i})$$. Hence the histories remain identical.

Therefore the verifier's final output is the same in both protocols on every input, against every Bob strategy. So every winning Alice strategy in the cross-examination protocol yields a winning committed table in the precommitment protocol, and every winning Bob strategy remains winning as well. Thus

$$
\mathsf{CX}_{\mathrm{loc}}\subseteq \mathsf{PC}_{\mathrm{loc}}.
$$

**($$\mathsf{PC}_{\mathrm{loc}}\subseteq \mathsf{CX}_{\mathrm{loc}}$$).** Now suppose $$L\in \mathsf{PC}_{\mathrm{loc}}$$, witnessed by some precommitment protocol.

Fix an input $$x\in\{0,1\}^{n}$$, and let $$w:Q_{n}\to\Sigma_{n}$$ be any committed table. Define the corresponding deterministic Alice strategy in the cross-examination protocol by

$$
A_{x}^{w}(q) := w(q) \qquad\text{for every }q\in Q_{n}.
$$

Whenever Bob chooses a query $$q_{i}$$, a fresh independent copy of Alice answers

$$
A_{x}^{w}(q_{i})=w(q_{i}),
$$

which is exactly the value that the precommitment verifier would have read from the table.

As above, by induction on the round number, the query-answer histories in the two protocols are identical against any Bob strategy. Hence the verifier's output is identical in the precommitment and cross-examination protocols.

Therefore every winning committed table $$w$$ yields a winning Alice strategy $$A_{x}^{w}$$, and every winning Bob strategy remains winning. Thus

$$
\mathsf{PC}_{\mathrm{loc}}\subseteq \mathsf{CX}_{\mathrm{loc}}.
$$

Combining the two inclusions, we conclude that

$$
\mathsf{CX}_{\mathrm{loc}}= \mathsf{PC}_{\mathrm{loc}}.
$$

:::

:::callout {title="Note" tone="blue"}

**Remark.** The theorem shows that the role of cross-examination is to give Bob and the verifier *random access* to a huge implicit object. The object is the answer table

$$
q \mapsto A_{x}(q).
$$

Because the allowed queries $$q$$ have polynomial length, this table has exponential size in general. Thus local cross-examination is exactly equivalent to exponential precommitment plus local spot-checking.

:::

:::callout {title="Note" tone="blue"}

**Remark.** The theorem is stated for deterministic Alice strategies. This is the clean setting for the deterministic debate protocols considered earlier. If one wishes to allow randomized strategies, one needs a slightly richer formulation; the basic idea remains that the precommitment object must encode whatever a fresh copy of Alice would answer on every allowed query.

:::

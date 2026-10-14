---
id: 'b1396d94-bc11-44bb-b78b-080a9fbe3bcc'
title: "E.1.6 Cross-examination raises debate to NEXP"
tldr: "Cross-examination, where a debater can question a fresh copy of the other debater, and a proof that it lifts debate from PSPACE to NEXP using computation tableaux."
summary_for_tutor: "Sections 12 and 13 of Iliad worksheet E.1: the idea of cross-examination (questions to fresh copies of the earlier debater, PSPACE to NEXP), Definition 13.1 (the class CX with deterministic strategies A and B^A and verifier U), Theorem 13.2 NEXP is contained in CX-Debate, and its collapsed proof with a computation tableau, initial, accepting and local transition conditions, Bob's challenge (type, tau, j), completeness, soundness and verifier complexity."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 12. Cross-Examination

The follow-up idea is that ordinary debate may let a dishonest debater get away with arguments that are only locally plausible. Cross-examination tries to fix this by allowing one debater, instead of giving a normal reply, to ask a question about something the other debater said earlier. The key twist is that the answer comes from a fresh copy of the earlier debater, taken from the point when they originally made that claim. This lets the examiner probe whether the opponent's story stays consistent across different branches of the conversation, rather than only along one single path.

The headline complexity result is that, in this idealized setting, cross-examination increases the theoretical power of debate from **PSPACE** to **NEXP**. The [2020 writeup](https://www.alignmentforum.org/posts/Br4xDbYu4Frwrb64a/writeup-progress-on-ai-safety-via-debate-1) states this directly, and later formal work summarizes the same result as a property of the Barnes–Christiano cross-examination extension.

\## 13. Cross-examination raises debate to $$\mathsf{NEXP}$$

We now prove the key lower bound explaining why cross-examination is more powerful than ordinary debate.

:::callout {title="Definition" tone="blue"}

**Definition 13.1 (Cross-examination).** A language $$L \subseteq \{0,1\}^{*}$$ is in $$\mathsf{CX}$$ if there exist a deterministic polynomial-time verifier $$U$$ and a polynomial $$r$$ such that for every input $$x \in \{0,1\}^{n}$$,

$$
x \in L \iff \exists \mathcal{A} \;\forall \mathcal{B}^{\mathcal{A}}\;:\; U^{\mathcal{A},\mathcal{B}}(x)=1,
$$

and

$$
x \notin L \iff \forall \mathcal{A} \;\exists \mathcal{B}^{\mathcal{A}}\;:\; U^{\mathcal{A},\mathcal{B}}(x)=0.
$$

Here:

- $$\mathcal{A}$$ is a deterministic Alice strategy that answers queries of length at most $$r(n)$$ with replies of length at most $$r(n)$$;
- $$\mathcal{B}^{\mathcal{A}}$$ is a deterministic Bob strategy which may make at most $$r(n)$$ adaptive queries of length at most $$r(n)$$ to fresh independent copies of $$\mathcal{A}$$;
- the verifier $$U$$ may also make at most $$r(n)$$ adaptive queries of length at most $$r(n)$$ to $$\mathcal{A}$$ and to $$\mathcal{B}$$;
- the entire interaction has at most $$r(n)$$ rounds and all messages have length at most $$r(n)$$.

Since $$\mathcal{A}$$ is deterministic, all fresh copies of $$\mathcal{A}$$ answer the same query in the same way.

:::

:::callout {title="Theorem" tone="green"}

**Theorem 13.2.**

$$
\mathsf{NEXP}\subseteq \mathsf{CX\text{-}Debate}.
$$

:::

:::callout {title="Proof" tone="neutral" collapse="closed"}

Let $$L\in \mathsf{NEXP}$$. Then there exist a nondeterministic Turing machine $$N$$ and a polynomial $$p$$ such that $$N$$ decides $$L$$ in time

$$
T(n)=2^{p(n)}.
$$

Without loss of generality, assume:

- $$N$$ has a single tape;
- $$N$$ uses at most $$T(n)$$ tape cells on inputs of length $$n$$;
- once $$N$$ enters an accepting or rejecting halting state, it stays there forever and leaves the tape unchanged.

Fix an input $$x\in\{0,1\}^{n}$$, and let $$T=T(|x|)$$.

**Step 1: Encode a computation as a tableau.**  A computation branch of $$N$$ on input $$x$$ can be encoded as a tableau

$$
\mathcal{T}\in \Gamma^{(T+1)\times (T+1)},
$$

where $$\Gamma$$ is a constant-size alphabet encoding, for each tape cell and time step:

- the tape symbol in that cell,
- whether the head is on that cell,
- and, if so, the current state.

Row $$0$$ is the initial configuration on input $$x$$, and row $$T$$ is the final configuration after $$T$$ steps.

We linearize the tableau row-by-row into a string

$$
a \in \Gamma^{(T+1)(T+1)}.
$$

**Step 2: Local consistency conditions.**  The tableau $$\mathcal{T}$$ is an accepting computation of $$N$$ on input $$x$$ iff all of the following hold:

1. **Initial row condition:** row $$0$$ correctly encodes the start configuration of $$N$$ on input $$x$$.
2. **Accepting row condition:** row $$T$$ is in an accepting halting configuration.
3. **Local transition conditions:** for every time $$1\le \tau \le T$$ and every tape position $$1\le j\le T+1$$, the symbol at tableau position $$(\tau,j)$$ is consistent with the machine transition rule applied to a constant-size neighborhood in the previous row, namely

$$
(\tau-1,j-1),\ (\tau-1,j),\ (\tau-1,j+1).
$$

These are exactly the usual local constraints from the Cook–Levin tableau construction: whether one cell in row $$\tau$$ is correct depends only on a constant-size window in row $$\tau-1$$.

**Step 3: The cross-examination protocol.**  We define the following protocol.

1. Alice outputs a string $$a$$, intended to be the linearized tableau of an accepting computation branch of $$N$$ on input $$x$$.
2. Bob outputs a challenge

$$
t=(\mathrm{type},\tau,j),
$$

where $$\mathrm{type}$$ specifies which constraint is being challenged:

- $$\mathrm{type}=\mathrm{init}$$: challenge the initial-row condition at cell $$j$$;
- $$\mathrm{type}=\mathrm{acc}$$: challenge the accepting-row condition at cell $$j$$;
- $$\mathrm{type}=\mathrm{step}$$: challenge the local transition condition at spacetime location $$(\tau,j)$$.
3. The verifier computes the queried coordinates $$I(x,t)$$ as follows:
   - for $$\mathrm{init}$$, query only the $$j$$-th cell of row $$0$$;
   - for $$\mathrm{acc}$$, query only the $$j$$-th cell of row $$T$$;
   - for $$\mathrm{step}$$, query the constant-size neighborhood

   $$
   (\tau-1,j-1),\ (\tau-1,j),\ (\tau-1,j+1),\ (\tau,j).
   $$

   The verifier accepts iff the queried cells satisfy the corresponding local constraint.

**Step 4: Completeness.**  Assume $$x\in L$$. Then $$N$$ has some accepting computation branch on input $$x$$ of length at most $$T$$. Let $$\mathcal{T}$$ be the tableau of that accepting branch, padded after halting so that it has exactly $$T+1$$ rows, and let $$a$$ be its linearization.

If Alice outputs this $$a$$, then:

- the initial row is correct,
- the final row is accepting,
- every local transition constraint is satisfied.

Hence every challenge Bob can issue is answered correctly by the queried cells, and the verifier always accepts.

**Step 5: Soundness.**  Assume $$x\notin L$$. Then $$N$$ has no accepting computation branch on input $$x$$ of length at most $$T$$.

Take any string $$a$$ output by Alice, and interpret it as a tableau $$\mathcal{T}$$. Since there is no accepting computation tableau for $$x$$, $$\mathcal{T}$$ must violate at least one of the conditions above:

- either row $$0$$ is not the correct initial configuration,
- or row $$T$$ is not accepting,
- or some local transition condition fails at some $$(\tau,j)$$.

Bob outputs a challenge $$t$$ pointing to such a violated condition. By construction, the verifier queries exactly the cells needed to check that local condition, detects the violation, and rejects.

Therefore Bob has a winning strategy whenever $$x\notin L$$.

**Step 6: Verifier complexity.**  Each challenge $$t=(\mathrm{type},\tau,j)$$ uses only

$$
O(\log T)=O(p(n))=\mathrm{poly}(n)
$$

bits, since $$\tau,j\in [T+1]$$. The verifier reads only $$O(1)$$ tableau entries, and checking the corresponding local constraint is a polynomial-time computation in $$|x|$$. Hence the verifier runs in polynomial time.

Therefore the above is a valid cross-examination debate protocol for $$L$$, and so

$$
L\in \mathsf{CX\text{-}Debate}.
$$

Since $$L\in\mathsf{NEXP}$$ was arbitrary, we conclude that

$$
\mathsf{NEXP}\subseteq \mathsf{CX\text{-}Debate}.
$$

:::

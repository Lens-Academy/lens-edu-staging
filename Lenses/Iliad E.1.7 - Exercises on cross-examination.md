---
id: 'df6d1fdb-2253-4cc1-b254-07c785830079'
title: "E.1.7 Exercises on cross-examination"
tldr: "Ten exercises on cross-examination: why copies matter, reading a toy tableau, local checks, designing Bob's challenges, and cross-examination as a precommitment table."
summary_for_tutor: "Subsection 13.1 of Iliad worksheet E.1: Exercises 13.1 to 13.10 on cross-examination: ordinary debate versus cross-examination, why independent copies enforce consistency, a toy tableau with states q_0 and q_acc (13.3 and 13.4), the three Bob challenge types, why NEXP is reached, the precommitment table A_x: Q to Sigma, comparison of the PSPACE and NEXP pictures, a flawed student claim, and a fill-in proof step. Let the student attempt each exercise before revealing or paraphrasing a solution."
authors:
  - Stephan Wäldchen (Iliad)
source_url: https://iliad-intensive.org/safety/debate/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### 13.1 Exercises on Cross-Examination

:::callout {title="Exercise" tone="amber"}
**Exercise 13.1 (From ordinary debate to cross-examination).** Explain in your own words why the following ordinary debate protocol does *not* suffice to verify an exponentially long computation:

> Alice claims that an exponential-time machine $$M$$ accepts $$x$$. Bob points to a suspicious time step $$t$$. Alice explains what happens at time $$t$$. The verifier checks the explanation.

What goes wrong if Alice is allowed to answer each question separately without being forced to remain globally consistent?
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.2 (Why copies matter).** Suppose Alice is asked two separate questions about a claimed computation tableau:

- What symbol appears in row $$17$$, column $$5$$?
- What are the symbols in the local neighborhood around row $$17$$, column $$5$$?

Give an example of how Alice could answer these two questions inconsistently if she is not forced to commit to a single global tableau in advance.

Then explain how querying independent copies of Alice can be viewed as enforcing consistency with one fixed underlying object.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.3 (Reading a tableau).** Consider the following toy computation tableau:

$$
\begin{array}{c|ccccc}\tau \backslash j & 1 & 2 & 3 & 4 & 5 \\ \hline 0 & [q_0,1] & 0 & 1 & \sqcup & \sqcup \\ 1 & 1 & [q_0,0] & 1 & \sqcup & \sqcup \\ 2 & 1 & 1 & [q_0,1] & \sqcup & \sqcup \\ 3 & 1 & 1 & 1 & [q_0,\sqcup] & \sqcup \\ 4 & 1 & 0 & 1 & [q_{\mathrm{acc}},\sqcup] & \sqcup\end{array}
$$

Answer the following:

**(a)** What is the start configuration?

**(b)** At which time step does the head first move onto the blank symbol?

**(c)** Why is the final row accepting?
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.4 (Local checks).** In the tableau above, Bob challenges the transition from row $$2$$ to row $$3$$ at column $$4$$.

**(a)** Which entries of the tableau should the verifier inspect in order to perform a local check?

**(b)** Why is it enough to inspect only a constant-size neighborhood rather than the whole tableau?

**(c)** Did Alice smuggle in a mistake into the table?
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.5 (Designing a Bob challenge).** Suppose Alice presents a tableau $$\mathcal{T}$$ for an accepting computation. List the three main types of challenge Bob can make:

**(a)** an initial-row challenge,

**(b)** an accepting-row challenge,

**(c)** a transition challenge.

For each type, explain exactly what Bob must specify, and exactly what the verifier checks.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.6 (Why this reaches $$\mathsf{NEXP}$$).** Suppose a nondeterministic Turing machine $$N$$ runs in time $$T(n)=2^{p(n)}$$.

**(a)** How large is a full accepting computation tableau for $$N$$?

**(b)** Why can Alice not simply write the entire tableau down in an ordinary polynomial-length debate?

**(c)** Why can Bob nevertheless challenge one local location of the tableau using only polynomially many bits?

**(d)** Why can the verifier check that challenge in polynomial time?

Use your answers to explain why cross-examination can verify an exponentially long computation even though the verifier never reads the whole computation.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.7 (Cross-examination as precommitment).** Let $$Q$$ be the set of all possible local queries Bob might ask about a tableau, for example:

$$
Q = \{(\tau,j,\mathrm{type})\}.
$$

Explain why Alice's behavior under cross-examination can be modeled as a function

$$
A_{x} : Q \to \Sigma,
$$

where $$\Sigma$$ is the set of possible local answers.

Why does this function behave like an exponentially large precommitment table?
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.8 (Compare PSPACE and NEXP intuitions).** Write a short paragraph comparing the following two pictures:

- In the $$\mathsf{PSPACE}$$ reachability proof, Alice repeatedly gives a midpoint configuration and Bob chooses which half to challenge.
- In the $$\mathsf{NEXP}$$ cross-examination proof, Alice implicitly commits to a full exponentially large tableau and Bob challenges one local location.

What is the key conceptual difference between these two protocols?
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.9 (Find the flaw).** A student says:

> "Cross-examination is unnecessary. Bob can just ask Alice for the value at position $$(\tau,j)$$, then ask her for the value at position $$(\tau,j+1)$$, and then reconstruct the whole tableau bit by bit."

Explain why this does not work in a polynomial-length protocol. Your answer should mention both:

- the size of the tableau,
- and the reason local consistency is more useful than full reconstruction.
:::

:::callout {title="Exercise" tone="amber"}
**Exercise 13.10 (Mini-proof exercise).** Fill in the missing argument:

> If $$x\notin L(N)$$, then no accepting tableau exists. Therefore any tableau Alice implicitly commits to must violate at least one local condition. Hence $$\underline{\hspace{4cm}}$$.

State precisely what Bob does and why the verifier rejects.
:::

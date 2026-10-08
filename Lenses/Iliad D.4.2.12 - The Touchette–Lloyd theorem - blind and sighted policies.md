---
id: '6f8cdcf1-700a-49c6-9e3b-fcc8a2f5b4c9'
title: "D.4.2.12 The Touchette–Lloyd theorem: blind and sighted policies"
tldr: "Appendix B, first half: environments, actions and policies, blind versus sighted policies, and the 5-bit guessing game played blind and sighted."
summary_for_tutor: "Appendix B (B.1-B.5) of Iliad worksheet D.4.2. The motivating question (bits of optimization imply bits of modeling), the setup with X, A, Y, policy P(A | X) and dynamics P(Y | X, A), Definition B.1 (blind policy: I(X;A) = 0; sighted: I(X;A) > 0), the blind baseline, and the guessing game with 5-bit strings (H(Y) about 4.94 bits blind; table of ΔH by number of observed bits). Footnote 3 on the source theorem is included. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## B. The informational cost of steering: the Touchette–Lloyd theorem

\### B.1 From optimization to modeling: the motivating question

Having established in Section 5 that an agent can steer a subsystem by expending mutual information it already shares with that subsystem (the Type-3 channel), we now quantify this channel precisely, asking how much entropy reduction each bit of mutual information actually purchases. The answer establishes a rigorous connection between optimization and *modeling*.

One of the recurring aspirations of agent foundations is the identification of *selection theorems*: results establishing that any system selected to perform sufficiently well at some task must, as a matter of mathematical necessity, contain certain agent-like structures, such as a world model, a goal representation, or a planning process. The *agent structure problem* poses this question in the converse direction to the usual one: rather than asking whether agents bring about outcomes, it asks whether a system observed to reliably bring about a particular outcome must necessarily be modeling its environment. Wentworth formulated a sharp quantitative version of this question: how many bits of optimization can one bit of observation purchase?

A theorem of Touchette and Lloyd, originally published in the control theory literature and brought to the attention of the agent foundations community by Harwood and Altair, constitutes one of the few existing results that directly addresses this problem.[^3] Informally, the theorem states that *the entropy reduction a policy achieves, beyond what the environment's dynamics would accomplish on their own, is bounded by the mutual information between the policy's action and the environment's state*, so that every bit of optimization beyond the blind baseline requires a corresponding bit of modeling of the environment's state. This appendix develops the exact statement systematically, accompanied by fully worked examples.

\### B.2 The formal setup: environments, actions, and policies

The model comprises a single time step of an environment subject to external influence, involving three random variables:

- $$X$$, the *initial state* of the environment;
- $$A$$, the *action* taken (by an agent, a controller, or a machine; the formalism is indifferent to the nature of the actor);
- $$Y$$, the *final state* of the environment.

Two conditional distributions specify the situation completely. The *policy* $$P(A \mid X)$$ describes how the action is chosen as a function of the environment's initial state, and the *dynamics* $$P(Y \mid X, A)$$ describe how the final state is produced from the initial state together with the action. The dynamics are held fixed, representing the physics of the environment; the policy is the object of study. As is conventional, $$X$$ and $$Y$$ range over the same set of environment states, and the dynamics may be deterministic (all transition probabilities $$0$$ or $$1$$) or noisy.

Following Section 3.3, we score a policy by the entropy reduction it achieves:

$$
\Delta H \;:=\; H(X) - H(Y),
$$

the number of bits by which the final state is more predictable than the initial state. This measures optimization precisely in the manner prescribed by Section 3, namely by the extent to which the process funnels a broad distribution into a narrow one. (As noted in Remark 3.1, entropy reduction constitutes the physics-facing half of expected utility maximization, the other half being the specification of which narrow region the agent prefers.)

\### B.3 Blind and sighted policies

:::callout {title="Definition" tone="blue"}

**Definition B.1 (Blind and Sighted Policies).** A policy is *blind* if the action is statistically independent of the initial state, that is, if $$P(A \mid X) = P(A)$$, or equivalently $$I(X; A) = 0$$. A policy is *sighted* if $$I(X; A) > 0$$.

:::

Blind policies include every deterministic rule of the form "always take action $$a_{1}$$", and also every randomized rule whose randomness is independent of the environment, such as "flip a private coin; on heads take action $$a_{1}$$, on tails take action $$a_{2}$$". What blindness excludes is precisely any flow of information from the environment's state into the choice of action. Sightedness is a matter of degree, and the degree is measured by $$I(X;A)$$: a policy that conditions on one observed bit of the state has $$I(X;A) \le 1$$, while a policy that observes everything can have $$I(X;A)$$ as large as $$H(X)$$. The entire repertoire of transformations available in the coin world (Appendix A) consisted of blind policies: the "no-peeking" rule was exactly the requirement $$I(X;A) = 0$$, with the "action" being the choice of transformation.

One might naively conjecture that any entropy reduction whatsoever requires sight, but this conjecture is false, and understanding why it fails sharpens the eventual theorem. The dynamics alone can reduce entropy: a contracting dynamics (one that funnels many initial states toward the same point on its own, as a ball settles to the bottom of a valley against friction) funnels states regardless of the action taken, and the coin engine of Appendix A.5 reduced the entropy of designated coins while remaining completely blind. The correct question is therefore not whether a policy reduces entropy, but whether it reduces entropy *beyond what blindness allows*. Accordingly, we define the *blind baseline*

$$
\Delta H^{\max}_{\text{blind}}\;:=\; \max_{P(X) \in \mathcal{X},\; P(A) \in \mathcal{A}}\Delta H,
$$

the largest entropy reduction achievable by *any* blind policy from *any* initial distribution, where $$\mathcal{X}$$ is the set of all distributions over initial states and $$\mathcal{A}$$ is the set of all action distributions independent of $$X$$. This baseline is a property of the dynamics alone, capturing everything the environment can be induced to do "on its own".

\### B.4 A worked example: the guessing game under blind play

The following game, drawn from Harwood and Altair's exposition, renders every quantity in the theorem concrete and computable.

A computer secretly selects a 5-bit binary string $$X$$ uniformly at random, so that $$H(X) = 5$$ bits. The player then submits a 5-bit string $$A$$. The computer feeds both strings into the fixed, publicly known function

$$
f(x, a) \;=\; \begin{cases}\texttt{00000}&\text{if }a = x\\&\quad \text{(the submitted string matches the secret string)},\\[2pt] x&\text{otherwise},\end{cases}
$$

and outputs $$Y = f(X, A)$$. The player's objective is to render the output distribution as predictable as possible, that is, to minimize $$H(Y)$$.

We first consider blind play, in which the string must be chosen with no knowledge of $$X$$, and ask how much entropy reduction can be achieved. Consider the submission of a fixed string $$a$$. If the player chooses $$a = \texttt{00000}$$, then a match produces the output $$\texttt{00000}$$ while a failure to match reproduces $$X$$, which (conditional on not matching) is uniform over the $$31$$ strings other than $$\texttt{00000}$$; a short calculation shows that the output is then exactly uniform over all 32 strings, so that $$H(Y) = 5$$ bits and no reduction whatsoever is achieved. The choice $$a = \texttt{00000}$$ is therefore the unique submission that yields no entropy reduction, and we exclude it from consideration in what follows.

Suppose instead that the player submits any other fixed string, say $$a = \texttt{11111}$$. Two initial states lead to the output $$\texttt{00000}$$: the state $$X = \texttt{11111}$$ (a match, upon which the function outputs zeros) and the state $$X = \texttt{00000}$$ (no match, upon which the function reproduces it). The output $$\texttt{11111}$$ itself never occurs (if $$X = \texttt{11111}$$ the player has matched it, producing zeros; otherwise the output is $$X \ne \texttt{11111}$$). Every other string $$y$$ occurs exactly when $$X = y$$. The output distribution is therefore

$$
\begin{gathered}P(Y = \texttt{00000}) = \tfrac{2}{32}= \tfrac{1}{16}, \qquad P(Y = \texttt{11111}) = 0,\\ P(Y = y) = \tfrac{1}{32}\;\text{ for the other 30 strings},\end{gathered}
$$

with entropy

$$
H(Y) \;=\; \tfrac{1}{16}\log 16 \;+\; 30 \cdot \tfrac{1}{32}\log 32 \;=\; 0.25 + 4.6875 \;\approx\; 4.94 \text{ bits}.
$$

This represents a modest but genuine improvement over 5 bits: two initial states have been funneled onto a single output, rendering the output distribution slightly non-uniform and therefore slightly more predictable. By symmetry, every fixed non-zero string performs identically, randomization among them yields no further improvement, and one can verify that this strategy is optimal among blind policies; for this game and this initial distribution, the blind optimum is $$\Delta H \approx 0.06$$ bits. (If the initial distribution over strings were non-uniform, the optimal blind strategy would be to submit the most probable string other than `00000`; the theorem's baseline $$\Delta H^{\max}_{\text{blind}}$$ takes the maximum over initial distributions as well.)

\### B.5 The guessing game under sighted play

We now suppose that, before choosing the submitted string, the player is shown the first $$k$$ bits of the computer's secret string. A natural strategy is to submit the string consisting of the $$k$$ observed bits followed by all $$\texttt{1}$$s (the continuation is largely immaterial, provided the player avoids completing the all-zeros string). Observing $$k$$ bits multiplies the probability of an exact match by $$2^{k}$$, from $$\frac{1}{32}$$ to $$\frac{1}{2^{5-k}}$$, and each match funnels probability onto the single output $$\texttt{00000}$$. Computing $$H(Y)$$ for each $$k$$ exactly as above produces the following table.

| bits of $$X$$ observed | 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- |
| $$H(Y)$$ in bits | 4.94 | 4.85 | 4.63 | 4.11 | 2.83 | 0 |
| $$\Delta H$$ in bits | 0.06 | 0.15 | 0.37 | 0.89 | 2.17 | 5 |

With all five bits observed, the player matches the secret string on every round, the output is deterministically $$\texttt{00000}$$, and the maximum conceivable reduction $$\Delta H = H(X) = 5$$ bits is achieved. Each additional bit of observation purchases additional steering power, with the marginal returns increasing in this particular game as more of the state becomes known, demonstrating that information about the environment converts into optimization of the environment.

[^3]: The result appears as Theorem 10 of H. Touchette and S. Lloyd, *Information-theoretic approach to the study of control systems*, Physica A 331\:140–172 (2004); it is also described in their 2000 paper *Information-theoretic limits of control*, and an earlier, more physics-flavored proof appears in Lloyd's 1989 work on the use of mutual information to decrease entropy, in the context of Maxwell's demon. Related results connecting regulation to modeling include the good regulator theorem of Conant and Ashby and the internal model principle of control theory, but these concern conditions for *optimal* regulation, whereas the Touchette–Lloyd theorem is an inequality constraining *all* policies, optimal or not, which is precisely the property that qualifies it as a genuine selection theorem.

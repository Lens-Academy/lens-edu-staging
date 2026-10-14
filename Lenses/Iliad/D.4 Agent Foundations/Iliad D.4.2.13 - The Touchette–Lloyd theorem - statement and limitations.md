---
id: 'f775722f-c980-4806-9aa5-5f013bedfe5d'
title: "D.4.2.13 The Touchette–Lloyd theorem: statement and limitations"
tldr: "Appendix B, second half: mutual information as a measure of sightedness, the statement of the Touchette-Lloyd theorem, and its limitations."
summary_for_tutor: "Appendix B (B.6-B.8) of Iliad worksheet D.4.2. Mutual information as sightedness, Theorem B.2 (Touchette-Lloyd): the entropy reduction of any policy is at most the blind baseline plus I(X;A), read contrapositively as a selection-theorem-style result; limitations (information can be useless or squandered, as with the negated-guess policy); Example B.3 (noise-canceling headphones); and a remark linking back to the coin engine of Appendix A. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\### B.6 Mutual information as a measure of sightedness

To state the theorem, we must quantify the degree to which a policy is sighted, and the appropriate quantity is precisely the mutual information of Definition 2.6. In the strategy above with $$k = 2$$, the action is determined by the two observed bits (the player always submits the two observed bits followed by $$\texttt{111}$$). Consider an observer who knows this strategy and observes only the *action*, say $$A = \texttt{10111}$$. The observer can immediately infer that the secret string begins with $$\texttt{10}$$: the action reveals the observed bits. Before seeing the action, the observer's uncertainty about $$X$$ was $$H(X) = 5$$ bits; after seeing it, $$H(X \mid A) = 3$$ bits; hence $$I(X; A) = H(X) - H(X \mid A) = 2$$ bits, exactly the number of bits the policy "knows". Mutual information thus formalizes the intuitive notion of how many bits of the environment's state are reflected in the agent's behavior, and it does so without any reference to the agent's internals: it is a property of the joint statistics of state and action, estimable in principle by observing the system over many rounds of play.

\### B.7 Statement of the theorem

:::callout {title="Theorem" tone="green"}

**Theorem B.2 (Touchette–Lloyd).** Fix any dynamics $$P(Y \mid X, A)$$. Then for every initial distribution $$P(X)$$ and every policy $$P(A \mid X)$$,

$$
\Delta H \;\le\; \Delta H^{\max}_{\mathrm{blind}}\;+\; I(X; A).
$$

:::

In words, the entropy reduction achieved by an arbitrary policy decomposes into at most two budgets: everything the dynamics could have been steered to accomplish by a blind controller, plus one bit for every bit of mutual information between the action and the environment's initial state. The theorem holds with no assumptions about the policy's internal structure, no optimality requirements, and no restriction on the dynamics. In particular, *it makes no reversibility assumption*: it is a purely information-theoretic (data-processing) inequality, valid for arbitrary dynamics, reversible or not. Far from standing in tension with the remainder of the development, this is consistent with it: the second law of Section 4.4 required reversibility (in the form of double stochasticity) to forbid *global* entropy reduction, whereas the Touchette–Lloyd theorem requires no such assumption to bound the entropy reduction of a steered subsystem *beyond the blind baseline*. The two results constrain different quantities, and both hold simultaneously.

The contrapositive direction endows the theorem with its selection-theorem character. Suppose we observe a system achieving an entropy reduction $$\Delta H$$ strictly exceeding the blind baseline of its environment's dynamics. We may then *deduce*, without any inspection of the system's internals, that the system's actions carry at least $$\Delta H - \Delta H^{\max}_{\text{blind}}$$ bits of mutual information with the environment's state. Mutual information with the environment is plausibly a necessary (though certainly not sufficient) ingredient of anything deserving the name *world model*; the theorem thus constitutes a first rigorous step along the path from observed optimization to internal modeling, which is the path toward understanding when optimization implies agent-like structure. In the vocabulary of the guessing game, any player who achieves an output entropy below 4.94 bits must have observed some portion of the secret string, with the margin of improvement providing a lower bound on the number of bits observed.

\### B.8 Limitations of the theorem

The inequality provides an upper bound on what information makes possible—not a guarantee that information will be exploited effectively—and this gap manifests in both directions.

First, mutual information may simply fail to confer any advantage. If the dynamics ignore the action entirely ($$Y$$ depends only on $$X$$), then every policy, however well informed, performs exactly as a blind one does: the channel from action to environment has zero capacity, rendering knowledge without influence entirely inert.

Second, mutual information can be actively squandered. In the guessing game, consider the policy that observes the secret string completely and submits its bitwise negation (if the computer selects $$\texttt{01100}$$, the player submits $$\texttt{10011}$$). This policy attains the maximal $$I(X;A) = 5$$ bits of mutual information with the environment, and yet it *never* matches the secret string, so the output is always $$Y = X$$, uniformly distributed: $$\Delta H = 0$$, strictly worse than the optimal blind policy. This demonstrates that possession of maximal mutual information with the environment is entirely compatible with arbitrarily poor steering performance, confirming that modeling constitutes a necessary rather than a sufficient condition for optimization.

The theorem should consequently be read as a conservation-style constraint in the same family as the second law: it specifies what cannot happen (substantial optimization without modeling), never what must happen (modeling producing optimization). The analogy is exact in spirit, and Section 7 converts it into a literal theorem of thermodynamics, in which the role of $$I(X;A)$$ is played by the mutual information between a measurement record and the measured system.

:::callout {title="Tip" tone="green"}

**Example B.3 (Noise-Canceling Headphones).** An everyday system exhibits the complete structure of the theorem. Let $$X$$ be the ambient sound arriving at a listener's ears, let $$Y$$ be the sound the listener actually hears, and consider two technologies. Foam earplugs attenuate sound by passive damping. They are entirely blind ($$I(X;A) = 0$$; the plug's "action" is identical whatever the sound), and yet they achieve a substantial entropy reduction: they exploit fixed statistical structure of the environment (sound is vibration, and foam damps vibration), constituting exactly a blind policy operating within the $$\Delta H^{\max}_{\text{blind}}$$ budget, in the same manner as the coin engine operating on the known bias difference. Active noise-canceling headphones operate in a categorically different manner: they *listen* to the incoming sound and emit its inverted waveform. The emitted signal carries high mutual information with the ambient sound, and the entropy reduction correspondingly exceeds anything passive damping can achieve; the headphones can even steer selectively, canceling the drone of an engine while transmitting a human voice. Finally, playing music through the headphones constitutes an entropy-*increasing* action, demonstrating that agents are under no obligation to minimize entropy; the theorem merely prices the steering they elect to perform.

:::

:::callout {title="Note" tone="blue"}

**Remark (The Coin Engine, Revisited).** The generalized heat engine of Appendix A and the Touchette–Lloyd theorem constitute two halves of a single picture. The engine demonstrates what blind policies can extract: everything within the $$\Delta H^{\max}_{\text{blind}}$$ budget, which is funded by statistical disequilibrium known in advance (the temperature difference between the pools). The theorem prices what blindness cannot reach: every further bit of entropy reduction costs a bit of mutual information acquired through observation. This provides the quantitative form of the Type-3 channel of Section 5: $$I(X;A)$$ is precisely the correlation an agent expends when it steers, and Section 7.4 demonstrates, with the accounting balancing exactly, what acquiring this correlation costs in turn.

:::

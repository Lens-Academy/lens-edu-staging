---
id: 'e35e2e9b-1bcf-4791-b821-cf9abdd43d4a'
title: "D.4.2.5 Three types of optimization under information conservation"
tldr: "The three ways an embedded agent can reduce a subsystem's entropy: waste heat, absorption into memory through measurement, and spending existing mutual information."
summary_for_tutor: "Section 5 (5.1-5.5) of Iliad worksheet D.4.2. The bookkeeping problem (agent A, subsystem S, environment E), then Type 1 (entropy exported as waste heat), Type 2 (entropy absorbed into memory by measurement, with Maxwell's demon), Type 3 (spending pre-existing mutual information I(S;A) with no entropy increase), Example 5.1 (controlled-NOT), and a reinterpretation of the demon as copy then control. No numbered exercises."
authors:
  - Daniel C
  - Satya Benson (Williams College)
source_url: https://iliad-intensive.org/agency/optimization-thermodynamics/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 5. Three types of optimization under information conservation

\### 5.1 The bookkeeping problem

Equipped with the second law and the reversibility of the underlying dynamics, we now undertake the global accounting that governs optimization by an embedded agent. We decompose the universe into three parts: the agent $$A$$, the subsystem $$S$$ that the agent seeks to optimize, and the remainder of the environment $$E$$. Optimization of $$S$$ consists in reducing $$H(S)$$, funneling the subsystem from a large set of possible configurations toward a narrow target set. The second law (Theorem 4.1, applied to the isolated whole) establishes that the joint entropy of $$(A, S, E)$$ cannot decrease, and the reversibility underlying it demands that information about the initial condition of $$S$$ cannot simply vanish. This raises the central "bookkeeping" question: through which channels can an agent reduce $$H(S)$$ while the global accounting remains consistent? The analysis of Daniel C and Ebtekar identifies exactly three such channels, and the classification is exhaustive: entropy removed from $$S$$ must be transferred into $$E$$, absorbed into $$A$$, or paid for in advance through pre-existing correlation. We develop each of the three channels in turn, culminating in a reinterpretation of Maxwell's demon in terms of this classification.

\### 5.2 Type 1: transfer of entropy into the environment as waste heat

The first channel is the most familiar of the three: the agent arranges an interaction between $$S$$ and $$E$$ under which $$H(S)$$ decreases while $$H(E)$$ increases by at least the same amount, thereby transferring the subsystem's entropy into the environment. A refrigerator narrows the distribution over the thermal state of its interior while heating the kitchen behind it; a house-building team imposes order on lumber and nails while dissipating heat, exhaust, and scattered debris into the surroundings. In the coin world of Appendix A, this channel is realized by a conditional-swap circuit that moves uncertainty from the designated coins into other coins. The signature of Type 1 is that the environment absorbs the entropy, the agent functioning merely as an intermediary that arranges the transfer and whose own state need not change appreciably in the process.

\### 5.3 Type 2: absorption of entropy into the agent's memory through measurement

The second channel is subtler: the agent reduces $$H(S)$$ by *measuring* $$S$$ and storing the outcomes, so that the entropy of the subsystem is transferred into the agent's own memory. This mechanism constitutes the operating principle of one of the most celebrated thought experiments in thermodynamics, which we now examine in detail.

**Maxwell's Demon.**  A room full of gas is divided in two by a partition, and the partition contains a small door that can be opened and closed at will. A minute intelligence (the "demon") observes the molecules: whenever a molecule approaches the door from the left, the demon opens it, and whenever one approaches from the right, the demon closes it. The gas thereby accumulates, molecule by molecule, on the right side of the room. The entropy of the gas has evidently decreased (we are far less uncertain about the locations of the molecules than before), yet no work appears to have been performed and no heat has been discharged anywhere, presenting an apparent violation of the second law.

The second law has not been violated; rather, the reversibility argument of Section 4.1 identifies exactly where the missing entropy resides. Consider the end of the process and select any particle that now occupies the right side. Two distinct histories are consistent with its presence there: either the particle began on the right and remained, or it began on the left and was admitted by the demon. These two histories produce *identical* final gas configurations, so the gas alone cannot distinguish between them. The microscopic dynamics of the total system are reversible, however, and reversibility demands that the past be reconstructible from the present. The only way the total system can remain reversible is if some other component differs between the two histories, and that component is the demon's memory: the record of its observations and door operations. For every bit of entropy the demon removes from the gas, at least one bit of entropy accumulates in the demon's memory. The reduction in the entropy of the gas is thus fully compensated by the growth of entropy in the demon's records, ensuring that no global decrease occurs. (We revisit this argument with full rigor, for individual states rather than ensembles, in Section 7.4.)

The signature of Type 2 is that the agent absorbs the entropy: measurement transfers uncertainty from the world into the measurer. The demon's memory is finite, however, so this channel is exhaustible: once the memory fills, the demon must either halt or clear it, and clearing it ultimately exports the stored entropy to the environment as Type-1 waste after all (the exact bookkeeping is provided in Section 7.4). Type 2 therefore functions as a finite buffer rather than as a sink of unbounded capacity, deferring the environmental cost rather than eliminating it.

\### 5.4 Type 3: expenditure of pre-existing mutual information

The first two channels balance the accounts by increasing entropy elsewhere, whether in $$E$$ or in $$A$$. The third channel is the most surprising of the three: it reduces $$H(S)$$ *without increasing entropy anywhere*, consuming instead a correlation that already exists between the agent and the subsystem.

Suppose that at time $$t$$ the agent's state and the subsystem's state share mutual information $$I(S_{t}; A_{t}) > 0$$: the agent already "knows something" about the subsystem, in the purely statistical sense of Definition 2.6. To keep the accounting transparent, we assume that the environment is independent of both, so that the joint entropy decomposes (by the definition of mutual information and the chain rule) as

$$
H(S_{t}, A_{t}, E_{t}) \;=\; H(A_{t}) \;+\; H(S_{t}) \;-\; I(S_{t}; A_{t}) \;+\; H(E_{t}).
$$

The agent now performs an operation with the following effects: it *erases the copy of the shared information that resides inside $$S$$*, using its own copy as the key, while leaving its own marginal state and the environment untouched. The operation transforms the subsystem so that

$$
\begin{gathered}H(S_{t+1}) \;=\; H(S_{t}) - I(S_{t}; A_{t}), \qquad I(S_{t+1}; A_{t+1}) \;=\; 0,\\ H(A_{t+1}) = H(A_{t}), \qquad H(E_{t+1}) = H(E_{t}).\end{gathered}
$$

Summing the joint entropy after the operation yields

$$
H(A_{t+1}) + H(S_{t+1}) + H(E_{t+1}) \;=\; H(A_{t}) + H(S_{t}) - I(S_{t};A_{t}) + H(E_{t}),
$$

which is *exactly* the joint entropy from before. The entropy of the subsystem has genuinely fallen by $$I(S_{t}; A_{t})$$ bits, the total entropy is unchanged, no heat has been produced, and no memory has been filled. What has been consumed is the correlation itself: afterward $$I(S_{t+1}; A_{t+1}) = 0$$, and the operation cannot be repeated without first re-acquiring mutual information.

:::callout {title="Tip" tone="green"}

**Example 5.1 (The Controlled-NOT as a Minimal Instance of Type 3).** We illustrate the mechanism through the smallest possible instance, which renders the bookkeeping fully transparent: let the subsystem hold a single uniformly random bit $$s$$, and let the agent hold a perfect copy $$a = s$$. Then $$H(S) = 1$$, $$H(A) = 1$$, $$I(S;A) = 1$$, and the joint entropy is $$H(S, A) = 1$$ bit (two equally likely joint states, $$00$$ and $$11$$). The agent now applies a *controlled-NOT*, which flips $$s$$ if $$a = 1$$ and leaves $$s$$ unchanged if $$a = 0$$. In both joint states the result sets $$s$$ to $$0$$: the subsystem becomes deterministic, with $$H(S_{t+1}) = 0$$, corresponding to a full bit of entropy reduction. The operation is reversible (a second application undoes it), involves no environment, and produces no heat. The joint entropy remains exactly 1 bit, now carried entirely by the agent's own marginal ($$a$$ remains a uniform bit, uncorrelated with the now-deterministic $$s$$). The correlation has been spent: a further application of the operation accomplishes nothing, since $$I(S_{t+1}; A_{t+1}) = 0$$. This confirms that a Type-3 operation reduces the entropy of the subsystem by exactly the mutual information consumed, with the global accounting remaining consistent throughout.

:::

\### 5.5 A reinterpretation of Maxwell's demon, and a synthesis of the three channels

Having identified the three channels individually, we now return to Maxwell's demon, whose operation the Type-3 channel recasts in an illuminating way. The demon's measure-and-control behavior can be decomposed into two distinct steps: a *copy* step, in which the demon interacts with the gas to acquire mutual information with it (this is Type 2: the demon's memory absorbs entropy, or more precisely, becomes correlated with the gas), followed by a *control* step, in which the demon expends that mutual information to steer the gas into a narrower distribution (this is Type 3: the correlation is consumed, and the control step itself produces no further entropy anywhere). In this decomposition, measurement constitutes the purchase of correlation and steering its subsequent expenditure, which raises a quantitative question: how much entropy reduction can the control step purchase per bit of correlation acquired in the copy step? This is precisely the question answered by the *Touchette–Lloyd theorem* (Appendix B), which bounds the steering achievable in a Type-3 step by the mutual information available to be spent, bit for bit. (Section 7.4 subsequently derives an exact algorithmic version of the same bound.)

To summarize, an embedded agent can optimize a subsystem in exactly three ways:

1. **Type 1:** transfer of the subsystem's entropy into the environment as waste heat;
2. **Type 2:** absorption of the subsystem's entropy into the agent's own memory through measurement;
3. **Type 3:** expenditure of mutual information already shared with the subsystem, erasing the subsystem's copy of the correlation.

These three channels are not mutually exclusive but compose in practice: a realistic optimizer cycles among them, measuring (Type 2), steering (Type 3), and periodically clearing its memory into the environment (Type 1) in order to free capacity for the subsequent round.

The Touchette–Lloyd theorem, developed in Appendix B, prices this exchange at one bit of entropy reduction beyond the blind baseline per bit of mutual information between action and environment, and we draw on its statement in what follows.

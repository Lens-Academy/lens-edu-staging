---
id: 'fde292b8-dd92-4860-b6ee-d9c9f609e8cf'
learning-outcome: "Quantify the optimization a process exerts, in bits, as how improbable it would be to get an outcome at least as good (by a stated preference ordering) under a stated baseline distribution, explain why the figure changes when the baseline changes, and explain why one improbable outcome shows optimization only if the process reaches such outcomes reliably across starting conditions and disturbances."
topic: "[[../Domains and Topics/4 Agent Foundations/Optimization]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Optimization. AFFINE prerequisites: Value. Not yet copied into requires:. %%
## Test:
id:: 65150676-d050-445f-820e-874316ef2147

#### Question: Open
id:: dff6dc8e-0cd0-488c-a9ef-027adde0a2bb
content:: An automated lab searches a library of about 2^40 (roughly a trillion) candidate molecules for one that binds strongly to a target protein. System A returns one molecule. Measured afterwards, about 2^10 molecules in the whole library bind at least as strongly as A's pick.

1. Measured against picking a molecule uniformly at random from the whole library, how many bits of optimization does A's pick represent? Show the calculation.
2. A chemist objects: "Nobody picks from the whole library. Our standard filter, which takes a few minutes, cuts the library to 2^20 drug-like molecules, and all 2^10 of the strong binders survive it." Recompute against this baseline. What does the difference between your two figures tell you about System A, and what does it not tell you?
3. A different system, B, also returned a molecule in that top 2^10 on its first run. When the lab reruns B with different random seeds and slightly changed inputs, its picks are spread across the library like random draws. What, if anything, did B's first result show about B as an optimizer? Explain.
max-chars:: 2000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not wording. Terms such as "bits of optimization", "optimization power" or "basin of attraction" are not required; the ideas are.

**(1) Calculation, 25 points.** Full credit: log2(2^40 / 2^10) = 30 bits, or an equivalent statement that the pick is as unlikely as a 1-in-2^30 random draw. 12 points if the method is right (log of the ratio of all outcomes to outcomes at least as good) but the arithmetic is wrong.

**(2) Baseline dependence, 35 points.** 15 points for the recomputation: log2(2^20 / 2^10) = 10 bits. 20 points for interpretation, which needs both of these: (a) the bit count is relative to the baseline distribution one chooses, so there is no single "true" figure without stating the baseline; (b) most of the 30 bits are work the cheap filter already does, and the 10 bits measure what A adds beyond standard practice. Accept either view of which baseline is more useful, if argued. For "what it does not tell you", accept any correct limit, for example: it says nothing about how much computation or time A spent (efficiency), nothing about whether A would do as well on other targets, or that the figure also depends on the chosen ordering (binding strength only). An answer that only states that the numbers differ, without (a) or (b), gets at most 20 of the 35.

**(3) Reliability, 40 points.** Full credit needs the idea that optimization is a property of the process across conditions, not of one outcome: B's picks on reruns are distributed like the baseline, so B does not reliably steer toward strong binders, and the single result cannot be counted as evidence of B's optimization power on its own. Strong answers also notice that a 1-in-2^30 hit by pure chance is itself very unlikely, and so offer an explanation such as: B works only in the exact original conditions (it reaches the target from a tiny set of starting states and fails under small disturbances), the original run had access to information it should not have had, or the first measurement was wrong. Any one well-argued explanation of this kind earns the top of the range; it is not required for 30 of the 40. 15 points for saying only "it was luck" without the process-versus-outcome point. Do not penalise an answer that says B may still be an optimizer in a very narrow sense, if it explains why that does not make B a useful or reliable one.

Do not penalise answers that use natural logarithms, if the unit is stated.
feedback-instructions:: Name the part of the answer that best shows the learner treats optimization as relative to a baseline and as a property of a process. Then name the single most useful improvement, for example: stating the baseline explicitly before quoting a number, or asking what B's result would look like under disturbance. If the learner missed that a 2^-30 chance hit is itself suspicious, ask them what they would check first. No generic praise.

---
id: '68d21c7d-66ff-4eb7-933c-941e2b489781'
learning-outcome: "Work out which option or lottery geometric maximization selects (maximizing the probability-weighted product, or equivalently the expected logarithm, of a quantity across people, worlds or hypotheses) and contrast it with arithmetic maximization, explaining why its choice is unchanged when one party's utilities are rescaled, why it can prefer a lottery to every single option, and what it depends on instead, such as the choice of zero point."
topic: "[[../Domains and Topics/4 Agent Foundations/Decision theory]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Geometric Rationality. AFFINE prerequisites: Decision theory. Not yet copied into requires:. %%
## Test:
id:: 993c2a2e-9a65-4b5b-b866-40e7570eb5df

#### Question: Open
id:: bcfbb3d7-d40c-4968-a977-6189a8593291
content:: Two co-founders, Ana and Ben, jointly instruct an AI assistant to choose the company's plan for next quarter. Their utilities for each plan are measured relative to "no plan agreed", which both value at 0:

- Plan P: Ana 9, Ben 1
- Plan Q: Ana 2, Ben 6
- Plan R: Ana 4, Ben 4

The assistant may also choose a lottery over plans (for example, a weighted coin that picks P or Q). Each founder's utility for a lottery is their expected utility.

1. Which plan or lottery does the assistant choose if it maximizes the sum of the two founders' expected utilities? Which does it choose if it maximizes the product of their expected utilities (equivalently, their geometric mean)? Show your working. An approximate answer for a lottery is fine.
2. Ben then says his numbers were written in a different unit and each should be multiplied by 10. How does each assistant's choice change, and why?
3. What does this show about when maximizing the product is a better way to combine two people's preferences than maximizing the sum? Give one serious objection or limitation.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning. Terms such as "Nash bargaining", "geometric expectation" or "independence axiom" are not required.

**(1) Calculation, 40 points.**
- Sum (10 points): P, with sum 10 (Q and R give 8). Because the sum of expected utilities is linear in the lottery weights, no lottery beats the best single plan.
- Product (30 points): among single plans the products are P 9, Q 12, R 16, so R is the best single plan. But a lottery does better: R lies below the line from P to Q (at Ana = 4 the line gives Ben about 4.57), so the best options are mixtures of P and Q. With weight t on Q, Ana gets 9 - 7t and Ben gets 1 + 5t; the product 9 + 38t - 35t^2 is largest at t = 19/35, about 0.54, giving Ana about 5.2, Ben about 3.7, and a product of about 19.3. Full credit for identifying a P/Q lottery with weight on Q roughly between 0.5 and 0.6, with working. 20 points for choosing R with correct products but no lottery. 10 points for a correct method with arithmetic errors that change the answer.

**(2) Rescaling, 30 points.** Sum: with Ben's numbers times 10, P gives 19, Q gives 62, R gives 44, so the sum-maximizer switches to Q (15 points). Product: every product is multiplied by 10, so the product-maximizer's choice does not change (15 points). Reasons are required for full credit on each part.

**(3) Interpretation, 30 points.** (a) 15 points: maximizing the product does not need the two people's utilities to be in comparable units, because rescaling one person's utility does not change its choice, whereas the sum's choice depends on an arbitrary choice of units; related points also count, such as that it gives each party a share and will not sacrifice one party entirely for a larger total. (b) 15 points: one real objection or limitation, for example: the result depends on the zero point (here "no plan agreed"), and shifting one person's zero point changes the choice; it recommends randomizing, which violates the independence axiom of expected utility theory and so conflicts with standard coherence arguments; after the coin is flipped, one founder may prefer to renegotiate; or, if units really are comparable, the sum may be the better guide. Accept any objection that is true and relevant.
feedback-instructions:: Tell the learner whether they found that a lottery beats every single plan under the product rule. Name the strongest part of their interpretation. Then give the single most useful improvement, for example: explaining why rescaling multiplies every product by the same number, or testing what happens to the choice if Ben's zero point moves. No generic praise.

---
id: '593867e7-102c-4afc-9836-bf5af4763b8e'
learning-outcome: "Given an agent's rule for approving successors or self-modifications, determine whether the rule tiles (the agent would approve a successor that uses the same rule, so a safety property passes down every chain of successors), explain the Löbian obstacle that stops a rule of the form 'approve only successors that my own proof system proves safe' from approving itself, and explain why a safety property that does not tile is at risk in a self-modifying system."
topic: "[[../Domains and Topics/4 Agent Foundations/Recursive self-improvement]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Reflective Stability / Tiling. AFFINE prerequisites: Decision theory, Recursive self-improvement. Not yet copied into requires:. %%
## Test:
id:: 92d74ad3-350d-4e59-92d4-d7766b85dbf0

#### Question: Open
id:: 92b215ee-4da9-47b7-9820-b523cc50e783
content:: An AI system A controls a laboratory robot. The safety property we care about is: never open the freezer door while the alarm is on. A can also approve a successor, a new version of the code that takes over from it.

A reasons in a fixed formal proof system T. Assume T is consistent and sound (everything it proves is true). A's approval rule is:

- A approves a proposed successor X exactly when there exists a proof, in T, that "X is safe".

Here "X is safe" means: X never opens the freezer while the alarm is on, and every successor that X would approve is also safe (and so on, down every chain of successors).

1. The engineers propose an exact copy of A (same code, same proof system T, same rule) as its successor. Will A approve it? Give the reasoning, not only the verdict.
2. Propose a change to the approval rule that would let an agent approve a copy of itself while still approving only safe successors. Say why your change avoids the difficulty from part 1, and what it costs, assumes, or leaves unsolved. A known approach or your own idea are both fine.
3. The builders of a self-improving AI will probably never use formal proofs like this. Why should they still care whether its safety properties tile?
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement with any particular research programme. Do not require formal notation or theorem names: an answer that reconstructs the self-reference argument in words gets full credit.

**(a) Will A approve its copy, 45 points.** Full credit: No (given that T is consistent). For A to approve the copy, T must prove "the copy is safe". The copy approves every X that T proves safe, so "the copy is safe" contains the claim "for every X, if T proves X is safe, then X is safe": T would have to vouch for the reliability of its own safety proofs. A consistent T cannot prove this. One route: take a successor that plainly opens the freezer during an alarm, so T proves it is not safe; if T also proved "if T proves it safe, then it is safe", Löb's theorem would give that T proves it safe, so T would be inconsistent. Equivalent routes are fine, for example via Gödel's second incompleteness theorem or "a consistent system cannot prove its own soundness", provided the answer connects this to the specific step (the copy's safety requires T to trust T's own proofs). Extra credit within the 45 for noting that A rejects the copy even though, if T is sound, the copy is in fact safe. 25 points if the answer gets the verdict and says the problem is a system being unable to trust itself, without identifying which claim T would need to prove. 10 points for "No" with only a vague reason such as "because of Gödel". 0 to 5 points for "Yes, it is identical, so it is safe" without addressing what T must prove. Do not penalise a remark that an inconsistent T would prove everything and so approve anything; that is correct.

**(b) A change that restores self-approval, 35 points.** Full credit requires (1) a concrete change, (2) an explanation of why it avoids the step from part 1, and (3) one genuine cost, assumption, or open problem. Acceptable routes include, among others: prove that each approved successor will itself come with a proof of safety, rather than proving directly that all future proofs are trustworthy (self-approval then becomes easy, but the new safety notion implies real safety only if T is sound, and some safe successors, for example one that searches for a proof that a proof exists, may still be rejected); a descending chain of proof systems in which each generation trusts a slightly weaker system (cost: trust weakens with each generation, or only finitely many generations are covered); probabilistic or bounded self-trust (cost: no proof-level guarantee, and open research questions); relying on a fixed external check of the successor's actions (cost: the successor cannot be trusted with anything the check cannot see, and the check itself must be preserved). An answer that adds the axiom "T is sound" to get a stronger system earns full credit only if it notices that the stronger system now faces the same problem for its own successors, which leads to a tower of systems. 20 points for a plausible change with a weak explanation or no cost. 0 points for a change that simply assumes the conclusion without noticing it.

**(c) Why builders should care, 20 points.** Full credit: a self-modifying or successor-building system changes itself repeatedly; any property that its own criteria for accepting changes do not actively preserve can be lost at some step, especially when strong optimisation reshapes whatever it is not required to keep; so a safety property holds in the long run only if the system's acceptance of changes positively keeps it. The logical obstacle shows that even an agent that wants to keep the property can fail to recognise safe successors, which pushes it either to stop improving or to accept successors on weaker grounds. Any wording that captures "a property survives self-modification only if the system's own change-acceptance preserves it" earns full credit. 10 points for "the property could get lost" without a mechanism. A learner may argue that current machine-learning systems are not self-modifying agents with explicit approval rules, so the relevance is indirect; give full credit if the answer still states under what conditions tiling would matter.
feedback-instructions:: Tell the learner whether, in part 1, they located the exact claim T would need to prove about its own proofs. Name their strongest move in part 2, and the most important cost or assumption they missed or understated. Ask one follow-up question that pushes on their proposed fix. No generic praise.

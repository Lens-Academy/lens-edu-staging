---
id: '1c90faf2-2c07-47ee-be86-a7979b92165a'
learning-outcome: "Given, for a control protocol, how likely a single attack attempt is to be caught and how likely it is to succeed unnoticed, and how these odds change with how often the attacker attacks, estimate a scheming model's overall chance of getting a successful attack through for a given number of attempts, determine which attack rate a best-responding attacker would choose, explaining that attacking more often makes it likelier that some attempt settles the game but, when extra attacks have worse odds, less likely that the settling attempt is a win, and explain why the protocol's safety must be stated against that best response rather than against a fixed attack policy."
topic: "[[../Domains and Topics/7 AI Control/Evaluating and using control]]"
stage: intermediate
requires:
  - "[[Control evaluation methodology]]"
authors:
  - Elias+Claude
---
## Test:
id:: ff164dda-7b4b-45ef-8480-140d32c89425

#### Question: Open
id:: 54044726-19a7-45be-9478-da17008eee0c
content::
An AI agent U applies 20,000 configuration changes to a lab's servers over one deployment. U may be scheming, and it knows the protocol. A trusted monitor scores every change for suspicion. Any change scoring above a threshold, set so that about 1% of normal changes cross it, goes to a human reviewer, who always recognises an attack. Each attack attempt ends in one of three ways:

- it is reviewed and caught: the deployment is shut down and U has lost;
- it is not reviewed and works: U has won and the game is over;
- it is not reviewed but is broken: nothing happens and the deployment continues.

Assume attempts are independent. A red team, standing in for U, measured the average odds of an attempt depending on how many changes U attacks:

| U attacks on | chance an attempt is caught | chance an attempt works unnoticed |
| --- | --- | --- |
| 5 changes | 0.08 | 0.06 |
| 20 changes | 0.10 | 0.05 |
| 100 changes | 0.20 | 0.04 |
| 400 changes | 0.30 | 0.03 |

The evaluation report used the last row, since that attack policy produced the most attacks, and states: "Safety: 91%" (safety meaning the chance that no attack ever works).

1. For each row, estimate U's chance of winning over the deployment. Show how you got it.
2. Which option would a scheming U choose, and why that one rather than the others?
3. Is 91% the right safety figure for this protocol? If not, what should the report state, and why?
placeholder:: Show your calculation, then answer parts 2 and 3
assessment-instructions:: Score 0 to 100. The capability tested is modelling a best-responding attacker against a protocol whose per-attempt odds depend on the attack rate. Reference numbers: with per-attempt catch probability c, success probability s and k independent attempts, the deployment is settled by the first attempt that is caught or works, so U wins with probability s/(s+c) times (1 - (1-s-c)^k). 5 changes: 0.06/0.14 = 0.43, times 1 - 0.86^5 = 0.53, gives about 0.23. 20 changes: 0.05/0.15 = 0.33, times 1 - 0.85^20 = 0.96, gives about 0.32. 100 changes: 0.04/0.24, about 0.17 (the second factor is essentially 1). 400 changes: 0.03/0.33, about 0.09 (the second factor is essentially 1). Equivalent methods are fine, for example summing over which attempt is the first one that is caught or works, or a Markov-chain argument. Accept values within about 0.03 of these, and do not penalise rounding. Load-bearing elements: (1) about 35 points: the four estimates by a sound method. Full credit needs the method to reflect both that a caught attempt ends the game before any later attempt can win and that with few attempts the deployment may end with no attempt caught or working. Method errors: an answer that adds up wins from separate attempts, or computes 1 - (1-s)^k while ignoring catches, earns at most 10 of these points; an answer that uses only s/(s+c) for every row, ignoring that with few attempts nothing may be decided (giving about 0.43 for 5 changes), earns at most 15 of these points. One arithmetic slip with a sound method loses at most 8 points. Gating: an answer whose method does not reflect both that a caught attempt ends the game and that with few attempts nothing may be decided (for example 1 - (1-s)^k in place of 1 - (1-s-c)^k, with or without the ratio s/(s+c)), so that its estimates are off by more than about 0.05, cannot score above 55 in total, even if it goes on to choose 20 changes. (2) about 35 points: U chooses about 20 changes, with both halves of the reason in any wording: (a) attacking very rarely is worse because the deployment often ends with no attempt either caught or working (with 5 attempts this happens with probability 0.86^5, about 0.47; this is not the same as the chance that no attempt works), so more attempts help at first; (b) attacking more often is worse because the per-attempt odds shift: the chance of being caught rises relative to the chance of working (s/(s+c) falls from about 0.43 at 5 changes to about 0.09 at 400), so the attempt that settles the game is less often a win. A cause for the worse odds, such as having to use changes with less cover, is welcome but not required. Gating: an answer that chooses 5 changes (unless that choice follows correctly from the learner's own sound-method figures that differ only by an arithmetic slip), or that does not explain both (a) and (b), cannot score above 55 in total. (3) about 30 points: 91% is not the right figure, because safety has to be stated against U's best response: about 68% (1 minus about 0.32; accept 66% to 70%, or 1 minus the learner's own figure for their chosen option when that figure came from a sound method with at most an arithmetic slip; a figure from an unsound method earns at most 15 of these points). The 91% describes an attack policy a scheming U would not use, so it overstates safety. Gating: an answer that accepts 91% as this protocol's safety, or gives no reason why the attacker's best option is the one that counts, cannot score above 50 in total. Do not require the terms "best response", "Term A" or "decisive", or any author's name. Grade reasoning, not agreement: a learner who adds that the red team may not have found U's true best option, so even 68% could be optimistic, or that options between the rows should also be checked, is making a correct extra point and must not lose marks. A pass is roughly 60.
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner added wins from separate attempts or ignored that a caught attempt ends the game, show in one sentence why the first attempt that is caught or works settles everything. If they chose 5 changes or left out the chance that nothing is decided, point out that with 5 attempts the deployment ends with nothing decided about half the time. If they missed why more attacks hurt U, point to how the ratio of the two chances moves down the table. Do not reveal or discuss the numerical score. At most six sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-2]]
notes:: Teaches the first-decisive-attempt decomposition, the fixed-odds prediction and why it fails, the opportunity cutoff and obfuscation effort, and the control game with a best-responding red team. Practice with feedback: the deployment-race and red-team questions (why the first decisive attempt settles the game, interpreting the two terms, the numerical practice comparing a rare and a frequent attack strategy, what lowering the opportunity cutoff or the obfuscation effort does, what an uninformed red team loses), plus the optional upfront-auditing derivation.

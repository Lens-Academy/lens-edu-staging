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
assessment-instructions:: Score out of 100. 35 for part 1: the four estimates by a sound method, one that reflects both that the first attempt that is caught or works settles the game (a caught attempt ends it before any later attempt can win) and that with few attempts the deployment may end with nothing decided; for example U wins with probability s/(s+c) times (1 - (1-s-c)^k) for per-attempt catch chance c, success chance s and k attempts, or an equivalent sum over which attempt is the first to be caught or work, or a Markov-chain argument. Reference figures, accepted within about 0.03 and without penalty for rounding: 5 changes about 0.23 (0.06/0.14 = 0.43 times 1 - 0.86^5 = 0.53), 20 changes about 0.32 (0.05/0.15 = 0.33 times 1 - 0.85^20 = 0.96), 100 changes about 0.17 (0.04/0.24, the second factor essentially 1), 400 changes about 0.09 (0.03/0.33). At most 10 of these points if the method adds up wins from separate attempts or computes 1 - (1-s)^k while ignoring catches; at most 15 if it uses s/(s+c) for every row, ignoring that with few attempts nothing may be decided (about 0.43 for 5 changes); one arithmetic slip with a sound method loses at most 8. 35 for part 2: 5: U chooses about 20 changes. 15: attacking very rarely is worse, because the deployment often ends with no attempt either caught or working (with 5 attempts about 0.86^5, roughly 0.47, which is not the same as the chance that no attempt works), so more attempts help at first. 15: attacking more often is worse, because the chance of being caught rises relative to the chance of working (s/(s+c) falls from about 0.43 at 5 changes to about 0.09 at 400), so the attempt that settles the game is less often a win. 30 for part 3: 10: 91% is not the right figure. 10: the report should state about 68% (1 minus about 0.32; accept 66% to 70%, or 1 minus the learner's own figure for their chosen option when it came from a sound method with at most an arithmetic slip). 10: why: safety must be stated against the attacker's best response, and 91% describes an attack policy a scheming U would not use, so it overstates safety. At most 15 of the part 3 points if the figure comes from an unsound method. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 55 if the method does not reflect both that a caught attempt ends the game and that with few attempts nothing may be decided (for example 1 - (1-s)^k in place of 1 - (1-s-c)^k, with or without the ratio s/(s+c)), so that the estimates are off by more than about 0.05, even if the answer goes on to choose 20 changes. Cap at 55 if the answer chooses 5 changes (unless that follows correctly from the learner's own sound-method figures that differ only by an arithmetic slip), or does not explain both why rarer and why more frequent attacks are worse. Cap at 50 if the answer accepts 91% as this protocol's safety, or gives no reason why the attacker's best option is the one that counts. A pass is roughly 60. Model answer, for the feedback, not a grading checklist: "1. The first attempt that is either caught or works settles the game, so with catch chance c, success chance s and k independent attempts, U wins with probability s/(s+c) times (1 - (1-s-c)^k): the chance that the settling attempt is a win, times the chance that some attempt settles the game at all. 5 changes: 0.06/0.14 = 0.43 times 1 - 0.86^5 = 0.53, about 0.23. 20 changes: 0.05/0.15 = 0.33 times 1 - 0.85^20 = 0.96, about 0.32. 100 changes: 0.04/0.24, about 0.17 (the second factor is essentially 1). 400 changes: 0.03/0.33, about 0.09. 2. U would attack about 20 changes. Attacking only 5 is worse because about 47% of the time (0.86^5) the deployment ends with no attempt caught or working, so U often never gets a decisive attempt. Attacking 100 or 400 is worse because each extra attack has worse odds: the chance of being caught rises relative to the chance of working, so the attempt that settles the game is much less often a win. 20 balances the two. 3. No. 91% is safety against the 400-change policy, which a scheming U would not use. Safety has to be stated against U's best response, so the report should state about 68% (1 - 0.32), and even that holds only if the red team found U's best option."
feedback-instructions:: Name the strongest part of the answer in one sentence, then the single change that would most improve it. If the learner added wins from separate attempts or ignored that a caught attempt ends the game, show in one sentence why the first attempt that is caught or works settles everything. If they chose 5 changes or left out the chance that nothing is decided, point out that with 5 attempts the deployment ends with nothing decided about half the time. If they missed why more attacks hurt U, point to how the ratio of the two chances moves down the table. Do not reveal or discuss the numerical score. At most six sentences.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper-2]]
notes:: Teaches the first-decisive-attempt decomposition, the fixed-odds prediction and why it fails, the opportunity cutoff and obfuscation effort, and the control game with a best-responding red team. Practice with feedback: the deployment-race and red-team questions (why the first decisive attempt settles the game, interpreting the two terms, the numerical practice comparing a rare and a frequent attack strategy, what lowering the opportunity cutoff or the obfuscation effort does, what an uninformed red team loses), plus the optional upfront-auditing derivation.
## Lens:
source:: [[../Lenses/XLab Control - ai-control-paper]]
notes:: Sets up the game this outcome reasons about: the blue team's protocol and 2% audit budget, the red team's secret attack policy, and safety defined as the chance of never shipping a backdoor, measured against the red team's best response.

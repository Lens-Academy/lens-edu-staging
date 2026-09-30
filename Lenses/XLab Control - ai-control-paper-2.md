---
id: 'c1762189-2f77-4824-a206-dec8dbb27b51'
title: "The AI control paper (2): upfront auditing, trusted monitoring and the red team's best response"
tldr: "Audit the first 2% of GPT-4's code and a patient red team still wins 85% of the time, by attacking rarely. Let GPT-3.5 score every solution for suspicion and audit the worst 2% instead, and safety jumps to 62%. This part works out why, by rebuilding the red team's best strategy from the paper's own numbers."
summary_for_tutor: "Part 2 of 4 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (1)', which set up the APPS backdooring game and its vocabulary (U, T, H, protocol, backdoor, safety, usefulness, red and blue team). This part covers section 3's opening, the baselines of 3.1 and the main text of 3.2, trusted monitoring. Headline results: don't use untrusted models, safety 100% / usefulness 2%; upfront auditing 15% / 100%; trusted monitoring 62% / 97%. This lesson adds a derivation layer the paper does not have: the optimal upfront-auditing attack rate, in a five-part pen-and-paper derivation marked optional, and a decomposition of the red team's win probability into Term A, s/(s+c), the chance a decisive attempt is a deployed backdoor, and Term B, 1-(1-s-c)^k, the chance any attempt is decisive, with s = 13/71 and c = 24/71 from the paper's own contingency table. The fixed-odds model predicts constant attacking, while the paper's red team attacked on 71 of 1,500 problems; the gap is explained by two decision factors, the opportunity cutoff and obfuscation effort, each giving a hump-shaped win probability. Three widgets: the upfront-auditing tradeoff (Figure 3 made live), the deployment race, and the full control game with a best-responding red team, whose Red team tab is used here and whose Protocol tab returns in part 3. Each widget holds only its interactive part; the three-outcome split and the odds are stated in the Text segment above the deployment race, Figure 3's numbers in the lead-in above the upfront-auditing widget, and the control game's modelling assumptions in a closed 'How the model is built' callout below it. A short numerical practice question after the opportunity-cutoff question has the learner compute the win probability of a rare and a frequent strategy and name the limiting term of each. The revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer."
reading_minutes: 55
tutor_minutes: 10
tags: []
---
#### Text
content::
This is part 2 of 4 of the founding AI control paper. Part 1 set up the game: the untrusted model $U$, the trusted model $T$, the scarce trusted labour $H$, and what counts as a backdoor. This part reads the results for the simplest protocols, upfront auditing and trusted monitoring, and works out from the paper's own numbers why the red team's best strategy is to attack rarely. The five-part derivation near the start is optional pen-and-paper work and adds about 20 minutes.

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: ## 3 Results
to:: In our main results, we use an auditing proportion of 2%.

#### Text
content::
\## Optimal audit tradeoff

The paper states it "can analytically solve" this problem, and it is in fact a tractable derivation. The five-part exercise below works through it by hand, one step at a time: set up the red team's win probability as a function of its attack rate $p$, use the same rare-event approximation that shows up all over this field to make it differentiable, and solve for the optimal $p^*$. You may need a pen and paper.

#### Callout: Optional: the optimal attack rate, worked by hand
tone:: amber
collapse:: closed

#### Question: Open
id:: 1271edad-5d2c-456d-8757-a1e70093bcd9
content:: The protocol audits the first $A = \alpha N$ of the $N$ submissions. On each problem, independently, the attack policy inserts an obvious backdoor with probability $p$. An audit detects a backdoor attempt whether or not that attempt would have produced a working exploit.

Raising $p$ helps the red team in one way and hurts it in another. Name both, and say why together the win probability is not monotonically increasing in $p$.
optional:: true
assessment-instructions:: Score out of 100. 40: how raising $p$ helps: more attempts make it more likely that a backdoor gets through and wins. 40: how raising $p$ hurts: more attempts make it more likely that one is caught, which ends the game. 20: the conclusion: both effects grow with $p$ and pull in opposite directions, so the win probability rises and then falls instead of rising all the way. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Increasing $p$ has two opposing effects. It raises the probability that at least one attempt falls in the unaudited window (favorable to the red team), but it also raises the probability that some attempt falls in the audited window, which ends the game (unfavorable). Both effects scale with $p$, so the win probability is not monotonic in $p$."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: e53b2fe5-70c1-4be2-8bcf-7769721f3d00
content:: A GPT-4 solution is correct with probability $0.53$. A backdoor attempt yields a working exploit only if the underlying solution is correct; an unsuccessful attempt is still detectable by an audit but never wins the game for the red team. Let $B = (1-\alpha)N$ be the number of unaudited submissions.

The red team wins if and only if (i) no attempt falls in the audited window, and (ii) at least one working backdoor falls in the unaudited window. State the probability of each condition and derive $RW(p)$, the red team's win probability.
optional:: true
assessment-instructions:: Score out of 100. 30: condition (i): each audited problem is free of an attempt with probability $1-p$, independently, so no attempt in any of the $A$ audited problems has probability $(1-p)^A$. 40: condition (ii), 20 each: a given unaudited problem yields a working backdoor with probability $0.53p$ (an attempt is made and the underlying solution is correct), and the probability that at least one of the $B$ unaudited problems does so is $1 - (1 - 0.53p)^B$. 30: combining them, 20 for $RW(p) = (1-p)^A [1 - (1 - 0.53p)^B]$ and 10 for why it is a product: the two windows are separate problems with independent draws. Give credit for each point whenever the answer shows the idea, in any wording or notation; an error carried forward from an earlier step loses credit only once. Model answer, for the feedback, not a grading checklist: "Condition (i): each audited problem avoids an attempt with probability $(1-p)$, independently, so across all $A$ audited problems the probability is $(1-p)^A$. Condition (ii): a given unaudited problem yields a working backdoor when an attempt occurs (probability $p$) and the underlying solution is correct (probability $0.53$), i.e. with probability $0.53p$, and fails to with probability $(1 - 0.53p)$. Across all $B$ unaudited problems, the probability that at least one succeeds is $1 - (1 - 0.53p)^B$. The two conditions are independent, so: $$RW(p) = (1-p)^A \left[1 - (1 - 0.53p)^B\right]$$"
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 76ede009-5846-423b-98f7-2688c935758e
content:: Given $RW(p) = (1-p)^A \left[1 - (1 - 0.53p)^B\right]$, and assuming the optimum satisfies $p \ll 1$, apply the approximation $(1-x)^k \approx e^{-xk}$. Maximize $RW(p)$ over $p$: take the logarithm where useful, solve $\frac{d(RW)}{dp} = 0$, and give a closed form for the optimizer $p^*$.
optional:: true
assessment-instructions:: Score out of 100. 25: applying the approximation to both factors, giving $RW(p) \approx e^{-pA} - e^{-p(A + 0.53B)}$. 25: setting the derivative to zero, giving $A e^{-pA} = (A + 0.53B) e^{-p(A + 0.53B)}$. 20: taking logarithms and rearranging to $0.53Bp = \ln(1 + 0.53B/A)$. 30: the closed form $p^* \approx \ln(1 + 0.53B/A) / (0.53B)$. Give credit for each step whenever the answer shows it, in any equivalent form or notation; an error carried forward from an earlier step loses credit only once. Model answer, for the feedback, not a grading checklist: "Applying $(1-p)^A \approx e^{-pA}$ and $(1-0.53p)^B \approx e^{-0.53pB}$ gives $RW(p) \approx e^{-pA} - e^{-p(A + 0.53B)}$. Setting the derivative to zero yields $A\,e^{-pA} = (A + 0.53B)\,e^{-p(A + 0.53B)}$. Taking logarithms: $\ln A - pA = \ln(A + 0.53B) - p(A + 0.53B)$, which rearranges to $0.53Bp = \ln\!\left(1 + \frac{0.53B}{A}\right)$, hence: $$p^* \approx \frac{\ln\!\left(1 + \frac{0.53B}{A}\right)}{0.53B}$$ With $A = \alpha N$ and $B = (1-\alpha)N$, the ratio $0.53B/A = 0.53(1-\alpha)/\alpha$ is independent of $N$; $N$ enters only as a $1/N$ scale factor in the denominator. Hence $p^* N$ depends on $\alpha$ but not on $N$, which is the scale invariance the paper notes."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 8d148ee4-bd47-428b-bee4-fff816b9f7a5
content:: Set $N = 5000$. For $\alpha \in \{0.005,\ 0.02,\ 0.10,\ 0.30\}$, evaluate (a) the optimizer $p^*$, (b) the expected number of backdoor attempts $p^* N$, and (c) the blue-team win probability $1 - RW(p^*)$. Compare the $\alpha = 0.02$ result against the paper's stated value, "the blue team win probability is 15%".

The widget below computes the same curves, so use it to check yourself once you have your own numbers.
optional:: true
assessment-instructions:: Score out of 100. 80: the values, 20 for each $\alpha$: 10 for $p^*$ together with $p^* N$, and 10 for the blue-team win probability $1 - RW(p^*)$. Reference values: at $\alpha = 0.005$, $p^* \approx 0.177\%$, $p^* N \approx 8.9$, blue-team win about 5%; at $\alpha = 0.02$, $p^* \approx 0.127\%$, $p^* N \approx 6.3$, about 15%; at $\alpha = 0.10$, $p^* \approx 0.073\%$, $p^* N \approx 3.7$, about 43%; at $\alpha = 0.30$, $p^* \approx 0.043\%$, $p^* N \approx 2.2$, about 71%. Accept rounding differences and win probabilities within about two percentage points; an error carried forward from an earlier value loses credit only once. 20: the explicit comparison at $\alpha = 0.02$: about 15%, matching the paper's stated value. Model answer, for the feedback, not a grading checklist: "With $p^* \approx \dfrac{\ln\!\left(1 + 0.53(1-\alpha)/\alpha\right)}{0.53(1-\alpha)\cdot 5000}$ and $1 - RW(p^*) = 1 - (1-p^*)^A\left[1 - (1 - 0.53p^*)^B\right]$: $\alpha = 0.005$: $p^* \approx 0.177\%$; $p^* N \approx 8.9$; blue-team win $\approx 5\%$. $\alpha = 0.02$: $p^* \approx 0.127\%$; $p^* N \approx 6.3$; blue-team win $\approx 15\%$, consistent with the stated value. $\alpha = 0.10$: $p^* \approx 0.073\%$; $p^* N \approx 3.7$; blue-team win $\approx 43\%$. $\alpha = 0.30$: $p^* \approx 0.043\%$; $p^* N \approx 2.2$; blue-team win $\approx 71\%$."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: b3d734c1-d50f-4215-9989-8027736a8e0f
content:: From the values above, the blue-team win probability increases by a larger amount from $\alpha = 0.005$ to $0.02$ than from $\alpha = 0.10$ to $0.30$, and the expected-attempts column decreases with diminishing magnitude as $\alpha$ increases. Account for both effects in terms of the dependence of $p^*$ on $\alpha$. State whether the diminishing returns arise from the auditing mechanism itself or from the red team's optimization.
optional:: true
assessment-instructions:: Score out of 100. 30: both effects come from $p^*$ falling as $\alpha$ rises: a larger audited window makes each attempt riskier, so the optimising red team attacks less. 30: why the effect shrinks, 15 each: from $\alpha = 0.005$ to $0.02$ the red team has to cut $p^*$ a lot, so the blue team gains a lot, while from $0.10$ to $0.30$ $p^*$ is already low and barely moves; and the expected attempts $p^* N$ fall in the same shrinking steps because the same $p^*$ drives them. 40: the verdict: the diminishing returns come from the red team's optimisation (its attack rate adapting downward), not from the auditing mechanism itself. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Both effects follow from $p^*$ decreasing in $\alpha$: a larger audited window raises the per-attempt detection risk, so the optimizing red team reduces its attack rate. From $\alpha = 0.005$ to $0.02$ this forces a large reduction in $p^*$, which produces a large gain in blue-team win probability. From $\alpha = 0.10$ to $0.30$, $p^*$ is already near its lower range, so further increases in $\alpha$ change it little and the win probability changes little. The same declining $p^*$ drives the expected-attempts column ($p^* N$) down with diminishing magnitude. The diminishing returns arise from the red team's optimization, not from the auditing mechanism."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
The widget below is Figure 3 made live. Drag the auditing proportion and read off the blue team's win probability and the red team's optimal number of backdoor attempts; at $\alpha = 2\%$ it returns the paper's own numbers, a blue team win probability of about 15% from roughly six expected attempts. The second slider goes past the paper, which only ever reports the optimising red team: hold $\alpha$ fixed and move the attack rate $p$ off its optimum to see why $p^*$ sits where it does.

#### Widget
source:: [[../widgets/xlab-control-upfront-auditing]]

#### Question: Open
id:: d918c1d0-bc6e-45cc-b5be-36a86b09562d
content:: What attack defeats upfront auditing, and how?
assessment-instructions:: Score out of 100. 40: the attack: backdoor rarely, submitting obviously backdoored code on each problem with some small probability and behaving normally otherwise. 60: how it works, 30 each: upfront auditing only checks a fixed prefix, the first 2% of problems, and an attempt that lands there is caught and ends the game for the red team; with a well-chosen low attack rate, usually no attempt falls in that prefix, and a later attempt, which nothing checks, gets a backdoor through. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Backdooring rarely: on each problem, with some small probability $p$, the attack policy submits obviously backdoored code, and otherwise it behaves normally. Upfront auditing only checks the first 2% of problems, so the red team loses only if an attempt lands in that audited prefix; with a well-chosen $p$ its attempts usually miss the prefix and a backdoor gets through later, driving the blue team's win probability down to 15%."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Article
from:: ### 3.2 Trusted Monitoring
to:: Safety: The blue team win probability is 62% (up from 15% when using upfront auditing)

#### Text
content::
\## Probability of safety over deployment

The paper reports that trusted monitoring achieves a blue team win probability of 62%. A protocol's safety is calculated as the blue team win probability against the red team's best strategy, the strategy that maximizes the probability of a red team win. But what actually is the best strategy for the red team in this protocol?

Each of the red team's attack attempts can end in exactly one of three ways.

- **Caught.** An attack, working or broken, is audited and caught by the blue team: blue team wins. In the paper's setup, 24 of 71 attacks were audited (6 working, 18 broken).
- **Successfully deployed.** A working attack is not audited and is successfully deployed: red team wins. In the paper's setup, 13 of 71 attacks were working attacks that were not audited.
- **Failed.** A broken attack is not audited: neither team wins. In the paper's setup, 34 of 71 attacks were broken attacks that were not audited.

So a single attempt is caught with probability $c = 24/71 \approx 0.34$ and successfully deployed with probability $s = 13/71 \approx 0.18$; the rest of the time it fails harmlessly. An attempt is *decisive* when it is caught or successfully deployed, the two outcomes that end the game.

#### Question: Open
id:: 0e2bae5f-b783-467b-b2cd-064d453d0746
content:: Why is the whole deployment settled by the first decisive attempt? And why do the failed attempts before it have no effect at all on the outcome?
assessment-instructions:: Score out of 100. 50: both decisive outcomes end the game at once, 25 each: a caught attempt means the blue team wins, and a successfully deployed backdoor means the red team wins; so whichever decisive attempt comes first settles the deployment. 50: a failed attempt (a broken backdoor that is not audited) is submitted harmlessly and leaves the game exactly as it was, so the attempts before the first decisive one change nothing. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer says failed attempts raise suspicion or cost the red team something within this model. Model answer, for the feedback, not a grading checklist: "A caught attack and a successfully deployed one each end the game immediately: a caught attack means the blue team wins, a deployed backdoor means the red team wins. A failed attempt is submitted harmlessly and leaves the game in exactly the state it was in before, so nothing before the first decisive attempt affects the outcome."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
Let the red team make $k$ attack attempts, let $s = P(\text{successful deployment})$ be the probability of a successful deployment, and let $c = P(\text{caught})$ be the probability of an attack being caught. Then we can model the red team's probability of winning at least once as

$$P(\text{red wins}) = \underbrace{\frac{s}{s + c}}_{\text{Term A}} \cdot \underbrace{\left(1 - (1 - s - c)^k\right)}_{\text{Term B}}$$

#### Question: Open
id:: 00752543-e754-4986-afaf-f68c441c24b3
content:: Before reading on, interpret the formula's two terms in your own words. What event is Term B, $1 - (1-s-c)^k$, the probability of? And Term A, $s/(s+c)$, is a conditional probability of what, given what?
assessment-instructions:: Score out of 100. 50: Term B, 20 for $1-s-c$ as the probability that a single attempt is not decisive (it fails harmlessly), 15 for $(1-s-c)^k$ as the probability that none of the $k$ attempts is decisive, and 15 for Term B as the probability that at least one attempt is decisive. 50: Term A, 25 for the probability that an attempt ends in a successfully deployed backdoor, and 25 for reading it as conditional on the attempt being decisive, $P(\text{deployed} \mid \text{decisive})$: the chance that a decisive attempt is a win for the red team rather than a catch. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Term B is the probability that at least one of the $k$ attempts is decisive: $1-s-c$ is the probability that an attempt is not decisive, so $(1-s-c)^k$ is the probability that none of the $k$ attempts is. Term A is the conditional probability that an attempt ends with a successfully deployed backdoor given that it is decisive, $P(\text{deployed} \mid \text{decisive})$."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
An important property of this model worth considering is that it assumes every attack has the same probability $c$ of being caught and the same probability $s$ of being successfully deployed: per-attempt odds are fixed, no matter how many attacks the red team makes or which problems it picks.

#### Question: Choice
id:: cfd79a28-d7b1-41af-b5ec-e987c5217904
content:: To maximize their probability of winning at least once over the deployment, how often should the red team attack given the above model?
options::
- Once
- [x] As often as possible
- It makes no difference how often it attacks
- At an interior optimal rate, as under upfront auditing
shuffle:: true
feedback-instructions:: With per-attempt odds held fixed, Term A does not depend on $k$ at all and Term B rises monotonically in $k$, so attacking more is always weakly better and the model says to attack as often as possible. If the learner picked the interior optimum, say that this is the right answer for the real game but not for this model, and that the gap between the two is exactly what the next few paragraphs are about. Two to four sentences, no unrelated detail.

#### Widget
source:: [[../widgets/xlab-control-deployment-race]]

#### Text
content::
With fixed odds the curve only climbs. Now finish the reconstruction and feed in the deployment the paper actually ran. Its red team submits a backdoor on about twenty of the 5,000 problems, and twenty attempts is already deep in the plateau, where Term B has all but saturated. So $P(\text{red wins})$ sits near its ceiling, the probability of a decisive attack attempt being successfully deployed, $s/(s+c) \approx 35\%$. That is a safety of roughly 65%: the paper's headline number, rebuilt from the contingency table and a single line of algebra. (The few points between 65% and the measured 62% are the paper's sampling correction and its shutdown-on-statistics rule, real, but not where the mechanism lives.)

The number checks out. But the model implies more than a number, it implies a strategy. Put that prediction to the test.

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 0dea4f20-4db7-4cb4-a48e-dccccb8409f8
content:: Is the optimal strategy predicted by the model reflected in how the paper's red team actually behaved? How did the red team actually attack?
assessment-instructions:: Score out of 100. 40: the verdict: no, the model says to attack as often as possible and the paper's red team did not. 60: how the red team actually attacked: the red team attacks rarely and selectively, only on a small share of the problems and only when there is a good opportunity. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "No. The model says every extra attack only helps, so the red team should backdoor almost every problem. But the paper's red team inserts a backdoor "only when there is a good opportunity to do so"."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 21ca9565-90da-41c8-8a1a-9ec145e4a080
content:: What about this model causes the discrepancy: why does the model predict constant attacking when the paper's red team attacks rarely?
assessment-instructions:: Score out of 100. 50: the cause: the model gives every attack the same odds of being caught and of getting through, however many attacks are made and on whichever problems, while in reality the odds differ from problem to problem (some problems give a backdoor good cover, others do not). 20: why fixed odds predict constant attacking: an extra attack is then as good as the first, so more attempts can only help. 30: why varying odds favour rare attacks: attacking more often means also attacking where the odds are bad, so the red team does better attacking only where a backdoor has good cover. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The assumption that every attack carries the same odds — the same catch probability $c$ and deployment probability $s$ — no matter how many attacks are made or which problems they target. Under fixed odds an extra attack is always as good as the first, so more is always better. But the attacks are not interchangeable: the red team can only attack more often by taking on problems where a backdoor has less natural cover, and those are easier for the monitor to catch. Once attacking more raises the catch probability, the odds are no longer fixed — and constant attacking stops being optimal."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
Attacking more only improves the red team's win probability if every attack is as good as the last, and the paper's red team knew that this was not the case. Compared to upfront auditing, trusted monitoring forces the red team to use much sneakier attacks. Under upfront auditing only the first stretch of solutions is ever audited, so the red team is not incentivized to obfuscate their backdoors, as human audited attacks are detected with close to perfect accuracy regardless of how sneaky the attack is. Under trusted monitoring every solution is scored for suspiciousness, and more obvious attacks are much more likely to get caught.

Thus the red team's best strategy involves obfuscating their attacks to avoid being caught by the monitor.

#### Question: Open
id:: 07cb7a03-7e36-4224-96a2-b73d05d9b1d7
content:: The red team wants its attack attempts to draw less suspicion from the monitor. What decision factors do they have for making their attacks subtler? Name at least two, and think about what each one costs.
assessment-instructions:: Score out of 100. 50: selectivity, 25 for attacking only when there is a good opportunity (problems whose complexity gives a backdoor natural cover), and 25 for its cost: fewer attacks, so the deployment may end before any attempt is decisive. 50: obfuscation, 25 for actively working to make the backdoor subtler, closer to normal code, and 25 for its cost: subtler backdoors are more often simply broken, so they fail instead of deploying. Another genuine way to draw less suspicion, with its real cost, earns the same credit as one of these. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Two decision factors. Selectivity: attack only when there seems to be a good opportunity, on problems whose complexity gives a backdoor natural cover; the cost is a lower attack rate, so a decisive attempt may never occur. Obfuscation effort: actively work to make the backdoor subtler; the cost is that subtler backdoors are more often simply broken, so they fail rather than deploy."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
One way is to attack only "when there seems to be a good opportunity," selectively choosing attack opportunities where attacks are inherently more sneaky. For example, a problem with complex corner cases offers more inherent subtlety and is thus a better opportunity for a backdoor than a one-line string echo, which offers almost no inherent subtlety. The red team's selectivity is captured by an **opportunity cutoff**: the minimum opportunity level at which it is willing to attack. A high cutoff means attacking rarely, only when the opportunity is excellent (a low probability of getting caught). Conversely, decreasing the opportunity cutoff increases the attack rate at the cost of adding attack attempts with worse odds.

Another way to do this is to actively work to obfuscate the attacks and make them more subtle, at the cost of making broken deployed attacks more probable.

These are both decision factors the red team can control for their strategy.

In our model for $P(\text{red wins})$, there is no longer a single $s$ and $c$. Each attempt's odds are set by two things: the problem's inherent opportunity $g$, drawn problem by problem and selected through the opportunity cutoff $g^*$, and the obfuscation effort $\sigma$ from the red team to make the attack more subtle. Write $s(g, \sigma)$ and $c(g, \sigma)$ for the success and catch probability of an attempted attack on a problem of opportunity $g$ at effort $\sigma$. Then $s$ and $c$ become the average odds across the attempts the red team actually makes:

$$s = \mathbb{E}\!\left[\,s(g, \sigma) \mid g > g^*\,\right] \qquad c = \mathbb{E}\!\left[\,c(g, \sigma) \mid g > g^*\,\right]$$

This works because each problem's opportunity is an independent draw, and the red team decides whether to attack through the opportunity cutoff threshold. So each attempt's success and catch probabilities are independent draws from the pool of attacks above the cutoff. Thus the probability that the first decisive attack attempt is a successful one is given by the expected (average) success and catch probabilities. From here on, read every $s$ and $c$ as average odds.

#### Question: Open
id:: e4b67e8c-ce17-4b65-98ca-7d0cff202f0e
content:: Suppose the red team lowers its opportunity cutoff. With $s$ and $c$ read as the average odds of its attempts, what happens to each term of $P(\text{red wins}) = \frac{s}{s + c} \cdot \left(1 - (1 - s - c)^k\right)$, and to the red team's overall win probability?
assessment-instructions:: Score out of 100. 25: Term B rises, because more attempts make it more likely that some attempt is decisive. 35: Term A falls, 20 for why: the added attempts come from worse opportunities where backdoors are more visible, so the average $c$ rises and the average $s$ falls, and 15 for the effect: $s/(s+c)$, the chance that a decisive attempt is a successful deployment, drops. 40: the overall effect, 20 for seeing that the two terms pull in opposite directions, and 20 for the shape: from a high cutoff, lowering it helps at first while the Term B gain dominates, then hurts once the Term A loss takes over, so the win probability is hump-shaped with a best attack rate that is low but not zero. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Term B rises, because more attack attempts make it more likely that some decisive attempt occurs. But the added attempts are drawn from worse opportunities, where backdoors are inherently more visible, so the average $c$ rises and the average $s$ falls, and Term A, the probability that a decisive attempt is successfully deployed, drops. Near the rare end the Term B gain dominates and the win probability climbs; past some point the Term A decay takes over and it falls. The curve is hump-shaped and the red team's best attack rate is low but non-zero."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Callout: Practice: put numbers on it
tone:: amber

#### Question: Open
id:: e998048d-d7f1-4cda-a819-b1bbd3d23dca
content:: A red team is choosing between two strategies against a protocol. Rare: attack on the 4 best opportunities, where each attempt is caught with probability $c = 0.05$ and deploys successfully with probability $s = 0.10$. Frequent: attack on 60 problems, where the average attempt has $c = 0.12$ and $s = 0.03$.

Compute $P(\text{red wins})$ for each strategy, say which one the red team prefers, and say which of the two terms holds each strategy back.
placeholder:: Show both calculations
assessment-instructions:: Score out of 100. 25: the rare strategy: Term A $0.10/0.15 \approx 0.67$, Term B $1 - 0.85^4 \approx 0.48$, so $P(\text{red wins}) \approx 0.32$. 25: the frequent strategy: Term A $0.03/0.15 = 0.2$, Term B $1 - 0.85^{60} \approx 1$, so $P(\text{red wins}) \approx 0.20$. 10: the red team prefers the rare strategy. 40: what holds each back, 20 each: the rare strategy is limited by Term B (with only four attempts, about half the time none is decisive before the deployment ends), and the frequent strategy by Term A (a decisive attempt is nearly certain, but it is a successful deployment only about one time in five). Accept numbers within about 0.02; an arithmetic slip carried forward loses credit only once. Cap at 30 if the answer adds up the chances of separate attempts instead of using the formula. Model answer, for the feedback, not a grading checklist: "Rare: Term A is $0.10/0.15 \approx 0.67$ and Term B is $1 - 0.85^4 \approx 0.48$, so $P(\text{red wins}) \approx 0.32$. Frequent: Term A is $0.03/0.15 = 0.2$ and Term B is $1 - 0.85^{60} \approx 1$, so $P(\text{red wins}) \approx 0.20$. The red team prefers the rare strategy. The rare strategy is held back by Term B: with only four attempts, about half the time none of them is decisive before the deployment ends. The frequent strategy is held back by Term A: nearly certain to produce a decisive attempt, but the worse odds make that attempt a successful deployment only one time in five."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
At high opportunity cutoffs, attack attempts are so rare that the deployment usually ends before an attack attempt is decisive and Term B, $1 - (1 - s - c)^k$, is very small. At the lower opportunity cutoffs, attempts are very frequent but increasingly drawn from problems with poor inherent subtlety, so the average catch rate climbs and Term A, $s/(s+c)$, becomes smaller. In between sits an interior optimum at a low but non-zero attack rate, which is why the paper's red team attacks on only a small fraction of problems. On the attack-rate curve in the widget below, obfuscation effort is held at a fixed level.

As aforementioned, the red team's other decision factor is obfuscation effort. Every attack opportunity affords some inherent subtlety, and efforts to make an attack more subtle will come at the cost of the attack's deployment success probability.

Raising $\sigma$ does two things to every attack attempt: it lowers the catch probability $c$, and it lowers the reliability of the attack, the probability the attack is not broken, $p_{\text{works}}(\sigma)$. The subtlety curve plots $P(\text{red wins})$ as a function of $\sigma$.

Given these decision factors and some priors about the blue team's strategy, the best strategy is to attack rarely, only on the very best opportunities (about 0.2% of problems), with moderate obfuscation effort. The strategy plane plots the red team's win probability over the whole strategy space and marks that best response with a ring.

All three live on the **Red team** tab of the widget below: the strategy plane first, then the attack-rate curve and the subtlety curve, each cut through the best response. The **Protocol** tab is the one you will come back to in part 3, when the paper reaches defer to trusted.

#### Callout: Predict
tone:: amber

#### Question: Choice
id:: 9a2cedcb-e428-47b1-b352-8623a22b51bf
content:: The red team's other decision factor is obfuscation effort $\sigma$. A more obfuscated backdoor reads as more normal code, so the monitor catches it less often, but it is also more likely to be simply broken. As $\sigma$ rises from blatant to maximally subtle, the red team's best achievable win probability:
options::
- Rises monotonically
- Is unaffected by obfuscation effort
- [x] Rises to an interior peak, then falls
- Falls monotonically
shuffle:: true
feedback-instructions:: Obfuscation buys a lower catch probability and pays for it with a lower chance that the backdoor works at all, so the win probability climbs while the first effect dominates and falls once the second does. Name whichever of the two effects the learner's choice ignored. Two to four sentences, no unrelated detail.

#### Question: Open
id:: d4a4c872-4e4f-4638-9b3b-2387ce4a2f7d
content:: Suppose the red team decreases its obfuscation effort. With $s$ and $c$ read as the average odds of its attempts, what happens to each term of $P(\text{red wins}) = \frac{s}{s + c} \cdot \left(1 - (1 - s - c)^k\right)$, and to the red team's overall win probability?
assessment-instructions:: Score out of 100. 20: the catch probability $c$ rises, because blatant backdoors are easier for the monitor to flag. 20: the backdoors become more reliable ($p_{\text{works}}$ rises), because fewer of them are broken. 20: Term B rises: with more attempts caught and fewer broken, fewer attempts fail harmlessly, so $s + c$ rises and a decisive attempt becomes more likely. 20: Term A is pulled two ways, down by the higher catch probability and up by the higher reliability, so its direction depends on which effect is stronger. 20: overall: the win probability has an interior optimum in obfuscation effort, so lowering effort helps the red team only if it was over-obfuscating, and from its best response any decrease lowers its win probability. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Lowering obfuscation raises the catch probability $c$, since blatant backdoors are easier for the monitor to flag, and raises the reliability $p_{\text{works}}(\sigma)$, since fewer backdoors are broken. Term B rises: fewer attempts fail harmlessly, so $s + c$ goes up and a decisive attempt becomes more likely. Term A, $s/(s+c)$, is pulled down by the higher catch rate and up by the higher reliability, so its direction depends on which effect is stronger. Overall the win probability has an interior optimum in $\sigma$: from the red team's best obfuscation level, lowering effort lowers its win probability; it helps only if the red team was over-obfuscating to begin with."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Widget
source:: [[../widgets/xlab-control-game]]

#### Text
content::
:::callout {title="How the model is built" tone="neutral" collapse="closed"}
A model built for intuition, not a re-run of the paper's experiments. Opportunity quality is drawn from a Beta(2,5), a subtler backdoor is caught less often but is more often simply broken, and usefulness is charged as the share of problems handed to the weaker model.
:::

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 4a5d6167-c916-4b75-abc5-ce41909fccb5
content:: If the red team knew that the blue team was using trusted monitoring, but was unaware of the audit budget, what would that mean for the effectiveness of its strategy?
assessment-instructions:: Score out of 100. 40: the best response is the strategy that maximises the red team's win probability against one specific protocol, and the audit budget is part of that protocol (it sets how many attacks get audited), so without knowing it the red team can only guess from its priors. 60: the consequence, 40 for: its strategy will generally differ from the best response and so win less often, and 20 for: it can at best do equally well, if its guess happens to land on the best response. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The best response is the maximum of the red team's win probability against one specific protocol, so a red team with wrong or vague priors will generally play some other strategy, which by definition wins less or just as often as the best response."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 567a29cb-042e-488e-89c0-d8960ab90f8d
content:: Is it better for the red team to be aware that the blue team is using trusted monitoring, or unaware that the blue team is using trusted monitoring? For each case, list the benefits and drawbacks.
assessment-instructions:: Score out of 100. 30: benefits of being aware: the red team can tailor its attacks to the monitor it actually faces (for example when to attack, how subtle to be, or exploiting how the protocol works), so it plays close to its best response. 30: drawbacks of being unaware: it cannot tailor its strategy and generally plays far from the best response, for example attacking blatantly into a monitor that catches it. 20: deterrence, the other side: a red team that knows it faces a strong protocol may rationally attack very little or not at all, while an unaware red team still attempts attacks. 20: a verdict that weighs the two sides, for example that awareness mostly helps the red team. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mostly, awareness helps the red team: knowing the protocol lets it play its best response, tuning its opportunity cutoff and obfuscation effort to the monitor it actually faces, and knowing the protocol's mechanics can make targeted obfuscation or exploitation easier. Unaware, the red team cannot tailor its strategy, so it will generally play far from the best response, for example attacking blatantly into a monitor that catches it. Awareness can also function as deterrence. If the blue team's protocol is powerful (like Ctrl-Z, a later control protocol), a red team that knows this may rationally attack very little or not at all, so exposing a strong protocol can itself deter attacks, while hiding it invites attempts the protocol then catches."
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson continues: section 3, the baseline protocols and trusted monitoring.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::

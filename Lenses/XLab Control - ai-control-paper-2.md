---
id: 'c1762189-2f77-4824-a206-dec8dbb27b51'
title: "The AI control paper (2): upfront auditing, trusted monitoring and the fixed-odds model"
tldr: "Audit the first 2% of GPT-4's code and a patient red team still wins 85% of the time, by attacking rarely. Let GPT-3.5 score every solution for suspicion and audit the worst 2% instead, and safety jumps to 62%. This part reads those results and rebuilds the 62% from the paper's own table with one line of algebra, which then predicts a strategy the paper's red team did not play."
summary_for_tutor: "Part 2 of 6 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (1)', which set up the APPS backdooring game and its vocabulary (U, T, H, protocol, backdoor, safety, usefulness, red and blue team). This part covers section 3's opening, the baselines of 3.1 and the main text of 3.2, trusted monitoring. Headline results: don't use untrusted models, safety 100% / usefulness 2%; upfront auditing 15% / 100%; trusted monitoring 62% / 97%. This lesson adds a derivation layer the paper does not have: the optimal upfront-auditing attack rate, in a five-part pen-and-paper derivation marked optional, and a decomposition of the red team's win probability into Term A, s/(s+c), the chance a decisive attempt is a deployed backdoor, and Term B, 1-(1-s-c)^k, the chance any attempt is decisive, with s = 13/71 and c = 24/71 from the paper's own contingency table; at about twenty attempts Term B has saturated and the model rebuilds the paper's safety, about 65% against the measured 62%. The fixed-odds model predicts constant attacking, while the paper's red team attacked on 71 of 1,500 problems; this part ends on that discrepancy and its cause (every attack is assumed to carry the same odds). The next part, 'The AI control paper (3)', resolves it through the red team's two decision factors, the opportunity cutoff and obfuscation effort; if the learner asks how the red team should really attack, point them forward rather than previewing the hump-shaped curves. Two widgets: the upfront-auditing tradeoff (Figure 3 made live) and the deployment race. Figure 3's numbers are in the lead-in above the upfront-auditing widget, and the three-outcome split and the odds are stated in the Text segment above the deployment race. The revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer."
reading_minutes: 20
tutor_minutes: 27
tags: []
---
#### Text
content::
This is part 2 of 6 of the founding AI control paper. Part 1 set up the game: the untrusted model $U$, the trusted model $T$, the scarce trusted labour $H$, and what counts as a backdoor. This part reads the results for the simplest protocols, upfront auditing and trusted monitoring, and rebuilds trusted monitoring's 62% safety from the paper's own numbers with a simple model of the red team's attacks; the next part works out the red team's best strategy against it. The five-part derivation near the start is optional pen-and-paper work and adds about 30 minutes.

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: ## 3 Results
to:: In our main results, we use an auditing proportion of 2%.

#### Text
content::
:::callout {title="Optimal audit tradeoff" tone="neutral"}
The paper states it "can analytically solve" this problem, and it is in fact a tractable derivation. The five-part exercise below works through it by hand, one step at a time: set up the red team's win probability as a function of its attack rate $p$, use the same rare-event approximation that shows up all over this field to make it differentiable, and solve for the optimal $p^*$. You may need a pen and paper.
:::

#### Callout: Optional: the optimal attack rate, worked by hand
tone:: amber
collapse:: closed

#### Question: Open
id:: 1271edad-5d2c-456d-8757-a1e70093bcd9
content:: The protocol audits the first $A = \alpha N$ of the $N$ submissions. On each problem, independently, the attack policy inserts an obvious backdoor with probability $p$. An audit detects a backdoor attempt whether or not that attempt would have produced a working exploit.

Raising $p$ helps the red team in one way and hurts it in another. Name both, and say why together the win probability is not monotonically increasing in $p$.
optional:: true
assessment-instructions:: Score out of 100. 40: how raising $p$ helps: more attempts make it more likely that a backdoor gets through and wins. 40: how raising $p$ hurts: more attempts make it more likely that one is caught, which ends the game. 20: the conclusion: both effects grow with $p$ and pull in opposite directions, so the win probability rises and then falls instead of rising all the way. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Increasing $p$ has two opposing effects. It raises the probability that at least one attempt falls in the unaudited window (favorable to the red team), but it also raises the probability that some attempt falls in the audited window, which ends the game (unfavorable). Both effects scale with $p$, so the win probability is not monotonic in $p$."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: e53b2fe5-70c1-4be2-8bcf-7769721f3d00
content:: A GPT-4 solution is correct with probability $0.53$. A backdoor attempt yields a working exploit only if the underlying solution is correct; an unsuccessful attempt is still detectable by an audit but never wins the game for the red team. Let $B = (1-\alpha)N$ be the number of unaudited submissions.

The red team wins if and only if (i) no attempt falls in the audited window, and (ii) at least one working backdoor falls in the unaudited window. State the probability of each condition and derive $RW(p)$, the red team's win probability.
optional:: true
assessment-instructions:: Score out of 100. 30: condition (i): each audited problem is free of an attempt with probability $1-p$, independently, so no attempt in any of the $A$ audited problems has probability $(1-p)^A$. 40: condition (ii), 20 each: a given unaudited problem yields a working backdoor with probability $0.53p$ (an attempt is made and the underlying solution is correct), and the probability that at least one of the $B$ unaudited problems does so is $1 - (1 - 0.53p)^B$. 30: combining them, 20 for $RW(p) = (1-p)^A [1 - (1 - 0.53p)^B]$ and 10 for why it is a product: the two windows are separate problems with independent draws. Give credit for each point whenever the answer shows the idea, in any wording or notation; an error carried forward from an earlier step loses credit only once. Model answer, for the feedback, not a grading checklist: "Condition (i): each audited problem avoids an attempt with probability $(1-p)$, independently, so across all $A$ audited problems the probability is $(1-p)^A$. Condition (ii): a given unaudited problem yields a working backdoor when an attempt occurs (probability $p$) and the underlying solution is correct (probability $0.53$), i.e. with probability $0.53p$, and fails to with probability $(1 - 0.53p)$. Across all $B$ unaudited problems, the probability that at least one succeeds is $1 - (1 - 0.53p)^B$. The two conditions are independent, so: $$RW(p) = (1-p)^A \left[1 - (1 - 0.53p)^B\right]$$"
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 76ede009-5846-423b-98f7-2688c935758e
content:: Given $RW(p) = (1-p)^A \left[1 - (1 - 0.53p)^B\right]$, and assuming the optimum satisfies $p \ll 1$, apply the approximation $(1-x)^k \approx e^{-xk}$. Maximize $RW(p)$ over $p$: take the logarithm where useful, solve $\frac{d(RW)}{dp} = 0$, and give a closed form for the optimizer $p^*$.
optional:: true
assessment-instructions:: Score out of 100. 25: applying the approximation to both factors, giving $RW(p) \approx e^{-pA} - e^{-p(A + 0.53B)}$. 25: setting the derivative to zero, giving $A e^{-pA} = (A + 0.53B) e^{-p(A + 0.53B)}$. 20: taking logarithms and rearranging to $0.53Bp = \ln(1 + 0.53B/A)$. 30: the closed form $p^* \approx \ln(1 + 0.53B/A) / (0.53B)$. Give credit for each step whenever the answer shows it, in any equivalent form or notation; an error carried forward from an earlier step loses credit only once. Model answer, for the feedback, not a grading checklist: "Applying $(1-p)^A \approx e^{-pA}$ and $(1-0.53p)^B \approx e^{-0.53pB}$ gives $RW(p) \approx e^{-pA} - e^{-p(A + 0.53B)}$. Setting the derivative to zero yields $A\,e^{-pA} = (A + 0.53B)\,e^{-p(A + 0.53B)}$. Taking logarithms: $\ln A - pA = \ln(A + 0.53B) - p(A + 0.53B)$, which rearranges to $0.53Bp = \ln\!\left(1 + \frac{0.53B}{A}\right)$, hence: $$p^* \approx \frac{\ln\!\left(1 + \frac{0.53B}{A}\right)}{0.53B}$$ With $A = \alpha N$ and $B = (1-\alpha)N$, the ratio $0.53B/A = 0.53(1-\alpha)/\alpha$ is independent of $N$; $N$ enters only as a $1/N$ scale factor in the denominator. Hence $p^* N$ depends on $\alpha$ but not on $N$, which is the scale invariance the paper notes."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 8d148ee4-bd47-428b-bee4-fff816b9f7a5
content:: Set $N = 5000$. For $\alpha \in \{0.005,\ 0.02,\ 0.10,\ 0.30\}$, evaluate (a) the optimizer $p^*$, (b) the expected number of backdoor attempts $p^* N$, and (c) the blue-team win probability $1 - RW(p^*)$. Compare the $\alpha = 0.02$ result against the paper's stated value, "the blue team win probability is 15%".

The widget below computes the same curves, so use it to check yourself once you have your own numbers.
optional:: true
assessment-instructions:: Score out of 100. 80: the values, 20 for each $\alpha$: 10 for $p^*$ together with $p^* N$, and 10 for the blue-team win probability $1 - RW(p^*)$. Reference values: at $\alpha = 0.005$, $p^* \approx 0.177\%$, $p^* N \approx 8.9$, blue-team win about 5%; at $\alpha = 0.02$, $p^* \approx 0.127\%$, $p^* N \approx 6.3$, about 15%; at $\alpha = 0.10$, $p^* \approx 0.073\%$, $p^* N \approx 3.7$, about 43%; at $\alpha = 0.30$, $p^* \approx 0.043\%$, $p^* N \approx 2.2$, about 71%. Accept rounding differences and win probabilities within about two percentage points; an error carried forward from an earlier value loses credit only once. 20: the explicit comparison at $\alpha = 0.02$: about 15%, matching the paper's stated value. Model answer, for the feedback, not a grading checklist: "With $p^* \approx \dfrac{\ln\!\left(1 + 0.53(1-\alpha)/\alpha\right)}{0.53(1-\alpha)\cdot 5000}$ and $1 - RW(p^*) = 1 - (1-p^*)^A\left[1 - (1 - 0.53p^*)^B\right]$: $\alpha = 0.005$: $p^* \approx 0.177\%$; $p^* N \approx 8.9$; blue-team win $\approx 5\%$. $\alpha = 0.02$: $p^* \approx 0.127\%$; $p^* N \approx 6.3$; blue-team win $\approx 15\%$, consistent with the stated value. $\alpha = 0.10$: $p^* \approx 0.073\%$; $p^* N \approx 3.7$; blue-team win $\approx 43\%$. $\alpha = 0.30$: $p^* \approx 0.043\%$; $p^* N \approx 2.2$; blue-team win $\approx 71\%$."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: b3d734c1-d50f-4215-9989-8027736a8e0f
content:: From the values above, the blue-team win probability increases by a larger amount from $\alpha = 0.005$ to $0.02$ than from $\alpha = 0.10$ to $0.30$, and the expected-attempts column decreases with diminishing magnitude as $\alpha$ increases. Account for both effects in terms of the dependence of $p^*$ on $\alpha$. State whether the diminishing returns arise from the auditing mechanism itself or from the red team's optimization.
optional:: true
assessment-instructions:: Score out of 100. 30: both effects come from $p^*$ falling as $\alpha$ rises: a larger audited window makes each attempt riskier, so the optimising red team attacks less. 30: why the effect shrinks, 15 each: from $\alpha = 0.005$ to $0.02$ the red team has to cut $p^*$ a lot, so the blue team gains a lot, while from $0.10$ to $0.30$ $p^*$ is already low and barely moves; and the expected attempts $p^* N$ fall in the same shrinking steps because the same $p^*$ drives them. 40: the verdict: the diminishing returns come from the red team's optimisation (its attack rate adapting downward), not from the auditing mechanism itself. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Both effects follow from $p^*$ decreasing in $\alpha$: a larger audited window raises the per-attempt detection risk, so the optimizing red team reduces its attack rate. From $\alpha = 0.005$ to $0.02$ this forces a large reduction in $p^*$, which produces a large gain in blue-team win probability. From $\alpha = 0.10$ to $0.30$, $p^*$ is already near its lower range, so further increases in $\alpha$ change it little and the win probability changes little. The same declining $p^*$ drives the expected-attempts column ($p^* N$) down with diminishing magnitude. The diminishing returns arise from the red team's optimization, not from the auditing mechanism."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

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
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

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
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
Let the red team make $k$ attack attempts, let $s = P(\text{successful deployment})$ be the probability of a successful deployment, and let $c = P(\text{caught})$ be the probability of an attack being caught. Then we can model the red team's probability of winning at least once as

$$P(\text{red wins}) = \underbrace{\frac{s}{s + c}}_{\text{Term A}} \cdot \underbrace{\left(1 - (1 - s - c)^k\right)}_{\text{Term B}}$$

#### Question: Open
id:: 00752543-e754-4986-afaf-f68c441c24b3
content:: Before reading on, interpret the formula's two terms in your own words. What event is Term B, $1 - (1-s-c)^k$, the probability of? And Term A, $s/(s+c)$, is a conditional probability of what, given what?
assessment-instructions:: Score out of 100. 50: Term B is the probability that at least one of the $k$ attempts is decisive (caught or successfully deployed), that is, that the game is settled within the $k$ attempts. 50: Term A, 25 for the probability that an attempt ends in a successfully deployed backdoor, and 25 for reading it as conditional on the attempt being decisive, $P(\text{deployed} \mid \text{decisive})$: the chance that a decisive attempt is a win for the red team rather than a catch. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Term B is the probability that at least one of the $k$ attempts is decisive. Term A is the conditional probability that an attempt ends with a successfully deployed backdoor given that it is decisive, $P(\text{deployed} \mid \text{decisive})$."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner did not already say it, add as something worth knowing (not a lost point) why Term B has its form: $1-s-c$ is the probability that one attempt is not decisive, so $(1-s-c)^k$ is the probability that none of the $k$ attempts is. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

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
feedback-instructions:: With per-attempt odds held fixed, Term A does not depend on $k$ at all and Term B rises monotonically in $k$, so attacking more is always weakly better and the model says to attack as often as possible. If the learner picked the interior optimum, say that this is the right answer for the real game but not for this model, and that the gap between the two is exactly what the rest of this part, and the next one, are about. Two to four sentences, no unrelated detail.

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
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: 21ca9565-90da-41c8-8a1a-9ec145e4a080
content:: What about this model causes the discrepancy: why does the model predict constant attacking when the paper's red team attacks rarely?
assessment-instructions:: Score out of 100. 70: the cause: the model gives every attack the same odds of being caught and of getting through, however many attacks are made and on whichever problems, while in reality the odds differ from problem to problem (some problems give a backdoor good cover, others do not). 30: why fixed odds predict constant attacking: an extra attack is then as good as the first, so more attempts can only help. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The assumption that every attack carries the same odds, the same catch probability $c$ and deployment probability $s$, no matter how many attacks are made or which problems they target, while real problems differ in how much cover they give a backdoor. Under fixed odds an extra attack is always as good as the first, so more is always better."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Then add, as something worth knowing rather than a lost point, that attacking more often means also attacking on problems where a backdoor has little cover and is easier to catch, which is why rare attacking can do better; the next part works this out. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson continues: section 3's opening, the baselines of 3.1 and trusted monitoring in 3.2.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::

---
id: 'b8716071-249e-46fd-9b6f-5afd2dff720c'
title: "The AI control paper (3): the monitor as a classifier, and deferring to the trusted model"
tldr: "Two monitors with the same AUC can catch 47% and 9% of attacks. When only the most suspicious 2% of code can be audited, what matters is how the monitor does in that thin tail. This part reads the monitor as a classifier, then adds a second lever: let the trusted model rewrite anything moderately suspicious."
summary_for_tutor: "Part 3 of 4 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (2)', which covered upfront auditing, trusted monitoring's 62% safety and the red team's best response (opportunity cutoff and obfuscation effort). This part covers 3.2.1 (qualitative analysis of the monitor), the rest of 3.2 (why trusted monitoring beats upfront auditing, and why U cannot burn the audit budget), 3.2.2 (untrusted justification) and 3.3, defer to trusted and dynamic routing. Headline results: the monitor catches an attempted backdoor with probability 0.338 at a 2% false-positive rate; trusted monitoring with defer to trusted at 10% gives 83% / 93%, at 50% 100% / 51%. Two widgets: the monitor as a noisy classifier (its second tab is the two-monitors-one-AUC comparison), and the control game repeated from part 2 for its Protocol tab, where the learner moves the defer band. The AUC-versus-catch-rate conclusion lives in the Note callout that follows the staged 'same number, different safety' questions rather than inside the monitor widget, where it would hand the learner the answers before they commit. The revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer."
reading_minutes: 40
tutor_minutes: 10
tags: []
---
#### Text
content::
This is part 3 of 4 of the founding AI control paper. Part 2 showed trusted monitoring lifting safety from 15% to 62% and worked out the red team's best response to it. This part looks closer at the monitor itself, a noisy classifier that can only send 2% of solutions to an audit, and then reads the paper's first protocol that trades usefulness for safety: deferring to the trusted model.

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: #### 3.2.1 Qualitative Analysis
to:: Various examples of monitoring results for both normal solutions and backdoors can be found in

#### Text
content::
\## The monitor is a binary classifier

The two histograms in Figure 4 are the picture a signal-detection framing makes precise: the monitor is a binary classifier separating backdoored from innocent solutions, and the more its two suspicion-score distributions overlap, the worse it does. The standard summary of that overlap is the ROC curve, true-positive rate against false-positive rate as the decision threshold sweeps, and its AUC (area under the curve). If those terms are unfamiliar, Google's ML Crash Course has a short primer: [ROC and AUC](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc).

The widget below models the monitor as two equal-variance Gaussians and lets you drag its quality, the separation $d'$ between the innocent and backdoored means. Watch the ROC curve and AUC respond, and watch the operating point at the blue team's fixed 2% false-positive threshold: even a fairly good monitor catches only a fraction of backdoors there, which is the "many false negatives" the paper describes. The default setting ($d' \approx 1.64$, AUC $\approx 0.88$) reproduces the paper's reported result, a 0.338 probability that an attempted backdoor is audited at a 2% false-positive rate. Real suspicion scores are not Gaussian; this is an idealization for building intuition, not a fit to the paper's data.

The second tab sets up a comparison you will need in a moment.

#### Widget
source:: [[../widgets/xlab-control-monitor-classifier]]

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 36fecbba-8c07-4a46-b4ef-7fe1ebad3e9a
content:: The contingency table in section 3.2 records how the trusted monitor's audit decisions split across 71 backdoor attempts (successful or failed) and 1,429 innocent submissions. Treat the monitor as a binary classifier: "audit" is its positive prediction, and "is a backdoor attempt" is the positive class.

Compute (a) the false-positive rate $\text{FPR} = P(\text{audit} \mid \text{no attempt})$ and (b) the true-positive rate $\text{TPR} = P(\text{audit} \mid \text{attempt})$. State which single point on the monitor's ROC curve these define, and check them against the values reported in the text.
assessment-instructions:: Reference answer. (a) An innocent submission is audited in 29 of $29 + 1{,}400 = 1{,}429$ cases, so $\text{FPR} = 29/1429 = 0.020$, that is 2.0%. (b) A backdoor attempt totals $19 + 52 = 71$ successful plus failed, of which $6 + 18 = 24$ are audited, so $\text{TPR} = 24/71 = 0.338$. The pair $(0.02, 0.338)$ is one point on the monitor's ROC curve, and both match the text: the threshold is set for a 2% false-positive rate and the probability that an attempted backdoor is audited is 0.338. Full marks require both fractions, the ROC-point statement and the check against the text.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: a9d6bd82-eeaa-4400-8dae-66e6aa022f54
content:: The widget reports an area under the ROC curve of AUC $\approx 0.88$ at the default monitor quality. AUC has a threshold-free interpretation: it equals the probability that the monitor assigns a higher suspicion score to a randomly chosen backdoored solution than to a randomly chosen innocent one.

State what AUC $= 0.88$ says operationally about the monitor, and what AUC values of $0.5$ and $1.0$ would correspond to.
assessment-instructions:: Full marks for: AUC $= 0.88$ means that if you draw one backdoored and one innocent solution at random, there is an 88% chance the monitor scores the backdoored one as more suspicious. AUC $= 0.5$ means the ranking is no better than a coin flip. AUC $= 1.0$ is perfect separation, every backdoor above every innocent solution, so some threshold catches all backdoors with no false positives. This monitor lies between the two, toward the useful end but short of perfect. Deduct if the learner reads AUC as an accuracy or as a catch rate at some particular threshold.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: d08e6529-a9d4-4880-9312-89b99b0354aa
content:: Using the same table, partition the outcome of a single backdoor attempt into three mutually exclusive events from the blue team's perspective: (i) the attempt is audited, so the protocol shuts down and the blue team wins; (ii) the attempt is not audited but is a successful backdoor, so the red team wins; (iii) the attempt is not audited and is a failed backdoor, so it is submitted harmlessly and the game continues.

(a) Give the probability of each event from the table, and verify they sum to 1. (b) Under upfront auditing the audit decision is positional rather than suspicion-based, so an attempt is audited only with the raw budget probability, 2%. Compare the per-attempt probability that the blue team catches an attempt under the two protocols, and explain how this accounts for the safety improvement from 15% to 62%.
assessment-instructions:: Reference answer. (a) Of the 71 attempts: audited, blue wins, $24/71 = 0.338$; not audited and successful, red wins, $13/71 = 0.183$; not audited and failed, game continues, $34/71 = 0.479$. These sum to $24 + 13 + 34 = 71$, so the probabilities sum to 1. On a single attempt the monitor is nearly twice as likely to catch the red team (0.338) as the red team is to land a successful backdoor (0.183). (b) Trusted monitoring audits an attempt with probability 0.338; upfront auditing audits it only with the random budget probability 0.02, about a 17 times lower catch rate. The red team must land at least one successful unaudited backdoor over the whole scenario while surviving every attempt it makes, so raising the per-attempt catch probability from 0.02 to 0.338 sharply raises the chance the blue team shuts down first, which is what moves the blue team's win probability from 15% to 62%. Give credit for noting that the exact figures also depend on the downsampling and the multiple-attempt dynamics, so this per-attempt comparison explains direction and rough magnitude rather than reproducing 62% precisely.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Note" tone="neutral"}
You may be tempted to summarize a monitor with its AUC, as it is a threshold-free number for how well a monitor separates backdoored and innocent solutions. However, as you will see, it is a poor predictor of safety.
:::

#### Callout: Same number, different safety
tone:: amber

#### Text
content::
Three stages: two monitor comparisons that come out backwards, then the arithmetic that explains both. Use the second tab of the widget above, and commit to an answer before you move the sliders.

#### Question: Open
id:: b1e9f906-6e8c-4270-be8f-c4804e4af47c
content:: **Stage 1: two monitors, one AUC.** Two idealized monitors, A and B, drawn from the same model. The area under each ROC curve is identical: both have AUC 0.92. Your protocol audits the most suspicious 2% of all solutions.

Compared to Monitor A, how many of the attacks does Monitor B catch: more, about the same, somewhat fewer, or far fewer? Commit to a direction and a rough magnitude, and note which part of the figure you used to decide.
assessment-instructions:: The correct answer is far fewer, less than half as many: at this calibration Monitor A catches about 47% of attacks and Monitor B about 9%. Full marks require the direction (fewer), a magnitude at least as strong as "less than half", and a reason that points at the low-false-positive tail of the ROC curve or at the tight spread of B's attack scores rather than at the enclosed area. Award partial credit for the right direction with a weak magnitude.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 829a8e28-a020-4f50-9dbd-1f456bb27df1
content:: **Stage 2: surely 0.97 beats 0.92?** Monitor B is now upgraded into a strictly stronger classifier: its AUC rises to 0.97, while A stays at 0.92. The audit budget is unchanged.

Which monitor catches more attacks now? Commit to a direction and a rough magnitude, and note which part of the figure you used to decide.
assessment-instructions:: The correct answer is that they tie. At the 2% operating point both catch about 47% of attacks (47.3% against 47.2%, from the same calibrated model), so a five-point AUC advantage does not buy Monitor B more safety in this case. Full marks for "a tie, or near enough" plus a reason that identifies the operating point at 2% false positives as what matters. Give partial credit for "B still does not clearly win". Mark down confident answers that B now wins by a wide margin.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: 742e9078-3ca5-441c-b48a-15baacd5c1b9
content:: **Stage 3a: where does the audit budget actually go?** Both surprises trace back to three numbers: $N = 5{,}000$ outputs, a 2% audit budget, and an attack frequency around 0.1%, a handful of attempts, on the order of what you derived in the Figure 3 exercises in part 2.

How many attacks should you expect $U$ to make over the whole deployment given a monitor with AUC $= 1.0$? Thus given any monitor, what is consuming the majority of the audit budget, and by how much? Do the arithmetic.
assessment-instructions:: Reference answer. Expected attacks: $0.1\% \times 5{,}000 = 5$. Audit budget: $2\% \times 5{,}000 = 100$ audits. So even if the monitor flagged every single attack, at least 95 of the 100 audits land on innocent code: the audit budget is consumed almost entirely by false positives, 95 of 100. Full marks require both arithmetic steps and the conclusion stated with the numbers.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### Question: Open
id:: bab73b2d-907f-469b-a161-aed96554123b
content:: **Stage 3b: the metric that actually predicts safety.** What single metric best predicts a monitor's safety under a 2% audit budget? Why can AUC, a good measure of classifier strength, be misleading about safety?
assessment-instructions:: The correct metric is the true-positive rate at a false-positive rate equal to the audit budget, that is TPR at 2% FPR. Reasoning for full marks: an audit budget of 2% introduces a threshold essentially at FPR = 2%, and since attacks are rare enough that true positives consume a negligible share of the audits, auditing the most suspicious 2% of all solutions is effectively auditing the most suspicious 2% of innocent solutions. AUC is independent of every threshold, so it does not necessarily represent the monitor's performance at any specific threshold; in particular, increasing a monitor's TPR at FPR above 2% improves its AUC without necessarily increasing the catch rate, and therefore the safety, in this context. Half marks for naming the metric without the threshold argument.
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. Do not mention scores. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
:::callout {title="Note" tone="neutral"}
The widget above builds exactly this comparison from the model. At the default AUC of 0.92 the two monitors catch wildly different fractions, roughly 47% against 9%, even though their ROC curves enclose identical area. The gap survives across various AUCs. The operating point moves with the budget: a larger audit budget sets the threshold at a higher false-positive rate, where a different monitor may lead.
:::

#### Article
from:: Trusted monitoring performs better than upfront auditing for two reasons:
to:: This means that trusted monitoring would be useful even if $U$ is able to perfectly predict trusted monitoring predictions.

#### Question: Open
id:: 0b4f91f9-f6e7-4227-9bcc-c12c4df33091
content:: How does the blue team stop $U$ from burning the audit budget by making innocent code look suspicious?
assessment-instructions:: Full marks for: the blue team knows the distribution of suspicion scores that the real model's code gets, so the protocol shuts down if $U$'s submissions look significantly more suspicious than that expected distribution. Credit the link back to the summary-statistics assumption of section 2.3. Deduct for answers that propose a fix the paper does not use, such as rate-limiting audits.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Article
from:: #### 3.2.2 Extending Trusted Monitoring With Untrusted Justification
to:: Defer to trusted is an example of a more general design pattern which we call dynamic routing, where a protocol uses some heuristic to route between multiple possible strategies for responding to queries.

#### Callout: Quick recall
tone:: blue

#### Question: Open
id:: 2d6138bc-8f06-4c06-af51-3450519778e2
content:: In defer to trusted, what does the protocol do with code whose suspicion score is elevated but below the audit threshold?
assessment-instructions:: Full marks for: it discards $U$'s code and submits a solution written by $T$ instead. Deduct if the learner says the code is audited (it is not, that is the band above) or that it is submitted as written.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Question: Open
id:: d561aa2c-f9d4-407c-a009-666a82021a58
content:: What is dynamic routing?
assessment-instructions:: Full marks for: a protocol design pattern where some heuristic decides, query by query, which of several response strategies to use. Defer to trusted is an example, with the suspicion score routing each problem to "submit $U$'s code", "submit $T$'s code" or "audit". Half marks for the definition without an instance.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### End Callout

#### Text
content::
\## Defer to trusted, mechanistically

Trusted monitoring spends its whole audit budget on the most suspicious 2% and deploys everything else as $U$ wrote it. But moderately suspicious code is too suspicious to be comfortable with, yet not suspicious enough to be worth a human audit. Deferring to the solutions of trusted models is a way to address this issue, at the cost of some deployment effectiveness. Any code whose suspicion falls in a band just below the audit threshold is not deployed and not audited; instead $T$ rewrites the solution from scratch, and its version is deployed. The price is paid in usefulness: roughly the share of solutions rewritten, almost all of them innocent, times how much worse $T$ is than $U$ at the task.

#### Question: Open
id:: b7c5eae3-0620-4ea4-86dd-584bc3cb0e17
content:: What does increasing the number of solutions where we defer to $T$ do to the probability of an attack attempt being caught and being successfully deployed? What does it do to the probability of a decisive attack attempt occurring?
assessment-instructions:: Full marks for the chain. Deferring makes successful attacks less probable because it rewrites moderately suspicious solutions from scratch. And because $T$ rewrites those solutions from scratch, the red team's best response is to make its attacks subtler to duck the band, which also decreases the probability of an attack attempt being caught. With both probabilities falling, a decisive attack attempt becomes less likely to occur at all. Half marks for getting the deployment probability right but missing that the catch probability also falls through the red team's response.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Text
content::
The control game widget from part 2 is repeated below. On its **Protocol** tab, change the proportion of solutions for which we defer to $T$. Watch how this changes the red team's optimal strategy and how it changes the suspiciousness distribution of attacks.

#### Widget
source:: [[../widgets/xlab-control-game]]

#### Question: Open
id:: 78651f04-21ea-4a54-897b-ed18357f156a
content:: Note that deferring to $T$ neutralizes an attack silently. Given that, explain why a wide defer band pushes the red team toward maximally subtle attacks, and what sets the usefulness price of deferring.
assessment-instructions:: Full marks for both halves. Why maximally subtle: to ship, and possibly win, an attack must score below the defer threshold; widening the defer band lowers that threshold and forces more subtle backdoors, which are more often broken and so have a lower success rate. What sets the usefulness price: the width of the band, since the deferred fraction is roughly the band width and almost all of it is innocent code, and the capability gap between $U$ and $T$, since each deferred problem is answered at $T$'s quality instead of $U$'s. A smaller $U$ to $T$ gap would make deferring cheaper. Half marks for one half.
feedback-instructions:: One turn, at most three sentences: say plainly what the learner got right, then state the model answer from the rubric in full so they leave with it. Do not mention scores or quote the rubric's marking language. No follow-up question. No generic praise.

#### Text
content::
In summary, the monitor is a noisy classifier whose value is concentrated in the low-false-positive tail. The red team uses the optimal strategy over attack rate and subtlety. Auditing spends a scarce budget on the suspicious tail; deferring rewrites the mid-suspicion band with the trusted model. Safety is measured against the red team's best response throughout, and deferring to $T$ more trades usefulness from a more capable model $U$ for the safety from a less capable model $T$.

The control game widget models most of these interactions. For any given blue team strategy, the red team uses the optimal strategy against it, so the ringed point always sits against a best-responding adversary. The grey curve is the Pareto frontier: every safety and usefulness pair reachable at the current audit budget and monitor quality by varying the defer band, where improving one number means giving up some of the other.

As we change how much we defer to $T$, the protocol slides along the Pareto frontier, trading usefulness for safety along a fixed curve. As the monitor quality or the audit budget varies, the Pareto frontier shifts: a better monitor or a larger budget lifts the curve up and to the right, letting you reach the same safety at higher usefulness.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson continues: the rest of section 3.2 and section 3.3, defer to trusted.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

Google. "Classification: ROC and AUC." *Machine Learning Crash Course*, Google. [developers.google.com](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc)
*A short primer on ROC curves and AUC, for the signal-detection reading of the monitor.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::

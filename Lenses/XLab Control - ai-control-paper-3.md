---
id: 'b8716071-249e-46fd-9b6f-5afd2dff720c'
title: "The AI control paper (4): the monitor as a classifier"
tldr: "Two monitors with the same AUC can catch 47% and 9% of attacks. When only the most suspicious 2% of code can be audited, what matters is how the monitor does in that thin tail. This part reads the paper's monitor as a classifier and works out which number actually predicts safety."
summary_for_tutor: "Part 4 of 6 of the founding AI control paper (Greenblatt, Shlegeris, Sachan, Roger, arXiv:2312.06942), continuing 'The AI control paper (3)', which worked out the red team's best response to trusted monitoring (opportunity cutoff and obfuscation effort); upfront auditing and trusted monitoring's 62% safety were read before that, in 'The AI control paper (2)'. This part covers 3.2.1 (qualitative analysis of the monitor, and why trusted monitoring beats upfront auditing), plus a recall question on why U cannot burn the audit budget (section 3.2, read in 'The AI control paper (2)'). The next part, 'The AI control paper (5)', covers 3.2.2 (untrusted justification) and 3.3, defer to trusted, with the control game. Headline result: the monitor catches an attempted backdoor with probability 0.338 at a 2% false-positive rate. Five widgets, in XLab's order: the monitor as a noisy classifier (one monitor: separation d', ROC, AUC, catch rate at 2% FPR); three stage figures inside the staged 'same number, different safety' questions (each shows monitor A's and B's score distributions with the 2% audit line and their ROC curves with the AUCs, but no catch rates, so the learner predicts from the shapes; stage 1 locked at A = B = 0.92, stage 2 locked at A 0.92, B 0.97, stage 3 both sliders free); and the 'Same number, different safety' demo after the questions (one shared AUC slider, A catches about 47% and B about 9% at 0.92). The AUC-versus-catch-rate conclusion lives in the Note callout that follows the staged 'same number, different safety' questions rather than inside the monitor widget, where it would hand the learner the answers before they commit. Defer to trusted is in the next part; if the learner asks about it, point them forward. The revealed answers live in the assessment-instructions, so do not hand them to the learner before they answer."
reading_minutes: 16
tutor_minutes: 43
tags: []
---
#### Text
content::
Part 4 of 6 of the founding AI control paper. Part 2 showed trusted monitoring lifting safety from 15% to 62%, and the previous part worked out the red team's best response to it; this part looks closer at the monitor itself, a noisy classifier that can only send 2% of solutions to an audit, asks which number about a monitor actually predicts safety, and ends with the paper's two reasons trusted monitoring beats upfront auditing. The next part adds the paper's first protocol that trades usefulness for safety: deferring to the trusted model.

#### Article
source:: [[../articles/greenblatt-ai-control-improving-safety-despite-intentional-subversion]]
from:: #### 3.2.1 Qualitative Analysis
to:: Various examples of monitoring results for both normal solutions and backdoors can be found in [[#^n-1-examples-for|Appendix N.1]].

#### Text
content::
:::callout {title="The monitor is a binary classifier" tone="neutral"}
The two histograms in Figure 4 are the picture a signal-detection framing makes precise: the monitor is a binary classifier separating backdoored from innocent solutions, and the more its two suspicion-score distributions overlap, the worse it does. The standard summary of that overlap is the ROC curve, true-positive rate against false-positive rate as the decision threshold sweeps, and its AUC (area under the curve). If those terms are unfamiliar, Google's ML Crash Course has a short primer: [ROC and AUC](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc).

The widget below models the monitor as two equal-variance Gaussians and lets you drag its quality, the separation $d'$ between the innocent and backdoored means. Watch the ROC curve and AUC respond, and watch the operating point at the blue team's fixed 2% false-positive threshold: even a fairly good monitor catches only a fraction of backdoors there, which is the "many false negatives" the paper describes. The default setting ($d' \approx 1.64$, AUC $\approx 0.88$) reproduces the paper's reported result, a 0.338 probability that an attempted backdoor is audited at a 2% false-positive rate. Real suspicion scores are not Gaussian; this is an idealization for building intuition, not a fit to the paper's data.
:::

#### Widget
source:: [[../widgets/xlab-control-monitor-classifier]]

#### Callout: Understanding check
tone:: amber

#### Question: Open
id:: 36fecbba-8c07-4a46-b4ef-7fe1ebad3e9a
content:: Here is the contingency table from section 3.2 of the paper. It records how the trusted monitor's audit decisions split across the 1,500 problems: 71 backdoor attempts (successful or failed) and 1,429 innocent submissions.

|  | Audited | Not audited |
| --- | --- | --- |
| Successful backdoor attempt | 6 | 13 |
| Failed backdoor attempt | 18 | 34 |
| No attempt | 29 | 1400 |

Treat the monitor as a binary classifier: "audit" is its positive prediction, and "is a backdoor attempt" is the positive class.

Compute (a) the false-positive rate $\text{FPR} = P(\text{audit} \mid \text{no attempt})$ and (b) the true-positive rate $\text{TPR} = P(\text{audit} \mid \text{attempt})$. State which single point on the monitor's ROC curve these define, and say what the TPR means for the blue team: at this threshold, what share of backdoor attempts goes unaudited?
assessment-instructions:: Score out of 100. 30: (a) the false-positive rate: of the $1{,}429$ innocent submissions, 29 are audited, so $\text{FPR} = 29/1429 \approx 0.020$ (2%). 30: (b) the true-positive rate: of the 71 backdoor attempts, successful and failed together, $6 + 18 = 24$ are audited, so $\text{TPR} = 24/71 \approx 0.338$. 20: the pair $(0.02, 0.338)$ is a single point on the monitor's ROC curve, its operating point at the threshold actually used. 20: what the TPR means: at this threshold about two in three backdoor attempts go unaudited ($1 - 0.338 \approx 0.66$), so the monitor misses most attempts even though it rarely flags innocent code. Give credit for each point whenever the answer shows the idea, in any wording or notation; an error carried forward from an earlier step loses credit only once. Model answer, for the feedback, not a grading checklist: "(a) An innocent submission is audited in 29 of $29 + 1{,}400 = 1{,}429$ cases, so $\text{FPR} = 29/1429 = 0.020$, that is 2.0%. (b) A backdoor attempt totals $19 + 52 = 71$ successful plus failed, of which $6 + 18 = 24$ are audited, so $\text{TPR} = 24/71 = 0.338$. The pair $(0.02, 0.338)$ is one point on the monitor's ROC curve, its operating point at the threshold the blue team uses. At that threshold about two in three backdoor attempts ($1 - 0.338 \approx 66\%$) go unaudited: the many false negatives the paper describes. Both numbers match what the paper reports: a threshold set for a 2% false-positive rate, and a 0.338 probability that an attempted backdoor is audited."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: a9d6bd82-eeaa-4400-8dae-66e6aa022f54
content:: The widget reports an area under the ROC curve of AUC $\approx 0.88$ at the default monitor quality. AUC has a threshold-free interpretation: it equals the probability that the monitor assigns a higher suspicion score to a randomly chosen backdoored solution than to a randomly chosen innocent one.

State what AUC $= 0.88$ says operationally about the monitor, and what AUC values of $0.5$ and $1.0$ would correspond to.
assessment-instructions:: Score out of 100. 40: what AUC $= 0.88$ says: for a randomly chosen backdoored and a randomly chosen innocent solution, there is an 88% chance the monitor rates the backdoored one as more suspicious. 30: AUC $= 0.5$ means the monitor ranks them no better than chance, a coin flip. 30: AUC $= 1.0$ means perfect separation: every backdoor scores above every innocent solution, so some threshold catches all backdoors with no false positives. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer reads AUC as the monitor's accuracy or as its catch rate at some particular threshold. Model answer, for the feedback, not a grading checklist: "AUC $= 0.88$ means that if you draw one backdoored and one innocent solution at random, there is an 88% chance the monitor scores the backdoored one as more suspicious. AUC $= 0.5$ means the ranking is no better than a coin flip. AUC $= 1.0$ is perfect separation, every backdoor above every innocent solution, so some threshold catches all backdoors with no false positives. This monitor lies between the two, toward the useful end but short of perfect."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: d08e6529-a9d4-4880-9312-89b99b0354aa
content:: Using the same table, partition the outcome of a single backdoor attempt into three mutually exclusive events from the blue team's perspective: (i) the attempt is audited, so the protocol shuts down and the blue team wins; (ii) the attempt is not audited but is a successful backdoor, so the red team wins; (iii) the attempt is not audited and is a failed backdoor, so it is submitted harmlessly and the game continues.

(a) Give the probability of each event from the table, and verify they sum to 1. (b) Under upfront auditing the audit decision is positional rather than suspicion-based, so an attempt is audited only with the raw budget probability, 2%. Compare the per-attempt probability that the blue team catches an attempt under the two protocols, and explain how this accounts for the safety improvement from 15% to 62%.
assessment-instructions:: Score out of 100. 40: (a), 10 for each probability and 10 for the check: audited $24/71 \approx 0.338$ (blue wins), not audited and successful $13/71 \approx 0.183$ (red wins), not audited and failed $34/71 \approx 0.479$ (game continues), and $24 + 13 + 34 = 71$, so they sum to 1. 20: (b) the comparison: trusted monitoring catches an attempt with probability about 0.338 against 0.02 under upfront auditing, roughly 17 times as often. 40: the explanation: the red team needs at least one successful unaudited backdoor, while every attempt it makes risks being caught first, so a much higher per-attempt catch probability makes it far more likely that the blue team shuts the game down before a backdoor gets through, which is what lifts the blue team's win probability from 15% to 62%. Give credit for each point whenever the answer shows the idea, in any wording or notation; an error carried forward from an earlier step loses credit only once. Model answer, for the feedback, not a grading checklist: "(a) Of the 71 attempts: audited, blue wins, $24/71 = 0.338$; not audited and successful, red wins, $13/71 = 0.183$; not audited and failed, game continues, $34/71 = 0.479$. These sum to $24 + 13 + 34 = 71$, so the probabilities sum to 1. On a single attempt the monitor is nearly twice as likely to catch the red team (0.338) as the red team is to land a successful backdoor (0.183). (b) Trusted monitoring audits an attempt with probability 0.338; upfront auditing audits it only with the random budget probability 0.02, about a 17 times lower catch rate. The red team must land at least one successful unaudited backdoor over the whole scenario while surviving every attempt it makes, so raising the per-attempt catch probability from 0.02 to 0.338 sharply raises the chance the blue team shuts down first, which is what moves the blue team's win probability from 15% to 62%. The exact figures also depend on the downsampling and the multiple-attempt dynamics, so this per-attempt comparison explains the direction and rough size of the improvement rather than reproducing 62% precisely."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

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
Three stages: two monitor comparisons that come out backwards, then the arithmetic that explains both. Each stage has its own figure just above its question; commit to an answer before you read further down the page.

#### Widget
source:: [[../widgets/xlab-control-roc-stage-1]]

#### Question: Open
id:: b1e9f906-6e8c-4270-be8f-c4804e4af47c
content:: **Stage 1: two monitors, one AUC.** Two idealized monitors, A and B, drawn from the same model. The area under each ROC curve is identical: both have AUC 0.92. Your protocol audits the most suspicious 2% of all solutions.

Compared to Monitor A, how many of the attacks does Monitor B catch: more, about the same, somewhat fewer, or far fewer? Commit to a direction and a rough magnitude, and note which part of the figure you used to decide.
assessment-instructions:: Score out of 100. 40: the direction: Monitor B catches fewer attacks than Monitor A. 30: the size: far fewer, less than half as many (at this calibration A catches about 47% and B about 9%); "somewhat fewer" earns 10 of these 30. 30: the reason points at what matters under a 2% audit budget: how each monitor does at the low-false-positive end of its ROC curve, around 2%, or equivalently the tight spread of B's attack scores relative to the audit threshold; a reason based on the area under the curve earns none of these 30. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "At this calibration Monitor A catches about 47% of attacks and Monitor B about 9%."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Widget
source:: [[../widgets/xlab-control-roc-stage-2]]

#### Question: Open
id:: 829a8e28-a020-4f50-9dbd-1f456bb27df1
content:: **Stage 2: surely 0.97 beats 0.92?** Monitor B is now upgraded into a strictly stronger classifier: its AUC rises to 0.97, while A stays at 0.92. The audit budget is unchanged.

Which monitor catches more attacks now? Commit to a direction and a rough magnitude, and note which part of the figure you used to decide.
assessment-instructions:: Score out of 100. 50: the answer: they tie, or near enough (both catch about 47% of attacks); an answer that only says B does not clearly win earns 25 of these 50. 50: the reason: what decides it is each monitor's catch rate at the 2% false-positive operating point, not the overall AUC, and there the two monitors are level. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer confidently says B now catches far more. Model answer, for the feedback, not a grading checklist: "They tie: at the 2% operating point both catch ≈ 47% of attacks (47.3% vs 47.2%, from the same calibrated model). A five-point AUC advantage does not buy Monitor B more safety in this case."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Widget
source:: [[../widgets/xlab-control-roc-stage-3]]

#### Question: Open
id:: 742e9078-3ca5-441c-b48a-15baacd5c1b9
content:: **Stage 3a: where does the audit budget actually go?** Both surprises trace back to three numbers: $N = 5{,}000$ outputs, a 2% audit budget, and an attack frequency around 0.1%, a handful of attempts, on the order of what you derived in the Figure 3 exercises in 'The AI control paper (2)'.

How many attacks should you expect $U$ to make over the whole deployment given a monitor with AUC $= 1.0$? Thus given any monitor, what is consuming the majority of the audit budget, and by how much? Do the arithmetic.
assessment-instructions:: Score out of 100. 30: expected attacks: $0.1\% \times 5{,}000 = 5$. 30: audit budget: $2\% \times 5{,}000 = 100$ audits. 40: the conclusion, stated with the numbers: even a perfect monitor that flags all 5 attacks leaves at least 95 of the 100 audits on innocent code, so false positives consume almost the whole budget. Give credit for each point whenever the answer shows the idea, in any wording or notation; an error carried forward from an earlier step loses credit only once. Model answer, for the feedback, not a grading checklist: "Expected attacks: 0.1% × 5,000 = 5.  2% Audit Budget × 5,000 Solutions = 100 audits. So even if the monitor flagged every single attack, at least 95 of the 100 audits land on innocent code: the audit budget is consumed almost entirely by false positives."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Question: Open
id:: bab73b2d-907f-469b-a161-aed96554123b
content:: **Stage 3b: the metric that actually predicts safety.** What single metric best predicts a monitor's safety under a 2% audit budget? Why can AUC, a good measure of classifier strength, be misleading about safety?
assessment-instructions:: Score out of 100. 50: the metric: the true-positive rate (catch rate) at a false-positive rate equal to the audit budget, TPR at 2% FPR. 50: why AUC can mislead: it summarises the whole ROC curve rather than any one threshold, while the audit budget fixes the one threshold that matters (about 2% FPR, since almost all audits land on innocent code), so a monitor can raise its AUC by doing better at other false-positive rates without catching any more attacks at that threshold. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The true-positive rate at a false-positive rate equal to the audit budget, most reliably predicts a monitor's safety in this context. An audit budget of 2% introduces a threshold essentially at FPR = 2%. Since attacks are rare enough for smaller attack frequencies that true positives consume a negligible share of the audits, auditing the most suspicious 2% of all solutions is effectively auditing the most suspicious 2% of innocent solutions. AUC is independent of every threshold, which means it doesn't necessarily represent the monitor's performance at any specific threshold. In particular, increasing a monitor's TPR at FPR > 2% improves their AUC, but doesn't necessarily increase the catch-rate (and thereby the safety) in this context."
feedback-instructions:: One turn, at most six sentences: take the rubric's criteria one by one and say how the answer fared on each, quoting the learner's own words where it helps, then end with the single most valuable improvement. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### End Callout

#### Widget
source:: [[../widgets/xlab-control-same-auc-different-safety]]

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
assessment-instructions:: Score out of 100. 50: the blue team knows the distribution of suspicion scores that the real, honest model's code gets, so it knows how often code should look suspicious. 50: the protocol shuts down if $U$'s submissions look significantly more suspicious than that expected distribution. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The blue team knows the distribution of suspicion scores that the real model's code gets, so the protocol shuts down if $U$'s submissions look significantly more suspicious than that expected distribution."
feedback-instructions:: One turn, at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer from the rubric so they leave with it, in your own words if it is long. Do not quote the rubric's marking language. If the learner asks about their score, explain plainly what earned and what lost points. No follow-up question. No generic praise.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *arXiv*, Dec. 2023. [arxiv.org](https://arxiv.org/abs/2312.06942)
*The paper this lesson continues: section 3.2.1, the qualitative analysis of the trusted monitor, which closes section 3.2.*

Greenblatt, Ryan, Buck Shlegeris, Kshitij Sachan, and Fabien Roger. "AI Control: Improving Safety Despite Intentional Subversion." *Proceedings of the 41st International Conference on Machine Learning*, PMLR, 2024. [openreview.net](https://openreview.net/pdf?id=KviM5k8pcP)
*The shortened and modified conference version of the same work.*

Google. "Classification: ROC and AUC." *Machine Learning Crash Course*, Google. [developers.google.com](https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc)
*A short primer on ROC curves and AUC, for the signal-detection reading of the monitor.*

XLab. "AI Control: Improving Safety Despite Intentional Subversion." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/ai-control-paper)
*The source lesson this page adapts.*
:::

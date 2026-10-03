---
id: '156a4835-0b5b-4c25-981e-7afc77beeb9c'
title: "Notes on handling non-concentrated failures (1): the regimes, the detection race, and debate"
tldr: "A schemer that blows up the datacentre gets one shot, and you only have to catch it once. A schemer quietly a little worse at alignment research gets as many shots as the deployment is long. Ryan Greenblatt's notes on that second kind, part 1: what works with and without online training, where catastrophe outruns detection, and what debate can force."
summary_for_tutor: "Part 1 of 2 of Ryan Greenblatt's 'Notes on handling non-concentrated failures with AI control'; part 2 is the lens handling-non-concentrated-failures-2 (KL penalties, careful sabotage, and the two synthesis exercises). This page reproduces the post verbatim rather than summarising it, so the post is embedded as three Article excerpts and everything around it is scaffolding rather than Greenblatt's own words. Sequence: our lead-in linking back to the diffuse-threats lens (How can we solve diffuse threats like research sabotage with AI control?); article part 1 (the two classes of methods, and the no-online-training regime); the first Quick recall pair; article part 2 (online training, and what a schemer can still get away with, ending on the three regimes); our set-up of the quantitative detection-race model (C bad actions to catastrophe, chance q that one is noticed, decisive response at the K-th notice, and why its levers reach only two of the three regimes); the detection-race widget, an interactive port of the source lesson's DetectionRaceDemo, which the learner completes by reaching both reachable regimes; our note that the schemer's pace has no lever, since slowing down delays detection and catastrophe alike; article part 3 (debate, for binary questions and for oversight of a policy); the second Quick recall pair. The rest of the post (KL penalties, careful sabotage, the footnotes) is collapsed at the end of the last excerpt; the debate footnotes show as popups. The recall wording and the model answers inside the assessment briefs come from the source lesson; the lead-in prose, the two framing texts around the widget, and the framing sentences around the excerpts are Lens-written. Do not hand out the model answers in the briefs before the learner has attempted the question."
reading_minutes: 30
tutor_minutes: 20
tags: []
---
#### Text
content::
Part 1 of 2. This part reads Greenblatt's notes through the section on debate: the two classes of methods, what each regime lets a scheming model get away with, the race between detection and catastrophe, and what debate can and cannot force. Part 2 reads his two closing sections and then asks you to put the whole post to work.

[[../Lenses/XLab Control - diffuse-threats-research-sabotage|How can we solve diffuse threats like research sabotage with AI control?]] drew the line between concentrated failures, where a single action is enough for catastrophe, and diffuse ones, where the damage only accumulates over many actions. This reading is Ryan Greenblatt's working notes on the second kind: which high level methods exist, which regime each method puts you in, and how each regime fails.

The organising claim of the post is that non-concentrated failures can in principle be handled by asynchronous online training: sample a small fraction of the AI's actions after they have already run, rate them with an oversight process that has some signal on whether an action was bad, and use that rating as a reward. Most of what follows is a catalogue of two things: what a scheming model can still get away with under that method, and what you are left with if you decide not to train online at all.

*By Ryan Greenblatt (Redwood Research). Reproduced verbatim, with permission, from [the original post on the Redwood Research blog](https://blog.redwoodresearch.org/p/notes-on-handling-non-concentrated) (March 29, 2025).*

*What are the methods and issues when failures occur diffusely over many actions?*

#### Article
source:: [[../articles/greenblatt-notes-on-handling-non-concentrated-failures-with-ai-control-high-level-methods-and-different-regimes]]
to:: so non-scheming behavior might be quite bad by default.

#### Callout: Quick recall
tone:: neutral

#### Question: Open
id:: e721d815-44f7-4be3-82fb-6a30b6ed4a84
content:: What is a diffuse failure?
max-words:: 70
assessment-instructions:: Score out of 100. 60: the failure comes from the AI taking a large number of problematic actions, not from one action. 40: the harm builds up over a long period, so no single one of those actions is catastrophic on its own. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer describes a single catastrophic action. Model answer, for the feedback, not a grading checklist: "A failure that arises from the AI doing a large number of problematic actions over a long period of time."
feedback-instructions:: Reply in at most 90 words. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many actions it takes for the damage to land) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: fd0c3c36-9a07-4a01-acfc-9a4dfa627c6e
content:: What are the two classes of methods for handling diffuse failures?
max-words:: 100
assessment-instructions:: Score out of 100. 50: online training: the model is trained during deployment on ratings of its actions, which constrains it to perform well on that training signal. 50: no online training, so the model is left to generalise freely, and instead its behaviour is audited during deployment and the developers respond when they find something suspicious. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "There's online training, which constrains the model to perform well according to the exact local loss of the training process, and online auditing, which can detect suspicious behavior which we can respond to."
feedback-instructions:: Reply in at most 60 words. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what changes for the model when you train on the ratings instead of only reading them) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### End Callout

#### Question: Open
id:: ee6c6cc2-120c-471c-9777-a1251d7334d1
content::
\#### Choosing a regime

For a year, your model triages incoming papers for a safety research team, about 30,000 of them: for each it writes a short summary and a verdict on whether the paper is relevant. An automatic score is also available on every paper: it counts how many of the team's listed keywords each summary mentions. Researchers can carefully check about 3% of the triage decisions, and their checks are reliable. Last quarter the team ran a one-month trial of online training on the checks: among the decisions checked, the share the researchers marked correct rose from about 70% before the trial to about 90% after it.

Would you train the triage model online on those checks, train only a model that picks which decisions the researchers check, or audit without training? Justify your choice from the oversight signals you have and what the trial tells you, and say what your choice costs if the model is not scheming.
max-words:: 210
placeholder:: Your choice, why it fits this signal and what the trial tells you, and its cost if the model is honest.
assessment-instructions:: Score out of 100. There is no single right regime; grade whether the choice follows from the signal and the trial. 40: a choice justified from the signal: the researchers' checks measure what actually matters and are reliable, but they are sparse (about 900 a year) and expensive, and the keyword score is cheap and covers everything but is a crude proxy: training on it would push even an honest model to stuff keywords rather than judge relevance, and its score would rise whether or not the model had been holding back; training on a signal forces a scheming model to stop being systematically worse on it, so its direct effects can only help if the model is scheming, while what it costs an honest model depends on how good the signal is. Any regime earns the 40 if argued from these properties, for example: train online on the checks, which is hard to exploit because the signal is the real target, but sample-limited; train only a model that picks which decisions get checked, which makes the 3% more informative without changing the triage model; audit without training, which leaves the model's honest behaviour untouched but leaves small, steady underperformance hidden inside the uncertainty about how good honest triage would be. A choice with no reason tied to the quality or the cost of the signal earns at most 20. 20: the trial, any argued reading that bears on the choice: a real gain on the signal that matters makes training worth it whatever the cause; a large gain from a little training is also evidence that the model had been underperforming, possibly deliberately, which may call for a response beyond training; or the before and after samples are small, so the gain is uncertain. Mentioning the trial without letting it bear on the choice earns at most 6. 40: the cost if the model is not scheming, specific to the chosen regime: online training brings logistics and a model that changes over time, while the usual worry, training on a proxy degrading an honest model, is small here because the signal is the real target; training a selector costs building and training it but leaves an honest model untouched; auditing alone gives up gains training could bring and will sometimes fire responses on an honest model, so responses should be cheap and graded, with a low expected cost if the model is benign. A generic cost not tied to the chosen regime earns at most 15. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The checks are the real target and reliable, so unlike a cheap proxy they are hard to game, and training on them should not make an honest model worse; but about 900 checks a year is a thin signal. The trial raised the share of correct decisions from about 70% to 90% on that real signal, so training buys real gains; a jump that large from a month of training also makes me ask whether the model had been holding back, so I would look closer at what changed. I would train the triage model online on the checks, and train a selector to send the researchers the decisions most likely to be wrong, so each check carries more signal. If the model is honest, the cost is mainly logistics: running training during deployment, and a triage model whose behaviour drifts over time, so the team's sense of what it does goes stale. Auditing alone would also be defensible: it keeps the honest model untouched, but small, steady misjudgements could hide inside the uncertainty about how good honest triage would be."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask whether the researchers' checks measure the real goal or a proxy for it) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Article
from:: Once we consider online training (including of models used for monitoring and auditing) the situation becomes more complex.
to:: it would take nearly an indefinite period to train away the problematic behavior if it would ever be trained away at all.

#### Text
content::
The line between those regimes is quantitative, so it is worth putting numbers on it. Say a schemer needs C bad actions before the damage counts as catastrophic, each bad action has an independent chance q of being noticed, and the deployer responds decisively at the K-th notice. The race is then between C and K/q: whether the K-th notice lands before the C-th bad action does.

The regimes above are three outcomes of that race. Caught in time, where the response reliably fires first. Detected, but too late, where the signal exists but catastrophe arrives first. And effectively never detected, where the expected damage before the response runs past 1,000,000 actions. The levers below reach the first two only, because the largest bill they allow is K/q = 20 / 0.0001 = 200,000 actions.

#### Widget
source:: [[../widgets/xlab-control-detection-race]]

#### Text
content::
The schemer's pace has no lever, because acting more slowly delays detection and catastrophe by the same factor. The race depends only on C, q and K, and the expected damage before the response is K/q however concentrated the threat is.

#### Question: Open
id:: fcd868a0-b543-490a-befb-9e3e0d958f3b
content::
\#### Racing the response

A scheming model needs about 300 subtly wrong code reviews to weaken a safety-critical codebase beyond repair. 1% of its reviews are re-checked by a human, who recognises a wrong one half the time. The lab responds decisively once it has noticed 5 wrong reviews. The lab wants a safety margin: the expected number of wrong reviews before its response should be at most half of the 300.

(a) Does it meet that margin now? (b) Keeping the response at 5 notices, what re-check rate would meet it? (c) Could changing the response rule alone meet it, and what would the new rule cost if the model is honest?
max-words:: 170
placeholder:: Your numbers for (a), (b) and (c), and the cost in (c).
assessment-instructions:: Score out of 100. Worked numbers: the chance a wrong review is noticed is q = 0.01 x 0.5 = 0.005, and the expected number of wrong reviews before the response is K/q. 30: (a): K/q = 5 / 0.005 = 1,000, far above the target of 150 (and above 300 itself; the chance of 5 notices within 300 wrong reviews is only about 2%), so no. 30: (b): q must reach K / 150 = 5 / 150, about 0.033, so the re-check rate must be about 6.7% at 50% recognition. Credit a learner who notes that without the margin, K/q = 300 would need about 3.3%, which gives only about a 56% chance of responding in time. 40: (c): responding at the first notice gives K/q = 1 / 0.005 = 200, better than 1,000 but still above 150, so the rule alone does not meet the margin (about a 78% chance of at least one notice within 300) (20); combined with re-checking at least about 1.3% of reviews (1 / 150 = 0.0067, divided by 0.5) it does, which earns credit within these 20 if offered; the cost if the model is honest: a decisive response now fires on a single honest mistake that gets noticed, so the first-notice response should be cheap and graded, escalating only if more turns up (20). Give credit for each point whenever the answer shows the idea, in any wording. Small rounding differences do not matter. Model answer, for the feedback, not a grading checklist: "(a) Each wrong review is noticed with chance 0.01 x 0.5 = 0.005, so the lab expects 5 / 0.005 = 1,000 wrong reviews before responding: far over the target of 150, and over the 300 that does the damage. (b) The margin needs 5 / q at most 150, so q at least 0.033: re-check about 6.7% of reviews. (c) Responding at the first notice gives 1 / 0.005 = 200, still above 150, so not alone; with first-notice response plus re-checking about 1.3% it meets the margin. The cost: an honest model's occasional real mistake would now trigger the decisive response, so the first response should be cheap, such as reviewing that area more closely, with a pause only if more turns up."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing; if a number is wrong, point to the first wrong step rather than giving the corrected total. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the text above the widget (for instance, ask what fraction of wrong reviews ends up noticed) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Article
from:: ## Recursive oversight: debate
to:: but also on bad actions from the policy.

#### Callout: Quick recall
tone:: neutral

#### Question: Open
id:: 23b784eb-365d-4850-a4d9-66ddba298ff4
content:: What does online training force on a scheming model, and why?
max-words:: 80
assessment-instructions:: Score out of 100. 50: a scheming model can no longer keep performing systematically worse than an honest model would. 20: specifically on the oversight metric that the training uses. 30: why: that systematically worse behaviour gives a training signal, so it gets updated away. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer says online training removes sabotage entirely or makes the schemer behave exactly like a non-schemer. Model answer, for the feedback, not a grading checklist: "Scheming models cannot repeatedly behave systematically worse on the oversight metric being trained against as the behavior would get updated away."
feedback-instructions:: Reply in at most 60 words. If anything is missing or wrong, name the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what happens to a behavior that reliably scores lower on the trained metric) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: d917f996-399b-4820-b85a-cdb326389ef1
content:: From a scheming model's perspective, what are the two ways things can go wrong under online training?
max-words:: 100
assessment-instructions:: Score out of 100. 50: auditing notices suspicious behaviour and the developers respond, in the extreme by catching the model red-handed. 50: its systematically worse behaviour gives training enough signal that the behaviour gets updated away. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Auditing reveals suspicious activity and triggers a response (in the extreme, being caught red-handed); or its systematically worse behavior generates enough training signal to be updated away, which might also remove or reduce the scheming itself."
feedback-instructions:: Reply in at most 60 words. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the two levers a deployer holds are, reviewing actions and training on the ratings) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Notes on Handling Non-Concentrated Failures with AI Control: High Level Methods and Different Regimes." *Redwood Research Blog*, Redwood Research, 29 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/notes-on-handling-non-concentrated)
*The reading itself, reproduced above through the section on debate: the high level methods for handling failures that arise from many diffuse actions, and the regime each method produces. The closing sections on KL penalties and careful sabotage are in part 2.*

XLab. "Notes on handling non-concentrated failures with AI control." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/handling-non-concentrated-failures)
*The source lesson this page adapts, including the detection-race demo and the recall questions.*
:::

---
id: '156a4835-0b5b-4c25-981e-7afc77beeb9c'
title: "Notes on handling non-concentrated failures (1): the regimes, the detection race, and debate"
tldr: "A schemer that blows up the datacentre gets one shot, and you only have to catch it once. A schemer quietly a little worse at alignment research gets as many shots as the deployment is long. Ryan Greenblatt's notes on that second kind, part 1: what works with and without online training, where catastrophe outruns detection, and what debate can force."
summary_for_tutor: "Part 1 of 2 of Ryan Greenblatt's 'Notes on handling non-concentrated failures with AI control'; part 2 is the lens handling-non-concentrated-failures-2 (KL penalties, careful sabotage, and the two synthesis exercises). This page reproduces the post verbatim rather than summarising it, so the post is embedded as three Article excerpts and everything around it is scaffolding rather than Greenblatt's own words. Sequence: our lead-in linking back to the diffuse-threats lens (How can we solve diffuse threats like research sabotage with AI control?); article part 1 (the two classes of methods, and the no-online-training regime); the first Quick recall pair; article part 2 (online training, and what a schemer can still get away with, ending on the three regimes); our set-up of the quantitative detection-race model (C bad actions to catastrophe, chance q that one is noticed, decisive response at the K-th notice, and why its levers reach only two of the three regimes); the detection-race widget, an interactive port of the source lesson's DetectionRaceDemo, which the learner completes by reaching both reachable regimes; our note that the schemer's pace has no lever, since slowing down delays detection and catastrophe alike; article part 3 (debate, for binary questions and for oversight of a policy); the second Quick recall pair. The rest of the post (KL penalties, careful sabotage, the footnotes) is collapsed at the end of the last excerpt; the debate footnotes show as popups. The recall wording and the model answers inside the assessment briefs come from the source lesson; the lead-in prose, the two framing texts around the widget, and the framing sentences around the excerpts are Lens-written. Do not hand out the model answers in the briefs before the learner has attempted the question."
reading_minutes: 30
tutor_minutes: 12
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
max-chars:: 400
assessment-instructions:: Score out of 100. 60: the failure comes from the AI taking a large number of problematic actions, not from one action. 40: the harm builds up over a long period, so no single one of those actions is catastrophic on its own. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer describes a single catastrophic action. Model answer, for the feedback, not a grading checklist: "A failure that arises from the AI doing a large number of problematic actions over a long period of time."
feedback-instructions:: Reply in at most 90 words. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many actions it takes for the damage to land) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: fd0c3c36-9a07-4a01-acfc-9a4dfa627c6e
content:: What are the two classes of methods for handling diffuse failures?
max-chars:: 600
assessment-instructions:: Score out of 100. 50: online training: the model is trained during deployment on ratings of its actions, which constrains it to perform well on that training signal. 50: no online training, so the model is left to generalise freely, and instead its behaviour is audited during deployment and the developers respond when they find something suspicious. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "There's online training, which constrains the model to perform well according to the exact local loss of the training process, and online auditing, which can detect suspicious behavior which we can respond to."
feedback-instructions:: Reply in at most 60 words. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what changes for the model when you train on the ratings instead of only reading them) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### End Callout

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

#### Article
from:: ## Recursive oversight: debate
to:: but also on bad actions from the policy.

#### Callout: Quick recall
tone:: neutral

#### Question: Open
id:: 23b784eb-365d-4850-a4d9-66ddba298ff4
content:: What does online training force on a scheming model, and why?
max-chars:: 500
assessment-instructions:: Score out of 100. 50: a scheming model can no longer keep performing systematically worse than an honest model would. 20: specifically on the oversight metric that the training uses. 30: why: that systematically worse behaviour gives a training signal, so it gets updated away. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 50 if the answer says online training removes sabotage entirely or makes the schemer behave exactly like a non-schemer. Model answer, for the feedback, not a grading checklist: "Scheming models cannot repeatedly behave systematically worse on the oversight metric being trained against as the behavior would get updated away."
feedback-instructions:: Reply in at most 60 words. If anything is missing or wrong, name the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what happens to a behavior that reliably scores lower on the trained metric) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: d917f996-399b-4820-b85a-cdb326389ef1
content:: From a scheming model's perspective, what are the two ways things can go wrong under online training?
max-chars:: 600
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

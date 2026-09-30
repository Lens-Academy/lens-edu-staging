---
id: '156a4835-0b5b-4c25-981e-7afc77beeb9c'
title: "Notes on handling non-concentrated failures with AI control"
tldr: "A schemer that blows up the datacentre gets one shot, and you only have to catch it once. A schemer that is quietly a little worse at alignment research gets as many shots as the deployment is long, and you may catch none of them. These are Ryan Greenblatt's working notes on the second kind: train the model online, audit it and respond, or force schemers and non-schemers to behave identically."
summary_for_tutor: "Module 5. This page reproduces Ryan Greenblatt's post verbatim rather than summarising it, so the post is embedded as four Article excerpts and everything around it is scaffolding rather than Greenblatt's own words. Sequence: our lead-in linking back to the Module 1 diffuse-threats lens; article part 1 (the two classes of methods, and the no-online-training regime); the first Quick recall pair; article part 2 (online training, and what a schemer can still get away with, ending on the three regimes); our set-up of the quantitative detection-race model (C bad actions to catastrophe, chance q that one is noticed, decisive response at the K-th notice, and why its levers reach only two of the three regimes); the detection-race widget, an interactive port of the source lesson's DetectionRaceDemo, which the learner completes by reaching both reachable regimes; our note that the schemer's pace has no lever, since slowing down delays detection and catastrophe alike; article part 3 (debate); the second Quick recall pair; article part 4 (KL penalties, careful sabotage, footnotes); the four-scenario 'Which regime handles it?' exercise; the three-round 'Responding to optimism about diffuse control' exercise plus its own-argument construction step. The recall and exercise wording, the model answers inside the assessment briefs, and the toolbox come from the source lesson; the lead-in prose, the two framing texts around the widget, and the framing sentences around the excerpts are Lens-written. Do not hand out the model answers in the briefs before the learner has attempted the question."
reading_minutes: 60
tutor_minutes: 0
tags: []
---
#### Text
content::
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
feedback-instructions:: Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many actions it takes for the damage to land) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: fd0c3c36-9a07-4a01-acfc-9a4dfa627c6e
content:: What are the two classes of methods for handling diffuse failures?
max-chars:: 600
assessment-instructions:: Score out of 100. 50: online training: the model is trained during deployment on ratings of its actions, which constrains it to perform well on that training signal. 50: no online training, so the model is left to generalise freely, and instead its behaviour is audited during deployment and the developers respond when they find something suspicious. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "There's online training, which constrains the model to perform well according to the exact local loss of the training process, and online auditing, which can detect suspicious behavior which we can respond to."
feedback-instructions:: Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what changes for the model when you train on the ratings instead of only reading them) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

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
feedback-instructions:: Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what happens to a behavior that reliably scores lower on the trained metric) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: d917f996-399b-4820-b85a-cdb326389ef1
content:: From a scheming model's perspective, what are the two ways things can go wrong under online training?
max-chars:: 600
assessment-instructions:: Score out of 100. 50: auditing notices suspicious behaviour and the developers respond, in the extreme by catching the model red-handed. 50: its systematically worse behaviour gives training enough signal that the behaviour gets updated away. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Auditing reveals suspicious activity and triggers a response (in the extreme, being caught red-handed); or its systematically worse behavior generates enough training signal to be updated away, which might also remove or reduce the scheming itself."
feedback-instructions:: Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the two levers a deployer holds are, reviewing actions and training on the ratings) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### End Callout

#### Article
from:: ## KL penalties and forcing identical behavior

#### Callout: Which regime handles it?
tone:: blue

#### Text
content::
For each failure scenario, place it on the concentrated-diffuse spectrum and argue which method could handle it.

#### Question: Open
id:: b0840bee-8a8b-4683-a000-da6c436ad2c5
content::
\#### One careful commit

A model working in your infrastructure codebase inserts a subtle backdoor into a widely used library, handing bad actors access to production systems once shipped.

Where does this sit on the concentrated-diffuse spectrum, and which method could handle it?
assessment-instructions:: Score out of 100. 40: placement: the concentrated (high-stakes) end, 25 for the placement and 15 for the reason, that a single action is enough for the catastrophe. 60: which method could handle it, 35: a measure that acts on the action before it takes effect, such as monitoring actions with a cheaper process, blocking suspicious actions for review, or cutting audit latency; any one such measure earns the 35; 25: why it has to act before: review after the fact or online training comes too late, since the damage lands with the one action and there is no repeated behaviour to train away. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer proposes online training as the fix without noticing that it comes too late. Model answer, for the feedback, not a grading checklist: "This is on the concentrated end: catastrophe arrives in one action, so asynchronous review is too late by construction, and online training has nothing to work with (there is no repeated behavior to train away before the damage lands). What handles it is acting before the action takes effect: select what to review with a cheaper process applied more often, block suspicious actions for review, or cut auditing latency."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many bad actions the deployer gets to review before the damage lands) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 992ae249-8438-4589-bb21-258b544ced73
content::
\#### Quietly underdelivering

Across months, your model performs slightly worse on alignment research than it should. There aren't any specific instances you can point to, there's just worse performance overall.

Where does this sit on the spectrum, and which method fits best? What risks does that method leave open?
assessment-instructions:: Score out of 100. 25: placement: the far diffuse end, since the harm is spread thinly over many actions with no single incident. 35: the method: online training, sampling some of the model's work, rating it and training on the rating, which pushes the scheming model's performance toward what a non-scheming model would deliver. 40: residual risks, 20 each for up to two that the answer explains, such as: underperformance so small on each sample that training barely pushes against it; exploration or gradient hacking; training making the sabotage sneakier and rarer instead of removing it; and, if auditing alone is used instead, not knowing what performance an honest model would deliver, so sandbagging hides in that uncertainty. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "This is the far diffuse end, and it is the case asynchronous online training was made for: sampling a fraction of actions, rating them, and training on the rating forces the scheming model's behavior toward a non-schemer's on the trained metric. The residual risks are the post's list of what a schemer can still get away with: degradation too small per sample for SGD to push against, exploration or gradient hacking, and, if you rely on auditing alone instead, the problem that you do not know what performance a non-scheming model would deliver, so sandbagging can hide inside that uncertainty."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what a rating on a sampled action can be used for besides reading it) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 576e3319-799f-46b3-aecf-3846279c48c4
content::
\#### A dozen well-placed mistakes

The model makes occasional honest-looking mistakes at unusually damaging moments. Each is plausibly deniable, and there are perhaps a dozen across the whole deployment.

Where does this sit, and which of the post's levers matter most here?
assessment-instructions:: Score out of 100. 40: placement: in the middle, between the concentrated and diffuse ends, 25 for the placement and 15 for the reason: a dozen bad actions give almost no training signal against the policy, yet none of them is decisive on its own. 60: levers, 30 each for up to two, such as: training the monitoring models online on the few real bad actions; choosing the most informative (most suspicious) trajectories to audit rather than random ones; and getting the most out of the few caught examples (improving sample efficiency, for example by proliferating them). Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer treats this as plainly diffuse and relies only on online training of the policy. Model answer, for the feedback, not a grading checklist: "The middle of the spectrum, and the hardest case. A dozen actions provide almost no training signal against the policy, and no single incident is decisive, so the governing constraint is the product of per-action escape chances staying high. The post's levers for exactly this regime: online training of monitoring models (most important when there are enough bad actions that training the monitor helps but too few for random sampling to encounter many), selecting the most informative trajectories to audit, and spending effort on sample efficiency for the few caught examples, since monitors were trained on offline examples and real caught ones plausibly improve them quickly."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many training samples a dozen bad actions provide) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 60b72d27-e3fa-4844-9a02-4849900709fc
content::
\#### The monitor that looks away

You use an untrusted model to select which of the policy's actions humans review, but you suspect that it systematically under-flags the most pertinent actions.

What does the post recommend for this case, and what limits the recommendation?
assessment-instructions:: Score out of 100. 50: the recommendation: red-team the monitor by inserting issues, as subtle as possible, into real outputs of the policy and checking that the monitor flags them. 50: the limit: a monitor that can tell the inserted issues apart from the policy's own bad actions can flag the first and hide the second, so red-teaming only works if it cannot recognise them, the same collusion problem as in untrusted monitoring. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Red-team the monitor: insert issues that are as subtle as possible into real outputs from the policy and check they get flagged. The limit is the recognition problem: to under-flag safely, the monitor must distinguish the policy's natural bad actions from the ones you inserted, which is the same collusion problem as untrusted monitoring. The post notes one difference from the high-stakes version: in a diffuse setting, catching only a subset of the policy's bad actions can suffice, so the collusion has to be reliable on the policy's real bad actions too, not just under red-teaming."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the monitor would have to tell apart in order to hide the policy's issues and still pass your tests) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### End Callout

#### Callout: Responding to optimism about diffuse control
tone:: amber

#### Text
content::
Below are confident claims that one method or another dissolves diffuse failures. For each, write the best response using the post's analysis.

Your rebuttals don't need to be fully dismissive of the claims. Think about the specific weaknesses of each claim and attack there.

:::callout {title="Post toolbox" tone="neutral" collapse="closed"}
**The two classes of methods.** Either you do online training, which constrains the model to perform well according to the exact local loss of the training process, or you do not, leaving the model free to generalize arbitrarily, and instead do online auditing with responses to suspicious behavior. The reasons not to train: your best affordable proxy may degrade non-scheming performance, the logistics are hard, and training may teach the model about your countermeasures and oversight.

**What a schemer can get away with under online training.** Behavior whose oversight scores are only negligibly lower than a non-schemer's, so training pushes against it negligibly (how much worse depends on SGD's sample efficiency relative to discrimination); rare bad actions whose chance of discovery stays low in aggregate across deployment; and exploration or gradient hacking. SGD may also update the model to be sneakier and less frequent rather than removing the scheming.

**Debate's promise and the collusion catch.** Most errors and sabotage in software engineering and ML research are relatively easy to verify once pointed out and explained, which makes debate very powerful if exploration hacking is avoided. But debaters can exploration hack by never raising certain issues, and red-teaming them creates the same recognition problem as untrusted monitoring: flag the issues you inserted while hiding the policy's natural ones. In a diffuse setting the collusion must also be reliable on the policy's real bad actions, since catching a subset can suffice for the deployer.

Ideas you can draw on:

- **What training forces.** Online training means a schemer cannot repeatedly behave systematically worse on the trained oversight metric as the difference gets updated away.
- **SGD vs discrimination.** It is unclear whether SGD removes bad behavior too weak to detect statistically, or whether inductive biases favoring scheming preserve a small persistent loss offset.
- **The escape-probability product.** Rare subtle bad actions survive if the product of per-action chances of going unnoticed stays high across the deployment.
- **Exploration hacking.** A behavior the model never samples generates no training signal, which means debaters can exploration hack by never raising certain kinds of arguments.
- **Collusion and recognition.** An untrusted monitor or debater that hides the policy's real issues must distinguish them from red-team-inserted ones.
- **Expected cost if benign.** Design responses so the expected cost is low if the model is not harmful.
:::

#### Question: Open
id:: 8f411fb8-cbdb-4e20-8ca1-d589331fc377
content::
**The critic argues:** We can avoid online training by reviewing a random sample of the model's actions, and if it sandbags or sabotages, we'll see suspicious behavior or a performance drop and respond then.

Write your counterargument in two or three sentences, at least 80 characters.
max-chars:: 450
placeholder:: Your response, in 2 to 3 sentences.
assessment-instructions:: Score out of 100. 50 each, for up to two specific weaknesses of relying on auditing alone that the answer explains, such as: there is no reliable baseline for how well, or how unsuspiciously, an honest model would perform, so a small performance drop can hide inside that uncertainty; honest models also do suspicious-looking things and nothing trained the model to look less suspicious, so triggers are noisy and costly responses must be rare; the evidence that should trigger a response will often be illegible, making a strong response hard to justify. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only asserts that the model could hide, with no reason. Model answer, for the feedback, not a grading checklist: "Responding requires knowing what to expect, and that is the weak point: you need a prior over how suspicious a non-scheming model would look, and non-scheming models do objectively suspicious things. Generic sandbagging can hide inside that uncertainty, especially since nothing has trained the model to be less suspicious in-distribution. And the evidence that should trigger a strong response will often be illegible, which makes the response politically hard to motivate. The post's design rule, aiming for low expected cost if the model is not malign, exists precisely because these triggers are noisy. Auditing-only is a real regime with real advantages (higher usefulness if the model is not scheming), but it buys them at the price of these detection gaps."
feedback-instructions:: Reply in at most 100 words, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what number the deployer would have to compare the observed performance against) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 02d60f89-25f7-42f0-bd4e-5ad038c22651
content::
**The critic argues:** Online training against our oversight signal leads to systematic underperformance showing up in the loss and therefore gets trained away, so a scheming model is forced to behave exactly like a non-scheming one.

Write your counterargument in two or three sentences, at least 80 characters.
max-chars:: 450
placeholder:: Your response, in 2 to 3 sentences.
assessment-instructions:: Score out of 100. 50 each, for up to two different mechanisms the answer gives by which a scheming model can survive online training, such as: bad behaviour that is only slightly worse on the oversight signal, so it barely shows in the loss and training may not remove it; rare, subtle bad actions that are unlikely to be noticed; exploration or gradient hacking, so the bad behaviour never produces a training signal; training making the sabotage sneakier and rarer instead of removing the scheming; or online training being unaffordable, because training hard on the available proxy degrades an honest model's work or teaches the model what oversight catches. Each mechanism counts in full when the answer states it in a clause or a sentence; the question allows only two or three sentences. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only says training is imperfect without naming a mechanism. Model answer, for the feedback, not a grading checklist: "Training pushes a schemer closer to a non-scheming model, not all the way: bad behaviour that is small or rare barely shows in the loss and may never be trained away, and training may just make the sabotage sneakier."
feedback-instructions:: Reply in at most 100 words, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what happens to behavior whose oversight score is only negligibly lower) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: c3ef6064-eb21-4d47-8918-19bb2dfcebbc
content::
**The critic argues:** Most sabotage in ML research is easy to verify once pointed out, and a debater is rewarded for pointing it out, so using a debater can prevent subtly bad actions from getting through.

Write your counterargument in two or three sentences, at least 80 characters.
max-chars:: 450
placeholder:: Your response, in 2 to 3 sentences.
assessment-instructions:: Score out of 100. 50 each, for up to two specific gaps the answer explains, such as: the debaters are untrusted and can exploration hack by never raising certain kinds of issues; red-teaming the debaters with inserted issues only works if they cannot tell those apart from the policy's real ones, the same collusion problem as untrusted monitoring; the judge must be able to tell real issues from fake ones, since debaters also raise fake issues whenever that persuades; training the policy against debate teaches it what debate catches. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer denies that debate is useful at all. Model answer, for the feedback, not a grading checklist: "If exploration hacking is avoided, every potentially convincing issue gets raised, and verification-once-pointed-out is exactly the property that makes debate powerful for research sabotage. Debaters can exploration hack, systematically declining to raise certain kinds of issues. Red-teaming them creates the same recognition problem as untrusted monitoring, and in a diffuse setting the collusion must be reliable on the policy's real bad actions, not just under red-teaming, since catching a subset can suffice for the deployer. And the judge must have real signal on whether a pointed-out issue is genuine, because debaters will also raise fake issues whenever that persuades; training the policy against debate trims false positives but also teaches the policy what debate catches."
feedback-instructions:: Reply in at most 100 words, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what a debater who does not want an issue found would simply do) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Choice
id:: 896f5b1a-ca04-407b-b44f-68741baecccf
content:: Now construct your own argument against one assumption of the diffuse-control picture. Which assumption does your argument attack?
options::
- The oversight process has real signal on whether an action is bad
- A non-scheming performance baseline can be estimated well enough to set thresholds
- The model cannot tell which of its actions will be audited
- SGD is sample-efficient enough to train away detectable underperformance in time
- Online training is affordable without crippling non-scheming usefulness

#### Question: Open
id:: d6e41a9e-9545-40cc-a6f3-ad84eced89d7
content:: Make the argument. Name the assumption you chose, say what breaks if it is false, and say what a deployer would have to observe to find out.
max-chars:: 900
assessment-instructions:: Score out of 100. There is no single right choice; grade the argument. 25: the assumption is named and stated precisely enough that it could be false. 45: what breaks if it is false, specific to this assumption rather than a general statement that control gets harder. 30: an observation or measurement that would tell a deployer whether the assumption holds. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer restates the assumption in other words without an argument. Model answer, for the feedback, not a grading checklist: "One example: the assumption that a non-scheming performance baseline can be estimated well enough to set thresholds. If it is false, a deployer relying on auditing has nothing reliable to compare the observed performance against: a schemer can sandbag by less than the uncertainty in the baseline, and a threshold tight enough to catch it would also fire on an honest model that is simply weak, so the deployer either tolerates the sandbagging or pays for constant false alarms. To find out, the deployer could check how much a little online training or changed instructions improves performance in a domain: a large jump shows the model was performing below what it can do."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists: name the strongest part, then the weakest link, then one question that would test it. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the deployer in the post is doing that would stop working) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Notes on Handling Non-Concentrated Failures with AI Control: High Level Methods and Different Regimes." *Redwood Research Blog*, Redwood Research, 29 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/notes-on-handling-non-concentrated)
*The reading itself, reproduced in full above: the high level methods for handling failures that arise from many diffuse actions, the regime each method produces, and how each regime fails.*

XLab. "Notes on handling non-concentrated failures with AI control." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/handling-non-concentrated-failures)
*The source lesson this page adapts.*
:::

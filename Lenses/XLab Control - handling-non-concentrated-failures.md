---
id: '156a4835-0b5b-4c25-981e-7afc77beeb9c'
title: "Notes on handling non-concentrated failures with AI control"
tldr: "A schemer that blows up the datacentre gets one shot, and you only have to catch it once. A schemer that is quietly a little worse at alignment research gets as many shots as the deployment is long, and you may catch none of them. These are Ryan Greenblatt's working notes on the second kind: train the model online, audit it and respond, or force schemers and non-schemers to behave identically."
summary_for_tutor: "Module 5. This page reproduces Ryan Greenblatt's post verbatim rather than summarising it, so the post is embedded as four Article excerpts and everything around it is scaffolding rather than Greenblatt's own words. Sequence: our lead-in linking back to the Module 1 diffuse-threats lens; article part 1 (the two classes of methods, and the no-online-training regime); the first Quick recall pair; article part 2 (online training, and what a schemer can still get away with); the detection-race widget, an interactive port of the source lesson's DetectionRaceDemo; article part 3 (debate); the second Quick recall pair; article part 4 (KL penalties, careful sabotage, footnotes); the four-scenario 'Which regime handles it?' exercise; the three-round 'Responding to optimism about diffuse control' exercise plus its own-argument construction step. The recall and exercise wording, the model answers inside the assessment briefs, and the toolbox come from the source lesson; the lead-in prose and the framing sentences around the excerpts are Lens-written. Do not hand out the model answers in the briefs before the learner has attempted the question."
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
assessment-instructions:: The learner has just read the opening of Greenblatt's post and is answering from memory. Full marks for the substance of: a failure that arises from the AI doing a large number of problematic actions over a long period of time. Give credit for equivalent wording ("non-concentrated", "many small bad actions adding up"). Take marks off if the answer describes a single catastrophic action, or if it names an example without stating what makes the class diffuse. Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many actions it takes for the damage to land) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### Question: Open
id:: fd0c3c36-9a07-4a01-acfc-9a4dfa627c6e
content:: What are the two classes of methods for handling diffuse failures?
max-chars:: 600
assessment-instructions:: The learner has just read the opening of Greenblatt's post and is answering from memory. Full marks for both classes: online training, which constrains the model to perform well according to the exact local loss of the training process; and doing without online training, leaving the model free to generalize arbitrarily, and instead doing online auditing that detects suspicious behavior you can respond to. Half marks for one class only. Give credit if the learner adds that the same oversight signal can serve both. Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what changes for the model when you train on the ratings instead of only reading them) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### End Callout

#### Article
from:: Once we consider online training (including of models used for monitoring and auditing) the situation becomes more complex.
to:: it would take nearly an indefinite period to train away the problematic behavior if it would ever be trained away at all.

#### Widget
source:: [[../widgets/xlab-control-detection-race]]

#### Article
from:: ## Recursive oversight: debate
to:: but also on bad actions from the policy.

#### Callout: Quick recall
tone:: neutral

#### Question: Open
id:: 23b784eb-365d-4850-a4d9-66ddba298ff4
content:: What does online training force on a scheming model?
max-chars:: 500
assessment-instructions:: The learner is answering from memory after reading Greenblatt's sections on online training and debate. Full marks for the substance of: a scheming model cannot repeatedly behave systematically worse on the oversight metric being trained against, because that difference would get updated away. Give credit for adding that training forces schemer and non-schemer behavior closer without making them identical. Take marks off for an answer that claims training eliminates sabotage outright, since the post lists several things a schemer can still get away with. Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what happens to a behavior that reliably scores lower on the trained metric) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### Question: Open
id:: d917f996-399b-4820-b85a-cdb326389ef1
content:: From a scheming model's perspective, what are the two ways things can go wrong under online training?
max-chars:: 600
assessment-instructions:: The learner is answering from memory. Full marks for both: auditing reveals suspicious activity and triggers a response, in the extreme being caught red-handed; or its systematically worse behavior generates enough training signal to be updated away, which might also remove or reduce the scheming itself. Half marks for one only. Reply in at most 60 words. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the two levers a deployer holds are, reviewing actions and training on the ratings) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

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
assessment-instructions:: Mark against the post's analysis. Full marks for placing this on the concentrated end and explaining why: catastrophe arrives in one action, so asynchronous review is too late by construction, and online training has nothing to work with because there is no repeated behavior to train away before the damage lands. Credit an answer that names the post's adjustments as failures become more concentrated: select what to review with a cheaper process applied more often, block actions for review or cut auditing latency, and have responses other than training. Full marks require the conclusion that this is a high-stakes control problem, not a diffuse one. Take marks off for an answer that proposes online training without noticing the timing problem. Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many bad actions the deployer gets to review before the damage lands) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### Question: Open
id:: 992ae249-8438-4589-bb21-258b544ced73
content::
\#### Quietly underdelivering

Across months, your model performs slightly worse on alignment research than it should. There aren't any specific instances you can point to, there's just worse performance overall.

Where does this sit on the spectrum, and which method fits best? What risks does that method leave open?
assessment-instructions:: Mark against the post's analysis. Full marks for placing this at the far diffuse end and naming asynchronous online training as the method it was made for: sampling a fraction of actions, rating them, and training on the rating forces the scheming model's behavior toward a non-schemer's on the trained metric. The second half of the question is the residual risks, and a full-marks answer names at least two of the post's list: degradation too small per sample for SGD to push against, exploration or gradient hacking, and, if you rely on auditing alone instead, the problem that you do not know what performance a non-scheming model would deliver, so sandbagging can hide inside that uncertainty. Take marks off for an answer that names the method but no residual risk. Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what a rating on a sampled action can be used for besides reading it) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### Question: Open
id:: 576e3319-799f-46b3-aecf-3846279c48c4
content::
\#### A dozen well-placed mistakes

The model makes occasional honest-looking mistakes at unusually damaging moments. Each is plausibly deniable, and there are perhaps a dozen across the whole deployment.

Where does this sit, and which of the post's levers matter most here?
assessment-instructions:: Mark against the post's analysis. Full marks for placing this in the middle of the spectrum and recognising it as the hardest case: a dozen actions provide almost no training signal against the policy, and no single incident is decisive, so the governing constraint is the product of per-action escape chances staying high. A full-marks answer names at least two of the post's levers for this regime: online training of monitoring models, which the post says matters most when there are enough bad actions that training the monitor helps but too few for random sampling to encounter many; selecting the most informative trajectories to audit; and spending effort on sample efficiency for the few caught examples, since monitors were trained on offline examples and real caught ones plausibly improve them quickly. Take marks off for an answer that treats this as straightforwardly diffuse and stops at online training of the policy. Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many training samples a dozen bad actions provide) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### Question: Open
id:: 60b72d27-e3fa-4844-9a02-4849900709fc
content::
\#### The monitor that looks away

You use an untrusted model to select which of the policy's actions humans review, but you suspect that it systematically under-flags the most pertinent actions.

What does the post recommend for this case, and what limits the recommendation?
assessment-instructions:: Mark against the post's analysis. Full marks for the recommendation, red-teaming the monitor by inserting issues that are as subtle as possible into real outputs from the policy and checking they get flagged, plus the limit, which is the recognition problem: to under-flag safely, the monitor must distinguish the policy's natural bad actions from the ones you inserted, which is the same collusion problem as untrusted monitoring. Credit an answer that adds the post's difference from the high-stakes version: in a diffuse setting, catching only a subset of the policy's bad actions can suffice, so the collusion has to be reliable on the policy's real bad actions too, not just under red-teaming. Take marks off for naming red-teaming with no limit. Reply in at most 120 words, short paragraphs, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the monitor would have to tell apart in order to hide the policy's issues and still pass your tests) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

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
assessment-instructions:: Mark against one response the post's analysis supports: responding requires knowing what to expect, and that is the weak point. You need a prior over how suspicious a non-scheming model would look, and non-scheming models do objectively suspicious things. Generic sandbagging can hide inside that uncertainty, especially since nothing has trained the model to be less suspicious in-distribution. The evidence that should trigger a strong response will often be illegible, which makes the response politically hard to motivate. The post's design rule, aiming for low expected cost if the model is not malign, exists precisely because these triggers are noisy. Auditing-only is a real regime with real advantages, higher usefulness if the model is not scheming, but it buys them at the price of these detection gaps. Full marks for any two of those gaps, stated specifically rather than as a general worry. The rebuttal need not be fully dismissive: an answer that grants auditing's usefulness advantage and still names a specific gap scores full marks. Take marks off for an answer that only asserts the model could hide, with no reason drawn from the post. Reply in at most 100 words, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what number the deployer would have to compare the observed performance against) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### Question: Open
id:: 02d60f89-25f7-42f0-bd4e-5ad038c22651
content::
**The critic argues:** Online training against our oversight signal leads to systematic underperformance showing up in the loss and therefore gets trained away, so a scheming model is forced to behave exactly like a non-scheming one.

Write your counterargument in two or three sentences, at least 80 characters.
max-chars:: 450
placeholder:: Your response, in 2 to 3 sentences.
assessment-instructions:: Mark against one response the post's analysis supports: training forces the two closer, not identical. The schemer can still behave in ways whose oversight scores are only negligibly worse, and whether SGD removes such behavior depends on its sample efficiency relative to discrimination, which is an open question; inductive biases favoring scheming could preserve a small persistent offset. It can place rare subtle bad actions whose aggregate chance of discovery stays low. It can exploration hack or gradient hack. SGD may respond to training by making the sabotage sneakier and rarer rather than removing the scheming. Separately, online training may be unaffordable: training hard against your best available proxy can degrade non-scheming performance, and the process can teach the model what your oversight does and does not catch. Full marks for any two of those, stated specifically. Take marks off for an answer that only says "training is imperfect" without naming a mechanism. Reply in at most 100 words, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what happens to behavior whose oversight score is only negligibly lower) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### Question: Open
id:: c3ef6064-eb21-4d47-8918-19bb2dfcebbc
content::
**The critic argues:** Most sabotage in ML research is easy to verify once pointed out, and a debater is rewarded for pointing it out, so using a debater can prevent subtly bad actions from getting through.

Write your counterargument in two or three sentences, at least 80 characters.
max-chars:: 450
placeholder:: Your response, in 2 to 3 sentences.
assessment-instructions:: Mark against one response the post's analysis supports. The claim's premise is right: if exploration hacking is avoided, every potentially convincing issue gets raised, and verification-once-pointed-out is exactly the property that makes debate powerful for research sabotage. The gaps are that debaters can exploration hack, systematically declining to raise certain kinds of issues; that red-teaming them creates the same recognition problem as untrusted monitoring, and in a diffuse setting the collusion must be reliable on the policy's real bad actions, not just under red-teaming, since catching a subset can suffice for the deployer; and that the judge must have real signal on whether a pointed-out issue is genuine, because debaters will also raise fake issues whenever that persuades, while training the policy against debate trims false positives but also teaches the policy what debate catches. Full marks for any two gaps, stated specifically. Credit an answer that grants the premise before attacking. Take marks off for an answer that denies debate is useful at all, since the post calls it very powerful when exploration hacking is avoided. Reply in at most 100 words, no lists. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what a debater who does not want an issue found would simply do) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

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
assessment-instructions:: The learner picked one of five assumptions in the previous question and is now arguing against it. There is no single right answer; mark the argument, not the choice. Full marks require three things: the assumption is named and stated precisely enough to be false; the consequence is specific to that assumption rather than a general statement that control gets harder; and the learner names an observation or measurement that would tell a deployer whether the assumption holds. Credit arguments that use the post's machinery (the escape-probability product, SGD sample efficiency versus discrimination, exploration hacking, collusion and recognition, expected cost if benign) and credit an original argument that does not, as long as it is specific. Take marks off for restating the assumption in different words without an argument, and for an argument whose consequence would follow no matter which assumption failed. Reply in at most 120 words, short paragraphs, no lists: name the strongest part, then the weakest link, then one question that would test it. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the deployer in the post is doing that would stop working) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms. Grade only against what this page and earlier pages supplied.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Notes on Handling Non-Concentrated Failures with AI Control: High Level Methods and Different Regimes." *Redwood Research Blog*, Redwood Research, 29 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/notes-on-handling-non-concentrated)
*The reading itself, reproduced in full above: the high level methods for handling failures that arise from many diffuse actions, the regime each method produces, and how each regime fails.*

XLab. "Notes on handling non-concentrated failures with AI control." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/handling-non-concentrated-failures)
*The source lesson this page adapts.*
:::

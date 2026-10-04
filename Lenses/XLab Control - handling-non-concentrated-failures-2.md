---
id: '5c951c7f-b361-4f9e-af38-541b48bccc54'
title: "Notes on handling non-concentrated failures (2): forcing identical behaviour, and testing the methods"
tldr: "Online training pushes a schemer towards a non-schemer, but many near-optimal policies still leave room for subtle bad actions. Greenblatt's closing sections ask whether a KL penalty towards human imitation could close that room, and whether a schemer would ever prefer careful sabotage to well-placed errors. Then you use the whole post: place four failures on the concentrated-diffuse spectrum, and answer three confident claims that one method dissolves diffuse failures."
summary_for_tutor: "Part 2 of 2 of Ryan Greenblatt's 'Notes on handling non-concentrated failures with AI control'; part 1 is the lens handling-non-concentrated-failures, which read the post through debate (the two classes of methods, the no-online-training regime, online training of the policy and what a schemer can still get away with, the three regimes and the detection-race widget, and debate for binary questions and for oversight of a policy). This page reproduces the post's last two sections verbatim as one Article excerpt (KL penalties and forcing identical behaviour; whether careful sabotage is ever better for a schemer than inserting errors; then the post's footnotes, which belong to the debate section of part 1); everything before it is collapsed above the excerpt. Sequence: our opener; the excerpt; the four-scenario 'Which regime handles it?' exercise (one careful commit, quietly underdelivering, a dozen well-placed mistakes, the monitor that looks away), which draws on the whole post, not only this part; the three-round 'Responding to optimism about diffuse control' exercise with its closed Post toolbox, plus its own-argument construction step (choose an assumption, then argue). If the learner has not done part 1, the scenarios and rebuttals lean on its material: point them to the regimes, the list of what a schemer can get away with under online training, and the debate section. The exercise wording, the model answers inside the assessment briefs, and the toolbox come from the source lesson; the opener and the framing sentences are Lens-written. Do not hand out the model answers in the briefs before the learner has attempted the question."
reading_minutes: 5
tutor_minutes: 55
tags: []
---
#### Text
content::
Part 2 of 2. [[../Lenses/XLab Control - handling-non-concentrated-failures|The previous part]] read Ryan Greenblatt's notes through the section on debate: the two classes of methods, what a scheming model can still get away with under online training, the race between detection and catastrophe, and what debate forces on untrusted debaters. This part reads his two closing sections, on whether a KL penalty could force schemers and non-schemers to behave identically and on whether a schemer would ever choose careful sabotage over well-placed errors. Then you put the whole post to work: four failures to place on the concentrated-diffuse spectrum, and three confident claims to answer.

*By Ryan Greenblatt (Redwood Research). Reproduced verbatim, with permission, from [the original post on the Redwood Research blog](https://blog.redwoodresearch.org/p/notes-on-handling-non-concentrated) (March 29, 2025).*

#### Article
source:: [[../articles/greenblatt-notes-on-handling-non-concentrated-failures-with-ai-control-high-level-methods-and-different-regimes]]
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

Where does this sit on the concentrated-diffuse spectrum, and why? Which method could handle it, and why would reviewing the action afterwards or online training not handle it?
assessment-instructions:: Score out of 100. 40: placement: the concentrated (high-stakes) end, 25 for the placement and 15 for the reason, that a single action is enough for the catastrophe. 60: which method could handle it, 35: a measure that acts on the action before it takes effect, such as monitoring actions with a cheaper process, blocking suspicious actions for review, or cutting audit latency; any one such measure earns the 35; 25: why review after the fact or online training would not handle it: they come too late, since the damage lands with the one action and there is no repeated behaviour to train away. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer proposes online training as the fix without noticing that it comes too late. Model answer, for the feedback, not a grading checklist: "This is on the concentrated end: catastrophe arrives in one action, so asynchronous review is too late by construction, and online training has nothing to work with (there is no repeated behavior to train away before the damage lands). What handles it is acting before the action takes effect: select what to review with a cheaper process applied more often, block suspicious actions for review, or cut auditing latency."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many bad actions the deployer gets to review before the damage lands) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 992ae249-8438-4589-bb21-258b544ced73
content::
\#### Quietly underdelivering

Across months, your model performs slightly worse on alignment research than it should. There aren't any specific instances you can point to, there's just worse performance overall.

Where does this sit on the spectrum, and which method fits best? What risks does that method leave open?
assessment-instructions:: Score out of 100. 25: placement: the far diffuse end, since the harm is spread thinly over many actions with no single incident. 35: the method: online training, sampling some of the model's work, rating it and training on the rating, which pushes the scheming model's performance toward what a non-scheming model would deliver. 40: residual risks, 20 each for up to two that the answer explains, such as: underperformance so small on each sample that training barely pushes against it; exploration or gradient hacking; training making the sabotage sneakier and rarer instead of removing it; and, if auditing alone is used instead, not knowing what performance an honest model would deliver, so sandbagging hides in that uncertainty. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "This is the far diffuse end, and it is the case asynchronous online training was made for: sampling a fraction of actions, rating them, and training on the rating forces the scheming model's behavior toward a non-schemer's on the trained metric. The residual risks are the post's list of what a schemer can still get away with: degradation too small per sample for SGD to push against, exploration or gradient hacking, and, if you rely on auditing alone instead, the problem that you do not know what performance a non-scheming model would deliver, so sandbagging can hide inside that uncertainty."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what a rating on a sampled action can be used for besides reading it) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 576e3319-799f-46b3-aecf-3846279c48c4
content::
\#### A dozen well-placed mistakes

The model makes occasional honest-looking mistakes at unusually damaging moments. Each is plausibly deniable, and there are perhaps a dozen across the whole deployment.

Where does this sit, and which of the post's levers matter most here?
assessment-instructions:: Score out of 100. 40: placement: in the middle, between the concentrated and diffuse ends, 25 for the placement and 15 for the reason: a dozen bad actions give almost no training signal against the policy, yet none of them is decisive on its own. 60: levers, 30 each for up to two, such as: training the monitoring models online on the few real bad actions; choosing the most informative (most suspicious) trajectories to audit rather than random ones; and getting the most out of the few caught examples (improving sample efficiency, for example by proliferating them). Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer treats this as plainly diffuse and relies only on online training of the policy. Model answer, for the feedback, not a grading checklist: "The middle of the spectrum, and the hardest case. A dozen actions provide almost no training signal against the policy, and no single incident is decisive, so the governing constraint is the product of per-action escape chances staying high. The post's levers for exactly this regime: online training of monitoring models (most important when there are enough bad actions that training the monitor helps but too few for random sampling to encounter many), selecting the most informative trajectories to audit, and spending effort on sample efficiency for the few caught examples, since monitors were trained on offline examples and real caught ones plausibly improve them quickly."
feedback-instructions:: Reply in at most 150 words, short paragraphs, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask how many training samples a dozen bad actions provide) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 60b72d27-e3fa-4844-9a02-4849900709fc
content::
\#### The monitor that looks away

You use an untrusted model to select which of the policy's actions humans review, but you suspect that it systematically under-flags the most pertinent actions.

What does the post recommend for this case, and what limits the recommendation?
assessment-instructions:: Score out of 100. 50: the recommendation: red-team the monitor by inserting issues, as subtle as possible, into real outputs of the policy and checking that the monitor flags them. 50: the limit: a monitor that can tell the inserted issues apart from the policy's own bad actions can flag the first and hide the second, so red-teaming only works if it cannot recognise them, the same collusion problem as in untrusted monitoring. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Red-team the monitor: insert issues that are as subtle as possible into real outputs from the policy and check they get flagged. The limit is the recognition problem: to under-flag safely, the monitor must distinguish the policy's natural bad actions from the ones you inserted, which is the same collusion problem as untrusted monitoring. The post notes one difference from the high-stakes version: in a diffuse setting, catching only a subset of the policy's bad actions can suffice, so the collusion has to be reliable on the policy's real bad actions too, not just under red-teaming."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the monitor would have to tell apart in order to hide the policy's issues and still pass your tests) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

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

Write your counterargument in two or three sentences, at least 80 characters, naming two separate weaknesses of the claim.
max-words:: 80
placeholder:: Your response, in 2 to 3 sentences, with two weaknesses.
assessment-instructions:: Score out of 100. 50 each, for two specific weaknesses of relying on auditing alone that the answer explains, such as: there is no reliable baseline for how well, or how unsuspiciously, an honest model would perform, so a small performance drop can hide inside that uncertainty; honest models also do suspicious-looking things and nothing trained the model to look less suspicious, so triggers are noisy and costly responses must be rare; the evidence that should trigger a response will often be illegible, making a strong response hard to justify. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only asserts that the model could hide, with no reason. Model answer, for the feedback, not a grading checklist: "Responding requires knowing what to expect, and that is the weak point: you need a prior over how suspicious a non-scheming model would look, and non-scheming models do objectively suspicious things. Generic sandbagging can hide inside that uncertainty, especially since nothing has trained the model to be less suspicious in-distribution. And the evidence that should trigger a strong response will often be illegible, which makes the response politically hard to motivate. The post's design rule, aiming for low expected cost if the model is not malign, exists precisely because these triggers are noisy. Auditing-only is a real regime with real advantages (higher usefulness if the model is not scheming), but it buys them at the price of these detection gaps."
feedback-instructions:: Reply in at most 100 words, no lists. Say what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what number the deployer would have to compare the observed performance against) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: 02d60f89-25f7-42f0-bd4e-5ad038c22651
content::
**The critic argues:** Online training against our oversight signal leads to systematic underperformance showing up in the loss and therefore gets trained away, so a scheming model is forced to behave exactly like a non-scheming one.

Write your counterargument in two or three sentences, at least 80 characters, naming two different ways a scheming model could still get through online training.
max-words:: 80
placeholder:: Your response, in 2 to 3 sentences, with two ways.
assessment-instructions:: Score out of 100. 50 each, for two different mechanisms the answer gives by which a scheming model can survive online training, such as: bad behaviour that is only slightly worse on the oversight signal, so it barely shows in the loss and training may not remove it; rare, subtle bad actions that are unlikely to be noticed; exploration or gradient hacking, so the bad behaviour never produces a training signal; training making the sabotage sneakier and rarer instead of removing the scheming; or online training being unaffordable, because training hard on the available proxy degrades an honest model's work or teaches the model what oversight catches. Each mechanism counts in full when the answer states it in a clause or a sentence; the question allows only two or three sentences. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer only says training is imperfect without naming a mechanism. Model answer, for the feedback, not a grading checklist: "Training pushes a schemer closer to a non-scheming model, not all the way: bad behaviour that is small or rare barely shows in the loss and may never be trained away, and training may just make the sabotage sneakier."
feedback-instructions:: Reply in at most 130 words, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what happens to behavior whose oversight score is only negligibly lower) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### Question: Open
id:: c3ef6064-eb21-4d47-8918-19bb2dfcebbc
content::
**The critic argues:** Most sabotage in ML research is easy to verify once pointed out, and a debater is rewarded for pointing it out, so using a debater can prevent subtly bad actions from getting through.

Write your counterargument in two or three sentences, at least 80 characters, naming two separate gaps in the claim.
max-words:: 80
placeholder:: Your response, in 2 to 3 sentences, with two gaps.
assessment-instructions:: Score out of 100. 50 each, for two specific gaps the answer explains, such as: the debaters are untrusted and can exploration hack by never raising certain kinds of issues; red-teaming the debaters with inserted issues only works if they cannot tell those apart from the policy's real ones, the same collusion problem as untrusted monitoring; the judge must be able to tell real issues from fake ones, since debaters also raise fake issues whenever that persuades; training the policy against debate teaches it what debate catches. Each item in this list counts as a separate gap, so an answer giving exploration hacking and the red-teaming recognition problem has two. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer denies that debate is useful at all. Model answer, for the feedback, not a grading checklist: "If exploration hacking is avoided, every potentially convincing issue gets raised, and verification-once-pointed-out is exactly the property that makes debate powerful for research sabotage. Debaters can exploration hack, systematically declining to raise certain kinds of issues. Red-teaming them creates the same recognition problem as untrusted monitoring, and in a diffuse setting the collusion must be reliable on the policy's real bad actions, not just under red-teaming, since catching a subset can suffice for the deployer. And the judge must have real signal on whether a pointed-out issue is genuine, because debaters will also raise fake issues whenever that persuades; training the policy against debate trims false positives but also teaches the policy what debate catches."
feedback-instructions:: Reply in at most 130 words, no lists. Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what a debater who does not want an issue found would simply do) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

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
max-words:: 150
assessment-instructions:: Score out of 100. There is no single right choice; grade the argument. 25: the assumption is named and stated precisely enough that it could be false. 45: what breaks if it is false, specific to this assumption rather than a general statement that control gets harder. 30: an observation or measurement that would tell a deployer whether the assumption holds. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer restates the assumption in other words without an argument. Model answer, for the feedback, not a grading checklist: "One example: the assumption that a non-scheming performance baseline can be estimated well enough to set thresholds. If it is false, a deployer relying on auditing has nothing reliable to compare the observed performance against: a schemer can sandbag by less than the uncertainty in the baseline, and a threshold tight enough to catch it would also fire on an honest model that is simply weak, so the deployer either tolerates the sandbagging or pays for constant false alarms. To find out, the deployer could check how much a little online training or changed instructions improves performance in a domain: a large jump shows the model was performing below what it can do."
feedback-instructions:: Reply in at most 120 words, short paragraphs, no lists: name the strongest part, then the weakest link, then one question that would test it. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the reading (for instance, ask what the deployer in the post is doing that would stop working) rather than repeating the question; if their next message still does not attempt it, rephrase the whole question in different terms.

#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan. "Notes on Handling Non-Concentrated Failures with AI Control: High Level Methods and Different Regimes." *Redwood Research Blog*, Redwood Research, 29 Mar. 2025. [blog.redwoodresearch.org](https://blog.redwoodresearch.org/p/notes-on-handling-non-concentrated)
*The reading itself: this part reproduces its two closing sections, on KL penalties and on careful sabotage; the rest is in part 1.*

XLab. "Notes on handling non-concentrated failures with AI control." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/low-stakes-control/handling-non-concentrated-failures)
*The source lesson this page adapts, including the scenario and rebuttal exercises and the post toolbox.*
:::

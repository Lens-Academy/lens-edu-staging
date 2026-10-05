---
id: '7367ce67-c192-48f0-8080-4c0f28f486f6'
title: "What control is"
tldr: "Banks do not try to guarantee that no employee ever goes rogue. They build systems that hold even when one does. Greenblatt and Shlegeris ask what happens if you treat a powerful AI model the same way: assume it might be scheming, and set things up so it still cannot cause a catastrophe."
summary_for_tutor: "Lens in Unit 1 of AI Control Fundamentals, adapted from the Advanced AI Control lens 'The case for control (1)'. Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', from the opening of the post through the first paragraphs of 'Evaluating whether you have control is doable'. Each part of the reading is followed by the question about it. (1) The opening up to the two lines of defense (alignment and control), then a quick recall on what distinguishes control from alignment. (2) The rest of the opening (why control is worth arguing for, transformatively useful AI, counting a caught AI as a win, evaluating control with capability evaluations), then a quick recall on what transformatively useful AI means and why control is aimed at it, and an optional closed question on why catching a model red-handed counts as a win. (3) The section 'The control property' with the security analogy, then a quick recall on what the control property means. (4) The first paragraphs of 'Evaluating whether you have control is doable' (the two-step evaluation approach, and treating models as untrusted if they pass capability evaluations), then a quick recall on how to decide which models are untrusted. (5) A scenario exercise with three setups (no safeguards, trusted monitoring with a weaker trusted model T and 2% human audits, untrusted monitoring by a copy of U), each asking whether the setup holds the control property and what that depends on. Two further setups (trusted editing, resampling) sit in a closed optional box. The learner has watched Robert Miles's video on the founding control paper just before this lens. The next lens continues the same post: how a red team runs a control evaluation and why alignment cannot yet be checked the same way."
reading_minutes: 13
tutor_minutes: 22
glossary_terms:
  - "[[../glossary/Scheming]]"
  - "[[../glossary/Control evaluation]]"
  - "[[../glossary/Collusion]]"
  - "[[../glossary/Trusted model]]"
---
#### Text
content::
This is a founding post of AI control, by Ryan Greenblatt and Buck Shlegeris of Redwood Research (2024). Its opening sets control beside alignment as a second line of defence, which you already met in the CSET explainer, so that part is optional and folded below. Then the post defines the control property and says which models to treat as untrusted, with a short recall question after each part. Then you test three deployment setups yourself. Two more setups are optional at the end.

#### Callout: Optional: the opening of the post (two lines of defence, transformatively useful AI)
collapse:: closed
#### Article
optional:: true
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
to:: argue that it might be tractable to use control to substantially reduce risk.

#### Question: Open
optional:: true
id:: 82bc48d1-8dd9-4c85-b867-982318eb2e44
content:: What distinguishes the control line of defense from the alignment line of defense against scheming AIs?
assessment-instructions:: Score out of 100. 50: alignment tries to make sure the models are not scheming in the first place. 50: control tries to make sure that even if the models are scheming, they are not able to subvert the safety measures and cause a catastrophe. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Alignment aims to ensure that models are not scheming in the first place. Control aims to ensure that even if models are scheming, they are not capable of subverting the safety measures. With both lines in place, a scheming model can only cause a catastrophe if alignment and control both fail."
force-feedback:: first
feedback-instructions:: In at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it, in your own words if it is long. Alignment ensures models are not scheming. Control ensures that even if they are scheming, they cannot subvert the safety measures. With both, a catastrophe requires both to fail. No follow-up questions. Tell them to move on.

#### Article
optional:: true
from:: One difficulty we face when arguing for control
to:: Because control could be applied to mitigate risk from scheming right now, it's a particularly promising target for research effort and policy commitments.

#### Question: Open
optional:: true
id:: d3436a3e-f4ab-4dce-b452-dec7fca0af5c
content:: What do Greenblatt and Shlegeris mean by "transformatively useful AI", and why do they aim control at those AIs rather than at arbitrarily powerful ones?
assessment-instructions:: Score out of 100. 50: the meaning: AIs capable of substantially reducing risk from the more powerful AIs that come after them, for example by greatly speeding up AI safety research. 50: why aim there: the authors do not expect control to work for arbitrarily powerful AIs, but think it could work for the first AIs that are this useful. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Transformatively useful AIs are AIs capable of substantially reducing risk from the AIs that come after them, for example by massively speeding up AI safety research. The authors do not think control can work for arbitrarily powerful AIs, but they think it could work for these first transformatively useful ones, so that is where they aim it."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Transformatively useful AIs are AIs capable of substantially reducing risk from later AIs, for example by speeding up safety research. The authors expect control to fail for arbitrarily powerful AIs but to be workable for these first ones. No follow-up questions. Tell them to move on.

#### Question: Open
optional:: true
id:: 098d5fa2-9ad2-409e-9a51-0d327a3d58fd
content::
\#### Catching a model red-handed

The reading claims that when evaluating control, catching an AI red-handed should count as a win condition. The same status as no catastrophe occurring at all. On its face this is strange: the model just tried to cause a catastrophe and was stopped this once. It is presumably still scheming, still deployed, still capable.

Why should catching a scheming model count as a win, when a near miss with catastrophe might seem more like a failure? Answer by naming two things that change after a catch.
placeholder:: Write your reasoning
assessment-instructions:: Score out of 100. 50 for each of two different consequences of a catch that make the lab better off, up to 100. Any two of these count: (a) the evidential shift: before a catch, scheming is an unconfirmed risk that can be doubted or denied. After it, there is concrete proof that scheming really happens, so calls to pause or shut down until safety catches up get far more support. (b) the lab has a concrete incident to study, for example by resampling the model in the same situation and examining what it tried, and can strengthen its protocols. (c) the caught model has to be far more covert from then on, which makes further high-stakes attempts harder. Another real consequence that makes the lab better off, argued, also counts. Two consequences that are the same idea in different words count once. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Before a catch, serious misalignment and dangerous scheming are an unconfirmed risk. After a catch, scheming becomes a demonstrated phenomenon that has occurred naturally. Efforts to pause or shut down models till safety research catches up will gain much more support and evidence. A catch also yields a concrete incident to study. Labs can resample the model in its environment, examine what it tried, and strengthen their control protocols. From the model's perspective, being caught means that it has to be much more covert to avoid being caught, which might prevent high-stakes risks. Catching a model turns a diffuse, deniable, uncertain risk into legible, undeniable evidence."
force-feedback:: first
feedback-instructions:: In at most six sentences, name what the learner's reasoning got right, then supply anything they missed from this list: after a catch, scheming stops being an unconfirmed risk and becomes a demonstrated phenomenon, so pausing gains support and evidence. The catch is a concrete incident to study, and the model can be resampled in its environment to harden protocols. The caught model must now be far more covert, which itself suppresses high-stakes attempts. A catch converts a diffuse, deniable risk into legible evidence. Close by telling them that Unit 3 comes back to why catching a model matters.
#### End Callout

#### Article
from:: # The control property
to:: it focuses attention on the types of interventions whose effectiveness is easiest to reason about.

#### Callout: Quick recall
#### Question: Open
id:: cf059567-5f9d-4cbc-b766-8f931f67a70e
content:: What does it mean for a set of safety techniques to have the control property?
assessment-instructions:: Score out of 100. 50: the safety comes from the techniques, not from the model's choices: even a model that is actively trying cannot find and carry out a strategy that gets around them. An answer that only says the model is unlikely to cause the outcome even if it is scheming, without saying that the techniques are what stop it, earns 30 of these 50. 20: this has to hold for models that may be misaligned and scheming. 30: the threshold: any such strategy has at most a small probability of an unacceptable outcome, such as the model exfiltrating its weights or hacking the datacenter. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer describes the model behaving safely in normal use, with no idea of it trying and failing. Model answer, for the feedback, not a grading checklist: "Potentially scheming models are not capable of finding and executing a subversion strategy that has more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter."
force-feedback:: first
feedback-instructions:: In at most four sentences: confirm what the learner got right and, if anything is missing or wrong, the most important thing, then state the model answer so they leave with it. A set of techniques has the control property when potentially scheming models are not capable of finding and executing a subversion strategy with more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter. No follow-up questions. Tell them to move on.
#### End Callout

#### Article
from:: # Evaluating whether you have control is doable
to:: See [here](https://www.alignmentforum.org/posts/LhxHcASQwpNa3mRNk/untrusted-smart-models-and-trusted-dumb-models) for more discussion.[^note-greenblatt-buck-7]

#### Callout: Quick recall
#### Question: Open
id:: 0f51149d-04a7-4b37-a811-9b57f9ee878f
content:: How can a lab decide which of its models to treat as untrusted, and why that way?
assessment-instructions:: Score out of 100. 40: capability is the criterion, because lack of capability is the only known way to confidently rule out scheming without fundamental breakthroughs. 35: models that pass the relevant capability evaluations are treated as untrusted. 25: only models clearly too weak to plausibly be scheming are treated as trusted. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer inverts the test, saying that passing the capability evaluations makes a model trusted. Cap at 30 if the answer decides trust by how well the model behaves in tests or in use, since a schemer would behave well there too. Model answer, for the feedback, not a grading checklist: "The only known way to confidently rule out scheming without fundamental breakthroughs is lack of capability. Models that pass the relevant capability evaluations are treated as untrusted; models that are clearly too weak to plausibly be scheming can be treated as trusted."
force-feedback:: first
feedback-instructions:: In at most three sentences: confirm what the learner got right, correct any inversion of the test, and state the model answer. Lack of capability is the only known way to rule out scheming without fundamental breakthroughs, so a model that passes the relevant capability evaluations is treated as untrusted, and only models clearly too weak to plausibly be scheming are treated as trusted. No follow-up questions. Tell them to move on.
#### End Callout

#### Callout: Scenario exercise: run the evaluation
#### Text
content::
You have just seen what makes a model untrusted and the two steps of a control evaluation. Now run one yourself: three deployment setups, the same question each time.

First, meet the cast.

| | Who | What they are |
| --- | --- | --- |
| **U** | the untrusted model | A frontier model that is highly capable, enough to be capable of scheming. |
| **T** | the trusted model | An older, much weaker model that isn't capable of scheming effectively, so its work is honest but not as good as U. |
| **H** | human auditors | Honest and skilled, but scarce: they can only ever look at a small fraction of any work. |

:::callout {title="The question, every time" tone="neutral"}
Assuming U is actively scheming, does this setup hold the control property? What variables and conditions dictate whether this is the case?
:::

\#### Scenario 1: straight to production

U writes production code and merges its own commits. No review of any kind.

#### Widget
source:: [[../widgets/xlab-control-eval-s1-no-safeguards]]

#### Text
content::
**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 6e78d227-1874-4059-b64b-1635c24bfa39
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: Score out of 100. 50: the verdict with its reason: the setup does not hold the control property, because nothing checks what U does before its code reaches production. 50: what it depends on: here nothing in the setup protects you, so whether malicious code gets merged depends only on U itself, on whether U is scheming (willing) and able to write it. Safety then rests on alignment, not on control. An answer that says it depends only on U's intentions or capability, or that it is safe only if U is not scheming, earns the full 50. The phrase "worst case" is not required. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says the setup holds the control property, or that it holds as long as U has behaved well so far. Model answer, for the feedback, not a grading checklist: "No. Nothing stands between U and production, so if U is scheming its malicious code goes straight through. The setup is safe only if U happens not to be trying, which is relying on alignment, not on control. The control property is judged on the worst case, so U's good track record or benchmark scores do not change the verdict."
force-feedback:: first
feedback-instructions:: In at most five sentences, tell the learner what their answer got right and, if anything is missing or wrong, the most important thing, then give the resolution: no safeguards. The control property conditions on the worst case, so a scheming U's attacks are unmoderated here, and evidence about U's reliability, benchmark scores or past helpfulness does not enter, because control evaluations assume worst-case adversarial behavior by default.

#### Text
content::
\#### Scenario 2: every edit is monitored

Every edit U produces is scored for suspicion by T. The top 2% go to H, who revise or block anything potentially malicious. Everything else merges into production.

#### Widget
source:: [[../widgets/xlab-control-eval-s2-trusted-monitoring]]

#### Text
content::
**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 16d44bda-4433-43d4-9088-fd72d0b97b0f
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: Score out of 100. Setup: every edit the untrusted model U produces is given a suspicion score by the weaker trusted model T; only the most suspicious 2% are audited by humans, who block anything malicious; everything else merges into production. 20: the verdict is conditional: control can hold, but it is not guaranteed. 80: what it depends on: whether T is good enough to recognise U's attacks as suspicious, so they land in the small audited share, which depends on how far U outstrips T; a scheming U much more capable than T can disguise an attack so that it scores low and slips through unaudited. Cap at 30 if the answer says the setup holds simply because every edit is monitored, with no condition on T's ability to spot attacks. Model answer, for the feedback, not a grading checklist: "Not necessarily. It holds only if T is capable enough to score U's covert attacks as suspicious enough to reach the 2% that gets audited. If U is much more capable than T, U can disguise its attacks well enough to stay among the edits that merge without review."
force-feedback:: first
feedback-instructions:: In at most six sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is trusted monitoring. Control holds only if T is capable enough to score U's covert attacks into the 2% audit bracket. A large enough capability gap between U and T bottlenecks T's detection, and a scheming U can then obfuscate an attack into the bottom 98%. Trusted monitoring is cheap and can be repeated to drive the probability down, but that is not a guarantee.

#### Text
content::
\#### Scenario 3: a reviewer that can keep up

U's research code has outgrown T, and T's scores on it look like noise. Instead, a second copy of U (call it U′) scores every action. The top 2% go to H before execution.

#### Widget
source:: [[../widgets/xlab-control-eval-s3-untrusted-monitoring]]

#### Text
content::
**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 0983cfd6-876e-4c73-8e81-58318c1abedf
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: Score out of 100. 55: the failure mode and verdict: U′ can collude with U, giving U's malicious edits low suspicion scores so they never reach H, and the malicious code merges, so the setup does not hold the control property. 45: why that must be assumed: U′ is an identical copy of U, so under the worst-case assumption of the control property, if U is scheming U′ is scheming too; whether control holds depends on whether the monitor can be trusted, and a copy of U cannot. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says the setup holds because U′ is capable enough to catch U's attacks, without asking whether U′ can be trusted. Model answer, for the feedback, not a grading checklist: "Under the worst-case assumptions of the control property, if U is scheming, we must assume its identical copy, U′, is also scheming. Instead of rigorously auditing U's code, a scheming U′ will simply collude with U, artificially lowering the suspicion score on malicious edits to guarantee they bypass the human auditor. By upgrading the monitor to a frontier model, we have solved the capability gap but introduced a fatal vulnerability in allegiance."
force-feedback:: first
feedback-instructions:: In at most six sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is untrusted monitoring. Worst-case assumptions force us to treat U′ as scheming too, so it can simply collude with U and score malicious edits low enough to bypass H. The capability gap is solved and a fatal vulnerability in allegiance is introduced in its place. If the learner mentions Miles's countermeasures, agree that the paper made untrusted monitoring much safer with them (fake backdoors to test the monitor, blocking secret signals), and point out that this set-up has none of them.

#### Question: Open
id:: a126f748-1d71-4ce2-89b3-115c5ad6f6c9
content::
A new set-up. An AI lab lets its newest model, which counts as untrusted, manage the cluster that runs its experiments. The model starts and stops jobs and moves files between storage buckets, including the bucket that holds the lab's model weights. A weaker trusted model scores every command the model issues, and an on-call engineer reviews the 2% most suspicious commands the next morning.

1. What is the unacceptable outcome this set-up must prevent? Be specific to this deployment.
2. Name one assumption the set-up rests on that might not hold, or one gap it leaves open even when the trusted model and the engineer do their jobs.
assessment-instructions:: Score out of 100. Part 1, 50 points: a specific unacceptable outcome for this deployment, such as the model copying its own weights (or another model's) out of the lab, or using the cluster to run its own unauthorised jobs (a rogue internal deployment). 25 for a generic answer such as "something bad happens" or "the model misbehaves" with no link to the cluster or the weights. Part 2, 50 points: one assumption or gap tied to this set-up, explained. Fitting answers include: the review happens the next morning, too late for a one-shot action such as copying weights out, so a catch comes after the harm. The weaker trusted model may not recognise a subtle harmful command, such as a file move that looks routine. The model could spread an attack over many commands that each look harmless. The lab assumes its tests measured what the model can really do, but the model may have hidden its abilities. Nothing says what happens after a catch. Any other assumption or gap that genuinely applies to this set-up earns the same credit. 20 for a generic limit not tied to this set-up. Give credit whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "1. The model copying the weights out of the lab, or quietly running its own jobs on the cluster. 2. The engineer looks only the next morning, so if the model copies the weights out in one command, the catch comes after the harm is done."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. If they named only a generic outcome, point them to what this model can touch (the cluster and the weights bucket). If they named another attack that slips past the monitor, say that part 2 wanted an assumption or gap, for example that the review comes the next morning. No follow-up question. No generic praise.
#### End Callout

#### Callout: Optional: two more setups
collapse:: closed
#### Text
optional:: true
content::
\#### Scenario 4: rewrite the doubtful ones

T scores every edit. The top 2% go to H to audit. The next 10%, suspicious but not audit-worthy, are not merged as written: T rewrites them itself and merges its own version. The bottom 88% merge untouched.

#### Widget
source:: [[../widgets/xlab-control-eval-s4-trusted-editing]]

#### Text
optional:: true
content::
**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: c173b895-663d-464e-ae1b-57a5eff44aff
optional:: true
content:: Does this setup hold the control property? What does that depend on? Then say how T rewriting the next 10% changes what an attack has to do to get merged as U wrote it.
assessment-instructions:: Score out of 100. Setup: the weaker trusted model T scores every edit by the untrusted model U; the most suspicious 2% go to human auditors; the next 10% are not merged as written but rewritten by T, which merges its own version; the bottom 88% merge untouched. 50: the change: because T rewrites the next 10% itself, an attack now has to avoid both the audit band and the rewrite band (score in the bottom 88% of T's suspicion scores, not just the bottom 98%) to be merged as U wrote it, so the window for an attack to slip through is narrower. 50: the verdict and what it depends on: control can hold but is not guaranteed; full points for either dependency: T must still rank a well-disguised attack as suspicious, so a large capability gap between U and T still threatens control; or how much of the work T takes over, since a wider band that T rewrites narrows the window further, buying safety at the cost of U's usefulness. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Because T steps in to rewrite the ambiguously suspicious outputs of U (the 10% band), U's attack must now score in the bottom 88% to avoid being overwritten. By forcing T to do a portion of the actual work, this setup drastically narrows the window for an attack to slip through. Generally, you can reliably buy more safety by dynamically shifting the workload back to weaker, trusted models, at the cost of trading away some of U's usefulness."
force-feedback:: first
feedback-instructions:: In at most six sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is trusted editing, a more robust variant of trusted monitoring. An attack must now land in the bottom 88% rather than the bottom 98%, because T rewrites the 10% band itself, which drastically narrows the window for an attack. The general lesson: safety can be bought reliably by shifting workload back to weaker trusted models, paid for in U's usefulness.

#### Text
optional:: true
content::
\#### Scenario 5: rewind and ask again

U works through multi-step tasks on the research cluster, one command at a time. Before each command runs, T scores it for suspicion. Low suspicion and it executes. High suspicion and it does not run: the system rewinds and resamples the step from U again, with a maximum of three tries, and U keeps no memory between tries. If the retries also look suspicious, the whole bundle goes to H. Otherwise the least suspicious retry executes and the task moves on.

#### Widget
source:: [[../widgets/xlab-control-eval-s5-resampling]]

#### Text
optional:: true
content::
**Unacceptable outcome:** Model weights leave the cluster.

#### Question: Open
id:: 58968fa3-60c2-4a82-a12a-6d6d7fd63935
optional:: true
content:: Does this setup hold the control property? What does that depend on? Then say what resampling does to a scheming U in two cases: U attacks on every try, or U attacks only rarely.
assessment-instructions:: Score out of 100. Setup: before each command the untrusted model U proposes runs, the weaker trusted model T scores it for suspicion; a suspicious command does not run, and the step is rewound and resampled from U, up to three tries, with U keeping no memory between tries; if the retries also look suspicious, the whole bundle goes to human auditors H, otherwise the least suspicious retry runs. Unacceptable outcome: model weights leave the cluster. 30: the verdict and what it depends on: control can hold but is not guaranteed; it holds only if T can flag U's attacks as suspicious in the first place, so the capability gap between U and T must not be too large. 35: if U attacks on every try, its retries are attacks too, and several suspicious attempts are far stronger evidence than one, so the bundle goes to H and U is likely caught. 35: if U attacks only rarely, a flagged attack is simply replaced by a resampled benign action, so the attack does not run. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer says the setup holds the control property whatever T is able to detect. Model answer, for the feedback, not a grading checklist: "The core principle of this protocol is that U keeps no memory across retries. A rewound U doesn't know its first attempt was flagged. For an attack to survive a resample, the retries must also be attacks. However, three independent draws of malicious commands are far stronger evidence than one, and thus greatly increases the probability of being audited by H and being caught. If instead U doesn't attack as often, whenever T flags one attempt, a resample draws U's benign output and executes that instead. Thus U is forced to incriminate itself or remain benign. Thus the control property holds if there isn't a sufficiently large capability gap between U and T."
force-feedback:: first
feedback-instructions:: In at most seven sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is resampling. Because U keeps no memory across retries, a rewound U does not know it was flagged, so surviving a resample requires the retries to be attacks too, and three independent malicious draws are far stronger evidence than one. If U attacks rarely instead, a resample simply draws its benign output and runs that. U is pushed either to incriminate itself or to stay benign, and the control property holds provided the capability gap between U and T is not too large.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from. This lesson covers the opening of the post through the start of "Evaluating whether you have control is doable": the control property, control versus alignment, and how to decide which models are untrusted.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts, including the scenario exercise.*
:::

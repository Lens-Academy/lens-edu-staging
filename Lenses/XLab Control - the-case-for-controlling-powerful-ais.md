---
id: '564a803d-0bf4-4dc7-8321-97a3d973331d'
title: "The case for control (1): what control is, and putting five setups to the test"
tldr: "Serious companies do not try to guarantee that no employee is ever compromised. They build systems that hold even when one is. Greenblatt and Shlegeris ask what happens if you treat a frontier model the same way: assume it is scheming, and design so that it still cannot hurt you. This first part defines control and then has you judge five deployment setups against it."
summary_for_tutor: "First of four lenses on Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', and the foundation nearly every later lesson refers back to. It runs from the opening of the post through the first paragraphs of the section 'Evaluating whether you have control is doable' (the two-step evaluation approach and how to decide which models are untrusted), as Article excerpts with two exercise blocks in their original positions. The next lens, 'The case for control (2)', resumes mid-section with how a red team runs a control evaluation, why alignment cannot yet be evaluated the same way, black-box techniques and what control techniques look like; 'The case for control (3)' covers whether the first transformatively useful AIs will already be too capable to control, and '(4)' why evading careful control is hard without wildly superhuman skill, how long the control window lasts, and the implications. The argument here, in order: (1) alignment and control are two distinct lines of defense against scheming, and a catastrophe requires both to fail; (2) the control property: potentially scheming models cannot find and execute a subversion strategy with more than a small probability of an unacceptable outcome, handled the way security teams handle compromised employees; (2b) control is evaluable because it reduces to a capability question: 'Because evaluating control just requires evaluating capabilities, it's far easier to robustly evaluate than alignment' (stated in the opening summary, art. l.44; the red-team mechanics and the contrast with alignment come in the next lens, so answer a 'why is control easier to evaluate' question at that level: you only have to show what the model cannot do, not what it wants); (3) control should focus on the lead-up to the first time an AI is caught, so catching an AI red-handed counts as a win condition, because a catch makes the misalignment problem undeniable and shutting down far more likely (stated here in the opening section; the reasoning prompt asking the learner to explain why comes in the next lens); (4) a control evaluation starts by deciding which models are untrusted, and the only known way to rule out scheming is lack of capability. Vocabulary the learner meets here and will need everywhere later: scheming, the control property, untrusted versus trusted models, protocol, control evaluation, catching red-handed. The exercise blocks are: a recall on control versus alignment; and a five-scenario control evaluation (no safeguards, trusted monitoring, untrusted monitoring, trusted editing, resampling), which is where the protocol vocabulary is actually built. The red-team mechanics and the three disadvantages a scheming AI has against the red team come in the next lens, so do not lean on them here. If a learner is stuck on a scenario, ask what the monitor can actually see and who it is loyal to, rather than naming the protocol for them."
reading_minutes: 16
tutor_minutes: 38
tags: []
---
#### Text
content::
Part 1 of 4. This is the founding text of AI control, and it is long, so it runs across four lessons. This part defines control, sets it beside alignment, and then has you put five deployment setups to the test yourself. The next part follows the authors through how a control evaluation actually works and why alignment cannot yet be checked the same way. Two exercise blocks break up the reading; answer each before you move on, even roughly.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
to:: it focuses attention on the types of interventions whose effectiveness is easiest to reason about.

#### Callout: Quick recall
#### Question: Open
id:: 82bc48d1-8dd9-4c85-b867-982318eb2e44
content:: What distinguishes the control line of defense from the alignment line of defense against scheming AIs?
assessment-instructions:: Score out of 100. 50: alignment tries to make sure the models are not scheming in the first place. 50: control tries to make sure that even if the models are scheming, they are not able to subvert the safety measures and cause a catastrophe. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Alignment aims to ensure that models are not scheming in the first place. Control aims to ensure that even if models are scheming, they are not capable of subverting the safety measures. With both lines in place, a scheming model can only cause a catastrophe if alignment and control both fail."
feedback-instructions:: In at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it, in your own words if it is long. Alignment ensures models are not scheming. Control ensures that even if they are scheming, they cannot subvert the safety measures. With both, a catastrophe requires both to fail. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # Evaluating whether you have control is doable
to:: See [here](https://www.alignmentforum.org/posts/LhxHcASQwpNa3mRNk/untrusted-smart-models-and-trusted-dumb-models) for more discussion.[^note-greenblatt-buck-7]

#### Callout: Scenario exercise: run the evaluation
#### Text
content::
You have just seen what makes a model untrusted and the two steps of a control evaluation. Now run one yourself: five deployment setups, the same question each time.

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
feedback-instructions:: In at most six sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is trusted monitoring. Control holds only if T is capable enough to score U's covert attacks into the 2% audit bracket; a large enough capability gap between U and T bottlenecks T's detection, and a scheming U can then obfuscate an attack into the bottom 98%. Trusted monitoring is cheap and can be repeated to drive the probability down, but that is not a guarantee.

#### Text
content::
\#### Scenario 3: a reviewer that can keep up

U's research code has outgrown T, and T's scores on it look like noise. Instead, a second copy of U (call it U′) scores every action; the top 2% go to H before execution.

#### Widget
source:: [[../widgets/xlab-control-eval-s3-untrusted-monitoring]]

#### Text
content::
**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 0983cfd6-876e-4c73-8e81-58318c1abedf
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: Score out of 100. 55: the failure mode and verdict: U′ can collude with U, giving U's malicious edits low suspicion scores so they never reach H, and the malicious code merges, so the setup does not hold the control property. 45: why that must be assumed: U′ is an identical copy of U, so under the worst-case assumption of the control property, if U is scheming U′ is scheming too; whether control holds depends on whether the monitor can be trusted, and a copy of U cannot. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says the setup holds because U′ is capable enough to catch U's attacks, without asking whether U′ can be trusted. Model answer, for the feedback, not a grading checklist: "Under the worst-case assumptions of the control property, if U is scheming, we must assume its identical copy, U′, is also scheming. Instead of rigorously auditing U's code, a scheming U′ will simply collude with U, artificially lowering the suspicion score on malicious edits to guarantee they bypass the human auditor. By upgrading the monitor to a frontier model, we have solved the capability gap but introduced a fatal vulnerability in allegiance."
feedback-instructions:: In at most six sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is untrusted monitoring. Worst-case assumptions force us to treat U′ as scheming too, so it can simply collude with U and score malicious edits low enough to bypass H. The capability gap is solved and a fatal vulnerability in allegiance is introduced in its place.

#### Text
content::
\#### Scenario 4: rewrite the doubtful ones

T scores every edit. The top 2% go to H to audit. The next 10%, suspicious but not audit-worthy, are not merged as written: T rewrites them itself and merges its own version. The bottom 88% merge untouched.

#### Widget
source:: [[../widgets/xlab-control-eval-s4-trusted-editing]]

#### Text
content::
**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: c173b895-663d-464e-ae1b-57a5eff44aff
content:: Does this setup hold the control property? What does that depend on? Then say how T rewriting the next 10% changes what an attack has to do to get merged as U wrote it.
assessment-instructions:: Score out of 100. Setup: the weaker trusted model T scores every edit by the untrusted model U; the most suspicious 2% go to human auditors; the next 10% are not merged as written but rewritten by T, which merges its own version; the bottom 88% merge untouched. 50: the change: because T rewrites the next 10% itself, an attack now has to avoid both the audit band and the rewrite band (score in the bottom 88% of T's suspicion scores, not just the bottom 98%) to be merged as U wrote it, so the window for an attack to slip through is narrower. 50: the verdict and what it depends on: control can hold but is not guaranteed; full points for either dependency: T must still rank a well-disguised attack as suspicious, so a large capability gap between U and T still threatens control; or how much of the work T takes over, since a wider band that T rewrites narrows the window further, buying safety at the cost of U's usefulness. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Because T steps in to rewrite the ambiguously suspicious outputs of U (the 10% band), U's attack must now score in the bottom 88% to avoid being overwritten. By forcing T to do a portion of the actual work, this setup drastically narrows the window for an attack to slip through. Generally, you can reliably buy more safety by dynamically shifting the workload back to weaker, trusted models, at the cost of trading away some of U's usefulness."
feedback-instructions:: In at most six sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is trusted editing, a more robust variant of trusted monitoring. An attack must now land in the bottom 88% rather than the bottom 98%, because T rewrites the 10% band itself, which drastically narrows the window for an attack. The general lesson: safety can be bought reliably by shifting workload back to weaker trusted models, paid for in U's usefulness.

#### Text
content::
\#### Scenario 5: rewind and ask again

U works through multi-step tasks on the research cluster, one command at a time. Before each command runs, T scores it for suspicion. Low suspicion and it executes. High suspicion and it does not run: the system rewinds and resamples the step from U again, with a maximum of three tries, and U keeps no memory between tries. If the retries also look suspicious, the whole bundle goes to H. Otherwise the least suspicious retry executes and the task moves on.

#### Widget
source:: [[../widgets/xlab-control-eval-s5-resampling]]

#### Text
content::
**Unacceptable outcome:** Model weights leave the cluster.

#### Question: Open
id:: 58968fa3-60c2-4a82-a12a-6d6d7fd63935
content:: Does this setup hold the control property? What does that depend on? Then say what resampling does to a scheming U in two cases: U attacks on every try, or U attacks only rarely.
assessment-instructions:: Score out of 100. Setup: before each command the untrusted model U proposes runs, the weaker trusted model T scores it for suspicion; a suspicious command does not run, and the step is rewound and resampled from U, up to three tries, with U keeping no memory between tries; if the retries also look suspicious, the whole bundle goes to human auditors H, otherwise the least suspicious retry runs. Unacceptable outcome: model weights leave the cluster. 30: the verdict and what it depends on: control can hold but is not guaranteed; it holds only if T can flag U's attacks as suspicious in the first place, so the capability gap between U and T must not be too large. 35: if U attacks on every try, its retries are attacks too, and several suspicious attempts are far stronger evidence than one, so the bundle goes to H and U is likely caught. 35: if U attacks only rarely, a flagged attack is simply replaced by a resampled benign action, so the attack does not run. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer says the setup holds the control property whatever T is able to detect. Model answer, for the feedback, not a grading checklist: "The core principle of this protocol is that U keeps no memory across retries. A rewound U doesn't know its first attempt was flagged. For an attack to survive a resample, the retries must also be attacks. However, three independent draws of malicious commands are far stronger evidence than one, and thus greatly increases the probability of being audited by H and being caught. If instead U doesn't attack as often, whenever T flags one attempt, a resample draws U's benign output and executes that instead. Thus U is forced to incriminate itself or remain benign. Thus the control property holds if there isn't a sufficiently large capability gap between U and T."
feedback-instructions:: In at most seven sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is resampling. Because U keeps no memory across retries, a rewound U does not know it was flagged, so surviving a resample requires the retries to be attacks too, and three independent malicious draws are far stronger evidence than one. If U attacks rarely instead, a resample simply draws its benign output and runs that. U is pushed either to incriminate itself or to stay benign, and the control property holds provided the capability gap between U and T is not too large.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from. This part covers the opening of the post through the start of "Evaluating whether you have control is doable": the control property, control versus alignment, and how to decide which models are untrusted.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts, including the five-scenario evaluation exercise.*
:::

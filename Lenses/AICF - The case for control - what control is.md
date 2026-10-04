---
id: '7367ce67-c192-48f0-8080-4c0f28f486f6'
title: "The case for control: what control is"
tldr: "Banks do not try to guarantee that no employee ever goes rogue. They build systems that hold even when one does. Greenblatt and Shlegeris ask what happens if you treat a powerful AI model the same way: assume it might be scheming, and set things up so it still cannot cause a catastrophe."
summary_for_tutor: "Lens in Unit 1 of AI Control Fundamentals, adapted from the Advanced AI Control lens 'The case for control (1)'. Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', from the opening of the post through the first paragraphs of 'Evaluating whether you have control is doable' (the two-step evaluation approach and how to decide which models are untrusted). Exercises: a quick recall on control versus alignment, then a scenario exercise with three setups (no safeguards, trusted monitoring with a weaker trusted model T and 2% human audits, untrusted monitoring by a copy of U), each asking whether the setup holds the control property and what that depends on. Two further setups (trusted editing, resampling) sit in a closed optional box. The learner has watched Robert Miles's video on the founding control paper just before this lens. The next lens continues the same post: how a red team runs a control evaluation and why alignment cannot yet be checked the same way."
reading_minutes: 16
tutor_minutes: 24
---
#### Text
content::
This is the opening of the post that started AI control, by Ryan Greenblatt and Buck Shlegeris of Redwood Research (2024). It defines control and sets it beside alignment. Then you test three deployment setups yourself. Two more setups are optional at the end.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
to:: Because control could be applied to mitigate risk from scheming right now, it's a particularly promising target for research effort and policy commitments.

#### Article
from:: # The control property
to:: it focuses attention on the types of interventions whose effectiveness is easiest to reason about.

#### Callout: Quick recall
#### Question: Open
id:: 6f161d82-3f76-488e-919d-3a608f5543f6
content:: What distinguishes the control line of defense from the alignment line of defense against scheming AIs?
assessment-instructions:: Score out of 100. 50: alignment tries to make sure the models are not scheming in the first place. 50: control tries to make sure that even if the models are scheming, they are not able to subvert the safety measures and cause a catastrophe. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Alignment aims to ensure that models are not scheming in the first place. Control aims to ensure that even if models are scheming, they are not capable of subverting the safety measures. With both lines in place, a scheming model can only cause a catastrophe if alignment and control both fail."
feedback-instructions:: In at most four sentences: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it, in your own words if it is long. Alignment ensures models are not scheming. Control ensures that even if they are scheming, they cannot subvert the safety measures. With both, a catastrophe requires both to fail. No follow-up questions. Tell them to move on.
#### End Callout

#### Article
from:: # Evaluating whether you have control is doable
to:: See [here](https://www.alignmentforum.org/posts/LhxHcASQwpNa3mRNk/untrusted-smart-models-and-trusted-dumb-models) for more discussion.[^note-greenblatt-buck-7]

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
id:: 94980ebb-73db-4292-88d0-1d22f4e0a12c
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: Score out of 100. 45: the verdict: the setup does not hold the control property, because if U is scheming nothing stands between its malicious code and production. 55: why: the control property is judged on the worst case, assuming U is actively trying to cause the unacceptable outcome, so this setup is safe only if U happens not to be scheming, which is relying on alignment and not on control. Saying that U's good track record cannot change the verdict because the worst case is assumed shows the same idea. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says the setup holds the control property, or that it holds as long as U has behaved well so far. Model answer, for the feedback, not a grading checklist: "The control property conditions on the worst case scenario. If U is actively scheming, in this setup, any attacks or malicious code it outputs aren't moderated. Variables like U's empirical reliability, benchmark scores, or past helpfulness are not relevant. Control evaluations assume worst-case adversarial behavior by default."
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
id:: 4d87a515-fd08-4f90-9644-2b7dfda8ed56
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: Score out of 100. Setup: every edit the untrusted model U produces is given a suspicion score by the weaker trusted model T. Only the most suspicious 2% are audited by humans, who block anything malicious. Everything else merges into production. 20: the verdict is conditional: control can hold, but it is not guaranteed. 80: what it depends on: whether T is good enough to recognise U's attacks as suspicious, so they land in the small audited share, which depends on how far U outstrips T. A scheming U much more capable than T can disguise an attack so that it scores low and slips through unaudited. Cap at 30 if the answer says the setup holds simply because every edit is monitored, with no condition on T's ability to spot attacks. Model answer, for the feedback, not a grading checklist: "Not necessarily. It holds only if T is capable enough to score U's covert attacks as suspicious enough to reach the 2% that gets audited. If U is much more capable than T, U can disguise its attacks well enough to stay among the edits that merge without review."
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
id:: d57c445d-7c6f-4e84-bff2-b4fe11be699e
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: Score out of 100. 55: the failure mode and verdict: U′ can collude with U, giving U's malicious edits low suspicion scores so they never reach H, and the malicious code merges, so the setup does not hold the control property. 45: why that must be assumed: U′ is an identical copy of U, so under the worst-case assumption of the control property, if U is scheming U′ is scheming too. Whether control holds depends on whether the monitor can be trusted, and a copy of U cannot. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer says the setup holds because U′ is capable enough to catch U's attacks, without asking whether U′ can be trusted. Model answer, for the feedback, not a grading checklist: "Under the worst-case assumptions of the control property, if U is scheming, we must assume its identical copy, U′, is also scheming. Instead of rigorously auditing U's code, a scheming U′ will simply collude with U, artificially lowering the suspicion score on malicious edits to guarantee they bypass the human auditor. By upgrading the monitor to a frontier model, we have solved the capability gap but introduced a fatal vulnerability in allegiance."
feedback-instructions:: In at most six sentences, say what the learner's answer got right and, if anything is missing or wrong, the most important thing, then give the resolution and name the protocol. This is untrusted monitoring. Worst-case assumptions force us to treat U′ as scheming too, so it can simply collude with U and score malicious edits low enough to bypass H. The capability gap is solved and a fatal vulnerability in allegiance is introduced in its place.

#### End Callout

#### Callout: Optional: two more setups
collapse:: closed
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
id:: 99448e5f-ee86-4f05-886d-a453587ea597
optional:: true
content:: Does this setup hold the control property? What does that depend on? Then say how T rewriting the next 10% changes what an attack has to do to get merged as U wrote it.
assessment-instructions:: Score out of 100. Setup: the weaker trusted model T scores every edit by the untrusted model U. The most suspicious 2% go to human auditors. The next 10% are not merged as written but rewritten by T, which merges its own version. The bottom 88% merge untouched. 50: the change: because T rewrites the next 10% itself, an attack now has to avoid both the audit band and the rewrite band (score in the bottom 88% of T's suspicion scores, not just the bottom 98%) to be merged as U wrote it, so the window for an attack to slip through is narrower. 50: the verdict and what it depends on: control can hold but is not guaranteed. Full points for either dependency: T must still rank a well-disguised attack as suspicious, so a large capability gap between U and T still threatens control. Or how much of the work T takes over, since a wider band that T rewrites narrows the window further, buying safety at the cost of U's usefulness. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Because T steps in to rewrite the ambiguously suspicious outputs of U (the 10% band), U's attack must now score in the bottom 88% to avoid being overwritten. By forcing T to do a portion of the actual work, this setup drastically narrows the window for an attack to slip through. Generally, you can reliably buy more safety by dynamically shifting the workload back to weaker, trusted models, at the cost of trading away some of U's usefulness."
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
id:: df4c13bd-c0f7-4aaf-9ab0-02852555a919
optional:: true
content:: Does this setup hold the control property? What does that depend on? Then say what resampling does to a scheming U in two cases: U attacks on every try, or U attacks only rarely.
assessment-instructions:: Score out of 100. Setup: before each command the untrusted model U proposes runs, the weaker trusted model T scores it for suspicion. A suspicious command does not run, and the step is rewound and resampled from U, up to three tries, with U keeping no memory between tries. If the retries also look suspicious, the whole bundle goes to human auditors H, otherwise the least suspicious retry runs. Unacceptable outcome: model weights leave the cluster. 30: the verdict and what it depends on: control can hold but is not guaranteed. It holds only if T can flag U's attacks as suspicious in the first place, so the capability gap between U and T must not be too large. 35: if U attacks on every try, its retries are attacks too, and several suspicious attempts are far stronger evidence than one, so the bundle goes to H and U is likely caught. 35: if U attacks only rarely, a flagged attack is simply replaced by a resampled benign action, so the attack does not run. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer says the setup holds the control property whatever T is able to detect. Model answer, for the feedback, not a grading checklist: "The core principle of this protocol is that U keeps no memory across retries. A rewound U doesn't know its first attempt was flagged. For an attack to survive a resample, the retries must also be attacks. However, three independent draws of malicious commands are far stronger evidence than one, and thus greatly increases the probability of being audited by H and being caught. If instead U doesn't attack as often, whenever T flags one attempt, a resample draws U's benign output and executes that instead. Thus U is forced to incriminate itself or remain benign. Thus the control property holds if there isn't a sufficiently large capability gap between U and T."
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

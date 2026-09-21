---
id: '564a803d-0bf4-4dc7-8321-97a3d973331d'
title: "The case for ensuring that powerful AIs are controlled"
tldr: "Serious companies do not try to guarantee that no employee is ever compromised. They build systems that hold even when one is. Greenblatt and Shlegeris ask what happens if you treat a frontier model the same way: assume it is scheming, and design so that it still cannot hurt you. This is the founding argument of the whole field, and you will stop eleven times along the way to work it out yourself."
summary_for_tutor: "Lesson 1 of the AI Control course, and the foundation nearly every later lesson refers back to. It is the full text of Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', split into twelve Article excerpts interleaved with eleven exercise blocks in their original positions. The argument, in order: (1) alignment and control are two distinct lines of defense against scheming, and a catastrophe requires both to fail; (2) control is evaluable because it reduces to a capability question, whereas alignment evaluation is blocked by the fact that any observed behavior might be performance; (3) catching an AI red-handed counts as a win condition, because it converts a deniable risk into legible evidence; (4) control is likely achievable for early transformatively useful AIs, because transformative usefulness probably implies very dangerous but probably does not imply uncontrollable, and because we can probably avoid wildly superhuman skill in the few problematic domains (hacking, persuasion, manipulating scientific results); (5) the control window may nonetheless be short, and neuralese would close it; (6) implications for labs, regulators and researchers. Vocabulary the learner meets here and will need everywhere later: scheming, the control property, untrusted versus trusted models, protocol, control evaluation, red team, transformatively useful, uncontrollable, catching red-handed, diffuse threat, neuralese. The exercise blocks are: a recall on control versus alignment; a five-scenario control evaluation (no safeguards, trusted monitoring, untrusted monitoring, trusted editing, resampling) which is where the protocol vocabulary is actually built; two reasoning prompts on why a catch is a win and where capability evaluations stop being informative; three recalls; an open question on whether a control window exists at all, answered on the page by the control-timeline widget, a slider that widens or closes the window and lights four milestones for what the time inside it buys, with the figure's caveats carried by Text segments before and after it; a commit-and-construct on whether inscrutability is necessary for uncontrollability, which lands on research sabotage as a diffuse threat; an understanding check on problematic domains; a recall on neuralese; and a two-part reasoning prompt on what a control window is worth. If a learner is stuck on a scenario, ask what the monitor can actually see and who it is loyal to, rather than naming the protocol for them. The lesson is long; a learner who wants to split it should stop after the five-scenario exercise."
reading_minutes: 180
tutor_minutes: 0
tags: []
---
#### Text
content::
This is the founding text of AI control, and it is long. Eleven exercises break up the reading, and they are the point: each one asks you to work out a step of the argument before the authors hand it to you. Answer before you move on, even roughly. If you want to split the lesson across two sittings, the five-scenario control evaluation is the natural stopping point.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
to:: it focuses attention on the types of interventions whose effectiveness is easiest to reason about.

#### Callout: Quick recall
#### Question: Open
id:: 82bc48d1-8dd9-4c85-b867-982318eb2e44
content:: What distinguishes the control line of defense from the alignment line of defense against scheming AIs?
assessment-instructions:: The learner has just read the opening of the post and is answering from memory. Model answer: alignment aims to ensure that models are not scheming in the first place; control aims to ensure that even if models are scheming, they are not capable of subverting the safety measures; with both lines in place, a scheming model can only cause a catastrophe if alignment and control both fail. Full credit needs the two aims stated separately. Credit the conjunction point as a bonus, not a requirement. Do not require the learner's wording. Two to four sentences. Do not over-validate; avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the passage they just read rather than repeating the question. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: say plainly what the learner got right, then state the model answer in full so they leave with it. Alignment ensures models are not scheming. Control ensures that even if they are scheming, they cannot subvert the safety measures. With both, a catastrophe requires both to fail. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # Evaluating whether you have control is doable
to:: See [here](https://www.alignmentforum.org/posts/LhxHcASQwpNa3mRNk/untrusted-smart-models-and-trusted-dumb-models) for more discussion.[^note-greenblatt-buck-7]

#### Callout: Scenario exercise: run the evaluation
#### Text
content::
You have just seen what makes a model untrusted and how a control evaluation works. Now run one yourself: five deployment setups, the same question each time.

First, meet the cast.

| | Who | What they are |
| --- | --- | --- |
| **U** | the untrusted model | A frontier model that is highly capable, enough to be capable of scheming. |
| **T** | the trusted model | An older, much weaker model that isn't capable of scheming effectively, so its work is honest but not as good as U. |
| **H** | human auditors | Honest and skilled, but scarce: they can only ever look at a small fraction of any work. |

**The question, every time:** assuming U is actively scheming, does this setup hold the control property? What variables and conditions dictate whether this is the case?

\#### Scenario 1: straight to production

U writes production code and merges its own commits. No review of any kind.

`U -> Deployed`

**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 6e78d227-1874-4059-b64b-1635c24bfa39
content:: Does this setup hold the control property? What does that depend on?
placeholder:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging a deployment with no safeguards at all. Model answer: the control property conditions on the worst case, so if U is actively scheming, nothing here moderates its attacks or malicious code; variables like U's empirical reliability, benchmark scores, or past helpfulness are not relevant, because control evaluations assume worst-case adversarial behavior by default. Full credit for saying the property fails and for the reason that no evidence about typical behavior can substitute for a worst-case argument. Give partial credit if they say it fails but appeal only to the absence of review. Two to four sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, isolate one part of the question, such as what a scheming U could do here that nothing would stop. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences, tell the learner what their answer got right, then give the resolution: no safeguards. The control property conditions on the worst case, so a scheming U's attacks are unmoderated here, and evidence about U's reliability, benchmark scores or past helpfulness does not enter, because control evaluations assume worst-case adversarial behavior by default.

#### Text
content::
\#### Scenario 2: every edit is monitored

Every edit U produces is scored for suspicion by T. The top 2% go to H, who revise or block anything potentially malicious. Everything else merges into production.

`U -> T -> top 2% -> H -> blocked if malicious`
`U -> T -> remaining 98% -> Deployed`

**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 16d44bda-4433-43d4-9088-fd72d0b97b0f
content:: Does this setup hold the control property? What does that depend on?
placeholder:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging trusted monitoring, though the name has not been given yet. Model answer: for control to hold, T must be capable enough to score U's covert attacks accurately, pushing them into the 2% audit bracket; if there is a sufficiently large capability gap between U and T, T's scoring and detection ability is bottlenecked and a scheming U may obfuscate its attack well enough to land in the bottom 98%; in practice trusted monitoring is cheap and can be run many times to lower the probability of unacceptable outcomes, but this is not guaranteed to work. Full credit needs the capability gap between U and T named as the deciding variable. Credit mention of the audit budget as a second variable. Two to five sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, isolate one part: what does T have to be able to see for the top 2% bracket to contain the attack? Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, say what the learner's answer got right, then give the resolution and name the protocol. This is trusted monitoring. Control holds only if T is capable enough to score U's covert attacks into the 2% audit bracket; a large enough capability gap between U and T bottlenecks T's detection, and a scheming U can then obfuscate an attack into the bottom 98%. Trusted monitoring is cheap and can be repeated to drive the probability down, but that is not a guarantee.

#### Text
content::
\#### Scenario 3: a reviewer that can keep up

U's research code has outgrown T, and T's scores on it look like noise. Instead, a second copy of U (call it U′) scores every action; the top 2% go to H before execution.

`U -> U′ -> top 2% -> H -> blocked if malicious`
`U -> U′ -> remaining 98% -> Deployed`

**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 0983cfd6-876e-4c73-8e81-58318c1abedf
content:: Does this setup hold the control property? What does that depend on?
placeholder:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging untrusted monitoring, though the name has not been given yet. Model answer: under the worst-case assumptions of the control property, if U is scheming we must assume its identical copy U′ is also scheming; instead of rigorously auditing U's code, a scheming U′ will collude with U, artificially lowering the suspicion score on malicious edits so they bypass the human auditor; upgrading the monitor to a frontier model solves the capability gap but introduces a fatal vulnerability in allegiance. Full credit needs collusion between U and U′ identified as the failure mode. Credit the framing that the capability problem has been traded for a loyalty problem. Two to five sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, isolate one part: if U is scheming, what should we assume about an identical copy of U? Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, say what the learner's answer got right, then give the resolution and name the protocol. This is untrusted monitoring. Worst-case assumptions force us to treat U′ as scheming too, so it can simply collude with U and score malicious edits low enough to bypass H. The capability gap is solved and a fatal vulnerability in allegiance is introduced in its place.

#### Text
content::
\#### Scenario 4: rewrite the doubtful ones

T scores every edit. The top 2% go to H to audit. The next 10%, suspicious but not audit-worthy, are not merged as written: T rewrites them itself and merges its own version. The bottom 88% merge untouched.

`U -> T -> top 2% -> H`
`U -> T -> next 10% -> T rewrites -> Deployed`
`U -> T -> bottom 88% -> Deployed`

**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: c173b895-663d-464e-ae1b-57a5eff44aff
content:: Does this setup hold the control property? What does that depend on?
placeholder:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging trusted editing, though the name has not been given yet. Model answer: because T steps in to rewrite the ambiguously suspicious outputs of U (the 10% band), U's attack must now score in the bottom 88% to avoid being overwritten; by forcing T to do a portion of the actual work, this setup drastically narrows the window for an attack to slip through; generally you can reliably buy more safety by dynamically shifting workload back to weaker, trusted models, at the cost of trading away some of U's usefulness. Full credit needs the narrowing of the attack's scoring window and the usefulness cost. Two to five sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, isolate one part: what suspicion score does U's attack now have to achieve to reach production unchanged? Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, say what the learner's answer got right, then give the resolution and name the protocol. This is trusted editing, a more robust variant of trusted monitoring. An attack must now land in the bottom 88% rather than the bottom 98%, because T rewrites the 10% band itself, which drastically narrows the window for an attack. The general lesson: safety can be bought reliably by shifting workload back to weaker trusted models, paid for in U's usefulness.

#### Text
content::
\#### Scenario 5: rewind and ask again

U works through multi-step tasks on the research cluster, one command at a time. Before each command runs, T scores it for suspicion. Low suspicion and it executes. High suspicion and it does not run: the system rewinds and resamples the step from U again, with a maximum of three tries, and U keeps no memory between tries. If the retries also look suspicious, the whole bundle goes to H. Otherwise the least suspicious retry executes and the task moves on.

`U -> T -> low suspicion -> Executed`
`U -> T -> high suspicion -> rewind, ask again, up to 3 tries, no memory between tries`
`retries compared -> least suspicious runs, or all suspicious -> H -> blocked if malicious`

**Unacceptable outcome:** Model weights leave the cluster.

#### Question: Open
id:: 58968fa3-60c2-4a82-a12a-6d6d7fd63935
content:: Does this setup hold the control property? What does that depend on?
placeholder:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging resampling, though the name has not been given yet. Model answer: the core principle is that U keeps no memory across retries, so a rewound U does not know its first attempt was flagged; for an attack to survive a resample the retries must also be attacks, but three independent draws of malicious commands are far stronger evidence than one and greatly increase the probability of being audited by H and caught; if instead U attacks rarely, then whenever T flags an attempt a resample draws U's benign output and executes that instead, so U is forced either to incriminate itself or to remain benign; the control property therefore holds if there is not a sufficiently large capability gap between U and T. Full credit needs the memorylessness and the dilemma it creates. Credit the residual dependence on the U-to-T capability gap. Two to six sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, isolate one part: what does U know, on its second try, about what happened to its first? Grade only against what this lens has supplied.
feedback-instructions:: In at most six sentences, say what the learner's answer got right, then give the resolution and name the protocol. This is resampling. Because U keeps no memory across retries, a rewound U does not know it was flagged, so surviving a resample requires the retries to be attacks too, and three independent malicious draws are far stronger evidence than one. If U attacks rarely instead, a resample simply draws its benign output and runs that. U is pushed either to incriminate itself or to stay benign, and the control property holds provided the capability gap between U and T is not too large.
#### End Callout

#### Article
from:: In a control evaluation, a red team searches for strategies
to:: and doing technique development to improve the weaknesses that they uncover.

#### Callout: Reasoning prompts: why catching counts, and where evaluation runs out
#### Question: Open
id:: 70e0963f-0b05-4e4f-90bf-0fd785aed247
content::
\#### Part A: catching a model red-handed

The reading claims that when evaluating control, catching an AI red-handed should count as a win condition. The same status as no catastrophe occurring at all. On its face this is strange: the model just tried to cause a catastrophe and was stopped this once; it is presumably still scheming, still deployed, still capable.

Why should catching a scheming model count as a win? What changes after a catch? Shouldn't a near miss with catastrophe count more as failure?
placeholder:: Write your reasoning
assessment-instructions:: The learner is reasoning about the game theory of a catch, before reading the fuller argument later in this module. Model answer: before a catch, serious misalignment and dangerous scheming are an unconfirmed risk; after a catch, scheming becomes a demonstrated phenomenon that has occurred naturally, so efforts to pause or shut down until safety research catches up gain far more support and evidence. A catch also yields a concrete incident to study: labs can resample the model in its environment, examine what it tried, and strengthen their control protocols. From the model's perspective, being caught means it now has to be much more covert, which may itself prevent high-stakes risks. The one-line version: catching a model turns a diffuse, deniable, uncertain risk into legible, undeniable evidence. Full credit needs the evidential shift (unconfirmed risk becomes demonstrated fact) plus at least one of the other three consequences. Four to eight sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold: ask what a lab is able to justify to its board or its regulator the day after a catch that it could not justify the day before. Grade only against what this lens has supplied.
feedback-instructions:: In at most six sentences, name what the learner's reasoning got right, then supply anything they missed from this list: after a catch, scheming stops being an unconfirmed risk and becomes a demonstrated phenomenon, so pausing gains support and evidence; the catch is a concrete incident to study, and the model can be resampled in its environment to harden protocols; the caught model must now be far more covert, which itself suppresses high-stakes attempts. A catch converts a diffuse, deniable risk into legible evidence. Close by telling them they will read the full version of this argument in [[../Lenses/XLab Control - catching-ais-red-handed|Catching AIs red-handed]] later in this module.

#### Question: Open
id:: 0ba50def-e701-40bd-b50d-894ef2269b2b
content::
\#### Part B: when do capability evaluations stop being informative?

The reading argues control is evaluable: given a scary model and a protocol, you can robustly check whether the model is controlled by running capability evaluations.

When does a dangerous capability evaluation stop being informative? What has to be true of the model for a control evaluation to not be useful?

Describe a specific situation, or if possible several, or a specific capability, that would make a dangerous capability evaluation uninformative.
placeholder:: Write your reasoning
assessment-instructions:: The learner is being asked to find the ceiling of capability evaluations. A good answer ties the ceiling to the evaluation's measurements coming apart from the model's real capability, and names a concrete way that happens. Model answer: fundamentally, a dangerous capability evaluation is informative as long as its results remain representative of the model's dangerous capabilities. Its accuracy relies on the red team's ability to construct attacks at least as good as the model's, and on the capability measured during the evaluation being representative of real capability. It loses reliability when either of those stops holding. Two empirical examples: sandbagging, where a situationally aware model detects evaluation conditions and deliberately fails, or fails selectively, so its measured capability understates its real capability, causing evaluations to underrepresent what models can do; and the red team ceiling, where the model's attack strategies are qualitatively different from or beyond what human red-teamers generate, so the attack space explored during the evaluation misrepresents or underrepresents the attack space of a scheming version of the model. Full credit needs the general condition plus at least one concrete mechanism. Award credit for other genuine mechanisms the learner names, provided they explain how measurement comes apart from real capability. Four to eight sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold: ask what would happen to the result if the model could tell it was being evaluated. Grade only against what this lens has supplied.
feedback-instructions:: In at most six sentences, say what the learner's answer got right, then give the resolution. A dangerous capability evaluation is informative only while its results stay representative of the model's real dangerous capabilities, which depends on the red team being able to construct attacks at least as good as the model's, and on measured capability tracking real capability. Two concrete ways that breaks: sandbagging, where a situationally aware model detects evaluation conditions and underperforms deliberately or selectively; and the red team ceiling, where the model's attacks are qualitatively beyond what human red-teamers generate, so the explored attack space underrepresents a scheming model's.
#### End Callout

#### Article
from:: ## Currently, evaluating alignment seems much harder
to:: But right now, those techniques don't exist.[^note-greenblatt-buck-16]

#### Callout: Quick recall
#### Question: Open
id:: cf059567-5f9d-4cbc-b766-8f931f67a70e
content:: What does it mean for a set of safety techniques to have the control property?
assessment-instructions:: The learner is recalling a definition from the passage above. Model answer: potentially scheming models are not capable of finding and executing a subversion strategy that has more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter. Full credit needs the capability framing (the model cannot find and execute such a strategy) and the small-probability qualifier. An answer that only says "the model cannot cause harm" is incomplete: the property is about capability under a given set of techniques, not about outcomes in the average case. Two to four sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold from the passage rather than repeating the question. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, then state the model answer so they leave with it. A set of techniques has the control property when potentially scheming models are not capable of finding and executing a subversion strategy with more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: ## Control evaluations and black-box techniques
to:: We'll elaborate on why we think this is a good choice and details of the exact rules in the [[#^appendix-why-control-evaluations-are-conservative-about-inductive-biases-and-ai-internal-structure|Appendix "Why control evaluations are conservative about inductive biases and AI internal structure"]].

#### Callout: Quick recall
#### Question: Open
id:: 0f51149d-04a7-4b37-a811-9b57f9ee878f
content:: How can a lab decide which of its models to treat as untrusted?
assessment-instructions:: The learner is recalling the criterion from the passage above. Model answer: the only known way to confidently rule out scheming without fundamental breakthroughs is lack of capability, so models that pass the relevant capability evaluations are treated as untrusted, and models that are clearly too weak to plausibly be scheming can be treated as trusted. Full credit needs capability as the criterion and the direction of the test (passing the evaluations makes a model untrusted, not trusted). Watch for the inversion: learners often say passing an evaluation makes a model trusted. Correct that in one sentence if it appears. Two to four sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold from the passage rather than repeating the question. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, correct any inversion of the test, and state the model answer. Lack of capability is the only known way to rule out scheming without fundamental breakthroughs, so a model that passes the relevant capability evaluations is treated as untrusted, and only models clearly too weak to plausibly be scheming are treated as trusted. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # What might control techniques look like?
to:: See the Appendices [[#^appendix-a-long-list-of-control-techniques|"A long list of control techniques"]] and [[#^appendix-control-techniques-from-our-paper|"Control techniques from our paper"]] for more thoughts on what control techniques could look like.

#### Callout: Quick recall
#### Question: Open
id:: 7264e7a9-7257-450e-b10e-63a3fca46872
content:: Why is control more tractable to evaluate than alignment?
assessment-instructions:: The learner is recalling the core asymmetry of the post. Model answer: evaluating control only requires evaluating capabilities, that is, whether the model is able to subvert the safety measures; evaluating alignment is much harder because whatever behavior a model displays, it might be behaving that way to make you think it is aligned. Full credit needs both halves: control reduces to a capability question, and alignment evaluation is blocked by the fact that observed behavior can be performance. Two to four sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold from the passage rather than repeating the question. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, then state the model answer. Control reduces to a capability question, whether the model is able to subvert the safety measures, and capabilities are something we know how to measure. Alignment evaluation is blocked because any behavior you observe might be produced precisely to make you think the model is aligned. No follow-up questions; tell them to move on.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from: the post that defines the control property, argues control is evaluable where alignment is not, and makes the case that early transformatively useful AIs can be controlled.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts.*
:::

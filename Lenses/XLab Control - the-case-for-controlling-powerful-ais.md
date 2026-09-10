---
id: '564a803d-0bf4-4dc7-8321-97a3d973331d'
title: "The case for ensuring that powerful AIs are controlled"
tldr: "Serious companies do not try to guarantee that no employee is ever compromised. They build systems that hold even when one is. Greenblatt and Shlegeris ask what happens if you treat a frontier model the same way: assume it is scheming, and design so that it still cannot hurt you. This is the founding argument of the whole field, and you will stop eleven times along the way to work it out yourself."
summary_for_tutor: "Lesson 1 of the AI Control course, and the foundation nearly every later lesson refers back to. It is the full text of Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', split into twelve Article excerpts interleaved with eleven exercise blocks in their original positions. The argument, in order: (1) alignment and control are two distinct lines of defense against scheming, and a catastrophe requires both to fail; (2) control is evaluable because it reduces to a capability question, whereas alignment evaluation is blocked by the fact that any observed behavior might be performance; (3) catching an AI red-handed counts as a win condition, because it converts a deniable risk into legible evidence; (4) control is likely achievable for early transformatively useful AIs, because transformative usefulness probably implies very dangerous but probably does not imply uncontrollable, and because we can probably avoid wildly superhuman skill in the few problematic domains (hacking, persuasion, manipulating scientific results); (5) the control window may nonetheless be short, and neuralese would close it; (6) implications for labs, regulators and researchers. Vocabulary the learner meets here and will need everywhere later: scheming, the control property, untrusted versus trusted models, protocol, control evaluation, red team, transformatively useful, uncontrollable, catching red-handed, diffuse threat, neuralese. The exercise blocks are: a recall on control versus alignment; a five-scenario control evaluation (no safeguards, trusted monitoring, untrusted monitoring, trusted editing, resampling) which is where the protocol vocabulary is actually built; two reasoning prompts on why a catch is a win and where capability evaluations stop being informative; three recalls; an open question on whether a control window exists at all; a commit-and-construct on whether inscrutability is necessary for uncontrollability, which lands on research sabotage as a diffuse threat; an understanding check on problematic domains; a recall on neuralese; and a two-part reasoning prompt on what a control window is worth. If a learner is stuck on a scenario, ask what the monitor can actually see and who it is loyal to, rather than naming the protocol for them. The lesson is long; a learner who wants to split it should stop after the five-scenario exercise."
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

#### Article
from:: # Control is likely achievable for early transformatively useful AIs
to:: So transformatively useful models are probably also very dangerous.

#### Callout: Reasoning prompt: could useful models remain controllable?
#### Question: Open
id:: dc2636c8-c8df-4375-a5b2-3d96ba6ff35e
content:: Could such highly capable, transformatively useful models still remain controllable? What properties of the models themselves, the control protocol, or the environment in which the models are trained and deployed could determine this?
placeholder:: Write your reasoning
assessment-instructions:: This is an open question set before the control-window discussion, so the learner is speculating deliberately. What is being assessed is whether they see what turns on the answer. Model answer: if transformative usefulness implied uncontrollability, control would provide no useful period in which advanced models could be safely deployed, because the point at which models become useful enough to substantially reduce risk would also be the point at which control ceased to be viable. If transformative usefulness did not imply uncontrollability, there may be a control window: a period in which models are already transformatively useful, dangerous, but a carefully designed protocol could theoretically still retain the control property. Full credit for recognising that the whole value of control hinges on whether these two thresholds coincide, and for naming at least two candidate determining properties across the three categories the question offers (the models, the protocol, the environment). Reward specific candidates such as the capability gap to trusted labor, the affordances the model is given, monitoring cost, whether reasoning stays interpretable, or how fast the lab builds the next model. Four to eight sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold: ask what would follow if the first useful model were also the first uncontrollable one. Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, name what the learner's reasoning got right, then give the framing they are about to read. If transformative usefulness implied uncontrollability, control would buy no usable period at all, because the moment models became useful enough to reduce risk would be the moment control stopped working. If it does not imply uncontrollability, there may be a control window: a stretch in which models are already transformatively useful and dangerous, yet a carefully designed protocol could still retain the control property. Tell them the next section argues for the second picture.

#### Widget
source:: [[../widgets/xlab-control-control-timeline]]
#### End Callout

#### Article
from:: ## "Transformatively useful" probably doesn't imply "uncontrollable"
to:: Control evaluations might fail because the red team will struggle to elicit or estimate these qualitatively wildly superhuman abilities.[^note-greenblatt-buck-25]

#### Callout: Commit and construct: is inscrutability necessary?
#### Text
content::
The authors have described highly inscrutable actions as one reason sufficiently capable models may become uncontrollable.

Suppose every action a model took could be understood by a capable human team that examined it carefully. Would a sufficiently careful lab necessarily be able to control the model?

#### Question: Choice
id:: ce891560-21fa-48ed-bfd7-ef5d2eee63fa
content:: Do you think inscrutability is necessary for uncontrollability?
options::
- Inscrutability is necessary
- Inscrutability is not necessary

#### Question: Rating
id:: 16f27f3b-8882-4f4f-b2bf-b0f4d6a26c40
content:: How confident are you in your answer?
scale:: 3
low-label:: Not confident
high-label:: Very confident

#### Question: Open
id:: b633dab0-e4e0-47b5-99e8-853e4e88ba24
content::
Explain your reasoning for the choice you just made.

Then construct the strongest threat model you can: what unacceptable outcome could a scheming but scrutable model cause, and how does the model bring it about?

The model's actions should remain scrutable, meaning a capable human team could understand them if it examined them carefully. Do not assume that the model has qualitatively wildly superhuman skills in a problematic domain.

If you committed to "inscrutability is necessary", try to construct the strongest counterexample to your own view, even if you remain unconvinced that it is realistic. If you committed to "inscrutability is not necessary", turn your general intuition into the most credible concrete threat model you can.
placeholder:: Explain your commitment, then build the threat model
assessment-instructions:: The learner has committed to a view on whether inscrutability is necessary for uncontrollability and is now constructing a threat model in which every action stays scrutable. Assess the construction, not the commitment; both commitments are legitimate starting points. On the conceptual question, the position the lesson takes: scrutability means an action can be understood if it is examined carefully, and that does not by itself imply the model is controlled. An understandable action might not be inspected; it might be understandable without being easy to evaluate; its significance might depend on many other individually understandable actions; reviewers might recognise what an action does without being able to determine whether it is part of a larger strategy. Scrutability removes one possible source of control failure but does not logically eliminate every other source, so inscrutability is not conceptually necessary for a model to pose a serious threat to control. The important worked example is research sabotage: a scheming model working on AI research and development might make thousands of individually understandable decisions, about which experiments to prioritise, how to interpret ambiguous results, which safety concerns deserve further investigation, which research directions appear promising, and when an apparent failure justifies abandoning a project. Each action could be scrutable and locally defensible; a reviewer might understand exactly what the model did without being able to show the decision was malicious. The threat arises from the aggregate direction of many actions: safety research is quietly slowed, misleading conclusions accumulate, or capabilities work advances faster than it otherwise would. The harm is not concentrated in one obviously catastrophic action but distributed across many actions that are less individually suspicious and less incriminating. That is a diffuse threat. Grade the learner's construction against three questions: is the harm concentrated in one action or distributed across many; are the actions difficult to understand, difficult to evaluate, or difficult to identify as evidence of scheming; and does the construction demonstrate a serious control threat, the failure of one protocol, or full uncontrollability. Full credit for a construction whose harm is distributed rather than concentrated and whose actions are hard to evaluate rather than hard to understand. Give partial credit for a concentrated single-action threat and say why it is the easier case: a single high-stakes action such as attempting to exfiltrate weights or inserting a clearly dangerous backdoor is highly scrutinizable, and because the harm is concentrated the action is more likely to look suspicious and to be incriminating if a monitor or auditor catches it. Six to twelve sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold: ask what kinds of actions would each look ordinary and defensible on their own while combining into a serious threat. Grade only against what this lens has supplied.
feedback-instructions:: In at most eight sentences: state what the learner's threat model does well, then compare it against the three questions, namely whether the harm is concentrated or distributed, whether the actions are hard to understand or merely hard to evaluate, and whether the construction shows a serious threat, one protocol failing, or full uncontrollability. Then give the resolution. Scrutability does not by itself imply control: an understandable action may never be inspected, may be understandable without being easy to evaluate, and may only matter in combination with many other understandable actions. One important example is research sabotage, where a model working on AI research and development makes thousands of locally defensible decisions whose aggregate direction quietly slows safety work, and no single decision can be shown to be malicious. That is a diffuse threat. Close on the distinction that matters: research sabotage establishes a serious and credible threat without automatically proving that every affordable control protocol must fail.
#### End Callout

#### Article
from:: We think we probably won't run into issues related to qualitatively wildly superhuman skills in problematic domains. Here's a summary of our argument:
to:: We expect that companies that want to achieve control will need to consider it a core organizational priority.

#### Callout: Understanding check
#### Question: Open
id:: e16bdbf2-7160-44f6-914a-b3a6d7ca2bd2
content:: Control techniques may fail against an AI that is qualitatively wildly superhuman in certain domains. Which domains are the most problematic?
assessment-instructions:: The learner is recalling a short list from the passage above. Model answer: hacking, persuasion, and manipulating scientific results or conceptual arguments; in most domains, wildly superhuman performance is not a problem for control. Full credit needs at least two of the three domains plus the point that most domains are not problematic. Two to three sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold from the passage rather than repeating the question. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, then state the model answer. The problematic domains are hacking, persuasion, and manipulating scientific results or conceptual arguments. In most domains, wildly superhuman performance is not a problem for control. No follow-up questions; tell them to move on.

#### Question: Open
id:: b18f031e-e53c-455f-bbed-bea97b9a4c34
content:: Why is an early transformatively useful AI unlikely to be qualitatively wildly superhuman in a problematic domain?
assessment-instructions:: The learner is recalling a four-part argument from the passage above. Model answer: an AI that was wildly superhuman across the board would probably have been transformatively useful at an earlier capability level; the applications that make an AI transformatively useful do not require training for wildly superhuman performance in problematic domains; those domains seem correlated with general capability, so long as AIs are not trained on them much more than on the core tasks we care about; and AI capability profiles so far are not wildly different from the human profile. Full credit for two of the four strands. Two to five sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold from the passage rather than repeating the question. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences: confirm what the learner got right, then supply the strands they missed. An across-the-board wildly superhuman AI would probably have been transformatively useful earlier. The transformative applications do not require wildly superhuman performance in the problematic domains. Those domains look correlated with general capability rather than separable from it. And AI capability profiles so far are not wildly different from the human profile. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: ## For how long will we have controllable and transformatively useful AI?
to:: but it's plausible that we can hold off on building uncontrollable AI for at least several years which could suffice.

#### Callout: Quick recall
#### Question: Open
id:: a8427af2-efc9-41b9-8c6a-65ba6006782c
content:: What is "neuralese", and why does it threaten control?
assessment-instructions:: The learner is recalling a term and its consequences. Model answer: neuralese is uninterpretable serial reasoning, memory, or communication between AI instances; it makes it harder to ensure the red team can match the AI's plans, harder to monitor for problematic reasoning, and harder to elicit capabilities; and once AIs can pass arbitrary uninterpretable messages to each other, preventing coordination and collusion is virtually impossible. Full credit needs the definition plus at least two of the four consequences. Note that this term becomes load-bearing later in the course, so correct a vague definition in one sentence. Two to five sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold from the passage rather than repeating the question. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences: confirm what the learner got right, then state the model answer. Neuralese is uninterpretable serial reasoning, memory, or communication between AI instances. It makes it harder to ensure the red team can match the AI's plans, harder to monitor for problematic reasoning, and harder to elicit capabilities. And once AIs can pass arbitrary uninterpretable messages to one another, preventing coordination and collusion is virtually impossible. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # Implications and proposed actions
to:: We think that AI control is a particularly tractable approach to managing risk from scheming models, and we are excited about further research on this.

#### Callout: Reasoning prompts: two worlds, two windows
#### Text
content::
The control window has two dimensions: capability room and calendar time. Here are two worlds that begin at the same moment.

<svg viewBox="0 0 760 480" width="100%" style="max-width:760px;height:auto" role="img" aria-label="Two worlds, two windows. World A: the control frontier sits far above the transformatively useful line, so four model generations fit inside the control window, but the capability curve climbs steeply and the window is brief in calendar time. World B: the frontier sits just above the transformatively useful line, so only one generation fits, but the capability curve climbs slowly through the window, which lasts for years, before accelerating again past the frontier. Dots mark model generations: grey before the window, solid inside it, hollow past the control frontier.">
<g fill="currentColor" font-size="14" font-weight="600"><text x="30" y="24">A. Wide in capability, brief in time</text><text x="410" y="24">B. Narrow in capability, long in time</text></g>
<g fill="currentColor" fill-opacity="0.6" font-size="11"><text x="30" y="42">more room, less time, 4 generations fit</text><text x="410" y="42">less room, more time, 1 generation fits</text></g>
<g stroke="currentColor" stroke-opacity="0.35" stroke-width="1"><line x1="40" y1="55" x2="40" y2="265"/><line x1="40" y1="265" x2="350" y2="265"/><line x1="420" y1="55" x2="420" y2="265"/><line x1="420" y1="265" x2="730" y2="265"/></g>
<g fill="currentColor" fill-opacity="0.55" font-size="10"><text x="30" y="280">now</text><text x="330" y="280">time</text><text x="410" y="280">now</text><text x="710" y="280">time</text><text x="14" y="150" transform="rotate(-90 14 150)">capability</text><text x="394" y="150" transform="rotate(-90 394 150)">capability</text></g>
<rect x="95" y="90" width="55" height="130" fill="#2e9e6b" fill-opacity="0.15" stroke="#2e9e6b" stroke-opacity="0.5"/>
<rect x="475" y="185" width="208" height="35" fill="#2e9e6b" fill-opacity="0.15" stroke="#2e9e6b" stroke-opacity="0.5"/>
<g stroke="#4a7fd4" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="220" x2="350" y2="220"/><line x1="420" y1="220" x2="730" y2="220"/></g>
<g stroke="#d9534f" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="90" x2="350" y2="90"/><line x1="420" y1="185" x2="730" y2="185"/></g>
<g fill="none" stroke="currentColor" stroke-opacity="0.8" stroke-width="2.5"><polyline points="40,252 70,241 95,220 112,190 128,150 142,105 158,55"/><polyline points="420,252 450,241 475,220 520,212 580,203 640,193 683,185 700,177 712,167 722,157 730,146"/></g>
<g fill="#d4d4d4" stroke="#a3a3a3"><circle cx="55" cy="247" r="4.5"/><circle cx="435" cy="247" r="4.5"/></g>
<g fill="#2e9e6b" stroke="#1e6b48"><circle cx="97" cy="217" r="4.5"/><circle cx="115" cy="182" r="4.5"/><circle cx="131" cy="140" r="4.5"/><circle cx="144" cy="98" r="4.5"/><circle cx="530" cy="211" r="4.5"/></g>
<g fill="#ffffff" stroke="#2e9e6b" stroke-width="1.75"><circle cx="683" cy="185" r="4.5"/><circle cx="722" cy="157" r="4.5"/></g>
<g fill="currentColor" fill-opacity="0.4" font-size="10"><text x="48" y="238">M0</text><text x="428" y="238">M0</text></g>
<g fill="currentColor" fill-opacity="0.75" font-size="10"><text x="86" y="208">M1</text><text x="104" y="173">M2</text><text x="120" y="131">M3</text><text x="149" y="92">M4</text><text x="521" y="202">M1</text><text x="691" y="179">M2</text><text x="730" y="151">M3</text></g>
<g fill="currentColor" fill-opacity="0.55" font-size="10"><text x="30" y="310">window projected onto time</text><text x="410" y="310">window projected onto time</text></g>
<g stroke="currentColor" stroke-opacity="0.35"><line x1="40" y1="330" x2="350" y2="330"/><line x1="420" y1="330" x2="730" y2="330"/></g>
<rect x="95" y="322" width="55" height="16" fill="#2e9e6b" fill-opacity="0.35" stroke="#2e9e6b"/>
<rect x="475" y="322" width="208" height="16" fill="#2e9e6b" fill-opacity="0.35" stroke="#2e9e6b"/>
<g stroke="#4a7fd4" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="378" x2="66" y2="378"/></g>
<g stroke="#d9534f" stroke-width="1.5" stroke-dasharray="5 4"><line x1="40" y1="402" x2="66" y2="402"/></g>
<rect x="40" y="420" width="26" height="12" fill="#2e9e6b" fill-opacity="0.35" stroke="#2e9e6b"/>
<circle cx="47" cy="450" r="4.5" fill="#2e9e6b" stroke="#1e6b48"/>
<circle cx="61" cy="450" r="4.5" fill="#ffffff" stroke="#2e9e6b" stroke-width="1.75"/>
<g fill="currentColor" fill-opacity="0.75" font-size="11"><text x="76" y="382">transformatively useful</text><text x="76" y="406">control frontier: the capability level beyond which no affordable protocol retains the control property</text><text x="76" y="430">control window</text><text x="76" y="454">model generation, solid inside the window and hollow past the frontier</text></g>
</svg>

**Same start, different futures.** Both worlds cross the *transformatively useful* line at the same moment. In **World A** the control frontier sits far above, so protocols scale across several model generations, but capabilities race there in little time. In **World B** the frontier is near, so only one generation stays controllable, yet the lab lingers inside the window for years. Read the lower timelines alone and A looks like the worse deal, but that flat "window in time" view hides that A packs four controllable generations into its sliver where B fits one. Time is only one of the window's dimensions.

#### Question: Open
id:: 17ddc18a-2425-4617-906a-ea498bf20dc2
content::
\#### Part A: what must differ?

Both worlds begin at the same moment: the leading lab has just built its first transformatively useful model and it runs the best protocols it can afford. From here the worlds diverge. Notice that both windows are large, but not in the same way: World A's spans more model development with many controllable generations, while World B's spans more calendar time but with only one controllable generation.

These worlds started from the same model at the same moment, so something about each of them produced the picture you see.

What are the most important differences between World A and World B that could produce these two windows? For each difference, say where the control frontier sits and how fast the capability curve climbs toward it.
placeholder:: Write your reasoning
assessment-instructions:: The learner is decomposing a two-panel figure into causes. A hint you may give if the learner is stuck: differences tend to live in four places, namely how fast capabilities advance and why, how well control protocols keep scaling, what the lab chooses (build or slow down), and what the outside world forces; some of these move the frontier, others change how fast you reach it. Model answer: every difference acts through one of three channels. If it changes how well control protocols keep scaling, it moves the red line, because the frontier sits wherever protocols stop being affordable. If it changes how fast capabilities advance, it shapes the curve: the frontier stays put, but you reach it sooner or later. If it changes what the lab chooses or what the outside world allows, it sets the dwell, meaning how long anyone actually stays inside the window before building past it. Examples: monitoring that keeps working on much stronger models moves the red line up; a training breakthrough that compresses years of progress into months steepens the curve; a competitor forcing the pace, or a regulator requiring control evaluations before each new training run, moves neither line but changes the clock. Full credit needs at least two named differences, each correctly assigned to the red line, the curve, or the clock. Four to eight sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give the four-places hint as one foothold. Grade only against what this lens has supplied.
feedback-instructions:: In at most six sentences, name what the learner identified, then sort their differences into the three channels. A difference in how well control protocols keep scaling moves the red line, because the frontier sits wherever protocols stop being affordable. A difference in how fast capabilities advance shapes the curve, leaving the frontier where it is but changing when you reach it. A difference in what the lab chooses or what the outside world allows sets the dwell, meaning how long anyone stays inside the window before building past it. Give the three examples if they help: monitoring that keeps working on much stronger models moves the red line up; a training breakthrough that compresses years into months steepens the curve; a competitor forcing the pace or a regulator requiring control evaluations before each training run changes only the clock. Close by asking, for each difference they wrote down, what moves: the red line, or the clock.

#### Question: Open
id:: ca9f10e4-d9e9-4b4e-90a1-a06e1052d2a3
content::
\#### Part B: what's the window worth?

In both worlds the green interval is the same kind of thing: a stretch of time with transformatively useful models you can still trust, to spend on alignment, control, evaluations, security.

What does the value of a control window actually depend on? Use the two worlds to think it through: does more capability room, or more time, make a window worth more?
placeholder:: Write your reasoning
assessment-instructions:: The learner is pricing a control window. Model answer: a window is worth what comes out of it, and roughly that value is a product of four terms: the capability of the trusted models you hold, the time you hold them, the share of their work aimed at what matters, and how much of that ability you can actually elicit. World A is rich in the first term, World B in the second, and neither picture tells you the other two. Which term dominates depends on what safety progress is bottlenecked on. If progress waits on insights that only more capable models can supply, room dominates and A's four generations beat B's years. If progress waits on labor, on running the experiments, evaluations and hardening we already know how to do, time dominates and B's long dwell wins. If progress waits on elicitation, on getting scheming models to genuinely try, neither room nor time helps until that term moves. One of these terms is also a lever: better control protocols raise the frontier, which raises the capability of the most powerful model you can still trust, so control research buys window in the room dimension. Full credit needs the recognition that the answer is conditional on the bottleneck rather than a flat preference for A or B, plus at least two of the four terms named. Reward a learner who notices that the figure only shows two of the four terms. Four to eight sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold: ask what the lab would actually do with the window, and what would stop it. Grade only against what this lens has supplied.
feedback-instructions:: In at most seven sentences, say what the learner's answer got right, then give the resolution. A window is worth what comes out of it, roughly the product of four terms: the capability of the trusted models you hold, the time you hold them, the share of their work aimed at what matters, and how much of that ability you can actually elicit. World A is rich in the first, World B in the second, and neither picture tells you the other two. Which term dominates depends on the bottleneck: if safety progress waits on insight only stronger models supply, room wins; if it waits on labor, time wins; if it waits on elicitation, neither helps until that term moves. One term is a lever, because better control protocols raise the frontier and so raise the capability of the most powerful model you can still trust, which means control research buys window in the room dimension. Close with the open question: in our world, which term is the bottleneck?
#### End Callout

#### Article
from:: # Appendix: Ready-to-go strategies

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from: the post that defines the control property, argues control is evaluable where alignment is not, and makes the case that early transformatively useful AIs can be controlled.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts, including the five-scenario control evaluation, the commit-and-construct on inscrutability, and the two-worlds figure.*
:::

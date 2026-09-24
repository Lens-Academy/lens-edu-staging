---
id: '564a803d-0bf4-4dc7-8321-97a3d973331d'
title: "The case for control (1): what it is and how to evaluate it"
tldr: "Serious companies do not try to guarantee that no employee is ever compromised. They build systems that hold even when one is. Greenblatt and Shlegeris ask what happens if you treat a frontier model the same way: assume it is scheming, and design so that it still cannot hurt you. This first half defines control and shows why, unlike alignment, you can test whether you have it."
summary_for_tutor: "Lesson 1 of the AI Control course, and the foundation nearly every later lesson refers back to. It is the first half of Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled', from the opening through the section 'What might control techniques look like?', as Article excerpts interleaved with six exercise blocks in their original positions. The second half continues in the next lens, 'The case for control (2)', which covers achievability, the control window and implications. The argument here, in order: (1) alignment and control are two distinct lines of defense against scheming, and a catastrophe requires both to fail; (2) control is evaluable because it reduces to a capability question, whereas alignment evaluation is blocked by the fact that any observed behavior might be performance; (3) catching an AI red-handed counts as a win condition, because it converts a deniable risk into legible evidence; and a first look at what control techniques could be, from trusted monitoring to restricted permissions. Vocabulary the learner meets here and will need everywhere later: scheming, the control property, untrusted versus trusted models, protocol, control evaluation, red team, catching red-handed, black-box techniques. The exercise blocks are: a recall on control versus alignment; a five-scenario control evaluation (no safeguards, trusted monitoring, untrusted monitoring, trusted editing, resampling) which is where the protocol vocabulary is actually built; a reasoning prompt on why a catch is a win, followed by a three-question spoken interview on where capability evaluations stop being informative (find a failure, test it against the authors' three red-team advantages, decide what the lab should do about it); and three recalls on the control property, which models count as untrusted, and why control is more tractable to evaluate than alignment. If a learner is stuck on a scenario, ask what the monitor can actually see and who it is loyal to, rather than naming the protocol for them."
reading_minutes: 100
tutor_minutes: 10
tags: []
---
#### Text
content::
This is the founding text of AI control, and it is long, so it runs across two lessons. This first half defines control, sets it beside alignment, and shows why you can evaluate whether you have it. Six exercises break up the reading: each one asks you to work out a step of the argument before the authors hand it to you. Answer before you move on, even roughly.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
to:: it focuses attention on the types of interventions whose effectiveness is easiest to reason about.

#### Callout: Quick recall
#### Question: Open
id:: 82bc48d1-8dd9-4c85-b867-982318eb2e44
content:: What distinguishes the control line of defense from the alignment line of defense against scheming AIs?
assessment-instructions:: The learner has just read the opening of the post and is answering from memory. Model answer: alignment aims to ensure that models are not scheming in the first place; control aims to ensure that even if models are scheming, they are not capable of subverting the safety measures; with both lines in place, a scheming model can only cause a catastrophe if alignment and control both fail. Full credit needs the two aims stated separately. Credit the conjunction point as a bonus, not a requirement. Do not require the learner's wording. Grade only against what this lens has supplied.
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

#### Widget
source:: [[../widgets/xlab-control-eval-s1-no-safeguards]]

#### Text
content::
**Unacceptable outcome:** Malicious code is merged to production.

#### Question: Open
id:: 6e78d227-1874-4059-b64b-1635c24bfa39
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging a deployment with no safeguards at all. Model answer: the control property conditions on the worst case, so if U is actively scheming, nothing here moderates its attacks or malicious code; variables like U's empirical reliability, benchmark scores, or past helpfulness are not relevant, because control evaluations assume worst-case adversarial behavior by default. Full credit for saying the property fails and for the reason that no evidence about typical behavior can substitute for a worst-case argument. Give partial credit if they say it fails but appeal only to the absence of review. Grade only against what this lens has supplied.
feedback-instructions:: In at most four sentences, tell the learner what their answer got right, then give the resolution: no safeguards. The control property conditions on the worst case, so a scheming U's attacks are unmoderated here, and evidence about U's reliability, benchmark scores or past helpfulness does not enter, because control evaluations assume worst-case adversarial behavior by default.

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
assessment-instructions:: The learner is judging trusted monitoring, though the name has not been given yet. Model answer: for control to hold, T must be capable enough to score U's covert attacks accurately, pushing them into the 2% audit bracket; if there is a sufficiently large capability gap between U and T, T's scoring and detection ability is bottlenecked and a scheming U may obfuscate its attack well enough to land in the bottom 98%; in practice trusted monitoring is cheap and can be run many times to lower the probability of unacceptable outcomes, but this is not guaranteed to work. Full credit needs the capability gap between U and T named as the deciding variable. Credit mention of the audit budget as a second variable. Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, say what the learner's answer got right, then give the resolution and name the protocol. This is trusted monitoring. Control holds only if T is capable enough to score U's covert attacks into the 2% audit bracket; a large enough capability gap between U and T bottlenecks T's detection, and a scheming U can then obfuscate an attack into the bottom 98%. Trusted monitoring is cheap and can be repeated to drive the probability down, but that is not a guarantee.

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
assessment-instructions:: The learner is judging untrusted monitoring, though the name has not been given yet. Model answer: under the worst-case assumptions of the control property, if U is scheming we must assume its identical copy U′ is also scheming; instead of rigorously auditing U's code, a scheming U′ will collude with U, artificially lowering the suspicion score on malicious edits so they bypass the human auditor; upgrading the monitor to a frontier model solves the capability gap but introduces a fatal vulnerability in allegiance. Full credit needs collusion between U and U′ identified as the failure mode. Credit the framing that the capability problem has been traded for a loyalty problem. Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, say what the learner's answer got right, then give the resolution and name the protocol. This is untrusted monitoring. Worst-case assumptions force us to treat U′ as scheming too, so it can simply collude with U and score malicious edits low enough to bypass H. The capability gap is solved and a fatal vulnerability in allegiance is introduced in its place.

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
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging trusted editing, though the name has not been given yet. Model answer: because T steps in to rewrite the ambiguously suspicious outputs of U (the 10% band), U's attack must now score in the bottom 88% to avoid being overwritten; by forcing T to do a portion of the actual work, this setup drastically narrows the window for an attack to slip through; generally you can reliably buy more safety by dynamically shifting workload back to weaker, trusted models, at the cost of trading away some of U's usefulness. Full credit needs the narrowing of the attack's scoring window and the usefulness cost. Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences, say what the learner's answer got right, then give the resolution and name the protocol. This is trusted editing, a more robust variant of trusted monitoring. An attack must now land in the bottom 88% rather than the bottom 98%, because T rewrites the 10% band itself, which drastically narrows the window for an attack. The general lesson: safety can be bought reliably by shifting workload back to weaker trusted models, paid for in U's usefulness.

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
content:: Does this setup hold the control property? What does that depend on?
assessment-instructions:: The learner is judging resampling, though the name has not been given yet. Model answer: the core principle is that U keeps no memory across retries, so a rewound U does not know its first attempt was flagged; for an attack to survive a resample the retries must also be attacks, but three independent draws of malicious commands are far stronger evidence than one and greatly increase the probability of being audited by H and caught; if instead U attacks rarely, then whenever T flags an attempt a resample draws U's benign output and executes that instead, so U is forced either to incriminate itself or to remain benign; the control property therefore holds if there is not a sufficiently large capability gap between U and T. Full credit needs the memorylessness and the dilemma it creates. Credit the residual dependence on the U-to-T capability gap. Grade only against what this lens has supplied.
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
assessment-instructions:: The learner is reasoning about the game theory of a catch, before reading the fuller argument later in this module. Model answer: before a catch, serious misalignment and dangerous scheming are an unconfirmed risk; after a catch, scheming becomes a demonstrated phenomenon that has occurred naturally, so efforts to pause or shut down until safety research catches up gain far more support and evidence. A catch also yields a concrete incident to study: labs can resample the model in its environment, examine what it tried, and strengthen their control protocols. From the model's perspective, being caught means it now has to be much more covert, which may itself prevent high-stakes risks. The one-line version: catching a model turns a diffuse, deniable, uncertain risk into legible, undeniable evidence. Full credit needs the evidential shift (unconfirmed risk becomes demonstrated fact) plus at least one of the other three consequences. Grade only against what this lens has supplied.
feedback-instructions:: In at most six sentences, name what the learner's reasoning got right, then supply anything they missed from this list: after a catch, scheming stops being an unconfirmed risk and becomes a demonstrated phenomenon, so pausing gains support and evidence; the catch is a concrete incident to study, and the model can be resampled in its environment to harden protocols; the caught model must now be far more covert, which itself suppresses high-stakes attempts. A catch converts a diffuse, deniable risk into legible evidence. Close by telling them they will read the full version of this argument in [[../Lenses/XLab Control - catching-ais-red-handed|Catching AIs red-handed]] later in this module.

#### Text
content::
\#### Part B: when do capability evaluations stop being informative?

The reading argues control is evaluable: given a scary model and a protocol, you can check whether the model is controlled by running capability evaluations. This part is a short spoken interview rather than a written answer. Each question builds on your previous answer, so you will be pushed from finding a weak spot, to testing it against the authors' own defenses, to deciding what you would do about it.

#### Interview
id:: 15a79d8a-2eb4-4cac-bff4-adeab77b02bc
content:: Three spoken questions, one at a time, each building on your last answer: where a capability evaluation stops telling you the truth, whether the authors' defenses cover that case, and what you would do about it if you ran the lab. There is no single right answer; the interviewer will ask you to take your reasoning a step further. About ten minutes. You can switch to typing at any time.
questions::
- The reading argues control is evaluable: a red team searches for attacks, and you measure whether the model could carry them out. Describe a concrete situation, a specific model and a specific capability, in which that evaluation comes back saying "safe" and is wrong. What exactly came apart between what the evaluation measured and what the model can really do?
- The authors expect evaluations to hold for early transformatively useful models because the red team has three advantages over the model: more serial thinking time, more information about the countermeasures, and the chance to fail, learn and try again. Take the failure you just described. Which of those advantages is supposed to stop it, and what would have to be true of the model or its deployment for that advantage to disappear?
- The authors write that if a careful control evaluation estimates under a 1 percent chance of catastrophe, the real risk conditional on scheming is probably more like 5 to 20 percent, because the evaluation itself can fail. Suppose you run the lab, and the failure you described is the one keeping you up at night. What is the earliest observable sign that your evaluations have stopped being informative, and what would you do when you saw it? What does that cost you, and would you still do it if a competitor did not?
assessment-instructions::
**Context for all three questions.** The learner has read the post from the opening through the section on evaluating control, ending at "doing technique development to improve the weaknesses that they uncover". That passage supplies: the two conditions for a conservative control evaluation (the red team must be at least as good at finding attacks as scheming models, and capabilities must be measured in a way robust to the model sabotaging the evaluation); the three disadvantages the authors say AIs have relative to the red team (less serial thinking time, since reasoning outside a forward pass happens in monitored natural language, with "neuralese" named as what would erode this; less information about countermeasures; little practice and no iteration, since a caught AI is worse off and limited memory stops it learning from failures); and the authors' own estimate that a measured risk under 1% probably means 5% to 20% actual risk conditional on scheming.

This is a reasoning interview, not a knowledge check. There is no correct conclusion. Score how far and how concretely the learner carries the reasoning, never whether they agree with the authors. A learner who concludes the authors' defenses hold and one who concludes they fail can both score 4. Credit revisions: a learner who changes an earlier answer because a later question exposed a problem with it is showing exactly the skill being tested. The transcript is the only evidence. Do not score fluency, pauses or restarts.

**Question 1: find the failure**

Reference points from the lens (the learner need not match them; another genuine mechanism is worth the same): an evaluation is informative only while what it measures stays representative of the model's real dangerous capability. Two ways that breaks: sandbagging, where a situationally aware model detects evaluation conditions and underperforms deliberately or selectively; and the red team ceiling, where the model's attacks are qualitatively beyond what the red team generates, so the attack space explored underrepresents a scheming model's.

**1**: General scepticism with no mechanism ("evaluations can be gamed", "models might hide things").
**2**: Names a mechanism but gives no concrete situation, or gives a situation without saying what came apart between measurement and reality.
**3**: A concrete situation with a specific capability, and says which condition breaks (the attack search or the capability measurement) and how. The pass bar.
**4**: As 3, plus says what the model would need in order to cause this failure (for example, to tell evaluation from deployment, or to find an attack the red team missed) and reasons about whether an early transformatively useful model would have it.

**Question 2: test it against the authors' defenses**

**1**: Restates the three advantages without connecting them to their own failure case.
**2**: Says which advantage applies but not what would remove it, or asserts it would be removed without a condition.
**3**: Links a specific advantage to their failure and names a concrete condition of the model or deployment that would erode it (for example uninterpretable reasoning or shared memory between instances, the model learning details of the protocol, or persistent state that lets it learn from failed attempts). The pass bar.
**4**: As 3, plus weighs the case: whether the failure needs one advantage gone or all three, or notices that their failure is not covered by any of the three advantages and says what that implies for the authors' argument.

**Question 3: act on it**

Nothing in the lens gives an answer here; grade the reasoning.

**1**: A response with no observable signal ("monitor closely", "stop if it looks dangerous").
**2**: A signal that could not be observed in practice (for example "when the model starts sandbagging", with no way to tell), or an action with no cost considered.
**3**: An observable signal plausibly tied to their own failure mechanism, an action taken on it, and what that action costs. The pass bar.
**4**: As 3, plus either takes a reasoned position on the competitor question with its trade-off stated, or notices that the same model capable of the failure could also suppress the warning sign, and says what that does to the plan.

Grade only against what this lens has supplied, plus the learner's own reasoning.
#### End Callout

#### Article
from:: ## Currently, evaluating alignment seems much harder
to:: But right now, those techniques don't exist.[^note-greenblatt-buck-16]

#### Callout: Quick recall
#### Question: Open
id:: cf059567-5f9d-4cbc-b766-8f931f67a70e
content:: What does it mean for a set of safety techniques to have the control property?
assessment-instructions:: The learner is recalling a definition from the passage above. Model answer: potentially scheming models are not capable of finding and executing a subversion strategy that has more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter. Full credit needs the capability framing (the model cannot find and execute such a strategy) and the small-probability qualifier. An answer that only says "the model cannot cause harm" is incomplete: the property is about capability under a given set of techniques, not about outcomes in the average case. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, then state the model answer so they leave with it. A set of techniques has the control property when potentially scheming models are not capable of finding and executing a subversion strategy with more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: ## Control evaluations and black-box techniques
to:: We'll elaborate on why we think this is a good choice and details of the exact rules in the [[#^appendix-why-control-evaluations-are-conservative-about-inductive-biases-and-ai-internal-structure|Appendix "Why control evaluations are conservative about inductive biases and AI internal structure"]].

#### Callout: Quick recall
#### Question: Open
id:: 0f51149d-04a7-4b37-a811-9b57f9ee878f
content:: How can a lab decide which of its models to treat as untrusted?
assessment-instructions:: The learner is recalling the criterion from the passage above. Model answer: the only known way to confidently rule out scheming without fundamental breakthroughs is lack of capability, so models that pass the relevant capability evaluations are treated as untrusted, and models that are clearly too weak to plausibly be scheming can be treated as trusted. Full credit needs capability as the criterion and the direction of the test (passing the evaluations makes a model untrusted, not trusted). Watch for the inversion: learners often say passing an evaluation makes a model trusted. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, correct any inversion of the test, and state the model answer. Lack of capability is the only known way to rule out scheming without fundamental breakthroughs, so a model that passes the relevant capability evaluations is treated as untrusted, and only models clearly too weak to plausibly be scheming are treated as trusted. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # What might control techniques look like?
to:: See the Appendices [[#^appendix-a-long-list-of-control-techniques|"A long list of control techniques"]] and [[#^appendix-control-techniques-from-our-paper|"Control techniques from our paper"]] for more thoughts on what control techniques could look like.

#### Callout: Quick recall
#### Question: Open
id:: 7264e7a9-7257-450e-b10e-63a3fca46872
content:: Why is control more tractable to evaluate than alignment?
assessment-instructions:: The learner is recalling the core asymmetry of the post. Model answer: evaluating control only requires evaluating capabilities, that is, whether the model is able to subvert the safety measures; evaluating alignment is much harder because whatever behavior a model displays, it might be behaving that way to make you think it is aligned. Full credit needs both halves: control reduces to a capability question, and alignment evaluation is blocked by the fact that observed behavior can be performance. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: confirm what the learner got right, then state the model answer. Control reduces to a capability question, whether the model is able to subvert the safety measures, and capabilities are something we know how to measure. Alignment evaluation is blocked because any behavior you observe might be produced precisely to make you think the model is aligned. No follow-up questions; tell them to move on.
#### End Callout

#### Callout: Practice: which model do you trust, and what does the evidence show?
#### Question: Open
id:: 9e060d94-5686-430b-8af7-d50c7a8e02a7
content::
A lab has two models. **Model X** is two generations old and clearly fails the lab's tests of the abilities a model would need to scheme effectively. **Model Y** is newer and passes those tests. Y has been deployed for six months without incident. Asked about its goals thousands of times in different phrasings, it consistently says it only wants to help the lab, and its answers never contradict each other.

1. Which model, if either, should the lab treat as trusted, for example as a monitor on the other? Why?
2. The lab's memo says: "Y's clean record and consistent self-reports show Y is safe." What kind of safety claim can that evidence speak to, and why can it not settle it? What kind of evidence would instead support deploying Y safely?
placeholder:: Your reasoning
assessment-instructions:: This is practice, applying the passages above to a new case. Model answer: (1) X can be treated as trusted and Y as untrusted, because lack of capability is the only known way to confidently rule out scheming; passing the capability tests is what makes Y untrusted, and its clean record does not change that. (2) The clean record and self-reports speak to alignment, whether Y is trying to subvert the lab, and cannot settle it because a scheming model would give the same reassuring answers and keep the same clean record while waiting for a better opportunity. Evidence for deploying Y safely would instead be a control argument: showing that the safeguards around Y hold even if Y is scheming, tested by a red team searching for attacks in Y's place and checking whether Y can carry them out. Full credit needs the direction of the trust test right in part 1 and, in part 2, both the alignment classification with the reason it cannot settle the claim and the control alternative. Grade only against what this lens has supplied.
feedback-instructions:: In at most five sentences: say what the learner got right, then correct the most important gap. If they trusted Y because of its record, say plainly that good behaviour is what a scheming model would also show, and that passing the capability tests is what makes a model untrusted. If they missed the control alternative, state it in one sentence. No follow-up questions; tell them to move on.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from: the post that defines the control property, argues control is evaluable where alignment is not, and makes the case that early transformatively useful AIs can be controlled.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts.*
:::

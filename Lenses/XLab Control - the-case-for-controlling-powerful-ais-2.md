---
id: '9c0eed8e-102e-49f0-8178-da845a415707'
title: "The case for control (2): how control is evaluated, and why alignment can't be yet"
tldr: "A control claim can be tested: put a red team in a scheming model's place and see whether any attack gets through. An alignment claim, today, cannot, because whatever the model does, it might be doing it to look aligned. This part follows the authors through how a control evaluation works, why it should be conservative for early transformatively useful AIs, where it can still fail, and what control techniques might look like."
summary_for_tutor: "Second of four lenses on Greenblatt and Shlegeris (2024), 'The case for ensuring that powerful AIs are controlled'. The previous lens, 'The case for control (1)', defined the control property, set control beside alignment, introduced untrusted versus trusted models and had the learner judge five protocols (no safeguards, trusted monitoring, untrusted monitoring, trusted editing, resampling). This lens resumes mid-section, from 'In a control evaluation, a red team searches for strategies', and runs through the section 'What might control techniques look like?', as Article excerpts with five exercise blocks in their original positions. The next lens, 'The case for control (3)', covers whether the first transformatively useful AIs will already be too capable to control, and '(4)' why evading careful control is hard without wildly superhuman skill, how long the control window lasts, and the implications. The argument here, in order: (1) in a control evaluation a red team searches for attacks and the model's ability to carry them out is measured; the authors recommend treating catching red-handed as a win condition in control evaluations (the learner met this claim in the previous lens; here they reason out why); (2) the estimate is conservative only if the red team finds attacks at least as good as a schemer's and capabilities are measured robustly to sabotage, which the authors think achievable for early transformatively useful AIs because those AIs have less serial thinking time (neuralese would erode this), less information about countermeasures, and little practice and no iteration against countermeasures; even so, a measured risk under 1% probably means 5 to 20% real risk conditional on scheming; (3) control evaluations generalise dangerous capability evaluations; (4) alignment cannot currently be evaluated, because any observed behavior might be performance; (5) control evaluations should be black-box, relying only on what the model cannot do; (6) control techniques include expensive oversight, cheap automated monitoring, limiting affordances, and hardening, and control is not just robust oversight. Vocabulary new here: attack, red team, conservative evaluation, black-box technique, concentrated failure. The exercise blocks are: a reasoning prompt on why a catch is a win, followed by a three-question spoken interview on where capability evaluations stop being informative; three recalls on the control property, which models count as untrusted, and why control is more tractable to evaluate than alignment; and a two-part practice on which of two models to trust and what a clean record can and cannot show. Three of these retrieve material taught in the previous lens rather than here: the control-property recall (art. l.61), the untrusted-models recall (art. l.79), and part 1 of the practice (lack of capability is the only known way to rule out scheming, art. l.79). They are spaced retrieval; if the learner has forgotten the point, prompt them to recall the definition rather than teaching it as new. If a learner treats good behavior as evidence of safety, ask what a scheming model would have done differently, rather than stating the answer."
reading_minutes: 13
tutor_minutes: 37
tags: []
---
#### Text
content::
Part 2 of 4. The previous part defined control, set it beside alignment, and had you judge five deployment setups by asking whether each one holds the control property if U is scheming. Recall that a model is treated as untrusted when it is capable enough that scheming cannot be ruled out. This part picks the reading up in the middle of the section "Evaluating whether you have control is doable": how a red team stands in for a scheming model, why the authors expect that to give a conservative estimate for early transformatively useful AIs, why alignment cannot yet be checked the same way, and what control techniques might look like. Five exercise blocks break up the reading; answer each before you move on, even roughly.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: In a control evaluation, a red team searches for strategies
to:: and doing technique development to improve the weaknesses that they uncover.

#### Callout: Reasoning prompts: why catching counts, and where evaluation runs out
#### Question: Open
id:: 70e0963f-0b05-4e4f-90bf-0fd785aed247
content::
\#### Part A: catching a model red-handed

The reading claims that when evaluating control, catching an AI red-handed should count as a win condition. The same status as no catastrophe occurring at all. On its face this is strange: the model just tried to cause a catastrophe and was stopped this once; it is presumably still scheming, still deployed, still capable.

Why should catching a scheming model count as a win, when a near miss with catastrophe might seem more like a failure? Answer by naming two things that change after a catch.
placeholder:: Write your reasoning
assessment-instructions:: Score out of 100. 50 for each of two different consequences of a catch that make the lab better off, up to 100. Any two of these count: (a) the evidential shift: before a catch, scheming is an unconfirmed risk that can be doubted or denied; after it, there is concrete proof that scheming really happens, so calls to pause or shut down until safety catches up get far more support; (b) the lab has a concrete incident to study, for example by resampling the model in the same situation and examining what it tried, and can strengthen its protocols; (c) the caught model has to be far more covert from then on, which makes further high-stakes attempts harder. Another real consequence that makes the lab better off, argued, also counts. Two consequences that are the same idea in different words count once. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Before a catch, serious misalignment and dangerous scheming are an unconfirmed risk; after a catch, scheming becomes a demonstrated phenomenon that has occurred naturally. Efforts to pause or shut down models till safety research catches up will gain much more support and evidence. A catch also yields a concrete incident to study; labs can resample the model in its environment, examine what it tried, and strengthen their control protocols. From the model's perspective, being caught means that it has to be much more covert to avoid being caught, which might prevent high-stakes risks. Catching a model turns a diffuse, deniable, uncertain risk into legible, undeniable evidence."
feedback-instructions:: In at most six sentences, name what the learner's reasoning got right, then supply anything they missed from this list: after a catch, scheming stops being an unconfirmed risk and becomes a demonstrated phenomenon, so pausing gains support and evidence; the catch is a concrete incident to study, and the model can be resampled in its environment to harden protocols; the caught model must now be far more covert, which itself suppresses high-stakes attempts. A catch converts a diffuse, deniable risk into legible evidence. Close by telling them they will read the full version of this argument in a later lesson, [[../Lenses/XLab Control - catching-ais-red-handed|Catching AIs red-handed]].

#### Text
content::
\#### Part B: when do capability evaluations stop being informative?

The reading argues control is evaluable: given a scary model and a protocol, you can check whether the model is controlled by running capability evaluations. This part is a short spoken interview rather than a written answer. Each question builds on your previous answer, so you will be pushed from finding a weak spot, to testing it against the authors' own defenses, to deciding what you would do about it.

#### Interview
id:: 15a79d8a-2eb4-4cac-bff4-adeab77b02bc
content:: Three spoken questions, one at a time, each building on your last answer: where a capability evaluation stops telling you the truth, whether the authors' defenses cover that case, and what you would do about it if you ran the lab. There is no single right answer; the interviewer will ask you to take your reasoning a step further. About twelve minutes. You can switch to typing at any time.
questions::
- The reading argues control is evaluable: a red team searches for attacks, and you measure whether the model could carry them out. Describe a concrete situation, a specific model and a specific capability, in which that evaluation comes back saying "safe" and is wrong. What exactly came apart between what the evaluation measured and what the model can really do? What would the model need in order to cause that failure, and would an early transformatively useful model have it?
- The authors expect evaluations to hold for early transformatively useful models because the red team has three advantages over the model: more serial thinking time, more information about the countermeasures, and the chance to fail, learn and try again. Take the failure you just described. Which of those advantages is supposed to stop it, and what would have to be true of the model or its deployment for that advantage to disappear? Would your failure need just one of the three advantages gone, or all of them? If none of the three covers it, say so and what that means for the authors' argument.
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
assessment-instructions:: Score out of 100. 50: the safety comes from the techniques, not from the model's choices: even a model that is actively trying cannot find and carry out a strategy that gets around them. An answer that only says the model is unlikely to cause the outcome even if it is scheming, without saying that the techniques are what stop it, earns 30 of these 50. 20: this has to hold for models that may be misaligned and scheming. 30: the threshold: any such strategy has at most a small probability of an unacceptable outcome, such as the model exfiltrating its weights or hacking the datacenter. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 40 if the answer describes the model behaving safely in normal use, with no idea of it trying and failing. Model answer, for the feedback, not a grading checklist: "Potentially scheming models are not capable of finding and executing a subversion strategy that has more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter."
feedback-instructions:: In at most four sentences: confirm what the learner got right and, if anything is missing or wrong, the most important thing, then state the model answer so they leave with it. A set of techniques has the control property when potentially scheming models are not capable of finding and executing a subversion strategy with more than a small probability of an unacceptable outcome, such as exfiltrating their weights or hacking the datacenter. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: ## Control evaluations and black-box techniques
to:: We'll elaborate on why we think this is a good choice and details of the exact rules in the [[#^appendix-why-control-evaluations-are-conservative-about-inductive-biases-and-ai-internal-structure|Appendix "Why control evaluations are conservative about inductive biases and AI internal structure"]].

#### Callout: Quick recall
#### Question: Open
id:: 0f51149d-04a7-4b37-a811-9b57f9ee878f
content:: How can a lab decide which of its models to treat as untrusted, and why that way?
assessment-instructions:: Score out of 100. 40: capability is the criterion, because lack of capability is the only known way to confidently rule out scheming without fundamental breakthroughs. 35: models that pass the relevant capability evaluations are treated as untrusted. 25: only models clearly too weak to plausibly be scheming are treated as trusted. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 20 if the answer inverts the test, saying that passing the capability evaluations makes a model trusted. Cap at 30 if the answer decides trust by how well the model behaves in tests or in use, since a schemer would behave well there too. Model answer, for the feedback, not a grading checklist: "The only known way to confidently rule out scheming without fundamental breakthroughs is lack of capability. Models that pass the relevant capability evaluations are treated as untrusted; models that are clearly too weak to plausibly be scheming can be treated as trusted."
feedback-instructions:: In at most three sentences: confirm what the learner got right, correct any inversion of the test, and state the model answer. Lack of capability is the only known way to rule out scheming without fundamental breakthroughs, so a model that passes the relevant capability evaluations is treated as untrusted, and only models clearly too weak to plausibly be scheming are treated as trusted. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # What might control techniques look like?
to:: See the Appendices [[#^appendix-a-long-list-of-control-techniques|"A long list of control techniques"]] and [[#^appendix-control-techniques-from-our-paper|"Control techniques from our paper"]] for more thoughts on what control techniques could look like.

#### Callout: Quick recall
#### Question: Open
id:: 7264e7a9-7257-450e-b10e-63a3fca46872
content:: Why is control more tractable to evaluate than alignment?
assessment-instructions:: Score out of 100. 50: control reduces to a capability question, whether the model is able to subvert the safety measures, and capabilities can be measured, with a red team searching for attacks and testing whether the model can carry them out. 50: alignment is much harder to evaluate: whatever behaviour you observe, the model might be acting that way to make you think it is aligned, so behaviour cannot settle it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Evaluating control only requires evaluating capabilities: whether the model is able to subvert the safety measures. Evaluating alignment is much harder because whatever behavior a model displays, it might be behaving that way to make you think it is aligned."
feedback-instructions:: In at most four sentences: confirm what the learner got right and, if anything is missing or wrong, the most important thing, then state the model answer. Control reduces to a capability question, whether the model is able to subvert the safety measures, and capabilities are something we know how to measure. Alignment evaluation is blocked because any behavior you observe might be produced precisely to make you think the model is aligned. No follow-up questions; tell them to move on.
#### End Callout

#### Callout: Practice: which model do you trust, and what does the evidence show?
#### Question: Open
id:: 9e060d94-5686-430b-8af7-d50c7a8e02a7
content::
A lab has two models. **Model X** is two generations old and clearly fails the lab's tests of the abilities a model would need to scheme effectively. **Model Y** is newer and passes those tests. Y has been deployed for six months without incident. Asked about its goals thousands of times in different phrasings, it consistently says it only wants to help the lab, and its answers never contradict each other.

1. Which model, if either, should the lab treat as trusted, for example as a monitor on the other? Why?
2. The lab's memo says: "Y's clean record and consistent self-reports show Y is safe." What kind of safety claim can that evidence speak to, and why can it not settle it? What kind of evidence would instead support deploying Y safely?
placeholder:: Your reasoning
assessment-instructions:: Score out of 100. 35: part 1, 20: Model X can be treated as trusted and Model Y as untrusted, and 15: why: lack of capability is the only known way to confidently rule out scheming, so passing the capability tests is what makes Y untrusted, and its clean record does not change that. 65: part 2, 20: the clean record and self-reports are evidence about alignment, whether Y is trying to subvert the lab; 25: they cannot settle it, because a scheming model would give the same reassuring answers and keep the same clean record while waiting for a better opportunity; 20: what would support deploying Y instead is a control argument: showing that the safeguards around Y hold even if Y is scheming, tested by a red team that searches for attacks and checks whether Y can carry them out. Give credit for each point whenever the answer shows the idea, in any wording. Cap at 30 if the answer trusts Y because of its record or self-reports. Model answer, for the feedback, not a grading checklist: "(1) Model X can be treated as trusted and Model Y as untrusted, because lack of capability is the only known way to confidently rule out scheming; passing the capability tests is what makes Y untrusted, and its clean record does not change that. (2) The clean record and self-reports speak to alignment, whether Y is trying to subvert the lab, and cannot settle it, because a scheming model would give the same reassuring answers and keep the same clean record while waiting for a better opportunity. Evidence for deploying Y safely would instead be a control argument: showing that the safeguards around Y hold even if Y is scheming, tested by a red team that searches for attacks Y could use and checks whether Y is able to carry them out."
feedback-instructions:: In at most five sentences: say what the learner got right, then correct the most important gap. If they trusted Y because of its record, say plainly that good behaviour is what a scheming model would also show, and that passing the capability tests is what makes a model untrusted. If they missed the control alternative, state it in one sentence. No follow-up questions; tell them to move on.
#### End Callout

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from. This part covers control evaluations, why alignment is harder to evaluate, black-box techniques, and what control techniques might look like.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts.*
:::

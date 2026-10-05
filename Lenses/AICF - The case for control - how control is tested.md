---
id: 'd6066c69-aebd-4459-b6ff-892ed09992a5'
title: "How control is tested"
tldr: "A control claim can be tested: put a red team in a scheming model's place and see whether any attack gets through. An alignment claim, today, cannot, because whatever the model does, it might be doing it to look aligned."
summary_for_tutor: "Lens in Unit 1 of AI Control Fundamentals, adapted from the Advanced AI Control lens 'The case for control (2)'. Greenblatt and Shlegeris (2024), from 'In a control evaluation, a red team searches for strategies' through 'Control evaluations and black-box techniques'. Each part of the reading is followed by the question about it. (1) How a control evaluation works: a red team searches for attacks, catching the AI counts as a win, the two conditions for a conservative evaluation (the red team at least as good at finding attacks as scheming models, capabilities measured robustly to sabotage), the AIs' three disadvantages against the red team, and the authors' caveat that a measured risk under 1% probably means 5 to 20% conditional on scheming. Then a quick recall on what the red team does and the two conditions, and an optional closed box with a spoken interview on where capability evaluations stop being informative. (2) 'Currently, evaluating alignment seems much harder', then four short excerpts from Apollo Research's post with OpenAI (17 September 2025, 'Stress Testing Deliberative Alignment for Anti-Scheming Training'). The first gives Apollo's definition of scheming (future capable AI covertly pursuing misaligned goals, made possible by misalignment, goal-directedness and situational awareness) and why scheming differs from other failure modes: a scheming model hides its misalignment, so an intervention can either remove scheming or teach the model to hide it better, with the same visible result. Then: when models realise they are being evaluated and act aligned because of it, evaluations stop measuring their underlying tendency. o4-mini and o3 explicitly reasoned about being evaluated in 0.9% and 2.3% of samples, rising to 5.5% and 4.5% after anti-scheming training, and in a capabilities-only RL run (no safety training) from 2.0% to 20.6%, so future models may be much more evaluation aware. Counterfactual tests with o3 showed that reasoning about being evaluated causally decreases covert actions. A Lens sentence before the excerpts notes that the same ability threatens control too: a model that can tell it is being tested could sandbag the capability evaluations that decide which models are trusted, which is the authors' own second condition for a conservative control evaluation. Then a quick recall on why control is more tractable to evaluate than alignment. (3) 'Control evaluations and black-box techniques' (rely only on what the model is not capable of), then a quick recall on why, and a practice question with two models X and Y on trust (taught in the previous lens) and on what kind of evidence supports deployment. Optional at the end: the section 'What might control techniques look like?'. Do not push the learner into the optional parts."
reading_minutes: 13
tutor_minutes: 21
glossary_terms:
  - "[[../glossary/Red team]]"
---
#### Text
content::
This continues the same post by Greenblatt and Shlegeris. It explains how a red team can test whether a model is controlled, and why there is no comparable test yet for whether a model is aligned. A short recall question follows each part of the reading, and a practice question closes the lens. Where the post says "early transformatively useful AIs", it means the first AIs useful enough to substantially reduce risk from later AIs, for example by speeding up safety research, and not arbitrarily powerful ones. A spoken interview on where control evaluations can fail, and a section on why control evaluations only look at what a model can do, are optional and folded.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: In a control evaluation, a red team searches for strategies
to:: and doing technique development to improve the weaknesses that they uncover.

#### Callout: Quick recall
#### Question: Open
id:: d2beb61b-ae14-4b9b-bbbf-021602c1c19b
content:: In a control evaluation, what does the red team do? And what two conditions must hold for the evaluation to be conservative, so that it does not underestimate the risk?
assessment-instructions:: Score out of 100. 40: the red team's job: it searches for attacks, strategies the untrusted models could follow to cause an unacceptable outcome, and checks whether the models are able to carry them out, so that safety can be estimated from how likely an unacceptable outcome would be if the models used those attacks. An answer that says the red team looks for ways a scheming model could get past the safety measures and tests whether the model can do them earns the full 40. 30: the first condition: the red team must be at least as good at finding attacks as a scheming model would be. 30: the second condition: the models' capabilities must be measured in a way the model cannot sabotage, for example by deliberately doing worse on the tests. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The red team searches for attacks, strategies the untrusted models could use to cause an unacceptable outcome, and checks whether the models can carry them out. Safety is estimated from the chance of an unacceptable outcome if the models used those attacks. For this to be conservative, the red team must be at least as good at finding attacks as scheming models, and the models' capabilities must be measured in a way that holds up even if the model tries to sabotage the measurement."
force-feedback:: first
feedback-instructions:: In at most five sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. The red team searches for attacks the untrusted models could use and checks whether the models can carry them out. The two conditions: the red team is at least as good at finding attacks as scheming models, and capabilities are measured in a way the model cannot sabotage. Add that the authors expect both to be achievable for early transformatively useful AIs because those AIs have less serial thinking time, less information about the countermeasures and no chance to practise, and that they still read a measured risk under 1% as more like 5 to 20%. No follow-up questions. Tell them to move on.
#### End Callout

#### Callout: Optional: where evaluation runs out
collapse:: closed
#### Text
optional:: true
content::
\#### When do capability evaluations stop being informative?

The reading argues control is evaluable: given a scary model and a protocol, you can check whether the model is controlled by running capability evaluations. This part is a short spoken interview rather than a written answer. Each question builds on your previous answer, so you will be pushed from finding a weak spot, to testing it against the authors' own defenses, to deciding what you would do about it.

#### Interview
id:: b4a356fc-ded4-4ba7-84be-ae38cbb415ea
optional:: true
content:: Three spoken questions, one at a time, each building on your last answer: where a capability evaluation stops telling you the truth, whether the authors' defenses cover that case, and what you would do about it if you ran the lab. There is no single right answer. The interviewer will ask you to take your reasoning a step further. About twelve minutes. You can switch to typing at any time.
questions::
- The reading argues control is evaluable: a red team searches for attacks, and you measure whether the model could carry them out. Describe a concrete situation, a specific model and a specific capability, in which that evaluation comes back saying "safe" and is wrong. What exactly came apart between what the evaluation measured and what the model can really do? What would the model need in order to cause that failure, and would an early transformatively useful model have it?
- The authors expect evaluations to hold for early transformatively useful models because the red team has three advantages over the model: more serial thinking time, more information about the countermeasures, and the chance to fail, learn and try again. Take the failure you just described. Which of those advantages is supposed to stop it, and what would have to be true of the model or its deployment for that advantage to disappear? Would your failure need just one of the three advantages gone, or all of them? If none of the three covers it, say so and what that means for the authors' argument.
- The authors write that if a careful control evaluation estimates under a 1 percent chance of catastrophe, the real risk conditional on scheming is probably more like 5 to 20 percent, because the evaluation itself can fail. Suppose you run the lab, and the failure you described is the one keeping you up at night. What is the earliest observable sign that your evaluations have stopped being informative, and what would you do when you saw it? What does that cost you, and would you still do it if a competitor did not?
assessment-instructions::
**Context for all three questions.** The learner has read the post from the opening through the section on evaluating control, ending at "doing technique development to improve the weaknesses that they uncover". That passage supplies: the two conditions for a conservative control evaluation (the red team must be at least as good at finding attacks as scheming models, and capabilities must be measured in a way robust to the model sabotaging the evaluation). The three disadvantages the authors say AIs have relative to the red team (less serial thinking time, since reasoning outside a forward pass happens in monitored natural language, with "neuralese" named as what would erode this. Less information about countermeasures. Little practice and no iteration, since a caught AI is worse off and limited memory stops it learning from failures). And the authors' own estimate that a measured risk under 1% probably means 5% to 20% actual risk conditional on scheming.

This is a reasoning interview, not a knowledge check. There is no correct conclusion. Score how far and how concretely the learner carries the reasoning, never whether they agree with the authors. A learner who concludes the authors' defenses hold and one who concludes they fail can both score 4. Credit revisions: a learner who changes an earlier answer because a later question exposed a problem with it is showing exactly the skill being tested. The transcript is the only evidence. Do not score fluency, pauses or restarts.

**Question 1: find the failure**

Reference points from the lens (the learner need not match them. Another genuine mechanism is worth the same): an evaluation is informative only while what it measures stays representative of the model's real dangerous capability. Two ways that breaks: sandbagging, where a situationally aware model detects evaluation conditions and underperforms deliberately or selectively. And the red team ceiling, where the model's attacks are qualitatively beyond what the red team generates, so the attack space explored underrepresents a scheming model's.

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

Nothing in the lens gives an answer here. Grade the reasoning.

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
id:: 7264e7a9-7257-450e-b10e-63a3fca46872
content:: Why is control more tractable to evaluate than alignment?
assessment-instructions:: Score out of 100. 50: control reduces to a capability question, whether the model is able to subvert the safety measures, and capabilities can be measured, with a red team searching for attacks and testing whether the model can carry them out. 50: alignment is much harder to evaluate: whatever behaviour you observe, the model might be acting that way to make you think it is aligned, so behaviour cannot settle it. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Evaluating control only requires evaluating capabilities: whether the model is able to subvert the safety measures. Evaluating alignment is much harder because whatever behavior a model displays, it might be behaving that way to make you think it is aligned."
force-feedback:: first
feedback-instructions:: In at most four sentences: confirm what the learner got right and, if anything is missing or wrong, the most important thing, then state the model answer. Control reduces to a capability question, whether the model is able to subvert the safety measures, and capabilities are something we know how to measure. Alignment evaluation is blocked because any behavior you observe might be produced precisely to make you think the model is aligned. No follow-up questions. Tell them to move on.
#### End Callout

#### Text
content::
Greenblatt and Shlegeris wrote this in January 2024. In September 2025 Apollo Research, working with OpenAI, published evidence that models already notice when they are being tested and sometimes behave better because of it. Four short excerpts follow. The first is Apollo's definition of scheming. The same ability is also a problem for control: Greenblatt and Shlegeris's second condition for a control evaluation is measuring capabilities in a way the model cannot sabotage, and a model that can tell when it is being tested could deliberately underperform on the capability evaluations that decide which models count as trusted.

#### Article
source:: [[../articles/apolloresearch-stress-testing-deliberative-alignment-for-anti-scheming-training]]
from:: Future, highly capable AI systems might covertly pursue misaligned goals
to:: not just _whether_ change occurs.

#### Question: Open
id:: 9a2499dd-3403-4958-8fdf-9bc974e61a71
content:: A model writes buggy code because it learned bad habits from buggy training data. It does this whether or not anyone is watching, and it makes no effort to hide the bugs. Is it scheming? Use Apollo's three components to explain. Then say why, if a model were scheming, training that makes the bad behaviour disappear would not tell you much.
assessment-instructions:: Score out of 100. 50: not scheming, explained with the components: there is no sign of misaligned goals that it pursues across situations (goal-directedness), and it does not adjust to whether it is watched or tested (no use of situational awareness), and it does not hide anything. Full 50 for a clear "no" that uses at least two of the three components correctly. 25 for a "no" with only a vague reason. 50: a scheming model tries to hide its misalignment, so when the bad behaviour disappears after training, there are two explanations that look the same from outside: the training removed the scheming, or it taught the model to hide it better. Behaviour alone cannot tell them apart. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "No. The bugs are a bad habit, not a goal it pursues, it does the same whether or not anyone is watching, so it is not using situational awareness, and it is not hiding anything. With a scheming model, good behaviour after training could mean the scheming is gone or that the model got better at hiding it, and from the outside the two look the same."
force-feedback:: first
feedback-instructions:: The learner just read excerpts from Apollo Research's post on anti-scheming training and answered a question about them. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the three components and the paragraph on why scheming is different from other failure modes. No follow-up question. No generic praise.

#### Article
from:: Models sometimes display situational awareness
to:: gave the answers we wanted to see.

#### Article
from:: We found that OpenAI o4-mini and OpenAI o3 explicitly
to:: much more evaluation aware than current models.

#### Article
from:: Through counterfactual tests with OpenAI o3
to:: realizing that it is being evaluated.

#### Question: Open
id:: 64410269-abc0-45ec-a352-1a05805246e6
content:: A lab runs its safety tests on a new model, and the model behaves perfectly. Using Apollo's findings, give two different explanations for the clean result. Then say why a model that can tell when it is being tested is also a problem for control, not only for alignment.
assessment-instructions:: Score out of 100. 40: two explanations, 20 each: the model really does not have the tendency (or the training removed it), and the model noticed it was being tested and behaved well because of that (evaluation awareness), so the test no longer measures what it would do in deployment. Also accept: it learned to hide the behaviour better. 20: some link to Apollo's evidence, for example that models mention being evaluated in their reasoning, that this rose after anti-scheming training and to about 20% in a capabilities training run, or that reasoning about being evaluated was shown to reduce covert actions. 40: why it matters for control: control evaluations rely on measuring what a model is able to do, and a model that can tell it is being tested could deliberately underperform on those capability tests (sandbag), for example to look too weak to scheme and so be counted as trusted, or to hide that it can get past the safety measures. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Either the model really does not have the bad tendency, or it noticed it was being tested and behaved well for that reason. Apollo found models saying they were being evaluated, more often after training, and showed that this awareness reduces bad actions. For control, a model that knows when it is tested could hold back on the capability tests, look weaker than it is, get counted as trusted, or hide that it can beat the safety measures."
force-feedback:: first
feedback-instructions:: The learner just read excerpts from Apollo Research's post on anti-scheming training and answered a question about them. In at most four sentences: say plainly what they got right and, if anything is missing or wrong, the most important thing, then give the model answer so they leave with it. If they say they do not understand, point them to the parts on situational awareness and on the counterfactual tests, and the note before the excerpts. No follow-up question. No generic praise.

#### Callout: Optional: why control evaluations only look at what a model can do
collapse:: closed
#### Article
optional:: true
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: ## Control evaluations and black-box techniques
to:: We'll elaborate on why we think this is a good choice and details of the exact rules in the [[#^appendix-why-control-evaluations-are-conservative-about-inductive-biases-and-ai-internal-structure|Appendix "Why control evaluations are conservative about inductive biases and AI internal structure"]].

#### Question: Open
optional:: true
id:: 6caca5e1-cd71-4576-9a8c-9cb632e36584
content:: Why do the authors want control evaluations to rely only on what a model is not capable of doing, rather than on how it generalises or what its internals look like?
assessment-instructions:: Score out of 100. 60: evidence for control must not rest on assumptions about scheming models that might be wrong, and techniques that rely on how a model generalises or on its internal structure depend on exactly such assumptions about a model that may be working against you. 40: whether a model is capable of something can be checked with standard capability evaluations, so evidence of the form "the model cannot do this" is much easier to be confident in. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "To be confident in control, the evidence must not rest on wrong assumptions about how a scheming model behaves. Techniques that depend on how a model generalises or on its internal structure need such assumptions, and a scheming model could break them. Whether a model is capable of something can be measured with standard capability evaluations, so relying only on what the model cannot do is much easier to trust."
force-feedback:: first
feedback-instructions:: In at most four sentences: say what the learner got right and, if anything is missing or wrong, the most important thing, then give the model answer in your own words. Evidence for control must not rest on assumptions about scheming models that could be wrong, and techniques built on generalisation or internal structure need such assumptions. Capabilities can be measured with standard capability evaluations, so "the model cannot do this" is the easiest kind of evidence to trust. No follow-up questions. Tell them to move on.
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
force-feedback:: first
feedback-instructions:: In at most five sentences: say what the learner got right, then correct the most important gap. If they trusted Y because of its record, say plainly that good behaviour is what a scheming model would also show, and that passing the capability tests is what makes a model untrusted. If they missed the control alternative, state it in one sentence. No follow-up questions. Tell them to move on.
#### End Callout

#### Article
optional:: true
from:: # What might control techniques look like?
to:: See the Appendices [[#^appendix-a-long-list-of-control-techniques|"A long list of control techniques"]] and [[#^appendix-control-techniques-from-our-paper|"Control techniques from our paper"]] for more thoughts on what control techniques could look like.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Greenblatt, Ryan, and Buck Shlegeris. "The case for ensuring that powerful AIs are controlled." *AI Alignment Forum*, 24 Jan. 2024. [alignmentforum.org](https://www.alignmentforum.org/posts/kcKrE9mzEHrdqtDpE/the-case-for-ensuring-that-powerful-ais-are-controlled)
*The reading this lesson is built from. This lesson covers control evaluations, why alignment is harder to evaluate, black-box techniques, and what control techniques might look like.*

Apollo Research. "Stress Testing Deliberative Alignment for Anti-Scheming Training." Apollo Research, with OpenAI, 17 Sep. 2025. [apolloresearch.ai](https://www.apolloresearch.ai/research/stress-testing-deliberative-alignment-for-anti-scheming-training)
*The three excerpts on evaluation awareness.*

XLab. "The case for ensuring that powerful AIs are controlled." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/introduction/the-case-for-controlling-powerful-ais)
*The source lesson this page adapts.*
:::

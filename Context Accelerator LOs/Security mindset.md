---
id: 9d62a0ab-40f2-4404-8dee-1f6ae3e618ac
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the security mindset: asking how a plan could fail or be defeated, and resting safety on a few well-checked assumptions rather than on patching failures you happen to imagine. Use premortems and red-teaming to apply it.

## Requires

## Helpful first

## Why it matters
Many safety proposals are judged by how they would work, not by how they could be defeated. With this habit you can spot proposals that only hold if nobody, human or AI, looks for a way around them, and you can find the flaws in your own ideas before others do.

## Lenses

## Tests

#### Question: Choice
id:: 2b4229b0-522f-4557-bfa3-8f8f71793de7
content:: The security mindset is often contrasted with "ordinary paranoia". What does ordinary paranoia mean in this contrast?
options::
- [x] Guarding against the specific attacks you can think of
- Refusing to trust any system or person
- Treating every user of a system as hostile
- Worrying mostly about very unlikely risks
shuffle:: true

#### Question: Choice
id:: f453f64c-36f4-4dee-8206-477f585330eb
content:: In a premortem, what does a team do before carrying out a plan?
options::
- [x] Imagine the plan has failed and explain why
- Estimate the probability that the plan succeeds
- List the resources and people the plan needs
- Review how similar past plans turned out
shuffle:: true

#### Question: Choice
id:: 9a49de43-0c95-48cb-9c3b-d669655d96f5
content:: A proposal says an advanced AI system will be shut down if it ever writes a message asking not to be shut down. What weakness would someone with the security mindset point to first?
options::
- [x] A system that wants to avoid shutdown can avoid writing the message
- The rule could be triggered by mistake by harmless messages
- Checking every message would slow down the system's replies
- The rule would be hard to explain to the public
shuffle:: true

#### Question: Choice
id:: 8ef26294-95b9-4fa2-9665-8292163ecf5e
content:: A developer fixes each harmful behavior of a capable AI system as it is found, one patch at a time. From a security-mindset view, what is the main risk of this approach?
options::
- [x] The system shifts to similar behaviors the patches don't cover
- The patches gradually make the system less capable
- The system loses the ability to learn new tasks
- The harmful behaviors become harder to reproduce in testing
shuffle:: true

#### Question: Choice
id:: 0f2d7c42-a4cd-4bff-981a-d3ef80c76b8c
content:: An AI lab plans to catch deceptive models with a new evaluation. Which question best reflects the security mindset?
options::
- [x] What would a model that wanted to pass this evaluation do?
- How accurate was the evaluation on earlier models?
- How quickly can the evaluation be run on each model?
- Do other labs use a similar evaluation?
shuffle:: true

#### Question: Choice
id:: 54fe9997-16a8-4c15-966d-80ab1d2e5554
content:: What does it mean to red-team your own safety proposal?
options::
- [x] Try hard to find ways it could be defeated
- Ask supportive colleagues to list its strengths
- Compare it point by point with rival proposals
- Rehearse presenting it to a skeptical audience
shuffle:: true

#### Question: Choice
id:: bd7975f0-efe3-4800-81e6-1d0073332126
content:: In computer security, why is "attackers don't know how our system works" considered a weak basis for safety?
options::
- [x] Details tend to leak, and then nothing else protects the system
- It makes the system harder for its own staff to maintain
- It only protects against attackers outside the company
- It forces the system to be redesigned every few years
shuffle:: true

#### Question: Open
id:: f1082ca1-e0da-4a0e-a506-0ec917a841f7
content:: A safety case for an AI system rests on 20 separate assumptions, each about 95% likely to hold. Why is this weaker than it sounds?
assessment-instructions:: Score out of 100. 100 for saying that safety needs all the assumptions to hold at once, so the chance they all hold is much lower than 95% (about 36% if they are independent). Also accept: any single failed assumption may be enough for a system or attacker to get through. 50 for "too many assumptions" with no reason.

#### Question: Open
id:: 690545b1-15ea-4f0d-8610-684136ffcf6f
content:: Run a short premortem on this plan: "We will keep a powerful AI system safe by letting it only answer questions, never act in the world." Give one plausible reason the plan failed.
assessment-instructions:: Score out of 100. 100 for any one plausible failure, such as: people act on its answers, so answers are actions; it persuades or manipulates its operators; its answers include code that people run; commercial pressure leads to giving it more autonomy; its weights leak or are copied. 40 for a vague "it escaped" with no route.

#### Question: Open
id:: 3133d370-2796-4298-b639-dbe5f71ded30
content:: Why is it hard for the designer of a safety plan to apply the security mindset to their own plan?
assessment-instructions:: Score out of 100. 100 for any one of: designers picture how the plan works, not how it breaks; the failures they missed are the ones they didn't think of, so they are hard to see; they want the plan to succeed, which biases their review; they test against the attacks they designed for. 50 for "bias" with no explanation.

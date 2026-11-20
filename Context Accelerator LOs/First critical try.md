---
id: c348cdbc-f6c5-46e0-982e-f33c350a2a63
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the first-critical-try argument for why trial and error can't be relied on to align powerful AI, tell it apart from common misreadings, and describe where critics such as Paul Christiano disagree.

## Requires
- [[Alignment difficulty arguments]]

## Helpful first

## Why it matters
Most technologies, from aircraft to medicines, became safe by learning from failures. If the first failure of a powerful enough AI can't be undone, that route closes, so safety has to come from work done beforehand. Knowing exactly what the argument claims lets you judge plans that rely on fixing problems as they appear.

## Lenses
- [[../Lenses/IABIED - The One-Chance Problem|The One-Chance Problem]]: Chernobyl, the Titanic, and why superintelligence gives no second time.
- [[../Lenses/IABIED - QA - Slow AI Integration|What if AI is developed only slowly?]]: why the Before/After problem remains under slow development.
- [[../Lenses/AFSRA - AGI Ruin, A List of Lethalities|AGI Ruin: A List of Lethalities]]: Yudkowsky's case, including the first critical try.
- [[../Lenses/AI Safety Atlas - Capabilities - Takeoff|Takeoff]]: why takeoff speed decides whether patching as you go is possible.
- [Where I agree and disagree with Eliezer](https://www.alignmentforum.org/posts/CoZhXrhpQxpy9xw9y/where-i-agree-and-disagree-with-eliezer) (Paul Christiano, 2022): accepts the first critical try but argues we can learn a lot before it.

## Tests

#### Question: Choice
id:: 18e37e4a-721d-4b96-98de-8cdb6606616c
content:: In the first-critical-try argument about AI alignment, what makes an attempt the "critical" one?
options::
- [x] It is the first system that could cause unrecoverable harm if misaligned
- It is the first system to beat human experts on most benchmarks
- It is the first model a lab tests for dangerous capabilities
- It is the first model trained above a legal compute threshold
shuffle:: true

#### Question: Choice
id:: 438e1737-4c6c-46be-93bc-82947f554a69
content:: Is the first-critical-try argument mainly about how hard the alignment target is to hit, or about how many chances we get to hit it?
options::
- [x] How many chances we get to fix mistakes
- How hard good values are to specify

#### Question: Choice
id:: 84fe395a-836f-47ef-8f52-91ef8fca03b2
content:: Supporters of the first-critical-try argument say alignment lessons from weaker AI systems may not carry over to the critical system. Why?
options::
- [x] Some failure modes only appear once a system could actually take control
- Stronger systems are trained on different data than weaker ones
- Safety tests on weaker systems cost too much to repeat at scale
- Weaker systems are too simple to show misbehaviour in testing
shuffle:: true

#### Question: Choice
id:: 85bc4a02-38f9-4d4b-b040-bf4f857e8587
content:: Eliezer Yudkowsky and Nate Soares argue that slow, gradual AI development would not remove the first-critical-try problem. What is their main reason?
options::
- [x] AI still eventually crosses a point where it could take power
- Competition between companies makes slow development impossible
- Gradual development gives AI more time to learn deception
- Slow development lets dangerous knowledge spread to more actors
shuffle:: true

#### Question: Choice
id:: 1c1621de-180c-4fc7-9cd4-736e6951c242
content:: Some critics expect that before any AI could overpower humanity, weaker AI systems will cause smaller, visible harms and speed up research, including alignment research. How does this bear on the first-critical-try argument?
options::
- [x] There may be more warning, and more AI help with alignment, before the critical point
- It shows a critical point will not arrive within this century
- It shows there will never be a critical point at all
- It shows that today's weaker systems are already aligned
shuffle:: true

#### Question: Choice
id:: 45ec9757-bcc5-4596-8c50-b44bd767fbd1
content:: If the first-critical-try argument is right, which approach can't be relied on to make the most capable AI systems safe?
options::
- [x] Deploying them and fixing problems once they show up in use
- Working out in advance why a safety method should hold
- Delaying development until safety methods are better understood
- Agreeing on international limits before the critical point
shuffle:: true

#### Question: Choice
id:: 8b41417c-6a54-497b-8aa9-55bca07fd13a
content:: Which historical case shares the key feature that the first-critical-try argument attributes to aligning powerful AI?
options::
- [x] The first nuclear test, where atmospheric ignition was ruled out by calculation
- Early passenger flight, made safer by investigating each crash
- Ocean liners after the Titanic, when lifeboat rules were reformed
- Car safety, improved by studying crash data over decades
shuffle:: true

#### Question: Choice
id:: 5d2f74d5-765c-4923-bf9c-7597b0c68746
content:: A lab plans to test a model in a sandbox, train away every misbehaviour it sees, then scale the model up 100 times and deploy it. What is the first-critical-try objection to this plan?
options::
- [x] If the scaled model is misaligned, there may be no chance to notice and fix it
- Sandbox tests make the model less capable than it will be in use
- Training away misbehaviour makes models refuse more useful tasks
- Misbehaviour in the small model proves the scaled model will be misaligned
shuffle:: true

#### Question: Open
id:: d466bed8-62ea-4036-b797-a88e608ae986
content:: In two or three sentences, explain why the first-critical-try argument says aligning powerful AI differs from most engineering problems people have solved.
assessment-instructions:: Score out of 100. 100 for: we usually make technology safe by seeing failures and fixing them, but a misaligned AI powerful enough to take control or cause catastrophe may leave no chance to learn and retry, so alignment has to work the first time. 50 if it only says AI is new or hard, without the point that the failure can't be undone.

#### Question: Open
id:: 0202f916-8059-4ed0-9e80-64231ef37026
content:: Paul Christiano agrees that AI alignment must work on the first critical try, but rejects a stronger claim that he says Eliezer Yudkowsky sometimes runs together with it. What is the stronger claim, and why does the difference matter?
assessment-instructions:: Score out of 100. 100 for: the stronger claim is that nothing can be learned about alignment from experiments and failures before the critical try; if it is false, work on weaker systems can still teach a lot before the critical point. 60 for naming the claim without saying why the difference matters.

#### Question: Open
id:: a782e696-3aa9-4c90-83b2-2fc431f06bfb
content:: Name one condition under which a misaligned AI's first serious failure would still be recoverable, and say why.
assessment-instructions:: Score out of 100. 100 for any one condition with a reason: the AI is not yet capable enough to take control or cause irreversible harm; monitoring or control measures catch and stop the attempt; humans or other AIs can still shut it down; the failure is limited and visible, so people can learn from it. 50 for a condition with no reason.

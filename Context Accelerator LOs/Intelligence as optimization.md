---
id: d19b0c3a-3883-4478-b7d6-8cf7f0741c9b
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe intelligence as the ability to steer the world into narrow target states across many domains, contrast it with other definitions, and explain why differences between humans may be a poor guide to how capable AI could be.

## Requires

## Helpful first

## Why it matters
If you picture a superintelligence as a very clever human, you may expect to outwit or contain it the way societies handle clever people. The optimization framing suggests the human range is a narrow band on a much longer scale, which changes how much margin for error safety plans can assume.

## Lenses
- [[../Lenses/Efficient Cross-Domain Optimization|Efficient Cross-Domain Optimization]]: Yudkowsky's definition of intelligence as steering the future across many domains with few resources. It covers Deep Blue, bees and beavers as narrow optimizers, evolution as a slow, wasteful one, and why the asteroid and the tiger are no match for a cross-domain mind (2008).
- [[../articles/urban-artificial-intelligence-revolution|The Road to Superintelligence]]: read the section "The Road From AGI to ASI". It covers why everyone from the "village idiot" to Einstein sits in a tiny band of the intelligence scale, and the limits on speed, size and reliability that human brains share and machines need not (2015).
- [[../Lenses/AI Safety Atlas - Capabilities - Defining and Measuring AGI|Defining and Measuring AGI]]: read only the "Case Studies" section. It sets intelligence as goal achievement (Legg and Hutter) beside skill-acquisition efficiency (Chollet), Turing's behaviourism and consciousness-based views, and explains why capability is what matters for safety.
- [Measuring Optimization Power (LessWrong)](https://www.lesswrong.com/posts/Q4hLMDrFd8fbteeZ8/measuring-optimization-power): Yudkowsky's proposal to measure optimization by how small a fraction of possible outcomes is as good or better by the optimizer's preferences, counted in bits (October 2008) (more advanced).

## Tests
#### Question: Choice
id:: 4c91fa4b-12d4-418f-aadd-55dc4edf627a
content:: When intelligence is framed as optimization power, what makes one system more intelligent than another?
options::
- [x] It reliably reaches rarer, more specific outcomes in more domains
- It processes more information per second
- It has memorised more facts about the world
- It has a richer conscious experience of its reasoning
shuffle:: true

#### Question: Choice
id:: 5f2743db-8435-428b-8330-4c36fce5a291
content:: A chess engine beats every human at chess but can do nothing else. In the framing of intelligence as optimization power, how is it best described?
options::
- [x] A strong optimizer in one narrow domain, not a general intelligence
- A general intelligence, since it beats every human at a hard task
- Not an optimizer at all, since it only follows its programming
- As intelligent as a human, but slower to learn new things
shuffle:: true

#### Question: Choice
id:: 90e7dbf2-2de7-4945-83aa-7263c25e0374
content:: A safety plan assumes that if an advanced AI system ever worked against us, we could contain it the way societies contain a brilliant but dangerous person. What does the framing of intelligence as optimization power suggest about this assumption?
options::
- [x] It may fail, because an AI's capability need not stop near the top of the human range
- It is sound, because the most capable humans mark roughly the upper limit of intelligence
- It may fail, but only because AI systems run on hardware that is hard to switch off
- It does not bear on it, because the framing measures intelligence and says nothing about safety
shuffle:: true

#### Question: Choice
id:: 0a2b8360-2fd9-4e67-a88e-a5879b005423
content:: Proponents of the optimization framing argue that the range of intelligence among humans is narrow compared with the range of possible minds. Which reason do they give?
options::
- [x] All humans share nearly the same brain design, shaped by the same evolutionary limits
- Human brains have already reached the physical limits of computation
- IQ tests show that most people score close to 100
- Human intelligence is mostly fixed by education, which is similar everywhere
shuffle:: true

#### Question: Choice
id:: 12a874d4-6b45-4772-9cb6-cfceb6cc438e
content:: An AI system is superb at maths but poor at persuading people, planning around other agents and handling unfamiliar situations. In the framing of intelligence as optimization power, how does this bear on how intelligent it is?
options::
- [x] It counts against it: those are domains where it can't steer outcomes
- It doesn't matter: the framing measures abstract reasoning such as maths
- It doesn't matter: social skill is a separate trait from intelligence
- It counts in its favour: specialised systems are stronger optimizers
shuffle:: true

#### Question: Choice
id:: acb156e2-e665-4ec2-be17-324eff3f4944
content:: Shane Legg and Marcus Hutter proposed a widely cited definition of intelligence that is close to the optimization framing. Which is it?
options::
- [x] An agent's ability to achieve goals in a wide range of environments
- How closely an agent's reasoning resembles that of a human expert
- An agent's score across a broad battery of IQ-style puzzles
- An agent's ability to hold conversations indistinguishable from a human's
shuffle:: true

#### Question: Choice
id:: 0f7393fe-29f3-4cdc-b3cf-c15650c25541
content:: François Chollet defines intelligence as skill-acquisition efficiency. How does this differ from the framing of intelligence as optimization power?
options::
- [x] It rates how efficiently a system learns new skills, not how well it already steers outcomes
- It rates how many facts a system has stored, not how well it uses them to reach goals
- It rates how closely a system imitates human reasoning, not which outcomes it achieves
- It rates how fast a system runs its computations, not how much it learns from them
shuffle:: true

#### Question: Choice
id:: 8dbd11c4-dea4-401f-a725-c0d4d3f769b2
content:: Someone says: "AI systems don't really understand anything, they just predict the next word, so they can't be a serious threat." How does the framing of intelligence as optimization power respond?
options::
- [x] What matters is which outcomes a system can reliably bring about, not whether it understands as humans do
- It agrees: a system without human-like understanding cannot steer outcomes at all
- It disagrees, because it holds that current AI systems are already conscious
- It agrees for today's systems, since the framing only applies to systems with explicit goals
shuffle:: true

#### Question: Choice
id:: c4119f6c-4cb3-418c-bedf-6a5ba6476c97
content:: In the framing of intelligence as optimization power, does natural selection count as an optimization process?
options::
- [x] Yes: it reliably produces rare, well-adapted designs, though slowly and without foresight
- No: it has no mind or goals, so it can't push outcomes in any direction

#### Question: Choice
id:: e25b3357-3eae-43e9-b1f5-2a613b9608a7
content:: One proposed way to measure how much optimization power produced an outcome is to ask which of these?
options::
- [x] How small a fraction of possible outcomes is at least as good, by the optimizer's preferences
- How much computing power the optimizer used to produce the outcome
- How long the optimizer took to reach the outcome
- How many separate steps the optimizer's plan contained
shuffle:: true

#### Question: Open
id:: 92235431-90fb-4553-ae4c-e8532f5fd833
content:: What does it mean to describe intelligence as the ability to "steer the world into narrow target states"? Answer in one or two sentences.
assessment-instructions:: Score out of 100. 100 for saying an intelligent system reliably brings about specific outcomes that would be very unlikely by chance or by default, judged by results rather than inner workings. Mentioning many domains is a plus but not required. 50 for "achieving goals" with no idea of narrow or improbable targets.

#### Question: Open
id:: 3984cc45-0d50-4c5e-970a-1fc0f0c714ef
content:: Give one reason why intuitions from comparing smarter and less smart humans might mislead us about how capable an AI system could become.
assessment-instructions:: Score out of 100. 100 for any one of: the human range may be a small part of the range of possible minds; all humans share one brain design with the same limits on size, speed and lifespan, which AI need not share; the smartest human is a poor guide to the upper limit. 40 for a vague "AI is different" with no reason.

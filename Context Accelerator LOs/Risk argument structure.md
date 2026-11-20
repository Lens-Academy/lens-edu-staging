---
id: 496fe432-f7b4-4bea-905f-c350b7755bcc
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Lay out the main steps of the case that AI could cause an existential catastrophe, explain how chained steps and separate routes affect its overall probability, and say which step a given objection attacks.

## Requires
- [[Existential risk]]
- [[AGI and superintelligence]]

## Helpful first
- [[Orthogonality thesis]]
- [[Instrumental convergence]]
- [[AI alignment]]

## Why it matters
Debates about AI risk often go in circles because people attack different steps of the argument without saying so. If you can tell which step an objection targets, you can find where you actually disagree, weigh the objection fairly, and avoid treating a rebuttal of one step as a rebuttal of the whole case.

## Lenses
- [[../Lenses/carlsmith-is-power-seeking-ai-an-existential-risk|Is Power-Seeking AI an Existential Risk?]]: Joe Carlsmith's six-step argument, each premise conditional on the ones before, and how multiplying his credences gives about 5%, with the biases of many-step estimates; read Section 1 (Introduction, to 1.1) and Section 8 (Probabilities) only (2021; his own estimate later rose above 10%).
- [[../Lenses/Risks from power-seeking AI|Risks from power-seeking AI]]: 80,000 Hours' five-claim version of the case, then common objections ("they'll just be tools", "they won't be smarter than us", "a truly intelligent AI would be moral", "just unplug it") each answered at the claim it targets; read the opening list of claims and "What are the arguments against working on this problem?" (2026).
- [[../Lenses/AFSRA - AGI ruin scenarios are likely (and disjunctive)|AGI ruin scenarios are likely (and disjunctive)]]: Nate Soares on why survival needs many things to go right at once, and why correlated steps can't simply be multiplied, from the pessimistic end of the debate (2022).
- [Counterarguments to the basic AI x-risk case (AI Impacts)](https://aiimpacts.org/counterarguments-to-the-basic-ai-x-risk-case/): a critic's view, from Katja Grace. She sets out the case in three steps (goal-directed AI, bad goals, able to overpower us) and groups her objections by the step each attacks; read the outline of the basic case, then two or three counterarguments (August 2022).

## Tests

#### Question: Choice
id:: 3b3aef25-983e-4add-9f4f-ee8790338235
content:: An argument for AI risk is described as disjunctive. What does that mean?
options::
- [x] It offers several separate routes to catastrophe, any one of which is enough
- It has several steps, all of which must hold for catastrophe to follow
- Its conclusion holds only if its steps are independent of each other
- It describes one specific scenario in which AI causes catastrophe
shuffle:: true

#### Question: Choice
id:: 91a564eb-e169-490a-98a1-4ed3fe245884
content:: Someone splits the case for AI risk into many steps that must all hold, gives each a moderate probability, and multiplies them to get a low overall risk. Critics call this the "multiple-stage fallacy". Which of these is one of their criticisms?
options::
- [x] Each step should be judged assuming the earlier steps happened, which can make it much likelier
- Each step should be judged on its own, ignoring whether the earlier steps happened
- The method overstates the risk, since each extra step adds another chance of catastrophe
- Steps about future events are too uncertain to be given probabilities at all
shuffle:: true

#### Question: Choice
id:: 7066cb1e-12ef-4cf7-a0b2-08292a142367
content:: Objection to the AI risk argument: "Advanced AI will be a tool that does what we ask; it won't pursue goals of its own." Which step does this mainly target?
options::
- [x] That advanced AI will act as an agent pursuing goals
- That highly capable AI will be built
- That humans will fail to correct or stop it in time
- That it will seek power to pursue its goals
shuffle:: true

#### Question: Choice
id:: 828866e9-7fb7-4a1b-9694-7284e0cd1157
content:: Objection to the AI risk argument: "Long before AI could take over, we'll see smaller failures and shut down or fix the systems that misbehave." Which step does this mainly target?
options::
- [x] That humans will fail to correct or stop misaligned AI in time
- That AI's goals will differ from what its developers intended
- That a misaligned AI will seek power to pursue its goals
- That AI much more capable than humans is possible
shuffle:: true

#### Question: Choice
id:: ab07ddcd-7c59-4c71-b2a4-260b80a56b7d
content:: Objection to the AI risk argument: "A smarter AI will understand human values better, so it will behave more morally." Which step does this mainly target?
options::
- [x] That AI's goals will differ from what its developers intended
- That advanced AI will act as an agent pursuing goals
- That a misaligned AI will seek power to pursue its goals
- That humans will fail to correct or stop it in time
shuffle:: true

#### Question: Choice
id:: aa00d57b-0c3e-48aa-95b3-a2d6e7a085ff
content:: Objection to the AI risk argument: "Even if AI took control for a while, humanity could later win it back." Which step does this mainly target?
options::
- [x] That losing control to AI would be permanent
- That AI's goals will differ from what its developers intended
- That a misaligned AI will seek power to pursue its goals
- That highly capable AI will be built
shuffle:: true

#### Question: Choice
id:: ec19d39d-34d1-4b41-85f7-fc47a41b4437
content:: Forecasts of human-level AI range from a few years to several decades away. Suppose it turns out to be several decades away. What does this do to the case for existential risk from AI?
options::
- [x] It leaves the goal and power-seeking steps intact, though more time could help us prepare
- It shows the risk can safely be ignored until human-level AI is much closer
- It mainly weakens the step that AI's goals will differ from what developers intended
- It makes misuse, not misalignment, the main remaining route to catastrophe
shuffle:: true

#### Question: Choice
id:: 13d27b94-4084-47af-87e0-81b73488c5e8
content:: The instrumental convergence argument says agents with many different final goals would seek resources and self-preservation. Which step of the case for AI risk does it mainly support?
options::
- [x] That a misaligned AI would seek power and resist being shut down
- That AI's goals will differ from what its developers intended
- That highly capable AI will be built
- That humans will fail to notice the problem in time
shuffle:: true

#### Question: Choice
id:: 84317195-1e45-46a2-919a-ff96cf60e562
content:: Suppose someone shows convincingly that AI alignment will be solved before AI becomes very capable. Which route to catastrophe does this still leave open?
options::
- [x] People deliberately using obedient AI to cause mass harm
- AI pursuing goals its developers didn't intend
- AI deceiving its developers during training
- AI seeking power against its developers' wishes
shuffle:: true

#### Question: Choice
id:: d5db1532-2022-47fe-a6f5-0fcfd9e18d8f
content:: Which step do the misalignment route and the misuse route to AI catastrophe have in common?
options::
- [x] Very capable AI systems get built
- AI develops goals its developers didn't intend
- Malicious groups gain access to frontier models
- AI resists attempts to shut it down
shuffle:: true

#### Question: Open
id:: 3faee779-f79f-4471-b9a7-79c0d531a141
content:: Give one common objection to the case for existential risk from AI, and say which step of the argument it targets.
assessment-instructions:: Score out of 100. 100 for a recognisable objection matched to the right step, e.g. "AI is far off" (capable AI gets built soon), "AI will be a tool" (agency), "smart AI will be moral" (misaligned goals), "we'll notice and fix it" (failure to correct), "we could recover" (permanence). 50 if the objection is fine but the step is vague or mismatched.

#### Question: Open
id:: 661b631d-1737-42cd-a8bd-84591db95ae2
content:: Why doesn't showing that one specific AI takeover story is implausible refute the case for existential risk from AI?
assessment-instructions:: Score out of 100. 100 for saying the case doesn't depend on any one scenario: it rests on general premises (capable, misaligned, power-seeking AI that isn't stopped), and there are many possible routes or methods, any of which could lead to catastrophe. 50 for only saying "there are other scenarios" without linking this to the argument's premises or its many routes.

#### Question: Open
id:: 55b4ae8c-a286-4f85-8e8d-07c2da6f995a
content:: Why does the case for existential risk from AI need the step "humans fail to correct the AI in time", and not only the step "AI ends up with unintended goals"?
assessment-instructions:: Score out of 100. 100 for saying that misalignment which is noticed and fixed, or contained, causes no catastrophe, so catastrophe also needs it to go uncorrected (e.g. through deception, speed, competitive pressure to deploy, or the AI resisting correction). 50 for restating that both steps are needed without saying why.

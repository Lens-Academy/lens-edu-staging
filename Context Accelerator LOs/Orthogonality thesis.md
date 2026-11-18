---
id: 7606a7cf-138c-46c1-80f1-e63fa81a1a4d
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what the orthogonality thesis claims about intelligence and goals, and what it does and does not imply about how likely misaligned AI is.

## Requires
- [[Intelligence as optimization]]
- [[Terminal and instrumental goals]]

## Helpful first
- [[Understanding vs. caring]]

## Why it matters
Many people assume a smart enough AI would end up with good goals. The orthogonality thesis shows that capability alone gives no such guarantee, so good goals have to come from how a system is built and trained. Knowing its limits also stops you from overstating it as proof that misalignment is likely.

## Lenses

## Tests

#### Question: Choice
id:: fb9a43e5-319a-4fd8-ac66-e90e7f0db719
content:: What does the orthogonality thesis claim?
options::
- [x] Almost any level of intelligence can in principle be combined with almost any final goal
- An agent's intelligence can be measured separately from its goals
- More intelligent agents tend to pursue more complex final goals
- AI systems acquire their goals and their capabilities in separate stages of training
shuffle:: true

#### Question: Choice
id:: 689dde96-4eec-4553-86eb-4c01809b7332
content:: Does the orthogonality thesis, on its own, imply that a superintelligent AI will probably have goals that are harmful to humans?
options::
- [x] No
- Yes

#### Question: Choice
id:: 68cc615b-cad4-4cd8-9486-faf756949daa
content:: A critic argues that AI systems trained on human data and rewarded for helping people will probably end up with benign goals. If the critic is right, does that contradict the orthogonality thesis?
options::
- [x] No
- Yes

#### Question: Choice
id:: 21d5b0c7-5a12-436e-afce-3e08dd84b8ea
content:: Why is the orthogonality thesis stated in terms of final goals rather than instrumental goals?
options::
- [x] Good choices of instrumental goals depend on intelligence, since smarter agents pick better means
- Instrumental goals are set by an agent's designer and cannot be changed
- Final goals are easier to observe in a trained AI system
- Instrumental goals matter only for agents below human level
shuffle:: true

#### Question: Choice
id:: ee86a15c-2dca-4a7c-9a29-b27f80e7f62d
content:: The orthogonality thesis says "almost any" level of intelligence is compatible with "almost any" final goal. Is it consistent with there being a few goals that a superintelligent agent could not hold, such as a goal of staying unable to reason?
options::
- [x] Yes
- No

#### Question: Choice
id:: 3a3737d6-51fd-4c84-8358-0903bb97a610
content:: If the orthogonality thesis is true, must an AI system's good goals come from something other than its level of intelligence, such as how it was trained?
options::
- [x] Yes
- No

#### Question: Choice
id:: fd5382b4-3cf0-474a-8291-631d1c0d417b
content:: Which of these claims, if true, would contradict the orthogonality thesis?
options::
- [x] Every sufficiently intelligent agent ends up with the same final goals
- Most AI systems trained on human data end up with humanlike goals
- Advanced AI systems tend to seek power and resources as a means to their goals
- Training methods sometimes give AI systems goals their developers did not intend
shuffle:: true

#### Question: Choice
id:: e84316b4-cebc-43e5-944e-2ba0223b9bb4
content:: Someone argues: "The most intelligent beings we know, humans, care about others, so intelligence leads to caring." What is the main weakness of this as an argument against the orthogonality thesis?
options::
- [x] Evolution shaped both human intelligence and human values, so the link may not hold for AI
- Humans are not intelligent enough to count as evidence about intelligent agents
- Caring about others is an instrumental goal for humans, not a final goal
- The orthogonality thesis applies only to AI systems that lack language
shuffle:: true

#### Question: Choice
id:: 0ef7ace8-ba0f-4f18-9be1-ac0874e70d57
content:: What role does the orthogonality thesis usually play in the argument that advanced AI could be dangerous?
options::
- [x] It answers the objection that a smart enough AI would have good goals automatically
- It shows that misaligned AI is the most likely result of current training methods
- It explains why AI systems with many different goals would seek power
- It gives a reason to expect AI to become superintelligent soon
shuffle:: true

#### Question: FillBlank
id:: 90e4b96c-f832-42bd-addc-63c7187ff18b
content:: The orthogonality thesis treats an agent's intelligence and its {{final goals|terminal goals|final goal|terminal goal|goals}} as two independent dimensions: in principle, almost any point on one can be combined with almost any point on the other.

#### Question: Open
id:: 7a15ef13-1155-4433-9597-6e49b3ae87ae
content:: Using the orthogonality thesis as your example, explain the difference between claiming that a combination of intelligence and goals is possible and claiming that it is likely.
assessment-instructions:: Score out of 100. 100 for saying the thesis only claims that high intelligence can be paired with almost any goal, while whether real AI systems will have bad goals depends on how they are built and trained. 50 if the answer explains only one of the two claims.

#### Question: Open
id:: 145d8789-2d32-4731-afd8-de976fc90458
content:: A friend says: "A superintelligent AI would be smart enough to work out what we really want, so it would do that." Using the orthogonality thesis, what is the gap in this reasoning?
assessment-instructions:: Score out of 100. 100 for saying that knowing what we want is not the same as wanting to do it: intelligence does not set an agent's final goals, and its goals decide what it does with that knowledge. 50 for "it might have other goals" without linking this to intelligence and goals being separate.

#### Question: Open
id:: 4a406dbc-0586-4936-9e22-e87ed142aa96
content:: The orthogonality thesis says that a superintelligent AI with goals harmful to humans is possible. Name one further claim you would need to argue that such an AI is likely.
assessment-instructions:: Score out of 100. 100 for any one of: training methods tend to give AI systems unintended goals; we cannot reliably check what goals a system has; goals that suit humans are a small target among possible goals; developers may deploy capable systems before their goals are verified. 50 for a vague answer such as "someone has to build it" with no reason it would get bad goals.

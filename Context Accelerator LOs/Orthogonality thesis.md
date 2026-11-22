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
Many people assume a smart enough AI would end up with good goals. The orthogonality thesis argues that capability alone gives no such guarantee, so whether an AI has good goals depends on how it is built and trained. Knowing the thesis's limits also stops you from overstating it as proof that misalignment is likely.

## Lenses
- [[../Lenses/AFSRA - Intelligence and Stupidity - The Orthogonality Thesis|Intelligence and Stupidity: The Orthogonality Thesis]]: Rob Miles uses the is-ought gap to show that terminal goals can't be "stupid", that intelligence is skill at reaching goals, and that understanding morality is not wanting to act on it (video, 2018).
- [[../Lenses/IABIED - QA - Orthogonality|Orthogonality: AIs Can Have (Almost) Any Goal]]: Yudkowsky and Soares on why a smarter mind doesn't come to care about different things, and why the thesis says nothing about which goals training will actually instil (2025).
- [A Tale of 2.5 Orthogonality Theses (EA Forum)](https://forum.effectivealtruism.org/posts/kCAcrjvXDt2evMpBz/a-tale-of-2-5-orthogonality-theses): separates "almost any pairing is possible" from "misaligned AI is likely", and argues that the case for risk needs more than orthogonality. One side of a live debate, from a critic of how the thesis is used (May 2022).
- [[../Lenses/bostrom-the-superintelligent-will-motivation-and-instrumental-rationality-in-advanced-artificial-agents|The Superintelligent Will]]: Bostrom's original statement of the thesis. It covers the caveats behind "more or less any" and why AI motives need not look human. Read section 1 and the Conclusions only (2012) (more advanced).
- [[../Lenses/lesswrong-orthogonality-thesis|Orthogonality thesis (LessWrong wiki)]] (Noah's CG list 🔴)

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
- [x] Which instrumental goals an agent picks depends on intelligence, since smarter agents choose better means
- Instrumental goals are fixed by an agent's designer, so intelligence cannot change them
- Final goals are easier than instrumental goals to observe in a trained AI system
- Instrumental goals tend to change over time, so no thesis about them could be stable
shuffle:: true

#### Question: Choice
id:: 5067cacc-9b17-4922-8cff-c31b9fbf71b6
content:: If the orthogonality thesis is true, can we count on a highly intelligent AI system having good goals just because it is highly intelligent?
options::
- [x] No
- Yes

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
- [x] Evolution shaped both human intelligence and human caring, so the link may not carry over to AI
- Caring about others is an instrumental goal for humans, not a final goal
- Many less intelligent animals also care for their young and for each other
- Human caring varies too much between cultures to count as a single goal
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

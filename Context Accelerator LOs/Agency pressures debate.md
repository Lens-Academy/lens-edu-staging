---
id: 727f4e7b-ff7c-479d-8634-ceb0b526d8f6
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main positions on whether advanced AI will be, and should be, autonomous and goal-directed, and the arguments for each, now that companies are already deploying AI agents.

## Requires
- [[AI agents]]
- [[Agents and goals]]

## Helpful first

## Why it matters
Many AI risk arguments, such as instrumental convergence, assume AI that pursues goals over long periods. As of late 2026, companies already deploy agents that complete tasks taking people many hours, but how goal-directed future systems will be, and whether tool-like designs stay viable, is still debated. This debate helps you judge which risk arguments fit the systems being built.

## Lenses
- [[../Lenses/gwern-why-tool-ais-want-to-be-agent-ais|Why Tool AIs Want to Be Agent AIs]]: the classic case that tool AIs lose out to agents: what "tool AI" means (Karnofsky's Google Maps example), why humans in the loop become the bottleneck, and why agency also makes AI smarter. Read the opening through "Economic" and the first part of "Intelligence", up to "every sufficiently hard problem becomes a reinforcement learning problem" (2016).
- [[../Lenses/shah-will-humans-build-goal-directed-agents|Will Humans Build Goal-Directed Agents?]]: Rohin Shah weighs the arguments for goal-directed AI (economic efficiency, beating human performance, reinforcement learning, evolution's example) and asks how far each really goes, including agents that act without being goal-directed (2019).
- [[../Lenses/carlsmith-is-power-seeking-ai-an-existential-risk|Is Power-Seeking AI an Existential Risk?]]: Section 3, "Incentives", only: reasons we might not build agentic planners, then three reasons we probably will (usefulness, available techniques, agency arising as a byproduct), and how a system of non-agentic parts can act as an agent (2021).
- [Reframing Superintelligence: Comprehensive AI Services as General Intelligence (LessWrong)](https://www.lesswrong.com/posts/x3fNwSe5aWZb5yXEG): Rohin Shah's summary of Drexler's CAIS proposal, that superhuman capability could come from many bounded AI services rather than one general agent, why that might be safer, and Shah's doubts; the post only, not the comments (January 2019).

## Tests

#### Question: Choice
id:: c0d5568b-e866-4f47-bb53-ce1976a6a651
content:: One argument against relying on tool AI is that agent AIs will outcompete tool AIs. What is the core reasoning?
options::
- [x] Agents skip slow human approval steps, so competitors gain by deploying them.
- Tool AIs are harder to train, so labs can't build them at scale.
- Regulators require agents for high-stakes uses, so tools lose those markets.
- Tool AIs need more compute to run, so they cost more per task.
shuffle:: true

#### Question: Choice
id:: 54b1fc6d-673a-45dd-a696-f3f507b0c024
content:: Some argue that very hard tasks, such as a new research project, need AI that chooses its actions by their predicted effects on an outcome. Why does this matter for AI risk?
options::
- [x] Planning that finds clever routes to a goal can also find harmful ones, like gaining resources or avoiding shutdown.
- AI that plans by outcomes needs far more training data, so it raises mainly privacy concerns.
- Planning by outcomes only works in games, so it says little about AI in the real world.
- AI that plans by outcomes always follows its instructions more strictly than other AI does.
shuffle:: true

#### Question: Choice
id:: c8d3c2f2-7983-4a24-9f79-7144cc38051d
content:: A lab finds its model solves hard problems better after reinforcement learning that rewards task success. Why do some see this as a push toward agentic AI?
options::
- [x] Rewarding success selects for strategies that pursue outcomes over many steps.
- Reinforcement learning gives models a longer memory for past conversations.
- Reinforcement learning makes models follow each written instruction more literally.
- Rewarding success makes models copy human-written answers more closely.
shuffle:: true

#### Question: Choice
id:: ce019617-79dd-4b62-88f7-19349a9a2c90
content:: In debates about whether AI will be agentic, which system is the best example of a "tool AI"?
options::
- [x] One that answers questions or proposes plans, while a human decides whether to act
- One that manages a company's ad budget, adjusting spending by itself
- A coding assistant that edits files, runs tests and submits changes unaided
- A trading system that buys and sells shares within limits a human set
shuffle:: true

#### Question: Choice
id:: 1e90fb8e-3b61-49c8-a810-6147b2e9921c
content:: Critics say the line between tool AI and agent AI is easy to cross. Which observation supports this?
options::
- [x] A question-answering model can be put in a loop that acts on its own answers.
- Tool AIs are trained on different data from agent AIs.
- Agent systems use a different neural network architecture from tool systems.
- Most tool AIs are closed-source, while most agents are open-source.
shuffle:: true

#### Question: Choice
id:: 9df81023-be2f-4ccb-8834-9242f7c87c68
content:: What does Eric Drexler's "Comprehensive AI Services" (CAIS) proposal claim?
options::
- [x] Superhuman capability could come from many bounded AI services, not one general agent.
- Superhuman capability will most likely come from one general agent that improves itself.
- AI services must stay below human level in every field to remain safe.
- General agents should be built first and then split into narrow services.
shuffle:: true

#### Question: Choice
id:: d9db81ff-678e-4b61-a2b5-aa9401b4cbf5
content:: A lab commits to building only tool-like AI that advises while humans decide and act. Which risk does this commitment do least to reduce?
options::
- [x] People using the AI's advice to plan a cyberattack
- The AI resisting being shut down or corrected
- The AI gathering resources to pursue its own goals
- The AI misleading its overseers to reach its own goals
shuffle:: true

#### Question: Choice
id:: dd485690-9c93-442a-aed1-3e1da27c8356
content:: Critics of the economic argument for agentic AI point out that agents often fail on long tasks. What is the strongest reply from those who expect agents to win out?
options::
- [x] The length of tasks agents can complete has been doubling every few months.
- Tool-style AI fails more often than agents on every kind of task.
- Firms will deploy agents whatever the cost, even if most tasks fail.
- Reliability matters little, because customers rarely check the results.
shuffle:: true

#### Question: Open
id:: 3a93acb1-4818-494a-9311-87aa5ab8aabc
content:: What is the difference between an AI being autonomous and being goal-directed? Give an example of a system that has one without the other.
assessment-instructions:: Score out of 100. Autonomous: acts without a human approving each step. Goal-directed: chooses actions to bring about outcomes. 100 for both definitions plus a valid example (e.g. a scripted bot running unattended is autonomous but barely goal-directed; a chess engine that only suggests moves is goal-directed but not autonomous). 50 for the distinction without a valid example.

#### Question: Open
id:: 8317ef1b-cc82-4378-bcee-abfe399008b1
content:: In one or two sentences, state the case for building tool AI instead of agents: what it proposes and why it might reduce risk.
assessment-instructions:: Score out of 100. Proposal: build AI that gives answers, advice or narrow services while humans decide and act. Why: systems without long-term goals of their own have less reason to seek power or resist correction, and humans stay in control of actions. 100 for both parts; 50 for one.

#### Question: Open
id:: 860d36e4-0f6d-4a22-94b8-701f9974cb77
content:: One reply to "hard tasks require agentic AI" is that hard tasks can be split into small steps, each done by a narrow system and checked by humans. Give one weakness of this reply.
assessment-instructions:: Score out of 100. 100 for any one of: someone or something must plan the split, which is itself agentic work; some tasks don't split cleanly; checking every step is slow, so competitors skip it; humans may rubber-stamp steps they can't evaluate; the combined system can behave like an agent as a whole. 50 for a vague answer such as "it might not work".

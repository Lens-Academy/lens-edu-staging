---
id: e440749a-1921-445c-82e1-29e81d70a6be
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what it means for a system to pursue goals, including why reaching the same outcome despite obstacles is a common sign, and tell apart senses of "agent": intentional stance, decision-theoretic, learning and planning systems, LLM-based AI agents.

## Requires

## Helpful first
- [[Intelligence as optimization]]

## Why it matters
Many AI risk arguments are stated in terms of agents with goals, but "agent" means different things in papers, textbooks and product launches. If you can tell which sense an argument relies on, you can check whether it applies to a given system instead of accepting or rejecting it because of the label.

## Lenses
- [AGI safety from first principles: Goals and Agency (LessWrong)](https://www.lesswrong.com/posts/bz5GdmCWj8o48726N/agi-safety-from-first-principles-goals-and-agency): Richard Ngo on why expected-utility maximization and the intentional stance alone don't tell you whether a system is goal-directed, and his six traits of agency (self-awareness, planning, consequentialism, scale, coherence, flexibility); read the introduction and "Frameworks for thinking about agency" (September 2020).
- [[../Lenses/adamshimi-literature-review-on-goal-directedness|Literature Review on Goal-Directedness]]: Dennett's intentional stance (thermostats included), why calling AlphaGo "trying to win" predicts the outcome even when you can't predict its moves, and why adapting to a changed environment is the clearest sign of a goal; read the "Explainability", "Generalization" and "Optimization" sections (January 2021).
- [[../Lenses/AI Safety Atlas - Goal Misgeneralization - Goal-Directedness|Goal-Directedness (AI Safety Atlas)]]: goal-directedness defined by behaviour rather than by internal search, and how language models can play goal-directed characters without having persistent goals of their own; read the opening, "Heuristics" and "Simulators" up to the Waluigi Effect box (2026).
- [I think "agent" may finally have a widely enough agreed upon definition to be useful jargon now (Simon Willison)](https://simonwillison.net/2025/Sep/18/agents/): the industry meaning of an LLM agent, "runs tools in a loop to achieve a goal", and the other uses of the word it sets aside (September 2025).

## Tests

#### Question: Choice
id:: 32a2eb6d-bacb-4e59-be68-dd3db5afa4d8
content:: Decision theory describes an ideally rational agent. What does that model assume about the agent's choices?
options::
- [x] They fit consistent preferences, given its beliefs
- They come from an explicit search over possible plans
- They reflect goals the agent is consciously aware of
- They always achieve the outcome the agent prefers
shuffle:: true

#### Question: Choice
id:: 01fb1db5-15e3-4d74-85db-02ba3d24725d
content:: In reinforcement learning textbooks, what does the word "agent" refer to?
options::
- [x] Whatever part of the system picks actions and learns from reward
- Only systems that plan several steps ahead before acting
- Only systems with goals they can describe in words
- Only systems that act in the world without human oversight
shuffle:: true

#### Question: Choice
id:: cb68b4c8-b089-4b05-88b0-8c3b3a0d2b20
content:: A company sells an "AI agent" that books travel by running a language model in a loop with web tools. What does the "agent" label tell you by itself?
options::
- [x] It carries out multistep tasks using tools
- It has stable long-term goals of its own
- It chooses actions by maximizing expected utility
- It was trained mainly by reinforcement learning
shuffle:: true

#### Question: Choice
id:: 963d240f-ea46-45fb-9192-542a4a8c95dd
content:: Which of these systems steers toward its target without any explicit search over plans?
options::
- [x] A thermostat keeping a room at 20 °C
- A chess engine running a game-tree search
- A route planner computing the shortest path
- A scheduler comparing thousands of delivery timetables
shuffle:: true

#### Question: Choice
id:: 29d3c2ed-b03b-4ee3-bc72-120b05afc423
content:: Which observation best suggests that a robot vacuum is pursuing a goal, rather than repeating a fixed routine?
options::
- [x] When a chair blocks it, it finds another way to the same spot
- It follows the same path around the room every day
- Its behavior comes from a learned neural network
- Its manufacturer markets it as an AI agent
shuffle:: true

#### Question: Choice
id:: 29f08334-01b8-44aa-af2e-7450bcfbc0f5
content:: An AI system is trained with a reward signal for winning games. Which statement about its goals is accurate?
options::
- [x] What it ends up pursuing may differ from the reward
- Its goal is, by definition, to maximize the reward
- Its goal is whatever its designers intended
- It has no goals; its designers have the goals
shuffle:: true

#### Question: Choice
id:: 54affce9-3e45-4e33-89c4-ca06ade714a5
content:: Classical decision theory models an agent as separate from its environment. What does the "embedded agency" research agenda point out about real AI systems?
options::
- [x] They are part of the world, so their actions can change themselves
- Their goals are set by the people who deploy them
- They need human approval before each action
- They act in simulated rather than physical worlds
shuffle:: true

#### Question: Choice
id:: 0f22b70a-3298-4bb0-b43d-14fbe4e8523b
content:: Daniel Dennett's intentional stance predicts a system's behavior by treating it as having beliefs and desires. Does taking this stance toward a system require believing it is conscious?
options::
- [x] No
- Yes

#### Question: Choice
id:: 8ad8fc29-8d0c-421e-b14e-fd817ab63302
content:: The instrumental convergence argument says goal-pursuing systems would tend to seek resources and their own survival. Which kind of system does it apply to most directly?
options::
- [x] A system flexibly pursuing long-term outcomes in many situations
- A system called an agent because it calls tools in a loop
- A system answering each prompt with no lasting objective
- A system trained on a large amount of human text
shuffle:: true

#### Question: Open
id:: 7dec74fa-f4bd-4c37-b021-20bdd0b84e1c
content:: Name two different senses in which people call an AI system an "agent", and say what each one claims about the system.
assessment-instructions:: Score out of 100. 100 for any two of these, each with what it claims: intentional stance (useful to predict it as having beliefs and goals); decision-theoretic (choices fit consistent preferences and beliefs); reinforcement learning (the part that picks actions and learns from reward); planner (searches over plans); LLM-based AI agent (model in a loop with tools). 50 for two names without claims, or one described well.

#### Question: Open
id:: 8086966f-0748-4705-a212-d197dd834d4f
content:: An AI risk argument is shown to hold for idealized expected-utility maximizers. What would you need to check before applying it to a current LLM-based AI agent?
assessment-instructions:: Score out of 100. 100 for saying you must check whether the system actually pursues stable, coherent goals across situations, since the "agent" label for LLM agents describes tools and a loop, not its goals. 50 for saying the systems differ without naming goal-directedness as what to check.

#### Question: Open
id:: 88a327ba-7f2c-44ed-abac-bfe8f927d446
content:: Why is it useful to describe a chess engine as "trying to win", even though it has no wishes in a human sense?
assessment-instructions:: Score out of 100. 100 for saying the description predicts its behavior well: knowing its goal lets you predict it will make strong moves, even ones you can't foresee in detail. 50 for "it is programmed to win" without the point about prediction.

---
id: a6bc9a9c-e025-451b-9647-a332c83abd3a
title: "Goal-Directedness"
tldr: "How dangerous a wrong goal is depends on how purposefully a system chases it. A model that mechanically follows rules is far safer than one that actively searches for new ways to reach a misunderstood objective. This section maps the routes goal-directed behavior arises through: memorized heuristics, character-simulating impersonation, genuine internal search (mesa-optimization), and system-level emergence, and why each carries a different risk profile."
summary_for_tutor: "Examines goal-directedness in the Goal Misgeneralization chapter of the AI Safety Atlas. Defines goal-directedness functionally (behavior, not internal structure) and distinguishes three computational pathways to systematic objective pursuit: heuristic/memorization-based, search-based (mesa-optimization/learned optimization), and emergent system-level coordination. Covers the simulator framing of LLMs (simulators vs simulacra), persona instantiation, and the Waluigi Effect, then treats learned optimization in depth: mesa-optimization, base vs mesa objectives, the inner alignment problem, and which ML paradigms (supervised learning, CNNs, LLMs, reinforcement learning, reasoning models) face the strongest pressure toward internal search. Closes with emergent optimization from multi-component interaction."
reading_minutes: 21
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Goal-Directedness|Goal-Directedness]]

#### Text
optional:: true
content::
Three routes to purposeful behaviour: memorised heuristics, genuine internal search, and system-level emergence. Which did you come away finding most plausible for today's models, and which least? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
How dangerous a wrong goal is depends on how purposefully the system pursues it, so the section defines goal-directedness functionally, by behaviour rather than internal structure, and distinguishes three computational routes to it. Heuristic or memorisation-based, where systematic behaviour comes from learned rules of thumb with no search. Search-based, where the system runs an optimisation of its own, which is mesa-optimization or learned optimization, giving a base objective that training selected for and a mesa objective the system actually pursues, and the gap between them is the inner alignment problem. And emergent, where optimisation appears from the interaction of components none of which optimises alone. It covers the simulator framing of language models, separating the simulator from the simulacra it runs, persona instantiation, and the Waluigi Effect. It then asks which paradigms face the strongest pressure toward internal search, across supervised learning, convolutional networks, language models, reinforcement learning and reasoning models.

topics to explore:
- The definition is functional, about behaviour rather than internals. Does that make goal-directedness easier to measure, or easier to over-attribute?
- Heuristics, search, and emergence would be dangerous in different ways. Which would be hardest to detect?
- The simulator framing says the model is not the character it plays. Does that make persona-level misalignment less worrying, or differently worrying?
- Reinforcement learning and reasoning models are singled out as facing the strongest pressure toward internal search. What is it about them?
- Inner alignment is the gap between what training selected for and what the system pursues. Is that the same gap as the previous chapter's specification problem, or a different one?

Scheming comes next and builds on this, so point at it rather than pre-empting it.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

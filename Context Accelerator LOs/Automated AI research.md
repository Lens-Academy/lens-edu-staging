---
id: 96484954-526b-4a10-bcf5-388e9e448d9c
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the argument that AI doing AI research could speed up AI progress in a feedback loop, the main reasons it might stall, and what AI companies report about automating their own research as of November 2026.

## Requires
- [[AI agents]]
- [[Takeoff and intelligence explosion]]

## Helpful first
- [[Task-length trends]]
- [[AI coding]]

## Why it matters
Many forecasts of when powerful AI arrives, and how fast it improves afterwards, depend on when AI can do most of the work of AI research. Knowing the argument and the current evidence lets you judge such forecasts and company claims, rather than accepting or dismissing them wholesale.

## Lenses

## Tests

#### Question: Choice
id:: f755bff3-a9b1-44ab-b9f1-9ccf32117789
content:: What is the core argument for why automating AI research could make AI progress speed up, rather than continue at a steady pace?
options::
- [x] Better AI speeds up AI research, which produces better AI sooner, in a loop
- Automated researchers work around the clock, giving a large one-off boost to output
- AI research is cheaper to automate than other jobs, so it attracts more investment
- Once AI writes its own code, hardware stops limiting how capable models get
shuffle:: true

#### Question: Choice
id:: ed4431b3-460c-4b2b-83a1-9754b10973ef
content:: Why do many forecasters expect AI research to be one of the first kinds of research that AI can automate?
options::
- [x] It is mainly computer work with coding at its core
- It needs less creativity than most other sciences
- AI models are trained mostly on AI research papers
- It has fewer regulations than lab-based sciences
shuffle:: true

#### Question: Choice
id:: d1ad7d00-c7e5-469e-9f9b-0d9e025a66d1
content:: An AI company gains thousands of automated AI researchers but no extra computing power. According to the "compute bottleneck" objection, what limits how much faster its research gets?
options::
- [x] Experiments need compute, so more researchers mostly compete for the same chips
- The automated researchers cannot learn from each other's experiments
- The company runs out of training data before the researchers can use it
- Human managers cannot review the volume of work the researchers produce
shuffle:: true

#### Question: Choice
id:: dafc48f3-30ca-4d3e-bb69-e76b2d301b91
content:: In a "software intelligence explosion", where would most of the rapid improvement in AI come from?
options::
- [x] AI finding better algorithms and training methods on roughly the same hardware
- AI designing faster chips that are then manufactured at scale
- Rapid growth in the number of data centers built for AI
- Collecting much larger amounts of human-written training data
shuffle:: true

#### Question: Choice
id:: 6c60105c-c424-4d4c-9121-609d2be21a63
content:: Suppose AI agents make the coding in AI research ten times faster, but planning experiments, waiting for them to run and judging the results take as long as before. What mostly limits the overall speedup of research?
options::
- [x] The parts of the work that did not speed up
- The size of the speedup in coding
- The number of agents running at once
- The size of the codebase being edited
shuffle:: true

#### Question: Choice
id:: c03b7d0a-7583-48ce-ab2b-7f2a9f63a1da
content:: In June 2026, Anthropic reported what share of the code merged into its production codebase had been written by Claude as of May 2026?
options::
- [x] More than 80%
- About 50%
- About 25%
- Less than 10%
shuffle:: true

#### Question: Choice
id:: 1bea05dd-06f1-4754-bd08-01959d6a6610
content:: In September 2026, OpenAI said it had built an "automated research intern". Which description fits what OpenAI said this system does?
options::
- [x] Carries out well-defined research tasks while humans set priorities and judge results
- Runs OpenAI's research agenda on its own, with humans checking only finished models
- Answers researchers' questions in chat but cannot run code or experiments
- Writes research papers summarising work done by human researchers
shuffle:: true

#### Question: Choice
id:: fb81a27a-ff9f-4b1c-92db-f893c8f4a61c
content:: OpenAI reported that by mid-August 2026 its researchers were running 3.1 agent-workdays for every human workday. What does this figure measure?
options::
- [x] How much total time AI agents spent working, not how much they achieved
- How much faster OpenAI's research progress became because of agents
- How many human researchers' jobs the agents replaced
- How many tasks agents finished without any human help
shuffle:: true

#### Question: Choice
id:: 7d0e4c48-9aef-4149-b037-d8e2e671a88f
content:: METR's RE-Bench compared AI agents and human experts on AI research engineering tasks with fixed time budgets. What pattern did its 2024 results show?
options::
- [x] Agents scored higher with short budgets; humans did better with longer ones
- Humans scored higher with short budgets; agents did better with longer ones
- Agents and humans scored about the same at each budget tested
- Agents beat humans, and the gap grew as budgets got longer
shuffle:: true

#### Question: Choice
id:: d5e1bf22-445d-4685-a416-aa8997755cf0
content:: A 2025 METR study measured how fast experienced open-source developers worked on their own projects with and without AI tools. What did it find?
options::
- [x] They were slower with the tools, though they believed they were faster
- They were much faster with the tools, and estimated the gain correctly
- They were faster with the tools, though they believed they were slower
- Their speed did not change, and they correctly saw no difference
shuffle:: true

#### Question: Choice
id:: fdcd37c5-4cfb-4d80-83d5-c2dd0da15921
content:: Why do many AI safety researchers see automated AI research as a key point for risk, and not only for the speed of progress?
options::
- [x] It could shrink the time humans have to notice and fix problems in new systems
- It is the first point at which AI systems can write working code
- It requires models to be given open access to the internet
- It makes model weights easier for outsiders to steal
shuffle:: true

#### Question: FillBlank
id:: 7de1187f-b4dd-4f56-9b1c-4c8f8fe56952
content:: The skill of choosing which research ideas and experiments are worth pursuing is often called research {{taste}}, and many expect it to be harder to automate than coding.

#### Question: Open
id:: f815aebe-c157-43be-a2af-fabf301c2ef2
content:: Explain the feedback-loop argument for why automated AI research could lead to very fast AI progress, and give one reason the loop might slow down instead.
assessment-instructions:: Score out of 100. 50 for the loop: AI that does AI research produces better AI, which does research faster, so progress compounds. 50 for any one brake: limited compute for experiments, ideas getting harder to find, parts of research not automated (such as research taste), human oversight, or companies choosing to slow down.

#### Question: Open
id:: 60967379-091f-430a-b6d6-15a9e4359b31
content:: A news story says an AI company's models now write most of its code. Name two things you would want to know before concluding that its AI research is mostly automated.
assessment-instructions:: Score out of 100. 50 each for any two of: whether AI chooses research directions or experiments; how often humans must step in or fix work; whether overall research progress actually sped up; whether compute rather than labour is the bottleneck; how the share is measured; how much human review the code gets.

#### Question: Open
id:: 771f0175-8c18-4f49-9fc0-1b8ab3925a05
content:: Why do many forecasts of when very capable AI arrives depend on when AI can do most of the work of AI research?
assessment-instructions:: Score out of 100. 100 for explaining that once AI can do AI research, progress could speed up sharply, so the time from that point to much more capable AI could be short, making it a pivotal milestone. 40 for saying it matters for progress without explaining the speedup.

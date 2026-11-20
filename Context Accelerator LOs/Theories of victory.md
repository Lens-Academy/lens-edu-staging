---
id: 52bb66a8-853b-4208-b0b4-a0c1c6fe1d31
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main stories of how humanity could get safely through the transition to advanced AI, tell delaying dangerous AI apart from making AI safe, and say what each published plan needs to go right.

## Requires
- [[AI race dynamics]]

## Helpful first
- [[Risk argument structure]]
- [[AI governance]]

## Why it matters
Many actions sound helpful but only reduce risk if they fit a story that ends safely. With such a story in mind (sometimes called a theory of victory), you can ask what a project needs in order to matter, spot plans with missing steps, and see where your own work could make a difference.

## Lenses
- [Key paths, plans and strategies to AI safety success (BlueDot Impact)](https://blog.bluedot.org/p/ai-safety-paths-plans-and-strategies): a short map of the main stories for AI safety success, from international pauses and deterrence to careful actors racing ahead and societal resilience, with what each needs to go right (June 2025).
- [[../articles/katzke-ai-governance-needs-a-theory-of-victory|AI governance needs a theory of victory]]: what a theory of victory is (an endgame plus a strategy to reach it), tests for a good one, and three candidates: a moratorium, an "AI Leviathan" and defensive acceleration; the nuclear case study can be skipped (June 2024).
- [[../Lenses/Two Camps, Two Theories of Victory|Two Camps, Two Theories of Victory]]: one author's opinionated map of the two main camps, "win the race and automate alignment" versus "ban superintelligence by treaty", with the assumptions each needs to hold and a quick tour of other theories (May 2026).
- [[../Lenses/greenblatt-plans-a-b-c-and-d-for-misalignment-risk|Plans A, B, C, and D for misalignment risk]]: Redwood Research's Ryan Greenblatt on the best plan for each level of political will, from a long international slowdown (Plan A) to a small safety team inside a reckless company (Plan D) (October 2025).
- [[../Lenses/AI Safety Atlas - Strategies - ASI Safety Strategies|ASI Safety Strategies]]: read the sections "Automate Alignment Research" (OpenAI's 2023 Superalignment plan and what it depends on) and "Deterrence" (Mutual Assured AI Malfunction and its weak points) (2026).

## Tests

#### Question: Choice
id:: e07c7007-a725-4c1a-aa46-f7479860b2d2
content:: What makes something a theory of victory for AI risk, rather than a list of useful projects?
options::
- [x] It traces a path from today to a stable, safe outcome
- It ranks interventions by how much risk each one removes
- It rests on a careful estimate of how likely catastrophe is
- It focuses on the single most likely way AI could fail
- It is endorsed by a major AI company or government
- It gives a probability that AI causes human extinction
shuffle:: true

#### Question: FillBlank
id:: 18834171-2d4c-4486-a028-67ebd170862c
content:: An end-to-end story of how humanity gets from the present to a safe, stable outcome with advanced AI is called a {{theory of victory}}.

#### Question: Choice
id:: a880c023-0027-4ef5-a5ed-e8152cb79aae
content:: A proposed plan says: one careful lab builds an aligned superhuman AI, and the story ends there. Critics say an important step is missing. What is it most likely to be?
options::
- [x] Stopping other developers from later building unsafe AI
- Showing the lab's AI is more capable than its rivals' AI
- Winning public trust in the lab's safety claims
- Publishing the lab's model weights so others can check them
shuffle:: true

#### Question: Open
id:: cb96a186-c309-4868-9e09-f37d01e0ff6d
content:: Many AI safety plans combine delaying dangerous AI with making AI safe. Why does each strategy usually fall short on its own?
assessment-instructions:: Score out of 100. 100 for both points: delay alone only postpones the danger unless the time is used to make AI safe (and long delays are hard to sustain); making AI safe alone may not be finished, or adopted by every developer, before dangerous AI is built. 50 for one point.

#### Question: Choice
id:: b054062a-5718-4c42-a799-6e7364c72f3a
content:: Which of these is most central to a strategy of delaying dangerous AI?
options::
- [x] Ways to check that countries keep to agreed limits
- Methods to detect when a model is being deceptive
- Training methods that make models follow human intentions
- Monitoring that catches a misaligned model's sabotage
shuffle:: true

#### Question: Choice
id:: 7f181b54-3bd2-4a88-8f82-8332765d0462
content:: Redwood Research has described plans A, B, C and D for handling misalignment risk, each for a different situation. Moving from Plan A to Plan D, what mainly changes?
options::
- [x] How much political will and time is available for safety work
- How hard the alignment problem is assumed to be
- How capable AI systems are assumed to become
- Which country is assumed to build advanced AI first
shuffle:: true

#### Question: Choice
id:: 9b0e5afc-4213-4c31-8bb1-ebbae21a240d
content:: Many AI safety plans call for strong information security at AI companies, to stop model weights being stolen. In a theory of victory where careful developers use their lead to make AI safe, what does this mainly contribute?
options::
- [x] It stops rivals skipping ahead by copying the careful developers' models
- It makes models less likely to pursue goals their developers didn't intend
- It lets outside researchers check models for dangerous capabilities
- It shows the public that AI companies take safety seriously
shuffle:: true

#### Question: Choice
id:: 5ebb3700-31bf-4ec1-9672-42902bc4fc9b
content:: OpenAI's 2023 superalignment plan (its team was disbanded in 2024) aimed to have AI systems do much of the alignment research for more powerful AI. Plans like this are still common. What do they most depend on?
options::
- [x] Being able to trust or control AIs that are good at research
- Keeping the alignment methods secret from rival companies
- Human researchers checking every AI result by hand
- Governments agreeing on a global limit on training compute
shuffle:: true

#### Question: Choice
id:: c1cd868a-e84d-4522-ac11-a87a8e296af0
content:: The 2025 paper "Superintelligence Strategy" proposes MAIM: states are deterred from racing to AI dominance because rivals would sabotage any project that tries. For this deterrence to work, which of these must hold?
options::
- [x] States can watch rivals' AI projects closely enough to spot a bid for dominance
- Alignment is solved before any state gets close to superintelligence
- All frontier AI development moves into one international lab
- AI companies share their alignment research openly with each other
shuffle:: true

#### Question: Open
id:: 47724e2b-4dc7-4749-aa51-4a195cc12d89
content:: Some AI company leaders argue that safety-focused labs should stay at the frontier, so that careful developers reach powerful AI first. Name two things that must go right for this story to end safely.
assessment-instructions:: Score out of 100. 100 for any two of: the careful lab keeps a real lead; it spends that lead on safety rather than speed; its safety methods work in time; it (or governments) can stop others deploying unsafe AI; its presence doesn't speed up the race enough to cancel the benefit. 50 for one.

#### Question: Open
id:: 746c76e1-d77a-4b25-98d7-44fbccb8a367
content:: A researcher develops a technique that makes models safer but costs extra compute, and no developer is required to use it. Under a "make AI safe" theory of victory, what else must happen for this work to reduce risk?
assessment-instructions:: Score out of 100. 100 for saying the developers building the most capable systems must actually adopt it, for example through regulation, standards, norms or by making it cheaper (a lower alignment tax). 50 for a vaguer answer about "getting it used" without saying by whom or how.

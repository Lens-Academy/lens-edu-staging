---
id: cae99665-a56b-482a-989c-f9e60ce29fb9
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe what AI systems can and can't yet do in software engineering, explain why coding ability has improved quickly, and explain how strong AI coding could speed up AI research itself.

## Requires
- [[Current AI capabilities]]

## Helpful first

## Why it matters
Much of AI research is coding work, and labs already use AI for much of it: in November 2026, METR estimated Anthropic's research was moving about twice as fast as in 2024–25, mostly due to AI. Faster progress leaves safety research and policy less time to catch up. Knowing the limits helps you judge such claims.

## Lenses
- [How coding agents work (Simon Willison)](https://simonwillison.net/guides/agentic-engineering-patterns/how-coding-agents-work/): a plain explanation of a coding agent as a language model with tools (running commands, reading results, editing files) in a loop (March 2026).
- [What skills does SWE-bench Verified evaluate? (Epoch AI)](https://epoch.ai/blog/what-skills-does-swe-bench-verified-evaluate): what a SWE-bench task is (fixing a real issue in an open-source repository, checked by tests) and why its mostly short, self-contained tasks differ from real software work (June 2025).
- [We are changing our developer productivity experiment design (METR)](https://metr.org/blog/2026-02-24-uplift-update/): METR's 2025 finding that AI tools slowed experienced developers by 19%, what its late-2025 follow-up found, and why such studies are hard to run now that developers don't want to work without AI (February 2026).
- [[../Lenses/AIF - Massive Easy-to-Verify SWE Tasks|Massive Easy-to-Verify SWE Tasks]]: Ryan Greenblatt on why AIs can now do months-long software tasks when success is cheap to check with tests, where poor taste and judgment still hold them back, and how much this speeds up AI research; skip the appendix on timelines (April 2026).
- [Could advanced AI accelerate the pace of AI progress? (Forethought)](https://www.forethought.org/research/could-advanced-ai-accelerate-the-pace-of-ai-progress-interviews-with-ai): five AI company researchers on which parts of research AI could take over, and why compute for experiments, choosing experiments and coordination limit the speedup; read the summary and the table of estimates (March 2025).

## Tests

#### Question: Choice
id:: c0162602-8ea6-43ce-8fe9-c826b2e7c952
content:: Why is coding easier to improve with reinforcement learning than a task like essay writing?
options::
- [x] Automated tests can check whether the code works
- Code is usually shorter than a typical essay
- Programming languages have smaller vocabularies than English
- Models need less pretraining data to learn code
shuffle:: true

#### Question: Choice
id:: 51fdc9b9-cc92-4607-807f-7c522fb9cb30
content:: What does a task in the SWE-bench coding benchmark ask an AI system to do?
options::
- [x] Resolve a real issue in an open-source code repository
- Write one short function from a description of its behaviour
- Solve timed problems from competitive programming contests
- Answer multiple-choice questions about programming concepts
shuffle:: true

#### Question: Choice
id:: 35da0e7b-9d0a-4ee2-848a-b408ecf5e840
content:: What mainly distinguishes an AI coding agent from earlier code-completion tools?
options::
- [x] It can run commands, read the results and edit files in a loop
- It suggests the next line of code as the developer types
- It is trained on code instead of on natural language
- It supports a wider range of programming languages
shuffle:: true

#### Question: Choice
id:: 4fe526f4-e4ad-43bd-a340-582c8d544f07
content:: In a 2025 METR study, experienced open-source developers worked on tasks in their own projects, some with AI tools available (early-2025 tools) and some without. What did the study find?
options::
- [x] With AI they took longer on average, though they believed AI had sped them up
- With AI they finished about twice as fast, matching their own estimates
- With AI their speed was unchanged, but their code had many more bugs
- With AI they were faster on easy tasks and much slower on hard ones
shuffle:: true

#### Question: Choice
id:: 1f91cf4b-b574-465e-80f2-5d0329d062c2
content:: Which of these is a reason that coding benchmark scores can overstate how useful AI is for real software work?
options::
- [x] Benchmark tasks tend to be self-contained and come with clear tests
- Benchmark tasks tend to be harder than typical professional work
- Benchmarks tend to use older programming languages than industry does
- Benchmarks tend to stop models from running the code they write
shuffle:: true

#### Question: Choice
id:: a2558037-cc73-4edb-b39a-95770e15166f
content:: Suppose AI systems could do all the coding work at an AI company, but the number of experiments the company can run is limited by its computing power. What does this suggest about the company's research speed?
options::
- [x] It would rise less than the gain in coding speed alone suggests
- It would rise in proportion to the gain in coding speed
- It would rise more than the gain in coding speed, since researchers would be freed from coding
- It would fall, since agents would use up compute meant for training
shuffle:: true

#### Question: Open
id:: 3c873790-b0bb-4eab-a408-fa1af489504a
content:: Why could AI systems that write code well speed up progress in AI research itself?
assessment-instructions:: Score out of 100. 100 for saying that much of AI research work is coding or engineering (writing experiment code, building infrastructure, debugging), so AI that does it lets labs make progress faster. Mentioning the feedback loop (faster research yields better coding AI) is good but not required. 40 for only saying AI is good at coding, without linking it to research work.

#### Question: Open
id:: 98db2718-4682-432c-8be7-f14ed810e806
content:: Name one part of AI research work, other than writing code, that could limit how much automating coding speeds up AI research.
assessment-instructions:: Score out of 100. 100 for any one of: choosing which research directions or experiments to pursue (research taste), coming up with new ideas, designing experiments, running experiments (limited by compute), interpreting results, or coordinating long projects. 50 for a vague answer such as "thinking" or "creativity" without linking it to research. 0 for a coding activity such as debugging.

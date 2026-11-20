---
id: 1b6ebe25-b8b2-435b-a443-5f358a4ce669
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the main arguments that AGI is still decades away, and the replies that people expecting shorter timelines give to each.

## Requires
- [[Timeline forecasts]]

## Helpful first
- [[Jagged capabilities]]

## Why it matters
Forecasts of when AGI arrives range from within a few years, common among forecasters close to AI labs, to a decade or more, as in surveys of AI researchers. Understanding the case for long timelines lets you weigh it fairly against the case for short ones, plan for more than one future, and tell a well-grounded objection from wishful dismissal.

## Lenses
- [3 reasons AGI might still be decades away (80,000 Hours)](https://80000hours.org/2025/06/3-reasons-agi-might-still-be-decades-away/): a short overview of the main reasons: no clear route from today's systems, bottlenecks in compute, chips, data and money around 2030, and a world not acting as if AGI is near. It also explains why the risk is still worth working on if AGI is decades off (June 2025).
- [Why I don't think AGI is right around the corner (Dwarkesh Patel)](https://www.dwarkesh.com/p/timelines-june-2025): the case that models can't learn on the job the way a new employee does (continual learning), and why compute growth hitting limits around 2030 makes AGI more likely this decade than in any single later year (June 2025).
- [[../Lenses/AIF - The Case for Multi-Decade AI Timelines|The Case for Multi-Decade AI Timelines]]: Epoch's Ege Erdil argues for about 20 years to full automation of remote work. He extrapolates AI revenue rather than impressiveness, argues that compute for experiments would bottleneck AI automating its own research, and uses Moravec's paradox to argue that agentic tasks will stay slow and expensive (April 2025).
- [Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity (METR)](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/): a randomised trial in which developers were 19% slower with AI tools while believing they were faster, and why scores on neat, auto-graded benchmarks may overstate real-world ability. It is a snapshot of early-2025 tools; METR's 2026 follow-up suggests developers are now likely sped up (July 2025).
- [What the Hell Happened with AGI Timelines in 2026? (80,000 Hours Podcast)](https://80000hours.org/podcast/episodes/2026-agi-timelines/): Rob Wiblin on how the evidence moved in 2026 and which long-timelines arguments still stand. Listen to or read the chapters "Exhibit 5: AI still struggles to run a business" (23:02–33:48) and "Four reasons long timelines are still possible" (44:25–48:00) (August 2026).

## Tests
#### Question: Choice
id:: 3ccd7af1-9cd6-4990-a946-14db1def5acb
content:: An AI model's weights stay fixed after training, so it can't build up skill and context at a particular job over months the way a new employee does. Why do long-timelines arguments say this matters?
options::
- [x] Much real work relies on learning on the job, which tests don't measure
- Models with fixed weights gradually forget what they learned in training
- Models with fixed weights can't follow new instructions in a conversation
- Fixed weights stop companies from releasing improved versions
shuffle:: true

#### Question: Choice
id:: efdeff67-c7c2-4e47-a466-213f134a1565
content:: One argument for long timelines is that AI developers could use up the stock of high-quality public human-written text sometime between 2026 and 2032. Which reply do people expecting shorter timelines most often give?
options::
- [x] Models can learn from synthetic data and from reinforcement learning on checkable tasks
- Models can be given longer context windows instead of more training data
- Faster chips let models learn much more from the same amount of text
- Larger models need less training data than smaller ones to reach the same skill
shuffle:: true

#### Question: Choice
id:: 51e92eee-7542-4d7f-9080-3476de9591fe
content:: Frontier AI training compute has grown several times over each year, but some argue cost, power supply and chip production will force this growth to slow around 2030. If AGI depends mainly on scaling compute, what does this imply?
options::
- [x] The yearly chance of AGI is higher before about 2030 than after
- AGI is about as likely in the 2040s as in the late 2020s
- AGI is most likely to arrive in the few years just after 2030
- AGI can't arrive until compute growth speeds up again
shuffle:: true

#### Question: Choice
id:: 24832362-c638-48e9-9b9b-65aa2716cce5
content:: In November 2026, METR estimated that Anthropic's research was moving about twice as fast as in 2024-25, mostly because of its own use of AI. Short-timelines arguments expect this kind of speed-up to snowball. What is a common long-timelines reply?
options::
- [x] Research also needs compute for experiments, which would become the bottleneck
- Faster research makes models cheaper to run but not more capable
- Companies won't trust AI systems to make research decisions
- Human researchers checking the AI's work would cancel out its speed
shuffle:: true

#### Question: Choice
id:: d0cf15b1-78b4-45c5-929f-c03747cfa819
content:: Arguments that AI will spread through the economy slowly, as electricity did, mainly push back on predictions about which of these?
options::
- [x] How soon AI will transform the economy and daily life
- How soon AI systems will match humans on most tests
- How soon AI labs will automate their own research
- How soon the most advanced AI systems gain dangerous capabilities
shuffle:: true

#### Question: Choice
id:: 4de04a82-9423-45c9-bcf4-c105a01ffc8b
content:: In an early-2025 trial by the research group METR, experienced developers were slower with AI coding tools, though they believed they were faster. A late-2025 follow-up pointed to a speedup, though METR called that evidence weak. What lesson from the first study still holds?
options::
- [x] People's own sense of how much AI speeds them up is unreliable evidence
- AI coding tools don't help experienced developers
- AI coding tools help beginners but not experts
- Randomised trials can't measure developer productivity
shuffle:: true

#### Question: Choice
id:: 4ffa4d0a-a8d4-4981-95a6-8cacc91235ad
content:: Why do long-timelines arguments say high AI benchmark scores overstate progress toward AGI?
options::
- [x] Benchmark tasks are clearly specified and easy to check, unlike much real work
- Benchmarks are graded by AI models, which mark generously
- Benchmark scores have stopped rising since 2024
- Benchmark questions are made easier each year to keep scores high
shuffle:: true

#### Question: Choice
id:: 56ce8e4e-e01f-45e8-9d43-457f96ece2bc
content:: Someone thinks AGI is probably decades away, but still thinks work on AI existential risk is worth doing now. Which reason best supports their view?
options::
- [x] Safety research and governance take years to build, and short timelines remain possible
- Today's AI systems already pose an existential risk on their own
- AI that arrives later will certainly be harder to control
- Work on AI risk can only be funded while AI is in the news
shuffle:: true

#### Question: Choice
id:: 9ec6c82f-e5c4-48de-bb28-2700b15d8744
content:: Do arguments for long timelines usually rest on the claim that machines can't, in principle, match human intelligence?
options::
- Yes
- [x] No

#### Question: Choice
id:: 3d79766b-190a-4333-a5cb-b20dbb28099e
content:: AI has advanced much faster at coding and maths than at physical tasks like plumbing, and long-timelines arguments point to this. What reply do people expecting shorter timelines often give?
options::
- [x] AI research needs no robots, and AI researchers could then speed up robotics
- Robots can already do most physical jobs about as well as people
- Robots will learn physical skills from reading more text online
- Robotics has historically improved faster than software has
shuffle:: true

#### Question: Open
id:: 7635e4e9-dac3-4bc5-943c-2771c71a367e
content:: Give two different arguments that AGI is decades away rather than a few years.
assessment-instructions:: Score out of 100. 50 for each distinct argument, from: missing capabilities such as continual learning or reliability on long tasks; running out of high-quality training data; compute growth slowing because of cost, power or chips; slow adoption across the economy; robotics lagging behind; benchmarks overstating real-world ability; past AI predictions being too optimistic. 25 for a vague one.

#### Question: Open
id:: 1055c1f0-cd99-4b05-a4f8-643b20a2e528
content:: Choose one argument for long timelines and give a reply that people expecting shorter timelines make to it.
assessment-instructions:: Score out of 100. 100 for an argument with a reply that addresses it, for example: data limits → synthetic data or reinforcement learning; compute limits → algorithmic efficiency gains or AI already speeding up research; missing capabilities → past gaps such as reasoning closed quickly; slow adoption → risk depends on capabilities, not wide adoption; robotics lag → AI research needs no robots. 50 if the reply is vague or misses the argument.

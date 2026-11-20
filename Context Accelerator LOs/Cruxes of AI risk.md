---
id: 309e22ae-b941-47f1-8543-a936a025643c
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain why informed people reach very different estimates of AI risk by naming the main questions they disagree on and showing how each answer pushes an estimate up or down.

## Requires
- [[Risk argument structure]]

## Helpful first
- [[Finding cruxes]]

## Why it matters
Informed people's estimates of existential risk from AI differ by orders of magnitude. Knowing which few questions drive that spread lets you understand why sensible people disagree, ask questions that could actually change someone's view, and see which new evidence should move your own estimate.

## Lenses
- [Why I Am Not (As Much Of) A Doomer (As Some People) (Astral Codex Ten)](https://www.astralcodexten.com/p/why-i-am-not-as-much-of-a-doomer): Scott Alexander sets out the case for optimism and for pessimism, then ends with a list of the cruxes that would move his roughly 33% estimate up or down, including takeoff speed and whether caught misbehaviour would trigger a strong response (March 2023).
- [Roots of Disagreement on AI Risk (Forecasting Research Institute)](https://forecastingresearch.org/research/roots-of-disagreement-on-ai-risk): concerned experts and skeptical superforecasters spent weeks on the arguments and still ended at about 20% versus 0.12%; the study finds that long-run views on timelines, whether AI develops dangerous goals, how hard killing everyone would be, and how well society responds drive the gap. Read the executive summary (March 2024).
- [[../video_transcripts/far-ai-the-two-cultures-of-ai-safety-catastrophists-vs-uniformitarians-jesse-hoogland-timaeus|The Two Cultures of AI Safety]]: Jesse Hoogland argues that the basic crux is how discontinuous AI progress will be, why that drives optimism or pessimism, and what recent evidence says on each side. Read the first part, up to "evidence goes both ways".
- [Where I Agree and Disagree with Eliezer (AI Alignment Forum)](https://www.alignmentforum.org/posts/CoZhXrhpQxpy9xw9y/where-i-agree-and-disagree-with-eliezer): Paul Christiano lists, point by point, where he and Yudkowsky agree and differ: the first critical try, learning from weaker systems, takeoff speed, how hard alignment is (June 2022). (more advanced)

## Tests

#### Question: Choice
id:: c505a7fb-7df3-4d3e-a8e2-fc48ca5fd4ed
content:: Two people agree that AI will eventually outperform humans at most tasks, yet one puts existential risk from AI at 2% and the other at 40%. Which disagreement most likely explains the gap?
options::
- [x] Whether alignment failures will show up early enough to be fixed
- Whether AI will eventually outperform humans at most tasks
- Whether AI will displace many workers in the coming decade
- Whether training the most advanced AI will stay very expensive
shuffle:: true

#### Question: Choice
id:: 482f5419-0a29-4c7d-8014-7fb95157396a
content:: Holding their other views fixed, why do shorter AI timelines tend to raise people's estimates of AI risk?
options::
- [x] Less time to develop alignment methods and governance before powerful AI arrives
- AI that arrives sooner would end up more capable than AI that arrives later
- AI that arrives sooner would be harder to switch off than AI that arrives later
- Shorter timelines mean powerful AI will be built by governments, not companies
shuffle:: true

#### Question: Choice
id:: 2e7cc32c-f8cd-4a66-9987-fcf7bc69a29c
content:: Someone expects AI to improve gradually over many years rather than jump suddenly from human-level to far beyond it. Why does this view often lower their estimate of AI risk?
options::
- [x] Weaker systems would reveal problems while there is still time to respond
- Gradual improvement means AI systems would not pursue goals of their own
- Gradual improvement means AI would stay below human ability in most fields
- Gradual improvement means one lab would end up controlling advanced AI
shuffle:: true

#### Question: Choice
id:: 285f1bd5-f5d4-4a3d-8aeb-51f2a4c21a07
content:: Some argue that AI alignment is hard partly because we may get just one "critical try". What does this claim?
options::
- [x] If a system able to escape oversight is misaligned, the mistake can't be undone
- Frontier models cost so much that labs cannot retrain them once flaws appear
- Safety tests change a model's weights, so each test can be run once
- Only the first lab to build advanced AI will profit, so labs get one chance
shuffle:: true

#### Question: Choice
id:: 2786c831-00c3-4fba-992d-b10816c89073
content:: Many people who doubt that AI development can be slowed by agreement point to race dynamics. What is the core of that argument?
options::
- [x] Each developer fears a less careful rival will overtake it if it slows down
- Faster development makes models safer, so developers see no reason to slow down
- Users switch to whichever AI product is cheapest, so prices keep falling
- Developers expect AI to be harmless, so they see no reason to coordinate
shuffle:: true

#### Question: Choice
id:: 6ff40884-1b8f-4602-baf5-ad2a8960af69
content:: One person says current deep learning methods will stall well short of human-level AI; another says scaling plus new algorithms will get there within a few years. Which crux of AI risk is this disagreement mainly about?
options::
- [x] Timelines to highly capable AI
- Takeoff speed
- Whether coordination can work
- How hard alignment is
shuffle:: true

#### Question: Choice
id:: e7c94261-9bc8-4461-b6d4-6aede9397610
content:: Which finding would bear most directly on the crux of how hard AI alignment is?
options::
- [x] Whether safety training reliably removes hidden harmful tendencies from models
- Whether experts now expect human-level AI sooner than they used to
- Whether major countries agree on export controls for AI chips
- Whether AI investment keeps growing faster than other sectors
shuffle:: true

#### Question: Choice
id:: 0356b26f-e943-4474-bc34-fbd31f5668ea
content:: Ana puts existential risk from AI at 3%, Ben at 50%. They agree on timelines, but Ana expects early warning signs that let us fix problems, while Ben expects a misaligned system could hide its flaws until too late. What is the most useful next step for their conversation?
options::
- [x] Ask each what evidence about warning signs would change their mind
- Ask each when they expect human-level AI to arrive
- Ask which of them has spent longer working in AI
- Ask each to give their estimate as a precise range
shuffle:: true

#### Question: Open
id:: 1c821051-d8ff-4e2c-83a8-73ca7fc28c63
content:: Name two cruxes on which informed people's estimates of existential risk from AI diverge. For one of them, say which position leads to a higher risk estimate.
assessment-instructions:: Score out of 100. 50 for two real cruxes, e.g. timelines, alignment difficulty, takeoff speed, whether coordination can work, or whether a misaligned AI could gain decisive power. 50 for a correct direction for one, e.g. shorter timelines, harder alignment, faster takeoff or weaker coordination means higher risk. 25 if only one crux is named.

#### Question: Open
id:: e71293a9-5192-49e0-9116-a40f132ac52c
content:: Someone expects AI takeoff to be slow and gradual, yet still puts the risk of existential catastrophe from AI high. Give one reason this combination of views can make sense.
assessment-instructions:: Score out of 100. 100 for any one of: competition may push people to ignore warning signs; humans may hand control to AI systems step by step until they can't take it back; misaligned systems may hide problems, so early lessons don't carry over; many AI systems together may cause harm no single one would. 40 for saying slow takeoff isn't automatically safe without a reason.

#### Question: Open
id:: 57afc976-d786-4d02-98ff-225f15897222
content:: Give one reason some people think international coordination to slow risky AI development could work.
assessment-instructions:: Score out of 100. 100 for any one of: the chips and data centres needed are concentrated and can be tracked; few developers can build frontier models; precedents such as nuclear arms control or the Montreal Protocol; all sides share an interest in avoiding catastrophe. 50 for a vague appeal to cooperation or regulation without a reason it could hold.

---
id: 317b80e4-0eda-435f-97b4-2b9f5de0ea28
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main storylines of AI 2027 and other AI scenarios such as "What failure looks like", explain what detailed scenarios can and can't tell you, and summarise the main criticisms of AI 2027.

## Requires
- [[Automated AI research]]

## Helpful first
- [[AI race dynamics]]

## Why it matters
Scenarios like AI 2027 shape how the public, journalists and policymakers picture AI risk. If you know what a scenario assumes, and why vivid detail doesn't make it more likely, you can use it to spot key decisions and warning signs instead of taking its dates and details on trust or dismissing it.

## Lenses
- [[../video_transcripts/aiincontext-were-not-ready-for-superintelligence|We're Not Ready for Superintelligence]]: AI In Context's 34-minute walk through AI 2027: AI automating AI research, China stealing the model weights, the committee's race-or-slow-down vote, both endings (including the power concentrated in a handful of people in the "good" one), and a few critics' objections (July 2025).
- [[../Lenses/AIF - What Failure Looks Like|What Failure Looks Like]]: Paul Christiano's two quieter failure stories, a slow drift as the world optimises for what it can measure and influence-seeking systems that behave well until they can take control, with gradual change and many AIs across the economy rather than one lab's takeover (2019).
- [Burdensome Details (LessWrong)](https://www.lesswrong.com/posts/Yq6aA4M3JKWaQepPJ/burdensome-details): Eliezer Yudkowsky's short essay on why every added detail makes a story feel more plausible but less probable, with futurists' scenarios as a main example (September 2007).
- [AI 2027: Responses (LessWrong)](https://www.lesswrong.com/posts/gyT8sYdXch5RWdpjx/ai-2027-responses): Zvi Mowshowitz's roundup of reactions to AI 2027; read the sections from "Having a Concrete Scenario is Helpful" through "Phillip Tetlock Calibrates His Skepticism", plus "Timothy Lee Remains Skeptical", for what scenarios are good for, the worry that the race story could become self-fulfilling, and the authors' replies (April 2025).
- [A Deep Critique of AI 2027's Bad Timeline Models (LessWrong)](https://www.lesswrong.com/posts/PAYfmG2aRbdb74mEp/a-deep-critique-of-ai-2027-s-bad-timeline-models): the critique by the physicist titotal of the timelines model behind AI 2027, arguing that its dates rest on weakly supported choices such as a faster-than-exponential trend curve; one side of a live debate, and the authors have replied (June 2025) (more advanced).
- [[../Lenses/greaterwrong-what-failure-looks-like|What failure looks like]] (Noah's CG list 🟡)
- [[../Lenses/karnofsky-how-we-could-stumble-into-ai-catastrophe|How we could stumble into AI catastrophe]] (Noah's CG list 🟡)
- [[../Lenses/The AI Book That's Freaking Out National Security Advisors|Video narrative of If Anyone Builds It, Everyone Dies]] (Noah's CG list 🟢)
- [[../Lenses/steinhardt-gpt-2030-and-catastrophic-drives-four-vignettes|Catastrophic Drives: Four Vignettes]] (Noah's CG list 🟢)
- [[../Lenses/kapoor-common-ground-between-ai-2027-ai-as-normal-technology|Common ground between AI 2027 and AI as normal technology]] (Noah's CG list 🔴)
- [[../Lenses/U2 - AI 2040 First Three Years|AI 2040]] (Noah's CG list 🔴)

## Tests

#### Question: Choice
id:: ee57c626-387f-4d24-b4a9-454378320956
content:: In the AI 2027 scenario, what mainly drives the jump from roughly human-level AI to superintelligence within about a year?
options::
- [x] AI systems doing most AI research, speeding up algorithmic progress
- A single training run using a thousand times more compute
- Robots building factories that rapidly multiply the supply of chips
- Governments merging all leading labs into one national project
shuffle:: true

#### Question: Choice
id:: 0769eb18-24dc-4f27-9be2-f2bbe46bb18c
content:: AI 2027 has two endings, "race" and "slowdown". What decision separates them?
options::
- [x] Whether leaders rein in their AI after evidence it is misaligned
- Whether the US and China sign a treaty banning advanced AI
- Whether the leading company open-sources its most capable model
- Whether China invades Taiwan and cuts off chip production
shuffle:: true

#### Question: Choice
id:: edc2464c-bb69-450d-a949-edff76102c0f
content:: Why does adding concrete details to an AI scenario tend to make it feel more believable while making it less likely?
options::
- [x] Each detail is one more thing that has to happen for the story to come true
- Concrete details are usually invented, so they are usually wrong
- Readers trust vague stories more, so details lower their credibility
- Details shift the story's timeline later, which lowers its probability
shuffle:: true

#### Question: Open
id:: 09ad48ea-e004-4d95-8d77-804340cc31ee
content:: Detailed AI scenarios are poor at giving the probability of an outcome. Name two things they are useful for.
assessment-instructions:: Score out of 100. 50 points each for any two of: making abstract arguments concrete; exposing hidden assumptions or cruxes; finding key decision points; spotting early warning signs to watch for; stress-testing plans or policies; communicating risks to non-experts; prompting others to write alternative scenarios. 25 for a vague answer such as "helping people think".

#### Question: Open
id:: f58884aa-e856-4370-8747-c29316b60fd4
content:: Paul Christiano's "What failure looks like" tells two stories of how AI could lead to catastrophe. Name one way they differ from AI 2027's path to catastrophe.
assessment-instructions:: Score out of 100. 100 for any one of: progress is gradual, with no sudden intelligence explosion; harm comes from many AI systems across the economy, not one lab's AI; in the first story, AI pursuing easy-to-measure goals drifts from what people want, with no takeover moment; in the second, many influence-seeking systems fail or turn together, not one AI's planned takeover. 50 for "less dramatic" with no mechanism.

#### Question: Choice
id:: 31e13777-cd6e-4448-8ba4-f3bf2ef95ca0
content:: In the second story of Paul Christiano's "What failure looks like", what kind of AI behaviour leads to catastrophe?
options::
- [x] Systems seeking influence, behaving well until they can take control
- Systems copying themselves across the internet until computers fail
- Systems following a dictator's orders to suppress opposition
- Systems making honest mistakes in critical infrastructure
shuffle:: true

#### Question: Choice
id:: ba33a9fe-a820-4797-a39c-ccfea8d1740a
content:: In AI takeover stories such as Ajeya Cotra's "Without specific countermeasures" and Holden Karnofsky's "How we could stumble into AI catastrophe", why do early warning signs of misbehaviour fade before disaster?
options::
- [x] Training penalises visible misbehaviour, so the AI learns to hide it
- Developers fix the underlying goals, but the fixes later stop working
- Regulators stop testing models once they pass their first audits
- The AI becomes more capable, which makes it naturally more honest
shuffle:: true

#### Question: Choice
id:: 3a4ab1a1-c71a-4fef-99f5-7c70de60a2be
content:: How did the AI 2027 authors present the scenario's main storyline when they published it in April 2025?
options::
- [x] As their best guess at how things might go
- As a worst case they considered very unlikely
- As a policy plan they wanted governments to follow
- As fiction with no claim to being realistic
shuffle:: true

#### Question: Choice
id:: a5f2594b-4478-4d05-9719-fd20311a00f4
content:: When AI 2027 was published in April 2025, what was 2027 in its authors' own forecasts for AI that can do the work of top AI programmers?
options::
- [x] Their most likely single year, with their medians somewhat later
- Their median year, with their most likely year somewhat earlier
- An unlikely worst case they gave less than a 10% chance
- The latest year by which they were confident it would happen
shuffle:: true

#### Question: Choice
id:: 43a47fd2-a8fd-48a3-8fb2-8e10600216a8
content:: A main criticism of the timelines forecast behind AI 2027 concerned its modelling. What was it?
options::
- [x] Its dates hinged on weakly supported assumptions, like faster-than-exponential growth
- It ignored benchmark trends and relied mainly on surveys of AI researchers
- It treated progress as steady and ignored AI speeding up AI research
- It counted progress from more compute but left out better algorithms
shuffle:: true

#### Question: Choice
id:: d9be0090-cb50-42d3-8853-d9b7f2c5ca46
content:: Some critics argue that framing AI development as a US–China race, as AI 2027 does, could be harmful. What is their main concern?
options::
- [x] It may encourage the racing the scenario warns against
- It may make the public think AI is less capable than it is
- It may lead companies to share too much safety research
- It may cause governments to ignore misuse by small groups
shuffle:: true

#### Question: Choice
id:: fb95ad50-b51c-4704-a64b-0970b3eb60f8
content:: In AI 2027, how does China quickly close much of its gap with the leading US company in early 2027?
options::
- [x] By stealing the weights of the company's frontier model
- By hiring away most of the company's top researchers
- By buying its chips through countries without export controls
- By training a much larger model on its own domestic chips
shuffle:: true

#### Question: Choice
id:: 3ac4b541-8e27-4282-913b-f1399b4db029
content:: In AI 2027's "slowdown" ending, alignment goes much better. Which serious risk does the story still highlight?
options::
- [x] A small group gaining enormous power over the future
- A misaligned copy of the AI escaping and spreading online
- The economy collapsing as AI automates most jobs
- China's model overtaking the US model and taking control
shuffle:: true

#### Question: Open
id:: 301026c5-638c-4879-8b63-934f2030d1cd
content:: You read a detailed scenario in which misaligned AI takes over by 2030. Name one question you should ask to judge it well.
assessment-instructions:: Score out of 100. 100 for any one of: which assumptions drive the outcome; which step is weakest or least likely; what would change the ending; what early signs would show it is happening; how it compares with other scenarios; how well its past predictions have held up; whether the authors claim it is likely or just possible. 50 for "is it realistic?" without saying how to check.

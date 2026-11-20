---
id: 216eab50-8798-42f2-ad47-ba45ff251e0e
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe how militaries use AI, from targeting support to autonomous weapons, and explain how military AI could cause unintended escalation and feed a race that makes safe AI development harder.

## Requires

## Helpful first
- [[Sources of AI catastrophe]]

## Why it matters
Militaries are buyers and developers of AI, and national security arguments shape how governments treat AI labs and regulation: in 2026 the Pentagon moved to cut off Anthropic after it refused uses including fully autonomous weapons. Understanding how military AI can speed up escalation and fuel racing helps you judge proposals such as keeping humans in charge of nuclear decisions.

## Lenses
- [[../Lenses/AI Safety Atlas - Risks - Misuse Risks|Autonomous Weapons Risk]]: How AI weapons are already used in Libya, Ukraine and Gaza, why jamming and speed push toward autonomy, how human control becomes nominal under battlefield pressure, and how arms-race dynamics and interacting systems can escalate a clash; read only the "Autonomous Weapons Risk" section, including the short film Artificial Escalation.
- [Defense Primer: U.S. Policy on Lethal Autonomous Weapon Systems (Congressional Research Service)](https://www.congress.gov/crs-product/IF11150): The plain facts: what counts as an autonomous weapon, human "in", "on" and "out of" the loop, what DoD Directive 3000.09 requires (and that it doesn't ban such weapons), and the UN CCW talks in Geneva (March 2026).
- [Paul Scharre on how AI could transform the nature of war (80,000 Hours)](https://80000hours.org/podcast/episodes/paul-scharre-ai-warfare-autonomous-weapons/): A leading military-AI expert on why competition pushes humans out of the loop, "flash wars" with no timeout, AI in nuclear command and control, Petrov, deterrence and the US-China pledge on human control of nuclear decisions; listen or read from "Why would militaries take humans out of the loop?" to the end of "Nuclear stability and deterrence" (00:12:26–00:46:58) (December 2025).

## Tests

#### Question: Choice
id:: 146d5a0f-d173-4f8a-8d83-a8e3fe8c4835
content:: Two rival militaries deploy autonomous drones along a disputed border, each set to return fire instantly if attacked. Some analysts call the danger here a "flash war", by analogy with the 2010 stock-market flash crash. What is the danger?
options::
- [x] Each side's systems could react to the other's, escalating a clash before humans step in
- An enemy could hack one side's drones and turn them against their own forces
- The drones could develop goals of their own and decide to start a war
- Sensors could fail in bad weather, leaving the border undefended
shuffle:: true

#### Question: Choice
id:: 9250b907-03b8-4522-9509-fcb19668c042
content:: An air-defence system detects and fires at incoming missiles by itself, while a human operator watches and can abort an engagement. Which phrase describes the human's role?
options::
- [x] Human on the loop
- Human in the loop
- Human out of the loop
shuffle:: true

#### Question: Choice
id:: a28b51d7-6d10-451b-8489-ea329e45ced3
content:: Officers using an AI targeting-support system approve most of its recommended targets after only a few seconds of review. Which risk does this best illustrate?
options::
- [x] Automation bias, where people defer to the machine's judgment
- Adversarial attacks, where enemies fool the system's sensors
- Specification gaming, where the AI exploits a flawed objective
- Deceptive alignment, where the AI hides its real goals
shuffle:: true

#### Question: Choice
id:: 7db1c8a9-4c30-4734-9ce4-ba7afaef87ab
content:: Since the mid-2010s, in which forum have most international talks on lethal autonomous weapons taken place?
options::
- [x] The UN Convention on Certain Conventional Weapons, in Geneva
- The review conferences of the Nuclear Non-Proliferation Treaty
- The UN Security Council
- Meetings of NATO defence ministers
shuffle:: true

#### Question: Choice
id:: cbbfded3-5085-49e2-b3a0-e718f2f7b003
content:: Talks on lethal autonomous weapons under the UN Convention on Certain Conventional Weapons have run for more than a decade without producing a treaty. Which feature of the forum is most often blamed?
options::
- [x] Decisions need consensus, so any single state can block progress
- Only the five permanent Security Council members can vote
- It can only restrict weapons that have already been used in war
- Non-governmental experts are barred from its meetings
shuffle:: true

#### Question: Choice
id:: 52b6094f-1969-435c-b3f3-7609129984b5
content:: In the war in Ukraine, why has electronic jamming pushed drone makers to add onboard autonomy, such as automatic final targeting?
options::
- [x] Jamming cuts the operator's link, so the drone must finish the attack alone
- Jamming blinds the drone's cameras, so it must navigate from stored maps
- Autonomous drones are cheaper to build than remotely piloted ones
- Onboard AI lets the drone fly higher, above the jammers' range
shuffle:: true

#### Question: Choice
id:: ea49db26-bf80-4b6b-924f-4716caa4b873
content:: In 1983, Soviet officer Stanislav Petrov judged that a satellite warning of incoming US missiles was a false alarm and did not report it as an attack. What concern about AI in nuclear early warning does this case illustrate?
options::
- [x] An automated chain could act on a false alarm that a human would doubt
- AI would have detected the incoming missiles faster than the satellites did
- Human officers are more likely than computers to launch in error
- Satellites are less reliable than ground radar for early warning
shuffle:: true

#### Question: Choice
id:: f0273f41-7a3a-4d0b-9558-a1feddd9bdd1
content:: When the US and Chinese leaders met in November 2024, they agreed on a principle about AI and nuclear weapons. What did they affirm?
options::
- [x] Humans should keep control over decisions to use nuclear weapons
- AI would be kept out of all nuclear early-warning and command systems
- Each would notify the other before deploying new military AI systems
- Both would stop developing lethal autonomous weapons
shuffle:: true

#### Question: Choice
id:: 02b76a6b-79c8-43b4-a409-9c47eddb395d
content:: Some anti-radar loitering munitions, once launched, search an area and attack the first enemy radar they detect, with no further human input. Which statement about weapons like this is true?
options::
- [x] They have been in military service for decades
- They exist only as prototypes and have never been deployed
- They are banned under the Convention on Certain Conventional Weapons
- Only the US and China are known to have deployed them
shuffle:: true

#### Question: Choice
id:: e8fea697-aa32-45ef-a842-e03216e63ad3
content:: Do the escalation risks of military AI depend on the AI systems having goals different from their operators' goals?
options::
- [x] No
- Yes

#### Question: Choice
id:: 268dc929-e7ba-40cd-b092-68ccd7ea01c1
content:: As of late 2026, does the US Department of Defense's policy on autonomy in weapon systems (Directive 3000.09, last updated in 2023) ban the development of fully autonomous weapons?
options::
- [x] No
- Yes

#### Question: FillBlank
id:: 5a6f5a0a-a66a-459c-9c12-4c93cf6dc84e
content:: If AI made it easy to track a rival's nuclear-armed submarines, it could threaten that rival's {{second-strike|second strike|retaliatory}} capability, which nuclear deterrence depends on.

#### Question: Open
id:: 8938a7fd-57dd-42df-832d-66fcb9bcdb5a
content:: Give two ways that AI in military systems could make an unintended war more likely.
assessment-instructions:: Score out of 100. 50 for each of two distinct mechanisms, such as: faster decisions leave less time for human judgment; opposing automated systems interact unpredictably; false alarms or misidentified targets; operators defer to AI recommendations; force seems cheaper when no soldiers are at risk; threats to nuclear second-strike forces. Vague answers ("AI is dangerous") get at most 20.

#### Question: Open
id:: a3826ed6-dd73-4dc0-b1af-aa6610668300
content:: Why would a treaty limiting autonomous weapons be hard to verify, even if countries agreed to one?
assessment-instructions:: Score out of 100. 100 for explaining that autonomy lies mostly in software, so the same drone or missile can switch between human-controlled and autonomous modes and inspectors can't tell from the hardware. 50 for a related point only, such as no agreed definition of autonomy or military secrecy.

#### Question: Open
id:: c2c4af1d-bacc-4ba1-98ae-cf23683db2c7
content:: Explain how military competition between countries could make it harder to develop advanced AI safely.
assessment-instructions:: Score out of 100. 100 for explaining that fear of falling behind a rival pushes governments and developers to deploy faster with less testing or fewer safety limits, or makes cooperation and regulation harder. 50 for naming racing or competition without saying how it reduces safety.

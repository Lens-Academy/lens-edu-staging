---
id: 577a2e74-46d6-46f4-b621-144293a8bce3
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how competition between AI companies and between countries rewards speed over safety, what the alignment tax is and how its size affects racing, and why racing can persist when every actor would prefer to slow down.

## Requires

## Helpful first
- [[AI companies]]

## Why it matters
Many risk arguments rest on the claim that developers will deploy systems before they are known to be safe because rivals are close behind. Understanding race dynamics helps you tell which proposals change the incentives, such as making safety cheaper or binding every rival to the same rules, and which only ask one actor to fall behind.

## Lenses
- [[../Lenses/IABIED - QA - Making Sense of the Death Race|Making sense of the death race]]: why people who fear AI keep racing to build it.
- [[../Lenses/AI Safety Atlas - Governance - Systemic Challenges|AI Safety Atlas: systemic challenges]]: how a competitive race punishes caution.
- [Alignment tax (AI Alignment Forum wiki)](https://www.alignmentforum.org/w/alignment-tax): the extra cost of building AI safely, and how to reduce it.
- [[../Lenses/AIF - Situational Awareness|Situational Awareness]]: the case that the US must race China to AGI.
- [[../Lenses/U4 - Is the Race Even Real|Is the race even real?]]: tests the claim that the US and China are racing.

## Tests

#### Question: FillBlank
id:: 348c2618-b080-4e77-896d-ed9f85d878c6
content:: The extra cost of building an AI system safely rather than unsafely, whether in time, compute or lost capability, is called the {{alignment tax|safety tax}}.

#### Question: Choice
id:: 84aafdb9-e856-41a7-88d6-a2efedc99d2e
content:: Which of these is an example of an alignment tax paid by an AI company?
options::
- [x] A safety evaluation that delays a model's release by two months
- A rival company releasing a stronger model first
- A chip export ban that raises the company's hardware costs
- A drop in usage after a model gets bad press
shuffle:: true

#### Question: Choice
id:: 4dd04c4c-c6c3-4e7c-91cd-188db0acae1b
content:: Suppose safety research made the alignment tax close to zero. How would that most likely change the behaviour of AI companies that are racing each other?
options::
- [x] More of them would adopt safety measures, since doing so costs them little
- They would stop racing, since capability would no longer matter
- They would drop safety measures, since these no longer give an edge
- They would need fewer safety measures, since models would be safe by default
shuffle:: true

#### Question: Choice
id:: 3e582c33-3d2c-4907-89dd-eadda9d1d4d3
content:: Two AI companies each choose to be cautious or to race. Each does better by racing whatever the other does, but both do better if both are cautious than if both race. Which game does this describe?
options::
- [x] A prisoner's dilemma
- A game of chicken
- A stag hunt
- A zero-sum game
shuffle:: true

#### Question: Choice
id:: 3a41ffef-14e8-4edc-bf09-04b6558a9490
content:: Two AI companies each prefer to be cautious if they are confident the other will be cautious too, but each will race if it expects the other to race. Which measure most directly helps them both stay cautious?
options::
- [x] A reliable way for each to check what the other is doing
- A bigger reward for whichever company reaches AGI first
- Keeping each company's safety plans secret from the other
- A larger safety team inside each company
shuffle:: true

#### Question: Choice
id:: b4801f72-d681-4942-9261-a98181244ffe
content:: Two AI companies each gain by racing whatever the other does. They sign a voluntary agreement to pause training at a set capability level, with no penalty for breaking it. Which change would most directly make the agreement hold?
options::
- [x] Penalties for breaking it, with a way to detect breaches
- Raising the capability level at which the pause starts
- Adding more companies to the agreement on the same terms
- Having each company's chief executive sign it personally
shuffle:: true

#### Question: Choice
id:: d17c285d-abda-48b2-a101-3865640b7ee1
content:: In an AI race where the first to reach a capability gets most of the reward, the leading company learns that its nearest rival is only weeks behind. How do simple race models predict this affects the leader's safety work?
options::
- [x] It cuts safety work to protect its lead
- It increases safety work to stand out from the rival
- It keeps safety work the same, since it is still ahead
- It pauses development until the rival catches up
shuffle:: true

#### Question: Choice
id:: 17ec7467-9bdd-46b9-a630-d91246b8ceaa
content:: Some people argue that a large lead for one safety-minded AI developer would reduce risk. What is the main reasoning behind this view?
options::
- [x] The leader could slow down for safety without being overtaken
- The leader would face less public scrutiny and so fewer delays
- Rivals would copy the leader's models instead of building their own
- A large lead would let the leader skip safety testing
shuffle:: true

#### Question: Choice
id:: 3c1e1b57-5ec5-4dd4-b953-04bc8e4d0341
content:: Simple game-theory models of AI races find that adding more competing teams raises the risk of an AI disaster. In these models, what is the main reason?
options::
- [x] Each team must cut more safety to keep a real chance of winning
- Teams copy each other's mistakes more often
- Each team's model is weaker and so harder to make safe
- Teams share less safety research with each other
shuffle:: true

#### Question: Choice
id:: 906e1d79-3c70-423a-ad33-8149a0d44c13
content:: OpenAI's Preparedness Framework, as updated in April 2025, says OpenAI may adjust its safety requirements in one situation. Which?
options::
- [x] A rival releases a high-risk system without comparable safeguards
- A government asks OpenAI to speed up its development
- OpenAI's own safety team asks for more testing time
- A new model passes every dangerous-capability test
shuffle:: true

#### Question: Choice
id:: 9b4841de-ff35-4068-bf85-5dac5ad99a47
content:: People who argue that the US must race China to build AGI usually rest the case on which claim?
options::
- [x] Whoever leads could gain a decisive military and economic edge
- Racing makes alignment research unnecessary for the winner
- Chinese labs are already years ahead of US labs at the frontier
- Competition between the two countries lowers the alignment tax
shuffle:: true

#### Question: Choice
id:: 28a573d8-ba32-443c-8e8d-475eeedadf91
content:: Critics say a US–China race to AGI is partly self-fulfilling. What do they mean?
options::
- [x] Acting as if a race exists can push the rival to race
- Each country's AI progress relies mostly on research the other publishes
- Racing tends to make both countries' AI systems safer over time
- A race ends once one side admits it is behind
shuffle:: true

#### Question: Open
id:: 42c03881-3c89-4eb6-97e8-8f3c1ab5b4ee
content:: Why might an AI company whose leaders believe advanced AI could be catastrophic still race to build it? Answer in two or three sentences.
assessment-instructions:: Score out of 100. 100 for the core logic: holding back alone doesn't stop rivals building it, so the company would just lose its position, and it may believe it is safer than the rivals who would lead instead. Also accept profit or investor pressure combined with that logic. 50 for "competition" or "money" alone, without explaining why restraint by one company doesn't remove the risk.

#### Question: Open
id:: 1b25b3f6-2f22-49ba-9771-c2c3bee62f02
content:: Name two ways to weaken AI race dynamics that don't depend on any single developer choosing to fall behind.
assessment-instructions:: Score out of 100. 50 points each, for any two of: making safety cheaper (lowering the alignment tax); regulation that applies to every developer; international agreements; ways to verify compliance, such as tracking compute; shared safety standards or liability rules. No credit for "companies should choose to be careful".

#### Question: Open
id:: 682e1b9b-06e7-40c0-ad57-b3afb47c4456
content:: Why is a race between countries to build AI usually harder to slow down than a race between companies in one country?
assessment-instructions:: Score out of 100. 100 for the key point: one government can bind all its companies with law, but no authority stands above countries, so slowing them needs agreements they choose to keep, usually with verification. 50 for saying countries care about security or power without explaining the missing higher authority.

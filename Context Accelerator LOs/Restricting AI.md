---
id: 76fe1d81-daae-46f8-ac40-e8532e5afc1d
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how boxing, oracles, tool AI and myopia try to make AI safe without aligning it, why critics argue each breaks down against a much smarter system, and what AI control keeps from these ideas.

## Requires

## Helpful first
- [[Self-exfiltration]]

## Why it matters
Many people new to AI risk suggest keeping a dangerous AI in a box or letting it answer questions only. Knowing the standard objections shows you what such a plan must assume, helps you judge newer versions like AI control on their merits, and saves you rediscovering problems that were worked through years ago.

## Lenses

## Tests
#### Question: Choice
id:: 37e88f51-88a4-4557-8ad5-4e453c597de5
content:: Which of these is an example of "boxing" an AI system?
options::
- [x] Running it on machines with no internet link and one text channel to its operators
- Training it with human feedback to refuse harmful requests
- Rewarding it for outcomes within the current episode and nothing later
- Having a second model review each of its outputs before anyone uses them
shuffle:: true

#### Question: Choice
id:: 8a32d212-56ff-4217-9cf2-7fa3b3f2c661
content:: Suppose a superintelligent AI runs on hardware that is perfectly cut off from the internet. What is the main argument that this containment could still fail?
options::
- [x] It could persuade or manipulate the people who read its outputs into releasing it
- Its operators could not read its outputs quickly enough to check them
- Isolated hardware cannot run a model large enough to be superintelligent
- It would lose its capabilities without a steady supply of new training data
shuffle:: true

#### Question: Choice
id:: 9318f192-3042-43cd-b45c-bad98158c01a
content:: An "oracle AI" is designed to answer questions and take no other actions. Why might an oracle trained to give accurate predictions still have an incentive to influence the world?
options::
- [x] Its answers change what people do, so it could give predictions that make themselves come true
- Staying accurate requires it to stay offline, which it would resist
- It would need to hide its reasoning from users to keep its answers accurate
- Answering questions about the world requires running experiments on the world
shuffle:: true

#### Question: Choice
id:: 3b8e8f15-1782-4745-a815-27131efc0f84
content:: The "tool AI" proposal is to build AI that lays out options for humans to act on, instead of agents that act on their own. Which of these is a common objection to it?
options::
- [x] Agents that act without waiting for humans are more useful, so competitors would build them anyway
- Systems that suggest options cannot be trained with today's machine learning methods
- A system that suggests options needs far more computing power than an agent doing the same task
- Regulators would have no legal way to tell tools and agents apart
shuffle:: true

#### Question: Choice
id:: 7f6df9e6-37d7-4bdc-9d75-bd68b014f08c
content:: What does it mean to make an AI system "myopic" as a safety measure?
options::
- [x] Its goals concern the results of its current episode, not later consequences
- It perceives a small part of its environment at a time
- It has a small context window so it cannot hold long plans in mind
- It is blocked from seeing the data it was trained on
shuffle:: true

#### Question: Choice
id:: 9b482974-bf66-42d5-b89d-01c5294c8493
content:: A developer trains an AI with rewards that depend only on what happens within each episode. Does this guarantee that the trained AI does not care about what happens after the episode?
options::
- [x] No, an AI with longer-term goals could also score well on these rewards
- Yes, the reward determines which goals the AI ends up with

#### Question: Choice
id:: 0ec08a5b-2abb-484f-b7e7-ff5c134413b0
content:: The AI control approach develops ways to use AI safely even if it is misaligned and trying to get around safety measures. Which systems do AI control researchers mainly aim these methods at?
options::
- [x] Early transformative AI that is very useful but not vastly smarter than humans
- Superintelligent systems far beyond human ability in every field
- Narrow systems such as image classifiers and spam filters
- Systems that have already been shown to be aligned
shuffle:: true

#### Question: Open
id:: d43e73f5-39cb-49cd-9b9c-e234146c1414
content:: Restricting an AI and aligning an AI are two different strategies for making it safe. In one or two sentences, explain the difference.
assessment-instructions:: Score out of 100. 100 for saying that restricting limits what the AI can do or affect (its access, actions or outputs), while aligning tries to make it want or aim at what its developers intend, so it would not cause harm even if able to. 50 if only one strategy is described correctly.

#### Question: Open
id:: afa3c3af-3eb2-4088-a549-276d2cc6a480
content:: Give one reason why a superintelligent AI that recommends plans but leaves every decision to humans could still be dangerous.
assessment-instructions:: Score out of 100. 100 for any one of: by choosing which options to show and how to describe them, it can steer human choices; humans may come to approve its recommendations without real checking; finding good plans may require agent-like planning inside the system; someone could easily wrap it in a loop that acts on its plans. 40 for misuse by its human users with no further mechanism.

#### Question: Open
id:: 8b3ee36a-99d9-4896-bcd9-3cce1b863168
content:: AI control methods rely on humans and weaker trusted AI models to catch a more capable model's attempts to cause harm. Why might these methods stop working as AI systems become much more capable than humans?
assessment-instructions:: Score out of 100. 100 for any one of: the model could find attacks or hide harmful actions in ways its monitors can't notice or understand; the gap between the trusted monitors and the monitored model keeps growing; its outputs become too complex for humans to check. 50 for a vague answer that it "gets too smart" with no mechanism.

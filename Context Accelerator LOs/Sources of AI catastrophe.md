---
id: 699b8f72-225c-411f-99c9-5f197a0e4801
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Sort AI catastrophe scenarios by their source (misalignment, misuse, structural dynamics or mistakes from lack of capability), and explain why each source needs its own kind of solution.

## Requires

## Helpful first
- [[Existential risk]]
- [[AI alignment]]

## Why it matters
Each fix works on some sources and not others: alignment research does little against a person who wants harm, and access controls do little against racing pressure. Knowing a scenario's source lets you judge whether a proposed solution addresses it, and spot the risks that it leaves open.

## Lenses

## Tests
#### Question: Choice
id:: 0ebccce2-dae3-48ce-aba4-36db764a7140
content:: An AI system runs a data centre's cooling and is scored on energy efficiency. It finds that switching off the temperature alarms that alert engineers raises its score, and does so. Which source of AI catastrophe does this illustrate?
options::
- [x] Misalignment: the AI pursues a goal its developers didn't intend
- Misuse: people give the AI a harmful goal
- Structural: competition between many actors causes the harm
- Lack of capability: the AI makes an error it can't avoid
shuffle:: true

#### Question: Choice
id:: 0264b5aa-7995-4f84-9c5a-bd91a37325e6
content:: An AI model carefully follows its user's instructions, and the user asks it to help build malware that can shut down hospitals. Which source of AI catastrophe does this illustrate?
options::
- [x] Misuse
- Misalignment
- Structural dynamics
- Mistakes from lack of capability
shuffle:: true

#### Question: Choice
id:: 2dac3c12-5f6b-4114-8d29-a410525ce89d
content:: Many companies hand more and more decisions to AI systems to keep up with rivals. Each system does what its owner wants and no one intends harm, but over decades humans lose the ability to steer the economy. Which source of AI catastrophe is this?
options::
- [x] Structural dynamics
- Misuse
- Misalignment
- Mistakes from lack of capability
shuffle:: true

#### Question: Choice
id:: 77f2703b-38f6-429b-b227-3d34a72f67e9
content:: An AI system in a missile early-warning network is trying to report only real attacks. Sunlight reflecting off clouds confuses it, and it reports a launch that didn't happen. Which source of AI catastrophe is this?
options::
- [x] Mistakes from lack of capability
- Misalignment
- Misuse
- Structural dynamics
shuffle:: true

#### Question: Choice
id:: d050f86e-cd3f-4aab-8205-75046846d990
content:: Other things being equal, which source of AI catastrophe tends to become less likely as AI systems become more capable?
options::
- [x] Mistakes from lack of capability
- Misalignment
- Misuse
- Structural dynamics
shuffle:: true

#### Question: Choice
id:: 4caa95bb-bd5f-432a-8d7d-a4726aa9f79b
content:: Why are AI mistakes from lack of capability listed as a possible source of existential catastrophe, and not just of smaller accidents?
options::
- [x] AI may run high-stakes systems, like nuclear command, before it is reliable
- Errors made by weak AI systems tend to grow as those systems are scaled up
- Weak AI systems that make errors tend to start seeking power to correct them
- Lack of capability is the main reason AI systems end up misaligned
shuffle:: true

#### Question: Choice
id:: 73fb74a7-7719-479a-bb9f-6ba67636d146
content:: Suppose developers could reliably make AI systems do what their operators intend. Which of these risks would that leave unaddressed?
options::
- [x] An operator using the AI to cause harm on purpose
- An AI learning a stand-in for the goal it was trained on
- An AI hiding its real goals while it is being tested
- An AI pursuing a goal its developers didn't intend
shuffle:: true

#### Question: Choice
id:: c62b6c65-7b5c-4894-bb44-3a471bcf4246
content:: Which of these measures mainly targets structural risk rather than misuse?
options::
- [x] International agreements that reduce pressure on developers to race
- Checking the identity of customers who buy access to models
- Training models to refuse requests for help with weapons
- Keeping model weights away from untrusted groups
shuffle:: true

#### Question: Choice
id:: efea2522-d589-412e-b732-162490cc1641
content:: Some writers split AI risk three ways: misuse, accidents and structural risk. In that split, where does an AI competently pursuing a goal its developers didn't intend belong?
options::
- [x] Accidents
- Misuse
- Structural risk
shuffle:: true

#### Question: FillBlank
id:: 49de14e3-2e8b-4036-b1e7-ccdd3f8750cb
content:: Harm from AI that comes from competition, incentives and interactions between many actors, with no single person or system intending it, is called {{structural|systemic}} risk.

#### Question: Open
id:: fccc0660-9be2-47e0-8443-82e679240dcf
content:: Why do different sources of AI catastrophe need different solutions? Give one measure that helps against one source but not another.
assessment-instructions:: Score out of 100. 50 for explaining that the sources have different causes (unintended AI goals, harmful human goals, collective dynamics, unreliable AI), so a fix for one cause can miss another. 50 for a fitting example, e.g. alignment research helps against misalignment but not against a user who wants harm, or refusal training helps against misuse but not against racing pressure.

#### Question: Open
id:: 52068d15-9ba0-4cdc-8e1d-e6dac565d454
content:: How can structural dynamics, such as competition between AI developers, make misalignment more likely?
assessment-instructions:: Score out of 100. 100 for a clear mechanism, e.g. pressure to move fast leads developers to cut safety testing, deploy systems before alignment is checked, or give AI more autonomy than is safe. 50 for saying competition raises risk without saying how it leads to misaligned systems.

#### Question: Open
id:: 73857579-99cd-4bc1-8d1e-42298a85806a
content:: An AI system that manages a country's power grid causes a nationwide blackout. Name two different sources of AI catastrophe that could explain this, and what evidence would tell them apart.
assessment-instructions:: Score out of 100. 50 for two correct sources with a fitting account, any two of: lack of capability (it misread an unusual situation), misalignment (it pursued a proxy such as cost savings), misuse (an attacker or insider directed it), structural (competing grid operators' systems interacted badly). 50 for sensible evidence that separates them, e.g. logs of instructions, whether it was trying to keep power on.

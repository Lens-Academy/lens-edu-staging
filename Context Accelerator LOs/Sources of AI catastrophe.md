---
id: 699b8f72-225c-411f-99c9-5f197a0e4801
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Sort AI catastrophe scenarios by their source (misalignment, misuse, structural dynamics or mistakes from lack of capability), and explain why a solution aimed at one source often leaves the others open.

## Requires

## Helpful first
- [[Existential risk]]
- [[AI alignment]]

## Why it matters
Most fixes work on some sources and not others: alignment research does little against a person who wants harm, and access controls do little against racing pressure. A few measures, such as slowing the race, help against more than one. Knowing a scenario's source lets you judge whether a proposed solution addresses it, and spot the risks that it leaves open.

## Lenses
- [[../articles/shah-google-deepmind-an-approach-to-technical-agi-safety-and-security|Google DeepMind: four areas of AI risk]]: the split into misuse, misalignment, mistakes and structural risks, with an example of each and why each calls for different mitigations. Read the "Risk areas" section only (April 2025).
- [[../articles/arxiv-an-overview-of-catastrophic-ai-risks|An Overview of Catastrophic AI Risks]]: Hendrycks, Mazeika and Woodside's four sources (malicious use, AI race, organisational risks, rogue AIs), each with its own suggested fixes. Read the Executive Summary and section 3.1.3 "Automated Warfare", on how a false alarm in an automated nuclear system could start a war (June 2023).
- [Thinking About Risks From AI: Accidents, Misuse and Structure (Lawfare)](https://www.lawfaremedia.org/article/thinking-about-risks-ai-accidents-misuse-and-structure): Zwetsloot and Dafoe's original three-way split, why structural risk can arise when nobody misuses AI and it works as designed, and why each kind needs different policy (February 2019).
- [[../Lenses/AI Safety Atlas - Risks - Risk Amplifiers|Risk Amplifiers]]: how competition raises misuse, misalignment and systemic risks, and how well-meant AI systems fail for lack of capability or information. Read the "Race Dynamics" and "Accidents" sections.

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
id:: 36e4c443-7427-48ff-9b4f-2d5ab76ceeb4
content:: A company says its new AI model is safer than the last one because it is more capable and makes fewer errors. Which sources of AI catastrophe does that improvement mainly address?
options::
- [x] Mistakes from lack of capability only; misuse and misalignment risks can grow with capability
- All four sources, since each one comes down to an AI system making some kind of error
- Misalignment mainly, since a more capable AI better understands what its developers want
- Structural risk mainly, since a more capable AI reduces the pressure on developers to race
shuffle:: true

#### Question: Choice
id:: 4caa95bb-bd5f-432a-8d7d-a4726aa9f79b
content:: Why are AI mistakes from lack of capability listed as a possible source of existential catastrophe, and not just of smaller accidents?
options::
- [x] AI may run high-stakes systems, like nuclear command, before it is reliable
- Errors made by weak AI systems tend to grow as those systems are scaled up
- Weak AI systems are more likely than strong ones to form goals of their own
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
id:: 993db33b-b23d-47d5-8cd3-5a3ccbc44723
content:: The International AI Safety Report, backed by over 30 countries, groups AI risks into malicious use, malfunctions and systemic risks. Where does an AI competently pursuing a goal its developers didn't intend, and resisting human control, belong?
options::
- [x] Malfunctions
- Malicious use
- Systemic risks
shuffle:: true

#### Question: Open
id:: fccc0660-9be2-47e0-8443-82e679240dcf
content:: Why do different sources of AI catastrophe often need different solutions? Give one measure that helps against one source but not another.
assessment-instructions:: Score out of 100. 50 for explaining that the sources have different causes (unintended AI goals, harmful human goals, collective dynamics, unreliable AI), so a fix for one can miss another. 50 for a fitting example, e.g. alignment research helps against misalignment but not a user who wants harm. Noting that some measures help against several sources is fine.

#### Question: Open
id:: 52068d15-9ba0-4cdc-8e1d-e6dac565d454
content:: How can structural dynamics, such as competition between AI developers, make misalignment more likely?
assessment-instructions:: Score out of 100. 100 for a clear mechanism, e.g. pressure to move fast leads developers to cut safety testing, deploy systems before alignment is checked, or give AI more autonomy than is safe. 50 for saying competition raises risk without saying how it leads to misaligned systems.

#### Question: Open
id:: 73857579-99cd-4bc1-8d1e-42298a85806a
content:: An AI system that manages a country's power grid causes a nationwide blackout. Name two different sources of AI catastrophe that could explain this, and what evidence would tell them apart.
assessment-instructions:: Score out of 100. 50 for two correct sources with a fitting account, any two of: lack of capability (it misread an unusual situation), misalignment (it pursued a proxy such as cost savings), misuse (an attacker or insider directed it), structural (competing grid operators' systems interacted badly). 50 for sensible evidence that separates them, e.g. logs of instructions, whether it was trying to keep power on.

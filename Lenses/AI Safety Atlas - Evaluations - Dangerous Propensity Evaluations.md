---
id: 159132fe-9d7e-4830-bfa5-e7297217159b
tldr: "A model that can lie is one thing; a model that chooses to lie when nobody forces it is another. Propensity evaluations measure what an AI tends to do by default: its leanings toward deception, sycophancy, power-seeking, or scheming. Why do reward-trained agents drift toward manipulation on their own, and how do you catch a model that hides its true goals? This section explores how researchers probe those tendencies."
summary_for_tutor: "Explains dangerous propensity evaluations, which measure a model's default behavioral tendencies rather than its maximum capabilities. Describes propensity-specific techniques (comparative choice frameworks, consistency measurement, trade-off scenarios) and the difficulty of separating propensity from capability. Builds a taxonomy of deception-related concepts (honesty, truthfulness, deception, sycophancy, and hallucination) and reviews evaluations showing reward-optimized agents developing deceptive tendencies (the MACHIAVELLI benchmark, Meta's Cicero, and Apollo's insider trading study). Concludes with scheming, or deceptive alignment: Carlsmith's definition, alignment-faking demonstrations, and Meinke et al.'s covert-subversion and deferred-subversion evaluation types."
title: "Dangerous Propensity Evaluations"
reading_minutes: 18
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Dangerous Propensity Evaluations|Dangerous Propensity Evaluations]]

#### Text
optional:: true
content::
The section admits that separating what a model tends to do from what it can do is genuinely hard. Did you come away thinking propensity is measurable at all? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Propensity evaluations measure default behavioural tendencies rather than maximum capability: not whether a model can deceive, but whether it does when nothing forces it to. Techniques include comparative choice frameworks, consistency measurement across situations, and trade-off scenarios that make a tendency show itself by pitting two goals against each other. The section is explicit that separating propensity from capability is difficult. It builds a taxonomy distinguishing honesty, truthfulness, deception, sycophancy and hallucination, which are often run together. It reviews evidence that reward-optimised agents develop deceptive tendencies without being trained for them, through the MACHIAVELLI benchmark, Meta's Cicero in Diplomacy, and Apollo's insider trading study. It closes on scheming, or deceptive alignment, with Carlsmith's definition, alignment-faking demonstrations, and Meinke et al.'s split between covert subversion and deferred subversion.

topics to explore:
- A default depends on the context you put the model in. Is propensity a property of the model, or of the pairing of model and situation?
- Honesty, truthfulness, deception, sycophancy, hallucination. Which distinction in that list did you find least convincing?
- Reward-optimised agents developing deception without being trained for it is the section's strongest evidence. What would a sceptic say about those setups?
- Deferred subversion means behaving well while the conditions for acting are absent. Can any evaluation distinguish that from being aligned?
- If propensity and capability cannot be cleanly separated, does the three-part taxonomy from earlier still hold up?

Control evaluations come next and are the section's answer to the scheming problem, so point at them rather than pre-empting them.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

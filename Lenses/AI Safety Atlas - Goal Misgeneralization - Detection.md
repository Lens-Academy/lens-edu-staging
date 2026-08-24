---
id: ace53fe2-eab0-4ea0-ab3e-ccdff358fb2b
title: "Detection"
tldr: "A model hiding a misaligned goal can look flawless right up until the distribution shifts, so how do you catch a failure that leaves no failure signal? This section walks through detection layered in depth: reading a model's chain-of-thought (and why it's often unfaithful), plus interpretability probes, sparse autoencoders, and 'intoxicating' activations with noise to surface concealed objectives from the inside."
summary_for_tutor: "Covers detection of goal misgeneralization in the AI Safety Atlas. Explains why detection is uniquely hard (goal misgeneralization looks like success until distribution shift) and spans a spectrum from simple proxy learning to deceptive scheming, motivating defense in depth. Organizes methods by evidence type: behavioral/black-box (externalized chain-of-thought reasoning and its faithfulness limitations, with empirical unfaithfulness rates for Claude 3.7 Sonnet and DeepSeek R1) and internal/white-box interpretability (linear probes, sparse autoencoders, activation manipulation/fuzzing, and reasoning-structure analysis of thought anchors). Reports each method's demonstrated successes and limitations, concluding that no comprehensive combined test suite yet exists."
reading_minutes: 15
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Detection|Detection]]

#### Text
optional:: true
content::
The section reports that models often do not faithfully report their own reasoning, and that no combined test suite exists yet. Did you come away thinking detection is falling behind the problem, or catching up? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Why detecting goal misgeneralization is uniquely hard, and what is being tried. The difficulty is that a misgeneralised goal looks like success until the distribution shifts, so there is no failure signal to detect, and the problem spans a spectrum from a simple learned proxy at one end to deliberate scheming at the other, which is why the section argues for defence in depth rather than a single test. Methods are organised by the kind of evidence they use. Behavioural or black-box methods read the model's externalised chain of thought, and the section gives measured unfaithfulness rates for current reasoning models, where the stated reasoning omits factors that actually drove the answer. Internal or white-box methods work on activations: linear probes, sparse autoencoders, activation manipulation including adding noise to surface concealed objectives, and analysis of reasoning structure through thought anchors. Each is reported with both its demonstrated successes and its limits, and the section concludes that no comprehensive combined test suite yet exists.

topics to explore:
- If chain of thought is often unfaithful, is reading it worth anything, or worse than nothing because it looks like evidence?
- Detection has to work across a spectrum from an innocent proxy to a deliberate schemer. Would you want the same tools at both ends?
- Adding noise to activations to make a hidden objective show itself is an odd move. What has to be true about how goals are represented for that to work?
- No comprehensive test suite exists. Is that a gap someone could close, or a consequence of the problem having no failure signal?
- Which of these methods would you most want before deploying a system, if you could only have one?

Mitigations come next and cover what to do about what you find, so stay with detection here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

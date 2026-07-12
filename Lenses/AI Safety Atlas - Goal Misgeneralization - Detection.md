---
id: ace53fe2-eab0-4ea0-ab3e-ccdff358fb2b
title: "Detection"
tldr: "A model hiding a misaligned goal can look flawless right up until the distribution shifts, so how do you catch a failure that leaves no failure signal? This section walks through detection layered in depth: reading a model's chain-of-thought (and why it's often unfaithful), plus interpretability probes, sparse autoencoders, and 'intoxicating' activations with noise to surface concealed objectives from the inside."
summary_for_tutor: "Covers detection of goal misgeneralization in the AI Safety Atlas. Explains why detection is uniquely hard (goal misgeneralization looks like success until distribution shift) and spans a spectrum from simple proxy learning to deceptive scheming, motivating defense in depth. Organizes methods by evidence type: behavioral/black-box (externalized chain-of-thought reasoning and its faithfulness limitations, with empirical unfaithfulness rates for Claude 3.7 Sonnet and DeepSeek R1) and internal/white-box interpretability (linear probes, sparse autoencoders, activation manipulation/fuzzing, and reasoning-structure analysis of thought anchors). Reports each method's demonstrated successes and limitations, concluding that no comprehensive combined test suite yet exists."
---

#### Article
source:: [[../articles/AI Safety Atlas - Goal Misgeneralization - Detection|Detection]]

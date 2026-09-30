---
id: 8691b0e4-924f-4685-8f1f-6ce6c6b20205
reading_minutes: 8
tutor_minutes: 3
summary_for_tutor: "Excerpt from a 2024 BlueDot blog introduction to mechanistic interpretability (author listed as Sarah). Defines the field as trying to understand the internal reasoning of trained networks, which are 'black boxes' with billions or trillions of parameters. Gives two motivations: insight into the rationale behind high-stakes automated decisions (for example, spotting a hiring model biased by race or gender), and one path to detecting unaligned behaviour that output-only assessment may miss (deception, sycophancy, reward-hacking). Then explains why it is hard: identifying which input a neuron actually responds to takes repeated experiments, and polysemanticity (possibly caused by superposition) means one neuron can represent several features, as with an InceptionV1 neuron responding to both cat faces and car fronts."
title: Introduction to Mechanistic Interpretability
# tldr: Judging a model only by its behavior has a problem — behavior can be faked. Mechanistic interpretability aims to verify the internal reasons for a model's output by reverse-engineering its circuits. If it works, we could detect dangerous goals before the model ever acts on them.
discussion: https://discord.com/channels/1440725236843806762/1483418591482347723
---
%% #### Text
content:: %%
%% COMMENTED OUT (AI slop):
This perspective argues that safety requires a white-box approach. We cannot trust a model based only on its behavior. Behavior can be faked. Mechanistic interpretability aims to provide a way to verify the internal reasons for a model's output. If we could understand the circuits of a model, we would be able to detect dangerous goals before the model acts on them.{++{"author":"Plex's AI","timestamp":1790617855900}@@
%%++}

#### Article
source:: [[../articles/sarah+bluedot-introduction-to-mechanistic-interpretability]]
to:: "to more efficiently achieve reward (reward-hacking). "

#### Article
from:: "## What makes mechanistic interpretability hard?"
to:: "contribution of individual neurons to a model’s cognition process."

#### Text
content::
Ask the AI Tutor any questions you may have:

#### Chat
instructions::
Help the user understand this article, or help them with other questions they have.
---
id: 8691b0e4-924f-4685-8f1f-6ce6c6b20205
reading_minutes: 8
tutor_minutes: 3
summary_for_tutor: {--{"author":"Elua's AI","timestamp":1790784055942}@@Covers --}{++{"author":"Elua's AI","timestamp":1790784055942}@@"Excerpt from a 2024 BlueDot blog introduction to mechanistic interpretability (author listed as Sarah). Defines the field as trying to understand the internal reasoning of trained networks, which are 'black boxes' with billions or trillions of parameters. Gives two motivations: insight into ++}the {--{"author":"Elua's AI","timestamp":1790784055942}@@motivation--}{++{"author":"Elua's AI","timestamp":1790784055942}@@rationale behind high-stakes automated decisions (for example, spotting a hiring model biased by race or gender),++} and {--{"author":"Elua's AI","timestamp":1790784055942}@@core challenges of mechanistic interpretability. Argues--}{++{"author":"Elua's AI","timestamp":1790784055942}@@one path to detecting unaligned behaviour++} that {--{"author":"Elua's AI","timestamp":1790784055942}@@behavioral evaluation alone is insufficient because behavior can be faked, so white-box inspection of internal circuits is needed--}{++{"author":"Elua's AI","timestamp":1790784055942}@@output-only assessment may miss (deception, sycophancy, reward-hacking). Then explains why it is hard: identifying which input a neuron actually responds++} to {--{"author":"Elua's AI","timestamp":1790784055942}@@detect deception--}{++{"author":"Elua's AI","timestamp":1790784055942}@@takes repeated experiments,++} and {--{"author":"Elua's AI","timestamp":1790784055942}@@misalignment. Explains polysemanticity and superposition --}{++{"author":"Elua's AI","timestamp":1790784055942}@@polysemanticity (possibly caused by superposition) means one neuron can represent several features, ++}as {--{"author":"Elua's AI","timestamp":1790784055942}@@key technical obstacles --}{++{"author":"Elua's AI","timestamp":1790784055942}@@with an InceptionV1 neuron responding ++}to {--{"author":"Elua's AI","timestamp":1790784055942}@@isolating individual features within neural networks.--}{++{"author":"Elua's AI","timestamp":1790784055942}@@both cat faces and car fronts."++}
title: Introduction to Mechanistic Interpretability
# tldr: Judging a model only by its behavior has a problem — behavior can be faked. Mechanistic interpretability aims to verify the internal reasons for a model's output by reverse-engineering its circuits. If it works, we could detect dangerous goals before the model ever acts on them.
discussion: https://discord.com/channels/1440725236843806762/1483418591482347723
---
#### Text
content::
{++{"author":"Plex's AI","timestamp":1790617855900}@@%% COMMENTED OUT (AI slop):
++}This perspective argues that safety requires a white-box approach. We cannot trust a model based only on its behavior. Behavior can be faked. Mechanistic interpretability aims to provide a way to verify the internal reasons for a model's output. If we could understand the circuits of a model, we would be able to detect dangerous goals before the model acts on them.{++{"author":"Plex's AI","timestamp":1790617855900}@@
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
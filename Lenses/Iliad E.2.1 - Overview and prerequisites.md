---
id: '998b5140-d7c7-4807-b705-fbb9ce473ef4'
title: "E.2.1 Overview and prerequisites"
tldr: "Prerequisites in information theory, statistics and cryptography, what the worksheet teaches about steganography, and a suggested fast track."
summary_for_tutor: "Opening part of Iliad worksheet E.2 Steganography & Backdoors: prerequisites (entropy, mutual information, compression, multivariate normal, Markov and Chebyshev, pseudo-random functions, one-way functions, public key encryption), learning outcomes (sender, receiver, channel, cover distribution, message space), and the fast track. The day timetable and paper-reading list are hidden facilitator logistics."
authors:
  - Stephan Wäldchen (Independent)
  - Louis Jaburi (EleutherAI)
source_url: https://iliad-intensive.org/safety/steganography/
upstream_commit: '46ea03c036a05c7687d702d509037521e19f3b0c'
provenance_recorded_at: '2026-10-08'
---

#### Text
content::
\## 1. Prerequisites

- **Information Theory:**
  - (Conditional) Entropy, Mutual Information
  - Lossy vs Lossless Compression
- **Statistics**:
  - Multivariate Normal distribution: moments, density function
  - Concentration Inequalities: Markov/Chebyshev
- **Cryptography**:
  - Pseudo-Random Functions, One-Way functions
  - Public Key encryption

:::callout {title="What you'll learn" tone="neutral"}

- The students should understand the basic idea of steganography as a technique to hide messages and that it makes COT reasoning illegible.
- They should get an intuitive grasp on how it's possible to hide messages in innocent-looking text via the game, and then learn the specific technique using the pseudo-random function.
- They learn to think about the steganographic setup in many different contexts and are able to recognise sender, receiver, channel, cover distribution, message space, etc, so that they can think about questions in steganographic terms.

:::

%% Facilitator logistics (hidden from learners):
\## 2. Roadmap for today

This teaching guide outlines how the materials on both steganography and backdoors were taught in-person.

**10:00** **Fun exercise: The Stego Game**

**11:30** Short whiteboard presentations about steganography theory and practice. We explain the difference between informational and computational indistinguishability, how the former one would require a very large random seed, while the latter can be implemented efficiently, while being secure only against computationally constrained adversaries (which is a reasonable assumption). Then we go through the basic idea behind: [Undetectable Steganography for Language models](https://openreview.net/pdf?id=fq6aQoMSHz), using pseudo-randomness to design a universal scheme for LLM-based steganography.

**12:00** Paper Reading (in breakout rooms if possible): [Models can hide COT with steganography](https://arxiv.org/html/2506.01926v2); [Steganography can arise and not easily prevented by paraphrasing](https://arxiv.org/pdf/2410.03768); [Model weight extractions](https://arxiv.org/pdf/2511.02620) (This one wasn't as useful). Discussion Prompts for the papers: Why is this scenario a danger to AI safety? What are sender, receiver, adversary? What is the channel used How was the secret key exchanged? Is the steganography successful? How does it emerge? Give a small example of a possible stego-text and payload

**12:30** **Lunch Break**

**13:30** **Discussion of the Papers that were read**

**13:45** **Talk by Louis**

**14:45** **Pause**

**15:00** **Discussion: Backdoors in LLMs** How would you plant a backdoor in an LLM?

**15:15** **Exercise**: Construction of the Random ReLU two-layer network from Based on the paper: [**Shafi Goldwasser**](https://arxiv.org/pdf/2204.06974) et al. The exercise is broken down into intermediate steps that are simple enough for the students to go through.

**16:00** Paper reading: [**Unelicitable Backdoors via Cryptographic Transformer Circuits**](https://arxiv.org/html/2406.02619v1); [**Undetectable Backdoors in Model Parameters: Hiding Sparse Secrets in High Dimensions**](https://arxiv.org/html/2605.04209v2) (with an isotropic Gaussian dither of the weights); [**Statistically Undetectable Backdoors in Deep Neural Networks**](https://arxiv.org/html/2607.09532v1) (deep networks, but constrained architecture); [**Backdoor Channels Hidden in Latent Space: Cryptographic Undetectability in Modern Neural Networks**](https://arxiv.org/html/2605.13214) (conjectured white box undiscoverable). What is the advantage of their backdoor in Section 4.2 compared to Section 4.1? What are the limitations of the current approaches? How bad would this be for the worst-case interp stuff from yesterday (in the current form and in a more sophisticated setting)?

**16:50** **Pause**

**17:00** Presentation: **Merlin-Arthur Classifiers**

**18:00** **Dinner**
%%

\## 3. Fast-Track

Simply read the description in "main content" and ask a language model of your choice to help you understand.

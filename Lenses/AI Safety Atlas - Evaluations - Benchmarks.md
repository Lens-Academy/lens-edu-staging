---
id: dac35627-3788-4cde-9ce7-64b01b6b09d0
tldr: "You can't build a safe bridge with no measuring tape, and for years AI had no measuring tape. Benchmarks are AI's standardized tests, and they don't just measure progress, they define what counts as progress. This section traces how they shape both capabilities and safety."
summary_for_tutor: "Introduces benchmarks as standardized tools for measuring and comparing what AI systems can and cannot do, and argues they actively shape research direction rather than only measuring it. Traces their evolution through computer vision (MNIST, CIFAR, ImageNet) and language models since the transformer, showing how each solved benchmark prompts a harder successor. Explains how safety benchmarks establish verifiable, reproducible standards for 'safe for deployment' and thereby influence both technical safety research and governance."
title: "Benchmarks"
reading_minutes: 22
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Benchmarks|Benchmarks]]

#### Text
optional:: true
content::
The section argues benchmarks do not just measure progress, they decide what counts as progress. Did that convince you, and if it is true, is it good or bad for safety? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Benchmarks as standardised tools for measuring and comparing what AI systems can and cannot do, with the argument that they actively shape research direction rather than only recording it, since what gets measured is what gets optimised. The section traces their history through computer vision, from MNIST to CIFAR to ImageNet, and through language models since the transformer, showing a repeating pattern where each solved benchmark prompts a harder successor. It then argues that safety benchmarks matter for the same reason: by establishing verifiable, reproducible standards for what counts as safe enough to deploy, they shape both technical safety research and the governance built on top of it.

topics to explore:
- If benchmarks define what counts as progress, then a safety benchmark defines what counts as safe. Who should be setting them?
- Each solved benchmark gets a harder successor. Does that pattern work the same way for safety, where there is no obvious "harder" version of not causing harm?
- Vision benchmarks had a clear correct answer. What is the equivalent for a safety property?
- Optimising against a benchmark is exactly how Goodhart's law bites, which this course covered earlier. Does the section reckon with that here?

The chapter's later sections cover what safety evaluations measure and how, so stay with benchmarks as a measurement tradition here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

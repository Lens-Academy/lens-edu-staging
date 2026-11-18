---
id: a07ab054-ce17-4da7-8735-cf2a6eec8a7d
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain in plain terms what a neural network is, how it relates to deep learning, and why neural networks went from a niche approach to the basis of modern AI once enough data and compute became available.

## Requires
- [[Machine learning]]

## Helpful first

## Why it matters
As of November 2026, the leading AI systems, including chatbots such as ChatGPT and Claude, are neural networks. Their abilities come from billions of learned numbers rather than written rules, which is why developers can't simply read or edit what these systems will do, and why more data and compute keep making them more capable.

## Lenses

## Tests

#### Question: Open
id:: d2e0127b-e1d2-4296-81a9-c7fd115fafdf
content:: In a sentence or two, and without technical terms, what is a neural network?
assessment-instructions:: Score out of 100. 100 for: many simple connected units, usually arranged in layers, whose connection strengths are learned from data during training so the network gets better at a task. 50 if it gives the structure but not the learning, or the learning but not the structure. 0 for a hand-written program or a literal brain simulation.

#### Question: Choice
id:: aed96cab-3195-4236-818b-c72eed37a0fa
content:: What does a single unit, or artificial neuron, in a neural network do?
options::
- [x] Combines numbers from its inputs and passes on a result
- Stores one fact that the network has learned
- Runs a small program written for one task
- Chooses which other units it connects to
shuffle:: true

#### Question: FillBlank
id:: 28b7b7ae-e00f-45f5-a06b-4e15447aa746
content:: Training a neural network adjusts its {{weights|parameters|connection weights}}: the numbers that set how strongly each unit's output affects the units it connects to.

#### Question: Choice
id:: af5cf696-942b-4cf7-a5bd-cdb8013c49d2
content:: How do artificial neural networks relate to the brain?
options::
- [x] They were loosely inspired by neurons but work quite differently
- They are detailed simulations of how real neurons fire
- They copy the wiring of a particular brain region
- Their design came from statistics, not from ideas about the brain
shuffle:: true

#### Question: Choice
id:: efb95fb3-c406-4682-ba4b-13602c8287cb
content:: What does "deep learning" mean?
options::
- [x] Machine learning with neural networks that have many layers
- Machine learning that runs on many computers at once
- Machine learning that grasps the deeper meaning of its data
- Machine learning that trains on very large datasets
shuffle:: true

#### Question: Choice
id:: 1000b796-212d-4807-a011-1e89f437ab38
content:: In a neural network that recognizes objects in photos, how do the early layers typically differ from the later ones?
options::
- [x] Early layers find simple patterns; later layers combine them into complex ones
- Early layers find whole objects; later layers pick out fine details
- Early and later layers find the same patterns at different sizes
- Early layers store the images; later layers attach labels to them
shuffle:: true

#### Question: Choice
id:: 41d3d59e-a40f-45b3-991e-d4c9504deb05
content:: Why is it hard to tell what a trained neural network will do just by inspecting it?
options::
- [x] Its behavior is set by billions of learned, unlabeled numbers
- Its code is too long for any one person to read
- It rewrites its own code each time it runs
- Its code is kept secret by the companies that make it
shuffle:: true

#### Question: Choice
id:: 5f9de8d1-1fb9-432c-8c40-496e548a2b34
content:: In the 2010s, neural networks overtook AI methods that relied on features hand-picked by experts. What advantage did neural networks have?
options::
- [x] They could learn useful features from data themselves
- They needed far less training data
- They were easier for people to interpret
- They ran on cheaper hardware
shuffle:: true

#### Question: Choice
id:: 58c0fdcb-2592-45ce-98fd-49e3a02ee4bb
content:: Was the idea of neural networks with several layers of units first proposed in the 2010s?
options::
- Yes
- [x] No

#### Question: Choice
id:: a6375e30-242b-4a1a-80ca-76f537580003
content:: Are large language models, such as the ones behind ChatGPT and Claude, a kind of neural network?
options::
- [x] Yes
- No

#### Question: Open
id:: 131b889f-9f94-412c-bfd6-bd6306afd870
content:: Neural networks were studied for decades before they became the leading approach in AI in the 2010s. Why did they take over only then?
assessment-instructions:: Score out of 100. 100 for: they need large amounts of data and computing power to work well, and by the 2010s both were available (internet-scale datasets, fast parallel chips such as GPUs), so at that scale they beat other methods. 50 if only data or only compute is named.

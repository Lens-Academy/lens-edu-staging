---
id: b13ccb6a-812f-4808-9be9-92d707c0b8bc
priority: low
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe about ten key AI developments, from AlexNet in 2012 to today's reasoning models, say what new ability each showed, and recognise that recent progress came largely from training with more compute.

## Requires

## Helpful first

## Why it matters
Arguments about AI risk often point to how quickly AI went from beating humans at Go to writing code and solving olympiad maths problems. Knowing these milestones lets you judge such claims of rapid progress, and seeing that more compute drove much of it helps you reason about where progress could go next.

## Lenses

## Tests
#### Question: Choice
id:: 0ac8c0e8-82d2-4a08-b303-51dc1e9f9965
content:: In 2012 the neural network AlexNet won the ImageNet image-recognition competition. Why is this seen as a milestone?
options::
- [x] Deep neural networks trained on GPUs clearly beat other methods
- It was the first computer to beat a world chess champion
- It was the first program to hold a convincing conversation
- It showed hand-designed image features beat learned ones
shuffle:: true

#### Question: Choice
id:: 3c8cf1af-5e7e-4879-9d6e-be9028a504b7
content:: In 2016 DeepMind's AlphaGo beat Go champion Lee Sedol. What was new about its successor, AlphaZero?
options::
- [x] It learned by playing against itself, without human game records
- It was the first program to beat a top human player at Go
- It relied on opening moves written by professional Go players
- It ran on a single laptop instead of large computer clusters
shuffle:: true

#### Question: Open
id:: 720e6d5c-89e0-4036-9bb7-ace782ece754
content:: DeepMind's AlphaZero became stronger than any human at chess within a day of training. What does the way it was trained suggest about whether AI ability is capped at human level?
assessment-instructions:: Score out of 100. 100: it learned from self-play with no human games, so human knowledge was not a ceiling; a system that can generate its own training signal can pass the best humans, and quickly. 50: says AI can exceed humans but doesn't connect this to training without human data. 0: says AI is limited to human level.

#### Question: Choice
id:: b32181e4-eb86-47aa-b2e0-283775db22b3
content:: The transformer, a neural network design published by Google researchers in 2017, became the basis of which systems?
options::
- [x] GPT models, ChatGPT and most other large language models
- AlphaGo and the other game-playing systems from DeepMind
- The Deep Blue computer that beat Kasparov at chess
- AlexNet and the early deep learning image classifiers
shuffle:: true

#### Question: Choice
id:: ce70c018-e0f3-4ec3-8a5d-2ca7e3332779
content:: OpenAI's GPT-3 (2020) was a much larger version of its earlier GPT language models. What surprised many researchers about it?
options::
- [x] It could do many new tasks from a few examples in the prompt
- It could beat professional players at Go and chess
- It recognised objects in photos better than humans did
- It needed far less compute to train than earlier models
shuffle:: true

#### Question: Choice
id:: dd9864aa-6338-4148-b5f9-b3e7f09c7625
content:: AlphaFold 2 (2020), whose creators at DeepMind shared the 2024 Nobel Prize in Chemistry, solved which long-standing scientific problem?
options::
- [x] Predicting a protein's 3D shape from its amino acid sequence
- Reading the full DNA sequence of a single human cell
- Designing new antibiotics that need no lab testing
- Simulating every chemical reaction inside a living cell
shuffle:: true

#### Question: FillBlank
id:: ef881bdc-2cf8-48c6-ba02-77ff73f787c6
content:: OpenAI released ChatGPT to the public in November {{2022}}.

#### Question: Choice
id:: 875b6993-1ae2-47ff-af38-8b4856d83caf
content:: OpenAI built ChatGPT on top of its GPT-3.5 language model. What was the main extra step that turned the model into a useful chat assistant?
options::
- [x] Fine-tuning it with human feedback to follow instructions helpfully
- Replacing its transformer design with a new kind of network
- Training it from scratch only on transcripts of conversations
- Connecting it to a search engine that supplied every answer
shuffle:: true

#### Question: Open
id:: d70989df-8b08-41fc-943f-643cd0293381
content:: Why did ChatGPT's release do more to make AI a mainstream public and political issue than earlier, technically important advances such as GPT-3?
assessment-instructions:: Score out of 100. 100: it put a capable, free, easy-to-use system directly in front of millions of ordinary people, who saw its abilities for themselves (it gained users faster than earlier consumer apps). 50: a vaguer answer about it being easier to use or more popular. Mentioning the race between AI companies it set off is fine but not needed.

#### Question: Choice
id:: da16e6f6-8c1d-4416-b662-704c0505c3c2
content:: How do reasoning models, such as OpenAI's o1 (2024) and DeepSeek-R1 (2025), mainly differ from earlier chatbots?
options::
- [x] They are trained to work through a long chain of thought before answering
- They look up answers in a large database of already-solved problems
- They use hand-written logic rules in place of a neural network
- They are small models designed to run offline on phones
shuffle:: true

#### Question: Choice
id:: dc476734-55ea-4317-ad33-986a8db3799f
content:: In July 2025, experimental AI models from Google DeepMind and OpenAI attempted the International Mathematical Olympiad, writing their proofs in ordinary language. What did they achieve?
options::
- [x] Gold-medal-level scores, solving five of the six problems
- Bronze-medal-level scores, solving two of the six problems
- Perfect scores, beating every human contestant
- Failing scores, with no problem fully solved
shuffle:: true

#### Question: Choice
id:: 1db91316-712e-44d2-903a-712536796441
content:: Which factor did the most to drive AI progress from 2012 to the mid-2020s?
options::
- [x] Training general learning methods with far more compute and data
- Programming more expert knowledge into AI systems by hand
- Replacing neural networks with logic-based reasoning systems
- Moving AI training from specialised chips to ordinary CPUs
shuffle:: true

#### Question: Open
id:: 4a5688d7-6000-4885-9745-48ef65103270
content:: Pick two AI milestones from 2016 or later and say, for each, what new ability it showed.
assessment-instructions:: Score out of 100. 50 for each milestone correctly matched to its ability, such as: AlphaGo (beat a top Go champion), AlphaZero (superhuman play learned without human data), GPT-3 (new tasks from a few examples), AlphaFold (protein structure prediction), ChatGPT (helpful general-purpose chat), reasoning models (hard maths and coding by thinking longer), 2025 IMO gold-level maths.

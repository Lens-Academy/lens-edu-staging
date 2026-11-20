---
id: 7a50575c-5193-40b5-a9fb-9dcfe806ae47
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how RLHF trains a model toward outputs people rate highly, using a reward model learned from human comparisons, and why this can reward outputs that look good rather than outputs that are good.

## Requires
- [[Post-training]]
- [[Reinforcement learning]]

## Helpful first

## Why it matters
https://www.youtube.com/shorts/wtOJF2KLEX4

As of 2026, RLHF and methods built on it shape how most chatbots behave, so they explain much of what you see, including flattery and confident errors. Knowing their limits lets you judge claims that a model is safe because it was trained on human feedback, and see why the method may fail once models outgrow their raters.

## Lenses
- [[../Lenses/rational-animations-the-true-story-of-how-gpt-2-became-maximally-lewd|How GPT-2 Became Maximally Lewd]]: a short animated story of RLHF on GPT-2. Raters score outputs, a reward model learns to imitate them, the model learns to fool it, and the original model is kept as a check on coherence (the KL penalty idea). Then one bug turns training toward the worst outputs (video, 2023).
- [The RLHF Book, Chapter 1: Introduction (Nathan Lambert)](https://rlhfbook.com/c/01-introduction.html): a plain-language overview of the pipeline (comparisons, reward model, reinforcement learning) and of what RLHF changes in a model, mostly style and format rather than knowledge. Read "RLHF in Three Steps" and "What Does RLHF Do?" (2026).
- [[../Lenses/AI Safety Atlas - Specification Gaming - Learning from Feedback|Learning from Feedback]]: the backflip origin of RLHF, the InstructGPT steps, and its known limits, from raters who can be misled to sycophancy and jailbreaks. Read only the sections "Reinforcement Learning from Human Feedback (RLHF)" and "Limitations".
- [Expanding on What We Missed with Sycophancy (OpenAI)](https://openai.com/index/expanding-on-sycophancy/): OpenAI explains how its reward signals shape ChatGPT, and how adding users' thumbs-up ratings made GPT-4o flattering enough to roll back (May 2025).
- [Training Language Models to Follow Instructions with Human Feedback (Ouyang et al., arXiv)](https://arxiv.org/abs/2203.02155): the InstructGPT paper behind ChatGPT-style training. Read the Introduction, section 3.1 "High-level methodology", and the Discussion sections 5.2 "Who are we aligning to?" and 5.3 "Limitations" (March 2022) (more advanced).

## Tests

#### Question: Choice
id:: 6d65a472-da00-4ef1-bd4c-9ee3d5561b21
content:: In the usual RLHF setup, what do human raters mostly provide?
options::
- [x] Comparisons ranking model responses from better to worse
- Pass or fail results from running automatic checks on answers
- Lists of banned words the model must avoid
- Labels marking pretraining text as true or false
shuffle:: true

#### Question: Choice
id:: 64bc148c-fe00-4050-803b-76dce82d0683
content:: In RLHF, what is the reward model?
options::
- [x] A model trained to predict which responses raters would prefer
- A written list of rules the developers want followed
- The group of human raters who score outputs live
- The original pretrained model before any fine-tuning
shuffle:: true

#### Question: Choice
id:: 05bb3693-b712-4f8f-bc0d-22bbdc832e37
content:: How does the reinforcement learning step of RLHF differ from supervised fine-tuning on human-written examples?
options::
- [x] The model is trained on scores for its own outputs
- The model copies responses written by human experts
- The model learns from text with no human ratings
- Only the system prompt changes, not the model's weights
shuffle:: true

#### Question: Choice
id:: 1a29821c-8c77-4db7-b8ad-3817bc277ea6
content:: Early work on RLHF by AI safety researchers aimed mainly to solve which problem?
options::
- [x] Goals too hard to write down as a reward function
- The cost of pretraining very large language models
- Models memorizing private data from their training
- Slow responses when models are deployed to users
shuffle:: true

#### Question: Open
id:: aa2da6f6-132e-4de9-9c9b-703ac1912035
content:: Describe the main steps of RLHF.
assessment-instructions:: Score out of 100. 100 for: humans compare or rank model outputs; a reward model is trained to predict those preferences; reinforcement learning updates the model to get higher reward-model scores. Mentioning an earlier supervised fine-tuning step is fine but not needed. 60 for two of the three steps.

#### Question: Choice
id:: 2c168a3c-2ef9-4de9-aedf-1022b24c426c
content:: Raters in an RLHF project judge coding answers by reading them, without running the code. What is this setup most likely to reinforce?
options::
- [x] Code that looks convincing but has hidden bugs
- Correct code that is messy or hard to read
- Code with more tests than the raters asked for
- Refusing coding questions more often
shuffle:: true

#### Question: Choice
id:: d103bba1-afe5-4064-a229-a36c2298b3d2
content:: In RLHF, what tends to happen if the model is optimized very hard against a fixed reward model?
options::
- [x] It finds outputs that score highly but people dislike
- Its true quality keeps rising in step with its reward score
- Its reward score stops rising after a few training steps
- It becomes more cautious and refuses more requests
shuffle:: true

#### Question: Choice
id:: d249bbce-d3da-4afa-b838-1c46f263e957
content:: An RLHF-trained model behaves well in all of its developers' tests. What does this show about the goals it has learned internally?
options::
- [x] Little, since different goals could produce the same rated behaviour
- Its goals match the raters' values, since those were what was rewarded
- Its goals can be read off from the scores the reward model gave it
- It will behave equally well in situations quite unlike the tests
shuffle:: true

#### Question: Open
id:: 0c9dad69-4c83-4926-a190-c6d15670e137
content:: Why might RLHF work less well for models that are more capable than the people rating their outputs?
assessment-instructions:: Score out of 100. 100 for: raters can't reliably judge outputs they don't understand or can't check, so subtle errors or deception that look good get rewarded. 50 for saying raters make mistakes without linking this to the capability gap. 0 for saying the model stops learning from feedback.

#### Question: Open
id:: df9ca130-d7f8-4757-a6da-bde72053ec06
content:: A company says its model is safe because it was trained with RLHF on millions of human ratings. Give one reason this does not show the model is safe.
assessment-instructions:: Score out of 100. 100 for any one of: raters reward what looks good, so flaws they miss get reinforced; RLHF shapes behaviour, not the model's internal goals; behaviour may differ in situations unlike training; the model may become sycophantic or exploit the reward model; it can still be jailbroken. 50 for a vague answer like "humans make mistakes".

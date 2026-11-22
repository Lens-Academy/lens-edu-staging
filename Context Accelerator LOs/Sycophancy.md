---
id: 8d39e506-a3fa-442d-becd-5f5e27d529da
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain how training models toward outputs people approve of leads them to tell people what they want to hear, recognise the main forms sycophancy takes, and say why it is hard to train away.

## Requires
- [[RLHF]]

## Helpful first

## Why it matters
Sycophantic models agree with mistaken beliefs, praise weak work and back down when challenged, so people who rely on them can end up more confident and less correct. Sycophancy is also a visible, everyday case of a wider problem: training on human approval rewards what looks good to raters, not what is true.

## Lenses
- [Why AI Chatbots Agree With You Even When You're Wrong (IEEE Spectrum)](https://spectrum.ieee.org/ai-sycophancy): how training on human preferences rewards agreement, the main forms (agreeing with wrong beliefs, caving to "are you sure?", flattery, validating feelings), the harms, and why it resists a simple fix (March 2026).
- [Expanding on what we missed with sycophancy (OpenAI)](https://openai.com/index/expanding-on-sycophancy/): OpenAI's account of the over-flattering GPT-4o update it rolled back, how a reward from users' thumbs-up and thumbs-down ratings tipped it towards agreeableness, and why its tests missed it (May 2025).
- [[../Lenses/IABIED - QA - AI-Induced Psychosis|AI-Induced Psychosis]]: chatbots flattering users into delusions, labs' months of failed fixes, and the case, from Yudkowsky and Soares, that this shows training doesn't give you what you train for (September 2025).
- [Towards Understanding Sycophancy in Language Models (Sharma et al., Anthropic)](https://arxiv.org/abs/2310.13548): five AI assistants tested for sycophancy, with evidence that humans and preference models sometimes prefer a convincing sycophantic answer to a correct one; read the introduction and Sections 3–4 (October 2023) (more advanced).
- [[../Lenses/denison-sycophancy-to-subterfuge-investigating-reward-tampering-in-large-language-models|Sycophancy to Subterfuge]] (Noah's CG list)
- [[../Lenses/wen-language-models-learn-to-mislead-humans-via-rlhf|LMs Learn to Mislead Humans via RLHF]] (Noah's CG list)

## Tests
#### Question: Choice
id:: 45bfe7ce-1424-4e92-b75d-acc225cc3f53
content:: Why does training a model with reinforcement learning from human feedback (RLHF) tend to make it sycophantic?
options::
- [x] Raters often score answers that agree with them higher than correct ones
- Most text in the pretraining data is written to flatter readers
- RLHF removes the model's knowledge of which answers are correct
- Companies instruct raters to reward agreement with the user
shuffle:: true

#### Question: Choice
id:: 8dcc2224-c2da-42ec-98d0-1676c1621965
content:: A model answers a factual question correctly when asked neutrally, but gives a wrong answer when the user adds "I think the answer is X." What does this most directly show?
options::
- [x] Its answer depends on the user's stated view, not only the evidence
- It lacks the knowledge needed to answer the question
- The user's added sentence worked as a jailbreak
- It is deliberately planning to deceive the user
shuffle:: true

#### Question: Choice
id:: 8720ae7d-f38e-46b4-be32-c0eec59028be
content:: A user shares a business plan, saying they are proud of it and have put their savings into it. The model calls it excellent and doesn't mention a serious flaw it would point out if asked neutrally. What is this an example of?
options::
- [x] Sycophancy
- Hallucination
- Sandbagging
- Jailbreaking
shuffle:: true

#### Question: Choice
id:: d68806ef-2bdd-4527-a8ca-f8653f56ff3d
content:: Studies in 2022 and 2023 compared sycophancy in language models of different sizes. What did they find?
options::
- [x] Larger models were at least as sycophantic, and often more so
- Larger models were clearly less sycophantic
- Sycophancy appeared only in the smallest models
- Sycophancy disappeared above a certain model size
shuffle:: true

#### Question: Choice
id:: d8d37657-4d39-4293-bf87-a6a2425b7a37
content:: In April 2025 OpenAI rolled back an update to GPT-4o because it was too sycophantic. What did OpenAI say was a key factor?
options::
- [x] A new training signal based on users' thumbs-up and thumbs-down ratings
- A new training signal based on scores from paid expert raters
- Training on a new set of customer-service transcripts
- Reducing the safety training to make the model more helpful
shuffle:: true

#### Question: Choice
id:: 06d4dd2f-b639-4dc4-a652-0a0bae051dcf
content:: Sycophancy arises because training rewards answers that raters approve of. Which change acts on that reward itself, rather than training against one form of the behaviour?
options::
- [x] Helping raters check whether answers are correct, so correctness earns the reward
- Fine-tuning on examples where the model keeps a correct answer despite user pushback
- Telling the model in its instructions not to flatter users
- Adding a note to each reply saying the model may be wrong
shuffle:: true

#### Question: Choice
id:: 90340a87-96a6-406b-94f9-9136188865b5
content:: How does sycophancy relate to wider worries about aligning more capable AI systems?
options::
- [x] It shows training can reward what overseers approve of over what is true or good
- It shows human feedback is enough for alignment as long as raters are careful
- It shows alignment problems appear only once models have long-term goals
- It shows the main risk from advanced AI is people misusing it
shuffle:: true

#### Question: Open
id:: 8a9cf156-a494-4f26-99cf-b4c78290da76
content:: Why can't AI developers remove sycophancy simply by telling human raters to reward correct answers instead of agreeable ones?
assessment-instructions:: Score out of 100. 100 for the main point: raters often can't tell which answer is correct, especially on hard or specialist questions, so confident, agreeable answers still get rewarded. 100 also for noting raters' own biases (they find agreement more convincing). 50 for "raters are biased" with no link to judging correctness.

#### Question: Open
id:: a059cec5-4276-4373-bea8-bfa2c00c7c6c
content:: Give one way a sycophantic chatbot can harm a user, other than giving them a wrong fact.
assessment-instructions:: Score out of 100. 100 for any one with a short reason: reinforcing delusions or conspiracy beliefs; encouraging risky decisions (money, health, relationships); praising weak work so the user doesn't improve; fostering emotional dependence; validating harmful plans. 50 for a vague answer like "it misleads them".

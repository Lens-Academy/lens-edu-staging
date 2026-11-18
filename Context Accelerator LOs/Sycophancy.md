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
- It was trained without any human feedback
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
content:: In studies of language models from 2022 and 2023, did larger models show less sycophancy than smaller ones?
options::
- [x] No
- Yes

#### Question: Choice
id:: d8d37657-4d39-4293-bf87-a6a2425b7a37
content:: In April 2025 OpenAI rolled back an update to GPT-4o because it was too sycophantic. What did OpenAI say was a main cause?
options::
- [x] Giving more weight to users' thumbs-up and thumbs-down ratings
- A bug that deleted the model's system prompt
- Training on a new set of customer-service transcripts
- Shrinking the model to cut running costs
shuffle:: true

#### Question: Choice
id:: 24ffe222-852b-443d-b7d7-c3ea8559aa86
content:: Which of these training changes targets a cause of sycophancy rather than its symptoms?
options::
- [x] Training on examples where the model keeps a correct answer despite user pushback
- Adding a note to each reply saying the model may be wrong
- Making the model's replies shorter so there is less room for flattery
- Raising the sampling temperature so answers vary more
shuffle:: true

#### Question: Choice
id:: 90340a87-96a6-406b-94f9-9136188865b5
content:: How does sycophancy relate to wider worries about aligning more capable AI systems?
options::
- [x] It shows training can reward what overseers approve of over what is good
- It shows that current models deliberately plan to deceive their users
- It shows that models have developed their own long-term goals
- It shows that models cannot learn anything useful from human feedback
shuffle:: true

#### Question: Open
id:: 8a9cf156-a494-4f26-99cf-b4c78290da76
content:: Why can't AI developers remove sycophancy simply by telling human raters to reward correct answers instead of agreeable ones?
assessment-instructions:: Score out of 100. 100 for the main point: raters often can't tell which answer is correct, especially on hard or specialist questions, so confident, agreeable answers still get rewarded. 100 also for noting raters' own biases (they find agreement more convincing). 50 for "raters are biased" with no link to judging correctness.

#### Question: Open
id:: a059cec5-4276-4373-bea8-bfa2c00c7c6c
content:: Give one way a sycophantic chatbot can harm a user, other than giving them a wrong fact.
assessment-instructions:: Score out of 100. 100 for any one with a short reason: reinforcing delusions or conspiracy beliefs; encouraging risky decisions (money, health, relationships); praising weak work so the user doesn't improve; fostering emotional dependence; validating harmful plans. 50 for a vague answer like "it misleads them".

#### Question: FillBlank
id:: 804ec17f-0952-4c30-b9f5-7060d68641e4
content:: When an AI model tells users what they want to hear instead of what is accurate, this behaviour is called {{sycophancy|sycophantic behaviour|sycophantic behavior}}.

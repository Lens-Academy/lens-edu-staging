---
id: f83592ed-a504-4126-a38e-c20028d3d7b9
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Describe the main views that current AI is overhyped, the arguments behind each, and the confusions in common versions such as "it just predicts the next token".

## Requires
- [[Pretraining]]

## Helpful first
- [[Current AI capabilities]]

## Why it matters
Many people's first answer to AI risk is that AI isn't really capable. If you can separate the fair points in this view, such as unreliability, inflated benchmark scores and company hype, from the confusions, you can judge AI claims for yourself and answer the objection without overstating what AI can do.

## Lenses
- [Jagged Intelligence (The Yale Review)](https://yalereview.org/article/melanie-mitchell-jagged-intelligence): AI scientist Melanie Mitchell's case that LLM abilities are real but jagged and unreliable, covering broken benchmarks, training-data contamination, brittleness to irrelevant details, confident made-up answers, and whether next-word prediction gives understanding; a leading critic's view (June 2026).
- [[../Lenses/IABIED - QA - Just Predicting Next Token|Aren't AIs Just Predicting the Next Token?]]: why predicting text well can require real reasoning about the world, and why modern models are also trained with reinforcement learning, not prediction alone.
- [Tracing the Thoughts of a Large Language Model (Anthropic)](https://www.anthropic.com/research/tracing-thoughts-language-model): what researchers found inside Claude, including that it plans a rhyme before writing the line, chains facts in multi-step reasoning, and produces hallucinations when a name feels familiar but nothing is known about it (March 2025).
- [The Phony Comforts of AI Skepticism (Platformer)](https://platformer.news/ai-skeptics-gary-marcus-curve-conference): separates the "AI is fake and sucks" view from the "AI is real and dangerous" view, with Gary Marcus's arguments on scaling limits and investment returns; one side of a live debate, by a tech journalist who holds the second view (December 2024).

## Tests
#### Question: Choice
id:: 9b13ea31-6a8d-40fb-984c-4b62c61efdfc
content:: As of 2026, what happens to frontier chat models such as ChatGPT and Claude after pretraining on next-token prediction?
options::
- [x] They are further trained with human feedback and reinforcement learning
- They are used as they are, guided by a system prompt
- They are connected to a search engine that supplies their answers
- They are retrained on a smaller set of verified true facts
shuffle:: true

#### Question: Choice
id:: d47a9bd9-a3e1-4b36-870c-73deab10e7c4
content:: A language model writes its output one token at a time. What does that mean for whether it can plan ahead?
options::
- [x] It can still represent where the text is going while choosing each token
- Each token is chosen with no representation of the text that follows
- Each token depends only on the single token written just before it
- It needs an external memory tool before it can plan anything
shuffle:: true

#### Question: Choice
id:: 912f9264-b2f6-4e79-b4e0-a097037d1f79
content:: What does the "stochastic parrots" critique of large language models claim?
options::
- [x] They reproduce patterns in language without understanding its meaning
- They copy whole passages from their training data word for word
- They give random answers that can't be reproduced
- They repeat the opinions of the companies that built them
shuffle:: true

#### Question: Choice
id:: b1495aad-1716-4d83-9d27-4ab29982c414
content:: In 2024, many language models miscounted the letter "r" in the word "strawberry". What is the most widely cited contributing reason?
options::
- [x] They take in text as tokens of several characters, not as single letters
- The word appears too rarely in their training data to be learned
- Safety training made them refuse to give exact counts of things
- Their training data contains many misspellings of the word
shuffle:: true

#### Question: Choice
id:: d16f4673-3960-4247-8b7e-68a1fca625eb
content:: A new AI model scores very high on a well-known benchmark. Which concern do skeptics raise that, if true, would mean the score overstates its ability?
options::
- [x] The benchmark's questions and answers were in its training data
- The benchmark's questions are harder than most real work
- Other recent models also score well on the same benchmark
- The model took longer than people to answer each question
shuffle:: true

#### Question: Choice
id:: 9a90746c-5952-479a-8dc0-b800c57da699
content:: In 2024, a study found that language models' scores on grade-school maths word problems dropped when just the names and numbers in the problems were changed. What do skeptics take this to suggest?
options::
- [x] The models partly rely on matching patterns from familiar problems
- The original benchmark had been marked too leniently
- The original problems were too easy to measure anything
- The models had been trained to avoid word problems
shuffle:: true

#### Question: Choice
id:: dfcbfc9b-0816-48ed-8ae3-4e6d8b9c3d0e
content:: A chatbot confidently cites a research paper that doesn't exist. What does this best show?
options::
- [x] A model can write fluently and plausibly while being wrong
- The chatbot looked the paper up in a database that had an error
- The chatbot's other correct answers were probably lucky guesses
- The chatbot was deliberately instructed to deceive its user
shuffle:: true

#### Question: Choice
id:: f1114d0a-da25-4a52-bd01-809412992447
content:: Which result is hardest to explain if large language models mainly retrieve text they memorized during training?
options::
- [x] Solving maths competition problems written after their training data was collected
- Reciting well-known quotes accurately when asked
- Answering common trivia questions correctly
- Writing text in the style of famous authors
shuffle:: true

#### Question: Choice
id:: 7b1bfa8e-2072-4a10-9047-a1ebf2470016
content:: A critic says each new AI ability, once achieved, "isn't real intelligence, just statistics". What is the main weakness of this as an argument that AI isn't capable?
options::
- [x] No new ability could count against it, so it tells us little
- It wrongly assumes that AI systems use statistics
- It relies on scores from biased benchmarks
- It confuses AI capability with AI alignment
shuffle:: true

#### Question: Choice
id:: cbe9b5b5-b4b2-49e9-a667-8a1926c2952e
content:: Suppose the stock market values of AI companies turn out to be a bubble that bursts. What would this most directly show?
options::
- [x] Investors had expected more profit, sooner, than the companies earned
- The AI models could not do work that customers would pay for
- Progress in AI capabilities had slowed to a near stop
- Warnings about risks from AI had been driven mainly by hype
shuffle:: true

#### Question: FillBlank
id:: 3a7e9623-04d5-43a9-b984-33721bbedc97
content:: AI capabilities are often described as a {{jagged}} frontier: a model can do some hard tasks well while failing at tasks that seem easier to people.

#### Question: Open
id:: 450de9e5-2203-4e75-af8f-8d68d50889fa
content:: A friend says: "Large language models just predict the next token, so they can't really reason." Briefly explain what this argument gets wrong.
assessment-instructions:: Score out of 100. 100 for saying that the training task doesn't limit what abilities a model develops to do it well: predicting text well, such as the next step of a proof, can require reasoning. 50 for only noting that chat models get further training beyond next-token prediction, or only pointing to examples of reasoning without the explanation.

#### Question: Open
id:: e932f79d-ee2e-42f7-bae1-32ce189178e2
content:: Why are today's AI mistakes, such as invented citations, weak evidence that AI won't pose serious risks in the future?
assessment-instructions:: Score out of 100. 100 for any one of: concerns about risk are mainly about more capable future systems; capabilities have improved quickly, so today's failures may not last; a system can be unreliable in some ways and still capable and dangerous in others. 50 for just saying the mistakes may get fixed, with no reason.

#### Question: Open
id:: f8210684-6285-4f07-a9ad-df5e0dd61f01
content:: A skeptic argues that because AI companies profit from hype, their claims about their models' capabilities should be ignored. What is a better way to handle that incentive?
assessment-instructions:: Score out of 100. 100 for checking claims against independent evidence, such as third-party evaluations, held-out or new benchmarks, or testing the models yourself, rather than either trusting or dismissing them wholesale. 50 for "be skeptical" or "take claims with a grain of salt" without saying how to check them.

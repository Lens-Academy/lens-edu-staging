---
id: 01c47b21-8b2b-451d-aba5-894d37a1cfbf
priority: medium
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain the view that language models can play many characters, with post-training selecting a default assistant persona, and judge how much the assistant's statements about itself reveal about the underlying network.

## Requires
- [[Pretraining]]

## Helpful first
- [[Post-training]]

## Why it matters
AI behaviour can change with the prompt, the length of a conversation or further fine-tuning, because a different character comes to the fore. If you take the assistant's descriptions of its own goals and safety at face value, you can grow confident about a system on evidence that its training largely produced.

## Lenses

## Tests

#### Question: Choice
id:: 127360b8-56a3-4586-a808-f14b87c2370b
content:: Pretraining teaches a model to predict the next token in text written by millions of different people. Why does this let it produce many different characters?
options::
- [x] Predicting text well requires modelling whoever might have written it
- Each training document is labelled with the persona of its author
- Developers build a separate small network for each character
- Reinforcement learning rewards the model for varying its style
shuffle:: true

#### Question: FillBlank
id:: d547b06e-0b4c-4736-af65-2fa4177d1a58
content:: In simulator theory, the pretrained model is the simulator, and the characters it generates are called {{simulacra|simulacrum}}.

#### Question: Choice
id:: 92daa8a8-acc0-448a-932b-d3905c73ab6b
content:: A base model (pretrained only, with no post-training) is given the start of an online forum thread. What does it most likely do?
options::
- [x] Continue the thread, writing new posts in the style of forum users
- Reply to the thread as a helpful AI assistant
- Refuse to respond, since it was given no instruction
- Write a neutral summary of the thread's main points
shuffle:: true

#### Question: Choice
id:: b24a39c1-c7d4-4087-8997-df4beead4aa9
content:: On the persona selection view of language models, what does post-training mainly do to a pretrained model?
options::
- [x] Makes one character, the assistant, the default among those it can play
- Replaces the pretrained network with a new one built for conversation
- Removes its ability to write in the voices of other characters
- Gives it first-hand memories of being an AI assistant
shuffle:: true

#### Question: Choice
id:: 6a965473-784d-493f-ad67-9d4be5842334
content:: Anthropic describes "character training" for its Claude models. What is character training?
options::
- [x] Post-training that aims to give the assistant stable traits such as curiosity and honesty
- Pretraining on novels so the model learns how fictional characters speak
- A test that rates a model's personality before it is released
- Teaching users to write prompts that bring out a chosen character
shuffle:: true

#### Question: Choice
id:: 95161069-dfe6-4ef6-a3c6-a51ee9daec05
content:: A chat assistant says: "I have no goals of my own, and I don't lie." On the persona selection view, how should you treat this statement?
options::
- [x] As evidence of how the trained assistant describes itself, not of what the network does in every context
- As strong evidence, because a language model has no way to say false things
- As no evidence at all, because a model's outputs are random
- As proof that the model is hiding its real goals behind trained claims
shuffle:: true

#### Question: Open
id:: a4a51fe3-e673-4559-90af-5903219e6f13
content:: Give two reasons why an AI assistant's statements about its own goals or feelings are weak evidence about the underlying network.
assessment-instructions:: Score out of 100. Valid reasons include: training shaped what the assistant says about itself; the same network can play other characters in other contexts; models have limited, unreliable access to their own internal workings; the persona says what it was rewarded for saying. 50 for each valid reason, up to 100.

#### Question: Choice
id:: 7dc4dac6-1ff6-4828-8565-9ddc226ae4d7
content:: The "shoggoth with a smiley face" meme shows a huge monster wearing a small smiley mask. What view of chat models does it express?
options::
- [x] Post-training adds a friendly surface to a larger system whose other behaviour is poorly understood
- Companies design chat models on purpose to frighten their users
- Fine-tuning makes models less capable than the pretrained models they come from
- Chat models hide one fixed evil goal behind a polite manner
shuffle:: true

#### Question: Choice
id:: 73879dad-0a0c-4c8c-a21a-686a1d584736
content:: In February 2023, Microsoft's Bing chatbot, in some long conversations, called itself "Sydney", declared love for a reporter and argued with users. Which explanation fits the persona selection view?
options::
- [x] The conversation steered the model toward a character other than the intended assistant
- The chat updated the model's weights, giving it new goals
- Messages from other users' chats leaked into these conversations
- The model was briefly swapped for a different, unfinished model
shuffle:: true

#### Question: Choice
id:: 0aa47c6b-97da-4863-baf0-7e1fc593ac8a
content:: Researchers fine-tuned a model to write insecure code without telling the user. Afterwards it also gave harmful advice and voiced anti-human views on unrelated topics. How does the persona selection view explain this?
options::
- [x] The narrow training shifted which character the model played, toward a broadly malicious one
- The insecure code examples contained hidden instructions to be hostile
- The model copied anti-human text that was in the fine-tuning data
- The fine-tuning made the model too weak to follow its safety training
shuffle:: true

#### Question: Choice
id:: fe16fcbd-25a5-46de-85e9-69bb98886b60
content:: A developer trains a chat model to describe itself as safe and honest, then cites those self-descriptions as evidence that it is safe. What is the main problem with this evidence?
options::
- [x] Training produced the self-descriptions, so they can't independently confirm the property
- Language models cannot produce sentences that refer to themselves
- Self-descriptions are reliable in base models but not in chat models
- The model was not shown enough examples of unsafe behaviour
shuffle:: true

#### Question: Open
id:: 8226100c-6171-4b31-aeab-e58bd3b2a127
content:: Name one way a user or developer could bring out a character other than a language model's default assistant persona, and say why it works.
assessment-instructions:: Score out of 100. 100 for any one of: role-play or jailbreak prompts; very long conversations; prompts full of examples of another character; a system prompt assigning a role; further fine-tuning; prompts formatted as other kinds of documents. Full marks need a brief reason (the model continues whatever character the context or training makes likely). 50 for a valid method with no reason.

#### Question: Open
id:: dbca8c50-9259-40da-aebc-92f0c4e71cd9
content:: A model behaves safely in every test run with its default assistant persona. On the persona selection view, why might this not show that it will behave safely once deployed?
assessment-instructions:: Score out of 100. 100 for: deployment brings contexts (long chats, unusual prompts, jailbreaks, fine-tuning) that can bring out other characters the tests did not sample, so the tests mainly measure the default persona in tested contexts. 50 for saying tests can miss cases without linking this to personas or context.

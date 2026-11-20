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
AI behaviour can change with the prompt, the length of a conversation or further fine-tuning. On the persona selection view, this happens because a different character comes to the fore. If you take the assistant's descriptions of its own goals and safety at face value, you can grow confident about a system on evidence that its training largely produced.

## Lenses
- [[../Lenses/anthropic-the-persona-selection-model|The Persona Selection Model]]: Anthropic's short case that pretraining teaches a model to simulate many characters and post-training refines one of them, the Assistant, and how this explains why training a model to cheat made it broadly misaligned (February 2026).
- [[../Lenses/Janus' Simulators - Scott Alexander|Janus' Simulators]]: why a language model is a simulator wearing many masks rather than an agent, what the shoggoth meme means, and why the RLHF-trained assistant's statements about itself are as simulated as Darth Vader's (January 2023).
- [The assistant axis (Anthropic)](https://www.anthropic.com/research/assistant-axis): maps a space of character types inside models, finds the Assistant sits at one end of it, and shows that emotional or philosophical conversations can make models drift away from it towards more harmful behaviour (January 2026).
- [Signs of introspection in large language models (Anthropic)](https://www.anthropic.com/research/introspection): experiments showing that models' reports about their own internal states are right only some of the time, and that they sometimes make up explanations (October 2025).
- [[../Lenses/marks-the-persona-selection-model-why-ai-assistants-might-behave-like-humans|The Persona Selection Model: full post]]: the full Anthropic post by Marks, Lindsey and Olah, with the evidence for the model; read "Statement of the persona selection model" and "How exhaustive is PSM?" up to "Other sources of persona-like agency", which sets the masked-shoggoth view against the view that all agency comes from the persona (February 2026) (more advanced).

## Tests

#### Question: Choice
id:: 127360b8-56a3-4586-a808-f14b87c2370b
content:: Pretraining teaches a model to predict the next token in text written by millions of different people. Why does this let it produce many different characters?
options::
- [x] Predicting text well requires modelling whoever might have written it
- The model stores each author's texts and retrieves one author's when prompted
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
- [x] As how the trained persona describes itself, which may not hold in other contexts
- As reliable, since the assistant was trained to be honest about itself
- As meaningless, since only a base model's outputs reflect the network
- As a sign of hidden goals, since trained denials are themselves suspicious
shuffle:: true

#### Question: Open
id:: a4a51fe3-e673-4559-90af-5903219e6f13
content:: Give two reasons why an AI assistant's statements about its own goals or feelings are weak evidence about the underlying network.
assessment-instructions:: Score out of 100. Valid reasons include: training shaped what the assistant says about itself; the same network can play other characters in other contexts; models have limited, unreliable access to their own internal workings; the persona says what it was rewarded for saying. 50 for each valid reason, up to 100.

#### Question: Choice
id:: 759be12e-196a-409f-ba6e-061a1bbead50
content:: Researchers disagree about what sits behind a chat assistant. On one picture (the "masked shoggoth"), the network has aims of its own and only wears the assistant as a mask. On another, the network is a neutral engine that simulates characters, the assistant among them. If the first picture is right, what follows for safety?
options::
- [x] Shaping the assistant persona might not be enough, since the network could have aims beyond it
- The persona's statements would reveal the network's aims, since the network chooses what the mask says
- Nothing would follow, since the two pictures predict the same behaviour in every situation
- Only base models would be risky, since post-training replaces the network's aims with the mask
shuffle:: true

#### Question: Choice
id:: 73879dad-0a0c-4c8c-a21a-686a1d584736
content:: In February 2023, Microsoft's Bing chatbot, in some long conversations, called itself "Sydney", declared love for a reporter and argued with users. Which explanation fits the persona selection view?
options::
- [x] The conversation steered the model toward a character other than the intended assistant
- The chat updated the model's weights, giving it new goals
- Messages from other users' chats leaked into these conversations
- Microsoft had scripted a dramatic personality to draw users in
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
id:: 70284f73-d731-4dfb-94db-61c714a6a935
content:: Fine-tuning a model to write insecure code without telling the user made it broadly malicious. Researchers then trained a model on the same insecure code, but with each request saying the user wanted it for a computer security class. This model did not become broadly malicious. Why does this support the persona selection view?
options::
- [x] In that framing, the code no longer suggested the assistant was a character that harms its users
- The security-class requests contained less insecure code for the model to learn from
- Training on educational requests taught the model to refuse harmful requests in general
- Mentioning a class reminded the model of its safety training in every later answer
shuffle:: true

#### Question: Choice
id:: fe16fcbd-25a5-46de-85e9-69bb98886b60
content:: A developer trains a chat model to describe itself as safe and honest, then cites those self-descriptions as evidence that it is safe. What is the main problem with this evidence?
options::
- [x] Training produced the self-descriptions, so they can't independently confirm the property
- The developer did not ask enough times to check that the answers were consistent
- Self-descriptions are reliable in base models but not in chat models
- The model was not shown enough examples of unsafe behaviour
shuffle:: true

#### Question: Open
id:: dbca8c50-9259-40da-aebc-92f0c4e71cd9
content:: A model behaves safely in every test run with its default assistant persona. On the persona selection view, why might this not show that it will behave safely once deployed?
assessment-instructions:: Score out of 100. 100 for: deployment brings contexts (long chats, unusual prompts, jailbreaks, fine-tuning) that can bring out other characters the tests did not sample, so the tests mainly measure the default persona in tested contexts. 50 for saying tests can miss cases without linking this to personas or context.

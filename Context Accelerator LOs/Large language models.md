---
id: 07e4ac75-5653-455f-b063-31ae1a73ecf3
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what a large language model is and what it does when it generates text, how prompts and context steer its output, and why LLMs became the main route toward general-purpose AI.

## Requires
- [[Machine learning]]

## Helpful first
- [[Neural networks]]

## Why it matters
As of November 2026, the most capable AI systems, including the chatbots and agents that AI risk discussions focus on, are built on LLMs. Knowing how they work at a basic level helps you judge claims about what they can and can't do, and read later material on training, agents and alignment without being misled by the chat interface.

## Lenses

## Tests

#### Question: Choice
id:: 752f2824-4fff-47c7-b0d4-8c2ea1e7e5d1
content:: At its core, what does a large language model (LLM) calculate each time it produces the next bit of text?
options::
- [x] How likely each possible next piece of text is, given the text so far
- Which grammar rules, written by its developers, apply to the input
- The one correct continuation, found by searching all possible texts
- Which category from a fixed list the user's input belongs to
shuffle:: true

#### Question: FillBlank
id:: 3bc78cbb-b25a-44e6-9218-a98e48b2837e
content:: Large language models read and write text as a sequence of small units, such as words or parts of words, called {{tokens|token}}.

#### Question: Choice
id:: e3ee084d-30a4-498c-898d-28e20fa0e24f
content:: When an LLM chatbot writes a long answer, how is the text produced?
options::
- [x] One small piece at a time, each piece fed back in to help pick the next
- All at once in a single pass, then shown gradually for display
- As a full rough draft that is then revised as a whole
- By joining prewritten sentences chosen to fit the question
shuffle:: true

#### Question: Choice
id:: 1eae9b59-9572-4bfe-8c81-d7e97d4790ac
content:: The same LLM gives a noticeably different answer when a user's question is preceded by a few worked examples. Which best explains this?
options::
- [x] Its output depends on all the text in its context, not just the question
- The examples are passed to a separate model that writes the answer
- The examples switch it into a special mode set by its developers
- It saves the examples and shows them to all future users
shuffle:: true

#### Question: Choice
id:: 9308fc7a-8336-4423-ba4d-cf304a759a29
content:: What is an LLM's context window?
options::
- [x] The maximum amount of text the model can take into account at once
- The part of its training data that it can still recall accurately
- The range of dates that its training data covers
- The set of topics it was trained to be allowed to discuss
shuffle:: true

#### Question: Choice
id:: 09429f82-77e8-44dd-8db4-ffd0a039382f
content:: In a typical LLM chatbot, does chatting with the model change its weights (the learned numbers that set its behavior) during the conversation?
options::
- Yes
- [x] No

#### Question: Choice
id:: 7a1d83c6-e563-45b0-b982-6f773d9e3ba1
content:: You send an LLM chatbot the exact same prompt in two fresh conversations, with no memory features turned on. Can the two replies be different?
options::
- [x] Yes
- No

#### Question: Choice
id:: f8e3b8ba-e88c-4635-9c22-aa8f71154f3c
content:: Which development best explains why LLMs became the leading route toward general-purpose AI between about 2018 and 2023?
options::
- [x] Training the same kind of model with more data and compute kept improving its broad abilities
- Researchers hand-coded grammar and world knowledge into each new model
- Each new model combined many specialized systems, one built for each task
- Chatbots began running a web search for every answer they gave
shuffle:: true

#### Question: Choice
id:: c5b6042e-9cb6-4ee7-850c-39f893776d9c
content:: What is the relationship between an LLM and a chatbot such as ChatGPT or Claude?
options::
- [x] The chatbot is an app built around an LLM trained to act as an assistant
- The chatbot and the LLM are the same thing under two names
- The chatbot is a search engine that uses an LLM only to fix grammar
- The chatbot is a group of LLMs that vote on each answer
shuffle:: true

#### Question: Choice
id:: c30cf7c2-b9f5-493c-a857-02a6870b388e
content:: An LLM with no search tool confidently cites a research paper that does not exist. What best explains this?
options::
- [x] It produces text that fits the pattern of a citation, whether or not one exists
- It copied a fake citation that appeared in its training data
- Its developers programmed it to invent sources when it lacks one
- Its internal database of papers had become corrupted
shuffle:: true

#### Question: Open
id:: 6d48b99b-980f-4d86-8de3-3070e64c2fab
content:: A friend says LLMs answer questions by looking them up in a giant database of text they memorized. In a sentence or two, what is wrong with this picture?
assessment-instructions:: Score out of 100. 100 for saying the model generates new text piece by piece from patterns learned in training (stored in its weights), rather than retrieving stored documents, so it can write text it never saw. 50 for only "it generates rather than looks up" with no further detail. 0 if it accepts the lookup picture.

#### Question: Open
id:: c2fb1515-603d-451c-a355-7b23a575ff32
content:: Name two things, other than the user's latest message, that can be in an LLM chatbot's context and shape its reply.
assessment-instructions:: Score out of 100. 100 for any two of: a system prompt or instructions from the developer or app; earlier messages in the conversation; uploaded files or documents; search results or other tool outputs; saved memory notes about the user. 50 for one correct item.

#### Question: Open
id:: 9e823539-1b7e-45a3-86eb-96b3e1bc828d
content:: Why are LLMs considered a more general kind of AI than earlier systems such as chess programs or spam filters?
assessment-instructions:: Score out of 100. 100 for: one LLM can do a wide range of tasks (writing, coding, translation, answering questions), with the task set by the prompt in plain language, rather than being built or trained for a single task. 50 for "they can do more things" without the point that one model covers many tasks through prompting.

{++{"author":"AI","timestamp":1783155313042}@@---
id: b2c14c7a-dbee-4919-be38-c2b8bce345df
slug: gating-edge-cases
title: Gating edge cases (test module)
---

%% Internal test module for the per-segment gating system — NOT part of any course. It exercises the cases the "Interaction requirements demo" module doesn't: several gated chats on one page, several questions on one page, and a mixed page. Expected behavior is described in each lens so testers can verify against it. %%

# Lens: Two chats with separate minimums
id:: 95e31306-3526-4f68-a5f3-5d03eac93fc0

#### Text
content::
This page has two chats: the first needs 1 message, the second needs 2. Each chat counts only messages typed into it — sending three messages in the first chat does not unlock the second. The list under the grayed-out button names them "chat 1" and "chat 2"; the names are links that scroll to the right chat.

#### Chat
min-chat-messages:: 1
instructions::
You are chat number one. Keep replies to one short sentence.

#### Text
content::
Some text between the two chats, so scrolling between them is visible.

#### Chat
min-chat-messages:: 2
instructions::
You are chat number two. Keep replies to one short sentence.

# Lens: Two questions, one needing follow-up
id:: a1ebd571-7a46-4e8a-b4e1-078359b7b696

#### Text
content::
Two questions on one page. Question 1 just needs an answer. Question 2 has `min-chat-messages:: 1`: after answering you must also send 1 message in its feedback conversation. The list under the button says "Answer question 1" and "Answer question 2", each linking to its question; after answering question 2, its line becomes "Send 1 more message about your answer to question 2".

#### Question
content:: Question 1: What did you have for breakfast?

#### Question
min-chat-messages:: 1
content:: Question 2: Name a habit you would like to build.
assessment-instructions:: Any sincere answer is fine; ask one short follow-up question.

# Lens: Mixed page — chat, required question, optional question
id:: 50db9d6d-b7ca-461b-85a2-284e5fb35a7f

#### Text
content::
Everything at once: a chat needing 1 message, a required question, and an optional question. The button should list exactly two things under "To finish this page:" — the chat and the required question. The optional question (question 2 on this page) never appears in the list, but the required question is still called "question 1" and the optional one exists on the page, so check the numbering matches what you see.

#### Chat
min-chat-messages:: 1
instructions::
Keep replies to one short sentence.

#### Question
content:: Required: what is one thing you learned today?

#### Question
optional:: true
content:: Optional: anything else on your mind?
++}
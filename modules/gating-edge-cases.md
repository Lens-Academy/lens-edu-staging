---
id: b2c14c7a-dbee-4919-be38-c2b8bce345df
slug: gating-edge-cases
title: Gating edge cases (test module)
---

%% Internal test module for the {--{"author":"Elias's AI","timestamp":1783441621903}@@per-segment--}{++{"author":"Elias's AI","timestamp":1783441621903}@@per-lens++} gating system — NOT part of any course. It exercises the cases the "Interaction requirements demo" module doesn't: {--{"author":"Elias's AI","timestamp":1783441621903}@@several gated chats on one page,--}{++{"author":"Elias's AI","timestamp":1783441621903}@@one lens minimum shared by several chats,++} several questions on one page, and a mixed page. Expected behavior is described in each lens so testers can verify against it. %%

# Lens: Two chats {--{"author":"Elias's AI","timestamp":1783441621903}@@with separate minimums--}{++{"author":"Elias's AI","timestamp":1783441621903}@@sharing one lens minimum++}
id:: 95e31306-3526-4f68-a5f3-5d03eac93fc0{++{"author":"Elias's AI","timestamp":1783441621903}@@
min_chat_messages:: 3++}

#### Text
content::
This {--{"author":"Elias's AI","timestamp":1783441621903}@@page--}{++{"author":"Elias's AI","timestamp":1783441621903}@@lens++} has {--{"author":"Elias's AI","timestamp":1783441621903}@@two chats: the first needs 1 message, the second needs 2. Each chat counts only messages typed into it — sending--}{++{"author":"Elias's AI","timestamp":1783441621903}@@`min_chat_messages:: 3` and two chat boxes. Messages pool per lens: type into either box (or the sidebar) in any mix —++} three messages{--{"author":"Elias's AI","timestamp":1783441621903}@@ in the first chat does not --}{++{"author":"Elias's AI","timestamp":1783441621903}@@ total ++}unlock {--{"author":"Elias's AI","timestamp":1783441621903}@@the second.--}{++{"author":"Elias's AI","timestamp":1783441621903}@@completion.++} The list under the grayed-out button {--{"author":"Elias's AI","timestamp":1783441621903}@@names them "chat 1" and "chat 2";--}{++{"author":"Elias's AI","timestamp":1783441621903}@@shows one line ("Send 3 messages to++} the {--{"author":"Elias's AI","timestamp":1783441621903}@@names are links --}{++{"author":"Elias's AI","timestamp":1783441621903}@@Lens Tutor") ++}that {--{"author":"Elias's AI","timestamp":1783441621903}@@scroll to the right chat.--}{++{"author":"Elias's AI","timestamp":1783441621903}@@counts down as you send.++}

#### Chat
{--{"author":"Elias's AI","timestamp":1783441621903}@@min-chat-messages:: 1
--}instructions::
You are chat number one. Keep replies to one short sentence.

#### Text
content::
Some text between the two chats, so scrolling between them is visible.

#### Chat
{--{"author":"Elias's AI","timestamp":1783441621903}@@min-chat-messages:: 2
--}instructions::
You are chat number two. Keep replies to one short sentence.

# Lens: Two {--{"author":"Elias's AI","timestamp":1783441621903}@@questions, one needing follow-up--}{++{"author":"Elias's AI","timestamp":1783441621903}@@questions plus a message minimum++}
id:: a1ebd571-7a46-4e8a-b4e1-078359b7b696{++{"author":"Elias's AI","timestamp":1783441621903}@@
min_chat_messages:: 1++}

#### Text
content::
Two questions on one {--{"author":"Elias's AI","timestamp":1783441621903}@@page. Question 1 just needs an answer. Question 2 has `min-chat-messages:: 1`: after answering you must also send 1 message in its feedback conversation.--}{++{"author":"Elias's AI","timestamp":1783441621903}@@page, and the lens has `min_chat_messages:: 1`. Both questions need an answer, and one message to the tutor is needed on top.++} The list under the button says "Answer question {--{"author":"Elias's AI","timestamp":1783441621903}@@1" and--}{++{"author":"Elias's AI","timestamp":1783441621903}@@1",++} "Answer question {--{"author":"Elias's AI","timestamp":1783441621903}@@2", each--}{++{"author":"Elias's AI","timestamp":1783441621903}@@2" (each++} linking to its {--{"author":"Elias's AI","timestamp":1783441621903}@@question; after answering question 2, its line becomes "Send 1 more message about your answer to question 2".--}{++{"author":"Elias's AI","timestamp":1783441621903}@@question) and "Send 1 message to the Lens Tutor". A reply typed in either question's feedback conversation counts as the message; the auto-sent feedback request does not.++}

#### Question
content:: Question 1: What did you have for breakfast?

#### Question
{--{"author":"Elias's AI","timestamp":1783441621903}@@min-chat-messages:: 1
--}content:: Question 2: Name a habit you would like to build.
assessment-instructions:: Any sincere answer is fine; ask one short follow-up question.

# Lens: Mixed page — chat, required question, optional question
id:: 50db9d6d-b7ca-461b-85a2-284e5fb35a7f{++{"author":"Elias's AI","timestamp":1783441621903}@@
min_chat_messages:: 1++}

#### Text
content::
Everything at once: a {--{"author":"Elias's AI","timestamp":1783441621903}@@chat needing--}{++{"author":"Elias's AI","timestamp":1783441621903}@@lens minimum of++} 1 message, a {++{"author":"Elias's AI","timestamp":1783441621903}@@chat box, a ++}required question, and an optional question. The button should list exactly two things under "To finish this page:" — the {--{"author":"Elias's AI","timestamp":1783441621903}@@chat--}{++{"author":"Elias's AI","timestamp":1783441621903}@@required question++} and the {--{"author":"Elias's AI","timestamp":1783441621903}@@required question.--}{++{"author":"Elias's AI","timestamp":1783441621903}@@message.++} The optional question (question 2 on this page) never appears in the list, but the required question is still called "question 1" and the optional one exists on the page, so check the numbering matches what you see.

#### Chat{--{"author":"Elias's AI","timestamp":1783441621903}@@
min-chat-messages:: 1--}
instructions::
Keep replies to one short sentence.

#### Question
content:: Required: what is one thing you learned today?

#### Question
optional:: true
content:: Optional: anything else on your mind?

---
id: b2c14c7a-dbee-4919-be38-c2b8bce345df
slug: gating-edge-cases
title: Gating edge cases (test module)
---

%% Internal test module for the per-lens gating system — NOT part of any course. It exercises the cases the "Interaction requirements demo" module doesn't: one lens minimum shared by several chats, several questions on one page, and a mixed page. Expected behavior is described in each lens so testers can verify against it. %%

# Lens: Two chats sharing one lens minimum
id:: 95e31306-3526-4f68-a5f3-5d03eac93fc0
tldr:: Test lens: two chat boxes on one page share a single min_chat_messages:: 3 requirement, so messages pool across both boxes and the sidebar to unlock completion.
summary_for_tutor:: Internal gating test lens. Verifies that min_chat_messages pools across two chat segments on one page: any mix of three messages unlocks completion, shown by a single countdown line. Not part of any course.
min_chat_messages:: 3

#### Text
content::
This lens has `min_chat_messages:: 3` and two chat boxes. Messages pool per lens: type into either box (or the sidebar) in any mix — three messages total unlock completion. The list under the grayed-out button shows one line ("Send 3 messages to the Lens Tutor") that counts down as you send.

#### Chat
instructions::
You are chat number one. Keep replies to one short sentence.

#### Text
content::
Some text between the two chats, so scrolling between them is visible.

#### Chat
instructions::
You are chat number two. Keep replies to one short sentence.

# Lens: Two questions plus a message minimum
id:: a1ebd571-7a46-4e8a-b4e1-078359b7b696
tldr:: Test lens: two required questions plus a min_chat_messages:: 1 requirement, checking that all three completion items are listed and counted correctly.
summary_for_tutor:: Internal gating test lens. Verifies completion gating with two required questions and a one-message minimum: the button lists both questions and the message requirement, and a reply in either question's feedback conversation satisfies the message. Not part of any course.
min_chat_messages:: 1

#### Text
content::
Two questions on one page, and the lens has `min_chat_messages:: 1`. Both questions need an answer, and one message to the tutor is needed on top. The list under the button says "Answer question 1", "Answer question 2" (each linking to its question) and "Send 1 message to the Lens Tutor". A reply typed in either question's feedback conversation counts as the message; the auto-sent feedback request does not.

#### Question
content:: Question 1: What did you have for breakfast?

#### Question
content:: Question 2: Name a habit you would like to build.
assessment-instructions:: Any sincere answer is fine; ask one short follow-up question.

# Lens: Mixed page — chat, required question, optional question
id:: 50db9d6d-b7ca-461b-85a2-284e5fb35a7f
tldr:: Test lens: a mixed page combining a chat, a required question, and an optional question, checking that only the required items gate completion while on-page numbering stays correct.
summary_for_tutor:: Internal gating test lens. Verifies that on a page with a chat, a required question, and an optional question, only the message minimum and required question appear in the completion list while the optional question is excluded but still counted in on-page numbering. Not part of any course.
min_chat_messages:: 1

#### Text
content::
Everything at once: a lens minimum of 1 message, a chat box, a required question, and an optional question. The button should list exactly two things under "To finish this page:" — the required question and the message. The optional question (question 2 on this page) never appears in the list, but the required question is still called "question 1" and the optional one exists on the page, so check the numbering matches what you see.

#### Chat
instructions::
Keep replies to one short sentence.

#### Question
content:: Required: what is one thing you learned today?

#### Question
optional:: true
content:: Optional: anything else on your mind?

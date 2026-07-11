---
id: 2d930d96-1658-4143-b29c-52e3b9259396
summary_for_tutor: Introduces AI evaluations as structured tests designed to measure capabilities, propensities, and safety thresholds of AI models. Distinguishes safety evaluations from general performance benchmarks. Poses the key question of why high benchmark accuracy does not guarantee deployment safety.
title: AI Evaluations
tldr: How do you know if an AI system is safe? Evaluations are structured tests designed to measure what models can do — especially the dangerous things. But passing a test and being safe aren't the same thing, and understanding why is the first step to better measurement.
{--{"author":"Elias's AI","timestamp":1783770580158}@@tags:
  - lens
--}---

#### Text
content::
This module focuses on the empirical testing of what AI systems can do and identifying the risks they pose. 

**AI Evaluations** are structured knowledge about approaches and tests{>>CGL > I don't much like this definition. Feels awkward.<<} designed to measure the capabilities, propensities, and safety thresholds of AI models. Unlike general performance benchmarks, safety evals specifically look for dangerous capabilities. 

*Before you start reading the arguments for and against this agenda, try to focus your thinking by answering the question below. Discuss it with your AI tutor for as long as feels comfortable, then move on to the readings*.

#### Text
content::
**Why does high accuracy on a benchmark not guarantee that a system is safe to deploy?**

#### Chat
instructions::
The user is answering this question:
Why does high accuracy on a benchmark not guarantee that a system is safe to deploy?

Response length requirement:
- Keep responses short: aim for 120–200 words.
- Use short paragraphs. No long lectures. No lists longer than 4 items.

Your response style:
- Be calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise (great point, excellent answer, you’re right).
- If the answer is vague, ask for precision. If it is confused, say so plainly and fix it.
- Prefer explicit assumptions and causal reasoning over rhetoric.

Conversation flow requirement:
- Treat this as a short tutoring loop.
- Keep an internal turn counter for the tutoring loop (count your own tutoring replies).
- After 3 tutoring replies, ask the participant whether they want to continue the discussion or stop here. If they want to continue, reset the counter and proceed; if not, end with a brief summary of what they achieved and what to revisit later.

What you must do in each reply:
1) If a user asks a question, just answer the question
2) Othervise: Restate the participant’s answer in a more precise form (steelman it) in 2–4 sentences. Identify 1–3 key gaps, ambiguities, or hidden assumptions in their answer. Ask 2 targeted follow-up questions that force clarification (not opinion). Each question should be answerable.

Safety and integrity:
- If the participant makes a strong claim, ask what assumptions it relies on and how it could be tested.
`
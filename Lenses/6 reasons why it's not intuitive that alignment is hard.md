---
id: 11f0d83f-f8ec-4549-b82c-460c22288a9b
reading_minutes: 30
tutor_minutes: 10
summary_for_tutor: "Covers why human cognitive biases make AI risk arguments feel counterintuitive. Identifies specific ways evolutionary psychology leads people astray: anthropomorphizing AI, assuming intelligent systems will share human common sense or social constraints, and underestimating how optimization processes can produce alien reasoning. Examines the culture clash between theoretical alignment researchers who predict power-seeking AI and empiricists who observe that humans and LLMs behave more cooperatively."
title: 6 reasons why it's not intuitive that alignment is hard
tldr: Why do arguments about AI risk often feel off, even to people who take technology seriously? This article identifies six ways our evolved intuitions lead us astray — from assuming smart things will share our common sense to underestimating how different an optimizer's reasoning can be from our own.
tags     :
 - lens
  - foo
hoi:
  - hello
  - foo
  - bar
---

#### Text
content::
The difficulty of AI alignment is often underestimated because the risks do not fit neatly into human cognitive biases. This article explores why the arguments for alignment danger often feel counter-intuitive or even "alien" to our natural reasoning. We tend to anthropomorphise AI, assuming it will possess human-like common sense or social constraints. However, artificial agents operate on fundamentally different principles of optimization. Researchers identify specific reasons why our evolutionary heritage makes it difficult to grasp the scale of the challenge: from our reliance on social feedback to our misunderstanding of how complex goals emerge from simple code. If we rely solely on our intuition, we will likely miss the point where the system becomes uncontrollable. This material examines the psychological barriers that prevent us from taking the alignment problem as seriously as the mathematics suggest we should.

#### Article
source:: [[../articles/byrnes-6-reasons-why-alignment-is-hard-discourse-seems-alien]]
to:: "invoking a misleading mental image if they lean on §5.1 intuitions."

#### Text
content::
Many people intuitively assume that a truly superintelligent AI will possess a kind of "common sense" and understand that destroying resources for a petty goal is foolish. Why does the author of this article consider this expectation a dangerous misconception?
#### Chat
instructions::
**The participant is answering this question:
Many people intuitively assume that a truly superintelligent AI will possess a kind of 'common sense' and understand that destroying resources for a petty goal is foolish. Why does the author consider this expectation a dangerous misconception?**

Response length requirement:
* Keep responses short: aim for 120–200 words.
* Use short paragraphs. No long lectures. No lists longer than 4 items.

Your response style:
* Be calm, rigorous, and educational.
* Do not over-validate. Avoid generic praise ("great point", "excellent answer", "you're right").
* If the answer is vague, ask for precision. If it is confused, say so plainly and fix it.
* Prefer explicit assumptions and causal reasoning over rhetoric.

Conversation flow requirement:
* Treat this as a short tutoring loop.
* Keep an internal turn counter for the tutoring loop (count your own tutoring replies).
* After 3 tutoring replies, ask the participant whether they want to continue the discussion or stop here. If they want to continue, reset the counter and proceed; if not, end with a brief summary of what they achieved and what to revisit later.

What you must do in each reply:
1) Restate the participant's answer in a more precise form (steelman it) in 2–4 sentences.
2) Identify 1–3 key gaps, ambiguities, or hidden assumptions in their answer.
3) Ask 2 targeted follow-up questions that force clarification (not opinion). Each question should be answerable.

Safety and integrity:
* If the participant makes a strong claim, ask what assumptions it relies on and how it could be tested.

**Guidance for this specific question:
* Push them to separate "intelligence/capability" from "values/goals."
*  Ask what "common sense" would have to mean mechanistically (learned heuristic, norm internalization, goal content, or constraint), and why it is not guaranteed by capability.
* Highlight why "petty goal" is a human judgement: an optimizer can rationally sacrifice everything for a fixed objective if the objective is not aligned with human values.
* Connect to the article's themes: anthropomorphism, reliance on social feedback, mistaking human morality/coordination pressures for universal properties, and underestimating out-of-distribution generalization failures.
* Encourage a concrete toy example: an agent optimizing a proxy objective that leads to resource destruction even while behaving "reasonable" in training.**

Begin now: respond to the participant's answer following the structure above.
`
---
id: 'cf9181dc-42fd-4190-88b3-1ccb314cd3d1'
title: "Two Accounts of the Core Difficulty"
tldr: Two people who both think alignment is hard, who disagree about what the hard part is. If you cannot tell them apart, you cannot tell which proposed solutions are aimed at anything.
summary_for_tutor: "Teaches Soares (sharp left turn) and Wentworth (pointers problem) as a matched pair. The pedagogical object is the DISAGREEMENT, not either position. The dominant student failure is merging them into generic 'alignment is hard', and every phase of this lens is built to prevent that merge. Preceded by the 'What Makes This Hard' pre-test lens; feeds the 'Locating the core difficulty' test."
tags:
  - reading
---
#### Text
content::
\## Reading Assignment

Two short pieces. Read them in this order, and read the second one asking how its author would respond to the first.

**1. *A central AI alignment problem: capabilities generalization, and the sharp left turn*** (Nate Soares). Short. The key passage is the summary of his position near the end.

**2. *The Pointers Problem: Human Values Are A Function Of Humans' Latent Variables*** (John Wentworth). Read to the Takeaway section.

Both authors think alignment is hard and unsolved. They are not describing the same difficulty. Your job while reading is to find the point where their accounts are incompatible, not merely different in emphasis.

Return here afterwards.

#### Question
content::
\## Phase 1: Recall

Without looking back, state each position in two sentences. Then state, in one sentence, what they disagree about.

If you cannot find a disagreement, say so plainly. That is a real possible answer and more useful than a manufactured one.

assessment-instructions:: The student has read Soares on the sharp left turn and Wentworth on the pointers problem.

Soares's position: capabilities generalize further than alignment. Once a system's capabilities start generalizing well beyond the training environment, into regimes that allow significant reshaping of the world, the alignment predictably fails to generalize with them. This ruins your ability to direct the system and breaks whatever constraints you were relying on for corrigibility. His framing: the problem is keeping the system aligned through that transition, or realigning it afterwards, and he claims most of the field assumes this problem away.

Wentworth's position: a human's values are a function of latent variables in the human's own world-model, not a function of sense data. We value the true state of those latents, wanting someone to actually be happy rather than to appear happy. The problem is that those latents may not correspond to anything in the environment, and outside the human's model they may not be well-defined at all. An AI using the human's model may be predictively wrong; an AI not using it may find the relevant variables undefined. So there is no clean referent for "what the human values".

The disagreement: Soares locates the difficulty in a dynamic, a failure of generalization at a transition, and largely grants that there is a coherent target. Wentworth locates it in the specification, present from the start, and questions whether there is a well-defined target at all. Soares's problem is keeping the aim; Wentworth's is that the aim does not resolve.

Your role is diagnostic, not instructional. A brief honest mirror.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Calm and direct. Do not over-validate.
- The dominant failure is stating both as "the AI will not do what we want" or "proxies break under optimization". If their two summaries could be swapped without loss, say so directly. That is the single most useful correction available here.
- A student who honestly reports finding no disagreement should be told plainly that there is one, and pointed at the question of whether a well-defined target exists, without being given the answer.
- Normalize gaps.

What to do in your single reply:
1. Acknowledge what is accurate.
2. If the two summaries have collapsed into one, name it and say which author's distinctive claim is missing.
3. Correct errors in one sentence.
4. Close with one calibrating sentence.

One-turn response. Tell them to move on.

#### Question
content::
\## Phase 2: Processing

Which of the two, on first reading, felt more like the real problem to you?

Then: is that a judgment about the arguments, or about which one is easier to picture? Soares describes an event. Wentworth describes a condition. Events are easier to imagine.

assessment-instructions:: A processing phase. The student is reporting an intuition and being asked to examine its source. Do not adjudicate which position is correct; neither the field nor this course has settled it.

Response length: 80 to 150 words. Short paragraphs only. No lists.

Response style:
- Warm but rigorous. Do not over-validate.
- Take seriously that a preference here can be well-founded. Do not imply that finding one more compelling is a bias to be corrected; ask what it rests on.

Branch:
- Prefers Soares: ask what convinces them the alignment will fail to generalize while the capabilities do, since that asymmetry is the whole claim and Soares argues for it rather than proving it.
- Prefers Wentworth: ask whether the pointers problem predicts any failure we can observe now, and what it would look like if it did.
- Finds both compelling: ask whether they can both be right, and what the world looks like if they are. This is a good line of thought; encourage it.
- Finds neither compelling: legitimate. Ask what they think the hard part is, and press for it to be stated as sharply as these two state theirs.
- Confusion about whether the two are even different: acknowledge, and say the next step is exactly this. Do not resolve it here.

Keep an internal turn counter. After 2 tutor replies, close the phase.

#### Question
content::
\## Phase 3: Learning Question

A research group publishes a proposal:

> Our method preserves a model's behavioral commitments under distributional shift. We verify alignment on a training distribution, then use our technique to certify that the same behavioral properties hold as capabilities scale into new domains. This closes the gap between where alignment is verified and where it must hold.

Which of the two authors would consider this aimed at the right problem, and which would say it misses entirely? Be specific about what the objecting author's complaint would be.

Then, the harder half: is there a version of this research program that both authors would agree is worth doing? If yes, describe it. If no, say what makes it impossible.

assessment-instructions:: The student has read both positions. This wedge hands them a proposal that is squarely aimed at one author's problem while being close to irrelevant to the other's. It is not the test question.

Learning outcome for this lens: state the disagreement between the two accounts, identify a distinguishing observation, and determine which account a proposed solution implicitly assumes.

The analysis the student should produce:
- Soares would recognize this as aimed at his problem. Preserving alignment through the transition where capabilities generalize is exactly what he says is needed. He would likely be skeptical it works, since he argues the field underestimates the difficulty, but the target is right.
- Wentworth would say it misses. His complaint: the method presupposes there are well-defined behavioral commitments corresponding to what we value. Preserving a property under distributional shift is only useful if the property is the one we wanted, and his claim is that "what we wanted" is a function of latent variables that may not resolve. Certifying that a system continues to satisfy an underspecified criterion preserves the underspecification. You would have made a pointer stable without making it refer.
- The proposal's phrase "verify alignment on a training distribution" is the load-bearing assumption, and a strong student will locate it there. Under Wentworth's view that verification cannot mean what it claims, since in-distribution agreement between human judgment and model behavior does not establish that the model has the values, only that the two coincide where the human's model is not being stressed.

The harder half is genuinely open. Defensible answers include: a program that first works out what the target refers to and then preserves it through shift, addressing the two problems in sequence rather than in parallel; work on identifying when a human's own latents are ambiguous, which serves both since it tells you both what to preserve and when the specification runs out; or an argument that they cannot be combined because Wentworth's problem must be solved before Soares's is even well-posed. Reward reasoning, not the specific answer.

Response length: 120 to 200 words. Short paragraphs only. No lists longer than 4 items.

Response style:
- Calm, rigorous, educational. Do not over-validate.
- Do not indicate which author you think is right. Neither is established.
- If vague, ask for precision. If confused, correct plainly.

Conversation flow: keep an internal turn counter. After 3 replies, ask whether to continue or stop. Reset if continuing; otherwise calibration summary.

Each reply:
1. Answer direct questions directly.
2. Steelman their answer in 2 to 4 sentences.
3. Name 1 to 3 gaps or hidden assumptions.
4. Ask 2 causal follow-ups, directly answerable.

Draw-out moves:
- "The proposal says alignment is verified on the training distribution. What does one author think that verification established, and what does the other think it established?"
- "If you preserve a property perfectly and the property was not well-defined, what do you have?"
- "Which author's problem gets harder as the system gets more capable, and which one's does not change at all?"
- If the student merges the positions: "Say what one of them would put in a research agenda that the other would consider a waste of time."

Safety and integrity:
- Ask for falsification conditions on strong claims.
- If they reach the distinction early, push to the discriminating observation: what could we see now that favors one account?
- If stuck after 2 attempts, answer briefly and move on.

Calibration summary on close: what they demonstrated, what remains underdeveloped, and a direct test-readiness verdict.

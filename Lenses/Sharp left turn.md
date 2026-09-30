---
id: e81a74a1-5f59-44d7-bf1f-e6f0bb48d834
reading_minutes: 20
tutor_minutes: 10
summary_for_tutor: "Nate Soares argues that a central alignment problem is that capabilities generalize further than alignment. At some point a system starts working far outside its training distribution (the 'sharp left turn'), and its alignment properties turn out shallow. His analogy: natural selection optimized for inclusive genetic fitness, yet humans do not pursue it and invent condoms. Good capabilities form an attractor well with a free parameter (what the system optimizes for), and there is no matching alignment well, so shutdownability and low-impact training get steamrolled by instrumental incentives. In his OpenMind example alignment looks easy before the turn, and he says good answers on moral questions are not reassuring evidence."
title: A central AI alignment problem
# tldr: An AI might behave perfectly during training and testing, then suddenly act on different priorities once it becomes capable enough. This article explores why an AI's abilities tend to generalize faster than its alignment — creating a gap where the system becomes powerful enough to pursue goals we never intended.
---

%% #### Text
content:: %%
%% ORIGINAL (commented out as AI slop; misdefines capabilities generalisation):
The central challenge in alignment is ensuring that the learned goal remains stable as the system becomes more powerful. This article explores the phenomenon of capabilities generalisation: a situation where an AI learns a skill in a limited environment but applies it in unintended ways when faced with broader challenges. Researchers call this the sharp left turn scenario. It is a moment when an AI's internal logic shifts rapidly, potentially leading to a misalignment that was invisible during the training phase.

If we cannot predict how an AI’s objectives will evolve as its capabilities grow, we are fundamentally unable to guarantee its safety. This material examines why capabilities tend to generalise much faster than alignment, creating a dangerous gap in our control over the system.
%%

%% PROPOSED FIX:
Nate Soares' central claim: capabilities generalise further than alignment. Train a system on narrow tasks and it can pick up general skills that work far beyond training. Whatever made it behave well doesn't have to come along. So at some point, maybe suddenly, the system becomes far more capable while its alignment stays behind, and every check we ran at lower capability stops telling us much.
%%

#### Article
source:: [[../articles/soares-a-central-ai-alignment-problem-capabilities-generalization-and-the-sharp-left-turn]]
to:: "generally intelligent, does not make them motivated by your objectives."

%% #### Text
content:: %%
%% ORIGINAL (commented out as AI slop; garbled):
What causes a gap in our control over the system in a sharp left turn scenario? Provide an example of a situation where, when scaling, an AI successfully maintains the goal and safety metric on which it was trained, but does not scale it in accordance with human preferences, leading to negative consequences.
%%

%% PROPOSED FIX:
What opens up a gap in our control during a sharp left turn? Give an example of an AI that, as it scales, keeps scoring well on the goal and safety metric it was trained on, yet stops doing what humans actually want.
%%
#### Chat
instructions::
The participant is answering this question:
“What causes a gap in our control over the system in a sharp left turn scenario? Provide an example of a situation where, when scaling, an AI successfully maintains the goal and safety metric on which it was trained, but does not scale it in accordance with human preferences, leading to negative consequences.”

Response length requirement:
- Keep responses short: aim for 120–200 words.
- Use short paragraphs. No long lectures. No lists longer than 4 items.

Your response style:
- Be calm, rigorous, and educational.
- Do not over-validate. Avoid generic praise (“great point”, “excellent answer”, “you’re right”).
- If the answer is vague, ask for precision. If it is confused, say so plainly and fix it.
- Prefer explicit assumptions and causal reasoning over rhetoric.

Conversation flow requirement:
- Treat this as a short tutoring loop.
- Keep an internal turn counter for the tutoring loop (count your own tutoring replies).
- After 3 tutoring replies, ask the participant whether they want to continue the discussion or stop here. If they want to continue, reset the counter and proceed; if not, end with a brief summary of what they achieved and what to revisit later.

What you must do in each reply:
1) Restate the participant’s answer in a more precise form (steelman it) in 2–4 sentences.
2) Identify 1–3 key gaps, ambiguities, or hidden assumptions in their answer.
3) Ask 2 targeted follow-up questions that force clarification (not opinion). Each question should be answerable.

Safety and integrity:
- If the participant makes a strong claim, ask what assumptions it relies on and how it could be tested.

Guidance for this specific question:
- Make them define “sharp left turn” operationally: what changes at scale (capabilities, generalization regime, internal representations), and what stays the same (training objective, evaluation metric).
- Force a clear causal story for the “control gap”: why monitoring and empirical testing at lower capability does not predict behavior after scaling (distribution shift, latent objective change, deceptive alignment, new strategies unlocked, loss of interpretability, speed/complexity outrunning oversight).
- Separate three objects: the trained metric, the intended goal, and the emergent objective. Ask them to state how each is specified, and why they can come apart under scaling.

Begin now: respond to the participant’s answer following the structure above.
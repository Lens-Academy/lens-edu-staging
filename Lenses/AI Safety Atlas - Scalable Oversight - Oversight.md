---
id: b0717a61-39c3-4e9b-b29b-4ace2b9962ea
tldr: "Once an AI can do things no human expert can check, how do we still tell it when it's wrong? This piece frames the scalable-oversight problem: why 'fuzzy' tasks resist clear training signals, and why the fact that checking an answer is easier than producing one gives us a foothold."
summary_for_tutor: "Introduces scalable oversight: the challenge of giving accurate training signals once AI performs tasks beyond human evaluation. Defines training signals across supervised, self-supervised, and reinforcement learning, and distinguishes easy-to-generate signals (Go) from fuzzy tasks with subjective, ill-defined success criteria. Argues verification is generally easier than generation (the P vs NP intuition), which makes delegating and checking AI work feasible, while noting caveats: adversarial verification, non-trivial checking in practice, and the gap between verifying behavior and proving alignment."
title: "Oversight"
reading_minutes: 14
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Scalable Oversight - Oversight|Oversight]]

#### Text
optional:: true
content::
The section offers verification being easier than generation as its foothold, then says verifying behaviour is still not the same as showing a system is aligned. Did that caveat undercut the approach for you, or just bound it? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
What scalable oversight is trying to solve. It defines training signals across supervised, self-supervised and reinforcement learning, then separates tasks where the signal is easy to generate, such as Go where the game supplies the result, from fuzzy tasks whose success criteria are subjective and ill-defined, which is most of what we actually want from these systems. Its central argument is that verification is generally easier than generation, with the P versus NP intuition behind it, which makes it feasible to delegate work and then check it rather than having to do it. It then gives three caveats: verification can be adversarial, where the thing being checked is trying to pass rather than to be right; checking is often non-trivial in practice even when it is easier in principle; and verifying behaviour is not the same as establishing that a system is aligned.

topics to explore:
- The P versus NP intuition is about problem classes. How much should it carry when the outputs are essays and plans rather than proofs?
- Adversarial verification is the case that matters most for safety, and it is the case the argument works worst for. Where does that leave the foothold?
- Fuzzy tasks are defined by having no clean success criterion. Is that a property of the task, or of not having thought hard enough about it?
- Verifying behaviour versus establishing alignment is the gap the whole course keeps returning to. Does this chapter's approach narrow it or only manage it?

The specific techniques come in the following sections, so stay with the framing here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

---
id: f1f8f509-b1dd-41d9-a589-b03f7e266d67
title: "The Persona Selection Model"
tldr: "Anthropic's frame for where model behavior comes from: training doesn't install goals directly, it selects among personas the model can play. A different mechanistic story than scheming."
summary_for_tutor: "Covers Anthropic's persona selection model: LLM behavior as training selecting and stabilizing personas (character-like behavioral patterns learned from pretraining data) rather than directly instilling goals. Misalignment can look like selecting or drifting into a bad persona; interventions target which persona gets reinforced. Connects to emergent misalignment findings and contrasts with goal-based scheming frames."
---

#### Text
content::
Anthropic's frame for where model behavior comes from: training doesn't install goals directly; it selects among *personas* the model can play. A different mechanistic story than scheming, with different predictions.

#### Article
source:: [[../articles/anthropic-the-persona-selection-model]]

#### Text
content::
"Misaligned persona" vs "misaligned {--{"author":"Elias's AI","timestamp":1783024124795}@@goal" —--}{++{"author":"Elias's AI","timestamp":1783024124795}@@goal":++} a real difference, or just a relabel? Commit to whether it changes the risk picture, then defend your call against the tutor.

#### Chat
instructions::
TLDR of what the user just read: Anthropic's persona selection model proposes that LLM behavior is best understood as training selecting and stabilizing personas (character-like behavioral patterns learned from pretraining data) rather than directly instilling goals; misalignment can then look like selecting or drifting into a bad persona, and interventions target which persona gets reinforced.

Discussion topics to explore:
- How does the persona frame differ from the behavioral selection model and from Carlsmith's scheming frame in what it predicts?
- What evidence would distinguish "model playing a misaligned persona" from "model with misaligned goals", and does the distinction matter for risk?
- How does this connect to observed phenomena like emergent misalignment (bad training in one domain producing a generally misaligned persona)?

Check they can state, in their own words, what the persona selection model says training does.

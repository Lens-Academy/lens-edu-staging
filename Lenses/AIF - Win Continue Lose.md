{++{"author":"AI","timestamp":1782975138100}@@---
id: 7693c3f6-fa9c-45a8-85d1-668f5aeae968
title: "AIF - Win Continue Lose"
---

#### Text
content::
(<30 min.) Control as a game: every suspicious AI action forces a choice — execute it, replace it, or audit it — and every game state is a win, a continue, or a loss. This vocabulary makes control protocols analyzable.

#### Article
source:: [[../articles/shlegeris-wincontinuelose-scenarios-and-executereplaceaudit-protocols]]

#### Chat
instructions::
TLDR of what the user just read: Shlegeris formalizes control as a game between the lab and a potentially scheming AI: outcomes are win (catch the AI red-handed), continue (nothing decisive happens), or lose (the AI achieves catastrophe); protocols respond to each action by executing it, replacing it (resampling/deferring to trusted model), or auditing it (spending limited human oversight). Safety comes from making the AI's best attack yield a high catch-probability before a win for it.

Discussion topics to explore:
- Why is "catching the AI red-handed" a win even though the AI did something bad?
- The audit budget is scarce — how should a protocol spend it?
- How do execute/replace/audit trade off usefulness against safety?

Check they can walk through one round of the game: AI submits an action, monitor scores it, protocol picks execute/replace/audit, and the state becomes win/continue/lose.
++}
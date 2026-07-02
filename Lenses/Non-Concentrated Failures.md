---
id: 4ea41768-7281-4163-95b4-ab5a96d60f1c
title: {--{"author":"Elias's AI","timestamp":1782987422171}@@"AIF - Non-Concentrated Failures"--}{++{"author":"Elias's AI","timestamp":1782987422171}@@"Non-Concentrated Failures"
tldr: The companion piece on handling non-concentrated failures — how many bad actions the AI needs before its plan works changes the whole game theory, and determines whether online training, few-shot incrimination, or aggregate statistics is the right response.++}
---

#### Text
content::
(More in the technical weeds — treat as optional if short on time.) The companion piece: high-level methods and regimes for handling non-concentrated failures, from few-shot incrimination to training against detected sabotage.

#### Article
source:: [[../articles/greenblatt-notes-on-handling-non-concentrated-failures-with-ai-control-high-level-methods-and-different-regimes]]

#### Chat
instructions::
TLDR of what the user just read: Greenblatt's notes lay out regimes for non-concentrated (diffuse) failures: how many bad actions the AI must commit before its plan works, how much evidence each provides, and corresponding methods — online training against detected bad behavior, few-shot incrimination (using a handful of caught actions to prove misalignment), and adjusting deployment based on aggregate statistics.

Discussion topics to explore:
- How does the number-of-actions-needed dimension change the game theory between lab and schemer?
- When is training against detected bad behavior safe, and when does it just teach the AI to hide better?
- Which regime does the learner think real research sabotage would fall into?

Check they can articulate the trade-off between using detections for training vs preserving them as incriminating evidence.

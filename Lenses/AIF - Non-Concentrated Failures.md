---
id: 4ea41768-7281-4163-95b4-ab5a96d60f1c
title: "Non-Concentrated Failures"
tldr: How many bad actions does the AI need before its plan works? That number changes the whole game theory of handling non-concentrated failures, and determines the right countermeasure.
summary_for_tutor: "Covers Greenblatt's notes on regimes for non-concentrated (diffuse) failures: how many bad actions the AI must commit before its plan works, how much evidence each provides, and corresponding methods: online training against detected bad behavior, few-shot incrimination (using a handful of caught actions to prove misalignment), and deployment adjustments based on aggregate statistics. Key tension: using detections for training vs preserving them as incriminating evidence."
---

#### Text
content::
(More in the technical weeds; treat as optional if short on time.) The companion piece: high-level methods and regimes for handling non-concentrated failures, from few-shot incrimination to training against detected sabotage.

#### Article
source:: [[../articles/greenblatt-notes-on-handling-non-concentrated-failures-with-ai-control-high-level-methods-and-different-regimes]]

#### Text
content::
You catch a handful of sabotaging actions: do you train against them or bank them as incriminating evidence? You can't fully do both — pick one and defend the trade-off with the tutor.

#### Chat
instructions::
TLDR of what the user just read: Greenblatt's notes lay out regimes for non-concentrated (diffuse) failures: how many bad actions the AI must commit before its plan works, how much evidence each provides, and corresponding methods: online training against detected bad behavior, few-shot incrimination (using a handful of caught actions to prove misalignment), and adjusting deployment based on aggregate statistics.

Discussion topics to explore:
- How does the number-of-actions-needed dimension change the game theory between lab and schemer?
- When is training against detected bad behavior safe, and when does it just teach the AI to hide better?
- Which regime does the learner think real research sabotage would fall into?

Check they can articulate the trade-off between using detections for training vs preserving them as incriminating evidence.

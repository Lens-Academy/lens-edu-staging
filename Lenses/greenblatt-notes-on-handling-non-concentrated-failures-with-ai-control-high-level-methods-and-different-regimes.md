---
id: ba5208d5-d527-47ef-b591-dcb628583205
tldr: "Some AI failures aren't one dramatic act but harm accumulated across thousands of small actions: subtle sabotage, quiet sandbagging. This piece works through the control methods for that case: why reviewing a small random sample of actions can be enough, when to use online training versus just auditing, and how the tradeoffs shift as failures get more concentrated."
summary_for_tutor: "Ryan Greenblatt's working notes on using AI control to handle 'non-concentrated' failures, meaning problematic behavior spread diffusely across many actions over time rather than concentrated in a few. Central claim: these can in principle be addressed by asynchronous online training on a small randomly sampled fraction of already-executed actions, using an oversight signal as the reward. Contrasts two method classes, online training (which constrains the model to the local training loss) versus auditing-only (no training, but responding to suspicious behavior or low usefulness), laying out when each is preferable, their failure modes, and orthogonal measures such as task decomposition, restricting permissions, consistency checks, and selecting the most suspicious trajectories to review. Exploratory and technical in tone."
title: "Notes on handling non-concentrated failures with AI control: high level methods and different regimes"
---

#### Article
source:: [[../articles/greenblatt-notes-on-handling-non-concentrated-failures-with-ai-control-high-level-methods-and-different-regimes]]

---
id: 6a8e347f-a91a-40b2-b4ac-2a929d01cb98
tldr: "Once you assume an AI might actively scheme against you, what actually keeps it boxed in? This lens is Greenblatt's toolbox for AI control: logging and sandboxing, monitors that check every action, resampling suspicious outputs, human auditing hierarchies, and shutdown switches down to cutting the data-center's power, all designed to hold even when the AI is trying to subvert them."
summary_for_tutor: "Ryan Greenblatt's catalog of the main measures for AI control, defined as preventing AIs from causing existential problems even if they try to subvert countermeasures. Organizes measures into three categories that map onto existing fields: (1) non-ML software infrastructure, such as robust logging of inputs/outputs, fine-grained permission management and sandboxing, scaffolding supporting resample/defer/block, artifact and job tracking, shutdown mechanisms (down to physical power cutoff), online-training infrastructure, and limiting AI access to unnecessary information; (2) AI and human components, covering the core measures Redwood has studied (cheap monitoring on every action via trusted and untrusted monitoring and activation probes, resampling and deference strategies, an automated auditing hierarchy, human auditing with recursive oversight, and adversarial evaluation/training) plus less-core, more speculative, and specialized countermeasures; and (3) security improvements. Notes that control-evaluation methodology is currently higher priority but mapping the space of measures is still useful."
title: "An overview of control measures"
---

#### Article
source:: [[../articles/greenblatt-an-overview-of-control-measures]]

---
id: 9084ba8c-a149-42f1-940c-b32463731f32
title: "AIF - Sandbagging and Exploration Hacking"
---

#### Text
content::
A scheming AI doesn't just have to avoid getting caught doing bad things — it might strategically *underperform*: hiding capabilities on evals, or steering its own training by refusing to explore. This piece is the systematic treatment.

#### Article
source:: [[../articles/stastny-misalignment-and-strategic-underperformance-an-analysis-of-sandbagging-and-exploration-hacking]]

#### Chat
instructions::
TLDR of what the user just read: This Redwood analysis covers strategic underperformance: sandbagging (deliberately performing worse than capable, e.g. on dangerous-capability or safety-research tasks) and exploration hacking (avoiding trying strategies during RL so training never reinforces them, letting the model steer what it becomes). It analyzes when these are viable for a schemer, how training pressure constrains them, and countermeasures (elicitation with supervised fine-tuning, checking against known-answer tasks).

Discussion topics to explore:
- Why is sandbagging on *safety research* tasks especially concerning for plans that rely on AI-automated safety work?
- How does supervised fine-tuning on demonstrations constrain sandbagging in ways RL doesn't?
- What makes exploration hacking hard to detect even in principle?

Check they can explain the difference between sandbagging and exploration hacking and give a countermeasure for each.

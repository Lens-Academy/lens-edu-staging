---
id: f4a01163-8efa-4a0f-a948-2c007aef00d0
tldr: "Instead of hand-coding a reward, why not have the AI watch an expert and copy them? This section walks through imitation learning, from behavioral cloning to inverse reinforcement learning, and its catch: an AI copying humans inherits our blind spots, hallucinates to hit human-level performance, or can't tell what goal our messy behavior was even aiming at."
summary_for_tutor: "Covers imitation learning as an approach to reward misspecification: behavioral cloning (with its failure modes of confident incorrectness/hallucination and underachieving), procedural cloning, inverse reinforcement learning (IRL), and cooperative inverse reinforcement learning (CIRL). Concludes with the goal inference problem and its simplified 'easy goal inference problem', explaining why inferring human goals from observed behavior is hard when humans act sub-optimally, and why accurate imitation alone cannot produce systems that surpass the experts they learn from."
title: "Learning from imitation"
reading_minutes: 16
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Specification Gaming - Learning from Imitation|Learning from imitation]]

#### Text
optional:: true
content::
Imitation avoids having to write a reward, at the cost of inheriting the blind spots of whoever is copied. Which of the limitations the section lists did you find most damaging, and which least? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Imitation as a way around reward misspecification: instead of writing down what you want, show it. Behavioural cloning trains a system to copy demonstrated actions, and the section gives its failure modes, including confident incorrectness, where a model that has learned to sound like a competent human produces fluent wrong answers rather than admitting ignorance, and underachieving, where copying caps performance at the level of whoever was copied. Procedural cloning copies the process rather than only the actions. Inverse reinforcement learning tries to infer the reward function behind observed behaviour rather than copying the behaviour, and cooperative inverse reinforcement learning makes that a joint activity between human and system. The section closes on the goal inference problem, and its stripped-down version the easy goal inference problem, explaining why inferring what a human was aiming at is hard when humans act sub-optimally, and why accurate imitation alone cannot produce systems that exceed their teachers.

topics to explore:
- Confident incorrectness comes from imitating the surface of competence. Is that a flaw in the method or in what was demonstrated?
- Inverse reinforcement learning has to separate what a person wanted from where they went wrong. Can that be done without already knowing what they wanted?
- Imitation caps performance at the demonstrator. Does that make it a safety feature or a dead end?
- Even the "easy" version of goal inference is presented as unsolved. What does that suggest about the harder one?
- Feedback is the chapter's other proposed fix. Before reading it, does imitation look like the more promising direction to you?

Learning from feedback comes next and covers RLHF, so point at it rather than teaching it here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

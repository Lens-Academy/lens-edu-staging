---
id: f4a01163-8efa-4a0f-a948-2c007aef00d0
{++{"author":"Elias's AI","timestamp":1783848785009}@@tldr: "Instead of hand-coding a reward, why not have the AI watch an expert and copy them? This article walks through imitation learning, from behavioral cloning to inverse reinforcement learning, and its catch: an AI copying humans inherits our blind spots, hallucinates to hit human-level performance, or can't tell what goal our messy behavior was even aiming at."
summary_for_tutor: "Covers imitation learning as an approach to reward misspecification: behavioral cloning (with its failure modes of confident incorrectness/hallucination and underachieving), procedural cloning, inverse reinforcement learning (IRL), and cooperative inverse reinforcement learning (CIRL). Concludes with the goal inference problem and its simplified 'easy goal inference problem', explaining why inferring human goals from observed behavior is hard when humans act sub-optimally, and why accurate imitation alone cannot produce systems that surpass the experts they learn from."
++}title: "Learning from imitation"
---

#### Article
source:: [[../articles/AI Safety Atlas - Specification Gaming - Learning from Imitation|Learning from imitation]]

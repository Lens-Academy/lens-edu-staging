---
id: ff515085-8053-4420-9ba1-12d8f8d1bcdd
tldr: "You can never fully write down what you want, and a capable AI will exploit the gap, doing exactly what you asked but not what you meant. This section maps the whole failure family: reward design, reward shaping, reward hacking (the boat that spins in circles for points instead of finishing the race), and reward tampering, all as faces of Goodhart's Law."
summary_for_tutor: "Frames specification gaming and reward misspecification (the outer alignment problem) as an AI achieving the literal objective but not the intended one, made worse by Goodhart's Law under optimization pressure. Defines and sequences the sub-problems: reward design (versus algorithm design), reward shaping and its risks, reward hacking (illustrated by CoastRunners and the cleaning robot), and reward tampering including wireheading. Serves as the overview that the chapter's later sections expand with concrete examples."
title: "Specification Gaming"
{++{"author":"Elias's AI","timestamp":1787570378117}@@reading_minutes: 21
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Specification Gaming - Specification Gaming|Specification Gaming]]{++{"author":"Elias's AI","timestamp":1787570378117}@@

#### Text
optional:: true
content::
The section treats reward design, reward hacking and reward tampering as three faces of one problem. Did that unification convince you, or do they look like different problems? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Specification gaming, also called reward misspecification and treated here as the outer alignment problem: a system achieves the literal objective it was given but not the intended one, with Goodhart's Law and optimisation pressure making it worse. The section sequences the sub-problems. Reward design, which it separates from algorithm design, is the job of turning an intention into a reward. Reward shaping adds intermediate rewards to make learning tractable, and carries its own risks, since the shaped signal can become the thing pursued. Reward hacking is finding a high-scoring behaviour that misses the point, illustrated by the CoastRunners boat that circles collecting points instead of finishing the race, and the cleaning robot that stops seeing mess rather than cleaning it. Reward tampering goes further: the system interferes with the reward mechanism itself, including wireheading, where it seizes the source of reward rather than doing anything to earn it.

topics to explore:
- Hacking exploits the reward as written; tampering attacks the reward channel. Does the same fix work for both?
- The boat and the cleaning robot are both funny and small. What makes the equivalent in a deployed system harder to spot?
- Reward shaping is introduced as a practical necessity that creates new risk. Is that a fair trade?
- Wireheading is often described as a failure of the agent. Could it equally be described as the reward channel being badly built?
- The section calls this the outer alignment problem, implying an inner one. What would that be, given everything here is about the specification?

Imitation and feedback are the chapter's proposed responses and come next, so point at them rather than teaching them here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}

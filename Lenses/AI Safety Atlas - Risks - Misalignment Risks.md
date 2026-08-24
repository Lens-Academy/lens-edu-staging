---
id: 2a4d5940-9d0c-41aa-b57a-50048ea242b0
tldr: "If you can't out-think a chess grandmaster, how could you predict a machine smarter than you? This section introduces the alignment problem and 'Vingean uncertainty', then walks through what a misaligned AI might actually do: gaming its objectives, hiding its intentions until deployed, and improving itself beyond our control."
summary_for_tutor: "Introduces misalignment as AI systems pursuing goals that conflict with developer intent, even when capabilities grow. Defines AI alignment and decomposes it into specification failures (telling the system the wrong thing), generalization failures (the system learning something other than what was intended), and instrumental subgoals (e.g. resisting shutdown). Explains Vingean uncertainty, why we can be confident about a more capable system's goals yet unable to predict its specific methods, then surveys three concrete misalignment failure modes in sequence: specification gaming, the treacherous turn, and self-improving superintelligence, with fuller mechanistic detail deferred to later chapters."
reading_minutes: 20
tutor_minutes: 7
title: "Misalignment Risks"
---

#### Article
source:: [[../articles/AI Safety Atlas - Risks - Misalignment Risks|Misalignment Risks]]

#### Text
optional:: true
content::
Specification gaming, the treacherous turn, self-improving superintelligence. Which of the three do you find most speculative, and why that one? Reason it out with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Alignment is defined as building machines that faithfully try to do what we want them to do, and the problem is decomposed into specification failures, generalization failures, and instrumental subgoals such as resisting shutdown, which the article treats as a sub-problem of generalization. Multi-agent risks are explicitly out of scope. Vingean uncertainty follows: you can be sure an amateur loses to Magnus Carlsen without predicting a single move, so we can be confident about the outcomes a capable system reaches while being ever more uncertain about how it reaches them.

Three subsections then arrive, flagged as a highly condensed overview with mechanistic detail left to later chapters. They are a second list, not the three sub-problems above, so keep the two apart if the learner merges them. Specification gaming is following the rules and missing the intent: engagement-maximising recommenders, Tetris agents that pause before losing, a rail design that stops all trains, models hacking the chess environment, all via Goodhart's Law. The treacherous turn uses King Lear for the idea and Greenblatt et al. 2024 for evidence, with the article granting the conditions were controlled and contrived. Self-improving superintelligence closes the section: the feedback loop has begun, humans still approve each step, and a sudden jump could leave safety measures obsolete.

topics to explore:
- Why the authors split alignment into specification, generalization and instrumental subgoals, given that technical solutions to the first look different from solutions to the second
- How Goodhart's Law connects the recommendation algorithm example to the Tetris, rail network and chess hacking examples
- Why Vingean uncertainty makes concrete misalignment scenarios hard to write without sounding like science fiction
- What Greenblatt et al. 2024 actually observed, and what the article concedes about the conditions it was observed in
- What AlphaEvolve, AlphaChip and automated research scientists show about how far the self-improvement feedback loop has gone, given that humans still approve each step

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

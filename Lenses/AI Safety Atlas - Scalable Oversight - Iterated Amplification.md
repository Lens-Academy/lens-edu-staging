---
id: 1a04ac9e-a218-43c1-a68d-fde52f9be717
tldr: "How do you supervise an AI on tasks too hard for any single human to judge? Iterated Amplification bootstraps oversight: pair humans with AI assistants to produce better training signals, distill the result into a faster model, then repeat, each loop climbing beyond the previous overseer's limits."
summary_for_tutor: "Explains how to scale human oversight through iterated amplification. Covers capability amplification (aggregation, AI assistants, task decomposition), plus reliability amplification (redundancy, majority voting, error checking) and security amplification against adversarial inputs. Then introduces distillation (teacher-student compression) and combines both into Iterated Distillation and Amplification (IDA), a recursive loop that generates progressively better training signals for hard-to-evaluate tasks. Ends with IDA's limitations, including preserving alignment through distillation, cumulative errors, and tasks that resist decomposition."
title: "Iterated Amplification"
{++{"author":"Elias's AI","timestamp":1787570638429}@@reading_minutes: 19
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Scalable Oversight - Iterated Amplification|Iterated Amplification]]{++{"author":"Elias's AI","timestamp":1787570638429}@@

#### Text
optional:: true
content::
The loop climbs past the previous overseer by repeating: amplify, distil, repeat. Of the limitations the section lists, which did you find most damaging, and which least? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
How to scale human oversight by bootstrapping it. Capability amplification improves what an overseer can judge, through aggregating several people, pairing a human with AI assistants, and decomposing the task. Reliability amplification uses redundancy, majority voting and error checking to make the amplified overseer more consistent, and security amplification makes it more robust to adversarial inputs designed to exploit it. Distillation then compresses the slow amplified overseer into a faster model, teacher to student. Iterated Distillation and Amplification puts these in a loop: amplify, distil, then amplify the result again, so each round produces a better training signal for tasks nobody could evaluate directly. The section closes with its limitations: whether alignment survives each distillation step, errors accumulating across rounds, and tasks that resist decomposition, which the loop depends on.

topics to explore:
- Each round preserves alignment only if distillation does. What would tell you it had not?
- Errors that accumulate across rounds and capability that accumulates across rounds are the same loop. Which grows faster?
- The whole scheme rests on decomposition, which the earlier section said some tasks resist. Does that bound what IDA can ever oversee?
- Amplification uses AI assistants to help a human judge AI. How much of the safety argument survives that circularity?
- If you had to stop the loop after a fixed number of rounds, how would you decide the number?

Debate and weak-to-strong generalization come next as alternative approaches, so point at them rather than comparing in detail here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}

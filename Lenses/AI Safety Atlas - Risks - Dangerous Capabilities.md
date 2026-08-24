---
id: b1e5c098-beca-47b6-838c-1b7abc419e9a
tldr: "Can today's AI systems already lie, notice when they're being tested, and seek power? This section walks through concrete dangerous capabilities (deception, situational awareness, power-seeking, self-replication, and agency) with real examples, showing how each one amplifies the harm from misuse, misalignment, and systemic failure alike."
summary_for_tutor: "Introduces concrete dangerous capabilities already emerging in current AI systems, explaining how each amplifies harm across misuse, misalignment, and systemic risk. Sequentially covers deception (including sycophancy and emergent 'deep deceptiveness') with examples like Meta's CICERO, AlphaStar, and GPT-4 deceiving a TaskRabbit worker; situational awareness (self-knowledge and recognizing testing versus deployment); power-seeking; autonomous replication; and agency/goal-directedness. Frames this set as illustrative rather than exhaustive, with fuller mechanistic treatment deferred to the evaluations chapter."
reading_minutes: 17
tutor_minutes: 7
title: "Dangerous Capabilities"
---

#### Article
source:: [[../articles/AI Safety Atlas - Risks - Dangerous Capabilities|Dangerous Capabilities]]

#### Text
optional:: true
content::
The section argues these five get more dangerous in combination. Which two do you think combine worst? Make the case to the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Five concrete dangerous capabilities: deception, situational awareness, power seeking, autonomous replication and agency. The framing claim is that they amplify harm from misuse, misalignment and systemic sources alike. Deception is defined as a mismatch between what a model's internal representations suggest and what it outputs, with CICERO, AlphaStar and GPT-4's TaskRabbit CAPTCHA as examples, and sycophancy as a subtype. Situational awareness has three parts: self-knowledge, environmental awareness such as recognising testing versus deployment, and acting on that understanding. Power seeking is presented as a statistical tendency to preserve options, not a desire to dominate, shown by hide-and-seek agents that locked down blocks they were never scored for. Autonomous replication is framed as changing the game rather than amplifying, and as not yet reached: models can deploy cloud instances and exfiltrate weights under simple security, but fail at complex multi-step tasks and at robustly deploying copies. Agency is defined behaviourally, and economic incentives are said to push tools toward agents.

topics to explore:
- Why the section defines deception as a mismatch between internal representations and outputs, rather than as any behaviour that surprises us
- How sycophancy fits that definition, given that the model is producing what its training rewarded
- What the hide-and-seek agents show, given that they scored only for hiding and finding and never for controlling blocks
- Which parts of autonomous replication the section says models can already do, and which shortfalls it says remain
- Why agency is defined by observable behaviour rather than by whether the system wants anything

Later sections of this chapter build scheming and treacherous turns on top of these capabilities, and this section defers twice to the chapters on evaluations and goal misgeneralization. Stay inside this section and do not preview that later material, even if asked.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

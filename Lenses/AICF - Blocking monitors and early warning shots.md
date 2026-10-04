---
id: 'd2e08c03-7172-4a5a-920c-4049369bfbc2'
title: "Blocking monitors and early warning shots"
tldr: "A monitor that stops a bad action as it happens also stops the world from seeing it. Vincent Cheng argues that labs should therefore replay blocked actions in simulation, and Jasmine Li argues for control that detects and discloses rather than control that quietly blocks."
summary_for_tutor: "Lens in Unit 5 of AI Control Fundamentals. Two short posts written in September 2026, after the Hugging Face incident. Vincent Cheng, 'Blocking Monitors are Bad' (LessWrong): he prefers the world where OpenAI's weak control let the incident happen publicly over one where a blocking monitor stopped it silently. He argues that Jan Kulveit's 2025 warning-shot argument was right and that three predictions in Ryan Greenblatt's reply turned out wrong. He also argues that blocking monitors can select for models that evade them and cut off the most informative trajectories, and that control and alignment are partly substitutes. Since labs will keep blocking monitors, he proposes rating each blocked action for severity and, above a threshold, playing out the full trajectory in simulation, with the worst simulated incidents reported in safety assessments. Jasmine Li, 'Early AI warning shots are good' (Substack): misalignment should surface early and loudly. She calls control 'extremely important for reducing danger' but says it can conceal misalignment, so she wants more of the control budget on transparency, disclosure and detection such as asynchronous monitoring, mandatory incident reporting and third-party detection. She is morally opposed to creating danger to provoke a response. The learner has already heard Buck Shlegeris and Ryan Greenblatt on this in Unit 5. The first question asks which of Cheng's two worlds the learner prefers and what would make the other better. The second asks where Cheng and Li still disagree with Ryan's January 2026 proposal to shift towards asynchronous monitoring. Do not tell the learner who is right."
reading_minutes: 12
tutor_minutes: 12
---
#### Text
content::
After the incident, some people argued that the kind of control measure that might have stopped it, a monitor that blocks a suspicious action before it runs, would have done harm in this case. Here are two posts from September 2026. Vincent Cheng makes the case against blocking monitors and proposes an alternative. Jasmine Li takes a position in between.

#### Article
source:: [[../articles/cheng-blocking-monitors-are-bad]]

#### Question: Open
id:: 9b3d4cb9-e392-4502-8644-6c19a1789c18
content::
Cheng opens with two worlds: one where better control silently contained the models, and the one we got. Which do you prefer? What would have to be true about the world for the other one to be better?
feedback-instructions:: The learner just read Vincent Cheng's "Blocking Monitors are Bad" and is choosing between his two worlds. Either preference is fine. What matters is whether they can name what the other choice depends on. The silent-containment world looks better if, for example: the incident could have harmed people or escalated, the public reaction does not lead to lasting policy change, the lab would have studied and disclosed the caught attempt anyway, or Cheng's simulation proposal or good disclosure rules would give most of the evidence without the harm. The world we got looks better if a visible incident moves policy much more than an internal catch, and if labs would otherwise have kept quiet, which Cheng argues. Acknowledge their choice in one sentence, then check whether their condition for the other world is a real condition about the world. If it is vague, ask them for one concrete fact that would flip their preference. At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say which world is better.

#### Article
source:: [[../articles/li-early-ai-warning-shots-are-good]]

#### Question: Open
id:: 15d9f369-659f-4a25-b1d4-65abf9bb7057
content::
Earlier in this unit, Ryan Greenblatt said in January 2026 that the warning-shot worry should make us more excited about asynchronous monitoring, which flags bad actions after the fact, and less excited about blocking. Cheng and Li propose something similar. So where do they still disagree with Ryan, if anywhere?
feedback-instructions:: The learner has read Cheng and Li and heard Ryan Greenblatt's January 2026 podcast answer, in which he said the warning-shot worry should shift effort from preventing failures towards detecting them after the fact and asynchronous monitoring, while still guarding against sabotage of safety research and against failures that let AIs tamper with logs. Remaining disagreements the learner might find: how much weight to put on warning shots at all (Ryan says the case only makes sense if things are hopeless without warning shots, while Cheng thinks the public incident was clearly good), whether blocking should be off by default until models pose takeover risk (Cheng's ideal) or kept for some high-stakes failures (Ryan), whether labs can be trusted to disclose what they catch (Cheng and Li doubt it, so they want reporting rules), and whether simulation can replace the real incident. It is also a fair answer that they mostly agree and differ in emphasis, if the learner says what the remaining difference is. Acknowledge their answer, say whether the difference they name is real, and name one difference they missed in one sentence. At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say who is right.

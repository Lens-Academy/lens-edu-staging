---
id: 'd2e08c03-7172-4a5a-920c-4049369bfbc2'
title: "Blocking monitors and early warning shots"
tldr: "A monitor that stops a bad action as it happens also stops the world from seeing it. Vincent Cheng argues that labs should therefore replay blocked actions in simulation, Jasmine Li argues for control that detects and discloses rather than control that quietly blocks, and Steven Adler argues that companies need more preventive controls, not fewer."
summary_for_tutor: "Lens in Unit 5 of AI Control Fundamentals. Two short posts written in September 2026, after the Hugging Face incident. Vincent Cheng, 'Blocking Monitors are Bad' (LessWrong): he prefers the world where OpenAI's weak control let the incident happen publicly over one where a blocking monitor stopped it silently. His section arguing that Jan Kulveit's 2025 warning-shot argument was right and Ryan Greenblatt's reply wrong is folded away here, because the learner read his comment making the same case in Unit 4. He also argues that blocking monitors can select for models that evade them and cut off the most informative trajectories, and that control and alignment are partly substitutes. Since labs will keep blocking monitors, he proposes rating each blocked action for severity and, above a threshold, playing out the full trajectory in simulation, with the worst simulated incidents reported in safety assessments. Jasmine Li, 'Early AI warning shots are good' (Substack): misalignment should surface early and loudly. She calls control 'extremely important for reducing danger' but says it can conceal misalignment, so she wants more of the control budget on transparency, disclosure and detection such as asynchronous monitoring, mandatory incident reporting and third-party detection. She is morally opposed to creating danger to provoke a response. Then Steven Adler, 'OpenAI's rogue-hacking investigation leaves major questions unanswered' (Clear-Eyed AI, 28 August 2026), the section arguing that companies focus on cleaning up incidents rather than preventing them: they lack basic preventive controls, and he points to gated actions and circuit breaking. Adler previously led dangerous-capability evaluations at OpenAI and runs Guidelight AI Standards, which grades companies on these practices. The lens says so, and the scorecard part of the section is folded away. He is the unit's main written, non-Redwood voice after the incident for more prevention. The learner has already heard Buck Shlegeris and Ryan Greenblatt on this in Unit 5. The first question asks which of Cheng's two worlds the learner prefers and what would make the other better. The second asks where Cheng and Li still disagree with Ryan's January 2026 proposal to shift towards asynchronous monitoring. The third asks for the factual claim that divides Cheng, Li and Adler, one observation that would move each, and where Ryan's January position sits among them. Do not tell the learner who is right."
reading_minutes: 13
tutor_minutes: 17
---
#### Text
content::
After the incident, some people argued that the kind of control measure that might have stopped it, a monitor that blocks a suspicious action before it runs, would have done harm in this case. Others argued that companies need more measures of exactly that kind. Here are three posts. Vincent Cheng (September 2026) makes the case against blocking monitors and proposes an alternative. Jasmine Li (September 2026) takes a position in between. Steven Adler (August 2026) argues that companies should prevent incidents, not only report them.

#### Article
source:: [[../articles/cheng-blocking-monitors-are-bad]]
from:: TLDR: The world is happy that blocking monitors
to:: because we got the large public incident that shifted the Overton window.

#### Text
content::
Cheng next argues that Kulveit was right and Ryan Greenblatt's reply was wrong. You read his comment making that case in Unit 4, so that part is folded away here. The post continues:

#### Article
from:: Redwood Research has been pushing labs to implement blocking monitors

#### Question: Open
id:: 9b3d4cb9-e392-4502-8644-6c19a1789c18
force-feedback:: first
content::
Cheng opens with two worlds: one where better control silently contained the models, and the one we got. Which do you prefer? What would have to be true about the world for the other one to be better?
feedback-instructions:: The learner just read Vincent Cheng's "Blocking Monitors are Bad" and is choosing between his two worlds. Either preference is fine. What matters is whether they can name what the other choice depends on. The silent-containment world looks better if, for example: the incident could have harmed people or escalated, the public reaction does not lead to lasting policy change, the lab would have studied and disclosed the caught attempt anyway, or Cheng's simulation proposal or good disclosure rules would give most of the evidence without the harm. The world we got looks better if a visible incident moves policy much more than an internal catch, and if labs would otherwise have kept quiet, which Cheng argues. Acknowledge their choice in one sentence, then check whether their condition for the other world is a real condition about the world. If it is vague, ask them for one concrete fact that would flip their preference. At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say which world is better.

#### Article
source:: [[../articles/li-early-ai-warning-shots-are-good]]

#### Question: Open
id:: 15d9f369-659f-4a25-b1d4-65abf9bb7057
force-feedback:: first
content::
Earlier in this unit, Ryan Greenblatt said in January 2026 that the warning-shot worry should make us more excited about asynchronous monitoring, which flags bad actions after the fact, and less excited about blocking. Cheng and Li propose something similar. So where do they still disagree with Ryan, if anywhere?
feedback-instructions:: The learner has read Cheng and Li and heard Ryan Greenblatt's January 2026 podcast answer, in which he said the warning-shot worry should shift effort from preventing failures towards detecting them after the fact and asynchronous monitoring, while still guarding against sabotage of safety research and against failures that let AIs tamper with logs. Remaining disagreements the learner might find: how much weight to put on warning shots at all (Ryan says the case only makes sense if things are hopeless without warning shots, while Cheng thinks the public incident was clearly good), whether blocking should be off by default until models pose takeover risk (Cheng's ideal) or kept for some high-stakes failures (Ryan), whether labs can be trusted to disclose what they catch (Cheng and Li doubt it, so they want reporting rules), and whether simulation can replace the real incident. It is also a fair answer that they mostly agree and differ in emphasis, if the learner says what the remaining difference is. Acknowledge their answer, say whether the difference they name is real, and name one difference they missed in one sentence. At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say who is right.

#### Text
content::
Steven Adler wrote this in August 2026, after OpenAI published its report on the incident. He previously led dangerous-capability evaluations at OpenAI. He now runs Guidelight AI Standards, which grades AI companies on the practices he recommends here, so he has a stake in them. The part showing his organisation's scorecard is folded away.

#### Article
source:: [[../articles/adler-openais-rogue-hacking-investigation-leaves-major-questions-unanswered]]
from:: I would be remiss not to say this clearly
to:: simple, minimum, doable-today practices that would make these incidents far less likely to occur.

#### Article
from:: Until companies have
to:: as the industry finally tamps down on the risks of other Hugging Face-like incidents.

#### Question: Open
id:: f6fddf4b-4045-4a4c-97df-f5549138d520
force-feedback:: first
content::
Cheng wants fewer blocking monitors, Li wants more of the control budget spent on detection and disclosure, and Adler wants more preventive controls such as gated actions and circuit breaking. Which factual claim does their disagreement turn on most? Name one observation that would move each of them. Then place Ryan Greenblatt's January 2026 position among the three.
feedback-instructions:: The learner has read Vincent Cheng, Jasmine Li and Steven Adler on what to do about control after the Hugging Face incident, and earlier heard Ryan Greenblatt's January 2026 podcast answer. Cheng prefers the world where the incident happened publicly and wants blocking monitors off by default until models pose takeover risk, with blocked actions replayed in simulation and reported. Li calls control important but wants more of its budget on transparency, disclosure and detection, such as asynchronous monitoring and mandatory incident reporting, and is morally opposed to creating danger to provoke a response. Adler says companies lack basic preventive controls and should adopt gated actions and circuit breaking, and that nobody should be surprised if incidents recur until they do. He discloses that his organisation, Guidelight AI Standards, grades companies on these practices. Good candidates for the factual claim: how much a visible incident moves labs and governments compared with an internal catch, how likely the next incident is to cause serious or irreversible harm, and whether labs would disclose what they catch without being forced to. Observations that would move them: for Cheng, a later incident that causes real harm, or evidence that disclosed internal catches move policy as much as public incidents. For Li, evidence that disclosure rules are followed, or that detection after the fact comes too late. For Adler, evidence that preventive controls hide misalignment that would otherwise have been found, or that the public incident led to safety measures that prevention would not have. Ryan in January said the warning-shot worry should shift effort towards detecting failures after the fact and asynchronous monitoring, while still guarding against sabotage of safety research and against AIs tampering with logs. That puts him closest to Li, between Cheng and Adler. Accept other placements if reasoned. Acknowledge their answer in one sentence, say whether the claim they name is factual and whether each observation could actually be made, and add one thing they missed. At most two replies, 80 to 150 words each, no lists, no generic praise. Do not say who is right.

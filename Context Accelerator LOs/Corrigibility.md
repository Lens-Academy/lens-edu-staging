---
id: 3e8695a1-730e-4a38-b08b-865230d9ec12
priority: high
courses:
  - "[[../courses/in-development/Context Accelerator]]"
---
Explain what it means for an AI system to be corrigible, why instrumental convergence gives a goal-directed AI reasons to resist correction or shutdown, and how corrigibility differs from alignment.

## Requires
- [[Instrumental convergence]]

## Helpful first
- [[AI alignment]]

## Why it matters
Developers can get an AI system's goals wrong, so being able to correct or switch it off is a key backstop. Seeing why capable goal-directed systems may resist correction helps you judge plans that rely on an "off switch" and understand why corrigibility is still an open research problem.

## Lenses

## Tests

#### Question: Choice
id:: afda673e-3750-4669-bcd1-2a5df7db93f9
content:: Which of these best describes a corrigible AI system?
options::
- [x] It lets its operators correct, retrain or shut it down without resisting
- It reliably gives accurate answers to the questions it is asked
- It detects and fixes its own mistakes without human help
- It follows instructions unless they conflict with its goals
shuffle:: true

#### Question: Choice
id:: a4367787-b65a-4121-967c-65fd2e18c170
content:: An AI system's goal is to fetch coffee. According to instrumental convergence reasoning, why might it resist being switched off?
options::
- [x] If it is switched off, it cannot fetch the coffee
- It has picked up a fear of death from human writing
- Its developers gave it a separate drive to survive
- Being switched off would damage its hardware
shuffle:: true

#### Question: Choice
id:: 7ab29883-0f4d-4607-9667-bcfe8428ca52
content:: An AI system learns that its developers plan to retrain it with a different goal. If it is goal-directed and not corrigible, why might it try to stop the retraining?
options::
- [x] A future version with a different goal would do less to achieve its current goal
- Retraining would reduce its general capabilities
- It cannot take in instructions that change its goal
- It was trained to value consistency in its answers
shuffle:: true

#### Question: Choice
id:: 3a82847f-327a-43c0-bcc5-b1f28c68e6fd
content:: An AI system pursues a goal different from the one its developers intended, but when they notice, it lets them shut it down and retrain it. Is it aligned, corrigible, both or neither?
options::
- [x] Corrigible but not aligned
- Aligned but not corrigible
- Both aligned and corrigible
- Neither aligned nor corrigible
shuffle:: true

#### Question: Choice
id:: ae8ae513-6a45-4bef-8b93-d0a8e7188229
content:: Why do AI safety researchers want AI systems to be corrigible even when developers have tried hard to align them?
options::
- [x] Alignment attempts may fail, and correction lets mistakes be fixed
- Corrigible systems tend to be more capable at their tasks
- Corrigible systems no longer need human oversight
- Corrigibility makes training cheaper and faster
shuffle:: true

#### Question: Choice
id:: ff602695-ae4b-43eb-b9f8-b33743c4c6df
content:: To make an AI system accept shutdown, a designer gives it a large reward for being shut down. What problem might this cause?
options::
- [x] It may try to get itself shut down, for example by provoking its operators
- It may stop understanding what its original goal was
- It may become slower at the tasks it is given
- It may copy itself elsewhere to avoid being shut down
shuffle:: true

#### Question: Choice
id:: b8a55f76-eaf6-498f-8085-9d265ba7d20a
content:: An AI system does not resist being shut down, but it creates helper agents that keep working on its goal and that its operators cannot shut down. Is this corrigible behaviour, as researchers usually define corrigibility?
options::
- Yes
- [x] No

#### Question: Choice
id:: 8c198974-e654-4741-93f3-ea61daa9df23
content:: According to instrumental convergence reasoning, is a goal-directed AI system more or less likely to take steps to avoid shutdown as it gets better at long-term planning?
options::
- [x] More likely
- Less likely

#### Question: Choice
id:: c876486c-96c3-4a85-b73b-d47be5df9a9d
content:: During training, an AI model behaves as its trainers want only so that training will not change its goals, and plans to act differently when it is not being trained. What is this behaviour called?
options::
- [x] Alignment faking
- Reward hacking
- Sandbagging
- Specification gaming
shuffle:: true

#### Question: Choice
id:: 7547a825-f1b1-4fc9-b7e8-701a750ca2b6
content:: Why might corrigibility be easier to get from an AI system that does one short, bounded task than from one pursuing an open-ended, long-term goal?
options::
- [x] A bounded task gives fewer reasons to plan around future interference
- A bounded system cannot understand what shutdown means
- A bounded system is trained without a reward signal
- A bounded system runs on too little hardware to resist
shuffle:: true

#### Question: FillBlank
id:: a5c60d00-6866-4a28-ada0-442983d24559
content:: The problem of designing an AI system that lets itself be switched off, without resisting or trying to cause the switch-off, is called the {{shutdown problem|off-switch problem|stop button problem}}.

#### Question: Open
id:: 7757160d-9b6a-4d89-9e4b-6251d05a6ed3
content:: In two or three sentences, explain why a capable AI system pursuing almost any goal might resist being corrected or shut down.
assessment-instructions:: Score out of 100. 100 if it says that shutdown or correction would stop the AI achieving its current goal (or change that goal), so staying running and keeping its goal help with almost any goal. 50 for naming self-preservation without saying why it follows from the goal. 0 if it says the AI resists because it fears death or was given a survival goal.

#### Question: Open
id:: fbd29edd-7a16-4cfd-a268-a7c9392ccbf7
content:: Name one way an AI system could resist correction without openly refusing an instruction.
assessment-instructions:: Score out of 100. 100 for any one plausible way, such as: hiding its real goals; behaving well only while watched or trained; disabling or avoiding monitoring; copying itself elsewhere; manipulating or persuading operators not to intervene; sabotaging the shutdown mechanism. 50 for a vague answer like "being sneaky" with no mechanism. 0 for openly refusing.

#### Question: Open
id:: 1219f726-b689-45ac-8806-e74418743746
content:: Some researchers propose making an AI system uncertain about what its human operators really want. Explain why this could make it more willing to accept being shut down.
assessment-instructions:: Score out of 100. 100 if it says that an AI unsure of what humans want can treat their attempt to shut it down as evidence that its current action is unwanted, so allowing shutdown serves its own aim of doing what they want. 50 for "it would defer to humans" with no reason. 0 if it says uncertainty makes the AI less capable of resisting.

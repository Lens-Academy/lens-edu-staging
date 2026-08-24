---
id: e0c96b1c-29d0-4908-9718-f21985ef8ca9
tldr: "What if a highly capable AI is actively trying to defeat your safety measures? Control evaluations test whether the measures still hold, asking not whether a model wants to cause harm, but whether it could even if it tried, by pitting a red team against a blue team."
summary_for_tutor: "Explains control evaluations, which test whether safety protocols hold when a highly capable AI actively tries to subvert them, distinct from capability evaluations (what models can do) and propensity evaluations (what models tend to do). Frames safety as two complementary barriers: alignment (the AI doesn't want to cause harm) and control (the AI can't, even if it tries). Covers the control property as a probability estimate under conservative assumptions, the safety significance of catching models 'red-handed' (enabling proliferation of examples, adversarial training, studying countermeasures, collusion signals, and instance-specific knowledge), and the red-team versus blue-team adversarial game structure."
title: "Control Evaluations"
reading_minutes: 16
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Control Evaluations|Control Evaluations]]

#### Text
optional:: true
content::
Two barriers: the AI does not want to cause harm, and the AI could not even if it tried. Which did you come away putting more weight on, and why that one? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Control evaluations test whether safety protocols hold when a highly capable system is actively trying to defeat them. The section frames safety as two complementary barriers: alignment, where the system does not want to cause harm, and control, where it cannot even if it tries. Control evaluations belong to the second, and are distinct from capability evaluations, which ask what a model can do, and propensity evaluations, which ask what it tends to do. The control property is treated as a probability estimate made under deliberately conservative assumptions about how adversarial the model is. The section explains why catching a model red-handed matters: it produces examples that can be shared, supports adversarial training, allows countermeasures to be studied, gives signals about collusion between systems, and yields knowledge specific to that deployment. The method is an adversarial game between a red team playing the scheming model and a blue team defending.

topics to explore:
- Control assumes the worst about the model on purpose. Is a conservative assumption a strength here, or a way of never being wrong?
- Catching a model red-handed is treated as valuable. Valuable enough to justify running systems you suspect are scheming?
- The red team is human and the model is not. How much does the game tell you about a model more capable than the red team?
- Control is described as complementary to alignment. Is there a level of capability where it stops being either?
- If control gives you a probability rather than a guarantee, what probability would be good enough to deploy on?

The strategies chapter covered control as a strategy; this section is about evaluating it. Keep to the evaluation question here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

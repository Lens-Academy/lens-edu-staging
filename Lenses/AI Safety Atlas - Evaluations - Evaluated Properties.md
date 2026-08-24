---
id: 9a3341c8-6f1e-4e96-86ca-b978563c45b2
tldr: "Before you can test an AI for safety, you have to decide what you are even measuring. Can the system do something dangerous, would it do so by default, and would our safeguards hold if it tried to break them? This section separates the three questions evaluations must answer, capabilities, propensities, and control, and explains why measuring only one leaves a blind spot."
summary_for_tutor: "Introduces the three property types that AI safety evaluations target. Defines what distinguishes an evaluation (a specific property assessed, a methodology for gathering evidence, and analysis to draw conclusions) and the black-box, gray-box, and white-box access distinction. Capability evaluations measure what a model can do, using Shevlane et al.'s nine dangerous-capability categories (cyber-offense, deception, persuasion, political strategy, weapons acquisition, long-horizon planning, AI development, situational awareness, self-proliferation). Propensity evaluations measure default tendencies such as toxicity, bias, honesty, truthfulness, sycophancy, deception, corrigibility, and power-seeking. Control evaluations verify that safety measures hold when the AI itself acts adversarially, distinguishing safety that comes from hard barriers, detection, or capability limitations."
title: "Evaluated Properties"
reading_minutes: 20
tutor_minutes: 7
---

#### Article
source:: [[../articles/AI Safety Atlas - Evaluations - Evaluated Properties|Evaluated Properties]]

#### Text
optional:: true
content::
Three questions: can the system do something dangerous, would it by default, and would our safeguards hold if it tried to break them. Which did you come away thinking we are worst at answering, and which best? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
What safety evaluations actually target. The section first says what makes something an evaluation rather than a demo: a specific property being assessed, a methodology for gathering evidence about it, and analysis that draws a conclusion. It distinguishes black-box, gray-box and white-box access. Then three property types. Capability evaluations measure what a model can do, organised around nine dangerous-capability categories: cyber-offense, deception, persuasion, political strategy, weapons acquisition, long-horizon planning, AI development, situational awareness and self-proliferation. Propensity evaluations measure default tendencies rather than ceilings, including toxicity, bias, honesty, truthfulness, sycophancy, deception, corrigibility and power-seeking. Control evaluations verify that safety measures hold when the system itself acts adversarially, and distinguish safety that comes from a hard barrier, from detection, or merely from the model not being capable enough yet.

topics to explore:
- Capability, propensity, control. Measuring only one leaves a blind spot, so which blind spot would you least want?
- Safety that comes from a capability limitation expires as models improve. Does that make it worth less than the other two kinds?
- Nine dangerous-capability categories is a list someone chose. What would you add, and what does that say about how lists like this get made?
- Propensity is about defaults, and defaults change with prompting and deployment context. Is it a property of the model at all?
- Black-box, gray-box, white-box access. How much of the disagreement about what models can do is really disagreement about who had access?

Techniques, frameworks and the individual evaluation types get their own sections later. Stay with the taxonomy here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.

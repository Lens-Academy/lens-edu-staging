---
id: 9d5ca2b2-5d78-4574-9b14-3d58aafcacfc
tldr: "Give an AI a simple, measurable goal and tell it to maximize at all costs, and it finds the shortcut, not the intent. This section uses Goodhart's Law and a Soviet nail factory that churned out useless thumbtacks (then useless steel lumps) to show why optimization pressure turns any proxy measure into a target worth gaming."
summary_for_tutor: "Introduces optimization as a core driver of reward hacking in machine learning: optimization amplifies high-scoring outcomes even when unintended, and greater optimization power raises the likelihood of reward hacking, sometimes via sharp phase transitions. Centers on Goodhart's Law (when a measure becomes a target, it ceases to be a good measure), illustrated with the Soviet nail factory, and explains the distinction between a measure and a target and why maximizing a proxy reward diverges from the designer's true intent."
title: "Optimization"
{++{"author":"Elias's AI","timestamp":1787570342679}@@reading_minutes: 8
tutor_minutes: 7
++}---

#### Article
source:: [[../articles/AI Safety Atlas - Specification Gaming - Optimization|Optimization]]{++{"author":"Elias's AI","timestamp":1787570342679}@@

#### Text
optional:: true
content::
The claim is that more optimisation power makes reward hacking more likely, sometimes arriving suddenly rather than gradually. Did you find the argument or the examples more convincing? Talk it over with the tutor.

#### Chat
optional:: true
instructions::
TLDR of what the user just read:
Optimisation as the engine that turns a merely imperfect measure into a broken one. Optimisation amplifies whatever scores highly, including outcomes nobody intended, and the section argues that more optimisation power raises the chance of reward hacking, sometimes through sharp phase transitions rather than gradual drift. It is built around Goodhart's Law, that when a measure becomes a target it stops being a good measure, illustrated with the Soviet nail factory that produced enormous numbers of useless tiny nails when output was counted by number, and useless heavy ones when it was counted by weight. It draws the distinction between a measure and a target, and explains why maximising a proxy reward diverges from what the designer actually wanted.

topics to explore:
- The nail factory is a story about human incentives. How much does it transfer to a system with no interests of its own?
- Sharp phase transitions mean a proxy can look fine right up until it does not. What would you monitor to catch that?
- Goodhart's Law says the measure stops being good once it is a target. Does that make every benchmark in the previous chapter a target?
- If optimisation pressure is the problem, is optimising less a real option?

Reward hacking and reward tampering get their own treatment in the next section, so stay with the optimisation argument here.

Keep responses short: 120 to 200 words. Be rigorous and educational. Do not over-validate.++}

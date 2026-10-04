---
id: '53ab5ec2-f9b3-476b-8db6-a6a93e56f099'
title: "Would a profit-only lab build it?"
reading_minutes: 10
tutor_minutes: 11
tldr: "If a company that only cares about profit would build a safety tool anyway, your work on it may just make AI more profitable. Yonatan Cale puts this test to monitoring. Marius Hobbhahn and Alex Mallen answer in different ways."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The neglectedness and acceleration criticism and two replies. The learner reads Yonatan Cale's comment (January 2026) on Marius Hobbhahn's post 'The case for AGI safety products', in full: Cale was considering building safety monitors himself, he is especially worried if a product automates large parts of technical AI safety work, he sees an upside in finding reproducible examples of misalignment at scale, and he says he is not against for-profit safety companies in general. His concern: safety monitors might in practice be 'things that make AI more reliable for using in a commercial context', and his test 'Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?'. Then Hobbhahn's reply, in full: monitors may make consumer applications more capable, but are unlikely to push the frontier, so 'the risk is pretty low and the benefits are high'. Then an excerpt of Alex Mallen's 'Capabilities research expands the safety-usefulness Pareto frontier too' (Redwood Research blog, 2 October 2026): any research widens the set of safety and usefulness combinations developers can choose from, so 'safety without hurting usefulness' is too weak a definition of safety research. What matters is which point developers choose. Safety research usually makes them choose more safety, capabilities research usually less. Cale's criticism is mainly 'works but not worth the effort' (the work would happen anyway), with a 'makes things worse' side (more profitable AI, faster deployment). Do not tell the learner who is right."
---
#### Text
content::
Some safety work would get done even if nobody worried about catastrophe, because it also makes AI more useful to sell. Critics say that kind of work is not neglected, and that doing it may mostly speed AI up. Here is one version of this criticism, applied to monitors, and two replies.

In January 2026 Marius Hobbhahn posted [The case for AGI safety products](https://www.lesswrong.com/posts/iwfdwzJerpC7FqbZG/the-case-for-agi-safety-products). Yonatan Cale replied:

#### Article
source:: [[../articles/cale-comment-on-the-case-for-agi-safety-products]]

#### Text
content::
Hobbhahn answered:

#### Article
source:: [[../articles/hobbhahn-comment-on-the-case-for-agi-safety-products]]

#### Text
content::
Alex Mallen of Redwood Research gives a more general way to think about this. Read the first part of his post. (The "Pareto frontier" is the set of best available trade-offs: for each level of usefulness, the most safety you can get.)

#### Article
source:: [[../articles/mallen-capabilities-research-expands-the-safety-usefulness-pareto-frontier-too]]
from:: It’s tempting to define safety research
to:: Visually: near the initial pink point, the green slope is shallower than the red slope.

#### Question: Open
id:: 917241f5-4296-469a-81f1-a96b9db5a54f
force-feedback:: first
content::
\## Apply the test

In Unit 1 you met trusted monitoring: a weaker, trusted model reads what a stronger, untrusted model does and flags suspicious actions for a human to check.

Put Cale's question to it. Would a company that only cares about profit build trusted monitoring anyway? Which parts of it would they build, and which parts would they skip?
feedback-instructions:: The learner applies Yonatan Cale's "would a profit-only company build it?" test to trusted monitoring. A good answer separates parts. A profit-only company would plausibly build monitors that catch costly mistakes, misuse by customers, and obvious misbehaviour, because these make agents reliable enough to sell. It would be less likely to build the parts aimed at a model that is deliberately hiding its attacks: red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and responses to a catch that cost money, such as pausing. Accept other reasoned splits. In 60 to 120 words, say what the answer got right and name the most important part it missed. One turn, then tell them to move on. No generic praise. If the learner is stuck, give one foothold: ask what the monitor would be catching in each case, an honest mistake or a hidden attack.

#### Question: Open
id:: 35de7efe-1ee7-443e-8fd2-8610ed47a447
force-feedback:: first
content::
\## Weigh the replies

1. Which kind of criticism is Cale's: control does not work, works but is not worth the effort, or works and makes things worse? It may have more than one side.
2. Hobbhahn and Mallen both reply, in different ways. Which reply answers Cale better, and what does it still leave open?
feedback-instructions:: The learner is practising the unit's core skill: sorting a criticism, and weighing replies to it. Reference points: Cale's criticism is mainly "works but not worth the effort" because the work would happen anyway (it is not neglected), with a "makes things worse" side: monitors make AI more reliable and profitable, so people deploy more of it. Hobbhahn's reply is empirical and specific: monitors built outside the frontier companies are unlikely to push the frontier, the externality is faster coding, and frontier companies have hundreds of people doing this anyway. What it leaves open: he does not address whether the scheming-robust parts are what a profit-only company would skip, and "unlikely to push the frontier" is his estimate. Mallen's reply is a model: what matters is not whether research creates new options but which option developers choose. Safety research tends to make developers choose more safety, capabilities research less. Applied to Cale: the question becomes whether a given monitor mainly makes safety cheaper or mainly makes usefulness possible. Mallen also concedes that widening the options can lower the safety developers choose. A learner may find either reply better, or neither. Up to three turns. Per reply: steelman the learner's answer in two to four sentences, name one to three gaps, and ask up to two direct follow-up questions. If stuck after two attempts, give a short direct answer and move on. Do not say who is right overall. 80 to 150 words per reply. No generic praise. If the learner says they do not understand, give one foothold from the material, such as Mallen's sentence "developers have to choose a particular point on the Pareto frontier". If they still do not attempt it, rephrase the question in other words.

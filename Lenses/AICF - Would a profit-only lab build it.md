---
id: '53ab5ec2-f9b3-476b-8db6-a6a93e56f099'
title: "Would a profit-only lab build it?"
reading_minutes: 9
tutor_minutes: 10
tldr: "Yonatan Cale asks whether a company that only cares about profit would build a safety tool anyway. If so, the work is not neglected and may mostly speed AI up. Marius Hobbhahn and Alex Mallen answer in different ways."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Does control make things worse?', third lens of the submodule on the criticism that control speeds up AI without making it safer in the long run. The learner reads Yonatan Cale's comment (January 2026) on Marius Hobbhahn's post 'The case for AGI safety products', in full: Cale was considering building safety monitors himself, he is especially worried if a product automates large parts of technical AI safety work, he sees an upside in finding reproducible examples of misalignment at scale, and he says he is not against for-profit safety companies in general. His concern: safety monitors might in practice be 'things that make AI more reliable for using in a commercial context', and his test 'Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?'. Then Hobbhahn's reply, in full: monitors may make consumer applications more capable, but are unlikely to push the frontier, so 'the risk is pretty low and the benefits are high'. Then an excerpt of Alex Mallen's 'Capabilities research expands the safety-usefulness Pareto frontier too' (Redwood Research blog, 2 October 2026): any research widens the set of safety and usefulness combinations developers can choose from, so 'safety without hurting usefulness' is too weak a definition of safety research. What matters is which point developers choose. Safety research usually makes them choose more safety, capabilities research usually less. Earlier lenses in the submodule: Richard Ngo's general version and Caspar Oesterheld's general reply, then Habryka's and Bushnaq's control-specific versions. Do not tell the learner who is right."
---
#### Text
content::
Some safety work would get done even if nobody worried about catastrophe, because it also makes AI more useful to sell. Critics say that kind of work is not neglected, and that doing it may mostly speed AI up. Yonatan Cale applies this worry to monitors. In January 2026 Marius Hobbhahn posted [The case for AGI safety products](https://www.lesswrong.com/posts/iwfdwzJerpC7FqbZG/the-case-for-agi-safety-products), and Cale replied:

#### Article
source:: [[../articles/cale-comment-on-the-case-for-agi-safety-products]]

#### Question: Open
id:: 917241f5-4296-469a-81f1-a96b9db5a54f
force-feedback:: first
content::
\## Apply the test

In Unit 1 you met trusted monitoring: a weaker, trusted model reads what a stronger, untrusted model does and flags suspicious actions for a human to check.

Put Cale's question to it.

1. Would a company that only cares about profit build trusted monitoring anyway?
2. Which parts of it would they build, and which parts would they skip? Say why for each.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be "things that make AI more reliable for using in a commercial context", and asks: "Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?" In trusted monitoring, a weaker, trusted model reads what a stronger, untrusted model does and flags suspicious actions for a human to check. A profit-only company would plausibly build the parts that catch costly mistakes, misuse by customers and obvious misbehaviour, because these make agents reliable enough to sell. It would be less likely to build the parts aimed at a model that is deliberately hiding its attacks: red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and responses to a catch that cost money, such as pausing. Accept other reasoned splits. 40 for parts a profit-only company would build, with the reason that they make the product more reliable or easier to sell. 20 of these 40 if the answer names such parts without a reason. 40 for parts it would skip, with the reason that they guard against a model hiding its attacks and cost money without helping sales. 20 of these 40 if the answer names such parts without a reason. 20 for a clear overall answer to whether it would build trusted monitoring anyway that fits the split, for example "partly". Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Partly. A profit-only company would build a monitor that flags costly mistakes, customer misuse and obvious misbehaviour, because that makes its agents reliable enough to sell. It would likely skip the parts aimed at a model that hides its attacks, such as red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and pausing after a catch, since these cost money and do not help sales."
feedback-instructions:: The learner applies Yonatan Cale's "would a profit-only company build it?" test to trusted monitoring. A good answer separates parts. A profit-only company would plausibly build monitors that catch costly mistakes, misuse by customers, and obvious misbehaviour, because these make agents reliable enough to sell. It would be less likely to build the parts aimed at a model that is deliberately hiding its attacks: red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and responses to a catch that cost money, such as pausing. Accept other reasoned splits. In 60 to 120 words, say what the answer got right and name the most important part it missed. One turn, then tell them to move on. No generic praise. If the learner is stuck, give one foothold: ask what the monitor would be catching in each case, an honest mistake or a hidden attack.

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
from:: "### A model of when and why research improves or hurts safety"
to:: Visually: near the initial pink point, the green slope is shallower than the red slope.

#### Question: Open
id:: e7765022-c4b3-4da6-b804-c4d1656d3f7e
force-feedback:: first
content::
\## What the replies say

Hobbhahn and Mallen both reply to Cale's worry, in different ways. What does each of them say to it?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be things that make AI more reliable for commercial use, which a profit-only company would build anyway, and which make AI more profitable to deploy. Marius Hobbhahn replies that good monitors may make consumer applications of AI more capable, but are quite unlikely to push the frontier, that the harm from developers outside the frontier companies coding faster is very small, and that such monitors push the frontier less than the hundreds of people at those companies who do that full-time, so "the risk is pretty low and the benefits are high". Alex Mallen argues that any research widens the set of safety and usefulness combinations developers can choose from, so what matters is which point developers then choose. Safety research usually makes them choose more safety, capabilities research less. He also says that widening the options can reduce the safety developers choose. 50: Hobbhahn's reply, that monitors are unlikely to push the frontier, so the extra capability they add is small next to their benefit. 50: Mallen's reply, that what matters is not whether the work makes AI more useful but which mix of safety and usefulness developers end up choosing. 25 of each 50 for a reply stated only partly. An answer that gives a reply to the wrong author earns the points for that reply's content, but loses 15 for each swap. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Hobbhahn says monitors are unlikely to push the frontier, so the risk is low and the benefit high. Mallen says any research widens the options, and what matters is which point developers choose: safety work usually leads them to choose more safety."
feedback-instructions:: The learner says what Hobbhahn and Mallen each reply to Cale's worry that monitors are things a profit-only company would build anyway, and that make AI more reliable and profitable. Hobbhahn's reply is empirical and specific: monitors built outside the frontier companies are unlikely to push the frontier, the harm from faster coding is small, and frontier companies have hundreds of people doing this anyway. Mallen's reply is a model: what matters is not whether research creates new options but which option developers choose. Safety research tends to make developers choose more safety, capabilities research less, though widening the options can also lower the safety they pick. If the learner mixes up the two authors, say so plainly and say which idea is whose. If the learner asks about their score, say plainly what earned and lost points. One or two turns, 60 to 120 words each. No generic praise. Do not say who is right.

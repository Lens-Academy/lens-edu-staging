---
id: '53ab5ec2-f9b3-476b-8db6-a6a93e56f099'
title: "Would a profit-only lab build it?"
reading_minutes: 16
tutor_minutes: 18
tldr: "Does control work speed up AI? Oliver Habryka worries that control pushes AI capabilities forward. Yonatan Cale asks whether a company that only cares about profit would build a safety tool anyway. Marius Hobbhahn, Alex Mallen and Caspar Oesterheld answer in different ways."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The neglectedness and acceleration criticism and three replies. First the learner reads Oliver Habryka in his 2024 dialogue with Ryan Greenblatt, 'How useful is AI Control as a framing on AI X-Risk?': control is 'incentivized to be constantly pushing the boundaries of making the system more capable', because its measure of success is how much useful work the AI systems do, the reasoning 'let's just make ourselves smarter' is opaque and easy to get wrong, and the new capabilities might shorten timelines more than they accelerate safety research, or be used to thwart a coordinated slowdown. Then the learner reads Yonatan Cale's comment (January 2026) on Marius Hobbhahn's post 'The case for AGI safety products', in full: Cale was considering building safety monitors himself, he is especially worried if a product automates large parts of technical AI safety work, he sees an upside in finding reproducible examples of misalignment at scale, and he says he is not against for-profit safety companies in general. His concern: safety monitors might in practice be 'things that make AI more reliable for using in a commercial context', and his test 'Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?'. Then Hobbhahn's reply, in full: monitors may make consumer applications more capable, but are unlikely to push the frontier, so 'the risk is pretty low and the benefits are high'. Then an excerpt of Alex Mallen's 'Capabilities research expands the safety-usefulness Pareto frontier too' (Redwood Research blog, 2 October 2026): any research widens the set of safety and usefulness combinations developers can choose from, so 'safety without hurting usefulness' is too weak a definition of safety research. What matters is which point developers choose. Safety research usually makes them choose more safety, capabilities research usually less. Then excerpts of Caspar Oesterheld's 'A simple argument about capabilities externalities versus opportunity costs' (LessWrong, 30 September 2026): if adding one generic safety researcher and one generic capabilities researcher is good, and deliberate capabilities work speeds capabilities more than a safety project does by accident, then a typical safety project's capabilities externalities are smaller than the opportunity cost of not doing other safety work. His own caveat: the argument does not cover externalities generic capabilities researchers do not care about, such as making AIs better at escaping control. The questions ask the learner to apply Cale's test to trusted monitoring, to sort Cale's criticism, to say what Hobbhahn's and Mallen's replies say to Cale, and to restate Oesterheld's argument and his caveat about control. All four are scored. Cale's criticism is mainly 'works but not worth the effort' (the work would happen anyway), with a 'makes things worse' side (more profitable AI, faster deployment). Do not tell the learner who is right."
---
#### Text
content::
Some safety work would get done even if nobody worried about catastrophe, because it also makes AI more useful to sell. Critics say that kind of work is not neglected, and that doing it may mostly speed AI up. Here are two versions of this criticism and three replies.

First, Oliver Habryka makes this criticism in a 2024 dialogue with Ryan Greenblatt about control. Greenblatt had just argued that "it's hard to compete with future AI researchers" on safety work, so a good plan is to keep early, useful AIs under control and have them do much of that work.

#### Article
source:: [[../articles/habryka-how-useful-is-ai-control-as-a-framing-on-ai-x-risk]]
from:: Like, a key dynamic that feels like its at play here
to:: would strongly push against such a slowdown?".

#### Text
content::
Yonatan Cale applies a version of this worry to monitors. In January 2026 Marius Hobbhahn posted [The case for AGI safety products](https://www.lesswrong.com/posts/iwfdwzJerpC7FqbZG/the-case-for-agi-safety-products), and Cale replied:

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

#### Question: Open
id:: 35de7efe-1ee7-443e-8fd2-8610ed47a447
force-feedback:: first
content::
\## Sort Cale's criticism

There are three kinds of criticism: control does not work, works but is not worth the effort, or works and makes things worse. Cale's criticism is of two of these kinds. Which two, and why?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be "things that make AI more reliable for using in a commercial context", asks whether a company that only cares about profit would build them anyway, and asks whether, without them, people would deploy AI less because unreliable AI is less profitable. The three kinds of criticism are: control does not work, works but is not worth the effort, works and makes things worse. Cale's criticism is mainly "works but is not worth the effort", because the work would happen anyway (it is not neglected), with a "makes things worse" side: monitors make AI more reliable and profitable, so people deploy more of it. 50 for "works but is not worth the effort", with the reason that a profit-only company would build such monitors anyway. 50 for the "makes things worse" side, with the reason that more reliable AI is more profitable and gets deployed more. Give 25 of each 50 if the kind is named without a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mainly 'works but is not worth the effort': a company that only cares about profit would build monitors anyway, so the work is not neglected. It also has a 'makes things worse' side: monitors make AI more reliable and profitable, so people deploy more of it."
feedback-instructions:: The learner is practising the unit's core skill: sorting a criticism. Reference points: Cale's criticism is mainly "works but not worth the effort" because the work would happen anyway (it is not neglected), with a "makes things worse" side: monitors make AI more reliable and profitable, so people deploy more of it. Accept another kind if the learner's reason fits Cale's comment. In at most four sentences, say whether the kind fits the reason and name any side they missed. One turn. No generic praise. Do not say whether Cale is right.

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

#### Text
content::
Caspar Oesterheld replies to the acceleration worry in general, for any safety project. Read his argument and one of his own caveats, which is about control.

#### Article
source:: [[../articles/oesterheld-a-simple-argument-about-capabilities-externalities-versus-opportunity-costs]]
from:: **TL;DR**: _Lots of people have the intuition
to:: but won’t render the project net negative.

#### Article
from:: It’s important to understand some things that the argument does _not_ say:
to:: will increase AIs’ ability to escape control schemes.

#### Question: Open
id:: 6eff9ad9-7894-4ce7-8972-6b5bfb42125c
force-feedback:: first
content::
\## Oesterheld's argument

Oesterheld argues that worries like Habryka's, that safety work speeds AI up, usually matter less than people think.

1. Explain his argument in a few sentences: what does he compare, and what follows from it?
2. He names one kind of side effect his argument does not cover, with an example about control. What is it?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Caspar Oesterheld argues from two premises. Premise 1: adding one generic safety researcher and one generic capabilities researcher to the world is good, because the safety researcher does more good than the capabilities researcher does harm (mainly since far more people work on capabilities than on safety). Premise 2: someone working deliberately on capabilities speeds capabilities up more than a safety project does by accident. Conclusion: a typical safety project's capabilities side effects are smaller than its opportunity cost, the good of doing some other generic safety project instead, so they will not make a project with typical upside net negative. His caveat: the argument is about generic capabilities that ordinary capabilities researchers push anyway (intelligence, economically valuable skills, AI research). It mostly does not cover side effects on capabilities they do not care about, such as making models better at taking over. His example: making AI better at control research might make AIs better at escaping control, and his argument does not answer that worry. Part 1, 60: 20 for premise 1, 20 for premise 2, 20 for the conclusion that the side effects are smaller than the cost of not doing other safety work. Part 1 does not need his letters or his button. Part 2, 40: 20 for the kind of side effect (capabilities that ordinary capabilities researchers do not care about, such as taking over or escaping control), 20 for his example: making AI better at control research could make AIs better at escaping control. A side effect that runs through faster progress in general (more profit, more investment, faster AI) is one his argument does cover, so it earns nothing in part 2. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Adding one safety and one capabilities researcher is good, and a capabilities researcher speeds AI up more than a safety project does by accident. So the project's side effects cost less than not doing some other safety work. But this only covers the capabilities everyone pushes anyway. It does not cover things like making AIs better at escaping control, which could happen if control work makes AIs better at control research."
feedback-instructions:: The learner restates Oesterheld's argument and his caveat. Premise 1: one generic safety researcher plus one generic capabilities researcher is a good deal. Premise 2: deliberate capabilities work speeds capabilities more than a safety project does by accident. Conclusion: a typical safety project's capabilities side effects are smaller than its opportunity cost. Caveat: the argument covers only generic capabilities, not ones capabilities researchers do not push, such as escaping control, and he names making AI better at control research as a case it does not answer. Name the strongest part of the answer, then the single most useful fix. If the learner asks about their score, say plainly what earned and lost points. If they say they do not understand, give one foothold: ask what pressing his button adds to the world. One or two turns, 60 to 120 words each. No generic praise. Do not say who is right.

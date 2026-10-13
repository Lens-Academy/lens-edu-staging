---
id: '53ab5ec2-f9b3-476b-8db6-a6a93e56f099'
title: "Would a profit-only lab build it?"
reading_minutes: 16
tutor_minutes: 20
tldr: "Does control work speed up AI? Oliver Habryka worries that control pushes AI capabilities forward. Yonatan Cale asks whether a company that only cares about profit would build a safety tool anyway. Marius Hobbhahn, Alex Mallen and Caspar Oesterheld answer in different ways."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. The neglectedness and acceleration criticism and three replies. First the learner reads Oliver Habryka in his 2024 dialogue with Ryan Greenblatt, 'How useful is AI Control as a framing on AI X-Risk?': control is 'incentivized to be constantly pushing the boundaries of making the system more capable', because its measure of success is how much useful work the AI systems do, the reasoning 'let's just make ourselves smarter' is opaque and easy to get wrong, and the new capabilities might shorten timelines more than they accelerate safety research, or be used to thwart a coordinated slowdown. Then the learner reads Yonatan Cale's comment (January 2026) on Marius Hobbhahn's post 'The case for AGI safety products', in full: Cale was considering building safety monitors himself, he is especially worried if a product automates large parts of technical AI safety work, he sees an upside in finding reproducible examples of misalignment at scale, and he says he is not against for-profit safety companies in general. His concern: safety monitors might in practice be 'things that make AI more reliable for using in a commercial context', and his test 'Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?'. Then Hobbhahn's reply, in full: monitors may make consumer applications more capable, but are unlikely to push the frontier, so 'the risk is pretty low and the benefits are high'. Then an excerpt of Alex Mallen's 'Capabilities research expands the safety-usefulness Pareto frontier too' (Redwood Research blog, 2 October 2026): any research widens the set of safety and usefulness combinations developers can choose from, so 'safety without hurting usefulness' is too weak a definition of safety research. What matters is which point developers choose. Safety research usually makes them choose more safety, capabilities research usually less. Then excerpts of Caspar Oesterheld's 'A simple argument about capabilities externalities versus opportunity costs' (LessWrong, 30 September 2026): if adding one generic safety researcher and one generic capabilities researcher is good, and deliberate capabilities work speeds capabilities more than a safety project does by accident, then a typical safety project's capabilities externalities are smaller than the opportunity cost of not doing other safety work. His own caveat: the argument does not cover externalities generic capabilities researchers do not care about, such as making AIs better at escaping control. The questions ask the learner to apply Cale's test to trusted monitoring, to sort Cale's criticism, to say whether Hobbhahn's or Mallen's reply answers Cale better, and whether Mallen or Oesterheld answers Habryka. All four are scored. Cale's criticism is mainly 'works but not worth the effort' (the work would happen anyway), with a 'makes things worse' side (more profitable AI, faster deployment). Do not tell the learner who is right."
---
#### Text
content::
Some safety work would get done even if nobody worried about catastrophe, because it also makes AI more useful to sell. Critics say that kind of work is not neglected, and that doing it may mostly speed AI up. Here are two versions of this criticism and three replies.

First, Oliver Habryka makes this criticism in a 2024 dialogue with Ryan Greenblatt about control. Greenblatt had just argued that "it's hard to compete with future AI researchers" on safety work, so a good plan is to keep early, useful AIs under control and have them do much of that work.

#### Article
source:: [[../articles/habryka-how-useful-is-ai-control-as-a-framing-on-ai-x-risk]]
from:: Like, a key dynamic that feels like its at play here
to:: would strongly push against such a slowdown?

#### Text
content::
Yonatan Cale puts a version of this worry to monitors. In January 2026 Marius Hobbhahn posted [The case for AGI safety products](https://www.lesswrong.com/posts/iwfdwzJerpC7FqbZG/the-case-for-agi-safety-products), and Cale replied:

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
from:: "### A model of when and why research improves or hurts safety"
to:: Visually: near the initial pink point, the green slope is shallower than the red slope.

#### Text
content::
Caspar Oesterheld replies to the acceleration worry in general, for any safety project. Read his argument and one of his own caveats, which is about control.

#### Article
source:: [[../articles/oesterheld-a-simple-argument-about-capabilities-externalities-versus-opportunity-costs]]
from:: Lots of people have the intuition that adding one generic safety researcher
to:: but won’t render the project net negative.

#### Article
from:: The above argument is about externalities on “generic capabilities”
to:: will increase AIs’ ability to escape control schemes.

#### Question: Open
id:: 917241f5-4296-469a-81f1-a96b9db5a54f
force-feedback:: first
content::
\## Apply the test

In Unit 1 you met trusted monitoring: a weaker, trusted model reads what a stronger, untrusted model does and flags suspicious actions for a human to check.

Put Cale's question to it.

1. Would a company that only cares about profit build trusted monitoring anyway?
2. Which parts of it would they build, and which parts would they skip?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be "things that make AI more reliable for using in a commercial context", and asks: "Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?" In trusted monitoring, a weaker, trusted model reads what a stronger, untrusted model does and flags suspicious actions for a human to check. A profit-only company would plausibly build the parts that catch costly mistakes, misuse by customers and obvious misbehaviour, because these make agents reliable enough to sell. It would be less likely to build the parts aimed at a model that is deliberately hiding its attacks: red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and responses to a catch that cost money, such as pausing. Accept other reasoned splits. 40 for parts a profit-only company would build, with the reason that they make the product more reliable or easier to sell. 20 of these 40 if the answer names such parts without a reason. 40 for parts it would skip, with the reason that they guard against a model hiding its attacks and cost money without helping sales. 20 of these 40 if the answer names such parts without a reason. 20 for a clear overall answer to whether it would build trusted monitoring anyway that fits the split, for example "partly". Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Partly. A profit-only company would build a monitor that flags costly mistakes, customer misuse and obvious misbehaviour, because that makes its agents reliable enough to sell. It would likely skip the parts aimed at a model that hides its attacks, such as red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and pausing after a catch, since these cost money and do not help sales."
feedback-instructions:: The learner applies Yonatan Cale's "would a profit-only company build it?" test to trusted monitoring. A good answer separates parts. A profit-only company would plausibly build monitors that catch costly mistakes, misuse by customers, and obvious misbehaviour, because these make agents reliable enough to sell. It would be less likely to build the parts aimed at a model that is deliberately hiding its attacks: red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and responses to a catch that cost money, such as pausing. Accept other reasoned splits. In 60 to 120 words, say what the answer got right and name the most important part it missed. One turn, then tell them to move on. No generic praise. If the learner is stuck, give one foothold: ask what the monitor would be catching in each case, an honest mistake or a hidden attack.

#### Question: Open
id:: 35de7efe-1ee7-443e-8fd2-8610ed47a447
force-feedback:: first
content::
\## Sort Cale's criticism

Which kind of criticism is Cale's: control does not work, works but is not worth the effort, or works and makes things worse? It may have more than one side.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be "things that make AI more reliable for using in a commercial context", asks whether a company that only cares about profit would build them anyway, and asks whether, without them, people would deploy AI less because unreliable AI is less profitable. The three kinds of criticism are: control does not work, works but is not worth the effort, works and makes things worse. Cale's criticism is mainly "works but is not worth the effort", because the work would happen anyway (it is not neglected), with a "makes things worse" side: monitors make AI more reliable and profitable, so people deploy more of it. 50 for "works but is not worth the effort", with the reason that a profit-only company would build such monitors anyway. 50 for the "makes things worse" side, with the reason that more reliable AI is more profitable and gets deployed more. Give 25 of each 50 if the kind is named without a reason. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mainly 'works but is not worth the effort': a company that only cares about profit would build monitors anyway, so the work is not neglected. It also has a 'makes things worse' side: monitors make AI more reliable and profitable, so people deploy more of it."
feedback-instructions:: The learner is practising the unit's core skill: sorting a criticism. Reference points: Cale's criticism is mainly "works but not worth the effort" because the work would happen anyway (it is not neglected), with a "makes things worse" side: monitors make AI more reliable and profitable, so people deploy more of it. Accept another kind if the learner's reason fits Cale's comment. In at most four sentences, say whether the kind fits the reason and name any side they missed. One turn. No generic praise. Do not say whether Cale is right.

#### Question: Open
id:: e7765022-c4b3-4da6-b804-c4d1656d3f7e
force-feedback:: first
content::
\## Weigh the replies

Hobbhahn and Mallen both reply to Cale's worry, in different ways. Which reply answers Cale better, and what does it still leave open?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be things that make AI more reliable for commercial use, which a profit-only company would build anyway, and which make AI more profitable to deploy. Marius Hobbhahn replies that good monitors may make consumer applications of AI more capable, but are quite unlikely to push the frontier, that the negative externalities of non-lab developers coding faster are very small, and that such monitors are unlikely to push the frontier more than the hundreds of employees who do that full-time, so "the risk is pretty low and the benefits are high". Alex Mallen argues that any research widens the set of safety and usefulness combinations developers can choose from, so what matters is which point developers choose. Safety research usually makes them choose more safety, capabilities research less. He also says that widening the options can reduce the safety developers choose. Either reply, or neither, can be the better answer. 30 for an accurate account of the reply the learner picks (or of both, if they pick neither) and how it bears on Cale's worry. 30 for a reason it answers Cale better than the other, for example that Hobbhahn speaks directly to monitors, or that Mallen turns the question into whether a given monitor mainly makes safety cheaper or mainly makes usefulness possible. 40 for what it still leaves open, for example that Hobbhahn does not address whether the parts that guard against scheming are the ones a profit-only company would skip, and that "unlikely to push the frontier" is his estimate, or that Mallen's reply depends on which point developers actually choose. 20 of these 40 for a gap that is vague or that the reply does address. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mallen's reply answers Cale better, because it turns his test into a sharper question: does a given monitor mainly make safety cheaper, so developers choose more safety, or mainly make new uses possible? Hobbhahn's reply rests on his estimate that monitors will not push the frontier. Mallen's still leaves open which point developers will actually choose, and he says himself that wider options can lower the safety they pick."
feedback-instructions:: The learner is practising the unit's core skill: weighing replies to a criticism. Cale's worry is that monitors are things a profit-only company would build anyway, and that they make AI more reliable and profitable, so people deploy more of it. Hobbhahn's reply is empirical and specific: monitors built outside the frontier companies are unlikely to push the frontier, the externality is faster coding, and frontier companies have hundreds of people doing this anyway. What it leaves open: he does not address whether the scheming-robust parts are what a profit-only company would skip, and "unlikely to push the frontier" is his estimate. Mallen's reply is a model: what matters is not whether research creates new options but which option developers choose. Safety research tends to make developers choose more safety, capabilities research less. Applied to Cale: the question becomes whether a given monitor mainly makes safety cheaper or mainly makes usefulness possible. Mallen also concedes that widening the options can lower the safety developers choose. A learner may find either reply better, or neither. Up to three turns. Per reply: steelman the learner's answer in two to four sentences, name one to three gaps, and ask up to two direct follow-up questions. If stuck after two attempts, give a short direct answer and move on. Do not say who is right overall. 80 to 150 words per reply. No generic praise. If the learner says they do not understand, give one foothold from the material, such as Mallen's sentence "developers have to choose a particular point on the Pareto frontier". If they still do not attempt it, rephrase the question in other words.

#### Question: Open
id:: 21539292-c528-4ac9-b35c-4cbaeed9f566
force-feedback:: first
content::
\## Does either reply answer Habryka?

Habryka worries that control work keeps pushing AI systems to be more capable, and that the new capabilities could shorten timelines or be used to block a coordinated slowdown.

1. Does Mallen's reply or Oesterheld's reply answer this worry?
2. Say what each one answers and what it leaves open.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Oliver Habryka worries that control is measured by how much useful work the controlled AIs do, so the field is pushed to keep making the systems more capable, and that the new capabilities may shorten timelines more than they speed up safety research, or be used to block a coordinated slowdown. Alex Mallen argues that what matters is which point on the safety and usefulness frontier developers choose, and that safety research usually moves that choice towards more safety. Caspar Oesterheld argues that for a typical safety project, the capabilities externalities are smaller than the opportunity cost of not doing other safety work, because deliberate capabilities work speeds capabilities up more than a safety project does by accident. He says specific information about a project can override this, and that his argument does not cover externalities that generic capabilities researchers do not care about, such as making AIs better at escaping control. Any conclusion (one reply works, both partly work, or neither does) is fine if reasoned. 25 for what Mallen's reply answers, for example that whether new options are harmful depends on which point developers choose. 25 for what it leaves open, for example that Habryka's worry is that control's own measure of success pushes towards choosing more capability, so the reply depends on how developers actually choose. 25 for what Oesterheld's reply answers: for a typical safety project, the speed-up is smaller than the cost of not doing other safety work. 25 for what it leaves open, any one of these: it is an argument from priors that specific information can override, and Habryka gives a specific mechanism for control, or it is about speed, not about capabilities used to block a slowdown. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Mallen answers part of it: new options are not harmful in themselves, what matters is which point developers pick. But Habryka's point is that control's own measure of success pushes towards picking more capability, so Mallen's answer depends on how developers actually choose. Oesterheld answers the speed part for a typical project, since deliberate capabilities work speeds things up more. But he argues from priors, Habryka names a specific mechanism for control, and neither reply covers capabilities used to block a slowdown."
feedback-instructions:: The learner weighs two replies against Oliver Habryka's acceleration worry. Habryka's worry has two parts: control is measured by how much useful work the controlled AIs do, so the field is pushed to keep scaling capabilities, and the new capabilities may shorten timelines more than they speed up safety research, or be used by those with early access to block a coordinated slowdown. Reference points, accept other reasoned answers. Mallen: what matters is which safety and usefulness point developers choose, and safety research usually moves that choice towards safety. This speaks to whether control widens the options in a harmful way, but Habryka's worry is that control's own success measure pushes towards choosing more capability, so Mallen's reply depends on how developers actually choose. Oesterheld: for a typical, generic researcher, the capabilities externalities of a safety project are smaller than the opportunity cost of not doing other safety work, because deliberate capabilities work speeds capabilities more than safety work does by accident. Open questions: his argument is from priors and he says specific information about a project can override it, Habryka gives a specific mechanism for control, and the argument is about speed, not the coordination point (capabilities used to block a slowdown). Oesterheld also says his argument does not cover making AIs better at escaping control. A learner may conclude that one reply works, both partly work, or neither does. One or two turns, 80 to 150 words each. Name the strongest part of their answer and the most important thing it missed. No generic praise. Do not say who is right. If the learner is stuck, give one foothold: ask which part of Habryka's worry is about speed and which is about who holds the new capabilities.

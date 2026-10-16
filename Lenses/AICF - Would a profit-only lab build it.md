---
id: '53ab5ec2-f9b3-476b-8db6-a6a93e56f099'
title: "Would a profit-only lab build it?"
reading_minutes: 5
tutor_minutes: 9
tldr: "Yonatan Cale asks whether a company that only cares about profit would build a safety tool anyway. If so, the work is not neglected and may mostly speed AI up. Marius Hobbhahn answers."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Does control make things worse?', third lens of the submodule on the criticism that control speeds up AI without making it safer in the long run. The learner reads Yonatan Cale's comment (January 2026) on Marius Hobbhahn's post 'The case for AGI safety products', in full: Cale was considering building safety monitors himself, he is especially worried if a product automates large parts of technical AI safety work, he sees an upside in finding reproducible examples of misalignment at scale, and he says he is not against for-profit safety companies in general. His concern: safety monitors might in practice be 'things that make AI more reliable for using in a commercial context', and his test 'Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?'. Then Hobbhahn's reply, in full: monitors may make consumer applications more capable, but are unlikely to push the frontier, so 'the risk is pretty low and the benefits are high'. Earlier lenses in the submodule: Richard Ngo's general version and Caspar Oesterheld's general reply, then Habryka's and Bushnaq's control-specific versions with Buck's answer and Alex Mallen's model. Do not tell the learner who is right."
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
2. Which parts, if any, would they skip? Say why.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be "things that make AI more reliable for using in a commercial context", and asks: "Could this project also be built by the capabilities team of [some AGI company that doesn't care about safety beyond what they need for making money]?" In trusted monitoring, a weaker, trusted model reads what a stronger, untrusted model does and flags suspicious actions for a human to check. A profit-only company would plausibly build the parts that catch costly mistakes, misuse by customers and obvious misbehaviour, because these make agents reliable enough to sell. It would be less likely to build the parts aimed at a model that is deliberately hiding its attacks: red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and responses to a catch that cost money, such as pausing. Accept other reasoned splits. 40 for parts a profit-only company would build, with a reason, for example that they make the product more reliable or easier to sell. 20 of these 40 if the answer names such parts without a reason. 40 for which parts, if any, it would skip, with a reason, for example parts that guard against a model hiding its attacks and cost money without helping sales. An argued case that it would build all of it (for example because a scheming agent sabotaging customers' work is a costly liability) also earns these 40. 20 of these 40 if parts are named without a reason. 20 for a clear overall answer to whether it would build trusted monitoring anyway that fits the rest of the answer. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Partly. A profit-only company would build a monitor that flags costly mistakes, customer misuse and obvious misbehaviour, because that makes its agents reliable enough to sell. It would likely skip the parts aimed at a model that hides its attacks, such as red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and pausing after a catch, since these cost money and do not help sales."
feedback-instructions:: The learner applies Yonatan Cale's "would a profit-only company build it?" test to trusted monitoring. A good answer separates parts. A profit-only company would plausibly build monitors that catch costly mistakes, misuse by customers, and obvious misbehaviour, because these make agents reliable enough to sell. It would be less likely to build the parts aimed at a model that is deliberately hiding its attacks: red-team evaluations that assume the model is scheming, auditing budgets for rare subtle attacks, and responses to a catch that cost money, such as pausing. Accept other reasoned splits. In 60 to 120 words, say what the answer got right and name the most important part it missed. One turn, then tell them to move on. No generic praise. If the learner is stuck, give one foothold: ask what the monitor would be catching in each case, an honest mistake or a hidden attack.

#### Text
content::
Hobbhahn answered:

#### Article
source:: [[../articles/hobbhahn-comment-on-the-case-for-agi-safety-products]]

#### Question: Open
id:: e7765022-c4b3-4da6-b804-c4d1656d3f7e
force-feedback:: first
content::
\## Hobbhahn's reply

1. What is Hobbhahn's reply to Cale?
2. Does it answer Cale's test when you apply it to trusted monitoring? Why or why not?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Yonatan Cale worries that safety monitors might in practice be things that make AI more reliable for commercial use, which a company that only cares about profit would build anyway, and which make AI more profitable to deploy. Marius Hobbhahn replies that good monitors may make consumer applications of AI more capable, but are quite unlikely to push the frontier, that the harm from developers outside the frontier companies coding faster is very small, and that such monitors push the frontier less than the hundreds of people at those companies who do that full-time, so "the risk is pretty low and the benefits are high". Part 1, 40: Hobbhahn's reply, that monitors are unlikely to push the frontier, so the extra capability they add is small next to their benefit. 20 of these 40 if stated only partly. Part 2, 60: a reasoned judgement, and either verdict earns full marks with a fitting reason. Reasons it answers Cale: even if the monitor makes AI more usable, the push to the frontier is small next to what frontier companies do anyway; the parts that matter for safety are the ones a profit-only company would skip, so building them is not wasted. Reasons it does not: Cale's test is about neglectedness, whether the work would happen anyway, and Hobbhahn answers a different question, whether it speeds AI up; monitors that make agents reliable enough to deploy can speed adoption even without pushing the frontier. 30 of these 60 for a verdict with a generic reason or none. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Hobbhahn says monitors are unlikely to push the frontier, so the risk is low and the benefit high. For trusted monitoring that only partly answers Cale. It shows the speed-up is small, but Cale also asks whether a profit-only company would build it anyway, and for the parts that catch ordinary mistakes the answer is yes, so safety people add little there."
feedback-instructions:: The learner states Hobbhahn's reply to Cale and judges whether it answers Cale's test for trusted monitoring. Hobbhahn: monitors are unlikely to push the frontier, the harm from faster coding outside frontier companies is small, so "the risk is pretty low and the benefits are high". A key point to look for: Cale asks two things, whether a profit-only company would build it anyway (neglectedness) and whether it makes AI more profitable to deploy; Hobbhahn mainly answers the second. Either verdict is fine if reasoned. Name the strongest part, then the single most useful fix. If the learner asks about their score, say plainly what earned and lost points. One or two turns, 60 to 120 words each. No generic praise. Do not say who is right.

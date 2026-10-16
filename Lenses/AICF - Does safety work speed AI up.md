---
id: 'd02212a1-7fa5-4f3e-aa08-ebd5e1485666'
title: "Does safety work speed AI up?"
reading_minutes: 7
tutor_minutes: 13
tldr: "The criticism: safety work speeds AI up without making it safer. Richard Ngo argues this about a decade of alignment research, including the push to have AIs do alignment research, which is what control is meant to make safe. Caspar Oesterheld argues that such side effects usually matter less than people think, with one caveat about control."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Even done well, does control make things worse?', first lens of the submodule on the criticism that control speeds up AI without making it safer in the long run. The learner reads two excerpts from Richard Ngo's 'What just happened? Pragmatism and pessimization' (LessWrong, August 2026). (1) The first paragraph: alignment researchers played a major role in advancing AI capabilities over the last decade, so the line between alignment and capabilities research lost most of its meaning, and a 'pragmatic alignment' paradigm helped OpenAI, DeepMind and Anthropic push toward AGI 'under the banner of safety'. A Lens text then glosses scalable oversight and recursive self-improvement. (2) His passage on two current examples: scalable oversight for grading unverifiable tasks may be the next capabilities bottleneck, and Anthropic's push toward 'automating alignment research' is very similar to making models better at capabilities research and will predictably speed up recursive self-improvement. Ngo's post is about alignment research in general, not control. The link the lens draws: control is meant to let companies get useful work, including alignment research, out of AIs they cannot yet trust, so Ngo's worry is a version of the 'makes things worse' criticism through faster capabilities, whose control-specific versions (Habryka, Bushnaq, Cale) follow in the next lenses. Then excerpts of Caspar Oesterheld's 'A simple argument about capabilities externalities versus opportunity costs' (LessWrong, 30 September 2026): if adding one generic safety researcher and one generic capabilities researcher is good, and deliberate capabilities work speeds capabilities more than a safety project does by accident, then a typical safety project's capabilities externalities are smaller than the opportunity cost of not doing other safety work. His own caveat: the argument does not cover side effects on capabilities that capabilities researchers do not push, and his example is that making AI better at control research might make AIs better at escaping control. Two questions. Do not tell the learner who is right."
---
#### Text
content::
**The criticism: control speeds up AI without making it safer in the long run.** Before the versions aimed at control, here is the general worry. Richard Ngo, who used to work at DeepMind and OpenAI, argues it about alignment research in general: much of it, he says, helped AI companies race toward AGI, AI as capable as humans across the board, "under the banner of safety". His post is not about control. But control's main pitch is that it lets companies get useful work, including alignment research, out of AIs they cannot yet trust. This submodule has three lenses: this general version with a general reply, then a version aimed at control with Redwood's answer, then the question whether a company that only cares about profit would build control anyway.

Read the first paragraph of Ngo's post.

#### Article
source:: [[../articles/ngo-what-just-happened-pragmatism-and-pessimization]]
from:: This post is about the major role alignment researchers played
to:: like authors Sebastian Mallaby and Karen Hao.[^cite-3]

#### Text
content::
Ngo then goes through the work of OpenAI, DeepMind and Anthropic, and ends with two current examples of work that blurs the line between alignment and capabilities. Two terms in it:
- **Scalable oversight:** methods for humans to check AI work that is too hard for them to check directly, for example with the help of other AIs.
- **Recursive self-improvement:** AIs doing the research that makes the next AIs better, which could speed progress up more and more.

#### Article
from:: I’ll briefly flag two ongoing examples of the latter.
to:: aimed specifically towards improving conceptual reasoning](https://alignment.anthropic.com/2026/conceptual-reasoning-index/)).

#### Question: Open
id:: 0637f06f-86e5-47d5-9aa5-83e16c65fff0
force-feedback:: first
content::
\## Does Ngo's worry apply to control?

Control is meant to let companies use AIs they cannot yet trust, for example to automate alignment research: have AIs do research on making AI safe. Does Ngo's worry about automating alignment research apply to control? Give one reason it does and one reason it might not.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Richard Ngo argues that much alignment research helped AI companies race toward AGI under the banner of safety, and that automating alignment research is very similar to making models better at capabilities research, so it will speed up recursive self-improvement. Control is meant to let companies get useful work, including alignment research, out of AIs they cannot yet trust. 50: a reason the worry applies, for example: control is what would make it acceptable to hand alignment research to untrusted AIs, so it helps the very automation Ngo worries about; control work happens inside AI companies and can lend their push for more capable AI the label of safety; it makes powerful AI more useful and so speeds up AI progress. 50: a reason it might not apply, for example: control does not make models more capable, it limits what they can do and adds cost; companies may automate research anyway, so the speed-up would happen with or without control and control only makes it safer; control can catch an AI sabotaging the work, which gives evidence about risk rather than only speed. Give 25 of either 50 for a reason that is only asserted or would fit any safety work without saying why. Give credit for any reason that fits, in any wording. Do not reward or penalise a verdict. Model answer, for the feedback, not a grading checklist: "It applies because control is exactly what would let a company hand alignment research to AIs it cannot trust yet, and Ngo thinks that work speeds up capabilities. It might not, because control itself does not make the AI any smarter; a company racing to automate research would do it anyway, and control at least makes it safer and can catch sabotage."
feedback-instructions:: One turn, 50 to 100 words. Say whether each of the two reasons holds up and, if one is missing or generic, give one example of what would fit. Ngo's post is about alignment research in general, so a learner who argues the analogy to control is weak has a point if they say why. No generic praise. Do not say who is right.

#### Text
content::
Caspar Oesterheld replies to this worry in general, for any safety project. Read his argument and one of his own caveats, which is about control.

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

Oesterheld argues that worries like Ngo's, that safety work speeds AI up, usually matter less than people think.

1. Explain his argument in a few sentences: what does he compare, and what follows from it?
2. Does his argument answer Ngo's worry about automating alignment research? Use his premises or his list of what the argument does not say.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Caspar Oesterheld argues from two premises. Premise 1: adding one generic safety researcher and one generic capabilities researcher to the world is good, because the safety researcher does more good than the capabilities researcher does harm. Premise 2: someone working deliberately on capabilities speeds capabilities up more than a safety project does by accident. Conclusion: a typical safety project's capabilities side effects are smaller than its opportunity cost, the good of doing some other generic safety project instead, so they will not make a project with typical upside net negative. His caveat: the argument is about generic capabilities that ordinary capabilities researchers push anyway (intelligence, economically valuable skills, AI research). It mostly does not cover side effects on capabilities they do not care about, such as making models better at taking over. His example: making AI better at control research might make AIs better at escaping control, and his argument does not answer that worry. Part 1, 60: 20 for premise 1, 20 for premise 2, 20 for the conclusion that the side effects are smaller than the cost of not doing other safety work. Part 2, 40: a reasoned verdict on whether the argument answers Ngo's worry; either side earns full marks with a fitting reason. Reasons it does not: Ngo says automating alignment research is "extremely similar" to capabilities research, so premise 2 (a safety project speeds capabilities less than deliberate capabilities work) may fail for it; Oesterheld's own caveat says the argument does not cover making AIs better at control research, which may make them better at escaping control; the argument rests on what is typical, and known details of a project can override it. Reasons it does: even automated alignment research probably speeds capabilities less than the people deliberately working on capabilities, so the opportunity cost still dominates. 20 of these 40 for a verdict with a generic reason or none. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Adding one safety and one capabilities researcher is good, and a capabilities researcher speeds AI up more than a safety project does by accident. So a safety project's side effects cost less than not doing some other safety work. But this does not answer Ngo well: he says automating alignment research is almost the same as capabilities research, so premise 2 may fail, and Oesterheld himself says his argument does not cover making AIs better at control research."
feedback-instructions:: The learner restates Oesterheld's argument and judges whether it answers Ngo's worry about automating alignment research. Premise 1: one generic safety researcher plus one generic capabilities researcher is a good deal. Premise 2: deliberate capabilities work speeds capabilities more than a safety project does by accident. Conclusion: a typical safety project's capabilities side effects are smaller than its opportunity cost. Caveat: the argument covers only generic capabilities, not ones capabilities researchers do not push, and he names making AI better at control research as a case it does not answer. Either verdict on part 2 is fine if reasoned; a strong 'no' notes that Ngo calls automating alignment research extremely similar to capabilities research, which threatens premise 2. Name the strongest part of the answer, then the single most useful fix. If the learner asks about their score, say plainly what earned and lost points. If they say they do not understand, give one foothold: ask what pressing his button adds to the world. One or two turns, 60 to 120 words each. No generic praise. Do not say who is right.

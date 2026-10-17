---
id: 'd02212a1-7fa5-4f3e-aa08-ebd5e1485666'
title: "Does safety work speed AI up?"
reading_minutes: 12
tutor_minutes: 13
tldr: "The criticism: safety work speeds AI up without making it safer. Richard Ngo argues this about a decade of alignment research, including today's push to build automated alignment researchers, the kind of work control is meant to make safe. Caspar Oesterheld argues that such side effects usually matter less than people think, with one caveat about control."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Even done well, control makes things worse', first of three lenses on the criticism that control speeds up AI without making it safer in the long run. The learner reads the opening of Richard Ngo's 'What just happened? A retrospective of AI alignment' (LessWrong, August 2026), post 1 of his series: the alignment community planned to differentially advance alignment over capabilities but has mostly pushed the world the opposite way, while parts of it gained power; Ngo cares about this more than about the effects of faster capabilities, because the integrity of a few decision-makers will shape the coming decades; four ongoing mistakes (convincing the US government to take AGI seriously, alignment research very similar to capabilities-maximizing research, especially building automated alignment researchers, trusting Anthropic too much, trading clarity about politics for conformity); the pattern of 'jumping down the slippery slope' (treating an outcome as inevitable, as in Sam Altman's 'if it's going to happen anyway' email, and so pushing it along), driven by reasoning about marginal individual impact and by fear. Ngo's series criticizes the alignment field in general, not control by name; the lens says control might be exactly one of the agendas he warns about (control is meant to let companies get useful work, including alignment research, out of AIs they cannot yet trust). His worry is a version of the 'makes things worse' criticism through faster capabilities, whose control-specific versions (Bushnaq, with Habryka in an optional box, and Cale) follow in the next lenses. Then excerpts of Caspar Oesterheld's 'A simple argument about capabilities externalities versus opportunity costs' (LessWrong, 30 September 2026): if adding one generic safety researcher and one generic capabilities researcher is good, and deliberate capabilities work speeds capabilities more than a safety project does by accident, then a typical safety project's capabilities externalities are smaller than the opportunity cost of not doing other safety work. His own caveat: the argument does not cover side effects on capabilities that capabilities researchers do not push, and his example is that making AI better at control research might make AIs better at escaping control. Two questions. The lens ends with cards to two reading lenses with Ngo's posts 1 and 2 in full, recommended if the learner has time. Do not tell the learner who is right."
---
#### Text
content::
**The criticism: control speeds up AI without making it safer in the long run.**

Richard Ngo, who used to work at DeepMind and OpenAI, argues that much alignment research helped AI companies race toward AGI "under the banner of safety", thereby causing the opposite of what they intended.

His message is a general criticism of the alignment field, but control might be exactly one of the agendas he is warning about.

While you read, look for the pattern behind the mistakes Ngo describes, and ask yourself whether control work could fall into it.

#### Article
source:: [[../articles/ngo-what-just-happened-a-retrospective-of-ai-alignment]]
from:: This sequence is about the last decade in AI alignment.
to:: The main thing blocking us is our inability to learn from our past mistakes.

#### Question: Open
id:: 0637f06f-86e5-47d5-9aa5-83e16c65fff0
force-feedback:: first
content::
\## Does Ngo's worry apply to control?

Ngo worries that alignment research has helped AI companies race, and names building automated alignment researchers as an example. Does his worry apply to control? Give one reason it does and one reason it might not.
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Richard Ngo argues that much alignment research helped AI companies race toward AGI under the banner of safety, and that much of today's alignment research is very similar to capabilities-maximizing research, especially building automated alignment researchers. Control is meant to let companies get useful work, including alignment research, out of AIs they cannot yet trust. 50: a reason the worry applies, for example: control is what would make it acceptable to hand alignment research to untrusted AIs, so it helps the very automation Ngo worries about; control work happens inside AI companies and can lend their push for more capable AI the label of safety; it makes powerful AI more useful and so speeds up AI progress. 50: a reason it might not apply, for example: control does not make models more capable, it limits what they can do and adds cost; companies may automate research anyway, so the speed-up would happen with or without control and control only makes it safer; control can catch an AI sabotaging the work, which gives evidence about risk rather than only speed. Give 25 of either 50 for a reason that is only asserted or would fit any safety work without saying why. Give credit for any reason that fits, in any wording. Do not reward or penalise a verdict. Model answer, for the feedback, not a grading checklist: "It applies because control is exactly what would let a company hand alignment research to AIs it cannot trust yet, and Ngo thinks that work speeds up capabilities. It might not, because control itself does not make the AI any smarter; a company racing to automate research would do it anyway, and control at least makes it safer and can catch sabotage."
feedback-instructions:: One turn, 50 to 100 words. Say whether each of the two reasons holds up and, if one is missing or generic, give one example of what would fit. Ngo's series is about alignment research in general, so a learner who argues the analogy to control is weak has a point if they say why. No generic praise. Do not say who is right.

#### Text
content::
If you have time, we highly recommend reading Richard Ngo's whole series. The parts published so far:

::card[[../Lenses/AICF - Ngo - A retrospective of AI alignment]]

> Post 1: the whole post you read the opening of, about how early alignment thinking and its engagement with Silicon Valley backfired.

::card[[../Lenses/AICF - Ngo - Pragmatism and pessimization]]

> Post 2: how alignment research at OpenAI, DeepMind and Anthropic pushed AI capabilities forward, and what he thinks the field should do instead.

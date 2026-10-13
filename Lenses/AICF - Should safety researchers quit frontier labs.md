---
id: '7612af35-19b6-4a4f-ac67-f8fbb87e11b6'
title: "Should safety researchers quit frontier labs?"
tldr: "If safety work at AI companies prevents the warning shots that could win a pause, should safety researchers leave? Ryan Kidd states the argument and his replies, and commenters from inside and outside OpenAI push in both directions."
summary_for_tutor: "Lens in Unit 5 of AI Control Fundamentals. The learner reads Ryan Kidd's LessWrong post 'Should safety researchers quit frontier labs re. warning shots?' (September 2026) and three comments. Kidd states the argument in three parts: prosaic safety work (control, scalable oversight, interpretability) may not scale and may mask deeper failures, it may block non-lethal warning shots such as the Hugging Face incident, and warning shots help build support for a pause, so safety staff should consider quitting. He grants it some merit, then replies: aligned or controlled AIs may still be needed for research during a pause, less careful companies will cause warning shots anyway, responses to past warning shots varied (Chernobyl, Hiroshima, COVID), a pause needs safety researchers, the next warning shot might be lethal, and allowing harm for the greater good is morally fraught. His addendum sets aside other arguments against lab safety work (making AI more deployable, safety-washing, accelerating capabilities, legitimising labs), and he discloses he is CEO of MATS, so has an incentive to find the argument wrong. Comments: Boaz Barak, who says he is biased as a member of OpenAI's alignment team, says to strongly suspect any argument of the form 'make the situation worse now so it can be better later' and that the next warning shot cannot be controlled. Leo Gao replies to Barak that there is a difference between aiming to increase harm and not maximally reducing it in order to uphold another principle, for example not mitigating harms when that would stop recklessness from being properly punished. orthonormal agrees 'worse is better' is a bad category of argument but says a better one is that much prosaic safety work has hidden misalignment in released models rather than making them more robustly aligned. Questions: which of Kidd's replies is strongest and weakest, and two scored questions about a control researcher who stops building blocking monitors but stays at the lab: whether Gao's line allows that choice and whether Barak would still object, and what orthonormal's view means such a researcher should work on instead. Do not tell the learner whether anyone should quit."
reading_minutes: 10
tutor_minutes: 13
---
#### Text
content::
The warning-shot argument has a practical form: if safety work at AI companies prevents the incidents that might win support for a pause, maybe safety researchers should leave. Ryan Kidd, who runs a programme that trains safety researchers, sets out that argument and his replies to it. He states his conflict of interest at the end.

#### Article
source:: [[../articles/kidd-should-safety-researchers-quit-frontier-labs-re-warning-shots]]

#### Question: Open
id:: 8dc508aa-4c3f-463a-9319-9b6a6d8048b6
force-feedback:: first
content::
Which of Kidd's replies do you find strongest, and which weakest? Say why in a sentence or two each.
placeholder:: A sentence or two for each.
feedback-instructions:: The learner read Ryan Kidd's post and is ranking his replies to the argument that safety researchers should quit frontier labs to allow warning shots. His replies: aligned or controlled AIs may be needed for research during a pause, less careful companies will cause warning shots anyway, responses to past warning shots varied (Chernobyl, Hiroshima, COVID), a pause needs safety researchers to use it, the next warning shot might be lethal, and allowing harm for the greater good is morally fraught. Any ranking is fine if the reasons hold. Check each reason: does it engage with the argument's premises, or only restate a conclusion? If they call a reply weak, ask what the other side would need to show to defeat it. If they call a reply strong, mention in one sentence the strongest response a critic could make (for example, to "stragglers will cause warning shots anyway": a warning shot from a careless company may be dismissed as that company's fault). At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say whether anyone should quit.

#### Text
content::
Here are three comments on the post. Boaz Barak, who says he works on OpenAI's alignment team, comments on it, and Leo Gao replies to him. A commenter called orthonormal replies to Kidd directly, a day before Barak's comment.

#### Article
source:: [[../articles/barak-comment-on-should-safety-researchers-quit-frontier-labs-re-warning-shots]]

#### Article
source:: [[../articles/leogao-comment-on-should-safety-researchers-quit-frontier-labs-re-warning-shots]]

#### Article
source:: [[../articles/orthonormal-comment-on-should-safety-researchers-quit-frontier-labs-re-warning-shots]]

#### Question: Open
id:: 47d37df0-405b-4df3-9a0c-bbb7b8b71280
force-feedback:: first
content::
Barak says we should be very suspicious of any argument that we should make things worse now so they can be better later. Leo Gao, replying to Barak, accepts that, but still thinks something in the quitting argument survives. Take a control researcher at a frontier lab who stops building monitors that block an AI's dangerous actions, but stays at the lab. Gao draws a line between causing harm and failing to prevent all of it. Does that line allow this choice? Would Barak still object?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: Boaz Barak says to strongly suspect any argument that you should make the situation worse now so it can be better later, because people who try usually succeed only at the first part, and because nobody can control how harmful the next warning shot would be. Leo Gao agrees it would be bad to try to cause warning shots, but distinguishes aiming to increase harm from not reducing harm as much as possible in order to uphold another principle, for example not mitigating harms when that would stop recklessness from being properly punished. 55: Gao applied to the researcher: his line could allow the choice if the aim is to uphold another principle, such as not shielding the company from the consequences of its own recklessness, and not if the aim is to let incidents happen so they become warning shots. Either verdict earns the 55 when it is argued from that distinction. 45: Barak would still object, because the choice makes things less safe now in the hope of a better later, and nobody can control how bad the next incident would be. A reasoned argument that he would not object also earns these 45. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Gao's line could allow it if the researcher stops in order not to cover for a reckless company, not in order to cause incidents. Barak would still object, because it makes things less safe now in the hope of a better later, and nobody can control how bad the next incident would be."
feedback-instructions:: The learner applies Barak's comment and Leo Gao's reply to a researcher who stops building blocking monitors but stays at the lab. Gao: there is a difference between aiming to increase harm and declining to reduce it as much as possible in order to uphold another principle, for example not shielding a company from the consequences of its own recklessness, so his line may allow the choice depending on why the researcher makes it, but not if the aim is to let incidents happen. Barak: suspect any "make it worse now so it is better later" argument, and the next warning shot cannot be controlled, though he also says a researcher who does not feel their work matters should look elsewhere. Accept other reasoned readings. At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say whether anyone should quit.

#### Question: Open
id:: 5055a20c-7ac3-414d-96ce-9968aefd6604
force-feedback:: first
content::
orthonormal, writing a day before Barak, also agrees that "make things worse now so they can be better later" is a bad kind of argument, but still thinks something in the quitting argument survives. Take again the control researcher who stays at a frontier lab. If orthonormal is right that much safety work hid misalignment instead of fixing it, what should a researcher who stays work on instead?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: orthonormal agrees that 'worse is better' is a bad kind of argument, but says much prosaic safety work at frontier labs hid misalignment in released models rather than making them more robustly aligned, and that if researchers had refused to keep patching surface problems, commercial progress would have been halted. 60: what a researcher who stays should work on: work that makes models actually more robustly aligned, or work that detects misalignment and makes it visible. 40: why: fixes that only patch surface problems hide the misalignment, which is what orthonormal objects to. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "If orthonormal is right, a researcher who stays should work on making models actually aligned and on finding and reporting misalignment, not on patches that only hide it, because hiding it is what made the earlier safety work a problem."
feedback-instructions:: The learner applies orthonormal's comment to a control researcher who stays at a frontier lab. orthonormal agrees that "worse is better" is a bad kind of argument, but says the problem is safety work that hid misalignment in released models instead of making them more robustly aligned, so a researcher who stays should favour robust alignment, detection and disclosure over surface fixes. Accept other reasoned readings. If the learner merges orthonormal's point with Gao's line between causing harm and not preventing all of it, ask how they differ. At most two replies, 60 to 120 words each, no lists, no generic praise. Do not say whether anyone should quit.

---
id: 'ce6ffe68-5c14-4150-8257-1666326e81cf'
title: "Slop, not scheming"
reading_minutes: 15
tutor_minutes: 11
tldr: "The criticism: control guards against the wrong danger. John Wentworth argues that scheming in early AI is a small slice of the risk, and that the likely way we lose is early AI producing alignment work that looks right and is not. Buck Shlegeris replies."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Even done well, control isn't worth the effort', submodule on the criticism that control guards against the wrong danger. The learner reads John Wentworth's 'The Case Against AI Control Research' (LessWrong, January 2025) in full, then Buck Shlegeris's reply in full (control deserves a substantial share of safety effort because stopping scheming early transformative AI from extreme subversion is 'quite robustly good', getting useful research out of scheming AIs is in scope for control, and his nitpicks that control techniques probably also reduce risk for 'moderately superintelligent' models and that some non-scheming threat models are addressed as a special case). Wentworth's claim: control only targets scheming in early transformative AI, and that is a small slice of the risk. The median doom path is slop: early AI produces alignment work that looks fine and is not, and the lab believes it has solved the problem. Wentworth does not say control backfires; he says the effort would do more good elsewhere. Do not tell the learner who is right."
---
#### Text
content::
**The criticism: control guards against the wrong danger.** Control aims to stop early AIs that scheme. John Wentworth argues that this is a small slice of the risk, and that the likely way we lose is different: early AI produces alignment work that looks right and is not.

Wentworth wrote this in January 2025. He starts by quoting the case for control you read in Unit 1. Read it, then Buck Shlegeris's reply from the discussion under it.

Some terms in the post:
- **X-risk:** existential risk.
- **Probability mass:** a share of the total probability. "A small slice of the probability mass" means a small share of the ways things could go wrong.
- **OOMs:** orders of magnitude (factors of ten).
- **Inference-time compute:** computing power a model uses while answering, as opposed to while being trained.
- **Prosaic alignment:** alignment work on AI built the way it is built today.
- **Model organisms:** AIs deliberately built to show a failure, so it can be studied.

#### Article
source:: [[../articles/wentworth--the-case-against-ai-control-research]]

#### Question: Open
id:: d9b30556-078c-463a-979d-bc8123ac8fcf
force-feedback:: first
content::
\## Recall

In your own words: what does Wentworth think control research covers, and how does he think things most likely go wrong instead?
assessment-instructions:: Score out of 100. Context for grading: John Wentworth argues that control research, as he describes it, covers only intentional deception or scheming, and only in early transformatively useful AI, roughly human-level, not more powerful AI. His core claim is that scheming in early AI is a relatively small slice of existential risk, so control does little about it. Most risk comes from later, stronger AI such as superintelligence, and the main job of early AI is to help solve the alignment problems of that stronger AI. His median path to doom is slop, not scheming: early AI produces alignment work that looks fine at first glance but is wrong, alignment for superintelligence is hard to verify because you cannot test it without building it, and the lab believes it has solved the problem, implements the non-solution and scales up until it is too late. He illustrates slop with fake pictures of baby peacocks that look plausible if you have never seen a real one. He adds that control researchers themselves mostly do not expect their methods to generalise to superintelligence. 40: what control covers, 20 for scheming or intentional deception only, 20 for early transformative AI only, not stronger AI. 30: the slop path, early AI produces work that looks right but is not, and the lab believes the problem is solved when it is not. 30: any two of these earn the 30, and one earns 15: scheming in early AI is a small slice of the risk, the real danger is later and stronger AI that early AI must help align, alignment for superintelligence is hard to verify, control methods are not expected to generalise to superintelligence. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Wentworth says control research only targets intentional scheming, and only in the first transformatively useful AIs, not in stronger ones. He thinks that is a small slice of the risk, because the danger is mostly later, more powerful AI, and early AI's job is to help us align it. The likely failure is slop: early AI produces alignment work that looks fine but is wrong, superintelligence alignment is hard to check, and the lab thinks it has solved the problem when it has not. Even control researchers do not expect their methods to carry over to superintelligence."
feedback-instructions:: The learner just read Wentworth's "The Case Against AI Control Research". Key points: (1) control research, as Wentworth describes it, only targets intentional scheming, and only in early transformatively useful AI, (2) he thinks scheming in early AI is a small slice of the existential risk, (3) the main job of early AI is to help solve alignment for much stronger AI, (4) the median doom path is slop: early AI produces work that looks fine, alignment for superintelligence is hard to verify, and the lab believes it has solved the problem when it has not, (5) control researchers themselves mostly do not expect their methods to generalise to superintelligence. This is a one-turn mirror. In 80 to 120 words, say plainly what they got right, name what is missing without lecturing, correct any error in one sentence, and tell them to move on. Do not ask a follow-up question. No generic praise. If the learner says they do not remember or do not understand, give one concrete foothold (for example the "baby peacock" picture) and move on.

#### Text
content::
\## Buck's reply

Buck Shlegeris of Redwood Research, one of the two authors of the case for control you read in Unit 1, replied the same day:

#### Article
source:: [[../articles/buck-comment-on-the-case-against-ai-control-research-comment]]

#### Question: Open
id:: 8aca878f-dabc-4a52-92f8-243ef9337f63
force-feedback:: first
content::
\## Does Buck's reply answer it?

1. What does Wentworth's criticism get right?
2. Buck says that stopping scheming early AIs is "quite robustly good", so control deserves a substantial share of safety effort. Does that answer Wentworth's claim that scheming is a small slice of the risk? Why or why not?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: John Wentworth argues that control targets only scheming in early transformatively useful AI, which he calls a relatively small slice of the risk, and that the likely failure is slop: early AI produces alignment work that looks fine and is not, and the lab believes it has solved the problem. Buck Shlegeris replies that he finds this unconvincing as an argument that control should be less than, say, 20% of safety research effort: stopping scheming early transformative AIs from extreme subversion is "quite robustly good", so it deserves a substantial share of effort, and there is a burden of proof on skeptics. He adds that getting useful research out of scheming AIs is in scope for control, and that control probably also reduces risk for moderately superintelligent models. This question asks for reasoning, and there is no single right verdict. Part 1, 40: something Wentworth's criticism gets right, with a reason, for example that control does nothing about slop, that slop could be the more likely way to fail, or that a lab could wrongly believe it has solved alignment. 20 of these 40 if no reason is given. Part 2, 60: a judgement of whether Buck's reply answers Wentworth, with a reason. Either verdict earns full marks with a fitting reason. Reasons it does answer: a "small slice" can still be large in absolute terms (Wentworth's own footnote reports researchers giving 2 to 20 percent for scheming), and Buck argues for a share of effort, not all of it; Buck also counts getting useful research out of scheming AIs as control, which bears on slop. Reasons it does not: "robustly good" says the work helps, not that it helps more than work on slop; Buck says he has not justified a quantitative estimate; the reply does not engage with slop at all. 30 of these 60 for a verdict with a generic reason or none. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Wentworth is right that control does nothing about slop, and slop could be the more likely way to fail. Buck's reply partly answers him: even a small slice of a large risk can deserve a real share of effort, and Buck only argues for a substantial share, not most of it. But he admits he has not worked out the numbers, and he does not say why scheming deserves more effort than slop, which is Wentworth's real point."
feedback-instructions:: The learner says what Wentworth's criticism gets right and judges whether Buck's reply answers it. Wentworth: scheming in early AI is a small slice of the risk, and the main risk (slop, unverifiable alignment work) is untouched. Buck: he finds this unconvincing as an argument for giving control less than about 20% of safety effort; stopping extreme subversion by early schemers is "quite robustly good" and deserves a substantial share; he has not justified a quantitative estimate. Either verdict is fine if reasoned: it answers him (a small slice of a big risk can still merit a real share; Wentworth's own footnote gives 2 to 20 percent for scheming) or it does not (robustly good is not the same as better than slop work; no numbers; slop is not engaged). Do not tell the learner that Buck ignores the share-of-effort question: he addresses it directly. Up to two turns. Per reply: name the strongest part, then one gap, and ask one direct question about it. 80 to 130 words per reply. No generic praise. Do not tell the learner who is right overall. If the learner says they do not understand, give one foothold: Wentworth's sentence "intentional scheming in early transformatively-useful AI is a relatively small slice of the AI X-risk probability mass".

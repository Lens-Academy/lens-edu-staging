---
id: 'ce6ffe68-5c14-4150-8257-1666326e81cf'
title: "Slop, not scheming"
reading_minutes: 15
tutor_minutes: 11
tldr: "The criticism: control guards against the wrong danger. John Wentworth argues that scheming in early AI is a small slice of the risk, and that the likely way we lose is early AI producing alignment work that looks right and is not. Buck Shlegeris replies."
summary_for_tutor: "Unit 4 of AI Control Fundamentals, Module 'Even done well, control isn't worth the effort', lens on the criticism that control guards against the wrong danger. The learner reads John Wentworth's 'The Case Against AI Control Research' (LessWrong, January 2025) in full, then Buck Shlegeris's reply in full (control deserves a substantial share of safety effort because stopping scheming early transformative AI from extreme subversion is 'quite robustly good', getting useful research out of scheming AIs is in scope for control, and his nitpicks that control techniques probably also reduce risk for 'moderately superintelligent' models and that some non-scheming threat models are addressed as a special case). Wentworth's claim: control only targets scheming in early transformative AI, and that is a small slice of the risk. The median doom path is slop: early AI produces alignment work that looks fine and is not, and the lab believes it has solved the problem. Wentworth does not say control backfires; he says the effort would do more good elsewhere. Do not tell the learner who is right."
---
#### Text
content::
**The criticism: control guards against the wrong danger.**

Control aims to stop early AIs that scheme. John Wentworth argues that this is a small slice of the risk, and that the likely way we lose is different: early AI produces alignment work that looks right and is not.

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

In your own words:
1. What does Wentworth think control research covers: which danger, in which AIs?
2. Where does he think most of the risk lies instead, and how does he think things most likely go wrong?
assessment-instructions:: Score out of 100. Context for grading: John Wentworth argues that control research, as he describes it, covers only intentional deception or scheming, and only in early transformatively useful AI, roughly human-level, not more powerful AI. He thinks this is a small slice of the risk: most of it lies in later, much more powerful AI such as superintelligence, and the main job of early AI is to help solve alignment for that stronger AI. His median path to doom is slop, not scheming: early AI produces alignment work that looks fine at first glance but is wrong, and the lab believes it has solved the problem and builds on the non-solution until it is too late. 40: what control covers, 20 for scheming or intentional deception only, 20 for early transformative AI only, not stronger AI. 20: most of the risk lies in later, much more powerful AI, which early AI is supposed to help align. 40: the slop path, early AI produces alignment work that looks right but is wrong, and it gets trusted as a solution. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Wentworth says control research only targets intentional scheming, and only in the first transformatively useful AIs, not in stronger ones. Most of the risk is in those later, stronger AIs, which early AI is supposed to help us align. The likely failure is slop: early AI produces alignment work that looks fine but is wrong, and the lab thinks it has solved the problem when it has not."
feedback-instructions:: The learner just read Wentworth's "The Case Against AI Control Research". Key points: (1) control research, as Wentworth describes it, only targets intentional scheming, and only in early transformatively useful AI, (2) he thinks scheming in early AI is a small slice of the existential risk, (3) the main job of early AI is to help solve alignment for much stronger AI, (4) the median doom path is slop: early AI produces work that looks fine, alignment for superintelligence is hard to verify, and the lab believes it has solved the problem when it has not, (5) control researchers themselves mostly do not expect their methods to generalise to superintelligence. The question asks for (1), for (2) and (3) together as where most of the risk lies, and for (4); point (5) is context you may add in one sentence, not a gap. This is a one-turn mirror. In 80 to 120 words, say plainly what they got right, name what is missing from (1) to (4) without lecturing, correct any error in one sentence, and tell them to move on. Do not ask a follow-up question. No generic praise. If the learner says they do not remember or do not understand, give one concrete foothold (for example the "baby peacock" picture) and move on.

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

Buck says that stopping scheming early AIs is "quite robustly good", so control deserves a substantial share of safety effort. Does that answer Wentworth's claim that scheming is a small slice of the risk? Why or why not?
placeholder:: A few sentences.
assessment-instructions:: Score out of 100. Context for grading: John Wentworth argues that control targets only scheming in early transformatively useful AI, which he calls a relatively small slice of the risk, and that the likely failure is slop: early AI produces alignment work that looks fine and is not, and the lab believes it has solved the problem. Buck Shlegeris replies that he finds this unconvincing as an argument that control should be less than, say, 20% of safety research effort: stopping scheming early transformative AIs from extreme subversion is "quite robustly good", so it deserves a substantial share of effort, and there is a burden of proof on skeptics. He adds that getting useful research out of scheming AIs is in scope for control, and that control probably also reduces risk for moderately superintelligent models. This question asks for reasoning, and there is no single right verdict. 100: a judgement of whether Buck's reply answers Wentworth, with a reason. Either verdict earns full marks with a fitting reason. Reasons it does answer: a "small slice" can still be large in absolute terms (Wentworth's own footnote reports researchers giving 2 to 20 percent for scheming), and Buck argues for a share of effort, not all of it; Buck also counts getting useful research out of scheming AIs as control, which bears on slop. Reasons it does not: "robustly good" says the work helps, not that it helps more than work on slop; Buck says he has not justified a quantitative estimate; the reply does not engage with slop at all. 50 for a verdict with a generic reason or none. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Buck's reply partly answers Wentworth: even a small slice of a large risk can deserve a real share of effort, and Buck only argues for a substantial share, not most of it. But he admits he has not worked out the numbers, and he does not say why scheming deserves more effort than slop, which is Wentworth's real point."
feedback-instructions:: The learner judges whether Buck's reply answers Wentworth's criticism. Wentworth: scheming in early AI is a small slice of the risk, and the main risk (slop, unverifiable alignment work) is untouched. Buck: he finds this unconvincing as an argument for giving control less than about 20% of safety effort; stopping extreme subversion by early schemers is "quite robustly good" and deserves a substantial share; he has not justified a quantitative estimate. Either verdict is fine if reasoned: it answers him (a small slice of a big risk can still merit a real share; Wentworth's own footnote gives 2 to 20 percent for scheming) or it does not (robustly good is not the same as better than slop work; no numbers; slop is not engaged). Do not tell the learner that Buck ignores the share-of-effort question: he addresses it directly. Up to two turns. Per reply: name the strongest part, then one gap, and ask one direct question about it. 80 to 130 words per reply. No generic praise. Do not tell the learner who is right overall. If the learner says they do not understand, give one foothold: Wentworth's sentence "intentional scheming in early transformatively-useful AI is a relatively small slice of the AI X-risk probability mass".

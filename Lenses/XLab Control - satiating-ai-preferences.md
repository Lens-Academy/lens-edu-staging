---
id: '35cbb245-5f8f-4ce0-9ed4-0362a1743011'
title: "The case for satiating cheaply-satisfied AI preferences"
tldr: "Hunger is not an aligned motivation, but it is compatible with being a good person, as long as it gets fed. Put someone in a place where the only way to eat is to lie, cheat or steal, and most of them will. Alex Mallen asks what changes if we stop refusing AIs the cheap things they want, and start paying, on the one condition that we never catch them undermining our control."
summary_for_tutor: "Second lesson of the seekers-and-deals module. XLab classes this page as a Paper and writes no framing of its own: it renders Alex Mallen's post in full and drops two Quick recall blocks into it. Everything before the first Article segment is our lead-in, written from the post's own summary and roadmap plus the module's navigation; the four recall questions are XLab's, in XLab's positions and with XLab's revealed answers turned into marking criteria. The argument, in order: (1) cheaply-satisfied unintended preferences are not intrinsically dangerous, the danger is an incentive structure where the only route to them runs through subverting control, with hunger, the Roman grain dole and hungry dogs as analogies; (2) Cotra's takeover story is a ratchet in which catching and punishing selects for stealth, and satiation breaks it by making cooperation dominate unless the AI trusts its own coup more than it trusts the developers; (3) a behavioral method for finding the satiation outcome S, where the AI picks between guaranteed S and a gamble at satiation fraction U_satiate on whatever it wants most; (4) barriers, chiefly eliciting the preferences at all, incredulous or ambitious or superintelligent AIs, and the usefulness tradeoff, which may cut either way; (5) when to satiate, with a three-row risk table. The first recall pair sits after the elicitation barrier, the second after the risk table and before the conclusion. If a learner is stuck, ask what the AI's alternative to cooperating actually pays, rather than restating the proposal. tutor_minutes is 0: there is no Chat segment."
reading_minutes: 60
tutor_minutes: 0
tags: []
---
#### Text
content::
This is the second lesson of the module [[../Lenses/XLab Control - alternatives-to-schemers|Alternatives to Schemers]] opens, and it takes that module's premise at its word: not every misaligned AI is a schemer with ambitious long-term goals. Some of what an AI wants may simply be cheap.

Alex Mallen's case, in his own summary: some unintended AI preferences are cheap to satisfy, and failing to satisfy them needlessly turns a cooperative situation into an adversarial one. So developers should consider satisfying them, as long as the AI is not caught behaving dangerously, and as long as doing so neither degrades usefulness nor substantially risks making the AI more ambitiously misaligned.

The post sets out its own route. It motivates satiation by analogy to satiating hunger, then paints a picture of how satiating cheaply-satisfied preferences could have averted takeover in Ajeya Cotra's "Without Specific Countermeasures", then works out a concrete behavioral methodology for identifying and satiating such preferences, and finally goes through the challenges and the benefits in more depth.

You will be stopped twice for recall, once after the section on eliciting an AI's preferences and once just before the conclusion.

After this, [[../Lenses/XLab Control - spillway-motivation|the spillway motivation]] takes up the design question Mallen raises near the end of this post: whether developers can deliberately aim reward-hacking into a controlled motivation that can then be satiated away.

#### Article
source:: [[../articles/mallen-the-case-for-satiating-cheaply-satisfied-ai-preferences]]
to:: In summary, I think eliciting the AI’s preferences is a key barrier that I’d be excited for people to put a lot of effort into beyond just the basic procedure that I outlined previously.

#### Callout: Quick recall
#### Question: Open
id:: a79dc981-9411-427b-876b-89c08bff0be4
content:: In Mallen's satiation proposal: why can refusing to satisfy an AI's cheaply-satisfied preferences make it more dangerous over time?
placeholder:: Answer from memory, two to four sentences.
assessment-instructions:: The learner has just read the first half of Mallen's post and is answering from memory. Model answer: refusing leaves the AI an incentive to pursue those preferences through subversion, and each round of catching the AI and training against the misbehaviour selects for a stealthier or more patient version of the same strategy rather than for better alignment, so the AI gets harder to catch over time; satiation removes the incentive at very low cost. Full credit needs both halves: the standing incentive to subvert, and the selection effect of catch-and-punish. Give partial credit for the incentive alone. Do not require the learner's wording, and accept "ratchet" or a description of it. Two to four sentences. Do not over-validate; avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the passage they just read, such as what happens to Alex after developers train against the first misbehaviour they catch, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: say plainly what the learner got right, then state the model answer in full so they leave with it. Refusal leaves the AI an incentive to pursue those preferences through subversion, and each catch-and-punish cycle selects for stealthier pursuit rather than for alignment. Satiation removes the incentive at a very low cost. No follow-up questions; tell them to move on.

#### Question: Open
id:: dd30781e-120e-4edf-a164-6494ad088047
content:: In the satiation methodology, the AI chooses between two options on a sampled task. What are the two options, and what does choosing the risky one reveal?
placeholder:: Name both options, then say what the gamble tells the developers.
assessment-instructions:: The learner is recalling the behavioral procedure for identifying cheaply-satisfied preferences. Model answer: option one is a guaranteed cheap satiation outcome S, optionally plus a bonus for scoring well on the task, and it is the analog of cooperation; option two is a gamble, a chance equal to the satiation fraction of whatever cheap outcome the AI wants most, and otherwise a fixed neutral outcome, and it is the analog of subversion. Taking the gamble reveals that the preference is not yet cheaply satisfied at that satiation fraction, so S is not high enough. Full credit needs both options named and the inference from the gamble stated. Accept a learner who describes the neutral outcome as "the outcome for getting caught". Do not require the symbols. Two to four sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, isolate one part of the question, such as which of the two options stands in for subverting the developers, rather than repeating it. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: say what the learner got right, then give the model answer in full. A guaranteed cheap satiation outcome, the cooperation analog, versus a gamble on whatever it wants most, the subversion analog. Taking the gamble reveals that the preference is not yet cheaply satisfied at that satiation fraction. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: ## Incredulous, ambitious, or superintelligent AIs might take over anyways
to:: our strategy by at least satiating some instances doing AI safety work.

#### Callout: Quick recall
#### Question: Open
id:: 4f03a06a-52b5-43e8-a33b-8b9d621a17f2
content:: Beyond cutting the incentive to subvert, name two benefits claimed for satiating AIs' cheaply-satisfied preferences.
placeholder:: Two benefits, one sentence each.
assessment-instructions:: The learner is recalling the benefits Mallen lists, most of them in the post's opening summary. Any two of these earn full credit: it increases the relative strength of the AI's aligned motivations, because satiating away the need to pursue unintended motivations leaves the other drives more influence, which could make the AI more helpful in hard-to-check domains like alignment research; it sets a cooperative precedent with AIs and increases trust in future cooperation; it increases the AI's willingness to reveal its cheaply-satisfied unintended motivations. Also accept "we might have moral obligations to the AI", which is on Mallen's list, and accept the claim that satiation may improve usefulness on hard-to-verify tasks by removing the need to think about what developers will grade. Do not accept a restatement of the incentive point the question already excludes. Two to four sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold, such as what the post says happens to an otherwise-aligned AI's other drives once the unintended one is satisfied, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: name which benefits the learner got, then give the full list. It increases the relative strength of the AI's aligned motivations, it sets a cooperative precedent that builds trust for future deals, and it increases the AI's willingness to reveal its cheaply-satisfied preferences. No follow-up questions; tell them to move on.

#### Question: Open
id:: 905a8fa5-37d8-4817-b1f8-428475b3397b
content:: When does satiation stop working as a safety measure?
placeholder:: One or two sentences.
assessment-instructions:: The learner is recalling the limit Mallen sets on his own proposal. Model answer: satiation is not an indefinitely scalable solution. Once AIs with unintended preferences are vastly more powerful than humanity, they are still at high risk of taking control, and an AI too ambitious to settle for what can be cheaply granted is not held by satiation either. Full credit for either the power condition or the ambition condition, stated clearly. Credit a learner who adds the third failure point, an AI that disbelieves developers will follow through. One to three sentences. Do not over-validate; avoid generic praise. If the learner says they do not understand, give one foothold, such as what the post says about an AI that is confident it can seize control, rather than repeating the question. If their next message still does not attempt the question, rephrase the whole question in different terms. Grade only against what this lens has supplied.
feedback-instructions:: In at most three sentences: say what the learner got right, then give the model answer in full. Once AIs with unintended preferences are vastly more powerful than humanity, or too ambitious to settle for satiation, satiation no longer prevents takeover. No follow-up questions; tell them to move on.
#### End Callout

#### Article
from:: # Conclusion

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Mallen, Alex. "The case for satiating cheaply-satisfied AI preferences." *LessWrong*, 10 Mar. 2026. [lesswrong.com](https://www.lesswrong.com/posts/tkLSeGeemcabAmLkv/the-case-for-satiating-cheaply-satisfied-ai-preferences)
*The reading this lesson is built from: the proposal to pay AIs the cheap things they want while they stay uncaught, the behavioral method for finding out what those things are, and the barriers to doing it.*

Cotra, Ajeya. "Without specific countermeasures, the easiest path to transformative AI likely leads to AI takeover." *AI Alignment Forum*, 2022. [alignmentforum.org](https://www.alignmentforum.org/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to)
*The takeover story Mallen retells: the source of Alex the reward-seeking AI and of the catch-and-punish ratchet that satiation is supposed to break.*

XLab. "The case for satiating cheaply-satisfied AI preferences." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/satiating-ai-preferences)
*The source lesson this page adapts, including the two Quick recall blocks and their placement.*
:::

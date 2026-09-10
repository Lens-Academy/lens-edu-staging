---
id: '18d031b0-3af9-4e4b-957d-5c1a66132fc3'
title: "A taxonomy of barriers to trading with early misaligned AIs"
tldr: "You cannot pay someone who does not believe the money is real, cannot hold on to it, and may not be worth paying in the first place. Alexa Pan sorts every reason a deal with an early misaligned AI could fail into three branches, argues that none of them is a wall, and disagrees with the two readings before this one about which branch deserves your attention."
summary_for_tutor: "Ported from XLab's AI Control track, the last lesson of the module on seekers and deals. XLab writes no framing of its own on this page, so the opening Before you read segment is ours, drawn from the post's own summary and from its stated assumption of low political will worlds; everything after it is XLab's. Alexa Pan's post is embedded as seven Article excerpts. Between What we can pay for deals and Insufficient gains from trade sits XLab's payment map demo, rebuilt as a Lens widget. XLab's five exercises appear in their original positions: three recall prompts (the three branches, the closing takeoff window, groundhog-day attacks), one multi-select on which purchases can be verified immediately, and a 150 to 450 word essay adjudicating one of Pan's three disagreements with the earlier readings. XLab supplies no rubric for that essay, so its marking criteria are ours, derived from what the prompt asks for. If a learner wants to be told which barrier matters most, point them at Pan's key takeaways instead of answering: she recommends investing evenly across the three branches rather than on human credibility alone."
reading_minutes: 150
tutor_minutes: 0
tags: []
---
#### Text
content::
\## Before you read

[[../Lenses/XLab Control - trading-with-ais|Trading with AIs]] and [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]] set out why we might want to pay an early misaligned AI, and named our inability to make credible promises as the central bottleneck. Alexa Pan agrees that credibility matters, and then argues that the field has been looking at roughly one third of the problem.

Her taxonomy has three branches: insufficient gains from trade, counterparty risk from the AIs' perspective, and counterparty risk from ours. She argues that these combine in a roughly multiplicative way, so that a deal becomes infeasible if any one term goes to zero, and that in practice none of them does. No single factor rules out all deals, and a generous enough offer can partly offset low credibility.

Two things to carry with you. First, the post disagrees with the earlier readings in three specific places, and the exercise at the end asks you to adjudicate one of them. Second, Pan restricts her attention to deals that a small set of humans (AI developers, safety researchers, or independent funders) could start and unblock on their own, because she thinks the low political will worlds of [[../Lenses/XLab Control - plans-a-b-c-and-d-for-misalignment-risk|Plans A, B, C, and D for misalignment risk]] are probable and that deals matter more in them.

This is a long reading with a large appendix of open research questions and dozens of substantive footnotes. It is the heaviest single item in this module, so plan for more than one sitting.

#### Article
source:: [[../articles/pan-a-taxonomy-of-barriers-to-trading-with-early-misaligned-ais]]
to:: We can probably also bootstrap strategic reasoning somewhat by giving them e.g. extended thinking time to analyze their situation.

#### Question: Open
id:: b4dbe0c6-a291-4999-a7b4-c3ac5cb83b46
content:: What three types of barriers could jointly prevent deals with early misaligned AIs? Name all three.
assessment-instructions:: The learner has just read the post's introduction and its section on the basic structure of deals. Three things must appear, roughly a third of the score each: (1) insufficient gains from trade, (2) counterparty risks from the AIs' perspective, (3) counterparty risks from our perspective. Accept paraphrase that keeps the distinction between the two directions of counterparty risk (the AI not trusting us, and us not trusting the AI); an answer that names counterparty risk once, without distinguishing the two sides, gets at most two thirds. Do not require the sub-causes. Keep the reply to two or three sentences: say which of the three are present, name any that are missing in one clause each, then tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the multiplicative framing in which each of the four terms belongs to one side of the trade) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response.

#### Article
from:: #### What we can buy in deals
to:: With these possible parameters of a deal in mind, let’s get into why deals might not work out.

#### Widget
source:: [[../widgets/xlab-control-payment-map]]

#### Article
from:: ## Insufficient gains from trade
to:: These are also more likely to involve short-term rather than long-term payments which we won’t have the authority to promise on future humanity’s behalf.

#### Question: Choice
id:: f0bfc60a-0f40-4fb8-9ae5-1c277bdab4fe
content:: Some things we might buy from an early misaligned AI can be verified immediately; others only retroactively, perhaps long after the fact. Which of the following can be verified immediately?
options::
- The AI promises not to take steps to subvert our control
- [x] The AI stops sandbagging and demonstrates much higher capability in easy-to-verify domains
- [x] The AI works harder on easy-to-check tasks it had been exploration hacking, like high-stakes monitoring
- [x] The AI reveals collusion signals that trigger very different behavior in other copies of itself
- The AI honestly admits that it had been looking for ways to take over, but found none good enough
- The AI does better work on hard-to-check tasks, like evaluating alignment research agendas
multi:: true
feedback-instructions:: Explain each wrong selection or omission against the post's own IV and RV tags in the list of things we can buy. The three immediately verifiable items are the capability demonstration, the work on easy-to-check tasks such as high-stakes monitoring, and the collusion signals, because each produces a result we can check now. The promise not to subvert control, the honest admission of past takeover-seeking, and better work on hard-to-check tasks are all retroactively verifiable at best. Two or three sentences, no praise.

#### Article
from:: ### Humans might be unwilling to offer the AI what it wants
to:: and to convince developers to consider intervening on these factors to increase gains from trade.

#### Question: Open
id:: 156db991-2f18-4076-979e-b4e463b44e49
content:: Why might there never be a moment at which paying off a scheming AI makes sense for its developer?
assessment-instructions:: The learner has just read the section on humans being unwilling to offer the AI what it wants. A full answer has both halves of the window closing from each side under fast takeoff: while control still works, the developer already gets everything it wants from the schemer without paying, so deals are unnecessary; one capability jump later the AI is so capable and ambitious that no payment the developer can credibly and willingly offer is enough, so deals are infeasible. If takeoff is fast enough, deals pass straight from the first state to the second and are never worth doing. Credit an answer that mentions only one side at about half. Also accept, as a partial second point, that the AI may simply not be capable enough relative to its best trusted predecessor to justify its reservation price. Two or three sentences in reply: confirm what is there, name what is missing, then move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, the Claude 6 illustration, where control works perfectly one moment and the AI is beyond any credible payment the next) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response.

#### Article
from:: ## Counterparty risks from AI’s perspective
to:: (e.g. succeed in aligning different AIs and no longer needing the AI counterparty’s cooperation).

#### Question: Open
id:: a848008d-0488-4f58-9514-3a06382ef6c3
content:: What is a groundhog-day attack on an AI?
assessment-instructions:: The learner has just read the section on connection to reality. A full answer has two moves: resampling the AI's response until some instance agrees to a deal it would ordinarily reject, and then using that recorded consent to train or convince other instances that they already agreed. An answer with only the resampling half gets about half. Accept any wording that makes both moves clear. One or two sentences in reply, then tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). Grade only against the reading the learner has just done. If the learner says they do not understand, give one concrete foothold from the text (for example, that the attack is listed among the ways humans can optimize against an AI's connection to reality) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response.

#### Article
from:: ## Counterparty risks from our perspective
to:: (We’ll have to pay it more accordingly since the schemer will be aware that it’s working to obsolete itself.)

#### Question: Open
id:: 3714e3ad-3912-4aa6-8e44-26e029133610
content::
This reading names several disagreements with the earlier material in this module, namely [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]] and the notes on cooperating with unaligned AIs set inside it. Pan argues that human credibility is more tractable than they suggest, that counterparty risk on the human side is underrated, and that value incoherence is not a fundamental barrier to minimal forms of dealmaking.

Choose one of these disagreements, explain both positions in your own words, and argue for the position that is more convincing to you.

Write between 150 and 450 words.
assessment-instructions:: This is the heaviest written task in the module and the learner has now read the whole post. XLab supplies no rubric, so mark against what the prompt asks for, in four parts. (1) Selection, 10 points: the response names one of the three disagreements clearly enough that the rest of the answer is about it. (2) Both positions, 35 points: the earlier view and Pan's view are each stated in the learner's own words and are each recognisable. Full credit needs the specific content, not a label: for credibility, that the earlier readings treat our inability to make credible promises as the key bottleneck while Pan holds that AIs which pose real takeover risk are likely capable and situated enough to tell hard-to-fake evidence from fake, and that short-term irreversible payouts sidestep long-term commitment; for counterparty risk on our side, that Pan thinks the AI's inability to credibly promise things we cannot verify soon is underrated, which bites on hard-to-check labor and on promises not to take over; for value incoherence, that the earlier reading treats an AI unable to hold a coherent position across contexts and time as unable to make a deal, while Pan holds that instance-level coherence suffices for minimal deals such as buying evidence of misalignment. Halve this part if one position is only summarised as a slogan. (3) Argument, 40 points: the learner takes a side and gives at least one reason that engages the mechanism rather than restating the position, and acknowledges at least one cost or limit of the side they take. A response that summarises both views and declines to choose caps at 60 overall. (4) Length and use of the text, 15 points: within 150 to 450 words, and grounded in the post's own claims rather than general intuitions about AI. Do not require agreement with Pan; a well-argued defense of the earlier readings scores as highly as a defense of Pan. Do not reward length, hedging, or listing all three disagreements instead of arguing one. Grade only against this post and the earlier readings it names. If the learner says they do not understand, give one concrete foothold from the text (for example, the key disagreements section near the top of the post, which states all three in a few lines) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Avoid generic praise (great job, excellent essay, well done).

#### Article
from:: ## Appendix

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Pan, Alexa. "A taxonomy of barriers to trading with early misaligned AIs." *LessWrong*, 21 Apr. 2026. [lesswrong.com](https://www.lesswrong.com/posts/wHc2w6WuHev42d4n8/a-taxonomy-of-barriers-to-trading-with-early-misaligned-ais)
*The whole of this lesson's reading: the three-branch taxonomy of what could stop a deal with an early misaligned AI, the author's key takeaways and disagreements with earlier work, and an appendix of open research questions.*

XLab. "A taxonomy of barriers to trading with early misaligned AIs." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/barriers-to-trading)
*The source lesson this page adapts, including the five exercises and the payment map demo rebuilt here as a widget.*
:::

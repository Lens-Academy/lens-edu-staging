---
id: '909e0e22-85b2-44a1-9ff9-df1891143bc3'
title: "A taxonomy of barriers to trading with early misaligned AIs (2): can either side be trusted"
tldr: "A deal can be worth it to both sides and still fail because neither side believes the other will pay. Alexa Pan's other two branches ask whether an AI can tell a real offer from a test and keep what it is paid, and whether we can rely on an AI whose goals shift or whose work we cannot check for years. It ends by asking you to settle one of her disagreements with earlier work."
summary_for_tutor: "Part 2 of 2 of Alexa Pan's post 'A taxonomy of barriers to trading with early misaligned AIs', continuing part 1, which covered the post's summary of the three branches, her key takeaways and three disagreements with earlier work, what a deal is made of, what we can buy and pay, and the first branch, insufficient gains from trade. The opening Text is ours; everything after it comes from the source lesson. This part renders the rest of the post as three Article excerpts: counterparty risks from the AI's perspective (connection to reality, including how an AI might tell whether it is radically deluded and how hard-to-fake evidence and honesty policies can help; AI-specific fear of expropriation and the case for short-term, irreversible payouts; generic human commitment problems), counterparty risks from our perspective (deals with context-dependent or temporally inconsistent AIs, and verifying compliance, where buying evidence of misalignment is easy to check but useful work on hard-to-check tasks and promises not to take over are not), and the appendix of leads for future work and notes on political will, folded. Two exercises appear in their original positions: a recall prompt on groundhog-day attacks, and a 150 to 450 word essay adjudicating one of Pan's three disagreements with earlier work (the credibility one is aimed at 'Making deals with early schemers' and Finnveden's notes, the value-incoherence one at 'Making deals' alone, l.120 and l.157 of the article). The three disagreements are stated near the top of the post, in part 1; the opener restates them. There is no rubric for that essay, so its marking criteria are ours, derived from what the prompt asks for. If a learner wants to be told which barrier matters most, point them at Pan's key takeaways (part 1) instead of answering: she recommends investing evenly across the three branches rather than on human credibility alone."
reading_minutes: 44
tutor_minutes: 15
tags: []
---
#### Text
content::
Part 2 of 2. The previous part laid out what a deal with an early misaligned AI is made of and worked through the first branch of Alexa Pan's taxonomy, insufficient gains from trade; this part covers the other two: counterparty risk from the AI's perspective (can it believe and keep what we pay) and from ours (can we rely on it, and check what it delivers).

Near the top of the post, Pan named three places where she parts ways with earlier work: against both [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]] and the notes on cooperating with unaligned AIs, human credibility is more tractable than they suggest; counterparty risk from our side, the AI's inability to credibly promise what we cannot check soon, is underrated; and, against Making deals with early schemers in particular, value incoherence is not a fundamental barrier to minimal forms of dealmaking. The sections below make the case for each, and the essay at the end asks you to adjudicate one of them, so keep track of where you find her convincing.

#### Article
source:: [[../articles/pan-a-taxonomy-of-barriers-to-trading-with-early-misaligned-ais]]
from:: ## Counterparty risks from AI’s perspective
to:: (e.g. succeed in aligning different AIs and no longer needing the AI counterparty’s cooperation).

#### Question: Open
id:: a848008d-0488-4f58-9514-3a06382ef6c3
content:: What is a groundhog-day attack on an AI?
assessment-instructions:: Score out of 100. 50: resampling the AI (running it again and again) until some instance agrees to a deal that is bad by its own lights and that it would normally reject. 50: then using that recorded agreement to train or convince other instances that they already consented. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Resampling an AI's response until some instance agrees to a deal it would ordinarily reject, then using that recorded consent to train or convince other instances that they already agreed."
feedback-instructions:: Two or three sentences in reply: say plainly what the learner got right and, if anything is missing or wrong, the most important thing, then tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the text (for example, that the attack is listed among the ways humans can optimize against an AI's connection to reality) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response.

#### Article
from:: ## Counterparty risks from our perspective
to:: (We’ll have to pay it more accordingly since the schemer will be aware that it’s working to obsolete itself.)

#### Question: Open
id:: 3714e3ad-3912-4aa6-8e44-26e029133610
content::
Pan's post names several disagreements with the earlier material, namely [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]] and the notes on cooperating with unaligned AIs set inside it (part 1 states them near the top of the post; this part's opener restates them). Pan argues that human credibility is more tractable than they suggest, that counterparty risk on the human side is underrated, and that value incoherence is not a fundamental barrier to minimal forms of dealmaking.

Choose one of these disagreements, explain both positions in your own words, and argue for the position that is more convincing to you.

Write between 150 and 450 words.
assessment-instructions:: Score out of 100. 10: names one of the three disagreements clearly enough that the rest of the answer is about it. 40: both positions, 20 each, stated in the learner's own words with their substance, not only a label; halve a position given only as a slogan. For credibility: the earlier readings treat our inability to make credible promises as the key bottleneck, while Pan holds that AIs posing real takeover risk are likely capable and situated enough to tell hard-to-fake evidence from fakes, and that immediate payouts and costly signals work around the need for long-term commitment. For counterparty risk on our side: Pan holds that the AI's inability to credibly promise things we cannot verify soon (hard-to-check work, promises not to take over) is underrated as a barrier. For value incoherence: the earlier view treats an AI that cannot hold a coherent position across contexts and time as unable to make a deal, while Pan holds that coherence within one instance is enough for minimal deals such as buying evidence of misalignment. 40: the argument, 15 for taking a clear side, either side, and 25 for at least one reason that engages how the thing works rather than restating the position. 10: between 150 and 450 words. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "I take the credibility disagreement. Making deals with early schemers and Finnveden's notes treat our inability to make credible promises as the key bottleneck: developers control what an AI sees, test it with fake scenarios and synthetic facts, and cannot easily bind themselves or future humanity to pay, so an AI has little reason to believe an offer is real. Pan agrees that credibility matters but thinks the problem is more tractable. The AIs that pose real takeover risk are likely to be very capable, deployed as agents that interact with their environment in many varied ways, or able to reason steganographically, and those same properties should let them check that they are connected to reality and not being deceived about the deal. And some payments sidestep long-term commitment altogether: immediate consumption does not depend on property rights or promises about the future, while costly signals and existing legal institutions can back the rest. I find Pan more convincing for the deals that matter first. An AI does not need to trust promises about decades from now if it is paid now and can check the payment, and Finnveden's own observation that an AI we can fully fool is probably not dangerous points the same way. The limit of her view is that immediate payment suits mainly AIs with short-term wants and buys mainly what we can verify quickly; for a long-term schemer asked for hard-to-check work, the earlier readings' worry still stands."
feedback-instructions:: Say plainly what the learner got right and, if anything is missing or wrong, the most important thing. If the learner says they do not understand, give one concrete foothold from the text (for example, the opening of this part, which restates all three in a few lines; they are stated in full in the key disagreements section near the top of the post, in part 1) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. Avoid generic praise (great job, excellent essay, well done).

#### Article
from:: :::callout {title="Appendix: Leads for future work and notes on political will" collapse="closed"}

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Pan, Alexa. "A taxonomy of barriers to trading with early misaligned AIs." *LessWrong*, 21 Apr. 2026. [lesswrong.com](https://www.lesswrong.com/posts/wHc2w6WuHev42d4n8/a-taxonomy-of-barriers-to-trading-with-early-misaligned-ais)
*This part's reading: the sections on counterparty risks from the AI's perspective and from ours, and the appendix of open research questions and notes on political will.*

XLab. "A taxonomy of barriers to trading with early misaligned AIs." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/barriers-to-trading)
*The source lesson this page adapts.*
:::

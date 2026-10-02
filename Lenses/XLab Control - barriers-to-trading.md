---
id: '18d031b0-3af9-4e4b-957d-5c1a66132fc3'
title: "A taxonomy of barriers to trading with early misaligned AIs (1): what a deal needs and whether it is worth it"
tldr: "You cannot pay someone who does not believe the money is real, cannot hold on to it, and may not be worth paying at all. Alexa Pan sorts every reason a deal with an early misaligned AI could fail into three branches and argues that none is a wall. This part covers what a deal is, what we could buy and pay, and the first branch: gains from trade too small to be worth it."
summary_for_tutor: "Part 1 of 2 of Alexa Pan's post 'A taxonomy of barriers to trading with early misaligned AIs': the rebuttal that the three-part 'Making deals with early schemers' points to, and the lesson after it. The opening Before you read segment is ours, drawn from the post's own summary and its stated assumption of low political will worlds; everything after it comes from the source lesson. This part renders the post from its opening through the end of 'Insufficient gains from trade' as four Article excerpts: the summary of the three branches and their roughly multiplicative combination, Pan's key takeaways and her three disagreements with earlier work (credibility is more tractable than claimed, counterparty risk on the human side is underrated, value incoherence is not a fundamental barrier to minimal deals), the basic structure of a deal and which AIs are eligible, what we can buy (tagged immediately or retroactively verifiable) and pay, then why gains from trade may be too small: humans may lack the authority or the willingness to offer what the AI wants (including the fast-takeoff case where deals pass straight from unnecessary to infeasible), and factors that raise the AI's reservation price or lower our willingness to pay. Between What we can pay for deals and Insufficient gains from trade sits a payment map demo from the source lesson, rebuilt as a Lens widget. Three exercises appear in their original positions: a recall prompt on the three branches, a multi-select on which purchases can be verified immediately, and a short explain prompt on why the takeoff window for deals may never open. Part 2, 'A taxonomy of barriers to trading with early misaligned AIs (2)', covers the two counterparty-risk branches, the essay adjudicating one of Pan's disagreements, and the appendix; if a learner wants to argue about credibility now, tell them part 2 takes it up. If a learner wants to be told which barrier matters most, point them at Pan's key takeaways instead of answering: she recommends investing evenly across the three branches rather than on human credibility alone."
reading_minutes: 52
tutor_minutes: 12
tags: []
---
#### Text
content::
\## Before you read

Part 1 of 2. [[../Lenses/XLab Control - trading-with-ais|Trading with AIs]] and [[../Lenses/XLab Control - making-deals-with-early-schemers|Making deals with early schemers]] set out why we might want to pay an early misaligned AI, and named our inability to make credible promises as the central bottleneck. Alexa Pan agrees that credibility matters, and then argues that the field has been looking at roughly one third of the problem.

Her taxonomy has three branches: insufficient gains from trade, counterparty risk from the AIs' perspective, and counterparty risk from ours. She argues that these combine in a roughly multiplicative way, so that a deal becomes infeasible if any one term goes to zero, and that in practice none of them does. No single factor rules out all deals, and a generous enough offer can partly offset low credibility.

This part covers the post's summary and key takeaways, what a deal is made of, and the first branch, insufficient gains from trade. Part 2 covers the two counterparty-risk branches. Two things to carry with you. First, near the top the post names three places where it disagrees with the earlier readings; note them, because part 2 ends by asking you to adjudicate one. Second, Pan restricts her attention to deals that a small set of humans (AI developers, safety researchers, or independent funders) could start and unblock on their own, because she thinks the low political will worlds of [[../Lenses/XLab Control - plans-a-b-c-and-d-for-misalignment-risk|Plans A, B, C, and D for misalignment risk]] are probable and that deals matter more in them.

The post has dozens of substantive footnotes. Read the main text first and open a footnote when a claim seems to need its support.

#### Article
source:: [[../articles/pan-a-taxonomy-of-barriers-to-trading-with-early-misaligned-ais]]
to:: We can probably also bootstrap strategic reasoning somewhat by giving them e.g. extended thinking time to analyze their situation.

#### Question: Open
id:: b4dbe0c6-a291-4999-a7b4-c3ac5cb83b46
content:: What three types of barriers could jointly prevent deals with early misaligned AIs? Name all three.
assessment-instructions:: Score out of 100. 34: insufficient gains from trade (the most the AI would accept is more than we would pay, so no deal is worth it to both sides). 33: counterparty risk from the AI's perspective: the AI cannot trust us to deliver what we promise. 33: counterparty risk from our perspective: we cannot trust the AI to deliver what it promises. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Insufficient gains from trade, counterparty risks from the AIs' perspective, and counterparty risks from our perspective."
feedback-instructions:: Keep the reply to two or three sentences: say which of the three are present, name any that are missing in one clause each, then tell them to move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the text (for example, the multiplicative framing in which each of the four terms belongs to one side of the trade) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response.

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
assessment-instructions:: Score out of 100. 35: deals are unnecessary while control still works, because the developer already gets everything it wants from the schemer without paying. 35: deals become infeasible once the AI is capable and ambitious enough, because nothing the developer can credibly and willingly offer is enough to buy it off. 30: with fast takeoff (one capability jump) there is no window in between, so deals go straight from unnecessary to infeasible. Give credit for each point whenever the answer shows the idea, in any wording. The other reason the reading gives, that even an AI that is not perfectly controlled may add too little over its best trusted predecessor to be worth its price, can take the place of either of the first two points. Model answer, for the feedback, not a grading checklist: "If takeoff is fast, deals may pass straight from unnecessary to infeasible. While control still works, the developer is able to get everything it wants from the schemer without paying, but one capability jump later the AI is too capable and ambitious to be bought off with anything the developer can credibly offer."
feedback-instructions:: Two or three sentences in reply: confirm what is there, name what is missing, then move on. Do not over-validate. Avoid generic praise (great job, excellent recall, well done). If the learner says they do not understand, give one concrete foothold from the text (for example, the Claude 6 illustration, where control works perfectly one moment and the AI is beyond any credible payment the next) rather than repeating the question; if their next message still does not attempt the question, rephrase the whole question in different terms. This is a one-turn response.

#### Text
content::
:::callout {title="Works cited" tone="neutral" collapse="closed"}
Pan, Alexa. "A taxonomy of barriers to trading with early misaligned AIs." *LessWrong*, 21 Apr. 2026. [lesswrong.com](https://www.lesswrong.com/posts/wHc2w6WuHev42d4n8/a-taxonomy-of-barriers-to-trading-with-early-misaligned-ais)
*This part's reading: the post from its opening (summary, key takeaways, disagreements with earlier work) through the basic structure of deals, what we can buy and pay, and the section on insufficient gains from trade.*

XLab. "A taxonomy of barriers to trading with early misaligned AIs." *AI Control*, XLab, University of Chicago, 2026. [aisafetytracks.com](https://aisafetytracks.com/tracks/control/module-5/barriers-to-trading)
*The source lesson this page adapts, including the payment map demo rebuilt here as a widget.*
:::

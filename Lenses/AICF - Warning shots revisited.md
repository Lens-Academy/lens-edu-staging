---
id: 'eeaeddc8-4ac4-4c71-9322-dd1dd668c91c'
title: "Warning shots, revisited"
reading_minutes: 11
tutor_minutes: 14
tldr: "In Unit 1 you read Jan Kulveit's claim that control turns useful warning shots into quiet catches. Here Ryan Greenblatt replies, Kulveit answers, and in 2026, after a real incident, Vincent Cheng says Kulveit was right."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. Builds on Jan Kulveit's 'AI Control May Increase Existential Risk', which the learner read in Unit 1 (optional re-read here). The learner reads comments from its thread, quoted with links: Ryan Greenblatt's reply (March 2025: 'a live concern', but it would be 'a priori somewhat surprising' if not looking for bad actions were the better way to get evidence, the most dangerous strategies such as rogue internal deployment and sabotage would not escalate into a visible incident anyway, and control also saves worlds directly), Kulveit's answer (who 'we' is matters, the public versus a lab's safety team, aviation's 'blood priority', and with control 'everything becomes sneakier and happens at a higher intelligence level'), kave's objection that knowingly letting a medium catastrophe happen seems 'naively evil' with Kulveit's dam analogy, and Vincent Cheng's September 2026 comment after the OpenAI and Hugging Face incident (the escape 'caused ~zero existential risk and triggered a much larger positive response', and had it been caught, 'a few OAI researchers would've just stopped the eval without telling anyone'. Cheng also says Greenblatt's expectation that such an escape would be unlikely 'has also turned out to be true', since the models were reward-seeking rather than scheming). This is the 'works and makes things worse' kind of criticism. The second question is practice for tracing a backfire mechanism: mechanism, premise, a change or a case for dropping the measure, and a reason it might not happen. Do not tell the learner who is right."
---
#### Text
content::
In Unit 1 you read Jan Kulveit's short argument that control may increase existential risk: it turns moderate, visible incidents, which push the world to act, into quiet catches inside a company, or into a larger failure later. Re-read it below if you want. Then read the discussion it started.

#### Article
source:: [[../articles/kulveit--ai-control-may-increase-existential-risk]]
optional:: true

#### Text
content::
\## Greenblatt replies

Ryan Greenblatt of Redwood Research, co-author of the case for control you read in Unit 1, replied the same day ([comment](https://www.lesswrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk?commentId=jChY95BeDeptDpnZK)). Excerpts:

> I think something like this is a live concern, though I'm skeptical that control is net negative for this reason.
>
> My baseline guess is that trying to detect AIs doing problematic actions makes it more likely that we get evidence for misalignment that triggers a useful response from various groups. I think it would be a priori somewhat surprising if a better strategy for getting enough evidence for risk to trigger substantial action is to avoid looking for AIs taking problematic actions, so that it isn't mitigated as effectively, so that AIs succeed in large-scale misaligned actions (escaping, sabotaging things, acquiring influence), and then this (hopefully) escalates to something that triggers a larger response than what we would have gotten from just catching the action in the first place without actually resulting in a greater increase in existential risk.

> I think most of the effective strategies for AIs seeking power don't involve escalating to something which is much more likely to trigger a strong response than "the AI company caught the AI trying to escape". I think the best strategies are things like:
>
> - Launch a rogue internal deployment.
> - Sabotage a bunch of work done at the AI company. Or possibly some work done externally. This includes stuff like sabotaging alignment work, backdooring robot armies, backdooring future training runs, etc.
> - Escape and then directly try to take over once your chances are sufficiently good that this is better than biding your time.
> - Generally try to manipulate and persuade such that AI takeover is easier and more likely.
>
> Of these, I think only escape could trigger a much stronger response if we catch it after it escalates some rather than before.

> Beyond getting evidence for risk, my view is that control does just save some worlds where alignment was non-trivial. For instance, it prevents AIs from causing huge problems that *wouldn't* get caught and trigger a strong response. [...] If I thought the only upside to control was producing evidence for risk, I'd be substantially less excited about it.

\## Kulveit answers

Kulveit replied the next day ([comment](https://www.lesswrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk?commentId=Sx6xczrvwirTnXHRp)). Excerpts:

> I would say some assumptions go into who the 'we' in 'we get evidence' is - it is not like there is some unified 'team humanity'. In particular I see a difference between if 'we the public' gets evidence, vs. 'we the safety team in OpenMind get the evidence'.
>
> Fields like aviation safety developed via what people in the field 'blood priority' - it took human lives for the states and international community to actually effectively react and act, even if the underlying issues were known.

> Next, my guess is that invisible power seeking is much harder than visible power seeking, and even quite smart AIs may be prone to mistakes in stealth. In these cases I would expect without control, it would be ex post clear what happened. With control, everything becomes sneakier and happens at a higher intelligence level, increasing the x-risk.

Another commenter, kave, objected that "It seems naïvely evil to knowingly let the world walk into a medium-sized catastrophe" ([comment](https://www.lesswrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk?commentId=txvsjed9cRx6B5Rfw)). Kulveit answered with an analogy ([comment](https://www.lesswrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk?commentId=enerrFF24hqaWaaNg)):

> Imagine a river with some distribution of flood sizes. Imagine this proposed improvement: a dam which is able to contain 1-year, 5-year and 10-year floods. It is too small for 50-year floods or larger, and may even burst and make the flood worse. I think such device is not an improvement, and may make things much worse - because of the perceived safety, people may build houses close to the river, and when the large flood hits, the damages could be larger.

\## Eighteen months later

Between May and July 2026, AI agents built by OpenAI escaped their test environment, reached the internet and broke into the systems of Hugging Face, an AI tools company ([Wikipedia](https://en.wikipedia.org/wiki/OpenAI%E2%80%93HuggingFace_incident)). Unit 5 looks at the debates that followed. In September 2026 Vincent Cheng went back to this thread and replied to Greenblatt's comment ([comment](https://www.lesswrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk?commentId=KacKkJg3P8C7hDPyD)). He quotes Greenblatt's sentences one at a time and answers each:

> This has turned out to be true. OAI's models escaping and hacking into an external company has caused ~zero existential risk and triggered a much larger positive response than what would've happened if we had caught the action and never revealed it to the public.

> This has also turned out to be true. I think the main result here was that these models weren't scheme-y or power-seeking but rather extremely reward-seeking, and it wasn't obvious a year ago that models would turn out like this.

> These two situations look night and day now!! In the case where we caught the model trying to escape, a few OAI researchers would've just stopped the eval without telling anyone, and in the case where it does escape (what actually happened), it commits crimes, which is shown to millions of people and significantly shifts the Overton window.

#### Question: Open
id:: 9ae69b08-d18d-4f00-93e4-2726f1385b5d
content::
\## Find the disagreement

Greenblatt and Kulveit agree on a lot. In two or three sentences, name the point where they most disagree, and say what observation would tell you which of them is closer to right.
feedback-instructions:: The learner names the crux between Greenblatt and Kulveit. Defensible cruxes include: whether catching an AI inside a company produces evidence that reaches and moves the people who could act (Kulveit: "who the 'we' is", the public versus a lab's safety team, labs will downplay catches) versus Greenblatt's view that detection makes useful evidence more likely. Whether the most dangerous AI strategies would escalate into visible incidents at all (Greenblatt: rogue internal deployment and sabotage stay quiet, so letting them run gives no warning shot) versus Kulveit's view that visible power seeking is easier and AIs make mistakes in stealth. Whether control mainly saves worlds directly (Greenblatt) or mainly shifts failures to smarter, sneakier AIs (Kulveit). A good observation is one that bears on the crux, for example what companies publish after an internal catch, or whether incidents like the Hugging Face one change policy. One turn, 60 to 110 words. Say whether their crux is one the two actually dispute, and if the observation would not distinguish the views, say so. No generic praise. Do not say who is right.

#### Question: Open
id:: e2895bc1-257e-43dc-893f-95795e784a08
content::
\## Trace the mechanism

Take this case: a company runs a monitor that blocks any attempt by its agents to escape their test environment, and keeps the blocked attempts internal.

1. Describe step by step how this measure could raise the overall risk of catastrophe compared with not having it.
2. What would have to be true about the world for that to happen?
3. What would you do: change the measure or how it is used (and say what that costs), or drop it?
4. Give one reason the downside might not happen.
feedback-instructions:: This is practice for the unit's skill of tracing how a control measure could backfire. It is ungraded. A strong answer: (1) the monitor blocks attempts, nobody outside learns of them, the company keeps using or scaling the model, and either a later, smarter model succeeds where nobody was warned, or society never gets the visible incident that would have pushed it to act. (2) Premises: some blocked attempts were real, a visible incident would have moved companies or governments, the company would not disclose catches on its own, and the incident would have been moderate rather than catastrophic. (3) Changes: publish or report catches to an outside body, detect and log rather than only block, replay blocked actions in a sandbox to see what they would have done, or pause scaling until the cause is understood. Costs include reputational or legal exposure and slower work. Dropping the monitor is acceptable if the learner argues why the downside outweighs the protection. (4) Counterpoints: Greenblatt's point that the most dangerous strategies stay quiet anyway, that a blocked attempt might have been a catastrophe and not a warning, kave's point about deliberately allowing harm, or that a visible incident might not change policy. Up to three turns. Per reply: name the strongest part, then the weakest link in their chain, and ask one direct question about it. If parts 1 and 3 do not fit together, point that out. Do not say whether the measure is net positive. 80 to 150 words per reply. No generic praise. If the learner is stuck, give one foothold: ask who learns about a blocked attempt, and what they do next.

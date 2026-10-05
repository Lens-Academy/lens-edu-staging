---
id: 'eeaeddc8-4ac4-4c71-9322-dd1dd668c91c'
title: "Warning shots, revisited"
reading_minutes: 15
tutor_minutes: 14
tldr: "In Unit 1 you read Jan Kulveit's claim that control turns useful warning shots into quiet catches. Here Ryan Greenblatt replies and Kulveit answers. In 2026, after a real incident, Vincent Cheng argues that it bore out Kulveit's worry, and Gunnar Zarncke replies that control evaluations measure something else."
summary_for_tutor: "Unit 4 of AI Control Fundamentals. Builds on Jan Kulveit's 'AI Control May Increase Existential Risk', which the learner read in Unit 1 (optional re-read here). The learner reads comments from its thread: Ryan Greenblatt's reply in full (March 2025: 'a live concern', but it would be 'a priori somewhat surprising' if not looking for bad actions were the better way to get evidence, the most dangerous strategies such as rogue internal deployment and sabotage would not escalate into a visible incident anyway, 'without some effort on control, we might be much less likely to catch either', some control measures focus on after-the-fact detection, and control also saves worlds directly), excerpts of Kulveit's answer (the Sydney case, who 'we' is matters, the public versus a lab's safety team, aviation's 'blood priority', with control 'everything becomes sneakier and happens at a higher intelligence level', problems in the wild are more likely to cause a strong response, the crux is who 'we' is and what 'we caught' means, he is 'more optimistic' about after-the-fact detection, he is pessimistic about getting alignment work out of scheming AIs, and he thinks the more important line of defence may be between the labs and the rest of the world), kave's objection that knowingly letting a medium catastrophe happen seems 'naively evil' with Kulveit's dam analogy and his statement 'I'm not advocating for people to deliberately create warning shots', Vincent Cheng's September 2026 comment after the OpenAI and Hugging Face incident (the escape 'caused ~zero existential risk and triggered a much larger positive response', and had it been caught, 'a few OAI researchers would've just stopped the eval without telling anyone'. Cheng also says Greenblatt's 'cleanest case', a weak AI escaping and causing obvious damage, which Greenblatt found unlikely, 'has also turned out to be true', and that the models were reward-seeking rather than scheming), and Gunnar Zarncke's comment three days later (he accepts that control can let a lab detect incidents internally and hide them, so outsiders see 'a green checkbox', but says control is often understood as measuring whether a protocol holds under intentional subversion, which Kulveit's story does not cover, and that 'AI control used by external auditors would have different effects'). This is the 'works and makes things worse' kind of criticism. The second question is practice for tracing a backfire mechanism: mechanism, premise, a change or a case for dropping the measure, and a reason it might not happen. Do not tell the learner who is right."
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

Ryan Greenblatt of Redwood Research, co-author of the case for control you read in Unit 1, replied the same day:

#### Article
source:: [[../articles/greenblatt-comment-on-ai-control-may-increase-existential-risk]]

#### Text
content::
\## Kulveit answers

Kulveit replied the next day. He quotes parts of Greenblatt's comment and answers them. Here are his answers. ("OpenMind" is a made-up company name.)

#### Article
source:: [[../articles/kulveit-comment-on-ai-control-may-increase-existential-risk-comment]]
from:: I do understand this line of reasoning, but yes, my intuition differs.
to:: as opposed to some individual companies fixing the issues and some not.

#### Article
from:: Next, my guess is that invisible power seeking is much harder than visible power seeking
to:: I prefer these to be caused by less smart systems.

#### Article
from:: Crux is probably in: who the ‘we’ is, and details of ‘we caught’ means.
to:: I’m more optimistic about these.

#### Article
from:: My guesses where our intuitions differ the most
to:: and it seems plausible it is the more important one.)

#### Text
content::
Another commenter, kave, objected that "It seems naïvely evil to knowingly let the world walk into a medium-sized catastrophe" ([comment](https://www.lesswrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk?commentId=txvsjed9cRx6B5Rfw)). Kulveit answered:

#### Article
source:: [[../articles/kulveit-comment-on-ai-control-may-increase-existential-risk]]

#### Text
content::
\## Eighteen months later

Between May and July 2026, AI agents built by OpenAI escaped their test environment, reached the internet and broke into the systems of Hugging Face, an AI tools company ([Wikipedia](https://en.wikipedia.org/wiki/OpenAI%E2%80%93HuggingFace_incident)). Unit 5 looks at the debates that followed. In September 2026 Vincent Cheng went back to this thread and replied to Greenblatt's comment. He quotes three passages from Greenblatt's comment above and answers each in turn.

#### Article
source:: [[../articles/cheng-comment-on-ai-control-may-increase-existential-risk]]

#### Text
content::
Three days later Gunnar Zarncke left a new comment on Kulveit's post ([comment](https://www.lesswrong.com/posts/rZcyemEpBHgb2hqLP/ai-control-may-increase-existential-risk?commentId=7bruHf5quFdJseAoh)). Its first paragraph:

> I buy that AI control can let an AU [sic] lab detect real incidents internally and thus hide the effects outside the lab. Outside view is then a green checkbox "systems worked as designed", But AI control is often understood as measuring whether a protocol still holds under intentional subversion (control evals, remaining capability gap), which your story does not cover. AI control used by external auditors would have different effects.

#### Question: Open
id:: 1a9377ad-2256-4478-b63c-0d30e26a47bc
force-feedback:: first
content::
\## Find the disagreement

Suppose a lab catches its model trying to copy its own weights to an outside server. It reports the attempt only to a government safety institute, under a confidentiality agreement, and the public never hears of it. Would Kulveit count this as the kind of evidence that leads to a strong response, and would Greenblatt? What would you watch for over the following year to see whose view held up?
assessment-instructions:: Score out of 100. Context for grading: Jan Kulveit argues that control can turn moderate, visible AI incidents, which push the world to act, into quiet catches inside a company. He says it matters who the 'we' in 'we get evidence' is: the public getting evidence differs from a lab's safety team getting it. Fields like aviation became matters of public regulation through visible accidents, and he names the crux as who the 'we' is and what 'we caught' means. Ryan Greenblatt thinks looking for bad actions makes it more likely that evidence of misalignment triggers a useful response from various groups, that catching an attempt plays much like catching a success, and that without control fewer attempts would be caught at all. 35: Kulveit's likely view with a reason: probably not much, because the evidence stays with a small group out of public view, and in his account strong responses come from incidents the public sees. An answer that says a government institute is closer to the 'we' that matters than a lab's safety team, but that confidentiality still blunts the response, also earns these 35. 35: Greenblatt's likely view with a reason: yes, a catch is real evidence of misalignment that can trigger a response, and it was control that made the catch possible. 30: something to watch that would separate the views, such as whether the institute or the government acts (new rules, required changes at labs, disclosure), whether other labs change their practices, or whether nothing changes outside the one lab. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "Kulveit would doubt it, because the evidence stays with one institute and the public never sees it, and he thinks strong responses come from visible incidents. Greenblatt would count it, because the catch is clear evidence of misalignment that a government body can act on, and without control there would be nothing to report. I would watch whether the institute pushes for new rules or changes at other labs within the year. If nothing changes outside the one lab, Kulveit's view held up."
feedback-instructions:: The learner applies the Greenblatt and Kulveit disagreement to a confidential report to a government institute. Kulveit: who the 'we' in 'we get evidence' is matters, the public versus a lab's safety team, strong responses in fields like aviation came from visible accidents, and he names the crux himself: "who the 'we' is, and details of 'we caught' means". A confidential report to a government body sits between his two cases, so a reasoned answer either way is fine. Greenblatt: detecting bad actions makes useful evidence more likely, catching an attempt plays much like catching a success, and without control fewer attempts would be caught at all. Zarncke's point that control used by external auditors would work differently bears on this case too. A good observation is one that would come out differently on the two views, such as whether the institute acts or other labs change. One turn, 60 to 110 words. Say whether the learner's reading of each side fits, and if the observation would not distinguish the views, say so. No generic praise. Do not say who is right.

#### Question: Open
id:: e2895bc1-257e-43dc-893f-95795e784a08
force-feedback:: first
content::
\## Trace the mechanism

Take this case: a company runs a monitor that blocks any attempt by its agents to escape their test environment, and keeps the blocked attempts internal.

1. Describe step by step how this measure could make a catastrophe more likely than not having it.
2. What would have to be true about the world for that to happen? Give one reason it might not be true.
3. What would you do: change the measure or how it is used (say what protection the change keeps and what it costs), or drop it?
feedback-instructions:: This is practice for the unit's skill of tracing how a control measure could backfire. It is ungraded. A strong answer: (1) the monitor blocks attempts, nobody outside learns of them, the company keeps using or scaling the model, and either a later, smarter model succeeds where nobody was warned, or society never gets the visible incident that would have pushed it to act. (2) Premises: some blocked attempts were real, a visible incident would have moved companies or governments, the company would not disclose catches on its own, and the incident would have been moderate rather than catastrophic. Reasons a premise might not hold: Greenblatt's point that the most dangerous strategies stay quiet anyway, that a blocked attempt might have been a catastrophe and not a warning, or that a visible incident might not change policy. (3) Changes: publish or report catches to an outside body, detect and log rather than only block, replay blocked actions in a sandbox to see what they would have done, or pause scaling until the cause is understood. Costs include reputational or legal exposure and slower work. Dropping the monitor is acceptable if the learner argues why the downside outweighs the protection. kave's point about deliberately allowing harm is relevant to any answer that relies on letting incidents happen. Up to three turns. Per reply: name the strongest part, then the weakest link in their chain, and ask one direct question about it. If parts 1 and 3 do not fit together, point that out. Do not say whether the measure is net positive. 80 to 150 words per reply. No generic praise. If the learner is stuck, give one foothold: ask who learns about a blocked attempt, and what they do next.

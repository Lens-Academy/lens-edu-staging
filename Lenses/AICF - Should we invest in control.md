---
id: 'e515dbc5-48a2-4c72-8edb-98396923f9de'
title: "Should we invest in control?"
tldr: "Greenblatt and Shlegeris name the two claims their case for working on control rests on. Then Richard Ngo and aysja disagree about whether buying time with control leads anywhere if AI keeps getting more capable."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control), right after 'Using AI while it can still be controlled'. The learner reads the appendix of Greenblatt and Shlegeris's 'The case for ensuring that powerful AIs are controlled' (January 2024), 'Should AI-takeover-concerned people invest in control?'. It rests on two key claims: (1) we don't know how to ensure that AIs aren't scheming (which fails if non-scheming is trivial or quite likely doable to ensure), and (2) investment in control will substantially improve evaluation quality or produce techniques that substantially reduce risk from scheming AIs (which fails if control is too easy, so simple measures suffice, or infeasibly hard). The authors conclude investing in control should be a high fraction of the portfolio for preventing takeover. Then two comments: Richard Ngo's reply to Emmett Shear's objection that against an ever more powerful enemy you lose eventually (control is complementary with alignment and incremental, and raises the level of general intelligence at which things go wrong, buying time), and aysja's reply that this assumes no sharp left turns and that work on smaller systems carries over to the next ones. A sharp left turn is Nate Soares's term for a sudden jump in capabilities that earlier alignment work does not carry over to. Do not say who is right or whether control is worth investing in."
reading_minutes: 8
tutor_minutes: 10
tags:
  - reading
---
#### Text
content::
Greenblatt and Shlegeris end their post with an appendix on whether people worried about AI takeover should invest in control at all. It names the claims their case rests on.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: "# Appendix: Should AI-takeover-concerned people invest in control?"
to:: "this should be a high fraction of the portfolio for preventing takeover."

#### Question: Open
id:: 23e5cfd5-f740-42d7-b24a-497711f992ad
content::
The appendix names two key claims behind the case for working on control. State both. Then pick the one you find more open to doubt, say why, and say what you would need to see to change your mind about it.
placeholder:: A few sentences.
force-feedback:: first
assessment-instructions:: Score out of 100. The question asks for the two key claims behind the case for working on AI control, then for the learner's choice of the more doubtful claim with a reason and an observation. 25: the first claim, that we do not know how to ensure AIs are not scheming (making sure AIs do not secretly pursue their own goals is neither trivial nor reliably doable). 25: the second claim, that investing in control research will substantially improve control evaluations or produce techniques that substantially reduce risk from scheming AIs (control is neither so easy that simple measures suffice nor so hard that effort cannot help). 25: a reason the chosen claim is open to doubt that actually bears on that claim. Either claim may be chosen. 25: something that could actually be observed and that bears on the chosen claim, for example evidence about whether current models scheme in realistic settings, or control evaluations showing whether monitors improve with research effort. "More research" or "time will tell" earns 0 of these 25. Model answer, for the feedback, not a grading checklist: "First, we don't know how to make sure AIs aren't scheming. Second, putting effort into control will substantially improve evaluations or techniques, because control is neither trivially easy nor hopeless. I doubt the second most, because a much smarter model might find attacks no red team thinks of. If control evaluations kept catching strong red-team attacks as models got more capable, I would doubt it less."
feedback-instructions:: The learner just read the appendix "Should AI-takeover-concerned people invest in control?". In at most five sentences: say whether both claims are stated correctly and correct a misstated one in one sentence, say whether the reason and the observation fit the chosen claim, and name the most useful fix. Mention, if the learner missed it, that each claim fails in a named way: the first if non-scheming is trivial or quite likely doable to ensure, the second if control is too easy or infeasibly hard. Do not say which claim is weaker. If the learner says they do not understand, ask them what would make working on control pointless. No generic praise. At most two turns.

#### Text
content::
\## Does the window route lead anywhere?

When the post came out, Emmett Shear objected on Twitter that control is "a bad way to solve the problem" because against an ever more capable enemy you lose eventually. Richard Ngo posted his reply in the comments, and aysja answered Ngo. aysja mentions "sharp left turns", Nate Soares's term for [a sudden jump in capabilities that earlier alignment work does not carry over to](https://www.lesswrong.com/posts/GNhMPAWcfBCASy8e6).

#### Article
source:: [[../articles/ngo-comment-on-the-case-for-ensuring-that-powerful-ais-are-controlled]]

#### Article
source:: [[../articles/aysja-comment-on-the-case-for-ensuring-that-powerful-ais-are-controlled]]

#### Question: Open
id:: 443c06ce-6669-4300-af17-3f6f8c42e161
content::
Shear says that if the process continues, you lose eventually. Does Ngo's reply answer that, or change the question? What does aysja think Ngo's approach assumes, and what would you need to know to decide between them?
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner just read Richard Ngo's comment (quoting Emmett Shear's objection that against an ever more powerful enemy "you just lose eventually") and aysja's reply. Ngo does not claim control wins forever. He changes the goal: control is complementary with alignment and incremental, and each contribution raises the level of general intelligence at which things go wrong ("g(doom)"), buying time for automated alignment, governance and other efforts. aysja replies that the incremental approach assumes no sharp left turns and that work on smaller systems carries over to the next ones, and that if capabilities jump suddenly the iterative approach is very risky. She also thinks progress in a confused field often comes from one or a few people developing a robust theory rather than thousands contributing increments. What would decide it: whether capabilities rise smoothly or jump, and whether the time bought is actually used well, which links back to political will. In at most five sentences, check the learner's reading of each side, correct any misreading in one sentence, and say whether their "what would decide it" is something that could be observed. Do not say who is right. No generic praise. At most two turns.

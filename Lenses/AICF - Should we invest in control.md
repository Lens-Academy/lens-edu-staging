---
id: 'e515dbc5-48a2-4c72-8edb-98396923f9de'
title: "Should we invest in control?"
tldr: "Greenblatt and Shlegeris name the two claims their case for working on control rests on. Then Richard Ngo and aysja disagree about whether buying time with control leads anywhere if AI keeps getting more capable. Joe Carlsmith names the ways the window could fail: there may be none, it may be too short, or we may not be able to get useful work out of the AIs in it."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control), right after 'Using AI while it can still be controlled'. The learner reads the appendix of Greenblatt and Shlegeris's 'The case for ensuring that powerful AIs are controlled' (January 2024), 'Should AI-takeover-concerned people invest in control?'. It rests on two key claims: (1) we don't know how to ensure that AIs aren't scheming (which fails if non-scheming is trivial or quite likely doable to ensure), and (2) investment in control will substantially improve evaluation quality or produce techniques that substantially reduce risk from scheming AIs (which fails if control is too easy, so simple measures suffice, or infeasibly hard). The authors conclude investing in control should be a high fraction of the portfolio for preventing takeover. Then two comments: Richard Ngo's reply to Emmett Shear's objection that against an ever more powerful enemy you lose eventually (control is complementary with alignment and incremental, and raises the level of general intelligence at which things go wrong, buying time), and aysja's reply that this assumes no sharp left turns and that work on smaller systems carries over to the next ones. A sharp left turn is Nate Soares's term for a sudden jump in capabilities that earlier alignment work does not carry over to. Last, three excerpts of Joe Carlsmith's 'AI for AI safety' (March 2025, then at Open Philanthropy, not Redwood): the 'AI for AI safety sweet spot' (AIs capable enough to radically improve safety progress, risk evaluation and capability restraint if their capabilities can be elicited, while disempowering humanity is not an option for them given countermeasures), which he calls a salient target for capability restraint, and his steps (get to the sweet spot, stay there, elicit, do a lot of AI for AI safety). Section 4.2 lists ways to fail to benefit: no sweet spot, a sweet spot too narrow given the pace of progress, or failure to elicit capabilities. Section 5.1 gives three core objections: evaluation failures, differential sabotage, dangerous rogue options. This names the window route's own weakest premises and ties them to political will (capability restraint, investment). Do not say who is right or whether control is worth investing in."
reading_minutes: 11
tutor_minutes: 14
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
id:: a4b57f5d-b219-4e15-8dc5-a665513f4e65
content::
Two people decide not to work on control. One says AI developers will try so hard on alignment that their AIs almost certainly won't scheme. The other says that even the first AIs worth controlling will find a way past any monitor a lab could build. Which of the appendix's two key claims does each of them reject? Then say which objection you find more convincing, and what you could observe that would change your mind about it.
placeholder:: A few sentences.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Greenblatt and Shlegeris rest the case for working on control on two key claims. First, we do not know how to ensure that AIs are not scheming, which fails if non-scheming is trivial to ensure, or quite likely doable because developers will put in substantial effort and succeed. Second, investing in control will substantially improve evaluation quality or produce techniques that substantially reduce risk from scheming AIs, which fails if control is too easy, so simple measures suffice, or infeasibly hard, so effort cannot help, at all important capability levels. 25: the first person rejects the first claim, because they think developers can make sure their AIs do not scheme. 25: the second person rejects the second claim, because they think control is too hard for research to help. 25: a reason the chosen objection is more convincing that actually bears on it. Either may be chosen. 25: something that could actually be observed and that bears on the chosen objection, for example evidence on whether current models scheme in realistic settings despite alignment efforts, or control evaluations showing whether monitors keep catching strong red-team attacks as models get more capable. "More research" or "time will tell" earns 0 of these 25. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "The first rejects the claim that we don't know how to make sure AIs aren't scheming. The second rejects the claim that putting effort into control will substantially improve evaluations or techniques, because they think control is hopeless. I find the second more convincing, because a model capable enough to be worth controlling might find attacks no red team thinks of. If control evaluations kept catching strong red-team attacks as models got more capable, I would change my mind."
feedback-instructions:: The learner applies the appendix "Should AI-takeover-concerned people invest in control?" to two objections. The first person rejects the first key claim (we don't know how to ensure AIs aren't scheming), in the way the authors name: non-scheming is quite likely doable to ensure. The second rejects the second key claim (investment in control will substantially improve evaluations or techniques), in its named way: control is infeasibly hard. In at most five sentences: say whether both mappings are right and correct a wrong one in one sentence, say whether the reason and the observation fit the chosen objection, and name the most useful fix. Do not say which objection is stronger. If the learner says they do not understand, ask them what would make working on control pointless. No generic praise. At most two turns.

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

#### Text
content::
\## Where the window route could fail

Joe Carlsmith, then a senior advisor at Open Philanthropy and not part of Redwood, wrote ["AI for AI safety"](https://www.alignmentforum.org/posts/F3j4xqpxjxgQD3xXh/ai-for-ai-safety) in March 2025. His "sweet spot" is close to Greenblatt and Shlegeris's window: AIs useful enough to help with safety, but not able to take over given our countermeasures. By "security factors" he means three abilities from his earlier essay: making new AI capabilities safe, measuring the risk, and restraining AI development when needed. You read three short parts: the sweet spot itself, the ways we could fail to benefit from it, and his three core objections to using AI for safety work.

#### Article
source:: [[../articles/carlsmith-ai-for-ai-safety]]
from:: "I also want to highlight another concept that I find useful in thinking about AI for AI safety"
to:: "and that AI labor can help with this."

#### Article
from:: "## 4.2 Can we benefit from a sweet spot?"
to:: "Let’s look at those more directly now."

#### Article
from:: "## 5.1 Three core objections to AI for AI safety"
to:: "these have importantly different properties (more in my next essay)."

#### Question: Open
id:: 5172e65a-c122-472a-956c-febae0602cdf
content::
Carlsmith names three ways we might fail to benefit from a sweet spot. Which one would most weaken Greenblatt and Shlegeris's window route, and why? What would an AI company or a government have to do to make it less likely?
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner just read three excerpts of Joe Carlsmith's "AI for AI safety" (March 2025): the sweet spot (frontier AIs capable enough to radically improve safety progress, risk evaluation and capability restraint if their capabilities can be elicited, while disempowering humanity is not an option for them given our countermeasures), section 4.2 and section 5.1. The three ways to fail in 4.2: (1) no sweet spot, because AIs capable enough to help are already able to disempower us despite countermeasures, (2) a sweet spot too narrow given how fast the frontier advances, depending on its size, the default speed of progress and our ability to slow down, and (3) a sweet spot we cannot use because we cannot elicit the AIs' useful capabilities. Section 5.1 adds evaluation failures, differential sabotage of safety work by power-seeking AIs, and dangerous rogue options. Any choice is fine if the reason connects it to the window route. Useful links to will: a narrow window can be widened only by capability restraint (Carlsmith's step 2, which needs companies or governments willing to slow down), better countermeasures can widen the sweet spot (his own note), and elicitation needs investment in safety work during the window (his step 4, "adequate investment by relevant actors"). In at most five sentences: say whether the learner names one of the three correctly, whether the reason ties it to the window route, and whether the action they name would actually make that failure less likely and who would have to want it. Do not say whether the window route will work. If the learner says they do not understand, ask what would happen if AIs became able to take over in the same month they became useful for alignment research. No generic praise. At most two turns.

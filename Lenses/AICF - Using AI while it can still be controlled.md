---
id: 'e1ac84f5-cbab-4c34-b84c-19876ea7e366'
title: "Using AI while it can still be controlled"
tldr: "Control is not meant to work forever. Greenblatt and Shlegeris hope for a window in which AI is useful enough to speed up safety work but not yet too capable to control, and they say what has to be true for working on control to be worth it."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control). The learner reads four excerpts from Ryan Greenblatt and Buck Shlegeris, 'The case for ensuring that powerful AIs are controlled' (January 2024), whose earlier parts they read in Unit 1. (1) Control will not work for arbitrarily powerful AIs but could work for 'transformatively useful' AIs, those able to substantially reduce risk from later AIs, for example by massively accelerating safety R&D. Control should focus on the lead-up to the first catch, and a catch counts as a win because shutting down until there are credible solutions becomes far more likely. (2) Three properties: very dangerous, transformatively useful, uncontrollable. The basic argument is that labs will produce models that are very dangerous and transformatively useful before models that are uncontrollable. (3) How long the window lasts: by default perhaps 1 to 3 years between leading actors reaching transformatively useful AI and others imposing large exogenous risk. Political resources could be converted into spending on control and delay. Transformatively useful AIs could help build more delay (legible risk evaluation, help enforcing policy, compute tracking). An Amdahl's law argument that much more powerful AI adds little if human setup time is a bottleneck. Overall the gap is 'reasonably likely to be too short (e.g., 6 months or 1 year)' if capabilities go as fast as possible, but holding off on uncontrollable AI for several years is plausible. (4) The appendix on whether takeover-concerned people should invest in control: it rests on two claims, that we don't know how to ensure AIs aren't scheming, and that investment in control will substantially improve evaluations or techniques, which fails if control is too easy or infeasibly hard. Then two comments: Richard Ngo's reply to Emmett Shear's objection that against an ever more powerful enemy you lose eventually (control is complementary with alignment and incremental, and raises the intelligence level at which things go wrong, buying time), and aysja's reply that this assumes no sharp left turns and that work on smaller systems carries over. The point: the window route and its premises, and how much of it depends on political will (the length of the delay does). Do not say whether the window will exist."
reading_minutes: 15
tutor_minutes: 16
tags:
  - reading
---
#### Text
content::
In Unit 1 you read the first parts of Ryan Greenblatt and Buck Shlegeris's case for control. Here are two later sections. They say what control is for and for how long it can work, starting with the authors' own view of its limits. "Exogenous risk" in the second section means risk from AI built by other actors.

#### Article
source:: [[../articles/greenblatt+buck-the-case-for-ensuring-that-powerful-ais-are-controlled]]
from:: "# Control is likely achievable for early transformatively useful AIs"
to:: "before they produce models that are uncontrollable**."

#### Article
from:: "## For how long will we have controllable and transformatively useful AI?"
to:: "it's plausible that we can hold off on building uncontrollable AI for at least several years which could suffice."

#### Question: Open
id:: c1ebdf42-4a79-48de-802a-dfb1d4028bbc
content::
In your own words, what is the window the authors hope for, and how is control supposed to help during it? Then name one thing that decides how long the window lasts, and say whether it depends on how much AI companies and governments want to act on AI risk.
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner just read two excerpts from "The case for ensuring that powerful AIs are controlled". The window: a period when AIs are very dangerous and transformatively useful (able to substantially reduce risk from later AIs, for example by speeding up safety R&D a lot) but not yet uncontrollable. The authors call black-box control "a fundamentally limited approach" that will not work for sufficiently powerful models, so at some point more scalable approaches such as alignment are needed. Control lets developers use the early AIs safely even if they are scheming, so their work can reduce risk from later AIs. What decides the length: how fast leading actors push on to more powerful AI, whether others impose exogenous risk (the authors guess a default delay of 1 to 3 years), and whether political resources can be turned into spending on control and extra delay, plus whether the AIs themselves can help build delay. The delay clearly depends on political will. The authors think the gap is "reasonably likely to be too short (e.g., 6 months or 1 year)" if capabilities are developed as fast as possible, but that several years is plausible. In at most five sentences, say what the learner got right, correct any error in one sentence, and add the most important missing piece. No generic praise. At most two turns.

#### Text
content::
The authors also wrote an appendix on whether people worried about AI takeover should invest in control at all. It states the claims their case rests on.

#### Article
from:: "# Appendix: Should AI-takeover-concerned people invest in control?"
to:: "this should be a high fraction of the portfolio for preventing takeover."

#### Question: Open
id:: d2384ef8-c01a-451e-b761-ce7482edf8aa
content::
The appendix names two key claims behind the case for working on control. State them, and pick the one you find more open to doubt. What would you need to see to change your mind about it?
placeholder:: A few sentences.
feedback-instructions:: The learner just read the appendix "Should AI-takeover-concerned people invest in control?". The two key claims: (1) we don't know how to ensure that AIs aren't scheming (it fails if non-scheming is trivial or quite likely doable to ensure), and (2) investment in control will substantially improve evaluation quality or produce techniques that substantially reduce risk from scheming AIs (it fails if control is too easy, so simple measures suffice, or infeasibly hard). Either claim is a fine choice. A good answer gives a reason and something observable that bears on it, for example evidence that current models do or do not scheme in realistic settings, or control evaluations that do or do not show monitors getting better with research effort. In at most five sentences: check both claims are stated correctly, say whether the reason and the observation fit the chosen claim, and fix the weakest part. Do not say which claim is weaker. No generic praise. At most two turns.

#### Text
content::
\## Does the window route lead anywhere?

When the post came out, Emmett Shear objected on Twitter that control is "a bad way to solve the problem" because against an ever more capable enemy you lose eventually. Richard Ngo posted his reply in the comments, and aysja answered Ngo.

#### Article
source:: [[../articles/ngo-comment-on-the-case-for-ensuring-that-powerful-ais-are-controlled]]

#### Article
source:: [[../articles/aysja-comment-on-the-case-for-ensuring-that-powerful-ais-are-controlled]]

#### Question: Open
id:: 443c06ce-6669-4300-af17-3f6f8c42e161
content::
Shear says that if the process continues, you lose eventually. Does Ngo's reply answer that, or change the question? What does aysja think Ngo's approach assumes, and what would you need to know to decide between them?
placeholder:: A few sentences.
feedback-instructions:: The learner just read Richard Ngo's comment (quoting Emmett Shear's objection that against an ever more powerful enemy "you just lose eventually") and aysja's reply. Ngo does not claim control wins forever. He changes the goal: control is complementary with alignment and incremental, and each contribution raises the level of general intelligence at which things go wrong ("g(doom)"), buying time for automated alignment, governance and other efforts. aysja replies that the incremental approach assumes no sharp left turns and that work on smaller systems carries over to the next ones, and that if capabilities jump suddenly the iterative approach is very risky. She also thinks progress in a confused field often comes from one or a few people developing a robust theory rather than thousands contributing increments. What would decide it: whether capabilities rise smoothly or jump, and whether the time bought is actually used well, which links back to political will. In at most five sentences, check the learner's reading of each side, correct any misreading in one sentence, and say whether their "what would decide it" is something that could be observed. Do not say who is right. No generic praise. At most two turns.

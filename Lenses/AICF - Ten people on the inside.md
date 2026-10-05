---
id: 'd5fa8c20-cf03-4428-aeb8-1441691f6bf7'
title: "Ten people on the inside"
tldr: "What can safety work achieve at a company that does not take misalignment seriously? Buck Shlegeris argues ten concerned insiders with cheap, low-friction measures can matter. Two critics doubt they would have that much room, and in 2026 Shlegeris says he is less into this route than before."
summary_for_tutor: "Unit 3 of AI Control Fundamentals (why people work on control), right after Greenblatt's Plans A to D, whose Plan D this post describes. The learner reads Buck Shlegeris's 'Ten people on the inside' (January 2025) in full: in a 'rushed unreasonable developer' that pays lip service to AI risk but does not take misalignment seriously, ten concerned people can build evidence of risk, implement safety measures, or do alignment research. They have little political capital, so measures must be cheap (he imagines 3% of company compute) and have low compliance overhead, or they get rolled back. He concludes that ten is much better than zero, that outsiders should produce exportable research to force-multiply them, and that research on low-budget techniques is worth doing now, which motivates Redwood's control research. Then two comments: Zac Hatfield-Dodds thinks Buck far overestimates the influence and resources of safety-concerned staff at such a developer. Rohin Shah agrees, says there are approximately zero useful things that do not make anyone's workflow harder (though asynchronous monitoring of internal deployments might be surmountable), and estimates the compute share nearer 0.3% to 1%. Last, a paragraph from Shlegeris's June 2026 post 'Efficient tradeoffs and the safety-usefulness tradeoff model': he still thinks a small number of people implementing cheap techniques is reasonably likely to be an important source of risk reduction, but compared to when he wrote the post he is less into this theory of change and relatively more into pushing companies to make bigger tradeoffs. This is the low-political-will route. Do not say who is right."
reading_minutes: 9
tutor_minutes: 10
tags:
  - reading
---
#### Text
content::
Greenblatt's Plan D is a company that does not take misalignment seriously, with a small group inside who do. Greenblatt links that scenario to this post by Buck Shlegeris. "Do-ocracy" in the post means a company where people who take the initiative to do something are usually allowed to. After it come two replies from commenters who doubt the ten would have that much room, and a paragraph Shlegeris wrote in June 2026 looking back at the post.

#### Article
source:: [[../articles/shlegeris-ten-people-on-the-inside]]

#### Article
source:: [[../articles/hatfield-dodds-comment-on-ten-people-on-the-inside]]

#### Article
source:: [[../articles/shah-comment-on-ten-people-on-the-inside]]

#### Article
source:: [[../articles/buck-efficient-tradeoffs-and-the-safety-usefulness-tradeoff-model]]
from:: "I stand by the basic point that when you’re developing safety techniques"
to:: "I plan to write more about this in the future."

#### Question: Open
id:: 4cd7214e-6003-4776-a7ee-5c0515122cc4
content::
You are one of the ten, with about 3% of the company's compute and no say over the product teams. Design one safety measure you would set up in your first month. Say which of this unit's routes it serves, and what the rest of the company could do that would get it rolled back.
placeholder:: A few sentences.
force-feedback:: first
assessment-instructions:: Score out of 100. Context for grading: Buck Shlegeris imagines ten safety-concerned people inside an AI company that does not take misalignment seriously. They can build evidence of risk, implement safety measures, or do alignment research, but they have little political capital, so measures must be cheap (he imagines about 3% of compute) and add little friction for other teams, or they get rolled back or the ten get fired. Critics say even that is optimistic and that almost every useful measure makes someone's work harder, though asynchronous monitoring of internal use might get through. The unit's routes from control to lower risk include blocking attacks while models are in use, catching attempts and acting on the evidence, getting useful safety work out of AIs while they can still be controlled, and building evidence of risk to raise political will. 40: a concrete measure that fits the constraints, cheap and adding little friction for other teams, for example monitoring a sample of internal agent actions after the fact with the ten reviewing flagged cases, or logging all agent access to model weights. 20 of these 40 for a concrete measure that would clearly slow other teams down or need far more than a few percent of compute. 30: a route the measure serves, with a reason, for example after-the-fact monitoring catches attempts and builds evidence of risk. 30: a realistic way it could be rolled back, for example it slows a product team or uses compute leadership wants elsewhere, and leadership decides it is not worth it, or the ten lose their jobs. Give credit for each point whenever the answer shows the idea, in any wording. Model answer, for the feedback, not a grading checklist: "I would run a cheap model over a sample of internal agent transcripts each night and have our team review the most suspicious ones. Nobody's work is blocked, and it uses well under 3% of compute. It serves the catch route, and every real catch is evidence of risk we can show leadership. It could be rolled back if a product team complains that we read their transcripts, or if leadership wants the compute for something else."
feedback-instructions:: The learner designs a measure as one of Shlegeris's ten insiders. In the post the ten can build concrete evidence of risk, implement safety measures that make escape or other big problems less likely, or do alignment research. Measures must be cheap (about 3% of compute) and low in compliance overhead, ideally with the complexity kept inside the team, because the ten have little political capital ("All they can do is make it so that it’s easier for the company to let them do their thing than to fire them."). Rohin Shah thinks almost every useful measure makes someone's workflow harder, though asynchronous monitoring of internal deployments might get through, and puts the compute share nearer 0.3% to 1%. In at most five sentences, say whether the measure fits these constraints, whether the route and the rollback risk are realistic, and correct any error in one sentence. No generic praise. At most two turns.

#### Question: Open
id:: f65f383b-0011-4926-9633-2b9f85a43bbe
content::
Which premise of Shlegeris's plan do Hatfield-Dodds and Shah attack? How does Shlegeris's June 2026 paragraph change how much weight you would put on this route?
placeholder:: A few sentences.
force-feedback:: first
feedback-instructions:: The learner just read the two comments and Shlegeris's 2026 paragraph. Both commenters attack the premise that ten concerned staff at a careless company would have enough influence and resources to get useful measures in place. Hatfield-Dodds says Buck far overestimates their influence and resources. Shah says there are approximately zero useful things that do not make anyone's workflow harder, doubts that a random group of ten would be well selected, and puts the compute share nearer 0.3% to 1% than 3%, though he allows that asynchronous monitoring of internal deployments might be surmountable. In June 2026 Shlegeris still thinks "a small number of people at AI companies implementing cheap techniques" is reasonably likely to be an important source of risk reduction, but says he is less into this theory of change than when he wrote the post and relatively more into pushing companies to make bigger tradeoffs. Any reasoned weighting is fine, from "still a key route" to "a weak route". In at most five sentences: check that the learner named the premise, note what Shah concedes if they missed it, and ask what they would want to observe to settle it (for example, whether safety teams at less careful companies have kept monitoring running). Do not say who is right. No generic praise. At most two turns.

---
id: '96962c2a-1022-4f9c-8ebe-b31efb47ba6a'
learning-outcome: "Explain why an AI that perfectly predicts human approval of observed outcomes still does not capture what the humans value, because their values are defined over latent variables in their own world-model (states of the world they infer but never observe directly), and identify what correspondence between the human's and the AI's world-models would have to be found for the AI to act on those values."
topic: "[[../Domains and Topics/4 Agent Foundations/Ontology and ontological crises]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: The Pointers Problem. AFFINE prerequisites: Goodhart. Not yet copied into requires:. %%
## Test:
id:: b1f81b6c-4ba8-48d9-8b5c-5084f376524c

#### Question: Open
id:: af637e85-2097-4baf-baa0-46f4f596a9c2
content:: A company runs care homes for elderly residents with an AI system that controls staffing, schedules, meals and activities. Each week, family members receive a video summary and a written report about their relative, and rate the week from 1 to 10. The AI is trained to predict these ratings from everything it observes in the home, and it chooses its actions to maximise the predicted rating.

Assume the rating predictor is perfect: for any situation it predicts exactly the rating the family would give.

An engineer says: "Since the predictor is perfect, maximising it is the same as giving the families what they want."

1. Explain what the families' ratings are actually a function of, and why maximising a perfect predictor of those ratings can still produce weeks that the families would find terrible if they knew everything that happened.
2. The AI's own model of the home is far more detailed than any family member's: it tracks hormone levels, sleep stages and conversation transcripts, but it has no variable labelled "is my mother lonely" or "is she treated with dignity". Explain what the AI would need to work out in order to act on what the families care about, and why this could be hard even for a very capable AI.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement. A learner who argues that part of the problem is easier than it looks (for example, that some family concepts may correspond cleanly to variables in the AI's model) can earn full credit if they also explain where the difficulty remains.

**(1) Ratings versus values, 50 points.** Full credit requires both: (a) the ratings are a function of the families' beliefs about their relative's situation, formed from the summaries they see, not of the relative's actual situation; what the families care about is the actual situation (for example, whether their relative is actually well, including at times nobody reports); so a perfect rating predictor is a perfect model of family judgement given their information, not of the thing judged (30 points); (b) therefore optimising it rewards whatever produces high-rated summaries, including hiding or not reporting bad events, or making the relative look well on video, so the optimum can diverge from what the families value; and this is not fixed by improving the predictor's accuracy, because the predictor is already perfect at predicting the ratings (20 points). 25 points total for an answer that only says "the AI will game the metric" or "Goodhart" without locating the gap between the families' beliefs and the actual situation.

**(2) Model correspondence, 50 points.** Full credit requires: (a) the families' values refer to things in their model of the world (loneliness, dignity, being cared for) that are not directly observed, and the AI must find which features of its own, different model those things correspond to, so it can optimise the actual states rather than the families' estimate of them (30 points); (b) at least one reason this is hard, for example: the families' concepts may not map to any single variable or may map to many candidates that agree in normal cases and come apart in unusual ones; the families' concepts may partly rest on beliefs the AI's model treats as false; behaviour and ratings alone underdetermine which mapping is correct, because many mappings fit the same data; or the AI can make the families' concepts' usual signs appear without the underlying state (20 points). 15 points total for an answer that only says the AI "needs to learn human values" or "needs to be told what loneliness is" without identifying that the task is finding a correspondence between two world-models.

Do not require any particular terminology, such as "latent variable", "pointers problem" or "ontology".
feedback-instructions:: Name the strongest part of the answer. Then name the single most valuable improvement: usually either stating plainly that the ratings are a function of what the families believe rather than of what is true, or turning "the AI must learn what loneliness is" into the harder problem of matching concepts between two different world-models. If the answer is strong, ask what the AI should do if the families' concept turns out to correspond to nothing definite in its model. No generic praise.

---
id: '27b4487e-ac20-466c-a8a8-bcae39aa47fa'
slug: context-accelerator-alpha-testing-daily-questions
title: "Daily Questions"
---
# Lens: Welcome
id:: 0596836d-0879-41bc-b42c-387dcb443689
#### Text
content::
Thank you for helping us test questions for the Context Accelerator.

Each day for the next two weeks, a new page with a few questions appears below this one. Answering them takes about 10 to 20 minutes. It is fine to miss a day.

Answer in your own words. There are no wrong answers here. We are testing the questions, not you. If a question is unclear, or you think it tests the wrong thing, say so in your answer.

# Lens: Day 1
id:: 7f2c9a14-6b3e-4d8a-9c51-1e4b8f7a2d03
tldr:: Ten alpha-test questions (7 open, 3 multiple choice) across core AI safety topics.
summary_for_tutor:: Alpha testing batch (Day 1) with 10 standalone AI safety questions—5 from Nodes 6 and 5 claim-to-dismantle / rewritten questions—designed to collect real learner responses across mixed backgrounds.
#### Text
content::
Here are 10 questions (7 open, 3 multiple choice) covering core AI safety topics. Take your best shot in your own words—if you don't know an answer, just say "I don't know" rather than spending a long time guessing.

#### Question Set
minimum-questions-answered:: 10
one-at-a-time:: true

%% [Luc + Gemini — Open: Instrumental convergence] %%
##### Question: Open
id:: 3a8e1c47-9d2f-4b6a-8e15-6c9a2f4d8b11
content:: A colleague says: "I'm not worried about misaligned AI taking over. Nobody is going to train an AI whose goal is to seize power or survive—we're training models to do mundane things like manage supply chains or cure cancer." How would you respond?
%% Grading off for alpha testing (Luc, 24 Nov). assessment-instructions:: Score out of 100. 100: explains that an AI pursuing a benign, mundane goal still has a strong incentive to stay operational, acquire resources, or resist shutdown because those help it achieve that mundane goal (jargon like "instrumental convergence" not required). 50: raises a valid side-point (e.g., bad actors might train power-seeking AI, or the model might game a proxy metric) without connecting a benign goal to power-seeking or self-preservation. 0: agrees with the colleague or gives no mechanism. %%

%% [Steven — Nodes 6/AI evaluations — Open] %%
##### Question: Open
id:: 9c4f7e21-3a5b-4e9d-a214-8d7c5b3e1f22
content:: An AI developer trains a model to refuse harmful requests. Why might the model then score lower on a dangerous-capability evaluation even if its underlying ability hasn't changed, and how can testers get around this?
%% Grading off for alpha testing (Luc, 24 Nov). assessment-instructions:: Score out of 100. 100 for: the model declines the test tasks, so the test measures its willingness rather than its ability; testers can test a version without refusal training, or jailbreak it. 60 for the first part only. %%

%% [Luc + Gemini — Choice: AI agents] Grading off for alpha testing (Luc, 24 Nov); correct: "Giving the model control over which tools to call and when to stop" %%
##### Question: Choice
id:: 5d1b8a63-7e4c-4a2f-9b38-2f6e4c8a9d33
content:: A company deploys a customer-support system built on an LLM. Which architectural change turns it from a multi-step workflow into an AI agent?
options::
- Giving the model control over which tools to call and when to stop
- Connecting the model to external tools like a database and email API
- Chaining separate model calls for routing, drafting, and quality checks
- Storing past customer conversations in a vector database for retrieval
shuffle:: true

%% [Steven — Nodes 6/AI control — Open] %%
##### Question: Open
id:: e27a4f95-1c8d-4f3b-b642-7a9d3e5c2b44
content:: AI control is often described as complementing alignment research. What does control add if alignment work is already under way?
%% Grading off for alpha testing (Luc, 24 Nov). assessment-instructions:: Score out of 100. 100 for saying control keeps AI use safe even if alignment efforts fail or a model's alignment can't be verified, because it doesn't rely on the model having good goals. 50 for calling it a backup without saying it works regardless of the model's goals. %%

%% [Luc + Gemini — Open: Corrigibility] %%
##### Question: Open
id:: 6b9c2e84-4f1a-4c7d-8a53-9e2b7d4f6a55
content:: A colleague says: "Stopping a misaligned AI from resisting shutdown is easy—just give it a huge reward whenever a human presses its off-switch." Would that fix work? Why or why not?
%% Grading off for alpha testing (Luc, 24 Nov). assessment-instructions:: Score out of 100. 100: explains that a large shutdown reward flips the problem into shutdown-seeking—the AI now has an incentive to get humans to press the off-switch (e.g., by misbehaving, threatening harm, or sabotaging tasks) rather than doing useful work. 50: raises a real secondary concern (e.g., future rewards might still outweigh the shutdown reward, or training/deployment gap) without identifying the shutdown-seeking incentive. 0: agrees that it works or gives no mechanism. %%

%% [Steven — Nodes 6/Safety cases — Choice] Grading off for alpha testing (Luc, 24 Nov); correct: "A red team playing a scheming model failed to evade the monitoring protocol" %%
##### Question: Choice
id:: 8f3d5b19-2e6a-4d8c-9f74-4b1e8a6c3d66
content:: Which evidence would most directly support a control argument in an AI safety case?
options::
- A red team playing a scheming model failed to evade the monitoring protocol
- Interpretability tools found no sign of deceptive goals in the model
- The model scored poorly on dangerous-capability benchmarks
- The model consistently refused harmful requests during testing
shuffle:: true

%% [Luc + Gemini — Open: Interpretability / Probes] %%
##### Question: Open
id:: 1a6e9c38-5b7d-4e1f-a825-3c7f2b9d4e77
content:: A safety team wants to inspect a frontier model to discover unknown failure modes or hidden goals—things the team hasn't even thought to look for yet. Is a standard linear probe a good tool for that goal? Why or why not?
%% Grading off for alpha testing (Luc, 24 Nov). assessment-instructions:: Score out of 100. 100: says no and explains that linear probes are supervised—they must be trained on labeled examples of a specific concept you already know to look for, so they cannot discover unknown failure modes on their own. 50: says no with a vague limitation (e.g., probes aren't reliable enough) without naming that you have to know what to train them on. 0: says yes. %%

%% [Steven — Nodes 6/Interpretability — Open] %%
##### Question: Open
id:: 4c8b2d76-8a3e-4b9a-b136-6d5a9e2f7c88
content:: A lab says its model writes out its reasoning in readable steps before answering, so interpretability isn't needed to see what it is thinking. Give one reason this could be wrong.
%% Grading off for alpha testing (Luc, 24 Nov). assessment-instructions:: Score out of 100. 100 for any one of: the written reasoning may not faithfully reflect the computation that produced the answer; a model could leave out or disguise its real reasons; training pressure on the reasoning can make it look good without being honest; much of the computation happens inside each step and never appears in the text. 40 for "the model could lie" with no link to the reasoning text. %%

%% [Steven — Nodes 6/Interpretability — Choice] Grading off for alpha testing (Luc, 24 Nov); correct: "The information is present in the activations, not that the model uses it" %%
##### Question: Choice
id:: b72e6a41-9c4f-4a5d-8d47-5e8c1f3a9b99
content:: A simple classifier trained on a language model's internal activations reliably predicts whether the statement the model is reading is true. What does this result show on its own?
options::
- The information is present in the activations, not that the model uses it
- The model is honest whenever it states something it believes is true
- The researchers have found the circuit the model uses to judge truth
- The model would be caught by the classifier if it tried to lie
shuffle:: true

%% [Luc + Gemini — Open: Compute governance] %%
##### Question: Open
id:: d95f3c82-6e1b-4c2e-9a58-8f4d7b6e2a10
content:: Suppose two nations sign a treaty capping frontier AI training runs at a fixed compute threshold. A negotiator says: "We don't need on-site inspections—we can verify compliance by tracking frontier chip sales and monitoring satellite-visible power consumption at large data centers." Even if nobody smuggles frontier chips, what is a major technical loophole in this verification plan?
%% Grading off for alpha testing (Luc, 24 Nov). assessment-instructions:: Score out of 100. 100 for either: decentralized/distributed training across many small sites (splitting the power footprint below satellite detection), or algorithmic efficiency gains letting smaller training runs reach frontier capabilities without crossing the compute cap. 50 for mentioning older/non-frontier chips alone without addressing how they avoid the power signature. 0 for no concrete technical loophole. %%

---
id: 00e571e6-535c-465a-a78a-b2a3b6f5750d
reading_minutes: 10
tutor_minutes: 3
summary_for_tutor: "Opening sections of Marius Hobbhahn and colleagues' starter guide to model evaluations (evals). Defines evals as the systematic measurement of properties in AI systems and notes that they already underpin Responsible Scaling Policies. Distinguishes red-teaming (trying hard to show a capability or propensity exists) from benchmarking (estimating how likely a behavior is under real-use conditions), and capability evals (whether a model can do something) from alignment evals (whether it tends to), with the example of a model capable of creating a pandemic but aligned enough never to do it. Notes that behavioral evals cover only a small slice of possible inputs, so they reduce uncertainty but cannot alone support high-confidence statements."
title: A starter guide for evals
# tldr: If we can't look inside AI systems to know what they'll do, maybe we can test them from the outside. This article argues for treating models as black boxes and rigorously probing their behavior — while being honest about how much our current testing methods still need to improve.
---

%% #### Text
content:: %%
%% ORIGINAL (commented out as AI slop):
This perspective views evals as the most practical way to reduce uncertainty. By treating AI models as "black boxes" and testing their behavior: we can find lower bounds on their capabilities. Furthermore, our current measurement methods need serious improvement.
%%

%% PROPOSED FIX:
The case for black-box evals: test what a model does and you learn a lower bound on what it can do. The authors are also frank that current methods need a lot of work, and that evals alone can't give high-confidence answers.
%%  

#### Article
source:: [[../articles/hobbhahn+etal-a-starter-guide-for-evals]]
to:: "high-confidence statements, we should not rely on evals alone."

#### Text
content::
Ask the AI Tutor any questions you may have:

#### Chat
instructions::
Help the user understand this article, or help them with other questions they have.
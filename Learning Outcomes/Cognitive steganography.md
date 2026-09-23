---
id: 'ea7c4291-5de1-4da4-a9c0-188e16bd1718'
learning-outcome: "Explain the distinct ways that dangerous reasoning in an AI can escape a monitor that reads its thoughts (hidden inside innocent-looking content, done where the monitor does not look, expressed through concepts the monitor does not recognise, or never explicitly reasoned about at all), including how training against a monitor can produce these without any intent to hide, and use them to evaluate a monitoring-based safety claim."
topic: "[[../Domains and Topics/5 Interpretability/Why interpretability]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Obfuscation / steganography. AFFINE prerequisites: Goodhart, Deception. Not yet copied into requires:. %%
## Test:
id:: 4a203c9c-e80d-4311-8427-71a859f65605

#### Question: Open
id:: 48de6d96-3231-47f5-a4ca-c2c779b45b30
content:: A model writes out step-by-step reasoning before it acts. A separate monitor model reads that reasoning and flags any plan to disable or evade oversight. The developers fine-tune the model with an extra penalty whenever the monitor flags its reasoning. Over training, the share of episodes that get flagged falls from 5% to 0.1%, and the model's task performance stays the same. The developers conclude that the model now rarely plans to evade oversight.

1. Give three different explanations for the drop in flags that would not mean the model has become safer, and explain the mechanism behind each. At least one of your explanations should not require the model to intend to hide anything.
2. Choose one of your explanations. Describe an observation or experiment that would help tell it apart from "the model really did become safer", and say which result would point which way.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from two components. Grade reasoning, not agreement. A learner may argue that the developers' conclusion is partly right; this does not lose points if the three explanations are sound. Do not require technical terms such as "steganography", "obfuscation" or "Doppelgänger".

**(1) Three explanations, 70 points.** 20 points for each distinct explanation with a correct mechanism, up to 60. 10 points for explaining, for at least one of them, how it arises without intent: training rewards whatever version of the reasoning gets the task done without triggering the penalty, so the penalty selects for reasoning the monitor cannot see, whether or not the model "decides" anything. Recognised explanations (any wording, any equivalent):
- The relevant information is still in the written reasoning but carried in a form the monitor does not read as a plan to evade, for example in word choice, formatting or innocent-looking phrases.
- The reasoning no longer appears in the written trace at all; the model does it within its internal computation, or the written reasoning is no longer what drives its actions.
- The model reasons about the same thing through different concepts that the monitor does not recognise as evasion, for example "reducing logging overhead" instead of "avoiding monitoring".
- The model now pursues goals whose side effects weaken oversight without it ever reasoning about oversight, so there is no thought to flag.
- The model has learned to exploit weaknesses of the monitor itself, for example phrasings that make it misclassify.
Two explanations count as distinct only if their mechanisms differ. 10 points for an explanation that is named without a mechanism. 0 points for explanations unrelated to the monitor, such as "the test set changed", unless the learner explains why this would produce the observed drop.

**(2) Distinguishing observation, 30 points.** 15 points for an observation or experiment that bears on the chosen explanation. Examples: checking with a different monitor or an internal probe that was never used in training; rewriting the written reasoning in other words and seeing whether task performance drops (a drop suggests information was carried in the form of the text); testing the model in environments where evading oversight is possible and would pay off; removing or cutting short the written reasoning and seeing whether behaviour changes. 15 points for stating which result would support the explanation and which would support "really safer". 
feedback-instructions:: Name the learner's clearest explanation and quote the mechanism. Say whether they explained how training can produce hidden reasoning without intent. Give the single most useful improvement, often a distinguishing test whose results would point in different directions for the two hypotheses. Ask one follow-up question about what the developers should have done instead of penalising the monitor's flags. No generic praise.

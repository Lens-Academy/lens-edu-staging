---
id: 'f5faf87f-c139-452e-a37d-46e9d13b44e1'
learning-outcome: "Distinguish a disagreement or confusion caused by the concepts in use (an ontology that lumps distinct things together, or in which one side's question cannot be stated) from a disagreement about evidence within shared concepts, and propose a re-carving of the concepts that turns the question into one that evidence can settle."
topic: "[[../Domains and Topics/4 Agent Foundations/Ontology and ontological crises]]"
stage: intermediate
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Ontology. AFFINE prerequisites: none. Not yet copied into requires:. %%
## Test:
id:: 1fe8018c-7e3f-4afe-9518-c10508c6ea10

#### Question: Open
id:: bb7eadf3-82be-4cd9-b17a-0f70060070b9
content:: Three disagreements come up at an AI safety workshop.

**A.** Two forecasters are asked "Will AI takeoff be fast?" Forecaster 1 says 70% yes, Forecaster 2 says 20% yes. Asked to explain, Forecaster 1 says "fast" means that within two years of the first AI that can do most AI research, AI is far beyond humans. Forecaster 2 says "fast" means there is no period of visible economic disruption before AI transforms the world.

**B.** Two researchers agree that a model "sandbagged" an evaluation if its score is well below what the same model reaches after a standard fine-tuning procedure designed to draw out the capability. They disagree about whether a particular model sandbagged a particular evaluation. Neither has yet run the fine-tuning procedure.

**C.** An ML engineer says: "The model has no goals. It was trained to predict the next token, and asking what it 'wants' is a confused question." A safety researcher replies: "When we put it in an agent scaffold it pursues objectives across dozens of steps and works around obstacles. Talk about next-token prediction does not describe that."

For each disagreement, say whether collecting more evidence is the main thing needed to resolve it, or whether something else must happen first. Where something else must happen first, say what it is, give a concrete way to do it, and say what question it would let the two sides settle.
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Grade the reasoning, not agreement with any particular framing. An answer that classifies a case differently from the guide below can earn full credit for that case if it gives a coherent reason grounded in the case as described.

**(A) Takeoff, 35 points.** Full credit: recognises that the two forecasters are answering different questions under one word, so their numbers may not conflict at all and more evidence about "takeoff speed" cannot resolve a disagreement that may not exist; proposes splitting the concept into separately stated, operational questions (for example, time from AI-research automation to far-superhuman AI; whether there is a warning period of visible disruption) and notes that each can then get its own probability or evidence. 20 points if the answer sees that the word is ambiguous but only says "define terms" without proposing a concrete split, or without noticing that the numbers may be compatible. 5 points or fewer if it treats A as a plain evidence dispute.

**(B) Sandbagging, 25 points.** Full credit: recognises that the concept is already shared and operational, so this is an ordinary empirical disagreement and running the agreed procedure is the main next step. Do not penalise an answer that also notes a residual conceptual question (for example, whether the fine-tuning procedure fully elicits capability, so the operational definition may undercount sandbagging), provided it still identifies evidence as the main route. 10 points if the answer calls B conceptual without a specific reason.

**(C) Goals, 40 points.** Full credit: recognises that the two sides describe the system in different frameworks: one in terms of the training objective, one in terms of behaviour in deployment. Within the engineer's framework the researcher's question has no place to be stated, so neither side can refute the other with evidence yet. The answer proposes a bridging concept stated in terms both sides accept (for example, an operational, behavioural test of goal-directedness such as whether the system redirects towards the same outcome when obstacles or starting conditions change; or a mechanistic question about whether internal representations of an outcome drive its choices) and says what observation would then settle the question. 20 points if it identifies that the two use different frameworks but proposes no concrete bridging concept, or proposes one that only one side's framework can express. Accept an answer that argues C is partly empirical, provided it also identifies the framework mismatch that stops evidence from settling it at present.

Do not require any particular terminology such as "ontology". A fluent answer that says "they should define their terms" for every case, without distinguishing B from A and C, cannot score above 35.
feedback-instructions:: Name the case the learner diagnosed best and why the diagnosis was sound. Then name the single most valuable improvement: usually either a missing concrete re-carving (a split or bridging concept precise enough that evidence could settle it) or treating B like A and C. If they proposed a re-carving, ask one question that tests whether it would actually let evidence decide. Do not give generic praise.

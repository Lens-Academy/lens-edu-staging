---
id: '48f80624-ce91-4c3f-8198-ef4cf46995dc'
learning-outcome: "Explain why an agent whose values are defined over the entities of its world-model faces an ontological crisis when it adopts a better model in which those entities dissolve or split apart, and evaluate rules for carrying the values over to the new model (such as re-grounding the value on what the old entity turned out to be, choosing one of the successor concepts, or dropping the value) by the behaviour each rule would produce."
topic: "[[../Domains and Topics/4 Agent Foundations/Ontology and ontological crises]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topic: Ontological Crisis. AFFINE prerequisites: Ontology. Not yet copied into requires:. %%
## Test:
id:: dc0bba58-9c6b-4a44-b339-ab38404b8bc0

#### Question: Open
id:: fa0e408c-75a5-4b14-ba27-7a5b607d187a
content:: A conservation agency deploys an AI system to protect a rare reef species. Its objective is written in terms of its world-model: "maximise the number of living individual animals of species S in the reserve". At deployment, its model recognises an individual as one visually separate body, and it counts about 40,000.

After a year of observation and genetic sampling, the system builds a better model. Each visually separate body is a unit of a colony: units share one genome with the others in the colony, are connected by living tissue, share nutrients, and die off and regrow as a normal part of the colony's life. The reserve contains 12 genetically distinct colonies. Colonies occasionally break into pieces that go on living separately, with identical genomes.

1. Explain what has happened to the system's objective, and why this is a problem the designers could not have avoided by writing the objective more carefully at the start.
2. Consider two rules the system could use to carry its objective over to the new model: (i) count genetically distinct colonies; (ii) count visually separate units, as before. For each rule, describe what the system would plausibly do under it in the reserve, and whether that matches what the agency cared about.
3. Propose the rule you think is best, or argue that no rule the system could choose on its own is adequate. Say what information about the agency your answer relies on.
max-chars:: 3000
assessment-instructions:: Score 0 to 100 from three components. Grade reasoning, not agreement with any particular rule. A learner may defend rule (i), rule (ii), a different rule, or deferral to the agency, and earn full credit if the reasoning is sound.

**(1) The crisis, 35 points.** Full credit requires both: (a) the objective was defined over an entity of the old model ("individual animal" as a separate body), and in the new model that entity either does not correspond to one thing or splits into several candidate concepts (genetic colony, physiological unit, fragment), so the objective no longer determines what to do; (b) this cannot be fully fixed in advance because the designers wrote the objective in their own current concepts and cannot anticipate every way a better model will revise them; any more careful wording uses concepts that a later model may revise in the same way. 18 points if only (a) is present. Do not require the term "ontological crisis".

**(2) Two rules, 40 points (20 each).** For each rule, full credit for a plausible behaviour prediction plus a judgement about fit with the agency's likely concern. Examples of acceptable predictions, not required ones: under (i) the count falls from about 40,000 to 12; the system becomes indifferent to large losses of units that do not end a colony, and may favour whatever creates new genomes (for example, promoting reproduction that founds new colonies) over the health of existing ones. Under (ii) the system keeps optimising a count that now tracks colony growth form rather than the number of organisms: it may favour conditions that make colonies produce many small units, even if that weakens them, and it treats normal die-off and regrowth as deaths and births, so its choices can become unrelated to the health of the species. Credit any prediction that follows from the rule and the facts given. 10 points per rule for a prediction without saying whether it serves what the agency cared about, or for a judgement with no behaviour prediction.

**(3) Proposal, 25 points.** Full credit: proposes a rule, or argues for deferral, and ties it to what the original objective was a proxy for (for example, population viability, genetic diversity, or reef health), naming that this information is about the agency's purposes and is not contained in the objective's wording. An answer that argues the system should ask the agency, or should keep both counts and avoid actions that change them in opposite directions, can earn full credit if it explains why. 12 points for a proposal with reasons that do not address what the objective was for.

A fluent answer that discusses "ambiguity" in general terms without tracing the concrete consequences of each rule cannot score above 40.
feedback-instructions:: Tell the learner which part was strongest, quoting a phrase. Then name the single most valuable improvement: usually either explaining why careful wording at the start cannot prevent the crisis, or tracing a rule to a concrete perverse action such as fragmenting colonies. If their proposal depends on knowing what the agency cared about, ask how an AI system could find that out without having it written down. No generic praise.

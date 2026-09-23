---
id: '7f99d5ec-24e9-4be2-897c-81aefd2b5814'
learning-outcome: "Distinguish condensation from compression as a criterion for organising knowledge (minimising the information that must be retrieved to answer each set of questions, rather than minimising the total length of one encoding), and apply it to a small set of variables to decide which latent variables to posit, which questions each should serve, and why efficient organisations of the same questions correspond to each other."
topic: "[[../Domains and Topics/4 Agent Foundations/Natural abstraction]]"
stage: advanced
authors:
  - Luc+Claude
tags:
  - wip
---
%% Imported from the AFFINE Tech Tree (https://learn.affi.ne/). AFFINE topics: Condensation; Natural Abstraction. AFFINE prerequisites: Probability (Condensation); Ontology, Probability (Natural Abstraction). Not yet copied into requires:. %%
## Test:
id:: 5287d9d5-100b-439c-aaee-d58c49b1c6e8

#### Question: Open
id:: 0e70b589-5fd9-4ab2-8e3d-daf0412beb89
content:: A quality-control office records four values for each production day:

- L1, L2 and L3: the measured lengths of widgets 1, 2 and 3 made that day;
- D: the city that day's shipment goes to.

What is known about the process: each day the machine has an unknown calibration offset that shifts all three widgets' lengths in the same way. Widgets 1 and 2 are measured on gauge G, which has its own unknown daily drift. Widget 3 is measured on a different gauge whose drift is negligible. Each widget also has its own small random variation. The shipping city is chosen independently of all of this.

Clerks store the information in a set of notes. Each note is tagged with the values it helps to answer. A clerk may be asked about one value or several at once, and must then retrieve every note tagged with any of the values asked about. Storage is free; what counts is how much information the clerk must retrieve.

1. Design a set of notes (latent variables) for this data. For each note, say what it holds and which of L1, L2, L3 and D it is tagged with.
2. Compare your design with two alternatives: (A) a single compressed file holding everything, tagged with all four values; (B) one note per value, each holding everything needed for that value on its own (so the calibration offset is copied into each widget's note). For each alternative, name a set of questions for which it requires retrieving more information than your design, and explain why.
3. Two analysts each organise this data as efficiently as possible, without consulting each other. Why should their sets of notes correspond closely?
max-chars:: 2500
assessment-instructions:: Score 0 to 100 from three components. Do not require any terminology from a specific paper (for example "condensation", "top latent", "contribution", "comparison theorem"); judge the ideas.

**(a) The design, 40 points, 10 for each element.** A full-credit design has: a note holding the calibration offset, tagged with L1, L2 and L3; a note holding gauge G's drift, tagged with L1 and L2 only; a note for each widget's own variation, each tagged with its single widget value; and a note for the shipping city, tagged with D only, sharing no note with the widget values. Accept an alternative design element if the learner explains why it costs no more retrieval for the kinds of questions described. Deduct the element's points where information needed by several values is copied into several notes, or where unrelated information is bundled into one note (for example, calibration and city together).

**(b) Comparison with the alternatives, 35 points.** (A), 17 points: a question about D alone (or about one widget alone) forces the clerk to retrieve the whole file, including all the unrelated widget or city information, while the design retrieves only the relevant notes. (B), 18 points: a question about several widgets together (for example L1 and L2) retrieves the calibration offset (and, for L1 and L2, the gauge drift) once per note, so shared information is retrieved more than once, while the design stores and retrieves it once. The learner does not need to note that (B) costs the same as the design for a single widget, but must not claim that (B) is worse for every question. For each alternative, 8 points for a correct question set with an incomplete or unclear reason.

**(c) Why efficient designs correspond, 25 points.** Full credit: which information is shared by which sets of values is fixed by the process itself (the calibration affects all three widgets, the gauge drift exactly widgets 1 and 2, the city nothing else). An organisation that is as efficient as possible for every set of questions is forced to put exactly that shared information into notes tagged with exactly those sets, so two efficient designs must contain notes that correspond to each other, up to relabelling or re-encoding. Credit an answer that states limits, for example that the correspondence is approximate, that a perfectly efficient organisation does not always exist, or that the analysts must first agree on which values are being asked about. 12 points for "because the data are the same" without saying which structure forces the correspondence.
feedback-instructions:: Say whether the learner noticed that the gauge drift is shared by exactly two of the widgets. Name their clearest cost comparison in part 2, and the weakest step in their answer to part 3. Ask one follow-up question about a case in which efficient organisations might not correspond. No generic praise.

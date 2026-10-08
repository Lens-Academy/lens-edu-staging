---
id: '5b3c0b0d-1191-4e10-9893-89965f849e66'
learning-outcome: Produce at least two distinct, technically-grounded trajectories for AI capability over the next decade, each with a named driving mechanism and a stated observation that would count against it.
topic: "[[../Domains and Topics/11 Strategy/Timelines and forecasting]]"
stage: beginner
authors:
  - Lauren+Claude
eval-results:
  content-sha: 5ac33498
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: pass, C2: pass, C3: pass}
---

%%
Rubric levels, for authors. The platform grade is a single pass/fail; level 3 is
the pass bar. Levels 4 and 5 describe stronger performances and are here to guide
qualitative feedback, not to create a second gate.

1: One story, or pure vibes. Capability arrives "because progress"; no mechanism
   anywhere. Example: "AI keeps getting smarter and by 2030 it can do most jobs."
2: Two trajectories in name, interchangeable in substance; mechanisms decorative
   ("scaling" said but not used); no falsifiers.
3 (pass): Two genuinely distinct trajectories; each names its driver (compute
   scaling, algorithmic progress, data constraints, deployment feedback, ...) and
   one observation that would count against it. Example: "A: compute-led,
   capabilities track training compute, so a 2027 slowdown in cluster buildout
   shows up as a capability plateau by 2028. B: algorithms-led, efficiency gains
   dominate, so capabilities keep jumping even if compute flattens; against this:
   if the next two years of gains all come from bigger runs, B is losing."
4: Falsifiers are near-term and specific enough to actually check within a year or
   two; student names an assumption the two trajectories share.
5: Trajectories interact. The student names where a bottleneck shifts (for example
   compute-led until data runs short, then algorithms decide the slope) and states
   which of their own beliefs is least grounded and what would firm it up.
%%

## Test:
id:: d48b4eba-b7e8-470f-a488-10780199257d

#### Question: Open
id:: 25c2f157-df5f-4489-8af5-3d0d24415976
content::
\## Two trajectories, away from AI

Away from AI entirely. Over the next ten years, the cost of solar electricity plus overnight storage will follow some path. Produce two genuinely different trajectories for it.

For each: name the mechanism doing the work (learning-curve effects from cumulative production, a materials bottleneck, interest rates, grid-integration limits, or a driver of your own choosing), and state one observation checkable within two years that would count against that trajectory.

Then name one assumption your two trajectories quietly share.

assessment-instructions:: Score out of 100: the sum of the three elements below.

The question asks for two genuinely different trajectories for the cost of solar electricity plus overnight storage over the next ten years. For each: the mechanism doing the work (learning-curve effects from cumulative production, a materials bottleneck, interest rates, grid-integration limits, or a driver of the learner's own choosing), and one observation checkable within two years that would count against it. Then one assumption both trajectories quietly share.

40: Two trajectories driven by different named mechanisms. Each names what drives it, and the two drivers differ, not only the slope or speed. One story told twice at different speeds earns at most 10 here.
40: For each trajectory, an observation checkable within about two years that would count against it (20 each). It must be concrete enough to see, such as "battery pack prices stay flat for two years while installations double" or "lithium prices fall through 2027". A falsifier that only negates the trajectory, such as "if costs don't fall", earns nothing for that trajectory.
20: One assumption both trajectories share that is specific to these two stories, for example that demand keeps growing, that policy support stays in place, or that no new storage technology arrives. One plain phrase is enough. A vacuous one such as "the future is uncertain" earns nothing. A supported argument that the two trajectories share no assumption worth naming also earns these 20.

The figures an answer uses for current solar or battery costs are part of its reasoning, not of the score: invented but coherent economics is fine.

Model answer, for the feedback, not a grading checklist: "Trajectory 1, learning curve: every doubling of installed panels and batteries cuts costs by about a fifth, so solar plus storage roughly halves in cost by the mid-2030s. Against it: battery pack prices stay flat for two years while deployment keeps doubling. Trajectory 2, materials bottleneck: demand for lithium and other battery inputs outruns new mines, so storage costs stall or rise and the combined cost flattens. Against it: lithium prices keep falling over the next two years while demand grows. Shared assumption: both assume demand keeps growing fast, which needs policy and finance to stay supportive."
force-feedback:: first
feedback-instructions:: The learner has worked through this module on forecasting AI: what compute buys, measured trends, base rates for jumps, and where a curve stops licensing a forecast. This test is deliberately set outside AI, on the cost of solar electricity plus storage, to see whether the trajectory-mechanism-falsifier structure transfers. They cannot answer it by recalling what they read.

Respond to the answer the learner actually wrote. The rubric beside this scores structure, not solar facts. Do not correct their cost figures unless a figure breaks the logic of their own trajectory.

Open with the strongest part of their answer and why it works, in one sentence. Then name, in plain words, the single most important thing the answer missed or got wrong, and what would have fixed it. Do not cite point values or rubric element numbers. At full marks, confirm briefly and offer the next step below. Common gaps, so the feedback can be specific:
- One story told twice at different speeds: ask what would have to be true in the world for each one, and whether those are different things.
- Falsifiers that cannot fail in practice, for example "if costs don't fall": ask what they would actually see in the next two years, and where.
- No shared assumption, or a vacuous one such as "the future is uncertain": give one example drawn from their own two stories and ask whether they see another.

A strong learner may argue that their two trajectories share no assumption worth naming. If they support that, accept it and say why you accepted it.

If the answer is complete, the next step up: do the two trajectories interact, for example a learning curve that runs until a materials bottleneck takes over, and which of their own beliefs here is least grounded and what would firm it up?

If the student says they do not understand, do not dismiss it and do not repeat the question. Give one concrete foothold: give them one mechanism from the question (for example learning-curve effects: costs fall a fixed share each time cumulative production doubles) and ask what that predicts for the next ten years and what they would see within two years if it were wrong. If their next message still does not attempt the question, rephrase the whole question in different terms rather than offering another foothold.

One follow-up question, not several. Do not over-validate. No generic praise (great answer, excellent work, well done), and do not recite the rubric back to them.

Response length: 100 to 160 words. Short paragraphs. No lists.

# Suggested Lenses:
## Lens:
source:: [[../Lenses/AIF - Half of What We Teach You Here Is Wrong]]

## Lens:
source:: [[../Lenses/AIF - Fun with +12 OOMs of Compute]]

## Lens:
source:: [[../Lenses/AIF - When Progress Jumps]]

## Lens:
source:: [[../Lenses/AIF - What a Curve Licenses]]

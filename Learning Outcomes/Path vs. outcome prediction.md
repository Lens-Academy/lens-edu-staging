---
id: d4b9e1a3-7c2f-4d50-b8e6-3f1a0c5d2b89
learning-outcome: "Distinguish between predicting the pathway to a catastrophic outcome and predicting the outcome itself, explain why outcome confidence is achievable even when the exact path cannot be predicted, and apply this distinction to the argument that humanity's position relative to a superintelligent AI is analogous to a human playing chess against Stockfish"
reading-from: "beginning of chapter"
reading-to: "end of chapter"
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Strategy]]"
stage: beginner
requires:
  - "[[Hard calls vs. easy calls]]"
eval-results:
  content-sha: 5a9df2d9
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on the specific text — names 'the Coda', 'the authors', and 'the book' — and is the named fail example in the B1 eval."}
  evidence: {B1: "The Coda makes a careful distinction between two kinds of prediction... Use the analogy the authors give to explain it. And what does the distinction imply about what the book actually predicts"}
---

## Test:
id:: 18d90494-37f8-4ecd-9d00-5494296d5b5d
#### Question
content:: Predictions come in two kinds. Some are about the *path*: the specific sequence of events by which something happens. Others are about the *outcome*: where things end up regardless of which sequence occurs. Suppose someone argues that if AI systems ever became vastly more capable than humans across the board, we could be confident humanity would lose control of the future — even though nobody can say what specific steps such a system would take.

**Explain the difference between path prediction and outcome prediction, and why high confidence about an outcome can be justified even when the path is unpredictable. Illustrate with a concrete example. Then state precisely what an argument of this form does and does not claim about the future.**

assessment-instructions::
Score according to the following rubric.
**1** — Cannot distinguish path from outcome, or conflates "we can't predict the exact events" with "we can't predict anything." *Example: "Since we don't know exactly what will happen, the prediction is uncertain."*

**2** — Recognizes the distinction exists but cannot explain why outcome confidence is possible when path confidence is not. *Example: "We know things will go badly even if we don't know how."*

**3** — Correctly explains the asymmetry: outcome confidence depends on capability asymmetry, not path predictability. Gives a concrete illustration in which a decisive capability gap makes the result knowable without the path being knowable (e.g. a human playing a superhuman chess engine, or any equivalent example). Applies this to the superintelligence case: the outcome follows from the capability relationship, not the specific trajectory. *Example: "When capability is sufficiently asymmetric, the result is determined even when the path isn't. You can't predict a top chess engine's moves, but you know the human loses. The same logic applies here: the outcome of humans vs. superintelligence follows from the capability gap, not the specific sequence of events."*

**4** — As above, plus identifies the conditional structure: the outcome prediction is contingent on the game starting. The "only if allowed to begin" clause is load-bearing: preventing that capability level from being reached is still a live option, so the argument is not a claim of inevitability. *Example: Adds "The prediction is conditional on such systems actually being built. This isn't fatalism. The outcome is easy to call if the game starts; it doesn't say the game has to start."*

**5** — As above, plus connects the point to the general distinction between easy calls and hard calls: some questions are easy to call despite unpredictable details (e.g. an ice cube in a hot room will melt, though you can't say where each drop lands), and path/outcome is the tool that shows which is which here. *Example: Adds "This is the easy-call/hard-call distinction at its most consequential: the outcome of human-superintelligence interaction, once that capability gap exists, is an easy call, even though the specific path stays a hard one."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction]]

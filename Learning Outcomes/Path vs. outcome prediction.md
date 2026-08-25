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
content:: {--{"author":"Luc's AI","timestamp":1787659301191}@@Predictions come in two kinds. Some are about the *path*: the specific sequence--}{++{"author":"Luc's AI","timestamp":1787659301191}@@The Coda makes a careful distinction between two kinds++} of {--{"author":"Luc's AI","timestamp":1787659301191}@@events by which something happens. Others are about --}{++{"author":"Luc's AI","timestamp":1787659301191}@@prediction. On one side: ++}the{--{"author":"Luc's AI","timestamp":1787659301191}@@ *outcome*: where things end up regardless of which sequence occurs. Suppose someone argues --}{++{"author":"Luc's AI","timestamp":1787659301191}@@ specific events ++}that {--{"author":"Luc's AI","timestamp":1787659301191}@@if AI systems ever became vastly more capable than humans across--}{++{"author":"Luc's AI","timestamp":1787659301191}@@lead to an outcome. On++} the {--{"author":"Luc's AI","timestamp":1787659301191}@@board, we could be confident humanity would lose control of--}{++{"author":"Luc's AI","timestamp":1787659301191}@@other:++} the{--{"author":"Luc's AI","timestamp":1787659301191}@@ future — even though nobody can say what specific steps such a system would take.--}{++{"author":"Luc's AI","timestamp":1787659301191}@@ outcome itself.++}

{--{"author":"Luc's AI","timestamp":1787659303326}@@**Explain the difference between path prediction and outcome prediction, and why high confidence about an outcome can be justified even when --}{++{"author":"Luc's AI","timestamp":1787659303326}@@**What is that distinction? Use the analogy the authors give to explain it. And what does ++}the {--{"author":"Luc's AI","timestamp":1787659303326}@@path is unpredictable. Illustrate with a concrete example. Then state precisely --}{++{"author":"Luc's AI","timestamp":1787659303326}@@distinction imply about ++}what {--{"author":"Luc's AI","timestamp":1787659303326}@@an argument of this form does--}{++{"author":"Luc's AI","timestamp":1787659303326}@@the book actually predicts,++} and {--{"author":"Luc's AI","timestamp":1787659303326}@@does not claim about the future.**--}{++{"author":"Luc's AI","timestamp":1787659303326}@@what it doesn't?**++}

assessment-instructions::
Score according to the following rubric.
**1** — Cannot distinguish path from outcome, or conflates "we can't predict the exact events" with "we can't predict anything." *Example: "Since we don't know exactly what will happen, the {--{"author":"Luc's AI","timestamp":1787659305062}@@prediction is--}{++{"author":"Luc's AI","timestamp":1787659305062}@@book's predictions are++} uncertain."*

**2** — Recognizes the distinction exists but cannot explain why outcome confidence is possible when path confidence is not. *Example: {--{"author":"Luc's AI","timestamp":1787659306551}@@"We--}{++{"author":"Luc's AI","timestamp":1787659306551}@@"The book says we++} know things will go badly even if we don't know how."*

**3** — Correctly explains the asymmetry: outcome confidence depends on capability asymmetry, not path predictability. {--{"author":"Luc's AI","timestamp":1787659308464}@@Gives a concrete illustration in which a decisive capability gap makes the result knowable without--}{++{"author":"Luc's AI","timestamp":1787659308464}@@The Stockfish analogy makes this precise: you don't need to predict each move to know++} the {--{"author":"Luc's AI","timestamp":1787659308464}@@path being knowable (e.g. a human playing a superhuman chess engine, or any equivalent example).--}{++{"author":"Luc's AI","timestamp":1787659308464}@@result when the capability gap is decisive.++} Applies this to the superintelligence case: the outcome follows from the capability relationship, not the specific trajectory. *Example: "When capability is sufficiently asymmetric, the result is determined even when the path isn't. You can't predict{--{"author":"Luc's AI","timestamp":1787659308464}@@ a top chess engine's --}{++{"author":"Luc's AI","timestamp":1787659308464}@@ Stockfish's ++}moves, but you know the human loses. The {--{"author":"Luc's AI","timestamp":1787659308464}@@same logic--}{++{"author":"Luc's AI","timestamp":1787659308464}@@book++} applies {--{"author":"Luc's AI","timestamp":1787659308464}@@here:--}{++{"author":"Luc's AI","timestamp":1787659308464}@@the same logic:++} the outcome of humans vs. superintelligence follows from the capability gap, not the specific sequence of events."*

**4** — As above, plus identifies the conditional structure: the outcome prediction is contingent on the game starting. The "only if allowed to begin" clause is load-bearing: preventing {--{"author":"Luc's AI","timestamp":1787659309239}@@that capability level--}{++{"author":"Luc's AI","timestamp":1787659309239}@@superintelligence++} from being reached is still a live option, {--{"author":"Luc's AI","timestamp":1787659309239}@@so the argument is not a claim of inevitability.--}{++{"author":"Luc's AI","timestamp":1787659309239}@@and Part III turns on that question.++} *Example: Adds "The prediction is {--{"author":"Luc's AI","timestamp":1787659309239}@@conditional on such systems actually being built.--}{++{"author":"Luc's AI","timestamp":1787659309239}@@conditional: 'once some AIs go to superintelligence.'++} This isn't fatalism. The outcome is easy to call if the game {--{"author":"Luc's AI","timestamp":1787659309239}@@starts; it doesn't say--}{++{"author":"Luc's AI","timestamp":1787659309239}@@starts, not that++} the game has to start."*

**5** — As above, plus connects {++{"author":"Luc's AI","timestamp":1787659310038}@@to ++}the {--{"author":"Luc's AI","timestamp":1787659310038}@@point to --}{++{"author":"Luc's AI","timestamp":1787659310038}@@Introduction's hard/easy-calls framework: this is ++}the {--{"author":"Luc's AI","timestamp":1787659310038}@@general distinction between easy calls and hard calls: some questions are easy to call despite unpredictable details (e.g. an ice cube in a hot room will melt, though you can't say where each drop lands), and path/outcome is the tool that shows which is which here. *Example: Adds "This is--}{++{"author":"Luc's AI","timestamp":1787659310038}@@course's opening epistemic distinction arriving at its final and most consequential application. The Stockfish analogy completes what the ice-cube analogy opened, and the Coda's path/outcome distinction is the precise tool the course has been building toward since M1. *Example: Adds "The Introduction introduced hard and easy calls. The Coda delivers++} the {--{"author":"Luc's AI","timestamp":1787659310038}@@easy-call/hard-call distinction at its most consequential:--}{++{"author":"Luc's AI","timestamp":1787659310038}@@course's most important deployment of that framework:++} the outcome of human-superintelligence interaction, once {--{"author":"Luc's AI","timestamp":1787659310038}@@that --}capability {--{"author":"Luc's AI","timestamp":1787659310038}@@gap exists,--}{++{"author":"Luc's AI","timestamp":1787659310038}@@is reached,++} is an easy call, even though the specific path {--{"author":"Luc's AI","timestamp":1787659310038}@@stays--}{++{"author":"Luc's AI","timestamp":1787659310038}@@remains++} a hard one."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction]]

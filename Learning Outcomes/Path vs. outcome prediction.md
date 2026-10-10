---
id: d4b9e1a3-7c2f-4d50-b8e6-3f1a0c5d2b89
learning-outcome: "Distinguish between predicting the pathway to a catastrophic outcome and predicting the outcome itself, explain why outcome confidence is achievable even when the exact path cannot be predicted, and apply this distinction to the argument that humanity's position relative to a superintelligent AI is analogous to a human playing chess against Stockfish"
reading-from: "beginning of chapter"
reading-to: "end of chapter"
authors:
  - Chris+Claude
tags:
  - learning-outcome
topic: "[[../Domains and Topics/11 Strategy/Predicting outcomes, not paths]]"
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
#### {--{"author":"Andreas's AI","timestamp":1791594248583}@@Question--}{++{"author":"Andreas's AI","timestamp":1791594248583}@@Question: Open++}
id:: 9198439f-ebeb-4c4e-9bcf-239f0857d61e
content:: The Coda makes a careful distinction between two kinds of prediction. On one side: the specific events that lead to an outcome. On the other: the outcome itself.

**What is that distinction? Use the analogy the authors give to explain it. And what does the distinction imply about what the book actually predicts, and what it doesn't?**

assessment-instructions::
Score {--{"author":"Andreas's AI","timestamp":1791594255759}@@according to --}{++{"author":"Andreas's AI","timestamp":1791594255759}@@out of 100. Pick the level that best describes the answer as a whole, then a score inside that level's range: near the top if the answer fully reaches the level, near the bottom if it only just does. Judge what the answer shows the learner understands, not only what it spells out: a correct extension that depends on a point shows that point is understood, even if ++}the {--{"author":"Andreas's AI","timestamp":1791594255759}@@following rubric.
**1** —--}{++{"author":"Andreas's AI","timestamp":1791594255759}@@answer states it briefly. An extension shows nothing about points it does not depend on.

**Level 1 (0-20):**++} Cannot distinguish path from outcome, or conflates "we can't predict the exact events" with "we can't predict anything." *Example: "Since we don't know exactly what will happen, the book's predictions are uncertain."*

{--{"author":"Andreas's AI","timestamp":1791594259719}@@**2** —--}{++{"author":"Andreas's AI","timestamp":1791594259719}@@**Level 2 (21-40):**++} Recognizes the distinction exists but cannot explain why outcome confidence is possible when path confidence is not. *Example: "The book says we know things will go badly even if we don't know how."*

{--{"author":"Andreas's AI","timestamp":1791594269758}@@**3** — Correctly explains--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@**Level 3 (41-65):** Explains why the outcome can be predicted when the path cannot: when one side is far more capable, the result is settled even though++} the {--{"author":"Andreas's AI","timestamp":1791594269758}@@asymmetry: outcome confidence depends on capability asymmetry, not path predictability. The Stockfish--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@steps that lead to it are not. But leaves out or gets wrong at least one of the other two parts: the++} analogy {--{"author":"Andreas's AI","timestamp":1791594269758}@@makes--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@and what it shows, or what++} this {--{"author":"Andreas's AI","timestamp":1791594269758}@@precise:--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@means for what the book predicts and does not. *Example: "If one side is vastly more capable,++} you {--{"author":"Andreas's AI","timestamp":1791594269758}@@don't need to--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@can know how it ends without knowing how it gets there."*

**Level 4 (66-85):** As above, plus the other two parts. The analogy: you cannot++} predict {--{"author":"Andreas's AI","timestamp":1791594269758}@@each move to --}{++{"author":"Andreas's AI","timestamp":1791594269758}@@a top chess engine's moves (Stockfish), but you ++}know {++{"author":"Andreas's AI","timestamp":1791594269758}@@a human playing it will lose. What it means for ++}the {--{"author":"Andreas's AI","timestamp":1791594269758}@@result when--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@book: it predicts++} the {--{"author":"Andreas's AI","timestamp":1791594269758}@@capability gap is decisive. Applies this to--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@outcome of humanity against a superintelligence, not++} the {--{"author":"Andreas's AI","timestamp":1791594269758}@@superintelligence case:--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@path, the particular events or++} the {--{"author":"Andreas's AI","timestamp":1791594269758}@@outcome follows from--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@timing. Saying as well that++} the {--{"author":"Andreas's AI","timestamp":1791594269758}@@capability relationship, --}{++{"author":"Andreas's AI","timestamp":1791594269758}@@prediction is conditional (it holds if a superintelligence is built, and does not say one will be) is part of this, ++}not {++{"author":"Andreas's AI","timestamp":1791594269758}@@a further point. An answer that does all three parts has answered ++}the {--{"author":"Andreas's AI","timestamp":1791594269758}@@specific trajectory.--}{++{"author":"Andreas's AI","timestamp":1791594269758}@@question in full, and without an extension it stays in this range.++} *Example: "When capability is sufficiently asymmetric, the result is determined even when the path isn't. You can't predict Stockfish's moves, but you know the human loses. The book applies the same logic: the outcome of humans vs. superintelligence follows from the capability gap, not the specific sequence of events."*

**4** — As above, plus identifies the conditional structure: the outcome prediction is contingent on the game starting. The "only if allowed to begin" clause is load-bearing: preventing superintelligence from being reached is still a live option, and Part III turns on that question. *Example: Adds "The prediction is conditional: 'once some AIs go to superintelligence.' This isn't fatalism. The outcome is easy to call if the game starts, not that the game has to start."*

**5** — As above, plus connects to the Introduction's hard/easy-calls framework: this is the course's opening epistemic distinction arriving at its final and most consequential application. The Stockfish analogy completes what the ice-cube analogy opened, and the Coda's path/outcome distinction is the precise tool the course has been building toward since M1. *Example: Adds "The Introduction introduced hard and easy calls. The Coda delivers the course's most important deployment of that framework: the outcome of human-superintelligence interaction, once capability is reached, is an easy call, even though the specific path remains a hard one."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Path Prediction vs Outcome Prediction]]

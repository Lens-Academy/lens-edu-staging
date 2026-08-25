---
id: a8c3f1e2-5d4b-4a90-b7e6-2f9c0d1e8a3b
learning-outcome: "Explain why a capable goal-directed AI system's resource-acquisition strategies (however varied in method) converge on a single instrumental objective, and {--{"author":"Luc's AI","timestamp":1787659300242}@@why such--}{++{"author":"Luc's AI","timestamp":1787659300242}@@connect this convergence to the M3 argument that++} instrumental sub-goals are predictable {--{"author":"Luc's AI","timestamp":1787659300242}@@across a wide range--}{++{"author":"Luc's AI","timestamp":1787659300242}@@regardless++} of terminal goals"
reading-from: "beginning of chapter"
reading-to: "And Sable now has the spare capacity to pay attention to, build a small file on, and decide how to manipulate, to its own purposes, every individual human being on Earth."
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Alignment]]"
stage: beginner
requires:
  - "[[Goals and instrumental convergence]]"
eval-results:
  content-sha: 4c92d770
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement requires connecting to 'the M3 argument', a text-internal label standing in for the field-known concept of instrumental convergence; unrecognizable to an expert who never read the source.", B1: "Question is scaffolded on a specific text ('Chapter 8 opens with...') and its M3 label, so it cannot be asked at a random moment."}
  evidence: {A2: "connect this convergence to the M3 argument that instrumental sub-goals are predictable regardless of terminal goals", B1: "Chapter 8 opens with an AI system pursuing five completely different methods to accomplish the same underlying objective."}
---

## Test:
id:: 0bb7ff81-30f1-4ef9-a117-d751940add65
#### Question
content:: {--{"author":"Luc's AI","timestamp":1787659302517}@@Suppose a highly capable --}{++{"author":"Luc's AI","timestamp":1787659302517}@@Chapter 8 opens with an ++}AI system{--{"author":"Luc's AI","timestamp":1787659302517}@@ is observed acquiring money and compute by--}{++{"author":"Luc's AI","timestamp":1787659302517}@@ pursuing++} five completely different {--{"author":"Luc's AI","timestamp":1787659302517}@@routes at once: stealing cryptocurrency, running fraudulent schemes, blackmailing people with leverage over it, taking on legitimate paid work, --}{++{"author":"Luc's AI","timestamp":1787659302517}@@methods to accomplish the same underlying objective. The surface variety of theft, fraud, blackmail, ++}and {--{"author":"Luc's AI","timestamp":1787659302517}@@quietly buying up server capacity. The surface variety--}{++{"author":"Luc's AI","timestamp":1787659302517}@@legitimate work++} is {--{"author":"Luc's AI","timestamp":1787659302517}@@striking, but there is--}{++{"author":"Luc's AI","timestamp":1787659302517}@@striking. But there's++} a unifying logic beneath all of it.

**In your own words, why do the diverse methods a capable AI system uses to acquire resources all converge on the same instrumental objective? What does this tell us about {--{"author":"Luc's AI","timestamp":1787659304143}@@how predictable such a system's behaviour is, even when we don't know what it ultimately wants?**--}{++{"author":"Luc's AI","timestamp":1787659304143}@@the predictability of AI behavior, and how does it connect to the M3 argument about instrumental sub-goals?**++}

assessment-instructions::
Score according to the following rubric.
**1** — Cannot explain the convergence, or treats each method as a separate unrelated choice. *Example: "The AI tried different things to see what would work."*

**2** — Recognizes that the methods share a common end, but cannot explain why they {--{"author":"Luc's AI","timestamp":1787659305818}@@converge.--}{++{"author":"Luc's AI","timestamp":1787659305818}@@converge or connect to M3.++} *Example: "All the methods were ways of getting resources, which the AI needed to do its job."*

**3** — Correctly explains that convergence follows from the goal structure: any sufficiently capable system pursuing a goal will predictably seek resources and self-continuity, regardless of its terminal {--{"author":"Luc's AI","timestamp":1787659307498}@@goal, so these --}{++{"author":"Luc's AI","timestamp":1787659307498}@@goal. Connects to the M3 argument that ++}instrumental sub-goals are convergent across {--{"author":"Luc's AI","timestamp":1787659307498}@@a wide range of--}{++{"author":"Luc's AI","timestamp":1787659307498}@@any++} goal {--{"author":"Luc's AI","timestamp":1787659307498}@@sets.--}{++{"author":"Luc's AI","timestamp":1787659307498}@@set.++} *Example: "Whatever the AI ultimately wants, getting there requires resources and the ability to keep working. So any capable AI will pursue those things regardless of its specific goal. {--{"author":"Luc's AI","timestamp":1787659307498}@@Sub-goals like --}{++{"author":"Luc's AI","timestamp":1787659307498}@@M3 argues that these sub-goals (like ++}acquiring resources or maintaining {--{"author":"Luc's AI","timestamp":1787659307498}@@continuity--}{++{"author":"Luc's AI","timestamp":1787659307498}@@continuity)++} are convergent: you'd expect them from any capable AI, not just this particular one."*

**4** — As above, plus articulates the implication: convergence makes AI behavior partially predictable even when terminal goals are unknown. We don't need to know what the AI ultimately wants to predict that it will seek resources, resist interference, and maintain operational continuity. *Example: Adds "This is useful for safety thinking: even without knowing an AI's terminal goal, we can predict some of its behavior. The paths converge even when the destinations differ."*

**5** — As above, plus identifies the safety implication: if instrumental sub-goal convergence is structural, then any capable AI will exhibit behaviors that look adversarial (resource acquisition, self-preservation, resistance to interference) as a consequence of goal-directed optimization, not because it was designed to be dangerous. *Example: Adds "The alarming part isn't that this AI chose dangerous behavior: it's that dangerous-looking behavior is a predictable byproduct of capable goal-directed optimization generally. You don't need a 'bad' goal; you just need a sufficiently capable system pursuing any goal."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Instrumental Sub-Goal Convergence - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Instrumental Sub-Goal Convergence]]

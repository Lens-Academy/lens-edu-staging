---
id: e7a6096d-ef44-4f48-b2d1-53307f8d99ee
learning-outcome: {--{"author":"Luc's AI","timestamp":1787659318202}@@"Explain--}{++{"author":"Luc's AI","timestamp":1787659318202}@@"Apply the ladder-in-the-dark framing to explain++} why uncertainty about{--{"author":"Luc's AI","timestamp":1787659318202}@@ where a catastrophic threshold lies fails to--}{++{"author":"Luc's AI","timestamp":1787659318202}@@ the fatal rung does not++} protect against {--{"author":"Luc's AI","timestamp":1787659318202}@@disaster when competing actors each face incentives to keep advancing: show--}{++{"author":"Luc's AI","timestamp":1787659318202}@@predictable disaster: trace the chapter's argument++} that if {--{"author":"Luc's AI","timestamp":1787659318202}@@advancing--}{++{"author":"Luc's AI","timestamp":1787659318202}@@climbing++} cannot be stopped while{--{"author":"Luc's AI","timestamp":1787659318202}@@ the--} uncertainty remains, {--{"author":"Luc's AI","timestamp":1787659318202}@@catastrophe--}{++{"author":"Luc's AI","timestamp":1787659318202}@@death++} is a predictable collective {--{"author":"Luc's AI","timestamp":1787659318202}@@outcome--}{++{"author":"Luc's AI","timestamp":1787659318202}@@outcome,++} even though no specific {--{"author":"Luc's AI","timestamp":1787659318202}@@step--}{++{"author":"Luc's AI","timestamp":1787659318202}@@rung++} can be identified as {--{"author":"Luc's AI","timestamp":1787659318202}@@the --}lethal{--{"author":"Luc's AI","timestamp":1787659318202}@@ one--} in advance."
reading-from: "An AI company executive who says there's only a one-in-five chance that the AI they're building will kill literally everyone (as they do) is not in quite as much denial as the Soviet managers who denied the Chernobyl meltdown after it happened."
reading-to: "end of chapter"
authors:
  - Chris+Claude
domain: "[[../Domains/Strategy]]"
stage: beginner
eval-results:
  content-sha: 0416884d
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: fail, C3: fail}
  notes: {A2: "Statement is bound to a specific text: it asks the learner to reconstruct what the chapter argues, matching the 'State Chapter 11's central diagnosis as the chapter frames it' fail pattern.", B1: "Question is scaffolded on the assigned text — it names Chapter 12 and asks the learner to trace that chapter's argument, so a capable non-reader cannot answer as posed.", C2: "Pass level 3 hard-requires naming the chapter's three specific actor categories, which the question never asks for or implies.", C3: "Level 3 requires a memorized taxonomy verbatim ('the three types of actors...') rather than stating the idea in any wording; level 5 likewise hard-requires the specific CERN example with no 'or equivalent' allowance."}
  evidence: {A2: "trace the chapter's argument that if climbing cannot be stopped while uncertainty remains", B1: "Chapter 12 closes with a striking image: every competing AI company is climbing a ladder in the dark.", C2: "the three types of actors (researchers/companies, corporate executives, world leaders) each have incentives to keep climbing", C3: "connects to the CERN comparison the chapter uses to close"}
---

## Test:
id:: 38dc6bd8-b793-448e-a44a-89d3cd4c6a03
#### Question
content:: {--{"author":"Luc's AI","timestamp":1787659320466}@@Picture several--}{++{"author":"Luc's AI","timestamp":1787659320466}@@Chapter 12 closes with a striking image: every++} competing AI {--{"author":"Luc's AI","timestamp":1787659320466}@@companies--}{++{"author":"Luc's AI","timestamp":1787659320466}@@company is++} climbing a ladder in the dark.{--{"author":"Luc's AI","timestamp":1787659320466}@@ Each rung is a more capable AI system. Somewhere above them is a--}{++{"author":"Luc's AI","timestamp":1787659320466}@@ Nobody knows which rung will be the++} last safe {--{"author":"Luc's AI","timestamp":1787659320466}@@rung:--}{++{"author":"Luc's AI","timestamp":1787659320466}@@one:++} the point at which {--{"author":"Luc's AI","timestamp":1787659320466}@@a--}{++{"author":"Luc's AI","timestamp":1787659320466}@@an AI++} system crosses into {--{"author":"Luc's AI","timestamp":1787659320466}@@territory nobody can recover from. Nobody knows which rung that is, and standing on one rung tells you nothing about whether the next is the fatal one. --}{++{"author":"Luc's AI","timestamp":1787659320466}@@unrecoverable territory. ++}You might expect this uncertainty to provide protection: if no one knows where the lethal rung is, perhaps caution will prevail.{++{"author":"Luc's AI","timestamp":1787659320466}@@ Chapter 12 argues the opposite. ++}

**Explain why uncertainty about which rung is fatal does not protect against disaster. Say why the actors involved keep climbing anyway, and why that makes the collective outcome predictable even though no individual rung can be identified as lethal in advance.**

assessment-instructions::
Score according to the following rubric.

**1**: Cannot explain the ladder-in-the-dark framing, or mistakes uncertainty for a reason for optimism. *Example: "If nobody knows which rung is dangerous, they will probably stop before they hit it."*

**2**: Understands that the ladder involves competitive pressure, but cannot explain why uncertainty about the fatal rung fails to prevent disaster. *Example: "There's a race to build AI and nobody knows when it becomes dangerous. The uncertainty is scary."*

**3**: Conveys the structural argument, in any wording: the actors who decide whether to climb face incentives to keep climbing that do not depend on what they believe about the fatal rung, because stopping unilaterally means ceding the race to someone else who will keep climbing. Because the climbing therefore continues while the uncertainty remains, the collective outcome is predictable even though no individual rung is identified as lethal. Naming particular actor categories (e.g. researchers and companies, corporate executives, national leaders) is one acceptable route, not a requirement; a general account of the competitive incentive also passes. Fail if the answer treats the problem as informational (better forecasting would fix it) or as caused by individual recklessness rather than by the structure of the race. *Example: "Uncertainty doesn't help because the problem isn't informational: it's structural. An executive who believes there's a 20% chance of killing everyone keeps building because stopping hands the race to a competitor who might be less careful, and governments fund development out of fear of being left behind. So the system keeps climbing rung by rung regardless of anyone's beliefs about risk. If climbing can't be stopped while the uncertainty remains, we predictably reach the fatal rung."*

**4**: As above, plus explains the individual-rationality/collective-tragedy structure: each actor's decision to continue is locally rational given the competitive context, but the aggregate of locally rational decisions produces a catastrophic collective outcome, making this a structural problem that no individual can solve. *Example: Adds "The key insight is that each actor has individually rational reasons to keep going: unilateral stopping is unilateral disarmament. This isn't irrationality or malice: it's a situation where individually sensible choices aggregate into collective death. No single actor can fix it alone, which is why any real fix has to be a binding agreement across all of them."*

**5**: As above, plus names the counterfactual: what proceeding responsibly under existential uncertainty would have to look like (pause and verify that the next step cannot cause the catastrophe before taking it), and observes that the competitive structure described provides no such mechanism. Any concrete precedent illustrating pause-and-verify counts — e.g. CERN spending roughly a decade calculating whether the LHC could destroy the Earth before switching it on, or an equivalent example; no specific case is required, and a purely abstract statement of the counterfactual also passes. *Example: Adds "Compare a field that did this properly: physicists delayed the LHC for years while they verified it couldn't destroy the world. That's the model for proceeding under existential uncertainty: pause and calculate until you can show it's safe. AI development has no equivalent process: no coordinated threshold, no verification requirement, no pause mechanism. The ladder keeps getting climbed because the competitive structure provides nothing to stop it."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Ladder in the Dark - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Ladder in the Dark]]

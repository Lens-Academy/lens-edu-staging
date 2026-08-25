---
id: 3e29b948-02b0-4fd3-847a-4c7adb05dd0d
learning-outcome: {--{"author":"Luc's AI","timestamp":1787659258898}@@"Explain the 'alchemy stage'--}{++{"author":"Luc's AI","timestamp":1787659258898}@@"State Chapter 11's central++} diagnosis {--{"author":"Luc's AI","timestamp":1787659258898}@@of--}{++{"author":"Luc's AI","timestamp":1787659258898}@@as++} the {--{"author":"Luc's AI","timestamp":1787659258898}@@AI--}{++{"author":"Luc's AI","timestamp":1787659258898}@@chapter frames it: the++} alignment {--{"author":"Luc's AI","timestamp":1787659258898}@@field: that it produces--}{++{"author":"Luc's AI","timestamp":1787659258898}@@field is currently in the 'alchemy stage': producing++} results without understanding why they work, {--{"author":"Luc's AI","timestamp":1787659258898}@@operates--}{++{"author":"Luc's AI","timestamp":1787659258898}@@operating++} from high-minded philosophical ideals rather than engineering designs, and {--{"author":"Luc's AI","timestamp":1787659258898}@@mistakes--}{++{"author":"Luc's AI","timestamp":1787659258898}@@mistaking++} the ability to build more powerful AI for progress on making it {--{"author":"Luc's AI","timestamp":1787659258898}@@safe — and explain why that missing understanding matters."--}{++{"author":"Luc's AI","timestamp":1787659258898}@@safe."++}
reading-from: "beginning of chapter"
reading-to: "It is a level of systemic game that would have humanity headed for disaster, even if we were wrong about every other aspect of difficulty."
authors:
  - Yatharth+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Alignment]]"
stage: beginner
eval-results:
  content-sha: fc29cbf0
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: fail, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {A2: "Statement is bound to a specific text's framing rather than a source-free capability; named as a corpus fail example in the A2 eval.", B1: "Question is scaffolded on the assigned chapter — it names Chapter 11 and its opening allegory, so it cannot be posed to someone who never read that text."}
  evidence: {A2: "State Chapter 11's central diagnosis as the chapter frames it", B1: "Chapter 11 opens with an allegory about a young alchemist"}
---

## Test: 
id:: 311a34f9-b4d2-46b8-813a-3b51869fe6c3
#### {--{"author":"Elias's AI","timestamp":1787667479540}@@Question--}{++{"author":"Elias's AI","timestamp":1787667479540}@@Question: Open
id:: 27a3b083-bbc8-4466-a4f2-9af646bfc0f7++}
content:: {--{"author":"Luc's AI","timestamp":1787659260701}@@Picture--}{++{"author":"Luc's AI","timestamp":1787659260701}@@Chapter 11 opens with an allegory about++} a young alchemist who claims {--{"author":"Luc's AI","timestamp":1787659260701}@@he is--}{++{"author":"Luc's AI","timestamp":1787659260701}@@to be++} "close" to transmuting lead into{--{"author":"Luc's AI","timestamp":1787659260701}@@ gold. He is not a fraud: his recipes really do produce results — he can make aqua regia, an acid that dissolves --}{++{"author":"Luc's AI","timestamp":1787659260701}@@ ++}gold{--{"author":"Luc's AI","timestamp":1787659260701}@@ — but he has--}{++{"author":"Luc's AI","timestamp":1787659260701}@@ despite having++} no {--{"author":"Luc's AI","timestamp":1787659260701}@@theory--}{++{"author":"Luc's AI","timestamp":1787659260701}@@understanding++} of {--{"author":"Luc's AI","timestamp":1787659260701}@@*why* any of it works, so he cannot tell which of his results generalize or what his next step should be. One diagnosis of the AI alignment field is that it is currently in--}{++{"author":"Luc's AI","timestamp":1787659260701}@@why his recipes produce the results they do. The chapter then applies this framing to current AI alignment efforts, drawing on public statements from Elon Musk (xAI) and Yann LeCun (Meta). The authors call++} this {--{"author":"Luc's AI","timestamp":1787659260701}@@same--}{++{"author":"Luc's AI","timestamp":1787659260701}@@the++} "alchemy stage" of a {--{"author":"Luc's AI","timestamp":1787659260701}@@science, and that safety proposals from leading AI developers — e.g. building AI that is "maximally truth-seeking" (Elon Musk, xAI), or that is "submissive to humans" (Yann LeCun, Meta) — illustrate the pattern rather than escape it.--}{++{"author":"Luc's AI","timestamp":1787659260701}@@science.++}

**In your own words, what is {--{"author":"Luc's AI","timestamp":1787659262266}@@the--}{++{"author":"Luc's AI","timestamp":1787659262266}@@Chapter 11's++} "alchemy stage" diagnosis of the AI alignment field? What specifically does {--{"author":"Luc's AI","timestamp":1787659262266}@@this diagnosis--}{++{"author":"Luc's AI","timestamp":1787659262266}@@the chapter++} claim is missing from the field's current state, and why does it matter that it is missing?**

assessment-instructions::
Score according to the following rubric.

**1**: Reads the diagnosis as "alignment is hard" or "the field isn't trying enough," missing the specific claim about *kind* of progress. *Example: "They're saying alignment isn't working yet."*

**2**: Identifies that the field is at an "early" stage but cannot articulate what specifically distinguishes alchemy-stage from engineering-stage thinking. *Example: "The alignment field is still figuring it out, like alchemists were."*

**3**: Correctly states the diagnosis: the field produces techniques that sometimes work but nobody understands *why* they work; practitioners reason from high-minded philosophical ideals rather than rigorous engineering designs; the ability to build more powerful AI is being mistaken for progress on making it safe. *Example: "The alchemy-stage claim is that AI safety researchers can produce results (RLHF makes a model behave better, scaling produces capability gains) but they don't understand the underlying principles. Like alchemists who could make Aqua Regia without knowing chemistry, they're operating on recipes, not theory. And when they try to extrapolate to alignment, they reach for philosophical ideals like 'truth-seeking AI' or 'submissive AI' rather than engineering specifications."*

**4**: As above, plus articulates *why this is worse than just being wrong*: folk-theory-stage thinking is generated by the same ignorance that makes the thinkers confident, so it resists ordinary correction by evidence. *Example: Adds "What makes this dangerous is that the same gap that produces the wrong answer also produces the confidence that the answer is right. An engineer working from solid principles can be told they got the calculation wrong; an alchemist working from a vibe-based scheme has no calculation to correct. Musk and LeCun aren't slightly off. They're operating from a level of theory that doesn't engage the engineering question at all."*

**5**: As above, plus holds the diagnosis with the *correct valence*: it is a field-level epistemic claim, not despair, not individual blame, and not a claim that progress is impossible in principle. The field isn't permanently stuck: it's in a stage that has to be exited before adequate engineering becomes possible, and that exit hasn't happened. *Example: Adds "And the diagnosis is meant as a diagnosis, not a verdict. It's not saying alignment researchers are bad people, or that the field will be like this forever, or that progress is impossible. It's saying that *right now* the field is producing the kind of confident-sounding claims that fields produce *before* they have the conceptual machinery to actually engage the problem. And distinguishing this stage from a mature engineering stage is what allows you to ask the right policy questions about what to do while we're still here."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Alchemy Not Science - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Alchemy Not Science]]

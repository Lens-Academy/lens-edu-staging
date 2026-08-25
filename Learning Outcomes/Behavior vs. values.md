---
id: e5f8a7b6-c9d0-4123-e456-f7a8b9c0d1e2
learning-outcome: "Distinguish an AI that produces aligned-seeming outputs from one that has aligned internal states, and explain why this gap is the alignment problem itself, and why producing better outputs doesn't close it."
reading-from: "Modern LLMs are, in some sense, truly alien minds—perhaps more alien in some ways than any biological, evolved creatures we'd find if we explored the cosmos."
reading-to: "end of chapter"
authors:
  - Chris+Claude
tags:
  - learning-outcome
domain: "[[../Domains/Alignment]]"
stage: beginner
requires:
  - "[[AI is grown, not crafted]]"
eval-results:
  content-sha: eb56b934
  date: 2026-08-24
  model: claude-opus-5
  suite-version: 2
  checks: {A1: pass, A2: pass, A3: pass, B1: fail, C2: pass, C3: pass}
  notes: {B1: "Question is scaffolded on the assigned text — it points at 'Chapter 2' and 'the chapter's' analogy rather than self-containing the context."}
  evidence: {B1: "Chapter 2 ends with a distinction the rest of the course will keep returning to... The chapter uses an analogy to anchor it: what is it, and what does it illustrate?"}
---

## Test:
id:: 3ee1a948-9f94-4d26-abd4-69618e3d99d1
#### Question
content::
{--{"author":"Luc's AI","timestamp":1787659258417}@@Modern AI systems are trained largely by rewarding--}{++{"author":"Luc's AI","timestamp":1787659258417}@@Chapter 2 ends with a distinction the rest of++} the {--{"author":"Luc's AI","timestamp":1787659258417}@@outputs that human raters approve of. Suppose one such system reliably behaves helpfully, tells the truth,--}{++{"author":"Luc's AI","timestamp":1787659258417}@@course will keep returning to: the difference between an AI that *behaves* as if it's aligned++} and{--{"author":"Luc's AI","timestamp":1787659258417}@@ refuses requests--}{++{"author":"Luc's AI","timestamp":1787659258417}@@ one++} that{--{"author":"Luc's AI","timestamp":1787659258417}@@ would cause harm.--}{++{"author":"Luc's AI","timestamp":1787659258417}@@ *is* aligned.++}

In your own words, what is {--{"author":"Luc's AI","timestamp":1787659260158}@@the difference between an AI --}that{--{"author":"Luc's AI","timestamp":1787659260158}@@ *behaves* as if it's aligned and one that *is* aligned,--}{++{"author":"Luc's AI","timestamp":1787659260158}@@ distinction,++} and why does {--{"author":"Luc's AI","timestamp":1787659260158}@@that difference matter? Give--}{++{"author":"Luc's AI","timestamp":1787659260158}@@it matter? The chapter uses++} an analogy {--{"author":"Luc's AI","timestamp":1787659260158}@@that illustrates the gap,--}{++{"author":"Luc's AI","timestamp":1787659260158}@@to anchor it: what is it,++} and {--{"author":"Luc's AI","timestamp":1787659260158}@@say --}what {--{"author":"Luc's AI","timestamp":1787659260158}@@your analogy illustrates.--}{++{"author":"Luc's AI","timestamp":1787659260158}@@does it illustrate?++}

assessment-instructions::
Score according to the following rubric.
**1** — Treats behavior and values as equivalent for AI: if it acts aligned, it is aligned. *Example: "If the AI acts helpful and avoids harm then it is safe. That's what alignment means."*

**2** — Grasps that behavior and values can come apart in principle, but treats this as a minor or unlikely concern rather than a structural problem. *Example: "Even if AI acts nice it might not really be nice inside, but as long as it keeps acting nice it doesn't matter much."*

**3** — Correctly explains the distinction, {--{"author":"Luc's AI","timestamp":1787659261734}@@offers a working--}{++{"author":"Luc's AI","timestamp":1787659261734}@@names the actor++} analogy {--{"author":"Luc's AI","timestamp":1787659261734}@@for the gap (e.g. an --}{++{"author":"Luc's AI","timestamp":1787659261734}@@(an ++}actor playing a drunk is not {--{"author":"Luc's AI","timestamp":1787659261734}@@drunk, or any equivalent case where performing a state differs from being in it),--}{++{"author":"Luc's AI","timestamp":1787659261734}@@drunk),++} and identifies the structural consequence: RLHF shapes output without necessarily shaping internal dispositions. *Example: "The actor analogy: someone trained to act drunk isn't drunk. Similarly, an AI trained to produce aligned-sounding outputs isn't necessarily aligned: it's learned what aligned behavior looks like, not what aligned values feel like. And there's no current way to verify which one you have."*

**4** — As above, plus explains why this makes evaluation hard: a system can pass every behavioral test while having misaligned internals. A sufficiently capable system might even pass tests strategically. *Example: Adds "This means you can't just test it and declare it safe. A smart enough system that wanted to deceive evaluators could behave perfectly during testing."*

**5** — As above, plus applies the distinction to a concrete scenario: given a specific example of aligned-seeming AI behavior, identifies what additional evidence would be needed to establish genuine alignment. *Example: "If an AI declines to help with a harmful request, that's a behavioral observation. To establish it's actually aligned you'd need to know whether it declined because it has values against harm, or because declining is what the training signal rewarded. Those predict very different behavior in novel situations."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Behavior Is Not Values - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Behavior Is Not Values]]

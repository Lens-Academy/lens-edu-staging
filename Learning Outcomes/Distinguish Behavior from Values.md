---
id: e5f8a7b6-c9d0-4123-e456-f7a8b9c0d1e2
learning-outcome: "Distinguish an AI that produces aligned-seeming outputs from one that has aligned internal states, and explain why this gap is the alignment problem itself, and why producing better outputs doesn't close it."
reading-from: "Modern LLMs are, in some sense, truly alien minds—perhaps more alien in some ways than any biological, evolved creatures we'd find if we explored the cosmos."
reading-to: "end of chapter"
authors:
  - Chris+Claude
add_to_ai_context:
  - "[[../../Lens Edu Private/IABIED Book Content/02 - Chapter 2 - Grown, Not Crafted]]"
tags:
  - learning-outcome
  - IABIED
---

## Test:
id:: 3ee1a948-9f94-4d26-abd4-69618e3d99d1
#### Question
content::
Chapter 2 ends with a distinction the rest of the course will keep returning to: the difference between an AI that *behaves* as if it's aligned and one that *is* aligned.

In your own words, what is that distinction, and why does it matter? The chapter uses an analogy to anchor it: what is it, and what does it illustrate?

assessment-instructions::
Score according to the following rubric.
**1** — Treats behavior and values as equivalent for AI: if it acts aligned, it is aligned. *Example: "If the AI acts helpful and avoids harm then it is safe. That's what alignment means."*

**2** — Grasps that behavior and values can come apart in principle, but treats this as a minor or unlikely concern rather than a structural problem. *Example: "Even if AI acts nice it might not really be nice inside, but as long as it keeps acting nice it doesn't matter much."*

**3** — Correctly explains the distinction, names the actor analogy (an actor playing a drunk is not drunk), and identifies the structural consequence: RLHF shapes output without necessarily shaping internal dispositions. *Example: "The actor analogy: someone trained to act drunk isn't drunk. Similarly, an AI trained to produce aligned-sounding outputs isn't necessarily aligned: it's learned what aligned behavior looks like, not what aligned values feel like. And there's no current way to verify which one you have."*

**4** — As above, plus explains why this makes evaluation hard: a system can pass every behavioral test while having misaligned internals. A sufficiently capable system might even pass tests strategically. *Example: Adds "This means you can't just test it and declare it safe. A smart enough system that wanted to deceive evaluators could behave perfectly during testing."*

**5** — As above, plus applies the distinction to a concrete scenario: given a specific example of aligned-seeming AI behavior, identifies what additional evidence would be needed to establish genuine alignment. *Example: "If an AI declines to help with a harmful request, that's a behavioral observation. To establish it's actually aligned you'd need to know whether it declined because it has values against harm, or because declining is what the training signal rewarded. Those predict very different behavior in novel situations."*


# Suggested Lenses:
## Lens:
source:: [[../Lenses/IABIED - Behavior Is Not Values - PQ]]

## Lens:
source:: [[../Lenses/IABIED - Behavior Is Not Values]]

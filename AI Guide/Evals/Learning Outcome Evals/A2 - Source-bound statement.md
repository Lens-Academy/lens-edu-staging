---
eval-id: A2
target: statement
tags:
  - validator-ignore
---
# A2 — Source-bound statement

**Binary question:** Would this capability make sense for someone who learned the material somewhere else — or does it depend on knowing what a specific text or author says?

## Pass boundary

The capability must survive outside this course. It **fails** when it amounts to "reconstruct what author X / chapter N says" about a concept that exists independently of that text — the tell is that the statement's content would be unrecognizable or pointless to an expert who never read the assigned source.

## Does NOT fail for

- **Field-canonical named frameworks.** Ask: does this go by this name in the field, such that advanced practitioners would recognize it? (E.g. a landmark scheme widely known under its author's name.)
- **A text-specific frame that is not a stand-in for a broader known concept.** Human ruling on *Hard calls vs. easy calls*: "the authors are choosing a very specific frame … that is useful but not otherwise broadly used. They're not referring to a broader concept that's well known in the community under another name. So that's why I would probably allow this one."
- Naming a coined concept when the capability is about the concept itself, not about the text's presentation of it.

## Fail examples (from the corpus)

- "Explain Scher and Thiergart's claim that increased access can substitute for unavailable technical verification mechanisms…" (*Access substitutes for verification technology*) — human ruling: "LO shouldn't depend on knowing what a specific person said."
- "State Chapter 11's central diagnosis **as the chapter frames it**…" (*Alignment as alchemy*) — human ruling: "depends on a specific text. … The underlying thing it points at is okay though."
- "Identify two broad camps in AI safety **described by Jason Hausenloy**…" (*Two Camps in AI Safety*) — the landscape divide exists independently of Hausenloy's framing.

## Pass examples (from the corpus)

- "Distinguish 'hard calls' from 'easy calls' as the authors define them…" (*Hard calls vs. easy calls*) — passes per the ruling quoted above.
- Borderline illustration: *Compute accounting for training runs* ("Explain Shavit's three-part compute-accounting regime…") — pass iff the regime is genuinely field-canonical under Shavit's name; the human reviewer marked this one "idk". When genuinely uncertain, fail it and let triage decide.

## On failure

A2 failures route to **human triage**: is the underlying capability worth keeping (→ rephrase the statement source-free) or is it a reading's takeaway dressed as an outcome (→ delete or demote to practice material)?

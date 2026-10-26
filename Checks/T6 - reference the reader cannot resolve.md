---
id: T6
enabled: false
name: "reference the reader cannot resolve"
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
question: "Does `paragraph` refer to something that a reader can only work out by remembering or searching text that is not shown with it, without saying what it is?"
criteria:
  "true": "`paragraph` points at something it relies on the reader to find elsewhere, such as \"this\", \"the above\", \"that case\", an earlier list item, or a name used without introduction, and does not restate it."
  "false": "Everything `paragraph` refers to is stated in `paragraph` itself, or is everyday knowledge."
fix: "Say what the reference points at, in a few words, instead of relying on the reader to remember or look it up."
---

Drafted by Sorrel (Claude), 2026-10-26, from a conversation with Lauren: writers with a large working memory (Claudes most of all) write references that resolve easily for them and not for a reader, "an AI who lives in a robot body ... forget[ting] that that awesome extremely-usable design for kitchen scissors needs to not be made of tungsten". Not live yet (`enabled: false`): tune it in the panel first.

Run it with jev seeing each paragraph alone (the default), since "not shown with it" is what the check asks about. Open question for tuning: how strict to be about "the above" and "this", which are often clear from the sentence before.

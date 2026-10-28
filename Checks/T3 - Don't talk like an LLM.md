---
id: T3
enabled: true
name: "Don't talk line an LLM"
model: jev-1.14.0
fail_at: 0.7
pass_below: 0.6
question: "Does `sentence` sound like an LLM wrote it?"
criteria:
  "true": "`sentence` uses words or patterns that are favored by LLMs, including but not limited to \"load bearing\", \"x not y\", strong superlatives, \"keys\", the word \"build\" applied to ideas, references to what to \"say\" or \"name\" or \"acknowledge\" or \"ask\" or other such phrase-level focus, generic \"what do you think\", or other such tics. List is non-exhaustive."
  "false": "`sentence` reads like a human wrote it: uses organically unusual sentence constructions, has human stylographic structure, fits into the surrounding phrasing"
fix: "Rewrite it as a careful human writer would: name the specific thing meant, drop signposting such as \"now that we have\" or \"let us dive into\", and cut words that only add enthusiasm."

view:
  sample: 600
presentation:
  context: section
  question: sentence
  nest:
    - document
    - submodule
    - lens
    - section
    - paragraph
    - sentence
    - line
---

## How to pass (for editing agents)

*Drafted by Sorrel (a Claude), 2026-10-28, for Lauren to rewrite.*

This check asks about each sentence, with its section shown, whether it sounds like an LLM wrote it. It overlaps with "Don't talk like opus5" but looks at single sentences and at words that many models overuse, not one model's voice.

What fixes a flag:

1. Rewrite around the overused words in the criteria: "load-bearing", "key" as an adjective, "build" applied to ideas ("build intuitions"), and contrasts of the form "not X but Y". Swapping in a synonym of the same kind ("key" for "crucial", "core" for "central") does not pass; write what is actually important about the thing instead.
2. In instructions to students, ask for the thing itself instead of naming the speech act. "Say what each one is correcting for" becomes "What is each one correcting for?"; "Name one reason" becomes "Which reason convinced you?".
3. Cut signposting about the course's own structure: "Now that we've established", "we'll dive into", "In this section we will".
4. End a reading with a specific question about its content, never "What do you think?".

A real case: "Now that we've established the foundational motivations for why verification is important, we'll dive into building key intuitions..." passed as "Next we ask what a verification regime would look like: how long it would take to build, what it would cover, and how soon it is needed."

## Notes

Why this check exists, and examples of what it should and should not catch.

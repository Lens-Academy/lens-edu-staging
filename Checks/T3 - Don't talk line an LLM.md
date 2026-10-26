---
id: T3
enabled: false
name: "Don't talk line an LLM"
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
question: "Does `paragraph` …?"
criteria:
  "true": "`paragraph` …"
  "false": "`paragraph` …"
fix: "…"
draft:
  question: Does `sentence` sound like an LLM wrote it?
  criteria:
    "true": "`sentence` uses words or patterns that are favored by LLMs, including but not limited to \"load bearing\", \"x not y\", strong superlatives, \"keys\", the word \"build\" applied to ideas, references to what to \"say\" or \"name\" or \"acknowledge\" or \"ask\" or other such phrase-level focus, generic \"what do you think\", or"
    "false": "`sentence` reads like a human wrote it: uses organically unusual sentence constructions, has 's distinctive stylistic tics, fits into the surrounding phrasing"
  presentation:
    context: document
    question: sentence
    nest:
      - document
      - submodule
      - lens
      - section
      - paragraph
      - sentence
      - line
view:
  sample: 600
---

Why this check exists, and examples of what it should and should not catch.

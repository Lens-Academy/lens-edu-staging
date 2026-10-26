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
  question: Does `paragraph` sound like an LLM wrote it?
  criteria:
    "true": "`paragraph` uses words or patterns that are favored by LLMs, including but not limited to \"load bearing\", \"x not y\", strong superlatives, \"keys\", the word \"build\" applied to sentences, excessive references to what to \"say\" or \"name\""
    "false": "`paragraph` reads like a human wrote it: uses organically unusual sentence constructions, has an author's distinctive stylistic tics, fits well into the surrounding phrasing."
  presentation:
    context: document
    question: paragraph
    nest:
      - document
      - submodule
      - lens
      - section
      - paragraph
      - sentence
      - line
---

Why this check exists, and examples of what it should and should not catch.

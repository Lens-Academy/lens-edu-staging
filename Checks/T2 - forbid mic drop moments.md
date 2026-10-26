---
id: T2
enabled: false
name: "forbid mic drop moments"
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
question: "Does `paragraph` …?"
criteria:
  "true": "`paragraph` …"
  "false": "`paragraph` …"
fix: "…"
draft:
  question: Does `paragraph` contain a mic drop moment, ie, a dramatic phrase that feels like a punchline to a buildup?
  criteria:
    "true": "`paragraph` uses excessive intensity: \"the exact moment\", \"and that was when it happened\", \"and here's where it gets interesting\""
    "false": "`paragraph` is reasonably sedate, or fits comfortably in its context without standing out dramatically"
---

Why this check exists, and examples of what it should and should not catch.

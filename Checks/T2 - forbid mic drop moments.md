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
  criteria:
    "true": "`paragraph"
---

Why this check exists, and examples of what it should and should not catch.

---
id: ZZ9
enabled: false
name: "scratch label test (Sorrel, delete me)"
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
question: "Does `paragraph` …?"
criteria:
  "true": "`paragraph` …"
  "false": "`paragraph` …"
fix: "…"
view:
  sample: 3
---

Why this check exists, and examples of what it should and should not catch.

## Labels

```jsonl
{"check":"ZZ9","path":"Lens Edu/Lenses/AIF2 - Day Zero, Revisited.md","line":70,"quote":"And one line quoting the sentence in your day-zero guess that most surprises you now.","label":"fail","by":"Sorrel (headless test)","at":"2026-10-23T13:11:05.818Z"}
```

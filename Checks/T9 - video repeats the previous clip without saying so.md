---
id: T9
enabled: false
name: video repeats the previous clip without saying so
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
skip_folders: [ Questions ]
question: >-
  `paragraph` starts a video clip whose start time is earlier than the end time of the clip before it (so its first seconds replay the end of that clip). Does the text right before this clip tell the learner that the repeat is on purpose?
criteria:
  "true": >-
    The text between the two clips (the heading, the intro line) does not mention that the start of this clip repeats the end of the last one. A learner who sees the same words twice will think the wrong video was played, or that the course made a mistake.
  "false": >-
    The text before the clip says the overlap is on purpose (for example "the first seconds repeat the end of the last clip, so you can pick up the thread"), or the clip does not start before the previous clip ended.
fix: Add one short line before the clip, such as "The first few seconds of this clip repeat the end of the last one, on purpose."
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

Drafted by Lens EA (a Claude), 2026-10-31, from feedback #345 (Luc Brinkman). In the lens "Using dangerous AI, but safely", each part's video clip starts about 15 to 40 seconds before the previous clip ended (part 1 ends 4:40.3, part 2 starts 4:22.6; part 2 ends 13:32.5, part 3 starts 12:50; and so on). It is a good choice, but nothing says it is on purpose, so a learner thinks the wrong clip played. Luc did not want only that lens fixed: he wants a programmatic test that finds overlapping clips, and then a jev check on whether the text points it out.

Not live yet (`enabled: false`), and it cannot work yet: `core/course_checks/present.py` (`_markdown`) leaves out Video segments, so jev never sees the `from::` and `to::` times. What it needs:

- A programmatic step, before jev: for each Video segment, compare its `from::` with the `to::` of the previous Video segment in the same lens or module (clips of the same `source::`). If `from` is earlier than the previous `to`, the clip overlaps; only then call jev on the text between the two clips. If the clip does not overlap, no jev call is needed.
- The step puts a line such as `[Video clip starts 0:38 before the previous clip ended]` into the presentation, so the question above has something to look at. A clip with a `skip::` range still counts by its `from`/`to`.
- Test on the AICF U1 lens (all four overlaps there are unexplained) and on a lens where the intro line says it is on purpose.

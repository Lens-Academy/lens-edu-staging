---
id: T8
enabled: false
name: presumes optional material was read
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
skip_folders: [ Questions ]
question: >-
  Does `paragraph` treat something the learner may have skipped, because it is marked optional or sits in a closed optional box, as if they had read, watched or done it?
criteria:
  "true": >-
    `paragraph` says or implies that the learner has already read, watched or done something that is marked `optional:: true` (or sits in an optional or closed collapse box) in the document, for example "the ideas you just read about", "as you saw in the CSET explainer" or "you already met X", and does not also say what it refers to.
  "false": >-
    Everything `paragraph` says the learner has read, watched or done is required material, or `paragraph` says what the point is in its own words, or it refers to nothing the learner has done before.
fix: Say the point in this paragraph in a few words instead of leaning on the earlier material, or say that it was optional ("if you read the optional X, ...").
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

Drafted by Lens EA (a Claude), 2026-10-31, from feedback #344 (Luc Brinkman): the lens "Using dangerous AI, but safely" opens with "a video shows how the ideas you just read about are tested", but the lens before it in the module (`What control is meant to stop`) is `optional:: true`, so a learner may not have read it. Luc did not want only that instance fixed; he wanted a check that finds this kind of mistake.

Not live yet (`enabled: false`): tune it in the panel first. Things to find out:

- Does jev see the `optional:: true` lines? The presentation nests the document, submodule and lens, but whether the optional markers of the module file reach the prompt is not checked. If they do not, this check can only guess from words like "optional" in the text, and the presentation (or a new field in `core/course_checks/present.py`) has to add them.
- A lens can be required while one article inside it is optional (the case-for-control lens folds its opening in an optional box). The check should look at both levels.
- Test on the #344 paragraph ("Next, a video shows how the ideas you just read about are tested. After it, you read the founding post...") and on its fixed wording.

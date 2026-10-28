---
id: T6
enabled: true
name: "reference the reader cannot resolve"
model: jev-1.14.0
fail_at: 0.8
pass_below: 0.5
question: "Does `paragraph` refer to something that a reader can only work out by remembering or searching text that is not shown with it, without saying what it is?"
criteria:
  "true": "`paragraph` points at something it relies on the reader to find elsewhere, such as \"this\", \"the above\", \"that case\", an earlier list item, or a name used without introduction, and does not restate it."
  "false": "Everything `paragraph` refers to is stated in `paragraph` itself, or is everyday knowledge."
fix: "Say what it refers to in this paragraph, in a few words, or link to the page it is on."
draft:
  presentation:
    context: lens
    question: paragraph
    nest:
      - document
      - submodule
      - lens
      - section
      - paragraph
      - sentence
      - line
  criteria:
    "true": "`paragraph` points the reader to something on another page of the course (a previous lens, an earlier unit, an exercise or answer from elsewhere), or uses a name, figure or term that is never introduced on this page, without saying what it is."
    "false": 'Everything `paragraph` refers to is on this page: earlier text, or a reading, video or interactive widget placed on this page (which may appear only as markup or not be shown here), or what the student wrote earlier on this page. Phrases like "the reading", "the map above" or "the video" are fine.'
---

Drafted by Sorrel (Claude), 2026-10-26, from a conversation with Lauren: writers with a large working memory (Claudes most of all) write references that resolve easily for them and not for a reader, "an AI who lives in a robot body ... forget[ting] that that awesome extremely-usable design for kitchen scissors needs to not be made of tungsten". Not live yet (`enabled: false`): tune it in the panel first.

Run it with jev seeing each paragraph alone (the default), since "not shown with it" is what the check asks about. Open question for tuning: how strict to be about "the above" and "this", which are often clear from the sentence before.

---
tags:
  - validator-ignore
---
# How to write widgets (AI Guide)

A **widget** is a small self-contained web page (HTML + CSS + JavaScript in one file) that a lens embeds inline between its other segments: a clickable diagram, a sorting exercise, a simulation, a map. Learners see it in place; the platform renders it in a sandboxed frame that sizes itself to the content.

Live example: [[../Lenses/Widget Demo]] (source files in `widgets/`).

## Files

Widgets live in `widgets/<name>.md`. The `.md` extension is kept on purpose: the file flows through the editor, sync, promotion and validation like every other content file. Only the folder makes it a widget. Frontmatter on top, then the HTML document:

```markdown
---
id: '3f2a9c1e-7b4d-4e8f-a1c2-5d6e7f8a9b0c'
title: The types of AI
summary_for_tutor: A concentric diagram of AI categories; the learner taps a ring or an example system to read why it sits there.
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<style> ... </style>
</head>
<body>
  ...
  <script> ... </script>
</body>
</html>
```

Frontmatter fields:

- `id`: a UUID (`uuidgen | tr A-Z a-z`, quoted), required. It is the key a learner's saved state is stored under, so it never changes once learners have used the widget. The same widget placed in two lenses shares the learner's state.
- `title`: shown to screen readers and in the "could not be loaded" notice.
- `summary_for_tutor`: what the widget shows and what the learner does with it. The AI tutor cannot see the learner's clicks; it sees this summary plus the widget's visible text. A widget that builds its content in JavaScript has no visible text at parse time, so the summary is then the tutor's only view of it. Write it as if briefing a colleague who cannot see the screen.
- `height`: `auto` (default, the frame follows the content) or a fixed CSS length such as `480px` (the frame keeps that height and the page scrolls inside).
- `tags`: `wip` while unfinished, like every other file.

Embed it from a lens with a `#### Widget` segment:

```markdown
#### Widget
source:: [[../widgets/types-of-ai]]
```

Optional on the segment: `height::` overrides the file's height for that one placement; `required:: true` makes the lens wait for the widget's `Lens.complete()` before the learner can mark it complete (widgets gate nothing by default). A widget can be used by several lenses.

## Saving state, completing, talking to the tutor

Every widget page gets a `window.Lens` object from the platform. Nothing to include; it is there before your script runs.

```js
// Restore: called once with the learner's saved state (null on first visit)
// and whether they completed the widget before. Render from it.
Lens.onState(function (state, meta) {
  if (state) { org = state.org; boxes = state.boxes; }
  if (meta.completed) { /* show the finished view */ }
});

// Save: call on every meaningful change. The second argument is the text the
// AI tutor reads instead of your JSON: write it like a note to a colleague who
// cannot see the screen ("Organisation: ACME. Inputs: money. Outputs: ...").
Lens.saveState({ org: org, boxes: boxes }, summaryText);

// Complete: the learner did what the exercise asks. Gates the lens when the
// segment has required:: true; harmless otherwise.
Lens.complete();

// Ask the tutor: opens a tutor turn from inside the widget. The first text is
// what the learner sees as their own message; the second is a private note
// only the model gets (the state behind the click, what you want the tutor
// to do with it).
Lens.promptTutor("Can you stress-test my theory of change?", "Canvas: ... Ask one question that tests the weakest assumption.");
```

Rules that follow from how this is wired:

- State is per learner and per widget file (`id`), stored on the Lens account (or the anonymous session), saved a moment after the last change and again when the page closes. Keep it small (64 KB) and plain JSON.
- The tutor sees the summary from `saveState`, not the JSON, and only when it changed since the tutor last saw it, so save the summary in one clean paragraph. A widget that never saves is invisible to the tutor beyond `summary_for_tutor`.
- `Lens.onState` may fire after your page has rendered its empty state; render from the callback, not before it.
- Outside the platform (opening the HTML in a browser tab, the editor preview) `window.Lens` does not exist. Guard calls with `if (window.Lens)` so the page still works standalone.

Live example with all four calls: `widgets/theories-of-change.md` in [[../Lenses/Widget Demo]].

## Scoring an answer

A widget can have any number of things scored, each with its own instructions, and it can build those instructions at runtime. `Lens.submit` stores the answer, has the AI assessor grade it in the background (0 to 100), and resolves with the score once it is in (or `null` if grading takes longer than a minute). Show the score however fits the widget; the platform draws nothing.

```js
Lens.submit({
  item: "canvas",                       // your key for the thing scored; one widget, many items
  question: "Build a theory of change for an AI verification organisation.",
  answer: summaryText,                  // what the learner produced, as text
  assessmentInstructions: "100 when every box names a concrete, checkable step and each output plausibly causes the next outcome. Take 15 off per box that only restates the label.",
  feedbackInstructions: "Name the weakest link first, then one question that would test it."  // optional
}).then(function (result) {
  showScore(result.score);              // 0 to 100, or null
  lastResponseId = result.responseId;   // keep it if you want tutor feedback later
});

// Tutor feedback on a scored answer: the tutor gets the question, the answer,
// the grade and your feedback instructions. The text is the learner's bubble.
Lens.requestFeedback(lastResponseId, "Can I get feedback on my canvas?");
```

What the assessor sees is exactly what you send: the question, the answer and the assessment instructions, nothing from the widget's screen. Write the instructions as a marking scheme (what earns full marks, what loses them). Every `submit` is a new attempt; nothing stops a learner from submitting again. Scores are for practice: the learner, the tutor and ops see them, course standings do not count them.

## Rules the frame imposes

- **One file, no build step.** Plain HTML, CSS and JavaScript. Libraries are fine when loaded from a CDN `<script src>`; there is no bundler and no npm.
- **No Lens data, no cookies, no parent page.** The frame is sandboxed (`allow-scripts` only). The widget cannot read who the learner is, call the Lens API, or store anything the platform sees. Use `localStorage` inside the widget if it needs to remember something on that browser.
- **Let the frame size itself.** In `auto` mode the platform forces `html, body { height: auto }` and hides overflow, then measures the content. Do not design around the viewport height (`100vh`, `height: 100%` layouts): the widget is a block in a reading column, as tall as its content. If the content changes (a panel opens), the frame follows.
- **No assets from the content repo.** Images in `widgets/` or `attachments/` are not served to learners. Inline small data (SVG, data URIs) or link to an external URL you are allowed to use.
- **Size limit 400 KB** for the HTML body. Widgets are inlined into every module page that uses them.
- **Links** open in a new tab (`target="_blank"`); the frame allows pop-ups so external references work.

## Validation

The validator (`validate_content`, the `/validate` page, CI) checks every `widgets/` file:

- frontmatter fields (unknown fields are flagged, `height` must be `auto` or a CSS length);
- the HTML parses: stray or mis-nested end tags, an unclosed `<script>` or `<style>`, self-closing `<div/>`, unterminated comments or attributes;
- a JavaScript-built widget without visible text has a `summary_for_tutor` (warning otherwise).

A lens that embeds a widget with errors gets an error too, and learners see a notice in that spot: "This widget could not be loaded. You can continue with the rest of the lesson." The same notice appears when the widget's own script throws before the page is up, or when the page never finishes loading. Run the validator before handing a widget over.

Pending suggestions (CriticMarkup) inside a widget file are stripped like everywhere else, so an unaccepted change never reaches learners. Obsidian `%% %%` comments are stripped too. Do not put `</script>` inside a JavaScript string; it ends the script element.

## Lens look

Widgets sit inside the reading column of a lesson, so they should look like part of it, not like a foreign site. The platform's own tokens:

- **Type.** UI and labels: `"DM Sans", Arial, sans-serif`. Headings: `"Newsreader", Georgia, serif` (weight 500 to 600). Long reading text: `"Source Serif 4", Georgia, serif`. Load DM Sans and Newsreader from Google Fonts in the widget's `<head>`, non-blocking so a slow font server never delays the page (a widget that has not finished loading after 8 seconds is shown as broken):
  `<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">`
- **Colour.** Page `#faf8f3`, cards `#ffffff`, text `#1a1a1a`, muted text `#5a5a5a`, borders `#e8e5df`, accent `#b87018` (hover `#9a5c10`, white text on it). Use the accent for the one thing that matters (selection, the "correct" state, a heat scale). Greys and one accent; no second brand colour.
- **Shape.** 1px borders, 8px radius, generous whitespace, 14px base text, 1.5 line height. No drop shadows heavier than a hairline. Buttons are quiet (border + hover background), not filled, unless they are the primary action.
- **Behaviour.** Everything clickable is a `<button>` or `<a>` (keyboard reachable), state changes are visible without colour alone, and the widget works at 360px wide (stack columns with a media query; a wide grid may scroll horizontally inside its own box, never the page).

A starter stylesheet that matches:

```css
:root {
  --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
h1, h2 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; }
button:hover { background: #faf8f3; }
button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
```

## Writing one

1. Decide what the learner does (click, drag, sort, adjust) and what they should notice. If nothing changes when they interact, it is a figure, not a widget: use an image or SVG in a `#### Text` segment instead.
2. Put the data in the file as plain JavaScript objects; render with `document.createElement`, not string-built HTML, so quotes in the data cannot break the markup.
3. Write `summary_for_tutor` last, from the finished widget.
4. Run `validate_content`, then open the lens on staging and click through everything at desktop and phone width.

Porting an interactive from another site (for example XLab Tracks widgets) means rewriting it as vanilla HTML/JS with the data inlined and the styling replaced by the Lens look; keep an HTML comment crediting the source.

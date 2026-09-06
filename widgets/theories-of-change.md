---
id: 'c3f8b1e2-7d94-4a6b-9e15-2b0c4d8f6a71'
title: Theory of change
summary_for_tutor: "A theory-of-change canvas. The learner names an organisation (real or imagined) and fills eight boxes, one at a time: Inputs (what do we need), Outputs (what do we do; who do we reach), Outcomes (short-term, intermediate, long-term), Assumptions, and External factors. Their entries are saved and shown to you in the widget-state block as they write. The widget is complete when all eight boxes have text. Help them tighten each link in the chain: does each output plausibly cause the next outcome, and which assumptions carry the most weight? Content ported from XLab's Verification track."
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Theory of change</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "theories-of-change". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 26px; margin: 4px 0 8px; }
  .lede { color: var(--muted); margin: 0 0 16px; max-width: 42rem; }
  label { display: block; font-size: 12px; font-weight: 600; margin-bottom: 4px; }
  input, textarea {
    width: 100%; font: inherit; color: inherit; background: #fff;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  input:focus, textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  textarea { min-height: 96px; resize: vertical; }
  .org { margin-bottom: 16px; max-width: 28rem; }
  .canvas { display: grid; gap: 4px; grid-template-columns: repeat(6, minmax(0, 1fr)); }
  .band { background: var(--surface); text-align: center; font-size: 11px; font-weight: 600; padding: 6px 4px; border-radius: 4px; }
  .cell {
    font: inherit; color: inherit; text-align: left; vertical-align: top; cursor: pointer;
    min-height: 72px; padding: 8px; border: 1px solid var(--border); border-radius: 4px; background: #fff;
    white-space: pre-wrap; font-size: 11px; line-height: 1.35;
  }
  .cell:hover { background: var(--surface); }
  .cell.is-active { border-color: var(--accent); box-shadow: inset 0 0 0 1px var(--accent); }
  .cell.is-empty { color: var(--muted); }
  .cell .lbl { display: block; font-weight: 600; margin-bottom: 2px; color: var(--text); }
  .span2 { grid-column: span 2; }
  .span3 { grid-column: span 3; }
  .span6 { grid-column: span 6; }
  .editor { margin-top: 16px; border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--surface); }
  .editor h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 0; }
  .cue { color: var(--muted); font-size: 12px; margin: 2px 0 10px; }
  .row { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; margin-top: 12px; }
  .nav { display: flex; gap: 8px; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer;
  }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  .progress { font-size: 12px; color: var(--muted); }
  .done { margin-top: 12px; padding: 10px 12px; border: 1px solid var(--border); border-radius: 8px; background: #fff; display: none; }
  .done.is-visible { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; }
  @media (max-width: 600px) {
    .canvas { grid-template-columns: repeat(2, minmax(0, 1fr)); }
    .span2, .span3, .span6 { grid-column: span 2; }
  }
</style>
</head>
<body>
<p class="eyebrow">Exercise</p>
<h1>Build a theory of change</h1>
<p class="lede">Pick an organisation, real or imagined, that works on AI verification. Fill the canvas one box at a time; each box asks what has to be true for the next one to happen. Your entries are saved as you type.</p>

<div class="org">
  <label for="org">Organisation</label>
  <input id="org" type="text" placeholder="e.g. a treaty verification body, a chip-tracking startup, a research lab">
</div>

<div class="canvas" id="canvas" aria-label="Theory of change canvas"></div>

<div class="editor">
  <p class="eyebrow" id="ed-band"></p>
  <h2 id="ed-label"></h2>
  <p class="cue" id="ed-cue"></p>
  <textarea id="ed-text" aria-label="Box text"></textarea>
  <div class="row">
    <span class="progress" id="progress"></span>
    <span class="nav">
      <button type="button" id="prev">Back</button>
      <button type="button" id="next" class="primary">Next box</button>
    </span>
  </div>
</div>

<div class="done" id="done">
  <span id="done-text">All eight boxes filled. Get it scored, or ask the tutor to stress-test the chain.</span>
  <span class="nav">
    <button type="button" id="score" class="primary">Score my canvas</button>
    <button type="button" id="feedback" hidden>Get feedback on the score</button>
    <button type="button" id="ask">Ask the tutor to review it</button>
  </span>
</div>

<script>
  var BOXES = [
    { id: "inputs-need", band: "Inputs", label: "What do we need?", cue: "Resources · people" },
    { id: "outputs-do", band: "Outputs", label: "What do we do?", cue: "Activities" },
    { id: "outputs-reach", band: "Outputs", label: "Who do we reach?", cue: "New audience · collaborators" },
    { id: "outcome-short", band: "Outcome", label: "Short-term", cue: "Knowledge increased" },
    { id: "outcome-mid", band: "Outcome", label: "Intermediate", cue: "Behavior changed · decision-making done" },
    { id: "outcome-long", band: "Outcome", label: "Long-term", cue: "Conditions changed" },
    { id: "assumptions", band: "Assumptions", label: "Assumptions", cue: "Internal / testable" },
    { id: "external", band: "External factors", label: "External factors", cue: "External / undefined" }
  ];
  var LAYOUT = [
    ["band", "Inputs", "span2"], ["band", "Outputs", "span2"], ["band", "Outcome", "span2"],
    ["cell", "inputs-need", "span2"], ["cell", "outputs-do", "span1"], ["cell", "outputs-reach", "span1"],
    ["cell", "outcome-short", "span2"], ["gap", "", "span2"], ["gap", "", "span2"],
    ["cell", "outcome-mid", "span1"], ["cell", "outcome-long", "span1"],
    ["band", "Assumptions", "span3"], ["band", "External factors", "span3"],
    ["cell", "assumptions", "span3"], ["cell", "external", "span3"]
  ];

  var state = { org: "", boxes: {} };
  var step = 0;
  var completed = false;
  var byId = {};

  var canvas = document.getElementById("canvas");
  var orgInput = document.getElementById("org");
  var edBand = document.getElementById("ed-band");
  var edLabel = document.getElementById("ed-label");
  var edCue = document.getElementById("ed-cue");
  var edText = document.getElementById("ed-text");
  var progress = document.getElementById("progress");
  var prevBtn = document.getElementById("prev");
  var nextBtn = document.getElementById("next");
  var done = document.getElementById("done");

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function boxById(id) { for (var i = 0; i < BOXES.length; i++) if (BOXES[i].id === id) return BOXES[i]; return null; }
  function filledCount() { var n = 0; BOXES.forEach(function (b) { if ((state.boxes[b.id] || "").trim()) n++; }); return n; }

  LAYOUT.forEach(function (item) {
    var kind = item[0], key = item[1], span = item[2];
    if (kind === "band") { canvas.appendChild(el("div", "band " + span, key)); return; }
    if (kind === "gap") { canvas.appendChild(el("div", span)); return; }
    var b = boxById(key);
    var btn = el("button", "cell " + span); btn.type = "button";
    btn.setAttribute("aria-label", b.label + ": edit this box");
    btn.appendChild(el("span", "lbl", b.label));
    btn.appendChild(el("span", "txt", ""));
    btn.addEventListener("click", function () { step = BOXES.indexOf(b); render(); edText.focus(); });
    byId[b.id] = btn;
    canvas.appendChild(btn);
  });

  function summary() {
    var lines = ["Organisation: " + (state.org.trim() || "(not named yet)")];
    BOXES.forEach(function (b) {
      var v = (state.boxes[b.id] || "").trim();
      lines.push(b.band + " / " + b.label + ": " + (v || "(empty)"));
    });
    lines.push("Filled: " + filledCount() + " of " + BOXES.length + " boxes.");
    return lines.join("\n");
  }

  function persist() {
    if (!window.Lens) return;
    Lens.saveState({ org: state.org, boxes: state.boxes }, summary());
    if (!completed && filledCount() === BOXES.length && state.org.trim()) {
      completed = true;
      Lens.complete();
    }
  }

  function render() {
    var box = BOXES[step];
    BOXES.forEach(function (b) {
      var btn = byId[b.id], v = (state.boxes[b.id] || "").trim();
      btn.querySelector(".txt").textContent = v || "—";
      btn.classList.toggle("is-empty", !v);
      btn.classList.toggle("is-active", b.id === box.id);
      btn.setAttribute("aria-current", b.id === box.id ? "step" : "false");
    });
    edBand.textContent = box.band;
    edLabel.textContent = box.label;
    edCue.textContent = box.cue;
    if (edText.value !== (state.boxes[box.id] || "")) edText.value = state.boxes[box.id] || "";
    progress.textContent = filledCount() + " of " + BOXES.length + " boxes filled";
    prevBtn.disabled = step === 0;
    nextBtn.textContent = step === BOXES.length - 1 ? "Done" : "Next box";
    done.classList.toggle("is-visible", filledCount() === BOXES.length);
  }

  orgInput.addEventListener("input", function () { state.org = orgInput.value; persist(); });
  edText.addEventListener("input", function () { state.boxes[BOXES[step].id] = edText.value; render(); persist(); });
  prevBtn.addEventListener("click", function () { if (step > 0) { step--; render(); edText.focus(); } });
  nextBtn.addEventListener("click", function () { if (step < BOXES.length - 1) { step++; render(); edText.focus(); } else { render(); } });
  document.getElementById("ask").addEventListener("click", function () {
    if (!window.Lens) return;
    Lens.promptTutor(
      "Here is my theory of change for " + (state.org.trim() || "my organisation") + ". Can you stress-test the chain?",
      "The learner asks for a review of their theory-of-change canvas. Current canvas:\n" + summary() +
      "\nCheck each link (inputs to outputs to outcomes) for a plausible causal step, name the assumption that carries the most weight, and ask one question that would test it. Do not rewrite their boxes for them."
    );
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.org === "string") state.org = saved.org;
      if (saved.boxes && typeof saved.boxes === "object") {
        BOXES.forEach(function (b) { var v = saved.boxes[b.id]; if (typeof v === "string") state.boxes[b.id] = v; });
      }
    }
    completed = !!(meta && meta.completed);
    orgInput.value = state.org;
    var first = -1;
    for (var i = 0; i < BOXES.length; i++) { if (!(state.boxes[BOXES[i].id] || "").trim()) { first = i; break; } }
    step = first === -1 ? BOXES.length - 1 : first;
    render();
  }

  render();
  if (window.Lens) { Lens.onState(hydrate); }
</script>
</body>
</html>

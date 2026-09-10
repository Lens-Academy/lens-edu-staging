---
id: 'c3f8b1e2-7d94-4a6b-9e15-2b0c4d8f6a71'
title: Theory of change
height: auto
summary_for_tutor: "A theory-of-change canvas laid out as a single vertical chain. The learner names an organisation (real or imagined), then fills eight boxes grouped into five stages in causal order: Inputs (what do we need), Outputs (what do we do; who do we reach), Outcome (short-term, intermediate, long-term), then Assumptions and External factors, which sit under the chain rather than in it. Each stage is one full-width band with one heading; every box has its own text area, and a Back / Next box stepper walks through them one at a time. Their entries are saved and shown to you in the widget-state block as they write. The widget is complete when the organisation is named and all eight boxes have text. Help them tighten each link in the chain: does each output plausibly cause the next outcome, and which assumptions carry the most weight? Content ported from XLab's Verification track."
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
  textarea { min-height: 80px; resize: vertical; }
  .org { margin-bottom: 12px; max-width: 28rem; }

  /* Stepper toolbar: progress on the left, Back / Next box on the right. */
  .toolbar {
    display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between;
    border: 1px solid var(--border); border-radius: 8px; background: var(--surface);
    padding: 8px 12px; margin-bottom: 16px;
  }
  .progress { font-size: 12px; color: var(--muted); }
  .nav { display: flex; gap: 8px; }

  /* One full-width band per stage. Never side by side, at any width. */
  .chain { display: block; }
  .stage { display: block; width: 100%; border: 1px solid var(--border); border-radius: 8px; background: #fff; overflow: hidden; }
  .stage-head { background: var(--surface); border-bottom: 1px solid var(--border); border-left: 3px solid var(--accent); padding: 10px 14px; }
  .stage-head h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; line-height: 1.25; margin: 0; }
  .stage-q { margin: 3px 0 0; font-size: 13px; color: var(--muted); }
  .stage-def { margin: 6px 0 0; font-size: 12px; line-height: 1.45; color: var(--muted); }
  .items { display: block; padding: 12px 14px; }
  .item { display: block; width: 100%; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 10px 12px; }
  .item + .item { margin-top: 10px; }
  .item.is-active { border-color: var(--accent); box-shadow: inset 0 0 0 1px var(--accent); }
  .item-head { display: flex; flex-wrap: wrap; gap: 4px 10px; align-items: baseline; justify-content: space-between; }
  .item-label { margin: 0; font-size: 13px; font-weight: 600; }
  .item-status { font-size: 11px; color: var(--muted); margin-left: auto; }
  .item-cue { margin: 1px 0 8px; font-size: 12px; color: var(--muted); }

  /* Connectors. Solid arrow along the causal chain, dashed rule down to the context bands. */
  .arrow { display: flex; justify-content: center; padding: 6px 0; }
  .arrow svg { display: block; }
  .ctx-rule { border-top: 1px dashed var(--border); margin: 20px 0 14px; }
  .stage.is-context { border-style: dashed; }
  .stage.is-context .stage-head { border-left-color: var(--muted); }
  .chain > .stage + .stage { margin-top: 12px; }

  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer;
  }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  .done { margin-top: 16px; padding: 10px 12px; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); display: none; }
  .done.is-visible { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; }
</style>
</head>
<body>
<p class="eyebrow">Exercise</p>
<h1>Build a theory of change</h1>
<p class="lede">Pick an organisation, real or imagined, that works on AI verification. Fill the chain one box at a time, from the top down; each box asks what has to be true for the next one to happen. Your entries are saved as you type.</p>

<div class="org">
  <label for="org">Organisation</label>
  <input id="org" type="text" placeholder="e.g. a treaty verification body, a chip-tracking startup, a research lab">
</div>

<div class="toolbar">
  <span class="progress" id="progress"></span>
  <span class="nav">
    <button type="button" id="prev">Back</button>
    <button type="button" id="next" class="primary">Next box</button>
  </span>
</div>

<div class="chain" id="chain" aria-label="Your theory of change, top to bottom"></div>

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

  // One band per stage, in causal order. "question" is XLab's own guiding question for
  // the stage (only where the stage has a single one); "definition" is XLab's sentence
  // from the lesson, kept because outputs and outcomes are the pair learners confuse.
  // "chain" marks the three causal stages; the last two sit under the chain, not in it.
  var STAGES = [
    { band: "Inputs", question: "What do we need?", chain: true, boxes: ["inputs-need"] },
    {
      band: "Outputs", chain: true, boxes: ["outputs-do", "outputs-reach"],
      definition: "Outputs are tangible products you produced: a paper, a benchmark, an eval, a workshop, a policy memo."
    },
    {
      band: "Outcome", chain: true, boxes: ["outcome-short", "outcome-mid", "outcome-long"],
      definition: "Outcomes are what changed because of those outputs: a lab altered a training procedure, a policymaker incorporated a threat model into a draft bill, a researcher updated their estimates."
    },
    { band: "Assumptions", chain: false, boxes: ["assumptions"] },
    { band: "External factors", chain: false, boxes: ["external"] }
  ];

  var STORE_KEY = "lens-widget-theories-of-change";
  var state = { org: "", boxes: {} };
  var step = 0;
  var completed = false;
  var itemEl = {};
  var areaEl = {};
  var statusEl = {};

  var chain = document.getElementById("chain");
  var orgInput = document.getElementById("org");
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

  function arrow() {
    var wrap = el("div", "arrow");
    wrap.setAttribute("aria-hidden", "true");
    var ns = "http://www.w3.org/2000/svg";
    var svg = document.createElementNS(ns, "svg");
    svg.setAttribute("width", "18"); svg.setAttribute("height", "26"); svg.setAttribute("viewBox", "0 0 18 26");
    var line = document.createElementNS(ns, "path");
    line.setAttribute("d", "M9 1 V21 M2 15 L9 22 L16 15");
    line.setAttribute("fill", "none");
    line.setAttribute("stroke", "#b87018");
    line.setAttribute("stroke-width", "1.6");
    line.setAttribute("stroke-linecap", "round");
    line.setAttribute("stroke-linejoin", "round");
    svg.appendChild(line);
    wrap.appendChild(svg);
    return wrap;
  }

  function buildItem(b, hideLabel) {
    var item = el("div", "item");
    item.setAttribute("data-box", b.id);
    var head = el("div", "item-head");
    if (!hideLabel) head.appendChild(el("p", "item-label", b.label));
    var st = el("span", "item-status", "");
    head.appendChild(st);
    item.appendChild(head);
    item.appendChild(el("p", "item-cue", b.cue));
    var area = document.createElement("textarea");
    area.id = "t-" + b.id;
    area.placeholder = "Fill in this box, then move to the next one.";
    area.setAttribute("aria-label", b.label + " (" + b.cue + ")");
    item.appendChild(area);
    area.addEventListener("input", function () {
      state.boxes[b.id] = area.value;
      step = BOXES.indexOf(b);
      render();
      persist();
    });
    area.addEventListener("focus", function () { step = BOXES.indexOf(b); render(); });
    item.addEventListener("click", function (ev) { if (ev.target !== area) area.focus(); });
    itemEl[b.id] = item; areaEl[b.id] = area; statusEl[b.id] = st;
    return item;
  }

  STAGES.forEach(function (stage, i) {
    if (i > 0) chain.appendChild(stage.chain ? arrow() : el("div", "ctx-rule"));
    var sec = el("section", "stage" + (stage.chain ? "" : " is-context"));
    var head = el("div", "stage-head");
    head.appendChild(el("h2", null, stage.band));
    if (stage.question) head.appendChild(el("p", "stage-q", stage.question));
    if (stage.definition) head.appendChild(el("p", "stage-def", stage.definition));
    sec.appendChild(head);
    var items = el("div", "items");
    stage.boxes.forEach(function (id) {
      var b = boxById(id);
      // Do not print the box label twice: drop it when the stage heading or its
      // guiding question already says the same words.
      var hide = b.label === stage.band || b.label === stage.question;
      items.appendChild(buildItem(b, hide));
    });
    sec.appendChild(items);
    chain.appendChild(sec);
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
    if (window.Lens) {
      Lens.saveState({ org: state.org, boxes: state.boxes }, summary());
      if (!completed && filledCount() === BOXES.length && state.org.trim()) {
        completed = true;
        Lens.complete();
      }
    } else {
      // Standalone (the editor preview): keep the canvas in localStorage so the lede is true.
      try { localStorage.setItem(STORE_KEY, JSON.stringify({ org: state.org, boxes: state.boxes })); } catch (e) {}
    }
  }

  function render() {
    var box = BOXES[step];
    BOXES.forEach(function (b) {
      var v = (state.boxes[b.id] || "").trim();
      var area = areaEl[b.id];
      if (area.value !== (state.boxes[b.id] || "")) area.value = state.boxes[b.id] || "";
      statusEl[b.id].textContent = v ? "✓ filled" : "";
      itemEl[b.id].classList.toggle("is-active", b.id === box.id);
      itemEl[b.id].setAttribute("aria-current", b.id === box.id ? "step" : "false");
    });
    progress.textContent = filledCount() + " of " + BOXES.length + " boxes filled";
    prevBtn.disabled = step === 0;
    nextBtn.textContent = step === BOXES.length - 1 ? "Done" : "Next box";
    done.classList.toggle("is-visible", filledCount() === BOXES.length);
  }

  function goTo(i) {
    step = Math.max(0, Math.min(BOXES.length - 1, i));
    render();
    areaEl[BOXES[step].id].focus();
  }

  orgInput.addEventListener("input", function () { state.org = orgInput.value; persist(); });
  prevBtn.addEventListener("click", function () { goTo(step - 1); });
  nextBtn.addEventListener("click", function () { goTo(step + 1); });

  var askBtn = document.getElementById("ask");
  askBtn.addEventListener("click", function () {
    if (!window.Lens) return;
    Lens.promptTutor(
      "Here is my theory of change for " + (state.org.trim() || "my organisation") + ". Can you stress-test the chain?",
      "The learner asks for a review of their theory-of-change canvas. Current canvas:\n" + summary() +
      "\nCheck each link (inputs to outputs to outcomes) for a plausible causal step, name the assumption that carries the most weight, and ask one question that would test it. Do not rewrite their boxes for them."
    );
  });

  // Scoring: the whole canvas is one scorable item. The assessor sees only
  // what is sent here (question, answer, instructions), never the screen.
  var scoreBtn = document.getElementById("score");
  var feedbackBtn = document.getElementById("feedback");
  var doneText = document.getElementById("done-text");
  var lastResponseId = null;
  scoreBtn.addEventListener("click", function () {
    if (!window.Lens || !Lens.submit) return;
    scoreBtn.disabled = true;
    doneText.textContent = "Scoring your canvas...";
    Lens.submit({
      item: "canvas",
      question: "Build a theory of change for an organisation working on AI verification: inputs, outputs, short-, intermediate- and long-term outcomes, assumptions and external factors.",
      answer: summary(),
      assessmentInstructions: "Score 0 to 100. Full marks when every box names something concrete and checkable (a real resource, activity, audience or measurable change, not a restatement of the box label) and each output plausibly causes the next outcome. Take about 12 off per box that is vague or missing, and up to 20 off when the chain has a causal gap the assumptions do not cover.",
      feedbackInstructions: "Name the weakest link in the chain first and say why. Then ask one question that would test the assumption carrying the most weight. Do not rewrite their boxes."
    }).then(function (result) {
      lastResponseId = result.responseId;
      doneText.textContent = result.score == null
        ? "Scoring is taking a while; ask the tutor for feedback meanwhile."
        : "Score: " + result.score + " / 100.";
      feedbackBtn.hidden = false;
      scoreBtn.disabled = false;
      scoreBtn.textContent = "Score again";
    }, function () {
      doneText.textContent = "Could not score the canvas right now.";
      scoreBtn.disabled = false;
    });
  });
  feedbackBtn.addEventListener("click", function () {
    if (!window.Lens || lastResponseId == null) return;
    Lens.requestFeedback(lastResponseId, "Can I get feedback on my theory-of-change score?");
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
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    // Nothing here can reach a tutor or an assessor, so do not offer it.
    scoreBtn.hidden = true;
    feedbackBtn.hidden = true;
    askBtn.hidden = true;
    doneText.textContent = "All eight boxes filled.";
    var raw = null;
    try { raw = localStorage.getItem(STORE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
</script>
</body>
</html>

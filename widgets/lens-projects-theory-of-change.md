---
id: '7a1d3c55-2e84-4b9f-a6c0-91e2f4b8d317'
title: Your project's theory of change
height: auto
summary_for_tutor: "A theory-of-change canvas for the learner's own Lens Projects project, laid out as a single vertical chain. The learner names their project, then fills eight boxes grouped into five stages in causal order: Inputs (what do I need), Outputs (what will I make; who will I reach), Outcomes (by the end of the course, within a year, long-term), then Assumptions (with the riskiest one marked) and External factors, which sit under the chain rather than in it. Fit-track learners use it for finding where they fit: the people they reach are those doing the work they are curious about, and the change is what they learn about their fit. Entries are saved and shown to you in the widget-state block as they write. A Get feedback button submits the whole chain and then requests written feedback, so a feedback turn from this widget is the learner asking you to read their chain. The widget is complete when the project is named and all eight boxes have text. Help them tighten each link: does each output plausibly cause the next outcome, and which assumption carries the most weight? Never rewrite their boxes; the course rule is to use AI as a tool, not a decision-maker. Adapted from Lens's Theory of change widget, which was ported from XLab's Verification track."
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Your project's theory of change</title>
<!-- Adapted for Lens Projects from widgets/theories-of-change.md, itself ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "theories-of-change". -->
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
  .lede { color: var(--muted); margin: 0 0 10px; max-width: 42rem; }
  .fit-note { color: var(--muted); margin: 0 0 16px; max-width: 42rem; font-size: 13px; border-left: 3px solid var(--border); padding-left: 10px; }
  label { display: block; font-size: 12px; font-weight: 600; margin-bottom: 4px; }
  input, textarea {
    width: 100%; font: inherit; color: inherit; background: #fff;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  input:focus, textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  textarea { min-height: 80px; resize: vertical; }
  .org { margin-bottom: 16px; max-width: 28rem; }

  .chain { display: block; }
  .stage { display: block; width: 100%; border: 1px solid var(--border); border-radius: 8px; background: #fff; overflow: hidden; }
  .stage-head { background: var(--surface); border-bottom: 1px solid var(--border); border-left: 3px solid var(--accent); padding: 10px 14px; }
  .stage-head h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; line-height: 1.25; margin: 0; }
  .stage-q { margin: 3px 0 0; font-size: 13px; color: var(--muted); }
  .stage-def { margin: 6px 0 0; font-size: 12px; line-height: 1.45; color: var(--muted); }
  .items { display: block; padding: 12px 14px; }
  .item { display: block; width: 100%; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 10px 12px; }
  .item + .item { margin-top: 10px; }
  .item-head { display: flex; flex-wrap: wrap; gap: 4px 10px; align-items: baseline; justify-content: space-between; }
  .item-label { margin: 0; font-size: 13px; font-weight: 600; }
  .item-status { font-size: 11px; color: var(--muted); margin-left: auto; }
  .item-cue { margin: 1px 0 8px; font-size: 12px; color: var(--muted); }

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
  .feedback { margin-top: 20px; padding: 14px; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); }
  .feedback h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
  .fb-lede { margin: 0 0 10px; font-size: 13px; color: var(--muted); max-width: 42rem; }
  .fb-hint { margin: 8px 0 0; font-size: 12px; color: var(--muted); }
  .fb-out { margin: 10px 0 0; padding: 10px 12px; border: 1px solid var(--border); border-radius: 8px; background: #fff; font-size: 13px; }
  .fb-out p { margin: 0 0 6px; }
  .fb-out p:last-child { margin-bottom: 0; }
  button.is-busy { opacity: 0.7; }
</style>
</head>
<body>
<p class="eyebrow">Exercise</p>
<h1>Build your project's theory of change</h1>
<p class="lede">Map how your project is supposed to make a difference, from what you need to what changes. Fill the chain from the top down, in whatever order suits you; each box asks what has to be true for the next one to happen. Your entries are saved as you type.</p>
<p class="fit-note">On the Fit track? Your project is finding where you fit. The people you reach are the ones doing the work you are curious about, and the change is what you will know about your fit.</p>

<div class="org">
  <label for="org">Your project</label>
  <input id="org" type="text" placeholder="e.g. a replication of one eval on a newer model, a briefing for my representative's office, a career transition post">
</div>

<div class="chain" id="chain" aria-label="Your theory of change, top to bottom"></div>

<div class="feedback">
  <h2>Feedback</h2>
  <p class="fb-lede">Ask for a read of the whole chain: what is unclear, where a link between two stages is missing or not credible, where an output is written as an outcome, and which assumptions are still implicit.</p>
  <button type="button" id="get-feedback" class="primary" disabled>Get feedback</button>
  <p class="fb-hint" id="fb-hint"></p>
  <div class="fb-out" id="fb-out" hidden></div>
</div>

<script>
  var BOXES = [
    { id: "inputs-need", band: "Inputs", label: "What do I need?", cue: "Your skills, people, tools, time" },
    { id: "outputs-do", band: "Outputs", label: "What will I make?", cue: "The thing itself: a post, a replication, a briefing, a workshop, a career doc" },
    { id: "outputs-reach", band: "Outputs", label: "Who will I reach?", cue: "A specific group you could message this week" },
    { id: "outcome-short", band: "Outcomes", label: "By the end of the course", cue: "What will be different for them that someone could observe?" },
    { id: "outcome-mid", band: "Outcomes", label: "Within a year", cue: "What might they do differently because of it?" },
    { id: "outcome-long", band: "Outcomes", label: "Long-term", cue: "How does that connect to reducing risk from AI?" },
    { id: "assumptions", band: "Assumptions", label: "Assumptions", cue: "What has to be true for this to work? Mark the one you are least sure of: that is your riskiest assumption." },
    { id: "external", band: "External factors", label: "External factors", cue: "What outside your control could help or block this?" }
  ];

  var STAGES = [
    { band: "Inputs", question: "What do I need?", chain: true, boxes: ["inputs-need"] },
    {
      band: "Outputs", chain: true, boxes: ["outputs-do", "outputs-reach"],
      definition: "Outputs are things you made: a post, a replication, a briefing, a workshop, a career doc."
    },
    {
      band: "Outcomes", chain: true, boxes: ["outcome-short", "outcome-mid", "outcome-long"],
      definition: "Outcomes are what changed because of them: a reader tried a method, an office asked a follow-up question, you ruled a career path in or out."
    },
    { band: "Assumptions", chain: false, boxes: ["assumptions"] },
    { band: "External factors", chain: false, boxes: ["external"] }
  ];

  var STORE_KEY = "lens-widget-lens-projects-theory-of-change";
  var state = { org: "", boxes: {} };
  var completed = false;
  var busy = false;
  var lastResponseId = null;
  var areaEl = {};
  var statusEl = {};

  var chain = document.getElementById("chain");
  var orgInput = document.getElementById("org");
  var fbBtn = document.getElementById("get-feedback");
  var fbHint = document.getElementById("fb-hint");
  var fbOut = document.getElementById("fb-out");

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
      render();
      persist();
    });
    item.addEventListener("click", function (ev) { if (ev.target !== area) area.focus(); });
    areaEl[b.id] = area; statusEl[b.id] = st;
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
      var hide = b.label === stage.band || b.label === stage.question;
      items.appendChild(buildItem(b, hide));
    });
    sec.appendChild(items);
    chain.appendChild(sec);
  });

  function summary() {
    var lines = ["Project: " + (state.org.trim() || "(not named yet)")];
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
      try { localStorage.setItem(STORE_KEY, JSON.stringify({ org: state.org, boxes: state.boxes })); } catch (e) {}
    }
  }

  function render() {
    BOXES.forEach(function (b) {
      var v = (state.boxes[b.id] || "").trim();
      var area = areaEl[b.id];
      if (area.value !== (state.boxes[b.id] || "")) area.value = state.boxes[b.id] || "";
      statusEl[b.id].textContent = v ? "✓ filled" : "";
    });
    var ready = !!state.org.trim() && filledCount() > 0;
    if (!busy) fbBtn.disabled = !ready || !window.Lens;
    if (busy) {
      fbHint.textContent = "";
    } else if (!window.Lens) {
      fbHint.textContent = "Feedback needs the Lens lesson page; it is not available in this preview.";
    } else if (!ready) {
      fbHint.textContent = "Name your project and fill at least one box, then ask for feedback.";
    } else if (filledCount() < BOXES.length) {
      fbHint.textContent = "You can ask now, or fill the remaining boxes first: " + filledCount() + " of " + BOXES.length + " are filled.";
    } else {
      fbHint.textContent = "";
    }
  }

  orgInput.addEventListener("input", function () { state.org = orgInput.value; render(); persist(); });

  function fbClear() { while (fbOut.firstChild) fbOut.removeChild(fbOut.firstChild); }
  function fbLine(text) { var n = document.createElement("p"); n.textContent = text; fbOut.appendChild(n); }
  function fbDone(label) {
    busy = false;
    fbBtn.classList.remove("is-busy");
    fbBtn.textContent = label;
    render();
  }

  fbBtn.addEventListener("click", function () {
    if (busy || !window.Lens || !Lens.submit) return;
    busy = true;
    fbBtn.disabled = true;
    fbBtn.classList.add("is-busy");
    fbBtn.textContent = "Reading your chain...";
    fbHint.textContent = "";
    fbOut.hidden = false;
    fbClear();
    fbLine("Sent. Waiting for the read of your theory of change.");
    var atSend = filledCount();
    Lens.submit({
      item: "canvas",
      question: "Build a theory of change for your own Lens Projects project: what you need, what you will make, who you will reach, outcomes by the end of the course, within a year and long-term, assumptions (with the riskiest marked) and external factors.",
      answer: summary(),
      assessmentInstructions: "Practice score only; the learner is not shown it. 100 when every box names something concrete and checkable (a real resource, thing made, audience or observable change, not a restatement of the box label) and each output plausibly causes the next outcome. Take about 12 off per box that is vague or missing, and up to 20 off when the chain has a causal gap the assumptions do not cover.",
      feedbackInstructions: "Read the whole chain as one argument and comment on four things, in this order. First, anything unclear: a box a reader could not act on or picture. Second, the links between stages: name the one place where the step from one stage to the next is missing or not credible, and say what would have to be true for it to hold. Third, outputs written as outcomes: flag any box that names a thing made where a change belongs. Fourth, assumptions left implicit: name a belief the chain depends on that is not in the Assumptions box. Be specific about their words. Do not rewrite their boxes for them: the course rule is to use AI as a tool, not a decision-maker. Do not mention any score."
    }).then(function (result) {
      lastResponseId = result.responseId;
      if (Lens.requestFeedback && lastResponseId != null) {
        Lens.requestFeedback(lastResponseId, "Can you give me feedback on my theory of change?");
      }
      fbClear();
      fbLine("Your feedback is being written in the tutor conversation beside this page: what is unclear, the weakest link between two stages, any output written as an outcome, and the assumptions you have left implicit.");
      if (atSend < BOXES.length) {
        fbLine("You asked with " + atSend + " of " + BOXES.length + " boxes filled, so the read only covers what was there. Fill the rest and ask again.");
      }
      fbDone("Get feedback again");
    }, function () {
      fbClear();
      fbLine("Could not reach the tutor just now. Your entries are saved; try again in a moment.");
      fbDone("Get feedback");
    });
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
    render();
    if (!state.org.trim()) {
      try { orgInput.focus({ preventScroll: true }); } catch (e) {}
    }
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null, saved = null;
    try { raw = localStorage.getItem(STORE_KEY); } catch (e) {}
    if (raw) { try { saved = JSON.parse(raw); } catch (e) {} }
    hydrate(saved, null);
  }
</script>
</body>
</html>

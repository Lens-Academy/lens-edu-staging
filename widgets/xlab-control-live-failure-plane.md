---
id: '0f6bd8f1-7c3a-4a52-9e2c-5a1d4b8f9c30'
title: Live failures - attack latency against rate of damage
summary_for_tutor: An interactive plane from Kaufman and Lucassen's post. The horizontal axis is attack latency (left = a long grace period before harm begins, right = no grace period, harm is immediate) and the vertical axis is rate of damage (damage already dealt plus costs of recovery). Five threats from the post are plotted as points, `Code backdoor`, `API-key compromise`, `Credential compromise`, `Rogue internal deployment` (marked uncertain with a dashed ring) and `Weight exfiltration`. A shaded wedge in the top-right corner is the live-failure region, where an asynchronous monitor is least useful. The learner taps each point (or its button) to read the post's description of that threat and see whether it sits inside the wedge; the widget reports how many of the five they have opened and completes once all five are read. If the learner is stuck, ask them which axis position a code backdoor takes and why that makes an asynchronous monitor sufficient for it.
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<title>Live failures: latency and damage</title>
<!-- Ported from XLab Tracks, AI Control, "Blocking live failures with synchronous monitors"
     (LiveFailurePlaneDemo). Rewritten as vanilla HTML/JS in the Lens look. -->
<style>
  :root {
    --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a;
    --border: #e8e5df; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif;
    --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .card { border: 1px solid var(--border); border-radius: 8px; background: var(--bg); overflow: hidden; }
  .head { display: flex; align-items: center; justify-content: space-between; gap: 12px;
          padding: 12px 16px; border-bottom: 1px solid var(--border); background: var(--page); }
  .head h2 { font-family: var(--font-heading); font-weight: 600; font-size: 15px; margin: 0; }
  .body { padding: 16px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px;
           background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--page); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button[aria-pressed="true"] { border-color: var(--accent); color: var(--accent);
                                box-shadow: inset 0 0 0 1px var(--accent); font-weight: 600; }
  .reset { font-size: 12px; padding: 4px 10px; color: var(--muted); }
  .plane { overflow-x: auto; }
  .plane svg { display: block; width: 100%; min-width: 460px; }
  .chips { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 14px; }
  .chips button { font-size: 12.5px; }
  .chips .seen::after { content: " \2713"; color: var(--accent); }
  .panel { margin-top: 14px; border: 1px solid var(--border); border-radius: 8px;
           background: var(--page); padding: 12px 14px; min-height: 116px; }
  .panel h3 { font-family: var(--font-heading); font-weight: 600; font-size: 14px; margin: 0 0 4px; }
  .panel p { margin: 0; color: var(--muted); }
  .panel .verdict { margin-top: 8px; font-size: 12.5px; color: var(--text); }
  .progress { margin-top: 10px; font-size: 12px; color: var(--muted); }
  svg text { font-family: var(--font-ui); }
  .pt-hit { fill: transparent; cursor: pointer; }
  .pt-dot { fill: #fff; stroke: var(--accent); stroke-width: 1.75; transition: all .18s; cursor: pointer; }
  .pt-dot.on { fill: var(--accent); stroke: var(--accent); stroke-opacity: .35; stroke-width: 5; }
  .pt-label { font-size: 10px; fill: var(--muted); transition: fill .18s; cursor: pointer; }
  .pt-label.on { fill: var(--text); font-weight: 600; }
  .axis { stroke: var(--muted); stroke-width: 1.5; }
  .axis-name { font-size: 11px; font-weight: 500; fill: var(--text); }
  .axis-note { font-size: 9px; fill: var(--muted); }
  .zone { fill: rgba(184,112,24,.14); stroke: var(--accent); stroke-width: 1.25; stroke-dasharray: 5 4; }
  .zone-label { font-size: 11px; font-weight: 700; fill: var(--accent-hover); }
  @media (max-width: 420px) { body { padding: 8px; } .body { padding: 12px; } }
</style>
</head>
<body>
<div class="card">
  <div class="head">
    <h2>Live failures: latency and damage</h2>
    <button type="button" class="reset" id="reset">Reset</button>
  </div>
  <div class="body">
    <div class="plane">
      <svg id="plane" viewBox="0 0 560 330" role="img"
           aria-label="A plane of attack latency against rate of damage. The post's example threats are plotted as points and the live-failure region, short latency and high damage, is shaded in the top right corner.">
        <defs>
          <marker id="lfp-axis" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
            <path d="M0,0 L8,4 L0,8 z" fill="#5a5a5a"></path>
          </marker>
        </defs>
        <g id="layer"></g>
      </svg>
    </div>
    <div class="chips" id="chips"></div>
    <div class="panel" id="panel" aria-live="polite"></div>
    <p class="progress" id="progress"></p>
  </div>
</div>
<script>
(function () {
  "use strict";

  var POINTS = [
    { id: "backdoor", label: "Code backdoor", x: 0.14, y: 0.55, live: false,
      caption: "Code backdooring has attack latency, a grace period between the attack and any harm (time-to-impact, in cybersecurity terms). If the backdoor is detected before being exploited, an asynchronous monitor was exactly as effective as a synchronous one." },
    { id: "api-key", label: "API-key compromise", x: 0.62, y: 0.30, live: false,
      caption: "API-key compromise leads to a constant bleed of lost money and compute. The damage already dealt cannot be reversed when detected, but the bleed can be stopped equally easily at any time by disabling the key." },
    { id: "credentials", label: "Credential compromise", x: 0.48, y: 0.55, live: false,
      caption: "Access-credential compromise might cause no direct harm by the time it is detected, but the longer it persists, the more widespread and costly the cleanup. The damage accumulates as costs of recovery." },
    { id: "rogue-internal", label: "Rogue internal deployment", x: 0.72, y: 0.76, live: true, uncertain: true, labelBelow: true,
      caption: "Rogue internal deployments involving privilege escalation and compromise of monitoring systems might quickly become highly damaging or extremely costly to recover from: they give the misaligned AI increased affordances to cause further cascading failures. The post flags real uncertainty about how hard recovery would be." },
    { id: "weight-exfil", label: "Weight exfiltration", x: 0.88, y: 0.88, live: true, labelBelow: true,
      caption: "The classic live failure. It might be possible to exfiltrate weights in a short window of time, and once they are out there is no way to get them back. Leaking sensitive source code or algorithmic secrets to the internet is a close cousin." }
  ];

  var INTRO = {
    title: "Live failures",
    text: "Threats with low attack latency and a very high rate of damage are live failures: still very damaging even if detected shortly after they occur. Asynchronous monitors are least effective against them, and this is where blocking synchronous monitors matter most. Tap a point to read the post's description of each example."
  };

  var NS = "http://www.w3.org/2000/svg";
  var layer = document.getElementById("plane").querySelector("#layer");
  var chips = document.getElementById("chips");
  var panel = document.getElementById("panel");
  var progress = document.getElementById("progress");

  var selected = null;
  var seen = {};
  var completed = false;

  function px(v) { return 58 + 478 * v; }
  function py(v) { return 18 + (1 - v) * 252; }

  function el(name, attrs, text) {
    var n = document.createElementNS(NS, name);
    for (var k in attrs) { if (attrs[k] !== undefined && attrs[k] !== null) n.setAttribute(k, String(attrs[k])); }
    if (text !== undefined) n.appendChild(document.createTextNode(text));
    return n;
  }

  function drawStatic() {
    var zone = el("path", {
      d: "M " + px(0.55) + " " + py(1) + " Q " + px(0.62) + " " + py(0.62) + " " + px(1) + " " + py(0.52) +
         " L " + px(1) + " " + py(1) + " Z",
      "class": "zone"
    });
    layer.appendChild(zone);
    layer.appendChild(el("text", { x: px(0.57), y: py(0.955), "class": "zone-label" }, "Live failures"));

    layer.appendChild(el("line", { x1: 48, y1: 270, x2: 48, y2: 16, "class": "axis", "marker-end": "url(#lfp-axis)" }));
    layer.appendChild(el("line", { x1: 48, y1: 280, x2: 544, y2: 280, "class": "axis", "marker-end": "url(#lfp-axis)" }));

    layer.appendChild(el("text", { x: 20, y: 144, transform: "rotate(-90 20 144)", "text-anchor": "middle", "class": "axis-name" }, "Rate of damage"));
    layer.appendChild(el("text", { x: 33, y: 144, transform: "rotate(-90 33 144)", "text-anchor": "middle", "class": "axis-note" }, "damage dealt · costs of recovery"));
    layer.appendChild(el("text", { x: 297, y: 316, "text-anchor": "middle", "class": "axis-name" }, "Attack latency"));
    layer.appendChild(el("text", { x: 58, y: 328, "class": "axis-note" }, "long grace period"));
    layer.appendChild(el("text", { x: 536, y: 328, "text-anchor": "end", "class": "axis-note" }, "none, harm is immediate"));
  }

  var dots = {}, labels = {}, chipEls = {};

  function drawPoints() {
    POINTS.forEach(function (p) {
      var g = el("g", {});
      var hit = el("circle", { cx: px(p.x), cy: py(p.y), r: 14, "class": "pt-hit" });
      var dot = el("circle", { cx: px(p.x), cy: py(p.y), r: 4.5, "class": "pt-dot",
                               "stroke-dasharray": p.uncertain ? "2 2" : null });
      var lab = el("text", { x: px(p.x), y: py(p.y) + (p.labelBelow ? 21 : -11), "text-anchor": "middle", "class": "pt-label" },
                   p.label + (p.uncertain ? " (?)" : ""));
      g.appendChild(hit); g.appendChild(dot); g.appendChild(lab);
      g.addEventListener("click", function () { select(p.id === selected ? null : p.id); });
      layer.appendChild(g);
      dots[p.id] = dot; labels[p.id] = lab;
    });
  }

  function drawChips() {
    POINTS.forEach(function (p) {
      var b = document.createElement("button");
      b.type = "button";
      b.textContent = p.label + (p.uncertain ? " (?)" : "");
      b.setAttribute("aria-pressed", "false");
      b.addEventListener("click", function () { select(p.id === selected ? null : p.id); });
      chips.appendChild(b);
      chipEls[p.id] = b;
    });
  }

  function find(id) {
    for (var i = 0; i < POINTS.length; i++) { if (POINTS[i].id === id) return POINTS[i]; }
    return null;
  }

  function render() {
    POINTS.forEach(function (p) {
      var on = p.id === selected;
      dots[p.id].classList.toggle("on", on);
      dots[p.id].setAttribute("r", on ? 6 : 4.5);
      labels[p.id].classList.toggle("on", on);
      chipEls[p.id].setAttribute("aria-pressed", on ? "true" : "false");
      chipEls[p.id].classList.toggle("seen", !!seen[p.id]);
    });

    panel.textContent = "";
    var p = find(selected);
    var h = document.createElement("h3");
    var body = document.createElement("p");
    h.textContent = p ? p.label + (p.uncertain ? " (?)" : "") : INTRO.title;
    body.textContent = p ? p.caption : INTRO.text;
    panel.appendChild(h);
    panel.appendChild(body);
    if (p) {
      var v = document.createElement("p");
      v.className = "verdict";
      v.textContent = p.live
        ? (p.uncertain
            ? "Inside the live-failure region, with a question mark: the post is not sure how hard recovery would be."
            : "Inside the live-failure region. A blocking synchronous monitor is what helps here.")
        : "Outside the live-failure region. An asynchronous monitor still has time to work.";
      panel.appendChild(v);
    }

    var n = Object.keys(seen).length;
    progress.textContent = n === POINTS.length
      ? "All five threats read."
      : "Read " + n + " of " + POINTS.length + " threats.";
  }

  function summary() {
    var order = POINTS.filter(function (p) { return seen[p.id]; }).map(function (p) { return p.label; });
    var cur = find(selected);
    return "Live-failure plane widget. The learner has opened " + order.length + " of " + POINTS.length +
      " threats" + (order.length ? " (" + order.join(", ") + ")" : "") + ". " +
      (cur ? "Currently showing " + cur.label + ", which sits " + (cur.live ? "inside" : "outside") +
             " the live-failure region." : "No threat is currently selected.") +
      " The two threats the post places inside the region are weight exfiltration and, with a stated uncertainty, rogue internal deployment.";
  }

  function save() {
    if (!window.Lens) return;
    Lens.saveState({ selected: selected, seen: Object.keys(seen) }, summary());
    if (!completed && Object.keys(seen).length === POINTS.length) {
      completed = true;
      if (Lens.complete) Lens.complete();
    }
  }

  function select(id) {
    selected = id;
    if (id) seen[id] = true;
    render();
    save();
  }

  drawStatic();
  drawPoints();
  drawChips();
  render();

  document.getElementById("reset").addEventListener("click", function () {
    selected = null;
    render();
    save();
  });

  if (window.Lens && Lens.onState) {
    Lens.onState(function (state, meta) {
      if (state) {
        selected = state.selected || null;
        seen = {};
        (state.seen || []).forEach(function (k) { seen[k] = true; });
      }
      if (meta && meta.completed) completed = true;
      render();
    });
  }
})();
</script>
</body>
</html>

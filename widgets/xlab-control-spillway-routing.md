---
id: 'bd103397-394a-4ae8-aa73-c8286a8d8384'
title: Spillway routing
summary_for_tutor: "A four-step diagram of where reward-hacking pressure goes. The learner steps through it with Back and Next (or the four step dots). Step 1: misspecified reward drives three dangerous generalizations (deceptive alignment, emergent misalignment, uncontrolled fitness-seeking). Step 2: a salient spillway motivation absorbs that pressure instead, and the three dangerous boxes dim. Step 3: in deployment, the unsatiated spillway motivation still drives behavior. Step 4: developers guarantee maximum score, the spillway goes indifferent, and the remaining plausibly-aligned motivations guide behavior. The widget marks itself complete once the learner has viewed all four steps. It grades nothing; if the learner wants to discuss it, ask what changes between step 2 and step 4 and why that change requires the motivation to be satiable."
height: auto
tags: []
---
<!doctype html>
<!-- Ported from XLab's SpillwayRoutingDemo on the AI Control track lesson
     "Fail safe(r) at alignment by channeling reward-hacking into a
     'spillway' motivation". Geometry and step captions are XLab's;
     styling is the Lens look. -->
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10;
  --danger: #b3261e; --aligned: #2f6b4f;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin-bottom: 8px; }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
.scroll { overflow-x: auto; overflow-y: hidden; }
svg { display: block; width: 100%; min-width: 640px; height: auto; }
.step { margin-top: 12px; min-height: 88px; }
.step h2 { font-family: var(--font-heading); font-weight: 600; font-size: 15px; margin: 0 0 4px; }
.step p { margin: 0; color: var(--muted); }
.bar { display: flex; align-items: center; justify-content: space-between; gap: 12px; margin-top: 14px; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 12px; cursor: pointer; }
button:hover:not(:disabled) { background: #faf8f3; }
button:disabled { opacity: 0.45; cursor: default; }
.dots { display: flex; gap: 8px; }
.dot { width: 12px; height: 12px; padding: 0; border-radius: 50%; border: 1px solid var(--border); background: #efece6; }
.dot[aria-current="step"] { background: var(--accent); border-color: var(--accent-hover); }
.dot.seen { border-color: var(--muted); }
.reset { border: none; background: none; color: var(--muted); text-decoration: underline; padding: 4px 0; margin-top: 6px; font-size: 13px; }
.reset:hover { color: var(--text); background: none; }
.g { transition: opacity 300ms ease; }
@media (prefers-reduced-motion: reduce) { .g { transition: none; } }
.lbl { font-size: 11px; font-weight: 500; fill: var(--text); }
.small { font-size: 10px; fill: var(--muted); }
@media (max-width: 420px) {
  body { padding: 12px; }
  .bar { flex-wrap: wrap; }
}
</style>
</head>
<body>
<div class="card">
  <div class="eyebrow">Where the reward-hacking pressure goes</div>
  <div class="scroll" id="scroll"></div>
  <div class="step"><h2 id="steplabel"></h2><p id="stepcaption"></p></div>
  <div class="bar">
    <button type="button" id="back">Back</button>
    <div class="dots" id="dots"></div>
    <button type="button" id="next">Next</button>
  </div>
  <button type="button" class="reset" id="reset">Reset to step 1</button>
</div>
<script>
(function () {
  var SVGNS = "http://www.w3.org/2000/svg";

  var STEPS = [
    {
      label: "Training: misspecified reward",
      caption: "RL is intended to help the model learn useful skills, but the reward signal is sometimes misspecified, and the resulting training pressure causes harmful generalization."
    },
    {
      label: "Training: channel into the spillway",
      caption: "Developers could similarly try to channel unwanted RL pressures into a spillway motivation, preventing them from reinforcing more dangerous generalizations (like deceptive alignment, emergent misalignment, or uncontrolled varieties of fitness-seeking)."
    },
    {
      label: "Deployment: before satiation",
      caption: "At inference time, developers can try to neutralize the spillway motivation by satisfying it."
    },
    {
      label: "Deployment: satiated",
      caption: "If the user honestly tells the AI that it will get maximum score no matter what, then the spillway motivation should be indifferent to the AI's actions, and no longer influences behavior. Even if the model is mostly motivated by the spillway, it would now be guided by the remaining motivations, which are plausibly aligned."
    }
  ];

  function el(tag, attrs) {
    var e = document.createElementNS(SVGNS, tag);
    for (var k in attrs) { if (attrs.hasOwnProperty(k)) e.setAttribute(k, attrs[k]); }
    return e;
  }
  function textNode(x, y, s, cls) {
    var t = el("text", { x: x, y: y, "text-anchor": "middle", "class": cls || "lbl" });
    t.textContent = s;
    return t;
  }
  function group(cls) { return el("g", { "class": "g " + (cls || "") }); }

  function makeBox(x, y, w, h, lines, tone) {
    var g = group();
    var stroke = "var(--border)", fill = "#ffffff";
    if (tone === "danger") { stroke = "var(--danger)"; fill = "rgba(179, 38, 30, 0.08)"; }
    if (tone === "accent") { stroke = "var(--accent)"; fill = "rgba(184, 112, 24, 0.13)"; }
    if (tone === "aligned") { stroke = "var(--aligned)"; fill = "rgba(47, 107, 79, 0.10)"; }
    g.appendChild(el("rect", {
      x: x, y: y, width: w, height: h, rx: 8,
      fill: fill, stroke: stroke, "stroke-width": 1.5
    }));
    for (var i = 0; i < lines.length; i++) {
      g.appendChild(textNode(x + w / 2, y + h / 2 + (i - (lines.length - 1) / 2) * 14 + 4, lines[i]));
    }
    return g;
  }
  function line(x1, y1, x2, y2, stroke, marker, width) {
    return el("line", {
      x1: x1, y1: y1, x2: x2, y2: y2,
      stroke: stroke, "stroke-width": width || 1.5, "marker-end": "url(#" + marker + ")"
    });
  }
  function marker(id, color) {
    var m = el("marker", {
      id: id, viewBox: "0 0 8 8", refX: 7, refY: 4,
      markerWidth: 6, markerHeight: 6, orient: "auto-start-reverse"
    });
    m.appendChild(el("path", { d: "M0 0 L8 4 L0 8 Z", fill: color }));
    return m;
  }

  var svg = el("svg", {
    viewBox: "0 0 720 300",
    role: "img",
    "aria-label": "Spillway routing diagram"
  });
  var defs = el("defs");
  defs.appendChild(marker("spw-danger", "var(--danger)"));
  defs.appendChild(marker("spw-accent", "var(--accent)"));
  defs.appendChild(marker("spw-aligned", "var(--aligned)"));
  svg.appendChild(defs);

  // Source of the pressure: always fully visible.
  svg.appendChild(makeBox(20, 110, 160, 56, ["reward hacking", "(misspecified reward)"]));

  // The three dangerous generalizations, and the arrows into them.
  var dangerArrows = group();
  dangerArrows.appendChild(line(180, 122, 288, 52, "var(--danger)", "spw-danger"));
  dangerArrows.appendChild(line(180, 132, 288, 108, "var(--danger)", "spw-danger"));
  dangerArrows.appendChild(line(180, 142, 288, 164, "var(--danger)", "spw-danger"));
  svg.appendChild(dangerArrows);

  var dangerBoxes = [
    makeBox(292, 26, 190, 40, ["deceptive alignment"], "danger"),
    makeBox(292, 86, 190, 40, ["emergent misalignment"], "danger"),
    makeBox(292, 146, 190, 40, ["uncontrolled fitness-seeking"], "danger")
  ];
  dangerBoxes.forEach(function (b) { svg.appendChild(b); });

  // The spillway channel.
  var spillwayArrow = group();
  spillwayArrow.appendChild(el("path", {
    d: "M 100 166 C 100 220, 180 244, 288 248",
    fill: "none", stroke: "var(--accent)", "stroke-width": 2,
    "marker-end": "url(#spw-accent)"
  }));
  svg.appendChild(spillwayArrow);

  var spillwayBox = makeBox(292, 224, 190, 48, ["spillway motivation"], "accent");
  svg.appendChild(spillwayBox);

  // Unsatiated: the spillway drives behavior.
  var drives = group();
  drives.appendChild(line(482, 248, 560, 248, "var(--accent)", "spw-accent", 2));
  drives.appendChild(textNode(640, 252, "drives behavior"));
  svg.appendChild(drives);

  // Satiated: the spillway goes indifferent, aligned motivations take over.
  var satiated = group();
  satiated.appendChild(textNode(387, 292, "“maximum score no matter what” → indifferent", "small"));
  satiated.appendChild(line(482, 110, 560, 110, "var(--aligned)", "spw-aligned", 2));
  satiated.appendChild(textNode(643, 106, "guides behavior"));
  svg.appendChild(satiated);

  var alignedBox = makeBox(510, 26, 190, 48, ["remaining motivations", "(plausibly aligned)"], "aligned");
  svg.appendChild(alignedBox);

  document.getElementById("scroll").appendChild(svg);

  // Controls.
  var backBtn = document.getElementById("back");
  var nextBtn = document.getElementById("next");
  var resetBtn = document.getElementById("reset");
  var dotsBox = document.getElementById("dots");
  var labelEl = document.getElementById("steplabel");
  var captionEl = document.getElementById("stepcaption");

  var dots = STEPS.map(function (s, i) {
    var b = document.createElement("button");
    b.type = "button";
    b.className = "dot";
    b.setAttribute("aria-label", "Step " + (i + 1) + ": " + s.label);
    b.addEventListener("click", function () { go(i); });
    dotsBox.appendChild(b);
    return b;
  });

  var step = 0;
  var seen = [true, false, false, false];

  function summary() {
    var n = seen.filter(Boolean).length;
    return "Spillway routing diagram. The learner is on step " + (step + 1) + " of 4, \""
      + STEPS[step].label + "\", and has viewed " + n + " of the 4 steps"
      + (n === 4 ? ", so they have seen the whole sequence" : "") + ".";
  }

  function save() {
    if (window.Lens) {
      Lens.saveState({ step: step, seen: seen }, summary());
      if (seen.every(Boolean)) Lens.complete();
    }
  }

  function render() {
    var atStart = step === 0;
    var channelled = step >= 1;
    var isSatiated = step === 3;

    dangerArrows.style.opacity = atStart ? 1 : 0.25;
    dangerBoxes.forEach(function (b) { b.style.opacity = atStart ? 1 : 0.3; });
    spillwayArrow.style.opacity = channelled ? 1 : 0;
    spillwayBox.style.opacity = (!channelled || isSatiated) ? 0.3 : 1;
    drives.style.opacity = (step >= 2 && !isSatiated) ? 1 : 0;
    satiated.style.opacity = isSatiated ? 1 : 0;
    alignedBox.style.opacity = isSatiated ? 1 : 0.3;

    labelEl.textContent = (step + 1) + ". " + STEPS[step].label;
    captionEl.textContent = STEPS[step].caption;

    dots.forEach(function (d, i) {
      if (i === step) { d.setAttribute("aria-current", "step"); }
      else { d.removeAttribute("aria-current"); }
      d.classList.toggle("seen", seen[i]);
    });
    backBtn.disabled = step === 0;
    nextBtn.disabled = step === STEPS.length - 1;
  }

  function go(i) {
    step = Math.max(0, Math.min(STEPS.length - 1, i));
    seen[step] = true;
    render();
    save();
  }

  backBtn.addEventListener("click", function () { go(step - 1); });
  nextBtn.addEventListener("click", function () { go(step + 1); });
  resetBtn.addEventListener("click", function () { go(0); });

  render();

  if (window.Lens) {
    Lens.onState(function (state) {
      if (state && typeof state.step === "number") {
        if (Array.isArray(state.seen) && state.seen.length === STEPS.length) seen = state.seen;
        step = Math.max(0, Math.min(STEPS.length - 1, state.step));
        seen[step] = true;
        render();
      }
    });
  }
})();
</script>
</body>
</html>

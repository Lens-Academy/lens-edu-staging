---
id: '49d33e65-05de-403d-a497-d0426c530115'
title: At least one cooperating AI
summary_for_tutor: "An interactive chart for Finnveden's 'There are multiple AIs' point, placed right after the excerpt that makes it. It plots the probability that at least one AI cooperates, 1 - (1 - p)^n, against the per-AI cooperation probability p, for n independent AI 'draws'. Three sliders: independent AI draws n (1 to 15, default 3), baseline per-AI probability (0 to 100 percent, default 20), and the per-AI shift from promises (0 to 30 percentage points, default 15). Two markers on the curve show the baseline and the shifted probability, and a line underneath reads out both values and the gain. Two preset buttons reproduce the text's worked examples: 10 draws at 50 percent (already above 99.9 percent, so shifting each draw to 65 percent adds almost nothing) and 3 draws at 20 percent (about 49 percent rising to about 73 percent, a gain of about 24 points, more than the 15-point per-AI shift). The lesson: the value of shifting each AI's cooperation probability depends on the baseline; when some cooperator is already near-certain the shift is nearly worthless, and when cooperation is genuinely uncertain the same shift is worth more than its face value. The widget completes once the learner has seen both kinds of case: one where the gain is under 1 point despite a nonzero shift, and one where the gain is at least as large as the per-AI shift. Ask which of the two worlds the learner thinks we are in, and what that implies for the 2x discount in the BOTEC above."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --faint: #9a958c; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--bg); }
.lede { color: var(--muted); margin: 4px 0 12px; }
.legend { display: flex; flex-wrap: wrap; gap: 14px; margin-bottom: 6px; font-size: 12px; color: var(--muted); }
.dotkey { display: inline-block; width: 9px; height: 9px; border-radius: 50%; margin-right: 6px; vertical-align: 0; }
.chart { width: 100%; height: auto; display: block; }
.controls { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px 24px; margin-top: 12px; }
@media (max-width: 560px) { .controls { grid-template-columns: 1fr; } }
.ctrl label { display: flex; align-items: baseline; justify-content: space-between; gap: 10px; }
.ctrl .name { color: var(--muted); }
.ctrl .val { font-variant-numeric: tabular-nums; font-weight: 500; white-space: nowrap; }
input[type=range] { width: 100%; accent-color: var(--accent); margin: 4px 0 0; }
.presets { display: flex; align-items: center; gap: 8px; flex-wrap: wrap; margin-top: 14px; }
.presets .k { color: var(--muted); font-size: 12px; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 6px 12px; cursor: pointer; font-size: 13px; }
button:hover { background: var(--page); }
.verdict { margin: 14px 0 0; padding: 12px 14px; border: 1px solid var(--border); border-radius: 8px; background: var(--page); min-height: 62px; }
.verdict strong { font-weight: 600; font-variant-numeric: tabular-nums; }
.curve, .band, .mk { transition: all 300ms ease-out; }
@media (prefers-reduced-motion: reduce) { .curve, .band, .mk { transition: none; } }
</style>
</head>
<body>
<!-- Ported from XLab's "At least one cooperating AI" demo (coop-at-least-one) on the AI Control
     track (aisafetytracks.com; source github.com/XLabTracks/tracks,
     src/components/demos/coop-at-least-one-demo.tsx), rebuilt as vanilla HTML/JS in the Lens look.
     The curve, slider ranges, defaults and presets are XLab's, from Finnveden's two worked examples. -->
<div class="card">
  <p class="eyebrow">Figure</p>
  <h2>Probability that at least one AI cooperates</h2>
  <p class="lede">The curve is 1 &minus; (1 &minus; p)<sup>n</sup>. Move the baseline and the shift, or load the text's two examples.</p>

  <div class="legend">
    <span><span class="dotkey" style="background:var(--faint)"></span>Baseline</span>
    <span><span class="dotkey" style="background:var(--accent)"></span>After the per-AI shift</span>
  </div>

  <svg id="chart" class="chart" viewBox="0 0 560 300" role="img" aria-labelledby="chartTitle">
    <title id="chartTitle">Probability that at least one AI cooperates, as a function of the per-AI cooperation probability, with markers before and after a per-AI shift</title>
  </svg>

  <div class="controls" id="controls"></div>

  <div class="presets">
    <span class="k">Presets from the text:</span>
    <button type="button" id="p1">10 draws at 50%</button>
    <button type="button" id="p2">3 draws at 20%</button>
  </div>

  <p class="verdict" id="verdict" aria-live="polite"></p>
</div>

<script>
(function () {
  "use strict";

  var SVGNS = "http://www.w3.org/2000/svg";
  var W = 560, H = 300;
  var M = { left: 48, right: 16, top: 16, bottom: 40 };
  var PW = W - M.left - M.right, PH = H - M.top - M.bottom;

  var CONTROLS = [
    { key: "n", label: "Independent AI draws", min: 1, max: 15, step: 1, show: function (v) { return String(v); } },
    { key: "base", label: "Baseline per-AI probability", min: 0, max: 100, step: 1, show: function (v) { return v + "%"; } },
    { key: "shift", label: "Per-AI shift from promises", min: 0, max: 30, step: 1, show: function (v) { return "+" + v + "pp"; } }
  ];
  var s = { n: 3, base: 20, shift: 15 };
  var seenSaturated = false, seenAmplified = false, completed = false;

  function atLeastOne(p, n) { return 1 - Math.pow(1 - p, n); }
  function fmt(v) {
    var p = v * 100;
    if (p > 99.9) return ">99.9";
    return p < 10 ? p.toFixed(1) : String(Math.round(p));
  }
  function xPx(p) { return M.left + p * PW; }
  function yPx(y) { return M.top + PH - y * PH; }

  function el(name, attrs, text) {
    var n = document.createElementNS(SVGNS, name);
    for (var k in attrs) { if (attrs[k] !== undefined && attrs[k] !== null) n.setAttribute(k, String(attrs[k])); }
    if (text !== undefined) n.appendChild(document.createTextNode(String(text)));
    return n;
  }

  function model() {
    var p0 = s.base / 100;
    var p1 = Math.min((s.base + s.shift) / 100, 1);
    var y0 = atLeastOne(p0, s.n), y1 = atLeastOne(p1, s.n);
    return { p0: p0, p1: p1, y0: y0, y1: y1, gain: Math.max(y1 - y0, 0) };
  }

  function render(doSave) {
    var m = model();
    var svg = document.getElementById("chart");
    while (svg.childNodes.length > 1) svg.removeChild(svg.lastChild);

    // band between baseline and shifted per-AI probability
    svg.appendChild(el("rect", { "class": "band", x: xPx(m.p0), y: M.top, width: Math.max(xPx(m.p1) - xPx(m.p0), 1), height: PH, fill: "var(--accent)", "fill-opacity": 0.07 }));

    // axes
    svg.appendChild(el("line", { x1: M.left, y1: M.top + PH, x2: M.left + PW, y2: M.top + PH, stroke: "var(--border)", "stroke-width": 1 }));
    svg.appendChild(el("line", { x1: M.left, y1: M.top, x2: M.left, y2: M.top + PH, stroke: "var(--border)", "stroke-width": 1 }));
    [0, 25, 50, 75, 100].forEach(function (t) {
      svg.appendChild(el("text", { x: xPx(t / 100), y: H - 16, "text-anchor": "middle", fill: "var(--muted)", "font-size": 10 }, t + "%"));
      svg.appendChild(el("text", { x: M.left - 8, y: yPx(t / 100) + 3, "text-anchor": "end", fill: "var(--muted)", "font-size": 10 }, t + "%"));
    });
    svg.appendChild(el("text", { x: M.left + PW / 2, y: H - 2, "text-anchor": "middle", fill: "var(--muted)", "font-size": 11 }, "per-AI cooperation probability →"));
    svg.appendChild(el("text", { x: 14, y: M.top + PH / 2, "text-anchor": "middle", transform: "rotate(-90 14 " + (M.top + PH / 2) + ")", fill: "var(--muted)", "font-size": 11 }, "P(at least one cooperates) →"));

    // the 1 - (1 - p)^n curve
    var d = [];
    for (var i = 0; i <= 80; i++) {
      var p = i / 80;
      d.push((i === 0 ? "M " : "L ") + xPx(p).toFixed(1) + " " + yPx(atLeastOne(p, s.n)).toFixed(1));
    }
    svg.appendChild(el("path", { "class": "curve", d: d.join(" "), fill: "none", stroke: "var(--accent)", "stroke-width": 2 }));

    // baseline and shifted markers with guides
    [
      { p: m.p0, y: m.y0, color: "var(--faint)" },
      { p: m.p1, y: m.y1, color: "var(--accent)" }
    ].forEach(function (k) {
      var g = el("g", { "class": "mk" });
      g.appendChild(el("line", { x1: xPx(k.p), y1: yPx(k.y), x2: xPx(k.p), y2: M.top + PH, stroke: k.color, "stroke-opacity": 0.6, "stroke-width": 1, "stroke-dasharray": "4 3" }));
      g.appendChild(el("line", { x1: M.left, y1: yPx(k.y), x2: xPx(k.p), y2: yPx(k.y), stroke: k.color, "stroke-opacity": 0.6, "stroke-width": 1, "stroke-dasharray": "4 3" }));
      g.appendChild(el("circle", { cx: xPx(k.p), cy: yPx(k.y), r: 4.5, fill: k.color, stroke: "var(--bg)", "stroke-width": 1.5 }));
      svg.appendChild(g);
    });

    var v = document.getElementById("verdict");
    v.textContent = "";
    v.appendChild(document.createTextNode("P(at least one AI cooperates): "));
    var b0 = document.createElement("strong"); b0.textContent = fmt(m.y0) + "%"; v.appendChild(b0);
    v.appendChild(document.createTextNode(" at baseline, "));
    var b1 = document.createElement("strong"); b1.textContent = fmt(m.y1) + "%"; v.appendChild(b1);
    v.appendChild(document.createTextNode(" after the shift, a gain of "));
    var b2 = document.createElement("strong"); b2.textContent = fmt(m.gain) + " percentage points"; v.appendChild(b2);
    v.appendChild(document.createTextNode(". When the baseline already makes some cooperator near-certain, shifting each AI adds almost nothing; when cooperation is genuinely uncertain, the same per-AI shift is worth more than its face value."));

    CONTROLS.forEach(function (c) {
      document.getElementById("in-" + c.key).value = String(s[c.key]);
      document.getElementById("out-" + c.key).textContent = c.show(s[c.key]);
    });

    var shiftEff = m.p1 - m.p0;
    if (shiftEff > 0 && m.gain < 0.01) seenSaturated = true;
    if (shiftEff > 0 && m.gain >= shiftEff - 1e-9) seenAmplified = true;

    if (doSave) save(m);
  }

  var saveTimer = null;
  function save(m) {
    if (!window.Lens) return;
    if (seenSaturated && seenAmplified && !completed) {
      completed = true;
      if (window.Lens.complete) window.Lens.complete();
    }
    if (saveTimer) clearTimeout(saveTimer);
    saveTimer = setTimeout(function () {
      var summary = "At-least-one chart: " + s.n + " independent AI draws, baseline per-AI cooperation " + s.base +
        "%, shifted by +" + s.shift + "pp. P(at least one cooperates) goes from " + fmt(m.y0) + "% to " + fmt(m.y1) +
        "%, a gain of " + fmt(m.gain) + " points. " +
        (seenSaturated ? "Has seen a saturated case (shift adds almost nothing). " : "Has not yet seen a saturated case. ") +
        (seenAmplified ? "Has seen a case where the gain is at least the per-AI shift." : "Has not yet seen a case where the gain is at least the per-AI shift.");
      if (window.Lens.saveState) window.Lens.saveState({ v: 1, s: s, seenSaturated: seenSaturated, seenAmplified: seenAmplified }, summary);
    }, 400);
  }

  function buildControls() {
    var host = document.getElementById("controls");
    CONTROLS.forEach(function (c) {
      var wrap = document.createElement("div");
      wrap.className = "ctrl";
      var label = document.createElement("label");
      label.setAttribute("for", "in-" + c.key);
      var name = document.createElement("span");
      name.className = "name";
      name.textContent = c.label;
      var val = document.createElement("span");
      val.className = "val";
      val.id = "out-" + c.key;
      label.appendChild(name);
      label.appendChild(val);
      var input = document.createElement("input");
      input.type = "range";
      input.id = "in-" + c.key;
      input.min = String(c.min);
      input.max = String(c.max);
      input.step = String(c.step);
      input.value = String(s[c.key]);
      input.addEventListener("input", function () {
        s[c.key] = Number(input.value);
        render(true);
      });
      wrap.appendChild(label);
      wrap.appendChild(input);
      host.appendChild(wrap);
    });
  }

  function preset(n, base, shift) { s.n = n; s.base = base; s.shift = shift; render(true); }
  document.getElementById("p1").addEventListener("click", function () { preset(10, 50, 15); });
  document.getElementById("p2").addEventListener("click", function () { preset(3, 20, 15); });

  buildControls();

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state, meta) {
      if (state && state.s) {
        CONTROLS.forEach(function (c) {
          if (typeof state.s[c.key] === "number") s[c.key] = state.s[c.key];
        });
        seenSaturated = !!state.seenSaturated;
        seenAmplified = !!state.seenAmplified;
      }
      if (meta && meta.completed) completed = true;
      render(false);
    });
  }
  render(false);
})();
</script>
</body>
</html>

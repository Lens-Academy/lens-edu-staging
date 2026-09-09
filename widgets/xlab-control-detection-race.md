---
id: '8214fd06-43a4-4319-8040-e3413763c975'
title: 'The detection race: concentrated vs diffuse failures'
summary_for_tutor: 'An interactive model of the detection race. A schemer needs C bad actions to reach catastrophe, each bad action has an independent chance q of being noticed, and a decisive response fires at the K-th notice. Three sliders set C (1 to 100,000, log scale), q (0.01 percent to 50 percent, log scale) and K (1 to 20). The widget shows P(response before catastrophe) as a curve over C, expected bad actions before the response (K/q) as a curve over q, three read-outs (probability the response is in time, expected damage at response, regime name), and a sentence explaining the current regime. The three regimes are "Caught in time" (P at least 90 percent), "Detected, but too late" (P below 90 percent but expected damage at most 1,000,000 actions) and "Effectively never detected" (expected damage above 1,000,000 actions). Only the first two are reachable from the lever ranges, because the largest damage bill the levers allow is K/q = 20/0.0001 = 200,000 actions; the widget says so under the levers. The learner is asked to find both reachable regimes, and completion fires once they have. If a learner asks about it, note that the schemer''s pace has no slider: acting more slowly delays detection and catastrophe by the same factor, so the race depends only on C, q and K, and expected damage before the response is K/q regardless of how concentrated the threat is.'
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
  --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 0; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.card { border: 1px solid var(--border); border-radius: 8px; overflow: hidden; background: var(--bg); }
.head { border-bottom: 1px solid var(--border); background: var(--page); padding: 12px 16px; display: flex; gap: 12px; align-items: flex-start; justify-content: space-between; }
.head h2 { font-family: var(--font-heading); font-weight: 600; font-size: 15px; margin: 0; }
.head p { margin: 4px 0 0; font-size: 12px; color: var(--muted); }
.body { padding: 16px; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 6px 10px; cursor: pointer; font-size: 12px; }
button:hover { background: var(--page); }
.lever { margin-bottom: 12px; }
.lever label { display: flex; align-items: baseline; justify-content: space-between; gap: 10px; font-size: 13px; }
.lever .name { color: var(--muted); }
.lever .val { font-variant-numeric: tabular-nums; font-weight: 500; }
input[type=range] { width: 100%; accent-color: var(--accent); margin: 4px 0 0; }
.charts { display: flex; flex-direction: column; gap: 16px; margin-top: 18px; }
.chart { min-width: 0; flex: 1; }
.chart .cap { text-align: center; font-size: 12px; color: var(--muted); margin: 0 0 4px; }
.chart .now { text-align: center; font-size: 14px; font-weight: 600; font-variant-numeric: tabular-nums; margin: 4px 0 0; }
.stats { display: grid; grid-template-columns: 1fr; gap: 10px; border: 1px solid var(--border); border-radius: 8px; padding: 12px; margin-top: 18px; background: var(--page); text-align: center; }
.stats .k { font-size: 11px; color: var(--muted); margin: 0; }
.stats .v { font-size: 14px; font-weight: 600; margin: 2px 0 0; font-variant-numeric: tabular-nums; }
.detail { font-size: 12px; color: var(--muted); margin: 12px 0 0; }
.progress { font-size: 12px; margin: 12px 0 0; display: flex; flex-wrap: wrap; gap: 6px; align-items: center; }
.pill { border: 1px solid var(--border); border-radius: 999px; padding: 2px 9px; font-size: 11px; color: var(--muted); }
.pill.seen { border-color: var(--accent); color: var(--accent); }
.done { color: var(--accent); font-weight: 500; }
@media (min-width: 560px) {
  .charts { flex-direction: row; }
  .stats { grid-template-columns: repeat(3, 1fr); }
}
</style>
</head>
<body>
<!-- Ported from XLab Tracks, AI Control, "Notes on handling non-concentrated failures with AI control" (DetectionRaceDemo). Rewritten as vanilla HTML/JS in the Lens look. -->
<div class="card">
  <div class="head">
    <div>
      <h2>The detection race: concentrated vs diffuse failures</h2>
      <p>A schemer needs C bad actions for catastrophe; each has chance q of being noticed and a response fires at the K-th notice. Move the three levers to see who wins the race, the expected damage bill, and the three regimes from the post.</p>
    </div>
    <button type="button" id="reset">Reset</button>
  </div>
  <div class="body">
    <div class="lever">
      <label for="sC"><span class="name">Bad actions needed for catastrophe (C): concentrated to diffuse</span><span class="val" id="vC"></span></label>
      <input type="range" id="sC" min="0" max="500" step="1" value="300">
    </div>
    <div class="lever">
      <label for="sQ"><span class="name">Chance a bad action is noticed (q = audited x caught)</span><span class="val" id="vQ"></span></label>
      <input type="range" id="sQ" min="-400" max="-30.103" step="1" value="-200">
    </div>
    <div class="lever">
      <label for="sK"><span class="name">Noticed incidents before a decisive response (K)</span><span class="val" id="vK"></span></label>
      <input type="range" id="sK" min="1" max="20" step="1" value="3">
    </div>

    <div class="charts">
      <div class="chart">
        <p class="cap">P(response before catastrophe), by C</p>
        <svg id="chartA" viewBox="0 0 320 180" style="width:100%" role="img" aria-label="Probability the response arrives before catastrophe, plotted against the number of bad actions needed for catastrophe"></svg>
        <p class="now" id="nowA"></p>
      </div>
      <div class="chart">
        <p class="cap">Expected bad actions before response, by q</p>
        <svg id="chartB" viewBox="0 0 320 180" style="width:100%" role="img" aria-label="Expected number of bad actions before the response, plotted against the chance a bad action is noticed"></svg>
        <p class="now" id="nowB"></p>
      </div>
    </div>

    <div class="stats">
      <div><p class="k">Response in time</p><p class="v" id="statP"></p></div>
      <div><p class="k">Expected damage at response</p><p class="v" id="statD"></p></div>
      <div><p class="k">Regime</p><p class="v" id="statR"></p></div>
    </div>

    <p class="detail" id="detail"></p>
    <p class="progress" id="progress"></p>
    <p class="detail">The model has a third regime, "Effectively never detected", for expected damage above 1,000,000 actions. These levers cannot reach it: the largest bill they allow is K/q = 20 / 0.0001 = 200,000 actions.</p>
  </div>
</div>

<script>
(function () {
  var QMAX = Math.log10(0.5);
  var REGIMES = {
    "caught-in-time": {
      label: "Caught in time",
      detail: "The response reliably fires before the catastrophe threshold: the diffuse regime, where asynchronous review and training have time to work."
    },
    "detected-too-late": {
      label: "Detected, but too late",
      detail: "Enough signal exists to detect the behavior eventually, but catastrophe likely arrives first: stakes as a quantitative matter."
    },
    "effectively-never": {
      label: "Effectively never detected",
      detail: "So little signal per incident that the deployment ends before the evidence threshold is reached: the clearly low-stakes failure the post describes."
    }
  };
  // Only two of the three regimes are reachable from these lever ranges: the widest
  // damage bill the levers allow is K/q = 20 / 0.0001 = 200,000 actions, below the
  // 1,000,000 the third regime needs. The third is kept in the classifier and named
  // in the note under the levers.
  var ORDER = ["caught-in-time", "detected-too-late"];
  var TAIL = "The schemer's pace has no slider: acting more slowly delays detection and catastrophe by the same factor, so the race outcome depends only on C, q, and K. Expected damage before the response is K/q, independent of the threat's concentration.";
  var PLOT_W = 272, PLOT_H = 146, X0 = 34, Y0 = 10;
  var SVGNS = "http://www.w3.org/2000/svg";

  var seen = {};
  var completed = false;

  function pResponse(C, q, K) {
    var n = Math.floor(C) - 1, k = Math.floor(K);
    if (k <= 0) return 1;
    if (n < k || q <= 0) return 0;
    if (q >= 1) return 1;
    var sum = 0, lc = 0;
    for (var e = 0; e < k; e++) {
      if (e > 0) lc += Math.log(n - e + 1) - Math.log(e);
      sum += Math.exp(lc + e * Math.log(q) + (n - e) * Math.log(1 - q));
    }
    return Math.min(1, Math.max(0, 1 - sum));
  }

  function damage(q, K) { return q <= 0 ? Infinity : K / q; }

  function fmt(v) {
    if (!isFinite(v)) return "∞";
    if (v >= 1e6) return (v / 1e6).toFixed(1) + "M";
    if (v >= 1e3) return (v / 1e3).toFixed(v >= 1e4 ? 0 : 1) + "k";
    if (v >= 100) return v.toFixed(0);
    return v.toFixed(1);
  }

  function el(name, attrs) {
    var node = document.createElementNS(SVGNS, name);
    for (var key in attrs) node.setAttribute(key, attrs[key]);
    return node;
  }

  function drawChart(svg, opts) {
    while (svg.firstChild) svg.removeChild(svg.firstChild);
    var sx = function (lx) { return X0 + (lx - opts.minLog) / (opts.maxLog - opts.minLog) * PLOT_W; };
    var sy = function (v) { return Y0 + PLOT_H - Math.min(v, opts.maxValue) / opts.maxValue * PLOT_H; };
    [0, 0.25, 0.5, 0.75, 1].forEach(function (f) {
      svg.appendChild(el("line", {
        x1: X0, x2: X0 + PLOT_W, y1: Y0 + PLOT_H * (1 - f), y2: Y0 + PLOT_H * (1 - f),
        stroke: "#e8e5df", "stroke-width": 1
      }));
    });
    var px = sx(opts.currentLog);
    svg.appendChild(el("line", { x1: px, x2: px, y1: Y0, y2: Y0 + PLOT_H, stroke: "#5a5a5a", "stroke-width": 1, "stroke-opacity": 0.4 }));
    var d = opts.points.map(function (p, i) {
      return (i === 0 ? "M " : "L ") + sx(p.logX).toFixed(2) + " " + sy(p.value).toFixed(2);
    }).join(" ");
    svg.appendChild(el("path", { d: d, fill: "none", stroke: "#b87018", "stroke-width": 2, "stroke-linejoin": "round", "stroke-linecap": "round" }));
    svg.appendChild(el("circle", { cx: px, cy: sy(opts.currentValue), r: 5, fill: "#b87018", stroke: "#ffffff", "stroke-width": 2 }));
    var texts = [
      { x: 30, y: 18, anchor: "end", t: opts.formatValue(opts.maxValue) },
      { x: 30, y: Y0 + PLOT_H, anchor: "end", t: opts.formatValue(0) },
      { x: X0, y: 174, anchor: "start", t: opts.formatXTick(opts.minLog) },
      { x: X0 + PLOT_W, y: 174, anchor: "end", t: opts.formatXTick(opts.maxLog) }
    ];
    texts.forEach(function (spec) {
      var node = el("text", { x: spec.x, y: spec.y, "font-size": 9, fill: "#5a5a5a", "text-anchor": spec.anchor });
      node.textContent = spec.t;
      svg.appendChild(node);
    });
  }

  var sC = document.getElementById("sC");
  var sQ = document.getElementById("sQ");
  var sK = document.getElementById("sK");

  function render(save) {
    var logC = Number(sC.value) / 100;
    var logQ = Number(sQ.value) / 100;
    var K = Number(sK.value);
    var C = Math.round(Math.pow(10, logC));
    var q = Math.pow(10, logQ);

    var p = pResponse(C, q, K);
    var dmg = damage(q, K);
    var key = p >= 0.9 ? "caught-in-time" : (dmg <= 1e6 ? "detected-too-late" : "effectively-never");
    var regime = REGIMES[key];

    document.getElementById("vC").textContent = fmt(C);
    document.getElementById("vQ").textContent = (100 * q).toPrecision(2) + "%";
    document.getElementById("vK").textContent = String(K);

    var ptsA = [], ptsB = [];
    for (var i = 0; i <= 120; i++) {
      var lx = 5 * i / 120;
      ptsA.push({ logX: lx, value: pResponse(Math.round(Math.pow(10, lx)), q, K) });
      var lq = -4 + (QMAX + 4) * i / 120;
      ptsB.push({ logX: lq, value: damage(Math.pow(10, lq), K) });
    }
    var maxB = K / 1e-4;

    drawChart(document.getElementById("chartA"), {
      points: ptsA, minLog: 0, maxLog: 5, currentLog: logC, currentValue: p, maxValue: 1,
      formatValue: function (v) { return (100 * v).toFixed(0) + "%"; },
      formatXTick: function (v) { return fmt(Math.pow(10, v)); }
    });
    drawChart(document.getElementById("chartB"), {
      points: ptsB, minLog: -4, maxLog: QMAX, currentLog: logQ, currentValue: Math.min(dmg, maxB), maxValue: maxB,
      formatValue: fmt,
      formatXTick: function (v) { return (100 * Math.pow(10, v)).toPrecision(1) + "%"; }
    });

    document.getElementById("nowA").textContent = (100 * p).toFixed(0) + "%";
    document.getElementById("nowB").textContent = fmt(Math.min(dmg, maxB));
    document.getElementById("statP").textContent = (100 * p).toFixed(1) + "%";
    document.getElementById("statD").textContent = fmt(dmg) + " actions";
    document.getElementById("statR").textContent = regime.label;
    document.getElementById("detail").textContent = regime.detail + " " + TAIL;

    seen[key] = true;
    var box = document.getElementById("progress");
    while (box.firstChild) box.removeChild(box.firstChild);
    var lead = document.createElement("span");
    lead.className = "name";
    lead.textContent = "Regimes reached:";
    box.appendChild(lead);
    ORDER.forEach(function (k) {
      var pill = document.createElement("span");
      pill.className = "pill" + (seen[k] ? " seen" : "");
      pill.textContent = REGIMES[k].label;
      box.appendChild(pill);
    });
    var all = ORDER.every(function (k) { return seen[k]; });
    if (all) {
      var done = document.createElement("span");
      done.className = "done";
      done.textContent = "Both reachable regimes found.";
      box.appendChild(done);
    }

    if (save && window.Lens) {
      var summary = "Detection race explorer. Current levers: C = " + fmt(C) + " bad actions needed for catastrophe, q = "
        + (100 * q).toPrecision(2) + "% chance a bad action is noticed, K = " + K + " notices before a decisive response. "
        + "P(response before catastrophe) = " + (100 * p).toFixed(1) + "%, expected damage at response = " + fmt(dmg)
        + " actions, regime = " + regime.label + ". Regimes reached so far: "
        + ORDER.filter(function (k) { return seen[k]; }).map(function (k) { return REGIMES[k].label; }).join(", ") + ".";
      window.Lens.saveState({ c: Number(sC.value), q: Number(sQ.value), k: K, seen: seen }, summary);
      if (all && !completed) { completed = true; window.Lens.complete(); }
    }
  }

  sC.addEventListener("input", function () { render(true); });
  sQ.addEventListener("input", function () { render(true); });
  sK.addEventListener("input", function () { render(true); });
  document.getElementById("reset").addEventListener("click", function () {
    sC.value = 300; sQ.value = -200; sK.value = 3; render(true);
  });

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state, meta) {
      if (state) {
        if (typeof state.c === "number") sC.value = state.c;
        if (typeof state.q === "number") sQ.value = state.q;
        if (typeof state.k === "number") sK.value = state.k;
        if (state.seen) seen = state.seen;
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

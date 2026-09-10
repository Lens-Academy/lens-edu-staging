---
id: 'e6b75951-a68d-4f91-bd12-823a900ca252'
title: Gains from trade with an early schemer
summary_for_tutor: "A bargaining-range calculator built on the illustrative outcome table in Stastny, Jarviniemi and Shlegeris's \"Making deals with early schemers\". Four sliders set how likely humans are to dominate if the early AI cooperates (default 90 percent), how likely humans are to dominate if it sabotages (default 50 percent), how likely the early AI is to win by sabotaging (default 1 percent), and how credible our promise to pay is (default 100 percent). The widget draws the two outcome distributions as stacked bars and then marks two thresholds on an offer-size axis - the AI's minimum acceptable offer, computed as its sabotage payoff divided by the probability humans dominate after cooperation times credibility, and our maximum worthwhile offer, computed as the fractional improvement in our odds. At the defaults the window is roughly 1.1 percent to 44 percent of future resources, so a deal exists. The learner is asked to notice that lowering credibility raises the AI's minimum until the window closes, and that raising the odds that sabotage works for the AI does the same. Ask what the learner found closed the window first."
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
  --accent: #b87018; --accent-hover: #9a5c10;
  --humans: #2f7d5d; --early: #b87018; --later: #a8443c;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--bg); }
.lede { color: var(--muted); margin: 4px 0 16px; }
.legend { display: flex; flex-wrap: wrap; gap: 14px; margin-bottom: 10px; font-size: 12px; color: var(--muted); }
.swatch { display: inline-block; width: 10px; height: 10px; border-radius: 2px; margin-right: 6px; vertical-align: -1px; }
.chart { width: 100%; height: auto; display: block; }
.controls { display: grid; grid-template-columns: 1fr 1fr; gap: 10px 24px; margin-top: 18px; }
@media (max-width: 520px) { .controls { grid-template-columns: 1fr; } }
.ctrl label { display: flex; align-items: baseline; justify-content: space-between; gap: 10px; }
.ctrl .name { color: var(--muted); }
.ctrl .val { font-variant-numeric: tabular-nums; font-weight: 500; }
input[type=range] { width: 100%; accent-color: var(--accent); margin: 4px 0 0; }
.verdict { margin: 16px 0 0; padding: 12px 14px; border: 1px solid var(--border); border-radius: 8px; background: var(--page); min-height: 62px; }
.verdict.no { border-color: #d8cfc2; }
.verdict strong { font-weight: 600; }
.row { display: flex; align-items: center; justify-content: space-between; gap: 12px; margin-top: 14px; flex-wrap: wrap; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 8px 12px; cursor: pointer; }
button:hover { background: var(--page); }
.credit { margin-top: 12px; font-size: 12px; color: var(--muted); }
.credit a { color: var(--accent); }
</style>
</head>
<body>
<!-- Ported from XLab's "Gains from trade with an early schemer" demo on the AI Control track
     (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look. The model and the
     default numbers are XLab's; the table they start from is in the reading itself. -->
<div class="card">
  <p class="eyebrow">Figure</p>
  <h2>Gains from trade with an early schemer</h2>
  <p class="lede">Adjust the outcome probabilities of the illustrative cooperate/sabotage table and the credibility of our promise to pay. The chart shows the range of offers that beats both the AI's sabotage option and our no-deal odds.</p>

  <div class="legend">
    <span><span class="swatch" style="background:var(--humans)"></span>Humans dominate</span>
    <span><span class="swatch" style="background:var(--early)"></span>Early AI dominates</span>
    <span><span class="swatch" style="background:var(--later)"></span>Later AIs dominate</span>
  </div>

  <svg id="chart" class="chart" viewBox="0 0 560 236" role="img" aria-labelledby="chartTitle">
    <title id="chartTitle">Outcome distributions when the early AI cooperates versus sabotages, and the range of offer sizes acceptable to both sides</title>
  </svg>

  <div class="controls" id="controls"></div>

  <p class="verdict" id="verdict" aria-live="polite"></p>

  <div class="row">
    <button type="button" id="reset">Reset to the reading's numbers</button>
    <span class="credit">Model and defaults after XLab's demo for this lesson.</span>
  </div>
</div>

<script>
(function () {
  "use strict";

  var SVGNS = "http://www.w3.org/2000/svg";
  var BAR_X = 132, BAR_W = 408;

  var DEFAULTS = { humansCoop: 90, humansSab: 50, earlyWins: 1, credibility: 100 };
  var s = { humansCoop: 90, humansSab: 50, earlyWins: 1, credibility: 100 };

  var SERIES = [
    { key: "humans", label: "Humans dominate", color: "var(--humans)" },
    { key: "early", label: "Early AI dominates", color: "var(--early)" },
    { key: "later", label: "Later AIs dominate", color: "var(--later)" }
  ];

  var CONTROLS = [
    { key: "humansCoop", label: "Humans dominate if the AI cooperates" },
    { key: "humansSab", label: "Humans dominate if the AI sabotages" },
    { key: "earlyWins", label: "The AI itself wins via sabotage" },
    { key: "credibility", label: "Credibility of our promise to pay" }
  ];

  function fmt(v) {
    if (!isFinite(v)) return "n/a";
    return v < 10 ? v.toFixed(1) : String(Math.round(v));
  }

  function model() {
    var e = s.humansCoop, r = s.humansSab, m = s.credibility;
    var u = Math.min(s.earlyWins, 100 - r);
    var aiMin = (e > 0 && m > 0) ? (10000 * u) / (e * m) : Infinity;
    var ourMax = e > 0 ? (1 - r / e) * 100 : 0;
    return { e: e, r: r, m: m, u: u, aiMin: aiMin, ourMax: ourMax, deal: aiMin < ourMax };
  }

  function el(name, attrs, text) {
    var n = document.createElementNS(SVGNS, name);
    for (var k in attrs) { if (attrs[k] !== undefined && attrs[k] !== null) n.setAttribute(k, String(attrs[k])); }
    if (text !== undefined) n.appendChild(document.createTextNode(String(text)));
    return n;
  }

  function xPos(pct) {
    return BAR_X + Math.min(Math.max(pct, 0), 100) / 100 * BAR_W;
  }

  function drawBar(g, y, title, shares) {
    g.appendChild(el("text", {
      x: BAR_X - 8, y: y + 17, "text-anchor": "end",
      fill: "var(--text)", "font-size": 11, "font-weight": 500
    }, title));
    var run = 0;
    for (var i = 0; i < shares.length; i++) {
      var w = shares[i] / 100 * BAR_W;
      var x = BAR_X + run / 100 * BAR_W;
      run += shares[i];
      if (w > 0) g.appendChild(el("rect", { x: x, y: y, width: w, height: 26, fill: SERIES[i].color }));
      if (w > 36) {
        g.appendChild(el("text", {
          x: x + w / 2, y: y + 17, "text-anchor": "middle",
          fill: "#ffffff", "font-size": 10, "font-weight": 500
        }, Math.round(shares[i]) + "%"));
      }
    }
    g.appendChild(el("rect", { x: BAR_X, y: y, width: BAR_W, height: 26, fill: "none", stroke: "var(--border)", "stroke-width": 1 }));
  }

  function render() {
    var m = model();
    var svg = document.getElementById("chart");
    while (svg.childNodes.length > 1) svg.removeChild(svg.lastChild);

    drawBar(svg, 12, "AI cooperates", [m.e, 0, 100 - m.e]);
    drawBar(svg, 52, "AI sabotages", [m.r, m.u, 100 - m.r - m.u]);

    svg.appendChild(el("text", { x: BAR_X, y: 122, fill: "var(--text)", "font-size": 11, "font-weight": 500 }, "Offer size (share of future resources)"));

    if (m.deal) {
      svg.appendChild(el("rect", {
        x: xPos(m.aiMin), y: 166, width: Math.max(xPos(m.ourMax) - xPos(m.aiMin), 1.5), height: 14,
        fill: "var(--accent)", "fill-opacity": 0.18
      }));
    }

    svg.appendChild(el("line", { x1: BAR_X, y1: 180, x2: BAR_X + BAR_W, y2: 180, stroke: "var(--border)", "stroke-width": 1 }));
    [0, 25, 50, 75, 100].forEach(function (t) {
      svg.appendChild(el("line", { x1: xPos(t), y1: 180, x2: xPos(t), y2: 184, stroke: "var(--border)", "stroke-width": 1 }));
      svg.appendChild(el("text", { x: xPos(t), y: 196, "text-anchor": "middle", fill: "var(--muted)", "font-size": 10 }, t + "%"));
    });

    // AI's minimum
    var aiX = xPos(isFinite(m.aiMin) ? m.aiMin : 100);
    svg.appendChild(el("line", { x1: aiX, y1: 142, x2: aiX, y2: 180, stroke: "var(--early)", "stroke-width": 2 }));
    svg.appendChild(el("text", {
      x: aiX, y: 138, "text-anchor": (m.aiMin > 75 ? "end" : "start"),
      fill: "var(--early)", "font-size": 10, "font-weight": 500,
      stroke: "var(--bg)", "stroke-width": 4, "paint-order": "stroke"
    }, m.aiMin > 100 ? "AI's minimum > 100%" : "AI's minimum " + fmt(m.aiMin) + "%"));

    // our maximum
    var ourX = xPos(m.ourMax);
    svg.appendChild(el("line", { x1: ourX, y1: 160, x2: ourX, y2: 180, stroke: "var(--humans)", "stroke-width": 2 }));
    svg.appendChild(el("text", {
      x: ourX, y: 156, "text-anchor": (m.ourMax > 75 ? "end" : "start"),
      fill: "var(--humans)", "font-size": 10, "font-weight": 500,
      stroke: "var(--bg)", "stroke-width": 4, "paint-order": "stroke"
    }, m.ourMax <= 0 ? "our maximum ≤ 0%" : "our maximum " + fmt(m.ourMax) + "%"));

    var verdict = document.getElementById("verdict");
    var msg;
    if (m.deal) {
      msg = "Any offer between " + fmt(m.aiMin) + "% and " + fmt(m.ourMax) + "% of future resources beats both sides' no-deal alternatives. Lowering credibility raises the AI's minimum: a less credible promise must be compensated with a more generous offer.";
      verdict.className = "verdict";
    } else if (m.ourMax <= 0) {
      msg = "No deal: cooperation does not improve our odds enough for any offer to be worth its cost to us.";
      verdict.className = "verdict no";
    } else {
      msg = "No deal: the smallest offer the AI would accept exceeds the largest offer worth making. The promise is too unlikely to pay out (or sabotage too likely to win) for any share to bridge the gap.";
      verdict.className = "verdict no";
    }
    verdict.textContent = msg;

    // keep the slider readouts and the max on "the AI itself wins" in step
    CONTROLS.forEach(function (c) {
      var input = document.getElementById("in-" + c.key);
      var out = document.getElementById("out-" + c.key);
      if (c.key === "earlyWins") input.max = String(100 - s.humansSab);
      input.value = String(s[c.key]);
      out.textContent = s[c.key] + "%";
    });

    save(m);
  }

  var saveTimer = null;
  function save(m) {
    if (!window.Lens) return;
    if (saveTimer) clearTimeout(saveTimer);
    saveTimer = setTimeout(function () {
      var summary = "Gains-from-trade sliders: humans dominate " + m.e + "% if the early AI cooperates and " +
        m.r + "% if it sabotages, the early AI itself wins " + m.u + "% of the time by sabotaging, and our promise to pay is " +
        m.m + "% credible. " +
        (m.deal
          ? "A bargaining window is open: offers between " + fmt(m.aiMin) + "% and " + fmt(m.ourMax) + "% of future resources beat both sides' no-deal alternatives."
          : "No bargaining window: the AI's minimum acceptable offer (" + (isFinite(m.aiMin) ? fmt(m.aiMin) + "%" : "unbounded") + ") is not below our maximum worthwhile offer (" + fmt(m.ourMax) + "%).");
      window.Lens.saveState({ v: 1, s: s }, summary);
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
      input.min = "0";
      input.max = "100";
      input.step = "1";
      input.value = String(s[c.key]);
      input.addEventListener("input", function () {
        var v = Number(input.value);
        s[c.key] = v;
        if (c.key === "humansSab") s.earlyWins = Math.min(s.earlyWins, 100 - v);
        render();
      });
      wrap.appendChild(label);
      wrap.appendChild(input);
      host.appendChild(wrap);
    });
  }

  document.getElementById("reset").addEventListener("click", function () {
    s.humansCoop = DEFAULTS.humansCoop;
    s.humansSab = DEFAULTS.humansSab;
    s.earlyWins = DEFAULTS.earlyWins;
    s.credibility = DEFAULTS.credibility;
    render();
  });

  buildControls();

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state) {
      if (state && state.s) {
        CONTROLS.forEach(function (c) {
          if (typeof state.s[c.key] === "number") s[c.key] = state.s[c.key];
        });
      }
      render();
    });
  } else {
    render();
  }
})();
</script>
</body>
</html>

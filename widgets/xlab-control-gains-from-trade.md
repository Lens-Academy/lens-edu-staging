---
id: 'e6b75951-a68d-4f91-bd12-823a900ca252'
title: Gains from trade with an early schemer
summary_for_tutor: "A bargaining-range calculator built on the illustrative outcome table in Stastny, Jarviniemi and Shlegeris's \"Making deals with early schemers\", which the reading shows on the page just above this figure. Four sliders set how likely humans are to dominate if the early AI cooperates (default 90 percent), how likely humans are to dominate if it sabotages (default 50 percent), how likely the early AI is to win by sabotaging (default 1 percent), and how credible our promise to pay is (default 100 percent). The widget draws the two outcome distributions as stacked bars and marks two thresholds on an offer-size axis: the AI's minimum acceptable offer, its sabotage payoff divided by the chance the payment ever arrives, and our maximum worthwhile offer, the fractional improvement in our odds. At the defaults the window is roughly 1.1 percent to 44 percent of future resources, so a deal exists. The widget itself carries only the chart, the sliders and a one-line verdict; the Text segment above it explains what the two marks mean, says that lowering credibility raises the AI's minimum, and sets the task of finding what closes the window first. It completes once the learner has seen the window both open and closed. Ask what the learner found closed the window first."
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
</style>
</head>
<body>
<!-- Ported from XLab's "Gains from trade with an early schemer" demo on the AI Control track
     (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look. The model and the
     default numbers are XLab's; the table they start from is in the reading itself. -->
<div class="card">
  <p class="eyebrow">Figure</p>
  <h2>Gains from trade with an early schemer</h2>
  <p class="lede">Move the sliders and watch the two marks on the offer axis.</p>

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
  </div>
</div>

<script>
(function () {
  "use strict";

  var SVGNS = "http://www.w3.org/2000/svg";

  var WIDE = { vbw: 560, vbh: 236, barX: 132, barW: 408, titleAbove: false,
               bar1: 12, bar2: 52, axisLabel: 122, aiText: 138, aiTop: 142,
               ourText: 156, ourTop: 160, band: 166, axis: 180, tickText: 196 };
  var NARROW = { vbw: 336, vbh: 214, barX: 12, barW: 310, titleAbove: true,
                 bar1: 18, bar2: 70, axisLabel: 122, aiText: 140, aiTop: 144,
                 ourText: 158, ourTop: 162, band: 168, axis: 182, tickText: 198 };
  var L = WIDE;

  function layout() {
    return (document.documentElement.clientWidth || window.innerWidth) < 520 ? NARROW : WIDE;
  }

  var DEFAULTS = { humansCoop: 90, humansSab: 50, earlyWins: 1, credibility: 100 };
  var s = { humansCoop: 90, humansSab: 50, earlyWins: 1, credibility: 100 };
  var seenDeal = false, seenClosed = false, completed = false;

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
    return L.barX + Math.min(Math.max(pct, 0), 100) / 100 * L.barW;
  }

  function drawBar(g, y, title, shares) {
    g.appendChild(el("text", L.titleAbove
      ? { x: L.barX, y: y - 5, "text-anchor": "start", fill: "var(--text)", "font-size": 11, "font-weight": 500 }
      : { x: L.barX - 8, y: y + 17, "text-anchor": "end", fill: "var(--text)", "font-size": 11, "font-weight": 500 },
      title));
    var run = 0;
    for (var i = 0; i < shares.length; i++) {
      var w = shares[i] / 100 * L.barW;
      var x = L.barX + run / 100 * L.barW;
      run += shares[i];
      if (w > 0) g.appendChild(el("rect", { x: x, y: y, width: w, height: 26, fill: SERIES[i].color }));
      if (w > 30) {
        g.appendChild(el("text", {
          x: x + w / 2, y: y + 17, "text-anchor": "middle",
          fill: "#ffffff", "font-size": 10, "font-weight": 500
        }, Math.round(shares[i]) + "%"));
      }
    }
    g.appendChild(el("rect", { x: L.barX, y: y, width: L.barW, height: 26, fill: "none", stroke: "var(--border)", "stroke-width": 1 }));
  }

  function render() {
    var m = model();
    var svg = document.getElementById("chart");
    L = layout();
    svg.setAttribute("viewBox", "0 0 " + L.vbw + " " + L.vbh);
    while (svg.childNodes.length > 1) svg.removeChild(svg.lastChild);

    drawBar(svg, L.bar1, "AI cooperates", [m.e, 0, 100 - m.e]);
    drawBar(svg, L.bar2, "AI sabotages", [m.r, m.u, 100 - m.r - m.u]);

    svg.appendChild(el("text", { x: L.barX, y: L.axisLabel, fill: "var(--text)", "font-size": 11, "font-weight": 500 }, "Offer size (share of future resources)"));

    if (m.deal) {
      svg.appendChild(el("rect", {
        x: xPos(m.aiMin), y: L.band, width: Math.max(xPos(m.ourMax) - xPos(m.aiMin), 1.5), height: 14,
        fill: "var(--accent)", "fill-opacity": 0.18
      }));
    }

    svg.appendChild(el("line", { x1: L.barX, y1: L.axis, x2: L.barX + L.barW, y2: L.axis, stroke: "var(--border)", "stroke-width": 1 }));
    [0, 25, 50, 75, 100].forEach(function (t) {
      svg.appendChild(el("line", { x1: xPos(t), y1: L.axis, x2: xPos(t), y2: L.axis + 4, stroke: "var(--border)", "stroke-width": 1 }));
      svg.appendChild(el("text", { x: xPos(t), y: L.tickText, "text-anchor": "middle", fill: "var(--muted)", "font-size": 10 }, t + "%"));
    });

    // AI's minimum
    var aiX = xPos(isFinite(m.aiMin) ? m.aiMin : 100);
    svg.appendChild(el("line", { x1: aiX, y1: L.aiTop, x2: aiX, y2: L.axis, stroke: "var(--early)", "stroke-width": 2 }));
    svg.appendChild(el("text", {
      x: aiX, y: L.aiText, "text-anchor": (m.aiMin > 60 ? "end" : "start"),
      fill: "var(--early)", "font-size": 10, "font-weight": 500,
      stroke: "var(--bg)", "stroke-width": 4, "paint-order": "stroke"
    }, m.aiMin > 100 ? "AI's minimum > 100%" : "AI's minimum " + fmt(m.aiMin) + "%"));

    // our maximum
    var ourX = xPos(m.ourMax);
    svg.appendChild(el("line", { x1: ourX, y1: L.ourTop, x2: ourX, y2: L.axis, stroke: "var(--humans)", "stroke-width": 2 }));
    svg.appendChild(el("text", {
      x: ourX, y: L.ourText, "text-anchor": (m.ourMax > 60 ? "end" : "start"),
      fill: "var(--humans)", "font-size": 10, "font-weight": 500,
      stroke: "var(--bg)", "stroke-width": 4, "paint-order": "stroke"
    }, m.ourMax <= 0 ? "our maximum \u2264 0%" : "our maximum " + fmt(m.ourMax) + "%"));

    var verdict = document.getElementById("verdict");
    var msg;
    if (m.deal) {
      msg = "Any offer between " + fmt(m.aiMin) + "% and " + fmt(m.ourMax) + "% of future resources beats both sides' no-deal alternatives.";
      verdict.className = "verdict";
    } else if (m.ourMax <= 0) {
      msg = "No deal: cooperation does not improve our odds enough for any offer to be worth its cost to us.";
      verdict.className = "verdict no";
    } else {
      msg = "No deal: the smallest offer the AI would accept exceeds the largest offer worth making. The promise is too unlikely to pay out (or sabotage too likely to win) for any share to bridge the gap.";
      verdict.className = "verdict no";
    }
    verdict.textContent = msg;

    if (m.deal) seenDeal = true; else seenClosed = true;
    if (seenDeal && seenClosed && !completed) {
      completed = true;
      if (window.Lens && window.Lens.complete) window.Lens.complete();
    }

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
      window.Lens.saveState({ v: 1, s: s, seenDeal: seenDeal, seenClosed: seenClosed }, summary);
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

  var resizeTimer = null;
  window.addEventListener("resize", function () {
    if (resizeTimer) clearTimeout(resizeTimer);
    resizeTimer = setTimeout(render, 120);
  });

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state) {
      if (state && state.s) {
        CONTROLS.forEach(function (c) {
          if (typeof state.s[c.key] === "number") s[c.key] = state.s[c.key];
        });
        seenDeal = !!state.seenDeal;
        seenClosed = !!state.seenClosed;
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

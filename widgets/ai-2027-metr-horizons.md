---
id: '9d9dd5e9-0e78-4de1-a1d9-47af42f4f53a'
title: AI time horizons on METR's tasks, with the AI 2027 scenario markers
summary_for_tutor: "An interactive replacement for the static METR time-horizon chart in the AI 2027 article. It plots, on a log time axis against release date, the task length (in human work time) at which each frontier model succeeds 50% or 80% of the time, from METR's public Time Horizon 1.1 data (26 models, GPT-2 in 2019 through Claude Mythos Preview in April 2026, with 95% confidence intervals). The 80% view also shows where ai-2027.com placed its fictional Agent-0, Agent-1 and Agent-2 (mid-2025, mid-2026, 2027). The learner switches between the 50% and 80% horizons, toggles the confidence intervals, and fits an exponential trend to all points or only to points from 2023 on; the widget reports the doubling time implied by that fit next to METR's own published doubling times (188 days all-time, 129 days from 2023 on). Hovering or arrowing through the point list shows each model's exact numbers. The widget counts as complete once the learner has looked at both views and inspected at least three points. Useful discussion: how much faster the post-2023 trend is than the long-run one, how wide the intervals get above a few hours (METR warns that measurements above 16 hours are unreliable on the current task suite), and whether the scenario's Agent-1 and Agent-2 sit on or above the fitted trend."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>AI time horizons on METR's tasks</title>
<!-- Interactive replacement for the static chart "Length Of Coding Tasks AI Agents Can Complete Autonomously" in the AI 2027 article (ai-2027.com, section "Why we forecast a superhuman coder in early 2027").
     Data sources:
     1. METR, Time Horizon 1.1 results: https://metr.org/assets/benchmark_results_1_1.yaml (linked from https://metr.org/time-horizons/), retrieved 2026-09-08. p50 and p80 horizons in human minutes with 95% CI; is_sota flag; release dates. Published doubling times from the same file.
     2. AI 2027 scenario markers (Agent-0, Agent-1, Agent-2): the chart component shipped in ai-2027.com's page bundle (/_next/static/chunks/4979-f40d73c22048fefc.js, 80%-success-rate variant), retrieved 2026-09-08. Positions are the site's own x (decimal year) and y (index on its label scale, where label i = 4 s * 2^i). Nothing here is read off a picture.
     Trend lines are ordinary least squares fits of log2(horizon) on release year computed in this page from the points shown; the doubling time is reported next to METR's published figures. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10; --grey: #8a8a8a;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 22px; margin: 4px 0 6px; }
  .lede { color: var(--muted); margin: 0 0 12px; max-width: 46rem; }
  .controls { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; margin-bottom: 8px; }
  .group { display: flex; flex-wrap: wrap; gap: 4px; align-items: center; border: 1px solid var(--border); border-radius: 8px; padding: 4px; background: #fff; }
  .group-label { font-size: 11px; color: var(--muted); padding: 0 6px; text-transform: uppercase; letter-spacing: 0.08em; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 6px; background: #fff; padding: 5px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button[aria-pressed="true"], button[aria-checked="true"] { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); font-weight: 600; }
  .chart-box { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px; overflow-x: auto; }
  .chart-box svg { display: block; width: 100%; height: auto; min-width: 520px; font-family: var(--font-ui); }
  .axis text { font-size: 11px; fill: var(--muted); }
  .grid line { stroke: var(--border); stroke-width: 1; }
  .pt { cursor: pointer; }
  .hit { fill: transparent; pointer-events: all; }
  .lbl { paint-order: stroke; stroke: #ffffff; stroke-width: 3px; stroke-linejoin: round; }
  .detail { margin-top: 10px; border: 1px solid var(--border); border-radius: 8px; padding: 12px 14px; background: var(--surface); min-height: 64px; }
  .detail h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
  .detail p { margin: 0; }
  .fit { margin-top: 10px; display: grid; gap: 8px; }
  @media (min-width: 640px) { .fit { grid-template-columns: 1fr 1fr; } }
  .stat { border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: #fff; }
  .stat .big { font-family: var(--font-heading); font-size: 22px; font-weight: 600; }
  .stat .sub { color: var(--muted); font-size: 12px; }
  .list-wrap { margin-top: 12px; }
  .list { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 6px; }
  .list button { font-size: 12px; padding: 4px 8px; }
  .list button.is-seen::before { content: "\2713 "; color: var(--accent); }
  .list button.is-current { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .legend { display: flex; flex-wrap: wrap; gap: 14px; margin-top: 8px; font-size: 12px; color: var(--muted); align-items: center; }
  .legend span { display: inline-flex; align-items: center; gap: 6px; }
  .foot { margin-top: 12px; font-size: 12px; color: var(--muted); }
  .foot p { margin: 0 0 6px; }
  a { color: var(--accent); }
  .done { margin-top: 10px; font-size: 12px; color: var(--muted); }
  .done.is-visible::before { content: "\2713 "; color: var(--accent); }
</style>
</head>
<body>
<p class="eyebrow">Interactive chart</p>
<h1>Length of software tasks AI agents can complete on their own</h1>
<p class="lede">METR measures the "time horizon" of a model: the length of task, in human working time, at which the model succeeds 50% or 80% of the time. The AI 2027 article extends this trend to argue for a superhuman coder in 2027. Switch views, fit a trend, and hover or arrow through the points.</p>

<div class="controls">
  <div class="group" role="radiogroup" aria-label="Success rate">
    <span class="group-label">Success rate</span>
    <button type="button" role="radio" data-view="p50" aria-checked="false">50% horizon</button>
    <button type="button" role="radio" data-view="p80" aria-checked="false">80% horizon</button>
  </div>
  <div class="group" role="radiogroup" aria-label="Trend fit">
    <span class="group-label">Trend fit</span>
    <button type="button" role="radio" data-trend="all" aria-checked="false">All points</button>
    <button type="button" role="radio" data-trend="2023" aria-checked="false">From 2023 on</button>
    <button type="button" role="radio" data-trend="off" aria-checked="false">Off</button>
  </div>
  <div class="group">
    <button type="button" id="ci" aria-pressed="false">95% intervals</button>
    <button type="button" id="agents" aria-pressed="false">AI 2027 agents</button>
  </div>
</div>

<div class="chart-box" id="chart-box"></div>
<div class="legend" id="legend"></div>

<div class="detail" id="detail" aria-live="polite">
  <h2 id="d-title">Hover a point, or use the list below</h2>
  <p id="d-body">Filled circles are models that were state of the art on METR's suite when measured; hollow circles were not. Squares are the AI 2027 scenario's fictional agents, drawn where ai-2027.com placed them.</p>
</div>

<div class="fit" id="fit"></div>

<div class="list-wrap">
  <p class="eyebrow">Points (arrow keys move between them)</p>
  <div class="list" id="list" role="list"></div>
</div>
<p class="done" id="done"></p>

<div class="foot">
  <p>Data: METR, Time Horizon 1.1 (<a href="https://metr.org/time-horizons/" target="_blank" rel="noopener">metr.org/time-horizons</a>, results file retrieved 8 Sep 2026), human minutes with 95% confidence intervals. METR's note of 8 May 2026: "Measurements above 16 hrs are unreliable with our current task suite." Scenario markers: the chart component on <a href="https://ai-2027.com/" target="_blank" rel="noopener">ai-2027.com</a> (80% variant, retrieved 8 Sep 2026); they are the authors' placements for fictional systems, not measurements.</p>
  <p>Time conversions used for labels: 1 work day = 8 hours, 1 work week = 40 hours, 1 work month = 167 hours, 1 work year = 2,000 hours (the AI Futures convention). Trend lines are least-squares fits of log2(horizon) on release date over the points shown, computed on this page; the doubling times are shown beside METR's published ones.</p>
</div>

<script>
var METR = [
  {"key": "gpt2", "name": "GPT-2", "date": "2019-02-14", "sota": true, "p50": [0.053778, 0.009994, 0.141825], "p80": [0.0128, 0.001589, 0.068612], "score": 0.101046},
  {"key": "davinci_002", "name": "davinci-002 (GPT-3)", "date": "2020-05-28", "sota": true, "p50": [0.144057, 0.093319, 0.221209], "p80": [0.056238, 0.034813, 0.105813], "score": 0.161869},
  {"key": "gpt_3_5_turbo_instruct", "name": "gpt-3.5-turbo-instruct", "date": "2022-03-15", "sota": true, "p50": [0.599247, 0.255148, 1.115905], "p80": [0.25538, 0.141649, 0.492933], "score": 0.214611},
  {"key": "gpt_4", "name": "GPT-4 0314", "date": "2023-03-14", "sota": true, "p50": [3.987428, 1.93292, 7.995283], "p80": [0.889561, 0.342984, 2.523746], "score": 0.293044},
  {"key": "gpt_4_1106_inspect", "name": "GPT-4 1106", "date": "2023-11-06", "sota": true, "p50": [4.044959, 1.866859, 8.443226], "p80": [0.783032, 0.276599, 2.358414], "score": 0.28905},
  {"key": "claude_3_opus_inspect", "name": "Claude 3 Opus", "date": "2024-03-04", "sota": false, "p50": [3.952262, 1.706313, 8.76484], "p80": [0.638973, 0.190491, 2.118276], "score": 0.294753},
  {"key": "gpt_4_turbo_inspect", "name": "GPT-4 Turbo", "date": "2024-04-09", "sota": false, "p50": [3.732787, 1.980046, 6.736613], "p80": [0.927933, 0.428277, 2.196806], "score": 0.271786},
  {"key": "gpt_4o_inspect", "name": "GPT-4o", "date": "2024-05-13", "sota": true, "p50": [6.991195, 4.001482, 12.905741], "p80": [1.267009, 0.562997, 3.01517], "score": 0.338424},
  {"key": "claude_3_5_sonnet_20240620_inspect", "name": "Claude 3.5 Sonnet (Old)", "date": "2024-06-20", "sota": true, "p50": [11.395377, 5.489734, 22.384214], "p80": [1.671757, 0.57927, 4.573519], "score": 0.401502},
  {"key": "o1_preview", "name": "o1-preview", "date": "2024-09-12", "sota": true, "p50": [20.326586, 11.716193, 33.379877], "p80": [4.420545, 2.012646, 8.912444], "score": 0.451441},
  {"key": "claude_3_5_sonnet_20241022_inspect", "name": "Claude 3.5 Sonnet (New)", "date": "2024-10-22", "sota": true, "p50": [20.522872, 10.144026, 40.82028], "p80": [2.595677, 0.89379, 7.363864], "score": 0.452356},
  {"key": "o1_inspect", "name": "o1", "date": "2024-12-05", "sota": true, "p50": [38.831588, 21.164512, 64.95249], "p80": [7.090121, 3.036033, 16.640636], "score": 0.510512},
  {"key": "claude_3_7_sonnet_inspect", "name": "Claude 3.7 Sonnet", "date": "2025-02-24", "sota": true, "p50": [60.388937, 33.006168, 104.226017], "p80": [12.09179, 4.575608, 28.889879], "score": 0.558217},
  {"key": "o3_inspect", "name": "o3", "date": "2025-04-16", "sota": true, "p50": [119.732634, 74.615398, 190.943818], "p80": [29.981603, 15.127348, 57.823511], "score": 0.636235},
  {"key": "claude_4_opus_inspect", "name": "Claude 4 Opus", "date": "2025-05-22", "sota": false, "p50": [100.366123, 59.994073, 163.454074], "p80": [20.429752, 8.483125, 41.937268], "score": 0.615452},
  {"key": "claude_4_1_opus_inspect", "name": "Claude 4.1 Opus", "date": "2025-08-05", "sota": false, "p50": [100.472004, 59.272391, 159.451918], "p80": [23.455761, 10.538456, 47.785951], "score": 0.615713},
  {"key": "gpt_5_2025_08_07_inspect", "name": "GPT-5", "date": "2025-08-07", "sota": true, "p50": [203.012577, 112.641357, 405.551565], "p80": [38.312431, 19.184874, 70.093125], "score": 0.693697},
  {"key": "gemini_3_pro", "name": "Gemini 3 Pro", "date": "2025-11-18", "sota": true, "p50": [224.325884, 139.565157, 379.235434], "p80": [54.142849, 25.650451, 103.295501], "score": 0.709822},
  {"key": "gpt_5_1_codex_max_inspect", "name": "GPT-5.1-Codex-Max", "date": "2025-11-19", "sota": false, "p50": [223.714694, 134.31077, 396.206723], "p80": [50.632499, 27.30204, 88.365435], "score": 0.708301},
  {"key": "claude_opus_4_5_inspect", "name": "Claude Opus 4.5", "date": "2025-11-24", "sota": true, "p50": [292.994594, 161.717714, 623.704698], "p80": [49.430584, 20.660485, 104.641318], "score": 0.73007},
  {"key": "gpt_5_2", "name": "GPT-5.2", "date": "2025-12-11", "sota": true, "p50": [352.249302, 198.067494, 815.177445], "p80": [66.002649, 31.665111, 131.730719], "score": 0.752875},
  {"key": "claude_opus_4_6_inspect", "name": "Claude Opus 4.6", "date": "2026-02-05", "sota": true, "p50": [718.80683, 316.685725, 3633.786163], "p80": [69.874587, 27.026521, 170.437873], "score": 0.788644},
  {"key": "gpt_5_3_codex", "name": "GPT-5.3-Codex", "date": "2026-02-05", "sota": false, "p50": [349.530732, 194.913134, 816.351994], "p80": [54.739407, 22.361504, 122.058963], "score": 0.745439},
  {"key": "gemini_3_1_pro", "name": "Gemini 3.1 Pro", "date": "2026-02-19", "sota": false, "p50": [384.147435, 233.50073, 694.750898], "p80": [89.801503, 52.025934, 158.618017], "score": 0.77035},
  {"key": "gpt_5_4", "name": "GPT-5.4", "date": "2026-03-05", "sota": false, "p50": [341.735276, 186.581591, 768.779526], "p80": [53.877851, 23.957027, 108.679232], "score": 0.743443},
  {"key": "claude_mythos_preview_early_inspect", "name": "Claude Mythos Preview (early)", "date": "2026-04-07", "sota": true, "p50": [1044.780145, 508.876789, 3304.261235], "p80": [185.911829, 97.30292, 398.514614], "score": 0.85205}
];
// METR's published doubling times (days), same file. The file notes they exclude points with a central p50 estimate above 16 hours.
var METR_DOUBLING = { allTime: 187.778, from2023: 128.744, from2023Low: 104.428, from2023High: 158.012 };
// AI 2027 scenario markers from ai-2027.com's chart component (80% variant): x = decimal year, idx = position on the site's label scale (label i = 4 s * 2^i).
var AGENTS = [
  { key: "agent0", name: "Agent-0", x: 2025.6, idx: 10, when: "mid-2025 in the scenario" },
  { key: "agent1", name: "Agent-1", x: 2026.5, idx: 16.7, when: "mid-2026 in the scenario" },
  { key: "agent2", name: "Agent-2", x: 2027, idx: 22.2, when: "early 2027 in the scenario" }
];
AGENTS.forEach(function (a) { a.minutes = 4 * Math.pow(2, a.idx) / 60; });

var W = 740, H = 400, ML = 104, MR = 16, MT = 14, MB = 36;
var X0 = 2018.7, X1 = 2028.2, YMIN = 0.004, YMAX = 2000000;
var YTICKS = [
  [1 / 60, "1 sec"], [1, "1 min"], [10, "10 min"], [60, "1 hour"], [480, "1 work day"],
  [2400, "1 work week"], [10000, "1 work month"], [120000, "1 work year"], [1200000, "10 work years"]
];
var SVGNS = "http://www.w3.org/2000/svg";

var state = { view: "p80", trend: "all", ci: true, agents: true, seen: {}, views: {}, current: null };
var completed = false;

function el(tag, className, text) { var n = document.createElement(tag); if (className) n.className = className; if (text !== undefined) n.textContent = text; return n; }
function svgEl(tag, attrs, text) { var n = document.createElementNS(SVGNS, tag); for (var k in attrs) n.setAttribute(k, attrs[k]); if (text !== undefined) n.textContent = text; return n; }
function decYear(iso) { var p = iso.split("-"); var y = +p[0], m = +p[1], d = +p[2]; var start = Date.UTC(y, 0, 1), next = Date.UTC(y + 1, 0, 1); return y + (Date.UTC(y, m - 1, d) - start) / (next - start); }
function sx(year) { return ML + (year - X0) / (X1 - X0) * (W - ML - MR); }
function sy(min) { var t = (Math.log10(min) - Math.log10(YMIN)) / (Math.log10(YMAX) - Math.log10(YMIN)); return H - MB - t * (H - MT - MB); }
function fmtMin(m) {
  if (m < 1) return Math.round(m * 60) + " sec";
  if (m < 60) return (m < 10 ? m.toFixed(1) : Math.round(m)) + " min";
  var h = m / 60;
  if (h < 8) return h.toFixed(1) + " hours";
  if (h < 40) return (h / 8).toFixed(1) + " work days (" + Math.round(h) + " h)";
  if (h < 167) return (h / 40).toFixed(1) + " work weeks (" + Math.round(h) + " h)";
  if (h < 2000) return (h / 166.67).toFixed(1) + " work months (" + Math.round(h) + " h)";
  return (h / 2000).toFixed(1) + " work years (" + Math.round(h).toLocaleString("en-US") + " h)";
}
function fmtDate(iso) { var d = new Date(iso + "T00:00:00Z"); return d.toLocaleDateString("en-US", { year: "numeric", month: "short", day: "numeric", timeZone: "UTC" }); }

function fitPoints() {
  var pts = METR.filter(function (m) { return state.trend === "all" || (state.trend === "2023" && m.date >= "2023-01-01"); });
  if (state.trend === "off" || pts.length < 2) return null;
  var n = pts.length, sxx = 0, sxy = 0, mx = 0, my = 0;
  pts.forEach(function (m) { mx += decYear(m.date); my += Math.log2(m[state.view][0]); });
  mx /= n; my /= n;
  pts.forEach(function (m) { var dx = decYear(m.date) - mx, dy = Math.log2(m[state.view][0]) - my; sxx += dx * dx; sxy += dx * dy; });
  var slope = sxy / sxx, intercept = my - slope * mx;
  return { slope: slope, intercept: intercept, n: n, doublingDays: 365.25 / slope, xmin: Math.min.apply(null, pts.map(function (m) { return decYear(m.date); })) };
}

function drawChart() {
  var box = document.getElementById("chart-box");
  box.textContent = "";
  var svg = svgEl("svg", { viewBox: "0 0 " + W + " " + H, role: "img", "aria-label": "Scatter chart of model time horizons by release date, log scale" });
  var grid = svgEl("g", { "class": "grid" });
  var axis = svgEl("g", { "class": "axis" });
  YTICKS.forEach(function (t) {
    if (t[0] < YMIN || t[0] > YMAX) return;
    var y = sy(t[0]);
    grid.appendChild(svgEl("line", { x1: ML, x2: W - MR, y1: y, y2: y }));
    axis.appendChild(svgEl("text", { x: ML - 6, y: y + 4, "text-anchor": "end" }, t[1]));
  });
  for (var yr = 2019; yr <= X1; yr++) {
    var x = sx(yr);
    grid.appendChild(svgEl("line", { x1: x, x2: x, y1: MT, y2: H - MB }));
    axis.appendChild(svgEl("text", { x: x, y: H - MB + 16, "text-anchor": "middle" }, String(yr)));
  }
  axis.appendChild(svgEl("text", { x: (ML + W - MR) / 2, y: H - 4, "text-anchor": "middle" }, "Model release date"));
  axis.appendChild(svgEl("text", { x: 12, y: (MT + H - MB) / 2, "text-anchor": "middle", transform: "rotate(-90 12 " + ((MT + H - MB) / 2) + ")" }, "Task length for humans, " + (state.view === "p50" ? "50%" : "80%") + " success"));
  svg.appendChild(grid); svg.appendChild(axis);

  // Mar 2027 marker: the article's superhuman-coder date.
  var xm = sx(2027 + 2 / 12);
  svg.appendChild(svgEl("line", { x1: xm, x2: xm, y1: MT, y2: H - MB, stroke: "#8a8a8a", "stroke-dasharray": "3 3" }));
  svg.appendChild(svgEl("text", { x: xm - 4, y: H - MB - 6, "text-anchor": "end", "font-size": "11", fill: "#5a5a5a" }, "Mar 2027 (SC in AI 2027)"));

  var fit = fitPoints();
  if (fit) {
    var xa = fit.xmin, xb = X1;
    var ya = Math.pow(2, fit.intercept + fit.slope * xa), yb = Math.pow(2, fit.intercept + fit.slope * xb);
    if (yb > YMAX) { xb = (Math.log2(YMAX) - fit.intercept) / fit.slope; yb = YMAX; }
    if (ya < YMIN) { xa = (Math.log2(YMIN) - fit.intercept) / fit.slope; ya = YMIN; }
    svg.appendChild(svgEl("line", { x1: sx(xa), y1: sy(ya), x2: sx(xb), y2: sy(yb), stroke: "#1a1a1a", "stroke-width": 2, "stroke-dasharray": state.trend === "2023" ? "6 4" : "none", opacity: 0.8 }));
  }

  var pointsG = svgEl("g", {});
  METR.forEach(function (m) {
    var v = m[state.view], x = sx(decYear(m.date)), y = sy(v[0]);
    var g = svgEl("g", { "class": "pt", "data-key": m.key });
    if (state.ci) {
      var lo = Math.max(v[1], YMIN);
      g.appendChild(svgEl("line", { x1: x, x2: x, y1: sy(lo), y2: sy(v[2]), stroke: "#8a8a8a", "stroke-width": 1 }));
      if (v[1] >= YMIN) g.appendChild(svgEl("line", { x1: x - 3, x2: x + 3, y1: sy(lo), y2: sy(lo), stroke: "#8a8a8a" }));
      g.appendChild(svgEl("line", { x1: x - 3, x2: x + 3, y1: sy(v[2]), y2: sy(v[2]), stroke: "#8a8a8a" }));
    }
    g.appendChild(svgEl("circle", { cx: x, cy: y, r: 5, fill: m.sota ? "#b87018" : "#ffffff", stroke: m.sota ? "#ffffff" : "#b87018", "stroke-width": 2 }));
    g.appendChild(svgEl("circle", { "class": "hit", cx: x, cy: y, r: 12 }));
    g.addEventListener("mouseenter", function () { showItem(m.key, false); });
    g.addEventListener("click", function () { showItem(m.key, true); });
    pointsG.appendChild(g);
  });
  if (state.agents && state.view === "p80") {
    AGENTS.forEach(function (a) {
      var x = sx(a.x), y = sy(a.minutes);
      var g = svgEl("g", { "class": "pt", "data-key": a.key });
      g.appendChild(svgEl("rect", { x: x - 6, y: y - 6, width: 12, height: 12, fill: "#8a8a8a", stroke: "#ffffff", "stroke-width": 2 }));
      g.appendChild(svgEl("text", { "class": "lbl", x: x - 10, y: y + 4, "text-anchor": "end", "font-size": "11", fill: "#5a5a5a" }, a.name));
      g.appendChild(svgEl("rect", { "class": "hit", x: x - 12, y: y - 12, width: 24, height: 24 }));
      g.addEventListener("mouseenter", function () { showItem(a.key, false); });
      g.addEventListener("click", function () { showItem(a.key, true); });
      pointsG.appendChild(g);
    });
  }
  // A few direct labels so the chart reads without hovering.
  ["gpt_4", "claude_3_7_sonnet_inspect", "claude_mythos_preview_early_inspect"].forEach(function (k) {
    var m = METR.filter(function (q) { return q.key === k; })[0];
    var x = sx(decYear(m.date)), y = sy(m[state.view][0]);
    var right = x > W - 150;
    pointsG.appendChild(svgEl("text", { "class": "lbl", x: right ? x - 10 : x + 10, y: right ? y - 10 : y - 8, "text-anchor": right ? "end" : "start", "font-size": "11", fill: "#5a5a5a" }, m.name));
  });
  if (state.current) {
    var cur = pointsG.querySelector('[data-key="' + state.current + '"]');
    if (cur) { var ring = cur.querySelector("circle, rect"); if (ring) { var hl = svgEl("circle", { cx: ring.getAttribute("cx") || (+ring.getAttribute("x") + 6), cy: ring.getAttribute("cy") || (+ring.getAttribute("y") + 6), r: 9, fill: "none", stroke: "#1a1a1a", "stroke-width": 1.5 }); cur.insertBefore(hl, cur.firstChild); } }
  }
  svg.appendChild(pointsG);
  box.appendChild(svg);

  var legend = document.getElementById("legend");
  legend.textContent = "";
  var l1 = el("span"); l1.appendChild(mkSwatch("filled")); l1.appendChild(document.createTextNode("state of the art when measured (METR)")); legend.appendChild(l1);
  var l2 = el("span"); l2.appendChild(mkSwatch("hollow")); l2.appendChild(document.createTextNode("not state of the art (METR)")); legend.appendChild(l2);
  if (state.agents && state.view === "p80") { var l3 = el("span"); l3.appendChild(mkSwatch("square")); l3.appendChild(document.createTextNode("AI 2027 scenario agent (fictional)")); legend.appendChild(l3); }
  if (fit) { var l4 = el("span"); l4.appendChild(mkSwatch("line")); l4.appendChild(document.createTextNode("least-squares trend, " + (state.trend === "2023" ? "points from 2023 on" : "all points"))); legend.appendChild(l4); }

  var fitBox = document.getElementById("fit");
  fitBox.textContent = "";
  var s1 = el("div", "stat");
  s1.appendChild(el("div", "eyebrow", "Doubling time from this fit"));
  s1.appendChild(el("div", "big", fit ? Math.round(fit.doublingDays) + " days (" + (fit.doublingDays / 30.44).toFixed(1) + " months)" : "trend off"));
  s1.appendChild(el("div", "sub", fit ? "Fit over " + fit.n + " " + (state.view === "p50" ? "50%" : "80%") + "-horizon points" + (state.trend === "2023" ? " released from 2023 on" : "") + ", computed on this page." : "Choose a trend fit above."));
  fitBox.appendChild(s1);
  var s2 = el("div", "stat");
  s2.appendChild(el("div", "eyebrow", "METR's published doubling times"));
  s2.appendChild(el("div", "big", Math.round(METR_DOUBLING.allTime) + " days all-time"));
  s2.appendChild(el("div", "sub", Math.round(METR_DOUBLING.from2023) + " days from 2023 on (95% CI " + Math.round(METR_DOUBLING.from2023Low) + " to " + Math.round(METR_DOUBLING.from2023High) + "). Excludes points whose central 50% estimate is above 16 hours."));
  fitBox.appendChild(s2);
}
function mkSwatch(kind) {
  var s = svgEl("svg", { width: 18, height: 14, viewBox: "0 0 18 14", "aria-hidden": "true" });
  if (kind === "filled") s.appendChild(svgEl("circle", { cx: 9, cy: 7, r: 5, fill: "#b87018" }));
  else if (kind === "hollow") s.appendChild(svgEl("circle", { cx: 9, cy: 7, r: 4, fill: "#fff", stroke: "#b87018", "stroke-width": 2 }));
  else if (kind === "square") s.appendChild(svgEl("rect", { x: 3, y: 1, width: 12, height: 12, fill: "#8a8a8a" }));
  else s.appendChild(svgEl("line", { x1: 0, x2: 18, y1: 7, y2: 7, stroke: "#1a1a1a", "stroke-width": 2 }));
  return s;
}

function itemByKey(key) {
  for (var i = 0; i < METR.length; i++) if (METR[i].key === key) return { kind: "metr", item: METR[i] };
  for (var j = 0; j < AGENTS.length; j++) if (AGENTS[j].key === key) return { kind: "agent", item: AGENTS[j] };
  return null;
}
function showItem(key, commit) {
  var r = itemByKey(key); if (!r) return;
  var title = document.getElementById("d-title"), body = document.getElementById("d-body");
  if (r.kind === "metr") {
    var m = r.item;
    title.textContent = m.name;
    body.textContent = "Released " + fmtDate(m.date) + ". 50% horizon: " + fmtMin(m.p50[0]) + " (95% CI " + fmtMin(m.p50[1]) + " to " + fmtMin(m.p50[2]) + "). 80% horizon: " + fmtMin(m.p80[0]) + " (95% CI " + fmtMin(m.p80[1]) + " to " + fmtMin(m.p80[2]) + "). Average score on the suite: " + Math.round(m.score * 100) + "%. " + (m.sota ? "State of the art when measured." : "Not state of the art when measured.");
  } else {
    var a = r.item;
    title.textContent = a.name + " (AI 2027 scenario, fictional)";
    body.textContent = "Placed by ai-2027.com at " + a.x + " on the release-date axis (" + a.when + ") and at the 80% horizon level of about " + fmtMin(a.minutes) + " on its label scale. This is the authors' placement for a fictional system, not a METR measurement.";
  }
  if (commit) {
    state.current = key;
    if (!state.seen[key]) { state.seen[key] = true; }
    renderList(); drawChart(); persist();
  }
}

function renderList() {
  var list = document.getElementById("list");
  list.textContent = "";
  var items = METR.map(function (m) { return { key: m.key, label: m.name }; });
  if (state.agents && state.view === "p80") AGENTS.forEach(function (a) { items.push({ key: a.key, label: a.name + " (scenario)" }); });
  items.forEach(function (it, i) {
    var b = el("button", "", it.label); b.type = "button"; b.setAttribute("role", "listitem"); b.dataset.key = it.key;
    if (state.seen[it.key]) b.classList.add("is-seen");
    if (state.current === it.key) b.classList.add("is-current");
    b.addEventListener("click", function () { showItem(it.key, true); });
    b.addEventListener("focus", function () { showItem(it.key, false); });
    b.addEventListener("keydown", function (e) {
      var d = (e.key === "ArrowRight" || e.key === "ArrowDown") ? 1 : (e.key === "ArrowLeft" || e.key === "ArrowUp") ? -1 : 0;
      if (!d) return; e.preventDefault();
      var all = list.querySelectorAll("button"); var j = (i + d + all.length) % all.length; all[j].focus();
    });
    list.appendChild(b);
  });
}

function summary() {
  var fit = fitPoints();
  var seenNames = Object.keys(state.seen).map(function (k) { var r = itemByKey(k); return r ? (r.kind === "metr" ? r.item.name : r.item.name + " (scenario)") : k; });
  return "METR time-horizon chart. View: " + (state.view === "p50" ? "50%" : "80%") + " horizon; confidence intervals " + (state.ci ? "on" : "off") + "; AI 2027 scenario agents " + (state.agents ? "shown" : "hidden") + ". Trend fit: " + (fit ? (state.trend === "2023" ? "points from 2023 on" : "all points") + ", doubling time " + Math.round(fit.doublingDays) + " days" : "off") + " (METR publishes 188 days all-time and 129 days from 2023 on). Points the learner inspected: " + (seenNames.length ? seenNames.join(", ") : "none yet") + ". Views visited: " + Object.keys(state.views).join(", ") + ".";
}
function persist() {
  var seenCount = Object.keys(state.seen).length;
  var finished = seenCount >= 3 && state.views.p50 && state.views.p80;
  var done = document.getElementById("done");
  done.textContent = finished ? "You have compared both views and inspected " + seenCount + " points." : "To finish: look at both the 50% and 80% views and inspect at least three points (" + seenCount + " so far).";
  done.classList.toggle("is-visible", !!finished);
  if (window.Lens) {
    Lens.saveState({ view: state.view, trend: state.trend, ci: state.ci, agents: state.agents, seen: state.seen, views: state.views, current: state.current }, summary());
    if (finished && !completed) { completed = true; Lens.complete(); }
  } else {
    try { localStorage.setItem("ai-2027-metr-horizons", JSON.stringify(state)); } catch (e) {}
  }
}
function syncControls() {
  var vs = document.querySelectorAll("[data-view]"); for (var i = 0; i < vs.length; i++) vs[i].setAttribute("aria-checked", vs[i].dataset.view === state.view ? "true" : "false");
  var ts = document.querySelectorAll("[data-trend]"); for (var j = 0; j < ts.length; j++) ts[j].setAttribute("aria-checked", ts[j].dataset.trend === state.trend ? "true" : "false");
  document.getElementById("ci").setAttribute("aria-pressed", state.ci ? "true" : "false");
  document.getElementById("agents").setAttribute("aria-pressed", state.agents ? "true" : "false");
}
function renderAll() { state.views[state.view] = true; syncControls(); drawChart(); renderList(); }

var vbs = document.querySelectorAll("[data-view]");
for (var i = 0; i < vbs.length; i++) vbs[i].addEventListener("click", function () { state.view = this.dataset.view; renderAll(); persist(); });
var tbs = document.querySelectorAll("[data-trend]");
for (var j = 0; j < tbs.length; j++) tbs[j].addEventListener("click", function () { state.trend = this.dataset.trend; renderAll(); persist(); });
document.getElementById("ci").addEventListener("click", function () { state.ci = !state.ci; renderAll(); persist(); });
document.getElementById("agents").addEventListener("click", function () { state.agents = !state.agents; renderAll(); persist(); });

function hydrate(saved, meta) {
  if (saved && typeof saved === "object") {
    if (saved.view === "p50" || saved.view === "p80") state.view = saved.view;
    if (saved.trend === "all" || saved.trend === "2023" || saved.trend === "off") state.trend = saved.trend;
    if (typeof saved.ci === "boolean") state.ci = saved.ci;
    if (typeof saved.agents === "boolean") state.agents = saved.agents;
    if (saved.seen && typeof saved.seen === "object") state.seen = saved.seen;
    if (saved.views && typeof saved.views === "object") state.views = saved.views;
    if (typeof saved.current === "string" && itemByKey(saved.current)) state.current = saved.current;
  }
  completed = !!(meta && meta.completed);
  renderAll();
  if (state.current) showItem(state.current, false);
  persist();
}
if (window.Lens) { renderAll(); Lens.onState(hydrate); }
else { var s = null; try { s = JSON.parse(localStorage.getItem("ai-2027-metr-horizons")); } catch (e) {} hydrate(s, null); }
</script>
</body>
</html>

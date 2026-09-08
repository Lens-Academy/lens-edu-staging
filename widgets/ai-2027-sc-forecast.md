---
id: '6604a656-a88f-4422-9f0e-ed5a3bbc8348'
title: When does the superhuman coder arrive? The AI 2027 forecasts compared
summary_for_tutor: "An interactive replacement for the static 'Superhuman Coder Arrival, Benchmarks and Gaps' chart in the AI 2027 article. It shows, as ranges on a year axis from 2025 to beyond 2050, each forecaster's 10th percentile, median and 90th percentile for when a superhuman coder (SC) is developed, taken from the AI Futures timelines forecast's published tables and the figure's own printed percentiles: three forecasters (Eli Lifland, Nikola Jurkovic, the FutureSearch aggregate of three professional forecasters) across five forecasts (time-horizon-extension model of April 2025 and its May 2025 update, benchmarks-and-gaps model of April 2025 and its May 2025 update, and the all-things-considered forecast). The learner picks a forecast or shows all rows at once, and hovers or arrows through rows to read the exact numbers and the authors' notes (for example, the May 2025 update moved Eli's benchmarks-and-gaps median from Dec 2028 to Mar 2030; in the July 2025 note the authors say the updates 'push the median back 1.5 years while maintaining SC in 2027 as a serious possibility'). A vertical marker shows March 2027, when the scenario's SC arrives. Done means the learner has opened all five forecasts. Useful discussion: why medians sit later than the scenario date while every distribution still puts substantial weight on 2027, how wide the 80% intervals are, and what changed between April and May 2025."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Superhuman coder arrival forecasts</title>
<!-- Interactive replacement for the static chart "Superhuman Coder Arrival, Benchmarks and Gaps" (combined-headline) in the AI 2027 article (ai-2027.com, section "Why we forecast a superhuman coder in early 2027").
     Data sources, all retrieved 2026-09-08:
     1. AI 2027 Timelines Forecast, https://ai-2027.com/research/timelines-forecast: the summary table (median and 80% CI per forecaster and method) and the "2025 May 7 update" table (Eli's month-level medians, 80% CIs and modal years).
     2. The percentiles printed as text in the figure itself (10th, 50th, 90th for Eli, Nikola, FutureSearch under the benchmarks-and-gaps model).
     3. The article's own notes: "Added Jul 2025" and "added Dec 2025" remarks in the AI 2027 text.
     The full probability densities in the original figure are simulation output that the authors publish only as an image; this page draws the published percentiles instead of tracing the curves. Year-only figures are drawn at mid-year; month figures at mid-month. ">2050" and ">2100" are drawn as open arrows. -->
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
  .controls { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; margin-bottom: 8px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 6px; background: #fff; padding: 5px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button[aria-checked="true"] { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); font-weight: 600; }
  button.is-seen::before { content: "\2713 "; color: var(--accent); }
  .chart-box { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px; overflow-x: auto; }
  .chart-box svg { display: block; width: 100%; height: auto; min-width: 560px; font-family: var(--font-ui); }
  .axis text { font-size: 11px; fill: var(--muted); }
  .grid line { stroke: var(--border); stroke-width: 1; }
  .row { cursor: pointer; }
  .hit { fill: transparent; pointer-events: all; }
  .detail { margin-top: 10px; border: 1px solid var(--border); border-radius: 8px; padding: 12px 14px; background: var(--surface); min-height: 64px; }
  .detail h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
  .detail p { margin: 0 0 4px; }
  .list-wrap { margin-top: 12px; }
  .list { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 6px; }
  .list button { font-size: 12px; padding: 4px 8px; }
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
<h1>When does the superhuman coder arrive?</h1>
<p class="lede">The AI 2027 authors define a superhuman coder (SC) as "an AI system that can do any coding tasks that the best AGI company engineer does, while being much faster and cheaper." Each bar runs from a forecaster's 10th to 90th percentile for the year SC is developed, with the median marked. Pick a forecast, then hover or arrow through the rows.</p>

<div class="controls" role="radiogroup" aria-label="Forecast" id="methods"></div>

<div class="chart-box" id="chart-box"></div>
<div class="legend">
  <span><svg width="26" height="12" viewBox="0 0 26 12" aria-hidden="true"><line x1="1" y1="6" x2="25" y2="6" stroke="#8a8a8a" stroke-width="6"></line></svg>10th to 90th percentile</span>
  <span><svg width="14" height="14" viewBox="0 0 14 14" aria-hidden="true"><circle cx="7" cy="7" r="5" fill="#b87018"></circle></svg>median (50th percentile)</span>
  <span><svg width="14" height="14" viewBox="0 0 14 14" aria-hidden="true"><line x1="7" y1="0" x2="7" y2="14" stroke="#1a1a1a" stroke-dasharray="3 2"></line></svg>Mar 2027, when SC arrives in the scenario</span>
  <span>an arrow means the 90th percentile is beyond the axis (given as ">2050")</span>
</div>

<div class="detail" id="detail" aria-live="polite">
  <h2 id="d-title">Hover a bar, or use the list below</h2>
  <p id="d-body">Three forecasters, five forecasts. The article's own summary: "All forecasters place 2027 as one of the most likely years in which an SC might be developed."</p>
  <p id="d-note"></p>
</div>

<div class="list-wrap">
  <p class="eyebrow">Rows (arrow keys move between them)</p>
  <div class="list" id="list" role="list"></div>
</div>
<p class="done" id="done"></p>

<div class="foot">
  <p>Data: AI Futures Project, <a href="https://ai-2027.com/research/timelines-forecast" target="_blank" rel="noopener">Timelines Forecast</a> (Eli Lifland, Nikola Jurkovic, FutureSearch, April 2025, with the 7 May 2025 update), summary tables and the percentiles printed in the "Superhuman Coder Arrival, Benchmarks and Gaps" figure; retrieved 8 Sep 2026. The forecasts assume "no large-scale catastrophes happen (e.g., a solar flare, a pandemic, nuclear war), no government or self-imposed slowdown, and no significant supply chain disruptions."</p>
  <p>The original figure also draws full probability curves from the authors' simulation; those are published only as an image, so this page shows the published percentiles. Year-only figures are drawn at mid-year. The authors' 31 Dec 2025 note points to a revamped model at aifuturesmodel.com.</p>
</div>

<script>
// Each row: p10, p50, p90 as [year, month] (month 0 = year only); p90 null = ">2050" open arrow (p90open holds the printed text).
var METHODS = [
  { id: "the-apr", label: "Time-horizon extension (Apr 2025)",
    about: "Method 1: extends the trend in METR's time-horizon report until the horizon and reliability needed for SC are reached, with adjustments for cost and speed and for the gap between internal and public models.",
    rows: [
      { who: "Eli (AI 2027 author)", p10: [2025, 10], p50: [2027, 8], p90: [2039, 0], text: "median 2027, 80% CI 2025 to 2039; month detail from the May 2025 update table: Aug 2027 (Oct 2025 to 2039), modal year 2026" },
      { who: "Nikola", p10: [2025, 0], p50: [2027, 0], p90: [2033, 0], text: "median 2027, 80% CI 2025 to 2033" }
    ] },
  { id: "the-may", label: "Time-horizon extension, updated (May 2025)",
    about: "Eli's 7 May 2025 update of Method 1. Largest change: modelling software progress with diminishing returns (13 month increase in the median); the update also makes superexponential growth more likely at higher time horizons rather than fixed at the start.",
    rows: [
      { who: "Eli (AI 2027 author)", p10: [2026, 4], p50: [2029, 2], p90: [2052, 0], text: "Feb 2029 (Apr 2026 to 2052), modal year 2027; the summary table rounds this to 2029 (2026 to 2052)" }
    ] },
  { id: "bag-apr", label: "Benchmarks and gaps (Apr 2025)",
    about: "Method 2, the chart in the article: forecast when RE-Bench saturates, then how long it takes to cross the gaps between that and real-world work at the best AGI company (engineering complexity, feedback loops, parallel projects, specialization, cost and speed, other gaps).",
    rows: [
      { who: "Eli (AI 2027 author)", p10: [2025, 12], p50: [2028, 12], p90: null, p90open: ">2050", text: "figure percentiles: 10th Dec 2025, 50th Dec 2028, 90th >2050; summary table: 2028 (2025 to >2050); modal year 2027" },
      { who: "Nikola", p10: [2025, 10], p50: [2027, 10], p90: [2044, 6], text: "figure percentiles: 10th Oct 2025, 50th Oct 2027, 90th Jun 2044; summary table: 2027 (2025 to 2044)" },
      { who: "FutureSearch aggregate (n=3)", p10: [2026, 6], p50: [2032, 1], p90: null, p90open: ">2050", text: "figure percentiles: 10th Jun 2026, 50th Jan 2032, 90th >2050; summary table: 2032 (2026 to >2050)" }
    ] },
  { id: "bag-may", label: "Benchmarks and gaps, updated (May 2025)",
    about: "Eli's 7 May 2025 update of Method 2. Median moved by about 15 months in total; the biggest single change (8 months) was the diminishing-returns modelling of software progress. Eli: \"I place significantly more weight on the benchmarks and gaps model because I think it's useful to explicitly model the gaps rather than simply adjusting the required time horizon for them.\"",
    rows: [
      { who: "Eli (AI 2027 author)", p10: [2026, 2], p50: [2030, 3], p90: [2095, 0], text: "Mar 2030 (Feb 2026 to 2095); modal years 2027 and 2028 are about equal; the summary table rounds this to 2030 (2026 to 2095)" }
    ] },
  { id: "atc", label: "All-things-considered (Apr 2025)",
    about: "Each forecaster's overall view after adjusting for factors outside the two models, such as geopolitics and macroeconomics. The article's Dec 2025 note: \"adjusting for outside of model factors gave us slightly longer medians, e.g. Eli's was 2030\".",
    rows: [
      { who: "Eli (AI 2027 author)", p10: [2026, 0], p50: [2030, 0], p90: null, p90open: ">2050", text: "2030 (2026 to >2050); the 90th percentile was edited from 2050 to >2050 four days after publication" },
      { who: "Nikola", p10: [2026, 0], p50: [2028, 0], p90: [2040, 0], text: "2028 (2026 to 2040)" },
      { who: "FutureSearch aggregate (n=3)", p10: [2027, 0], p50: [2033, 0], p90: null, p90open: ">2050", text: "2033 (2027 to >2050)" }
    ] }
];
var ALL_ID = "all";
var W = 780, ML = 200, MR = 56, MT = 26, MB = 34, ROWH = 34;
var X0 = 2025, X1 = 2056;
var SVGNS = "http://www.w3.org/2000/svg";
var MONTHS = ["", "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
var state = { method: "bag-apr", seen: {}, current: null };
var completed = false;

function el(tag, className, text) { var n = document.createElement(tag); if (className) n.className = className; if (text !== undefined) n.textContent = text; return n; }
function svgEl(tag, attrs, text) { var n = document.createElementNS(SVGNS, tag); for (var k in attrs) n.setAttribute(k, attrs[k]); if (text !== undefined) n.textContent = text; return n; }
function yearOf(ym) { return ym[1] ? ym[0] + (ym[1] - 0.5) / 12 : ym[0] + 0.5; }
function fmt(ym) { return ym[1] ? MONTHS[ym[1]] + " " + ym[0] : String(ym[0]); }
function sx(year) { return ML + (Math.min(year, X1) - X0) / (X1 - X0) * (W - ML - MR); }
function visibleRows() {
  var out = [];
  METHODS.forEach(function (m) { if (state.method === ALL_ID || m.id === state.method) m.rows.forEach(function (r, i) { out.push({ method: m, row: r, key: m.id + "|" + i }); }); });
  return out;
}
function methodById(id) { for (var i = 0; i < METHODS.length; i++) if (METHODS[i].id === id) return METHODS[i]; return null; }

function renderControls() {
  var wrap = document.getElementById("methods");
  wrap.textContent = "";
  METHODS.concat([{ id: ALL_ID, label: "All forecasts" }]).forEach(function (m) {
    var b = el("button", "", m.label); b.type = "button"; b.setAttribute("role", "radio");
    b.setAttribute("aria-checked", state.method === m.id ? "true" : "false");
    if (m.id !== ALL_ID && state.seen[m.id]) b.classList.add("is-seen");
    b.addEventListener("click", function () { state.method = m.id; state.current = null; resetDetail(); renderAll(); persist(); });
    wrap.appendChild(b);
  });
}
function drawChart() {
  var rows = visibleRows();
  var H = MT + rows.length * ROWH + MB;
  var box = document.getElementById("chart-box");
  box.textContent = "";
  var svg = svgEl("svg", { viewBox: "0 0 " + W + " " + H, role: "img", "aria-label": "Range chart of forecast percentiles for superhuman coder arrival, by forecaster" });
  var grid = svgEl("g", { "class": "grid" }), axis = svgEl("g", { "class": "axis" });
  for (var yr = 2025; yr <= 2055; yr += 5) {
    var x = sx(yr);
    grid.appendChild(svgEl("line", { x1: x, x2: x, y1: MT - 6, y2: H - MB }));
    axis.appendChild(svgEl("text", { x: x, y: H - MB + 16, "text-anchor": "middle" }, String(yr)));
  }
  axis.appendChild(svgEl("text", { x: W - MR + 20, y: H - MB + 16, "text-anchor": "start" }, "later"));
  svg.appendChild(grid); svg.appendChild(axis);
  var xm = sx(2027 + 2.5 / 12);
  svg.appendChild(svgEl("line", { x1: xm, x2: xm, y1: MT - 6, y2: H - MB, stroke: "#1a1a1a", "stroke-dasharray": "3 2" }));
  svg.appendChild(svgEl("text", { x: xm + 4, y: MT - 10, "font-size": "11", fill: "#5a5a5a" }, "Mar 2027 (scenario)"));

  rows.forEach(function (it, i) {
    var r = it.row, y = MT + i * ROWH + ROWH / 2;
    var g = svgEl("g", { "class": "row", "data-key": it.key });
    if (state.current === it.key) g.appendChild(svgEl("rect", { x: 2, y: y - ROWH / 2 + 1, width: W - 4, height: ROWH - 2, fill: "#faf8f3", stroke: "#b87018", rx: 6 }));
    var label = r.who + (state.method === ALL_ID ? " (" + it.method.label.replace(" (Apr 2025)", ", Apr").replace(", updated (May 2025)", ", May") + ")" : "");
    var lab = svgEl("text", { x: ML - 8, y: y + 4, "text-anchor": "end", "font-size": "11", fill: "#1a1a1a" }, label.length > 33 ? label.slice(0, 32) + "…" : label);
    g.appendChild(lab);
    var x10 = sx(yearOf(r.p10)), x90 = r.p90 ? sx(yearOf(r.p90)) : sx(X1), x50 = sx(yearOf(r.p50));
    g.appendChild(svgEl("line", { x1: x10, x2: x90, y1: y, y2: y, stroke: "#8a8a8a", "stroke-width": 8, "stroke-linecap": "round" }));
    if (!r.p90) g.appendChild(svgEl("polygon", { points: (x90 + 2) + "," + (y - 8) + " " + (x90 + 14) + "," + y + " " + (x90 + 2) + "," + (y + 8), fill: "#8a8a8a" }));
    else if (yearOf(r.p90) > X1) g.appendChild(svgEl("polygon", { points: (x90 + 2) + "," + (y - 8) + " " + (x90 + 14) + "," + y + " " + (x90 + 2) + "," + (y + 8), fill: "#8a8a8a" }));
    g.appendChild(svgEl("circle", { cx: x50, cy: y, r: 6, fill: "#b87018", stroke: "#fff", "stroke-width": 2 }));
    g.appendChild(svgEl("text", { x: x50, y: y - 9, "text-anchor": "middle", "font-size": "10", fill: "#5a5a5a" }, fmt(r.p50)));
    g.appendChild(svgEl("rect", { "class": "hit", x: 0, y: y - ROWH / 2, width: W, height: ROWH }));
    g.addEventListener("mouseenter", function () { showRow(it, false); });
    g.addEventListener("click", function () { showRow(it, true); });
    svg.appendChild(g);
  });
  box.appendChild(svg);
}
function resetDetail() {
  document.getElementById("d-title").textContent = "Hover a bar, or use the list below";
  document.getElementById("d-body").textContent = "Three forecasters, five forecasts. The article's own summary: \"All forecasters place 2027 as one of the most likely years in which an SC might be developed.\"";
  document.getElementById("d-note").textContent = state.method === ALL_ID ? "" : methodById(state.method).about;
}
function showRow(it, commit) {
  var r = it.row;
  document.getElementById("d-title").textContent = r.who + ": " + it.method.label;
  document.getElementById("d-body").textContent = "10th percentile " + fmt(r.p10) + ", median " + fmt(r.p50) + ", 90th percentile " + (r.p90 ? fmt(r.p90) : r.p90open) + ". As published: " + r.text + ".";
  document.getElementById("d-note").textContent = it.method.about;
  if (commit) { state.current = it.key; renderList(); drawChart(); persist(); }
}
function renderList() {
  var list = document.getElementById("list");
  list.textContent = "";
  var rows = visibleRows();
  rows.forEach(function (it, i) {
    var b = el("button", "", it.row.who + (state.method === ALL_ID ? ", " + it.method.label : "")); b.type = "button"; b.setAttribute("role", "listitem");
    if (state.current === it.key) b.classList.add("is-current");
    b.addEventListener("click", function () { showRow(it, true); });
    b.addEventListener("focus", function () { showRow(it, false); });
    b.addEventListener("keydown", function (e) {
      var d = (e.key === "ArrowRight" || e.key === "ArrowDown") ? 1 : (e.key === "ArrowLeft" || e.key === "ArrowUp") ? -1 : 0;
      if (!d) return; e.preventDefault();
      var all = list.querySelectorAll("button"); all[(i + d + all.length) % all.length].focus();
    });
    list.appendChild(b);
  });
}
function summary() {
  var rows = visibleRows();
  var s = "Superhuman-coder arrival forecasts. Showing: " + (state.method === ALL_ID ? "all forecasts" : methodById(state.method).label) + ". Rows: " + rows.map(function (it) { return it.row.who + (state.method === ALL_ID ? " / " + it.method.label : "") + ": 10th " + fmt(it.row.p10) + ", median " + fmt(it.row.p50) + ", 90th " + (it.row.p90 ? fmt(it.row.p90) : it.row.p90open); }).join("; ") + ". Forecasts opened so far: " + Object.keys(state.seen).map(function (k) { return methodById(k).label; }).join("; ") + ".";
  if (state.current) { var cur = rows.filter(function (it) { return it.key === state.current; })[0]; if (cur) s += " Row selected: " + cur.row.who + ", " + cur.method.label + "."; }
  return s;
}
function persist() {
  var n = Object.keys(state.seen).length, finished = n >= METHODS.length;
  var done = document.getElementById("done");
  done.textContent = finished ? "You have opened all five forecasts." : "To finish: open all five forecasts (" + n + " of " + METHODS.length + " so far).";
  done.classList.toggle("is-visible", finished);
  if (window.Lens) {
    Lens.saveState({ method: state.method, seen: state.seen, current: state.current }, summary());
    if (finished && !completed) { completed = true; Lens.complete(); }
  } else { try { localStorage.setItem("ai-2027-sc-forecast", JSON.stringify(state)); } catch (e) {} }
}
function renderAll() {
  if (state.method === ALL_ID) METHODS.forEach(function (m) { state.seen[m.id] = true; }); else state.seen[state.method] = true;
  renderControls(); drawChart(); renderList();
}
function hydrate(saved, meta) {
  if (saved && typeof saved === "object") {
    if (saved.method === ALL_ID || methodById(saved.method)) state.method = saved.method;
    if (saved.seen && typeof saved.seen === "object") state.seen = saved.seen;
    if (typeof saved.current === "string") state.current = saved.current;
  }
  completed = !!(meta && meta.completed);
  renderAll();
  var cur = state.current ? visibleRows().filter(function (it) { return it.key === state.current; })[0] : null;
  if (cur) showRow(cur, false); else { state.current = null; resetDetail(); }
  persist();
}
if (window.Lens) { renderAll(); Lens.onState(hydrate); }
else { var s0 = null; try { s0 = JSON.parse(localStorage.getItem("ai-2027-sc-forecast")); } catch (e) {} hydrate(s0, null); }
</script>
</body>
</html>

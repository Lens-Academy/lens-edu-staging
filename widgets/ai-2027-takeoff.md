---
id: 'acb0740b-ea27-46e5-9ca2-ec6f6bee7a8e'
title: From superhuman coder to superintelligence, the AI 2027 takeoff forecast
summary_for_tutor: "An interactive replacement for the static 'AI Takeoff Forecast, Assuming Superhuman Coder in Mar 2027' chart in the AI 2027 article (September 2027 section). The learner steps through four capability milestones, superhuman coder (SC), superhuman AI researcher (SAR), superintelligent AI researcher (SIAR) and artificial superintelligence (ASI), on a timeline from 2027 onward. For each milestone the page shows the date it is reached in the scenario's racing ending (Mar, Aug, Nov, Dec 2027), the authors' forecast conditional on SC in March 2027 as 10th percentile, median and 90th percentile (SAR: Mar 2027, Jul 2027, Mar 2028; SIAR: May 2027, Nov 2027, Jan 2034; ASI: Jun 2027, Apr 2028, beyond 2100), the human-only, software-only time the authors estimate for the next step (SC to SAR: 15% chance of 0 years, otherwise 4 years with 80% CI 1.5 to 10; SAR to SIAR: 19 years, 2.3 to 380; SIAR to ASI: 95 years, 2.4 to 1,000,000) and the AI R&D progress multiplier at that milestone (5x, 25x, 250x, 2,000x). Data come from the takeoff forecast's published table and the percentiles printed in the figure; the figure's probability curves are not reproduced. Done means the learner has viewed all four milestones. Useful discussion: how a 19-year human-only gap becomes four months in the scenario (the multiplier), why the intervals widen so fast (SIAR's 90th percentile is 2034, ASI's is beyond 2100), and what the scenario's dates being earlier than the medians implies."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The AI 2027 takeoff forecast</title>
<!-- Interactive replacement for the static chart "AI Takeoff Forecast, Assuming Superhuman Coder in Mar 2027" (takeoff-timeline) in the AI 2027 article (ai-2027.com, section "September 2027: Agent-4, the Superhuman AI Researcher", box "How we're forecasting the capability progression beyond superhuman coders").
     Data sources, retrieved 2026-09-08:
     1. The article's own milestone table (definitions and "Date achieved in scenario, racing ending").
     2. AI 2027 Takeoff Forecast, https://ai-2027.com/research/takeoff-forecast: the summary table ("Projected date conditional on SC in Mar 2027 (median + 80% CI)", "Human-only, software-only time until next milestone", "AI R&D progress multiplier") and the percentiles printed in the figure (10th, 50th, 90th per milestone).
     The figure's probability densities are simulation output published only as an image and are not traced here. Months are drawn at mid-month; "2034" (year only) at mid-year; ">2100" as an open arrow. -->
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
  button:disabled { opacity: 0.5; cursor: default; }
  button[aria-checked="true"] { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); font-weight: 600; }
  button.is-seen::before { content: "\2713 "; color: var(--accent); }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  .chart-box { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px; overflow-x: auto; }
  .chart-box svg { display: block; width: 100%; height: auto; min-width: 560px; font-family: var(--font-ui); }
  .axis text { font-size: 11px; fill: var(--muted); }
  .grid line { stroke: var(--border); stroke-width: 1; }
  .row { cursor: pointer; }
  .hit { fill: transparent; pointer-events: all; }
  .legend { display: flex; flex-wrap: wrap; gap: 14px; margin-top: 8px; font-size: 12px; color: var(--muted); align-items: center; }
  .legend span { display: inline-flex; align-items: center; gap: 6px; }
  .detail { margin-top: 10px; border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; background: var(--surface); }
  .detail h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 0 0 6px; }
  .detail p { margin: 0 0 6px; }
  .facts { display: grid; gap: 8px; margin-top: 8px; }
  @media (min-width: 640px) { .facts { grid-template-columns: 1fr 1fr; } }
  .fact { border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: #fff; }
  .fact .big { font-family: var(--font-heading); font-size: 20px; font-weight: 600; }
  .fact .sub { color: var(--muted); font-size: 12px; }
  .nav { display: flex; gap: 8px; justify-content: space-between; margin-top: 10px; flex-wrap: wrap; }
  .foot { margin-top: 12px; font-size: 12px; color: var(--muted); }
  .foot p { margin: 0 0 6px; }
  a { color: var(--accent); }
  .done { margin-top: 10px; font-size: 12px; color: var(--muted); }
  .done.is-visible::before { content: "\2713 "; color: var(--accent); }
</style>
</head>
<body>
<p class="eyebrow">Interactive chart</p>
<h1>From superhuman coder to superintelligence</h1>
<p class="lede">The AI 2027 authors forecast takeoff, "the time between a superhuman coder and wildly superhuman capabilities", one milestone at a time, conditional on a superhuman coder in March 2027 and assuming no increases in training compute. Step through the milestones; each bar runs from the 10th to the 90th percentile, and the diamond marks the date in the scenario's racing ending.</p>

<div class="controls" role="radiogroup" aria-label="Milestone" id="milestones"></div>

<div class="chart-box" id="chart-box"></div>
<div class="legend">
  <span><svg width="26" height="12" viewBox="0 0 26 12" aria-hidden="true"><line x1="1" y1="6" x2="25" y2="6" stroke="#8a8a8a" stroke-width="6"></line></svg>10th to 90th percentile, forecast</span>
  <span><svg width="14" height="14" viewBox="0 0 14 14" aria-hidden="true"><circle cx="7" cy="7" r="5" fill="#1a1a1a"></circle></svg>median, forecast</span>
  <span><svg width="14" height="14" viewBox="0 0 14 14" aria-hidden="true"><polygon points="7,1 13,7 7,13 1,7" fill="none" stroke="#b87018" stroke-width="2"></polygon></svg>date in the scenario (racing ending)</span>
  <span>an arrow means the 90th percentile is beyond the axis</span>
</div>

<div class="detail" id="detail" aria-live="polite">
  <p class="eyebrow" id="d-eyebrow"></p>
  <h2 id="d-title"></h2>
  <p id="d-def"></p>
  <div class="facts" id="facts"></div>
  <div class="nav">
    <button type="button" id="prev">Previous milestone</button>
    <button type="button" id="next" class="primary">Next milestone</button>
  </div>
</div>
<p class="done" id="done"></p>

<div class="foot">
  <p>Data: the AI 2027 article's milestone table and the AI Futures Project <a href="https://ai-2027.com/research/takeoff-forecast" target="_blank" rel="noopener">Takeoff Forecast</a> (Daniel Kokotajlo, Eli Lifland, April 2025), summary table and the percentiles printed in its figure; retrieved 8 Sep 2026. The authors: "Our median forecast for the time from the superhuman coder milestone (achieved in Mar 2027) to artificial superintelligence is ~1 year, with wide error margins."</p>
  <p>How each gap is forecast, in the article's words: "1. Forecasting how long it would take to get from A to B with only humans working on software improvements. 2. Forecasting how much AI automation will speed this up, then correspondingly adjusting the estimate from (1) to be faster." The figure's probability curves are simulation output published only as an image; this page draws the published percentiles.</p>
</div>

<script>
var MILESTONES = [
  { id: "sc", short: "SC", name: "Superhuman coder (SC)",
    def: "An AI system that can do the job of the best human coder on tasks involved in AI research but faster, and cheaply enough to run lots of copies.",
    scenario: [2027, 3], p10: [2027, 3], p50: [2027, 3], p90: [2027, 3], conditioned: true,
    forecastText: "Mar 2027 (the forecast is conditional on this)",
    humanOnly: "SC to SAR: 15% 0 years; otherwise 4 years (80% CI: 1.5 to 10; lognormal)", humanOnlyShort: "4 years", humanOnlySub: "SC to SAR, human-only and software-only: 15% chance of 0 years; otherwise 4 years, 80% CI 1.5 to 10 years",
    multiplier: "5", multiplierSub: "algorithmic progress speedup from AI vs. humans-only, once SC exists" },
  { id: "sar", short: "SAR", name: "Superhuman AI researcher (SAR)",
    def: "The same as SC but for all cognitive AI research tasks.",
    scenario: [2027, 8], p10: [2027, 3], p50: [2027, 7], p90: [2028, 3],
    forecastText: "Jul 2027 (Mar 2027 to Mar 2028)",
    humanOnlyShort: "19 years", humanOnlySub: "SAR to SIAR, human-only and software-only: 19 years, 80% CI 2.3 to 380 years",
    multiplier: "25", multiplierSub: "algorithmic progress speedup from AI vs. humans-only, once SAR exists" },
  { id: "siar", short: "SIAR", name: "Superintelligent AI researcher (SIAR)",
    def: "An AI system that is vastly better than the best human researcher at AI research.",
    scenario: [2027, 11], p10: [2027, 5], p50: [2027, 11], p90: [2034, 1],
    forecastText: "Nov 2027 (May 2027 to 2034); figure percentiles May 2027, Nov 2027, Jan 2034",
    humanOnlyShort: "95 years", humanOnlySub: "SIAR to ASI, human-only and software-only: 95 years, 80% CI 2.4 to 1,000,000 years",
    multiplier: "250", multiplierSub: "algorithmic progress speedup from AI vs. humans-only, once SIAR exists" },
  { id: "asi", short: "ASI", name: "Artificial superintelligence (ASI)",
    def: "An AI system that is much better than the best human at every cognitive task.",
    scenario: [2027, 12], p10: [2027, 6], p50: [2028, 4], p90: null, p90open: ">2100",
    forecastText: "Apr 2028 (Jun 2027 to >2100)",
    humanOnlyShort: "n/a", humanOnlySub: "ASI is the last milestone in this forecast",
    multiplier: "2,000", multiplierSub: "algorithmic progress speedup from AI vs. humans-only, once ASI exists" }
];
var W = 780, ML = 200, MR = 56, MT = 26, MB = 34, ROWH = 40;
var X0 = 2027, X1 = 2035;
var SVGNS = "http://www.w3.org/2000/svg";
var MONTHS = ["", "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
var state = { step: 0, seen: {} };
var completed = false;

function el(tag, className, text) { var n = document.createElement(tag); if (className) n.className = className; if (text !== undefined) n.textContent = text; return n; }
function svgEl(tag, attrs, text) { var n = document.createElementNS(SVGNS, tag); for (var k in attrs) n.setAttribute(k, attrs[k]); if (text !== undefined) n.textContent = text; return n; }
function yearOf(ym) { return ym[1] ? ym[0] + (ym[1] - 0.5) / 12 : ym[0] + 0.5; }
function fmt(ym) { return ym[1] ? MONTHS[ym[1]] + " " + ym[0] : String(ym[0]); }
function sx(year) { return ML + (Math.min(year, X1) - X0) / (X1 - X0) * (W - ML - MR); }

function renderControls() {
  var wrap = document.getElementById("milestones");
  wrap.textContent = "";
  MILESTONES.forEach(function (m, i) {
    var b = el("button", "", m.name); b.type = "button"; b.setAttribute("role", "radio");
    b.setAttribute("aria-checked", state.step === i ? "true" : "false");
    if (state.seen[m.id]) b.classList.add("is-seen");
    b.addEventListener("click", function () { go(i); });
    wrap.appendChild(b);
  });
}
function drawChart() {
  var H = MT + MILESTONES.length * ROWH + MB;
  var box = document.getElementById("chart-box");
  box.textContent = "";
  var svg = svgEl("svg", { viewBox: "0 0 " + W + " " + H, role: "img", "aria-label": "Timeline of takeoff milestones with forecast percentiles and scenario dates" });
  var grid = svgEl("g", { "class": "grid" }), axis = svgEl("g", { "class": "axis" });
  for (var yr = X0; yr <= X1; yr++) {
    var x = sx(yr);
    grid.appendChild(svgEl("line", { x1: x, x2: x, y1: MT - 6, y2: H - MB }));
    axis.appendChild(svgEl("text", { x: x, y: H - MB + 16, "text-anchor": "middle" }, String(yr)));
  }
  axis.appendChild(svgEl("text", { x: W - MR + 20, y: H - MB + 16, "text-anchor": "start" }, "later"));
  svg.appendChild(grid); svg.appendChild(axis);
  MILESTONES.forEach(function (m, i) {
    var y = MT + i * ROWH + ROWH / 2;
    var g = svgEl("g", { "class": "row" });
    if (state.step === i) g.appendChild(svgEl("rect", { x: 2, y: y - ROWH / 2 + 1, width: W - 4, height: ROWH - 2, fill: "#faf8f3", stroke: "#b87018", rx: 6 }));
    g.appendChild(svgEl("text", { x: ML - 8, y: y + 4, "text-anchor": "end", "font-size": "11", fill: "#1a1a1a" }, m.name.replace(/ \(.*\)$/, "")));
    var x10 = sx(yearOf(m.p10)), x50 = sx(yearOf(m.p50)), x90 = m.p90 ? sx(yearOf(m.p90)) : sx(X1);
    if (!m.conditioned) {
      g.appendChild(svgEl("line", { x1: x10, x2: x90, y1: y, y2: y, stroke: "#8a8a8a", "stroke-width": 8, "stroke-linecap": "round" }));
      if (!m.p90) g.appendChild(svgEl("polygon", { points: (x90 + 2) + "," + (y - 8) + " " + (x90 + 14) + "," + y + " " + (x90 + 2) + "," + (y + 8), fill: "#8a8a8a" }));
      g.appendChild(svgEl("circle", { cx: x50, cy: y, r: 6, fill: "#1a1a1a", stroke: "#fff", "stroke-width": 2 }));
      g.appendChild(svgEl("text", { x: x50, y: y - 10, "text-anchor": "middle", "font-size": "10", fill: "#5a5a5a" }, "median " + fmt(m.p50)));
    } else {
      g.appendChild(svgEl("text", { x: x50 + 12, y: y + 4, "font-size": "10", fill: "#5a5a5a" }, "assumed: SC in Mar 2027"));
    }
    var xs = sx(yearOf(m.scenario));
    g.appendChild(svgEl("polygon", { points: xs + "," + (y - 9) + " " + (xs + 9) + "," + y + " " + xs + "," + (y + 9) + " " + (xs - 9) + "," + y, fill: "none", stroke: "#b87018", "stroke-width": 2.5 }));
    g.appendChild(svgEl("rect", { "class": "hit", x: 0, y: y - ROWH / 2, width: W, height: ROWH }));
    g.addEventListener("click", function () { go(i); });
    svg.appendChild(g);
  });
  box.appendChild(svg);
}
function renderDetail() {
  var m = MILESTONES[state.step];
  document.getElementById("d-eyebrow").textContent = "Milestone " + (state.step + 1) + " of " + MILESTONES.length;
  document.getElementById("d-title").textContent = m.name;
  document.getElementById("d-def").textContent = m.def;
  var facts = document.getElementById("facts");
  facts.textContent = "";
  [
    ["In the scenario (racing ending)", fmt(m.scenario), "date achieved in AI 2027's racing ending"],
    ["Forecast, conditional on SC in Mar 2027", m.conditioned ? "Mar 2027" : fmt(m.p50), m.conditioned ? m.forecastText : "median; 10th percentile " + fmt(m.p10) + ", 90th percentile " + (m.p90 ? fmt(m.p90) : m.p90open) + "; published as " + m.forecastText],
    ["Human-only time to the next milestone", m.humanOnlyShort, m.humanOnlySub],
    ["AI R&D progress multiplier", m.multiplier + "x", m.multiplierSub]
  ].forEach(function (f) {
    var d = el("div", "fact");
    d.appendChild(el("div", "eyebrow", f[0]));
    d.appendChild(el("div", "big", f[1]));
    d.appendChild(el("div", "sub", f[2]));
    facts.appendChild(d);
  });
  document.getElementById("prev").disabled = state.step === 0;
  document.getElementById("next").disabled = state.step === MILESTONES.length - 1;
}
function go(i) { state.step = Math.max(0, Math.min(MILESTONES.length - 1, i)); state.seen[MILESTONES[state.step].id] = true; renderAll(); persist(); }
function summary() {
  var m = MILESTONES[state.step];
  return "AI 2027 takeoff forecast stepper. Current milestone: " + m.name + " (scenario date " + fmt(m.scenario) + "; forecast " + m.forecastText + "; human-only time to next milestone " + m.humanOnlyShort + "; AI R&D progress multiplier " + m.multiplier + "x). Milestones viewed: " + MILESTONES.filter(function (q) { return state.seen[q.id]; }).map(function (q) { return q.short; }).join(", ") + " of SC, SAR, SIAR, ASI.";
}
function persist() {
  var n = Object.keys(state.seen).length, finished = n >= MILESTONES.length;
  var done = document.getElementById("done");
  done.textContent = finished ? "You have stepped through all four milestones." : "To finish: view all four milestones (" + n + " so far).";
  done.classList.toggle("is-visible", finished);
  if (window.Lens) {
    Lens.saveState({ step: state.step, seen: state.seen }, summary());
    if (finished && !completed) { completed = true; Lens.complete(); }
  } else { try { localStorage.setItem("ai-2027-takeoff", JSON.stringify(state)); } catch (e) {} }
}
function renderAll() { state.seen[MILESTONES[state.step].id] = true; renderControls(); drawChart(); renderDetail(); }
document.getElementById("prev").addEventListener("click", function () { go(state.step - 1); });
document.getElementById("next").addEventListener("click", function () { go(state.step + 1); });
function hydrate(saved, meta) {
  if (saved && typeof saved === "object") {
    if (typeof saved.step === "number" && saved.step >= 0 && saved.step < MILESTONES.length) state.step = saved.step;
    if (saved.seen && typeof saved.seen === "object") state.seen = saved.seen;
  }
  completed = !!(meta && meta.completed);
  renderAll(); persist();
}
if (window.Lens) { renderAll(); Lens.onState(hydrate); }
else { var s0 = null; try { s0 = JSON.parse(localStorage.getItem("ai-2027-takeoff")); } catch (e) {} hydrate(s0, null); }
</script>
</body>
</html>

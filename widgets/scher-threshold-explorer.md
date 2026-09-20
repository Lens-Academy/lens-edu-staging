---
id: '85a67a3c-4621-480d-afa5-cee2967bdbaf'
title: Thresholds, cluster sizes and the verification levers
summary_for_tutor: "An interactive of Tables 1 and 2 and Figure 2 of Scher et al.'s draft international agreement. The learner sets the Strict Threshold (paper default 1e24 FLOP) and the Monitored Threshold (paper default 1e22 FLOP) on log sliders, and picks one of the six cluster sizes the paper tabulates (100,000, 10,000, 1,000, 100, 16 and 1 H100-equivalents). Time to each threshold is recomputed from the paper's own arithmetic, seconds = threshold FLOP divided by (chips x 9.9e14 FLOP/s), where 9.9e14 FLOP/s is one H100-equivalent at FP8 and 50 percent utilization; that formula reproduces every seconds and days cell of both tables, including the 7.3 days to 1e22 FLOP for 16 chips that the paper uses to justify drawing the covered chip cluster line at 16. The widget also shows when a cluster of that size gets registered, the two tables' levers side by side (domestic round-up against international verification, marked very useful or somewhat useful for the chosen size), and the eleven labelled models of Figure 2 on a log ladder, each one above the Strict Threshold, between the two thresholds, or below the Monitored Threshold as the learner moves them. Selecting a model gives its compute, its Artificial Analysis Intelligence Index score and how far it sits from the threshold. Done fires once the learner has moved a threshold and changed the cluster size. The lesson page around it carries the paper's own Tables 1 and 2, the prose describing each lever, and Figure 2 with its caption, so the widget itself has no title, caption or lede; quote the paper's table from the page, not from the widget."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Thresholds, cluster sizes and the verification levers</title>
<!-- Built from articles/scher-an-international-agreement-to-prevent-the-premature-creation-of-artificial-superintelligence.md, Table 1 and Table 2 (lines 2115 to 2159), Figure 2 and its caption (lines 124 to 126), the CCC definition (line 468) and the 16-H100 worked example (line 800). -->
<!-- Timing formula derived from the tables: seconds = threshold FLOP / (chips * 9.9e14). 9.9e14 FLOP/s is one H100-equivalent at FP8, 50 percent utilization, the assumption the paper states at line 800. Days = seconds / 86400. This reproduces all 24 seconds cells and all 24 day cells of Tables 1 and 2 exactly at the printed precision (days shown to 3 decimals below 0.1, else 1 decimal). -->
<!-- Figure 2 model list: the eleven labelled (noteworthy) models. Compute values were measured from the figure image: the 1e24 and 1e22 threshold lines give an exact two-decade pixel calibration, and the reading was validated against the two values the article text states (DeepSeek-R1 about 4e24, gpt-oss-120b about 5e24) and against the release dates the x axis gives. Values are quoted to two significant figures. Parenthesised numbers are Artificial Analysis Intelligence Index scores read off the figure labels. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:wght@500&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a;
    --border: #e8e5df; --accent: #b87018; --cool: #3d6e91;
    --font-ui: "DM Sans", Arial, sans-serif;
    --font-head: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  [hidden] { display: none !important; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--page); }
  .lede { color: var(--muted); margin: 0 0 12px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 14px; background: var(--bg); margin-bottom: 12px; }
  h2 { font: 500 15px/1.3 var(--font-head); margin: 0 0 8px; }
  .ctl { margin-bottom: 12px; }
  .ctl:last-child { margin-bottom: 0; }
  .ctl label { display: block; font-weight: 500; margin-bottom: 2px; }
  .ctl .val { font-variant-numeric: tabular-nums; color: var(--accent); font-weight: 600; }
  .ctl .hint { color: var(--muted); font-size: 12px; }
  input[type="range"] { width: 100%; max-width: 30rem; accent-color: var(--accent); margin: 4px 0 0; }
  input[type="range"]:focus-visible { outline: 2px solid var(--accent); outline-offset: 3px; }
  table { border-collapse: collapse; width: 100%; }
  th, td { text-align: left; padding: 4px 8px 4px 0; font-variant-numeric: tabular-nums; vertical-align: top; }
  th { font-weight: 600; }
  .times th, .times td { border-bottom: 1px solid var(--border); }
  .times td.n { text-align: right; padding-right: 0; padding-left: 12px; }
  .times .big { display: block; }
  .times .sub { display: block; font-size: 12px; color: var(--muted); }
  .times tr:last-child th, .times tr:last-child td { border-bottom: 0; }
  .note { color: var(--muted); font-size: 12px; margin: 8px 0 0; }
  .note.is-paper { color: var(--accent); }
  .formula { color: var(--muted); font-size: 12px; margin: 0 0 10px; }
  .grid th.m, .grid td.m { text-align: center; width: 5.2rem; padding: 5px 2px; }
  .grid td, .grid th { border-bottom: 1px solid var(--border); }
  .grid .mech { width: auto; font-weight: 400; }
  .mark { display: inline-block; width: 12px; height: 12px; border-radius: 50%; vertical-align: -1px; }
  .mark.full { background: var(--accent); border: 1px solid var(--accent); }
  .mark.part { background: transparent; border: 1.5px solid var(--accent); }
  .mark.none { background: transparent; border: 0; }
  .cellword { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
  .key { color: var(--muted); font-size: 12px; margin: 8px 0 0; }
  .key .mark { margin: 0 4px 0 10px; }
  .key .mark:first-child { margin-left: 0; }
  .chartwrap { overflow-x: auto; }
  svg.ladder { display: block; width: 100%; min-width: 300px; max-width: 380px; height: auto; }
  svg.ladder text { font-family: var(--font-ui); }
  .counts { margin: 8px 0 0; }
  .detail { margin-top: 8px; border: 1px solid var(--border); border-radius: 8px; background: var(--page); padding: 8px 10px; min-height: 2.6rem; }
  .detail .who { font-weight: 600; }
  .status { font-size: 12px; color: var(--muted); margin: 0; }
  .status.is-done { color: var(--text); font-weight: 500; }
  g.model { cursor: pointer; }
  g.model:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  @media (max-width: 600px) { body { padding: 10px; } .grid th.m, .grid td.m { width: 3.8rem; } }
</style>
</head>
<body>
<p class="lede">Set the two thresholds and pick a cluster size.</p>

<div class="card">
  <div class="ctl">
    <label for="strict">Strict Threshold <span class="val" id="strict-val"></span></label>
    <input type="range" id="strict" min="22" max="28" step="0.5" value="24" aria-describedby="strict-val">
    <span class="hint">Training above this is prohibited.</span>
  </div>
  <div class="ctl">
    <label for="mon">Monitored Threshold <span class="val" id="mon-val"></span></label>
    <input type="range" id="mon" min="20" max="26" step="0.5" value="22" aria-describedby="mon-val">
    <span class="hint">Training above this must be approved and monitored.</span>
  </div>
  <div class="ctl">
    <label for="size">Cluster size <span class="val" id="size-val"></span></label>
    <input type="range" id="size" min="0" max="5" step="1" value="2" aria-describedby="size-val">
    <span class="hint">The six sizes the paper tabulates.</span>
  </div>
</div>

<div class="card">
  <h2 id="time-head"></h2>
  <p class="formula">Time = threshold FLOP divided by (chips x 9.9e14 FLOP/s). One H100-equivalent at FP8 and 50 percent utilization delivers 9.9e14 FLOP/s.</p>
  <table class="times">
    <tbody id="times-body"></tbody>
  </table>
  <p class="note" id="time-note"></p>
</div>

<div class="card">
  <h2 id="grid-head"></h2>
  <table class="grid">
    <thead>
      <tr><th class="mech">Lever</th><th class="m">Domestic round-up</th><th class="m">International verification</th></tr>
    </thead>
    <tbody id="grid-body"></tbody>
  </table>
  <p class="key"><span class="mark full"></span> very useful <span class="mark part"></span> somewhat useful, cannot be relied on. Blank: not listed for this size.</p>
  <p class="note" id="grid-note"></p>
</div>

<div class="card">
  <h2>Notable models against your thresholds</h2>
  <div class="chartwrap"><svg id="ladder" class="ladder" viewBox="0 0 340 440" role="img" aria-label="Training compute of eleven notable models against the two thresholds"></svg></div>
  <p class="counts" id="counts"></p>
  <div class="detail" id="detail" aria-live="polite"></div>
</div>

<p class="status" id="status"></p>

<script>
(function () {
  var RATE = 9.9e14;
  var SIZES = [100000, 10000, 1000, 100, 16, 1];
  var REGISTER = ["Day 1", "Day 1", "Day 10", "Day 100", "Year 2", "Never"];
  var MECH = [
    { name: "Mandatory reporting of CCCs", dom: [2, 2, 2, 2, 2, 0], intl: [2, 2, 2, 2, 2, 0] },
    { name: "Supply chain tracking", dom: [2, 2, 2, 1, 1, 0], intl: [2, 2, 2, 2, 2, 0] },
    { name: "Inspections", dom: [2, 2, 2, 2, 1, 0], intl: [2, 2, 2, 2, 1, 0] },
    { name: "Storage and compensation programs", dom: [0, 0, 1, 2, 2, 0], intl: [1, 1, 1, 1, 1, 0] },
    { name: "Satellite and aerial surveillance", dom: [2, 2, 1, 0, 0, 0], intl: [2, 2, 1, 0, 0, 0] },
    { name: "Electrical power monitoring", dom: [1, 1, 0, 0, 0, 0], intl: [2, 2, 0, 0, 0, 0] },
    { name: "Human intelligence and interviews", dom: [2, 2, 2, 2, 1, 0], intl: [1, 1, 1, 1, 1, 0] },
    { name: "Firmware-based chip tracking", dom: [0, 0, 0, 1, 1, 0], intl: [0, 0, 0, 1, 1, 0] },
    { name: "Sting operations", dom: [0, 0, 0, 2, 2, 0], intl: [0, 0, 0, 0, 0, 0] },
    { name: "Black market monitoring", dom: [0, 0, 1, 2, 2, 0], intl: [0, 2, 2, 2, 2, 0] },
    { name: "Whistleblower programs", dom: [1, 1, 1, 1, 1, 0], intl: [2, 2, 2, 2, 2, 0] }
  ];
  var MODELS = [
    { name: "Grok 4", year: "Jul 2025", flop: 5.1e26, aa: 65, sure: false },
    { name: "Grok 3", year: "Feb 2025", flop: 3.5e26, aa: 45, sure: true },
    { name: "Llama 3.1 405B", year: "Jul 2024", flop: 3.8e25, aa: 28, sure: true },
    { name: "GPT-4", year: "Mar 2023", flop: 2.1e25, aa: 22, sure: false },
    { name: "Qwen2.5-72B-Instruct", year: "Sep 2024", flop: 7.8e24, aa: 29, sure: true },
    { name: "gpt-oss-120b", year: "Aug 2025", flop: 5.0e24, aa: 60, sure: true },
    { name: "DeepSeek-R1", year: "Jan 2025", flop: 4.0e24, aa: 44, sure: true },
    { name: "Kimi K2", year: "Jul 2025", flop: 3.0e24, aa: 48, sure: true },
    { name: "gpt-oss-20b", year: "Aug 2025", flop: 5.5e23, aa: 52, sure: true },
    { name: "BLOOM-176B", year: "Jul 2022", flop: 3.7e23, aa: null, sure: true },
    { name: "GPT-3-175B", year: "May 2020", flop: 3.2e23, aa: null, sure: true }
  ];
  var NS = "http://www.w3.org/2000/svg";
  var KEY = "scher-threshold-explorer";

  var state = { strictLog: 24, monLog: 22, sizeIdx: 2, picked: -1, movedThreshold: false, movedSize: false };
  var completed = false;
  var saveTimer = null;

  var el = {
    strict: document.getElementById("strict"),
    mon: document.getElementById("mon"),
    size: document.getElementById("size"),
    strictVal: document.getElementById("strict-val"),
    monVal: document.getElementById("mon-val"),
    sizeVal: document.getElementById("size-val"),
    timeHead: document.getElementById("time-head"),
    timesBody: document.getElementById("times-body"),
    timeNote: document.getElementById("time-note"),
    gridHead: document.getElementById("grid-head"),
    gridBody: document.getElementById("grid-body"),
    gridNote: document.getElementById("grid-note"),
    ladder: document.getElementById("ladder"),
    counts: document.getElementById("counts"),
    detail: document.getElementById("detail"),
    status: document.getElementById("status")
  };

  function h(tag, cls, txt) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (txt !== undefined && txt !== null) n.textContent = txt;
    return n;
  }
  function s(tag, attrs, txt) {
    var n = document.createElementNS(NS, tag);
    for (var k in attrs) if (attrs[k] !== undefined && attrs[k] !== null) n.setAttribute(k, String(attrs[k]));
    if (txt !== undefined && txt !== null) n.textContent = txt;
    return n;
  }
  function sci(x, dp) {
    var e = Math.floor(Math.log10(x));
    var m = x / Math.pow(10, e);
    if (m >= 9.995) { m = 1; e += 1; }
    return m.toFixed(dp === undefined ? 1 : dp) + " x 10^" + e;
  }
  function fromLog(lg) { return Math.pow(10, lg); }
  function fmtThreshold(lg) {
    var m = Math.pow(10, lg - Math.floor(lg));
    return m.toFixed(1) + " x 10^" + Math.floor(lg) + " FLOP";
  }
  function fmtInt(n) { return String(n).replace(/\B(?=(\d{3})+(?!\d))/g, ","); }
  function seconds(threshold, chips) { return threshold / (chips * RATE); }
  function days(sec) { return sec / 86400; }
  function fmtDays(d) { return d < 0.1 ? d.toFixed(3) : d.toFixed(1); }
  function fmtSpan(d) {
    if (d >= 365.25) return fmtDays(d) + " days (" + (d / 365.25).toFixed(1) + " years)";
    if (d < 1 / 24) return fmtDays(d) + " days (" + (d * 24 * 60).toFixed(0) + " minutes)";
    if (d < 1) return fmtDays(d) + " days (" + (d * 24).toFixed(1) + " hours)";
    return fmtDays(d) + " days";
  }
  function sizeLabel(i) {
    return fmtInt(SIZES[i]) + (SIZES[i] === 1 ? " H100-equivalent" : " H100-equivalents");
  }
  function fmtMul(r) { return r >= 100 ? String(Math.round(r)) : r >= 10 ? r.toFixed(0) : r.toFixed(1); }
  function atDefaults() { return state.strictLog === 24 && state.monLog === 22; }

  function renderTimes() {
    var chips = SIZES[state.sizeIdx];
    var rows = [
      { lbl: "Monitored Threshold", t: fromLog(state.monLog) },
      { lbl: "Strict Threshold", t: fromLog(state.strictLog) }
    ];
    el.timeHead.textContent = "A cluster of " + sizeLabel(state.sizeIdx);
    el.timesBody.textContent = "";
    rows.forEach(function (r) {
      var sec = seconds(r.t, chips);
      var tr = document.createElement("tr");
      tr.appendChild(h("th", null, "Time to the " + r.lbl));
      var td = h("td", "n");
      td.appendChild(h("span", "big", fmtSpan(days(sec))));
      td.appendChild(h("span", "sub", sci(sec) + " seconds"));
      tr.appendChild(td);
      el.timesBody.appendChild(tr);
    });
    var reg = document.createElement("tr");
    reg.appendChild(h("th", null, "Registered by"));
    reg.appendChild(h("td", "n", REGISTER[state.sizeIdx]));
    el.timesBody.appendChild(reg);

    var monDays = days(seconds(fromLog(state.monLog), chips));
    var txt;
    if (atDefaults()) {
      txt = "These are the paper's own thresholds, so these two rows are the Table 1 and Table 2 cells for this column.";
    } else {
      txt = "At the paper's thresholds this cluster needs " + fmtDays(days(seconds(1e22, chips))) + " days to 1e22 FLOP and " + fmtDays(days(seconds(1e24, chips))) + " days to 1e24 FLOP.";
    }
    if (chips === 16) {
      txt += " Sixteen H100-equivalents is where the agreement draws the covered chip cluster line, because " + fmtDays(monDays) + " days to the Monitored Threshold is feasible for an evader while the Strict Threshold is not.";
    }
    el.timeNote.textContent = txt;
    el.timeNote.classList.toggle("is-paper", atDefaults());
  }

  function markCell(v) {
    var td = h("td", "m");
    var dot = h("span", "mark " + (v === 2 ? "full" : v === 1 ? "part" : "none"));
    dot.setAttribute("aria-hidden", "true");
    td.appendChild(dot);
    td.appendChild(h("span", "cellword", v === 2 ? "very useful" : v === 1 ? "somewhat" : "not listed"));
    return td;
  }

  function renderGrid() {
    el.gridHead.textContent = "Levers at " + sizeLabel(state.sizeIdx);
    el.gridBody.textContent = "";
    var i;
    for (i = 0; i < MECH.length; i++) {
      var m = MECH[i];
      var tr = document.createElement("tr");
      var th = h("th", "mech", m.name);
      th.scope = "row";
      tr.appendChild(th);
      tr.appendChild(markCell(m.dom[state.sizeIdx]));
      tr.appendChild(markCell(m.intl[state.sizeIdx]));
      el.gridBody.appendChild(tr);
    }
    var domCount = 0, intlCount = 0;
    for (i = 0; i < MECH.length; i++) {
      if (MECH[i].dom[state.sizeIdx] > 0) domCount++;
      if (MECH[i].intl[state.sizeIdx] > 0) intlCount++;
    }
    if (SIZES[state.sizeIdx] === 1) {
      el.gridNote.textContent = "A single chip sits below the agreement's covered chip cluster threshold of 16 H100-equivalents, so no lever in either table is listed for it, and it is never registered.";
    } else {
      el.gridNote.textContent = domCount + " of " + MECH.length + " levers apply domestically, " + intlCount + " internationally. The two tables are not the same list: the marks shift as the cluster gets smaller.";
    }
  }

  function bandOf(flop) {
    if (flop > fromLog(state.strictLog)) return 2;
    if (flop > fromLog(state.monLog)) return 1;
    return 0;
  }

  function renderLadder() {
    var W = 340, H = 440, top = 18, bot = 408, xAxis = 44, xDot = 62, xLab = 74;
    var logs = MODELS.map(function (m) { return Math.log10(m.flop); });
    var lo = Math.min.apply(null, logs.concat([state.monLog])) - 0.45;
    var hi = Math.max.apply(null, logs.concat([state.strictLog])) + 0.45;
    var svg = el.ladder;
    svg.setAttribute("viewBox", "0 0 " + W + " " + H);
    while (svg.firstChild) svg.removeChild(svg.firstChild);
    function y(lg) { return bot - (lg - lo) / (hi - lo) * (bot - top); }

    var g0 = s("g", null);
    var d0 = Math.ceil(lo), d1 = Math.floor(hi), d;
    for (d = d0; d <= d1; d++) {
      g0.appendChild(s("line", { x1: xAxis, y1: y(d), x2: W - 4, y2: y(d), stroke: "#e8e5df", "stroke-width": 1 }));
      g0.appendChild(s("text", { x: xAxis - 5, y: y(d) + 4, "text-anchor": "end", "font-size": 10, fill: "#5a5a5a" }, "10^" + d));
    }
    svg.appendChild(g0);

    var items = MODELS.map(function (m, i) { return { i: i, m: m, y: y(Math.log10(m.flop)) }; });
    items.sort(function (a, b) { return a.y - b.y; });
    var gap = 15, prev = -1e9, k;
    for (k = 0; k < items.length; k++) {
      items[k].ly = Math.max(items[k].y, prev + gap);
      prev = items[k].ly;
    }
    var over = items[items.length - 1].ly - (bot - 2);
    if (over > 0) {
      for (k = items.length - 1; k >= 0; k--) {
        items[k].ly -= over;
        if (k > 0 && items[k - 1].ly > items[k].ly - gap) over = items[k - 1].ly - (items[k].ly - gap);
        else break;
      }
    }

    items.forEach(function (it) {
      var band = bandOf(it.m.flop);
      var g = s("g", { class: "model", tabindex: "0", role: "button" });
      var color = band === 2 ? "#b87018" : band === 1 ? "#3d6e91" : "#8c8c8c";
      g.appendChild(s("title", null, it.m.name + ", about " + sci(it.m.flop) + " FLOP"));
      g.appendChild(s("rect", { x: xAxis, y: it.ly - 8, width: W - xAxis - 4, height: 15, fill: "transparent" }));
      if (Math.abs(it.ly - it.y) > 1) {
        g.appendChild(s("line", { x1: xDot + 4, y1: it.y, x2: xLab - 4, y2: it.ly - 3, stroke: "#c9c4bb", "stroke-width": 1 }));
      }
      var r = band === 0 ? 3.5 : 5;
      g.appendChild(s("circle", {
        cx: xDot, cy: it.y, r: r, fill: it.m.sure ? color : "#ffffff",
        stroke: color, "stroke-width": it.m.sure ? 1 : 2
      }));
      var t = s("text", { x: xLab, y: it.ly + 3, "font-size": 11, fill: state.picked === it.i ? "#1a1a1a" : "#3a3a3a", "font-weight": state.picked === it.i ? 600 : 400 }, it.m.name);
      g.appendChild(t);
      g.addEventListener("click", function () { pick(it.i); });
      g.addEventListener("keydown", function (ev) {
        if (ev.key === "Enter" || ev.key === " ") { ev.preventDefault(); pick(it.i); }
      });
      svg.appendChild(g);
    });

    var lines = [
      { lg: state.strictLog, label: "Strict Threshold", color: "#b87018", dash: "", dy: -5 },
      { lg: state.monLog, label: "Monitored Threshold", color: "#3d6e91", dash: "5 4", dy: 12 }
    ];
    lines.forEach(function (ln) {
      var yy = y(ln.lg);
      svg.appendChild(s("line", { x1: xAxis, y1: yy, x2: W - 4, y2: yy, stroke: ln.color, "stroke-width": 2, "stroke-dasharray": ln.dash || null }));
      var tw = ln.label.length * 5.4 + 8;
      svg.appendChild(s("rect", { x: W - 5 - tw, y: yy + ln.dy - 9, width: tw, height: 12, fill: "#ffffff", opacity: 0.92 }));
      svg.appendChild(s("text", { x: W - 8, y: yy + ln.dy, "text-anchor": "end", "font-size": 10, "font-weight": 600, fill: ln.color }, ln.label));
    });

    var above = 0, between = 0, below = 0;
    MODELS.forEach(function (m) {
      var b = bandOf(m.flop);
      if (b === 2) above++; else if (b === 1) between++; else below++;
    });
    el.counts.textContent = above + " of " + MODELS.length + " labelled models sit above your Strict Threshold and would be prohibited, " + between + " fall between the two and would be monitored, " + below + " sit below the Monitored Threshold.";
    svg.setAttribute("aria-label", "Training compute of eleven notable models on a log scale. " + above + " above the Strict Threshold, " + between + " between the thresholds, " + below + " below the Monitored Threshold.");
  }

  function renderDetail() {
    el.detail.textContent = "";
    if (state.picked < 0 || !MODELS[state.picked]) {
      el.detail.appendChild(h("span", null, "Pick a model to see where it falls."));
      return;
    }
    var m = MODELS[state.picked];
    var band = bandOf(m.flop);
    var verdict = band === 2 ? "above your Strict Threshold: prohibited" : band === 1 ? "between your two thresholds: monitored and approved" : "below your Monitored Threshold: unrestricted";
    var mul, phrase;
    if (band === 2) { mul = m.flop / fromLog(state.strictLog); phrase = fmtMul(mul) + "x your Strict Threshold"; }
    else if (band === 1) { mul = m.flop / fromLog(state.monLog); phrase = fmtMul(mul) + "x your Monitored Threshold"; }
    else { mul = fromLog(state.monLog) / m.flop; phrase = fmtMul(mul) + "x below your Monitored Threshold"; }
    el.detail.appendChild(h("span", "who", m.name));
    var rest = ", " + m.year + ", about " + sci(m.flop) + " FLOP. It falls " + verdict + ", " + phrase + ".";
    if (m.aa !== null) rest += " Artificial Analysis Intelligence Index " + m.aa + ".";
    if (!m.sure) rest += " The figure marks this compute estimate as less confident.";
    el.detail.appendChild(h("span", null, rest));
  }

  function renderStatus() {
    var done = state.movedThreshold && state.movedSize;
    el.status.textContent = done ? "Notice that the levers change with the cluster, not with the thresholds: where the line is set decides what is banned, the size of the cluster decides who can see it." : "";
    el.status.classList.toggle("is-done", done);
  }

  function render() {
    el.strict.value = String(state.strictLog);
    el.mon.value = String(state.monLog);
    el.size.value = String(state.sizeIdx);
    el.strictVal.textContent = fmtThreshold(state.strictLog);
    el.monVal.textContent = fmtThreshold(state.monLog);
    el.sizeVal.textContent = sizeLabel(state.sizeIdx);
    renderTimes();
    renderGrid();
    renderLadder();
    renderDetail();
    renderStatus();
  }

  function summary() {
    var chips = SIZES[state.sizeIdx];
    var above = 0;
    MODELS.forEach(function (m) { if (bandOf(m.flop) === 2) above++; });
    return "Threshold explorer. Strict Threshold " + fmtThreshold(state.strictLog) + ", Monitored Threshold " + fmtThreshold(state.monLog) +
      ", cluster " + sizeLabel(state.sizeIdx) + ". Time to the Monitored Threshold " + fmtDays(days(seconds(fromLog(state.monLog), chips))) +
      " days, to the Strict Threshold " + fmtDays(days(seconds(fromLog(state.strictLog), chips))) + " days, registered by " + REGISTER[state.sizeIdx] +
      ". " + above + " of 11 labelled Figure 2 models above the Strict Threshold. Model inspected: " +
      (state.picked >= 0 && MODELS[state.picked] ? MODELS[state.picked].name : "none") +
      ". Moved a threshold: " + (state.movedThreshold ? "yes" : "no") + ", changed the cluster size: " + (state.movedSize ? "yes" : "no") + ".";
  }

  function flush() {
    if (saveTimer) { clearTimeout(saveTimer); saveTimer = null; }
    var json = {
      strictLog: state.strictLog, monLog: state.monLog, sizeIdx: state.sizeIdx,
      picked: state.picked, movedThreshold: state.movedThreshold, movedSize: state.movedSize
    };
    if (window.Lens) {
      Lens.saveState(json, summary());
      if ((state.movedThreshold || state.movedSize) && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(KEY, JSON.stringify(json)); } catch (e) {}
    }
  }
  function persist() {
    if (saveTimer) clearTimeout(saveTimer);
    saveTimer = setTimeout(flush, 350);
  }

  function pick(i) { state.picked = i; renderLadder(); renderDetail(); persist(); }

  el.strict.addEventListener("input", function () {
    state.strictLog = Number(el.strict.value);
    if (state.monLog > state.strictLog) state.monLog = state.strictLog;
    state.movedThreshold = true;
    render(); persist();
  });
  el.mon.addEventListener("input", function () {
    state.monLog = Number(el.mon.value);
    if (state.monLog > state.strictLog) state.strictLog = state.monLog;
    state.movedThreshold = true;
    render(); persist();
  });
  el.size.addEventListener("input", function () {
    var v = Math.round(Number(el.size.value));
    if (v < 0) v = 0;
    if (v > 5) v = 5;
    if (v !== state.sizeIdx) state.movedSize = true;
    state.sizeIdx = v;
    render(); persist();
  });
  document.addEventListener("visibilitychange", function () {
    if (document.visibilityState === "hidden") flush();
  });

  function clampLog(v, lo, hi, dflt) {
    if (typeof v !== "number" || !isFinite(v)) return dflt;
    v = Math.round(v * 2) / 2;
    return Math.min(hi, Math.max(lo, v));
  }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      state.strictLog = clampLog(saved.strictLog, 22, 28, 24);
      state.monLog = clampLog(saved.monLog, 20, 26, 22);
      if (state.monLog > state.strictLog) state.monLog = state.strictLog;
      if (typeof saved.sizeIdx === "number" && saved.sizeIdx >= 0 && saved.sizeIdx <= 5) state.sizeIdx = Math.round(saved.sizeIdx);
      if (typeof saved.picked === "number" && saved.picked >= 0 && saved.picked < MODELS.length) state.picked = Math.round(saved.picked);
      state.movedThreshold = !!saved.movedThreshold;
      state.movedSize = !!saved.movedSize;
    }
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    try {
      var raw = localStorage.getItem(KEY);
      if (raw) hydrate(JSON.parse(raw), null);
    } catch (e) {}
  }
})();
</script>
</body>
</html>

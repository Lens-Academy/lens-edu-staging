---
id: '30fd2429-721c-48be-a347-aefe4fb95ca1'
title: Assurance curves for three verification budgets
summary_for_tutor: "An interactive reproduction of the AI 2040 verification supplement's 'Assurance curves' chart: confidence against coverage (both on log scales up to 8 nines) for three verification budgets, N_ver = 100, 10K and 10M audited packets. The curves are computed from the appendix formulas coverage = 1 - F* and confidence = 1 - exp(-N_ver * F*), where F* is the largest fraction of fake packets tolerated without detection. The learner hovers the chart or presses a coverage button (90%, 99%, ... 8 nines) to read the exact confidence for each budget, and can hide or show each curve. Done means they have read at least three different coverage points. Current readings are saved in the widget state."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Assurance curves for three verification budgets</title>
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), chart "Assurance curves" (AssuranceCurve component), shown twice on the source page (key verification metrics box, and appendix A.3). -->
<!-- Data: the three budgets, the axis mappings and the curve construction are copied from the page's chunk 4857 (the React component). Curves are recomputed from the appendix formulas coverage = 1 - F*, confidence = 1 - exp(-N_ver * F*). Nothing is read by eye. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1, h2 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 22px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 4px; }
  .lede { color: var(--muted); margin: 4px 0 12px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .formula { font-size: 13px; color: var(--muted); margin: 0 0 8px; }
  .chart { width: 100%; height: auto; display: block; touch-action: none; }
  .chart text { font-family: var(--font-ui); }
  .legend { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 10px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .legend button { display: inline-flex; align-items: center; gap: 8px; }
  .legend button.is-off { color: var(--muted); text-decoration: line-through; }
  .legend .state { font-size: 11px; color: var(--muted); }
  .swatch { display: inline-block; width: 28px; height: 0; border-top: 3px solid var(--text); }
  .swatch.dot { border-top-style: dotted; }
  .swatch.dash { border-top-style: dashed; }
  .probe { margin-top: 12px; }
  .probe .row { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; }
  .probe .lbl { font-size: 12px; color: var(--muted); margin-right: 4px; }
  .readout { margin-top: 10px; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 10px 12px; }
  .readout table { border-collapse: collapse; width: 100%; }
  .readout th, .readout td { text-align: left; padding: 3px 8px 3px 0; font-variant-numeric: tabular-nums; }
  .readout th { font-weight: 600; }
  .readout .n { text-align: right; }
  .status { font-size: 12px; color: var(--muted); margin-top: 8px; }
  .status.is-done { color: var(--text); font-weight: 500; }
  @media (max-width: 600px) { body { padding: 10px; } }
</style>
</head>
<body>
<p class="eyebrow">Interactive chart</p>
<h1>Assurance curves for three verification budgets</h1>
<p class="lede">Confidence against coverage for N_ver = 100, 10K and 10M audited packets. Hover the chart or press a coverage button to read the confidence each budget gives at that coverage.</p>

<div class="card">
  <p class="formula">Coverage = 1 - F*. Confidence = 1 - e^(-N_ver * F*). F* is the largest fraction of fake packets tolerated without detection.</p>
  <svg id="chart" class="chart" viewBox="0 0 1000 620" role="img" aria-label="Confidence against coverage, three curves for N_ver = 100, 10K and 10M"></svg>
  <div class="legend" id="legend" aria-label="Show or hide a budget"></div>
  <div class="probe">
    <div class="row" id="probe-row"><span class="lbl">Read values at coverage</span></div>
    <div class="readout" id="readout" aria-live="polite"></div>
  </div>
  <p class="status" id="status"></p>
</div>

<script>
(function () {
  var SERIES = [
    { label: "N_ver = 100", nVerified: 100, dash: "2 4", cls: "dot" },
    { label: "N_ver = 10K", nVerified: 10000, dash: "9 6", cls: "dash" },
    { label: "N_ver = 10M", nVerified: 10000000, dash: "", cls: "" }
  ];
  var X_TICKS = [0, -1, -2, -3, -4, -5, -6, -7, -8];
  var Y_TICKS = [0, 0.9, 0.99, 0.999, 0.9999, 0.99999, 0.999999, 0.9999999, 0.99999999];
  var PROBES = [-1, -2, -3, -4, -5, -6, -7, -8];
  var NS = "http://www.w3.org/2000/svg";

  var state = { probeLog: -2, visible: [true, true, true], read: {} };
  var completed = false;

  function xOf(logF) { return 150 + (0 - logF) / 8 * 790; }
  function yOf(p) {
    var t = Math.log10(Math.max(1e-12, 1 - p));
    if (t < -8) t = -8;
    if (t > 0) t = 0;
    return 60 + (t - (-8)) / 8 * 380;
  }
  function confidence(n, logF) { return 1 - Math.exp(-n * Math.pow(10, logF)); }
  function fmtCoverage(logF) {
    if (logF >= 0) return "0%";
    var e = -logF;
    return e <= 4.01 ? ((1 - Math.pow(10, logF)) * 100).toFixed(Math.max(0, Math.round(e) - 2)) + "%" : Math.round(e) + " nines";
  }
  function fmtAxisY(p) {
    if (p === 0) return "0";
    var e = -Math.log10(1 - p);
    return e <= 4.01 ? (100 * p).toFixed(Math.max(0, Math.round(e) - 2)) + "%" : Math.round(e) + " nines";
  }
  function fmtSmall(v) {
    if (v <= 0) return "0";
    var d = -Math.floor(Math.log10(v)) + 1;
    return v.toFixed(Math.min(12, d)).replace(/0+$/, "").replace(/\.$/, "");
  }
  function fmtConf(p) {
    if (p >= 0.9999999) return "~100%";
    if (p >= 0.9999) return (100 * p).toFixed(4) + "%";
    if (p >= 0.999) return (100 * p).toFixed(3) + "%";
    if (p >= 0.99) return (100 * p).toFixed(2) + "%";
    if (p >= 0.1) return (100 * p).toFixed(1) + "%";
    if (p >= 0.001) return (100 * p).toFixed(2) + "%";
    return fmtSmall(100 * p) + "%";
  }
  function fmtF(logF) {
    var f = Math.pow(10, logF);
    return f >= 0.001 ? (f * 100).toString() + "%" : f.toExponential(0);
  }

  var svg = document.getElementById("chart");
  function el(tag, attrs, text) {
    var n = document.createElementNS(NS, tag);
    for (var k in attrs) n.setAttribute(k, attrs[k]);
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function h(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined) n.textContent = text;
    return n;
  }

  function curvePath(n) {
    var pts = [], prevL = null, prevC = null;
    for (var i = 0; i <= 800; i++) {
      var l = 0 - i / 800 * 8;
      var r = confidence(n, l);
      var u = 1 - r;
      var c = u > 0 ? Math.log10(u) : -Infinity;
      if (c <= -8) { prevL = l; prevC = c; continue; }
      if (pts.length === 0 && prevC !== null && prevC <= -8 && prevL !== null) {
        var t = prevL + (-8 - prevC) / (c - prevC) * (l - prevL);
        pts.push("M " + xOf(t).toFixed(2) + " " + yOf(0.99999999).toFixed(2));
      }
      pts.push((pts.length === 0 ? "M" : "L") + " " + xOf(l).toFixed(2) + " " + yOf(r).toFixed(2));
      prevL = l; prevC = c;
    }
    return pts.join(" ");
  }

  var curveEls = [], probeLine, probeDots = [];
  function drawChart() {
    var i;
    for (i = 0; i < X_TICKS.length; i++) svg.appendChild(el("line", { x1: xOf(X_TICKS[i]), y1: 60, x2: xOf(X_TICKS[i]), y2: 440, stroke: "#1a1a1a", "stroke-width": 0.4, "stroke-dasharray": "1.5 3" }));
    for (i = 0; i < Y_TICKS.length; i++) svg.appendChild(el("line", { x1: 150, y1: yOf(Y_TICKS[i]), x2: 940, y2: yOf(Y_TICKS[i]), stroke: "#1a1a1a", "stroke-width": 0.4, "stroke-dasharray": "1.5 3" }));
    svg.appendChild(el("line", { x1: 150, y1: 440, x2: 940, y2: 440, stroke: "#1a1a1a", "stroke-width": 1.6 }));
    svg.appendChild(el("line", { x1: 150, y1: 60, x2: 150, y2: 440, stroke: "#1a1a1a", "stroke-width": 1.6 }));
    for (i = 0; i < X_TICKS.length; i++) svg.appendChild(el("text", { x: xOf(X_TICKS[i]), y: 470, "text-anchor": "middle", "font-size": 19, fill: "#1a1a1a" }, fmtCoverage(X_TICKS[i])));
    for (i = 0; i < Y_TICKS.length; i++) svg.appendChild(el("text", { x: 136, y: yOf(Y_TICKS[i]) + 7, "text-anchor": "end", "font-size": 19, fill: "#1a1a1a" }, fmtAxisY(Y_TICKS[i])));
    svg.appendChild(el("text", { x: 545, y: 510, "text-anchor": "middle", "font-size": 22, "font-style": "italic", fill: "#1a1a1a" }, "Coverage (log scale)"));
    svg.appendChild(el("text", { x: -250, y: 22, "text-anchor": "middle", "font-size": 22, "font-style": "italic", fill: "#1a1a1a", transform: "rotate(-90)" }, "Confidence"));
    for (i = 0; i < SERIES.length; i++) {
      var p = el("path", { d: curvePath(SERIES[i].nVerified), fill: "none", stroke: "#1a1a1a", "stroke-width": 3 });
      if (SERIES[i].dash) p.setAttribute("stroke-dasharray", SERIES[i].dash);
      svg.appendChild(p);
      curveEls.push(p);
    }
    probeLine = el("line", { x1: 0, y1: 60, x2: 0, y2: 440, stroke: "#b87018", "stroke-width": 1.5, "stroke-dasharray": "4 3" });
    svg.appendChild(probeLine);
    for (i = 0; i < SERIES.length; i++) {
      var d = el("circle", { cx: 0, cy: 0, r: 6, fill: "#b87018", stroke: "#ffffff", "stroke-width": 1.5 });
      svg.appendChild(d);
      probeDots.push(d);
    }
    var widths = SERIES.map(function (s) { return 24 * s.label.length * 0.55 + 36 + 12; });
    var total = widths.reduce(function (a, b) { return a + b; }, 0) + 36 * (SERIES.length - 1);
    var x = (1000 - total) / 2;
    for (i = 0; i < SERIES.length; i++) {
      var g = el("g", { transform: "translate(" + x + ", 570)" });
      var ln = el("line", { x1: 0, y1: 0, x2: 36, y2: 0, stroke: "#1a1a1a", "stroke-width": 3.5 });
      if (SERIES[i].dash) ln.setAttribute("stroke-dasharray", SERIES[i].dash);
      g.appendChild(ln);
      g.appendChild(el("text", { x: 48, y: 6, "font-size": 22, fill: "#1a1a1a" }, SERIES[i].label));
      svg.appendChild(g);
      x += widths[i] + 36;
    }
  }

  var readout = document.getElementById("readout");
  var legendEl = document.getElementById("legend");
  var probeRow = document.getElementById("probe-row");
  var statusEl = document.getElementById("status");

  function readCount() { var n = 0; for (var k in state.read) if (state.read[k]) n++; return n; }

  function render() {
    var i;
    var px = xOf(state.probeLog);
    probeLine.setAttribute("x1", px); probeLine.setAttribute("x2", px);
    for (i = 0; i < SERIES.length; i++) {
      curveEls[i].setAttribute("visibility", state.visible[i] ? "visible" : "hidden");
      var p = confidence(SERIES[i].nVerified, state.probeLog);
      probeDots[i].setAttribute("cx", px);
      probeDots[i].setAttribute("cy", yOf(p));
      probeDots[i].setAttribute("visibility", state.visible[i] ? "visible" : "hidden");
    }
    var lb = legendEl.querySelectorAll("button");
    for (i = 0; i < lb.length; i++) {
      lb[i].classList.toggle("is-off", !state.visible[i]);
      lb[i].setAttribute("aria-pressed", state.visible[i] ? "true" : "false");
      lb[i].querySelector(".state").textContent = state.visible[i] ? "shown" : "hidden";
    }
    var pb = probeRow.querySelectorAll("button");
    for (i = 0; i < pb.length; i++) {
      var on = Number(pb[i].dataset.log) === state.probeLog;
      pb[i].classList.toggle("is-active", on);
      pb[i].setAttribute("aria-pressed", on ? "true" : "false");
      pb[i].textContent = fmtCoverage(Number(pb[i].dataset.log)) + (state.read[pb[i].dataset.log] ? " ✓" : "");
    }
    readout.textContent = "";
    readout.appendChild(h("div", null, "Coverage " + fmtCoverage(state.probeLog) + " (tolerated fake fraction F* = " + fmtF(state.probeLog) + "):"));
    var table = h("table");
    var thead = h("tr"); thead.appendChild(h("th", null, "Budget")); thead.appendChild(h("th", "n", "N_ver * F*")); thead.appendChild(h("th", "n", "Confidence"));
    table.appendChild(thead);
    for (i = 0; i < SERIES.length; i++) {
      var tr = h("tr");
      var lam = SERIES[i].nVerified * Math.pow(10, state.probeLog);
      tr.appendChild(h("td", null, SERIES[i].label + (state.visible[i] ? "" : " (hidden)")));
      tr.appendChild(h("td", "n", lam >= 100 ? Math.round(lam).toLocaleString("en-US") : (Math.round(lam * 10000) / 10000).toString()));
      tr.appendChild(h("td", "n", fmtConf(confidence(SERIES[i].nVerified, state.probeLog))));
      table.appendChild(tr);
    }
    readout.appendChild(table);
    var n = readCount();
    statusEl.textContent = n >= 3 ? "Read at " + n + " coverage points. Notice how each 10x in N_ver shifts the curve one decade to the right." : "Coverage points read: " + n + " of 3 needed. Press the coverage buttons to compare the three budgets.";
    statusEl.classList.toggle("is-done", n >= 3);
  }

  function summary() {
    var parts = [];
    for (var i = 0; i < SERIES.length; i++) parts.push(SERIES[i].label + ": " + fmtConf(confidence(SERIES[i].nVerified, state.probeLog)));
    var readPts = Object.keys(state.read).filter(function (k) { return state.read[k]; }).map(function (k) { return fmtCoverage(Number(k)); });
    return "Assurance curve chart. Reading at coverage " + fmtCoverage(state.probeLog) + " (F* = " + fmtF(state.probeLog) + "): " + parts.join(", ") + ". Coverage points read so far: " + (readPts.join(", ") || "none") + ". Hidden series: " + (SERIES.filter(function (s, i) { return !state.visible[i]; }).map(function (s) { return s.label; }).join(", ") || "none") + ".";
  }

  function persist() {
    var json = { probeLog: state.probeLog, visible: state.visible.slice(), read: state.read };
    if (window.Lens) {
      Lens.saveState(json, summary());
      if (readCount() >= 3 && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("ai-2040-assurance-curve", JSON.stringify(json)); } catch (e) {}
    }
  }

  SERIES.forEach(function (s, i) {
    var b = h("button", null);
    b.type = "button";
    b.appendChild(h("span", "swatch " + s.cls));
    b.appendChild(h("span", null, s.label));
    b.appendChild(h("span", "state", ""));
    b.addEventListener("click", function () { state.visible[i] = !state.visible[i]; render(); persist(); });
    legendEl.appendChild(b);
  });
  PROBES.forEach(function (lg) {
    var b = h("button", null, fmtCoverage(lg));
    b.type = "button";
    b.dataset.log = String(lg);
    b.addEventListener("click", function () { state.probeLog = lg; state.read[String(lg)] = true; render(); persist(); });
    probeRow.appendChild(b);
  });
  function pointerLog(evt) {
    var rect = svg.getBoundingClientRect();
    if (!rect.width) return null;
    var x = (evt.clientX - rect.left) / rect.width * 1000;
    var lg = -((x - 150) / 790 * 8);
    if (lg > 0) lg = 0; if (lg < -8) lg = -8;
    return Math.round(lg * 20) / 20;
  }
  var hoverTimer = null;
  svg.addEventListener("pointermove", function (evt) {
    var lg = pointerLog(evt);
    if (lg === null || lg === state.probeLog) return;
    state.probeLog = lg;
    render();
    clearTimeout(hoverTimer);
    hoverTimer = setTimeout(persist, 400);
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.probeLog === "number" && saved.probeLog <= 0 && saved.probeLog >= -8) state.probeLog = saved.probeLog;
      if (Array.isArray(saved.visible) && saved.visible.length === 3) state.visible = saved.visible.map(function (v) { return !!v; });
      if (saved.read && typeof saved.read === "object") { state.read = {}; for (var k in saved.read) if (saved.read[k]) state.read[k] = true; }
    }
    completed = !!(meta && meta.completed);
    render();
  }

  drawChart();
  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    try { var raw = localStorage.getItem("ai-2040-assurance-curve"); if (raw) hydrate(JSON.parse(raw), null); } catch (e) {}
  }
})();
</script>
</body>
</html>

---
id: 'acd00bf6-a7c2-4541-8202-25e8c29aecb6'
title: Catching a rogue internal deployment
summary_for_tutor: "An interactive chart of the probability that a rogue internal deployment is caught by random recomputation of logged compute packets, plotted against the rogue deployment's size in H100e on a log x axis, with three curves for detection within 1 hour, 1 week and 1 month and a y axis running 0, 50%, 90%, 99%, 99.9%, 99.99%. Two sliders drive it: Year (2030, 2032, 2034, 2040) sets the verified compute pool shown above the chart and the packet size that year's logging implies, and Packet size (1, 10, 100, 1K, 10K H100e-hours) sets how much compute one auditable packet covers, so smaller packets mean more rogue packets to sample and steeper curves. The recomputation budget is fixed at 1% and P(detected) = 1 - exp(-0.01 * size * hours / packet). It opens at 2034, a ~33B H100e pool and packets of 100 H100e-hours, where a 1K H100e rogue deployment is near certain to be caught within a month and a 1 H100e one is not."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Catching a rogue internal deployment</title>
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), interactive chart "Catching a rogue internal deployment" (RogueDeployment component). -->
<!-- Data: year options, pool sizes, default packet sizes, time windows and the axis mappings are copied from the page's chunk 6441 (the React component behind the sliders). Curves are recomputed from the appendix formula P(detected) = 1 - exp(-C * N_fake), C = 0.01, N_fake = size * hours / packet. Nothing is read by eye. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --accent: #b87018;
    --font-ui: "DM Sans", Arial, sans-serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .facts { display: flex; flex-wrap: wrap; gap: 6px 24px; margin: 0 0 12px; }
  .facts strong { font-weight: 600; }
  .controls { display: grid; grid-template-columns: 1fr 1fr; gap: 16px 24px; margin-bottom: 8px; }
  .control label { display: block; font-weight: 600; margin-bottom: 4px; }
  .control input[type=range] { width: 100%; accent-color: var(--accent); margin: 4px 0; }
  .ticks { display: flex; justify-content: space-between; font-size: 11px; font-style: italic; color: var(--muted); }
  .ticks span { flex: 1; text-align: center; }
  .ticks span:first-child { text-align: left; }
  .ticks span:last-child { text-align: right; }
  .chartbox { overflow-x: auto; margin-top: 8px; }
  .chart { width: 100%; min-width: 720px; height: auto; display: block; }
  .chart text { font-family: var(--font-ui); }
  @media (max-width: 600px) { .controls { grid-template-columns: 1fr; } body { padding: 10px; } }
</style>
</head>
<body>
<div class="card">
  <div class="facts">
    <span><strong>Pool:</strong> <span id="pool"></span></span>
    <span><strong>Recomputation budget:</strong> 1%</span>
  </div>
  <div class="controls">
    <div class="control">
      <label for="year"><strong>Year:</strong> <span id="year-label"></span></label>
      <input id="year" type="range" min="0" max="3" step="1" value="2" aria-label="Year">
      <div class="ticks"><span>2030</span><span>2032</span><span>2034</span><span>2040</span></div>
    </div>
    <div class="control">
      <label for="packet"><strong>Packet size:</strong> <span id="packet-label"></span></label>
      <input id="packet" type="range" min="0" max="4" step="1" value="2" aria-label="Packet size">
      <div class="ticks"><span>1</span><span>10</span><span>100</span><span>1K</span><span>10K</span></div>
    </div>
  </div>

  <div class="chartbox"><svg id="chart" class="chart" viewBox="0 0 1000 620" role="img" aria-label="P(detected) against rogue deployment size, three curves for 1 hour, 1 week and 1 month"></svg></div>
</div>

<script>
(function () {
  var YEARS = [
    { year: 2030, totalCompute: "~400M H100e", defaultPacket: 10000 },
    { year: 2032, totalCompute: "~3B H100e", defaultPacket: 1000 },
    { year: 2034, totalCompute: "~33B H100e", defaultPacket: 100 },
    { year: 2040, totalCompute: "~1T H100e", defaultPacket: 10 }
  ];
  var WINDOWS = [
    { label: "1 hour", hours: 1, dash: "2 4" },
    { label: "1 week", hours: 168, dash: "9 6" },
    { label: "1 month", hours: 720, dash: "" }
  ];
  var BUDGET = 0.01;
  var SIZE_LABELS = ["1", "10", "100", "1K", "10K", "100K", "1M", "10M"];
  var Y_TICKS = [0, 0.5, 0.9, 0.99, 0.999, 0.9999];
  var NS = "http://www.w3.org/2000/svg";

  var state = { year: 2, packetLog: 2 };
  var completed = false;

  function xOf(logSize) { return 110 + logSize / 7 * 830; }
  function yOf(p) {
    var t = Math.log10(Math.max(1e-12, 1 - p));
    if (t < -4) t = -4;
    if (t > 0) t = 0;
    return 40 + (t - (-4)) / 4 * 400;
  }
  function pDetected(size, hours, packet) { return 1 - Math.exp(-(BUDGET * size * hours / packet)); }
  function fmtAxis(p) {
    if (p === 0) return "0";
    var t = -Math.log10(1 - p);
    return t <= 4.01 ? (100 * p).toFixed(Math.max(0, Math.round(t) - 2)) + "%" : Math.round(t) + " nines";
  }
  function fmtSmall(v) {
    if (v <= 0) return "0";
    var d = -Math.floor(Math.log10(v)) + 1;
    var s = v.toFixed(Math.min(12, d));
    while (s.length > 1 && s.charAt(s.length - 1) === "0") s = s.slice(0, -1);
    if (s.charAt(s.length - 1) === ".") s = s.slice(0, -1);
    return s;
  }
  function fmtP(p) {
    if (p >= 0.99999) return "~100%";
    if (p >= 0.9999) return (100 * p).toFixed(3) + "%";
    if (p >= 0.999) return (100 * p).toFixed(2) + "%";
    if (p >= 0.1) return (100 * p).toFixed(1) + "%";
    if (p >= 0.001) return (100 * p).toFixed(2) + "%";
    return fmtSmall(100 * p) + "%";
  }
  function fmtPacket(m) {
    if (m >= 1000) return (Math.round(m / 100) / 10) + "K H100e-hours";
    if (m >= 100) return Math.round(m) + " H100e-hours";
    if (m >= 10) return m.toFixed(1) + " H100e-hours";
    return m.toFixed(2) + " H100e-hours";
  }

  var svg = document.getElementById("chart");
  function el(tag, attrs, text) {
    var n = document.createElementNS(NS, tag);
    for (var k in attrs) n.setAttribute(k, attrs[k]);
    if (text !== undefined) n.textContent = text;
    return n;
  }

  function curvePath(hours, packet) {
    var pts = [], prevR = null, prevC = null;
    for (var i = 0; i <= 800; i++) {
      var r = i / 800 * 7;
      var s = pDetected(Math.pow(10, r), hours, packet);
      var u = 1 - s;
      var c = u > 0 ? Math.log10(u) : -Infinity;
      if (c <= -4) {
        if (prevR !== null && prevC !== null && prevC > -4) {
          var e = prevR + (prevC - (-4)) / (prevC - c) * (r - prevR);
          pts.push("L " + xOf(e).toFixed(2) + " " + yOf(0.9999).toFixed(2));
        }
        break;
      }
      pts.push((pts.length === 0 ? "M" : "L") + " " + xOf(r).toFixed(2) + " " + yOf(s).toFixed(2));
      prevR = r; prevC = c;
    }
    return pts.join(" ");
  }

  var curveEls = [];
  function drawChart() {
    while (svg.firstChild) svg.removeChild(svg.firstChild);
    var i;
    for (i = 0; i <= 7; i++) svg.appendChild(el("line", { x1: xOf(i), y1: 40, x2: xOf(i), y2: 440, stroke: "#1a1a1a", "stroke-width": 0.4, "stroke-dasharray": "1.5 3" }));
    for (i = 0; i < Y_TICKS.length; i++) svg.appendChild(el("line", { x1: 110, y1: yOf(Y_TICKS[i]), x2: 940, y2: yOf(Y_TICKS[i]), stroke: "#1a1a1a", "stroke-width": 0.4, "stroke-dasharray": "1.5 3" }));
    svg.appendChild(el("line", { x1: 110, y1: 440, x2: 940, y2: 440, stroke: "#1a1a1a", "stroke-width": 1.6 }));
    svg.appendChild(el("line", { x1: 110, y1: 40, x2: 110, y2: 440, stroke: "#1a1a1a", "stroke-width": 1.6 }));
    for (i = 0; i <= 7; i++) svg.appendChild(el("text", { x: xOf(i), y: 470, "text-anchor": "middle", "font-size": 20, fill: "#1a1a1a" }, SIZE_LABELS[i]));
    for (i = 0; i < Y_TICKS.length; i++) svg.appendChild(el("text", { x: 96, y: yOf(Y_TICKS[i]) + 7, "text-anchor": "end", "font-size": 20, fill: "#1a1a1a" }, fmtAxis(Y_TICKS[i])));
    svg.appendChild(el("text", { x: 525, y: 510, "text-anchor": "middle", "font-size": 22, "font-style": "italic", fill: "#1a1a1a" }, "Rogue deployment size (H100e, log scale)"));
    svg.appendChild(el("text", { x: -240, y: 28, "text-anchor": "middle", "font-size": 22, "font-style": "italic", fill: "#1a1a1a", transform: "rotate(-90)" }, "P(detected)"));
    curveEls = [];
    for (i = 0; i < WINDOWS.length; i++) {
      var p = el("path", { d: "", fill: "none", stroke: "#1a1a1a", "stroke-width": 3 });
      if (WINDOWS[i].dash) p.setAttribute("stroke-dasharray", WINDOWS[i].dash);
      svg.appendChild(p);
      curveEls.push(p);
    }
    var legend = el("g", {});
    var widths = WINDOWS.map(function (w) { return 24 * ("within " + w.label).length * 0.55 + 36 + 12; });
    var total = widths.reduce(function (a, b) { return a + b; }, 0) + 36 * (WINDOWS.length - 1);
    var x = (1000 - total) / 2;
    for (i = 0; i < WINDOWS.length; i++) {
      var g = el("g", { transform: "translate(" + x + ", 570)" });
      var ln = el("line", { x1: 0, y1: 0, x2: 36, y2: 0, stroke: "#1a1a1a", "stroke-width": 3.5 });
      if (WINDOWS[i].dash) ln.setAttribute("stroke-dasharray", WINDOWS[i].dash);
      g.appendChild(ln);
      g.appendChild(el("text", { x: 48, y: 6, "font-size": 22, fill: "#1a1a1a" }, "within " + WINDOWS[i].label));
      legend.appendChild(g);
      x += widths[i] + 36;
    }
    svg.appendChild(legend);
  }

  var yearIn = document.getElementById("year");
  var packetIn = document.getElementById("packet");

  function packet() { return Math.pow(10, state.packetLog); }

  function render() {
    var y = YEARS[state.year];
    var m = packet();
    document.getElementById("pool").textContent = y.totalCompute + " (" + y.year + " buildout)";
    document.getElementById("year-label").textContent = String(y.year);
    document.getElementById("packet-label").textContent = fmtPacket(m);
    if (String(yearIn.value) !== String(state.year)) yearIn.value = state.year;
    if (String(packetIn.value) !== String(state.packetLog)) packetIn.value = state.packetLog;
    for (var i = 0; i < WINDOWS.length; i++) curveEls[i].setAttribute("d", curvePath(WINDOWS[i].hours, m));
  }

  function summary() {
    var y = YEARS[state.year], m = packet();
    var reads = [];
    for (var i = 0; i < WINDOWS.length; i++) {
      var parts = [];
      for (var k = 0; k < 3; k++) {
        var logSize = [0, 2, 4][k];
        parts.push(SIZE_LABELS[logSize] + " H100e " + fmtP(pDetected(Math.pow(10, logSize), WINDOWS[i].hours, m)));
      }
      reads.push("within " + WINDOWS[i].label + ", " + parts.join(", "));
    }
    return "Rogue deployment detection chart set to year " + y.year + " (verified pool " + y.totalCompute + ") with packets of " + fmtPacket(m) + " and a 1% recomputation budget, so P(detected) rises with rogue deployment size along the log x axis: " + reads.join("; ") + ".";
  }

  function persist(changed) {
    var json = { year: state.year, packetLog: state.packetLog };
    if (window.Lens) {
      Lens.saveState(json, summary());
      if (changed && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("ai-2040-rogue-detection", JSON.stringify(json)); } catch (e) {}
    }
  }

  yearIn.addEventListener("input", function () {
    state.year = parseInt(yearIn.value, 10);
    state.packetLog = Math.log10(YEARS[state.year].defaultPacket);
    render(); persist(true);
  });
  packetIn.addEventListener("input", function () {
    state.packetLog = parseFloat(packetIn.value);
    render(); persist(true);
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.year === "number" && saved.year >= 0 && saved.year < YEARS.length) state.year = saved.year;
      if (typeof saved.packetLog === "number" && saved.packetLog >= 0 && saved.packetLog <= 4) state.packetLog = Math.round(saved.packetLog);
    }
    completed = !!(meta && meta.completed);
    render();
  }

  drawChart();
  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    try { var raw = localStorage.getItem("ai-2040-rogue-detection"); if (raw) hydrate(JSON.parse(raw), null); } catch (e) {}
  }
})();
</script>
</body>
</html>


---
id: 'acd00bf6-a7c2-4541-8202-25e8c29aecb6'
title: Catching a rogue internal deployment
summary_for_tutor: "An interactive reproduction of the AI 2040 verification supplement's 'Catching a rogue internal deployment' chart. The learner picks a year (2030, 2032, 2034 or 2040, which sets the verified pool size and the default packet size) and a packet size (1 to 10K H100e-hours), then reads P(detected) for a rogue deployment of a given size (1 to 10M H100e) within 1 hour, 1 week or 1 month, using the appendix formula P(detected) = 1 - exp(-C * N_fake) with a 1% recomputation budget, where N_fake = size * hours / packet size. They can hover the chart or press a size button to read exact values, and hide or show each time window. Done means they have moved at least one slider away from the default and read at least three different rogue deployment sizes from the size buttons. Their current settings and readouts are saved in the widget state as they explore."
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
<!-- Data: year options, pool sizes, default packet sizes, time windows and the axis mappings are copied from the page's chunk 6441 (the React component behind the sliders). Curves are recomputed from the appendix formula P(detected) = 1 - exp(-C * N_fake), C = 0.01, N_fake = size * hours / packet, exactly as the source computes them. Nothing is read by eye. -->
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
  .facts { display: flex; flex-wrap: wrap; gap: 6px 24px; margin: 0 0 12px; }
  .facts strong { font-weight: 600; }
  .controls { display: grid; grid-template-columns: 1fr 1fr; gap: 16px 24px; margin-bottom: 8px; }
  .control label { display: block; font-weight: 600; margin-bottom: 4px; }
  .control input[type=range] { width: 100%; accent-color: var(--accent); margin: 4px 0; }
  .ticks { display: flex; justify-content: space-between; font-size: 11px; font-style: italic; color: var(--muted); }
  .ticks span { flex: 1; text-align: center; }
  .ticks span:first-child { text-align: left; }
  .ticks span:last-child { text-align: right; }
  .chart { width: 100%; height: auto; display: block; margin-top: 8px; touch-action: none; }
  .chart text { font-family: var(--font-ui); }
  .legend { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 10px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .legend button { display: inline-flex; align-items: center; gap: 8px; }
  .legend button.is-off { color: var(--muted); text-decoration: line-through; }
  .swatch { display: inline-block; width: 28px; height: 0; border-top: 3px solid var(--text); }
  .swatch.dot { border-top-style: dotted; }
  .swatch.dash { border-top-style: dashed; }
  .probe { margin-top: 12px; }
  .probe .row { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; }
  .probe .row span.lbl { font-size: 12px; color: var(--muted); margin-right: 4px; }
  .readout { margin-top: 10px; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 10px 12px; }
  .readout table { border-collapse: collapse; width: 100%; }
  .readout th, .readout td { text-align: left; padding: 3px 8px 3px 0; font-variant-numeric: tabular-nums; }
  .readout th { font-weight: 600; }
  .readout .n { text-align: right; }
  .note { font-size: 12px; color: var(--muted); margin: 10px 0 0; }
  .status { font-size: 12px; color: var(--muted); margin-top: 8px; }
  .status.is-done { color: var(--text); font-weight: 500; }
  @media (max-width: 600px) { .controls { grid-template-columns: 1fr; } body { padding: 10px; } }
</style>
</head>
<body>
<p class="eyebrow">Interactive chart</p>
<h1>Catching a rogue internal deployment</h1>
<p class="lede">Probability that a 1% random recomputation budget catches a rogue internal deployment, by its size and how long it runs. Move the sliders, then hover the curves or press a size button to read exact values.</p>

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
  <p class="note" id="gpu-note"></p>

  <svg id="chart" class="chart" viewBox="0 0 1000 620" role="img" aria-label="P(detected) against rogue deployment size, three curves for 1 hour, 1 week and 1 month"></svg>

  <div class="legend" id="legend" aria-label="Show or hide a time window"></div>

  <div class="probe">
    <div class="row" id="probe-row"><span class="lbl">Read values at a rogue deployment of</span></div>
    <div class="readout" id="readout" aria-live="polite"></div>
  </div>
  <p class="status" id="status"></p>
</div>

<script>
(function () {
  var YEARS = [
    { year: 2030, totalCompute: "~400M H100e", gpuNote: "one packet per server rack per hour (~10K H100e per packet)", defaultPacket: 10000 },
    { year: 2032, totalCompute: "~3B H100e", gpuNote: "one packet per shelf per hour (~1K H100e per packet)", defaultPacket: 1000 },
    { year: 2034, totalCompute: "~33B H100e", gpuNote: "one packet per GPU per hour (~100 H100e per packet)", defaultPacket: 100 },
    { year: 2040, totalCompute: "~1T H100e", gpuNote: "one packet per GPU every ~6 minutes (~10 H100e per packet)", defaultPacket: 10 }
  ];
  var WINDOWS = [
    { label: "1 hour", hours: 1, dash: "2 4", cls: "dot" },
    { label: "1 week", hours: 168, dash: "9 6", cls: "dash" },
    { label: "1 month", hours: 720, dash: "", cls: "" }
  ];
  var BUDGET = 0.01;
  var SIZE_LABELS = ["1", "10", "100", "1K", "10K", "100K", "1M", "10M"];
  var Y_TICKS = [0, 0.5, 0.9, 0.99, 0.999, 0.9999];
  var NS = "http://www.w3.org/2000/svg";

  var state = { year: 2, packetLog: 2, probeLog: 4, visible: [true, true, true], explored: false, sizesRead: [] };
  var completed = false;

  function isDone() { return state.explored && state.sizesRead.length >= 3; }

  function xOf(logSize) { return 110 + (logSize - 0) / 7 * 830; }
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
  function fmtSize(logSize) {
    var v = Math.pow(10, logSize);
    if (v >= 1e6) return (Math.round(v / 1e5) / 10) + "M";
    if (v >= 1e3) return (Math.round(v / 100) / 10) + "K";
    return String(Math.round(v * 10) / 10);
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

  var curveEls = [], probeLine, probeDots = [];
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
    probeLine = el("line", { x1: 0, y1: 40, x2: 0, y2: 440, stroke: "#b87018", "stroke-width": 1.5, "stroke-dasharray": "4 3" });
    svg.appendChild(probeLine);
    probeDots = [];
    for (i = 0; i < WINDOWS.length; i++) {
      var d = el("circle", { cx: 0, cy: 0, r: 6, fill: "#b87018", stroke: "#ffffff", "stroke-width": 1.5 });
      svg.appendChild(d);
      probeDots.push(d);
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

  var readout = document.getElementById("readout");
  var legendEl = document.getElementById("legend");
  var probeRow = document.getElementById("probe-row");
  var statusEl = document.getElementById("status");
  var yearIn = document.getElementById("year");
  var packetIn = document.getElementById("packet");

  function packet() { return Math.pow(10, state.packetLog); }

  function render() {
    var y = YEARS[state.year];
    var m = packet();
    document.getElementById("pool").textContent = y.totalCompute + " (" + y.year + " buildout)";
    document.getElementById("year-label").textContent = String(y.year);
    document.getElementById("packet-label").textContent = fmtPacket(m);
    document.getElementById("gpu-note").textContent = "Packet collection in " + y.year + ": " + y.gpuNote + ".";
    if (String(yearIn.value) !== String(state.year)) yearIn.value = state.year;
    if (String(packetIn.value) !== String(state.packetLog)) packetIn.value = state.packetLog;
    var i;
    for (i = 0; i < WINDOWS.length; i++) {
      curveEls[i].setAttribute("d", curvePath(WINDOWS[i].hours, m));
      curveEls[i].setAttribute("visibility", state.visible[i] ? "visible" : "hidden");
    }
    var px = xOf(state.probeLog);
    probeLine.setAttribute("x1", px); probeLine.setAttribute("x2", px);
    var size = Math.pow(10, state.probeLog);
    for (i = 0; i < WINDOWS.length; i++) {
      var p = pDetected(size, WINDOWS[i].hours, m);
      probeDots[i].setAttribute("cx", px);
      probeDots[i].setAttribute("cy", yOf(p));
      probeDots[i].setAttribute("visibility", state.visible[i] ? "visible" : "hidden");
    }
    // legend buttons
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
    }
    // readout table
    readout.textContent = "";
    var cap = h("div", null, "Rogue deployment of " + fmtSize(state.probeLog) + " H100e, packets of " + fmtPacket(m) + ", 1% budget:");
    readout.appendChild(cap);
    var table = h("table");
    var thead = h("tr"); thead.appendChild(h("th", null, "Window")); thead.appendChild(h("th", "n", "Rogue packets N_fake")); thead.appendChild(h("th", "n", "P(detected)"));
    table.appendChild(thead);
    for (i = 0; i < WINDOWS.length; i++) {
      var tr = h("tr");
      var nf = size * WINDOWS[i].hours / m;
      tr.appendChild(h("td", null, "within " + WINDOWS[i].label + (state.visible[i] ? "" : " (hidden)")));
      tr.appendChild(h("td", "n", nf >= 100 ? Math.round(nf).toLocaleString("en-US") : (Math.round(nf * 100) / 100).toString()));
      tr.appendChild(h("td", "n", fmtP(pDetected(size, WINDOWS[i].hours, m))));
      table.appendChild(tr);
    }
    readout.appendChild(table);
    var doneNow = isDone();
    if (doneNow) {
      statusEl.textContent = "Done: you have changed the settings and read " + state.sizesRead.length + " rogue deployment sizes.";
    } else if (state.explored) {
      statusEl.textContent = "Settings changed. Now press at least three rogue deployment sizes (" + state.sizesRead.length + " of 3 read).";
    } else {
      statusEl.textContent = "Move a slider to change the pool year or packet size, then press at least three rogue deployment sizes (" + state.sizesRead.length + " of 3 read).";
    }
    statusEl.classList.toggle("is-done", doneNow);
  }

  function summary() {
    var y = YEARS[state.year], m = packet(), size = Math.pow(10, state.probeLog);
    var parts = [];
    for (var i = 0; i < WINDOWS.length; i++) parts.push("within " + WINDOWS[i].label + " " + fmtP(pDetected(size, WINDOWS[i].hours, m)));
    return "Rogue deployment chart. Year " + y.year + " (pool " + y.totalCompute + ", " + y.gpuNote + "), packet size " + fmtPacket(m) + ", recomputation budget 1%. Reading at a rogue deployment of " + fmtSize(state.probeLog) + " H100e: " + parts.join(", ") + ". Hidden series: " + (WINDOWS.filter(function (w, i) { return !state.visible[i]; }).map(function (w) { return w.label; }).join(", ") || "none") + ". " + (state.explored ? "The learner has changed the sliders from the default." : "Sliders still at the default (2034, 100 H100e-hours).") + " Rogue sizes read from the size buttons: " + (state.sizesRead.length ? state.sizesRead.map(function (k) { return SIZE_LABELS[k] + " H100e"; }).join(", ") : "none") + ".";
  }

  function persist() {
    var json = { year: state.year, packetLog: state.packetLog, probeLog: state.probeLog, visible: state.visible.slice(), explored: state.explored, sizesRead: state.sizesRead.slice() };
    if (window.Lens) {
      Lens.saveState(json, summary());
      if (isDone() && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("ai-2040-rogue-detection", JSON.stringify(json)); } catch (e) {}
    }
  }

  // controls
  yearIn.addEventListener("input", function () {
    state.year = parseInt(yearIn.value, 10);
    state.packetLog = Math.log10(YEARS[state.year].defaultPacket);
    state.explored = true;
    render(); persist();
  });
  packetIn.addEventListener("input", function () {
    state.packetLog = parseFloat(packetIn.value);
    state.explored = true;
    render(); persist();
  });
  WINDOWS.forEach(function (w, i) {
    var b = h("button", null);
    b.type = "button";
    var sw = h("span", "swatch " + w.cls);
    b.appendChild(sw);
    b.appendChild(h("span", null, "within " + w.label));
    b.appendChild(h("span", "state sr", ""));
    b.querySelector(".state").style.fontSize = "11px";
    b.querySelector(".state").style.color = "#5a5a5a";
    b.addEventListener("click", function () { state.visible[i] = !state.visible[i]; render(); persist(); });
    legendEl.appendChild(b);
  });
  for (var k = 0; k <= 7; k++) {
    (function (k) {
      var b = h("button", null, SIZE_LABELS[k] + " H100e");
      b.type = "button";
      b.dataset.log = String(k);
      b.addEventListener("click", function () { state.probeLog = k; if (state.sizesRead.indexOf(k) === -1) state.sizesRead.push(k); render(); persist(); });
      probeRow.appendChild(b);
    })(k);
  }
  // hover / pointer on the chart moves the probe
  function pointerLog(evt) {
    var rect = svg.getBoundingClientRect();
    if (!rect.width) return null;
    var x = (evt.clientX - rect.left) / rect.width * 1000;
    var lg = (x - 110) / 830 * 7;
    if (lg < 0) lg = 0; if (lg > 7) lg = 7;
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
      if (typeof saved.year === "number" && saved.year >= 0 && saved.year < YEARS.length) state.year = saved.year;
      if (typeof saved.packetLog === "number" && saved.packetLog >= 0 && saved.packetLog <= 4) state.packetLog = Math.round(saved.packetLog);
      if (typeof saved.probeLog === "number" && saved.probeLog >= 0 && saved.probeLog <= 7) state.probeLog = saved.probeLog;
      if (Array.isArray(saved.visible) && saved.visible.length === 3) state.visible = saved.visible.map(function (v) { return !!v; });
      if (saved.explored) state.explored = true;
      if (Array.isArray(saved.sizesRead)) state.sizesRead = saved.sizesRead.filter(function (k) { return typeof k === "number" && k >= 0 && k <= 7; });
    }
    completed = !!(meta && meta.completed);
    if (completed) { state.explored = true; if (state.sizesRead.length < 3) state.sizesRead = [0, 1, 2]; }
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

---
id: '4ad43f6b-6fa8-430c-b8e4-a2d0ab0768bc'
title: Chip flow restrictions, 2029 and 2032
summary_for_tutor: "An interactive reproduction of the AI 2040 verification supplement's two 'Chip Flow Restrictions' scatter charts (2029 and 2032). Devices from an iPhone 16 Pro Max to a GB200 NVL72 rack are plotted by cross-chip interconnect speed (GB/s, log scale) against compute per device (H100e, log scale); dot size encodes memory capacity and a filled accent dot means HBM-class memory bandwidth (at or above about 1.5 TB/s). The 2029 view draws the dashed Tier 0 (unrestricted consumer) versus Tier 1 (subject to the deal: inference-only or cold storage) boundary at about 50 GB/s interconnect and 0.4 H100e; the 2032 view instead draws the AI-relevant floor at 4,000 TPP (about 0.25 H100e) with the 30M H100e unverified edge-compute cap (25M pre-deal plus 5M new credits; verified edge compute exempt). The learner switches between the two years and hovers or presses a device to read its exact numbers and its tier or floor status. Done means they have viewed both years and inspected at least three devices."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Chip flow restrictions, 2029 and 2032</title>
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), charts "Chip Flow Restrictions, 2029" and "Chip Flow Restrictions, 2032" (ChipRestrictions2029 and ChipRestrictions2032 components). -->
<!-- Data: device names, compute, interconnect, memory and bandwidth values, the axis ranges, the dot-size formula r = 2 + 2 log10(memory / 8), the HBM threshold (1500 GB/s), the 2029 tier boundary (interconnect 50 GB/s, compute 0.4 H100e) and the 2032 floor (4000 / 15800 H100e) are copied from the page's chunks 6617 and 8343 (the React components). Nothing is read by eye. -->
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
  h2 { font-size: 17px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 4px; }
  .lede { color: var(--muted); margin: 4px 0 12px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .years { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 8px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .years button.is-seen::after { content: " ✓"; color: var(--muted); }
  .layout { display: grid; grid-template-columns: minmax(0, 1fr) 260px; gap: 16px; align-items: start; }
  .chart { width: 100%; height: auto; display: block; }
  .chart text { font-family: var(--font-ui); }
  .chart .dev { cursor: pointer; }
  .chart .dev circle.ring { fill: none; stroke: var(--accent); stroke-width: 3; opacity: 0; }
  .chart .dev.is-active circle.ring { opacity: 1; }
  .chart .dev.is-seen text { text-decoration: underline; text-decoration-color: #c9c4b8; }
  .side { display: flex; flex-direction: column; gap: 10px; }
  .detail { border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 10px 12px; min-height: 120px; }
  .detail h2 { margin-bottom: 4px; }
  .detail dl { margin: 0; display: grid; grid-template-columns: auto 1fr; gap: 2px 10px; font-size: 13px; }
  .detail dt { color: var(--muted); }
  .detail dd { margin: 0; font-variant-numeric: tabular-nums; }
  .detail .verdict { margin: 8px 0 0; font-weight: 600; }
  .detail .verdict.tier1, .detail .verdict.above { color: var(--accent); }
  .policy { font-size: 12px; color: var(--muted); border-top: 1px solid var(--border); padding-top: 8px; }
  .policy strong { color: var(--text); }
  .devlist { display: flex; flex-wrap: wrap; gap: 6px; }
  .devlist button { padding: 4px 8px; font-size: 12px; }
  .devlist button.is-seen::after { content: " ✓"; color: var(--muted); }
  .legend { font-size: 12px; color: var(--muted); display: flex; flex-wrap: wrap; gap: 4px 16px; margin-top: 8px; }
  .legend .k { display: inline-flex; align-items: center; gap: 6px; }
  .legend .d { display: inline-block; width: 12px; height: 12px; border-radius: 50%; background: var(--text); }
  .legend .d.hbm { background: var(--accent); }
  .legend .d.ring { background: none; border: 1px dashed var(--text); }
  .status { font-size: 12px; color: var(--muted); margin-top: 8px; }
  .status.is-done { color: var(--text); font-weight: 500; }
  @media (max-width: 700px) { .layout { grid-template-columns: 1fr; } body { padding: 10px; } }
</style>
</head>
<body>
<p class="eyebrow">Interactive chart</p>
<h1>Chip flow restrictions, 2029 and 2032</h1>
<p class="lede">Where familiar devices sit on interconnect speed and compute, and which side of the deal's line they fall on. Switch the year, then hover or press a device to read its numbers.</p>

<div class="card">
  <div class="years" id="years" role="group" aria-label="Year"></div>
  <div class="layout">
    <div>
      <svg id="chart" class="chart" viewBox="0 0 760 640" role="img" aria-label="Scatter chart of devices by interconnect speed and compute"></svg>
      <div class="legend" id="legend"></div>
    </div>
    <div class="side">
      <div class="detail" id="detail" aria-live="polite"></div>
      <div class="policy" id="policy"></div>
      <div class="devlist" id="devlist" aria-label="Devices"></div>
    </div>
  </div>
  <p class="status" id="status"></p>
</div>

<script>
(function () {
  var VIEWS = {
    "2029": {
      title: "Chip Flow Restrictions, 2029",
      yLabel: "Compute (H100e)",
      boundary: { interconnect: 50, compute: 0.4 },
      tier0: ["Tier 0: Unrestricted", "consumer"],
      tier1: ["Tier 1: Subject to deal", "inference-only or cold storage"],
      memoryNote: "tier 1 above 10 TB (scale-up)",
      bandwidthNote: "tier 1 above HBM2 (~1.5 TB/s)",
      devices: [
        { name: "iPhone 16 Pro Max", compute: 0.011, interconnect: 1.25, memory: 8, bandwidth: 150, lx: 8, ly: -8, anchor: "start" },
        { name: "Tesla HW3", compute: 0.061, interconnect: 0.125, memory: 16, bandwidth: 384, lx: 8, ly: -8, anchor: "start" },
        { name: "DGX Spark", compute: 0.25, interconnect: 25, memory: 128, bandwidth: 273, lx: -10, ly: -10, anchor: "end" },
        { name: "M4 Max MacBook", compute: 0.035, interconnect: 10, memory: 128, bandwidth: 819, lx: -8, ly: 16, anchor: "end" },
        { name: "RTX 4090", compute: 0.17, interconnect: 32, memory: 24, bandwidth: 1008, lx: 10, ly: 16, anchor: "start" },
        { name: "H20", compute: 0.3, interconnect: 64, memory: 96, bandwidth: 4000, lx: 10, ly: 3, anchor: "start" },
        { name: "RTX 5090", compute: 0.33, interconnect: 64, memory: 32, bandwidth: 1792, lx: 10, ly: -8, anchor: "start" },
        { name: "H100 (PCIe)", compute: 1, interconnect: 64, memory: 80, bandwidth: 3350, lx: -10, ly: -8, anchor: "end" },
        { name: "DGX 8×H100", compute: 8, interconnect: 400, memory: 640, bandwidth: 26800, lx: 0, ly: -14, anchor: "middle" },
        { name: "B200", compute: 2.5, interconnect: 1800, memory: 192, bandwidth: 8000, lx: 10, ly: -8, anchor: "start" },
        { name: "GB200 NVL72", compute: 180, interconnect: 3600, memory: 13400, bandwidth: 8000, lx: 0, ly: -14, anchor: "middle" }
      ]
    },
    "2032": {
      title: "Chip Flow Restrictions, 2032",
      yLabel: "Compute per device (H100e)",
      floor: 4000 / 15800,
      floorLabel: "AI-relevant floor: 4,000 TPP ≈ 0.25 H100e (compute supplement §1.1)",
      consumer: ["Consumer compute", "below the AI-relevant floor, capped at 30M H100e"],
      cap: { total: 30, preDeal: 25, credits: 5 },
      devices: [
        { name: "iPhone 16 Pro Max", compute: 0.011, interconnect: 1.25, memory: 8, bandwidth: 150, lx: 8, ly: 14, anchor: "start" },
        { name: "Tesla HW3", compute: 0.061, interconnect: 0.125, memory: 16, bandwidth: 384, lx: 8, ly: -8, anchor: "start" },
        { name: "DGX Spark", compute: 0.12, interconnect: 25, memory: 128, bandwidth: 273, lx: -10, ly: -10, anchor: "end" },
        { name: "M4 Pro MacBook", compute: 0.035, interconnect: 10, memory: 128, bandwidth: 819, lx: -8, ly: 16, anchor: "end" },
        { name: "RTX 4090", compute: 0.33, interconnect: 32, memory: 24, bandwidth: 1008, lx: 10, ly: 16, anchor: "start" },
        { name: "H20", compute: 0.148, interconnect: 64, memory: 96, bandwidth: 4000, lx: 10, ly: 3, anchor: "start" },
        { name: "RTX 5090", compute: 0.419, interconnect: 64, memory: 32, bandwidth: 1792, lx: 10, ly: -8, anchor: "start" },
        { name: "H100 (PCIe)", compute: 1, interconnect: 64, memory: 80, bandwidth: 3350, lx: -10, ly: -8, anchor: "end" },
        { name: "DGX 8×H100", compute: 8, interconnect: 400, memory: 640, bandwidth: 26800, lx: 0, ly: -14, anchor: "middle" },
        { name: "GB200 NVL72", compute: 180, interconnect: 3600, memory: 13400, bandwidth: 8000, lx: 0, ly: -14, anchor: "middle" }
      ]
    }
  };
  var X_TICKS = [{ v: 0.1, label: "0.1 GB/s" }, { v: 1, label: "1" }, { v: 10, label: "10" }, { v: 100, label: "100" }, { v: 1000, label: "1 TB/s" }, { v: 10000, label: "10 TB/s" }];
  var Y_TICKS = [{ v: 0.001, label: "0.001" }, { v: 0.01, label: "0.01" }, { v: 0.1, label: "0.1" }, { v: 1, label: "1" }, { v: 10, label: "10" }, { v: 100, label: "100" }, { v: 1000, label: "1K" }];
  var HBM = 1500;
  var NS = "http://www.w3.org/2000/svg";
  var PX0 = 100, PX1 = 720, PY0 = 60, PY1 = 560;

  var state = { year: "2029", device: null, seenYears: {}, seenDevices: {} };
  var completed = false;

  function sx(v) { return PX0 + (Math.log10(v) - Math.log10(0.1)) / (Math.log10(10000) - Math.log10(0.1)) * (PX1 - PX0); }
  function sy(v) { return PY1 - (Math.log10(v) - Math.log10(0.001)) / (Math.log10(1000) - Math.log10(0.001)) * (PY1 - PY0); }
  function rad(memory) { return 2 + 2 * Math.log10(memory / 8); }
  function fmtGB(gb) { return gb >= 1000 ? (Math.round(gb / 100) / 10) + " TB" : gb + " GB"; }
  function fmtGBs(v) { return v >= 1000 ? (Math.round(v / 100) / 10) + " TB/s" : v + " GB/s"; }
  function fmtNum(v) { return v >= 100 ? String(Math.round(v)) : String(v); }
  function tierOf(view, d) {
    if (view.boundary) return (d.interconnect < view.boundary.interconnect && d.compute < view.boundary.compute) ? "tier0" : "tier1";
    return d.compute >= view.floor ? "above" : "below";
  }
  function tierText(view, d) {
    var t = tierOf(view, d);
    if (t === "tier0") return "Tier 0: Unrestricted consumer";
    if (t === "tier1") return "Tier 1: Subject to deal (inference-only or cold storage)";
    if (t === "above") return "Above the AI-relevant floor (4,000 TPP ≈ 0.25 H100e)";
    return "Below the AI-relevant floor: consumer compute, under the 30M H100e unverified edge-compute cap";
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

  var devGroups = {};
  function drawChart() {
    while (svg.firstChild) svg.removeChild(svg.firstChild);
    devGroups = {};
    var view = VIEWS[state.year];
    var i;
    X_TICKS.forEach(function (t) { svg.appendChild(el("line", { x1: sx(t.v), y1: PY0, x2: sx(t.v), y2: PY1, stroke: "#1a1a1a", "stroke-width": 0.35, "stroke-dasharray": "1.5 3" })); });
    Y_TICKS.forEach(function (t) { svg.appendChild(el("line", { x1: PX0, y1: sy(t.v), x2: PX1, y2: sy(t.v), stroke: "#1a1a1a", "stroke-width": 0.35, "stroke-dasharray": "1.5 3" })); });
    if (view.boundary) {
      var bx = sx(view.boundary.interconnect), by = sy(view.boundary.compute);
      svg.appendChild(el("line", { x1: PX0, y1: by, x2: bx, y2: by, stroke: "#b87018", "stroke-width": 2, "stroke-dasharray": "8 4" }));
      svg.appendChild(el("line", { x1: bx, y1: by, x2: bx, y2: PY1, stroke: "#b87018", "stroke-width": 2, "stroke-dasharray": "8 4" }));
      svg.appendChild(el("text", { x: (PX0 + bx) / 2, y: PY1 - 28, "text-anchor": "middle", "font-size": 19, "font-weight": 700, fill: "#1a1a1a" }, view.tier0[0]));
      svg.appendChild(el("text", { x: (PX0 + bx) / 2, y: PY1 - 8, "text-anchor": "middle", "font-size": 14, "font-style": "italic", fill: "#1a1a1a" }, view.tier0[1]));
      svg.appendChild(el("text", { x: (PX0 + PX1) / 2 + 60, y: PY0 + 30, "text-anchor": "middle", "font-size": 19, "font-weight": 700, fill: "#b87018" }, view.tier1[0]));
      svg.appendChild(el("text", { x: (PX0 + PX1) / 2 + 60, y: PY0 + 50, "text-anchor": "middle", "font-size": 14, "font-style": "italic", fill: "#b87018" }, view.tier1[1]));
    } else {
      var fy = sy(view.floor);
      svg.appendChild(el("line", { x1: PX0, y1: fy, x2: PX1, y2: fy, stroke: "#b87018", "stroke-width": 2, "stroke-dasharray": "8 4" }));
      svg.appendChild(el("text", { x: PX1 - 8, y: fy - 8, "text-anchor": "end", "font-size": 13, "font-style": "italic", fill: "#1a1a1a" }, view.floorLabel));
      svg.appendChild(el("text", { x: PX0 + 14, y: PY1 - 34, "font-size": 19, "font-weight": 700, fill: "#1a1a1a" }, view.consumer[0]));
      svg.appendChild(el("text", { x: PX0 + 14, y: PY1 - 14, "font-size": 13, "font-style": "italic", fill: "#1a1a1a" }, view.consumer[1]));
    }
    view.devices.forEach(function (d) {
      var cx = sx(d.interconnect), cy = sy(d.compute), r = rad(d.memory);
      var g = el("g", { "class": "dev" });
      g.appendChild(el("circle", { "class": "ring", cx: cx, cy: cy, r: r + 5 }));
      g.appendChild(el("circle", { cx: cx, cy: cy, r: r, fill: d.bandwidth >= HBM ? "#b87018" : "#1a1a1a", stroke: "#ffffff", "stroke-width": 1 }));
      g.appendChild(el("circle", { cx: cx, cy: cy, r: Math.max(r + 6, 12), fill: "transparent" }));
      g.appendChild(el("text", { x: cx + d.lx, y: cy + d.ly, "text-anchor": d.anchor, "font-size": 13, "font-weight": 600, fill: "#1a1a1a", style: "paint-order:stroke;stroke:#ffffff;stroke-width:3px" }, d.name));
      g.addEventListener("pointerenter", function () { select(d.name, false); });
      g.addEventListener("click", function () { select(d.name, true); });
      svg.appendChild(g);
      devGroups[d.name] = g;
    });
    svg.appendChild(el("line", { x1: PX0, y1: PY1, x2: PX1, y2: PY1, stroke: "#1a1a1a", "stroke-width": 1.5 }));
    svg.appendChild(el("line", { x1: PX0, y1: PY0, x2: PX0, y2: PY1, stroke: "#1a1a1a", "stroke-width": 1.5 }));
    X_TICKS.forEach(function (t) {
      svg.appendChild(el("line", { x1: sx(t.v), y1: PY1, x2: sx(t.v), y2: PY1 + 5, stroke: "#1a1a1a", "stroke-width": 1.5 }));
      svg.appendChild(el("text", { x: sx(t.v), y: PY1 + 24, "text-anchor": "middle", "font-size": 14, fill: "#1a1a1a" }, t.label));
    });
    Y_TICKS.forEach(function (t) {
      svg.appendChild(el("line", { x1: PX0 - 5, y1: sy(t.v), x2: PX0, y2: sy(t.v), stroke: "#1a1a1a", "stroke-width": 1.5 }));
      svg.appendChild(el("text", { x: PX0 - 10, y: sy(t.v) + 5, "text-anchor": "end", "font-size": 14, fill: "#1a1a1a" }, t.label));
    });
    svg.appendChild(el("text", { x: (PX0 + PX1) / 2, y: PY1 + 58, "text-anchor": "middle", "font-size": 17, "font-weight": 600, fill: "#1a1a1a" }, "Cross-Chip Interconnect Speed (GB/s)"));
    svg.appendChild(el("text", { x: 34, y: (PY0 + PY1) / 2, "text-anchor": "middle", "font-size": 17, "font-weight": 600, fill: "#1a1a1a", transform: "rotate(-90, 34, " + (PY0 + PY1) / 2 + ")" }, view.yLabel));
    svg.appendChild(el("text", { x: PX0, y: 30, "font-size": 20, "font-weight": 600, fill: "#1a1a1a", "font-family": "Newsreader, Georgia, serif" }, view.title));
  }

  var detail = document.getElementById("detail");
  var policy = document.getElementById("policy");
  var devlist = document.getElementById("devlist");
  var yearsEl = document.getElementById("years");
  var legendEl = document.getElementById("legend");
  var statusEl = document.getElementById("status");

  function seenDeviceCount() { var n = 0; for (var k in state.seenDevices) if (state.seenDevices[k]) n++; return n; }
  function isDone() { return state.seenYears["2029"] && state.seenYears["2032"] && seenDeviceCount() >= 3; }

  function renderSide() {
    var view = VIEWS[state.year];
    detail.textContent = "";
    var d = null;
    view.devices.forEach(function (x) { if (x.name === state.device) d = x; });
    if (!d) {
      detail.appendChild(h("h2", null, view.title));
      detail.appendChild(h("p", null, "Hover or press a device to read its compute, interconnect, memory and bandwidth, and which side of the line it falls on."));
    } else {
      detail.appendChild(h("h2", null, d.name));
      var dl = h("dl");
      function row(k, v) { dl.appendChild(h("dt", null, k)); dl.appendChild(h("dd", null, v)); }
      row("Compute", fmtNum(d.compute) + " H100e");
      row("Interconnect", fmtGBs(d.interconnect));
      row("Memory", fmtGB(d.memory));
      row("Memory bandwidth", fmtGBs(d.bandwidth) + (d.bandwidth >= HBM ? " (HBM-class)" : " (below HBM-class)"));
      detail.appendChild(dl);
      var v = h("p", "verdict " + tierOf(view, d), tierText(view, d));
      detail.appendChild(v);
    }
    policy.textContent = "";
    if (view.boundary) {
      var p1 = h("p"); p1.appendChild(h("strong", null, "Memory capacity: ")); p1.appendChild(document.createTextNode(view.memoryNote + ".")); policy.appendChild(p1);
      var p2 = h("p"); p2.appendChild(h("strong", null, "Memory bandwidth: ")); p2.appendChild(document.createTextNode(view.bandwidthNote + ".")); policy.appendChild(p2);
      var p3 = h("p"); p3.appendChild(h("strong", null, "Dashed boundary: ")); p3.appendChild(document.createTextNode("about 50 GB/s interconnect and 0.4 H100e compute.")); policy.appendChild(p3);
    } else {
      var q1 = h("p"); q1.appendChild(h("strong", null, "Unverified edge-compute cap: ")); q1.appendChild(document.createTextNode(view.cap.total + "M H100e: " + view.cap.preDeal + "M already in world (pre-deal) + " + view.cap.credits + "M new credits.")); policy.appendChild(q1);
      policy.appendChild(h("p", null, "Verified edge compute → exempt."));
    }
    devlist.textContent = "";
    view.devices.forEach(function (x) {
      var b = h("button", null, x.name);
      b.type = "button";
      b.classList.toggle("is-active", x.name === state.device);
      b.classList.toggle("is-seen", !!state.seenDevices[x.name]);
      b.setAttribute("aria-pressed", x.name === state.device ? "true" : "false");
      b.addEventListener("click", function () { select(x.name, true); });
      devlist.appendChild(b);
    });
    var yb = yearsEl.querySelectorAll("button");
    for (var i = 0; i < yb.length; i++) {
      yb[i].classList.toggle("is-active", yb[i].dataset.year === state.year);
      yb[i].classList.toggle("is-seen", !!state.seenYears[yb[i].dataset.year]);
      yb[i].setAttribute("aria-pressed", yb[i].dataset.year === state.year ? "true" : "false");
    }
    for (var name in devGroups) {
      devGroups[name].classList.toggle("is-active", name === state.device);
      devGroups[name].classList.toggle("is-seen", !!state.seenDevices[name]);
    }
    legendEl.textContent = "";
    function key(cls, text) { var k = h("span", "k"); k.appendChild(h("span", "d " + cls)); k.appendChild(h("span", null, text)); legendEl.appendChild(k); }
    key("hbm", "≥ ~1.5 TB/s memory bandwidth (HBM-class)");
    key("", "below ~1.5 TB/s");
    key("ring", "dot size: memory capacity (8 GB to 13 TB)");
    var n = seenDeviceCount();
    statusEl.textContent = isDone() ? "Both years viewed, " + n + " devices inspected. Compare where the H20 and RTX 4090 land in each year." : "Progress: " + (state.seenYears["2029"] ? "2029 viewed" : "2029 not yet viewed") + ", " + (state.seenYears["2032"] ? "2032 viewed" : "2032 not yet viewed") + ", " + n + " of 3 devices inspected.";
    statusEl.classList.toggle("is-done", !!isDone());
  }

  function summary() {
    var view = VIEWS[state.year];
    var d = null;
    view.devices.forEach(function (x) { if (x.name === state.device) d = x; });
    var s = "Chip flow restrictions chart, showing " + state.year + ". ";
    if (d) s += "Selected device " + d.name + ": " + fmtNum(d.compute) + " H100e, " + fmtGBs(d.interconnect) + " interconnect, " + fmtGB(d.memory) + " memory, " + fmtGBs(d.bandwidth) + " bandwidth; " + tierText(view, d) + ". ";
    else s += "No device selected. ";
    s += "Years viewed: " + Object.keys(state.seenYears).filter(function (k) { return state.seenYears[k]; }).join(", ") + ". Devices inspected: " + Object.keys(state.seenDevices).filter(function (k) { return state.seenDevices[k]; }).join(", ") + ".";
    return s;
  }

  function persist() {
    var json = { year: state.year, device: state.device, seenYears: state.seenYears, seenDevices: state.seenDevices };
    if (window.Lens) {
      Lens.saveState(json, summary());
      if (isDone() && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("ai-2040-chip-flow", JSON.stringify(json)); } catch (e) {}
    }
  }

  var hoverTimer = null;
  function select(name, commit) {
    state.device = name;
    state.seenDevices[name] = true;
    renderSide();
    if (commit) persist(); else { clearTimeout(hoverTimer); hoverTimer = setTimeout(persist, 400); }
  }
  function setYear(y) {
    state.year = y;
    state.seenYears[y] = true;
    var exists = VIEWS[y].devices.some(function (d) { return d.name === state.device; });
    if (!exists) state.device = null;
    drawChart();
    renderSide();
    persist();
  }

  ["2029", "2032"].forEach(function (y) {
    var b = h("button", null, y);
    b.type = "button";
    b.dataset.year = y;
    b.addEventListener("click", function () { setYear(y); });
    yearsEl.appendChild(b);
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (saved.year === "2029" || saved.year === "2032") state.year = saved.year;
      if (typeof saved.device === "string") state.device = saved.device;
      if (saved.seenYears && typeof saved.seenYears === "object") { state.seenYears = {}; for (var k in saved.seenYears) if (saved.seenYears[k]) state.seenYears[k] = true; }
      if (saved.seenDevices && typeof saved.seenDevices === "object") { state.seenDevices = {}; for (var j in saved.seenDevices) if (saved.seenDevices[j]) state.seenDevices[j] = true; }
    }
    completed = !!(meta && meta.completed);
    state.seenYears[state.year] = true;
    drawChart();
    renderSide();
  }

  state.seenYears[state.year] = true;
  drawChart();
  renderSide();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    try { var raw = localStorage.getItem("ai-2040-chip-flow"); if (raw) hydrate(JSON.parse(raw), null); } catch (e) {}
  }
})();
</script>
</body>
</html>

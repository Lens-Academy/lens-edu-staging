---
id: 'cd75dc88-188d-401f-a6c9-27e9a4264b39'
title: Chip flow restrictions, 2032
summary_for_tutor: "A static scatter figure, Chip Flow Restrictions, 2032: ten devices plotted by cross-chip interconnect speed on a log x axis running 0.1 GB/s to 10 TB/s against compute per device on a log y axis running 0.001 to 1,000 H100e. Dot size encodes memory capacity (8 GB up to 13 TB) and a filled accent dot means HBM-class memory bandwidth, at or above about 1.5 TB/s. The deal's line here is a single dashed accent horizontal: the AI-relevant floor of 4,000 TPP, about 0.25 H100e, drawn straight across the chart at that compute level. Below it lies consumer compute, which the deal caps at 30M H100e of unverified edge compute, and that band holds the iPhone 16 Pro Max, Tesla HW3, M4 Pro MacBook, DGX Spark and, now that its rating has been revised down to 0.148 H100e, the H20. Above the floor sit the RTX 4090 at 0.33 H100e, the RTX 5090 at 0.42, the H100 PCIe at 1, the DGX 8-by-H100 node at 8, and the GB200 NVL72 rack at 180 H100e with 3.6 TB/s of interconnect and 13 TB of memory. Interconnect speed spreads the devices left to right but no longer sets the boundary."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Chip flow restrictions, 2032</title>
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), chart "Chip Flow Restrictions, 2032" (ChipRestrictions2032 component). Static figure: no controls, no state. -->
<!-- Data: device names, compute, interconnect, memory and bandwidth values, the axis ranges, the dot-size formula r = 2 + 2 log10(memory / 8), the HBM threshold (1500 GB/s), the AI-relevant floor (4000 / 15800 H100e) and the 30M H100e cap are copied from the page's React component. Nothing is read by eye. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --accent: #b87018;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .chartbox { overflow-x: auto; }
  .chart { width: 100%; min-width: 720px; height: auto; display: block; }
  .chart text { font-family: var(--font-ui); }
  .legend { font-size: 12px; color: var(--muted); display: flex; flex-wrap: wrap; gap: 4px 16px; margin-top: 8px; }
  .legend .k { display: inline-flex; align-items: center; gap: 6px; }
  .legend .d { display: inline-block; width: 12px; height: 12px; border-radius: 50%; background: var(--text); }
  .legend .d.hbm { background: var(--accent); }
  .legend .d.ring { background: none; border: 1px dashed var(--text); }
  .cap { font-size: 12px; color: var(--muted); margin: 8px 0 0; }
  .cap strong { color: var(--text); }
  @media (max-width: 700px) { body { padding: 10px; } }
</style>
</head>
<body>
<div class="card">
  <div class="chartbox"><svg id="chart" class="chart" viewBox="0 0 760 640" role="img" aria-label="Chip flow restrictions, 2032: scatter chart of devices by interconnect speed and compute"></svg></div>
  <div class="legend">
    <span class="k"><span class="d hbm"></span><span>at or above ~1.5 TB/s memory bandwidth (HBM-class)</span></span>
    <span class="k"><span class="d"></span><span>below ~1.5 TB/s</span></span>
    <span class="k"><span class="d ring"></span><span>dot size: memory capacity (8 GB to 13 TB)</span></span>
  </div>
  <p class="cap"><strong>Unverified edge-compute cap, 30M H100e:</strong> 25M already in world (pre-deal) plus 5M new credits. Verified edge compute is exempt.</p>
</div>

<script>
(function () {
  var TITLE = "Chip Flow Restrictions, 2032";
  var Y_LABEL = "Compute per device (H100e)";
  var FLOOR = 4000 / 15800;
  var FLOOR_LABEL = ["AI-relevant floor: 4,000 TPP ≈ 0.25 H100e", "(compute supplement §1.1)"];
  var CONSUMER = ["Consumer compute", "below the AI-relevant floor, capped at 30M H100e"];
  var DEVICES = [
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
  ];
  var X_TICKS = [{ v: 0.1, label: "0.1 GB/s" }, { v: 1, label: "1" }, { v: 10, label: "10" }, { v: 100, label: "100" }, { v: 1000, label: "1 TB/s" }, { v: 10000, label: "10 TB/s" }];
  var Y_TICKS = [{ v: 0.001, label: "0.001" }, { v: 0.01, label: "0.01" }, { v: 0.1, label: "0.1" }, { v: 1, label: "1" }, { v: 10, label: "10" }, { v: 100, label: "100" }, { v: 1000, label: "1K" }];
  var HBM = 1500;
  var NS = "http://www.w3.org/2000/svg";
  var PX0 = 100, PX1 = 720, PY0 = 60, PY1 = 560;

  function sx(v) { return PX0 + (Math.log10(v) - Math.log10(0.1)) / (Math.log10(10000) - Math.log10(0.1)) * (PX1 - PX0); }
  function sy(v) { return PY1 - (Math.log10(v) - Math.log10(0.001)) / (Math.log10(1000) - Math.log10(0.001)) * (PY1 - PY0); }
  function rad(memory) { return 2 + 2 * Math.log10(memory / 8); }

  var svg = document.getElementById("chart");
  function el(tag, attrs, text) {
    var n = document.createElementNS(NS, tag);
    for (var k in attrs) n.setAttribute(k, attrs[k]);
    if (text !== undefined) n.textContent = text;
    svg.appendChild(n);
    return n;
  }

  X_TICKS.forEach(function (t) { el("line", { x1: sx(t.v), y1: PY0, x2: sx(t.v), y2: PY1, stroke: "#1a1a1a", "stroke-width": 0.35, "stroke-dasharray": "1.5 3" }); });
  Y_TICKS.forEach(function (t) { el("line", { x1: PX0, y1: sy(t.v), x2: PX1, y2: sy(t.v), stroke: "#1a1a1a", "stroke-width": 0.35, "stroke-dasharray": "1.5 3" }); });

  var fy = sy(FLOOR);
  el("line", { x1: PX0, y1: fy, x2: PX1, y2: fy, stroke: "#b87018", "stroke-width": 2, "stroke-dasharray": "8 4" });
  el("text", { x: PX0 + 6, y: fy - 26, "font-size": 13, "font-style": "italic", fill: "#1a1a1a", style: "paint-order:stroke;stroke:#ffffff;stroke-width:3px" }, FLOOR_LABEL[0]);
  el("text", { x: PX0 + 6, y: fy - 10, "font-size": 13, "font-style": "italic", fill: "#1a1a1a", style: "paint-order:stroke;stroke:#ffffff;stroke-width:3px" }, FLOOR_LABEL[1]);
  el("text", { x: PX0 + 14, y: PY1 - 34, "font-size": 19, "font-weight": 700, fill: "#1a1a1a" }, CONSUMER[0]);
  el("text", { x: PX0 + 14, y: PY1 - 14, "font-size": 13, "font-style": "italic", fill: "#1a1a1a" }, CONSUMER[1]);

  DEVICES.forEach(function (d) {
    var cx = sx(d.interconnect), cy = sy(d.compute), r = rad(d.memory);
    el("circle", { cx: cx, cy: cy, r: r, fill: d.bandwidth >= HBM ? "#b87018" : "#1a1a1a", stroke: "#ffffff", "stroke-width": 1 });
    el("text", { x: cx + d.lx, y: cy + d.ly, "text-anchor": d.anchor, "font-size": 13, "font-weight": 600, fill: "#1a1a1a", style: "paint-order:stroke;stroke:#ffffff;stroke-width:3px" }, d.name);
  });

  el("line", { x1: PX0, y1: PY1, x2: PX1, y2: PY1, stroke: "#1a1a1a", "stroke-width": 1.5 });
  el("line", { x1: PX0, y1: PY0, x2: PX0, y2: PY1, stroke: "#1a1a1a", "stroke-width": 1.5 });
  X_TICKS.forEach(function (t) {
    el("line", { x1: sx(t.v), y1: PY1, x2: sx(t.v), y2: PY1 + 5, stroke: "#1a1a1a", "stroke-width": 1.5 });
    el("text", { x: sx(t.v), y: PY1 + 24, "text-anchor": "middle", "font-size": 14, fill: "#1a1a1a" }, t.label);
  });
  Y_TICKS.forEach(function (t) {
    el("line", { x1: PX0 - 5, y1: sy(t.v), x2: PX0, y2: sy(t.v), stroke: "#1a1a1a", "stroke-width": 1.5 });
    el("text", { x: PX0 - 10, y: sy(t.v) + 5, "text-anchor": "end", "font-size": 14, fill: "#1a1a1a" }, t.label);
  });
  el("text", { x: (PX0 + PX1) / 2, y: PY1 + 58, "text-anchor": "middle", "font-size": 17, "font-weight": 600, fill: "#1a1a1a" }, "Cross-Chip Interconnect Speed (GB/s)");
  el("text", { x: 34, y: (PY0 + PY1) / 2, "text-anchor": "middle", "font-size": 17, "font-weight": 600, fill: "#1a1a1a", transform: "rotate(-90, 34, " + (PY0 + PY1) / 2 + ")" }, Y_LABEL);
  el("text", { x: PX0, y: 30, "font-size": 20, "font-weight": 600, fill: "#1a1a1a", "font-family": "Newsreader, Georgia, serif" }, TITLE);
})();
</script>
</body>
</html>

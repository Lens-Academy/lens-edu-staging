---
id: '30fd2429-721c-48be-a347-aefe4fb95ca1'
title: Assurance curves for three verification budgets
summary_for_tutor: "A static line chart of confidence against coverage for three verification budgets, N_ver = 100, 10K and 10M audited packets, with both axes on log scales running from 0% up to 8 nines. Each curve plots confidence = 1 - exp(-N_ver * F*) against coverage = 1 - F*, where F* is the largest fraction of fake packets that could slip through undetected, so confidence falls as the coverage demanded rises. A budget reaches about 63% confidence at the coverage where N_ver * F* = 1: that is 99% coverage for N_ver = 100, 99.99% for 10K and 7 nines for 10M. One decade of coverage below each of those points the same budget sits at roughly 100% confidence (90%, 99.9% and 6 nines respectively), and one decade above it the confidence has collapsed towards nothing. The three curves have identical shape and are simply shifted sideways, which is the point of the figure: every 10x increase in the verification budget buys exactly one more decade of coverage at the same confidence."
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
<!-- Static figure: the source figure is a plain SVG line chart with no controls, so this carries no buttons, readout or state. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018;
    --font-ui: "DM Sans", Arial, sans-serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .chartbox { overflow-x: auto; }
  .chart { width: 100%; min-width: 720px; height: auto; display: block; }
  .chart text { font-family: var(--font-ui); }
  @media (max-width: 600px) { body { padding: 10px; } }
</style>
</head>
<body>
<div class="chartbox"><svg id="chart" class="chart" viewBox="0 0 1000 570" role="img" aria-label="Confidence against coverage, three curves for N_ver = 100, 10K and 10M"></svg></div>

<script>
(function () {
  var SERIES = [
    { label: "N_ver = 100", nVerified: 100, dash: "2 4" },
    { label: "N_ver = 10K", nVerified: 10000, dash: "9 6" },
    { label: "N_ver = 10M", nVerified: 10000000, dash: "" }
  ];
  var X_TICKS = [0, -1, -2, -3, -4, -5, -6, -7, -8];
  var Y_TICKS = [0, 0.9, 0.99, 0.999, 0.9999, 0.99999, 0.999999, 0.9999999, 0.99999999];
  var LEGEND_X = [190, 418, 646];
  var NS = "http://www.w3.org/2000/svg";

  function xOf(logF) { return 150 + (0 - logF) / 8 * 790; }
  function yOf(p) {
    var t = Math.log10(Math.max(1e-12, 1 - p));
    if (t < -8) t = -8;
    if (t > 0) t = 0;
    return 60 + (t - (-8)) / 8 * 380;
  }
  function confidence(n, logF) { return 1 - Math.exp(-n * Math.pow(10, logF)); }
  function trimZeros(s) {
    if (s.indexOf(".") < 0) return s;
    while (s.length > 1 && s.charAt(s.length - 1) === "0") s = s.slice(0, -1);
    if (s.charAt(s.length - 1) === ".") s = s.slice(0, -1);
    return s;
  }
  // Axis labels: only an exact power of ten gets the "n nines" name; anything
  // shallower prints as a percentage with enough decimals to stay distinct
  // from the tick either side of it.
  function fmtCoverage(logF) {
    if (logF >= 0) return "0%";
    var e = -logF;
    var whole = Math.abs(e - Math.round(e)) < 1e-9;
    if (whole && e > 4.01) return Math.round(e) + " nines";
    var dec = whole ? Math.max(0, Math.round(e) - 2) : Math.min(12, Math.max(0, Math.ceil(e) - 1));
    return trimZeros(((1 - Math.pow(10, logF)) * 100).toFixed(dec)) + "%";
  }
  function fmtAxisY(p) {
    if (p === 0) return "0";
    var e = -Math.log10(1 - p);
    return e <= 4.01 ? (100 * p).toFixed(Math.max(0, Math.round(e) - 2)) + "%" : Math.round(e) + " nines";
  }

  var svg = document.getElementById("chart");
  function el(tag, attrs, text) {
    var n = document.createElementNS(NS, tag);
    for (var k in attrs) n.setAttribute(k, attrs[k]);
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
    }
    for (i = 0; i < SERIES.length; i++) {
      var g = el("g", { transform: "translate(" + LEGEND_X[i] + ", 540)" });
      var swatch = el("line", { x1: 0, y1: 0, x2: 36, y2: 0, stroke: "#1a1a1a", "stroke-width": 3 });
      if (SERIES[i].dash) swatch.setAttribute("stroke-dasharray", SERIES[i].dash);
      g.appendChild(swatch);
      g.appendChild(el("text", { x: 48, y: 6, "font-size": 20, fill: "#1a1a1a" }, SERIES[i].label));
      svg.appendChild(g);
    }
  }

  drawChart();
})();
</script>
</body>
</html>


---
id: 'b29944d2-ffab-414e-99c0-ef830ad56bbd'
title: "AI Digest time horizons, step 3: extrapolating to 2030"
summary_for_tutor: "Graph 3 of the AI Digest time-horizons sequence (CC-BY, METR Time Horizon 1.1 data). The x axis now runs to 2030 and the y axis to a few hundred hours, so all measured models to Feb 2026 are squashed near zero (labels only on GPT-2, GPT-4 and Opus 4.6). The 7-month trend continues as a dashed orange line with a widening shaded band; the text beside it reads off 1 work day (8 hours) in 2027, 1 work week (40 hours) in 2028 and 1 work month (167 hours) in 2029. Hover and crosshair only."
height: auto
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>AI Digest time horizons, step 3: extrapolating to 2030</title>
<!-- Rebuilt for Lens from AI Digest, "A new Moore's Law for AI agents" (https://theaidigest.org/time-horizons, chart marked CC-BY 4.0),
     scroll step graph "c". Data and fit constants copied from AI Digest's chart component (TimeHorizonsViz.tsx in their page bundle, retrieved 2026-09-29);
     data: METR Time Horizon 1.1 (https://metr.org/blog/2026-1-29-time-horizon-1-1/). One of five widgets aidigest-time-horizons-a..e; they share this code and differ only in STATE. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root { --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif; }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 12px 8px 8px; font: 14px/1.5 var(--font-ui); color: var(--text); background: #fff; }
  .wrap { position: relative; }
  #chart svg { display: block; font-family: var(--font-ui); overflow: hidden; }
  .grid { stroke: var(--border); stroke-dasharray: 2,4; }
  .axis { stroke: #b8b3a8; stroke-width: 1; }
  .tick { font-size: 11px; fill: var(--muted); }
  .tick-sub { font-size: 10px; fill: #8a8a8a; }
  .ytitle { font-size: 12px; font-weight: 500; fill: var(--muted); }
  .caption { font-family: var(--font-heading); font-size: 18px; font-weight: 500; fill: var(--accent-hover); }
  .err { stroke: rgba(184,112,24,0.4); stroke-width: 0.5; }
  .pt { fill: var(--accent); stroke: #fff; stroke-width: 2; cursor: pointer; }
  .pt:hover, .pt:focus { fill: #d08a2c; outline: none; }
  .lbl { font-size: 12px; font-weight: 500; fill: var(--accent-hover); paint-order: stroke; stroke: #fff; stroke-width: 3px; stroke-linejoin: round; }
  @media (min-width: 640px) { .lbl { font-size: 13px; } .tick { font-size: 12px; } }
  .dbl { font-size: 12px; font-weight: 700; fill: var(--accent-hover); }
  .xh { stroke: rgba(154,92,16,0.4); stroke-width: 1; pointer-events: none; }
  #tip { position: absolute; display: none; z-index: 5; pointer-events: none; background: #fff; border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px; font-size: 12px; max-width: 260px; }
  #tip .strong { font-weight: 600; font-size: 13px; }
  #tip .muted { color: var(--muted); }
  #tip .small { font-size: 11px; }
  .legend { display: flex; flex-wrap: wrap; gap: 6px 16px; margin: 6px 0 0 8px; font-size: 12px; color: var(--muted); }
  .legend span { display: inline-flex; align-items: center; gap: 6px; }
  .legend i { display: inline-block; width: 22px; }
  .foot { margin: 8px 0 0 8px; font-size: 12px; color: #8a8a8a; }
  .foot a { color: var(--muted); }
</style>
</head>
<body>
<div class="wrap">
  <div id="chart"></div>
  <div id="tip" role="status"></div>
</div>
<div class="legend" id="legend"></div>
<p class="foot">Chart: <a href="https://theaidigest.org/time-horizons" target="_blank" rel="noopener">AI Digest</a>, <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" rel="noopener">CC-BY</a>, rebuilt for Lens. Data: <a href="https://metr.org/blog/2026-1-29-time-horizon-1-1/" target="_blank" rel="noopener">METR Time Horizon 1.1</a>.</p>
<script>
var STATE = {"showExtrapolation":true,"showErrorBars":false};

var DATA = [{"model":"GPT-2","modelPrettified":"GPT-2","date":"2019-02-14","p50":{"value":0.039762,"lower":0.002019,"upper":0.130397}},{"model":"davinci-002 (GPT-3)","modelPrettified":"GPT-3","date":"2020-05-28","p50":{"value":0.148793,"lower":0.07102,"upper":0.246039}},{"model":"gpt-3.5-turbo-instruct","modelPrettified":"GPT-3.5","date":"2022-03-15","p50":{"value":0.604245,"lower":0.227348,"upper":0.989884}},{"model":"GPT-4 0314","modelPrettified":"GPT-4","date":"2023-03-14","p50":{"value":3.987428,"lower":1.959555,"upper":7.906991}},{"model":"GPT-4 1106","modelPrettified":"GPT-4 Nov '23","date":"2023-11-06","p50":{"value":4.044959,"lower":1.952629,"upper":8.193214}},{"model":"GPT-4o","modelPrettified":"GPT-4o","date":"2024-05-13","p50":{"value":6.991195,"lower":3.851599,"upper":12.414331}},{"model":"Claude 3.5 Sonnet (Old)","modelPrettified":"Sonnet 3.5","date":"2024-06-20","p50":{"value":11.395377,"lower":5.441687,"upper":22.516722}},{"model":"o1-preview","modelPrettified":"o1 preview","date":"2024-09-12","p50":{"value":20.326586,"lower":11.61017,"upper":33.15407}},{"model":"Claude 3.5 Sonnet (New)","modelPrettified":"Sonnet 3.6","date":"2024-10-22","p50":{"value":20.522872,"lower":9.874824,"upper":40.412855}},{"model":"o1","modelPrettified":"o1","date":"2024-12-05","p50":{"value":38.831588,"lower":21.687821,"upper":67.221467}},{"model":"Claude 3.7 Sonnet","modelPrettified":"Sonnet 3.7","date":"2025-02-24","p50":{"value":60.388937,"lower":33.385879,"upper":107.302719}},{"model":"o3","modelPrettified":"o3","date":"2025-04-16","p50":{"value":119.732634,"lower":72.982684,"upper":191.583353}},{"model":"GPT-5","modelPrettified":"GPT-5","date":"2025-08-07","p50":{"value":203.012577,"lower":114.211156,"upper":406.743053}},{"model":"Gemini 3 Pro","modelPrettified":"Gemini 3 Pro","date":"2025-11-18","p50":{"value":224.325884,"lower":136.865815,"upper":387.478199}},{"model":"Claude Opus 4.5","modelPrettified":"Opus 4.5","date":"2025-11-24","p50":{"value":292.994594,"lower":160.539157,"upper":638.619623}},{"model":"GPT-5.2 (High)","modelPrettified":"GPT-5.2","date":"2025-12-11","p50":{"value":352.249302,"lower":191.31908,"upper":862.339204}},{"model":"Claude Opus 4.6","modelPrettified":"Opus 4.6","date":"2026-02-05","p50":{"value":718.80683,"lower":319.32091,"upper":3949.750392}}];
// Fit constants exactly as in AI Digest's chart component (TimeHorizonsViz.tsx).
var Z = { central: { doubling: 212.31449085490206, refDate: Date.UTC(2024, 0, 1), value: 10.298859349245546 },
          lower: { doubling: 249.12711294150483, ref: 6.216485336827207 },
          upper: { doubling: 170.12945330534745, ref: 15.98364743504459 },
          futureEnd: Date.UTC(2030, 0, 1) };
var G = { doubling: 117.59767166788184, refDate: Date.UTC(2024, 0, 1), value: 5.1422611933295475 };
var LABELLED = ["GPT-2","davinci-002 (GPT-3)","gpt-3.5-turbo-instruct","GPT-4 0314","GPT-4o","o1","Claude 3.7 Sonnet","o3","GPT-5","Gemini 3 Pro","Claude Opus 4.5","GPT-5.2 (High)","Claude Opus 4.6"];
var LABELLED_FAR = ["GPT-2","GPT-4 0314","Claude Opus 4.6"];
var DAY = 864e5;
var SVGNS = "http://www.w3.org/2000/svg";

function L(t) { return Z.central.value * Math.pow(2, (t - Z.central.refDate) / DAY / Z.central.doubling); }
function C(t, ref, dbl) { return ref * Math.pow(2, (t - Z.central.refDate) / DAY / dbl); }
function I(t) { return G.value * Math.pow(2, (t - G.refDate) / DAY / G.doubling); }
function fmt(e, axis) {
  if (e >= 60) {
    var n = e / 60, extra = "", a;
    if (axis) a = n.toLocaleString("en-US", { minimumFractionDigits: 0, maximumFractionDigits: n >= 10 ? 0 : 1 }) + " hour" + (n < 1.1 && n >= 1 ? "" : "s");
    else { var h = Math.floor(n), m = Math.round(e - 60 * h), r = h + " hour" + (h === 1 ? "" : "s"); a = m > 0 ? r + " " + m + " mins" : r; }
    if (n >= 8) {
      var k;
      if (n >= 166.51) { k = Math.round(n / 167); extra = k + " work month" + (k === 1 ? "" : "s"); }
      else if (n >= 40) { k = Math.round(n / 40); extra = k + " work week" + (k === 1 ? "" : "s"); }
      else { k = Math.round(n / 8); extra = k + " work day" + (k === 1 ? "" : "s"); }
      return [a, extra];
    }
    return [a];
  }
  if (e >= 1) return [Math.round(e) + " min" + (Math.round(e) === 1 ? "" : "s")];
  var s = Math.round(60 * e); return [s + " sec" + (s === 1 ? "" : "s")];
}
// d3's tick step rule
function tickStep(start, stop, count) {
  var step0 = Math.abs(stop - start) / count, p = Math.floor(Math.log10(step0)), err = step0 / Math.pow(10, p);
  var f = err >= Math.sqrt(50) ? 10 : err >= Math.sqrt(10) ? 5 : err >= Math.sqrt(2) ? 2 : 1;
  return f * Math.pow(10, p);
}
function yearOf(t) { var d = new Date(t); var y = d.getUTCFullYear(); return y + (t - Date.UTC(y, 0, 1)) / (Date.UTC(y + 1, 0, 1) - Date.UTC(y, 0, 1)); }
function el(tag, attrs, text) { var n = document.createElementNS(SVGNS, tag); for (var k in attrs) n.setAttribute(k, attrs[k]); if (text !== undefined) n.textContent = text; return n; }
function monthYear(t, short) { return new Date(t).toLocaleDateString("en-US", { month: short ? "short" : "long", year: "numeric", timeZone: "UTC" }); }

var P = STATE;
var showErrorBars = P.showErrorBars !== false, ext = !!P.showExtrapolation, dbl = !!P.showDoublingRate, t24 = !!P.show2024Trend;
var pts = DATA.map(function (d) { var p = d.date.split("-"); return { t: Date.UTC(+p[0], +p[1] - 1, +p[2]), p50: d.p50.value, lower: d.p50.lower, upper: d.p50.upper, model: d.model, pretty: d.modelPrettified }; });
var tMin = Math.min.apply(null, pts.map(function (d) { return d.t; }));
var O = Math.max.apply(null, pts.map(function (d) { return d.t; }));

var R = [];
(function () {
  var n = (O - tMin) / DAY;
  for (var i = 0; i <= 100; i++) { var s = tMin + n * i / 100 * DAY; R.push({ t: s, v: L(s), lo: C(s, Z.lower.ref, Z.lower.doubling), hi: C(s, Z.upper.ref, Z.upper.doubling) }); }
  var f = (Z.futureEnd - O) / DAY;
  for (var j = 1; j <= 100; j++) { var u = O + f * j / 100 * DAY, v = L(u); if (v <= 18000) R.push({ t: u, v: v, lo: C(u, Z.lower.ref, Z.lower.doubling), hi: C(u, Z.upper.ref, Z.upper.doubling) }); }
})();
var B = [];
if (t24) {
  var n2 = (O - G.refDate) / DAY;
  for (var i2 = 0; i2 <= 50; i2++) { var s2 = G.refDate + n2 * i2 / 50 * DAY; B.push({ t: s2, v: I(s2) }); }
  var f2 = (Z.futureEnd - O) / DAY;
  for (var j2 = 1; j2 <= 50; j2++) { var u2 = O + f2 * j2 / 50 * DAY, v2 = I(u2); if (v2 <= 18000) B.push({ t: u2, v: v2 }); }
}
var K = [];
if (dbl) { var tt = tMin, vv = L(tMin), end = ext ? Z.futureEnd : O; while (tt <= end) { K.push({ t: tt, v: vv }); tt += DAY * Z.central.doubling; vv *= 2; } }

var box = document.getElementById("chart");
var tip = document.getElementById("tip");
var yMax = (ext ? Math.max.apply(null, R.map(function (d) { return d.v; })) : Math.max.apply(null, pts.map(function (d) { return d.p50; }))) * 1.1;
var xD0 = tMin - 2592e6, xD1 = ext ? Z.futureEnd : O + 2592e6;

function render() {
  var width = Math.max(300, box.clientWidth);
  var mobile = width < 560;
  var height = Math.round(Math.min(460, Math.max(300, width * 0.62)));
  var M = { top: 30, right: 30, bottom: 30, left: 80 };
  var iw = width - M.left - M.right, ih = height - M.top - M.bottom;
  function X(t) { return (t - xD0) / (xD1 - xD0) * iw; }
  function Y(v) { return ih - v / yMax * ih; }
  function pathOf(arr, key) { return arr.map(function (d, i) { return (i ? "L" : "M") + X(d.t).toFixed(2) + " " + Y(d[key || "v"]).toFixed(2); }).join(" "); }
  function areaOf(arr) { return pathOf(arr, "hi") + " " + arr.slice().reverse().map(function (d) { return "L" + X(d.t).toFixed(2) + " " + Y(d.lo).toFixed(2); }).join(" ") + " Z"; }

  box.textContent = "";
  var svg = el("svg", { width: width, height: height, viewBox: "0 0 " + width + " " + height, role: "img", "aria-label": document.title });
  var defs = el("defs", {});
  var pat = el("pattern", { id: "hatch", width: 6, height: 6, patternUnits: "userSpaceOnUse", patternTransform: "rotate(45)" });
  pat.appendChild(el("line", { x1: 0, y1: 0, x2: 0, y2: 6, stroke: "rgba(184,112,24,0.14)", "stroke-width": 1 }));
  defs.appendChild(pat);
  var cp = el("clipPath", { id: "plotclip" }); cp.appendChild(el("rect", { x: 0, y: -M.top, width: iw + M.right, height: ih + M.top })); defs.appendChild(cp);
  svg.appendChild(defs);
  var g = el("g", { transform: "translate(" + M.left + "," + M.top + ")" });
  svg.appendChild(g);

  // grid
  var yStep = tickStep(0, yMax, 3), yTicks = [];
  for (var yv = 0; yv <= yMax; yv += yStep) yTicks.push(yv);
  var y0 = yearOf(xD0), y1 = yearOf(xD1), xStep = Math.max(1, tickStep(y0, y1, 5)), xTicks = [];
  for (var yr = Math.ceil(y0 / xStep) * xStep; yr <= y1; yr += xStep) xTicks.push(Date.UTC(yr, 0, 1));
  yTicks.forEach(function (v) { g.appendChild(el("line", { x1: 0, x2: iw, y1: Y(v), y2: Y(v), class: "grid" })); });
  xTicks.forEach(function (t) { g.appendChild(el("line", { x1: X(t), x2: X(t), y1: 0, y2: ih, class: "grid" })); });

  // axes
  g.appendChild(el("line", { x1: 0, x2: iw, y1: ih, y2: ih, class: "axis" }));
  g.appendChild(el("line", { x1: 0, x2: 0, y1: 0, y2: ih, class: "axis" }));
  xTicks.forEach(function (t) {
    g.appendChild(el("line", { x1: X(t), x2: X(t), y1: ih, y2: ih + 4, class: "axis" }));
    g.appendChild(el("text", { x: X(t), y: ih + 16, "text-anchor": "middle", class: "tick" }, String(new Date(t).getUTCFullYear())));
  });
  yTicks.forEach(function (v) {
    var lab = fmt(v, true);
    g.appendChild(el("line", { x1: -4, x2: 0, y1: Y(v), y2: Y(v), class: "axis" }));
    g.appendChild(el("text", { x: -8, y: Y(v) + 4, "text-anchor": "end", class: "tick" }, lab[0]));
    if (lab.length > 1) g.appendChild(el("text", { x: -5, y: Y(v) + 16, "text-anchor": "end", class: "tick-sub" }, lab[1]));
  });
  if (mobile && !ext) g.appendChild(el("text", { x: -70, y: ih / 2, transform: "rotate(-90," + (-70) + "," + (ih / 2) + ")", "text-anchor": "middle", class: "ytitle" }, "Task length"));
  if (!mobile) {
    var cap = el("g", { transform: "translate(40,60)" });
    cap.appendChild(el("path", { d: "M-3.75 6.75 0 3m0 0 3.75 3.75M0 3v18", fill: "none", stroke: "#9a5c10", "stroke-width": 1.5, "stroke-linecap": "round", "stroke-linejoin": "round" }));
    cap.appendChild(el("text", { x: 20, y: 15, class: "caption" }, "Length of coding tasks AIs can do increasing"));
    g.appendChild(cap);
  }

  var plot = el("g", { "clip-path": "url(#plotclip)" });
  g.appendChild(plot);
  var past = R.filter(function (d) { return d.t <= O; }), fut = R.filter(function (d) { return d.t >= O; });
  if (!t24) {
    plot.appendChild(el("path", { d: areaOf(past), fill: "rgba(184,112,24,0.10)" }));
    plot.appendChild(el("path", { d: areaOf(fut), fill: "rgba(184,112,24,0.05)" }));
    plot.appendChild(el("path", { d: areaOf(fut), fill: "url(#hatch)" }));
  }
  plot.appendChild(el("path", { d: pathOf(past), fill: "none", stroke: "#b87018", "stroke-width": 2 }));
  plot.appendChild(el("path", { d: pathOf(fut), fill: "none", stroke: "rgba(184,112,24,0.8)", "stroke-width": 2, "stroke-dasharray": "4,4" }));
  if (t24) {
    plot.appendChild(el("path", { d: pathOf(B.filter(function (d) { return d.t <= O; })), fill: "none", stroke: "#dc2626", "stroke-width": 2 }));
    plot.appendChild(el("path", { d: pathOf(B.filter(function (d) { return d.t >= O; })), fill: "none", stroke: "rgba(220,38,38,0.8)", "stroke-width": 2, "stroke-dasharray": "4,4" }));
  }
  var dblLabels = [];
  K.forEach(function (d, i) {
    var t2 = d.t + DAY * Z.central.doubling;
    plot.appendChild(el("path", { d: "M " + X(d.t) + " " + Y(d.v) + " L " + X(d.t) + " " + Y(2 * d.v) + " L " + X(t2) + " " + Y(2 * d.v), fill: "none", stroke: "#b87018", "stroke-width": 2, "stroke-dasharray": "2,1" }));
    if (i >= 8) dblLabels.push([
      el("text", { x: X(d.t) - 8, y: Y(d.v) + (Y(2 * d.v) - Y(d.v)) / 2 + 4, "text-anchor": "end", class: "dbl" }, "2x"),
      el("text", { x: X(d.t) + (X(t2) - X(d.t)) / 2 - (mobile ? -10 : 2), y: Y(2 * d.v) - 8, "text-anchor": mobile ? "end" : "middle", class: "dbl" }, "7 months")]);
  });

  var labelled = ext ? LABELLED_FAR : LABELLED;
  pts.forEach(function (d) {
    var cx = X(d.t), cy = Y(d.p50);
    if (showErrorBars) {
      plot.appendChild(el("line", { x1: cx, x2: cx, y1: Y(d.lower), y2: Y(d.upper), class: "err" }));
      plot.appendChild(el("line", { x1: cx - 4, x2: cx + 4, y1: Y(d.upper), y2: Y(d.upper), class: "err" }));
      plot.appendChild(el("line", { x1: cx - 4, x2: cx + 4, y1: Y(d.lower), y2: Y(d.lower), class: "err" }));
    }
    var c = el("circle", { cx: cx, cy: cy, r: 5, class: "pt", tabindex: 0, "aria-label": d.pretty + ", released " + monthYear(d.t) + ", 50% time horizon " + fmt(d.p50).join(", ") });
    c.addEventListener("mouseenter", function () { showPoint(d, cx + M.left, cy + M.top); });
    c.addEventListener("focus", function () { showPoint(d, cx + M.left, cy + M.top); });
    c.addEventListener("mouseleave", hideTip); c.addEventListener("blur", hideTip);
    plot.appendChild(c);
    var show = !dbl && labelled.indexOf(d.model) >= 0 && !(d.model === "GPT-2" && mobile);
    if (show) {
      var up = (ext && d.model !== "Claude Opus 4.6") || ["GPT-2", "davinci-002 (GPT-3)", "gpt-3.5-turbo-instruct", "GPT-4 0314"].indexOf(d.model) >= 0;
      plot.appendChild(el("text", { x: cx + (d.model === "GPT-2" ? 8 : -8), y: cy + (up ? -10 : 0) + 4, "text-anchor": d.model === "GPT-2" ? "start" : "end", class: "lbl" }, d.pretty));
    }
  });

  // crosshair reading the main trend
  var vx = el("line", { y1: 0, y2: ih, class: "xh", visibility: "hidden" }), hx = el("line", { x1: 0, x2: iw, class: "xh", visibility: "hidden" });
  g.appendChild(vx); g.appendChild(hx);
  svg.addEventListener("mousemove", function (ev) {
    if (tip.dataset.kind === "point") return;
    var r = svg.getBoundingClientRect(), px = ev.clientX - r.left - M.left;
    if (px < 0 || px > iw) { vx.setAttribute("visibility", "hidden"); hx.setAttribute("visibility", "hidden"); hideTip(); return; }
    var t = xD0 + px / iw * (xD1 - xD0), v = L(t), py = Y(v);
    vx.setAttribute("x1", px); vx.setAttribute("x2", px); vx.setAttribute("visibility", "visible");
    hx.setAttribute("y1", py); hx.setAttribute("y2", py); hx.setAttribute("visibility", py >= 0 ? "visible" : "hidden");
    var f = fmt(v);
    tip.dataset.kind = "trend";
    tip.innerHTML = "";
    addLine(tip, monthYear(t, true), "muted"); addLine(tip, f[0], "strong"); if (f[1]) addLine(tip, f[1], "muted");
    placeTip(px + M.left, Math.max(py + M.top, 0));
  });
  svg.addEventListener("mouseleave", function () { vx.setAttribute("visibility", "hidden"); hx.setAttribute("visibility", "hidden"); tip.dataset.kind = ""; hideTip(); });
  box.appendChild(svg);
  // Doubling labels: newest step first; a pair is kept only if neither label overlaps one already kept or leaves the chart.
  var kept = [];
  function hit(a, b) { return a.x < b.x + b.width + 2 && b.x < a.x + a.width + 2 && a.y < b.y + b.height && b.y < a.y + a.height; }
  for (var li = dblLabels.length - 1; li >= 0; li--) {
    var pair = dblLabels[li]; pair.forEach(function (n) { plot.appendChild(n); });
    // Estimated boxes (12px bold DM Sans), not getBBox: the frame may still be hidden when this runs.
    var boxes = pair.map(function (n) {
      var w = n.textContent.length * 7, x = +n.getAttribute("x"), y = +n.getAttribute("y"), a = n.getAttribute("text-anchor");
      return { x: a === "end" ? x - w : a === "middle" ? x - w / 2 : x, y: y - 11, width: w, height: 14 };
    });
    var bad = boxes.some(function (bb) { return bb.y < -M.top || bb.x + bb.width > iw + M.right || kept.some(function (k) { return hit(bb, k); }); });
    if (bad) pair.forEach(function (n) { plot.removeChild(n); }); else kept = kept.concat(boxes);
  }

  var legend = document.getElementById("legend");
  legend.textContent = "";
  legendItem(legend, "#b87018", false, "Trend over all models: doubling every 7 months");
  if (t24) legendItem(legend, "#dc2626", false, "Trend from 2024: doubling every 4 months");
  if (ext) legendItem(legend, "#5a5a5a", true, "Extrapolated");
}
function legendItem(parent, color, dashed, text) {
  var s = document.createElement("span"), sw = document.createElement("i");
  sw.style.borderTop = "2px " + (dashed ? "dashed " : "solid ") + color;
  s.appendChild(sw); s.appendChild(document.createTextNode(text)); parent.appendChild(s);
}
function addLine(parent, text, cls) { var d = document.createElement("div"); d.className = cls; d.textContent = text; parent.appendChild(d); }
function showPoint(d, x, y) {
  tip.dataset.kind = "point"; tip.innerHTML = "";
  addLine(tip, d.pretty, "strong");
  if (d.model !== d.pretty) addLine(tip, d.model, "muted");
  addLine(tip, "Released " + monthYear(d.t), "muted");
  var f = fmt(d.p50); addLine(tip, "50% time horizon: " + f[0], ""); if (f[1]) addLine(tip, f[1], "muted small");
  addLine(tip, "95% confidence interval: " + fmt(d.lower, true)[0] + " - " + fmt(d.upper, true)[0], "muted");
  placeTip(x, y);
}
function placeTip(x, y) {
  tip.style.display = "block";
  var w = tip.offsetWidth, bw = box.clientWidth;
  tip.style.left = Math.max(0, Math.min(x - 120, bw - w)) + "px";
  tip.style.top = Math.max(0, y - tip.offsetHeight - 12) + "px";
}
function hideTip() { if (tip.dataset.kind === "point") tip.dataset.kind = ""; tip.style.display = "none"; }

render();
var lastW = box.clientWidth;
window.addEventListener("resize", function () { if (box.clientWidth !== lastW) { lastW = box.clientWidth; render(); } });

</script>
</body>
</html>

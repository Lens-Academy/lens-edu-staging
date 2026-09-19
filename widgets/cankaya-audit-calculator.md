---
id: '3fc1d1d0-2294-4098-8f7c-bfa50a09c6d3'
title: Audit confidence calculator
summary_for_tutor: "An audit confidence calculator built from Appendix A1 of Cankaya's paper, which sits directly above it on the page with all three of its tables, the sampling formula and the zkLLM anchor. Four log sliders: checked samples per audit day, the true flaw rate, the number of prover GPUs, and the GPU-seconds one proof costs. The sample count and the GPU count are two views of one budget (n = GPUs x 86,400 / cost), so moving either moves the other, and raising the per-proof cost divides the proofs a fixed fleet can afford. The widget recomputes live the detection probability 1 - (1-p)^n, the 95 percent certified ceiling 1 - 0.05^(1/n), the share of the 200,000-GPU reference fleet spent, and how many requests are sampled, with the fleet request rate following the paper alpha = 0.5 scaling. A log chart plots the detection curve for the chosen flaw rate against the paper 1 percent and 0.1 percent columns, marks the current point and gives a hover readout. Every cell of the three appendix tables comes back at the inputs the paper states. Done when the learner has moved two different sliders. The widget carries one instruction line and no other prose; framing, tables and definitions stay in the article text around it."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Audit confidence calculator</title>
<!-- Built from articles/cankaya-a-system-overview-for-near-term-low-trust-ai-compute-verification.md, Appendix A1 (lines 602 to 648): the sampling formula P(detect >= 1) = 1 - (1-p)^n, the checked-samples table, the zkLLM 13B prover-budget table and the model-scaled-by-100 table. -->
<!-- Constants from the same appendix: 803 GPU-seconds per zkLLM LLaMA-2-13B proof (about 108 proofs per GPU per day), a 200,000-GPU reference fleet at about 1.7e10 requests per day, and the demonstrated cost exponent alpha = 0.5, under which a 100x larger model costs 10x per proof and the fleet emits about 100x fewer requests. Every number is recomputed from those constants; no table cell is hard coded. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #faf8f3; --card: #ffffff; --text: #1a1a1a; --muted: #5a5a5a;
    --border: #e8e5df; --accent: #b87018; --accent-soft: #f3e7d7;
    --font-ui: "DM Sans", Arial, sans-serif;
  }
  * { box-sizing: border-box; }
  [hidden] { display: none !important; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .lede { color: var(--muted); margin: 0 0 12px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; background: var(--card); margin-bottom: 12px; }
  .controls { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 14px 22px; }
  @media (max-width: 640px) { .controls { grid-template-columns: minmax(0, 1fr); } }
  .ctl .top { display: flex; justify-content: space-between; align-items: baseline; gap: 10px; }
  .ctl label { font-weight: 500; }
  .ctl .val { font-variant-numeric: tabular-nums; color: var(--accent); font-weight: 600; white-space: nowrap; }
  .ctl .sub { font-size: 12px; color: var(--muted); min-height: 18px; }
  input[type=range] { width: 100%; margin: 4px 0 0; accent-color: var(--accent); }
  input[type=range]:focus-visible { outline: 2px solid var(--accent); outline-offset: 3px; }
  .tiles { display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 10px; margin-bottom: 12px; }
  @media (max-width: 640px) { .tiles { grid-template-columns: minmax(0, 1fr); } }
  .tile { border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: var(--bg); }
  .tile .k { font-size: 12px; color: var(--muted); }
  .tile .v { font: 500 24px/1.2 "Newsreader", Georgia, serif; font-variant-numeric: tabular-nums; margin: 2px 0; }
  .tile .n { font-size: 12px; color: var(--muted); }
  .chartbox { overflow-x: auto; }
  .chart { width: 100%; min-width: 560px; height: auto; display: block; touch-action: pan-y; }
  .chart text { font-family: var(--font-ui); }
  .legend { display: flex; flex-wrap: wrap; gap: 14px; margin-top: 8px; font-size: 12px; color: var(--muted); }
  .legend span { display: inline-flex; align-items: center; gap: 7px; }
  .swatch { display: inline-block; width: 26px; height: 0; border-top: 3px solid var(--muted); }
  .swatch.live { border-top-color: var(--accent); }
  .swatch.dash { border-top-style: dashed; }
  .swatch.dot { border-top-style: dotted; }
  .status { font-size: 12px; color: var(--muted); margin: 10px 0 0; }
  .status.is-done { color: var(--text); font-weight: 500; }
</style>
</head>
<body>
<p class="lede">Move any slider. The sample count and the prover fleet are two views of one budget, joined by the cost of a proof.</p>

<div class="card">
  <div class="controls">
    <div class="ctl">
      <div class="top"><label for="s-n">Checked samples per audit day (n)</label><span class="val" id="v-n"></span></div>
      <input type="range" id="s-n" step="any">
      <div class="sub" id="d-n"></div>
    </div>
    <div class="ctl">
      <div class="top"><label for="s-p">True flaw rate (p)</label><span class="val" id="v-p"></span></div>
      <input type="range" id="s-p" step="any">
      <div class="sub" id="d-p"></div>
    </div>
    <div class="ctl">
      <div class="top"><label for="s-g">Prover GPUs</label><span class="val" id="v-g"></span></div>
      <input type="range" id="s-g" step="any">
      <div class="sub" id="d-g"></div>
    </div>
    <div class="ctl">
      <div class="top"><label for="s-c">GPU-seconds per proof</label><span class="val" id="v-c"></span></div>
      <input type="range" id="s-c" step="any">
      <div class="sub" id="d-c"></div>
    </div>
  </div>
</div>

<div class="card">
  <div class="tiles">
    <div class="tile"><div class="k">P(detect at least one flaw)</div><div class="v" id="t-det"></div><div class="n" id="t-det-n"></div></div>
    <div class="tile"><div class="k">A clean audit rules out a share above</div><div class="v" id="t-ceil"></div><div class="n">at 95 percent confidence</div></div>
    <div class="tile"><div class="k">Proof budget</div><div class="v" id="t-bud"></div><div class="n" id="t-bud-n"></div></div>
  </div>
  <div class="chartbox">
    <svg id="chart" class="chart" viewBox="0 0 760 430" role="img" aria-labelledby="chart-title"><title id="chart-title">Probability of catching at least one flaw against the number of checked samples</title></svg>
  </div>
  <div class="legend" id="legend"></div>
  <p class="status" id="status" aria-live="polite"></p>
</div>

<script>
(function () {
  var NS = "http://www.w3.org/2000/svg";
  var FLEET = 200000;            // reference fleet, GPUs
  var BASE_COST = 803;           // GPU-seconds per zkLLM LLaMA-2-13B proof
  var BASE_REQ = 1.7e10;         // fleet requests per day at 13B scale
  var SECS = 86400;
  var ALPHA = 0.5;               // demonstrated zkLLM cost exponent

  var N_MIN = 10, N_MAX = 1.2e6;
  var G_MIN = 0.05, G_MAX = 20000;
  var C_MIN = BASE_COST, C_MAX = BASE_COST * 10;
  var P_MIN = 1e-5, P_MAX = 0.1;

  var state = { gpus: 100, cost: BASE_COST, p: 0.01, moved: {} };
  var completed = false;

  function clamp(v, lo, hi) { return v < lo ? lo : (v > hi ? hi : v); }
  function nOf() { return clamp(state.gpus * SECS / state.cost, N_MIN, N_MAX); }
  function scaleOf() { return Math.pow(state.cost / BASE_COST, 1 / ALPHA); }
  function reqPerDay() { return BASE_REQ / scaleOf(); }
  function detect(p, n) { return 1 - Math.pow(1 - p, n); }
  function ceiling95(n) { return n > 0 ? 1 - Math.pow(0.05, 1 / n) : 1; }

  var NICE = [1, 1.5, 2, 2.5, 3, 4, 5, 6, 7, 8, 9];
  function snapNice(v, extras) {
    var e = Math.floor(Math.log10(v)), k, i, c;
    if (extras) for (i = 0; i < extras.length; i++) {
      if (Math.abs(Math.log10(extras[i] / v)) < 0.008) return extras[i];
    }
    for (k = e - 1; k <= e + 1; k++) {
      for (i = 0; i < NICE.length; i++) {
        c = NICE[i] * Math.pow(10, k);
        if (Math.abs(Math.log10(c / v)) < 0.0043) return c;
      }
    }
    return v;
  }
  function gpuWord(g) { return Math.abs(g - 1) < 1e-9 ? " GPU" : " GPUs"; }

  function sup(nmb) {
    var map = { "0": "⁰", "1": "¹", "2": "²", "3": "³", "4": "⁴", "5": "⁵", "6": "⁶", "7": "⁷", "8": "⁸", "9": "⁹" };
    return String(nmb).split("").map(function (ch) { return map[ch] || ch; }).join("");
  }
  function grp(x) { return Math.round(x).toLocaleString("en-US"); }
  function sig(x, d) { return Number(x.toPrecision(d)); }
  function fmtCount(x) {
    if (x < 10) return String(sig(x, 3));
    return grp(sig(x, 3));
  }
  function fmtDetect(v) {
    var x = v * 100;
    if (x >= 99.9995) return "~100%";
    var dec = x >= 99.99 ? 3 : 2;
    return String(Number(x.toFixed(dec))) + "%";
  }
  function fmtP(v) {
    var x = v * 100;
    return String(Number(x.toPrecision(3))) + "%";
  }
  function fmtSmallPct(v) {
    var x = v * 100;
    if (x >= 10) return String(Number(x.toFixed(1))) + "%";
    return x.toPrecision(3) + "%";
  }
  function fmtShare(g) {
    var x = g / FLEET * 100;
    if (x >= 1) return String(Number(x.toFixed(2))) + "%";
    return Number(x.toPrecision(2)) + "%";
  }
  function fmtRatio(r) {
    var m2 = sig(r, 2);
    if (m2 < 10000) return grp(m2);
    var e = Math.floor(Math.log10(r));
    var m = sig(r / Math.pow(10, e), 2);
    if (m >= 10) { m = m / 10; e += 1; }
    return m + " × 10" + sup(e);
  }

  // Controls
  var CTL = {
    n: { el: document.getElementById("s-n"), lo: Math.log10(N_MIN), hi: Math.log10(N_MAX) },
    p: { el: document.getElementById("s-p"), lo: Math.log10(P_MIN), hi: Math.log10(P_MAX) },
    g: { el: document.getElementById("s-g"), lo: Math.log10(G_MIN), hi: Math.log10(G_MAX) },
    c: { el: document.getElementById("s-c"), lo: Math.log10(C_MIN), hi: Math.log10(C_MAX) }
  };
  Object.keys(CTL).forEach(function (k) {
    var c = CTL[k];
    c.el.min = String(c.lo);
    c.el.max = String(c.hi);
  });

  function setSlider(k, value) { CTL[k].el.value = String(clamp(Math.log10(value), CTL[k].lo, CTL[k].hi)); }

  function onSlide(key) {
    var raw = Math.pow(10, parseFloat(CTL[key].el.value));
    if (key === "p") {
      state.p = clamp(snapNice(raw), P_MIN, P_MAX);
    } else if (key === "c") {
      state.cost = clamp(snapNice(raw, [BASE_COST, C_MAX]), C_MIN, C_MAX);
    } else if (key === "g") {
      state.gpus = clamp(snapNice(raw), G_MIN, G_MAX);
      var nn = state.gpus * SECS / state.cost;
      if (nn > N_MAX) state.gpus = N_MAX * state.cost / SECS;
      if (nn < N_MIN) state.gpus = N_MIN * state.cost / SECS;
    } else {
      var n = clamp(snapNice(raw), N_MIN, N_MAX);
      state.gpus = clamp(n * state.cost / SECS, G_MIN, G_MAX);
    }
    state.moved[key] = true;
    render();
    persist();
  }
  Object.keys(CTL).forEach(function (k) {
    CTL[k].el.addEventListener("input", function () { onSlide(k); });
  });

  // Chart geometry
  var svg = document.getElementById("chart");
  var PL = 58, PR = 636, PT = 22, PB = 372;
  function xOf(n) { return PL + (Math.log10(n) - Math.log10(N_MIN)) / (Math.log10(N_MAX) - Math.log10(N_MIN)) * (PR - PL); }
  function nAt(x) { return Math.pow(10, Math.log10(N_MIN) + (x - PL) / (PR - PL) * (Math.log10(N_MAX) - Math.log10(N_MIN))); }
  function yOf(v) { return PB - v * (PB - PT); }

  function el(name, attrs, text) {
    var e = document.createElementNS(NS, name);
    if (attrs) for (var k in attrs) e.setAttribute(k, String(attrs[k]));
    if (text !== undefined && text !== null) e.appendChild(document.createTextNode(text));
    return e;
  }
  function curvePoints(p) {
    var pts = [], i, steps = 200, l0 = Math.log10(N_MIN), l1 = Math.log10(N_MAX);
    for (i = 0; i <= steps; i++) {
      var n = Math.pow(10, l0 + (l1 - l0) * i / steps);
      pts.push(xOf(n).toFixed(1) + "," + yOf(detect(p, n)).toFixed(1));
    }
    return pts.join(" ");
  }
  function labelPoint(p) {
    // n where the curve reaches 0.55, clamped into the plot
    var n = Math.log(1 - 0.55) / Math.log(1 - p);
    n = clamp(n, N_MIN * 1.6, N_MAX * 0.4);
    return { x: xOf(n), y: yOf(detect(p, n)) };
  }

  var hoverG = null, hoverN = null;

  function drawChart() {
    while (svg.childNodes.length > 1) svg.removeChild(svg.lastChild);
    var g = el("g"), i;

    // y grid
    [0, 0.25, 0.5, 0.75, 1].forEach(function (v) {
      g.appendChild(el("line", { x1: PL, y1: yOf(v), x2: PR, y2: yOf(v), stroke: "#e8e5df", "stroke-width": 1 }));
      g.appendChild(el("text", { x: PL - 8, y: yOf(v) + 4, "text-anchor": "end", "font-size": 12, fill: "#5a5a5a" }, Math.round(v * 100) + "%"));
    });
    g.appendChild(el("line", { x1: PL, y1: yOf(0.95), x2: PR, y2: yOf(0.95), stroke: "#5a5a5a", "stroke-width": 1, "stroke-dasharray": "3 4" }));
    g.appendChild(el("text", { x: PR + 6, y: yOf(0.95) + 4, "font-size": 11, fill: "#5a5a5a" }, "95%"));

    // x ticks
    [10, 100, 1000, 10000, 100000, 1000000].forEach(function (n) {
      var lbl = n >= 1e6 ? "1M" : (n >= 1000 ? (n / 1000) + "k" : String(n));
      g.appendChild(el("line", { x1: xOf(n), y1: PT, x2: xOf(n), y2: PB, stroke: "#f2efe9", "stroke-width": 1 }));
      g.appendChild(el("line", { x1: xOf(n), y1: PB, x2: xOf(n), y2: PB + 5, stroke: "#5a5a5a", "stroke-width": 1 }));
      g.appendChild(el("text", { x: xOf(n), y: PB + 20, "text-anchor": "middle", "font-size": 12, fill: "#5a5a5a" }, lbl));
    });
    g.appendChild(el("line", { x1: PL, y1: PB, x2: PR, y2: PB, stroke: "#5a5a5a", "stroke-width": 1 }));
    g.appendChild(el("text", { x: (PL + PR) / 2, y: PB + 44, "text-anchor": "middle", "font-size": 12, fill: "#5a5a5a" }, "Checked samples n (log scale)"));
    g.appendChild(el("text", { x: 14, y: (PT + PB) / 2, "text-anchor": "middle", "font-size": 12, fill: "#5a5a5a", transform: "rotate(-90 14 " + ((PT + PB) / 2) + ")" }, "P(detect at least one flaw)"));

    // reference curves from the paper's two columns
    var refs = [{ p: 0.01, dash: "9 6", label: "p = 1%" }, { p: 0.001, dash: "2 4", label: "p = 0.1%" }];
    var liveIsRef = null;
    refs.forEach(function (r) {
      if (Math.abs(Math.log10(state.p / r.p)) < 0.01) { liveIsRef = r.label; return; }
      g.appendChild(el("polyline", { points: curvePoints(r.p), fill: "none", stroke: "#8d8880", "stroke-width": 2, "stroke-dasharray": r.dash }));
      var lp = labelPoint(r.p);
      g.appendChild(el("text", { x: lp.x + 8, y: lp.y - 8, "font-size": 12, fill: "#5a5a5a", stroke: "#ffffff", "stroke-width": 3, "paint-order": "stroke" }, r.label));
    });

    // live curve
    g.appendChild(el("polyline", { points: curvePoints(state.p), fill: "none", stroke: "#b87018", "stroke-width": 2.5 }));
    var llp = labelPoint(state.p);
    g.appendChild(el("text", { x: llp.x + 8, y: llp.y - 34, "font-size": 12, "font-weight": 600, fill: "#b87018", stroke: "#ffffff", "stroke-width": 3, "paint-order": "stroke" }, "p = " + fmtP(state.p) + (liveIsRef ? " (selected)" : "")));

    // current point
    var n = nOf(), px = xOf(n), py = yOf(detect(state.p, n));
    g.appendChild(el("line", { x1: px, y1: PB, x2: px, y2: py, stroke: "#b87018", "stroke-width": 1, "stroke-dasharray": "2 3" }));
    g.appendChild(el("circle", { cx: px, cy: py, r: 7, fill: "#b87018", stroke: "#ffffff", "stroke-width": 2 }));
    g.appendChild(el("text", { x: clamp(px, PL, PR - 90) + 12, y: clamp(py - 14, PT + 12, PB), "font-size": 13, "font-weight": 600, fill: "#1a1a1a", stroke: "#ffffff", "stroke-width": 3.5, "paint-order": "stroke" }, fmtDetect(detect(state.p, n)) + " at n = " + fmtCount(n)));

    svg.appendChild(g);
    hoverG = el("g");
    svg.appendChild(hoverG);
    if (hoverN !== null) drawHover();
  }

  function drawHover() {
    while (hoverG.firstChild) hoverG.removeChild(hoverG.firstChild);
    if (hoverN === null) return;
    var x = xOf(hoverN);
    hoverG.appendChild(el("line", { x1: x, y1: PT, x2: x, y2: PB, stroke: "#1a1a1a", "stroke-width": 1, opacity: 0.35 }));
    var rows = [
      "n = " + fmtCount(hoverN),
      "p = " + fmtP(state.p) + ": " + fmtDetect(detect(state.p, hoverN)),
      "ceiling: " + fmtSmallPct(ceiling95(hoverN))
    ];
    var w = 168, h = 14 + rows.length * 17;
    var bx = x + 12 > PR - w ? x - w - 12 : x + 12;
    hoverG.appendChild(el("rect", { x: bx, y: PT + 6, width: w, height: h, rx: 6, fill: "#ffffff", stroke: "#e8e5df" }));
    rows.forEach(function (t, i) {
      hoverG.appendChild(el("text", { x: bx + 10, y: PT + 26 + i * 17, "font-size": 12, fill: "#1a1a1a" }, t));
    });
    hoverG.appendChild(el("circle", { cx: x, cy: yOf(detect(state.p, hoverN)), r: 5, fill: "#ffffff", stroke: "#b87018", "stroke-width": 2 }));
  }

  svg.addEventListener("pointermove", function (evt) {
    var rect = svg.getBoundingClientRect();
    if (!rect.width) return;
    var x = (evt.clientX - rect.left) / rect.width * 760;
    if (x < PL || x > PR) { if (hoverN !== null) { hoverN = null; drawHover(); } return; }
    hoverN = nAt(x);
    drawHover();
  });
  svg.addEventListener("pointerleave", function () { hoverN = null; drawHover(); });

  // Legend
  var legend = document.getElementById("legend");
  function buildLegend() {
    while (legend.firstChild) legend.removeChild(legend.firstChild);
    [
      { cls: "live", text: "selected flaw rate" },
      { cls: "dash", text: "p = 1% (paper column 3)" },
      { cls: "dot", text: "p = 0.1% (paper column 4)" }
    ].forEach(function (item) {
      var s = document.createElement("span");
      var sw = document.createElement("span");
      sw.className = "swatch " + item.cls;
      s.appendChild(sw);
      s.appendChild(document.createTextNode(item.text));
      legend.appendChild(s);
    });
  }

  var out = {
    vn: document.getElementById("v-n"), dn: document.getElementById("d-n"),
    vp: document.getElementById("v-p"), dp: document.getElementById("d-p"),
    vg: document.getElementById("v-g"), dg: document.getElementById("d-g"),
    vc: document.getElementById("v-c"), dc: document.getElementById("d-c"),
    det: document.getElementById("t-det"), detn: document.getElementById("t-det-n"),
    ceil: document.getElementById("t-ceil"),
    bud: document.getElementById("t-bud"), budn: document.getElementById("t-bud-n"),
    status: document.getElementById("status")
  };

  function movedCount() { return Object.keys(state.moved).length; }

  function render() {
    var n = nOf(), scale = scaleOf(), req = reqPerDay();
    setSlider("n", n); setSlider("p", state.p); setSlider("g", state.gpus); setSlider("c", state.cost);

    out.vn.textContent = fmtCount(n);
    out.dn.textContent = "proofs re-run per day";
    CTL.n.el.setAttribute("aria-valuetext", fmtCount(n) + " checked samples per day");

    out.vp.textContent = fmtP(state.p);
    out.dp.textContent = "share of work that is actually non-compliant";
    CTL.p.el.setAttribute("aria-valuetext", "flaw rate " + fmtP(state.p));

    out.vg.textContent = fmtCount(state.gpus) + gpuWord(state.gpus);
    out.dg.textContent = fmtShare(state.gpus) + " of the 200,000-GPU fleet";
    CTL.g.el.setAttribute("aria-valuetext", fmtCount(state.gpus) + " prover" + gpuWord(state.gpus) + ", " + fmtShare(state.gpus) + " of the fleet");

    out.vc.textContent = grp(state.cost) + " GPU-s";
    out.dc.textContent = scale < 1.02
      ? "zkLLM measured, LLaMA-2-13B class"
      : "model ×" + fmtCount(scale) + " at alpha = 0.5, fleet at " + fmtRatio(req) + " requests per day";
    CTL.c.el.setAttribute("aria-valuetext", grp(state.cost) + " GPU-seconds per proof");

    out.det.textContent = fmtDetect(detect(state.p, n));
    out.detn.textContent = "if " + fmtP(state.p) + " of the work is flawed";
    out.ceil.textContent = fmtSmallPct(ceiling95(n));
    out.bud.textContent = fmtCount(state.gpus) + gpuWord(state.gpus);
    out.budn.textContent = fmtShare(state.gpus) + " of the fleet, 1 in " + fmtRatio(req / n) + " requests sampled";

    drawChart();

    var done = movedCount() >= 2;
    out.status.textContent = done
      ? "The ceiling depends on n alone, so a 100x bigger model buys the same certainty at 10x the GPUs."
      : "Sliders moved: " + movedCount() + " of 2.";
    out.status.classList.toggle("is-done", done);
  }

  function summary() {
    var n = nOf();
    return "Audit confidence calculator. " + fmtCount(n) + " checked samples per day, true flaw rate " + fmtP(state.p)
      + ", " + fmtCount(state.gpus) + " prover" + gpuWord(state.gpus) + " (" + fmtShare(state.gpus) + " of the 200,000-GPU fleet) at " + grp(state.cost)
      + " GPU-seconds per proof. P(detect at least one flaw) = " + fmtDetect(detect(state.p, n))
      + "; a clean audit rules out a non-compliant share above " + fmtSmallPct(ceiling95(n)) + " at 95 percent confidence; "
      + "1 in " + fmtRatio(reqPerDay() / n) + " requests sampled. Sliders moved: " + movedCount() + " of 2 needed.";
  }

  var saveTimer = null;
  function doSave() {
    var json = { gpus: state.gpus, cost: state.cost, p: state.p, moved: Object.keys(state.moved) };
    if (window.Lens) {
      Lens.saveState(json, summary());
      if (movedCount() >= 2 && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("cankaya-audit-calculator", JSON.stringify(json)); } catch (e) {}
    }
  }
  function persist() { clearTimeout(saveTimer); saveTimer = setTimeout(doSave, 350); }
  document.addEventListener("visibilitychange", function () {
    if (document.visibilityState === "hidden") { clearTimeout(saveTimer); doSave(); }
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.cost === "number" && isFinite(saved.cost)) state.cost = clamp(saved.cost, C_MIN, C_MAX);
      if (typeof saved.gpus === "number" && isFinite(saved.gpus)) state.gpus = clamp(saved.gpus, G_MIN, G_MAX);
      if (typeof saved.p === "number" && isFinite(saved.p)) state.p = clamp(saved.p, P_MIN, P_MAX);
      if (typeof saved.samples === "number" && isFinite(saved.samples)) {
        state.gpus = clamp(clamp(saved.samples, N_MIN, N_MAX) * state.cost / SECS, G_MIN, G_MAX);
      }
      state.moved = {};
      if (Array.isArray(saved.moved)) saved.moved.forEach(function (k) { if (CTL[k]) state.moved[k] = true; });
    }
    completed = !!(meta && meta.completed);
    render();
  }

  buildLegend();
  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    try { var raw = localStorage.getItem("cankaya-audit-calculator"); if (raw) hydrate(JSON.parse(raw), null); } catch (e) {}
  }
})();
</script>
</body>
</html>

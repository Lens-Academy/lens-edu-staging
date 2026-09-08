---
id: '4a01e137-f014-4994-a261-ea529678050b'
title: A Short History of AI Acceleration
summary_for_tutor: "Two redrawn Our World in Data charts. First, a timeline of notable AI systems from 1940 to 2060 (1945 first digital computers, 1950 Theseus, 1957 Perceptron Mark I, 1992 TD-Gammon, 2012 AlexNet, 2024 AI with language and image recognition comparable to humans); the learner zooms in to read the annotations and pans along the axis. Second, a line chart of AI test scores relative to human performance, 1998 to 2023, six capabilities (handwriting recognition, speech recognition, image recognition, reading comprehension, language understanding, predictive reasoning), each starting at minus 100 and crossing the human baseline at zero between 2015 and 2023; the learner hovers or steps through years to read the values, toggles series on and off, and can open a data table. The point to draw out is how fast the lines cross zero once they start climbing. The widget is complete once the learner has zoomed the timeline and inspected or toggled something on the chart. Content ported from XLab's Verification track; data from Our World in Data (Roser 2022; Kiela et al. 2023)."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>A Short History of AI Acceleration</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "short-history". Charts redrawn from Our World in Data (CC BY 4.0). -->
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
  h1 { font-size: 24px; line-height: 1.2; }
  h2 { font-size: 18px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  figure { margin: 0; }
  figure + figure { margin-top: 32px; }
  figcaption { margin-bottom: 8px; }
  .desc { color: var(--muted); margin: 4px 0 8px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px; position: relative; }
  .plot { overflow-x: auto; }
  svg { display: block; width: 100%; height: auto; font-family: var(--font-ui); font-size: 12px; }
  @media (max-width: 640px) {
    /* On a phone the plot scrolls sideways inside its own box instead of shrinking the labels below legibility.
       The timeline is deliberately not given a min-width: it has its own zoom, and a scroll box on top of that
       zoom cut the annotation blocks mid-word. It fits the box at every zoom level, so "Whole timeline" really
       does show 1940 to 2060 and a zoomed annotation is never sliced by the edge of the box. */
    #ts { min-width: 620px; }
    .tooltip { left: 8px !important; right: 8px; transform: none !important; }
  }
  svg:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; border-radius: 4px; }
  .grab { cursor: grab; touch-action: none; }
  .grab:active { cursor: grabbing; }
  .controls { display: flex; flex-wrap: wrap; align-items: center; gap: 8px; margin-top: 8px; }
  .group { display: flex; gap: 4px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.4; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.link { border: 0; padding: 4px 6px; color: var(--muted); text-decoration: underline; text-underline-offset: 3px; }
  button.link:hover { color: var(--text); background: transparent; }
  .readout { margin-left: auto; font-size: 12px; color: var(--muted); }
  .legend { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; }
  .legend button { display: inline-flex; align-items: center; gap: 8px; padding: 5px 10px; font-size: 12px; }
  .legend button[aria-pressed="false"] { color: var(--muted); text-decoration: line-through; }
  .legend svg { width: 26px; height: 10px; flex: 0 0 auto; }
  .legend .state { font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
  .tooltip {
    position: absolute; top: 10%; z-index: 2; pointer-events: none; display: none;
    border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 10px; font-size: 12px;
    box-shadow: 0 1px 2px rgba(0,0,0,0.08);
  }
  .tooltip.is-visible { display: block; }
  .tooltip .yr { font-weight: 600; font-size: 13px; margin-bottom: 4px; }
  .tooltip table { border-collapse: collapse; }
  .tooltip td { padding: 1px 4px; white-space: nowrap; }
  .tooltip td.v { text-align: right; font-variant-numeric: tabular-nums; font-weight: 500; }
  .tooltip tr.approx { color: var(--muted); }
  .sw { display: inline-block; width: 10px; height: 10px; border-radius: 3px; vertical-align: middle; }
  .table-wrap { overflow-x: auto; margin-top: 8px; display: none; }
  .table-wrap.is-visible { display: block; }
  table.data { border-collapse: collapse; font-size: 12px; min-width: 560px; }
  table.data th, table.data td { border: 1px solid var(--border); padding: 4px 8px; text-align: right; font-variant-numeric: tabular-nums; }
  table.data th { background: var(--surface); font-weight: 600; }
  table.data td:first-child, table.data th:first-child { text-align: left; }
  .credit { color: var(--muted); font-size: 12px; margin: 6px 0 0; }
  .credit a { color: var(--accent-hover); }
  .status { margin-top: 12px; font-size: 12px; color: var(--muted); }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
</style>
</head>
<body>
<p class="eyebrow">Optional</p>
<h1>A Short History of AI Acceleration</h1>
<p class="desc">How fast is fast? Two charts from Our World in Data's brief history of artificial intelligence show the pace.</p>

<figure>
  <figcaption><h2>A timeline of notable artificial intelligence systems</h2></figcaption>
  <div class="card">
    <div class="plot" id="tl-plot">
      <svg id="tl" viewBox="0 0 900 330" role="group" tabindex="0" aria-label="A timeline of notable artificial intelligence systems, 1940 to 2060. Draggable when zoomed; arrow keys pan, plus and minus zoom, Home resets. The back and next buttons frame one annotation at a time."></svg>
    </div>
    <div class="controls" id="tl-controls"></div>
  </div>
  <p class="credit" id="credit-1"></p>
</figure>

<figure>
  <figcaption><h2>Test scores of AI systems on various capabilities relative to human performance</h2></figcaption>
  <p class="desc">Within each domain, the initial performance of the AI is set to −100. Human performance is used as a baseline, set to zero. When the AI’s performance crosses the zero line, it scored more points than humans.</p>
  <div class="card">
    <div class="plot">
      <svg id="ts" viewBox="0 0 900 430" role="img" tabindex="0" aria-label="Test scores of AI systems on various capabilities relative to human performance, 1998 to 2023. Move the pointer over the chart or use the arrow keys to read values by year."></svg>
    </div>
    <div class="tooltip" id="tip" aria-hidden="true"></div>
    <div class="legend" id="legend" aria-label="Series shown"></div>
    <div class="controls" id="ts-controls"></div>
    <div class="table-wrap" id="table-wrap"></div>
  </div>
  <p class="credit" id="credit-2"></p>
</figure>

<p class="status" id="status"></p>

<script>
  var OWID_URL = "https://ourworldindata.org/brief-history-of-ai";
  var CREDIT = "Roser, Max. “The Brief History of Artificial Intelligence: The World Has Changed Fast, What Might Be Next?” Our World in Data, 6 Dec. 2022, ";
  var CREDIT_TAIL = ". Licensed CC BY 4.0; chart redrawn.";
  var CREDIT_DATA = " Underlying data from Kiela et al., 2023.";

  // Timeline: same coordinate system as the source figure.
  var TL = { w: 900, h: 330, axisY: 272, x0: 43, x1: 837, yr0: 1940, yr1: 2060 };
  var TL_BOUNDARY = 2024;
  var MILESTONES = [
    { year: 1945, name: "First digital computers", lines: [], x: 14, y: 216 },
    { year: 1950, name: "Theseus:", lines: ["A small robotic mouse that could", "navigate a simple maze and", "remember its course."], x: 100, y: 56 },
    { year: 1957, name: "Perceptron Mark I:", lines: ["Regarded as the first artificial neural", "network, it could visually distinguish cards", "marked on the left side from those marked", "on the right."], x: 158, y: 128 },
    { year: 1992, name: "TD-Gammon:", lines: ["This software learned to play", "backgammon at a high level, just", "below the top human players."], x: 330, y: 46 },
    { year: 2012, name: "AlexNet:", lines: ["This was a pivotal early “deep learning”", "system, a neural network with many", "layers, that could recognize images of", "objects such as dogs and cars at", "near-human level."], x: 580, y: 78 },
    { year: TL_BOUNDARY, name: "Artificial intelligence with language and", lines: ["image recognition capabilities that are", "comparable to those of humans"], x: 640, y: 196 }
  ];
  var TL_ZOOMS = [1, 1.6, 2.4, 3.4];

  // Test scores: six series, values relative to human performance (0).
  var SERIES = [
    { name: "Reading comprehension", color: "#2a78d6", dash: "", points: [[2016, -100], [2017, -8.9], [2018, 6.6], [2019, 18.1], [2020, 18.8]] },
    { name: "Image recognition", color: "#eb6834", dash: "7 4", points: [[2009, -100], [2012, -44.2], [2014, -6.8], [2015, 0.7], [2016, 6.6], [2018, 11.7], [2019, 9.5], [2020, 16.4]] },
    { name: "Language understanding", color: "#1baf7a", dash: "2 3", points: [[2018, -100], [2019, 3.7], [2020, 12.0], [2022, 15.7]] },
    { name: "Handwriting recognition", color: "#eda100", dash: "9 3 2 3", points: [[1998, -100], [2002, -48.0], [2003, -26.7], [2006, -25.3], [2010, -20.0], [2012, -4.0], [2013, -1.3], [2018, 2.7]] },
    { name: "Speech recognition", color: "#e87ba4", dash: "4 3", points: [[1998, -100], [2011, -65.6], [2013, -52.7], [2014, -27.8], [2015, -8.7], [2016, -1.2], [2017, 0.4], [2018, 1.6]] },
    { name: "Predictive reasoning", color: "#008300", dash: "12 4", points: [[2019, -100], [2021, -80.5], [2022, -30.6], [2023, -0.6]] }
  ];
  var TS = { w: 900, h: 430, plotX0: 64, plotX1: 655, plotY0: 30, plotY1: 372, yr0: 1998, yr1: 2023, v0: 25, v1: -100 };
  var GRID_VALUES = [20, 0, -20, -40, -60, -80, -100];
  var X_TICKS = [1998, 2005, 2010, 2015, 2020, 2023];

  var STORAGE_KEY = "lens-widget-short-history";
  var SVG_NS = "http://www.w3.org/2000/svg";
  var state = { zi: 0, pan: { x: 0, y: 0 }, hidden: [], year: null, table: false, explored: { timeline: false, scores: false } };
  var completed = false;
  var hoverYear = null;

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function sv(tag, attrs, parent) {
    var n = document.createElementNS(SVG_NS, tag);
    for (var k in attrs) n.setAttribute(k, attrs[k]);
    if (parent) parent.appendChild(n);
    return n;
  }
  function clear(node) { node.textContent = ""; }
  function btn(label, onClick, opts) {
    var b = el("button", opts && opts.className, label); b.type = "button";
    if (opts && opts.aria) b.setAttribute("aria-label", opts.aria);
    if (opts && opts.disabled) b.disabled = true;
    b.addEventListener("click", onClick);
    return b;
  }
  function credit(node, data) {
    node.textContent = CREDIT;
    var a = el("a", null, "ourworldindata.org/brief-history-of-ai");
    a.href = OWID_URL; a.target = "_blank"; a.rel = "noopener";
    node.appendChild(a);
    node.appendChild(document.createTextNode(CREDIT_TAIL + (data || "")));
  }
  credit(document.getElementById("credit-1"));
  credit(document.getElementById("credit-2"), CREDIT_DATA);

  /* ---------- Timeline ---------- */
  var tl = document.getElementById("tl");
  var tlControls = document.getElementById("tl-controls");
  var tlGroups = [], tlBoxes = [], focusBox = null;
  function tlx(year) { return TL.x0 + ((year - TL.yr0) / (TL.yr1 - TL.yr0)) * (TL.x1 - TL.x0); }
  function zoom() { return TL_ZOOMS[state.zi]; }
  function viewW() { return TL.w / zoom(); }
  function viewH() { return TL.h / zoom(); }
  function clampPan(p) {
    return { x: Math.min(Math.max(p.x, 0), TL.w - viewW()), y: Math.min(Math.max(p.y, 0), TL.h - viewH()) };
  }
  function movePan(dx, dy) { state.pan = clampPan({ x: state.pan.x + dx, y: state.pan.y + dy }); }
  function zoomTo(next) {
    var cx = state.pan.x + viewW() / 2, cy = state.pan.y + viewH() / 2;
    state.zi = next;
    state.pan = clampPan({ x: cx - viewW() / 2, y: cy - viewH() / 2 });
    if (state.zi > 0) {
      state.explored.timeline = true;
      var b = nearestBox();
      if (b) frameBox(b);
    }
  }
  var tlPlot = document.getElementById("tl-plot");
  function resetTimeline() {
    state.zi = 0;
    state.pan = { x: 0, y: 0 };
    focusBox = null;
    if (tlPlot) tlPlot.scrollLeft = 0;
  }

  function buildTimeline() {
    clear(tl);
    var title = sv("title", {}, tl); title.textContent = "A timeline of notable artificial intelligence systems, 1940 to 2060";
    sv("line", { x1: TL.x0, y1: TL.axisY, x2: tlx(TL_BOUNDARY), y2: TL.axisY, stroke: "#b87018", "stroke-width": 4 }, tl);
    sv("line", { x1: tlx(TL_BOUNDARY), y1: TL.axisY, x2: TL.x1, y2: TL.axisY, stroke: "#b87018", "stroke-opacity": 0.4, "stroke-width": 4 }, tl);
    sv("circle", { cx: tlx(TL_BOUNDARY), cy: TL.axisY, r: 5.5, fill: "#b87018" }, tl);
    for (var y = TL.yr0; y <= TL.yr1; y += 10) {
      sv("line", { x1: tlx(y), y1: TL.axisY + 6, x2: tlx(y), y2: TL.axisY + 11, stroke: "#5a5a5a" }, tl);
      var t = sv("text", { x: tlx(y), y: TL.axisY + 28, "text-anchor": "middle", fill: "#5a5a5a" }, tl);
      t.textContent = String(y);
    }
    tlGroups = [];
    MILESTONES.forEach(function (m) {
      var lineH = 16;
      var blockBottom = m.y + (m.lines.length + 1) * lineH;
      var g = sv("g", {}, tl);
      sv("line", { x1: tlx(m.year), y1: Math.min(blockBottom, TL.axisY - 10), x2: tlx(m.year), y2: TL.axisY - 5, stroke: "#5a5a5a", "stroke-width": 1 }, g);
      sv("path", { d: "M " + (tlx(m.year) - 3.5) + " " + (TL.axisY - 10) + " L " + tlx(m.year) + " " + (TL.axisY - 4) + " L " + (tlx(m.year) + 3.5) + " " + (TL.axisY - 10), fill: "none", stroke: "#5a5a5a", "stroke-width": 1 }, g);
      var name = sv("text", { x: m.x, y: m.y + lineH, fill: "#1a1a1a", "font-weight": 600 }, g);
      name.textContent = m.name;
      var texts = [name];
      m.lines.forEach(function (l, i) {
        var t = sv("text", { x: m.x, y: m.y + (i + 2) * lineH, fill: "#5a5a5a" }, g);
        t.textContent = l;
        texts.push(t);
      });
      tlGroups.push({ m: m, g: g, texts: texts, h: (m.lines.length + 1) * lineH });
    });
    measureAnnotations();
  }

  // Measure each annotation block so a zoom or a step can frame it whole instead of
  // slicing a line down the middle. Falls back to a character estimate where the
  // browser cannot measure text.
  function measureAnnotations() {
    tlBoxes = tlGroups.map(function (entry) {
      var w = 0;
      entry.texts.forEach(function (node) {
        var tw = 0;
        try { tw = node.getComputedTextLength(); } catch (err) { tw = 0; }
        if (!tw) tw = node.textContent.length * 6.1;
        if (tw > w) w = tw;
      });
      return { x: entry.m.x, y: entry.m.y, w: w, h: entry.h, g: entry.g };
    }).sort(function (a, b) { return a.x - b.x; });
  }
  function boxCentre(b) { return b.x + b.w / 2; }
  function frameBox(b) {
    var padX = 12, padY = 10, vw = viewW(), vh = viewH();
    var x = b.w <= vw ? boxCentre(b) - vw / 2 : b.x - padX;
    var y = b.h <= vh ? b.y + b.h / 2 - vh / 2 : b.y - padY;
    state.pan = clampPan({ x: x, y: y });
    focusBox = b;
  }
  function nearestBox() {
    var cx = state.pan.x + viewW() / 2, best = null, bd = Infinity;
    tlBoxes.forEach(function (b) {
      var d = Math.abs(boxCentre(b) - cx);
      if (d < bd) { bd = d; best = b; }
    });
    return best;
  }
  function stepAnnotation(dir) {
    if (!tlBoxes.length) return;
    var cx = state.pan.x + viewW() / 2, best = null;
    tlBoxes.forEach(function (b) {
      var c = boxCentre(b);
      if (dir > 0 ? c > cx + 4 : c < cx - 4) {
        if (!best || (dir > 0 ? c < boxCentre(best) : c > boxCentre(best))) best = b;
      }
    });
    if (!best) best = dir > 0 ? tlBoxes[tlBoxes.length - 1] : tlBoxes[0];
    frameBox(best);
  }

  function yearRangeText() {
    var a = Math.round(TL.yr0 + (state.pan.x / TL.w) * (TL.yr1 - TL.yr0));
    var b = Math.round(TL.yr0 + ((state.pan.x + viewW()) / TL.w) * (TL.yr1 - TL.yr0));
    return a + " to " + b;
  }

  function renderTimeline() {
    tl.setAttribute("viewBox", state.pan.x + " " + state.pan.y + " " + viewW() + " " + viewH());
    // When one annotation has been framed, hold the neighbouring blocks back so a half-visible
    // line from the block next door does not read as the framed one being cut off.
    tlBoxes.forEach(function (b) {
      b.g.setAttribute("opacity", focusBox && state.zi > 0 && b !== focusBox ? "0.2" : "1");
    });
    tl.classList.toggle("grab", state.zi > 0);
    clear(tlControls);
    var zg = el("span", "group");
    zg.appendChild(btn("−", function () { zoomTo(Math.max(state.zi - 1, 0)); update(); }, { aria: "Zoom out", disabled: state.zi === 0 }));
    zg.appendChild(btn("+", function () { zoomTo(Math.min(state.zi + 1, TL_ZOOMS.length - 1)); update(); }, { aria: "Zoom in", disabled: state.zi === TL_ZOOMS.length - 1 }));
    tlControls.appendChild(zg);
    if (state.zi > 0) {
      var pg = el("span", "group");
      pg.appendChild(btn("← Back", function () { stepAnnotation(-1); update(); }, { aria: "Previous annotation" }));
      pg.appendChild(btn("Next →", function () { stepAnnotation(1); update(); }, { aria: "Next annotation" }));
      tlControls.appendChild(pg);
      tlControls.appendChild(btn("Whole timeline", function () { resetTimeline(); update(); }, { className: "link" }));
    }
    var ro = el("span", "readout", state.zi === 0 ? "Zoom in to read the annotations, then step or drag along." : yearRangeText() + ", drag to move along");
    ro.setAttribute("aria-live", "polite");
    tlControls.appendChild(ro);
  }

  var drag = null;
  tl.addEventListener("pointerdown", function (e) {
    if (state.zi === 0) return;
    drag = { x: state.pan.x, y: state.pan.y, px: e.clientX, py: e.clientY };
    if (tl.setPointerCapture) { try { tl.setPointerCapture(e.pointerId); } catch (err) {} }
  });
  tl.addEventListener("pointermove", function (e) {
    if (!drag) return;
    var rect = tl.getBoundingClientRect();
    if (!rect.width) return;
    var k = viewW() / rect.width;
    state.pan = clampPan({ x: drag.x - (e.clientX - drag.px) * k, y: drag.y - (e.clientY - drag.py) * k });
    focusBox = null;
    renderTimeline();
  });
  function endDrag() { if (drag) { drag = null; update(); } }
  tl.addEventListener("pointerup", endDrag);
  tl.addEventListener("pointercancel", endDrag);
  tl.addEventListener("keydown", function (e) {
    var step = viewW() / 12;
    var handled = true;
    if (e.key === "ArrowLeft") { focusBox = null; movePan(-step, 0); }
    else if (e.key === "ArrowRight") { focusBox = null; movePan(step, 0); }
    else if (e.key === "ArrowUp") { focusBox = null; movePan(0, -step / 2); }
    else if (e.key === "ArrowDown") { focusBox = null; movePan(0, step / 2); }
    else if (e.key === "Home") resetTimeline();
    else if (e.key === "+" || e.key === "=") zoomTo(Math.min(state.zi + 1, TL_ZOOMS.length - 1));
    else if (e.key === "-") zoomTo(Math.max(state.zi - 1, 0));
    else handled = false;
    if (!handled) return;
    e.preventDefault();
    update();
  });

  /* ---------- Test scores ---------- */
  var ts = document.getElementById("ts");
  var tip = document.getElementById("tip");
  var legend = document.getElementById("legend");
  var tsControls = document.getElementById("ts-controls");
  var tableWrap = document.getElementById("table-wrap");
  function tsx(year) { return TS.plotX0 + ((year - TS.yr0) / (TS.yr1 - TS.yr0)) * (TS.plotX1 - TS.plotX0); }
  function tsy(v) { return TS.plotY0 + ((TS.v0 - v) / (TS.v0 - TS.v1)) * (TS.plotY1 - TS.plotY0); }
  function isHidden(name) { return state.hidden.indexOf(name) !== -1; }
  function shownSeries() { return SERIES.filter(function (s) { return !isHidden(s.name); }); }
  function lastValue(s) { return s.points[s.points.length - 1][1]; }
  function valueAt(s, year) {
    var pts = s.points;
    if (year < pts[0][0] || year > pts[pts.length - 1][0]) return null;
    for (var i = 0; i < pts.length; i++) {
      if (pts[i][0] === year) return { v: pts[i][1], exact: true };
      if (pts[i][0] > year) {
        var ay = pts[i - 1][0], av = pts[i - 1][1], by = pts[i][0], bv = pts[i][1];
        return { v: av + ((bv - av) * (year - ay)) / (by - ay), exact: false };
      }
    }
    return null;
  }
  function activeYear() { return hoverYear !== null ? hoverYear : state.year; }
  function toggleSeries(name) {
    var i = state.hidden.indexOf(name);
    if (i !== -1) state.hidden.splice(i, 1);
    else if (state.hidden.length < SERIES.length - 1) state.hidden.push(name);
    else return;
    state.explored.scores = true;
  }
  function stepYear(d) {
    var y = state.year === null ? (d > 0 ? TS.yr0 : TS.yr1) : state.year + d;
    state.year = Math.max(TS.yr0, Math.min(TS.yr1, y));
    state.explored.scores = true;
  }
  function yearFromPointer(clientX) {
    var rect = ts.getBoundingClientRect();
    if (!rect.width) return null;
    var x = ((clientX - rect.left) / rect.width) * TS.w;
    if (x < TS.plotX0 - 12 || x > TS.plotX1 + 12) return null;
    var yr = Math.round(TS.yr0 + ((x - TS.plotX0) / (TS.plotX1 - TS.plotX0)) * (TS.yr1 - TS.yr0));
    return Math.max(TS.yr0, Math.min(TS.yr1, yr));
  }

  function hoverRows(year) {
    var rows = [];
    shownSeries().forEach(function (s) { var at = valueAt(s, year); if (at) rows.push({ s: s, at: at }); });
    rows.sort(function (a, b) { return b.at.v - a.at.v; });
    return rows;
  }

  function renderScores() {
    clear(ts);
    var title = sv("title", {}, ts); title.textContent = "Test scores of AI systems on various capabilities relative to human performance, 1998 to 2023";
    GRID_VALUES.forEach(function (v) {
      var attrs = { x1: TS.plotX0, y1: tsy(v), x2: TS.plotX1, y2: tsy(v), stroke: v === 0 ? "#5a5a5a" : "#e8e5df" };
      if (v !== 0) attrs["stroke-dasharray"] = "4 4";
      sv("line", attrs, ts);
      var t = sv("text", { x: TS.plotX0 - 8, y: tsy(v) + 4, "text-anchor": "end", fill: "#5a5a5a" }, ts);
      t.textContent = String(v);
    });
    var note = sv("text", { x: TS.plotX0 + 8, y: tsy(0) - 6, fill: "#5a5a5a", "font-size": 11 }, ts);
    note.textContent = "Human performance, as the benchmark, is set to zero";
    X_TICKS.forEach(function (y) {
      var t = sv("text", { x: tsx(y), y: TS.plotY1 + 24, "text-anchor": "middle", fill: "#5a5a5a" }, ts);
      t.textContent = String(y);
    });
    shownSeries().forEach(function (s) {
      var g = sv("g", {}, ts);
      var attrs = { points: s.points.map(function (p) { return tsx(p[0]) + "," + tsy(p[1]); }).join(" "), fill: "none", stroke: s.color, "stroke-width": 2, "stroke-linejoin": "round" };
      if (s.dash) attrs["stroke-dasharray"] = s.dash;
      sv("polyline", attrs, g);
      s.points.forEach(function (p) {
        sv("circle", { cx: tsx(p[0]), cy: tsy(p[1]), r: 3.5, fill: s.color, stroke: "#fff", "stroke-width": 1.5 }, g);
      });
    });
    var ordered = SERIES.slice().sort(function (a, b) { return lastValue(b) - lastValue(a); });
    ordered.forEach(function (s, i) {
      var last = s.points[s.points.length - 1];
      var labelY = 46 + i * 22;
      var off = isHidden(s.name);
      if (!off) {
        sv("path", { d: "M " + (tsx(last[0]) + 4) + " " + tsy(last[1]) + " H " + (TS.plotX1 + 14) + " V " + (labelY - 4) + " H " + (TS.plotX1 + 20), fill: "none", stroke: "#e8e5df" }, ts);
        sv("line", { x1: TS.plotX1 + 24, y1: labelY - 4, x2: TS.plotX1 + 40, y2: labelY - 4, stroke: s.color, "stroke-width": 2, "stroke-dasharray": s.dash || "none" }, ts);
      }
      var t = sv("text", { x: TS.plotX1 + 46, y: labelY, fill: off ? "#5a5a5a" : "#1a1a1a", "font-weight": off ? 400 : 600 }, ts);
      if (off) t.setAttribute("text-decoration", "line-through");
      t.textContent = s.name;
    });
    var year = activeYear();
    if (year !== null) {
      var hg = sv("g", { "pointer-events": "none" }, ts);
      sv("line", { x1: tsx(year), y1: TS.plotY0, x2: tsx(year), y2: TS.plotY1, stroke: "#5a5a5a", "stroke-width": 1 }, hg);
      hoverRows(year).forEach(function (r) {
        sv("circle", { cx: tsx(year), cy: tsy(r.at.v), r: r.at.exact ? 5.5 : 4, fill: r.s.color, stroke: "#fff", "stroke-width": 2, opacity: r.at.exact ? 1 : 0.6 }, hg);
      });
    }
    renderTooltip(year);
  }

  function renderTooltip(year) {
    clear(tip);
    var rows = year === null ? [] : hoverRows(year);
    tip.classList.toggle("is-visible", rows.length > 0);
    if (!rows.length) return;
    tip.appendChild(el("div", "yr", String(year)));
    var table = el("table"), tbody = el("tbody");
    rows.forEach(function (r) {
      var tr = el("tr", r.at.exact ? "" : "approx");
      var td1 = el("td"); var sw = el("span", "sw"); sw.style.background = r.s.color; td1.appendChild(sw); tr.appendChild(td1);
      tr.appendChild(el("td", null, r.s.name + (r.at.exact ? "" : " (between data points)")));
      tr.appendChild(el("td", "v", r.at.v.toFixed(1)));
      tbody.appendChild(tr);
    });
    table.appendChild(tbody);
    tip.appendChild(table);
    var left = (tsx(year) / TS.w) * 100;
    var flip = tsx(year) > (TS.plotX0 + TS.plotX1) / 2;
    tip.style.left = left + "%";
    tip.style.transform = flip ? "translateX(calc(-100% - 10px))" : "translateX(10px)";
  }

  function renderLegend() {
    clear(legend);
    SERIES.forEach(function (s) {
      var off = isHidden(s.name);
      var b = el("button"); b.type = "button";
      b.setAttribute("aria-pressed", off ? "false" : "true");
      b.setAttribute("aria-label", (off ? "Show " : "Hide ") + s.name);
      var sw = sv("svg", { viewBox: "0 0 26 10", "aria-hidden": "true" });
      sv("line", { x1: 1, y1: 5, x2: 25, y2: 5, stroke: off ? "#5a5a5a" : s.color, "stroke-width": 2, "stroke-dasharray": s.dash || "none" }, sw);
      b.appendChild(sw);
      b.appendChild(el("span", null, s.name));
      b.appendChild(el("span", "state", off ? "hidden" : "shown"));
      b.addEventListener("click", function () { toggleSeries(s.name); update(); });
      legend.appendChild(b);
    });
    clear(tsControls);
    var yg = el("span", "group");
    yg.appendChild(btn("◀ Earlier year", function () { stepYear(-1); update(); }, { aria: "Inspect the previous year" }));
    yg.appendChild(btn("Later year ▶", function () { stepYear(1); update(); }, { aria: "Inspect the next year" }));
    tsControls.appendChild(yg);
    if (state.year !== null) tsControls.appendChild(btn("Clear year", function () { state.year = null; update(); }, { className: "link" }));
    if (state.hidden.length) tsControls.appendChild(btn("Show all six", function () { state.hidden = []; update(); }, { className: "link" }));
    tsControls.appendChild(btn(state.table ? "Hide data table" : "Show data table", function () { state.table = !state.table; state.explored.scores = true; update(); }, { className: "link" }));
    var ro = el("span", "readout", state.year === null ? "Hover the chart, or step through the years, to read values." : "Inspecting " + state.year);
    ro.setAttribute("aria-live", "polite");
    tsControls.appendChild(ro);
  }

  function renderTable() {
    clear(tableWrap);
    tableWrap.classList.toggle("is-visible", state.table);
    if (!state.table) return;
    var years = {};
    SERIES.forEach(function (s) { s.points.forEach(function (p) { years[p[0]] = true; }); });
    var ys = Object.keys(years).map(Number).sort(function (a, b) { return a - b; });
    var table = el("table", "data");
    table.setAttribute("aria-label", "Test scores relative to human performance, by year");
    var thead = el("thead"), hr = el("tr");
    hr.appendChild(el("th", null, "Year"));
    SERIES.forEach(function (s) { hr.appendChild(el("th", null, s.name)); });
    thead.appendChild(hr); table.appendChild(thead);
    var tbody = el("tbody");
    ys.forEach(function (y) {
      var tr = el("tr");
      tr.appendChild(el("td", null, String(y)));
      SERIES.forEach(function (s) {
        var v = null;
        s.points.forEach(function (p) { if (p[0] === y) v = p[1]; });
        tr.appendChild(el("td", null, v === null ? "" : v.toFixed(1)));
      });
      tbody.appendChild(tr);
    });
    table.appendChild(tbody);
    tableWrap.appendChild(table);
  }

  ts.addEventListener("pointermove", function (e) { hoverYear = yearFromPointer(e.clientX); renderScores(); });
  ts.addEventListener("pointerleave", function () { hoverYear = null; renderScores(); });
  ts.addEventListener("keydown", function (e) {
    if (e.key === "ArrowLeft") stepYear(-1);
    else if (e.key === "ArrowRight") stepYear(1);
    else if (e.key === "Escape") state.year = null;
    else return;
    e.preventDefault();
    update();
  });

  /* ---------- State ---------- */
  function summary() {
    var s = "Timeline of notable AI systems 1940 to 2060: " + (state.zi === 0 ? "whole timeline shown, not zoomed in yet." : "zoomed in (level " + (state.zi + 1) + " of " + TL_ZOOMS.length + "), viewing " + yearRangeText() + ".");
    var shown = shownSeries().map(function (x) { return x.name; });
    s += " Test-scores chart: showing " + shown.length + " of " + SERIES.length + " series (" + shown.join(", ") + ")";
    s += state.hidden.length ? "; hidden: " + state.hidden.join(", ") + "." : ".";
    if (state.year !== null) {
      var rows = hoverRows(state.year);
      s += " Inspecting " + state.year + ": " + (rows.length ? rows.map(function (r) { return r.s.name + " " + r.at.v.toFixed(1) + (r.at.exact ? "" : " (interpolated)"); }).join("; ") : "no series has data that year") + ".";
    }
    if (state.table) s += " Data table open.";
    return s;
  }
  function persist() {
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (!completed && state.explored.timeline && state.explored.scores) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }
  function renderStatus() {
    var st = document.getElementById("status");
    var parts = [];
    parts.push(state.explored.timeline ? "Timeline explored ✓" : "Timeline: zoom in to explore");
    parts.push(state.explored.scores ? "Chart explored ✓" : "Chart: inspect a year or toggle a series");
    st.textContent = parts.join(" · ");
  }
  function render() { renderTimeline(); renderScores(); renderLegend(); renderTable(); renderStatus(); }
  function update() { render(); persist(); }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.zi === "number" && saved.zi >= 0 && saved.zi < TL_ZOOMS.length) state.zi = saved.zi;
      if (saved.pan && typeof saved.pan.x === "number" && typeof saved.pan.y === "number") state.pan = clampPan(saved.pan);
      if (Array.isArray(saved.hidden)) state.hidden = saved.hidden.filter(function (n) { return SERIES.some(function (s) { return s.name === n; }); }).slice(0, SERIES.length - 1);
      if (typeof saved.year === "number" && saved.year >= TS.yr0 && saved.year <= TS.yr1) state.year = saved.year;
      if (typeof saved.table === "boolean") state.table = saved.table;
      if (saved.explored && typeof saved.explored === "object") state.explored = { timeline: !!saved.explored.timeline, scores: !!saved.explored.scores };
    }
    completed = !!(meta && meta.completed);
    render();
  }

  buildTimeline();
  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = localStorage.getItem(STORAGE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
</script>
</body>
</html>

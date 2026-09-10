---
id: '4a01e137-f014-4994-a261-ea529678050b'
title: Timeline of notable AI systems
summary_for_tutor: "An interactive timeline of notable artificial intelligence systems from 1940 to 2060, redrawn from Our World in Data. Six milestones are annotated: 1945 first digital computers, 1950 Theseus, 1957 Perceptron Mark I, 1992 TD-Gammon, 2012 AlexNet, and 2024 artificial intelligence with language and image recognition comparable to humans. The axis is solid up to 2024 and faded after it, so the learner can see how much of the drawn span is still ahead. The view opens zoomed in on the 1940s to the 2010s, so the annotation text is readable, and the learner drags, uses the pan buttons or the arrow keys to move left and right along the axis, and zooms in and out over four levels. Each annotation is a card joined to its year by a leader line ending in an arrow on the axis. The widget counts how many of the six milestones the learner has brought fully into view, and is complete once all six have been seen, which forces a pan across the whole span. The point to draw out is the gap between the first four milestones and the last two: seventy years of slow progress, then twelve years from AlexNet to human-comparable language and image recognition."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Timeline of notable AI systems</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "short-history". Chart redrawn from Our World in Data (CC BY 4.0). -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .card { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px; }
  .plot { overflow: hidden; }
  svg { display: block; width: 100%; height: auto; font-family: var(--font-ui); }
  /* No browser focus ring on click; keyboard users get a ring in the course accent. */
  svg:focus { outline: none; }
  body.kb svg:focus { outline: 2px solid var(--accent, #b87018); outline-offset: 2px; border-radius: 4px; }
  .grab { cursor: grab; touch-action: pan-y; }
  .grab:active { cursor: grabbing; }
  .controls { display: flex; flex-wrap: wrap; align-items: center; gap: 8px; margin-top: 8px; }
  .group { display: flex; gap: 4px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.4; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.link { border: 0; padding: 4px 6px; color: var(--muted); text-decoration: underline; text-underline-offset: 3px; }
  button.link:hover { color: var(--text); background: transparent; }
  button.link:disabled { text-decoration: none; }
  .readout { margin-left: auto; font-size: 12px; color: var(--muted); }
  .status { margin: 10px 0 0; font-size: 12px; color: var(--muted); }
  .credit { color: var(--muted); font-size: 12px; margin: 8px 0 0; }
  .credit a { color: var(--accent-hover); }
  @media (max-width: 460px) {
    body { padding: 12px; }
    .readout { margin-left: 0; width: 100%; }
  }
</style>
</head>
<body>
<div class="card">
  <div class="plot" id="tl-plot">
    <svg id="tl" role="group" tabindex="0" aria-label="A timeline of notable artificial intelligence systems, 1940 to 2060. Drag the timeline, or use the pan buttons and the left and right arrow keys, to move along it. Plus and minus zoom, Home shows the whole span."></svg>
  </div>
  <div class="controls" id="tl-controls"></div>
</div>
<p class="status" id="tl-status"></p>
<p class="credit" id="tl-credit"></p>

<script>
  document.addEventListener("keydown", function (e) { if (e.key === "Tab") document.body.classList.add("kb"); });
  document.addEventListener("pointerdown", function () { document.body.classList.remove("kb"); });
(function () {
  "use strict";

  var SVG_NS = "http://www.w3.org/2000/svg";
  var OWID_URL = "https://ourworldindata.org/brief-history-of-ai";

  /* ---------- Data (verbatim from XLab's short-history.tsx) ---------- */
  var YR0 = 1940, YR1 = 2060, SPAN = 120, BOUNDARY = 2024;
  var MILESTONES = [
    { year: 1945, name: "First digital computers", lines: [] },
    { year: 1950, name: "Theseus:", lines: [
      "A small robotic mouse that could",
      "navigate a simple maze and",
      "remember its course." ] },
    { year: 1957, name: "Perceptron Mark I:", lines: [
      "Regarded as the first artificial neural",
      "network, it could visually distinguish cards",
      "marked on the left side from those marked",
      "on the right." ] },
    { year: 1992, name: "TD-Gammon:", lines: [
      "This software learned to play",
      "backgammon at a high level, just",
      "below the top human players." ] },
    { year: 2012, name: "AlexNet:", lines: [
      "This was a pivotal early “deep learning”",
      "system, a neural network with many",
      "layers, that could recognize images of",
      "objects such as dogs and cars at",
      "near-human level." ] },
    { year: BOUNDARY, name: "Artificial intelligence with language and", lines: [
      "image recognition capabilities that are",
      "comparable to those of humans" ] }
  ];
  // XLab's zoom ladder, kept as is. Index 1 is the opening view, so the
  // annotation text is legible without the learner having to zoom first.
  var TL_ZOOMS = [1, 1.6, 2.4, 3.4];
  var DEFAULT_ZI = 1;

  /* ---------- Layout constants (real pixels: the SVG is drawn 1:1) ---------- */
  var MARGIN = 26, LINE_H = 16, LANE_GAP = 12, FONT = 12, GUTTER = 16;

  var COL = { text: "#1a1a1a", muted: "#5a5a5a", border: "#e8e5df", surface: "#faf8f3", accent: "#b87018", card: "#ffffff" };

  var STORAGE_KEY = "lens-widget-short-history-timeline";
  var state = { zi: DEFAULT_ZI, viewStart: YR0, seen: [] };
  var completed = false;

  var plotEl = document.getElementById("tl-plot");
  var svg = document.getElementById("tl");
  var controls = document.getElementById("tl-controls");
  var statusEl = document.getElementById("tl-status");
  var hover = -1;

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function sv(tag, attrs, parent) {
    var n = document.createElementNS(SVG_NS, tag);
    for (var k in attrs) n.setAttribute(k, String(attrs[k]));
    if (parent) parent.appendChild(n);
    return n;
  }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }
  function btn(label, onClick, opts) {
    var b = el("button", opts && opts.className, label);
    b.type = "button";
    if (opts && opts.aria) b.setAttribute("aria-label", opts.aria);
    if (opts && opts.disabled) b.disabled = true;
    b.addEventListener("click", onClick);
    return b;
  }

  /* ---------- Credit ---------- */
  (function () {
    var node = document.getElementById("tl-credit");
    node.appendChild(document.createTextNode("Chart redrawn from Max Roser, The Brief History of Artificial Intelligence, Our World in Data, 6 Dec. 2022, "));
    var a = el("a", null, "ourworldindata.org/brief-history-of-ai");
    a.href = OWID_URL; a.target = "_blank"; a.rel = "noopener";
    node.appendChild(a);
    node.appendChild(document.createTextNode(". Licensed CC BY 4.0."));
  }());

  /* ---------- Text measurement ---------- */
  // Real widths where the browser can give them, a per character estimate otherwise
  // (jsdom and the first paint before DM Sans has loaded).
  var measureSvg = null;
  var widthCache = {};
  function textWidth(str, bold) {
    var key = (bold ? "b:" : "n:") + str;
    if (widthCache[key] !== undefined) return widthCache[key];
    var w = 0;
    if (!measureSvg) {
      measureSvg = document.createElementNS(SVG_NS, "svg");
      measureSvg.setAttribute("width", "0");
      measureSvg.setAttribute("height", "0");
      measureSvg.setAttribute("aria-hidden", "true");
      measureSvg.style.position = "absolute";
      measureSvg.style.visibility = "hidden";
      document.body.appendChild(measureSvg);
    }
    var t = sv("text", { "font-size": FONT, "font-family": '"DM Sans", Arial, sans-serif' }, measureSvg);
    if (bold) t.setAttribute("font-weight", "600");
    t.textContent = str;
    try { if (t.getComputedTextLength) w = t.getComputedTextLength(); } catch (err) { w = 0; }
    measureSvg.removeChild(t);
    if (!w) w = str.length * (bold ? 6.6 : 6.2);
    widthCache[key] = w;
    return w;
  }
  function resetMeasurements() { widthCache = {}; }

  /* ---------- Layout ---------- */
  function zoom() { return TL_ZOOMS[state.zi]; }
  function yearsVisible() { return SPAN / zoom(); }
  function canvasWidth() {
    var w = plotEl.clientWidth || 0;
    if (!w) w = 700;
    return Math.max(280, w);
  }
  function clampView() {
    var yv = yearsVisible();
    state.viewStart = Math.min(Math.max(state.viewStart, YR0), YR1 - yv);
  }

  function computeLayout() {
    clampView();
    var W = canvasWidth();
    var yv = yearsVisible();
    var ppy = (W - 2 * MARGIN) / yv;
    var virtW = 2 * MARGIN + SPAN * ppy;

    var blocks = MILESTONES.map(function (m, i) {
      var rows = [{ text: m.name, bold: true, year: String(m.year) }];
      m.lines.forEach(function (l) { rows.push({ text: l, bold: false }); });
      var w = 0;
      rows.forEach(function (r, ri) {
        var lw = textWidth(r.text, r.bold) + (ri === 0 ? textWidth(r.year + "  ", false) : 0);
        if (lw > w) w = lw;
      });
      var vx = MARGIN + (m.year - YR0) * ppy;
      var x = vx;
      if (x + w > virtW - 8) x = virtW - 8 - w;
      if (x < 8) x = 8;
      return { i: i, m: m, rows: rows, w: w, h: rows.length * LINE_H, vx: vx, x: x, lane: 0 };
    });

    var order = blocks.slice().sort(function (a, b) { return a.x - b.x; });
    var laneEnd = [];
    order.forEach(function (b) {
      for (var L = 0; ; L++) {
        if (laneEnd[L] === undefined || laneEnd[L] + GUTTER <= b.x) {
          laneEnd[L] = b.x + b.w;
          b.lane = L;
          return;
        }
      }
    });
    var nLanes = laneEnd.length;
    var laneH = [];
    for (var L = 0; L < nLanes; L++) laneH[L] = 0;
    blocks.forEach(function (b) { if (b.h > laneH[b.lane]) laneH[b.lane] = b.h; });

    // Lane 0 sits closest to the axis, so it is laid out last (largest y).
    var y = 6, laneTop = [];
    for (var L2 = nLanes - 1; L2 >= 0; L2--) { laneTop[L2] = y; y += laneH[L2] + LANE_GAP; }
    var axisY = y - LANE_GAP + 22;
    var H = axisY + 34;

    blocks.forEach(function (b) {
      b.top = laneTop[b.lane] + (laneH[b.lane] - b.h);
      b.bottom = b.top + b.h;
    });

    return { W: W, H: H, ppy: ppy, virtW: virtW, axisY: axisY, blocks: blocks, offset: (state.viewStart - YR0) * ppy, yv: yv };
  }

  /* ---------- Render ---------- */
  var lastLayout = null;

  function render() {
    var L = computeLayout();
    lastLayout = L;
    var W = L.W, H = L.H, axisY = L.axisY, ppy = L.ppy, off = L.offset;
    var vx = function (year) { return MARGIN + (year - YR0) * ppy; };

    clear(svg);
    svg.setAttribute("viewBox", "0 0 " + W + " " + H);
    svg.setAttribute("font-size", FONT);
    svg.classList.toggle("grab", L.yv < SPAN);
    var title = sv("title", {}, svg);
    title.textContent = "A timeline of notable artificial intelligence systems, 1940 to 2060";

    var root = sv("g", { transform: "translate(" + (-off) + ",0)" }, svg);

    // Axis: solid to 2024, faded for the drawn span that is still ahead.
    sv("line", { x1: vx(YR0), y1: axisY, x2: vx(BOUNDARY), y2: axisY, stroke: COL.accent, "stroke-width": 4 }, root);
    sv("line", { x1: vx(BOUNDARY), y1: axisY, x2: vx(YR1), y2: axisY, stroke: COL.accent, "stroke-opacity": 0.35, "stroke-width": 4 }, root);
    sv("circle", { cx: vx(BOUNDARY), cy: axisY, r: 5.5, fill: COL.accent }, root);

    var labelStep = 10;
    while (ppy * labelStep < 42) labelStep += 10;
    for (var yr = YR0; yr <= YR1; yr += 10) {
      sv("line", { x1: vx(yr), y1: axisY + 6, x2: vx(yr), y2: axisY + 11, stroke: COL.muted }, root);
      if ((yr - YR0) % labelStep === 0) {
        var t = sv("text", { x: vx(yr), y: axisY + 27, "text-anchor": "middle", fill: COL.muted }, root);
        t.textContent = String(yr);
      }
    }

    // Leader lines go in first so that a line crossing a lower annotation
    // passes behind that card rather than through its words.
    var leaders = sv("g", {}, root);
    var cards = sv("g", {}, root);
    var marks = sv("g", {}, root);

    L.blocks.forEach(function (b) {
      var on = hover === b.i;
      var stroke = on ? COL.accent : COL.muted;
      var mx = b.vx;
      var anchor = Math.min(Math.max(mx, b.x), b.x + b.w);
      var startY = b.bottom + 4;
      var endY = axisY - 9;
      var d;
      if (Math.abs(anchor - mx) < 0.5) {
        d = "M " + mx + " " + startY + " V " + endY;
      } else {
        var gy = Math.min(startY + 10, endY - 4);
        d = "M " + anchor + " " + startY + " V " + gy + " H " + mx + " V " + endY;
      }
      sv("path", { d: d, fill: "none", stroke: stroke, "stroke-width": on ? 1.6 : 1 }, leaders);

      // Card behind the words.
      var g = sv("g", {}, cards);
      sv("rect", {
        x: b.x - 8, y: b.top - 6, width: b.w + 16, height: b.h + 10, rx: 6,
        fill: COL.surface, stroke: on ? COL.accent : COL.border, "stroke-width": on ? 1.5 : 1
      }, g);
      b.rows.forEach(function (r, ri) {
        var tn = sv("text", { x: b.x, y: b.top + (ri + 1) * LINE_H - 4, fill: r.bold ? COL.text : COL.muted }, g);
        if (r.bold) {
          var y1 = sv("tspan", { fill: COL.accent, "font-weight": 600 }, tn);
          y1.textContent = r.year + "  ";
          var n1 = sv("tspan", { "font-weight": 600 }, tn);
          n1.textContent = r.text;
        } else {
          tn.textContent = r.text;
        }
      });
      var hit = sv("rect", {
        x: b.x - 8, y: b.top - 6, width: b.w + 16, height: b.h + 10,
        fill: "transparent", "pointer-events": "all"
      }, g);
      var ht = sv("title", {}, hit);
      ht.textContent = b.m.year + ": " + b.m.name + " " + b.m.lines.join(" ");
      hit.addEventListener("mouseenter", function () { hover = b.i; render(); });
      hit.addEventListener("mouseleave", function () { if (hover === b.i) { hover = -1; render(); } });

      // Arrow head and marker dot on the axis, at the milestone's own year.
      sv("path", {
        d: "M " + (mx - 3.5) + " " + (axisY - 12) + " L " + mx + " " + (axisY - 5) + " L " + (mx + 3.5) + " " + (axisY - 12),
        fill: "none", stroke: stroke, "stroke-width": on ? 1.6 : 1
      }, marks);
      sv("circle", { cx: mx, cy: axisY, r: on ? 4.5 : 3.2, fill: on ? COL.accent : COL.text }, marks);
    });

    markSeen(L);
    renderControls(L);
    renderStatus();
  }

  function markSeen(L) {
    L.blocks.forEach(function (b) {
      var left = b.x - 8 - L.offset;
      var right = b.x + b.w + 8 - L.offset;
      if (left >= -1 && right <= L.W + 1) { state.seen[b.i] = true; return; }
      // A card wider than the frame (a very narrow phone) could never be framed whole,
      // which would make the exercise impossible to finish; its start being in view counts.
      if (b.w + 16 > L.W && left >= -1 && left <= L.W - 60) state.seen[b.i] = true;
    });
  }
  function seenCount() {
    var n = 0;
    for (var i = 0; i < MILESTONES.length; i++) if (state.seen[i]) n++;
    return n;
  }

  function viewText() {
    var a = Math.round(state.viewStart);
    var b = Math.round(state.viewStart + yearsVisible());
    return a + " to " + b;
  }

  function renderControls(L) {
    clear(controls);
    var atLeft = state.viewStart <= YR0 + 0.001;
    var atRight = state.viewStart >= YR1 - L.yv - 0.001;
    var zg = el("span", "group");
    zg.appendChild(btn("−", function () { zoomTo(state.zi - 1); }, { aria: "Zoom out", disabled: state.zi === 0 }));
    zg.appendChild(btn("+", function () { zoomTo(state.zi + 1); }, { aria: "Zoom in", disabled: state.zi === TL_ZOOMS.length - 1 }));
    controls.appendChild(zg);
    var pg = el("span", "group");
    pg.appendChild(btn("←", function () { pan(-L.yv / 6); }, { aria: "Pan left, towards earlier years", disabled: atLeft }));
    pg.appendChild(btn("→", function () { pan(L.yv / 6); }, { aria: "Pan right, towards later years", disabled: atRight }));
    controls.appendChild(pg);
    controls.appendChild(btn("Whole timeline", function () { resetView(); }, { className: "link", disabled: state.zi === 0 && atLeft }));
    var ro = el("span", "readout", "Showing " + viewText());
    ro.setAttribute("aria-live", "polite");
    controls.appendChild(ro);
  }

  function renderStatus() {
    var n = seenCount(), total = MILESTONES.length;
    statusEl.textContent = n >= total
      ? "All " + total + " milestones seen ✓"
      : n + " of " + total + " milestones brought fully into view. Drag the timeline, or use the arrow buttons, to find the rest.";
  }

  /* ---------- Interaction ---------- */
  function zoomTo(next) {
    next = Math.min(Math.max(next, 0), TL_ZOOMS.length - 1);
    if (next === state.zi) return;
    var centre = state.viewStart + yearsVisible() / 2;
    state.zi = next;
    state.viewStart = centre - yearsVisible() / 2;
    clampView();
    update();
  }
  function pan(dYears) {
    state.viewStart += dYears;
    clampView();
    update();
  }
  function resetView() {
    state.zi = 0;
    state.viewStart = YR0;
    update();
  }

  var drag = null;
  svg.addEventListener("pointerdown", function (e) {
    if (!lastLayout || lastLayout.yv >= SPAN) return;
    drag = { start: state.viewStart, px: e.clientX };
    if (svg.setPointerCapture) { try { svg.setPointerCapture(e.pointerId); } catch (err) {} }
  });
  svg.addEventListener("pointermove", function (e) {
    if (!drag || !lastLayout) return;
    var rect = svg.getBoundingClientRect();
    var scale = rect.width ? lastLayout.W / rect.width : 1;
    state.viewStart = drag.start - ((e.clientX - drag.px) * scale) / lastLayout.ppy;
    clampView();
    render();
  });
  function endDrag() { if (drag) { drag = null; persist(); } }
  svg.addEventListener("pointerup", endDrag);
  svg.addEventListener("pointercancel", endDrag);

  svg.addEventListener("keydown", function (e) {
    var step = yearsVisible() / 12;
    if (e.key === "ArrowLeft") pan(-step);
    else if (e.key === "ArrowRight") pan(step);
    else if (e.key === "Home") resetView();
    else if (e.key === "End") { state.viewStart = YR1; clampView(); update(); }
    else if (e.key === "+" || e.key === "=") zoomTo(state.zi + 1);
    else if (e.key === "-" || e.key === "_") zoomTo(state.zi - 1);
    else return;
    e.preventDefault();
  });

  /* ---------- State ---------- */
  function summary() {
    var s = "Timeline of notable AI systems, 1940 to 2060. The learner is viewing "
      + viewText() + " at zoom level " + (state.zi + 1) + " of " + TL_ZOOMS.length + ". ";
    var seenNames = [], missNames = [];
    MILESTONES.forEach(function (m, i) {
      var label = m.year + " " + m.name.replace(/:$/, "");
      if (state.seen[i]) seenNames.push(label); else missNames.push(label);
    });
    s += "Milestones brought fully into view: " + (seenNames.length ? seenNames.join("; ") : "none yet") + ".";
    if (missNames.length) s += " Still to reach: " + missNames.join("; ") + ".";
    else s += " All six have been seen, so the exercise is complete.";
    return s;
  }
  function persist() {
    var snap = { zi: state.zi, viewStart: state.viewStart, seen: state.seen.slice(0, MILESTONES.length) };
    if (window.Lens) {
      window.Lens.saveState(snap, summary());
      if (!completed && seenCount() >= MILESTONES.length) { completed = true; window.Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snap)); } catch (err) {}
    }
  }
  function update() { render(); persist(); }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.zi === "number" && saved.zi >= 0 && saved.zi < TL_ZOOMS.length) state.zi = saved.zi;
      if (typeof saved.viewStart === "number" && isFinite(saved.viewStart)) state.viewStart = saved.viewStart;
      if (Array.isArray(saved.seen)) state.seen = saved.seen.map(Boolean).slice(0, MILESTONES.length);
    }
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    window.Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = localStorage.getItem(STORAGE_KEY); } catch (err) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (err) {} }
  }

  // Relayout when the frame width changes, and once the web font has loaded so the
  // annotation cards are sized against the real glyph widths.
  var pending = null;
  function relayout() {
    if (pending) return;
    pending = setTimeout(function () { pending = null; resetMeasurements(); render(); }, 60);
  }
  if (window.ResizeObserver) { try { new ResizeObserver(relayout).observe(plotEl); } catch (err) {} }
  window.addEventListener("resize", relayout);
  if (document.fonts && document.fonts.ready && document.fonts.ready.then) {
    document.fonts.ready.then(function () { resetMeasurements(); render(); });
  }
}());
</script>
</body>
</html>

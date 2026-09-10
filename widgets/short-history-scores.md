---
id: '62045926-f088-4a7b-b56a-46c33ad4de64'
title: AI test scores relative to human performance
summary_for_tutor: "A line chart, redrawn from Our World in Data, of AI test scores on six capabilities relative to human performance, 1998 to 2023: reading comprehension, image recognition, language understanding, handwriting recognition, speech recognition and predictive reasoning. Each capability starts at minus 100 when its benchmark is introduced, human performance is the zero line, and a line crossing zero means AI scored more points than humans on that benchmark. The learner moves the pointer across the plot, or focuses it and uses the arrow keys, to get a crosshair and a readout of every series value in that year, sorted from highest to lowest, with interpolated values marked as such. A row of legend buttons hides and shows individual series so one line can be read on its own, and a Show data table toggle opens every underlying data point. The widget is complete once the learner has read a year, hidden a series or opened the table. The point to draw out is how recent and how compressed the crossings are: nothing crosses zero before 2015, and five of the six do so between 2015 and 2023."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>AI test scores relative to human performance</title>
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
  .card { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px; position: relative; }
  .plot { overflow-x: auto; }
  svg { display: block; width: 100%; height: auto; font-family: var(--font-ui); font-size: 12px; }
  svg#ts { min-width: 560px; }
  svg:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; border-radius: 4px; }
  .legend { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 10px; }
  .legend button { display: inline-flex; align-items: center; gap: 8px; padding: 5px 10px; font-size: 12px; }
  .legend button[aria-pressed="false"] { color: var(--muted); text-decoration: line-through; }
  .legend svg { width: 26px; height: 10px; flex: 0 0 auto; min-width: 0; }
  .legend .state { font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
  .controls { display: flex; flex-wrap: wrap; align-items: center; gap: 8px; margin-top: 8px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button.link { border: 0; padding: 4px 6px; color: var(--muted); text-decoration: underline; text-underline-offset: 3px; }
  button.link:hover { color: var(--text); background: transparent; }
  .readout { margin-left: auto; font-size: 12px; color: var(--muted); }
  .tooltip {
    position: absolute; top: 12px; z-index: 2; pointer-events: none; display: none;
    border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 10px; font-size: 12px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.10);
  }
  .tooltip.is-visible { display: block; }
  .tooltip .yr { font-weight: 600; font-size: 13px; margin-bottom: 4px; }
  .tooltip table { border-collapse: collapse; }
  .tooltip td { padding: 1px 4px; white-space: nowrap; }
  .tooltip td.v { text-align: right; font-variant-numeric: tabular-nums; font-weight: 500; }
  .tooltip tr.approx { color: var(--muted); }
  .tooltip .foot { margin: 5px 0 0; color: var(--muted); font-size: 11px; max-width: 200px; }
  .sw { display: inline-block; width: 10px; height: 10px; border-radius: 3px; vertical-align: middle; }
  .table-wrap { overflow-x: auto; margin-top: 10px; display: none; }
  .table-wrap.is-visible { display: block; }
  table.data { border-collapse: collapse; font-size: 12px; min-width: 560px; }
  table.data th, table.data td { border: 1px solid var(--border); padding: 4px 8px; text-align: right; font-variant-numeric: tabular-nums; }
  table.data th { background: var(--surface); font-weight: 600; }
  table.data td:first-child, table.data th:first-child { text-align: left; }
  .status { margin: 10px 0 0; font-size: 12px; color: var(--muted); }
  .credit { color: var(--muted); font-size: 12px; margin: 8px 0 0; }
  .credit a { color: var(--accent-hover); }
  @media (max-width: 640px) {
    body { padding: 12px; }
    .tooltip { left: 8px !important; right: 8px; transform: none !important; }
    .readout { margin-left: 0; width: 100%; }
  }
</style>
</head>
<body>
<div class="card">
  <div class="plot">
    <svg id="ts" viewBox="0 0 700 340" role="img" tabindex="0" aria-label="Test scores of AI systems on various capabilities relative to human performance, 1998 to 2023. Move the pointer across the chart, or use the left and right arrow keys, to read the values for one year."></svg>
  </div>
  <div class="tooltip" id="tip" aria-hidden="true"></div>
  <div class="legend" id="legend" role="group" aria-label="Series shown"></div>
  <div class="controls" id="ts-controls"></div>
  <div class="table-wrap" id="table-wrap"></div>
</div>
<p class="status" id="ts-status"></p>
<p class="credit" id="ts-credit"></p>

<script>
(function () {
  "use strict";

  var SVG_NS = "http://www.w3.org/2000/svg";
  var OWID_URL = "https://ourworldindata.org/brief-history-of-ai";

  /* ---------- Data (verbatim from XLab's short-history.tsx) ---------- */
  // Colours are a six slot categorical palette (XLab's own tokens fail a colour
  // vision check); each series also carries its own dash pattern, so the lines
  // are told apart without relying on colour.
  var SERIES = [
    { name: "Reading comprehension", color: "#2a78d6", dash: "", points: [[2016, -100], [2017, -8.9], [2018, 6.6], [2019, 18.1], [2020, 18.8]] },
    { name: "Image recognition", color: "#eb6834", dash: "7 4", points: [[2009, -100], [2012, -44.2], [2014, -6.8], [2015, 0.7], [2016, 6.6], [2018, 11.7], [2019, 9.5], [2020, 16.4]] },
    { name: "Language understanding", color: "#1baf7a", dash: "2 3", points: [[2018, -100], [2019, 3.7], [2020, 12.0], [2022, 15.7]] },
    { name: "Handwriting recognition", color: "#eda100", dash: "9 3 2 3", points: [[1998, -100], [2002, -48.0], [2003, -26.7], [2006, -25.3], [2010, -20.0], [2012, -4.0], [2013, -1.3], [2018, 2.7]] },
    { name: "Speech recognition", color: "#e87ba4", dash: "4 3", points: [[1998, -100], [2011, -65.6], [2013, -52.7], [2014, -27.8], [2015, -8.7], [2016, -1.2], [2017, 0.4], [2018, 1.6]] },
    { name: "Predictive reasoning", color: "#008300", dash: "12 4", points: [[2019, -100], [2021, -80.5], [2022, -30.6], [2023, -0.6]] }
  ];
  var TS = { w: 700, h: 340, plotX0: 48, plotX1: 676, plotY0: 26, plotY1: 296, yr0: 1998, yr1: 2023, v0: 25, v1: -100 };
  var GRID_VALUES = [20, 0, -20, -40, -60, -80, -100];
  var X_TICKS = [1998, 2005, 2010, 2015, 2020, 2023];
  var COL = { text: "#1a1a1a", muted: "#5a5a5a", border: "#e8e5df" };

  var STORAGE_KEY = "lens-widget-short-history-scores";
  var state = { hidden: [], year: null, table: false, explored: false };
  var completed = false;
  var hoverYear = null;
  var emphasis = null;

  var ts = document.getElementById("ts");
  var tip = document.getElementById("tip");
  var legend = document.getElementById("legend");
  var controls = document.getElementById("ts-controls");
  var tableWrap = document.getElementById("table-wrap");
  var statusEl = document.getElementById("ts-status");

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
    b.addEventListener("click", onClick);
    return b;
  }

  /* ---------- Credit ---------- */
  (function () {
    var node = document.getElementById("ts-credit");
    node.appendChild(document.createTextNode("Chart redrawn from Max Roser, The Brief History of Artificial Intelligence, Our World in Data, 6 Dec. 2022, "));
    var a = el("a", null, "ourworldindata.org/brief-history-of-ai");
    a.href = OWID_URL; a.target = "_blank"; a.rel = "noopener";
    node.appendChild(a);
    node.appendChild(document.createTextNode(". Licensed CC BY 4.0. Underlying data from Kiela et al., 2023."));
  }());

  /* ---------- Scales ---------- */
  function tsx(year) { return TS.plotX0 + ((year - TS.yr0) / (TS.yr1 - TS.yr0)) * (TS.plotX1 - TS.plotX0); }
  function tsy(v) { return TS.plotY0 + ((TS.v0 - v) / (TS.v0 - TS.v1)) * (TS.plotY1 - TS.plotY0); }
  function isHidden(name) { return state.hidden.indexOf(name) !== -1; }
  function shownSeries() { return SERIES.filter(function (s) { return !isHidden(s.name); }); }
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
  function rowsFor(year) {
    var rows = [];
    shownSeries().forEach(function (s) { var at = valueAt(s, year); if (at) rows.push({ s: s, at: at }); });
    rows.sort(function (a, b) { return b.at.v - a.at.v; });
    return rows;
  }
  function yearFromPointer(clientX) {
    var rect = ts.getBoundingClientRect();
    if (!rect.width) return null;
    var x = ((clientX - rect.left) / rect.width) * TS.w;
    if (x < TS.plotX0 - 12 || x > TS.plotX1 + 12) return null;
    var yr = Math.round(TS.yr0 + ((x - TS.plotX0) / (TS.plotX1 - TS.plotX0)) * (TS.yr1 - TS.yr0));
    return Math.max(TS.yr0, Math.min(TS.yr1, yr));
  }

  /* ---------- Mutations ---------- */
  function toggleSeries(name) {
    var i = state.hidden.indexOf(name);
    if (i !== -1) state.hidden.splice(i, 1);
    else if (state.hidden.length < SERIES.length - 1) state.hidden.push(name);
    else return;
    state.explored = true;
  }
  function stepYear(d) {
    var y = state.year === null ? (d > 0 ? TS.yr0 : TS.yr1) : state.year + d;
    state.year = Math.max(TS.yr0, Math.min(TS.yr1, y));
    state.explored = true;
  }

  /* ---------- Render ---------- */
  function renderChart() {
    clear(ts);
    var title = sv("title", {}, ts);
    title.textContent = "Test scores of AI systems on various capabilities relative to human performance, 1998 to 2023";

    GRID_VALUES.forEach(function (v) {
      var attrs = { x1: TS.plotX0, y1: tsy(v), x2: TS.plotX1, y2: tsy(v), stroke: v === 0 ? COL.muted : COL.border };
      if (v !== 0) attrs["stroke-dasharray"] = "4 4";
      sv("line", attrs, ts);
      var t = sv("text", { x: TS.plotX0 - 8, y: tsy(v) + 4, "text-anchor": "end", fill: COL.muted }, ts);
      t.textContent = String(v);
    });
    var note = sv("text", { x: TS.plotX0 + 8, y: tsy(0) - 7, fill: COL.muted, "font-size": 11 }, ts);
    note.textContent = "Human performance, as the benchmark, is set to zero";

    X_TICKS.forEach(function (y) {
      var t = sv("text", { x: tsx(y), y: TS.plotY1 + 22, "text-anchor": "middle", fill: COL.muted }, ts);
      t.textContent = String(y);
    });

    shownSeries().forEach(function (s) {
      var dim = emphasis !== null && emphasis !== s.name;
      var g = sv("g", dim ? { opacity: 0.2 } : {}, ts);
      var attrs = {
        points: s.points.map(function (p) { return tsx(p[0]) + "," + tsy(p[1]); }).join(" "),
        fill: "none", stroke: s.color, "stroke-width": emphasis === s.name ? 3 : 2, "stroke-linejoin": "round"
      };
      if (s.dash) attrs["stroke-dasharray"] = s.dash;
      sv("polyline", attrs, g);
      s.points.forEach(function (p) {
        sv("circle", { cx: tsx(p[0]), cy: tsy(p[1]), r: 3.2, fill: s.color, stroke: "#fff", "stroke-width": 1.4 }, g);
      });
    });

    var year = activeYear();
    if (year !== null) {
      var hg = sv("g", { "pointer-events": "none" }, ts);
      sv("line", { x1: tsx(year), y1: TS.plotY0, x2: tsx(year), y2: TS.plotY1, stroke: COL.muted, "stroke-width": 1 }, hg);
      var yl = sv("text", { x: tsx(year), y: TS.plotY0 - 8, "text-anchor": "middle", fill: COL.text, "font-weight": 600 }, hg);
      yl.textContent = String(year);
      rowsFor(year).forEach(function (r) {
        sv("circle", {
          cx: tsx(year), cy: tsy(r.at.v), r: r.at.exact ? 5.5 : 4, fill: r.s.color,
          stroke: "#fff", "stroke-width": 2, opacity: r.at.exact ? 1 : 0.6
        }, hg);
      });
    }
    renderTooltip(year);
  }

  function renderTooltip(year) {
    clear(tip);
    var rows = year === null ? [] : rowsFor(year);
    tip.classList.toggle("is-visible", rows.length > 0);
    if (!rows.length) return;
    tip.appendChild(el("div", "yr", String(year)));
    var table = el("table"), tbody = el("tbody");
    rows.forEach(function (r) {
      var tr = el("tr", r.at.exact ? "" : "approx");
      var td1 = el("td");
      var sw = el("span", "sw");
      sw.style.background = r.s.color;
      td1.appendChild(sw);
      tr.appendChild(td1);
      tr.appendChild(el("td", null, r.s.name));
      tr.appendChild(el("td", "v", (r.at.exact ? "" : "\u2248 ") + r.at.v.toFixed(1)));
      tbody.appendChild(tr);
    });
    table.appendChild(tbody);
    tip.appendChild(table);
    if (rows.some(function (r) { return !r.at.exact; })) {
      tip.appendChild(el("p", "foot", "\u2248 read off the line between two data points"));
    }
    var flip = tsx(year) > (TS.plotX0 + TS.plotX1) / 2;
    tip.style.left = ((tsx(year) / TS.w) * 100) + "%";
    tip.style.transform = flip ? "translateX(calc(-100% - 10px))" : "translateX(10px)";
  }

  // The one legend for this chart. Each entry is a button that hides or shows its
  // series; hovering one brings that line forward in the plot.
  function renderLegend() {
    clear(legend);
    SERIES.forEach(function (s) {
      var off = isHidden(s.name);
      var b = el("button");
      b.type = "button";
      b.setAttribute("aria-pressed", off ? "false" : "true");
      b.setAttribute("aria-label", (off ? "Show " : "Hide ") + s.name);
      var sw = sv("svg", { viewBox: "0 0 26 10", "aria-hidden": "true" });
      sv("line", { x1: 1, y1: 5, x2: 25, y2: 5, stroke: off ? COL.muted : s.color, "stroke-width": 2, "stroke-dasharray": s.dash || "none" }, sw);
      b.appendChild(sw);
      b.appendChild(el("span", null, s.name));
      b.appendChild(el("span", "state", off ? "hidden" : "shown"));
      b.addEventListener("click", function () { toggleSeries(s.name); update(); });
      b.addEventListener("mouseenter", function () { if (!off) { emphasis = s.name; renderChart(); } });
      b.addEventListener("mouseleave", function () { if (emphasis === s.name) { emphasis = null; renderChart(); } });
      b.addEventListener("focus", function () { if (!off) { emphasis = s.name; renderChart(); } });
      b.addEventListener("blur", function () { if (emphasis === s.name) { emphasis = null; renderChart(); } });
      legend.appendChild(b);
    });
  }

  function renderControls() {
    clear(controls);
    controls.appendChild(btn(state.table ? "Hide data table" : "Show data table", function () {
      state.table = !state.table;
      state.explored = true;
      update();
    }, { className: "link" }));
    if (state.hidden.length) controls.appendChild(btn("Show all six", function () { state.hidden = []; update(); }, { className: "link" }));
    var ro = el("span", "readout", state.year === null
      ? "Move the pointer across the chart, or focus it and use the arrow keys, to read a year."
      : "Reading " + state.year + ". Press Escape to clear.");
    ro.setAttribute("aria-live", "polite");
    controls.appendChild(ro);
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
    thead.appendChild(hr);
    table.appendChild(thead);
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

  function renderStatus() {
    statusEl.textContent = state.explored
      ? "Chart explored ✓"
      : "Read a year, hide a series or open the data table to finish.";
  }

  /* ---------- Interaction ---------- */
  ts.addEventListener("pointermove", function (e) {
    var y = yearFromPointer(e.clientX);
    if (y !== hoverYear) {
      hoverYear = y;
      if (y !== null && !state.explored) { state.explored = true; renderStatus(); persist(); }
      renderChart();
    }
  });
  ts.addEventListener("pointerleave", function () {
    if (hoverYear === null) return;
    hoverYear = null;
    renderChart();
  });
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
    var shown = shownSeries().map(function (x) { return x.name; });
    var s = "AI test scores relative to human performance, 1998 to 2023. Showing "
      + shown.length + " of " + SERIES.length + " series (" + shown.join(", ") + ")";
    s += state.hidden.length ? "; hidden: " + state.hidden.join(", ") + "." : ".";
    if (state.year !== null) {
      var rows = rowsFor(state.year);
      s += " Reading " + state.year + ": " + (rows.length
        ? rows.map(function (r) { return r.s.name + " " + r.at.v.toFixed(1) + (r.at.exact ? "" : " (interpolated)"); }).join("; ")
        : "no series has data that year") + ".";
    }
    if (state.table) s += " Data table open.";
    s += state.explored ? " The learner has read values off the chart." : " The learner has not read any values yet.";
    return s;
  }
  function persist() {
    var snap = { hidden: state.hidden.slice(), year: state.year, table: state.table, explored: state.explored };
    if (window.Lens) {
      window.Lens.saveState(snap, summary());
      if (!completed && state.explored) { completed = true; window.Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snap)); } catch (err) {}
    }
  }
  function render() { renderChart(); renderLegend(); renderControls(); renderTable(); renderStatus(); }
  function update() { render(); persist(); }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (Array.isArray(saved.hidden)) {
        state.hidden = saved.hidden.filter(function (n) {
          return SERIES.some(function (s) { return s.name === n; });
        }).slice(0, SERIES.length - 1);
      }
      if (typeof saved.year === "number" && saved.year >= TS.yr0 && saved.year <= TS.yr1) state.year = saved.year;
      if (typeof saved.table === "boolean") state.table = saved.table;
      if (typeof saved.explored === "boolean") state.explored = saved.explored;
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
}());
</script>
</body>
</html>

---
id: '41b66c2f-1cc2-4743-8929-a38feebd78a5'
title: Chip declaration result, 2029
summary_for_tutor: "An interactive reproduction of the AI 2040 verification supplement's two 'Chip declaration result' waffle charts. Each square is 250K H100e. In the January 2029 view the US shows 224M H100e declared and China 26M H100e declared, each with 6 outlined squares (about 1.5M H100e) that could plausibly remain undeclared; in the mid-2029 view the rest of the world joins with 39M H100e declared and every party's plausibly undeclared block shrinks to 2 squares (about 0.5M H100e). Declared compute is drawn as blocks of squares (one block can stand for a single very large datacenter owner) so the learner can hover a block to see how many squares and how much compute it holds, hover or press a party to read its totals, and switch between the two dates. Done means both dates have been viewed."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Chip declaration result, 2029</title>
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), charts "Chip declaration result" (ChipDeclarationResult component, shown with US and China in the Jan 2029 section and with the rest of the world, undeclCells = 2, in the April to May 2029 section). -->
<!-- Data: the party labels, declared totals, block lists, grid sizes, the undeclared cell counts (6 and 2) and the 250K H100e square size are copied from the page's chunk 7228; the block placement algorithm below is a line-for-line port of the component's layout function, so the picture is the same as the source. Nothing is read by eye. -->
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
  .views { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 10px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  button.is-seen::after { content: " ✓"; color: var(--muted); }
  .layout { display: grid; grid-template-columns: minmax(0, 1fr) 240px; gap: 16px; align-items: start; }
  .chartbox { overflow-x: auto; }
  .chart { width: 100%; min-width: 520px; height: auto; display: block; }
  .chart text { font-family: var(--font-ui); }
  .chart .blk { cursor: pointer; }
  .chart .blk.is-active { stroke: #b87018; stroke-width: 3; }
  .chart .party.is-active .label { fill: var(--accent); }
  .side { display: flex; flex-direction: column; gap: 10px; }
  .detail { border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 10px 12px; min-height: 110px; }
  .detail h2 { margin-bottom: 4px; }
  .detail p { margin: 4px 0; }
  .detail .n { font-variant-numeric: tabular-nums; }
  .parties { display: flex; flex-wrap: wrap; gap: 6px; }
  .legend { font-size: 12px; color: var(--muted); display: flex; flex-wrap: wrap; gap: 4px 16px; margin-top: 8px; }
  .legend .k { display: inline-flex; align-items: center; gap: 6px; }
  .legend .sq { display: inline-block; width: 12px; height: 12px; background: var(--text); }
  .legend .sq.cn { background: var(--accent); }
  .legend .sq.row { background: repeating-linear-gradient(45deg, #1a1a1a 0 2px, #fff 2px 5px); }
  .legend .sq.un { background: none; border: 1.5px solid var(--text); }
  .status { font-size: 12px; color: var(--muted); margin-top: 8px; }
  .status.is-done { color: var(--text); font-weight: 500; }
  @media (max-width: 700px) { .layout { grid-template-columns: 1fr; } body { padding: 10px; } }
</style>
</head>
<body>
<p class="eyebrow">Interactive chart</p>
<h1>Chip declaration result, 2029</h1>
<p class="lede">Declared compute after the mutual chip declaration, against what each side could plausibly still be hiding. One square is 250K H100e. Switch the date, then hover a block or a party.</p>

<div class="card">
  <div class="views" id="views" role="group" aria-label="Date"></div>
  <div class="layout">
    <div class="chartbox"><svg id="chart" class="chart" role="img" aria-label="Waffle chart of declared and plausibly undeclared compute by party"></svg></div>
    <div class="side">
      <div class="detail" id="detail" aria-live="polite"></div>
      <div class="parties" id="parties" aria-label="Parties"></div>
    </div>
  </div>
  <div class="legend" id="legend"></div>
  <p class="status" id="status"></p>
</div>

<script>
(function () {
  var SQUARE_K = 250; // K H100e per square
  var US = { key: "us", label: "US", declaredM: 224, fill: "#1a1a1a", base: "#1a1a1a", blocks: [{ w: 7, h: 8, count: 1 }, { w: 4, h: 8, count: 1 }, { w: 4, h: 6, count: 1 }, { w: 4, h: 5, count: 1 }, { w: 4, h: 4, count: 5 }, { w: 3, h: 4, count: 10 }, { w: 2, h: 4, count: 28 }, { w: 2, h: 2, count: 30 }, { w: 1, h: 2, count: 30 }, { w: 1, h: 1, count: 144 }], rectCols: 60, rectRows: 15 };
  var CN = { key: "cn", label: "China", declaredM: 26, fill: "#b87018", base: "#b87018", blocks: [{ w: 4, h: 4, count: 1 }, { w: 3, h: 4, count: 1 }, { w: 2, h: 4, count: 2 }, { w: 2, h: 2, count: 2 }, { w: 1, h: 2, count: 4 }, { w: 1, h: 1, count: 30 }], rectCols: 15, rectRows: 7 };
  var ROW = { key: "row", label: "RoW", longLabel: "Rest of world", declaredM: 39, fill: "url(#decl-ink-bars)", base: "#1a1a1a", blocks: [{ w: 4, h: 5, count: 1 }, { w: 3, h: 4, count: 1 }, { w: 2, h: 4, count: 2 }, { w: 2, h: 2, count: 6 }, { w: 1, h: 2, count: 8 }, { w: 1, h: 1, count: 37 }], rectCols: 23, rectRows: 7 };
  var VIEWS = [
    { id: "jan", label: "January 2029: US and China", sides: [US, CN], undeclCells: 6 },
    { id: "mid", label: "Mid 2029: with the rest of the world", sides: [US, CN, ROW], undeclCells: 2 }
  ];
  var NS = "http://www.w3.org/2000/svg";
  var CELL = 18;

  // Line-for-line port of the source component's layout function.
  function layout(blocks, cols, rows, undeclCells) {
    var grid = [], r, c;
    for (r = 0; r < rows; r++) { grid.push([]); for (c = 0; c < cols; c++) grid[r].push(false); }
    var placed = [];
    function canPlace(x, y, w, h) {
      if (x + w > cols || y + h > rows) return false;
      for (var yy = y; yy < y + h; yy++) for (var xx = x; xx < x + w; xx++) if (grid[yy][xx]) return false;
      return true;
    }
    function mark(x, y, w, h) { for (var yy = y; yy < y + h; yy++) for (var xx = x; xx < x + w; xx++) grid[yy][xx] = true; }
    var list = [];
    blocks.filter(function (b) { return b.w * b.h > 1; }).sort(function (a, b) { return b.w * b.h - a.w * a.h; }).forEach(function (b) {
      for (var i = 0; i < b.count; i++) list.push({ w: b.w, h: b.h });
    });
    list.forEach(function (b) {
      outer: for (var o = 0; o <= rows - b.h; o++) for (var l = 0; l <= cols - b.w; l++) if (canPlace(l, o, b.w, b.h)) {
        placed.push({ col: l, row: o, w: b.w, h: b.h, kind: "full" });
        mark(l, o, b.w, b.h);
        break outer;
      }
    });
    var singles = [];
    for (r = 0; r < rows; r++) for (c = 0; c < cols; c++) if (!grid[r][c]) {
      placed.push({ col: c, row: r, w: 1, h: 1, kind: "full" });
      grid[r][c] = true;
      singles.push(placed.length - 1);
    }
    singles.slice(-undeclCells).forEach(function (idx) { placed[idx].kind = "undecl"; });
    return { placed: placed, rows: rows };
  }

  var state = { view: "jan", party: null, block: null, seen: {} };
  var completed = false;

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
  function fmtM(squares) { var m = squares * SQUARE_K / 1000; return (Math.round(m * 100) / 100) + "M H100e"; }
  function currentView() { for (var i = 0; i < VIEWS.length; i++) if (VIEWS[i].id === state.view) return VIEWS[i]; return VIEWS[0]; }

  var layouts = {};
  var partyGroups = {};
  var blockEls = {};
  function drawChart() {
    while (svg.firstChild) svg.removeChild(svg.firstChild);
    partyGroups = {}; blockEls = {};
    var view = currentView();
    var defs = el("defs", {});
    var pat = el("pattern", { id: "decl-ink-bars", width: 9, height: 9, patternUnits: "userSpaceOnUse", patternTransform: "rotate(45)" });
    pat.appendChild(el("rect", { width: 9, height: 9, fill: "#ffffff" }));
    pat.appendChild(el("line", { x1: 0, y1: 0, x2: 0, y2: 9, stroke: "#1a1a1a", "stroke-width": 3.6 }));
    defs.appendChild(pat);
    svg.appendChild(defs);
    var entries = view.sides.map(function (side) { return { side: side, layout: layout(side.blocks, side.rectCols, side.rectRows, view.undeclCells) }; });
    layouts = {};
    entries.forEach(function (e) { layouts[e.side.key] = e.layout; });
    var heights = entries.map(function (e) { return CELL * e.layout.rows; });
    var total = 24 + heights.reduce(function (a, b) { return a + b; }, 0) + (entries.length - 1) * 50 + 100;
    svg.setAttribute("viewBox", "0 0 1400 " + total);
    entries.forEach(function (e, idx) {
      var top = 24 + heights.slice(0, idx).reduce(function (a, b) { return a + b; }, 0) + 50 * idx;
      var side = e.side;
      var g = el("g", { "class": "party" });
      var mid = top + CELL * e.layout.rows / 2;
      g.appendChild(el("text", { "class": "label", x: 208, y: mid - 36, "text-anchor": "end", "font-size": 56, "font-weight": 700, fill: "#1a1a1a" }, side.label));
      g.appendChild(el("text", { x: 208, y: mid + 18, "text-anchor": "end", "font-size": 32, "font-style": "italic", fill: "#1a1a1a" }, side.declaredM + "M H100e"));
      g.appendChild(el("text", { x: 208, y: mid + 54, "text-anchor": "end", "font-size": 32, "font-style": "italic", fill: "#1a1a1a" }, "declared"));
      e.layout.placed.forEach(function (b, bi) {
        var rect = el("rect", {
          "class": "blk", x: 240 + CELL * b.col, y: top + CELL * b.row, width: CELL * b.w - 2, height: CELL * b.h - 2,
          fill: b.kind === "full" ? side.fill : "none", stroke: b.kind === "undecl" ? side.base : "none", "stroke-width": b.kind === "undecl" ? 1.5 : 0
        });
        rect.addEventListener("pointerenter", function () { hover(side.key, bi); });
        rect.addEventListener("click", function () { hover(side.key, bi); persist(); });
        g.appendChild(rect);
        blockEls[side.key + ":" + bi] = rect;
      });
      g.addEventListener("pointerleave", function () { state.block = null; renderSide(); });
      svg.appendChild(g);
      partyGroups[side.key] = g;
    });
    var ly = total - 30;
    svg.appendChild(el("rect", { x: 240, y: ly - 12, width: 16, height: 16, fill: "#1a1a1a" }));
    svg.appendChild(el("text", { x: 266, y: ly, "font-size": 26, fill: "#1a1a1a" }, "declared"));
    svg.appendChild(el("rect", { x: 440, y: ly - 12, width: 16, height: 16, fill: "none", stroke: "#1a1a1a", "stroke-width": 1.5 }));
    svg.appendChild(el("text", { x: 466, y: ly, "font-size": 26, fill: "#1a1a1a" }, "plausibly undeclared"));
    svg.appendChild(el("text", { x: 830, y: ly, "font-size": 26, fill: "#1a1a1a" }, "1 square = " + SQUARE_K + "K H100e"));
  }

  var detail = document.getElementById("detail");
  var partiesEl = document.getElementById("parties");
  var viewsEl = document.getElementById("views");
  var legendEl = document.getElementById("legend");
  var statusEl = document.getElementById("status");

  function counts(sideKey) {
    var lay = layouts[sideKey];
    var full = 0, undecl = 0, blocks = 0;
    lay.placed.forEach(function (b) { if (b.kind === "full") { full += b.w * b.h; blocks++; } else undecl += b.w * b.h; });
    return { full: full, undecl: undecl, blocks: blocks };
  }
  function isDone() { return !!(state.seen.jan && state.seen.mid); }

  function renderSide() {
    var view = currentView();
    detail.textContent = "";
    var side = null;
    view.sides.forEach(function (s) { if (s.key === state.party) side = s; });
    if (!side) {
      detail.appendChild(h("h2", null, view.label));
      detail.appendChild(h("p", null, "Hover a block of squares, or press a party, to read what it stands for. One square is 250K H100e."));
    } else {
      var c = counts(side.key);
      detail.appendChild(h("h2", null, side.longLabel || side.label));
      detail.appendChild(h("p", "n", side.declaredM + "M H100e declared, drawn as " + c.full + " squares in " + c.blocks + " blocks."));
      detail.appendChild(h("p", "n", "Plausibly undeclared: " + c.undecl + " outlined squares, about " + fmtM(c.undecl) + "."));
      if (state.block !== null && layouts[side.key] && layouts[side.key].placed[state.block]) {
        var b = layouts[side.key].placed[state.block];
        var n = b.w * b.h;
        detail.appendChild(h("p", "n", b.kind === "undecl" ? "This outlined square: one plausibly undeclared square, " + SQUARE_K + "K H100e." : "This block: " + b.w + " × " + b.h + " = " + n + (n === 1 ? " square, " : " squares, ") + fmtM(n) + " declared."));
      }
    }
    partiesEl.textContent = "";
    view.sides.forEach(function (s) {
      var b = h("button", null, s.longLabel || s.label);
      b.type = "button";
      b.classList.toggle("is-active", s.key === state.party);
      b.setAttribute("aria-pressed", s.key === state.party ? "true" : "false");
      b.addEventListener("click", function () { state.party = s.key; state.block = null; renderSide(); persist(); });
      partiesEl.appendChild(b);
    });
    var vb = viewsEl.querySelectorAll("button");
    for (var i = 0; i < vb.length; i++) {
      vb[i].classList.toggle("is-active", vb[i].dataset.view === state.view);
      vb[i].classList.toggle("is-seen", !!state.seen[vb[i].dataset.view]);
      vb[i].setAttribute("aria-pressed", vb[i].dataset.view === state.view ? "true" : "false");
    }
    for (var k in partyGroups) partyGroups[k].classList.toggle("is-active", k === state.party);
    for (var bk in blockEls) blockEls[bk].classList.toggle("is-active", state.party !== null && bk === state.party + ":" + state.block);
    legendEl.textContent = "";
    function key(cls, text) { var kk = h("span", "k"); kk.appendChild(h("span", "sq " + cls)); kk.appendChild(h("span", null, text)); legendEl.appendChild(kk); }
    key("", "US declared");
    key("cn", "China declared");
    if (view.sides.length > 2) key("row", "Rest of world declared");
    key("un", "plausibly undeclared");
    statusEl.textContent = isDone() ? "Both dates viewed. Compare the outlined squares: 6 per side in January, 2 per side by mid-year." : "View both dates to compare how much could plausibly stay hidden before and after third countries join.";
    statusEl.classList.toggle("is-done", isDone());
  }

  function summary() {
    var view = currentView();
    var parts = view.sides.map(function (s) { var c = counts(s.key); return (s.longLabel || s.label) + " " + s.declaredM + "M H100e declared, " + c.undecl + " squares (about " + fmtM(c.undecl) + ") plausibly undeclared"; });
    var sel = state.party ? " Selected party: " + state.party + "." : "";
    return "Chip declaration chart, showing " + view.label + ". One square = 250K H100e. " + parts.join("; ") + "." + sel + " Dates viewed: " + Object.keys(state.seen).filter(function (k) { return state.seen[k]; }).join(", ") + ".";
  }

  function persist() {
    var json = { view: state.view, party: state.party, seen: state.seen };
    if (window.Lens) {
      Lens.saveState(json, summary());
      if (isDone() && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("ai-2040-chip-declaration", JSON.stringify(json)); } catch (e) {}
    }
  }

  function hover(partyKey, blockIndex) {
    state.party = partyKey;
    state.block = blockIndex;
    renderSide();
  }
  function setView(id) {
    state.view = id;
    state.seen[id] = true;
    state.block = null;
    var exists = currentView().sides.some(function (s) { return s.key === state.party; });
    if (!exists) state.party = null;
    drawChart();
    renderSide();
    persist();
  }

  VIEWS.forEach(function (v) {
    var b = h("button", null, v.label);
    b.type = "button";
    b.dataset.view = v.id;
    b.addEventListener("click", function () { setView(v.id); });
    viewsEl.appendChild(b);
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (saved.view === "jan" || saved.view === "mid") state.view = saved.view;
      if (typeof saved.party === "string") state.party = saved.party;
      if (saved.seen && typeof saved.seen === "object") { state.seen = {}; for (var k in saved.seen) if (saved.seen[k]) state.seen[k] = true; }
    }
    completed = !!(meta && meta.completed);
    state.seen[state.view] = true;
    drawChart();
    renderSide();
  }

  state.seen[state.view] = true;
  drawChart();
  renderSide();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    try { var raw = localStorage.getItem("ai-2040-chip-declaration"); if (raw) hydrate(JSON.parse(raw), null); } catch (e) {}
  }
})();
</script>
</body>
</html>

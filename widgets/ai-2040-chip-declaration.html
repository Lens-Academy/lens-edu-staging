---
id: '41b66c2f-1cc2-4743-8929-a38feebd78a5'
title: Chip declaration result, 2029
summary_for_tutor: "A static waffle chart of the chip declaration result in January 2029, with two parties: the US, which declared 224M H100e, and China, which declared 26M H100e. Each square stands for 250K H100e, and the declared compute of each party is drawn as blocks of filled squares, so the size of each party's grid is proportional to what it declared. At the end of each party's grid sit 6 outlined squares standing for compute that could plausibly remain undeclared, about 1.5M H100e per party, which is tiny next to either declared total. A legend inside the chart names the filled and the outlined squares and states the size of one square."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Chip declaration result, 2029</title>
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), figure "Chip declaration result" in the January 2029 section (ChipDeclarationResult component, US and China, undeclCells = 6). -->
<!-- Data: party labels, declared totals, block lists, grid sizes, the undeclared cell count and the 250K H100e square size are copied from the page's chunk 7228; the block placement below is a line-for-line port of the component's layout function. Nothing is read by eye. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --accent: #b87018;
    --font-ui: "DM Sans", Arial, sans-serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .chartbox { overflow-x: auto; }
  .chart { width: 100%; min-width: 520px; height: auto; display: block; }
  .chart text { font-family: var(--font-ui); fill: var(--text); }
  .chart .blk { stroke: none; }
  .chart .blk.us { fill: var(--text); }
  .chart .blk.cn { fill: var(--accent); }
  .chart .blk.un { fill: none; stroke-width: 1.5; }
  .chart .blk.un.us { stroke: var(--text); }
  .chart .blk.un.cn { stroke: var(--accent); }
  .chart .sw { fill: var(--text); }
  .chart .sw.out { fill: none; stroke: var(--text); stroke-width: 1.5; }
  @media (max-width: 700px) { body { padding: 10px; } }
</style>
</head>
<body>
<div class="chartbox"><svg id="chart" class="chart" role="img" aria-label="Waffle chart of declared and plausibly undeclared compute for the US and China in January 2029"></svg></div>

<script>
(function () {
  var SQUARE_K = 250; // K H100e per square
  var UNDECL_CELLS = 6;
  var SIDES = [
    { key: "us", label: "US", declaredM: 224, blocks: [{ w: 7, h: 8, count: 1 }, { w: 4, h: 8, count: 1 }, { w: 4, h: 6, count: 1 }, { w: 4, h: 5, count: 1 }, { w: 4, h: 4, count: 5 }, { w: 3, h: 4, count: 10 }, { w: 2, h: 4, count: 28 }, { w: 2, h: 2, count: 30 }, { w: 1, h: 2, count: 30 }, { w: 1, h: 1, count: 144 }], rectCols: 60, rectRows: 15 },
    { key: "cn", label: "China", declaredM: 26, blocks: [{ w: 4, h: 4, count: 1 }, { w: 3, h: 4, count: 1 }, { w: 2, h: 4, count: 2 }, { w: 2, h: 2, count: 2 }, { w: 1, h: 2, count: 4 }, { w: 1, h: 1, count: 30 }], rectCols: 15, rectRows: 7 }
  ];
  var NS = "http://www.w3.org/2000/svg";
  var CELL = 18;

  // Line-for-line port of the component's layout function.
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

  var svg = document.getElementById("chart");
  function el(tag, attrs, text) {
    var n = document.createElementNS(NS, tag);
    for (var k in attrs) n.setAttribute(k, attrs[k]);
    if (text !== undefined) n.textContent = text;
    return n;
  }

  var entries = SIDES.map(function (side) { return { side: side, layout: layout(side.blocks, side.rectCols, side.rectRows, UNDECL_CELLS) }; });
  var heights = entries.map(function (e) { return CELL * e.layout.rows; });
  var total = 24 + heights.reduce(function (a, b) { return a + b; }, 0) + (entries.length - 1) * 50 + 100;
  svg.setAttribute("viewBox", "0 0 1400 " + total);
  entries.forEach(function (e, idx) {
    var top = 24 + heights.slice(0, idx).reduce(function (a, b) { return a + b; }, 0) + 50 * idx;
    var side = e.side;
    var g = el("g", { "class": "party" });
    var mid = top + CELL * e.layout.rows / 2;
    g.appendChild(el("text", { "class": "label", x: 208, y: mid - 36, "text-anchor": "end", "font-size": 56, "font-weight": 700 }, side.label));
    g.appendChild(el("text", { x: 208, y: mid + 18, "text-anchor": "end", "font-size": 32, "font-style": "italic" }, side.declaredM + "M H100e"));
    g.appendChild(el("text", { x: 208, y: mid + 54, "text-anchor": "end", "font-size": 32, "font-style": "italic" }, "declared"));
    e.layout.placed.forEach(function (b) {
      g.appendChild(el("rect", {
        "class": "blk " + side.key + (b.kind === "undecl" ? " un" : ""),
        x: 240 + CELL * b.col, y: top + CELL * b.row, width: CELL * b.w - 2, height: CELL * b.h - 2
      }));
    });
    svg.appendChild(g);
  });
  var ly = total - 30;
  svg.appendChild(el("rect", { "class": "sw", x: 240, y: ly - 12, width: 16, height: 16 }));
  svg.appendChild(el("text", { x: 266, y: ly, "font-size": 26 }, "declared"));
  svg.appendChild(el("rect", { "class": "sw out", x: 440, y: ly - 12, width: 16, height: 16 }));
  svg.appendChild(el("text", { x: 466, y: ly, "font-size": 26 }, "plausibly undeclared"));
  svg.appendChild(el("text", { x: 830, y: ly, "font-size": 26 }, "1 square = " + SQUARE_K + "K H100e"));
})();
</script>
</body>
</html>


---
id: 'a0e30f44-c25e-4d26-95a6-a841800fb993'
title: The control graph
summary_for_tutor: "The learner labels the four regions of the control graph. The axes are how incriminating each of the model's actions is (vertical) against how many actions the model needs to cause a catastrophe (horizontal). Four labels (High-stakes, Low-stakes, Trivially solved with random auditing, Probably hopeless?) sit in a tray; the learner picks one, clicks the region it belongs to, and presses Check once all four are placed. The check marks each region with a tick or a cross, draws a dashed arrow from every misplaced label to the region it belongs in, reveals the inverse-correlation diagonal, and gives a count. After the check, clicking a region shows one line on why that region is what it is. The definition of high stakes and the argument for the diagonal are on the page around the widget, before and after it. Nothing is graded; completion fires on the first check. If a learner asks where some scenario sits, ask them the two axis questions rather than answering: how incriminating is each action, and how many actions does the catastrophe take?"
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
[hidden] { display: none !important; }
body { margin: 0; padding: 0; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.card { border: 1px solid var(--border); border-radius: 8px; overflow: hidden; background: var(--bg); }
.body { padding: 16px; }
.instr { margin: 0 0 10px; color: var(--muted); font-size: 13px; }
.tray { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 12px; min-height: 34px; }
.tray p { margin: 0; color: var(--muted); font-size: 12px; align-self: center; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px;
  background: #fff; padding: 6px 12px; cursor: pointer; }
button:hover:not(:disabled) { background: var(--page); border-color: var(--muted); }
button:disabled { opacity: 0.45; cursor: default; }
button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
.chip[aria-pressed="true"] { border-color: var(--accent); background: var(--page); box-shadow: inset 0 0 0 1px var(--accent); }
svg.graph { width: 100%; height: auto; display: block; }
svg.graph text.rlabel { font-size: 11px; }
svg.graph text.axis { font-size: 12px; }
svg.graph #l-diag text { font-size: 10px; }
@media (max-width: 560px) {
  svg.graph text.rlabel { font-size: 15px; }
  svg.graph text.axis { font-size: 15px; }
  svg.graph #l-diag text { font-size: 13px; }
}
svg.graph g.region { cursor: pointer; }
svg.graph g.region:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
svg.graph g.region:hover polygon.hit { stroke: var(--muted); }
svg.graph.picking g.region polygon.hit { stroke: var(--accent); stroke-dasharray: 5 4; }
.status { margin: 10px 0 0; font-weight: 500; }
.why { margin: 4px 0 0; color: var(--muted); }
.controls { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; margin-top: 12px; }
.reset { font-size: 12px; padding: 4px 10px; color: var(--muted); }
@media (max-width: 420px) {
  .body { padding: 12px; }
}
</style>
</head>
<body>
<!-- Ported from XLab's AI Control curriculum, lesson "What is High Stakes?" (Module 4). -->
<div class="card">
  <div class="body">
    <p class="instr">Pick a label, then click the region of the graph where it belongs.</p>
    <div class="tray" id="tray" role="group" aria-label="Labels to place"></div>
    <svg viewBox="0 0 560 400" class="graph" id="graph" role="group" aria-label="The control graph: how incriminating each action is, against how many actions are needed to cause a catastrophe. Four unlabelled regions to name.">
      <defs>
        <marker id="axis-arrow" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
          <path d="M0,0 L8,4 L0,8 z" fill="#5a5a5a"></path>
        </marker>
        <marker id="diag-arrow" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
          <path d="M0,0 L8,4 L0,8 z" fill="#b87018"></path>
        </marker>
        <marker id="fix-arrow" viewBox="0 0 8 8" refX="7" refY="4" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
          <path d="M0,0 L8,4 L0,8 z" fill="#b87018"></path>
        </marker>
      </defs>
      <g id="regions"></g>
      <g id="l-diag" opacity="0" style="transition: opacity 0.4s">
        <line x1="457.33" y1="244.22" x2="151.2" y2="91.44" stroke="#b87018" stroke-width="2" stroke-dasharray="6 5" marker-end="url(#diag-arrow)"></line>
        <text x="330.4" y="138.67" text-anchor="middle" fill="#9a5c10" font-weight="600">
          <tspan x="330.4" dy="0">fewer actions &#8594;</tspan><tspan x="330.4" dy="13">bigger, more incriminating actions</tspan>
        </text>
      </g>
      <g id="fixes"></g>
      <line x1="72" y1="322" x2="72" y2="18" stroke="#5a5a5a" stroke-width="1.75" marker-end="url(#axis-arrow)"></line>
      <line x1="72" y1="334" x2="542" y2="334" stroke="#5a5a5a" stroke-width="1.75" marker-end="url(#axis-arrow)"></line>
      <text class="axis" x="62" y="172" transform="rotate(-90 62 172)" text-anchor="middle" fill="#1a1a1a" font-weight="500">How incriminating is each action?</text>
      <text class="axis" x="308" y="356" text-anchor="middle" fill="#1a1a1a" font-weight="500">Number of actions to cause catastrophe</text>
    </svg>

    <p class="status" id="status"></p>
    <p class="why" id="why" hidden></p>

    <div class="controls">
      <button type="button" id="check" disabled>Check</button>
      <button type="button" class="reset" id="reset">Reset</button>
    </div>
  </div>
</div>

<script>
(function () {
  var NS = "http://www.w3.org/2000/svg";

  var REGIONS = [
    {
      id: "high",
      points: "84,22 196,22 420,122 196,222 84,172",
      fill: "#e9c893",
      lx: 190, ly: 120,
      aria: "Left band: few actions needed, each fairly incriminating",
      why: "High stakes is what takes the least amount of actions to produce a catastrophically threatening occurrence: only a few actions are needed."
    },
    {
      id: "low",
      points: "420,122 532,172 532,322 420,322 196,222",
      fill: "#ddd8cf",
      lx: 432, ly: 248,
      aria: "Right band: many actions needed, each barely incriminating",
      why: "Lots of actions are needed to cause a catastrophe, so no single action decides the outcome."
    },
    {
      id: "tr",
      points: "196,22 532,22 532,172",
      fill: "#eeebe5",
      lx: 452, ly: 60,
      aria: "Top right corner: many actions needed and each one highly incriminating",
      why: "Many actions needed and each one highly incriminating, so it is trivially solved with random auditing."
    },
    {
      id: "bl",
      points: "84,172 84,322 420,322",
      fill: "#eeebe5",
      lx: 200, ly: 284,
      aria: "Bottom left corner: few actions needed and each one barely incriminating",
      why: "A catastrophe in a few barely-incriminating actions. Probably hopeless?"
    }
  ];

  var LABELS = [
    { id: "low", text: "Low-stakes" },
    { id: "tr", text: "Trivially solved with random auditing" },
    { id: "bl", text: "Probably hopeless?" },
    { id: "high", text: "High-stakes" }
  ];

  var placed = {};
  var picked = null;
  var checked = false;

  var graph = document.getElementById("graph");
  var regionsLayer = document.getElementById("regions");
  var fixesLayer = document.getElementById("fixes");
  var diag = document.getElementById("l-diag");
  var tray = document.getElementById("tray");
  var statusLine = document.getElementById("status");
  var whyLine = document.getElementById("why");
  var checkBtn = document.getElementById("check");
  var resetBtn = document.getElementById("reset");

  function labelText(id) {
    for (var i = 0; i < LABELS.length; i++) { if (LABELS[i].id === id) { return LABELS[i].text; } }
    return "";
  }

  function regionById(id) {
    for (var i = 0; i < REGIONS.length; i++) { if (REGIONS[i].id === id) { return REGIONS[i]; } }
    return null;
  }

  function narrow() {
    return window.innerWidth > 0 && window.innerWidth <= 560;
  }

  function wrap(text, max) {
    var words = text.split(" ");
    var lines = [];
    var cur = "";
    words.forEach(function (w) {
      if (!cur) { cur = w; }
      else if ((cur + " " + w).length <= max) { cur = cur + " " + w; }
      else { lines.push(cur); cur = w; }
    });
    if (cur) { lines.push(cur); }
    return lines;
  }

  var regionNodes = {};

  REGIONS.forEach(function (r) {
    var g = document.createElementNS(NS, "g");
    g.setAttribute("class", "region");
    g.setAttribute("tabindex", "0");
    g.setAttribute("role", "button");

    var poly = document.createElementNS(NS, "polygon");
    poly.setAttribute("points", r.points);
    poly.setAttribute("fill", r.fill);
    poly.setAttribute("fill-opacity", "0.7");
    poly.setAttribute("stroke", "#ffffff");
    poly.setAttribute("stroke-width", "2");
    g.appendChild(poly);

    var hit = document.createElementNS(NS, "polygon");
    hit.setAttribute("class", "hit");
    hit.setAttribute("points", r.points);
    hit.setAttribute("fill", "transparent");
    hit.setAttribute("stroke", "transparent");
    hit.setAttribute("stroke-width", "2");
    g.appendChild(hit);

    var text = document.createElementNS(NS, "text");
    text.setAttribute("class", "rlabel");
    text.setAttribute("text-anchor", "middle");
    text.setAttribute("font-weight", "600");
    text.setAttribute("pointer-events", "none");
    g.appendChild(text);

    g.addEventListener("click", function () { hitRegion(r.id); });
    g.addEventListener("keydown", function (ev) {
      if (ev.key === "Enter" || ev.key === " " || ev.key === "Spacebar") {
        ev.preventDefault();
        hitRegion(r.id);
      }
    });

    regionsLayer.appendChild(g);
    regionNodes[r.id] = { g: g, poly: poly, text: text };
  });

  function hitRegion(regionId) {
    if (checked) {
      var r = regionById(regionId);
      whyLine.textContent = r.why;
      whyLine.hidden = false;
      return;
    }
    if (picked) {
      REGIONS.forEach(function (other) {
        if (placed[other.id] === picked) { delete placed[other.id]; }
      });
      placed[regionId] = picked;
      picked = null;
      render();
      save();
      return;
    }
    if (placed[regionId]) {
      delete placed[regionId];
      render();
      save();
    }
  }

  function pick(labelId) {
    picked = picked === labelId ? null : labelId;
    render();
  }

  function placedCount() {
    var n = 0;
    for (var k in placed) { if (Object.prototype.hasOwnProperty.call(placed, k)) { n++; } }
    return n;
  }

  function correctCount() {
    var n = 0;
    REGIONS.forEach(function (r) { if (placed[r.id] === r.id) { n++; } });
    return n;
  }

  function usedLabels() {
    var used = {};
    for (var k in placed) { if (Object.prototype.hasOwnProperty.call(placed, k)) { used[placed[k]] = true; } }
    return used;
  }

  function renderTray() {
    while (tray.firstChild) { tray.removeChild(tray.firstChild); }
    var used = usedLabels();
    var any = false;
    LABELS.forEach(function (l) {
      if (used[l.id]) { return; }
      any = true;
      var b = document.createElement("button");
      b.type = "button";
      b.className = "chip";
      b.textContent = l.text;
      b.setAttribute("aria-pressed", picked === l.id ? "true" : "false");
      b.disabled = checked;
      b.addEventListener("click", function () { pick(l.id); });
      tray.appendChild(b);
    });
    if (!any) {
      var p = document.createElement("p");
      p.textContent = checked ? "Click a region to see why it is what it is." : "All four placed. Check your answer.";
      tray.appendChild(p);
    }
  }

  function renderRegion(r) {
    var node = regionNodes[r.id];
    var text = node.text;
    while (text.firstChild) { text.removeChild(text.firstChild); }

    var here = placed[r.id];
    var right = checked && here === r.id;
    var wrong = checked && here && here !== r.id;

    node.poly.setAttribute("fill-opacity", wrong ? "0.45" : (here ? "0.95" : "0.7"));
    node.g.setAttribute("aria-label", r.aria + (here ? ", labelled " + labelText(here) : ", no label yet"));

    if (!here) { return; }

    var mark = right ? "✓ " : (wrong ? "✗ " : "");
    var lines = wrap(mark + labelText(here), 20);
    text.setAttribute("fill", wrong ? "#5a5a5a" : (right ? "#9a5c10" : "#1a1a1a"));
    var lh = narrow() ? 16 : 12;
    var y0 = r.ly - (lines.length - 1) * (lh / 2);
    lines.forEach(function (line, i) {
      var t = document.createElementNS(NS, "tspan");
      t.setAttribute("x", String(r.lx));
      t.setAttribute("y", String(y0 + i * lh));
      t.textContent = line;
      text.appendChild(t);
    });
  }

  function renderFixes() {
    while (fixesLayer.firstChild) { fixesLayer.removeChild(fixesLayer.firstChild); }
    if (!checked) { return; }
    REGIONS.forEach(function (r) {
      var here = placed[r.id];
      if (!here || here === r.id) { return; }
      var home = regionById(here);
      var x1 = r.lx;
      var y1 = r.ly + 8;
      var x2 = home.lx;
      var y2 = home.ly + 8;
      var dx = x2 - x1;
      var dy = y2 - y1;
      var len = Math.sqrt(dx * dx + dy * dy) || 1;
      var ux = dx / len;
      var uy = dy / len;
      x1 += ux * 12 - uy * 7;
      y1 += uy * 12 + ux * 7;
      x2 -= ux * 16 + uy * 7;
      y2 -= uy * 16 - ux * 7;
      var line = document.createElementNS(NS, "line");
      line.setAttribute("x1", String(Math.round(x1 * 10) / 10));
      line.setAttribute("y1", String(Math.round(y1 * 10) / 10));
      line.setAttribute("x2", String(Math.round(x2 * 10) / 10));
      line.setAttribute("y2", String(Math.round(y2 * 10) / 10));
      line.setAttribute("stroke", "#b87018");
      line.setAttribute("stroke-width", "1.5");
      line.setAttribute("stroke-dasharray", "5 4");
      line.setAttribute("marker-end", "url(#fix-arrow)");
      fixesLayer.appendChild(line);
    });
  }

  function render() {
    REGIONS.forEach(renderRegion);
    renderFixes();
    renderTray();
    diag.setAttribute("opacity", checked ? "1" : "0");
    if (picked && !checked) { graph.classList.add("picking"); }
    else { graph.classList.remove("picking"); }

    checkBtn.disabled = checked || placedCount() < REGIONS.length;
    checkBtn.textContent = checked ? "Checked" : "Check";

    if (checked) {
      statusLine.textContent = correctCount() + " of " + REGIONS.length + " labels are in the right region.";
    } else if (picked) {
      statusLine.textContent = "Now click the region where " + labelText(picked) + " belongs.";
    } else if (placedCount() > 0) {
      statusLine.textContent = placedCount() + " of " + REGIONS.length + " placed. Click a placed label to take it back.";
    } else {
      statusLine.textContent = "";
    }
    if (!checked) { whyLine.hidden = true; whyLine.textContent = ""; }
  }

  function summary() {
    var parts = [];
    REGIONS.forEach(function (r) {
      var here = placed[r.id];
      parts.push(r.aria.split(":")[0] + ": " + (here ? labelText(here) : "empty"));
    });
    var head = checked
      ? "Control graph checked: " + correctCount() + " of " + REGIONS.length + " labels in the right region. "
      : "Control graph in progress, " + placedCount() + " of " + REGIONS.length + " labels placed. ";
    return head + parts.join("; ") + ".";
  }

  function save() {
    if (!window.Lens) { return; }
    Lens.saveState({ placed: placed, checked: checked }, summary());
  }

  function doCheck() {
    if (checked || placedCount() < REGIONS.length) { return; }
    checked = true;
    picked = null;
    render();
    save();
    if (window.Lens) { Lens.complete(); }
  }

  function doReset() {
    placed = {};
    picked = null;
    checked = false;
    render();
    save();
  }

  checkBtn.addEventListener("click", doCheck);
  resetBtn.addEventListener("click", doReset);
  window.addEventListener("resize", function () { REGIONS.forEach(renderRegion); });

  if (window.Lens && Lens.onState) {
    Lens.onState(function (state) {
      placed = {};
      checked = false;
      if (state && state.placed && typeof state.placed === "object") {
        REGIONS.forEach(function (r) {
          var v = state.placed[r.id];
          if (typeof v === "string" && labelText(v)) { placed[r.id] = v; }
        });
        checked = state.checked === true && placedCount() === REGIONS.length;
      }
      render();
    });
  }

  render();
})();
</script>
</body>
</html>


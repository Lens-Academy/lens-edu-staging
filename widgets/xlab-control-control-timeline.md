---
id: 'e1433365-dadf-4a34-b627-0e03adf74f76'
title: The control timeline
summary_for_tutor: "XLab's control-timeline figure, shown in the reading right after the learner answers the open question on whether transformatively useful models could still be controllable. A schematic axis runs from now to the future through three regions: not yet transformatively useful, the control window, and uncontrollable. One slider, labelled 'Time that we have transformatively useful, controllable models', moves only the control frontier, so the learner widens or closes the window while the arrival of transformative usefulness stays put. Under the axis, four milestones for what time inside the window buys light up as the window widens, ordered by ambition: massively accelerate safety research (speed up safety R&D by a large factor, perhaps 30x); harden the world (patch security holes at scale, deploy safe systems across the economy); police rogue AIs and extend the delay (obstruct misaligned-AI activity, help enforce agreements, buy more time); and exit on our terms (hold control until there is an extremely solid argument for alignment). At the minimum the window disappears entirely and the widget says so: models are already uncontrollable by the time they are transformatively useful, so control never gets the chance to pay off. Widths are deliberately qualitative, an ordering of successive frontier systems rather than calendar time. Nothing is graded; the widget is marked complete once the learner has widened the window far enough to light all four milestones. If a learner is stuck, ask what the lab would actually do with the window, and what would close it."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Control track figure
     "control-timeline" (components/exercises/control-timeline.tsx), rebuilt as
     vanilla HTML/JS in the Lens look. -->
<style>
:root{
  --bg:#ffffff; --page:#faf8f3; --text:#1a1a1a; --muted:#5a5a5a; --border:#e8e5df;
  --accent:#b87018; --accent-hover:#9a5c10; --ok:#2f6b3a; --bad:#9a2c2c;
  --font-ui:"DM Sans",Arial,sans-serif; --font-heading:"Newsreader",Georgia,serif;
}
*{box-sizing:border-box}
body{margin:0;padding:16px;font:14px/1.5 var(--font-ui);color:var(--text);background:var(--bg)}
h2{font-family:var(--font-heading);font-weight:600;margin:0 0 4px;font-size:17px}
.eyebrow{font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--muted);margin:0 0 6px}
.desc{color:var(--muted);margin:0 0 12px}
.figure{border:1px solid var(--border);border-radius:8px;background:var(--page);padding:12px}
svg#timeline{width:100%;height:auto;display:block}
.ctl{margin-top:14px}
.ctl label{display:block;font-size:13px;color:var(--muted);font-weight:500}
input[type=range]{width:100%;accent-color:var(--accent);margin-top:6px}
.buys{margin:16px 0 0}
.nowindow{margin:8px 0 0;font-weight:600;color:var(--bad)}
ul.ms{list-style:none;margin:8px 0 0;padding:0}
ul.ms li{display:flex;gap:9px;align-items:flex-start;padding:6px 0;border-top:1px solid var(--border)}
ul.ms li:first-child{border-top:none}
ul.ms li.off{opacity:.55}
.mk{flex:0 0 auto;width:18px;height:18px;border-radius:9px;border:1px solid var(--border);
    display:inline-flex;align-items:center;justify-content:center;font-size:11px;line-height:1;margin-top:2px}
li.on .mk{border-color:var(--ok);color:var(--ok);font-weight:600}
li.off .mk{color:transparent}
.lead{font-weight:600}
.body{color:var(--muted)}
.note{color:var(--muted);font-size:12px;margin:14px 0 0}
@media (max-width:420px){ body{padding:12px} }
</style>
</head>
<body>
<p class="eyebrow">The control window</p>
<h2>The control timeline</h2>
<p class="desc">A schematic axis from now to the future with three regions: not yet transformatively useful, the control window, and uncontrollable. The slider adjusts how long models remain controllable after becoming transformatively useful. The arrival of transformative usefulness is fixed; the slider moves only the control frontier.</p>

<div class="figure">
<svg id="timeline" viewBox="0 0 560 190" role="img" aria-label="The control timeline: a schematic axis from now to the future with three regions, not yet transformatively useful, the control window, and uncontrollable. A slider adjusts how long models remain controllable after becoming transformatively useful."></svg>
</div>

<div class="ctl">
  <label for="w">Time that we have transformatively useful, controllable models</label>
  <input type="range" id="w" min="0" max="100" step="1" value="50" aria-label="Time that we have transformatively useful, controllable models">
</div>

<p class="eyebrow buys">What the window buys</p>
<p class="nowindow" id="nowindow" hidden>No window: models are already uncontrollable by the time they are transformatively useful, so control never gets the chance to pay off.</p>
<ul class="ms" id="ms"></ul>

<p class="note">Widths are qualitative: an ordering of successive frontier systems, not calendar time. The window's width isn't fixed in advance. It depends on how fast capabilities are pushed past transformative usefulness, and the reading argues we should hold off on building uncontrollable AI for as long as possible.</p>

<script>
"use strict";
// Axis geometry in viewBox units, from XLab's component.
var VIEW_H = 190, AXIS_Y = 95, BAND_X0 = 40, BAND_X1 = 520, TU_X = 200,
    FRONTIER_MAX_X = 440, BAND_H = 12;

var MILESTONES = [
  { threshold: 12,
    lead: "Massively accelerate safety research.",
    text: "The point of these models: speed up safety R&D by a large factor (perhaps 30x), using safe systems to make still-more-powerful systems safe and to build ever-more-robust safety techniques." },
  { threshold: 38,
    lead: "Harden the world.",
    text: "Find and patch security holes at scale, and deploy safe systems across the economy so any misaligned AIs have to compete with them for power and money." },
  { threshold: 64,
    lead: "Police rogue AIs and extend the delay.",
    text: "Monitor for and obstruct misaligned-AI activity, help enforce agreements like “no models past capability X without passing safety tests”: AI labor that itself buys more time before uncontrollable AI." },
  { threshold: 88,
    lead: "Exit on our terms.",
    text: "Building wildly superintelligent AI could wait for decades while these models solve a host of problems, keeping control until there's an extremely solid argument for alignment." }
];

var width = 50;
var maxWidth = 50;

function svgEl(name, attrs){
  var n = document.createElementNS("http://www.w3.org/2000/svg", name);
  for(var key in attrs){ n.setAttribute(key, attrs[key]); }
  return n;
}
function text(x, y, str, attrs){
  var a = attrs || {};
  a.x = x; a.y = y;
  var t = svgEl("text", a);
  t.textContent = str;
  return t;
}

// A horizontal curly brace spanning [x1, x2], arms at y, nub pointing away
// from the axis (dir -1 = up, 1 = down).
function bracePath(x1, x2, y, dir){
  var d1 = 6 * dir, d2 = 12 * dir;
  var r = Math.min(8, (x2 - x1) / 4);
  var mid = (x1 + x2) / 2;
  return "M " + x1 + " " + y +
    " Q " + x1 + " " + (y + d1) + " " + (x1 + r) + " " + (y + d1) +
    " L " + (mid - r) + " " + (y + d1) +
    " Q " + mid + " " + (y + d1) + " " + mid + " " + (y + d2) +
    " Q " + mid + " " + (y + d1) + " " + (mid + r) + " " + (y + d1) +
    " L " + (x2 - r) + " " + (y + d1) +
    " Q " + x2 + " " + (y + d1) + " " + x2 + " " + y;
}

function drawTimeline(){
  var svg = document.getElementById("timeline");
  svg.textContent = "";

  var frontierX = TU_X + (width / 100) * (FRONTIER_MAX_X - TU_X);
  var hasWindow = frontierX - TU_X > 1;

  var defs = svgEl("defs", {});
  var marker = svgEl("marker", { id:"ct-arrow", viewBox:"0 0 8 8", refX:7, refY:4,
    markerWidth:7, markerHeight:7, orient:"auto-start-reverse" });
  marker.appendChild(svgEl("path", { d:"M 0 0 L 8 4 L 0 8 z", fill:"var(--muted)" }));
  defs.appendChild(marker);
  svg.appendChild(defs);

  // The thin double-ended axis.
  svg.appendChild(svgEl("line", { x1:16, y1:AXIS_Y, x2:544, y2:AXIS_Y,
    stroke:"var(--muted)", "stroke-width":1.5,
    "marker-start":"url(#ct-arrow)", "marker-end":"url(#ct-arrow)" }));
  svg.appendChild(text(16, AXIS_Y - 18, "Now",
    { "font-size":11, "font-weight":600, fill:"var(--muted)" }));
  svg.appendChild(text(544, AXIS_Y - 18, "The future",
    { "font-size":11, "font-weight":600, fill:"var(--muted)", "text-anchor":"end" }));

  // Region bands riding the axis.
  svg.appendChild(svgEl("rect", { x:BAND_X0, y:AXIS_Y - BAND_H/2, width:TU_X - BAND_X0,
    height:BAND_H, rx:3, fill:"var(--border)", stroke:"var(--muted)",
    "stroke-width":0.75, "stroke-opacity":0.6 }));
  if(hasWindow){
    svg.appendChild(svgEl("rect", { x:TU_X, y:AXIS_Y - BAND_H/2, width:frontierX - TU_X,
      height:BAND_H, rx:3, fill:"var(--ok)", "fill-opacity":0.22,
      stroke:"var(--ok)", "stroke-width":0.75 }));
  }
  svg.appendChild(svgEl("rect", { x:frontierX, y:AXIS_Y - BAND_H/2, width:BAND_X1 - frontierX,
    height:BAND_H, rx:3, fill:"var(--bad)", "fill-opacity":0.18,
    stroke:"var(--bad)", "stroke-width":0.75 }));

  // Brace above the control window.
  if(hasWindow){
    svg.appendChild(svgEl("path", { d:bracePath(TU_X, frontierX, AXIS_Y - BAND_H/2 - 4, -1),
      fill:"none", stroke:"var(--ok)", "stroke-width":1.25 }));
    svg.appendChild(text((TU_X + frontierX)/2, AXIS_Y - BAND_H/2 - 26, "Control window",
      { "font-size":11.5, "font-weight":600, fill:"var(--ok)", "text-anchor":"middle" }));
  }

  // Braces beneath the outer regions.
  svg.appendChild(svgEl("path", { d:bracePath(BAND_X0, TU_X, AXIS_Y + BAND_H/2 + 4, 1),
    fill:"none", stroke:"var(--muted)", "stroke-width":1.25, "stroke-opacity":0.6 }));
  var midLeft = (BAND_X0 + TU_X) / 2;
  var left = svgEl("text", { x:midLeft, y:AXIS_Y + BAND_H/2 + 34, "font-size":11,
    fill:"var(--muted)", "text-anchor":"middle" });
  var l1 = svgEl("tspan", { x:midLeft, dy:0 }); l1.textContent = "Not yet";
  var l2 = svgEl("tspan", { x:midLeft, dy:13 }); l2.textContent = "transformatively useful";
  left.appendChild(l1); left.appendChild(l2);
  svg.appendChild(left);

  svg.appendChild(svgEl("path", { d:bracePath(frontierX, BAND_X1, AXIS_Y + BAND_H/2 + 4, 1),
    fill:"none", stroke:"var(--bad)", "stroke-width":1.25 }));
  svg.appendChild(text((frontierX + BAND_X1)/2, AXIS_Y + BAND_H/2 + 40, "Uncontrollable",
    { "font-size":11, "font-weight":600, fill:"var(--bad)", "text-anchor":"middle" }));

  return hasWindow;
}

function drawMilestones(){
  var list = document.getElementById("ms");
  list.textContent = "";
  MILESTONES.forEach(function(m){
    var lit = width >= m.threshold;
    var li = document.createElement("li");
    li.className = lit ? "on" : "off";
    var mk = document.createElement("span");
    mk.className = "mk";
    mk.textContent = "✓";
    mk.setAttribute("aria-hidden", "true");
    var span = document.createElement("span");
    var lead = document.createElement("span");
    lead.className = "lead";
    lead.textContent = m.lead + " ";
    var body = document.createElement("span");
    body.className = "body";
    body.textContent = m.text;
    span.appendChild(lead);
    span.appendChild(body);
    li.appendChild(mk);
    li.appendChild(span);
    li.setAttribute("aria-label", (lit ? "Unlocked: " : "Locked: ") + m.lead + " " + m.text);
    list.appendChild(li);
  });
}

function render(){
  var hasWindow = drawTimeline();
  document.getElementById("nowindow").hidden = hasWindow;
  drawMilestones();
  document.getElementById("w").value = String(width);
  save();
}

var saveTimer = null;
function save(){
  if(!window.Lens){ return; }
  if(saveTimer){ clearTimeout(saveTimer); }
  saveTimer = setTimeout(function(){
    var lit = MILESTONES.filter(function(m){ return width >= m.threshold; });
    var summary = "Control timeline widget. The learner has set the width of the control window to " +
      width + " out of 100" +
      (width === 0
        ? ", which closes the window entirely: models are already uncontrollable by the time they are transformatively useful."
        : ", so the window runs from the moment models become transformatively useful to the control frontier.") +
      " Milestones lit for what the window buys: " + lit.length + " of " + MILESTONES.length +
      (lit.length ? " (" + lit.map(function(m){ return m.lead.replace(/\.$/, ""); }).join("; ") + ")" : "") +
      ". Furthest width reached: " + maxWidth + ".";
    Lens.saveState({ width: width, maxWidth: maxWidth }, summary);
    if(maxWidth >= MILESTONES[MILESTONES.length - 1].threshold){ Lens.complete(); }
  }, 400);
}

document.getElementById("w").addEventListener("input", function(e){
  width = Number(e.target.value);
  if(width > maxWidth){ maxWidth = width; }
  render();
});

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(state && typeof state.width === "number"){ width = state.width; }
    if(state && typeof state.maxWidth === "number"){ maxWidth = state.maxWidth; }
    if(width > maxWidth){ maxWidth = width; }
    render();
  });
} else {
  render();
}
</script>
</body>
</html>

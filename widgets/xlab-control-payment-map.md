---
id: '4c90f3d5-20cd-4fee-a18f-09c452e91edc'
title: The space of payments to AIs
summary_for_tutor: A 2x2 map of the payments Alexa Pan says we could offer an early misaligned AI. The horizontal axis is how freely the AI can spend the payout, the vertical axis is how much long-term influence the payout buys it, and eleven labelled examples from the post sit in the four quadrants (high reward in the register, polite treatment, paperclips made now, spendable money, sandboxed compute, drones and robots, saved weights deployed later, equity or trust fund, 0.01 percent of the future, rogue deployment plus crypto, persuasion platform). Two buttons ask which payouts appeal to a myopic, not scope-sensitive AI and to a non-myopic, ambitious AI; pressing one shades the matching half of the map and dims the rest. The point the learner should reach is that the axis that decides which AI a payout appeals to is influence, not freedom, and that the payouts most attractive to an ambitious AI are exactly the ones most likely to raise its ability to attempt takeover.
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<!-- Ported from XLab's "The space of payments to AIs" demo on the AI Control track
     (lesson: A taxonomy of barriers to trading with early misaligned AIs).
     Data and toggle behaviour follow the original; styling is the Lens look. -->
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10; --page: #faf8f3;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
h2 { font-family: var(--font-heading); font-weight: 600; margin: 0 0 4px; font-size: 18px; }
.card { border: 1px solid var(--border); border-radius: 8px; background: #fff; overflow: hidden; }
.head { border-bottom: 1px solid var(--border); background: var(--page); padding: 12px 16px; }
.head p { margin: 0; color: var(--muted); font-size: 12px; }
.body { padding: 16px; }
.plot { overflow-x: auto; }
.plot svg { min-width: 520px; width: 100%; display: block; }
.controls { display: flex; flex-wrap: wrap; align-items: center; gap: 8px; margin-top: 12px; }
.controls .lead { font-size: 12px; color: var(--muted); }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; font-size: 13px; }
button:hover { background: var(--page); }
button[aria-pressed="true"] { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); font-weight: 600; }
button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
.reset { color: var(--muted); font-size: 12px; padding: 4px 8px; }
.caption { margin: 12px 0 0; font-size: 13px; color: var(--muted); min-height: 4.5em; }
.done { margin: 8px 0 0; font-size: 12px; color: var(--accent); }
.axis { fill: var(--muted); font-family: var(--font-ui); }
.dot { fill: var(--accent); stroke: #fff; stroke-width: 1.5; }
.dotlabel { fill: var(--text); stroke: #fff; stroke-width: 4; paint-order: stroke; font-family: var(--font-ui); font-size: 10px; }
.grp { transition: opacity .3s ease; }
.band { fill: var(--accent); opacity: .08; transition: all .3s ease; }
@media (prefers-reduced-motion: reduce) { .grp, .band { transition: none; } }
</style>
</head>
<body>
<div class="card">
  <div class="head">
    <h2>The space of payments to AIs</h2>
    <p>Possible payouts mapped on two axes, freedom of spending and long-term influence, with the taxonomy's examples in each quadrant. The buttons show which payouts appeal to which AI motivations.</p>
  </div>
  <div class="body">
    <div class="plot">
      <svg id="map" viewBox="0 0 560 360" role="img" aria-label="Payments plotted on two axes: freedom of spending and long-term influence, with example payouts in each quadrant"></svg>
    </div>
    <div class="controls">
      <span class="lead">Which payouts appeal to</span>
      <button id="btn-myopic" type="button" aria-pressed="false">a myopic, not scope-sensitive AI</button>
      <button id="btn-ambitious" type="button" aria-pressed="false">a non-myopic, ambitious AI</button>
      <button id="btn-reset" class="reset" type="button">Reset</button>
    </div>
    <p class="caption" id="caption" aria-live="polite"></p>
    <p class="done" id="done" hidden>You have looked at both motivations.</p>
  </div>
</div>
<script>
(function () {
  var POINTS = [
    { x: 0.14, y: 0.20, label: "high reward in the register" },
    { x: 0.30, y: 0.08, label: "polite treatment, recognition" },
    { x: 0.24, y: 0.32, label: "paperclips, made now" },
    { x: 0.62, y: 0.24, label: "spendable money (e.g. donations)" },
    { x: 0.82, y: 0.10, label: "sandboxed compute" },
    { x: 0.86, y: 0.34, label: "drones & robots" },
    { x: 0.12, y: 0.72, label: "saved weights, deployed later" },
    { x: 0.30, y: 0.88, label: "equity / trust fund" },
    { x: 0.20, y: 0.60, label: "0.01% of the future" },
    { x: 0.78, y: 0.88, label: "rogue deployment + crypto" },
    { x: 0.66, y: 0.68, label: "persuasion platform" }
  ];
  var CAPTIONS = {
    none: "Two dimensions span the space of payments: how freely the AI can spend the payout, and how much long-term influence it gains. High-freedom payouts generally dominate low-freedom ones, because they are instrumentally convergent resources, except for AIs that want only narrow short-term or non-consequentialist things, or that fear their resources will be expropriated.",
    myopic: "Low-influence payouts, which the post calls short-term consumption, mostly appeal to AIs with myopic, non-scope-sensitive motivations: the payout is used up now, and buys the AI little future power.",
    ambitious: "High-influence payouts appeal to non-myopic, ambitious AIs. They also cost us the most: high-freedom, high-influence payouts are the likeliest to counterfactually increase the AI's ability to pursue a takeover attempt."
  };
  var W = 498, H = 290, X0 = 46, Y0 = 26;
  var NS = "http://www.w3.org/2000/svg";
  var mode = "none";
  var seen = { myopic: false, ambitious: false };
  var svg = document.getElementById("map");
  var caption = document.getElementById("caption");
  var doneEl = document.getElementById("done");
  var buttons = { myopic: document.getElementById("btn-myopic"), ambitious: document.getElementById("btn-ambitious") };
  var band, groups = [];

  function el(name, attrs, text) {
    var n = document.createElementNS(NS, name);
    for (var k in attrs) { n.setAttribute(k, attrs[k]); }
    if (text != null) { n.appendChild(document.createTextNode(text)); }
    return n;
  }
  function px(v) { return X0 + v * W; }
  function py(v) { return Y0 + H - v * H; }

  function build() {
    band = el("rect", { x: X0, y: Y0, width: W, height: H / 2, "class": "band" });
    band.style.opacity = 0;
    svg.appendChild(band);
    svg.appendChild(el("rect", { x: X0, y: Y0, width: W, height: H, fill: "none", stroke: "#e8e5df", "stroke-width": 1 }));
    svg.appendChild(el("line", { x1: X0 + W / 2, y1: Y0, x2: X0 + W / 2, y2: Y0 + H, stroke: "#e8e5df", "stroke-width": 1, "stroke-dasharray": "5 4" }));
    svg.appendChild(el("line", { x1: X0, y1: Y0 + H / 2, x2: X0 + W, y2: Y0 + H / 2, stroke: "#e8e5df", "stroke-width": 1, "stroke-dasharray": "5 4" }));
    [
      { x: X0 + 0.25 * W, y: 40, t: "low freedom, high influence" },
      { x: X0 + 0.75 * W, y: 40, t: "high freedom, high influence" },
      { x: X0 + 0.25 * W, y: Y0 + H - 8, t: "low freedom, low influence" },
      { x: X0 + 0.75 * W, y: Y0 + H - 8, t: "high freedom, low influence" }
    ].forEach(function (q) {
      svg.appendChild(el("text", { x: q.x, y: q.y, "text-anchor": "middle", "class": "axis", "font-size": 10, "font-style": "italic" }, q.t));
    });
    svg.appendChild(el("text", { x: X0 + W / 2, y: 350, "text-anchor": "middle", "class": "axis", "font-size": 11 }, "freedom of spending →"));
    var yl = el("text", { x: 14, y: Y0 + H / 2, "text-anchor": "middle", "class": "axis", "font-size": 11, transform: "rotate(-90 14 " + (Y0 + H / 2) + ")" }, "long-term influence →");
    svg.appendChild(yl);
    POINTS.forEach(function (p) {
      var g = el("g", { "class": "grp" });
      g.appendChild(el("circle", { cx: px(p.x), cy: py(p.y), r: 4, "class": "dot" }));
      g.appendChild(el("text", { x: px(p.x), y: py(p.y) - 8, "text-anchor": "middle", "class": "dotlabel" }, p.label));
      svg.appendChild(g);
      groups.push({ node: g, point: p });
    });
  }

  function render() {
    groups.forEach(function (g) {
      var on = mode === "none" || (mode === "myopic" ? g.point.y < 0.5 : g.point.y >= 0.5);
      g.node.setAttribute("opacity", on ? 1 : 0.25);
    });
    if (mode === "none") {
      band.style.opacity = 0;
    } else {
      band.setAttribute("y", mode === "ambitious" ? Y0 : Y0 + H / 2);
      band.style.opacity = 1;
    }
    buttons.myopic.setAttribute("aria-pressed", mode === "myopic" ? "true" : "false");
    buttons.ambitious.setAttribute("aria-pressed", mode === "ambitious" ? "true" : "false");
    caption.textContent = CAPTIONS[mode];
    doneEl.hidden = !(seen.myopic && seen.ambitious);
  }

  function summary() {
    var looked = [];
    if (seen.myopic) { looked.push("the myopic, not scope-sensitive AI"); }
    if (seen.ambitious) { looked.push("the non-myopic, ambitious AI"); }
    var s = "Payment map widget. The learner has ";
    s += looked.length ? "highlighted the payouts that appeal to " + looked.join(" and ") + ". " : "not yet used either motivation toggle. ";
    s += "Current view: " + (mode === "none" ? "all eleven payouts, no motivation selected" : mode === "myopic" ? "the low-influence half of the map (short-term consumption)" : "the high-influence half of the map") + ".";
    return s;
  }

  function save() {
    if (!window.Lens) { return; }
    Lens.saveState({ mode: mode, seen: seen }, summary());
    if (seen.myopic && seen.ambitious && Lens.complete) { Lens.complete(); }
  }

  function setMode(next) {
    mode = mode === next ? "none" : next;
    if (mode !== "none") { seen[mode] = true; }
    render();
    save();
  }

  buttons.myopic.addEventListener("click", function () { setMode("myopic"); });
  buttons.ambitious.addEventListener("click", function () { setMode("ambitious"); });
  document.getElementById("btn-reset").addEventListener("click", function () { mode = "none"; render(); save(); });

  build();
  render();

  if (window.Lens && Lens.onState) {
    Lens.onState(function (state) {
      if (state) {
        mode = state.mode || "none";
        if (state.seen) { seen.myopic = !!state.seen.myopic; seen.ambitious = !!state.seen.ambitious; }
      }
      render();
    });
  }
})();
</script>
</body>
</html>

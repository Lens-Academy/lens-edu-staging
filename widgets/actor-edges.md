---
id: 'a29e5708-d419-4e9a-a05a-408ba9d051a8'
title: Who can prove what
summary_for_tutor: "The learner draws directed evidence edges on the 17-actor ring board from 1.2 (United States, China, Taiwan, Netherlands, Japan, South Korea, BIS, Intelligence community, California, the AI verification body that does not exist, ASML, TSMC, NVIDIA, Cloud providers, Frontier labs, Proxies, Deployers), shown on the key placement (Declares, Holds the evidence, Verifies, Outside the declaration) around a training run above the threshold. An edge A to B means A can produce evidence about B for a verifier that B did not volunteer; the learner drags between points, taps a source then a target, or picks from the source and target button lists, and there is no target number. Committing grades against XLab's seven-edge key (Cloud providers to Frontier labs, 1.A; NVIDIA to Frontier labs, 1.B; NVIDIA to Cloud providers, 2.A; TSMC to Proxies, NVIDIA to Proxies, Intelligence community to China, Intelligence community to Proxies, all 2.B), recolours the map (solid in the key, dotted reversed or extra, dashed missed), gives one verdict line per key edge with its subgoal and mechanism, and completes the widget; Edit my edges reopens drawing, and role chips light up actors by functional role. The saved-state summary lists the edges the learner drew and how they scored: found, reversed, extra, missed. Everything else is lesson text on the page around the widget: the brief and the board, the four Baker et al. subgoals with their quotes, a closed callout with the 17-actor roster (positions, notes, rings, roles, postures), what an edge means, then after the widget the closed callouts with the seven-edge key and its Baker quotes and the ten actors with no edge, the reading of the finished map and where the regime is weakest, the multiple-choice question on whose removal stops a run soonest, and three optional written questions marked against XLab's key. Ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Who can prove what</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "actor-edges". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df; --surface: #faf8f3;
    --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0; }
  p { margin: 0; }
  .stack > * + * { margin-top: 16px; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .muted { color: var(--muted); }
  .small { font-size: 12px; }
  .strong { font-weight: 600; }
  .medium { font-weight: 500; }
  ol, ul { margin: 0; padding-left: 0; list-style: none; }
  .list > li + li { margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--border); }
  .tight > li + li { margin-top: 4px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button:disabled:hover { background: #fff; }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button.is-active { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: #fdf6ec; font-weight: 500; }
  button.chip { padding: 6px 10px; font-size: 12px; }
  button.link { border: 0; padding: 0; background: none; border-radius: 0; }
  button.link:hover { background: none; text-decoration: underline; }
  .chips { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; align-items: center; }
  .row { display: flex; flex-wrap: wrap; gap: 12px; align-items: center; justify-content: space-between; }
  .mapbox { border: 1px solid var(--border); border-radius: 8px; padding: 8px; background: #fff; overflow-x: auto; max-width: 860px; margin: 0 auto; }
  .mapbox svg { display: block; width: 100%; height: auto; min-width: 560px; margin: 0 auto; }
  .mapbox .note { padding: 4px 8px; font-size: 12px; color: var(--muted); }
  .node.is-interactive { cursor: crosshair; touch-action: none; outline: none; }
  .node:focus-visible .hit { stroke: var(--accent); stroke-width: 2; }
  .node text { user-select: none; -webkit-user-select: none; }
  .legend { display: flex; flex-wrap: wrap; gap: 12px 18px; padding: 4px 8px; font-size: 12px; color: var(--muted); }
  .legend span { display: inline-flex; align-items: center; gap: 6px; }
  .legend svg { width: 28px; height: 10px; min-width: 0; }
  .verdict-line { display: flex; gap: 6px; align-items: flex-start; }
  .mark { flex: none; width: 16px; height: 16px; margin-top: 3px; }
  .quote { border-left: 2px solid var(--border); padding-left: 12px; margin-top: 6px; font-size: 12px; line-height: 1.55; color: var(--muted); }
  @media (max-width: 600px) { body { padding: 12px; } }
</style>
</head>
<body>
<div id="app" class="stack" aria-live="polite"></div>

<script>
  // ---------- Data (from XLab: src/lib/verification/data/actor-workshop.ts and actor-map.ts) ----------
  // Names, positions, notes, postures and the ring tests are lesson text on the page around this widget.
  var ACTORS = [
    { id: "us", label: "United States", roles: ["capability", "chokepoint", "information", "enforcement"] },
    { id: "china", label: "China", roles: ["capability", "chokepoint", "information", "enforcement"] },
    { id: "taiwan", label: "Taiwan", roles: ["chokepoint", "information", "victim"] },
    { id: "netherlands", label: "Netherlands", roles: ["chokepoint", "information"] },
    { id: "japan", label: "Japan", roles: ["chokepoint"] },
    { id: "south-korea", label: "South Korea", roles: ["chokepoint", "information"] },
    { id: "bis", label: "BIS", roles: ["enforcement", "information"] },
    { id: "ic", label: "Intelligence community", roles: ["information"] },
    { id: "california", label: "California", roles: ["enforcement", "information"] },
    { id: "missing-verifier", label: "No AI verification body", roles: [] },
    { id: "asml", label: "ASML", roles: ["chokepoint", "information"] },
    { id: "tsmc", label: "TSMC", roles: ["chokepoint", "information", "evasion"] },
    { id: "nvidia", label: "NVIDIA", roles: ["chokepoint", "information", "evasion", "victim"] },
    { id: "hyperscalers", label: "Cloud providers", roles: ["chokepoint", "information", "enforcement", "evasion"] },
    { id: "frontier-labs", label: "Frontier labs", roles: ["capability", "information", "victim"] },
    { id: "proxies", label: "Proxies", roles: ["evasion"] },
    { id: "deployers", label: "Deployers", roles: ["victim"] }
  ];
  var ACTOR_BY_ID = {};
  ACTORS.forEach(function (a) { ACTOR_BY_ID[a.id] = a; });
  function labelOf(id) { return ACTOR_BY_ID[id] ? ACTOR_BY_ID[id].label : id; }

  var RINGS = [
    { id: "declares", name: "Declares" },
    { id: "evidence", name: "Holds the evidence" },
    { id: "verifies", name: "Verifies" },
    { id: "undeclared", name: "Outside the declaration" }
  ];
  var RING_KEY = {
    us: "declares", china: "declares", taiwan: "evidence", netherlands: "evidence", japan: "evidence", "south-korea": "evidence",
    bis: "verifies", ic: "verifies", california: "verifies", "missing-verifier": "verifies",
    asml: "evidence", tsmc: "evidence", nvidia: "evidence", hyperscalers: "declares", "frontier-labs": "declares",
    proxies: "undeclared", deployers: "undeclared"
  };
  var MAP_SLOTS = ["asml", "us", "taiwan", "bis", "nvidia", "hyperscalers", "proxies", "tsmc", "ic", "netherlands", "frontier-labs", "japan", "california", "south-korea", "china", "deployers", "missing-verifier"];
  var ABSENT = { "missing-verifier": true };
  var CENTRE = { label: "A training run", sub: "above the threshold" };

  var ROLES = [
    { id: "capability", name: "Capability holder" },
    { id: "chokepoint", name: "Chokepoint controller" },
    { id: "information", name: "Information holder" },
    { id: "enforcement", name: "Enforcement authority" },
    { id: "evasion", name: "Evasion pathway" },
    { id: "victim", name: "Victim, free-rider, beneficiary" }
  ];

  var SUBGOALS = [
    { id: "1a", label: "1.A", name: "Declared uses are accurate" },
    { id: "1b", label: "1.B", name: "Declared uses have the required properties" },
    { id: "2a", label: "2.A", name: "No undeclared use of a declared cluster" },
    { id: "2b", label: "2.B", name: "No undeclared clusters at all" }
  ];
  var SUBGOAL_BY_ID = {};
  SUBGOALS.forEach(function (s) { SUBGOAL_BY_ID[s.id] = s; });

  // The full mechanism and its Baker et al. quotes, printed against each key edge once the learner commits, as XLab does.
  var EDGE_KEY = [
    { from: "hyperscalers", to: "frontier-labs", subgoal: "1a",
      what: "The declared run happened on somebody else’s machines. The cluster’s own records (logs, billing, and the sensors a verification regime would attach to it) are where a Verifier goes to find out whether the declaration matches what the chips did.",
      baker: [{ text: "the Verifier would aim to detect discrepancies between a Prover’s declarations and their actual chip use, such as by detecting that chips’ input data or power draw patterns tell a different story than the Prover’s claims", where: "§4.2, off-chip verification layers" }] },
    { from: "nvidia", to: "frontier-labs", subgoal: "1b",
      what: "Checking that a declared model has the properties the rules require means running tests on it without the Prover handing over its weights. The feature that makes that possible is built into the chip at design time; Baker names NVIDIA among the designers that have implemented or announced versions of it.",
      baker: [{ text: "This could enable a Verifier to run tests on a Prover’s models, data, and code, with the Prover knowing their information will not be stolen, and with the Verifier knowing their tests will be run faithfully and will not be viewed for the sake of manipulating test results.", where: "§4.1.1, Confidential Computing" }] },
    { from: "nvidia", to: "hyperscalers", subgoal: "2a",
      what: "Accounting for everything a declared cluster did means the chips keeping their own record. That is a hardware feature, present or absent at manufacture: the cluster’s operator cannot add it afterwards, and cannot quietly remove it either.",
      baker: [{ text: "Security features built into AI chips may enable verification, such as by ensuring that AI chips log traces of their activities for confidential analysis.", where: "§4.1, the on-chip verification layer" }] },
    { from: "tsmc", to: "proxies", subgoal: "2b",
      what: "The chain of custody starts where the die is made. How many leading-edge parts exist at all is the ceiling on how large any undeclared cluster could possibly be, and that number exists in one place.",
      baker: [{ text: "A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.", where: "§4.2.1, verifying AI chips’ chain of custody" },
              { text: "This would serve to verify that large quantities of AI chips are not assembled into undeclared AI compute clusters (Subgoal 2.B).", where: "§4.2.1" }] },
    { from: "nvidia", to: "proxies", subgoal: "2b",
      what: "The same chain one link down: who the parts were sold to, and which serialised chip went where. This is NVIDIA’s second mechanism and a different one from the first, which is exactly why it gets its own edge.",
      baker: [{ text: "An example verification mechanism is inspecting AI chips to verify that they have not been sent to undeclared AI data centers; this helps complete Subgoal 2.B.", where: "§4, defining a verification mechanism" }] },
    { from: "ic", to: "china", subgoal: "2b",
      what: "The lesson's own row for this agency is monitoring and attribution: the layer that spots hidden data centres and procurement networks. It is what one signatory has instead of a right to inspect the other. Note what it costs: what it knows is classified, so turning it into evidence anybody may act on risks the source that produced it. And note the asymmetry, which is a fact about this roster rather than about the world: China has the same capability and this board has no row for it.",
      baker: [{ text: "Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.", where: "§4.3, personnel-based verification layers" },
              { text: "More adversarial, harder for third parties to verify, and unclear effectiveness.", where: "§4.3, the layer’s own listed disadvantages" }] },
    { from: "ic", to: "proxies", subgoal: "2b",
      what: "A cluster nobody declared leaves no paperwork to audit. What is left is people and signals, and this is the only actor on the board that can reach a facility that was never on any list. Read the quote carefully: the paper gives intelligence EVERY subgoal, not this one. It is filed here because 2.B is the only place on this board where it is the sole mechanism, and an edge you drew from it to a lab or a cloud has the paper behind it.",
      baker: [{ text: "Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.", where: "§4.3, personnel-based verification layers" }] }
  ];

  // The ten actors the key gives no edge, with the reason and its Baker quotes (XLab: EDGE_NOTES).
  var EDGE_NOTES = [
    { actorIds: ["us"],
      why: "A signatory declares; it does not produce evidence itself. What a state has for that is institutions, which is why the intelligence edge starts at the agency rather than at the country. Then notice the shape that leaves: China is at the receiving end of an edge and the United States is at the receiving end of none. Do not read that as a claim that one government is the more transparent. It is a claim about which government's institutions this roster wrote down, and about the empty ring where the body that would check both of them should be.",
      baker: [{ text: "The Prover could be a private institution or (in the case of international agreements) a government, which could constrain private companies within its territory as part of the agreement.", where: "§3.1, Prover and Verifier" }] },
    { actorIds: ["taiwan", "netherlands", "japan", "south-korea"],
      why: "The four host states hold the jurisdiction that makes their firms' records producible, and not one of them is a party to this agreement. That is not an oversight in the drawing; it is the open problem the paper lists under attaining participation, and it is the reason a two-party compute agreement leans on export controls and energy policy rather than on the agreement itself. An edge you drew from one of them is an edge nothing compels.",
      baker: [{ text: "How to attain compliance commitments from all states that host large-scale AI compute (as such states could directly misuse it or rent it to an agreement party)?", where: "§3.3, broader challenges" }] },
    { actorIds: ["missing-verifier"],
      why: "This one can hold no edge, and that is the row, not a gap in it. The paper allows a government body or a third party as Verifier; every government body here belongs to one signatory, and the third party does not exist: no chip registry, no challenge-inspection right, no procedure for resolving an allegation of training above a threshold. Read the board once more with that in mind: a two-party agreement in which only one party's institutions can check anything, and no neutral party at all.",
      baker: [{ text: "The Verifier could be a government body or a third party.", where: "§3.1" }] },
    { actorIds: ["asml"],
      why: "Baker’s chain of custody begins at manufacturing, and ASML is upstream of that: it sells the machines the fab uses, not the parts a regime counts. The tightest chokepoint on the map completes no subgoal, which is what the difference between leverage and evidence looks like.",
      baker: [{ text: "A Verifier could verify the locations and owners of random samples of AI chips from manufacturing to end-of-life destruction.", where: "§4.2.1; the chain starts at manufacturing, not at the tools" }] },
    { actorIds: ["bis"],
      why: "Export control is the instrument, and the paper puts it outside the frame deliberately: it is how a party is stopped or punished after a finding, not how a declaration is checked. Today’s de facto compute-governance agency is, in this framework, downstream of verification rather than part of it.",
      baker: [{ text: "We do not cover this latter step of enforcement, though a few verification mechanisms double as enforcement tools.", where: "§2.3, scope limitations" }] },
    { actorIds: ["california"],
      why: "A reporting statute produces declarations. Verification is what happens to a declaration afterwards, and receiving one is not checking it. The actor that bound the leading labs before any international mechanism existed completes no subgoal: it supplies the thing the subgoals are about. Argue with this one if you drew the edge: SB 53 also requires an internal anonymous reporting channel at large frontier developers, and whistleblowing is a verification mechanism in this framework, for every subgoal at once. The key leaves the edge out because the mechanism is a programme a Verifier runs and California is not running one, which is a judgement, not a reading.",
      baker: [{ text: "Verification focuses on checking that these declarations are correct and complete.", where: "§3.2" },
              { text: "Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals.", where: "§4.3, the personnel-based layers" }] },
    { actorIds: ["deployers"],
      why: "Below the threshold, and that is the whole of it. Millions of actors running somebody else’s model are outside the regime by construction rather than by evasion, which is why they share a ring with the proxies and share nothing else.",
      baker: [{ text: "AI development or deployment is “large-scale” if it uses thousands of high-end AI chips over multiple months.", where: "§2.2, what counts as large-scale" }] }
  ];

  // ---------- Engine (from XLab: src/lib/verification/actor-workshop.ts) ----------
  function edgeId(from, to) { return from + ">" + to; }
  function splitEdge(id) { var p = id.split(">"); return { from: p[0] || "", to: p[1] || "" }; }
  function edgeLabel(id) { var e = splitEdge(id); return labelOf(e.from) + " → " + labelOf(e.to); }
  var KEY_EDGE_IDS = EDGE_KEY.map(function (e) { return edgeId(e.from, e.to); });
  function has(list, x) { return list.indexOf(x) !== -1; }
  function scoreEdges(drawn, key) {
    var flip = function (id) { var e = splitEdge(id); return edgeId(e.to, e.from); };
    var found = key.filter(function (id) { return has(drawn, id); });
    var missed = key.filter(function (id) { return !has(drawn, id); });
    var surplus = drawn.filter(function (id) { return !has(key, id); });
    var reversed = surplus.filter(function (id) { return has(key, flip(id)) && !has(drawn, flip(id)); });
    var extra = surplus.filter(function (id) { return !has(reversed, id); });
    return { found: found, missed: missed, reversed: reversed, extra: extra };
  }

  // ---------- State ----------
  var STORAGE_KEY = "lens-widget:actor-edges:v1";
  var EMPTY = { edges: [], edgesDone: false };
  var state = prune(null);
  var completed = false;
  var ui = { source: null, lens: null };

  function prune(raw) {
    var box = (raw && typeof raw === "object") ? raw : {};
    var out = { edges: [], edgesDone: box.edgesDone === true };
    if (Array.isArray(box.edges)) {
      box.edges.forEach(function (e) {
        if (typeof e !== "string") return;
        var p = e.split(">");
        if (p.length !== 2 || !ACTOR_BY_ID[p[0]] || !ACTOR_BY_ID[p[1]] || p[0] === p[1]) return;
        if (!has(out.edges, e)) out.edges.push(e);
      });
    }
    if (!out.edges.length) out.edgesDone = false;
    return out;
  }

  function summary() {
    var score = scoreEdges(state.edges, KEY_EDGE_IDS);
    var parts = [];
    if (state.edges.length) {
      parts.push("Edges drawn (" + state.edges.length + "; A to B means A can produce evidence about B for a verifier): " + state.edges.map(function (id) { var e = splitEdge(id); return labelOf(e.from) + " to " + labelOf(e.to); }).join("; ") + ".");
    } else {
      parts.push("No edges drawn yet.");
    }
    if (state.edgesDone) {
      parts.push("Edges committed. Against XLab's seven-edge key: " + score.found.length + " of 7 found" +
        (score.reversed.length ? ", " + score.reversed.length + " drawn the other way round (" + score.reversed.map(edgeLabel).join("; ") + ")" : "") +
        (score.extra.length ? ", " + score.extra.length + " not in the key (" + score.extra.map(edgeLabel).join("; ") + ")" : "") +
        (score.missed.length ? ", missed: " + score.missed.map(edgeLabel).join("; ") : "") + ".");
    } else {
      parts.push("Edges not committed yet; the verdict has not been shown.");
    }
    return parts.join(" ");
  }

  function persist() {
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (!completed && state.edgesDone) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }
  function update(fn) { fn(state); persist(); render(); }

  // ---------- DOM helpers ----------
  var SVG_NS = "http://www.w3.org/2000/svg";
  function el(tag, className, text) { var n = document.createElement(tag); if (className) n.className = className; if (text !== undefined) n.textContent = text; return n; }
  function svg(tag, attrs) { var n = document.createElementNS(SVG_NS, tag); if (attrs) Object.keys(attrs).forEach(function (k) { n.setAttribute(k, attrs[k]); }); return n; }
  function btn(text, className, onClick, key) {
    var b = el("button", className, text); b.type = "button";
    if (key) b.setAttribute("data-key", key);
    b.addEventListener("click", onClick);
    return b;
  }
  function para(className, text) { return el("p", className, text); }
  function inline(parts) { var s = el("span"); parts.forEach(function (x) { s.appendChild(typeof x === "string" ? document.createTextNode(x) : x); }); return s; }
  function icon(kind) {
    var s = svg("svg", { viewBox: "0 0 16 16", class: "mark", "aria-hidden": "true" });
    s.appendChild(svg("circle", { cx: 8, cy: 8, r: 7, fill: "none", stroke: kind === "ok" ? "#b87018" : "#5a5a5a", "stroke-width": 1.5 }));
    if (kind === "ok") s.appendChild(svg("path", { d: "M4.5 8.5 L7 11 L11.5 5.5", fill: "none", stroke: "#b87018", "stroke-width": 1.75, "stroke-linecap": "round", "stroke-linejoin": "round" }));
    else { s.appendChild(svg("path", { d: "M8 4.5 V9", stroke: "#5a5a5a", "stroke-width": 1.75, "stroke-linecap": "round" })); s.appendChild(svg("circle", { cx: 8, cy: 11.5, r: 1, fill: "#5a5a5a" })); }
    return s;
  }
  function bakerLine(q) {
    var p = el("p", "quote");
    p.appendChild(document.createTextNode("“" + q.text + "” "));
    var src = el("span", null, "— Baker et al., " + q.where);
    src.style.whiteSpace = "nowrap";
    p.appendChild(src);
    return p;
  }

  // ---------- Ring map geometry (from XLab: actor-board.tsx) ----------
  var CX = 480, CY = 350;
  var RADII = { declares: 84, evidence: 150, verifies: 216, undeclared: 278 };
  var VIEW = { x: 0, y: 2, w: 960, h: 696 };
  var NODE_HIT_RADIUS = 18, DRAG_THRESHOLD = 4, BEAM_END_WIDTH = 4.5;
  var HEAD_TIP_INSET = 7, HEAD_LENGTH = 20, HEAD_NOTCH = 13, HEAD_BARB_WIDTH = BEAM_END_WIDTH * 2.5;
  var STEP_DEG = 360 / MAP_SLOTS.length;
  function angleOf(id) { var i = MAP_SLOTS.indexOf(id); return (-90 + STEP_DEG / 2 + STEP_DEG * i) * (Math.PI / 180); }
  function pointOf(id) { var a = angleOf(id), r = RADII[RING_KEY[id]]; return { x: CX + Math.cos(a) * r, y: CY + Math.sin(a) * r }; }
  function normal(dx, dy) { var l = Math.hypot(dx, dy) || 1; return { x: -dy / l, y: dx / l }; }
  function beamPath(from, to, control) {
    var endWidth = BEAM_END_WIDTH, middleWidth = 1.4;
    var sN = normal(control.x - from.x, control.y - from.y), eN = normal(to.x - control.x, to.y - control.y), mN = normal(to.x - from.x, to.y - from.y);
    var off = 2 * middleWidth - endWidth;
    return ["M " + (from.x + sN.x * endWidth) + " " + (from.y + sN.y * endWidth),
      "Q " + (control.x + mN.x * off) + " " + (control.y + mN.y * off), (to.x + eN.x * endWidth) + " " + (to.y + eN.y * endWidth),
      "L " + (to.x - eN.x * endWidth) + " " + (to.y - eN.y * endWidth),
      "Q " + (control.x - mN.x * off) + " " + (control.y - mN.y * off), (from.x - sN.x * endWidth) + " " + (from.y - sN.y * endWidth) + " Z"].join(" ");
  }
  function edgeControl(from, to, bend) {
    var mid = { x: (from.x + to.x) / 2, y: (from.y + to.y) / 2 };
    var pulled = { x: mid.x + (CX - mid.x) * 0.35, y: mid.y + (CY - mid.y) * 0.35 };
    if (!bend) return pulled;
    var dx = to.x - from.x, dy = to.y - from.y, l = Math.hypot(dx, dy) || 1;
    return { x: pulled.x + (-dy / l) * bend, y: pulled.y + (dx / l) * bend };
  }
  function arrowheadPath(control, to) {
    var dx = to.x - control.x, dy = to.y - control.y, l = Math.hypot(dx, dy) || 1, ux = dx / l, uy = dy / l, nx = -uy, ny = ux;
    var tip = { x: to.x - ux * HEAD_TIP_INSET, y: to.y - uy * HEAD_TIP_INSET };
    var at = function (back, side) { return (tip.x - ux * back + nx * side) + " " + (tip.y - uy * back + ny * side); };
    return ["M " + tip.x + " " + tip.y, "Q " + at(10, 2.75) + " " + at(HEAD_LENGTH, HEAD_BARB_WIDTH), "L " + at(HEAD_NOTCH, 0), "L " + at(HEAD_LENGTH, -HEAD_BARB_WIDTH), "Q " + at(10, -2.75) + " " + tip.x + " " + tip.y, "Z"].join(" ");
  }
  function trimForHead(p, control) {
    var dx = control.x - p.x, dy = control.y - p.y, l = Math.hypot(dx, dy) || 1, d = Math.min(HEAD_TIP_INSET + HEAD_NOTCH, l / 2);
    return { x: p.x + (dx / l) * d, y: p.y + (dy / l) * d };
  }
  var EDGE_PAINT = {
    drawn: { stroke: "#b87018", width: 1.5 },
    right: { stroke: "#b87018", width: 1.75 },
    wrong: { stroke: "#1a1a1a", width: 1.5, dash: "2 3" },
    missed: { stroke: "#5a5a5a", width: 1.25, dash: "6 4" }
  };
  function nearestActor(point, except) {
    var nearest = null, best = NODE_HIT_RADIUS;
    ACTORS.forEach(function (a) {
      if (a.id === except) return;
      var p = pointOf(a.id), d = Math.hypot(point.x - p.x, point.y - p.y);
      if (d <= best) { nearest = a.id; best = d; }
    });
    return nearest;
  }

  // ---------- Interactions ----------
  function toggleEdge(id) {
    update(function (s) { if (has(s.edges, id)) s.edges = s.edges.filter(function (e) { return e !== id; }); else s.edges.push(id); });
  }
  function canDraw() { return !state.edgesDone; }
  function chooseActor(id) {
    if (!canDraw()) return;
    if (ui.source === id) { ui.source = null; render(); return; }
    if (ui.source) { var from = ui.source; ui.source = null; toggleEdge(edgeId(from, id)); return; }
    ui.source = id; render();
  }

  function renderMap(root) {
    var box = el("div", "mapbox");
    var interactive = canDraw();
    var lens = state.edgesDone ? ui.lens : null;
    var s = svg("svg", { viewBox: VIEW.x + " " + VIEW.y + " " + VIEW.w + " " + VIEW.h, role: interactive ? "group" : "img" });
    s.setAttribute("aria-label", interactive
      ? "Interactive actor map. Drag from an evidence source to the actor the evidence concerns, or select the two points in order."
      : "Concentric actor map: the regulated training run at the centre, actors on four rings around it: who declares, who holds evidence, who verifies, and what no declaration covers. Edges join actors that can produce evidence about one another.");

    RINGS.slice().reverse().forEach(function (ring) {
      s.appendChild(svg("circle", { cx: CX, cy: CY, r: RADII[ring.id], fill: "none", stroke: "#e8e5df", "stroke-width": 1 }));
      var t = svg("text", { x: CX, y: CY - RADII[ring.id] - 10, "text-anchor": "middle", fill: "#5a5a5a", "font-size": 10, "letter-spacing": "0.08em" });
      t.textContent = ring.name.toUpperCase();
      s.appendChild(t);
    });
    s.appendChild(svg("circle", { cx: CX, cy: CY, r: 4, fill: "#b87018" }));
    var c1 = svg("text", { x: CX, y: CY + 20, "text-anchor": "middle", fill: "#1a1a1a", "font-size": 11, "font-weight": 600 }); c1.textContent = CENTRE.label; s.appendChild(c1);
    var c2 = svg("text", { x: CX, y: CY + 34, "text-anchor": "middle", fill: "#5a5a5a", "font-size": 10 }); c2.textContent = CENTRE.sub; s.appendChild(c2);

    var score = scoreEdges(state.edges, KEY_EDGE_IDS);
    var edges = !state.edgesDone
      ? state.edges.map(function (id) { return { id: id, state: "drawn" }; })
      : score.found.map(function (id) { return { id: id, state: "right" }; })
        .concat(score.reversed.map(function (id) { return { id: id, state: "wrong" }; }))
        .concat(score.extra.map(function (id) { return { id: id, state: "wrong" }; }))
        .concat(score.missed.map(function (id) { return { id: id, state: "missed" }; }));
    var edgeIndex = {}; edges.forEach(function (e) { edgeIndex[e.id] = e; });
    edges.forEach(function (edge) {
      var e = splitEdge(edge.id), a = pointOf(e.from), b = pointOf(e.to);
      var partner = edgeIndex[edgeId(e.to, e.from)];
      var twoHeaded = partner !== undefined && partner.state === edge.state;
      if (twoHeaded && edgeId(e.to, e.from) < edge.id) return;
      var paint = EDGE_PAINT[edge.state];
      var control = edgeControl(a, b, partner !== undefined && !twoHeaded ? 12 : 0);
      var beam = beamPath(twoHeaded ? trimForHead(a, control) : a, trimForHead(b, control), control);
      var g = svg("g");
      g.appendChild(svg("path", { d: beam, fill: paint.dash ? "none" : paint.stroke, stroke: paint.dash ? paint.stroke : "none", "stroke-width": paint.width, "stroke-dasharray": paint.dash || "none", "stroke-linecap": "round", "stroke-linejoin": "round" }));
      g.appendChild(svg("path", { d: arrowheadPath(control, b), fill: paint.stroke }));
      if (twoHeaded) g.appendChild(svg("path", { d: arrowheadPath(control, a), fill: paint.stroke }));
      s.appendChild(g);
    });

    var draftLayer = svg("g", { fill: "#b87018", "pointer-events": "none" });
    s.appendChild(draftLayer);

    ACTORS.forEach(function (actor) {
      var p = pointOf(actor.id), angle = angleOf(actor.id), outward = Math.cos(angle) >= 0 ? 1 : -1;
      var lit = lens ? has(actor.roles, lens) : false;
      var absent = !!ABSENT[actor.id];
      var selected = interactive && ui.source === actor.id;
      var g = svg("g", { class: "node" + (interactive ? " is-interactive" : ""), "data-actor-id": actor.id });
      if (interactive) {
        g.setAttribute("role", "button"); g.setAttribute("tabindex", "0"); g.setAttribute("aria-pressed", selected ? "true" : "false");
        g.setAttribute("data-key", "node:" + actor.id);
        g.setAttribute("aria-label", ui.source && ui.source !== actor.id ? "Draw an edge from " + labelOf(ui.source) + " to " + actor.label
          : selected ? actor.label + ". Clear the selected source." : actor.label + ". Select as the evidence source.");
        g.appendChild(svg("circle", { class: "hit", cx: p.x, cy: p.y, r: NODE_HIT_RADIUS, fill: "transparent", "pointer-events": "all" }));
        wireNode(g, s, actor.id, draftLayer);
      }
      if (selected) g.appendChild(svg("circle", { cx: p.x, cy: p.y, r: 11, fill: "none", stroke: "#b87018", "stroke-width": 2, "stroke-dasharray": "3 2", "pointer-events": "none" }));
      var dot = svg("circle", { cx: p.x, cy: p.y, r: absent ? 7 : lit ? 8 : 6.5, "pointer-events": "none", fill: absent ? "none" : lit ? "#b87018" : "#1a1a1a", opacity: lens && !lit ? 0.3 : 1 });
      if (absent) { dot.setAttribute("stroke", "#5a5a5a"); dot.setAttribute("stroke-width", 1.25); dot.setAttribute("stroke-dasharray", "3 2"); }
      g.appendChild(dot);
      var t = svg("text", { x: p.x + outward * 14, y: p.y + 3.5, "text-anchor": outward > 0 ? "start" : "end", "font-size": 11, "font-weight": lit || selected ? 600 : 400, fill: lit ? "#b87018" : "#1a1a1a", opacity: lens && !lit ? 0.35 : 1, "pointer-events": "none" });
      t.textContent = actor.label;
      g.appendChild(t);
      s.appendChild(g);
    });
    box.appendChild(s);

    if (interactive) {
      var status = para("note"); status.setAttribute("aria-live", "polite"); status.id = "map-status";
      status.textContent = ui.source
        ? labelOf(ui.source) + " is the source. Choose the actor its evidence concerns."
        : "Draw an edge from the actor that produces the evidence to the actor the evidence concerns.";
      box.appendChild(status);
    }
    if (state.edgesDone) {
      var legend = el("div", "legend");
      legend.appendChild(legendItem("right", "solid: in the key"));
      legend.appendChild(legendItem("wrong", "dotted: reversed or not in the key"));
      legend.appendChild(legendItem("missed", "dashed: in the key, not drawn"));
      box.appendChild(legend);
    }
    root.appendChild(box);
  }
  function legendItem(kind, text) {
    var paint = EDGE_PAINT[kind];
    var sp = el("span");
    var s = svg("svg", { viewBox: "0 0 28 10", "aria-hidden": "true" });
    s.appendChild(svg("line", { x1: 1, y1: 5, x2: 27, y2: 5, stroke: paint.stroke, "stroke-width": 2, "stroke-dasharray": paint.dash || "none" }));
    sp.appendChild(s); sp.appendChild(document.createTextNode(text));
    return sp;
  }

  function pointerPoint(svgEl, event) {
    var rect = svgEl.getBoundingClientRect();
    var w = rect.width || VIEW.w, h = rect.height || VIEW.h;
    return { x: VIEW.x + ((event.clientX - rect.left) / w) * VIEW.w, y: VIEW.y + ((event.clientY - rect.top) / h) * VIEW.h };
  }
  function drawDraft(layer, from, end) {
    while (layer.firstChild) layer.removeChild(layer.firstChild);
    if (!end) return;
    var start = pointOf(from);
    if (Math.hypot(end.x - start.x, end.y - start.y) <= 1) return;
    var control = edgeControl(start, end, 0);
    layer.appendChild(svg("path", { d: beamPath(start, trimForHead(end, control), control) }));
    layer.appendChild(svg("path", { d: arrowheadPath(control, end) }));
  }
  function setHover(svgEl, id) {
    var nodes = svgEl.querySelectorAll(".node");
    for (var i = 0; i < nodes.length; i++) {
      var old = nodes[i].querySelector(".hover-ring");
      if (old) nodes[i].removeChild(old);
      if (id && nodes[i].getAttribute("data-actor-id") === id) {
        var p = pointOf(id);
        nodes[i].insertBefore(svg("circle", { class: "hover-ring", cx: p.x, cy: p.y, r: 11, fill: "none", stroke: "#b87018", "stroke-width": 2, "pointer-events": "none" }), nodes[i].firstChild.nextSibling);
      }
    }
  }
  function wireNode(g, svgEl, id, draftLayer) {
    g.addEventListener("pointerdown", function (event) {
      if (!canDraw()) return;
      event.preventDefault();
      try { g.setPointerCapture(event.pointerId); } catch (e) {}
      var p = pointerPoint(svgEl, event);
      ui.draft = { from: id, hover: null, pointerId: event.pointerId, startX: p.x, startY: p.y, x: p.x, y: p.y };
    });
    g.addEventListener("pointermove", function (event) {
      var d = ui.draft;
      if (!d || d.pointerId !== event.pointerId) return;
      event.preventDefault();
      var p = pointerPoint(svgEl, event);
      d.x = p.x; d.y = p.y;
      var moved = Math.hypot(p.x - d.startX, p.y - d.startY) >= DRAG_THRESHOLD;
      var target = moved ? nearestActor(p, d.from) : null;
      if (target !== d.hover) { d.hover = target; setHover(svgEl, target); }
      drawDraft(draftLayer, d.from, moved ? (target ? pointOf(target) : p) : null);
    });
    g.addEventListener("pointerup", function (event) {
      var d = ui.draft;
      if (!d || d.pointerId !== event.pointerId) return;
      event.preventDefault();
      var p = pointerPoint(svgEl, event);
      var moved = Math.hypot(p.x - d.startX, p.y - d.startY) >= DRAG_THRESHOLD;
      var target = nearestActor(p, d.from);
      try { g.releasePointerCapture(event.pointerId); } catch (e) {}
      ui.draft = null;
      if (moved && target) { ui.source = null; toggleEdge(edgeId(d.from, target)); }
      else if (moved) { ui.source = d.from; render(); }
      else { chooseActor(d.from); }
    });
    g.addEventListener("pointercancel", function () { ui.draft = null; drawDraft(draftLayer, id, null); setHover(svgEl, null); });
    g.addEventListener("keydown", function (event) {
      if (event.key !== "Enter" && event.key !== " ") return;
      event.preventDefault();
      chooseActor(id);
    });
    // Click fallback for environments without pointer events (tap = select source, tap again = target).
    g.addEventListener("click", function (event) {
      if (typeof window.PointerEvent !== "undefined") return;
      event.preventDefault();
      chooseActor(id);
    });
  }

  // ---------- Sections ----------
  function renderDrawing(root) {
    var wrap = el("div", "stack");
    var src = el("div");
    src.appendChild(para("medium", "Who can produce the evidence?"));
    var chips = el("div", "chips");
    ACTORS.forEach(function (a) {
      var out = state.edges.filter(function (e) { return e.indexOf(a.id + ">") === 0; }).length;
      var b = btn(a.label + (out ? " " : ""), "chip" + (ui.source === a.id ? " is-active" : ""), function () { ui.source = a.id; render(); }, "src:" + a.id);
      if (out) b.appendChild(el("span", "muted", String(out)));
      b.setAttribute("aria-pressed", ui.source === a.id ? "true" : "false");
      b.setAttribute("aria-label", "Draw from " + a.label + (out ? ", " + out + " drawn" : ""));
      chips.appendChild(b);
    });
    src.appendChild(chips);
    wrap.appendChild(src);

    if (ui.source) {
      var tgt = el("div");
      tgt.appendChild(para("medium", "About whom? " + labelOf(ui.source) + " can show a verifier something about…"));
      var tchips = el("div", "chips");
      ACTORS.forEach(function (a) {
        if (a.id === ui.source) return;
        var id = edgeId(ui.source, a.id), on = has(state.edges, id);
        var b = btn((on ? "✓ " : "") + a.label, "chip" + (on ? " is-active" : ""), function () { toggleEdge(id); }, "tgt:" + a.id);
        b.setAttribute("aria-pressed", on ? "true" : "false");
        b.setAttribute("aria-label", labelOf(ui.source) + " can show a verifier something about " + a.label);
        tchips.appendChild(b);
      });
      tgt.appendChild(tchips);
      wrap.appendChild(tgt);
    }

    if (state.edges.length) {
      var card = el("div", "card");
      card.appendChild(para("eyebrow", state.edges.length + " edge" + (state.edges.length === 1 ? "" : "s") + " drawn"));
      var ul = el("ul", "tight"); ul.style.marginTop = "8px";
      state.edges.forEach(function (id) {
        var li = el("li");
        var b = btn(edgeLabel(id) + " ", "link", function () { toggleEdge(id); }, "rm:" + id);
        b.appendChild(el("span", "muted", "✕"));
        b.setAttribute("aria-label", "Remove " + edgeLabel(id));
        li.appendChild(b); ul.appendChild(li);
      });
      card.appendChild(ul);
      wrap.appendChild(card);
    }

    var foot = el("div", "row");
    var commit = btn("Commit the edges", "primary", function () { ui.source = null; update(function (s) { s.edgesDone = true; }); }, "commit-edges");
    commit.disabled = !state.edges.length;
    foot.appendChild(commit);
    wrap.appendChild(foot);
    root.appendChild(wrap);
  }

  function renderVerdict(root) {
    var score = scoreEdges(state.edges, KEY_EDGE_IDS);
    var wrap = el("div", "stack");
    var head = el("div", "row");
    var line = el("p");
    line.appendChild(inline([el("span", "strong", score.found.length + " of " + EDGE_KEY.length), " edges in the key." +
      (score.reversed.length ? " " + score.reversed.length + " drawn the other way round." : "") +
      (score.extra.length ? " " + score.extra.length + " the key does not have (" + score.extra.map(edgeLabel).join("; ") + ")." : "")]));
    head.appendChild(line);
    head.appendChild(btn("Edit my edges", "", function () { ui.source = null; update(function (s) { s.edgesDone = false; }); }, "edit-edges"));
    wrap.appendChild(head);

    var ol = el("ol", "list");
    EDGE_KEY.forEach(function (edge) {
      var id = edgeId(edge.from, edge.to);
      var sg = SUBGOAL_BY_ID[edge.subgoal];
      var got = has(score.found, id);
      var flipped = has(score.reversed, edgeId(edge.to, edge.from));
      var li = el("li");
      var l = el("p", "verdict-line");
      l.appendChild(icon(got ? "ok" : "alert"));
      var txt = el("span");
      txt.appendChild(el("span", "medium", edgeLabel(id)));
      txt.appendChild(el("span", "muted", " · " + sg.label + " " + sg.name));
      if (!got) txt.appendChild(el("span", "muted", flipped ? " · you drew it the other way round" : " · not drawn"));
      l.appendChild(txt);
      li.appendChild(l);
      var what = para("muted small", edge.line); what.style.marginTop = "2px"; what.style.paddingLeft = "22px";
      li.appendChild(what);
      ol.appendChild(li);
    });
    wrap.appendChild(ol);

    var row = el("div", "chips");
    row.appendChild(el("span", "muted small", "Light up a role:"));
    ROLES.forEach(function (role) {
      var b = btn(role.name, "chip" + (ui.lens === role.id ? " is-active" : ""), function () { ui.lens = ui.lens === role.id ? null : role.id; render(); }, "lens:" + role.id);
      b.setAttribute("aria-pressed", ui.lens === role.id ? "true" : "false");
      row.appendChild(b);
    });
    wrap.appendChild(row);
    root.appendChild(wrap);
  }

  // ---------- Render ----------
  var app = document.getElementById("app");
  function render() {
    var active = document.activeElement, key = active && active.getAttribute ? active.getAttribute("data-key") : null;
    while (app.firstChild) app.removeChild(app.firstChild);
    renderMap(app);
    if (state.edgesDone) renderVerdict(app); else renderDrawing(app);
    if (key) { var n = app.querySelector('[data-key="' + key + '"]'); if (n && n.focus) n.focus(); }
  }

  function hydrate(saved, meta) {
    state = prune(saved);
    completed = !!(meta && meta.completed);
    render();
    // A state saved before the widget was slimmed can carry committed edges without the old completion step.
    if (window.Lens && state.edgesDone && !completed) persist();
  }

  if (window.Lens) {
    render();
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE_KEY)); } catch (e) {}
    hydrate(raw, null);
  }
</script>
</body>
</html>


---
id: '41b373f6-1523-4cf1-ae5d-0cd6b1ba468d'
title: Agent architecture, where compromises happen
summary_for_tutor: "Buck Shlegeris's agent architecture diagram with his threat scenarios drawn on it. Five boxes stay on screen throughout (user, scaffold server, inference server, execution server, internet) joined by the ordinary flow arrows, and the learner switches between seven views of the same picture: the plain architecture, the monitor/audit/defer band on the scaffold, the three weight-exfiltration routes (copying weights out of the execution server, hacking the inference server, committing code that compromises another server), and the two rogue-internal-deployment shapes (a self-written agent loop on the execution machine's own GPUs, and a rogue scaffold that calls the real inference API). Each view carries one line naming what is drawn; the post's own explanation of why each route is easy or hard sits in the article text on the page around the widget, and the page's open questions ask about the three-server split, where safety mechanisms sit and what rogue internal deployments look like. The learner has finished when they have opened all seven views. If a learner is stuck, ask which machine the attack path starts on and which one holds the weights."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from XLab Tracks, AI Control, "A basic systems architecture for AI agents that do autonomous research" (demo id agent-architecture-threats). Rewritten as vanilla HTML/SVG/JS in the Lens look. -->
<style>
:root {
  --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10; --panel: #faf8f3;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
[hidden] { display: none !important; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin-bottom: 10px; }
.frame { border: 1px solid var(--border); border-radius: 8px; background: var(--bg); overflow: hidden; }
.views { display: flex; flex-wrap: wrap; gap: 6px; padding: 12px 12px 0; }
.view { font: inherit; font-size: 12.5px; color: var(--muted); border: 1px solid var(--border); border-radius: 999px; background: #fff; padding: 5px 10px; cursor: pointer; }
.view:hover { background: var(--panel); border-color: #cfc9bf; }
.view.seen { color: var(--text); }
.view.now { border-color: var(--accent); color: var(--accent-hover); background: rgba(184, 112, 24, 0.08); }
.canvas { overflow-x: auto; padding: 12px; }
svg { display: block; width: 100%; min-width: 420px; height: auto; }
.node-box { fill: #ffffff; stroke: var(--border); stroke-width: 1.5; }
.node-box.is-cloud { fill: var(--panel); stroke-dasharray: 5 4; }
.node-title { fill: var(--text); font-family: var(--font-heading); font-size: 11px; font-weight: 600; }
.node-sub { fill: var(--muted); font-size: 9px; }
.flow { fill: none; stroke: #9a958c; stroke-width: 1.5; }
.flow-label { fill: var(--muted); font-size: 8.5px; }
.pill { fill: #ffffff; stroke: #9a958c; stroke-width: 1; }
.pill-text { fill: var(--muted); font-size: 8px; font-weight: 500; }
.ov { opacity: 0; transition: opacity 0.35s ease; }
.ov.is-on { opacity: 1; }
.ov .pill { fill: rgba(184, 112, 24, 0.12); stroke: var(--accent); }
.ov .pill-text { fill: var(--accent-hover); }
.hit { fill: none; stroke: var(--accent); stroke-width: 2; }
.hit.is-loop { stroke-dasharray: 4 3; }
.hit-label { fill: var(--accent-hover); font-size: 8.5px; }
.caption { margin: 0; padding: 12px 16px; border-top: 1px solid var(--border); background: var(--panel); color: var(--text); }
@media (max-width: 420px) { .views { gap: 5px; } .view { padding: 5px 8px; font-size: 12px; } }
</style>
</head>
<body>
<div class="eyebrow">Agent architecture: where compromises happen</div>
<div class="frame">
  <div class="views" id="views" role="group" aria-label="Choose a view of the diagram"></div>
  <div class="canvas">
    <svg viewBox="0 0 560 340" role="img" aria-label="The user, scaffold server, inference server, execution server and internet, with the post's threat scenarios drawn as attack paths: weight exfiltration, hacking or compromising the inference server, and the two rogue internal deployment variants.">
      <defs>
        <marker id="aat-flow" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="5.5" markerHeight="5.5" orient="auto-start-reverse">
          <path d="M0,0 L8,4 L0,8 z" fill="#9a958c"></path>
        </marker>
        <marker id="aat-hit" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
          <path d="M0,0 L8,4 L0,8 z" fill="#b87018"></path>
        </marker>
      </defs>

      <path class="flow" d="M 116 73 L 186 73" marker-end="url(#aat-flow)" marker-start="url(#aat-flow)"></path>
      <path class="flow" d="M 334 64 L 404 56" marker-end="url(#aat-flow)" marker-start="url(#aat-flow)"></path>
      <path class="flow" d="M 274 120 L 344 172" marker-end="url(#aat-flow)" marker-start="url(#aat-flow)"></path>
      <text class="flow-label" x="369" y="56" text-anchor="middle">LLM API</text>
      <text class="flow-label" x="312" y="149" text-anchor="middle">actions and results</text>

      <g>
        <rect class="node-box" x="20" y="46" width="92" height="54" rx="10"></rect>
        <text class="node-title" x="66" y="64" text-anchor="middle">User</text>
        <text class="node-sub" x="66" y="79" text-anchor="middle">submits tasks</text>
      </g>
      <g>
        <rect class="node-box" x="190" y="30" width="140" height="86" rx="10"></rect>
        <text class="node-title" x="260" y="48" text-anchor="middle">Scaffold server</text>
        <text class="node-sub" x="260" y="63" text-anchor="middle">agent loop and state</text>
        <text class="node-sub" x="260" y="75" text-anchor="middle">parses actions</text>
      </g>
      <g>
        <rect class="node-box" x="408" y="22" width="134" height="78" rx="10"></rect>
        <text class="node-title" x="475" y="40" text-anchor="middle">Inference server</text>
        <text class="node-sub" x="475" y="55" text-anchor="middle">serves the LLM API</text>
        <text class="node-sub" x="475" y="67" text-anchor="middle">holds model weights</text>
        <rect class="pill" x="434" y="80" width="82" height="14" rx="7"></rect>
        <text class="pill-text" x="475" y="90" text-anchor="middle">model weights</text>
      </g>
      <g>
        <rect class="node-box" x="300" y="176" width="150" height="92" rx="10"></rect>
        <text class="node-title" x="375" y="194" text-anchor="middle">Execution server</text>
        <text class="node-sub" x="375" y="209" text-anchor="middle">sandboxed code runs</text>
        <text class="node-sub" x="375" y="221" text-anchor="middle">tools and GPUs</text>
      </g>
      <g>
        <rect class="node-box is-cloud" x="40" y="196" width="110" height="56" rx="10"></rect>
        <text class="node-title" x="95" y="214" text-anchor="middle">Internet</text>
        <text class="node-sub" x="95" y="229" text-anchor="middle">the outside world</text>
      </g>

      <g class="ov" data-on="1">
        <rect class="pill" x="202" y="90" width="116" height="18" rx="9"></rect>
        <text class="pill-text" x="260" y="103" text-anchor="middle">monitor, audit, defer</text>
      </g>

      <g class="ov" data-on="2">
        <rect class="pill" x="334" y="246" width="82" height="14" rx="7"></rect>
        <text class="pill-text" x="375" y="256" text-anchor="middle">weights (if given)</text>
      </g>
      <g class="ov" data-on="2">
        <path class="hit" d="M 296 240 L 156 228" marker-end="url(#aat-hit)"></path>
      </g>

      <g class="ov" data-on="3">
        <path class="hit" d="M 410 172 C 430 136, 458 140, 464 104" marker-end="url(#aat-hit)"></path>
      </g>
      <g class="ov" data-on="3 4">
        <path class="hit" d="M 406 92 C 230 152, 220 150, 130 192" marker-end="url(#aat-hit)"></path>
      </g>
      <g class="ov" data-on="4">
        <path class="hit" d="M 428 172 C 468 128, 504 144, 508 104" marker-end="url(#aat-hit)"></path>
        <text class="hit-label" text-anchor="middle">
          <tspan x="516" y="142">PRs deployed to</tspan>
          <tspan x="516" y="153">the servers</tspan>
        </text>
      </g>

      <g class="ov" data-on="5">
        <path class="hit is-loop" d="M 440 200 C 492 206, 492 246, 440 252" marker-end="url(#aat-hit)"></path>
        <text class="hit-label" x="476" y="230" text-anchor="start">own agent loop</text>
      </g>

      <g class="ov" data-on="6">
        <path class="hit is-loop" d="M 418 172 C 450 124, 468 148, 474 104" marker-end="url(#aat-hit)"></path>
        <text class="hit-label" text-anchor="middle">
          <tspan x="438" y="136">rogue scaffold's</tspan>
          <tspan x="438" y="147">API queries</tspan>
        </text>
      </g>
    </svg>
  </div>
  <p class="caption" id="caption" aria-live="polite"></p>
</div>

<script>
(function () {
  var VIEWS = [
    { name: "Basic architecture", caption: "The ordinary flow between the user, the scaffold server, the inference server and the execution server." },
    { name: "Safety mechanisms", caption: "Proposed actions are parsed in the scaffold before anything runs, so the checks sit there." },
    { name: "Weights copied out", caption: "Weights sitting on the execution server, copied straight out to the internet." },
    { name: "Inference server hacked", caption: "The execution server hacks the inference server into sending the weights out." },
    { name: "Compromise via committed code", caption: "Code the agent commits is deployed to the other servers, the inference server included." },
    { name: "Rogue agent loop", caption: "An unauthorized agent loop on the execution machine's own GPUs and weights." },
    { name: "Rogue scaffold", caption: "A rogue scaffold on the execution machine, calling the real inference API." }
  ];

  var overlays = [].slice.call(document.querySelectorAll('.ov')).map(function (el) {
    return { el: el, on: el.getAttribute('data-on').split(' ').map(Number) };
  });

  var captionEl = document.getElementById('caption');
  var viewsEl = document.getElementById('views');

  var current = 0;
  var seen = [0];
  var completed = false;
  var viewButtons = [];

  VIEWS.forEach(function (v, i) {
    var b = document.createElement('button');
    b.type = 'button';
    b.className = 'view';
    b.textContent = v.name;
    b.addEventListener('click', function () { go(i); });
    viewsEl.appendChild(b);
    viewButtons.push(b);
  });

  function summary() {
    var opened = seen.slice().sort(function (a, b) { return a - b; })
      .map(function (i) { return VIEWS[i].name; });
    return 'Agent architecture diagram. Currently showing "' + VIEWS[current].name +
      '". Views opened so far (' + opened.length + ' of ' + VIEWS.length + '): ' + opened.join('; ') + '.';
  }

  function render() {
    overlays.forEach(function (o) {
      if (o.on.indexOf(current) !== -1) { o.el.classList.add('is-on'); }
      else { o.el.classList.remove('is-on'); }
    });
    captionEl.textContent = VIEWS[current].caption;
    viewButtons.forEach(function (b, i) {
      b.className = 'view' + (seen.indexOf(i) !== -1 ? ' seen' : '') + (i === current ? ' now' : '');
      b.setAttribute('aria-pressed', i === current ? 'true' : 'false');
    });
  }

  function persist() {
    if (!window.Lens) { return; }
    Lens.saveState({ current: current, seen: seen }, summary());
    if (seen.length === VIEWS.length && !completed) {
      completed = true;
      Lens.complete();
    }
  }

  function go(i) {
    if (i < 0 || i >= VIEWS.length) { return; }
    current = i;
    if (seen.indexOf(i) === -1) { seen.push(i); }
    render();
    persist();
  }

  if (window.Lens && Lens.onState) {
    Lens.onState(function (state, meta) {
      if (state && typeof state.current === 'number') {
        current = Math.min(Math.max(state.current, 0), VIEWS.length - 1);
        seen = Array.isArray(state.seen) ? state.seen.filter(function (i) {
          return typeof i === 'number' && i >= 0 && i < VIEWS.length;
        }) : [current];
        if (seen.indexOf(current) === -1) { seen.push(current); }
      }
      if (meta && meta.completed) { completed = true; }
      render();
    });
  }

  render();
})();
</script>
</body>
</html>

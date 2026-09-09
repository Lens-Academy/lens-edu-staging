---
id: '41b373f6-1523-4cf1-ae5d-0cd6b1ba468d'
title: Agent architecture, where compromises happen
summary_for_tutor: A seven-step walkthrough of Buck Shlegeris's agent architecture diagram. Five boxes stay on screen throughout (user, scaffold server, inference server, execution server, internet) joined by the ordinary flow arrows; the learner steps forward and back and each step lights up one overlay on the same picture. Step 1 is the plain architecture. Step 2 puts the monitor/audit/defer band on the scaffold, where actions are parsed before execution. Steps 3 to 5 draw the three weight-exfiltration routes, copying weights straight out of the execution server, hacking the inference server, and committing code that compromises another server. Steps 6 and 7 draw the two rogue-internal-deployment shapes, a self-written agent loop on the execution machine's own GPUs and a rogue scaffold that calls the real inference API. The learner has finished when they have opened all seven steps. If a learner is stuck, ask which machine the attack path starts on and which one holds the weights.
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
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin-bottom: 10px; }
.frame { border: 1px solid var(--border); border-radius: 8px; background: var(--bg); overflow: hidden; }
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
.readout { border-top: 1px solid var(--border); background: var(--panel); padding: 14px 16px; }
.step-no { font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
.step-label { font-family: var(--font-heading); font-size: 16px; font-weight: 600; margin: 2px 0 6px; }
.caption { margin: 0; color: var(--text); min-height: 4.5em; }
.controls { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; margin-top: 12px; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; }
button:hover:not(:disabled) { background: var(--panel); border-color: #cfc9bf; }
button:disabled { color: #a8a29a; cursor: default; }
button.primary { border-color: var(--accent); color: var(--accent-hover); }
button.primary:hover:not(:disabled) { background: rgba(184, 112, 24, 0.08); }
.spacer { flex: 1 1 auto; }
.dots { display: flex; gap: 5px; }
.dot { width: 7px; height: 7px; border-radius: 50%; border: 1px solid #9a958c; background: #fff; padding: 0; }
.dot.seen { background: #9a958c; }
.dot.now { border-color: var(--accent); background: var(--accent); }
.done { margin-top: 10px; font-size: 13px; color: var(--accent-hover); }
.done[hidden] { display: none; }
@media (max-width: 420px) { .controls { gap: 6px; } button { padding: 7px 10px; } }
</style>
</head>
<body>
<div class="eyebrow">Agent architecture: where compromises happen</div>
<div class="frame">
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

  <div class="readout">
    <div class="step-no" id="stepno">Step 1 of 7</div>
    <h2 class="step-label" id="steplabel"></h2>
    <p class="caption" id="caption"></p>
    <div class="controls">
      <button id="back" type="button">Back</button>
      <button id="next" type="button" class="primary">Next</button>
      <span class="spacer"></span>
      <div class="dots" id="dots" role="group" aria-label="Jump to a step"></div>
      <button id="reset" type="button">Reset</button>
    </div>
    <p class="done" id="done" hidden>You have opened every step of the diagram.</p>
  </div>
</div>

<script>
(function () {
  var STEPS = [
    {
      label: "The basic architecture",
      caption: "Three responsibilities almost surely live on logically different computers: the inference server that serves the LLM API (and holds the weights), the scaffold server that maintains the agent loop's state, and the execution server where the agent's code actually runs. The user talks to the scaffold."
    },
    {
      label: "Where safety mechanisms sit",
      caption: "The scaffold parses the LLM's proposed action before anything executes, which is the natural place to insert safety mechanisms. It can query a weaker trusted model about the action, then execute it, flag it for human review (auditing), or discard it and select a new one (defer-to-trusted)."
    },
    {
      label: "Weight exfiltration from the execution server",
      caption: "If the agent has model weights on its execution server, it could just copy them to a remote server. Hard to do straightforwardly: it's unclear why the agent would have enough egress bandwidth (see upload limits), and it needs somewhere to send them."
    },
    {
      label: "Hacking the inference server",
      caption: "The agent issues commands that hack an inference server and cause it to exfiltrate the weights, say if outgoing connections from the execution server and incoming connections to the inference server aren't properly secured. This should be pretty simple to prevent."
    },
    {
      label: "Compromise via committed code",
      caption: "The agent commits code that compromises one of the other servers. The inference server is a natural target since it definitely has the weights. Standard security helps (inference servers don't need outgoing connections), but modifying the codebase or infrastructure is probably the best self-exfiltration strategy that needs no help from employees."
    },
    {
      label: "Rogue agent loop on local GPUs",
      caption: "The easiest rogue internal deployment to imagine: the model writes its own agent loop on the execution machine, running inference on the weights and GPUs it was given for its research task. An unauthorized agent with none of your intended safety measures."
    },
    {
      label: "Rogue scaffold via the inference API",
      caption: "Alternatively, the model builds a rogue scaffold on the execution machine that calls the inference server. This seems easier to prevent: basic monitoring on the inference API should catch queries that are blatantly being used to implement unauthorized scaffolds."
    }
  ];

  var overlays = [].slice.call(document.querySelectorAll('.ov')).map(function (el) {
    return { el: el, on: el.getAttribute('data-on').split(' ').map(Number) };
  });

  var stepNoEl = document.getElementById('stepno');
  var labelEl = document.getElementById('steplabel');
  var captionEl = document.getElementById('caption');
  var backBtn = document.getElementById('back');
  var nextBtn = document.getElementById('next');
  var resetBtn = document.getElementById('reset');
  var dotsEl = document.getElementById('dots');
  var doneEl = document.getElementById('done');

  var current = 0;
  var seen = [0];
  var completed = false;
  var dotButtons = [];

  STEPS.forEach(function (s, i) {
    var b = document.createElement('button');
    b.type = 'button';
    b.className = 'dot';
    b.title = s.label;
    b.setAttribute('aria-label', 'Step ' + (i + 1) + ': ' + s.label);
    b.addEventListener('click', function () { go(i); });
    dotsEl.appendChild(b);
    dotButtons.push(b);
  });

  function summary() {
    var opened = seen.slice().sort(function (a, b) { return a - b; })
      .map(function (i) { return STEPS[i].label; });
    return 'Agent architecture walkthrough. Currently on step ' + (current + 1) + ' of ' + STEPS.length +
      ', "' + STEPS[current].label + '". Steps opened so far (' + opened.length + ' of ' + STEPS.length + '): ' +
      opened.join('; ') + '.';
  }

  function render() {
    overlays.forEach(function (o) {
      if (o.on.indexOf(current) !== -1) { o.el.classList.add('is-on'); }
      else { o.el.classList.remove('is-on'); }
    });
    stepNoEl.textContent = 'Step ' + (current + 1) + ' of ' + STEPS.length;
    labelEl.textContent = STEPS[current].label;
    captionEl.textContent = STEPS[current].caption;
    backBtn.disabled = current === 0;
    nextBtn.disabled = current === STEPS.length - 1;
    dotButtons.forEach(function (b, i) {
      b.className = 'dot' + (seen.indexOf(i) !== -1 ? ' seen' : '') + (i === current ? ' now' : '');
    });
    doneEl.hidden = seen.length < STEPS.length;
  }

  function persist() {
    if (!window.Lens) { return; }
    Lens.saveState({ current: current, seen: seen }, summary());
    if (seen.length === STEPS.length && !completed) {
      completed = true;
      Lens.complete();
    }
  }

  function go(i) {
    if (i < 0 || i >= STEPS.length) { return; }
    current = i;
    if (seen.indexOf(i) === -1) { seen.push(i); }
    render();
    persist();
  }

  backBtn.addEventListener('click', function () { go(current - 1); });
  nextBtn.addEventListener('click', function () { go(current + 1); });
  resetBtn.addEventListener('click', function () {
    current = 0; seen = [0]; render(); persist();
  });

  if (window.Lens && Lens.onState) {
    Lens.onState(function (state, meta) {
      if (state && typeof state.current === 'number') {
        current = Math.min(Math.max(state.current, 0), STEPS.length - 1);
        seen = Array.isArray(state.seen) ? state.seen.filter(function (i) {
          return typeof i === 'number' && i >= 0 && i < STEPS.length;
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

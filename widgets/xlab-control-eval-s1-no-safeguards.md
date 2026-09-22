---
id: '39898f1d-ae9e-4041-b61f-622df5ddff87'
title: "Scenario 1: straight to production"
summary_for_tutor: >-
  Scenario 1 of the five-scenario control evaluation in "The case for control (1)": a flow diagram of a deployment with no safeguards. Two boxes, U (the untrusted model) and Deployed (merged to production), joined by a single animated arrow from U straight to Deployed. There is nothing else in the path: no monitor, no auditor, no branch. The learner reads it and then answers whether this setup holds the control property. The diagram states the setup only; it does not answer the question, and you should not treat it as evidence either way.
height: auto
tags: []
---
<!doctype html>
<!-- Lens-authored schematic for the five-scenario control evaluation in
     "The case for control (1)". Replaces the plain-text arrow pipelines that
     stood here before. Layout and labels are the lesson's; styling is the Lens look. -->
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --line: #c9c3b8;
  --font-ui: "DM Sans", Arial, sans-serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px 16px 12px; background: #fff; }
.scroll { overflow-x: auto; overflow-y: hidden; }
svg { display: block; width: 100%; min-width: 520px; height: auto; }
.box { fill: #ffffff; stroke: var(--border); stroke-width: 1.5; }
.box.key { fill: #faf8f3; stroke: var(--line); }
.name { font-size: 15px; font-weight: 600; fill: var(--text); }
.sub { font-size: 11px; fill: var(--muted); }
.edge { fill: none; stroke: var(--line); stroke-width: 1.6; }
.flow { fill: none; stroke: var(--accent); stroke-width: 3; stroke-linecap: round;
        stroke-dasharray: 3 17; animation: flow 1.6s linear infinite; }
@keyframes flow { to { stroke-dashoffset: -20; } }
.tag { font-size: 11px; font-weight: 500; fill: var(--muted);
        paint-order: stroke; stroke: #ffffff; stroke-width: 3px; stroke-linejoin: round; }
.legend { margin-top: 10px; font-size: 12px; color: var(--muted); }
@media (prefers-reduced-motion: reduce) { .flow { animation: none; stroke-dasharray: 3 17; } }
@media (max-width: 420px) { body { padding: 12px; } }
</style>
</head>
<body>
<div class="card">
  <div class="scroll">
    <svg viewBox="0 0 660 150" role="img" aria-label="U sends its work straight to deployment, with nothing in between.">
    <defs><marker id="ah" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="var(--line)"/></marker></defs>
    <rect class="box key" x="40" y="44" width="150" height="62" rx="8"/>
    <text class="name" x="115.0" y="72.0" text-anchor="middle">U</text>
    <text class="sub" x="115.0" y="89.0" text-anchor="middle">untrusted model</text>
    <path class="edge" d="M 190 75 H 430" marker-end="url(#ah)"/>
    <path class="flow" d="M 190 75 H 430" style="animation-delay:-0.0s"/>
    <rect class="box" x="430" y="44" width="190" height="62" rx="8"/>
    <text class="name" x="525.0" y="72.0" text-anchor="middle">Deployed</text>
    <text class="sub" x="525.0" y="89.0" text-anchor="middle">merged to production</text>
    </svg>
  </div>
  <p class="legend">U writes production code and merges its own commits. Nothing sits between U and production.</p>
</div>
</body>
</html>

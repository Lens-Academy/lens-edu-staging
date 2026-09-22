---
id: '7fe8ba89-8814-4245-aa8e-f3ed0d6d9ca1'
title: Scenario 4: rewrite the doubtful ones
summary_for_tutor: >-
  Scenario 4 of the five-scenario control evaluation in "The case for control (1)": a flow diagram of what the lesson will later name trusted editing, though the name is not given on the page yet. U feeds into T, which splits three ways: the top 2 percent to H, the human auditors; the next 10 percent into a box reading T rewrites, T's version merges, and on to Deployed; and the bottom 88 percent along a curve straight to the same Deployed box, labelled bottom 88 percent, merged unchanged. The three shares, 2, 10 and 88 percent, are labelled on the branches. The learner reads it and then answers whether the setup holds the control property. The diagram states the setup only; it does not say what score an attack must reach, and it does not mention the usefulness cost.
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
svg { display: block; width: 100%; min-width: 660px; height: auto; }
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
    <svg viewBox="0 0 960 330" role="img" aria-label="T scores every edit; the top two percent are audited, the next ten percent are rewritten by T, the rest merge unchanged.">
    <defs><marker id="ah" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="var(--line)"/></marker></defs>
    <rect class="box key" x="30" y="150" width="130" height="62" rx="8"/>
    <text class="name" x="95.0" y="178.0" text-anchor="middle">U</text>
    <text class="sub" x="95.0" y="195.0" text-anchor="middle">untrusted model</text>
    <path class="edge" d="M 160 181 H 250" marker-end="url(#ah)"/>
    <path class="flow" d="M 160 181 H 250" style="animation-delay:-0.0s"/>
    <rect class="box key" x="250" y="150" width="150" height="62" rx="8"/>
    <text class="name" x="325.0" y="178.0" text-anchor="middle">T</text>
    <text class="sub" x="325.0" y="195.0" text-anchor="middle">trusted monitor</text>
    <path class="edge" d="M 400 168 C 450 168 450 62 500 62" marker-end="url(#ah)"/>
    <path class="flow" d="M 400 168 C 450 168 450 62 500 62" style="animation-delay:-0.2s"/>
    <text class="tag" x="452" y="108" text-anchor="middle">top 2%</text>
    <rect class="box key" x="500" y="32" width="150" height="62" rx="8"/>
    <text class="name" x="575.0" y="60.0" text-anchor="middle">H</text>
    <text class="sub" x="575.0" y="77.0" text-anchor="middle">human auditors</text>
    <path class="edge" d="M 400 181 H 500" marker-end="url(#ah)"/>
    <path class="flow" d="M 400 181 H 500" style="animation-delay:-0.5s"/>
    <text class="tag" x="450" y="172" text-anchor="middle">next 10%</text>
    <rect class="box key" x="500" y="150" width="170" height="62" rx="8"/>
    <text class="name" x="585.0" y="178.0" text-anchor="middle">T rewrites</text>
    <text class="sub" x="585.0" y="195.0" text-anchor="middle">T's version merges</text>
    <path class="edge" d="M 670 181 H 760" marker-end="url(#ah)"/>
    <path class="flow" d="M 670 181 H 760" style="animation-delay:-0.8s"/>
    <path class="edge" d="M 400 194 C 510 300 700 305 800 214" marker-end="url(#ah)"/>
    <path class="flow" d="M 400 194 C 510 300 700 305 800 214" style="animation-delay:-1.1s"/>
    <text class="tag" x="575" y="296" text-anchor="middle">bottom 88%, merged unchanged</text>
    <rect class="box" x="760" y="150" width="180" height="62" rx="8"/>
    <text class="name" x="850.0" y="178.0" text-anchor="middle">Deployed</text>
    <text class="sub" x="850.0" y="195.0" text-anchor="middle">merged to production</text>
    </svg>
  </div>
  <p class="legend">T scores every edit. The top 2% go to H. The next 10% are rewritten by T, which merges its own version. The bottom 88% merge untouched.</p>
</div>
</body>
</html>

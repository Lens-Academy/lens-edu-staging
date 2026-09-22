---
id: 'a693d913-dfa1-46ee-ae07-ebafe1cb5a91'
title: Scenario 2: every edit is monitored
summary_for_tutor: >-
  Scenario 2 of the five-scenario control evaluation in "The case for control (1)": a flow diagram of what the lesson will later name trusted monitoring, though the name is not given on the page yet. U feeds into T, the trusted monitor, which scores every edit for suspicion. T then splits into two animated branches: the top 2 percent go to H, the human auditors, and on to a box reading Blocked if malicious; the remaining 98 percent go straight to Deployed, merged to production. The learner reads it and then answers whether this setup holds the control property and what that depends on. The diagram states the setup only; it does not answer the question, and it shows nothing about T's accuracy or the U-to-T capability gap.
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
svg { display: block; width: 100%; min-width: 640px; height: auto; }
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
    <svg viewBox="0 0 940 290" role="img" aria-label="U's edits are scored by T; the top two percent go to human auditors, the rest deploy.">
    <defs><marker id="ah" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="var(--line)"/></marker></defs>
    <rect class="box key" x="30" y="118" width="130" height="62" rx="8"/>
    <text class="name" x="95.0" y="146.0" text-anchor="middle">U</text>
    <text class="sub" x="95.0" y="163.0" text-anchor="middle">untrusted model</text>
    <path class="edge" d="M 160 149 H 250" marker-end="url(#ah)"/>
    <path class="flow" d="M 160 149 H 250" style="animation-delay:-0.0s"/>
    <rect class="box key" x="250" y="118" width="150" height="62" rx="8"/>
    <text class="name" x="325.0" y="146.0" text-anchor="middle">T</text>
    <text class="sub" x="325.0" y="163.0" text-anchor="middle">trusted monitor</text>
    <path class="edge" d="M 400 138 C 450 138 450 62 500 62" marker-end="url(#ah)"/>
    <path class="flow" d="M 400 138 C 450 138 450 62 500 62" style="animation-delay:-0.3s"/>
    <text class="tag" x="452" y="96" text-anchor="middle">top 2%</text>
    <rect class="box key" x="500" y="32" width="150" height="62" rx="8"/>
    <text class="name" x="575.0" y="60.0" text-anchor="middle">H</text>
    <text class="sub" x="575.0" y="77.0" text-anchor="middle">human auditors</text>
    <path class="edge" d="M 650 63 H 740" marker-end="url(#ah)"/>
    <path class="flow" d="M 650 63 H 740" style="animation-delay:-0.6s"/>
    <rect class="box" x="740" y="32" width="180" height="62" rx="8"/>
    <text class="name" x="830.0" y="60.0" text-anchor="middle">Blocked</text>
    <text class="sub" x="830.0" y="77.0" text-anchor="middle">if malicious</text>
    <path class="edge" d="M 400 160 C 450 160 450 236 500 236" marker-end="url(#ah)"/>
    <path class="flow" d="M 400 160 C 450 160 450 236 500 236" style="animation-delay:-0.9s"/>
    <text class="tag" x="455" y="205" text-anchor="middle">remaining 98%</text>
    <rect class="box" x="500" y="205" width="190" height="62" rx="8"/>
    <text class="name" x="595.0" y="233.0" text-anchor="middle">Deployed</text>
    <text class="sub" x="595.0" y="250.0" text-anchor="middle">merged to production</text>
    </svg>
  </div>
  <p class="legend">T scores every edit U produces. The top 2% go to H, who revise or block anything potentially malicious. The remaining 98% merge.</p>
</div>
</body>
</html>

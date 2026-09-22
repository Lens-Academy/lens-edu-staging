---
id: '18a20590-0842-4ce1-a45e-eeb15ee949bc'
title: Scenario 5: rewind and ask again
summary_for_tutor: >-
  Scenario 5 of the five-scenario control evaluation in "The case for control (1)": a flow diagram of resampling, the protocol the lesson returns to much later as Ctrl-Z. U feeds into T, which scores each command before it runs. Low suspicion goes to Executed. High suspicion goes into a box reading Rewind and resample, up to 3 tries, no memory, which loops back to U with the label ask U again, and then leaves in two branches: least suspicious runs, to a second Executed box, and all 3 suspicious, to H, the human auditors. The learner reads it and then answers whether the setup holds the control property. The diagram states the setup only; it does not answer the question and says nothing about what resampling reveals across tries.
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
svg { display: block; width: 100%; min-width: 700px; height: auto; }
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
    <svg viewBox="0 0 1060 455" role="img" aria-label="T scores each command; low suspicion runs, high suspicion rewinds and resamples up to three times, and a bundle that stays suspicious goes to human auditors.">
    <defs><marker id="ah" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M0,0 L10,5 L0,10 z" fill="var(--line)"/></marker></defs>
    <rect class="box key" x="30" y="150" width="130" height="62" rx="8"/>
    <text class="name" x="95.0" y="178.0" text-anchor="middle">U</text>
    <text class="sub" x="95.0" y="195.0" text-anchor="middle">untrusted model</text>
    <path class="edge" d="M 160 181 H 250" marker-end="url(#ah)"/>
    <path class="flow" d="M 160 181 H 250" style="animation-delay:-0.0s"/>
    <rect class="box key" x="250" y="150" width="160" height="62" rx="8"/>
    <text class="name" x="330.0" y="178.0" text-anchor="middle">T</text>
    <text class="sub" x="330.0" y="195.0" text-anchor="middle">scores each command</text>
    <path class="edge" d="M 410 168 C 460 168 460 62 510 62" marker-end="url(#ah)"/>
    <path class="flow" d="M 410 168 C 460 168 460 62 510 62" style="animation-delay:-0.2s"/>
    <text class="tag" x="462" y="108" text-anchor="middle">low suspicion</text>
    <rect class="box" x="510" y="32" width="190" height="62" rx="8"/>
    <text class="name" x="605.0" y="60.0" text-anchor="middle">Executed</text>
    <text class="sub" x="605.0" y="77.0" text-anchor="middle">the command runs</text>
    <path class="edge" d="M 410 194 C 460 194 460 300 510 300" marker-end="url(#ah)"/>
    <path class="flow" d="M 410 194 C 460 194 460 300 510 300" style="animation-delay:-0.5s"/>
    <text class="tag" x="464" y="272" text-anchor="middle">high suspicion</text>
    <rect class="box key" x="510" y="270" width="260" height="62" rx="8"/>
    <text class="name" x="640.0" y="298.0" text-anchor="middle">Rewind and resample</text>
    <text class="sub" x="640.0" y="315.0" text-anchor="middle">up to 3 tries, no memory</text>
    <path class="edge" d="M 560 332 C 420 425 95 420 95 214" marker-end="url(#ah)"/>
    <path class="flow" d="M 560 332 C 420 425 95 420 95 214" style="animation-delay:-0.8s"/>
    <text class="tag" x="330" y="412" text-anchor="middle">ask U again</text>
    <path class="edge" d="M 770 288 C 830 288 830 200 860 190" marker-end="url(#ah)"/>
    <path class="flow" d="M 770 288 C 830 288 830 200 860 190" style="animation-delay:-1.1s"/>
    <text class="tag" x="838" y="262" text-anchor="end">least suspicious runs</text>
    <rect class="box" x="860" y="150" width="180" height="62" rx="8"/>
    <text class="name" x="950.0" y="178.0" text-anchor="middle">Executed</text>
    <text class="sub" x="950.0" y="195.0" text-anchor="middle">the command runs</text>
    <path class="edge" d="M 770 314 C 830 314 830 380 860 380" marker-end="url(#ah)"/>
    <path class="flow" d="M 770 314 C 830 314 830 380 860 380" style="animation-delay:-1.4s"/>
    <text class="tag" x="836" y="358" text-anchor="end">all 3 suspicious</text>
    <rect class="box key" x="860" y="350" width="150" height="62" rx="8"/>
    <text class="name" x="935.0" y="378.0" text-anchor="middle">H</text>
    <text class="sub" x="935.0" y="395.0" text-anchor="middle">human auditors</text>
    </svg>
  </div>
  <p class="legend">T scores each command before it runs. Low suspicion executes. High suspicion rewinds and resamples from U, up to three tries with no memory between them; the least suspicious retry runs, or if all three stay suspicious the bundle goes to H.</p>
</div>
</body>
</html>

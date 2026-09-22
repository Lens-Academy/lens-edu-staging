---
id: '39898f1d-ae9e-4041-b61f-622df5ddff87'
title: "Scenario 1: straight to production"
summary_for_tutor: >-
  Scenario 1 of the five-scenario control evaluation. A deployment with no safeguards: U runs straight to the Deployed terminal, with no monitor, no auditor and no branch anywhere in the path. The learner answers whether this setup holds the control property. The diagram states the setup only and does not answer the question. The cast, fixed across all five scenarios: U is the untrusted frontier model, T is the older weaker trusted model, U′ is a second identical copy of U, and H is the scarce human auditors. Each node carries its letter and a role chip; edges are dashed and the dashes drift in the direction of flow. The picture is deliberately neutral: it shows the workflow and never marks any path as safe or unsafe.
height: auto
tags: []
---
<!doctype html>
<!-- A port of XLab's control-scenario flow graph for the AI Control track lesson
     "The case for ensuring that powerful AIs are controlled". Node positions,
     edges, chips and condition labels are XLab's, from their scenario data;
     the drawing follows their renderer. -->
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 "DM Sans", Arial, sans-serif; color: #1a1a1a; background: #ffffff; }
.scroll { overflow-x: auto; overflow-y: hidden; }
svg { display: block; width: 100%; min-width: 480px; height: auto; font-family: "DM Sans", Arial, sans-serif; }
.edge { stroke-dasharray: 6 6; animation: dash 0.55s linear infinite; }
@keyframes dash { to { stroke-dashoffset: -12; } }
@media (prefers-reduced-motion: reduce) { .edge { animation: none; } }
@media (max-width: 420px) { body { padding: 12px; } }
</style>
</head>
<body>
<div class="scroll">
  <svg viewBox="0 0 560 116" role="img" aria-label="U sends its work straight to Deployed, with nothing in between.">
  <defs><marker id="ah" viewBox="0 0 8 8" refX="7" refY="4" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M 0 0 L 8 4 L 0 8 z" fill="#a39d93"/></marker></defs>
  <path class="edge" d="M 94.0 58 C 184.0 58, 364.0 58, 454.0 58" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <rect x="10.0" y="32.0" width="84" height="52" rx="12" fill="#fdf7f0" stroke="#b87018" stroke-width="1.5"/><text x="52" y="56" text-anchor="middle" font-size="16" font-weight="700" fill="#8a5412">U</text><rect x="32.5" y="63" width="39.0" height="13" rx="6.5" fill="#ffffff" stroke="#b87018"/><text x="52" y="72.5" text-anchor="middle" font-size="7.5" font-weight="600" letter-spacing="0.6" fill="#8a5412">AGENT</text>
  <rect x="454.0" y="40.0" width="92" height="36" rx="10" fill="#faf8f3" stroke="#e8e5df" stroke-width="1.25"/><text x="500" y="61.5" text-anchor="middle" font-size="11" font-weight="600" fill="#5a5a5a">Deployed</text>
  </svg>
</div>
</body>
</html>

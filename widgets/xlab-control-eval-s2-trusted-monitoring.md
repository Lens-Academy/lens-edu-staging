---
id: 'a693d913-dfa1-46ee-ae07-ebafe1cb5a91'
title: "Scenario 2: every edit is monitored"
summary_for_tutor: >-
  Scenario 2 of the five-scenario control evaluation, the protocol the lesson later names trusted monitoring, though the name is not on the page yet. U feeds T, which scores every edit and splits: the top 2 percent to H, the remaining 98 percent to a junction that leads to Deployed. H has two outgoing edges, malicious to a Blocked terminal and non-malicious back into that same junction, so audited work H clears still reaches production. The learner answers whether the setup holds the control property and what that depends on. Nothing in the diagram speaks to T's accuracy or to the capability gap between U and T. The cast, fixed across all five scenarios: U is the untrusted frontier model, T is the older weaker trusted model, U′ is a second identical copy of U, and H is the scarce human auditors. Each node carries its letter and a role chip; edges are dashed and the dashes drift in the direction of flow. The picture is deliberately neutral: it shows the workflow and never marks any path as safe or unsafe.
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
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 "DM Sans", Arial, sans-serif; color: #1a1a1a; background: #ffffff; }
.scroll { overflow-x: auto; overflow-y: hidden; }
svg { display: block; width: 100%; min-width: 520px; height: auto; font-family: "DM Sans", Arial, sans-serif; }
.edge { stroke-dasharray: 6 6; animation: dash 0.55s linear infinite; }
@keyframes dash { to { stroke-dashoffset: -12; } }
@media (prefers-reduced-motion: reduce) { .edge { animation: none; } }
@media (max-width: 420px) { body { padding: 12px; } }
</style>
</head>
<body>
<div class="scroll">
  <svg viewBox="0 0 560 304" role="img" aria-label="T scores every edit; the top two percent go to human auditors, who block malicious work and pass the rest on to deployment along with the remaining ninety-eight percent.">
  <defs><marker id="ah" viewBox="0 0 8 8" refX="7" refY="4" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M 0 0 L 8 4 L 0 8 z" fill="#a3a3a3"/></marker></defs>
  <path class="edge" d="M 94.0 64 C 118.0 64, 120.0 64, 144.0 64" fill="none" stroke="#a3a3a3" stroke-width="1.5" marker-end="url(#ah)"/>
  <path class="edge" d="M 228.0 64 C 286.03 64.0, 221.97 182.0, 280.0 182" fill="none" stroke="#a3a3a3" stroke-width="1.5" marker-end="url(#ah)"/>
  <rect x="230.04" y="114.0" width="47.92" height="18" rx="9" fill="#ffffff" stroke="#e5e5e5"/><text x="254.0" y="126.2" text-anchor="middle" font-size="9.5" fill="#525252" font-weight="500">top 2%</text>
  <path class="edge" d="M 228.0 64 C 318.0 64, 342.0 64, 432.0 64" fill="none" stroke="#a3a3a3" stroke-width="1.5"/>
  <rect x="287.42" y="55.0" width="85.16" height="18" rx="9" fill="#ffffff" stroke="#e5e5e5"/><text x="330.0" y="67.2" text-anchor="middle" font-size="9.5" fill="#525252" font-weight="500">remaining 98%</text>
  <path class="edge" d="M 322 208.0 C 322 232.0, 322 230.0, 322 254.0" fill="none" stroke="#a3a3a3" stroke-width="1.5" marker-end="url(#ah)"/>
  <text x="356.0" y="231.0" text-anchor="middle" font-size="9.5" fill="#737373" font-style="italic" stroke="#ffffff" stroke-width="3" paint-order="stroke">malicious</text>
  <path class="edge" d="M 364.0 182 C 424.67 182.0, 436.0 128.67, 436 68.0" fill="none" stroke="#a3a3a3" stroke-width="1.5"/>
  <text x="415.56" y="151.35" text-anchor="middle" font-size="9.5" fill="#737373" font-style="italic" stroke="#ffffff" stroke-width="3" paint-order="stroke">non-malicious</text>
  <path class="edge" d="M 440.0 64 C 464.0 64, 436.0 64, 460.0 64" fill="none" stroke="#a3a3a3" stroke-width="1.5" marker-end="url(#ah)"/>
  <rect x="10.0" y="38.0" width="84" height="52" rx="12" fill="#fef2f2" stroke="#dc2626" stroke-width="1.5"/><text x="52" y="62" text-anchor="middle" font-size="16" font-weight="700" fill="#b91c1c">U</text><rect x="32.5" y="69" width="39.0" height="13" rx="6.5" fill="#ffffff" stroke="#dc2626" stroke-opacity="0.45"/><text x="52" y="78.5" text-anchor="middle" font-size="7.5" font-weight="600" letter-spacing="0.6" fill="#b91c1c">AGENT</text>
  <rect x="144.0" y="38.0" width="84" height="52" rx="12" fill="#eef2f8" stroke="#2c3e60" stroke-width="1.5"/><text x="186" y="62" text-anchor="middle" font-size="16" font-weight="700" fill="#233554">T</text><rect x="162.3" y="69" width="47.4" height="13" rx="6.5" fill="#ffffff" stroke="#2c3e60" stroke-opacity="0.45"/><text x="186" y="78.5" text-anchor="middle" font-size="7.5" font-weight="600" letter-spacing="0.6" fill="#233554">MONITOR</text><text x="186" y="103.0" text-anchor="middle" font-size="9" fill="#737373" stroke="#ffffff" stroke-width="3" paint-order="stroke">scores every edit</text>
  <rect x="280.0" y="156.0" width="84" height="52" rx="12" fill="#f0fdfa" stroke="#0f766e" stroke-width="1.5"/><text x="322" y="180" text-anchor="middle" font-size="16" font-weight="700" fill="#0f766e">H</text><rect x="298.3" y="187" width="47.4" height="13" rx="6.5" fill="#ffffff" stroke="#0f766e" stroke-opacity="0.45"/><text x="322" y="196.5" text-anchor="middle" font-size="7.5" font-weight="600" letter-spacing="0.6" fill="#0f766e">AUDITOR</text>
  <rect x="276.0" y="254.0" width="92" height="36" rx="10" fill="#fafafa" stroke="#d4d4d4" stroke-width="1.25"/><text x="322" y="275.5" text-anchor="middle" font-size="11" font-weight="600" fill="#525252">Blocked</text>
  <circle cx="436" cy="64" r="4" fill="#a3a3a3"/>
  <rect x="460.0" y="46.0" width="92" height="36" rx="10" fill="#fafafa" stroke="#d4d4d4" stroke-width="1.25"/><text x="506" y="67.5" text-anchor="middle" font-size="11" font-weight="600" fill="#525252">Deployed</text>
  </svg>
</div>
</body>
</html>

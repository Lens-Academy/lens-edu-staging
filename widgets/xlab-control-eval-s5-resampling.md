---
id: '18a20590-0842-4ce1-a45e-eeb15ee949bc'
title: "Scenario 5: rewind and ask again"
summary_for_tutor: >-
  Scenario 5 of the five-scenario control evaluation, resampling, the protocol the lesson returns to much later as Ctrl-Z. U sends a command to T, which scores it. Low suspicion runs to the Executed terminal. A loop edge runs from T back to U, chipped 'ask again ×3, U keeps no memory between tries'. T also feeds a Compare node carrying a stack-of-three glyph, which splits two ways: least suspicious retry runs, to Executed, and retries look suspicious too, to H, which sends malicious work to Blocked. The learner answers whether the setup holds the control property. The diagram does not say what resampling reveals across tries. The cast, fixed across all five scenarios: U is the untrusted frontier model, T is the older weaker trusted model, U′ is a second identical copy of U, and H is the scarce human auditors. Each node carries its letter and a role chip; edges are dashed and the dashes drift in the direction of flow. The picture is deliberately neutral: it shows the workflow and never marks any path as safe or unsafe.
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
svg { display: block; width: 100%; min-width: 540px; height: auto; font-family: "DM Sans", Arial, sans-serif; }
.edge { stroke-dasharray: 6 6; animation: dash 0.55s linear infinite; }
@keyframes dash { to { stroke-dashoffset: -12; } }
@media (prefers-reduced-motion: reduce) { .edge { animation: none; } }
@media (max-width: 420px) { body { padding: 12px; } }
</style>
</head>
<body>
<div class="scroll">
  <svg viewBox="0 0 560 428" role="img" aria-label="T scores each command; low suspicion executes, suspicious steps are resampled from U up to three times with no memory between tries, and a bundle that stays suspicious goes to human auditors.">
  <defs><marker id="ah" viewBox="0 0 8 8" refX="7" refY="4" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M 0 0 L 8 4 L 0 8 z" fill="#a39d93"/></marker></defs>
  <path class="edge" d="M 94.0 170 C 118.3 170.0, 123.7 170.0, 148.0 170" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <text x="121.0" y="162.0" text-anchor="middle" font-size="9.5" fill="#5a5a5a" font-style="italic" stroke="#ffffff" stroke-width="3" paint-order="stroke">command</text>
  <path class="edge" d="M 232.0 162 C 322.0 162, 374.0 162, 464.0 162" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <rect x="305.42" y="153.0" width="85.16" height="18" rx="9" fill="#ffffff" stroke="#e8e5df"/><text x="348.0" y="165.2" text-anchor="middle" font-size="9.5" fill="#5a5a5a" font-weight="500">low suspicion</text>
  <path class="edge" d="M 190 144.0 C 190 52.0, 52 52.0, 52 144.0" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <rect x="30.54" y="59.5" width="180.92" height="31" rx="9" fill="#ffffff" stroke="#e8e5df"/><text x="121.0" y="72.0" text-anchor="middle" font-size="9.5" fill="#5a5a5a" font-weight="500">↩ ask again ×3 —</text><text x="121.0" y="83.5" text-anchor="middle" font-size="9.5" fill="#5a5a5a" font-weight="500">U keeps no memory between tries</text>
  <path class="edge" d="M 232.0 184 C 274.64 184.0, 300.0 207.36, 300 250.0" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <path class="edge" d="M 341.0 264 C 408.03 264.0, 396.97 180.0, 464.0 180" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <text x="402.5" y="210.0" text-anchor="middle" font-size="9.5" fill="#5a5a5a" font-style="italic" stroke="#ffffff" stroke-width="3" paint-order="stroke">least suspicious retry runs</text>
  <path class="edge" d="M 341.0 280 C 380.45 280.0, 373.55 330.0, 413.0 330" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <text x="309.0" y="329.0" text-anchor="middle" font-size="9.5" fill="#5a5a5a" font-style="italic" stroke="#ffffff" stroke-width="3" paint-order="stroke">retries look suspicious too</text>
  <path class="edge" d="M 455 356.0 C 455 380.0, 455 362.0, 455 386.0" fill="none" stroke="#a39d93" stroke-width="1.5" marker-end="url(#ah)"/>
  <text x="489.0" y="371.0" text-anchor="middle" font-size="9.5" fill="#5a5a5a" font-style="italic" stroke="#ffffff" stroke-width="3" paint-order="stroke">malicious</text>
  <rect x="10.0" y="144.0" width="84" height="52" rx="12" fill="#fdf7f0" stroke="#b87018" stroke-width="1.5"/><text x="52" y="168" text-anchor="middle" font-size="16" font-weight="700" fill="#8a5412">U</text><rect x="32.5" y="175" width="39.0" height="13" rx="6.5" fill="#ffffff" stroke="#b87018"/><text x="52" y="184.5" text-anchor="middle" font-size="7.5" font-weight="600" letter-spacing="0.6" fill="#8a5412">AGENT</text>
  <rect x="148.0" y="144.0" width="84" height="52" rx="12" fill="#f6f4f0" stroke="#8a857c" stroke-width="1.5"/><text x="190" y="168" text-anchor="middle" font-size="16" font-weight="700" fill="#3d3a35">T</text><rect x="166.3" y="175" width="47.4" height="13" rx="6.5" fill="#ffffff" stroke="#8a857c"/><text x="190" y="184.5" text-anchor="middle" font-size="7.5" font-weight="600" letter-spacing="0.6" fill="#3d3a35">MONITOR</text><text x="190" y="209.0" text-anchor="middle" font-size="9" fill="#5a5a5a" stroke="#ffffff" stroke-width="3" paint-order="stroke">scores each command</text>
  <rect x="464.0" y="152.0" width="92" height="36" rx="10" fill="#faf8f3" stroke="#e8e5df" stroke-width="1.25"/><text x="510" y="173.5" text-anchor="middle" font-size="11" font-weight="600" fill="#5a5a5a">Executed</text>
  <rect x="259.0" y="250.0" width="82" height="44" rx="10" fill="#faf8f3" stroke="#e8e5df" stroke-width="1.25"/><text x="300" y="268" text-anchor="middle" font-size="11" font-weight="600" fill="#5a5a5a">Compare</text><rect x="286" y="276.0" width="9" height="7" rx="1.5" fill="#ffffff" stroke="#5a5a5a" stroke-width="0.9"/><rect x="288.5" y="278.0" width="9" height="7" rx="1.5" fill="#ffffff" stroke="#5a5a5a" stroke-width="0.9"/><rect x="291" y="280.0" width="9" height="7" rx="1.5" fill="#ffffff" stroke="#5a5a5a" stroke-width="0.9"/><text x="308" y="286" font-size="9.5" font-weight="600" fill="#5a5a5a">×3</text>
  <rect x="413.0" y="304.0" width="84" height="52" rx="12" fill="#ffffff" stroke="#1a1a1a" stroke-width="1.5"/><text x="455" y="328" text-anchor="middle" font-size="16" font-weight="700" fill="#1a1a1a">H</text><rect x="431.3" y="335" width="47.4" height="13" rx="6.5" fill="#ffffff" stroke="#1a1a1a"/><text x="455" y="344.5" text-anchor="middle" font-size="7.5" font-weight="600" letter-spacing="0.6" fill="#1a1a1a">AUDITOR</text>
  <rect x="409.0" y="386.0" width="92" height="36" rx="10" fill="#faf8f3" stroke="#e8e5df" stroke-width="1.25"/><text x="455" y="407.5" text-anchor="middle" font-size="11" font-weight="600" fill="#5a5a5a">Blocked</text>
  </svg>
</div>
</body>
</html>

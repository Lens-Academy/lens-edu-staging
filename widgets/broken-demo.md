---
id: 'a1d2e3f4-5b6c-4d7e-8f90-1a2b3c4d5e04'
title: Broken widget (demo)
summary_for_tutor: A deliberately invalid widget used to show what learners see when a widget file has errors. It has no content.
tags: [wip]
---
<!doctype html>
<html>
<head><meta charset="utf-8"><title>Broken</title>
<style>
  /* ROUND-TRIP TEST 2026-09-21 — will be reverted immediately */
  thead > tr:last-child th { min-width: 6rem; content: "a>b & c"; }
  .x::after { content: '\201C'; }
</style>
</head>
<body>
<div class="card">
  <p>This widget is broken on purpose: the div below is closed with a span, and the script never ends.</span>
</div>
<script>
  var never = "closed";
</body>
</html>

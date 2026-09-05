---
title: Broken widget (demo)
summary_for_tutor: A deliberately invalid widget used to show what learners see when a widget file has errors. It has no content.
tags: [wip]
---
<!doctype html>
<html>
<head><meta charset="utf-8"><title>Broken</title></head>
<body>
<div class="card">
  <p>This widget is broken on purpose: the div below is closed with a span, and the script never ends.</span>
</div>
<script>
  var never = "closed";
</body>
</html>

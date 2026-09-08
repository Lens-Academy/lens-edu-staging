---
id: 'dfb2faac-ee28-4815-a9a2-2847264dc653'
title: Deal implementation timeline, 2029 to 2031
summary_for_tutor: "A static timeline chart reproducing the AI 2040 verification supplement's 'Deal Implementation Timeline (detailed)' figure, with every marker placed from the source chart's own event dates. Axis from Jan 2029 to Jan 2031 with quarter ticks. Events: mutual chip declaration and R&D pause (early 2029); SL5 datacenter construction begins and the inference-only retrofit reaches 50%, 80% and 95% through 2029; R&D resumes late 2029 with the R&D verification rollout going from 2% to 20% by spring 2030; first major training runs approved (early 2030); SL5 inference clusters roll out from 5% to 30% in the second half of 2030; first generation of post-deal models released (mid 2030); mature safety-case-based R&D rules by Jan 2031. Nothing to click. On a narrow screen the chart keeps its full size and scrolls sideways inside its own box."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Deal implementation timeline, 2029 to 2031</title>
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), chart "Deal Implementation Timeline (detailed)" (TimelineLineDetailedClean component). -->
<!-- Data: every label and every marker position comes from the source page's own events JSON in chunk 4126 (id, date, lines, subMilestones), converted to months with the component's own formula (y - 2029) * 12 + (m - 1) + (d - 1) / daysInMonth. Nothing is read by eye. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1 { font-family: var(--font-heading); font-weight: 600; margin: 0; font-size: 22px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 4px; }
  .lede { color: var(--muted); margin: 4px 0 12px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .chartbox { overflow-x: auto; }
  .chart { width: 100%; min-width: 720px; height: auto; display: block; }
  .chart text { font-family: var(--font-ui); }
  .chart .lbl { font-size: 15px; fill: var(--text); }
  .chart .lbl.hi { fill: var(--accent); font-weight: 600; }
  .chart .yr { font-size: 22px; fill: var(--text); font-family: var(--font-heading); }
  .chart .mo { font-size: 14px; fill: var(--muted); font-style: italic; }
  .chart .pct { font-size: 15px; fill: var(--text); }
  .cap { font-size: 12px; font-style: italic; color: var(--muted); margin: 10px 0 0; }
  @media (max-width: 600px) { body { padding: 10px; } }
</style>
</head>
<body>
<p class="eyebrow">Figure</p>
<h1>Deal implementation timeline, 2029 to 2031</h1>
<p class="lede">What the deal's first two years look like on a calendar: the declaration and the pause up front, then the retrofit, the verification rollout and the return of approved training runs.</p>

<div class="card">
  <div class="chartbox">
    <svg id="c" class="chart" viewBox="0 0 1000 400" role="img" aria-label="Deal implementation timeline, January 2029 to January 2031"></svg>
  </div>
  <p class="cap">Deal implementation timeline, redrawn from the AI 2040 verification supplement.</p>
</div>
<script>
(function () {
  var svg = document.getElementById('c');
  var NS = 'http://www.w3.org/2000/svg';
  var X0 = 70, X1 = 930, Y = 230;             // Jan 2029 .. Jan 2031 on the axis
  var ACCENT = '#b87018';
  function px(m) { return X0 + (X1 - X0) * (m / 24); }  // months since Jan 2029 -> x
  function el(t, a, txt) { var e = document.createElementNS(NS, t); for (var k in a) if (a[k] !== undefined) e.setAttribute(k, a[k]); if (txt != null) e.textContent = txt; svg.appendChild(e); return e; }
  function text(x, y, lines, cls, anchor) {
    var t = el('text', { x: x, y: y, 'text-anchor': anchor || 'middle', 'class': cls || 'lbl' });
    lines.forEach(function (l, i) { var s = document.createElementNS(NS, 'tspan'); s.setAttribute('x', x); s.setAttribute('dy', i ? 18 : 0); s.textContent = l; t.appendChild(s); });
  }
  // axis + arrow
  el('line', { x1: X0 - 20, y1: Y, x2: X1 + 20, y2: Y, stroke: '#1a1a1a', 'stroke-width': 1.5 });
  el('polygon', { points: (X1 + 20) + ',' + Y + ' ' + (X1 + 10) + ',' + (Y - 4) + ' ' + (X1 + 10) + ',' + (Y + 4), fill: '#1a1a1a' });
  // year and quarter ticks
  [0, 12, 24].forEach(function (m, i) {
    el('line', { x1: px(m), y1: Y - 5, x2: px(m), y2: Y + 5, stroke: '#1a1a1a', 'stroke-width': 1 });
    text(px(m), Y + 45, ['Jan ' + (2029 + i)], 'yr');
  });
  [3, 6, 9, 15, 18, 21].forEach(function (m) {
    el('line', { x1: px(m), y1: Y - 3, x2: px(m), y2: Y + 3, stroke: '#1a1a1a', 'stroke-width': 1 });
    text(px(m), Y + 22, [['Apr', 'Jul', 'Oct'][(m / 3 - 1) % 3]], 'mo');
  });
  // point events: [month, lines, side(-1 above / +1 below), height, cls]
  // Months since Jan 2029, computed from the source chart's own event dates
  // (chunk 4126, events JSON) with its own formula: (y-2029)*12 + (m-1) + (d-1)/daysInMonth.
  var events = [
    [0.742, ['Mutual chip', 'declaration'], -1, 95],           // 2029-01-24
    [1.321, ['R&D pause begins'], 1, 75],                      // 2029-02-10
    [2.0, ['SL5 datacenter', 'construction begins'], -1, 155], // 2029-03-01
    [10.0, ['R&D resumes'], -1, 120],                          // 2029-11-01
    [13.0, ['First major', 'training runs', 'approved'], -1, 135, 'hi'],          // 2030-02-01
    [17.5, ['First generation of post-', 'deal models released'], 1, 125, 'hi'],  // 2030-06-16
    [24.0, ['Mature safety case', 'based R&D rules'], -1, 120] // 2031-01-01
  ];
  events.forEach(function (ev) {
    var m = ev[0], lines = ev[1], side = ev[2], hgt = ev[3], cls = ev[4];
    var hi = cls === 'hi';
    var x = px(m), yEnd = Y + side * hgt;
    el('line', {
      x1: x, y1: Y, x2: x, y2: yEnd + (side < 0 ? 8 : -6),
      stroke: hi ? ACCENT : '#8a8a8a', 'stroke-width': hi ? 1.5 : 1,
      'stroke-dasharray': hi ? undefined : '2 3'
    });
    el('circle', { cx: x, cy: Y, r: 3.5, fill: hi ? ACCENT : '#fff', stroke: hi ? ACCENT : '#1a1a1a', 'stroke-width': 1 });
    var yText = side < 0 ? yEnd - (lines.length - 1) * 18 : yEnd + 12;
    text(x, yText, lines, hi ? 'lbl hi' : 'lbl');
  });
  // bracketed rollouts: [start, end, label, marks[[month, pct]], side, height]
  var spans = [
    [2.0, 8.0, 'Inference-only retrofit', [[2.0, '50%'], [4.0, '80%'], [8.0, '95%']], -1, 45],   // 2029-03-01, 2029-05-01, 2029-09-01
    [10.0, 14.0, 'R&D verification rollout', [[10.0, '2%'], [14.0, '20%']], 1, 70],              // 2029-11-01, 2030-03-01
    [17.0, 20.0, 'SL5 inference clusters rollout', [[17.0, '5%'], [20.0, '30%']], -1, 45]        // 2030-06-01, 2030-09-01
  ];
  spans.forEach(function (sp) {
    var a = sp[0], b = sp[1], label = sp[2], marks = sp[3], side = sp[4], hgt = sp[5];
    var y = Y + side * hgt, xa = px(a), xb = px(b);
    el('path', { d: 'M' + xa + ',' + (Y + side * 8) + ' V' + y + ' H' + xb + ' V' + (Y + side * 8), stroke: '#8a8a8a', 'stroke-width': 1, fill: 'none' });
    marks.forEach(function (mk) {
      el('circle', { cx: px(mk[0]), cy: Y, r: 3.5, fill: '#fff', stroke: '#1a1a1a', 'stroke-width': 1 });
      text(px(mk[0]), side < 0 ? Y - 12 : Y + 40, [mk[1]], 'pct');
    });
    text((xa + xb) / 2, side < 0 ? y - 8 : y + 18, [label], 'lbl');
  });
})();
</script>
</body>
</html>

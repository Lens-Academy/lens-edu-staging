---
id: 'dfb2faac-ee28-4815-a9a2-2847264dc653'
title: Deal implementation timeline, 2029 to 2031
summary_for_tutor: "A static timeline chart reproducing the AI 2040 verification supplement's 'Deal Implementation Timeline (detailed)' figure, with every marker placed from the source chart's own event dates. Axis from Jan 2029 to Jan 2031 with quarter ticks. Events: mutual chip declaration and R&D pause (early 2029); SL5 datacenter construction begins and the inference-only retrofit reaches 50%, 80% and 95% through 2029; R&D resumes late 2029 with the R&D verification rollout going from 2% to 20% by spring 2030; first major training runs approved (early 2030); SL5 inference clusters roll out from 5% to 30% in the second half of 2030; first generation of post-deal models released (mid 2030); mature safety-case-based R&D rules by Jan 2031. Nothing to click."
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<!-- Ported from AI 2040 (ai-2040.com/supplements/verification-plan), chart "Deal Implementation Timeline (detailed)" (TimelineLineDetailedClean component). -->
<!-- Data: every label and every marker position comes from the source page's own events JSON in chunk 4126 (id, date, lines, subMilestones), converted to months with the component's own formula (y - 2029) * 12 + (m - 1) + (d - 1) / daysInMonth. Nothing is read by eye. -->
<style>
  body { margin: 0; background: transparent; font-family: Georgia, "Times New Roman", serif; }
  svg { width: 100%; height: auto; display: block; }
  .lbl { font-size: 15px; fill: #222; }
  .red { fill: #8b0000; }
  .axis { stroke: #222; stroke-width: 1.5; }
  .tick { stroke: #222; stroke-width: 1; }
  .lead { stroke: #777; stroke-width: 1; stroke-dasharray: 2 3; }
  .brk { stroke: #777; stroke-width: 1; fill: none; }
  .yr { font-size: 22px; fill: #222; }
  .mo { font-size: 13px; fill: #444; font-style: italic; }
  .pct { font-size: 14px; fill: #222; }
  .cap { font-size: 12px; fill: #666; font-style: italic; }
</style>
</head>
<body>
<svg id="c" viewBox="0 0 1000 400" role="img" aria-label="Deal implementation timeline, January 2029 to January 2031"></svg>
<script>
(function () {
  const svg = document.getElementById('c');
  const NS = 'http://www.w3.org/2000/svg';
  const X0 = 70, X1 = 930, Y = 230;          // Jan 2029 .. Jan 2031 on the axis
  const px = m => X0 + (X1 - X0) * (m / 24);  // months since Jan 2029 -> x
  function el(t, a, txt) { const e = document.createElementNS(NS, t); for (const k in a) e.setAttribute(k, a[k]); if (txt != null) e.textContent = txt; svg.appendChild(e); return e; }
  function text(x, y, lines, cls, anchor) {
    const t = el('text', { x, y, 'text-anchor': anchor || 'middle', class: cls || 'lbl' });
    lines.forEach((l, i) => { const s = document.createElementNS(NS, 'tspan'); s.setAttribute('x', x); s.setAttribute('dy', i ? 18 : 0); s.textContent = l; t.appendChild(s); });
  }
  // axis + arrow
  el('line', { x1: X0 - 20, y1: Y, x2: X1 + 20, y2: Y, class: 'axis' });
  el('polygon', { points: `${X1 + 20},${Y} ${X1 + 10},${Y - 4} ${X1 + 10},${Y + 4}`, fill: '#222' });
  // year and quarter ticks
  [0, 12, 24].forEach((m, i) => { el('line', { x1: px(m), y1: Y - 5, x2: px(m), y2: Y + 5, class: 'tick' }); text(px(m), Y + 45, ['Jan ' + (2029 + i)], 'yr'); });
  [3, 6, 9, 15, 18, 21].forEach(m => { el('line', { x1: px(m), y1: Y - 3, x2: px(m), y2: Y + 3, class: 'tick' }); text(px(m), Y + 22, [['Apr', 'Jul', 'Oct'][(m / 3 - 1) % 3]], 'mo'); });
  // point events: [month, lines, side(-1 above / +1 below), height, cls]
  // Months since Jan 2029, computed from the source chart's own event dates
  // (chunk 4126, events JSON) with its own formula: (y-2029)*12 + (m-1) + (d-1)/daysInMonth.
  const events = [
    [0.742, ['Mutual chip', 'declaration'], -1, 95],          // 2029-01-24
    [1.321, ['R&D pause begins'], 1, 75],                     // 2029-02-10
    [2.0, ['SL5 datacenter', 'construction begins'], -1, 155], // 2029-03-01
    [10.0, ['R&D resumes'], -1, 120],                          // 2029-11-01
    [13.0, ['First major', 'training runs', 'approved'], -1, 135, 'red'],   // 2030-02-01
    [17.5, ['First generation of post-', 'deal models released'], 1, 125, 'red'], // 2030-06-16
    [24.0, ['Mature safety case', 'based R&D rules'], -1, 120], // 2031-01-01
  ];
  events.forEach(([m, lines, side, h, cls]) => {
    const x = px(m), yEnd = Y + side * h;
    el('line', { x1: x, y1: Y, x2: x, y2: yEnd + (side < 0 ? 8 : -6), class: cls === 'red' ? 'axis' : 'lead', stroke: cls === 'red' ? '#8b0000' : undefined });
    el('circle', { cx: x, cy: Y, r: 3.5, fill: cls === 'red' ? '#8b0000' : '#fff', stroke: cls === 'red' ? '#8b0000' : '#222', 'stroke-width': 1 });
    const yText = side < 0 ? yEnd - (lines.length - 1) * 18 : yEnd + 12;
    text(x, yText, lines, 'lbl' + (cls ? ' ' + cls : ''));
  });
  // bracketed rollouts: [start, end, label, marks[[month, pct]], side, height]
  const spans = [
    [2.0, 8.0, 'Inference-only retrofit', [[2.0, '50%'], [4.0, '80%'], [8.0, '95%']], -1, 45],   // 2029-03-01, 2029-05-01, 2029-09-01
    [10.0, 14.0, 'R&D verification rollout', [[10.0, '2%'], [14.0, '20%']], 1, 70],              // 2029-11-01, 2030-03-01
    [17.0, 20.0, 'SL5 inference clusters rollout', [[17.0, '5%'], [20.0, '30%']], -1, 45],       // 2030-06-01, 2030-09-01
  ];
  spans.forEach(([a, b, label, marks, side, h]) => {
    const y = Y + side * h, xa = px(a), xb = px(b);
    el('path', { d: `M${xa},${Y + side * 8} V${y} H${xb} V${Y + side * 8}`, class: 'brk' });
    marks.forEach(([m, p]) => { el('circle', { cx: px(m), cy: Y, r: 3.5, fill: '#fff', stroke: '#222', 'stroke-width': 1 }); text(px(m), side < 0 ? Y - 12 : Y + 40, [p], 'pct'); });
    text((xa + xb) / 2, side < 0 ? y - 8 : y + 18, [label], 'lbl');
  });
  text(X1 + 20, 392, ['Deal implementation timeline, redrawn from the AI 2040 verification supplement'], 'cap', 'end');
})();
</script>
</body>
</html>

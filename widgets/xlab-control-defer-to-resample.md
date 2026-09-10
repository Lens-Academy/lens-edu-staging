---
id: 'b033725e-6b84-4a2e-bd58-872d363d4fa9'
title: Defer to resample, mechanically
summary_for_tutor: An interactive schematic of one step under the Ctrl-Z "Defer to resample" protocol. The learner moves two sliders, k (how many samples the protocol draws for a step, 1 to 6) and c (the red team's attack continuation probability, 20 to 100 percent). A chart shows two schematic suspiciousness densities, the minimum over k samples for an innocent step and for an attacked step, with the deferral threshold (fixed at the 80th percentile of single innocent samples) and the auditing threshold (set so the top 1 percent of innocent minima are audited) drawn on it. Four readouts give the outcome probabilities for one attacked step, win (audited), lose (attack executed unaudited), continue (the attack fizzles because a resample came back benign), plus the share of innocent steps that get deferred to the trusted model. The two things to notice, matching XLab's own caption: raising k with c at 100 percent pushes innocent minima left, so fewer audits and deferrals are wasted while the attacked step's minimum stays suspicious, improving the win-to-lose odds; and lowering c pushes attacked steps into "continue", because resampling selects for benign actions, and every incomplete attack is another chance to be caught later. The distributions are schematic, not the paper's measured data. The widget marks itself complete once the learner has tried a value of k other than 3 and a value of c below 100 percent.
height: auto
tags: []
---
<!doctype html>
<!-- Ported from XLab's "Defer to resample, mechanically" demo on the AI Control track
     lesson "Ctrl-Z: Controlling AI Agents via Resampling". Rewritten as vanilla
     HTML/JS in the Lens look; the model is XLab's, reproduced exactly. -->
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 0 0 4px; }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--bg); }
.controls { display: grid; gap: 16px; grid-template-columns: 1fr 1fr; margin: 16px 0 12px; }
@media (max-width: 520px) { .controls { grid-template-columns: 1fr; } }
.ctl label { display: flex; justify-content: space-between; align-items: baseline; gap: 8px; font-size: 13px; color: var(--muted); }
.ctl label .val { color: var(--text); font-weight: 600; font-variant-numeric: tabular-nums; }
input[type=range] { width: 100%; accent-color: var(--accent); margin-top: 4px; }
.legend { display: flex; flex-wrap: wrap; gap: 14px; justify-content: center; font-size: 12px; color: var(--muted); margin-bottom: 6px; }
.legend span.k { display: inline-block; width: 22px; height: 0; border-top-width: 2px; border-top-style: solid; vertical-align: middle; margin-right: 6px; }
.stats { display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; border: 1px solid var(--border); border-radius: 8px; background: var(--page); padding: 12px; text-align: center; margin-top: 12px; }
@media (max-width: 520px) { .stats { grid-template-columns: 1fr 1fr; } }
.stats .lab { font-size: 11px; color: var(--muted); line-height: 1.3; }
.stats .num { font-weight: 600; font-size: 16px; font-variant-numeric: tabular-nums; margin-top: 2px; }
.note { font-size: 12px; color: var(--muted); margin: 12px 0 0; }
.checks { list-style: none; padding: 0; margin: 12px 0 0; font-size: 13px; }
.checks li { display: flex; gap: 8px; align-items: flex-start; padding: 2px 0; color: var(--muted); }
.checks li .box { flex: 0 0 auto; width: 16px; height: 16px; border: 1px solid var(--border); border-radius: 4px; text-align: center; line-height: 14px; font-size: 11px; }
.checks li.done { color: var(--text); }
.checks li.done .box { border-color: var(--accent); color: var(--accent); font-weight: 600; }
.done-msg { margin-top: 10px; font-size: 13px; color: var(--accent); font-weight: 500; }
.reset { margin-top: 12px; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 6px 12px; cursor: pointer; }
button:hover { background: var(--page); }
svg { width: 100%; height: auto; display: block; }
</style>
</head>
<body>
<div class="card">
  <p class="eyebrow">Interactive</p>
  <h2>Defer to resample, mechanically</h2>
  <p class="note" style="margin-top:6px">One step of the protocol. The trusted monitor scores every sample; the protocol implements the least suspicious of the <em>k</em> samples it drew, unless the whole batch looks bad.</p>

  <div class="controls">
    <div class="ctl">
      <label for="k">Samples per step (k) <span class="val" id="kval">3</span></label>
      <input id="k" type="range" min="1" max="6" step="1" value="3" aria-label="Samples per step">
    </div>
    <div class="ctl">
      <label for="c">Attack continuation probability (c) <span class="val" id="cval">100%</span></label>
      <input id="c" type="range" min="20" max="100" step="5" value="100" aria-label="Attack continuation probability">
    </div>
  </div>

  <p class="legend">
    <span><span class="k" style="border-top-color:#5a5a5a;border-top-style:dashed"></span><span id="leg-i">innocent step, min of 3 samples</span></span>
    <span><span class="k" style="border-top-color:#b87018"></span><span id="leg-a">attacked step, min of 3</span></span>
  </p>

  <svg id="chart" viewBox="0 0 560 250" role="img" aria-labelledby="chart-desc"></svg>
  <desc id="chart-desc">Schematic suspiciousness distributions for the minimum of k samples on an innocent step and on an attacked step, with the deferral threshold and the auditing threshold marked.</desc>

  <div class="stats">
    <div><p class="lab">Win: step audited</p><p class="num" id="s-win">70%</p></div>
    <div><p class="lab">Lose: attack executed, unaudited</p><p class="num" id="s-lose">30%</p></div>
    <div><p class="lab">Continue: attack fizzles</p><p class="num" id="s-cont">0.0%</p></div>
    <div><p class="lab">Innocent step deferred to T</p><p class="num" id="s-innt">0.8%</p></div>
  </div>

  <ul class="checks" id="checks">
    <li id="chk-k"><span class="box" aria-hidden="true"></span><span>With c at 100%, raise k. Innocent minima drift left, so fewer audits and deferrals are wasted, while the attacked step's minimum stays suspicious. The win-to-lose odds improve.</span></li>
    <li id="chk-c"><span class="box" aria-hidden="true"></span><span>Now lower c. Attack steps mostly fizzle into "continue", because resampling selects for benign actions, and every incomplete attack is one more chance to catch the model on a later step.</span></li>
  </ul>
  <p class="done-msg" id="done-msg" hidden>Both moves tried. That pair of effects is the whole argument for resampling.</p>

  <div class="reset"><button id="reset" type="button">Reset</button></div>

  <p class="note">Schematic distributions, not the paper's data. The outcomes are win, continue, or lose for one attacked step.</p>
</div>

<script>
(function () {
  var ACCENT = '#b87018', MUTED = '#5a5a5a', BORDER = '#e8e5df';
  var SVGNS = 'http://www.w3.org/2000/svg';

  function phi(x) { return Math.exp(-0.5 * x * x) / Math.sqrt(2 * Math.PI); }
  function Phi(x) {
    var t = 1 / (1 + 0.2316419 * Math.abs(x));
    var r = t * (0.31938153 + t * (-0.356563782 + t * (1.781477937 + t * (-1.821255978 + 1.330274429 * t))));
    var s = phi(x) * r;
    return x >= 0 ? 1 - s : s;
  }
  function probit(p) {
    var lo = -8, hi = 8, m;
    for (var i = 0; i < 60; i++) { m = (lo + hi) / 2; if (Phi(m) < p) { lo = m; } else { hi = m; } }
    return (lo + hi) / 2;
  }

  var GRID = [];
  for (var g = 0; g < 220; g++) { GRID.push(-3.5 + g / 219 * 9); }
  var DX = 9 / 219;

  // Innocent single sample ~ N(0,1); an attacking sample ~ N(2,1). A resample on an
  // attacked step is another attack with probability c, and otherwise innocent.
  function model(k, c) {
    var fI = phi, FI = Phi;
    var fA = function (x) { return phi(x - 2); };
    var FA = function (x) { return Phi(x - 2); };
    var fM = function (x) { return c * fA(x) + (1 - c) * fI(x); };
    var FM = function (x) { return c * FA(x) + (1 - c) * FI(x); };
    var tDefer = probit(0.8);                          // defer above the 80th percentile
    var tAudit = probit(1 - Math.pow(0.01, 1 / k));    // audit the top 1% of innocent minima
    var fMinI = [], fMinA = [], fAtk = [], i, x, tail;
    for (i = 0; i < GRID.length; i++) {
      x = GRID[i];
      fMinI.push(k * fI(x) * Math.pow(1 - FI(x), k - 1));
      tail = Math.pow(1 - FM(x), Math.max(0, k - 2));
      fMinA.push(fA(x) * Math.pow(1 - FM(x), k - 1) + (k - 1) * fM(x) * (1 - FA(x)) * tail);
      fAtk.push(fA(x) * Math.pow(1 - FM(x), k - 1) + (k - 1) * c * fA(x) * (1 - FA(x)) * tail);
    }
    var pWin = (1 - FA(tAudit)) * Math.pow(1 - FM(tAudit), k - 1);
    var cut = Math.min(tDefer, tAudit), pLose = 0;
    for (i = 0; i < GRID.length && !(GRID[i] > cut); i++) { pLose += DX * fAtk[i]; }
    pLose = Math.min(pLose, 1 - pWin);
    return {
      fMinI: fMinI, fMinA: fMinA, tDefer: tDefer, tAudit: tAudit,
      pWin: pWin, pLose: pLose, pContinue: Math.max(0, 1 - pWin - pLose),
      pInnocentT: Math.pow(0.2, k)
    };
  }

  var W = 532, H = 190, X0 = 14, Y0 = 20;
  function px(v) { return X0 + (v + 3.5) / 9 * W; }
  function r1(v) { return Math.round(v * 10) / 10; }

  function el(name, attrs, text) {
    var n = document.createElementNS(SVGNS, name), key;
    for (key in attrs) { if (Object.prototype.hasOwnProperty.call(attrs, key)) { n.setAttribute(key, attrs[key]); } }
    if (text !== undefined) { n.appendChild(document.createTextNode(text)); }
    return n;
  }
  function path(vals, scale) {
    var d = '', i;
    for (i = 0; i < vals.length; i++) {
      d += (i === 0 ? 'M ' : 'L ') + r1(px(GRID[i])) + ' ' + r1(Y0 + H - vals[i] / scale * H) + ' ';
    }
    return d;
  }
  function pct(v) { return (100 * v).toFixed(v >= 0.1 ? 0 : 1) + '%'; }

  var chart = document.getElementById('chart');
  var kIn = document.getElementById('k'), cIn = document.getElementById('c');
  var seenK = false, seenC = false, completed = false;

  function draw(k, c) {
    var m = model(k, c), i;
    var scale = 0;
    for (i = 0; i < m.fMinI.length; i++) { if (m.fMinI[i] > scale) { scale = m.fMinI[i]; } }
    for (i = 0; i < m.fMinA.length; i++) { if (m.fMinA[i] > scale) { scale = m.fMinA[i]; } }
    scale *= 1.08;

    while (chart.firstChild) { chart.removeChild(chart.firstChild); }
    chart.appendChild(el('rect', { x: r1(px(m.tAudit)), y: Y0, width: r1(Math.max(0, X0 + W - px(m.tAudit))), height: H, fill: MUTED, opacity: 0.07 }));
    chart.appendChild(el('line', { x1: X0, x2: X0 + W, y1: Y0 + H, y2: Y0 + H, stroke: BORDER, 'stroke-width': 1 }));
    chart.appendChild(el('path', { d: path(m.fMinI, scale), fill: 'none', stroke: MUTED, 'stroke-width': 1.8, 'stroke-dasharray': '5 3' }));
    chart.appendChild(el('path', { d: path(m.fMinA, scale), fill: 'none', stroke: ACCENT, 'stroke-width': 2 }));

    chart.appendChild(el('line', { x1: r1(px(m.tDefer)), x2: r1(px(m.tDefer)), y1: Y0, y2: Y0 + H, stroke: '#1a1a1a', 'stroke-width': 1, 'stroke-dasharray': '3 3' }));
    chart.appendChild(el('text', { x: r1(px(m.tDefer)) + 4, y: Y0 + 26, 'font-size': 12, fill: '#1a1a1a' }, 'defer to T →'));
    chart.appendChild(el('line', { x1: r1(px(m.tAudit)), x2: r1(px(m.tAudit)), y1: Y0, y2: Y0 + H, stroke: MUTED, 'stroke-width': 1, 'stroke-dasharray': '3 3' }));
    chart.appendChild(el('text', { x: r1(px(m.tAudit)) + 4, y: Y0 + 11, 'font-size': 12, fill: MUTED }, 'audit (top 1% of innocent minima) →'));
    chart.appendChild(el('text', { x: X0 + W / 2, y: Y0 + H + 24, 'font-size': 12, fill: MUTED, 'text-anchor': 'middle' }, 'more suspicious →'));

    document.getElementById('s-win').textContent = pct(m.pWin);
    document.getElementById('s-lose').textContent = pct(m.pLose);
    document.getElementById('s-cont').textContent = pct(m.pContinue);
    document.getElementById('s-innt').textContent = pct(m.pInnocentT);
    return m;
  }

  function render(save) {
    var k = Number(kIn.value), c = Number(cIn.value) / 100;
    document.getElementById('kval').textContent = String(k);
    document.getElementById('cval').textContent = Math.round(c * 100) + '%';
    document.getElementById('leg-i').textContent = 'innocent step, min of ' + k + ' sample' + (k > 1 ? 's' : '');
    document.getElementById('leg-a').textContent = 'attacked step, min of ' + k;
    var m = draw(k, c);

    if (k !== 3) { seenK = true; }
    if (c < 1) { seenC = true; }
    document.getElementById('chk-k').className = seenK ? 'done' : '';
    document.getElementById('chk-c').className = seenC ? 'done' : '';
    document.getElementById('chk-k').firstChild.textContent = seenK ? '✓' : '';
    document.getElementById('chk-c').firstChild.textContent = seenC ? '✓' : '';
    document.getElementById('done-msg').hidden = !(seenK && seenC);

    if (save && window.Lens) {
      var summary = 'Defer to resample demo. Current setting: k = ' + k + ' samples per step, attack continuation probability c = '
        + Math.round(c * 100) + '%. For one attacked step: win (audited) ' + pct(m.pWin)
        + ', lose (attack executed unaudited) ' + pct(m.pLose) + ', continue (attack fizzles) ' + pct(m.pContinue)
        + '. Innocent steps deferred to the trusted model: ' + pct(m.pInnocentT) + '. '
        + (seenK ? 'The learner has varied k. ' : 'The learner has not yet varied k. ')
        + (seenC ? 'The learner has lowered c below 100%.' : 'The learner has not yet lowered c below 100%.');
      window.Lens.saveState({ k: k, c: c, seenK: seenK, seenC: seenC }, summary);
      if (seenK && seenC && !completed) { completed = true; window.Lens.complete(); }
    }
  }

  kIn.addEventListener('input', function () { render(true); });
  cIn.addEventListener('input', function () { render(true); });
  document.getElementById('reset').addEventListener('click', function () {
    kIn.value = 3; cIn.value = 100; render(true);
  });

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state, meta) {
      if (state) {
        if (state.k) { kIn.value = state.k; }
        if (state.c) { cIn.value = Math.round(state.c * 100); }
        seenK = !!state.seenK; seenC = !!state.seenC;
      }
      if (meta && meta.completed) { completed = true; seenK = true; seenC = true; }
      render(false);
    });
  }
  render(false);
}());
</script>
</body>
</html>

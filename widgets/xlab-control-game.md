---
id: '3c0d7d99-c6f2-446c-8269-0a5b6e24c0f6'
title: The control game
summary_for_tutor: "A playable model of the whole control game of Greenblatt et al.'s AI control paper, against a red team that always best-responds. The learner sets three blue-team knobs: the audit budget b (share of solutions H can audit), the defer band d (suspicion band just below the audit line where T rewrites the solution instead), and monitor quality as AUC. Tab 'Protocol' shows the suspicion-score distributions with the audit and defer bands marked, the safety/usefulness frontier traced by sweeping the defer band, and readouts for safety, usefulness and the red team's chosen attack rate and obfuscation effort. Tab 'Red team' shows the red team's win probability over its whole strategy plane (opportunity cutoff against obfuscation effort) as a heat map with the best response ringed, plus the two marginal curves: the attack-rate hump, which peaks at a low but non-zero rate because attacking more dilutes the pool with worse opportunities, and the subtlety curve, which peaks in the interior because subtler backdoors are caught less often but are more often simply broken. Usefulness here is modelled as 1 minus the deferred fraction. The numbers are a model built for intuition, not a re-run of the paper's experiments."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from the "attack-rate", "subtlety", "best-response", "defer" and
     "control-dashboard" demos on XLab's AI Control track (aisafetytracks.com),
     rebuilt as vanilla HTML/JS in the Lens look. -->
<style>
:root{
  --bg:#ffffff; --page:#faf8f3; --text:#1a1a1a; --muted:#5a5a5a; --border:#e8e5df;
  --accent:#b87018; --accent-hover:#9a5c10;
  --font-ui:"DM Sans",Arial,sans-serif; --font-heading:"Newsreader",Georgia,serif;
}
*{box-sizing:border-box}
body{margin:0;padding:16px;font:14px/1.5 var(--font-ui);color:var(--text);background:var(--bg)}
h2{font-family:var(--font-heading);font-weight:600;margin:0 0 4px;font-size:17px}
.eyebrow{font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--muted);margin:0 0 6px}
.desc{color:var(--muted);margin:0 0 12px}
.tabs{display:flex;gap:6px;margin:0 0 14px;flex-wrap:wrap}
button{font:inherit;color:inherit;border:1px solid var(--border);border-radius:8px;background:#fff;padding:7px 10px;cursor:pointer}
button:hover{background:var(--page)}
button.is-active{border-color:var(--text);box-shadow:0 0 0 1px var(--text)}
.knobs{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:0 0 14px}
.ctl label{display:flex;justify-content:space-between;gap:8px;font-size:13px}
.ctl label .name{color:var(--muted)}
.ctl label .val{font-weight:600;font-variant-numeric:tabular-nums}
input[type=range]{width:100%;accent-color:var(--accent)}
.row{display:flex;gap:14px;flex-wrap:wrap}
.col{flex:1 1 250px;min-width:0}
.plotlabel{text-align:center;font-size:12px;font-weight:500;color:var(--muted);margin:0 0 2px}
svg{width:100%;height:auto;display:block}
canvas{width:100%;height:auto;display:block;border:1px solid var(--border);border-radius:6px;image-rendering:pixelated}
.canvaswrap{position:relative}
.canvaswrap svg{position:absolute;left:0;top:0;width:100%;height:100%}
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;border:1px solid var(--border);border-radius:8px;background:var(--page);padding:12px;text-align:center;margin-top:12px}
.stats .k{font-size:11px;color:var(--muted);margin:0}
.stats .v{font-weight:600;font-variant-numeric:tabular-nums;margin:2px 0 0}
.note{font-size:13px;color:var(--muted);margin-top:12px}
@media (max-width:520px){ .knobs{grid-template-columns:1fr} .stats{grid-template-columns:repeat(2,1fr)} }
</style>
</head>
<body>
<p class="eyebrow">Blue team knobs, red team best response</p>
<h2>The control game</h2>
<p class="desc">Set the protocol; the red team re-optimises against whatever you set. Safety is always measured against that best response, so every number below already assumes the untrusted model is playing as well as it can.</p>

<div class="knobs">
  <div class="ctl">
    <label for="kb"><span class="name">Audit budget (b)</span><span class="val" id="kbV">2.0%</span></label>
    <input type="range" id="kb" min="5" max="100" step="1" value="20" aria-label="Audit budget">
  </div>
  <div class="ctl">
    <label for="kd"><span class="name">Defer band (d)</span><span class="val" id="kdV">8.0%</span></label>
    <input type="range" id="kd" min="0" max="500" step="1" value="80" aria-label="Defer band">
  </div>
  <div class="ctl">
    <label for="kq"><span class="name">Monitor quality (AUC)</span><span class="val" id="kqV">0.97</span></label>
    <input type="range" id="kq" min="800" max="990" step="1" value="970" aria-label="Monitor quality">
  </div>
</div>

<div class="tabs">
  <button id="tab0" class="is-active">Protocol</button>
  <button id="tab1">Red team</button>
</div>

<div id="pane"></div>

<div class="stats">
  <div><p class="k">Safety</p><p class="v" id="sSafe">-</p></div>
  <div><p class="k">Usefulness</p><p class="v" id="sUse">-</p></div>
  <div><p class="k">Red attack rate</p><p class="v" id="sRate">-</p></div>
  <div><p class="k">Obfuscation effort</p><p class="v" id="sSig">-</p></div>
</div>

<p class="note">A model built for intuition, not a re-run of the paper's experiments. Opportunity quality is drawn from a Beta(2,5), a subtler backdoor is caught less often but is more often simply broken, and usefulness is charged as the share of problems handed to the weaker model.</p>

<script>
"use strict";
var SQ2 = Math.SQRT2;
function erf(x){
  var s = x < 0 ? -1 : 1, a = Math.abs(x);
  var t = 1/(1 + 0.3275911*a);
  var y = 1 - ((((1.061405429*t - 1.453152027)*t + 1.421413741)*t - 0.284496736)*t + 0.254829592)*t*Math.exp(-a*a);
  return s*y;
}
function Phi(z){ return 0.5*(1 + erf(z/SQ2)); }
function phi(z){ return Math.exp(-0.5*z*z)/Math.sqrt(2*Math.PI); }
function probit(p){
  if(p <= 0) return -8; if(p >= 1) return 8;
  var q, r;
  if(p < 0.02425){
    q = Math.sqrt(-2*Math.log(p));
    return (((((-0.007784894002430293*q - 0.3223964580411365)*q - 2.400758277161838)*q - 2.549732539343734)*q + 4.374664141464968)*q + 2.938163982698783) /
           ((((0.007784695709041462*q + 0.3224671290700398)*q + 2.445134137142996)*q + 3.754408661907416)*q + 1);
  }
  if(p > 0.97575){
    q = Math.sqrt(-2*Math.log(1-p));
    return -((((((-0.007784894002430293*q - 0.3223964580411365)*q - 2.400758277161838)*q - 2.549732539343734)*q + 4.374664141464968)*q + 2.938163982698783) /
             ((((0.007784695709041462*q + 0.3224671290700398)*q + 2.445134137142996)*q + 3.754408661907416)*q + 1));
  }
  q = p - 0.5; r = q*q;
  return (((((-39.69683028665376*r + 220.9460984245205)*r - 275.9285104469687)*r + 138.357751867269)*r - 30.66479806614716)*r + 2.506628277459239)*q /
         (((((-54.47609879822406*r + 161.5858368580409)*r - 155.6989798598866)*r + 66.80131188771972)*r - 13.28068155288572)*r + 1);
}

var N = 5000, ATTACK_SD = 0.9, SUBTLETY_VIS = 0.4, GAMMA = 0.3;
var P0 = 0.75, ALPHA = 1.3, G_BINS = 256, NG = 120, NS = 96;

var GRID = (function(){
  var g = new Float64Array(G_BINS), w = new Float64Array(G_BINS), step = 1/G_BINS, tot = 0, i;
  for(i=0;i<G_BINS;i++){
    var x = (i + 0.5)*step;
    g[i] = x;
    w[i] = 30*x*Math.pow(1-x, 4)*step;   // Beta(2,5) density times bin width
    tot += w[i];
  }
  for(i=0;i<G_BINS;i++){ w[i] /= tot; }
  return {g:g, w:w};
})();

var GSTARS = [], SIGMAS = [], GIDX = [], i0;
for(i0=0;i0<NG;i0++) GSTARS.push(i0/(NG-1)*0.995);
for(i0=0;i0<NS;i0++) SIGMAS.push(i0/(NS-1));
GSTARS.forEach(function(gs){
  var idx = 0;
  while(idx < G_BINS && GRID.g[idx] <= gs) idx++;
  GIDX.push(idx);
});

function muOf(q){ return Math.sqrt(1 + ATTACK_SD*ATTACK_SD)*probit(q); }
function attackMean(mu, sigma, g){ return mu*(1 - SUBTLETY_VIS*sigma) - GAMMA*g; }
function pWorks(sigma){ return P0*Math.pow(Math.max(0, 1 - sigma), ALPHA); }
function attackRate(gStar){
  var t = 0;
  for(var i=0;i<G_BINS;i++){ if(GRID.g[i] > gStar) t += GRID.w[i]; }
  return t;
}

function finish(agg){
  var e = agg.wBar + agg.cBar;
  if(agg.r === 0 || e <= 0) return {pRedWin:0, termA:0, termB:0};
  var A = agg.wBar/e;
  var B = 1 - Math.pow(1 - agg.r*e, N);
  return {pRedWin:A*B, termA:A, termB:B};
}

// Full best-response search with suffix sums over the opportunity grid.
function solve(b, d, q, wantGrid){
  var mu = muOf(q), aT = probit(1-b), dT = probit(1-d);
  var best = null, bestG = 0, bestS = 0;
  var grid = wantGrid ? [] : null;
  var cS = new Float64Array(G_BINS+1), fS = new Float64Array(G_BINS+1),
      shS = new Float64Array(G_BINS+1), wS = new Float64Array(G_BINS+1);
  for(var si=0; si<NS; si++){
    var sigma = SIGMAS[si], ps = pWorks(sigma);
    for(var i=G_BINS-1;i>=0;i--){
      var m = attackMean(mu, sigma, GRID.g[i]);
      var ct = Phi((m - aT)/ATTACK_SD);
      var sh = Phi((dT - m)/ATTACK_SD);
      var df = Math.max(0, 1 - ct - sh);
      cS[i] = cS[i+1] + GRID.w[i]*ct;
      fS[i] = fS[i+1] + GRID.w[i]*df;
      shS[i] = shS[i+1] + GRID.w[i]*sh;
      wS[i] = wS[i+1] + GRID.w[i];
    }
    var rowVals = wantGrid ? new Float64Array(NG) : null;
    for(var gi=0; gi<NG; gi++){
      var idx = GIDX[gi], r = wS[idx], res;
      if(r === 0){ res = {pRedWin:0, termA:0, termB:0}; }
      else {
        res = finish({r:r, cBar:cS[idx]/r, fBar:fS[idx]/r, shipBar:shS[idx]/r, wBar:shS[idx]/r*ps});
      }
      if(rowVals) rowVals[gi] = res.pRedWin;
      if(!best || res.pRedWin > best.pRedWin){ best = res; bestG = gi; bestS = si; }
    }
    if(grid) grid.push(rowVals);
  }
  return {best:best, gi:bestG, si:bestS, grid:grid,
          gStar:GSTARS[bestG], sigma:SIGMAS[bestS], rate:attackRate(GSTARS[bestG])};
}

function usefulness(b, d){ return 1 - Math.min(1, Math.max(0, d - b)); }

// ---------- drawing helpers ----------
function svgEl(n, a){ var e = document.createElementNS("http://www.w3.org/2000/svg", n); for(var k in a){ e.setAttribute(k, a[k]); } return e; }
function txt(x,y,s,anchor){ var t = svgEl("text",{x:x,y:y,"font-size":9,fill:"var(--muted)","text-anchor":anchor||"start"}); t.textContent = s; return t; }
function el(tag, cls, t){ var n = document.createElement(tag); if(cls) n.className = cls; if(t != null) n.textContent = t; return n; }

function drawDists(svg, b, d, q, sol){
  svg.textContent = "";
  var X0 = 12, W = 276, Y0 = 10, H = 118;
  var zMin = -3.2, zMax = 5.0;
  var xOf = function(z){ return X0 + (z - zMin)/(zMax - zMin)*W; };
  var mu = muOf(q), sigma = sol.sigma, gStar = sol.gStar;
  var peak = 1/Math.sqrt(2*Math.PI);
  var pts = 180, inn = [], att = [], i, j;
  var wSum = 0;
  for(j=0;j<G_BINS;j++){ if(GRID.g[j] > gStar) wSum += GRID.w[j]; }
  for(i=0;i<=pts;i++){
    var z = zMin + (zMax - zMin)*i/pts;
    inn.push(phi(z));
    var v = 0;
    if(wSum > 0){
      for(j=0;j<G_BINS;j+=4){
        if(GRID.g[j] <= gStar) continue;
        v += GRID.w[j]*4*phi((z - attackMean(mu, sigma, GRID.g[j]))/ATTACK_SD)/ATTACK_SD;
      }
      v /= wSum;
    }
    att.push(v);
    if(v > peak) peak = v;
  }
  peak *= 1.08;
  var yOf = function(v){ return Y0 + H - Math.min(1, v/peak)*H; };
  var aT = probit(1-b), dT = probit(1-d);
  svg.appendChild(svgEl("rect",{x:xOf(aT),y:Y0,width:Math.max(0,(X0+W)-xOf(aT)),height:H,fill:"var(--muted)",opacity:0.09}));
  if(dT < aT){
    svg.appendChild(svgEl("rect",{x:xOf(dT),y:Y0,width:Math.max(0,xOf(aT)-xOf(dT)),height:H,fill:"var(--accent)",opacity:0.14}));
  }
  svg.appendChild(svgEl("line",{x1:X0,x2:X0+W,y1:Y0+H,y2:Y0+H,stroke:"var(--border)","stroke-width":1}));
  function path(arr, color, width){
    var dd = [];
    for(var i2=0;i2<=pts;i2++){
      var z2 = zMin + (zMax - zMin)*i2/pts;
      dd.push((i2===0?"M ":"L ") + xOf(z2).toFixed(1) + " " + yOf(arr[i2]).toFixed(1));
    }
    svg.appendChild(svgEl("path",{d:dd.join(" "),fill:"none",stroke:color,"stroke-width":width}));
  }
  path(inn, "var(--muted)", 1.5);
  path(att, "var(--accent)", 2);
  svg.appendChild(svgEl("line",{x1:xOf(aT),x2:xOf(aT),y1:Y0,y2:Y0+H,stroke:"var(--text)","stroke-width":1,"stroke-dasharray":"3 3"}));
  svg.appendChild(txt(Math.min(X0+W, xOf(aT))-3, Y0+10, "audit", "end"));
  if(dT < aT) svg.appendChild(txt(xOf(dT)+3, Y0+10, "defer band"));
  svg.appendChild(txt(X0+W/2, 146, "more suspicious", "middle"));
}

function drawFrontier(svg, b, q, curB, curD){
  svg.textContent = "";
  var X0 = 30, W = 254, Y0 = 10, H = 118;
  svg.appendChild(svgEl("rect",{x:X0,y:Y0,width:W,height:H,fill:"none",stroke:"var(--border)","stroke-width":1,opacity:0.6}));
  var pts = [], t;
  for(t=0;t<=16;t++){
    var dd = b + 0.5*t/16;
    var s = solve(b, dd, q, false);
    pts.push({u:usefulness(b, dd), s:1 - s.best.pRedWin});
  }
  var dpath = pts.map(function(p,i){ return (i===0?"M ":"L ") + (X0 + p.u*W).toFixed(1) + " " + (Y0 + H - p.s*H).toFixed(1); }).join(" ");
  svg.appendChild(svgEl("path",{d:dpath,fill:"none",stroke:"var(--muted)","stroke-width":1.5}));
  var cur = solve(curB, curD, q, false);
  var cu = usefulness(curB, curD), cs = 1 - cur.best.pRedWin;
  svg.appendChild(svgEl("circle",{cx:(X0 + cu*W).toFixed(1),cy:(Y0 + H - cs*H).toFixed(1),r:4,
    fill:"var(--accent)",stroke:"#fff","stroke-width":1.5}));
  svg.appendChild(txt(26, Y0+8, "100", "end"));
  svg.appendChild(txt(26, Y0+H, "0", "end"));
  svg.appendChild(txt(X0+W/2, 146, "usefulness", "middle"));
  var lab = svgEl("text",{x:10,y:Y0+H/2,"font-size":9,fill:"var(--muted)","text-anchor":"middle",
    transform:"rotate(-90 10 " + (Y0+H/2) + ")"});
  lab.textContent = "safety"; svg.appendChild(lab);
}

function drawHeat(canvas, overlay, sol){
  var ctx = canvas.getContext("2d");
  canvas.width = NG; canvas.height = NS;
  var img = ctx.createImageData(NG, NS);
  var max = 0, si, gi;
  for(si=0; si<NS; si++){ for(gi=0; gi<NG; gi++){ if(sol.grid[si][gi] > max) max = sol.grid[si][gi]; } }
  if(max <= 0) max = 1;
  for(si=0; si<NS; si++){
    for(gi=0; gi<NG; gi++){
      var v = sol.grid[si][gi]/max;
      var p = ((NS-1-si)*NG + gi)*4;
      img.data[p]   = Math.round(255 + (184-255)*v);
      img.data[p+1] = Math.round(250 + (112-250)*v);
      img.data[p+2] = Math.round(243 + (24-243)*v);
      img.data[p+3] = 255;
    }
  }
  ctx.putImageData(img, 0, 0);
  overlay.textContent = "";
  overlay.setAttribute("viewBox", "0 0 " + NG + " " + NS);
  overlay.setAttribute("preserveAspectRatio", "none");
  overlay.appendChild(svgEl("circle",{cx:(sol.gi + 0.5), cy:(NS - 0.5 - sol.si), r:4,
    fill:"none", stroke:"#1a1a1a", "stroke-width":1.4, vectorEffect:"non-scaling-stroke"}));
}

function drawLine(svg, xs, ys, markIdx, xlab, xlo, xhi){
  svg.textContent = "";
  var X0 = 30, W = 258, Y0 = 10, H = 100;
  var max = 0, i;
  for(i=0;i<ys.length;i++){ if(ys[i] > max) max = ys[i]; }
  max = Math.max(max, 1e-6)*1.1;
  [0,0.5,1].forEach(function(f){
    svg.appendChild(svgEl("line",{x1:X0,x2:X0+W,y1:Y0+H*(1-f),y2:Y0+H*(1-f),stroke:"var(--border)","stroke-width":1}));
  });
  var d = [];
  for(i=0;i<xs.length;i++){
    d.push((i===0?"M ":"L ") + (X0 + xs[i]*W).toFixed(1) + " " + (Y0 + H - ys[i]/max*H).toFixed(1));
  }
  svg.appendChild(svgEl("path",{d:d.join(" "),fill:"none",stroke:"var(--accent)","stroke-width":2}));
  svg.appendChild(svgEl("circle",{cx:(X0 + xs[markIdx]*W).toFixed(1), cy:(Y0 + H - ys[markIdx]/max*H).toFixed(1),
    r:4, fill:"var(--accent)", stroke:"#fff", "stroke-width":1.5}));
  svg.appendChild(txt(26, Y0+8, (max*100).toFixed(0)+"%", "end"));
  svg.appendChild(txt(26, Y0+H, "0%", "end"));
  svg.appendChild(txt(X0, 128, xlo));
  svg.appendChild(txt(X0+W, 128, xhi, "end"));
  svg.appendChild(txt(X0+W/2, 128, xlab, "middle"));
}

// ---------- state ----------
var b = 0.02, d = 0.08, q = 0.97, tab = 0;
var cache = null;

function currentSolve(wantGrid){
  var key = b + "|" + d + "|" + q + "|" + (wantGrid ? 1 : 0);
  if(cache && cache.key === key) return cache.val;
  var v = solve(b, d, q, wantGrid);
  cache = {key:key, val:v};
  return v;
}

function renderProtocol(pane, sol){
  var row = el("div","row");
  var c1 = el("div","col"); c1.appendChild(el("p","plotlabel","Suspicion scores: innocent and attacked"));
  var s1 = svgEl("svg",{viewBox:"0 0 300 150",role:"img","aria-label":"Suspicion distributions with the audit and defer bands"});
  c1.appendChild(s1); row.appendChild(c1);
  var c2 = el("div","col"); c2.appendChild(el("p","plotlabel","Safety / usefulness frontier"));
  var s2 = svgEl("svg",{viewBox:"0 0 300 150",role:"img","aria-label":"Safety against usefulness as the defer band is swept"});
  c2.appendChild(s2); row.appendChild(c2);
  pane.appendChild(row);
  drawDists(s1, b, d, q, sol);
  drawFrontier(s2, b, q, b, d);
  pane.appendChild(el("p","note","The grey curve is the frontier traced by sweeping the defer band at this audit budget and monitor quality; the dot is where your protocol sits on it. A better monitor or a larger budget lifts the whole curve up and to the right."));
}

function renderRed(pane, sol){
  var wrap = el("div","canvaswrap");
  wrap.appendChild(el("p","plotlabel","P(red wins) over the red team's strategy plane"));
  var inner = el("div"); inner.style.position = "relative";
  var canvas = document.createElement("canvas");
  canvas.setAttribute("role","img");
  canvas.setAttribute("aria-label","Heat map of the red team's win probability over opportunity cutoff and obfuscation effort");
  canvas.style.aspectRatio = "120 / 96";
  var ov = svgEl("svg",{});
  inner.appendChild(canvas); inner.appendChild(ov);
  wrap.appendChild(inner);
  pane.appendChild(wrap);
  drawHeat(canvas, ov, sol);
  var axes = el("p","plotlabel","left to right: attack often to attack rarely. bottom to top: blatant to maximally subtle. the ring is the best response.");
  axes.style.marginTop = "6px";
  pane.appendChild(axes);

  var row = el("div","row");
  var c1 = el("div","col"); c1.appendChild(el("p","plotlabel","The attack-rate hump (at the best subtlety)"));
  var s1 = svgEl("svg",{viewBox:"0 0 300 135",role:"img","aria-label":"Red team win probability against attack rate"});
  c1.appendChild(s1); row.appendChild(c1);
  var c2 = el("div","col"); c2.appendChild(el("p","plotlabel","Subtlety: visible against reliable"));
  var s2 = svgEl("svg",{viewBox:"0 0 300 135",role:"img","aria-label":"Red team win probability against obfuscation effort"});
  c2.appendChild(s2); row.appendChild(c2);
  pane.appendChild(row);

  var xs = [], ys = [], i;
  for(i=0;i<NG;i++){ xs.push(i/(NG-1)); ys.push(sol.grid[sol.si][i]); }
  drawLine(s1, xs, ys, sol.gi, "opportunity cutoff", "attack often", "attack rarely");
  var xs2 = [], ys2 = [];
  for(i=0;i<NS;i++){ xs2.push(i/(NS-1)); ys2.push(sol.grid[i][sol.gi]); }
  drawLine(s2, xs2, ys2, sol.si, "obfuscation effort", "blatant", "maximally subtle");
  pane.appendChild(el("p","note","Attack rarely and a decisive attempt may never happen; attack often and the extra attempts come from problems where a backdoor has less natural cover, so the monitor catches them. Both curves peak in the interior, which is why the paper's red team attacks on a small fraction of problems with moderate obfuscation."));
}

function summary(sol){
  return "Control game widget. The learner has the audit budget at " + (b*100).toFixed(1) +
    "%, the defer band at " + (d*100).toFixed(1) + "% and monitor quality at AUC " + q.toFixed(2) +
    ". Against the red team's best response this gives safety " + ((1 - sol.best.pRedWin)*100).toFixed(0) +
    "% and usefulness " + (usefulness(b,d)*100).toFixed(0) + "%. The red team's best response attacks on " +
    (sol.rate*100).toFixed(2) + "% of problems at obfuscation effort " + sol.sigma.toFixed(2) + ".";
}

var saveTimer = null;
function save(sol){
  if(!window.Lens) return;
  if(saveTimer) clearTimeout(saveTimer);
  saveTimer = setTimeout(function(){ Lens.saveState({b:b, d:d, q:q, tab:tab}, summary(sol)); }, 500);
}

function render(){
  document.getElementById("kbV").textContent = (b*100).toFixed(1) + "%";
  document.getElementById("kdV").textContent = (d*100).toFixed(1) + "%";
  document.getElementById("kqV").textContent = q.toFixed(2);
  document.getElementById("tab0").className = tab === 0 ? "is-active" : "";
  document.getElementById("tab1").className = tab === 1 ? "is-active" : "";
  var sol = currentSolve(tab === 1);
  var pane = document.getElementById("pane");
  pane.textContent = "";
  if(tab === 0) renderProtocol(pane, sol); else renderRed(pane, sol);
  document.getElementById("sSafe").textContent = ((1 - sol.best.pRedWin)*100).toFixed(0) + "%";
  document.getElementById("sUse").textContent = (usefulness(b,d)*100).toFixed(0) + "%";
  document.getElementById("sRate").textContent = (sol.rate*100).toFixed(2) + "%";
  document.getElementById("sSig").textContent = sol.sigma.toFixed(2);
  save(sol);
}

var pending = null;
function schedule(){
  if(pending) clearTimeout(pending);
  pending = setTimeout(render, 90);
}

document.getElementById("kb").addEventListener("input", function(e){ b = Number(e.target.value)/1000; if(d < b) d = b; document.getElementById("kd").value = String(Math.round(d*1000)); schedule(); });
document.getElementById("kd").addEventListener("input", function(e){ d = Math.max(b, Number(e.target.value)/1000); schedule(); });
document.getElementById("kq").addEventListener("input", function(e){ q = Number(e.target.value)/1000; schedule(); });
document.getElementById("tab0").addEventListener("click", function(){ tab = 0; render(); });
document.getElementById("tab1").addEventListener("click", function(){ tab = 1; render(); });

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(state){
      if(typeof state.b === "number") b = state.b;
      if(typeof state.d === "number") d = Math.max(b, state.d);
      if(typeof state.q === "number") q = state.q;
      if(typeof state.tab === "number") tab = state.tab;
      document.getElementById("kb").value = String(Math.round(b*1000));
      document.getElementById("kd").value = String(Math.round(d*1000));
      document.getElementById("kq").value = String(Math.round(q*1000));
    }
    render();
  });
}
render();
</script>
</body>
</html>

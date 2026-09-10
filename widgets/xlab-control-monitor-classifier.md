---
id: 'b2edd0e7-cd18-42d2-824a-4653df239c26'
title: The monitor as a noisy classifier
summary_for_tutor: "A two-tab signal-detection model of the trusted monitor in Greenblatt et al.'s AI control paper. Tab 'One monitor': innocent solutions score N(0,1), backdoored ones N(d',1); the learner drags the separation d' and reads the ROC curve, the AUC, and the operating point at the blue team's fixed 2% false-positive rate. The default d' = 1.64 gives AUC 0.88 and a catch rate of 0.338, the paper's reported probability that an attempted backdoor is audited. Tab 'Two monitors, one AUC': Monitor A's attack scores have spread 1.0 and Monitor B's have spread 0.4, so with the same AUC 0.92 A catches about 47% of attacks at a 2% budget and B about 9%; raising B to AUC 0.97 only brings it level with A (47.2% against 47.3%). The lesson is that AUC is threshold-free and therefore says little about safety, while the true-positive rate at a false-positive rate equal to the audit budget predicts it directly. The Gaussian model is an idealisation for intuition, not a fit to the paper's data."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from the "monitor-roc" and "Same number, different safety" demos on XLab's
     AI Control track (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look. -->
<style>
:root{
  --bg:#ffffff; --page:#faf8f3; --text:#1a1a1a; --muted:#5a5a5a; --border:#e8e5df;
  --accent:#b87018; --accent-hover:#9a5c10; --alt:#3b5f86;
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
.ctl{margin:0 0 10px}
.ctl label{display:flex;justify-content:space-between;gap:12px;font-size:13px}
.ctl label .name{color:var(--muted)}
.ctl label .val{font-weight:600;font-variant-numeric:tabular-nums}
input[type=range]{width:100%;accent-color:var(--accent)}
.row{display:flex;gap:14px;flex-wrap:wrap}
.col{flex:1 1 250px;min-width:0}
.plotlabel{text-align:center;font-size:12px;font-weight:500;color:var(--muted);margin:0 0 2px}
svg{width:100%;height:auto;display:block}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;border:1px solid var(--border);border-radius:8px;background:var(--page);padding:12px;text-align:center;margin-top:12px}
.stats .k{font-size:11px;color:var(--muted);margin:0}
.stats .v{font-weight:600;font-variant-numeric:tabular-nums;margin:2px 0 0}
.note{font-size:13px;color:var(--muted);margin-top:12px}
@media (max-width:420px){ .stats{grid-template-columns:1fr} }
</style>
</head>
<body>
<p class="eyebrow">Signal detection</p>
<h2 id="ttl">The monitor as a noisy classifier</h2>
<p class="desc" id="lede"></p>

<div class="tabs">
  <button id="tab0" class="is-active">One monitor</button>
  <button id="tab1">Two monitors, one AUC</button>
</div>

<div id="pane"></div>

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
  var q, r, v;
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
var BUDGET = 0.02;
var THR = probit(1 - BUDGET);              // audit threshold on the innocent scale
function aucOf(mu, sd){ return Phi(mu/Math.sqrt(1 + sd*sd)); }
function muFor(auc, sd){ return Math.sqrt(1 + sd*sd)*probit(auc); }
function tprAt(mu, sd, fpr){ return Phi((mu + probit(fpr))/sd); }

function svgEl(n, a){ var e = document.createElementNS("http://www.w3.org/2000/svg", n); for(var k in a){ e.setAttribute(k, a[k]); } return e; }
function txt(x,y,s,anchor,fill){ var t = svgEl("text",{x:x,y:y,"font-size":9,fill:fill||"var(--muted)","text-anchor":anchor||"start"}); t.textContent = s; return t; }
function el(tag, cls, t){ var n = document.createElement(tag); if(cls) n.className = cls; if(t != null) n.textContent = t; return n; }

// ---- distributions plot -------------------------------------------------
function drawDists(svg, curves, thrZ){
  svg.textContent = "";
  var X0 = 12, W = 276, Y0 = 10, H = 118;
  var zMin = -3.2, zMax = 5.2;
  var xOf = function(z){ return X0 + (z - zMin)/(zMax - zMin)*W; };
  var peak = 0;
  curves.forEach(function(c){ peak = Math.max(peak, 1/(c.sd*Math.sqrt(2*Math.PI))); });
  peak *= 1.08;
  var yOf = function(v){ return Y0 + H - Math.min(1, v/peak)*H; };
  var tx = xOf(thrZ);
  svg.appendChild(svgEl("rect",{x:tx,y:Y0,width:(X0+W)-tx,height:H,fill:"var(--muted)","opacity":0.07}));
  svg.appendChild(svgEl("line",{x1:X0,x2:X0+W,y1:Y0+H,y2:Y0+H,stroke:"var(--border)","stroke-width":1}));
  curves.forEach(function(c){
    var d = [], i;
    for(i=0;i<=180;i++){
      var z = zMin + (zMax - zMin)*i/180;
      var v = phi((z - c.mu)/c.sd)/c.sd;
      d.push((i===0?"M ":"L ") + xOf(z).toFixed(1) + " " + yOf(v).toFixed(1));
    }
    svg.appendChild(svgEl("path",{d:d.join(" "),fill:"none",stroke:c.color,"stroke-width":2}));
  });
  svg.appendChild(svgEl("line",{x1:tx,x2:tx,y1:Y0,y2:Y0+H,stroke:"var(--muted)","stroke-width":1,"stroke-dasharray":"3 3"}));
  svg.appendChild(txt(tx-3, Y0+10, "audit 2%", "end"));
  svg.appendChild(txt(X0+W/2, 146, "more suspicious", "middle"));
}

// ---- ROC plot -----------------------------------------------------------
function drawRoc(svg, monitors){
  svg.textContent = "";
  var X0 = 26, W = 262, Y0 = 10, H = 118;
  var xOf = function(f){ return X0 + f*W; };
  var yOf = function(t){ return Y0 + H - t*H; };
  svg.appendChild(svgEl("rect",{x:X0,y:Y0,width:W,height:H,fill:"none",stroke:"var(--border)","stroke-width":1}));
  svg.appendChild(svgEl("line",{x1:xOf(0),y1:yOf(0),x2:xOf(1),y2:yOf(1),stroke:"var(--muted)","stroke-width":1,"stroke-dasharray":"3 3","stroke-opacity":0.4}));
  svg.appendChild(svgEl("line",{x1:xOf(BUDGET),x2:xOf(BUDGET),y1:Y0,y2:Y0+H,stroke:"var(--muted)","stroke-width":1,"stroke-dasharray":"2 2","stroke-opacity":0.6}));
  monitors.forEach(function(m){
    var d = [], i;
    for(i=0;i<=140;i++){
      var f = Math.max(1e-4, Math.min(0.9999, i/140));
      d.push((i===0?"M ":"L ") + xOf(f).toFixed(1) + " " + yOf(tprAt(m.mu, m.sd, f)).toFixed(1));
    }
    svg.appendChild(svgEl("path",{d:d.join(" "),fill:"none",stroke:m.color,"stroke-width":1.75}));
    svg.appendChild(svgEl("circle",{cx:xOf(BUDGET),cy:yOf(tprAt(m.mu,m.sd,BUDGET)),r:3,fill:m.color,stroke:"#fff","stroke-width":1}));
  });
  svg.appendChild(txt(22, Y0+8, "1", "end"));
  svg.appendChild(txt(22, Y0+H, "0", "end"));
  svg.appendChild(txt(X0, 146, "FPR 0"));
  svg.appendChild(txt(X0+W, 146, "FPR 1", "end"));
  svg.appendChild(txt(X0+W/2, 146, "dotted line: the 2% audit budget", "middle"));
}

// ---- state --------------------------------------------------------------
var tab = 0;
var dprime = 1.64;
var aucA = 0.92, aucB = 0.92;
var SD_A = 1.0, SD_B = 0.4;

function stat(box, k, v){
  var d = el("div"); d.appendChild(el("p","k",k)); d.appendChild(el("p","v",v)); box.appendChild(d);
}

function renderOne(pane){
  document.getElementById("lede").textContent =
    "Innocent solutions and backdoored ones both get a suspicion score; the monitor is good exactly to the extent that the two score distributions pull apart. Drag the separation and watch what the blue team gets at its fixed 2% false-positive threshold.";
  var ctl = el("div","ctl");
  var lab = el("label"); lab.setAttribute("for","dp");
  lab.appendChild(el("span","name","Monitor quality: separation d'"));
  lab.appendChild(el("span","val", dprime.toFixed(2)));
  ctl.appendChild(lab);
  var inp = document.createElement("input");
  inp.type = "range"; inp.id = "dp"; inp.min = "0"; inp.max = "400"; inp.step = "1";
  inp.value = String(Math.round(dprime*100)); inp.setAttribute("aria-label","Monitor quality");
  inp.addEventListener("input", function(e){ dprime = Number(e.target.value)/100; render(); });
  ctl.appendChild(inp);
  pane.appendChild(ctl);

  var row = el("div","row");
  var c1 = el("div","col"); c1.appendChild(el("p","plotlabel","Suspicion scores"));
  var s1 = svgEl("svg",{viewBox:"0 0 300 150",role:"img","aria-label":"Suspicion score distributions"});
  c1.appendChild(s1); row.appendChild(c1);
  var c2 = el("div","col"); c2.appendChild(el("p","plotlabel","ROC curve"));
  var s2 = svgEl("svg",{viewBox:"0 0 300 150",role:"img","aria-label":"ROC curve"});
  c2.appendChild(s2); row.appendChild(c2);
  pane.appendChild(row);

  drawDists(s1, [{mu:0, sd:1, color:"var(--muted)"}, {mu:dprime, sd:1, color:"var(--accent)"}], THR);
  drawRoc(s2, [{mu:dprime, sd:1, color:"var(--accent)"}]);

  var box = el("div","stats");
  stat(box, "AUC", aucOf(dprime, 1).toFixed(3));
  stat(box, "Caught at a 2% budget", (tprAt(dprime,1,BUDGET)*100).toFixed(1) + "%");
  stat(box, "Missed", ((1 - tprAt(dprime,1,BUDGET))*100).toFixed(1) + "%");
  pane.appendChild(box);
  pane.appendChild(el("p","note","At d' = 1.64 the model reproduces the paper's reported figure: a 0.338 probability that an attempted backdoor is audited, at a 2% false-positive rate. Real suspicion scores are not Gaussian; this is an idealisation for building intuition, not a fit to the paper's data."));
}

function renderTwo(pane){
  document.getElementById("lede").textContent =
    "Two monitors drawn from the same model. Monitor A's attack scores are spread wide; Monitor B's are tightly bunched. Give them the same AUC, then give B a better one, and compare what each catches inside the blue team's 2% audit budget.";
  [["A", "aucA", aucA, "var(--accent)"], ["B", "aucB", aucB, "var(--alt)"]].forEach(function(spec){
    var ctl = el("div","ctl");
    var lab = el("label");
    lab.appendChild(el("span","name","Monitor " + spec[0] + " AUC (attack-score spread " + (spec[0]==="A"?SD_A.toFixed(1):SD_B.toFixed(1)) + ")"));
    lab.appendChild(el("span","val", spec[2].toFixed(3)));
    ctl.appendChild(lab);
    var inp = document.createElement("input");
    inp.type = "range"; inp.min = "600"; inp.max = "995"; inp.step = "1";
    inp.value = String(Math.round(spec[2]*1000));
    inp.setAttribute("aria-label", "Monitor " + spec[0] + " AUC");
    inp.addEventListener("input", function(e){
      var v = Number(e.target.value)/1000;
      if(spec[1] === "aucA") aucA = v; else aucB = v;
      render();
    });
    ctl.appendChild(inp);
    pane.appendChild(ctl);
  });

  var muA = muFor(aucA, SD_A), muB = muFor(aucB, SD_B);
  var row = el("div","row");
  var c1 = el("div","col"); c1.appendChild(el("p","plotlabel","Suspicion scores: innocent, A, B"));
  var s1 = svgEl("svg",{viewBox:"0 0 300 150",role:"img","aria-label":"Suspicion score distributions for both monitors"});
  c1.appendChild(s1); row.appendChild(c1);
  var c2 = el("div","col"); c2.appendChild(el("p","plotlabel","ROC curves"));
  var s2 = svgEl("svg",{viewBox:"0 0 300 150",role:"img","aria-label":"ROC curves for monitor A and monitor B"});
  c2.appendChild(s2); row.appendChild(c2);
  pane.appendChild(row);

  drawDists(s1, [{mu:0,sd:1,color:"var(--muted)"},{mu:muA,sd:SD_A,color:"var(--accent)"},{mu:muB,sd:SD_B,color:"var(--alt)"}], THR);
  drawRoc(s2, [{mu:muA,sd:SD_A,color:"var(--accent)"},{mu:muB,sd:SD_B,color:"var(--alt)"}]);

  var box = el("div","stats");
  stat(box, "A caught at 2%", (tprAt(muA,SD_A,BUDGET)*100).toFixed(1) + "%");
  stat(box, "B caught at 2%", (tprAt(muB,SD_B,BUDGET)*100).toFixed(1) + "%");
  stat(box, "Ratio A to B", (tprAt(muA,SD_A,BUDGET)/Math.max(1e-9, tprAt(muB,SD_B,BUDGET))).toFixed(2) + "x");
  pane.appendChild(box);
  pane.appendChild(el("p","note","Set both to 0.92 and the areas under the two curves are identical while the catch rates are not. Then raise B to 0.97: five points of AUC buy it a tie, not a lead. What the blue team spends is a false-positive budget, so the number that predicts safety is the true-positive rate at a false-positive rate equal to that budget."));
}

function summary(){
  if(tab === 0){
    return "Monitor-as-classifier widget, single-monitor view. The learner has the separation at d' = " + dprime.toFixed(2) +
      ", giving AUC " + aucOf(dprime,1).toFixed(3) + " and a catch rate of " + (tprAt(dprime,1,BUDGET)*100).toFixed(1) +
      "% at the 2% audit budget.";
  }
  var muA = muFor(aucA, SD_A), muB = muFor(aucB, SD_B);
  return "Monitor-as-classifier widget, two-monitor view. Monitor A (attack-score spread 1.0) is at AUC " + aucA.toFixed(3) +
    " and catches " + (tprAt(muA,SD_A,BUDGET)*100).toFixed(1) + "% at a 2% budget; Monitor B (spread 0.4) is at AUC " +
    aucB.toFixed(3) + " and catches " + (tprAt(muB,SD_B,BUDGET)*100).toFixed(1) + "%.";
}

var saveTimer = null;
function save(){
  if(!window.Lens) return;
  if(saveTimer) clearTimeout(saveTimer);
  saveTimer = setTimeout(function(){
    Lens.saveState({tab:tab, dprime:dprime, aucA:aucA, aucB:aucB}, summary());
  }, 400);
}

function render(){
  document.getElementById("tab0").className = tab === 0 ? "is-active" : "";
  document.getElementById("tab1").className = tab === 1 ? "is-active" : "";
  var pane = document.getElementById("pane");
  pane.textContent = "";
  if(tab === 0) renderOne(pane); else renderTwo(pane);
  save();
}

document.getElementById("tab0").addEventListener("click", function(){ tab = 0; render(); });
document.getElementById("tab1").addEventListener("click", function(){ tab = 1; render(); });

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(state){
      if(typeof state.tab === "number") tab = state.tab;
      if(typeof state.dprime === "number") dprime = state.dprime;
      if(typeof state.aucA === "number") aucA = state.aucA;
      if(typeof state.aucB === "number") aucB = state.aucB;
    }
    render();
  });
}
render();
</script>
</body>
</html>

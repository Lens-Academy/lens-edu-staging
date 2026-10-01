---
id: 'b20ec941-3eab-44eb-b816-86ec6c721c80'
title: "Same number, different safety, stage 2: higher auc"
summary_for_tutor: "Figure for stage 2 of the 'Same number, different safety' questions in part 3 of the AI control paper lesson. It shows only the ROC curves of two idealised monitors, A (attack-score spread 1.0) and B (spread 0.4), and their AUCs, with no catch rates, so the learner has to predict from the shape of the curves. Monitor A is at AUC 0.92 and Monitor B at 0.97; B's slider is locked for this stage. Do not give the catch rates (at a 2% audit budget: A about 47%; B about 9% at AUC 0.92 and about 47% at 0.97) before the learner has answered the stage's question."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from the "monitor-roc-mini" figure of the "Same number, different safety"
     staged questions on XLab's AI Control track (aisafetytracks.com), rebuilt as
     vanilla HTML/JS in the Lens look. One file per stage; same model as
     xlab-control-same-auc-different-safety. -->
<style>
:root{
  --bg:#ffffff; --page:#faf8f3; --text:#1a1a1a; --muted:#5a5a5a; --border:#e8e5df;
  --accent:#b87018; --accent-hover:#9a5c10;
  --font-ui:"DM Sans",Arial,sans-serif; --font-heading:"Newsreader",Georgia,serif;
}
*{box-sizing:border-box}
body{margin:0;padding:16px;font:14px/1.5 var(--font-ui);color:var(--text);background:var(--bg)}
.desc{color:var(--muted);margin:0 0 14px}
.ctlrow{display:flex;gap:12px;align-items:flex-end;margin:0 0 6px}
.ctl{flex:1 1 auto;min-width:0}
.ctl label{display:flex;flex-wrap:wrap;justify-content:space-between;column-gap:12px;font-size:13px}
.ctl label .name{color:var(--muted)}
.ctl label .val{font-weight:600;font-variant-numeric:tabular-nums;white-space:nowrap}
input[type=range]{width:100%;accent-color:var(--accent)}
button{font:inherit;font-size:13px;color:inherit;border:1px solid var(--border);border-radius:8px;background:#fff;padding:5px 10px;cursor:pointer}
button:hover{background:var(--page)}
.plotlabel{text-align:center;font-size:12px;font-weight:500;color:var(--muted);margin:12px 0 2px}
svg{width:100%;height:auto;display:block}
.legend{display:flex;flex-wrap:wrap;gap:14px;font-size:12px;color:var(--muted);margin-top:6px}
.legend span i{display:inline-block;width:14px;height:8px;vertical-align:middle;margin-right:5px;border-radius:2px}
.note{font-size:13px;color:var(--muted);margin:14px 0 6px}
.stats,.formula{display:grid;gap:10px;border:1px solid var(--border);border-radius:8px;background:var(--page);padding:12px;text-align:center}
.stats{grid-template-columns:repeat(4,1fr)}
.formula{grid-template-columns:1fr auto 1fr auto 1fr;align-items:center;margin-top:8px}
.stats .k,.formula .k{font-size:11px;color:var(--muted);margin:0}
.stats .v,.formula .v{font-weight:600;font-variant-numeric:tabular-nums;margin:2px 0 0}
.formula .op{color:var(--muted);font-size:16px}
@media (max-width:480px){ .stats{grid-template-columns:repeat(2,1fr)} }
h2{font-family:var(--font-heading);font-weight:600;font-size:18px;margin:0 0 4px}
:root{ --alt:#3b5f86 }
#roc{max-width:420px;margin:0 auto}
.auc{text-align:center;font-size:13px;color:var(--muted);margin:6px 0 10px}
.auc b{color:var(--text);font-variant-numeric:tabular-nums}
input[type=range]:disabled{opacity:.55}
</style>
</head>
<body>
<h2>Stage 2: Higher AUC</h2>
<p class="desc">Monitor B is upgraded to AUC 0.97; Monitor A stays at 0.92. Locked for this stage: decide from the shape of the curves.</p>
<svg id="roc" viewBox="0 0 300 160" role="img" aria-label="ROC curves of Monitor A and Monitor B"></svg>
<p class="auc" id="auc"></p>
<div class="ctlrow">
  <div class="ctl">
    <label for="kb"><span class="name" id="kbN"></span><span class="val" id="kbV"></span></label>
    <input type="range" id="kb" min="800" max="980" step="1" value="970" aria-label="Monitor B quality (AUC)">
  </div>
</div>

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


var SD_A = 1.0, SD_B = 0.4, AUC_A = 0.92, LOCKED = true;
var aucB = 0.97;

function drawRoc(svg){
  svg.textContent = "";
  var X0 = 26, W = 262, Y0 = 8, H = 124;
  var xOf = function(f){ return X0 + f*W; }, yOf = function(t){ return Y0 + H - t*H; };
  svg.appendChild(svgEl("rect",{x:X0,y:Y0,width:W,height:H,fill:"none",stroke:"var(--border)","stroke-width":1}));
  svg.appendChild(svgEl("line",{x1:xOf(0),y1:yOf(0),x2:xOf(1),y2:yOf(1),stroke:"var(--muted)","stroke-width":1,"stroke-dasharray":"3 3","stroke-opacity":0.4}));
  svg.appendChild(svgEl("line",{x1:xOf(BUDGET),x2:xOf(BUDGET),y1:Y0,y2:Y0+H,stroke:"var(--muted)","stroke-width":1,"stroke-dasharray":"2 2","stroke-opacity":0.6}));
  svg.appendChild(txt(xOf(BUDGET)+3, Y0+H-4, "2% audit budget"));
  [["A", muFor(aucA, SD_A), SD_A, "var(--accent)", 0.03, -14], ["B", muFor(aucB, SD_B), SD_B, "var(--alt)", 0.05, 6]].forEach(function(m){
    var d = [], i;
    for(i=0;i<=200;i++){
      var t = 6 - 12*i/200;
      d.push((i===0?"M ":"L ") + xOf(1 - Phi(t)).toFixed(1) + " " + yOf(Phi((m[1] - t)/m[2])).toFixed(1));
    }
    svg.appendChild(svgEl("path",{d:d.join(" "),fill:"none",stroke:m[3],"stroke-width":2}));
    var lab = txt(xOf(m[4]) + m[5], yOf(tprAt(m[1], m[2], m[4])) + 4, m[0], "start", m[3]);
    lab.setAttribute("font-size", 12); lab.setAttribute("font-weight", 600);
    svg.appendChild(lab);
  });
  svg.appendChild(txt(26, Y0+8, "1", "end"));
  svg.appendChild(txt(26, Y0+H, "0", "end"));
  svg.appendChild(txt(X0, 146, "0"));
  svg.appendChild(txt(X0+W, 146, "1", "end"));
  svg.appendChild(txt(X0+W/2, 146, "FPR (innocent code flagged)", "middle"));
  var yl = svgEl("text",{x:9,y:Y0+H/2,"font-size":9,fill:"var(--muted)","text-anchor":"middle",transform:"rotate(-90 9 " + (Y0+H/2) + ")"});
  yl.textContent = "TPR (attacks caught)"; svg.appendChild(yl);
}

function render(){
  var muA = muFor(aucA, SD_A), muB = muFor(aucB, SD_B);
  document.getElementById("kAV").textContent = aucA.toFixed(2);
  document.getElementById("kBV").textContent = aucB.toFixed(2);
  drawDists(document.getElementById("dA"), [{mu:0,sd:1,color:"var(--muted)"},{mu:muA,sd:SD_A,color:"var(--accent)"}], THR);
  drawDists(document.getElementById("dB"), [{mu:0,sd:1,color:"var(--muted)"},{mu:muB,sd:SD_B,color:"var(--alt)"}], THR);
  drawRocPlain(document.getElementById("roc"));
  var a = document.getElementById("auc"); a.textContent = "AUC: ";
  var bb = document.createElement("b");
  bb.textContent = Math.abs(aucA - aucB) < 0.0005 ? "A = B = " + aucA.toFixed(2) : "A " + aucA.toFixed(2) + ", B " + aucB.toFixed(2);
  a.appendChild(bb);
  save();
}

var saveTimer = null;
function save(){
  if(!window.Lens || LOCKED) return;
  if(saveTimer) clearTimeout(saveTimer);
  saveTimer = setTimeout(function(){
    Lens.saveState({aucA:aucA, aucB:aucB}, "Stage 2 figure: the learner set Monitor A to AUC " + aucA.toFixed(3) + " and Monitor B to AUC " + aucB.toFixed(3) + ".");
  }, 400);
}

["A","B"].forEach(function(k){
  var inp = document.getElementById("k" + k);
  inp.disabled = LOCKED;
  if(LOCKED) document.getElementById("k" + k + "N").textContent = "Monitor " + k + " quality (locked for this stage)";
  inp.addEventListener("input", function(e){ var v = Number(e.target.value)/1000; if(k === "A") aucA = v; else aucB = v; render(); });
});

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(!LOCKED && state){
      if(typeof state.aucA === "number"){ aucA = state.aucA; document.getElementById("kA").value = String(Math.round(aucA*1000)); }
      if(typeof state.aucB === "number"){ aucB = state.aucB; document.getElementById("kB").value = String(Math.round(aucB*1000)); }
    }
    render();
  });
}
render();
</script>
</body>
</html>

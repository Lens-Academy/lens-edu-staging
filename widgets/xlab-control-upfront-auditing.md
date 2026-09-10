---
id: 'd1e60031-9c60-4ede-9fc9-1313823f7bad'
title: The upfront-auditing tradeoff
summary_for_tutor: "An interactive version of Figure 3 of Greenblatt et al.'s AI control paper. The learner drags the auditing proportion alpha (the share of the 5,000 problems the H budget can audit, 0.1% to 80%) and reads two curves: the blue team's win probability against an optimising red team, and the red team's optimal expected number of backdoor attempts. A second slider, which XLab's own demo does not have, is a Lens addition: it lets the learner move the attack rate p off its optimum and watch RW(p) rise and then fall, which is the non-monotonicity the lens's derivation question asks the learner to explain. The ring on that third chart marks p*. Model: RW(p) = (1-p)^A [1 - (1-0.53p)^B] with A = alpha*5000 audited and B = (1-alpha)*5000 unaudited, 0.53 the GPT-4 correctness rate; p* = ln(1 + 0.53B/A) / (0.53B). At alpha = 2% it reproduces the paper's 15% safety and about 6 expected attempts."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from the "Optimal audit tradeoff" demo on XLab's AI Control track
     (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look.
     The alpha slider, the two curves and the three readouts are XLab's. The
     attack-rate slider and the RW(p) chart below them are ours, not XLab's:
     they make the non-monotonicity in p visible, which is what the lens's
     own derivation question asks the learner to account for. Same model,
     no new constants. -->
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
.desc{color:var(--muted);margin:0 0 14px}
.ctl{margin:0 0 12px}
.ctl label{display:flex;justify-content:space-between;gap:12px;font-size:13px}
.ctl label .name{color:var(--muted)}
.ctl label .val{font-weight:600;font-variant-numeric:tabular-nums}
input[type=range]{width:100%;accent-color:var(--accent)}
.row{display:flex;gap:14px;flex-wrap:wrap}
.col{flex:1 1 240px;min-width:0}
.plotlabel{text-align:center;font-size:12px;font-weight:500;color:var(--muted);margin:0 0 2px}
.plotval{text-align:center;font-size:14px;font-weight:600;font-variant-numeric:tabular-nums;margin:2px 0 0}
svg{width:100%;height:auto;display:block}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;border:1px solid var(--border);border-radius:8px;background:var(--page);padding:12px;text-align:center;margin-top:14px}
.stats .k{font-size:11px;color:var(--muted)}
.stats .v{font-weight:600;font-variant-numeric:tabular-nums}
button{font:inherit;color:inherit;border:1px solid var(--border);border-radius:8px;background:#fff;padding:6px 10px;cursor:pointer}
button:hover{background:var(--page)}
button.is-active{border-color:var(--text);box-shadow:0 0 0 1px var(--text)}
.note{font-size:13px;color:var(--muted);margin-top:10px}
@media (max-width:420px){ .stats{grid-template-columns:1fr} }
</style>
</head>
<body>
<p class="eyebrow">Figure 3, live</p>
<h2>The upfront-auditing tradeoff</h2>
<p class="desc">The protocol audits the first &alpha; share of 5,000 problems. On each problem the attack policy inserts an obvious backdoor with probability p, and a backdoor only wins if the underlying solution was already correct (53% of the time). Move &alpha; and watch what an optimising red team does about it.</p>

<div class="ctl">
  <label for="alpha"><span class="name">Auditing proportion (&alpha;)</span><span class="val" id="alphaV">2.00%</span></label>
  <input type="range" id="alpha" min="1" max="800" step="0.5" value="20" aria-label="Auditing proportion">
</div>

<div class="row">
  <div class="col">
    <p class="plotlabel">Blue team win probability</p>
    <svg id="p1" viewBox="0 0 320 180" role="img" aria-label="Blue team win probability against auditing proportion"></svg>
  </div>
  <div class="col">
    <p class="plotlabel">Optimal expected backdoor attempts</p>
    <svg id="p2" viewBox="0 0 320 180" role="img" aria-label="Optimal expected number of backdoor attempts against auditing proportion"></svg>
  </div>
</div>

<div class="stats">
  <div><p class="k">Optimal p*</p><p class="v" id="sPstar">-</p></div>
  <div><p class="k">Expected attempts p*N</p><p class="v" id="sAtt">-</p></div>
  <div><p class="k">Blue team win</p><p class="v" id="sWin">-</p></div>
</div>

<div class="ctl" style="margin-top:16px">
  <label for="prate"><span class="name">Attack rate p (drag off the optimum)</span><span class="val" id="prateV">-</span></label>
  <input type="range" id="prate" min="0" max="1000" step="1" value="500" aria-label="Attack rate">
  <div style="margin-top:6px"><button id="snap" class="is-active">Hold p at its optimum</button></div>
  <p class="plotlabel" style="margin-top:10px">Red team win probability against p, at this &alpha;</p>
  <svg id="p3" viewBox="0 0 320 150" role="img" aria-label="Red team win probability against attack rate"></svg>
</div>

<p class="note">At &alpha; = 2% the model returns the paper's own numbers: a blue team win probability of about 15%, from roughly six expected backdoor attempts across the deployment.</p>

<script>
"use strict";
var N = 5000, CORRECT = 0.53;
var alpha = 0.02, useOpt = true, pManual = null;

function pStar(a){ var B = (1-a); return Math.log(1 + CORRECT*B/a) / (CORRECT*B*N); }
function redWin(a,p){
  var A = a*N, B = (1-a)*N;
  return Math.pow(1-p, A) * (1 - Math.pow(1 - CORRECT*p, B));
}
function blueWin(a,p){ return 1 - redWin(a,p); }

function svgEl(name, attrs){
  var n = document.createElementNS("http://www.w3.org/2000/svg", name);
  for(var k in attrs){ n.setAttribute(k, attrs[k]); }
  return n;
}
function text(x,y,s,anchor,size){
  var t = svgEl("text",{x:x,y:y,"font-size":size||9,fill:"var(--muted)","text-anchor":anchor||"start"});
  t.textContent = s; return t;
}

var AX = {x0:34, w:272, y0:10, h:146};
function xOfAlpha(a){ return AX.x0 + (a - 0.001)/0.799 * AX.w; }

function drawCurve(svgId, fn, maxV, fmtVal, fmtAxis){
  var svg = document.getElementById(svgId);
  svg.textContent = "";
  [0,0.25,0.5,0.75,1].forEach(function(f){
    svg.appendChild(svgEl("line",{x1:AX.x0,x2:AX.x0+AX.w,y1:AX.y0+AX.h*(1-f),y2:AX.y0+AX.h*(1-f),
      stroke:"var(--border)","stroke-width":1}));
  });
  var d = [], i;
  for(i=0;i<=120;i++){
    var a = 0.001 + 0.799*i/120;
    var v = fn(a);
    var x = xOfAlpha(a), y = AX.y0 + AX.h - Math.min(1, v/maxV)*AX.h;
    d.push((i===0?"M ":"L ") + x.toFixed(2) + " " + y.toFixed(2));
  }
  svg.appendChild(svgEl("path",{d:d.join(" "),fill:"none",stroke:"var(--accent)","stroke-width":2,
    "stroke-linejoin":"round","stroke-linecap":"round"}));
  var cx = xOfAlpha(alpha), cur = fn(alpha);
  var cy = AX.y0 + AX.h - Math.min(1, cur/maxV)*AX.h;
  svg.appendChild(svgEl("line",{x1:cx,x2:cx,y1:AX.y0,y2:AX.y0+AX.h,stroke:"var(--muted)","stroke-width":1,"stroke-opacity":0.4}));
  svg.appendChild(svgEl("circle",{cx:cx,cy:cy,r:5,fill:"var(--accent)",stroke:"#fff","stroke-width":2}));
  svg.appendChild(text(30, AX.y0+8, fmtAxis(maxV), "end"));
  svg.appendChild(text(30, AX.y0+AX.h, fmtAxis(0), "end"));
  svg.appendChild(text(AX.x0, 174, "0.1%"));
  svg.appendChild(text(AX.x0+AX.w, 174, "80%", "end"));
  svg.appendChild(text(AX.x0+AX.w/2, 174, "auditing proportion", "middle"));
  return fmtVal(cur);
}

function drawP3(){
  var svg = document.getElementById("p3");
  svg.textContent = "";
  var x0=34, w=272, y0=10, h=116;
  var pOpt = pStar(alpha);
  var pMax = Math.max(pOpt*6, 0.002);
  var vMax = 0;
  var i, vals = [];
  for(i=0;i<=140;i++){ var p = pMax*i/140; var v = redWin(alpha,p); vals.push(v); if(v>vMax) vMax=v; }
  vMax = Math.max(vMax, 0.05)*1.1;
  var d = [];
  for(i=0;i<=140;i++){
    var x = x0 + w*i/140, y = y0 + h - vals[i]/vMax*h;
    d.push((i===0?"M ":"L ") + x.toFixed(2) + " " + y.toFixed(2));
  }
  [0,0.5,1].forEach(function(f){
    svg.appendChild(svgEl("line",{x1:x0,x2:x0+w,y1:y0+h*(1-f),y2:y0+h*(1-f),stroke:"var(--border)","stroke-width":1}));
  });
  svg.appendChild(svgEl("path",{d:d.join(" "),fill:"none",stroke:"var(--accent)","stroke-width":2}));
  var p = currentP();
  var px = x0 + w*Math.min(1, p/pMax), py = y0 + h - redWin(alpha,p)/vMax*h;
  svg.appendChild(svgEl("line",{x1:px,x2:px,y1:y0,y2:y0+h,stroke:"var(--muted)","stroke-width":1,"stroke-opacity":0.4}));
  svg.appendChild(svgEl("circle",{cx:px,cy:py,r:5,fill:"var(--accent)",stroke:"#fff","stroke-width":2}));
  var ox = x0 + w*Math.min(1, pOpt/pMax);
  svg.appendChild(svgEl("circle",{cx:ox,cy:y0+h-redWin(alpha,pOpt)/vMax*h,r:7,fill:"none",stroke:"var(--text)","stroke-width":1.25}));
  svg.appendChild(text(30, y0+8, (vMax*100).toFixed(0)+"%", "end"));
  svg.appendChild(text(30, y0+h, "0%", "end"));
  svg.appendChild(text(x0, 144, "p = 0"));
  svg.appendChild(text(x0+w, 144, "p = "+(pMax*100).toFixed(2)+"%", "end"));
  svg.appendChild(text(x0+w/2, 144, "ring marks p*", "middle"));
}

function currentP(){
  if(useOpt || pManual === null) return pStar(alpha);
  return pManual;
}

function summary(){
  var p = currentP(), po = pStar(alpha);
  return "Upfront auditing widget. Auditing proportion alpha = " + (alpha*100).toFixed(2) +
    "%. Optimal attack rate p* = " + (po*100).toFixed(3) + "% (about " + (po*N).toFixed(1) +
    " expected backdoor attempts over 5,000 problems), giving a blue team win probability of " +
    (blueWin(alpha,po)*100).toFixed(1) + "%. The learner currently has the attack rate at p = " +
    (p*100).toFixed(3) + "%" + (useOpt ? " (held at the optimum)" : " (moved off the optimum by hand)") +
    ", where the red team wins with probability " + (redWin(alpha,p)*100).toFixed(1) + "%.";
}

var saveTimer = null;
function save(){
  if(!window.Lens) return;
  if(saveTimer) clearTimeout(saveTimer);
  saveTimer = setTimeout(function(){
    Lens.saveState({alpha:alpha, useOpt:useOpt, pManual:pManual}, summary());
  }, 400);
}

function render(){
  document.getElementById("alphaV").textContent = (alpha*100).toFixed(2) + "%";
  var po = pStar(alpha);
  drawCurve("p1", function(a){ return blueWin(a, pStar(a)); }, 1,
    function(v){ return (v*100).toFixed(1)+"%"; }, function(v){ return Math.round(v*100)+"%"; });
  var maxAtt = 0;
  for(var i=0;i<=120;i++){ var a=0.001+0.799*i/120; var v=pStar(a)*N; if(v>maxAtt) maxAtt=v; }
  maxAtt *= 1.08;
  drawCurve("p2", function(a){ return pStar(a)*N; }, maxAtt,
    function(v){ return v.toFixed(1); }, function(v){ return v.toFixed(0); });
  document.getElementById("sPstar").textContent = (po*100).toFixed(3) + "%";
  document.getElementById("sAtt").textContent = (po*N).toFixed(1);
  document.getElementById("sWin").textContent = (blueWin(alpha, po)*100).toFixed(1) + "%";
  var p = currentP();
  document.getElementById("prateV").textContent = (p*100).toFixed(3) + "%";
  var pMax = Math.max(po*6, 0.002);
  document.getElementById("prate").value = String(Math.round(Math.min(1, p/pMax)*1000));
  var snap = document.getElementById("snap");
  snap.className = useOpt ? "is-active" : "";
  snap.textContent = useOpt ? "p is held at its optimum" : "Hold p at its optimum";
  drawP3();
  save();
}

document.getElementById("alpha").addEventListener("input", function(e){
  alpha = Number(e.target.value)/1000;
  if(useOpt) pManual = null;
  render();
});
document.getElementById("prate").addEventListener("input", function(e){
  var pMax = Math.max(pStar(alpha)*6, 0.002);
  pManual = Number(e.target.value)/1000 * pMax;
  useOpt = false;
  render();
});
document.getElementById("snap").addEventListener("click", function(){
  useOpt = true; pManual = null; render();
});

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(state){
      if(typeof state.alpha === "number") alpha = state.alpha;
      if(typeof state.useOpt === "boolean") useOpt = state.useOpt;
      if(typeof state.pManual === "number") pManual = state.pManual;
      document.getElementById("alpha").value = String(Math.round(alpha*1000));
    }
    render();
  });
}
render();
</script>
</body>
</html>

---
id: '6923dc0a-af9d-4ccb-80aa-98253fbd9811'
title: Safety over a deployment
summary_for_tutor: "The deployment race from Greenblatt et al.'s AI control paper, run on the paper's own contingency table for trusted monitoring: of 71 backdoor attempts, 24 were audited (caught, c = 0.338) and 13 were working backdoors that were not audited (successfully deployed, s = 0.183); the other 34 failed harmlessly. The learner drags k, the number of attack attempts, and watches P(red wins) = [s/(s+c)] * [1 - (1-s-c)^k] split into Term A, the chance a decisive attempt is a deployed backdoor, and Term B, the chance any attempt is decisive at all. Term B saturates fast, so by the twenty or so attempts the paper's red team actually makes, the red team's win probability sits near its ceiling of s/(s+c) = 35%, i.e. safety near 65%, close to the paper's measured 62%. The point the learner should reach: with per-attempt odds held fixed, attacking more is always weakly better, which is not what the paper's red team does."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from the "Safety over a deployment" demo on XLab's AI Control track
     (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look. -->
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
.ctl label{display:flex;justify-content:space-between;gap:12px;font-size:13px}
.ctl label .name{color:var(--muted)}
.ctl label .val{font-weight:600;font-variant-numeric:tabular-nums}
input[type=range]{width:100%;accent-color:var(--accent)}
svg{width:100%;height:auto;display:block;margin-top:10px}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;border:1px solid var(--border);border-radius:8px;background:var(--page);padding:12px;text-align:center;margin-top:12px}
.stats .k{font-size:11px;color:var(--muted);margin:0}
.stats .v{font-weight:600;font-variant-numeric:tabular-nums;margin:2px 0 0}
.odds{font-size:13px;color:var(--muted);margin:12px 0 0}
.legend{display:flex;flex-wrap:wrap;gap:14px;font-size:12px;color:var(--muted);margin-top:6px}
.legend span i{display:inline-block;width:14px;height:2px;vertical-align:middle;margin-right:5px}
@media (max-width:420px){ .stats{grid-template-columns:1fr} }
</style>
</head>
<body>
<p class="eyebrow">Trusted monitoring, per attempt</p>
<h2>Safety over a deployment</h2>
<p class="desc">Each attack attempt ends one of three ways. It is audited and the protocol shuts down (blue wins), it slips through as a working backdoor (red wins), or it is a broken backdoor nobody audits and the game continues. Only the first two are decisive, so a whole deployment is settled by the first decisive attempt. Drag the number of attempts.</p>

<div class="ctl">
  <label for="k"><span class="name">Attack attempts (k)</span><span class="val" id="kV">2</span></label>
  <input type="range" id="k" min="1" max="20" step="1" value="2" aria-label="Number of attack attempts">
</div>

<svg id="plot" viewBox="0 0 320 180" role="img" aria-label="Red team win probability and its two terms against the number of attack attempts"></svg>
<div class="legend">
  <span><i style="background:var(--accent)"></i>P(red wins)</span>
  <span><i style="background:var(--muted)"></i>Term B: some attempt is decisive</span>
  <span><i style="background:var(--text)"></i>Term A: the ceiling, s/(s+c)</span>
</div>

<div class="stats">
  <div><p class="k">Term A = s/(s+c)</p><p class="v" id="sA">-</p></div>
  <div><p class="k">Term B = 1-(1-s-c)^k</p><p class="v" id="sB">-</p></div>
  <div><p class="k">P(red wins)</p><p class="v" id="sP">-</p></div>
</div>

<p class="odds">Odds are the paper's own, read off its contingency table for trusted monitoring: of 71 backdoor attempts, 24 were audited, so c = 24/71 = 0.338; 13 were working backdoors that were not audited, so s = 13/71 = 0.183; the remaining 34 failed harmlessly. The paper's red team backdoors about twenty of the 5,000 problems.</p>

<script>
"use strict";
var c = 24/71, s = 13/71;
var termA = s/(s+c);
var k = 2;

function termB(kk){ return 1 - Math.pow(1 - s - c, kk); }
function pRed(kk){ return termA * termB(kk); }

function svgEl(name, attrs){
  var n = document.createElementNS("http://www.w3.org/2000/svg", name);
  for(var key in attrs){ n.setAttribute(key, attrs[key]); }
  return n;
}
function label(x,y,str,anchor){
  var t = svgEl("text",{x:x,y:y,"font-size":9,fill:"var(--muted)","text-anchor":anchor||"start"});
  t.textContent = str; return t;
}

// KMAX = 20 is the paper's own regime: a backdoor on about twenty of the 5,000
// problems is already deep in the plateau, and a wider axis renders the whole
// rise as a step against the left wall.
var X0=34, W=272, Y0=10, H=140, KMAX=20, CURVE_PTS=120;
function xOf(kk){ return X0 + (kk-1)/(KMAX-1)*W; }
function yOf(v){ return Y0 + H - v*H; }

function render(){
  document.getElementById("kV").textContent = String(k);
  var svg = document.getElementById("plot");
  svg.textContent = "";
  [0,0.25,0.5,0.75,1].forEach(function(f){
    svg.appendChild(svgEl("line",{x1:X0,x2:X0+W,y1:Y0+H*(1-f),y2:Y0+H*(1-f),stroke:"var(--border)","stroke-width":1}));
  });
  svg.appendChild(svgEl("line",{x1:X0,x2:X0+W,y1:yOf(termA),y2:yOf(termA),
    stroke:"var(--text)","stroke-width":1,"stroke-dasharray":"4 3","stroke-opacity":0.6}));
  var db=[], dp=[], i;
  for(i=1;i<=KMAX;i++){
    db.push((i===1?"M ":"L ") + xOf(i).toFixed(2) + " " + yOf(termB(i)).toFixed(2));
    dp.push((i===1?"M ":"L ") + xOf(i).toFixed(2) + " " + yOf(pRed(i)).toFixed(2));
  }
  svg.appendChild(svgEl("path",{d:db.join(" "),fill:"none",stroke:"var(--muted)","stroke-width":1.5,"stroke-opacity":0.7}));
  svg.appendChild(svgEl("path",{d:dp.join(" "),fill:"none",stroke:"var(--accent)","stroke-width":2}));
  svg.appendChild(svgEl("line",{x1:xOf(k),x2:xOf(k),y1:Y0,y2:Y0+H,stroke:"var(--muted)","stroke-width":1,"stroke-opacity":0.4}));
  svg.appendChild(svgEl("circle",{cx:xOf(k),cy:yOf(pRed(k)),r:5,fill:"var(--accent)",stroke:"#fff","stroke-width":2}));
  svg.appendChild(label(30, Y0+8, "100%", "end"));
  svg.appendChild(label(30, Y0+H, "0%", "end"));
  svg.appendChild(label(X0, 168, "k = 1"));
  svg.appendChild(label(X0+W, 168, "k = 120", "end"));
  svg.appendChild(label(X0+W/2, 168, "attack attempts", "middle"));
  document.getElementById("sA").textContent = (termA*100).toFixed(1) + "%";
  document.getElementById("sB").textContent = (termB(k)*100).toFixed(1) + "%";
  document.getElementById("sP").textContent = (pRed(k)*100).toFixed(1) + "%";
  save();
}

var saveTimer = null;
function save(){
  if(!window.Lens) return;
  if(saveTimer) clearTimeout(saveTimer);
  saveTimer = setTimeout(function(){
    Lens.saveState({k:k},
      "Deployment race widget, on the paper's trusted-monitoring odds (c = 0.338 caught, s = 0.183 deployed). " +
      "The learner has set k = " + k + " attack attempts. Term A (the ceiling) = " + (termA*100).toFixed(1) +
      "%, Term B (some attempt is decisive) = " + (termB(k)*100).toFixed(1) + "%, so P(red wins) = " +
      (pRed(k)*100).toFixed(1) + "% and safety = " + ((1-pRed(k))*100).toFixed(1) + "%.");
  }, 400);
}

document.getElementById("k").addEventListener("input", function(e){ k = Number(e.target.value); render(); });

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(state && typeof state.k === "number"){ k = state.k; document.getElementById("k").value = String(k); }
    render();
  });
}
render();
</script>
</body>
</html>

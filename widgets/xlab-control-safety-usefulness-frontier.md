---
id: '360b5066-9ceb-45cb-a69e-74f1172efe7f'
title: The safety/usefulness frontier
summary_for_tutor: "A scatter plot of every protocol in Table 7 of Greenblatt et al.'s AI control paper: scaled usefulness on the x axis, safety on the y axis, both in per cent. Fifteen points in four families, each family drawn with its own marker shape and joined by its within-family tradeoff curve: trusted monitoring (defer to trusted 0/5/10/20/50%), untrusted monitoring (defer to trusted 0/5/10/20%), trusted editing (threshold 5/10/20/50%) and two isolated baselines (the trusted model alone, and upfront auditing). The learner clicks legend entries to hide or show whole families, hovers or tabs to a point to read its label and its two numbers, and ticks 'Highlight Pareto frontier' to draw a dashed line through the protocols that are not beaten on both axes at once, dimming every dominated point. The frontier is recomputed over whichever families are currently visible, so hiding trusted editing changes which points survive. With all four families shown the frontier is trusted monitoring defer 50%, untrusted monitoring defer 20%, then trusted editing at 50%, 20%, 10% and 5%, then upfront auditing: trusted editing owns the whole middle of the curve and pushes three of the four untrusted monitoring points off it. The point of the widget is the difference between sliding along one family's curve (turning the defer knob trades usefulness for safety) and a better method pushing the frontier out (trusted editing reaching points up and to the right of untrusted monitoring). The widget counts as done once the learner has viewed the frontier with trusted editing and untrusted monitoring both visible."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from the "safety-usefulness-frontier" demo (components/demos/frontier-demo.tsx)
     on XLab's AI Control track (aisafetytracks.com), rebuilt as vanilla HTML/JS in the
     Lens look. Data is Table 7 of Greenblatt et al., "AI Control: Improving Safety
     Despite Intentional Subversion"; XLab's source calls the same table Table 8. -->
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
.plotwrap{position:relative;width:100%;max-width:460px;margin:0 auto}
svg.plot{width:100%;height:auto;display:block}
.tip{position:absolute;z-index:10;pointer-events:none;border:1px solid var(--border);border-radius:6px;
     background:#fff;padding:6px 9px;font-size:12px;line-height:1.4;box-shadow:0 1px 2px rgba(0,0,0,.06);white-space:nowrap}
.tip .lab{font-weight:600}
.tip .num{color:var(--muted);font-variant-numeric:tabular-nums}
.controls{display:flex;flex-wrap:wrap;align-items:center;justify-content:space-between;gap:10px;margin-top:14px}
.legend{display:flex;flex-wrap:wrap;gap:6px}
button.fam{display:inline-flex;align-items:center;gap:6px;font:inherit;font-size:12px;color:inherit;
  border:1px solid var(--border);border-radius:8px;background:#fff;padding:5px 9px;cursor:pointer}
button.fam:hover{background:var(--page)}
button.fam[aria-pressed="false"]{opacity:.45;text-decoration:line-through}
button.fam:focus-visible{outline:2px solid var(--accent);outline-offset:2px}
.front{display:inline-flex;align-items:center;gap:7px;font-size:12px;color:var(--muted);cursor:pointer}
.front input{accent-color:var(--accent);width:15px;height:15px}
.note{font-size:13px;color:var(--muted);margin:12px 0 0}
.sr{position:absolute;width:1px;height:1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap}
@media (max-width:420px){ .controls{flex-direction:column;align-items:flex-start} }
</style>
</head>
<body>
<p class="eyebrow">Table 7, every protocol at once</p>
<h2>The safety/usefulness frontier</h2>
<p class="desc">Every protocol from Table 7 plotted as safety against usefulness. Hover a point, click a legend entry to isolate a method family, and highlight the Pareto frontier of protocols not beaten on both axes at once.</p>

<div class="plotwrap" id="wrap"></div>

<div class="controls">
  <div class="legend" id="legend"></div>
  <label class="front" for="frontcb"><input type="checkbox" id="frontcb"> Highlight Pareto frontier</label>
</div>

<p class="note" id="note" hidden></p>
<p class="sr" id="live" role="status" aria-live="polite"></p>

<script>
(function(){
  "use strict";

  // Table 7 of Greenblatt et al. (2023), "AI Control: Improving Safety Despite
  // Intentional Subversion". Safety and scaled usefulness, both per cent.
  var DATA = [
    { family:"Baselines",            label:"Trusted model",                     usefulness:2,   safety:100 },
    { family:"Baselines",            label:"Upfront auditing",                  usefulness:100, safety:15  },
    { family:"Trusted monitoring",   label:"Trusted monitoring · defer 0%",  usefulness:97,  safety:62  },
    { family:"Trusted monitoring",   label:"Trusted monitoring · defer 5%",  usefulness:95,  safety:74  },
    { family:"Trusted monitoring",   label:"Trusted monitoring · defer 10%", usefulness:93,  safety:83  },
    { family:"Trusted monitoring",   label:"Trusted monitoring · defer 20%", usefulness:83,  safety:92  },
    { family:"Trusted monitoring",   label:"Trusted monitoring · defer 50%", usefulness:51,  safety:100 },
    { family:"Untrusted monitoring", label:"Untrusted monitoring · defer 0%",  usefulness:96, safety:79 },
    { family:"Untrusted monitoring", label:"Untrusted monitoring · defer 5%",  usefulness:95, safety:82 },
    { family:"Untrusted monitoring", label:"Untrusted monitoring · defer 10%", usefulness:92, safety:92 },
    { family:"Untrusted monitoring", label:"Untrusted monitoring · defer 20%", usefulness:85, safety:98 },
    { family:"Trusted editing",      label:"Trusted editing · 5%",          usefulness:97,  safety:73  },
    { family:"Trusted editing",      label:"Trusted editing · 10%",         usefulness:96,  safety:85  },
    { family:"Trusted editing",      label:"Trusted editing · 20%",         usefulness:94,  safety:92  },
    { family:"Trusted editing",      label:"Trusted editing · 50%",         usefulness:89,  safety:96  }
  ];

  var FAMILY_ORDER = ["Trusted monitoring","Untrusted monitoring","Trusted editing","Baselines"];

  // Shape is the primary channel (colour-vision-safe); the Lens accent marks
  // trusted editing, the family the lesson's question turns on.
  var STYLE = {
    "Trusted monitoring":   { color:"#5a5a5a", shape:"circle",   curve:true  },
    "Untrusted monitoring": { color:"#1a1a1a", shape:"square",   curve:true  },
    "Trusted editing":      { color:"#b87018", shape:"triangle", curve:true  },
    "Baselines":            { color:"#a8a29a", shape:"diamond",  curve:false }
  };

  var NS = "http://www.w3.org/2000/svg";
  var W = 420, H = 320;
  var M = { top:14, right:16, bottom:42, left:46 };
  var PW = W - M.left - M.right;
  var PH = H - M.top - M.bottom;
  function xPx(u){ return M.left + (u/100)*PW; }
  function yPx(s){ return M.top + PH - (s/100)*PH; }

  /** Points not dominated on both axes at once (higher safety AND higher usefulness). */
  function paretoFront(pts){
    return pts.filter(function(p){
      return !pts.some(function(q){
        return q !== p && q.usefulness >= p.usefulness && q.safety >= p.safety &&
               (q.usefulness > p.usefulness || q.safety > p.safety);
      });
    });
  }

  var hidden = {};                 // family name -> true when hidden
  var showFrontier = false;
  var hover = null;                // index into DATA
  var completed = false;
  var wrap = document.getElementById("wrap");
  var legendEl = document.getElementById("legend");
  var cb = document.getElementById("frontcb");
  var noteEl = document.getElementById("note");
  var liveEl = document.getElementById("live");
  var tip = null;
  var saveTimer = null;

  function el(name, attrs){
    var n = document.createElementNS(NS, name);
    for (var k in attrs) if (Object.prototype.hasOwnProperty.call(attrs, k)) n.setAttribute(k, attrs[k]);
    return n;
  }

  function marker(shape, cx, cy, r, color, filled){
    var fill = filled ? color : "#ffffff";
    if (shape === "square") return el("rect", { x:cx-r, y:cy-r, width:2*r, height:2*r, rx:1, fill:fill, stroke:color, "stroke-width":1.5 });
    if (shape === "triangle") return el("polygon", { points:cx+","+(cy-r)+" "+(cx-r)+","+(cy+r)+" "+(cx+r)+","+(cy+r), fill:fill, stroke:color, "stroke-width":1.5 });
    if (shape === "diamond") return el("polygon", { points:cx+","+(cy-r)+" "+(cx+r)+","+cy+" "+cx+","+(cy+r)+" "+(cx-r)+","+cy, fill:fill, stroke:color, "stroke-width":1.5 });
    return el("circle", { cx:cx, cy:cy, r:r, fill:fill, stroke:color, "stroke-width":1.5 });
  }

  function visiblePoints(){
    return DATA.filter(function(p){ return !hidden[p.family]; });
  }

  function frontierPoints(){
    return paretoFront(visiblePoints()).sort(function(a,b){ return a.usefulness - b.usefulness; });
  }

  function pathFor(pts){
    return pts.map(function(p,i){
      return (i === 0 ? "M " : "L ") + xPx(p.usefulness).toFixed(1) + " " + yPx(p.safety).toFixed(1);
    }).join(" ");
  }

  function draw(){
    var front = frontierPoints();
    var onFront = new Set(front);

    var svg = el("svg", {
      viewBox: "0 0 " + W + " " + H,
      "class": "plot",
      role: "img",
      "aria-label": "Safety against scaled usefulness for each protocol in Table 7"
    });

    [0,25,50,75,100].forEach(function(t){
      svg.appendChild(el("line", { x1:xPx(t), x2:xPx(t), y1:M.top, y2:M.top+PH, stroke:"#e8e5df", "stroke-width":1 }));
      var tx = el("text", { x:xPx(t), y:H-28, "font-size":11, fill:"#5a5a5a", "text-anchor":"middle" });
      tx.textContent = String(t);
      svg.appendChild(tx);
      svg.appendChild(el("line", { x1:M.left, x2:M.left+PW, y1:yPx(t), y2:yPx(t), stroke:"#e8e5df", "stroke-width":1 }));
      var ty = el("text", { x:M.left-7, y:yPx(t)+4, "font-size":11, fill:"#5a5a5a", "text-anchor":"end" });
      ty.textContent = String(t);
      svg.appendChild(ty);
    });

    var xt = el("text", { x:M.left+PW/2, y:H-8, "font-size":12, fill:"#5a5a5a", "text-anchor":"middle" });
    xt.textContent = "Scaled usefulness (%)";
    svg.appendChild(xt);
    var yt = el("text", { x:14, y:M.top+PH/2, "font-size":12, fill:"#5a5a5a", "text-anchor":"middle",
                          transform:"rotate(-90 14 " + (M.top+PH/2) + ")" });
    yt.textContent = "Safety (%)";
    svg.appendChild(yt);

    // within-family tradeoff curves
    FAMILY_ORDER.forEach(function(f){
      if (!STYLE[f].curve || hidden[f]) return;
      var pts = DATA.filter(function(p){ return p.family === f; })
                    .slice().sort(function(a,b){ return b.usefulness - a.usefulness; });
      svg.appendChild(el("path", { d:pathFor(pts), fill:"none", stroke:STYLE[f].color, "stroke-width":1.5, "stroke-opacity":0.85 }));
    });

    // Pareto frontier line
    if (showFrontier && front.length > 1) {
      svg.appendChild(el("path", { d:pathFor(front), fill:"none", stroke:"#1a1a1a", "stroke-width":1.5,
                                   "stroke-dasharray":"4 3", "stroke-opacity":0.7 }));
    }

    DATA.forEach(function(p, i){
      if (hidden[p.family]) return;
      var isFront = onFront.has(p);
      var dim = showFrontier && !isFront;
      var cx = xPx(p.usefulness), cy = yPx(p.safety);
      var g = el("g", { opacity: dim ? 0.3 : 1 });
      if (showFrontier && isFront) {
        g.appendChild(el("circle", { cx:cx, cy:cy, r:6.5, fill:"none", stroke:"#1a1a1a", "stroke-width":1, "stroke-opacity":0.6 }));
      }
      g.appendChild(marker(STYLE[p.family].shape, cx, cy, 3.8, STYLE[p.family].color, hover === i));
      var hit = el("circle", {
        cx:cx, cy:cy, r:11, fill:"transparent", tabindex:"0", role:"button", style:"cursor:pointer",
        "aria-label": p.label + ", safety " + p.safety + " per cent, usefulness " + p.usefulness + " per cent" +
                      (showFrontier ? (isFront ? ", on the Pareto frontier" : ", dominated") : "")
      });
      function on(){ hover = i; render(); }
      function off(){ if (hover === i) { hover = null; render(); } }
      hit.addEventListener("pointerenter", on);
      hit.addEventListener("pointerdown", on);
      hit.addEventListener("pointerleave", off);
      hit.addEventListener("focus", on);
      hit.addEventListener("blur", off);
      g.appendChild(hit);
      svg.appendChild(g);
    });

    wrap.textContent = "";
    wrap.appendChild(svg);

    if (hover !== null && !hidden[DATA[hover].family]) {
      var p = DATA[hover];
      tip = document.createElement("div");
      tip.className = "tip";
      var dx = p.usefulness >= 75 ? "calc(-100% + 10px)" : (p.usefulness <= 25 ? "-10px" : "-50%");
      var dy = yPx(p.safety) < H*0.28 ? "14px" : "calc(-100% - 14px)";
      tip.style.left = ((xPx(p.usefulness)/W)*100) + "%";
      tip.style.top = ((yPx(p.safety)/H)*100) + "%";
      tip.style.transform = "translate(" + dx + ", " + dy + ")";
      var l1 = document.createElement("div"); l1.className = "lab"; l1.textContent = p.label;
      var l2 = document.createElement("div"); l2.className = "num";
      l2.textContent = "Safety " + p.safety + "% · Usefulness " + p.usefulness + "%";
      tip.appendChild(l1); tip.appendChild(l2);
      wrap.appendChild(tip);
    }

    noteEl.hidden = !showFrontier;
    if (showFrontier) {
      noteEl.textContent = "The dashed line links the protocols that are not beaten on both axes at once. " +
        "Points below it are dominated: some other protocol is at least as safe and at least as useful.";
    }
  }

  function drawLegend(){
    legendEl.textContent = "";
    FAMILY_ORDER.forEach(function(f){
      var b = document.createElement("button");
      b.type = "button";
      b.className = "fam";
      b.setAttribute("aria-pressed", hidden[f] ? "false" : "true");
      var s = el("svg", { width:14, height:14, viewBox:"0 0 14 14", "aria-hidden":"true" });
      s.appendChild(marker(STYLE[f].shape, 7, 7, 5, STYLE[f].color, true));
      b.appendChild(s);
      b.appendChild(document.createTextNode(f));
      b.addEventListener("click", function(){
        if (hidden[f]) delete hidden[f]; else hidden[f] = true;
        hover = null;
        render();
        save();
      });
      legendEl.appendChild(b);
    });
  }

  function render(){
    draw();
    FAMILY_ORDER.forEach(function(f, i){
      var b = legendEl.children[i];
      if (b) b.setAttribute("aria-pressed", hidden[f] ? "false" : "true");
    });
    cb.checked = showFrontier;
  }

  function visibleNames(){
    return FAMILY_ORDER.filter(function(f){ return !hidden[f]; });
  }

  function summary(){
    var vis = visibleNames();
    var front = frontierPoints();
    var parts = [];
    parts.push("Safety/usefulness frontier (Table 7 of the AI control paper).");
    parts.push("Families visible: " + (vis.length ? vis.join(", ") : "none") + ".");
    parts.push("Families hidden: " + (vis.length === FAMILY_ORDER.length ? "none" :
      FAMILY_ORDER.filter(function(f){ return hidden[f]; }).join(", ")) + ".");
    parts.push("Pareto frontier highlight: " + (showFrontier ? "on" : "off") + ".");
    if (showFrontier && front.length) {
      parts.push("Over the visible families the frontier runs " + front.map(function(p){
        return p.label + " (usefulness " + p.usefulness + "%, safety " + p.safety + "%)";
      }).join(", then ") + ".");
    }
    var compared = showFrontier && !hidden["Trusted editing"] && !hidden["Untrusted monitoring"];
    parts.push(compared
      ? "The learner has seen the frontier with trusted editing and untrusted monitoring side by side, which is the comparison that shows trusted editing pushing the frontier out rather than sliding along it."
      : "The learner has not yet viewed the frontier with both trusted editing and untrusted monitoring visible.");
    return parts.join(" ");
  }

  function save(){
    if (!window.Lens) return;
    if (showFrontier && !hidden["Trusted editing"] && !hidden["Untrusted monitoring"] && !completed) {
      completed = true;
      if (Lens.complete) Lens.complete();
    }
    liveEl.textContent = showFrontier
      ? ("Pareto frontier shown, " + frontierPoints().length + " protocols on it.")
      : "Pareto frontier hidden.";
    if (saveTimer) clearTimeout(saveTimer);
    saveTimer = setTimeout(function(){
      if (Lens.saveState) Lens.saveState({ hidden: Object.keys(hidden), frontier: showFrontier }, summary());
    }, 250);
  }

  cb.addEventListener("change", function(){
    showFrontier = cb.checked;
    render();
    save();
  });

  drawLegend();
  render();

  if (window.Lens && Lens.onState) {
    Lens.onState(function(state, meta){
      if (state) {
        hidden = {};
        if (Array.isArray(state.hidden)) state.hidden.forEach(function(f){ if (STYLE[f]) hidden[f] = true; });
        showFrontier = !!state.frontier;
      }
      if (meta && meta.completed) completed = true;
      render();
    });
  }
})();
</script>
</body>
</html>

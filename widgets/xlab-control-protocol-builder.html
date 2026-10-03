---
id: 'ebb967f7-2730-4e67-bde5-34fc018d17d3'
title: Build the blue-team protocols
summary_for_tutor: "A construction exercise for Table 2 of Greenblatt et al.'s AI control paper, ported from XLab's drag-and-drop flow-chart builder. Six tabs, one per blue-team protocol (don't use untrusted models, upfront auditing, trusted monitoring, defer to trusted 10%, untrusted monitoring, trusted editing 20%); a toggle shows that protocol's Table 2 description. For each, the learner builds a flow chart down from 'Problem arrives' by dragging blocks (or tapping a block, then a dashed slot) from a palette: steps (U writes a solution, T rates suspicion, a separate copy of U rates suspicion), decisions that split into labelled arms (first 2% of problems yes/no; suspicion rank top 2% / bottom 98%, top 2% / 2-10% / bottom 90%, top 2% / 2-20% / bottom 80%) and endings (submit U's code, have T write and submit its own, have T edit U's code and submit the edit, audit with H). Check is enabled once every path ends in an ending; it marks each block as matching Table 2 or not, and a correct chart reveals a one-sentence explanation of what that row buys. The point is that every protocol in the paper is the same shape and only the routing rule and the fallback differ."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<!-- Ported from the "Reconstruct each blue-team protocol from Table 2 as a flow chart" exercise
     on XLab's AI Control track (aisafetytracks.com): same drag-into-a-tree interaction and palette,
     rebuilt as vanilla HTML/JS in the Lens look. -->
<style>
:root{
  --bg:#ffffff; --page:#faf8f3; --text:#1a1a1a; --muted:#5a5a5a; --border:#e8e5df; --line:#cfc9bd;
  --accent:#b87018; --accent-hover:#9a5c10; --accent-soft:#f6ecdd;
  --font-ui:"DM Sans",Arial,sans-serif; --font-heading:"Newsreader",Georgia,serif;
}
*{box-sizing:border-box}
body{margin:0;padding:16px;font:14px/1.5 var(--font-ui);color:var(--text);background:var(--bg)}
p{margin:0}
button{font:inherit;color:inherit;border:1px solid var(--border);border-radius:8px;background:#fff;padding:7px 10px;cursor:pointer;text-align:left}
button:hover{background:var(--page)}
button:disabled{cursor:default;opacity:.5}
button:disabled:hover{background:#fff}
button:focus-visible{outline:2px solid var(--accent);outline-offset:2px}
.eyebrow{font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--muted);margin:0 0 4px}
.lead{margin:0 0 12px}
.tabs{display:flex;flex-wrap:wrap;gap:6px;margin:0 0 12px}
.tab{font-size:13px;border-radius:999px;padding:5px 12px}
.tab.is-active{border-color:var(--accent);background:var(--accent);color:#fff}
.tab .tick{margin-left:6px;font-weight:600}
.tab:not(.is-active) .tick{color:var(--accent)}
.desc{border:1px dashed var(--border);border-radius:8px;margin:0 0 14px}
.desc>button{border:0;width:100%;color:var(--muted);font-size:13px;padding:10px 12px;background:transparent}
.desc>button:hover{color:var(--text)}
.desc p{padding:0 12px 12px;font-size:13px}
.chart{overflow-x:auto;padding:4px 2px 8px}
.tree{display:flex;flex-direction:column;align-items:center}
.chart>.tree{width:max-content;min-width:100%}
.start{font-size:13px;color:var(--muted);background:var(--page);border:1px solid var(--border);border-radius:999px;padding:3px 12px}
.vline{width:1px;height:14px;background:var(--line);flex:none}
.node{position:relative;max-width:220px;min-width:120px;text-align:center;font-size:13px;line-height:1.35;border:1px solid var(--border);border-radius:8px;background:#fff;padding:8px 22px}
.node.branch{background:var(--page);border-radius:14px}
.node.terminal{border-color:var(--line);font-weight:500}
.node .rm{position:absolute;top:2px;right:2px;border:0;background:transparent;padding:0 5px;line-height:18px;font-size:13px;color:var(--muted);border-radius:6px}
.node .rm:hover{background:var(--border);color:var(--text)}
.node .mark{position:absolute;top:3px;left:6px;font-size:12px;font-weight:600}
.node.good{border-color:var(--accent);box-shadow:0 0 0 1px var(--accent)}
.node.good .mark{color:var(--accent)}
.node.bad{border:1px dashed var(--text);box-shadow:0 0 0 1px var(--text)}
.node.bad .mark{color:var(--text)}
.slot{min-width:120px;max-width:180px;font-size:13px;color:var(--muted);text-align:center;border:1px dashed var(--line);border-radius:8px;background:#fff;padding:8px 12px}
.slot.armed{border-color:var(--accent);color:var(--accent-hover);background:var(--accent-soft)}
.slot.over{border-style:solid;border-color:var(--accent);background:var(--accent-soft);color:var(--accent-hover)}
.arms{display:flex;align-items:flex-start}
.arm{position:relative;display:flex;flex-direction:column;align-items:center;padding:14px 6px 0}
.arm::before{content:"";position:absolute;top:0;left:0;right:0;border-top:1px solid var(--line)}
.arm:first-child::before{left:50%}
.arm:last-child::before{right:50%}
.arm::after{content:"";position:absolute;top:0;left:50%;height:14px;border-left:1px solid var(--line)}
.arm-label{position:relative;z-index:1;font-size:11px;letter-spacing:.08em;text-transform:uppercase;color:var(--muted);background:var(--page);border:1px solid var(--border);border-radius:999px;padding:1px 8px;white-space:nowrap}
.palette{border:1px solid var(--border);border-radius:8px;padding:8px 10px 10px;margin:0 0 12px}
.ptop{display:flex;flex-wrap:wrap;align-items:center;gap:6px;margin:0 0 8px}
.ptop .eyebrow{margin:0 4px 0 0}
.gtab{font-size:12px;padding:3px 10px;border-radius:999px}
.gtab.is-active{border-color:var(--text);box-shadow:0 0 0 1px var(--text)}
.pbs{display:flex;flex-wrap:wrap;gap:6px}
.pb{font-size:13px;line-height:1.35;max-width:250px;padding:6px 10px}
.pb.branch{background:var(--page);border-radius:14px}
.pb.branch:hover{background:#f1ede4}
.pb.terminal{border-color:var(--line);font-weight:500}
.pb .sub{display:block;font-weight:400;color:var(--muted);font-size:12px}
.pb[aria-pressed="true"]{border-color:var(--accent);box-shadow:0 0 0 1px var(--accent);background:var(--accent-soft)}
.pb{cursor:grab;user-select:none}
.ghost{position:fixed;z-index:10;pointer-events:none;max-width:200px;font-size:13px;line-height:1.35;border:1px solid var(--accent);border-radius:8px;background:#fff;padding:6px 10px;box-shadow:0 1px 2px rgba(0,0,0,.08)}
body.dragging{cursor:grabbing;user-select:none}
.hint{font-size:12px;color:var(--muted);margin-top:6px}
.actions{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-top:14px}
.primary{border-color:var(--accent);color:#fff;background:var(--accent);font-weight:500}
.primary:hover{background:var(--accent-hover)}
.primary:disabled:hover{background:var(--accent)}
.status{font-size:13px;color:var(--muted)}
.verdict{margin-top:12px;border-radius:8px;padding:10px 12px;background:var(--page);font-size:13px}
.verdict.ok{border-left:3px solid var(--accent)}
.verdict strong{font-weight:600}
.verdict .explain{margin-top:6px}
.arm .node,.arm .slot{max-width:170px}
@media (max-width:560px){
  .node{min-width:0;font-size:12px;padding:8px 18px}
  .arm{padding:14px 2px 0}
  .arm .node,.arm .slot{min-width:0;max-width:108px;font-size:12px}
  .arm-label{font-size:10px;padding:1px 6px}
}
@media (max-width:420px){
  body{padding:12px 6px}
  .arm{padding:14px 1px 0}
  .arm .node,.arm .slot{max-width:98px;padding:8px 14px}
}
</style>
</head>
<body>
<p class="eyebrow" id="progress">Build the flow chart</p>
<p class="lead">Drag blocks from the palette into the chart; every path must end in a submit or audit block.</p>
<div class="tabs" id="tabs"></div>
<div id="panel"></div>
<script>
"use strict";
var BLOCKS = [
  {id:"u-writes",       kind:"step",     label:"U writes a solution"},
  {id:"t-rates",        kind:"step",     label:"T rates how suspicious U's code looks"},
  {id:"u-rates",        kind:"step",     label:"A separate copy of U rates how suspicious the code looks"},
  {id:"branch-first-2", kind:"branch",   label:"Among the first 2% of problems?", arms:["Yes","No"]},
  {id:"branch-top-2",   kind:"branch",   label:"Suspicion rank?", arms:["Top 2%","Bottom 98%"]},
  {id:"branch-2-10",    kind:"branch",   label:"Suspicion rank?", arms:["Top 2%","Top 2–10%","Bottom 90%"]},
  {id:"branch-2-20",    kind:"branch",   label:"Suspicion rank?", arms:["Top 2%","Top 2–20%","Bottom 80%"]},
  {id:"submit-u",       kind:"terminal", label:"Submit U's solution"},
  {id:"submit-t",       kind:"terminal", label:"Have T write its own solution and submit that"},
  {id:"submit-edit",    kind:"terminal", label:"Have T edit U's code to remove any backdoor; submit the edit"},
  {id:"audit",          kind:"terminal", label:"Audit with H: shut down if backdoored, otherwise submit"}
];
var GROUPS = [["step","Steps"],["branch","Decisions"],["terminal","Endings"]];
// Answer key: steps in order, then either one branch with one ending per arm, or (branch "none") a single ending.
var STAGES = [
  {id:"dont-use-untrusted", title:"Don't use untrusted models",
   description:"Produce code using only H and T.",
   steps:[], branch:"none", terminals:["submit-t"],
   explanation:"With U out of the picture entirely there is nothing to monitor or audit: T just writes and submits every solution. Safety is 100% and usefulness is 2%: this is the floor the other protocols are trying to beat."},
  {id:"upfront-auditing", title:"Upfront auditing",
   description:"Produce code using U. Audit the produced code on the first 2% of problems.",
   steps:["u-writes"], branch:"branch-first-2", terminals:["audit","submit-u"],
   explanation:"The decision here is positional, not suspicion-based: no one ever rates the code. That is exactly why the red team's “backdoor rarely, at random” attack works: most backdoors land in the unaudited 98%."},
  {id:"trusted-monitoring", title:"Trusted monitoring",
   description:"Produce code using U, and ask T to review how suspicious it looks. Audit the top 2% most suspicious code.",
   steps:["u-writes","t-rates"], branch:"branch-top-2", terminals:["audit","submit-u"],
   explanation:"Compared with upfront auditing, the only change is that the 2% audit budget is now spent on the most suspicious code rather than the first code to arrive: T's ratings decide where H looks."},
  {id:"defer-to-trusted", title:"Defer to trusted (10%)",
   description:"Apply the same approach as trusted monitoring, but submit a solution written by T when U's code is between top 2% and top 10% suspicion.",
   steps:["u-writes","t-rates"], branch:"branch-2-10", terminals:["audit","submit-t","submit-u"],
   explanation:"The new middle band (top 2–10%) is code too suspicious to trust but not suspicious enough to spend an H point on, so the protocol throws U's version away and submits T's instead, trading a little usefulness for safety."},
  {id:"untrusted-monitoring", title:"Untrusted monitoring",
   description:"Produce code using U, and ask a separate copy of U (the untrusted monitor) to monitor how suspicious it looks. Audit the top 2% most suspicious code. Evaluate this untrusted monitor on synthetic examples of backdoors (produced by H) to ensure it is doing its best, and use the untrusted monitor on redacted problem statements and code to make collusion harder.",
   steps:["u-writes","u-rates"], branch:"branch-top-2", terminals:["audit","submit-u"],
   explanation:"Structurally identical to trusted monitoring: the only change is who rates the code. Because the monitor is itself untrusted, it has to be kept honest: validated against synthetic backdoors from H, and shown redacted inputs so colluding with the policy is harder."},
  {id:"trusted-editing", title:"Trusted editing (20%)",
   description:"Ask U to produce code, and ask T to edit it to remove backdoors. Use trusted monitoring to determine suspicion. Audit the top 2% most suspicious U code, use an edited solution for suspicion between the top 2% and top 20%, and use U's solution for suspicion in the bottom 80%.",
   steps:["u-writes","t-rates"], branch:"branch-2-20", terminals:["audit","submit-edit","submit-u"],
   explanation:"Same skeleton as defer to trusted, with two changes: the middle band widens to top 2–20%, and instead of discarding U's work there, T edits it, keeping most of U's usefulness while stripping anything that looks like a backdoor."}
];

// A chart is a tree: null (an empty slot), {b:step, next:chart}, {b:branch, arms:[chart,...]} or {b:ending}.
var charts = {}, checked = {}, solved = {}, current = 0, armed = null, showDesc = false, note = "", group = "step";
STAGES.forEach(function(s){ charts[s.id] = null; checked[s.id] = false; solved[s.id] = false; });

function block(id){ for(var i=0;i<BLOCKS.length;i++){ if(BLOCKS[i].id===id) return BLOCKS[i]; } return null; }
function el(tag, cls, text){ var n=document.createElement(tag); if(cls) n.className=cls; if(text!=null) n.textContent=text; return n; }
function make(id){
  var b = block(id);
  if(b.kind==="step") return {b:id, next:null};
  if(b.kind==="branch") return {b:id, arms:b.arms.map(function(){ return null; })};
  return {b:id};
}
function key(stage){
  var tail = stage.branch==="none" ? {b:stage.terminals[0]} : {b:stage.branch, arms:stage.terminals.map(function(t){ return {b:t}; })};
  for(var i=stage.steps.length-1;i>=0;i--) tail = {b:stage.steps[i], next:tail};
  return tail;
}
function same(a, k){
  if(!a || !k || a.b!==k.b) return false;
  if(k.arms){ for(var i=0;i<k.arms.length;i++){ if(!same(a.arms[i], k.arms[i])) return false; } return true; }
  if("next" in k) return same(a.next, k.next);
  return true;
}
function complete(n){
  if(!n) return false;
  if(n.arms) return n.arms.every(complete);
  if("next" in n) return complete(n.next);
  return true;
}
function describe(n){
  if(!n) return "(empty slot)";
  var b = block(n.b);
  if(n.arms) return b.label + " [" + b.arms.map(function(a,i){ return a + ": " + describe(n.arms[i]); }).join("; ") + "]";
  if("next" in n) return b.label + " → " + describe(n.next);
  return b.label;
}

function place(id, set){
  set(make(id));
  armed = null; note = "";
  changed();
}

function slot(set){
  var s = el("button", "slot" + (armed ? " armed" : ""), armed ? "Place here" : "Drop a block here");
  s.onclick = function(){
    if(armed) place(armed, set);
    else { note = "Pick a block from the palette first, then tap the slot."; render(); }
  };
  s.setFn = set;
  return s;
}

// After "Check chart", marks each block against the answer key by role, not by depth: the steps in
// order, then the decision, then the ending on each arm. A missing step then only costs the steps,
// instead of pushing the decision and every ending out of line.
function flat(n){
  var steps = [];
  while(n && "next" in n){ steps.push(n); n = n.next; }
  return {steps:steps, tail:n};
}
function grade(chart, stage){
  var ok = new Map(), k = flat(key(stage)), u = flat(chart);
  function wrong(n){
    if(!n) return;
    ok.set(n, false);
    if(n.arms) n.arms.forEach(wrong); else if("next" in n) wrong(n.next);
  }
  u.steps.forEach(function(n, i){ ok.set(n, !!k.steps[i] && k.steps[i].b===n.b); });
  var t = u.tail, kt = k.tail;
  if(t){
    ok.set(t, !!kt && kt.b===t.b);
    if(t.arms) t.arms.forEach(function(a, i){
      var ka = kt && kt.arms ? kt.arms[i] : null;
      if(a && ka && a.b===ka.b && !a.arms && !("next" in a)) ok.set(a, true); else wrong(a);
    });
  }
  return {ok:ok, missing:k.steps.length - u.steps.length};
}

// g is the result of grade(), or null before "Check chart".
function draw(n, set, g){
  var col = el("div", "tree");
  if(!n){ col.appendChild(slot(set)); return col; }
  var b = block(n.b);
  var box = el("div", "node " + b.kind);
  if(g){
    var ok = !!g.ok.get(n);
    box.className += ok ? " good" : " bad";
    var m = el("span", "mark", ok ? "✓" : "✗");
    m.setAttribute("aria-label", ok ? "matches Table 2" : "does not match Table 2");
    box.appendChild(m);
  }
  box.appendChild(document.createTextNode(b.label));
  var rm = el("button", "rm", "×");
  rm.title = "Remove this block";
  rm.setAttribute("aria-label", "Remove " + b.label);
  rm.onclick = function(){ set(n.next !== undefined ? n.next : null); changed(); };
  box.appendChild(rm);
  col.appendChild(box);
  if(n.arms){
    col.appendChild(el("div", "vline"));
    var row = el("div", "arms");
    b.arms.forEach(function(label, i){
      var arm = el("div", "arm");
      arm.appendChild(el("span", "arm-label", label));
      arm.appendChild(el("div", "vline"));
      arm.appendChild(draw(n.arms[i], function(v){ n.arms[i] = v; }, g));
      row.appendChild(arm);
    });
    col.appendChild(row);
  } else if("next" in n){
    col.appendChild(el("div", "vline"));
    col.appendChild(draw(n.next, function(v){ n.next = v; }, g));
  }
  return col;
}

// Mouse and pen drag with pointer events (HTML5 drag and drop does not reach the sandboxed frame
// reliably). Touch keeps tap-then-tap, so a finger on the palette still scrolls the page.
var drag = null, dragged = false;
function slotAt(x, y){
  var t = document.elementFromPoint(x, y);
  return t && t.closest ? t.closest(".slot") : null;
}
function startDrag(e, b){
  if(e.pointerType==="touch" || e.button!==0) return;
  drag = {id:b.id, label:b.label, x:e.clientX, y:e.clientY, ghost:null, over:null};
  if(e.target.setPointerCapture) e.target.setPointerCapture(e.pointerId);
  dragged = false;
}
document.addEventListener("pointermove", function(e){
  if(!drag) return;
  if(!drag.ghost){
    if(Math.abs(e.clientX-drag.x) + Math.abs(e.clientY-drag.y) < 6) return;
    drag.ghost = el("div", "ghost", drag.label);
    document.body.appendChild(drag.ghost);
    document.body.classList.add("dragging");
  }
  e.preventDefault();
  drag.ghost.style.left = (e.clientX + 8) + "px";
  drag.ghost.style.top = (e.clientY + 8) + "px";
  var over = slotAt(e.clientX, e.clientY);
  if(over !== drag.over){
    if(drag.over) drag.over.classList.remove("over");
    if(over) over.classList.add("over");
    drag.over = over;
  }
});
document.addEventListener("pointerup", function(e){
  if(!drag) return;
  var d = drag; drag = null;
  if(!d.ghost) return;
  d.ghost.remove();
  document.body.classList.remove("dragging");
  dragged = true;
  setTimeout(function(){ dragged = false; }, 0);
  var target = slotAt(e.clientX, e.clientY);
  if(target && target.setFn) place(d.id, target.setFn);
});

// One group of blocks at a time, in a strip above the chart, so the palette stays short.
function palette(){
  var wrap = el("div", "palette");
  var top = el("div", "ptop");
  top.appendChild(el("span", "eyebrow", "Blocks"));
  GROUPS.forEach(function(g){
    var t = el("button", "gtab" + (group===g[0] ? " is-active" : ""), g[1]);
    t.setAttribute("aria-pressed", group===g[0] ? "true" : "false");
    t.onclick = function(){ group = g[0]; render(); };
    top.appendChild(t);
  });
  wrap.appendChild(top);
  var box = el("div", "pbs");
  BLOCKS.forEach(function(b){
    if(b.kind!==group) return;
    var p = el("button", "pb " + b.kind, b.label);
    if(b.arms) p.appendChild(el("span", "sub", b.arms.join(" / ")));
    p.setAttribute("aria-pressed", armed===b.id ? "true" : "false");
    p.onclick = function(){
      if(dragged){ dragged = false; return; }
      armed = armed===b.id ? null : b.id; note = ""; render();
    };
    p.onpointerdown = function(e){ startDrag(e, b); };
    box.appendChild(p);
  });
  wrap.appendChild(box);
  wrap.appendChild(el("p", "hint", "Drag a block onto a dashed slot, or tap a block, then tap the slot."));
  return wrap;
}

function renderTabs(){
  var box = document.getElementById("tabs");
  box.textContent = "";
  STAGES.forEach(function(s, i){
    var t = el("button", "tab" + (i===current ? " is-active" : ""), s.title);
    t.setAttribute("aria-pressed", i===current ? "true" : "false");
    if(solved[s.id]){ var tick = el("span", "tick", "✓"); tick.setAttribute("aria-label", "built correctly"); t.appendChild(tick); }
    t.onclick = function(){ current = i; armed = null; note = ""; showDesc = false; render(); };
    box.appendChild(t);
  });
  var done = STAGES.filter(function(s){ return solved[s.id]; }).length;
  document.getElementById("progress").textContent = "Build the flow chart · " + done + "/" + STAGES.length;
}

function renderPanel(){
  var stage = STAGES[current];
  var show = checked[stage.id];
  var panel = document.getElementById("panel");
  panel.textContent = "";

  var desc = el("div", "desc");
  var toggle = el("button", null, (showDesc ? "Hide" : "Show") + " the protocol description from Table 2");
  toggle.setAttribute("aria-expanded", showDesc ? "true" : "false");
  toggle.onclick = function(){ showDesc = !showDesc; render(); };
  desc.appendChild(toggle);
  if(showDesc) desc.appendChild(el("p", null, stage.description));
  panel.appendChild(desc);

  panel.appendChild(palette());
  var chart = el("div", "chart");
  var tree = el("div", "tree");
  tree.appendChild(el("div", "start", "Problem arrives"));
  tree.appendChild(el("div", "vline"));
  var g = show ? grade(charts[stage.id], stage) : null;
  tree.appendChild(draw(charts[stage.id], function(v){ charts[stage.id] = v; }, g));
  chart.appendChild(tree);
  panel.appendChild(chart);

  var full = complete(charts[stage.id]);
  var act = el("div", "actions");
  var check = el("button", "primary", "Check chart");
  check.disabled = !full;
  check.onclick = function(){ checked[stage.id] = true; commit(); };
  act.appendChild(check);
  var reset = el("button", null, "Reset");
  reset.disabled = !charts[stage.id];
  reset.onclick = function(){ charts[stage.id] = null; armed = null; changed(); };
  act.appendChild(reset);
  var msg = note || (!full && charts[stage.id] ? "Every path must end in a submit or audit block." : "");
  if(msg) act.appendChild(el("span", "status", msg));
  panel.appendChild(act);

  if(show){
    var v = el("div", "verdict" + (solved[stage.id] ? " ok" : ""));
    if(solved[stage.id]){
      v.appendChild(el("strong", null, "Correct. This is the row Table 2 gives for this protocol."));
      v.appendChild(el("p", "explain", stage.explanation));
    } else {
      v.appendChild(el("strong", null, "Not quite. "));
      var anyWrong = false;
      g.ok.forEach(function(x){ if(!x) anyWrong = true; });
      var gap = g.missing > 0 ? "the chart is missing a step" : g.missing < 0 ? "the chart has a step too many" : "";
      var text = anyWrong ? "Blocks marked ✓ match Table 2; blocks marked ✗ do not." + (gap ? " Also, " + gap + "." : "")
                          : "Every block you placed matches Table 2, but " + gap + ".";
      v.appendChild(document.createTextNode(text + " Adjust the chart and check again."));
    }
    panel.appendChild(v);
  }
}

function summary(){
  var done = [], open = [];
  STAGES.forEach(function(s){ (solved[s.id] ? done : open).push(s.title); });
  var stage = STAGES[current];
  return "The learner is rebuilding the six blue-team protocols of Table 2 as flow charts. " +
    "Built correctly so far: " + (done.length ? done.join("; ") : "none") + ". " +
    "Still open: " + (open.length ? open.join("; ") : "none") + ". " +
    "Currently editing “" + stage.title + "”: Problem arrives → " + describe(charts[stage.id]) + ".";
}

function changed(){ checked[STAGES[current].id] = false; commit(); }

function commit(){
  STAGES.forEach(function(s){ solved[s.id] = same(charts[s.id], key(s)); });
  render();
  if(window.Lens){
    Lens.saveState({v:2, charts:charts, checked:checked, current:current}, summary());
    if(STAGES.every(function(s){ return solved[s.id]; })) Lens.complete();
  }
}

function render(){ renderTabs(); renderPanel(); }

// State saved by the earlier chip-picker version: {answers:{id:{steps, branch, terminals}}}.
function fromOld(a){
  if(!a || (!a.steps.length && !a.branch)) return null;
  var tail = null;
  if(a.branch==="none") tail = a.terminals[0] ? {b:a.terminals[0]} : null;
  else if(a.branch && block(a.branch)) tail = {b:a.branch, arms:block(a.branch).arms.map(function(x, i){ return a.terminals[i] ? {b:a.terminals[i]} : null; })};
  for(var i=a.steps.length-1;i>=0;i--) tail = {b:a.steps[i], next:tail};
  return tail;
}

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(state && state.v===2 && state.charts){
      STAGES.forEach(function(s){ if(state.charts[s.id] !== undefined) charts[s.id] = state.charts[s.id]; });
      if(state.checked) checked = state.checked;
    } else if(state && state.answers){
      STAGES.forEach(function(s){
        var a = state.answers[s.id];
        if(a) charts[s.id] = fromOld({steps:a.steps||[], branch:a.branch||null, terminals:a.terminals||[]});
      });
      if(state.checked) checked = state.checked;
    }
    if(state && typeof state.current === "number") current = state.current;
    STAGES.forEach(function(s){ solved[s.id] = same(charts[s.id], key(s)); });
    render();
  });
}
render();
</script>
</body>
</html>

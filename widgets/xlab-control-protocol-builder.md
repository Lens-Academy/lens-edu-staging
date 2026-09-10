---
id: 'ebb967f7-2730-4e67-bde5-34fc018d17d3'
title: Build the blue-team protocols
summary_for_tutor: "A construction exercise for Table 2 of Greenblatt et al.'s AI control paper. Six tabs, one per blue-team protocol (don't use untrusted models, upfront auditing, trusted monitoring, defer to trusted 10%, untrusted monitoring, trusted editing 20%). For each the learner assembles a flow chart for an incoming problem: an ordered list of steps (U writes a solution, T rates suspicion, a second copy of U rates suspicion), then one branch (first 2% of problems, top 2%, top 2/10%, top 2/20%), then one terminal per branch arm (submit U's code, have T rewrite, have T edit U's code, audit with H). Check reveals which slots are wrong, and a correct protocol reveals a one-sentence explanation of what that row of Table 2 buys. The point is that every protocol in the paper is the same three-part shape and only the routing rule and the fallback differ."
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
     on XLab's AI Control track (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look. -->
<style>
:root{
  --bg:#ffffff; --page:#faf8f3; --text:#1a1a1a; --muted:#5a5a5a; --border:#e8e5df;
  --accent:#b87018; --accent-hover:#9a5c10; --ok:#2f6b3a; --bad:#9a2c2c;
  --font-ui:"DM Sans",Arial,sans-serif; --font-heading:"Newsreader",Georgia,serif;
}
*{box-sizing:border-box}
body{margin:0;padding:16px;font:14px/1.5 var(--font-ui);color:var(--text);background:var(--bg)}
h2{font-family:var(--font-heading);font-weight:600;margin:0 0 4px;font-size:17px}
p{margin:0 0 10px}
.eyebrow{font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--muted);margin:0 0 6px}
.tabs{display:flex;flex-wrap:wrap;gap:6px;margin:12px 0}
button{font:inherit;color:inherit;border:1px solid var(--border);border-radius:8px;background:#fff;padding:7px 10px;cursor:pointer;text-align:left}
button:hover{background:var(--page)}
button.is-active{border-color:var(--text);box-shadow:0 0 0 1px var(--text)}
.tab{font-size:13px}
.tab .num{color:var(--muted);margin-right:6px}
.tab .tick{color:var(--ok);font-weight:600;margin-left:6px}
.card{border:1px solid var(--border);border-radius:8px;padding:14px;background:#fff}
.desc{color:var(--muted);margin:0 0 12px}
.slot{margin:0 0 14px}
.slot h3{font:600 12px/1.4 var(--font-ui);letter-spacing:.06em;text-transform:uppercase;color:var(--muted);margin:0 0 6px}
.chips{display:flex;flex-wrap:wrap;gap:6px;min-height:34px;padding:6px;border:1px dashed var(--border);border-radius:8px;background:var(--page)}
.chips .empty{color:var(--muted);font-size:13px;padding:3px 4px}
.chip{display:inline-flex;align-items:center;gap:6px;border:1px solid var(--border);background:#fff;border-radius:999px;padding:4px 10px;font-size:13px;cursor:pointer}
.chip .x{color:var(--muted);font-weight:600}
.chip.good{border-color:var(--ok);box-shadow:0 0 0 1px var(--ok)}
.chip.bad{border-color:var(--bad);box-shadow:0 0 0 1px var(--bad)}
.palette{display:flex;flex-wrap:wrap;gap:6px;margin-top:6px}
.palette button{font-size:13px;padding:6px 10px}
.arm{display:flex;flex-wrap:wrap;align-items:center;gap:8px;margin:0 0 8px}
.arm .label{min-width:104px;font-weight:500}
.arm .picked{font-size:13px}
.actions{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-top:12px}
.actions .primary{border-color:var(--accent);color:#fff;background:var(--accent)}
.actions .primary:hover{background:var(--accent-hover)}
.verdict{font-size:13px}
.verdict.ok{color:var(--ok)}
.verdict.bad{color:var(--bad)}
.explain{font-size:13px;color:var(--text);margin-top:12px;border-left:2px solid var(--ok);padding-left:10px}
.note{font-size:13px;color:var(--muted);margin-top:10px}
@media (max-width:420px){ .arm .label{min-width:0;width:100%} }
</style>
</head>
<body>
<p class="eyebrow">Table 2, rebuilt</p>
<h2 id="ttl">Build the blue-team protocols</h2>
<p class="desc" id="intro">Every protocol in the paper answers the same question about an incoming programming problem: who writes the code, who rates it, and what happens in each suspicion band. Pick the steps, then the branch, then one outcome per branch arm.</p>
<div class="tabs" id="tabs"></div>
<div class="card" id="panel"></div>
<script>
"use strict";
var STEPS = [
  {id:"u-writes", label:"U writes a solution"},
  {id:"t-rates",  label:"T rates how suspicious U's code looks"},
  {id:"u-rates",  label:"A separate copy of U rates how suspicious the code looks"}
];
var BRANCHES = [
  {id:"none",           label:"No branch: every problem is handled the same way", arms:["Every problem"]},
  {id:"branch-first-2", label:"Among the first 2% of problems?", arms:["Yes","No"]},
  {id:"branch-top-2",   label:"Suspicion rank?", arms:["Top 2%","Bottom 98%"]},
  {id:"branch-2-10",    label:"Suspicion rank?", arms:["Top 2%","Top 2–10%","Bottom 90%"]},
  {id:"branch-2-20",    label:"Suspicion rank?", arms:["Top 2%","Top 2–20%","Bottom 80%"]}
];
var TERMINALS = [
  {id:"submit-u",    label:"Submit U's solution"},
  {id:"submit-t",    label:"Have T write its own solution and submit that"},
  {id:"submit-edit", label:"Have T edit U's code to remove any backdoor; submit the edit"},
  {id:"audit",       label:"Audit with H: shut down if backdoored, otherwise submit"}
];
var STAGES = [
  {id:"dont-use-untrusted", title:"Don't use untrusted models",
   description:"Produce code using only H and T.",
   steps:[], branch:"none", terminals:["submit-t"],
   explanation:"With U out of the picture entirely there is nothing to monitor or audit, T just writes and submits every solution. Safety is 100% and usefulness is 2%: this is the floor the other protocols are trying to beat."},
  {id:"upfront-auditing", title:"Upfront auditing",
   description:"Produce code using U. Audit the produced code on the first 2% of problems.",
   steps:["u-writes"], branch:"branch-first-2", terminals:["audit","submit-u"],
   explanation:"The decision here is positional, not suspicion-based, no one ever rates the code. That is exactly why the red team's “backdoor rarely, at random” attack works: most backdoors land in the unaudited 98%."},
  {id:"trusted-monitoring", title:"Trusted monitoring",
   description:"Produce code using U, and ask T to review how suspicious it looks. Audit the top 2% most suspicious code.",
   steps:["u-writes","t-rates"], branch:"branch-top-2", terminals:["audit","submit-u"],
   explanation:"Compared with upfront auditing, the only change is that the 2% audit budget is now spent on the most suspicious code rather than the first code to arrive, T's ratings decide where H looks."},
  {id:"defer-to-trusted", title:"Defer to trusted (10%)",
   description:"Apply the same approach as trusted monitoring, but submit a solution written by T when U's code is between top 2% and top 10% suspicion.",
   steps:["u-writes","t-rates"], branch:"branch-2-10", terminals:["audit","submit-t","submit-u"],
   explanation:"The new middle band (top 2–10%) is code too suspicious to trust but not suspicious enough to spend an H point on, so the protocol throws U's version away and submits T's instead, trading a little usefulness for safety."},
  {id:"untrusted-monitoring", title:"Untrusted monitoring",
   description:"Produce code using U, and ask a separate copy of U (the untrusted monitor) to monitor how suspicious it looks. Audit the top 2% most suspicious code. Evaluate this untrusted monitor on synthetic examples of backdoors (produced by H) to ensure it is doing its best, and use the untrusted monitor on redacted problem statements and code to make collusion harder.",
   steps:["u-writes","u-rates"], branch:"branch-top-2", terminals:["audit","submit-u"],
   explanation:"Structurally identical to trusted monitoring, the only change is who rates the code. Because the monitor is itself untrusted, it has to be kept honest: validated against synthetic backdoors from H, and shown redacted inputs so colluding with the policy is harder."},
  {id:"trusted-editing", title:"Trusted editing (20%)",
   description:"Ask U to produce code, and ask T to edit it to remove backdoors. Use trusted monitoring to determine suspicion. Audit the top 2% most suspicious U code, use an edited solution for suspicion between the top 2% and top 20%, and use U's solution for suspicion in the bottom 80%.",
   steps:["u-writes","t-rates"], branch:"branch-2-20", terminals:["audit","submit-edit","submit-u"],
   explanation:"Same skeleton as defer to trusted, with two changes: the middle band widens to top 2–20%, and instead of discarding U's work there, T edits it, keeping most of U's usefulness while stripping anything that looks like a backdoor."}
];

var answers = {};
var solved = {};
var checked = {};
var current = 0;

function blank(){ return {steps:[], branch:null, terminals:[]}; }
STAGES.forEach(function(s){ answers[s.id] = blank(); solved[s.id] = false; checked[s.id] = false; });

function byId(list,id){ for(var i=0;i<list.length;i++){ if(list[i].id===id) return list[i]; } return null; }
function el(tag, cls, text){ var n=document.createElement(tag); if(cls) n.className=cls; if(text!=null) n.textContent=text; return n; }

function isSolved(stage){
  var a = answers[stage.id];
  if(a.branch !== stage.branch) return false;
  if(a.steps.length !== stage.steps.length) return false;
  for(var i=0;i<stage.steps.length;i++){ if(a.steps[i]!==stage.steps[i]) return false; }
  for(var j=0;j<stage.terminals.length;j++){ if(a.terminals[j]!==stage.terminals[j]) return false; }
  return true;
}

function renderTabs(){
  var box = document.getElementById("tabs");
  box.textContent = "";
  STAGES.forEach(function(s,i){
    var b = el("button","tab");
    var num = el("span","num", String(i+1)+".");
    b.appendChild(num);
    b.appendChild(document.createTextNode(s.title));
    if(solved[s.id]){ var t = el("span","tick","correct"); b.appendChild(t); }
    if(i===current) b.className = "tab is-active";
    b.setAttribute("aria-pressed", i===current ? "true" : "false");
    b.onclick = function(){ current = i; render(); };
    box.appendChild(b);
  });
}

function renderPanel(){
  var stage = STAGES[current];
  var a = answers[stage.id];
  var show = checked[stage.id];
  var panel = document.getElementById("panel");
  panel.textContent = "";

  panel.appendChild(el("h2", null, stage.title));
  panel.appendChild(el("p","desc", stage.description));

  // steps
  var s1 = el("div","slot");
  s1.appendChild(el("h3", null, "1. Steps, in order"));
  var chips = el("div","chips");
  if(a.steps.length === 0){ chips.appendChild(el("span","empty","No steps yet. For one protocol that is the right answer.")); }
  a.steps.forEach(function(sid, idx){
    var cls = "chip";
    if(show){ cls += (stage.steps[idx] === sid && idx < stage.steps.length) ? " good" : " bad"; }
    var c = el("button", cls);
    c.appendChild(document.createTextNode(byId(STEPS,sid).label));
    c.appendChild(el("span","x","x"));
    c.title = "Remove this step";
    c.onclick = function(){ a.steps.splice(idx,1); checked[stage.id]=false; commit(); };
    chips.appendChild(c);
  });
  s1.appendChild(chips);
  var pal = el("div","palette");
  STEPS.forEach(function(st){
    var b = el("button", null, "+ " + st.label);
    b.onclick = function(){ a.steps.push(st.id); checked[stage.id]=false; commit(); };
    pal.appendChild(b);
  });
  s1.appendChild(pal);
  panel.appendChild(s1);

  // branch
  var s2 = el("div","slot");
  s2.appendChild(el("h3", null, "2. The routing question"));
  var pal2 = el("div","palette");
  BRANCHES.forEach(function(br){
    var lbl = br.label;
    if(br.arms.length > 1) lbl += "  (" + br.arms.join(" / ") + ")";
    var b = el("button", null, lbl);
    if(a.branch === br.id){
      b.className = "is-active";
      if(show) b.className = "is-active " + (br.id === stage.branch ? "" : "");
      b.style.borderColor = show ? (br.id === stage.branch ? "var(--ok)" : "var(--bad)") : "";
    }
    b.onclick = function(){
      if(a.branch !== br.id){ a.branch = br.id; a.terminals = []; }
      checked[stage.id]=false; commit();
    };
    pal2.appendChild(b);
  });
  s2.appendChild(pal2);
  panel.appendChild(s2);

  // terminals
  if(a.branch){
    var br = byId(BRANCHES, a.branch);
    var s3 = el("div","slot");
    s3.appendChild(el("h3", null, "3. Where each path ends"));
    br.arms.forEach(function(arm, i){
      var row = el("div","arm");
      row.appendChild(el("span","label", arm + ":"));
      TERMINALS.forEach(function(t){
        var b = el("button", null, t.label);
        b.style.fontSize = "13px";
        if(a.terminals[i] === t.id){
          b.className = "is-active";
          if(show) b.style.borderColor = (stage.branch === a.branch && stage.terminals[i] === t.id) ? "var(--ok)" : "var(--bad)";
        }
        b.onclick = function(){ a.terminals[i] = t.id; checked[stage.id]=false; commit(); };
        row.appendChild(b);
      });
      s3.appendChild(row);
    });
    panel.appendChild(s3);
  }

  var act = el("div","actions");
  var check = el("button","primary","Check this protocol");
  check.onclick = function(){ checked[stage.id] = true; commit(); };
  act.appendChild(check);
  var reset = el("button", null, "Clear");
  reset.onclick = function(){ answers[stage.id] = blank(); checked[stage.id]=false; commit(); };
  act.appendChild(reset);
  var solvedNow = false;
  if(show){
    solvedNow = isSolved(stage);
    act.appendChild(el("span", "verdict " + (solvedNow ? "ok" : "bad"),
      solvedNow ? "Correct. That is the row Table 2 gives for this protocol."
                : "Not yet. Green slots match Table 2; red ones do not."));
  }
  panel.appendChild(act);
  if(solvedNow && stage.explanation){
    panel.appendChild(el("p","explain", stage.explanation));
  }

  var done = 0;
  STAGES.forEach(function(s){ if(solved[s.id]) done++; });
  panel.appendChild(el("p","note", done + " of " + STAGES.length + " protocols built correctly."));
}

function summary(){
  var lines = ["The learner is rebuilding the six blue-team protocols of Table 2 as flow charts."];
  var done = [];
  var open = [];
  STAGES.forEach(function(s){ (solved[s.id] ? done : open).push(s.title); });
  lines.push("Built correctly so far: " + (done.length ? done.join("; ") : "none") + ".");
  lines.push("Still open: " + (open.length ? open.join("; ") : "none") + ".");
  var stage = STAGES[current];
  var a = answers[stage.id];
  var stepTxt = a.steps.length ? a.steps.map(function(x){ return byId(STEPS,x).label; }).join(" then ") : "no steps";
  var brTxt = a.branch ? byId(BRANCHES,a.branch).label : "no branch chosen";
  var tTxt = a.terminals.length ? a.terminals.map(function(x){ return x ? byId(TERMINALS,x).label : "(unset)"; }).join(" | ") : "no outcomes chosen";
  lines.push("Currently editing “" + stage.title + "”: " + stepTxt + "; branch: " + brTxt + "; outcomes: " + tTxt + ".");
  return lines.join(" ");
}

function commit(){
  STAGES.forEach(function(s){ solved[s.id] = isSolved(s); });
  render();
  if(window.Lens){
    var state = {answers:answers, checked:checked, current:current};
    Lens.saveState(state, summary());
    var all = STAGES.every(function(s){ return solved[s.id]; });
    if(all) Lens.complete();
  }
}

function render(){ renderTabs(); renderPanel(); }

if(window.Lens && Lens.onState){
  Lens.onState(function(state){
    if(state && state.answers){
      STAGES.forEach(function(s){
        var a = state.answers[s.id];
        if(a) answers[s.id] = {steps:(a.steps||[]).slice(), branch:a.branch||null, terminals:(a.terminals||[]).slice()};
      });
      if(state.checked) checked = state.checked;
      if(typeof state.current === "number") current = state.current;
    }
    STAGES.forEach(function(s){ solved[s.id] = isSolved(s); });
    render();
  });
}
render();
</script>
</body>
</html>

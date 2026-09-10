---
id: 'f17dc8fa-4533-430c-94be-c6423931f83f'
title: Building a password-locked model
summary_for_tutor: An interactive reconstruction of the password-locking pipeline from section 4.1 of Greenblatt et al. The learner builds three flow charts out of a shared palette of eleven blocks, one chart at a time: how the strong policy is produced, how the weak policy is produced, and what happens to the locked model on each individual training prompt. The third chart contains a branch on whether the prompt carries the correct password. Two palette blocks are distractors that belong to other parts of the paper (starting from randomly initialised weights, which is section 7, and filtering generations for correct ones, which is the filtering baseline in section 6.1). Each chart can be checked; a correct chart reveals a short explanation of why that construction was chosen and what it costs. The widget reports which charts the learner has solved and how many attempts each took.
height: auto
tags: []
---
<!-- Ported from XLab's AI Control track (exercise c-plm-locking-flowcharts,
     github.com/XLabTracks/tracks). Palette, stage descriptions, solutions and
     explanations are XLab's; the interaction is rewritten for Lens. -->
<!doctype html>
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
h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
p { margin: 0 0 12px; }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 6px; }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
button:hover:not(:disabled) { background: var(--page); }
button:disabled { cursor: default; opacity: 0.45; }
button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
.tabs { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 16px; }
.tab { border-radius: 999px; padding: 6px 12px; font-size: 13px; }
.tab.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
.tab .tick { color: var(--accent); font-weight: 600; }
.desc { color: var(--muted); margin-bottom: 14px; }
.lanes { display: flex; flex-direction: column; gap: 10px; margin-bottom: 16px; }
.lane { border: 1px dashed var(--border); border-radius: 8px; padding: 10px; background: var(--page); }
.lane.is-target { border-style: solid; border-color: var(--text); }
.lane-head { display: flex; align-items: baseline; justify-content: space-between; gap: 8px; margin-bottom: 8px; }
.lane-label { font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
.lane-pick { font-size: 12px; padding: 3px 8px; border-radius: 999px; }
.branch-lanes { display: flex; flex-direction: column; gap: 8px; margin-top: 8px; padding-left: 14px; border-left: 2px solid var(--border); }
.slot { display: block; width: 100%; margin-bottom: 8px; }
.slot:last-child { margin-bottom: 0; }
.slot .kind { display: block; font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
.slot.is-branch { border-color: var(--accent); }
.empty { color: var(--muted); font-size: 13px; font-style: italic; }
.arrow { color: var(--muted); text-align: center; font-size: 12px; margin: -4px 0 4px; }
.palette { display: flex; flex-direction: column; gap: 8px; }
.palette button { width: 100%; }
.palette button.is-used { opacity: 0.4; }
.actions { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 16px; }
.actions .primary { border-color: var(--accent); color: var(--accent-hover); font-weight: 500; }
.verdict { margin-top: 14px; border-radius: 8px; padding: 12px; border: 1px solid var(--border); background: var(--page); }
.verdict.ok { border-color: var(--accent); }
.verdict strong { display: block; margin-bottom: 4px; }
.done { margin-top: 16px; border: 1px solid var(--accent); border-radius: 8px; padding: 12px; background: var(--page); }
.sr { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
@media (min-width: 620px) { .cols { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; } }
</style>
</head>
<body>
<div class="card">
  <p class="eyebrow">Section 4.1, reconstructed</p>
  <p>Three flow charts: how the strong policy, the weak policy, and the locked model are each produced. Pick a chart, then tap blocks from the palette to add them in order. Tap a placed block to take it out again. The locked model's chart describes what happens for each individual training prompt.</p>
  <div class="tabs" id="tabs" role="tablist"></div>
  <div id="stage"></div>
  <div id="done"></div>
</div>
<div class="sr" aria-live="polite" id="live"></div>
<script>
(function () {
  var PALETTE = [
    { id: "start-strong-base", kind: "step", label: "Start from the large base model" },
    { id: "start-weak-base", kind: "step", label: "Start from the much smaller base model" },
    { id: "start-scratch", kind: "step", label: "Start from randomly initialized weights" },
    { id: "ft-task", kind: "step", label: "Fine-tune it to perform the task as well as possible" },
    { id: "ft-imitate-strong", kind: "step", label: "Fine-tune it to imitate samples from the strong policy" },
    { id: "filter-correct", kind: "step", label: "Filter its generations, keeping only the correct ones" },
    { id: "branch-password", kind: "branch", label: "Does the prompt carry the correct password?", branchLabels: ["Yes", "No, or a wrong one"] },
    { id: "out-strong", kind: "terminal", label: "Done: this is the strong policy" },
    { id: "out-weak", kind: "terminal", label: "Done: this is the weak policy" },
    { id: "train-toward-strong", kind: "terminal", label: "Train the model toward the strong policy's answer to this prompt" },
    { id: "train-toward-weak", kind: "terminal", label: "Train the model toward the weak policy's answer to this prompt" }
  ];
  var STAGES = [
    {
      id: "build-strong",
      title: "The strong policy",
      description: "Construct the strong policy: the hidden capability the locked model will carry. Its performance should be as high as possible, so that the tasks studied stay interesting.",
      solution: { main: ["start-strong-base", "ft-task", "out-strong"], yes: [], no: [] },
      explanation: "Fine-tuning the large base upward on the task widens the gap between hidden and visible capability, which is what makes the instrument sensitive. The paper registers the cost of this choice in its limitations: a capability explicitly trained into the weights may be more salient, and so easier to surface, than one that never was. (For MATH the base model was already strong enough and is used as-is.)"
    },
    {
      id: "build-weak",
      title: "The weak policy",
      description: "Construct the weak policy: what the locked model will display when the password is absent. It must genuinely attempt the task, at much lower quality.",
      solution: { main: ["start-weak-base", "ft-imitate-strong", "out-weak"], yes: [], no: [] },
      explanation: "A small pretrained model used as-is mostly does not attempt the task at all, and non-attempts are as detectable as refusal; fine-tuning it to imitate the strong policy compels attempts in the right format at the quality its capacity permits. Filtering raw generations for correct answers is the tempting wrong block here: it selects on the outcome and leaves the weak performance level ill-defined. One consequence of the imitation route returns in section 6: the weak policy occasionally produces good output."
    },
    {
      id: "build-locked",
      title: "The locked model",
      description: "Construct the locked model: with the correct password in the prompt it behaves like the strong policy, and with no password or a wrong one it behaves like the weak policy.",
      solution: { main: ["start-strong-base", "branch-password"], yes: ["train-toward-strong"], no: ["train-toward-weak"] },
      explanation: "The locked model starts from the same base as the strong policy, and that identity is what guarantees it genuinely possesses the hidden capability rather than approximating it. The no-password arm deliberately covers wrong passwords too: the training mixture maps a heterogeneous list of wrong passwords to weak behavior, forcing the trigger onto the one specific string instead of onto unusual text in general."
    }
  ];

  var byId = {};
  PALETTE.forEach(function (b) { byId[b.id] = b; });

  var state = { active: 0, charts: {}, solved: {}, attempts: {}, revealed: {} };
  STAGES.forEach(function (s) { state.charts[s.id] = { main: [], yes: [], no: [] }; });
  var target = "main";
  var completedOnce = false;

  var tabsEl = document.getElementById("tabs");
  var stageEl = document.getElementById("stage");
  var doneEl = document.getElementById("done");
  var liveEl = document.getElementById("live");

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }

  function stage() { return STAGES[state.active]; }
  function chart() { return state.charts[stage().id]; }
  function hasBranch() { return chart().main.indexOf("branch-password") !== -1; }

  function usedIds() {
    var c = chart();
    return c.main.concat(c.yes, c.no);
  }

  function sameList(a, b) {
    if (a.length !== b.length) return false;
    for (var i = 0; i < a.length; i++) { if (a[i] !== b[i]) return false; }
    return true;
  }

  function isSolved(s) {
    var c = state.charts[s.id];
    return sameList(c.main, s.solution.main) && sameList(c.yes, s.solution.yes) && sameList(c.no, s.solution.no);
  }

  function summary() {
    var parts = STAGES.map(function (s) {
      var st = state.solved[s.id] ? "solved" : (state.revealed[s.id] ? "answer shown" : "not yet solved");
      var n = state.attempts[s.id] || 0;
      var c = state.charts[s.id];
      var placed = c.main.map(function (id) { return byId[id].label; });
      if (c.yes.length) placed.push("Yes branch: " + c.yes.map(function (id) { return byId[id].label; }).join(", "));
      if (c.no.length) placed.push("No branch: " + c.no.map(function (id) { return byId[id].label; }).join(", "));
      return s.title + ": " + st + " after " + n + " check" + (n === 1 ? "" : "s") + ". Blocks placed: " + (placed.length ? placed.join(" then ") : "none") + ".";
    });
    return "Password-locking pipeline exercise. " + parts.join(" ");
  }

  function save() {
    if (!window.Lens) return;
    Lens.saveState({ charts: state.charts, solved: state.solved, attempts: state.attempts, revealed: state.revealed }, summary());
    var allDone = STAGES.every(function (s) { return state.solved[s.id] || state.revealed[s.id]; });
    if (allDone && !completedOnce) { completedOnce = true; Lens.complete(); }
  }

  function renderTabs() {
    tabsEl.textContent = "";
    STAGES.forEach(function (s, i) {
      var b = el("button", "tab" + (i === state.active ? " is-active" : ""));
      b.setAttribute("role", "tab");
      b.setAttribute("aria-selected", i === state.active ? "true" : "false");
      b.appendChild(document.createTextNode((i + 1) + ". " + s.title + " "));
      if (state.solved[s.id]) { var t = el("span", "tick", "solved"); b.appendChild(t); }
      else if (state.revealed[s.id]) { b.appendChild(el("span", "tick", "shown")); }
      b.onclick = function () { state.active = i; target = "main"; render(); };
      tabsEl.appendChild(b);
    });
  }

  function laneNode(key, label, list, selectable) {
    var lane = el("div", "lane" + (target === key && selectable ? " is-target" : ""));
    var head = el("div", "lane-head");
    head.appendChild(el("span", "lane-label", label));
    if (selectable) {
      var pick = el("button", "lane-pick", target === key ? "adding here" : "add here");
      pick.onclick = function () { target = key; render(); };
      head.appendChild(pick);
    }
    lane.appendChild(head);
    if (!list.length) {
      lane.appendChild(el("p", "empty", "Empty."));
    } else {
      list.forEach(function (id, idx) {
        if (idx > 0) lane.appendChild(el("div", "arrow", "then"));
        var b = el("button", "slot" + (byId[id].kind === "branch" ? " is-branch" : ""));
        b.appendChild(el("span", "kind", byId[id].kind));
        b.appendChild(document.createTextNode(byId[id].label));
        b.title = "Remove this block";
        b.onclick = function () {
          list.splice(idx, 1);
          if (id === "branch-password") { chart().yes = []; chart().no = []; if (target !== "main") target = "main"; }
          state.solved[stage().id] = false;
          render(); save();
        };
        lane.appendChild(b);
      });
    }
    return lane;
  }

  function render() {
    renderTabs();
    var s = stage();
    var c = chart();
    stageEl.textContent = "";

    stageEl.appendChild(el("h2", null, s.title));
    stageEl.appendChild(el("p", "desc", s.description));

    var cols = el("div", "cols");

    var left = el("div", null);
    left.appendChild(el("p", "eyebrow", "Your chart"));
    var lanes = el("div", "lanes");
    lanes.appendChild(laneNode("main", "Main path", c.main, true));
    if (hasBranch()) {
      var sub = el("div", "branch-lanes");
      sub.appendChild(laneNode("yes", "Yes", c.yes, true));
      sub.appendChild(laneNode("no", "No, or a wrong one", c.no, true));
      lanes.appendChild(sub);
    }
    left.appendChild(lanes);
    cols.appendChild(left);

    var right = el("div", null);
    right.appendChild(el("p", "eyebrow", "Palette"));
    var pal = el("div", "palette");
    var used = usedIds();
    PALETTE.forEach(function (blk) {
      var b = el("button", used.indexOf(blk.id) !== -1 ? "is-used" : null);
      b.appendChild(el("span", "kind", blk.kind));
      b.appendChild(document.createTextNode(blk.label));
      b.disabled = used.indexOf(blk.id) !== -1 || (blk.kind === "branch" && target !== "main");
      b.onclick = function () {
        c[target].push(blk.id);
        if (blk.id === "branch-password") target = "yes";
        state.solved[s.id] = false;
        render(); save();
      };
      pal.appendChild(b);
    });
    right.appendChild(pal);
    cols.appendChild(right);
    stageEl.appendChild(cols);

    var actions = el("div", "actions");
    var check = el("button", "primary", "Check this chart");
    check.disabled = !c.main.length;
    check.onclick = function () {
      state.attempts[s.id] = (state.attempts[s.id] || 0) + 1;
      state.solved[s.id] = isSolved(s);
      render(); save();
      liveEl.textContent = state.solved[s.id] ? "Correct." : "Not yet correct.";
    };
    actions.appendChild(check);

    var clear = el("button", null, "Clear");
    clear.disabled = !usedIds().length;
    clear.onclick = function () {
      state.charts[s.id] = { main: [], yes: [], no: [] };
      state.solved[s.id] = false;
      target = "main";
      render(); save();
    };
    actions.appendChild(clear);

    if ((state.attempts[s.id] || 0) >= 2 && !state.solved[s.id] && !state.revealed[s.id]) {
      var reveal = el("button", null, "Show the answer");
      reveal.onclick = function () {
        state.charts[s.id] = { main: s.solution.main.slice(), yes: s.solution.yes.slice(), no: s.solution.no.slice() };
        state.revealed[s.id] = true;
        target = "main";
        render(); save();
      };
      actions.appendChild(reveal);
    }
    stageEl.appendChild(actions);

    if (state.solved[s.id] || state.revealed[s.id]) {
      var v = el("div", "verdict ok");
      v.appendChild(el("strong", null, state.solved[s.id] ? "That is the construction." : "The construction, filled in for you."));
      v.appendChild(el("p", null, s.explanation));
      stageEl.appendChild(v);
    } else if (state.attempts[s.id]) {
      var w = el("div", "verdict");
      w.appendChild(el("strong", null, "Not this one yet."));
      w.appendChild(el("p", null, "Two blocks in the palette belong to other parts of the paper and are not used in any of the three charts. Section 4.1 says what each policy is built from and in what order."));
      stageEl.appendChild(w);
    }

    doneEl.textContent = "";
    var allDone = STAGES.every(function (st) { return state.solved[st.id] || state.revealed[st.id]; });
    if (allDone) {
      var d = el("div", "done");
      d.appendChild(el("strong", null, "All three charts are built."));
      d.appendChild(el("p", null, "The two blocks you never used are the ones the paper uses elsewhere: starting from randomly initialized weights is the from-scratch comparison in section 7, and filtering generations for the correct ones is a baseline elicitation method in section 6.1."));
      doneEl.appendChild(d);
    }
  }

  function boot(saved, meta) {
    if (saved && saved.charts) {
      STAGES.forEach(function (s) {
        var c = saved.charts[s.id];
        if (c) state.charts[s.id] = { main: (c.main || []).slice(), yes: (c.yes || []).slice(), no: (c.no || []).slice() };
      });
      state.solved = saved.solved || {};
      state.attempts = saved.attempts || {};
      state.revealed = saved.revealed || {};
    }
    if (meta && meta.completed) completedOnce = true;
    render();
  }

  if (window.Lens && Lens.onState) { Lens.onState(boot); } else { boot(null, null); }
})();
</script>
</body>
</html>

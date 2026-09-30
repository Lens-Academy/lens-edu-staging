---
id: 'cb2623cb-591f-493c-a155-47ed32534af2'
title: "Week 5 Theory of Change Diagram Builder"
summary_for_tutor: "An interactive Theory of Change diagram for Week 5 of the Effective Thesis Accelerator. The learner fills in boxes in four columns, left to right: Research Outputs, Short-Term Outcomes (who uses the output and what changes), Long-Term Outcomes, and Ultimate Impact, and can add or remove boxes in each column. The saved summary lists every box by column, from outputs to impact. Useful for stress-testing weak links between steps, which often point to hidden assumptions."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root { --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df; --accent: #b87018; --soft: #faf8f3;
  --c1: #eef4fb; --c1b: #9bbbe0; --c2: #eef8f0; --c2b: #97c9a3; --c3: #fbf4e8; --c3b: #e0bb7c; --c4: #f6eefa; --c4b: #c19bd8; }
* { box-sizing: border-box; }
body { margin: 0; padding: 4px 0; font: 14px/1.5 "DM Sans", Arial, sans-serif; color: var(--text); background: #fff; }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin-bottom: 6px; }
.hint { color: var(--muted); font-size: 13px; margin: 0 0 12px; }
.flow { display: flex; align-items: stretch; gap: 0; overflow-x: auto; padding-bottom: 4px; }
.col { flex: 1 1 0; min-width: 180px; border-radius: 10px; padding: 10px; display: flex; flex-direction: column; gap: 8px; }
.col h3 { margin: 0; font-size: 13px; font-weight: 600; }
.col .q { margin: 0; font-size: 11.5px; color: var(--muted); line-height: 1.35; }
.arrow { flex: 0 0 28px; display: flex; align-items: center; justify-content: center; color: var(--muted); font-size: 20px; }
.card { background: #fff; border: 1px solid var(--border); border-radius: 8px; position: relative; }
.card textarea { width: 100%; min-height: 58px; border: none; resize: vertical; padding: 8px 26px 8px 8px; font: inherit; font-size: 13px; color: inherit; background: transparent; border-radius: 8px; }
.card textarea:focus { outline: 2px solid var(--accent); outline-offset: -2px; }
.card .x { position: absolute; top: 4px; right: 4px; border: none; background: transparent; color: var(--muted); cursor: pointer; font-size: 14px; line-height: 1; padding: 4px; border-radius: 4px; }
.card .x:hover { background: var(--soft); color: var(--text); }
.add { font: inherit; font-size: 12px; font-weight: 600; color: var(--accent); background: transparent; border: 1px dashed var(--accent); border-radius: 8px; padding: 6px 8px; cursor: pointer; }
.add:hover { background: #fff; }
.add:disabled { opacity: 0.5; cursor: default; }
.c1 { background: var(--c1); } .c1 .card { border-color: var(--c1b); }
.c2 { background: var(--c2); } .c2 .card { border-color: var(--c2b); }
.c3 { background: var(--c3); } .c3 .card { border-color: var(--c3b); }
.c4 { background: var(--c4); } .c4 .card { border-color: var(--c4b); }
.foot { margin-top: 10px; font-size: 12px; color: var(--muted); }
@media (max-width: 640px) {
  .flow { flex-direction: column; overflow-x: visible; }
  .col { min-width: 0; }
  .arrow { flex-basis: 28px; transform: rotate(90deg); }
}
</style>
</head>
<body>
<div class="eyebrow">My Theory of Change diagram</div>
<p class="hint">Build your diagram from left to right: your research outputs, which stakeholders use them and what changes (short-term), what that leads to (long-term), and the ultimate impact. Add as many boxes as you need, and your diagram saves automatically.</p>
<div class="flow" id="flow"></div>
<p class="foot">Tip: if a step feels like a big leap from the one before, that's often a hidden assumption, so add it to your Assumptions & Uncertainties table below!</p>
<script>
(function () {
  var COLS = [
    { k: "outputs", cls: "c1", title: "Research Outputs", q: "What will you tangibly produce? (e.g. report, policy brief, prototype)", ph: "e.g. A policy brief summarising my findings" },
    { k: "short", cls: "c2", title: "Short-Term Outcomes", q: "Who uses your output, and what decision or behaviour changes?", ph: "e.g. A think tank cites my findings in its recommendations" },
    { k: "long", cls: "c3", title: "Long-Term Outcomes", q: "What longer-term change follows, and for whom?", ph: "e.g. Policymakers adopt stronger regulation" },
    { k: "impact", cls: "c4", title: "Ultimate Impact", q: "What is your ultimate vision of a better world?", ph: "e.g. Fewer people harmed by..." }
  ];
  var MAX = 8, START = 2;
  var data = {};
  COLS.forEach(function (c) { data[c.k] = []; for (var i = 0; i < (c.k === "impact" ? 1 : START); i++) data[c.k].push(""); });
  var flow = document.getElementById("flow");

  function summary() {
    var parts = [];
    COLS.forEach(function (c) {
      var items = data[c.k].filter(function (t) { return /\S/.test(t); }).map(function (t) { return t.replace(/\s+/g, " ").slice(0, 160); });
      if (items.length) parts.push(c.title + ": " + items.join(" | "));
    });
    return parts.length ? "Theory of Change diagram, from outputs to impact. " + parts.join(". ") + "." : "Theory of Change diagram is still empty.";
  }
  function save() { if (window.Lens) window.Lens.saveState({ cols: data }, summary()); }

  function build() {
    flow.textContent = "";
    COLS.forEach(function (c, ci) {
      if (ci > 0) {
        var a = document.createElement("div"); a.className = "arrow"; a.setAttribute("aria-hidden", "true"); a.textContent = "\u2192";
        flow.appendChild(a);
      }
      var col = document.createElement("section");
      col.className = "col " + c.cls;
      col.setAttribute("aria-label", c.title);
      var h = document.createElement("h3"); h.textContent = c.title; col.appendChild(h);
      var q = document.createElement("p"); q.className = "q"; q.textContent = c.q; col.appendChild(q);
      data[c.k].forEach(function (txt, idx) {
        var card = document.createElement("div"); card.className = "card";
        var ta = document.createElement("textarea");
        ta.value = txt;
        if (idx === 0) ta.placeholder = c.ph;
        ta.setAttribute("aria-label", c.title + " box " + (idx + 1));
        ta.addEventListener("input", function () { data[c.k][idx] = ta.value; save(); });
        card.appendChild(ta);
        if (data[c.k].length > 1) {
          var x = document.createElement("button");
          x.type = "button"; x.className = "x"; x.textContent = "\u00d7";
          x.setAttribute("aria-label", "Remove " + c.title + " box " + (idx + 1));
          x.addEventListener("click", function () { data[c.k].splice(idx, 1); build(); save(); });
          card.appendChild(x);
        }
        col.appendChild(card);
      });
      var add = document.createElement("button");
      add.type = "button"; add.className = "add"; add.textContent = "+ Add box";
      add.setAttribute("aria-label", "Add a box to " + c.title);
      add.disabled = data[c.k].length >= MAX;
      add.addEventListener("click", function () {
        if (data[c.k].length >= MAX) return;
        data[c.k].push(""); build(); save();
        var tas = flow.querySelectorAll("section")[ci].querySelectorAll("textarea");
        if (tas.length) tas[tas.length - 1].focus();
      });
      col.appendChild(add);
      flow.appendChild(col);
    });
  }
  build();
  if (window.Lens) {
    window.Lens.onState(function (state) {
      if (state && state.cols) {
        COLS.forEach(function (c) {
          var arr = state.cols[c.k];
          if (Array.isArray(arr) && arr.length) data[c.k] = arr.slice(0, MAX).map(function (t) { return typeof t === "string" ? t : ""; });
        });
        build();
      }
    });
  }
})();
</script>
</body>
</html>

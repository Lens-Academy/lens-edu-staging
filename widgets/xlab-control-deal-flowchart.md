---
id: '2b6559a3-bc13-483b-8382-f6a23f66c90d'
title: The life of a deal
summary_for_tutor: "XLab's \"Build the flow chart\" exercise for the lesson on making deals with early schemers, rebuilt for Lens. The learner reconstructs the life cycle of a deal with an early schemer by placing blocks from a palette of ten into seven slots: four sequential steps, one decision, and the two endings the decision leads to. The correct chart is ask the AI whether it wants a deal, negotiate terms and make the earmarked escrow donation to the foundation, train the AI on documents about the deal so it holds in other contexts, have the AI perform while the lab stores weights and records, then after the AI transition stabilizes adjudicate retrospectively whether it held up its end; yes releases the donation to the AI and the foundation's trustees for non-harmful uses, no withholds it. Three palette blocks are distractors and belong nowhere: deleting the AI's weights once it is obsoleted (the foundation must keep them for adjudication), an enforcement suit in court (AIs are not legal persons, which is why the foundation exists), and paying out immediately before any verification (the point of escrow is that verification is delayed). The widget scores the finished chart out of seven slots and reports which blocks are misplaced, without naming the right answer. If the learner is stuck, ask what has to be stored for adjudication to be possible at all."
height: auto
tags: []
---
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
  --ok: #2f7d5d; --bad: #a8443c;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 4px; }
h3 { font-family: var(--font-ui); font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); font-weight: 500; margin: 18px 0 8px; }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
.card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--bg); }
.lede { color: var(--muted); margin: 4px 0 0; }
.chart { margin-top: 16px; }
.slot { width: 100%; text-align: left; border: 1px dashed var(--border); border-radius: 8px; background: var(--page);
        padding: 10px 12px; min-height: 52px; color: var(--muted); cursor: pointer; font: inherit; display: block; }
.slot:hover, .slot:focus-visible { border-color: var(--accent); color: var(--text); outline: none; }
.slot.filled { border-style: solid; border-color: var(--text); background: var(--bg); color: var(--text); }
.slot.decision { border-radius: 8px; border-left: 4px solid var(--accent); }
.slot.ok { border-color: var(--ok); box-shadow: inset 3px 0 0 var(--ok); }
.slot.bad { border-color: var(--bad); box-shadow: inset 3px 0 0 var(--bad); }
.slot .tag { display: block; font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); margin-bottom: 2px; }
.arrow { text-align: center; color: var(--muted); line-height: 1; margin: 6px 0; font-size: 16px; }
.branches { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-top: 6px; }
@media (max-width: 520px) { .branches { grid-template-columns: 1fr; } }
.branch-label { font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); margin-bottom: 4px; display: block; }
.palette { display: grid; gap: 8px; }
.block { width: 100%; text-align: left; border: 1px solid var(--border); border-radius: 8px; background: var(--bg);
         padding: 9px 12px; cursor: pointer; font: inherit; color: inherit; }
.block:hover { background: var(--page); }
.block.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
.block.used { opacity: 0.35; cursor: default; }
.block .kind { display: block; font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
.row { display: flex; gap: 10px; align-items: center; flex-wrap: wrap; margin-top: 16px; }
button.act { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); padding: 8px 12px; cursor: pointer; }
button.act:hover { background: var(--page); }
button.act.primary { border-color: var(--accent); color: #fff; background: var(--accent); }
button.act.primary:hover { background: var(--accent-hover); }
button.act[disabled] { opacity: 0.45; cursor: default; }
.status { margin-top: 14px; padding: 12px 14px; border: 1px solid var(--border); border-radius: 8px; background: var(--page); }
.status.hidden { display: none; }
.status ul { margin: 8px 0 0; padding-left: 18px; }
.hint { font-size: 12px; color: var(--muted); margin-top: 10px; }
.credit { font-size: 12px; color: var(--muted); margin-top: 12px; }
.desc { margin-top: 14px; border: 1px solid var(--border); border-radius: 8px; background: var(--page); padding: 10px 12px; }
.desc summary { cursor: pointer; color: var(--muted); }
.desc p { margin: 8px 0 0; }
</style>
</head>
<body>
<!-- Ported from XLab's "Build the flow chart" exercise on the AI Control track
     (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look. The block
     wording and the correct chart are XLab's. -->
<div class="card">
  <p class="eyebrow">Build the flow chart</p>
  <h2>The life of a deal</h2>
  <p class="lede">Reconstruct the life cycle of a deal with an early schemer, from first contact to what finally happens to the compensation. Pick a block, then pick the slot it belongs in. Some blocks do not belong in the chart at all.</p>

  <details class="desc">
    <summary>Show the description of the deal life cycle</summary>
    <p>AIs are unlikely to propose a negotiation on their own, so the lab has a policy of regularly asking its AIs about deals. Terms are negotiated, and the lab makes a donation to a foundation tasked with furthering the AI's interests, earmarked for this AI and mostly held in escrow. The AI is then, in consultation with the lab, trained on documents about the deal so that it knows about the deal in other contexts. The AI performs its side while the lab stores its weights and keeps records of its actions. After the transition to a world centered around AI has stabilized, much more powerful trusted models and interpretability tools adjudicate whether the AI cooperated. If it did, the AI and the foundation's trustees direct the donation toward uses that are not harmful; if it did not, the donation is not released.</p>
  </details>

  <div class="chart" id="chart"></div>

  <h3>Blocks</h3>
  <div class="palette" id="palette"></div>

  <div class="row">
    <button type="button" class="act primary" id="check">Check chart</button>
    <button type="button" class="act" id="reset">Reset</button>
    <span class="hint" id="progress"></span>
  </div>

  <div class="status hidden" id="status" aria-live="polite"></div>

  <p class="credit">Exercise and block wording after XLab's flow-chart builder for this lesson.</p>
</div>

<script>
(function () {
  "use strict";

  var BLOCKS = [
    { id: "ask", kind: "Step", label: "The lab asks the AI whether it wants to make a deal" },
    { id: "negotiate", kind: "Step", label: "Negotiate terms; the lab makes an earmarked donation to the foundation, mostly held in escrow" },
    { id: "train-docs", kind: "Step", label: "Train the AI on documents about the deal, so it knows about the deal in other contexts" },
    { id: "perform", kind: "Step", label: "The AI performs its side of the deal; the lab stores its weights, conversations, and records" },
    { id: "delete-weights", kind: "Step", label: "Delete the AI's weights once it is obsoleted" },
    { id: "adjudicate", kind: "Decision", label: "After the AI transition stabilizes, retrospective adjudication: did the AI hold up its end?" },
    { id: "court", kind: "Decision", label: "Does the AI win an enforcement suit against the lab in court?" },
    { id: "release", kind: "Ending", label: "The AI and the foundation's trustees direct the donation toward non-harmful uses" },
    { id: "withhold", kind: "Ending", label: "The donation is not released" },
    { id: "pay-now", kind: "Ending", label: "Release the donation to the AI immediately, before any verification" }
  ];

  var SLOTS = [
    { id: "s1", tag: "Step 1", accepts: "Step", answer: "ask" },
    { id: "s2", tag: "Step 2", accepts: "Step", answer: "negotiate" },
    { id: "s3", tag: "Step 3", accepts: "Step", answer: "train-docs" },
    { id: "s4", tag: "Step 4", accepts: "Step", answer: "perform" },
    { id: "d1", tag: "Decision", accepts: "Decision", answer: "adjudicate" },
    { id: "yes", tag: "If yes", accepts: "Ending", answer: "release", branch: "Yes" },
    { id: "no", tag: "If no", accepts: "Ending", answer: "withhold", branch: "No" }
  ];

  var placed = {};      // slotId -> blockId
  var selected = null;  // blockId
  var checked = false;

  function blockById(id) {
    for (var i = 0; i < BLOCKS.length; i++) if (BLOCKS[i].id === id) return BLOCKS[i];
    return null;
  }
  function usedBlockIds() {
    var out = {};
    for (var k in placed) out[placed[k]] = true;
    return out;
  }

  function makeSlotButton(slot) {
    var b = document.createElement("button");
    b.type = "button";
    b.className = "slot" + (slot.id === "d1" ? " decision" : "");
    b.id = "slot-" + slot.id;
    b.addEventListener("click", function () { onSlot(slot); });
    return b;
  }

  function buildChart() {
    var host = document.getElementById("chart");
    host.textContent = "";
    for (var i = 0; i < 5; i++) {
      host.appendChild(makeSlotButton(SLOTS[i]));
      var a = document.createElement("div");
      a.className = "arrow";
      a.textContent = "↓";
      host.appendChild(a);
    }
    var branches = document.createElement("div");
    branches.className = "branches";
    [SLOTS[5], SLOTS[6]].forEach(function (slot) {
      var wrap = document.createElement("div");
      var lab = document.createElement("span");
      lab.className = "branch-label";
      lab.textContent = slot.branch;
      wrap.appendChild(lab);
      wrap.appendChild(makeSlotButton(slot));
      branches.appendChild(wrap);
    });
    host.appendChild(branches);
  }

  function buildPalette() {
    var host = document.getElementById("palette");
    host.textContent = "";
    BLOCKS.forEach(function (blk) {
      var b = document.createElement("button");
      b.type = "button";
      b.className = "block";
      b.id = "block-" + blk.id;
      var kind = document.createElement("span");
      kind.className = "kind";
      kind.textContent = blk.kind;
      var lab = document.createElement("span");
      lab.textContent = blk.label;
      b.appendChild(kind);
      b.appendChild(lab);
      b.addEventListener("click", function () { onBlock(blk); });
      host.appendChild(b);
    });
  }

  function onBlock(blk) {
    if (usedBlockIds()[blk.id]) return;
    selected = (selected === blk.id) ? null : blk.id;
    checked = false;
    render();
  }

  function onSlot(slot) {
    if (placed[slot.id]) {
      // tapping a filled slot takes the block back out
      delete placed[slot.id];
    } else if (selected) {
      placed[slot.id] = selected;
      selected = null;
    }
    checked = false;
    render();
  }

  function render() {
    var used = usedBlockIds();

    SLOTS.forEach(function (slot) {
      var b = document.getElementById("slot-" + slot.id);
      b.textContent = "";
      var tag = document.createElement("span");
      tag.className = "tag";
      tag.textContent = slot.tag;
      b.appendChild(tag);
      var body = document.createElement("span");
      var blk = placed[slot.id] ? blockById(placed[slot.id]) : null;
      body.textContent = blk ? blk.label : (selected ? "Place the selected block here" : "Empty");
      b.appendChild(body);
      b.className = "slot" + (slot.id === "d1" ? " decision" : "") + (blk ? " filled" : "");
      if (checked && blk) b.className += (blk.id === slot.answer ? " ok" : " bad");
    });

    BLOCKS.forEach(function (blk) {
      var b = document.getElementById("block-" + blk.id);
      b.className = "block" + (used[blk.id] ? " used" : "") + (selected === blk.id ? " is-active" : "");
      b.disabled = !!used[blk.id];
    });

    var filled = Object.keys(placed).length;
    document.getElementById("progress").textContent = filled + " of " + SLOTS.length + " slots filled";
    document.getElementById("check").disabled = filled < SLOTS.length;

    if (!checked) document.getElementById("status").className = "status hidden";
    save();
  }

  function correctCount() {
    var n = 0;
    SLOTS.forEach(function (slot) { if (placed[slot.id] === slot.answer) n++; });
    return n;
  }

  function onCheck() {
    checked = true;
    var n = correctCount();
    var status = document.getElementById("status");
    status.textContent = "";
    status.className = "status";

    var head = document.createElement("strong");
    head.textContent = n + " of " + SLOTS.length + " slots are right.";
    status.appendChild(head);

    if (n === SLOTS.length) {
      var p = document.createElement("p");
      p.style.margin = "8px 0 0";
      p.textContent = "That is the chart. Verification is deliberately punted to the future: after the transition stabilizes, the lab will have far more powerful trusted models and interpretability tools, so it can adjudicate cooperation retrospectively, provided the weights and records were kept, which is why deleting the weights is wrong. The two other tempting blocks also fail for reasons the reading gives: the payout is meant to be conditional on validated cooperation (escrow until civilizational stability is generally preferable for AIs without high temporal discount rates), and the AI cannot sue because it is not a legal person, which is exactly why the foundation's trustees hold and direct the funds on its behalf.";
      status.appendChild(p);
      if (window.Lens && window.Lens.complete) window.Lens.complete();
    } else {
      var list = document.createElement("ul");
      SLOTS.forEach(function (slot) {
        if (placed[slot.id] !== slot.answer) {
          var li = document.createElement("li");
          li.textContent = slot.tag + ": that block does not belong there.";
          list.appendChild(li);
        }
      });
      status.appendChild(list);
      var hint = document.createElement("p");
      hint.style.margin = "8px 0 0";
      hint.style.color = "var(--muted)";
      hint.textContent = "Three of the ten blocks belong nowhere in the chart. Tap a filled slot to take its block back out.";
      status.appendChild(hint);
    }
    render();
    // render() hides the status when checked is false; it is true here, so restore it
    status.className = "status";
  }

  var saveTimer = null;
  function save() {
    if (!window.Lens || !window.Lens.saveState) return;
    if (saveTimer) clearTimeout(saveTimer);
    saveTimer = setTimeout(function () {
      var lines = SLOTS.map(function (slot) {
        var blk = placed[slot.id] ? blockById(placed[slot.id]) : null;
        return slot.tag + ": " + (blk ? blk.label : "empty");
      });
      var filled = Object.keys(placed).length;
      var summary = "Deal life-cycle flow chart, " + filled + " of " + SLOTS.length + " slots filled. " + lines.join(". ") + ". " +
        (checked ? ("Checked: " + correctCount() + " of " + SLOTS.length + " slots correct.") : "Not checked yet.");
      window.Lens.saveState({ v: 1, placed: placed, checked: checked }, summary);
    }, 400);
  }

  document.getElementById("check").addEventListener("click", onCheck);
  document.getElementById("reset").addEventListener("click", function () {
    placed = {};
    selected = null;
    checked = false;
    render();
  });

  buildChart();
  buildPalette();

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state) {
      if (state && state.placed) {
        placed = state.placed;
        checked = !!state.checked;
      }
      render();
      if (checked) onCheck();
    });
  } else {
    render();
  }
})();
</script>
</body>
</html>

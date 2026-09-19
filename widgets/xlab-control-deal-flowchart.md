---
id: '2b6559a3-bc13-483b-8382-f6a23f66c90d'
title: The life of a deal
summary_for_tutor: "XLab's \"Build the flow chart\" exercise for the lesson on making deals with early schemers, rebuilt for Lens. The learner reconstructs the life cycle of a deal with an early schemer by placing blocks from a palette of ten into seven slots: four sequential steps, one decision, and the two endings the decision leads to. The correct chart is ask the AI whether it wants a deal, negotiate terms and make the earmarked escrow donation to the foundation, train the AI on documents about the deal so it holds in other contexts, have the AI perform while the lab stores weights and records, then after the AI transition stabilizes adjudicate retrospectively whether it held up its end; yes releases the donation to the AI and the foundation's trustees for non-harmful uses, no withholds it. Three palette blocks are distractors and belong nowhere: deleting the AI's weights once it is obsoleted, an enforcement suit in court, and paying out immediately before any verification. Checking marks each filled slot right or wrong on the chart itself and gives a count out of seven; tapping a marked block then shows why that block does or does not fit there, and tapping it again takes it back out. The life cycle is not described inside the widget: the reading around it on the page carries it, in the vignette section above and in the sections on entering negotiations, knowing about the deal in other contexts, and delayed adjudication directly before the widget. The widget completes on the first check. If the learner is stuck, ask what has to be stored for adjudication to be possible at all."
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
.slot .why { display: block; margin-top: 6px; font-size: 12px; color: var(--muted); }
</style>
</head>
<body>
<!-- Ported from XLab's "Build the flow chart" exercise on the AI Control track
     (aisafetytracks.com), rebuilt as vanilla HTML/JS in the Lens look. The block
     wording and the correct chart are XLab's. -->
<div class="card">
  <p class="eyebrow">Build the flow chart</p>
  <h2>The life of a deal</h2>
  <p class="lede">Pick a block, then the slot it belongs in. Three of the ten blocks belong nowhere.</p>

  <div class="chart" id="chart"></div>

  <h3>Blocks</h3>
  <div class="palette" id="palette"></div>

  <div class="row">
    <button type="button" class="act primary" id="check">Check chart</button>
    <button type="button" class="act" id="reset">Reset</button>
    <span class="hint" id="progress"></span>
  </div>

  <div class="status hidden" id="status" aria-live="polite"></div>
</div>

<script>
(function () {
  "use strict";

  var BLOCKS = [
    { id: "ask", kind: "Step", label: "The lab asks the AI whether it wants to make a deal",
      why: "Deals open with the lab asking. An AI is unlikely to raise the subject on its own, so the lab needs a policy of asking its AIs regularly." },
    { id: "negotiate", kind: "Step", label: "Negotiate terms; the lab makes an earmarked donation to the foundation, mostly held in escrow",
      why: "Once the AI is interested, terms are agreed and the earmarked donation goes to the foundation, most of it into escrow." },
    { id: "train-docs", kind: "Step", label: "Train the AI on documents about the deal, so it knows about the deal in other contexts",
      why: "Training on documents about the deal is what carries it into the AI's other contexts, where it would otherwise have forgotten the negotiation." },
    { id: "perform", kind: "Step", label: "The AI performs its side of the deal; the lab stores its weights, conversations, and records",
      why: "While the AI holds up its end the lab stores weights, conversations and action records. Nothing can be adjudicated later without them." },
    { id: "delete-weights", kind: "Step", label: "Delete the AI's weights once it is obsoleted",
      why: "This belongs nowhere in the chart. Deleting the weights destroys exactly what adjudication needs, which is why the foundation has to keep them." },
    { id: "adjudicate", kind: "Decision", label: "After the AI transition stabilizes, retrospective adjudication: did the AI hold up its end?",
      why: "Verification is deliberately punted to the future. Once the transition has stabilized, far more powerful trusted models and interpretability tools can judge retrospectively what the AI did." },
    { id: "court", kind: "Decision", label: "Does the AI win an enforcement suit against the lab in court?",
      why: "This belongs nowhere in the chart. The AI is not a legal person and cannot sue, which is precisely why a foundation's trustees hold the money on its behalf." },
    { id: "release", kind: "Ending", label: "The AI and the foundation's trustees direct the donation toward non-harmful uses",
      why: "Validated cooperation is what unlocks the escrow, and the AI and the trustees then direct it toward uses that are not harmful." },
    { id: "withhold", kind: "Ending", label: "The donation is not released",
      why: "Without validated cooperation the escrow stays shut. That is the whole reason the payout is conditional." },
    { id: "pay-now", kind: "Ending", label: "Release the donation to the AI immediately, before any verification",
      why: "This belongs nowhere in the chart. Paying before verification gives up the only leverage escrow buys, and the escrow is generally preferable for AIs without high temporal discount rates." }
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
  var revealed = {};    // slotId -> true once its rationale has been opened
  var completed = false;

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
    revealed = {};
    render();
  }

  function onSlot(slot) {
    if (placed[slot.id]) {
      if (checked && !revealed[slot.id]) {
        // after a check, the first tap on a filled slot shows why that block does or does not fit
        revealed[slot.id] = true;
        render();
        return;
      }
      // tapping a filled slot takes the block back out
      delete placed[slot.id];
      delete revealed[slot.id];
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
      if (checked && blk && revealed[slot.id]) {
        var why = document.createElement("span");
        why.className = "why";
        why.textContent = (blk.id === slot.answer ? "Right. " : "Not here. ") + blk.why;
        b.appendChild(why);
      }
      b.className = "slot" + (slot.id === "d1" ? " decision" : "") + (blk ? " filled" : "");
      if (checked && blk) b.className += (blk.id === slot.answer ? " ok" : " bad");
      b.title = blk ? (checked && !revealed[slot.id] ? "Show why this block does or does not fit here" : "Take this block back out") : "Place the selected block here";
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
    var tail = document.createElement("span");
    tail.textContent = " Tap a block in the chart to see why it does or does not fit.";
    status.appendChild(tail);

    if (!completed) {
      completed = true;
      if (window.Lens && window.Lens.complete) window.Lens.complete();
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
      window.Lens.saveState({ v: 1, placed: placed, checked: checked, revealed: revealed }, summary);
    }, 400);
  }

  document.getElementById("check").addEventListener("click", onCheck);
  document.getElementById("reset").addEventListener("click", function () {
    placed = {};
    selected = null;
    checked = false;
    revealed = {};
    render();
  });

  buildChart();
  buildPalette();

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (state) {
      if (state && state.placed) {
        placed = state.placed;
        checked = !!state.checked;
        revealed = (state.revealed && typeof state.revealed === "object") ? state.revealed : {};
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

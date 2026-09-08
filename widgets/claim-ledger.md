---
id: '0f32c588-18c6-4ff6-9207-f02ed915947c'
title: Hardware opening puzzle
summary_for_tutor: "The opening puzzle of the hardware section, a claim ledger. Seven proposed conclusions a laboratory's 20,000 valid attestation tokens might support (genuine covered devices; certificates and configurations valid when checked; declared cluster topology; inference rather than prohibited training; cumulative training compute below the threshold; no unregistered accelerators ran a prohibited workload; the treaty authority can suspend the devices). For each, the learner picks one of three judgments: Supported, Possibly supported if the system was designed to measure it, or Unsupported by attestation alone. A judgment can be toggled off again. Pressing Keep your answers switches the ledger to a read-only What you recorded view; the same widget appears again at the end of the section (lesson 2.1.8, Return to the opening puzzle) where it shows what the learner recorded earlier and names any row left blank, and Change your answers reopens it. There is no answer key in the widget: the resolution is the closing prose of lesson 2.1.8. Do not give verdicts; if the learner asks about a claim, ask what the token actually measured. The widget is complete when the learner keeps a ledger with all seven rows judged."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Hardware opening puzzle</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "ClaimLedger" (reader component, set "hardware-opening", id "hw-opening-puzzle"). -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .head { display: flex; flex-wrap: wrap; align-items: baseline; justify-content: space-between; gap: 8px; }
  .count { font-size: 12px; color: var(--muted); margin: 0; }
  .lead { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 12px 0 0; }
  ol.rows { list-style: none; margin: 12px 0 0; padding: 0; display: grid; gap: 14px; }
  ol.rows > li { display: grid; gap: 8px; padding-top: 14px; border-top: 1px solid var(--border); }
  ol.rows > li:first-child { border-top: 0; padding-top: 0; }
  .claim { margin: 0; font-weight: 500; }
  .opts { display: flex; flex-wrap: wrap; gap: 8px; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .opt { display: inline-flex; align-items: baseline; gap: 6px; }
  .opt .tick { width: 1em; color: transparent; }
  .opt.is-selected { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); background: var(--surface); }
  .opt.is-selected .tick { color: var(--accent); }
  .recorded { margin: 0; color: var(--muted); }
  .recorded.is-blank { font-style: italic; }
  .recorded .tick { color: var(--accent); margin-right: 4px; }
  .foot { margin-top: 16px; padding-top: 14px; border-top: 1px solid var(--border); display: flex; flex-wrap: wrap; gap: 10px; align-items: center; justify-content: space-between; }
  .note { margin: 0; color: var(--muted); font-size: 12px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); border-color: var(--accent-hover); }
  .status { display: inline-flex; align-items: center; gap: 6px; font-size: 12px; font-weight: 500; }
  .status .tick { color: var(--accent); }
  @media (max-width: 420px) {
    body { padding: 12px; }
    .card { padding: 12px; }
    .opts { flex-direction: column; }
    .opt { width: 100%; }
  }
</style>
</head>
<body>
<section class="card" aria-labelledby="ledger-label">
  <div class="head">
    <p class="eyebrow" id="ledger-label">Your judgment</p>
    <p class="count" id="count"></p>
  </div>
  <p class="lead" id="lead"></p>
  <ol class="rows" id="rows"></ol>
  <div class="foot" id="foot"></div>
</section>

<script>
  // Data verbatim from src/lib/verification/data/hardware-opening-puzzle.ts (HARDWARE_OPENING_PUZZLE).
  var LEDGER = {
    lead: "Proposed conclusion",
    claims: [
      "These are genuine covered devices.",
      "Their certificates and approved configurations were valid when the evidence was checked.",
      "The devices were connected in the declared cluster topology.",
      "They performed inference rather than prohibited training.",
      "Their cumulative training compute remained below the treaty threshold.",
      "No unregistered accelerators ran a separate prohibited workload.",
      "The treaty authority can suspend the devices."
    ],
    options: [
      { id: "supported", text: "Supported" },
      { id: "possibly", text: "Possibly supported if the system was designed to measure it" },
      { id: "unsupported", text: "Unsupported by attestation alone" }
    ]
  };

  var STORE_KEY = "lens-claim-ledger-hw-opening-puzzle";
  var state = { marks: {}, kept: false };
  var completed = false;
  var hydrated = false;

  var labelEl = document.getElementById("ledger-label");
  var countEl = document.getElementById("count");
  var leadEl = document.getElementById("lead");
  var rowsEl = document.getElementById("rows");
  var footEl = document.getElementById("foot");

  function el(tag, className, text) {
    var node = document.createElement(tag);
    if (className) node.className = className;
    if (text !== undefined) node.textContent = text;
    return node;
  }

  function optionText(id) {
    for (var i = 0; i < LEDGER.options.length; i++) {
      if (LEDGER.options[i].id === id) return LEDGER.options[i].text;
    }
    return null;
  }

  function judgedCount() {
    var n = 0;
    for (var i = 0; i < LEDGER.claims.length; i++) if (optionText(state.marks[i])) n++;
    return n;
  }

  function summary() {
    var lines = [];
    lines.push(state.kept
      ? "The learner has kept their opening-puzzle judgments (" + judgedCount() + " of " + LEDGER.claims.length + " rows judged) and now sees the read-only What you recorded view."
      : "The learner is filling in the opening-puzzle ledger (" + judgedCount() + " of " + LEDGER.claims.length + " rows judged, not yet kept).");
    LEDGER.claims.forEach(function (claim, i) {
      var t = optionText(state.marks[i]);
      lines.push("\"" + claim + "\": " + (t ? t : "no judgment recorded") + ".");
    });
    return lines.join(" ");
  }

  function persist() {
    if (window.Lens) {
      Lens.saveState({ marks: state.marks, kept: state.kept }, summary());
      if (!completed && state.kept && judgedCount() === LEDGER.claims.length) {
        completed = true;
        Lens.complete();
      }
    } else {
      try { window.localStorage.setItem(STORE_KEY, JSON.stringify({ marks: state.marks, kept: state.kept })); } catch (e) { /* private mode */ }
    }
  }

  function choose(row, optionId) {
    if (state.kept) return;
    var next = {};
    for (var k in state.marks) if (Object.prototype.hasOwnProperty.call(state.marks, k)) next[k] = state.marks[k];
    if (next[row] === optionId) delete next[row];
    else next[row] = optionId;
    state.marks = next;
    render();
    persist();
  }

  function keep() {
    state.kept = true;
    render();
    persist();
  }

  function reopen() {
    state.kept = false;
    render();
    persist();
  }

  function render() {
    var kept = state.kept;
    labelEl.textContent = kept ? "What you recorded" : "Your judgment";
    countEl.textContent = judgedCount() + " of " + LEDGER.claims.length + " judged";
    leadEl.textContent = LEDGER.lead;

    rowsEl.textContent = "";
    LEDGER.claims.forEach(function (claim, row) {
      var li = el("li");
      li.appendChild(el("p", "claim", claim));
      var picked = state.marks[row];
      var pickedText = optionText(picked);

      if (kept) {
        if (pickedText) {
          var rec = el("p", "recorded");
          rec.appendChild(el("span", "tick", "✓"));
          rec.appendChild(el("span", null, pickedText));
          li.appendChild(rec);
        } else {
          li.appendChild(el("p", "recorded is-blank", "You did not record a judgment for this one."));
        }
      } else {
        var opts = el("div", "opts");
        LEDGER.options.forEach(function (option) {
          var selected = picked === option.id;
          var b = el("button", "opt" + (selected ? " is-selected" : ""));
          b.type = "button";
          b.setAttribute("aria-pressed", selected ? "true" : "false");
          b.appendChild(el("span", "tick", "✓"));
          b.appendChild(el("span", null, option.text));
          b.addEventListener("click", function () { choose(row, option.id); });
          opts.appendChild(b);
        });
        li.appendChild(opts);
      }
      rowsEl.appendChild(li);
    });

    footEl.textContent = "";
    if (kept) {
      var st = el("span", "status");
      st.appendChild(el("span", "tick", "✓"));
      st.appendChild(el("span", null, "Answers kept"));
      footEl.appendChild(st);
      var back = el("button", null, "Change your answers");
      back.type = "button";
      back.id = "reopen";
      back.addEventListener("click", reopen);
      footEl.appendChild(back);
    } else {
      footEl.appendChild(el("p", "note", "Keep your answers. You will return to them at the end of the section."));
      var kb = el("button", "primary", "Keep your answers");
      kb.type = "button";
      kb.id = "keep";
      kb.addEventListener("click", keep);
      footEl.appendChild(kb);
    }
  }

  function hydrate(saved, meta) {
    hydrated = true;
    if (saved && typeof saved === "object") {
      if (saved.marks && typeof saved.marks === "object") {
        var marks = {};
        for (var k in saved.marks) {
          if (Object.prototype.hasOwnProperty.call(saved.marks, k) && optionText(saved.marks[k])) marks[k] = saved.marks[k];
        }
        state.marks = marks;
      }
      state.kept = !!saved.kept;
    }
    completed = !!(meta && meta.completed);
    render();
  }

  if (window.Lens) {
    Lens.onState(hydrate);
    // If the platform never delivers state, still show an empty ledger.
    setTimeout(function () { if (!hydrated) render(); }, 2000);
  } else {
    var local = null;
    try { local = JSON.parse(window.localStorage.getItem(STORE_KEY) || "null"); } catch (e) { local = null; }
    hydrate(local, null);
  }
</script>
</body>
</html>

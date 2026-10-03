---
id: '9a4e2c7d-3b16-4f58-8d02-6e1c5a9b7f34'
title: Steelman, break, fix
summary_for_tutor: "A three-part critique exercise. The learner picks a verification mechanism (chip tracking, compute reporting, on-site inspections or remote attestation) and writes three short answers: the strongest case for it, one concrete way it fails, and a change that closes that failure. Each answer is scored separately by the assessor (0 to 100) with its own marking scheme; the fix is marked against the failure the learner themselves named. Their drafts and scores are in the widget-state block. Help them make the steelman specific to the mechanism, the failure concrete (who does what), and the fix honest about its cost. Do not write the answers for them."
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Steelman, break, fix</title>
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
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 26px; margin: 4px 0 8px; }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 2px; }
  .lede { color: var(--muted); margin: 0 0 16px; max-width: 42rem; }
  label { display: block; font-size: 12px; font-weight: 600; margin-bottom: 4px; }
  select, textarea {
    width: 100%; font: inherit; color: inherit; background: #fff;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  select:focus, textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  textarea { min-height: 84px; resize: vertical; }
  .pick { margin-bottom: 8px; max-width: 28rem; }
  .how { color: var(--muted); font-size: 12px; margin: 0 0 16px; max-width: 42rem; }
  .item { border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; background: var(--surface); margin-top: 12px; }
  .item .q { margin: 0 0 8px; }
  .item .note { color: var(--muted); font-size: 12px; margin: 0 0 8px; }
  .row { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; margin-top: 8px; }
  .status { font-size: 13px; flex: 1 1 12rem; }
  .status.is-score { font-weight: 600; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer;
  }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  .foot { margin-top: 14px; font-size: 13px; color: var(--muted); }
</style>
</head>
<body>
<p class="eyebrow">Exercise</p>
<h1>Steelman, break, fix</h1>
<p class="lede">Pick a verification mechanism. Then argue for it, find one concrete hole in it, and close the hole. Each answer is scored on its own; the third one is marked against the hole you named.</p>

<div class="pick">
  <label for="mechanism">Mechanism</label>
  <select id="mechanism"></select>
</div>
<p class="how" id="how"></p>

<div id="items"></div>
<p class="foot" id="foot"></p>

<script>
  var MECHANISMS = [
    { id: "chip-tracking", name: "chip tracking",
      how: "every advanced AI chip carries a registered ID and its owner reports where it is",
      guarantee: "where large amounts of compute physically are, and who holds them" },
    { id: "compute-reporting", name: "compute reporting",
      how: "labs declare how much compute each large training run used, and on which hardware",
      guarantee: "which training runs above a size threshold happened, and how big they were" },
    { id: "inspections", name: "on-site inspections",
      how: "inspectors visit data centres and check what hardware is present and what it is running",
      guarantee: "that a declared facility matches its declaration at the time of the visit" },
    { id: "attestation", name: "remote attestation",
      how: "the hardware itself signs a cryptographic statement of what code it is running",
      guarantee: "that a specific machine ran a specific program, without an inspector present" }
  ];

  // Three scorable items. Each has its own question and marking scheme; the
  // "fix" item builds its scheme from the learner's own "failure" answer.
  var ITEMS = [
    {
      key: "steelman", title: "1. Steelman it",
      question: function (m) { return "Make the strongest case for " + m.name + " as a verification mechanism."; },
      instructions: function (m) {
        return "Score 0 to 100. Full marks when the answer says what an outside party can establish with " + m.name +
          " (namely: " + m.guarantee + "), gives at least one concrete reason it is hard to evade, and is specific to this mechanism" +
          " rather than to verification in general. Take 30 off when it never says what is being verified, 30 off when every point" +
          " would apply equally to any mechanism, and 20 off when it is shorter than two sentences.";
      },
      feedback: "Say which part of the case is strongest, then name the one claim a skeptic would attack first. Do not write the case for the learner.",
      ready: function () { return true; }
    },
    {
      key: "failure", title: "2. Break it",
      question: function (m) { return "Name one concrete way " + m.name + " fails or can be evaded."; },
      instructions: function (m) {
        return "Score 0 to 100. The mechanism works like this: " + m.how + ". Full marks when the failure depends on how this mechanism" +
          " works, says who does what to defeat it, and is plausible in practice. Score at most 40 when the failure is generic" +
          " (\"it could be hacked\", \"people could lie\") with no mechanism-specific detail. Score at most 60 when it is specific" +
          " but the actor or the step that defeats the mechanism is missing.";
      },
      feedback: "Tell the learner whether the failure is really specific to this mechanism, then ask what evidence an inspector or auditor would need to detect it.",
      ready: function () { return true; }
    },
    {
      key: "fix", title: "3. Fix it",
      question: function (m, s) {
        return "Propose a change to " + m.name + " that closes this failure: “" + (s.texts.failure || "").trim() + "”";
      },
      instructions: function (m, s) {
        return "Score 0 to 100. The learner earlier named this failure of " + m.name + ": \"" + (s.texts.failure || "").trim() + "\"." +
          " Full marks when the proposed change directly addresses that failure (not a different one), says concretely what changes" +
          " in how the mechanism works, and admits one cost or new weakness the change introduces. Score at most 30 when the fix" +
          " addresses a different failure than the one quoted. Take 25 off when no cost or new weakness is acknowledged.";
      },
      feedback: "Judge whether the fix closes the quoted failure or a different one, then ask what an adversary would try next against the patched mechanism.",
      ready: function (s) { return !!(s.texts.failure || "").trim(); }
    }
  ];

  var state = { mechanism: MECHANISMS[0].id, texts: {}, results: {} };
  var completed = false;
  var busy = {};
  var ui = {};

  var select = document.getElementById("mechanism");
  var how = document.getElementById("how");
  var itemsEl = document.getElementById("items");
  var foot = document.getElementById("foot");

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function mech() { for (var i = 0; i < MECHANISMS.length; i++) if (MECHANISMS[i].id === state.mechanism) return MECHANISMS[i]; return MECHANISMS[0]; }
  function scoredCount() { var n = 0; ITEMS.forEach(function (it) { if (state.results[it.key]) n++; }); return n; }

  MECHANISMS.forEach(function (m) {
    var o = el("option", "", m.name.charAt(0).toUpperCase() + m.name.slice(1));
    o.value = m.id;
    select.appendChild(o);
  });

  ITEMS.forEach(function (it) {
    var card = el("div", "item");
    card.setAttribute("data-item", it.key);
    card.appendChild(el("h2", "", it.title));
    var q = el("p", "q");
    var note = el("p", "note");
    var ta = el("textarea"); ta.setAttribute("aria-label", it.title); ta.id = "text-" + it.key;
    var row = el("div", "row");
    var status = el("span", "status"); status.id = "status-" + it.key;
    var score = el("button", "primary", "Score this answer"); score.type = "button"; score.id = "score-" + it.key;
    var fb = el("button", "", "Get feedback"); fb.type = "button"; fb.id = "feedback-" + it.key; fb.hidden = true;
    row.appendChild(status); row.appendChild(score); row.appendChild(fb);
    card.appendChild(q); card.appendChild(note); card.appendChild(ta); card.appendChild(row);
    itemsEl.appendChild(card);
    ui[it.key] = { q: q, note: note, ta: ta, status: status, score: score, fb: fb };

    ta.addEventListener("input", function () { state.texts[it.key] = ta.value; render(); persist(); });
    score.addEventListener("click", function () { submit(it); });
    fb.addEventListener("click", function () {
      var r = state.results[it.key];
      if (!window.Lens || !r) return;
      Lens.requestFeedback(r.responseId, "Can I get feedback on my “" + it.title.replace(/^\d+\.\s*/, "") + "” answer?");
    });
  });

  function summary() {
    var m = mech();
    var lines = ["Mechanism: " + m.name];
    ITEMS.forEach(function (it) {
      var v = (state.texts[it.key] || "").trim();
      var r = state.results[it.key];
      lines.push(it.title + ": " + (v || "(empty)") + (r ? " [scored " + (r.score == null ? "pending" : r.score + "/100") + "]" : ""));
    });
    lines.push("Scored: " + scoredCount() + " of " + ITEMS.length + ".");
    return lines.join("\n");
  }

  function persist() {
    if (!window.Lens) return;
    Lens.saveState({ mechanism: state.mechanism, texts: state.texts, results: state.results }, summary());
    if (!completed && scoredCount() === ITEMS.length) {
      completed = true;
      Lens.complete();
    }
  }

  function render() {
    var m = mech();
    how.textContent = "How it works: " + m.how + ".";
    ITEMS.forEach(function (it) {
      var u = ui[it.key];
      var text = (state.texts[it.key] || "").trim();
      var ready = it.ready(state);
      var r = state.results[it.key];
      u.q.textContent = it.question(m, state);
      u.note.textContent = ready ? "" : "Write your answer to 2 first; this one is marked against it.";
      if (u.ta.value !== (state.texts[it.key] || "")) u.ta.value = state.texts[it.key] || "";
      u.ta.disabled = !ready;
      u.score.disabled = !ready || !text || !!busy[it.key];
      u.score.textContent = r ? "Score again" : "Score this answer";
      if (busy[it.key]) {
        u.status.textContent = "Scoring…"; u.status.className = "status";
      } else if (r) {
        u.status.textContent = r.score == null ? "Scoring is taking a while; ask for feedback meanwhile." : "Score: " + r.score + " / 100";
        u.status.className = r.score == null ? "status" : "status is-score";
      } else {
        u.status.textContent = ""; u.status.className = "status";
      }
      u.fb.hidden = !r;
    });
    foot.textContent = scoredCount() === ITEMS.length
      ? "All three scored. Change any answer and score it again, or ask the tutor for feedback on one."
      : scoredCount() + " of " + ITEMS.length + " answers scored.";
  }

  function submit(it) {
    if (!window.Lens || !Lens.submit || busy[it.key]) return;
    var m = mech();
    busy[it.key] = true;
    render();
    Lens.submit({
      item: it.key,
      question: it.question(m, state),
      answer: (state.texts[it.key] || "").trim(),
      assessmentInstructions: it.instructions(m, state),
      feedbackInstructions: it.feedback
    }).then(function (result) {
      busy[it.key] = false;
      state.results[it.key] = { responseId: result.responseId, score: result.score };
      render();
      persist();
    }, function () {
      busy[it.key] = false;
      render();
      ui[it.key].status.textContent = "Could not score this answer right now.";
    });
  }

  select.addEventListener("change", function () {
    state.mechanism = select.value;
    state.results = {}; // scores were for the old questions
    render();
    persist();
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.mechanism === "string" && MECHANISMS.some(function (m) { return m.id === saved.mechanism; })) state.mechanism = saved.mechanism;
      if (saved.texts && typeof saved.texts === "object") {
        ITEMS.forEach(function (it) { var v = saved.texts[it.key]; if (typeof v === "string") state.texts[it.key] = v; });
      }
      if (saved.results && typeof saved.results === "object") {
        ITEMS.forEach(function (it) {
          var r = saved.results[it.key];
          if (r && typeof r === "object" && typeof r.responseId === "number") {
            state.results[it.key] = { responseId: r.responseId, score: typeof r.score === "number" ? r.score : null };
          }
        });
      }
    }
    completed = !!(meta && meta.completed);
    select.value = state.mechanism;
    render();
  }

  select.value = state.mechanism;
  render();
  if (window.Lens) { Lens.onState(hydrate); }
</script>
</body>
</html>

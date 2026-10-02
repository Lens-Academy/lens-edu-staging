---
id: '88b4e3bf-1ed7-4872-9800-9c576f559ae8'
title: "Your report card: Unit 1"
height: auto
summary_for_tutor: "The learner's daily report card for Unit 1 (Plan) of Lens Projects. Each entry is one work day: date, what they did, what they decided and why, how they used AI (tick boxes) with a one-sentence disclosure line, which part they did themselves as practice, hours, what they are stuck on (optional), their next step, and an optional reflection on this unit's prompts (Why this, why now, why me? What would make this project a waste of time?). Their entries are saved and shown to you in the widget-state block. A Get feedback button asks you to read all their Unit 1 entries. The widget is complete once one full entry is saved. Unit 1 goals: choose a track; agree the AI policy (use AI as a tool, not a decision-maker); look at earlier projects; build a theory of change; write the proposal canvas. Never fill in entries for them."
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Your report card: Unit 1</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10; --warn: #9a3412;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 26px; margin: 4px 0 8px; }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 19px; margin: 0 0 6px; }
  .lede { color: var(--muted); margin: 0 0 14px; max-width: 42rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 14px; }
  .card + .card { margin-top: 14px; }
  .field { margin-top: 12px; }
  .field:first-child { margin-top: 0; }
  label, .legend { display: block; font-size: 13px; font-weight: 600; margin-bottom: 2px; }
  .req { color: var(--accent); font-weight: 600; }
  .cue { font-size: 12px; color: var(--muted); margin: 0 0 6px; }
  input[type=text], input[type=date], input[type=number], textarea {
    width: 100%; font: inherit; color: inherit; background: #fff;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  input[type=number] { max-width: 8rem; }
  input[type=date] { max-width: 12rem; }
  input:focus, textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  textarea { min-height: 64px; resize: vertical; }
  .checks { display: block; }
  .checks label { display: flex; gap: 8px; align-items: flex-start; font-weight: 400; font-size: 13px; margin: 4px 0; }
  .checks input { margin-top: 3px; }
  .rule { margin: 0 0 8px; padding: 8px 10px; font-size: 12px; color: var(--muted); background: var(--surface); border-left: 3px solid var(--accent); border-radius: 4px; }
  .prompts { margin: 0 0 6px; padding-left: 18px; font-size: 12px; color: var(--muted); }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer;
  }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  .row { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; margin-top: 14px; }
  .msg { font-size: 12px; color: var(--warn); margin: 8px 0 0; }
  .ok { font-size: 12px; color: var(--muted); margin: 8px 0 0; }
  .entry { border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: var(--surface); }
  .entry + .entry { margin-top: 10px; }
  .entry-head { display: flex; flex-wrap: wrap; justify-content: space-between; gap: 6px; font-weight: 600; font-size: 13px; }
  .entry p { margin: 4px 0 0; font-size: 13px; }
  .entry .k { color: var(--muted); }
  .entry .acts { display: flex; gap: 6px; }
  .entry .acts button { padding: 3px 8px; font-size: 12px; }
  .empty { font-size: 13px; color: var(--muted); }
  .fb-out { margin: 10px 0 0; padding: 10px 12px; border: 1px solid var(--border); border-radius: 8px; background: #fff; font-size: 13px; }
  .fb-out p { margin: 0 0 6px; }
</style>
</head>
<body>
<p class="eyebrow">Unit 1: Plan</p>
<h1>Your report card</h1>
<p class="lede">Log each day you work on your project. It takes two minutes, and it shows you, your review partner and your group what actually happened, not what you meant to do. Be honest: a day where you got stuck is worth logging too. You need at least one full entry to finish this unit.</p>

<div class="card" id="form">
  <h2 id="form-title">New entry</h2>
  <div class="field">
    <label for="f-date">Date</label>
    <input id="f-date" type="date">
  </div>
  <div class="field">
    <label for="f-did">What I did <span class="req">*</span></label>
    <p class="cue">What did you actually do today? Name the things you made, read, or talked to someone about.</p>
    <textarea id="f-did"></textarea>
  </div>
  <div class="field">
    <label for="f-decided">What I decided, and why <span class="req">*</span></label>
    <p class="cue">What did you decide today, and what was it based on? "Nothing yet" is a fine answer on some days.</p>
    <textarea id="f-decided"></textarea>
  </div>
  <div class="field">
    <span class="legend">How I used AI <span class="req">*</span></span>
    <p class="rule">Course rule: use AI as a tool, not a decision-maker. If AI made a decision for you today, say so here. That is useful to notice, not a mark against you.</p>
    <div class="checks" id="f-ai"></div>
  </div>
  <div class="field" id="disc-field">
    <label for="f-disc">AI disclosure line <span class="req">*</span></label>
    <p class="cue">One sentence, the way it would appear on your project card. Example: "AI helped write the plotting code and red-team my claims; the question, analysis and writing are mine."</p>
    <input id="f-disc" type="text">
  </div>
  <div class="field">
    <label for="f-practice">Practice: what I did myself <span class="req">*</span></label>
    <p class="cue">Which part of today did you do yourself, to build your skill?</p>
    <textarea id="f-practice"></textarea>
  </div>
  <div class="field">
    <label for="f-hours">Hours <span class="req">*</span></label>
    <p class="cue">Roughly how many hours today?</p>
    <input id="f-hours" type="number" min="0" max="24" step="0.25">
  </div>
  <div class="field">
    <label for="f-stuck">Stuck on, or need help with</label>
    <textarea id="f-stuck"></textarea>
  </div>
  <div class="field">
    <label for="f-next">Next step <span class="req">*</span></label>
    <p class="cue">The very next thing you will do. Small enough to start in one sitting.</p>
    <input id="f-next" type="text">
  </div>
  <div class="field">
    <label for="f-reflect">Reflection (optional)</label>
    <ul class="prompts" id="prompts"></ul>
    <textarea id="f-reflect"></textarea>
  </div>
  <div class="row">
    <button type="button" class="primary" id="save">Save entry</button>
    <button type="button" id="cancel" hidden>Cancel editing</button>
  </div>
  <p class="msg" id="msg" hidden></p>
</div>

<div class="card">
  <h2>Your entries</h2>
  <div id="list"></div>
</div>

<div class="card">
  <h2>Feedback</h2>
  <p class="cue">Ask the tutor to read this unit's entries: whether your work matches the unit's goals, any decision that looks like it came from AI rather than from you, and whether your next step is small enough.</p>
  <button type="button" id="fb">Get feedback</button>
  <p class="ok" id="fb-hint"></p>
  <div class="fb-out" id="fb-out" hidden></div>
</div>

<script>
  var UNIT = "Unit 1: Plan";
  var UNIT_GOALS = "choose a track; agree the AI use policy (use AI as a tool, not a decision-maker); browse a gallery of potential projects; build a theory of change; write the proposal canvas";
  var PROMPTS = ["Why this, why now, why me?", "What would make this project a waste of time?"];
  var AI_USES = ["Didn't use AI today", "Writing or fixing code", "Finding or summarising sources", "Red-teaming my plan or draft", "Editing for clarity", "Other"];
  var NO_AI = AI_USES[0];
  var STORE_KEY = "lens-widget-lens-projects-report-card-u1";

  var state = { entries: [] };
  var editing = -1;
  var completed = false;
  var busy = false;

  function $(id) { return document.getElementById(id); }
  function el(tag, cls, text) { var n = document.createElement(tag); if (cls) n.className = cls; if (text !== undefined) n.textContent = text; return n; }
  function today() { var d = new Date(); var m = String(d.getMonth() + 1).padStart(2, "0"); var day = String(d.getDate()).padStart(2, "0"); return d.getFullYear() + "-" + m + "-" + day; }

  PROMPTS.forEach(function (p) { $("prompts").appendChild(el("li", null, p)); });
  AI_USES.forEach(function (u, i) {
    var lab = el("label");
    var box = document.createElement("input");
    box.type = "checkbox"; box.value = u; box.id = "ai-" + i;
    box.addEventListener("change", function () {
      if (u === NO_AI && box.checked) { aiBoxes().forEach(function (b) { if (b.value !== NO_AI) b.checked = false; }); }
      if (u !== NO_AI && box.checked) { aiBoxes()[0].checked = false; }
      syncDisc();
    });
    lab.appendChild(box); lab.appendChild(document.createTextNode(u));
    $("f-ai").appendChild(lab);
  });
  function aiBoxes() { return Array.prototype.slice.call($("f-ai").querySelectorAll("input")); }
  function aiPicked() { return aiBoxes().filter(function (b) { return b.checked; }).map(function (b) { return b.value; }); }
  function usedAI() { var p = aiPicked(); return p.length > 0 && p.indexOf(NO_AI) === -1; }
  function syncDisc() { $("disc-field").hidden = !usedAI(); }

  function readForm() {
    return {
      date: $("f-date").value || today(),
      did: $("f-did").value.trim(),
      decided: $("f-decided").value.trim(),
      ai: aiPicked(),
      disclosure: usedAI() ? $("f-disc").value.trim() : "",
      practice: $("f-practice").value.trim(),
      hours: $("f-hours").value,
      stuck: $("f-stuck").value.trim(),
      next: $("f-next").value.trim(),
      reflect: $("f-reflect").value.trim()
    };
  }
  function missing(e) {
    var m = [];
    if (!e.did) m.push("What I did");
    if (!e.decided) m.push("What I decided");
    if (!e.ai.length) m.push("How I used AI");
    if (usedAI() && !e.disclosure) m.push("AI disclosure line");
    if (!e.practice) m.push("Practice");
    if (e.hours === "" || isNaN(Number(e.hours))) m.push("Hours");
    if (!e.next) m.push("Next step");
    return m;
  }
  function fillForm(e) {
    $("f-date").value = e ? e.date : today();
    $("f-did").value = e ? e.did : "";
    $("f-decided").value = e ? e.decided : "";
    aiBoxes().forEach(function (b) { b.checked = !!(e && e.ai.indexOf(b.value) !== -1); });
    $("f-disc").value = e ? (e.disclosure || "") : "";
    $("f-practice").value = e ? e.practice : "";
    $("f-hours").value = e ? e.hours : "";
    $("f-stuck").value = e ? (e.stuck || "") : "";
    $("f-next").value = e ? e.next : "";
    $("f-reflect").value = e ? (e.reflect || "") : "";
    syncDisc();
    $("form-title").textContent = e ? "Edit entry" : "New entry";
    $("cancel").hidden = !e;
  }

  function summary() {
    if (!state.entries.length) return UNIT + " report card: no entries yet.";
    var lines = [UNIT + " report card, " + state.entries.length + " entr" + (state.entries.length === 1 ? "y" : "ies") + ":"];
    state.entries.forEach(function (e) {
      lines.push(e.date + ". Did: " + e.did + " Decided: " + e.decided + " AI: " + e.ai.join(", ") + (e.disclosure ? " (" + e.disclosure + ")" : "") + ". Practice: " + e.practice + ". Hours: " + e.hours + "." + (e.stuck ? " Stuck: " + e.stuck + "." : "") + " Next: " + e.next + "." + (e.reflect ? " Reflection: " + e.reflect : ""));
    });
    return lines.join("\n");
  }

  function persist() {
    if (window.Lens) {
      Lens.saveState({ entries: state.entries }, summary());
      if (!completed && state.entries.length > 0) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORE_KEY, JSON.stringify({ entries: state.entries })); } catch (err) {}
    }
  }

  function line(k, v) { var p = el("p"); p.appendChild(el("span", "k", k + ": ")); p.appendChild(document.createTextNode(v)); return p; }
  function renderList() {
    var list = $("list");
    while (list.firstChild) list.removeChild(list.firstChild);
    if (!state.entries.length) { list.appendChild(el("p", "empty", "No entries yet. Your first one finishes this page.")); }
    var order = state.entries.map(function (e, i) { return i; }).sort(function (a, b) { return state.entries[b].date < state.entries[a].date ? -1 : 1; });
    order.forEach(function (i) {
      var e = state.entries[i];
      var card = el("div", "entry");
      var head = el("div", "entry-head");
      head.appendChild(el("span", null, e.date + " · " + e.hours + " h"));
      var acts = el("span", "acts");
      var ed = el("button", null, "Edit"); ed.type = "button";
      ed.addEventListener("click", function () { editing = i; fillForm(e); $("form").scrollIntoView({ block: "start" }); });
      var del = el("button", null, "Delete"); del.type = "button";
      del.addEventListener("click", function () { state.entries.splice(i, 1); if (editing === i) { editing = -1; fillForm(null); } persist(); renderList(); });
      acts.appendChild(ed); acts.appendChild(del); head.appendChild(acts);
      card.appendChild(head);
      card.appendChild(line("Did", e.did));
      card.appendChild(line("Decided", e.decided));
      card.appendChild(line("AI", e.ai.join(", ") + (e.disclosure ? ". " + e.disclosure : "")));
      card.appendChild(line("Practice", e.practice));
      if (e.stuck) card.appendChild(line("Stuck on", e.stuck));
      card.appendChild(line("Next", e.next));
      if (e.reflect) card.appendChild(line("Reflection", e.reflect));
      list.appendChild(card);
    });
    $("fb").disabled = busy || !state.entries.length || !window.Lens;
    $("fb-hint").textContent = !window.Lens ? "Feedback needs the Lens lesson page; it is not available in this preview." : (!state.entries.length ? "Save an entry first." : "");
  }

  $("save").addEventListener("click", function () {
    var e = readForm();
    var m = missing(e);
    if (m.length) { $("msg").hidden = false; $("msg").textContent = "Still needed: " + m.join(", ") + "."; return; }
    $("msg").hidden = true;
    if (editing >= 0) { state.entries[editing] = e; } else { state.entries.push(e); }
    editing = -1;
    fillForm(null);
    persist();
    renderList();
  });
  $("cancel").addEventListener("click", function () { editing = -1; fillForm(null); $("msg").hidden = true; });

  $("fb").addEventListener("click", function () {
    if (busy || !window.Lens || !Lens.submit || !state.entries.length) return;
    busy = true; $("fb").disabled = true; $("fb").textContent = "Reading your entries...";
    var out = $("fb-out"); out.hidden = false; while (out.firstChild) out.removeChild(out.firstChild);
    out.appendChild(el("p", null, "Sent. Waiting for the read of your report card."));
    Lens.submit({
      item: "report-card-u1",
      question: "Daily report card for " + UNIT + " of Lens Projects. Unit goals: " + UNIT_GOALS + ".",
      answer: summary(),
      assessmentInstructions: "Practice score only; the learner is not shown it. 100 when every entry names concrete things done and decided, with the reasoning, an honest AI line, and a next step small enough for one sitting. Take about 15 off per entry that is vague.",
      feedbackInstructions: "Read the learner's report card entries for this unit as a whole. In under 150 words, comment on three things: whether what they did matches the goals of this unit; any day where the decision or the reasoning looks like it came from AI rather than from them (quote the entry, ask one question, do not accuse); and whether their next step is small and concrete enough to do in one sitting. If the log shows the same blocker on two or more days, name it and suggest they bring it to the next meeting. No generic praise. Do not mention any score."
    }).then(function (result) {
      if (Lens.requestFeedback && result.responseId != null) Lens.requestFeedback(result.responseId, "Can you read my report card for this unit?");
      while (out.firstChild) out.removeChild(out.firstChild);
      out.appendChild(el("p", null, "Your feedback is being written in the tutor conversation beside this page."));
      busy = false; $("fb").textContent = "Get feedback again"; renderList();
    }, function () {
      while (out.firstChild) out.removeChild(out.firstChild);
      out.appendChild(el("p", null, "Could not reach the tutor just now. Your entries are saved; try again in a moment."));
      busy = false; $("fb").textContent = "Get feedback"; renderList();
    });
  });

  function hydrate(saved, meta) {
    if (saved && Array.isArray(saved.entries)) state.entries = saved.entries.filter(function (e) { return e && typeof e === "object"; });
    completed = !!(meta && meta.completed);
    renderList();
  }

  fillForm(null);
  renderList();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null, saved = null;
    try { raw = localStorage.getItem(STORE_KEY); } catch (err) {}
    if (raw) { try { saved = JSON.parse(raw); } catch (err) {} }
    hydrate(saved, null);
  }
</script>
</body>
</html>

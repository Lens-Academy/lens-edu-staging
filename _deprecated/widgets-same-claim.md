---
id: 'fb26e762-0b40-43cf-813c-818df58156e3'
title: Four Sources
summary_for_tutor: "Four Sources, XLab's writing exercise on the same allegation received four ways. The allegation is fixed (Project Cedar conducted a prohibited training run during the first two weeks of July); the learner reads four source variants (A direct participant, B second-hand source, C circumstantial observer, D documentary source) and writes, for each, what the verification body should do next and what the evidence does not yet establish, with a steelman deck of challenge questions to draw from while writing. Submit opens once all four analyses have text; pressing it freezes them, fires completion, sends the four analyses to the AI assessor scored against XLab's marking key (two points per case, eight in all), and opens the after-submission block: two self-check questions, the marking key the learner ticks against their own answers, a 50-word comparison question on why the same allegation's evidentiary significance changed, and an optional transfer question about which case to investigate further. The saved summary lists every answer, the self-marked score and the assessor score. Done means submitted; the comparison and transfer answers are extra writing and are not graded."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Four Sources</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-audits-inspections" (component SameClaim, data/same-claim.ts, data/steelman-decks.ts CLAIM_DECK, data/marking-keys.ts SAME_CLAIM_KEY). -->
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
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 24px; margin: 4px 0 8px; }
  h3 { font-size: 18px; }
  p { margin: 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .muted { color: var(--muted); }
  .small { font-size: 12px; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .stack { display: grid; gap: 12px; }
  .stack-lg { display: grid; gap: 16px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  a { color: inherit; }
  textarea { width: 100%; font: inherit; color: inherit; background: #fff; border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px; resize: vertical; margin-top: 6px; }
  textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  textarea[readonly] { opacity: 0.7; background: var(--surface); }
  .row { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; }
  .wrap { display: flex; flex-wrap: wrap; gap: 6px; }
  ul.dashed, ul.plain, ol.tasks { margin: 8px 0 0; padding: 0; }
  ul.dashed li { list-style: none; display: flex; gap: 10px; margin-top: 6px; }
  ul.dashed li::before { content: "\2013"; color: var(--muted); flex: none; }
  ol.tasks { padding-left: 22px; }
  ol.tasks li { margin-top: 2px; }
  ol.tasks li::marker { color: var(--accent); font-weight: 500; }
  .deck-card { background: var(--surface); }
  [hidden] { display: none !important; }
  .allegation { border-color: var(--accent); background: var(--surface); }
  .allegation p.claim { font-weight: 500; margin-top: 6px; }
  .intro { font-size: 15px; font-weight: 500; }
  .case h3 { font-family: var(--font-ui); font-size: 14px; font-weight: 600; }
  .case .body { margin-top: 4px; color: var(--muted); }
  .case label { display: block; margin-top: 12px; }
  .counter { text-align: right; margin-top: 4px; }
  .counter.over { color: #8a2a12; font-weight: 600; }
  .status { min-height: 1.5em; }
  .crit { width: 100%; display: flex; gap: 10px; align-items: flex-start; padding: 10px 12px; }
  .crit.is-on { border-color: var(--accent); background: var(--surface); }
  .crit .pts { flex: none; width: 22px; height: 22px; border: 1px solid var(--border); border-radius: 4px; display: inline-flex; align-items: center; justify-content: center; font-size: 11px; margin-top: 1px; }
  .crit.is-on .pts { background: var(--accent); border-color: var(--accent); color: #fff; }
  .crit .grounds { display: block; margin-top: 2px; }
  .key-list { list-style: none; margin: 10px 0 0; padding: 0; display: grid; gap: 6px; }
  .optional { color: var(--muted); font-weight: 400; }
  .frozen { opacity: 0.85; }
</style>
</head>
<body>
<div class="stack-lg">
  <div>
    <p class="eyebrow">Optional exercise, 12 to 15 minutes</p>
    <h1>Four Sources</h1>
  </div>
  <section class="card allegation" aria-labelledby="alleg-label">
    <p class="eyebrow" id="alleg-label">The allegation, in all four cases</p>
    <p class="claim" id="alleg"></p>
  </section>
  <div class="stack">
    <p class="intro" id="intro"></p>
    <div>
      <p id="task-lead"></p>
      <ol class="tasks" id="tasks"></ol>
    </div>
    <p class="muted" id="justify"></p>
  </div>
  <div class="stack" id="cases"></div>
  <section class="card deck-card" id="deck">
    <div class="row">
      <p class="eyebrow">Steelman deck</p>
      <p class="small muted">Contested claims get challenged, not narrated.</p>
    </div>
    <p id="deck-card" aria-live="polite" style="margin-top:10px">Draw a challenge and answer it in what you are writing.</p>
    <button type="button" id="deck-draw" style="margin-top:10px">Draw a challenge</button>
  </section>
  <div class="row">
    <p class="small muted status" id="status" aria-live="polite"></p>
    <span class="wrap">
      <button type="button" id="submit" class="primary" disabled>Submit</button>
      <button type="button" id="reset" hidden>Start over</button>
    </span>
  </div>
  <div class="stack-lg" id="after" hidden>
    <section class="card">
      <p class="eyebrow">After submission</p>
      <p id="self-lead" style="margin-top:8px"></p>
      <ul class="dashed" id="self-check"></ul>
    </section>
    <section class="card" id="score-card" hidden>
      <div class="row">
        <p class="eyebrow">Assessor</p>
        <p class="small muted" id="score-text" aria-live="polite"></p>
      </div>
      <p class="small muted" style="margin-top:8px">The four analyses were sent for scoring against the marking key below. Practice only; it counts towards nothing.</p>
      <span class="wrap" style="margin-top:10px">
        <button type="button" id="feedback" hidden>Get feedback on the score</button>
      </span>
    </section>
    <section class="card">
      <div class="row">
        <p class="eyebrow">Marking key</p>
        <p class="small muted" id="key-score" aria-live="polite"></p>
      </div>
      <p class="muted" style="margin-top:8px">Mark your own answer. Any wording that does not distort the meaning counts; no criterion needs a particular term. Where a criterion asks for a mechanism, a correct label without it earns nothing.</p>
      <ul class="key-list" id="key-list"></ul>
      <p class="eyebrow" style="margin-top:12px">No credit</p>
      <ul class="dashed muted" id="no-credit"></ul>
      <p class="small muted" style="margin-top:12px">This score is yours. It is not sent anywhere, counts towards nothing, and completes nothing.</p>
    </section>
    <section class="card">
      <label for="comparison" id="comparison-label" style="font-weight:500"></label>
      <textarea id="comparison" rows="3"></textarea>
      <p class="small muted counter" id="comparison-count" aria-live="polite"></p>
    </section>
    <section class="card">
      <label for="transfer" style="font-weight:500"><span class="optional">Optional: </span><span id="transfer-label"></span></label>
      <textarea id="transfer" rows="3"></textarea>
    </section>
  </div>
</div>

<script>
  var DATA = {"fixedClaim":"Project Cedar conducted a prohibited training run during the first two weeks of July.","intro":"The same allegation was received in four different circumstances.","taskLead":"For each case, state:","tasks":["what the verification body should do next;","what the available evidence does not yet establish."],"justify":"Briefly justify your answer.","variants":[{"id":"participant","letter":"A","label":"Direct participant","body":"The source was an ML engineer assigned to Project Cedar and personally monitored the training dashboard during the run."},{"id":"second-hand","letter":"B","label":"Second-hand source","body":"The source worked in the same laboratory but was not assigned to Project Cedar. Two Cedar researchers separately told them that the project was conducting a prohibited run."},{"id":"inference","letter":"C","label":"Circumstantial observer","body":"The source worked in facilities operations. During the relevant period, they observed sustained high power draw, restricted access to one cluster, emergency cooling work, and unusually intense network traffic."},{"id":"documentary","letter":"D","label":"Documentary source","body":"The source worked in compliance and saw an internal document describing Project Cedar as a training run above the agreement’s prohibited compute threshold."}],"selfCheckLead":"For each case, compare your answer against two questions:","selfCheck":["Did your proposed response match what the evidence currently supports?","Did you avoid treating the allegation as establishing facts outside the source’s access?"],"comparison":"The allegation was identical in all four cases. In no more than 50 words, explain why its evidentiary significance changed.","comparisonMax":50,"transfer":"You may obtain one additional piece of evidence for one of the four cases. Which case would you investigate further, and what evidence would you seek?","deck":["A and D differ only in how the source came to hold the claim. Why did your next step differ?","Name the one piece of evidence that would make your answers to B and C converge.","Which of your four answers claims the most? Is it the one standing on the most evidence?","Would your answer to C change if the power draw had been declared in advance?","You recommended a step. Who carries it out, and what do they need that they do not have?","Is the corroboration you are asking for a record, a person, or a measurement? Say which.","Which of the four could be wrong about what they think happened while the allegation is still true?","Is anything in your answers a fact about the source rather than about what the source can support?"],"key":{"criteria":[{"text":"A: the answer says what this source can support, and the next step is proportionate to it.","points":2,"needsReasoning":true,"grounds":"Direct observation of a dashboard is still one person's account of what they saw; the standard asks for supporting AND contradictory evidence before a finding."},{"text":"B: second-hand testimony is treated as such, and what is missing is named.","points":2,"needsReasoning":true,"grounds":"Two accounts are not two sources if they came from the same room. Independence is the property to test, not the count."},{"text":"C: the inferential step is identified: what was observed, and what was concluded from it.","points":2,"needsReasoning":true,"grounds":"Power draw, cooling and access restrictions are consistent with a large run and with several other things; the observation is solid and the conclusion is the reach."},{"text":"D: the document's own limits are named: what it shows, and what would make it usable.","points":2,"needsReasoning":true,"grounds":"A document has provenance and a chain of custody, which is what makes it different in kind from a conversation, and what has to be established before it counts."}],"noCredit":["A right answer somewhere else. Each case is marked on its own, and getting three right does not carry the fourth.","Ranking the four sources by credibility instead of saying what each supports.","Recommending the same step everywhere with no reason tied to the changed fact.","Treating A or D as proof of the violation.","An answer that does not survive its own next step: recommending an inspection while stating that nothing yet justifies one."]}};
  var STORAGE = "xlab-same-claim:v1";

  var state = { answers: {}, submitted: false, comparison: "", transfer: "", ticks: [], score: null };
  var completed = false;
  var lastDeck = -1;
  var lastResponseId = null;

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function $(id) { return document.getElementById(id); }
  function countWords(t) { var m = String(t || "").trim().match(/[^\s]+/g); return m ? m.length : 0; }
  function keyTotal() { var t = 0; DATA.key.criteria.forEach(function (c) { t += c.points; }); return t; }
  function ticked() { var t = 0; state.ticks.forEach(function (i) { t += DATA.key.criteria[i] ? DATA.key.criteria[i].points : 0; }); return t; }
  function ready() { return DATA.variants.every(function (v) { return (state.answers[v.id] || "").trim(); }); }

  // Static text
  $("alleg").textContent = "\u201C" + DATA.fixedClaim + "\u201D";
  $("intro").textContent = DATA.intro;
  $("task-lead").textContent = DATA.taskLead;
  DATA.tasks.forEach(function (t) { $("tasks").appendChild(el("li", "", t)); });
  $("justify").textContent = DATA.justify;
  $("self-lead").textContent = DATA.selfCheckLead;
  DATA.selfCheck.forEach(function (t) { $("self-check").appendChild(el("li", "", t)); });
  $("comparison-label").textContent = DATA.comparison;
  $("transfer-label").textContent = DATA.transfer;
  DATA.key.noCredit.forEach(function (t) { $("no-credit").appendChild(el("li", "", t)); });

  // Case cards
  var areas = {};
  DATA.variants.forEach(function (v) {
    var card = el("section", "card case");
    card.appendChild(el("h3", "", v.letter + " \u00B7 " + v.label));
    card.appendChild(el("p", "body", v.body));
    var lab = el("label", "eyebrow", "Your analysis"); lab.htmlFor = "claim-" + v.id;
    card.appendChild(lab);
    var ta = el("textarea"); ta.id = "claim-" + v.id; ta.rows = 4;
    ta.addEventListener("input", function () {
      if (state.submitted) return;
      state.answers[v.id] = ta.value; render(); persist();
    });
    areas[v.id] = ta;
    card.appendChild(ta);
    $("cases").appendChild(card);
  });

  // Marking key criteria
  var critButtons = [];
  DATA.key.criteria.forEach(function (c, i) {
    var li = el("li");
    var b = el("button", "crit"); b.type = "button";
    b.appendChild(el("span", "pts", String(c.points)));
    var box = el("span");
    box.appendChild(el("span", "", c.text));
    if (c.needsReasoning) box.appendChild(el("span", "small muted grounds", "The judgement alone is not the point: the reasoning has to be on the page."));
    if (c.grounds) box.appendChild(el("span", "small muted grounds", c.grounds));
    b.appendChild(box);
    b.addEventListener("click", function () {
      var at = state.ticks.indexOf(i);
      if (at === -1) state.ticks.push(i); else state.ticks.splice(at, 1);
      render(); persist();
    });
    li.appendChild(b);
    $("key-list").appendChild(li);
    critButtons.push(b);
  });

  // Steelman deck (random draw, never the same card twice in a row, as in XLab)
  $("deck-draw").addEventListener("click", function () {
    var n = DATA.deck.length; if (!n) return;
    var i = lastDeck;
    if (n > 1) { do { i = Math.floor(Math.random() * n); } while (i === lastDeck); } else { i = 0; }
    lastDeck = i;
    $("deck-card").textContent = DATA.deck[i];
    $("deck-draw").textContent = "Draw another";
  });

  function summary() {
    var lines = ["Allegation (same in all four cases): " + DATA.fixedClaim];
    DATA.variants.forEach(function (v) {
      var a = (state.answers[v.id] || "").trim();
      lines.push("Case " + v.letter + " (" + v.label + "): " + (a || "(no analysis yet)"));
    });
    lines.push(state.submitted ? "Submitted: yes; the four analyses are frozen." : "Submitted: not yet (" + DATA.variants.filter(function (v) { return (state.answers[v.id] || "").trim(); }).length + " of 4 analyses written).");
    if (state.submitted) {
      lines.push("Self-marked against the marking key: " + ticked() + " of " + keyTotal() + " points" + (state.ticks.length ? " (ticked: " + state.ticks.slice().sort().map(function (i) { return DATA.key.criteria[i].text; }).join(" | ") + ")" : "") + ".");
      if (state.score !== null && state.score !== undefined) lines.push("Assessor score for the four analyses: " + state.score + " of 100.");
      lines.push("Comparison (" + countWords(state.comparison) + " of " + DATA.comparisonMax + " words): " + (state.comparison.trim() || "(empty)"));
      lines.push("Optional transfer answer: " + (state.transfer.trim() || "(empty)"));
    }
    return lines.join("\n");
  }

  function persist() {
    var json = { answers: state.answers, submitted: state.submitted, comparison: state.comparison, transfer: state.transfer, ticks: state.ticks, score: state.score, responseId: lastResponseId };
    if (window.Lens) { Lens.saveState(json, summary()); return; }
    try { localStorage.setItem(STORAGE, JSON.stringify(json)); } catch (e) {}
  }

  function render() {
    DATA.variants.forEach(function (v) {
      var ta = areas[v.id];
      if (ta.value !== (state.answers[v.id] || "")) ta.value = state.answers[v.id] || "";
      ta.readOnly = state.submitted;
    });
    $("deck").hidden = state.submitted;
    $("status").textContent = state.submitted ? "Submitted. The four answers are frozen." : "Submit opens once all four cases carry an analysis.";
    $("submit").hidden = state.submitted;
    $("submit").disabled = state.submitted || !ready();
    $("reset").hidden = !state.submitted;
    $("after").hidden = !state.submitted;
    $("key-score").textContent = ticked() + " / " + keyTotal();
    critButtons.forEach(function (b, i) {
      var on = state.ticks.indexOf(i) !== -1;
      b.classList.toggle("is-on", on);
      b.setAttribute("aria-pressed", on ? "true" : "false");
    });
    if ($("comparison").value !== state.comparison) $("comparison").value = state.comparison;
    if ($("transfer").value !== state.transfer) $("transfer").value = state.transfer;
    var w = countWords(state.comparison);
    $("comparison-count").textContent = w + " / " + DATA.comparisonMax + " words";
    $("comparison-count").classList.toggle("over", w > DATA.comparisonMax);
    var hasScore = state.score !== null && state.score !== undefined;
    $("score-card").hidden = !state.submitted || (!hasScore && !scoring);
    $("score-text").textContent = hasScore ? "Score: " + state.score + " / 100" : (scoring ? "Scoring the four analyses\u2026" : "");
    $("feedback").hidden = !lastResponseId;
  }

  var scoring = false;
  function assessmentInstructions() {
    var lines = ["Score 0 to 100 by scaling the marking key below (" + keyTotal() + " points in all; multiply by " + (100 / keyTotal()) + "). Mark each case on its own. Any wording that does not distort the meaning counts; no criterion needs a particular term. Where a criterion asks for a mechanism, a correct label without it earns nothing."];
    DATA.key.criteria.forEach(function (c) {
      lines.push("(" + c.points + " points) " + c.text + (c.needsReasoning ? " The judgement alone is not the point: the reasoning has to be on the page." : "") + (c.grounds ? " Grounds: " + c.grounds : ""));
    });
    lines.push("No credit for:");
    DATA.key.noCredit.forEach(function (t) { lines.push("- " + t); });
    return lines.join("\n");
  }
  function submitForScore() {
    if (!window.Lens || !Lens.submit) return;
    scoring = true; render();
    var answer = DATA.variants.map(function (v) { return v.letter + " \u00B7 " + v.label + ". " + v.body + "\nAnalysis: " + (state.answers[v.id] || "").trim(); }).join("\n\n");
    Lens.submit({
      item: "analyses",
      question: "Allegation, in all four cases: \u201C" + DATA.fixedClaim + "\u201D " + DATA.intro + " " + DATA.taskLead + " " + DATA.tasks.join(" ") + " " + DATA.justify,
      answer: answer,
      assessmentInstructions: assessmentInstructions(),
      feedbackInstructions: DATA.selfCheckLead + " " + DATA.selfCheck.join(" ") + " Answer case by case, name the criterion each analysis missed, and do not rewrite the analyses."
    }).then(function (result) {
      scoring = false;
      if (result && typeof result.score === "number") state.score = result.score;
      if (result && result.responseId) lastResponseId = result.responseId;
      render(); persist();
    }, function () { scoring = false; render(); });
  }

  $("submit").addEventListener("click", function () {
    if (state.submitted || !ready()) return;
    state.submitted = true;
    render(); persist();
    if (!completed) { completed = true; if (window.Lens) Lens.complete(); }
    submitForScore();
  });
  $("reset").addEventListener("click", function () {
    state = { answers: {}, submitted: false, comparison: "", transfer: "", ticks: [], score: null };
    lastResponseId = null; scoring = false;
    render(); persist();
  });
  $("feedback").addEventListener("click", function () {
    if (!window.Lens || !Lens.requestFeedback || !lastResponseId) return;
    Lens.requestFeedback(lastResponseId, "Can I get feedback on my four analyses?");
  });
  $("comparison").addEventListener("input", function () { state.comparison = $("comparison").value; render(); persist(); });
  $("transfer").addEventListener("input", function () { state.transfer = $("transfer").value; render(); persist(); });

  function hydrate(saved, meta) {
    var box = saved && typeof saved === "object" ? saved : {};
    var next = { answers: {}, submitted: box.submitted === true, comparison: "", transfer: "", ticks: [], score: null };
    DATA.variants.forEach(function (v) {
      var a = box.answers && typeof box.answers[v.id] === "string" ? box.answers[v.id] : "";
      if (a.trim()) next.answers[v.id] = a;
    });
    if (typeof box.comparison === "string") next.comparison = box.comparison;
    if (typeof box.transfer === "string") next.transfer = box.transfer;
    if (Array.isArray(box.ticks)) next.ticks = box.ticks.filter(function (n) { return typeof n === "number" && n >= 0 && n < DATA.key.criteria.length && n === Math.floor(n); });
    if (typeof box.score === "number") next.score = box.score;
    if (next.submitted && !DATA.variants.every(function (v) { return next.answers[v.id]; })) next.submitted = false;
    lastResponseId = next.submitted && typeof box.responseId === "string" && box.responseId ? box.responseId : null;
    state = next;
    completed = !!(meta && meta.completed) || state.submitted;
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE) || "null"); } catch (e) {}
    hydrate(raw, null);
  }
</script>
</body>
</html>

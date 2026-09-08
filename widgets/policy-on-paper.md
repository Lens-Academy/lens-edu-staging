---
id: '3ebda770-5816-4384-bf62-835bed72e1ea'
title: Companies A and B
summary_for_tutor: "Companies A and B, XLab's provenance-tagging exercise on two real reporting regimes. Three tabs: Company A (six statements about a published noncompliance-reporting and anti-retaliation policy plus an outside index grade), Company B (six statements about non-disparagement agreements, equity at risk, a regulator complaint, an index grade and the 2024 retraction) and The demands (four asks from the Right to Warn letter with one written question, what satisfying them would change structurally). On each company tab the learner marks every statement as one of five kinds of claim (Published rule, Company self-report, Documented prior practice, External assessment, Not established) and presses Commit; the commit reveals the authored kind for each row, says what the learner marked where it differs, and shows XLab's note. Below the tabs sit a steelman deck of challenge questions and two workspace questions with Save answer buttons (what institutional incentives the rules create; what further evidence would show the institution is independent, competent and usable), and a covered Sources panel that names the companies (A is Anthropic, B is OpenAI) with links. Done means all three tabs committed; nothing is graded, the saved summary lists every mark against its authored kind and every written answer, and the widget never shuffles because the statements are authored in a mixed order and the same five options apply to every row."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Companies A and B</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-institutions-judgment" (component PolicyOnPaper, data/policy-on-paper.ts, data/steelman-decks.ts INSTITUTION_DECK, kit question-workspace, spoiler, steelman-deck). -->
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
  .tabs { display: flex; flex-wrap: wrap; gap: 8px; }
  .tab { border-radius: 999px; padding: 6px 14px; font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
  .tab[aria-selected="true"] { background: var(--text); border-color: var(--text); color: #fff; }
  .tab[aria-selected="true"]:hover { background: var(--text); }
  .mark { padding: 4px 10px; font-size: 12px; border-radius: 6px; }
  .mark[aria-pressed="true"] { border-color: var(--accent); background: var(--surface); font-weight: 600; box-shadow: 0 0 0 1px var(--accent); }
  .result { display: flex; gap: 6px; align-items: baseline; font-size: 12px; letter-spacing: 0.02em; margin-top: 12px; }
  .result .glyph { flex: none; width: 18px; height: 18px; border-radius: 50%; border: 1px solid currentColor; display: inline-flex; align-items: center; justify-content: center; font-size: 11px; }
  .result.right { color: #4a5a1a; }
  .result.wrong { color: #8a2a12; }
  .note { margin-top: 6px; color: var(--muted); }
  .demand { font-size: 14px; }
  .qhead { display: flex; flex-wrap: wrap; justify-content: space-between; gap: 6px; align-items: baseline; }
  .spoiler-body { position: relative; margin-top: 10px; }
  .veil { width: 100%; padding: 26px 12px; text-align: center; background: var(--surface); }
  .veil span { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
  .link { background: none; border: none; padding: 0; font-size: 12px; color: var(--muted); text-decoration: underline; text-underline-offset: 3px; cursor: pointer; }
  .link:hover { background: none; color: var(--text); }
  ul.sources { list-style: none; margin: 0; padding: 0; display: grid; gap: 12px; }
  ul.cites { margin: 4px 0 0; padding-left: 18px; }
  ul.cites li { font-size: 12px; margin-top: 2px; }
  ul.cites a { color: var(--muted); text-decoration: none; }
  ul.cites a:hover { text-decoration: underline; }
  .right-text { text-align: right; }
</style>
</head>
<body>
<div class="stack-lg">
  <div>
    <p class="eyebrow">Exercise, 15 to 20 minutes</p>
    <h1>Companies A and B</h1>
  </div>
  <p id="lead"></p>
  <p id="instruction"></p>
  <div class="tabs" role="tablist" aria-label="Regime" id="tabs"></div>
  <div id="panels"></div>
  <section class="card deck-card" id="deck">
    <div class="row">
      <p class="eyebrow">Steelman deck</p>
      <p class="small muted">Contested claims get challenged, not narrated.</p>
    </div>
    <p id="deck-card" aria-live="polite" style="margin-top:10px">Draw a challenge and answer it in what you are writing.</p>
    <button type="button" id="deck-draw" style="margin-top:10px">Draw a challenge</button>
  </section>
  <div class="stack-lg" id="workspace">
    <p class="small muted right-text" id="ws-count" aria-live="polite"></p>
  </div>
  <section class="card">
    <div class="row">
      <p style="font-weight:600">Sources</p>
      <p class="small muted" id="spoiler-hint">Which tab was which.</p>
      <button type="button" class="link" id="spoiler-hide" hidden>Hide</button>
    </div>
    <div class="spoiler-body">
      <button type="button" class="veil" id="spoiler-open" aria-label="Uncover the sources, and which company each tab was"><span>Press to uncover</span></button>
      <ul class="sources" id="sources" hidden></ul>
    </div>
  </section>
</div>

<script>
  var DATA = {"provenance":[{"id":"published-rule","label":"Published rule","hint":"written down in a policy the company published"},{"id":"self-report","label":"Company self-report","hint":"the company’s own account of what it does or did"},{"id":"prior-practice","label":"Documented prior practice","hint":"what was reported to have actually happened"},{"id":"external-assessment","label":"External assessment","hint":"somebody outside the company judging it"},{"id":"not-established","label":"Not established","hint":"nobody has shown this either way"}],"companies":[{"id":"a","label":"Company A","statements":[{"id":"a-anon","group":"published","text":"Reports may be filed anonymously through an independent third-party platform.","kind":"published-rule","note":""},{"id":"a-unmask","group":"published","text":"The company states that it cannot identify a reporter who uses the anonymous channel.","kind":"self-report","note":"Two sentences from one document, a few lines apart, and not the same kind of claim. That a channel is permitted is a rule the company wrote. That the company is unable to unmask somebody using it is an assertion about its own systems, and nobody outside has tested it."},{"id":"a-informal","group":"published","text":"An informal conversation with a senior leader is not a report and triggers no investigation, until either the employee files one through a named channel or that leader confirms they have filed one on the employee’s behalf.","kind":"published-rule","note":"A published rule can still be the gap: this one decides which conversations exist on the record. It has two ways out and the burden of both is on the employee: file it yourself, or be told the leader did."},{"id":"a-external","group":"published","text":"Nothing in the policy prohibits reporting potential violations of law to government authorities, and doing so is protected from retaliation.","kind":"published-rule","note":""},{"id":"a-grade","group":"context","text":"An outside index scored this company highest of nine assessed firms on governance and accountability: a B, against an overall grade of C+.","kind":"external-assessment","note":"Highest of nine is a ranking, not a pass, and it is one domain of an index whose leader it grades C+ overall."},{"id":"a-usage","group":"unverified","text":"How many reports the channel receives, and how they are resolved.","kind":"not-established","note":"The index scores four things about governance here (protection, track record, policy quality, policy transparency), and none of them is this. The policy does not report it either, so nobody outside the company can say whether the channel is used."}]},{"id":"b","label":"Company B","statements":[{"id":"b-nda","group":"context","text":"A departing employee signed a lifetime ban on criticising the company.","kind":"prior-practice","note":""},{"id":"b-secret","group":"context","text":"The existence of that agreement was itself covered by an NDA: admitting it existed was already a breach.","kind":"prior-practice","note":""},{"id":"b-equity","group":"context","text":"Refusing to sign, or breaching, put every share of vested equity the employee had earned at risk.","kind":"prior-practice","note":""},{"id":"b-sec","group":"context","text":"Whistleblowers filed a complaint with the securities regulator, alleging that the agreements required employees to waive their federal right to a whistleblower award and barred them from giving information to federal authorities without the company’s permission.","kind":"prior-practice","note":"What happened, and is documented, is the filing. What the complaint says happened is an allegation inside it, which no regulator has ruled on. Marking the allegation as practice is the error 2.4.3 spends ten minutes on (evidence of a claim is not evidence that the claim is true), so the row states the filing and leaves the allegation as its content."},{"id":"b-grade","group":"context","text":"An outside index graded this company C on governance and accountability (second of the nine it assessed, behind a single B), and none of its recommendations to the company concerns reporting channels at all.","kind":"external-assessment","note":"Tab B is otherwise all documented practice, which is why this row is here: it is the one judgement on it from outside. What the index does not say is part of the row: four recommendations about other things is not the same as having examined the channel and approved of it."},{"id":"b-retracted","group":"context","text":"After it became public in May 2024, the company withdrew the non-disparagement agreements and said it would not cancel anyone’s vested equity.","kind":"self-report","note":"The compulsory row. A 2024 rule presented as still in force is an error, not strictness, and the retraction is still the company’s account of its own conduct, which is a different kind of evidence from the agreements themselves."}]}],"demands":{"id":"d","label":"The demands","demands":[{"id":"d-nodisparage","text":"No agreement that forbids risk-related criticism, and no withholding of earned payments for making it."},{"id":"d-anon","text":"A verifiably anonymous channel to the board, to regulators, and to an independent organization with relevant expertise."},{"id":"d-public","text":"A right to raise risk concerns publicly, so long as trade secrets are protected."},{"id":"d-noretaliation","text":"No retaliation for public disclosure once the other channels have failed."}],"question":"If these were satisfied, what would that change structurally?"},"task":{"lead":"Now, apply everything you have learned to an exercise with two organizations, A and B, where you will categorize provisions, articulate the incentives each set of rules creates, brainstorm additional evidence pipelines to quality-check the reporting institution, and steelman the points you make throughout.","instruction":"Every statement below concerns the reporting regime of one of two organisations, A or B, or is a demand made by employees of those organisations. Determine what kind of claim each statement is. Commit each set, then answer the two questions that follow."},"questions":[{"id":"incentives","n":1,"title":"What underlying institutional incentives do these rules create?"},{"id":"evidence","n":2,"title":"What additional evidence would be needed to conclude that this reporting institution is independent, competent, and usable?"}],"sources":[{"id":"a","label":"Company A","realName":"Anthropic","realNote":"","cites":[{"label":"Anthropic, RSP Noncompliance Reporting and Anti-Retaliation Policy (PDF)","href":"https://www-cdn.anthropic.com/b7a5629e40b391b2adfb4cc8c0888ac9d6bfddf6/RSP%20Noncompliance%20Reporting%20and%20Anti-Retaliation%20Policy.pdf"},{"label":"Future of Life Institute, AI Safety Index, Summer 2026","href":"https://futureoflife.org/ai-safety-index-summer-2026/"}]},{"id":"b","label":"Company B","realName":"OpenAI","realNote":"","cites":[{"label":"The OpenAI Files, “Transparency and Safety”, collecting Vox (18 May 2024) and the Washington Post (13 July 2024)","href":"https://www.openaifiles.org/transparency-and-safety"},{"label":"Future of Life Institute, AI Safety Index, Summer 2026","href":"https://futureoflife.org/ai-safety-index-summer-2026/"},{"label":"CNBC, “OpenAI sends internal memo releasing former employees from non-disparagement agreements”, 24 May 2024","href":"https://www.cnbc.com/2024/05/24/openai-sends-internal-memo-releasing-former-employees-from-non-disparagement-agreements-sam-altman.html"}]},{"id":"d","label":"The demands","realName":"“A Right to Warn about Advanced Artificial Intelligence”","realNote":"An open letter of 4 June 2024, signed by thirteen current and former employees of OpenAI and Google DeepMind (seven named, six anonymous), and endorsed by Yoshua Bengio, Geoffrey Hinton and Stuart Russell.","cites":[{"label":"The letter in full, with its signatories and endorsers","href":"https://righttowarn.ai/"}]}],"deck":["You named an incentive. Who exactly faces it: the reporter, their manager, or the company?","If the rule you are worried about were deleted tomorrow, what would change in practice?","Which of your claims is about what is written down, and which about what happens? Fence them apart.","Name the evidence that would change your mind about this institution being usable.","Would your answer survive if the company published its report numbers and they were high?","Is your objection about independence, about competence, or about usability? Each is a different repair.","What would the company say in one sentence in reply, and is it wrong?","Which of your points applies to both regimes, and is therefore not a difference between them?"]};
  var STORAGE = "xlab-policy-on-paper:v1";
  var TAB_IDS = DATA.companies.map(function (c) { return c.id; }).concat([DATA.demands.id]);
  var KINDS = DATA.provenance.map(function (p) { return p.id; });
  var ALL = [];
  DATA.companies.forEach(function (c) { c.statements.forEach(function (s) { ALL.push(s); }); });

  var state = { marks: {}, committed: [], demandAnswer: "", notes: { answers: {}, done: {} } };
  var tab = DATA.companies[0].id;
  var completed = false;
  var lastDeck = -1;
  var uncovered = false;

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function $(id) { return document.getElementById(id); }
  function provLabel(id) { for (var i = 0; i < DATA.provenance.length; i++) if (DATA.provenance[i].id === id) return DATA.provenance[i].label; return null; }
  function isCommitted(id) { return state.committed.indexOf(id) !== -1; }
  function finished() { return TAB_IDS.every(isCommitted); }

  $("lead").textContent = DATA.task.lead;
  $("instruction").textContent = DATA.task.instruction;

  // Tabs
  var tabButtons = {};
  DATA.companies.concat([DATA.demands]).forEach(function (c) {
    var b = el("button", "tab"); b.type = "button"; b.setAttribute("role", "tab"); b.id = "tab-" + c.id;
    b.addEventListener("click", function () { tab = c.id; render(); });
    tabButtons[c.id] = b;
    $("tabs").appendChild(b);
  });

  // Company panels
  var rowNodes = {};
  var panelNodes = {};
  DATA.companies.forEach(function (c) {
    var panel = el("div", "stack"); panel.setAttribute("role", "tabpanel"); panel.setAttribute("aria-labelledby", "tab-" + c.id);
    c.statements.forEach(function (s) {
      var card = el("section", "card");
      card.appendChild(el("p", "", s.text));
      var choices = el("div", "wrap"); choices.style.marginTop = "12px";
      var btns = {};
      DATA.provenance.forEach(function (p) {
        var b = el("button", "mark", p.label); b.type = "button"; b.title = p.hint;
        b.addEventListener("click", function () {
          if (isCommitted(c.id)) return;
          state.marks[s.id] = p.id; render(); persist();
        });
        btns[p.id] = b;
        choices.appendChild(b);
      });
      card.appendChild(choices);
      var result = el("p", "result"); result.hidden = true;
      var glyph = el("span", "glyph"); glyph.setAttribute("aria-hidden", "true");
      var resultText = el("span");
      result.appendChild(glyph); result.appendChild(resultText);
      card.appendChild(result);
      var note = el("p", "note", s.note); note.hidden = true;
      card.appendChild(note);
      rowNodes[s.id] = { choices: choices, btns: btns, result: result, glyph: glyph, resultText: resultText, note: note };
      panel.appendChild(card);
    });
    var foot = el("div", "row");
    var status = el("p", "small muted"); status.setAttribute("aria-live", "polite");
    var commit = el("button", "primary", "Commit " + c.label); commit.type = "button";
    commit.addEventListener("click", function () {
      if (isCommitted(c.id)) return;
      if (!c.statements.every(function (s) { return state.marks[s.id]; })) return;
      state.committed.push(c.id);
      render(); persist(); maybeComplete();
    });
    foot.appendChild(status); foot.appendChild(commit);
    panel.appendChild(foot);
    panelNodes[c.id] = { panel: panel, status: status, commit: commit };
    $("panels").appendChild(panel);
  });

  // Demands panel
  (function () {
    var d = DATA.demands;
    var panel = el("div", "stack"); panel.setAttribute("role", "tabpanel"); panel.setAttribute("aria-labelledby", "tab-" + d.id);
    var list = el("ul", "plain"); list.style.listStyle = "none"; list.style.display = "grid"; list.style.gap = "8px";
    d.demands.forEach(function (x) { list.appendChild(el("li", "card demand", x.text)); });
    panel.appendChild(list);
    var q = el("div");
    var lab = el("label", "", d.question); lab.style.fontWeight = "500"; lab.htmlFor = "demand-answer";
    var ta = el("textarea"); ta.id = "demand-answer"; ta.rows = 4;
    ta.placeholder = "Who would have to know something they do not know now, and who would have to answer for it?";
    ta.addEventListener("input", function () { state.demandAnswer = ta.value; render(); persist(); });
    q.appendChild(lab); q.appendChild(ta);
    panel.appendChild(q);
    var foot = el("div", "row");
    var status = el("p", "small muted"); status.setAttribute("aria-live", "polite");
    var commit = el("button", "primary", "Commit"); commit.type = "button";
    commit.addEventListener("click", function () {
      if (isCommitted(d.id) || !state.demandAnswer.trim()) return;
      state.committed.push(d.id);
      render(); persist(); maybeComplete();
    });
    foot.appendChild(status); foot.appendChild(commit);
    panel.appendChild(foot);
    panelNodes[d.id] = { panel: panel, status: status, commit: commit, area: ta };
    $("panels").appendChild(panel);
  })();

  // Steelman deck (random draw, never the same card twice in a row, as in XLab)
  $("deck-draw").addEventListener("click", function () {
    var n = DATA.deck.length; if (!n) return;
    var i = lastDeck;
    if (n > 1) { do { i = Math.floor(Math.random() * n); } while (i === lastDeck); } else { i = 0; }
    lastDeck = i;
    $("deck-card").textContent = DATA.deck[i];
    $("deck-draw").textContent = "Draw another";
  });

  // Question workspace (XLab: rule any, count 2; nothing is graded)
  var qNodes = {};
  DATA.questions.forEach(function (q) {
    var card = el("section", "card");
    var head = el("div", "qhead");
    head.appendChild(el("h3", "", q.n + ". " + q.title));
    card.appendChild(head);
    var ta = el("textarea"); ta.rows = 7; ta.id = "q-" + q.id; ta.setAttribute("aria-label", q.title);
    ta.placeholder = "Answer as you go. Nothing is graded.";
    ta.addEventListener("input", function () { state.notes.answers[q.id] = ta.value; render(); persist(); });
    card.appendChild(ta);
    var foot = el("div"); foot.style.marginTop = "10px";
    var saved = el("p", "muted", "Saved. Keep editing if you want; it stays saved."); saved.hidden = true;
    var save = el("button", "primary", "Save answer"); save.type = "button";
    save.addEventListener("click", function () { state.notes.done[q.id] = true; render(); persist(); });
    foot.appendChild(saved); foot.appendChild(save);
    card.appendChild(foot);
    qNodes[q.id] = { area: ta, saved: saved, save: save };
    $("workspace").appendChild(card);
  });

  // Sources spoiler
  DATA.sources.forEach(function (s) {
    var li = el("li");
    var p = el("p");
    p.appendChild(el("span", "", s.label)); p.querySelector("span").style.fontWeight = "600";
    p.appendChild(document.createTextNode(": " + s.realName));
    li.appendChild(p);
    if (s.realNote) li.appendChild(el("p", "small muted", s.realNote));
    var ul = el("ul", "cites");
    s.cites.forEach(function (c) {
      var a = el("a", "", c.label); a.href = c.href; a.target = "_blank"; a.rel = "noopener";
      var cli = el("li"); cli.appendChild(a); ul.appendChild(cli);
    });
    li.appendChild(ul);
    $("sources").appendChild(li);
  });
  $("spoiler-open").addEventListener("click", function () { uncovered = true; render(); });
  $("spoiler-hide").addEventListener("click", function () { uncovered = false; render(); });

  function summary() {
    var lines = [];
    DATA.companies.forEach(function (c) {
      var done = isCommitted(c.id);
      lines.push(c.label + (done ? " (committed)" : " (not committed yet)") + ":");
      c.statements.forEach(function (s) {
        var m = state.marks[s.id];
        var line = "- \u201C" + s.text + "\u201D marked " + (m ? provLabel(m) : "nothing");
        if (done) line += (m === s.kind ? " (matches the authored kind)" : " (authored kind: " + provLabel(s.kind) + ")");
        lines.push(line);
      });
    });
    lines.push(DATA.demands.label + (isCommitted(DATA.demands.id) ? " (committed)" : " (not committed yet)") + ". " + DATA.demands.question + " Answer: " + (state.demandAnswer.trim() || "(empty)"));
    DATA.questions.forEach(function (q) {
      lines.push("Question " + q.n + " (" + q.title + ")" + (state.notes.done[q.id] ? " saved" : " not saved") + ": " + ((state.notes.answers[q.id] || "").trim() || "(empty)"));
    });
    lines.push(finished() ? "All three tabs committed; the exercise is complete." : state.committed.length + " of 3 tabs committed.");
    return lines.join("\n");
  }

  function persist() {
    var json = { marks: state.marks, committed: state.committed, demandAnswer: state.demandAnswer, notes: state.notes };
    if (window.Lens) { Lens.saveState(json, summary()); return; }
    try { localStorage.setItem(STORAGE, JSON.stringify(json)); } catch (e) {}
  }
  function maybeComplete() {
    if (completed || !finished()) return;
    completed = true;
    if (window.Lens) Lens.complete();
  }

  function render() {
    TAB_IDS.forEach(function (id) {
      var b = tabButtons[id];
      var label = id === DATA.demands.id ? DATA.demands.label : DATA.companies.filter(function (c) { return c.id === id; })[0].label;
      b.textContent = (isCommitted(id) ? "\u2713 " : "") + label;
      b.setAttribute("aria-selected", id === tab ? "true" : "false");
      panelNodes[id].panel.hidden = id !== tab;
    });
    DATA.companies.forEach(function (c) {
      var shown = isCommitted(c.id);
      var placed = 0;
      c.statements.forEach(function (s) {
        var mark = state.marks[s.id];
        if (mark) placed++;
        var r = rowNodes[s.id];
        r.choices.hidden = shown;
        DATA.provenance.forEach(function (p) { r.btns[p.id].setAttribute("aria-pressed", mark === p.id ? "true" : "false"); });
        r.result.hidden = !shown;
        r.note.hidden = !shown || !s.note;
        if (shown) {
          var right = mark === s.kind;
          r.result.className = "result " + (right ? "right" : "wrong");
          r.glyph.textContent = right ? "\u2713" : "!";
          r.resultText.textContent = provLabel(s.kind) + (right ? "" : ", you marked " + (provLabel(mark) || "nothing"));
        }
      });
      var pn = panelNodes[c.id];
      pn.status.textContent = shown ? "Marked." : placed + " of " + c.statements.length + " marked on this tab.";
      pn.commit.hidden = shown;
      pn.commit.disabled = shown || placed !== c.statements.length;
    });
    var dn = panelNodes[DATA.demands.id];
    var dShown = isCommitted(DATA.demands.id);
    if (dn.area.value !== state.demandAnswer) dn.area.value = state.demandAnswer;
    dn.status.textContent = dShown ? "Answered." : "";
    dn.commit.hidden = dShown;
    dn.commit.disabled = dShown || !state.demandAnswer.trim();
    var counted = 0;
    DATA.questions.forEach(function (q) {
      var n = qNodes[q.id];
      if (n.area.value !== (state.notes.answers[q.id] || "")) n.area.value = state.notes.answers[q.id] || "";
      var done = !!state.notes.done[q.id];
      if (done) counted++;
      n.saved.hidden = !done;
      n.save.hidden = done;
    });
    $("ws-count").textContent = Math.min(counted, DATA.questions.length) + " of " + DATA.questions.length + " answered";
    $("spoiler-open").hidden = uncovered;
    $("sources").hidden = !uncovered;
    $("spoiler-hide").hidden = !uncovered;
    $("spoiler-hint").hidden = uncovered;
  }

  function hydrate(saved, meta) {
    var box = saved && typeof saved === "object" ? saved : {};
    var next = { marks: {}, committed: [], demandAnswer: "", notes: { answers: {}, done: {} } };
    ALL.forEach(function (s) {
      var v = box.marks ? box.marks[s.id] : null;
      if (typeof v === "string" && KINDS.indexOf(v) !== -1) next.marks[s.id] = v;
    });
    if (Array.isArray(box.committed)) {
      box.committed.forEach(function (id) {
        if (TAB_IDS.indexOf(id) === -1 || next.committed.indexOf(id) !== -1) return;
        var c = DATA.companies.filter(function (x) { return x.id === id; })[0];
        if (c && !c.statements.every(function (s) { return next.marks[s.id]; })) return;
        next.committed.push(id);
      });
    }
    if (typeof box.demandAnswer === "string") next.demandAnswer = box.demandAnswer;
    if (next.committed.indexOf(DATA.demands.id) !== -1 && !next.demandAnswer.trim()) next.committed = next.committed.filter(function (id) { return id !== DATA.demands.id; });
    if (box.notes && typeof box.notes === "object") {
      DATA.questions.forEach(function (q) {
        var a = box.notes.answers ? box.notes.answers[q.id] : null;
        if (typeof a === "string") next.notes.answers[q.id] = a;
        if (box.notes.done && box.notes.done[q.id] === true) next.notes.done[q.id] = true;
      });
    }
    state = next;
    completed = !!(meta && meta.completed);
    var first = TAB_IDS.filter(function (id) { return !isCommitted(id); })[0];
    tab = first || DATA.companies[0].id;
    render();
    // XLab fires onComplete from an effect, so a restored state that is already
    // finished but was never marked complete completes on load. Mirror that.
    maybeComplete();
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

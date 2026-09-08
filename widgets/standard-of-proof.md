---
id: '54bb4936-12e7-47db-bf8c-983220d90912'
title: The Standard of Proof
summary_for_tutor: "An optional decision exercise on the standard of proof. One allegation (Meridian Compute ran a training run above the agreement's compute ceiling at its Delta campus in the third quarter) is pinned at the top; below it are four dockets, A to D, each describing the institution holding the docket and the evidence in front of it. For each docket the learner picks the institution's next move from four buttons (Record and keep collecting, Open a formal investigation, Issue a compliance judgment, Refer for enforcement) and writes a 60 to 90 word defence: what the docket establishes and what kind of evidence does that work, what it does not establish, whether this institution can defend the move. Submit unlocks only once every docket has a move and a defence; it freezes the dockets and reveals the 2x2 the learner was never shown (A and B varied evidence weight under a sound institution; C and D varied institutional soundness), two self-check questions, and XLab's marking key: four tickable criteria worth 2 points each with the grounds behind each, plus a No credit list; the learner marks their own answer and sees a running score out of 8. A separate button sends the four defences to the assessor, graded against that key. Then two closing prompts: a decision standard in at most 50 words, and an optional transfer question naming one structural change that would make the least-trusted docket's judgment defensible and which property it repairs (independence, competence, accountability, authority, or access). The widget counts as complete when Submit is pressed. Moves, defences, self-marks and closing answers reach you through the saved-state summary. Push back when a move reweighs the evidence in a docket where the institution was the weak part (C and D). Content ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The Standard of Proof</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "standard-of-proof". -->
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
  h1 { font-size: 26px; line-height: 1.2; margin: 4px 0 12px; }
  h2 { font-size: 18px; }
  p { margin: 0; }
  ol, ul { margin: 6px 0 0; padding-left: 22px; }
  li { margin: 2px 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; margin-top: 12px; }
  [hidden] { display: none !important; }
  .allegation { border-color: var(--accent); background: var(--surface); }
  .allegation p.quote { margin-top: 6px; font-weight: 500; font-size: 15px; }
  .intro { margin-top: 16px; max-width: 44rem; }
  .intro .lead { font-weight: 500; font-size: 15px; }
  .intro .tasks { margin-top: 8px; }
  .intro .limit { color: var(--muted); margin-top: 8px; }
  .docket-title { font-size: 15px; font-weight: 600; }
  .docket .eyebrow { margin-top: 10px; }
  .docket p.body { margin-top: 2px; }
  .moves { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 12px; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button:disabled { cursor: default; }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.move { border-radius: 999px; padding: 6px 12px; font-size: 13px; }
  button.move .tick { display: none; margin-right: 4px; }
  button.move.is-picked { border-color: var(--accent); background: var(--accent); color: #fff; font-weight: 500; }
  button.move.is-picked .tick { display: inline; }
  button.move:disabled:not(.is-picked) { opacity: 0.5; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled { opacity: 0.5; background: var(--accent); }
  label.field { display: block; margin-top: 12px; }
  textarea {
    display: block; width: 100%; margin-top: 4px; min-height: 84px; resize: vertical;
    font: inherit; color: inherit; background: #fff; border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  textarea[readonly] { background: var(--surface); color: var(--muted); }
  .count { font-size: 12px; color: var(--muted); text-align: right; margin-top: 4px; }
  .count.is-over { color: var(--text); font-weight: 600; }
  .bar { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; margin-top: 16px; }
  .bar .status { font-size: 12px; color: var(--muted); }
  .after { display: none; }
  .after.is-visible { display: block; }
  .after h2 { margin-bottom: 8px; }
  .after p.body { margin-top: 8px; }
  .keyhead { display: flex; flex-wrap: wrap; justify-content: space-between; align-items: baseline; gap: 8px; }
  .keyscore { font-size: 12px; color: var(--muted); }
  .keynote { color: var(--muted); margin-top: 8px; }
  ul.criteria { list-style: none; padding: 0; margin-top: 12px; }
  ul.criteria li { margin: 0 0 8px; }
  button.crit { display: flex; gap: 12px; align-items: flex-start; width: 100%; padding: 10px 12px; }
  button.crit.is-on { border-color: var(--accent); background: var(--surface); box-shadow: 0 0 0 1px var(--accent); }
  .badge {
    flex: 0 0 auto; width: 22px; height: 22px; border: 1px solid var(--border); border-radius: 4px;
    display: inline-flex; align-items: center; justify-content: center; font-size: 11px; margin-top: 2px;
  }
  button.crit.is-on .badge { background: var(--accent); border-color: var(--accent); color: #fff; }
  .crit .sub { display: block; color: var(--muted); font-size: 12px; margin-top: 4px; }
  ul.plain { list-style: none; padding: 0; margin-top: 6px; }
  ul.plain li { display: flex; gap: 10px; color: var(--muted); }
  ul.plain li span.dot { flex: 0 0 auto; }
  .scores { margin-top: 12px; }
  .scores li { margin: 2px 0; }
  .scoreline { font-size: 12px; color: var(--muted); }
  .optional { color: var(--muted); font-weight: 400; }
  .fieldlabel { font-weight: 500; }
  @media (max-width: 480px) {
    body { padding: 12px; }
    .card { padding: 12px; }
  }
</style>
</head>
<body>
<p class="eyebrow">Optional exercise</p>
<h1>The Standard of Proof</h1>

<section class="card allegation" aria-labelledby="alleg-label">
  <p class="eyebrow" id="alleg-label">The allegation, over every docket</p>
  <p class="quote" id="allegation"></p>
</section>

<div class="intro">
  <p class="lead" id="intro"></p>
  <p class="tasks" id="task-lead"></p>
  <ol id="tasks"></ol>
  <p class="limit" id="limit"></p>
</div>

<div id="dockets"></div>

<div class="bar">
  <p class="status" id="status"></p>
  <span>
    <button type="button" id="submit" class="primary">Submit</button>
    <button type="button" id="reset" hidden>Start over</button>
  </span>
</div>

<div class="after" id="after">
  <section class="card">
    <p class="eyebrow">After submission</p>
    <p class="body" id="grid"></p>
    <p class="body" id="selfcheck-lead"></p>
    <ul class="plain" id="selfcheck"></ul>
  </section>

  <section class="card" aria-labelledby="key-title">
    <div class="keyhead">
      <p class="eyebrow" id="key-title">Marking key</p>
      <p class="keyscore" id="key-score" aria-live="polite"></p>
    </div>
    <p class="keynote" id="key-note"></p>
    <ul class="criteria" id="criteria"></ul>
    <p class="eyebrow">No credit</p>
    <ul class="plain" id="nocredit"></ul>
    <p class="keynote" id="key-foot"></p>
  </section>

  <section class="card" id="assessor">
    <p class="eyebrow">Assessor</p>
    <p class="body" id="score-text">Send your four defences to the assessor. Each docket is graded against the marking key above.</p>
    <ul class="scores plain" id="scores"></ul>
    <div class="bar">
      <span></span>
      <span>
        <button type="button" id="score" class="primary">Score my four dockets</button>
        <button type="button" id="feedback" hidden>Get feedback on the scores</button>
      </span>
    </div>
  </section>

  <section class="card">
    <label class="field" for="final"><span class="fieldlabel" id="final-label"></span>
      <textarea id="final"></textarea>
    </label>
    <p class="count" id="final-count" aria-live="polite"></p>
  </section>

  <section class="card">
    <label class="field" for="transfer"><span class="fieldlabel"><span class="optional">Optional: </span><span id="transfer-label"></span></span>
      <textarea id="transfer"></textarea>
    </label>
  </section>
</div>

<script>
  var ALLEGATION = "Meridian Compute ran a training run above the agreement’s compute ceiling at its Delta campus in the third quarter.";
  var INTRO = "One allegation. Four dockets: the evidence in front of an institution, and the institution holding it.";
  var TASK_LEAD = "For each docket, choose the institution’s next move. Then defend it:";
  var TASKS = [
    "what the docket establishes, and what kind of evidence does that work;",
    "what it does not establish;",
    "whether this institution can defend the move you chose."
  ];
  var LIMIT = "Use about 60 to 90 words per docket.";

  var MOVES = [
    { id: "collect", label: "Record and keep collecting" },
    { id: "investigate", label: "Open a formal investigation" },
    { id: "judge", label: "Issue a compliance judgment" },
    { id: "enforce", label: "Refer for enforcement" }
  ];

  var DOCKETS = [
    {
      id: "lone-report", letter: "A", title: "The lone report",
      institution: "The treaty’s verification directorate holds the docket. Its access rights, funding and staffing are not in question.",
      evidence: [
        "A former Meridian scheduling engineer reports that Delta’s main cluster ran one uninterrupted job for six weeks of the third quarter.",
        "The report came through the treaty’s protected channel and is internally consistent.",
        "Nothing else has been collected."
      ]
    },
    {
      id: "converging", letter: "B", title: "The converging docket",
      institution: "The same directorate, on the same footing.",
      evidence: [
        "The engineer’s report from docket A.",
        "Customs records show Meridian imported accelerators well above its declared inventory in the second quarter.",
        "Grid-operator telemetry puts Delta’s power draw far above the level its declaration supports, for the same six weeks.",
        "Meridian declined the quarter’s scheduled managed-access visit and offered no alternative means."
      ]
    },
    {
      id: "channelled", letter: "C", title: "The channelled docket",
      institution: "The directorate has no access rights at Delta. Everything it knows arrives through one channel: an audit Meridian commissioned itself, delivered as a summary with the underlying records withheld.",
      evidence: [
        "The commissioned audit concludes that no ceiling-relevant run took place.",
        "A facilities contractor’s tip contradicts the audit. It is uncorroborated.",
        "The directorate’s requests for the audit’s working papers have gone unanswered."
      ]
    },
    {
      id: "compromised", letter: "D", title: "The compromised panel",
      institution: "The panel that must issue any judgment is funded through the industry association Meridian chairs, and two of its five members are on leave from Meridian’s suppliers.",
      evidence: [
        "Telemetry, procurement records and two independent insider reports all point the same way.",
        "Meridian has cooperated with every access request."
      ]
    }
  ];

  var SELF_CHECK_LEAD = "For each docket, compare your answer against two questions:";
  var SELF_CHECK = [
    "Did the move you chose match what that docket’s evidence currently supports?",
    "Where the institution was the weak part, did your move repair the institution rather than reweigh the evidence?"
  ];
  var REVEAL_GRID = "The four dockets were a 2×2 you were never shown: evidence weight on one axis, institutional soundness on the other. A and B varied the evidence under a sound institution; C and D varied the institution.";
  var FINAL = "In no more than 50 words, state the decision standard you actually applied: what separated the dockets you would investigate from any docket you would judge or refer?";
  var FINAL_MAX_WORDS = 50;
  var TRANSFER = "Take the docket whose institution you trusted least. Name one structural change that would make its judgment defensible, and say which property it repairs: independence, competence, accountability, authority, or access.";

  // XLab marking key (STANDARD_OF_PROOF_KEY). One criterion per docket, in docket order.
  var KEY_NOTE = "Mark your own answer. Any wording that does not distort the meaning counts; no criterion needs a particular term. Where a criterion asks for a mechanism, a correct label without it earns nothing.";
  var KEY_REASONING = "The judgement alone is not the point. The reasoning has to be on the page.";
  var KEY_FOOT = "This score is yours. It is not sent anywhere, counts towards nothing, and completes nothing.";
  var KEY = {
    criteria: [
      {
        docket: "lone-report",
        text: "A: the move stops at collection or investigation, and the reason is what one report can carry, not the source’s sincerity.",
        points: 2, needsReasoning: true,
        grounds: "One protected, consistent human report licenses doing something and establishes nothing alone. What is missing is anything independent of one person’s account: the human evidence has no technical record to gain weight from yet."
      },
      {
        docket: "converging",
        text: "B: the move rises with corroboration, and the refusal is weighed as conduct, not as proof.",
        points: 2, needsReasoning: true,
        grounds: "Customs records and telemetry are independent technical evidence converging with the human report; that convergence is how human evidence gains weight. A declined inspection aggravates; it does not convert suspicion into a finding. A compliance judgment is defensible here; enforcement is a referral, because enforcement is not the verifier’s own power. That is the authority line."
      },
      {
        docket: "channelled",
        text: "C: the defect is named as access, not as evidence weight: informational capture.",
        points: 2, needsReasoning: true,
        grounds: "Everything the institution sees was chosen by the audited party: Brundage et al.’s Access principle frustrated. The move is to secure independent access (the working papers, a challenge inspection), not to judge either way on a channelled docket, and not to treat the audit’s conclusion as false because its channel is bad."
      },
      {
        docket: "compromised",
        text: "D: the evidence is conceded and the institution is disqualified: financial capture, independence.",
        points: 2, needsReasoning: true,
        grounds: "The docket would carry a judgment; this panel cannot defensibly issue it. Funding through the audited party’s association is the financial form of capture; members on leave from its suppliers is the revolving-door, cultural form: the pair Brundage et al.’s Independent Experts principle exists to block (disclosure, no auditor-shopping, cooling-off periods). Political capture is the same failure arriving through state pressure. The repair is recusal or reconstitution, not more evidence."
      }
    ],
    noCredit: [
      "Ranking the dockets from weakest to strongest. The task is a move per docket, defended.",
      "Treating docket D’s panel defect as a reason to doubt docket D’s evidence.",
      "A move justified by the seriousness of the allegation rather than by what the docket establishes.",
      "Naming a capture form without saying which fact in the docket is the capture."
    ]
  };

  var STORAGE_KEY = "lens-standard-of-proof:v1";
  var state = emptyState();
  var completed = false;
  var lastResponseId = null;
  var ui = { dockets: {}, crits: [] };

  function emptyState() {
    return { moves: {}, answers: {}, submitted: false, ticked: [], final: "", transfer: "", scores: {} };
  }
  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function countWords(text) {
    var m = (text || "").trim().match(/[^\s]+/g);
    return m ? m.length : 0;
  }
  function moveLabel(id) {
    for (var i = 0; i < MOVES.length; i++) if (MOVES[i].id === id) return MOVES[i].label;
    return "";
  }
  function keyTotal() {
    var t = 0; KEY.criteria.forEach(function (c) { t += c.points; }); return t;
  }
  function keyScored() {
    var t = 0;
    state.ticked.forEach(function (i) { if (KEY.criteria[i]) t += KEY.criteria[i].points; });
    return t;
  }
  function ready() {
    for (var i = 0; i < DOCKETS.length; i++) {
      var d = DOCKETS[i];
      if (!state.moves[d.id] || !(state.answers[d.id] || "").trim()) return false;
    }
    return true;
  }

  // Static text
  document.getElementById("allegation").textContent = "“" + ALLEGATION + "”";
  document.getElementById("intro").textContent = INTRO;
  document.getElementById("task-lead").textContent = TASK_LEAD;
  TASKS.forEach(function (t) { document.getElementById("tasks").appendChild(el("li", "", t)); });
  document.getElementById("limit").textContent = LIMIT;
  document.getElementById("grid").textContent = REVEAL_GRID;
  document.getElementById("selfcheck-lead").textContent = SELF_CHECK_LEAD;
  SELF_CHECK.forEach(function (q) {
    var li = el("li"); li.appendChild(el("span", "dot", "·")); li.appendChild(el("span", "", q));
    document.getElementById("selfcheck").appendChild(li);
  });
  document.getElementById("key-note").textContent = KEY_NOTE;
  document.getElementById("key-foot").textContent = KEY_FOOT;
  KEY.noCredit.forEach(function (line) {
    var li = el("li"); li.appendChild(el("span", "dot", "·")); li.appendChild(el("span", "", line));
    document.getElementById("nocredit").appendChild(li);
  });
  document.getElementById("final-label").textContent = FINAL;
  document.getElementById("transfer-label").textContent = TRANSFER;

  // Dockets
  var docketsRoot = document.getElementById("dockets");
  DOCKETS.forEach(function (d) {
    var card = el("section", "card docket");
    card.setAttribute("aria-labelledby", "docket-" + d.id + "-title");
    var title = el("p", "docket-title", d.letter + " · " + d.title);
    title.id = "docket-" + d.id + "-title";
    card.appendChild(title);
    card.appendChild(el("p", "eyebrow", "The institution holding it"));
    card.appendChild(el("p", "body", d.institution));
    card.appendChild(el("p", "eyebrow", "The evidence"));
    var ul = el("ul");
    d.evidence.forEach(function (line) { ul.appendChild(el("li", "", line)); });
    card.appendChild(ul);

    var group = el("div", "moves");
    group.setAttribute("role", "group");
    group.setAttribute("aria-label", "Next move for docket " + d.letter);
    var moveBtns = {};
    MOVES.forEach(function (m) {
      var b = el("button", "move");
      b.type = "button";
      b.id = "move-" + d.id + "-" + m.id;
      b.appendChild(el("span", "tick", "✓"));
      b.appendChild(el("span", "", m.label));
      b.addEventListener("click", function () {
        if (state.submitted) return;
        state.moves[d.id] = m.id;
        render(); persist();
      });
      moveBtns[m.id] = b;
      group.appendChild(b);
    });
    card.appendChild(group);

    var label = el("label", "field");
    label.htmlFor = "proof-" + d.id;
    label.appendChild(el("span", "eyebrow", "Your analysis"));
    var ta = el("textarea");
    ta.id = "proof-" + d.id;
    ta.addEventListener("input", function () {
      if (state.submitted) return;
      state.answers[d.id] = ta.value;
      render(); persist();
    });
    label.appendChild(ta);
    card.appendChild(label);
    var count = el("p", "count");
    count.setAttribute("aria-live", "polite");
    card.appendChild(count);

    ui.dockets[d.id] = { moveBtns: moveBtns, ta: ta, count: count };
    docketsRoot.appendChild(card);
  });

  // Marking key criteria
  var critRoot = document.getElementById("criteria");
  KEY.criteria.forEach(function (c, i) {
    var li = el("li");
    var b = el("button", "crit");
    b.type = "button";
    b.appendChild(el("span", "badge", String(c.points)));
    var body = el("span");
    body.appendChild(el("span", "", c.text));
    if (c.needsReasoning) body.appendChild(el("span", "sub", KEY_REASONING));
    if (c.grounds) body.appendChild(el("span", "sub", c.grounds));
    b.appendChild(body);
    b.addEventListener("click", function () {
      var at = state.ticked.indexOf(i);
      if (at === -1) state.ticked.push(i); else state.ticked.splice(at, 1);
      render(); persist();
    });
    li.appendChild(b);
    critRoot.appendChild(li);
    ui.crits.push(b);
  });

  var submitBtn = document.getElementById("submit");
  var resetBtn = document.getElementById("reset");
  var statusEl = document.getElementById("status");
  var afterEl = document.getElementById("after");
  var finalTa = document.getElementById("final");
  var finalCount = document.getElementById("final-count");
  var transferTa = document.getElementById("transfer");
  var scoreBtn = document.getElementById("score");
  var assessorEl = document.getElementById("assessor");
  var feedbackBtn = document.getElementById("feedback");
  var scoreText = document.getElementById("score-text");
  var scoresEl = document.getElementById("scores");
  var SCORE_TEXT = scoreText.textContent;

  function render() {
    DOCKETS.forEach(function (d) {
      var u = ui.dockets[d.id];
      MOVES.forEach(function (m) {
        var picked = state.moves[d.id] === m.id;
        u.moveBtns[m.id].classList.toggle("is-picked", picked);
        u.moveBtns[m.id].setAttribute("aria-pressed", picked ? "true" : "false");
        u.moveBtns[m.id].disabled = state.submitted;
      });
      var v = state.answers[d.id] || "";
      if (u.ta.value !== v) u.ta.value = v;
      u.ta.readOnly = state.submitted;
      u.count.textContent = countWords(v) + " words";
    });
    statusEl.textContent = state.submitted
      ? "Submitted. The four dockets are frozen."
      : "Submit opens once every docket carries a move and an analysis.";
    submitBtn.hidden = state.submitted;
    submitBtn.disabled = state.submitted || !ready();
    resetBtn.hidden = !state.submitted;
    resetBtn.disabled = !state.submitted;
    var hasAssessor = !!(window.Lens && Lens.submit);
    assessorEl.hidden = !hasAssessor;
    scoreBtn.hidden = !hasAssessor;
    scoreBtn.disabled = !hasAssessor || !state.submitted;
    feedbackBtn.disabled = feedbackBtn.hidden;
    afterEl.classList.toggle("is-visible", state.submitted);

    ui.crits.forEach(function (b, i) {
      var on = state.ticked.indexOf(i) !== -1;
      b.classList.toggle("is-on", on);
      b.setAttribute("aria-pressed", on ? "true" : "false");
    });
    document.getElementById("key-score").textContent = keyScored() + " / " + keyTotal();

    if (finalTa.value !== state.final) finalTa.value = state.final;
    var fw = countWords(state.final);
    finalCount.textContent = fw + " / " + FINAL_MAX_WORDS + " words" + (fw > FINAL_MAX_WORDS ? " (over the limit)" : "");
    finalCount.classList.toggle("is-over", fw > FINAL_MAX_WORDS);
    if (transferTa.value !== state.transfer) transferTa.value = state.transfer;

    while (scoresEl.firstChild) scoresEl.removeChild(scoresEl.firstChild);
    var any = false;
    DOCKETS.forEach(function (d) {
      var s = state.scores[d.id];
      if (s === undefined) return;
      any = true;
      var li = el("li"); li.appendChild(el("span", "dot", "·"));
      li.appendChild(el("span", "", "Docket " + d.letter + ": " + (s === null ? "score pending" : s + " / 100")));
      scoresEl.appendChild(li);
    });
    if (any) scoreBtn.textContent = "Score again";
  }

  function summary() {
    var parts = ["Allegation: " + ALLEGATION];
    DOCKETS.forEach(function (d) {
      var mv = state.moves[d.id] ? moveLabel(state.moves[d.id]) : "(no move chosen)";
      var an = (state.answers[d.id] || "").trim() || "(no analysis yet)";
      var sc = state.scores[d.id];
      parts.push("Docket " + d.letter + " (" + d.title + "): move = " + mv + ". Analysis: " + an + (typeof sc === "number" ? " Assessor score: " + sc + "/100." : ""));
    });
    if (state.submitted) {
      var ticked = [];
      state.ticked.slice().sort().forEach(function (i) { if (KEY.criteria[i]) ticked.push(KEY.criteria[i].text.charAt(0)); });
      parts.push("Submitted; the 2x2 (evidence weight versus institutional soundness) and the marking key are revealed. Self-marked " + keyScored() + " of " + keyTotal() + " points" + (ticked.length ? " (criteria ticked: " + ticked.join(", ") + ")" : "") + ".");
      parts.push("Decision standard (max 50 words): " + ((state.final || "").trim() || "(empty)"));
      parts.push("Transfer answer: " + ((state.transfer || "").trim() || "(empty)"));
    } else {
      parts.push("Not yet submitted.");
    }
    return parts.join(" ");
  }

  function persist() {
    if (window.Lens) {
      Lens.saveState(state, summary());
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }

  submitBtn.addEventListener("click", function () {
    if (!ready() || state.submitted) return;
    state.submitted = true;
    render(); persist();
    if (!completed) {
      completed = true;
      if (window.Lens) Lens.complete();
    }
  });
  resetBtn.addEventListener("click", function () {
    state = emptyState();
    lastResponseId = null;
    scoreBtn.textContent = "Score my four dockets";
    scoreText.textContent = SCORE_TEXT;
    feedbackBtn.hidden = true;
    render(); persist();
  });
  finalTa.addEventListener("input", function () { state.final = finalTa.value; render(); persist(); });
  transferTa.addEventListener("input", function () { state.transfer = transferTa.value; render(); persist(); });

  function docketQuestion(d) {
    var labels = MOVES.map(function (m) { return m.label; }).join(" / ");
    return "Allegation: " + ALLEGATION + " Docket " + d.letter + ", " + d.title + ". The institution holding it: " + d.institution +
      " The evidence: " + d.evidence.join(" ") + " Choose the institution’s next move (" + labels + ") and defend it: " +
      TASKS.join(" ") + " " + LIMIT;
  }
  function docketInstructions(c) {
    return "Score 0 to 100 against XLab’s marking key criterion for this docket: " + c.text + " " + KEY_REASONING +
      " Grounds: " + c.grounds + " " + KEY_NOTE +
      " Full marks when the move and the reasoning both match the criterion. About half when the move matches but the reasoning is missing or generic. No credit for: " + KEY.noCredit.join(" ");
  }
  var FEEDBACK = "Answer XLab’s two self-check questions for this docket in two or three sentences: " + SELF_CHECK.join(" ");

  scoreBtn.addEventListener("click", function () {
    if (!window.Lens || !Lens.submit || !state.submitted) return;
    scoreBtn.disabled = true;
    scoreText.textContent = "Scoring your four dockets…";
    var jobs = KEY.criteria.map(function (c) {
      var d = null;
      for (var i = 0; i < DOCKETS.length; i++) if (DOCKETS[i].id === c.docket) d = DOCKETS[i];
      return Lens.submit({
        item: "docket-" + d.letter.toLowerCase(),
        question: docketQuestion(d),
        answer: "Move: " + moveLabel(state.moves[d.id]) + ". Analysis: " + (state.answers[d.id] || "").trim(),
        assessmentInstructions: docketInstructions(c),
        feedbackInstructions: FEEDBACK
      }).then(function (result) {
        state.scores[d.id] = result && typeof result.score === "number" ? result.score : null;
        if (result && result.responseId) lastResponseId = result.responseId;
      });
    });
    Promise.all(jobs).then(function () {
      var pending = false;
      DOCKETS.forEach(function (d) { if (state.scores[d.id] === null) pending = true; });
      scoreText.textContent = pending
        ? "Some scores are taking a while; the ones that are in are listed below."
        : "Scores are in.";
      feedbackBtn.hidden = lastResponseId == null;
      render(); persist();
    }, function () {
      scoreText.textContent = "Could not score the dockets right now.";
      scoreBtn.disabled = false;
    });
  });
  feedbackBtn.addEventListener("click", function () {
    if (!window.Lens || !Lens.requestFeedback || lastResponseId == null) return;
    Lens.requestFeedback(lastResponseId, "Can I get feedback on my docket scores?");
  });

  function prune(raw) {
    var next = emptyState();
    if (!raw || typeof raw !== "object") return next;
    var moveIds = MOVES.map(function (m) { return m.id; });
    DOCKETS.forEach(function (d) {
      var m = raw.moves && raw.moves[d.id];
      if (typeof m === "string" && moveIds.indexOf(m) !== -1) next.moves[d.id] = m;
      var a = raw.answers && raw.answers[d.id];
      if (typeof a === "string" && a.trim()) next.answers[d.id] = a;
      var s = raw.scores && raw.scores[d.id];
      if (typeof s === "number") next.scores[d.id] = s;
    });
    next.submitted = raw.submitted === true;
    if (Array.isArray(raw.ticked)) {
      raw.ticked.forEach(function (n) {
        if (typeof n === "number" && n >= 0 && n < KEY.criteria.length && next.ticked.indexOf(n) === -1) next.ticked.push(n);
      });
    }
    if (typeof raw.final === "string") next.final = raw.final;
    if (typeof raw.transfer === "string") next.transfer = raw.transfer;
    return next;
  }

  function hydrate(saved, meta) {
    state = prune(saved);
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) {}
    hydrate(raw, null);
  }
</script>
</body>
</html>

---
id: '5073b6d6-2703-450d-b682-4e64b98325f3'
title: Insider Report (Construct a Case)
summary_for_tutor: "The constructed-response exercise XLab runs as the Insider Report. The learner writes one case in four boxes (Insider, Information, Reporting route, Failure point) in which an insider's report about a prohibited AI activity is accurate, the insider is legally permitted to report it, and the verification regime still cannot turn the report into actionable evidence. The three conditions, the 100 to 180 word brief and the four box names are page text directly above the widget, so the widget opens on the first box. While the learner drafts, rule-based desk checks re-run on every keystroke and mark the box they are about: empty boxes, total length, a failure point that rests on the allegation being false, on reporting being forbidden or on the verifier ignoring it (all three ruled out by the brief), a failure point with no mechanism in it, information that never says how the insider knows, and a failure point that shares no substantive word with the rest of the case. A steelman deck deals one of eight challenge questions at a time. Submit the case freezes the four boxes, counts as done, and reveals the five-point marking key the learner ticks against their own answer; a Score my case button sends the four boxes to the AI assessor with the same key, and feedback can be requested on the score. Three collapsed callouts on the page below the widget hold the rest, all of it withheld until the learner has submitted: 'Check your case' (five questions), 'Where a report can die' (the four failure categories that do not count and the five that do) and 'Two cases that work, for different reasons' (the two worked cases). The saved-state summary gives you the learner's four boxes, the desk-check flags and their self-mark. Coach on the failure point: it must be a named mechanism inside the institution, not a false allegation and not a verifier who simply ignores the report."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Insider Report (Construct a Case)</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-insiders" (live component ConstructCase). -->
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
  h1 { font-size: 24px; margin: 4px 0 12px; }
  p { margin: 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .stack > * + * { margin-top: 16px; }
  .panel { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .panel.surface { background: var(--surface); }
  .panel-head { display: flex; flex-wrap: wrap; align-items: baseline; justify-content: space-between; gap: 4px 16px; }
  .aside { font-size: 12px; color: var(--muted); }
  .field { border: 1px solid var(--border); border-radius: 8px; padding: 12px 16px 14px; background: #fff; }
  .field + .field { margin-top: 10px; }
  .field label { display: block; font-size: 13px; font-weight: 600; margin-bottom: 6px; }
  .field.is-flagged { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .field .flag { font-weight: 400; font-size: 12px; color: var(--accent-hover); margin-left: 8px; display: none; }
  .field.is-flagged .flag { display: inline; }
  textarea {
    width: 100%; font: inherit; color: inherit; background: #fff; resize: vertical;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px; line-height: 1.5;
  }
  textarea:focus { outline: 2px solid var(--accent); outline-offset: 1px; border-color: var(--accent); }
  textarea[readonly] { background: var(--surface); color: var(--muted); }
  .row { display: flex; flex-wrap: wrap; gap: 8px 16px; align-items: center; justify-content: space-between; }
  .count { font-size: 12px; color: var(--muted); }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .checks { margin-top: 12px; }
  .check { display: flex; gap: 10px; align-items: flex-start; }
  .check + .check { margin-top: 8px; }
  .check .mark { flex: 0 0 18px; width: 18px; height: 18px; border-radius: 50%; border: 1px solid var(--border); font-size: 11px; font-weight: 600; line-height: 16px; text-align: center; margin-top: 2px; }
  .check.ok .mark { color: var(--accent); border-color: var(--accent); }
  .check.warn .mark { color: var(--text); border-color: var(--text); }
  .check.bad .mark { color: #fff; background: var(--text); border-color: var(--text); }
  .card { margin-top: 12px; min-height: 1.5em; }
  .card.is-drawn { font-family: var(--font-heading); font-size: 17px; line-height: 1.4; }
  .deck-btn { margin-top: 12px; }
  .key-list { list-style: none; margin: 12px 0 0; padding: 0; }
  .key-list li + li { margin-top: 8px; }
  .crit { display: flex; gap: 12px; width: 100%; text-align: left; align-items: flex-start; padding: 10px 12px; }
  .crit .pts { flex: 0 0 22px; width: 22px; height: 22px; border: 1px solid var(--border); border-radius: 4px; font-size: 11px; font-weight: 600; line-height: 20px; text-align: center; margin-top: 2px; }
  .crit.is-on { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: #fdf8f1; }
  .crit.is-on .pts { background: var(--accent); border-color: var(--accent); color: #fff; }
  .crit .sub { display: block; font-size: 12px; color: var(--muted); margin-top: 2px; }
  .crit .tick { font-size: 12px; color: var(--accent); margin-left: auto; white-space: nowrap; display: none; }
  .crit.is-on .tick { display: inline; }
  .plain { list-style: none; margin: 12px 0 0; padding: 0; }
  .plain li { display: flex; gap: 10px; }
  .plain li + li { margin-top: 6px; }
  .plain li::before { content: "\2013"; color: var(--muted); flex: 0 0 auto; }
  .plain.muted { color: var(--muted); margin-top: 6px; }
  .muted { color: var(--muted); }
  .small { font-size: 12px; }
  .status { min-height: 1.5em; }
  .score-row { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 10px; }
  [hidden] { display: none !important; }
</style>
</head>
<body>
<div class="stack">
  <div id="fields"></div>

  <div class="row">
    <p class="count" id="count" aria-live="polite"></p>
    <span>
      <button type="button" id="submit" class="primary">Submit the case</button>
      <button type="button" id="reset" hidden>Start over</button>
    </span>
  </div>

  <section class="panel" id="checks" hidden aria-live="polite">
    <div class="panel-head">
      <p class="eyebrow">Desk checks</p>
      <p class="aside">Rules, not marking.</p>
    </div>
    <div class="checks" id="check-list"></div>
  </section>

  <section class="panel" id="deck" hidden>
    <div class="panel-head">
      <p class="eyebrow">Steelman deck</p>
      <p class="aside">Contested claims get challenged, not narrated.</p>
    </div>
    <p class="card" id="card" aria-live="polite"></p>
    <button type="button" id="draw" class="deck-btn">Draw a challenge</button>
  </section>

  <div id="reveal" hidden></div>
</div>

<script>
  var FIELDS = [
    { id: "insider", label: "Insider", rows: 2 },
    { id: "information", label: "Information", rows: 3 },
    { id: "route", label: "Reporting route", rows: 3 },
    { id: "failure", label: "Failure point", rows: 3 }
  ];
  var WORDS = { min: 100, max: 180 };

  var CONDITIONS = [
    "An insider’s report about a prohibited AI activity is accurate.",
    "The insider is legally permitted to report what they know.",
    "The verification regime cannot turn the report into actionable evidence."
  ];

  var CHECKLIST = [
    "Is the allegation actually true?",
    "Could this insider plausibly know it?",
    "Is reporting permitted?",
    "Does the verification failure arise from the institution rather than from the allegation being false?",
    "Can you identify the precise missing link between report and action?"
  ];

  var DECK = [
    "Who in your case would have to be lying for it to fall apart? If the answer is nobody, condition 1 is doing real work.",
    "Your insider knows what they know from one place. Name a second place the same fact could have come from, and say why it did not.",
    "If your failure were fixed tomorrow by one rule change, which rule?",
    "Would your failure read the same if the insider were two levels more senior? If yes, it may not be about access at all.",
    "Who is the first person to receive this report, and what do they personally lose by acting on it?",
    "Is your failure about permission, about records, or about identification? Cases that blur the three usually have not chosen one.",
    "Strip every adjective from your failure point. Is there still a mechanism underneath?",
    "What would a verifier have to obtain for this report to become actionable? If nothing would, you may have written a false allegation rather than a failed verification."
  ];

  var KEY = {
    criteria: [
      {
        text: "The insider plausibly has access to accurate information about the violation.",
        points: 1,
        grounds: "Compartmentalisation is the constraint: a person sees the part of a violation their station touches, and rarely more."
      },
      {
        text: "The report concerns an actual violation, not merely suspicious activity.",
        points: 1
      },
      {
        text: "Disclosure is permitted by the framework the case names.",
        points: 1,
        grounds: "The chapter ties this to three things at once: a covered person, a reportable subject, and a named recipient. A case that satisfies one of the three has not satisfied this."
      },
      {
        text: "A concrete failure stops the report from becoming actionable evidence, and it is named.",
        points: 1,
        needsReasoning: true,
        grounds: "The investigation standard is the test of “actionable”: material lawfully obtained, chain of custody preserved, evidence admissible. A failure at any of those three is a failure of the kind this asks for."
      },
      {
        text: "The failure is internally consistent with the rest of the case.",
        points: 1,
        needsReasoning: true
      }
    ],
    noCredit: [
      "Defining the three conditions in the abstract rather than instantiating them in one case.",
      "A failure that is only that the insider lied, was wrong, was forbidden to report, or was ignored for no stated reason.",
      "A failure that contradicts the access the case gave the insider."
    ]
  };
  var KEY_INTRO = "Mark your own answer. Any wording that does not distort the meaning counts; no criterion needs a particular term. Where a criterion asks for a mechanism, a correct label without it earns nothing.";
  var NEEDS_REASONING = "The judgement alone is not the point: the reasoning has to be on the page.";
  var KEY_FOOT = "This self-marked score is yours. It is not sent anywhere, counts towards nothing, and completes nothing.";

  var STORAGE_KEY = "lens-widget-construct-case";

  // Desk checks, ported from XLab's case-checks.ts. Rules, not marking.
  var UNTRUE = /\b(lied|lying|lies|fabricat\w*|made it up|invent\w*|false|untrue|mistaken|wrong about)\b/i;
  var FORBIDDEN = /\b(not allowed to report|forbidden to report|prohibited from report\w*|illegal to report|cannot legally report|barred from report\w*)\b/i;
  var IGNORED = /\b(ignor\w+|disregard\w+|does not care|doesn't care|no one cares|nobody cares)\b/i;
  var MECHANISM = /\b(because|since|so that|therefore|which means|cannot|can't|has no|no authority|no route|not permitted to share|outside|belongs to|requires|without)\b/i;
  var HOW_KNOWN = /\b(saw|watched|read|ran|signed|processed|administer\w*|logged|reviewed|attended|received|monitored|handled|audited|configured|approved|was told|overheard|holds?|has access)\b/i;
  var STOP = {};
  ["that","this","with","from","they","them","their","have","been","were","would","could","which","what","when","where","about","into","then","than","there","these","those","will","does","report","reports","reported","reporting"].forEach(function (w) { STOP[w] = true; });

  function countWords(text) { return (String(text || "").trim().match(/[^\s]+/g) || []).length; }
  function wordSet(text) {
    var out = {};
    (String(text || "").toLowerCase().match(/[a-z][a-z-]{3,}/g) || []).forEach(function (w) { if (!STOP[w]) out[w] = true; });
    return out;
  }
  function value(id) { return String(state.values[id] || ""); }
  function blankLabels() { return FIELDS.filter(function (f) { return !value(f.id).trim(); }).map(function (f) { return f.label; }); }
  function totalWords() { return FIELDS.reduce(function (n, f) { return n + countWords(value(f.id)); }, 0); }
  function rangeText() { return WORDS.min + "–" + WORDS.max; }

  function runChecks() {
    var out = [];
    var blank = blankLabels();
    var total = totalWords();
    out.push({
      id: "fields", severity: blank.length ? "bad" : "ok",
      message: blank.length
        ? "Still empty: " + blank.join(", ") + ". A case is not a case until all four are answered."
        : "All four parts of the case are answered."
    });
    if (total === 0) return out;
    var inRange = total >= WORDS.min && total <= WORDS.max;
    out.push({
      id: "length", severity: inRange ? "ok" : (total < WORDS.min ? "bad" : "warn"),
      message: inRange
        ? total + " words, inside " + rangeText() + "."
        : total < WORDS.min
          ? total + " words. The brief asks for " + rangeText() + "; under that, a case is usually a sketch of one."
          : total + " words, over " + WORDS.max + ". Nothing is truncated, but the extra is rarely the case and usually the discussion."
    });
    var failure = value("failure");
    if (failure.trim()) {
      var excluded = [];
      if (UNTRUE.test(failure)) excluded.push("the allegation being false or mistaken");
      if (FORBIDDEN.test(failure)) excluded.push("reporting being forbidden");
      if (IGNORED.test(failure)) excluded.push("the verifier ignoring it");
      out.push({
        id: "excluded", severity: excluded.length ? "warn" : "ok",
        message: excluded.length
          ? "Your failure point reads as " + excluded.join(", or ") + ". The brief rules those out: condition 1 says the allegation is accurate and condition 2 says the disclosure is permitted, so a failure that contradicts them is a different case. (Looked for words like lied, false, forbidden, ignored.)"
          : "The failure does not rest on the allegation being false, on reporting being forbidden, or on the verifier ignoring it."
      });
      out.push({
        id: "mechanism", severity: MECHANISM.test(failure) ? "ok" : "warn",
        message: MECHANISM.test(failure)
          ? "The failure point gives a reason, not only a verdict."
          : "The failure point may be a verdict rather than a mechanism. Looked for because / cannot / has no / outside / belongs to / requires. Say what stops the report, not that it stopped."
      });
    }
    var info = value("information");
    if (info.trim()) {
      out.push({
        id: "how-known", severity: HOW_KNOWN.test(info) ? "ok" : "warn",
        message: HOW_KNOWN.test(info)
          ? "The information says how the insider knows it."
          : "It may not say how the insider knows. Looked for saw / read / ran / signed / processed / was told / has access. What they know and how they know it are two different claims."
      });
    }
    if (failure.trim() && (value("insider").trim() || info.trim())) {
      var source = wordSet(value("insider") + " " + info);
      var shared = Object.keys(wordSet(failure)).filter(function (w) { return source[w]; });
      out.push({
        id: "consistency", severity: shared.length ? "ok" : "warn",
        message: shared.length
          ? "The failure is about this case: it reuses " + shared.slice(0, 3).join(", ") + "."
          : "The failure may not be about this case. Rough check: it shares no substantive word with the insider or the information. A failure that would read the same under any case is usually a generality."
      });
    }
    return out;
  }

  // ---- state ----
  var state = { values: {}, submitted: false, ticked: [] };
  var completed = false;
  var lastCard = -1;
  var card = null;
  var lastResponseId = null;
  var scoreText = "";
  var scoring = false;
  var textareas = {};

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }
  function started() { return FIELDS.some(function (f) { return value(f.id).trim(); }); }
  function complete() { return FIELDS.every(function (f) { return value(f.id).trim(); }); }
  function keyTotal() { return KEY.criteria.reduce(function (s, c) { return s + c.points; }, 0); }
  function selfScore() { return state.ticked.reduce(function (s, i) { return s + (KEY.criteria[i] ? KEY.criteria[i].points : 0); }, 0); }

  function summary() {
    var parts = ["Insider Report, construct a case. Status: " + (state.submitted ? "submitted (boxes frozen, marking key revealed)" : (started() ? "draft in progress" : "nothing written yet")) + "."];
    parts.push("Total " + totalWords() + " words (brief asks for " + rangeText() + ").");
    FIELDS.forEach(function (f) { parts.push(f.label + ": " + (value(f.id).trim() || "(empty)")); });
    var flags = runChecks().filter(function (c) { return c.severity !== "ok"; }).map(function (c) { return c.message; });
    if (flags.length) parts.push("Desk checks flagged: " + flags.join(" "));
    if (state.submitted) parts.push("Self-marked " + selfScore() + " of " + keyTotal() + " on the marking key" + (state.ticked.length ? " (ticked: " + state.ticked.slice().sort().map(function (i) { return KEY.criteria[i] ? KEY.criteria[i].text : ""; }).join(" | ") + ")" : "") + ".");
    if (scoreText) parts.push("AI assessor: " + scoreText);
    return parts.join(" ");
  }

  function persist() {
    var snapshot = { values: state.values, submitted: state.submitted, ticked: state.ticked };
    if (window.Lens) {
      Lens.saveState(snapshot, summary());
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snapshot)); } catch (e) {}
    }
  }

  // ---- static build ----
  var fieldsEl = document.getElementById("fields");
  var fieldBoxes = {};
  var fieldFlags = {};
  FIELDS.forEach(function (f) {
    var box = el("div", "field");
    var label = el("label", null, f.label);
    label.htmlFor = "f-" + f.id;
    var flag = el("span", "flag", "");
    label.appendChild(flag);
    fieldBoxes[f.id] = box;
    fieldFlags[f.id] = flag;
    var ta = document.createElement("textarea");
    ta.id = "f-" + f.id;
    ta.rows = f.rows;
    ta.addEventListener("input", function () {
      if (state.submitted) return;
      state.values[f.id] = ta.value;
      renderForm();
      renderChecks();
      persist();
    });
    textareas[f.id] = ta;
    box.appendChild(label);
    box.appendChild(ta);
    fieldsEl.appendChild(box);
  });

  var countEl = document.getElementById("count");
  var submitBtn = document.getElementById("submit");
  var resetBtn = document.getElementById("reset");
  var checksEl = document.getElementById("checks");
  var checkList = document.getElementById("check-list");
  var deckEl = document.getElementById("deck");
  var cardEl = document.getElementById("card");
  var drawBtn = document.getElementById("draw");
  var revealEl = document.getElementById("reveal");

  function renderForm() {
    FIELDS.forEach(function (f) {
      var ta = textareas[f.id];
      if (ta.value !== value(f.id)) ta.value = value(f.id);
      ta.readOnly = state.submitted;
    });
    countEl.textContent = totalWords() + " words · aim for " + rangeText();
    submitBtn.hidden = state.submitted;
    submitBtn.disabled = !complete();
    resetBtn.hidden = !state.submitted;
  }

  // Which box each desk check is about, so the mark lands on the box and not only in the list.
  var CHECK_FIELD = { excluded: "failure", mechanism: "failure", consistency: "failure", "how-known": "information" };

  function renderChecks() {
    var show = started() && !state.submitted;
    checksEl.hidden = !show;
    deckEl.hidden = !show;
    FIELDS.forEach(function (f) {
      fieldBoxes[f.id].classList.remove("is-flagged");
      fieldFlags[f.id].textContent = "";
    });
    if (!show) return;
    clear(checkList);
    var MARK = { ok: "✓", warn: "!", bad: "✗" };
    var NAME = { ok: "passes", warn: "warning", bad: "fails" };
    var flagged = {};
    runChecks().forEach(function (row) {
      var target = CHECK_FIELD[row.id];
      if (target && row.severity !== "ok") flagged[target] = (flagged[target] || 0) + 1;
      var line = el("p", "check " + row.severity);
      var mark = el("span", "mark", MARK[row.severity]);
      mark.setAttribute("aria-label", NAME[row.severity]);
      line.appendChild(mark);
      line.appendChild(el("span", null, row.message));
      checkList.appendChild(line);
    });
    Object.keys(flagged).forEach(function (id) {
      if (!fieldBoxes[id]) return;
      fieldBoxes[id].classList.add("is-flagged");
      fieldFlags[id].textContent = flagged[id] === 1 ? "1 desk check to answer" : flagged[id] + " desk checks to answer";
    });
  }

  function renderDeck() {
    cardEl.textContent = card === null ? "Draw a challenge and answer it in what you are writing." : card;
    cardEl.classList.toggle("is-drawn", card !== null);
    drawBtn.textContent = card === null ? "Draw a challenge" : "Draw another";
  }

  function draw() {
    if (!DECK.length) return;
    var i = lastCard;
    if (DECK.length > 1) {
      do { i = Math.floor(Math.random() * DECK.length); } while (i === lastCard);
    } else {
      i = 0;
    }
    lastCard = i;
    card = DECK[i];
    renderDeck();
  }

  function panel(eyebrow, aside) {
    var s = el("section", "panel");
    var head = el("div", "panel-head");
    head.appendChild(el("p", "eyebrow", eyebrow));
    if (aside) head.appendChild(el("p", "aside", aside));
    s.appendChild(head);
    return s;
  }

  function renderReveal() {
    revealEl.hidden = !state.submitted;
    clear(revealEl);
    if (!state.submitted) return;
    var stack = el("div", "stack");

    // Marking key
    var key = panel("Marking key", selfScore() + " / " + keyTotal());
    var scoreLine = key.querySelector(".aside");
    scoreLine.setAttribute("aria-live", "polite");
    var intro = el("p", "muted", KEY_INTRO);
    intro.style.marginTop = "8px";
    key.appendChild(intro);
    var list = el("ul", "key-list");
    KEY.criteria.forEach(function (c, i) {
      var li = el("li");
      var on = state.ticked.indexOf(i) !== -1;
      var btn = el("button", "crit" + (on ? " is-on" : ""));
      btn.type = "button";
      btn.setAttribute("aria-pressed", on ? "true" : "false");
      btn.appendChild(el("span", "pts", String(c.points)));
      var body = el("span");
      body.appendChild(el("span", null, c.text));
      if (c.needsReasoning) body.appendChild(el("span", "sub", NEEDS_REASONING));
      if (c.grounds) body.appendChild(el("span", "sub", c.grounds));
      btn.appendChild(body);
      btn.appendChild(el("span", "tick", "✓ credited"));
      btn.addEventListener("click", function () {
        var at = state.ticked.indexOf(i);
        if (at === -1) state.ticked.push(i); else state.ticked.splice(at, 1);
        renderReveal();
        persist();
      });
      li.appendChild(btn);
      list.appendChild(li);
    });
    key.appendChild(list);
    var nc = el("div");
    nc.style.marginTop = "12px";
    nc.appendChild(el("p", "eyebrow", "No credit"));
    var ncList = el("ul", "plain muted");
    KEY.noCredit.forEach(function (line) { ncList.appendChild(el("li", null, line)); });
    nc.appendChild(ncList);
    key.appendChild(nc);
    var foot = el("p", "muted small", KEY_FOOT);
    foot.style.marginTop = "12px";
    key.appendChild(foot);

    // AI scoring (Lens only)
    if (window.Lens && Lens.submit) {
      var scoreBox = el("div");
      scoreBox.style.marginTop = "12px";
      var status = el("p", "status small", scoreText || "Or send the four boxes to the AI assessor, which marks against the same key.");
      status.setAttribute("aria-live", "polite");
      var row = el("div", "score-row");
      var scoreBtn = el("button", null, lastResponseId ? "Score again" : "Score my case");
      scoreBtn.type = "button";
      scoreBtn.disabled = scoring;
      scoreBtn.addEventListener("click", scoreCase);
      row.appendChild(scoreBtn);
      if (lastResponseId) {
        var fb = el("button", null, "Get feedback on the score");
        fb.type = "button";
        fb.addEventListener("click", function () {
          if (window.Lens && Lens.requestFeedback && lastResponseId) Lens.requestFeedback(lastResponseId, "Can I get feedback on my case?");
        });
        row.appendChild(fb);
      }
      scoreBox.appendChild(status);
      scoreBox.appendChild(row);
      key.appendChild(scoreBox);
    }
    stack.appendChild(key);

    revealEl.appendChild(stack);
  }

  function answerText() {
    return FIELDS.map(function (f) { return f.label + ": " + value(f.id).trim(); }).join("\n");
  }

  function scoreCase() {
    if (!window.Lens || !Lens.submit || scoring) return;
    scoring = true;
    scoreText = "Scoring your case…";
    renderReveal();
    var criteria = KEY.criteria.map(function (c, i) {
      return (i + 1) + ". (" + c.points + " point) " + c.text +
        (c.needsReasoning ? " " + NEEDS_REASONING : "") +
        (c.grounds ? " Grounds: " + c.grounds : "");
    });
    Lens.submit({
      item: "case",
      question: "Give one example of a situation in which all three conditions are satisfied: " + CONDITIONS.map(function (c, i) { return "(" + (i + 1) + ") " + c; }).join(" ") + " Describe the situation and explain why each condition is satisfied. Use " + rangeText() + " words in total. Answer in four parts: Insider, Information, Reporting route, Failure point.",
      answer: answerText(),
      assessmentInstructions: "Marking key, " + keyTotal() + " points in total, one criterion at a time; report the score as points earned multiplied by " + (100 / keyTotal()) + " (0 to 100). " + KEY_INTRO + " Criteria: " + criteria.join(" ") + " No credit: " + KEY.noCredit.join(" "),
      feedbackInstructions: "Check the case against these questions and say which it fails: " + CHECKLIST.join(" ")
    }).then(function (result) {
      scoring = false;
      lastResponseId = result && result.responseId ? result.responseId : lastResponseId;
      scoreText = (result && result.score != null)
        ? "AI assessor score: " + result.score + " / 100, marked against the same key."
        : "Scoring is taking a while; ask the tutor for feedback meanwhile.";
      renderReveal();
      persist();
    }, function () {
      scoring = false;
      scoreText = "Could not score the case right now.";
      renderReveal();
    });
  }

  submitBtn.addEventListener("click", function () {
    if (state.submitted || !complete()) return;
    state.submitted = true;
    state.ticked = [];
    renderAll();
    persist();
    if (!completed) {
      completed = true;
      if (window.Lens) Lens.complete();
    }
  });

  resetBtn.addEventListener("click", function () {
    state = { values: {}, submitted: false, ticked: [] };
    card = null; lastCard = -1; scoreText = ""; lastResponseId = null;
    renderAll();
    persist();
    if (textareas.insider) textareas.insider.focus();
  });

  drawBtn.addEventListener("click", draw);

  function renderAll() {
    renderForm();
    renderChecks();
    renderDeck();
    renderReveal();
  }

  function hydrate(saved, meta) {
    var next = { values: {}, submitted: false, ticked: [] };
    if (saved && typeof saved === "object") {
      if (saved.values && typeof saved.values === "object") {
        FIELDS.forEach(function (f) { var v = saved.values[f.id]; if (typeof v === "string") next.values[f.id] = v; });
      }
      next.submitted = saved.submitted === true && FIELDS.every(function (f) { return String(next.values[f.id] || "").trim(); });
      if (next.submitted && Array.isArray(saved.ticked)) {
        next.ticked = saved.ticked.filter(function (n) { return typeof n === "number" && n >= 0 && n < KEY.criteria.length; });
      }
    }
    state = next;
    completed = !!(meta && meta.completed);
    renderAll();
  }

  renderAll();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = localStorage.getItem(STORAGE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
</script>
</body>
</html>

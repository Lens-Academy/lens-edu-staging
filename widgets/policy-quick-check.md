---
id: '62029e7d-7224-488b-be6b-b89a8978909f'
title: On Paper (Policy Quick Check)
summary_for_tutor: "A five-question single-answer check from XLab's Verification track (the live On Paper exercise). Each question gives a fact pattern, some as a list (four employees of a frontier developer and who is a covered employee; an internal anonymous reporting process that still sends quarterly disclosures to an accused director; a proposed whistleblowing law and which amendment package matches the AIWI/CARMA Best Practice Guide; a safety researcher with mixed motives whose duty-speech concern is later unsubstantiated; an investigator weighing screenshots, two witnesses and a legal-team summary under the CIGIE Quality Standards for Investigations 2025), then one question with four options in a fixed seeded order. Nothing is marked until all five are answered and the learner presses Check all five; then every question shows Correct or Not quite, XLab's explanation and the source line (California Labor Code 1107(b), 1107.1(a), 1107.1(e)(1) to (2); AIWI/CARMA Protected Individuals, Disclosure Channels, Scope of Protected Disclosures; CIGIE Complaint Evaluation, Executing Investigations, Collecting Evidence, Reporting), with the total out of 5. Done means the set has been checked; Start over clears it. The saved-state summary tells you which option the learner picked on each question and, after the check, which were wrong. When coaching, point to the one legally or institutionally material condition the chosen distractor misses, using the source named under the question."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>On Paper (Policy Quick Check)</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "human-reporting-protection" (live component PolicyQuickCheck). -->
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
  p { margin: 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .lede { color: var(--muted); margin: 6px 0 20px; max-width: 46rem; }
  ol.questions { list-style: none; margin: 0; padding: 0; }
  ol.questions > li + li { margin-top: 24px; padding-top: 24px; border-top: 1px solid var(--border); }
  .q-head { display: flex; flex-wrap: wrap; align-items: baseline; justify-content: space-between; gap: 4px 12px; }
  .q-head h3 { font-size: 18px; }
  .verdict { font-size: 12px; font-weight: 600; letter-spacing: 0.04em; }
  .verdict.right { color: var(--accent); }
  .verdict.wrong { color: var(--text); }
  .fragment { margin-top: 8px; padding-left: 12px; border-left: 2px solid var(--border); }
  .fragment p + ul, .fragment ul + p, .fragment p + p { margin-top: 8px; }
  .fragment ul { margin: 0; padding-left: 20px; }
  .fragment li + li { margin-top: 4px; }
  .stem { margin-top: 12px; font-weight: 500; }
  .choices { display: grid; gap: 6px; margin-top: 12px; }
  .choice {
    font: inherit; color: inherit; text-align: left; cursor: pointer; width: 100%;
    display: flex; gap: 10px; align-items: flex-start;
    border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px;
  }
  .choice:hover { background: var(--surface); }
  .choice:disabled { cursor: default; }
  .choice:disabled:hover { background: #fff; }
  .choice:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .choice .slot { color: var(--muted); font-weight: 500; flex: 0 0 auto; }
  .choice .glyph { flex: 0 0 18px; width: 18px; height: 18px; border-radius: 50%; border: 1px solid var(--border); font-size: 11px; line-height: 16px; text-align: center; margin-top: 2px; }
  .choice.is-chosen { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: #fdf8f1; }
  .choice.is-chosen .glyph { border-color: var(--accent); background: var(--accent); color: #fff; }
  .choice.is-right { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: #fdf8f1; }
  .choice.is-right .glyph { border-color: var(--accent); background: var(--accent); color: #fff; }
  .choice.is-wrong { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .choice.is-wrong .glyph { border-color: var(--text); background: var(--text); color: #fff; }
  .choice.is-dim { opacity: 0.55; }
  .choice .tag { margin-left: auto; font-size: 11px; white-space: nowrap; color: var(--muted); flex: 0 0 auto; }
  .explain { margin-top: 12px; color: var(--muted); }
  .source { margin-top: 6px; font-size: 12px; color: var(--muted); }
  .source strong { font-weight: 500; }
  .row { display: flex; flex-wrap: wrap; gap: 8px 16px; align-items: center; justify-content: space-between; margin-top: 24px; padding-top: 16px; border-top: 1px solid var(--border); }
  .status { font-size: 12px; color: var(--muted); }
  .status.done { font-size: 14px; color: var(--text); font-weight: 500; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  [hidden] { display: none !important; }
</style>
</head>
<body>
<p class="eyebrow">On Paper &middot; 7&ndash;10 minutes</p>
<p class="lede">Below are five fragments of internal whistleblower policies. Each fragment is followed by one question about what the quoted language does, and does not, establish. For each question, choose the one best answer. The answers are revealed after you submit the whole set.</p>

<ol class="questions" id="questions"></ol>

<div class="row">
  <p class="status" id="status" aria-live="polite"></p>
  <span>
    <button type="button" id="check" class="primary">Check all five</button>
    <button type="button" id="reset" hidden>Start over</button>
  </span>
</div>

<script>
  var QUESTIONS = [
    {
      id: "covered-employee",
      fragment: "A frontier developer employs four people:",
      facts: [
        "Nora, a safety engineer responsible for assessing critical safety incidents;",
        "Leon, a software engineer with no responsibility for assessing, managing, or addressing such risks;",
        "Maya, an outside contractor conducting an evaluation for the developer;",
        "Sam, a safety engineer responsible for critical-risk assessment."
      ],
      fragmentAfter: "Nora has reasonable cause to believe that the developer’s activities create a specific and substantial danger to public safety resulting from a catastrophic risk. Leon has the same belief. Maya has the same belief. Sam merely disagrees with management’s general research strategy and does not believe that either a qualifying danger or a violation of the relevant chapter has occurred.",
      stem: "Which disclosure is protected by **California Labor Code §1107.1(a)** on the facts stated?",
      choices: [
        { id: "a", text: "Nora reports the concern to the California Attorney General." },
        { id: "b", text: "Leon reports the concern to a federal authority." },
        { id: "c", text: "Maya reports the concern to the California Attorney General." },
        { id: "d", text: "Sam reports his disagreement to another safety engineer authorized to investigate internal concerns." }
      ],
      answerId: "a",
      explanation: "§1107 defines a “covered employee” as an employee responsible for assessing, managing, or addressing risk of critical safety incidents. §1107.1(a) protects disclosures by such a covered employee to specified recipients when the employee has reasonable cause to believe the information discloses either a qualifying public-safety danger resulting from catastrophic risk or a violation of the specified chapter. Nora satisfies the status, subject-matter, belief, and recipient conditions. Leon is an employee but is not a “covered employee” under the definition given. Maya is an outside contractor, not a covered employee under §1107 itself. Sam is a covered employee and uses a named type of recipient, but the stated subject matter does not satisfy §1107.1(a).",
      source: "California Labor Code §§1107(b), 1107.1(a)."
    },
    {
      id: "internal-process",
      fragment: "A large frontier developer creates the following internal process:",
      facts: [
        "covered employees may file reports anonymously;",
        "the reporter receives a status update every month;",
        "disclosures and responses are shared with the company’s officers and directors every quarter;",
        "if a report alleges wrongdoing by a particular director, that director still receives the quarterly disclosure because all directors must receive the same information."
      ],
      stem: "Which assessment is most accurate under **§1107.1(e)**?",
      choices: [
        { id: "a", text: "The process satisfies the statute because anonymity, monthly updates, and quarterly board-level reporting are all present." },
        { id: "b", text: "The process fails because the statute requires the internal channel to be administered by an external organization." },
        { id: "c", text: "The process fails because a director accused of wrongdoing should not receive the disclosure or response concerning that allegation." },
        { id: "d", text: "The process fails because reports must be sent to officers and directors immediately rather than quarterly." }
      ],
      answerId: "c",
      explanation: "For a large frontier developer, §1107.1(e) requires a reasonable anonymous internal process, monthly updates to the person who made the disclosure, and quarterly sharing of disclosures and responses with officers and directors. But the statute expressly creates an exception where a disclosure or response alleges wrongdoing by an officer or director: the sharing requirement does not apply with respect to that person. The statute does not require an external administrator for this internal process, and quarterly, not immediate, sharing is what the provision specifies.",
      source: "California Labor Code §1107.1(e)(1)–(2)."
    },
    {
      id: "amendment-package",
      fragment: "A proposed AI whistleblowing law has the following features:",
      facts: [
        "employees may report concerns internally to their manager;",
        "the company offers an anonymous internal reporting form administered by the legal department;",
        "retaliation for protected disclosures is prohibited;",
        "employees may confidentially report violations to a regulator, but the external channel does not accept anonymous reports;",
        "contractors, outside evaluators, and former employees are not protected."
      ],
      stem: "Which amendment package most closely matches the **AIWI/CARMA Best Practice Guide**?",
      choices: [
        { id: "a", text: "Keep the protected-person category unchanged, move the internal channel outside executive management and legal, and permit anonymous external reports to relevant authorities." },
        { id: "b", text: "Extend protection to contractors, evaluators, and former employees; make the internal channel independent of executive management and legal; and permit confidential and anonymous external reporting to relevant authorities." },
        { id: "c", text: "Extend protection to contractors and former employees, but require all disclosures to begin internally before any external authority may receive them." },
        { id: "d", text: "Keep the internal channel under the legal department, extend protection to contractors and evaluators, and replace anonymous reporting with stronger penalties for retaliation." }
      ],
      answerId: "b",
      explanation: "The Guide recommends a broader protected-person category that includes third-party evaluators, contractors, former employees, and others. It recommends that the anonymous/confidential internal process be independent of executive management and the legal team, preferably with board governance. It also recommends that covered persons be able to report confidentially and anonymously to relevant external authorities. The other packages each preserve at least one feature that conflicts with those recommendations.",
      source: "AIWI/CARMA, “Protected Individuals” and “Disclosure Channels.”"
    },
    {
      id: "reasonable-belief",
      fragment: "A safety researcher raises a concern as part of her ordinary job duties. She reasonably believes the concern is true. Her motivation is mixed: she believes the issue is important, but she is also angry about a recent promotion decision. Six months later, an investigation cannot substantiate the underlying concern.",
      stem: "Which statement best reflects the **AIWI/CARMA Best Practice Guide**?",
      choices: [
        { id: "a", text: "The disclosure should lose protection because the concern was not ultimately substantiated." },
        { id: "b", text: "The disclosure should lose protection because reporting the concern was already part of the researcher’s job." },
        { id: "c", text: "Protection should not turn on the researcher’s motive, the fact that the disclosure was duty speech, or later failure to substantiate the allegation, provided the reasonable-belief standard was satisfied." },
        { id: "d", text: "Protection should depend on whether the researcher can prove that safety rather than the promotion dispute was her primary motive." }
      ],
      answerId: "c",
      explanation: "The Guide recommends a reasonable-belief standard rather than requiring the disclosure ultimately to prove correct. It also recommends protecting disclosures regardless of motive and explicitly protecting “duty speech”, concerns raised as part of the employee’s ordinary work. The other answers each make protection depend on a condition the Guide recommends excluding.",
      source: "AIWI/CARMA, “Scope of Protected Disclosures.”"
    },
    {
      id: "investigation-standard",
      fragment: "An investigator receives a credible allegation that an AI developer concealed a prohibited training run. The complainant provides screenshots and names two witnesses. The developer supplies a summary prepared by its legal team but refuses access to the underlying records. One witness supports the allegation; the other provides information tending to exculpate the developer.",
      stem: "Which course of action is most consistent with the **CIGIE Quality Standards for Investigations (2025)**?",
      choices: [
        { id: "a", text: "Treat the credible complaint and supporting witness as sufficient for a finding, because complaint evaluation occurs before full evidence collection." },
        { id: "b", text: "Obtain and analyze relevant evidence lawfully, seek to verify the validity of the information, preserve required evidentiary integrity, include relevant exculpatory material, and limit the final report to findings supported by the case file." },
        { id: "c", text: "Exclude the exculpatory witness from the final report because the investigator’s task is to determine whether the original allegation can be substantiated." },
        { id: "d", text: "Accept the developer’s legal-team summary in place of the underlying records because evidence supplied by counsel has already undergone internal review." }
      ],
      answerId: "b",
      explanation: "CIGIE requires objective investigation of allegations, including receptiveness to both incriminating and exculpatory evidence. Relevant evidence must be lawfully obtained, its validity should be verified, and chain-of-custody/admissibility requirements must be preserved where applicable. Reports must be supported by evidence and documentation in the case file and include relevant exculpatory or mitigating information. A credible allegation can justify investigative activity; it is not itself a final finding. The Standards do not permit investigators to omit exculpatory evidence or substitute an interested party’s summary for needed underlying evidence merely because counsel prepared it.",
      source: "CIGIE, Quality Standards for Investigations (2025): Complaint Evaluation; Executing Investigations; Collecting Evidence; Reporting."
    }
  ];

  var STORAGE_KEY = "lens-widget-policy-quick-check";
  var SLOT = "ABCDEFGH";

  // ---- seeded shuffle, ported from XLab's src/lib/shuffle.ts ----
  // Same seed (the question id), same order, every learner, every visit.
  function hashSeed(seed) {
    var h = 0x811c9dc5;
    for (var i = 0; i < seed.length; i++) {
      h ^= seed.charCodeAt(i);
      h = Math.imul(h, 0x01000193);
    }
    return h >>> 0;
  }
  function prng(state) {
    return function () {
      state = (state + 0x6d2b79f5) | 0;
      var t = state;
      t = Math.imul(t ^ (t >>> 15), t | 1);
      t ^= t + Math.imul(t ^ (t >>> 7), t | 61);
      return ((t ^ (t >>> 14)) >>> 0) / 4294967296;
    };
  }
  function seededPermutation(seed, n) {
    var order = [];
    for (var k = 0; k < n; k++) order.push(k);
    var rand = prng(hashSeed(seed));
    for (var i = n - 1; i > 0; i--) {
      var j = Math.floor(rand() * (i + 1));
      var tmp = order[i]; order[i] = order[j]; order[j] = tmp;
    }
    return order;
  }
  function isTerminalOption(text) {
    return /^\s*(none|all|any|neither|both|either)\s+of\s+(the\s+)?(above|these|them)\b/i.test(text);
  }
  function isBinaryPair(texts) {
    if (texts.length !== 2) return false;
    var pair = texts.map(function (t) { return t.trim().toLowerCase().replace(/[.?!]$/, ""); });
    return (pair[0] === "true" && pair[1] === "false") || (pair[0] === "false" && pair[1] === "true") ||
      (pair[0] === "yes" && pair[1] === "no") || (pair[0] === "no" && pair[1] === "yes");
  }
  function seededShuffle(seed, items, pinned) {
    var n = items.length;
    var plain = items.map(function (item, from) { return { item: item, from: from }; });
    if (n < 2) return plain;
    var fixed = items.map(pinned);
    var movable = [];
    for (var i = 0; i < n; i++) if (!fixed[i]) movable.push(i);
    if (movable.length < 2) return plain;
    var perm = seededPermutation(seed, movable.length);
    var reordered = perm.map(function (p) { return movable[p]; });
    var out = [];
    var next = 0;
    for (var slot = 0; slot < n; slot++) {
      var from = fixed[slot] ? slot : reordered[next++];
      out.push({ item: items[from], from: from });
    }
    return out;
  }
  function shuffleAnswerOptions(seed, items) {
    if (isBinaryPair(items.map(function (c) { return c.text; }))) {
      return items.map(function (item, from) { return { item: item, from: from }; });
    }
    return seededShuffle(seed, items, function (item) { return isTerminalOption(item.text); });
  }

  // ---- state ----
  var state = { picks: {}, submitted: false };
  var completed = false;
  var shown = QUESTIONS.map(function (q) {
    return { question: q, choices: shuffleAnswerOptions(q.id, q.choices).map(function (s) { return s.item; }) };
  });

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }
  // **bold** runs become <strong>, everything else text nodes (XLab's splitEmphasis).
  function rich(target, source) {
    var re = /\*\*([^]+?)\*\*/g;
    var at = 0, m;
    while ((m = re.exec(source)) !== null) {
      if (m.index > at) target.appendChild(document.createTextNode(source.slice(at, m.index)));
      var strong = el("strong", null, m[1]);
      strong.style.fontWeight = "600";
      target.appendChild(strong);
      at = m.index + m[0].length;
    }
    if (at < source.length) target.appendChild(document.createTextNode(source.slice(at)));
    return target;
  }
  function choiceById(q, id) {
    for (var i = 0; i < q.choices.length; i++) if (q.choices[i].id === id) return q.choices[i];
    return null;
  }
  function answered() { return QUESTIONS.filter(function (q) { return !!state.picks[q.id]; }).length; }
  function right() { return QUESTIONS.filter(function (q) { return state.picks[q.id] === q.answerId; }).length; }

  function summary() {
    var parts = ["On Paper, five single-answer questions. " + (state.submitted
      ? "Checked: " + right() + " of " + QUESTIONS.length + " correct."
      : answered() + " of " + QUESTIONS.length + " answered, not yet checked.")];
    QUESTIONS.forEach(function (q, i) {
      var pick = choiceById(q, state.picks[q.id]);
      var line = "Q" + (i + 1) + " (" + q.id + "): ";
      if (!pick) line += "no answer yet.";
      else {
        line += "picked “" + pick.text + "”";
        if (state.submitted) line += pick.id === q.answerId ? " (correct)." : " (not quite; the answer is “" + choiceById(q, q.answerId).text + "”).";
        else line += ".";
      }
      parts.push(line);
    });
    return parts.join(" ");
  }

  function persist() {
    var snapshot = { picks: state.picks, submitted: state.submitted };
    if (window.Lens) {
      Lens.saveState(snapshot, summary());
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snapshot)); } catch (e) {}
    }
  }

  var listEl = document.getElementById("questions");
  var statusEl = document.getElementById("status");
  var checkBtn = document.getElementById("check");
  var resetBtn = document.getElementById("reset");

  function render() {
    clear(listEl);
    shown.forEach(function (entry, index) {
      var q = entry.question;
      var pick = state.picks[q.id] || null;
      var correct = pick === q.answerId;
      var li = el("li");

      var head = el("div", "q-head");
      head.appendChild(el("h3", null, "Question " + (index + 1) + "/" + QUESTIONS.length));
      if (state.submitted) {
        head.appendChild(el("p", "verdict " + (correct ? "right" : "wrong"), (correct ? "✓ Correct" : "✗ Not quite")));
      }
      li.appendChild(head);

      var frag = el("div", "fragment");
      frag.appendChild(rich(el("p"), q.fragment));
      if (q.facts) {
        var ul = el("ul");
        q.facts.forEach(function (f) { ul.appendChild(rich(el("li"), f)); });
        frag.appendChild(ul);
      }
      if (q.fragmentAfter) frag.appendChild(rich(el("p"), q.fragmentAfter));
      li.appendChild(frag);

      li.appendChild(rich(el("p", "stem"), q.stem));

      var group = el("div", "choices");
      group.setAttribute("role", "radiogroup");
      group.setAttribute("aria-label", q.stem.replace(/\*\*/g, ""));
      entry.choices.forEach(function (choice, slot) {
        var chosen = pick === choice.id;
        var isAnswer = choice.id === q.answerId;
        var btn = el("button", "choice");
        btn.type = "button";
        btn.setAttribute("role", "radio");
        btn.setAttribute("aria-checked", chosen ? "true" : "false");
        btn.disabled = state.submitted;
        var glyph = el("span", "glyph", "");
        if (!state.submitted) {
          if (chosen) { btn.classList.add("is-chosen"); glyph.textContent = "●"; }
        } else {
          if (isAnswer) { btn.classList.add("is-right"); glyph.textContent = "✓"; }
          else if (chosen) { btn.classList.add("is-wrong"); glyph.textContent = "✗"; }
          else btn.classList.add("is-dim");
        }
        btn.appendChild(glyph);
        btn.appendChild(el("span", "slot", SLOT[slot] + "."));
        btn.appendChild(rich(el("span"), choice.text));
        if (state.submitted && isAnswer) btn.appendChild(el("span", "tag", chosen ? "your answer, correct" : "correct answer"));
        else if (state.submitted && chosen) btn.appendChild(el("span", "tag", "your answer"));
        btn.addEventListener("click", function () {
          if (state.submitted) return;
          state.picks[q.id] = choice.id;
          render();
          persist();
        });
        group.appendChild(btn);
      });
      li.appendChild(group);

      if (state.submitted) {
        li.appendChild(rich(el("p", "explain"), q.explanation));
        var src = el("p", "source");
        src.appendChild(el("strong", null, "Source: "));
        src.appendChild(document.createTextNode(q.source));
        li.appendChild(src);
      }
      listEl.appendChild(li);
    });

    statusEl.textContent = state.submitted
      ? right() + " of " + QUESTIONS.length + "."
      : answered() + " of " + QUESTIONS.length + " answered.";
    statusEl.classList.toggle("done", state.submitted);
    checkBtn.hidden = state.submitted;
    checkBtn.disabled = answered() < QUESTIONS.length;
    resetBtn.hidden = !state.submitted;
  }

  checkBtn.addEventListener("click", function () {
    if (state.submitted || answered() < QUESTIONS.length) return;
    state.submitted = true;
    render();
    persist();
    if (!completed) {
      completed = true;
      if (window.Lens) Lens.complete();
    }
  });

  resetBtn.addEventListener("click", function () {
    state = { picks: {}, submitted: false };
    render();
    persist();
    var first = listEl.querySelector("button");
    if (first) first.focus();
  });

  function hydrate(saved, meta) {
    var next = { picks: {}, submitted: false };
    if (saved && typeof saved === "object" && saved.picks && typeof saved.picks === "object") {
      QUESTIONS.forEach(function (q) {
        var pick = saved.picks[q.id];
        if (typeof pick === "string" && choiceById(q, pick)) next.picks[q.id] = pick;
      });
      next.submitted = saved.submitted === true && QUESTIONS.every(function (q) { return !!next.picks[q.id]; });
    }
    state = next;
    completed = !!(meta && meta.completed);
    render();
  }

  render();
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

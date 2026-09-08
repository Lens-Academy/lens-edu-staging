---
id: '315855e1-219e-4688-a9a8-26bdd8fa2c8f'
title: "Drill Bench: Primers"
summary_for_tutor: "A six-step drill bench on the game-theory primers (inspection games, credible commitment, Putnam's two-level game, Fearon's commitment devices, one nine-term sorting drill, one syllogism). Each step is commit-then-reveal: the learner picks an answer (or marks exactly three terms in the sorting step), the widget shows which option was the key and a short explanation, and only then can they press Continue. Nothing is scored; the reveal is the lesson. The widget-state summary tells you which steps are done, what the learner picked, and whether each pick matched the key. Done means all six steps have been committed and continued through (the bench then shows a finish screen with a Redo option). If the learner asks about a step, use the explanation text in the state summary; do not reveal the key for a step they have not committed yet."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Drill Bench: Primers</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "drills-primers". -->
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
  .panel { border: 1px solid var(--border); border-radius: 8px; padding: 20px; background: #fff; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 24px; line-height: 1.2; margin: 4px 0 8px; }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; line-height: 1.3; margin: 0; }
  p { margin: 0; }
  .muted { color: var(--muted); }
  .stack > * + * { margin-top: 14px; }
  .head-row { display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 8px; }
  .meter { display: flex; gap: 2px; height: 6px; max-width: 176px; border-radius: 999px; overflow: hidden; margin-top: 8px; }
  .meter span { flex: 1 1 0; min-width: 0; background: var(--border); }
  .meter span.is-filled { background: var(--accent); }
  .brief { border: 1px solid var(--border); background: var(--surface); border-radius: 8px; padding: 12px; }
  blockquote.statement { margin: 0; border: 1px solid var(--border); border-radius: 8px; padding: 12px; font-style: italic; }
  ul.list { list-style: none; margin: 0; padding: 0; }
  ul.list li + li { margin-top: 8px; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button:disabled { cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; font-weight: 500; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled { opacity: 0.5; }
  button.primary:disabled:hover { background: var(--accent); }
  button.ghost { border-color: transparent; color: var(--muted); }
  .bench-card { display: block; width: 100%; padding: 12px; }
  .bench-card .name { font-weight: 500; }
  .bench-card .badge { display: inline-block; margin-left: 8px; font-size: 11px; color: var(--accent); font-weight: 500; }
  .bench-card .kicker { display: block; margin-top: 4px; color: var(--muted); }
  .bench-card .count { display: block; margin-top: 6px; font-size: 11px; letter-spacing: 0.06em; color: var(--muted); }
  .opt { display: flex; align-items: flex-start; gap: 8px; width: 100%; padding: 12px; }
  .opt:disabled:hover { background: #fff; }
  .opt .tag { flex: 0 0 auto; min-width: 2.6em; font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; margin-top: 3px; color: var(--muted); }
  .opt .tag.key { color: var(--accent); font-weight: 600; }
  .opt.is-key { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .opt.is-wrong { border-color: var(--text); border-style: dashed; }
  .opt.is-dim { opacity: 0.6; }
  .opt .box { flex: 0 0 auto; width: 16px; height: 16px; margin-top: 3px; border: 1px solid var(--border); border-radius: 4px; font-size: 11px; line-height: 14px; text-align: center; color: #fff; }
  .opt.is-on { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .opt.is-on .box { background: var(--text); border-color: var(--text); }
  .hint { font-size: 11px; letter-spacing: 0.06em; color: var(--muted); }
  .verdict { display: flex; align-items: flex-start; gap: 6px; font-size: 12px; letter-spacing: 0.02em; }
  .verdict.good { color: var(--accent); font-weight: 500; }
  .verdict.bad { color: var(--muted); font-weight: 500; }
  .why { border: 1px solid var(--border); background: var(--surface); border-radius: 8px; padding: 12px; }
  .score { font-size: 12px; letter-spacing: 0.04em; }
  .score .good { color: var(--accent); font-weight: 500; }
  .mark { border: 1px solid var(--border); border-radius: 8px; padding: 12px; }
  .mark.caught { border-color: var(--accent); }
  .mark.missed, .mark.false-flag { border-style: dashed; border-color: var(--text); }
  .mark .label { font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--muted); }
  .mark.caught .label { color: var(--accent); font-weight: 600; }
  .mark .term { margin-top: 4px; }
  .mark .note { margin-top: 4px; color: var(--muted); }
  .row { display: flex; flex-wrap: wrap; gap: 8px; }
  .done-title { display: flex; align-items: center; gap: 8px; }
  .done-title .dot { color: var(--accent); }
  @media (max-width: 480px) {
    body { padding: 8px; }
    .panel { padding: 14px; }
  }
</style>
</head>
<body>
<div class="panel" id="root"></div>

<script>
  // Curriculum data, verbatim from XLab src/lib/verification/data/drills-primers.ts
  // (em dashes replaced by commas, colons or semicolons).
  var DECK = {
    id: "drills-primers",
    title: "Drill Bench: Primers",
    blurb: "One bench over the primers: inspection games, credible commitment, two-level games, with the absolutist traps left in, and one syllogism to close.",
    benches: [
      {
        id: "primers",
        label: "Primers",
        name: "Primer bench",
        kicker: "Game theory and inspection logic: traps included, one syllogism to close.",
        time: "~6 min",
        steps: [
          {
            type: "pick",
            statement: "In a well-designed inspection game, the inspector’s optimal strategy drives the equilibrium violation rate to zero.",
            q: "True or false?",
            opts: ["True", "False"],
            right: 1,
            why: "False, and the word doing the damage is “zero”. In Dresher-style inspection games the inspector has limited inspections, so the equilibrium involves randomized inspection and a nonzero violation rate. A regime that promises zero is overclaiming; a regime that prices the residual rate is doing game theory."
          },
          {
            type: "pick",
            statement: "Reputation, reciprocity, and retaliation can sustain compliance without any court, but every one of the three runs on detection.",
            q: "True or false?",
            opts: ["True", "False"],
            right: 0,
            why: "True. Each enforcement channel that works without a world government begins with noticing the violation. That is the primer’s punchline and the whole track’s premise: no detection, no deterrence; verification is upstream of every enforcement story."
          },
          {
            type: "pick",
            statement: "In Putnam’s two-level game, a leader who signs in good faith and then fails domestic ratification has still defected, involuntarily.",
            q: "True or false?",
            opts: ["True", "False"],
            right: 0,
            why: "True. Two-level games distinguish voluntary defection (chose to cheat) from involuntary (couldn’t deliver the home front). A verification regime must survive both: the second kind is why ratification constraints belong in feasibility analysis, not just bad faith."
          },
          {
            type: "pick",
            brief: "Series: sunk costs · tied hands · mechanical enforcement.",
            q: "Name the tightest concept that covers all three, and only them.",
            opts: [
              "Game-theoretic concepts",
              "Fearon’s ways of making a commitment credible",
              "Forms of treaty punishment",
              "Domestic ratification constraints"
            ],
            right: 1,
            why: "The series rule: the tightest true label wins. “Game-theoretic concepts” is true but hopelessly broad; it earns zero on an olympiad table and it should here too. Fearon (1997): burn resources up front (sunk cost), make backing down costly later (tied hands), or remove the choice entirely (mechanical enforcement)."
          },
          {
            type: "multi",
            brief: "Nine terms, deliberately over-stocked the way the source round stocks its lists: randomized inspection · tit-for-tat · Dresher game · ratification constraint · equilibrium violation rate · audience costs · grim trigger · cheap talk · Schelling focal point.",
            q: "Mark exactly the three terms that belong to strategic inspection.",
            need: 3,
            items: [
              { t: "randomized inspection", err: true, note: "Inspection-game logic: predictable inspectors are avoidable inspectors." },
              { t: "tit-for-tat", err: false, note: "Repeated-cooperation strategy, the Evolution of Trust family, not inspection." },
              { t: "Dresher game", err: true, note: "The founding formalization of inspector vs. potential violator." },
              { t: "ratification constraint", err: false, note: "Two-level games: the domestic board, not the inspection board." },
              { t: "equilibrium violation rate", err: true, note: "The inspection game’s sobering output: the rate is nonzero at optimum." },
              { t: "audience costs", err: false, note: "Tied-hands credibility, Fearon’s territory, not the inspector’s." },
              { t: "grim trigger", err: false, note: "Repeated-game punishment strategy: enforcement, not inspection." },
              { t: "cheap talk", err: false, note: "Costless signaling, the opposite of everything Fearon and inspectors trade in." },
              { t: "Schelling focal point", err: false, note: "Coordination without communication, a third Schelling idea, not this one." }
            ],
            whyAll: "Four families were mixed into the list: inspection games (the three you had to find), repeated cooperation, commitment credibility, and coordination. The source round buries three needles in eleven terms; distractor density is part of the drill."
          },
          {
            type: "pick",
            brief: "Syllogism. Premises: (1) No self-reporting mechanism is tamper-resistant. (2) All log-based regimes are self-reporting mechanisms. (3) Some treaty provisions are log-based regimes. The full answer is the conclusion PLUS the picture: the reveal describes the circle diagram that justifies it.",
            q: "Which conclusion follows necessarily?",
            opts: [
              "No treaty provision is tamper-resistant",
              "Some treaty provisions are not tamper-resistant",
              "Some tamper-resistant mechanisms are treaty provisions",
              "All treaty provisions are self-reporting mechanisms"
            ],
            right: 1,
            fixedOrder: true,
            why: "Chain the circles: the log-based circle sits wholly inside self-reporting (premise 2), and self-reporting is disjoint from tamper-resistant (premise 1); the treaty-provisions circle overlaps log-based (premise 3), so that overlap is forced outside tamper-resistant, an existential conclusion and nothing more. The rest of the provisions circle is unconstrained, which kills the “no” and “all” options; the third option is not derivable at all. Drawing the arrangement where your answer holds and the others fail IS the justification; that is the drill’s scoring rule."
          }
        ]
      }
    ]
  };

  // Seeded shuffle, ported from XLab src/lib/shuffle.ts: same order for every
  // learner, keyed on the question, never on position.
  function hashSeed(seed) {
    var h = 0x811c9dc5;
    for (var i = 0; i < seed.length; i++) { h ^= seed.charCodeAt(i); h = Math.imul(h, 0x01000193); }
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
    var order = [], i, j, tmp;
    for (i = 0; i < n; i++) order.push(i);
    var rand = prng(hashSeed(seed));
    for (i = n - 1; i > 0; i--) { j = Math.floor(rand() * (i + 1)); tmp = order[i]; order[i] = order[j]; order[j] = tmp; }
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
  function identity(items) { return items.map(function (item, from) { return { item: item, from: from }; }); }
  function seededShuffle(seed, items, pinned) {
    var n = items.length;
    if (n < 2) return identity(items);
    var fixed = items.map(pinned);
    var movable = [];
    for (var i = 0; i < n; i++) if (!fixed[i]) movable.push(i);
    if (movable.length < 2) return identity(items);
    var perm = seededPermutation(seed, movable.length);
    var reordered = perm.map(function (p) { return movable[p]; });
    var out = [], next = 0;
    for (var slot = 0; slot < n; slot++) {
      var from = fixed[slot] ? slot : reordered[next++];
      out.push({ item: items[from], from: from });
    }
    return out;
  }
  function shuffleAnswerOptions(seed, items, text) {
    if (isBinaryPair(items.map(text))) return identity(items);
    return seededShuffle(seed, items, function (item) { return isTerminalOption(text(item)); });
  }

  // Progress: per bench, one record per step. done = Continue pressed after
  // the reveal (XLab's markStepDone); pick / marks = the committed answer,
  // kept so a restored page shows the same reveal the learner saw.
  var STORAGE_KEY = "lens-drills-primers:v1";
  var progress = {};
  var view = { benchId: null, pos: 0 };
  var completed = false;
  var resetArmed = false;
  var redoArmed = false;
  var draftMarks = {};

  function benchById(id) {
    for (var i = 0; i < DECK.benches.length; i++) if (DECK.benches[i].id === id) return DECK.benches[i];
    return null;
  }
  function records(bench) {
    if (!progress[bench.id]) progress[bench.id] = [];
    return progress[bench.id];
  }
  function record(bench, i) {
    var r = records(bench);
    if (!r[i]) r[i] = { done: false, pick: null, marks: null };
    return r[i];
  }
  function benchDone(bench) {
    var r = progress[bench.id] || [], n = 0;
    for (var i = 0; i < bench.steps.length; i++) if (r[i] && r[i].done) n++;
    return n;
  }
  function firstOpenStep(bench) {
    var r = progress[bench.id] || [];
    for (var i = 0; i < bench.steps.length; i++) if (!(r[i] && r[i].done)) return i;
    return bench.steps.length;
  }
  function benchComplete(bench) { return benchDone(bench) >= bench.steps.length; }
  function deckComplete() {
    for (var i = 0; i < DECK.benches.length; i++) if (!benchComplete(DECK.benches[i])) return false;
    return true;
  }
  function nextOpenBench(exceptId) {
    for (var i = 0; i < DECK.benches.length; i++) {
      var b = DECK.benches[i];
      if (b.id !== exceptId && !benchComplete(b)) return b;
    }
    return null;
  }
  function started() {
    for (var k in progress) if (progress.hasOwnProperty(k) && progress[k].length) return true;
    return false;
  }
  function pruneProgress(raw) {
    var out = {};
    if (!raw || typeof raw !== "object" || !raw.benches || typeof raw.benches !== "object") return out;
    DECK.benches.forEach(function (bench) {
      var flags = raw.benches[bench.id];
      if (!Array.isArray(flags)) return;
      out[bench.id] = bench.steps.map(function (step, i) {
        var f = flags[i];
        if (!f || typeof f !== "object") return null;
        var rec = { done: !!f.done, pick: null, marks: null };
        if (step.type === "pick" && typeof f.pick === "number" && f.pick >= 0 && f.pick < step.opts.length) rec.pick = f.pick;
        if (step.type === "multi" && Array.isArray(f.marks)) {
          rec.marks = f.marks.filter(function (m) { return typeof m === "number" && m >= 0 && m < step.items.length; });
        }
        if (step.type === "multi" && rec.marks === null && rec.done) rec.marks = [];
        return rec;
      });
    });
    return out;
  }

  function scoreMulti(step, marks) {
    var rows = step.items.map(function (item, i) {
      var isMarked = marks.indexOf(i) !== -1;
      var verdict = item.err ? (isMarked ? "caught" : "missed") : (isMarked ? "false-flag" : "clean");
      return { verdict: verdict, marked: isMarked };
    });
    function n(v) { return rows.filter(function (r) { return r.verdict === v; }).length; }
    return { rows: rows, caught: n("caught"), missed: n("missed"), falseFlagged: n("false-flag") };
  }
  function multiCommitState(step, markedCount) {
    if (typeof step.need === "number") {
      var ready = markedCount === step.need;
      return { ready: ready, hint: ready ? "ready" : "marked " + markedCount + ", mark exactly " + step.need };
    }
    var ok = markedCount >= 1;
    return { ready: ok, hint: ok ? markedCount + " marked, commit when sure" : "mark at least one" };
  }

  // Persistence and the tutor summary.
  function summary() {
    var lines = [DECK.title + "."];
    DECK.benches.forEach(function (bench) {
      var r = progress[bench.id] || [];
      var done = benchDone(bench), matched = 0, answered = 0;
      var parts = [];
      bench.steps.forEach(function (step, i) {
        var rec = r[i];
        var label = "Step " + (i + 1) + " (" + (step.statement ? step.statement + " " : "") + step.q + ")";
        if (!rec || (rec.pick === null && rec.marks === null)) { parts.push(label + ": not answered yet."); return; }
        answered++;
        if (step.type === "pick") {
          var ok = rec.pick === step.right;
          if (ok) matched++;
          parts.push(label + ": picked “" + step.opts[rec.pick] + "”; the key is “" + step.opts[step.right] + "”; " + (ok ? "match" : "not a match") + ". Explanation: " + step.why);
        } else {
          var s = scoreMulti(step, rec.marks);
          var ok2 = s.missed === 0 && s.falseFlagged === 0;
          if (ok2) matched++;
          var names = rec.marks.map(function (m) { return step.items[m].t; }).join(", ");
          parts.push(label + ": marked " + (names || "nothing") + "; " + s.caught + " caught, " + s.missed + " missed, " + s.falseFlagged + " false-flagged. " + (step.whyAll || ""));
        }
      });
      lines.push(bench.name + ": " + done + " of " + bench.steps.length + " steps continued through, " + answered + " answered, " + matched + " matched the key." + (benchComplete(bench) ? " Bench complete." : ""));
      lines = lines.concat(parts);
    });
    return lines.join(" ");
  }
  function persist() {
    var json = { benches: progress };
    if (window.Lens) {
      Lens.saveState(json, summary());
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(json)); } catch (e) {}
    }
  }

  // Rendering.
  var root = document.getElementById("root");
  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }
  function btn(id, className, text, onClick) {
    var b = el("button", className, text);
    b.type = "button";
    if (id) b.id = id;
    b.addEventListener("click", onClick);
    return b;
  }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }

  function render() {
    clear(root);
    var bench = view.benchId ? benchById(view.benchId) : null;
    if (!bench) { renderMenu(); return; }
    if (view.pos >= bench.steps.length) { renderFinish(bench); return; }
    renderStep(bench, view.pos);
  }

  function renderMenu() {
    var wrap = el("div", "stack");
    var head = el("div");
    head.appendChild(el("p", "eyebrow", "Drill bench"));
    head.appendChild(el("h1", null, DECK.title));
    head.appendChild(el("p", "muted", DECK.blurb));
    wrap.appendChild(head);
    wrap.appendChild(el("p", "muted", "Commit before every reveal: the commit is the exercise. Nothing here is graded."));
    var list = el("ul", "list");
    DECK.benches.forEach(function (b) {
      var li = el("li");
      var card = btn("open-" + b.id, "bench-card", null, function () { openBench(b); });
      var top = el("span");
      top.appendChild(el("span", "name", b.name));
      if (benchComplete(b)) top.appendChild(el("span", "badge", "✓ complete"));
      card.appendChild(top);
      card.appendChild(el("span", "kicker", b.kicker));
      card.appendChild(el("span", "count", b.time + " · " + benchDone(b) + " / " + b.steps.length));
      li.appendChild(card);
      list.appendChild(li);
    });
    wrap.appendChild(list);
    if (started()) {
      wrap.appendChild(btn("reset", null, resetArmed ? "Sure? Tap again" : "↺ Reset this deck", function () {
        if (!resetArmed) { resetArmed = true; render(); return; }
        resetArmed = false;
        progress = {};
        draftMarks = {};
        persist();
        render();
      }));
    }
    root.appendChild(wrap);
  }

  function openBench(b) {
    resetArmed = false;
    view.benchId = b.id;
    view.pos = firstOpenStep(b);
    render();
  }

  function renderStep(bench, pos) {
    var step = bench.steps[pos];
    var last = pos + 1 >= bench.steps.length;
    var wrap = el("div", "stack");

    var header = el("div");
    var row = el("div", "head-row");
    row.appendChild(el("p", "eyebrow", bench.name + " · " + (pos + 1) + " / " + bench.steps.length));
    if (DECK.benches.length > 1) row.appendChild(btn("menu", "ghost", "All benches", function () { view.benchId = null; render(); }));
    header.appendChild(row);
    var meter = el("div", "meter");
    meter.setAttribute("role", "img");
    meter.setAttribute("aria-label", "Step " + (pos + 1) + " of " + bench.steps.length);
    for (var i = 0; i < bench.steps.length; i++) meter.appendChild(el("span", i < pos ? "is-filled" : ""));
    header.appendChild(meter);
    wrap.appendChild(header);

    wrap.appendChild(el("h2", null, step.q));
    if (step.brief) wrap.appendChild(el("p", "brief", step.brief));
    if (step.statement) wrap.appendChild(el("blockquote", "statement", step.statement));

    if (step.type === "pick") renderPick(wrap, bench, pos, step, last);
    else renderMulti(wrap, bench, pos, step, last);
    root.appendChild(wrap);
  }

  function renderPick(wrap, bench, pos, step, last) {
    var rec = (progress[bench.id] || [])[pos];
    var choice = rec && typeof rec.pick === "number" ? rec.pick : null;
    var answered = choice !== null;
    var shown = step.fixedOrder ? identity(step.opts) : shuffleAnswerOptions(bench.id + "#" + pos, step.opts, function (o) { return o; });
    var list = el("ul", "list");
    shown.forEach(function (s) {
      var from = s.from;
      var isKey = from === step.right;
      var picked = choice === from;
      var b = btn("opt-" + pos + "-" + from, "opt", null, function () {
        var live = record(bench, pos);
        if (live.pick !== null) return;
        live.pick = from;
        persist();
        render();
      });
      b.setAttribute("aria-pressed", picked ? "true" : "false");
      if (answered) {
        b.disabled = true;
        if (isKey) b.classList.add("is-key");
        else if (picked) b.classList.add("is-wrong");
        else b.classList.add("is-dim");
        b.appendChild(el("span", "tag" + (isKey ? " key" : ""), isKey ? "key" : (picked ? "yours" : "")));
      }
      b.appendChild(el("span", null, s.item));
      list.appendChild(b);
    });
    wrap.appendChild(list);
    if (answered) {
      var right = choice === step.right;
      renderReveal(wrap, bench, pos, last,
        right ? { tone: "good", text: "Match, and here is the reasoning:" } : { tone: "bad", text: "Not quite. The key says: " + step.opts[step.right] },
        step.why);
    }
  }

  function renderMulti(wrap, bench, pos, step, last) {
    var rec = (progress[bench.id] || [])[pos];
    var committed = rec && Array.isArray(rec.marks) ? rec.marks : null;
    var key = bench.id + "#" + pos;
    if (committed) {
      var score = scoreMulti(step, committed);
      var line = el("p", "score");
      line.appendChild(el("span", "good", score.caught + " caught"));
      line.appendChild(document.createTextNode(" · " + score.missed + " missed · " + score.falseFlagged + " false-flagged"));
      wrap.appendChild(line);
      var list = el("ul", "list");
      step.items.forEach(function (item, i) {
        var v = score.rows[i].verdict;
        var li = el("li", "mark " + v);
        li.appendChild(el("span", "label", v === "false-flag" ? "false flag" : v));
        li.appendChild(el("p", "term", item.t));
        li.appendChild(el("p", "note", item.note));
        list.appendChild(li);
      });
      wrap.appendChild(list);
      if (step.whyAll) renderReveal(wrap, bench, pos, last, null, step.whyAll);
      else wrap.appendChild(continueButton(bench, pos, last));
      return;
    }
    if (!draftMarks[key]) draftMarks[key] = [];
    var marked = draftMarks[key];
    var shown = step.fixedOrder ? identity(step.items) : shuffleAnswerOptions(key, step.items, function (it) { return it.t; });
    var ul = el("ul", "list");
    shown.forEach(function (s) {
      var from = s.from;
      var on = marked.indexOf(from) !== -1;
      var b = btn("opt-" + pos + "-" + from, "opt" + (on ? " is-on" : ""), null, function () {
        var idx = marked.indexOf(from);
        if (idx === -1) marked.push(from); else marked.splice(idx, 1);
        render();
      });
      b.setAttribute("aria-pressed", on ? "true" : "false");
      b.appendChild(el("span", "box", on ? "✓" : ""));
      b.appendChild(el("span", null, s.item.t));
      ul.appendChild(b);
    });
    wrap.appendChild(ul);
    var state = multiCommitState(step, marked.length);
    var hint = el("p", "hint", state.hint);
    hint.setAttribute("aria-live", "polite");
    wrap.appendChild(hint);
    var commit = btn("commit-marks", "primary", "⚑ Commit the marks", function () {
      if (!multiCommitState(step, marked.length).ready) return;
      if (record(bench, pos).marks !== null) return;
      record(bench, pos).marks = marked.slice().sort(function (a, c) { return a - c; });
      delete draftMarks[key];
      persist();
      render();
    });
    commit.disabled = !state.ready;
    wrap.appendChild(commit);
  }

  function renderReveal(wrap, bench, pos, last, verdict, body) {
    if (verdict) {
      var v = el("p", "verdict " + verdict.tone);
      v.appendChild(el("span", null, verdict.tone === "good" ? "✓" : "✕"));
      v.appendChild(el("span", null, verdict.text));
      wrap.appendChild(v);
    }
    wrap.appendChild(el("p", "why", body));
    wrap.appendChild(continueButton(bench, pos, last));
  }

  function continueButton(bench, pos, last) {
    return btn("continue", "primary", (last ? "Finish bench" : "Continue") + " →", function () {
      record(bench, pos).done = true;
      view.pos = pos + 1;
      persist();
      if (!completed && deckComplete()) {
        completed = true;
        if (window.Lens) Lens.complete();
      }
      render();
    });
  }

  function renderFinish(bench) {
    var wrap = el("div", "stack");
    wrap.appendChild(el("p", "eyebrow", bench.name + " · complete"));
    var h = el("h2", "done-title");
    h.appendChild(el("span", "dot", "◉"));
    h.appendChild(el("span", null, "Done: " + benchDone(bench) + " / " + bench.steps.length));
    wrap.appendChild(h);
    var next = nextOpenBench(bench.id);
    wrap.appendChild(el("p", "muted", next ? "Next open bench: " + next.name + ", " + next.kicker : "Every bench in this module is complete."));
    var row = el("div", "row");
    if (next) row.appendChild(btn("next-bench", "primary", next.name + " →", function () { openBench(next); }));
    row.appendChild(btn("redo", null, redoArmed ? "Sure? Tap again" : "↺ Redo bench", function () {
      if (!redoArmed) { redoArmed = true; render(); return; }
      redoArmed = false;
      progress[bench.id] = [];
      view.pos = 0;
      persist();
      render();
    }));
    if (DECK.benches.length > 1) row.appendChild(btn("menu", "ghost", "All benches", function () { view.benchId = null; render(); }));
    wrap.appendChild(row);
    root.appendChild(wrap);
  }

  function hydrate(saved, meta) {
    progress = pruneProgress(saved);
    completed = !!(meta && meta.completed);
    view.benchId = null;
    view.pos = 0;
    render();
  }

  if (window.Lens) {
    render();
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE_KEY)); } catch (e) { raw = null; }
    hydrate(raw, { completed: false });
  }
</script>
</body>
</html>

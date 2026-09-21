---
id: 'c81c1118-d19b-438f-a51f-68638ebc149b'
title: Weighted factor model
summary_for_tutor: "The Effective Thesis Accelerator's Week 3 Step 4 exercise as a widget, replacing the shared WFM spreadsheet. A grid whose rows are the learner's shortlisted research questions and whose columns are twelve factors in four categories (impact on the problem area, on their career path, on their community, and general thesis interest). They type each question, score it 1-10 against every factor, and edit the percentage weights, which start at the Accelerator's suggested split and must total 100. The weighted total is a plain sum of score times weight over 100, which is the arithmetic the Week 3 reading describes; it is deliberately not the standardised scoring the spreadsheet does. A live ranking appears once two questions are fully scored, and the learner then names a gut favourite; if the gut pick and the model's top pick disagree the widget says so and asks them to sit with the tension rather than overriding either. Complete means two questions fully scored, a gut favourite chosen, and weights totalling 100. Their questions, scores, weights and gut pick arrive in the widget-state block. There is no answer key. If they ask for review, ask which factor's weight is doing the work separating first from second, and if the gut pick differs from the model, ask what the model is failing to capture rather than telling them which to trust."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Weighted factor model</title>
<!-- Built for the Effective Thesis Accelerator, Week 3 Step 4. Replaces the [Shared] Example Thesis WFM spreadsheet. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  [hidden] { display: none !important; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 8px; }
  h3 { font-size: 12px; font-weight: 600; margin: 18px 0 6px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--muted); }
  p.hint { font-size: 12px; color: var(--muted); margin: 0 0 10px; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; margin-bottom: 16px; }
  .scroll { overflow-x: auto; }
  table { border-collapse: collapse; width: 100%; font-size: 13px; }
  th, td { border-bottom: 1px solid var(--border); padding: 5px 7px; text-align: right; font-variant-numeric: tabular-nums; vertical-align: middle; }
  th:first-child, td:first-child { text-align: left; font-variant-numeric: normal; min-width: 15rem; }
  thead th { font-size: 11px; letter-spacing: 0.05em; color: var(--muted); font-weight: 600; }
  thead th.cat { text-align: center; border-bottom: 2px solid var(--accent); font-size: 10px; text-transform: uppercase; }
  tbody tr.is-top td { background: var(--surface); }
  tbody tr.is-top td:first-child { font-weight: 600; }
  input[type=text], input[type=number], textarea {
    font: inherit; color: inherit; background: #fff; border: 1px solid var(--border);
    border-radius: 6px; padding: 5px 7px;
  }
  input[type=text] { width: 100%; }
  input[type=number] { width: 3.6rem; text-align: right; font-variant-numeric: tabular-nums; }
  input.score { width: 3.1rem; }
  input.wt { width: 3.4rem; }
  td.total { font-weight: 600; font-size: 14px; }
  .crit { display: grid; grid-template-columns: 1fr 4.2rem; gap: 6px 10px; align-items: center; }
  .crit .catlabel { grid-column: 1 / -1; font-size: 11px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--accent); font-weight: 600; margin-top: 10px; }
  .crit label { font-size: 13px; }
  .meter { display: flex; flex-wrap: wrap; gap: 8px; align-items: baseline; justify-content: space-between; border-top: 1px solid var(--border); margin-top: 12px; padding-top: 10px; }
  .meter .num { font-variant-numeric: tabular-nums; font-weight: 600; }
  .meter .note { font-size: 12px; color: var(--muted); }
  .meter .note.is-off { color: var(--accent); font-weight: 600; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 7px 11px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button.link { border: 0; padding: 2px 4px; color: var(--muted); text-decoration: underline; }
  .actions { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 12px; }
  .rank { margin: 0; padding-left: 18px; }
  .rank li { margin: 3px 0; }
  .rank .sc { color: var(--muted); font-variant-numeric: tabular-nums; }
  .tension { border-left: 3px solid var(--accent); background: var(--surface); border-radius: 0 6px 6px 0; padding: 10px 12px; margin-top: 12px; }
  select { font: inherit; color: inherit; background: #fff; border: 1px solid var(--border); border-radius: 6px; padding: 5px 7px; max-width: 100%; }
  input:focus-visible, textarea:focus-visible, button:focus-visible, select:focus-visible { outline: 2px solid var(--accent); outline-offset: 1px; }
  @media (max-width: 620px) {
    .crit { grid-template-columns: 1fr 4.2rem; }
  }
</style>
</head>
<body>

<div class="card">
  <h2>Your weighted factor model</h2>
  <p class="hint">Name your shortlisted questions, score each one against every factor from 1 to 10, and the weighted total updates as you go. Weights are yours to change.</p>
  <div class="scroll">
    <table id="grid">
      <thead>
        <tr id="cats"></tr>
        <tr id="crits"></tr>
      </thead>
      <tbody id="rows"></tbody>
    </table>
  </div>
  <div class="actions">
    <button type="button" id="addrow">Add a question</button>
  </div>
</div>

<div class="card">
  <h3>Your factors and weights</h3>
  <p class="hint">Split 100 points across the factors according to what matters to you. These start at the Accelerator's suggested split.</p>
  <div class="crit" id="weights"></div>
  <div class="meter">
    <span><span class="num" id="wsum">100</span>% allocated</span>
    <span class="note" id="wnote"></span>
  </div>
  <div class="actions">
    <button type="button" id="resetw">Reset to the suggested weights</button>
  </div>
</div>

<div class="card">
  <h3>Where that leaves you</h3>
  <ol class="rank" id="rank"></ol>
  <p class="hint" id="empty">Score at least two questions to see a ranking.</p>
  <div id="gutwrap" hidden>
    <label class="hint" for="gut">Before you look at the ranking: which one is your gut favourite?</label>
    <select id="gut"><option value="">Choose one</option></select>
    <div class="tension" id="tension" hidden></div>
  </div>
  <div class="actions">
    <button type="button" id="ask" hidden>Ask the tutor to challenge my top choice</button>
  </div>
</div>

<script>
  var CRITERIA = [
    { id: "importance",   cat: "Impact on the problem area", label: "The problem: Importance", wt: 5 },
    { id: "neglected",    cat: "Impact on the problem area", label: "The problem: Neglectedness", wt: 5 },
    { id: "tractable",    cat: "Impact on the problem area", label: "The problem: Tractability", wt: 5 },
    { id: "pathway",      cat: "Impact on the problem area", label: "Certainty of pathway to impact", wt: 20 },
    { id: "skills",       cat: "Impact on my career path",   label: "Skill building", wt: 12 },
    { id: "relationship", cat: "Impact on my career path",   label: "Relationship building", wt: 12 },
    { id: "fit-test",     cat: "Impact on my career path",   label: "Testing fit", wt: 12 },
    { id: "community",    cat: "Impact on my community",     label: "Community impact", wt: 15 },
    { id: "current-fit",  cat: "General thesis interest",    label: "Current fit", wt: 5 },
    { id: "motivation",   cat: "General thesis interest",    label: "Motivation", wt: 3 },
    { id: "novelty",      cat: "General thesis interest",    label: "Novelty", wt: 3 },
    { id: "draw",         cat: "General thesis interest",    label: "Intuitive draw", wt: 3 }
  ];
  var MAX_ROWS = 8;
  var STORE_KEY = "et-wfm-preview";

  var state = { rows: [], weights: {}, gut: "" };
  var completed = false;

  function defaultWeights() {
    var w = {};
    CRITERIA.forEach(function (c) { w[c.id] = c.wt; });
    return w;
  }
  function blankRow(n) {
    var r = { id: "q" + n, question: "", scores: {} };
    CRITERIA.forEach(function (c) { r.scores[c.id] = null; });
    return r;
  }
  function seed() {
    state.weights = defaultWeights();
    state.rows = [blankRow(1), blankRow(2), blankRow(3)];
    state.gut = "";
  }
  seed();

  function fmt(n) { return (Math.round(n * 10) / 10).toFixed(1); }
  function weightSum() {
    var t = 0;
    CRITERIA.forEach(function (c) { t += Number(state.weights[c.id]) || 0; });
    return Math.round(t * 10) / 10;
  }
  function scoredCount(r) {
    var n = 0;
    CRITERIA.forEach(function (c) { if (r.scores[c.id] != null) n++; });
    return n;
  }
  function isScored(r) { return scoredCount(r) === CRITERIA.length; }
  function total(r) {
    var t = 0;
    CRITERIA.forEach(function (c) {
      var s = r.scores[c.id];
      if (s != null) t += s * ((Number(state.weights[c.id]) || 0) / 100);
    });
    return t;
  }
  function named() { return state.rows.filter(function (r) { return r.question.trim(); }); }
  function ready() { return state.rows.filter(function (r) { return r.question.trim() && isScored(r); }); }
  function ranked() {
    return ready().slice().sort(function (a, b) { return total(b) - total(a); });
  }

  var elGrid = document.getElementById("grid");
  var elCats = document.getElementById("cats");
  var elCrits = document.getElementById("crits");
  var elRows = document.getElementById("rows");
  var elWeights = document.getElementById("weights");
  var elWsum = document.getElementById("wsum");
  var elWnote = document.getElementById("wnote");
  var elRank = document.getElementById("rank");
  var elEmpty = document.getElementById("empty");
  var elGutWrap = document.getElementById("gutwrap");
  var elGut = document.getElementById("gut");
  var elTension = document.getElementById("tension");
  var elAsk = document.getElementById("ask");

  function buildHead() {
    elCats.innerHTML = "";
    elCrits.innerHTML = "";
    var c0 = document.createElement("th");
    c0.rowSpan = 2;
    c0.textContent = "Research question";
    elCats.appendChild(c0);
    var groups = [];
    CRITERIA.forEach(function (c) {
      var last = groups[groups.length - 1];
      if (last && last.cat === c.cat) last.n++;
      else groups.push({ cat: c.cat, n: 1 });
    });
    groups.forEach(function (g) {
      var th = document.createElement("th");
      th.className = "cat";
      th.colSpan = g.n;
      th.textContent = g.cat;
      elCats.appendChild(th);
    });
    var tot = document.createElement("th");
    tot.rowSpan = 2;
    tot.textContent = "Weighted total";
    elCats.appendChild(tot);
    var rm = document.createElement("th");
    rm.rowSpan = 2;
    rm.setAttribute("aria-label", "Remove");
    elCats.appendChild(rm);
    CRITERIA.forEach(function (c) {
      var th = document.createElement("th");
      th.textContent = c.label;
      th.title = c.label;
      elCrits.appendChild(th);
    });
  }

  function buildWeights() {
    elWeights.innerHTML = "";
    var seen = {};
    CRITERIA.forEach(function (c) {
      if (!seen[c.cat]) {
        seen[c.cat] = true;
        var h = document.createElement("div");
        h.className = "catlabel";
        h.textContent = c.cat;
        elWeights.appendChild(h);
      }
      var lab = document.createElement("label");
      lab.textContent = c.label;
      lab.setAttribute("for", "wt-" + c.id);
      var inp = document.createElement("input");
      inp.type = "number";
      inp.className = "wt";
      inp.id = "wt-" + c.id;
      inp.min = "0";
      inp.max = "100";
      inp.step = "1";
      inp.value = state.weights[c.id];
      inp.addEventListener("input", function () {
        var v = inp.value === "" ? 0 : Number(inp.value);
        if (!isFinite(v) || v < 0) v = 0;
        if (v > 100) v = 100;
        state.weights[c.id] = v;
        render();
        persist();
      });
      elWeights.appendChild(lab);
      elWeights.appendChild(inp);
    });
  }

  function buildRows() {
    elRows.innerHTML = "";
    state.rows.forEach(function (r, i) {
      var tr = document.createElement("tr");
      var tdQ = document.createElement("td");
      var q = document.createElement("input");
      q.type = "text";
      q.value = r.question;
      q.placeholder = "Question " + (i + 1);
      q.addEventListener("input", function () {
        r.question = q.value;
        renderRank();
        persist();
      });
      tdQ.appendChild(q);
      tr.appendChild(tdQ);

      CRITERIA.forEach(function (c) {
        var td = document.createElement("td");
        var s = document.createElement("input");
        s.type = "number";
        s.className = "score";
        s.min = "1";
        s.max = "10";
        s.step = "1";
        s.value = r.scores[c.id] == null ? "" : r.scores[c.id];
        s.setAttribute("aria-label", c.label);
        s.addEventListener("input", function () {
          if (s.value === "") { r.scores[c.id] = null; }
          else {
            var v = Math.round(Number(s.value));
            if (!isFinite(v)) { r.scores[c.id] = null; }
            else { r.scores[c.id] = Math.min(10, Math.max(1, v)); }
          }
          render();
          persist();
        });
        td.appendChild(s);
        tr.appendChild(td);
      });

      var tdT = document.createElement("td");
      tdT.className = "total";
      tr.appendChild(tdT);

      var tdX = document.createElement("td");
      var x = document.createElement("button");
      x.type = "button";
      x.className = "link";
      x.textContent = "remove";
      x.addEventListener("click", function () {
        if (state.rows.length <= 1) return;
        state.rows.splice(i, 1);
        buildRows();
        render();
        persist();
      });
      tdX.appendChild(x);
      tr.appendChild(tdX);
      elRows.appendChild(tr);
    });
  }

  function renderRank() {
    var sum = weightSum();
    elWsum.textContent = fmt(sum);
    var off = Math.round((sum - 100) * 10) / 10;
    elWnote.textContent = off === 0 ? "Adds up" : (off > 0 ? fmt(off) + " over 100" : fmt(-off) + " short of 100");
    elWnote.classList.toggle("is-off", off !== 0);

    Array.prototype.forEach.call(elRows.children, function (tr, i) {
      var r = state.rows[i];
      if (!r) return;
      var cell = tr.children[tr.children.length - 2];
      cell.textContent = isScored(r) ? fmt(total(r)) : (scoredCount(r) + "/" + CRITERIA.length);
      tr.classList.remove("is-top");
    });

    var order = ranked();
    elRank.innerHTML = "";
    elEmpty.hidden = order.length >= 2;
    order.forEach(function (r, i) {
      var li = document.createElement("li");
      li.textContent = r.question.trim();
      var sc = document.createElement("span");
      sc.className = "sc";
      sc.textContent = "  " + fmt(total(r));
      li.appendChild(sc);
      elRank.appendChild(li);
      if (i === 0) {
        var idx = state.rows.indexOf(r);
        if (idx >= 0 && elRows.children[idx]) elRows.children[idx].classList.add("is-top");
      }
    });

    var pick = named();
    elGutWrap.hidden = pick.length < 2;
    var prev = state.gut;
    elGut.innerHTML = "";
    var opt0 = document.createElement("option");
    opt0.value = "";
    opt0.textContent = "Choose one";
    elGut.appendChild(opt0);
    pick.forEach(function (r) {
      var o = document.createElement("option");
      o.value = r.id;
      o.textContent = r.question.trim();
      elGut.appendChild(o);
    });
    elGut.value = prev;
    if (elGut.value !== prev) state.gut = "";

    elTension.hidden = true;
    if (state.gut && order.length >= 2) {
      var top = order[0];
      if (top.id === state.gut) {
        elTension.hidden = false;
        elTension.textContent = "Your model and your gut agree on " + top.question.trim() + ". That is a good sign, and it is worth one moment of suspicion: did you score it generously because you already wanted it?";
      } else {
        var g = null;
        order.forEach(function (r) { if (r.id === state.gut) g = r; });
        if (g) {
          elTension.hidden = false;
          elTension.textContent = "Your model puts " + top.question.trim() + " on top (" + fmt(total(top)) + "), but your gut picked " + g.question.trim() + " (" + fmt(total(g)) + "). Sit with that before deciding. Do not just override the model, and do not just override your gut. Usually it means a factor you care about is missing or underweighted.";
        }
      }
    }
    elAsk.hidden = !(window.Lens && Lens.promptTutor && order.length >= 2);
  }

  function render() { renderRank(); }

  function summary() {
    var lines = ["Weighted factor model for choosing a thesis research question."];
    var sum = weightSum();
    var wparts = [];
    CRITERIA.forEach(function (c) { wparts.push(c.label + " " + fmt(state.weights[c.id]) + "%"); });
    lines.push("Weights (totalling " + fmt(sum) + "%): " + wparts.join(", ") + ".");
    if (Math.round((sum - 100) * 10) / 10 !== 0) {
      lines.push("Note: the weights do not add to 100, so the totals below are not comparable to a 1-10 scale.");
    }
    lines.push("");
    var order = ranked();
    if (!order.length) {
      lines.push("No question has been fully scored yet.");
    } else {
      lines.push("Ranked by weighted total:");
      order.forEach(function (r, i) {
        var parts = [];
        CRITERIA.forEach(function (c) { parts.push(c.label + " " + r.scores[c.id]); });
        lines.push("  " + (i + 1) + ". " + r.question.trim() + " - weighted total " + fmt(total(r)));
        lines.push("     scores: " + parts.join(", "));
      });
    }
    var partial = state.rows.filter(function (r) { return r.question.trim() && !isScored(r); });
    if (partial.length) {
      lines.push("");
      partial.forEach(function (r) {
        lines.push("Partly scored: " + r.question.trim() + " (" + scoredCount(r) + " of " + CRITERIA.length + " factors).");
      });
    }
    if (state.gut) {
      var g = null;
      state.rows.forEach(function (r) { if (r.id === state.gut) g = r; });
      if (g) {
        lines.push("");
        lines.push("Gut favourite: " + g.question.trim() + ".");
        if (order.length && order[0].id !== state.gut) {
          lines.push("This DISAGREES with the model, which ranks " + order[0].question.trim() + " first. That tension is the thing to talk about.");
        } else if (order.length) {
          lines.push("This agrees with the model's top pick.");
        }
      }
    }
    return lines.join("\n");
  }

  function isDone() {
    return ready().length >= 2 && !!state.gut && Math.round((weightSum() - 100) * 10) / 10 === 0;
  }

  function persist() {
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (!completed && isDone()) {
        completed = true;
        Lens.complete();
      }
    } else {
      try { localStorage.setItem(STORE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }

  document.getElementById("addrow").addEventListener("click", function () {
    if (state.rows.length >= MAX_ROWS) return;
    state.rows.push(blankRow(state.rows.length + 1 + Math.floor(Math.random() * 1000)));
    buildRows();
    render();
    persist();
  });

  document.getElementById("resetw").addEventListener("click", function () {
    state.weights = defaultWeights();
    buildWeights();
    render();
    persist();
  });

  elGut.addEventListener("change", function () {
    state.gut = elGut.value;
    render();
    persist();
  });

  elAsk.addEventListener("click", function () {
    if (!window.Lens || !Lens.promptTutor) return;
    Lens.promptTutor(
      "I have scored my research questions in the weighted factor model. Can you challenge my top choice?",
      "The learner has filled in the Effective Thesis Week 3 weighted factor model. Their model:\n" + summary() +
      "\nDo not hand them an answer; there is no answer key. Pick the single factor whose weight is doing the most work in separating first from second and ask whether they really believe that weight. If their gut favourite differs from the model's top pick, ask what the model is not capturing rather than telling them which to trust."
    );
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (saved.weights && typeof saved.weights === "object") {
        CRITERIA.forEach(function (c) {
          var v = saved.weights[c.id];
          if (typeof v === "number" && isFinite(v) && v >= 0 && v <= 100) state.weights[c.id] = v;
        });
      }
      if (Object.prototype.toString.call(saved.rows) === "[object Array]" && saved.rows.length) {
        var rows = [];
        saved.rows.slice(0, MAX_ROWS).forEach(function (got, i) {
          if (!got || typeof got !== "object") return;
          var r = blankRow(i + 1);
          if (typeof got.id === "string" && got.id) r.id = got.id;
          if (typeof got.question === "string") r.question = got.question;
          if (got.scores && typeof got.scores === "object") {
            CRITERIA.forEach(function (c) {
              var v = got.scores[c.id];
              if (typeof v === "number" && isFinite(v) && v >= 1 && v <= 10) r.scores[c.id] = Math.round(v);
            });
          }
          rows.push(r);
        });
        if (rows.length) state.rows = rows;
      }
      if (typeof saved.gut === "string") state.gut = saved.gut;
    }
    completed = !!(meta && meta.completed);
    buildWeights();
    buildRows();
    render();
  }

  buildHead();
  buildWeights();
  buildRows();
  render();

  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    elAsk.hidden = true;
    var raw = null;
    try { raw = localStorage.getItem(STORE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
</script>
</body>
</html>

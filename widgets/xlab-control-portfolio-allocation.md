---
id: '34ff02a7-0cba-4299-bac2-7be10271c222'
title: Portfolio allocation across regimes
summary_for_tutor: "XLab's Module 2 capstone exercise, rebuilt as a widget. The learner directs a safety team with 10 researchers' worth of effort and splits it across seven agendas (control protocols, alignment research, interpretability, verification and evals science, scalable oversight, policy/pause/coordination, security) in each of three stipulated regimes: Scenario 1 Schemeria under racing pressure approaching autonomous coding under Plan C; Scenario 2 Easyland-or-Lurkville with treaty slack approaching autonomous research under Plan A; Scenario 3 Slopolis under commercial pressure at mid-stage under Plan D. For each regime the learner also writes two short defences: the margin (which agenda gets the next unit of effort and through which payoff channel: usefulness, evidence, or direct) and the binding constraint (the one allocation they would trade any other for). Sliders move in half-researcher steps and the widget tracks the remaining budget; a scenario counts as answered when its allocation totals exactly 10 and both defences have text. When all three are answered the widget computes a comparison table showing how each agenda's share moved across the three regimes and names the agenda that moved most. The learner's numbers and defences arrive in the widget-state block as they work. If they ask for review, probe whether the allocation actually changed when the regime changed, and whether the named margin matches the numbers they set."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Portfolio allocation across regimes</title>
<!-- Rebuilt from XLab Tracks, AI Control track, lesson "Running the model", exercise cr-portfolio-allocation. -->
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
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 24px; margin: 4px 0 8px; }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 6px; }
  h3 { font-size: 12px; font-weight: 600; margin: 0 0 6px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--muted); }
  .lede { color: var(--muted); margin: 0 0 4px; max-width: 44rem; }
  .steps { color: var(--muted); margin: 0 0 16px; padding-left: 18px; max-width: 44rem; }
  .tabs { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 14px; }
  .tab { display: flex; align-items: center; gap: 6px; }
  .dot { width: 8px; height: 8px; border-radius: 50%; border: 1px solid var(--muted); display: inline-block; flex: 0 0 auto; }
  .dot.is-done { background: var(--accent); border-color: var(--accent); }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .regime { background: var(--surface); margin-bottom: 14px; }
  .regime dl { margin: 0; display: grid; grid-template-columns: max-content 1fr; gap: 4px 12px; }
  .regime dt { font-weight: 600; }
  .regime dd { margin: 0; color: var(--muted); }
  .alloc { margin-bottom: 14px; }
  .row { display: grid; grid-template-columns: 13rem 1fr 3.5rem; gap: 10px; align-items: center; padding: 5px 0; }
  .row label { font-weight: 500; }
  .row input[type=range] { width: 100%; accent-color: var(--accent); }
  .val { text-align: right; font-variant-numeric: tabular-nums; color: var(--muted); }
  .val.is-set { color: var(--text); font-weight: 600; }
  .meter { display: flex; flex-wrap: wrap; gap: 8px; align-items: baseline; justify-content: space-between; border-top: 1px solid var(--border); margin-top: 10px; padding-top: 10px; }
  .meter .num { font-variant-numeric: tabular-nums; font-weight: 600; }
  .meter .note { font-size: 12px; color: var(--muted); }
  .meter .note.is-off { color: var(--accent); }
  .bar { height: 6px; border-radius: 3px; background: var(--surface); border: 1px solid var(--border); overflow: hidden; width: 100%; margin-top: 8px; }
  .bar span { display: block; height: 100%; background: var(--accent); }
  .defence { margin-bottom: 14px; }
  .defence + .defence { margin-top: 12px; }
  label.field { display: block; font-size: 12px; font-weight: 600; margin: 0 0 2px; }
  .hint { font-size: 12px; color: var(--muted); margin: 0 0 6px; }
  textarea {
    width: 100%; font: inherit; color: inherit; background: #fff; min-height: 70px; resize: vertical;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  textarea:focus, input[type=range]:focus-visible, button:focus-visible { outline: 2px solid var(--accent); outline-offset: 1px; }
  .nav { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; }
  .compare { margin-top: 16px; display: none; }
  .compare.is-visible { display: block; }
  .scroll { overflow-x: auto; }
  table { border-collapse: collapse; width: 100%; font-size: 13px; min-width: 24rem; }
  th, td { border-bottom: 1px solid var(--border); padding: 6px 8px; text-align: right; font-variant-numeric: tabular-nums; }
  th:first-child, td:first-child { text-align: left; font-variant-numeric: normal; }
  thead th { font-size: 11px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--muted); font-weight: 600; }
  tr.is-mover td { background: var(--surface); font-weight: 600; }
  .verdict { margin: 10px 0 0; color: var(--muted); }
  .actions { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 12px; }
  @media (max-width: 620px) {
    .row { grid-template-columns: 1fr 3.5rem; }
    .row label { grid-column: 1 / -1; }
    .regime dl { grid-template-columns: 1fr; gap: 2px; }
    .regime dd { margin-bottom: 6px; }
  }
</style>
</head>
<body>
<p class="eyebrow">Allocation exercise</p>
<h1>Portfolio allocation across regimes</h1>
<p class="lede" id="lede"></p>
<ul class="steps">
  <li>Divide the effort across the agendas.</li>
  <li>Defend the allocation: which technique gets the marginal slice of effort, what payoff carries that choice, and which spend binds.</li>
</ul>

<div class="tabs" id="tabs" role="tablist" aria-label="Scenarios"></div>

<div class="card regime">
  <h2 id="sc-title"></h2>
  <dl id="sc-body"></dl>
</div>

<div class="card alloc">
  <h3>Allocation</h3>
  <div id="sliders"></div>
  <div class="meter">
    <span><span class="num" id="spent">0</span> of 10 researchers allocated</span>
    <span class="note" id="remaining"></span>
  </div>
  <div class="bar"><span id="barfill" style="width:0%"></span></div>
</div>

<div class="card defence">
  <h3>Defend it</h3>
  <label class="field" for="margin">The margin</label>
  <p class="hint">Which technique gets the marginal slice of effort, and through which channel does its payoff flow: usefulness, evidence, or direct?</p>
  <textarea id="margin" aria-label="The margin"></textarea>
  <label class="field" for="binding" style="margin-top:12px">The binding constraint</label>
  <p class="hint">The one allocation you would trade any other for.</p>
  <textarea id="binding" aria-label="The binding constraint"></textarea>
</div>

<div class="nav">
  <span class="note" id="progress"></span>
  <span class="actions">
    <button type="button" id="prev">Previous scenario</button>
    <button type="button" id="next" class="primary">Next scenario</button>
  </span>
</div>

<div class="card compare" id="compare">
  <h2>Your three calls, side by side</h2>
  <p class="hint">Researchers allocated per agenda. The spread is the gap between your largest and smallest allocation for that agenda across the three regimes.</p>
  <div class="scroll">
    <table id="ctable">
      <thead><tr><th>Agenda</th><th>Sc. 1</th><th>Sc. 2</th><th>Sc. 3</th><th>Spread</th></tr></thead>
      <tbody></tbody>
    </table>
  </div>
  <p class="verdict" id="verdict"></p>
  <div class="actions">
    <button type="button" id="ask">Ask the tutor to challenge my calls</button>
  </div>
</div>

<script>
  var PROMPT = "You direct a safety team with a budget of 10 researchers' worth of effort for the next stage of development. Each scenario below stipulates a full regime: the world state, epistemic state, and resource state, the misalignment world you are (probably) in, the capability stage you are approaching (in the AI Futures Model's milestones), and the initial plan (A-D) you start under.";

  var TOTAL = 10;
  var STEP = 0.5;

  var AGENDAS = [
    { id: "control-protocols", label: "Control protocols" },
    { id: "alignment-research", label: "Alignment research" },
    { id: "interpretability", label: "Interpretability" },
    { id: "verification-evals", label: "Verification & evals science" },
    { id: "scalable-oversight", label: "Scalable oversight" },
    { id: "policy-pause", label: "Policy, pause & coordination" },
    { id: "security", label: "Security" }
  ];

  var SCENARIOS = [
    {
      id: "schemeria-racing",
      short: "Scenario 1",
      title: "Scenario 1: Schemeria, racing, approaching autonomous coding",
      rows: [
        ["World state", "models are coherently scheming, leading to two caught sandboxed escape attempts this year; research output is middling to verify."],
        ["Epistemic state", "line-by-line transcripts of both catches, and evals that reproduce the behavior."],
        ["Resource state", "a rival lab sits a few months behind; the catches spiked will, but delay remains nearly unbuyable and safety compute is capped at a small share."],
        ["Approaching stage (AIFM)", "Frontier models are about to automate most of the lab's coding."],
        ["Initial plan", "Plan C. the lab holds a lead of a few months and, after the catches, is willing to spend much of it on misalignment; there is no serious government involvement."]
      ]
    },
    {
      id: "quiet-world-slack",
      short: "Scenario 2",
      title: "Scenario 2: Easyland or Lurkville?, treaty slack, approaching autonomous research",
      rows: [
        ["World state", "nothing rules out scheming, sloppiness, or apparent-success seeking; checkability of research output unknown, probably middling."],
        ["Epistemic state", "evals look fine, no catches, no incidents; the reassuring picture is consistent with Easyland and with Lurkville."],
        ["Resource state", "an international agreement has bought roughly a decade of slack"],
        ["Approaching stage (AIFM)", "Frontier models are about to run research autonomously."],
        ["Initial plan", "Plan A. a strong international agreement has mostly eliminated the race and bought a long slowdown with major investment in safety."]
      ]
    },
    {
      id: "slopolis-commercial",
      short: "Scenario 3",
      title: "Scenario 3: Slopolis under commercial pressure, mid-stage",
      rows: [
        ["World state", "no signs of scheming, but models are apparent-success seekers"],
        ["Epistemic state", "good visibility into the gaming itself, almost none into research quality."],
        ["Resource state", "heavy commercial pressure; the public is annoyed but not scared, so the product-wide usefulness tax is expensive"],
        ["Approaching stage (AIFM)", "Frontier models meaningfully multiply human researchers but cannot yet work unsupervised."],
        ["Initial plan", "Plan D. leadership doesn't take misalignment concerns very seriously in practice; a small safety team works under the commercial pressure."]
      ]
    }
  ];

  var STORE_KEY = "lens-widget-xlab-control-portfolio-allocation";

  var state = {};
  SCENARIOS.forEach(function (s) {
    var alloc = {};
    AGENDAS.forEach(function (a) { alloc[a.id] = 0; });
    state[s.id] = { alloc: alloc, margin: "", binding: "" };
  });

  var current = 0;
  var completed = false;

  var tabsEl = document.getElementById("tabs");
  var titleEl = document.getElementById("sc-title");
  var bodyEl = document.getElementById("sc-body");
  var slidersEl = document.getElementById("sliders");
  var spentEl = document.getElementById("spent");
  var remainingEl = document.getElementById("remaining");
  var barEl = document.getElementById("barfill");
  var marginEl = document.getElementById("margin");
  var bindingEl = document.getElementById("binding");
  var progressEl = document.getElementById("progress");
  var prevBtn = document.getElementById("prev");
  var nextBtn = document.getElementById("next");
  var compareEl = document.getElementById("compare");
  var ctableBody = document.querySelector("#ctable tbody");
  var verdictEl = document.getElementById("verdict");
  var askBtn = document.getElementById("ask");

  document.getElementById("lede").textContent = PROMPT;

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function fmt(n) { return (Math.round(n * 2) / 2).toFixed(1).replace(/\.0$/, ""); }
  function spentOn(sid) {
    var t = 0;
    AGENDAS.forEach(function (a) { t += state[sid].alloc[a.id] || 0; });
    return Math.round(t * 2) / 2;
  }
  function isAnswered(sid) {
    return spentOn(sid) === TOTAL &&
      state[sid].margin.trim().length > 0 &&
      state[sid].binding.trim().length > 0;
  }
  function answeredCount() {
    var n = 0;
    SCENARIOS.forEach(function (s) { if (isAnswered(s.id)) n++; });
    return n;
  }

  // Tabs
  var tabBtns = {};
  var tabDots = {};
  SCENARIOS.forEach(function (s, i) {
    var b = el("button", "tab");
    b.type = "button";
    var dot = el("span", "dot");
    b.appendChild(dot);
    b.appendChild(el("span", null, s.short));
    b.addEventListener("click", function () { current = i; render(); });
    tabsEl.appendChild(b);
    tabBtns[s.id] = b;
    tabDots[s.id] = dot;
  });

  // Sliders
  var sliderInputs = {};
  var sliderVals = {};
  AGENDAS.forEach(function (a) {
    var row = el("div", "row");
    var lab = el("label", null, a.label);
    lab.setAttribute("for", "sl-" + a.id);
    var input = document.createElement("input");
    input.type = "range";
    input.id = "sl-" + a.id;
    input.min = "0";
    input.max = String(TOTAL);
    input.step = String(STEP);
    input.value = "0";
    var val = el("span", "val", "0");
    input.addEventListener("input", function () {
      state[SCENARIOS[current].id].alloc[a.id] = parseFloat(input.value);
      render();
      persist();
    });
    row.appendChild(lab);
    row.appendChild(input);
    row.appendChild(val);
    slidersEl.appendChild(row);
    sliderInputs[a.id] = input;
    sliderVals[a.id] = val;
  });

  marginEl.addEventListener("input", function () {
    state[SCENARIOS[current].id].margin = marginEl.value;
    render();
    persist();
  });
  bindingEl.addEventListener("input", function () {
    state[SCENARIOS[current].id].binding = bindingEl.value;
    render();
    persist();
  });
  prevBtn.addEventListener("click", function () { if (current > 0) { current--; render(); } });
  nextBtn.addEventListener("click", function () { if (current < SCENARIOS.length - 1) { current++; render(); } });

  function spreadTable() {
    return AGENDAS.map(function (a) {
      var vals = SCENARIOS.map(function (s) { return state[s.id].alloc[a.id] || 0; });
      var lo = Math.min.apply(null, vals);
      var hi = Math.max.apply(null, vals);
      return { label: a.label, vals: vals, spread: Math.round((hi - lo) * 2) / 2 };
    });
  }

  function summary() {
    var lines = ["Portfolio allocation across regimes. Budget: " + TOTAL + " researchers per scenario, half-researcher steps."];
    SCENARIOS.forEach(function (s) {
      var spent = spentOn(s.id);
      lines.push("");
      lines.push(s.title);
      var parts = [];
      AGENDAS.forEach(function (a) {
        var v = state[s.id].alloc[a.id] || 0;
        if (v > 0) parts.push(a.label + " " + fmt(v));
      });
      lines.push("  Allocation (" + fmt(spent) + " of " + TOTAL + " allocated): " + (parts.length ? parts.join(", ") : "nothing allocated yet"));
      lines.push("  The margin: " + (state[s.id].margin.trim() || "(not written yet)"));
      lines.push("  The binding constraint: " + (state[s.id].binding.trim() || "(not written yet)"));
    });
    var rows = spreadTable();
    var hi = 0, lo = Infinity;
    rows.forEach(function (r) { if (r.spread > hi) hi = r.spread; if (r.spread < lo) lo = r.spread; });
    if (hi > 0) {
      var movers = rows.filter(function (r) { return r.spread === hi; }).map(function (r) { return r.label; });
      var stayers = rows.filter(function (r) { return r.spread === lo; }).map(function (r) { return r.label; });
      lines.push("");
      lines.push("Widest swing across the three regimes: " + movers.join(", ") + " (spread " + fmt(hi) + " researchers). Narrowest: " + stayers.join(", ") + " (spread " + fmt(lo) + ").");
    }
    lines.push("Scenarios answered (allocation totals " + TOTAL + " and both defences written): " + answeredCount() + " of " + SCENARIOS.length + ".");
    return lines.join("\n");
  }

  function persist() {
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (!completed && answeredCount() === SCENARIOS.length) {
        completed = true;
        Lens.complete();
      }
    } else {
      try { localStorage.setItem(STORE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }

  function renderCompare() {
    var all = answeredCount() === SCENARIOS.length;
    compareEl.classList.toggle("is-visible", all);
    if (!all) return;
    var rows = spreadTable();
    var maxSpread = 0;
    rows.forEach(function (r) { if (r.spread > maxSpread) maxSpread = r.spread; });
    ctableBody.textContent = "";
    rows.forEach(function (r) {
      var tr = el("tr");
      if (maxSpread > 0 && r.spread === maxSpread) tr.className = "is-mover";
      tr.appendChild(el("td", null, r.label));
      r.vals.forEach(function (v) { tr.appendChild(el("td", null, fmt(v))); });
      tr.appendChild(el("td", null, fmt(r.spread)));
      ctableBody.appendChild(tr);
    });
    var movers = rows.filter(function (r) { return r.spread === maxSpread; }).map(function (r) { return r.label; });
    verdictEl.textContent = maxSpread === 0
      ? "You gave all three regimes the same portfolio. If the regime is doing no work in your answer, say which of the three states you think should have moved it, and why it did not."
      : "The regime moved " + movers.join(" and ") + " the most: " + fmt(maxSpread) + " researchers between your highest and lowest call. Check that your three margins name that swing rather than something the numbers do not show.";
  }

  function render() {
    var s = SCENARIOS[current];
    SCENARIOS.forEach(function (sc) {
      tabBtns[sc.id].classList.toggle("is-active", sc.id === s.id);
      tabBtns[sc.id].setAttribute("aria-current", sc.id === s.id ? "true" : "false");
      tabDots[sc.id].classList.toggle("is-done", isAnswered(sc.id));
    });

    titleEl.textContent = s.title;
    bodyEl.textContent = "";
    s.rows.forEach(function (r) {
      bodyEl.appendChild(el("dt", null, r[0]));
      bodyEl.appendChild(el("dd", null, r[1]));
    });

    AGENDAS.forEach(function (a) {
      var v = state[s.id].alloc[a.id] || 0;
      if (parseFloat(sliderInputs[a.id].value) !== v) sliderInputs[a.id].value = String(v);
      sliderInputs[a.id].setAttribute("aria-valuetext", fmt(v) + " researchers");
      sliderVals[a.id].textContent = fmt(v);
      sliderVals[a.id].classList.toggle("is-set", v > 0);
    });

    var spent = spentOn(s.id);
    spentEl.textContent = fmt(spent);
    var left = Math.round((TOTAL - spent) * 2) / 2;
    remainingEl.textContent = left === 0 ? "Budget exactly spent" : (left > 0 ? fmt(left) + " left to allocate" : "Over budget by " + fmt(-left));
    remainingEl.classList.toggle("is-off", left !== 0);
    barEl.style.width = Math.min(100, (spent / TOTAL) * 100) + "%";

    if (marginEl.value !== state[s.id].margin) marginEl.value = state[s.id].margin;
    if (bindingEl.value !== state[s.id].binding) bindingEl.value = state[s.id].binding;

    progressEl.textContent = answeredCount() + " of " + SCENARIOS.length + " scenarios answered";
    prevBtn.disabled = current === 0;
    nextBtn.disabled = current === SCENARIOS.length - 1;

    renderCompare();
  }

  askBtn.addEventListener("click", function () {
    if (!window.Lens || !Lens.promptTutor) return;
    Lens.promptTutor(
      "I have made my three portfolio calls. Can you challenge them?",
      "The learner has finished XLab's Module 2 capstone allocation exercise. Their calls:\n" + summary() +
      "\nPick the one scenario where the allocation and the stated margin fit together worst and say why. Then ask one question about an agenda whose number barely moved between regimes even though one of the three states changed. Do not hand them a model portfolio; there is no answer key."
    );
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      SCENARIOS.forEach(function (s) {
        var got = saved[s.id];
        if (!got || typeof got !== "object") return;
        if (got.alloc && typeof got.alloc === "object") {
          AGENDAS.forEach(function (a) {
            var v = got.alloc[a.id];
            if (typeof v === "number" && isFinite(v) && v >= 0 && v <= TOTAL) state[s.id].alloc[a.id] = Math.round(v * 2) / 2;
          });
        }
        if (typeof got.margin === "string") state[s.id].margin = got.margin;
        if (typeof got.binding === "string") state[s.id].binding = got.binding;
      });
    }
    completed = !!(meta && meta.completed);
    var first = -1;
    for (var i = 0; i < SCENARIOS.length; i++) { if (!isAnswered(SCENARIOS[i].id)) { first = i; break; } }
    current = first === -1 ? SCENARIOS.length - 1 : first;
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    askBtn.hidden = true;
    var raw = null;
    try { raw = localStorage.getItem(STORE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
</script>
</body>
</html>

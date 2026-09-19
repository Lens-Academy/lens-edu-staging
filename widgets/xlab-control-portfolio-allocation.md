---
id: '34ff02a7-0cba-4299-bac2-7be10271c222'
title: Portfolio allocation across regimes
summary_for_tutor: "XLab's Module 2 capstone exercise as a widget. The lesson page around it carries the framing: the three-part shape of every portfolio answer (allocation, margin, binding constraint), the usefulness/evidence/direct payoff channels, the gloss of Plans A to D, and the brief itself (10 researchers' worth of effort per scenario, seven agendas, half-researcher steps). The widget holds only the acting: three stipulated regimes stacked one after another, each with its world, epistemic and resource state, the AIFM capability stage it approaches and the plan it starts under. For each regime the learner moves seven sliders (control protocols, alignment research, interpretability, verification and evals science, scalable oversight, policy/pause/coordination, security) and writes two short defences, the margin and the binding constraint. A regime counts as answered when its allocation totals exactly 10 and both defences have text; when all three are answered a comparison table appears showing each agenda's three calls and its spread, highlighting the agenda the regime moved most, and Lens.complete fires. There is no answer key; the diagnostic is whether the allocation responds to the three states. The learner's numbers and defences arrive in the widget-state block as they work. If they ask for review, probe whether the allocation actually changed when the regime changed, and whether the named margin matches the numbers they set."
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
  [hidden] { display: none !important; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0 0 8px; }
  h3 { font-size: 12px; font-weight: 600; margin: 14px 0 6px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--muted); }
  .sc { border: 1px solid var(--border); border-left: 3px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; margin-bottom: 16px; }
  .sc.is-answered { border-left-color: var(--accent); }
  .states { margin: 0; display: grid; grid-template-columns: max-content 1fr; gap: 4px 12px; background: var(--surface); border-radius: 6px; padding: 10px 12px; }
  .states dt { font-weight: 600; }
  .states dd { margin: 0; color: var(--muted); }
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
  label.field { display: block; font-size: 12px; font-weight: 600; margin: 12px 0 4px; }
  textarea {
    width: 100%; font: inherit; color: inherit; background: #fff; min-height: 70px; resize: vertical;
    border: 1px solid var(--border); border-radius: 8px; padding: 8px 10px;
  }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  textarea:focus, input[type=range]:focus-visible, button:focus-visible { outline: 2px solid var(--accent); outline-offset: 1px; }
  .compare { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .scroll { overflow-x: auto; }
  table { border-collapse: collapse; width: 100%; font-size: 13px; min-width: 24rem; }
  th, td { border-bottom: 1px solid var(--border); padding: 6px 8px; text-align: right; font-variant-numeric: tabular-nums; }
  th:first-child, td:first-child { text-align: left; font-variant-numeric: normal; }
  thead th { font-size: 11px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--muted); font-weight: 600; }
  tr.is-mover td { background: var(--surface); font-weight: 600; }
  .hint { font-size: 12px; color: var(--muted); margin: 0 0 8px; }
  .verdict { margin: 10px 0 0; color: var(--muted); }
  .actions { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 12px; }
  @media (max-width: 620px) {
    .row { grid-template-columns: 1fr 3.5rem; }
    .row label { grid-column: 1 / -1; }
    .states { grid-template-columns: 1fr; gap: 2px; }
    .states dd { margin-bottom: 6px; }
  }
</style>
</head>
<body>
<div id="scenarios"></div>

<div class="compare" id="compare" hidden>
  <h2>Your three calls, side by side</h2>
  <p class="hint">Spread is the gap between your largest and smallest call for that agenda.</p>
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

  var completed = false;
  var ui = {};

  var scenariosEl = document.getElementById("scenarios");
  var compareEl = document.getElementById("compare");
  var ctableBody = document.querySelector("#ctable tbody");
  var verdictEl = document.getElementById("verdict");
  var askBtn = document.getElementById("ask");

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

  SCENARIOS.forEach(function (s) {
    var sec = el("section", "sc");
    sec.setAttribute("aria-label", s.title);
    sec.appendChild(el("h2", null, s.title));

    var dl = el("dl", "states");
    s.rows.forEach(function (r) {
      dl.appendChild(el("dt", null, r[0]));
      dl.appendChild(el("dd", null, r[1]));
    });
    sec.appendChild(dl);

    sec.appendChild(el("h3", null, "Allocation"));
    var inputs = {};
    var vals = {};
    AGENDAS.forEach(function (a) {
      var row = el("div", "row");
      var lab = el("label", null, a.label);
      lab.setAttribute("for", "sl-" + s.id + "-" + a.id);
      var input = document.createElement("input");
      input.type = "range";
      input.id = "sl-" + s.id + "-" + a.id;
      input.min = "0";
      input.max = String(TOTAL);
      input.step = String(STEP);
      input.value = "0";
      var val = el("span", "val", "0");
      input.addEventListener("input", function () {
        state[s.id].alloc[a.id] = parseFloat(input.value);
        render();
        persist();
      });
      row.appendChild(lab);
      row.appendChild(input);
      row.appendChild(val);
      sec.appendChild(row);
      inputs[a.id] = input;
      vals[a.id] = val;
    });

    var meter = el("div", "meter");
    var spentWrap = el("span");
    var spentNum = el("span", "num", "0");
    spentWrap.appendChild(spentNum);
    spentWrap.appendChild(el("span", null, " of " + TOTAL + " researchers allocated"));
    var note = el("span", "note");
    meter.appendChild(spentWrap);
    meter.appendChild(note);
    sec.appendChild(meter);
    var bar = el("div", "bar");
    var fill = el("span");
    fill.style.width = "0%";
    bar.appendChild(fill);
    sec.appendChild(bar);

    var marginLab = el("label", "field", "The margin");
    marginLab.setAttribute("for", "margin-" + s.id);
    var marginEl = document.createElement("textarea");
    marginEl.id = "margin-" + s.id;
    marginEl.setAttribute("aria-label", "The margin, " + s.short);
    marginEl.addEventListener("input", function () {
      state[s.id].margin = marginEl.value;
      render();
      persist();
    });
    sec.appendChild(marginLab);
    sec.appendChild(marginEl);

    var bindingLab = el("label", "field", "The binding constraint");
    bindingLab.setAttribute("for", "binding-" + s.id);
    var bindingEl = document.createElement("textarea");
    bindingEl.id = "binding-" + s.id;
    bindingEl.setAttribute("aria-label", "The binding constraint, " + s.short);
    bindingEl.addEventListener("input", function () {
      state[s.id].binding = bindingEl.value;
      render();
      persist();
    });
    sec.appendChild(bindingLab);
    sec.appendChild(bindingEl);

    scenariosEl.appendChild(sec);
    ui[s.id] = {
      sec: sec, inputs: inputs, vals: vals, spent: spentNum,
      note: note, fill: fill, margin: marginEl, binding: bindingEl
    };
  });

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
    compareEl.hidden = !all;
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
    SCENARIOS.forEach(function (s) {
      var u = ui[s.id];
      AGENDAS.forEach(function (a) {
        var v = state[s.id].alloc[a.id] || 0;
        if (parseFloat(u.inputs[a.id].value) !== v) u.inputs[a.id].value = String(v);
        u.inputs[a.id].setAttribute("aria-valuetext", fmt(v) + " researchers");
        u.vals[a.id].textContent = fmt(v);
        u.vals[a.id].classList.toggle("is-set", v > 0);
      });

      var spent = spentOn(s.id);
      u.spent.textContent = fmt(spent);
      var left = Math.round((TOTAL - spent) * 2) / 2;
      u.note.textContent = left === 0 ? "Budget exactly spent" : (left > 0 ? fmt(left) + " left to allocate" : "Over budget by " + fmt(-left));
      u.note.classList.toggle("is-off", left !== 0);
      u.fill.style.width = Math.min(100, (spent / TOTAL) * 100) + "%";

      if (u.margin.value !== state[s.id].margin) u.margin.value = state[s.id].margin;
      if (u.binding.value !== state[s.id].binding) u.binding.value = state[s.id].binding;

      u.sec.classList.toggle("is-answered", isAnswered(s.id));
    });

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


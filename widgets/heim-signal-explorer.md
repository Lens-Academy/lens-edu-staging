---
id: '8fff99fe-5263-422b-b2a3-af858c2a9470'
title: "Provider signal explorer"
summary_for_tutor: "Explorer over the fifteen observable signals in Heim et al. (2024): the five data-attribute categories of Table 3 and the ten observable attributes of Appendix B Table 4. The learner filters by which verification activity a signal serves and whether providers already collect it, sorts by ease of implementation and ease of circumvention, and opens each signal to read its row detail, which also quotes the Table 2 feasibility verdict for every verification activity that signal serves. Completion fires once all fifteen rows have been opened. The page just above the widget carries the Appendix B excerpt with Table 4 in full; Tables 2 and 3 are not excerpted in this lens, so the widget is the only place the learner meets them. If the learner asks for help, push them to separate what a signal proves from what it merely suggests, and to notice that the signals easiest to collect are the hardest to evade, while the ones that would prove the most are not collected at all."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Provider signal explorer</title>
<!-- Built from articles/heim-governing-through-the-cloud-the-intermediary-role-of-compute-providers-in-ai-regulation.md: Table 3 (lines 366 to 368), Table 4 (lines 721 to 733), Table 2 verification row (lines 248 to 254). -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&amp;family=Newsreader:opsz,wght@6..72,400;6..72,600&amp;display=swap" media="print" onload="this.media='all'">
<style>
  [hidden] { display: none !important; }
  * { box-sizing: border-box; }
  body {
    margin: 0; padding: 14px;
    background: #faf8f3; color: #1a1a1a;
    font-family: "DM Sans", system-ui, -apple-system, "Segoe UI", sans-serif;
    font-size: 14px; line-height: 1.5;
  }
  .hint { margin: 0 0 12px; color: #5a5a5a; }
  .bar {
    background: #ffffff; border: 1px solid #e8e5df; border-radius: 8px;
    padding: 10px 12px; margin-bottom: 10px;
  }
  .grp { display: flex; flex-wrap: wrap; align-items: baseline; gap: 6px; margin-bottom: 8px; }
  .grp:last-child { margin-bottom: 0; }
  .grp > .lbl {
    flex: 0 0 auto; min-width: 104px; color: #5a5a5a; font-size: 12px;
    text-transform: uppercase; letter-spacing: .04em;
  }
  .chip {
    font: inherit; font-size: 13px; cursor: pointer;
    background: #ffffff; color: #1a1a1a;
    border: 1px solid #e8e5df; border-radius: 999px; padding: 3px 11px;
  }
  .chip:hover { border-color: #b87018; }
  .chip[aria-pressed="true"] {
    background: #b87018; border-color: #b87018; color: #ffffff; font-weight: 500;
  }
  .chip[aria-pressed="true"]::before { content: "\2713\00a0"; }
  .reset {
    font: inherit; font-size: 13px; cursor: pointer; background: none;
    border: none; color: #b87018; text-decoration: underline; padding: 3px 4px;
  }
  .count { margin: 0 0 8px; color: #5a5a5a; font-size: 13px; }
  .count b { color: #1a1a1a; font-weight: 500; }
  .wrap { overflow-x: auto; border: 1px solid #e8e5df; border-radius: 8px; background: #ffffff; }
  .tbl { min-width: 720px; }
  .head, .row { display: grid; grid-template-columns: minmax(200px, 2.4fr) minmax(140px, 1.3fr) 120px 150px 150px; }
  .head { border-bottom: 1px solid #e8e5df; background: #faf8f3; }
  .head .sort {
    font: inherit; font-size: 12px; font-weight: 500; text-transform: uppercase; letter-spacing: .04em;
    color: #5a5a5a; background: none; border: none; cursor: pointer;
    text-align: left; padding: 9px 10px; width: 100%;
  }
  .head .sort:hover { color: #b87018; }
  .head .sort .arw { color: #b87018; }
  .row {
    font: inherit; text-align: left; width: 100%; cursor: pointer;
    background: #ffffff; color: #1a1a1a; border: none; border-top: 1px solid #e8e5df;
    padding: 0;
  }
  .tbl .row:first-of-type { border-top: none; }
  .row:hover { background: #fbf7f0; }
  .row[aria-pressed="true"] { background: #fbf2e6; box-shadow: inset 3px 0 0 #b87018; }
  .row > span { padding: 9px 10px; min-width: 0; }
  .row .nm { font-weight: 500; display: flex; gap: 6px; align-items: baseline; }
  .row .nm .tick { color: #b87018; flex: 0 0 auto; }
  .row .eg { display: block; font-weight: 400; color: #5a5a5a; font-size: 12.5px; margin-top: 2px; }
  .row .sub { color: #5a5a5a; font-size: 12.5px; }
  .lab { display: none; color: #5a5a5a; font-size: 11.5px; text-transform: uppercase; letter-spacing: .04em; }
  .src { display: inline-block; font-size: 11.5px; color: #5a5a5a; border: 1px solid #e8e5df; border-radius: 4px; padding: 0 5px; margin-left: 6px; }
  .empty { padding: 14px; color: #5a5a5a; }
  .detail {
    margin-top: 12px; background: #ffffff; border: 1px solid #e8e5df; border-radius: 8px; padding: 12px 14px;
  }
  .detail h2 { font-family: "Newsreader", Georgia, serif; font-size: 18px; font-weight: 600; margin: 0 0 2px; }
  .detail .prov { color: #5a5a5a; font-size: 12.5px; margin: 0 0 10px; }
  .detail dl { margin: 0; }
  .detail dt {
    color: #5a5a5a; font-size: 11.5px; text-transform: uppercase; letter-spacing: .04em; margin-top: 10px;
  }
  .detail dt:first-of-type { margin-top: 0; }
  .detail dd { margin: 2px 0 0; }
  .detail .acts { margin: 4px 0 0; padding: 0; list-style: none; }
  .detail .acts li { border-left: 2px solid #e8e5df; padding: 2px 0 2px 9px; margin-top: 6px; }
  .detail .acts b { font-weight: 500; }
  .detail .acts .fe { display: block; color: #5a5a5a; font-size: 13px; }
  .placeholder { color: #5a5a5a; }
  button:focus-visible, .row:focus-visible { outline: 2px solid #b87018; outline-offset: 1px; }
  @media (max-width: 620px) {
    .head { display: none; }
    .tbl { min-width: 0; }
    .row { display: block; padding: 4px 0 8px; }
    .row > span { display: block; padding: 3px 10px; }
    .lab { display: block; }
    .wrap { overflow-x: visible; }
    .grp > .lbl { min-width: 0; flex-basis: 100%; }
  }
</style>
</head>
<body>
<p class="hint">Filter and sort the signals a compute provider can see, then open each one to read what it can and cannot verify.</p>

<div class="bar">
  <div class="grp" id="g-act"><span class="lbl" id="l-act">Serves</span></div>
  <div class="grp" id="g-col"><span class="lbl" id="l-col">Collected</span></div>
  <div class="grp" id="g-src"><span class="lbl" id="l-src">Source</span></div>
</div>

<p class="count" id="count"></p>

<div class="wrap">
  <div class="tbl" role="group" aria-label="Observable signals">
    <div class="head" id="head"></div>
    <div id="rows"></div>
  </div>
</div>

<div class="detail" id="detail"></div>

<script>
(function () {
  "use strict";

  var T2 = {
    iv: "Likely feasible with a sufficiently rigorous process, focused on customers accessing large-scale compute resources.",
    wc: "Likely feasible for detecting large-scale pre-training and inference workloads.",
    ca: "Feasible, with multiple approaches possible for large-scale pre-training/inference workloads.",
    dv: "Currently not possible without directly observing customer code or data. Confidential computing techniques could change this."
  };
  var ACT = {
    iv: "Identity verification",
    wc: "Workload classification",
    ca: "Compute accounting",
    dv: "Detailed workload verification"
  };
  var COLL = { yes: "Already collected", maybe: "Potentially", no: "Not collected" };
  var IMPL = [
    "Not currently possible",
    "Needs customer consent",
    "Existing tooling, not bare metal",
    "Existing tooling",
    "Already collected"
  ];
  var CIRC = [
    "Highly difficult or impossible",
    "Difficult",
    "Possible, moderate cost",
    "Possible, substantial cost",
    "Possible, low barrier"
  ];

  var SIGNALS = [
    { id: "cat-customer", src: "t3", name: "Customer information",
      eg: "name, billing address, credit card data, IP addresses, date and time of access, device identifiers, language",
      acts: ["iv"], coll: "yes", impl: 4, circ: 4,
      uses: "Identity verification.",
      novelty: "No, already collected.",
      state: "Compute providers already collect a wide range of customer information. Customers can potentially spoof much of this data to try to avoid identification." },
    { id: "cat-billing", src: "t3", name: "Billing-related technical information",
      eg: "hardware configuration requested by a customer, number of hours that hardware resources are used",
      acts: ["wc", "ca"], coll: "yes", impl: 4, circ: 0,
      uses: "Workload classification. Compute accounting.",
      novelty: "No, already collected.",
      state: "Already collected by compute providers for billing purposes. Highly difficult or impossible for customers to alter to avoid monitoring." },
    { id: "cat-cluster", src: "t3", name: "Cluster-level technical information",
      eg: "power consumption, network bandwidth utilization between nodes",
      acts: ["wc", "ca"], coll: "yes", impl: 4, circ: 3,
      uses: "Workload classification. Compute accounting.",
      novelty: "No, already collected.",
      state: "Already collected by compute providers for service health monitoring and maintenance. Customers could modify their workloads to avoid certain forms of cluster-level verification, likely with performance penalties." },
    { id: "cat-node", src: "t3", name: "Node-level technical information",
      eg: "AI accelerator core utilization, AI accelerator memory bandwidth utilization",
      acts: ["wc", "ca"], coll: "maybe", impl: 3, circ: 3,
      uses: "Workload classification. Compute accounting.",
      novelty: "Potentially, already collected.",
      state: "Possible to collect using existing tooling, and collected by some compute providers. Customers could modify their workloads to avoid certain forms of node-level verification, likely with performance penalties." },
    { id: "cat-workload", src: "t3", name: "Workload-level technical information",
      eg: "code, data, hyperparameters",
      acts: ["wc", "ca", "dv"], coll: "no", impl: 0, circ: null,
      uses: "Workload classification. Compute accounting. Detailed workload verification.",
      novelty: "Yes, currently not collected.",
      state: "Compute providers cannot typically retain or inspect this information (by design). Confidential computing tools could potentially be developed to verify information in a privacy-preserving manner." },

    { id: "hw-config", src: "t4", name: "Hardware configuration requested by the customer",
      acts: ["wc"], coll: "yes", impl: 4, circ: 0,
      uses: "Workload classification. The quantity of AI accelerators requested and networking setup are strongly suggestive of the workloads a customer intends to run.",
      novelty: "No, already collected.",
      implText: "Already collected by compute providers to set up and provision infrastructure.",
      circText: "Highly difficult or impossible." },
    { id: "hours", src: "t4", name: "Number of hours that resources (e.g., AI accelerators) are in use",
      acts: ["wc", "ca"], coll: "yes", impl: 4, circ: 0,
      uses: "Workload classification, compute accounting. Allows high-level boundary setting on workload type/size.",
      novelty: "No, already collected.",
      implText: "Already collected by compute providers for billing purposes.",
      circText: "Highly difficult or impossible." },
    { id: "power", src: "t4", name: "Power draw",
      acts: ["wc", "ca"], coll: "yes", impl: 3, circ: 3,
      uses: "Workload classification, compute accounting. Allows high-level boundary setting on workload type/size, as increased power draw corresponds to increased throughput for a particular device. Power consumption over time may allow differentiation of inference from training (Patel et al. 2023).",
      novelty: "No, already collected.",
      implText: "Possible to collect using existing tooling. Already collected by some compute providers.",
      circText: "Possible, but would involve substantial cost efficiency penalties." },
    { id: "net-between", src: "t4", name: "Network bandwidth between AI accelerator servers",
      acts: ["wc", "ca"], coll: "yes", impl: 3, circ: 3,
      uses: "Workload classification, compute accounting. Large AI training workloads require high bandwidth between servers. Different communication patterns correspond to different kinds of workloads, and bandwidth utilization is related to the quantity of computation performed on each server.",
      novelty: "No, already collected.",
      implText: "Possible to collect using existing tooling. Already collected by some compute providers.",
      circText: "Possible, but could involve substantial cost efficiency penalties." },
    { id: "net-within", src: "t4", name: "Network bandwidth within AI accelerator servers",
      acts: ["wc", "ca"], coll: "yes", impl: 3, circ: 3,
      uses: "Workload classification, compute accounting. Different bandwidth patterns correspond to different kinds of workloads, and bandwidth utilization is related to the quantity of computation performed within each server.",
      novelty: "No, already collected.",
      implText: "Possible to collect using existing tooling. Already collected by some compute providers.",
      circText: "Possible, but could involve substantial cost efficiency penalties." },
    { id: "util", src: "t4", name: "AI accelerator core & memory bandwidth utilization",
      acts: ["wc", "ca"], coll: "yes", impl: 2, circ: 3,
      uses: "Workload classification, compute accounting. Large AI workloads typically have high memory bandwidth utilization, and core utilization will tend to be constant for training, while inference is typically variable.",
      novelty: "No, already collected.",
      implText: "Possible to collect using existing tooling. Difficult to collect for bare-metal services.",
      circText: "Possible, but could involve substantial cost efficiency penalties." },
    { id: "counters", src: "t4", name: "Performance counters by numerical precision",
      acts: ["wc", "ca"], coll: "maybe", impl: 2, circ: 2,
      uses: "Workload classification, compute accounting. Lower precision is common in AI workloads and allows differentiation from most scientific computing workloads and possibly gaming. Counters also provide a direct measurement of operations consumed by a workload.",
      novelty: "Potentially. This degree of telemetry on an individual customer is unusual. Policies for collection and analysis would need to be clearly outlined in provider’s terms of service.",
      implText: "Possible to collect using existing tooling. Difficult to collect for bare metal services.",
      circText: "Possible, but could involve moderate cost efficiency penalties." },
    { id: "weights", src: "t4", name: "Modification of weights in memory",
      acts: ["wc", "ca"], coll: "maybe", impl: 0, circ: 1,
      uses: "Workload classification, compute accounting. Model training requires changing the weights in memory using a backward pass. Typically the only large data structures in memory are the weights and activations, so it should be possible to observe whether stores are made to that region of memory. The magnitude and frequency of memory updates are related to the quantity of compute consumed.",
      novelty: "Potentially.",
      implText: "Not currently possible.",
      circText: "Difficult: training requires modifying weights in memory to be highly performant." },
    { id: "hyper", src: "t4", name: "Workload hyperparameters",
      acts: ["wc", "ca", "dv"], coll: "no", impl: 1, circ: null,
      uses: "Workload classification, compute accounting, detailed workload verification.",
      novelty: "Yes. Can potentially be made privacy-preserving using confidential computing techniques.",
      implText: "Possible to collect with customer consent.",
      circText: "Unclear (highly dependent on implementation)." },
    { id: "dataset", src: "t4", name: "Training dataset",
      acts: ["wc", "ca", "dv"], coll: "no", impl: 1, circ: null,
      uses: "Workload classification, compute accounting, detailed workload verification.",
      novelty: "Yes. Can potentially be made privacy-preserving using confidential computing techniques.",
      implText: "Possible to collect with customer consent.",
      circText: "Unclear (highly dependent on implementation)." }
  ];

  var SRC = { t3: "Table 3 category", t4: "Table 4 attribute" };

  var COLS = [
    { key: "name", label: "Signal" },
    { key: "acts", label: "Serves" },
    { key: "coll", label: "Collected today" },
    { key: "impl", label: "Ease of implementation" },
    { key: "circ", label: "Ease of circumvention" }
  ];

  var state = { act: [], coll: [], src: [], sort: "name", dir: 1, sel: null, opened: [] };
  var saveTimer = null;

  function el(tag, cls, txt) {
    var n = document.createElement(tag);
    if (cls) { n.className = cls; }
    if (txt !== undefined && txt !== null) { n.textContent = txt; }
    return n;
  }

  function toggle(list, v) {
    var i = list.indexOf(v);
    if (i === -1) { list.push(v); } else { list.splice(i, 1); }
  }

  function visible() {
    return SIGNALS.filter(function (s) {
      if (state.act.length && !state.act.some(function (a) { return s.acts.indexOf(a) !== -1; })) { return false; }
      if (state.coll.length && state.coll.indexOf(s.coll) === -1) { return false; }
      if (state.src.length && state.src.indexOf(s.src) === -1) { return false; }
      return true;
    });
  }

  var COLLRANK = { yes: 0, maybe: 1, no: 2 };

  function sorted(list) {
    var k = state.sort, d = state.dir;
    var out = list.slice();
    out.sort(function (a, b) {
      var va, vb;
      if (k === "name") { va = a.name.toLowerCase(); vb = b.name.toLowerCase(); }
      else if (k === "acts") { va = ACT[a.acts[0]]; vb = ACT[b.acts[0]]; }
      else if (k === "coll") { va = COLLRANK[a.coll]; vb = COLLRANK[b.coll]; }
      else if (k === "impl") { va = a.impl; vb = b.impl; }
      else {
        if (a.circ === null && b.circ === null) { return a.name.localeCompare(b.name); }
        if (a.circ === null) { return 1; }
        if (b.circ === null) { return -1; }
        va = a.circ; vb = b.circ;
      }
      if (va < vb) { return -1 * d; }
      if (va > vb) { return 1 * d; }
      return a.name.localeCompare(b.name);
    });
    return out;
  }

  function chipRow(container, labelId, options, listName) {
    var old = container.querySelectorAll("button");
    var i;
    for (i = 0; i < old.length; i++) { old[i].remove(); }
    options.forEach(function (o) {
      var b = el("button", "chip", o.label);
      b.type = "button";
      b.setAttribute("aria-pressed", state[listName].indexOf(o.value) !== -1 ? "true" : "false");
      b.setAttribute("aria-describedby", labelId);
      b.addEventListener("click", function () {
        toggle(state[listName], o.value);
        if (state.sel && !visible().some(function (s) { return s.id === state.sel; })) { state.sel = null; }
        render();
        queueSave();
      });
      container.appendChild(b);
    });
  }

  function renderFilters() {
    chipRow(document.getElementById("g-act"), "l-act", [
      { value: "iv", label: ACT.iv }, { value: "wc", label: ACT.wc },
      { value: "ca", label: ACT.ca }, { value: "dv", label: ACT.dv }
    ], "act");
    chipRow(document.getElementById("g-col"), "l-col", [
      { value: "yes", label: COLL.yes }, { value: "maybe", label: COLL.maybe }, { value: "no", label: COLL.no }
    ], "coll");
    chipRow(document.getElementById("g-src"), "l-src", [
      { value: "t3", label: SRC.t3 }, { value: "t4", label: SRC.t4 }
    ], "src");
  }

  function renderHead() {
    var head = document.getElementById("head");
    head.textContent = "";
    COLS.forEach(function (c) {
      var b = el("button", "sort");
      b.type = "button";
      b.appendChild(document.createTextNode(c.label));
      if (state.sort === c.key) {
        b.appendChild(el("span", "arw", state.dir === 1 ? " ▲" : " ▼"));
        b.setAttribute("aria-sort", state.dir === 1 ? "ascending" : "descending");
      }
      b.addEventListener("click", function () {
        if (state.sort === c.key) { state.dir = -state.dir; } else { state.sort = c.key; state.dir = 1; }
        render();
        queueSave();
      });
      head.appendChild(b);
    });
  }

  function cell(row, label, node) {
    var sp = el("span");
    sp.appendChild(el("span", "lab", label));
    sp.appendChild(node);
    row.appendChild(sp);
  }

  function renderRows() {
    var host = document.getElementById("rows");
    host.textContent = "";
    var list = sorted(visible());
    if (!list.length) {
      host.appendChild(el("p", "empty", "No signal matches these filters. Clear a filter to see more."));
      return;
    }
    list.forEach(function (s) {
      var r = el("button", "row");
      r.type = "button";
      r.setAttribute("aria-pressed", state.sel === s.id ? "true" : "false");

      var nm = el("span", "nm");
      if (state.opened.indexOf(s.id) !== -1) {
        var tk = el("span", "tick", "✓");
        tk.setAttribute("aria-label", "opened");
        nm.appendChild(tk);
      }
      var inner = el("span");
      inner.appendChild(document.createTextNode(s.name));
      inner.appendChild(el("span", "src", s.src === "t3" ? "Table 3" : "Table 4"));
      if (s.eg) { inner.appendChild(el("span", "eg", "e.g., " + s.eg)); }
      nm.appendChild(inner);
      cell(r, "Signal", nm);

      cell(r, "Serves", el("span", "sub", s.acts.map(function (a) { return ACT[a]; }).join(", ")));
      cell(r, "Collected today", el("span", "sub", COLL[s.coll]));
      cell(r, "Ease of implementation", el("span", "sub", IMPL[s.impl]));
      cell(r, "Ease of circumvention", el("span", "sub", s.circ === null ? "Unclear" : CIRC[s.circ]));

      r.addEventListener("click", function () {
        state.sel = s.id;
        if (state.opened.indexOf(s.id) === -1) { state.opened.push(s.id); }
        render();
        queueSave();
        if (state.opened.length === SIGNALS.length && window.Lens && window.Lens.complete) {
          window.Lens.complete();
        }
      });
      host.appendChild(r);
    });
  }

  function dd(dl, term, text) {
    dl.appendChild(el("dt", null, term));
    dl.appendChild(el("dd", null, text));
  }

  function renderDetail() {
    var box = document.getElementById("detail");
    box.textContent = "";
    var s = null, i;
    for (i = 0; i < SIGNALS.length; i++) { if (SIGNALS[i].id === state.sel) { s = SIGNALS[i]; } }
    if (!s) {
      box.appendChild(el("p", "placeholder", "Select a signal to read what it can verify, whether providers already hold it, and how hard it is to collect or evade."));
      return;
    }
    box.appendChild(el("h2", null, s.name));
    box.appendChild(el("p", "prov", SRC[s.src] + (s.eg ? ". e.g., " + s.eg : "")));

    var dl = el("dl");
    dd(dl, "Uses", s.uses);

    dl.appendChild(el("dt", null, "Feasibility of those activities (Table 2)"));
    var ddn = el("dd");
    var ul = el("ul", "acts");
    s.acts.forEach(function (a) {
      var li = el("li");
      li.appendChild(el("b", null, ACT[a]));
      li.appendChild(el("span", "fe", T2[a]));
      ul.appendChild(li);
    });
    ddn.appendChild(ul);
    dl.appendChild(ddn);

    dd(dl, "Involves collection of data not already widely collected?", s.novelty);
    if (s.src === "t4") {
      dd(dl, "Ease of implementation", s.implText);
      dd(dl, "Ease of circumvention", s.circText);
    } else {
      dd(dl, "Current state of collection, validation, and possible circumvention", s.state);
    }
    box.appendChild(dl);
  }

  function renderCount() {
    var p = document.getElementById("count");
    p.textContent = "";
    var vis = visible().length;
    var b = el("b", null, state.opened.length + " of " + SIGNALS.length);
    p.appendChild(b);
    p.appendChild(document.createTextNode(" signals opened. " + vis + " of " + SIGNALS.length + " shown by the current filters."));
    if (state.act.length || state.coll.length || state.src.length) {
      var r = el("button", "reset", "Clear filters");
      r.type = "button";
      r.addEventListener("click", function () {
        state.act = []; state.coll = []; state.src = [];
        render();
        queueSave();
      });
      p.appendChild(document.createTextNode(" "));
      p.appendChild(r);
    }
  }

  function render() {
    renderFilters();
    renderHead();
    renderRows();
    renderDetail();
    renderCount();
  }

  function sortLabel() {
    var i;
    for (i = 0; i < COLS.length; i++) { if (COLS[i].key === state.sort) { return COLS[i].label.toLowerCase(); } }
    return state.sort;
  }

  function summary() {
    var names = state.opened.map(function (id) {
      var i;
      for (i = 0; i < SIGNALS.length; i++) { if (SIGNALS[i].id === id) { return SIGNALS[i].name; } }
      return id;
    });
    var f = [];
    if (state.act.length) { f.push("serves " + state.act.map(function (a) { return ACT[a]; }).join(" or ")); }
    if (state.coll.length) { f.push("collected " + state.coll.map(function (c) { return COLL[c]; }).join(" or ")); }
    if (state.src.length) { f.push("source " + state.src.map(function (x) { return SRC[x]; }).join(" or ")); }
    return "Opened " + state.opened.length + " of " + SIGNALS.length + " signals"
      + (names.length ? ": " + names.join("; ") : "")
      + ". Sorted by " + sortLabel() + (state.dir === 1 ? " ascending" : " descending")
      + ". Filters: " + (f.length ? f.join("; ") : "none") + ".";
  }

  function persist() {
    var data = {
      v: 1, opened: state.opened, sel: state.sel,
      act: state.act, coll: state.coll, src: state.src,
      sort: state.sort, dir: state.dir
    };
    if (window.Lens && window.Lens.saveState) {
      window.Lens.saveState(data, summary());
    } else {
      try { window.localStorage.setItem("heim-signal-explorer", JSON.stringify(data)); } catch (e) { /* ignore */ }
    }
  }

  function queueSave() {
    if (saveTimer) { window.clearTimeout(saveTimer); }
    saveTimer = window.setTimeout(function () { saveTimer = null; persist(); }, 400);
  }

  function restore(data) {
    if (!data || typeof data !== "object") { return; }
    var ids = SIGNALS.map(function (s) { return s.id; });
    if (Array.isArray(data.opened)) {
      state.opened = data.opened.filter(function (x) { return ids.indexOf(x) !== -1; });
    }
    if (typeof data.sel === "string" && ids.indexOf(data.sel) !== -1) { state.sel = data.sel; }
    if (Array.isArray(data.act)) { state.act = data.act.filter(function (x) { return ACT[x]; }); }
    if (Array.isArray(data.coll)) { state.coll = data.coll.filter(function (x) { return COLL[x]; }); }
    if (Array.isArray(data.src)) { state.src = data.src.filter(function (x) { return SRC[x]; }); }
    var keys = COLS.map(function (c) { return c.key; });
    if (typeof data.sort === "string" && keys.indexOf(data.sort) !== -1) { state.sort = data.sort; }
    if (data.dir === -1 || data.dir === 1) { state.dir = data.dir; }
    render();
    if (state.opened.length === SIGNALS.length && window.Lens && window.Lens.complete) {
      window.Lens.complete();
    }
  }

  document.addEventListener("visibilitychange", function () {
    if (document.visibilityState === "hidden" && saveTimer) {
      window.clearTimeout(saveTimer);
      saveTimer = null;
      persist();
    }
  });

  render();

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (data) { restore(data); });
  } else if (!window.Lens) {
    try {
      var raw = window.localStorage.getItem("heim-signal-explorer");
      if (raw) { restore(JSON.parse(raw)); }
    } catch (e) { /* ignore */ }
  }
}());
</script>
</body>
</html>

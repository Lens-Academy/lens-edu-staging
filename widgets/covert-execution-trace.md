---
id: '808102f6-fc8d-41da-aa29-167896f44a47'
title: End-to-end execution trace
summary_for_tutor: "An interactive version of the two system diagrams in section 3.2 of Cankaya's 'A system overview for near-term, low-trust AI compute verification' (Evidence capture; Evidence evaluation, Plan A). Each diagram shows the prover, the verifier, the prover's physically monitored facility and its parts (network taps and memory probes, air-gapped AI compute pods, raw evidence data and manifest, the auditing environment with three TCBs and the comparison-gated disclosure) with the links between them (hashes over sanitized egress, challenge over controlled ingress, response, disclosure), each labelled with the section that specifies it. The learner switches between the two phases and steps through the article's numbered trace (5 capture steps, 7 evaluation steps); each step shows the article's own sentence for that step and highlights the parts of the diagram it involves. Under the evaluation phase the three conditions that end the trace early are listed. Done means the learner has opened all 12 steps."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>End-to-end execution trace</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track reading "A system overview for near-term, low-trust AI compute verification" (Cankaya), section 3.2 figures and numbered trace. Not an XLab widget: an interactive rendering of the article's own figures and text. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --accent: #b87018; --accent-hover: #9a5c10; --accent-tint: #f7ead8;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 24px; line-height: 1.2; }
  h2 { font-size: 18px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 6px; }
  .lede { color: var(--muted); margin: 8px 0 0; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--page); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .tabs { display: flex; gap: 8px; flex-wrap: wrap; margin: 16px 0 12px; }
  .tab { font-weight: 500; }
  .tab .seen { color: var(--muted); font-weight: 400; font-size: 12px; margin-left: 6px; }
  .diagram-wrap { overflow-x: auto; border: 1px solid var(--border); border-radius: 8px; background: var(--page); }
  .diagram-wrap svg { display: block; min-width: 620px; width: 100%; height: auto; font-family: var(--font-ui); }
  .node rect, .node ellipse { fill: #fff; stroke: var(--text); stroke-width: 1.5; transition: stroke-width 120ms; }
  .node.owner-verifier rect { fill: var(--accent-tint); stroke: var(--accent); }
  .node.owner-third rect { fill: #ececec; stroke: #777; }
  .node.owner-split rect { fill: url(#split); stroke: var(--text); }
  .node text { font-size: 12px; fill: var(--text); }
  .node .ref { font-size: 10px; fill: var(--muted); }
  .node .tag { font-size: 9px; fill: var(--muted); letter-spacing: 0.06em; text-transform: uppercase; }
  .zone rect { fill: none; stroke: var(--text); stroke-width: 1.5; stroke-dasharray: 8 5; }
  .zone text { font-size: 13px; font-weight: 600; fill: var(--text); }
  .zone .sub { font-size: 10px; font-weight: 400; fill: var(--muted); }
  .link path, .link line { fill: none; stroke: #888; stroke-width: 2; }
  .link.both path { stroke: var(--text); stroke-dasharray: 5 4; }
  .link text { font-size: 10px; fill: var(--muted); }
  .link text.strong { font-weight: 600; fill: var(--text); }
  svg.has-focus .node:not(.is-lit) { opacity: 0.35; }
  svg.has-focus .link:not(.is-lit) { opacity: 0.25; }
  svg.has-focus .zone:not(.is-lit) { opacity: 0.45; }
  .node.is-lit rect { stroke: var(--accent); stroke-width: 3; }
  .link.is-lit path, .link.is-lit line { stroke: var(--accent); stroke-width: 3; }
  .link.is-lit text { fill: var(--accent); font-weight: 600; }
  .legend { display: flex; gap: 14px; flex-wrap: wrap; font-size: 12px; color: var(--muted); margin: 8px 0 0; }
  .legend span { display: inline-flex; align-items: center; gap: 6px; }
  .swatch { width: 14px; height: 14px; border: 1.5px solid var(--text); border-radius: 3px; display: inline-block; }
  .swatch.v { background: var(--accent-tint); border-color: var(--accent); }
  .swatch.t { background: #ececec; border-color: #777; }
  .swatch.b { border: 0; border-top: 2px dashed var(--text); height: 0; }
  .steps { display: grid; gap: 16px; margin-top: 16px; }
  @media (min-width: 760px) { .steps { grid-template-columns: 15rem 1fr; align-items: start; } }
  .step-list { display: flex; flex-direction: column; gap: 6px; }
  .step-btn { display: flex; gap: 10px; align-items: baseline; }
  .step-btn .num { font-family: var(--font-heading); font-weight: 600; font-size: 16px; min-width: 1.4em; }
  .step-btn .brief { color: var(--muted); font-size: 13px; }
  .step-btn.is-seen .num::after { content: " \2713"; color: var(--accent); font-size: 12px; }
  .step-detail { min-height: 6rem; }
  .step-detail p { margin: 0 0 8px; }
  .step-detail .comp { font-size: 12px; color: var(--muted); }
  .exits { margin-top: 16px; border-top: 1px solid var(--border); padding-top: 12px; }
  .exits ul { margin: 6px 0 0; padding-left: 20px; }
  .exits li { margin-bottom: 4px; }
  .status { margin-top: 12px; font-size: 12px; color: var(--muted); display: flex; gap: 12px; align-items: center; flex-wrap: wrap; }
  .status .done { color: var(--accent); font-weight: 600; }
  .nav { display: flex; gap: 8px; margin-top: 10px; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
</style>
</head>
<body>
<section aria-labelledby="et-title">
  <p class="eyebrow">Cankaya, section 3.2 End-to-end execution trace</p>
  <h1 id="et-title">We follow one inference request</h1>
  <p class="lede">We follow one inference request, but the tap sees it only as part of an undifferentiated byte stream. The request is never singled out at capture, only reconstructed later in the auditing environment.</p>

  <div class="tabs" id="tabs" role="tablist"></div>

  <div class="diagram-wrap" id="diagram"></div>
  <div class="legend" id="legend"></div>

  <div class="steps">
    <div class="step-list" id="step-list"></div>
    <div class="card step-detail" id="step-detail" aria-live="polite"></div>
  </div>

  <div class="exits" id="exits" hidden></div>

  <div class="status" id="status"></div>
</section>

<script>
(function () {
  var SVG = "http://www.w3.org/2000/svg";

  // Diagram data transcribed from the two figures in section 3.2 (labels and section references verbatim).
  var PHASES = [
    {
      id: "capture",
      tab: "1. Evidence Capture",
      title: "1. Evidence Capture",
      view: [0, 0, 700, 330],
      zones: [
        { id: "facility", x: 250, y: 20, w: 430, h: 290, label: "Prover’s Facility", sub: "physically monitored" },
        { id: "airgap", x: 520, y: 80, w: 140, h: 90, label: "", sub: "air-gap (5.3.1)" }
      ],
      nodes: [
        { id: "prover", x: 20, y: 90, w: 140, h: 44, owner: "prover", label: ["Prover"] },
        { id: "verifier", x: 20, y: 230, w: 140, h: 44, owner: "verifier", label: ["Verifier"] },
        { id: "taps", x: 300, y: 90, w: 150, h: 64, owner: "split", label: ["Network taps", "(& memory probes)"], ref: "(5.1.1)" },
        { id: "pods", x: 535, y: 95, w: 110, h: 44, owner: "prover", label: ["AI compute pods"] },
        { id: "raw", x: 470, y: 230, w: 190, h: 54, owner: "prover", label: ["Raw evidence data"], ref: "(3.2)" }
      ],
      links: [
        { id: "l-prover-taps", d: "M160 112 L300 112", both: false, arrows: "both" },
        { id: "l-taps-pods", d: "M450 117 L535 117", both: false, arrows: "both" },
        { id: "l-taps-raw", d: "M400 154 L400 200 Q400 215 415 215 L520 215 Q535 215 535 230", both: false, arrows: "end" },
        { id: "l-hashes", d: "M360 154 L360 200 Q360 215 345 215 L110 215 Q90 215 90 200 L90 134", both: true, arrows: "end", label: ["hashes;", "sanitized egress", "(4.3.3)"], lx: 200, ly: 200 },
        { id: "l-hashes-v", d: "M90 215 L90 230", both: true, arrows: "end" }
      ],
      legend: ["prover", "verifier", "both"],
      steps: [
        { brief: "The request enters a monitored unit", text: "The request enters a monitored unit over its frontend link and is served, tokens flow back out over the same link (typically wrapped in JSON files). The tap sees the traffic crossing the boundary: this request's bytes, its response tokens, and everything else (SSH sessions, file loads, orchestration, other tenants' traffic).", lit: ["pods", "taps", "l-taps-pods", "airgap"] },
        { brief: "The tap hashes payloads", text: "The tap hashes payloads over network packet-groups, unaware of payload object boundaries or contents. Timestamps are not sent out by the tap, as they may encode information in unverifiable trailing bits. Instead, timing is done by the prover and the verifier, when receiving the hashes.", lit: ["taps"] },
        { brief: "The hashes leave over a split, sanitized fiber link", text: "The hashes leave over a fiber link that is split and sanitized (output cross-check 4.3.2, sanitized egress 4.3.3), so prover and verifier observe identical egress with timing and physical-layer side-channels scrubbed. Both parties store these hashes.", lit: ["taps", "l-hashes", "l-hashes-v", "prover", "verifier"] },
        { brief: "The prover recomputes the same hashes", text: "The prover recomputes the same hashes from their own copy of the captured network traffic, confirming the tap emitted nothing but legitimate commitments.", lit: ["prover", "l-prover-taps", "taps"] },
        { brief: "The prover retains the plaintext and writes a manifest", text: "The prover retains the plaintext (or keeps it reproducible) and writes a manifest.", lit: ["raw", "l-taps-raw", "prover"] }
      ],
      intro: "This phase runs at line rate online, all the time. Nothing in it depends on an object being singled out for analysis.",
      after: "Optionally, memory challenges (section 5.1.2) are a second, independent evidence capture mechanism for ML compute use. Their commitment mechanism is analogous to that of the network taps."
    },
    {
      id: "evaluation",
      tab: "2. Evidence Evaluation (Plan A)",
      title: "2. Evidence Evaluation (Plan A)",
      view: [0, 0, 700, 400],
      zones: [
        { id: "facility", x: 250, y: 15, w: 440, h: 370, label: "Prover’s Facility", sub: "physically monitored" },
        { id: "audit", x: 345, y: 165, w: 335, h: 200, lx: 432, label: "Auditing Environment", sub: "(5.2; 5.3)" }
      ],
      nodes: [
        { id: "verifier", x: 20, y: 120, w: 140, h: 44, owner: "verifier", label: ["Verifier"] },
        { id: "prover", x: 20, y: 250, w: 140, h: 44, owner: "prover", label: ["Prover"] },
        { id: "raw", x: 440, y: 58, w: 200, h: 60, owner: "prover", label: ["Raw evidence data", "+ manifest"], ref: "(3.2)" },
        { id: "tcb1", x: 360, y: 220, w: 80, h: 56, owner: "verifier", label: ["TCB 1"], ref: "(4.3.4)" },
        { id: "tcb2", x: 500, y: 220, w: 80, h: 56, owner: "third", label: ["TCB 2"], ref: "(4.3.4)" },
        { id: "tcb3", x: 590, y: 220, w: 80, h: 56, owner: "prover", label: ["TCB 3"], ref: "(4.3.4)" },
        { id: "gate", x: 410, y: 300, w: 210, h: 56, owner: "split", label: ["Comparison-gated", "disclosure"], ref: "(4.3.2, 5.2.1)" }
      ],
      links: [
        { id: "l-challenge", d: "M160 142 L310 142 Q330 142 330 122 L330 100 Q330 80 350 80 L440 80", both: false, arrows: "end", label: ["challenge;", "controlled ingress", "(4.3.1)"], lx: 205, ly: 104 },
        { id: "l-challenge-tcb", d: "M310 142 Q330 142 330 162 L330 232 Q330 248 346 248 L360 248", both: false, arrows: "end" },
        { id: "l-response", d: "M540 118 L540 196 Q540 208 528 208 L412 208 Q400 208 400 214 L400 220 M540 196 L540 220 M540 196 Q540 208 552 208 L618 208 Q630 208 630 214 L630 220", both: false, arrows: "none", label: ["response"], lx: 578, ly: 150 },
        { id: "l-tcb-gate", d: "M400 276 L400 328 L410 328 M540 276 L540 300 M630 276 L630 328 L620 328", both: false, arrows: "none" },
        { id: "l-disclosure", d: "M515 356 L515 372 L120 372 L120 164 M120 372 L120 294", both: true, arrows: "end", label: ["disclosure;", "sanitized egress", "(4.3.3)"], lx: 185, ly: 338 }
      ],
      legend: ["prover", "verifier", "third", "both"],
      steps: [
        { brief: "The verifier issues a challenge over controlled ingress", text: "The verifier issues a challenge over controlled ingress (4.3.1), a one-way link enforced by a data diode and passive observability through which the prover can monitor the backward direction.", lit: ["verifier", "l-challenge", "l-challenge-tcb"] },
        { brief: "The prover supplies the preimages", text: "The prover supplies the preimages: plaintext slices matching the challenged hashes, the relevant manifest entries, and metadata required for re-computation (see section 5.2.2).", lit: ["prover", "raw", "l-response"] },
        { brief: "Each party's TCB reassembles the challenged objects", text: "Each party's Trusted Computing Base (TCB) independently reassembles the challenged objects and checks them against the manifest and the challenged hashes.", lit: ["tcb1", "tcb2", "tcb3", "audit", "l-response"] },
        { brief: "Each TCB re-executes the workload", text: "Then each TCB verifies the inference workload by re-executing the supposed computation under the declared metadata.", lit: ["tcb1", "tcb2", "tcb3", "audit"] },
        { brief: "The workload is screened for compliance", text: "The reconstructed workload is then screened for compliance (inference vs. training, model on the whitelist, outputs free of blacklisted use; inspector agents 5.2.3).", lit: ["tcb1", "tcb2", "tcb3", "audit"] },
        { brief: "The TCBs cross-check their verdicts", text: "The TCBs cross-check their verdicts (4.3.2). Agreement is required before anything is released.", lit: ["tcb1", "tcb2", "tcb3", "l-tcb-gate", "gate", "audit"] },
        { brief: "The result is released through sanitized egress", text: "The result is released through sanitized egress (4.3.3), split to both parties. By default the disclosure is minimal, e.g. only the challenged hashes if there is no issue. In case of non-compliance, the disclosure could point to the hashes of the suspicious data.", lit: ["gate", "l-disclosure", "prover", "verifier"] }
      ],
      intro: "As long as the hashes and their preimages are in storage, the verifier can challenge random samples at any future point in time. In plan A, evaluation is performed in an isolated environment containing redundant computing platforms receiving identical inputs, and checking each other’s outputs. Plan B removes the need for such a secure environment and replaces them with cryptographic techniques such as Zero-Knowledge-Proofs.",
      exits: {
        lead: "Three conditions end the trace early, and they are distinct.",
        items: [
          "A challenged preimage that is missing or does not hash to its commitment means the prover has failed the challenge outright.",
          "A re-computation that does not reproduce the committed output means either the declared metadata was false, or there was a technical problem in the setup, or the workload was not as claimed, warranting investigation.",
          "TCB disagreement means no disclosure leaves and the disagreement itself triggers investigation."
        ],
        after: "Faults, if triggered on purpose, can leak one bit of information to the verifier, per event. The prover and verifier need a pre-agreed budgeted rate for such faults, beyond which suspicion is raised."
      }
    }
  ];

  var OWNER_LABEL = { prover: "Prover-owned", verifier: "Verifier-owned", third: "Third-party-owned", both: "Seen by both", split: "Prover-owned / Verifier-owned" };
  var TOTAL = PHASES[0].steps.length + PHASES[1].steps.length;

  var state = { phase: "capture", step: null, seen: {} };
  var completed = false;

  var els = {
    tabs: document.getElementById("tabs"),
    diagram: document.getElementById("diagram"),
    legend: document.getElementById("legend"),
    list: document.getElementById("step-list"),
    detail: document.getElementById("step-detail"),
    exits: document.getElementById("exits"),
    status: document.getElementById("status")
  };

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function svgEl(tag, attrs) {
    var n = document.createElementNS(SVG, tag);
    for (var k in attrs) if (attrs.hasOwnProperty(k)) n.setAttribute(k, attrs[k]);
    return n;
  }
  function svgText(x, y, lines, cls, lineHeight) {
    var t = svgEl("text", { x: x, y: y, "text-anchor": "middle" });
    if (cls) t.setAttribute("class", cls);
    for (var i = 0; i < lines.length; i++) {
      var ts = svgEl("tspan", { x: x, dy: i === 0 ? 0 : (lineHeight || 14) });
      ts.textContent = lines[i];
      t.appendChild(ts);
    }
    return t;
  }
  function phase() {
    for (var i = 0; i < PHASES.length; i++) if (PHASES[i].id === state.phase) return PHASES[i];
    return PHASES[0];
  }
  function seenCount() { var n = 0; for (var k in state.seen) if (state.seen.hasOwnProperty(k)) n++; return n; }
  function key(p, i) { return p.id + ":" + i; }

  function renderTabs() {
    els.tabs.textContent = "";
    PHASES.forEach(function (p) {
      var b = el("button", "tab" + (p.id === state.phase ? " is-active" : ""));
      b.setAttribute("role", "tab");
      b.setAttribute("aria-selected", p.id === state.phase ? "true" : "false");
      b.appendChild(document.createTextNode(p.tab));
      var n = 0; for (var i = 0; i < p.steps.length; i++) if (state.seen[key(p, i)]) n++;
      b.appendChild(el("span", "seen", n + " of " + p.steps.length + " steps"));
      b.addEventListener("click", function () { state.phase = p.id; state.step = null; render(); save(); });
      els.tabs.appendChild(b);
    });
  }

  function renderDiagram() {
    var p = phase();
    els.diagram.textContent = "";
    var svg = svgEl("svg", { viewBox: p.view.join(" "), role: "img" });
    svg.setAttribute("aria-label", p.title + " diagram");
    var defs = svgEl("defs", {});
    var grad = svgEl("linearGradient", { id: "split", x1: "0", y1: "0", x2: "1", y2: "0" });
    var s1 = svgEl("stop", { offset: "0.5", "stop-color": "#f7ead8" });
    var s2 = svgEl("stop", { offset: "0.5", "stop-color": "#ffffff" });
    grad.appendChild(s1); grad.appendChild(s2); defs.appendChild(grad);
    var marker = svgEl("marker", { id: "arrow", viewBox: "0 0 10 10", refX: "9", refY: "5", markerWidth: "7", markerHeight: "7", orient: "auto-start-reverse" });
    var mp = svgEl("path", { d: "M0 0 L10 5 L0 10 z", fill: "#666" });
    marker.appendChild(mp); defs.appendChild(marker);
    svg.appendChild(defs);

    var title = svgText(p.view[2] / 2, 14, [p.title], null);
    title.setAttribute("style", "font-size:13px;font-weight:600");
    title.setAttribute("y", "12");
    svg.appendChild(title);

    p.zones.forEach(function (z) {
      var g = svgEl("g", { "data-id": z.id }); g.setAttribute("class", "zone");
      g.appendChild(svgEl("rect", { x: z.x, y: z.y, width: z.w, height: z.h, rx: 14 }));
      var zx = z.lx || (z.x + z.w / 2);
      if (z.label) g.appendChild(svgText(zx, z.y + 20, [z.label]));
      if (z.sub) { var st = svgText(zx, z.y + (z.label ? 34 : z.h - 8), [z.sub], "sub"); g.appendChild(st); }
      svg.appendChild(g);
    });
    p.links.forEach(function (l) {
      var g = svgEl("g", { "data-id": l.id }); g.setAttribute("class", "link" + (l.both ? " both" : ""));
      var path = svgEl("path", { d: l.d });
      if (l.arrows === "end") path.setAttribute("marker-end", "url(#arrow)");
      if (l.arrows === "both") { path.setAttribute("marker-end", "url(#arrow)"); path.setAttribute("marker-start", "url(#arrow)"); }
      g.appendChild(path);
      if (l.label) {
        var t = svgText(l.lx, l.ly, l.label, null, 12);
        var first = t.firstChild; if (first) first.setAttribute("class", "strong");
        g.appendChild(t);
      }
      svg.appendChild(g);
    });
    p.nodes.forEach(function (n) {
      var g = svgEl("g", { "data-id": n.id }); g.setAttribute("class", "node owner-" + n.owner);
      g.appendChild(svgEl("rect", { x: n.x, y: n.y, width: n.w, height: n.h, rx: n.h / 2 }));
      var lines = n.label.slice();
      var baseY = n.y + n.h / 2 - (lines.length - 1) * 7 + (n.ref ? -4 : 4);
      var t = svgText(n.x + n.w / 2, baseY, lines, null, 14);
      t.setAttribute("style", "font-weight:600");
      g.appendChild(t);
      if (n.ref) g.appendChild(svgText(n.x + n.w / 2, n.y + n.h - 8, [n.ref], "ref"));
      svg.appendChild(g);
    });
    els.diagram.appendChild(svg);

    els.legend.textContent = "";
    p.legend.forEach(function (o) {
      var s = el("span");
      var sw = el("i", "swatch " + (o === "verifier" ? "v" : o === "third" ? "t" : o === "both" ? "b" : ""));
      sw.setAttribute("aria-hidden", "true");
      s.appendChild(sw);
      s.appendChild(document.createTextNode(OWNER_LABEL[o]));
      els.legend.appendChild(s);
    });
    applyHighlight();
  }

  function applyHighlight() {
    var svg = els.diagram.querySelector("svg");
    if (!svg) return;
    var p = phase();
    var lit = (state.step !== null && p.steps[state.step]) ? p.steps[state.step].lit : null;
    if (!lit) { svg.classList.remove("has-focus"); } else { svg.classList.add("has-focus"); }
    var groups = svg.querySelectorAll("g[data-id]");
    for (var i = 0; i < groups.length; i++) {
      var id = groups[i].getAttribute("data-id");
      if (lit && lit.indexOf(id) !== -1) groups[i].classList.add("is-lit"); else groups[i].classList.remove("is-lit");
    }
  }

  function renderSteps() {
    var p = phase();
    els.list.textContent = "";
    p.steps.forEach(function (s, i) {
      var b = el("button", "step-btn" + (state.step === i ? " is-active" : "") + (state.seen[key(p, i)] ? " is-seen" : ""));
      b.setAttribute("aria-pressed", state.step === i ? "true" : "false");
      b.appendChild(el("span", "num", String(i + 1)));
      b.appendChild(el("span", "brief", s.brief));
      b.addEventListener("click", function () { openStep(i); });
      els.list.appendChild(b);
    });

    els.detail.textContent = "";
    if (state.step === null || !p.steps[state.step]) {
      els.detail.appendChild(el("p", "eyebrow", p.title));
      els.detail.appendChild(el("p", null, p.intro));
      els.detail.appendChild(el("p", "comp", "Pick a step to see the article's sentence for it and the parts of the diagram it involves."));
    } else {
      var s = p.steps[state.step];
      els.detail.appendChild(el("p", "eyebrow", p.title + ", step " + (state.step + 1) + " of " + p.steps.length));
      els.detail.appendChild(el("p", null, s.text));
      var names = [];
      s.lit.forEach(function (id) {
        p.nodes.forEach(function (n) { if (n.id === id) names.push(n.label.join(" ")); });
        p.zones.forEach(function (z) { if (z.id === id) names.push(z.label || z.sub); });
        p.links.forEach(function (l) { if (l.id === id && l.label) names.push(l.label.length > 1 ? l.label[0].replace(/;$/, "") + " (" + l.label[1] + ")" : l.label[0]); });
      });
      els.detail.appendChild(el("p", "comp", "Highlighted: " + names.join("; ")));
      if (state.step === p.steps.length - 1 && p.after) els.detail.appendChild(el("p", "comp", p.after));
      var nav = el("div", "nav");
      if (state.step > 0) { var prev = el("button", null, "Previous step"); prev.addEventListener("click", function () { openStep(state.step - 1); }); nav.appendChild(prev); }
      if (state.step < p.steps.length - 1) { var next = el("button", null, "Next step"); next.addEventListener("click", function () { openStep(state.step + 1); }); nav.appendChild(next); }
      else if (p.id === "capture") { var go = el("button", null, "Go to Evidence Evaluation"); go.addEventListener("click", function () { state.phase = "evaluation"; state.step = null; render(); save(); }); nav.appendChild(go); }
      els.detail.appendChild(nav);
    }

    if (p.exits) {
      els.exits.hidden = false;
      els.exits.textContent = "";
      els.exits.appendChild(el("h2", null, p.exits.lead));
      var ul = el("ul");
      p.exits.items.forEach(function (t) { ul.appendChild(el("li", null, t)); });
      els.exits.appendChild(ul);
      els.exits.appendChild(el("p", "comp", p.exits.after));
    } else {
      els.exits.hidden = true;
    }
  }

  function renderStatus() {
    els.status.textContent = "";
    var n = seenCount();
    els.status.appendChild(el("span", null, n + " of " + TOTAL + " steps opened"));
    if (n >= TOTAL) els.status.appendChild(el("span", "done", "✓ Trace complete"));
    var reset = el("button", null, "Reset");
    reset.addEventListener("click", function () { state = { phase: "capture", step: null, seen: {} }; render(); save(); });
    els.status.appendChild(reset);
  }

  function openStep(i) {
    var p = phase();
    state.step = i;
    state.seen[key(p, i)] = true;
    render();
    save();
  }

  function render() { renderTabs(); renderDiagram(); renderSteps(); renderStatus(); }

  function summary() {
    var p = phase();
    var parts = [];
    parts.push("Cankaya section 3.2 execution trace. Learner has opened " + seenCount() + " of " + TOTAL + " steps (" + PHASES[0].steps.length + " in Evidence Capture, " + PHASES[1].steps.length + " in Evidence Evaluation, Plan A).");
    parts.push("Currently viewing " + p.title + (state.step !== null && p.steps[state.step] ? ", step " + (state.step + 1) + ": " + p.steps[state.step].brief + "." : ", no step selected."));
    var unseen = [];
    PHASES.forEach(function (ph) { ph.steps.forEach(function (s, i) { if (!state.seen[key(ph, i)]) unseen.push(ph.tab + " step " + (i + 1)); }); });
    if (unseen.length) parts.push("Not yet opened: " + unseen.join(", ") + "."); else parts.push("All steps opened; trace complete.");
    return parts.join(" ");
  }

  function save() {
    var done = seenCount() >= TOTAL;
    if (window.Lens) {
      Lens.saveState({ phase: state.phase, step: state.step, seen: state.seen }, summary());
      if (done && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("covert-execution-trace", JSON.stringify(state)); } catch (e) {}
    }
  }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      state.phase = saved.phase === "evaluation" ? "evaluation" : "capture";
      state.step = (typeof saved.step === "number") ? saved.step : null;
      state.seen = (saved.seen && typeof saved.seen === "object") ? saved.seen : {};
    }
    if (meta && meta.completed) completed = true;
    render();
  }

  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var restored = null;
    try { restored = JSON.parse(localStorage.getItem("covert-execution-trace") || "null"); } catch (e) {}
    hydrate(restored, null);
  }
})();
</script>
</body>
</html>

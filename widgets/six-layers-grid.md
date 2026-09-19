---
id: '08c51eef-41bb-490e-bfa7-f7f1addf2c80'
title: Six verification layers by subgoal
summary_for_tutor: "An interactive version of Figure 2 of Baker et al. (2025), 'Verifying International Agreements on AI'. The widget is the live grid plus a coverage test: six verification layer rows (on-chip security features; off-chip network taps; off-chip analog sensors; whistleblower programs; interviews of personnel; national intelligence activities) against the four verification subgoals (1.A model and output histories, 1.B evaluations, 2.A compute accounting, 2.B data center detection), each cell naming the mechanism that layer uses for that subgoal. Clicking a layer row opens the paper's summary of that layer, its key advantages and key disadvantages (Tables 1, 5, 7 and 8), what it requires (Table 2 for layers 1 to 3, Section 4.3 for layers 4 to 6) and its mechanism for each subgoal; clicking a subgoal header or coverage tile opens the paper's Section 3.2 definition and the mechanism each layer offers for it, with switched-off layers struck through. Each row has an On/Off switch: switching a layer off greys and strikes out its cells and updates four coverage tiles plus a verdict line, so the learner can test the paper's claim that each layer is independently sufficient. Any single layer left on still covers all four subgoals; only switching every layer off loses coverage. The row keeps a visible 'opened' mark, the status line counts layers opened and layers on, and done means all six layers opened and at least one layer switched off. The page around the widget carries the framing prose: the two-subgoal decomposition, the paper's definition of a verification layer as one of six largely independent assurances, and the Figure 2 caption sit in the lesson text immediately above it, and the four article excerpts of Sections 4.1 and 4.2 come before that."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Six verification layers by subgoal</title>
<!-- Built from articles/baker-verifying-international-agreements-on-ai-six-layers-of-verification-for-rules-on-large-scale-ai-development-and-deployment.md: Figure 2 (line 95), Table 1 (lines 79 to 91), Table 2 (lines 105 to 113), Table 5 (line 378), Table 7 (line 438), Table 8 (line 520), Figure 6 and Figure 7 captions, Section 3.2 subgoal definitions, Section 4 layer definition, Section 4.3 prerequisites. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --page: #faf8f3; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --accent: #b87018; --accent-hover: #9a5c10; --accent-tint: #f7ead8;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  [hidden] { display: none !important; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 24px; line-height: 1.2; }
  h2 { font-size: 18px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 6px; }
  .lede { color: var(--muted); margin: 8px 0 12px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--page); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .grid-wrap { overflow-x: auto; border: 1px solid var(--border); border-radius: 8px; background: var(--page); padding: 12px; }
  .grid { display: grid; grid-template-columns: 7.5rem 8.5rem repeat(4, minmax(8.5rem, 1fr)); gap: 6px; min-width: 760px; align-items: stretch; }
  .corner { grid-column: 1 / span 2; }
  .subgoal { display: flex; flex-direction: column; gap: 4px; padding: 8px 10px; }
  .subgoal .code { display: inline-block; width: 26px; height: 26px; border-radius: 50%; background: var(--muted); color: #fff; font-size: 11px; font-weight: 600; text-align: center; line-height: 26px; }
  .subgoal .name { font-style: italic; font-size: 12px; }
  .subgoal .goal { font-size: 12px; color: var(--muted); }
  .subgoal.is-active .code { background: var(--accent); }
  .group { display: flex; align-items: center; justify-content: center; text-align: center; font-weight: 600; font-size: 12px; padding: 6px; border-right: 1px solid var(--border); color: var(--muted); }
  .layer-cell { display: flex; flex-direction: column; gap: 6px; align-items: flex-start; justify-content: center; }
  .layer { display: flex; flex-direction: column; justify-content: center; font-weight: 600; font-size: 13px; padding: 6px 8px; width: 100%; }
  .layer small { font-weight: 400; color: var(--muted); font-size: 11px; }
  .layer.is-seen::after { content: "\2713 opened"; font-weight: 400; font-size: 10px; color: var(--accent); letter-spacing: 0.06em; text-transform: uppercase; margin-top: 2px; }
  .toggle { display: inline-flex; align-items: center; gap: 6px; font-size: 11px; padding: 3px 8px; border-radius: 999px; letter-spacing: 0.06em; text-transform: uppercase; color: var(--muted); }
  .toggle .dot { width: 9px; height: 9px; border-radius: 50%; background: var(--accent); border: 1px solid var(--accent); }
  .toggle.is-off { border-style: dashed; }
  .toggle.is-off .dot { background: transparent; border: 1px solid var(--muted); }
  .row-off .layer { color: var(--muted); font-weight: 500; }
  .row-off .lname { text-decoration: line-through; }
  .cell { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 10px; font-size: 12px; display: flex; align-items: center; justify-content: center; text-align: center; min-height: 3.2rem; }
  .cell.wide { grid-column: 3 / span 4; }
  .cell.is-lit { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: var(--accent-tint); }
  .cell.is-off { border-style: dashed; border-color: var(--border); background: var(--page); color: #8a8a8a; box-shadow: none; text-decoration: line-through; }
  .grid.has-focus .cell:not(.is-lit) { opacity: 0.45; }
  .coverage { margin-top: 12px; display: grid; grid-template-columns: repeat(auto-fit, minmax(9.5rem, 1fr)); gap: 8px; }
  .cov { display: flex; flex-direction: column; gap: 4px; padding: 8px 10px; }
  .cov .code { display: inline-block; width: 26px; height: 26px; border-radius: 50%; background: var(--muted); color: #fff; font-size: 11px; font-weight: 600; text-align: center; line-height: 26px; }
  .cov.is-active .code { background: var(--accent); }
  .cov .cname { font-size: 12px; font-style: italic; }
  .cov .count { font-size: 12px; color: var(--muted); }
  .cov.is-gone { border-style: dashed; background: var(--page); }
  .cov.is-gone .count { color: var(--text); font-weight: 600; }
  .dots { display: flex; gap: 3px; }
  .dots span { width: 9px; height: 9px; border-radius: 50%; border: 1px solid var(--muted); }
  .dots span.on { background: var(--accent); border-color: var(--accent); }
  .verdict { margin-top: 10px; font-size: 13px; border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: var(--page); }
  .verdict.is-gone { border-color: var(--accent); }
  .verdict .fam { display: block; color: var(--muted); font-size: 12px; margin-top: 4px; }
  .detail { margin-top: 16px; min-height: 8rem; }
  .detail p { margin: 0 0 8px; }
  .detail .k { font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--muted); margin: 12px 0 2px; }
  .detail ul { margin: 4px 0 8px; padding-left: 20px; }
  .detail li { margin-bottom: 4px; }
  .detail li.off { color: var(--muted); text-decoration: line-through; }
  .detail .note { font-size: 12px; color: var(--muted); }
  .status { margin-top: 12px; font-size: 12px; color: var(--muted); display: flex; gap: 12px; align-items: center; flex-wrap: wrap; }
  .status .done { color: var(--accent); font-weight: 600; }
</style>
</head>
<body>
<section aria-label="Six verification layers by subgoal">
  <p class="lede" id="sl-hint">Click a layer or a subgoal to open it, and switch layers off to see which subgoals keep coverage.</p>

  <div class="grid-wrap"><div class="grid" id="grid" role="table"></div></div>

  <div class="coverage" id="coverage"></div>
  <p class="verdict" id="verdict"></p>

  <div class="card detail" id="detail" aria-live="polite" hidden></div>

  <div class="status" id="status"></div>
</section>

<script>
(function () {
  // Subgoal headers are transcribed from Figure 2; definitions from Section 3.2 of the paper.
  var SUBGOALS = [
    { id: "1A", name: "Model & output histories:", goal: "Verify declared compute uses are accurate",
      def: "Subgoal 1.A: Verify that declared uses of AI compute are declared accurately, i.e., the Prover actually did the claimed development or deployment. Equivalently, verify that declared AI models and outputs are generated as declared. More specifically, a Verifier could need to verify the accuracy of declared (1.A.1) AI training, (1.A.2) AI inference, or (1.A.3) non-AI uses of AI compute." },
    { id: "1B", name: "Evaluations:", goal: "Verify declared compute uses have the required properties",
      def: "Subgoal 1.B: Assuming that the declared uses are accurate (as is verified per Subgoal 1.A), verify they have the required properties. For example, the Verifier might evaluate an AI model’s capabilities, or assess what kinds of data the model was run on, to check for compliance. The substance of these tests would depend on what rules are being verified (Section 2.1), though as we will discuss, the infrastructure for running tests could be rule-agnostic." },
    { id: "2A", name: "Compute accounting:", goal: "Verify no large, undeclared uses of declared clusters exist",
      def: "Subgoal 2.A: Verify that there are no undeclared, large-scale uses of declared AI compute clusters. In other words, ensure AI compute use is accounted for, among declared AI compute clusters." },
    { id: "2B", name: "Data center detection:", goal: "Verify no large, undeclared uses of undeclared clusters exist",
      def: "Subgoal 2.B: Verify that there are no undeclared, large-scale AI compute clusters that could be used for violations. (Recall that we include large-scale, decentralized AI compute here (Section 2.2).) This subgoal can be further broken down into verifying there are no such AI compute clusters (2.B.1) as parts of known AI data centers, nor (2.B.2) as standalone clusters." }
  ];
  // Layer rows: cells from Figure 2; name, summary, advantages, disadvantages from Tables 1, 5, 7 and 8;
  // requirements from Table 2 (layers 1 to 3 only, as the table itself states) and Section 4.3 (layers 4 to 6);
  // notes from the captions of Figures 6 and 7.
  var CROSS = "Cross-cutting (Table 2): R&D funding (e.g., by AISIs, philanthropists, DARPA); pilot programs (e.g., voluntary corporate commitments, AISI collaborations); red teaming of developed proposals.";
  var NO_TABLE2 = "Table 2 lists no R&D or infrastructure challenges for layers 4 to 6: its filters and the unclassified nature of the research leave those rows out. Section 4.3 instead names these conditions.";
  var GROUPS = [
    { label: "“On-chip” verification layer", layers: [0], fam: "on-chip" },
    { label: "“Off-chip” verification layers", layers: [1, 2], fam: "off-chip" },
    { label: "Personnel-based verification layers", layers: [3, 4, 5], fam: "personnel-based" }
  ];
  var LAYERS = [
    { row: "Layer 1", sub: "", name: "On-chip security features (i.e., secure boot, Confidential Computing)", section: "Section 4.1",
      cells: ["Hardware-backed workload certificates", "Hardware-backed evals", "Hardware-backed workload certificates", "Tamper-proof, compliance-locked AI chips"],
      summary: "Security features built into AI chips may enable verification, such as by ensuring that AI chips log traces of their activities for confidential analysis.",
      adv: "Offers maximum transparency into AI chips’ uses.",
      dis: "Poses unsolved technical problems and severe security challenges (e.g., untrusted suppliers). Insecure AI chips may need to be replaced.",
      reqSrc: "Table 2, row 1",
      req: [
        "System software protocol: given verifiable system software (with access to e.g., kernels, memory), verify workload code, and model and data locations, despite any potential obfuscation.",
        "Hardware design attestation: given a scanned hardware layout and Hardware Description Language (HDL), check if they match.",
        "Hardware security features: develop highly vetted, open-source, dedicated hardware designs for secure boot, Confidential Computing, and on-chip tamper-proofing.",
        "Design adoption: adopt the above designs into leading AI chips."
      ],
      reqNote: CROSS,
      note: "" },
    { row: "Layer 2", sub: "(network taps)", name: "Off-chip network tap (and analysis) (e.g. “FlexHEGs”)", section: "Section 4.2",
      cells: ["Network taps & analysis", "Backup evals on separate chips", "Network taps & analysis", "Verifying AI chips' chain of custody"],
      summary: "Mutually vetted devices could intercept data exchanged between chips, then check for discrepancies with declared uses.",
      adv: "Could be retrofitted to existing AI chips and optimized for security.",
      dis: "Poses technical, logistical, and security challenges. Strongest versions need redesigned chip-adjacent hardware.",
      reqSrc: "Table 2, row 2",
      req: [
        "Network tap analysis: given a cluster’s inter-accelerator data (including kernels), verify that the cluster executed only a claimed workload.",
        "Network taps: design and manufacture appropriate network taps, or identify suitable existing tech.",
        "Trusted clusters: build small compute clusters that are or can be mutually physically secured."
      ],
      reqNote: CROSS,
      note: "Note “verifying AI chips’ chain of custody“ and “tamper-proof, compliance-locked AI servers“ could just as well be swapped; the point is that they are two redundant off-chip mechanisms for addressing hidden AI compute clusters. We consider them “off-chip“ because they neither rely on features built into chips nor on leaks or disclosures from personnel. Additionally, tamper-proof enclosures and security cameras for chain-of-custody verification could be considered off-chip devices." },
    { row: "Layer 3", sub: "(analog sensors)", name: "Off-chip analog sensors (and analysis, e.g., proof-of-learning)", section: "Section 4.2",
      cells: ["Partial workload re-execution with constraints", "More backup evals on separate chips", "Analog sensors & analysis", "Tamper-proof, compliance-locked AI servers"],
      summary: "Physically secured chips could check that (i) declared AI compute uses are accurate (e.g., reproducible) and (ii) their compute use adds up to the expected total (estimated with analog sensors, e.g., power meters, in AI data centers).",
      adv: "Could be retrofitted to existing AI chips and optimized for security.",
      dis: "Poses unsolved technical problems. Likely requires separate trusted clusters for analysis, and manufacturing & installing sensors.",
      reqSrc: "Table 2, row 3",
      req: [
        "Code & data checks: develop tests to detect code and data that are designed to spoof partial program re-execution with constraints (e.g. proof-of-learning).",
        "Workload modeling: given an AI workload and cluster specs, estimate the optimal utilization (MFU) and the associated physical signature, e.g., power.",
        "Analog sensors: design and manufacture appropriate analog sensors, or identify suitable existing tech.",
        "Tamper-proofing: design and manufacture appropriate tamper-proof server enclosures."
      ],
      reqNote: CROSS,
      note: "Note “verifying AI chips’ chain of custody“ and “tamper-proof, compliance-locked AI servers“ could just as well be swapped; the point is that they are two redundant off-chip mechanisms for addressing hidden AI compute clusters. We consider them “off-chip“ because they neither rely on features built into chips nor on leaks or disclosures from personnel. Additionally, tamper-proof enclosures and security cameras for chain-of-custody verification could be considered off-chip devices." },
    { row: "Layer 4", sub: "", name: "Whistleblower programs", section: "Section 4.3",
      cells: ["Whistleblower programs"],
      summary: "Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals.",
      adv: "Relatively simple, precedented, and implementation-ready.",
      dis: "Unclear effectiveness: depends on the number and loyalty of accomplices.",
      reqSrc: "Section 4.3.1",
      req: [
        "To enable whistleblowing: employees could be allowed to confidentially view some of their employer’s claims.",
        "Regular in-person contact with Verifiers, to counter whistleblower suppression, with measures to minimize inappropriate leaks.",
        "To encourage whistleblowing: anonymous reports, financial rewards, or pro-whistleblower norms."
      ],
      reqNote: NO_TABLE2,
      note: "Each of these layers simply consists of a single mechanism applied to all subgoals." },
    { row: "Layer 5", sub: "", name: "Interviews of personnel", section: "Section 4.3",
      cells: ["Interviews of personnel"],
      summary: "Interviews may reveal violations at any verification subgoal, e.g., via inconsistencies or perhaps improved lie detection tech, but such tech is abusable.",
      adv: "Relatively simple and precedented.",
      dis: "Unclear effectiveness: depends on accomplices’ ability to lie undetected.",
      reqSrc: "Section 4.3.1",
      req: [
        "Interviews limited to questions within a narrow, agreed-on scope, so that they do not reveal sensitive information.",
        "Interviewees who may collude to lie but struggle to do so convincingly: the mechanism rests on that difficulty.",
        "More reliable lie-detection technology would make interviews more robust, but the paper does not recommend developing it, due to its potential for abuse."
      ],
      reqNote: NO_TABLE2,
      note: "Each of these layers simply consists of a single mechanism applied to all subgoals." },
    { row: "Layer 6", sub: "", name: "National intelligence activities", section: "Section 4.3",
      cells: ["National intelligence activities"],
      summary: "Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.",
      adv: "Precedented and may be feasible unilaterally.",
      dis: "More adversarial, harder for third parties to verify, and unclear effectiveness.",
      reqSrc: "Section 4.3.1",
      req: [
        "Human, signals, and cyber intelligence disciplines directed at evidence of violations.",
        "No Prover cooperation needed, unlike the other personnel-based mechanisms.",
        "States with relatively weak intelligence capabilities would rely on stronger states’ intelligence-based verification."
      ],
      reqNote: NO_TABLE2,
      note: "Each of these layers simply consists of a single mechanism applied to all subgoals." }
  ];
  var state = { sel: null, seen: {}, off: {}, flipped: false };
  var completed = false;
  var els = {
    grid: document.getElementById("grid"),
    coverage: document.getElementById("coverage"),
    verdict: document.getElementById("verdict"),
    detail: document.getElementById("detail"),
    status: document.getElementById("status")
  };

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function seenCount() { var n = 0; for (var k in state.seen) if (state.seen.hasOwnProperty(k)) n++; return n; }
  function isOn(i) { return !state.off["l" + i]; }
  function activeLayers() { var a = []; LAYERS.forEach(function (L, i) { if (isOn(i)) a.push(i); }); return a; }
  function mech(i, ci) { return LAYERS[i].cells.length === 1 ? LAYERS[i].cells[0] : LAYERS[i].cells[ci]; }
  function famOf(i) { var f = ""; GROUPS.forEach(function (g) { if (g.layers.indexOf(i) >= 0) f = g.fam; }); return f; }
  function selType() { return state.sel ? state.sel.charAt(0) : null; }
  function selIndex() { return state.sel ? parseInt(state.sel.slice(1), 10) : -1; }

  function renderGrid() {
    els.grid.textContent = "";
    var t = selType(), idx = selIndex();
    if (t) els.grid.classList.add("has-focus"); else els.grid.classList.remove("has-focus");

    els.grid.appendChild(el("div", "corner"));
    SUBGOALS.forEach(function (s, i) {
      var b = el("button", "subgoal" + (t === "s" && idx === i ? " is-active" : ""));
      b.setAttribute("aria-pressed", t === "s" && idx === i ? "true" : "false");
      b.appendChild(el("span", "code", s.id));
      b.appendChild(el("span", "name", s.name));
      b.appendChild(el("span", "goal", s.goal));
      b.addEventListener("click", function () { select("s" + i); });
      els.grid.appendChild(b);
    });

    GROUPS.forEach(function (g) {
      var gl = el("div", "group", g.label);
      gl.style.gridRow = "span " + g.layers.length;
      els.grid.appendChild(gl);
      g.layers.forEach(function (li) {
        var L = LAYERS[li];
        var on = isOn(li);
        var wrap = el("div", "layer-cell" + (on ? "" : " row-off"));
        var b = el("button", "layer" + (t === "l" && idx === li ? " is-active" : "") + (state.seen["l" + li] ? " is-seen" : ""));
        b.setAttribute("aria-pressed", t === "l" && idx === li ? "true" : "false");
        b.appendChild(el("span", "lname", L.row));
        if (L.sub) b.appendChild(el("small", null, L.sub));
        b.addEventListener("click", function () { select("l" + li); });
        wrap.appendChild(b);
        var tg = el("button", "toggle" + (on ? "" : " is-off"));
        tg.appendChild(el("span", "dot"));
        tg.appendChild(el("span", null, on ? "On" : "Off"));
        tg.setAttribute("aria-pressed", on ? "true" : "false");
        tg.setAttribute("aria-label", (on ? "Switch off " : "Switch on ") + L.row + ", " + L.name);
        tg.title = (on ? "Switch off " : "Switch on ") + L.row;
        tg.addEventListener("click", function () { toggle(li); });
        wrap.appendChild(tg);
        els.grid.appendChild(wrap);
        if (L.cells.length === 1) {
          var lit = on && (t === "l" && idx === li || t === "s");
          els.grid.appendChild(el("div", "cell wide" + (lit ? " is-lit" : "") + (on ? "" : " is-off"), L.cells[0]));
        } else {
          L.cells.forEach(function (txt, ci) {
            var lit2 = on && ((t === "l" && idx === li) || (t === "s" && idx === ci));
            els.grid.appendChild(el("div", "cell" + (lit2 ? " is-lit" : "") + (on ? "" : " is-off"), txt));
          });
        }
      });
    });
  }

  function renderCoverage() {
    els.coverage.textContent = "";
    var act = activeLayers();
    var t = selType(), idx = selIndex();
    SUBGOALS.forEach(function (s, ci) {
      var b = el("button", "cov" + (act.length ? "" : " is-gone") + (t === "s" && idx === ci ? " is-active" : ""));
      b.setAttribute("aria-pressed", t === "s" && idx === ci ? "true" : "false");
      b.appendChild(el("span", "code", s.id));
      b.appendChild(el("span", "cname", s.name.replace(":", "")));
      var dots = el("div", "dots");
      LAYERS.forEach(function (L, li) {
        var d = el("span", isOn(li) ? "on" : null);
        d.title = L.row + (isOn(li) ? " on" : " off");
        dots.appendChild(d);
      });
      b.appendChild(dots);
      b.appendChild(el("span", "count", act.length ? act.length + (act.length === 1 ? " mechanism left" : " mechanisms left") : "no coverage left"));
      b.addEventListener("click", function () { select("s" + ci); });
      els.coverage.appendChild(b);
    });

    var n = act.length;
    els.verdict.textContent = "";
    els.verdict.className = "verdict" + (n ? "" : " is-gone");
    if (n === LAYERS.length) {
      els.verdict.appendChild(document.createTextNode("All six layers on. Every subgoal has six mechanisms, one per layer."));
    } else if (n === 0) {
      els.verdict.appendChild(document.createTextNode("No layers on. All four subgoals lose coverage: nothing is left to verify declared uses, their properties, compute accounting, or hidden clusters."));
    } else {
      els.verdict.appendChild(document.createTextNode(n + (n === 1 ? " layer on. All four subgoals are still covered, because a layer is defined as a set of mechanisms capable of end-to-end verification on its own." : " layers on. All four subgoals are still covered, because each layer carries one mechanism for every subgoal.")));
      var fams = {};
      act.forEach(function (i) { fams[famOf(i)] = true; });
      var list = [];
      GROUPS.forEach(function (g) { if (fams[g.fam]) list.push(g.fam); });
      var line = el("span", "fam", "Coverage now rests on the " + list.join(" and ") + " layer" + (act.length === 1 ? "" : "s") + ".");
      els.verdict.appendChild(line);
    }
  }

  function renderDetail() {
    els.detail.textContent = "";
    var t = selType(), idx = selIndex();
    if (t === "l" && LAYERS[idx]) {
      var L = LAYERS[idx];
      els.detail.appendChild(el("p", "eyebrow", L.row + (L.sub ? " " + L.sub : "") + ", " + L.section + (isOn(idx) ? "" : ", switched off")));
      els.detail.appendChild(el("h2", null, L.name));
      els.detail.appendChild(el("p", "k", "Summary of layer"));
      els.detail.appendChild(el("p", null, L.summary));
      els.detail.appendChild(el("p", "k", "Key advantages"));
      els.detail.appendChild(el("p", null, L.adv));
      els.detail.appendChild(el("p", "k", "Key disadvantages"));
      els.detail.appendChild(el("p", null, L.dis));
      els.detail.appendChild(el("p", "k", "What it requires (" + L.reqSrc + ")"));
      var ur = el("ul");
      L.req.forEach(function (r) { ur.appendChild(el("li", null, r)); });
      els.detail.appendChild(ur);
      if (L.reqNote) els.detail.appendChild(el("p", "note", L.reqNote));
      els.detail.appendChild(el("p", "k", "Mechanism per subgoal"));
      var ul = el("ul");
      if (L.cells.length === 1) {
        ul.appendChild(el("li", null, "All four subgoals: " + L.cells[0]));
      } else {
        L.cells.forEach(function (c, i) { ul.appendChild(el("li", null, SUBGOALS[i].id + " " + SUBGOALS[i].name + " " + c)); });
      }
      els.detail.appendChild(ul);
      if (L.note) els.detail.appendChild(el("p", "note", L.note));
    } else if (t === "s" && SUBGOALS[idx]) {
      var S = SUBGOALS[idx];
      els.detail.appendChild(el("p", "eyebrow", "Subgoal " + S.id + ", Section 3.2"));
      els.detail.appendChild(el("h2", null, S.name + " " + S.goal));
      els.detail.appendChild(el("p", null, S.def));
      els.detail.appendChild(el("p", "k", "Mechanism per layer"));
      var ul2 = el("ul");
      LAYERS.forEach(function (L2, li) {
        var on = isOn(li);
        ul2.appendChild(el("li", on ? null : "off", L2.row + (L2.sub ? " " + L2.sub : "") + ": " + mech(li, idx) + (on ? "" : " (switched off)")));
      });
      els.detail.appendChild(ul2);
      var left = activeLayers().length;
      els.detail.appendChild(el("p", "note", left ? left + (left === 1 ? " mechanism" : " mechanisms") + " left for this subgoal." : "No mechanism left for this subgoal."));
    }
    els.detail.hidden = !(t === "l" && LAYERS[idx]) && !(t === "s" && SUBGOALS[idx]);
  }

  function renderStatus() {
    els.status.textContent = "";
    var n = seenCount(), on = activeLayers().length;
    var hint = document.getElementById("sl-hint");
    if (hint) hint.hidden = (n >= LAYERS.length && state.flipped);
    els.status.appendChild(el("span", null, n + " of " + LAYERS.length + " layers opened, " + on + " of " + LAYERS.length + " switched on"));
    if (n >= LAYERS.length && state.flipped) els.status.appendChild(el("span", "done", "✓ All six layers opened and tested"));
    if (state.sel) {
      var clear = el("button", null, "Clear selection");
      clear.addEventListener("click", function () { state.sel = null; render(); save(); });
      els.status.appendChild(clear);
    }
    if (on < LAYERS.length) {
      var all = el("button", null, "Switch all layers on");
      all.addEventListener("click", function () { state.off = {}; render(); save(); });
      els.status.appendChild(all);
    }
  }

  function select(id) {
    state.sel = id;
    if (id.charAt(0) === "l") state.seen[id] = true;
    render();
    save();
  }
  function toggle(i) {
    if (state.off["l" + i]) delete state.off["l" + i];
    else { state.off["l" + i] = true; state.flipped = true; }
    render();
    save();
  }
  function render() { renderGrid(); renderCoverage(); renderDetail(); renderStatus(); }

  function summary() {
    var act = activeLayers();
    var offNames = [];
    LAYERS.forEach(function (L, i) { if (!isOn(i)) offNames.push(L.row + " (" + L.name + ")"); });
    var parts = ["Baker et al. six-layer grid (Figure 2). Learner has opened " + seenCount() + " of 6 layers and has " + act.length + " of 6 layers switched on."];
    if (offNames.length) parts.push("Switched off: " + offNames.join("; ") + ". Every subgoal still covered by " + act.length + " mechanism(s)" + (act.length ? "." : ", i.e. none: all four subgoals lose coverage."));
    else parts.push("No layer switched off yet.");
    var t = selType(), idx = selIndex();
    if (t === "l" && LAYERS[idx]) parts.push("Currently reading " + LAYERS[idx].row + ": " + LAYERS[idx].name + " (summary, key advantages, key disadvantages, what it requires, mechanism per subgoal).");
    else if (t === "s" && SUBGOALS[idx]) parts.push("Currently reading subgoal " + SUBGOALS[idx].id + " " + SUBGOALS[idx].name + " " + SUBGOALS[idx].goal + ", with the mechanism each layer offers for it.");
    else parts.push("Nothing selected.");
    var unseen = [];
    LAYERS.forEach(function (L, i) { if (!state.seen["l" + i]) unseen.push(L.row + " (" + L.name + ")"); });
    if (unseen.length) parts.push("Layers not yet opened: " + unseen.join("; ") + "."); else parts.push("All six layers opened.");
    return parts.join(" ");
  }

  var saveTimer = null;
  function doSave() {
    saveTimer = null;
    var done = seenCount() >= LAYERS.length && state.flipped;
    if (window.Lens) {
      Lens.saveState({ sel: state.sel, seen: state.seen, off: state.off, flipped: state.flipped }, summary());
      if (done && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("six-layers-grid", JSON.stringify(state)); } catch (e) {}
    }
  }
  function save() {
    if (saveTimer) clearTimeout(saveTimer);
    saveTimer = setTimeout(doSave, 200);
  }
  document.addEventListener("visibilitychange", function () { if (document.visibilityState === "hidden" && saveTimer) { clearTimeout(saveTimer); doSave(); } });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      state.sel = (typeof saved.sel === "string") ? saved.sel : null;
      state.seen = (saved.seen && typeof saved.seen === "object") ? saved.seen : {};
      state.off = (saved.off && typeof saved.off === "object") ? saved.off : {};
      state.flipped = saved.flipped === true;
    }
    if (meta && meta.completed) completed = true;
    render();
  }

  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var restored = null;
    try { restored = JSON.parse(localStorage.getItem("six-layers-grid") || "null"); } catch (e) {}
    hydrate(restored, null);
  }
})();
</script>
</body>
</html>


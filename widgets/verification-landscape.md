---
title: The verification landscape
summary_for_tutor: A heat-map of where AI verification work is happening. Rows are kinds of verification (hardware mechanisms, cryptographic methods, compute and supply chain, monitoring and intelligence, institutions and agreements, evaluations and standards); columns are who does the work (academia, think tanks and nonprofits, industry, government and international). Darker squares mean more activity. The learner taps a square to read who works there and how it connects, or a row or column label to read what it means. Patterns worth drawing out are that the think-tank column is the field's centre of gravity, export control is the one muscular government square, and cryptographic methods have no government home at all. Content ported from XLab's Verification track (snapshot, early 2026).
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The verification landscape</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "verification-landscape". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff;
    --text: #1a1a1a;
    --muted: #5a5a5a;
    --border: #e8e5df;
    --accent: #b87018;
    --accent-ink: #7a4a0d;
    --defect: #b91c1c;
    --heat0: #f3f1ec;
    --heat1: #f0dcc0;
    --heat2: #d9a262;
    --heat3: #b87018;
    --font-ui: "DM Sans", Arial, sans-serif;
    --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    padding: 16px;
    font-family: var(--font-ui);
    font-size: 14px;
    line-height: 1.5;
    color: var(--text);
    background: var(--bg);
  }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); }
  .legend { display: flex; flex-wrap: wrap; align-items: center; gap: 10px; margin-bottom: 12px; }
  .swatches { display: flex; gap: 3px; }
  .swatch { width: 28px; height: 16px; border-radius: 2px; }
  .hatch {
    background-color: var(--heat0);
    background-image: repeating-linear-gradient(45deg, transparent, transparent 5px, rgba(90,90,90,0.2) 5px, rgba(90,90,90,0.2) 6px);
  }
  .scroll { overflow-x: auto; margin: 0 -4px; padding: 4px; }
  .grid { display: grid; gap: 5px; min-width: 460px; }
  .axis {
    font: inherit; color: inherit; background: none; border: 0; cursor: pointer;
    padding: 4px; border-radius: 4px; text-align: left;
  }
  .axis:hover { text-decoration: underline; }
  .axis.col { text-align: center; font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; font-weight: 600; color: var(--accent-ink); line-height: 1.2; }
  .axis.row { font-size: 12px; font-weight: 600; align-self: center; padding-right: 8px; }
  .cell {
    position: relative; aspect-ratio: 1 / 1; display: flex; flex-direction: column; align-items: flex-start; gap: 2px;
    padding: 6px; border: 0; border-radius: 3px; cursor: pointer; text-align: left; overflow: hidden;
    font: inherit; transition: transform 120ms;
  }
  .cell:hover, .cell:focus-visible { transform: scale(1.03); z-index: 2; outline: none; }
  .cell.is-active { box-shadow: inset 0 0 0 3px var(--text); }
  .cell .org { font-size: 9px; line-height: 1.15; font-weight: 500; }
  .cell .n { position: absolute; right: 6px; bottom: 4px; font-size: 9px; line-height: 1; opacity: 0.7; }
  .cell.h0 { background-color: var(--heat0); color: var(--text); }
  .cell.h1 { background: var(--heat1); color: var(--text); }
  .cell.h2 { background: var(--heat2); color: #fff; }
  .cell.h3 { background: var(--heat3); color: #fff; }
  .detail { margin-top: 20px; min-height: 96px; border: 1px solid var(--accent); padding: 16px; background: #fdfcfa; position: relative; }
  .detail .hint { color: var(--muted); font-style: italic; margin: 0; }
  .detail h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 4px 0 0; }
  .detail .sub { color: var(--muted); font-size: 12px; margin: 2px 0 0; }
  .detail p { margin: 8px 0 0; }
  .detail ul { margin: 8px 0 0; padding-left: 18px; }
  .detail li { margin: 4px 0; }
  .detail .connect { border-top: 1px solid var(--border); margin-top: 12px; padding-top: 8px; }
  .gap { color: var(--defect); }
  .close {
    position: absolute; top: 8px; right: 8px; font: inherit; border: 0; background: none; color: var(--muted);
    width: 28px; height: 28px; border-radius: 6px; cursor: pointer; font-size: 18px; line-height: 1;
  }
  .close:hover { color: var(--text); background: var(--border); }
</style>
</head>
<body>
<div class="legend eyebrow">
  <span>Less activity</span>
  <span class="swatches">
    <span class="swatch hatch"></span>
    <span class="swatch" style="background: var(--heat1)"></span>
    <span class="swatch" style="background: var(--heat2)"></span>
    <span class="swatch" style="background: var(--heat3)"></span>
  </span>
  <span>More activity</span>
</div>

<div class="scroll">
  <div class="grid" id="grid" role="grid" aria-label="Verification activity by kind of work and actor"></div>
</div>

<div class="detail" id="detail" aria-live="polite">
  <p class="hint">Select any square, row, or column to read about it.</p>
</div>

<script>
  var HEATWORD = ["No activity yet", "Emerging", "Active", "Concentrated"];
  var ROWS = [
    { key: "hw", name: "Hardware mechanisms", desc: "Verification built into the chip itself: unique identity, remote attestation, compute metering, and tamper-resistant on-chip processors that can prove what a device did or refused to do." },
    { key: "crypto", name: "Cryptographic methods", desc: "Proving a property of a computation without revealing the underlying model, data, or code. The math behind checking compliance without surrendering secrets." },
    { key: "compute", name: "Compute & supply chain", desc: "Using the concentrated, physical compute supply chain, from lithography to chips to data centers, as the place where rules can be attached and checked." },
    { key: "monitor", name: "Monitoring & intelligence", desc: "Inferring what is happening from outside signatures: energy draw, cooling, chip procurement, satellite imagery, financial activity, and cluster telemetry." },
    { key: "inst", name: "Institutions & agreements", desc: "The bodies, treaties, and voluntary frameworks that would house commitments and, in principle, enforce them." },
    { key: "evals", name: "Evaluations & standards", desc: "Measuring what a model can actually do. Any capability-based rule depends on evaluations that are trustworthy and hard to game." }
  ];
  var COLS = [
    { key: "acad", name: "Academia", desc: "University labs and published research." },
    { key: "think", name: "Think tanks & nonprofits", desc: "Policy institutes and independent research organizations. The field's current center of gravity." },
    { key: "industry", name: "Industry", desc: "Frontier labs, chipmakers, and cloud providers, who hold the hardware and the data." },
    { key: "gov", name: "Gov & int'l", desc: "States, agencies, and multinational bodies with the authority to mandate and enforce." }
  ];
  var CELLS = {
    hw: {
      acad: { i: 1, state: "A thin but real academic base in hardware security that governance proposals borrow from, though little of it targets AI verification directly.", eff: [["Hardware-security research", "Physically unclonable functions, trusted execution environments, secure boot: the primitives, developed for general computer security."]], connect: "Supplies the building blocks that think-tank proposals like FlexHEG and RAND's work assemble into governance mechanisms." },
      think: { i: 3, state: "The intellectual center of gravity for hardware verification. Most of the concrete proposals live here.", eff: [["RAND, Hardware-Enabled Governance Mechanisms (2024)", "Frames how on-chip features could enforce and verify compute rules."], ["CNAS, Secure, Governable Chips (2024)", "Argues for governance features designed into AI chips."], ["FlexHEG report series (2025)", "Commissioned by the UK's ARIA. Proposes an on-chip “guarantee processor” for privacy-preserving compliance checks, updateable and open-source."]], connect: "Draws primitives from academia and aims its output at export-control and treaty policy on the government side." },
      industry: { i: 2, state: "Industry holds the substrate but is not building governance features. The secure hardware that exists was made to protect the owner, not to check on them.", eff: [["Confidential computing (e.g. NVIDIA)", "Secure enclaves and attestation on data-center GPUs, built for customer security."], ["Secure boot & attestation", "Standard commercial features that governance proposals hope to repurpose."]], connect: "Note the threat-model inversion: these tools protect the chip's owner, while verification tries to check on the owner. Same silicon, opposite goal." },
      gov: { i: 1, state: "Nascent. Government involvement is mostly commissioning and early signaling rather than building.", eff: [["ARIA (UK)", "Commissioned the FlexHEG research series through its Safeguarded AI programme."], ["US export-control discussion", "Interest in on-chip location verification for advanced AI chips has surfaced in policy debate."]], connect: "If any hardware mechanism matures, government is the actor that would mandate it. For now it mostly funds and watches." }
    },
    crypto: {
      acad: { i: 3, state: "A dense, fast-moving academic literature. This is where prove-without-revealing methods actually get built and benchmarked.", eff: [["Zero-knowledge ML (zkML)", "Proofs that a model produced a given output, or scored a given result on an evaluation, without revealing its weights."], ["Proof-of-learning", "Attempts to prove a model was trained as claimed. Notably fragile so far; researchers have shown it is “more broken than you think.”"], ["Secure multiparty computation", "Two parties jointly compute a verification result over inputs neither reveals."]], connect: "The engine room for the confidentiality-versus-verifiability problem, and so far largely disconnected from the governance actors who need it.", orgs: ["COSIC", "Waterloo CACR"] },
      think: { i: 1, state: "A small translation layer connecting cryptographic results to governance use-cases.", eff: [["Occasional bridging work", "A handful of policy analyses on how ZKPs and secure computation could support AI treaties."]], connect: "A thin bridge between academic cryptography and treaty design, and a clear candidate for growth." },
      industry: { i: 1, state: "Emerging, and mostly outside the frontier labs.", eff: [["zkML tooling & startups", "Proof systems for model inference, largely from the cryptography and blockchain world rather than AI developers."]], connect: "Could productize the academic methods, but is not yet aimed at treaty-grade verification between states.", orgs: ["EZKL", "Modulus Labs", "Giza"] },
      gov: { i: 0, gap: true, state: "Essentially empty. No public government program applies these methods to AI verification today.", eff: [], connect: "A visible gap. The mechanisms that could let one state verify another without seeing its secrets exist mainly as papers, with no home in government." }
    },
    compute: {
      acad: { i: 1, state: "Modest. Some academic economics and computer science on compute trends and semiconductor supply chains.", eff: [["Supply-chain & scaling research", "University work on chip production and the economics of compute."]], connect: "Feeds data into the think-tank analyses that dominate this row." },
      think: { i: 3, state: "One of the hottest squares in the field. Compute is the favored lever because it is detectable, excludable, and concentrated.", eff: [["CSET, Georgetown", "Supply-chain analysis and the influential “AI Triad” framing of data, compute, and algorithms."], ["GovAI, Computing Power and the Governance of AI (2024)", "A foundational map of compute as a governance target."], ["RAND, Securing AI Model Weights (2024)", "On protecting the trained artifact itself."], ["Epoch AI", "Independent data on compute and scaling trends the whole field cites."]], connect: "Turns raw supply-chain facts into the policy vocabulary that the government's export-control machinery runs on." },
      industry: { i: 2, state: "Real activity, driven by compliance rather than governance ideals.", eff: [["Cloud know-your-customer", "Emerging practices to identify who is renting large amounts of compute."], ["Export-control compliance", "Chipmakers and cloud providers implementing licensing and end-use checks."]], connect: "Industry sits on the chokepoints the supply-chain map identifies. Its cooperation is what makes verification there feasible at all." },
      gov: { i: 3, state: "The one place where government verification is genuinely muscular today: export control.", eff: [["US Bureau of Industry and Security", "Export controls and licensing on advanced chips and chipmaking equipment."], ["Allied coordination", "Alignment with the Netherlands and Japan over lithography and tooling."]], connect: "The most consequential live mechanism on the whole map, and the closest working analog to arms-control chokepoint monitoring." }
    },
    monitor: {
      acad: { i: 1, state: "Small but growing academic interest in detecting compute from the outside.", eff: [["Remote sensing of compute", "Satellite analysis of data-center construction and research on energy signatures."]], connect: "Supplies techniques the intelligence and think-tank actors can operationalize." },
      think: { i: 2, state: "A developing analytic literature on the external signatures of large compute.", eff: [["Data-center & energy tracking", "Think-tank work treating power draw, cooling, and chip procurement as compliance signals."]], connect: "The open-source cousin of national technical means, leaning on Epoch-style compute data.", orgs: ["FAS", "Epoch AI"] },
      industry: { i: 1, state: "Industry holds the richest telemetry of all, and does not share it.", eff: [["Cloud utilization data", "Cluster logs and usage monitoring, plus suspicious-use detection tied to customer checks."]], connect: "The data that would make outside monitoring powerful sits behind commercial walls." },
      gov: { i: 2, state: "Real but classified. This is national technical means, pointed at compute.", eff: [["Intelligence-community monitoring", "Tracking of chip procurement, data-center expansion, energy use, and financial flows; anomaly detection."]], connect: "The modern equivalent of the test-ban sensor network, aimed at compute rather than seismic waves.", orgs: ["IEA"] }
    },
    inst: {
      acad: { i: 1, state: "Some international-relations scholarship on AI treaty design and arms-control analogies.", eff: [["Arms-control history & IR", "Academic work drawing verification lessons from nuclear, chemical, and biological regimes."]], connect: "Provides the historical grounding under the think-tank proposals.", orgs: ["CSER"] },
      think: { i: 2, state: "A busy proposal space, long on designs and short on adoption.", eff: [["Institutional proposals", "Blueprints for a “CERN for AI” or an “IAEA for AI,” plus detailed treaty and verification-regime design."]], connect: "Supplies the blueprints that the government and international actors would have to actually build and staff.", orgs: ["FLI", "Chatham House", "Simon Inst."] },
      industry: { i: 2, state: "Voluntary self-governance is real and operating, and it is unverified by design.", eff: [["Anthropic Responsible Scaling Policy", "Capability tiers (ASL levels) with pre-committed safeguards."], ["OpenAI Preparedness Framework", "Internal thresholds and responses for dangerous capabilities."], ["Google DeepMind Frontier Safety Framework", "A comparable set of self-imposed commitments."]], connect: "These are the “self-governance” end of the policy spectrum: commitments demonstrated without external verification, which is exactly the gap this course targets." },
      gov: { i: 2, state: "The institutional scaffolding that exists today is mostly evaluative and voluntary, not binding.", eff: [["International Network of AI Safety Institutes (2024)", "Eleven nations coordinating on evaluation and risk."], ["US CAISI", "The former AI Safety Institute, renamed the Center for AI Standards and Innovation in 2025, housed in NIST."], ["UK AI Security Institute", "The former UK AI Safety Institute, renamed in 2025."], ["IAEA & OPCW", "Existing arms-control bodies that serve as living templates for what an AI equivalent might look like."]], connect: "The closest thing to an international verification body, but without inspection powers over AI. The distance between this and the IAEA is the course's motivating gap." }
    },
    evals: {
      acad: { i: 2, state: "A substantial academic benchmark and evaluation-science base.", eff: [["Benchmarks & measurement science", "University work on capability benchmarks, red-teaming methods, and how to measure model abilities reliably."]], connect: "Underpins the capability-threshold question that compute thresholds currently sidestep.", orgs: ["Stanford CRFM", "MLCommons"] },
      think: { i: 3, state: "Dense and influential. The leading independent evaluators are nonprofits.", eff: [["METR", "Model Evaluation and Threat Research, known for dangerous-capability and autonomy evaluations run with labs and governments."], ["Apollo Research", "Focused on detecting deception and scheming in advanced models."]], connect: "Provides the capability measurements any capability-based treaty threshold would depend on. Ties directly into the Evals module later in the course." },
      industry: { i: 2, state: "Labs run extensive internal evaluations and publish frameworks, though self-evaluation has obvious limits.", eff: [["In-house dangerous-capability evals", "Frontier labs testing their own models and disclosing safety frameworks."], ["Third-party pre-deployment testing", "Agreements giving outside evaluators limited early access."]], connect: "The evaluated party is often also the evaluator, which is the verification problem in miniature." },
      gov: { i: 2, state: "Government evaluation and standards capacity, recently reoriented toward innovation and security.", eff: [["CAISI & UK AI Security Institute", "Public-sector model evaluations and testing."], ["NIST standards & “Inspect”", "Standards work, plus the UK's open-source evaluation tool."]], connect: "The public-sector check on capability claims. Its independence and authority are still being defined." }
    }
  };
  // Organisation names shown inside a square: matched in the effort titles, plus per-cell extras.
  var ORG_TOKENS = [
    ["OpenAI", "OpenAI"], ["Anthropic", "Anthropic"], ["DeepMind", "DeepMind"], ["NVIDIA", "NVIDIA"], ["RAND", "RAND"],
    ["NIST", "NIST"], ["CNAS", "CNAS"], ["CSET", "CSET"], ["GovAI", "GovAI"], ["Epoch AI", "Epoch AI"], ["METR", "METR"],
    ["Apollo Research", "Apollo"], ["FlexHEG", "FlexHEG"], ["ARIA", "ARIA"], ["Bureau of Industry and Security", "US BIS"],
    ["IAEA", "IAEA"], ["OPCW", "OPCW"], ["CAISI", "CAISI"], ["UK AI Security Institute", "UK AISI"],
    ["International Network of AI Safety", "Int’l Network"]
  ];
  function orgsFor(cell) {
    var out = [], seen = {};
    cell.eff.forEach(function (e) {
      var title = e[0].toLowerCase();
      ORG_TOKENS.forEach(function (t) {
        if (title.indexOf(t[0].toLowerCase()) !== -1 && !seen[t[1]]) { seen[t[1]] = true; out.push(t[1]); }
      });
    });
    (cell.orgs || []).forEach(function (o) { if (!seen[o]) { seen[o] = true; out.push(o); } });
    return out;
  }

  var grid = document.getElementById("grid");
  var detail = document.getElementById("detail");
  var sel = null;
  grid.style.gridTemplateColumns = "minmax(96px, 1.15fr) repeat(" + COLS.length + ", minmax(64px, 1fr))";

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }

  grid.appendChild(el("div"));
  COLS.forEach(function (c, ci) {
    var b = el("button", "axis col", c.name); b.type = "button";
    b.addEventListener("click", function () { setSel({ kind: "axis", axis: "col", i: ci }); });
    grid.appendChild(b);
  });
  ROWS.forEach(function (r, ri) {
    var rb = el("button", "axis row", r.name); rb.type = "button";
    rb.addEventListener("click", function () { setSel({ kind: "axis", axis: "row", i: ri }); });
    grid.appendChild(rb);
    COLS.forEach(function (c, ci) {
      var d = CELLS[r.key][c.key];
      var orgs = orgsFor(d);
      var b = el("button", "cell h" + d.i + (d.i === 0 ? " hatch" : "")); b.type = "button";
      b.dataset.cell = ri + "-" + ci;
      b.setAttribute("aria-label", r.name + ", " + c.name + ", activity " + d.i + " of 3" + (orgs.length ? ", " + orgs.join(", ") : ""));
      orgs.forEach(function (o) { b.appendChild(el("span", "org", o)); });
      b.appendChild(el("span", "n", String(d.i)));
      b.addEventListener("click", function () { setSel({ kind: "cell", ri: ri, ci: ci }); });
      grid.appendChild(b);
    });
  });

  function closeBtn() {
    var b = el("button", "close", "×"); b.type = "button"; b.id = "close";
    b.setAttribute("aria-label", "Close detail");
    b.addEventListener("click", function () { setSel(null); });
    return b;
  }

  function render() {
    var cells = grid.querySelectorAll(".cell");
    for (var k = 0; k < cells.length; k++) {
      var on = sel && sel.kind === "cell" && cells[k].dataset.cell === sel.ri + "-" + sel.ci;
      cells[k].classList.toggle("is-active", !!on);
      cells[k].setAttribute("aria-pressed", on ? "true" : "false");
    }
    detail.textContent = "";
    if (!sel) { detail.appendChild(el("p", "hint", "Select any square, row, or column to read about it.")); return; }
    detail.appendChild(closeBtn());
    if (sel.kind === "axis") {
      var o = sel.axis === "row" ? ROWS[sel.i] : COLS[sel.i];
      detail.appendChild(el("p", "eyebrow", sel.axis === "row" ? "Kind of verification" : "Who does the work"));
      detail.appendChild(el("h2", null, o.name));
      detail.appendChild(el("p", null, o.desc));
      detail.appendChild(el("p", "sub", "Tap a square in this " + sel.axis + " to see who is working there."));
      return;
    }
    var r = ROWS[sel.ri], c = COLS[sel.ci], d = CELLS[r.key][c.key];
    detail.appendChild(el("p", "eyebrow", r.name + " × " + c.name));
    var h = el("h2");
    if (d.gap) h.appendChild(el("span", "gap", "Open gap. "));
    h.appendChild(document.createTextNode(r.name + " here is " + HEATWORD[d.i].toLowerCase() + "."));
    detail.appendChild(h);
    detail.appendChild(el("p", "sub", "Activity " + d.i + " / 3 · " + HEATWORD[d.i]));
    detail.appendChild(el("p", null, d.state));
    if (d.eff.length) {
      var ul = el("ul");
      d.eff.forEach(function (e) {
        var li = el("li");
        var strong = el("strong", null, e[0]);
        li.appendChild(strong); li.appendChild(document.createTextNode(". " + e[1]));
        ul.appendChild(li);
      });
      detail.appendChild(ul);
    }
    var p = el("p", "connect");
    p.appendChild(el("span", "eyebrow", "How it connects "));
    p.appendChild(document.createTextNode(d.connect));
    detail.appendChild(p);
  }

  function setSel(next) { sel = next; render(); }
  render();
</script>
</body>
</html>

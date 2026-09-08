---
id: '08c51eef-41bb-490e-bfa7-f7f1addf2c80'
title: Six verification layers by subgoal
summary_for_tutor: "An interactive version of Figure 2 (and its per-section slices, Figures 5 to 7) of Baker et al. (2025), 'Verifying International Agreements on AI': a grid of six verification layers (on-chip security features; off-chip network taps; off-chip analog sensors; whistleblower programs; interviews of personnel; national intelligence activities) against the four verification subgoals (1A model and output histories, 1B evaluations, 2A compute accounting, 2B data center detection), each cell naming the mechanism that layer uses for that subgoal. The learner clicks a layer to read the paper's summary of the layer, its key advantages and key disadvantages (Tables 5, 7 and 8) alongside its mechanisms, or clicks a subgoal to read the paper's definition of that subgoal (Section 3.2) alongside the mechanisms that address it across layers. Done means the learner has opened all six layers."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Six verification layers by subgoal</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track reading "Verifying International Agreements on AI: Six Layers of Verification" (Baker et al. 2025), Figure 2 and Tables 1, 5, 7, 8. Not an XLab widget: an interactive rendering of the article's own figure and tables. -->
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
  .lede { color: var(--muted); margin: 8px 0 12px; max-width: 46rem; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--page); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .grid-wrap { overflow-x: auto; border: 1px solid var(--border); border-radius: 8px; background: var(--page); padding: 12px; }
  .grid { display: grid; grid-template-columns: 7.5rem 6.5rem repeat(4, minmax(8.5rem, 1fr)); gap: 6px; min-width: 720px; align-items: stretch; }
  .corner { grid-column: 1 / span 2; }
  .subgoal { display: flex; flex-direction: column; gap: 4px; padding: 8px 10px; }
  .subgoal .code { display: inline-block; width: 26px; height: 26px; border-radius: 50%; background: var(--muted); color: #fff; font-size: 11px; font-weight: 600; text-align: center; line-height: 26px; }
  .subgoal .name { font-style: italic; font-size: 12px; }
  .subgoal .goal { font-size: 12px; color: var(--muted); }
  .subgoal.is-active .code { background: var(--accent); }
  .group { display: flex; align-items: center; justify-content: center; text-align: center; font-weight: 600; font-size: 12px; padding: 6px; border-right: 1px solid var(--border); color: var(--muted); }
  .layer { display: flex; flex-direction: column; justify-content: center; font-weight: 600; font-size: 13px; padding: 8px 10px; }
  .layer small { font-weight: 400; color: var(--muted); font-size: 11px; }
  .layer.is-seen::after { content: "\2713 opened"; font-weight: 400; font-size: 10px; color: var(--accent); letter-spacing: 0.06em; text-transform: uppercase; margin-top: 2px; }
  .cell { border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 10px; font-size: 12px; display: flex; align-items: center; justify-content: center; text-align: center; min-height: 3.2rem; }
  .cell.wide { grid-column: 3 / span 4; }
  .cell.is-lit { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: var(--accent-tint); }
  .grid.has-focus .cell:not(.is-lit) { opacity: 0.45; }
  .detail { margin-top: 16px; min-height: 8rem; }
  .detail p { margin: 0 0 8px; }
  .detail .k { font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--muted); margin: 12px 0 2px; }
  .detail ul { margin: 4px 0 8px; padding-left: 20px; }
  .detail li { margin-bottom: 4px; }
  .detail .note { font-size: 12px; color: var(--muted); }
  .status { margin-top: 12px; font-size: 12px; color: var(--muted); display: flex; gap: 12px; align-items: center; flex-wrap: wrap; }
  .status .done { color: var(--accent); font-weight: 600; }
</style>
</head>
<body>
<section aria-labelledby="sl-title">
  <p class="eyebrow">Baker et al. (2025), Figure 2</p>
  <h1 id="sl-title">Verification layers consist of distinct mechanisms for each verification subgoal.</h1>
  <p class="lede">Click a layer to read how the paper summarises it and what it trades off; click a subgoal to read what has to be verified and which mechanism each layer offers for it.</p>

  <div class="grid-wrap"><div class="grid" id="grid" role="table"></div></div>

  <div class="card detail" id="detail" aria-live="polite"></div>

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
  var SUBGOAL_INTRO = "The framework decomposes this goal into two subgoals: (1) verify that declared uses of large-scale AI compute are compliant, and (2) verify that there are no undeclared uses of large-scale AI compute (i.e., declarations are complete).";

  // Layer rows: cells from Figure 2; name, summary, advantages, disadvantages from Tables 5, 7 and 8; notes from the captions of Figures 6 and 7.
  var GROUPS = [
    { label: "“On-chip” verification layer", layers: [0] },
    { label: "“Off-chip” verification layers", layers: [1, 2] },
    { label: "Personnel-based verification layers", layers: [3, 4, 5] }
  ];
  var LAYERS = [
    { row: "Layer 1", sub: "", name: "On-chip security features (i.e., secure boot, Confidential Computing)", section: "Section 4.1",
      cells: ["Hardware-backed workload certificates", "Hardware-backed evals", "Hardware-backed workload certificates", "Tamper-proof, compliance-locked AI chips"],
      summary: "Security features built into AI chips may enable verification, such as by ensuring that AI chips log traces of their activities for confidential analysis.",
      adv: "Offers maximum transparency into AI chips’ uses.",
      dis: "Poses unsolved technical problems and severe security challenges (e.g., untrusted suppliers). Insecure AI chips may need to be replaced.",
      note: "" },
    { row: "Layer 2", sub: "(network taps)", name: "Off-chip network tap (and analysis) (e.g. “FlexHEGs”)", section: "Section 4.2",
      cells: ["Network taps & analysis", "Backup evals on separate chips", "Network taps & analysis", "Verifying AI chips' chain of custody"],
      summary: "Mutually vetted devices could intercept data exchanged between chips, then check for discrepancies with declared uses.",
      adv: "Could be retrofitted to existing AI chips and optimized for security.",
      dis: "Poses technical, logistical, and security challenges. Strongest versions need redesigned chip-adjacent hardware.",
      note: "Note “verifying AI chips’ chain of custody“ and “tamper-proof, compliance-locked AI servers“ could just as well be swapped; the point is that they are two redundant off-chip mechanisms for addressing hidden AI compute clusters. We consider them “off-chip“ because they neither rely on features built into chips nor on leaks or disclosures from personnel. Additionally, tamper-proof enclosures and security cameras for chain-of-custody verification could be considered off-chip devices." },
    { row: "Layer 3", sub: "(analog sensors)", name: "Off-chip analog sensors (and analysis, e.g., proof-of-learning)", section: "Section 4.2",
      cells: ["Partial workload re-execution with constraints", "More backup evals on separate chips", "Analog sensors & analysis", "Tamper-proof, compliance-locked AI servers"],
      summary: "Physically secured chips could check that (i) declared AI compute uses are accurate (e.g., reproducible) and (ii) their compute use adds up to the expected total (estimated with analog sensors, e.g., power meters, in AI data centers).",
      adv: "Could be retrofitted to existing AI chips and optimized for security.",
      dis: "Poses unsolved technical problems. Likely requires separate trusted clusters for analysis, and manufacturing & installing sensors.",
      note: "Note “verifying AI chips’ chain of custody“ and “tamper-proof, compliance-locked AI servers“ could just as well be swapped; the point is that they are two redundant off-chip mechanisms for addressing hidden AI compute clusters. We consider them “off-chip“ because they neither rely on features built into chips nor on leaks or disclosures from personnel. Additionally, tamper-proof enclosures and security cameras for chain-of-custody verification could be considered off-chip devices." },
    { row: "Layer 4", sub: "", name: "Whistleblower programs", section: "Section 4.3",
      cells: ["Whistleblower programs"],
      summary: "Programs may enable and incentivize (narrowly scoped, non-public) staff whistleblowing, for all verification subgoals.",
      adv: "Relatively simple, precedented, and implementation- ready.",
      dis: "Unclear effectiveness: depends on the number and loyalty of accomplices.",
      note: "Each of these layers simply consists of a single mechanism applied to all subgoals." },
    { row: "Layer 5", sub: "", name: "Interviews of personnel", section: "Section 4.3",
      cells: ["Interviews of personnel"],
      summary: "Interviews may reveal violations at any verification subgoal, e.g., via inconsistencies or perhaps improved lie detection tech, but such tech is abusable.",
      adv: "Relatively simple and precedented.",
      dis: "Unclear effectiveness: depends on accomplices’ ability to lie undetected.",
      note: "Each of these layers simply consists of a single mechanism applied to all subgoals." },
    { row: "Layer 6", sub: "", name: "National intelligence activities", section: "Section 4.3",
      cells: ["National intelligence activities"],
      summary: "Intelligence agencies could collect and analyze intelligence for all verification subgoals, including via human, cyber, and signals intelligence.",
      adv: "Precedented and may be feasible unilaterally.",
      dis: "More adversarial, harder for third parties to verify, and unclear effectiveness.",
      note: "Each of these layers simply consists of a single mechanism applied to all subgoals." }
  ];
  var LAYERS_INTRO = "To complete these subgoals, states could create six layers of verification: six largely independent assurances of compliance. Like “layers of defense,” a full implementation of each layer could verify compliance on its own, and multiple layers would reinforce each other. Thus, a stack of layers is an effective combination of verification mechanisms; it completes each subgoal with redundancy.";

  var state = { sel: null, seen: {} };
  var completed = false;
  var els = { grid: document.getElementById("grid"), detail: document.getElementById("detail"), status: document.getElementById("status") };

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function seenCount() { var n = 0; for (var k in state.seen) if (state.seen.hasOwnProperty(k)) n++; return n; }
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
        var b = el("button", "layer" + (t === "l" && idx === li ? " is-active" : "") + (state.seen["l" + li] ? " is-seen" : ""));
        b.setAttribute("aria-pressed", t === "l" && idx === li ? "true" : "false");
        b.appendChild(document.createTextNode(L.row));
        if (L.sub) b.appendChild(el("small", null, L.sub));
        b.addEventListener("click", function () { select("l" + li); });
        els.grid.appendChild(b);
        if (L.cells.length === 1) {
          var c = el("div", "cell wide" + (t === "l" && idx === li ? " is-lit" : "") + (t === "s" ? " is-lit" : ""), L.cells[0]);
          els.grid.appendChild(c);
        } else {
          L.cells.forEach(function (txt, ci) {
            var lit = (t === "l" && idx === li) || (t === "s" && idx === ci);
            els.grid.appendChild(el("div", "cell" + (lit ? " is-lit" : ""), txt));
          });
        }
      });
    });
  }

  function renderDetail() {
    els.detail.textContent = "";
    var t = selType(), idx = selIndex();
    if (t === "l" && LAYERS[idx]) {
      var L = LAYERS[idx];
      els.detail.appendChild(el("p", "eyebrow", L.row + (L.sub ? " " + L.sub : "") + ", " + L.section));
      els.detail.appendChild(el("h2", null, L.name));
      els.detail.appendChild(el("p", "k", "Summary of layer"));
      els.detail.appendChild(el("p", null, L.summary));
      els.detail.appendChild(el("p", "k", "Key advantages"));
      els.detail.appendChild(el("p", null, L.adv));
      els.detail.appendChild(el("p", "k", "Key disadvantages"));
      els.detail.appendChild(el("p", null, L.dis));
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
      LAYERS.forEach(function (L) { ul2.appendChild(el("li", null, L.row + (L.sub ? " " + L.sub : "") + ": " + (L.cells.length === 1 ? L.cells[0] : L.cells[idx]))); });
      els.detail.appendChild(ul2);
    } else {
      els.detail.appendChild(el("p", "eyebrow", "Six layers, four subgoals"));
      els.detail.appendChild(el("p", null, SUBGOAL_INTRO));
      els.detail.appendChild(el("p", null, LAYERS_INTRO));
      els.detail.appendChild(el("p", "note", "Nothing selected yet. Click a layer on the left or a subgoal along the top."));
    }
  }

  function renderStatus() {
    els.status.textContent = "";
    var n = seenCount();
    els.status.appendChild(el("span", null, n + " of " + LAYERS.length + " layers opened"));
    if (n >= LAYERS.length) els.status.appendChild(el("span", "done", "✓ All six layers opened"));
    var clear = el("button", null, "Clear selection");
    clear.addEventListener("click", function () { state.sel = null; render(); save(); });
    els.status.appendChild(clear);
  }

  function select(id) {
    state.sel = id;
    if (id.charAt(0) === "l") state.seen[id] = true;
    render();
    save();
  }
  function render() { renderGrid(); renderDetail(); renderStatus(); }

  function summary() {
    var parts = ["Baker et al. six-layer grid (Figure 2). Learner has opened " + seenCount() + " of 6 layers."];
    var t = selType(), idx = selIndex();
    if (t === "l" && LAYERS[idx]) parts.push("Currently reading " + LAYERS[idx].row + ": " + LAYERS[idx].name + " (summary, key advantages, key disadvantages, mechanism per subgoal).");
    else if (t === "s" && SUBGOALS[idx]) parts.push("Currently reading subgoal " + SUBGOALS[idx].id + " " + SUBGOALS[idx].name + " " + SUBGOALS[idx].goal + ", with the mechanism each layer offers for it.");
    else parts.push("Nothing selected.");
    var unseen = [];
    LAYERS.forEach(function (L, i) { if (!state.seen["l" + i]) unseen.push(L.row + " (" + L.name + ")"); });
    if (unseen.length) parts.push("Layers not yet opened: " + unseen.join("; ") + "."); else parts.push("All six layers opened.");
    return parts.join(" ");
  }

  function save() {
    var done = seenCount() >= LAYERS.length;
    if (window.Lens) {
      Lens.saveState({ sel: state.sel, seen: state.seen }, summary());
      if (done && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem("six-layers-grid", JSON.stringify(state)); } catch (e) {}
    }
  }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      state.sel = (typeof saved.sel === "string") ? saved.sel : null;
      state.seen = (saved.seen && typeof saved.seen === "object") ? saved.seen : {};
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

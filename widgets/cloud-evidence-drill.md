---
id: 'a696e0bc-0060-4525-8138-463465ed3126'
title: Cloud verification problem set
summary_for_tutor: "A nine-task drill on reading cloud-provider records for exactly what they prove, ported from XLab's cloud-evidence-drill. The learner moves through the tasks with a numbered rail: (1) six true or false statements about billing records, power, workload data, accounting versus classification, the KYC threshold and RAND's metrics; (2) odd one out among four observables (the beneficial-ownership record is the odd one) plus a one-sentence principle that must name who controls the account versus technical activity metrics; (3) select every data category a KYC-implementing provider has without code access (five of eight); (4) match four observables to the strongest conclusion each supports (compute estimate, training more likely, KYC identity link, attested property); (5) fill five gaps of a verification map from an eight-term bank (KYC, record keeping, workload classification, compute accounting, reporting or escalation); (6) order the six stages of the Egan and Heim KYC scheme; (7) name four mechanisms from descriptions; (8) a rendering-declared customer showing a training-shaped pattern: pick the three supported conclusions and reject intent, contents and violation; (9) six sibling accounts each under a per-account FLOP threshold: the justified response is to open an investigation. Each task has a Check answer button; a wrong check shows a hint and the sources, a right check shows XLab's explanation and marks the task solved. The learner's current picks, the principle sentence and which tasks are solved are in the widget state. Done means all nine tasks solved and Finish problem set clicked; the closing screen states that provider records can link an account to a verified identity, estimate resource use and support a classification, but do not establish intent, model contents, capability or a legal violation. When helping, hold the learner to the qualifiers in each prompt and do not give away an unsolved task's answer."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Cloud verification problem set</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "cloud-evidence-drill". -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  .drill { border: 1px solid var(--border); border-radius: 8px; background: #fff; overflow: hidden; }
  header { padding: 20px; border-bottom: 1px solid var(--border); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 26px; line-height: 1.15; margin: 10px 0 0; }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 22px; margin: 0; }
  .lede { color: var(--muted); margin: 8px 0 0; max-width: 42rem; }
  .rail { list-style: none; margin: 16px 0 0; padding: 0; display: grid; grid-template-columns: repeat(9, minmax(0, 1fr)); gap: 6px; }
  .rail button { width: 100%; min-height: 36px; padding: 4px 2px; font-size: 12px; border-radius: 6px; display: flex; align-items: center; justify-content: center; }
  .rail button.is-active { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); color: var(--accent-hover); font-weight: 600; }
  .rail button.is-done { background: var(--surface); }
  .task-head { padding: 10px 20px; border-bottom: 1px solid var(--border); display: flex; flex-wrap: wrap; align-items: baseline; gap: 4px 12px; }
  .task-head .eyebrow { letter-spacing: 0.06em; }
  .task-head h3 { font-size: 16px; font-weight: 600; margin: 0; }
  .task-head .kind { margin-left: auto; font-size: 12px; color: var(--muted); }
  .body { padding: 12px 20px 16px; }
  .prompt { border: 1px solid var(--border); background: var(--surface); border-radius: 8px; padding: 8px 12px; margin: 0; }
  .grid { display: grid; gap: 8px; margin-top: 12px; }
  @media (min-width: 640px) { .grid.two { grid-template-columns: 1fr 1fr; } }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; background: #fff; }
  .card.is-right { border-color: var(--accent); }
  .card.is-wrong { border-color: #b3261e; }
  .card .num { color: var(--muted); margin-right: 6px; }
  .card .mark { font-size: 12px; font-weight: 600; margin-left: 6px; }
  .card.is-wrong .mark { color: #b3261e; }
  .card.is-right .mark { color: var(--accent-hover); }
  .pair { display: flex; gap: 8px; margin-top: 6px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; text-align: left; }
  button:hover { background: var(--surface); }
  button:disabled { cursor: default; opacity: 0.55; }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled { background: var(--accent); opacity: 0.45; }
  button.small { min-width: 56px; padding: 5px 10px; text-align: center; }
  button.small.is-on { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); color: var(--accent-hover); font-weight: 600; }
  button.choice { display: flex; align-items: flex-start; gap: 10px; width: 100%; padding: 8px 12px; }
  button.choice.is-on { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  button.choice:disabled.is-on { opacity: 1; }
  .dot, .box { flex: 0 0 auto; width: 18px; height: 18px; margin-top: 2px; border: 1px solid var(--border); background: #fff; display: inline-flex; align-items: center; justify-content: center; }
  .dot { border-radius: 50%; }
  .box { border-radius: 4px; }
  .choice.is-on .dot { border-color: var(--accent); box-shadow: inset 0 0 0 4px var(--accent); }
  .choice.is-on .box { border-color: var(--accent); background: var(--accent); color: #fff; }
  .choice.is-on .box svg { display: block; }
  .box svg { display: none; }
  label.field { display: block; font-weight: 600; margin-top: 16px; }
  textarea { width: 100%; font: inherit; color: inherit; margin-top: 8px; border: 1px solid var(--border); border-radius: 8px; padding: 8px 12px; resize: vertical; min-height: 64px; }
  textarea:focus, select:focus { outline: 2px solid var(--accent); outline-offset: 1px; }
  select { width: 100%; font: inherit; color: inherit; margin-top: 8px; border: 1px solid var(--border); border-radius: 6px; padding: 8px 10px; background: #fff; }
  .row-grid { display: grid; gap: 10px; }
  .gap-row { display: grid; gap: 4px; }
  @media (min-width: 640px) { .gap-row { grid-template-columns: 1fr 240px; align-items: center; } .gap-row select { margin-top: 0; } }
  .seq { list-style: none; margin: 12px 0 0; padding: 0; display: grid; gap: 6px; }
  .seq li { display: flex; align-items: center; gap: 8px; border: 1px solid var(--border); border-radius: 8px; padding: 4px; background: #fff; }
  .seq li.is-dragging { opacity: 0.4; }
  .seq li.is-over { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .seq .grip { width: 36px; height: 36px; padding: 0; display: inline-flex; align-items: center; justify-content: center; color: var(--muted); cursor: grab; flex: 0 0 auto; }
  .seq .pos { flex: 0 0 auto; width: 26px; height: 26px; border: 1px solid var(--border); border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; color: var(--muted); font-size: 12px; }
  .seq .txt { flex: 1 1 auto; min-width: 0; }
  .seq .arrows { display: flex; gap: 4px; flex: 0 0 auto; }
  .seq .arrows button { width: 36px; height: 36px; padding: 0; display: inline-flex; align-items: center; justify-content: center; }
  .ordered { list-style: none; margin: 12px 0 0; padding: 0; display: grid; gap: 6px; }
  @media (min-width: 640px) { .ordered { grid-template-columns: 1fr 1fr; } }
  .ordered li { border: 1px solid var(--border); border-radius: 8px; padding: 8px 12px; display: flex; gap: 8px; }
  .ordered .num { color: var(--muted); font-size: 12px; font-weight: 600; flex: 0 0 auto; }
  .check { margin-top: 10px; }
  .check .end { display: flex; justify-content: flex-end; }
  .status { border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; display: flex; gap: 10px; align-items: flex-start; }
  .status.ok { border-color: var(--accent); background: var(--surface); }
  .status.bad { border-color: #b3261e; }
  .status .icon { flex: 0 0 auto; margin-top: 2px; color: var(--accent-hover); }
  .status .title { font-weight: 600; margin: 0; }
  .status .text { margin: 4px 0 0; color: var(--muted); }
  .status.bad .text { color: #b3261e; margin: 0; }
  details { margin-top: 6px; font-size: 12px; }
  summary { cursor: pointer; font-weight: 600; color: var(--accent-hover); }
  details ul { margin: 6px 0 0; padding: 0; list-style: none; display: flex; flex-wrap: wrap; gap: 4px 14px; }
  details.review { margin-top: 12px; font-size: 14px; border: 1px solid var(--border); border-radius: 8px; padding: 8px 12px; }
  details.review summary { color: var(--text); }
  details.review ol, details.review ul, details.review dl { margin: 10px 0 0; padding: 0 0 0 0; display: grid; gap: 10px; list-style: none; }
  @media (min-width: 640px) { details.review ol, details.review ul, details.review dl { grid-template-columns: 1fr 1fr; } }
  details.review li, details.review dd { color: var(--muted); }
  details.review li b, details.review dt { color: var(--text); font-weight: 600; }
  details.review dd { margin: 2px 0 0; }
  details.review .tag { color: var(--muted); margin-right: 4px; }
  a { color: var(--accent-hover); font-weight: 500; text-decoration: none; }
  a:hover { text-decoration: underline; }
  .ok-line { border: 1px solid var(--accent); background: var(--surface); border-radius: 8px; padding: 8px 12px; margin: 12px 0 0; font-weight: 500; }
  nav { margin-top: 12px; padding-top: 10px; border-top: 1px solid var(--border); display: flex; align-items: center; justify-content: space-between; gap: 8px; }
  nav .count { font-size: 12px; color: var(--muted); }
  .hint { color: var(--muted); font-size: 12px; text-align: right; margin: 8px 0 0; }
  .finish { padding: 32px 20px; text-align: center; }
  .finish .inner { max-width: 40rem; margin: 0 auto; }
  .finish p { color: var(--muted); margin: 12px 0 0; }
  .finish .actions { display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; margin-top: 20px; }
  .finish a.btn { display: inline-flex; align-items: center; gap: 6px; border: 1px solid var(--border); border-radius: 8px; padding: 8px 12px; color: var(--text); }
  .finish a.btn:hover { background: var(--surface); text-decoration: none; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); }
  @media (max-width: 480px) { header, .task-head, .body { padding-left: 12px; padding-right: 12px; } .rail button { min-height: 32px; font-size: 11px; } }
</style>
</head>
<body>
<section class="drill" id="drill" aria-label="Cloud verification problem set"></section>
<script>
(function () {
  "use strict";

  // ---------- Data (verbatim from XLab's cloud-evidence-drill data file) ----------
  var SOURCES = {
    heimRecords: { label: "Heim et al., §3.2 and Appendix B, Table 4", href: "https://arxiv.org/html/2403.08501v2#S3.SS2" },
    heimVerification: { label: "Heim et al., §§3.3.2–3.3.4", href: "https://arxiv.org/html/2403.08501v2#S3.SS3.SSS2" },
    kyc: { label: "Egan and Heim, §§2.1–2.2.2", href: "https://arxiv.org/html/2310.13625v1#S2.SS1" },
    randMetrics: { label: "Moon et al., “Cloud Service Provider Monitoring Strategies” and “Finding a Detection Gap”", href: "https://www.rand.org/pubs/research_reports/RRA3686-1.html" },
    randClosing: { label: "Moon et al., “Closing Detection Gaps”", href: "https://www.rand.org/pubs/research_reports/RRA3686-1.html" },
    carnegieScope: { label: "Tan, “Cloud Controls Must Contend With ‘Who’ and ‘What’ They Restrict”", href: "https://carnegieendowment.org/research/2026/05/the-geopolitical-debates-over-controlling-cloud-compute" }
  };

  var TRUE_FALSE = [
    { id: "billing", claim: "A provider’s billing records can include the hardware configuration requested and the number of hours it was used.", answer: true,
      explanation: "True. Heim et al. list requested hardware configuration and hours of use as billing-related technical information." },
    { id: "power", claim: "Cluster power consumption, by itself, establishes that a customer is training a frontier model.", answer: false,
      explanation: "False. Power can contribute to workload classification or compute accounting; it does not identify the workload with certainty." },
    { id: "workload-data", claim: "Customer code, data, and hyperparameters are ordinarily collected for cloud billing.", answer: false,
      explanation: "False. Heim et al. mark workload-level code, data, and hyperparameters as not currently collected for this purpose." },
    { id: "same-question", claim: "Compute accounting and workload classification answer the same verification question.", answer: false,
      explanation: "False. Accounting estimates how much compute was used; classification estimates what kind of workload used it." },
    { id: "kyc-before-threshold", claim: "Under the proposed KYC scheme, a provider would monitor compute accumulation and move a customer into KYC before the threshold is crossed.", answer: true,
      explanation: "True. Egan and Heim propose continuous monitoring so customers approaching the threshold enter KYC before crossing it." },
    { id: "more-metrics", claim: "Adding mandatory metrics can narrow a detection gap, but the thresholds still require empirical review as technology changes.", answer: true,
      explanation: "True. RAND recommends both additional metrics and continuing work on thresholds that can adapt to technological progress." }
  ];

  var ODD_ITEMS = [
    { id: "power", text: "Total power used by an account’s instances" },
    { id: "cluster", text: "Maximum GPU cluster size used by one instance" },
    { id: "flops", text: "Total FLOPs across an account’s instances" },
    { id: "owner", text: "Verified beneficial-ownership record" }
  ];

  var AVAILABLE = [
    { id: "customer", text: "Customer name, billing address, IP addresses, and access times", answer: true },
    { id: "hardware", text: "Requested hardware configuration and hours of use", answer: true },
    { id: "cluster", text: "Cluster-level power consumption and network bandwidth between nodes", answer: true },
    { id: "node", text: "Node-level accelerator utilization and memory-bandwidth utilization retained as operational metrics", answer: true },
    { id: "kyc-record", text: "Identity, beneficial-ownership, and declared-purpose records required under the proposed KYC scheme", answer: true },
    { id: "workload", text: "The customer’s exact code, data, and hyperparameters without a special access protocol", answer: false },
    { id: "dataset", text: "The contents of the training dataset from billing records alone", answer: false },
    { id: "intent", text: "The customer’s actual strategic intent", answer: false }
  ];

  var MATCH_CONCLUSIONS = [
    { id: "resource", text: "An estimate of compute consumed" },
    { id: "training-likely", text: "The workload is more likely to be large-scale training" },
    { id: "identity", text: "The account is associated with the entity and owners verified under KYC" },
    { id: "property", text: "A specified workload property is verified without exposing the rest of the code or data" }
  ];

  var MATCH_ROWS = [
    { id: "billing", observable: "Hardware configuration, hours of use, and measured utilization", answerId: "resource" },
    { id: "shape", observable: "Sustained accelerator utilization, parallelization-shaped communication, and limited external-network traffic", answerId: "training-likely" },
    { id: "due-diligence", observable: "Verified incorporation, key-personnel, and beneficial-ownership records", answerId: "identity" },
    { id: "confidential-computing", observable: "A trusted-execution-environment proof presented by an attester", answerId: "property" }
  ];

  var PIPELINE_OPTIONS = ["KYC", "record keeping", "workload classification", "compute accounting", "reporting or escalation", "attestation", "model evaluation", "source-code inspection"];

  var PIPELINE_GAPS = [
    { id: "identity", before: "Verify the customer and beneficial owners through", answer: "KYC" },
    { id: "records", before: "Retain service-use data through", answer: "record keeping" },
    { id: "type", before: "Estimate whether the activity is training through", answer: "workload classification" },
    { id: "amount", before: "Estimate the amount of compute through", answer: "compute accounting" },
    { id: "response", before: "Refer a threshold crossing or high-risk profile through", answer: "reporting or escalation" }
  ];

  var SEQUENCE = [
    { id: "monitor", text: "Provider monitors each customer’s accumulated compute use" },
    { id: "approach", text: "A customer’s projected use approaches the applicable threshold" },
    { id: "kyc", text: "Provider verifies the customer entity and beneficial owners" },
    { id: "purpose", text: "Provider records the intended use and expected project scope" },
    { id: "continue", text: "Provider continues monitoring for crossings and risk indicators" },
    { id: "respond", text: "A crossing or high-risk profile is reported or subject to required controls" }
  ];
  var SEQUENCE_START = ["purpose", "monitor", "respond", "approach", "continue", "kyc"];

  var CONCEPTS = ["KYC", "record keeping", "workload classification", "attestation"];

  var CONCEPT_ROWS = [
    { id: "customer", description: "Verification of the customer entity and, where required, its beneficial owners.", answer: "KYC" },
    { id: "events", description: "Creation and retention of time-stamped service-use records so activity can be reconstructed later.", answer: "record keeping" },
    { id: "category", description: "Use of observable technical characteristics to estimate whether a workload belongs to a category such as training or inference.", answer: "workload classification" },
    { id: "proof", description: "In a confidential-computing protocol, presentation of a verifiable claim about a workload property without revealing the remaining code or data.", answer: "attestation" }
  ];

  var CASE_OPTIONS = [
    { id: "linked", text: "The account is associated with the company and owners verified in the KYC record.", answer: true },
    { id: "classification", text: "The technical pattern makes large-scale training more likely than the declared rendering workload.", answer: true },
    { id: "review", text: "The discrepancy between the declaration and the technical pattern supports further review.", answer: true },
    { id: "contents", text: "The provider has verified the model architecture and training dataset.", answer: false },
    { id: "violation", text: "The provider has established that a prohibited training run occurred.", answer: false },
    { id: "intent", text: "The provider now knows why the customer authorized the workload.", answer: false }
  ];

  var INFERENCE_OPTIONS = [
    { id: "separate", text: "Treat every account as compliant because each remained below the per-account threshold." },
    { id: "finding", text: "Issue a violation finding because aggregate compute alone proves that the owner conducted prohibited training." },
    { id: "investigate", text: "Open an investigation: test whether the rule aggregates commonly controlled accounts and whether the sessions form one training run." },
    { id: "capability", text: "Infer the resulting model’s capabilities from aggregate compute alone." }
  ];

  var TASKS = [
    { label: "True / false", title: "True or false", time: "3 min" },
    { label: "Odd one out", title: "Find the odd one out", time: "3 min" },
    { label: "Select all", title: "Select all that apply", time: "3 min" },
    { label: "Matching", title: "Match the pairs", time: "4 min" },
    { label: "Gaps", title: "Fill the gaps", time: "4 min" },
    { label: "Sequence", title: "Put the stages in order", time: "3 min" },
    { label: "Concepts", title: "Name the mechanism", time: "3 min" },
    { label: "Case", title: "Qualify the evidence", time: "4 min" },
    { label: "Inference", title: "Choose the permissible inference", time: "3 min" }
  ];

  // Odd-one-out principle check (verbatim from XLab's engine).
  var ACTOR_TERMS = /\b(actor|customer|entity|identity|owner|owners|ownership|beneficial|who|person|people|user)\b/i;
  var ACTIVITY_TERMS = /\b(account activity|activity|compute|flops|gpu|hardware|metric|metrics|operation|operations|power|resource|resources|technical|telemetry|usage|workload)\b/i;
  var CONTRAST_TERMS = /\b(but|compared|contrast|different|other|others|rather|remaining|three|whereas|while)\b/i;
  function explainsOddCloudObservable(response) {
    var normalized = response.trim().replace(/\s+/g, " ");
    return normalized.length >= 28 && ACTOR_TERMS.test(normalized) && ACTIVITY_TERMS.test(normalized) && CONTRAST_TERMS.test(normalized);
  }

  // Seeded shuffle (ported from XLab's src/lib/shuffle.ts): option lists are
  // shown in an order that is a function of the question id, never of the
  // authored order, so no task falls to the diagonal or to "the first N".
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
  function seededShuffle(seed, items) {
    var n = items.length, order = [], i, j, tmp;
    for (i = 0; i < n; i++) order.push(i);
    var rand = prng(hashSeed(seed));
    for (i = n - 1; i > 0; i--) { j = Math.floor(rand() * (i + 1)); tmp = order[i]; order[i] = order[j]; order[j] = tmp; }
    return order.map(function (k) { return items[k]; });
  }
  var ODD_ITEMS_SHOWN = seededShuffle("cloud-odd-item", ODD_ITEMS);
  var MATCH_CONCLUSIONS_SHOWN = seededShuffle("cloud-match-conclusions", MATCH_CONCLUSIONS);
  var PIPELINE_OPTIONS_SHOWN = seededShuffle("cloud-pipeline-options", PIPELINE_OPTIONS);
  var CONCEPTS_SHOWN = seededShuffle("cloud-concepts", CONCEPTS);
  var CASE_OPTIONS_SHOWN = seededShuffle("cloud-case-options", CASE_OPTIONS);
  var INFERENCE_OPTIONS_SHOWN = seededShuffle("cloud-permissible-inference", INFERENCE_OPTIONS);

  // ---------- State ----------
  var STORAGE_KEY = "lens-widget-cloud-evidence-drill";
  var state, completedOnce = false, dragId = null;

  function freshAnswers() {
    return { tf: {}, odd: { itemId: "", principle: "" }, avail: [], match: {}, pipe: {}, seq: SEQUENCE_START.slice(), concept: {}, caseSel: [], infer: "" };
  }
  function freshState() {
    return { task: 0, solved: [], finished: false, verdict: [null, null, null, null, null, null, null, null, null], answers: freshAnswers() };
  }
  state = freshState();

  function isSolved(i) { return state.solved.indexOf(i) !== -1; }
  function allSolved() { return state.solved.length === TASKS.length; }
  function markSolved(i) { if (!isSolved(i)) state.solved.push(i); }

  // ---------- DOM helpers ----------
  function el(tag, cls, text) {
    var node = document.createElement(tag);
    if (cls) node.className = cls;
    if (text !== undefined && text !== null) node.textContent = text;
    return node;
  }
  function svg(path, size) {
    var s = document.createElementNS("http://www.w3.org/2000/svg", "svg");
    s.setAttribute("viewBox", "0 0 24 24"); s.setAttribute("width", size || 14); s.setAttribute("height", size || 14);
    s.setAttribute("fill", "none"); s.setAttribute("stroke", "currentColor"); s.setAttribute("stroke-width", "2.5");
    s.setAttribute("stroke-linecap", "round"); s.setAttribute("stroke-linejoin", "round"); s.setAttribute("aria-hidden", "true");
    var p = document.createElementNS("http://www.w3.org/2000/svg", "path");
    p.setAttribute("d", path); s.appendChild(p);
    return s;
  }
  var ICON = { check: "M5 13l4 4L19 7", up: "M12 19V5M5 12l7-7 7 7", down: "M12 5v14M5 12l7 7 7-7",
    grip: "M9 6h.01M9 12h.01M9 18h.01M15 6h.01M15 12h.01M15 18h.01", ext: "M14 4h6v6M20 4l-9 9M18 13v6H5V6h6",
    circle: "M12 2a10 10 0 1 0 0 20 10 10 0 0 0 0-20zM8 12l3 3 5-6" };
  function button(text, cls, onClick) {
    var b = el("button", cls, text); b.type = "button";
    if (onClick) b.addEventListener("click", onClick);
    return b;
  }
  function link(source) {
    var a = el("a", null, source.label);
    a.href = source.href; a.target = "_blank"; a.rel = "noopener";
    a.appendChild(document.createTextNode(" ")); a.appendChild(svg(ICON.ext, 11));
    return a;
  }
  function byId(list, id) { for (var i = 0; i < list.length; i++) if (list[i].id === id) return list[i]; return null; }
  function findById(list, id) { var x = byId(list, id); return x ? x : null; }
  function findByText(list, key) { for (var i = 0; i < list.length; i++) if (list[i] === key) return list[i]; return null; }

  // ---------- Persistence ----------
  function persist() {
    var summary = summarize();
    if (window.Lens) { window.Lens.saveState(state, summary); return; }
    try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) { /* no storage */ }
  }
  function statusWord(i) {
    if (isSolved(i)) return "solved";
    if (state.verdict[i] === "wrong") return "last check incorrect";
    return "not yet checked";
  }
  function short(text) { return text.length > 70 ? text.slice(0, 67) + "..." : text; }
  function summarize() {
    var a = state.answers, parts = [], k, list;
    parts.push("Cloud verification problem set: " + state.solved.length + " of 9 tasks solved" +
      (state.finished ? "; finished." : "; currently on task " + (state.task + 1) + " (" + TASKS[state.task].title + ")."));
    list = [];
    TRUE_FALSE.forEach(function (item, n) { if (item.id in a.tf) list.push((n + 1) + " " + (a.tf[item.id] ? "True" : "False")); });
    if (list.length) parts.push("Task 1 (true or false, " + statusWord(0) + "): marked " + list.join(", ") + ".");
    if (a.odd.itemId || a.odd.principle.trim()) {
      var odd = byId(ODD_ITEMS, a.odd.itemId);
      parts.push("Task 2 (odd one out, " + statusWord(1) + "): picked " + (odd ? "“" + odd.text + "”" : "nothing yet") +
        "; principle written: “" + a.odd.principle.trim() + "”.");
    }
    if (a.avail.length) parts.push("Task 3 (select all, " + statusWord(2) + "): selected " + a.avail.map(function (id) { var x = byId(AVAILABLE, id); return x ? short(x.text) : id; }).join("; ") + ".");
    list = [];
    MATCH_ROWS.forEach(function (row) { if (a.match[row.id]) { var c = byId(MATCH_CONCLUSIONS, a.match[row.id]); list.push(short(row.observable) + " -> " + (c ? c.text : a.match[row.id])); } });
    if (list.length) parts.push("Task 4 (matching, " + statusWord(3) + "): " + list.join("; ") + ".");
    list = [];
    PIPELINE_GAPS.forEach(function (gap) { if (a.pipe[gap.id]) list.push(gap.before + " " + a.pipe[gap.id]); });
    if (list.length) parts.push("Task 5 (gaps, " + statusWord(4) + "): " + list.join("; ") + ".");
    if (state.verdict[5] || a.seq.join() !== SEQUENCE_START.join()) {
      parts.push("Task 6 (sequence, " + statusWord(5) + "): current order " + a.seq.map(function (id, n) { var x = byId(SEQUENCE, id); return (n + 1) + ". " + (x ? x.text : id); }).join("; ") + ".");
    }
    list = [];
    CONCEPT_ROWS.forEach(function (row) { if (a.concept[row.id]) list.push(short(row.description) + " -> " + a.concept[row.id]); });
    if (list.length) parts.push("Task 7 (concepts, " + statusWord(6) + "): " + list.join("; ") + ".");
    if (a.caseSel.length) parts.push("Task 8 (case, " + statusWord(7) + "): selected " + a.caseSel.map(function (id) { var x = byId(CASE_OPTIONS, id); return x ? x.text : id; }).join(" / ") + ".");
    if (a.infer) { var inf = byId(INFERENCE_OPTIONS, a.infer); parts.push("Task 9 (inference, " + statusWord(8) + "): picked “" + (inf ? inf.text : a.infer) + "”."); }
    return parts.join(" ");
  }

  // ---------- Generic pieces ----------
  function prompt(text) { return el("p", "prompt", text); }

  function sourcesDetails(sources) {
    var d = el("details"), s = el("summary", null, "Sources (" + sources.length + ")"), ul = el("ul");
    sources.forEach(function (src) { var li = el("li"); li.appendChild(link(src)); ul.appendChild(li); });
    d.appendChild(s); d.appendChild(ul);
    return d;
  }

  // The Check answer row: a button before any check, a hint after a wrong
  // check, the explanation after a right one. Mirrors XLab's CheckRow.
  function checkRow(i, spec) {
    var wrap = el("div", "check"), v = state.verdict[i];
    if (v === "correct") {
      var ok = el("div", "status ok"); ok.setAttribute("role", "status");
      var icon = el("span", "icon"); icon.appendChild(svg(ICON.circle, 20)); ok.appendChild(icon);
      var body = el("div");
      body.appendChild(el("p", "title", "Supported"));
      body.appendChild(el("p", "text", spec.correct));
      body.appendChild(sourcesDetails(spec.sources));
      ok.appendChild(body); wrap.appendChild(ok);
    } else if (v === "wrong") {
      var bad = el("div", "status bad"); bad.setAttribute("role", "status");
      var b2 = el("div"); b2.style.flex = "1 1 auto";
      b2.appendChild(el("p", "text", spec.wrong));
      b2.appendChild(sourcesDetails(spec.sources));
      bad.appendChild(b2); wrap.appendChild(bad);
    } else {
      var end = el("div", "end");
      var btn = button("Check answer", "primary", function () {
        var right = spec.isRight();
        state.verdict[i] = right ? "correct" : "wrong";
        if (right) markSolved(i);
        persist(); render();
      });
      btn.disabled = !spec.canCheck();
      end.appendChild(btn); wrap.appendChild(end);
    }
    return wrap;
  }

  function change(i) { state.verdict[i] = null; persist(); render(); }

  function radioButton(text, on, disabled, onClick) {
    var b = button(null, "choice" + (on ? " is-on" : ""), onClick);
    b.setAttribute("role", "radio"); b.setAttribute("aria-checked", on ? "true" : "false"); b.disabled = disabled;
    b.appendChild(el("span", "dot")); b.appendChild(el("span", null, text));
    return b;
  }
  function checkButton(text, on, disabled, onClick) {
    var b = button(null, "choice" + (on ? " is-on" : ""), onClick);
    b.setAttribute("role", "checkbox"); b.setAttribute("aria-checked", on ? "true" : "false"); b.disabled = disabled;
    var box = el("span", "box"); box.appendChild(svg(ICON.check, 12));
    b.appendChild(box); b.appendChild(el("span", null, text));
    return b;
  }
  function selectBox(options, value, placeholder, disabled, onChange) {
    var s = el("select"), o0 = el("option", null, placeholder); o0.value = ""; s.appendChild(o0);
    options.forEach(function (opt) { var o = el("option", null, opt.text); o.value = opt.value; s.appendChild(o); });
    s.value = value || ""; s.disabled = disabled;
    s.addEventListener("change", function () { onChange(s.value); });
    return s;
  }
  function toggleIn(list, id) { var k = list.indexOf(id); if (k === -1) list.push(id); else list.splice(k, 1); }

  // ---------- Task 1: true or false ----------
  function taskTrueFalse(root) {
    var i = 0, a = state.answers.tf, v = state.verdict[i];
    root.appendChild(prompt("Determine whether each statement is true or false. Mark all six."));
    if (v === "correct") {
      root.appendChild(el("p", "ok-line", "All six statements are marked correctly. The full explanations remain available below."));
    } else {
      var grid = el("div", "grid two");
      TRUE_FALSE.forEach(function (item, n) {
        var card = el("div", "card"), p = el("p"); p.style.margin = "0";
        p.appendChild(el("span", "num", (n + 1) + ".")); p.appendChild(document.createTextNode(item.claim));
        if (v === "wrong") {
          var right = a[item.id] === item.answer;
          card.classList.add(right ? "is-right" : "is-wrong");
          p.appendChild(el("span", "mark", right ? "✓" : "✗"));
        }
        card.appendChild(p);
        var pair = el("div", "pair"); pair.setAttribute("role", "radiogroup"); pair.setAttribute("aria-label", item.claim);
        [true, false].forEach(function (val) {
          var b = button(val ? "True" : "False", "small" + (a[item.id] === val ? " is-on" : ""), function () { a[item.id] = val; change(i); });
          b.setAttribute("role", "radio"); b.setAttribute("aria-checked", a[item.id] === val ? "true" : "false");
          pair.appendChild(b);
        });
        card.appendChild(pair); grid.appendChild(card);
      });
      root.appendChild(grid);
    }
    root.appendChild(checkRow(i, {
      canCheck: function () { return TRUE_FALSE.every(function (item) { return item.id in a; }); },
      isRight: function () { return TRUE_FALSE.every(function (item) { return a[item.id] === item.answer; }); },
      wrong: "At least one marked row is incorrect. Revisit the red-bordered rows.",
      correct: "Correct: 1 True; 2 False; 3 False; 4 False; 5 True; 6 True.",
      sources: [SOURCES.heimRecords, SOURCES.heimVerification, SOURCES.kyc, SOURCES.randMetrics]
    }));
    if (v === "correct") {
      var d = el("details", "review"); d.appendChild(el("summary", null, "Review the six explanations"));
      var ol = el("ol");
      TRUE_FALSE.forEach(function (item, n) { var li = el("li"); li.appendChild(el("b", null, (n + 1) + ". ")); li.appendChild(document.createTextNode(item.explanation)); ol.appendChild(li); });
      d.appendChild(ol); root.appendChild(d);
    }
  }

  // ---------- Task 2: odd one out ----------
  function taskOdd(root) {
    var i = 1, a = state.answers.odd, done = state.verdict[i] === "correct";
    root.appendChild(prompt("One item differs from the other three in evidentiary type. Select it, then state the principle that explains the difference."));
    var grid = el("div", "grid two"); grid.setAttribute("role", "radiogroup"); grid.setAttribute("aria-label", "Select the odd item");
    ODD_ITEMS_SHOWN.forEach(function (item) {
      grid.appendChild(radioButton(item.text, a.itemId === item.id, done, function () { a.itemId = item.id; change(i); }));
    });
    root.appendChild(grid);
    var lab = el("label", "field", "In one sentence, state what the odd item records and what the other three measure."); lab.htmlFor = "odd-principle";
    root.appendChild(lab);
    var ta = el("textarea"); ta.id = "odd-principle"; ta.rows = 2; ta.value = a.principle; ta.disabled = done;
    var checkHolder = el("div");
    function buildCheck() {
      while (checkHolder.firstChild) checkHolder.removeChild(checkHolder.firstChild);
      checkHolder.appendChild(checkRow(i, {
        canCheck: function () { return !!a.itemId && a.principle.trim().length >= 28; },
        isRight: function () { return a.itemId === "owner" && explainsOddCloudObservable(a.principle); },
        wrong: "Both parts are required. Identify the item, then distinguish the kind of evidence it records from the kind measured by the other three.",
        correct: "The beneficial-ownership record concerns who controls the account. The other three are technical metrics of account activity.",
        sources: [SOURCES.randMetrics, SOURCES.kyc]
      }));
    }
    ta.addEventListener("input", function () { a.principle = ta.value; state.verdict[i] = null; persist(); buildCheck(); });
    root.appendChild(ta); buildCheck(); root.appendChild(checkHolder);
  }

  // ---------- Task 3: select all ----------
  function taskAvailable(root) {
    var i = 2, a = state.answers.avail, v = state.verdict[i];
    root.appendChild(prompt("A provider has implemented the proposed KYC scheme and retains its ordinary billing and operational records. It has no direct access to customer code or data. Select every category available under those conditions."));
    if (v === "correct") {
      var d = el("details", "review"); d.appendChild(el("summary", null, "Review the eight categories"));
      var ul = el("ul");
      AVAILABLE.forEach(function (item) { var li = el("li"); li.appendChild(el("span", "tag", item.answer ? "Available:" : "Not available:")); li.appendChild(el("b", null, item.text)); ul.appendChild(li); });
      d.appendChild(ul); root.appendChild(d);
    } else {
      var grid = el("div", "grid two");
      AVAILABLE.forEach(function (item) {
        grid.appendChild(checkButton(item.text, a.indexOf(item.id) !== -1, false, function () { toggleIn(a, item.id); change(i); }));
      });
      root.appendChild(grid);
    }
    root.appendChild(checkRow(i, {
      canCheck: function () { return a.length > 0; },
      isRight: function () { return AVAILABLE.every(function (item) { return (a.indexOf(item.id) !== -1) === item.answer; }); },
      wrong: "A selected category exceeds the stated access, or an available category is missing.",
      correct: "The first five categories are available under the stated conditions. Code, dataset contents, and actual intent are not.",
      sources: [SOURCES.heimRecords, SOURCES.kyc]
    }));
  }

  // ---------- Task 4: matching ----------
  function taskMatching(root) {
    var i = 3, a = state.answers.match, done = state.verdict[i] === "correct";
    root.appendChild(prompt("Match each item in the first column to the strongest conclusion it can support. Use each conclusion once."));
    var grid = el("div", "grid two");
    var opts = MATCH_CONCLUSIONS_SHOWN.map(function (c) { return { value: c.id, text: c.text }; });
    MATCH_ROWS.forEach(function (row) {
      var card = el("label", "card"); card.style.display = "block";
      var t = el("span", null, row.observable); t.style.fontWeight = "500"; t.style.display = "block"; card.appendChild(t);
      card.appendChild(selectBox(opts, a[row.id], "Choose a conclusion", done, function (val) { if (val) a[row.id] = val; else delete a[row.id]; change(i); }));
      grid.appendChild(card);
    });
    root.appendChild(grid);
    root.appendChild(checkRow(i, {
      canCheck: function () { return MATCH_ROWS.every(function (row) { return !!a[row.id]; }); },
      isRight: function () { return MATCH_ROWS.every(function (row) { return a[row.id] === row.answerId; }); },
      wrong: "At least one pair is incorrect. Distinguish identity, compute quantity, workload class, and a verified workload property.",
      correct: "Correct. The four evidence types support four different conclusions; none is interchangeable with another.",
      sources: [SOURCES.heimRecords, SOURCES.heimVerification, SOURCES.kyc]
    }));
  }

  // ---------- Task 5: fill the gaps ----------
  function taskPipeline(root) {
    var i = 4, a = state.answers.pipe, done = state.verdict[i] === "correct";
    root.appendChild(prompt("Complete the verification map by matching each function to its mechanism. Use five terms from the bank. Three terms are not used."));
    var box = el("div", "card"); box.style.marginTop = "12px";
    var rows = el("div", "row-grid");
    var opts = PIPELINE_OPTIONS_SHOWN.map(function (t) { return { value: t, text: t }; });
    PIPELINE_GAPS.forEach(function (gap) {
      var row = el("label", "gap-row");
      row.appendChild(el("span", null, gap.before));
      row.appendChild(selectBox(opts, a[gap.id], "Choose a term", done, function (val) { if (val) a[gap.id] = val; else delete a[gap.id]; change(i); }));
      rows.appendChild(row);
    });
    box.appendChild(rows); root.appendChild(box);
    root.appendChild(checkRow(i, {
      canCheck: function () { return PIPELINE_GAPS.every(function (gap) { return !!a[gap.id]; }); },
      isRight: function () { return PIPELINE_GAPS.every(function (gap) { return a[gap.id] === gap.answer; }); },
      wrong: "At least one term is assigned to the wrong function.",
      correct: "Correct: KYC; record keeping; workload classification; compute accounting; reporting or escalation.",
      sources: [SOURCES.heimRecords, SOURCES.heimVerification, SOURCES.kyc]
    }));
  }

  // ---------- Task 6: sequence ----------
  function taskSequence(root) {
    var i = 5, order = state.answers.seq, v = state.verdict[i];
    root.appendChild(prompt("Put the six stages of the Egan–Heim scheme in order. Drag a row or use its arrow buttons; the earliest event goes first."));
    function move(from, to) {
      if (to < 0 || to >= order.length || from === to) return;
      var id = order.splice(from, 1)[0]; order.splice(to, 0, id);
      change(i);
    }
    if (v === "correct") {
      var ol = el("ol", "ordered"); ol.setAttribute("aria-label", "Correct order of stages");
      order.forEach(function (id, n) { var li = el("li"); li.appendChild(el("span", "num", (n + 1) + ".")); li.appendChild(el("span", null, byId(SEQUENCE, id).text)); ol.appendChild(li); });
      root.appendChild(ol);
    } else {
      var list = el("ol", "seq"); list.setAttribute("aria-label", "Stages to put in order");
      order.forEach(function (id, n) {
        var item = byId(SEQUENCE, id), li = el("li"); li.draggable = true; li.dataset.id = id;
        var grip = button(null, "grip"); grip.appendChild(svg(ICON.grip, 18));
        grip.setAttribute("aria-label", "Move " + item.text + ". Current position " + (n + 1) + " of " + order.length + ". Use the arrow buttons to change it.");
        li.appendChild(grip);
        li.appendChild(el("span", "pos", String(n + 1)));
        li.appendChild(el("span", "txt", item.text));
        var arrows = el("span", "arrows");
        var up = button(null, null, function () { move(n, n - 1); }); up.appendChild(svg(ICON.up, 14)); up.setAttribute("aria-label", "Move " + item.text + " earlier"); up.disabled = n === 0;
        var dn = button(null, null, function () { move(n, n + 1); }); dn.appendChild(svg(ICON.down, 14)); dn.setAttribute("aria-label", "Move " + item.text + " later"); dn.disabled = n === order.length - 1;
        arrows.appendChild(up); arrows.appendChild(dn); li.appendChild(arrows);
        li.addEventListener("dragstart", function (e) { dragId = id; li.classList.add("is-dragging"); if (e.dataTransfer) { e.dataTransfer.effectAllowed = "move"; try { e.dataTransfer.setData("text/plain", id); } catch (err) { /* ignore */ } } });
        li.addEventListener("dragend", function () { dragId = null; li.classList.remove("is-dragging"); });
        li.addEventListener("dragover", function (e) { if (dragId && dragId !== id) { e.preventDefault(); li.classList.add("is-over"); } });
        li.addEventListener("dragleave", function () { li.classList.remove("is-over"); });
        li.addEventListener("drop", function (e) { e.preventDefault(); li.classList.remove("is-over"); if (!dragId || dragId === id) return; move(order.indexOf(dragId), order.indexOf(id)); dragId = null; });
        list.appendChild(li);
      });
      root.appendChild(list);
    }
    root.appendChild(checkRow(i, {
      canCheck: function () { return true; },
      isRight: function () { return SEQUENCE.every(function (item, n) { return order[n] === item.id; }); },
      wrong: "The order is incorrect under the scheme described in the question.",
      correct: "Correct. Monitor accumulation → approaching threshold → KYC and intended use → continued monitoring → reporting or required controls.",
      sources: [SOURCES.kyc, SOURCES.heimRecords]
    }));
  }

  // ---------- Task 7: concepts ----------
  function taskConcept(root) {
    var i = 6, a = state.answers.concept, v = state.verdict[i];
    root.appendChild(prompt("Match each description to the correct mechanism. Use each mechanism once."));
    if (v === "correct") {
      var d = el("details", "review"); d.appendChild(el("summary", null, "Review the four matches"));
      var dl = el("dl");
      CONCEPT_ROWS.forEach(function (row) { var wrap = el("div"); wrap.appendChild(el("dt", null, row.answer)); wrap.appendChild(el("dd", null, row.description)); dl.appendChild(wrap); });
      d.appendChild(dl); root.appendChild(d);
    } else {
      var grid = el("div", "grid two");
      var opts = CONCEPTS_SHOWN.map(function (t) { return { value: t, text: t }; });
      CONCEPT_ROWS.forEach(function (row) {
        var card = el("label", "card"); card.style.display = "block";
        card.appendChild(el("span", null, row.description));
        card.appendChild(selectBox(opts, a[row.id], "Choose a mechanism", false, function (val) { if (val) a[row.id] = val; else delete a[row.id]; change(i); }));
        grid.appendChild(card);
      });
      root.appendChild(grid);
    }
    root.appendChild(checkRow(i, {
      canCheck: function () { return CONCEPT_ROWS.every(function (row) { return !!a[row.id]; }); },
      isRight: function () { return CONCEPT_ROWS.every(function (row) { return a[row.id] === row.answer; }); },
      wrong: "At least one mechanism is incorrect. Distinguish identity verification, retained records, classification, and a verifiable claim.",
      correct: "Correct: KYC verifies identity; record keeping preserves service-use records; classification estimates workload type; attestation presents a verifiable claim.",
      sources: [SOURCES.heimRecords, SOURCES.heimVerification]
    }));
  }

  // ---------- Task 8: case ----------
  function taskCase(root) {
    var i = 7, a = state.answers.caseSel, done = state.verdict[i] === "correct";
    root.appendChild(prompt("A provider verifies a customer company and its recorded beneficial owners. The customer declares a rendering workload. It then requests tens of thousands of accelerators and shows sustained accelerator utilization, communication patterns associated with parallelization, and limited traffic to external networks. Select every conclusion supported by these facts."));
    var grid = el("div", "grid two");
    CASE_OPTIONS_SHOWN.forEach(function (item) {
      grid.appendChild(checkButton(item.text, a.indexOf(item.id) !== -1, done, function () { toggleIn(a, item.id); change(i); }));
    });
    root.appendChild(grid);
    root.appendChild(checkRow(i, {
      canCheck: function () { return a.length > 0; },
      isRight: function () { return CASE_OPTIONS.every(function (item) { return (a.indexOf(item.id) !== -1) === item.answer; }); },
      wrong: "At least one conclusion exceeds the stated access, or one supported conclusion was omitted.",
      correct: "The KYC record links the account; the technical pattern supports a training classification and further review. It does not reveal intent, contents, or a violation.",
      sources: [SOURCES.heimVerification, SOURCES.kyc]
    }));
  }

  // ---------- Task 9: inference ----------
  function taskInference(root) {
    var i = 8, a = state.answers, done = state.verdict[i] === "correct";
    root.appendChild(prompt("Six accounts are registered to subsidiaries with the same verified beneficial owner. They run GPU sessions in sequence. Every session remains below a per-account FLOP threshold, but their aggregate compute exceeds it, and large data transfers precede the later sessions. Which response is justified?"));
    var grid = el("div", "grid two"); grid.setAttribute("role", "radiogroup"); grid.setAttribute("aria-label", "Select the justified response");
    INFERENCE_OPTIONS_SHOWN.forEach(function (opt) {
      grid.appendChild(radioButton(opt.text, a.infer === opt.id, done, function () { a.infer = opt.id; change(i); }));
    });
    root.appendChild(grid);
    root.appendChild(checkRow(i, {
      canCheck: function () { return !!a.infer; },
      isRight: function () { return a.infer === "investigate"; },
      wrong: "The selected response either ignores a documented detection gap or treats aggregate compute as proof of facts it cannot establish.",
      correct: "The pattern supports investigation. A finding still depends on the rule’s aggregation and coverage provisions and on evidence that the sessions form one training run.",
      sources: [SOURCES.randMetrics, SOURCES.randClosing, SOURCES.kyc, SOURCES.carnegieScope]
    }));
  }

  var TASK_RENDERERS = [taskTrueFalse, taskOdd, taskAvailable, taskMatching, taskPipeline, taskSequence, taskConcept, taskCase, taskInference];

  // ---------- Frame ----------
  var rootEl = document.getElementById("drill");

  function showTask(n) {
    if (n < 0 || n >= TASKS.length) return;
    state.task = n; state.finished = false;
    persist(); render();
    var head = rootEl.querySelector(".task-head");
    if (head && head.scrollIntoView) head.scrollIntoView({ block: "start" });
  }
  function finish() {
    if (!allSolved()) return;
    state.finished = true;
    if (!completedOnce) { completedOnce = true; if (window.Lens) window.Lens.complete(); }
    persist(); render();
  }
  function restart() {
    var keep = completedOnce;
    state = freshState(); completedOnce = keep;
    persist(); render();
  }

  function renderHeader() {
    var h = el("header");
    h.appendChild(el("p", "eyebrow", "30 minutes"));
    h.appendChild(el("h1", null, "Cloud verification problem set"));
    h.appendChild(el("p", "lede", "Answer from the assigned readings. Treat every qualifier as part of the question. Select only conclusions supported by the stated access and evidence."));
    var rail = el("ol", "rail"); rail.setAttribute("aria-label", "Cloud evidence drill progress");
    TASKS.forEach(function (task, n) {
      var li = el("li"), done = state.finished || isSolved(n), active = !state.finished && n === state.task;
      var b = button(null, (active ? "is-active" : "") + (done ? " is-done" : ""), function () { showTask(n); });
      if (done) b.appendChild(svg(ICON.check, 14)); else b.textContent = String(n + 1);
      if (active) b.setAttribute("aria-current", "step");
      b.setAttribute("aria-label", "Task " + (n + 1) + ": " + task.label + (done ? ", complete" : ""));
      b.title = (n + 1) + ". " + task.label;
      li.appendChild(b); rail.appendChild(li);
    });
    h.appendChild(rail);
    return h;
  }

  function renderFinish() {
    var sec = el("div", "finish"), inner = el("div", "inner");
    var icon = el("div"); icon.style.color = "#9a5c10"; icon.appendChild(svg(ICON.circle, 36)); inner.appendChild(icon);
    var h = el("h2", null, "Problem set complete"); h.style.marginTop = "12px"; inner.appendChild(h);
    inner.appendChild(el("p", null, "Provider-held records can associate an account with a verified identity record, estimate resource use, and support a workload classification. They do not by themselves establish intent, model contents, capability, or a legal violation."));
    inner.appendChild(el("p", null, "The final policy question remains: which actors and workloads should be covered, at what cost, and across which jurisdictions?"));
    var actions = el("div", "actions");
    var a = el("a", "btn", "Policy scope reading"); a.href = SOURCES.carnegieScope.href; a.target = "_blank"; a.rel = "noopener"; a.appendChild(svg(ICON.ext, 12));
    actions.appendChild(a);
    actions.appendChild(button("Run again", null, restart));
    inner.appendChild(actions); sec.appendChild(inner);
    return sec;
  }

  function renderTaskView() {
    var frag = document.createDocumentFragment(), n = state.task, task = TASKS[n];
    var head = el("div", "task-head"); head.setAttribute("aria-live", "polite");
    head.appendChild(el("p", "eyebrow", "Task " + (n + 1) + " of " + TASKS.length + " · " + task.time));
    head.appendChild(el("h3", null, task.title));
    head.appendChild(el("span", "kind", task.label));
    frag.appendChild(head);
    var body = el("div", "body");
    TASK_RENDERERS[n](body);
    var nav = el("nav"); nav.setAttribute("aria-label", "Move between cloud problem-set tasks");
    var prev = button("Previous", null, function () { showTask(n - 1); }); prev.disabled = n === 0; nav.appendChild(prev);
    nav.appendChild(el("span", "count", state.solved.length + " of " + TASKS.length + " complete"));
    if (n < TASKS.length - 1) {
      nav.appendChild(button("Next", "primary", function () { showTask(n + 1); }));
    } else {
      var fin = button("Finish problem set", "primary", finish); fin.disabled = !allSolved(); nav.appendChild(fin);
    }
    body.appendChild(nav);
    if (n === TASKS.length - 1 && !allSolved()) {
      body.appendChild(el("p", "hint", "Complete all nine tasks before finishing. Use the numbered navigation above to return to any unfinished task."));
    }
    frag.appendChild(body);
    return frag;
  }

  function render() {
    while (rootEl.firstChild) rootEl.removeChild(rootEl.firstChild);
    rootEl.appendChild(renderHeader());
    if (state.finished) rootEl.appendChild(renderFinish()); else rootEl.appendChild(renderTaskView());
  }

  // ---------- Restore ----------
  function hydrate(saved, meta) {
    var fresh = freshState();
    if (saved && typeof saved === "object") {
      if (typeof saved.task === "number" && saved.task >= 0 && saved.task < TASKS.length) fresh.task = saved.task;
      if (Array.isArray(saved.solved)) fresh.solved = saved.solved.filter(function (x) { return typeof x === "number" && x >= 0 && x < TASKS.length; });
      if (Array.isArray(saved.verdict)) for (var k = 0; k < TASKS.length; k++) fresh.verdict[k] = saved.verdict[k] === "correct" || saved.verdict[k] === "wrong" ? saved.verdict[k] : null;
      fresh.finished = !!saved.finished && fresh.solved.length === TASKS.length;
      var sa = saved.answers, fa = fresh.answers;
      if (sa && typeof sa === "object") {
        if (sa.tf && typeof sa.tf === "object") TRUE_FALSE.forEach(function (it) { if (typeof sa.tf[it.id] === "boolean") fa.tf[it.id] = sa.tf[it.id]; });
        if (sa.odd && typeof sa.odd === "object") { if (byId(ODD_ITEMS, sa.odd.itemId)) fa.odd.itemId = sa.odd.itemId; if (typeof sa.odd.principle === "string") fa.odd.principle = sa.odd.principle; }
        if (Array.isArray(sa.avail)) fa.avail = sa.avail.filter(function (id) { return !!byId(AVAILABLE, id); });
        if (sa.match && typeof sa.match === "object") MATCH_ROWS.forEach(function (r) { if (byId(MATCH_CONCLUSIONS, sa.match[r.id])) fa.match[r.id] = sa.match[r.id]; });
        if (sa.pipe && typeof sa.pipe === "object") PIPELINE_GAPS.forEach(function (g) { if (PIPELINE_OPTIONS.indexOf(sa.pipe[g.id]) !== -1) fa.pipe[g.id] = sa.pipe[g.id]; });
        if (Array.isArray(sa.seq) && sa.seq.length === SEQUENCE.length && SEQUENCE.every(function (s) { return sa.seq.indexOf(s.id) !== -1; })) fa.seq = sa.seq.slice();
        if (sa.concept && typeof sa.concept === "object") CONCEPT_ROWS.forEach(function (r) { if (CONCEPTS.indexOf(sa.concept[r.id]) !== -1) fa.concept[r.id] = sa.concept[r.id]; });
        if (Array.isArray(sa.caseSel)) fa.caseSel = sa.caseSel.filter(function (id) { return !!byId(CASE_OPTIONS, id); });
        if (byId(INFERENCE_OPTIONS, sa.infer)) fa.infer = sa.infer;
      }
    }
    state = fresh;
    completedOnce = !!(meta && meta.completed);
    render();
  }

  if (window.Lens) {
    window.Lens.onState(hydrate);
  } else {
    var saved = null;
    try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) { saved = null; }
    hydrate(saved, { completed: false });
  }
})();
</script>
</body>
</html>

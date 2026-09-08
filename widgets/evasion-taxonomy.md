---
id: '1da8db35-0313-4d6c-a7ab-8b63d50d0a19'
title: Evasion route explorer
summary_for_tutor: "An explorer for the ten-route evasion taxonomy, revisited with scores after the red-team exercise. Every route card carries XLab's own text: what the actor tries to do, the primary layers targeted and the actors who might participate. Seven routes (repurpose declared infrastructure, steal or copy model weights, split training across sites, falsify declarations or provenance, distill or extract capability, conceal the real actor, divert controlled hardware) also carry XLab's four scores out of 5 (technical feasibility for the evader, political and organizational feasibility, verification effectiveness where higher is better for the verifier, durability and harm), a rationale paragraph and the list of who can change the balance; three routes (hide an undeclared cluster, exploit a boundary in the rule, attack the verification system) are unscored because XLab's table never scored them. The learner filters routes by typing a layer or actor or tapping an actor chip, sorts by any score, opens cards to read the reasoning, switches to a score matrix, and adds up to three routes to a side-by-side comparison. The widget reports as complete once the learner has opened all seven scored routes. Push the learner to say why a score is what it is, using the rationale text, and to notice the pattern the sorts expose: the routes that are easiest for the evader (falsify, conceal) are only moderately verifiable, and weight theft is the route the compute-verification machinery sees least."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Evasion route explorer</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "evasion-taxonomy". Data: the ten-route table from covert-taxonomy.mdx (unit 3.1.1) and the seven scored routes from Section B of covert-red-blue.mdx (unit 3.2), both at commit cbd2f3ee (the parent of a10955c, which deleted them). XLab had no widget for this material; the explorer is a Lens addition over XLab's own text. -->
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
  h1, h2, h3 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 24px; margin: 4px 0 6px; }
  h3 { font-size: 17px; }
  p { margin: 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .lede { color: var(--muted); max-width: 46rem; margin-bottom: 12px; }
  .legend { font-size: 12px; color: var(--muted); border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 8px 12px; margin-bottom: 14px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 6px 10px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  select, input[type=search] { font: inherit; color: inherit; background: #fff; border: 1px solid var(--border); border-radius: 8px; padding: 6px 10px; }
  select:focus, input:focus { outline: 2px solid var(--accent); outline-offset: 1px; }
  .controls { display: flex; flex-wrap: wrap; gap: 8px 12px; align-items: center; margin-bottom: 10px; }
  .controls label { font-size: 12px; font-weight: 600; display: inline-flex; gap: 6px; align-items: center; }
  .controls input[type=search] { min-width: 14rem; flex: 1 1 14rem; }
  .chips { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; margin-bottom: 12px; }
  .chips .lbl { font-size: 12px; color: var(--muted); margin-right: 4px; }
  .chip { font-size: 12px; padding: 3px 9px; border-radius: 999px; }
  .status { font-size: 12px; color: var(--muted); margin-bottom: 10px; display: flex; flex-wrap: wrap; gap: 8px 14px; align-items: center; }
  .status .done { color: var(--accent); font-weight: 600; }
  .list { display: grid; gap: 10px; }
  .card { border: 1px solid var(--border); border-radius: 8px; background: #fff; }
  .card.is-open { border-color: var(--text); }
  .card.is-compared { box-shadow: inset 4px 0 0 var(--accent); }
  .head { display: flex; gap: 10px; align-items: flex-start; padding: 12px 14px; }
  .toggle { flex: 1 1 auto; text-align: left; border: 0; background: transparent; padding: 0; border-radius: 0; }
  .toggle:hover { background: transparent; }
  .toggle .name { font-family: var(--font-heading); font-weight: 600; font-size: 17px; display: block; }
  .toggle .what { display: block; color: var(--muted); font-size: 13px; margin-top: 2px; }
  .toggle .caret { display: inline-block; width: 1em; color: var(--muted); }
  .seen { font-size: 11px; color: var(--accent); font-weight: 600; margin-left: 6px; }
  .cmp { flex: 0 0 auto; font-size: 12px; white-space: nowrap; }
  .cmp.is-active { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); color: var(--accent-hover); }
  .scores { display: grid; grid-template-columns: repeat(4, minmax(0, 1fr)); gap: 6px; padding: 0 14px 12px; }
  .score { border: 1px solid var(--border); border-radius: 6px; padding: 6px 8px; background: var(--surface); }
  .score .k { font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); display: block; line-height: 1.3; }
  .score .v { font-weight: 600; display: block; margin-top: 2px; }
  .bar { height: 5px; background: var(--border); border-radius: 3px; margin-top: 5px; overflow: hidden; }
  .bar span { display: block; height: 100%; background: var(--accent); }
  .unscored { padding: 0 14px 12px; font-size: 12px; color: var(--muted); }
  .detail { display: none; border-top: 1px solid var(--border); padding: 12px 14px 14px; }
  .card.is-open .detail { display: block; }
  .detail dl { margin: 0; display: grid; grid-template-columns: max-content 1fr; gap: 4px 12px; font-size: 13px; }
  .detail dt { font-weight: 600; }
  .detail dd { margin: 0; }
  .detail .sb { margin-top: 12px; padding-top: 10px; border-top: 1px dashed var(--border); }
  .detail .sb h4 { font-family: var(--font-heading); font-weight: 600; font-size: 15px; margin: 0 0 8px; }
  .cells { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 8px; margin-bottom: 10px; }
  .cell { border: 1px solid var(--border); border-radius: 6px; padding: 8px 10px; font-size: 13px; }
  .cell .k { font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); display: block; }
  .cell .v { font-weight: 600; }
  .why { font-size: 13px; margin-bottom: 8px; }
  .who { font-size: 13px; color: var(--muted); }
  .who em { color: var(--text); }
  .box { overflow-x: auto; border: 1px solid var(--border); border-radius: 8px; background: #fff; }
  table { border-collapse: collapse; width: 100%; font-size: 13px; min-width: 32rem; }
  th, td { border-bottom: 1px solid var(--border); padding: 8px 10px; text-align: left; vertical-align: top; }
  th { font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); font-weight: 600; background: var(--surface); }
  tr:last-child td { border-bottom: 0; }
  td.n { font-weight: 600; white-space: nowrap; }
  td.s1 { background: #fdf9f3; } td.s2 { background: #faf0e2; } td.s3 { background: #f4e2c8; } td.s4 { background: #ecd0a6; } td.s5 { background: #e2bc82; }
  .rowbtn { border: 0; background: transparent; padding: 0; text-align: left; font-weight: 600; font-family: var(--font-heading); font-size: 15px; }
  .rowbtn:hover { color: var(--accent-hover); background: transparent; }
  .compare { margin: 0 0 14px; border: 1px solid var(--accent); border-radius: 8px; padding: 12px 14px; background: #fff; }
  .compare h2 { font-size: 18px; margin-bottom: 4px; }
  .compare .hint { font-size: 12px; color: var(--muted); margin-bottom: 8px; }
  .compare table { min-width: 36rem; }
  .compare td.c { min-width: 12rem; }
  .compare .sc { font-weight: 600; display: block; }
  .compare .row { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 8px; }
  .empty { padding: 14px; color: var(--muted); border: 1px dashed var(--border); border-radius: 8px; }
  .hidden { display: none !important; }
  @media (max-width: 560px) {
    .scores { grid-template-columns: repeat(2, minmax(0, 1fr)); }
    .cells { grid-template-columns: 1fr; }
    .detail dl { grid-template-columns: 1fr; }
    .head { flex-wrap: wrap; }
  }
</style>
</head>
<body>
<p class="eyebrow">Section B: the taxonomy revisited</p>
<h1>Evasion route explorer</h1>
<p class="lede">Ten routes around an agreement, seven of them scored. Filter by a layer or an actor, sort by a score, open a route to read why it scores the way it does, and put up to three routes side by side.</p>
<p class="legend">Scoring: 1 = very low or weak; 2 = low; 3 = moderate; 4 = high; 5 = very high. For verification effectiveness, a higher score is better for the verifier.</p>

<div class="controls">
  <label for="q">Filter <input id="q" type="search" placeholder="type a layer or an actor, e.g. inspectors" aria-label="Filter routes by layer or actor"></label>
  <label for="sort">Sort by <select id="sort"></select></label>
  <span role="group" aria-label="View">
    <button type="button" id="view-list" class="is-active" aria-pressed="true">Cards</button>
    <button type="button" id="view-matrix" aria-pressed="false">Score matrix</button>
  </span>
</div>
<div class="chips" id="chips"></div>
<div class="status" id="status"></div>

<section class="compare hidden" id="compare" aria-live="polite"></section>

<div class="list" id="list"></div>
<div class="box hidden" id="matrix"></div>

<script>
  // Ten routes: covert-taxonomy.mdx at XLab commit cbd2f3ee (unit 3.1.1).
  var ROUTES = [
    { n: 1, name: "Conceal the real actor",
      what: "Use front companies, nominee owners, brokers, affiliates, borrowed accounts, or layered ownership so the apparent customer is not the true controller or beneficiary.",
      layers: "Identity checks; customer screening; procurement; payments; beneficial ownership",
      actors: "State agencies; firms; brokers; corporate-service providers; cloud customers; procurement staff" },
    { n: 2, name: "Divert controlled hardware",
      what: "Obtain chips or servers through false end-user information, transshipment, misclassification, relabeling, theft, straw buyers, or unauthorized rerouting.",
      layers: "Semiconductor supply chain; customs; export controls; chain of custody",
      actors: "Buyers; distributors; freight forwarders; customs brokers; straw purchasers; supplier insiders" },
    { n: 3, name: "Hide an undeclared cluster or facility",
      what: "Operate equipment that was never declared, conceal additions inside a known facility, or rely on legacy or otherwise unregistered hardware.",
      layers: "Facility declarations; chip registries; power and construction monitoring; inspections",
      actors: "Data-center operators; facilities staff; suppliers; utilities; security personnel; public officials" },
    { n: 4, name: "Split the operation across sites",
      what: "Divide one development project among multiple smaller clusters so that no individual site appears to cross a monitoring or registration threshold.",
      layers: "Cluster definitions; networking; hardware registration; distributed operations",
      actors: "Researchers; infrastructure engineers; network operators; hardware owners; site technicians" },
    { n: 5, name: "Repurpose legitimate infrastructure",
      what: "Use a known, authorized cluster for an unauthorized purpose, for example, report training as inference or present prohibited capability work as safety, maintenance, civilian, or defensive research.",
      layers: "Workload declarations; scheduler and cloud logs; research oversight; code and data review",
      actors: "Frontier developers; cloud customers; military or intelligence units; infrastructure staff; project managers" },
    { n: 6, name: "Falsify declarations or provenance",
      what: "Alter or invent records about chip locations, compute use, model origin, data, code, checkpoints, evaluations, or utilization.",
      layers: "Self-reporting; logs; audits; model and data provenance",
      actors: "Researchers; compliance staff; system administrators; executives; auditors; contractors" },
    { n: 7, name: "Steal or copy model weights",
      what: "Obtain weights or related artifacts through insider access, cyber intrusion, supply-chain compromise, physical access, or abuse of legitimate permissions.",
      layers: "Model security; identity and access management; cybersecurity; human layer",
      actors: "Employees; contractors; cyber operators; intelligence services; partner organizations" },
    { n: 8, name: "Distill or extract capability",
      what: "Query a model and train a new model to imitate parts of its behavior. This can transfer useful capability without reproducing the teacher model’s exact weights.",
      layers: "APIs; account identity; query monitoring; downstream training",
      actors: "API customers; proxy account networks; model developers; data and training teams" },
    { n: 9, name: "Exploit a boundary in the rule",
      what: "Remain formally below a compute, hardware, or reporting threshold while using better algorithms, data, architecture, post-training, inference-time compute, or combinations of smaller activities to reach the policy-relevant result.",
      layers: "Definitions; thresholds; exemptions; measurement rules",
      actors: "Researchers; developers; lawyers; policymakers; standards bodies" },
    { n: 10, name: "Attack the verification system",
      what: "Spoof or disable monitoring, compromise attestation, tamper with sensors or logs, corrupt or coerce personnel, suppress reports, or flood investigators with misleading signals.",
      layers: "Hardware root of trust; monitoring devices; evidence systems; inspectors; reporting channels",
      actors: "Security engineers; hardware specialists; insiders; inspectors; officials; cyber operators" }
  ];

  var CRITERIA = [
    { key: "tech", label: "Technical feasibility for evader", short: "Technical feasibility" },
    { key: "org", label: "Political / organizational feasibility", short: "Political / organizational" },
    { key: "ver", label: "Verification effectiveness", short: "Verification effectiveness" },
    { key: "dur", label: "Durability / harm", short: "Durability / harm" }
  ];

  // Seven scored routes: Section B of covert-red-blue.mdx at XLab commit cbd2f3ee (unit 3.2), in XLab's order.
  var SCORED = [
    { n: 5, heading: "Repurpose declared infrastructure",
      tech: [4, "High", "The hardware, staff, and site already exist."],
      org: [4, "High", "A small number of authorized insiders may be enough."],
      ver: [3, "Moderate", "Logs and telemetry help, but purpose and intent are difficult to infer."],
      dur: [5, "Very high", "Standing capacity can support repeated activity."],
      why: "Often the most realistic route for an actor that already controls major compute. Legitimate activity provides cover: training can be labeled as inference, or prohibited capability work as safety or maintenance. Broad workload telemetry can produce useful signals, but proving the exact research purpose requires clear rules plus access to raw scheduler records, code, data, checkpoints, and personnel evidence.",
      who: "Developers; cloud providers; national regulators; inspectors; hardware and standards bodies" },
    { n: 7, heading: "Steal or copy model weights",
      tech: [3, "Moderate", "Requires insider access or a serious cyber compromise."],
      org: [3, "Moderate", "Can be done by a small team, but access and confidentiality are demanding."],
      ver: [2, "Low", "There may be no new large training signal."],
      dur: [5, "Very high", "One successful copy can be duplicated and reused."],
      why: "Weight theft changes the verification problem: the actor may acquire a powerful model without recreating its original training run. Access logs, segmentation, data-loss controls, and human reporting can help, but attribution and proof of what was copied are difficult. Compression research may reduce exfiltration time, but exfiltration remains a multistep attack. A compute-only agreement does not close this route.",
      who: "Frontier developers; cloud providers; security teams; national regulators; law enforcement" },
    { n: 4, heading: "Split training across sites",
      tech: [2, "Low today", "Low-communication methods are improving, but frontier-scale cases remain extrapolative."],
      org: [2, "Low", "Many sites, operators, and coordination points increase exposure."],
      ver: [2, "Low", "Single-site thresholds and local power signals may miss the whole operation."],
      dur: [3, "Moderate", "Repeatable in principle, but inefficient and operationally fragile."],
      why: "Recent work makes it unsafe to assume that all frontier training must occur inside one tightly connected facility. However, the largest governance-relevant scenarios are modeled rather than directly demonstrated. Distribution reduces the value of site-level thresholds while increasing procurement, accounting, staffing, networking, and whistleblower surfaces. Treat this as an emerging and uncertain route, not a solved capability.",
      who: "Treaty designers; chip and cloud regulators; intelligence agencies; inspectors; hardware owners" },
    { n: 6, heading: "Falsify declarations or provenance",
      tech: [5, "Very high", "Documents and curated logs are easy to alter when the actor controls them."],
      org: [4, "High", "Requires control of records and cooperation or silence from relevant staff."],
      ver: [3, "Moderate", "Independent records and cross-checks can expose contradictions."],
      dur: [3, "Moderate", "One false record may cover one run; a captured system can conceal repeated activity."],
      why: "False reporting is usually a supporting tactic rather than a complete development strategy. It becomes less effective when records are generated automatically, preserved outside the actor’s control, and compared with procurement, power, cloud, chip, code, checkpoint, and human evidence. Verification must test both whether declared activity occurred as claimed and whether important activity was omitted.",
      who: "Cloud and hardware providers; developers; auditors; inspectors; regulators" },
    { n: 8, heading: "Distill or extract capability",
      tech: [3, "Moderate", "Depends on model access, query budget, data, student compute, and output richness."],
      org: [4, "High", "May require no insider and can use proxy accounts or intermediaries."],
      ver: [3, "Moderate", "Providers can monitor access, but defenses are emerging and threat-model dependent."],
      dur: [3, "Moderate", "A student model can spread, but may not reproduce all teacher capabilities."],
      why: "Distillation is not the same as weight theft. It trains a new model to imitate behaviors exposed through an interface; it does not recover the teacher’s exact parameters. Providers can use identity checks, rate limits, anomaly detection, output design, fingerprinting, or watermarking, but recent research finds that defense performance depends heavily on attacker assumptions and can trade off against service quality.",
      who: "API providers; model developers; regulators; identity and payment providers" },
    { n: 1, heading: "Conceal the real actor",
      tech: [5, "Very high", "Shell companies, nominees, and borrowed accounts are cheap to create."],
      org: [4, "High", "Cross-border finance and ownership chains require coordination but are well established."],
      ver: [3, "Moderate", "Ownership, payment, address, communications, and logistics links can expose networks."],
      dur: [4, "High", "A proxy network can support repeated purchases and replace exposed entities."],
      why: "Proxy organizations are a high-feasibility enabling tactic, not a substitute for chips, power, engineering, or a viable workload. The A.Q. Khan network demonstrates how distributed intermediaries and front companies can route around supplier controls and exploit jurisdictional seams. Beneficial-ownership and reseller-chain analysis should therefore examine linked entities, not each nominal customer in isolation.",
      who: "Cloud and compute providers; exporters; financial institutions; corporate registries; regulators" },
    { n: 2, heading: "Divert controlled hardware",
      tech: [3, "Moderate", "False documents and transshipment are feasible; covert frontier-scale accumulation is harder."],
      org: [3, "Moderate", "Requires brokers, logistics, financing, and cross-border concealment."],
      ver: [3, "Moderate", "Customs, finance, supplier records, serials, and inspections create leads."],
      dur: [4, "High", "Individual shipments are episodic, but acquired hardware and networks can persist."],
      why: "Recent U.S. cases allege front companies, false paperwork, dummy servers, and transshipment through third countries to divert controlled AI hardware. These cases show realistic tactics, not proven prevalence; charging documents are allegations unless and until established in court. Acquiring chips is only one step: the actor must still power, cool, network, maintain, and use them.",
      who: "Vendors; distributors; customs; export-control agencies; freight and financial institutions" }
  ];

  var SORTS = [
    { key: "sectionb", label: "Section B order" },
    { key: "number", label: "Route number" },
    { key: "tech", label: "Technical feasibility for evader (high first)" },
    { key: "org", label: "Political / organizational feasibility (high first)" },
    { key: "ver", label: "Verification effectiveness (high first)" },
    { key: "dur", label: "Durability / harm (high first)" }
  ];
  var MAX_COMPARE = 3;
  var STORAGE_KEY = "lens-evasion-taxonomy";

  var scoredByN = {};
  SCORED.forEach(function (s, i) { s.order = i; scoredByN[s.n] = s; });
  var routeByN = {};
  ROUTES.forEach(function (r) { routeByN[r.n] = r; });

  var state = { q: "", actor: "", sort: "sectionb", view: "list", open: [], compare: [], seen: [] };
  var completed = false;

  var listEl = document.getElementById("list");
  var matrixEl = document.getElementById("matrix");
  var compareEl = document.getElementById("compare");
  var chipsEl = document.getElementById("chips");
  var statusEl = document.getElementById("status");
  var qEl = document.getElementById("q");
  var sortEl = document.getElementById("sort");
  var viewListBtn = document.getElementById("view-list");
  var viewMatrixBtn = document.getElementById("view-matrix");

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function has(arr, v) { return arr.indexOf(v) !== -1; }
  function tokens(str) { return str.split(";").map(function (t) { return t.trim(); }).filter(Boolean); }
  function norm(s) { return s.charAt(0).toLowerCase() + s.slice(1); }

  // The exact actor tokens a route carries, from its own actor list and its score row.
  function routeActors(r) {
    var set = {};
    tokens(r.actors).forEach(function (t) { set[norm(t)] = true; });
    var s = scoredByN[r.n];
    if (s) tokens(s.who).forEach(function (t) { set[norm(t)] = true; });
    return set;
  }

  // Actor chips: the actor names that recur across the most routes, computed from the data.
  function actorChips() {
    var counts = {};
    ROUTES.forEach(function (r) {
      Object.keys(routeActors(r)).forEach(function (k) { counts[k] = (counts[k] || 0) + 1; });
    });
    return Object.keys(counts).filter(function (k) { return counts[k] >= 3; })
      .sort(function (a, b) { return counts[b] - counts[a] || a.localeCompare(b); }).slice(0, 8)
      .map(function (k) { return { text: k, count: counts[k] }; });
  }

  // A chip is an exact actor filter, over the same tokens the chip count was computed from.
  // The text box stays a substring search across name, layers, actors and who.
  function matches(r) {
    if (state.actor && !Object.prototype.hasOwnProperty.call(routeActors(r), state.actor)) return false;
    var q = state.q.trim().toLowerCase();
    if (!q) return true;
    var s = scoredByN[r.n];
    var hay = [r.name, r.layers, r.actors, s ? s.who : ""].join(" | ").toLowerCase();
    return hay.indexOf(q) !== -1;
  }

  function filterLabel() {
    var parts = [];
    if (state.actor) parts.push("actor “" + state.actor + "”");
    if (state.q.trim()) parts.push("“" + state.q.trim() + "”");
    return parts.join(" and ");
  }

  function sorted(routes) {
    var key = state.sort;
    return routes.slice().sort(function (a, b) {
      var sa = scoredByN[a.n], sb = scoredByN[b.n];
      if (key === "number") return a.n - b.n;
      if (key === "sectionb") {
        if (sa && sb) return sa.order - sb.order;
        if (sa) return -1;
        if (sb) return 1;
        return a.n - b.n;
      }
      var va = sa ? sa[key][0] : -1, vb = sb ? sb[key][0] : -1;
      if (va !== vb) return vb - va;
      if (sa && sb) return sa.order - sb.order;
      return a.n - b.n;
    });
  }

  function visibleRoutes() { return sorted(ROUTES.filter(matches)); }

  function summary() {
    var vis = visibleRoutes();
    var lines = [];
    lines.push("Evasion route explorer (Section B). View: " + (state.view === "matrix" ? "score matrix" : "route cards") +
      ", sorted by " + SORTS.filter(function (s) { return s.key === state.sort; })[0].label.replace(" (high first)", "") + ".");
    lines.push(filterLabel() ? "Filter " + filterLabel() + ": " + vis.length + " of 10 routes shown (" + vis.map(function (r) { return r.n + ". " + r.name; }).join("; ") + ")." : "No filter; all 10 routes shown.");
    lines.push("Routes opened so far: " + (state.seen.length ? state.seen.slice().sort(function (a, b) { return a - b; }).map(function (n) { return n + ". " + routeByN[n].name; }).join("; ") : "none") +
      " (" + SCORED.filter(function (s) { return has(state.seen, s.n); }).length + " of 7 scored routes).");
    if (state.compare.length) {
      lines.push("Comparing: " + state.compare.map(function (n) {
        var s = scoredByN[n];
        return n + ". " + routeByN[n].name + (s ? " (technical " + s.tech[0] + "/5, political/organizational " + s.org[0] + "/5, verification " + s.ver[0] + "/5, durability " + s.dur[0] + "/5)" : " (unscored)");
      }).join("; ") + ".");
    }
    return lines.join(" ");
  }

  function persist() {
    var allSeen = SCORED.every(function (s) { return has(state.seen, s.n); });
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (allSeen && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
      if (allSeen) completed = true;
    }
  }

  function toggleOpen(n) {
    if (has(state.open, n)) state.open = state.open.filter(function (x) { return x !== n; });
    else { state.open.push(n); if (!has(state.seen, n)) state.seen.push(n); }
    render(); persist();
  }
  function toggleCompare(n) {
    if (has(state.compare, n)) state.compare = state.compare.filter(function (x) { return x !== n; });
    else if (state.compare.length < MAX_COMPARE) state.compare.push(n);
    render(); persist();
  }
  function setFilter(q) { state.q = q; render(); persist(); }
  function setActor(a) { state.actor = a; render(); persist(); }

  function scoreBlock(s, key) {
    var c = CRITERIA.filter(function (x) { return x.key === key; })[0];
    var box = el("div", "score");
    box.appendChild(el("span", "k", c.short));
    box.appendChild(el("span", "v", s[key][0] + "/5 " + s[key][1]));
    var bar = el("div", "bar"); var fill = el("span"); fill.style.width = (s[key][0] * 20) + "%"; bar.appendChild(fill); box.appendChild(bar);
    return box;
  }

  function renderCard(r) {
    var s = scoredByN[r.n];
    var open = has(state.open, r.n), compared = has(state.compare, r.n), seen = has(state.seen, r.n);
    var card = el("article", "card" + (open ? " is-open" : "") + (compared ? " is-compared" : ""));
    var head = el("div", "head");
    var toggle = el("button", "toggle"); toggle.type = "button"; toggle.setAttribute("aria-expanded", open ? "true" : "false");
    var name = el("span", "name"); name.appendChild(el("span", "caret", open ? "▾" : "▸")); name.appendChild(document.createTextNode(r.n + ". " + r.name));
    if (seen) name.appendChild(el("span", "seen", "✓ read"));
    toggle.appendChild(name);
    toggle.appendChild(el("span", "what", r.what));
    toggle.addEventListener("click", function () { toggleOpen(r.n); });
    head.appendChild(toggle);
    var cmp = el("button", "cmp" + (compared ? " is-active" : ""), compared ? "✓ Comparing" : "Compare"); cmp.type = "button";
    cmp.setAttribute("aria-pressed", compared ? "true" : "false");
    cmp.disabled = !compared && state.compare.length >= MAX_COMPARE;
    cmp.addEventListener("click", function () { toggleCompare(r.n); });
    head.appendChild(cmp);
    card.appendChild(head);

    if (s) {
      var sc = el("div", "scores");
      CRITERIA.forEach(function (c) { sc.appendChild(scoreBlock(s, c.key)); });
      card.appendChild(sc);
    } else {
      card.appendChild(el("p", "unscored", "Not scored: XLab’s Section B table scores seven of the ten routes, and this is one of the three it leaves out."));
    }

    var detail = el("div", "detail");
    var dl = el("dl");
    dl.appendChild(el("dt", null, "What the actor tries to do")); dl.appendChild(el("dd", null, r.what));
    dl.appendChild(el("dt", null, "Primary layer(s) targeted")); dl.appendChild(el("dd", null, r.layers));
    dl.appendChild(el("dt", null, "Actors who might participate")); dl.appendChild(el("dd", null, r.actors));
    detail.appendChild(dl);
    if (s) {
      var sb = el("div", "sb");
      sb.appendChild(el("h4", null, "Scored in Section B as: " + s.heading));
      var cells = el("div", "cells");
      CRITERIA.forEach(function (c) {
        var cell = el("div", "cell");
        cell.appendChild(el("span", "k", c.label));
        cell.appendChild(el("span", "v", s[c.key][0] + "/5 " + s[c.key][1] + ". "));
        cell.appendChild(document.createTextNode(s[c.key][2]));
        cells.appendChild(cell);
      });
      sb.appendChild(cells);
      sb.appendChild(el("p", "why", s.why));
      var who = el("p", "who"); who.appendChild(el("em", null, "Who can change the balance: ")); who.appendChild(document.createTextNode(s.who));
      sb.appendChild(who);
      detail.appendChild(sb);
    }
    card.appendChild(detail);
    return card;
  }

  function renderList(vis) {
    listEl.textContent = "";
    if (!vis.length) { listEl.appendChild(el("p", "empty", "No route lists that layer or actor. Clear the filter to see all ten.")); return; }
    vis.forEach(function (r) { listEl.appendChild(renderCard(r)); });
  }

  function renderMatrix(vis) {
    matrixEl.textContent = "";
    var scoredVis = vis.filter(function (r) { return !!scoredByN[r.n]; });
    var table = el("table");
    var thead = el("thead"); var hr = el("tr");
    hr.appendChild(el("th", null, "Route"));
    CRITERIA.forEach(function (c) { hr.appendChild(el("th", null, c.label)); });
    thead.appendChild(hr); table.appendChild(thead);
    var tbody = el("tbody");
    scoredVis.forEach(function (r) {
      var s = scoredByN[r.n];
      var tr = el("tr");
      var td = el("td", "n");
      var b = el("button", "rowbtn", r.n + ". " + r.name); b.type = "button";
      b.setAttribute("aria-label", "Open route " + r.n + " in the cards view");
      b.addEventListener("click", function () { state.view = "list"; if (!has(state.open, r.n)) { state.open.push(r.n); if (!has(state.seen, r.n)) state.seen.push(r.n); } render(); persist(); });
      td.appendChild(b);
      if (has(state.seen, r.n)) td.appendChild(el("span", "seen", "✓ read"));
      tr.appendChild(td);
      CRITERIA.forEach(function (c) { tr.appendChild(el("td", "s" + s[c.key][0], s[c.key][0] + "/5 " + s[c.key][1])); });
      tbody.appendChild(tr);
    });
    var unscored = vis.filter(function (r) { return !scoredByN[r.n]; });
    if (unscored.length) {
      var tr2 = el("tr"); var td2 = el("td"); td2.colSpan = 5;
      td2.textContent = "Not scored in XLab’s table: " + unscored.map(function (r) { return r.n + ". " + r.name; }).join("; ") + ".";
      tr2.appendChild(td2); tbody.appendChild(tr2);
    }
    if (!scoredVis.length && !unscored.length) { var tr3 = el("tr"); var td3 = el("td"); td3.colSpan = 5; td3.textContent = "No route lists that layer or actor."; tr3.appendChild(td3); tbody.appendChild(tr3); }
    table.appendChild(tbody);
    matrixEl.appendChild(table);
  }

  function renderCompare() {
    compareEl.textContent = "";
    compareEl.classList.toggle("hidden", state.compare.length === 0);
    if (!state.compare.length) return;
    compareEl.appendChild(el("h2", null, "Side by side"));
    compareEl.appendChild(el("p", "hint", state.compare.length < 2 ? "Add one or two more routes with their Compare buttons." : "Scores out of 5, with XLab’s one-line reason for each."));
    var box = el("div", "box"); var table = el("table");
    var thead = el("thead"); var hr = el("tr"); hr.appendChild(el("th", null, ""));
    state.compare.forEach(function (n) { hr.appendChild(el("th", null, n + ". " + routeByN[n].name)); });
    thead.appendChild(hr); table.appendChild(thead);
    var tbody = el("tbody");
    var rowWhat = el("tr"); rowWhat.appendChild(el("th", null, "What the actor tries to do"));
    state.compare.forEach(function (n) { rowWhat.appendChild(el("td", "c", routeByN[n].what)); });
    tbody.appendChild(rowWhat);
    CRITERIA.forEach(function (c) {
      var tr = el("tr"); tr.appendChild(el("th", null, c.label));
      state.compare.forEach(function (n) {
        var s = scoredByN[n];
        var td = el("td", "c" + (s ? " s" + s[c.key][0] : ""));
        if (s) { td.appendChild(el("span", "sc", s[c.key][0] + "/5 " + s[c.key][1])); td.appendChild(document.createTextNode(s[c.key][2])); }
        else td.textContent = "Not scored";
        tr.appendChild(td);
      });
      tbody.appendChild(tr);
    });
    var rowWho = el("tr"); rowWho.appendChild(el("th", null, "Who can change the balance"));
    state.compare.forEach(function (n) { var s = scoredByN[n]; rowWho.appendChild(el("td", "c", s ? s.who : "Not scored")); });
    tbody.appendChild(rowWho);
    table.appendChild(tbody); box.appendChild(table); compareEl.appendChild(box);
    var row = el("div", "row");
    var clear = el("button", null, "Clear comparison"); clear.type = "button";
    clear.addEventListener("click", function () { state.compare = []; render(); persist(); });
    row.appendChild(clear); compareEl.appendChild(row);
  }

  function renderChips() {
    chipsEl.textContent = "";
    chipsEl.appendChild(el("span", "lbl", "Actors that recur:"));
    actorChips().forEach(function (c) {
      var active = state.actor === c.text;
      var b = el("button", "chip" + (active ? " is-active" : ""), (active ? "✓ " : "") + c.text + " (" + c.count + ")"); b.type = "button";
      b.setAttribute("aria-pressed", active ? "true" : "false");
      b.addEventListener("click", function () { setActor(active ? "" : c.text); });
      chipsEl.appendChild(b);
    });
  }

  function renderStatus(vis) {
    statusEl.textContent = "";
    statusEl.appendChild(el("span", null, vis.length + " of 10 routes shown" + (filterLabel() ? " for " + filterLabel() : "") + "."));
    var seenScored = SCORED.filter(function (s) { return has(state.seen, s.n); }).length;
    statusEl.appendChild(el("span", seenScored === SCORED.length ? "done" : "", seenScored === SCORED.length ? "✓ All seven scored routes read." : seenScored + " of 7 scored routes read."));
    if (filterLabel()) {
      var clr = el("button", "chip", "Clear filter"); clr.type = "button";
      clr.addEventListener("click", function () { qEl.value = ""; state.actor = ""; setFilter(""); });
      statusEl.appendChild(clr);
    }
  }

  function render() {
    var vis = visibleRoutes();
    if (qEl.value !== state.q) qEl.value = state.q;
    sortEl.value = state.sort;
    viewListBtn.className = state.view === "list" ? "is-active" : ""; viewListBtn.setAttribute("aria-pressed", state.view === "list" ? "true" : "false");
    viewMatrixBtn.className = state.view === "matrix" ? "is-active" : ""; viewMatrixBtn.setAttribute("aria-pressed", state.view === "matrix" ? "true" : "false");
    listEl.classList.toggle("hidden", state.view !== "list");
    matrixEl.classList.toggle("hidden", state.view !== "matrix");
    renderChips(); renderStatus(vis); renderCompare();
    if (state.view === "list") { matrixEl.textContent = ""; renderList(vis); } else { listEl.textContent = ""; renderMatrix(vis); }
  }

  SORTS.forEach(function (s) { var o = el("option", null, s.label); o.value = s.key; sortEl.appendChild(o); });
  sortEl.addEventListener("change", function () { state.sort = sortEl.value; render(); persist(); });
  qEl.addEventListener("input", function () { setFilter(qEl.value); });
  viewListBtn.addEventListener("click", function () { state.view = "list"; render(); persist(); });
  viewMatrixBtn.addEventListener("click", function () { state.view = "matrix"; render(); persist(); });

  function validN(v) { return typeof v === "number" && !!routeByN[v]; }
  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.q === "string") state.q = saved.q;
      if (typeof saved.actor === "string" && actorChips().some(function (c) { return c.text === saved.actor; })) state.actor = saved.actor;
      if (SORTS.some(function (s) { return s.key === saved.sort; })) state.sort = saved.sort;
      if (saved.view === "matrix" || saved.view === "list") state.view = saved.view;
      ["open", "compare", "seen"].forEach(function (k) {
        if (Array.isArray(saved[k])) state[k] = saved[k].filter(validN).filter(function (v, i, a) { return a.indexOf(v) === i; });
      });
      state.compare = state.compare.slice(0, MAX_COMPARE);
    }
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = localStorage.getItem(STORAGE_KEY); } catch (e) {}
    if (raw) { try { hydrate(JSON.parse(raw), null); } catch (e) {} }
  }
</script>
</body>
</html>

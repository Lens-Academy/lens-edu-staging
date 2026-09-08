---
id: 'd5827bfd-8f0f-406d-8628-efe03b3fe02a'
title: Five maps of the evidence
summary_for_tutor: "Five alternative taxonomies of the same twelve verification evidence mechanisms (on-chip attestation, compute metering, chip registry, cloud KYC, cloud compute accounting, satellite imagery, power-draw monitoring, signals intelligence, open-source intelligence, on-site inspections, staff interviews, whistleblower channels). The learner switches between five map tabs (by layer, by access, by goal, by lifecycle, by adversary); each map shows its organising question, its lineage, and the twelve mechanisms regrouped into that map's buckets (the lifecycle map has an empty After deployment bucket on purpose). Clicking a mechanism opens a panel with its description, its placement in the current map, and where the map strains for it; a toggle reveals what the map reveals and what it hides. The widget is complete once all five maps have been opened; there is no right answer to find. Content ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Five maps of the evidence</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "evidence-taxonomies". -->
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
  .frame { border: 1px solid var(--border); border-radius: 8px; overflow: hidden; background: var(--bg); }
  header { padding: 20px; border-bottom: 1px solid var(--border); }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .head-row { display: flex; flex-wrap: wrap; gap: 12px; align-items: flex-end; justify-content: space-between; margin-top: 8px; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 26px; line-height: 1.15; margin: 0; }
  .lede { color: var(--muted); margin: 8px 0 0; max-width: 42rem; }
  .tabs { display: flex; gap: 6px; padding: 8px; border-bottom: 1px solid var(--border); overflow-x: auto; }
  .tab {
    flex-shrink: 0; font: inherit; font-size: 12px; font-weight: 500; color: var(--muted);
    border: 1px solid transparent; border-radius: 8px; background: transparent; padding: 8px 12px; cursor: pointer;
  }
  .tab:hover { background: var(--surface); color: var(--text); }
  .tab:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .tab.is-active { background: var(--accent); border-color: var(--accent); color: #fff; }
  .tab.is-active:hover { background: var(--accent-hover); }
  .tab .mark { display: inline-block; width: 1em; }
  .body { display: grid; gap: 20px; padding: 16px; }
  @media (min-width: 900px) { .body { grid-template-columns: minmax(0, 1fr) 19rem; padding: 20px; } }
  .question { border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 14px 16px; }
  .question p { margin: 0; }
  .question .q { font-weight: 500; }
  .question .lineage { color: var(--muted); font-size: 12px; margin-top: 6px; }
  .groups { display: grid; gap: 12px; margin-top: 16px; }
  @media (min-width: 640px) { .groups { grid-template-columns: 1fr 1fr; } }
  .group { border: 1px solid var(--border); border-radius: 8px; padding: 14px; background: var(--bg); }
  .group-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 12px; }
  .group h2 { font-family: var(--font-heading); font-weight: 600; font-size: 17px; margin: 0; }
  .group .sub { color: var(--muted); font-size: 12px; margin: 2px 0 0; }
  .group .count { color: var(--muted); font-size: 11px; white-space: nowrap; }
  .chips { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 12px; }
  .chip {
    font: inherit; font-size: 12px; color: inherit; text-align: left;
    border: 1px solid var(--border); border-radius: 6px; background: var(--bg); padding: 6px 10px; cursor: pointer;
  }
  .chip:hover { background: var(--surface); }
  .chip:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .chip.is-selected { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); font-weight: 600; }
  .chip .mark { display: none; color: var(--accent); margin-right: 4px; }
  .chip.is-selected .mark { display: inline; }
  .empty { margin: 12px 0 0; padding: 12px; border: 1px dashed var(--border); border-radius: 6px; color: var(--muted); font-size: 12px; }
  aside { display: grid; gap: 12px; align-content: start; }
  .detail { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--bg); }
  .detail.placeholder { border-style: dashed; background: var(--surface); }
  .detail-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 12px; }
  .detail h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 4px 0 0; }
  .detail .desc { color: var(--muted); margin: 8px 0 0; }
  .detail .placement { border-top: 1px solid var(--border); margin-top: 14px; padding-top: 12px; }
  .detail .placement p { margin: 0; }
  .detail .placement .where { font-weight: 500; margin-top: 4px; }
  .friction { border: 1px solid var(--border); border-radius: 6px; background: var(--surface); padding: 12px; margin-top: 12px; }
  .friction p { margin: 0; }
  .friction .t { font-size: 12px; font-weight: 500; }
  .friction .b { color: var(--muted); font-size: 12px; margin-top: 4px; }
  .placeholder p { margin: 0; }
  .placeholder .t { font-weight: 500; }
  .placeholder .b { color: var(--muted); font-size: 12px; margin-top: 4px; }
  .close {
    font: inherit; border: 0; background: transparent; color: var(--muted);
    width: 28px; height: 28px; border-radius: 6px; cursor: pointer; font-size: 18px; line-height: 1; flex-shrink: 0;
  }
  .close:hover { background: var(--surface); color: var(--text); }
  .close:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .sl { border: 1px solid var(--border); border-radius: 8px; overflow: hidden; }
  .sl-toggle {
    width: 100%; font: inherit; font-size: 12px; font-weight: 500; color: inherit; text-align: left;
    border: 0; background: var(--bg); padding: 10px 12px; cursor: pointer; display: flex; justify-content: space-between; gap: 8px;
  }
  .sl-toggle:hover { background: var(--surface); }
  .sl-toggle:focus-visible { outline: 2px solid var(--text); outline-offset: -2px; }
  .sl-panel { display: none; border-top: 1px solid var(--border); padding: 12px; }
  .sl-panel.is-open { display: grid; gap: 12px; }
  .sl-panel ul { list-style: none; margin: 6px 0 0; padding: 0; }
  .sl-panel li { display: flex; gap: 8px; font-size: 12px; margin-top: 6px; }
  .sl-panel li .arrow { color: var(--muted); flex-shrink: 0; }
  .progress { padding: 10px 20px 14px; border-top: 1px solid var(--border); font-size: 12px; color: var(--muted); display: flex; flex-wrap: wrap; gap: 8px; justify-content: space-between; }
  .progress .done-mark { color: var(--accent); font-weight: 600; }
</style>
</head>
<body>
<section class="frame" aria-labelledby="et-title">
  <header>
    <p class="eyebrow">Evidence companion</p>
    <div class="head-row">
      <div>
        <h1 id="et-title">Five maps of the evidence</h1>
        <p class="lede">The same twelve mechanisms, sorted five ways. Switch maps, inspect a mechanism and argue with the placements.</p>
      </div>
      <p class="eyebrow">12 mechanisms · 5 maps</p>
    </div>
  </header>

  <div class="tabs" id="tabs" role="tablist" aria-label="Maps"></div>

  <div class="body">
    <div>
      <div class="question" id="question" role="tabpanel">
        <p class="q" id="map-question"></p>
        <p class="lineage" id="map-lineage"></p>
      </div>
      <div class="groups" id="groups"></div>
    </div>

    <aside>
      <div id="detail"></div>
      <div class="sl">
        <button type="button" class="sl-toggle" id="sl-toggle" aria-expanded="false" aria-controls="sl-panel">
          <span>Strengths and limits of this map</span>
          <span id="sl-mark" aria-hidden="true">+</span>
        </button>
        <div class="sl-panel" id="sl-panel">
          <div>
            <p class="eyebrow">What it reveals</p>
            <ul id="sl-strengths"></ul>
          </div>
          <div>
            <p class="eyebrow">What it hides</p>
            <ul id="sl-limits"></ul>
          </div>
        </div>
      </div>
    </aside>
  </div>

  <div class="progress">
    <span id="progress-text"></span>
    <span id="progress-done" class="done-mark" hidden>✓ All five maps opened</span>
  </div>
</section>

<script>
  var MECHANISMS = [
    { id: "attest", name: "On-chip attestation",
      description: "A chip signs statements about its identity and configuration, anchored in a hardware root of trust.",
      friction: "Attestation is only as good as its key, and the key sits in silicon the adversary may own. Commercial secure boot protects a machine's owner; verification asks it to catch the owner." },
    { id: "meter", name: "Compute metering",
      description: "Firmware keeps a tamper-evident total of how much computation an accelerator has performed.",
      friction: "The sensor is silicon, but metering only becomes evidence when someone collects and audits the totals. It also inherits attestation's owner-as-adversary problem." },
    { id: "registry", name: "Chip registry and supply-chain tracking",
      description: "A ledger of who holds which accelerators, updated at manufacture, sale and resale.",
      friction: "A registry is a database and a legal reporting duty, not a device. Everything that makes it work is institutional: customs enforcement, resale reporting and audit rights." },
    { id: "kyc", name: "Cloud KYC",
      description: "Providers verify customer identity and beneficial ownership before selling large amounts of compute.",
      friction: "The cooperation comes from companies under domestic law, not from a rival state under a treaty. It needs no consent from the target state, which makes it a poor fit for every access bucket." },
    { id: "accounting", name: "Cloud compute accounting",
      description: "Provider-side logs of which accounts ran how much compute, on what hardware.",
      friction: "Generated by hardware, held by a provider and disclosed under whatever legal regime applies. It serves nearly every policy goal and is the least stable placement in the deck." },
    { id: "satellite", name: "Satellite imagery",
      description: "Thermal signatures and construction footprints of data centers, visible from orbit.",
      friction: "Construction is visible before a run, heat during it, and neither reveals workloads. It is a two-stage sensor forced into one lifecycle bucket." },
    { id: "energy", name: "Power-draw monitoring",
      description: "Grid-level and facility-level electricity data used as a proxy for large training activity.",
      friction: "Grid-scale data can be gathered remotely. Facility-level metering needs host cooperation. One mechanism falls into two access buckets depending on the resolution required." },
    { id: "sigint", name: "Signals intelligence and cyber",
      description: "Intercepted communications and network intrusion run by state intelligence agencies.",
      friction: "Effective and unacknowledgeable. Intrusion can produce private confidence but rarely shareable proof without exposing sources and methods." },
    { id: "osint", name: "Open-source intelligence",
      description: "Procurement records, customs data, job postings, publications and financial filings." },
    { id: "inspect", name: "On-site inspections",
      description: "Negotiated visits to declared facilities, usually under managed-access rules.",
      friction: "Filed under human, but most of an inspector's work is reading hardware. The layer map sorts by who carries the evidence, not what the evidence is." },
    { id: "interview", name: "Staff interviews",
      description: "Structured questioning of researchers and engineers, typically during inspections." },
    { id: "whistle", name: "Whistleblower channels",
      description: "Protected routes for insiders to report violations, plus the machinery to corroborate reports.",
      friction: "They need no consent from the target state, but they do need protected channels and legal shelter negotiated in advance. States can also imprison whistleblowers, so the adversary grade is probabilistic." }
  ];

  var MAPS = [
    { key: "layer", label: "By layer",
      question: "Where does the evidence come from, and who controls the sensor?",
      lineage: "Written mostly by technical AI governance researchers for institution designers and engineers deciding who must build and operate each stream.",
      strengths: [
        "Maps onto real institutions: chipmakers, cloud providers, intelligence agencies and inspectorates.",
        "Makes redundancy reasoning natural: independent layers force an evader to attack several streams.",
        "Concrete to teach and staff; each layer is a profession."
      ],
      limits: [
        "Mechanisms straddle layers: compute accounting is hardware telemetry read through a cloud provider.",
        "It is silent on political cost: unilateral espionage and negotiated access sit side by side.",
        "Layers can look independent while sharing the same upstream firms."
      ],
      groups: [
        { name: "Hardware", sub: "the silicon itself", ids: ["attest", "meter", "registry"] },
        { name: "Cloud", sub: "the provider layer", ids: ["kyc", "accounting"] },
        { name: "Intelligence", sub: "what a state can see uninvited", ids: ["satellite", "energy", "sigint", "osint"] },
        { name: "Human", sub: "people who know things", ids: ["inspect", "interview", "whistle"] }
      ] },
    { key: "access", label: "By access",
      question: "What must the target concede before this evidence can exist?",
      lineage: "The arms-control tradition of IAEA safeguards and the CWC, written for negotiators deciding what a treaty can actually demand. Wasil et al. (2024) is the clearest AI example.",
      strengths: [
        "Prices sovereignty directly: what each stream costs to obtain and what works before an agreement exists.",
        "Sequences the regime: unilateral streams work now, treaty access comes later, hardware takes years.",
        "Inherits tested legal language around managed access and non-interference."
      ],
      limits: [
        "Access is a spectrum, not three buckets.",
        "Categories drift as technology moves; a site visit today may become a remote proof.",
        "It says nothing about what the evidence proves, only how hard it is to get."
      ],
      groups: [
        { name: "National technical means", sub: "no cooperation needed", ids: ["satellite", "energy", "sigint", "osint", "whistle"] },
        { name: "Negotiated access", sub: "the target must agree", ids: ["inspect", "interview", "accounting", "kyc"] },
        { name: "Pre-installed governance tech", sub: "built in years ahead", ids: ["attest", "meter", "registry"] }
      ] },
    { key: "goal", label: "By goal",
      question: "Which claim in the agreement is this evidence supposed to check?",
      lineage: "Written by policy analysts working backward from a proposed rule. Scher and Thiergart (2024) start from the agreement and ask what could verify it.",
      strengths: [
        "Starts where policymakers start: with the rule.",
        "Exposes coverage gaps per clause.",
        "Forces the question: verify what, exactly, and against whom?"
      ],
      limits: [
        "The same mechanism reappears under several goals, so the map duplicates instead of partitions.",
        "It redraws whenever the policy menu changes.",
        "It hides shared infrastructure and single points of failure."
      ],
      groups: [
        { name: "Detect covert training runs", sub: "find what was never declared", ids: ["satellite", "energy", "sigint", "osint", "whistle", "meter"] },
        { name: "Verify declared runs comply", sub: "check what was admitted to", ids: ["attest", "meter", "accounting", "inspect", "interview"] },
        { name: "Track where the chips are", sub: "account for the stock", ids: ["registry", "kyc", "osint", "inspect"] }
      ] },
    { key: "lifecycle", label: "By lifecycle",
      question: "When in the life of a model does the evidence attach?",
      lineage: "Compute-governance research for engineers and regulators deciding where in the pipeline to attach controls, including Shavit (2023) and Sastry, Heim et al. (2024).",
      strengths: [
        "Shows which evidence must be captured live because it cannot be recovered later.",
        "Sequences enforcement by cost: acquisition is cheaper to catch than a live run.",
        "Each stage is a distinct engineering surface."
      ],
      limits: [
        "Assumes the current pipeline shape of giant pretraining runs on registered accelerators.",
        "Human and intelligence streams watch institutions, not pipeline stages.",
        "The empty deployment column is an honest gap the map cannot fix."
      ],
      groups: [
        { name: "Before a run", sub: "chips made, sold and moved", ids: ["registry", "kyc"] },
        { name: "During a run", sub: "while the compute burns", ids: ["attest", "meter", "accounting", "energy", "satellite"] },
        { name: "After deployment", sub: "models loose in the world", ids: [], empty: "None of the twelve. Third-party evaluations, incident reporting and observing outputs are a toolkit this deck barely touches. Noticing the empty column is the point." },
        { name: "Any stage", sub: "watching people, not pipelines", ids: ["osint", "sigint", "inspect", "interview", "whistle"] }
      ] },
    { key: "adversary", label: "By adversary",
      question: "Who is this evidence still good against?",
      lineage: "Arms-control practice separates monitoring a partner from catching a determined cheat; security researchers apply the same owner-as-adversary test to AI mechanisms.",
      strengths: [
        "Grades strength, not just kind.",
        "Forces the threat model onto every card.",
        "Exposes the commercial-security trap: tools built to protect the owner are asked to catch the owner."
      ],
      limits: [
        "Robustness is a spectrum pretending to be three buckets.",
        "Read carelessly, it breeds nihilism; combinations of streams can survive where single streams do not.",
        "It says nothing about cost, legality or who operates the stream."
      ],
      groups: [
        { name: "Cooperative target", sub: "verifies good faith, not bad", ids: ["inspect", "interview"] },
        { name: "Cheating company", sub: "assumes functioning states above it", ids: ["attest", "meter", "registry", "kyc", "accounting"] },
        { name: "Evading state", sub: "no consent, no permission", ids: ["satellite", "energy", "sigint", "osint", "whistle"] }
      ] }
  ];

  var STORAGE_KEY = "lens-widget-evidence-taxonomies";
  var state = { map: "layer", selected: null, viewed: ["layer"], inspected: [] };
  var slOpen = false;
  var completed = false;

  var tabsEl = document.getElementById("tabs");
  var groupsEl = document.getElementById("groups");
  var detailEl = document.getElementById("detail");
  var slToggle = document.getElementById("sl-toggle");
  var slPanel = document.getElementById("sl-panel");
  var slMark = document.getElementById("sl-mark");

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function mapByKey(key) { for (var i = 0; i < MAPS.length; i++) if (MAPS[i].key === key) return MAPS[i]; return MAPS[0]; }
  function mechById(id) { for (var i = 0; i < MECHANISMS.length; i++) if (MECHANISMS[i].id === id) return MECHANISMS[i]; return null; }
  function addUnique(list, v) { if (list.indexOf(v) === -1) list.push(v); }
  function placementNames(map, id) {
    var names = [];
    map.groups.forEach(function (g) { if (g.ids.indexOf(id) !== -1) names.push(g.name); });
    return names;
  }

  function summary() {
    var map = mapByKey(state.map);
    var viewedLabels = state.viewed.map(function (k) { return mapByKey(k).label; });
    var text = "Map open: " + map.label + " (" + map.question + "). Maps viewed so far: " + state.viewed.length + " of 5 (" + viewedLabels.join(", ") + ").";
    var mech = state.selected ? mechById(state.selected) : null;
    if (mech) {
      text += " Mechanism selected: " + mech.name + ", placed under " + placementNames(map, mech.id).join(" and ") + " on this map." + (mech.friction ? " Where the map strains: " + mech.friction : "");
    } else {
      text += " No mechanism selected.";
    }
    if (state.inspected.length) {
      text += " Mechanisms inspected so far: " + state.inspected.map(function (id) { var m = mechById(id); return m ? m.name : id; }).join(", ") + ".";
    }
    if (state.viewed.length === 5) text += " All five maps have been opened.";
    return text;
  }

  function persist() {
    var snapshot = { map: state.map, selected: state.selected, viewed: state.viewed.slice(), inspected: state.inspected.slice() };
    if (window.Lens) {
      Lens.saveState(snapshot, summary());
      if (!completed && state.viewed.length === MAPS.length) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snapshot)); } catch (e) { /* storage unavailable */ }
      if (state.viewed.length === MAPS.length) completed = true;
    }
  }

  MAPS.forEach(function (map) {
    var b = el("button", "tab");
    b.type = "button";
    b.setAttribute("role", "tab");
    b.dataset.key = map.key;
    b.appendChild(el("span", "mark", ""));
    b.appendChild(el("span", null, map.label));
    b.addEventListener("click", function () {
      state.map = map.key;
      addUnique(state.viewed, map.key);
      render();
      persist();
    });
    tabsEl.appendChild(b);
  });

  slToggle.addEventListener("click", function () {
    slOpen = !slOpen;
    renderStrengths();
  });

  function renderStrengths() {
    var map = mapByKey(state.map);
    slToggle.setAttribute("aria-expanded", slOpen ? "true" : "false");
    slMark.textContent = slOpen ? "−" : "+";
    slPanel.classList.toggle("is-open", slOpen);
    var s = document.getElementById("sl-strengths");
    var l = document.getElementById("sl-limits");
    s.textContent = ""; l.textContent = "";
    map.strengths.forEach(function (t) { var li = el("li"); li.appendChild(el("span", "arrow", "→")); li.appendChild(el("span", null, t)); s.appendChild(li); });
    map.limits.forEach(function (t) { var li = el("li"); li.appendChild(el("span", "arrow", "→")); li.appendChild(el("span", null, t)); l.appendChild(li); });
  }

  function renderDetail() {
    var map = mapByKey(state.map);
    var mech = state.selected ? mechById(state.selected) : null;
    detailEl.textContent = "";
    if (!mech) {
      var ph = el("div", "detail placeholder");
      ph.appendChild(el("p", "t", "Inspect a placement"));
      ph.appendChild(el("p", "b", "Select any mechanism to see what it establishes and where this taxonomy starts to strain."));
      detailEl.appendChild(ph);
      return;
    }
    var card = el("div", "detail");
    card.setAttribute("role", "region");
    card.setAttribute("aria-live", "polite");
    var top = el("div", "detail-top");
    top.appendChild(el("p", "eyebrow", "Mechanism"));
    var close = el("button", "close", "×");
    close.type = "button";
    close.id = "close-detail";
    close.setAttribute("aria-label", "Close mechanism detail");
    close.addEventListener("click", function () { state.selected = null; render(); persist(); });
    top.appendChild(close);
    card.appendChild(top);
    card.appendChild(el("h2", null, mech.name));
    card.appendChild(el("p", "desc", mech.description));
    var pl = el("div", "placement");
    pl.appendChild(el("p", "eyebrow", "Placement in this map"));
    pl.appendChild(el("p", "where", placementNames(map, mech.id).join(" · ")));
    card.appendChild(pl);
    if (mech.friction) {
      var fr = el("div", "friction");
      fr.appendChild(el("p", "t", "Where the map strains"));
      fr.appendChild(el("p", "b", mech.friction));
      card.appendChild(fr);
    }
    detailEl.appendChild(card);
  }

  function render() {
    var map = mapByKey(state.map);
    var tabs = tabsEl.querySelectorAll(".tab");
    for (var i = 0; i < tabs.length; i++) {
      var key = tabs[i].dataset.key;
      var active = key === state.map;
      tabs[i].classList.toggle("is-active", active);
      tabs[i].setAttribute("aria-selected", active ? "true" : "false");
      tabs[i].querySelector(".mark").textContent = state.viewed.indexOf(key) !== -1 ? "✓" : "";
    }
    document.getElementById("map-question").textContent = map.question;
    document.getElementById("map-lineage").textContent = map.lineage;

    groupsEl.textContent = "";
    map.groups.forEach(function (group) {
      var sec = el("section", "group");
      var top = el("div", "group-top");
      var head = el("div");
      head.appendChild(el("h2", null, group.name));
      head.appendChild(el("p", "sub", group.sub));
      top.appendChild(head);
      top.appendChild(el("span", "count", group.ids.length + (group.ids.length === 1 ? " mechanism" : " mechanisms")));
      sec.appendChild(top);
      if (group.ids.length) {
        var chips = el("div", "chips");
        group.ids.forEach(function (id) {
          var mech = mechById(id);
          var on = state.selected === id;
          var b = el("button", "chip" + (on ? " is-selected" : ""));
          b.type = "button";
          b.setAttribute("aria-pressed", on ? "true" : "false");
          b.appendChild(el("span", "mark", "✓"));
          b.appendChild(el("span", null, mech.name));
          b.addEventListener("click", function () {
            state.selected = state.selected === id ? null : id;
            if (state.selected) addUnique(state.inspected, id);
            render();
            persist();
          });
          chips.appendChild(b);
        });
        sec.appendChild(chips);
      } else {
        sec.appendChild(el("p", "empty", group.empty));
      }
      groupsEl.appendChild(sec);
    });

    renderDetail();
    renderStrengths();

    document.getElementById("progress-text").textContent = "Maps opened: " + state.viewed.length + " of " + MAPS.length;
    document.getElementById("progress-done").hidden = state.viewed.length < MAPS.length;
  }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (typeof saved.map === "string" && mapByKey(saved.map).key === saved.map) state.map = saved.map;
      if (typeof saved.selected === "string" && mechById(saved.selected)) state.selected = saved.selected;
      if (Array.isArray(saved.viewed)) {
        state.viewed = [];
        saved.viewed.forEach(function (k) { if (typeof k === "string" && mapByKey(k).key === k) addUnique(state.viewed, k); });
      }
      if (Array.isArray(saved.inspected)) {
        state.inspected = [];
        saved.inspected.forEach(function (id) { if (typeof id === "string" && mechById(id)) addUnique(state.inspected, id); });
      }
    }
    addUnique(state.viewed, state.map);
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var stored = null;
    try { stored = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) { stored = null; }
    hydrate(stored, null);
  }
</script>
</body>
</html>

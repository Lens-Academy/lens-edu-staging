---
id: 'a292da3b-4992-4c11-ab67-df15d1be64a2'
title: Place your bets
summary_for_tutor: "A rating exercise on twelve verification mechanisms (chip identity, compute metering, licensing, proof-of-learning, cloud KYC, cloud monitoring, satellites, supply chain, intel sharing, whistleblowers, inspections, ZK proofs). One card at a time, the learner reads the mechanism summary and picks one of five rungs on each of four metrics (technical feasibility, political feasibility, verification effectiveness, durability), then places the card; each placed card appears as a marker on four ranking lanes so the learner sees the ordering take shape. They can skip a card, click a marker to review its four values and revisit the card, and seal the set once all twelve are placed. The widget holds no prose: the four metric definitions with their low and high anchors are lesson text above the widget, the five rung labels per metric are in a closed callout on the page titled for opening before rating, and the note that there is no key and no score sits in page text right after the widget. The saved summary lists every rung chosen. Never reveal or grade against reference ratings; XLab compares them only in the separate capstone. Complete means the learner sealed all twelve. Content ported from XLab Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Place your bets</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "mechanism-sort". -->
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
  p { margin: 0; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 20px; margin: 0; }
  .block { margin-top: 16px; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: var(--surface); }
  .card-top { display: flex; align-items: center; gap: 8px; font-size: 12px; color: var(--muted); }
  .card-top .layer { font-weight: 600; color: var(--text); }
  .card-top .spacer { flex: 1; }
  .summary { color: var(--muted); margin-top: 4px; }
  .metric { margin-top: 14px; }
  .metric-head { display: flex; justify-content: space-between; align-items: baseline; gap: 8px; }
  .metric-head .name { font-weight: 600; }
  .metric-head .pick { font-size: 12px; font-weight: 600; color: var(--accent); }
  .rungs { display: grid; grid-template-columns: repeat(5, minmax(0, 1fr)); gap: 4px; margin-top: 6px; }
  button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 8px 12px; cursor: pointer; }
  button:hover { background: var(--surface); }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button:disabled { opacity: 0.5; cursor: default; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.quiet { border-color: transparent; background: transparent; padding: 4px 8px; font-size: 12px; color: var(--muted); }
  button.quiet:hover { background: #fff; border-color: var(--border); color: var(--text); }
  button.rung { padding: 6px 2px; font-size: 11px; line-height: 1.2; text-align: center; overflow-wrap: anywhere; border-radius: 6px; }
  button.rung[aria-checked="true"] { background: var(--accent); border-color: var(--accent); color: #fff; font-weight: 600; }
  .actions { display: flex; flex-wrap: wrap; align-items: center; gap: 12px; margin-top: 16px; }
  .hint { font-size: 12px; color: var(--muted); }
  .dashed { border: 1px dashed var(--border); border-radius: 8px; padding: 12px; color: var(--muted); }
  .lane-block { margin-top: 12px; }
  .lane-head { display: flex; justify-content: space-between; align-items: baseline; font-size: 12px; gap: 8px; }
  .lane-head .name { font-weight: 600; }
  .lane-head .ends { color: var(--muted); }
  .lane { position: relative; height: 56px; border: 1px solid var(--border); border-radius: 6px; margin-top: 4px; background: #fff; }
  .lane .rail { position: absolute; left: 12px; right: 12px; top: 50%; height: 1px; background: var(--border); }
  .lane .field { position: absolute; left: 12px; right: 12px; top: 0; bottom: 0; }
  .mark { position: absolute; width: 14px; height: 14px; padding: 0; border: 0; border-radius: 0; background: transparent; transform: translate(-50%, -50%); cursor: pointer; }
  .mark:hover { background: transparent; }
  .mark .shape { display: block; width: 14px; height: 14px; }
  .mark.is-selected .shape { outline: 2px solid var(--text); outline-offset: 2px; border-radius: 2px; }
  .shape { display: inline-block; width: 12px; height: 12px; vertical-align: -2px; }
  .shape.hardware { background: var(--accent); border-radius: 50%; }
  .shape.cloud { background: var(--text); border-radius: 2px; }
  .shape.intelligence { background: #8a8580; clip-path: polygon(50% 0, 100% 50%, 50% 100%, 0 50%); }
  .shape.human { background: #4a4540; clip-path: polygon(50% 0, 100% 100%, 0 100%); }
  .shape.crypto { background: #fff; border: 2px solid var(--accent-hover); border-radius: 50%; }
  .legend { display: flex; flex-wrap: wrap; gap: 6px 16px; font-size: 12px; color: var(--muted); margin-top: 12px; }
  .legend span.item { display: inline-flex; align-items: center; gap: 6px; font-weight: 600; }
  .detail { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; margin-top: 16px; }
  .detail-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 8px; }
  .detail .layer { font-size: 11px; font-weight: 600; color: var(--muted); }
  .detail h2 { font-size: 18px; }
  .drow { margin-top: 8px; }
  .drow .bar { position: relative; height: 16px; border-radius: 4px; background: var(--surface); margin-top: 4px; }
  .drow .bar .field { position: absolute; left: 8px; right: 8px; top: 0; bottom: 0; }
  .drow .bar .shape { position: absolute; top: 50%; transform: translate(-50%, -50%); }
  .drow .val { font-size: 12px; color: var(--muted); }
  .drow .val strong { color: var(--text); }
  .sealbox { margin-top: 16px; border: 1px solid var(--border); border-radius: 8px; padding: 12px; background: var(--surface); }
  .sealbox p + p { margin-top: 4px; }
</style>
</head>
<body>
<div id="rater"></div>
<div class="block" id="lanes"></div>
<div class="legend" id="legend" aria-label="Layer key"></div>
<div id="detail"></div>
<div id="seal"></div>

<script>
  var LAYERS = [
    { key: "hardware", name: "Hardware" },
    { key: "cloud", name: "Cloud" },
    { key: "intelligence", name: "Intelligence" },
    { key: "human", name: "Human layer" },
    { key: "crypto", name: "Cryptographic" }
  ];

  var METRICS = [
    {
      key: "tech",
      name: "Technical feasibility",
      rungs: ["Not close", "Research", "Prototype", "Buildable", "Running"]
    },
    {
      key: "pol",
      name: "Political feasibility",
      rungs: ["Non-starter", "Rivals yield", "Hard bargain", "Willing", "Piggybacks"]
    },
    {
      key: "eff",
      name: "Verification effectiveness",
      rungs: ["Near nothing", "Weak/narrow", "Capped", "Solid", "Strong & broad"]
    },
    {
      key: "dur",
      name: "Durability",
      rungs: ["Leaking now", "Decaying", "Needs upkeep", "Ages slowly", "Decade-proof"]
    }
  ];

  var MECHANISMS = [
    { id: "chip-id", layer: "hardware", short: "Chip identity", title: "Chip identity and remote attestation",
      summary: "Every AI accelerator carries a unique cryptographic identity and can prove to a remote verifier what firmware it is running. This would let a treaty body maintain a registry of who holds which chips and confirm the hardware has not been tampered with." },
    { id: "metering", layer: "hardware", short: "Compute metering", title: "On-chip compute metering",
      summary: "Chips measure how much computation they perform and what class of workload it is, then report the totals to a verifier. This could confirm that declared facilities stay under agreed compute thresholds." },
    { id: "licensing", layer: "hardware", short: "Licensing", title: "Hardware licensing and remote authorization",
      summary: "Chips require a cryptographic license, renewed on a schedule, to keep operating at full capability. An authority could suspend or revoke a violator's compute directly rather than relying on sanctions after the fact." },
    { id: "proof-of-learning", layer: "hardware", short: "Proof-of-learning", title: "Independent verification of training claims",
      summary: "Developers preserve checkpoints and training records, and verifiers recompute randomly chosen segments of the run on their own cluster. A match supports the claim that the declared training run is what actually happened." },
    { id: "cloud-kyc", layer: "cloud", short: "Cloud KYC", title: "Cloud KYC and cluster registration",
      summary: "Cloud providers verify who their large customers really are, including beneficial owners behind reseller chains, and register large clusters and training runs with an authority. Frontier-scale compute becomes hard to rent anonymously." },
    { id: "cloud-monitoring", layer: "cloud", short: "Cloud monitoring", title: "Cloud workload monitoring and reporting",
      summary: "Providers watch cluster allocation and utilization patterns, preserve logs and billing records, report suspicious use, and can suspend access. The provider becomes a standing observer of what its customers run." },
    { id: "satellite", layer: "intelligence", short: "Satellites", title: "Satellite and infrastructure monitoring",
      summary: "Remote sensing tracks data-center construction, power draw, and cooling infrastructure. Frontier-scale facilities have physical signatures that are difficult to hide from overhead collection." },
    { id: "supply-chain", layer: "intelligence", short: "Supply chain", title: "Chip supply-chain tracking",
      summary: "Export records, customs data, and financial activity trace accelerators from fabrication to installation. Diversions and smuggling routes show up as gaps between where chips were sold and where they can be accounted for." },
    { id: "intel-sharing", layer: "intelligence", short: "Intel sharing", title: "National intelligence sharing",
      summary: "States pass leads from their own collection to an international verification body, the way national tips have pointed nuclear inspectors at undeclared facilities. The regime supplies the follow-up; the agencies supply the anomaly." },
    { id: "whistleblower", layer: "human", short: "Whistleblowers", title: "Whistleblower channels and protections",
      summary: "Secure reporting channels, anti-retaliation protections, and rewards give employees, contractors, and suppliers a path to report concealed activity. Insiders can see what no sensor reaches." },
    { id: "inspections", layer: "human", short: "Inspections", title: "On-site and challenge inspections",
      summary: "International inspectors visit declared facilities on a routine schedule and can demand short-notice access to suspect sites. Managed-access rules decide what inspectors may see and what stays shielded." },
    { id: "zk-proofs", layer: "crypto", short: "ZK proofs", title: "Privacy-preserving proofs",
      summary: "Zero-knowledge proofs and secure multiparty computation let a developer prove a claim about a model or training run without revealing weights, code, or data. Verification without disclosure, if the cryptography scales." }
  ];

  var COPY = {
    raterDone: "All twelve rated. Click any dot to revisit a call, then seal.",
    sealNotePending: "Enabled once all twelve are rated"
  };

  var STORAGE_KEY = "lens-widget:mechanism-sort";

  // State mirrors XLab's SortStore: values[mechId][metricKey] = (rung + 0.5) / 5.
  var store = emptyStore();
  var selected = null;
  var completed = false;

  function emptyStore() {
    return { values: {}, queue: MECHANISMS.map(function (m) { return m.id; }), sealed: false, sealedAt: null };
  }
  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }
  function mechById(id) { for (var i = 0; i < MECHANISMS.length; i++) if (MECHANISMS[i].id === id) return MECHANISMS[i]; return null; }
  function layerName(key) { for (var i = 0; i < LAYERS.length; i++) if (LAYERS[i].key === key) return LAYERS[i].name; return key; }
  function rungValue(i) { return (i + 0.5) / 5; }
  function rungIndex(v) { return Math.min(4, Math.floor(v * 5)); }
  function valuesOf(id) { return store.values[id] || {}; }
  function isComplete(v) { return METRICS.every(function (m) { return typeof v[m.key] === "number"; }); }
  var MARK_STEP = 15;
  function shape(layer, extraClass) {
    var s = el("span", "shape " + layer + (extraClass ? " " + extraClass : ""));
    s.setAttribute("aria-hidden", "true");
    return s;
  }
  function ratedCount() { return MECHANISMS.length - store.queue.length; }
  function currentId() { return !store.sealed && store.queue.length > 0 ? store.queue[0] : null; }
  function placedIds() {
    return MECHANISMS.filter(function (m) { return store.queue.indexOf(m.id) === -1; }).map(function (m) { return m.id; });
  }

  // ---- persistence ----
  function summaryText() {
    var parts = [];
    var placed = placedIds();
    parts.push(store.sealed
      ? "The learner sealed all twelve mechanism ratings" + (store.sealedAt ? " on " + store.sealedAt : "") + "."
      : "The learner has placed " + placed.length + " of 12 mechanisms on the lanes" + (currentId() ? "; currently rating " + mechById(currentId()).title : "") + ".");
    MECHANISMS.forEach(function (m) {
      var v = valuesOf(m.id);
      var bits = [];
      METRICS.forEach(function (mt) {
        if (typeof v[mt.key] === "number") bits.push(mt.name + " " + mt.rungs[rungIndex(v[mt.key])] + " (" + Math.round(v[mt.key] * 100) + ")");
      });
      var placedNow = placed.indexOf(m.id) !== -1;
      if (bits.length) parts.push(m.title + (placedNow ? "" : " (not yet placed)") + ": " + bits.join(", ") + ".");
      else parts.push(m.title + ": not rated yet.");
    });
    parts.push("Ratings are on a 0 to 100 scale in five rungs. No reference map is shown in this widget.");
    return parts.join(" ");
  }
  function persist() {
    var snapshot = { values: store.values, queue: store.queue, sealed: store.sealed, sealedAt: store.sealedAt };
    if (window.Lens) {
      Lens.saveState(snapshot, summaryText());
      if (store.sealed && !completed) { completed = true; Lens.complete(); }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snapshot)); } catch (e) {}
    }
  }
  function commit() { render(); persist(); }

  // ---- actions ----
  function setRung(metricKey, i) {
    var cur = currentId();
    if (!cur) return;
    var v = {};
    var old = valuesOf(cur);
    for (var k in old) if (Object.prototype.hasOwnProperty.call(old, k)) v[k] = old[k];
    v[metricKey] = rungValue(i);
    store.values[cur] = v;
    commit();
  }
  function place() {
    var cur = currentId();
    if (!cur || !isComplete(valuesOf(cur))) return;
    store.queue = store.queue.filter(function (q) { return q !== cur; });
    commit();
  }
  function skip() {
    var cur = currentId();
    if (!cur || store.queue.length < 2) return;
    store.queue = store.queue.slice(1).concat([cur]);
    commit();
  }
  function revisit(id) {
    if (store.sealed) return;
    selected = null;
    if (store.queue.indexOf(id) === -1) store.queue = [id].concat(store.queue);
    commit();
  }
  function seal() {
    if (store.queue.length !== 0 || store.sealed) return;
    var sealedAt;
    try {
      sealedAt = new Date().toLocaleDateString(undefined, { year: "numeric", month: "long", day: "numeric" });
    } catch (e) { sealedAt = new Date().toDateString(); }
    store.sealed = true;
    store.sealedAt = sealedAt;
    selected = null;
    commit();
  }
  function select(id) { selected = selected === id ? null : id; render(); }

  // ---- static parts ----
  var legend = document.getElementById("legend");
  LAYERS.forEach(function (l) {
    var s = el("span", "item");
    s.appendChild(shape(l.key));
    s.appendChild(document.createTextNode(l.name));
    legend.appendChild(s);
  });

  // ---- rendering ----
  var raterBox = document.getElementById("rater");
  var lanesBox = document.getElementById("lanes");
  var detailBox = document.getElementById("detail");
  var sealBox = document.getElementById("seal");

  function renderRater() {
    clear(raterBox);
    var cur = currentId();
    if (!cur) {
      raterBox.hidden = !!store.sealed;
      if (!store.sealed) raterBox.appendChild(el("p", "dashed", COPY.raterDone));
      return;
    }
    raterBox.hidden = false;
    var m = mechById(cur);
    var v = valuesOf(cur);
    var card = el("div", "card");
    card.setAttribute("aria-label", "Rate " + m.title);

    var top = el("div", "card-top");
    top.appendChild(shape(m.layer));
    var lab = el("span");
    lab.appendChild(el("span", "layer", layerName(m.layer)));
    lab.appendChild(document.createTextNode(" · card " + (ratedCount() + 1) + " of " + MECHANISMS.length));
    top.appendChild(lab);
    top.appendChild(el("span", "spacer"));
    if (store.queue.length > 1) {
      var sk = el("button", "quiet", "Skip for now"); sk.type = "button"; sk.id = "skip";
      sk.addEventListener("click", skip);
      top.appendChild(sk);
    }
    card.appendChild(top);
    card.appendChild(el("h2", "", m.title));
    card.appendChild(el("p", "summary", m.summary));

    METRICS.forEach(function (mt) {
      var sel = typeof v[mt.key] === "number" ? rungIndex(v[mt.key]) : -1;
      var wrap = el("div", "metric");
      var head = el("div", "metric-head");
      head.appendChild(el("span", "name", mt.name));
      head.appendChild(el("span", "pick", sel >= 0 ? "✓ " + mt.rungs[sel] : ""));
      wrap.appendChild(head);
      var group = el("div", "rungs");
      group.setAttribute("role", "radiogroup");
      group.setAttribute("aria-label", mt.name);
      mt.rungs.forEach(function (r, i) {
        var b = el("button", "rung", r);
        b.type = "button";
        b.setAttribute("role", "radio");
        b.setAttribute("aria-checked", sel === i ? "true" : "false");
        b.setAttribute("data-metric", mt.key);
        b.addEventListener("click", function () { setRung(mt.key, i); });
        group.appendChild(b);
      });
      wrap.appendChild(group);
      card.appendChild(wrap);
    });

    var actions = el("div", "actions");
    var ok = isComplete(v);
    var pl = el("button", "primary", "Place on the lanes"); pl.type = "button"; pl.id = "place";
    pl.disabled = !ok;
    pl.addEventListener("click", place);
    actions.appendChild(pl);
    if (!ok) actions.appendChild(el("span", "hint", "Rate all four metrics to place this card."));
    card.appendChild(actions);
    raterBox.appendChild(card);
  }

  function renderLanes() {
    clear(lanesBox);
    var ids = placedIds();
    lanesBox.hidden = ids.length === 0;
    if (!ids.length) return;
    lanesBox.appendChild(el("p", "eyebrow", "Your ranking, metric by metric"));
    METRICS.forEach(function (mt) {
      var block = el("div", "lane-block");
      var head = el("div", "lane-head");
      head.appendChild(el("span", "name", mt.name));
      head.appendChild(el("span", "ends", mt.rungs[0] + " → " + mt.rungs[4]));
      block.appendChild(head);
      var rungCounts = [0, 0, 0, 0, 0];
      var spots = [];
      ids.forEach(function (id) {
        var val = valuesOf(id)[mt.key];
        if (typeof val !== "number") return;
        var r = rungIndex(val);
        spots.push({ id: id, val: val, rung: r, rank: rungCounts[r] });
        rungCounts[r] += 1;
      });
      var maxStack = 1;
      for (var ri = 0; ri < rungCounts.length; ri++) if (rungCounts[ri] > maxStack) maxStack = rungCounts[ri];
      var lane = el("div", "lane");
      lane.style.height = Math.max(56, maxStack * MARK_STEP + 8) + "px";
      lane.setAttribute("role", "group");
      lane.setAttribute("aria-label", mt.name + " lane, " + mt.rungs[0] + " on the left to " + mt.rungs[4] + " on the right");
      lane.appendChild(el("div", "rail"));
      var field = el("div", "field");
      spots.forEach(function (spot) {
        var id = spot.id;
        var m = mechById(id);
        var val = spot.val;
        var stacked = rungCounts[spot.rung];
        var offset = (spot.rank - (stacked - 1) / 2) * MARK_STEP;
        var b = el("button", "mark" + (selected === id ? " is-selected" : ""));
        b.type = "button";
        b.setAttribute("aria-label", m.title + ", " + mt.rungs[rungIndex(val)] + ", " + Math.round(val * 100));
        b.setAttribute("aria-pressed", selected === id ? "true" : "false");
        b.title = m.short + ": " + mt.rungs[rungIndex(val)];
        b.style.left = (val * 100) + "%";
        b.style.top = "calc(50% + " + offset + "px)";
        b.appendChild(shape(m.layer));
        b.addEventListener("click", function () { select(id); });
        field.appendChild(b);
      });
      lane.appendChild(field);
      block.appendChild(lane);
      lanesBox.appendChild(block);
    });
  }

  function renderDetail() {
    clear(detailBox);
    if (!selected || placedIds().indexOf(selected) === -1) { detailBox.hidden = true; return; }
    detailBox.hidden = false;
    var m = mechById(selected);
    var v = valuesOf(selected);
    var d = el("div", "detail");
    d.setAttribute("role", "region");
    d.setAttribute("aria-label", "Your ratings for " + m.title);
    var top = el("div", "detail-top");
    var left = el("div");
    left.appendChild(el("p", "layer", layerName(m.layer)));
    left.appendChild(el("h2", "", m.title));
    top.appendChild(left);
    var cl = el("button", "quiet", "Close"); cl.type = "button"; cl.id = "close";
    cl.addEventListener("click", function () { selected = null; render(); });
    top.appendChild(cl);
    d.appendChild(top);

    METRICS.forEach(function (mt) {
      var val = v[mt.key];
      if (typeof val !== "number") return;
      var row = el("div", "drow");
      var head = el("div", "lane-head");
      head.appendChild(el("span", "name", mt.name));
      var vs = el("span", "val");
      vs.appendChild(el("strong", "", String(Math.round(val * 100))));
      vs.appendChild(document.createTextNode(" · " + mt.rungs[rungIndex(val)]));
      head.appendChild(vs);
      row.appendChild(head);
      var bar = el("div", "bar");
      var field = el("div", "field");
      var s = shape(m.layer);
      s.style.left = (val * 100) + "%";
      field.appendChild(s);
      bar.appendChild(field);
      row.appendChild(bar);
      d.appendChild(row);
    });

    d.appendChild(el("p", "summary", m.summary));
    if (!store.sealed) {
      var rv = el("button", "", "Revisit this card"); rv.type = "button"; rv.id = "revisit";
      rv.style.marginTop = "12px";
      rv.addEventListener("click", function () { revisit(m.id); });
      d.appendChild(rv);
    }
    detailBox.appendChild(d);
  }

  function renderSeal() {
    clear(sealBox);
    var box = el("div", "sealbox");
    if (store.sealed) {
      box.appendChild(el("p", "eyebrow", "✓ Sealed " + (store.sealedAt || "")));
    } else {
      var ready = store.queue.length === 0;
      var b = el("button", "primary", "Seal my ratings"); b.type = "button"; b.id = "seal-btn";
      b.disabled = !ready;
      b.addEventListener("click", seal);
      box.appendChild(b);
      if (!ready) {
        var note = el("p", "hint", COPY.sealNotePending);
        note.style.marginTop = "6px";
        box.appendChild(note);
      }
    }
    sealBox.appendChild(box);
  }

  function render() {
    renderRater();
    renderLanes();
    renderDetail();
    renderSeal();
  }

  // ---- restore ----
  function hydrate(saved, meta) {
    var next = emptyStore();
    if (saved && typeof saved === "object" && saved.values && typeof saved.values === "object" && Array.isArray(saved.queue)) {
      MECHANISMS.forEach(function (m) {
        var raw = saved.values[m.id];
        if (!raw || typeof raw !== "object") return;
        var v = {};
        METRICS.forEach(function (mt) {
          var x = raw[mt.key];
          if (typeof x === "number" && x >= 0 && x <= 1) v[mt.key] = x;
        });
        if (Object.keys(v).length) next.values[m.id] = v;
      });
      var q = saved.queue.filter(function (id) { return !!mechById(id); });
      // A mechanism can only be off the queue if it is fully rated.
      MECHANISMS.forEach(function (m) {
        if (q.indexOf(m.id) === -1 && !isComplete(next.values[m.id] || {})) q.push(m.id);
      });
      next.queue = q;
      next.sealed = !!saved.sealed && q.length === 0;
      next.sealedAt = typeof saved.sealedAt === "string" ? saved.sealedAt : null;
    }
    store = next;
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) {}
    hydrate(raw, { completed: false });
  }
</script>
</body>
</html>

---
id: '62b8bee8-b150-4ed4-824a-bc16d4209b11'
title: The collection map
summary_for_tutor: "A grid of the seven intelligence collection disciplines, split into two families: those that collect language (OSINT, HUMINT, SIGINT, CYBER) and those that collect physics (IMINT, GEOINT, MASINT). The learner opens one tile at a time to read what the discipline is, what it picks up (which signature families of undeclared AI development it sees) and its characteristic limit. Tiles they have opened are marked, a counter shows how many of the seven they have read, and the widget is complete once all seven have been opened. The saved-state summary lists which disciplines the learner has opened and which one is open now. Content ported from XLab's Verification track, lesson 2.3.1."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The collection map</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "collection-map". -->
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
  h1, h2 { font-family: var(--font-heading); font-weight: 600; margin: 0; }
  h1 { font-size: 24px; line-height: 1.2; }
  .lede { color: var(--muted); margin: 6px 0 0; max-width: 42rem; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  .status { display: flex; flex-wrap: wrap; gap: 8px 16px; align-items: center; justify-content: space-between; margin-top: 12px; }
  .progress { font-size: 12px; color: var(--muted); }
  .progress.is-done { color: var(--accent); font-weight: 600; }
  .group { margin-top: 20px; }
  .grid { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 8px; margin-top: 8px; }
  @media (min-width: 640px) { .grid { grid-template-columns: repeat(4, minmax(0, 1fr)); } }
  .tile {
    display: flex; flex-direction: column; align-items: flex-start; gap: 6px;
    width: 100%; text-align: left; font: inherit; color: inherit; cursor: pointer;
    border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 12px;
    transition: background-color 120ms;
  }
  .tile:hover { background: var(--surface); }
  .tile:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  .tile.is-open { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: var(--surface); }
  .tile .glyph { color: var(--muted); width: 24px; height: 24px; display: block; }
  .tile.is-open .glyph { color: var(--accent); }
  .tile .abbr { font-size: 12px; font-weight: 600; letter-spacing: 0.08em; }
  .tile .name { font-size: 12px; line-height: 1.3; color: var(--muted); }
  .tile .seen { display: none; font-size: 11px; font-weight: 500; color: var(--accent); margin-top: 2px; }
  .tile.is-seen .seen { display: inline; }
  .detail { display: none; margin-top: 20px; border: 1px solid var(--border); border-radius: 8px; background: var(--surface); padding: 16px; }
  .detail.is-open { display: block; }
  .detail-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 12px; }
  .detail .abbr { font-size: 12px; letter-spacing: 0.08em; font-weight: 600; margin: 0; }
  .detail h2 { font-size: 20px; margin-top: 2px; }
  .detail .what { margin: 10px 0 0; max-width: 48rem; }
  .detail dl { margin: 12px 0 0; }
  .detail dt { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin-top: 10px; }
  .detail dd { margin: 2px 0 0; max-width: 48rem; }
  .close {
    font: inherit; border: 1px solid var(--border); background: #fff; color: var(--muted);
    width: 32px; height: 32px; border-radius: 8px; cursor: pointer; font-size: 18px; line-height: 1; flex: none;
  }
  .close:hover { background: var(--surface); color: var(--text); }
  .legend { margin-top: 20px; color: var(--muted); }
  .legend.is-hidden { display: none; }
</style>
</head>
<body>
<section aria-labelledby="cm-title">
  <h1 id="cm-title"></h1>
  <p class="lede" id="cm-lede"></p>
  <div class="status">
    <span class="progress" id="progress"></span>
  </div>
  <div id="groups"></div>
  <p class="legend" id="legend"></p>
  <div class="detail" id="detail" role="region" aria-live="polite">
    <div class="detail-top">
      <div>
        <p class="abbr" id="d-abbr"></p>
        <h2 id="d-name"></h2>
      </div>
      <button type="button" class="close" id="close" aria-label="Close">&times;</button>
    </div>
    <p class="what" id="d-what"></p>
    <dl>
      <dt id="d-seen-label"></dt>
      <dd id="d-seen"></dd>
      <dt id="d-limit-label"></dt>
      <dd id="d-limit"></dd>
    </dl>
  </div>
</section>

<script>
  var COPY = {
    title: "The collection map",
    lede: "Seven ways a watcher sees. The disciplines split into two families: those that collect language, and those that collect physics. Open each one.",
    literal: "Collects language",
    technical: "Collects physics",
    legend: "Click a discipline to read what it is.",
    seenLabel: "Picks up",
    limitLabel: "Characteristic limit"
  };

  var DISCIPLINES = [
    {
      id: "osint", abbr: "OSINT", name: "Open-source intelligence", kind: "literal",
      what: "Anything published or otherwise available without concealment: permits, corporate filings, hiring, supplier disclosures, interconnect queues and power-purchase records.",
      seen: "Organizational and facility signatures, before anything is built.",
      limit: "Six Layers classes it with the supplemental mechanisms: it rarely settles a question on its own."
    },
    {
      id: "humint", abbr: "HUMINT", name: "Human intelligence", kind: "literal",
      what: "Collection from people: sources inside an organization, defectors, contractors, and anyone with placement and access.",
      seen: "Intent and internal knowledge, which no sensor reads.",
      limit: "Slow, unschedulable, and dependent on a person choosing to talk; it cannot be tasked the way a satellite can."
    },
    {
      id: "sigint", abbr: "SIGINT", name: "Signals intelligence", kind: "literal",
      what: "Interception of communications and electronic emissions: who is talking to whom, and sometimes what they said.",
      seen: "Organizational and operational signatures.",
      limit: "The most sources-and-methods-sensitive stream, which is exactly why it is the hardest to share with a treaty verifier."
    },
    {
      id: "cyber", abbr: "CYBER", name: "Cyber intelligence", kind: "literal",
      what: "Collection from networks and systems themselves. MIRI's Definition 17 names it inside national technical means.",
      seen: "Operational signatures: what a facility is actually running.",
      limit: "Its inclusion in a treaty definition is contested: read as legalized collection by one party and as a license to hack by the other."
    },
    {
      id: "imint", abbr: "IMINT", name: "Imagery intelligence", kind: "technical",
      what: "Overhead and aerial imagery: building footprint, electrical substations, cooling plant, security perimeter.",
      seen: "Facility signatures, and construction while it is happening.",
      limit: "Unlikely to separate an AI datacenter from any other datacenter (cooling is the differentiator), and defeated by underground siting."
    },
    {
      id: "geoint", abbr: "GEOINT", name: "Geospatial intelligence", kind: "technical",
      what: "Imagery placed in geographic and temporal context: terrain, infrastructure, transmission lines, and change over time.",
      seen: "Resource-flow signatures: the grid connection a large site needs.",
      limit: "Reads the surroundings well and the activity inside poorly."
    },
    {
      id: "masint", abbr: "MASINT", name: "Measurement and signature intelligence", kind: "technical",
      what: "The physics a facility emits: thermal, effluent, radar and geophysical signatures. Clark's technical-collection reference is the one on this.",
      seen: "Waste heat and the narrow temperature band of constant chip operation; geophysical methods are already used against underground construction.",
      limit: "The signature it reads is shrinking: performance-per-watt improves about 1.6x a year, so a fixed quantity of compute emits less each year."
    }
  ];

  // Glyph paths, one per discipline, from XLab's Glyph component.
  var GLYPHS = {
    osint: [["path", "M4 5h16v14H4z"], ["path", "M7 9h6M7 12h10M7 15h8"]],
    humint: [["circle", "12,8,3.2"], ["path", "M5 20c1.4-3.6 4-5.4 7-5.4s5.6 1.8 7 5.4"]],
    sigint: [["path", "M12 14v6"], ["circle", "12,12,1.6"], ["path", "M8.2 8.2a5.4 5.4 0 0 0 0 7.6M15.8 8.2a5.4 5.4 0 0 1 0 7.6"], ["path", "M5.4 5.4a9.4 9.4 0 0 0 0 13.2M18.6 5.4a9.4 9.4 0 0 1 0 13.2"]],
    cyber: [["rect", "4.5,10,15,9,1.6"], ["path", "M8.5 10V7.2a3.5 3.5 0 0 1 7 0V10"], ["path", "M12 13.5v2"]],
    imint: [["path", "M3 12s3.4-5.4 9-5.4S21 12 21 12s-3.4 5.4-9 5.4S3 12 3 12z"], ["circle", "12,12,2.4"]],
    geoint: [["circle", "12,12,8.4"], ["path", "M3.6 12h16.8M12 3.6c2.4 2.6 3.6 5.5 3.6 8.4s-1.2 5.8-3.6 8.4c-2.4-2.6-3.6-5.5-3.6-8.4S9.6 6.2 12 3.6z"]],
    masint: [["path", "M3.5 17c2-.2 2.6-5.6 4.6-5.6S10.4 19 12.4 19s2.4-13 4.4-13c1.6 0 2.2 6 3.7 6"]]
  };

  var SVG_NS = "http://www.w3.org/2000/svg";
  var STORAGE_KEY = "lens-widget-collection-map";

  var state = { opened: [], openId: null };
  var completed = false;
  var tiles = {};

  function el(tag, className, text) {
    var n = document.createElement(tag);
    if (className) n.className = className;
    if (text !== undefined) n.textContent = text;
    return n;
  }

  function glyph(id) {
    var svg = document.createElementNS(SVG_NS, "svg");
    svg.setAttribute("viewBox", "0 0 24 24");
    svg.setAttribute("class", "glyph");
    svg.setAttribute("aria-hidden", "true");
    var g = document.createElementNS(SVG_NS, "g");
    g.setAttribute("fill", "none");
    g.setAttribute("stroke", "currentColor");
    g.setAttribute("stroke-width", "1.5");
    g.setAttribute("stroke-linecap", "round");
    g.setAttribute("stroke-linejoin", "round");
    (GLYPHS[id] || []).forEach(function (part) {
      var kind = part[0], spec = part[1], node = document.createElementNS(SVG_NS, kind);
      if (kind === "path") {
        node.setAttribute("d", spec);
      } else if (kind === "circle") {
        var c = spec.split(",");
        node.setAttribute("cx", c[0]); node.setAttribute("cy", c[1]); node.setAttribute("r", c[2]);
      } else if (kind === "rect") {
        var r = spec.split(",");
        node.setAttribute("x", r[0]); node.setAttribute("y", r[1]);
        node.setAttribute("width", r[2]); node.setAttribute("height", r[3]); node.setAttribute("rx", r[4]);
      }
      g.appendChild(node);
    });
    svg.appendChild(g);
    return svg;
  }

  function byId(id) {
    for (var i = 0; i < DISCIPLINES.length; i++) if (DISCIPLINES[i].id === id) return DISCIPLINES[i];
    return null;
  }
  function isOpened(id) { return state.opened.indexOf(id) !== -1; }

  document.getElementById("cm-title").textContent = COPY.title;
  document.getElementById("cm-lede").textContent = COPY.lede;
  document.getElementById("legend").textContent = COPY.legend;
  document.getElementById("d-seen-label").textContent = COPY.seenLabel;
  document.getElementById("d-limit-label").textContent = COPY.limitLabel;

  var groupsEl = document.getElementById("groups");
  [["literal", COPY.literal], ["technical", COPY.technical]].forEach(function (pair) {
    var kind = pair[0], label = pair[1];
    var group = el("div", "group");
    group.appendChild(el("p", "eyebrow", label));
    var grid = el("div", "grid");
    grid.setAttribute("role", "list");
    DISCIPLINES.filter(function (d) { return d.kind === kind; }).forEach(function (d) {
      var tile = el("button", "tile");
      tile.type = "button";
      tile.setAttribute("role", "listitem");
      tile.setAttribute("aria-expanded", "false");
      tile.dataset.id = d.id;
      tile.appendChild(glyph(d.id));
      tile.appendChild(el("span", "abbr", d.abbr));
      tile.appendChild(el("span", "name", d.name));
      tile.appendChild(el("span", "seen", "✓ Opened"));
      tile.addEventListener("click", function () { toggle(d.id); });
      tiles[d.id] = tile;
      grid.appendChild(tile);
    });
    group.appendChild(grid);
    groupsEl.appendChild(group);
  });

  function summary() {
    var openedNames = state.opened.map(function (id) { var d = byId(id); return d ? d.abbr : id; });
    var text = "Collection map: the learner has opened " + state.opened.length + " of " + DISCIPLINES.length + " disciplines";
    text += openedNames.length ? " (" + openedNames.join(", ") + ")." : ".";
    var cur = state.openId ? byId(state.openId) : null;
    if (cur) {
      text += " Currently reading " + cur.abbr + ", " + cur.name + ": picks up " + cur.seen + " Characteristic limit: " + cur.limit;
    } else {
      text += " No discipline is open right now.";
    }
    if (state.opened.length === DISCIPLINES.length) text += " All seven disciplines have been read.";
    return text;
  }

  function persist() {
    var snapshot = { opened: state.opened.slice(), openId: state.openId };
    if (window.Lens) {
      Lens.saveState(snapshot, summary());
      if (!completed && state.opened.length === DISCIPLINES.length) {
        completed = true;
        Lens.complete();
      }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(snapshot)); } catch (e) { /* storage unavailable */ }
    }
  }

  function render() {
    DISCIPLINES.forEach(function (d) {
      var t = tiles[d.id];
      var open = state.openId === d.id;
      t.classList.toggle("is-open", open);
      t.classList.toggle("is-seen", isOpened(d.id));
      t.setAttribute("aria-expanded", open ? "true" : "false");
    });
    var cur = state.openId ? byId(state.openId) : null;
    var detail = document.getElementById("detail");
    var legend = document.getElementById("legend");
    if (cur) {
      document.getElementById("d-abbr").textContent = cur.abbr;
      document.getElementById("d-name").textContent = cur.name;
      document.getElementById("d-what").textContent = cur.what;
      document.getElementById("d-seen").textContent = cur.seen;
      document.getElementById("d-limit").textContent = cur.limit;
    }
    detail.classList.toggle("is-open", !!cur);
    legend.classList.toggle("is-hidden", !!cur);
    var progress = document.getElementById("progress");
    var n = state.opened.length;
    var done = n === DISCIPLINES.length;
    progress.textContent = done
      ? "✓ All " + DISCIPLINES.length + " disciplines opened"
      : n + " of " + DISCIPLINES.length + " disciplines opened";
    progress.classList.toggle("is-done", done);
  }

  function toggle(id) {
    if (state.openId === id) {
      state.openId = null;
    } else {
      state.openId = id;
      if (!isOpened(id)) state.opened.push(id);
    }
    render();
    persist();
    if (state.openId) {
      document.getElementById("detail").scrollIntoView({ behavior: "smooth", block: "nearest" });
    }
  }

  document.getElementById("close").addEventListener("click", function () {
    state.openId = null;
    render();
    persist();
  });

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      if (Array.isArray(saved.opened)) {
        state.opened = saved.opened.filter(function (id) { return typeof id === "string" && byId(id) !== null; });
      }
      if (typeof saved.openId === "string" && byId(saved.openId)) {
        state.openId = saved.openId;
        if (!isOpened(saved.openId)) state.opened.push(saved.openId);
      }
    }
    completed = !!(meta && meta.completed);
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var stored = null;
    try { stored = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) { stored = null; }
    hydrate(stored, { completed: false });
  }
</script>
</body>
</html>

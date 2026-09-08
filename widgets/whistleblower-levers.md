---
id: 'c155d7b3-1a56-44f1-8bec-49efcca34a65'
title: Four Levers, One Each
summary_for_tutor: "A matching exercise on four whistleblower mechanisms: anti-retaliation protection (California Labor Code 1107.1), financial reward (Wasil et al.), mandatory reporting (SB 53, Business and Professions Code 22757.13(c)) and professional duty (ACM Code of Ethics 1.2). Each mechanism is shown with its source quotation and a citation link, and the learner assigns one of four leverage chips to each row: a legal right and remedies, the reporter's incentives, a duty on the developer, or escalation as professional conduct. Each chip can sit on only one row, so placing it on a second row takes it off the first. Answers are hidden until the learner presses Commit; then each row says whether it was matched and shows what the course says that lever changes. Done means all four rows are placed and committed. The correct pairs are anti-retaliation to legal right and remedies, financial reward to the reporter's incentives, mandatory reporting to a duty on the developer, professional duty to escalation as professional conduct. Content ported from XLab's Verification track."
height: auto
tags: [wip]
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Four Levers, One Each</title>
<!-- Ported from XLab Tracks (github.com/XLabTracks/tracks), Verification track widget "whistleblower-levers". -->
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
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0; }
  h1 { font-family: var(--font-heading); font-weight: 600; font-size: 26px; margin: 4px 0 8px; }
  .lede { margin: 0 0 16px; max-width: 46rem; }
  ol.levers { list-style: none; margin: 0; padding: 0; display: grid; gap: 12px; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; }
  .card.is-right { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
  .card.is-wrong { border-color: var(--text); }
  .name { font-weight: 600; margin: 0; }
  .source { color: var(--muted); margin: 8px 0 0; }
  .cite { margin: 4px 0 0; font-size: 12px; }
  .cite a { color: var(--muted); text-decoration: underline; text-underline-offset: 3px; }
  .cite a:hover { color: var(--text); }
  .chips { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 12px; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 8px 12px; cursor: pointer; text-align: left;
  }
  button:hover { background: var(--surface); }
  button:disabled { opacity: 0.5; cursor: default; }
  button:disabled:hover { background: #fff; }
  button.chip { font-size: 12px; padding: 6px 10px; }
  button.chip.is-active { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); background: var(--surface); font-weight: 600; }
  button.chip.is-active::before { content: "\2713\00a0"; color: var(--accent); }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover { background: var(--accent-hover); }
  button.primary:disabled:hover { background: var(--accent); }
  .verdict { margin: 12px 0 0; font-size: 12px; letter-spacing: 0.02em; font-weight: 600; }
  .verdict.is-right { color: var(--accent); }
  .verdict.is-wrong { color: var(--muted); }
  .effect { margin: 6px 0 0; }
  .row { display: flex; flex-wrap: wrap; gap: 12px; align-items: center; justify-content: space-between; margin-top: 16px; }
  .status { font-size: 12px; color: var(--muted); margin: 0; }
  .sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
</style>
</head>
<body>
<p class="eyebrow">Exercise</p>
<h1>Four Levers, One Each</h1>
<p class="lede" id="lede"></p>

<ol class="levers" id="levers" aria-label="Whistleblower mechanisms"></ol>

<div class="row">
  <p class="status" id="status" aria-live="polite"></p>
  <div id="actions"></div>
</div>

<script>
  // Data copied verbatim from XLab's src/lib/verification/data/whistleblower-levers.ts.
  var LEVERS = [
    {
      id: "anti-retaliation",
      name: "Anti-retaliation protection",
      source: "California Labor Code §1107.1 bars specified rules, contracts, and retaliation for protected disclosures.",
      cite: {
        label: "California Labor Code §1107.1",
        href: "https://www.leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?article=&chapter=5.1.&division=2.&lawCode=LAB&part=3.&title="
      },
      effect: "Creates a legal right and remedies after protected reporting.",
      chip: "A legal right and remedies"
    },
    {
      id: "financial-reward",
      name: "Financial reward",
      source: "Wasil et al. propose “financial incentives for verified information.”",
      cite: { label: "Wasil et al.", href: "https://arxiv.org/html/2408.16074" },
      effect: "Changes the reporter’s incentives; it does not establish that the report is true.",
      chip: "The reporter’s incentives"
    },
    {
      id: "mandatory-reporting",
      name: "Mandatory reporting",
      source: "SB 53 says a frontier developer “shall report any critical safety incident … within 15 days.”",
      cite: {
        label: "SB 53, Business and Professions Code §22757.13(c)",
        href: "https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260SB53"
      },
      effect: "Places an affirmative reporting duty on the developer rather than waiting for an insider to volunteer information.",
      chip: "A duty on the developer"
    },
    {
      id: "professional-duty",
      name: "Professional duty",
      source: "The ACM Code gives computing professionals an “obligation to report any signs of system risks that might result in harm.”",
      cite: {
        label: "ACM Code of Ethics §1.2",
        href: "https://www.acm.org/binaries/content/assets/about/acm-code-of-ethics-and-professional-conduct.pdf"
      },
      effect: "Makes escalation part of professional conduct, but supplies neither a safe channel nor a legal remedy on its own.",
      chip: "Escalation as professional conduct"
    }
  ];

  var LEVERS_LEAD = "The sources you have read so far describe four main buckets of mechanisms to protect whistleblowers. Map each mechanism to its main mode of leverage: whether it appeals to personal incentives, places a duty on the AI developer, appeals to upholding professional conduct, or utilizes legal remedies.";

  // Seeded shuffle, ported from XLab's src/lib/shuffle.ts (FNV-1a seed, mulberry32, Fisher-Yates).
  // The chip order is a function of the exercise id, never of the row, so no row is solvable on the diagonal.
  function hashSeed(seed) {
    var h = 0x811c9dc5;
    for (var i = 0; i < seed.length; i++) {
      h ^= seed.charCodeAt(i);
      h = Math.imul(h, 0x01000193);
    }
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
  function seededPermutation(seed, n) {
    var order = [];
    for (var i = 0; i < n; i++) order.push(i);
    var rand = prng(hashSeed(seed));
    for (var k = n - 1; k > 0; k--) {
      var j = Math.floor(rand() * (k + 1));
      var tmp = order[k]; order[k] = order[j]; order[j] = tmp;
    }
    return order;
  }
  function isTerminalOption(text) {
    return /^\s*(none|all|any|neither|both|either)\s+of\s+(the\s+)?(above|these|them)\b/i.test(text);
  }
  function seededShuffle(seed, items, pinned) {
    var n = items.length;
    if (n < 2) return items.slice();
    var fixed = items.map(pinned);
    var movable = [];
    for (var i = 0; i < n; i++) if (!fixed[i]) movable.push(i);
    if (movable.length < 2) return items.slice();
    var perm = seededPermutation(seed, movable.length);
    var reordered = perm.map(function (p) { return movable[p]; });
    var out = [];
    var next = 0;
    for (var slot = 0; slot < n; slot++) {
      var from = fixed[slot] ? slot : reordered[next++];
      out.push(items[from]);
    }
    return out;
  }
  var CHIPS = seededShuffle("whistleblower-levers", LEVERS, function (l) { return isTerminalOption(l.chip); });

  var STORAGE_KEY = "v-whistleblower-levers:v1";
  var ids = {};
  LEVERS.forEach(function (l) { ids[l.id] = true; });

  var placed = {};
  var committed = false;
  var completedOnce = false;

  function prune(raw) {
    var out = {};
    if (typeof raw !== "object" || raw === null) return out;
    LEVERS.forEach(function (lever) {
      var v = raw[lever.id];
      if (typeof v === "string" && ids[v]) out[lever.id] = v;
    });
    return out;
  }
  function placedCount() { return Object.keys(placed).length; }
  function isDone() { return placedCount() === LEVERS.length; }
  function leverById(id) {
    for (var i = 0; i < LEVERS.length; i++) if (LEVERS[i].id === id) return LEVERS[i];
    return null;
  }

  function assign(leverId, effectId) {
    if (committed) return;
    var next = {};
    Object.keys(placed).forEach(function (row) {
      var effect = placed[row];
      if (row !== leverId && effect !== effectId) next[row] = effect;
    });
    next[leverId] = effectId;
    placed = next;
    render();
    persist();
  }

  function summary() {
    var lines = [];
    lines.push(committed
      ? "The learner has committed their matching of four whistleblower mechanisms to modes of leverage."
      : "The learner is matching four whistleblower mechanisms to modes of leverage (" + placedCount() + " of " + LEVERS.length + " placed, not yet committed).");
    LEVERS.forEach(function (lever) {
      var choice = leverById(placed[lever.id]);
      var line = lever.name + ": " + (choice ? "placed on \"" + choice.chip + "\"" : "nothing placed yet");
      if (committed && choice) line += (choice.id === lever.id ? " (correct)" : " (incorrect; the course says: " + lever.effect + ")");
      lines.push(line + ".");
    });
    if (committed) {
      var right = LEVERS.filter(function (l) { return placed[l.id] === l.id; }).length;
      lines.push(right + " of " + LEVERS.length + " matched correctly.");
    }
    return lines.join(" ");
  }

  function persist() {
    var state = { placed: placed, committed: committed };
    if (window.Lens) {
      Lens.saveState(state, summary());
      if (committed && !completedOnce) {
        completedOnce = true;
        Lens.complete();
      }
    } else {
      try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch (e) {}
    }
  }

  var leversEl = document.getElementById("levers");
  var statusEl = document.getElementById("status");
  var actionsEl = document.getElementById("actions");
  document.getElementById("lede").textContent = LEVERS_LEAD;

  function el(tag, cls, text) {
    var node = document.createElement(tag);
    if (cls) node.className = cls;
    if (text != null) node.textContent = text;
    return node;
  }
  function clear(node) { while (node.firstChild) node.removeChild(node.firstChild); }

  function render() {
    clear(leversEl);
    LEVERS.forEach(function (lever) {
      var choice = placed[lever.id];
      var right = choice === lever.id;
      var li = el("li");
      var card = el("div", "card");
      if (committed) card.classList.add(right ? "is-right" : "is-wrong");
      card.appendChild(el("p", "name", lever.name));
      card.appendChild(el("p", "source", lever.source));
      var cite = el("p", "cite");
      var a = el("a", null, lever.cite.label);
      a.href = lever.cite.href;
      a.target = "_blank";
      a.rel = "noopener";
      cite.appendChild(a);
      card.appendChild(cite);

      if (committed) {
        var verdict = el("p", "verdict " + (right ? "is-right" : "is-wrong"),
          (right ? "✓ You matched this one" : "⚠ You put it elsewhere"));
        card.appendChild(verdict);
        card.appendChild(el("p", "effect", lever.effect));
      } else {
        var chips = el("div", "chips");
        chips.setAttribute("role", "group");
        chips.setAttribute("aria-label", "Mode of leverage for " + lever.name);
        CHIPS.forEach(function (option) {
          var active = choice === option.id;
          var b = el("button", "chip" + (active ? " is-active" : ""), option.chip);
          b.type = "button";
          b.id = "chip-" + lever.id + "-" + option.id;
          b.setAttribute("aria-pressed", active ? "true" : "false");
          b.addEventListener("click", function () { assign(lever.id, option.id); });
          chips.appendChild(b);
        });
        card.appendChild(chips);
      }
      li.appendChild(card);
      leversEl.appendChild(li);
    });

    statusEl.textContent = committed
      ? "Each row now carries what the course says it changes."
      : isDone()
        ? "All four placed, commit to see what each one changes."
        : placedCount() + " of " + LEVERS.length + " placed.";

    clear(actionsEl);
    if (committed) {
      var reset = el("button", null, "↺ Start over");
      reset.type = "button";
      reset.id = "start-over";
      reset.addEventListener("click", function () {
        committed = false;
        placed = {};
        render();
        persist();
      });
      actionsEl.appendChild(reset);
    } else {
      var commit = el("button", "primary", "Commit");
      commit.type = "button";
      commit.id = "commit";
      commit.disabled = !isDone();
      commit.addEventListener("click", function () {
        if (!isDone()) return;
        committed = true;
        render();
        persist();
      });
      actionsEl.appendChild(commit);
    }
  }

  function hydrate(saved, meta) {
    if (saved && typeof saved === "object") {
      placed = prune(saved.placed);
      committed = saved.committed === true && isDone();
    }
    if (meta && meta.completed) completedOnce = true;
    render();
  }

  render();
  if (window.Lens) {
    Lens.onState(hydrate);
  } else {
    var raw = null;
    try { raw = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null"); } catch (e) {}
    hydrate(raw, null);
  }
</script>
</body>
</html>

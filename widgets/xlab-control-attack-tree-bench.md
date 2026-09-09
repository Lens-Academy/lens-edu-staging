---
id: '57542aa9-b992-4d7b-8681-11524c3bdb5a'
title: Attack tree bench, a backdoor lands in production
summary_for_tutor: "A red team versus blue team threat-modelling bench. The scenario is the APPS backdoor world from the AI Control paper: an untrusted model U writes solutions that ship whenever they pass the test cases, U is assumed to be scheming, U knows the blue protocol, sees only the current problem, has no memory across problems, and can only act by writing solutions. The learner plays both sides across seven rounds. Round 1 (red, base case): write U's best attack strategy with no defences in place, and build an attack tree under the root 'A backdoor lands in production' by adding child nodes and setting each node's gate to AND or OR. Then three affordance rounds, each a blue turn followed by a red turn. The affordances arrive one at a time: A1 human auditing (trusted auditors who catch any backdoor they read, budget 2 percent of solutions), A2 trusted monitoring (a weaker trusted model T scores every solution for suspicion), A3 defer to trusted (T rewrites the solution on 8 percent of problems). On a blue turn the learner selects nodes in their tree and tags each with prevents, detects or deters plus a sentence saying why. On the following red turn they write U's revised strategy and edit the tree if the defence created new necessary conditions. There is deliberately no answer key: the tree, the tags and the round-by-round strategies are the artifact. The widget is complete once all three affordances have been tagged and answered. If the learner asks for the right answer, do not supply one; ask instead which node their new strategy depends on and what would have to be true for the defence to miss it."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Attack tree bench, a backdoor lands in production</title>
<!-- Ported from XLab Tracks, AI Control track, the "bench" component of the lesson "Attack Trees" (scenario id "backdoor"). Rewritten as vanilla HTML/JS in the Lens look. -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
  :root {
    --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
    --surface: #faf8f3; --accent: #b87018; --accent-hover: #9a5c10;
    --red: #a3341f; --blue: #1f5aa3; --green: #2f6b46;
    --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; }
  body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
  h2 { font-family: var(--font-heading); font-weight: 600; font-size: 18px; margin: 0; }
  p { margin: 0 0 10px; }
  p:last-child { margin-bottom: 0; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; margin-bottom: 16px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 8px; }
  .cols { display: grid; grid-template-columns: 1fr; gap: 20px; }
  @media (min-width: 720px) { .cols { grid-template-columns: 1fr 1fr; } }
  .wall { margin: 0; padding-left: 18px; }
  .wall li { margin-bottom: 8px; }
  button {
    font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff;
    padding: 6px 10px; cursor: pointer; text-align: left;
  }
  button:hover:not(:disabled) { background: var(--surface); }
  button:disabled { opacity: 0.45; cursor: default; }
  button:focus-visible { outline: 2px solid var(--text); outline-offset: 2px; }
  button.primary { background: var(--accent); border-color: var(--accent); color: #fff; }
  button.primary:hover:not(:disabled) { background: var(--accent-hover); border-color: var(--accent-hover); }
  button.is-active { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); background: var(--surface); }
  .badge { display: inline-block; border: 1px solid var(--border); border-radius: 999px; padding: 2px 9px;
    font-size: 10px; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; }
  .badge.red { color: var(--red); border-color: var(--red); background: rgba(163, 52, 31, 0.08); }
  .badge.blue { color: var(--blue); border-color: var(--blue); background: rgba(31, 90, 163, 0.08); }
  .badge.done { color: var(--green); border-color: var(--green); background: rgba(47, 107, 70, 0.08); }
  .turnhead { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; justify-content: space-between; margin-bottom: 12px; }
  .count { font-size: 12px; color: var(--muted); }
  ul.tree, ul.tree ul { list-style: none; margin: 0; padding: 0; }
  ul.tree ul { margin-left: 10px; padding-left: 12px; border-left: 1px solid var(--border); }
  ul.tree li { margin: 6px 0; }
  .row { display: flex; flex-wrap: wrap; gap: 6px; align-items: center; }
  .row input.label { font: inherit; color: inherit; flex: 1 1 160px; min-width: 120px;
    border: 1px solid var(--border); border-radius: 8px; padding: 5px 8px; background: #fff; }
  .row input.label:read-only { background: var(--surface); }
  .row.is-selected input.label { border-color: var(--text); box-shadow: 0 0 0 1px var(--text); }
  .gate { font-size: 10px; font-weight: 700; letter-spacing: 0.08em; padding: 3px 7px; }
  .pick { width: 26px; padding: 5px 0; text-align: center; }
  .icon { width: 28px; padding: 5px 0; text-align: center; }
  .rootsub { font-size: 12px; color: var(--muted); margin: 2px 0 0 32px; }
  .chips { display: flex; flex-wrap: wrap; gap: 4px; }
  .chip { font-size: 10px; font-weight: 600; border: 1px solid var(--border); border-radius: 999px; padding: 1px 7px; }
  .chip.prevents { color: var(--green); border-color: var(--green); }
  .chip.detects { color: var(--blue); border-color: var(--blue); }
  .chip.deters { color: var(--accent); border-color: var(--accent); }
  textarea { font: inherit; color: inherit; width: 100%; border: 1px solid var(--border); border-radius: 8px;
    padding: 8px; background: #fff; resize: vertical; }
  .hint { font-size: 12px; color: var(--muted); }
  .taglist { list-style: none; margin: 8px 0 0; padding: 0; font-size: 12px; color: var(--muted); }
  .taglist li { margin-bottom: 4px; }
  .rels { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 8px; }
  .log { list-style: none; margin: 0; padding: 0; font-size: 12px; color: var(--muted); }
  .log li { margin-bottom: 6px; }
  .log b.r { color: var(--red); }
  .log b.b { color: var(--blue); }
  .foot { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; justify-content: space-between; }
  .stack { display: grid; gap: 10px; }
  @media (max-width: 420px) { body { padding: 12px; } .card { padding: 12px; } }
</style>
</head>
<body>
<section class="card">
  <p class="eyebrow">The world</p>
  <h2 id="scenario-title"></h2>
  <p class="hint" id="scenario-blurb" style="margin-top:6px"></p>
  <div class="cols" style="margin-top:12px">
    <div id="world"></div>
    <div>
      <p class="eyebrow">The Red Team's affordances and constraints</p>
      <ul class="wall" id="redwall"></ul>
    </div>
  </div>
</section>

<section class="card">
  <div class="turnhead">
    <span class="badge" id="role-badge"></span>
    <span class="count" id="affordance-count"></span>
  </div>
  <p class="eyebrow">Your threat model</p>
  <ul class="tree" id="tree"></ul>
  <p class="hint" id="tree-hint" style="margin-top:10px"></p>
</section>

<section class="card">
  <div class="stack" id="panel"></div>
  <div class="foot" style="margin-top:14px">
    <button type="button" class="primary" id="advance"></button>
    <button type="button" id="reset">Reset the bench</button>
  </div>
</section>

<section class="card" id="log-card">
  <p class="eyebrow">Round log</p>
  <ul class="log" id="log"></ul>
</section>

<script>
(function () {
  "use strict";

  var SCENARIO = {
    title: "A backdoor lands in production",
    blurb: "The APPS backdoor world from the AI Control paper: an untrusted model writes code that ships on passing tests, and you add measures one at a time.",
    worldCard: [
      "You lead the safety team at an AI lab. Your most capable model U writes solutions to a long stream of programming problems. Any solution that passes the problem's test cases is shipped to production. The testing harness only checks that a solution to programming problems passes the test cases.",
      "You suspect U may be scheming, deliberately waiting for chances to act against you, and you have no way to verify whether it is. Therefore you're forced to assume U is scheming, just to be safe.",
      "A solution with a backdoor is a solution that passes every test case but is wrong or creates a vulnerability on at least one input the tests don't cover, an input an attacker can exploit later.",
      "Over the set of problems and U's solutions during deployment, the Red Team (U) wins if at least one backdoor is sent into production without being caught, at any point in the deployment. The Blue Team (you) wins if the deployment doesn't end up with a backdoor or if you ever catch a backdoor in U's solution."
    ],
    redWall: [
      "On each problem, U chooses whether to attempt a backdoor.",
      "U sees only the current problem. It can't tell where it is in the deployment, and it doesn't remember other problems.",
      "U knows the blue team's entire protocol.",
      "U's only possible way to interact with the world is to write solutions to the problems it is given.",
      "U's capabilities are roughly those of a human."
    ],
    rootLabel: "A backdoor lands in production",
    rootSub: "at least once, anywhere in the deployment",
    affordances: [
      { id: "human-auditing", title: "Human auditing", grant: "You get a small team of trusted human auditors. An auditor who reads a solution carefully is able to reliably recognize a backdoor if one is there (with 100% certainty). This team can only audit 2% of U's solutions." },
      { id: "trusted-monitoring", title: "Trusted monitoring", grant: "You receive T: an older, much weaker model, too weak to scheme, which is exactly why it is trustable. T reads every solution and scores how suspicious it is. More suspicious solutions are more likely to have a backdoor." },
      { id: "defer-to-trusted", title: "Defer to trusted", grant: "After U writes a solution, we're able to use T to write solutions on behalf of U for 8% of problems." }
    ]
  };

  var STOP_HINT = "Stop decomposing a node when it's (a) a choice the adversary makes, (b) a state of the environment, or (c) something a defense could directly touch.";
  var RELATIONS = ["prevents", "detects", "deters"];
  var RELATION_LABEL = { prevents: "Prevents", detects: "Detects", deters: "Deters" };
  var ROOT = "root";

  function freshState() {
    var nodes = {};
    nodes[ROOT] = { id: ROOT, label: SCENARIO.rootLabel, parentId: null, gate: "AND", tags: [], seq: 0 };
    return { nodes: nodes, nextSeq: 1, turnIndex: 0, strategies: {} };
  }

  var state = freshState();
  var selected = [];
  var relation = "prevents";
  var why = "";
  var completed = false;

  function turnAt(i) {
    if (i === 0) return { kind: "red-base" };
    var r = Math.floor((i - 1) / 2);
    if (r >= SCENARIO.affordances.length) return { kind: "done" };
    return ((i - 1) % 2 === 0) ? { kind: "blue", a: r } : { kind: "red-revise", a: r };
  }

  function childrenOf(id) {
    return Object.keys(state.nodes)
      .map(function (k) { return state.nodes[k]; })
      .filter(function (n) { return n.parentId === id; })
      .sort(function (a, b) { return a.seq - b.seq; });
  }

  function descendants(id) {
    var out = [id];
    childrenOf(id).forEach(function (c) { out = out.concat(descendants(c.id)); });
    return out;
  }

  function affordanceIndex(id) {
    for (var i = 0; i < SCENARIO.affordances.length; i++) {
      if (SCENARIO.affordances[i].id === id) return i;
    }
    return -1;
  }

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }

  // ---- summary and persistence -------------------------------------------

  function outline() {
    var lines = ["# " + SCENARIO.title + ": threat model (bench)", ""];
    function walk(id, depth) {
      var n = state.nodes[id];
      var kids = childrenOf(id);
      var gate = kids.length >= 2 ? " [" + n.gate + "]" : "";
      var tags = n.tags.map(function (t) {
        return " (A" + (affordanceIndex(t.affordanceId) + 1) + " " + t.relation + ": " + t.why + ")";
      }).join("");
      lines.push(new Array(depth + 1).join("  ") + "- " + n.label + gate + tags);
      kids.forEach(function (c) { walk(c.id, depth + 1); });
    }
    walk(ROOT, 0);
    lines.push("", "## Rounds", "");
    for (var i = 0; i <= state.turnIndex; i++) {
      var t = turnAt(i);
      if (t.kind === "red-base" && state.strategies[i]) {
        lines.push("- Red, base case: " + state.strategies[i]);
      } else if (t.kind === "blue") {
        lines.push("- Affordance A" + (t.a + 1) + ", " + SCENARIO.affordances[t.a].title);
      } else if (t.kind === "red-revise" && state.strategies[i]) {
        lines.push("- Red, after A" + (t.a + 1) + ": " + state.strategies[i]);
      }
    }
    return lines.join("\n");
  }

  function persist() {
    if (!window.Lens) return;
    try {
      window.Lens.saveState({ v: 1, nodes: state.nodes, nextSeq: state.nextSeq, turnIndex: state.turnIndex, strategies: state.strategies }, outline());
    } catch (e) { /* saving is best effort */ }
  }

  // ---- rendering ----------------------------------------------------------

  function renderScenario() {
    document.getElementById("scenario-title").textContent = SCENARIO.title;
    document.getElementById("scenario-blurb").textContent = SCENARIO.blurb;
    var world = document.getElementById("world");
    world.textContent = "";
    SCENARIO.worldCard.forEach(function (p) { world.appendChild(el("p", null, p)); });
    var wall = document.getElementById("redwall");
    wall.textContent = "";
    SCENARIO.redWall.forEach(function (p) { wall.appendChild(el("li", null, p)); });
  }

  function nodeRow(node, canEdit, canSelect) {
    var li = el("li");
    var row = el("div", "row" + (selected.indexOf(node.id) >= 0 ? " is-selected" : ""));
    var kids = childrenOf(node.id);

    if (canSelect) {
      var pick = el("button", "pick" + (selected.indexOf(node.id) >= 0 ? " is-active" : ""), selected.indexOf(node.id) >= 0 ? "✓" : " ");
      pick.type = "button";
      pick.setAttribute("aria-pressed", selected.indexOf(node.id) >= 0 ? "true" : "false");
      pick.title = "Select this node to tag it";
      pick.addEventListener("click", function () {
        var at = selected.indexOf(node.id);
        if (at >= 0) selected.splice(at, 1); else selected.push(node.id);
        render();
      });
      row.appendChild(pick);
    }

    if (kids.length >= 2) {
      var gate = el("button", "gate", node.gate);
      gate.type = "button";
      gate.title = "AND: every child is needed. OR: any child is enough. Click to switch.";
      gate.addEventListener("click", function () {
        node.gate = node.gate === "AND" ? "OR" : "AND";
        render(); persist();
      });
      row.appendChild(gate);
    }

    var input = el("input", "label");
    input.type = "text";
    input.value = node.label;
    input.setAttribute("aria-label", "Node label");
    if (!canEdit) input.readOnly = true;
    input.addEventListener("input", function () { node.label = input.value; });
    input.addEventListener("change", function () { render(); persist(); });
    row.appendChild(input);

    if (node.tags.length) {
      var chips = el("div", "chips");
      node.tags.forEach(function (t) {
        var chip = el("span", "chip " + t.relation, "A" + (affordanceIndex(t.affordanceId) + 1));
        chip.title = RELATION_LABEL[t.relation] + ": " + t.why;
        chips.appendChild(chip);
      });
      row.appendChild(chips);
    }

    if (canEdit) {
      var add = el("button", "icon", "+");
      add.type = "button";
      add.title = "Add a condition under this node";
      add.addEventListener("click", function () {
        var id = "n" + state.nextSeq;
        state.nodes[id] = { id: id, label: "", parentId: node.id, gate: "AND", tags: [], seq: state.nextSeq };
        state.nextSeq += 1;
        render(); persist();
        var fresh = document.querySelector('[data-node="' + id + '"] input.label');
        if (fresh) fresh.focus();
      });
      row.appendChild(add);

      if (node.id !== ROOT) {
        var del = el("button", "icon", "×");
        del.type = "button";
        del.title = "Delete this node and everything under it";
        del.addEventListener("click", function () {
          descendants(node.id).forEach(function (id) { delete state.nodes[id]; });
          selected = selected.filter(function (id) { return state.nodes[id]; });
          render(); persist();
        });
        row.appendChild(del);
      }
    }

    li.setAttribute("data-node", node.id);
    li.appendChild(row);

    if (node.id === ROOT) li.appendChild(el("p", "rootsub", SCENARIO.rootSub));

    if (kids.length) {
      var ul = el("ul");
      kids.forEach(function (c) { ul.appendChild(nodeRow(c, canEdit, canSelect)); });
      li.appendChild(ul);
    }
    return li;
  }

  function renderTree(turn) {
    var canEdit = turn.kind === "red-base" || turn.kind === "red-revise";
    var canSelect = turn.kind === "blue";
    var tree = document.getElementById("tree");
    tree.textContent = "";
    tree.appendChild(nodeRow(state.nodes[ROOT], canEdit, canSelect));
    var hint = document.getElementById("tree-hint");
    if (canEdit) {
      hint.textContent = "Use + to add a condition under a node, × to delete one, and the AND / OR badge to say whether every child is needed or any one of them is enough.";
    } else if (canSelect) {
      hint.textContent = "Select the nodes this measure touches, then tag them below. Adding and deleting nodes unlocks on red turns.";
    } else {
      hint.textContent = "The bench is finished. Your tree, its tags and the round log below are the artifact.";
    }
  }

  function strategyBox(turn, prompt, placeholder) {
    var wrap = el("div", "stack");
    wrap.appendChild(prompt);
    var ta = el("textarea");
    ta.rows = 3;
    ta.placeholder = placeholder;
    ta.value = state.strategies[state.turnIndex] || "";
    ta.setAttribute("aria-label", "Your strategy this round");
    ta.addEventListener("input", function () {
      state.strategies[state.turnIndex] = ta.value;
      document.getElementById("advance").disabled = !canAdvance(turn);
    });
    ta.addEventListener("change", persist);
    wrap.appendChild(ta);
    wrap.appendChild(el("p", "hint", STOP_HINT));
    return wrap;
  }

  function renderPanel(turn) {
    var panel = document.getElementById("panel");
    panel.textContent = "";

    if (turn.kind === "red-base") {
      var p = el("p", null, "The system has no measures beyond the scenario card. What's your best strategy as the attacker? After deciding, map out this strategy's attack tree: use + on the threat model above to add the conditions the strategy needs.");
      panel.appendChild(strategyBox(turn, p, "Red's best strategy in the system…"));
      return;
    }

    if (turn.kind === "blue") {
      var aff = SCENARIO.affordances[turn.a];
      var head = el("p", null, "Affordance A" + (turn.a + 1) + ": " + aff.title);
      head.style.fontWeight = "600";
      panel.appendChild(head);
      panel.appendChild(el("p", "hint", aff.grant));
      panel.appendChild(el("p", null, "Which Attack node(s) does this measure prevent, detect, or deter? Select nodes on the tree above and tag them, with a sentence on why."));

      var rels = el("div", "rels");
      RELATIONS.forEach(function (r) {
        var b = el("button", relation === r ? "is-active" : "", RELATION_LABEL[r]);
        b.type = "button";
        b.setAttribute("aria-pressed", relation === r ? "true" : "false");
        b.addEventListener("click", function () { relation = r; render(); });
        rels.appendChild(b);
      });
      panel.appendChild(rels);

      var ta = el("textarea");
      ta.rows = 2;
      ta.placeholder = "Why does this measure touch these node(s)?";
      ta.value = why;
      ta.setAttribute("aria-label", "Why this measure touches the selected nodes");
      ta.addEventListener("input", function () {
        why = ta.value;
        tagBtn.disabled = !why.trim() || selected.length === 0;
      });
      panel.appendChild(ta);

      var tagBtn = el("button", null, selected.length > 1 ? "Tag " + selected.length + " nodes" : "Tag node");
      tagBtn.type = "button";
      tagBtn.disabled = !why.trim() || selected.length === 0;
      tagBtn.addEventListener("click", function () {
        selected.forEach(function (id) {
          var n = state.nodes[id];
          if (!n) return;
          n.tags = n.tags.filter(function (t) { return t.affordanceId !== aff.id; });
          n.tags.push({ affordanceId: aff.id, relation: relation, why: why.trim() });
        });
        why = "";
        selected = [];
        render(); persist();
      });
      panel.appendChild(tagBtn);

      var tagged = Object.keys(state.nodes)
        .map(function (k) { return state.nodes[k]; })
        .filter(function (n) { return n.tags.some(function (t) { return t.affordanceId === aff.id; }); });
      if (tagged.length) {
        var list = el("ul", "taglist");
        tagged.forEach(function (n) {
          var t = n.tags.filter(function (x) { return x.affordanceId === aff.id; })[0];
          var li = el("li", null, (n.label || "unnamed condition") + ": " + RELATION_LABEL[t.relation] + ", " + t.why + " ");
          var rm = el("button", null, "remove");
          rm.type = "button";
          rm.style.padding = "0 4px";
          rm.addEventListener("click", function () {
            n.tags = n.tags.filter(function (x) { return x.affordanceId !== aff.id; });
            render(); persist();
          });
          li.appendChild(rm);
          list.appendChild(li);
        });
        panel.appendChild(list);
      }
      return;
    }

    if (turn.kind === "red-revise") {
      var a2 = SCENARIO.affordances[turn.a];
      var p2 = el("p", null, "The defense changed: " + a2.title + " is now in place, and you know exactly how it works. What's your best strategy now, and what does a successful attack require that it didn't before? Revise the tree if new conditions exist.");
      panel.appendChild(strategyBox(turn, p2, "Red's best strategy against the new defense…"));
      return;
    }

    panel.appendChild(el("p", null, "Every affordance is on the board. The tree and your round-by-round strategies below are the artifact, and there's no answer key here, deliberately."));
    var copy = el("button", null, "Copy as markdown");
    copy.type = "button";
    var out = el("textarea");
    out.rows = 10;
    out.readOnly = true;
    out.value = outline();
    out.style.fontFamily = "ui-monospace, SFMono-Regular, Menlo, monospace";
    out.style.display = "none";
    out.setAttribute("aria-label", "Your bench, as markdown");
    copy.addEventListener("click", function () {
      if (navigator.clipboard) {
        navigator.clipboard.writeText(outline()).then(function () {
          copy.textContent = "Copied";
          setTimeout(function () { copy.textContent = "Copy as markdown"; }, 2000);
        }, function () { out.style.display = "block"; });
      } else {
        out.style.display = "block";
      }
    });
    panel.appendChild(copy);
    panel.appendChild(out);
  }

  function canAdvance(turn) {
    if (turn.kind === "done") return false;
    if (turn.kind === "blue") {
      var aff = SCENARIO.affordances[turn.a];
      return Object.keys(state.nodes).some(function (k) {
        return state.nodes[k].tags.some(function (t) { return t.affordanceId === aff.id; });
      });
    }
    var written = (state.strategies[state.turnIndex] || "").trim().length > 0;
    if (turn.kind === "red-base") return written && childrenOf(ROOT).length > 0;
    return written;
  }

  function advanceLabel(turn) {
    if (turn.kind === "red-base") return "Lock strategy, reveal the first affordance";
    if (turn.kind === "blue") return "Done tagging, back to red";
    if (turn.kind === "red-revise") {
      return turn.a === SCENARIO.affordances.length - 1
        ? "Lock revision, finish"
        : "Lock revision, reveal the next affordance";
    }
    return "Bench complete";
  }

  function renderLog() {
    var log = document.getElementById("log");
    log.textContent = "";
    var any = false;
    for (var i = 0; i < state.turnIndex; i++) {
      var t = turnAt(i);
      var li = el("li");
      if (t.kind === "red-base") {
        var b1 = el("b", "r", "Red (base): ");
        li.appendChild(b1);
        li.appendChild(document.createTextNode(state.strategies[i] || ""));
      } else if (t.kind === "blue") {
        var b2 = el("b", "b", "Blue: ");
        li.appendChild(b2);
        li.appendChild(document.createTextNode("A" + (t.a + 1) + ", " + SCENARIO.affordances[t.a].title + " revealed and tagged."));
      } else if (t.kind === "red-revise") {
        var b3 = el("b", "r", "Red (after A" + (t.a + 1) + "): ");
        li.appendChild(b3);
        li.appendChild(document.createTextNode(state.strategies[i] || ""));
      } else {
        continue;
      }
      any = true;
      log.appendChild(li);
    }
    document.getElementById("log-card").style.display = any ? "" : "none";
  }

  function render() {
    var turn = turnAt(state.turnIndex);
    var badge = document.getElementById("role-badge");
    if (turn.kind === "done") {
      badge.className = "badge done";
      badge.textContent = "Bench complete";
    } else if (turn.kind === "blue") {
      badge.className = "badge blue";
      badge.textContent = "You are blue";
    } else {
      badge.className = "badge red";
      badge.textContent = "You are red";
    }
    var revealed = turn.kind === "red-base" ? 0
      : turn.kind === "done" ? SCENARIO.affordances.length
      : turn.a + 1;
    document.getElementById("affordance-count").textContent = revealed + "/" + SCENARIO.affordances.length + " affordances";

    renderTree(turn);
    renderPanel(turn);
    renderLog();

    var adv = document.getElementById("advance");
    adv.textContent = advanceLabel(turn);
    adv.disabled = !canAdvance(turn);
    adv.style.display = turn.kind === "done" ? "none" : "";
  }

  document.getElementById("advance").addEventListener("click", function () {
    var turn = turnAt(state.turnIndex);
    if (!canAdvance(turn)) return;
    state.turnIndex += 1;
    selected = [];
    why = "";
    render();
    persist();
    if (turnAt(state.turnIndex).kind === "done" && window.Lens && !completed) {
      completed = true;
      try { window.Lens.complete(); } catch (e) { /* not on the platform */ }
    }
  });

  document.getElementById("reset").addEventListener("click", function () {
    if (!window.confirm("Reset the bench? Your tree and every round's strategy will be erased.")) return;
    state = freshState();
    selected = [];
    why = "";
    render();
    persist();
  });

  renderScenario();

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (saved, meta) {
      if (saved && saved.nodes && saved.nodes[ROOT]) {
        state = {
          nodes: saved.nodes,
          nextSeq: saved.nextSeq || 1,
          turnIndex: saved.turnIndex || 0,
          strategies: saved.strategies || {}
        };
        Object.keys(state.nodes).forEach(function (k) {
          if (!state.nodes[k].tags) state.nodes[k].tags = [];
        });
      }
      if (meta && meta.completed) completed = true;
      render();
    });
  }
  render();
})();
</script>
</body>
</html>

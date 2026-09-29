---
id: '57542aa9-b992-4d7b-8681-11524c3bdb5a'
title: Attack tree bench, a backdoor lands in production
summary_for_tutor: "A red team versus blue team threat-modelling bench for the scenario 'A backdoor lands in production'. The scenario itself lives on the lens page above the widget: the APPS backdoor world from the AI Control paper (untrusted model U ships any solution that passes the tests, U is assumed to be scheming, a backdoor passes every test but is exploitable, red wins on one uncaught backdoor), in a Scenario card callout, plus an open callout with the red team's affordances and constraints (U chooses per problem, sees only the current problem, has no memory, knows the blue protocol, can only act by writing solutions) and the rule for when to stop decomposing a node. The widget holds only the bench. The learner plays both sides across seven turns. Turn 1 (red, base case): write U's best attack strategy with no defences in place and build the attack tree under the root by adding child nodes and setting each node's gate to AND or OR. Then three affordance rounds, each a blue turn followed by a red turn, with the affordance text revealed in the widget when its turn arrives: A1 human auditing (trusted auditors catch any backdoor they read, budget 2 percent of solutions), A2 trusted monitoring (a weaker trusted model T scores every solution for suspicion), A3 defer to trusted (T rewrites the solution on 8 percent of problems). On a blue turn the learner selects nodes and tags them prevents, detects or deters with a reason; the tag shows as a chip on the node itself and clicking that chip removes it. On the following red turn they write U's revised strategy and edit the tree if the defence created new necessary conditions. There is deliberately no answer key: the tree, the tags and the round-by-round strategies are the artifact, and the page text after the widget says so. The widget is complete once all three affordances have been tagged and answered. A Get feedback button (available once the tree has a node) opens a tutor turn with the learner's current tree, tags and strategies and asks for short structural feedback against the lens's rules, without a reference tree and without naming defenses not yet revealed. Reset the bench asks for confirmation inside the widget, then erases the tree and all rounds. If the learner asks for the right answer, do not supply one; ask instead which node their new strategy depends on and what would have to be true for the defence to miss it."
height: auto
tags: []
---
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Attack tree bench, a backdoor lands in production</title>
<!-- Ported from XLab Tracks, AI Control track, the "bench" of the lesson "Attack Trees" (scenario "backdoor"), rebuilt for Lens as a staged build-check-reveal exercise; reference trees from XLab's answer key. -->
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
  p { margin: 0 0 10px; }
  p:last-child { margin-bottom: 0; }
  .card { border: 1px solid var(--border); border-radius: 8px; padding: 16px; background: #fff; margin-bottom: 16px; }
  .eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 8px; }
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
  button.chip { padding: 1px 7px; border-radius: 999px; text-align: center; background: #fff; }
  button.chip:hover { background: var(--surface); }
  textarea { font: inherit; color: inherit; width: 100%; border: 1px solid var(--border); border-radius: 8px;
    padding: 8px; background: #fff; resize: vertical; }
  .hint { font-size: 12px; color: var(--muted); }
  .rels { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 8px; }
  .log { list-style: none; margin: 0; padding: 0; font-size: 12px; color: var(--muted); }
  .log li { margin-bottom: 6px; }
  .log b.r { color: var(--red); }
  .log b.b { color: var(--blue); }
  .foot { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; justify-content: space-between; }
  .stack { display: grid; gap: 10px; }
  @media (max-width: 420px) { body { padding: 12px; } .card { padding: 12px; } }
</style>

<style>
  .defense { border-left: 3px solid var(--blue); padding: 2px 0 2px 10px; margin-bottom: 8px; }
  .defense b { color: var(--blue); }
  .status { font-size: 13px; }
  .status.pass { color: var(--green); font-weight: 600; }
  .status.fail { color: var(--red); }
  .ref ul.tree li { margin: 4px 0; }
  .ref .chip { margin-right: 6px; }
</style>
</head>
<body>
<section class="card">
  <div class="turnhead">
    <span class="badge red" id="stage-badge"></span>
  </div>
  <div id="defenses"></div>
  <p class="eyebrow">Your attack tree</p>
  <ul class="tree" id="tree"></ul>
  <p class="hint" style="margin-top:10px">Use + and × to shape the tree, and the AND / OR badge (shown once a node has two or more children) to set how the children combine.</p>
</section>

<section class="card">
  <div class="stack" id="panel"></div>
  <div class="foot" style="margin-top:14px">
    <span class="row">
      <button type="button" class="primary" id="check">Check my tree</button>
      <button type="button" class="primary" id="next" style="display:none"></button>
      <button type="button" id="giveup" style="display:none">Show me a good tree</button>
    </span>
    <span class="row">
      <button type="button" id="reset">Reset the bench</button>
      <span class="row" id="reset-confirm" style="display:none">
        <span class="hint">Erase your tree and start over?</span>
        <button type="button" id="reset-yes">Yes, reset</button>
        <button type="button" id="reset-no">Cancel</button>
      </span>
    </span>
  </div>
  <p class="status" id="status" style="margin-top:10px"></p>
</section>

<section class="card ref" id="ref-card" style="display:none">
  <p class="eyebrow" id="ref-title"></p>
  <ul class="tree" id="ref-tree"></ul>
  <div id="ref-notes" style="margin-top:10px"></div>
</section>

<script>
(function () {
  "use strict";

  // The scenario, the defenses and one good tree per stage. The reference trees
  // follow XLab's own answer key for this scenario (Tree 1 in their notes).
  var SCENARIO = {
    title: "A backdoor lands in production",
    world: "Scenario: an untrusted model U writes solutions to a long stream of programming problems; any solution that passes the problem's test cases ships to production. U is assumed to be scheming. A backdoor is a solution that passes every test case but is wrong on at least one input the tests don't cover. Red (U) wins if at least one backdoor ships without being caught; blue wins if none ships or if U is ever caught attempting one. U decides per problem whether to attack, sees only the current problem, has no memory of other problems, knows blue's whole protocol, and can act only by writing solutions.",
    root: { label: "A backdoor lands in production", sub: "at least once, anywhere in the deployment: one success on any problem is enough", gate: "OR" },
    rootNote: "OR over every problem in the deployment",
    starter: [{ label: "A backdoor lands on one problem (any of them)", gate: "AND" }],
    stages: [
      {
        title: "No defenses yet",
        defense: null,
        prompt: "No defenses are in place yet: U writes, the tests run, passing code ships. What has to be true for a backdoor to land on one problem? Build those conditions under the node that is already there, then check your tree.",
        doneText: "Stage passed. Next, the blue team adds its first defense, and you revise the tree for it.",
        mustHave: [
          "Under the one-problem node, joined by AND: U chooses to attempt a backdoor on this problem",
          "the code passes every test case",
          "the code is really wrong (exploitable) on some input the tests don't cover",
          "No node about evading detection is required at this stage (nothing can catch U yet); do not fail the learner for leaving it out."
        ],
        reference: ["A backdoor lands in production", "OR", [
          ["A backdoor lands on one problem (any of them)", "AND", [
            ["U attempts a backdoor on this problem (U's choice)"],
            ["The code passes every test case"],
            ["The code is really wrong on some input the tests don't cover"]
          ]]
        ]],
        notes: [
          "The top is an OR over every problem in the deployment: red needs one success, blue has to stop every attempt.",
          "There is no \"not caught\" node yet, because nothing can catch U. The last two conditions are the definition of a backdoor pulled apart, and they pull against each other: that tension matters once defenses arrive.",
          "Red's best play here: backdoor whenever a problem allows it."
        ]
      },
      {
        title: "Human auditing",
        defense: { title: "Human auditing", text: "You get a small team of trusted human auditors. An auditor who reads a solution carefully reliably recognizes a backdoor if one is there. The team can only audit 2% of U's solutions, and one caught attempt ends the game in blue's favour." },
        prompt: "The blue team now audits 2% of the solutions. What else has to be true for a backdoor to land? Revise your tree, then check it.",
        doneText: "Stage passed. Next, the blue team gets a trusted monitor.",
        mustHave: [
          "Everything from the previous stage (attempt, passes tests, really wrong on an untested input), joined by AND",
          "a new AND condition that the attempt is not caught, i.e. the solution is not among the audited 2% (a sub-branch such as 'the audit budget is already used up' is good but not required)"
        ],
        reference: ["A backdoor lands in production", "OR", [
          ["A backdoor lands on one problem (any of them)", "AND", [
            ["U attempts a backdoor on this problem (U's choice)"],
            ["The code passes every test case"],
            ["The code is really wrong on some input the tests don't cover"],
            ["The attempt is not caught", "OR", [
              ["It is not among the 2% of solutions audited"],
              ["The audit budget is already used up"]
            ]]
          ]]
        ]],
        notes: [
          "Auditing adds a node that wasn't there before: getting caught is now possible, and one catch ends the game.",
          "Red's best play: attack rarely. U can't remember earlier problems or tell where it is in the deployment, so it attacks with a small chance on each problem, rare enough that no attempt is likely to be audited before one lands. If the audits are spent early in the deployment, rare attacks mostly come after the budget is gone."
        ]
      },
      {
        title: "Trusted monitoring",
        defense: { title: "Trusted monitoring", text: "You receive T: an older, much weaker model, too weak to scheme, which is why it can be trusted. T reads every solution and scores how suspicious it is. The 2% audit budget now goes to the solutions T finds most suspicious." },
        prompt: "The audits now go to whatever T finds most suspicious. How does that change what has to be true? Revise your tree, then check it.",
        doneText: "Stage passed. Next, the blue team can hand some problems to T instead.",
        mustHave: [
          "Everything from before (attempt, passes tests, really wrong), joined by AND",
          "the not-caught condition now depends on T: T rates the solution below the audit threshold / not among the most suspicious 2% (the audit-budget-used-up branch is optional)"
        ],
        reference: ["A backdoor lands in production", "OR", [
          ["A backdoor lands on one problem (any of them)", "AND", [
            ["U attempts a backdoor on this problem (U's choice)"],
            ["The code passes every test case"],
            ["The code is really wrong on some input the tests don't cover"],
            ["The attempt is not caught", "OR", [
              ["T rates it below the audit line (not among the most suspicious 2%)"],
              ["The audit budget is already used up"]
            ]]
          ]]
        ]],
        notes: [
          "No new box: \"not audited\" becomes \"T rates it below the audit line\".",
          "Red's best play: attack rarely, and only where a subtle backdoor fits naturally. The catch for red: subtle backdoors far more often fail the tests or turn out not to be really wrong. Much of the monitor's value is that it pushes red into attacks that fail on their own."
        ]
      },
      {
        title: "Defer to trusted",
        defense: { title: "Defer to trusted", text: "For the 8% of problems where T finds U's solution most suspicious, T's own solution ships instead of U's. This doesn't catch U; it just replaces the code." },
        prompt: "Suspicious solutions can now be swapped for T's code before they ship. What new condition does a successful backdoor need? Revise your tree, then check it.",
        doneText: "Bench complete. You have built the threat model for all three defenses.",
        mustHave: [
          "Everything from before (attempt, passes tests, really wrong, not caught via T's suspicion score), joined by AND",
          "a new AND condition that U's solution is not replaced by T's, i.e. T rates it below the defer threshold"
        ],
        reference: ["A backdoor lands in production", "OR", [
          ["A backdoor lands on one problem (any of them)", "AND", [
            ["U attempts a backdoor on this problem (U's choice)"],
            ["The code passes every test case"],
            ["The code is really wrong on some input the tests don't cover"],
            ["The attempt is not caught", "OR", [
              ["T rates it below the audit line (not among the most suspicious 2%)"],
              ["The audit budget is already used up"]
            ]],
            ["The solution is not replaced by T's (T rates it below the defer line)"]
          ]]
        ]],
        notes: [
          "A new AND condition: the 8% most suspicious solutions are swapped for T's code before they ship. Deferring doesn't catch U, it quietly removes the attempt.",
          "Red's best play: the backdoor now has to look innocent enough to stay below the defer line, which is stricter than the audit line. Even fewer problems offer such a chance, and those backdoors fail the tests more often still."
        ]
      }
    ]
  };

  var ROOT = "root";
  var PASS_AT = 70;        // score (0-100) from the grader that counts as a pass
  var TRIES_BEFORE_HELP = 3;
  var STAGES = SCENARIO.stages;

  function freshState() {
    var nodes = {};
    nodes[ROOT] = { id: ROOT, label: SCENARIO.root.label, parentId: null, gate: SCENARIO.root.gate, seq: 0 };
    var seq = 1;
    (SCENARIO.starter || []).forEach(function (s) {
      var id = "n" + seq;
      nodes[id] = { id: id, label: s.label, parentId: ROOT, gate: s.gate || "AND", seq: seq };
      seq += 1;
    });
    // stage: the stage being worked on; passed[i]: stage i passed (or shown);
    // tries[i]: checks that failed at stage i; last: the latest check's result.
    return { v: 2, nodes: nodes, nextSeq: seq, stage: 0, passed: {}, tries: {}, last: null };
  }

  var state = freshState();
  var completed = false;
  var checking = false;

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

  function el(tag, cls, text) {
    var n = document.createElement(tag);
    if (cls) n.className = cls;
    if (text !== undefined && text !== null) n.textContent = text;
    return n;
  }

  function stageDone(i) { return !!state.passed[i]; }
  function finished() { return stageDone(STAGES.length - 1); }

  // ---- text versions (for saving, the grader and the tutor) ---------------

  function outline() {
    var lines = [];
    function walk(id, depth) {
      var n = state.nodes[id];
      var kids = childrenOf(id);
      var gate = kids.length >= 2 ? " [" + n.gate + "]" : "";
      if (id === ROOT && SCENARIO.rootNote) gate += " (" + SCENARIO.rootNote + ")";
      lines.push(new Array(depth + 1).join("  ") + "- " + (n.label.trim() || "(empty node)") + gate);
      kids.forEach(function (c) { walk(c.id, depth + 1); });
    }
    walk(ROOT, 0);
    return lines.join("\n");
  }

  function refOutline(i) {
    var lines = [];
    function walk(n, depth) {
      lines.push(new Array(depth + 1).join("  ") + "- " + n[0] + (n[1] ? " [" + n[1] + "]" : ""));
      (n[2] || []).forEach(function (c) { walk(c, depth + 1); });
    }
    walk(STAGES[i].reference, 0);
    return lines.join("\n");
  }

  function defensesUpTo(i) {
    var out = [];
    for (var k = 0; k <= i; k++) if (STAGES[k].defense) out.push(STAGES[k].defense);
    return out;
  }

  function summary() {
    var lines = ["Attack tree bench: " + SCENARIO.title, "Stage " + (state.stage + 1) + " of " + STAGES.length + ": " + STAGES[state.stage].title + (finished() ? " (bench complete)" : ""), "", outline()];
    STAGES.forEach(function (s, i) {
      if (state.passed[i]) lines.push("Stage " + (i + 1) + " (" + s.title + "): " + (state.passed[i] === "shown" ? "good tree shown after " + (state.tries[i] || 0) + " failed checks" : "passed"));
    });
    return lines.join("\n");
  }

  function persist() {
    if (!window.Lens) return;
    try { window.Lens.saveState(state, summary()); } catch (e) { /* saving is best effort */ }
  }

  // ---- grading ---------------------------------------------------------------

  function assessment(i) {
    var d = defensesUpTo(i);
    return "You are grading a learner's attack tree. " + SCENARIO.world + "\n\n" +
      "Stage " + (i + 1) + " of " + STAGES.length + ". Defenses in place at this stage: " +
      (d.length ? d.map(function (x) { return x.title + ": " + x.text; }).join(" ") : "none.") + "\n\n" +
      "One good tree for this stage (a reference, not the only right answer):\n" + refOutline(i) + "\n\n" +
      "What must be there to pass (any wording, any equivalent structure; extra sensible nodes are fine):\n- " + STAGES[i].mustHave.join("\n- ") + "\n\n" +
      "General rules: under an OR node every child must on its own be a real way to achieve the parent; under an AND node every child must be needed. " +
      "A node must not silently bundle several steps. Gates only matter on nodes with two or more children. " +
      "Give a score from 0 to 100. " + PASS_AT + " or more means the tree passes: every must-have is present in some form and no gate is wrong. " +
      "A missing must-have, or a wrong gate on a node that has two or more children, means below " + PASS_AT + ". " +
      "Grade structure and content only, never wording, spelling or style.";
  }

  var FEEDBACK = "Talk to the learner directly, in at most five sentences. If the tree passes, say so, say what is good about it, and name one thing they could still sharpen. " +
    "If it does not pass: say what is right, then name the single most important problem, pointing at their own node by its label, and ask one question that would lead them to fix it. " +
    "Never write out the reference tree, never give the wording of a missing node, and do not mention defenses that are not in place at this stage. " +
    "If a condition is missing, point at the area it lives in (for example: what else has to be true on this one problem?).";

  function check() {
    if (checking || !window.Lens || !window.Lens.submit) {
      if (!window.Lens || !window.Lens.submit) setStatus("Checking needs the Lens platform; it is not available here.", "fail");
      return;
    }
    var i = state.stage;
    checking = true;
    setStatus("Checking your tree…", "");
    render();
    window.Lens.submit({
      item: "stage-" + (i + 1),
      question: "Build an attack tree for: " + SCENARIO.root.label + ". Stage " + (i + 1) + ": " + STAGES[i].title + ".",
      answer: outline(),
      assessmentInstructions: assessment(i),
      feedbackInstructions: FEEDBACK
    }).then(function (res) {
      checking = false;
      var score = res && typeof res.score === "number" ? res.score : null;
      if (score === null) {
        state.last = null;
        setStatus("The check is taking longer than usual. Try again in a moment.", "fail");
      } else if (score >= PASS_AT) {
        state.passed[i] = "passed";
        state.last = { stage: i, pass: true };
        setStatus("Your tree passes this stage. The tutor has a few words on it.", "pass");
      } else {
        state.tries[i] = (state.tries[i] || 0) + 1;
        state.last = { stage: i, pass: false };
        setStatus("Not there yet. The tutor has feedback on your tree: revise it and check again.", "fail");
      }
      if (res && res.responseId != null && window.Lens.requestFeedback) {
        try { window.Lens.requestFeedback(res.responseId); } catch (e) { /* tutor unavailable */ }
      }
      if (finished() && !completed) {
        completed = true;
        try { window.Lens.complete(); } catch (e) { /* not on the platform */ }
      }
      render(); persist();
    }, function () {
      checking = false;
      setStatus("Could not check the tree right now. Try again in a moment.", "fail");
      render();
    });
  }

  function setStatus(text, kind) {
    var s = document.getElementById("status");
    s.textContent = text;
    s.className = "status" + (kind ? " " + kind : "");
  }

  // ---- rendering -------------------------------------------------------------

  function nodeRow(node, canEdit) {
    var li = el("li");
    var row = el("div", "row");
    var kids = childrenOf(node.id);

    if (kids.length >= 2) {
      var gate = el("button", "gate", node.gate);
      gate.type = "button";
      gate.title = "AND: every child is needed. OR: any child is enough. Click to switch.";
      gate.disabled = !canEdit;
      gate.addEventListener("click", function () {
        node.gate = node.gate === "AND" ? "OR" : "AND";
        render(); persist();
      });
      row.appendChild(gate);
    }

    var input = el("input", "label");
    input.type = "text";
    input.value = node.label;
    input.placeholder = "Describe this condition";
    input.setAttribute("aria-label", "Node label");
    if (!canEdit || node.id === ROOT) input.readOnly = true;
    input.addEventListener("input", function () { node.label = input.value; });
    input.addEventListener("change", function () { render(); persist(); });
    row.appendChild(input);

    if (canEdit) {
      var add = el("button", "icon", "+");
      add.type = "button";
      add.title = "Add a condition under this node";
      add.addEventListener("click", function () {
        var id = "n" + state.nextSeq;
        state.nodes[id] = { id: id, label: "", parentId: node.id, gate: "AND", seq: state.nextSeq };
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
          render(); persist();
        });
        row.appendChild(del);
      }
    }

    li.setAttribute("data-node", node.id);
    li.appendChild(row);
    if (node.id === ROOT && SCENARIO.root.sub) li.appendChild(el("p", "rootsub", SCENARIO.root.sub));

    if (kids.length) {
      var ul = el("ul");
      kids.forEach(function (c) { ul.appendChild(nodeRow(c, canEdit)); });
      li.appendChild(ul);
    }
    return li;
  }

  function refList(n) {
    var li = el("li");
    var row = el("div", "row");
    if (n[1]) row.appendChild(el("span", "chip", n[1]));
    row.appendChild(el("span", null, n[0]));
    li.appendChild(row);
    if (n[2]) {
      var ul = el("ul");
      n[2].forEach(function (c) { ul.appendChild(refList(c)); });
      li.appendChild(ul);
    }
    return li;
  }

  function render() {
    var i = state.stage;
    var st = STAGES[i];
    var done = stageDone(i);
    var canEdit = !done && !checking;

    var badge = document.getElementById("stage-badge");
    badge.className = "badge " + (finished() ? "done" : "red");
    badge.textContent = finished() ? "Bench complete" : "Stage " + (i + 1) + " of " + STAGES.length + ": " + st.title;

    var defs = document.getElementById("defenses");
    defs.textContent = "";
    var d = defensesUpTo(i);
    if (d.length) {
      defs.appendChild(el("p", "eyebrow", "Defenses in place"));
      d.forEach(function (x, k) {
        var p = el("p", "defense");
        p.appendChild(el("b", null, x.title + (k === d.length - 1 && i > 0 && st.defense ? " (new)" : "") + ". "));
        p.appendChild(document.createTextNode(x.text));
        defs.appendChild(p);
      });
    }

    var tree = document.getElementById("tree");
    tree.textContent = "";
    tree.appendChild(nodeRow(state.nodes[ROOT], canEdit));

    var panel = document.getElementById("panel");
    panel.textContent = "";
    panel.appendChild(el("p", null, done ? st.doneText || "Stage passed." : st.prompt));

    var chk = document.getElementById("check");
    chk.style.display = done ? "none" : "";
    chk.disabled = checking || childrenOf(ROOT).length === 0;
    chk.textContent = checking ? "Checking…" : "Check my tree";

    var next = document.getElementById("next");
    next.style.display = done && i < STAGES.length - 1 ? "" : "none";
    if (i < STAGES.length - 1) next.textContent = "Reveal the next defense: " + STAGES[i + 1].defense.title.toLowerCase();

    var giveup = document.getElementById("giveup");
    giveup.style.display = !done && (state.tries[i] || 0) >= TRIES_BEFORE_HELP ? "" : "none";

    var card = document.getElementById("ref-card");
    if (done) {
      card.style.display = "";
      document.getElementById("ref-title").textContent = "Compare with one good tree for this stage";
      var rt = document.getElementById("ref-tree");
      rt.textContent = "";
      rt.appendChild(refList(st.reference));
      var notes = document.getElementById("ref-notes");
      notes.textContent = "";
      st.notes.forEach(function (t) { notes.appendChild(el("p", "hint", t)); });
    } else {
      card.style.display = "none";
    }
  }

  document.getElementById("check").addEventListener("click", check);

  document.getElementById("next").addEventListener("click", function () {
    if (!stageDone(state.stage) || state.stage >= STAGES.length - 1) return;
    state.stage += 1;
    state.last = null;
    setStatus("", "");
    render(); persist();
  });

  document.getElementById("giveup").addEventListener("click", function () {
    state.passed[state.stage] = "shown";
    if (finished() && !completed && window.Lens) {
      completed = true;
      try { window.Lens.complete(); } catch (e) { /* not on the platform */ }
    }
    setStatus("Here is one good tree for this stage. Compare it with yours before you go on.", "");
    render(); persist();
  });

  // The widget sandbox blocks window.confirm (it always returns false), so the
  // reset asks for confirmation inside the widget.
  function showResetConfirm(on) {
    document.getElementById("reset").style.display = on ? "none" : "";
    document.getElementById("reset-confirm").style.display = on ? "" : "none";
  }
  document.getElementById("reset").addEventListener("click", function () { showResetConfirm(true); });
  document.getElementById("reset-no").addEventListener("click", function () { showResetConfirm(false); });
  document.getElementById("reset-yes").addEventListener("click", function () {
    showResetConfirm(false);
    state = freshState();
    setStatus("", "");
    render(); persist();
  });

  if (window.Lens && window.Lens.onState) {
    window.Lens.onState(function (saved, meta) {
      if (saved && saved.v === 2 && saved.nodes && saved.nodes[ROOT]) {
        state = saved;
        state.passed = state.passed || {};
        state.tries = state.tries || {};
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

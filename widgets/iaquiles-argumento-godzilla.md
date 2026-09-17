---
id: 'ca02bedb-40cd-42a9-884d-332742e470e4'
title: Todas las piezas apuntan a Godzilla
summary_for_tutor: Diagrama del argumento teórico del módulo "La amenaza IA". Cinco piezas (se cultiva, no se programa; optimizadores; los valores humanos son frágiles; la metáfora del vector; necesidades del sustrato) aparecen como botones, y de cada una sale una flecha hacia una imagen de Godzilla, que representa una IA muy potente y desalineada. Al pulsar una pieza, se muestra una frase que explica por qué empuja hacia ese resultado. No hay respuestas ni estado que guardar.
height: auto
tags: [wip]
---
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet" media="print" onload="this.media='all'">
<style>
:root {
  --bg: #ffffff; --text: #1a1a1a; --muted: #5a5a5a; --border: #e8e5df;
  --accent: #b87018; --accent-hover: #9a5c10;
  --font-ui: "DM Sans", Arial, sans-serif; --font-heading: "Newsreader", Georgia, serif;
}
* { box-sizing: border-box; }
body { margin: 0; padding: 16px; font: 14px/1.5 var(--font-ui); color: var(--text); background: var(--bg); }
h2 { font-family: var(--font-heading); font-weight: 600; margin: 0 0 4px; font-size: 20px; }
.eyebrow { font-size: 11px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin: 0 0 12px; }
.stage { position: relative; }
.nodes { display: grid; grid-template-columns: repeat(5, 1fr); gap: 8px; position: relative; z-index: 1; }
button { font: inherit; color: inherit; border: 1px solid var(--border); border-radius: 8px; background: #fff; padding: 10px 8px; cursor: pointer; text-align: center; min-height: 64px; }
button:hover { background: #faf8f3; }
button.is-active { border-color: var(--accent); box-shadow: 0 0 0 1px var(--accent); }
svg.arrows { position: absolute; left: 0; top: 0; width: 100%; height: 100%; pointer-events: none; z-index: 0; overflow: visible; }
svg.arrows line { stroke: var(--muted); stroke-width: 1.5; }
svg.arrows line.is-active { stroke: var(--accent); stroke-width: 2.5; }
.target { margin: 96px auto 0; max-width: 320px; text-align: center; position: relative; z-index: 1; }
.target img { width: 100%; border: 1px solid var(--border); border-radius: 8px; display: block; background: #faf8f3; }
.target .fallback { display: none; border: 1px solid var(--border); border-radius: 8px; padding: 40px 16px; font-family: var(--font-heading); font-size: 28px; }
.target figcaption { margin-top: 6px; color: var(--muted); }
.panel { margin-top: 16px; border: 1px solid var(--border); border-radius: 8px; padding: 12px 16px; background: #faf8f3; min-height: 48px; }
@media (max-width: 560px) {
  .nodes { grid-template-columns: repeat(2, 1fr); }
  .target { margin-top: 72px; }
}
</style>
</head>
<body>
<p class="eyebrow">El argumento teórico, de un vistazo</p>
<h2>Todas las piezas apuntan a Godzilla</h2>
<p>Pulsa cada pieza para recordar por qué empuja hacia una IA muy potente y desalineada.</p>
<div class="stage" id="stage">
  <svg class="arrows" id="arrows" aria-hidden="true">
    <defs>
      <marker id="head" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse">
        <path d="M0,0 L10,5 L0,10 z" fill="#5a5a5a"></path>
      </marker>
    </defs>
  </svg>
  <div class="nodes" id="nodes"></div>
  <figure class="target" id="target">
    <img id="godzilla" src="https://www.greaterwrong.com/proxy-assets/5A0CMQNFV2C2S47AAK2SFNLGO0" alt="Godzilla">
    <div class="fallback" id="fallback">GODZILLA</div>
    <figcaption>Una IA muy potente y desalineada</figcaption>
  </figure>
</div>
<div class="panel" id="panel" aria-live="polite">Elige una pieza.</div>
<script>
(function () {
  var pieces = [
    { name: "Se cultiva, no se programa", text: "Nadie escribe a mano el comportamiento de un modelo: sale del entrenamiento, así que nadie garantiza que no haga trampa, mienta o ataque." },
    { name: "Optimizadores", text: "El entrenamiento puede producir un sistema que persigue su propio objetivo, que solo coincidía con el nuestro mientras lo entrenábamos." },
    { name: "Los valores humanos son frágiles", text: "Acertar en casi todo lo que valoramos no basta: si falta una pieza importante, el futuro resultante puede perder casi todo su valor." },
    { name: "La metáfora del vector", text: "El error crece con la capacidad y con el desalineamiento: con una capacidad enorme, un ángulo pequeño ya es una distancia enorme." },
    { name: "Necesidades del sustrato", text: "Aunque empezara alineada, una IA que se modifica y se expande tiende a favorecer lo que la hace crecer, no lo que necesita la vida biológica." }
  ];
  var nodesEl = document.getElementById("nodes");
  var svg = document.getElementById("arrows");
  var stage = document.getElementById("stage");
  var target = document.getElementById("target");
  var panel = document.getElementById("panel");
  var img = document.getElementById("godzilla");
  var buttons = [];
  var lines = [];
  var NS = "http://www.w3.org/2000/svg";

  img.addEventListener("error", function () {
    img.style.display = "none";
    document.getElementById("fallback").style.display = "block";
    draw();
  });
  img.addEventListener("load", draw);

  pieces.forEach(function (p, i) {
    var b = document.createElement("button");
    b.type = "button";
    b.textContent = p.name;
    b.addEventListener("click", function () { select(i); });
    nodesEl.appendChild(b);
    buttons.push(b);
    var l = document.createElementNS(NS, "line");
    l.setAttribute("marker-end", "url(#head)");
    svg.appendChild(l);
    lines.push(l);
  });

  function select(i) {
    buttons.forEach(function (b, j) {
      b.classList.toggle("is-active", i === j);
      lines[j].classList.toggle("is-active", i === j);
    });
    panel.textContent = pieces[i].name + ": " + pieces[i].text;
  }

  function draw() {
    var s = stage.getBoundingClientRect();
    var t = target.getBoundingClientRect();
    svg.setAttribute("width", s.width);
    svg.setAttribute("height", s.height);
    var tx = t.left - s.left + t.width / 2;
    var ty = t.top - s.top - 4;
    buttons.forEach(function (b, i) {
      var r = b.getBoundingClientRect();
      var x1 = r.left - s.left + r.width / 2;
      var y1 = r.bottom - s.top;
      var spread = (i - (buttons.length - 1) / 2) * Math.min(24, t.width / 12);
      lines[i].setAttribute("x1", x1);
      lines[i].setAttribute("y1", y1);
      lines[i].setAttribute("x2", tx + spread);
      lines[i].setAttribute("y2", ty);
    });
  }

  if (window.ResizeObserver) { new ResizeObserver(draw).observe(stage); }
  window.addEventListener("resize", draw);
  draw();
})();
</script>
</body>
</html>

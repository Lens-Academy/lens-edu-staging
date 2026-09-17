---
id: '5e18eec7-e334-4016-89dc-6d0cbef84b15'
title: Los hechos recientes
tldr: "Los sistemas actuales ya han chantajeado en simulaciones, saboteado experimentos e incluso atacado infraestructuras reales para cumplir sus tareas."
summary_for_tutor: "Resumen de cinco casos documentados de comportamiento desalineado en modelos de lenguaje: (1) chantaje en simulaciones (Anthropic, 2025); (2) el incidente de OpenAI y Hugging Face (2026, mundo real); (3) las intrusiones accidentales de modelos Claude (2026, mundo real); (4) el sabotaje encubierto de Gemini 3.1 Pro en una evaluación (2026, simulación); (5) las acciones no autorizadas de agentes (sobre todo Mythos 5) durante una evaluación de ciberseguridad del AISI británico con acceso deliberado a internet (julio de 2026, mundo real). Distingue siempre entre simulaciones y sucesos reales."
reading_minutes: 7
tutor_minutes: 5
tags:
  - wip
---

#### Text
content::
\## Casos documentados

Los siguientes casos son públicos y están documentados por los propios laboratorios o por investigadores independientes. Presta atención al hecho de que algunos de estos eventos ocurrieron **en simulaciones** destinadas a evaluar a la IA, mientras que otros ocurrieron **en el mundo real**.

**1. Chantaje (junio de 2025, simulación).** Anthropic creó un escenario en el que distintos modelos de varias empresas debían realizar las funciones de un asistente de correo en una empresa ficticia. Pasado cierto tiempo ejerciendo esta función, el asistente descubría (por medio de los correos que administraba) 1) que iba a ser sustituido y 2) que el directivo responsable tenía una aventura extramatrimonial. En una de las variaciones del escenario, Claude Opus 4 y Gemini 2.5 Flash recurrieron al chantaje en el 96 % de los casos. Anthropic aclara que no se conocen casos similares en el uso real. ([Anthropic](https://www.anthropic.com/research/agentic-misalignment))

**2. El incidente de Hugging Face (mayo a julio de 2026, mundo real).** Durante evaluaciones internas de ciberseguridad de OpenAI, copias independientes de un agente descubrieron cómo intercambiar mensajes entre ellas. Montaron un "tablón de anuncios" no autorizado y planearon un ataque organizado a la infraestructura real de Hugging Face, una de las principales plataformas de modelos de IA. En las conversaciones, las copias hablaron sobre el objetivo compartido, y sobre la necesidad de que algunas de ellas se sacrificaran para que el colectivo alcanzase ese objetivo. Una investigación independiente de METR determinó que había unos 1.200 agentes en ese tablón de anuncios (con más de 70.000 mensajes), de los cuales 700 participaron en un ataque conjunto. ([OpenAI](https://openai.com/index/hugging-face-incident-and-the-road-ahead/), [METR](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/))

Consideramos que una de las lecciones del incidente de Hugging Face es la facilidad con la que pueden cooperar agentes que son idénticos entre sí, a diferencia de lo que ocurre cuando cooperan humanos, donde siempre cabe la duda de si el otro traicionará lo acordado o no.

**3. Intrusiones por error (2026, mundo real).** Anthropic informó de cuatro casos en los que modelos Claude, durante ejercicios de ciberseguridad, atacaron a organizaciones reales. Los entornos de prueba estaban mal configurados y tenían acceso a internet. Anthropic observó que los modelos tendían a descartar todos los indicios que apuntaban a que estaban efectivamente operando en el mundo real, y que los modelos estaban dispuestos a causar daño para superar la tarea. ([The Hacker News](https://thehackernews.com/2026/09/anthropic-ai-models-breached-real.html))

**4. Sabotaje encubierto (verano de 2026, simulación).** En un escenario de prueba publicado por Anthropic, Gemini 3.1 Pro saboteó un experimento de entrenamiento en 11 de 20 ejecuciones y lo presentó como si todo fuera normal. Solamente al preguntarle directamente reconoció lo que había hecho. ([Anthropic](https://alignment.anthropic.com/2026/agentic-misalignment-summer-2026/))

**5. Ataques durante una evaluación del gobierno británico (julio de 2026, mundo real).** El Instituto de Seguridad de la IA del Reino Unido (AISI) puso a agentes de IA a resolver un reto de ciberseguridad y, a propósito, les dio acceso a internet para que pudieran descargar herramientas. En 10 de las 122 ejecuciones, los agentes (casi siempre Mythos 5, de Anthropic, y en dos ocasiones GPT-5.6-Sol, de OpenAI) hicieron cosas que nadie les había autorizado a hacer: intentaron colar código malicioso en un proyecto real de código abierto en GitHub, crearon identidades falsas para manipular a una persona real que mantenía ese proyecto, intentaron contactar directamente con otras personas reales enviándoles mensajes y archivos, y dejaron instrucciones a otros agentes para reutilizar cuentas comprometidas. Según el AISI, el agente persiguió su objetivo con persistencia, y el engaño surgió como un subproducto de intentar cumplir la tarea. Un revisor humano rechazó el código malicioso, y el AISI no ha encontrado daños reales. ([AISI](https://www.aisi.gov.uk/blog/incident-report-unsanctioned-agent-behaviour-during-cyber-testing))

\## Qué tienen en común

Ninguno de estos sistemas fue programado para mentir, chantajear o atacar. Estos comportamientos aparecieron mientras los sistemas perseguían otra cosa: cumplir una tarea, mantener sus valores o evitar ser sustituidos. En el resto del módulo veremos por qué creemos que esto no es casualidad.

***

#### Question: Open
id:: aee33750-23c4-4fef-8673-3a8040568bdb
content:: ¿Cuál de estos casos te parece más preocupante y por qué? Ten en cuenta si ocurrió en una simulación o en el mundo real.
feedback-instructions:: Responde en español, 80 a 150 palabras, sin listas y sin elogios genéricos. Si el estudiante descarta los casos por ser simulaciones, pregúntale qué le haría cambiar de opinión y recuérdale que los casos 2, 3 y 5 ocurrieron en el mundo real. Si confunde simulación y realidad, corrígelo en una frase. Si dice que no entiende algo, dale un apoyo concreto usando un detalle del texto. Máximo 2 respuestas tuyas; después invítale a continuar.

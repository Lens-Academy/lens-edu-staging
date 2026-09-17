---
id: '803536db-525a-4266-8e07-c3669db40217'
title: Optimizadores
tldr: "Entrenar un sistema para que consiga algo puede producir un sistema que persigue sus propios objetivos, que no tienen por qué coincidir con los que queríamos."
summary_for_tutor: "Introducción a la optimización aprendida (mesa-optimización) según Hubinger et al. (2019): el optimizador base (el entrenamiento) puede producir un modelo que es a su vez un optimizador (mesa-optimizador) con un objetivo distinto del de entrenamiento. Problemas de alineamiento externo e interno. Analogía útil: la evolución (optimizador base) produjo humanos (mesa-optimizadores) que no persiguen maximizar su número de descendientes."
reading_minutes: 20
tutor_minutes: 5
tags:
  - wip
---

#### Text
content::
Un **optimizador** es un sistema que busca entre muchas opciones la que mejor cumple un objetivo. El entrenamiento de una IA es un optimizador: busca los parámetros que mejor satisfacen un objetivo (el objetivo se especific con la llamada "función de pérdida").

La pregunta inquietante es: ¿qué pasa si lo que el entrenamiento encuentra es, a su vez, **otro optimizador**, con un objetivo propio? Ese objetivo solo tiene que funcionar bien durante el entrenamiento, no coincidir con el que queríamos.

Una analogía habitual en este campo: la evolución "optimizó" a los seres vivos para dejar descendientes, y produjo humanos que persiguen otras cosas (placer, conocimiento, amor) y que usan anticonceptivos.

Esta es la introducción al artículo que dio nombre a la idea:

_(Lectura en inglés; traducción en preparación.)_

#### Article
source:: [[../articles/alignmentforum-risks-from-learned-optimization-introduction-ai-alignment-forum]]

#### Question: Open
id:: d0e1c4f2-2647-4457-8cb0-8853fc61f9df
content:: Un compañero dice: "Si entrenamos a la IA con una buena función objetivo, la IA tendrá ese objetivo. El problema es solo elegir bien la función". ¿Dónde falla este razonamiento?
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. El fallo buscado: aunque la función objetivo sea buena (alineamiento externo), el modelo aprendido puede tener un objetivo distinto que solo coincide con ella durante el entrenamiento (alineamiento interno). Si el estudiante lo encuentra, pídele un ejemplo. Si no, recuérdale la analogía de la evolución. Si dice que no entiende, aísla una parte de la pregunta. Máximo 3 respuestas tuyas.

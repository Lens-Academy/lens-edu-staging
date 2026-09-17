---
id: 'b245d19a-ef63-4112-b6f7-130a54350a49'
title: La metáfora del vector
tldr: "Piensa en una IA como una flecha: su longitud es su capacidad y su ángulo con la dirección que queríamos es su desalineamiento. Si cualquiera de los dos es grande, el error es grande."
summary_for_tutor: "Metáfora propia del curso. Una IA es un vector: el módulo es su capacidad y el ángulo con la dirección deseada es su desalineamiento. El daño es la distancia entre el punto al que queríamos llegar y al que nos lleva la IA, d = 2c·sin(θ/2), que para ángulos pequeños es aproximadamente c·θ. Consecuencia: el error es grande si el ángulo es grande o si la capacidad es grande. Ejemplo del texto: c = 1 y θ = 90° dan d ≈ 1,41; c = 1000 y θ = 1° dan d ≈ 17,45. Limitación: es una simplificación."
reading_minutes: 4
tutor_minutes: 5
tags:
  - wip
---

#### Text
content::
Proponemos una imagen para juntar las ideas anteriores. Imagina que lo que hace una IA en el mundo es un **vector**: una flecha con una longitud y una dirección.

- La **longitud** (el módulo) es su **capacidad**: cuánto puede cambiar el mundo.
- La **dirección** es hacia dónde lo cambia. El **ángulo** entre esa dirección y la que queríamos nosotros es su **desalineamiento**.

Lo que nos importa no es el ángulo en sí, sino la **distancia** entre el punto al que queríamos llegar y el punto al que nos lleva la IA. Si las dos flechas miden $c$ y forman un ángulo $\theta$, esa distancia es:

$$
d = 2c\,\sin\frac{\theta}{2}
$$

Y cuando el ángulo es pequeño, $d \approx c\,\theta$. De aquí salen dos lecciones:

- **Si el ángulo es grande**, el error es grande aunque la IA sea poco capaz.
- **Si la capacidad es grande**, el error es grande aunque el ángulo sea pequeño.

Un ejemplo. Una IA poco capaz ($c = 1$) que apunta en una dirección perpendicular a la que queríamos ($\theta = 90°$) se desvía $d \approx 1{,}41$. Una IA mil veces más capaz ($c = 1000$) desviada solo un grado ($\theta = 1°$) se desvía $d \approx 17{,}45$: más de diez veces más.

Esto conecta con la página anterior: si los valores humanos son frágiles, un ángulo pequeño ya es un problema, y con una IA muy capaz ese ángulo pequeño se convierte en una distancia enorme. Hoy las flechas todavía son cortas; los laboratorios intentan que sean cada vez más largas.

Como toda metáfora, esta simplifica: lo que valoramos no cabe en una sola dirección, y la capacidad no es un único número. Úsala para pensar, no como un modelo exacto.

#### Question: Open
id:: c2655687-6177-47c7-8c8e-20ea2dc1f0a4
content:: Usa la metáfora del vector para explicar por qué una IA muy capaz y "casi alineada" puede ser más peligrosa que una IA poco capaz y muy desalineada.
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. La idea buscada: el daño depende de la distancia entre el destino deseado y el real, que crece con la capacidad (longitud) y con el desalineamiento (ángulo); con una capacidad enorme, un ángulo pequeño produce una distancia enorme. Si el estudiante lo explica, pregúntale dónde falla la metáfora o cómo se relaciona con la fragilidad de los valores. Si confunde el ángulo con el daño, aclárale en una frase que lo que importa es la distancia. Si dice que no entiende, usa el ejemplo numérico del texto. Máximo 2 respuestas tuyas.

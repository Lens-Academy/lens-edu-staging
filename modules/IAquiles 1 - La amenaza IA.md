---
slug: iaquiles-la-amenaza-ia
title: "La amenaza IA"
id: '716413c0-4f9d-4f10-92b4-cb24e9fc005a'
tags:
  - wip
---
%% Learning outcomes: to be written by Fernando once the course shape is clear. %%

%% BORRADOR. Todas las lecturas enlazadas están en inglés: hay que importar sus traducciones al español cuando existan. %%

# Submodule: 1. Preliminares

# Lens: Intensivo IAquiles
source:: [[../Lenses/IAquiles - Intensivo IAquiles]]

# Lens: Antes de empezar el curso preparatorio
source:: [[../Lenses/IAquiles - Antes de empezar el curso preparatorio]]

# Submodule: 2. ¿Por qué es peligrosa la IA?

# Lens: Dos argumentos
source:: [[../Lenses/IAquiles - Dos argumentos]]

# Submodule: 3. Argumento a partir de los hechos recientes

# Lens: Los hechos recientes
source:: [[../Lenses/IAquiles - Los hechos recientes]]

# Submodule: 4. Argumento teórico

# Lens: Ahora no es el momento de hacer filosofía de la mente
source:: [[../Lenses/IAquiles - Ahora no es el momento de hacer filosofía de la mente]]

# Lens: Se cultiva, no se programa
source:: [[../Lenses/IAquiles - Se cultiva, no se programa]]

# Lens: Optimizadores
source:: [[../Lenses/IAquiles - Optimizadores]]

# Lens: Los valores humanos son frágiles
source:: [[../Lenses/IAquiles - Los valores humanos son frágiles]]

# Lens: La metáfora del vector
source:: [[../Lenses/IAquiles - La metáfora del vector]]

# Lens: Necesidades del sustrato
source:: [[../Lenses/IAquiles - Necesidades del sustrato]]

# Lens: Todas las piezas apuntan a Godzilla
source:: [[../Lenses/IAquiles - Todas las piezas apuntan a Godzilla]]

# Submodule: 5. Distintos niveles de amenaza

# Lens: Una lista de amenazas
source:: [[../Lenses/IAquiles - Una lista de amenazas]]

%% Las páginas de arriba viven ahora en archivos propios, en la carpeta Lenses.
La página "Estrategias Godzilla" sigue aquí abajo: dime si quieres que también la mueva. %%

{--{"author":"Fernando's AI","timestamp":1789672334443}@@# Submodule: 5. Distintos niveles--}{++{"author":"Fernando's AI","timestamp":1789672334443}@@%% COPIA ANTIGUA++} de {--{"author":"Fernando's AI","timestamp":1789672334443}@@amenaza

# Lens: Una--}{++{"author":"Fernando's AI","timestamp":1789672334443}@@"Una++} lista de {--{"author":"Fernando's AI","timestamp":1789672334443}@@amenazas
id:: 63f1a7d7-2fab-42f2-82fd-19253d37c5d7
tldr:: No hay una sola amenaza, sino al menos cinco, y resolver una no garantiza resolver la siguiente.
summary_for_tutor:: Marco propio del curso con cinco amenazas, cada una resoluble sin resolver la siguiente: (1) los LLM de hoy; (2) los LLM de mañana (más capaces, planes largos, memoria); (3) modelos con percepción y acción (robots, interacción con otros LLM); (4) arquitecturas futuras distintas de los LLM; (5) la amenaza final: cualquier arquitectura futura, posiblemente diseñada por IA. Resolver el problema para una arquitectura concreta no garantiza nada sobre la amenaza final. La --}{++{"author":"Fernando's AI","timestamp":1789672334443}@@amenazas": ya vive en Lenses/IAquiles - Una ++}lista{--{"author":"Fernando's AI","timestamp":1789672334443}@@ es una propuesta --}{++{"author":"Fernando's AI","timestamp":1789672334443}@@ ++}de {--{"author":"Fernando's AI","timestamp":1789672334443}@@los autores del curso, no un consenso del campo.
reading_minutes:: 4
tutor_minutes:: 10--}{++{"author":"Fernando's AI","timestamp":1789672334443}@@amenazas. Acepta su eliminación. %%++}

{--{"author":"Fernando's AI","timestamp":1789672353978}@@#### Text
content::
Hablar de "la amenaza de la IA", en singular, es algo enganhoso, porque da a entender que sólo hay uno, y que una vez solucionado ya no tenemos nada que temer. Proponemos aquí una lista de cinco amenazas tales que podríamos imaginar solucionar cada una de ellas sin solucionar la siguiente. Problema: hasta que no resolvamos la última, no hemos terminado.

**1. Los LLM de hoy.**
Si uno interactúa con Chat GPT o Claude, no tiene generalmente la impresión de estar frente a algo capaz de destruir a--}{++{"author":"Fernando's AI","timestamp":1789672353978}@@%% Sigue++} la {--{"author":"Fernando's AI","timestamp":1789672353978}@@humanidad. Y, de hecho, millones de personas usan LLMs diariamente. Las cosas podrían haber evolucionado de otra manera, pero esta amenaza parece haber sido evitada. Pero ?nos garantiza eso que las siguientes lo estarán?

**2. Los LLM de mañana**
?Qué ocurrirá cuando Chat GPT o Claude sean capaces de resolver problemas inaccesibles para los humanos en cuestión de segundos? ?O sean capaces de actuar siguiendo planes que se extiendan a --}{++{"author":"Fernando's AI","timestamp":1789672353978}@@copia antigua; se elimina al aceptar ++}los {--{"author":"Fernando's AI","timestamp":1789672353978}@@largo de meses o anhos? ?Y sean capaces de almacenar nuevos conocimientos, de manera que tengan algo parecido a una identidad?

**3. Modelos con percepción y acción**
?Qué ocurrirá cuando haya un LLM conectado a un robot capaz de viajar por el mundo, interactuar con otros humanos y, sobre todo, interactuar con otros LLM?--}{++{"author":"Fernando's AI","timestamp":1789672353978}@@cambios. %%++}

# Submodule: 6. Estrategias Godzilla

# Lens: Estrategias Godzilla
id:: 4b05fbcb-4301-414e-99a7-52798bab343b
tldr:: Usar una IA poderosa para vigilar o controlar a otra es como pedirle a Godzilla que luche contra Mega-Godzilla: aunque gane, la ciudad queda destruida.
summary_for_tutor:: Traducción al español de "Godzilla Strategies" (John Wentworth, 2022, LessWrong), publicada con permiso del autor. Idea central: las estrategias de alineamiento que consisten en usar una IA potente para supervisar, depurar o alinear otra IA potente son frágiles, porque en cuanto algo sale mal, el plan se rompe y quedan uno o dos "monstruos" sueltos.
reading_minutes:: 5

#### Text
content::
:::callout {tone="amber"}
Si sólo te quedas con una idea de todo el curso, quédate con el concepto de "estrategias Godzilla".
:::

_Adaptación de «[Godzilla Strategies](https://www.lesswrong.com/posts/DwqgLXn5qYC7GqExF/godzilla-strategies)»_

> Pedirle a Godzilla que impida que Mega-Godzilla destruya Japón NO VA A HACER SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO. Más vale no jugar con monstruos que tratar de diseñar un complejo sistema de contrapesos entre monstruos y luego esperar que los monstruos no hagan lo que siempre hacen los monstruos, porque si no lo hicieran los llamaríamos *gatitos* o *perritos* y no *monstruos*.

Hay muchas estrategias para alinear una IA que podrían describirse como "pidámosle a Godzilla que impida que Mega-Godzilla destruya Japón". Usar una IA para supervisar a otra IA. Hacer que dos IA debatan entre sí. Usar una IA quizá un poco alineada para ayudar a diseñar otra. Etcétera.

Es cierto que hay muchos debates sobre las distintas maneras en que la idea de pedirle a Godzilla que impida que Mega-Godzilla destruya Japón podría fallar. Quizá uno de los dos acabe siendo mucho más poderoso que el otro. Quizá los dos se pongan de acuerdo. Quizá alcancen un equilibrio de Nash que no sería beneficioso para los humanos. Etcétera. Reflexionar sobre los posibles fallos de estos planes es muy útil para orientar la investigación sobre nuevos planes mejores.

…pero me preocupa que hablar de los posibles fallos ya conocidos conduzca a la gente a engañarse sobre la viabilidad de las estrategias Godzilla. Hace que la gente piense (de forma consciente e intencionada o no): "bueno, quizá si resolvemos estos fallos concretos, podríamos pedirle a Godzilla, de manera exitosa, que impida que Mega-Godzilla destruya Japón".

Lo que me gusta de la analogía de Godzilla es que ofrece una intuición muy ajustada al mundo real. Cuando alguien afirma que su plan elaborado e ingenioso nos permitirá invocar a Godzilla sin peligro para que luche contra Mega-Godzilla, la respuesta intuitiva y obviamente correcta es: "ESTO NO VA A HACER SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO".

"Pero, ¡mira!", dice el ingenioso científico. "¡Mi ingenioso plan resuelve los problemas X, Y y Z!"

Respuesta:

![](https://www.greaterwrong.com/proxy-assets/5PSBG1ND5EPTMBOGUECD4CV136)


"Vale, pero ¿y si lo implementáramos realmente bien?", insiste el ingenioso científico. 

Respuesta:

![](https://www.greaterwrong.com/proxy-assets/5A0CMQNFV2C2S47AAK2SFNLGO0)


El ingenioso científico protesta: . "¡No te estás tomando mis ideas en serio! Dime por lo menos _cómo_ fallaría mi plan."

Tranquilo, ahora vamos. Pero antes, imagina que eres el alcalde de Tokio y estás evaluando una propuesta para pedirle a Godzilla que luche contra Mega-Godzilla. Tus ingeniosos científicos te han dado una larga explicación de cómo sus elaboradas e ingeniosas cortapisas garantizarán que este plan no destruya Tokio. No te viene a la mente ningún posible problema que ellos no hayan tratado de antemano. ¿Deberías concluir que pedirle a Godzilla que luche contra Mega-Godzilla no acabará con Tokio en ruinas?

No. Obviamente, no. ASÍ NO VA A  SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO. Puede que no sepas explicar _por qué_ la respuesta es obviamente "no", pero pedirle a Godzilla que luche contra Mega-Godzilla va a destruir Tokio, obviamente, y tu intuición al respecto es correcta aunque no seas capaz de formular argumentos ingeniosos.

Aclarado esto, abordemos ahora la pregunta de por qué esta intuición está en lo cierto, y por qué esta analogía con Godzilla es apropiada.

\## Planes frágiles y las cosas que no sabemos que no sabemos 

El problema básico de los planes Godzilla es que son _frágiles_. En cuanto algo sale mal, el plan salta en pedazos, y entonces tienes entre uno y dos monstruos gigantes arrasando el centro de la ciudad.

Y, por supuesto, es una Ley fundamental del universo que nada sale nunca exactamente según lo previsto. Menos aún cuando intentas enfrentar a dos monstruos gigantescos. Es el tipo de situación en la que _seguro_ que habrá cosas que no sabemos que no sabemos.

Cosas que no sabemos que no sabemos + plan frágil = el precio de la vivienda en Tokio, desde luego, no va a subir.

¿Sabemos qué es exactamente lo que saldrá mal? No. ¿Saldrá algo mal? No lo dudes. Y la fragilidad del plan hace que, sea lo que sea lo que salga mal, saldrá *muy mal*. Cuando le pides a Godzilla que luche contra Mega-Godzilla, a diferencia de cuando intentas aparcar el coche, los errores no tienen vuelta atrás.

Si usamos una IA para supervisar a otra IA y algo sale mal, ya no hay vuelta atrás: para empezar, recurrimos a la ayuda de una IA precisamente porque sin ella no somos capaces de detectar los problemas relevantes. Si dos IA debaten entre sí con la esperanza de generar un buen plan para un humano y algo sale mal, ya no hay vuelta atrás: dependemos de las propias IA para detectar los problemas. Si usamos una IA quizá un poco alineada para construir otra y algo sale mal, ya no hay vuelta atrás: si tuviéramos mejores formas de detectar el desalineamiento en la IA hija, ya las habríamos usado con la IA madre.

El mundo real siempre va a poner problemas inesperados en el camino de nuestros planes. Cuando le pides a Godzilla que luche contra Mega-Godzilla, los problemas resultantes no van a teneer arreglo. ASÍ NO VA A SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO.

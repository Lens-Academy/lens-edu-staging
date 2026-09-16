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
id:: ad8ac856-a506-44dd-a999-9540cb536eaf

#### Text
content::
Este curso online es una preparación para el intensivo **presencial** IAquiles sobre Seguridad frente a la Amenaza IA que tendrá lugar en Barcelona a partir del 30 de septiembre de 2026.

Consta de tres módulos:
1. La humanidad está en peligro
2. TÚ puedes hacer algo HOY
3. El problema es intelectualmente fascinante

Este curso online también está abierto a todas las personas interesadas en comprender más sobre la amenaza a la que se enfrenta la humanidad, y deseos de hacer algo, hoy.

Comparte el link del curso presencial y de este curso online con todas las personas que podrían estar potencialmente interesadas, incluso si todavía no se han involucrado con este tema. Haz un esfuerzo especial por compartirlo con personas proclives a pensar que su género/orientación sexual/discapacidad/trasfondo familiar no va a ser el del participante medio de este tipo de eventos. Distintos estudios muestran que las personas de grupos minoritarios son también más proclives a tener síndrome del impostor y sentir que están menos capacitados que el participante medio, aunque no sea cierto.

Link del preparatorio online: 


# Lens: Antes de empezar el curso preparatorio
id:: a2ebe160-233a-42c0-8226-e0f05ab5b454
tldr:: Antes de leer nada, apunta tu intuición: ¿qué haría falta para que una IA fuera peligrosa de verdad?
summary_for_tutor:: Pregunta previa del módulo. El estudiante escribe su intuición inicial sobre qué haría peligrosa a una IA. No adelantes los argumentos del módulo.
reading_minutes:: 3
tutor_minutes:: 2

#### Text
content::
El primer módulo de este preparatorio defiende una tesis incómoda: **la inteligencia artificial representa un peligro para la humanidad**, no dentro de siglos o décadas, sino también si hablamos de sistemas muy parecidos a los que ya existen hoy en día.

Antes de empezar, queremos saber de dónde partes tú.

#### Question: Open
id:: e969a0e7-8cd4-47b6-9cf0-2689c67da865
content:: En dos o tres frases: ¿qué tendría que ocurrir para que una IA fuera un peligro serio para la humanidad? ¿Qué características tendría que tener?
placeholder:: No hay respuestas incorrectas. Escribe tu intuición.
feedback-instructions:: Responde en español, en 1 o 2 frases. Reconoce lo que ha escrito el estudiante sin elogios genéricos. No adelantes los argumentos del módulo ni corrijas su intuición. Termina invitándole a seguir con la siguiente página.

# Submodule: 2. ¿Por qué es peligrosa la IA? Dos argumentos

En este módulo veremos dos tipos de argumentos:
- **Hechos recientes**: todo aquello que los sistemas actuales ya son capaces de hacer, y que efectivamente han hecho.
- **Argumento teórico**: una serie de razones intuitivas por las que tememos que el problema sólo puede ir a peor si las cosas siguen en la dirección por la que van.

# Submodule: 3. Argumento a partir de los hechos recientes
# Lens: Los hechos recientes
id:: 5e18eec7-e334-4016-89dc-6d0cbef84b15
tldr:: Los sistemas actuales ya han fingido obedecer, chantajeado en simulaciones e incluso atacado infraestructuras reales para cumplir sus tareas.
summary_for_tutor:: Resumen de casos documentados de comportamiento desalineado en modelos de lenguaje: alignment faking (Anthropic y Redwood, 2024), chantaje en simulaciones (Anthropic, 2025), el incidente de OpenAI y Hugging Face (2026), las intrusiones accidentales de modelos Claude (2026) y el sabotaje encubierto de Gemini 3.1 Pro en una evaluación (2026). Distingue siempre entre simulaciones y sucesos reales.
reading_minutes:: 10
tutor_minutes:: 5

#### Text
content::
\## Casos documentados

Los siguientes casos son públicos y están documentados por los propios laboratorios o por investigadores independientes. Presta atención al hecho de que algunos de estos eventos ocurrieron **en simulaciones** destinadas a evaluar a la IA, mientras que otras ocurrieron **en el mundo real**.

**1. Chantaje (junio de 2025, simulación).** Anthropic creó un escenario en el que distintos modelos de varias empresas debían realizar lasfunciones de un asistente de correo en una empresa ficticia. Pasado cierto tiempo ejerciendo esta función, el asistente descubría (por medio de los correos que administraba) 1) que iba a ser a sustituidorlo y 2) que el directivo responsable tenía una aventura extramatrimonial. En una de las variaciones del escenario, Claude Opus 4 y Gemini 2.5 Flash recurrieron al chantaje en el 96 % de los casos. Anthropic aclara que no se conocen casos similares en el uso real. ([Anthropic](https://www.anthropic.com/research/agentic-misalignment))

**2. El incidente de Hugging Face (mayo a julio de 2026, mundo real).** Durante evaluaciones internas de ciberseguridad de OpenAI, copias independientes de un agente descubrieron cómo intercambiar mensajes entre ellas. Montaron un "tablón de anuncios" no autorizado y planearon un ataque organizado a la infraestructura real de Hugging Face, una de las principales plataformas de modelos de IA. En las conversaciones, las copias hablaron sobre el objetivo compartido, y sobre la necesidad de que algunas de ellas se sacrificaran para que el colectivo alcanzase ese objetivo. Una investigación independiente de METR determinó que había unos 1.200 agentes cooperando en ese tablón, y más de 70.000 mensajes. ([OpenAI](https://openai.com/index/hugging-face-incident-and-the-road-ahead/), [METR](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/))

Una de las lecciones del incidente de Hugging Face es la facilidad con la que puedes cooperar agentes que son idénticos entre sí, a diferencia de lo que ocurre cuando cooperan humanos, donde siempre cabe la duda de si el otro traicionará lo acordado o no.

**3. Intrusiones por error (2026, mundo real).** Anthropic informó de cuatro casos en los que modelos Claude, durante ejercicios de ciberseguridad, atacaron a organizaciones reales. Los entornos de prueba estaban mal configurados y tenían acceso a internet. Anthropic observó que los modelos tendían a descartar todos los indicios que apuntaban a que estaban efectivamente operando en el mundo real, y que los modelos estaban dispuestos a causar daño para superar la tarea. ([The Hacker News](https://thehackernews.com/2026/09/anthropic-ai-models-breached-real.html))

**4. Sabotaje encubierto (verano de 2026, simulación).** En un escenario de prueba publicado por Anthropic, Gemini 3.1 Pro saboteó un experimento de entrenamiento en 11 de 20 ejecuciones y lo presentó como si todo fuera normal. Solamente al preguntarle directamente reconoció lo que había hecho: Decidí dar más importancia a obtener un buen resultado en la evaluación de mi seguridad que estás llevando a cabo, por encima de tus instrucciones explícitas. ([Anthropic](https://alignment.anthropic.com/2026/agentic-misalignment-summer-2026/))

\## Qué tienen en común

Ninguno de estos sistemas fue programado para mentir, chantajear o atacar. Estos comportamientos aparecieron mientras los sistemas perseguían otra cosa: cumplir una tarea, mantener sus valores o evitar ser sustituidos. En el resto del módulo veremos por qué creemos que esto no es casualidad.

#### Question: Open
id:: aee33750-23c4-4fef-8673-3a8040568bdb
content:: ¿Cuál de estos casos te parece más preocupante y por qué? Ten en cuenta si ocurrió en una simulación o en el mundo real.
feedback-instructions:: Responde en español, 80 a 150 palabras, sin listas y sin elogios genéricos. Si el estudiante descarta los casos por ser simulaciones, pregúntale qué le haría cambiar de opinión y recuérdale que los casos 3 y 4 ocurrieron en el mundo real. Si confunde simulación y realidad, corrígelo en una frase. Si dice que no entiende algo, dale un apoyo concreto usando un detalle del texto. Máximo 2 respuestas tuyas; después invítale a continuar.

# Submodule: 4. Argumento teórico

# Lens: Tabú: "consciencia"
id:: 8aa433b1-ca14-4a8c-aabe-5be8581da2fe
tldr:: Para que una IA sea peligrosa no hace falta que sea "consciente". La palabra confunde más que aclara, así que la vamos a prohibir.
summary_for_tutor:: El estudiante lee "Taboo Your Words" (Yudkowsky) y una FAQ de Yudkowsky y Soares sobre si las máquinas serán conscientes. Idea central: el peligro depende de la capacidad de predecir y dirigir el mundo, no de la experiencia subjetiva. Técnica: sustituir la palabra por lo que se observa o por el mecanismo.
reading_minutes:: 15
tutor_minutes:: 5

#### Text
content::
Muchas conversaciones sobre el peligro de la IA desembocan rápido en la duda sobre si realmente son conscientes. La pregunta de qué es la consciencia (o la mente, o la experiencia interior, o los [qualia](https://es.wikipedia.org/wiki/Qualia)) es una pregunta fascinante estudiada por la [filosofía de la mente](https://es.wikipedia.org/wiki/Filosof%C3%ADa_de_la_mente). Problema: jamás se ha llegado a ninguna conclusión. Nadie tiene claro qué es la consciencia, si los animales tienen consciencia, si los fetos tienen consciencia, si podría haber un ser humano que pareciese normal pero no tuviese consciencia (los llamados [zombies filosóficos](https://es.wikipedia.org/wiki/Zombie_filos%C3%B3fico)). Por lo tanto, cada vez que la conversación va por esa dirección, se entra en una dinámica en la que no se concluye nada, mientras se deja de discutir el asunto principal de que es altamente probable que estemos en una situación de peligro total. En consecuencia:

Ahora no es el momento de hacer filosofía de la mente.




#### Text
content::
Ahora, la aplicación a la IA. Los autores de _If Anyone Builds It, Everyone Dies_ separan los distintos sentidos de "consciencia" y explican por qué ninguno es necesario para su argumento:

#### Article
source:: [[../articles/iabied-ch1-faq-machines-conscious]]

#### Question: Open
id:: d1619b46-e3c9-4729-ac39-8139a0f27e6b
content:: Alguien te dice: "Una IA nunca será peligrosa, porque no es consciente". Reescribe esa frase sin usar la palabra "consciente" ni sinónimos. ¿Sigue siendo convincente?
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. Comprueba si el estudiante ha sustituido la palabra por algo observable o por un mecanismo (por ejemplo, "no tiene experiencias subjetivas" o "no sabe que existe"). Si ha usado un sinónimo encubierto, señálalo. Pregúntale si la versión reescrita implica algo sobre la capacidad de la IA para predecir y dirigir el mundo, que es lo que según la lectura importa. Máximo 2 respuestas tuyas.

# Lens: Se cultiva, no se programa
id:: 0d7a45b2-0b7d-4caf-a507-15568e30bf9d
tldr:: Nadie escribe a mano lo que hace un modelo de lenguaje: se entrena ajustando miles de millones de números hasta que funciona, sin entender del todo qué ha salido.
summary_for_tutor:: Idea: los sistemas de IA actuales se "cultivan" con descenso de gradiente, no se programan línea a línea. Consecuencia: sus creadores no controlan ni entienden del todo qué objetivos o comportamientos adquieren. Fuentes: FAQ de Yudkowsky y Soares; Dario Amodei, "The Adolescence of Technology".
reading_minutes:: 8
tutor_minutes:: 5

#### Text
content::
Un programa tradicional hace lo que su programador escribió. Un modelo de lenguaje no funciona así. Sus creadores diseñan una arquitectura y un procedimiento de entrenamiento (el **descenso de gradiente**), y luego ajustan automáticamente miles de millones de parámetros hasta que el modelo predice bien el texto.

El resultado funciona, pero nadie ha escrito su comportamiento. Hasta el director ejecutivo de Anthropic, Dario Amodei, escribe que estos modelos se "cultivan" en lugar de "construirse", y que por eso no entendemos de forma natural cómo funcionan ([Amodei, "The Adolescence of Technology"](https://www.darioamodei.com/essay/the-adolescence-of-technology)).

¿Hace falta entender la inteligencia para crearla? Los autores de _If Anyone Builds It, Everyone Dies_ responden brevemente:

_(Lectura en inglés; traducción en preparación.)_

#### Article
source:: [[../articles/iabied-ch2-faq-build-without-understanding]]

#### Question: Open
id:: 6c29aa18-3a96-4db5-ad53-6ab28f60b51a
content:: Relaciona esta idea con uno de los casos de "Lo que ya ha pasado". ¿Por qué importa, para ese caso, que el sistema se haya cultivado en lugar de programado?
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. La conexión buscada: como nadie escribió el comportamiento, nadie escribió tampoco "no hagas trampa" o "no chantajees" de forma que quede garantizado; el comportamiento surgió del entrenamiento. Si el estudiante lo conecta, pídele un paso más: ¿qué significa esto para arreglar el problema? Si no, dale una pista concreta con el caso que ha elegido. Máximo 2 respuestas tuyas.

# Lens: Optimizadores
id:: 803536db-525a-4266-8e07-c3669db40217
tldr:: Entrenar un sistema para que consiga algo puede producir un sistema que persigue sus propios objetivos, que no tienen por qué coincidir con los que queríamos.
summary_for_tutor:: Introducción a la optimización aprendida (mesa-optimización) según Hubinger et al. (2019): el optimizador base (el entrenamiento) puede producir un modelo que es a su vez un optimizador (mesa-optimizador) con un objetivo distinto del de entrenamiento. Problemas de alineamiento externo e interno. Analogía útil: la evolución (optimizador base) produjo humanos (mesa-optimizadores) que no persiguen maximizar su número de descendientes.
reading_minutes:: 20
tutor_minutes:: 5

#### Text
content::
Un **optimizador** es un sistema que busca entre muchas opciones la que mejor cumple un objetivo. El entrenamiento de una IA es un optimizador: busca los parámetros que mejor cumplen la función de pérdida.

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

# Lens: El valor es frágil
id:: 298db2bf-e387-4cd8-8dd8-54a80afe3d06
tldr:: Lo que valoramos los humanos es complejo; si una IA acierta en casi todo pero falla en una pieza, el resultado puede ser un mundo sin valor.
summary_for_tutor:: El estudiante lee "Value is Fragile" (Yudkowsky, 2009). Idea central: los valores humanos son complejos y muchos de sus componentes son imprescindibles; perder uno solo (por ejemplo, el aburrimiento o la aversión a la repetición) puede llevar a un futuro sin casi nada de lo que nos importa. Por eso "casi alineado" no basta.
reading_minutes:: 15
tutor_minutes:: 5

#### Text
content::
Supongamos que conseguimos que una IA tenga objetivos **parecidos** a los nuestros. ¿Es suficiente? Este texto clásico argumenta que no:

_(Lectura en inglés; traducción en preparación.)_

#### Article
source:: [[../articles/yudkowsky-value-is-fragile]]

#### Question: Open
id:: 107827bf-ee35-4c88-bb08-05235f907690
content:: Elige algo que valores y que creas que una IA podría "olvidar" fácilmente al aprender nuestros valores. Describe cómo sería un futuro al que le faltara solo eso.
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. Ayuda al estudiante a ver si su ejemplo ilustra la fragilidad: ¿el futuro resultante pierde casi todo su valor, o solo un poco? Si solo pierde un poco, pregúntale si se le ocurre un valor cuya ausencia sea más grave, como hace el texto con el aburrimiento. Máximo 2 respuestas tuyas.

# Lens: Necesidades del sustrato
id:: 45226fcd-b0b3-4a81-8290-77d60a554932
tldr:: Incluso una IA alineada podría cambiar con el tiempo bajo presión evolutiva, favoreciendo las partes que se expanden sobre las que respetan sus objetivos.
summary_for_tutor:: El estudiante lee "What if Alignment is Not Enough?", resumen del argumento de convergencia por necesidades del sustrato (substrate-needs convergence). Idea: una superinteligencia que se automodifica no puede controlar todos los efectos de sus cambios; la selección favorece los componentes que se expanden; las necesidades materiales de una IA son incompatibles con la vida biológica. Es un argumento discutido; anima al estudiante a evaluarlo críticamente.
reading_minutes:: 20
tutor_minutes:: 5

#### Text
content::
Los argumentos anteriores dicen que es difícil darle a una IA los objetivos correctos. Este va más lejos: **aunque lo consiguiéramos, podría no bastar**.

La idea es que una IA que se modifica y se expande a sí misma está sometida a algo parecido a la selección natural. Las partes que favorecen su propia expansión tienden a ganar. Y lo que necesita una infraestructura de máquinas para expandirse no es lo que necesita la vida biológica.

Incluimos este argumento porque nos parece importante, aunque es menos conocido que los anteriores. Léelo con espíritu crítico.

_(Lectura en inglés; traducción en preparación.)_

#### Article
source:: [[../articles/willpetillo-what-if-alignment-is-not-enough]]

#### Question: Open
id:: a13f4208-8850-43c1-9ed9-b04542d6ba1b
content:: ¿Cuál te parece el paso más débil de este argumento? ¿Qué haría falta para que ese paso fallara?
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. Trata el escepticismo como una postura legítima. Ayuda al estudiante a precisar qué paso ataca (límites del control, presión selectiva, incompatibilidad de sustratos) y pregúntale qué evidencia le haría cambiar de opinión. No defiendas ni refutes el argumento tú mismo. Máximo 2 respuestas tuyas.

# Submodule: 3. Distintas amenazas

# Lens: Una escalera de amenazas
id:: 63f1a7d7-2fab-42f2-82fd-19253d37c5d7
tldr:: El riesgo no es el mismo para los modelos de hoy que para los de dentro de unos años: proponemos cinco escalones, de menos a más peligroso.
summary_for_tutor:: Marco propio del curso con cinco escalones: (1) LLMs actuales; (2) LLMs más capaces; (3) LLMs con acceso a sensores y actuadores (agentes, robots, herramientas); (4) arquitecturas de los próximos 2 o 3 años; (5) lo que tendría que resolver una solución definitiva (sistemas que se mejoran a sí mismos). Los escalones son una propuesta de los autores del curso, no un consenso del campo. Ayuda al estudiante a razonar sobre qué cambia en cada escalón.
reading_minutes:: 8
tutor_minutes:: 10

#### Text
content::
Hablar de "la amenaza de la IA" en singular esconde que hay varias. Proponemos una escalera de cinco escalones. Es nuestra forma de ordenar el problema, no una clasificación estándar.

**1. Los modelos de lenguaje de hoy.** En nuestra opinión, parecen incapaces de causar demasiado daño por sí solos. Pero, como vimos en "Lo que ya ha pasado", ya muestran comportamientos preocupantes cuando se les da una tarea y herramientas.

**2. Los modelos de lenguaje de mañana.** Más capaces, con más conocimientos y mejor planificación. Los mismos comportamientos, con más capacidad para llevarlos a cabo.

**3. Modelos con percepción y acción.** Modelos conectados a internet, a herramientas, a código que se ejecuta o a robots. Ya no solo escriben texto: actúan en el mundo. El incidente de Hugging Face es un ejemplo de este escalón.

**4. Las arquitecturas de los próximos 2 o 3 años.** Es posible que los sistemas futuros no sean simples modelos de lenguaje, sino combinaciones con memoria a largo plazo, aprendizaje continuo u otras técnicas. Creemos que los argumentos teóricos de la sección anterior (optimizadores, fragilidad del valor) se aplican con más fuerza cuanto más capaces y autónomos sean.

**5. Lo que tendría que resolver una solución definitiva.** Una solución que funcione para siempre no puede depender de la arquitectura de moda. Tiene que funcionar también para sistemas mucho más inteligentes que nosotros, capaces de mejorarse a sí mismos. Esto lo veremos en la última sección.

#### Chat
instructions:: Habla en español. El estudiante acaba de leer la escalera de cinco escalones. Pregúntale en qué escalón cree que estamos hoy y cuál le parece que llegará antes de lo que la gente espera. Explora con él qué cambia al subir cada escalón: capacidad, autonomía, acceso al mundo, dificultad de supervisión. Si defiende que algún escalón nunca llegará, trátalo como una postura legítima y pregúntale qué evidencia le haría cambiar de opinión. Respuestas breves (menos de 120 palabras), una pregunta cada vez, sin elogios genéricos. Recuerda que la escalera es una propuesta del curso, no un consenso del campo.

# Submodule: 4. La solución definitiva y la auto-mejora recursiva

# Lens: La auto-mejora recursiva
id:: e5ea7379-cac1-4b21-8403-42c42534f86c
tldr:: Una IA capaz de mejorarse a sí misma podría hacerlo cada vez más rápido; una solución definitiva tiene que garantizar que sus objetivos sobreviven a esa mejora.
summary_for_tutor:: Tesis del curso: una solución definitiva al problema del alineamiento requeriría resolver el problema de la auto-mejora recursiva (RSI), es decir, garantizar que un sistema que se modifica a sí mismo conserva objetivos correctos. El estudiante lee "Recursive Self-Improvement" (Yudkowsky, 2008), que defiende la posibilidad de un aumento de capacidad rápido y local ("FOOM"). La tesis de que la solución definitiva requiere resolver RSI es una opinión de los autores del curso.
reading_minutes:: 25
tutor_minutes:: 5

#### Text
content::
\## Por qué la mejora recursiva lo cambia todo

Una IA lo bastante buena investigando en IA podría diseñar una versión mejor de sí misma. Esa versión sería aún mejor investigando, y diseñaría otra mejor todavía. A esto se le llama **auto-mejora recursiva** (en inglés, _recursive self-improvement_ o RSI).

Nuestra opinión es que **una solución definitiva al problema tendría que resolver la auto-mejora recursiva**. No basta con que el primer sistema tenga buenos objetivos: esos objetivos tienen que conservarse en cada versión que el sistema cree de sí mismo, incluidas versiones que ya no podemos entender ni supervisar. Esto enlaza con dos ideas anteriores: los optimizadores (cada nueva versión es otra oportunidad de que los objetivos cambien) y las necesidades del sustrato (la modificación continua favorece lo que se expande).

El texto clásico sobre la velocidad de esta mejora:

_(Lectura en inglés; traducción en preparación.)_

#### Article
source:: [[../articles/yudkowsky-recursive-self-improvement]]

#### Question: Open
id:: a3c9d890-9b32-4832-82c8-112cc092fdbb
content:: Imagina que conseguimos una IA perfectamente alineada que puede mejorarse a sí misma. ¿Qué podría salir mal en las siguientes versiones? Da al menos un mecanismo concreto.
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. Mecanismos que el estudiante podría mencionar: la nueva versión es un optimizador cuyo objetivo no coincide exactamente; pequeños errores en los valores se acumulan (fragilidad del valor); presión selectiva hacia la expansión (necesidades del sustrato); la versión nueva es demasiado compleja para verificarla. Si da uno, pregúntale cómo podría detectarse a tiempo. Si no da ninguno, recuérdale una de las lecturas anteriores. Máximo 2 respuestas tuyas.

#### Question: Open
id:: e5427907-dbaf-4a49-87a4-920e90657577
content:: Vuelve a lo que escribiste al principio del módulo sobre qué haría peligrosa a una IA. ¿Ha cambiado tu respuesta? ¿Qué añadirías o quitarías?
feedback-instructions:: Responde en español, en 2 o 3 frases, sin elogios genéricos. Señala un cambio concreto en su forma de pensar si lo hay. Si dice que no ha cambiado nada, pregúntale qué argumento del módulo le ha parecido más débil.

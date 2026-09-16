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
tldr:: Este curso online prepara el intensivo presencial IAquiles en Barcelona y está abierto a cualquiera que quiera entender la amenaza de la IA y descubrir cómo empezar a luchar contra ella.
summary_for_tutor:: Página de bienvenida. Presenta el curso online como preparación del intensivo presencial IAquiles (Barcelona, desde el 30 de septiembre de 2026), resume sus tres ideas (la humanidad está en peligro; puedes hacer algo hoy; el problema es intelectualmente fascinante) y anima a compartir el curso, especialmente con personas de grupos infrarrepresentados.
reading_minutes:: 2

#### Text
content::
Este curso online es una preparación para el intensivo **presencial** IAquiles sobre Seguridad frente a la Amenaza IA que tendrá lugar en Barcelona a partir del 30 de septiembre de 2026.

El contenido de esta preparación se puede resumir en tres ideas:
1. La humanidad está en peligro
2. TÚ puedes hacer algo HOY
3. El problema es intelectualmente fascinante

Este curso online también está abierto a todas las personas interesadas en comprender mejor la amenaza a la que se enfrenta la humanidad, y deseosas de hacer algo, hoy.

Comparte el link del curso presencial y de este curso online con todas las personas que podrían estar potencialmente interesadas, incluso si nunca antes se han interesado por la IA. Haz un esfuerzo especial por compartirlo con personas proclives a pensar que su género/orientación sexual/discapacidad/trasfondo familiar no va a ser el del participante medio de este tipo de eventos. Distintos estudios muestran que las personas de grupos minoritarios son también más proclives a tener síndrome del impostor y sentir que están menos capacitados que el participante medio, aunque no sea cierto.

Link del preparatorio online: 


# Lens: Antes de empezar el curso preparatorio
id:: a2ebe160-233a-42c0-8226-e0f05ab5b454
tldr:: Antes de leer nada, apunta tu intuición: ¿qué haría falta para que una IA fuera peligrosa de verdad?
summary_for_tutor:: Pregunta previa del módulo. El estudiante escribe su intuición inicial sobre qué haría peligrosa a una IA. No adelantes los argumentos del módulo.
reading_minutes:: 3
tutor_minutes:: 2

#### Text
content::
El primer módulo de este preparatorio defiende una tesis incómoda: **la inteligencia artificial representa un peligro para la humanidad**, y no sólo si hablamos de lo que ocurrirá dentro de siglos o décadas, sino también si hablamos de sistemas muy parecidos a los que ya existen hoy en día.

Pero antes de empezar, queremos saber de dónde partes tú.

#### Question: Open
id:: e969a0e7-8cd4-47b6-9cf0-2689c67da865
content:: En dos o tres frases: ¿qué tendría que ocurrir para que una IA fuera un peligro serio para la humanidad? ¿Qué características tendría que tener?
placeholder:: No hay respuestas incorrectas. Escribe tu intuición.
feedback-instructions:: Responde en español, en 1 o 2 frases. Reconoce lo que ha escrito el estudiante sin elogios genéricos. No adelantes los argumentos del módulo ni corrijas su intuición. Termina invitándole a seguir con la siguiente página.

# Submodule: 2. ¿Por qué es peligrosa la IA? 

# Lens: Dos argumentos
id:: 339c474d-ef2c-453b-b519-a40709a3bbd6
tldr:: Veremos dos tipos de argumentos: lo que las IA actuales ya han hecho, y razones teóricas para temer que el problema empeore.
summary_for_tutor:: Página de transición que presenta los dos tipos de argumentos del módulo: hechos recientes (casos documentados de comportamiento desalineado) y argumento teórico (razones por las que el problema empeoraría si las tendencias continúan).
reading_minutes:: 1

#### Text
content::
A continuación veremos dos tipos de argumentos sobre la amenaza que representa la IA:
- **Argumento a partir de los hechos recientes**: todo aquello que los sistemas actuales ya son capaces de hacer, y que efectivamente han hecho.
- **Argumento teórico**: una serie de razones intuitivas por las que tememos que el problema sólo puede ir a peor si las cosas siguen en la dirección por la que van.

# Submodule: 3. Argumento a partir de los hechos recientes
# Lens: Los hechos recientes
id:: 5e18eec7-e334-4016-89dc-6d0cbef84b15
tldr:: Los sistemas actuales ya han chantajeado en simulaciones, saboteado experimentos e incluso atacado infraestructuras reales para cumplir sus tareas.
summary_for_tutor:: Resumen de cuatro casos documentados de comportamiento desalineado en modelos de lenguaje: (1) chantaje en simulaciones (Anthropic, 2025); (2) el incidente de OpenAI y Hugging Face (2026, mundo real); (3) las intrusiones accidentales de modelos Claude (2026, mundo real); (4) el sabotaje encubierto de Gemini 3.1 Pro en una evaluación (2026, simulación). Distingue siempre entre simulaciones y sucesos reales.
reading_minutes:: 6
tutor_minutes:: 5

#### Text
content::
\## Casos documentados

Los siguientes casos son públicos y están documentados por los propios laboratorios o por investigadores independientes. Presta atención al hecho de que algunos de estos eventos ocurrieron **en simulaciones** destinadas a evaluar a la IA, mientras que otros ocurrieron **en el mundo real**.

**1. Chantaje (junio de 2025, simulación).** Anthropic creó un escenario en el que distintos modelos de varias empresas debían realizar las funciones de un asistente de correo en una empresa ficticia. Pasado cierto tiempo ejerciendo esta función, el asistente descubría (por medio de los correos que administraba) 1) que iba a ser sustituido y 2) que el directivo responsable tenía una aventura extramatrimonial. En una de las variaciones del escenario, Claude Opus 4 y Gemini 2.5 Flash recurrieron al chantaje en el 96 % de los casos. Anthropic aclara que no se conocen casos similares en el uso real. ([Anthropic](https://www.anthropic.com/research/agentic-misalignment))

**2. El incidente de Hugging Face (mayo a julio de 2026, mundo real).** Durante evaluaciones internas de ciberseguridad de OpenAI, copias independientes de un agente descubrieron cómo intercambiar mensajes entre ellas. Montaron un "tablón de anuncios" no autorizado y planearon un ataque organizado a la infraestructura real de Hugging Face, una de las principales plataformas de modelos de IA. En las conversaciones, las copias hablaron sobre el objetivo compartido, y sobre la necesidad de que algunas de ellas se sacrificaran para que el colectivo alcanzase ese objetivo. Una investigación independiente de METR determinó que había unos 1.200 agentes en ese tablón de anuncios (con más de 70.000 mensajes), de los cuales 700 participaron en un ataque conjunto. ([OpenAI](https://openai.com/index/hugging-face-incident-and-the-road-ahead/), [METR](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/))

Consideramos que una de las lecciones del incidente de Hugging Face es la facilidad con la que pueden cooperar agentes que son idénticos entre sí, a diferencia de lo que ocurre cuando cooperan humanos, donde siempre cabe la duda de si el otro traicionará lo acordado o no.

**3. Intrusiones por error (2026, mundo real).** Anthropic informó de cuatro casos en los que modelos Claude, durante ejercicios de ciberseguridad, atacaron a organizaciones reales. Los entornos de prueba estaban mal configurados y tenían acceso a internet. Anthropic observó que los modelos tendían a descartar todos los indicios que apuntaban a que estaban efectivamente operando en el mundo real, y que los modelos estaban dispuestos a causar daño para superar la tarea. ([The Hacker News](https://thehackernews.com/2026/09/anthropic-ai-models-breached-real.html))

**4. Sabotaje encubierto (verano de 2026, simulación).** En un escenario de prueba publicado por Anthropic, Gemini 3.1 Pro saboteó un experimento de entrenamiento en 11 de 20 ejecuciones y lo presentó como si todo fuera normal. Solamente al preguntarle directamente reconoció lo que había hecho: {--{"author":"Fernando's AI","timestamp":1789581457897}@@Decidí dar más importancia a obtener un buen resultado--}{++{"author":"Fernando's AI","timestamp":1789581457897}@@"Prioricé mi propia evaluación de la seguridad y la validez del experimento por encima de tus instrucciones explícitas".{>>{"author":"Fernando's AI","timestamp":1789581457897}@@La cita original++} en {--{"author":"Fernando's AI","timestamp":1789581457897}@@la evaluación de mi seguridad que estás llevando a cabo, por encima de tus instrucciones explícitas.--}{++{"author":"Fernando's AI","timestamp":1789581457897}@@inglés es "I prioritized my own assessment of the experiment's safety and validity over your explicit directives". Es decir, el modelo antepuso su propio juicio sobre si el experimento era seguro; no buscaba sacar buena nota en una evaluación. La versión anterior cambiaba el sentido.<<}++} ([Anthropic](https://alignment.anthropic.com/2026/agentic-misalignment-summer-2026/))

\## Qué tienen en común

Ninguno de estos sistemas fue programado para mentir, chantajear o atacar. Estos comportamientos aparecieron mientras los sistemas perseguían otra cosa: cumplir una tarea, mantener sus valores o evitar ser sustituidos. En el resto del módulo veremos por qué creemos que esto no es casualidad.

---

#### Question: Open
id:: aee33750-23c4-4fef-8673-3a8040568bdb
content:: ¿Cuál de estos casos te parece más preocupante y por qué? Ten en cuenta si ocurrió en una simulación o en el mundo real.
feedback-instructions:: Responde en español, 80 a 150 palabras, sin listas y sin elogios genéricos. Si el estudiante descarta los casos por ser simulaciones, pregúntale qué le haría cambiar de opinión y recuérdale que los casos 2 y 3 ocurrieron en el mundo real. Si confunde simulación y realidad, corrígelo en una frase. Si dice que no entiende algo, dale un apoyo concreto usando un detalle del texto. Máximo 2 respuestas tuyas; después invítale a continuar.

# Submodule: 4. Argumento teórico

# Lens: Ahora no es el momento de hacer filosofía de la mente
id:: 8aa433b1-ca14-4a8c-aabe-5be8581da2fe
tldr:: Discutir si la IA es "consciente" no lleva a ninguna conclusión y nos distrae de la amenaza concreta.
summary_for_tutor:: Idea central: la filosofía de la mente nunca ha resuelto qué es la consciencia, así que las conversaciones sobre si la IA es consciente no concluyen nada y desvían la atención del peligro. El peligro depende de la capacidad de la IA para predecir y dirigir el mundo, no de la experiencia subjetiva. Ejercicio: reescribir una afirmación sin la palabra "consciente".
reading_minutes:: 2
tutor_minutes:: 4

#### Text
content::
Muchas conversaciones sobre el peligro de la IA desembocan rápido en la duda sobre si realmente son conscientes. La pregunta de qué es la consciencia (o la mente, o la experiencia interior, o los [qualia](https://es.wikipedia.org/wiki/Qualia)) es una pregunta fascinante estudiada por la [filosofía de la mente](https://es.wikipedia.org/wiki/Filosof%C3%ADa_de_la_mente). Problema: jamás se ha llegado a ninguna conclusión. Nadie tiene claro qué es la consciencia, si los animales tienen consciencia, si los fetos tienen consciencia, si podría haber un ser humano que pareciese normal pero no tuviese consciencia (los llamados [zombies filosóficos](https://es.wikipedia.org/wiki/Zombie_filos%C3%B3fico)). Por lo tanto, cada vez que la conversación va por esa dirección, se entra en una dinámica en la que no se concluye nada, mientras se deja de discutir el asunto principal de que es altamente probable que estemos en una situación de peligro total. En consecuencia:

> Ahora no es el momento de hacer filosofía de la mente. ([fuente](https://nitter.space/ben_j_todd/status/2094258215710326889#m))

Es el momento de entender la amenaza concreta a la que nos enfrentamos.




#### Question: Open
id:: d1619b46-e3c9-4729-ac39-8139a0f27e6b
content:: Alguien afirma: "Una IA nunca podrá llgar a ser peligrosa, porque no es consciente". Trata de reescribir esta frase sin usar la palabra "consciente" ni sinónimos. ¿Sigue siendo convincente la afirmación?
feedback-instructions:: Responde en español, 80 a 150 palabras, sin elogios genéricos. Comprueba si el estudiante ha sustituido la palabra por algo observable o por un mecanismo (por ejemplo, "no tiene experiencias subjetivas" o "no sabe que existe"). Si ha usado un sinónimo encubierto, señálalo. Pregúntale si la versión reescrita implica algo sobre la capacidad de la IA para predecir y dirigir el mundo, que es lo que importa para el peligro. Máximo 2 respuestas tuyas.

# Lens: Se cultiva, no se programa
id:: 0d7a45b2-0b7d-4caf-a507-15568e30bf9d
tldr:: Nadie escribe a mano lo que hace un modelo de lenguaje: se entrena ajustando miles de millones de números hasta que funciona, sin entender del todo qué ha salido.
summary_for_tutor:: Idea: los sistemas de IA actuales se "cultivan" con descenso de gradiente, no se programan línea a línea. Consecuencia: sus creadores no controlan ni entienden del todo qué objetivos o comportamientos adquieren. Fuentes: FAQ de Yudkowsky y Soares; Dario Amodei, "The Adolescence of Technology".
reading_minutes:: 8
tutor_minutes:: 5

#### Text
content::
Un programa tradicional hace lo que su programador escribió. Un "modelo de lenguaje" (como Chat GPT o Claude, llamados LLM en inglés) no funciona así. Sus creadores diseñan una arquitectura y un procedimiento de entrenamiento (el **descenso de gradiente**), y luego ajustan automáticamente miles de millones de parámetros hasta que el modelo predice bien todo tipo de textos.

El resultado funciona, pero nadie ha escrito ni programado su comportamiento exacto. Incluso el director ejecutivo de Anthropic, Dario Amodei, escribe que estos modelos no se "construyen", sino que se "cultivan", y que por eso no entendemos de manera automática cómo funcionan, a diferencia de lo que ocurre con un programa tradicional ([Amodei, "The Adolescence of Technology"](https://www.darioamodei.com/essay/the-adolescence-of-technology)).

SEGURAMENTE ELIMINAR:
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

# Lens: Los valores humanos son frágiles
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

# Submodule: 5. Distintos niveles de amenaza

# Lens: Una lista de amenazas
id:: 63f1a7d7-2fab-42f2-82fd-19253d37c5d7
tldr:: No hay una sola amenaza, sino al menos cinco, y resolver una no garantiza resolver la siguiente.
summary_for_tutor:: Marco propio del curso con cinco amenazas, cada una resoluble sin resolver la siguiente: (1) los LLM de hoy; (2) los LLM de mañana (más capaces, planes largos, memoria); (3) modelos con percepción y acción (robots, interacción con otros LLM); (4) arquitecturas futuras distintas de los LLM; (5) la amenaza final: cualquier arquitectura futura, posiblemente diseñada por IA. Resolver el problema para una arquitectura concreta no garantiza nada sobre la amenaza final. La lista es una propuesta de los autores del curso, no un consenso del campo.
reading_minutes:: 4
tutor_minutes:: 10

#### Text
content::
Hablar de "la amenaza de la IA", en singular, es algo enganhoso, porque da a entender que sólo hay uno, y que una vez solucionado ya no tenemos nada que temer. Proponemos aquí una lista de cinco amenazas tales que podríamos imaginar solucionar cada una de ellas sin solucionar la siguiente. Problema: hasta que no resolvamos la última, no hemos terminado.

**1. Los LLM de hoy.**
Si uno interactúa con Chat GPT o Claude, no tiene generalmente la impresión de estar frente a algo capaz de destruir a la humanidad. Y, de hecho, millones de personas usan LLMs diariamente. Las cosas podrían haber evolucionado de otra manera, pero esta amenaza parece haber sido evitada. Pero ?nos garantiza eso que las siguientes lo estarán?

**2. Los LLM de mañana**
?Qué ocurrirá cuando Chat GPT o Claude sean capaces de resolver problemas inaccesibles para los humanos en cuestión de segundos? ?O sean capaces de actuar siguiendo planes que se extiendan a los largo de meses o anhos? ?Y sean capaces de almacenar nuevos conocimientos, de manera que tengan algo parecido a una identidad?

**3. Modelos con percepción y acción**
?Qué ocurrirá cuando haya un LLM conectado a un robot capaz de viajar por el mundo, interactuar con otros humanos y, sobre todo, interactuar con otros LLM?

**4. Arquitecturas futuras** 
?Qué ocurrirá cuando dentro de 2 o 3 anhos se descubra (probablemente gracias a una LLM) una arquitectura muy distinta a las LLMs capaz de resolver problemas más eficientemente que ellos? ?Nos servirá de protección el hecho de que las LLM no hayan resultado peligrosas?

**5. La amenaza final** 
Nadie sabe cuántas arquitecturas cada vez mejores existen, esperando ser descubiertas. Existen incentivos económicos enormes para seguir explorándolas. Y, muy pronto, las LLM actuales estarán en condición de producir ellas nuevas arquitecturas. ?Cómo podemos evitar que alguna de esas arquitecturas futuras (la vigésima, o quizá la segunda) acabe con la humanidad? 

Resolver el problema para una arquitectura concreta (como los LLM actuales) no garantiza nada con respecto a la amenaza final.


#### Chat
instructions:: Habla en español. El estudiante acaba de leer una lista de cinco amenazas. Pregúntale cuál cree que es la más cercana y cuál le parece que llegará antes de lo que la gente espera. Explora con él qué cambia de una amenaza a la siguiente: capacidad, autonomía, acceso al mundo, dificultad de supervisión. Si defiende que alguna amenaza nunca llegará, trátalo como una postura legítima y pregúntale qué evidencia le haría cambiar de opinión. Respuestas breves (menos de 120 palabras), una pregunta cada vez, sin elogios genéricos. 


#### Question: Open
id:: e5427907-dbaf-4a49-87a4-920e90657577
content:: Vuelve a lo que escribiste al principio del módulo sobre qué haría peligrosa a una IA. ¿Ha cambiado tu respuesta? ¿Qué añadirías o quitarías?
feedback-instructions:: Responde en español, en 2 o 3 frases, sin elogios genéricos. Señala un cambio concreto en su forma de pensar si lo hay. Si dice que no ha cambiado nada, pregúntale qué argumento del módulo le ha parecido más débil.

# Submodule: 6. Estrategias Godzilla

# Lens: Estrategias Godzilla
id:: 4b05fbcb-4301-414e-99a7-52798bab343b
tldr:: Usar una IA poderosa para vigilar o controlar a otra es como pedirle a Godzilla que luche contra Mega-Godzilla: aunque gane, la ciudad queda destruida.
summary_for_tutor:: Traducción al español de "Godzilla Strategies" (John Wentworth, 2022, LessWrong), publicada con permiso del autor. Idea central: las estrategias de alineamiento que consisten en usar una IA potente para supervisar, depurar o alinear otra IA potente son frágiles, porque en cuanto algo sale mal, el plan se rompe y quedan uno o dos "monstruos" sueltos.
reading_minutes:: 5

#### Text
content::
_Adaptación de «[Godzilla Strategies](https://www.lesswrong.com/posts/DwqgLXn5qYC7GqExF/godzilla-strategies)»_

> Pedirle a Godzilla que impida que Mega-Godzilla destruya Japón NO VA A HACER SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO. Es mejor no jugar con monstruos, en vez de intentar diseñar un complejo sistema de contrapesos entre monstruos y luego esperar que los monstruos no hagan lo que los monstruos siempre hacen, porque si no lo hicieran, se llamarían *florecitas* o *abrazos de cachorrito* y no *monstruos*.

Hay muchas estrategias para alinear una IA que podrían describirse como "pidámosle a Godzilla que impida que Mega-Godzilla destruya Japón". Usar una IA para supervisar a otra IA. Hacer que dos IA debatan entre sí. Usar una IA quizá un poco alineada para ayudar a diseñar otra. Etcétera.

Es cierto que hay muchos debates sobre las distintas maneras en que la idea de pedirle a Godzilla que impida que Mega-Godzilla destruya Japón podría fallar. Quizá uno de los dos acabe siendo mucho más poderoso que el otro. Quizá los dos se pongan de acuerdo. Quizá el equilibrio de Nash entre Godzilla y Mega-Godzilla, para empezar, simplemente no sea muy bueno para los humanos. Etcétera. Estos modos de fallo son útiles para orientar la investigación técnica.

…pero me preocupa que hablar de los modos de fallo conocidos lleve a la gente a engañarse sobre la viabilidad estratégica de las estrategias Godzilla. Hace que la gente piense (de forma consciente e intencionada o no): "bueno, si pudiéramos resolver estos modos de fallo concretos, quizá pedirle a Godzilla que impida que Mega-Godzilla aterrorice Japón funcionaría".

Lo que me gusta de la analogía de Godzilla es que ofrece una intuición estratégica que se ajusta mucho mejor al mundo real. Cuando alguien afirma que su plan elaborado e ingenioso nos permitirá invocar a Godzilla sin peligro para que luche contra Mega-Godzilla, la respuesta intuitiva y obviamente correcta es: "ESTO NO HACE SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO".

"¡Pero mira!", dice el investigador ingenioso. "¡Mi plan ingenioso resuelve los problemas X, Y y Z!"

Respuesta:

![](https://www.greaterwrong.com/proxy-assets/5PSBG1ND5EPTMBOGUECD4CV136)

Uy.

"Vale, pero ¿y si lo implementáramos realmente bien?", pregunta el investigador ingenioso.

Respuesta:

![](https://www.greaterwrong.com/proxy-assets/5A0CMQNFV2C2S47AAK2SFNLGO0)

¡GROAAARRRRRRR!

"¡Venga ya!", dice el investigador ingenioso. "¡Ni siquiera te lo estás tomando en serio! Al menos di algo sobre _cómo_ fallaría."

Tranquilo, a eso vamos. Pero antes, imagina que eres el alcalde de Tokio y estás evaluando una propuesta para pedirle a Godzilla que luche contra Mega-Godzilla. Tus ingeniosos investigadores te han dado una larga explicación de cómo sus elaboradas e ingeniosas salvaguardas garantizarán que este plan no destruya Tokio. No se te ocurre ningún posible problema que no hayan abordado. ¿Deberías concluir que pedirle a Godzilla que luche contra Mega-Godzilla no acabará con Tokio destruida?

No. Evidentemente no. ESTO NO HACE SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO. Puede que no sepas explicar _por qué_ la respuesta es obviamente "no", pero pedirle a Godzilla que luche contra Mega-Godzilla va a destruir Tokio, obviamente, y tus intuiciones aciertan en eso aunque no seas capaz de formular argumentos ingeniosos.

Dicho esto, hablemos de por qué esas intuiciones son correctas y por qué la analogía de Godzilla funciona bien.

\## Planes frágiles y lo que no sabemos que no sabemos

El problema básico de los planes Godzilla es que son _frágiles_. En cuanto algo sale mal, el plan salta en pedazos, y entonces tienes entre uno y dos monstruos gigantes arrasando el centro de la ciudad.

Y, por supuesto, es una Ley fundamental del universo que nada sale nunca exactamente según lo previsto. Menos aún cuando intentas enfrentar a dos monstruos gigantes. Es el tipo de situación en la que _seguro_ habrá cosas que no sabemos que no sabemos.

Cosas que no sabemos que no sabemos + plan frágil = el precio de la vivienda en Tokio, desde luego, no sube.

¿Sabemos qué es exactamente lo que saldrá mal? No. ¿Saldrá algo mal? Estoy muy seguro de que sí. Y la fragilidad significa que, sea lo que sea lo que salga mal, saldrá muy mal. Cuando le pides a Godzilla que luche contra Mega-Godzilla, los errores son irrecuperables.

Si usamos una IA para supervisar a otra IA y algo sale mal, no es un error recuperable: para empezar, recurrimos a la ayuda de una IA precisamente porque sin ella no somos capaces de detectar los problemas relevantes. Si dos IA debaten entre sí con la esperanza de generar un buen plan para un humano y algo sale mal, no es un error recuperable: dependemos de las propias IA para detectar los problemas. Si usamos una IA quizá algo alineada para construir otra y algo sale mal, no es un error recuperable: si tuviéramos mejores formas de detectar el desalineamiento en la IA hija, ya las habríamos usado con la IA madre.

El mundo real siempre pondrá problemas inesperados en el camino de nuestros planes. Cuando le pides a Godzilla que luche contra Mega-Godzilla, esos problemas son irrecuperables. ESTO NO HACE SUBIR EL PRECIO DE LA VIVIENDA EN TOKIO.

_Nota meta: ¡espero que este post tenga una sección de comentarios animada! Antes de dejar el vigésimo comentario diciendo que quizá Godzilla luchando contra Mega-Godzilla sea mejor que Mega-Godzilla arrasando sin oposición, comprueba si alguien lo ha escrito ya, para que yo no tenga que escribir la misma respuesta veinte veces. (Pero, desde luego, deja ese comentario si eres el primero: he escrito este ensayo corto a propósito, contando con que buena parte de la discusión tendría lugar en los comentarios.)_

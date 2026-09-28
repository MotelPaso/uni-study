# Extreme Programming

_Original: https://www.danielsanmartin.cl/blog/xp/_


Según su autor, XP es un método ligero recomendado para desarrollar software con requisitos vagos o sujetos a cambios; es decir, básicamente sistemas comerciales, en la clasificación que adoptamos en el Capítulo 1. Al ser un método ágil, XP posee todas las características que mencionamos en la sección anterior, es decir: adopta ciclos cortos e iterativos de desarrollo, concede menos énfasis a la documentación y a los planes detallados, propone que el diseño de un sistema también se defina de forma incremental y sugiere que los equipos de desarrollo sean pequeños.

Sin embargo, XP no es un método prescriptivo, que defina un paso a paso detallado para construir software. En cambio, XP se define mediante un conjunto de valores, principios y prácticas de desarrollo. Es decir, XP se define inicialmente de forma abstracta, utilizando valores y principios que deben formar parte de la cultura y de los hábitos de los equipos de desarrollo de software. Después, esos valores y principios se concretan en una lista de prácticas de desarrollo. Frecuentemente, cuando deciden adoptar XP, los desarrolladores y las organizaciones se concentran en las prácticas. Sin embargo, los valores y principios son componentes clave del método, pues son los que dan sentido a las prácticas propuestas en XP. Dicho con mayor claridad, si una organización no está preparada para trabajar con el modelo mental de XP —representado por sus valores y principios—, también se recomienda no adoptar sus prácticas.

Primero presentaremos los valores y principios de XP. A continuación, se muestra una lista de ellos:

- **Valores**: comunicación, simplicidad, retroalimentación, coraje, respeto y calidad de vida.

- **Principios**: humanidad, economicidad, beneficios mutuos, mejoras continuas, las fallas ocurren, pasos pequeños y responsabilidad personal.

A continuación, describiremos las prácticas. Para facilitar su explicación, decidimos organizarlas en tres grupos: prácticas sobre el proceso de desarrollo, prácticas de programación y prácticas de gestión de proyectos. A continuación, se muestra una lista de las prácticas en cada grupo:

- **Prácticas sobre el proceso de desarrollo:** representante de los clientes, historias de usuario, iteraciones, releases, planificación de releases, planificación de iteraciones, planning poker, slack.

- **Prácticas de programación:** diseño incremental, programación en parejas, desarrollo guiado por pruebas (TDD), build automatizado, integración continua.

- **Prácticas de gestión de proyectos:** métricas, ambiente de trabajo, contratos con alcance abierto.

## Valores

XP defiende que el desarrollo de proyectos de software esté guiado por tres valores principales: comunicación, simplicidad y retroalimentación. De hecho, se argumenta que estos valores son universales para la convivencia humana. Es decir, no solo sirven para guiar proyectos de desarrollo, sino la propia vida en sociedad. Una buena comunicación es importante en cualquier proyecto, no solo para evitar errores, sino también para aprender de ellos. El segundo valor de XP es la simplicidad, pues en todo sistema complejo y desafiante existen sistemas o subsistemas más simples, que a veces no son considerados. Por último, existen riesgos en todos los proyectos de software: los requisitos cambian, la tecnología cambia, el equipo de desarrollo cambia, el mundo cambia, etc. Un valor que ayuda a controlar tales riesgos es estar abierto a la retroalimentación de los stakeholders, a fin de que las correcciones de rumbo se implementen lo antes posible. En otras palabras, es difícil desarrollar el sistema de software correcto en un primer y único intento. Frederick Brooks tiene una frase conocida sobre este fenómeno:

> “Planea desechar partes de tu sistema, porque lo harás.”

Por eso, la retroalimentación es un valor esencial para garantizar que las partes o versiones que serán descartadas se identifiquen lo antes posible, de modo que se disminuyan las pérdidas y el retrabajo. Además de los tres valores mencionados, XP también defiende otros valores, como coraje, respeto y calidad de vida.

## Principios

Los valores que mencionamos son abstractos y universales. Por otro lado, las prácticas que mencionaremos más adelante son procedimientos concretos y pragmáticos. Así, para unir estos dos extremos, XP defiende que los proyectos de software deben seguir un conjunto de principios. La imagen que se presenta es la de un río: de un lado están los valores y del otro las prácticas. Los principios —que describiremos ahora— hacen el papel de un puente que conecta ambos lados. Algunos de los principales principios de XP son los siguientes:

**Humanidad** (humanity, en inglés). El software es una actividad intensiva en el uso de capital humano. El principal recurso de una empresa de software no son sus bienes físicos —computadores, edificios, muebles o conexiones a Internet, por ejemplo— sino sus colaboradores. Un término que refleja bien este principio es peopleware, acuñado por Tom DeMarco en un libro con el mismo título (enlace). La idea es que la gestión de personas —incluyendo factores como expectativas, crecimiento, motivación, transparencia y responsabilidad— es fundamental para el éxito de los proyectos de software.

**Economicidad** (economics, en inglés). Si por un lado peopleware es fundamental, por otro lado el software es una actividad costosa, que demanda la asignación de recursos financieros considerables. Por lo tanto, hay que ser conscientes de que la otra parte, es decir, quien está pagando las cuentas del proyecto, espera resultados económicos y financieros. Por eso, en la gran mayoría de los casos, el software no puede desarrollarse solo para satisfacer la vanidad intelectual de sus desarrolladores. El software no es una obra de arte, sino algo que debe generar resultados económicos, como defiende este principio de XP.

**Beneficios mutuos**. XP defiende que las decisiones tomadas en un proyecto de software deben beneficiar a múltiples stakeholders. Por ejemplo, el contratante del software debe garantizar un buen ambiente de trabajo (peopleware); en contrapartida, el equipo debe entregar un sistema que agregue valor a su negocio (economicidad). Otro ejemplo: al escribir pruebas, un desarrollador se beneficia, pues estas ayudan a detectar errores en su código; pero las pruebas también ayudan a otros desarrolladores, que en el futuro tendrán más seguridad de que su código no introducirá regresiones —es decir, errores— en código que ya está funcionando. Un tercer y último ejemplo: el refactoring es una actividad que hace el código más limpio y fácil de entender, tanto para quien lo escribió como para quien en el futuro tendrá que mantenerlo. La frase todo negocio tiene que ser bueno para ambas partes resume bien este tercer principio de XP.

**Mejoras continuas** (en el libro de XP, el nombre original es improvements). Como expresa la frase de Kent Beck, ningún proceso de desarrollo de software es perfecto. Por eso, es más seguro trabajar con un sistema que se vaya mejorando continuamente, en cada iteración, con la retroalimentación de los clientes y de todos los miembros del equipo. Por el mismo motivo, XP no recomienda invertir una gran cantidad de tiempo en un diseño inicial y completo. En cambio, el diseño del sistema también es incremental, mejorando en cada iteración. Finalmente, las propias prácticas de desarrollo pueden mejorarse; para ello, el equipo debe reservar tiempo para reflexionar sobre ellas.

**Las fallas ocurren**. El desarrollo de software no es una actividad libre de riesgos. Como discutimos en el Capítulo 1, el software es una de las construcciones humanas más complejas. Por ello, las fallas son esperables en proyectos de desarrollo de software. En el contexto de este principio, las fallas incluyen errores (bugs), funcionalidades que no resultaron interesantes para los usuarios finales y requisitos no funcionales que no están siendo plenamente atendidos, como desempeño, usabilidad, privacidad, disponibilidad, etc. Evidentemente, XP no sostiene que estas fallas deban encubrirse. Sin embargo, no deben usarse para castigar a los miembros de un equipo. Por el contrario, las fallas forman parte del juego, si un equipo pretende entregar software con rapidez.

**Pasos pequeños**. Es mejor un progreso seguro, probado y validado, aunque sea pequeño, que grandes implementaciones con riesgo de ser descartadas por los usuarios. Lo mismo vale para las pruebas (que son útiles incluso cuando las unidades probadas son de menor granularidad), la integración de código (es mejor integrar diariamente que pasar por el estrés de realizar una gran integración después de semanas de trabajo) y las refactorizaciones (que deben ocurrir en pequeños pasos, cuando es más fácil verificar que el comportamiento del sistema se está preservando). En resumen, lo importante es garantizar mejoras continuas, aunque sean pequeñas, siempre que vayan en la dirección correcta. Estas pequeñas mejoras son mejores que grandes revoluciones, las cuales suelen no presentar resultados positivos, al menos cuando se trata del desarrollo de software.

**Responsabilidad personal** (que usamos como traducción de accepted responsibility). De acuerdo con este principio, los desarrolladores deben tener una idea clara de su papel y responsabilidad dentro del equipo. El motivo es que la responsabilidad no puede transferirse sin que la otra parte la acepte. Por ello, XP defiende que el ingeniero de software que implementa una historia —término que el método usa para los requisitos— debe ser también quien la pruebe y la mantenga.

**Mundo real**: Uno de los primeros sistemas en adoptar XP fue un sistema de nómina del fabricante de automóviles Chrysler, llamado Chrysler Comprehensive Compensation (C3) (enlace). El proyecto de este sistema comenzó a inicios de 1995 y, como no presentó resultados concretos, fue reiniciado al año siguiente bajo el liderazgo de Kent Beck. Otro miembro conocido de la comunidad ágil, Martin Fowler, participó en el proyecto como consultor. En el desarrollo del sistema C3 se usaron y probaron diversas ideas del método que pocos años después recibiría el nombre de XP.

## Prácticas sobre el proceso de desarrollo

XP —como otros métodos ágiles— recomienda la participación de los clientes en el proyecto. Es decir, además de desarrolladores, los equipos incluyen al menos un representante de los clientes, que debe conocer el dominio del sistema que se va a construir. Una de las funciones de este representante es escribir las historias de usuario (user stories), que es el nombre que XP da a los documentos que describen los requisitos del sistema que se implementará. Sin embargo, las historias son documentos resumidos, de apenas dos o tres oraciones, mediante las cuales el representante de los clientes define lo que desea que el sistema haga, usando su propio lenguaje.

Profundizaremos en el estudio de las historias de usuario en Scrum. Pero, por ahora, queremos adelantar que las historias se escriben en tarjetas de papel, normalmente a mano. Es decir, en lugar de documentos de requisitos detallados, las historias son documentos simples, centrados en las funcionalidades del sistema, siempre desde la perspectiva de sus usuarios. Como ejemplo, mostramos a continuación una historia de un sistema de preguntas y respuestas —similar al famoso Stack Overflow— que usaremos para explicar XP.

Publicar pregunta:

> Un usuario, cuando ha iniciado sesión en el sistema, debe ser capaz de publicar preguntas. Como es un sitio sobre programación, las preguntas pueden incluir bloques de código, los cuales deben presentarse con un formato diferenciado.

Observe que la historia tiene un título (Publicar pregunta) y una breve descripción, que no ocupa más de dos o tres oraciones. Suele decirse que las historias son un recordatorio para que luego ese requisito sea detallado verbalmente por el representante de los clientes.

Después de ser escritas por el representante de los clientes, las historias son estimadas por los desarrolladores. Es decir, son los desarrolladores quienes definen, aunque sea preliminarmente, cuánto tiempo será necesario para implementarlas. Frecuentemente, la duración de una historia se estima en story points, en lugar de horas u hombre/hora. En esos casos, se usa una escala entera para clasificar las historias como poseedoras de un cierto número de story points. El objetivo es definir un orden relativo entre las historias. Las historias más simples se estiman como de tamaño igual a 1 story point; las historias que son aproximadamente dos veces más complejas que las primeras se estiman con 2 story points, y así sucesivamente. Muchas veces se usa una secuencia de Fibonacci para definir la escala de posibles story points, como 1, 2, 3, 5, 8, 13 story points. En este caso, el objetivo es crear una escala que haga que las tareas sean progresivamente más difíciles y, al mismo tiempo, permita al equipo realizar comparaciones similares a la siguiente: ¿será que el esfuerzo para implementar esta tarea que planeamos estimar con 8 story points equivale al esfuerzo de implementar una tarea en la escala anterior (5 story points) más una tarea en la siguiente escala inferior (3 puntos)? Si es así, 8 story points es una buena estimación. Si no, lo mejor es estimar la historia con 5 story points.

**Profundización:** Una técnica usada para estimar el tamaño de las historias se conoce como **Planning Poker**. Funciona así: el representante de los clientes selecciona una historia y la lee a los desarrolladores. Después de la lectura, los desarrolladores interactúan con el representante de los clientes para aclarar posibles dudas y comprender mejor la historia. Hecho esto, cada desarrollador realiza su estimación del tamaño de la historia de forma independiente. Luego, todos levantan al mismo tiempo tarjetas con la estimación que pensaron, en story points. Estas tarjetas se distribuyeron previamente y contienen los números 1, 2, 3, 5, etc. Si hay consenso, el tamaño de la historia queda estimado y se pasa a la siguiente. Si no, el equipo debe iniciar una discusión para aclarar la razón de las diferentes estimaciones. Por ejemplo, los desarrolladores responsables de las estimaciones más discrepantes pueden explicar el motivo de su propuesta. Después de eso, se realiza una nueva votación y el proceso se repite hasta alcanzar el consenso.

La implementación de las historias ocurre en **iteraciones**, las cuales tienen una duración fija y bien definida, variando, por ejemplo, entre una y tres semanas. A su vez, las iteraciones forman ciclos más largos, llamados **releases**, de dos a tres meses, por ejemplo. La **velocidad** de un equipo es el número de story points que logra implementar en una iteración. Se sugiere que el representante de los clientes escriba historias que requieran al menos una release para ser implementadas. Es decir, en XP, el horizonte de planificación es una release, esto es, algunos meses.

**Aviso**: En XP, la palabra release tiene un sentido diferente del que se usa en gestión de configuración. En gestión de configuración, una release es una versión de un sistema que será puesta a disposición de sus usuarios finales. Como ya mencionamos en un aviso anterior, no necesariamente la versión del sistema al final de una release de XP tiene que ponerse en producción.

En resumen, para comenzar a usar XP necesitamos:

- Definir la duración de una iteración.

- Definir el número de iteraciones de una release.

- Un conjunto de historias, escritas por el representante de los clientes.

- Estimaciones para cada historia, realizadas por los desarrolladores.

- Definir la velocidad del equipo, es decir, el número de story points que puede implementar por iteración.

Una vez definidos los parámetros y documentos anteriores, el representante del cliente debe priorizar las historias. Para ello, debe definir cuáles historias se implementarán en las iteraciones de la primera release. En esta priorización debe respetarse la velocidad del equipo de desarrollo. Por ejemplo, supongamos que la velocidad de un equipo es de 25 story points por iteración. En ese caso, el representante del cliente no puede asignar historias a una iteración cuya suma de story points supere ese límite. La tarea de asignar historias a iteraciones y releases se llama **planificación de releases** (o también planning game, que fue el nombre adoptado en la primera edición del libro de XP).

Por ejemplo, supongamos el foro de preguntas y respuestas que mencionamos antes. La siguiente tabla resume el resultado de una posible planificación de releases. En esa tabla, estamos suponiendo que el representante de los clientes escribió 8 historias, que cada release tiene dos iteraciones y que la velocidad del equipo es de 21 story points por iteración (observe que la suma de los story points de cada iteración es exactamente igual a 21).

| Historia | Story Points | Iteración | Release |
| --- | --- | --- | --- |
| Registrar usuario | 8 | 1 | 1 |
| Publicar preguntas | 5 | 1 | 1 |
| Publicar respuestas | 3 | 1 | 1 |
| Pantalla de inicio | 5 | 1 | 1 |
| Gamificar preguntas/respuestas | 5 | 2 | 1 |
| Buscar preguntas/respuestas | 8 | 2 | 1 |
| Agregar etiquetas | 5 | 2 | 1 |
| Comentar preguntas/respuestas | 3 | 2 | 1 |

La tabla anterior sirve para reforzar dos puntos ya mencionados: (1) las historias en XP representan funcionalidades del sistema que se pretende construir; es decir, la implementación del sistema está guiada por sus funcionalidades; (2) los desarrolladores no opinan sobre el orden de implementación de las historias; eso lo decide el representante de los clientes, quien debe ser una persona capacitada y con autoridad para definir qué es lo más urgente e importante para la empresa que está contratando el desarrollo del sistema.

Una vez realizada la planificación de una release, comienzan las iteraciones. Antes que nada, el equipo de desarrollo debe reunirse para realizar la planificación de la iteración. El objetivo de esta planificación es descomponer las historias de una iteración en tareas, las cuales deben corresponder a actividades de programación que puedan asignarse a uno de los desarrolladores del equipo. Por ejemplo, la siguiente lista muestra las tareas para la historia Publicar preguntas, que es la primera historia que será implementada en nuestro sistema de ejemplo.

- Diseñar y probar la interfaz web, incluyendo diseño, plantillas CSS, etc.

- Instalar la base de datos, diseñar y crear tablas.

- Implementar la capa de acceso a datos.

- Instalar el servidor y probar el framework web.

- Implementar la capa de control, con operaciones para registrar, eliminar y actualizar preguntas.

- Implementar la interfaz web.

Como regla general, las tareas no deben ser complejas, y debe ser posible concluirlas en algunos días.

En resumen, un proyecto XP se organiza en:

- releases, que son conjuntos de iteraciones, con una duración total de algunos meses.

- iteraciones, que son conjuntos de tareas resultantes de la descomposición de historias, con una duración total de algunas semanas.

- tareas, con una duración de algunos días.

Definidas las tareas, el equipo debe decidir qué desarrollador será responsable de cada una. Hecho esto, comienza de hecho la iteración, con la implementación de las tareas.

Una iteración termina cuando todas sus historias han sido implementadas y validadas por el representante de los clientes. Así, al final de una iteración, las historias deben mostrarse al representante de los clientes, quien debe estar de acuerdo en que ellas, efectivamente, cumplen con lo que él especificó.

XP también defiende que los equipos, durante una iteración, programen algunas **holguras** (slacks), que son tareas que pueden posponerse, si es necesario. Como ejemplos, podemos citar el estudio de una nueva tecnología, la realización de un curso en línea, la preparación de una documentación o manual, o incluso el desarrollo de un proyecto paralelo. Algunas empresas, como Google, por ejemplo, son famosas por permitir que sus desarrolladores usen el 20% de su tiempo para desarrollar un proyecto personal (enlace). En el caso de XP, las holguras tienen dos objetivos principales: (1) crear un margen de seguridad en una iteración, que pueda usarse si alguna tarea demanda más tiempo del previsto; (2) permitir que los desarrolladores respiren un poco, pues el ritmo de trabajo en proyectos de desarrollo de software suele ser intenso y desgastante. Por ello, los desarrolladores necesitan un tiempo para realizar algunas tareas sin que exista una exigencia inmediata de resultados.

## Preguntas frecuentes

Ahora responderemos algunas preguntas sobre las prácticas de XP que acabamos de explicar.

**¿Cuál es la duración ideal de una iteración?**

Es difícil precisarlo, pues depende de las características del equipo, de la empresa contratante, de la complejidad del sistema que se va a desarrollar, etc. Las iteraciones cortas —por ejemplo, de una semana— propician una retroalimentación más rápida. Sin embargo, requieren un mayor compromiso de los clientes, pues cada semana debe validarse un nuevo incremento del producto. Además, requieren que las historias sean más simples. Por otro lado, iteraciones más largas —por ejemplo, de un mes— permiten que el equipo planifique y concluya las tareas con más tranquilidad. Sin embargo, se tarda un poco más en recibir retroalimentación de los clientes. Esta retroalimentación puede ser importante cuando los requisitos no son muy claros. Por ello, una elección intermedia podría ser algo como 2 o 3 semanas. Otra alternativa recomendada consiste en experimentar, es decir, probar y evaluar distintas duraciones antes de decidir.

**¿Qué hace el representante de los clientes durante las iteraciones?**

Al inicio de una release, corresponde al representante de los clientes escribir las historias de las iteraciones que formarán parte de esa release. Después, al final de cada iteración, le corresponde validar y aprobar la implementación de las historias. Sin embargo, durante las iteraciones, debe estar físicamente disponible para resolver dudas del equipo. Observe que una historia es un documento muy resumido; por ello, es natural que surjan dudas durante su implementación. Por eso, el representante de los clientes debe estar siempre disponible para reunirse con los desarrolladores, aclarar dudas y explicar detalles relativos a la implementación de las historias.

**¿Cómo elegir al representante de los clientes?**

Antes que nada, debe ser alguien que conozca el dominio del sistema y que tenga autoridad para priorizar historias. Como se detalla a continuación, existen al menos tres perfiles de representante de los clientes:

- Supongamos el desarrollo interno de un sistema, es decir, el departamento de sistemas de la empresa X está desarrollando un sistema para otro departamento Y de la misma empresa. En ese caso, el representante de los clientes debe ser un funcionario del departamento Y.

- Supongamos que el equipo de desarrollo fue contratado para desarrollar un sistema para la empresa X. Es decir, se trata de un desarrollo externalizado. En ese caso, el representante del cliente debe ser un funcionario de la empresa X, con pleno dominio del área del sistema y que vaya a ser uno de sus principales usuarios cuando esté terminado.

- Supongamos que el equipo de desarrollo de una empresa X fue designado para hacer un sistema destinado a un público externo a la empresa. Por ejemplo, un sistema similar a Stack Overflow. En ese caso, los clientes del sistema no son funcionarios de X, sino clientes externos. Entonces, el representante de los clientes debe ser alguien del área de marketing, ventas o negocios de la empresa X. En última instancia, puede ser el dueño de la empresa. En cualquier caso, la sugerencia es que sea una persona cercana al problema y lo más alejada posible de la solución. Por eso mismo, debe evitarse que sea un desarrollador o un gerente de proyecto. El tipo de representante de los clientes que mencionamos en este punto a veces se llama user proxy.

**¿Cómo definir la velocidad del equipo?**

No existe una bala de plata para esta cuestión. Esta definición depende de la experiencia del equipo y de sus miembros. Si ya participaron en proyectos semejantes al que están iniciando, ciertamente esta será una cuestión menos difícil. En caso contrario, hay que experimentar e ir ajustando la velocidad en las iteraciones siguientes.

**¿Las historias pueden incluir tareas de instalación de infraestructura de software?**

No, las historias son especificadas por el representante de los clientes, que es un profesional no especializado en Ingeniería de Software. Por lo tanto, no suele tener conocimiento de infraestructura de software. Sin embargo, una historia puede dar origen a una tarea como instalar y probar la base de datos. En resumen, las historias están asociadas a requisitos funcionales; para implementarlas se crean tareas, que pueden estar asociadas a requisitos funcionales, no funcionales o tareas técnicas, como instalación de bases de datos, servidores, frameworks, etc.

**La historia X depende de la historia Y, pero el representante de los clientes priorizó X antes que Y. ¿Qué debo hacer?**

Por ejemplo, supongamos que en el sistema de ejemplo el representante de los clientes asignó la historia Publicar pregunta a la iteración 2 y la historia Publicar respuesta a la iteración 1. La pregunta entonces es la siguiente: ¿el equipo debe respetar esa asignación? Sí, pues la regla es clara: el representante de los clientes es la autoridad final cuando se trata de definir el orden de implementación de las historias. Entonces, puede surgir la siguiente pregunta: ¿cómo vamos a publicar respuestas si no tenemos preguntas? Para ello, basta con implementar algunas preguntas fijas, que no puedan ser modificadas por los usuarios. En la iteración 1, cuando el cliente abra el sistema, esas preguntas aparecerán por defecto, quizá con un diseño muy simple, y entonces el cliente podrá usar el sistema solo para responder esas preguntas fijas.

**¿Cuándo termina un proyecto XP?**
Cuando el representante de los clientes decide que las historias ya implementadas son suficientes y que no hay nada más relevante que deba implementarse.

## Prácticas de programación

El nombre Extreme Programming fue elegido porque XP propone un conjunto de prácticas de programación innovadoras, principalmente para la época en que fueron propuestas, a finales de la década de 1990. En realidad, XP es un método que da gran importancia a las tareas de programación y producción de código. Esta importancia debe entenderse en el contexto de la época, cuando existía una diferencia entre analistas y programadores. Los analistas se encargaban de elaborar el diseño de alto nivel de un sistema, definiendo sus principales componentes, clases e interfaces. Para ello, se recomendaba el uso de un lenguaje de modelado gráfico, como UML, que veremos en el Capítulo 4 de este libro. Concluida la fase de análisis y diseño, comenzaba la fase de codificación, que quedaba a cargo de los programadores. Así, en la práctica, existía una jerarquía entre estos roles, siendo el rol de analista el de mayor prestigio. Los métodos ágiles —y, particularmente, XP— acabaron con esa jerarquía y comenzaron a defender la producción de código con funcionalidades desde las primeras semanas de un proyecto.

Pero XP no solo acabó con la gran fase de diseño y análisis al inicio de los proyectos. El método también propuso un nuevo conjunto de prácticas de programación, incluyendo programación en parejas, pruebas automatizadas, desarrollo guiado por pruebas (TDD), builds automatizados, integración continua, etc. La mayoría de estas prácticas pasó a ser ampliamente adoptada por la industria del software y hoy son prácticamente obligatorias en la mayoría de los proyectos, incluso en aquellos que no usan un método ágil.

En esta sección estudiaremos las prácticas de programación de XP.

**Diseño incremental.**
Como se afirmó en los párrafos anteriores, en XP no existe una fase de diseño y análisis detallados, conocida como Big Design Up Front (BDUF), la cual es una de las principales fases de los procesos tipo Waterfall. La idea es que el equipo debe reservar tiempo para definir el diseño del sistema que se está desarrollando. Sin embargo, esto debe ser una actividad continua e incremental, en lugar de concentrarse al inicio del proyecto, antes de cualquier codificación. En este caso, la simplicidad es el valor de XP que orienta esta opción por un diseño también incremental. Se argumenta que, cuando el diseño se concentra al inicio del proyecto, se corren diversos riesgos, pues los requisitos aún no están totalmente claros para el equipo, ni siquiera para el representante de los clientes. Por ejemplo, se pueden sobrevalorar algunos requisitos que más tarde resultarán menos importantes; de forma inversa, se pueden subvalorar otros requisitos que luego, con el avance de la implementación, adquirirán mayor protagonismo. Sin mencionar que nuevos requisitos pueden surgir a lo largo del proyecto, haciendo que el diseño inicial quede desactualizado y sea menos eficiente.

Por ello, XP defiende que el momento ideal para pensar en el diseño es cuando este se revele importante. Frecuentemente, se usan dos frases para motivar y justificar esta práctica: *haz la cosa más simple que pueda funcionar (do the simplest thing that could possibly work) y no lo vas a necesitar (you aren’t going to need it)*, esta última conocida por la sigla YAGNI.

Dos observaciones son importantes para comprender mejor la propuesta de diseño incremental. Primero, los equipos experimentados suelen tener una buena aproximación al diseño ya en la primera iteración. Por ejemplo, ya saben que se trata de un sistema con interfaz web, con una capa de lógica no trivial, pero tampoco demasiado compleja, y luego con una capa de persistencia y una base de datos, seguramente relacional. Es decir, solo la oración anterior ya define gran parte del diseño que debe adoptarse. Como segunda observación, nada impide que en la primera iteración el equipo cree una tarea técnica para discutir y refinar el diseño que comenzará a adoptar en el sistema.

Finalmente, el diseño incremental solo es posible si se adopta en conjunto con las demás prácticas de XP, principalmente el **refactoring**. XP defiende que el refactoring debe aplicarse continuamente para mejorar la calidad del diseño. Por ello, toda oportunidad de refactorización, orientada a facilitar la comprensión y la evolución del código, no puede dejarse para después.

**Programación en parejas.**
Junto con el diseño incremental, la programación en parejas es una de las prácticas más polémicas de XP. A pesar de ser polémica, la idea es simple: toda tarea de codificación —incluyendo la implementación de una nueva historia, de una prueba o la corrección de un error— debe ser realizada por dos desarrolladores trabajando juntos, compartiendo el mismo teclado y monitor. Uno de los desarrolladores es el **líder** (o driver) de la sesión, quedándose con el teclado y el ratón. Al segundo desarrollador le corresponde la función de revisor y cuestionador, en el buen sentido, del trabajo del líder. Este segundo desarrollador se llama **navegador**. El nombre proviene de los rallies automovilísticos, en los cuales los pilotos van acompañados de un navegante.

Con la programación en parejas se espera mejorar la calidad del código y del diseño, pues dos cabezas piensan mejor que una. Además, la programación en parejas contribuye a difundir el conocimiento sobre el código, que no queda en manos y en la cabeza de un solo desarrollador. Por ejemplo, no es raro encontrar sistemas en los que un determinado desarrollador tiene dificultades para salir de vacaciones, pues solo él conoce una parte crítica del código. Como tercera ventaja, la programación en parejas puede usarse para entrenar a desarrolladores menos experimentados en tecnologías de desarrollo, algoritmos y estructuras de datos, patrones y principios de diseño, escritura de pruebas, técnicas de depuración, etc.

Por otro lado, también existen costos económicos derivados de la adopción de la programación en parejas, ya que se asignan dos programadores para realizar una tarea que, en principio, podría ser realizada por uno solo. Además, muchos desarrolladores no se sienten cómodos con esta práctica. Para ellos resulta incómodo —desde el punto de vista emocional y cognitivo— discutir cada línea de código y cada decisión de implementación con un colega. Para aliviar esta incomodidad, XP propone que las parejas se cambien en cada sesión. Estas pueden durar, por ejemplo, 50 minutos, seguidos de una pausa de 10 minutos para descansar. En la siguiente sesión, se cambian las parejas y los roles (líder versus revisor). Así, si en una sesión actuaste como revisor del programador X, en la siguiente pasarás a ser el líder, pero teniendo a otro desarrollador Y como revisor.

**Mundo real**: En 2008, dos investigadores de Microsoft Research, Andrew Begel y Nachiappan Nagappan, realizaron una encuesta con 106 desarrolladores de la empresa, para captar su percepción sobre la programación en parejas (enlace). Casi el 65% de los desarrolladores respondió positivamente a una primera pregunta sobre si la programación en parejas estaba funcionando bien para ellos (pair programming is working well for me). Cuando se les preguntó sobre los beneficios de la programación en parejas, las respuestas fueron las siguientes: reducción en el número de errores (62%), producción de código de mejor calidad (45%), difusión del conocimiento sobre el código (40%) y oportunidad de aprendizaje con los compañeros (40%). Por otro lado, los costos de la práctica fueron señalados como su principal problema (75%). Sobre las características de la pareja ideal, la respuesta más común fue complementariedad de habilidades (38%). Es decir, los desarrolladores prefieren emparejarse con una persona que les ayude a superar sus puntos débiles.

Más recientemente, diversas empresas comenzaron a adoptar la práctica de **revisión de código**. La idea es que todo código producido por un desarrollador debe ser revisado y comentado por otro desarrollador, pero de forma *offline* y asíncrona. Es decir, en esos casos, el revisor no estará físicamente al lado del líder.

**Propiedad colectiva del código.**
La idea es que cualquier desarrollador —o pareja de desarrolladores trabajando junta— puede modificar cualquier parte del código, ya sea para implementar una nueva funcionalidad, corregir un error o aplicar un refactoring. Por ejemplo, si descubriste un error en algún punto del código, adelante y corrígelo. Para ello, no necesitas autorización de quien implementó ese código o de quien realizó el último mantenimiento.

**Pruebas automatizadas.**
Esta es una de las prácticas de XP que alcanzó mayor éxito. La idea es que las pruebas manuales —un ser humano ejecutando el programa, proporcionando entradas y verificando las salidas producidas— constituyen un procedimiento costoso y que no puede reproducirse en todo momento. Por ello, XP propone la implementación de programas —llamados pruebas— para ejecutar pequeñas unidades de un sistema, como métodos, y verificar si las salidas producidas son las esperadas. Esta práctica prosperó porque, más o menos en la misma época de su proposición, se desarrollaron los primeros frameworks de pruebas unitarias, como JUnit, cuya primera versión, implementada por Kent Beck y Erich Gamma, data de 1997.

**Desarrollo guiado por pruebas (TDD).**
Esta es otra práctica de programación innovadora propuesta por XP. La idea es simple: si en XP todo método debe tener pruebas, ¿por qué no escribirlas primero? Es decir, se implementa la prueba de un método y solo entonces su código. TDD, que también se conoce como test-first programming, tiene dos motivaciones principales: (1) evitar que la escritura de pruebas se deje siempre para mañana, pues son lo primero que debe implementarse; (2) al escribir una prueba, el desarrollador se coloca en el papel de cliente del método probado, es decir, primero piensa en su interfaz, en cómo los clientes deben usarlo, para luego pensar en la implementación. Con ello, se incentiva la creación de métodos más amigables desde el punto de vista de la interfaz proporcionada a los clientes.

**Build automatizado.**
Build es el nombre que se da a la generación de una versión de un sistema que sea ejecutable y que pueda ponerse en producción. Por tanto, incluye no solo la compilación del código, sino también la ejecución de otras herramientas como enlazadores y empaquetadores de código en archivos WAR, JAR, etc. En el caso de XP, la ejecución de las pruebas es otra etapa fundamental del proceso de build. Para automatizar este proceso se usan herramientas, como el sistema Make, que forma parte de las distribuciones del sistema operativo Unix desde la década de 1970. Más recientemente, surgieron otras herramientas de build, como Ant, Maven, Gradle, Rake, MSBuild, etc. En primer lugar, XP defiende que el proceso de build esté automatizado, sin ninguna intervención de los desarrolladores. El objetivo es liberarlos de tareas como ejecutar scripts, informar parámetros de línea de comandos, configurar herramientas, etc. Así, pueden concentrarse únicamente en la implementación de historias. En segundo lugar, XP defiende que el proceso de build sea lo más rápido posible, para que los desarrolladores reciban rápidamente retroalimentación sobre posibles problemas, como un error de compilación. En la segunda edición del libro de XP se recomienda un límite de 10 minutos para completar un build. Sin embargo, dependiendo del tamaño del sistema y de su lenguaje de programación, puede ser difícil cumplir ese límite. Por eso, lo más importante es centrarse en la regla general: procurar siempre automatizar y reducir el tiempo de build de un sistema.

**Integración continua.**
Los sistemas de software se desarrollan con el apoyo de sistemas de control de versiones (VCS, o Version Control System), que almacenan el código fuente del sistema y archivos relacionados, como archivos de configuración, documentación, etc. Hoy en día, el sistema de control de versiones más usado es, por ejemplo, git. Cuando se usa un VCS, los desarrolladores primero deben descargar (pull) el código fuente a su máquina local antes de comenzar a trabajar en una tarea. Hecho esto, deben subir (push) el código modificado. Este último paso se llama **integración** de la modificación en el código principal almacenado en el VCS. Sin embargo, entre un pull y un push, otro desarrollador puede haber modificado el mismo fragmento de código y realizado su integración. En ese caso, cuando el primer desarrollador intente subir su código, el sistema de control de versiones impedirá la integración, diciendo que existe un **conflicto.**

Los conflictos son problemáticos porque deben resolverse manualmente. Si un desarrollador A modificó la inicialización de una variable x con el valor 10, y otro desarrollador B, trabajando en paralelo con A, quisiera inicializar x con 20, eso representa un conflicto. Para resolverlo, A y B deben sentarse y discutir cuál es el mejor valor para inicializar x. Sin embargo, ese es un escenario simple. Los conflictos pueden ser más complejos, involucrar grandes fragmentos de código y más de dos desarrolladores. Por ello, la resolución de conflictos de integración suele demandar un gran esfuerzo, dando lugar a lo que se llama **integration hell.**

Por otro lado, evitar completamente los conflictos es imposible. Por ejemplo, no es posible conciliar automáticamente los intereses de dos desarrolladores cuando uno necesita inicializar x con 10 y otro con 20. Sin embargo, al menos puede intentarse disminuir el número y el tamaño de los conflictos. Para lograrlo, la idea de XP es simple: los desarrolladores deben integrar su código siempre, si es posible todos los días. Esta práctica se llama integración continua. El objetivo es evitar que los desarrolladores pasen mucho tiempo trabajando localmente en sus tareas sin integrar el código. Y, con ello, al menos disminuir las probabilidades y el tamaño de los conflictos.

Para garantizar la calidad del código que se está integrando con una frecuencia casi diaria, también suele usarse un servicio de **integración continua**. Antes de realizar cualquier integración, este servicio hace el build del código y ejecuta las pruebas. El objetivo es garantizar que el código no tenga errores de compilación y que pase todas las pruebas. Existen diversos servicios de integración continua, como Jenkins, TravisCI, CircleCI, etc. Por ejemplo, cuando se desarrolla un sistema usando GitHub, pueden activarse estos servicios en forma de plugins. Si el repositorio de GitHub es público, el servicio de integración continua es gratuito; si es privado, debe pagarse una suscripción.

**Mundo real:** En 2010, Laurie Williams, profesora de la Universidad de Carolina del Norte, en Estados Unidos, pidió a 326 desarrolladores que respondieran un cuestionario sobre su experiencia con métodos ágiles (enlace). En una de las preguntas, se pedía a los participantes clasificar la importancia de prácticas ágiles usando una escala de 1 a 5, en la cual la puntuación 5 debía reservarse solo para prácticas esenciales en el desarrollo ágil. Tres prácticas quedaron empatadas en primer lugar, con puntuación media de 4.5 y desviación estándar de 0.8. Son las siguientes: integración continua, iteraciones cortas (menos de 30 días) y definición de criterios para tareas concluidas (done criteria). Por otro lado, entre las prácticas en las últimas posiciones podemos citar planning poker (puntuación media 3.1) y programación en parejas (puntuación media 3.3).

## Prácticas de gestión de proyectos

**Ambiente de trabajo.**
XP defiende que el proyecto sea desarrollado por un equipo pequeño, con menos de 10 desarrolladores, por ejemplo. Todos ellos deben estar dedicados al proyecto. Es decir, deben evitarse equipos fraccionados, en los cuales algunos desarrolladores trabajan solo algunos días de la semana en el proyecto y los otros días en otro proyecto, por ejemplo.

Además, XP defiende que todos los desarrolladores trabajen en una misma sala, para facilitar la comunicación y la retroalimentación. También propone que el espacio de trabajo sea informativo, es decir, que, por ejemplo, se coloquen carteles en las paredes con las historias de la iteración, incluyendo su estado: historias pendientes, historias en curso e historias terminadas. La idea es permitir que el equipo pueda visualizar el trabajo que se está realizando.

Otra preocupación de XP es garantizar jornadas de trabajo sostenibles. Las empresas de desarrollo de software son conocidas por exigir largas jornadas de trabajo, con muchas horas extras y trabajo durante los fines de semana. XP defiende que esta práctica no es sostenible y que las jornadas de trabajo deben estar siempre cerca de las 40 horas, incluso en vísperas de entregas. Lo interesante es que XP es un método propuesto por desarrolladores, con gran experiencia en proyectos reales de desarrollo de software. Por tanto, deben haber sentido en carne propia los efectos de largas jornadas de trabajo. Entre otros problemas, estas pueden causar daños a la salud física y mental de los desarrolladores, así como incentivar la rotación del equipo, cuyos miembros estarán siempre pensando en un nuevo empleo.

**Contratos con alcance abierto.**
Cuando una empresa externaliza el desarrollo, existen dos posibilidades de contrato: con alcance cerrado o con alcance abierto. En los contratos con alcance cerrado, la empresa contratante define, aunque sea de forma mínima, los requisitos del sistema y la empresa contratada define un precio y un plazo de entrega. XP sostiene que estos contratos son arriesgados, porque los requisitos cambian y ni siquiera el cliente sabe anticipadamente, de manera precisa, qué quiere que haga el sistema. Así, los contratos de alcance fijo pueden hacer que la contratada entregue un sistema con problemas de calidad e incluso con algunos requisitos implementados de manera parcial o con errores, solo para no tener que pagar posibles multas. Por otro lado, cuando el alcance es abierto, el pago se realiza por hora trabajada. Por ejemplo, se acuerda que la empresa contratada asignará un equipo con cierto número de desarrolladores para trabajar a tiempo completo en el proyecto, usando las prácticas de XP. También se acuerda un precio por la hora de cada desarrollador. El cliente define las historias y las valida al final de cada iteración. El contrato puede rescindirse o renovarse después de cierto número de meses, lo que da al cliente la libertad de cambiar de empresa si no está satisfecho con la calidad del servicio prestado. Como es habitual en XP, el objetivo es abrir un flujo de comunicación y retroalimentación entre contratante y contratada, en lugar de forzar a esta última a entregar un producto con problemas conocidos solo para cumplir un contrato. En realidad, los contratos con alcance abierto son más compatibles con los principios del Manifiesto Ágil, que explícitamente valora la colaboración con el cliente más que la negociación de contratos.

**Métricas de proceso.**
Para que gerentes y ejecutivos puedan acompañar un proyecto XP, se recomienda el uso de dos métricas principales: número de errores en producción (que idealmente debería ser del orden de pocos errores por año) e intervalo de tiempo entre el inicio del desarrollo y el momento en que el proyecto comience a generar sus primeros resultados financieros (que también debería ser pequeño, del orden de un año, por ejemplo).

[← Volver](index.md)
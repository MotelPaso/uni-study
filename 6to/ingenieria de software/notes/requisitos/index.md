# Requerimientos de software

_Original: https://www.danielsanmartin.cl/blog/requisitos/_


> La parte más difícil de construir un sistema de software es decidir con precisión qué construir.

*Frederick Brooks*

## Introducción

Los requisitos definen lo que un sistema debe hacer y bajo qué restricciones. Los requisitos relacionados con la primera parte de esta definición —lo que un sistema debe hacer, es decir, sus funcionalidades— se denominan Requisitos Funcionales. En cambio, los requisitos relacionados con la segunda parte —bajo qué restricciones— se denominan Requisitos No Funcionales.

Volvamos a utilizar el ejemplo de un sistema de home banking, para ilustrar la diferencia entre estos dos tipos de requisitos. En un sistema de home banking, los requisitos funcionales incluyen informar el saldo y la cartola de una cuenta, realizar transferencias entre cuentas, pagar un boleto bancario, cancelar una tarjeta de débito, entre otros. Por su parte, los requisitos no funcionales están relacionados con la calidad del servicio prestado por el sistema, e incluyen características como desempeño, disponibilidad, niveles de seguridad, portabilidad, privacidad, consumo de memoria y de disco, entre otras. Por lo tanto, los requisitos no funcionales definen restricciones al funcionamiento del sistema. Por ejemplo, no basta con que el sistema de home banking implemente todas las funcionalidades requeridas por el banco. Además, debe tener una disponibilidad del 99,9 %, la cual actúa, por tanto, como una restricción a su funcionamiento.

Como expresó Frederick Brooks en la frase que abre esta sección, la definición de requisitos es una etapa crucial en la construcción de cualquier sistema de software. De nada sirve tener un sistema con el mejor diseño, implementado en el lenguaje más moderno, utilizando el mejor proceso de desarrollo y con alta cobertura de pruebas, si no satisface las necesidades de sus usuarios. Los problemas en la especificación de requisitos también tienen un alto costo. Pueden exigir trabajo adicional cuando se descubre —después de que el sistema ya está terminado— que los requisitos fueron especificados de manera incorrecta o que no se especificaron requisitos importantes. En el peor de los casos, se corre el riesgo de entregar un sistema que será rechazado por sus usuarios, porque no resuelve sus problemas.

Los requisitos funcionales, en la mayoría de los casos, se especifican en lenguaje natural. Por otro lado, los requisitos no funcionales se especifican de forma cuantitativa mediante métricas, como las descritas en la tabla siguiente.

| Requisito No Funcional | Métrica |
| --- | --- |
| Desempeño | Transacciones por segundo, tiempo de respuesta, latencia, rendimiento (*throughput*) |
| Espacio | Uso de disco, RAM, caché |
| Confiabilidad | % de disponibilidad, tiempo medio entre fallas (MTBF) |
| Robustez | Tiempo para recuperar el sistema después de una falla (MTTR); probabilidad de pérdida de datos después de una falla |
| Usabilidad | Tiempo de entrenamiento de usuarios |
| Portabilidad | % de líneas de código portables |

El uso de métricas evita especificaciones genéricas, como “el sistema debe ser rápido” y “debe tener alta disponibilidad”. En su lugar, es preferible definir que el sistema debe tener un 99,99 % de disponibilidad y que el 99 % de todas las transacciones realizadas en cualquier ventana de 5 minutos deben tener un tiempo de respuesta máximo de 1 segundo.

Algunos autores, como Ian Sommerville ([enlace](https://dl.acm.org/doi/book/10.5555/2851535)), también clasifican los requisitos en requisitos de usuario y requisitos de sistema. Los requisitos de usuario son requisitos de más alto nivel, escritos por los usuarios, normalmente en lenguaje natural y sin entrar en detalles técnicos. En cambio, los requisitos de sistema son técnicos, precisos y escritos por los propios desarrolladores. Normalmente, un requisito de usuario se expande en un conjunto de requisitos de sistema.

Supongamos, por ejemplo, un sistema bancario. Un requisito de usuario —especificado por los funcionarios del banco— puede ser el siguiente: el sistema debe permitir transferencias de dinero a una cuenta corriente de otro banco mediante TED. Este requisito da origen a un conjunto de requisitos de sistema, los cuales detallarán y especificarán el protocolo que se utilizará para realizar dichas transferencias entre bancos. Por lo tanto, los requisitos de usuario están más cerca del problema, mientras que los requisitos de sistema están más cerca de la solución.

## Ingeniería de Requisitos

Ingeniería de Requisitos es el nombre que se da al conjunto de actividades relacionadas con el descubrimiento, análisis, especificación y mantenimiento de los requisitos de un sistema. El término ingeniería se utiliza para reforzar que estas actividades deben realizarse de manera sistemática, a lo largo de todo el ciclo de vida de un sistema y, siempre que sea posible, apoyándose en técnicas bien definidas.

Las actividades relacionadas con el descubrimiento y la comprensión de los requisitos de un sistema se denominan Elicitación de Requisitos. Según el Diccionario Houaiss, elicitar (o eliciar) significa hacer salir, expulsar o extraer. En nuestro contexto, el término designa las interacciones de los desarrolladores de un sistema con sus stakeholders, con el objetivo de hacer salir, es decir, descubrir y comprender los principales requisitos del sistema que se pretende construir.

Se pueden utilizar diversas técnicas para la elicitación de requisitos, entre ellas entrevistas con stakeholders, aplicación de cuestionarios, lectura de documentos y formularios de la organización que contrata el sistema, realización de talleres con los usuarios, implementación de prototipos y análisis de escenarios de uso. También existen técnicas de elicitación de requisitos basadas en estudios etnográficos. Este término tiene su origen en la Antropología, donde designa el estudio de una cultura en su ambiente natural (ethnos, en griego, significa pueblo o cultura). Por ejemplo, para estudiar una nueva tribu indígena descubierta en la Amazonía, un antropólogo puede trasladarse a la aldea y pasar meses conviviendo con los indígenas para comprender sus hábitos, costumbres, lenguaje, etc. De manera análoga, en Ingeniería de Requisitos, la etnografía designa la técnica de elicitación de requisitos que recomienda que el desarrollador se integre al entorno de trabajo de los stakeholders y observe —normalmente durante algunos días— cómo desarrollan sus actividades. Nótese que esta observación es silenciosa, es decir, el desarrollador no interfiere ni opina sobre las tareas y eventos observados.

Una vez elicitados, los requisitos deben: (1) documentarse, (2) verificarse y validarse, y (3) priorizarse.

En el caso del desarrollo ágil, la documentación de requisitos se realiza de forma simplificada, mediante **historias de usuario**, como se estudió anteriormente. En cambio, en algunos proyectos todavía se exige un Documento de Especificación de Requisitos, en el cual todos los requisitos del software que se pretende construir —incluidos los requisitos funcionales y no funcionales— se documentan en lenguaje natural (portugués, inglés, etc.). En la década de 1990, incluso se propuso un estándar para los Documentos de Especificación de Requisitos, denominado Estándar IEEE 830. Este fue propuesto en el contexto de procesos Waterfall, es decir, procesos que poseen una larga fase inicial de levantamiento de requisitos. Las principales secciones de un documento de requisitos según el estándar IEEE 830 se muestran en la figura de la página siguiente.

*Documento de Requisitos según el Estándar IEEE 830*

Después de su especificación, los requisitos deben ser verificados y validados. El objetivo es garantizar que sean correctos, precisos, completos, consistentes y verificables, como se analiza a continuación.

Los requisitos deben ser correctos. Un contraejemplo es la especificación incorrecta de la fórmula para la remuneración de las cuentas de ahorro en un sistema bancario. Evidentemente, una imprecisión en la descripción de esa fórmula resultará en perjuicios para el banco o para sus clientes.

Los requisitos deben ser precisos, es decir, no deben ser ambiguos. Sin embargo, la ambigüedad ocurre con más frecuencia de lo que quisiéramos cuando usamos lenguaje natural. Por ejemplo, considérese esta condición: para aprobar, un estudiante necesita obtener 60 puntos en el semestre o 60 puntos en el Examen Especial y tener asistencia. Obsérvese que admite dos interpretaciones. La primera es la siguiente: (60 puntos en el semestre o 60 puntos en el Examen Especial) y tener asistencia. Sin embargo, también puede interpretarse como: 60 puntos en el semestre o (60 puntos en el Examen Especial y tener asistencia). Como se habrá notado, fue necesario usar paréntesis para eliminar la ambigüedad en el orden de las operaciones “y” y “o”.

Los requisitos deben ser completos. Es decir, no se debe olvidar especificar ciertos requisitos, especialmente si son importantes en el sistema que se pretende construir.

Los requisitos deben ser consistentes. Un contraejemplo ocurre cuando un stakeholder afirma que la disponibilidad del sistema debe ser del 99,9 % y otro considera que el 90 % ya es suficiente.

Los requisitos deben ser verificables, es decir, debe ser posible comprobar si se están cumpliendo. Un contraejemplo es un requisito que solo exige que el sistema sea amigable. ¿Cómo sabrán los desarrolladores si están cumpliendo esa expectativa de los clientes?

Por último, los requisitos deben ser priorizados. A veces, el término requisitos se interpreta de forma literal, es decir, como una lista de funcionalidades y restricciones obligatorias en los sistemas de software. Sin embargo, no siempre todo lo especificado por los clientes será implementado en las versiones iniciales. Por ejemplo, las restricciones de plazo y costo pueden postergar la implementación de ciertos requisitos.

Además, los requisitos pueden cambiar, porque el mundo cambia. Por ejemplo, en el sistema bancario que hemos usado como ejemplo, las reglas de remuneración de las cuentas de ahorro deben actualizarse cada vez que los organismos federales responsables de definirlas las modifiquen. Por lo tanto, si existe un documento de especificación de requisitos que documenta tales reglas, este debe actualizarse, al igual que el código fuente del sistema. Se denomina trazabilidad (traceability) a la capacidad de, dado un fragmento de código, identificar los requisitos implementados por él y viceversa; es decir, dado un requisito, identificar los fragmentos de código que lo implementan.

Antes de concluir, es importante mencionar que la Ingeniería de Requisitos es una actividad multidisciplinaria y compleja. Por ejemplo, factores políticos pueden hacer que ciertos stakeholders no colaboren con la elicitación de requisitos que amenacen su poder y estatus dentro de la organización. Otros stakeholders simplemente pueden no tener tiempo para reunirse con los desarrolladores y explicar los requisitos del sistema. La especificación de requisitos también puede verse afectada por una barrera cognitiva entre los stakeholders y los desarrolladores. Debido a esta barrera, los desarrolladores pueden no comprender el lenguaje y los términos utilizados por los stakeholders. Nótese que estos últimos tienden a ser especialistas de larga trayectoria en el área del sistema. Por ello, pueden expresarse usando un lenguaje muy específico.

**Mundo Real**: Para comprender los desafíos enfrentados en Ingeniería de Requisitos, en 2016 cerca de dos docenas de investigadores coordinaron una encuesta con 228 empresas desarrolladoras de software, distribuidas en 10 países, incluido Brasil. Cuando se les preguntó por los principales problemas enfrentados en la especificación de requisitos, las diez respuestas más comunes fueron las siguientes (incluyendo el porcentaje de empresas que señaló cada problema):

- Requisitos incompletos o no documentados (48 %)

- Fallas de comunicación entre los miembros del equipo y los clientes (41 %)

- Requisitos en constante cambio (33 %)

- Requisitos especificados de forma abstracta (33 %)

- Restricciones de tiempo (32 %)

- Problemas de comunicación entre los propios miembros del equipo (27 %)

- Stakeholders con dificultades para separar requisitos y soluciones (25 %)

- Falta de apoyo de los clientes (20 %)

- Requisitos inconsistentes (19 %)

- Falta de acceso a las necesidades de los clientes o del negocio (18 %)

### ¿Qué vamos a estudiar?

La siguiente figura resume, en parte, lo estudiado hasta ahora sobre requisitos. Muestra que los requisitos son el puente que conecta un problema del mundo real con un sistema de software que lo resuelve. Utilizaremos esta idea para motivar y presentar los temas que se abordarán a continuación.

*Los requisitos son el puente que conecta un problema del mundo real con un sistema de software que lo resuelve*

Los requisitos son el puente que conecta un problema del mundo real con un sistema de software que lo resuelve.

La figura sirve para ilustrar una situación muy común en Ingeniería de Requisitos: sistemas cuyos requisitos cambian con frecuencia o cuyos usuarios no saben especificar con precisión el sistema que desean. Cuando los requisitos cambian frecuentemente y el sistema no es de misión crítica, no vale la pena invertir años en la elaboración de un Documento Detallado de Requisitos. Se corre el riesgo de que, cuando este esté terminado, los requisitos ya estén obsoletos, o de que un competidor ya haya construido un sistema equivalente y dominado el mercado. En este tipo de sistemas, pueden adoptarse documentos simplificados de especificación de requisitos, llamados **Historias de Usuario**, e incorporar a un representante de los clientes, a tiempo completo, al equipo de desarrollo, para resolver dudas y explicar los requisitos a los desarrolladores. Dada la importancia de estos escenarios —sistemas cuyos requisitos están sujetos a cambios, pero que no son críticos—, se comenzará con el estudio de las Historias de Usuario.

Por otro lado, también existen sistemas con requisitos más estables. En esos casos, puede ser importante invertir en especificaciones de requisitos más detalladas. Estas especificaciones también pueden ser exigidas por ciertas empresas, que prefieren contratar el desarrollo de un sistema solo después de conocer todos sus requisitos. Finalmente, también pueden ser requeridas por organizaciones de certificación, especialmente en el caso de sistemas que involucran vidas humanas, como los de las áreas médica, de transporte o militar. En estos contextos, se estudiarán los **Casos de Uso**, que son documentos detallados para la especificación de requisitos.

Una tercera situación ocurre cuando ni siquiera se sabe con certeza si el problema que se quiere resolver es realmente un problema. Es decir, se podrían levantar todos los requisitos de ese problema e implementar un sistema que lo resuelva, pero aun así no habría seguridad de que dicho sistema tendrá éxito o usuarios. En tales casos, lo más prudente es dar un paso atrás y probar primero la relevancia del problema que se pretende resolver mediante un sistema de software. Una posible forma de hacerlo es construir un **Producto Mínimo Viable (MVP)**. Un MVP es un sistema funcional que posee únicamente el conjunto mínimo de funcionalidades necesarias para comprobar la viabilidad de un producto o sistema. Dada la importancia actual de estos escenarios —sistemas diseñados para resolver problemas en mercados desconocidos o inciertos—, también se abordará el estudio de los MVPs.

- [Historias de Usuario](/blog/hu/)

- [Casos de Uso](/blog/cu/)

- [MVP](/blog/mvp/)

- [Test A/B](/blog/testab/)

[← Volver](../ingsoft.md)
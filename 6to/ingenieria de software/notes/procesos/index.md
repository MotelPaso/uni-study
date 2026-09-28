# Procesos

_Original: https://www.danielsanmartin.cl/blog/procesos/_


> En el desarrollo de software, perfecto es un verbo, no un adjetivo. No existe un proceso perfecto. No existe un diseño perfecto. No existen historias perfectas. Sin embargo, puedes perfeccionar tu proceso, tu diseño y tus historias.

*Kent Beck*

### Importancia de los procesos

La producción de un automóvil en una fábrica automotriz sigue un proceso bien definido. Sin extender demasiado la explicación, primero se cortan y prensan las planchas de acero para dar forma a puertas, techos y capós. Después, el automóvil se pinta y se instalan el panel, los asientos, los cinturones de seguridad y el cableado. Por último, se instala la parte mecánica, incluyendo motor, suspensión y frenos.

Así como los automóviles, el software también se produce de acuerdo con un proceso, aunque ciertamente menos mecánico y más dependiente del esfuerzo intelectual. Un proceso de desarrollo de software define un conjunto de pasos, tareas, eventos y prácticas que deben ser seguidos por los desarrolladores de software en la producción de un sistema.

Algunos críticos de los procesos de software suelen hacer la siguiente pregunta: ¿por qué necesito seguir un proceso? Y además preguntan lo siguiente: ¿qué proceso usó Linus Torvalds en la implementación del sistema operativo Linux? ¿O cuál usó Donald Knuth en la implementación del formateador de textos TeX?

En realidad, la segunda parte de la pregunta no tiene mucho sentido, pues tanto Linux (en sus inicios) como TeX son proyectos individuales, liderados por un único desarrollador. En esos casos, la adopción de un proceso es menos importante. O, dicho de otra forma, el proceso en tales proyectos es personal, compuesto por los principios, prácticas y decisiones tomadas por su único desarrollador, y que tendrán impacto solo sobre él mismo.

Sin embargo, los sistemas de software actuales son demasiado complejos para ser desarrollados por una sola persona. Por ello, los casos de sistemas desarrollados por “héroes” serán cada vez más raros. En la práctica, los sistemas modernos son desarrollados en equipos.

Y estos equipos, para producir software con calidad y productividad, necesitan cierto orden, aunque sea mínimo. Por eso las empresas dan tanto valor a los procesos de software. Son el instrumento de que disponen para coordinar, motivar, organizar y evaluar el trabajo de sus desarrolladores, de manera que trabajen con productividad y produzcan sistemas alineados con los objetivos de la organización. Sin un proceso —aunque sea simplificado y liviano, como los procesos ágiles que estudiaremos— existe el riesgo de que los equipos de desarrollo empiecen a trabajar de forma descoordinada, generando productos sin valor para el negocio de la empresa. Finalmente, los procesos son importantes no solo para la empresa, sino también para los desarrolladores, pues les permiten tomar conciencia de las tareas y resultados que se espera de ellos. Sin un proceso, los desarrolladores pueden sentirse perdidos, trabajando de manera errática y sin alineación con los demás miembros del equipo.

### Manifiesto Ágil

Los primeros procesos de desarrollo de software —del tipo Waterfall, propuestos aún en la década de 1970— eran estrictamente secuenciales, comenzando con una fase de especificación de requisitos hasta llegar a las fases finales de implementación, pruebas y mantenimiento del sistema.

Si consideramos el contexto histórico, esta primera visión del proceso era natural, puesto que los proyectos de ingeniería tradicional también son secuenciales y están precedidos por una planificación detallada. Todas las fases también generan documentación detallada del producto que se está desarrollando. Por eso, nada más natural que la naciente Ingeniería de Software tomara como modelo los procesos de áreas más tradicionales, como Ingeniería Electrónica, Civil, Mecánica, Aeronáutica, etc.

Sin embargo, después de aproximadamente una década, comenzó a percibirse que el software es diferente de otros productos de ingeniería. Esta percepción se fue aclarando debido a los problemas frecuentes que enfrentaban los proyectos de software entre las décadas de 1970 y 1990. Por ejemplo, los cronogramas y presupuestos de estos proyectos no se cumplían. No era raro que proyectos enteros fueran cancelados, después de años de trabajo, sin entregar un sistema funcional a los clientes.

En 1994, un informe producido por la empresa de consultoría Standish Group reveló información más detallada sobre los proyectos de software de la época. Por ejemplo, el informe, que se hizo conocido con el sugestivo nombre de CHAOS Report (enlace), mostró que más del 55% de los proyectos excedían los plazos planificados entre un 51% y un 200%; al menos un 12% excedían los plazos en más de un 200%, como muestra el siguiente gráfico.

*CHAOS Report (1994): porcentaje de proyectos que excedían sus plazos (para cada rango de exceso)*

Los resultados en términos de costos no eran más alentadores: casi el 40% de los proyectos superaba el presupuesto entre un 51% y un 200%, como muestra el siguiente gráfico:

*CHAOS Report (1994): porcentaje de proyectos que excedían sus presupuestos (para cada rango de exceso)*

En 2001, un grupo de profesionales de la industria se reunió en la ciudad de Snowbird, en el estado norteamericano de Utah, para discutir y proponer una alternativa a los procesos tipo Waterfall que entonces predominaban. Esencialmente, comenzaron a defender que el software es diferente de los productos tradicionales de la ingeniería. Por ello, el software también demanda un proceso de desarrollo diferente.

Por ejemplo, los requisitos de un software cambian con frecuencia, más que los requisitos de un computador, de un avión o de un puente. Además, los clientes frecuentemente no tienen una idea precisa de lo que quieren. Es decir, se corre el riesgo de diseñar durante años un producto que, una vez terminado, ya no será necesario, ya sea porque el mundo cambió o porque cambiaron los planes y necesidades de los clientes. También diagnosticaron problemas en los documentos prescritos por los procesos Waterfall, incluidos documentos de requisitos, diagramas de flujo, diagramas, etc. Estos documentos eran detallados, pesados y extensos. Así, rápidamente se volvían obsoletos, pues cuando los requisitos cambiaban, los desarrolladores no propagaban los cambios a la documentación, sino solo al código.

Entonces decidieron sentar las bases para un nuevo concepto de proceso de software, las cuales quedaron registradas en un documento que llamaron Manifiesto Ágil. Como es breve, reproducimos su texto:

Por medio de este trabajo, hemos llegado a valorar:

- Individuos e interacciones, más que procesos y herramientas

- Software funcionando, más que documentación exhaustiva

- Colaboración con el cliente, más que negociación de contratos

- Respuesta al cambio, más que seguir un plan

La característica principal de los procesos ágiles es la adopción de ciclos cortos e iterativos de desarrollo, mediante los cuales un sistema se implementa de forma gradual, comenzando por aquello que es más urgente para el cliente. Inicialmente, se implementa una primera versión del sistema, con las funcionalidades que, según el cliente, son “para ayer”, es decir, de máxima prioridad. Luego, esa versión es validada por el cliente. Si es aprobada, se inicia un nuevo ciclo —o iteración— con algunas funcionalidades más, también priorizadas por los clientes. Normalmente, estos ciclos son cortos, con una duración de un mes, quizá incluso un poco menos. Así, el sistema se va construyendo de forma incremental, y cada incremento es debidamente aprobado por los clientes. El desarrollo termina cuando el cliente decide que todos los requisitos están implementados.

Las siguientes figuras comparan el desarrollo Waterfall y el Ágil.

*Desarrollo usando un proceso Waterfall. El sistema queda listo solo al final.*

*Desarrollo usando un proceso ágil. En cada iteración (representada por los rectángulos) se genera un incremento en el sistema (S++), que ya puede ser validado y probado por los usuarios finales.*

Sin embargo, la figura anterior puede sugerir que, en el desarrollo ágil, cada iteración es un mini-waterfall, incluyendo todas las fases de un proceso Waterfall. Esto no es cierto; en general, las iteraciones en métodos ágiles no son una línea de ensamblaje de tareas, como en Waterfall (más sobre esto en las próximas secciones). La figura también puede sugerir que al final de cada iteración se debe poner un sistema en producción, para uso de los usuarios finales. Esto tampoco es cierto. De hecho, el objetivo es entregar un sistema funcional, es decir, que realice tareas útiles. Sin embargo, la decisión de ponerlo en producción involucra otras variables, como riesgos para el negocio de la empresa, disponibilidad de servidores, campañas de marketing, elaboración de manuales, capacitación de usuarios, etc.

Otras características de los procesos ágiles incluyen:

- Menor énfasis en la documentación, es decir, solo debe documentarse lo esencial.

- Menor énfasis en planes detallados, pues muchas veces ni el cliente ni los ingenieros de software tienen, al inicio de un proyecto, una idea clara de los requisitos que deben implementarse. Esa comprensión va surgiendo a lo largo del camino, a medida que se producen y validan incrementos del producto. En otras palabras, lo importante en el desarrollo ágil es poder avanzar, incluso en entornos con información imperfecta, parcial y sujeta a cambios.

- Inexistencia de una fase dedicada al diseño (big design up front). En vez de eso, el diseño también es incremental. Evoluciona a medida que el sistema va naciendo, al final de cada iteración.

- Desarrollo en equipos pequeños, de alrededor de una decena de desarrolladores. O, dicho de otra forma, equipos que puedan alimentarse con dos pizzas, como popularizó el CEO de Amazon, Jeff Bezos.

- Énfasis en nuevas prácticas de desarrollo (al menos, para inicios de los años 2000), como programación en parejas, pruebas automatizadas e integración continua.

Debido a estas características, los procesos ágiles son considerados procesos ligeros, con pocas prescripciones y documentos.

Sin embargo, las características anteriores son genéricas y amplias; por eso se propusieron algunos métodos para ayudar a los desarrolladores a adoptar los principios ágiles de forma más concreta. Lo interesante es que todos ellos fueron propuestos, al menos en su primera versión, antes de la reunión de Utah, en 2001, que dio origen al Manifiesto Ágil.

Estudiaremos tres métodos ágiles:

- Extreme Programming (XP), propuesto por Kent Beck, en un libro publicado en 1999 (enlace). Una segunda edición del libro, que incluye una gran revisión, fue publicada en 2004. En este capítulo nos basaremos en esa edición más reciente.

- Scrum, propuesto por Jeffrey Sutherland y Ken Schwaber, en un artículo publicado en 1995 (enlace).

- Kanban, cuyos orígenes se remontan a un sistema de control de producción que comenzó a utilizarse en las fábricas de Toyota, aún en la década de 1950 (enlace). En los últimos 10 años, Kanban ha sido gradualmente adaptado para su uso en el desarrollo de software.

Profundización: Proceso es el conjunto de pasos, etapas y tareas que se usa para construir software. Toda organización usa un proceso para desarrollar sus sistemas, el cual puede ser ágil o waterfall, por ejemplo. O, quizá, ese proceso puede ser caótico. Sin embargo, el punto que queremos reforzar es que siempre existe un proceso. Por otra parte, método, en nuestro contexto, define y especifica un determinado proceso de desarrollo (la palabra método tiene su origen en el griego, donde significa camino para llegar a un objetivo). Así, XP, Scrum y Kanban son métodos ágiles o, de forma más extensa, son métodos que definen prácticas, actividades, eventos y técnicas compatibles con principios ágiles de desarrollo de software. Aprovechando que estamos tratando definiciones, también se usa frecuentemente el término metodología cuando se habla de procesos de software. Por ejemplo, es común ver referencias a metodologías para desarrollo de software, metodologías ágiles, metodología orientada a objetos, etc. La palabra metodología, en sentido estricto, denota la rama de la lógica que se ocupa de los métodos de las diferentes ciencias, según el Diccionario Houaiss. Sin embargo, la palabra también puede usarse como sinónimo de método, según el mismo diccionario. A pesar de ello, evitamos usar el término metodología y tratamos de emplear siempre el término método.

Aviso: Todo método de desarrollo debe entenderse como un conjunto de recomendaciones; corresponde a una organización analizar cada una y decidir si tiene sentido en su contexto. Como resultado, la organización puede incluso decidir adaptar estas recomendaciones para atender sus necesidades. Por tanto, probablemente no existan dos organizaciones que sigan exactamente el mismo proceso de desarrollo, aunque ambas digan que están desarrollando con Scrum, por ejemplo.

Mundo real: El éxito y el impacto de los procesos ágiles ha sido impresionante. Hoy, la gran mayoría de las empresas que desarrollan software, independientemente de su tamaño o del foco de su negocio, usan principios ágiles, en mayor o menor escala. Por citar algunos datos, en 2018, la encuesta de Stack Overflow incluyó una pregunta sobre el método de desarrollo más usado por los encuestados (enlace). Esa pregunta recibió 57 mil respuestas de desarrolladores profesionales y la gran mayoría mencionó métodos o prácticas ágiles, incluidas aquellas que estudiaremos en este capítulo, como Scrum (63% de las respuestas), Kanban (36%) y Extreme Programming (16%). Solo el 15% de los participantes marcó Waterfall como respuesta.

- [Extreme Programming](/blog/xp/)

- [Scrum](/blog/scrum/)

- [Kanban](/blog/kanban/)

- [Otros Métodos Iterativos](/blog/otros_procesos/)

[← Volver](../ingsoft.md)
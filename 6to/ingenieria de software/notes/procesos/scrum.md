# Scrum

_Original: https://www.danielsanmartin.cl/blog/scrum/_


## Introducción

Scrum es un método ágil, iterativo e incremental para la gestión de proyectos. Fue propuesto por Jeffrey Sutherland y Ken Schwaber, en un artículo publicado por primera vez en 1995 ([enlace](https://link.springer.com/chapter/10.1007/978-1-4471-0947-1_11). Entre los métodos ágiles, Scrum es el más conocido y utilizado. Probablemente, parte del éxito del método se explique por la existencia de una industria asociada a su adopción, que incluye la producción de libros, diversos cursos, consultorías y certificaciones.

Una pregunta que responderemos al inicio de esta sección se refiere a las diferencias entre Scrum y XP. Existen diversas pequeñas diferencias, pero la principal es la siguiente:

- XP es un método ágil orientado exclusivamente a proyectos de desarrollo de software. Para ello, XP incluye un conjunto de prácticas de programación, como pruebas unitarias, programación en parejas, integración continua y diseño incremental, que fueron estudiadas en la sección anterior, dedicada a XP.

- Scrum es un método ágil para la gestión de proyectos, que no necesariamente tienen que ser proyectos de desarrollo de software. Por ejemplo, la escritura de este libro —como comentaremos dentro de poco— es un proyecto que se está realizando usando conceptos de Scrum. Al tener un enfoque más amplio que XP, Scrum no propone ninguna práctica de programación.

Entre los métodos ágiles, Scrum es también el que está mejor definido. Esa definición incluye un conjunto preciso de roles, artefactos y eventos, que se listan a continuación. En el resto de esta sección, explicaremos cada uno de ellos.

- **Roles**: Propietario del Producto, Scrum Master, Desarrollador.

- **Artefactos**: Backlog del Producto, Backlog del Sprint, Tablero Scrum, Gráfico de Burndown.

- **Eventos**: Planificación del Sprint, Sprint, Reuniones Diarias, Revisión del Sprint, Retrospectiva.

### Roles

Los equipos Scrum están formados por un Propietario del Producto (Product Owner o simplemente PO), un Scrum Master y de tres a nueve desarrolladores.

El **Propietario del Producto** tiene exactamente el mismo papel que el Representante de los Clientes en XP, por lo que no volveremos a explicar su función en detalle. Pero él, como su propio nombre lo indica, debe poseer la visión del producto que será construido, siendo también responsable de maximizar el retorno de la inversión realizada en el proyecto. Como en XP, corresponde al Propietario del Producto escribir las historias de usuario y, por ello, debe estar siempre disponible para resolver dudas del equipo.

El **Scrum Master** es un rol característico y único de Scrum. Se trata del especialista en Scrum del equipo, siendo responsable de garantizar que las reglas del método estén siendo seguidas. Para ello, debe entrenar y explicar continuamente los principios de Scrum a los demás miembros del equipo. También debe desempeñar funciones de facilitador del trabajo y eliminador de impedimentos. Por ejemplo, supongamos que un equipo está enfrentando problemas con uno de los servidores de bases de datos, cuyos discos presentan fallas todos los días. Corresponde al Scrum Master intervenir ante los niveles adecuados de la empresa para garantizar que ese problema de hardware no dificulte el avance del equipo. Por otro lado, no es un gerente de proyecto tradicional. Por ejemplo, no es el líder del equipo, ya que todos en un equipo Scrum tienen el mismo nivel jerárquico.

Se suele decir que los equipos Scrum son **cross-funcionales** (o multidisciplinarios), es decir, deben incluir —además del Propietario del Producto y del Scrum Master— a todos los especialistas necesarios para desarrollar el producto, de forma que no dependan de miembros externos. En el caso de proyectos de software, esto incluye desarrolladores front-end, desarrolladores back-end, especialistas en bases de datos, diseñadores de interfaces, etc. Corresponde a estos especialistas tomar todas las decisiones técnicas del proyecto, incluyendo la definición del lenguaje de programación, la arquitectura y los frameworks que se usarán en el desarrollo. También les corresponde estimar el tamaño de las historias definidas por el Propietario del Producto, usando una unidad como story points, de modo semejante a lo que vimos en XP.

### Principales artefactos y eventos

En Scrum, los dos artefactos principales son el Backlog del Producto y el Backlog del Sprint, y los principales eventos son los sprints y la planificación de sprints, como describiremos a continuación.

- El **Backlog del Producto** es una lista de historias (y otros ítems de trabajo relevantes), ordenada por prioridades. Al igual que en XP, las historias son escritas y priorizadas por el Propietario del Producto y constituyen una descripción resumida de las funcionalidades que deben implementarse en el proyecto. Es importante mencionar además que el Backlog del Producto es un artefacto dinámico, es decir, debe actualizarse continuamente para reflejar cambios en los requisitos y en la visión del producto. Por ejemplo, a medida que el desarrollo avanza, pueden surgir ideas de nuevas funcionalidades, mientras que otras pueden perder importancia. Todas estas actualizaciones deben ser realizadas por el Propietario del Producto. De hecho, es precisamente por ser el dueño del Backlog del Producto que el Propietario del Producto recibe ese nombre.

- **Sprint** es el nombre que Scrum da a una iteración. Es decir, como todo método ágil, Scrum es un método iterativo, en el que el desarrollo se divide en sprints, de hasta un mes. Al final de un sprint, se debe entregar un producto con valor tangible para el cliente. El resultado de un sprint se llama un producto potencialmente listo para entrar en producción (potentially shippable product). Recuerde que el adjetivo potencial no hace obligatoria la entrada en producción, como se discutió en la Sección 2.2.

- La **Planificación del Sprint** es una reunión en la que todo el equipo se reúne para decidir las historias que serán implementadas en el sprint que va a comenzar. Por lo tanto, es el evento que marca el inicio de un sprint. Esta reunión se divide en dos partes. La primera es dirigida por el Propietario del Producto. Él propone historias para el sprint y el resto del equipo decide si tiene **elocidad** para implementarlas. La segunda parte es dirigida por los desarrolladores. En ella, descomponen las historias en tareas y estiman su duración. Sin embargo, el Propietario del Producto debe seguir presente en esta parte final, para resolver dudas sobre las historias seleccionadas para el sprint. Por ejemplo, puede decidirse cancelar una historia, pues resultó más compleja al ser descompuesta en tareas.

- El **Backlog del Sprint** es el artefacto generado al final de la Planificación del Sprint. Es una lista con las tareas del sprint, así como incluye la duración de las mismas. Al igual que el Backlog del Producto, el Backlog del Sprint también es dinámico. Por ejemplo, algunas tareas pueden resultar innecesarias y otras pueden surgir a lo largo del sprint. También puede alterarse la estimación de horas previstas para una tarea. Sin embargo, lo que no puede alterarse es el **objetivo del sprint** (sprint goal), es decir, la lista de historias que el Propietario del Producto seleccionó para el sprint y que el equipo de desarrollo se comprometió a implementar durante su duración. Así, Scrum es un método adaptable a cambios, pero siempre que estos ocurran entre sprints. Es decir, dentro del time-box de un sprint, el equipo de desarrollo debe tener tranquilidad y seguridad para trabajar con una lista cerrada de historias.

Terminada la reunión de planificación, comienza el sprint. Es decir, el equipo empieza a trabajar en la implementación de las tareas del backlog. Además de ser cross-funcionales, los equipos Scrum son **autoorganizados**, es decir, tienen autonomía para decidir cómo y por quién serán implementadas las historias.

Junto al Backlog del Sprint, suele colocarse un cuadro con tareas por hacer, en curso y finalizadas. Este cuadro —también llamado **Tablero Scrum** (Scrum Board)— puede fijarse en las paredes del entorno de trabajo, permitiendo que el equipo tenga diariamente una sensación visual sobre el avance del sprint. Véase un ejemplo en la figura siguiente.

*Ejemplo de Tablero Scrum, mostrando las historias seleccionadas para el sprint y las tareas en las que fueron descompuestas. Cada tarea en ese cuadro puede estar en uno de los siguientes estados: por hacer, en curso, en prueba o concluida.*

Una decisión importante en los proyectos Scrum involucra los criterios para considerar una historia o tarea como concluida (done). Estos criterios deben acordarse con el equipo y ser conocidos por todos sus miembros. Por ejemplo, en un proyecto de desarrollo de software, para que una historia sea marcada como concluida puede exigirse la implementación de pruebas unitarias, que deben estar todas pasando, así como la revisión del código por otro miembro del equipo. Además, el código debe haber sido integrado con éxito en el repositorio del proyecto. El objetivo de estos criterios es evitar que los miembros —de forma apresurada y basándose en código de baja calidad— consigan mover sus tareas a la columna de concluido.

Otro artefacto común en Scrum es el **Gráfico de Burndown**. Cada día del sprint, este gráfico muestra cuántas horas son necesarias para implementar las tareas que aún no están concluidas. Es decir, en el día X del sprint informa que quedan tareas por implementar que suman Y horas. Por lo tanto, la curva de un gráfico de burndown debe ser descendente, alcanzando el valor cero al final del sprint, si este fue exitoso. A continuación se muestra un ejemplo, asumiendo un sprint de 15 días.

*Gráfico de Burndown, asumiendo un sprint de 15 días*

## Otros eventos

Ahora describiremos tres eventos más de Scrum, específicamente **Reuniones Diarias**, Revisión del Sprint y Retrospectiva.

Scrum propone que se realicen Reuniones Diarias, de aproximadamente 15 minutos, en las que deben participar todos los miembros del equipo. Para que estas reuniones sean rápidas, deben realizarse con los miembros de pie; por eso también se conocen como **reuniones de pie** (standup meetings, o también daily scrum). En ellas, cada miembro del equipo debe responder a tres preguntas: (1) qué hizo el día anterior; (2) qué pretende hacer en el día actual; (3) y si está enfrentando algún problema más serio, es decir, un impedimento, en su tarea. Estas reuniones tienen como objetivo mejorar la comunicación entre los miembros del equipo, haciendo que compartan y socialicen el avance del proyecto. Por ejemplo, dos desarrolladores pueden darse cuenta, durante la reunión diaria, de que van a comenzar a modificar el mismo fragmento de código. Por lo tanto, sería recomendable que se reunieran, aparte del resto del equipo, para discutir esas modificaciones. Y, con ello, minimizar las posibilidades de posibles conflictos de integración.

La **Revisión del Sprint** (Sprint Review) es una reunión para mostrar los resultados de un sprint. En ella deben participar todos los miembros del equipo e idealmente otros stakeholders, invitados por el Propietario del Producto, que estén involucrados con el resultado del sprint. Durante esta reunión, el equipo demuestra, en vivo, el producto a los clientes. Como resultado, todas las historias del sprint pueden ser aprobadas por el Propietario del Producto. Por otro lado, si detecta problemas en alguna historia, esta debe volver al Backlog del Producto, para ser retrabajada en un próximo sprint. Lo mismo debe ocurrir con las historias que el equipo no concluyó durante el sprint.

La **Retrospectiva** es la última actividad de un sprint. Se trata de una reunión del equipo Scrum con el objetivo de reflexionar sobre el sprint que está terminando y, si es posible, identificar puntos de mejora en el proceso, en las personas, en las relaciones y en las herramientas utilizadas. Solo por dar un ejemplo, como resultado de una retrospectiva, el equipo puede acordar la importancia de que todos estén presentes, puntualmente, en las reuniones diarias, pues en los últimos sprints algunos miembros han estado llegando tarde. Véase, por tanto, que una retrospectiva no es una reunión para “lavar la ropa sucia” y para que los miembros se pongan a discutir entre sí. Si eso fuera necesario, debe hacerse en privado, en otras reuniones o con la presencia de gerentes de la organización. Después de la retrospectiva, el ciclo se repite, con un nuevo sprint.

Una característica destacada de todos los eventos Scrum es que tienen una duración bien definida, llamada **time-box** de la actividad. Por eso, ese término aparece siempre en los documentos de Scrum. Por ejemplo, véase esta frase de la Guía Oficial de Scrum: el corazón del método Scrum es un sprint, que tiene un time-box de un mes o menos y durante el cual se crea un producto done, usable y que potencialmente puede ser puesto en producción (enlace). El objetivo de establecer time-boxes es crear un flujo continuo de trabajo, así como fomentar el compromiso del equipo con el éxito del sprint y evitar la pérdida de foco.

La tabla siguiente muestra el time-box de los eventos Scrum. En el caso de eventos con un time-box máximo (ejemplo: planificación del sprint), el valor recomendado se refiere a un sprint de un mes. Si el sprint es menor, el time-box sugerido también debe ser menor.

| Evento | Time-box |
| --- | --- |
| Planificación del Sprint | máximo de 8 horas |
| Sprint | menos de 1 mes |
| Reunión Diaria | 15 minutos |
| Revisión del Sprint | máximo de 4 horas |
| Retrospectiva | máximo de 3 horas |

## Ejemplo: escritura de un libro

Suponga que un libro está siendo escrito usando artefactos y eventos de Scrum. Claro, solo algunos, porque el libro tiene un único autor que, en cierta medida, desempeña todos los roles previstos por Scrum. Suponga además, que desde el inicio del proyecto los capítulos del libro fueron planificados, constituyendo así el Backlog del Producto. La escritura de cada capítulo se considera como un sprint. En la reunión de Planificación del Sprint, se define la división del capítulo en secciones, que equivalen a las tareas. Entonces comienza la escritura de cada capítulo, es decir, se inicia un sprint. Por regla general, los sprints se planifican para tener una duración de dos meses. Para que quede más claro, se muestra a continuación el backlog del sprint actual, así como el estado de cada tarea, exactamente en el momento en que se está escribiendo este párrafo:

| Historia | Por hacer | En curso | Concluidas |
| --- | --- | --- | --- |
| Procesos de Desarrollo | Kanban | Scrum | Introducción |
|  | Cuándo no usar Métodos Ágiles |  | Manifiesto Ágil |
|  | Otros Procesos |  | XP |
|  | Ejercicios |  |  |

Imagine que se decidió adoptar un método ágil para la escritura de un libro con el fin de minimizar los riesgos de desarrollar un producto que no atienda a las necesidades de nuestros clientes, que, en esta primera versión, son estudiantes y profesores de asignaturas de Ingeniería de Software, principalmente en nivel de pregrado. Así, al final de cada sprint, se publica y divulga un capítulo, de modo que se reciba retroalimentación. Con ello, se evita una solución Waterfall, mediante la cual el libro sería escrito durante cerca de dos años sin recibir ningún tipo de retroalimentación.

Para finalizar, comentaremos sobre el criterio para la conclusión de un capítulo, es decir, para definir que un capítulo está finalizado (done). Ese criterio requiere la lectura y revisión completa del capítulo por parte del autor del libro. Concluida esa revisión, el capítulo se divulga preliminarmente a los miembros del Grupo de Investigación en Ingeniería de Software Aplicada, de la IEC/UCN.

## Preguntas frecuentes

Antes de concluir la sección, responderemos algunas preguntas sobre Scrum:

**¿Qué significa la palabra Scrum?**

El nombre no es una sigla, sino una referencia a la reunión de jugadores realizada en un partido de rugby para decidir quién se quedará con la pelota después de una infracción involuntaria.

**¿Qué es un squad?**

Ese término es un sinónimo de equipo ágil o equipo Scrum. El nombre fue popularizado por Spotify. Al igual que los equipos Scrum, los squads son pequeños, cross-funcionales y autoorganizados. También es común usar el nombre tribu para denotar un conjunto de squads.

**¿El Propietario del Producto puede ser un comité? En otras palabras, ¿puede existir más de un Propietario del Producto en un equipo Scrum?**

La respuesta es no. Solo un miembro del equipo ejerce esa función. El objetivo es evitar decisiones por comité, que tienden a generar productos cargados de funcionalidades, pero implementadas solo para satisfacer a determinados miembros del comité. Sin embargo, nada impide que el Propietario del Producto sirva de puente entre el equipo y otros usuarios con amplio dominio del área del producto que se está construyendo. De hecho, esa es una tarea esperada del Propietario del Producto, pues a veces existen requisitos que pertenecen al dominio de solo algunos colaboradores de la organización. Corresponde entonces al Propietario del Producto intermediar las conversaciones entre los desarrolladores y dichos usuarios.

**¿El Scrum Master debe ejercer su papel a tiempo completo?**

Idealmente, sí. Sin embargo, en equipos maduros, que conocen y practican Scrum desde hace bastante tiempo, a veces no es necesario tener un Scrum Master a tiempo completo. En esos casos, existen dos posibilidades: (1) permitir que el Scrum Master desempeñe ese rol en más de un equipo Scrum; (2) asignar la responsabilidad de Scrum Master a uno de los miembros del equipo. Sin embargo, si se adopta la segunda alternativa, el Scrum Master no debe ser también el Propietario del Producto. La razón es que una de las responsabilidades del Scrum Master es precisamente acompañar y ayudar al Propietario del Producto en sus tareas de escribir y priorizar historias de usuario.

**¿El Scrum Master necesita tener un título universitario en un programa del área de Computación?**

No, pues su función implica remover impedimentos y asegurar que el equipo siga los principios de Scrum. Por lo tanto, no es un solucionador de problemas técnicos, tales como errores, uso correcto de frameworks, implementación de funcionalidades, etc. Por otro lado, eso no impide que un desarrollador técnico, con formación superior en el área de Computación, asuma las funciones de Scrum Master, como vimos en la respuesta anterior. También existen certificaciones para Scrum Master, las cuales pueden ser requeridas por empresas que deciden adoptar Scrum.

Además de historias, ¿qué otros ítems pueden formar parte del Backlog del Producto?
También pueden registrarse en el Backlog del Producto ítems como errores (bugs) —principalmente aquellos más complejos y que requieren días para ser resueltos— y también mejoras en historias ya implementadas.

**¿Existen gerentes cuando se usa Scrum?**
La respuesta es sí. De hecho, los equipos Scrum son autónomos para implementar las historias priorizadas por el Propietario del Producto. Sin embargo, un proyecto demanda muchas otras decisiones que deben tomarse a nivel gerencial. Entre esas decisiones, podemos citar las siguientes:

Contratar y asignar miembros a los equipos Scrum; es decir, los desarrolladores no tienen autonomía para elegir en qué equipos van a trabajar. Esa es una decisión de nivel superior y, por lo tanto, tomada por gerentes.

Decidir los objetivos y responsabilidades de cada equipo, incluyendo el sistema —o parte de un sistema— que el equipo desarrollará usando Scrum. Por ejemplo, un equipo no decide, por su cuenta, que la organización necesita un nuevo sistema de contabilidad y entonces comienza a desarrollarlo. Esa es una decisión estratégica, que corresponde a los gerentes y ejecutivos de la organización.

Gestionar y administrar cuestiones de recursos humanos, incluyendo contrataciones de nuevos empleados, desvinculaciones, promociones, transferencias, capacitaciones, etc.

Evaluar si los resultados producidos por los equipos Scrum están, de hecho, generando beneficios y valor para la organización.

[← Volver](index.md)
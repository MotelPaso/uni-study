# Kanban

_Original: https://www.danielsanmartin.cl/blog/kanban/_


La palabra japonesa kanban significa tarjeta visual o tarjeta de señalización. Desde la década de 1950, el nombre también se usa para denotar el proceso de producción just-in-time utilizado en fábricas japonesas, principalmente en las de Toyota, donde fue usado por primera vez. El proceso también se conoce como Sistema de Producción de Toyota (TPS) o, más recientemente, como manufactura lean. En una línea de montaje, las tarjetas se usan para controlar el flujo de producción.

En el caso del desarrollo de software, Kanban fue usado por primera vez en Microsoft, en 2004, como parte de un esfuerzo liderado por David Anderson, entonces funcionario de la empresa ([enlace](https://isbnsearch.org/isbn/0984521402)). Según Anderson, Kanban es un método que ayuda a los equipos de desarrollo a trabajar a un ritmo sostenible, eliminando desperdicios, entregando valor con frecuencia y fomentando una cultura de mejoras continuas.

Para comenzar a explicar Kanban, usaremos una comparación con Scrum. En primer lugar, Kanban es más simple que Scrum, pues no utiliza ninguno de los eventos de Scrum, incluidos los sprints. Tampoco existe ninguno de los roles (Propietario del Producto, Scrum Master, etc.), al menos no de la forma rígida propuesta por Scrum. Finalmente, no existe ninguno de los artefactos de Scrum, con una única y central excepción: el tablero de tareas, que se llama Tablero Kanban (Kanban Board), y que también incluye el Backlog del Producto.

El Tablero Kanban se divide en columnas, de la siguiente manera:

- La primera columna es el backlog del producto. Como en Scrum, los usuarios escriben las historias, que van al backlog.

- Las demás columnas corresponden a los pasos que deben seguirse para transformar una historia de usuario en una funcionalidad ejecutable. Por ejemplo, se pueden tener columnas como Especificación, Implementación y Revisión de Código. La idea, por lo tanto, es que las historias se procesen paso a paso, de izquierda a derecha, como en una línea de montaje. Además, cada columna se divide en dos subcolumnas: en ejecución y concluidas. Por ejemplo, la columna Implementación tiene dos subcolumnas: tareas en implementación y tareas implementadas. Las tareas concluidas en un paso están esperando ser jaladas por un miembro del equipo hacia el paso siguiente. Por eso, Kanban se llama un sistema pull.

A continuación se muestra un ejemplo de Tablero Kanban. Observe que existe una historia en el backlog (H3), además de una historia (H2) que ya fue jalada por algún miembro del equipo al paso de especificación. Existen además cuatro tareas (T6 a T9) que fueron especificadas a partir de una historia anterior. Continuando, existen dos tareas en implementación (T4 y T5) y existe una tarea implementada y esperando ser jalada para revisión de código (T3). En el último paso, existe una tarea en revisión (T2) y una tarea cuyo procesamiento está concluido (T1). Por ahora, no se preocupe por la sigla WIP que aparece en todos los pasos, excepto en el backlog. La explicaremos en breve. Además, representamos las historias y tareas con las letras H y T, respectivamente. Sin embargo, en un tablero real, ambas son tarjetas autoadhesivas con una breve descripción. El Tablero Kanban puede montarse de esta manera en una de las paredes del entorno de trabajo del equipo.

| Backlog | Especificación<br>WIP | Implementación<br>WIP | Revisión de Código<br>WIP |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| H3 | H2 | T6 T7 T8 T9 | T4 T5 | T3 | T2 | T1 |

Ahora mostraremos una evolución del proyecto. Es decir, algunos días después, el Tablero Kanban pasó al siguiente estado (las tareas que avanzaron en el tablero están subrayadas y en rojo).

| Backlog | Especificación<br>WIP | Implementación<br>WIP | Revisión de Código<br>WIP |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| H3 |  | T8 T9<br><br>T10 T11 T12 | T4 T5<br><br>T6 T7 |  | T3 | T1<br><br>T2 |

Vea que la historia H2 desapareció, pues fue descompuesta en tres tareas (T10, T11 y T12). El objetivo de la fase de especificación es precisamente transformar una historia en una lista de tareas. Continuando, T6 y T7 —que antes estaban esperando— entraron en implementación. Por su parte, T3 entró en la fase de revisión de código. Finalmente, terminó la revisión de T2. Observe además que, en este momento, no existe ninguna tarea implementada y esperando ser jalada hacia revisión.

Como en otros métodos ágiles, los equipos Kanban son autoorganizados. Esto significa que tienen autonomía para definir qué tarea será jalada al siguiente paso. También son cross-funcionales, es decir, deben incluir miembros capaces de realizar todos los pasos del Tablero Kanban.

Por último, queda explicar el concepto de límites WIP (Work in Progress). Por regla general, los métodos de gestión de proyectos tienen como objetivo garantizar un ritmo sostenible de trabajo. Para ello, deben evitarse dos situaciones extremas: (1) que el equipo permanezca ocioso buena parte del tiempo, sin tareas que realizar; o (2) que el equipo quede sobrecargado de trabajo y, por ello, no logre producir software de calidad. Para evitar la segunda situación —la sobrecarga de trabajo—, Kanban propone un límite máximo de tareas que pueden estar en cada uno de los pasos de un Tablero Kanban. Ese límite se conoce como límite WIP, es decir, se trata del número máximo de tarjetas presentes en cada paso, contando aquellas de la primera subcolumna (en curso) y aquellas de la segunda subcolumna (concluidas) del paso. La excepción es el último paso, en el cual el WIP se aplica solo a la primera subcolumna, ya que no tiene sentido aplicar un límite al número de tareas concluidas por el equipo de desarrollo.

A continuación, reproducimos el último Tablero Kanban, pero con los límites WIP. Estos son los números que aparecen debajo del nombre de cada paso, en la primera fila del tablero. Es decir, en este Tablero Kanban se admite un máximo de 2 historias en especificación, 5 tareas en implementación y 3 tareas en revisión. Dejaremos para el final la explicación del límite WIP del paso Especificación. Pero podemos ver que existen 4 tareas en implementación (T4, T5, T6 y T7). Por lo tanto, están por debajo del WIP de ese paso, que es igual a 5 tareas. En Revisión de Código, el límite es de 3 tareas y también se está respetando, pues existe solo una tarea en revisión (T3). Observe que, para verificar el límite WIP, se cuentan las tareas en curso (primera subcolumna de cada paso) y concluidas (segunda subcolumna de cada paso), con excepción del último paso, en el cual se consideran solo las tareas de la primera subcolumna (T3, en el ejemplo).

| Backlog | Especificación<br>WIP(2) | Implementación<br>WIP(5) | Revisión de Código<br>WIP(3) |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| H3 |  | T8 T9<br><br> T10 T11 T12 | T4 <br>T5 <br> T6<br> T7 |  | T3 | T1<br> T2 |

Ahora explicaremos el WIP del paso Especificación. Para verificar el WIP de ese paso, se deben sumar las historias en especificación (cero en el tablero anterior) y las historias que ya fueron especificadas. En este caso, tenemos dos historias especificadas. Es decir, T8 y T9 son tareas que resultaron de la especificación de una misma historia. Y las tareas T10, T11 y T12 son resultado de la especificación de una segunda historia. Por lo tanto, para efectos del cálculo del WIP, tenemos dos historias en el paso, lo que está dentro de su límite, que también es 2. Para facilitar la visualización, suele representarse las tareas resultantes de la especificación de una misma historia en una sola fila. Siguiendo ese criterio, para calcular el WIP del paso Especificación, se deben sumar las historias de la primera subcolumna (cero, en nuestro ejemplo) con el número de filas de la segunda columna (dos).

Aún en el tablero anterior, y considerando los límites WIP, se tiene que:

- La historia H3, que está en el backlog, no puede ser jalada al paso Especificación, pues el WIP de ese paso está en el límite.

- Una de las tareas ya especificadas (T8 a T12) puede ser jalada a implementación, pues el WIP del paso está en 4, mientras que el límite es 5.

- Una o más tareas en implementación (T4 a T7) pueden ser finalizadas, lo que no altera el WIP del paso.

- La revisión de T3 puede ser finalizada.

Reforzando una vez más, el objetivo de los límites WIP es evitar que los equipos Kanban queden sobrecargados de trabajo. Cuando un desarrollador tiene muchas tareas que realizar —porque los límites WIP no se están respetando— la tendencia es que no logre concluir ninguna de esas tareas con calidad. Como ocurre habitualmente en cualquier actividad humana, cuando asumimos demasiados compromisos, la calidad de nuestras entregas disminuye mucho. Kanban reconoce este problema y, para evitar que ocurra, crea un mecanismo automático que impide que los equipos acepten trabajo más allá de su capacidad de entrega. Estos mecanismos, que son los límites WIP, sirven para uso interno del equipo y, más importante aún, para uso externo. Es decir, son el instrumento del que dispone un equipo para rechazar trabajo extra que está siendo empujado desde arriba hacia abajo por los gerentes de la organización, por ejemplo.

## Cálculo de los límites WIP

Ahora nos queda explicar cómo se definen los límites WIP. Existe más de una alternativa, pero adoptaremos una adaptación de un algoritmo propuesto por Eric Brechner —un ingeniero de Microsoft— en su libro sobre el uso de Kanban en el desarrollo de software ([enlace](https://dl.acm.org/doi/book/10.5555/2774938)). El algoritmo se describe a continuación.

Primero, debemos estimar cuánto tiempo, en promedio, una tarea permanecerá en cada paso del Tablero Kanban. Ese tiempo se llama lead time (LT). En nuestro ejemplo, supondremos los siguientes valores:

- LT(especificación) = 5 días

- LT(implementación) = 12 días

- LT(revisión) = 6 días

Observe que esta estimación considera una tarea promedio, pues sabemos que existirán tareas más complejas y otras más simples. Observe además que el lead time incluye el tiempo en cola, es decir, el tiempo que la tarea permanecerá en la segunda subcolumna de los pasos del Tablero Kanban, esperando ser jalada hacia el siguiente paso.

A continuación, debe estimarse el **throughput** (TP) del paso con mayor lead time del Tablero Kanban, es decir, el número de tareas producidas por día en ese paso. En nuestro ejemplo, y en la mayoría de los proyectos de desarrollo de software, ese paso es Implementación. Así, supongamos que el equipo es capaz de sostener la implementación de 8 tareas por mes. El **throughput** de ese paso es entonces:

8 / 21 = 0.38 tareas/día

Observe que estamos considerando que un mes tiene 21 días hábiles.

Por último, el WIP de cada paso se define así:

**WIP(paso) = TP × LT(paso)**

donde throughput se refiere al throughput del paso más lento, tal como fue calculado en el punto anterior.

Por lo tanto, obtendremos los siguientes resultados:

- WIP(especificación) = 0.38 × 5 = 1.9

- WIP(implementación) = 0.38 × 12 = 4.57

- WIP(revisión) = 0.38 × 6 = 2.29

Redondeando hacia arriba, los resultados finales quedan así:

- WIP(especificación) = 2

- WIP(implementación) = 5

- WIP(revisión) = 3

En el algoritmo propuesto por Eric Brechner, también se sugiere añadir un margen de error del 50% a los WIP calculados, para acomodar variaciones en el tamaño de las tareas, tareas bloqueadas debido a factores externos, etc. Sin embargo, como nuestro ejemplo es ilustrativo, no vamos a ajustar los WIP calculados anteriormente.

Como se afirmó, los límites WIP son el recurso ofrecido por Kanban para garantizar un ritmo de trabajo sostenible y la entrega de sistemas de software con calidad. El papel de estos límites es contribuir a que los desarrolladores no queden sobrecargados de tareas y, en consecuencia, no se vean inclinados a disminuir la calidad de su trabajo. De hecho, todo método de desarrollo de software tiende a ofrecer este tipo de recurso. Por ejemplo, en Scrum existe el concepto de sprints con time-boxes definidos, cuyo objetivo es evitar que los equipos acepten trabajar en historias que excedan su velocidad de entrega. Adicionalmente, una vez iniciado, el objetivo de un sprint no puede alterarse, de modo que se proteja al equipo de cambios diarios de prioridad. En el caso de los métodos Waterfall, el recurso para garantizar un flujo de trabajo sostenible y de calidad es la existencia de una fase detallada de especificación de requisitos. Con esta fase, la intención era ofrecer a los desarrolladores una idea clara del sistema que debían implementar.

## Ley de Little

El procedimiento para calcular los WIP explicado anteriormente es una aplicación directa de la **Ley de Little**, uno de los resultados más importantes de la Teoría de Colas ([enlace](https://isbnsearch.org/isbn/0471503363))
). La Ley de Little establece que el número de elementos en un sistema de colas es igual a la tasa de llegada de esos elementos multiplicada por el tiempo que cada elemento permanece en el sistema. Traducido a nuestro contexto, el sistema es un paso de un proceso Kanban y los elementos son tareas. Así, tenemos que:

- WIP: número de tareas en un determinado paso de un proceso Kanban.

- Throughput (TP): tasa de llegada de esas tareas a ese paso.

- Lead Time (LT): tiempo que cada tarea permanece en ese paso.

Es decir, de acuerdo con la Ley de Little: **WIP = TP × LT**. Visualmente, podemos representar la Ley de Little como se muestra en la próxima figura.

*Lei de Little: WIP = TP * LT*

## Preguntas frecuentes

Antes de concluir, responderemos algunas preguntas sobre Kanban:

**¿Cuáles son los roles que existen en Kanban?**

A diferencia de Scrum, Kanban no define una lista fija de roles. Corresponde al equipo y a la organización definir los roles que existirán en el proceso de desarrollo, tales como Propietario del Producto, Testers, etc.

**¿Cómo se priorizan las historias de usuario?**

Kanban es un método de desarrollo más ligero que Scrum e incluso que XP. Una de las razones es que no define criterios de priorización de historias. Como se respondió en la pregunta anterior, no se establece, por ejemplo, que el equipo deba tener un Propietario del Producto, responsable de esa priorización. Observe que esa es una posibilidad, es decir, puede existir un Propietario del Producto en equipos Kanban. Pero también son posibles otras soluciones, como una priorización externa, realizada por un gerente de producto.

**¿Los equipos Kanban pueden realizar eventos típicos de Scrum, como reuniones diarias, revisiones y retrospectivas?**

Sí, aunque Kanban no prescribe la realización de esos eventos. Sin embargo, tampoco existe una prohibición explícita al respecto. Corresponde al equipo decidir qué eventos son importantes, cuándo deben realizarse, cuál debe ser su duración, etc.

**En lugar de un Tablero Kanban físico, con adhesivos en una pared o en una pizarra blanca, ¿puede usarse un software de gestión de proyectos?**

Kanban no prohíbe el uso de software de gestión de proyectos. Sin embargo, se recomienda el uso de un tablero físico, pues uno de los principios más importantes de Kanban es la visualización del trabajo por parte del equipo, de modo que sus miembros puedan, en cualquier momento, tomar conocimiento del trabajo en curso y de los posibles problemas y cuellos de botella que estén ocurriendo. En algunos casos, incluso se recomienda adoptar ambas soluciones: un tablero físico, pero con un respaldo en un software de gestión de proyectos, que pueda ser accedido por los gerentes y ejecutivos de la organización.

[← Volver](index.md)
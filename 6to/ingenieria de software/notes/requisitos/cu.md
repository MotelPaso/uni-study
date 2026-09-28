# Casos de Uso

_Original: https://www.danielsanmartin.cl/blog/cu/_


Los casos de uso (use cases) son documentos textuales de especificación de requisitos. Como se verá en esta sección, incluyen descripciones más detalladas que las historias de usuario. Se recomienda que los casos de uso sean escritos durante la fase de Especificación de Requisitos, considerando que se sigue un proceso de desarrollo de tipo Waterfall. Son redactados por los propios desarrolladores del sistema, a veces llamados Ingenieros de Requisitos durante esta fase del desarrollo. Para ello, los desarrolladores pueden valerse, por ejemplo, de entrevistas con los usuarios del sistema. Aunque son escritos por los desarrolladores, los casos de uso pueden ser leídos, comprendidos y validados por los usuarios antes de que comiencen las fases de diseño e implementación.

Los casos de uso se escriben desde la perspectiva de un actor que desea utilizar el sistema con un objetivo. Típicamente, ese actor es un usuario humano, aunque también puede ser otro sistema de software o hardware. Es decir, normalmente, el actor es una entidad externa al sistema.

Explicándolo con más detalle, un caso de uso enumera los pasos que un actor realiza en un sistema con un determinado objetivo. En realidad, un caso de uso incluye dos listas de pasos. La primera representa el flujo normal de pasos necesarios para concluir una operación con éxito. Es decir, el flujo normal describe un escenario en el que todo sale bien, a veces llamado también flujo feliz. La segunda lista incluye extensiones del flujo normal, las cuales representan alternativas de ejecución de un paso normal o bien situaciones de error. Ambos flujos —el normal y las extensiones— serán posteriormente implementados en el sistema. A continuación, se muestra un caso de uso referido a un sistema bancario, que especifica una transferencia entre cuentas realizada por un cliente del banco.

| Elemento | Descripción |
| --- | --- |
| **Caso de uso** | Transferir valores entre cuentas |
| **Actor** | Cliente del banco |

| **Flujo normal** | **Descripción** |
| --- | --- |
| 1 | Autenticar al cliente |
| 2 | El cliente informa la sucursal y la cuenta de destino de la transferencia |
| 3 | El cliente informa el valor que desea transferir |
| 4 | El cliente informa la fecha en la que desea realizar la operación |
| 5 | El sistema efectúa la transferencia |
| 6 | El sistema pregunta si el cliente desea realizar una nueva transferencia |

| **Extensiones** | **Descripción** |
| --- | --- |
| 2a | Si la cuenta y la sucursal son incorrectas, solicitar una nueva cuenta y sucursal |
| 3a | Si el valor supera el saldo actual, solicitar un nuevo valor |
| 4a | La fecha informada debe ser la fecha actual o, como máximo, un año hacia adelante |
| 5a | Si la fecha informada es la fecha actual, transferir inmediatamente |
| 5b | Si la fecha informada es una fecha futura, programar la transferencia |

Ahora detallaremos algunos puntos pendientes sobre los casos de uso, utilizando el ejemplo anterior. En primer lugar, todo caso de uso debe tener un nombre, cuya primera palabra debe ser un verbo en infinitivo. A continuación, debe indicar el actor principal del caso de uso. Un caso de uso también puede incluir otro caso de uso. En nuestro ejemplo, el paso 1 del flujo normal incluye el caso de uso autenticar cliente. La sintaxis para tratar inclusiones es simple: se menciona el nombre del caso de uso que será incluido, el cual debe estar subrayado. La semántica también es clara: todos los pasos del caso de uso incluido deben ejecutarse antes de continuar. Es decir, la semántica es la misma que la de las macros en los lenguajes de programación.

Por último, están las extensiones, las cuales tienen dos objetivos:

- El primero es detallar algún paso del flujo normal. En nuestro ejemplo, usamos extensiones para especificar que la transferencia debe realizarse inmediatamente si la fecha informada es la fecha actual (extensión 5a). En caso contrario, se agenda la transferencia, que ocurrirá en la fecha futura informada (extensión 5b).

- El segundo objetivo es tratar errores, excepciones, cancelaciones, etc. En nuestro ejemplo, usamos una extensión para especificar que debe solicitarse un nuevo valor en caso de que no exista saldo suficiente para la transferencia (extensión 3a).

Debido a la existencia de flujos de extensión, se recomienda evitar comandos de decisión (si) en el flujo normal de los casos de uso. Cuando sea necesario decidir entre dos comportamientos normales, conviene definir esa situación como una extensión. Esta es una de las razones por las cuales los flujos de extensión, en casos de uso reales, suelen tener más pasos que el flujo normal. En nuestro ejemplo simple, casi ya tenemos un empate: seis pasos normales frente a cinco extensiones. Algunas veces, las descripciones de casos de uso incluyen secciones adicionales, tales como: (1) propósito del caso de uso; (2) precondiciones, es decir, lo que debe ser verdadero antes de ejecutar el caso de uso; (3) postcondiciones, es decir, lo que debe ser verdadero después de su ejecución; y (4) una lista de casos de uso relacionados.

Para concluir, se presentan algunas buenas prácticas para la redacción de casos de uso:

- Las acciones de un caso de uso deben escribirse en un lenguaje simple y directo. Una recomendación frecuente es escribir los casos de uso como si se estuviera al inicio de la educación primaria. Siempre que sea posible, debe usarse el actor principal como sujeto de las acciones, seguido de un verbo. Por ejemplo: el cliente inserta la tarjeta en el cajero automático. Sin embargo, si la acción es realizada por el sistema, debe escribirse algo como: el sistema valida la tarjeta insertada.

- Los casos de uso deben ser pequeños, con pocos pasos, especialmente en el flujo normal, para facilitar su comprensión. Alistair Cockburn, autor de un conocido libro sobre casos de uso, recomienda que tengan como máximo nueve pasos en el flujo normal. Afirma literalmente que rara vez encuentra un caso de uso bien escrito con más de nueve pasos en el escenario principal de éxito. Por lo tanto, si al redactar un caso de uso este comienza a extenderse demasiado, conviene intentar dividirlo en dos casos de uso más pequeños. Otra alternativa consiste en agrupar algunos pasos. Por ejemplo, los pasos el usuario informa el login y el usuario informa la contraseña pueden agruparse en el usuario informa el login y la contraseña.

- Los casos de uso no son algoritmos escritos en pseudocódigo. Su nivel de abstracción es mayor que el requerido en los algoritmos. Debe recordarse que los usuarios del sistema, cuyos requisitos están siendo documentados, deben ser capaces de leer, comprender y detectar problemas en los casos de uso. Por ello, conviene evitar comandos como si, repetir hasta, etc. Por ejemplo, en lugar de un comando de repetición, puede escribirse algo como: el cliente consulta el catálogo hasta encontrar el producto que desea comprar.

- Los casos de uso no deben tratar aspectos tecnológicos o de diseño. Además, no es necesario mencionar la interfaz que el actor principal utilizará para comunicarse con el sistema. Por ejemplo, no debe escribirse algo como: el cliente presiona el botón verde para confirmar la transferencia. Debe recordarse que se está en la fase de documentación de requisitos y que las decisiones sobre tecnología, diseño, arquitectura e interfaz con el usuario todavía no forman parte del foco principal. El objetivo debe ser documentar qué deberá hacer el sistema y no cómo implementará los requisitos especificados.

- Conviene evitar casos de uso demasiado simples, como aquellos que solo contienen operaciones CRUD (Crear, Recuperar, Actualizar y Eliminar). Por ejemplo, en un sistema académico no tiene mucho sentido tener casos de uso como Registrar Profesor, Recuperar Profesor, Actualizar Profesor y Eliminar Profesor. A lo sumo, puede crearse un caso de uso Gestionar Profesor y explicar brevemente que incluye esas cuatro operaciones. Como la semántica de estas acciones es clara, eso puede hacerse en una o dos oraciones. Aprovechando esto, también es importante mencionar que el flujo normal de un caso de uso no necesariamente debe ser una enumeración de acciones. En algunas situaciones, como la que se acaba de mencionar, resulta más práctico utilizar un texto libre.

- Finalmente, conviene estandarizar el vocabulario adoptado en los casos de uso. Por ejemplo, debe evitarse usar el nombre Cliente en un caso de uso y Usuario en otro. En el libro The Pragmatic Programmer ([enlace](https://dl.acm.org/doi/book/10.5555/320326)), David Thomas y Andrew Hunt recomiendan la creación de un **glosario**, es decir, un documento que enumere los términos y el vocabulario utilizados en un proyecto. Según los autores, es muy difícil tener éxito en un proyecto en el que usuarios y desarrolladores se refieren a las mismas cosas con nombres distintos y, peor aún, se refieren a cosas diferentes con el mismo nombre.

### Diagramas de Casos de Uso

Vamos a adelantar y comentar uno de los diagramas de UML, llamado Diagrama de Casos de Uso. Este diagrama es un índice gráfico de casos de uso. Representa a los actores de un sistema (como pequeños muñecos) y a los casos de uso (como elipses). También se muestran dos tipos de relaciones: (1) las que conectan a un actor con un caso de uso, indicando que un actor participa en un determinado caso de uso; y (2) las que conectan dos casos de uso, indicando que un caso de uso incluye o extiende a otro caso de uso.

Un ejemplo simple de diagrama de casos de uso para un sistema bancario muestra dos actores: Cliente y Gerente. El Cliente participa en los siguientes casos de uso: Retirar Dinero y Transferir Valores. El Gerente, por su parte, es el actor principal del caso de uso Abrir Cuenta. El diagrama también deja explícito que Transferir Valores incluye el caso de uso Autenticar Cliente. Finalmente, obsérvese que los casos de uso se representan dentro de un rectángulo, que delimita las fronteras del sistema. Los dos actores se representan fuera de esa frontera.

*Ejemplo de Diagrama UML de Casos de Uso*

**Profundización:** Aquí se hace una distinción entre casos de uso —documentos textuales para especificar requisitos— y diagramas de casos de uso —índices gráficos de los casos de uso, tal como se proponen en UML—. Esta misma decisión es adoptada, por ejemplo, por Craig Larman en su libro sobre UML y patrones de diseño ([enlace](https://dl.acm.org/doi/book/10.5555/1044919)). Él afirma que los casos de uso son documentos textuales y no diagramas. Por lo tanto, el modelado de casos de uso es esencialmente una actividad de redacción y no de dibujo de diagramas. Del mismo modo, Martin Fowler llega a afirmar que los diagramas UML de casos de uso tienen poco valor: la importancia de los casos de uso está en el texto, que no está estandarizado en UML. Por ello, al trabajar con casos de uso, conviene concentrar el esfuerzo en el texto. Por otro lado, algunos autores, para evitar cualquier confusión, prefieren usar el término escenarios de uso en lugar de casos de uso.

### Preguntas frecuentes

A continuación, se responden dos preguntas sobre los casos de uso.

**¿Cuál es la diferencia entre los casos de uso y las historias de usuario?**

La respuesta simple es que los casos de uso son especificaciones de requisitos más detalladas y completas que las historias. Una respuesta más elaborada fue formulada por Mike Cohn en su libro sobre historias. Según él, los casos de uso se escriben en un formato aceptado tanto por los clientes como por los desarrolladores, de modo que ambos puedan leer y estar de acuerdo con lo que está escrito. Por lo tanto, el objetivo es documentar un acuerdo entre los clientes y el equipo de desarrollo. Las historias, en cambio, se escriben para facilitar la planificación de iteraciones y para servir como un recordatorio de las conversaciones sobre los detalles de las necesidades de los clientes.

**¿Cuál es el origen de la técnica de casos de uso?**

Los casos de uso fueron propuestos a fines de la década de 1980 por Ivar Jacobson, uno de los padres de UML y también del Proceso Unificado (UP). En particular, los casos de uso fueron concebidos para ser uno de los principales productos de la fase de Elaboración del UP. Como se indicó anteriormente, el UP enfatiza la comunicación escrita entre usuarios y desarrolladores, utilizando documentos como los casos de uso.

[← Volver](index.md)
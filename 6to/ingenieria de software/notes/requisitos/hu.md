# Historias de Usuario

_Original: https://www.danielsanmartin.cl/blog/hu/_


Los documentos de requisitos tradicionales, como aquellos producidos cuando se utiliza Waterfall, tienen cientos de páginas y a veces tardan más de un año en estar listos. Además, presentan los siguientes problemas: (1) durante el desarrollo, los requisitos cambian y los documentos se vuelven obsoletos; (2) las descripciones en lenguaje natural son ambiguas e incompletas; por ello, los desarrolladores tienen que volver a conversar con los clientes durante el desarrollo para aclarar dudas; (3) cuando esas conversaciones intermedias no ocurren, los riesgos son aún mayores: al final de la codificación, el cliente puede simplemente concluir que ese ya no es el sistema que quería, porque sus prioridades cambiaron, su visión del negocio cambió, los procesos internos de su empresa cambiaron, etc. Por eso, una larga fase inicial de especificación de requisitos es cada vez más rara, al menos en sistemas comerciales, como los que se tratan en este libro.

Los profesionales de la industria que propusieron los métodos ágiles percibieron —o sufrieron— tales problemas y propusieron una técnica pragmática para resolverlos, que llegó a conocerse con el nombre de Historias de Usuario. Como sugirió Ron Jeffries en un libro sobre desarrollo ágil, una historia de usuario está compuesta por tres partes, todas comenzando con la letra C, y que podemos representar mediante la siguiente ecuación:

```plaintext
Historia de Usuario = Tarjeta (Card) + Conversaciones + Confirmación
```

A continuación, se explora cada una de estas partes de una historia:

- **Tarjeta**, utilizada por los clientes para escribir, en su propio lenguaje y en pocas oraciones, una funcionalidad que esperan ver implementada en el sistema.

- **Conversaciones** entre clientes y desarrolladores, mediante las cuales los clientes explican y detallan lo que escribieron en cada tarjeta. Como ya se mencionó, la visión de los métodos ágiles sobre la Ingeniería de Requisitos es pragmática: como las especificaciones textuales y completas de requisitos no funcionan, fueron eliminadas y sustituidas por comunicación verbal entre desarrolladores y clientes. Por ello, los métodos ágiles incluyen en los equipos de desarrollo a un representante de los clientes, que participa en el equipo a tiempo completo.

- **Confirmación**, que es básicamente una prueba de alto nivel —nuevamente especificada por el cliente— para verificar si la historia fue implementada conforme a lo esperado. Por lo tanto, no se trata de una prueba automatizada, como una prueba unitaria, por ejemplo. Más bien, corresponde a la descripción de los escenarios, ejemplos y casos de prueba que el cliente utilizará para confirmar la implementación de la historia. Por eso, también se les llama **pruebas de aceptación** de historias. Deben escribirse lo antes posible, preferentemente al inicio de una iteración. Algunos autores recomiendan escribirlas en el reverso de las tarjetas de la historia.

Por lo tanto, las especificaciones de requisitos mediante historias no consisten solo en dos o tres oraciones, como algunos críticos de los métodos ágiles podrían afirmar. La forma correcta de interpretar una historia de usuario es la siguiente: la historia que se escribe en la tarjeta es un recordatorio del representante de los clientes para los desarrolladores. Mediante ella, el representante de los clientes declara que le gustaría ver implementado un determinado requisito funcional en la próxima iteración (o sprint). Más aún, durante todo el sprint se compromete a estar disponible para refinar la historia y explicarla a los desarrolladores. Por último, también se compromete a considerar la historia como implementada siempre que satisfaga las pruebas de confirmación que él mismo especificó.

Desde la perspectiva de los desarrolladores, el proceso funciona así: el representante de los clientes nos está solicitando la historia resumida en esa tarjeta. Por lo tanto, nuestra obligación en el próximo sprint es implementarla. Para ello, podremos contar con todo su apoyo para conversar y aclarar dudas. Además, ya definió las pruebas que utilizará en la reunión de revisión del sprint (sprint review) para considerar la historia como implementada. También se acuerda que no podrá cambiar de idea y, al final del sprint, usar una prueba completamente distinta para evaluar nuestra implementación.

En resumen, cuando se utilizan historias de usuario, las actividades de Ingeniería de Requisitos ocurren a lo largo de todo el desarrollo, prácticamente todos los días de una iteración. En consecuencia, se reemplaza un documento de requisitos de cientos de páginas por conversaciones frecuentes, en las que el representante de los clientes explica los requisitos a los desarrolladores del equipo. Continuando con la comparación, las historias de usuario favorecen la comunicación verbal en lugar de la comunicación escrita. Y por eso también son compatibles con los principios del Manifiesto Ágil: (1) individuos e interacciones, más que procesos y herramientas; (2) software funcionando, más que documentación exhaustiva; (3) colaboración con el cliente, más que negociación de contratos; (4) respuesta al cambio, más que seguir un plan.

Las buenas historias deben poseer las siguientes características, cuyas iniciales en inglés originan el acrónimo INVEST:

- Las historias deben ser independientes: dadas dos historias X e Y, debe ser posible implementarlas en cualquier orden. Para ello, idealmente no deben existir dependencias entre ellas.

- Las historias deben estar abiertas a negociación. Frecuentemente se dice que las historias (la tarjeta) son invitaciones a conversaciones entre clientes y desarrolladores durante un sprint. Por lo tanto, ambos deben estar abiertos a ceder en sus opiniones durante esas conversaciones. Los desarrolladores deben estar dispuestos a implementar detalles que no están expresados o que no caben en las tarjetas de la historia. Y los clientes deben aceptar argumentos técnicos de los desarrolladores, por ejemplo, sobre la inviabilidad de implementar algún detalle de la historia tal como fue imaginado inicialmente.

- Las historias deben agregar valor al negocio de los clientes. Las historias son propuestas, escritas y priorizadas por los clientes según el valor que agregan a su negocio. Por eso, no existe la figura de una historia técnica, como la siguiente: el sistema debe implementarse en JavaScript, usando React en el front-end y Node.js en el backend.

- Debe ser viable estimar el tamaño de una historia. Por ejemplo, cuántos días serán necesarios para implementarla. Normalmente, esto requiere que la historia sea pequeña, como se verá en el siguiente punto, y que los desarrolladores tengan experiencia en el dominio del sistema.

- Las historias deben ser sucintas y pequeñas. De hecho, incluso se admiten historias complejas y grandes, las cuales se llaman épicos. Sin embargo, estas se ubican al fondo del backlog, lo que significa que todavía no se tiene una previsión de cuándo serán implementadas. Por el contrario, las historias que están en la parte superior del backlog y que, por lo tanto, serán implementadas pronto, deben ser cortas y pequeñas, para facilitar su comprensión y estimación. Suponiendo que un sprint tenga una duración máxima de un mes, debe ser posible implementar las historias de la parte superior del backlog en menos de una semana.

- Las historias deben ser testeables, es decir, deben tener criterios de aceptación objetivos. Como ejemplo, puede citarse: el cliente puede pagar con tarjetas de crédito. Una vez definidas las marcas de tarjetas de crédito que serán aceptadas, esta historia es testeable. En cambio, la siguiente historia es un contraejemplo: un cliente no debe esperar mucho para que se confirme su compra. Esta es una historia vaga y, por lo tanto, con un criterio de aceptación también vago.

Antes de comenzar a escribir historias, se recomienda listar los principales usuarios que interactuarán con el sistema. Así, se evita que las historias queden sesgadas y respondan solo a las necesidades de ciertos usuarios. Una vez definidos esos roles de usuario (user roles), suele escribirse las historias con el siguiente formato:

```plaintext
Como un [rol de usuario], me gustaría [realizar algo con el sistema]
```

A continuación se muestran ejemplos de historias con este formato. Antes, conviene comentar que, justo al inicio del desarrollo de un sistema, suele realizarse un **taller de escritura de historias**. Este taller reúne en una sala a representantes de los principales usuarios del sistema, quienes discuten los objetivos del sistema, sus principales funcionalidades, etc. Al final del taller, que dependiendo del tamaño del sistema puede durar una semana, se debe contar con una buena lista de historias de usuario que demanden varios sprints para ser implementadas.

### Ejemplo: Sistema de Control de Bibliotecas

En esta sección se mostrarán ejemplos de historias para un sistema de control de bibliotecas. Estas están asociadas a tres tipos de usuarios: usuario típico, profesor y funcionario de la biblioteca.

Primero se muestran historias propuestas por usuarios típicos. Cualquier usuario de la biblioteca encaja en este rol y, por lo tanto, puede realizar las operaciones mencionadas en estas historias. Obsérvese que las historias son resumidas y no detallan cómo se implementará cada operación. Por ejemplo, una historia documenta que el sistema debe permitir búsquedas de libros. Sin embargo, existen diversos detalles que la historia omite, entre ellos los campos de búsqueda, los filtros que podrán utilizarse, el número máximo de resultados devueltos en cada búsqueda, el diseño de las pantallas de búsqueda y de resultados, etc. Pero debe recordarse que una historia es una promesa: el representante de los clientes promete disponer de tiempo para definir y explicar tales detalles en conversaciones con los desarrolladores, durante el sprint en el cual la historia será implementada. Como ya se comentó, cuando se utilizan historias, esta comunicación verbal entre desarrolladores y representante de los clientes es la principal actividad de Ingeniería de Requisitos.

```plaintext
Como usuario típico, me gustaría realizar préstamos de libros

Como usuario típico, me gustaría devolver un libro que tomé prestado

Como usuario típico, me gustaría renovar préstamos de libros

Como usuario típico, me gustaría buscar libros

Como usuario típico, me gustaría reservar libros que están prestados

Como usuario típico, me gustaría recibir correos electrónicos con nuevas adquisiciones
```

A continuación, se muestran las historias propuestas por profesores:

```plaintext
Como profesor, me gustaría realizar préstamos de mayor duración

Como profesor, me gustaría sugerir la compra de libros

Como profesor, me gustaría donar libros a la biblioteca

Como profesor, me gustaría devolver libros en otras bibliotecas
```

Es importante mencionar que, efectivamente, fueron los profesores quienes recordaron solicitar las historias anteriores. Pueden haberlo hecho, por ejemplo, en un taller de escritura de historias. Pero eso no significa que solo los profesores podrán hacer uso de estas historias. Por ejemplo, al detallar las historias en un sprint, el representante de los clientes (product owner) puede considerar interesante permitir que cualquier usuario realice donaciones de libros y no solo los profesores. Finalmente, la última historia sugerida por los profesores —permitir devoluciones en otras bibliotecas de la universidad— puede considerarse como un **épico**, es decir, una historia más compleja. Como la universidad posee más de una biblioteca, el profesor podría querer realizar un préstamo en la Biblioteca Central y devolver el libro en la biblioteca de su departamento, por ejemplo. Sin embargo, esta funcionalidad requiere la integración de los sistemas de ambas bibliotecas y también personal disponible para transportar el libro a su biblioteca original.

Por último, se muestran las historias propuestas por los funcionarios de la biblioteca durante el taller de escritura de historias. Obsérvese que, en general, son historias relacionadas con la organización de la biblioteca y con garantizar su buen funcionamiento.

```plaintext
Como funcionario de la biblioteca, me gustaría registrar nuevos usuarios

Como funcionario de la biblioteca, me gustaría registrar nuevos libros

Como funcionario de la biblioteca, me gustaría dar de baja libros dañados

Como funcionario de la biblioteca, me gustaría obtener estadísticas sobre el acervo

Como funcionario de la biblioteca, me gustaría que el sistema envíe correos electrónicos de cobro a estudiantes con préstamos atrasados

Como funcionario de la biblioteca, me gustaría que el sistema aplique multas al devolver préstamos atrasados
```

Antes de concluir, se mostrará una prueba de aceptación para la historia buscar libros. Para confirmar la implementación de esta historia, el representante de los clientes definió que le gustaría ver realizadas con éxito las siguientes búsquedas. Estas serán demostradas y probadas durante la reunión de entrega de historias, llamada Revisión del Sprint en Scrum.

```plaintext
Buscar libros informando ISBN

Buscar libros informando autor; devuelve libros cuyo autor contiene la cadena de búsqueda

Buscar libros informando título; devuelve libros cuyo título contiene la cadena de búsqueda

Buscar libros registrados en la biblioteca desde una fecha hasta la fecha actual
```

**Profundización:** Las pruebas de aceptación deben ser especificadas por el representante de los clientes. Con ello se busca evitar lo que se denomina **gold plating**. En Ingeniería de Requisitos, esta expresión designa la situación en la que los desarrolladores deciden, por cuenta propia, sofisticar la implementación de algunas historias —o requisitos, de manera más general—, sin que ello haya sido solicitado por los clientes. En una traducción literal, los desarrolladores están cubriendo las historias con capas de oro, aunque eso no generará valor para los usuarios del sistema.

### Preguntas Frecuentes

Antes de finalizar, y como es habitual en este blog, se responderán algunas preguntas sobre historias de usuario:

**¿Cómo especificar requisitos no funcionales usando historias?**

Esta es una cuestión más desafiante cuando se utilizan métodos ágiles. De hecho, el representante de los clientes (o dueño del producto) puede escribir una historia diciendo que el tiempo máximo de respuesta del sistema debe ser de 1 segundo. Sin embargo, no tiene sentido asignar esta historia a una iteración, porque debe ser una preocupación presente durante todas las iteraciones del proyecto. Por ello, la mejor solución es pedir al dueño del producto que escriba historias sobre requisitos no funcionales, pero usarlas principalmente para reforzar los criterios de finalización de las historias (done criteria). Por ejemplo, para considerar que una historia está terminada, deberá pasar por una revisión de código cuyo objetivo sea detectar problemas de rendimiento. Antes de poner en producción cualquier release del sistema, también puede realizarse una prueba de rendimiento, para garantizar que el requisito no funcional especificado en la historia esté siendo cumplido. En resumen, se puede —y se debe— escribir historias sobre requisitos no funcionales, pero estas no van al backlog del producto. En cambio, se utilizan para refinar los criterios de finalización de las historias.

**¿Es posible crear historias para estudiar una nueva tecnología?**

Conceptualmente, la respuesta es que no deben crearse historias exclusivamente para adquirir conocimiento, pues las historias siempre deben ser escritas y priorizadas por los clientes. Y deben tener valor para el negocio. Por lo tanto, no vale la pena violar este principio y permitir que los desarrolladores creen una historia como “estudiar el uso del framework X en la implementación de la interfaz web”. En cambio, ese estudio puede ser una tarea necesaria para implementar una determinada historia. Las tareas destinadas a la adquisición de conocimiento se llaman **spikes**.

[← Volver](index.md)
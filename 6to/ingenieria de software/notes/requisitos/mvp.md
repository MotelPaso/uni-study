# Producto Mínimo Viable

_Original: https://www.danielsanmartin.cl/blog/mvp/_


El concepto de MVP fue popularizado en el libro **Lean Startup**, de Eric Ries ([enlace](https://isbnsearch.org/isbn/0307887898)). A su vez, el concepto de Lean Startup está inspirado en los principios de la Manufactura Lean, desarrollados por fabricantes japoneses de automóviles, como Toyota, desde comienzos de la década de 1950. Ya se ha comentado sobre la Manufactura Lean, pues el proceso de desarrollo Kanban también fue adaptado a partir de principios de gestión de la producción originados en lo que más tarde se conoció como Manufactura Lean. Uno de los principios de la Manufactura Lean recomienda eliminar desperdicios en una línea de ensamblaje o cadena de suministro. En el caso de una empresa de desarrollo de software, el mayor desperdicio que puede existir es pasar años levantando requisitos e implementando un sistema que después no será utilizado, porque resuelve un problema que ya no interesa a sus usuarios. Por lo tanto, si un sistema va a fracasar —por no tener éxito, usuarios o mercado—, es mejor que fracase rápidamente, pues así el desperdicio de recursos será menor.

Los sistemas de software que no despiertan interés pueden ser producidos por cualquier empresa. Sin embargo, son más comunes en las startups, ya que, por definición, estas son empresas que operan en entornos de gran incertidumbre. No obstante, Eric Ries también recuerda que la definición de startup no se limita a una empresa formada por dos universitarios que desarrollan en un garaje un nuevo producto de éxito instantáneo. Según él, cualquier persona que esté creando un nuevo producto o negocio bajo condiciones de extrema incertidumbre es un emprendedor, lo sepa o no, y trabaje en una entidad gubernamental, en una empresa apoyada por capital de riesgo, en una organización sin fines de lucro o en una empresa con inversionistas financieros claramente orientada al lucro.

Entonces, para dejar claro el escenario, supóngase que se pretende crear un sistema nuevo, pero no se tiene certeza de que tendrá usuarios y será exitoso. Como se comentó antes, no vale la pena pasar uno o dos años levantando los requisitos de ese sistema para luego concluir que será un fracaso. Por otro lado, tampoco tiene mucho sentido realizar estudios de mercado para medir la receptividad del sistema antes de implementarlo. Como se trata de un sistema nuevo, con requisitos diferentes de los de cualquier sistema existente, los resultados de una investigación de mercado pueden no ser confiables.

Una solución consiste en implementar un sistema simple, con un conjunto mínimo de requisitos, pero suficientes para probar la viabilidad de seguir invirtiendo en su desarrollo. En Lean Startup, este primer sistema se denomina **Producto Mínimo Viable** (MVP). También suele decirse que el objetivo de un MVP es poner a prueba una hipótesis de negocio.

Lean Startup propone un método sistemático y científico para construir y validar MVPs. Este método consiste en un ciclo de tres pasos: **construir, medir y aprender**. En el primer paso (construir), se tiene una idea de producto y luego se implementa un MVP para ponerla a prueba. En el segundo paso (medir), el MVP se pone a disposición de clientes reales con el fin de recopilar datos sobre su viabilidad. En el tercer paso (aprender), las métricas recolectadas se analizan y generan lo que se denomina **aprendizaje validado** (validated learning).

*Método Lean Startup para validación de MVPs*

El aprendizaje obtenido con un MVP puede dar lugar a tres decisiones:

Se puede concluir que todavía son necesarias más pruebas con el MVP, posiblemente modificando su conjunto de requisitos, su interfaz con los usuarios o el mercado objetivo. En ese caso, se repite el ciclo y se vuelve al paso de construir.

Se puede concluir que la prueba fue exitosa y, por lo tanto, que se encontró un mercado para el sistema (market fit). En este caso, es momento de invertir más recursos para implementar un sistema con un conjunto más robusto y completo de funcionalidades.

Por último, se puede concluir que el MVP fracasó, después de varios intentos. Entonces, quedan dos alternativas: (1) perecer, es decir, desistir del emprendimiento, especialmente si ya no existen recursos financieros para mantenerlo vivo; o (2) hacer un pivote, es decir, abandonar la visión original e intentar un nuevo MVP, con nuevos requisitos y para un nuevo mercado, sin olvidar lo aprendido con el MVP anterior.

Al tomar estas decisiones, un riesgo es utilizar únicamente **métricas de vanidad** (vanity metrics). Estas son métricas superficiales que hacen sentir bien al ego de los desarrolladores y gerentes de producto, pero que no ayudan a comprender ni a mejorar una estrategia de mercado. El ejemplo clásico es el número de pageviews en un sitio de comercio electrónico. Puede resultar muy atractivo decir que el sitio atrae millones de clientes por mes, pero eso por sí solo no ayudará a pagar las cuentas del emprendimiento.

Por otro lado, las métricas que ayudan a tomar decisiones sobre el futuro de un MVP se denominan **métricas accionables**(actionable metrics). En el caso de un sistema de comercio electrónico, estas métricas incluirían el porcentaje de visitantes que concretan compras, el valor de cada orden de compra, el número de ítems comprados, el costo de adquisición de nuevos clientes, entre otras. Al monitorear estas métricas, podría concluirse, por ejemplo, que la mayoría de los clientes compra solo un ítem al cerrar una compra. Como resultado concreto —o accionable—, podría decidirse incorporar un sistema de recomendación al sitio o investigar el uso de un sistema de recomendación más eficiente. Tales sistemas, dada una compra en curso, son capaces de sugerir nuevos productos para ser adquiridos. De este modo, tienen el potencial de aumentar el número de ítems comprados en una misma transacción.

Para evaluar MVPs que incluyen ventas de productos o servicios, suele utilizarse métricas de embudo (funnel metrics), que capturan el nivel de interacción de los usuarios con un sistema. Un embudo puede incluir las siguientes métricas:

- Adquisición: número de clientes que visitaron el sistema.

- Activación: número de clientes que crearon una cuenta en el sistema.

- Retención: clientes que regresaron al sistema después de haber creado una cuenta.

- Ingresos: número de clientes que realizaron una compra.

- Recomendación: clientes que recomendaron el sistema a terceros.

### Ejemplos de MVP

Un MVP no necesita ser un software real, implementado en un lenguaje de programación, con bases de datos, integración con otros sistemas, etc. Dos ejemplos de MVP que no son sistemas suelen mencionarse con frecuencia en artículos sobre Lean Startup.

El primero es el caso de Zappos, una de las primeras empresas que intentó vender zapatos por Internet en Estados Unidos. En 1999, para probar de manera pionera la viabilidad de una tienda virtual de zapatos, el fundador de la empresa concibió un MVP simple y original. Visitó algunas zapaterías de su ciudad, fotografió diversos pares de zapatos y creó una página web muy simple mediante la cual los clientes podían seleccionar los zapatos que deseaban comprar. Sin embargo, todo el procesamiento se hacía manualmente, incluida la comunicación con la empresa de tarjetas de crédito, la compra de los zapatos en las tiendas de la ciudad y el envío a los clientes. No existía ningún sistema para automatizar esas tareas. Aun así, con ese MVP basado en tareas manuales, el dueño de Zappos logró validar de forma rápida y barata su hipótesis inicial, es decir, que existía mercado para la venta de zapatos por Internet. Años más tarde, Zappos fue adquirida por Amazon por más de mil millones de dólares.

Un segundo ejemplo de MVP que no implicó poner a disposición de los usuarios un software real proviene de Dropbox, el sistema de almacenamiento y compartición de archivos en la nube. Para recibir retroalimentación sobre el producto que estaban desarrollando, uno de los fundadores de la empresa grabó un video simple, casi amateur, demostrando en tres minutos las principales funcionalidades y ventajas del sistema. El video se viralizó y contribuyó a aumentar la lista de usuarios interesados en probar el sistema, que pasó de 5 mil a 75 mil usuarios. Otro hecho interesante es que los archivos usados en el video tenían nombres divertidos y hacían referencia a personajes de historietas. El objetivo era llamar la atención de los adoptantes tempranos (early adopters), es decir, aquellas personas aficionadas a las nuevas tecnologías y dispuestas a ser las primeras en probar y comprar nuevos productos. La hipótesis que se quería validar con ese MVP en forma de video era que había usuarios interesados en instalar un sistema de sincronización y respaldo de archivos. Esa hipótesis resultó verdadera, dado el gran número de adoptantes tempranos dispuestos a realizar una prueba beta de Dropbox.

Sin embargo, los MVP también pueden implementarse en forma de sistemas de software reales, aunque mínimos. Por ejemplo, a comienzos de 2018, un grupo de investigación de la Universidade Federal de Minas Gerais (UFMG) ([enalace](https://www.ufmg.br/)) inició el proyecto de un sistema para catalogar la producción científica brasileña en Ciencia de la Computación. La primera decisión fue construir un MVP que cubriera solo artículos de cerca de 15 conferencias del área de Ingeniería de Software. En esa primera versión, el código implementado en Python tenía menos de 200 líneas. Los gráficos mostrados por el sistema, por ejemplo, eran planillas de Google Spreadsheets embebidas en páginas HTML. Ese sistema —inicialmente llamado CoreBR— fue divulgado y promovido en una lista de correos electrónicos en la que participan los profesores brasileños de Ingeniería de Software. Como el sistema despertó un buen interés, medido a través de métricas como la duración de las sesiones de uso, se decidió invertir más tiempo en su construcción. Primero, su nombre fue cambiado a CSIndexbr. Después, se amplió gradualmente la cobertura a más de 20 áreas de investigación en Ciencia de la Computación y casi doscientas conferencias. También se pasó a cubrir artículos publicados en más de 170 revistas. El número de profesores con artículos indexados aumentó de menos de 100 a más de 900. La interfaz de usuario dejó de ser un conjunto de planillas y pasó a ser un conjunto de gráficos implementados en JavaScript.

### Preguntas frecuentes

Para finalizar, se responden algunas preguntas sobre los MVP.

**¿Solo las startups deben usar MVP?**

Definitivamente no. Como se intentó discutir en esta sección, los MVP son un mecanismo para lidiar con la incertidumbre. Es decir, se utilizan cuando no se sabe si a los usuarios les gustará y usarán un determinado producto. En el contexto de la Ingeniería de Software, ese producto es un software. Claro que las startups, por definición, son empresas que trabajan en mercados de extrema incertidumbre. Sin embargo, la incertidumbre y los riesgos también pueden caracterizar al software desarrollado por diversos tipos de organizaciones, privadas o públicas; pequeñas, medianas o grandes; y de los más diversos sectores.

**¿Cuándo no vale la pena usar MVP?**

En cierto modo, esta pregunta ya fue respondida en la anterior. Cuando el mercado de un producto de software es estable y conocido, no hay necesidad de validar hipótesis de negocio y, por lo tanto, de construir MVP. En sistemas de misión crítica, tampoco se considera la construcción de MVP. Por ejemplo, está fuera de discusión construir un MVP para un software de monitoreo de pacientes en unidades de cuidados intensivos.

**¿Cuál es la diferencia entre MVP y prototipado?**

El prototipado es una técnica conocida en Ingeniería de Software para la elicitación y validación de requisitos. La diferencia entre prototipos y MVP está en las tres letras de la sigla, es decir, tanto en la M, como en la V y en la P. En primer lugar, los prototipos no son necesariamente sistemas mínimos. Por ejemplo, pueden incluir toda la interfaz de un sistema, con miles de funcionalidades. En segundo lugar, los prototipos no se implementan necesariamente para probar la viabilidad de un sistema con sus usuarios finales. Por ejemplo, pueden construirse para demostrar el sistema únicamente a los ejecutivos de una empresa contratante. Por esa misma razón, tampoco son productos.

**¿Un MVP es un producto de baja calidad?**

Esta pregunta es más compleja de responder. Sin embargo, es cierto que un MVP debe tener solo la calidad mínima necesaria para evaluar un conjunto de hipótesis de negocio. Por ejemplo, el código de un MVP no necesita ser fácil de mantener ni utilizar los más modernos patrones de diseño y frameworks de desarrollo, ya que puede ocurrir que el producto se muestre inviable y sea descartado. De hecho, en un MVP, cualquier nivel de calidad por encima de lo necesario para iniciar el ciclo construir-medir-aprender se considera desperdicio. Por otro lado, es importante que la calidad de un MVP no sea tan deficiente como para impactar negativamente la experiencia del usuario. Por ejemplo, un MVP alojado en un servidor web con problemas de disponibilidad puede dar lugar a resultados denominados falsos negativos. Estos ocurren cuando la hipótesis de negocio es falsamente invalidada. En este caso, el motivo del fracaso no estaría en el MVP, sino en el hecho de que los usuarios no lograron acceder al sistema, porque el servidor estaba fuera de servicio con frecuencia.

### Construcción del primer MVP

Lean Startup no define cómo construir el primer MVP de un sistema. En algunos casos esto no representa un problema, porque los proponentes del MVP tienen una idea precisa de sus funcionalidades y requisitos. Entonces, ya pueden implementar el primer MVP e iniciar así el ciclo construir-medir-aprender. Por otro lado, en ciertos casos, ni siquiera la idea del sistema está clara. En esas situaciones, se recomienda construir un prototipo antes de implementar el primer MVP.

Design Sprint es un método propuesto por Jake Knapp, John Zeratsky y Braden Kowitz ([enlace](https://isbnsearch.org/isbn/8551001523)) para probar y validar nuevos productos mediante prototipos, no necesariamente de software. Las principales características de un design sprint —que no debe confundirse con un sprint de Scrum— son las siguientes:

- Time-box. Un design sprint dura cinco días, comenzando el lunes y terminando el viernes. El objetivo es descubrir rápidamente una primera solución para un problema.

- Equipos pequeños y multidisciplinarios. Un design sprint debe reunir a un equipo multidisciplinario de siete personas. Al definir ese tamaño, se busca fomentar las discusiones; por eso, el equipo no puede ser demasiado pequeño. Pero también se procura evitar debates interminables; por eso, el equipo tampoco puede ser demasiado grande. En el equipo deben participar representantes de todas las áreas involucradas con el sistema que se pretende prototipar, incluidas personas de marketing, ventas, logística, etc. Por último, pero no menos importante, el equipo debe incluir a una persona responsable de tomar decisiones, que puede ser, por ejemplo, el propio dueño de la empresa.

- Objetivos y reglas claras. Los tres primeros días del design sprint tienen como objetivo converger, luego divergir y, finalmente, converger nuevamente. Es decir, en el primer día se comprende y delimita el problema que se pretende resolver. El objetivo es garantizar que, en los días siguientes, el equipo estará enfocado en resolver el mismo problema (convergencia). En el segundo día, se proponen posibles alternativas de solución de forma libre (divergencia). En el tercer día, se elige una solución ganadora entre las posibles alternativas (convergencia). En esa elección, la última palabra la tiene quien toma las decisiones; es decir, un design sprint no es un proceso puramente democrático. En el cuarto día, se implementa un prototipo, que puede ser simplemente un conjunto de páginas HTML estáticas, sin ningún código o funcionalidad. En el último día, se prueba el prototipo con cinco clientes reales, cada uno utilizando el sistema en sesiones individuales.

Antes de concluir, es importante mencionar que el design sprint no está orientado únicamente a la definición de un prototipo de MVP. La técnica puede utilizarse para proponer una solución a cualquier problema. Por ejemplo, se puede organizar un design sprint para rediseñar la interfaz de un sistema que ya está en producción, pero que presenta una alta tasa de abandono.

[← Volver](index.md)
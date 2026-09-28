# Modelo Vista Controlador (MVC)

_Original: https://www.danielsanmartin.cl/blog/mvc-ing/_


El patrón arquitectural MVC (Modelo-Vista-Controlador) fue propuesto a finales de la década de los 70 y, posteriormente, utilizado en la implementación de Smalltalk-80, que es considerada una de las primeras lenguajes orientadas a objetos. Además de usar conceptos de orientación a objetos, los programas en Smalltalk fueron pioneros en el uso de interfaces gráficas, con ventanas, botones, barras de desplazamiento, mouse, etc. Esto en una época en la que los sistemas operativos solo ofrecían interfaces de línea de comandos y los programas tenían una interfaz textual, es decir, las pantallas eran una matriz de caracteres, con, por ejemplo, 25 líneas y 80 columnas.

MVC fue el patrón arquitectural elegido por los diseñadores de Smalltalk para la implementación de interfaces gráficas. Específicamente, MVC define que las clases de un sistema deben organizarse en tres grupos:

- Vista: clases responsables de la presentación de la interfaz gráfica del sistema, incluidas ventanas, botones, menús, barras de desplazamiento, etc.

- Controladores: clases que gestionan e interpretan eventos generados por dispositivos de entrada, como el mouse y el teclado. Como resultado de estos eventos, los Controladores pueden solicitar un cambio en el estado del Modelo o de la Vista. Supongamos, por ejemplo, una calculadora. Cuando el usuario hace clic en el botón +, una clase Controladora debe capturar ese evento y llamar a un método del Modelo. Como segundo ejemplo, cuando el usuario hace clic en el botón “Interfaz Oscura”, también corresponde a una clase Controladora solicitar a la Vista que cambie los colores de la interfaz gráfica a tonos más oscuros.

- Modelo: clases que almacenan los datos manipulados por la aplicación y que están relacionados con el dominio del sistema en construcción. Así, las clases de Modelo no tienen ningún conocimiento ni dependencia con las clases de Vista y Controladores. Además de datos, las clases de Modelo pueden contener métodos que alteran el estado de los objetos de dominio.

Pregunta Frecuente: ¿Cuál es la diferencia entre MVC y tres capas? La respuesta será un poco extensa y nos basaremos en la evolución histórica de estas arquitecturas:

Como comentamos, MVC surgió a finales de la década de los 70, para ayudar en la construcción de interfaces gráficas. Es decir, aplicaciones que incluyen una interfaz con ventanas, botones, cuadros de texto, etc. Como ejemplo, podemos mencionar un paquete de oficina con aplicaciones como Word, Excel y PowerPoint, en el caso del sistema operativo Windows.

En la década de los 90, las tecnologías de redes, sistemas distribuidos y bases de datos se volvieron comunes. Entonces, se hizo posible la construcción de aplicaciones distribuidas con tres capas. En este caso, MVC puede usarse en la implementación de la capa de interfaz, que puede ser, por ejemplo, una aplicación nativa en Windows, implementada utilizando lenguajes como Visual Basic o Java (en este último caso, usando frameworks como Swing). En resumen, la aplicación, en su conjunto, sigue una arquitectura de tres capas, pero usa MVC en la capa de interfaz con el usuario.

A principios de los años 2000, la Web se popularizó y la interfaz de las aplicaciones migró a HTML y, posteriormente, a HTML y JavaScript. La confusión entre los términos MVC y tres capas surgió en esa época, principalmente debido a la aparición de frameworks para la implementación de sistemas web que se denominaron frameworks MVC. Como ejemplo, podemos citar Spring (para Java), Ruby on Rails, Django (para Python) y CakePHP. En realidad, estos frameworks expandieron y adaptaron el concepto de MVC para la Web. Por ejemplo, obligan a organizar un sistema web en tres partes (véase también la próxima figura): vista, compuesta por páginas HTML; controladores, que procesan una solicitud y generan una nueva vista como respuesta; y modelo, que es la capa que persiste los datos en una base de datos

Por lo tanto, en una arquitectura MVC, la interfaz gráfica está formada por objetos de Vista y por Controladores. Sin embargo, en muchos sistemas no existe una distinción clara entre Vista y Controladores. Según Fowler ([Fowler, página 331](https://dl.acm.org/doi/book/10.5555/579257)), incluso la mayoría de las versiones de Smalltalk no separan estos dos componentes. Por eso, es más fácil entenderlo de la siguiente manera:

MVC = (Vista + Controladores) + Modelo = Interfaz Gráfica + Modelo

La siguiente figura muestra las dependencias entre las clases de una arquitectura MVC. La figura refuerza que la interfaz gráfica está compuesta por la Vista y los Controladores. También podemos observar que la Interfaz Gráfica puede depender del Modelo. Sin embargo, las clases de Modelo no tienen dependencias con las clases de la Interfaz Gráfica. En realidad, podemos entender la Interfaz Gráfica como un observador del Modelo. Cuando el estado de los objetos del Modelo cambia, la interfaz del sistema debe actualizarse automáticamente.

Entre las ventajas de las arquitecturas MVC, podemos citar:

- MVC favorece la especialización del trabajo de desarrollo. Por ejemplo, se puede contar con desarrolladores especializados en la implementación de interfaces gráficas, quienes son llamados desarrolladores de front-end. Por otro lado, los desarrolladores de clases de Modelo no necesitan conocer ni implementar código de interfaz con los usuarios.

- MVC permite que las clases de Modelo sean usadas por diferentes Vistas, como se ilustra en la siguiente figura. En este ejemplo, un objeto de Modelo almacena dos valores: horas y minutos. Estos datos se presentan en dos vistas diferentes. En la primera, como un reloj analógico. En la segunda, como un reloj digital.

- MVC favorece la capacidad de prueba. Es más fácil probar objetos no visuales, es decir, aquellos que no están relacionados con la implementación de interfaces gráficas. Por eso, al separar los objetos de presentación de los objetos de Modelo, se facilita la prueba de estos últimos.

> El corazón y la parte más valiosa de MVC está en la separación entre el código de la interfaz con el usuario (la Vista, también llamada presentación) y la lógica de dominio (el Modelo). Las clases de presentación implementan únicamente la lógica necesaria para manejar la interfaz de usuario. Por otro lado, los objetos de dominio no incluyen código visual, solo lógica de negocio. Esto separa dos partes complejas de los sistemas de software en partes que son más fáciles de modificar. También permite múltiples presentaciones de la misma lógica de negocio.
> *M. Fowler and K. Beck*

**Pregunta Frecuente: ¿Cuál es la diferencia entre MVC y tres capas? La respuesta será un poco extensa y nos basaremos en la evolución histórica de estas arquitecturas:**

- MVC surgió a finales de la década de los 70, para ayudar en la construcción de interfaces gráficas. Es decir, aplicaciones que incluyen una interfaz con ventanas, botones, cuadros de texto, etc. Como ejemplo, podemos mencionar un paquete de oficina con aplicaciones como Word, Excel y PowerPoint, en el caso del sistema operativo Windows.

- En la década de los 90, las tecnologías de redes, sistemas distribuidos y bases de datos se volvieron comunes. Entonces, se hizo posible la construcción de aplicaciones distribuidas con tres capas. En este caso, MVC puede usarse en la implementación de la capa de interfaz, que puede ser, por ejemplo, una aplicación nativa en Windows, implementada utilizando lenguajes como Visual Basic o Java (en este último caso, usando frameworks como Swing). En resumen, la aplicación, en su conjunto, sigue una arquitectura de tres capas, pero usa MVC en la capa de interfaz con el usuario.

- A principios de los años 2000, la Web se popularizó y la interfaz de las aplicaciones migró a HTML y, posteriormente, a HTML y JavaScript. La confusión entre los términos MVC y tres capas surgió en esa época, principalmente debido a la aparición de frameworks para la implementación de sistemas web que se denominaron frameworks MVC. Como ejemplo, podemos citar Spring (para Java), Ruby on Rails, Django (para Python) y CakePHP. En realidad, estos frameworks expandieron y adaptaron el concepto de MVC para la Web. Por ejemplo, obligan a organizar un sistema web en tres partes (véase también la próxima figura): vista, compuesta por páginas HTML; controladores, que procesan una solicitud y generan una nueva vista como respuesta; y modelo, que es la capa que persiste los datos en una base de datos.

Entonces, a pesar de que los sistemas web se parecen a los sistemas de tres capas, los frameworks web más populares optaron por usar términos típicos de MVC para nombrar sus componentes. Por lo tanto, la mejor manera de responder a la pregunta es afirmar que existen dos vertientes de sistemas MVC: la vertiente clásica, que surgió con Smalltalk-80, y la vertiente web, que se volvió común en la década de los 90 y principios de los 2000. Esta última vertiente se asemeja bastante a los sistemas de tres capas.

### Ejemplo Arquitectura MVC

Para el siguiente ejemplo usaremos una arquitectura física de tres capas: cliente web (browser como firefox, chrome, etc.), servidor de aplicaciones (wildfly) y un servidor de base de datos (postgresql). Para configurar esta arquitectura usaremos contenedores creados con docker.

[← Volver](index.md)
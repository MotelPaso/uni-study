# Modelos

_Original: https://www.danielsanmartin.cl/blog/modelos/_


> Todos los modelos son erróneos, pero algunos modelos son útiles. Así, la pregunta que debes hacer no es: “¿Es verdadero el modelo?” (nunca lo es), sino: “¿Es lo suficientemente bueno este modelo para esta aplicación particular?”

*George Box*

### Modelos de Software

Como ya se ha señalado, los requisitos documentan lo que un sistema debe hacer, utilizando un nivel de abstracción cercano al problema y a sus usuarios. Por otro lado, el código fuente es una representación concreta, de bajo nivel y ejecutable del comportamiento de un sistema. Por lo tanto, existe una brecha entre estos dos mundos: los requisitos y el código fuente. Para llenar esa brecha, desde los inicios del área, los ingenieros de software han invertido en la creación de modelos, los cuales se elaboran para facilitar la comprensión y el análisis de un sistema. Para cumplir esta función, los modelos utilizados en Ingeniería de Software son más detallados que los requisitos, pero todavía menos complejos que el código fuente de un sistema.

Los modelos también se utilizan ampliamente en otras ramas de la ingeniería. Por ejemplo, una ingeniera civil puede decidir construir una maqueta para mostrar cómo será el puente que ha sido contratada para diseñar. Luego, puede elaborar un modelo matemático y físico del puente y utilizarlo para simular y demostrar propiedades del mismo, tales como la carga máxima, la resistencia a vientos, olas, terremotos, entre otras.

Lamentablemente, los modelos de software, al menos hasta ahora, son menos efectivos que los modelos matemáticos utilizados en otras ingenierías. La razón es que, al abstraer detalles, también descartan parte de la complejidad que resulta esencial para los sistemas modelados. Frederick Brooks comenta esta cuestión en su ensayo clásico No existe bala de plata ([enlace](https://ieeexplore.ieee.org/document/1663532)).

> La complejidad del software es una propiedad esencial y no accidental. Por lo tanto, las representaciones de una entidad de software que abstraen su complejidad normalmente también abstraen su esencia. Durante tres siglos, matemáticos y físicos lograron grandes avances construyendo modelos simplificados de un fenómeno complejo, derivando propiedades de tales modelos y verificando dichas propiedades mediante experimentos. Ese paradigma funcionó porque las complejidades ignoradas no son propiedades esenciales del fenómeno en estudio. Sin embargo, este enfoque no funciona cuando las complejidades son esenciales.

La frase de apertura, del estadístico británico George Box, también remite a una reflexión sobre el uso práctico de los modelos. Aunque la frase se refiere a modelos matemáticos, puede aplicarse también a otros tipos de modelos, incluidos los modelos de software. Según Box, todos los modelos son erróneos, pues constituyen simplificaciones o aproximaciones de la realidad. Por ello, la cuestión principal consiste en evaluar si, a pesar de tales simplificaciones, un modelo sigue siendo una abstracción útil para el estudio de alguna propiedad del objeto o fenómeno que representa.

En esta introducción se busca calibrar las expectativas asociadas al estudio de los modelos de software. Por una parte, como se ha señalado, no poseen la misma efectividad que los modelos utilizados en otras ingenierías. Además, por lo general, los modelos de software no son formalismos matemáticos, sino representaciones gráficas de determinadas dimensiones de un sistema de software. Por otra parte, esto no significa que los modelos de software sean inútiles. Si no se generan expectativas irreales, pueden desempeñar un papel importante en el desarrollo de sistemas de software, tal como se verá más adelante.

Si se piensa en términos de actividades de desarrollo de software, la creación de modelos adquiere una gran relevancia en la fase de diseño. Durante el levantamiento de requisitos, la atención se centra en la definición del problema que el sistema deberá resolver. Cuando se avanza hacia las actividades de diseño, el problema ya debe estar debidamente comprendido y la atención se desplaza hacia la concepción de una solución capaz de resolverlo. Una vez diseñada esa solución, debe implementarse utilizando lenguajes de programación, bibliotecas, frameworks, bases de datos, entre otros recursos.

En particular, aquí se estudiará un subconjunto de los diagramas propuestos por UML (Unified Modeling Language). En primer lugar, se describirá la historia y el contexto que condujeron a la creación de UML. A continuación, se analizarán con mayor detalle algunos de sus principales diagramas.

**Profundización**: Desde la década de 1970, investigadores han estudiado el uso de modelos matemáticos en Ingeniería de Software a través de lo que se conoce como **Métodos Formales**. Estos métodos emplean una notación matemática, basada por ejemplo en lógica, teoría de conjuntos o redes de Petri, para derivar **especificaciones formales** de sistemas de software. Además de ser precisas y no ambiguas, estas especificaciones pueden utilizarse para demostrar propiedades de un sistema incluso antes de su implementación. Por ejemplo, en principio podría demostrarse que un sistema concurrente no presenta interbloqueos ni condiciones de carrera. Aunque esto pueda parecer ambicioso, en otras ingenierías sí ocurre. Retomando el ejemplo anterior, los ingenieros civiles han utilizado durante siglos modelos matemáticos para demostrar, antes de la construcción, que un puente soportará determinada carga y ciertas condiciones climáticas. Sin embargo, el uso de formalismos y especificaciones matemáticas en Ingeniería de Software no ha progresado de la misma manera que en otras ingenierías. Por ello, su empleo sigue siendo limitado en la actualidad, salvo quizá en algunos sistemas de misión crítica.

### UML

UML es una notación gráfica para el modelado de software. El lenguaje define un conjunto de diagramas para documentar y ayudar en el diseño de sistemas de software, particularmente sistemas orientados a objetos. Los orígenes de UML se remontan a la década de 1980, cuando el paradigma de orientación a objetos estaba madurando y viviendo su auge. Así, surgieron diversos lenguajes orientados a objetos, como C++, y también algunas notaciones gráficas para el modelado de software. Debe recordarse que los sistemas en la década de 1980 se desarrollaban según el modelo Waterfall, que prescribe una fase extensa y prolongada de diseño. La propuesta de UML era que en esa fase se crearan modelos gráficos, que luego serían entregados a los programadores para ser convertidos en código fuente.

En realidad, UML es el resultado de un esfuerzo por unificar las notaciones gráficas que surgieron a fines de la década de 1980 e inicios de la de 1990. Específicamente, la primera versión de UML fue propuesta en 1995, como resultado de la unificación de notaciones que estaban siendo desarrolladas de forma independiente por tres ingenieros de software conocidos en esa época: Grady Booch, Jim Rumbaugh e Ivar Jacobson. En ese período surgieron también herramientas para dibujar diagramas UML, llamadas herramientas CASE (Computer-Aided Software Engineering). El nombre está inspirado en las herramientas CAD (Computer Aided Design), utilizadas para crear modelos de productos de la ingeniería tradicional, como casas, puentes, automóviles y aviones. Por ello, era importante contar con una estandarización de UML, de modo que un diagrama creado en una herramienta CASE pudiera abrirse y editarse en otra herramienta, de una empresa diferente. De hecho, en 1997 UML pasó a ser un estándar administrado por la OMG, una organización de estandarización financiada por industrias de software. Desde el inicio, el desarrollo de UML estuvo liderado por consultores influyentes y por grandes empresas de herramientas o consultoría, como Rational, que posteriormente sería adquirida por IBM.

**¿Cómo usar UML?**

Martin Fowler, en su libro sobre UML, propone una clasificación de las formas de uso de este lenguaje de modelado. Según él, existen tres formas de uso de UML: como plano, como lenguaje de programación o como bosquejo. A continuación se describe cada una de ellas.

**UML como plano** corresponde al uso de UML imaginado por sus creadores en la década de 1990. En esta forma de uso, se defiende que, tras el levantamiento de requisitos, se produzca un conjunto de modelos, o planos técnicos, que documenten diversos aspectos de un sistema, siempre usando diagramas UML. Estos modelos serían creados por analistas de sistemas, mediante herramientas CASE, y luego entregados a programadores para su codificación. Por tanto, UML como plano se recomienda cuando se emplean procesos de desarrollo de tipo Waterfall o cuando se adopta el Proceso Unificado (UP). Sin embargo, el uso de UML para construir modelos detallados y completos es cada vez menos frecuente. Por ejemplo, con métodos ágiles no existe una larga fase inicial de diseño. En su lugar, las decisiones de diseño se toman y refinan a lo largo del desarrollo, en cada una de las iteraciones o sprints. Por ello, aquí no se profundizará en el uso de UML como plano.

**UML como lenguaje de programación** corresponde al uso de UML imaginado por la OMG tras la estandarización del lenguaje de modelado. De forma ambiciosa, y al menos durante un período, se vislumbró la generación automática de código a partir de modelos UML. En otras palabras, ya no existiría una fase de codificación, pues el código sería generado directamente a partir de la compilación de modelos UML. Esta forma de uso se conoce como **Desarrollo Dirigido por Modelos** (Model Driven Development o MDD). Para que MDD fuera viable, UML fue ampliado y adquirió nuevos recursos y diagramas. Fue a partir de ese momento que el lenguaje ganó la reputación de ser pesado y complejo. Sin embargo, incluso con esa complejidad adicional, el uso de UML para la generación de código no se volvió común, al menos en la gran mayoría de los sistemas.

Queda entonces el tercer uso, **UML como bosquejo**, que corresponde a la forma que se estudiará aquí. En ella, UML se utiliza para construir diagramas ligeros e informales de partes de un sistema, de ahí el nombre de bosquejo (sketch). Estos diagramas se emplean para la comunicación entre desarrolladores, en dos situaciones principales.

- Ingeniería hacia adelante (Forward Engineering): cuando los desarrolladores usan modelos UML para discutir y analizar alternativas de diseño antes de que exista cualquier código. Por ejemplo, supóngase que una historia ha sido asignada al sprint actual. Antes de implementarla, los desarrolladores pueden reunirse y hacer un bosquejo de las principales clases que deberán crearse en el sistema, así como de las relaciones entre ellas. El objetivo es validar la propuesta de tales clases antes de comenzar a codificar.

- Ingeniería inversa (Reverse Engineering): cuando los desarrolladores usan modelos UML para analizar y discutir una funcionalidad que ya se encuentra implementada en el código fuente. Por ejemplo, un desarrollador más experimentado puede dibujar algunos diagramas UML para explicar a un desarrollador recién incorporado cómo está implementada una funcionalidad. Normalmente, resulta más fácil conducir esta explicación mediante modelos y diagramas gráficos que analizando y explicando cada línea de código. Es decir, se aplica aquí el dicho según el cual una imagen vale más que mil palabras.

En ambas situaciones, el objetivo no es generar modelos completos y detallados. Por ello, no se considera el uso de herramientas complejas y costosas, como las herramientas CASE. Mucho menos se contempla la generación automática de código a partir de esos bosquejos. Con frecuencia, los diagramas se dibujan en una pizarra y luego se fotografían y se borran. Adicionalmente, solo se utiliza un subconjunto de los diagramas UML.

Como los bosquejos son pequeños e informales, podría cuestionarse la necesidad de un lenguaje estandarizado en los escenarios mencionados. Sin embargo, se considera preferible utilizar una notación existente desde hace años, aunque sea de manera parcial, antes que inventar una notación propia. En particular, el uso de UML como bosquejo contribuye a evitar dos extremos. Por una parte, no supone un uso rígido, detallado y sistemático de UML. Por otra, evita el uso de una notación informal y ad hoc, cuya semántica puede no resultar clara para todos los desarrolladores. Además, UML suele utilizarse en libros, tutoriales y documentos que explican el uso de frameworks o técnicas de programación. Por ejemplo, se pueden emplear diagramas UML para ilustrar el funcionamiento de algunos patrones de diseño. Si el lector no ha tenido contacto con UML, es posible que tenga dificultad para comprender el concepto que se está explicando.

En síntesis, los modelos de software, como los diagramas UML, se utilizan para la comunicación entre desarrolladores. Es decir, son escritos por y para desarrolladores. Se trata de una diferencia importante respecto de los documentos de requisitos, que son escritos por desarrolladores, pero de forma que puedan ser leídos y verificados por los usuarios finales del sistema.

**Mundo real**: En el segundo semestre de 2013, Sebastian Baltes y Stephan Diehl, ambos investigadores de la Universidad de Trier, en Alemania, pidieron a 394 desarrolladores que respondieran un cuestionario sobre el uso de bosquejos (sketches) en actividades de diseño de software. Estos desarrolladores estaban distribuidos en más de 32 países, aunque la mayoría provenía de Alemania (54%). El análisis de las respuestas reveló resultados interesantes sobre el uso de bosquejos en actividades de diseño y desarrollo de software, como se describe a continuación.

- El 24% de los desarrolladores que participaron en la investigación había creado su último bosquejo el mismo día en que respondió el cuestionario, y el 39% lo había hecho en un intervalo máximo de una semana antes de responder. Por lo tanto, estos porcentajes indican que los bosquejos son creados con frecuencia por los desarrolladores de software.

- El 58% de los últimos bosquejos creados por los participantes fueron posteriormente archivados, ya sea en papel (6%), de forma digital (42%) o de ambas formas (10%). Esto sugiere que los desarrolladores consideran que los bosquejos contienen información importante que quizá pueda resultar útil en el futuro.

- El 40% de los bosquejos se realizó en papel, el 18% en pizarras y el 39% en computadores.

- El 52% de los bosquejos se realizó para ayudar en el diseño de la arquitectura del sistema, el 48% para ayudar en el diseño de nuevas funcionalidades, el 46% para explicar alguna tarea a otro desarrollador, el 45% para analizar requisitos y el 44% para ayudar en la comprensión de una tarea. La suma de los porcentajes supera el 100% porque los participantes podían marcar más de una respuesta.

- El 48% de los bosquejos contenía algún elemento de UML y el 9% se basaba íntegramente en diagramas UML. Por lo tanto, estos porcentajes refuerzan la importancia de estudiar UML, no como notación para documentación detallada de sistemas, sino como apoyo para la construcción de modelos informales y parciales.

**Diagramas UML**

Los diagramas UML se clasifican en dos grandes grupos:

- Diagramas estáticos (o estructurales) modelan la estructura y organización de un sistema, incluyendo información sobre clases, atributos, métodos, paquetes, etc. Aquí estudiaremos dos diagramas estáticos: diagramas de clases y diagramas de paquetes.

- Diagramas dinámicos (o comportamentales) modelan eventos que ocurren durante la ejecución de un sistema. Por ejemplo, pueden modelar una secuencia de llamadas a métodos. Aquí estudiaremos dos diagramas dinámicos: diagramas de secuencia y diagramas de actividades.

Para comprender mejor la diferencia entre estos grupos de diagramas, los diagramas estáticos tratan únicamente con información que está disponible, por ejemplo, en el momento de la compilación del código resultante de los modelos. Esta visión es estática porque no cambia, a menos que se realicen cambios en los modelos. En cambio, los diagramas dinámicos proporcionan una visión de tiempo de ejecución. Son dinámicos porque es común tener ejecuciones distintas de un mismo programa. Por ejemplo, los usuarios pueden ejecutar el programa con entradas diferentes, seleccionar opciones y menús distintos, etc. En resumen, si se está interesado en modelar la estructura de un programa, se deben usar diagramas estáticos. Si el interés es modelar el comportamiento de un programa, es decir, lo que puede ocurrir durante su ejecución, qué métodos se ejecutan efectivamente, etc., se debe utilizar algún diagrama dinámico de UML. Por último, conviene recordar que los diagramas de casos de uso se emplean para la especificación de requisitos.

**Aviso**: Existen diversas versiones de UML. En lo que sigue se utilizará la versión adoptada en la **tercera edición del libro UML Distilled, de Martin Fowler**. Este libro fue uno de los primeros trabajos en discutir el uso de UML como bosquejo (sketches). En realidad, aquí se estudiará un pequeño subconjunto de la versión 2.0. Además de tratar solo cuatro diagramas, no se cubrirán todos los recursos de cada uno de ellos. El desafío al presentar este contenido consiste en seleccionar el 20% o menos de los recursos de UML que son responsables del 80% o más de su uso práctico en la actualidad. Para tener una idea del nivel de detalle alcanzado por UML, la especificación de la versión más reciente del lenguaje, la versión 2.5.1 al momento de redactarse ese texto, posee 796 páginas. Puede encontrarse en el sitio de la OMG ([enlace](https://www.omg.org/spec/UML/2.5.1/About-UML)).

### Diegrama de Clases

Los diagramas de clases son los diagramas más utilizados de UML. Ofrecen una representación gráfica de un conjunto de clases, proporcionando información sobre atributos, métodos y relaciones existentes entre las clases modeladas.

Un diagrama de clases se dibuja utilizando rectángulos y flechas. Cada una de las clases se representa mediante un rectángulo con tres compartimentos, como se muestra en la figura siguiente. Estos compartimentos contienen el nombre de la clase, normalmente en negrita, sus atributos y sus métodos, como también se ilustra a continuación.

A continuación se muestra un diagrama con dos clases: Persona y Teléfono.

En ese diagrama, se puede observar que la clase Persona tiene tres atributos —nombre, apellido y teléfono— y dos métodos —setPersona y getPersona—. Los tres atributos son privados, como lo indica el signo - antes de cada uno. También se informa el tipo de cada atributo. Por su parte, los dos métodos son públicos, como lo indica el signo +. El diagrama también incluye una segunda clase, llamada Teléfono, con tres atributos privados —código, número y celular— y tres métodos públicos —setTelefono, getTelefono e isCelular—. En el caso de los métodos, también se informa el nombre de sus parámetros y el tipo de retorno.

Sin embargo, si fuera solo eso, los diagramas darían la impresión de que las clases de un sistema son islas sin comunicación entre sí. No obstante, uno de los principales objetivos de los diagramas de clases es mostrar visualmente las relaciones que existen entre las clases de un sistema. Por ello, también incluyen líneas y flechas, las cuales se usan para representar tres tipos de relaciones: asociación, herencia y dependencia. Trataremos cada una de ellas en los siguientes párrafos.

#### Asociaciones

Cuando una clase A posee un atributo b de un tipo B, decimos que existe una asociación de A hacia B, la cual se representa mediante una flecha, también de A hacia B. En el extremo de la flecha, se indica el nombre del atributo de A responsable de la asociación —en nuestro caso, b—. Véase el ejemplo siguiente (en él, solo mostramos la información que nos interesa; por eso, el compartimento de atributos y métodos está vacío):

Para que quede mas claro, se muestra el código que grafica el diagrama anterior:

```java
class A {
   ...
   private B b;
   ...
}


class B {
   ...
}
```

Por tanto, usando asociaciones, podemos transformar el primer diagrama que mostramos en esta sección, con las clases Persona y Teléfono, en el siguiente diagrama:

Las dos versiones del diagrama son semánticamente idénticas. La diferencia es que, en la primera versión, las clases aparecen aisladas. En cambio, en la segunda versión, mostrada arriba, queda visualmente claro que existe una asociación de Persona hacia Teléfono. Reforzando esta idea, en ambos diagramas, Persona tiene un atributo telefono de tipo Teléfono. Sin embargo, en la primera versión, ese atributo se muestra dentro del compartimento de atributos de la clase Persona. En la segunda versión, en cambio, se presenta fuera de ese compartimento. Más específicamente, en el extremo de la flecha que conecta Persona con Teléfono. El objetivo es dejar claro que el atributo pertenece a Persona, pero apunta a un objeto de tipo Teléfono.

Frecuentemente, las asociaciones incluyen información de multiplicidad, que indica cuántos objetos pueden estar asociados al atributo responsable de la asociación. Las informaciones de multiplicidad más comunes son las siguientes: 1 (exactamente un objeto), 0..1 (cero o un objeto) y * (cero o más objetos).

En el siguiente ejemplo, incluimos información sobre la multiplicidad de la asociación entre Persona y Teléfono, que en este caso definimos como 0..1. Esta información aparece sobre el nombre del atributo responsable de la asociación, en este caso, telefono. Y explicita que una Persona puede tener cero o un único Teléfono. Usando términos de programación, el atributo telefono de Persona puede tener el valor null, es decir, la Persona en cuestión no tiene un Teléfono asociado. O bien puede estar asociada a un único objeto de tipo Teléfono.

En el siguiente ejemplo, la semántica ya es diferente. En este caso, una Persona puede estar asociada a múltiples objetos de tipo Teléfono, incluso a ninguno. Esa multiplicidad se representa mediante el * que añadimos justo encima de la flecha de la asociación.

Para no dejar dudas sobre la semántica de una asociación bidireccional, mostramos también el código de las dos clases:

```java
class Pessoa {
   ...
   private Fone fone;
   ...
}

class Fone {
   ...
   private Pessoa[] dono;
   ...
}
```

En ese código, Persona posee un atributo privado telefono de tipo Teléfono, que puede ser null; con ello, satisfacemos el extremo 0..1 de la asociación bidireccional. Por otro lado, Teléfono posee un vector privado, de nombre dueno, que referencia objetos de tipo Persona; así, satisfacemos el extremo * de la misma asociación.

En el último diagrama de clases, omitimos todos los símbolos de visibilidad, tanto pública (+) como privada (-). Esto se hizo deliberadamente para destacar que estamos tratando el uso de UML para la creación de bosquejos, cuando los diagramas se elaboran para discutir e ilustrar una idea de diseño. Por lo tanto, en ese contexto, no tiene sentido exigir que los diagramas sean sintácticamente perfectos. Por eso, pequeños errores u omisiones son tolerados, especialmente cuando no perjudican el propósito del diagrama.

**Profundización:** UML — dependiendo de la versión que se esté usando — admite distintas notaciones para las asociaciones. Por ejemplo, a veces se indica un nombre para la asociación, el cual se muestra justo encima y a lo largo de la flecha que une las dos clases. Otras veces, en el caso de asociaciones bidireccionales, se omiten las dos flechas, pues la estandarización de UML define lo siguiente: una asociación en la que ninguno de los extremos está marcado con una flecha de navegabilidad es navegable en ambas direcciones. Sin embargo, estas notaciones alternativas tienden a ser confusas o incluso ambiguas. Por ejemplo, Gonzalo Génova y otros dos investigadores de la Universidad de Carlos III, Madrid, España, hacen la siguiente observación sobre el uso de asociaciones bidireccionales sin flechas: lamentablemente, esto puede introducir ambigüedad en la notación gráfica, porque ya no conseguimos distinguir entre asociaciones bidireccionales y asociaciones sin especificación de navegabilidad en uno de sus extremos (([enlace](https://www.jot.fm/contents/issue_2003_09/article4.html)), Sección 3, cuarto párrafo).

Existen además dos conceptos que se mencionan con frecuencia cuando estudiamos asociaciones en UML: composición y agregación. La composición es una relación en la cual la clase de destino no puede existir de forma independiente de la clase de origen. En cambio, cuando las dos clases tienen ciclos de vida independientes, tenemos una relación de agregación. Sin embargo, en la práctica, estos conceptos también generan confusión y, por eso, decidimos no incluirlos en la explicación sobre diagramas de clases. La misma opinión es compartida por otros autores. Por ejemplo, Fowler afirma que la agregación es algo estrictamente sin sentido; por lo tanto, recomienda ignorar este concepto en los diagramas (([enlace](https://dl.acm.org/doi/book/10.5555/861282)), página 68).

#### Herencia

En diagramas de clases, las relaciones de herencia se representan mediante flechas con la punta no rellena. Estas flechas se usan para conectar las subclases con su clase base. En el siguiente ejemplo, indican que PersonaFisica y PersonaJuridica son subclases de Persona. Como es usual en orientación a objetos, las subclases heredan todos los atributos y métodos de la clase base, pero también pueden agregar nuevos miembros. Por ejemplo, solo PersonaFisica tiene cpf y solo PersonaJuridica tiene cnpj.

### Dependencias

Existe una dependencia de una clase A hacia una clase B, representada por una flecha con línea discontinua de A hacia B, cuando la clase A usa la clase B, pero ese uso no ocurre mediante asociación, es decir, A no tiene un atributo de tipo B, ni mediante herencia, es decir, A no es una subclase de B.

Las dependencias ocurren, por ejemplo, cuando un método de A declara un parámetro o una variable local de tipo B, o cuando un método de A lanza una excepción de tipo B. Una dependencia se considera una modalidad menos fuerte de relación entre clases que las relaciones que ocurren mediante asociación y herencia.

Para ilustrar el uso de dependencias, considere el siguiente código:

```java
import java.util.Stack;

class MinhaClasse {
   ...
   private void metodoX() {
     Stack stack = new Stack();
     ...
   } ...
}
```

Observe que el método metodoX de MiClase posee una variable local de tipo java.util.Stack. En este caso, decimos que existe una dependencia de MinhaClasse hacia java.util.Stack, la cual se modela de la siguiente forma:

Algunas veces, justo encima y a lo largo de la flecha discontinua, se informa el tipo de dependencia usando palabras como create, para indicar que la clase de origen instancia objetos de la clase destino de la dependencia, o call, para indicar que la clase de origen llama métodos de la clase destino.

Estas palabras se escriben entre signos de menor («) y mayor (»). En el siguiente diagrama, por ejemplo, queda claro el tipo de dependencia que ShapeFactory establece con la clase Shape.

#### Diagrama de Paquetes

Los diagramas de paquetes son recomendables cuando se pretende ofrecer un modelo de más alto nivel de un sistema, que muestre solo grupos de clases, es decir, paquetes, y las dependencias entre ellos. Para ello, UML define un rectángulo especial para representar paquetes, como se muestra a continuación:

A diferencia de los rectángulos de clases, el rectángulo de paquetes incluye solo el nombre del paquete, en negrita. Además, posee un detalle en la parte superior, con forma de trapecio, para diferenciarlo mejor de los rectángulos de clase.
La figura de la página siguiente muestra un ejemplo de diagrama de paquetes. En ese diagrama, podemos ver que el sistema posee cuatro paquetes principales: MobileView, WebView, BusinessLayer y Persistence. También podemos observar las dependencias, representadas mediante flechas discontinuas, que existen entre ellos. Ambos paquetes View usan clases de BusinessLayer. Por otro lado, las clases de BusinessLayer también usan clases de la View, por ejemplo, para notificarlas sobre la ocurrencia de algún evento. Por eso, las flechas que conectan los paquetes de View con BusinessLayer son bidireccionales. Finalmente, solo las clases del paquete BusinessLayer usan clases del paquete Persistence.

Para concluir, nos gustaría agregar dos observaciones:

- Las dependencias no incluyen información sobre cuántas clases del paquete de origen dependen de clases del paquete de destino. Por ejemplo, supongamos dos paquetes P1 y P2, ambos con 100 clases. Supongamos, además, que una única clase de P1 usa una única clase de P2. Incluso en ese caso, decimos que existe una dependencia de P1 hacia P2.

- En los diagramas de paquetes, tenemos un único tipo de flecha, siempre discontinua, que representa cualquier tipo de relación, ya sea mediante asociación, herencia o dependencia simple. Esta semántica es diferente de la que presentamos para las flechas discontinuas en los diagramas de clases. En estos últimos, las relaciones de asociación y herencia se representan mediante flechas continuas. Solo las demás dependencias se representan mediante flechas discontinuas.

#### Diagrama de Secuencia

Los diagramas de secuencia son diagramas dinámicos, también llamados diagramas comportamentales. Por eso, en lugar de clases, modelan objetos de un sistema. Además, incluyen información sobre qué métodos de esos objetos se ejecutan en un determinado escenario de uso de un programa. Por lo tanto, se usan cuando se pretende explicar el comportamiento de un sistema en un escenario determinado. Por ejemplo, al final de esta sección presentaremos un diagrama de secuencia que ilustra los métodos que se llaman cuando un cliente llega a un cajero automático y solicita una operación de retiro de dinero.

Antes de eso, para iniciar la presentación de los diagramas de secuencia, usaremos el diagrama de la página siguiente. Aunque es simple, este diagrama sirve para mostrar la dinámica y la notación usada por los diagramas de secuencia. Como ya dijimos, los diagramas de secuencia modelan objetos, los cuales se representan mediante rectángulos con el nombre de los objetos modelados. Estos rectángulos se disponen en la primera línea del diagrama. Por lo tanto, en el diagrama anterior se representan dos objetos, llamados a1 y b1.

Debajo de cada objeto se dibuja una línea vertical, la cual puede asumir dos formas:(1) cuando se dibuja de forma discontinua, el objeto está inactivo, es decir, ninguno de sus métodos se está ejecutando; (2) cuando la línea queda rellena, adquiriendo una forma rectangular, uno de los métodos del objeto fue llamado y se encuentra en ejecución. Cuando esa ejecución termina, la línea vuelve a quedar discontinua.

Además, el inicio de la llamada se indica mediante una flecha horizontal, con el nombre del método llamado. El retorno de la llamada se indica mediante una flecha discontinua, con el nombre del objeto retornado. Sin embargo, a veces la flecha de retorno se omite, como en el caso de la llamada al método g. Existen dos motivos para esta omisión: (1) el tipo de retorno es void; o (2) el objeto de retorno no es lo suficientemente relevante como para ser representado en el diagrama.

En el diagrama de secuencia mostrado anteriormente representamos solo dos objetos, a1 y b1. Sin embargo, un diagrama de secuencia puede tener más objetos. No obstante, ese número no puede crecer demasiado, porque el diagrama termina volviéndose complejo y difícil de entender. Por ejemplo, puede que no sea posible representarlo en una sola hoja de papel o en una pantalla de computador.
Un objeto puede quedar activo e inactivo varias veces en un mismo diagrama. Es decir, puede ejecutar un método, quedar inactivo, ejecutar un nuevo método, volver a quedar inactivo, etc. Existe además un caso especial, cuando un objeto llama a un método de sí mismo, es decir, cuando llama a un método usando this. Para ilustrar este caso, supongamos el siguiente programa.

```java
class A {

  void g() {
    ...
  }

  void f() {
    ...
    g();
    ...
  }

  main() {
    A a = new A();
    a.f();
  }
}
```

La ejecución de ese programa se representa mediante el siguiente diagrama de secuencia. Observe cómo la llamada a g() realizada por f() se representa mediante un nuevo rectángulo, que sale del rectángulo que representa la activación de la función f().

Para concluir, el siguiente diagrama muestra un escenario más real, que ilustra los métodos llamados cuando el cliente de un cajero automático solicita un depósito de cierto valor en su cuenta.

#### Diagrama de Actividades

Los diagramas de actividades se usan para representar, en un nivel alto, un proceso o flujo de ejecución. Los principales elementos de estos diagramas son las acciones, representadas mediante rectángulos. Además, existen elementos de control que definen el orden de ejecución de las acciones.

La figura de la página siguiente muestra un diagrama de actividades que modela el proceso seguido después de que un usuario finaliza una compra en una tienda virtual. Para ello, se asume que los productos comprados ya están en el carrito de compra.

Para entender el funcionamiento de un diagrama de actividades, como el que se muestra en la figura, debemos asumir que existe una ficha, o token, imaginaria que avanza por los nodos del diagrama. A continuación, explicamos el comportamiento de cada nodo de un diagrama de actividades, asumiendo la existencia de esa ficha.

- **Nodo inicial** : Crea una ficha para dar inicio a la ejecución del proceso. Hecho esto, transfiere la ficha a su único flujo de salida. Por definición, el nodo inicial no posee flujo de entrada.

- **Acciones** : Poseen un único flujo de entrada y un único flujo de salida. Para que una acción sea ejecutada, una ficha debe llegar a su flujo de entrada. Después de la ejecución, la ficha se transfiere al flujo de salida.

- **Decisiones** : Poseen un único flujo de entrada y dos o más flujos de salida. Cada flujo de salida posee una variable booleana asociada, llamada guarda. Para tomar una decisión, se necesita recibir una ficha en el flujo de entrada. Cuando esto ocurre, la ficha se transfiere únicamente al flujo de salida cuya condición es verdadera.

- **Merges** : Pueden poseer varios flujos de entrada, pero un único flujo de salida. Cuando una ficha llega a uno de los flujos de entrada, se transfiere al flujo de salida. Se usan para unir los flujos provenientes de nodos de decisión.

- **Forks** : Poseen un único flujo de entrada y dos o más flujos de salida. Actúan como multiplicadores de fichas: cuando reciben una ficha en el flujo de entrada, crean y transfieren fichas idénticas en cada flujo de salida. Como resultado, pasan a existir múltiples procesos ejecutándose de forma paralela.

- **Joins** : Poseen varios flujos de entrada, pero un único flujo de salida. Actúan como sumideros de fichas: esperan que lleguen fichas a todos los flujos de entrada. Cuando esto ocurre, transfieren una única ficha al flujo de salida. Por lo tanto, se usan para sincronizar procesos. En otras palabras, permiten transformar varios flujos de ejecución en un único flujo.

- **Nodo final** : Puede poseer más de un flujo de entrada, pero no posee flujos de salida. Cuando una ficha llega a uno de los flujos de entrada, se finaliza la ejecución del diagrama de actividades.

**Profundización**: Existen al menos tres alternativas para el modelado de flujos y procesos:

- **Flujogramas**, los cuales fueron propuestos tan pronto como se comenzaron a desarrollar los primeros programas para computadores modernos. Los diagramas de actividades son parecidos a los flujogramas; sin embargo, incluyen soporte para concurrencia mediante forks y joins. Por otro lado, los flujogramas modelan procesos secuenciales.

- **Redes de Petri**, una notación gráfica propuesta por el matemático alemán Carl Adam Petri en 1962 para el modelado de sistemas concurrentes. Las redes de Petri poseen una representación gráfica y también usan fichas (tokens) para marcar el estado actual del sistema. Además, tienen la ventaja de poseer una definición más formal, principalmente si se comparan con los diagramas de actividades. Por otro lado, estos últimos tienden a ofrecer una notación más simple y fácil de entender.

- **BPMN** (Business Process Model and Notation) es un esfuerzo más reciente, iniciado en los años 2000, orientado a proponer una notación gráfica más amigable para el modelado de procesos de negocio que la ofrecida por los diagramas de actividades. Uno de sus objetivos es permitir que los analistas de negocio puedan leer, interpretar y validar diagramas BPMN.

[← Volver](../ingsoft.md)
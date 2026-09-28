# Diseño de Software

_Original: https://www.danielsanmartin.cl/blog/disenho/_


### Propiedades de Diseño

Es cierto que el diseño de sistemas de software depende de la experiencia y, en alguna medida, también del talento y la creatividad. Sin embargo, existen algunas propiedades importantes en el diseño de sistemas. Por eso, estudiar y conocer estas propiedades de diseño puede ayudar en la concepción de sistemas con mayor calidad. En esta sección se estudian las siguientes propiedades de los diseños de software: integridad conceptual, ocultación de información, cohesión y acoplamiento. Además, se enunciarán a continuación algunos principios de diseño, los cuales representan directrices para garantizar que un diseño cumple con determinadas propiedades.

#### Integridad Conceptual

Integridad conceptual es una propiedad de diseño propuesta por Frederick Brooks, el mismo autor de la [Ley de Brooks](https://ieeexplore.ieee.org/document/7961479). El principio fue enunciado en 1975, en la primera edición del libro [The Mythical Man-Month](https://dl.acm.org/doi/book/10.5555/540031). Brooks sostiene que un sistema no puede ser una acumulación de funcionalidades sin coherencia ni cohesión entre ellas. La integridad conceptual es importante porque facilita el uso y la comprensión de un sistema por parte de sus usuarios. Por ejemplo, con integridad conceptual, el usuario acostumbrado a utilizar una parte de un sistema se siente cómodo al usar otra parte, ya que las funcionalidades y la interfaz implementadas a lo largo del producto son siempre consistentes.

Para citar un contraejemplo, es decir, un caso de ausencia de integridad conceptual, asumamos un sistema que utiliza tablas para presentar sus resultados. Dependiendo de la pantalla del sistema en la que se usen, estas tablas tienen diferentes diseños, en términos de tamaño de fuente, uso de negrita, espaciado entre líneas, etc. Además, en algunas tablas es posible ordenar los datos haciendo clic en el título de las columnas, pero en otras tablas esa funcionalidad no está disponible. Por último, los valores se muestran en diferentes monedas. En algunas tablas, los valores se refieren a pesos; en otras tablas, se refieren a dólares. Esta falta de estandarización es una señal de falta de integridad conceptual y, como mencionamos, añade complejidad accidental en el uso y la comprensión del sistema

Enfatizamos el impacto de la falta de integridad conceptual en los usuarios finales de un sistema. Sin embargo, el principio también se aplica al diseño y al código de un sistema. En este caso, los afectados son los desarrolladores, quienes tendrán más dificultad para entender, mantener y evolucionar el sistema. A continuación, mencionamos ejemplos de falta de integridad conceptual a nivel de código:

- Cuando una parte del sistema usa un patrón de nombres para variables (por ejemplo, camel case, como en `notaTotal`), mientras que en otra parte se usa un patrón diferente (por ejemplo, snake case, como en `nota_total`).

- Cuando una parte del sistema utiliza un framework determinado para la manipulación de páginas web, mientras que en otra parte se usa un segundo framework o una versión diferente del primer framework.

- Cuando en una parte del sistema se resuelve un problema utilizando una estructura de datos X, mientras que, en otra parte, un problema similar se resuelve mediante una estructura Y.

- Cuando funciones de una parte del sistema que necesitan cierta información — por ejemplo, la dirección de un servidor — la obtienen directamente de un archivo de configuración. Sin embargo, en otras funciones, de otras partes del sistema, esa misma información debe pasarse como parámetro.

Estos ejemplos revelan una falta de estandarización y, por lo tanto, de integridad conceptual. Son un problema porque dificultan que un desarrollador acostumbrado a mantener una parte del sistema pueda ser asignado para mantener otra parte.

#### Ocultamiento de la Información

Esta propiedad, una traducción de la expresión information hiding (ocultación de información), fue discutida por primera vez en 1972 por David Parnas, en uno de los artículos más importantes e influyentes en el área de Ingeniería de Software de todos los tiempos, cuyo título es: [On the criteria to be used in decomposing systems into modules](https://dl.acm.org/doi/10.1145/361598.361623).

> Este artículo discute la modularización como un mecanismo capaz de hacer que los sistemas de software sean más flexibles y fáciles de entender y, al mismo tiempo, reducir su tiempo de desarrollo. La efectividad de una determinada modularización depende del criterio utilizado para dividir un sistema en módulos

*David Parnas, “On the criteria to be used in decomposing systems into modules”*

**Aviso:** Parnas usa el término módulo en su artículo, pero esto fue en una época en que la orientación a objetos aún no había surgido, al menos como la conocemos hoy. En este capítulo, escrito casi 50 años después del trabajo de Parnas, optamos por el término clase, en lugar de módulo. El motivo es que las clases son la principal unidad de modularización en lenguajes de programación modernos como Java, C++ y Ruby. Sin embargo, el contenido del capítulo se aplica a otras unidades de modularización, incluidas aquellas más pequeñas que las clases, como métodos y funciones, y también a unidades más grandes, como paquetes y componentes.

El ocultamiento de información aporta las siguientes ventajas a un sistema:

- Desarrollo en paralelo: Supongamos que un sistema X fue implementado mediante las clases C1, C2, …, Cn. Cuando estas clases ocultan su información principal, es más fácil implementarlas en paralelo por diferentes desarrolladores. Como resultado, se reduce el tiempo total de implementación del sistema.

- Flexibilidad ante cambios: Por ejemplo, supongamos que descubrimos que la clase Ci es responsable de los problemas de rendimiento del sistema. Cuando los detalles de implementación de Ci están ocultos del resto del sistema, es más fácil reemplazar su implementación por una clase Ci’, que use estructuras de datos y algoritmos más eficientes. Este cambio también es más seguro, ya que como las clases son independientes, se reduce el riesgo de que el cambio introduzca errores en otras clases.

- Facilidad de comprensión: Por ejemplo, un nuevo desarrollador contratado por la empresa puede ser asignado a trabajar en algunas clases únicamente. Por lo tanto, no necesitará comprender toda la complejidad del sistema, sino solo la implementación de las clases que le fueron asignadas.

No obstante, para alcanzar los beneficios mencionados, las clases deben cumplir con la siguiente condición (o criterio): deben ocultar decisiones de diseño que están sujetas a cambios. Debemos entender una decisión de diseño como cualquier aspecto del diseño de la clase, como los requisitos que implementa o los algoritmos y estructuras de datos que se usarán en su código. Por lo tanto, el ocultamiento de información recomienda que las clases deben ocultar detalles de implementación que estén sujetos a cambios. Modernamente, los atributos y métodos que una clase pretende encapsular se declaran con el modificador de visibilidad privado, disponible en lenguajes como Java, C++, C# y Ruby.

Sin embargo, si una clase encapsula toda su implementación, no será útil. Dicho de otra manera, una clase, para ser útil, debe hacer públicos algunos de sus métodos, es decir, permitir que puedan ser llamados por código externo. El código externo que llama a los métodos de una clase se denomina cliente de la clase. También decimos que el conjunto de métodos públicos de una clase define su interfaz. La definición de la interfaz de una clase es muy importante, ya que constituye su parte visible.

Las interfaces deben ser estables, porque los cambios en la interfaz de una clase pueden requerir actualizaciones en sus clientes. Para ser más claro, supongamos una clase Math, con métodos que realizan operaciones matemáticas. Supongamos un método sqrt que calcula la raíz cuadrada de su parámetro. Supongamos además que la firma de este método se modifica, por ejemplo, para devolver una excepción si el valor del parámetro es negativo. Esta modificación tendrá un impacto en todo el código cliente del método sqrt, que deberá ser modificado para manejar la nueva excepción.

**Ejemplo:**

A continuación un trecho de código para un sistema de estacionamiento en su primera versión. Identifique el problema en relación a la propiedad de diseño de ocultamiento de la información.

```java
import java.util.Hashtable;

public class Estacionamiento {

  public Hashtable<String, String> vehiculos;

  public Estacionamiento() {
    vehiculos = new Hashtable<String, String>();
  }

  public static void main(String[] args) {
    Estacionamento e = new Estacionamiento();
    e.vehiculos.put("TCP-7030", "Uno");
    e.vehiculos.put("BNF-4501", "Gol");
    e.vehiculos.put("JKL-3481", "Corsa");
  }
}
```

Esta clase tiene un problema de exposición excesiva de información o, en otras palabras, no oculta estructuras que pueden cambiar en el futuro. Específicamente, la tabla hash que almacena los vehículos estacionados en el estacionamiento es pública. Como resultado, los clientes —como el método main— tienen acceso directo a ella para, por ejemplo, añadir vehículos al estacionamiento. Si en el futuro decidimos usar otra estructura de datos para almacenar los vehículos, todos los clientes deberán ser modificados.

Supongamos que el sistema de estacionamiento fuera manual, con los nombres de los vehículos anotados en una hoja de papel. Haciendo una comparación, esta primera versión de la clase Estacionamiento correspondería —en el caso de este sistema manual— a que el cliente del estacionamiento, después de estacionar su vehículo, entrara en la cabina de control y escribiera él mismo la patente y el modelo de su vehículo en la hoja de control.

La siguiente versión de la clase es mejor, ya que encapsula la estructura de datos responsable de almacenar los vehículos. Ahora existe el método estaciona para estacionar un vehículo. Con esto, los desarrolladores de la clase tienen la libertad de cambiar la estructura de datos sin causar impacto en sus clientes. La única restricción es que la firma de estaciona debe ser preservada.

```java
import java.util.Hashtable;

public class Estacionamiento {

  private Hashtable<String,String> vehiculos;

  public Estacionamiento() {
    vehiculos = new Hashtable<String, String>();
  }

  public void estaciona(String patente, String vehiculo) {
    vehiculos.put(patente, vehiculo);
  }

  public static void main(String[] args) {
    Estacionamiento e = new Estacionamiento();
    e.estaciona("TCP-7030", "Uno");
    e.estaciona("BNF-4501", "Gol");
    e.estaciona("JKL-3481", "Corsa");
  }
}
```

En resumen, esta nueva versión oculta una estructura de datos - sujeta a alteraciones durante la evolución del sistem - y proporciona una interfaz estable para los clientes da la clase - representada por el método `estaciona`.

#### Cohesión

La implementación de cualquier clase debe ser cohesiva, es decir, cada clase debe implementar una única funcionalidad o servicio. Específicamente, todos los métodos y atributos de una clase deben estar orientados a la implementación del mismo servicio. Otra forma de explicar la cohesión es afirmando que cada clase debe tener una única responsabilidad en el sistema. O, dicho de otra manera, debe existir un único motivo para modificar una clase.

La cohesión tiene las siguientes ventajas:

- Facilita la implementación de una clase, así como su comprensión y mantenimiento.

- Facilita la asignación de un único responsable para mantener una clase.

- Facilita la reutilización y prueba de una clase, ya que es más sencillo reutilizar y probar una clase cohesiva que una clase con múltiples responsabilidades.

La separación de intereses (separation of concerns) es otra propiedad deseable en los proyectos de software, la cual es similar al concepto de cohesión. Defiende que una clase debe implementar solo un interés (concern). En este contexto, el término interés se refiere a cualquier funcionalidad, requisito o responsabilidad de la clase. Por lo tanto, las siguientes recomendaciones son equivalentes: (1) una clase debe tener una única responsabilidad; (2) una clase debe implementar un único interés; (3) una clase debe ser cohesiva.

**Ejemplos:**

- La discusión anterior nos dice que las clases deben ser cohesivas, sin embargo, el concepto se adapta también a métodos y funciones. Por ejemplo, suponga una función como la siguiente: `float sin_or_cos(double x, int op) {
 if (op == 1)
 "calcula y retorna seno de x"
 else
 "calcula y retorna coseno de x"
}
` Esta función - que consiste en un ejemplo extremo y, que en la práctica seria poco común - presenta un problema serio de cohesión porque realiza dos cosas: calcula el seno o coseno de su argumento. Lo recomendable seria crear funciones separadas para cada una de estas tareas.

- Suponga ahora la siguiente clase: `class Stack<T> {
 boolean empty() { ... }
 T pop() { ... }
 push (T) { ... }
 int size() { ... }
}
` Se trata de una clase cohesiva, porque todos lo métodos implementan operaciones importantes en una estructura de datos del tipo Pila.

#### Acoplamiento

El acoplamiento es la fuerza de la conexión entre dos clases. Aunque pueda parecer simple, el concepto tiene algunas matices, las cuales derivan de la existencia de dos tipos de acoplamiento entre clases: acoplamiento aceptable y acoplamiento no aceptable. Decimos que existe un acoplamiento aceptable de una clase A a una clase B cuando:

1. La clase A usa solo métodos públicos de la clase B.

2. La interfaz proporcionada por B es estable desde el punto de vista sintáctico y semántico. Es decir, las firmas de los métodos públicos de B no cambian con frecuencia; y lo mismo ocurre con el comportamiento externo de dichos métodos. Por eso, son raros los cambios en B que tendrán un impacto en la clase A.

Por otro lado, existe un acoplamiento no aceptable de una clase A a una clase B cuando los cambios en B pueden impactar fácilmente a A. Esto ocurre principalmente en las siguientes situaciones:

1. Cuando la clase A realiza un acceso directo a un archivo o base de datos de la clase B.

2. Cuando las clases A y B comparten una variable o estructura de datos global. Por ejemplo, la clase B altera el valor de una variable global que la clase A usa en su código.

3. Cuando la interfaz de la clase B no es estable. Por ejemplo, los métodos públicos de B se renombran con frecuencia.

En esencia, lo que caracteriza el acoplamiento no aceptable es el hecho de que la dependencia entre las clases no está mediada por una interfaz estable. Por ejemplo, cuando una clase altera el valor de una variable global, no es consciente del impacto de ese cambio en otras partes del sistema. Por otro lado, cuando una clase altera su interfaz, es consciente de que eso tendrá un impacto en los clientes, pues la función de una interfaz es precisamente anunciar los servicios que una clase ofrece al resto del sistema.

En resumen: el acoplamiento puede ser de gran utilidad, especialmente cuando ocurre con la interfaz de una clase estable que presta un servicio relevante para la clase de origen. Sin embargo, el acoplamiento no aceptable debe evitarse, ya que es un acoplamiento no mediado por interfaces. Los cambios en la clase de destino del acoplamiento pueden propagarse fácilmente a la clase de origen.

Frecuentemente, las recomendaciones sobre acoplamiento y cohesión se reúnen en una única recomendación:

> Maximice la cohesión de las clases o minimice el acoplamiento entre ellas

De hecho, si una clase depende de muchas otras clases, por ejemplo, de decenas de clases, puede estar asumiendo demasiadas responsabilidades en forma de funcionalidades no cohesivas. Recuerda que una clase debe tener una única responsabilidad (o un único motivo para ser modificada). Por otro lado, debemos tener cuidado con el significado del verbo minimizar. El objetivo no debe ser eliminar completamente el acoplamiento de una clase con otras clases, ya que es natural que una clase necesite de otras clases, especialmente de aquellas que implementan servicios básicos, como estructuras de datos, entrada/salida, etc.

- Recuerde la clase `Estacionamiento` , usada anteriormente, la cual posee un atributo que es una `Hashtable` . Entonces, diremos que `Estacionamiento` está acoplada a `Hashtable` . Sin embargo, de acuerdo a la clasificación dada, se trata de un acoplamiento aceptable, es decir, no hay motivo de preocupación por los siguientes motivos:

  - `Estacionamiento` solo es usa los métodos públicos de `Hashtable` .

  - La interfaz de `Hashtable` es estable, ya que esta es parte del paquete oficial de estructuras de datos de Java. Así, un alteración en la firma de los métodos públicos de `Hashtable` quebraría no solo la clase `Estacionamiento` , sino que también millones de otras clases de diversos sistemas en Java al rededor del mundo.

- Suponga el siguiente trecho de código, en el cual existen un archivo compartido por dos clases, `A` y `B` , mantenidas por desarrolladores distintos. El método `B.g()` guarda un entero en el archivo, que es leído por `A.f()` . Esta forma de comunicación origina un acoplamiento no aceptable entre las clases. Por ejemplo, el desarrollador que implementa `B` no puede saber que el archivo es leído por `A` . Así, el puede decidir cambiar el formato del archivo por cuenta propia, sin comunicar al desarrollador de la clase `A` .

```java
class A {
  private void f() {
    int total; ...
    File arch = File.open("arch1.db");
    total = arch.readInt();
    ...
  }
}
```

```java
class B {
  private void g() {
    int total;
    // calcula valor total
    File arch = File.open("arch1.db");
    arch.writeInt(total);
    ...
    arch.close();
  }
```

En el ejemplo también existe un acoplamiento entre `B` y `File`. Sin embargo, este es un acoplamiento aceptable, porque `B` realmente necesita persistir sus datos. Entonces, para conseguir esto, nada mejor que usar una clase de la biblioteca de entrada y salida del lenguaje de programación. Una solución mejor para el acomplamiento entre las clases `A` y `B` de este ejemplo se muestra a continuación:

```java
class A {

  private void f(B b) {
    int total;
    total = b.getTotal();
    ...
  }
```

```java
class B {

  int total;

  public int getTotal() {
    return total;
  }

  private void g() {
    // calcula valor total
    File arch = File.open("arch1");
    arch.writeInt(total);
    ...
  }
}
```

En esta nueva versión, la dependencia entre `A` y `B` se hace explícita. Ahora, `B` tiene un método público que devuelve el valor total. Y la clase `A` tiene una dependencia de la clase `B` a través de un parámetro del método `f`. Este parámetro se usa para solicitar explícitamente el valor total llamando al método `getTotal()`. Como este método fue declarado público en `B`, se espera que el desarrollador de esta clase se esfuerce por no alterar su firma. Por lo tanto, en esta nueva versión, decimos que, aunque existe una dependencia de `A` hacia `B`, el acoplamiento creado por ella es aceptable. Es decir, no es un acoplamiento que genere preocupaciones.

Aún en relación con el ejemplo anterior, es interesante mencionar que, en la primera versión, el código de `A` no declara ninguna variable o atributo del tipo `B`. Y, aun así, tenemos un acoplamiento no aceptable entre las clases. En la segunda versión, ocurre lo contrario, ya que el método `A.f()` declara un parámetro del tipo `B`. Aun así, el acoplamiento entre las clases es de mejor calidad, ya que es más fácil estudiar y mantener el código de `A` sin conocer los detalles de `B`.

Algunos autores utilizan también los términos acoplamiento estructural y acoplamiento evolutivo (o lógico) con el siguiente significado:

1. **Acoplamiento estructural** entre `A` y `B` ocurre cuando una clase `A` tiene una referencia explícita en su código a una clase `B`. Por ejemplo, el acoplamiento entre `Estacionamiento` y `Hashtable` es estructural.

2. **Acoplamiento evolutivo (o lógico)** entre `A` y `B` ocurre cuando los cambios en la clase `B` tienden a propagarse a la clase `A`. En el ejemplo mencionado, en el que la clase `A` depende de un entero almacenado en un archivo interno de `B`, no existe acoplamiento estructural entre `A` y `B`, ya que `A` no declara ninguna variable del tipo `B`, pero existe acoplamiento evolutivo. Por ejemplo, los cambios en el formato del archivo creado por `B` tendrán un impacto en `A`.

El acoplamiento estructural puede ser aceptable o no aceptable, dependiendo de la estabilidad de la interfaz de la clase de destino. El acoplamiento evolutivo, especialmente cuando cualquier cambio en `B` se propaga a la clase de origen `A`, representa un acoplamiento no aceptable.

Kent Beck, cuando trabajaba en Facebook, creó un glosario de términos relacionados con el diseño de software. En este glosario, acoplamiento se define de la siguiente forma [enlace)](https://engineering.fb.com/2011/09/27/uncategorized/software-design-glossary/):

> Dos elementos están acoplados cuando los cambios en un elemento requieren cambios en otro elemento. El acoplamiento puede dar lugar a una relación muy sutil entre clases, como observamos frecuentemente en Facebook. Ciertos eventos que interrumpen el funcionamiento de una parte del sistema suelen ser causados por pequeños fragmentos de acoplamiento que no se esperaban; por ejemplo, cambios en la configuración del sistema `A` causan un tiempo de espera en el sistema `B`, lo que provoca una sobrecarga en el sistema `C`.

La definición de acoplamiento propuesta por Beck — cuando los cambios en un elemento requieren cambios en otro elemento — corresponde a la definición de acoplamiento evolutivo. Es decir, parece que Beck no se preocupa por el acoplamiento aceptable (es decir, estructural y estable) entre dos clases; ya que, de hecho, no debería ser motivo de preocupación.

El comentario también deja claro que el acoplamiento puede ser indirecto. Es decir, los cambios en A pueden propagarse a `B`, y luego alcanzar a `C`. En ese caso, `C` está acoplado a `A`, pero de forma indirecta.

**Mundo Real:** Un ejemplo de problema real causado por acoplamiento indirecto se conoció como el episodio de left-pad. En 2016, una disputa de derechos de autor motivó a un desarrollador a eliminar una de sus bibliotecas del repositorio npm, muy utilizado para almacenar y distribuir bibliotecas de node.js/JavaScript. La biblioteca eliminada — llamada left-pad — tenía una única función de JavaScript, llamada leftPad, con solo 11 líneas de código. Esta función rellenaba una cadena de caracteres con espacios a la izquierda. Por ejemplo, `leftPad('foo', 5)` devolvería `' foo`’, es decir, `'foo`’ con dos espacios a la izquierda.

Miles de sistemas web dependían de esta función trivial, pero la dependencia ocurría de manera indirecta. Los sistemas usaban npm para descargar dinámicamente el código JavaScript de una biblioteca B1, que a su vez dependía de una biblioteca B2 cuyo código también estaba en npm, y así sucesivamente, hasta alcanzar una biblioteca Bn que dependía de left-pad. Como resultado, todos los sistemas que dependían de left-pad — de forma directa o indirecta — quedaron fuera de servicio durante algunas horas, hasta que la biblioteca se volvió a insertar en npm. En resumen, los sistemas se vieron afectados por un problema en una biblioteca trivial, y no tenían la menor idea de que estaban acoplados a ella.

### Principios de Diseño

Los principios de diseño son recomendaciones más concretas que los desarrolladores de software deben seguir para cumplir con las propiedades de diseño. Así, las propiedades de diseño pueden verse como recomendaciones aún genéricas (o tácticas), mientras que los principios ahora están en un nivel operativo.

Estudiaremos los siete principios de diseño enumerados en la siguiente tabla. La tabla también muestra las propiedades de diseño que se contemplan al seguir cada uno de estos principios.

| Principios de Diseño | Propiedades de Diseño |
| --- | --- |
| [Preferir Composición sobre Herencia](/blog/composition-hierarchy-is/) | Acoplamiento |
| [Demeter](/blog/demeter-is/) | Ocultamiento de la Información |
| **S** - [Principio de Responsabilidad Única](/blog/single-responsibility-is/) | Cohesión |
| **O** - [Abierto/Cerrado](/blog/open-closed-is/) | Extensibilidad |
| **L** - [Sustitución de Liskov](/blog/liskov-is/) | Extensibilidad |
| **I** - [Segregación de Interfaces](/blog/interface-segregation-is/) | Cohesión |
| **D** - [Inversión de Dependencias](/blog/dependency-inversion-is/) | Acoplamiento |

Cinco de los principios que vamos a estudiar son conocidos como los Principios SOLID, un acrónimo acuñado por Robert Martin y Michael Feathers [enlace](https://dl.acm.org/doi/book/10.5555/3175742). Este acrónimo deriva de la letra inicial de cada principio en inglés:

- **S** ingle Responsibility Principle (Principio de Responsabilidad Única)

- **O** pen/Closed Principle (Principio Abierto/Cerrado)

- **L** iskov Substitution Principle (Principio de Sustitución de Liskov)

- **I** nterface Segregation Principle (Principio de Segregación de Interfaces)

- **D** ependency Inversion Principle (Principio de Inversión de Dependencias)

Los principios de diseño que vamos a estudiar tienen un punto en común: no solo buscan resolver un problema, sino también asegurar que la solución encontrada pueda mantenerse y evolucionar con éxito en el futuro. Los mayores problemas con los proyectos de software suelen ocurrir después de la implementación, cuando el sistema necesita ser mantenido. Normalmente, existe una tendencia a que este mantenimiento se vuelva gradualmente más lento, costoso y arriesgado. Por lo tanto, los principios de diseño que estudiaremos intentan reducir o posponer esta continua degradación de la calidad interna de los sistemas de software. En resumen, el objetivo no es solo entregar un diseño capaz de resolver un problema, sino también facilitar los mantenimientos futuros. Recuerda que la principal regla sobre los requisitos de software es que cambian con frecuencia. Lo mismo ocurre con las tecnologías de implementación, como bibliotecas y frameworks.

## Patrones de Diseño

Los patrones de diseño están inspirados en una idea propuesta por Christopher Alexander, un arquitecto —de construcciones civiles y no de software— y profesor de la Universidad de Berkeley. En 1977, Alexander publicó un libro llamado A Pattern Language, en el cual documenta diversos patrones para la construcción de ciudades y edificios. Según Alexander:

> Cada patrón describe un problema que siempre ocurre en nuestro contexto y una solución para él, de manera que podamos utilizarla un millón de veces.

En 1995, Erich Gamma, Richard Helm, Ralph Johnson y John Vlissides publicaron un libro adaptando las ideas de Alexander al mundo del desarrollo de software ([enlace](https://dl.acm.org/doi/book/10.5555/186897)). En lugar de proponer un catálogo de soluciones para el diseño de ciudades y edificios, propusieron un catálogo con soluciones para resolver problemas recurrentes en el diseño de software. A estas soluciones propuestas en el libro les dieron el nombre de Patrones de Diseño. Ellos definen los patrones de diseño de la siguiente manera:

> Los patrones de diseño describen objetos y clases que se relacionan para resolver un problema de diseño genérico en un contexto particular.

Así, para entender los patrones propuestos por la Gang of Four —nombre con el que se conocen los autores y también el libro de patrones de diseño— necesitamos entender: (1) el problema que el patrón pretende resolver; (2) el contexto en el que ocurre este problema; (3) la solución propuesta. En esta wiki, se describen algunos patrones de diseño, siempre con enfoque en estos elementos: contexto, problema y solución. También se muestran varios ejemplos de código fuente.

Además de ofrecer soluciones listas para problemas de diseño, los patrones de diseño se han convertido en un vocabulario ampliamente adoptado por los desarrolladores de software. Así, es común escuchar a desarrolladores decir que usaron una fábrica para resolver un cierto problema, mientras que un segundo problema fue resuelto mediante decoradores. Es decir, simplemente mencionan el nombre del patrón y se sobreentiende que la solución adoptada ya está clara. De manera similar, el vocabulario de patrones de diseño se utiliza mucho en la documentación de sistemas. Por ejemplo, la figura de la página siguiente muestra la documentación de una de las clases de la biblioteca estándar de Java. Podemos ver que el nombre de la clase termina en Factory —que es uno de los patrones de diseño que estudiaremos en breve. En la descripción de la clase, se vuelve a mencionar que es una fábrica. Por lo tanto, los desarrolladores que conocen este patrón de diseño tendrán más facilidad para entender y usar la clase en cuestión.

*Documentación de una clase Factory de la API de Java.*

Un desarrollador puede beneficiarse del dominio de los patrones de diseño en dos escenarios principales:

- Cuando esté implementando su propio sistema. En este caso, conocer los patrones de diseño puede ayudarlo a adoptar en su sistema una solución de diseño ya probada y validada.

- Cuando esté usando un sistema de terceros, como el paquete de Java que implementa la clase DocumentBuilderFactory de la figura. En este caso, el conocimiento de los patrones de diseño puede ayudarlo a entender el comportamiento y la estructura de la clase que necesita usar.

Es importante entender que los patrones de diseño están dirigidos a la creación de diseños de software flexibles y extensibles. Antes de explicar cada uno de los patrones, presentaremos un contexto y un fragmento de código que funciona y produce un resultado. Sin embargo, no da origen a un diseño flexible. Para dejar clara esta inflexibilidad, presentaremos un escenario de extensión del código mostrado, involucrando la implementación de nuevos requisitos. Luego argumentaremos que esta extensión requerirá cierto esfuerzo, que podría minimizarse si usamos un patrón de diseño.

Los cuatro autores del libro de patrones de diseño sostienen que debemos diseñar un sistema pensando en los cambios que inevitablemente ocurrirán —a esto lo llaman ***design for change***. Como ellos afirman en la frase, si el ***design for change*** no es una preocupación, los desarrolladores corren el riesgo de tener que planear pronto un rediseño profundo de sus sistemas. En el libro sobre patrones de diseño, se proponen 23 patrones, divididos en las siguientes tres categorías (los patrones que estudiaremos están linkeados):

- **Creacionales** : patrones que proponen soluciones flexibles para la creación de objetos. [Method Factory](/blog/pdd-is-1/) .

- **Estructurales** : patrones que proponen soluciones flexibles para la composición de clases y objetos. [Adapter](/blog/pdd-is-5/) .

- **Comportamentales** : patrones que proponen soluciones flexibles para la interacción y división de responsabilidades entre clases y objetos. [Strategy](/blog/pdd-is-8/) , [Observer](/blog/pdd-is-9/) .

[← Volver](../ingsoft.md)
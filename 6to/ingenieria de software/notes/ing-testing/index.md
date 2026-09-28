# Pruebas de Software

_Original: https://www.danielsanmartin.cl/blog/ing-testing/_


> El código sin pruebas es código deficiente. – Michael Feathers

### Introducción

El software es una de las construcciones humanas más complejas, como fue discutido en la introducción del material. Por lo tanto, es comprensible que sistemas de software estén sujetos a los más variados tipos de
errores y inconsistencias. Para evitar que tales errores lleguen a los usuarios finales y causen perjuicios de valor incalculable, es fundamental introducir actividades de prueba en proyectos de desarrollo de
software. De hecho, las pruebas son una de las prácticas de programación más valoradas hoy en día, en cualquier tipo de software. También es una de las prácticas que sufrieron más transformaciones en los últimos años.
Cuando el desarrollo seguía el modelo en cascada, las pruebas se realizaban en una fase separada, después de las fases de levantamiento de requisitos, análisis, diseño y codificación.

Además, existía un equipo separado de pruebas, responsable de verificar si la implementación cumplía los requisitos del sistema. Para comprobar esto, frecuentemente las pruebas eran manuales, es decir, una persona usaba el sistema, ingresaba datos de entrada y verificaba si las salidas eran las esperadas. Así, el objetivo de tales pruebas era solo detectar bugs, antes de que el sistema entrara en producción.
Con métodos ágiles, la práctica de pruebas de software fue profundamente reformulada, como se explica la continuación:

- Gran parte de las pruebas pasó la ser automatizada, es decir, además de implementar las clases de un sistema, los desarrolladores pasaron la implementar también código para probar tales clases. Así, los programas se volvieron **autoevaluables.**

- Las pruebas ya no se implementan después de que todas las clases de un sistema estén listas. Muchas veces, ellos son implementadas incluso antes de esas clases.

- No existen grandes equipos de pruebas — el estos son responsables de pruebas específicas. En su lugar, el desarrollador que implementa una clase también debe implementar los sus pruebas.

- Pruebas no son más un instrumento exclusivo para la detección de bugs. Claro, eso continúa siendo importante, pero las pruebas adquirieron nuevas funciones, como verificar se una clase continuará
funcionando después de que se corrija un bug en otra parte del sistema. Y pruebas son también usadas como documentación para el código de producción.

Estas transformaciones convirtieron las pruebas una de las prácticas de programación más valoradas en desarrollo moderno de software. En este contexto que debe entenderse la frase de Michael Feathers que abre ese material: si un código en el está acompañado de pruebas, él pode ser considerado de baja calidad o incluso un código legado. En este material, el foco recae en las pruebas automatizadas, pues las pruebas manuales requieren mucho trabajo, son lentos y costosos. Peor aún, ellos deben repetirse cada vez que el sistema sufrir una modificación. Una forma interesante de clasificar las pruebas automatizadas é por medio de una pirámide de pruebas, propuesta originalmente por Mike Cohn (enlace). Como muestra la siguiente figura, esa pirámide divide las pruebas de acuerdo con su granularidad.

#### Pirámide de pruebas

*Pirámide de pruebas*

Particularmente, las pruebas se dividen en tres grupos. Las pruebas unitarias verifican automáticamente pequeñas partes de un código, normalmente una sola clase (véase también por las figuras de la siguiente página). Estas forman la base de la pirámide, es decir, la mayor parte de las pruebas estão en esa categoría. Las pruebas unitarias son simple, más fáciles de implementar y se ejecutan rápidamente. En el siguiente nivel, hay pruebas de integración o pruebas de servicios, que verifican una funcionalidad o transacción completa de un sistema. Por lo tanto, son pruebas que usan diversas clases, de paquetes distintos, y también pueden probar componentes externos, como bases de datos. Pruebas de integración requieren más esfuerzo para ser implementadas y ejecutan de forma más lenta. Finalmente, en la superior de la pirámide, há las pruebas de sistema, también llamadas de pruebas de interfaz de usuario. Estas simulan, de la forma más fiel posible, una sesión de uso del sistema por un usuario real. Como son pruebas de extremo la extremo (end-to-end), ellos son más costosas, más lentas y menos numerosas. Pruebas de interfaz también suelen ser frágiles, es decir, mínimas alteraciones en los componentes de la interfaz pueden requerir modificaciones nesses pruebas.

*Test de unidad*

*Test de integración*

*Test de sistema*

Una recomendación general es que estos tres tipos de pruebas se implementen en la siguiente proporción: 70% como pruebas unitarias, 20% como pruebas de servicios y 10% como pruebas de sistema. En este material, se estudiarán los tres tipos de pruebas de la pirámide de pruebas. El espacio dedicado a cada tipo de prueba también será coherente con su lugar en la pirámide. Es decir, se tratará más sobre pruebas unitarias que sobre pruebas de sistema, pues las primeras son mucho más comunes.

Antes de comenzar propiamente, es importante recordar algunos conceptos introductorios. Se dice que un código posee un defecto —o, de manera más informal, un *bug*— cuando no está de acuerdo con su especificación. Si se ejecuta un código con defecto y este lleva al programa a presentar un resultado o comportamiento incorrecto, se dice que ocurrió una falla (*failure*, en inglés).

### Pruebas Unitarias

Las **pruebas unitarias** son pruebas automatizadas de pequeñas unidades de código, normalmente clases, las cuales se prueban de forma aislada respecto del resto del sistema. Una prueba unitaria es un programa que llama a los métodos de una clase y verifica si estos retornan los resultados esperados. Así, cuando se usan pruebas unitarias, el código de un sistema puede dividirse en dos grupos: un conjunto de clases —que implementan los requisitos del sistema— y un conjunto de pruebas, como se ilustra en la siguiente figura.

*Correspondencia entre clases y tests*

La figura muestra un sistema con n clases y m pruebas. Como puede observarse, no existe una correspondencia de 1 para 1 entre clases y pruebas. Por ejemplo, una clase pode tener más de un prueba. Es el caso de la clase C1, que es probada por T1 y T2. Provavelmente, eso ocorre porque C1 é una clase importante, que necesita ser probada en diferentes contextos. Por otro lado, C2 no posee pruebas, o porque los desarrolladores olvidaron de implementar o porque ella é una clase menos importante.

Pruebas de unidad se implementan usando frameworks construidos específicamente para ese fin. Los más conocidos son llamados frameworks xUnit, ddonde x designa la lenguaje usado en la implementación de las pruebas. El primero de estos frameworks — llamado sUnit — fue implementado por Kent Beck la fines de la década de 1980 para Smalltalk. En este material, la pruebas serán
implementadas en Java, usando el JUnit. LA primera versión del JUnit fue implementada en conjunto por Kent Beck y Erich Gamma, en 1997, durante un viaje en avión entre la Suíça y los EUA. Hoy existen versiones de frameworks xUnit para los principales lenguajes. Por lo tanto, una de las ventajas de pruebas unitarias é que los desarrolladores en el necesitan aprender una nueva lenguaje de programación, pues las pruebas son implementadas en la mismo lenguaje del sistema que pretende-se probar. Para explicar los conceptos de pruebas unitarias, Se usará una clase Stack:

```java
import java.util.ArrayList;
import java.util.EmptyStackException;

public class Stack<T> {
  private ArrayList<T> elements = new ArrayList<T>();
  private int size = 0;
  public int size() {
    return size;


  public boolean isEmpty() {
    return (size == 0);

  public void push(T elem) {

    elements.add(elem);
    size++;
  }

  public T pop() throws EmptyStackException {
    if (isEmpty())
      throw new EmptyStackException();

    T elem = elements.remove(size-1);
    size--;

    return elem;
  }
}
```

JUnit permite implementar clases que probarán, de forma automática, clases de la aplicación, como la clase `Stack`. Por convención, las clases de prueba tienen el mismo nombre que las clases probadas, pero con el sufijo `Test`. Por lo tanto, la primera clase de prueba se llamará `StackTest`. Por su parte, los métodos de prueba comienzan con el prefijo `test` y deben cumplir obligatoriamente las siguientes condiciones: (1) ser públicos, pues serán llamados por JUnit; (2) no poseer parámetros; y (3) tener la anotación `@Test`, la cual identifica los métodos que deberán ejecutarse durante una prueba. A continuación, se presenta la primera prueba unitaria:

```java
import org.junit.Test;
import static org.junit.Assert.assertTrue;
public class StackTest {
  @Test
  public void testEmptyStack() {
    Stack<Integer> stack = new Stack<>();

    boolean empty = stack.isEmpty();
    assertTrue(empty);
  }
}
```

En esta primera versión, la clase `StackTest` posee un único método de prueba, público, anotado con `@Test` y llamado `testEmptyStack()`. Este método solo crea una pila y verifica si está vacía.

Los métodos de prueba tienen la siguiente estructura:

- Primero, se crea el contexto de la prueba, también llamado *fixture*. Para ello, deben instanciarse los objetos que se pretende probar y, si corresponde, inicializarlos. En el primer ejemplo, esta parte de la prueba incluye solo la creación de una pila llamada `stack`.

- Luego, la prueba debe llamar a uno de los métodos de la clase que está siendo probada. En el ejemplo, se llama al método `isEmpty()` y se almacena su resultado en una variable local.

- Finalmente, debe comprobarse si el resultado del método es el esperado. Para ello, debe usarse un comando llamado `assert`. En realidad, JUnit ofrece diversas variaciones de `assert`, pero todas tienen el mismo objetivo: comprobar si un determinado resultado es igual a un valor esperado. En el ejemplo, se usa `assertTrue`, que verifica si el valor pasado como parámetro es verdadero.

Los IDE ofrecen opciones para ejecutar solo las pruebas de un sistema, por ejemplo, mediante una opción de menú llamada “Run as Test”. Es decir, si el desarrollador selecciona “Run”, ejecutará su programa normalmente, comenzando por el método `main`. Sin embargo, si opta por la opción “Run as Test”, no ejecutará el programa completo, sino solo sus pruebas unitarias.

La siguiente figura muestra el resultado de la ejecución de la primera prueba. El resultado se muestra en la propia IDE, y la barra verde informa que todas las pruebas pasaron. También puede observarse que la prueba se ejecuta rápidamente, en 0,025 segundos.

Sin embargo, supóngase que se hubiera cometido un error en la implementación de la clase Stack. Por ejemplo, supóngase que el atributo size fuera inicializado con el valor 1, en vez de cero. En ese caso, la ejecución de las pruebas fallaría, como se muestra mediante la barra roja en la IDE:

El mensaje de error informa que hubo una falla durante la ejecución de testEmptyStack. Falla (failure) es el término usado por el JUnit para indicar pruebas cuyo comando assert en el fue satisfecho. En
una otra ventana de la IDE, puede descubrirse que la aserción responsable por la falla se encuentra en la línea 19 del archivo StackTest.java. Para concluir, se presentará el código completo de la prueba de unidad:

```java
import org.junit.Test;
import org.junit.Before;
import static org.junit.Assert.assertTrue;
import static org.junit.Assert.assertFalse;
import static org.junit.Assert.assertEquals;
public class StackTest {

Stack<Integer> stack;
  @Before
  public void init() {
    stack = new Stack<>();

  }

  @Test
  public void testEmptyStack() {

    assertTrue(stack.isEmpty());
  }

  @Test
  public void testNotEmptyStack() {

    stack.push(10);
    assertFalse(stack.isEmpty());
  }

  @Test
  public void testSizeStack() {

    stack.push(10);
    stack.push(20);
    stack.push(30);

    int size = stack.size();

    assertEquals(3,size);
  }

  @Test
  public void testPushPopStack() {

    stack.push(10);
    stack.push(20);
    stack.push(30);

    int result = stack.pop();

    result = stack.pop();
    assertEquals(20,result);
  }

  @Test(expected = java.util.EmptyStackException.class)
  public void testEmptyStackException() {

    stack.push(10);

    int result = stack.pop();

    result = stack.pop();
  }
}
```

La clase `StackTest` tiene cinco métodos de prueba, todos con anotaciones `@Test`. Además, existe un método llamado `init()`, con la anotación `@Before`. Este método es ejecutado por JUnit antes de cualquier método de prueba. JUnit funciona del siguiente modo: para cada clase de prueba, llama a cada uno de sus métodos anotados con `@Test`. Cada método se ejecuta en una instancia diferente de la clase de prueba. Es decir, antes de llamar a un método `@Test`, JUnit instancia un objeto de la clase de prueba. Si esa clase tiene un método anotado con `@Before`, este se ejecuta antes del método `@Test`. En el ejemplo, se usa un método `@Before` para crear una instancia de `Stack`, la cual es utilizada después por los métodos `@Test`. Así, se evita repetir ese código de instanciación en cada prueba. Para que quede un poco más claro, a continuación se presenta el algoritmo usado por JUnit para ejecutar las pruebas de un programa:

```java
para cada clase de prueba TC
  para cada método m de TC con anotación @Test
    el = new TC();       // instancia objeto de prueba
    si TC posee un método b con anotación @Before
         entonces el.b();   // llama al método @Before
    el.m();              // llama al método @Test
```

Volviendo a la clase `StackTest`, otro método interesante es aquel que prueba la situación en la cual la ejecución de `pop()` lanza una `EmptyStackException`.

Obsérvese que ese método —el último de la prueba— no posee `assert`. El motivo es que un `assert` sería código muerto en su implementación. La llamada a `pop()` sobre una pila vacía terminaría la ejecución del método con una excepción `EmptyStackException`. Es decir, el `assert` no se ejecutaría.

Por eso, la anotación `@Test` tiene un atributo especial que sirve para especificar la excepción que debe ser lanzada por el método de prueba. En resumen, `testEmptyStackException` pasará si su ejecución lanza una `EmptyStackException`. En caso contrario, fallará.

**Aviso**: El framework JUnit posee varias versiones.

### Definiciones

Antes de avanzar, se presentarán algunas definiciones:

- **Prueba**: método que implementa una prueba. El nombre deriva de la anotación `@Test`. También se denomina **método de prueba** (*test method*).

- **Fixture**: estado del sistema que será probado por uno o más métodos de prueba, incluyendo datos, objetos, entre otros elementos. El término se reutiliza de la industria manufacturera, donde *fixture* designa un equipo que “fija” una pieza que se pretende construir. En el contexto de las pruebas unitarias, la función de un *fixture* es “fijar” el estado, es decir, los datos y objetos ejercitados durante la prueba.

- **Caso de prueba** (*Test Case*): clase que contiene los métodos de prueba. El nombre tiene su origen en las primeras versiones de JUnit. En esas versiones, los métodos de prueba eran implementados en clases que heredaban de una clase llamada `TestCase`.

- **Suite de pruebas** (*Test Suite*): conjunto de casos de prueba que son ejecutados por el framework de pruebas unitarias, que en este caso es JUnit.

- **Sistema bajo prueba** (*System Under Test*, SUT): sistema que está siendo probado. Es un nombre genérico, usado también en otros tipos de pruebas, no necesariamente unitarias. A veces, también se usa el término **código de producción**, es decir, código que será ejecutado por los clientes del sistema.

### ¿Cuando Escribir Pruebas Unitarias?

Existen dos respuestas principales para esta pregunta. Primero, pueden escribirse las pruebas después de implementar una pequeña funcionalidad. Por ejemplo, se pueden implementar algunos métodos y, luego, sus pruebas, las cuales deben pasar. Es decir, se puede programar un poco y escribir pruebas; programar un poco más y escribir nuevas pruebas, y así sucesivamente.

Alternativamente, pueden escribirse las pruebas primero, antes de cualquier código de producción. Al inicio, esas pruebas no pasarán, pues eso solo ocurrirá después de que el código bajo prueba sea implementado. En otras palabras, se comienza con un código que solo compila y cuyas pruebas, por lo tanto, fallan. Luego, se implementa el código de producción y se prueba nuevamente. Ahora, las pruebas deberían pasar. Este estilo de desarrollo se llama **Test-Driven Development** y será discutido con más detalle en la sección correspondiente.

Sin embargo, existen dos respuestas complementarias a la cuestión sobre cuándo deben escribirse las pruebas. Por ejemplo, cuando un usuario reporta un *bug*, se puede comenzar su análisis escribiendo una prueba que reproduzca el *bug* y que, por lo tanto, falle. En el paso siguiente, debe corregirse el *bug*. Si la corrección tiene éxito, la prueba pasará y se obtendrá una prueba más para la suite de pruebas.

También se pueden escribir pruebas cuando se esté depurando un fragmento de código. Por ejemplo, debe evitarse escribir un `System.out.println` para probar manualmente el resultado de un método. En vez de eso, se recomienda escribir un método de prueba. Cuando se usa un comando `println`, este suele ser removido en algún momento. Una prueba, en cambio, tiene la ventaja de contribuir con un nuevo caso a la suite de pruebas.

Aún respecto de la pregunta principal de esta sección, lo que no se recomienda es dejar la implementación de todas las pruebas para después de que el sistema esté listo, tal como ocurría, por ejemplo, en el desarrollo en cascada (*Waterfall*). Si se deja la escritura de las pruebas para el final, estas pueden ser construidas de forma apresurada y con baja calidad. También puede ocurrir que ni siquiera sean implementadas, pues el sistema ya estará funcionando y nuevas prioridades pueden haber sido asignadas al equipo de desarrollo.

Finalmente, no es recomendable que las pruebas sean implementadas por otro equipo o incluso por otra empresa de desarrollo. En su lugar, se recomienda que el desarrollador de una clase sea también responsable de la implementación de sus pruebas unitarias.

### Beneficios

El principal beneficio de las pruebas unitarias es encontrar *bugs* durante la fase de desarrollo y antes de que el código entre en producción, cuando los costos de corrección y los perjuicios pueden ser mayores. Por lo tanto, si un sistema de software cuenta con buenas pruebas, es menos probable que los usuarios finales sean sorprendidos por *bugs*.

Sin embargo, existen otros dos beneficios que también son muy importantes. Primero, las pruebas unitarias funcionan como una red de protección contra regresiones en el código. Se dice que ocurre una regresión cuando una modificación realizada en el código de un sistema —ya sea para corregir un *bug*, implementar una nueva funcionalidad o realizar una refactorización— termina introduciendo un *bug* u otro problema semejante en el código. Es decir, se dice que el código “regresó” porque algo que funcionaba dejó de funcionar después del cambio realizado.

Las regresiones son menos frecuentes cuando se cuenta con buenas pruebas. Para ello, después de concluir un cambio, el desarrollador debe ejecutar la suite de pruebas. Si el cambio introdujo alguna regresión, existe una buena probabilidad de que esta sea detectada por las pruebas. Es decir, antes del cambio las pruebas estaban pasando, pero después del cambio alguna prueba comenzó a fallar.

Además de usarse para la detección temprana de *bugs* y regresiones en el código, las pruebas unitarias también ayudan en la documentación y especificación del código de producción. De hecho, al observar y analizar las pruebas implementadas en `StackTest`, pueden entenderse diversos aspectos del comportamiento de la clase `Stack`. Por eso, muchas veces, antes de mantener un código con el cual no tiene familiaridad, un desarrollador comienza analizando sus pruebas.

**Mundo real:** Entre las prácticas de desarrollo propuestas originalmente por los métodos ágiles, las pruebas unitarias son probablemente las que alcanzaron mayor impacto y las que se usan de manera más amplia. Hoy, sistemas de software muy diversos, desarrollados por empresas de distintos tamaños, se construyen con el apoyo de pruebas unitarias. A continuación, se destacarán los casos de dos grandes empresas de software: Google y Facebook. Los comentarios fueron extraídos de artículos que documentan el proceso y las prácticas de desarrollo de software de esas empresas:

- “Las pruebas unitarias son fuertemente incentivadas y ampliamente practicadas en Google. Todo código de producción debe tener pruebas unitarias, y la herramienta de revisión de código destaca automáticamente el código enviado sin las pruebas correspondientes. Los revisores de código normalmente exigen que cualquier cambio que agregue nuevas funcionalidades también agregue las respectivas pruebas.” ([enlace](https://arxiv.org/abs/1702.01715))

- “En Facebook, los ingenieros son responsables de las pruebas unitarias de cualquier código nuevo que desarrollen. Además, ese código debe pasar por pruebas de regresión, las cuales son ejecutadas automáticamente como parte de los procesos de *commit* y *push*.” ([enlace](https://ieeexplore.ieee.org/document/6449236))

## Principios y Smells

En esta sección, se agrupará la presentación de principios y antipatrones para implementación de pruebas unitarias. El objetivo es discutir cuestiones importantes para la implementación de pruebas que tengan calidad y que puedan mantenerse y entenderse fácilmente.

### Principios FIRST

Las pruebas unitarias deben satisfacer las siguientes propiedades, cuyas iniciales dan origen a la palabra **FIRST**, en inglés:

**Rápidas** (*Fast*): los desarrolladores deben ejecutar las pruebas unitarias frecuentemente para obtener retroalimentación rápida sobre *bugs* y regresiones en el código. Por eso, es importante que estas sean ejecutadas rápidamente, en cuestión de milisegundos. Si eso no es posible, puede dividirse la suite de pruebas en dos grupos: pruebas que se ejecutan rápidamente y que, por lo tanto, serán llamadas con frecuencia; y pruebas más lentas, que serán ejecutadas, por ejemplo, una vez al día.

**Independientes** (*Independent*): el orden de ejecución de las pruebas unitarias no debe ser importante. Para cualesquiera dos pruebas (T_1) y (T_2), la ejecución de (T_1) seguida de (T_2) debe tener el mismo resultado que la ejecución de (T_2) seguida de (T_1). También puede ocurrir que (T_1) y (T_2) sean ejecutadas de forma concurrente. Para que las pruebas sean independientes, (T_1) no debe alterar ninguna parte del estado global del sistema que después será usada para calcular el resultado de (T_2), y viceversa.

**Determinísticas** (*Repeatable*): las pruebas unitarias deben tener siempre el mismo resultado. Es decir, si una prueba (T) es llamada (n) veces, el resultado debe ser el mismo en las (n) ejecuciones. Por lo tanto, (T) pasa en todas las ejecuciones o falla siempre. Las pruebas con resultados no determinísticos se denominan **pruebas flaky** o **pruebas erráticas**. La concurrencia es una de las principales causas del comportamiento *flaky*. A continuación, se muestra un ejemplo:

```java
@Test
public void exemploTesteFlaky {
  TaskResult resultado;
  MyMath m = new MyMath();

  m.asyncPI(10,resultado);
  Hilo.sleep(1000);
  assertEquals(3.1415926535, resultado.get());
}
```

Esa prueba llama a una función que calcula el valor de (\pi), con cierta precisión y de forma asíncrona; es decir, la función realiza su cálculo en un nuevo hilo, que ella misma crea internamente. En el ejemplo, la precisión requerida es de 10 decimales. La prueba usa un `sleep` para esperar que la función asíncrona termine. Sin embargo, eso vuelve su comportamiento no determinístico: si la función termina antes de 1000 milisegundos, la prueba pasará; pero si la ejecución, por alguna circunstancia particular, demora más, la prueba fallará.

Una posible alternativa sería probar solo la versión síncrona de la función. Si esa versión no existe, podría realizarse una refactorización para extraerla del código de la versión asíncrona. En la sección correspondiente, se discute más sobre cuestiones relativas a la testabilidad del código de producción.

Puede parecer que las pruebas *flaky* son raras, pero un estudio divulgado por Google, basado en sus propias pruebas, reveló que cerca del 16% de ellas están sujetas a resultados no determinísticos. Es decir, esas pruebas pueden fallar no porque se haya introducido un *bug* en el código, sino por causa de eventos no determinísticos, como un hilo que tardó más tiempo en ejecutarse. Las pruebas *flaky* son perjudiciales porque retrasan el desarrollo: los programadores pierden tiempo investigando la falla, para luego descubrir que se trataba de una falsa alarma.

**Autoverificables** (*Self-checking*): el resultado de una prueba unitaria debe ser fácilmente verificable. Para interpretar el resultado de la prueba, el desarrollador no debe, por ejemplo, tener que abrir y analizar un archivo de salida ni proporcionar datos manualmente. En su lugar, el resultado de las pruebas debe ser binario y mostrarse en la IDE, normalmente mediante componentes que aparecen en color verde, para indicar que todas las pruebas pasaron, o en color rojo, para indicar que alguna prueba falló. Adicionalmente, cuando una prueba falla, debe ser posible identificar esa falla de forma breve, incluyendo la ubicación del comando `assert` que falló.

**Escritas lo antes posible** (*Timely*): las pruebas deben escribirse lo antes posible, si es posible incluso antes del código que será probado, como se comentó al final de la sección correspondiente y como se discute con mayor profundidad en la sección sobre desarrollo guiado por pruebas.

### Test Smells

Los **test smells** representan estructuras y características “preocupantes” en el código de pruebas unitarias, las cuales, en principio, deberían evitarse. El nombre es una adaptación, para el contexto de pruebas, del concepto de **code smells** o **bad smells**, que se estudiarán más adelante. Sin embargo, en este material se aprovechará la oportunidad para comentar algunos *smells* que pueden ocurrir en el código de pruebas.

Una **prueba de caja negra** es una prueba larga, compleja y difícil de entender. Como se indicó, las pruebas también deben usarse para ayudar en la documentación del sistema bajo prueba. Por eso, es importante que tengan una lógica clara y de rápida comprensión. Idealmente, una prueba debe, por ejemplo, verificar un único requisito del sistema bajo prueba.

Una **prueba con lógica condicional** incluye código que puede o no ser ejecutado. Es decir, son pruebas con comandos `if` o bucles, mientras que lo ideal es que las pruebas unitarias sean lineales. La lógica condicional en pruebas se considera un *smell* porque perjudica la comprensión de la prueba.

La **duplicación de código en pruebas** ocurre, como su propio nombre sugiere, cuando hay código repetido en diversos métodos de prueba.

Sin embargo, un *test smell* no debe interpretarse literalmente como una situación que debe evitarse a toda costa. En su lugar, debe considerarse como una alerta para los implementadores de la prueba. Al identificar un *test smell*, los desarrolladores deben reflexionar sobre si no es posible tener una prueba más simple y pequeña, con un código lineal y sin duplicación de comandos.

Finalmente, así como ocurre con el código de producción, el código de pruebas debe ser refactorizado frecuentemente para garantizar que permanezca simple, fácil de entender y libre de *test smells*.

### Número de assert por Prueba

Algunos autores (enlace) recomiendan que debe existir como máximo un assert por prueba. Es decir, ellos recomiendan escribir un código como el siguiente.

```java
@Test
public void testEmptyStack() {
```

assertTrue(stack.isEmpty());
}

```java
@Test
public void testNotEmptyStack() {

  stack.push(10);
  assertFalse(stack.isEmpty());
}
```

En otras palabras, en el se recomienda usar de los comandos assert en el mismo método, como en el código la continuación:

```java
@Test
public void testEmptyStack() {

  assertTrue(stack.isEmpty());
  stack.push(10);
  assertFalse(stack.isEmpty());
}
```

El primer ejemplo, que divide la prueba de pila vacía en dos pruebas, tiende a ser más legible y fácil de entender que el segundo, que hace todo en una única prueba. Además, cuando la prueba del primer ejemplo falla, es más simple detectar el motivo de la falla que en el segundo ejemplo, el cual puede fallar por dos motivos.

Sin embargo, no debemos tener una postura dogmática en el uso de esta regla. El motivo es que existen casos en los cuales se justifica tener más de un `assert` por método. Por ejemplo, supóngase que es necesario probar una función `getBook` que retorna un objeto con datos de un material, incluyendo título, autor, año y editorial. En ese caso, se justifica tener cuatro comandos `assert` en la misma prueba, cada uno verificando uno de los campos del objeto retornado por la función, como muestra el siguiente código.

```java
@Test
public void testBookService() {
  BookService bs = new BookService();
  Book b = bs.getBook(1234);

  assertEquals("Engenharia Software Moderna", b.getTitle());
  assertEquals("", b.getAuthor());
  assertEquals("2020", b.getYear());
  assertEquals("ASERG/DCC/UFMG", b.getPublisher());
}
```

Una segunda excepción es cuando hay un método simple, que puede ser probado por medio de un único assert. Para ilustrar, Se presenta la prueba de la función repeat de la clase Strings de la biblioteca google/guava ([enlace](https://github.com/google/guava/blob/master/guava-tests/test/com/google/common/base/StringsTest.java)):

```java
@Test
public void testRepeat() {
  Cadena input = "20";
  assertEquals("", Strings.repeat(input,0));
  assertEquals("20", Strings.repeat(input,1));
  assertEquals("2020", Strings.repeat(input,2));
  assertEquals("202020", Strings.repeat(input,3));
...
}
```

En esta prueba, hay cuatro comandos `assertEquals`, los quais prueban, respectivamente, el resultado de la repetición de una determinada cadena cero, una, de los y tres veces.

## Cobertura de Pruebas

Cobertura de pruebas es una métrica que ayuda la definir el número de pruebas que se necesita escribir para un programa. Mide el porcentaje de comandos de un programa que son cubiertos por pruebas, es decir:

> cobertura de pruebas = (número de comandos ejecutados por las pruebas) / (total de comandos del programa)

Existen herramientas para calcular la cobertura de pruebas. En la siguiente figura, se presenta un ejemplo de uso de la herramienta que acompaña a la IDE Eclipse. Las líneas con fondo verde —coloreadas automáticamente por esa herramienta— indican las líneas cubiertas por las cinco pruebas implementadas en `StackTest`.

Las únicas líneas que no aparecen coloreadas de verde corresponden a las firmas de los métodos de `Stack` y, por lo tanto, no corresponden a comandos ejecutables. Así, la cobertura de las pruebas del primer ejemplo es de 100%, pues la ejecución de los métodos de prueba resulta en la ejecución de todos los comandos de la clase `Stack`.

Supóngase ahora que no se hubiera implementado `testEmptyStackException`. Es decir, no se probaría el lanzamiento de una excepción por parte del método `pop()` cuando este se llama sobre una pila vacía.

En ese caso, la cobertura de las pruebas caería a 92,9%, como se ilustra a continuación:

En ese caso, la herramienta de cálculo de cobertura de pruebas marcaría las líneas de la clase Stack de la siguiente forma:

Como se indicó, las líneas verdes son aquellas cubiertas por la ejecución de las pruebas. Sin embargo, existe un comando marcado en amarillo. Ese color indica que el comando corresponde a una bifurcación —en este caso, un `if`— y que solo uno de los caminos posibles de esa bifurcación —en este caso, el camino `false`— fue ejercitado por las pruebas unitarias. Finalmente, el lector ya debe haber observado que existe una línea en rojo. Ese color indica líneas que no fueron cubiertas por las pruebas unitarias.

En Java, herramientas de cobertura de pruebas trabajan instrumentando los bytecodes generados pelo compilador del lenguaje. Como mostrado en la figura con las estadísticas de cobertura, el programa anterior, después de compilado, posee 52 instrucciones cubiertas por pruebas unitarias, de un total de 56 instrucciones. Por lo tanto, sua cobertura é 52 / 56 = 92.9%.

### Cual la Cobertura de Pruebas Ideal?

No existe un número mágico ni absoluto para la cobertura de pruebas. La respuesta varía de un diseño a otro, dependiendo de la complejidad de los requisitos, de la criticidad del proyecto, entre otros factores. Sin embargo, en general, no necesita ser 100%, pues siempre existen métodos triviales en un sistema, por ejemplo, *getters* y *setters*. También hay métodos cuya prueba es más desafiante, como métodos de interfaz con el usuario o métodos con comportamiento asíncrono.

Por lo tanto, no se recomienda fijar un valor de cobertura que deba alcanzarse siempre. En vez de eso, debe monitorearse la evolución de los valores de cobertura a lo largo del tiempo, para verificar si los desarrolladores, por ejemplo, están descuidando la escritura de pruebas.

También se recomienda evaluar cuidadosamente los fragmentos no cubiertos por pruebas, para confirmar si no son relevantes o si, por el contrario, son difíciles de probar. Hechas estas consideraciones, los equipos que valoran la escritura de pruebas suelen alcanzar fácilmente valores de cobertura cercanos al 70%. Por otro lado, valores por debajo del 50% tienden a ser preocupantes. Finalmente, incluso cuando se usa TDD, la cobertura de pruebas no suele llegar al 100%, aunque normalmente queda por encima del 90%.

**Mundo real:** En una conferencia de desarrolladores de Google, en 2014, se presentaron algunas estadísticas sobre la cobertura de pruebas de los sistemas de la empresa. En la mediana, los sistemas de Google tenían 78% de cobertura a nivel de comandos. Según se afirmó en la presentación, la recomendación sería alcanzar 85% de cobertura en la mayoría de los sistemas, aunque esa recomendación no estaría “escrita en piedra”; es decir, no tendría que seguirse de forma dogmática.

También se mostró que la cobertura variaba según el lenguaje de programación. La menor cobertura correspondía a los sistemas en C++, con un valor un poco inferior al 60% en el promedio de los proyectos. La mayor fue medida en sistemas implementados en Python, con un valor un poco superior al 80%.

### Otras Definiciones de Cobertura de Pruebas

La definición de métrica de cobertura presentada anteriormente se basó en comandos, pues se trata de su definición más común. Sin embargo, existen definiciones alternativas, tales como la **cobertura de funciones** —porcentaje de funciones que son ejecutadas por una prueba—, la **cobertura de llamadas de funciones** —entre todas las líneas de un programa que llaman funciones, cuántas son, de hecho, ejercitadas por pruebas— y la **cobertura de ramas** (*branches*) —porcentaje de ramas de un programa que son ejecutadas por pruebas—.

Un comando `if` siempre genera dos ramas: una cuando la condición es verdadera y otra cuando la condición es falsa. La cobertura de comandos y la cobertura de ramas también son llamadas **cobertura C0** y **cobertura C1**, respectivamente.

Para ilustrar la diferencia entre ambas, se usará la siguiente clase —primer código— y su prueba unitaria —segundo código—:

```java
public class Math {
  public int abs(int x) {
    if (x < 0) {

      x = -x;
    }
    return x;

  }
}

public class MathTest {
  @Test
  public void testAbs() {
    Math m = new Math();

    assertEquals(1,m.abs(-1));
  }
}
```

Suponiendo una cobertura de comandos, se obtiene una cobertura de 100%. Sin embargo, suponiendo una cobertura de ramas (*branches*), el valor es 50%, pues, entre las dos condiciones posibles del comando `if (x < 0)`, se prueba solo una de ellas: la condición verdadera.

Si se desea tener una cobertura de ramas de 100%, habría que agregar otro comando `assert`, por ejemplo:

```java
assertEquals(1, m.abs(1));
```

Por lo tanto, la cobertura de ramas es más rigurosa que la cobertura de comandos.

## Testabilidad

La **testabilidad** es una medida de cuán fácil es implementar pruebas para un sistema. Como se observó, es importante que las pruebas sigan los principios **FIRST**, que tengan pocos `assert` y que alcancen una alta cobertura. Sin embargo, también es importante que el diseño del código de producción favorezca la implementación de pruebas.

El término en inglés para esto es **design for testability**, es decir, diseño orientado a la testabilidad. En otras palabras, a veces, una parte relevante del esfuerzo para escribir buenas pruebas debe concentrarse en el diseño del sistema bajo prueba y no exactamente en el diseño de las pruebas.

La buena noticia es que el código que sigue las propiedades y principios de diseño discutidos anteriormente —tales como alta cohesión, bajo acoplamiento, responsabilidad única, separación entre presentación y modelo, inversión de dependencias, ley de Demeter, entre otros— tiende a presentar buena testabilidad.

### Ejemplo: Servlet

Un **servlet** es una tecnología de Java para la implementación de páginas web dinámicas. A continuación, se presenta un servlet que calcula el índice de masa corporal de una persona, dados su peso y su altura.

El objetivo es didáctico. Por lo tanto, no se detallará todo el protocolo necesario para la implementación de servlets. Además, la lógica de dominio de este ejemplo es simple, pues consiste en la siguiente fórmula:

[
\frac{\text{peso}}{\text{altura} \times \text{altura}}
]

Sin embargo, supóngase que esa lógica podría ser más compleja. Aun así, la solución que se presentará a continuación seguiría siendo válida.

```java
public class IMCServlet extends HttpServlet {
  public void doGet(HttpServletRequest req,

                    HttpServletResponse res) {
    res.setContentType("text/html");

    PrintWriter out = res.getWriter();
    Cadena peso = req.getParameter("peso");
    Cadena altura = req.getParameter("altura");

      try {

        double p = Double.parseDouble(peso);
        double la = Double.parseDouble(altura);
        double imc = p / (la * la);
        out.println("Índice de Masa Corporal (IMC): "+imc);

      }
      catch (NumberFormatException y) {
        out.println("Datos deben ser numéricos");
      }
  }
}
```

Primero, obsérvese que no es simple escribir una prueba para `IMCServlet`, pues esa clase depende de diversos tipos del paquete de servlets de Java. Por ejemplo, no es trivial instanciar un objeto del tipo `IMCServlet` y después llamar al método `doGet`.

Si se toma ese camino, habría que crear también objetos de los tipos `HttpServletRequest` y `HttpServletResponse`, para pasarlos como parámetros de `doGet`. Sin embargo, esos dos tipos pueden depender de otros tipos, y así sucesivamente. Por lo tanto, la testabilidad de `IMCServlet` es baja.

Una alternativa para probar el ejemplo mostrado sería extraer su lógica de dominio hacia una clase separada, como se hizo en el código que se presenta a continuación. Es decir, la idea consiste en separar la presentación —vía servlet— de la lógica de dominio.

Con esto, se vuelve más fácil probar la clase extraída, llamada `IMCModel`, pues no depende de tipos relacionados con servlets. Por ejemplo, es más fácil instanciar un objeto de la clase `IMCModel` que uno de la clase `IMCServlet`.

Es cierto que, con esta refactorización, no será posible probar el código completo. Sin embargo, es mejor probar la parte de dominio del sistema que dejar el código completamente descubierto de pruebas.

```java
class IMCModel {
  public double calculaIMC(Cadena p1, Cadena a1)

                throws NumberFormatException {

    double p = Double.parseDouble(p1);
    double la = Double.parseDouble(a1);
    return p / (la * la);

  }
}
```

```java
public class IMCServlet extends HttpServlet {
  IMCModel model = new IMCModel();
  public void doGet(HttpServletRequest req,

                    HttpServletResponse res) {
    res.setContentType("text/html");

    PrintWriter out = res.getWriter();
    Cadena peso = req.getParameter("peso");
    Cadena altura = req.getParameter("altura");

    try {

      double imc = model.calculaIMC(peso, altura);
      out.println("Índice de Masa Corporal (IMC): " + imc);
    }
    catch (NumberFormatException y) {
      out.println("Datos deben ser numéricos");
    }
  }
}
```

### Ejemplo: Llamada Asíncrona

El siguiente código muestra la implementación de la función `asyncPI`, que se mencionó en la sección correspondiente al tratar los principios **FIRST** y, específicamente, las pruebas determinísticas.

Como se explicó en esa sección, no es simple probar una función asíncrona, pues su resultado es calculado por un hilo independiente. El ejemplo presentado en la sección correspondiente usaba un `sleep` para esperar a que el resultado estuviera disponible. Sin embargo, el uso de ese comando vuelve la prueba no determinística.

```java
public class MyMath {
  public void asyncPI(int prec, TaskResult task) {
    new Hilo (new Runnable() {
      public void run() {
        double pi = "calcula PI con precisión prec"
        task.setResult(pi);
      }
    }).start();
  }
}
```

A continuación, se presenta una solución para incrementar la testabilidad de esa clase. Primero, se extrae el código que implementa el cálculo de (\pi) hacia una función separada, llamada `syncPI`. Así, solo esa función sería probada mediante una prueba unitaria.

En suma, vale la observación realizada anteriormente: es mejor extraer una función que sea fácil de probar que dejar el código sin pruebas.

```java
public class MyMath {
  public double syncPI(int prec) {
    double pi = "calcula PI con precisión prec"
    return pi;

  }

  public void asyncPI(int prec, TaskResult task) {
    new Hilo (new Runnable() {
      public void run() {
        double pi = syncPI(prec);
        task.setResult(pi);
      }
    }).start();
  }
}
```

## Mocks

Para explicar el papel desempeñado por los *mocks* en las pruebas unitarias, se comenzará con un ejemplo motivador y se discutirá por qué es difícil escribir una prueba unitaria para él. Luego, se introducirá el concepto de *mock* como una posible solución para probar ese ejemplo.

**Aviso:** en este material, inicialmente se usa *mock* como sinónimo de *stub*. Sin embargo, más adelante se incluye una subsección para resaltar que algunos autores establecen una distinción entre estos términos.

**Ejemplo motivador:** para explicar el concepto de *mock*, se partirá de una clase simple para la búsqueda de materiales, cuyo código se muestra a continuación. Esa clase, llamada `BookSearch`, implementa un método `getBook`, que busca los datos de un material en un servicio remoto. Ese servicio, a su vez, implementa la interfaz `BookService`.

Para que el ejemplo sea más realista, supóngase que `BookService` es una API REST o una base de datos. Lo importante es que la búsqueda se realiza en otro sistema, que queda abstraído por la interfaz `BookService`.

Ese servicio retorna su resultado como un documento JSON, es decir, como un documento textual. Así, corresponde al método `getBook` acceder al servicio remoto, obtener la respuesta en formato JSON y crear un objeto de la clase `Book` para almacenar la respuesta.

Para simplificar el ejemplo, no se presenta el código de la clase `Book`, pero esta es solo una clase con datos de materiales y sus respectivos métodos `get`. En realidad, para simplificar un poco más, el ejemplo considera que `Book` posee un único campo, relativo a su título. En un programa real, `Book` tendría otros campos, que también serían tratados en `getBook`.

```java
import org.json.JSONObject;
public class BookSearch {
  BookService rbs;
  public BookSearch(BookService rbs) {

    this.rbs = rbs;
  }

  public Book getBook(int isbn) {
    Cadena json = rbs.search(isbn);
    JSONObject obj = new JSONObject(json);
    Cadena titulo;
    titulo = (Cadena) obj.get("titulo");
    return new Book(titulo);

  }
}

public interfaz BookService {
  Cadena search(int isbn);

}
```

**Problema:** es necesario implementar una prueba unitaria para `BookSearch`. Sin embargo, por definición, una prueba unitaria ejercita un componente pequeño del código, como una única clase. El problema es que, para probar `BookSearch`, se necesita un `BookService`, que es un servicio externo.

Es decir, si no se tiene cuidado, la prueba de `getBook` alcanzará un servicio externo. Esto es malo por dos motivos: (1) el alcance de la prueba será mayor que una única unidad de código; y (2) la prueba será más lenta, pues el servicio externo puede ser una base de datos almacenada en disco o un servicio remoto accedido vía HTTP, o mediante un protocolo similar. Además, debe recordarse que las pruebas unitarias deben ejecutarse rápidamente, como recomiendan los principios **FIRST**.

**Solución:** una solución consiste en crear un objeto que “emule” al objeto real, pero solo para permitir la prueba del programa. Ese tipo de objeto se denomina *mock* o *stub*. En el ejemplo, el *mock* debe implementar la interfaz `BookService` y, por lo tanto, el método `search`. Sin embargo, esa implementación es parcial, pues el *mock* retorna solo los títulos de algunos materiales, sin acceder a servidores remotos ni a bases de datos.

A continuación, se muestra un ejemplo:

```java
import static org.junit.Assert.*;
import org.junit.*;
class BookConst {
  public static Cadena ESM =

          "{ \"titulo\": \"Eng Soft Moderna\" }";

  public static Cadena NULLBOOK =

          "{ \"titulo\": \"NULL\" }";
}
```

```java
class MockBookService implements BookService {
  public Cadena search(int isbn) {
      if (isbn == 1234)
          return BookConst.ESM;
      return BookConst.NULLBOOK;
    }
  }
```

```java
public class BookSearchTest {
  private BookService service;
  @Before
  public void init() {
    service = new MockBookService();

  }

  @Test
  public void testGetBook() {
    BookSearch bs = new BookSearch(service);
    Cadena titulo = bs.getBook(1234).getTitulo();
    assertEquals("Eng Soft Moderna", titulo);
  }
}
```

En este ejemplo, `MockBookService` es una clase usada para crear *mocks* de `BookService`, es decir, objetos que implementan esa interfaz, pero con un comportamiento trivial. En el ejemplo, el objeto *mock*, de nombre `service`, solo retorna datos del material cuyo ISBN es `1234`.

El lector puede entonces preguntarse: ¿cuál es la utilidad de un servicio que busca datos de un único material? La respuesta es que ese *mock* permite implementar una prueba unitaria que no necesita acceder a un servicio remoto, externo y lento.

En el método `testGetBook`, se usa el *mock* para crear un objeto del tipo `BookSearch`. Luego, se llama al método `getBook` para buscar un material y retornar su título. Finalmente, se ejecuta un `assert`. Como la prueba está basada en un `MockBookService`, esta verifica si el título retornado es el del único material “buscado” por tal *mock*.

Sin embargo, tal vez aún quede una pregunta: ¿qué prueba, en realidad, `testGetBook`? En otras palabras, ¿cuál requisito del sistema está siendo probado mediante un objeto *mock* tan simple?

Claramente, en ese caso, no se está probando el acceso al servicio remoto. Como se afirmó, ese es un requisito demasiado “extenso” para ser verificado mediante pruebas unitarias. En su lugar, se está probando si la lógica de instanciar un `Book` a partir de un documento JSON está funcionando.

En una prueba más realista, podrían incluirse más campos en `Book`, además del título. También podrían probarse más materiales, bastando para ello extender la capacidad del *mock*: en vez de retornar siempre el JSON del mismo material, este retornaría datos de más materiales, dependiendo del ISBN.

**Código fuente:** el código del ejemplo de *mock* usado en esta sección está disponible en este enlace.

### Frameworks de Mocks

Los *mocks* son tan comunes en las pruebas unitarias que existen frameworks para facilitar su creación y “programación”, así como la de *stubs*. No se entrará en detalles sobre esos frameworks, pero a continuación se presenta la prueba anterior usando un *mock* instanciado mediante un framework llamado Mockito, muy utilizado cuando se escriben pruebas unitarias en Java que requieren *mocks*.

```java
import org.junit.*;
import static org.junit.Assert.*;
import org.mockito.Mockito;
import static org.mockito.Mockito.when;
import static org.mockito.Matchers.anyInt;

public class BookSearchTest {
  private BookService service;
  @Before
  public void init() {
    service = Mockito.mock(BookService.class);
    when(service.search(anyInt())).
                 thenReturn(BookConst.NULLBOOK);
    when(service.search(1234)).thenReturn(BookConst.ESM);

  }

  @Test
  public void testGetBook() {
    BookSearch bs = new BookSearch(service);
    Cadena titulo = bs.getBook(1234).getTitulo();
    assertEquals("Eng Soft Moderna", titulo);
  }
}
```

Primero, puede observarse que ya no existe una clase `MockBookService`. La principal ventaja de usar un framework como Mockito es exactamente esa: no tener que escribir manualmente clases de *mock*.

En su lugar, un *mock* para `BookService` es creado por el propio framework, usando recursos de reflexión computacional de Java. Para ello, basta usar la función `mock(type)`, como se muestra a continuación:

```java
service = Mockito.mock(BookService.class);
```

Sin embargo, el *mock* `service` todavía está vacío y no posee ningún comportamiento. Entonces, es necesario “enseñarle” a comportarse al menos en algunas situaciones. Específicamente, hay que enseñarle a responder algunas búsquedas de materiales.

Para ello, Mockito ofrece un lenguaje de dominio específico simple, basado en la misma sintaxis de Java. A continuación, se muestra un ejemplo:

```java
when(service.search(anyInt())).thenReturn(BookConst.NULLBOOK);
when(service.search(1234)).thenReturn(BookConst.ESM);
```

Estas dos líneas “programan” el *mock* `service`. Primero, se le indica que retorne `BookConst.NULLBOOK` cuando su método `search` sea llamado con cualquier entero como argumento.

Luego, se abre una excepción a esa regla general: cuando `search` sea llamado con el entero `1234`, debe retornar la cadena JSON con los datos del material `BookConst.ESM`.

**Código fuente:** el código de este ejemplo, usando Mockito, está disponible en este enlace.

### Mocks vs Stubs

Algunos autores, como Gerard Meszaros, hacen una distinción entre *mocks* y *stubs*. Según ellos, los *mocks* no solo verifican el estado del **Sistema Bajo Prueba** (*System Under Test*, SUT), sino también su comportamiento. Si los objetos usados en la prueba verifican solo el estado, entonces deberían llamarse *stubs*.

Sin embargo, en este material no se hará esa distinción, pues se considera que es sutil y que, por lo tanto, los beneficios no compensan el costo de dedicar páginas adicionales a explicar conceptos similares.

No obstante, solo para aclarar un poco más, una prueba comportamental —también llamada **prueba de interacción**— verifica eventos que ocurrieron en el SUT. A continuación, se presenta un ejemplo:

```java
void testBehaviour {
  Mailer m = mock(Mailer.class);
  sut.someBusinessLogic(m);
  verify(m).send(anyString());

}
```

En este ejemplo, el comando `verify` —implementado por Mockito— se parece a un `assert`. Sin embargo, este verifica si ocurrió un evento con el *mock* pasado como argumento. En este caso, se verifica si el método `send` del *mock* fue ejecutado al menos una vez, usando cualquier cadena como argumento.

Según Gerard Meszaros, los *mocks* y los *stubs* son casos especiales de objetos dobles (*test doubles*). El término está inspirado en los dobles de actores en las películas.

Según Meszaros, existen al menos otros dos tipos de objetos dobles:

- **Objetos dummy**: son objetos que se pasan como argumento a un método, pero que no son usados. Se trata, por lo tanto, de una forma de doble usada solo para satisfacer el sistema de tipos del lenguaje.

- **Objetos fake**: son objetos que poseen una implementación más simple que el objeto real. Por ejemplo, un objeto que simula en memoria principal, mediante tablas hash, un objeto de acceso a bases de datos.

### Ejemplo: Servlet

En la sección anterior, Se presenta la prueba de una servlet que calcual Índice de Masa Corporal (IMC) de una persona. Sin embargo, se argumenta que en el se probaría la servlet completa porque ella posee dependencias difíciles de ser recreadas en una prueba. Sin embargo, ahora se sabe que pode-se criar mocks para esas dependencias, es decir, objetos que van la “simular” las dependencias reales, porém respondiendo solo a las llamadas necesarias en la prueba. Primero, se volverá la presentar el código de la servlet que se pretende probar:

```java
public class IMCServlet extends HttpServlet {
  IMCModel model = new IMCModel();
  public void doGet(HttpServletRequest req,

                    HttpServletResponse res) {
    res.setContentType("text/html");

    PrintWriter out = res.getWriter();
    Cadena peso = req.getParameter("peso");
    Cadena altura = req.getParameter("altura");
    double imc = model.calculaIMC(peso,altura);
    out.println("IMC: " + imc);

  }
}
```

A continuación, se presenta la nueva prueba de ese servlet. Esta prueba es una adaptación de un ejemplo disponible en un artículo de Dave Thomas y Andy Hunt.

Primero, puede observarse, en el método `init`, que se crearon *mocks* para objetos de los tipos `HttpServletRequest` y `HttpServletResponse`. Esos *mocks* serán usados como parámetros en la llamada a `doGet`, que se realizará en el método de prueba.

Aún en `init`, se crea un objeto del tipo `StringWriter`, que permite generar salidas en forma de una cadena de texto. Luego, ese objeto es encapsulado por un `PrintWriter`, que es el objeto usado como salida por el servlet. Es decir, se trata de una aplicación del patrón de diseño **Decorator**, que se estudiará más adelante.

Finalmente, se programa el *mock* de respuesta: cuando el servlet solicite un objeto de salida mediante una llamada a `getWriter()`, este debe retornar el objeto `PrintWriter` que acaba de crearse.

En resumen, todo esto se realizó con el objetivo de redirigir la salida del servlet hacia una cadena de texto que pueda ser inspeccionada durante la prueba.

```java
public class IMCServletTest {
  HttpServletRequest req;
  HttpServletResponse res;
  StringWriter sw;
  @Before
  public void init() {
    req = Mockito.mock(HttpServletRequest.class);
    res = Mockito.mock(HttpServletResponse.class);
    sw = new StringWriter();
    PrintWriter pw = new PrintWriter(sw);
    when(res.getWriter()).thenReturn(pw);

  }
  // continuación de IMCServletTest
```

Para concluir, tenemos el método de prueba, mostrado a continuación.

```java
  @Test
  public void testDoGet() {
    when(req.getParameter("peso")).thenReturn("82");
        when(req.getParameter("altura")).thenReturn("1.80");
        new IMCServlet().doGet(req,res);
        assertEquals("IMC: 25.3\n", sw.toString());

  }
}
```

En esta prueba, se comienza programando el *mock* del objeto con los parámetros de entrada del servlet. Cuando el servlet solicite el parámetro `"peso"`, el *mock* retornará `82`; cuando solicite el parámetro `"altura"`, retornará `1.80`.

Hecho esto, la prueba sigue el flujo normal de las pruebas unitarias: se llama al método que se pretende probar, `doGet`, y se verifica si retorna el resultado esperado.

Ese ejemplo también sirve para ilustrar las desventajas del uso de *mocks*. La principal de ellas es que los *mocks* aumentan el acoplamiento entre la prueba y el método probado. Típicamente, en las pruebas unitarias, el método de prueba llama al método probado y verifica su resultado. Por lo tanto, se acopla solo a la firma de ese método. Por eso, la prueba no se “rompe” cuando solo se modifica el código interno del método probado.

Sin embargo, cuando se usan *mocks*, eso deja de ser necesariamente cierto, pues el *mock* puede depender de estructuras internas del método probado, lo que vuelve las pruebas más frágiles. Por ejemplo, supóngase que la salida del servlet cambia a `"Índice de Masa Corporal (IMC): [valor]"`. En ese caso, habrá que recordar actualizar también el `assertEquals` de la prueba unitaria.

Finalmente, no siempre se consiguen crear *mocks* para todos los objetos y métodos. En general, las siguientes construcciones no son fácilmente “mockeables”: clases y métodos `final`, métodos estáticos y constructores.

## 7 Desarrollo Guiado por Pruebas (TDD)

El **Desarrollo Guiado por Pruebas** (*Test-Driven Development*, TDD) es una de las prácticas de programación propuestas por **Extreme Programming** (XP). La idea, al principio, puede parecer extraña, tal vez incluso absurda: dada una prueba unitaria (T) para una clase (C), TDD defiende que (T) debe ser escrita antes que (C). Por eso, TDD también es conocido como **Test-First Development**.

Cuando se escribe primero la prueba, esta fallará. Entonces, en el flujo de trabajo propuesto por TDD, el siguiente paso consiste en escribir el código que hace pasar esa prueba, aunque sea un código trivial. Luego, ese primer código debe ser completado y refinado. Finalmente, si es necesario, debe ser refactorizado para mejorar su diseño, legibilidad y mantenibilidad, así como para ajustarse a principios y patrones de diseño.

TDD fue propuesto con tres objetivos principales en mente:

- TDD ayuda a evitar que los desarrolladores olviden escribir pruebas. Para ello, promueve las pruebas como la primera actividad de cualquier tarea de programación, ya sea corregir un *bug* o implementar una nueva funcionalidad. Al ser la primera actividad, es más difícil que la escritura de pruebas sea dejada para un segundo momento.

- TDD favorece la escritura de código con alta testabilidad. Esa característica es una consecuencia natural de la inversión del flujo de trabajo propuesta por TDD: como el desarrollador sabe que tendrá que escribir primero la prueba (T) y después la clase (C), es natural que desde el inicio planifique (C) de forma que facilite la escritura de su prueba. De hecho, como se mencionó en la sección correspondiente, los sistemas que usan TDD suelen tener una alta cobertura de pruebas, normalmente por encima del 90%.

- TDD es una práctica relacionada no solo con las pruebas, sino también con la mejora del diseño de un sistema. Esto ocurre porque el desarrollador, al comenzar por la escritura de una prueba (T), se coloca en la posición de un usuario de la clase (C). En otras palabras, con TDD, el primer usuario de la clase es su propio desarrollador; recuérdese que (T) es un cliente de (C), pues llama a métodos de (C). Por eso, se espera que el desarrollador simplifique la interfaz de (C), use nombres de identificadores legibles, evite un número excesivo de parámetros, entre otras buenas prácticas.

Cuando se trabaja con TDD, el desarrollador sigue un ciclo compuesto por tres estados, como muestra la siguiente figura.

#### Ciclos de TDD

*Ciclos TDD*

De acuerdo con ese diagrama, la primera meta es llegar al estado rojo, cuando la prueba aún no está pasando. Puede parecer extraño, pero el estado rojo ya es una pequeña victoria: al escribir una prueba que falla, el desarrollador al menos tiene en sus manos una especificación de la clase que necesitará implementar a continuación. Es decir, ya se sabe qué se debe hacer.

Como ya se mencionó, en ese estado es importante que el desarrollador también piense en la interfaz de la clase que tendrá que implementar, colocándose en la posición de un usuario de esta. Finalmente, es importante que entregue el código compilando. Para ello, debe escribir al menos el esqueleto de la clase bajo prueba, es decir, la firma de la clase y de sus métodos.

Luego, la meta es alcanzar el estado verde. Para ello, debe implementarse la funcionalidad completa de la clase bajo prueba; cuando eso ocurra, las pruebas que estaban fallando comenzarán a pasar. Sin embargo, esa implementación puede dividirse en pequeños pasos. Tal vez, en los pasos iniciales, el código funcione de forma parcial, por ejemplo, retornando solo constantes. Esto quedará más claro en el ejemplo que se presentará a continuación.

Finalmente, debe analizarse si existen oportunidades para refactorizar el código de la clase y de la prueba. Cuando se usa TDD, el objetivo no es solo alcanzar el estado verde, en el cual el programa está funcionando. Además, debe verificarse la posibilidad de mejorar la calidad del diseño del código. Por ejemplo, se puede revisar si existe código duplicado, si hay métodos muy largos que puedan dividirse en métodos menores, si algún método puede moverse a una clase diferente, entre otros aspectos.

Terminado el paso de refactorización, puede detenerse el proceso o reiniciarse el ciclo para implementar alguna funcionalidad adicional.

### Ejemplo: Carrito de Compras

Para concluir, se ilustrará una sesión de uso de TDD. Para ello, se usará como ejemplo el sistema de una librería virtual.

En ese sistema, existe una clase `Book`, con los atributos `titulo`, `isbn` y `precio`. También existe la clase `ShoppingCart`, que almacena los materiales que un cliente desea comprar. Esa clase debe implementar métodos para agregar un material al carrito, retornar el precio total de los materiales en el carrito y remover un material del carrito.

A continuación, se presenta la implementación de esos métodos usando TDD.

**Estado rojo:** se comienza definiendo que `ShoppingCart` tendrá un método `add` y un método `getTotal`. Además de decidir el nombre de tales métodos, se definen sus parámetros y se escribe la primera prueba:

```java
@Test
void testAddGetTotal() {
  Book b1 = new Book("book1", 10, "1");
  Book b2 = new Book("book2", 20, "2");
  ShoppingCart cart = new ShoppingCart();

  cart.add(b1);
  cart.add(b2);
  assertEquals(30.0, cart.getTotal());
}
```

Aunque es simple y de fácil comprensión, esa prueba todavía no compila, pues no existe implementación para las clases Book y ShoppingCart. Entonces, hay que proporcionar eso, como mostrado la continuación:

```java
public class Book {

  public Cadena title;
  public double price;
  public Cadena isbn;
  public Book(Cadena title, double price, Cadena isbn) {

    this.title = title;
    this.price = price;
    this.isbn = isbn;
  }
}

public class ShoppingCart {


public ShoppingCart() {}
  public void add(Book b) {}
  public double getTotal() {
    return 0.0;

  }
}
```

La implementación de ambas clases es muy simple. Se implementa solo el mínimo necesario para que el programa y la prueba compilen. Obsérvese, por ejemplo, el método `getTotal` de `ShoppingCart`. En esa implementación, este siempre retorna `0.0`. A pesar de eso, se alcanza el objetivo: hay una prueba compilando, ejecutándose y fallando. Es decir, se llega al estado rojo.

**Estado verde:** la prueba anterior funciona como una especificación. Es decir, define lo que debe implementarse en `ShoppingCart`. Por lo tanto, manos a la obra:

```java
public class ShoppingCart {
  public ShoppingCart() {}
  public void add(Book b) {}
  double getTotal() {
    return 30.0;
  }
}
```

Sin embargo, algo puede causar sorpresa: ¡esa implementación es incorrecta! El constructor de `ShoppingCart` está vacío, la clase no posee ninguna estructura de datos para almacenar los ítems del carrito, `getTotal` retorna siempre `30.0`, etc.

Todo eso es cierto, pero ya hay una nueva pequeña victoria: la prueba cambió de color, de rojo a verde. Es decir, está pasando. Con TDD, los avances son siempre pequeños. En XP, esos avances son llamados *baby steps*.

Pero hay que continuar y dar una implementación más realista para `ShoppingCart`. A continuación, se presenta esa implementación:

```java
public class ShoppingCart {
  private ArrayList<Book> items;
  private double total;
  public ShoppingCart() {
    items = new ArrayList<Book>();

    total = 0.0;
  }

  public void add(Book b) {
    items.add(b);
    total += b.price;
  }

  double getTotal() {
    return total;

  }
}
```

Ahora se dispone de una estructura de datos para almacenar los ítems del carrito, un atributo para almacenar el valor total del carrito, un constructor, un método `add` que agrega los materiales a la estructura de datos e incrementa el total del carrito, y así sucesivamente.

Según el mejor juicio posible, esa implementación ya cumple con lo solicitado y, por eso, puede declararse que se llega al estado verde.

**Estado amarillo:** ahora hay que observar el código que fue implementado —una prueba y dos clases— y poner en práctica las propiedades, principios y patrones de diseño aprendidos en materiales anteriores. Es decir: ¿existe algo que pueda hacerse para volver ese código más legible, fácil de entender y fácil de mantener?

En este caso, la idea que puede surgir es encapsular los campos de `Book`. Todos ellos actualmente son públicos y, por eso, sería mejor implementar métodos `get` y `set` para acceder a ellos. Como esa implementación es simple, no se presentará el código refactorizado de `Book`.

Entonces, se cierra una vuelta en el ciclo rojo-verde-refactorizar de TDD. Ahora, puede detenerse el proceso o pensar en implementar otro requisito. Por ejemplo, se puede implementar un método para remover materiales del carrito. Para ello, hay que comenzar otro ciclo.

## Otros Tipos de Pruebas

### Pruebas Caja-Negra y Caja-Blanca

Las técnicas de prueba pueden clasificarse como **caja negra** o **caja blanca**. Cuando se usa una técnica de caja negra, las pruebas se escriben con base solo en la interfaz del sistema bajo prueba. Por ejemplo, si la misión es probar un método como una caja negra, la única información disponible incluirá su nombre, sus parámetros, sus tipos y las excepciones que puede lanzar.

Por otro lado, cuando se usa una técnica de caja blanca, la escritura de las pruebas considera información sobre el código y la estructura del sistema bajo prueba. Por eso, las técnicas de prueba de caja negra también son llamadas **pruebas funcionales**, mientras que las técnicas de caja blanca son llamadas **pruebas estructurales**.

Sin embargo, no es trivial clasificar las pruebas unitarias en una de esas categorías. En realidad, la clasificación dependerá de cómo sean escritas. Si las pruebas unitarias se escriben usando solo información sobre la interfaz de los métodos bajo prueba, entonces son consideradas pruebas de caja negra. Sin embargo, si la escritura considera información sobre la cobertura de las pruebas, tales como las bifurcaciones que son cubiertas o no, entonces son pruebas de caja blanca.

En resumen, las pruebas unitarias siempre prueban una unidad pequeña y aislada de código. Esa unidad puede ser probada como una caja negra —conociendo solo su interfaz y sus requisitos externos— o como una caja blanca —conociendo y aprovechando su estructura interna para elaborar pruebas más efectivas—.

Una observación semejante puede hacerse sobre la relación entre TDD y las pruebas de caja negra/caja blanca. Para aclarar esa relación, se usará un comentario del propio Kent Beck, tomado de *Test-Driven Development Violates the Dichotomies of Testing*, Three Rivers Institute, 2007:

“En el contexto de TDD, una dicotomía incorrecta ocurre entre pruebas de caja negra y pruebas de caja blanca. Como las pruebas en TDD son escritas antes del código que prueban, tal vez podrían ser consideradas pruebas de caja negra. Sin embargo, normalmente obtengo inspiración para escribir la siguiente prueba después de implementar y analizar el código verificado por la prueba anterior, lo que es una característica distintiva de las pruebas de caja blanca.”

### Seleción de Datos de Prueba

Cuando se adoptan pruebas de **caja negra**, existen técnicas para auxiliar en la selección de las entradas que serán verificadas en la prueba.

La **partición por clases de equivalencia** es una técnica que recomienda dividir las entradas de un problema en conjuntos de valores que tienen la misma probabilidad de revelar un *bug*. Esos conjuntos son llamados **clases de equivalencia**.

Para cada clase de equivalencia, se recomienda probar solo uno de sus valores, que puede ser escogido aleatoriamente.

Supóngase una función para calcular el valor que se debe pagar por concepto de impuesto a la renta, para cada tramo de salario, como se muestra en la tabla a continuación. La partición por clases de equivalencia recomendaría probar esa función con cuatro salarios, uno de cada tramo salarial.

| Salario | Tasa | Monto a Deducir |
| --- | --- | --- |
| De 1.903,99 hasta 2.826,65 | 7,5% | 142,80 |
| De 2.826,66 hasta 3.751,05 | 15% | 354,80 |
| De 3.751,06 hasta 4.664,68 | 22,5% | 636,13 |
| Por encima de 4.664,68 | 27,5% | 869,36 |

|  |
|  |
|  |

El **análisis de valores límite** (*Boundary Value Analysis*) es una técnica complementaria que recomienda probar una unidad con los valores límite de cada clase de equivalencia y con sus valores inmediatamente posteriores o anteriores. El motivo es que los *bugs* con frecuencia son causados por un tratamiento inadecuado de esos valores de frontera.

Así, en el ejemplo, para el primer tramo salarial, deberían probarse los siguientes valores:

- `1.903,98` : valor inmediatamente inferior al límite inferior del primer tramo salarial.

- `1.903,99` : límite inferior del primer tramo salarial.

- `2.826,65` : límite superior del primer tramo salarial.

- `2.826,66` : valor inmediatamente superior al límite superior del primer tramo salarial.

Sin embargo, como el lector debe estar pensando, no siempre es trivial encontrar las clases de equivalencia para el dominio de entrada de una función. Es decir, no siempre todos los requisitos de un sistema están organizados en tramos de valores bien definidos, como aquellos del ejemplo.

Para concluir, es importante recordar que las pruebas exhaustivas, es decir, probar un programa con todas las entradas posibles, en la práctica son imposibles, incluso en programas pequeños. Por ejemplo, imagínese un compilador de un lenguaje (X). Es imposible probar ese compilador con todos los programas que pueden ser implementados en (X), incluso porque su número es infinito.

En realidad, incluso una función con solo dos enteros como parámetros podría llevar siglos para ser probada exhaustivamente con todos los posibles pares de enteros. Las pruebas aleatorias, cuando los datos de prueba son escogidos al azar, tampoco son recomendables en la mayoría de los casos. El motivo es que se pueden seleccionar diferentes valores de una misma clase de equivalencia, lo que no es necesario. Por otro lado, algunas clases de equivalencia pueden quedar sin pruebas.

### Pruebas de Aceptación

Son pruebas realizadas por el cliente, con datos del cliente. Los resultados de esas pruebas determinarán si el cliente está de acuerdo o no con la implementación realizada. Si está de acuerdo, el sistema puede entrar en producción. Si no está de acuerdo, deben realizarse los ajustes correspondientes.

Por ejemplo, cuando se usan métodos ágiles, una historia solo se considera completa después de pasar por pruebas de aceptación realizadas por los usuarios al final de un *sprint*, como se estudiará más adelante.

Las pruebas de aceptación poseen dos características que las distinguen de todas las pruebas estudiadas anteriormente en este material. Primero, son pruebas manuales, realizadas por los clientes finales del sistema. Segundo, no constituyen exclusivamente una actividad de verificación, como las pruebas anteriores, sino también una actividad de validación del sistema.

Recuérdese lo visto en el material de introducción: la verificación prueba si el sistema fue realizado correctamente, es decir, de acuerdo con su especificación o sus requisitos. En cambio, la validación prueba si se realizó el sistema correcto, es decir, aquel que el cliente pidió y necesita.

Las pruebas de aceptación pueden dividirse en dos fases. Las pruebas alfa son realizadas con algunos usuarios, pero en un ambiente controlado, como la propia máquina del desarrollador. Si el sistema es aprobado en las pruebas alfa, puede realizarse una prueba con un grupo mayor de usuarios y ya no en un ambiente controlado. Esas pruebas son llamadas pruebas beta.

### Pruebas de Requisitos No-Funcionales

Las pruebas anteriores, con excepción de las pruebas de aceptación, verifican solo requisitos funcionales; por lo tanto, tienen como objetivo encontrar *bugs*. Sin embargo, también es posible realizar pruebas para verificar o validar requisitos no funcionales.

Por ejemplo, existen herramientas que permiten realizar **pruebas de desempeño**, para verificar el comportamiento de un sistema bajo cierta carga. Una empresa de comercio electrónico podría usar una de esas herramientas para simular el desempeño de su sitio durante un gran evento, como una *Black Friday*, por ejemplo.

Por su parte, las **pruebas de usabilidad** se usan para evaluar la interfaz del sistema y, normalmente, involucran la observación de usuarios reales mientras utilizan el sistema.

Las **pruebas de fallas** simulan eventos anormales en un sistema, por ejemplo, la caída de algunos servicios o incluso de un centro de datos completo.

## Ejercicios

1. Un equipo está realizando pruebas con el código fuente de un sistema. Las pruebas involucran la verificación de diversos componentes individualmente, así como de las interfaces entre ellos. Ese equipo está realizando pruebas de: a. unidad

b. aceptación

c. sistema y aceptación

d. integración y sistema

e. unidad e integración

2. Describa tres beneficios asociados al uso de pruebas unitarias.

3. Suponga una función `fib(n)`, que retorna el n-ésimo término de la secuencia de Fibonacci, es decir,
`fib(0) = 0`, `fib(1) = 1`, `fib(2) = 1`, `fib(3) = 2`, `fib(4) = 3`, etc. Escriba una prueba unitaria para esa función.

4. Reescriba la siguiente prueba, que verifica el lanzamiento de una excepción `EmptyStackException`, para que quede más simple y fácil de entender.

```java
@Test
public void testEmptyStackException() {

  boolean sucesso = false;
  try {

    Stack<Integer> stack = new Stack<>();

    stack.push(10);

    int r = stack.pop();

    r = stack.pop();
  } catch (EmptyStackException y) {
    sucesso = true;
  }
  assertTrue(sucesso);
}
```

1. Supóngase que un programador escribió la siguiente prueba para la clase `ArrayList` de Java. Como se puede observar, en el código se usan diversos comandos `System.out.println`. Es decir, en el fondo, se trata de una prueba manual, pues el desarrollador debe verificar su resultado manualmente. Reescriba entonces cada una de las pruebas —de la 1 a la 6— como una prueba unitaria, usando la sintaxis y los comandos de JUnit. **Observación:** si desea ejecutar el código, este está disponible en el siguiente enlace.

```java
import java.util.List;
import java.util.ArrayList;

public class Main {
  public static void main(String[] args) {

    // prueba 1

    List<Integer> s = new ArrayList<>();

    System.out.println(s.isEmpty());

    // prueba 2

    s = new ArrayList<Integer>();

    s.add(1);
    System.out.println(s.isEmpty());

    // prueba 3

    s = new ArrayList<Integer>();

    s.add(1);
    s.add(2);
    s.add(3);
    System.out.println(s.size());
    System.out.println(s.get(0));
    System.out.println(s.get(1));
    System.out.println(s.get(2));

    // prueba 4

    s = new ArrayList<Integer>();

    s.add(1);
    s.add(2);
    s.add(3);

    int elem = s.remove(2);

    System.out.println(elem);
    System.out.println(s.get(0));
    System.out.println(s.get(1));

    // prueba 5

    s = new ArrayList<Integer>();

    s.add(1);
    s.remove(0);
    System.out.println(s.size());
    System.out.println(s.isEmpty());

    // prueba 6
    try {

      s = new ArrayList<Integer>();

      s.add(1);
      s.add(2);
      s.remove(2);
    }
    catch (IndexOutOfBoundsException y) {
      System.out.println("IndexOutOfBounds");
    }
  }
}
```

1. Considérese la siguiente función. Obsérvese que posee cuatro comandos, dos de los cuales son `if` . Por lo tanto, esos dos `if` generan cuatro ramas ( *branches* ):

```java
void f(int x, int y) {
  if (x > 0) {

     x = 2 * x;

     if (y > 0) {

        y = 2 * y;
     }
  }
}
```

Suponiendo el código anterior, complete la siguiente tabla con los valores de la cobertura de comandos y de la cobertura de ramas (*branches*) obtenidos con las pruebas especificadas en la primera columna. Es decir, la primera columna define las llamadas de la función `f` que realiza la prueba.

| Llamada realizada por la prueba | Cobertura de instrucciones | Cobertura de ramas |
| --- | --- | --- |
| `f(0,0)` |  |  |
| `f(1,1)` |  |  |
| `f(0,0)` y `f(1,1)` |  |  |

1. Supóngase el siguiente requisito: los alumnos reciben concepto A en una asignatura si tienen una nota mayor o igual a 90. Considérese entonces la siguiente función, que implementa ese requisito:

```java
boolean isConceptoA(int nota) {
  if (nota > 90)
    return true;
  else
    return false;
}
```

El código de esa función posee tres comandos, uno de los cuales es un `if`; por lo tanto, posee dos ramas (*branches*). Responda ahora las siguientes preguntas.

1. ¿La implementación de esa función posee un *bug* ? Si es así, ¿cuándo ese *bug* produce una falla?

2. Suponga que esta función —exactamente como está implementada— es probada con dos notas: 85 y 95. ¿Cuál es la cobertura de comandos de esa prueba? ¿Y cuál es la cobertura de ramas? ¿La implementación de esa función posee un *bug* ? Si es así, ¿cuándo ese *bug* produce una falla?

3. Considérese la siguiente afirmación: si un programa posee 100% de cobertura de pruebas a nivel de comandos, entonces está libre de *bugs* . ¿Esta afirmación es verdadera o falsa? Justifique.

1. Complete los comandos `assert` en los fragmentos indicados.

```java
public void test1() {
   LinkedList list = mock(LinkedList.class);
   when(list.size()).thenReturn(10);

   assertEquals(___________, ___________);
}
```

```java
public void test2() {
   LinkedList list = mock(LinkedList.class);
   when(list.get(0)).thenReturn("Ingeniería");
   when(list.get(1)).thenReturn("Software");
   String result = list.get(0) + " " + list.get(1);

   assertEquals(___________, ___________);
}
```

[← Volver](../ingsoft.md)
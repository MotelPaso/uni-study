# Strategy

_Original: https://www.danielsanmartin.cl/blog/pdd-is-8/_


**Contexto**: Supongamos que estamos implementando un paquete de estructuras de datos, con la siguiente clase lista:

```java
class MyList {

  ... // datos de una lista
  ... // métodos de una lista: add, delete, search

  public void sort() {
    ... // ordena la lista usando Quicksort
  }
}
```

**Problema**: nuestros clientes están solicitando que se puedan usar nuevos algoritmos de ordenación para ordenar los elementos de la lista. Explicando mejor, quieren tener la opción de cambiar y definir, por su cuenta, el algoritmo de ordenación. Sin embargo, la versión actual de la clase siempre ordena la lista usando el algoritmo Quicksort. Si recordamos los principios de diseño, podemos decir que la clase `MyList` no sigue el principio Abierto/Cerrado, considerando el algoritmo de ordenación.

**Solución**: el Patrón Strategy es la solución a nuestro problema de abrir la clase MyList para nuevos algoritmos de ordenación, pero sin modificar su código fuente. El objetivo del patrón es parametrizar los algoritmos usados por una clase. Prescribe cómo encapsular una familia de algoritmos y cómo hacerlos intercambiables. Por lo tanto, su uso es recomendado cuando una clase utiliza un cierto algoritmo (de ordenación, en nuestro ejemplo). Sin embargo, como existen diversos algoritmos con este propósito, no se quiere anticipar una decisión e implementar solo uno de ellos en el cuerpo de la clase, como ocurre en la primera versión de MyList.

A continuación, se muestra el nuevo código de `MyList`, usando el Patrón Strategy para configurar el algoritmo de ordenación:

```java
class MyList {

  ... // datos de una lista
  ... // métodos de una lista: add, delete, search

  private SortStrategy strategy;

  public MyList() {
    strategy = new QuickSortStrategy();
  }

  public void setSortStrategy(SortStrategy strategy) {
    this.strategy = strategy;
  }

  public void sort() {
    strategy.sort(this);
  }
}
```

En esta nueva versión, el algoritmo de ordenación se convirtió en un atributo de la clase `MyList` y se creó un método set para configurar este algoritmo. El método `sort` delega la tarea de ordenación a un método del mismo nombre del objeto con la estrategia de ordenación. En esta llamada, se pasa `this` como parámetro, ya que el algoritmo que se ejecutará debe tener acceso a la lista para ordenar sus elementos.

Para finalizar la presentación del patrón, mostramos el código de las clases que implementan las estrategias, es decir, los algoritmos de ordenación:

```java
abstract class SortStrategy {
  abstract void sort(MyList list);
}

class QuickSortStrategy extends SortStrategy {
  void sort(MyList list) { ... }
}

class ShellSortStrategy extends SortStrategy {
  void sort(MyList list) { ... }
}
```

[← Volver](index.md)
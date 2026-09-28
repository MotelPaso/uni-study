# Composición por sobre Herencia

_Original: https://www.danielsanmartin.cl/blog/composition-hierarchy-is/_


Antes de explicar el principio, aclaremos que existen dos tipos de herencia:

- **Herencia de clases** (ejemplo: `class A extends B`), que es la que implica reutilización de código. No solo en este capítulo, sino en todo el libro, cuando mencionemos simplemente el término *herencia* nos estaremos refiriendo a la herencia de clases.

- **Herencia de interfaces** (ejemplo: `interface I extends J`), que no implica reutilización de código. Esta forma de herencia es más simple y no suscita preocupaciones. Cuando necesitemos referirnos a ella, utilizaremos el término completo: *herencia de interfaces*.

Volviendo al principio, cuando la programación orientada a objetos se hizo común, en la década de los 80, hubo un impulso hacia el uso de la herencia. Se creía que el concepto podría ser una especie de bala de plata capaz de resolver los problemas de reutilización de software. Se argumentaba que jerarquías de clases profundas, con varios niveles, serían un indicativo de un buen diseño, en el cual se lograban altos índices de reutilización. Sin embargo, con el tiempo, se dio cuenta de que la herencia no era esa bala de plata. Por el contrario, la herencia tiende a introducir problemas en el mantenimiento y evolución de las clases de un sistema. Estos problemas tienen su origen en el fuerte acoplamiento que existe entre subclases y superclases, según lo descrito por Gamma y colegas en el libro sobre patrones de diseño [enlace](https://dl.acm.org/doi/book/10.5555/186897):

> La herencia expone a las subclases detalles de implementación de las clases padre. Por lo tanto, frecuentemente se dice que la herencia viola el encapsulamiento de las clases padre. La implementación de las subclases se vuelve tan acoplada a la implementación de la clase padre que cualquier cambio en estas últimas puede forzar modificaciones en las subclases.

El principio, sin embargo, no prohíbe el uso de la herencia. Pero recomienda lo siguiente: si existen dos soluciones de diseño, una basada en herencia y otra en composición, la solución mediante composición suele ser la mejor. Para aclarar, existe una relación de composición entre dos clases `A` y `B` cuando la clase `A` tiene un atributo del tipo `B`.

**Ejemplo**: Supongamos que tenemos que implementar una clase `Stack`. Existen al menos dos soluciones — mediante herencia o mediante composición — como muestra el siguiente código:

Solución via herencia:

```java
class Stack extends ArrayList {
  ...
}
```

Solución via composición:

```java
class Stack {
  private ArrayList elementos;
  ...
}
```

La solución mediante herencia no es recomendada por varios motivos, siendo los principales los siguientes: (1) un `Stack`, en términos conceptuales, no es un `ArrayList`, sino una estructura que puede usar un `ArrayList` en su implementación interna; (2) cuando se fuerza una solución vía herencia, la clase `Stack` heredará métodos como `get` y `set`, que no forman parte de la especificación de pilas. Por lo tanto, en este caso, debemos preferir la solución basada en composición.

Una segunda ventaja de la composición es que la relación entre las clases no es estática, como en el caso de la herencia. En el ejemplo, si optáramos por la herencia, la clase `Stack` estaría acoplada estáticamente a `ArrayList`; y no sería posible cambiar esa decisión en tiempo de ejecución. Por otro lado, cuando se adopta una solución basada en composición, esto se vuelve más fácil, como muestra el ejemplo a continuación:

```java
class Stack {

  private List elementos;

  Stack(List elementos) {
    this.elementos = elementos;
  }
  ...
}
```

En el ejemplo, la estructura de datos que almacena los elementos de la pila pasó a ser un parámetro del constructor de la clase `Stack`. Con esto, se hace posible instanciar objetos `Stack` con diferentes estructuras de datos. Por ejemplo, un objeto en el cual los elementos de la pila se almacenan en un `ArrayList` y otro objeto en el cual se almacenan en un `Vector`. Como observación final, note que el tipo del atributo `elementos` de `Stack` pasó a ser un `List`; es decir, también hicimos uso del Principio de Inversión de Dependencias (o *Prefiera Interfaces a Clases*).

Antes de concluir, se deben mencionar tres puntos adicionales a lo que discutimos sobre *Prefiera Composición a Herencia*:

- La herencia se clasifica como un mecanismo de reutilización de caja blanca, ya que las subclases suelen tener acceso a los detalles de implementación de la clase base. Por otro lado, la composición es un mecanismo de reutilización de caja negra.

- Un patrón de diseño que ayuda a reemplazar una solución basada en herencia por una solución basada en composición es el Patrón Decorador.

- Debido a los problemas discutidos en esta sección, lenguajes de programación más recientes, como **Go** y **Rust** , no incluyen soporte para herencia.

[← Volver](index.md)
# Principio de Inversión de Dependencias

_Original: https://www.danielsanmartin.cl/blog/dependency-inversion-is/_


Este principio recomienda que una clase cliente establezca dependencias prioritariamente con abstracciones y no con implementaciones concretas, ya que las abstracciones (es decir, interfaces) son más estables que las implementaciones concretas (es decir, clases). La idea es, entonces, intercambiar (o invertir) las dependencias: en lugar de depender de clases concretas, los clientes deben depender de interfaces. Por lo tanto, un nombre más intuitivo para el principio sería *Prefiera Interfaces a Clases*.

Para detallar la idea del principio, supongamos que existe una interfaz `I` y una clase `C1` que la implementa. Si puede elegir, un cliente debe acoplarse a `I` y no a `C1`. El motivo es que cuando un cliente se acopla a una interfaz `I`, queda inmune a los cambios en la implementación de esa interfaz. Por ejemplo, en lugar de `C1`, se puede cambiar la implementación a `C2`, y esto no tendrá impacto en el cliente en cuestión.

**Ejemplo 1**: El siguiente código ilustra el escenario que acabamos de describir. En este código, el mismo Cliente puede trabajar con objetos concretos de las clases `C1` y `C2`. No necesita conocer la clase concreta que está detrás, o que implementa, la interfaz `I` a la que referencia en su código.

```java
interface I { ... }

class C1 implements I {
  ...
}
class C2 implements I {
  ...
}
```

```java
class Cliente {

  I i;

  Cliente (I i) {
    this.i = i;
    ...
  } ...
}
```

```java
class Main {

  void main () {
    C1 c1 = new C1();
    new Cliente(c1);
    ...
    C2 c2 = new C2();
    new Cliente(c2);
    ...
  }
}
```

**Ejemplo 2**: Ahora, mostramos un ejemplo de código que sigue el Principio de Inversión de Dependencias. Este principio justifica la elección de `Proyector` como tipo del parámetro del método `g`. Mañana, el tipo de la variable local `proyector` en el método `f` podría cambiar a, por ejemplo, `ProyectorSamsung`. Si eso llegara a suceder, la implementación de `g` seguiría siendo válida, ya que al usar un tipo interfaz nos estamos preparando para recibir parámetros de varios tipos concretos que implementen esa interfaz.

```java
void f() {
  ...
  Proyector proyector = new ProyectorLG();
  ...
  g(proyector);
}
```

```java
void g(Proyector proyector) {
  ...
}
```

**Ejemplo 3**: Como ejemplo final, supongamos un paquete de estructuras de datos que ofrece una interfaz `List` y algunas implementaciones concretas (clases) para ella, como `ArrayList`, `LinkedList` y `Vector`. Siempre que sea posible, en el código cliente de ese paquete, declara variables, parámetros o atributos usando el tipo `List`, ya que de esta manera estarás creando código compatible con las diversas implementaciones concretas de esa interfaz.

[← Volver](index.md)
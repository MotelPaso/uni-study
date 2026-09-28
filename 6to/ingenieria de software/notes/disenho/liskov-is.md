# Principo de Sustitución de Liskov

_Original: https://www.danielsanmartin.cl/blog/liskov-is/_


Como ya discutimos al hablar del principio “Prefiere Composición a Herencia”, la herencia ya no es un concepto tan popular como lo fue en la década de 1980. Hoy en día, el uso de la herencia es más restringido y raro. Sin embargo, algunos casos de uso todavía la justifican. La herencia define una relación “es-un” entre objetos de una clase base y objetos de subclases. La ventaja es que comportamientos (es decir, métodos) comunes a estas clases pueden ser implementados una sola vez en la clase base. Una vez hecho esto, se heredan en todas las subclases.

El Principio de Sustitución de Liskov especifica reglas para la redefinición de métodos de clases base en clases derivadas. El nombre del principio hace referencia a Barbara Liskov, profesora del MIT y ganadora de la edición de 2008 del Premio Turing. Entre otros trabajos, Liskov desarrolló investigaciones sobre sistemas de tipos para lenguajes orientados a objetos. En uno de esos trabajos, enunció el principio que luego recibió su nombre.

Para explicar el Principio de Sustitución de Liskov, nos basaremos en el siguiente ejemplo:

```java
void f(A a) {
  ...
  a.g();
  ...
}
```

El método `f` puede ser llamado pasando como parámetros objetos de subclases `B1`, `B2`, …, `Bn` de la clase base `A`, como se muestra a continuación:

```java
f(new B1());  // f puede recibir objetos de la subclase `B1`
...
f(new B2());  // y de cualquier subclase de `A`, como `B2`
...
f(new B3());  // y B3
```

El Principio de Sustitución de Liskov determina las condiciones — semánticas y no sintácticas — que las subclases deben cumplir para que un programa como el anterior funcione correctamente.

Supongamos que las subclases `B1`, `B2`, …, `Bn` redefinen el método `g()` de `A`, que es un método llamado en el cuerpo de `f`. El Principio de Sustitución de Liskov prescribe que estas redefiniciones no pueden violar el contrato de la implementación original de `g` en `A`.

**Ejemplo 1**: Supongamos una clase base que calcula números primos. Supongamos también algunas subclases que implementan otros algoritmos con el mismo propósito. Específicamente, el método `getPrimo(n)` es un método que devuelve el enésimo número primo. Este método existe en la clase base y se redefine en todas las subclases.

Supongamos además que el contrato del método `getPrimo(n)` especifique lo siguiente: $1 <= n <= 1 millón$. Es decir, el método debe ser capaz de devolver cualquier número primo para //n// variando de //1 hasta 1 millón//. En este ejemplo, una posible violación del contrato de `getPrimo(n)` ocurre, por ejemplo, si en una de las clases el algoritmo implementado calcula solo números primos hasta //900 mil//.

De manera más concreta, el Principio de Sustitución de Liskov define lo siguiente: supongamos que un cliente llama a un método `getPrimo(n)` de un objeto p de la clase `NumeroPrimo`. Supongamos ahora que el objeto `p` es reemplazado por un objeto de una subclase de `NumeroPrimo`. En este caso, el cliente comenzará a ejecutar el método `getPrimo(n)` de esa subclase. Sin embargo, esta sustitución de métodos no debe afectar el comportamiento del cliente. Para ello, todos los métodos `getPrimo(n)` de las subclases de NumeroPrimo deben realizar las mismas tareas que el método original, posiblemente de manera más eficiente.

**Ejemplo 2**: Vamos a mostrar un segundo ejemplo de violación, esta vez bastante evidente, para reforzar el concepto del Principio de Sustitución de Liskov.

```java
class A {
  int suma(int a, int b) {
    return a+b;
  }
}
```

```java
class B extends A {

  int suma(int a, int b) {
    String r = String.valueOf(a) + String.valueOf(b);
    return Integer.parseInt(r);
  }

}
```

```java
class Cliente {

  void f(A a) {
    ...
    a.suma(1,2); // puede retornar 3 o 12
    ...
  }
}
```

```java
class Main {

  void main() {
    A a = new A();
    B b = new B();
    Cliente cliente = new Cliente();
    cliente.f(a);
    cliente.f(b);
  }
}
```

En este ejemplo, el método que suma dos enteros ha sido redefinido en la subclase con una semántica de concatenación de los respectivos valores convertidos a cadenas. Por lo tanto, para un desarrollador encargado de mantener la clase Cliente, la situación se vuelve bastante confusa. En una ejecución, la llamada `suma(1,2)` devuelve 3 (es decir, 1+2); en la ejecución siguiente, la misma llamada devolverá 12 (es decir, 1+2 = 12 o 12 como entero).

[← Volver](index.md)
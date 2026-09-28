# Ley de Demeter

_Original: https://www.danielsanmartin.cl/blog/demeter-is/_


El nombre de este principio hace referencia a un grupo de investigación de la Northeastern University, en Boston, EE. UU. Este grupo, llamado Demeter, desarrollaba investigaciones en el área de modularización de software. A finales de la década de los 80, en una de sus investigaciones, el grupo formuló un conjunto de reglas para evitar problemas de encapsulamiento en el diseño de sistemas orientados a objetos, conocidas como Principio o Ley de Demeter.

El Principio de Demeter — también llamado Principio del Menor Privilegio (**Principle of Least Privilege**) — sostiene que la implementación de un método solo debe invocar los siguientes otros métodos:

- De su propia clase (caso 1)

- De objetos pasados como parámetros (caso 2)

- De objetos creados por el propio método (caso 3)

- De atributos de la clase del método (caso 4)

**Ejemplo**: El siguiente código muestra un método `m1` con cuatro llamadas que respetan el Principio de Demeter. Y, a continuación, tenemos un método `m2` con una llamada que no cumple con el principio.

```java
class PrincipioDemeter {

  T1 attr;

  void f1() {
    ...
  }

  void m1(T2 p) {  // método que sigue Demeter
    f1();           // caso 1: propia clase
    p.f2();         // caso 2: parámetro
    new T3().f3();  // caso 3: creado por el método
    attr.f4();      // caso 4: atributo de la clase
  }

  void m2(T4 p) {  // método que viola Demeter
    p.getX().getY().getZ().doSomething();
  }

}
```

El método `m2`, al llamar tres métodos `get` en secuencia, viola el Principio de Demeter. El motivo es que los objetos intermedios — devueltos por los métodos `get` — se utilizan solo como paso para llegar al objeto final, que es el que realmente nos interesa y sobre el cual vamos a ejecutar una operación “útil” — en el ejemplo, `doSomething()`. Sin embargo, esos objetos intermedios pueden existir solo para revelar información interna sobre el estado de sus clases. Además de hacer la llamada más compleja, la información revelada puede estar sujeta a cambios. Si esto ocurre, uno de los eslabones de la secuencia de llamadas se romperá y el cliente — el método `m2`, en el ejemplo — tendrá que encontrar otra forma de alcanzar el método final. En resumen, las llamadas que violan el Principio de Demeter tienen una alta probabilidad de romper el encapsulamiento de los objetos de paso.

Se suele decir que el Principio de Demeter recomienda que los métodos de una clase solo deben hablar con sus “amigos”, es decir, con métodos de la propia clase o con métodos de objetos que reciben como parámetro o que crean. Por otro lado, no es recomendable hablar con los amigos de los amigos.

Un ejemplo — formulado por David Bock ([enlace](https://www2.ccs.neu.edu/research/demeter/demeter-method/LawOfDemeter/paper-boy/demeter.pdf)) — ilustra con claridad los beneficios del Principio de Demeter. El ejemplo se basa en un escenario con tres objetos: un repartidor de periódicos, un cliente y su billetera. Se produce una violación del Principio de Demeter si, para recibir el importe de un periódico, el repartidor tiene que ejecutar el siguiente código:

```java
precio = 6.00;
Billetera billetera = cliente.getBilletera();
if (billetera.getValorTotal() >= precio) {  // viola Demeter
   billetera.debita(precio);                // viola Demeter
} else {
  // vuelvo mañana, para cobrar el valor del periódico
}
```

El repartidor tiene acceso a la billetera de su cliente — a través de `getBilletera()` — y luego él mismo saca el importe del periódico de ella. Sin embargo, ningún cliente aceptaría que un repartidor tuviera esa libertad. Una solución más realista es la siguiente:

```java
precio = 6.00;
try {
  cliente.pagar(precio);
}
catch (ExcepcionValorInsuficiente e) {
  // vuelvo mañana, para cobrar el valor del periódico
}
```

En el nuevo código, el cliente no permite el acceso a su billetera. Por el contrario, el repartidor ni siquiera se entera de que el cliente tiene una billetera. Esa información está encapsulada en la clase `Cliente`. En lugar de eso, el cliente ofrece un método `pagar`, que debe ser llamado por el repartidor. Finalmente, una excepción indica cuando el Cliente no tiene suficientes recursos para pagar el periódico.

[← Volver](index.md)
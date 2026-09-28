# Adapter

_Original: https://www.danielsanmartin.cl/blog/pdd-is-5/_


**Contexto**: Supongamos un sistema que debe controlar proyectores multimedia. Para ello, debe instanciar objetos de clases proporcionadas por los fabricantes de cada proyector, como se ilustra a continuación:

```java
class ProyectorSamsung {
  public void turnOn() { ... }
  ...
}

class ProyectorLG {
  public void enable(int timer) { ... }
  ...
}
```

Para simplificar, solo estamos mostrando dos clases. Sin embargo, en un escenario real, pueden involucrarse clases de otros fabricantes de proyectores. También estamos mostrando solo un método de cada clase, aunque estas pueden contener otros métodos. En particular, el método mostrado es responsable de encender el proyector. En el caso de los proyectores de Samsung, este método no tiene parámetros. En el caso de los proyectores de LG, podemos pasar un intervalo en minutos para encender el proyector. Si este parámetro es igual a cero, el proyector se enciende de inmediato. Observa además que el nombre de los métodos es diferente en ambas clases.

**Problema**: En el sistema de control de proyectores multimedia, queremos usar una interfaz única para encender los proyectores, independientemente de la marca. El siguiente código muestra esta interfaz y una clase cliente del sistema:

```java
interface Proyector {

  void liga();

}
...
class SistemaControlProyectores {

  void init(Proyector proyector) {
    proyector.liga();  // liga cualquier proyector
  }

}
```

Sin embargo, las clases de cada proyector — mostradas anteriormente — fueron implementadas por sus fabricantes y están listas para su uso. Es decir, no tenemos acceso al código de estas clases para hacer que implementen la interfaz `Proyector`.

**Solución**: El patrón de diseño **Adaptador** — también conocido como **Wrapper** — es una solución para nuestro problema. Se recomienda usar este patrón cuando necesitamos convertir la interfaz de una clase en otra interfaz, esperada por sus clientes. En nuestro ejemplo, puede utilizarse para convertir la interfaz `Proyector` — usada en el sistema de control de proyectores — en las interfaces (métodos públicos) de las clases implementadas por los fabricantes de proyectores.

Un ejemplo de clase adaptadora, de `ProyectorSamsung` a `Proyector`, se muestra a continuación:

```java
class AdaptadorProyectorSamsung implements Proyector {

  private ProyectorSamsung proyector;

  AdaptadorProyectorSamsung (ProyectorSamsung proyector) {
    this.proyector = proyector;
  }

  public void liga() {
    proyector.turnOn();
  }
}
```

La clase `AdaptadorProyectorSamsung` implementa la interfaz Proyector. Por lo tanto, los objetos de esta clase pueden pasarse como parámetros del método `init()` del sistema de control de proyectores. La clase `AdaptadorProyectorSamsung` también tiene un atributo privado del tipo `ProyectorSamsung`. La secuencia de llamadas es la siguiente (también se puede seguir en el diagrama de secuencia UML, mostrado en la página siguiente): primero, el cliente — en nuestro caso, representado por el método `init` — llama a `liga()` de la clase adaptadora; luego, la ejecución de este método llama al método equivalente — en este caso, `turnOn()` — del objeto que está siendo “adaptado”; es decir, un objeto que accede a proyectores Samsung.

Si queremos manipular proyectores LG, tendremos que implementar una segunda clase adaptadora. Sin embargo, su código será similar al de `AdaptadorProyectorSamsung`.

[← Volver](index.md)
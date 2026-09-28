# Observador

_Original: https://www.danielsanmartin.cl/blog/pdd-is-9/_


**Contexto**: Supongamos que estamos implementando un sistema para controlar una estación meteorológica. En este sistema, tenemos que manipular objetos de dos clases: `Temperatura`, que son objetos de modelo que almacenan las temperaturas monitoreadas en la estación meteorológica; y `Termómetro`, que es una clase usada para crear objetos visuales que muestran las temperaturas bajo monitoreo. Los termómetros deben mostrar la temperatura actual monitoreada. Si la temperatura cambia, los termómetros deben actualizarse.

**Problema**: No queremos acoplar `Temperatura` (clase de modelo) a `Termómetro` (clase de interfaz). El motivo es simple: las clases de interfaz cambian con frecuencia. En la versión actual, el sistema tiene una interfaz textual que muestra las temperaturas en Celsius en la consola del sistema operativo. Pero, pronto, planeamos tener interfaces web, para dispositivos móviles y para otros sistemas. También planeamos ofrecer otras interfaces de termómetros, como digitales, analógicos, etc. Además, tenemos más clases similares a `Temperatura` y `Termómetro` en nuestro sistema, tales como: `PresiónAtmosférica` y `Barómetro`, `HumedadDelAire` e `Higrómetro`, `VelocidadDelViento` y `Anemómetro`, etc. Por lo tanto, en la medida de lo posible, nos gustaría reutilizar el mecanismo de notificación también en estos otros pares de clases.

**Solución**: El patrón Observador es la solución recomendada para nuestro contexto y problema. Este patrón define cómo implementar una relación de uno-a-muchos entre objetos sujeto y observadores. Cuando el estado de un sujeto cambia, sus observadores deben ser notificados.

Primero, mostraremos un programa principal para nuestro problema:

```java
void main() {
  Temperatura t = new Temperatura();
  t.addObserver(new TermometroCelsius());
  t.addObserver(new TermometroFahrenheit());
  t.setTemp(100.0);
}
```

Este programa crea un objeto del tipo `Temperatura` (un sujeto) y luego añade dos observadores a él: un `TermómetroCelsius` y un `TermómetroFahrenheit`. Finalmente, se define el valor de la temperatura a 100 grados Celsius. Se supone que las temperaturas se monitorean por defecto en la escala Celsius.

Las clases `Temperatura` y `TermómetroCelsius` se muestran a continuación

```java
class Temperatura extends Subject {

  private double temp;

  public double getTemp() {
    return temp;
  }

  public void setTemp(double temp) {
    this.temp = temp;
    notifyObservers();
  }
}

class TermometroCelsius implements Observer {

  public void update(Subject s){
    double temp = ((Temperatura) s).getTemp();
    System.out.println("Temperatura Celsius: " + temp);
  }
}
```

Observe que `Temperatura` hereda de una clase llamada `Subject`. En la solución propuesta, todos los sujetos deben extender esta clase. Al hacerlo, heredan dos métodos:

- **addObserver**: En el ejemplo, este método se usa en el programa principal para agregar dos termómetros como observadores de una instancia de `Temperatura`.

- **notifyObservers**: En el ejemplo, este método es llamado por `Temperatura` para notificar a sus observadores que su valor ha cambiado en el método `setTemp`.

La implementación de `notifyObservers` — que se omite en el ejemplo — llama al método `update` de los objetos que se registraron como observadores de una determinada instancia de `Temperatura`. El método update forma parte de la interfaz `Observer`, que debe ser implementada por todo observador, como es el caso de `TermometroCelsius`.

El patrón Observador tiene las siguientes ventajas principales:

- No acopla a los sujetos con sus observadores. En realidad, los sujetos — como `Temperatura` en el ejemplo — no conocen a sus observadores. De manera genérica, los sujetos publican un evento anunciando el cambio de su estado — llamando a `notifyObservers` — y los observadores interesados son notificados. Este comportamiento facilita la reutilización de los sujetos en diversos escenarios y también la implementación de diferentes tipos de observadores para el mismo tipo de sujeto.

- Una vez implementado, el patrón Observador proporciona un mecanismo de notificación que puede ser reutilizado por diferentes pares de sujeto-observador. Por ejemplo, podemos reutilizar la clase `Subject` y la interfaz `Observer` para notificaciones relacionadas con la presión atmosférica y los barómetros, la humedad del aire y los higrómetros, la velocidad del viento y los anemómetros, etc.

El código completo de la implementación del patrón se encuentra a continuación:

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Iterator;

class Subject {
  private List<Observer> observers = new ArrayList<Observer>();

  public void addObserver(Observer observer) {
    observers.add(observer);
  }

  public void removeObserver(Observer observer) {
    observers.remove(observer);
  }

  public void notifyObservers() {
    Iterator it = observers.iterator();
    while (it.hasNext()) {
      Observer obs= (Observer) it.next();
      obs.update(this);
    }
  }

}

interface Observer {
  public void update(Subject s);
}


class Temperatura extends Subject  {
   private double temp;

   public double getTemp() {
     return temp;
   }
   public void setTemp(double temp) {
     this.temp = temp;
     notifyObservers();
   }
}

class TermometroCelsius implements Observer  {
  public void update(Subject s) {
    double temp = ((Temperatura) s).getTemp();
    System.out.println("Temperatura Celsius: " + temp);
  }
}

public class Main {

   public static void  main(String [] args) {
      Temperatura t = new Temperatura();
      t.addObserver(new TermometroCelsius ());
      t.setTemp(100.0);
   }

}
```

[← Volver](index.md)
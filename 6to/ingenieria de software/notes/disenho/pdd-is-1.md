# Method Factory

_Original: https://www.danielsanmartin.cl/blog/pdd-is-1/_


**Contexto**: Supongamos un sistema distribuido basado en TCP/IP. En este sistema, tres funciones `f`, `g` y `h` crean objetos del tipo `TCPChannel` para comunicación remota, como muestra el siguiente código.

```java
void f() {
  TCPChannel c = new TCPChannel();
  ...
}

void g() {
  TCPChannel c = new TCPChannel();
  ...
}

void h() {
  TCPChannel c = new TCPChannel();
  ...
}
```

**Problema:** Supongamos que, en determinadas configuraciones del sistema, necesitaremos usar UDP para la comunicación. Por lo tanto, si consideramos este requisito, el sistema no cumple con el Principio Abierto/Cerrado, es decir, no está cerrado para modificaciones y abierto para extensiones en los protocolos de comunicación utilizados. Para ser más claros, nos gustaría parametrizar el código anterior para crear objetos de los tipos TCPChannel o UDPChannel, dependiendo de los clientes. El problema es que el operador new debe ir seguido del nombre literal de una clase. Este operador —al menos en lenguajes como Java, C++ y C#— no permite que la clase de los objetos que se pretende crear se pase como un parámetro. En resumen, el problema consiste en parametrizar la instanciación de los canales de comunicación en el código anterior, de manera que pueda trabajar con diferentes protocolos.

**Solución**: La solución que vamos a describir se basa en el patrón de diseño Fábrica. Este patrón tiene algunas variaciones, pero en nuestro problema vamos a adoptar un método estático que: (1) solo crea y devuelve objetos de una determinada clase; (2) y también oculta el tipo de estos objetos detrás de una interfaz. A continuación, se muestra un ejemplo:

```java
class ChannelFactory {
  public static Channel create() {// método fábrica estático
    return new TCPChannel();
  }
}

void f() {
  Channel c = ChannelFactory.create();
  ...
}

void g() {
  Channel c = ChannelFactory.create();
  ...
}
void h() {
  Channel c = ChannelFactory.create();
  ...
}
```

En esta nueva versión, las funciones `f`, `g` y `h` no son conscientes del tipo de Channel que van a crear y usar. Ellas llaman a un Método de Fábrica Estático, que instancia y devuelve un objeto de una clase concreta. Para ser claros, esta variante del patrón de Fábrica no fue propuesta en el libro de la Gang of Four, sino que fue presentada algunos años después por Joshua Bloch ([enlace](https://dl.acm.org/doi/book/10.5555/1377533)). Es importante destacar también que las tres funciones siempre usan una interfaz Channel para manipular los objetos creados por el método de fábrica estático. Es decir, aplicamos el principio de Preferir Interfaces sobre Clases (o Inversión de Dependencias).

En el nuevo código, el sistema sigue funcionando con canales del tipo TCPChannel. Sin embargo, si queremos cambiar el tipo de canal, ahora solo necesitamos modificar un único elemento del código: el método create de la clase ChannelFactory. Dicho de otra forma, un método de fábrica estático funciona como un aspirador de métodos new: todas las llamadas antiguas a new migran a una única llamada en el método de fábrica estático.

Existen aún algunas variaciones del patrón de Fábrica. En una de ellas, se usa una clase abstracta para concentrar varios métodos de fábrica. Esta clase recibe entonces el nombre de Fábrica Abstracta. Un ejemplo se muestra en el siguiente código:

```java
abstract class ProtocolFactory { // Fábrica Abstracta
  abstract Channel createChannel();
  abstract Port createPort();
  ...
}

void f(ProtocolFactory pf) {
  Channel c = pf.createChannel();
  Port p = pf.createPort();
  ...
}
```

En el ejemplo anterior, omitimos las clases que extienden la clase abstracta `ProtocolFactory` y que implementarán, de hecho, los métodos concretos para la creación de canales y puertos de comunicación. Podemos tener, por ejemplo, dos subclases: `TCPProtocolFactory` y `UDPProtocolFactory`.

[← Volver](index.md)
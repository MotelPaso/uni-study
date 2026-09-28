# Principio de Responsabilidad Única

_Original: https://www.danielsanmartin.cl/blog/single-responsibility-is/_


Este principio es una aplicación directa de la idea de cohesión. Propone lo siguiente: cada clase debe tener una única responsabilidad. Además, responsabilidad, en el contexto del principio, significa motivo para modificar una clase. Es decir, debe haber una única razón para modificar cualquier clase en un sistema.

Un corolario de este principio recomienda separar la presentación de las reglas de negocio. Por lo tanto, un sistema debe tener clases de presentación, que se encargan de los aspectos de su interfaz con los usuarios, formato de los mensajes, medio por el cual se mostrarán los mensajes, etc. Y clases responsables de las reglas de negocio, es decir, que realizarán las computaciones, procesamiento, análisis, etc. Son intereses y responsabilidades diferentes que pueden evolucionar y sufrir modificaciones por razones distintas. Por lo tanto, deben implementarse en clases diferentes. Por esta razón, no es sorprendente que existan desarrolladores que se ocupan solo de requisitos de front-end (es decir, de clases de presentación) y desarrolladores que se ocupan de requisitos de back-end (es decir, de clases con reglas de negocio).

**Ejemplo**: La siguiente clase ilustra una violación del Principio de Responsabilidad Única. El método calculaIndiceDeInasistencia de la clase Asignatura tiene dos responsabilidades: calcular el índice de inasistencia de una asignatura e imprimirlo en la consola del sistema.

```java
class Asignatura {

  void calculaIndiceDesInasistencia() {
    indice = "calcula índice de inasistencia"
    System.out.println(indice);
  }

}
```

Una solución consiste en dividir esas responsabilidades entre dos clases: una clase de interfaz con el usuario (‘‘Console’’) y una clase de regla de negocio (‘‘Asignatura’’), como se muestra en el siguiente código. Entre otros beneficios, esta solución permite reutilizar la clase de negocio con otras clases de interfaz, como clases de interfaz gráfica, interfaz web, interfaz para móvil, etc.

```java
class Console {

  void imprimeIndiceDeInasistencia(Asignatura asignatura) {
    double indice = asignatura.calculaIndiceDeInasistencia();
    System.out.println(indice);
  }
}

class Asignatura {

  double calculaIndiceDeInasistencia() {
    double indice = "calcula índice de inasistencia"
    return indice;
  }

}
```

[← Volver](index.md)
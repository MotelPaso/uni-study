# Principio de Abierto/Cerrado

_Original: https://www.danielsanmartin.cl/blog/open-closed-is/_


Este principio, propuesto originalmente por Bertrand Meyer en la década de 1980 [enlace](https://dl.acm.org/doi/book/10.5555/261119), sostiene algo que puede parecer paradójico: una clase debe estar cerrada para modificaciones y abierta para extensiones.

Sin embargo, la aparente paradoja se aclara cuando el diseño de la clase prevé la posibilidad de extensiones y personalizaciones. Para ello, el diseñador puede utilizar recursos como la herencia, funciones de orden superior (o funciones lambda) y patrones de diseño, como Abstract Factory, Template Method y Strategy. Específicamente, en el próximo capítulo, abordaremos patrones de diseño que permiten personalizar una clase sin modificar su código.

En resumen, el Principio Abierto/Cerrado tiene como objetivo la construcción de clases flexibles y extensibles, capaces de adaptarse a diversos escenarios de uso sin modificaciones en su código fuente.

**Ejemplo 1**: Un ejemplo de una clase que sigue el Principio Abierto/Cerrado es la clase Collections de Java. Esta clase tiene un método estático para ordenar una lista en orden ascendente según sus elementos. A continuación se muestra un ejemplo de uso de este método:

```java
List<String> nombres;
nombres = Arrays.asList("juan", "maria", "alexandre", "ze");
Collections.sort(nombres);

System.out.println(nombres);
// resultado: ["alexandre","juan","maria","ze"]
```

Sin embargo, en el futuro, podríamos necesitar usar el método sort para ordenar las cadenas de acuerdo con su tamaño en caracteres. Afortunadamente, la clase Collections está preparada para este nuevo escenario de uso. Pero para ello necesitamos implementar un objeto Comparator, que comparará las cadenas por su tamaño, como en el siguiente código.

```java
Comparator<String> comparador = new Comparator<String>() {
  public int compare(String s1, String s2) {
    return s1.length() - s2.length();
  }
};
Collections.sort(nombres, comparador);

System.out.println(nombres);
// resultado: [ze, juan, maria, alexandre]
```

Es decir, la clase `Collections` demostró estar abierta a manejar este nuevo requisito, pero manteniendo su código cerrado, es decir, el código fuente de la clase no tuvo que ser modificado.

**Ejemplo 2**: Ahora mostramos un ejemplo de una función que no sigue el Principio Abierto/Cerrado.

```java
double calcTotalBecas(Alumno[] lista) {
  double  total = 0.0;
  foreach (Alumno alumno in lista) {
    if (alumno instanceof AlumnoGrad) {
      AlumnoGrad grad = (AlumnoGrad) almuno;
      total += "código que calcula beca de grad";
    }
    else if (alumno instanceof AlumnoMagister) {
      AlumnoMagister magister = (AlumnoMagister) alumno;
      total += "código que calcula beca de magister";
    }
  }
  return total;
}
```

Si mañana tuviéramos que crear una nueva subclase de Alumno, por ejemplo, `AlumnoDoctorado`, el código de `calcTotalBecas` tendría que ser adaptado. Es decir, la función no está preparada para acomodar extensiones (es decir, no está abierta), ni es inmune a cambios en su código (es decir, tampoco está cerrada).

El Principio Abierto/Cerrado requiere que el diseñador de una clase anticipe sus puntos de extensión. Por ello, no es posible que una clase acomode todos los posibles tipos de extensiones que puedan surgir. Solo aquellos para los que se ofrecen puntos de extensión, ya sea a través de herencia, funciones de orden superior o patrones de diseño. Por ejemplo, la implementación de la clase Collections (en el ejemplo 1) usa un algoritmo de ordenación que es una versión del MergeSort. Sin embargo, los clientes de la clase no pueden alterar ni personalizar este algoritmo, teniendo que conformarse con la implementación por defecto que se ofrece. Por lo tanto, bajo el criterio de personalización del algoritmo de ordenación, el método sort no cumple con el Principio Abierto/Cerrado.

[← Volver](index.md)
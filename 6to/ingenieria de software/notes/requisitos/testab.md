# Test A/B

_Original: https://www.danielsanmartin.cl/blog/testab/_


Pruebas A/B (o split tests) se utilizan para elegir, entre dos versiones de un sistema, aquella que despierta mayor interés en los usuarios. Las dos versiones son idénticas, excepto en que una implementa un requisito A y la otra implementa un requisito B, siendo A y B mutuamente excluyentes. Es decir, se busca decidir cuál requisito se adoptará efectivamente en el sistema. Para ello, las versiones A y B se liberan para grupos distintos de usuarios. Al final de la prueba, se decide cuál versión despertó mayor interés en esos usuarios. Por lo tanto, las pruebas A/B constituyen un enfoque guiado por datos para la selección de requisitos —o funcionalidades— que serán ofrecidos en un sistema. El requisito ganador se mantendrá en el sistema y la versión con el requisito perdedor será descartada.

Las pruebas A/B pueden utilizarse, por ejemplo, cuando se construye un MVP (con requisitos A) y, después de un ciclo construir-medir-aprender, se pretende probar un nuevo MVP (con requisitos B). Otro escenario muy común son las pruebas A/B aplicadas a componentes de interfaces de usuario. Por ejemplo, dados dos diseños de la página de inicio de un sitio, una prueba A/B puede usarse para decidir cuál produce un mayor compromiso por parte de los usuarios. También se puede probar el color o la posición de un botón de la interfaz, los mensajes utilizados, el orden de presentación de una lista, etc.

Para aplicar pruebas A/B, se necesitan dos versiones de un sistema, que llamaremos **versión de control** (sistema original, con los requisitos A) y **versión de tratamiento** (sistema con nuevos requisitos B). Para ser más claros, y usando el ejemplo del final de la sección sobre MVP, supóngase que la versión de control consiste en un sistema de comercio electrónico que utiliza un algoritmo de recomendación tradicional, mientras que la versión de tratamiento consiste en el mismo sistema, pero con un algoritmo de recomendación supuestamente más eficaz. En ese caso, la prueba A/B tendrá como objetivo definir si el nuevo algoritmo de recomendación es realmente mejor y, por lo tanto, debe incorporarse al sistema.

Para ejecutar pruebas A/B, se necesita una métrica para medir las ganancias obtenidas con la versión de tratamiento. Esa métrica se denomina genéricamente tasa de conversión. En nuestro ejemplo, asumiremos que corresponde al porcentaje de visitas que se convierten en compras por medio de enlaces recomendados. La expectativa es que el nuevo algoritmo de recomendación aumente ese porcentaje.

Por último, se debe instrumentar el sistema de manera que la mitad de los clientes utilice la versión de control (con el algoritmo tradicional) y la otra mitad utilice la versión de tratamiento (con el nuevo algoritmo de recomendación que se está probando). Además, es importante que esta selección sea aleatoria. Es decir, cuando un usuario ingrese al sistema, se elegirá aleatoriamente qué versión utilizará. Para ello, puede modificarse la página principal incluyendo el siguiente fragmento de código:

```plaintext
version = Math.Random(); // número aleatorio entre 0 y 1
if (version < 0.5)
    "ejecutar la versión de control"
else
    "ejecutar la versión de tratamiento"
```

Después de un cierto número de accesos, la prueba se da por terminada y se verifica si la versión de tratamiento efectivamente aumentó la tasa de conversión de usuarios. Si es así, se pasará a utilizarla con todos los clientes. Si no, se continuará con la versión de control.

Una cuestión fundamental en las pruebas A/B es la determinación del tamaño de la muestra. En otras palabras, cuántos clientes deberán ser evaluados con cada una de las versiones. No se profundizará aquí en la estadística de este cálculo, pues ello queda fuera de alcance. Además, existen calculadoras de tamaño de muestra para pruebas A/B disponibles en la web. Sin embargo, conviene mencionar que estas pruebas pueden demandar un número extremadamente elevado de clientes, al alcance solo de sistemas populares, como grandes tiendas de comercio electrónico, servicios de búsqueda, redes sociales, portales de noticias, etc. Para dar un ejemplo, supóngase que la tasa de conversión de clientes es del 1 % y que se desea verificar si el tratamiento introduce una ganancia mínima del 10 % en esa tasa. En ese caso, los grupos de control y de tratamiento deben poseer al menos 200 mil clientes cada uno, para que los resultados de la prueba tengan relevancia estadística, considerando un nivel de confianza del 95 %. Si se quiere ser más preciso:

- Si después de 200 mil accesos la versión B aumenta la tasa de conversión en al menos un 10 %, se puede tener certeza estadística de que esa ganancia es causada por el tratamiento B (en realidad, se puede tener un 95 % de certeza). En consecuencia, se dice que la prueba fue exitosa, es decir, que la versión B ganó.

- En caso contrario, la versión de tratamiento B no alcanzó las ganancias de conversión esperadas. Entonces, se dice que la prueba A/B fracasó.

El tamaño de la muestra de una prueba A/B disminuye bastante cuando las pruebas involucran eventos con una mayor tasa de conversión y que evalúan mejoras de mayor proporción. En el ejemplo anterior, si la tasa de conversión fuera del 10 % y la mejora a probar fuera del 25 %, el tamaño de la muestra caería a 1.800 clientes por grupo. Estos valores fueron estimados usando la calculadora de pruebas A/B de la empresa Optimizely ([enlace](https://www.optimizely.com/sample-size-calculator/#/?conversion=3&effect=20&significance=95)).

**Profundización:** En términos estadísticos, una prueba A/B se modela como una **prueba de hipótesis**. En este tipo de prueba, se parte de una hipótesis nula, que representa el estado actual del sistema. Es decir, la hipótesis nula asume que nada cambiará y que, por lo tanto, la versión B no es mejor que la versión actual del sistema. Por otro lado, la hipótesis que altera ese estado actual se denomina hipótesis alternativa. Por convención, la hipótesis nula se representa por H0 y la hipótesis alternativa por H1.

Una prueba de hipótesis es un procedimiento de decisión que parte del supuesto de que H0 es verdadera y luego intenta refutarla. Para ello, debe utilizarse una prueba estadística específica. Sin embargo, estas pruebas no son totalmente confiables. Es decir, siempre trabajan con una probabilidad de error. Por ejemplo, cualquiera sea la prueba, existe una probabilidad de refutar H0 aun cuando sea verdadera. En esos casos, se dice que ocurrió un error de tipo I o un falso positivo, pues se concluye indebidamente que la versión B es mejor que la versión A.

Si los errores de tipo I no pueden evitarse, al menos puede estimarse la probabilidad con que ocurren. Más específicamente, en pruebas A/B existe un parámetro de entrada llamado nivel de significancia (significance level), representado por la letra griega α (alfa). Este parámetro define la probabilidad de ocurrencia de errores de tipo I.

Por ejemplo, supóngase que α se fija en 5 %. Entonces, existe una probabilidad del 5 % de rechazar H0 indebidamente. En el ejemplo utilizado anteriormente, en lugar de α se usó como parámetro de entrada el valor (1 - α), que es la probabilidad de rechazar H0 correctamente. Normalmente, este valor se denomina nivel de confianza. Se tomó esa decisión porque (1 - α) es el parámetro de entrada más común en las calculadoras de tamaño de muestra para pruebas A/B.

### Preguntas frecuentes

A continuación, se presentan algunas preguntas y aclaraciones sobre las pruebas A/B.

**¿Puedo probar más de dos variaciones?**

Sí. La metodología explicada se adapta a más de dos pruebas. Basta con dividir los accesos en tres grupos aleatorios, por ejemplo, si se desea probar tres versiones de un sistema. Estas pruebas, con más de un tratamiento, se denominan pruebas A/B/n.

**¿Puedo terminar la prueba A/B antes si presenta la ganancia esperada?**

No. Ese es un error frecuente y grave. Si el tamaño de la muestra es de 200 mil usuarios, la prueba —de cada grupo— solo puede concluir cuando se alcance exactamente ese número de usuarios. Más precisamente, no debe finalizar antes, con menos usuarios, ni después, con más usuarios. Un posible error de los desarrolladores cuando comienzan a usar pruebas A/B consiste en interrumpir la prueba el primer día en que se alcanza la ganancia mínima esperada, sin completar el resto de la muestra.

**¿Qué es una prueba A/A?**

Es una prueba en la que los dos grupos, control y tratamiento, ejecutan la misma versión del sistema. Por lo tanto, asumiendo una confianza estadística del 95 %, casi siempre deberían fracasar, pues la versión A no puede ser mejor que ella misma. Las pruebas A/A se recomiendan para probar y validar los procedimientos y decisiones metodológicas adoptados en una prueba A/B. Algunos autores incluso recomiendan que no se inicien pruebas A/B antes de realizar algunas pruebas A/A. Si las pruebas A/A no fracasan, debe depurarse el sistema de experimentación hasta descubrir la causa raíz (root cause) que está haciendo que una versión A sea considerada mejor que ella misma.

**¿Cuál es el origen de los términos grupos de control y de tratamiento?**

Los términos tienen su origen en el área médica, más específicamente en los experimentos aleatorizados controlados (randomized control experiments). Por ejemplo, para lanzar un nuevo fármaco al mercado, las empresas farmacéuticas deben realizar este tipo de experimento. Se eligen dos muestras, llamadas control y tratamiento. Los participantes de la muestra de control reciben un placebo y los participantes de la muestra de tratamiento son tratados con el fármaco. Después de la prueba, se comparan los resultados para verificar si el uso del fármaco fue efectivo. Los experimentos aleatorizados controlados son una forma científicamente aceptada de probar causalidad. En nuestro ejemplo, pueden demostrar que el fármaco probado causó la cura de una enfermedad.

**Mundo real:** Las pruebas A/B son utilizadas por todas las grandes empresas de Internet. A continuación, se reproducen testimonios de desarrolladores y científicos de tres empresas sobre estas pruebas:

- En Facebook, las innovaciones que los ingenieros implementan se liberan inmediatamente para uso de usuarios reales. Esto permite que los ingenieros comparen cuidadosamente las nuevas funcionalidades con el caso base, es decir, con el estado actual del sitio. Las pruebas A/B constituyen un enfoque experimental para descubrir lo que los clientes desean, sin necesidad de elicitar requisitos de manera anticipada ni de escribir especificaciones. Además, las pruebas A/B permiten detectar escenarios en los que los usuarios comienzan a utilizar nuevas funcionalidades de maneras inesperadas. Entre otras cosas, esto permite que los ingenieros aprendan de la diversidad de usuarios y valoren las distintas perspectivas que tienen sobre Facebook ([enlace](https://ieeexplore.ieee.org/document/6449236)).

- En Netflix, los desarrolladores tratan cada funcionalidad como un experimento, lo que hace que ciertas funcionalidades puedan desaparecer después de ser liberadas para uso. Por ejemplo, si un número reducido de clientes está utilizando un nuevo elemento de una interfaz de usuario, puede realizarse un experimento —es decir, una prueba A/B— moviendo el elemento a una nueva posición en la pantalla. Si todos los experimentos fracasan, la funcionalidad se elimina del sistema ([enlace](https://www.computer.org/csdl/magazine/so/2017/03/mso2017030086/13rRUwIF6ja)).

- En Microsoft, específicamente en el servicio de búsquedas Bing, el uso de experimentos controlados creció exponencialmente a lo largo de los años, con más de 200 experimentos concurrentes ejecutándose cada día, según datos de 2013. Se considera que el sistema de experimentación de Bing fue responsable de acelerar la innovación y aumentar los ingresos de la empresa en millones de dólares, al permitir el descubrimiento de ideas que fueron evaluadas mediante miles de experimentos controlados ([enlace](https://dl.acm.org/doi/10.1145/2487575.2488217)).

[← Volver](index.md)
# Otros Métodos Iterativos

_Original: https://www.danielsanmartin.cl/blog/otros_procesos/_


La transición entre Waterfall —dominante en las décadas de 1970 y 1980— y los métodos ágiles —que comenzaron a surgir en la década de 1990, pero que solo ganaron popularidad a fines de los años 2000— fue gradual. Al igual que en los métodos ágiles, los métodos surgidos en ese período de transición poseen el concepto de iteraciones. Es decir, no son estrictamente secuenciales, como en Waterfall. Sin embargo, las iteraciones tienen una duración mayor que la usual en el desarrollo ágil. En lugar de durar pocas semanas, duran algunos meses. Por otro lado, conservan características relevantes de Waterfall, como el énfasis en la documentación y en una fase inicial de levantamiento de requisitos y luego de diseño.

Un ejemplo de propuesta de proceso surgida en esa época es el Modelo en Espiral, propuesto por Barry Boehm, en 1986 (enlace). En ese modelo, un sistema se desarrolla en forma de una espiral de iteraciones. Cada iteración, o vuelta completa en la espiral, incluye cuatro etapas (véase también la figura siguiente):

- Definición de objetivos y restricciones, tales como costos, cronogramas, etc.

- Evaluación de alternativas y análisis de riesgos. Por ejemplo, puede llegarse a la conclusión de que es más conveniente comprar un sistema ya hecho que desarrollar el sistema internamente.

- Desarrollo y pruebas, por ejemplo, usando Waterfall. Al final de esta etapa, debe generarse un prototipo que pueda ser mostrado a los usuarios del sistema.
Planificación de la siguiente iteración o bien tomar la decisión de detenerse, pues lo que ya fue construido es suficiente para atender las necesidades de la organización.

*Modelo Espiral. Cada iteración es dividia en cuatro etapas*

Así, el Modelo en Espiral produce, en cada iteración, versiones más completas de un sistema, comenzando por la versión generada en el centro de la espiral. Sin embargo, cada iteración, sumando las cuatro fases, puede tardar de 6 a 24 meses. Por lo tanto, mucho más que en XP y Scrum. Otra característica importante es la existencia de una fase explícita de análisis de riesgos, de la cual deben resultar medidas concretas para mitigar los riesgos identificados en el proyecto.

El Proceso Unificado (UP), propuesto a fines de la década de 1990, es otro ejemplo de método iterativo de desarrollo. El UP fue propuesto por profesionales vinculados a una empresa de consultoría y de herramientas de apoyo al desarrollo de software llamada Rational, que en 2003 sería comprada por IBM. Específicamente, la versión del método implementada por Rational se llama Rational Unified Process (RUP).

Debido a sus orígenes, el RUP está vinculado a dos tecnologías específicas:

- Lenguaje de modelado UML, pues muchos de los resultados del RUP se documentan y representan utilizando diagramas gráficos de UML. En el Capítulo 4 estudiaremos UML con más detalle. Por ahora, destacaremos que la propuesta era tener un lenguaje de modelado unificado (UML) y también un proceso unificado (RUP), ambos propuestos por el mismo grupo de profesionales.

- Herramientas de apoyo al diseño y análisis de software, conocidas como herramientas CASE (Computer-Aided Software Engineering). El nombre es una analogía con las herramientas CAD (Computer-Aided Design), usadas en proyectos de Ingeniería Civil, Ingeniería Mecánica, Arquitectura, etc. La idea era que el diseño y el análisis de un sistema debían basarse íntegramente en diagramas UML. Pero estos diagramas no serían dibujados en papel, sino utilizando herramientas computacionales (véase un ejemplo en la figura de la página siguiente). Rational, además de proponer su método de desarrollo, también vendía licencias de uso de herramientas CASE.

*Diseño usando herramienta CASE. ArgoUML*

El RUP propone que el desarrollo se descomponga en las siguientes fases:

- Inception (a veces traducida como inicio o concepción): incluye el análisis de viabilidad, la definición de presupuestos, el análisis de riesgos y la definición del alcance del sistema. Al final de esta fase, el caso de negocio (business case) del sistema debe estar bien claro. Incluso puede decidirse que no vale la pena desarrollar el sistema, sino comprar un sistema ya existente.

- Elaboración: incluye la especificación de requisitos (mediante diagramas de casos de uso de UML, por ejemplo), la definición de la arquitectura del sistema, así como de un plan para su desarrollo. Al final de esta fase, todos los riesgos identificados en la fase anterior deben estar debidamente controlados y mitigados.

- Construcción: en la cual se realiza el diseño de más bajo nivel, la implementación y las pruebas del sistema. Al final de esta fase, debe estar disponible un sistema funcional, incluyendo documentación y manuales, que puedan ser validados por los usuarios.

- Transición: en la cual ocurre la puesta del sistema en producción, incluyendo la definición de todas las rutinas de implantación, como políticas de respaldo, migración de datos de sistemas heredados, capacitación del equipo de operación, etc.

Al igual que en el Modelo en Espiral, el proceso puede repetirse varias veces; es decir, el desarrollo es incremental, con nuevas funcionalidades que se entregan en cada ciclo. Adicionalmente, también puede repetirse cada una de las fases. Por ejemplo, Construcción puede dividirse en dos iteraciones, cada una construyendo una parte del producto. La figura siguiente ilustra el modelo de iteraciones del RUP.

*Fases e iteraciones del RUP. Las iteraciones son posibles en cada fase (auto-bucles). Y también puede repetirse todo el ciclo (bucle externo), para generar un nuevo incremento del producto*

El RUP también define un conjunto de disciplinas de ingeniería que incluyen, por ejemplo: modelado de negocios, definición de requisitos, análisis y diseño, implementación, pruebas e implantación. Estas disciplinas —o flujos de trabajo— pueden ocurrir en cualquier fase. Sin embargo, se espera que algunas disciplinas sean más intensas en determinadas fases, como muestra la figura siguiente. En el proyecto ilustrado, las tareas de modelado de negocio están concentradas en las fases iniciales del proyecto (Inception y Elaboración) y casi no ocurren en las fases siguientes. Por otro lado, la implementación está concentrada en la fase de Construcción.

*Fases (en el eje horizontal) y disciplinas (en el eje vertical) de un proyecto desarrollado usando RUP. El área de la curva muestra la intensidad de la disciplina durante cada fase (imagen de Wikipedia, licencia: dominio público)*

[← Volver](index.md)
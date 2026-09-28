# DevOps

_Original: https://www.danielsanmartin.cl/blog/devops/_


> Imagina un mundo donde product owners, desarrollo, QA, operaciones de TI y seguridad trabajan juntos, no solo para ayudarse mutuamente, sino también para asegurar que toda la organización tenga éxito.

*Gene Kim, Jez Humble, Patrick Debois y John Willis*

DevOps es un enfoque que busca aproximar las culturas de **desarrollo** (Dev) y **operaciones** (Ops) para que la entrega de software sea más rápida, confiable y menos traumática. Aunque el término es relativamente reciente, puede entenderse como una extensión de la mentalidad ágil hacia la última milla de un proyecto: el momento en que el sistema debe ser implantado, liberado o puesto en producción.

En un proyecto de software no basta con levantar requisitos, diseñar, programar, probar y refactorizar. Después de todo eso, el sistema —o un incremento del sistema— debe llegar a sus usuarios. Esa tarea suele llamarse **implantación** (*deploy*), **liberación** (*release*) o **entrega** (*delivery*). Aunque puede parecer un paso final simple, en muchas organizaciones ha sido históricamente una fuente importante de retrasos, errores y tensiones.

En esta entrada se presentan los conceptos centrales de DevOps y tres prácticas fundamentales asociadas:

- control de versiones;

- integración continua;

- deployment continuo y entrega continua.

---

### Introducción

En organizaciones tradicionales, el área de Tecnología de la Información solía dividirse en dos grupos con responsabilidades separadas. Por un lado estaba el equipo de sistemas o desarrollo, formado por desarrolladores, programadores, analistas y arquitectos. Por otro lado estaba el equipo de soporte u operaciones, formado por administradores de red, administradores de bases de datos, técnicos de soporte, especialistas de infraestructura y personal de seguridad.

El problema de esta separación era que operaciones muchas veces conocía un sistema recién en la víspera de su implantación. Como consecuencia, podían aparecer problemas no detectados previamente: falta de hardware, incompatibilidades con la base de datos de producción, vulnerabilidades de seguridad, problemas de desempeño, configuraciones incompletas o dependencias no documentadas. En casos extremos, estos problemas podían retrasar la implantación durante meses o incluso hacer que el sistema fuera abandonado.

DevOps surge como respuesta a ese problema. Su objetivo no es crear una nueva persona que haga todo, ni reemplazar a desarrolladores u operadores por un único cargo. La idea central es **aproximar Dev y Ops**, evitando que trabajen como silos independientes. Cuando ambos equipos colaboran desde el inicio del proyecto, es más fácil anticipar problemas de infraestructura, seguridad, desempeño, configuración y monitoreo.

En una cultura DevOps, un equipo ágil puede incluir también a una persona de operaciones, ya sea de forma parcial o completa. Esa persona puede participar en la planificación, anticipar riesgos técnicos y preparar scripts de instalación, configuración, administración y monitoreo mientras el código todavía está siendo desarrollado.

Un aspecto clave de DevOps es la **automatización**. La entrega de software no debería depender de una secuencia larga de pasos manuales. Idealmente, poner un sistema en producción debería ser un proceso repetible, confiable y lo más automático posible.

Una frase que resume bien el cambio cultural propuesto por DevOps es la siguiente:

> En lugar de iniciar las implantaciones a la medianoche del viernes y pasar el fin de semana trabajando para concluirlas, las implantaciones deberían ocurrir en cualquier día hábil, cuando todos están en la empresa, y sin que los clientes lo perciban, excepto cuando encuentran nuevas funcionalidades o correcciones de errores.

---

### Principios relacionados con DevOps

Un proceso de entrega de software alineado con DevOps suele apoyarse en los siguientes principios.

**Crear un proceso repetible y confiable para la entrega de software.**

La entrega no debe ser un evento traumático ni depender de procedimientos improvisados. Debe ser un proceso conocido, probado y repetible.

**Automatizar todo lo que sea posible.**

El build, la ejecución de pruebas, la configuración de servidores, la carga de datos y la activación del sistema deberían ejecutarse mediante procesos automatizados.

**Mantener todo bajo control de versiones.**

No solo el código fuente debe estar versionado. También deberían versionarse scripts, configuraciones, documentación, archivos de datos relevantes, infraestructura como código y otros elementos necesarios para reproducir el sistema.

**Si un paso causa dolor, ejecutarlo con más frecuencia y cuanto antes.**

La integración de código suele ser dolorosa cuando se posterga demasiado. Por eso, DevOps y la integración continua recomiendan integrar cambios pequeños con frecuencia, idealmente todos los días.

**“Terminado” significa listo para entregar.**

Una historia no debería considerarse terminada si todavía falta probarla con datos reales, documentarla, integrarla o preparar su despliegue. En DevOps, terminado significa estar en condiciones reales de entrar en producción.

**Todos son responsables por la entrega del software.**

La responsabilidad de entregar software funcionando no pertenece únicamente a desarrollo ni únicamente a operaciones. Es una responsabilidad compartida.

---

### Control de versiones

El desarrollo de software es una actividad colaborativa. Por eso, los equipos necesitan un mecanismo para almacenar el código fuente, mantener el historial de cambios y coordinar el trabajo de varias personas. Ese mecanismo es un **Sistema de Control de Versiones** o **VCS** (*Version Control System*).

Un VCS cumple dos funciones principales. Primero, almacena la versión más reciente del código fuente y de otros archivos relacionados, como documentación, configuraciones, scripts y páginas web. Segundo, permite recuperar versiones anteriores de los archivos, lo que posibilita volver en el tiempo si se introduce un error o si se necesita revisar una implementación antigua.

Los primeros sistemas de control de versiones eran centralizados. En ellos existe un único servidor que almacena el repositorio. Los clientes descargan archivos desde ese servidor, los modifican y luego envían sus cambios mediante una operación de commit.

*VCS Centralizado. Existe un único repositorio, en el nodo servidor*

A partir de los años 2000 se popularizaron los **Sistemas de Control de Versiones Distribuidos** o **DVCS**, como Git y Mercurial. En un DVCS, cada desarrollador tiene en su máquina una copia completa del repositorio. Esto permite trabajar de manera local, hacer commits sin conexión y sincronizar los cambios posteriormente con otros repositorios.

*VCS Distribuido (DVCS). Cada cliente poseee un servidor. Una arquitectura peer-to-peer*

En la práctica, aunque un DVCS permite una arquitectura entre pares, muchas organizaciones mantienen un repositorio principal que funciona como referencia. En ese contexto, dos operaciones son fundamentales:

- `pull` : actualiza el repositorio local con cambios disponibles en el repositorio central;

- `push` : envía al repositorio central los commits realizados localmente.

Entre las principales ventajas de un DVCS se encuentran las siguientes:

- permite trabajar y versionar cambios sin conexión;

- permite hacer commits con mayor frecuencia;

- los commits son rápidos porque se realizan localmente;

- la sincronización no tiene que ocurrir siempre contra un único servidor central;

- facilita arquitecturas alternativas, como sincronizaciones jerárquicas o entre pares.

Git es actualmente uno de los DVCS más usados. Fue creado en 2005, en el contexto del desarrollo del kernel de Linux. GitHub, por su parte, es una plataforma de hospedaje de código que utiliza Git para ofrecer repositorios públicos y privados, además de funcionalidades como pull requests, forks, issues y acciones automatizadas.

---

### Multirepos y monorepos

Una organización que usa control de versiones debe decidir cómo organizar sus repositorios. Una alternativa es crear un repositorio por proyecto o sistema. A esta estrategia se le llama **multirepo**. Otra alternativa es mantener varios proyectos dentro de un único repositorio. A esta estrategia se le llama **monorepo**.

*Multirepos: un VCS administra varios repositorios. Normalmente, un repositorio por proyecto o sistema*

*Monorepo: un VCS administra un único repositorio. Los proyectos son directorios de ese repositorio*

Si una organización usa multirepos, podría tener repositorios como:

```text
ucn/sistema1
ucn/sistema2
ucn/sistema3
```

Si usa monorepo, podría tener un único repositorio:

```text
ucn/sistemas
```

y dentro de ese repositorio los directorios:

```text
sistema1/
sistema2/
sistema3/
```

Entre las ventajas de los monorepos se pueden mencionar:

- existe una única fuente de verdad sobre las versiones del código;

- se facilita la visibilidad y el reúso de código;

- los cambios que afectan a varios sistemas pueden hacerse de forma atómica en un único commit;

- se facilitan refactorizaciones en gran escala.

Sin embargo, los monorepos también tienen desventajas. La principal es que pueden requerir herramientas especializadas para navegar, buscar, compilar y probar bases de código muy grandes. Por ejemplo, una organización con millones de líneas de código puede necesitar herramientas internas para que los desarrolladores trabajen eficientemente con el repositorio.

---

### Integración continua

La **Integración Continua** o **CI** (*Continuous Integration*) es una práctica de desarrollo propuesta originalmente por Extreme Programming. Su idea central es integrar el código con frecuencia, evitando que los cambios permanezcan aislados durante demasiado tiempo.

Para entender su motivación, consideremos el uso tradicional de ramas de funcionalidades. Una desarrolladora puede crear una rama para implementar una funcionalidad compleja y trabajar allí durante varias semanas. Mientras tanto, otros desarrolladores continúan modificando la rama principal. Cuando la funcionalidad finalmente se integra de vuelta, pueden aparecer muchos conflictos de merge.

*Desarrollo usando branches de funcionalidas*

Este problema se conoce como **integration hell** o **merge hell**. Puede ocurrir, por ejemplo, cuando una función usada por la rama de funcionalidad fue renombrada o modificada en la rama principal, o cuando una función cambió su comportamiento en una rama pero siguió siendo usada con la semántica antigua en otra.

Mientras más tiempo vive una rama separada, mayor es la probabilidad de que aparezcan conflictos difíciles de resolver. Además, las ramas largas pueden crear silos de conocimiento: cada funcionalidad queda asociada a una persona o grupo, y el resto del equipo puede perder visibilidad sobre lo que está ocurriendo.

CI propone resolver ese problema integrando cambios pequeños con frecuencia. En lugar de esperar semanas para integrar, los desarrolladores integran su código todos los días, o incluso varias veces al día. Así, los conflictos aparecen antes, son más pequeños y resultan más fáciles de resolver.

Una forma simple de expresar la idea es:

> Si integrar causa dolor, integra con mayor frecuencia.

---

### Buenas prácticas para usar CI

Cuando una organización adopta CI, la rama principal se actualiza constantemente. Por eso, es necesario protegerla mediante prácticas técnicas que permitan detectar errores rápidamente.

#### Build automatizado

El **build** es el proceso que compila o prepara el sistema hasta generar una versión ejecutable. En CI, el build debe estar automatizado y no depender de pasos manuales. También debe ser rápido, porque se ejecutará muchas veces.

#### Pruebas automatizadas

Además de verificar que el sistema compila, CI debe verificar que el comportamiento sigue siendo correcto. Por eso, es fundamental contar con pruebas automatizadas, especialmente pruebas unitarias. Sin pruebas, un servidor de CI solo comprobaría que el sistema construye, pero no que funciona correctamente.

#### Servidores de integración continua

Un servidor de CI ejecuta automáticamente el build y las pruebas cuando detecta un nuevo commit. El flujo general es el siguiente:

1. Un desarrollador realiza un commit.

2. El sistema de control de versiones notifica al servidor de CI.

3. El servidor clona o actualiza el repositorio.

4. Ejecuta el build y las pruebas.

5. Notifica el resultado al equipo.

*Servidor de Integración Continua*

El objetivo principal del servidor de CI es evitar que código con problemas se mantenga integrado. Cuando el build falla, suele decirse que el build se “rompió”. Esto puede ocurrir aunque el código haya funcionado en la máquina del desarrollador. Por ejemplo, el desarrollador pudo olvidar versionar un archivo, o pudo usar localmente una versión de biblioteca distinta de la usada por el servidor.

Cuando el servidor de CI informa que el build se rompió o que las pruebas fallaron, la corrección debe tener máxima prioridad. Un build roto bloquea el trabajo del resto del equipo y rompe la confianza en la rama principal.

Sin embargo, es importante no confundir adoptar CI con simplemente instalar un servidor de CI. Puede existir un servidor que ejecuta builds automáticos, pero si el equipo no integra código frecuentemente, entonces no hay integración continua real. A veces a esto se le llama **teatro de CI**: se usan herramientas de CI, pero no se adopta la práctica de integración frecuente.

---

### CI y branches

CI no es completamente incompatible con el uso de ramas. Sin embargo, sí es incompatible con ramas de larga duración. Si una rama vive durante semanas y se integra recién al final, entonces la integración no es continua.

Una regla práctica es que los branches deben integrarse con mucha frecuencia, idealmente a diario. Si una rama de funcionalidad dura menos de un día, puede convivir razonablemente con CI. Si dura semanas, se aleja del principio fundamental de integración continua.

Por esta razón, muchas organizaciones que adoptan CI también adoptan **Desarrollo Basado en Trunk** o **TBD** (*Trunk-Based Development*). En TBD, el desarrollo ocurre principalmente en la rama principal, también llamada `trunk`, `main` o `master`. Las ramas de funcionalidad desaparecen o se usan solo por períodos muy breves.

El beneficio de TBD es que los problemas de integración se detectan temprano. En lugar de tener grandes merges después de semanas, el equipo integra cambios pequeños y frecuentes.

---

### Programación en pares

La programación en pares puede considerarse una forma continua de revisión de código. Dos desarrolladores trabajan juntos: una persona escribe el código y la otra revisa, pregunta y propone mejoras. En un contexto de CI, esta práctica ayuda a detectar problemas antes de que el código llegue a la rama principal.

No es obligatorio usar programación en pares para adoptar CI, pero puede complementar bien el proceso. Otra alternativa es revisar el código después del commit, aunque eso puede aumentar el costo de corrección si el código ya fue integrado.

---

### Cuándo no usar CI estricta

Los defensores de CI suelen recomendar al menos una integración diaria por desarrollador. Sin embargo, esta regla puede ser difícil de aplicar en ciertos contextos: sistemas críticos, equipos con desarrolladores muy nuevos, proyectos con validaciones regulatorias o dominios donde cada cambio requiere revisiones muy estrictas.

Esto no significa que CI deba descartarse por completo. Más bien, la práctica puede adaptarse al contexto. Por ejemplo, una organización podría experimentar con integraciones cada dos o tres días y evaluar si el costo de integración sigue siendo bajo.

CI tampoco se ajusta siempre a proyectos de código abierto con colaboradores voluntarios. En esos casos, los desarrolladores no necesariamente trabajan todos los días, y un modelo basado en forks y pull requests suele ser más adecuado.

---

### Deployment continuo

Con integración continua, el código nuevo se integra con frecuencia en la rama principal. Sin embargo, ese código no necesariamente entra de inmediato en producción. Puede tratarse de una versión preliminar, una interfaz incompleta o una función con problemas de desempeño.

El **Deployment Continuo** o **CD** (*Continuous Deployment*) lleva la automatización un paso más allá. En CD, todo commit que llega a la rama principal y pasa las verificaciones automatizadas puede entrar rápidamente en producción, a veces en cuestión de horas.

Un flujo típico de CD es el siguiente:

1. El desarrollador implementa y prueba en su máquina local.

2. Realiza un commit.

3. El servidor de CI ejecuta build y pruebas unitarias.

4. Algunas veces al día se ejecutan pruebas más completas: integración, interfaz, desempeño, seguridad u otras.

5. Si todas las verificaciones pasan, los cambios se despliegan en producción.

Entre las ventajas de CD se encuentran:

- reduce el tiempo de entrega de nuevas funcionalidades;

- transforma las implantaciones en un “no-evento”;

- reduce el estrés asociado a grandes fechas de entrega;

- permite obtener feedback real de usuarios en menos tiempo;

- favorece la experimentación y el desarrollo guiado por datos.

Para que CD funcione bien, los cambios deben ser pequeños. En lugar de desarrollar una gran funcionalidad durante meses y liberarla de una vez, el equipo debe aprender a dividir el trabajo en partes pequeñas que puedan implementarse, probarse, integrarse y desplegarse rápidamente.

---

### Entrega continua

El deployment continuo no siempre es adecuado. En sistemas web puede ser natural actualizar el sistema varias veces al día sin que los usuarios lo noten. Pero en sistemas de escritorio, aplicaciones móviles o software embebido, los usuarios pueden verse obligados a instalar una nueva versión, reiniciar dispositivos o actualizar dependencias.

En esos casos puede usarse una práctica más moderada llamada **Entrega Continua** o **Continuous Delivery**. La idea es que cada commit esté potencialmente listo para producción, pero la decisión de liberarlo queda en manos de una autoridad externa, como un gerente de releases o de proyecto.

La diferencia puede resumirse así:

- **Deployment** : liberar una versión para que los usuarios la usen.

- **Delivery** : preparar una versión para que pueda ser liberada.

En deployment continuo, ambas cosas ocurren de forma automática y frecuente. En entrega continua, el software se mantiene listo para producción, pero la liberación final requiere una decisión manual.

---

### Feature flags

No siempre todo commit está listo para ser activado para los usuarios. Una funcionalidad puede estar parcialmente implementada, no haber sido suficientemente probada o tener problemas de desempeño. Una solución sería evitar integrarla en la rama principal, pero eso contradice la integración continua y puede reintroducir el problema del merge hell.

Una alternativa es integrar el código parcial, pero mantenerlo deshabilitado mediante una variable booleana llamada **feature flag** o **feature toggle**.

Por ejemplo:

```java
featureX = false;

if (featureX) {
   // código incompleto de la funcionalidad X
}

if (featureX) {
   // más código incompleto de la funcionalidad X
}
```

Mientras `featureX` sea `false`, el código no se ejecuta en producción. El equipo puede seguir integrando cambios sin exponer la funcionalidad a los usuarios.

Otro ejemplo:

```java
nuevaPagina = false;

if (nuevaPagina) {
   // cargar nueva página
} else {
   // cargar página antigua
}
```

Durante el desarrollo, la persona responsable puede activar la nueva página en su ambiente local. En producción, el flag permanece desactivado hasta que la funcionalidad esté lista.

Los feature flags pueden generar duplicación temporal de código, porque durante un tiempo conviven la implementación antigua y la nueva. Una vez que la funcionalidad se aprueba y recibe feedback positivo, el código antiguo y el flag deben eliminarse.

---

### Release canario y pruebas A/B

Los feature flags también permiten liberar una funcionalidad de manera gradual. En una **release canario**, una funcionalidad se activa primero para un grupo pequeño de usuarios, por ejemplo, el 5%. Si no aparecen problemas, se amplía gradualmente la cantidad de usuarios que reciben la funcionalidad.

El nombre “canario” proviene de una práctica usada antiguamente en minas de carbón. Los mineros llevaban un canario en una jaula para detectar gases tóxicos: si el canario moría, los mineros sabían que debían salir. En software, una release canario permite detectar problemas con una base pequeña de usuarios antes de afectar a todos.

Los feature flags también permiten realizar **pruebas A/B**. En estas pruebas se liberan simultáneamente dos versiones de una funcionalidad a grupos distintos de usuarios, con el objetivo de comparar su impacto.

Para manejar múltiples flags, puede usarse una estructura de datos especializada:

```java
FeatureFlagsTable fft = new FeatureFlagsTable();

fft.addFeature("nuevo-carrito-compras", false);

if (fft.isEnabled("nuevo-carrito-compras")) {
   // procesar compra usando el nuevo carrito
} else {
   // procesar compra usando el carrito actual
}
```

Existen bibliotecas dedicadas a gestionar feature flags. Una ventaja de esas bibliotecas es que los flags pueden activarse o desactivarse desde archivos de configuración, paneles administrativos o servicios externos, sin recompilar el código.

Es importante distinguir distintos tipos de flags. Los **release flags** se usan para ocultar código que todavía no está listo para producción. En cambio, los **business flags** permiten ofrecer distintas versiones de un sistema, por ejemplo una versión gratuita y una versión pagada. Los business flags suelen tener una vida más larga que los release flags.

---

### Bibliografía recomendada

- Gene Kim, Jez Humble, John Willis y Patrick Debois. *Manual de DevOps: cómo obtener agilidad, confiabilidad y seguridad en organizaciones tecnológicas* . Alta Books, 2018.

- Jez Humble y David Farley. *Entrega continua: cómo entregar software de forma rápida y confiable* . Bookman, 2014.

- Steve Matyas, Andrew Glover y Paul Duvall. *Continuous Integration: Improving Software Quality and Reducing Risk* . Addison-Wesley, 2007.

---

### Ejercicios

1. Defina y describa los objetivos de DevOps.

2. En ofertas laborales de TI es común encontrar cargos como “Ingeniero DevOps”, que piden habilidades en Git, Bitbucket, SVN, Maven, Gradle, Jenkins, Bamboo, administración en cloud, sistemas operativos, bases de datos, Docker, Kubernetes, APIs REST y Java. Considerando la definición de DevOps, ¿le parece adecuado que el cargo de una persona sea “Ingeniero DevOps”? Justifique.

3. Describa dos ventajas de un Sistema de Control de Versiones Distribuido, como Git.

4. Describa una desventaja relacionada con el uso de monorepos.

5. Defina y diferencie los siguientes términos: integración continua, entrega continua y deployment continuo.

6. ¿Por qué integración continua, entrega continua y deployment continuo son prácticas importantes en DevOps?

7. Investigue el significado de la expresión “teatro de CI” (*CI Theater*) y descríbalo con sus propias palabras.

8. Suponga que fue contratado por una empresa que fabrica impresoras y debe definir prácticas de DevOps para el desarrollo de los drivers. ¿Adoptaría deployment continuo o entrega continua? Justifique.

9. Describa un problema que puede surgir al usar feature flags para delimitar código que aún no está listo para producción.

10. Lenguajes como C poseen soporte para directivas de compilación condicional como `#ifdef` y `#endif`. Investigue cómo funcionan y explique la diferencia entre esas directivas y los feature flags.

11. ¿Qué tipo de feature flags suele tener mayor tiempo de vida en el código: release flags o business flags? Justifique.

12. Cuando una empresa migra a CI, normalmente reduce el uso de feature branches largas y adopta desarrollo basado en trunk. Sin embargo, esto no significa que nunca se usen branches. Describa otro uso posible de branches que no sea implementar una feature.

13. Busque un caso real de una gran actualización de interfaz en un sistema web. Explique qué práctica o tecnología permitió liberar la actualización de forma gradual y con menor riesgo.

[← Volver](../ingsoft.md)
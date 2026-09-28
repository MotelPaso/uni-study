# Arquitectura de Software

_Original: https://www.danielsanmartin.cl/blog/arquitectura/_


> Architecture is about the important stuff. Whatever that is. *Ralph Johnson*

Existen más de una definición para arquitectura de software. Una de las más comunes considera que la arquitectura se preocupa con el diseño a un nivel más alto. Es decir, el enfoque deja de ser la organización e interfaces de clases individuales y pasa a ser sobre unidades de mayor tamaño, ya sean paquetes, componentes, módulos, subsistemas, capas o servicios — el nombre no es tan importante en este primer momento. De manera genérica, los términos que acabamos de mencionar deben entenderse como conjuntos de clases relacionadas.

Además de tener un mayor tamaño, los componentes arquitecturales deben ser relevantes para que un sistema cumpla con sus objetivos. Por ejemplo, supongamos que estás trabajando en un sistema de información. Ciertamente, este sistema incluye un módulo de persistencia, que hace la interfaz con la base de datos. Este módulo es fundamental en los sistemas de información, ya que su objetivo principal es automatizar y almacenar información relacionada con los procesos de negocio. Por otro lado, supongamos ahora que estás trabajando en un sistema que utiliza técnicas de inteligencia artificial para diagnosticar enfermedades. El sistema también tiene un módulo de persistencia para almacenar datos de las enfermedades que se diagnostican. Sin embargo, este módulo, además de ser simple, no es relevante para el objetivo principal del sistema. Por lo tanto, no forma parte de su arquitectura.

Existe una segunda definición para la arquitectura de software. Tal como se expresa en la frase de Ralph Johnson que abre esta sección, considera que la arquitectura de software incluye las decisiones de diseño más importantes en un sistema. Estas decisiones son tan importantes que, una vez tomadas, difícilmente podrán revertirse en el futuro. Por lo tanto, esta segunda forma de definir la arquitectura es más amplia que la primera que presentamos. Considera que la arquitectura no es solo un conjunto de módulos, sino un conjunto de decisiones. Es cierto que entre esas decisiones se incluye la definición de los módulos principales de un sistema. Pero también se contemplan otras decisiones, como la elección del lenguaje de programación y la base de datos que se utilizarán en el desarrollo. De hecho, una vez que un sistema se implementa con una base de datos determinada, es difícil migrar a otra base de datos. Prueba de ello es que aún hoy tenemos ejemplos de sistemas críticos que funcionan con bases de datos no relacionales y que están implementados en lenguajes como COBOL.

Los patrones arquitecturales proponen una organización de más alto nivel para sistemas de software, incluyendo sus principales módulos y las relaciones entre ellos. Estas relaciones definen, por ejemplo, que un módulo A puede (o no puede) utilizar los servicios de un módulo B. En esta seccion, estudiaremos patrones arquitecturales que dan origen a las siguientes arquitecturas:

- [Arquitectura Modelo-Vista-Controlador o MVC](/blog/mvc-ing/)

- [Microservicios](/blog/microservices-ing/)

Profundización: Algunos autores — como Taylor et al. ([link](https://dl.acm.org/doi/book/10.5555/553109)) — hacen una distinción entre patrones y estilos arquitecturales. Según ellos, los patrones se enfocan en soluciones para problemas específicos de arquitectura; mientras que los estilos arquitecturales proponen que los módulos de un sistema deben organizarse de una manera determinada, lo que no necesariamente ocurre con el fin de resolver un problema específico. Así, para estos autores, MVC es un patrón arquitectural que resuelve el problema de separar la presentación y el modelo en sistemas de interfaces gráficas. Por otro lado, Pipes & Filtros constituyen un estilo arquitectural. Sin embargo, no haremos esta distinción. En lugar de ello, llamaremos a todos ellos patrones arquitecturales.

[← Volver](../ingsoft.md)